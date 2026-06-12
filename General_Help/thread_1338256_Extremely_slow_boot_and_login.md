---
title: "Extremely slow boot and login"
date: 2009-11-26
forum: General Help
---

### Post by Bullnose on 2009-11-26
Hi

I am running Ubuntu 9.10 on an Acer laptop. Everything was running fine until yesterday when I started up. It would boot to the login screen but there would be no login prompt box. It took about 2-3min for the box to show and when it did it would be just an all black or white box. Another minute and I could pick the user to login with. It takes another 1-2min before the password prompt comes up. The rest of the boot is just a little slower then normal. After that it seems to behave normally except for calling up the power manager does take a lot longer then it use to.

Anyone have any ideas?
Thanks

---

### Post by Bullnose on 2009-11-26
bump

---

### Post by boffyflow on 2009-12-01
I am experiencing the exact same problem with my Acer Travelmate 8200 since upgrading from 8.10 to 9.04. No problems during the upgrade process. I am suspecting that GDM is the culprit, but I am currrently at a loss.

Any pointers greatly appreciated.

Thanks.
Boffyflow

---

### Post by gmac99 on 2009-12-02
I am also having the same problem! Can anyone help? Thanks

---

### Post by joruz on 2009-12-05
Same prob here. Slow boot on my Acer notebook. Worked fine until 9.10

---

### Post by butcherbill on 2009-12-31
hello, I am using Acer TM 8200, I have the same problem, why? Only on ACER?

---

### Post by doobydave on 2010-05-16
Any news on this at all?

I have just installed 10.04 and 9.10 (both x64) on my ACER 5685 and I have long boot woes (3 mins)

In 10.04 I would get a dialog box on log in about the battery management app failing. No message on 9.10, but I'm guessing it is the same problem.

Booted up normally when not plugged in to the mains.
Edit, but has not done so again...

---

### Post by Maxlite on 2010-05-17
Add me to the list of slow-booters.  Only my problem is between 'power-on' and Grub (I think).  My sequence of events: power-on, wait, large command underline, wait, small underline, wait, boot starts and all is normal. Tried a re-install, same thing. Total boot time is about 2 minutes. I'm using a Toshiba Satelite A205-S5855. I'm giving serious consideration to wiping the disk clean with Gparted and re-installing again. Reinstalling Karmic (9.10) is under consideration too.  :confused:

---

### Post by doobydave on 2010-05-17
I doubt 9.10 would help, maybe try 9.04?

This looks like a bug in gnome-power-manager. Have just been reading some launchpad bug reports, and one reports the screen-dimming buttons not working. Well, my screen dimming buttons don't function, but it is the long boot time that is bugging me.

I read somewhere about switching off AHCI, but being a laptop, the BIOS is not up to anything like that.


.xsession-errors
(gnome-power-manager:2298): devkit-power-gobject-WARNING **: Error invoking GetAll() to get properties: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.

---

### Post by Maxlite on 2010-05-17
I didn't have any problems with 9.10 or 9.04.

I don't think the power manager has anything to do with it.  It's not in effect between power-on and when I see code starting to run. (is it?)

I'll have to look into the screen dimming bug.  Earlier today, while I was typing, this thing started to go in to power saving mode.  My dimmer works okay.

Crazy thing is, my wife's Dell laptop works fine with 10.04.  :confused:

---

### Post by doobydave on 2010-05-18
Well, i'm pretty certain my bug is gnome-power-manager related.

Only just realised you are not using an Acer (unlike everybody else who has posted here).
Do you have the battery icon present in your taskbar? Mine never makes it (except for that one time when it booted normally...)

---

