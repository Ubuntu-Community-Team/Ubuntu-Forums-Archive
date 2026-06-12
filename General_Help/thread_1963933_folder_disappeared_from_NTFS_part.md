---
title: "folder disappeared from NTFS part"
date: 2012-04-23
forum: General Help
---

### Post by cristian.ene on 2012-04-23
Hey,

I don't know how, but the user of the computer deleted a folder from a special ntfs partition.
I tried ntfs undelete, but the ntfs drive seems to be in use.

```
cristina@cristina-laptop:~$ sudo ntfsundelete /dev/sda5 -s
Access is denied because the NTFS volume is already exclusively opened.
The volume may be already mounted, or another software may use it which
could be identified for example by the help of the 'fuser' command.
You can use force option to avoid this check, but this is not recommended
and may lead to data corruption.

```

```
cristina@cristina-laptop:~$ sudo fdisk -l

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xf0f1f0f1

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          61      487424   83  Linux
Partition 1 does not end on cylinder boundary.
/dev/sda2           11870       14592    21864577    f  W95 Ext'd (LBA)
/dev/sda3              61        1885    14648320   83  Linux
/dev/sda4            1885       11870    80207872   83  Linux
/dev/sda5           12120       14592    19864372+   7  HPFS/NTFS
/dev/sda6           11870       12119     1999872   82  Linux swap / Solaris

Partition table entries are not in disk order

```

The ntfs mount is still full... only 8 mb left on that drive. but i can't find my 19GB folder in there
Ideas?

---

### Post by cristian.ene on 2012-04-23
The user: 

> 
I did the following
I created a shortcut for a folder on the desktop, from an ntfs drive. After this I moved the shortcut to desktop. I also created an icon for this folder, and by mistake I pressed "delete" and the folder was gone. I checked the recycle bin and it wasn't there. How can I recover this folder? 

---

### Post by cristian.ene on 2012-04-23
anyone?

---

