---
title: "A problem with the Intel chipset US15W"
date: 2012-10-07
forum: General Help
---

### Post by leopoldbirkholm on 2012-10-07
Hello fellow Ubuntuors,

I have a pickle with one laptop. It’s an Asus Eee PC 1201HA. Here is some specifications:
RAM: DDR2 SODIMM (2GB)
HDD: SATA 2.5" (250 GB)
CPU: Intel Atom Z520 single core low voltage ([http://ark.intel.com/products/35466](http://ark.intel.com/products/35466)) (and yeah, it’s slow)
Chipset: Intel US15W ([http://ark.intel.com/products/35444/Intel-SCH-US15W](http://ark.intel.com/products/35444/Intel-SCH-US15W))
Asus homepage for this model:
[http://www.asus.com/Eee/Eee_PC/Eee_PC_1201HA_Seashell/#specifications](http://www.asus.com/Eee/Eee_PC/Eee_PC_1201HA_Seashell/#specifications)
The GPU is integrated with the chipset.

The error:
I have a graphical issue. When booting I got one of two problems:
*A black screen. I know I have booted because I have seen the OEM picture of Asus at the boot and the little pling that prompts for the password
* Booting, seeing the OEM-picture and then the pling but only half a screen. The bottom half is the color the Joker in Batman likes. The color of Ubuntu for 12. It’s not red, not blue. Sorry, English is my second language. Anyhow, the top half is distorted and I can’t make heads or tail of it. I can log in as a guest, but then I can’t do any updates or installation. It will not either accepted “sudo” commands in Terminal.

I have googled it and found some promising leads.
* [http://ubuntuforums.org/showthread.php?t=1872768](http://ubuntuforums.org/showthread.php?t=1872768)
I have done the steps that the thread mentioned on the third input, I.E.
```
sudo add-apt-repository ppa:gma500/emgd 
sudo apt-get update
sudo apt-get install xorg-emgd emgd-dkms emgd-xorg-conf
sudo emgd-xorg-conf
```
I have done in recovery mode, hooked to Internet via Ethernet. Did not work.
* [http://ubuntuforums.org/showthread.php?t=1453445](http://ubuntuforums.org/showthread.php?t=1453445)
Not so much information about how to troubleshot the issue, more that the chipset is not so great.
* An article from ask.ubuntu but for the life of me, I can’t find it. That article mentioned that you should try to install N-Vidia drivers via recovery mode and as root. Allthough, the more I read about the problem, the less I belive it is relevant.

I will contiune reading in the forums about this chipset and the errors it’s causing for Ubuntu-user. My hope by posting my trouble is that someone have stumbled upon this chipset and found a guide on how to troubleshoot it and fix it.

So, please, please with some cookies on the side, does anyone know of this issue with the Intel US15W chipset?
Warm regards from the cold Sweden
Leopold
October 2012

---

### Post by mikewhatever on 2012-10-07
The problem with the US12W, aka Pouslbo, chipset is known well indeed. It's been used in many netboks, and to this day, Intel refuses to provide a working Linux driver. EMGD is the driver that doesn't work on 12.04, so no point installing it - the PPA has no packages for Precise anyway.

Please check out [the Poulsbo wiki]("https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsPoulsbo") for dealing with the graphics distortion.

---

### Post by leopoldbirkholm on 2012-10-08
> **mikewhatever said:**
> The problem with the US12W, aka Pouslbo, chipset is known well indeed. It's been used in many netboks, and to this day, Intel refuses to provide a working Linux driver. EMGD is the driver that doesn't work on 12.04, so no point installing it - the PPA has no packages for Precise anyway.

Please check out [the Poulsbo wiki]("https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsPoulsbo") for dealing with the graphics distortion.

Thank you. It is very interesting reading. I am now using [Jolicloud]("http://my.jolicloud.com/welcome") and it works nicely. But of course, I would love to have Ubuntu on the machine instead.

It's mentioning that it might be solved in the version 12.10. Fingers crossed. :-)

---

### Post by mikewhatever on 2012-10-08
The black screen/distortion problem should not affect 12.10, but that is actually an easy one. It may have looked scary when you've tried 12.04, but the workaround works (at least on the Dell Mini here), and is easy to apply. The big problem, that we do not have the driver that can fully utilize the GMA500 potential, will probably never be solved. For whatever odd reason, Intel is just not interested. 
Ubuntu 12.10 will not run well on gma500 netbooks anyway, with Unity2d gone, the interface will be just unusable.

---

### Post by leopoldbirkholm on 2012-10-17
Tomorrow is the date the Ubuntu 12.10 will be release (the 18:th of October). Then I can try if my cheap Asus will respond to Ubuntu. Weei!:guitar:

---

