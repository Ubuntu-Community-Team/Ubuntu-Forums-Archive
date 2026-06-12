---
title: "Problem accessing WD external harddrive"
date: 2010-03-29
forum: General Help
---

### Post by samenkov on 2010-03-29
Hi, 

I have a problem with an external harddrive (WD My Book Essential Edition 2.0)
which i can't access anymore.
I found on a blog the following instructions for a really similar problem and this
solved the other guy's problem.

sudo aptitude install ntfs-3g ntfs-config

then:

sudo mkdir /media/hdext
sudo mount -t ntfs-3g /dev/sdb1 /media/hdext -o force

My problem is that my harddrive is FAT32 and not NTFS.
Can anyone help me?
That's the result of: sudo fdisk -l 

Disk /dev/sdc: 1000.2 GB, 1000204886016 bytes 
255 heads, 63 sectors/track, 121601 cylinders 
Units = cylinders of 16065 * 512 = 8225280 bytes 
Disk identifier: 0xe8900690 

   Device Boot      Start         End      Blocks   Id  System 
/dev/sdc1               1      121601   976760001    c  W95 FAT32 (LBA)

Thanks!

---

### Post by DanGahan on 2010-03-29
try "sudo mount -t vfat /dev/sdc1 /media/hdext"

---

