---
title: "Clonezilla - Backup Grub?"
date: 2009-12-14
forum: General Help
---

### Post by Quarkrad on 2009-12-14
Can clonezilla backup grub so when you load a saved system image back to your HD you can also reload a working grub?  Just loaded a saved image back to sda1 and grub just sits there GRUB>    No matter what I do I've lost my system.  Would have been easier if I could have loaded the grub image as well.

---

### Post by howefield on 2009-12-14
If you image the disk, grub will be backed up.

If you have only imaged the partition(s) then I guess not.

---

### Post by RonCam on 2010-02-17
Was this ever resolved?  > **Quarkrad said:**
> ... grub just sits there [at] GRUB>    I have the *identical *problem and have tried "Beginners" mode in Clonezilla for both partition and disc imaging.  

> **howefield said:**
> If you image the disk, grub will be backed up.

I suspect the problem is not with the "backing up" but with the restoring. Is it true that GRUB is not on the partition itself?  If so, I'd by happy to just leave the original GRUB in place, if possible.  

This is with an ASUS L7014G and Leeenux Ubuntu for netbooks.

I am now looking at the Expert mode options in Clonezilla, but have not found the right combination.  Has anyone had success here??

---

### Post by RonCam on 2010-02-27
Possibly helpful information:

Problem solved, perfect image and restoration with Ext4, using fsarchiver on SystemRescueCD.  Grub works on first reboot, after restoration.  Never could figure out why Clonezilla works for so many, but failed on my system.

---

### Post by strobe on 2010-02-27
After struggling with SystemRescueCD and attempting to figure out were to even use the FSArchiver program (I'm very new to linux and used to GUI program windows to click and select) I finally gave up.  Found Clonezilla and it was nearly as simple as the DriveImage XML I was using originally for Windows.  Actually, the Clonezilla Live CD was easier because I didn't have to build a BartPE disk with pluggins added (although, I was able to add my Raid drivers with BartPE).  I created an image of my Karmic partition and saved it onto a usb drive.  I was able to restore without an issue.  Then created another and saved it on my shared NTFS partition.  Tested the restore, and, it too restored without a hitch.  I now have an image of a working Karmic OS with my wifi, compiz, emerald, hibernate/standby all functioning (which took me about a week and a half to get it all done).  
 
I only had to create the "savepart" (i think thats the option) and selected my Ubuntu partition. Compression was about 1/2-2/3 the original size.  I used the advanced mode (not beginners) just to confirm the partition I was imaging and where it was being saved.  The rest I basically kept default.  I haven't tested if I adjust the partition size and attempt a restore or anything else.  Only to see if the image I created would restore on the exact partition I created from.  Maybe there are more variables affecting the outcome.

---

