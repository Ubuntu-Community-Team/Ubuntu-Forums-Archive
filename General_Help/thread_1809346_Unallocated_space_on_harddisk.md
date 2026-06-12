---
title: "Unallocated space on harddisk"
date: 2011-07-21
forum: General Help
---

### Post by mmax on 2011-07-21
I am mmax. Love linux, specialy Ubuntu . I am using Ubuntu since 9.04, now on 10.04. Still learning it's various uses, customization and fixing things everyday. I am also sharing a blog about learning and many experience about Ubuntu.
 

  Recently I have installed Ubuntu 10.04 onto my friends machine. I choose this version for it's long term support. Hard disk capacity is only 80 gb. It's quite older gazette.  Samsung hd080h. It is a fresh install without duel boot. At my first attempt I found that there are a 1mb unallocated space after each partition. I partitiond hd in this order-
 
boot= 500 MB
swap= 1GB
root= 10 GB
home= 18 GB
another 2 partitions for storing files (25 gb each).
Screenshot [http://1.bp.blogspot.com/-iWX-t2ezxIQ/ThyHMO5isnI/AAAAAAAABJ0/ik4XyxGKHZE/s1600/80gbpartition.png](http://1.bp.blogspot.com/-iWX-t2ezxIQ/ThyHMO5isnI/AAAAAAAABJ0/ik4XyxGKHZE/s1600/80gbpartition.png)

Then I thought I have done some wrong. So deleted all partitions and repartition it in another way.
screenshot: [http://3.bp.blogspot.com/-T0sGzJVErIE/Th3Yz9BEVbI/AAAAAAAABKE/BF0JFKqPPM8/s1600/80gbhdinfo.png](http://3.bp.blogspot.com/-T0sGzJVErIE/Th3Yz9BEVbI/AAAAAAAABKE/BF0JFKqPPM8/s1600/80gbhdinfo.png)

I have found that 1mb size unallocated spaces are still in my harddisk.
 screenshot: [http://1.bp.blogspot.com/-9m7LufwWorU/Th3cl8e6IgI/AAAAAAAABKU/s4YRlZr1oo4/s1600/unallocatedpartitions.png](http://1.bp.blogspot.com/-9m7LufwWorU/Th3cl8e6IgI/AAAAAAAABKU/s4YRlZr1oo4/s1600/unallocatedpartitions.png)

I repartion hd again in different order. screenshot [http://4.bp.blogspot.com/-szDf2VYUHZ0/Th8-7THl-4I/AAAAAAAABKc/kKsV0oaE460/s1600/sda80du.png](http://4.bp.blogspot.com/-szDf2VYUHZ0/Th8-7THl-4I/AAAAAAAABKc/kKsV0oaE460/s1600/sda80du.png)
but found same result again. screenshot [http://1.bp.blogspot.com/-cVXNGWG8mII/Th8-7swd2hI/AAAAAAAABKk/J6kvvWwotAk/s1600/sda80gp.png](http://1.bp.blogspot.com/-cVXNGWG8mII/Th8-7swd2hI/AAAAAAAABKk/J6kvvWwotAk/s1600/sda80gp.png)

Everytime I partion my harddisk with Ubuntu 10.04.1 installment process (following manual partition). I checked it in Luma 002 (Puppy linux) and Ubuntu 10.10. gparted 0.6.2. On both system gpearted do not show any unallocated space on this harddisk. But gparted 0.5.1 (on ubuntu 10.04) shows several unallocated space each time.

At last I partion my harddisk again in a ubuntu 11.04 running machin. Deleted all partions ([http://4.bp.blogspot.com/-64YWz0erCZU/Tihe2hyX0EI/AAAAAAAABLU/Jb81NL3S6_c/s1600/del80hd.png](http://4.bp.blogspot.com/-64YWz0erCZU/Tihe2hyX0EI/AAAAAAAABLU/Jb81NL3S6_c/s1600/del80hd.png)), repartition in another order ([http://4.bp.blogspot.com/-3tYhS7SahTc/Tihe2_xyxDI/AAAAAAAABLc/dIh40gPxn4U/s1600/ata-samsung-hd080h.png](http://4.bp.blogspot.com/-3tYhS7SahTc/Tihe2_xyxDI/AAAAAAAABLc/dIh40gPxn4U/s1600/ata-samsung-hd080h.png)) and found same result ([http://3.bp.blogspot.com/-yW9RadbmEyk/Tihe2SU3mOI/AAAAAAAABLM/LzDxQmmq4g8/s1600/unallocated-gparted0.5.1-80gb.png](http://3.bp.blogspot.com/-yW9RadbmEyk/Tihe2SU3mOI/AAAAAAAABLM/LzDxQmmq4g8/s1600/unallocated-gparted0.5.1-80gb.png))

Now I install Ubuntu 10.04 on this harddisk and came to this forum. I feel fear whether it is safe to use this harddisk or not. I just curious to know that what is it? Is it any kind of problem? Are there any defect on my harddisk? Or, is it a gparted version limitation/ disadvancement? Or I am doing same wrong process everytime?

Please help me to know the fact. Thanks

---

### Post by CatKiller on 2011-07-21
It's possible that gparted is lining up your partitions on some kind of boundary, or it might be some function of cluster size. Or something.

I wouldn't worry about it. A handful of Megs out of an 80 Gig hard drive isn't really a high proportion.

---

### Post by Bucky Ball on 2011-07-21
I assume you have three primary partitions and an extended partition with your other logical partitions in that?

It is only possible to have four primary partitions on one physical hard drive. BUT, you can have as many *logical* partitions inside an extended partition as you like.

PS: Rule of thumb to put /swap at end (from the days when that was slowest part of the drive).

---

### Post by mmax on 2011-07-21
> **CatKiller said:**
> 
I wouldn't worry about it. A handful of Megs out of an 80 Gig hard drive isn't really a high proportion.
I am not worried about wasting some megabyts. But I did not create them. Why they are created automatically?

---

### Post by mmax on 2011-07-21
> **Bucky Ball said:**
> I assume you have three primary partitions and an extended partition with your other logical partitions in that?
Thank you. I know it.

---

### Post by Bucky Ball on 2011-07-21
Also, any reason for a separate /boot partition? Any reason for the two 25Gb partitions as this is not a dual-boot machine by the looks so no reason for NTFS partitions. What are they used for? Couldn't you just make /home 50Gb bigger?

I know this is OT but curious. ;)

---

### Post by CatKiller on 2011-07-21
> **mmax said:**
> I am not worried about wasting some megabyts. But I did not create them. Why they are created automatically?

Partition allocation is a dark art :)

It's obviously a consequence of some of the settings that you're using, but I'd just ignore it. It's not like you're going to be looking at your partition table every day.

---

### Post by mmax on 2011-07-21
> **Bucky Ball said:**
> Couldn't you just make /home 50Gb bigger? I have not created any NTFS partition. All are ext3. If /home crashe then? What will I do?

---

### Post by Bucky Ball on 2011-07-22
> **mmax said:**
> I have not created any NTFS partition. All are ext3. If /home crashe then? What will I do?

Keep it backed up on an external device. You should be doing that anyhow. ;)

---

### Post by mcduck on 2011-07-22
> **Bucky Ball said:**
> Keep it backed up on an external device. You should be doing that anyhow. ;)

+1 to this. Backups on same devices are pointless, and to tell you the truth even backups on another device that's always connected to the computer are kind of a bad idea. The only truly reliable backup is one that's done to an external media that's stored somewhere away from your computer (and if it's a hard drive it shouldn't be connected to anything apart from the very time you are making the backups)

What comes to partitioning, making a separate boot partition is very rarely necessary these days, and it's actually more than likely to cause you problems at some point or other. I'd recommend just keeping /boot on the root partition instead.

---

### Post by mmax on 2011-07-22
Dear freinds,
This is not a post for saving space or backup anything or wasting megs. I told on my first post that, I want to know the technical facts. Why every-time some space left unallocated automatically. Is it a problem or is it a special feature or it is normal in linux?

Thanks

---

### Post by mcduck on 2011-07-22
> **mmax said:**
> Dear freinds,
This is not a post for saving space or backup anything or wasting megs. I told on my first post that, I want to know the technical facts. Why every-time some space left unallocated automatically. Is it a problem or is it a special feature or it is normal in linux?

Thanks

Looks like a normal feature of partitioning, the partitioner aligning partition starts to cylinder boundaries, which leaves a bit of unused space between where the previous partition stops and next one begins.

As far as I know Linux doesn't actually care if the partitions are aligned to cylinder boundaries or not, but Windows on the other hand might have problems if they aren't aligned.

There's also the question of disk being in LBA mode versus being in CHS mode, the first one aligns partitions to sector boundaries, while the latter one aligns them to cylinder boundaries. If you then switch the disk to another mode you'll see the partitions slightly out of alignment. Which ones again isn't a problem, for Linux at least.

So no, it's not a problem (unless you care about the few megabytes you might loose), it's not a special feature and it's normal with any operating system.

---

### Post by Bucky Ball on 2011-07-22
> **mcduck said:**
> The only truly reliable backup is one that's done to an external media that's stored somewhere away from your computer (and if it's a hard drive it shouldn't be connected to anything apart from the very time you are making the backups)



Listen to the duck ...

> **mcduck said:**
> LBA mode versus being in CHDS mode, the first one aligns partitions to  sector boundaries, while the latter one aligns them to cylinder  boundaries. If you then switch the disk to another mode you'll see the  partitions slightly out of alignment.

... and this will take you a long way toward understanding your predicament ... you might call it an artefact left over from what doesn't divide into 1024 ...

---

### Post by Quackers on 2011-07-22
Regarding the 1MB space in between partitions, I think gparted is now set to do this by default. Certainly logical partitions need a small space in between them - something to do with partition info stored in that gap.

---

### Post by mmax on 2011-07-25
> something to do with partition info stored in that gap. Thank you. This kind of information I am looking for. This post should marked as [SOLVED] :D

---

### Post by Quackers on 2011-07-25
You're welcome :-)
You can mark the thread as solved using Thread Tools near the top of the page.

---

