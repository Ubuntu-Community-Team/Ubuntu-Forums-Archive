---
title: "Sount stuttering"
date: 2010-09-04
forum: General Help
---

### Post by usagiakumu on 2010-09-04
MP3s stutter, flash stutters, anything with multimedia stutters and it is beginning to annoy the :popcorn: out of me.

usagi@usagi-desktop:~$ lspci
00:00.0 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
00:00.1 RAM memory: nVidia Corporation C51 Memory Controller 0 (rev a2)
00:00.2 RAM memory: nVidia Corporation C51 Memory Controller 1 (rev a2)
00:00.3 RAM memory: nVidia Corporation C51 Memory Controller 5 (rev a2)
00:00.4 RAM memory: nVidia Corporation C51 Memory Controller 4 (rev a2)
00:00.5 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
00:00.6 RAM memory: nVidia Corporation C51 Memory Controller 3 (rev a2)
00:00.7 RAM memory: nVidia Corporation C51 Memory Controller 2 (rev a2)
00:02.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:04.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:09.0 RAM memory: nVidia Corporation MCP51 Host Bridge (rev a2)
00:0a.0 ISA bridge: nVidia Corporation MCP51 LPC Bridge (rev a3)
00:0a.1 SMBus: nVidia Corporation MCP51 SMBus (rev a3)
00:0a.2 RAM memory: nVidia Corporation MCP51 Memory Controller 0 (rev a3)
00:0b.0 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
00:0b.1 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
00:0d.0 IDE interface: nVidia Corporation MCP51 IDE (rev a1)
00:0e.0 IDE interface: nVidia Corporation MCP51 Serial ATA Controller (rev a1)
00:0f.0 IDE interface: nVidia Corporation MCP51 Serial ATA Controller (rev a1)
00:10.0 PCI bridge: nVidia Corporation MCP51 PCI Bridge (rev a2)
00:10.1 Audio device: nVidia Corporation MCP51 High Definition Audio (rev a2)
00:14.0 Bridge: nVidia Corporation MCP51 Ethernet Controller (rev a3)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
02:00.0 VGA compatible controller: nVidia Corporation GT200 [GeForce GTX 260] (rev a1)
03:05.0 FireWire (IEEE 1394): Agere Systems FW322/323 (rev 70)
03:09.0 Ethernet controller: Atheros Communications Inc. AR2413 802.11bg NIC (rev 01)
usagi@usagi-desktop:~$ 

AMD Athalon x2 5000+
2 gig DDR2 533
Nvidia GTX 260 (using Closed Source drivers)
Atheros AR 2413 wifi
500G Sata II WD 
Ubuntu 10.04.1 AMD64

Same issues arise in 32 bit as well as I had 32 bit installed before this. Any help is appreciated. This is kind of going to force me back to Windows 7. The package arrived today with Office 2010 and Windows 7 Ultimate x64 today, just waiting on the 4 gig of ram. I might stick it out with Ubuntu if the issue is easily ironed out.

---

### Post by sandyd on 2010-09-04
> **usagiakumu said:**
> MP3s stutter, flash stutters, anything with multimedia stutters and it is beginning to annoy the :popcorn: out of me.

usagi@usagi-desktop:~$ lspci
00:00.0 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
00:00.1 RAM memory: nVidia Corporation C51 Memory Controller 0 (rev a2)
00:00.2 RAM memory: nVidia Corporation C51 Memory Controller 1 (rev a2)
00:00.3 RAM memory: nVidia Corporation C51 Memory Controller 5 (rev a2)
00:00.4 RAM memory: nVidia Corporation C51 Memory Controller 4 (rev a2)
00:00.5 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
00:00.6 RAM memory: nVidia Corporation C51 Memory Controller 3 (rev a2)
00:00.7 RAM memory: nVidia Corporation C51 Memory Controller 2 (rev a2)
00:02.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:04.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:09.0 RAM memory: nVidia Corporation MCP51 Host Bridge (rev a2)
00:0a.0 ISA bridge: nVidia Corporation MCP51 LPC Bridge (rev a3)
00:0a.1 SMBus: nVidia Corporation MCP51 SMBus (rev a3)
00:0a.2 RAM memory: nVidia Corporation MCP51 Memory Controller 0 (rev a3)
00:0b.0 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
00:0b.1 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
00:0d.0 IDE interface: nVidia Corporation MCP51 IDE (rev a1)
00:0e.0 IDE interface: nVidia Corporation MCP51 Serial ATA Controller (rev a1)
00:0f.0 IDE interface: nVidia Corporation MCP51 Serial ATA Controller (rev a1)
00:10.0 PCI bridge: nVidia Corporation MCP51 PCI Bridge (rev a2)
00:10.1 Audio device: nVidia Corporation MCP51 High Definition Audio (rev a2)
00:14.0 Bridge: nVidia Corporation MCP51 Ethernet Controller (rev a3)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
02:00.0 VGA compatible controller: nVidia Corporation GT200 [GeForce GTX 260] (rev a1)
03:05.0 FireWire (IEEE 1394): Agere Systems FW322/323 (rev 70)
03:09.0 Ethernet controller: Atheros Communications Inc. AR2413 802.11bg NIC (rev 01)
usagi@usagi-desktop:~$ 

AMD Athalon x2 5000+
2 gig DDR2 533
Nvidia GTX 260 (using Closed Source drivers)
Atheros AR 2413 wifi
500G Sata II WD 
Ubuntu 10.04.1 AMD64

Same issues arise in 32 bit as well as I had 32 bit installed before this. Any help is appreciated. This is kind of going to force me back to Windows 7. The package arrived today with Office 2010 and Windows 7 Ultimate x64 today, just waiting on the 4 gig of ram. I might stick it out with Ubuntu if the issue is easily ironed out.try installing pulseaudio

---

### Post by usagiakumu on 2010-09-04
I love you!!!
I can't believe that fixed it, and I also found a beautiful little walk-through for flash!
[http://www.webupd8.org/2009/07/speed-up-flash-and-firefox-in-ubuntu.html](http://www.webupd8.org/2009/07/speed-up-flash-and-firefox-in-ubuntu.html)

---

