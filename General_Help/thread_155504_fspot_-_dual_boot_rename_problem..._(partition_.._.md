---
title: "fspot - dual boot rename problem... (partition .. issue?)"
date: 2006-04-05
forum: General Help
---

### Post by dotdot on 2006-04-05
ok folks check this one out.

simple config - dual boot.
I'm using windows to scan as it's about 10times quicker than sane.
I collect my scans - now I have to rename them - in linux.
I start up f-spot - can't rename them as it a windows filesystem.

I think I'll start up fspot as root - then i can do what I wish - fails with can't open display.

It doesn't have to be this petty / complex does it ?

Any have suggestions where
1/ i can mount windows rw (c partition)
2/ then fspot can rename images scaned in windows...

..thanks in adv.
..

---

### Post by dcstar on 2006-04-05
[QUOTE=dotdot]
......
Any have suggestions where
1/ i can mount windows rw (c partition)
2/ then fspot can rename images scaned in windows...

..thanks in adv.
..[/QUOTE]
You can simply add a mount point in your /etc/fstab file, for example mine has:
```
/dev/hda1       /c		vfat    	umask=000,noatime,auto			0       0
```
You should be able to do it using System-Administration-Disks if you prefer.

---

