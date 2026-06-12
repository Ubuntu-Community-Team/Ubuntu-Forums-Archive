---
title: "How far is ATi supported as kernel driver"
date: 2010-06-22
forum: General Help
---

### Post by filip007 on 2010-06-22
How far is ATi supported as kernel open source driver...?

I know that Radeon X1950 works fine but what about HD models like 2600PRO and 3650?

---

### Post by XSAlliN on 2010-06-22
As far as HD 4xxx - with 2D acceleration and limited 3D acceleration. Also limited features, but not even proprietary drivers (the linux ones) can top this. They're actually worse for everyday usage (can't se Refresh rate right) yet better for 3D applications like games - but if this your aim, then would be better to remove linux from your equation (at least for now).

---

### Post by Mark Phelps on 2010-06-22
> **filip007 said:**
> How far is ATi supported as kernel open source driver...?

I know that Radeon X1950 works fine but what about HD models like 2600PRO and 3650?

Actually this is a really good question ... for which I only have a partial answer.

The "standard response" would be "great" -- because of the open source RadeonHD driver.  But I read recently that this driver has been dropped,and now, only the Radeon driver will be continued.

Sorry, I can't find the actual source of that info.  But I remember the author said the HD driver had been supported under OpenSUSE.

If you want more details, probably the best place to go is the Phoronix forums.  They do a LOT of work with the different ATI drivers.

---

### Post by filip007 on 2010-06-27
Thank you...both

Yes i was asking the same thing on Phoronix but they did not know that Radeon 3D desktop effects works directly from CD/DVD when boot and they offer me a Geforce, so much about help on Phoronix.

So best driver is still just for R600 aka Radeon X1950, this GPU is still give a big kick, family system has X1950XT model and still play most of the games on W7.

Maybe i will just get then X1650XT 512MB, that can't be that pricey.

---

### Post by cascade9 on 2010-06-27
> **filip007 said:**
> So best driver is still just for R600 aka Radeon X1950, this GPU is still give a big kick, family system has X1950XT model and still play most of the games on W7.

Maybe i will just get then X1650XT 512MB, that can't be that pricey.

R4XX = Radeon x700 to x1250
R5XX = x1300 to  x1950 
R6XX = Radeon HD cards (2XXX to 3XXX)
R7XX = Radeon HD 4XXX

Why would you get a x1650xt? Even if you can still find one, they are outclassed by the newer cards (nVidia and ATI) some of which wil be cheaper from what I've seen over the years. Even if you do want an ATI instead of nVidia (which really is easier at this point in time, though that could change pretty soon), the R600 cards currently have ATI support and work with the open soruce drivers.

---

### Post by filip007 on 2010-06-27
R500 is the X1950 series OK that's my mistake...

I currently run G31 from board and it just fine for 3D effects on desktop, but when i try some Nexuiz for longer time it makes my display beige colors on top of screen then i need to cool down the get normal display back but still runs all 3D just fine.

Radeon HD 2600 Pro or maybe 3650 they are all the same price on used market so...

Geforce don't offer any quality at the bottom, that's just America, if want quality for reasonable price than you go with Radeon simple as that and have open the open source support so...

And nNidia you don't need to build better cheap cards if i say so, that's for tracking morans for my user name, social stuff is getting power this days.

---

### Post by gradinaruvasile on 2010-06-27
> **filip007 said:**
> Thank you...both

Yes i was asking the same thing on Phoronix but they did not know that Radeon 3D desktop effects works directly from CD/DVD when boot and they offer me a Geforce, so much about help on Phoronix.

So best driver is still just for R600 aka Radeon X1950, this GPU is still give a big kick, family system has X1950XT model and still play most of the games on W7.

Maybe i will just get then X1650XT 512MB, that can't be that pricey.

Ati open source drivers are lagging badly behind their proprietary drivers (which support only series 2xxx and newer). I do test the OSS drivers on an older Ati 9000 card (Debian Squeeze), but they dont fare well. The card is older so it *should* have better support than the newer ones. But the driver changes and changes but it is not yet good for opengl applications and sometimes crashes the x server.
Bottom line-the driver has rough edges, but it has them for years and frankly i dont see when it will support all of the card's features because if it cant do it on older cards, it will never be ready on newer ones.
We did use x1600 and x1300 cards in our office for work (Ubuntu 8.04-Ubuntu 9.04) but they were unstable - we replaced them with nvidias and since then we had 0 x server crashes. And before Ati dropped the support for sub-2xxx cards, we used their proprietary drivers and those were unstable too (and as far as i read, they are not changed much in this regard).

If you want to have the driver support that equals that of Window's get an nvidia card. I use nvidia cards in my computers and had no problems - everything works, 3d included by just installing the latest driver from nvidia's web page (also HD movies play with 5-10% CPU usage on VDPAU capable cards).
Stability is the best you can find for a video card under Linux.

---

### Post by filip007 on 2010-06-27
I just want to run with less work the possible that save a lot of time on long run, or i will just upgrade to new Intel IGP system when that times comes.

---

