---
title: "Error activating XKB configuration"
date: 2010-12-31
forum: General Help
---

### Post by zcrself on 2010-12-31
Error activating XKB configuration
It can happen under various circumstances:
- a bug in libxklavier library
- a bug in X server (xkbcomp, xmodmap utilities)
- X server with incompatible libxkbfile implementation

Xserver version data:
The X.Org Foundation
10300000

If you report this situation as a bug, please include:
- The result of xprop -root | grep XKB
- The result of gconftool-2 -R /desktop/gnome/peripherals/keyboard/kbd


[COLOR=Blue]**how to solve this problem?**[/COLOR]

---

### Post by zcrself on 2010-12-31
ncgr@ncgr-desktop:~$ gconftool-2 -R /desktop/gnome/peripherals/keyboard/kbd
 layouts = []
 overrideSettings = true
 options = []
 model =
ncgr@ncgr-desktop:~$  gconftool-2 -R /desktop/gnome/peripherals/keyboard/kbd
 layouts = []
 overrideSettings = true
 options = []
 model =

---

### Post by zcrself on 2010-12-31
ncgr@ncgr-desktop:~$ xprop -root | grep XKB
xprop:  unable to open display ''
usage:  xprop [-options ...] [[format [dformat]] atom] ...

where options include:
    -grammar                       print out full grammar for command line
    -display host:dpy              the X server to contact
    -id id                         resource id of window to examine
    -name name                     name of window to examine
    -font name                     name of font to examine
    -remove propname               remove a property
    -set propname value            set a property to a given value
    -root                          examine the root window
    -len n                         display at most n bytes of any property
    -notype                        do not display the type field
    -fs filename                   where to look for formats for properties
    -frame                         don't ignore window manager frames
    -f propname format [dformat]   formats to use for property of given name
    -spy                           examine window properties forever

---

