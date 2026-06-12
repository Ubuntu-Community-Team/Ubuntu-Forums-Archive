---
title: "CD-ROM Not Detected"
date: 2010-10-23
forum: General Help
---

### Post by LordVeovis on 2010-10-23
My SATA CD-ROM is not being recognized by Ubuntu.  I was not able to install from CD either, thankfully I have flash drives and other ways to install, but I need CD-ROM to work.

---

### Post by Jebtrix on 2010-10-23
See if your BIOS gives you an option to toggle AHCI mode for sata. This causes problems with M$ Windows too sometimes.

---

### Post by LordVeovis on 2010-10-24
I guess I should have given more info.  

I currently have an ASUS P5K Delux mobo, so there are MANY options.  I have been through most with no success.

I have just set it as you suggested; on my mobo by:
 Main Menu -->
   SATA config -->
      Intel Robson Technology (disabled or enabled)
       -Configure SATA as    AHCI

Still nothing.  Other options related to the SATA include for it to be configured as IDE or RAID (we can skip RAID).  When set as IDE, the IRT option above it changes to 'SATA Configuration' and has the following options:  Compatible, Disabled, Enhanced
When in either Compatible or Enhanced mode I am not able to detect the CD ROM either.

When it is set to AHCI, there is a new option on Main Menu for AHCI Configuration.  If I go to that option, it is pretty standard, shows the different AHCI Ports and what is currently detected there (CD ROM is there).

Any help, much appreciated.

EDIT:  Also it can partially boot an install CD, I can get to the boot selection menu on the disk but not much farther.

---

### Post by LordVeovis on 2010-10-26
Still hoping for help.  Anyone?

---

### Post by searchfgold6789 on 2010-10-26
Ubuntu cannot boot from the live cd, usually because it lacks drivers on the CD for your CD drive.
After it is installed, it probably still lacks drivers.
So try looking online for drivers for your CD-ROM.

---

### Post by ronparent on 2010-10-26
> Ubuntu cannot boot from the live cd, usually because it lacks drivers on the CD for your CD drive.
I don't believe this comment is valid. The problem is with the bios on your MB.

I have a similar problem with a blu-ray sata drive I've just installed. It wont boot but it is otherwise usable in Ubuntu 10.10. Is it possible that you have the same situation?

---

### Post by Automat2 on 2010-10-26
I had a similar problem with my DVD-RW. I changed the SATA cable, but in the end, I had to buy a new drive.

At the beginning, the old drive gave me errors on burning DVD's, later, did not recognize any disc I put in the drive, except if I pressed the cable connection against the drive in a very awkward position.

So far, the new one is working fine.

---

### Post by NewDisciple on 2010-10-26
I have had this problem several times and it has always been my sata cables. The cables may look okay but if the ends are not sitting just so-so they won't work. All it takes is a little bounce or even the slight vibration from normal operation to cause a problem.

---

