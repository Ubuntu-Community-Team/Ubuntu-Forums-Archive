---
title: "proprietary ati video card driver"
date: 2009-11-05
forum: General Help
---

### Post by rossjman1 on 2009-11-05
Hello, it's been a while since I've been here. I am currently running Ubuntu 8.10 (Ibex i think) and I've been out of the loop. I tried upgrading to 9.04 the other day and I got a message saying that my video card is no longer supported by the flgrx (sp?) driver.
I did some searching around and found that the newest version (the one used in 9.04 apparently) has dropped support for some ATI cards. I saw a thread on this board and a lot of people seem to have issues with this version of the driver. Does anyone here have the same video card as me and do you have any issues with the new driver? If so, were these problems solved in the newest version of Ubuntu (9.10)?

Information (from Catalyst Control Center):
Driver Version: 8.54.3
Catalyst Control Center Version: 2.1
Graphics Card: ATI Mobility Radeon X1400
OpenGL Version: 2.1.8087 Release

---

### Post by JillSwift on 2009-11-06
I have that exact video chip-set on my laptop. The proprietary driver does *not* support this chip-set under the version of X used in 9.10. The older drivers don't support the newer X.


However, the open source driver does a pretty good job, even allowing me to use compiz desktop effects. It's far from perfect, however, "Second Life" (a 3D world/game) performs terribly, for instance.

Basically, if you're not using 3D games, it does the job.

Otherwise you may want to stick with 8.10 for a while more.

---

### Post by HiImTye on 2009-11-06
oh no, sl

---

### Post by rossjman1 on 2009-11-06
I don't play video games at all on my laptop (I use my xbox360 for that), but I do use a lot of effects in Compiz (in Gnome) and the integrated WM in KDE4. Can you confirm that the screen doesn't flicker, dual screens is functional, and that performance is reliable? I feel the need to upgrade because I constantly have to restart alsa-utils to get sound to work, and it is a pain.
Also, do you know if ATI is planning on releasing a new version of the driver that will have support and the chances that it will be included in Ubuntu 10.04?

---

### Post by JillSwift on 2009-11-06
> **rossjman1 said:**
> I don't play video games at all on my laptop (I use my xbox360 for that), but I do use a lot of effects in Compiz (in Gnome) and the integrated WM in KDE4. Can you confirm that the screen doesn't flicker, dual screens is functional, and that performance is reliable? I feel the need to upgrade because I constantly have to restart alsa-utils to get sound to work, and it is a pain.
Also, do you know if ATI is planning on releasing a new version of the driver that will have support and the chances that it will be included in Ubuntu 10.04?
I can only confirm no flicker while using compiz, and reliability generally. I don't have a second screen, sorry.

AFAIK, ATI has no plans to support these older chip-sets under the new X.

---

