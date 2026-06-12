---
title: "Automatic mounting stopped"
date: 2006-02-14
forum: General Help
---

### Post by LeSkip on 2006-02-14
I don't quite understand how automatic mounting is supposed to work in Ubuntu. Previously, whenever I inserted a USB memory or external hard drive, it automatically appeared on the desktop as "x MB Volume".

This stopped a while back, and I can't quite understand why. I can still mount the disks manually, but how do I get automounting back up and running?

---

### Post by LeSkip on 2006-02-15
Okay, so I did a little more research this morning, and found out that it is gnome-volume-manager that is supposed to mount my devices, so I ran it manually on the console. For my two devices, a USB hard disk and a USB flash memory I get

manager.c/1619: New Device: /org/freedesktop/Hal/devices/storage_model_0M9AT00
manager.c/1642: not a mountable volume: /org/freedesktop/Hal/devices/storage_model_0M9AT00

and

manager.c/1619: New Device: /org/freedesktop/Hal/devices/storage_model_Cruzer_Micro
manager.c/1642: not a mountable volume: /org/freedesktop/Hal/devices/storage_model_Cruzer_Micro

I also found out that pmount mounts under /media, so when I run

pmount /dev/sda1

it does mount correctly!

So why won't gnome-volume-manager mount my devices?

Skip

---

### Post by newuser111 on 2006-02-15
do this sudo gpasswd -a <username> plugdev

---

### Post by LeSkip on 2006-02-15
[QUOTE=newuser111]do this sudo gpasswd -a <username> plugdev[/QUOTE]

Thanks for the tip, but it didn't do the trick. I  still get the same message that they are not mountable devices.

Any other ideas? Should I put something in fstab?

---

