---
title: "Ubuntu 64 bit and this graphics card?"
date: 2010-09-28
forum: General Help
---

### Post by altjx on 2010-09-28
How well does Ubuntu 64 bit work with 8GB of memory? Last time I tried to install on my laptop with 4GB of memory which was about 5-6 months ago, I had a lot of driver compatibility issue... I ask because I'm getting tired of all the lag issues with Windows...

Also, with this graphics card, I plan to play WoW. Anyone have any cards very similar and have real smooth gameplay?

XFX Radeon HD 4670 1GB PCIe w/Dual Link DVI

---

### Post by theozzlives on 2010-09-28
> **altjx said:**
> How well does Ubuntu 64 bit work with 8GB of memory? Last time I tried to install on my laptop with 4GB of memory which was about 5-6 months ago, I had a lot of driver compatibility issue... I ask because I'm getting tired of all the lag issues with Windows...

Also, with this graphics card, I plan to play WoW. Anyone have any cards very similar and have real smooth gameplay?

XFX Radeon HD 4670 1GB PCIe w/Dual Link DVI

The amount of memory on a system has nothing to do with driver compatibility. An ATI card is "ify" at best. Better to go nVidia.

---

### Post by altjx on 2010-09-28
> **theozzlives said:**
> The amount of memory on a graphics card has nothing to do with driver compatibility. An ATI card is "ify" at best. Better to go nVidia.

Yes, I know. I stated I had 8 GB because that's the only reason I'm going with Ubuntu 64-bit (which caused a lot of issues as opposed to when I had 32 bit). The graphics card question wasn't related to anything and is a separate question, sorry.

I already have this ATI card, not sure what to do =\

---

### Post by theozzlives on 2010-09-28
Try the live CD and see how it works out. If you can't take it back, ATI has some drivers for Ubuntu.

---

### Post by Glaucous on 2010-09-28
I'm using 8 GB RAM and XFX ATI HD4870, a quite similar setup although a quite more powerful graphics card. Linux seems to make use of 8 GB quite well (**cached** up to 99%). 

I don't think your 4670 will work very well with Wine and WoW though, my 4870 is handling it okay at best. NVIDIA seems to be recommended with Wine. 
I actually did some tests with my older NVIDIA 8600 GT (probably slighty worse than yours), which resulted in as good or better performance than my 4870.

Anyhow, try it out!

---

### Post by altjx on 2010-09-28
> **Glaucous said:**
> I'm using 8 GB RAM and XFX ATI HD4870, a quite similar setup although a quite more powerful graphics card. Linux seems to make use of 8 GB quite well (**cached** up to 99%). 

I don't think your 4670 will work very well with Wine and WoW though, my 4870 is handling it okay at best. NVIDIA seems to be recommended with Wine. 
I actually did some tests with my older NVIDIA 8600 GT (probably slighty worse than yours), which resulted in as good or better performance than my 4870.

Anyhow, try it out!

Thanks dude and above you. Going to boot up the live CD now. Forgot all about the damn thing.

---

### Post by coffeecat on 2010-09-28
The HD4200 in my laptop and HD4350 in my desktop work very well with the default open-source driver. I can get all the flashy compiz effects I want, but I don't know whether the acceleration would be enough for the games you play. Your HD4670 is different, of course, but it looks to be simply a more capable chipset than mine.

A quick search of this forum showed that some people get worse performance with the proprietary driver with the HD4670. That accords with my experience with the HD4200 in Karmic. The fglrx driver in Karmic with that card was appalling.

As an earlier  poster says, give the live CD a go. It will run on the open source driver and you might be able to tell if the driver is adequate for your needs.

---

