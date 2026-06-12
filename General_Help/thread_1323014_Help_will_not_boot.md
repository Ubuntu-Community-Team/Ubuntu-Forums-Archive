---
title: "Help will not boot"
date: 2009-11-11
forum: General Help
---

### Post by tatmark1 on 2009-11-11
I am having a problem booting into ubuntu. It worked fine yesterday..
i am getting /dev/disk/by-uuid/xxxxxx....ect does not exist
I am running 9.10 dual boot with vista on dual hard drives.
on live cd right now. i hope some one can help me. thanks

---

### Post by tatmark1 on 2009-11-11
to the top..help please

---

### Post by tatmark1 on 2009-11-11
Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xdefd3c49

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       47746   383518368+   7  HPFS/NTFS
/dev/sda2           47746       54273    52428800    7  HPFS/NTFS
/dev/sda3           54273       60802    52436992    7  HPFS/NTFS

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00023388

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       29265   235071081   83  Linux
/dev/sdb2           29266       30401     9124920    5  Extended
/dev/sdb5           29266       30401     9124888+  82  Linux swap / Solaris

---

### Post by tatmark1 on 2009-11-11
think it is fixed..
 i went into edit in grub and changed the uuid to the harddrive where ubuntu is installed in my case sdb1 and now i can boot. 
 is this the right way or will this cause me problems?

---

