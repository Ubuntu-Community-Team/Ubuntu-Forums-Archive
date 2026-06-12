---
title: "avant wiindows navigator(AWN) problem"
date: 2010-11-03
forum: General Help
---

### Post by konjeng on 2010-11-03
i can't open AWN from the icon
when i open from the terminal and try to go to "Dock Preference" or "About Awn" the following gets displayed at the terminal



sudo avant-window-navigator
Screen is composited
** (avant-window-navigator:2610): DEBUG: Updating gtk theme colours
** (avant-window-navigator:2610): DEBUG: Updating dialog colours
** (avant-window-navigator:2610): DEBUG: Spawned awn-applet[2615] for "quick-prefs.desktop", UID: 1, XID: 85983277
** (avant-window-navigator:2610): DEBUG: Spawned awn-applet[2617] for "taskmanager.desktop", UID: 3, XID: 85983278

(awn-applet:2617): GLib-CRITICAL **: g_dir_read_name: assertion `dir != NULL' failed

(awn-applet:2617): GLib-CRITICAL **: g_dir_close: assertion `dir != NULL' failed
Applet [1] flags: 1024: DockletHandlesPositionChange 
Awn Settings can't be run as root.
Awn Settings can't be run as root.
Applet [1] flags: 1024: DockletHandlesPositionChange 

(awn-applet:2617): Wnck-WARNING **: Property _NET_WM_VISIBLE_NAME contained invalid UTF-8


(awn-applet:2615): Wnck-WARNING **: Property _NET_WM_VISIBLE_NAME contained invalid UTF-8


(awn-applet:2615): Wnck-WARNING **: Property _NET_WM_VISIBLE_NAME contained invalid UTF-8


(awn-applet:2617): Wnck-WARNING **: Property _NET_WM_VISIBLE_NAME contained invalid UTF-8

Awn Settings can't be run as root.
Awn Settings can't be run as root.
Awn Settings can't be run as root.
 



please Help!!!!!



Thanking in anticipation :)

---

### Post by janpol on 2010-11-03
> **konjeng said:**
> 
Awn Settings can't be run as root.
Awn Settings can't be run as root.
Awn Settings can't be run as root.


Have you tried to open it from the terminal as a normal user?

```
avant-window-navigator
```

---

### Post by sikander3786 on 2010-11-03
sudo is not needed for running user owned tasks from the terminal as mentioned by janpol above. Thats what it is clearing statis in the error messages.

> Awn Settings can't be run as root.
Awn Settings can't be run as root.

Try running it without sudo and post back the error messages encountered.

---

### Post by konjeng on 2010-11-04
i have tried but it says another instance of awn is running. But i don't find it running
it get's displayed like this


avant-window-navigator

** (avant-window-navigator:2077): WARNING **: Another instance of Awn is running

---

### Post by kirkface8 on 2010-11-04
```
killall avant-window-navigator
```

then

```
avant-window-navigator
```

that should work

---

### Post by konjeng on 2010-11-04
I can kill the process but when i start awn again the following error occur and the error occurs indefinitely

 

killall avant-window-navigator
brolie@brolie-laptop:~$ avant-window-navigator
Screen is composited
** (avant-window-navigator:3672): DEBUG: Updating dialog colours
** (avant-window-navigator:3672): DEBUG: Spawned awn-applet[3673] for "quick-prefs.desktop", UID: 1, XID: 58720301
** (avant-window-navigator:3672): DEBUG: Spawned awn-applet[3675] for "taskmanager.desktop", UID: 3, XID: 58720302
** (avant-window-navigator:3672): DEBUG: Spawned awn-applet[3676] for "cairo-menu.desktop", UID: 1288804054, XID: 58720303
** (avant-window-navigator:3672): DEBUG: Spawned awn-applet[3677] for "showdesktop.desktop", UID: 1288804064, XID: 58720304
** (avant-window-navigator:3672): DEBUG: Spawned awn-applet[3678] for "media-player.desktop", UID: 1288804110, XID: 58720305

(awn-applet:3675): Gdk-CRITICAL **: gdk_region_rect_in: assertion `region != NULL' failed

(awn-applet:3675): Gdk-CRITICAL **: gdk_region_rect_in: assertion `region != NULL' failed

(awn-applet:3675): Gdk-CRITICAL **: gdk_region_rect_in: assertion `region != NULL' failed

(awn-applet:3675): Gdk-CRITICAL **: gdk_region_rect_in: assertion `region != NULL' failed

(awn-applet:3675): Gdk-CRITICAL **: gdk_region_rect_in: assertion `region != NULL' failed

(awn-applet:3675): Gdk-CRITICAL **: gdk_region_rect_in: assertion `region != NULL' failed

(awn-applet:3675): Gdk-CRITICAL **: gdk_region_rect_in: assertion `region != NULL' failed

(awn-applet:3675): Gdk-CRITICAL **: gdk_region_rect_in: assertion `region != NULL' failed

---

