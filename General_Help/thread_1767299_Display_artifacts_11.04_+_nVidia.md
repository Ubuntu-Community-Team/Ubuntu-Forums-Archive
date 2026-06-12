---
title: "Display artifacts 11.04 + nVidia"
date: 2011-05-25
forum: General Help
---

### Post by fsleeman on 2011-05-25
I have been getting some strange display artifacts since I upgraded from Ubuntu 10.10 to 11.04. I am using the Ubuntu packages for the nVidia drivers and am pretty sure I was doing the same in 10.04.

My card is a Quadro NVS 290 using nVidia driver 270.41.06. Everything was perfect before the upgrade. Here is a picture of the issue I am having:

[http://img59.imageshack.us/i/screenshotiuf.png/](http://img59.imageshack.us/i/screenshotiuf.png/)

The open slits at the top of the Firefox window are not really there, its part of the display problem, as well as the "hole" in the top menu bar.

Any ideas? Should I have install the drivers manually?

---

### Post by DinoT1985 on 2011-05-25
have you tried using the other prop driver?

---

### Post by fsleeman on 2011-05-25
Do you mean from the nVidia site? No, I have not tired another driver. I a little confused with the current nVidia driver situation with Ubuntu. It appears there are several different nVidia driver types I could use:

1) install .sh from nVidia website
2) package install from Ubuntu (what I am using)
3) Nouveau driver

Are there options I am missing? Which version is supplied by Ubuntu?

---

### Post by wildmanne39 on 2011-05-25
> **fsleeman said:**
> Do you mean from the nVidia site? No, I have not tired another driver. I a little confused with the current nVidia driver situation with Ubuntu. It appears there are several different nVidia driver types I could use:

1) install .sh from nVidia website
2) package install from Ubuntu (what I am using)
3) Nouveau driver

Are there options I am missing? Which version is supplied by Ubuntu?
Hi, there is usually two nvidia drivers in additional drivers, he is suggesting the you try the other one.

---

### Post by fsleeman on 2011-05-31
I tried the other driver (listed as 173.14.30 in nvidia settings) but am seeing the same problem.

---

### Post by fsleeman on 2011-06-02
Any thoughts? I didn't have any problems until I upgraded from 10.10.

---

### Post by BatteryKing on 2011-07-22
I am having the same problem with my system under 11.04 (using nVidia driver for my GForce 260) and the classic theme as Unity is totally worthless.

I installed 11.04 on a neighbor's computer (who is using a GForce 8600 GT) and he also hated on Unity pretty hard, so I switched him to classic, which he liked a lot better, and he had the same glitchy graphics problem where the background will show through no matter what window was open.  He also insisted on just using Firefox, so this problem is not related Chrome (as suggested by other posts).  So something is either broken with the classic window manager or something else in the graphics stack.

Also, what is the point of Unity?  Most Windows users I know are pretty fed up with Windows shenanigans and Windows is in the majority while every single Mac user I know is a zealot and wouldn't seriously consider another operating system.  So all Unity does is alienate all current and potential new users, especially when classic mode is broken probably because Unity is the development team's focus, not classic.

---

### Post by fsleeman on 2011-11-21
This problem appears to be fixed in Ubuntu 11.10. When I upgraded the artifacts completely disappeared.

---

