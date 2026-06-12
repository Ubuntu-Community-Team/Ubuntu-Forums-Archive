---
title: "Problem with partitioning a hard drive"
date: 2010-12-03
forum: General Help
---

### Post by 0x_ on 2010-12-03
I use 4 WDC WD15EARS-00Z hard drives on a Raid 5 array. I had to swap one drive because of an error. The new drive is exactly the same as the old one. But I somehow can't partition the new one the same way as the old one. Any help/pointers are appreciated!

```

# sfdisk -d /dev/sde | sfdisk /dev/sdf
Checking that no-one is using this disk right now ...
OK

Disk /dev/sdf: 182401 cylinders, 255 heads, 63 sectors/track
Old situation:
Units = cylinders of 8225280 bytes, blocks of 1024 bytes, counting from 0

   Device Boot Start     End   #cyls    #blocks   Id  System
/dev/sdf1          0+ 182400  182401- 1465136001   fd  Linux raid autodetect
/dev/sdf2          0       -       0          0    0  Empty
/dev/sdf3          0       -       0          0    0  Empty
/dev/sdf4          0       -       0          0    0  Empty
Warning: given size (2930277104) exceeds max allowable size (2930272001)

sfdisk: bad input
```




Old disk:
```
Disk /dev/sde: 1500GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
 1      32.8kB  1500GB  1500GB  primary               raid
```

New one:
```
Disk /dev/sdf: 1500GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
 1      32.3kB  1500GB  1500GB  primary               raid
```


Partition tool versions:

```
# fdisk -v
fdisk v2.12r
# cfdisk -v
cfdisk 2.12r
Copyright (C) 1994-2002 Kevin E. Martin & aeb
# sfdisk -v
sfdisk version 3.08 (aeb@cwi.nl, 040824) from util-linux-2.12r
# parted -v
GNU Parted 1.7.1
```



SOLUTION:
"fdisk -u /dev/sdf" and then create the partition starting with sector 64.

---

### Post by karthick87 on 2010-12-03
Install Gparted partition manager,it is very easy to make a partition with [B]gparted

[/B]```
sudo apt-get install gparted
```

---

