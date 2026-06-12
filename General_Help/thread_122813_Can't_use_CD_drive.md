---
title: "Can't use CD drive"
date: 2006-01-28
forum: General Help
---

### Post by wtd on 2006-01-28
I'm using Kubuntu 5.10, and for some reason, I cannot use my CD-ROM drive at all.  I know there's an audio CD in the drive, but I cannot access it or mount it.  I can't eject the CD.  Running the audiocd kio slave just has the little progress indicator spinning forever.

Any thoughts on what might be wrong?

---

### Post by amohanty on 2006-01-28
Can you post the contents of your /etc/fstab file?
Also post the output of **mount**.

AM

---

### Post by wtd on 2006-01-28
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda2       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdb        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
```

As for mount... it just hangs indefinitely.  The CD drive shows no activity.

---

### Post by amohanty on 2006-01-28
Try changing this
> /dev/hdb        /media/cdrom0   udf,iso9660 user,noauto     0       0
to:
> /dev/hdb        /media/cdrom0   **auto** user,noauto     0       0

and reboot - you dont really need to but its good karma :)

AM

---

### Post by wtd on 2006-01-28
Unfortunately that didn't change the situation at all.

---

### Post by amohanty on 2006-01-28
can you post the output of:
> lsof /dev/hdb

AM

---

### Post by wtd on 2006-01-28
```
$ sudo lsof /dev/hdb
$
```

---

### Post by amohanty on 2006-01-29
Ok try > sudo mount -a
if it goes through ok then try a > mount

if either one hangs then post the output of:
> dmesg

---

### Post by wtd on 2006-02-02
For no apparent reason, this problem seems to have resolved itself.

Thanks for the help anyway.  :)

---

