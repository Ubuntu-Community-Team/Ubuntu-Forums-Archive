---
title: "Partitioning"
date: 2010-04-13
forum: General Help
---

### Post by Daskies on 2010-04-13
So I've spent the better part of 3 hours trying to figure this out and I'm about to lose it. Basically I want to dual boot. One XP one Ubuntu. This I've done and was simple. Now what I want to do is make another partition that holds the files for both. I don't want to put programs on it, just every loose file I have. Ideally I would have a ~15gig XP partition, ~15gig Ubuntu partition, and the rest would be to hold my loose files.

So my "tree" looks like:
HD
- 210 GB NFTS XP partition (I want to slowly move out of this partition and into the new one. I'll have to move a few gigs, resize each partition, and move some more).
- 40 GB extended
-- 4 GB FAT (I tried using this to do what I wanted. Ubuntu doesn't have a problem with it. I can resize it. It looks hot. The problem is I can't find a way to get XP to recognize it).
-- 10 GB Ubuntu
-- 1 GB NFTS (I made this using XP to try and get things to work. I can see it under both XP and Ubuntu, but I can't resize it using GParted so it's pretty much useless.)
-- 25 GB free.

Any help is appreciated ("just put everything under XP or Ubuntu" isn't help, though).

---

### Post by dcstar on 2010-04-13
> **Daskies said:**
> So I've spent the better part of 3 hours trying to figure this out and I'm about to lose it. Basically I want to dual boot. One XP one Ubuntu. This I've done and was simple. Now what I want to do is make another partition that holds the files for both. I don't want to put programs on it, just every loose file I have. Ideally I would have a ~15gig XP partition, ~15gig Ubuntu partition, and the rest would be to hold my loose files.

So my "tree" looks like:
HD
- 210 GB NFTS XP partition (I want to slowly move out of this partition and into the new one. I'll have to move a few gigs, resize each partition, and move some more).
- 40 GB extended
-- 4 GB FAT (I tried using this to do what I wanted. Ubuntu doesn't have a problem with it. I can resize it. It looks hot. The problem is I can't find a way to get XP to recognize it).
-- 10 GB Ubuntu
-- 1 GB NFTS (I made this using XP to try and get things to work. I can see it under both XP and Ubuntu, but I can't resize it using GParted so it's pretty much useless.)
-- 25 GB free.


You cannot resize partitions or extended partitions that are mounted.

Please do a forum search for the many posts already on things like this.

---

### Post by Daskies on 2010-04-13
> **dcstar said:**
> You cannot resize partitions or extended partitions that are mounted.

Please do a forum search for the many posts already on things like this.
That post is literally useless to me. All you're doing is telling me I'm doing it wrong and giving me no indication on how I can fix it.

I can resize the FAT partition at any given time, but I can't open it in Windows.
I can't resize the NFTS partition and I'm given no option to "unmount" when using the CD version of GPartion. 

I don't know how to fix either of these and search of other topics doesn't help. I understand you probably get variations of the same questions constantly, but a post like yours is basically saying "if you're new to this go away; we're not going to help." You provide zero clues on what I'm looking for even through a search. Am I supposed to search for a way to load the FAT partition in Windows? Am I supposed to find a way to "unmount" the NFTS partition and resize it? I have zero idea which I should look for and "do a forum search" isn't giving me any answers.

---

### Post by f1r3flie on 2010-04-13
I suggest you backup all of your files then reinstall the operating systems with one 15gb windows partition and a ubuntu partition with the rest of the drive, then put the rest as a storage partition using a program called gparted on the Linux install. I've never used it, but I've read it is a nice, easy to use GUI program. There's more information on the application and how to use it in this thread: [http://ubuntuforums.org/showthread.php?t=539392](http://ubuntuforums.org/showthread.php?t=539392). You can then set up windows to be able to access the Ext3 partition using this software: [http://www.fs-driver.org/index.html](http://www.fs-driver.org/index.html). There's also more information on that in this thread: [http://ubuntuforums.org/showthread.php?t=115980](http://ubuntuforums.org/showthread.php?t=115980).

Hope this helps! :)

---

### Post by oldfred on 2010-04-13
If your swap file is in the extended partition, a liveCD will use it so the entire extended partition is mounted. You can right click on the swap and swapoff to allow editing of all the partitions in the extended.

Partitioning basics with some info on /data
[http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition](http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition)
Mount, hide & link windows partition
[http://ubuntuforums.org/showthread.php?t=1397508](http://ubuntuforums.org/showthread.php?t=1397508)
Share Windows partition:
[http://lifehacker.com/348858/use-a-single-data-store-when-dual-booting](http://lifehacker.com/348858/use-a-single-data-store-when-dual-booting)

---

