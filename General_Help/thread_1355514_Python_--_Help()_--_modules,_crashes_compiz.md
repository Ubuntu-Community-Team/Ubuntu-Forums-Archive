---
title: "Python -- Help() -- modules, crashes compiz"
date: 2009-12-15
forum: General Help
---

### Post by sanubie on 2009-12-15
For some reasons, when I run Python 2.6.4, or invoke 2.6.4 from the command line, it crashes when trying to access the help() function for modules. The screen goes blank momentarily and everything starts back up. Then I when it comes back and I close out the terminal everything vanishes (all screens go away). Then it starts back and everything is fine. Modules is the only one that crashes it. It generates "topics" and "keywords" but modules makes it spit out the following.

Here's what it says: 

```
Please wait a moment while I gather a list of all available modules...

 * Detected Session: gnome
 * Searching for installed applications...
 * No GLX_EXT_texture_from_pixmap with direct rendering context
 ... present with indirect rendering, exporting: LIBGL_ALWAYS_INDIRECT=1
 * Starting Compiz
 ... executing: compiz.real --replace --sm-disable --ignore-desktop-hints ccp --indirect-rendering
compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format
```

I tried Python3.1 and it generated the list of modules without crashing. Any ideas?

---

