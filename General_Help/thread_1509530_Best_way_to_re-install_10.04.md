---
title: "Best way to re-install 10.04?"
date: 2010-06-14
forum: General Help
---

### Post by LotsToLearn on 2010-06-14
A few weeks ago I upgraded to 10.04. A couple days later Ubuntu said my 80GB hard drive was full and then wouldn't let me start Ubuntu.
I found some online help and got in and deleted some files including some log files, that now I seem to need.
What's the best way to re-install (or repair?) 10.04 in such a way that my user files won't be overwritten?
Thanks in advance for your help,
 -John

---

### Post by bodhi.zazen on 2010-06-14
Unless you have a separate /home or /data partition you will need to back up your data and re-install.

If you re-install you should make a separate /home or /data partition.

Without knowing what you deleted it is hard to know if you can fix your situation short of a fresh install.

A fresh install takes 20 minutes , how long do you think it will take you to fix your problem.

And what was filling your hard drive ? 80 GB is HUGE for logs ...

---

### Post by LotsToLearn on 2010-06-14
What was filling the hard drive?  Excellent Question. I never got to the bottom of it. I had some old files that I didn't need any more and I found some log files to delete (didn't write down which ones); that bought me enough room to get going again. But then it happened again last Friday, but then this morning, without deleting anything, it started fine and Disk Analyzer said I had 38GB free.  I haven't deleted anything since Friday. Very odd!

I have copied everything from my home folder on to my external drive. So I have the files that were on my desktop, in my documents folder and in my email.  That's really all I care about.

---

### Post by sidzen on 2010-06-14
I would bet that NTFS was present somewhere on the HD in question before the upgrade.  ?

---

### Post by LotsToLearn on 2010-06-14
When I first switched from Windows XP to Ubuntu about 1.5 years ago, I first tried to partition the hard drive and keep Windows on part of it. An error occurred and, if I remember correctly, I just had the whole hard drive converted to Ubuntu. Maybe something was lingering from that process.?

---

### Post by gcvisel on 2010-06-14
I guess I'd like to hear the answer to the original question.  
 
My installation takes a long time to load (more than a minute from BIOS screen to visible desktop) and I'm thinking of doing the same.  Right now, my OS and Home are all in one partition, and I do back up the Home folder to an external HD.  I've arrived here by upgrades all the way back to 6.04, but wanted to do a clean install on my 160G HD.
 
I assume I want to make three partitions, a small one for the OS and a small swap file, plus the remainder of my disk for the Home folder?  Got recommended sizes?  
 
I have 4 Gig of memory, and assume I want the 64-bit version to take advantage of that.  EXT4 file systems?
 
Or is this all in a FAQ somewhere?
 
Thanks,
Spook

---

### Post by philinux on 2010-06-14
10.04 boots to usable desktop in 16 seconds.

/ anything from 8 to 12 gig

/swap if you have say 2 gig memory then swap should be 2 gig for suspend/hibernate etc.

/home the rest

---

### Post by hhoyt on 2010-06-14
I use 10.04 w/ ext4 and there IS a noticeable boot speed increase. My boot is just over 30sec. & the Phoronix benchmarks seem to substantiate.
Some folks say you should be on an UnInterruptible Power Supply (I am) to use it tho.
Actually if you look at prices on UPS vs the pain of a power surge, it is not a bad investment.

If you want to experiment, fsarchiver will let you backup ext3 and restore ext4. It is quite fast. the backup is something like
sudo fsarchiver -v savefs /media/MYDRV/SDA1.FSA /dev/sda1
where your drive is on sda1. You must mount r/w your dest and ensure your source is NOT mounted.

to convert to ext4, just restore with mkfs parm, something like
sudo fsarchiver -v restfs /media/MYDRV/SDA1.FSA id=0,dest=/dev/sda1,mkfs=ext4

You do not need to format your drive using this approach - tho perhaps you want to for swap.

 I have both gone back to ext3 and forward again to ext4 this way.

Cheers, Howard

---

### Post by sidzen on 2010-06-15
I would suggest (lots seem not to want to either hear or do this, for some reason I cannot fathom) downloading SystemRescueCD 1.3.4 from sourceforge, burning it to CD, reboot your computer with it in the cdrom drive, type <dban> at the first prompt at the bottom of the screen, the next screen will be light blue and, at it, type <autonuke>.  this will wipe the entire HDD with zeros, so there is NO trace of Windoze or RAID or any other Redmond-related BS on your drive.  THEN reboot and partition with the same sysrescd but hit F2 at the first prompt, then follow directions until after it loads, at which time one types <startx> then at the yellow terminal, <gparted>.

Best wishes.  Do this if you want -- its the quickest, simplest way to get a CLEAN install of any form of Linux, in my experience.

---

