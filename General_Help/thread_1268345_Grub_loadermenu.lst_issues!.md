---
title: "Grub loader/menu.lst issues!"
date: 2009-09-16
forum: General Help
---

### Post by smithpercussion on 2009-09-16
Hello, I installed Windows XP on a partition next to Ubuntu (for the family to use). I got rid of the Windows Bootloader and reinstalled grub. That went quite smoothly.

My current situation is that I cannot figure out what to tell my menu.lst to point to in order to find windows. The partition is NTFS format

The following is my output from fdisk -l

```
Disk /dev/sda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x46174617

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        6390    51327643+  83  Linux
/dev/sda2            6391       11661    42339307+   7  HPFS/NTFS
/dev/sda3           11662       12161     4016250    5  Extended
/dev/sda5           11662       12161     4016218+  82  Linux swap / Solaris

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00052600

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       30401   244196001   83  Linux

```

Here was my latest attempt

```
title              Windows XP
root               (hd0,0)
savedefault
makeactive
map                (hd0) (hd0)
chainloader        +1

```

Any ideas?
Thanks in advance!

---

