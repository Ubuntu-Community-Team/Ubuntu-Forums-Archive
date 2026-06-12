---
title: "can anyone help....?"
date: 2009-12-01
forum: General Help
---

### Post by b5a4qms on 2009-12-01
i have now tried all major linux os's and the same problem has followed through each. no usb mouse interface with more than one mouse. i have tried gnome, ubuntu 9.10, ubuntu 8.whatever lts, fedora, and demonoid. though with gnome i did get an error message:

error activating xkb configuation.
it can happen under various circumstances:
-a bug in libxklavier library
-a bug in x server (xkbcomp, xmodmap utilities)
-x server with incompatible lebxkbfile implementation

x server version data:
the x.org foundation
10600000

if you report this situation as a bug, pleas include:
the result of Xprop -root | grep xkb 
the result of gconftool-2 -R
/desktop/gnome/peripherals/keyboard/kbd



xprop -root | grep xkb showed:said it was unable to open display. then showed xprop options

gconftool-2-r /desktop/gnome/peripherals/keyboard/kbd showed: 
model = 
options = []
layouts = [en_us.utf-8]



any help would be great. thanks

---

