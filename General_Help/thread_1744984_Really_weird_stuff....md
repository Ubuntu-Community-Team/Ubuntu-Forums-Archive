---
title: "Really weird stuff..."
date: 2011-04-30
forum: General Help
---

### Post by Areku The O.F. on 2011-04-30
Hello, name's Alex Steve, and I'm a proud Ubuntu user since Karmic.

Pumped up from the release of Natty, I noticed something weird since my days with Karmic. My PC asks for additional drivers (mainly video) but it works fine without them, in fact, I can use Compiz and enable 3D effects without installing the drivers (I installed them once in Maverick, and aside the Plymouth glitch my PC was performing really slow). I tried Natty via liveCD and Unity wasn't working, I decided to upgrade but again Unity wasn't working, I log off, and log back in classic mode and install the video drivers and voila, Unity starts working. Messing around with it I noticed that while it performs really good, when I open up Firefox the CPU goes trough the roof and everything breaks up. I tried Unity 2D but is kinda lacking compared to the real deal, and while I love Unity I had to come back to Maverick because my PC can't handle it. The question at hand? Why I can use Compiz on Maverick, Lucid and Karmic without the video drivers and not in Natty, and why the PC feels so heavy when I use them?

My specs:

500 GB SATA HDD - 250 Win7, 250 Maverick
2 GB DDR RAM / 4 GB Swap
512 MB ATI Radeon 2400HD Pro AGP
Intel Pentium 4 @ 2.80 GHz

Thanks, and sorry for the long post!

---

### Post by 3Miro on 2011-04-30
ATI has a history of bad drivers, more recent versions are mostly fine (ever since AMD took over, they have been improving greatly, but older cards are still lacking).

Unity uses new hardware features that are apparently not supported by the default FOSS driver. Note that Ubuntu Classic and Unity both use Compiz (Ubuntu Classic No Effects does not use Compiz), so the issue is with Unity specifically. You can try to install CCSM (compizconfig-settings-manager) and play with the settings, if you disable some of the effects, then Unity may work fine.

For Firefox, you may be having issues with Hardware acceleration. Try turning it on/off to see if this helps.

---

