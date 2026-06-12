---
title: "Using old HDD are storage"
date: 2010-03-24
forum: General Help
---

### Post by mullinsn2000 on 2010-03-24
I had a Dell system that was fairly old and the video card went out.  I did not want to waste money on replacing a video card, so I opted to just build a new system.  The old HDD was SATA 250GB and has XP installed with many files I would like to get off of it.  The new system will have a 1.5TB SATA HDD and I will be dual booting Windows 7 and Ubuntu.  Here is my question:

Should I install both drives, put Windows 7 on new drive and then get into old HDD and retrieve files and then format it?  OR   Should I install both drives, set up the dual boot, then retrieve files from old drive then format it?

I am not sure if GRUB will detect the XP install and then have a tri-boot.  I have no interest in having XB bootable.  I just want to get some files off of it and then clear the HDD.

---

### Post by lindsay7 on 2010-03-24
If the files you want are just data files, you can install 7 to the new drive and then plug in the old dive and copy them down to your new one. It the files you are talking about are programs that is a different story. You could as you may not be able to transfer them over from xp to 7 as such.  I think if you install 7 and still have the xp os on the old drive and then install Ubuntu the boot loader or mbr or other system files will be seen by grub and it will want to account for them. If you just want to get the data files of the old drive I would disconnect it and install the new drive and install 7, then reconnect the old drive and copy the files that you want, then format the old drive and install Ubuntu.

---

### Post by mullinsn2000 on 2010-03-24
> **lindsay7 said:**
> If the files you want are just data files, you can install 7 to the new drive and then plug in the old dive and copy them down to your new one. It the files you are talking about are programs that is a different story. You could as you may not be able to transfer them over from xp to 7 as such.  I think if you install 7 and still have the xp os on the old drive and then install Ubuntu the boot loader or mbr or other system files will be seen by grub and it will want to account for them. If you just want to get the data files of the old drive I would disconnect it and install the new drive and install 7, then reconnect the old drive and copy the files that you want, then format the old drive and install Ubuntu.
I could care less about any programs on the old drive.  The files I want are mp3 and video files.  I will probably just put both drives in, install 7 to the new HDD, transfer files over and then format the old HDD.  After doing that I will then adjust partitions using 7 and then install Ubuntu.  I am anxiously waiting for the parts to arrive today.  I would like to get it put together before I have to go to class, lol.

---

### Post by mullinsn2000 on 2010-03-24
OR
Maybe I will just get an external enclosure and use the old HDD (once formatted) as a second USB backup HDD.

---

### Post by Jerry N on 2010-03-24
Just to keep from confusing things, I would leave the old drive disconnected while installing the dual boot on the new drive.  Then install the old drive and do what you want with it.  

Jerry

---

### Post by lindsay7 on 2010-03-24
Jerry is correct and that is what I was suggesting. If you leave the old hard drive in and install 7 it will see the old windows and want to do something with it. Just disconnect it until you have the new drive and 7 installed that way your mbr is going to be set on the new drive and when you get it going just reconnect the old drive and get your file off of it.  Then you can do what you want with the old drive.

---

### Post by mullinsn2000 on 2010-03-24
I understand.  The last computer I built was using IDE HDD's.  I forgot that SATA drives do not have jumpers to set in order to dictate which HDD to boot from.  I will install Win 7 on new HDD with old one disconnected and then put it in and clear it out, then I will set up the dual boot as to not mess up the MBR or GRUB.  It has been to long since I built a new system, lol.

---

### Post by lindsay7 on 2010-03-24
Good, let me know if you have problems.  I just built a new system this month and dual booted it with 7 and 9.10, so it is all fresh in my mind.

---

