---
title: "help"
date: 2009-07-29
forum: General Help
---

### Post by cowboy7305 on 2009-07-29
i have a external hard drive it shows up on my desktop as being mounted ,when i want to put any files in it it tells me i do not have permission to put files in it there is also a file in it called lost+found /media/disk/lost+found it has a little envelope at the side of it and i cant open this file ether,how do i get this drive to work 
many thanks

---

### Post by michy99 on 2009-07-29
First of all, what type of filesystem is on the drive? Can you post the output of these commands?```
sudo fdisk -l
df -h
cat /etc/fstab
```

---

### Post by cowboy7305 on 2009-07-29
Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd0f4738c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       60046   482319463+  83  Linux
/dev/sda2           60047       60801     6064537+   5  Extended
/dev/sda5           60047       60801     6064506   82  Linux swap / Solaris

Disk /dev/sdb: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x1c1d1c1d

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       14593   117218241   83  Linux
 
Its the 120 gig drive i want as external

---

