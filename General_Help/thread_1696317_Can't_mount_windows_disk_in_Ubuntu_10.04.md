---
title: "Can't mount windows disk in Ubuntu 10.04"
date: 2011-02-27
forum: General Help
---

### Post by ck07 on 2011-02-27
Hello Everyone,

I have installed ubuntu 10.04 in Windows Vista. I have got a problem that I can not access the windows files in Ubuntu, i.e., in Ubuntu the "mount" is failed. When I clicked the windows disk in the file browser of ubuntu a message error displayed "Error mounting: mount exited with exit code 2".
I have  used command "sudo fdisk -l" to show the partitions information, the results are

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

"Partition 1 does not end on cylinder boundary." is strange ?
Can anyone help me please ? Because I have very important data in this partition, I have retrieved these data.

Thanks in advance,
ck

---

