---
title: "Path to External DVD"
date: 2012-08-18
forum: General Help
---

### Post by borgward on 2012-08-18
How do I determine the path to external DVD burner so that I can check the Md5sum of disk I just burned?

Ubuntu 10.04

---

### Post by llamabr on 2012-08-18
Try posting the output of:

```
df
```

and we can probably give you a clue (or maybe it will just be obvious).

---

### Post by Habitual on 2012-08-18
> **borgward said:**
> How do I determine the path to external DVD burner so that I can check the Md5sum of disk I just burned?

Ubuntu 10.04

Aren't you supposed to check the md5sum before you burn the iso?

---

### Post by borgward on 2012-08-18
Before, and after.

---

### Post by llamabr on 2012-08-19
Ya, it doesn't hurt to check it on the disk, too.

Did you find it?  If so, mark the thread solved.

---

### Post by borgward on 2012-08-19
[QUOTE=llamabr;12181297]Ya, it doesn't hurt to check it on the disk, too.

Did you find it?

~$ df
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda1            110650276  57886660  47142876  56% /
none                   1021800       304   1021496   1% /dev
none                   1026020       400   1025620   1% /dev/shm
none                   1026020        84   1025936   1% /var/run
none                   1026020         0   1026020   0% /var/lock
none                   1026020         0   1026020   0% /lib/init/rw
/dev/sr1               1509398   1509398         0 100% /media/Zorin OS 6 Core 64

~$ md5sum /dev/sr1/media/zorin-os-6-core-64.iso
md5sum: /dev/sr1/media/zorin-os-6-core-64.iso: Not a directory

~$ cd /dev/sr1
bash: cd: /dev/sr1: Not a directory

/dev$ md5sum /sr1/zorin-os-6-core-64.iso
md5sum: /sr1/zorin-os-6-core-64.iso: No such file or directory

/dev$ md5sum /sr1/media/zorin-os-6-core-64.iso
md5sum: /sr1/media/zorin-os-6-core-64.iso: No such file or directory

What am I doing wrong?

---

