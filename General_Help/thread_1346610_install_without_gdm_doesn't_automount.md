---
title: "install without gdm doesn't automount"
date: 2009-12-05
forum: General Help
---

### Post by cong06 on 2009-12-05
I'm doing a regular install without gdm, to try and save memory for the computers.
It seems that in some obscure way gdm is connected to gnome-volume-manager, because I can't figure out why my usb removable disks won't automount anymore.

Just to test to make sure that it was the uninstalled gdm, and not something else, I reinstalled gdm, and automounting returned.

gnome-volume-manager is in the startup programs as:
```

/usr/lib/gnome-volume-manager/gnome-volume-manager --sm-disable

```

gdm is startign to seem more important then [I thought](http://ubuntuforums.org/showthread.php?t=1343831).

---

### Post by audiomick on 2009-12-05
Don't know if it is relevant or not, but I think I read recently that Gnome and Nautilus are very closely interdependant.

---

### Post by cong06 on 2009-12-09
ok. Lets try a different approach. If gnome-volume-manager doesn't do it, what do KDE use? what about Xubuntu?
There has to be other autmounters out there then just the gnome one.

---

