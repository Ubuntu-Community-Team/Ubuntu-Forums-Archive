---
title: "Linking removable media to gnome desktop"
date: 2006-05-07
forum: General Help
---

### Post by skippy81 on 2006-05-07
Hi, I installed a the latest stable kernel from kernel.org in order to get my m/bs chipset working at full speed DMA.  My ubuntu is now as fast as windows XP :p .

Unfortunately it was not completely without problems.  I was getting tons of 
> device-mapper: dm-linear: Device lookup failed errors on startup, and my removable disks did not seem to be mounting properly.  My response was to uninstall the EVMS packages, and remove the evms related stuff from my runlevel scripts.  This has killed all the error messages showing up, and my removable media is all accessable from the /media/ folder.  

However, if possible I would like to be able to access it quickly from within gnome.  Is there anyway I can return my disc icons to the desktop again by editing a file?  They dont show up under the places menu either.  Strangely enough my FAT32 windows partition is unaffected, it seems only to be removable media which has been removed from gnome's desktop.  

Thanks

---

### Post by Scunizi on 2006-05-08
I put these three lines in fstab.

/dev/sdc1 /media/usb1 vfat rw,user,fmask=0111,dmask=0000 0 0
/dev/sdd1 /media/usb2 vfat rw,user,fmask=0111,dmask=0000 0 0
/dev/sde1 /media/usb3 vfat rw,user,fmask=0111,dmask=0000 0 0

Then I did a mkdir in /media for usb1, usb2 & usb3.  I occationally have 3 different usb memory sticks plugged in.  Actually one of them is a mp3 player.  After I did all that and rebooted I had screen icons and a listing in the places menu.  I hope that helps!

---

### Post by skippy81 on 2006-05-08
Thankyou mate, Ill give that a try :)

---

