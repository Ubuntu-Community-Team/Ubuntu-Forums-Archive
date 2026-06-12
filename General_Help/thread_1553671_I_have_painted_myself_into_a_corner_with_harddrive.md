---
title: "I have painted myself into a corner with harddrive space"
date: 2010-08-15
forum: General Help
---

### Post by IQAndreas on 2010-08-15
A few months back I decided to double boot my computer with Windows 7 and Linux. I partitioned my 80GB harddrive as indicated by the attached image. I thought that 10GB would be enough for Ubuntu and the programs I use from day to day, but I am really starting to run out of space. 

The Windows 7 partition only contains about 35GB filled up, and I installed everything (including the OS) VERY recently and rarely use Windows. Almost everything in my Windows partition is very replaceable. It's mostly Steam games and other re-installable applications that take up so much space.


Would it be safe for mainly the Ubuntu install, but also the Windows install to repartition the Ubuntu space about 5GB "to the left"?

I'm not worried about overwriting a few Windows files. I'm worried about both partitions needing to be wiped and repartitioned or not working so NONE of the files on either are retrievable.

I only know the basics of how harddrives and partitioning works, so any reassurance or clarification would be helpful. But if I understand things correctly, disc space is written "from the left to the right" (from the diagram point of view), so it shouldn't be a problem, or?

---

### Post by matchett808 on 2010-08-15
painted yourself into a corner? too many .bmp files? 

(sorry I am on a roll of sarcastic comedy 1 liners atm!!)

I have successfully erased a HDD partition before and then extended ubuntu over it, but I would wait and see what other peep's say as I think part or all of what I done was frowned upon but I done it on a non-production compo.....

---

### Post by IQAndreas on 2010-08-15
Hehe... Witty, but not hilarious. ;)

> **matchett808 said:**
> I have successfully erased a HDD partition before and then extended ubuntu over it,
Though (and I probably should of clarified this) I don't want to replace the Windows partition. I'm still wanting the Windows side to be bootable with minimal file loss, I just want to steal some harddrive space from it to make room for more of my Ubuntu install.

And just ignore the recovery partition in the image. I don't want to touch that, as it is quite filled up already.

---

### Post by drs305 on 2010-08-15
From your image, it looks like you would have to shrink Windows, expand the extended partition, then expand your Ubuntu partition. This will take some time, as moving partitions 'left' means moving lots of bytes.

If you want to expand /, take a look at the second half of the first post in this thread, which gives you some advice on how to do this.
[Expanding an Ubuntu System Partition]("http://ubuntuforums.org/showthread.php?t=1219270")

Don't forget to defrag and backup important data before performing partitioning operations!

---

