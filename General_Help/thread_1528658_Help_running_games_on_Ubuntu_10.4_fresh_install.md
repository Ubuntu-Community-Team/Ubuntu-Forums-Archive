---
title: "Help running games on Ubuntu 10.4 fresh install"
date: 2010-07-11
forum: General Help
---

### Post by derision on 2010-07-11
Hello all, 
I recently got fed up with Windows and replaced it with this fine looking OS.
However, I'm having some difficulty playing the 3d open source games that should otherwise be compatible with Ubuntu.
For example, when I run Wolfenstein Enemy Territory, the screen simply turns black until I restart.
I am using an old Thinkpad T42 and my video card is an ATI Mobility Radeon 7500. 
I have downloaded so many programs and patches that I finally just gave up and reinstalled the OS.
Does anyone have any idea how I can make this simply work? It would kill me to have to go back to Windows - this OS otherwise seems awesome.
(I took a class to learn the basic nix commands, unfortunately they taught me nothing else)

Thanks,
der

---

### Post by derision on 2010-07-11
Can anyone suggest a driver package I can download from Synaptic or some simple way to be able to game from Ubuntu using my Thinkpad T42?

---

### Post by hawthornso23 on 2010-07-11
3-D games need 3-D support from your video card. The open source video drivers which are installed by default cannot yet make use of the full power of your card, although they are rapidly improving. To get full 3-D acceleration you need to install the proprietary drivers from ATI. Unfortunately these are not installable via repository. You have to go to ATI and follow the instructions. The good news however is that once you have installed proprietary video drivers with full 3-D acceleration, your 3-D games should run very well.

---

### Post by derision on 2010-07-11
Thank you, sir. You have been much help. I will go to their website and figure this out. What a relieving feeling it is to get away from the windows non-functional environment. Hopefully in the future I can contribute to this great community =)

der

Edit:
Dammit, there seems to be no driver for Ati Radeon 7500 and not a single forum post I found could in any way show me how to make it compatible to play 3d games. *sigh*

---

### Post by derision on 2010-07-12
Does anyone have any clue where or how I can make my T42 with the ATI Radeon Mobility 7500 play a simple 3d game? I don't know if I'm willing to sacrifice 3d game support for a nice OS.

---

### Post by techunit on 2010-07-12
Um your kind of out of luck until they fix those terrible graphics drivers!

---

### Post by derision on 2010-07-12
> **techunit said:**
> Um your kind of out of luck until they fix those terrible graphics drivers!
Well as long as I know that I'm doing something wrong, I guess I can live with it.
Say, you think I'd have better luck with the NVIDIA series?

---

### Post by hikaricore on 2010-07-12
Supported Nvidia cards work just fine with the proprietary driver.
Likewise supported ATI cards work fine as well.

---

### Post by derision on 2010-07-12
So is it safe to say that the newer ATI cards or NVIDIA for that matter work out of the box or without painful system reconfiguration?

---

### Post by hikaricore on 2010-07-12
I never said that, I just said that supported cards will work with the ati/nvidia proprietary drivers.
You'll need to check the nvidia and ati websites and see what cards are supported by each of the their linux drivers.

---

### Post by clhsharky on 2010-07-12
derision

Have you looked or searched for Wolfenstein Enemy Territory in

Gaming & Leisure
[http://ubuntuforums.org/forumdisplay.php?f=93](http://ubuntuforums.org/forumdisplay.php?f=93)

> Can anyone suggest a driver package I can download from Synaptic or some simple way to be able to game from Ubuntu using my Thinkpad T42?

Fresher OSS drivers including G3D(Gallium) for your card at this PPA
[https://edge.launchpad.net/~xorg-edgers/+archive/ppa](https://edge.launchpad.net/~xorg-edgers/+archive/ppa)
Read all

Sharky

---

