---
title: "Unexplained 400GB on my hard drive!"
date: 2011-08-23
forum: General Help
---

### Post by chrisp3047 on 2011-08-23
Hi there,

I ran disk usage analyser on Ubunutu 11.04, and it told me that I have used 838GB and have available 69GB.

But when I click 'scan filesystem' it says the size of the entire filesystem is 404GB. This accounts for all my 'known' data on the drive.

Could someone explain how I can find out what is using up the rest of my hard drive?

There is over 400gb that I don't understand what it is! I've looked at the recycle bin and cache, and these are small amounts. I'm starting to get worried that it's a virus??? Or a problem with my hard-drive?
 
Thanks to anyone who can help.
 
Chris

---

### Post by mcduck on 2011-08-23
And what size is your hard drive? Could you run "df -h" in a terminal and paste the output here?

Anyway, you should keep in mind that the disc usage analyzer is not a tool for checking how much of a certain disc/partition is used and how much is available. Instead, it's intended for analyzing how much space files and directories are using, and where most of the space is used. So it doesn't, by default, scan a single hard drive or a partition, but the whole filesystem instead, counting the space from all mounted drives. (in addition it does have a known bug with counting the space of virtual file systems twice, which you might see if you are using disc encryption, mounted network locations etc.)

(you *can* use the disc usage analyzer to check the used/available space of a certain partition, but to do that you'll have to specifically tell DUA to only scan a certain partition and to ignore everything else. There are many far better suited tools for that purpose, like the "df" command or even the System monitor)

---

### Post by Josep CA on 2011-08-23
Can you run GParted an pots the results? Maybe you have a hidden disk partition but not sure...

---

### Post by Wayne_V on 2011-08-23
There is a difference between filesystem and physical device.  Try the following commands:

sudo fdisk -l /dev/sda
df -ah
cd /home ; sudo du -sk *    .* | sort -n    (that's * space .*, not *.*)

---

### Post by howefield on 2011-08-23
Thread closed.

Duplicate here : [http://ubuntuforums.org/showthread.php?t=1827006&page=2](http://ubuntuforums.org/showthread.php?t=1827006&page=2)

---

