---
title: "Problems with Graphics Drivers"
date: 2010-06-06
forum: General Help
---

### Post by Mic[RSA] on 2010-06-06
Could someone please help us. My friend recently got Ubuntu for his laptop, very glad about it and all but he's having trouble getting it to run WoW. He uses wine but it throws an error, can not find display device or something in that line.
He went to System> Administrator >Hardware Drivers and there are no Nvidia display drivers listed (no drivers in fact). He has downloaded via Synaptic the Nvidia drivers but they still don't show. Could anyone help?

PS for some other reason it now also refuses to activate the extra visual effects, it had worked before. quite strange.

---

### Post by gradinaruvasile on 2010-06-06
You should be more specific about the problem.

What are exactly the packages that were installed?
Laptop model and video card model? Open a terminal, type "lspci", press enter. Copy-paste the output of the command here.

P.S. the "Hardware drivers" section is not always working as it should. And it shows the available proprietary drivers only.

---

### Post by wojox on 2010-06-06
Tell him to run:

```
sudo apt-get update; sudo apt-get upgrade
```

Then check.

---

### Post by pothvola3737 on 2010-06-06
Hm that is the point

His question is not clear....

Please specify your problem with detail then you will get the proper information.

If you dont do that then it will be hard for many people to solve this problem.:guitar::guitar::guitar:

---

### Post by Frikkie[RSA] on 2010-06-06
Hi. I'm the friend he's talking about.

My problem is that I don't think I've got any display drivers installed and therefore my WoW does not work through Wine. I went to the Synaptic Package Manager and downloaded and installed the nvidia-185-kernel-source, nvidia-173-dev and nvidia -96-dev. The last two packages are probably not needed?

When I go into WoW, I get an error message that says "Failed to find a suitable display device. Exiting program." (probably because the display drivers aren't installed?) and then quits.

My laptop specs are:

Model: HP Compaq nc6220
Memory: 994.4MB
CPU: Intel(R) Pentium(R) M processor 1.73GHz
Graphics: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 03)

When I type lscpi, this is what I get:

```
frikkie@frikkielaptop:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 2 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev d3)
00:1e.2 Multimedia audio controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 03)
00:1e.3 Modem: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Modem Controller (rev 03)
00:1f.0 ISA bridge: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 03)
02:04.0 Network controller: Intel Corporation PRO/Wireless 2915ABG [Calexico2] Network Connection (rev 05)
02:06.0 CardBus bridge: Texas Instruments PCIxx21/x515 Cardbus Controller
02:06.3 Mass storage controller: Texas Instruments PCIxx21 Integrated FlashMedia Controller
02:06.4 SD Host controller: Texas Instruments PCI6411/6421/6611/6621/7411/7421/7611/7621 Secure Digital Controller
02:06.5 Communication controller: Texas Instruments PCI6411/6421/6611/6621/7411/7421/7611/7621 Smart Card Controller
10:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5751M Gigabit Ethernet PCI Express (rev 11)

```

So I think one of my problems is that I don't know whether I should install ATI or Nvidia display drivers and whether they are installed because when I go to System>Administration>Hardware Drivers it says: "No proprietary drivers are in use on this system". But as you said the Hardware Drivers aren't so trustworthy, I will ignore this.

When I ran:

```
sudo apt-get update
```

it downloaded some stuff but when I ran 

```
sudo apt-get upgrade
```

I got this (don't know if it's a problem):

```
frikkie@frikkielaptop:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```

All help will be much appreciated.

---

### Post by IamMalkav on 2010-06-06
Your friend is using the Intel Pulsbo (the 915) chipset. This is not made by nVidia or ATI so don't go looking for drivers from them for that laptop. This chipset is notoriously given little support by Intel because they contracted it out to another company to produce. Good luck... your friend will need it to play WoW on that.

---

### Post by Frikkie[RSA] on 2010-06-06
Ok, I've found this handy [link]("http://www.happyassassin.net/2009/01/30/intel-gma-500-poulsbo-graphics-on-linux-a-precise-and-comprehensive-summary-as-to-why-youre-screwed/").

So basically I'm screwed and will never find decent display drivers for Linux for my display device and will never be able to play WoW on here? Or am I wrong (hopefully I am)?

I've found [this]("http://packages.debian.org/stable/xserver-xorg-video-intel"). It says it supports the i915 chip, but I've got the 915GM chip. Will it still work?

---

