---
title: "Recovery"
date: 2012-08-23
forum: General Help
---

### Post by Pian0maN on 2012-08-23
Hello all,  

I will start with the problem...  

A few days ago my laptop (windows 7) my laptop rebooted by itself but it didn't get any further then a black screen with a white mouse pointer that i could move around. It seems to stay on that screen forever (I left it on for one night, same). I cannot do anything, alt, ctrl, del doesn't work, clicking anywhere doesn't do anything. It was scheduled to do updates at the moment of the crash but i don't think that has anything to do with it, because it wasn't  scheduled to reboot when it went into black-screen-white-pointer for the first time (I had clicked 'delay reboot for 4 hours' less then 4 hours before the 'crash')  

Solutions I came up with: 
Of course I tried rebooting with the Windows CD, but somehow this doesn't work. It gets stuck in the black&white screen of death (from now on referred to as W&HSOD...) before I get any kind of menu. I tried the CD on another computer, on whitch it did work. Yes, I changed the BIOS settings into boot from CD/DVD. I downloaded RC.iso and put it on a disk to boot from: this gave me some options but when it then continues to boot, gives me a blue screen of death. I tried the bootup CD from LiveBoot from Wondershare, this gives me a menu with the options 'boot from CD' and 'boot from HDD' and both give me the B&WSOD. I then stumbled upon Knoppix, put it on a DVD and finally, something worked. It doesn't seem to have any problems. I then checked the HDD in 'Disk Utilities' and it appears to have 5 bad sectors. My HDD is partitioned into 4 ehm, parts? whitch are  
1. BIOS_RVY 
2. System 3. 
OS_Install 
4. Data 
All are NTFS.
 All the bad sectors are in part 3. This part I cannot mount using Knoppix. The 4th part seems to be fine, I can mount it and access and copy my files. Now, had I done regular backups, I would write zeros to the whole freakin' disk (something I eagerly look forward to, muhahaha), reinstall windows and pray that my HDD works fine from there on. But of course I didn't and I have some files that I would really like to have back, so I need to find a way into that 3rd part. I have tried testdisk and found out that a lot of my files are still there, but I still couldn't access my former 'documents and settings' folder. It just didn't find any files or folders there. I also ran PhotoRec, whitch I used to copy everything from partition 3 to an external harddisk, but some files still seem to be missing (or at least unrecognizable) and everything is a complete mess because file names are lost and folder structure too. I then started looking for other programs that could be of any help and came across RStudio for Linux. It also could scan OS_install, but didn't see any folders in Documents and Settings. Furthermore, because it is a demo version, I could not make an image of the partition so I can bomb the HDD with zeros without worries, start using my computer again and try to recover my files using windows, making stuff a lot easier (for me).  

So here are my questions: 
- Is there any other (free) program that can create an image of OS_Install? 
- If PhotoRec couldn't find my files (in origional shape), are they too corrupted to be recovered? But if only 5 sectors are bad, how can my total 'Documents and Settings' folder be invisible for both TestDisk and RStudio? 
- How is it possible that it just refuses to boot anything but knoppix from CD? Could it be that a boot from CD is not actually not a complete boot from cd but it gathers some information from the HDD, and that in my case exactly this information is somehow corrupted?
- Does it even make sense to zero my HDD in the hope this solves my problem and lets me boot windows from DVDs again? 
- Any other suggestions?  

I'm sorry to bother you with so much info and questions, I hope it all makes a bit of sense to you guys... Any help will be very much appreciated!

---

### Post by Pian0maN on 2012-08-23
Ah, and if this is the wrong section to post this kind of stuff, please forgive- and tell me, where to put it...

---

