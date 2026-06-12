---
title: "help pls"
date: 2010-05-04
forum: General Help
---

### Post by stefan22 on 2010-05-04
tried to  install quota
---> Apt-get install  quota
--->  Mcedit / etc / fstab here I wrote something wrong
# / Etc / fstab: static file system  information.
#
# <File System> <mount point> <type>  <options> <dump> <pass>
proc / proc proc defaults 0 0
# /  Dev/sda1
UUID =  6af53069-0d51-49be-b275-aeaea8d780c5 / ext4 relatime, errors =  remount-ro, usrqouta, grpqouta 0 1
# /  Dev/sda5
UUID =  d8e1f66c-1442-423e-b442-8ae66eded9d7 none swap sw 0 0
/ Dev/scd0 /  media/cdrom0 udf, iso9660 user, noauto, exec, utf8 0 0
/  Dev/fd0 / media /
---> Touch /  quota.user / quota.group
---> Chmod 600  / quota .*
--->  Mount-o remount /
---> Reboot
Mount  fail: (
trying to get into recovery  mode to edit what's wrong in / etc / fstab does not let me save

---

### Post by zaphod777 on 2010-05-05
when editing the fstab make sure you are using sudo or you can't save.

if you are using vi also make sure you use the command ":wq" that will write and quit.

---

### Post by dino99 on 2010-05-05
[http://www.ubuntugeek.com/how-to-setup-disk-quotas-in-ubuntu.html](http://www.ubuntugeek.com/how-to-setup-disk-quotas-in-ubuntu.html)

---

