---
title: "Using Ubuntu for the first time... Help!"
date: 2009-08-18
forum: General Help
---

### Post by James El Coco on 2009-08-18
OK, here's my situation... I am a brand new Ubuntu user having switched from Windows, trying to get everything to work on my Gateway MT3705 Laptop, I've tried 9.04 Jaunty, but am now running 8.04 Hardy, but it seems neither version will work perfectly with what I've got (yet!). In 9.04 my main issue is my Radeon Xpress 200M graphics card... this issue culminated with me trying to fix it with "fglrx" only to crash the whole system (at which point I installed 8.04 thinking it might work better).
Please keep in mind that before this I had ZERO knowledge of Linux or Ubuntu... I only tried 'fglrx' after much research into how to use the terminal commands, something I'm improving with, but still not 100 percent confident.
So... current problem with 8.04 is my wireless and ethernet... I have a Realtek 8185, which is currently inoperable in Ubuntu. No big deal, I thought, I'll plug into my parents DSL and download the updates needed from that... but that doesn't work either; they have BellSouth/ATT DSL with a Westell modem and no matter how I tried to configure it, it just wouldn't work (I did use it succesfully in 9.04, so I know it can be done). In Network Settings I tried setting the Wired connection to DHCP, but that didn't help. Also curious, what is the difference between 'eth0' and 'eth0:avahi'?
Today I've been trying to download drivers for the Realtek 8185 on a different computer, then transferring them to my laptop and installing them by hand. I downloaded Realtek's Linux driver from their website, and thought I was doing well following their instructions for the installation using terminal commands, but after "make", "make install" wouldn't work because it can't create the necessary directory. I tried to create the directory myself in the File Browser, only to discover I don't have permission (again... zero linux knowledge. This whole 'root' thing kind of confuses me).
Also having hard drive issues... about the half the time 9.04 would not find the hard drive on startup and drop me back out to a shell. 8.04 hasn't done this yet, but it incorrectly lists my available space as 177GB (impossible: I have a 100GB hard drive). This may just be that my hard drive is going bad, but I'm not sure how to test it.
Sorry if I'm being long-winded, just trying to be thorough. Any advice for a newbie is greatly appreciated!
thanks,
-Mike

---

### Post by oldos2er on 2009-08-18
After **make**, run **sudo make install**. You need to use **sudo** to get root privileges.

---

### Post by James El Coco on 2009-08-18
Thank you!  I knew it was something simple I was overlooking.

---

