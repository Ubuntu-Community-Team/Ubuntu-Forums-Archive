---
title: "Samba Sharing &amp; RAID 1 - noob :("
date: 2011-07-17
forum: General Help
---

### Post by dre2771 on 2011-07-17
Looking for a hand.  I am new to the form and I have just installed 11.04 and I am working through some issues.  

ISSUE:  I cannot successfully share my samba folder on my RAID 1 Drive through using a S-Link.  The S-link is located in my home directory and points to a folder on my RAID 1 mounted drive.  I know I having sharing setup correctly, since my shared folders on my other home directories can be accessed freely and is setup exactly the same.  

I have setup my user permission on the folders, but I don't know what else it could be?

Can anyone help me look for the obvious?  :mad:

Disk /dev/sda: 82.0 GB, 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00052ac8

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9574    76898304   83  Linux
/dev/sda2            9574        9965     3142657    5  Extended
/dev/sda5            9574        9965     3142656   82  Linux swap / Solaris

Disk /dev/sdb: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xae2cae2d

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1      243201  1953512001   83  Linux

Disk /dev/sdc: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xae2cae2c

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1      243201  1953512001   83  Linux

Disk /dev/md127: 2000.4 GB, 2000397746176 bytes
2 heads, 4 sectors/track, 488378356 cylinders
Units = cylinders of 8 * 512 = 4096 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00067c54


Thanks,
 Devin

---

