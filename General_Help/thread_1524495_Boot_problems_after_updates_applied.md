---
title: "Boot problems after updates applied"
date: 2010-07-05
forum: General Help
---

### Post by apesa on 2010-07-05
New behavior after upgrade to 10.04 from 9.10. A couple weeks ago I upgraded my 9.10 64 bit to Lucid. Upgrade went well, but during the first reboot into Lucid it never got past the splash screen. I got around that by going into Grub and booting in failsafe and once in I installed the ATI support and managed to get it to reboot. Last night I applied recommended updates and I am now back at the same stage, but can't get into the grub menu, the esc key does not want to work.

During boot it will act normal until it passes grub. Once past I get the message Starting Up, it pauses and displays the following message - "udevd work (127) inotify_add_watch (6, /dev/dm2... ,10) Failed no such file or folder" it then moves into the 10.04 splash screen with the four dots and then I get a blank plum or maroon screen w/o the login option.. Just a blank screen. There it will sit forever.

Another weird behavior.. When the screen sits idle for a while and I go to log back on I will get the login screen, enter my password and it will return me to the desktop.. for a split second. It will then return me back to the logon screen where I will have to enter my password once more and log back in. The second time I logon works fine.

---

### Post by dino99 on 2010-07-05
seems you have raid installed

---

### Post by apesa on 2010-07-05
> **dino99 said:**
> seems you have raid installed

An observation that is.. based on the device failure message for drive mapper.... But the real problem is or was my inability to get into Grub and boot into failsafe.. I finally was able to catch it just right using the esc key after approximately 100 reboots and got in with failsafe low graphics mode. reinstalled my ATI drivers and i'm back in business.

Any info on why I am having this much trouble getting a grub menu is much appreciated.

Pat

---

### Post by oldfred on 2010-07-05
If you are using old grub you press and hold the escape key from BIOS boot until the menu appears. If new grub2 then you use the shift key.

---

