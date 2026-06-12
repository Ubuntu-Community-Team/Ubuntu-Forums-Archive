---
title: "Think dead hdd but idk. Need it fixxed..lol"
date: 2011-06-17
forum: General Help
---

### Post by smurfgod on 2011-06-17
I have a 500 gig internal hdd that fails to boot. BSOD on any sort of boot, nothing will load etc,etc. I have Ubuntu 11.041 running off a 16 gig flash drive and I'm trying to repair the drive.

GParted will not check the drive. HDD Rebuilder from Hirens gets halfway thru and errors out. All signs point to a failing hard drive, but the SMART status and self test are always good. 

I looked at the partition table,fdisk -l /dev/sda2, sda2 is my Windows install that want boot. sda1 is a 1.46gig System partition and sda3 is my Toshiba recovery partition.

fdisk -l /dev/sda2 output---root@Satellite-L675D:/home/jeff# fdisk -l /dev/sda2

Disk /dev/sda2: 487.8 GB, 487759806464 bytes
255 heads, 63 sectors/track, 59300 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x6e697373

This doesn't look like a partition table
Probably you selected the wrong device.

     Device Boot      Start         End      Blocks   Id  System
/dev/sda2p1   ?      120528      234814   918008208   4f  QNX4.x 3rd part
Partition 1 does not end on cylinder boundary.
/dev/sda2p2   ?      119381      153271   272218546+  73  Unknown
Partition 2 does not end on cylinder boundary.
/dev/sda2p3   ?      113202      147075   272087568   2b  Unknown
Partition 3 does not end on cylinder boundary.
/dev/sda2p4   ?      177064      177067       27487   61  SpeedStor
Partition 4 does not end on cylinder boundary.

Partition table entries are not in disk order


Can post output to whatever commands.


[IMG]http://lookpic.com/c1/i2/3367/os3rLI5p.png[/IMG]

Error from GParted----Check and repair file system (ntfs) on /dev/sda2  00:00:01    ( ERROR )
    	
calibrate /dev/sda2  00:00:01    ( SUCCESS )
    	
path: /dev/sda2
start: 3074048
end: 955729919
size: 952655872 (454.26 GiB)
check file system on /dev/sda2 for errors and (if possible) fix them  00:00:00    ( ERROR )
    	
ntfsresize -P -i -f -v /dev/sda2
    	
ntfsresize v2.0.0 (libntfs 10:0:0)
Device name : /dev/sda2
NTFS volume version: 3.1
Cluster size : 4096 bytes
Current volume size: 487759802880 bytes (487760 MB)
Current device size: 487759806464 bytes (487760 MB)
Checking for bad sectors ...
Bad cluster: 0x3beb61c - 0x3beb61c (1)
Bad cluster: 0x3beb640 - 0x3beb640 (1)
ERROR: This software has detected that the disk has at least 2 bad sectors.

---

### Post by DirtyPC on 2011-06-17
You could have broken sectors on your HDD. I'd recommend backing up all your data on your flash drive and formatting it.

---

### Post by apesa on 2011-06-17
Try using DDrescue or dd_rescue. They are both wrappers around dd. dd will copy your hdd at the block level. So even if you can't boot or read the drive, you may be able to reassemble the data. You will need a linux system and a 500GB HDD or larger for the target. The last time I used this it took over 6 days of chugging along to get most of 160GB of data off the drive.

---

### Post by dandnsmith on 2011-06-17
Just 2 points:

fdisk -l /dev/sda2 is just plain wrong - should be fdisk -l /dev/sda to get meaningful output.

don't use gparted  to repair NTFS - can give problems.

---

### Post by smurfgod on 2011-06-17
> **dandnsmith said:**
> Just 2 points:

fdisk -l /dev/sda2 is just plain wrong - should be fdisk -l /dev/sda to get meaningful output.

don't use gparted  to repair NTFS - can give problems.


fdisk -l /dev/sda output:

root@Satellite-L675D:/home/jeff# fdisk -l /dev/sda

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xee997df4

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         192     1536000    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2   *         192       59492   476327936    7  HPFS/NTFS
/dev/sda3           59492       60802    10521600    7  HPFS/NTFS

sda1 is labeled as "System"

sda2 is the OS itself with all my stuff

sda3 is a recovery partition that was there when we got the laptop

What should be the boot partition?? Right now it's sda2.


Thanks

---

### Post by dandnsmith on 2011-06-17
> sda1 is labeled as "System"
not on that evidence - sda2 carries the boot flag, and all 3 partitions say the "SYSTEM" (ie partition type) is HPFS/NTFS.
As to what partition gets booted - that depends on the boot loader.
If you're trying to repair that HDD, and it was one which came with Windows7 installed, then you're playing with fire.
I only know enough to know that I don't know how to sort it out - let alone work out a safe way for you to try it. You're probably better off sticking to Windows tools of the appropriate vintage, as they'll be au fait with the situation.

You might get better advice if you say what the inital setup was, and how you've modified it, and then what happened.

Sorry

---

### Post by pricetech on 2011-06-17
The very small partition at the front of the drive is typical of Windows 7.  Your second partition is where the boot files and OS are.  The third partition, as you know, is the recovery partition.

Anyway;

Back up your data if at all possible before you attempt anything else using any utility under any OS.

If your computer has a hard drive test, run it.  If not, see if you can download diagnostics from the computer manufacturer.  If you don't find that, download a diagnostic from the hard drive manufacturer.

If the drive is indeed bad, don't attempt to use it for anything you actually consider important, even if some utility you run says it's fixed.  It's not worth the risk.

Good luck with it.

---

### Post by smurfgod on 2011-06-21
OK.

I finally got a Windows 7 disk to boot, and ran chkdsk and t fixxed several bad cluster sets. They all resided in a Norton 360 install that never installed. Always BSOD after loading it.

Reformated the drive and am now running Windows 7 x64 HP and am fixing to setup a dual boot with 11.04.

reran chkdsk with /f/r and found nothing.. Am I in the clear??

And should I shrink my Windows partition instead of allowing Ubuntu to do it during the install??


Thanks


Edit:

> **dandnsmith said:**
> not on that evidence - sda2 carries the boot flag, and all 3 partitions say the "SYSTEM" (ie partition type) is HPFS/NTFS.
As to what partition gets booted - that depends on the boot loader.
If you're trying to repair that HDD, and it was one which came with Windows7 installed, then you're playing with fire.
I only know enough to know that I don't know how to sort it out - let alone work out a safe way for you to try it. You're probably better off sticking to Windows tools of the appropriate vintage, as they'll be au fait with the situation.

You might get better advice if you say what the inital setup was, and how you've modified it, and then what happened.

Sorry

I have modified nothing. This is the original setup. It just failed to boot one day.

---

### Post by dandnsmith on 2011-06-21
Sounds like you're OK there, with no problem reports.
It's much better to do the shrink using Win7 tools, if you can, as then Win7 boot process will be kept informed.

---

