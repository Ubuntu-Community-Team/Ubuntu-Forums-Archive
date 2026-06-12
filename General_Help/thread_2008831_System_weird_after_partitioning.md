---
title: "System weird after partitioning"
date: 2012-06-23
forum: General Help
---

### Post by Lateralus138 on 2012-06-23
Hi all, I only use Ubuntu as a second os to help fix problems on Windows (and to test out), it is dual booted with Windows as my primary and recently I realized when I first partitioned my drives I gave Ubuntu way, way, way more than I needed on it and so the other day I put in my gparted cd and commenced to resizing the Ubuntu partition to add more to a second ntfs partition I have. The Windows partition is separate from the Windows OS, it is just a storage part and had about 20 gigs in it. My original Ubuntu had around 104 gigs or so and have of that is Windows files I've got stored there. Anyway I have very little room on my Windows OS partition and I didn't want to mess up any data so I transfered all that data to my Ubuntu part and still had around 15 gigs left on ubuntu. I put gparted in and I resized the Ubuntu down taking that 15 gigs away and added it to the 20 gig ntfs part leaving ubuntu with almost no space at all and I knew this, but I don't really care because Ubuntu is usually easy enough to fix and it's not my main OS. So now I have the Ubuntu part which is supposed to be around 89 gigs and my new ntfs part is 36 gigs.... when entering Ubuntu again I had the "System running in low graphics mode and so I fixed that and entered Ubuntu. I got a message about having no space at all and so went in to where my temp files for the new partition and they were still there and so I opened terminal as root and opened Nautilus and deleted those files from there, but they weren't in the trash bin... I opened the disk usage analyzer and what I saw was weird. I have so little space it wont let me save a screen shot and for some reason wouldn't let me save the screen shot to windows so I have to explain to you what I saw...

At the top it shows total size as 96 gigs (weird as it's only 89 gigs) and I scanned the whole file system and it says the whole drive is only 36 gigs which is what my new windows partition is. I opened a file manager into the root folder and selected all folders and looked at the properties and it says it's over 140 TBS!!! Yeah right my whole system is only over 300 gigs... 

I opened up Gparted in Ubuntu and it showed that  my ubuntu partition as 89gigs, what it's supposed to be and my 36 gig ntfs part write below it. After I deleted the temp Windows files it should read that I have around 20 gigs of 89 gigs free. 

Can someone help me please?

---

### Post by oldfred on 2012-06-23
Just to confirm there are no partition issues, post this:

sudo fdisk -lu
This only shows mounted partitions, so mount or click on other partitions in Nautilus to mount them first.
df -h

Some tools show the totals with all the mounted partitions, so it may be more than what you think, but the TB size is obviously an issue.

You need to houseclean. Just deleting does not remove from trash and you definitely need to empty that.

HOWTO: Recover Lost Disk Space - drs305
[http://ubuntuforums.org/showthread.php?t=1122670](http://ubuntuforums.org/showthread.php?t=1122670)
HOWTO: Cleaning up all those unnecessary junk files...
[http://ubuntuforums.org/showthread.php?t=140920](http://ubuntuforums.org/showthread.php?t=140920)

---

### Post by David Andersson on 2012-06-23
> **Lateralus138 said:**
> 
At the top it shows total size as 96 gigs (weird as it's only 89 gigs)

That is because there are different Giga units (and kilo,Mega,Tera). See [http://en.wikipedia.org/wiki/Gibibyte](http://en.wikipedia.org/wiki/Gibibyte). Windows show binary gigabyte as GB (old de facto standard) and does not use decimal gigabyte (AFAIK). Ubuntu show binary gigabyte as GiB and decimal gigabyte as GB (new real standard).

96 GB is about the same as 89 GiB so what you see it is exactly as weird as it should be.

---

### Post by Lateralus138 on 2012-06-23
> **David Andersson said:**
> That is because there are different Giga units (and kilo,Mega,Tera). See [http://en.wikipedia.org/wiki/Gibibyte](http://en.wikipedia.org/wiki/Gibibyte). Windows show binary gigabyte as GB (old de facto standard) and does not use decimal gigabyte (AFAIK). Ubuntu show binary gigabyte as GiB and decimal gigabyte as GB (new real standard).

96 GB is about the same as 89 GiB so what you see it is exactly as weird as it should be.
Ok but below that where it shows the scanning it shows the file system as 36 gigs. I'm trying to clean the disk as stated above and I got a little cleared, but the deborphan and localepurge were not installed and I had enough space to install localepurge and cleaned about 179 mbs , but Im having trouble install deboprhan from the software center and terminal. Feeding twins right now so I'll get back at you with more later on...

---

### Post by Lateralus138 on 2012-06-23
Ok wow thanx guys especially oldfred, after viewing your links I have just cleared over 45 gbs from the system, I did not know after a few years of messing with Ubuntu and Linux that when you deleted a file it doesn't completely remove the files and I had been using rm to delete things. I do spend more time in Windows though. I have a few errors to fix, but I know how to do that but this completely fixed my problem at hand, thanx again.

---

