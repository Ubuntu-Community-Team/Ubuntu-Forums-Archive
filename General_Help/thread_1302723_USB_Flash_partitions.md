---
title: "USB Flash partitions"
date: 2009-10-27
forum: General Help
---

### Post by nemiux on 2009-10-27
Hey, everyone. I have a 16gb flash, and I tried to install ubuntu on it, however, after one try ([http://www.pendrivelinux.com/ubuntu-...-from-live-cd/](http://www.pendrivelinux.com/ubuntu-...-from-live-cd/)) my flash divided in two and instead of 16gb, i was left with only 8. It happened before on the old flash, I mean the partitions. I used fdisk command to get it to normal, than windows asked me to format it, everything was sloved. However, with the new flash, i enter fdisk /dev/sdb (b is my flash letter there), and there is only one partition. I try to delete it create a new one, give it win95 fat 32 (hex code 'c'), but it didn't work, still 8gb on windows. Could someone help me with that? Thanks

---

### Post by Giblet5 on 2009-10-27
After you create the partition, did you use the 'w' command to write the partition table?

It displayed a warning, telling you that you need to reboot.

That is a lie.

Pull the stick out, wait 5, plug it back in (same as a reboot).

Now, check to see if the stick automounted. If so, unmount it and bring up fdisk again to check the partitioning. Is it correct now?

Format it ```
sudo mkfs.msdos -n "PENDRIVE" /dev/sdb1
```

Pull the stick, wait 5, plug it in.

Verify that you have a 16G fat32 filesystem and that it's correctly formatted.

ta da!

---

### Post by nemiux on 2009-10-27
Hey, thank you, It worked, my flash is normal again. The only question I have (to increase my knowledge), how does the mkfs commands work? What kind of them are there? Ty :)

---

### Post by H4F on 2009-10-27
> **nemiux said:**
> Hey, thank you, It worked, my flash is normal again. The only question I have (to increase my knowledge), how does the mkfs commands work? What kind of them are there? Ty :)

look at man mkfs . there you will find everything you need

---

### Post by alphaniner on 2009-10-27
There are many kinds.  For example, I'd never heard of **mkfs.msdos** before.  When I format a USB stick with Ubuntu I use **mkfs.vfat**.

In any case, if you want to learn more, start with
```
man mkfs
```

---------------

> It displayed a warning, telling you that you need to reboot.

That is a lie.


Painting with rather broad strokes there, no?  If that happened it's because he did something wrong: modifying the partition table while a partition on that device was mounted.  It might be helpful for him to understand that.

---

### Post by nemiux on 2009-10-27
Ty, anyway, I'm putting this thread [SLOVED]

---

