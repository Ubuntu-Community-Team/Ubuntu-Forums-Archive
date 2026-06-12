---
title: "How to update drivers?"
date: 2010-03-30
forum: General Help
---

### Post by TheNerdAL on 2010-03-30
Okay, so I think I have an SiS Driver(I'm not sure though, how can I be sure?), which I heard is not supported for Desktop Effects which makes me mad! D: Anyways, I want to update the drivers, and I don't know how to do that. Thanks! :D

PS: If I update my drivers, does that make my computer run a bit better?

---

### Post by kokkus on 2010-03-30
have you tried System>admin>hardware drivers?
Should have hardware drivers for your gfx card.
If not, then you should check their website.

---

### Post by TheNerdAL on 2010-03-30
> **kokkus said:**
> have you tried System>admin>hardware drivers?
Should have hardware drivers for your gfx card.
If not, then you should check their website.
It says no proprietary drivers are in use of the system.

---

### Post by TheNerdAL on 2010-03-31
Anyone?

---

### Post by Vaphell on 2010-03-31
what's your hardware exactly? find out what the gfx chipset is

in terminal:
```
lspci
```
or
```
hwinfo --gfxcard
```

and google a bit (sis <model> linux)

---

### Post by TheNerdAL on 2010-03-31
> **Vaphell said:**
> what's your hardware exactly? find out what the gfx chipset is

in terminal:
```
lspci
```
or
```
hwinfo --gfxcard
```

and google a bit (sis <model> linux)

00:00.0 Host bridge: Silicon Integrated Systems [SiS] 760/M760 Host (rev 02)
00:01.0 PCI bridge: Silicon Integrated Systems [SiS] SG86C202
00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS964 [MuTIOL Media IO] (rev 36)
00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE] (rev 01)
00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] AC'97 Sound Controller (rev a0)
00:03.0 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.1 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.2 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.3 USB Controller: Silicon Integrated Systems [SiS] USB 2.0 Controller
00:04.0 Ethernet controller: Silicon Integrated Systems [SiS] SiS900 PCI Fast Ethernet (rev 90)
00:05.0 IDE interface: Silicon Integrated Systems [SiS] RAID bus controller 180 SATA/PATA  [SiS] (rev 01)
00:0a.0 Communication controller: Conexant Systems, Inc. Device 2702 (rev 01)
00:0b.0 FireWire (IEEE 1394): VIA Technologies, Inc. VT6306/7/8 [Fire II(M)] IEEE 1394 OHCI Controller (rev 80)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 661/741/760 PCI/AGP or 662/761Gx PCIE VGA Display Adapter

---

### Post by TheNerdAL on 2010-04-01
Yup.
Anyone?

---

### Post by Mark Phelps on 2010-04-01
Found the thread below in the video subforum:

[http://ubuntuforums.org/showthread.php?t=1353903&highlight=sis]("http://ubuntuforums.org/showthread.php?t=1353903&highlight=sis")

You should search there.  There may be others as well.

---

### Post by 3rdalbum on 2010-04-01
> **TheNerdAL said:**
> Okay, so I think I have an SiS Driver(I'm not sure though, how can I be sure?), which I heard is not supported for Desktop Effects which makes me mad! D: Anyways, I want to update the drivers, and I don't know how to do that. Thanks! :D

PS: If I update my drivers, does that make my computer run a bit better?

3D and Compiz have never been supported on the SiS drivers; so if there is a later version of the driver, it won't help you.

You would need the "build-essential", "linux-headers-generic" and "xorg-dev" packages, and the source code for the SiS driver. You'd probably need to check out the latest version from their version control system (SVN, git, BZR, CVS, whatever sort of version control system they use from their code). And then you'd need to compile it.

If this is a desktop system, then you should just buy a new graphics card. Check whether your system uses AGP or PCI-E; if it uses PCI-E then you can buy one of today's lower-end Nvidia graphics cards, if it uses AGP then you'll need to buy an ATI-based AGP graphics card - PowerColor makes them.

---

### Post by Calash on 2010-04-01
[http://www.sis.com/download/](http://www.sis.com/download/)

I do not see the card you have listed there, but it may be part of the family.  They appear to only have Redhat installers for the updated drivers.  I believe you will need an application called "alien" to make them into a .deb format.

Be careful when playing with drivers outside of the package manager, especially ones that do some compiling when you install.  They tend to break when you get a kernel update, requires some knowledge of the command line to get them working again.  Nvidia is known for this, but I imagine others do it as well.  It is not difficult to work around as long as you are prepared before the updates.

---

### Post by TheNerdAL on 2010-04-01
> **Calash said:**
> [http://www.sis.com/download/](http://www.sis.com/download/)

I do not see the card you have listed there, but it may be part of the family.  They appear to only have Redhat installers for the updated drivers.  I believe you will need an application called "alien" to make them into a .deb format.

Be careful when playing with drivers outside of the package manager, especially ones that do some compiling when you install.  They tend to break when you get a kernel update, requires some knowledge of the command line to get them working again.  Nvidia is known for this, but I imagine others do it as well.  It is not difficult to work around as long as you are prepared before the updates.

I decided to install a new video card. But it would help if anyone had a step by step direction to update SiS from what you said. I'm sort of still a newb. :P

---

### Post by NCLI on 2010-04-01
SiS is notorious for doing as little as possible to support Linux, so there really isn't much point in us helping anyone upgrade their drivers when they suck anyway.

---

### Post by TheNerdAL on 2010-04-01
> **NCLI said:**
> SiS is notorious for doing as little as possible to support Linux, so there really isn't much point in us helping anyone upgrade their drivers when they suck anyway.

Lol, Good point. No Desktop Effects. D:

---

