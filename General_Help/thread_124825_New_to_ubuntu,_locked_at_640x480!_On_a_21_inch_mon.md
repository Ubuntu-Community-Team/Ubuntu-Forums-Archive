---
title: "New to ubuntu, locked at 640x480! On a 21 inch monitor."
date: 2006-02-02
forum: General Help
---

### Post by tokyopimp on 2006-02-02
I went into command line mode and ran the xorg auto configure, and that still didn't do it. 

I really want to get my hands dirty with Ubuntu, but it's just not going to happen at 640x480 on a 21 inch monitor! 

I have an Ati x800 Pro, and a 21' Viewsonic monitor. I am also not sure of which driver from ATI's site I should download. 

Also I am not sure if my Sound Blaster X-fi is supported, any help with this also would be welcome. 

Thanks for any help.

---

### Post by DoorGunner on 2006-02-02
Hi

This is in my opinion the best set of instructions for your ati card.
[http://ubuntuforums.org/showpost.php?p=423584](http://ubuntuforums.org/showpost.php?p=423584)

additional information you will need are your monitors specs. In particular the v-sync rate and h-sync rate.

it is a fairly painless process.....hopefully i have steered you in the right direction

---

### Post by mrcbrown on 2006-02-02
Is it a older CRT style monitor or a newer LCD? Most modern LCD and CRT's should be detected by Ubuntu, but yeah, follow the driver install - both my nVidia and ATI cards worked better under UB after manuf. drivers were installed.

---

### Post by mo_x on 2006-02-02
You probably need to set the refresh rates for your monitor. There are many topics about that on this forum. You can post your /etc/X11/xorg.conf and /var/log/Xorg.0.log so people can take a look at it.

---

### Post by Carrots171 on 2006-02-08
Creative X-Fi sound cards aren't supported under Linux AFAIK. :neutral:

---

### Post by AmboyGuy on 2006-02-08
[**HOWTO: change resolution/refresh rate in Xorg](http://www.ubuntuforums.org/showthread.php?t=83973)**

---

