---
title: "How should I install programs that don't have packages or makefiles."
date: 2011-12-18
forum: General Help
---

### Post by blindley on 2011-12-18
I just started using Ubuntu yesterday.  I installed the Blender package from the Ubuntu software center.  When I realized it was version 2.49, I promptly uninstalled it and went to the Blender website to get 2.6.  Now, it doesn't come with any kind of configure, or make files.  It's just a folder with the program and associated files.

Where exactly should I put it?  What I did was move the folder to /usr/local/bin and made a link to the program itself and moved it to the parent /usr/local/bin .  That works, and allows me to run blender from the command line.

Is that the standard way to do it?  Is there a standard way to do it?  Also, how to I get it to the applications menu under graphics?

---

### Post by gandaran on 2011-12-18
> Is that the standard way to do it? Is there a standard way to do it? Also, how to I get it to the applications menu under graphics?
use the main menu application to create a menu shortcut launcher
the launch command is just the full path to the blender executable file.
and if you are on ubuntu 11.10 unity then you can add the launcher to the side panel.

---

