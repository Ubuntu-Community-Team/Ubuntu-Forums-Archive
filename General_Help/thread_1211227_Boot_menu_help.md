---
title: "Boot menu help"
date: 2009-07-12
forum: General Help
---

### Post by biggiee on 2009-07-12
I recently installed ubuntu 9.4 64bit. And i was having problems with the 64bit settings so i partitioned the hard drive it was on then installed 9.4 32bit. For some reason the 64bit version is still in the boot menu. Im trying to find a way to remove it but i was woundering if there way to do this without having to unistall my current version of ubuntu

my boot menu looks like

Windows Vista
Ubuntu(64)
Ubuntu(32)

---

### Post by biggiee on 2009-07-12
bump

---

### Post by windy81 on 2009-07-12
im no expert, literlaly 2 days into ubuntu, however

 
```
gksudo gedit /boot/grub/menu.lst
```

allows you to edit the the grub boot menu. if that's any help :)

---

### Post by oldfred on 2009-07-12
If you just do not want to see it in you boot menu and you have standard install:
copy current menu.lst to backup, then edit menu.lst :

sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.backup
gksudo gedit /boot/grub/menu.lst

You can edit the 64 bit version out by adding # signs at the beginning of the lines or delete the lines. If you still have it installed you you may want to keep it to modify settings later. I am booting both but primarily using the 32 bit version now. To totally uninstall you can reformat the partition or delete and reuse the partition.

---

