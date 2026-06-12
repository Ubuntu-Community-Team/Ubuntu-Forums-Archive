---
title: "Moves transfered from Ubuntu 9.04 to Windows Vista disappeared ????"
date: 2009-08-28
forum: General Help
---

### Post by pi4r0n on 2009-08-28
Hello ALL

I just got really strange situation which I can not explain or find a explanation for :confused:

I download few moves (torrent) to my Ubuntu 9.04 then I moved these files from Ubuntu partition to my mounted Windows Vista partition and what is really strange when I login to Windows I could not see these moves there at all and what is even more strange is when I loged back to Ubuntu these files were not there instead of them were 5 MB sample files and not 700MB moves ?? 

I have attached my fstab for you informations so you can see how the partitions are mounted.

Do you think anyone can help ma and emplane what happened ??

> 
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda7 during installation
UUID=0a9f1a7b-d930-4d49-992b-acb85ce7688b /               ext3    relatime,errors=remount-ro 0       1
# /home was on /dev/sda6 during installation
UUID=e88f5d5d-de96-4d85-9808-c2829c32a8ea /home           ext3    relatime        0       2
# swap was on /dev/sda5 during installation
UUID=5a59503a-ce63-47ff-97a5-149cd639ceb9 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

Cheers

pi4r0n

---

### Post by yeeeev on 2009-08-28
NTFS has a nasty habit of loosing files if the power is cut in the middle of some operations, operations are not fully flushed to the disk, or just because...:)
Try to run chkdsk /f from vista. There's also ntfsfix in the ntfsutils, but I never tried it

Good luck!

---

