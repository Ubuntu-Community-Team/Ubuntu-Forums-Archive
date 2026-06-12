---
title: "Corrupted boot map?"
date: 2010-12-09
forum: General Help
---

### Post by shaolintl on 2010-12-09
My kubuntu 10.10 fails to start due to "unable to mount" /dev /sys etc.
when loading a live cd:

running fdisk -l, i get

Device    Boot Start   End  Blocks   Id  System
/dev/sda1      1       1    2047+    ee  GPT
/dev/sda2 *    1       9328 74920960 83  Linux
/dev/sda3      9328    9730 3227648  82  Linux swap / Solaris

umount /dev/sda2 tells me the device is not mounted but fsck /dev/sda2 says:
Device or resources busy while trying to open /dev/sda2
Filesystem mounted or opened exclusively by another program?

Is it possible to solve it or to access the data on the device?

What can cause it? It seems the OS tried to suspend or hibernate and had this crash.

Thanks,
Tomer

---

