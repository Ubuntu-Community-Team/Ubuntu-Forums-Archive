---
title: "Help with nVidia Geforce 2 TI"
date: 2009-08-27
forum: General Help
---

### Post by ZettaGeek on 2009-08-27
Greetings, :)

I recently switched from Ubuntu 8.04 to Ubuntu 9.04. Everything is working well, except for the graphics. What was painless in 8.04 seems to be much more complex in 9.04.

To be a bit more descriptive, I can't figure out how to install graphics drivers for my nVidia Geforce 2 TI. I think my problem had been explained regarding Xorg changes in the release notes for 8.10 as mentioned here:
[http://www.ubuntu.com/getubuntu/releasenotes/810](http://www.ubuntu.com/getubuntu/releasenotes/810)

So here's my question: Has a work around been found, and if so would one be kind enough to explain to me the install process for this graphics card in Ubuntu 9.04?

Using VESA/NV is not an option since I need 3D for Blender. If their isn't a work around, where can I find drivers to down-grade back to Ubuntu 8.04 from Ubuntu 9.04 without having to burn another disc.

Thank you for your time, a fast response would be appreciated. :) :) :)

- ZettaGeek

---

### Post by bmorency on 2009-08-27
I re read the link and i'm not sure of a fix.

---

### Post by ZettaGeek on 2009-08-28
bump.

---

### Post by P4man on 2009-08-28
Im guessing your cpu doesnt support SSE ? If it does, you should be ok with the nvidia  binary driver. If it doesn't, you're basically screwed. What cpu do you have?

I suppose you could try the nouveau drivers:
[http://nouveau.freedesktop.org/wiki/FrontPage](http://nouveau.freedesktop.org/wiki/FrontPage)

However, those are still very experimental when it comes to 3D.

---

### Post by ZettaGeek on 2009-08-28
My processor is an AMD Sempron 2800+. I can get anywhere between 1.6GHz/2.8GHz if needed.

Everyone I have talked to has said I should purchase a new card. Is this one worth the money?

[http://www.amazon.com/gp/product/B001D72NE0/ref=s9_simz_gw_s0_p23_t1?pf_rd_m=ATVPDKIKX0DER&pf_rd_s=center-2&pf_rd_r=08NHYRN20EXEFMJS03C5&pf_rd_t=101&pf_rd_p=470938631&pf_rd_i=507846](http://www.amazon.com/gp/product/B001D72NE0/ref=s9_simz_gw_s0_p23_t1?pf_rd_m=ATVPDKIKX0DER&pf_rd_s=center-2&pf_rd_r=08NHYRN20EXEFMJS03C5&pf_rd_t=101&pf_rd_p=470938631&pf_rd_i=507846)

---

### Post by P4man on 2009-08-28
A sempron definately supports SSE. There should be no problem using the nvidia binary drivers. You videocard is old and very slow compared to modern cards, but if worked well enough, there is no point buying a new one.

lets try the nvidia drivers with your current card first. If you go to system > administration > hardware drivers, what do you get ? Doesn't it propose to download binary drivers?

---

### Post by ZettaGeek on 2009-08-28
> **P4man said:**
> A sempron definately supports SSE. There should be no problem using the nvidia binary drivers. You videocard is old and very slow compared to modern cards, but if worked well enough, there is no point buying a new one.

lets try the nvidia drivers with your current card first. If you go to system > administration > hardware drivers, what do you get ? Doesn't it propose to download binary drivers?

There is nothing listed under hardware drivers. It says "No Proprietary  Drivers in use on this system."

I tried to install the 71.xx.xx drivers via Synaptic AND the latest drivers from the nVidia website, and it always results in Ubuntu running in low graphics mode. Very annoying. As I said though, it seems as though the Xorg included with 9.04 does not support this card anymore.

---

### Post by P4man on 2009-08-28
nvidia site is confusing me. it suggests the 71 driver for a geforce 2 GTS, but  the 96 for an even older geforce 2MX.

Hmm.. did you try the 96.43.13 ? They are only 2 months old, I would be surprised if they didnt support the current version of x.org. I would be equally surprised they would support a  GF2MX, but not the GTS or Ti. Then again who knows.. :s

---

### Post by ZettaGeek on 2009-08-28
> **P4man said:**
> nvidia site is confusing me. it suggests the 71 driver for a geforce 2 GTS, but  the 96 for an even older geforce 2MX.

Hmm.. did you try the 96.43.13 ? They are only 2 months old, I would be surprised if they didnt support the current version of x.org. I would be equally surprised they would support a  GF2MX, but not the GTS or Ti. Then again who knows.. :s


I also tried 96.xx.xx.. Does not support the nVidia Geforce 2 TI. I thought the same thing, why support the older (and lower power) MX, yet not support the newer Geforce2 TI. :p

---

### Post by P4man on 2009-08-28
thats odd 
and sucks for you heh.
I guess you're right that the 71 driver doesnt support the new xorg

ive read some ppl downgrading their xorg on jaunty to run older videodrivers, but thats maybe not the best solution. Other than that, looks like you have the choice between buying a new videocard or sticking with hardy.

---

### Post by TrakerJon on 2009-08-28
ATI and Nvidia Drivers and Desktop Effects

The new Ubuntu 9.04 Jaunty Jackalope system comes with a Nouveau display graphic driver by default and the advanced effects cannot be used. If you've already tried to enable restricted Ubuntu drivers and ATI/nVidia cannot be found in the list try installing the ATI/nVidia driver with this tutorial:

1. Run Applications/Add/Remove
2. From the left menu choose System Tools
3. Next from the right menu, find and select for install: Desktop Effects (Compiz Setup) and ATI/Nvidia binary X.org Driver (nVidia could be version 173 or 177). Selecting the driver will get the list of supported graphics cards.
4. Click Apply Changes and after installation go to System/Administration/Hardware Drivers
5. The system will search for available drivers, choose the recommended option from the list and activate the driver by clicking Activate.
6. Restart your system and the new ATI/nVidia graphic display driver will be in use.

Unsupported updated versions of X.org drivers, libraries, etc. for Ubuntu [https://edge.launchpad.net/~ubuntu-x...hive/x-updates](https://edge.launchpad.net/~ubuntu-x...hive/x-updates)
Note: Import the key and add the repositories for your specific distribution in System > Administration > Software Sources then run sudo apt-get update from a terminal window.

---

### Post by P4man on 2009-08-28
TrakerJon, have you read anything in this thread lol?

---

### Post by ZettaGeek on 2009-08-28
None of that helps me. :/ I have a graphics card that isn't supported by the new Xorg. I can't believe there isn't a work around this. :p

nVidia, please release your drivers into the GPL..

---

