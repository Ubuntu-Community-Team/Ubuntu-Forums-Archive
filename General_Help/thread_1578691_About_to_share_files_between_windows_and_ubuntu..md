---
title: "About to share files between windows and ubuntu."
date: 2010-09-20
forum: General Help
---

### Post by camoph on 2010-09-20
Hi. I hope to be clear with this problem, probably is a stupid one. I have Ubuntu 10.04 in my laptop and at the same time I have Windows 7 (partitioned disk). I use mostly Ubuntu, but I need windows for some stuff.
I want to share files of windows with Ubuntu (is weird but when I installed Ubuntu never gave me the option 
"share files from windows", I dunno why). Anyway, I can see the disk in Ubuntu, and I can see the folder /Documents and settings/, that creates windows by default with my files. However, the route is too long to arrive there from Ubuntu using the Terminal. I created a shadow link using lndir to arrive to my files easier. It works fine, however, sometimes when I go to the files using this route, these are lightened in red, and when I try to enter to one of these folders, the system doesn't recognize it. After a while, these are in blue and I can go in them. Why it is happening?. What I did Is the "correct" way to do it?. There is another way to do it? Thanks

---

### Post by garner_nc on 2010-09-20
Easiest thing to do is to create a data partition on your hard drive formatted ntfs and save all the files you want to share to it. Writing to your Windows 7 system partition using the Linux NTFS drivers is not a good idea. There have been reports of people getting their drive scrambled and thus un-bootable.

On my dual boot XP machine I have a 30 Gb partition for just this purpose. It's easy and reliable.

All the Best,
D> White

---

### Post by SeijiSensei on 2010-09-21
> **garner_nc said:**
> Writing to your Windows 7 system partition using the Linux NTFS drivers is not a good idea. There have been reports of people getting their drive scrambled and thus un-bootable.

I just did a quick search to read about these problems and can't find anything.  Could you post a link to an article that describes these corruption problems?

The [NTFS-3G FAQ](http://www.tuxera.com/community/ntfs-3g-faq/) doesn't report any corruption issues, nor do I see any being reported in Tuxera's forums.  The version of the driver on my Maverick system is still 2010.3.6, though; the current release version is 2010.8.8.  Perhaps we'll see an update soon.

---

