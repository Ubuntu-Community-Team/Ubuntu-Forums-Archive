---
title: "Re-sized partition error"
date: 2009-12-11
forum: General Help
---

### Post by Shmee89 on 2009-12-11
After attempting to resize my Vista partition with GParted and shrink it by 30Gb I receive an error upon mounting:  

&quot;Error mounting: mount exited with exit code 12: Failed to read last sector (303759344): Invalid argument HINTS: Either the volume is a RAID/LDM but it wasn't setup yet,    or it was not setup correctly (e.g. by not using mdadm --build ...),    or a wrong device is tried to be mounted,    or the partition table is corrupt (partition is smaller than NTFS),    or the NTFS boot sector is corrupt (NTFS size is not valid). Failed to mount '/dev/sda2': Invalid argument The device '/dev/sda2' doesn't seem to have a valid NTFS. Maybe the wrong device is used? Or the whole disk instead of a partition (e.g. /dev/sda, not /dev/sda1)? Or the other way around?&quot;


fdisk -lu lists my new partition as being: 
&quot;/dev/sda2         3074048   235753874   116339913+   7  HPFS/NTFS&quot;

  with the last sector actually being 235753874 instead of the 303759344 stated by mounting. This means that when I mount the drive it tries to read sectors outside of the range of the partition  Can I solve this without re-formatting? I want to keep /dev/sda1 (Windows Recovery Partition) and /dev/sda2 (Vista Partition) intact (I have other linux partitions on the same hard drive but they are easy to back up and reinstall)

---

### Post by Vishnu V on 2009-12-11
can you post me output of 
```

cat /etc/fstab

```

---

### Post by Mark Phelps on 2009-12-11
> **Shmee89 said:**
> After attempting to resize my Vista partition with GParted and shrink it by 30Gb I receive an error upon mounting:  

I've posted dozens of times in these forums about NOT using GParted to resize Vista OS partitions due to the risk of corrupting the OS partition -- but I guess no one bothers to check first, before doing something potentially destructive, anymore.

You should ONLY be using the Vista Disk Management utility to shrink the Vista OS partition.  IF it won't shrink much, run defrag a couple of times and disable hibernation.  If it still won't shrink much -- there are good reasons for that and forcing shrinkage using GParted will corrupt the filesystem.

A chkdsk run in Vista may fix it, but if you can't reboot into Vista to do that, you will need to boot from your Vista DVD and run Startup Repair three times.

You DO have a Vista DVD, right?

---

### Post by Shmee89 on 2009-12-11
Sorry, I know do realise it is my own fault. I did try shrinking in Vista but when it only managed to shrink by 100mb or so the first thought in my head was "Aghhh hell, I'm just going to use GParted"

Unfortunately my laptop didn't come with a DVD only a recovery partition and the key

I may be able to get my hands on a copy of Vista Business to use with my key then it should be ok I guess... Just need to reformat completely and start again

I can actually force grub to try and boot off the partition and that allows me to get into the windows booter where I can launch start up repair or start windows normally: 
If I start normally then I see about 2 seconds of loading then the computer shuts down
If I start up repair it loads into repair but then the repair immediately presents an error telling me it can't access recovery tools

Thanks for the help but I think I will just back up the Recovery Partition and my data and then just start again from scratch

I've learnt my lesson now though, Thanks

---

### Post by Mark Phelps on 2009-12-11
Wait ... before you do that ... go to the NeoSmart Technology forums.  They have links to ISO images you can download of 32-bit and 64-bit Vista recovery CDs and Win7 recovery CDs.

You can download the ISO you need, burn it to CD, and boot from that to do Startup Repair.

This will prevent you from having to wipe out everything you have to do a complete restore.

---

### Post by theonhighgod on 2010-08-09
I've not had problems with gparted and resizing ntfs partions, i must have done it atleast 5 to 6 times this last year and not had a problem.

I used ddrescue to copy data of a hard drive from a computer that would'nt boot for a few reasons (none being the hard drive i through) with the aim of upgrading the hard drive with out reinstalling everything. I have done this many times before, usually after making a direct copy i have to run chkdsk and resize with gparted, but this time i've got an error that reads:

Error mounting: mount exited with exit code 12: Failed to read last sector (156294336): Invalid argument
HINTS: Either the volume is a RAID/LDM but it wasn't setup yet,
   or it was not setup correctly (e.g. by not using mdadm --build ...),
   or a wrong device is tried to be mounted,
   or the partition table is corrupt (partition is smaller than NTFS),
   or the NTFS boot sector is corrupt (NTFS size is not valid).
Failed to mount '/dev/sdd1': Invalid argument
The device '/dev/sdd1' doesn't seem to have a valid NTFS.
Maybe the wrong device is used? Or the whole disk instead of a
partition (e.g. /dev/sda, not /dev/sda1)? Or the other way around?


tried using testdisk and it crashes! this is the only time its crashed on me, (would highly recommend testdisk btw) if anyone's got any ideas been posting [http://ubuntuforums.org/showthread.php?t=1483826](http://ubuntuforums.org/showthread.php?t=1483826)

thanks

---

### Post by ankcrimson on 2012-09-18
Hi
I faced a similar problem but got it fixed by this 
[http://www.makeuseof.com/tag/fix-corrupted-windows-ntfs-filesystem-ubuntu/](http://www.makeuseof.com/tag/fix-corrupted-windows-ntfs-filesystem-ubuntu/)

all i did was:


sudo apt-get install ntfsprogs

which installed ntfsprogs


then i used the following command:

sudo ntfsfix /dev/sda5



you can replace sda5 with your own drive number which is sda2

hope this solves the problem

---

### Post by ankcrimson on 2012-09-18
:)

---

### Post by Mark Phelps on 2012-09-18
> **ankcrimson said:**
> ... then i used the following command:

sudo ntfsfix /dev/sda5 

Then, you were VERY lucky! NTFSFIX is NOT a Linux equivalent of MS Windows CHKDSK and can only repair the most basic of NTFS problems.

Best general rule of thumb: Windows utilities for Windows filesystems; Linux utilities for Linux filesystems.

---

### Post by oldfred on 2012-09-18
Actually installing ntfsprogs now uninstalls ntfs-3g. 

A year or two ago the two were merged and all the useful functions of ntfsprogs are now in ntfs-3g. You get an old version of ntfsprogs that now conflicts with ntfs-3g.

One good example of why we close older threads as they may have information that is not up to date. 

Thread closed.

---

