---
title: "ATi Display no longer detected after update"
date: 2010-06-16
forum: General Help
---

### Post by milesbh on 2010-06-16
Hello all

I'm running Ubuntu 10.04, and after I installed a batch of updates, I restarted the computer and it gave me the low graphics mode window, and said that it couldn't detect any input from the display. I tried the option to start it in low graphics mode and it just tells me to wait while the X restarts I think, and then eventually it shows the same window with a full bar and I have to click 'OK' as the cancel button is grayed out and there's no other options, and then I'm just left with a blinking cursor in the top left of my screen. I can shutdown fine and I can login using the terminal kinda access (basically no GUI).

I have an ATi HD3200 and I was using the default driver that installs with Ubuntu, not fglrx.

Any help would be much appreciated. Sorry about the vague description of my problem, if no one can help using this description I'll give more details another day and post the logs.

---

### Post by dwel on 2010-06-16
Im still reletively new myself, but, when I updated from 9.10 to 10.04 nvidia was messed up. I uninstalled the drivers completely and reinstalled. Im still happy.

---

### Post by Milesdust on 2010-06-16
Well I have no idea how to reinstall the open source drivers. I would do that if I could but I don't know how. Do you know how or where I can find a guide that tells me how?

---

### Post by dwel on 2010-06-16
When my drivers messed up, it still gave me an option to start in low graphics mode, sometimes it would just bring me to a terminal where I would type 'startx'.


Then, goto system>administration>hardware drivers and remove the driver. reboot and goto the same place and re-install it.

Funny thing tho, after I un-installed the driver, my next boot did not have problems, as in: it didnt ask me if I wanted to start in low graphics mode.

EDIT: Perhaps [This]("https://help.ubuntu.com/community/BinaryDriverHowto") can help.

---

### Post by Patrick Wang on 2010-06-17
I also experienced the same problem this morning. I went to ATI website to download the latest driver (10.06), uninstalled my previous driver (10.04), restarted the machine, installed the latest one. and then it is all set. hope it helps.

---

