---
title: "Ati gfx card not showing up."
date: 2010-03-16
forum: General Help
---

### Post by StruckByRain on 2010-03-16
[COLOR="Teal"]**My ATI Radeon 9250 gfx card is not showing up in the "Hardware Drivers" window. This makes me think it's not functioning. Please help! Thanks. =)**[/COLOR]

---

### Post by dcstar on 2010-03-16
> **StruckByRain said:**
> [COLOR="Teal"]**My ATI Radeon 9250 gfx card is not showing up in the "Hardware Drivers" window. This makes me think it's not functioning. Please help! Thanks. =)**[/COLOR]

If you are running an Ubuntu version that has propriety ATI drivers available for that card then it will be listed there, otherwise you will be using the open source drivers.

If it was "not functioning" you would not be seeing anything at all on your screen.

---

### Post by StruckByRain on 2010-03-16
[COLOR="Teal"]**I'm using ubuntu 8.04... I just got the cd from a friend... =/ How do I install the drivers? =)**[/COLOR]

---

### Post by jocko on 2010-03-16
The open source drivers are already installed, so there's nothing you need to do.
There is no proprietary driver that support your card, ati dropped support for it in 2006 (and the last driver to support your card does not work on any ubuntu release newer than 6.06).

---

### Post by StruckByRain on 2010-03-16
[COLOR="Teal"]**Lol so I just as might as well not use it because when then factory installed gfx card was in there it ran much smoother.... When I finish upgrading and such, I'll put the factory one back in. XP Seems to be my only option without have a slow pc.... One question, are all NVIDIA gfx cards compatible with ubuntu? :D**[/COLOR]

---

### Post by bignol on 2010-03-16
> **jocko said:**
> The open source drivers are already installed, so there's nothing you need to do.
There is no proprietary driver that support your card, ati dropped support for it in 2006 (and the last driver to support your card does not work on any ubuntu release newer than 6.06).


I'm using 9.04 and have an ati rage xl (rev 27).

similar problems. and video or any kind of display is jerky etc. I've seen numerous complaints and solutions, but none according to my specs.[-o< i need any help....

---

### Post by jocko on 2010-03-16
> **StruckByRain said:**
> [COLOR=Teal]**... One question, are all NVIDIA gfx cards compatible with ubuntu? :D**[/COLOR]
There are a few different versions of nvidia's proprietary drivers that together support every nvidia card from the riva 128 (released in 1997) up to and including the GeForce 295 (released in 2009).
You'll probably need a newer ubuntu version than 8.04 to get support for the newer cards in "hardware drivers", though.
There's also the open source "nv" (2d only) and the open source "nouveau" (2d for now but 3d is coming) that should support all nvidia cards.

But don't give up on your radeon card yet. There are some settings you can change that may improve the performance of the open source driver. Check [this]("http://ubuntuforums.org/showthread.php?t=1305349&") thread.

---

### Post by Mark Phelps on 2010-03-16
> **bignol said:**
> I'm using 9.04 and have an ati rage xl (rev 27).

similar problems. and video or any kind of display is jerky etc. I've seen numerous complaints and solutions, but none according to my specs.[-o< i need any help....

The quoted area in your original post answers your question.  There are no ATI restricted drivers for your card that work in the newer Ubuntu versions.

---

### Post by bignol on 2010-03-16
> **Mark Phelps said:**
> The quoted area in your original post answers your question.  There are no ATI restricted drivers for your card that work in the newer Ubuntu versions.


Indeed. so therefore, I guess people simply just accommodate with the lag or purchase a newer video card... thats kinda depressing :shock:

---

### Post by jocko on 2010-03-16
> **bignol said:**
> Indeed. so therefore, I guess people simply just accommodate with the lag or purchase a newer video card... thats kinda depressing :shock:
Well... Since Rage XL was a low-budget card when it was released in 1999, I'm impressed that anyone is still using one.

---

### Post by Mark Phelps on 2010-03-16
> **bignol said:**
> Indeed. so therefore, I guess people simply just accommodate with the lag or purchase a newer video card... thats kinda depressing :shock:

Yep ... for the older cards, it's open source or nothing -- now that ATI has abandoned them in Linux.

---

### Post by bignol on 2010-03-16
> **jocko said:**
> Well... Since Rage XL was a low-budget card when it was released in 1999, I'm impressed that anyone is still using one.


It came factory. My pc is refurbished, has raid and everything. no sound card (whoomp waaaaa) and this crappy video card. 

So far I have tried editing swap (currently set to 10) reducing hardware acceleration in flash, even tried using envy, which has locked me out of my computer before. I'm scared to restart [-(

---

### Post by Mark Phelps on 2010-03-17
> **bignol said:**
> I... even tried using envy, 

Using envy is OK if there IS an ATI driver, but since there is not, it will only trash your display. So, save yourself the grief and don't bother with it.

---

### Post by jocko on 2010-03-17
> **bignol said:**
> ... even tried using envy, which has locked me out of my computer before. I'm scared to restart [-(
All envy does is that it installs the proprietary driver (fglrx, which currently supports radeon hd2000 and newer cards). Since there has **never** been any proprietary driver that supports any rage card (or anything else below radeon 8500), you'll just end up with a broken Xorg. Ati even discontinued support for rage cards in windows xp in 2002.

---

