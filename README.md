# Template: Semantic Release

A template that performs a semantic-release for NPM-based modules, using the [semantic-release](https://www.npmjs.com/package/semantic-release) NPM module.

## Usage

### Secrets

The following secrets are needed in order to execute correctly:

* `NPM_TOKEN` - NPM token. Used for publishing the updated version to the NPM Registry.
* `GH_TOKEN` - Github token. Used for tagging the correct commit SHA with the respective version.

#### Example

```
# screwdriver.yaml
---
jobs:
  main:
    secrets:
    # These secrets are defined in the Pipeline page
    - NPM_TOKEN
    - GH_TOKEN
    template: screwdriver-cd/semantic-release@stable
```

### What the Template Does

This template executes the following steps:

* `check_prerequisite`
* `install_binaries`
* `publish`

#### check_prerequisite

This step ensures that the `NPM_TOKEN` and `GH_TOKEN` secret variables are all set. However, this step does *not* verify nor validate the values; it only checks that they are populated.

#### install_binaries

This step installs the necessary binaries and libraries in order to perform all the template operations.

Overriding this step may cause unwanted side effects during the publish.

#### publish

This step is what performs the semantic release operations via the [semantic-release](https://www.npmjs.com/package/semantic-release) NPM module.
