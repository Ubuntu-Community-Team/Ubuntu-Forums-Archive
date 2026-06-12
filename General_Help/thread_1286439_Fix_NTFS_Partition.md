---
title: "Fix NTFS Partition"
date: 2009-10-09
forum: General Help
---

### Post by Big Luke on 2009-10-09
Hi all, now before you ask, i looked on the internet, googled for a long while, but i seem to have a somewhat unique problem.  I have 2 HDDs, a 80GB and a 500GB.  The 500GB has a 100GB NTFS partition with the Windows 7 RC on it(for games...windows only use IMO lol), a 15 GB partition for trying new OSs and finally a 350 GB partition for storage.  As i was sifting thru the 350 GB partition, organizing files, throwing out ones i dont need etc. i cam across some odd files and folders...i know i know, i shouldnt have touched them but...im sort of sleep deprived for the past week and i wasnt thinking straight so i deleted them.  All i know was that one folder was labled System Volume Information and there was a .dll and those are the only ones i can be sure of.  I didnt remember putting them on there so i just deleted them.  When i booted to Win7, tried to navigate to D:  which is the 350GB partition, it said that "D:/ is not accessible the file or directory is corrupted or unreadable".  Win7 doesnt recognize anything about the disk.  Since then ive tried ```
chkdsk D: /f
``` and ```
chkdsk D: /r
``` and simply ```
chkdsk D:
``` i then went on to try [TestDisk]("http://www.cgsecurity.org/wiki/TestDisk") and as far as all of them are concerned, there are no corrupt files...i believe i am just missing some files...any help would be very much appreciated.

O and reformatting is NOT an option for this disk.  o and Ubuntu can still navigate the partition.

---

### Post by dcstar on 2009-10-09
> **Big Luke said:**
> Hi all, now before you ask, i looked on the internet, googled for a long while, but i seem to have a somewhat unique problem.  I have 2 HDDs, a 80GB and a 500GB.  The 500GB has a 100GB NTFS partition with the Windows 7 RC on it(for games...windows only use IMO lol), a 15 GB partition for trying new OSs and finally a 350 GB partition for storage.  As i was sifting thru the 350 GB partition, organizing files, throwing out ones i dont need etc. i cam across some odd files and folders...i know i know, i shouldnt have touched them but...im sort of sleep deprived for the past week and i wasnt thinking straight so i deleted them.  **All i know was that one folder was labled System Volume Information and there was a .dll and those are the only ones i can be sure of.  I didnt remember putting them on there so i just deleted them**.  When i booted to Win7, tried to navigate to D:  which is the 350GB partition, it said that "D:/ is not accessible the file or directory is corrupted or unreadable".  Win7 doesnt recognize anything about the disk.  
........
 i then went on to try [TestDisk]("http://www.cgsecurity.org/wiki/TestDisk") and as far as all of them are concerned, there are no corrupt files...i believe i am just missing some files...any help would be very much appreciated.

O and reformatting is NOT an option for this disk.  o and Ubuntu can still navigate the partition.

How about you ask in a **Windows forum** how to repair your **Windows system**?

---

### Post by Big Luke on 2009-10-09
> **dcstar said:**
> How about you ask in a **Windows forum** how to repair your **Windows system**?

But I do not have Windows installed on the problematic partition, the files that i am assuming are causing the problems were deleted on Ubuntu, yet i cannot find them in the trash so i am wondering if they can be recoverd on Ubuntu.

---

### Post by CharlesA on 2009-10-09
> **Big Luke said:**
> But I do not have Windows installed on the problematic partition, the files that i am assuming are causing the problems were deleted on Ubuntu, yet i cannot find them in the trash so i am wondering if they can be recoverd on Ubuntu.

Copy the files from that partition to another drive and reformat the drive. If that doesn't work, you need to reinstall W7.

---

### Post by Big Luke on 2009-10-09
> **CharlesA said:**
> Copy the files from that partition to another drive and reformat the drive. If that doesn't work, you need to reinstall W7.

I would have done that except i do not have any more HDDs.  However I did create a new NTFS partition using empty space from the existing partition and i have been transferring files to the new partition, increasing its size and then decreasing the old ones size...rinse and repeat.

---

