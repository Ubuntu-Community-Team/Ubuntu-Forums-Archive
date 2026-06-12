---
title: "Ubuntu 10.10 freeze on boot (also 10.04 and Mint 10)"
date: 2010-12-26
forum: General Help
---

### Post by kalliba on 2010-12-26
Hi all,

First of all, love Ubuntu. I have a Toshiba Satellite A205 laptop 2GB RAM, running Meerkat 32bit. Used 2 previous versions of Ubuntu also.

For the past few months, about 75% of the time, on boot up the screen will freeze before I get to the login screen. No key combos (ctrl alt backspace, alt prnt screen, REISUB) work, I have to take out the battery, unplug and restart. It always boots normally the second time, whether I boot normally or attempt repair.

I recently installed Linux Mint 10 on dual boot, and the same thing happens with Mint.

I connect to the Internet via wireless, not sure if that is significant or not.

Please help me figure this one out. The problem does not appear immediately after installation, but only after updates and a couple reboots.

In the past, I did complete reinstalls of 10.04, 10.10 several times, using entire hard drive, and the same problem occurs. 

Thanks :)

---

### Post by spantch101 on 2011-01-05
ok .. seems the problem has been with the pm-utils in synaptic if you are having this issue check synaptic and see if you are running 1.4... if you are remove it and reinstall older version 1.3 here [http://packages.ubuntu.com/de/lucid/...utils/download](http://packages.ubuntu.com/de/lucid/...utils/download) fixed my problem... i just unplugged my laptop and its running perfectly... thanks to aspera for this info on launchpad hope this works for you...after install of 1.3 reboot just in case ...let me know how it works out for you.

---

### Post by rbrbos1 on 2011-01-05
Thank you spantch101 :) 

I found another way to avoid the problem, I don't understand why it works, but it does seem to work, so far:

simply, I remove the USB dongle for my Logitech (310?) Nano mouse whenever booting, and whenever updating. 

I did a fresh install 10.04, without the USB dongle inserted. Did all the updates without the mouse. Updated to 10.10, without the mouse installed. Running fine.

In some way,  updates screw up the left mouse button, if the USB mouse is active during the update.  

I am dual booting Linux Mint 10, and using the same method, no problems there either.

This only affects my laptop. My desktop has another model Logitech USB mouse/keyboard combo, and no problems at all with Ubuntu or Mint.

If the problem recurs, I'll try the deprecation. ):P

---

### Post by rbrbos1 on 2011-01-05
> **spantch101 said:**
> ok .. seems the problem has been with the pm-utils in synaptic if you are having this issue check synaptic and see if you are running 1.4... if you are remove it and reinstall older version 1.3 here [http://packages.ubuntu.com/de/lucid/...utils/download](http://packages.ubuntu.com/de/lucid/...utils/download) fixed my problem... i just unplugged my laptop and its running perfectly... thanks to aspera for this info on launchpad hope this works for you...after install of 1.3 reboot just in case ...let me know how it works out for you.

The link you provided doesn't work for me, brings up an Error page; 

Also, pm-utils affects power management, why would that affect the mouse?

---

### Post by rbrbos1 on 2011-01-05
apologies spatch101, I confused this thread with another, been having problems with the left mouse button

regarding freeze-ups, even though i have pm-utils 1.4.1-3, I've experienced no problems since reinstall of 10.10 and mint 10; 

this may be because I am using AC power only;

again, sorry for the confusing posts :(

---

