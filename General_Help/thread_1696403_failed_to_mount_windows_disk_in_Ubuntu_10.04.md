---
title: "failed to mount windows disk in Ubuntu 10.04"
date: 2011-02-27
forum: General Help
---

### Post by ck07 on 2011-02-27
Dear Everyone,

I have installed ubuntu 10.04 in windows vista. It works perfectly. But yesterday I have update some softwares in Vista. And now I can not mount the windows disk in Ubuntu, i.e., I can not retrieved any data in windows and neither can't I start windows vista.

Here is my partitions information 

*********************************************************************
Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xb7504fa5

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         192     1536000    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2             192       23288   185520700    7  HPFS/NTFS
Partition 2 does not end on cylinder boundary.
/dev/sda3           29127       30402    10240000    7  HPFS/NTFS
Partition 3 does not end on cylinder boundary.
/dev/sda4           23288       29127    46899201    5  Extended
Partition 4 does not end on cylinder boundary.
/dev/sda5           23288       28882    44933120   83  Linux
/dev/sda6           28882       29127     1965056   82  Linux swap / Solaris

Partition table entries are not in disk order

******************************************************************************

Then I try to mount "/dev/sda2" to "/mnt/win". I did as follows:

# cd /mnt/
# sudo mkdir win
# sudo mount -t ntfs /dev/sda2 /mnt/win -o "umask=022"

But after that, there is nothing in "/mnt/win", on folders in windows have appeared in "/mnt/win". 
Since I have very important data in the windows partition, I am appreciated if someone here can give me some suggestion.

Best,
ck

---

