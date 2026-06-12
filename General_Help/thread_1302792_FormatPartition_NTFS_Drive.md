---
title: "Format/Partition NTFS Drive"
date: 2009-10-27
forum: General Help
---

### Post by rfkrocktk on 2009-10-27
I recently bought a 1.5 TB external hard drive. The drive is great (except it doesn't have a power button, or a sata port, or the ability to daisy chain, but beggars can't be choosers ;)), but I wanted to format it to ext4. 

I have a lot of data on the drive, upwards of 200-300 GB. I don't have a way of backing up this data, but I wanted to convert the drive to ext4 seamlessly. Is it possible to format the free space on the drive to an ext4 partition, move the files from the remaining NTFS partition to the new ext4 partition, and then expand the ext4 partition to fill the drive?

---

### Post by recluce on 2009-10-27
> **rfkrocktk said:**
> 
I have a lot of data on the drive, upwards of 200-300 GB. I don't have a way of backing up this data, but I wanted to convert the drive to ext4 seamlessly. Is it possible to format the free space on the drive to an ext4 partition, move the files from the remaining NTFS partition to the new ext4 partition, and then expand the ext4 partition to fill the drive?

Possible: yes, recomended: no

GParted can shrink the NTFS partition and then setup a new EXT4 partition in the free space. After you move the data, you could delete the partition and expand the EXT4 partition.

However, things can go wrong in that process and GParted warns you to have a backup before doing operations such as the one described by me. For that reason, I cannot recomend you do this, even though it is possible.

---

### Post by rfkrocktk on 2009-10-27
Awesome, just good to know that it's possible.

---

### Post by sergiodlc on 2009-11-03
Please report if you finally got away with it.

---

### Post by rfkrocktk on 2009-11-03
I still haven't tried it to be honest. The goal was to convert the whole thing to ext4, but I need to access the external HD from my virtual Windows machine so I'm kind of stuck. 

I HATE NTFS. If there were any way for me to do it without any side effects, I'd jump right on board. I prefer ext4 100% over NTFS, especially since I just spent around 3 days defragging a few of my drives.

---

### Post by recluce on 2009-11-03
> **rfkrocktk said:**
> I still haven't tried it to be honest. The goal was to convert the whole thing to ext4, but I need to access the external HD from my virtual Windows machine so I'm kind of stuck. 


Assuming that you are using Virtual Box:

Virtual Box allows you to setup shared folders between host and guest, which show up as network drives in a virtual Windows machine. In theory, you could just set the root directory of the external drive as the shared directory, effectively sharing the whole drive between Ubuntu and Windows, Windows never knowing which filesystem was used on the drive.

One more issue: if your external drive is connected through USB, there will be no speed advantage in EXT4 over EXT3. If you use ext3, you could install EXT2 drivers under Windows to access the drive from Windows (real and virtual machines).

And while you are evaluating file systems, why not read up on ZFS?

---

### Post by rfkrocktk on 2009-11-03
VirtualBox's virtual folders are unstable at best on the 3.08 from an Ubuntu host to a Window$ XP guest. Whenever I've tried doing things over shared folders other than GUI file transfers, I've had nothing but problems. Most programs, if needing to write to the shared folder (and it IS read/write, I made sure) just crash on the XP side. 

Are there less fragmentation risks using ext4 over ext3? I thought I had heard that somewhere. I'll have to mess around with an ext3 partition with Window$ using the drivers. 

I'll look into ZFS, thanks for the suggestion. I haven't heard too much about it. Does it sport good speed, low fragmentation, and compatibility with most Linux/Window$ operating systems?

---

### Post by recluce on 2009-11-03
> **rfkrocktk said:**
> VirtualBox's virtual folders are unstable at best on the 3.08 from an Ubuntu host to a Window$ XP guest. Whenever I've tried doing things over shared folders other than GUI file transfers, I've had nothing but problems. Most programs, if needing to write to the shared folder (and it IS read/write, I made sure) just crash on the XP side. 

I have not had that problem yet. I am running Virtual Box 3.0.10 (non-free) on Jaunty x64.

> 
Are there less fragmentation risks using ext4 over ext3? I thought I had heard that somewhere. I'll have to mess around with an ext3 partition with Window$ using the drivers. 

I'll look into ZFS, thanks for the suggestion. I haven't heard too much about it. Does it sport good speed, low fragmentation, and compatibility with most Linux/Window$ operating systems?

Note that ZFS is not quite here yet (it is implemented under FreeBSD, Solaris and others, but Linux just gets a fuse-driver for now), but it shows you what is possible with a modern file system.

On ext3 vs. ext4 on external drives: as long as you use USB, don't even worry about the performance difference. USB will be your bottleneck. While I don't remember too clearly (it has been a while since I allowed Windows access to any important data), I had an ext2 Windows Filesystem driver installed that integrated completely, so even Windows tools recognized the ext2-system, just like they do for FAT and NTFS.

Only drawback: ext2 has no journal.

---

### Post by rfkrocktk on 2009-11-03
It seems that my problem was fixed with the 3.10 release, but I'll confirm this later on to be sure:
[http://www.virtualbox.org/ticket/4106](http://www.virtualbox.org/ticket/4106)

From what I read of ZFS, it seems pretty ridiculous. Full RAID-Z, SSD caching, 300+ quintillion zetabyte theoretical storage... it's unheard of. Sounds like it'll be the last file system ever written. :) I really hope they can get around the stupid meaningless licensing issues to get kernel-level support.

---

### Post by recluce on 2009-11-03
> **rfkrocktk said:**
> It seems that my problem was fixed with the 3.10 release, but I'll confirm this later on to be sure:
[http://www.virtualbox.org/ticket/4106](http://www.virtualbox.org/ticket/4106)


In that case, I might just have passed by that problem without realizing it, since I moved from 2.x to 3.0.x relatively late and got updated to 3.0.10 within a couple of days.

> 
From what I read of ZFS, it seems pretty ridiculous. Full RAID-Z, SSD caching, 300+ quintillion zetabyte theoretical storage... it's unheard of. Sounds like it'll be the last file system ever written. :) I really hope they can get around the stupid meaningless licensing issues to get kernel-level support.

I especially love the "copy on write" and the snapshot feature. That would make the accidental overwriting of an important document a non-event. If I understand the details correctly, it would also make the trashcan obsolete, as the filesystem would make intelligent decisions of what to overwrite when - and only when - no further empty sectors are available on the disk.

---

