---
title: "Recover Data from mdraid filesystem"
date: 2009-08-20
forum: General Help
---

### Post by Keldek on 2009-08-20
Hello, our server currently underwent some serious problems, in which our software RAID 1 array was rendered broken.

The techs at our server host have replaced BOTH drives with new ones and have allowed us to keep access to one of our old drives in order to recover data from it (the drive itself is not bad, they just replaced both drives because they needed to reload the OS and doing so on the working drive with our data on it would mean wiping our data).

My question is, how can I mount the original drive so I can copy our files from it to the new raid array?

fdisk -l outputs the following for the drive we need to mount:
```
Disk /dev/sdc: 1500.3 GB, 1500301910016 bytes
255 heads, 63 sectors/track, 182401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0004dd94

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1          13      104391   83  Linux
/dev/sdc2              14      117360   942589777+  fd  Linux raid autodetect
/dev/sdc3          117361      181356   514047870   fd  Linux raid autodetect
/dev/sdc4          181357      182401     8393962+   5  Extended
```

---

