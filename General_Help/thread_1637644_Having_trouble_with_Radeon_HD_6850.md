---
title: "Having trouble with Radeon HD 6850"
date: 2010-12-04
forum: General Help
---

### Post by galion on 2010-12-04
Hi,
I've been having problems getting my Ubuntu to work with ATI Radeon 6850.
I've had Kubuntu for some time now, and it worked fine on my old card (nVidia 9400 GT). When I changed cards, the boot screen didn't display correctly, and after that I just got a black screen that wasn't responding to anything. I tried reinstalling the whole OS, but even the installation's GUI wouldn't load up.

Next I tired regular Ubuntu. The installation went fine, but the graphic settings were low, as you would expect from a system with no graphics driver. I installed the driver the system automatically suggests but after installing and rebooting I ran into the exact same problem I did with Kubuntu - black screen, no response.

I got the notion that this card isn't fully supported yet, but I read other posts saying people got much further with this card then I did. Is there another driver I should be installing?

---

### Post by wannacme16 on 2010-12-04
I use an ATI card as well under Ultimate Edition 2.6 32 bit. I run into a similar situation with one unique twist though. I use a TV as my monitor and I had to install the system with the ATI driver not installed, install was with NVIDIA card that came with my system. Only thing was after I installed the system under the NVIDIA card I couldn't adjust screen resolution above 1024x768 and my TV required 1320x768. Icons took up too much space. Solution was install under NVIDIA, update system, shutdown, unplug and install ATI card and hook up monitor to ATI card. After restart do not install any drivers for the ATI card, in my system advanced graphics was automically enabled by the card with no need to install drivers. However, prior to realizing the situation with the drivers I did install the drivers via synaptic and rebooted system only to find black screen. I shutdown the system, removed ATI card and hooked monitor back up to NVIDIA card, rebooted and uninstalled ATI drivers. Shutdown the system, unplugged the system, reinstalled the ATI card, re hooked monitor to ATI card and rebooted back into system as if nothing wrong with full advanced graphics (compiz fully functional-3d desktop). In your case boot into the system using factory installed card and remove ATI drivers, shutdown and install ATI card and reboot and do not install any drivers. Hopefully, this might help.

---

### Post by galion on 2010-12-05
Alright, no driver then.. Thanks, I'll try that.
Did you have the same problem with the boot screen, too? It displays in text only for me, no graphics.

---

### Post by satis on 2010-12-05
I have the same problem, I thought the ubuntu drivers weren't up to date, but after taking a small peak at the amd site, there simply aren't linux drivers that support the radeon HD6xxx series yet.

I only see text also (albeit very shortly as I boot from ssd), first the blank screen with only one _ blinking (same as on my stable laptop), afterwards text where my laptops shows those ugly progress dots. I guess that also has something to do with small changes necessary in the open source drivers.

Anyway, just be patient and take a look from time to time at the drivers on amd.com.

---

### Post by wannacme16 on 2010-12-05
Don't know about how exactly to deal with getting out of text log-ins but look up sudo gdm in the forums. Sorry, don't wanna tell you something I don't know myself. Oh yeah when you get gui straight see if you can enable compiz without installing any drivers, I did under ATI but couldn't under NVIDIA. Let me know and good luck.

---

### Post by SeePU on 2010-12-11
Do you guys still recommend HD 6850?  I think ATI takes too long to support Linux.   The only pro is open source drivers but you don't get all features.

In addition, you don't even have the open source driver option until much later.  I hope whoever is saying it's working is noting whether they're using VESA drivers.   I guess if you have the watermark, the Catalyst/FGLRX/binary blob driver is installed since there is some detection.  But, that's showing no real support.  

I'm only considering the ATI card because it's cheaper than the comparable Nvidia.  But, at least with Nvidia, you know it will work relatively quickly even if you don't have the open code... it will still work once you have it set up.

---

### Post by Nowaysis on 2011-01-16
I'm having more or less the same problem with a 6850 card. Though the problem only started after I bought a new monitor. Before that, the card was behaving fine, with no drivers installed of course.

I used to have an old NEC monitor running 1280x1024 native, which Ubuntu let me set just fine. After changing to a new Samsung SyncMaster BX2335 with full HD resolution however, the monitor settings won't let me set anything above 1024x768, and "detect monitors" does nothing. I even tried formatting the partition and reinstalling the OS.

I too have tried installing the suggested drivers, but that only makes the system crash, of course.

What I really don't understand is why I was allowed to set 1280x1024 on my old monitor, but nothing above 1024x768 on the new one.

---

