---
title: "Update killed my drive! Please help!"
date: 2010-09-30
forum: General Help
---

### Post by null86 on 2010-09-30
Okay so here's what happened. I'm sitting here watching YouTube, when I get the update box. I  hit install updates ( which includes a kernel update) and after it is through, restart my computer. I have 3 drives on my computer. A 160gb(linux ext4 and a ntfs split 50/50), a 320gb(also ext4), and a 1.5tb(ntfs). After everything reboots and I come back to the desktop, my 1.5tb drive is gone. I have gone into windows which reads it as a raw drive and prompts me to format it. In Ubuntu, the Disk Utility sees the drive, smart is healthy all fine except under usage It is blank, and type is blank. It still sees it as a htfs/ntfs partition but will not mount it. I've tried everything i could find including using ntfsfix. I just got another drive to backup everything in the mail and then this happens. Please any suggestions. I have very important stuff on here so i'll try anything before the big "F".

---

### Post by Mark Phelps on 2010-09-30
First of all, if you encounter NTFS problems, you should not jump into using ntfsfix.  That can only fix minor problems.  You need an MS Windows machine to repair the NTFS partitions properly.

I would worry most about the 1.5TB drive -- that's a LOT of stuff to lose!

Since you're willing to try anything, I strongly suggest the following:
1) Unplug the 1.5TB drive NOW
2) Plug the drive into an MS Windows machine (preferrably running Win7) and see if the drive is recognized along with the partition(s) on it. If you don't get a drive letter, look in the Computer Management console under Disk Management, scroll down through the list of "drives" (actually, they are partitions, not drives) and see if the drive is listed as Offline.

If it is, try changing that to Online.  If it works, it will assign a drive Letter.

If that works, open the drive in Win7 and see if the files are OK.

If NONE of this works, there's a chance the partition(s) got trashed.  To see what's salvageable, do the following:
1) Go to the Runtime Software site and download the free version of GetDataBack for NTFS.  It's the best data recovery software out there.  
2) Install that on the MS Windows machine.  Open it and run it against the 1.5TB drive.  Let it run overnight as it takes a LONG time to scan large drives.  
3) Look at it the next day to see what files it found and the chances of recovering them.  If it found them and the chances are good, you will have to then decide if your files are worth the price of the SW.  

OK, now others here will tell you to hack around with Testdisk and Photorec, and while those MIGHT work (they never worked for ME on NTFS partitions), realize that every time you write to this drive, you are worsening the change of recovering ANYTHING.

So, you can mess around for free ... or you can spend money and buy something that is known to work.  

Your files ... your money.

---

### Post by null86 on 2010-10-01
Thanks for the advice! I looked in to that testdisk program since it is for Linux and gave it a shot. Fixed my partition table in 5 minutes. It seems that the last kernel update just erased my partition info on /dev/sdb1, so it couldn't read it properly. Now all my stuff is back and i am super happy! Thanks for the help!

---

