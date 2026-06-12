---
title: "Repairing file system after partial fsck on mounted partition"
date: 2011-04-04
forum: General Help
---

### Post by Nicholas Escalona on 2011-04-04
I'm running an Acer Aspire 1830T-3721 dual-booting Windows 7 with Ubuntu 10.10 (Desktop).

Background:
So first I dropped my laptop a couple feet while Windows was running. The laptop immediately shut off and then tried to boot. Booting Windows results in an unfortunate "Windows has encountered a problem communicating with a device connected to your computer. The error can be caused by ... faulty hardware ... Status: Oxc00000e9 Info: An unexpected I/O error has occurred." But Ubuntu booted fine, and could access my NTFS files fine, so I was trying to work on the problem from there. I try a few utilities, looking at the partition table, etc without actually applying any changes.

Then I run a fsck on the drive. It loudly warns me that if I continue on a mounted drive, then I'm going to mess things up. In a moment of stupidity I push on, thinking that surely it would ask me for more configuration, or confirmation, before actually starting. The fsck runs for about 1 second before I Ctrl-C it, running some preliminary stuff and then just starting pass 1.

After this, Ubuntu won't boot anymore. Instead, it hangs just after the init-bottom script runs. If I boot with init=/bin/bash, I can get to a shell, and see that my file system is still there, but not sure what else to do.

I've been running off of a SysRescCD LiveCD, from which I've looked at the drive with testdisk. Testdisk reports that "the hard disk seems too small" while showing me the partition table.

I ran a fsck on the Linux partition; it fixed a bunch of things. There has been no apparent effect on the boot behavior.

What stuff can I run to give you guys more diagnostic information? Sorry I'm not sure what I would run just yet. Thanks for any help.

I can access all my files, back them up, and reinstall Ubuntu, but I'm hoping there's a better solution, perhaps one that will also help me repair my Windows installation (but I'm looking at one problem at a time here).

---

### Post by fela on 2011-04-04
You know, I would back up, reinstall both operating systems. You're lucky the drive's still okay, what with dropping the laptop (it must have shock protection).

BTW, how can you access all your files if testdisk says your 'hard disk is too small'? Sound's like an partition table corruption to me.

---

### Post by matt_symes on 2011-04-04
Hi

If the disc has SMART data use it to check the hard drive. 

You can do this from a liveCD using 'Disc utility'->'Check SMART data and run tests' option 

... or if your prefer the command line from a live CD/USB...

```
sudo apt-get install smartmontools
sudo smartctl -t long /dev/sdX
```

where sdX is the drive. Let it finish. It will take a while then view the data with

```
sudo smartctl -a /dev/sdX
```

```
sudo fdisk -l
```

will tell you the drive device name. That is a small L.

Kind regards

---

### Post by Nicholas Escalona on 2011-04-04
> **fela said:**
> You know, I would back up, reinstall both operating systems. You're lucky the drive's still okay, what with dropping the laptop (it must have shock protection).

BTW, how can you access all your files if testdisk says your 'hard disk is too small'? Sound's like an partition table corruption to me.

Okay - I copied away my files from Linux and set off to reinstall Ubuntu by LiveCD. However, when I got to the partitioning part of the installation, the install program didn't see any partition table at all on the hard disk. That was odd. I tried GParted - when I'm booted from the Ubuntu LiveCD, it thinks the whole hard disk is unallocated. On the other hand, fdisk works. That means my disk doesn't have a GPT, but only an MBR table, right? How can I rectify this?

> **matt_symes said:**
> Hi

If the disc has SMART data use it to check the hard drive. 

You can do this from a liveCD using 'Disc utility'->'Check SMART data and run tests' option 

... or if your prefer the command line from a live CD/USB...

```
sudo apt-get install smartmontools
sudo smartctl -t long /dev/sdX
```

where sdX is the drive. Let it finish. It will take a while then view the data with

```
sudo smartctl -a /dev/sdX
```

```
sudo fdisk -l
```

will tell you the drive device name. That is a small L.

Kind regards

The output of my "fdisk -l" is:

```
Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x20bd20bc

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        1658    13312000    7  HPFS/NTFS
/dev/sdb2            1658        1671      102400    7  HPFS/NTFS
/dev/sdb3   *        1671       52259   406347508+   7  HPFS/NTFS
/dev/sdb4           52259       60802    68623632    f  W95 Ext'd (LBA)
/dev/sdb5           52259       60448    65778688   83  Linux
/dev/sdb6           60448       60802     2842616   82  Linux swap / Solaris
```

This is exactly as it should be, I think -
sdb1 is Acer's PQSERVICE partition for eRecovery
sdb2 is Windows's SYSTEM RESERVED partition
sdb3 is Windows's main C: partition
sdb4 is the extended partition
sdb5 is (logical) Ubuntu's root partition
sdb6 is (logical) swap

"sudo smartctl -l selftest /dev/sdb" preceded by "sudo smartctl -t long /dev/sdb" gives me:

```
smartctl 5.40 2010-03-16 r3077 [x86_64-unknown-linux-gnu] (local build)
Copyright (C) 2002-10 by Bruce Allen, http://smartmontools.sourceforge.net

=== START OF READ SMART DATA SECTION ===
SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Extended offline    Completed: read failure       90%      2649         66636134

```

I attempted to follow the instructions here ([http://smartmontools.sourceforge.net/badblockhowto.html#e2_example1](http://smartmontools.sourceforge.net/badblockhowto.html#e2_example1)). The first bad block is in sdb3, but when I tried to open it with debugfs...

```
debugfs 1.41.12 (17-May-2010)
debugfs:  open /dev/sdb3
/dev/sdb1: Bad magic number in super-block while opening filesystem
```

Ubuntu's graphical Disk Utility tells me in the SMART Test data window that there are "7 bad sectors".

Thanks for your replies. :)

---

### Post by Nicholas Escalona on 2011-04-05
(Previous post has been incompletely edited and doesn't represent a consistent picture.)

I successfully reinstalled Ubuntu after following this guide:
[http://www.rodsbooks.com/missing-parts/index.html](http://www.rodsbooks.com/missing-parts/index.html)
This repaired my MBR so parted understood it and I could install Ubuntu. My extended partition's size was too big for the drive, and had to be reduced a bit.

Closing this thread because topic in title is no longer the primary issue. Thanks for your help.

---

