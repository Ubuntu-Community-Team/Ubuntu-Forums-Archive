---
title: "Having issues regarding External HDD"
date: 2010-03-19
forum: General Help
---

### Post by GeRm305 on 2010-03-19
I had Ubuntu...(my main laptop is down right now so no Ubuntu until its up and going)..anyway, I formatted an external 2.5 HDD in Ubuntu to load music into it and use it for my car radio. My car radio only reads fat32 so i know the drive is formatted in fat32 but here is my problem.

Since my main laptop is down i am on a secondary laptop running windows 7..It reads the drive but says the space is unallocated. So a quick Google search gave me links to a few programs that are supposed to read a linux formatted drive and i have had no luck!

My question is, Since the drive is formatted in FAT32 shouldn't it read under ubuntu AND windows?...If i load my live disc it will read the drive fine. But i want to be able to do it under windows for now until my pc is back up and running...

Also i could but im trying to avoid reformatting the drive (although it works perfectly fine except in Windows)

Thanks for anyones help!

---

### Post by 2hot6ft2 on 2010-03-19
Have you considered using the livecd to gain access to the contents of the drive?
And yes win 7 "should" be able to read it but apparently not.

---

### Post by oldfred on 2010-03-19
How big is your drive?

this says win7 max is 32GB on FAT32.
[http://support.microsoft.com/kb/140365](http://support.microsoft.com/kb/140365)

---

### Post by GeRm305 on 2010-03-20
2hot: I can access the contents on the drive on the Live CD...Just trying to avoid having to use it to add a few new albums here and there

Oldfred: I guess that might be the problem...The drive is a 100gb...A buddy of mine wanted some albums and he put it on XP and it failed to read the drive...no luck with 7 either

But that makes no sense because not too long ago a lot of external HDD came formatted Fat32 right out of the box...the only draw back was if you had ONE file bigger than about 3.5gb it wont move to a fat32 drive but windows would def read fat32 500GB drives...strange.

---

### Post by srs5694 on 2010-03-20
I believe the Windows 7 32GB limit applies to formatting, and it will read bigger drives OK if they've already been formatted. I'm not positive of that, though.

GeRm305, you say you want to use this disk with your car radio. Have you done so already? If so, can the radio read the drive OK? If it does, don't try modifying the drive so that Windows can read it, too; you might just mess things up worse.

My suspicion is that the issue is one of the drive being partitioned with a FAT32 partition vs. the drive being set up with a "raw" FAT32 filesystem. Windows will normally expect a hard disk to have a partition table. I don't know how Windows reacts to hard disks that have "raw" filesystems on them without a partition table. I know Windows handles at least some unpartitioned removable media fine, but I wouldn't be remotely surprised to hear that it chokes on disks it perceives as hard disks unless they're partitioned.

Assuming the drive already holds data on it that you don't want to replace, you might want to try using a live Linux CD to check it out. If the fdisk command-line utility reports that it can't find a valid partition table, try mounting the raw disk device (/dev/sdb, for instance). If it mounts, then the disk is unpartitioned but has a valid filesystem on it. If fdisk reports partitions and you need to specify a partition number (as in /dev/sdb1) to mount a filesystem, then the disk is partitioned and Windows is having problems for some other reason.

---

### Post by GeRm305 on 2010-03-20
> **srs5694 said:**
> I believe the Windows 7 32GB limit applies to formatting, and it will read bigger drives OK if they've already been formatted. I'm not positive of that, though.

GeRm305, you say you want to use this disk with your car radio. Have you done so already? If so, can the radio read the drive OK? If it does, don't try modifying the drive so that Windows can read it, too; you might just mess things up worse.

My suspicion is that the issue is one of the drive being partitioned with a FAT32 partition vs. the drive being set up with a "raw" FAT32 filesystem. Windows will normally expect a hard disk to have a partition table. I don't know how Windows reacts to hard disks that have "raw" filesystems on them without a partition table. I know Windows handles at least some unpartitioned removable media fine, but I wouldn't be remotely surprised to hear that it chokes on disks it perceives as hard disks unless they're partitioned.

Assuming the drive already holds data on it that you don't want to replace, you might want to try using a live Linux CD to check it out. If the fdisk command-line utility reports that it can't find a valid partition table, try mounting the raw disk device (/dev/sdb, for instance). If it mounts, then the disk is unpartitioned but has a valid filesystem on it. If fdisk reports partitions and you need to specify a partition number (as in /dev/sdb1) to mount a filesystem, then the disk is partitioned and Windows is having problems for some other reason.

The radio reads the drive fine all my albums are on there and i can add to it with the livecd...Just wont read under windows...Ill give what you just stated a spin tommorrow and see how that turns out...

If i just format the drive in windows..will both windows AND ubuntu read it?

---

### Post by egalvan on 2010-03-20
> **GeRm305 said:**
> 
Oldfred: ..The drive is a 100gb...A buddy of mine wanted some albums and he put it on XP and it failed to read the drive...no luck with 7 either

not too long ago a **lot of external HDD came formatted Fat32 right out of the box**... windows would def read fat32 500GB drives...strange.

Too true, I saw a 1TB drive came formatted as FAT32...
wish I had checked the MBR on it...


> **srs5694 said:**
> **I believe the Windows 7 32GB limit applies to formatting,** and it will read bigger drives OK if they've already been formatted. I'm not positive of that, though.

Yeah, MS crippled it's own formatting software. There are workarounds, I just don't have them handy at the moment..


> issue is one of the drive being partitioned with a FAT32 partition vs. the drive being set up with a "raw" FAT32 filesystem. Windows will normally expect a hard disk to have a partition table. I don't know how Windows reacts to hard disks that have "raw" filesystems on them without a partition table. ... Windows handles at least some unpartitioned removable media fine, I wouldn't be surprised to hear that it chokes on disks it perceives as hard disks unless they're partitioned.

The vfat tools in parted are about as mature as anything can be,
 considering that they work on closed proprietary information (MS vfat).

I doubt that parted is not partitioning the drive correctly...
I don't believe parted will format a non-partitioned space..

Me, myself and I think this is most likely MS cutting ties with their old technology...


You may find that you need a fully-patched XP machine to do the work...

but I still think that parted is running fine...

(NOTE: I have no drives bigger than 750GB, so I have no first-hand knowledge of this, just going by what MS has done in the past.)

---

