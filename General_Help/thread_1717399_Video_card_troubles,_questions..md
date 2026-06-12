---
title: "Video card troubles, questions."
date: 2011-03-29
forum: General Help
---

### Post by spemsy on 2011-03-29
Hi. I've been fooling around with Ubuntu for a while now, and I really want to make the switch from XP permanent, but I have a problem. My video card is the ATI Radeon X1950, which lacks drivers for newer versions of Ubuntu. It looks like I need to use Ubuntu 8.4 or lower to use this video card. I have a couple of questions:

1. I saw something about installing an older kernel and an older xorg while in Ubuntu 10.10 and being able to use the old 8.4 ATI driver. Is this at all possible?

2. What is the difference between Ubuntu 8.4 and Ubuntu 10.04/10.10? If I were to use 8.4 would I be missing out on a lot of awesome features?

Any responses are much appreciated.

---

### Post by 3Miro on 2011-03-29
This is not entirely the way you think it is. Under Linux there are two types of drivers: Free Open Source (FOSS) and proprietary (prop). FOSS drivers are under the control of Ubuntu and prop drivers are controlled by one corporation or another (AMD in your case).

ATI (or AMD) has decided to stop supporting your video card, Ubuntu has not.

Recently AMD released a lot of information to the Linux community so that good FOSS drivers can be made. My guess is that 10.10 would work fine with the FOSS drivers. You should download a liveCD with either 10.04 or 10.10 and then boot form it (select the option "try Ubuntu"). Things should work fine. You may have trouble running visual effects and in worst case suspend. Other than that, things should be working.

---

### Post by Krytarik on 2011-03-30
The driver built by using the information *3Miro* mentioned is actually the Open Source Edge Driver (OSED), built by the Xorg-Edgers. It is *not* installed by default. The default open source driver is much more basic, and although even those supports hardware acceleration, the OSED is much more advanced and should provide the highest possible performance.

Also see here: [https://launchpad.net/~xorg-edgers/+archive/ppa]("https://launchpad.net/%7Exorg-edgers/+archive/ppa")

To add the PPA and 'upgrade' to the OSED, run those commands:
```
sudo add-apt-repository ppa:xorg-edgers/ppa
sudo apt-get update
sudo apt-get upgrade
```Greetings.

---

