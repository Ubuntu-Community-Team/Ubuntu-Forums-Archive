---
title: "Boot drive selection"
date: 2009-09-11
forum: General Help
---

### Post by kempy1000 on 2009-09-11
Hi

I just installed a new hard drive to my ubuntu mythtv backend/frontend.

I have the setup currently as:

320GB SATA for /var/lib/mythtv/videos and /torrent
160GB SATA for /var/lib/mythtv/recordings
80GB IDE for the main system drive

I just installed the 120GB SATA to the system.

The 160GB is shown as sda
The 320GB is shown as sdb
The 80GB is shown as sbc

However when i do "sudo fdisk -ls"

The output is this:

```


Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x39763975

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       19457   156288321   83  Linux

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000451d9

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        2602    20900533+  83  Linux
/dev/sdb2            2603       38913   291668107+  83  Linux

Disk /dev/sdc: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x4ab64125

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1        9360    75184168+  83  Linux
/dev/sdc2            9361        9729     2963992+   5  Extended
/dev/sdc5            9361        9729     2963961   82  Linux swap / Solaris



```

I noticed the sdb1 is flagged as the boot drive when sdc1 is the main system drive.

/boot is on sdc how come sdb is the boot drive?

Thanks
Chris

---

