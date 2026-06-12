---
title: "mount iso file that contains multiple partitions"
date: 2009-08-07
forum: General Help
---

### Post by Das Oracle on 2009-08-07
Hi Guys,

I imaged a dell hdd recently using "dd" that has 2 partitions (one dell recovery and the main partition) I can't mount the iso file directly because I get this error:

```
user@host:/media$ sudo mount -t ntfs -o loop wd640/image.iso /media/dellpc/
NTFS signature is missing.
Failed to mount '/dev/loop0': Invalid argument
The device '/dev/loop0' doesn't seem to have a valid NTFS.
Maybe the wrong device is used? Or the whole disk instead of a
partition (e.g. /dev/sda, not /dev/sda1)? Or the other way around?

```

I am guessing it is having the issue because it is seeing there are multiple partitions in the iso. How would I mount just one partition of the iso?

---

### Post by Zeroangel on 2009-08-07
have you tried using fdisk to seperate the partitions?

[http://ubuntuforums.org/showthread.php?t=711773](http://ubuntuforums.org/showthread.php?t=711773)

---

### Post by Das Oracle on 2009-08-08
> **Zeroangel said:**
> have you tried using fdisk to seperate the partitions?

[http://ubuntuforums.org/showthread.php?t=711773](http://ubuntuforums.org/showthread.php?t=711773)

Thanks!!! That worked perfectly!

---

