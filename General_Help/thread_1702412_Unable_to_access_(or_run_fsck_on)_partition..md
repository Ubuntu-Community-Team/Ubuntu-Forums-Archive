---
title: "Unable to access (or run fsck on) partition."
date: 2011-03-07
forum: General Help
---

### Post by expergefacio on 2011-03-07
Running ubuntu 9.04 for a while now, i had to take a forced reboot because of a blank screen when returning my laptop from suspension. The result was a error of the kind: No init found. Try passing init= bootarg. Identical to [this one.]("http://pinoy-computing-tips.blogspot.com/2010/08/how-to-fix-ubuntu-error-no-init-found.html")

In Ubuntu live a "240 GB Filesystem" appears in the Places menu. Clicking it gives a "org.freedesktop.dbus.error.noreply"-error after several minutes.

Following solutions from threads with similar errors I have tried following (as sudo from Terminal on Ubuntu live):

cfdisk gives:commands
```
FATAL ERROR: Bad primary partition 1: Partition ends in the final partial cylinder
```sfdisk -l gives:
```
Disk /dev/sda: 30401 cylinders, 255 heads, 63 sectors/track
Warning: extended partition does not start at a cylinder boundary.
DOS and Linux will interpret the contents differently.
Units = cylinders of 8225280 bytes, blocks of 1024 bytes, counting from 0

   Device Boot Start     End   #cyls    #blocks   Id  System
/dev/sda1          0+  29752-  29753- 238984193    5  Extended
/dev/sda2   *  29752+  30401-    649-   5211136    c  W95 FAT32 (LBA)
/dev/sda3          0       -       0          0    0  Empty
/dev/sda4          0       -       0          0    0  Empty
/dev/sda5          0+  29178-  29179- 234374144   83  Linux
/dev/sda6      29178+  29752-    574-   4609024   82  Linux swap / Solaris
```fsck on sda1 gives:
```
fsck.ext2: Attempt to read block from filesystem resulted in short read while trying to open /dev/sda1
Could this be a zero-length partition?
```fsck on sda5 gives:
```
fsck.ext4: Device or resource busy while trying to open /dev/sda5
Filesystem mounted or opened exclusively by another program?
```dd on sda1:
```
2+0 records in
2+0 records out
1024 bytes (1.0 kB) copied, 0.0112032 s, 91.4 kB/s
```dd on sda5:
```
468748288+0 records in
468748288+0 records out
239999123456 bytes (240 GB) copied, 8231.21 s, 29.2 MB/s
```I then ran fsck on the sda5 image and was finaly able to mount it:
```
ubuntu@ubuntu:/$ sudo fsck -y /media/RANA/backup-ubuntu-sda5.img
[COLOR=Red][... return message left out, href; http://pastebin.com/XcKqmsDy ...]("http://pastebin.com/XcKqmsDy")[/COLOR]
ubuntu@ubuntu:/$ sudo losetup -o$[0*8225280] /dev/loop1 /media/RANA/backup-ubuntu-sda5.img
ubuntu@ubuntu:/$ sudo mount /dev/loop1 -t ext4 /mnt
ubuntu@ubuntu:/$ cd /mnt
ubuntu@ubuntu:/mnt$ ls
bin    core  home            lib         mnt   root     srv  usr      vmlinuz.old
boot   dev   initrd.img      lost+found  opt   sbin     sys  var
cdrom  etc   initrd.img.old  media       proc  selinux  tmp  vmlinuz
```Still this i more like a compromise than a solution. The ideal thing would be if I could run fsck directly on the disc. Not making it necessary move all my my data twice more, and more important not re-installing the whole thing again, considering all files lying consistently on the disc.

Any ideas?

---

### Post by srs5694 on 2011-03-07
> **expergefacio said:**
> Running ubuntu 9.04 for a while now, i had to take a forced reboot because of a blank screen when returning my laptop from suspension.
...
cfdisk gives:commands
```
FATAL ERROR: Bad primary partition 1: Partition ends in the final partial cylinder
```

It sounds like cfdisk needs to be updated. I doubt if it's really a problem, but I can't be 100% positive of that without more precise output. You could try posting the output of:

```
sudo fdisk -lu
```

That will give information with sufficient precision to tell me if there's really a problem. Even if there is, though, it won't be causing your most immediate problem.

> sfdisk -l gives:
```
Disk /dev/sda: 30401 cylinders, 255 heads, 63 sectors/track
Warning: extended partition does not start at a cylinder boundary.
DOS and Linux will interpret the contents differently.
Units = cylinders of 8225280 bytes, blocks of 1024 bytes, counting from 0

   Device Boot Start     End   #cyls    #blocks   Id  System
/dev/sda1          0+  29752-  29753- 238984193    5  Extended
/dev/sda2   *  29752+  30401-    649-   5211136    c  W95 FAT32 (LBA)
/dev/sda3          0       -       0          0    0  Empty
/dev/sda4          0       -       0          0    0  Empty
/dev/sda5          0+  29178-  29179- 234374144   83  Linux
/dev/sda6      29178+  29752-    574-   4609024   82  Linux swap / Solaris
```fsck on sda1 gives:
```
fsck.ext2: Attempt to read block from filesystem resulted in short read while trying to open /dev/sda1
Could this be a zero-length partition?
```

*Do not* run fsck on an extended partition! At best it will give you an error message such as you've reported. In theory, a disk check utility could get confused enough to seriously trash your disk if you did this; however, I don't know what sorts of safeguards fsck.ext2 in particular has to prevent this. It's possible that this specific utility is smart enough to never trash your disk in this way.

> fsck on sda5 gives:
```
fsck.ext4: Device or resource busy while trying to open /dev/sda5
Filesystem mounted or opened exclusively by another program?
```

This means that the disk is in use. You should do better by unmounting the partition (via "sudo umount /dev/sda5", if you booted using a live CD) and trying again.

One caveat: I recall a similar problem being posted a few months ago. As I recall, something was attempting to scan or mount the filesystem at boot time, hanging, and leaving the filesystem in a state in which it couldn't be unmounted for fsck to do its job. Unfortunately, I don't recall the exact solution in that case. Some possibilities I'd try include:


[list]
[*]Booting using a different system, such as [System Rescue CD](http://www.sysresccd.org/) or [PartedMagic.](http://partedmagic.com) It's conceivable that whatever is trying to access your disk from the Ubuntu live CD would not be present in some other system.
[*]Remove the disk from the computer, boot, and then plug it in via a USB adapter (or hot plug using SATA, if you're feeling a bit adventurous). That might bypass the disk check features and enable you to check the disk.
[*]A bit risky, but: Back up the partition table (using "sudo sfdisk -d /dev/sda > parts.txt", then copying parts.txt to an external device), wipe it using fdisk or sfdisk, reboot, restore the partition table (using "sudo sfdisk -f /dev/sda < parts.txt"), and see if you can then run fsck on the partition. Try this only if you fully understand the commands I've specified; if you don't, IMHO it's too risky to try.
[*]Do a dd copy to another device or file, check it, and then copy everything back.
[/list]


> dd on sda5:
```
468748288+0 records in
468748288+0 records out
239999123456 bytes (240 GB) copied, 8231.21 s, 29.2 MB/s
```I then ran fsck on the sda5 image and was finaly able to mount it:

At this point, you've done 2/3 of my final option. You could just try copying everything directly back using dd. Ordinarily, I'd only try that option as a last resort because of the need to copy everything twice, but as you've already copied it once, it may be easier and safer than some of the alternatives. I think I'd try some non-Ubuntu boot disc before copying the dd image back, though.

---

### Post by expergefacio on 2011-03-08
Only having some minutes on the computer earlier, I went for dd'ing the image file back to the hard drive after running fsck on it. And i am now actually able to boot from it, and run my ubuntu-install... 

Anyhow i still get the exact same errors when running (s)fdisk -l :/


btw, sudo fdisk -lu gives:
```
Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xf2993cd5

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            2046   477970431   238984193    5  Extended
/dev/sda2   *   477972480   488394751     5211136    c  W95 FAT32 (LBA)
/dev/sda5            2048   468750335   234374144   83  Linux
/dev/sda6       468752384   477970431     4609024   82  Linux swap / Solaris
expergefacio@Bananen:~$ 
```

---

### Post by srs5694 on 2011-03-08
Your partition table is a little bit unusual, but unless I'm missing something, it's perfectly legal. Thus, I'll stick with my earlier tentative conclusion that cfdisk needs updating.

There's a slim chance that you could make cfdisk happy by juggling your partitions around -- say by converting the Linux partitions into primary partitions. There are risks to doing that, though, so unless there's more to the issue than you've mentioned (or if I've overlooked something in what you've posted), I'd just leave it as-is and not use cfdisk. GParted, parted, fdisk, sfdisk, and others should do the job even if cfdisk complains.

---

