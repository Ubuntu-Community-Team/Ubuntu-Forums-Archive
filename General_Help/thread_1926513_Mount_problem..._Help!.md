---
title: "Mount problem... Help!"
date: 2012-02-16
forum: General Help
---

### Post by fikis on 2012-02-16
Hi everybody...
I have a problem with Ubuntu 11.04 on VMware. When I try to mount a floppy, it does it (apparently) but when I try to open the floppy files, it says "total 0"... pratically, it doesn't mount it.
Can anyone help me, please? Thanks in advance

---

### Post by raja.genupula on 2012-02-16
[http://ubuntuforums.org/showthread.php?t=1484932](http://ubuntuforums.org/showthread.php?t=1484932)

look at post #2

---

### Post by drmrgd on 2012-02-16
How are you mounting your floppy, and what is your mountpoint?  Also, can you manually mount it?

```
sudo mount /dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
```

For me, VMware Player has set it up to mount the floppy in /media/floppy0.  It may be that the mount point is changed or not correct.

---

