---
title: "Honestly having real trouble even starting ubuntu :("
date: 2010-05-27
forum: General Help
---

### Post by 0perator on 2010-05-27
Hey guys, just posting here for any ideas as to what may be the problem, perhaps it's my computer (doubt) or perhaps I'm doing something wrong (likely).

So, I started off with 10.04, downloaded from the site and burnt to CD (checksummed and everything) i then rebooted my PC and booted from CD, the ubuntu loading screen starts, it doesn't ask what i want to do it just has a purple screen and at the bottom is what i presume to be a keyboard and a person inside a circle.
Then the red and white balls come, and that's when my computer freezes and the caps lock and scroll lock lights start to blink.

Then i tried 9.04 and the CD would boot, and have me select a language, after that i chose "install ubuntu" and it froze up and said READ ERROR. tried burning to a different CD and the same thing happened

then, downloaded 9.10 and the flashing ubuntu logo just sits there flashing for about 15 minutes, the first time i booted up i came back after about 30 mins and i had a bunch of error messages on the screen, like "tty1 respawning too fast, stopped" when i pressed ALT+F2 it says the same except for tty2 instead of 1.

Any ideas or help would be much appreciated thank you!

---

### Post by Ozymandias_117 on 2010-05-27
During the wierd purplish screen, press esc. Then select your language and try "Check Disk for Errors" (Or something to that effect)

---

### Post by 0perator on 2010-05-27
Will try that sir, and get back to you!

---

### Post by 0perator on 2010-05-27
OK, I'm in!

The error was that the windows file system was not closed, and it kept looping through that :-/

However the "installer" encountered an unrecoverable error. I am about to run the installer from the desktop session now. Will keep you posted.

---

### Post by 0perator on 2010-05-27
[Errno 5] Input/output error

This is often due to a faulty CD/DVD disk or drive, or a faulty hard disk. It may help to clean the CD/DVD, to burn the CD/DVD at a lower speed, to clean the CD/DVD drive lens (cleaning kits are often available from electronics suppliers), to check whether the hard disk is old and in need of replacement, or to move the system to a cooler environment.

Going to burn to a new CD should be ok then, i hope!

---

### Post by lykwydchykyn on 2010-05-27
If you have a flash drive handy, you might try installing from that if the CD fails again.  LiveCD's demand a lot from the CD drive, and I've found that an optical drive that's even a little problematic can stop an installation.


see [https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

---

### Post by Ozymandias_117 on 2010-05-27
> **lykwydchykyn said:**
> If you have a flash drive handy, you might try installing from that if the CD fails again.  LiveCD's demand a lot from the CD drive, and I've found that an optical drive that's even a little problematic can stop an installation.


see [https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

+1

The other option is to try to burn it at a slower speed.

---

### Post by 0perator on 2010-05-27
edit: My bad! just spotted the link, thank you!

---

### Post by 0perator on 2010-05-27
OK! Cooking on gas :) awesome thanks a lot for your help.

Now where's screens and graphics gone, I need to get my res to 1280x1024 but i cant find the tool i used to use in /usr/share/applications

:(

---

### Post by 0perator on 2010-05-27
Never mind, i did it. I went to System > Administration > nVidia X Server Settings and changed it there!

Cheers for all your help!!

---

