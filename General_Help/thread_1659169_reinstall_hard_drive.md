---
title: "reinstall hard drive"
date: 2011-01-03
forum: General Help
---

### Post by badperson on 2011-01-03
Hi,
I have a home server that recently crashed. I removed some ram, got it to start up, and I re-installed ubuntu server on a dedicated smaller drive. That was fine. 

Then I went to re-install a 2nd hard drive I had. I skipped the area in the documentation where it explains formatting and went straight to mounting the disk. 

I made the edits to /etc/fstab and was able to mount. 

but when I try to navigate to the new folder and see what's there, i only see a folder called lost+found. 

Any idea how to view the files in the drive?

---

### Post by lithopsian on 2011-01-03
What have you mounted it as?  Are you sure there are files on the drive?  What is the filesystem type?  Sounds like you just mounted an empty drive or did actually format it first.  sudo fdisk -l will show you the partitions you have.  parted or gparted will show more detail.

---

### Post by badperson on 2011-01-03
I think I got it...

here is the output from sudo fdisk -l for that drive: 

> Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xca4a77fb

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1      121601   976760001   83  Linux


Believe it or not... :oops::oops: ...I think what I did was create a samba share on the primary disk, and the disk I thought it was on was empty. Pretty embarrasing, but I think that's what happened.

---

