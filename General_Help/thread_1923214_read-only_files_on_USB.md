---
title: "read-only files on USB"
date: 2012-02-10
forum: General Help
---

### Post by lex1 on 2012-02-10
I am trying to delete some read-only files on a USB stick
I do have permission

the command I use is


mount -o remount,rw /mount/point

then I told the file system type is missing

can anyone suggest the correct line to use?

thanks
lex1

---

### Post by Khayyam on 2012-02-10
lex1 ..

Filesystem options remain the same as those on the original mount, so I'm not sure why your getting a "filesystem type" error. Anyhow, try with /dev/ .. without /dev I believe it reads /etc/fstab for mount info:
 
```
mount -o remount,rw /dev/sdX /mnt/point
```

If the error persists try setting the "-t <fstype>"

```
mount -o remount,rw -t <fstype> /dev/sdX /mnt/point
```
HTH ...

---

### Post by lex1 on 2012-02-10
thanksfor your post

forgot to mention

Feb 10 13:10:23 ubuntu kernel: [  757.972173] hfs: write access to a journaled filesystem is not supported, use the force option at your own risk, mounting read-only.

what force option is being refered to?

lex1

---

### Post by Khayyam on 2012-02-10
> **lex1 said:**
> thanks for your post

Lex1 .. your welcome

> **lex1 said:**
> forgot to mention ..

```
Feb 10 13:10:23 ubuntu kernel: [  757.972173] hfs: write access to a journaled filesystem is not supported, use the force option at your own risk, mounting read-only.
```

what force option is being refered to?

You are attempting to mount a "journaled" hfsplus filesystem. This is not "supported" as writing (rw) to a journaled filesystem **may** corrupt the journal (and so cause problems for OS X). The kernel is just warning you, it can be overridden by passing "force" to mount.

```
mount -o remount,rw,force /mnt/point
```


You do this at your own risk however. The best, or rather safest, method  is to boot OS X and use Disk Utilities to disable the journal on this  partition.

I've read of people not having any problems when force mounting journaled hfsplus filesystems, but you should take the warning into consideration.

HTH ...

---

### Post by lex1 on 2012-02-18
thanks for your post 
here is what is happeing at the moment

root@ubuntu:~# mount -o remount,rw,force /media/"Mac OS X Base System"
mount: warning: /media/Mac OS X Base System seems to be mounted read-only.
root@ubuntu:~#

tried the other way
mount -o remount,rw -t <fstype> /dev/sdX /mnt/point

is the fstype in brackets on the command line?
should it be hfs or hfsplus
seems from the sys file it could be sdb1 sdb2 sdb3

lex1


lex1

---

### Post by Khayyam on 2012-02-19
> **lex1 said:**
> root@ubuntu:~# mount -o remount,rw,force /media/"Mac OS X Base System"
mount: warning: /media/Mac OS X Base System seems to be mounted read-only.

Are you assuming it didn't remount because of the warning? Did you try to write to it?

> **lex1 said:**
> is the fstype in brackets on the command line? Should it be hfs or hfsplus? Seems from the sys file it could be sdb1 sdb2 sdb3

It is without brackets, hfsplus, and sbdX, where X would be the partition with the hfsplus filesystem.

best ... khay

ps. no need to PM, I recieve alerts.

---

