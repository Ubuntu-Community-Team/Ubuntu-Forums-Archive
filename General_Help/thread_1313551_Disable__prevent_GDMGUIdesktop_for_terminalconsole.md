---
title: "Disable / prevent GDM/GUI/desktop for terminal/console/text  only boot in ubuntu 9.10"
date: 2009-11-03
forum: General Help
---

### Post by terrox on 2009-11-03
Upgraded from Xubuntu 9.04 which I had set up gdm (the GUI) not auto-starting on purpose.
Now in 9.10 I can't disable gdm. I tried bum, xcconf, rcS.d, run level 3 & a few other things. Can't seem to get it to stop loading the desktop automatically. I just want the command line because I use it mostly as a web server and print server, sometimes I need the desktop - but i don't want all the xserver desktop stuff slowing down the bootup time or taking up RAM and CPU.

I'd like a grub option to set, that would be by far the easiest because I could just choose what mode to use on boot up. But whatever works in 9.10 is good.

---

### Post by lordbinky on 2009-11-09
I am having this same problem for an NFS debootstrap build.  I tried removing it from startup and even deleted /etc/init.d/gdm.  I cannot prevent it from starting.  It keeps coming back!  lol

---

### Post by lordbinky on 2009-11-09
I was able to uninstall gdm without effecting any of the other applications I have installed (apt-get remove gdm).  I am not sure if this is helpful to you.  When you need X, simply running startx will bring up the graphical interface.

---

