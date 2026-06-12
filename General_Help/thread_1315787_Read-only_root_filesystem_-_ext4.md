---
title: "Read-only root filesystem - ext4"
date: 2009-11-05
forum: General Help
---

### Post by bribera on 2009-11-05
I'm posting this in case anyone else runs into this issue.

First, the particulars:
[LIST]
[*]I'm running 9.10 on x86_64, and my root partition is ext4.
[*]I've mounted my ext4 partitions as "barrier=0,noatime,errors=remount-ro" - this is not really that safe, and probably caused my issues.
[/LIST]

This is a work computer, and I leave it on 24/7. When I started using it this morning, I couldn't write to any file on the root partition -- **the partition was mounted as read-only**.

I assumed this meant a drive error of some sort, so I rebooted to see if fsck would repair the errors - nope, it didn't! The bootloader **couldn't even mount the drive**. I entered my root password to start maintenance mode, and fixed the drive errors manually:

```
fdisk -A -a
```

This command tells fdisk to run through /etc/fstab and check each partition entered there (-A), and to automatically fix any errors without confirmation (-a). Given my choice of ext4 and mount options, there's a small chance I've lost some writes in this process. **Be careful** when choosing automatic repairs (-a) -- make sure that's really what you want!

---

### Post by tranquito on 2010-02-15
Similar thing keeps happening to me on a family computer, it seems to be specific to 9.10 though because other releases don't seem to have this problem. Could it be related to EXT4? The computer is an Dell Dimension E520. I also noticed that when Ubuntu starts to misbehave like this I am unable to mount External harddrives also with the same error. I have run fsdsk at boot at least 10 times. Is there a permenant solution?

---

### Post by ironclaw on 2010-02-16
> **bribera said:**
> ```
fdisk -A -a
```This command tells fdisk to run through /etc/fstab and check each partition entered there (-A), and to automatically fix any errors without confirmation (-a). Given my choice of ext4 and mount options, there's a small chance I've lost some writes in this process. **Be careful** when choosing automatic repairs (-a) -- make sure that's really what you want!

I think you mean fsck here, instead of fdisk. ;)

---

