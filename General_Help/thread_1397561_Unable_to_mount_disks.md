---
title: "Unable to mount disks"
date: 2010-02-03
forum: General Help
---

### Post by BearStalin on 2010-02-03
My computer recognises that there is a cd in the drive, but it won't let me open any. Whenever I try to it says

Unable to mount [Disk name]
Error mounting: mount exited with exit code 1: helper failed with:
mount: mount point /media/cdrom0 does not exist

I'm using Ubuntu 9.10, and everything was working fine until I tried messing around with mounting scripts. I for some reason felt compelled to try to mount the cd that was already in my drive, and after removing the cd, it wouldn't let me read any cds. Any help in getting Ubuntu to run cds ago would be greatly appreciated.

---

### Post by BearStalin on 2010-02-03
# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=b2d2f7eb-a5a7-40b1-9ec7-41440a7dd82d /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=e84a3f63-2edb-49d6-af6b-e15a199fde32 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

---

### Post by n0dix on 2010-02-03
Try:
```
sudo mkdir /media/cdrom0
```

---

### Post by tom4everitt on 2010-02-03
Telling from your error message it sounds like a folder is missing. 

You know how to check if the folder /media/cdrom0 exists? The command

ls /media 

will list your /media directory, if cdrom0 is not there you must have accidentally removed it. To create it again, do:

sudo mkdir /media/cdrom0      # To make the directory
sudo chmod 777 /media/cdrom0  # To give it full permissions

---

### Post by BearStalin on 2010-02-03
Wow. Thanks. That did it. I feel stupid, but I'm pretty new to Ubuntu.

---

