HTML Override

This is a custom module enabled on it which allows site administrators to designate specific node types as eligible to have the code in their body fields override the site’s theme.

This means that one-off special pages can be published using Drupal’s standard content management system and all the editorial tools and workflows present in it:  roles, permissions, revision control, and even search indexing.

The module has a single configuration page on which the user can set the content types which have the option to override the theme.  Nodes utilizing this option use whatever code has been added to the body field as the entirety of the HTML page served to the browser.

On the node edit forms for the designated content types, a checkbox now appears under the body field which, when checked, forces the display of the node to bypass Drupal’s theming system.

To use css and javascript files, simply use any file field attached to the node and upload them.  Once uploaded, they can be referenced in the normal ways (e,g: <link rel=”stylesheet” href=”path/to/files.css”>), with one exception and two caveats.  

The exception is that Drupal renames uploaded files which have a .js extension by appending a .txt extension.  Referencing these files using the txt extension does not affect their functionality:  
<script type="text/javascript" src="path/to/test.js.txt"></script>  

The first caveat is that file upload fields often have specific directories configured into which the uploaded files will be put.  Make sure to verify the paths of uploaded files before using them within the HTML of the body fields on nodes which will override the theme.  This can be done by “right-clicking” the uploaded files and choosing to copy the URL to the file.  Use that URL within your HTML.

The second caveat is that it’s best to use fully qualified URLs in your references to uploaded files in order to avoid problems caused by mismatches between url paths and relative URLs to referenced files:

<link rel="stylesheet" href="sites/default/files/file.css"> 

will fail if the path alias for the node is set to my/overridden/node so it’s better to use 

<link rel="stylesheet" href="http://mysite.com/sites/default/files/file.css">

Finally, for settings to take effect, sometimes the caches will need to be cleared.  The module will attempt to present a link to the user to do this, and this link can also always be found on the configuration page.

