---
title: "How to set group id for a hard disk mounted via fstab"
date: 2009-07-11
forum: General Help
---

### Post by 59chip on 2009-07-11
I followed ubuntu procedure here:

[https://help.ubuntu.com/community/InstallingANewHardDrive]("https://help.ubuntu.com/community/InstallingANewHardDrive")

I can't change group of mounted drive:

```
jean@jean-study:~$ cd /media
jean@jean-study:/media$ ls -l
total 20
lrwxrwxrwx 1 root root    6 2009-06-27 08:07 cdrom -> cdrom0
drwxr-xr-x 2 root root 4096 2009-06-27 08:07 cdrom0
drwxr-xr-x 2 root root 4096 2009-06-27 08:07 cdrom1
drwxrwxr-x 4 jean root 4096 1969-12-31 19:00 hd006GB
drwxrwxr-x 4 jean root 8192 1969-12-31 19:00 hd010GB
jean@jean-study:/media$ sudo chgrp users hd006GB
[sudo] password for jean: 
chgrp: changing group of `hd006GB': Operation not permitted
jean@jean-study:/media$ 

```

Here is fstab file:

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=a6da1353-a497-4066-992d-33797fb71693 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=9abf857e-c41a-459f-a983-e3022a8c7050 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0
#
#  10 GB hard drive
#
UUID=4A4F-5366  /media/hd010GB   vfat    rw,nosuid,nodev,uhelper=hal,shortname=mixed,uid=1000,utf8,umask=002,flush     0        2
#
#  6 GB hard drive
#
UUID=4A4F-53BE  /media/hd006GB   vfat    rw,nosuid,nodev,uhelper=hal,shortname=mixed,uid=1000,utf8,umask=002,flush     0        2

```

---

### Post by miklcct on 2009-07-13
add gid=xxx in the option column in /etc/fstab

---

