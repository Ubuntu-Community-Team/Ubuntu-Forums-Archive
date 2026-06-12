---
title: "boots to blank screen"
date: 2011-04-11
forum: General Help
---

### Post by teroges on 2011-04-11
I just upgraded my motherboard from a Amd Athlon 2200 to a AMD Sempron 3400 and changed video card from a Nvidia Gforce AGP card to a ATI Stealth S120. i am running 512MB ram, it is a dual boot system with Windows XP, XP runs fine but when i boot into Ubuntu 10.10 once it hits the login screen the screen goes blank. It appears Ubuntu is still loading but i can't see anything, Monitor goes into standby mode. Really wnat to get back to Ubuntu any help is very much appreciated.
 
 
Thanks 
 
Tim

---

### Post by Duncan Williams on 2011-04-11
Hi, I am sorta having the same issue. without going into all the details.
1. Have you tried going into recovery mode at boot screen.
then select failsafe graphic mode.
then use failsafe graphics for this session.
(this got me from blank screen to full gui with full monitor resolution and no problems I can notice)

2. Just downloading latest updates for natty and there are updates for graphics cards etc)

---

### Post by Duncan Williams on 2011-04-12
After downloading updates and a few reboots.
Boots straight into unity ubuntu.
Full resolution and using my fx5200 nvidia card.

---

### Post by alphaamanitin on 2011-04-13
What version of Ubuntu are you using?  I had something similar happen with 9.10 and below.  It would go to grub, I would see the Ubuntu logo and then a black screen.  Turned out that grub was trying to boot from my second hard drive.  Once I set the drive location, hit e in grub to edit boot menus, everything worked fine.  I then changed from drive locations, eg "/dev/sdb/" to UUIDs and never had the problem again.

AlphaA

---

