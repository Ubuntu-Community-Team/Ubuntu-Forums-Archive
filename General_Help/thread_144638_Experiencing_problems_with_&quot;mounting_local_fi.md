---
title: "Experiencing problems with &quot;mounting local file system&quot;"
date: 2006-03-14
forum: General Help
---

### Post by jerkface on 2006-03-14
And the problem is that it just fails on boot:) Here is my FSTAB..
```
 /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda3       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda7       none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
/dev/hda1       /media/windows  vfat    umask=000       0       0
/dev/hda2       /media/movies  ntfs    umask=0222      0       0

```
Can anyone help?

---

