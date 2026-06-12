---
title: "Setxkbmap vs Gnome Keyboard"
date: 2010-06-14
forum: General Help
---

### Post by Kzintee on 2010-06-14
I'm trying to setup my Belkin PS/2 ergo keyboard (F8E208-BLKSN PS/2).
The setup works great in Gnome keyboard layout manager, I can pick the russian phonetic layout, the keyboard shows up as generic pc105 (intl), and everything works fine, cursor keys and all.
However, using the same exact options does not work with setxkbmap...running 
setxkbmap -rules xfree86 -model pc105 -layout "us, ru" -option "grp:alt_shift_toggle" provides russian layout but cursor keys stop working. What is Gnome doing that's different in the layout from setxkbmap?

Edit:
setxkbmap -print prints out the gnome configuration. After that, edit the xorg.conf file according to the HOWTO. I used the Direct XKB syntax that is literally copy and paste from setxkbmap -print output.

---

