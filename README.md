Thumbnailer: A Plugin for Pelican
=================================

[![Build Status](https://img.shields.io/github/actions/workflow/status/pelican-plugins/thumbnailer/main.yml?branch=main)](https://github.com/pelican-plugins/thumbnailer/actions)
[![PyPI Version](https://img.shields.io/pypi/v/pelican-thumbnailer)](https://pypi.org/project/pelican-thumbnailer/)

Thumbnailer is a Pelican plugin that creates thumbnails for all of the images found under a specific directory, in various thumbnail sizes.


Installation
-------------

This plugin can be installed via:

    python -m pip install pelican-thumbnailer

[Pillow](https://pillow.readthedocs.io/) will be automatically installed in order to resize the images, and the thumbnail will only be re-built if it doesn't already exist (to save processing time). Depending on your local environment and your image types, you may need to also install [external libraries](https://pillow.readthedocs.io/en/stable/installation.html#external-libraries) to add support for certain image file formats.

As long as you have not explicitly added a `PLUGINS` setting to your Pelican settings file, then the newly-installed plugin should be automatically detected and enabled. Otherwise, you must add `thumbnailer` to your existing `PLUGINS` list. For more information, please see the [How to Use Plugins](https://docs.getpelican.com/en/latest/plugins.html#how-to-use-plugins) documentation.


Configuration
-------------

* `IMAGE_PATH` is the path to the image directory. It should reside inside your content directory, and defaults to `pictures`.
* `THUMBNAIL_DIR` is the path to the output sub-directory where the thumbnails are generated.
* `THUMBNAIL_SIZES` is a dictionary mapping size name to size specifications.
  The generated filename will be `originalname_thumbnailname.ext` unless `THUMBNAIL_KEEP_NAME` is set.
* `THUMBNAIL_KEEP_NAME` is a Boolean that, if set, puts the file with the original name in a `thumbnailname` folder, named like the key in `THUMBNAIL_SIZES`.
* `THUMBNAIL_KEEP_TREE` is a Boolean that, if set, saves the image directory tree.
* `THUMBNAIL_INCLUDE_REGEX` is an optional string that is used as regular expression to restrict thumbnailing to matching files. By default all files not starting with a dot are respected.

Sizes can be specified using any of the following formats:

* `wxh` will resize to exactly `wxh` cropping as necessary to get that size
* `wx?` will resize so that the width is the specified size, and the height will scale to retain aspect ratio
* `?xh` same as `wx?` but will height being a set size
* `s` is a shorthand for `wxh` where `w=h`


Contributing
------------

Contributions are welcome and much appreciated. Every little bit helps. You can contribute by improving the documentation, adding missing features, and fixing bugs. You can also help out by reviewing and commenting on [existing issues][].

To start contributing to this plugin, review the [Contributing to Pelican][] documentation, beginning with the **Contributing Code** section.

[existing issues]: https://github.com/pelican-plugins/thumbnailer/issues
[Contributing to Pelican]: https://docs.getpelican.com/en/latest/contribute.html
