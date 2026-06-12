---
title: "Cannot see/mount other internal HDD in 9.10"
date: 2009-11-30
forum: General Help
---

### Post by Cobracommand0 on 2009-11-30
Not sure where the correct place to post this would be, did some searching to see if there was already a command to fix this and didn't have much luck.

I have three sata drives on my box, two 80gb drives and a 160gb.  One of the 80gb HDD holds Ubuntu while the other two exist as storage drives.  When I did my clean install to 9.10 I was unable to see my other two drives with all my data (only had the single 80gb hooked up during the install); I've checked with gparted and fdisk -l but the only drive that I am able to see is my 80gb OS HDD.  Any thoughts on how to get 9.10 to recognise my other two drives and mount them?  Any links to other threads or mount commands would be most appreciated, I've hit a wall as far as fixing this issue.  

Cheers!

---

### Post by Cobracommand0 on 2009-11-30
After-work bump!

---

### Post by Johnny19734 on 2009-11-30
Go to Software Sources in the Administration menu. Add the proposed software updates. Then run update manager and install the updates. There was an issue with libusb and Karmic that was resolved with an update.  Also, what type of filing system are these two drives? NTFS/FAT/FAT32 etc?

---

### Post by Cobracommand0 on 2009-11-30
I believe they are NTFS drives, but I'm not 100% certain.  I ran through your suggestions, Johnny, but it did not fix the issue.  However, I think I discovered a new problem that is completely different from the original issue.  I realised that my 3rd and 4th SATA drives were turned off in my bios, upon enabling them my system CRAWLED through the post  and bios, asked for a grub choice (the menu with the grub, grub recovery, memtest, and something else) before finally failing to find the root (I think) and not loading the operating system..  I think I am having an issue similar to this thread:

[http://ubuntuforums.org/showthread.php?t=1340530](http://ubuntuforums.org/showthread.php?t=1340530)

But I followed those steps without a solution... As long as I have the two extra SATA's turned off, the system boots fine (except that I have lost my SATA DVD drive after turning the extras on).  I'm assuming that the issue is with running more than 2 SATA drives..

---

### Post by Johnny19734 on 2009-12-01
Turn the drives on in the BIOS and then boot in recovery mode. At this point it could get tricky. You will need to reload the grub. BEFORE you do this I back everything up.   Since the files are already install on you UBBY drive you should be able to reinstall straight from command...I don't want to give you detail instructions. There are tons of guides on here on how to reload you grub. But BACK UP BACK IT :P

---

