---
title: "Internal drive not showing up"
date: 2009-11-11
forum: General Help
---

### Post by vorbroker on 2009-11-11
My Laptops internal hard drive is not showing up. All that shows up is

-250 GB Hard Disk: System Reserved
-320 GB Hard Disk: Simple Drive     ---This is my external Hard Drive
-cdrom0
-Filesystem                        ---This is Ubuntu

The 250 GB Hard Disk is what im looking for. But when I click on that icon it only has

-Boot  
-bootmgr  
-BOOTSECT.BAK  
-NST  
-System Volume Information

Im not sure if i messed it up or something...i have already messed up a lot of stuff already......if i right click and go to properties it only shows like 35MB

Any help would be very nice :)

---

### Post by michy99 on 2009-11-11
What output do you get for```
sudo fdisk -l
```

---

### Post by vorbroker on 2009-11-11
Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x78744461

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          13      102400    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2              13       30402   244093952   17  Hidden HPFS/NTFS

Disk /dev/sdb: 40.0 GB, 40027029504 bytes
255 heads, 63 sectors/track, 4866 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x39bd121c

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        4661    37439451   83  Linux
/dev/sdb2            4662        4866     1646662+   5  Extended
/dev/sdb5            4662        4866     1646631   82  Linux swap / Solaris

Disk /dev/sdc: 320.1 GB, 320072932864 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xb9121dd9

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       38913   312568641    7  HPFS/NTFS

---

### Post by michy99 on 2009-11-11
I think the problem is that sda2 is marked as hidden. I don't know how to change it, but at least you have something to search for now.

EDIT: Try to change it with gparted.

---

