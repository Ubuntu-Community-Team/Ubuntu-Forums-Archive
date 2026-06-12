---
title: "Ubuntu Desktop Crashes"
date: 2012-01-08
forum: General Help
---

### Post by likeabat7 on 2012-01-08
Hey! This is my first post. My desktop running Ubuntu 11.10 64-bit has been having... problems staying alive. It will run for awhile then crash randomly. The time varies but it's generally withing 15 minutes of startup. It crashes whether I'm logged in or just at the log in screen. It automatically starts back up by itself. After I log in Ubuntu doesn't acknowledge it's crash or show a report that I know of. I am running a dual boot system and Windows 7 is working fine. I've had my CPU overheat before when I was testing it in windows and it shut down just like its doing in Ubuntu. I can boot up and use the terminal for limited amounts of time so if I need to supply any more info just let me know. Thanks!

---

### Post by Kevin McCready on 2012-03-14
My desktop in Lubuntu also goes weird every now and then. It seems to be another desktop all together from an earlier time - but all the info is not displayed. 

I'd tell you the details of my system but I can't access them now because none of my icons work. I'm on Lubuntu 11.something as far as I can remember.

---

### Post by swright007 on 2012-03-15
Did both of you upgrade from prior installations?  Perhaps the upgrades didn't go well.  I see you are both using 11.10  You might check to see if 2D mode is working better. It might just be a Unity error.

I wiped my partition just the other night and did a fresh install of 12.04 Beta 1 and it has been running slick.  I've used it for 8+ hours at a time and haven't had any worries... so far.  For stability I also run 10.04 on a separate partition.  

If you like and want to use 11.10 and you did have a messed up upgrade, perhaps a partition deletion and fresh install might cure the blinky desktop ills.  If you choose to do that, make sure you back up any important info, email addresses, pictures... etc.. beforehand.

---

### Post by Kevin McCready on 2012-03-15
no upgrade, except for accepting the update manager recommendations every few days.

I'm reluctant to wipe the system before I learn how to make a copy with usb-creator-common which is still proving problematic also

---

### Post by swright007 on 2012-03-15
The problematic USB CREATOR, had that problem recently too.  My issue with that was that I was plugging into the USB ports on the front of my computer and it would fail making a boot drive every time.  

It turned out that the ports on the front of my computer were Version 1 USB (very old)... the ports on the back of my computer were Version 2-3... Much newer and actually worked.  So try the USB in the back of your computer if you are using the ports up front! 

make sure you go into Disk Manager.  Once there select your USB drive (make SURE it is your USB drive you are selecting... VERY IMPORTANT (I lost all the data on a 2 TB HD cause I was half asleep recently))... un-mount your USB Flash drive. Then format it as FAT. Then MOUNT your drive again.  

Go into USB creator and try to install your image of 11.1 to your flash drive.

---

