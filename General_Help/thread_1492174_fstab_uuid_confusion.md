---
title: "fstab uuid confusion"
date: 2010-05-24
forum: General Help
---

### Post by zetharx on 2010-05-24
In fstab, partitions can be identified by a few different methods, but I am observing strange behavior dependent on how the partition is referenced.

```
UUID=0f9a8472-bf45-49d8-8499-81c6d4e4a906	/media/600	ext3	user,noauto,rw,sync	0 2
```

and

```
/dev/sdb1	/media/600	ext3	user,noauto,rw,sync	0 2
```

These two lines written in fstab (only one at a time of course) both reference the same partition.  They both work, but the former causes Start Menu >> Places >> 600 to show twice.  The latter only shows once.  Can someone explain why this is and how I could get the UUID reference to only display one listing in "Places"?  Thanks in advance.

---

### Post by drs305 on 2010-05-24
The easiest thing to try, if you can live with it, is to remove the "user" entry. I found that if the "user" entry is removed from your mount options the double entry in Places is eliminated. (Note: "defaults") also works.

Another option is to keep the settings you have and make the mount point something other than /media (such as /mnt). Then the partition will not show at all in Places, but you can make a shortcut in the lower left section so you can access it. You would not be able to mount it via the lower left link however.

---

