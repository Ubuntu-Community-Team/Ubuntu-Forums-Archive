---
title: "Sluggish and slow response"
date: 2012-05-24
forum: General Help
---

### Post by hiranyaroma on 2012-05-24
Hi,
I recently started using Ubuntu 12.04. My system specs are as follows.

Memory: 2 GB
Processor: Dual Core AMD Opteron(tm) Processor 180 × 2 
Graphics: VESA: MACH64GM
OS type: 32 bit
Disk: 250 GB

I have had a very sluggish experience using Ubuntu 12.04 (Like if I click on the minimize icon, the window takes about 2 seconds to minimize). Even videos which play well in smaller size, play stuck-stuck when I go full screen. Is it some hardware limitation or am I missing some graphics driver? Please suggest something.

---

### Post by kc1di on 2012-05-24
> **hiranyaroma said:**
> Hi,
I recently started using Ubuntu 12.04. My system specs are as follows.

Memory: 2 GB
Processor: Dual Core AMD Opteron(tm) Processor 180 × 2 
Graphics: VESA: MACH64GM
OS type: 32 bit
Disk: 250 GB

I have had a very sluggish experience using Ubuntu 12.04 (Like if I click on the minimize icon, the window takes about 2 seconds to minimize). Even videos which play well in smaller size, play stuck-stuck when I go full screen. Is it some hardware limitation or am I missing some graphics driver? Please suggest something.

I suspect it may be your video card.
What is it?

If you do not know please post the output of this command in a terminal:
```
lspci
```
l is lower case L

---

### Post by 2F4U on 2012-05-24
Seems to be an issue of the graphics card. Looks to me as if that could be an old ATI card? If I were you, I would try a desktop environment that doesn't have all that graphical eye candy that Unity comes with.

---

### Post by hiranyaroma on 2012-05-25
> **kc1di said:**
> I suspect it may be your video card.
What is it?

If you do not know please post the output of this command in a terminal:
```
lspci
```
l is lower case L
Here is the output of that command.

00:00.0 Memory controller: NVIDIA Corporation CK804 Memory Controller (rev a3)
00:01.0 ISA bridge: NVIDIA Corporation CK804 ISA Bridge (rev a3)
00:01.1 SMBus: NVIDIA Corporation CK804 SMBus (rev a2)
00:02.0 USB controller: NVIDIA Corporation CK804 USB Controller (rev a2)
00:02.1 USB controller: NVIDIA Corporation CK804 USB Controller (rev a3)
00:04.0 Multimedia audio controller: NVIDIA Corporation CK804 AC'97 Audio Controller (rev a2)
00:06.0 IDE interface: NVIDIA Corporation CK804 IDE (rev f2)
00:07.0 IDE interface: NVIDIA Corporation CK804 Serial ATA Controller (rev f3)
00:08.0 IDE interface: NVIDIA Corporation CK804 Serial ATA Controller (rev f3)
00:09.0 PCI bridge: NVIDIA Corporation CK804 PCI Bridge (rev a2)
00:0a.0 Bridge: NVIDIA Corporation CK804 Ethernet Controller (rev a3)
00:0b.0 PCI bridge: NVIDIA Corporation CK804 PCIE Bridge (rev a3)
00:0c.0 PCI bridge: NVIDIA Corporation CK804 PCIE Bridge (rev a3)
00:0d.0 PCI bridge: NVIDIA Corporation CK804 PCIE Bridge (rev a3)
00:0e.0 PCI bridge: NVIDIA Corporation CK804 PCIE Bridge (rev a3)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI Rage XL (rev 27)
01:06.0 FireWire (IEEE 1394): VIA Technologies, Inc. VT6306/7/8 [Fire II(M)] IEEE 1394 OHCI Controller (rev 80)

---

### Post by hiranyaroma on 2012-05-25
> **2F4U said:**
> Seems to be an issue of the graphics card. Looks to me as if that could be an old ATI card? If I were you, I would try a desktop environment that doesn't have all that graphical eye candy that Unity comes with.
Other desktop environment like? Ubuntu without unity? I chose Ubuntu because someone recommended me that its a smooth changeover from windows to ubuntu, and naturally I chose the latest version.

---

### Post by GreatDanton on 2012-05-25
It is smooth changeover, but only if you have good graphic card and enough memory. Otherwise the system is not running smooth. If you aren't happy with current system I would recommend you to install Xubuntu or Lubuntu, because they are lighter and less resource hungry (that means it will run much faster on the same computer :)

---

### Post by kc1di on 2012-05-25
Your video card is too old for good rendering of 3d in unity.
```
01:05.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI Rage XL (rev 27)
```

As others have recomended I would go with Lubuntu.  It should work well with that card Although your particular card has been known to cause problems with X in the past also. 

Another possibility is using the Mate desktop which is an updated gnome2 desktop.  that would be a little more complicated but if you want to try here's a page that will tell you how to do it :
good Luck.

[http://www.ubuntugeek.com/how-to-install-mate-desktop-environment-in-ubuntu-12-04precise11-10-oneiric.html]("http://www.ubuntugeek.com/how-to-install-mate-desktop-environment-in-ubuntu-12-04precise11-10-oneiric.html")

---

### Post by hiranyaroma on 2012-06-05
I switched to Lubuntu 12.04 and things seem great till now.

---

