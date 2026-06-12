---
title: "Boot hangs unless root mount point is absent from fstab -- why?"
date: 2010-11-20
forum: General Help
---

### Post by dlbeswick on 2010-11-20
Hi everyone, I started using Ubuntu a while ago. I have a little bit of previous experience with Linux. I'm using 64-bit 10.10.

A week or two after my initial install, Ubuntu started hanging during boot. The system was still responsive on some level though -- I could use shift-ctrl F7 and F2 to switch between ttys. Booting in recovery mode produced the same hang. I could still boot with an Ubuntu install disk on a USB stick, so I figured it wasn't hardware issues. I used this install disk boot to mount my Ubuntu drive and fiddle with different things to try and get it working. 

I made the boot sequence verbose and found it hung soon after mounting my root partition, but not always in the same place. I guess boot is done is parallel to a degree so it wouldn't always hang the same way. I tried the following, none of which worked:

1. Repairing OS using apt-get.
2. Unplugging all hard disks except boot drive.
3. Enabling and disabling AHCI, forcing IDE (Ubuntu is on an IDE drive.)
4. Removing all mount points I added from /etc/fstab, except root.
5. Using UUID to mount the root device in fstab.
6. Using /dev/disk/by-uuid to mount the root device in fstab.
7. Using /dev/sda1 to mount the root device in fstab.
8. Specifying errors=continue in fstab options.
9. Running fsck on the root drive (no errors.)
10. Forcing fsck on the root drive at boot.

What finally got it booting again was removing the root mount point from /etc/fstab altogether. I didn't expect that to work at all. I figure that something about the Ubuntu boot sequence presumes to mount root even if it's not in fstab.

The only thing I can think of that may have precipitated this was that after I read about mounting drives by UUID, I modified fstab and set my root partition to mount by UUID rather than by device path. I think Ubuntu stopped booting shortly after that. But the strange thing is that now, no matter how I mount root, whether by UUID or not, it hangs anyway. The only thing that works is removing root from fstab altogether. Does anyone know why this happens?

Thanks!

---

### Post by dcstar on 2010-11-20
> **dlbeswick said:**
> 
..........
The only thing I can think of that may have precipitated this was that after I read about mounting drives by UUID, **I modified fstab** and set my root partition to mount by UUID rather than by device path. **I think Ubuntu stopped booting shortly after that**. But the strange thing is that now, no matter how I mount root, whether by UUID or not, it hangs anyway. The only thing that works is removing root from fstab altogether. **Does anyone know why this happens?**

Thanks!

Probably because you stuffed up the fstab entry.

---

### Post by dlbeswick on 2010-11-20
It's a good theory when I think about it. But can you see anything wrong with any of these entries? These are all variations that I've tried.

/dev/sda1      /       ext4    errors=continue,users 0       1
/dev/sda1      /       ext4    errors=remount-ro,users 0       1
/dev/disk/by-uuid/bf19a070-8467-4b7b-9145-2a70fffceab4 /       ext4    errors=remount-ro,users 0       1
UUID=bf19a070-8467-4b7b-9145-2a70fffceab4      /       ext4    errors=remount-ro,users 0       1


When I first changed the fstab, I only modified the /dev/sda1 part. I didn't change anything else. I'm also mounting several other drives by UUID and that works fine.

---

