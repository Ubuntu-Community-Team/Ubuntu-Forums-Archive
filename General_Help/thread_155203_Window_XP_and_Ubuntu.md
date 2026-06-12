---
title: "Window XP and Ubuntu"
date: 2006-04-04
forum: General Help
---

### Post by hdavy2002 on 2006-04-04
HI all,
I have couple of partitions and I deleted my primary partition and installed Ubuntu, I had another primary partition and there was xp installed in it.
This is my fdisk info:

Disk /dev/hda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        3508    28177978+  83  Linux
/dev/hda2            3509        3649     1132582+  82  Linux swap / Solaris
/dev/hda3            3650        5305    13301820    7  HPFS/NTFS
/dev/hda4            5306        7296    15992707+   5  Extended
/dev/hda5            5306        7296    15992676    7  HPFS/NTFS

Now I see my NTFS partition at hda3

I did a change in sudo gedit /boot/grub/menu.lst as:

title        Microsoft Windows XP Home Edition
root (hd0,3)
savedefault
makeactive
chainloader +1


But it gives me some error when i access it via grub loader.

Please help, i have spent hours trying to install programs in windows, and i dont want to reinstall all over again. I now know windows like primary partition. Is there any way out.

---

### Post by croak77 on 2006-04-04
(hd0,3) is for /dev/hda4
(hd0,2) is for /dev/hda3

Try changing to root (hd0,3) to root (hd0,2)

---

