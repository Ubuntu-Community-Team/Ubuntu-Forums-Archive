---
title: "prevent overclocking"
date: 2010-04-29
forum: General Help
---

### Post by pqwoerituytrueiwoq on 2010-04-29
i am using the scaling applet to force the processors to the appropriate level (1Ghz each) but that is undone on every boot
[my PC]("http://reviews.cnet.com/laptops/hp-compaq-cq60-215dx/1707-3121_7-33496182.html")
```
00:00.0 RAM memory: nVidia Corporation MCP78S [GeForce 8200] Memory Controller (rev a2)
00:01.0 ISA bridge: nVidia Corporation Device 075e (rev a2)
00:01.1 SMBus: nVidia Corporation MCP78S [GeForce 8200] SMBus (rev a1)
00:01.3 Co-processor: nVidia Corporation MCP78S [GeForce 8200] Co-Processor (rev a2)
00:01.4 RAM memory: nVidia Corporation MCP78S [GeForce 8200] Memory Controller (rev a1)
00:02.0 USB Controller: nVidia Corporation MCP78S [GeForce 8200] OHCI USB 1.1 Controller (rev a1)
00:02.1 USB Controller: nVidia Corporation MCP78S [GeForce 8200] EHCI USB 2.0 Controller (rev a1)
00:04.0 USB Controller: nVidia Corporation MCP78S [GeForce 8200] OHCI USB 1.1 Controller (rev a1)
00:04.1 USB Controller: nVidia Corporation MCP78S [GeForce 8200] EHCI USB 2.0 Controller (rev a1)
00:06.0 IDE interface: nVidia Corporation MCP78S [GeForce 8200] IDE (rev a1)
00:07.0 Audio device: nVidia Corporation MCP72XE/MCP72P/MCP78U/MCP78S High Definition Audio (rev a1)
00:08.0 PCI bridge: nVidia Corporation MCP78S [GeForce 8200] PCI Bridge (rev a1)
00:09.0 IDE interface: nVidia Corporation MCP78S [GeForce 8200] SATA Controller (non-AHCI mode) (rev a2)
00:0a.0 Ethernet controller: nVidia Corporation MCP77 Ethernet (rev a2)
00:0b.0 PCI bridge: nVidia Corporation MCP78S [GeForce 8200] PCI Express Bridge (rev a1)
00:14.0 PCI bridge: nVidia Corporation MCP78S [GeForce 8200] PCI Bridge (rev a1)
00:18.0 Host bridge: Advanced Micro Devices [AMD] Mobile K10 [Turion X2, Athlon X2, Sempron] HyperTransport Configuration (rev 40)
00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 11h [Turion X2, Athlon X2, Sempron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] Mobile K10 [Turion X2, Athlon X2, Sempron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] Mobile K10 [Turion X2, Athlon X2, Sempron] Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] Mobile K10 [Turion X2, Athlon X2, Sempron] Link Control
02:00.0 VGA compatible controller: nVidia Corporation C77 [GeForce 8200M G] (rev a2)
07:00.0 Ethernet controller: Atheros Communications Inc. AR5001 Wireless Network Adapter (rev 01)

```running Ubuntu 10.04
more time is spent on grub than on booting the OS:lolflag:

---

### Post by pqwoerituytrueiwoq on 2010-04-30
did i forget to mention it wants to to sue my processors at 2 Ghz each?
[COLOR=white]Re-enable Sharks[/COLOR]

---

### Post by 3rdalbum on 2010-04-30
> **pqwoerituytrueiwoq said:**
> did i forget to mention it wants to to sue my processors at 2 Ghz each?

That's the native speed of your processor. Linux will scale the speed down when your system is not under load, and then scale it up to 2Ghz when it is.

If your CPU is staying at 2Ghz, then check System Monitor because it sounds like a program is running away with your CPU power. Kill whatever program is causing the high CPU use.

---

### Post by pqwoerituytrueiwoq on 2010-04-30
i am not so sure that is the native speed
only think i do that can cause it to go up are
booting
booting a virtual box
adobe flash
according to the specs on my system it is 2 ghz 
since it is dual core that would mean 1 ghz per core right?
[COLOR=white]Re-enable Sharks[/COLOR]

---

### Post by stoneage on 2010-04-30
No, both cores run at 2 GHz

---

### Post by pqwoerituytrueiwoq on 2010-04-30
> **stoneage said:**
> No, both cores run at 2 GHz
Awseome:guitar:

---

