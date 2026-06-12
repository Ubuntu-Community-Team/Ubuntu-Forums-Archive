---
title: "XGL/Compiz/Mplayer screen blanking"
date: 2006-06-18
forum: General Help
---

### Post by reuben on 2006-06-18
I can't figure this out; when I play movies using mplayer, the screen blanks every 15 minutes.

I'm running KDE/XGL/Compiz. 

.mplayer/config contains:
vo=xv
stop-xscreensaver=yes

When mplayer starts, it can't even find xscreensaver:

Xlib:  extension "XFree86-VidModeExtension" missing on display ":1.0".
xscreensaver_disable: Could not find XScreenSaver window.
No value set for `/apps/gnome-screensaver/idle_activation_enabled'


In the KDE control center, screensavers are set to not start automatically (they start when I lock the screen.) 

The "Display" module cannot be loaded by the control center, so it's possible that it's a setting in there. Where is the config file for this? 

I'm running gnome-window-decorator with compiz, but I don't think that pulls in gnome screensaver/power-saving options, does it??

---

