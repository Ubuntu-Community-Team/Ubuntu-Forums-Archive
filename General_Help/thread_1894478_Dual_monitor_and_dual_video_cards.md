---
title: "Dual monitor and dual video cards"
date: 2011-12-12
forum: General Help
---

### Post by fetal on 2011-12-12
Hello,

I'm running Ubuntu 11.10 with Fluxbox. I've got two video cards with two monitors. However, when I run jockey-gtk I see several drivers, but only one is activated and currently in use. Shouldn't there be two? Also there doesn't seem to be a way for me to tell the difference between the drivers so I don't know which driver goes to which card. 

When I run xcompmgr one of my monitors/cards just hangs. I have to ctrl +c for it to become responsive.


Any ideas?

Thanks!

---

### Post by deonis on 2011-12-12
Why do you need two video cards? Do you have one in PCI and one in AGP? Why don't  you just use DVI cable to add your second monitor ?

---

### Post by fetal on 2011-12-12
One is onboard the other is pci. I'd prefer it, but it's not an option

---

### Post by fetal on 2011-12-16
Here is my lspci

 00:00.0 RAM memory: nVidia Corporation MCP61 Memory Controller (rev a1)
 00:01.0 ISA bridge: nVidia Corporation MCP61 LPC Bridge (rev a2)
 00:01.1 SMBus: nVidia Corporation MCP61 SMBus (rev a2)
 00:01.2 RAM memory: nVidia Corporation MCP61 Memory Controller (rev a2)
 00:02.0 USB Controller: nVidia Corporation MCP61 USB Controller (rev a2)
 00:02.1 USB Controller: nVidia Corporation MCP61 USB Controller (rev a2)
 00:04.0 PCI bridge: nVidia Corporation MCP61 PCI bridge (rev a1)
 00:05.0 Audio device: nVidia Corporation MCP61 High Definition Audio (rev a2)
 00:06.0 IDE interface: nVidia Corporation MCP61 IDE (rev a2)
 00:07.0 Bridge: nVidia Corporation MCP61 Ethernet (rev a2)
 00:08.0 IDE interface: nVidia Corporation MCP61 SATA Controller (rev a2)
 00:08.1 IDE interface: nVidia Corporation MCP61 SATA Controller (rev a2)
 00:09.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2)
 00:0d.0 VGA compatible controller: nVidia Corporation C61 [GeForce 6150SE nForce 430] (rev a2)
 00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
 00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
 00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
 00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
 01:06.0 Multimedia audio controller: Ensoniq ES1370 [AudioPCI]
 01:07.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8169 Gigabit Ethernet (rev 10)
 01:0e.0 FireWire (IEEE 1394): Texas Instruments TSB43AB23 IEEE-1394a-2000 Controller (PHY/Link)
 02:00.0 VGA compatible controller: nVidia Corporation NV44 [GeForce 6200 TurboCache(TM)] (rev a1)

---

