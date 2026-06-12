---
title: "Cant boot into ubuntu 9.10"
date: 2009-10-27
forum: General Help
---

### Post by sickly on 2009-10-27
I have just bought a brand new hp pavillion dv4-2045dx that came with windows 7 installed on it. I was exited to install ubuntu on it when i got home and it boots up but after the ubuntu sighn it shows what might be some errors but not sure cause it happens to quickly, and then just stays on a stopwatch. Any ideas?
specs:
 
processor: AMD Turion II Dual Core M500 / 2.2 GHz
RAM:4 GIG DDR2
Display Type 14.1 in TFT active matrix 
Max Resolution 1280 x 800 
Graphics Processor / Vendor ATI Mobility RADEON HD 4200 
Video Memory 128 MB

---

### Post by XDevHald on 2009-10-27
Welcome to Ubuntu and the Forums!

First off we don't recommend using the beta development of Ubuntu Karmic as it's buggy and you're willing to go through the valley of death for a few more days. To make it easier, reinstall Ubuntu Karmic (the install takes only 10-15 minutes) and start fresh. 

Be sure to REMOVE Windows 7 as this will be considered a fresh operating system for your computer with nothing else installed other than Ubuntu. Post back if you have any other issues after the reinstallment.

---

### Post by jbrown96 on 2009-10-27
> **XDevHald said:**
> Welcome to Ubuntu and the Forums!

First off we don't recommend using the beta development of Ubuntu Karmic as it's buggy and you're willing to go through the valley of death for a few more days. To make it easier, reinstall Ubuntu Karmic (the install takes only 10-15 minutes) and start fresh. 

Be sure to REMOVE Windows 7 as this will be considered a fresh operating system for your computer with nothing else installed other than Ubuntu. Post back if you have any other issues after the reinstallment.

No that's ridiculous. Don't reinstall, and you certainly don't need to remove 7 if you don't want to. 
When you first boot the computer, hold the Shift key and you should get a "grub" menu. there should be a recovery option that will boot without the splash screen, so you can get a better look at the error messages. Try to post them back here. Eventually, you should get to a menu where you can choose a "root shell". take that option then try ```
su user-name
``` replace with your username, then ```
startx
``` Let me know if that gets you to the desktop, or try to post the errors here. 

Did this happen on the first boot? Were you able to install Ubuntu from the liveCD; if so, did you have any problems booting it?

---

### Post by sickly on 2009-10-28
thanks for the replys. But i did not even get to install yet because i cant even boot from the live cd. here is what the error says,
 
loading / ubnkern
loading / ubninit
 
modprobe:fatal: could not load /lib/modules/2.6.28-11-generic/modules.
dep: no s
 
loading, please wait....
 
busy box v1.10.2 (ubuntu 1:1.10.2-2 ubuntu7) built in shell (ash)
enter help for a list of buillt
 
 
 
And that is after the ubuntu loading screen stays on for about 3 mins.

---

### Post by ctc26 on 2009-10-28
What ISO are you using of Karmic - Beta, RC, or Daily Build?

Also 32 or 64?

---

### Post by sickly on 2009-10-28
sorry i forgot to say that those errors were from 9.04

---

### Post by P4man on 2009-10-28
In the main menu of the cd there is option "test this cd for defects" 
Run it, see if there is no problem with the cd (most likely cause)

If it does report problems, you may want to download the iso again ( i recommend doing so with bittorrent) and burn it again at the slowest possible speed. Or make a bootable USB stick if you dont like wasting cd's. To make the stick you can use this:
[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

assuming your pc can boot from usb.

---

### Post by P4man on 2009-10-28
> **XDevHald said:**
> 
Be sure to REMOVE Windows 7 as this will be considered a fresh operating system for your computer with nothing else installed other than Ubuntu..

Thats just nuts. Maybe the original poster should also give away to charity any other windows pc's he owns before we help him with his problem (which is clearly totally unrelated to windows) ?

---

### Post by ctc26 on 2009-10-28
I think the modprobe failure is unrelated.

Could be a graphics issue, try booting into 'safe graphics mode' at the beginning of the LiveCD.

Also make sure all of your BIOS settings are default, especially any that relate to Quietboot. 

Worse case senario, you could try the Alternate CD to at least get an install on your machine.

---

### Post by sickly on 2009-10-28
thanks for all the replies guys. But the problem here was that it was a bad cd or download. I now have ubuntu up and running since i dl and burnt a new copy. Thank again!

---

