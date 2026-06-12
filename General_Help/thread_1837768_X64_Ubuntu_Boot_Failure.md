---
title: "X64 Ubuntu Boot Failure"
date: 2011-09-02
forum: General Help
---

### Post by The Eight-Bit Link on 2011-09-02
I upgraded from ubuntu 32 bit to 64 bit by formatting the partition ubuntu was on and reinstalled. Only problem is it doesn't boot. When I went into recoverymod I get multiple ATA restart problems on the two drives in my case (except it attempts to restart all four ports: 0 1 2 and 3). It can't restart it, and after the third (or fourth) try it fails the drive and moves on. At the end of testing all the drives, it declares it cant find the root drive, then drops to a terminal. what's going on? Did I confuse GRUB? Is there an easy fix?

---

### Post by The Eight-Bit Link on 2011-09-08
Bump, still don't have Ubuntu working.
I don't really *need* it, but it's faster than Windows 7.

---

### Post by quarternote on 2011-09-08
I don't know about this exact problem, but few thing to check.
Do you get grub during the boot?
Can you get into terminal? If so, you can take a look at file /etc/fstab
That file contains all drives that should be mounted.
Some time ago i had problem when my drives does not use UUID codes. UUID is unique way to recognice partitions.

To see your partition you can use:
```
sudo fdisk -l
```
With this command you can find UUIDs:
```
ls -l /dev/disk/by-uuid
```

Also grub config files should have correct UUID.

You can also try to give some more info, so that some more experienced user may help you.

---

