# meta-partup

OpenEmbedded/Yocto layer providing the `partup` tool recipes and the
`image-types-partup` image class to build `.partup` packages.

## Usage

Add the layer to `bblayers.conf`, then in your machine or image configuration:

```
IMAGE_CLASSES += "image-types-partup"
IMAGE_FSTYPES += "partup"
```

## Class variables

| Variable                 | Description                                                                                          |
|--------------------------|------------------------------------------------------------------------------------------------------|
| `PARTUP_PACKAGE_FILES`   | Files (from `DEPLOY_DIR_IMAGE` or `IMGDEPLOYDIR`) included in the package                            |
| `PARTUP_PACKAGE_DEPENDS` | Recipes whose `do_deploy` (or `recipe:task`) must run before packaging                               |
| `PARTUP_PACKAGE_SUFFIX`  | Package file suffix (default `.partup`)                                                              |
| `PARTUP_LAYOUT_CONFIG`   | Layout YAML file name (default `${IMAGE_LINK_NAME}.yaml`)                                            |
| `PARTUP_SEARCH_PATH`     | Search path for the layout file (default: recipe dir and `files/partup` in each `BBPATH` entry)      |
| `PARTUP_SECTIONS`        | Names of optional `# BEGIN_<NAME>` / `# END_<NAME>` blocks; enabled by `PARTUP_SECTION_<name> = "1"` |
| `PARTUP_ARRAYS`          | Names of `# ARRAY_<NAME>` templates, expanded from `PARTUP_ARRAY_<name>`, replacing `@KEY@`          |

The layout file is expanded with the BitBake datastore, so `${VAR}` references
may be used in it.

## License

This layer is licensed under the MIT License. See [LICENSE](LICENSE) for
details.

## Maintainer

Copyright © 2026 PHYTEC Messtechnik GmbH

Maintainer: Martin Schwan <m.schwan@phytec.de>
