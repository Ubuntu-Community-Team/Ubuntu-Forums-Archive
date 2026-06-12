---
title: "How to enable Ctrl + Alt + Backspace in Xubuntu 12.04?"
date: 2012-07-07
forum: General Help
---

### Post by lethalfang on 2012-07-07
The way to enable it in Ubuntu doesn't work in Xubuntu. 
There is no "keyboard layout" in Xubuntu 12.04.

---

### Post by Toz on 2012-07-07
There are a number of ways to do this. 

1. According to: [https://wiki.ubuntu.com/XorgCtrlAltBackspace/]("https://wiki.ubuntu.com/XorgCtrlAltBackspace/"), Ctrl+Alt+Backspace was replaced with AltGR-Sysreq-K (I believe AltGr would be the Right Alt key).

2. The command "setxkbmap -option terminate:ctrl_alt_bksp" should re-enable it. You can add this command to your startup apps or to **~/.xprofile** (if the file doesn't exist, create it. Also make sure its executable). But this is not a system-wide change - only for the user that has this set.

3. As root, create the file **/usr/share/X11/xorg.conf.d/2-dontzap.conf** with the following content:
```
Section "ServerFlags"
  Option "DontZap" "false"
EndSection
```
(note: you'll need to restart X for this to take effect.)

---

