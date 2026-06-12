---
title: "DBAN/GParted/OS modification master help"
date: 2009-08-21
forum: General Help
---

### Post by matessim on 2009-08-21
So,Ubuntu Forums community:
Im looking into something like this, i want a Bootable "OS" of a sort, like DBAN/GParted to be installed on a partition, and have a password for booting it, i want it to be in the grub entry, so once i enter the password DBAN/GParted/Any tool you recommend will make a ramdisk, and zero the drive.
i hope it doesn't sounds too far fetched and i explained it well, can anyone help me with this?
so what i need
1:"Install" one of those live CD's, or some tool you guys know
2: Modifying it to the point that all i need to do is enter a password when i boot off it, and it Start's zeroing the HD

---

### Post by matessim on 2009-08-22
Ok so i found this
```
title   DBAN 1.0.7
root    (hd0,0)
kernel  /dban.bzi nuke="dwipe --autonuke"
initrd  /initrd.gz
boot
```
problem is i'm not sure it would work because, depending on the partition DBAN is located, it might destroy itself before everything wipes, or does it make a ramdisk automatically?.

anyway, is there anyway i can add a password? anyone know of?

---

