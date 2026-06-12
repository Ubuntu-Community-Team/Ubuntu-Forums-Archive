---
title: "Wacom P&amp;T and Virtual Box problems"
date: 2010-11-18
forum: General Help
---

### Post by Bromden on 2010-11-18
Hi all, I'm sorry but I can't find a way to solve 2 common problems. I'm using Ubuntu 10.10
The first problem concerns my Wacom Pen & Touch. The pen seems to work well, but the touch is very "laggy". It recognizes some multitouch moves, but it stops receiving signals frequently.

I've read these topics about a touch's bug:
[http://ubuntuforums.org/showpost.php?p=9675615&postcount=110](http://ubuntuforums.org/showpost.php?p=9675615&postcount=110)

I've modified the file into the folder needed to install/compile the drivers, i've made "make install" but nothing is changed...

I've also put the toggle-touch.sh files in my home but they're useless (i've assigned them to hotkeys, but their activation don't influence my wacom)...#-o

I would like to try the GUI configuration, but i don't know where i can find it...i don't even know if it's installed 



As for VirtualBox, i can't realize how to share folders or setting up USB...i'm pretty sure it isn't the Open Source version, so it must have all the needed functions.
I've activated the USB from settings, i've put the filter for my USB Pen, but when i try to use it in XP, all VB's options are grey, so i can't select it.

---

### Post by Bromden on 2010-11-19
Ok i've solved the USB problem with Virtual Box...i had only to do this permission passage:
Administration-->Users and Groups-->Manage Groups-->vboxusers-->properties-->check user box

The problem with Wacom tablet still persists...i'm gonna resintall ubuntu since i've messed up my xorg file (and as every respected noob would do, i've no back up copies XD), i hope it will solve all my problems...

---

