---
title: "Can't read write to file system"
date: 2010-09-07
forum: General Help
---

### Post by halfpower on 2010-09-07
I have a file system that I can't seem to read and write to.  I've tried everything I can think of.

```

root@xubuntu:/mnt/t1# ls -la
ls: cannot access .Trash-1000: Input/output error
total 116
drwxr-xr-x 14 root root 8192 1969-12-31 19:00 .
drwxr-xr-x  5 root root 4096 2010-09-07 21:30 ..
-rwxr-xr-x  1 root root   98 2010-09-07 20:43 DID.bin
drwxr-xr-x  7 root root 8192 2010-09-07 19:42 Music
-rwxr-xr-x  1 root root   40 2010-09-07 20:43 nonce.bin
drwxr-xr-x  6 root root 8192 2008-09-01 03:49 System
d?????????  ? ?    ?       ?                ? .Trash-1000
drwxr-xr-x  2 root root 8192 2010-06-16 14:13 Video
root@xubuntu:/mnt/t1# rmdir .Trash-1000
rmdir: failed to remove `.Trash-1000': Input/output error
root@xubuntu:/mnt/t1#

```

---

### Post by bodhi.zazen on 2010-09-07
boot a live CD and run fsck on the partition

```
fsck /dev/sda1
```

Change sda1 to the actual partition.

---

### Post by halfpower on 2010-09-07
Thanks.  I just backed up the drive, reformatted it, then moved the files back to the drive (except for the .Trash-1000 stray folder name thing).

---

