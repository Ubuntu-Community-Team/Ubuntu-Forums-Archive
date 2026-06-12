---
title: "Floppy Drive Privileges Set For Root"
date: 2010-06-01
forum: General Help
---

### Post by physic.dude on 2010-06-01
I just installed this floppy drive in my computer and I can view files on floppy disks but I can not add files to a disk, formating will not work.

All the privileges and ownership are set as root and I can not change them. (But I physically own it)

Here is what the privileges are set for:

---

### Post by plucky on 2010-06-03
Add this line to your **/etc/fstab** file
```
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
``` and then reboot and see if that works.

also check the driver is loaded ```
lsmod
``` and see if floppy is in the list.

Good Luck

---

