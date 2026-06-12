---
title: "What does the command &quot;gedit file.ext 2&gt; /dev/null &amp;&quot; do?"
date: 2012-03-31
forum: General Help
---

### Post by arroy_0209 on 2012-03-31
I have recently installed gedit-latex-plugin (0.2 rc3) with pre-existing gedit (2.30.3). the problem is if I open a tex file with gedit (using command gedit file.ext&), I get many comments, like:
```

DEBUG resources - Initializing resource locating
 DEBUG Preferences - <value key='BibtexExtensions'> not found
DEBUG JobManager - Created JobManager instance 148089836
 DEBUG GeditLaTeXPlugin - activate
DEBUG WindowContext - init
DEBUG GeditWindowDecorator - _init_tab_decorators: initialized 0 decorators
 DEBUG GeditWindowDecorator - active_tab_changed
 DEBUG GeditWindowDecorator - ---------- ADJUST: None
DEBUG GeditWindowDecorator - No window-scope views for this extension
DEBUG GeditWindowDecorator - _set_selected_bottom_view: 0
 DEBUG GeditWindowDecorator - _set_selected_side_view: 0
 DEBUG GeditWindowDecorator - tab_added
 DEBUG GeditTabDecorator - loaded
 DEBUG GeditTabDecorator - _adjust_editor: URI has changed

```
etc.
I do not understand why this happens. However in this forum there is another thread where a user reports the same and there is a suggestion to invoke the gedit command this way:
```
gedit file.ext 2> /dev/null &
``` then no such warning is shown. Can anyone please explain why there are no such comments in the second case? Is there any problem with the gedit-latex-plugin or not? I am confused.

---

### Post by flemur13013 on 2012-03-31
gedit file.ext 2> /dev/null &

"2" is the error output ("STDERR");  doing 

"$ command 2 > file.ext" 

writes the errors and warnings to "file.ext" rather than the terminal. 

When the file is /dev/null (bitbucket), the output is just thrown away.

Edit: it doesn't mean there's no more warnings or errors, you just don't see them (and you can probably ignore them anyway if gedit is working OK). 

Edit2: The "&" just means run the command in background, freeing up the terminal - leaving it off will be fine, too.

---

### Post by lmarmisa on 2012-03-31
This command redirects the [standard error stream]("http://en.wikipedia.org/wiki/Standard_streams") (stderr) to the [null device]("http://en.wikipedia.org/wiki//dev/null"). So, the warnings are ignored.

Best regards,

Luis

---

