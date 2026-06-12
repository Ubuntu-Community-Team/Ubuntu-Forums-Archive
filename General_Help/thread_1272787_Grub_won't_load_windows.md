---
title: "Grub won't load windows"
date: 2009-09-22
forum: General Help
---

### Post by woopud on 2009-09-22
I installed Ubuntu and now it won't load Windows XP, this is my sudo fdisk -l


Disk /dev/sda: 20.0 GB, 20020396032 bytes
255 heads, 63 sectors/track, 2434 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x68c268c2

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1165     9357831   83  Linux
/dev/sda2            1287        2433     9212805    7  HPFS/NTFS
Partition 2 does not end on cylinder boundary.
/dev/sda3            1166        1286      971932+   5  Extended
/dev/sda5            1166        1286      971901   82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdb: 20.0 GB, 20020396032 bytes
240 heads, 63 sectors/track, 2586 cylinders
Units = cylinders of 15120 * 512 = 7741440 bytes
Disk identifier: 0x0009f29a

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        2585    19542568+   7  HPFS/NTFS

---

### Post by Darkwing-Duck on 2009-09-22
Okay, sounds like you will also need to restore GRUB. You can find some good instructions here: [http://gwos.org/udsf/doku.php/core:grub:restore](http://gwos.org/udsf/doku.php/core:grub:restore)

---

### Post by c0mput3r_n3rD on 2009-09-22
Did you defragment winblows 10 or 15 times before installing Ubuntu?

---

### Post by woopud on 2009-09-22
Only reason I need Windows is for Chief Architect.

---

