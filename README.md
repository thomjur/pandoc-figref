# pandoc-figref

## Description
A simple lua-filter for Pandoc that creates in-text references to figures (for HTML/PDF/LaTeX output only). **This filter was tested with Pandoc version 3.1**.

## Installation
To install the pandoc-lua filter, just download the `pandoc-figref.lua` filter from the `filter/` folder in this repository.

If you want to apply the filter, just add it to your pipeline (CLI example) and make sure that it is accessible under the given path from your current location:

`pandoc --lua-filter=pandoc-figref.lua --citeproc <DOCUMENT>.md -o <DOCUMENT>.html`

**Important**: If you are using citeproc, it is crucial that pandoc-figref is called *before* citeproc!

## How-To
The pandoc-figref filter was inspired by [pandoc-fignos](https://github.com/tomduck/pandoc-fignos) (which sadly seems to have issues with newer versions of Pandoc). If you want to refer to an figure/image, you first need to assign an identifier to the figure:

```
![This is a figure caption.](figure1.png){#fig:figure1}
```

You can then create references/links to this figure from within your text by using the following syntax:

```
This is an important point (for the details, please see figure @fig:figure1).
```

Which will be rendered (HTML/LaTeX/PDF only) as `This is an important point (for the details, please see figure 1).`, where `1` is a link to the actual figure.