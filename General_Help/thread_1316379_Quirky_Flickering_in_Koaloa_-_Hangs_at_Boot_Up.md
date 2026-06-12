---
title: "Quirky Flickering in Koaloa - Hangs at Boot Up"
date: 2009-11-05
forum: General Help
---

### Post by cheaphacker on 2009-11-05
My system was down for a few days and I couldn't get my Karmic Koala to come up.  The screen would flicker with a command prompt asking me to enter my login.  It was flashing enough I was lucky I didn't get a seizure.  Anyway, I was able to get the command prompt in recovery mode and followed the instructions in this link, which saved me and I'm up and running again: [http://ubuntuforums.org/showthread.php?t=1300881](http://ubuntuforums.org/showthread.php?t=1300881).

I couldn't post a thanks because the thread was closed but I wanted to say thank you to eznet and shulegaa for posting this information.  For what its worth I switched between an old nvidia card, pro 64 I think it was, and an ATI Rage 128, which I'm running now.   Switching them and trying to install the drivers for each helped not at all.  Following the directions above to tweaking the xorg.conf file with the below allowed me to reboot normally.  Busid does have to be changed for your specific video card.  Good luck to all of the new Koala folks out there...

Section "Device"
           Identifier       "Configured Video Device" 
           Busid                  "PCI:01:00:00"
 EndSection

---

