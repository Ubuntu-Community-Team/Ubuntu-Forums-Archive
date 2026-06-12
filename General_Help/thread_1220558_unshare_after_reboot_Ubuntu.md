---
title: "unshare after reboot Ubuntu"
date: 2009-07-22
forum: General Help
---

### Post by hangnguyen on 2009-07-22
In Ubuntu I shared some disks (NTFS) for users may access to, but when Ubuntu reboot it did not share by default, I have right click and choose share option again, so everyday I must do that .

How to make those disks shared by default even after Ubuntu reboot .

Thanks for your help !
I am very newb .

H

---

### Post by darolu on 2009-07-23
Make sure samba is running when you start Ubuntu; go to System - Administration - Services and make sure Samba is marked; also verify your Samba settings at System - Administration - Samba; if you don't have a Samba option install:
```
sudo apt-get install system-config-samba
```

---

### Post by hangnguyen on 2009-07-23
Thanks for reply, after install system-config-samba I do not need right click and share again . It works very nice

however after Ubuntu restart it seem did not auto mount the NTFS partitions so users did not see anything, I have click every partitions to make it display and users can access at that time . Any solution for this issue ???

Thanks for your help ! Darolu

---

### Post by nikhilk on 2009-07-23
> **hangnguyen said:**
> however after Ubuntu restart it seem did not auto mount the NTFS partitions so users did not see anything, I have click every partitions to make it display and users can access at that time . Any solution for this issue ???

Post the contents of your "/etc/fstab" file. Do the partitions have the "noauto" option?

---

### Post by hangnguyen on 2009-07-23
Here is the   content of fstab
thanks

> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdd6
UUID=e7eb112d-0cba-4293-a267-86d732f204e9 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sdd5
UUID=16f84fc9-145f-4fdb-bf1e-96aa4c156b5d none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

---

### Post by nikhilk on 2009-07-24
I can see only three partitions in your fstab (which will be mounted automatically) viz. "/", "swap" and your CD-ROM drive. You need to add your NTFS partitions to the fstab file for them to be automatically mounted.
[Here]("http://www.psychocats.net/ubuntu/mountwindows") are some easy to follow instructions on doing that.

---

