---
title: "Why cp is corrupting my Flash pen FAT32"
date: 2011-12-23
forum: General Help
---

### Post by Arishy on 2011-12-23
Here what I did:
mkfs -T vfat /dev/sdb1
checked with fdisk -l .....ok
cp xxxx (file name) /dev/sdb1

took it to another Ubuntu (11.10) It is NOT recognized
but... fdisk -l see it !!!!!!
but... fstab does NOT see it.!!!!!

I reformat it with the SAME command, Ubuntu 11.10 now it see it

Add to all that:

When I insert it in W7 it is asking to format it !!!!!

I gave up...

What I should do to use my flash (almost in 2012)!!!!!!!!!
Come on guys .....

---

### Post by dandnsmith on 2011-12-23
Instant reaction: let W7 format it - this follows the recommendations in things like mkfs, fdisk, fstab to format Windows type filesystems with Windows tools.

---

### Post by dcstar on 2011-12-24
> **Arishy said:**
> Here what I did:
mkfs -T vfat /dev/sdb1
checked with fdisk -l .....ok
**cp xxxx (file name) /dev/sdb1**

**took it** to another Ubuntu (11.10) It is NOT recognized
but... fdisk -l see it !!!!!!
but... fstab does NOT see it.!!!!!

I reformat it with the SAME command, Ubuntu 11.10 now it see it

Add to all that:

When I insert it in W7 it is asking to format it !!!!!

I gave up...

What I should do to use my flash (almost in 2012)!!!!!!!!!
Come on guys .....

[LIST=1]
[*]Do not copy to /dev devices. Use the mounted partition name.
[*]Always correctly Unmount or Eject USB devices otherwise they **will** be corrupted.
[*]Stop stuffing around with the command line and use the GUI tools provided for these things.
[/LIST]

---

### Post by jwbrase on 2011-12-24
> **Arishy said:**
> cp xxxx (file name) /dev/sdb1

Doing this ***will*** corrupt the flash drive. You need to mount /dev/sdb1 first, then copy the file to the directory you mounted /dev/sdb1 to.

/dev/sdb1 is a file representing the exact contents of the first partition on the flash drive, including formatting information. If you copy a file directly to it, you *will* overwrite formatting information, corrupting the partition.

---

### Post by Arishy on 2011-12-24
Thank you "all" I know now the reason for corruption.
I believe ubuntu can "mount" the external drive without me "telling" it to mount ...Or I am wrong here too ?????

I know the answer, and I know I am going back to the core of Linux where for all "valid" reasons you have to be in control ALL the time. cp is an important command it deserve extra error message !!!  

For now my problem is solved thanks to you. And yes David! I will stick to the GUI untill the Kernel respond properly to hot usb plugin.

Have a lovely holiday season

---

### Post by jwbrase on 2011-12-24
> **Arishy said:**
> Thank you "all" I know now the reason for corruption.
I believe ubuntu can "mount" the external drive without me "telling" it to mount ...Or I am wrong here too ?????

If the flash drive has a filesystem on it when you plug it in, it should mount automatically. But if there's no filesystem on the drive for it to mount when you plug it in, you'll have to mount it manually after you use mkfs to create a filesystem. (The next time you plug it in after that, though, it should automount).

---

