---
title: "Drive Not Displayed"
date: 2010-11-16
forum: General Help
---

### Post by Corky1969 on 2010-11-16
I'm running a multi-drive system. I have Windows 7 installed on a western digital 74gb raptor, a second 74gb raptor as a data drive, a 300 gb seagate with ubuntu 10.10 installed and a 1tb maxtor as a data drive. 

Ubuntu doesn't see either western digital drives as being partitioned and therefore they don't show up except under the disk utility. I can't use the bootloader since Ubuntu doesn't see the drive. I have to go to the BIOS and manually tell the system what drive to boot from. Am I missing something that will allow Ubuntu to see the two raptors as partitioned. Windows 7 was installed first and still runs fine.

Thanks.

---

### Post by cariboo on 2010-11-16
Do all the drives show up when you type:

```
sudo fdisk -l
```

---

### Post by Corky1969 on 2010-11-16
Yes they do. Here is what it comes up with for those two drives.

Disk /dev/sdb: 74.4 GB, 74355769344 bytes
255 heads, 63 sectors/track, 9039 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xa599110d

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        9038    72597703+   7  HPFS/NTFS


Disk /dev/sdc: 74.4 GB, 74355769344 bytes
255 heads, 63 sectors/track, 9039 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xc2bac2ba

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1        9039    72605736    7  HPFS/NTFS

---

