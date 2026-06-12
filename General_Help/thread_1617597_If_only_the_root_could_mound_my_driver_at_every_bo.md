---
title: "If only the root could mound my driver at every boot?"
date: 2010-11-09
forum: General Help
---

### Post by Muskiet on 2010-11-09
I'm running Ubuntu 10.04 and have a 1.5 TB external hard drive (Seagate FreeAgent) hooked up to a USB port which I use for back-ups and such stuff.
I hardly ever reboot my computer (usually only when updates demand it) but when I do I need to manually mount this hard drive.
Since it can only be done by the root user I use "sudo gparted"  from the terminal to do that, but I'd like to know if there is a way to have Ubuntu do it automatically at every reboot?

edit: Yeah... I'm tired... it should read "If only the root could mount my drive at every boot?"

---

### Post by sohlinux on 2010-11-09
you should be able to mount the usb drive at boot by simply adding it to the /etc/fstab file. if you dont like to edit your fstab you can use a program like mountmanager which you will find in the software center.

---

### Post by Muskiet on 2010-11-09
MountManager works great.
Thanx!

---

### Post by WorMzy on 2010-11-09
Please note that you should use gksu or gksudo for graphical applications, NOT sudo. It doesn't matter so much for gparted, but it's worth baring in mind. :)

Also, you shouldn't need to use gparted to mount things; nautilus' "Places" sidebar should do the job perfectly well.

---

### Post by sohlinux on 2010-11-09
> **Muskiet said:**
> MountManager works great.
Thanx!

glad to hear it :)

---

