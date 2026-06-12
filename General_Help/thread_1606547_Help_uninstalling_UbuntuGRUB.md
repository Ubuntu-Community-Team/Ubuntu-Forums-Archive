---
title: "Help uninstalling Ubuntu/GRUB"
date: 2010-10-26
forum: General Help
---

### Post by Jmclark on 2010-10-26
Okay, so I'm trying to uninstall Ubuntu and GRUB from my Dell Latitude 2110, which is being dual booted with Windows 7. The only problem that I'm running into here, is that it is a "special" copy of Windows 7, with a bunch of restrictions and stuff on it, since it's one I got from my school. Mainly, I can't run anything from it (including .exe files). So basically, I don't want to touch that at all, and don't want anything to happen where I can't access it.

So how would I go about uninstalling Ubuntu and GRUB, returning it to the Windows 7 bootloader, without touching any of the files on the Windows 7 partition at all?

---

### Post by requeth on 2010-10-26
To delete ubuntu completely you can go into windows partition manager and delete the partitions. Then you can reappropriate the disk space into windows if you like, or leave the disk space available for future use with Linux.

When Linux installs and is dual booting with Windows, both Linux and GRUB won't touch the windows partitions. Windows leaves sector 0 as the master boot record which points to the windows partition. Linux stays on it's own partition and GRUB overwrites the windows MBR, but doesn't touch the windows partition.

To get rid of the GRUB MBR you can do one of two things:

1. If your computer happens to have a floppy drive you can find someone with an old windows startup disk and run fdisk.exe /mbr          You can usually download fdisk and probably run it on a USB key too, but I havn't done it.

2. Follow these directions if you have the windows CD: [http://www.ehow.com/how_4836283_repair-mbr-windows.html](http://www.ehow.com/how_4836283_repair-mbr-windows.html)

---

