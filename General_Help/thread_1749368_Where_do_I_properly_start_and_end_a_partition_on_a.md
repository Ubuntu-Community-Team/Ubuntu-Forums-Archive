---
title: "Where do I properly start and end a partition on a WD20EARS?"
date: 2011-05-04
forum: General Help
---

### Post by metalf8801 on 2011-05-04
The WD20EARS is a 2TB hard drive that has 4096 or 4K sectors instead of the older 512 sectors 

From what I've read I know that ever partition needs to begin on a multiple of 8 so if the first partition starts on 2048 that should work. However, I'm not sure where the partitions need to end. Does the last sector need to be a multiple of 8 or will that cause problems with the next partition? 


I read the following on [http://www.johannes-bauer.com/linux/wdc/?menuid=3]("http://www.johannes-bauer.com/linux/wdc/?menuid=3")

"You also have to take care that the last sector yields mod 7 divided by 8 (as fdisk displays the sectors inclusive, not exclusive). Therefore, this would work fine:" (What does MOD mean? I can't find it used in the same way anywhere else.) and then this exmaple &#8220;Here, we have created a partition from LBA 2048 to LBA 2847 (all inclusive). 2048 MOD 8 = 0, which is good. 2847 MOD 8 = 7, which is also good. You will notice the total partition size is divisible by 4096&#8221; Why is it good that the partition ends on 2847? 

If anyone can help that would be great!
Thank you
Dan

---

### Post by searchfgold6789 on 2011-05-04
GParted does it all automatically, right? Will the filesystem be seriously damaged if the partition does not start and end on a certain number?

---

### Post by srs5694 on 2011-05-04
Short answer: Don't worry about the partition's end point.

Long answer: "MOD" means [modulo]("http://en.wikipedia.org/wiki/Modulo_operation") -- basically just the remainder after division. The emphasis placed on this issue is misplaced, though. The reason for aligning the starts of partitions has to do with the way data are laid out by most filesystems -- namely, in 4 KiB chunks starting with the first sector of the partition. If these chunks don't align with the drive's 4 KiB physical sector size, performance will be degraded. This reason has nothing to do with the end point of the partition. The only advantage to being careful with the partition's end point is to minimize wasted space, by keeping the amount of space between partitions at 0. In a worst-case scenario, a gap between partitions will waste close to 1 MiB of disk space -- that's 0.000095% of a 1 TiB disk's size. Thus, I wouldn't worry about it. You'll waste far more space because of packages you never use, backup files, etc.

---

### Post by metalf8801 on 2011-05-04
> **searchfgold6789 said:**
> GParted does it all automatically, right? Will the filesystem be seriously damaged if the partition does not start and end on a certain number?

From what I've read no Gparted doesn't do it automatically or at least it didn't. Hopefully ether this has already changed and I can't find any confirmation of that or it will soon be changed. 

Partitioning a 4K hard drive improperly won't damage the file system but it can cut the performance of the hard drive by up to 50%.

---

### Post by metalf8801 on 2011-05-04
> **srs5694 said:**
> Short answer: Don't worry about the partition's end point.

Long answer: "MOD" means [modulo]("http://en.wikipedia.org/wiki/Modulo_operation") -- basically just the remainder after division. The emphasis placed on this issue is misplaced, though. The reason for aligning the starts of partitions has to do with the way data are laid out by most filesystems -- namely, in 4 KiB chunks starting with the first sector of the partition. If these chunks don't align with the drive's 4 KiB physical sector size, performance will be degraded. This reason has nothing to do with the end point of the partition. The only advantage to being careful with the partition's end point is to minimize wasted space, by keeping the amount of space between partitions at 0. In a worst-case scenario, a gap between partitions will waste close to 1 MiB of disk space -- that's 0.000095% of a 1 TiB disk's size. Thus, I wouldn't worry about it. You'll waste far more space because of packages you never use, backup files, etc.

Thank you srs5694 that's great to know

---

### Post by srs5694 on 2011-05-04
> **metalf8801 said:**
> From what I've read no Gparted doesn't do it automatically or at least it didn't. Hopefully ether this has already changed and I can't find any confirmation of that or it will soon be changed.

Recent versions of GParted default to 1 MiB alignment, which works with any modern disk or RAID array. I don't recall the exact version number where the transition was made, though.

> Partitioning a 4K hard drive improperly won't damage the file system but it can cut the performance of the hard drive by up to 50%.

In some cases it can be much much worse than that -- or occasionally not nearly that bad. See [this article](http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/) I wrote on the topic, complete with benchmarks. The good news is that ext4fs, which is quite popular now, seemed to be much less impaired than most others, with only a 4-8% penalty on most write operations, although it suffered from an unusually large 25% read penalty on small files. The bad news is that the mean performance degradation on small-file writes across six filesystems was a factor of 10.9 -- that is, an operation that takes 10 seconds on a properly-aligned filesystem would take 109 seconds on an improperly-aligned one. The magnitude of the problems astounded me. I ran the tests several times, and in several different ways, to convince myself they were real!

---

### Post by metalf8801 on 2011-05-04
> **srs5694 said:**
> Recent versions of GParted default to 1 MiB alignment, which works with any modern disk or RAID array. I don't recall the exact version number where the transition was made, though.



In some cases it can be much much worse than that -- or occasionally not nearly that bad. See [this article](http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/) I wrote on the topic, complete with benchmarks. The good news is that ext4fs, which is quite popular now, seemed to be much less impaired than most others, with only a 4-8% penalty on most write operations, although it suffered from an unusually large 25% read penalty on small files. The bad news is that the mean performance degradation on small-file writes across six filesystems was a factor of 10.9 -- that is, an operation that takes 10 seconds on a properly-aligned filesystem would take 109 seconds on an improperly-aligned one. The magnitude of the problems astounded me. I ran the tests several times, and in several different ways, to convince myself they were real!

Thank you for your corrections

---

### Post by mastablasta on 2011-05-05
if you have access to windows computer the WD offers tools for propper alignment. I am not sure if such tools would work via WINE.
 
Here is the info on alignment: [http://www.wdc.com/global/products/features/?id=7&language=1](http://www.wdc.com/global/products/features/?id=7&language=1)
 
if you scroll down you will find a link on how to do it in linux with parted with all information needed.
 
>  
Parted is one of the better tools and from version 2.1 onwards it includes support for aligning Advanced Format drives


---

### Post by metalf8801 on 2011-05-06
> **mastablasta said:**
> if you have access to windows computer the WD offers tools for propper alignment. I am not sure if such tools would work via WINE.
 
Here is the info on alignment: [http://www.wdc.com/global/products/features/?id=7&language=1](http://www.wdc.com/global/products/features/?id=7&language=1)
 
if you scroll down you will find a link on how to do it in linux with parted with all information needed.

I did look at it awhile back but it didn't seem like it would help me since I'm not going to install Windows XP on the WD20EARS hard drive which I believe is what the alignment to is for. 

Thank you for trying to help 
Dan

---

