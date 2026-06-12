---
title: "Error mounting: mount exited with exit code 2"
date: 2011-02-27
forum: General Help
---

### Post by ck07 on 2011-02-27
Hello everyone,

I have installed Ubuntu 10.04 in my laptop with Windows Vista installed. I can't open my directory of Windows in Ubuntu, a message error displayed "Unable to mount SW_Preload Error mounting: mount exited with exit code 2:"

I have execute the comand
# sudo fdisk -l , which will list your drives partitions

Here is the results:
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


Can anyone help me please ?
Thanks in advance,
ck

---

### Post by pollaeng on 2011-05-11
I Have Same problem with no solution; Just I figure out that every question about " Error mounting: mount exited with exit code 2" has no answer is there a hidden conspiracy on HD I should know about :)

---

### Post by LostFarmer on 2011-05-11
You do not say just what partition but will guess it is sda3.
255 heads, 63 sectors/track, **30401** cylinders
/dev/sda3           29127       **30402**    10240000    7  HPFS/NTFS

I mush prefer looking at sector data vice blocks. 
post '**fdisk -lu**'

Does all the other NTFS partitions open ?  Which one does not ?  (do not like to guess)

---

### Post by ck07 on 2011-05-12
Hi LostFarmer,
Thanks for your answer. I have forget which partition. But I have used the Ubuntu Live CD to reboot the PC. AT that time, i could mount the partition. However all the data has been lost.

---

