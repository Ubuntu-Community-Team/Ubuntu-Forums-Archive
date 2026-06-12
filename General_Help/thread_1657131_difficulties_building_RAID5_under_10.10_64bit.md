---
title: "difficulties building RAID5 under 10.10 64bit"
date: 2010-12-31
forum: General Help
---

### Post by jedigrover on 2010-12-31
Greetings--

I recently went shopping at newegg for components for a new home server to fulfill multiple needs--chief amongst them to replace an aging old Athlon box which has been running a 4TB software raid for years now.

So I ordered an ASUS P7P55D-E LX mobo, 8GB DDR2, a core i5 quad-core, and 6 WD "green" 2TB drives (I'm more concerned with capacity than speed).

I got it all assembled, using a 500GB 2.5" drive as the boot / host drive, a blu-ray reader, and splitting the 2TB drives amongst the 2 controllers (4 on the remaining ports of the x6 SATA controller and 2 on the x2 SATA-III controller, just not needing the SATA III capabilities).  I plan to use Software RAID5 rather than the fakeraid that might be supported by the chipset.  This affords maximum portability for the future.

At any rate, I installed 10.10 64-bit (Desktop), let it update, then installed mdadm and set about configuring the RAID5.  I decided to use the nifty graphical tool.  Last time I did this on my old Fedora box, it was all CLI.

All seemed to be going well, and I was letting it fully recover / synchronize before setting up a filesystem (planning on ext4 this time).  I kept an eye on it with cat /proc/mdstat.

After 20 hrs (averaging 25MB/sec on the sync...seems a bit slow, but who knows?)...it finishes and the RAID is immediately degraded with one volume (/dev/sdc1) marked as faulty and another volume marked as a spare.  I replaced the SATA cables with brand new ones as long ago I ran into an issue like this due to a bad cable.  Before trying again I ran the extensive SMART test and a read/write benchmark on each drive.  They all checked out fine.  So I started over and 20hrs later, same thing.

So I shut down and removed the offending drive and started with only 5 drives.  Another 19hrs go by and this one turns up /dev/sde1 faulty and another drive marked as a spare.  That drive was fine before, and is on a different controller from the one that it was finding as faulty before.

Now I am suspicious that there is a larger underlying issue and that the drives are not bad at all.

Should I have just gone with a 32-bit + PAE install?  Does the 64-bit have known issues with the software RAID?

Should I have just built it using the CLI?  Looking online, it seems people are having success with the GUI tool.  I don't think it is the GUI tool.  Checking with mdadm, it seems everything is being configured right.

Any ideas?

Thanks!

---

### Post by 555Ron on 2011-01-01
I think you will find the issue is the WD drives. I am also having problems with them. One issue is partitioning them correctly due to the 4kB sector size (Search advanced format) and the other is the heads parking all the time (being a 'green' drive'). Search Widdle3 to solve that problem. I've not had any luck yet getting them to work in a software RAID yet though...

---

### Post by jedigrover on 2011-01-01
Thanks for the info.  Looks like I'll have to be returning all 6 drives to newegg with that dastardly 15% restock fee.

Seems to me that if manufacturers are going to muck up their drives to not work with RAID, then they should be required to put that in 36-point font on ANY sell-sheet / spec-sheet.

Selling an *expensive* "RAID edition" of drives violates the "I" in RAID (inexpensive).

I swore off WD drives long ago, but came back this time due to firmware concerns on some Samsung drives (my previous server used all Samsungs with good luck) and due to price / power concerns.

Looks like I'll be permanently deleting WD from consideration for the future.

D

---

