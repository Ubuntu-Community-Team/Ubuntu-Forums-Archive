---
title: "gedit-latex-plugin shows annoying &quot;DEBUG&quot; messages"
date: 2010-11-25
forum: General Help
---

### Post by haugh on 2010-11-25
After installing gedit-latex-plugin, gedit outputs a bunch of debug messages when started from the terminal.

*Does anyone know how to get rid of the output?*  I want to keep the plugin, and it seems to work fine.

gedit-latex-plugin: version 0.2 rc3
gedit: version 2.30.3
ubuntu: version 10.10

```

$ gedit
2010-11-25 16:17:04,801 DEBUG resources - Initializing resource locating
2010-11-25 16:17:04,854 DEBUG Preferences - <value key='BibtexExtensions'> not found
2010-11-25 16:17:04,865 DEBUG JobManager - Created JobManager instance 30662096
2010-11-25 16:17:04,868 DEBUG GeditLaTeXPlugin - activate
2010-11-25 16:17:04,868 DEBUG WindowContext - init
2010-11-25 16:17:04,921 DEBUG GeditTabDecorator - No file loaded
2010-11-25 16:17:04,921 DEBUG GeditWindowDecorator - ---------- ADJUST: None
2010-11-25 16:17:04,923 DEBUG GeditWindowDecorator - No window-scope views for this extension
2010-11-25 16:17:04,923 DEBUG GeditWindowDecorator - _set_selected_bottom_view: 0
2010-11-25 16:17:04,923 DEBUG GeditWindowDecorator - _set_selected_side_view: 0
2010-11-25 16:17:04,923 DEBUG GeditWindowDecorator - _init_tab_decorators: initialized 1 decorators

```

---

### Post by LucasMB on 2010-12-03
I have the same issue. Using Ubuntu 10.04, gedit 2.30.3.
I guess the plugin is in test mode (alpha I think, version 0.2).
No idea how to disable that output.

---

### Post by hiromato on 2010-12-03
This seems to be a bug that has now been fixed in package gedit-latex-plugin - 0.2.0-1. Se below:

[https://bugs.launchpad.net/ubuntu/+source/gedit-latex-plugin/+bug/584462]("https://bugs.launchpad.net/ubuntu/+source/gedit-latex-plugin/+bug/584462")

---

### Post by chandra on 2011-02-01
> **haugh said:**
> 
*Does anyone know how to get rid of the output?*

Try invoking gedit from the command line. If the file you want to edit is called file.ext, you should type:

```
gedit file.ext 2> /dev/null &
```

This re-directs the STDERR pipe denoted by 2> to never-neverland denoted by /dev/null and backgrounds the process with the ampersand.

Please do let me know if this does not work for you, because it does for me.

HTH.

---

