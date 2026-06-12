---
title: "Lost drive permission after switching to ext4"
date: 2009-08-29
forum: General Help
---

### Post by guitarplaya85 on 2009-08-29
I recently updated my Ubuntu to 9.04 and thought it would behove me to switch to the new ext4 file system as well.  I followed the directions in the Ubuntu documentation and it worked without flaw on my boot drive (sda1).  After doing the the same on my media hard drive (sdb1), I am no longer able to mount the drive.  Nautilus says I do not have permissions, and when I run sudo nautilus, the drive does not even appear on the list.  The drive does appear in fstab, and I can confirm that it worked prior to the switch to ext4.  Can anyone point me in the right direction to get this drive working again?  I would hate to lose 1TB worth of media!

---

### Post by drs305 on 2009-08-29
Make sure you still own the mount point.

If you deleted and recreated a new partition, make sure the UUIDs match (sudo blkid).

If you have a copy of your old fstab, check the line for sdb1 and just change "ext3" to "ext4". 

If you don't, a simple fstab entry should be something like the following, although UUIDs are preferable:

> 
/dev/sdb1 /path/yourmountpoint ext4 defaults 0 2


If this doesn't fix things, we may need to know if you "converted" to ext4 or did you do a complete reformat of the drive to ext4.

---

### Post by guitarplaya85 on 2009-08-29
Problem solved.  Once I added the "2" to the fstab entry, I rebooted and the system ran a scan of the disk.  It seems as though all it needed was the scan.  Thanks!

---

