---
title: "Whole hard drive gone"
date: 2010-01-30
forum: General Help
---

### Post by ubuntüser on 2010-01-30
My whole hard drive shows up as gone! 
I have a OS drive, and then a 2x1TB raid drives in raid 1 configuration using MDADM.

Now, I booted up and that drive shows up as blank.
The output from cat /proc/mdstat is:

Personalities : [raid1] [linear] [multipath] [raid0] [raid6] [raid5] [raid4] [raid10] 
md0 : active raid1 sdb1[1] sda1[0]
      976759936 blocks [2/2] [UU]
      
unused devices: <none>


What happened to my drives???

My two raid drives are sda1 and sdb1

so when I do:

fdisk -u -l

Disk /dev/md0: 1000.2 GB, 1000202174464 bytes
2 heads, 4 sectors/track, 244189984 cylinders, total 1953519872 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00000000

Disk /dev/md0 doesn't contain a valid partition table

WTF?? How do I fix this? Or have I lost all my data?

Please help!
Thanks

---

