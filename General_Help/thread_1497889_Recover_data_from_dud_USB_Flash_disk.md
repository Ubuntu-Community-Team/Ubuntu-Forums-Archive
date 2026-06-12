---
title: "Recover data from dud USB Flash disk?"
date: 2010-05-31
forum: General Help
---

### Post by aquascrotum on 2010-05-31
I have a 4GB flash disk that went kaput after a power surge and power cut crashed the WinXP laptop that it was last used on.

Since then Windows will recognise that a drive has been put in but doesnt recognise the data.

Ubuntu does something similar - in location "computer:///" I have a "Silicon Motion,Inc. USB MEMORY BAR" listed but cannot mount the location.

Is there any way I can recover the data on the stick?

Output from sudo fdisk-l as follows:
kyle@kyle-desktop:~$ sudo fdisk -l (doesnt mount the disk)

```
Disk /dev/sda: 160.0 GB, 160000000000 bytes
255 heads, 63 sectors/track, 19452 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe686f016

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           6       48163+  de  Dell Utility
/dev/sda2   *           7        7427    59609182+   7  HPFS/NTFS
/dev/sda3           18847       19452     4867695   db  CP/M / CTOS / ...
/dev/sda4            7428       18846    91723117+   5  Extended
/dev/sda5            7428       18376    87947811   83  Linux
/dev/sda6           18377       18846     3775243+  82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdb: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0004fd4f

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       30401   244196001    5  Extended
/dev/sdb5               1       10458    84003822    b  W95 FAT32
/dev/sdb6           10459       15683    41969781    7  HPFS/NTFS
/dev/sdb7           15684       30401   118222303+  83  Linux
```

Any help would be appreciated.

---

