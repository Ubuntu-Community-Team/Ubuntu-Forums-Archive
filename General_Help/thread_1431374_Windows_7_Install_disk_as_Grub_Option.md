---
title: "Windows 7 Install disk as Grub Option ?"
date: 2010-03-16
forum: General Help
---

### Post by zonemikel on 2010-03-16
Ok i have a windows 7 iso and i want to add it to a partition on my usb hdd so i can install it on computers that dont have cdrom drives. I did it before for my netbook but this is different since the usb hdd has grub and windows already installed on it. 

my usb hdd (as seen from itself)
[PHP]Disk /dev/sdf: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00f200f2

   Device Boot      Start         End      Blocks   Id  System
/dev/sdf1               1        3655    29351616    7  HPFS/NTFS <-win XP part
/dev/sdf2            3656        7296    29246332+   5  Extended
/dev/sdf5            3656        6582    23511096   83  Linux  <-- netbook remix ubuntu
/dev/sdf6            7141        7296     1253038+  82  Linux swap / Solaris
/dev/sdf7   *        6583        7140     4482103+   b  W95 FAT32 <-- 4.7gig for win7 install disk [/PHP]I tried extracting the files to /dev/sdf7 then adding the boot option in my menu.lst 
[PHP]
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title        Microsoft Windows 7 UE install disk
rootnoverify    (hd0,6)
savedefault
chainloader    +1
[/PHP]but i got error 13 invalid or unsupported executable, any ideas ?

---

### Post by Mark Phelps on 2010-03-16
Win7 won't install to anything other than NTFS, so maybe, it won't run from a FAT volume, either.

Would reformat the FAT volume to NTFS, re-extract the files there, and see if that fixes the problem.

---

