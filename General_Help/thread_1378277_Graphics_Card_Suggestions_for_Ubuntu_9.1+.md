---
title: "Graphics Card Suggestions for Ubuntu 9.1+"
date: 2010-01-11
forum: General Help
---

### Post by Hudson78 on 2010-01-11
I have a machine that I triple-boot into Ubuntu, XP and Vista. 

My graphics card (Radeon X1550 with the RV516 chipset) worked fine with Ubuntu 8.x, but Ubuntu 9.x has caused me nothing but pain.  I've decided to just get a better-supported more modern card.

Fortunately, the work I do on the machine is not graphically intensive so the new card does not need to be cutting edge.  The only real requirements are that it be affordable, fit into the PCI slot and be supported by Ubuntu 9.x and those other two OS's.

Can anyone suggest a suitable graphics card?

---

### Post by cascade9 on 2010-01-11
nVidia 8400GS or 9400GT

---

### Post by ratcheer on 2010-01-11
+1

I bought a Sparkle card from NewEgg for about $40. nVidia 9400GT with 1 GB memory. It works great with 9.10.

Tim

---

### Post by Hudson78 on 2010-01-11
Just to make sure --- these PCI Express cards will fit into my old-fashioned PCI slot?

---

### Post by cascade9 on 2010-01-11
Nope. PCI-E (express) needs a different slot. 

You will need a PCI version if you dont have a PCI-E (x8 or x16 slot).

---

### Post by Yellow Pasque on 2010-01-11
What is the problem you are having? The X1550 should work well if you don't need a lot of 3D performance.

---

### Post by Hudson78 on 2010-01-11
> **Temüjin said:**
> What is the problem you are having? The X1550 should work well if you don't need a lot of 3D performance.

It works fine in Ubuntu 8.0.4 with the proprietary ATI driver.

I don't need a lot of graphics performance -- GoogleEarth is the most intensive app I run probably. (That is a whole different problem.)

In 9.0.4 it works fine IF I revert Xorg to an older version and use the ATI driver.  If I use the open-source driver, I get artifacts.

In 9.1, the card is not even seen. (no device detected).

The chipset reported by my card (RV516) is not specifically listed on [the open-source Radeon driver page]("https://help.ubuntu.com/community/RadeonDriver").

I have gotten contradictory advice about it.  One person says it's working fine for them, another says it's just not supported by the version of Xorg included in Ubuntu 9.x.  

Last year, I wrestled with it for about a week and finally just gave up and reverted to Ubunu 8.x.

I would love to get it working if possible.

---

### Post by Hudson78 on 2010-01-11
> **cascade9 said:**
> Nope. PCI-E (express) needs a different slot. 

You will need a PCI version if you dont have a PCI-E (x8 or x16 slot).

Ah, good. 

It looks like there are PCI versions available for both the [8400GS]("http://www.amazon.com/EVGA-512-P1-N724-LR-GeForce-512MB-Graphics/dp/B001QMJ8Z4/ref=pd_cp_e_2") and the [9400GT]("http://www.amazon.com/EVGA-512-P1-N946-LR-GeForce-9400-Graphics/dp/B00261K0MY/ref=sr_1_11?ie=UTF8&s=electronics&qid=1263224335&sr=1-11").

Glad I asked. :D

---

### Post by ankspo71 on 2010-01-11
no problems here with an MSI branded Nvidia 8400 GS.

---

### Post by Yellow Pasque on 2010-01-11
> **Hudson78 said:**
> In 9.1, the card is not even seen. (no device detected).
Where do you see this message; in Xorg log or from lspci command?

> another says it's just not supported by the version of Xorg included in Ubuntu 9.x.
That person is probably referring to using it with the proprietary fglrx/Catalyst. The X1550 is basically a rebadged X1300. I'm 99% sure the X1550 works with the open-source radeon driver, and if not, it definitely is supported by the open-source 'radeonhd' driver: [http://cgit.freedesktop.org/xorg/driver/xf86-video-radeonhd/plain/README](http://cgit.freedesktop.org/xorg/driver/xf86-video-radeonhd/plain/README)

Before spending money on a new card, I would try the following:
1) Make sure proprietary driver is completely purged: [https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver](https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver)
2) Update to latest 2D driver and Mesa/3D driver using the xorg-edgers PPA: [https://launchpad.net/~xorg-edgers/+archive/ppa](https://launchpad.net/~xorg-edgers/+archive/ppa)
3) Try starting GEarth in terminal like:
```
vblank_mode=0 googleearth
```

GoogleEarth requires a bit of graphics horsepower.

---

### Post by Hudson78 on 2010-01-11
> **Temüjin said:**
> Where do you see this message; in Xorg log or from lspci command?

This is actually a dialog at bootup:
"Ubuntu is running in low-graphics mode
The following error was encountered. You may need to update your configuration to solve this.
(EE) No devices detected."

> **Temüjin said:**
> 
That person is probably referring to using it with the proprietary fglrx/Catalyst. The X1550 is basically a rebadged X1300. I'm 99% sure the X1550 works with the open-source radeon driver, and if not, it definitely is supported by the open-source 'radeonhd' driver: [http://cgit.freedesktop.org/xorg/driver/xf86-video-radeonhd/plain/README](http://cgit.freedesktop.org/xorg/driver/xf86-video-radeonhd/plain/README)

Under Ubuntu 9.x, I have not had any success with any Catalyst driver. (I've tried 9.2 and as far back as 8.12 I think.)

The open-source radeon driver is the one Ubuntu includes automatically, right?  It "works", but there are artifacts. For example, the mouse cursor shows a dark line beneath it.  The graphics are sluggish.

The cgit.freedesktop driver I don't think I ever heard of.  I'll try it.

> **Temüjin said:**
> 
Before spending money on a new card, I would try the following:
1) Make sure proprietary driver is completely purged: [https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver](https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver)
2) Update to latest 2D driver and Mesa/3D driver using the xorg-edgers PPA: [https://launchpad.net/~xorg-edgers/+archive/ppa](https://launchpad.net/~xorg-edgers/+archive/ppa)
3) Try starting GEarth in terminal like:
```
vblank_mode=0 googleearth
```


When "fighting" this, I have usually just nuked my Ubuntu partition and rebuilt it from a Ubuntu CD. So I'm sure the proprietary driver was purged in at least *some* of my troubleshooting.

> **Temüjin said:**
> 
GoogleEarth requires a bit of graphics horsepower.

Understood, thanks.

I'm perfectly willing to nuke it again and take a "start from scratch" approach if you think that's best.

---

### Post by nss0000 on 2010-01-13
> **Hudson78 said:**
> I have a machine that I triple-boot into Ubuntu, XP and Vista. 

My graphics card (Radeon X1550 with the RV516 chipset) worked fine with Ubuntu 8.x, but Ubuntu 9.x has caused me nothing but pain.  I've decided to just get a better-supported more modern card.

Fortunately, the work I do on the machine is not graphically intensive so the new card does not need to be cutting edge.  The only real requirements are that it be affordable, fit into the PCI slot and be supported by Ubuntu 9.x and those other two OS's.

Can anyone suggest a suitable graphics card?

Without issue I run the BFG_9800_gtx+ on UBUNTU_9.1. With AMD-965/MSI-gd70 kit I run in-the "40s" on Phoronix-Test-Suite TROPICS.  

Price ~ $130. It's a BIG vidcard and needs a full-tower case & 600+w power_supply.

---

