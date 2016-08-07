# Sample flexmark-java application

Simple use of [flexmark-java] to convert [Markdown] to HTML with options settings compatible
with [Markdown Navigator] parser options.

### Options

Two parameters control the option configuration: `ForUseBy` enum allows selecting the following
Markdown Navigator context:

- `PARSER` equivalent to parsing for generating PsiTree and syntax highlighting
- `JAVAFX` equivalent to generating HTML for JavaFX WebView browser
- `SWING` equivalent to generating HTML for Swing browser
- `HTML` equivalent to generating the HTML plain HTML text

The other parameter is a set of options that emulate Markdown Navigator parser settings, with
defaults set to mimick GFM Document compatibility.

Nothing is stopping you from modifying the `MutableDataSet` returned by the static `options()`
method to customize the options to your requirements.

### HTML Rendering and Link Resolution

Keep in mind that Markdown Navigator provides custom link resolver to convert document relative
and site absolute links to actual files. This is not available outside of the plugin and if
desired must be implemented according to your project requirements via a
[flexmark-java extension].

Similarly none of the style sheets, java scripts or other necessary HTML document elements are
generated. These are left to the discretion of the user. This can be accomplished by wrapping
the rendered HTML with desired text or through a flexmark-java extension implementing a
`PhasedNodeRenderer` which will generate the necessary HTML for different parts of the HTML
document.

### Emoji Shortcuts

Emoji shortcut rendering requires [emoji-cheat-sheet.com] image file location to be provided for
emoji image URL generation. If the directory is not set then emoji shortcuts will be converted
to GitHub emoji URLs for testing purposes.

### Tables

By default parsing allows more flexible table parsing than allowed by GFM but for rendering
purposes options are set to emulate GFM table parsing.

[Emoji-Cheat-Sheet.com]: http://www.emoji-cheat-sheet.com/
[Markdown]: http://daringfireball.net/projects/markdown
[Markdown Navigator]: http://vladsch.com/product/multimarkdown
[flexmark-java]: https://github.com/vsch/flexmark-java
[flexmark-java extension]: https://github.com/vsch/flexmark-java/wiki/Writing-Extensions
[autolink-java]: https://github.com/robinst/autolink-java
[commonmark-java]: https://github.com/atlassian/commonmark-java
[gfm-tables]: https://help.github.com/articles/organizing-information-with-tables/

