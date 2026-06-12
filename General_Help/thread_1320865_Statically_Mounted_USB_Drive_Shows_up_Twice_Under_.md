---
title: "Statically Mounted USB Drive Shows up Twice Under Media"
date: 2009-11-09
forum: General Help
---

### Post by swordphsh on 2009-11-09
I just upgraded to 9.10 and have an external usb drive which is always connected to my laptop. I have it set in fstab to statically mount at /media/MyBook, but in 9.10 it is showing up twice under connected media and places. One is showing the orange USB drive icon and the other is showing the standard drive icon. Previous to 9.10, ubuntu would simply mount it and show the orange usb drive icon. 

If I remove the fstab option, the only shows the usb icon, but will not automount (I have usb automount disabled, hence the fstab entry).

---

### Post by mshpkh on 2009-11-09
I have exactly the same problem.  Any help would be appreciated.

---

### Post by swordphsh on 2009-11-11
I did a little more research and it is a bug in the gnome-vfs.

[https://bugs.launchpad.net/ubuntu/+source/gnome-vfs2/+bug/42017]("https://bugs.launchpad.net/ubuntu/+source/gnome-vfs2/+bug/42017")

---

