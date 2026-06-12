---
title: "Can't mount cdrom or usb after replacing optical drive"
date: 2010-03-24
forum: General Help
---

### Post by Luxx on 2010-03-24
My cdrom was sort of working, but the tray was physically damaged. The usb was working without a problem. 

After replacing the the cdrom drive with a similar model known to work well I could not get it to mount. I then tried to move important files to usb to try a fresh install. The usb stick flickered when I put it in, but it didn't mount. Same behaviour as the cdrom, the light goes on when I turn on the computer, but once I'm logged in I can't access the cdrom.

I have tried multiple variations of playing with fstab and trying to mount things in terminal to no avail. I just can't get Ubuntu to recognize the usb or cdrom even though their lights go on when I first try to use them.

I would greatly appreciate any advice that could lead me in the right direction.

---

### Post by Luxx on 2010-03-24
I got the usb working by following advice on this thread: [http://ubuntuforums.org/showthread.php?t=1416667&highlight=automount+policy](http://ubuntuforums.org/showthread.php?t=1416667&highlight=automount+policy)

This was a simple and effective fix for the usb, just changing policy behavior. Can the cdrom be that simple?

My cdrom is still not showing up once logged in. I can boot from the cdrom, so I know it works, I just can't access it once I am logged in.

---

### Post by desnaike on 2010-03-24
Well make sure drive is configured properly as master,slave,cs. And determine weather you have 80 wire/40 wire cables and last but not least did you read the drive manual.

---

### Post by Luxx on 2010-03-27
Optical drives have manuals? I have been replacing/upgrading computer parts for 12 years on various computers and have never seen one. It is configured correctly in BIOS and I can boot from a live CD with it. I just can't use it once I am logged into my system.

---

### Post by Sin@Sin-Sacrifice on 2010-03-27
Does ubuntu even see the drive? The mount command can show you.

---

