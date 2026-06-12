---
title: "Unable to create formatted partitions"
date: 2010-03-13
forum: General Help
---

### Post by Intrepid Ibex on 2010-03-13
I can't create any formatted partitions in my hdd (/dev/sda) with Gparted or KDE Partition Manager.

With either I can only create an unformatted partition. When trying to reformat it, I get this: [http://img502.imageshack.us/img502/9089/snapshot6d.png](http://img502.imageshack.us/img502/9089/snapshot6d.png)

> WARNING: the kernel failed to re-read the partition table on /dev/sda (Device or resource busy).  As a result, it may not reflect all of your changes until after reboot.

So the problem is apprarently at kernel level. After that the partition will of course just be shown as "Unknown" - even after a reboot.
What kinda app could possibly reserve my partition table?

---

### Post by Intrepid Ibex on 2010-03-13
Ok, I might've fixed it myself. For some reason I had a DOS-compatible partition table and what I did was that I removed the compatibility :).
```
**root@Archlinux> fdisk /dev/sda **                                                                     ~

WARNING: DOS-compatible mode is deprecated. It's strongly recommended to
         switch off the mode (command 'c') and change display units to
         sectors (command 'u').

Command (m for help): **u**
Changing display/entry units to sectors

Command (m for help): **c**
DOS Compatibility flag is not set

Command (m for help): **w**
The partition table has been altered!

Calling ioctl() to re-read partition table.

WARNING: Re-reading the partition table failed with error 16: Device or resource busy.
The kernel still uses the old table. The new table will be used at
the next reboot or after you run partprobe(8) or kpartx(8)
Syncing disks.
[1] root@Archlinux> 
```

**E:** Just had to do from live-CD.

---

### Post by pwn on 2010-06-11
I have the same problem, and this solution doesn't work for me. I'm not able to create a new partition.

---

### Post by Intrepid Ibex on 2010-08-01
It doesn't indeed because that is not the fix. I just _thought_ it would work.

But this thing has been fixed (probably with the kernel (2.6.34)) upstream. I'm myself using Arch Linux, with Ubuntu this should work out-of-the-box since the workaround (patch) had already been implemented with Ubuntu a long time ago but I never found out to what component the fix was (but most likely to the kernel).

---

