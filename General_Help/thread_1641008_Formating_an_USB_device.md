---
title: "Formating an USB device"
date: 2010-12-08
forum: General Help
---

### Post by nearlymagicman on 2010-12-08
Well, i guess the topic header is a give away. I want to format my USB-Stick, i looked in the internet and actually came up with two ways:

-gparted -> doesn't work at all, it doesn't even show the stick

-Konsole:
sudo umount /media/Stick    
sudo mkfs -t vfat /media/Stick
sudo eject /media/Stick
(even tho i am not a big fan of commands i don't get, i tried it and got this error line:
 mkfs.vfat 3.0.7 (24 Dec 2009)
/media/EEB3-EFCB: No such file or directory)

so well, neither way did work. Is there an other solution i might try?

&#8364;: Well it actually worked as far that none of my Ubuntu OS can recognize the stick anymore so i need a way to mount the usb stick as well!

---

### Post by ajgreeny on 2010-12-08
I am very surprised to hear that gparted does not see the stick.  What about fdisk?  Try ```
sudo fdsik -l
``` in terminal to find out if the stick is seen by the system that way, and if so what the output might be.

Are you certain the stick is still a good one and has not died?

---

### Post by Dennis N on 2010-12-08
With gparted, did you remember to choose the correct device (probably /dev/sdb) from the drop down box in the upper right?

---

### Post by argedion on 2010-12-08
Try to remove the drive and then reconnect it. I know for my USB drives that I have and use to format them I simply right click the icon on the desktop and choose format. I'm Using Ubuntu 10.04 with of course the Gnome Desktop.

---

