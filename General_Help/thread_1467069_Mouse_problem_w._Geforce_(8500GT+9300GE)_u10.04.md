---
title: "Mouse problem w. Geforce (8500GT+9300GE) u10.04"
date: 2010-04-30
forum: General Help
---

### Post by vitkowal on 2010-04-30
System: Ubuntu 10.04 64bit
Geforce (8500GT+9300GE) with one Monitor each. 

Hi everyone!

It seems that I have upgraded my distribution too early. 

The Mouse does not work properly on the screen of the 9300GE - this error was not present with u9.10. 

Problems: 

Mouse pointer wiggles as soon as it comes on the affected screen (ancillary screen, menue-screen is ok), is difficult to move back to the functioning screen, mouse buttons do not work. 

Display of icons and windows is ok, just the mouse does not work. 

The display mode in Nvidia X-Settings is xinerama, driver Version is 195.36.15, nvcontrol-ver 1.22, X-Server-vendor-ver 1.7.6

Any ideas? 

Thanks a lot in advance!

vitkowal

---

### Post by everaldo.peixoto on 2010-05-01
Hi, same problem but using the 32 bit Ubuntu version. 
In my case, I have two, a litle bit old, Nvidia cards, wich one with one physical display, this configuration worked fine in xinerama on Ubuntu 9.04 and 9.10, now although the secondary screen seems to be normal, when I put the mouse cursor there it (the mouse cursor) starts to flash and became very difficult to move, once I'm able to get it back to the main screen , there (on the main screen) everything works properly. 

I've edited the xorg.conf, trying some variations on input devices configuration, with no success.

Any suggestions?

Regards,

Everaldo

---

### Post by johansson.seb on 2010-05-08
Yep, this is probably [Bug #563100]("https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/563100").

---

### Post by vitkowal on 2010-06-16
Thanks a lot for pointing out the bug related to this - I just hope it will be fixed soon. 

I worked around it by plugging both monitors into one graphics card and using the other card as means to turn electricity into heat until the bug is fixed. 

Of course I'd love to hear about a fix for this bug. Thanks in advance! 

Greetings, 

mat

---

