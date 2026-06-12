---
title: "dual booing file system strategy"
date: 2006-04-03
forum: General Help
---

### Post by hildog on 2006-04-03
OK,

Before I get a bunch of replies like "search this forum before asking the question", let me say that I have already done that, and I've found plenty of information which I'll use once I get one more answer.

I'm currently dual-booting Ubuntu & XP on my laptop...I've partitioned it so that I have an 80GB partition (currently formatted as NTFS) that is to be used as a documents/download partition shared by both OSs. Because I've had some bad luck in the past year with file systems getting corrupted, and because I know that writing to an NTFS partition is still considered "experimental", I'm looking for a general consensus as to what the safest course of action is. I figure my choices are:

*install the "experimental" ntfs-writing capability
*convert the partition to FAT32
*copy all my data to an external drive, convert to FAT32 (or NTFS & install the experiment), re-copy all the data back - this is the step I'm trying to avoid because of the time it'll take.

I realize that option 3 is going to be the safest, but what are the real risks with options 1 & 2 ? How "experimental" is writing to NTFS ? Is it safe to convert a file system without risking damaging or losing data ? What's the worst that can happen ? Or, I should say, what's the worst that has happened ?

---

### Post by aysiu on 2006-04-03
hildog, I think you know the answer.

The worst that could happen? You lose your data.
The best option? #3, of course.

You really should do #3 because it's not only the safest method in general, but you should have backups of your data anyway--even if you're not changing the filesystem, even if you're not installing a new operating system.

Backups are good practice if your data means anything to you.

I back up all my data (well over 35 GB's worth) to an external hard drive every week.

---

