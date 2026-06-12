---
title: "CDROM won' work with ubuntu live disks"
date: 2012-07-04
forum: General Help
---

### Post by dgundling on 2012-07-04
I am trying to build up a computer to install various versions of ubuntu and other linux distros. Using an old WIN98SE boot disk I can load any version of windows easily. None of my 6 linux based live disks will boot from the same CDROM drive. On my other WINXP computer, any of the 6 live disks will boot easily. Does anyone have a cure for this? I have tried two CDROM drives with the same result. I have tried changing the boot order to all the combinations of HD, floppy drive, and CDROM drive that I can think of without success. I did manage to get Ubuntu 10.10 installed by first installing WINXP home and then, while in WIN XP inserting the live disk. The cdrom drive will not run a live disk when Ubuntu 10.10 is running.
 
Also I wonder why the Disk tool under admin in Ubuntu 10.10 shows the CDROM drive as a SCSI drive not as an IDE drive.
 
Thanks for any ideas.

---

### Post by GreatDanton on 2012-07-05
First thing I would recommend you is to make live Usb. However before you do that, check if your system is available for booting from USB (since you mentioned Windows 98-so I assume it's a bit old machine)

Live Usb can be easily done with this tool:[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

You just need Iso file and Unetbootin will take care of everything else.

P.S- Ubuntu 10.10 will be out of support very soon (or it's already?), so I would recommend you to install either Xubuntu or Lubuntu (that depends on your computer configuration). Could you please post your computer hardware?

Thanks.
I hope you will be able to follow this :)

---

### Post by mastablasta on 2012-07-05
did you check that the image you downloaded is good (Md5sum check)?
Did you check that the image burned good?
did you check to make sure your CD drive accept the kinds of cd's you are sticking into it?
did you burn the CD at slowest speed possible?
 
aside from unetbootin for USB linuxliveusb has a nice interface as well. works only in windows though.

---

### Post by dgundling on 2012-07-06
Great Danton,
 
Thanks for the reply. I haven't attempted to go the USB route as yet. I am trying to understand why the CDROM route won't work. Why can the CDROM read and boot windows disks and not do the same for LINUX based disks? Is there, perhaps, a newer CDROM driver out that I am unaware of? My WIN98SE boot disk has a CDROM driver dated 1996- 1997.

---

### Post by dgundling on 2012-07-06
Mastblasta,
 
Thanks for the reply. The answers to all but one of your questions is yes. I didn't check the Md5sum because two of the disks I am trying  to use are commercial Ubuntu distros and also because the versions I burned all work with my WIN XP based computers.

---

