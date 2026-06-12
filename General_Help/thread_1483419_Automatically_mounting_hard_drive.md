---
title: "Automatically mounting hard drive"
date: 2010-05-14
forum: General Help
---

### Post by joomafoo on 2010-05-14
I recently had to reinstall karmic as lucid was giving me a few issues. I had a second hard drive with ll my media that was set up to automatically mount. I followed [https://help.ubuntu.com/community/InstallingANewHardDrive](https://help.ubuntu.com/community/InstallingANewHardDrive) as idid previously to set it up again but it doesnt seem to want to work. If i remove the command from the fstab and remove the mounting directory i can go to places>WestDig be prompted for my password and i can access my media but as soon as i create a directory for the mount point and put the command in fstab and try to access it it tells me it is already mounted or busy and i cant get access. Does anyone out there have any ideas where i am going wrong?

---

### Post by burton247 on 2010-05-14
There could be an issue with your fstab file, post it up here and see if anyone can see any problems with it

---

### Post by Morbius1 on 2010-05-14
You also might want to post the output of the following command which will tell us how your system sees these partitions:

```
sudo blkid -c /dev/null
```

---

### Post by joomafoo on 2010-05-15
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=a94bf3d8-9baa-4fdb-a396-50d2e3effe6e /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=9fec43b2-e95a-437e-add1-84a370d4daba none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0 
/dev/sdb1    /media/westdig  ext3    defaults     0        2

and this is what i get when i ran that command
/dev/sda1: UUID="a94bf3d8-9baa-4fdb-a396-50d2e3effe6e" TYPE="ext4" 
/dev/sda5: UUID="9fec43b2-e95a-437e-add1-84a370d4daba" TYPE="swap" 
/dev/sdb1: LABEL="WestDig" UUID="e72360fb-e46c-4f26-8de2-353c14f5d35d" TYPE="ext3"

---

