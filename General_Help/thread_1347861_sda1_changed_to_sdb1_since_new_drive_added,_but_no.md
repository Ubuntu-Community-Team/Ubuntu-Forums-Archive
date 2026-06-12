---
title: "sda1 changed to sdb1 since new drive added, but not in fstab"
date: 2009-12-06
forum: General Help
---

### Post by munchkinmunchkin on 2009-12-06
I am using a Dell GX280 P4 with 250gb SATA hard drive as the main drive, and DVD rom as slave on the IDE. My computer has one SATA and one IDE connector. 

I have been running the alt encrypted version of Ubuntu 8.04 LTS for over a year and recently needed some more storage, so added a spare 80gb 7200 Seagate drive as master on the IDE with the DVD rom moved to slave.

It works fine except the boot partition of my original SATA drive has been renamed from dev/sda1 to dev/sdb1, and the new IDE drive is now dev/sda1 (got details from GParted), but in the fstab file the original boot partition of my drive with it's UUID is still named as dev/sda1, so both the boot partition of my main SATA master and my IDE master drive have the same name dev/sda1.

See my fstab file:

> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/mapper/ubuntua-root
UUID=5f493798-cd53-471f-b09a-8b38f89f545b /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda1
UUID=8b004b1c-8917-45e6-90ce-dacce7127725 /boot           ext3    relatime        0       2
# /dev/mapper/ubuntua-swap_1
UUID=d4a09848-f8ba-464f-8e48-4f4dedb59a5d none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/sda1	/media/extrastorage	ext3 defaults	0	2

Should I rename the fstab entry of /dev/sda1 of the master SATA boot drive to /dev/sdb1 or would changing it cause the drive to not be mounted and inaccessible? 

If the IDE drive is disconnected before booting up, the mount point then leads to the contents of the boot partition.

The newly formatted IDE drive (ext3) automatically acquired a lost & found folder after mounting, is this normal?

---

### Post by oldfred on 2009-12-06
This is the advantage of using UUIDs, they supposedly do not change unless you delete the partition and recreate it. 

The # sda reference is just a comment. But this next entry may not be correct depending on which drive you are actually mounted. You could also change this to the UUID style. Some suggest to assign labels to every partition (using gparted or other tools) and using the labels as the identifier.
/dev/sda1    /media/extrastorage    ext3 defaults    0    2

Yes everytime I have created a partition and mounted it, it seems to get a place to put the deleted files.

Understanding fstab
[http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)
[https://help.ubuntu.com/community/Mount/](https://help.ubuntu.com/community/Mount/)

---

### Post by munchkinmunchkin on 2009-12-06
> The # sda reference is just a comment. But this next entry may not be correct depending on which drive you are actually mounted. You could also change this to the UUID style. Some suggest to assign labels to every partition (using gparted or other tools) and using the labels as the identifier.
/dev/sda1 /media/extrastorage ext3 defaults 0 2

The above entry that I added in fstab, I followed the information here to create:

[https://help.ubuntu.com/community/InstallingANewHardDrive](https://help.ubuntu.com/community/InstallingANewHardDrive)

I also tried using the UUID method, all was well, but Ubuntu threw an 'hissy fit' when I rebooted with the drive removed, stopping in GRUB with an error message.





> Yes everytime I have created a partition and mounted it, it seems to get a place to put the deleted files.

I don't think it's for deleted files, it's marked up as 'lost & found'.

---

### Post by audiomick on 2009-12-06
As far as I know, "lost & found" is where the file system checking facility puts fragments and stuff that is "broken"

---

