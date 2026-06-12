---
title: "Ext4 Mount problem during boot."
date: 2009-11-07
forum: General Help
---

### Post by Amzo2 on 2009-11-07
Well I made some changes to my fstab, to optimise my boot time, which fail, so I restored my fstab to the original and it still fails to mount. 

Can't mount root file system, then it mounts as read only.

```
proc            /proc           proc    defaults        0       0

/dev/sda1 /               ext4  relatime,errors=remount-ro,data=writeback 0 0

UUID=d9071792-f895-4bc2-84df-cf5bd90929da none            swap    sw              0       0

/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

```

---

### Post by Amzo2 on 2009-11-07
I got it to mount by changing it to this in fstab

```
/dev/sda1 /               ext4  defaults,user,exec, 0 0
```

But now, I can't access my files or load into a gui, because my documents were encrypted, and it won't mount them.

think it might just be best to re-install.

---

