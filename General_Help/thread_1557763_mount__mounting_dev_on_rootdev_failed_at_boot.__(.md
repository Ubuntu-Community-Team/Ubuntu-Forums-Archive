---
title: "mount : mounting /dev on /root/dev failed at boot.  :("
date: 2010-08-21
forum: General Help
---

### Post by Roig on 2010-08-21
Hello i need help, because i don't know what i'm doing wrong..

I installed ubuntu 10.04 from the CD (downloaded from ubuntu website), all worked very well. until today that I decided to run the software updater. It installed all the updates correctly, I restarted ok, but i experienced a mini locks, for example when i was with firefox, firefox had mini hangs for about 15 seconds then run normally. Then all OS got unstable, windows showing no thing, for example when i tried to restart using the button, it didnot do anything. 

Well i reset my computer and BOOM!, im stuck after Grub showing me this: 

mount : mounting /dev on /root/dev failed : No such file or directory
mount : mounting /sys on /root/sys failed : No such file or directory 
mount : mounting /proc on /root/proc failed : No such file or directory
Target filesystem doesn't have /sbin/init
No init found. try passing init= bootarg
Busybox 1.13.3 ( Ubuntu 1:1.13.3-1ubuntu11) built-in shell (ash)

(initramfs)


.....

What's the problem.. ?

I'm able to reproduce this. I installed a fresh 10.4 again, then installed propietary drivers (nvidia), restart, all working flawless here, then updating all packages using the update-manager, restart, here not all working well (same sympthoms) so i decided to restart, then BOOM AGAIN..

I did the process 3 times and, the same, so I think something is BROKEN. So im able to reproduce it but don't know what the hell is causing it.

Anyone can help me a bit please? 
Thank you, and sorry for my poor english.

---

### Post by dino99 on 2010-08-21
mountmanager is an easy tool to deal with partitions and devices. Set your prefs into: system admin mountmanager (after installation of course ;))

---

