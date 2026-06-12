---
title: "Reformatting Internal Hardrive"
date: 2012-09-15
forum: General Help
---

### Post by northwestern on 2012-09-15
I have ran Ubuntu for the last two years from an external hard drive (alongside Windows 7 on the internal drive). A few weeks ago I shrunk my internal hard drive by 25gb and loaded Ubuntu 12.04 onto the drive.
Ubuntu is running fine but Windows 7 sometimes crashes for no reason , therefore I want to revert back to running Ubuntu on an external drive. My questions are.
1/ Do I just reformat the shrunk section being used for Ubuntu.
2/ How do I add the shrunken section back into my Windows 7 C drive.
3/ How do I remove the Ubuntu boot/grub screen from my Windows C drive.

Regards
Northwestern

---

### Post by jayboe on 2012-09-15
> **northwestern said:**
> I have ran Ubuntu for the last two years from an external hard drive (alongside Windows 7 on the internal drive). A few weeks ago I shrunk my internal hard drive by 25gb and loaded Ubuntu 12.04 onto the drive.
Ubuntu is running fine but Windows 7 sometimes crashes for no reason , therefore I want to revert back to running Ubuntu on an external drive. My questions are.
1/ Do I just reformat the shrunk section being used for Ubuntu.
2/ How do I add the shrunken section back into my Windows 7 C drive.
3/ How do I remove the Ubuntu boot/grub screen from my Windows C drive.

Regards
Northwestern

 It's been a couple of years since I messed with anything from Microsoft, but if I remember right....

  1. Reformatting it is up to you if you plan on regaining your original drive space
  2.  Hit your windows button (start button) and type computer configuration or right click on your start button and go to your properties to set you menu to show administartion tools so you can navigate to it from the start button the system tools... ? or something to that nature and then you will have the option to grow your windows drive back.... it;s been a while and I never messed with windows too much
   3. As far as removing the grub go and download easybcd and about two or three clicks and your MBR will be restored to normal.

 Hope it helps :)

---

### Post by Mark Phelps on 2012-09-16
> **northwestern said:**
> I have ran Ubuntu for the last two years from an external hard drive (alongside Windows 7 on the internal drive). A few weeks ago I shrunk my internal hard drive by 25gb and loaded Ubuntu 12.04 onto the drive.
Ubuntu is running fine but Windows 7 sometimes crashes for no reason , therefore I want to revert back to running Ubuntu on an external drive. My questions are.
NOTE -- all the advice below PRESUMES that you have Ubuntu installed in its own partition, NOT a Wubi install inside of a Windows partition ...
> 
1/ Do I just reformat the shrunk section being used for Ubuntu.
Boot into Win7.  Use the Disk Management utility to remove the Ubuntu partition.
Use the Backup feature to create and burn a Win7 Repair CD -- you will need this to restore the MBR.
> 2/ How do I add the shrunken section back into my Windows 7 C drive.
Use the Disk Management feature in Win7 to expand the Win7 partition.  May require a reboot to do this.
> 3/ How do I remove the Ubuntu boot/grub screen from my Windows C drive.
Boot from the Win7 Repair CD, run Startup Repair.  May have to run this three times, as tends to repair the MBR on the third pass.

---

