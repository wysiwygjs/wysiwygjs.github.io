Example:
==========
**http://wysiwygjs.github.io/**

wysiwyg.js
==========

'wysiwyg.js' is a (minified) 12k contenteditable-editor with no dependencies.
It does only:
* Transforms any HTML-element into contenteditable
* onselection-event: e.g. to open a toolbar
* onkeypress-event: e.g. to handle hotkeys
* onplaceholder-event: show/hide a placeholder

It works with:
* Internet Explorer 6+
* Firefox 3.5+
* Chrome 4+
* Safari 3.1+

If a &lt;textarea&gt; was used as 'element', the library:
* keeps the &lt;textarea&gt; in sync
* falls back to the &lt;textarea&gt; if the browser does not support 'contenteditable'
* Old iOS and Android 2.3- degrade to &lt;textarea&gt;

There is also a (minified) 9k jQuery-plugin '$.wysiwyg()' to create
a full-featured editor which depends on:
* wysiwyg.js
* jQuery
* FontAwesome (or PNG images)

wysiwyg.js-API:
==========
````
// create wysiwyg:
var wysiwygeditor = wysiwyg({
    element: document.getElmentById('editor-id'),
    onkeypress: function( code, character, shiftKey, altKey, ctrlKey, metaKey ) {
        },
    onselection: function( collapsed, rect, nodes, rightclick ) {
        },
    onplaceholder: function( visible ) {
        },
    hijackcontextmenu: false
});

// properties:
wysiwygeditor.getElement();
wysiwygeditor.getHTML(); -> 'html'
wysiwygeditor.setHTML( html );
wysiwygeditor.getSelectedHTML(); -> 'html'|false

// selection and popup:
wysiwygeditor.collapseSelection();
wysiwygeditor.openPopup(); -> popup-handle
wysiwygeditor.closePopup();

// exec commands:
wysiwygeditor.markup( styleWithCSS, insertBrOnReturn );
wysiwygeditor.removeFormat();
wysiwygeditor.bold();
wysiwygeditor.italic();
wysiwygeditor.underline();
wysiwygeditor.strikethrough();
wysiwygeditor.forecolor( '#color' );
wysiwygeditor.highlight( '#color' );
wysiwygeditor.fontName( fontname );
wysiwygeditor.fontSize( fontsize );
wysiwygeditor.subscript();
wysiwygeditor.superscript();
wysiwygeditor.align( 'left'|'center'|'right'|'justify' );
wysiwygeditor.format( tagname );
wysiwygeditor.insertLink( 'http://url.com/' );
wysiwygeditor.insertImage( 'http://url.com/' );
wysiwygeditor.insertHTML( 'html' );
wysiwygeditor.insertList( ordered );
````

$.wysiwyg()-API:
==========
````
var $editor = $('#editor').wysiwyg({
    placeholder: 'Type your text here...',
    position: 'selection'|'top'|'top-selection'|'bottom'|'bottom-selection',
    buttons = { ... },
    submit = { ... },
    smilies = { ... },
    dropfileclick: 'Click or drop image',
    styleWithCSS: false,
    insertBrOnReturn: false,
    placeholderUrl: 'www.example.com',
    clipImage: [width,height] | false,
    clipSmiley: [width,height] | false,
    onImageUpload: function( insert_image ),
    onEnterSubmit: function()
})
.focus(function(){})
.blur(function(){})
.change(function(){});
$editor.wysiwyg('html');
$editor.wysiwyg('html','new html');
$editor.wysiwyg('bold');
$editor.wysiwyg('italic');
$editor.wysiwyg('underline');
$editor.wysiwyg('strikethrough');
$editor.wysiwyg('forecolor','#color');
$editor.wysiwyg('highlight','#color');
$editor.wysiwyg('alignleft');
$editor.wysiwyg('aligncenter');
$editor.wysiwyg('alignright');
$editor.wysiwyg('alignjustify');
$editor.wysiwyg('subscript');
$editor.wysiwyg('superscript');
$editor.wysiwyg('format', tagname );
$editor.wysiwyg('indent');
$editor.wysiwyg('outdent');
$editor.wysiwyg('orderedlist');
$editor.wysiwyg('unorderedlist');
$editor.wysiwyg('insertlink','http://url.com/');
$editor.wysiwyg('insertimage','http://url.com/');
$editor.wysiwyg('inserthtml','html');
$editor.wysiwyg('removeformat');
````
