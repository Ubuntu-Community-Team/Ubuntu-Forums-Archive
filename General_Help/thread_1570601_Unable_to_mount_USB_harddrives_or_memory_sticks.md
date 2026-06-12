---
title: "Unable to mount USB harddrives or memory sticks"
date: 2010-09-08
forum: General Help
---

### Post by cliffjt on 2010-09-08
Hi, whenever I try to connect my 500Gb external harddrive or any USB memory stick, I get the following error...


 **Error mounting: mount: unknown filesystem type 'vfat'**

 Previously, I have been able to read the drives successfully, but I've just had to reinstall Ubuntu after an upgrade failed and since then I get the error. Ubuntu does 'see' the drives, but when I attempt to access them via Nautilus, that's when the error occurs.


 I did  fdisk -l and get the following output:


 Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x432e74c4


    Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       19083   153284166   83  Linux
/dev/sda2           19084       19457     3004124+   5  Extended
/dev/sda5           19084       19457     3004123+  82  Linux swap / Solaris


 Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000
    Device Boot      Start         End      Blocks   Id  System

/dev/sdb1               1       60802   488392033+   b  W95 FAT32
 Disk /dev/sdg: 4022 MB, 4022337024 bytes
255 heads, 63 sectors/track, 489 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000
    Device Boot      Start         End      Blocks   Id  System
/dev/sdg1               1         488     3919841    b  W95 FAT32
cliff@Doofus:~$


 How can I get Ubuntu to recognise these drives?


 Thanks

---

