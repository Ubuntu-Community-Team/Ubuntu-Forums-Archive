---
title: "help auto mounting a partition"
date: 2012-01-06
forum: General Help
---

### Post by DataSpy on 2012-01-06
I setup a separate partion for my data, I added the entry to fstab but when I issue the command "sudo mount -a" I get:

> mount: wrong fs type, bad option, bad superblock on /dev/sda6,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

when I do "dmesg | tail" I get:

> [ 1556.168613] EXT4-fs (sda6): Unrecognized mount option "default" or missing value

My fstab is:

> /dev/sda6 /home/dataspy/shares/storage ext4 default 0 0

fdisk -l

> Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00047938

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         608     4881408   83  Linux
Partition 1 does not end on cylinder boundary.
/dev/sda2             608       60802   483502081    5  Extended
/dev/sda5             608        1338     5858304   82  Linux swap / Solaris
/dev/sda6            1339       60801   477636516   83  Linux


I can mount this manually with "sudo mount /dev/sda6 /home/dataspy/shares/storage"

Any help greatly appreciated, thanks in advance!

---

### Post by lechien73 on 2012-01-06
An immediate tip is that "default" should be "defaults", so that might help :)

---

### Post by DataSpy on 2012-01-06
that fixed it, thanks!!!

---

### Post by lechien73 on 2012-01-06
Cool...it's often the typos that will get you ;)

If you get chance, could you use the **Thread Tools** menu at the top and mark this as [SOLVED]?

Thanks

---

