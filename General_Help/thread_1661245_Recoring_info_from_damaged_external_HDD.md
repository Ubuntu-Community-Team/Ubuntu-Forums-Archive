---
title: "Recoring info from damaged external HDD"
date: 2011-01-06
forum: General Help
---

### Post by ImagineLED on 2011-01-06
Using fdisk -l I get 

> Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00087e8c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       19076   153219072   83  Linux
/dev/sda2           19076       19458     3068929    5  Extended
/dev/sda5           19076       19458     3068928   82  Linux swap / Solaris

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000116bc

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        9730    78149632   83  Linux


my HDD sdb1 is not working properly, I need a really important document in there. Tried using dd_rhelp using this tutorial [http://www.ubuntugeek.com/recover-data-from-a-damaged-hard-disk-using-dd_rhelp.html](http://www.ubuntugeek.com/recover-data-from-a-damaged-hard-disk-using-dd_rhelp.html)

but in the end I get this error
>  sudo dd_rhelp /dev/sdb1 /dev/sda1/backup.img
dd_rhelp: error: '/dev/sda1/backup.img' is not accessible/could not be created...


I'm kinda new to linux so don't really know what else to do.

---

