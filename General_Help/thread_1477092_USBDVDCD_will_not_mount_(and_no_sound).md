---
title: "USB/DVD/CD will not mount (and no sound)"
date: 2010-05-08
forum: General Help
---

### Post by Titus A Duxass on 2010-05-08
Hi all,
Just done a fresh install of 10.04 LTS on a bog standard pc.
Everything works fine apart from USB devices will not mount nor will DVDs/CDs.

Sound does not work either.

The fsab:

glen@Office:~$ cat /etc/fstab 
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda5 during installation
UUID=01035b17-866a-49bb-afff-464d77e2da9c /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda7 during installation
UUID=c3e99f88-59e2-4f6b-85f8-3feaee556a9a /home           xfs     defaults        0       2
# swap was on /dev/sda6 during installation
UUID=75c6aa33-f6ef-4568-a47c-db0e9255ebaa none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

Any help would be appreciated.
Thanks
Titus

---

