---
title: "Max amount of mounted partitions"
date: 2011-05-11
forum: General Help
---

### Post by rcmaehl on 2011-05-11
Okay, I'm just wondering because I'm going to to test out just how many partitions I can make and mount on GPT. Is there a theoretical limit on the amount of partitions or mounts allowed? I was thinking there would be depending on if you were running i386 or x86_64 because both can only handle up to a certain interger.

---

### Post by blind2314 on 2011-05-11
> **rcmaehl said:**
> Okay, I'm just wondering because I'm going to to test out just how many partitions I can make and mount on GPT. Is there a theoretical limit on the amount of partitions or mounts allowed? I was thinking there would be depending on if you were running i386 or x86_64 because both can only handle up to a certain interger.
 
 
I don't think this is something you'll have to worry about..or information that is readily accessible.
 
The maximum number of mountpoints for a given file system depends on the file system limits, since mountpoints (directories) are treated as a 'file'. For example, ext4 has a theoretical limit of ~4 billion files, but that's per file system.

---

### Post by seawolf167 on 2011-05-11
From man 8 fdisk

Max mount points:
IDE: 63; SCSI: 15

---

### Post by blind2314 on 2011-05-11
> **seawolf167 said:**
> From man 8 fdisk
 
Max mount points:
IDE: 63; SCSI: 15
 
 
Also from the man page: "fdisk  doesn't  understand  GUID  Partition  Table  (GPT) and it is not designed for large partitions." So I don't believe that limit applies in this case.

---

### Post by oldfred on 2011-05-11
Some have already tested this. 

srs5694 said 128 partitions, but even that is not a firm number, it depends on what partitions tools will see and work with.
[http://ubuntuforums.org/archive/index.php/t-1561008.html](http://ubuntuforums.org/archive/index.php/t-1561008.html)

See Post by srs5694
[http://ubuntuforums.org/archive/index.php/t-1644760.html](http://ubuntuforums.org/archive/index.php/t-1644760.html)

---

### Post by srs5694 on 2011-05-11
There are two issues here:


[list]
[*]**Partitions per device limit** -- This defaults to 128 for GPT, but it can be increased quite a bit (see below). The theoretical limits would be quite preposterous; each partition table entry consumes 128 bytes, so each 512-byte sector in the partition table can define four partitions. Each partition table is duplicated (main and backup tables), so those values are effectively doubled. If you fill the theoretical maximum-sized disk (2^64 sectors) with 1-sector partitions, you'd need to devote 2/5 of the sectors to the partition table and the rest to partitions, so you could theoretically have (3/5)*(2^64) = 1.1 x 10^19 partitions. You'd need ridiculous quantities of RAM to maintain information on that partition table, though; and this theoretical limit also assumes a hard disk much larger than any now available. On a modern 3 TB disk, GPT could theoretically support about 3,515,625,000 512-byte partitions. Why anybody would want to create 3.5 billion 512-byte partitions is beyond me, though. ;)
[*]**Mounted partitions limit** -- There may be kernel- or filesystem-specific limits on the number of simultaneous mounted filesystems. The number of directories supported, as blind2314 suggests, is one such limit; however, you could theoretically work around that by mounting partitions inside each other. I don't happen to know what the practical limits are for this, though.
[/list]


Neither of these limits varies with i386 (32-bit) vs. AMD64 (64-bit) architectures, at least not in terms of the on-disk data structures. The data structures for both partition tables and filesystems are independent of the CPU architecture -- otherwise you'd never be able to exchange disks between computers of different architecture. That said, there may be limits in terms of in-kernel data structures, but I don't know enough about the kernel's internal data structures to know if that's the case.

I seem to recall once doing a test in which I created over 128 partitions on an MBR disk. Linux recognized them all, but I didn't attempt to mount them all simultaneously. Others have reported that Linux tops out at a much smaller number of partitions per disk. I suspect the discrepancy has to do with udev configurations. I did my tests on a Gentoo system, FWIW; Ubuntu presumably uses different udev configuration files, and so might have different limits.

I can't find the limits that seawolf167 mentions in my fdisk man pages, on either a Gentoo or an Ubuntu system. I know that there used to be such limits imposed by the kernel (not by fdisk), but udev enables working around such issues.

Finally, to create a GPT disk with more than 128 partitions, you must extend the size of the partition table. AFAIK, only [GPT fdisk (gdisk and sgdisk)](http://www.rodsbooks.com/gdisk/) supports doing this (by using the "s" option on the experts' menu). The partition table size might be impossible to extend once you've created partitions, depending on their locations, since the partition table must occupy contiguous sectors at both the beginning and end of the disk; if existing partitions already reside where an expanded partition table should reside, it won't be possible to expand the partition table. The last I checked, libparted had a bug that prevented it from working with unusual-sized partition tables, so if you expand your partition table's size, you'll be restricted to using gdisk or sgdisk on it (or perhaps non-Linux tools).

Check the [Wikipedia entry on GPT](http://en.wikipedia.org/wiki/GUID_Partition_Table) for more information on its low-level data structures, if you want to investigate this topic in more detail.

---

### Post by rcmaehl on 2011-05-12
Wow! Thanks for all the replies and links! :KS

So, there's a theoretical limit of ~4 billion mount points (as files) with a limit of 128-ish partitions per device with GPT. However, what if I was to set a large amount of GPT devices in a RAID (if it's even possible, I only get that raid is basically multiple devices showing up as one device/drive)?

---

### Post by srs5694 on 2011-05-12
The limit for GPT isn't "128-ish"; it's precisely 128 by default, but that limit can be raised to arbitrary values *if* you decide to do so and use appropriate software to implement it.

As to RAID, it depends on how it's implemented. In Linux software RAID, you can have up to however many partitions the partitioning scheme on the underlying disks supports. You either combine partitions from each disk together and use those directly; or you combine partitions together and then treat them as disks and further subdivide them using the same or a different partitioning scheme. When using hardware RAID, the physical disks are combined together in the disk controller and appear to be a single disk to Linux, so you've got the same limits on the combination disk that you'd have on a conventional physical disk of the same size. I'm less familiar with motherboard-based software RAID (aka "fake RAID"), but I think that it gets combined together in a way that's conceptually similar to hardware RAID, although the device names are different.

Most of this is of basically just theoretical/academic interest. In practice, few computers need more than about a dozen partitions. Personally, I find that when dealing with complex or frequently-changing configurations, Linux's Logical Volume Manager (LVM) greatly simplifies configuration, at least when Linux is the primary OS. (Linux's LVM is Linux-only, so it doesn't help a lot when multi-booting with Windows, Mac OS, or any other OS.) If you need more than half a dozen or so filesystems, and if you frequently reconfigure them to modify your installed OSes, then adding, deleting, resizing, and moving physical partitions becomes a major hassle. The logical volumes of LVM are more easily added, deleted, and resized than are partitions, and there's no need to move them (except across physical devices when adding or removing hard disks). Thus, despite the fact there's an LVM learning curve, actually using LVM is much easier than using conventional partitions in such environments.

---

