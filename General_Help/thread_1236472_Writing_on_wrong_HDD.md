---
title: "Writing on wrong HDD"
date: 2009-08-10
forum: General Help
---

### Post by mocka on 2009-08-10
I have followed the guide below to mount an additional drive in my set up of Ubuntu Server. Anyhow, even if I automounted the drive to a folder, the files I copy to the mount folder is being written on the wrong hard drive. What am I doing wrong?

The guide I followed: [https://help.ubuntu.com/community/InstallingANewHardDrive](https://help.ubuntu.com/community/InstallingANewHardDrive)

---

### Post by mikewhatever on 2009-08-10
Post you fstab for review.

cat /etc/fstab

---

### Post by mocka on 2009-08-10
This is my fstab:

> 
# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/mapper/HubuntuServer-root during installation
UUID=8c6a0942-1628-4bed-be27-f622b4eb5dc2 /               ext3    relatime,errors=remount-ro 0       1
# /boot was on /dev/sdb5 during installation
UUID=b3b1b9bd-59d1-4284-b81f-35b4ab62f65f /boot           ext2    relatime        0       2
# swap was on /dev/mapper/HubuntuServer-swap_1 during installation
UUID=ee370e9e-0acd-41ec-98f2-61048a569c50 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
/dev/sda1	/media/Samsung1	ext3	0	2


The last line is the one I have added. I want the HDD to mount to the folder Samsung1 under media.

EDIT: Due to the bad formatting in the post, I uploaded my fstab as a .txt file in addition.

---

### Post by drs305 on 2009-08-10
Try adding "defaults" as the options (or add whatever options you wish in the same place). 

> /dev/sda1 /media/Samsung1 ext3 **defaults** 0 2 

Save fstab, then run the following. If you get no messages from the second command, the partition is mounted correctly:
```

sudo umount /dev/sda1  # although it is probably not mounted anyway
sudo mount -a

```

---

### Post by mocka on 2009-08-10
Thanks a lot, that did the trick.

---

