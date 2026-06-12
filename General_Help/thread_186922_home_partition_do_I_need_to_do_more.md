---
title: "home partition do I need to do more?"
date: 2006-06-02
forum: General Help
---

### Post by bazcor on 2006-06-02
Hi everybody,

I've just made an install of dapper and I made two partitions / and home, what I need to know is if I need to do more to get my home directory onto the home partition.

thanks for any replies... Barry

---

### Post by stimpsonjcat on 2006-06-02
check your /etc/fstab file. there should be two separate lines for /home and /
like this:
```
/dev/hda7       /               ext3    noatime,errors=remount-ro 0       1
/dev/hda6       /home           ext3    noatime         0       2

```

---

### Post by meng on 2006-06-02
If you chose those options on a clean install, and had nothing else on the drive before that, then anything placed in home will be on the separate partition. (And your /etc/fstab should be similar to above.)

---

### Post by bazcor on 2006-06-02
I have the following in fstab:

[CODE]
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda6       /               ext3    defaults,errors=remount-ro 0       1
/dev/sda7       /home           ext3    defaults        0       2
/dev/sda8       none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0/
[CODE]


So I guess all is well, thanks again guys ... Barry

---

### Post by Ocxic on 2006-06-02
Your good, your home folder is mounted on sda7 so that whole partition is is used for your home directory.

---

