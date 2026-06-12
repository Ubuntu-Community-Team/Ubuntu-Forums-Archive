---
title: "Mounting a hard drive with options on command-line"
date: 2010-09-03
forum: General Help
---

### Post by zefew on 2010-09-03
I have a working fstab entry:

> 
/dev/sdc1 /media/sdc vfat rw,nosuid,nodev,uhelper=devkit,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,flush 0 0


But how do I mount the sdc drive with those options from the command-line without restarting? I've tried to do so with 'mount' utility, but had no luck.

---

### Post by WRDN on 2010-09-03
Although not exactly what you are looking for, you can add an entry such as the one quoted to /etc/fstab, then run the command:

```
sudo mount -a
```

This re-reads /etc/fstab and remounts the drives listed in it.

---

