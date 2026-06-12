---
title: "EXTERNAL USB HDD - Read only"
date: 2011-05-30
forum: General Help
---

### Post by newtonu on 2011-05-30
Hello all,

I have a External USB HDD from SAMSUNG, and as it mounts I'm unable to write anything on it. Always telling me it is a Read only file.

> ls -lThe result is this:
> drwxr-xr-x  2 root    root     4096 2011-05-23 18:05 dingoo
lrwxrwxrwx  1 root    root        7 2011-05-17 11:21 floppy -> floppy0
drwxr-xr-x  2 root    root     4096 2011-05-17 11:21 floppy0
drwx------ 12 newtonu newtonu 32768 1969-12-31 21:00 SAMSUNG

It is funny but the date is set to 1969. Don't know why.

It is formated in FAT32, and I'm using Ubuntu 11.04.

I'm new here on the FORUMS and been a Ubuntu user for 3 years now.

Thank you for the help!

---

### Post by AlphaLexman on 2011-05-30
What is the output of:
```
cat /etc/fstab
```

---

### Post by newtonu on 2011-05-30
> 
/etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sda1       /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=27a589ad-acac-47e4-bb85-275ece487a79 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0



Thank you!

---

### Post by newtonu on 2011-05-31
Anyone?

---

