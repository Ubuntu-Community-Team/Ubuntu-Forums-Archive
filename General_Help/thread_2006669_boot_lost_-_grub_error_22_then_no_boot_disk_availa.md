---
title: "boot lost - grub error 22 then no boot disk available"
date: 2012-06-19
forum: General Help
---

### Post by TheMrOrange on 2012-06-19
Hi all,

I have a Ubuntu 10.x system installed on a Dell laptop. No other OS installed with it.
Two days ago, at some stage after a reboot required for some system update, the system didn't reboot and grub came up with error 22
```

grub error 22 

```

from there, I booted from a live ubuntu cd:
fdisk -l showed me the hard-disk (on sda) and its partition on /dev/sda1. it recognizes the system as Linux and i can see the partition flagged for boot.

```

# fdisk -l

Disk /dev/sda: 160.0 GB
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x58000000

   Device Boot      Start         End            Blocks   Id   System
/dev/sda1   *           1     19457    156288321   83   Linux


```

I was able to mount the partition
```

mount /dev/sda1 /tmp/myhd

```
I looked inside it and (surprise) it's almost empty
```

# ls -R
.:
boot  lost+found

./boot:
grub

./boot/grub:
default  device.map  e2fs_stage1_5  fat_stage1_5  installed-version
jfs_stage1_5  minix_stage1_5  reiserfs_stage1_5  stage1  stage2
xfs_stage1_5

./lost+found:

```

I tried Boot Repair in order to to repair the Grub in the first place, then the grub together with the MBR. Boot Repair says that the boot was successfully repaired but when I reboot, no bootable device is found...

The hard-disk is last in the boot sequence and it doesn't matter if I move it forward.

Please have a look to the link below for Boot Repair output
paste.ubuntu.com/1049412

Please, any help is much appreciate.

Best,
Davide

---

### Post by YannBuntu on 2012-06-19
Hello Davide

Your partitions are broken.
You should not write any more on your disk until you recovered your documents (via TestDisk for example).
Then format the disk and reinstall everything.

---

### Post by oldfred on 2012-06-19
+1 on testdisk to see if you can recover your data.

Grub error 22 is from grub legacy, which we do not see much anymore as grub2 has been the standard since 9.10. You must have upgraded from an earlier version of Ubuntu to still have grub legacy.

I think Boot_Repair does not fix grub legacy, but it just installed syslinux boot loader which is a Windows work alike to boot Windows. But you do not show any kernels or other boot files, just some of grub legacy. So Boot-Repair could not see any Linux to repair.

---

### Post by TheMrOrange on 2012-06-19
Thanks, I will do try TestDisk.

I'm actually not too much worried about the data (I've backups) but the system configuration is quit important to me since it's a machine that has a particular setting of compilers and system variables for work...

I had quite a bad experience already recovering data from a broken HD. I couldn't recover the folders structure and all file names were modified... if TestDisk cannot make the partition boot again and only recovers files, I'm afraid, I will have to use an hammer to release a bit of stress ;)

Btw the system was originally a Ubuntu 8.x which comes with an old version of grub. The system was upgraded to versions 9 and 10 along last two years in order to keep a supported version on it. I wasn't aware the grub was outdated.

I'll keep you posted

Thanks,
Davide

---

### Post by YannBuntu on 2012-06-20
**@oldfred:** FYI, B-R can fix GRUB Legacy, but only if the necessary executables (grub-install..) are present. On TheMrOrange's system:
1) there are no GRUB executables, so B-R can't reinstall GRUB
2) There are also no apt executables, so B-R can't (purge&) download and reinstall GRUB
3) There is no detected non-Linux OS, but there is a partition (with no detected OS on it), so by default B-R put a generic (syslinux) MBR in sda and put the boot flag on this partition.

---

