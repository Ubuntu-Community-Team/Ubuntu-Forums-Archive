---
title: "Changing ownership/permissions..."
date: 2009-09-30
forum: General Help
---

### Post by kfitzenreiter on 2009-09-30
Hello everyone.

Okay, I'm trying to permit myself to read write execute files from a partition I have mounted on my ubuntu system.

I have in fstab

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda2 during installation
UUID=d35d46dc-845b-470d-aeac-cc20b0d83e83 /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=a8e9f989-90ed-4976-98d4-f6c708f87f5a none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
/dev/sda4    /home/kurt/Desktop/mycomputer/sda4    auto    rw,exec            0    0


I'm trying to be able to drag and drop files into the sda4 folder which appears with a lock next to it.  I'm not sure what to do next.  I tried chmod 777 * which didn't work.

Please advise

---

### Post by &#32 Greg on 2009-09-30
Try 

sudo chmod -R 777 /home/kurt/Desktop/mycomputer/sda4

---

### Post by kfitzenreiter on 2009-09-30
The command executed okay, I guess.  But, when I try to drag another folder on the desktop into that folder it says "error while copying...you do not have permissions to create it in this directory..."

---

### Post by kfitzenreiter on 2009-09-30
This is the fstab code that brought me joy....

/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
/dev/sda4    /home/kurt/Desktop/mycomputer/sda4    vfat    user,fmask=0111,dmask=0000    0    0

---

