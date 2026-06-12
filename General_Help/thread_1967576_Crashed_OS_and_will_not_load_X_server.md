---
title: "Crashed OS and will not load X server"
date: 2012-04-28
forum: General Help
---

### Post by carverj on 2012-04-28
Hi Guys,
I am unable to start X. I get a screen stating: "Your screen, graphics card and input device could not be detected correctly. You need to configure yourself" 

So far I only found the error: failed to load module "nv" (module does not exist, 0). Also found a broken link named /etc/alternatives/xinput-lo_TH. 

Also: The directory "usr/share/fonts/X11/cyrillic" does not exist. Entry deleted from font path
      The directory "usr/share/fonts/X11/100dpi/" does not exist. Entry deleted from font path
      The directory "usr/share/fonts/X11/75dpi" does not exist. Entry deleted from font path
      The directory "usr/share/fonts/X11/100dpi" does not exist. Entry deleted from font path

Specs are 64bit Natty AMD Athlon:

```
ubuntu@ubuntu:~$ lscpu
Architecture:          i686
CPU(s):                1
Thread(s) per core:    1
Core(s) per socket:    1
CPU socket(s):         1
Vendor ID:             AuthenticAMD
CPU family:            15
Model:                 79
Stepping:              2
CPU MHz:               2411.912
Virtualization:        AMD-V
L1d cache:             64K
L1i cache:             64K
L2 cache:              512K
```

```
ubuntu@ubuntu:~$ lspci
00:00.0 RAM memory: nVidia Corporation MCP55 Memory Controller (rev a1)
00:01.0 ISA bridge: nVidia Corporation MCP55 LPC Bridge (rev a2)
00:01.1 SMBus: nVidia Corporation MCP55 SMBus (rev a2)
00:01.2 RAM memory: nVidia Corporation MCP55 Memory Controller (rev a2)
00:02.0 USB Controller: nVidia Corporation MCP55 USB Controller (rev a1)
00:02.1 USB Controller: nVidia Corporation MCP55 USB Controller (rev a2)
00:04.0 IDE interface: nVidia Corporation MCP55 IDE (rev a1)
00:05.0 IDE interface: nVidia Corporation MCP55 SATA Controller (rev a2)
00:05.1 IDE interface: nVidia Corporation MCP55 SATA Controller (rev a2)
00:05.2 IDE interface: nVidia Corporation MCP55 SATA Controller (rev a2)
00:06.0 PCI bridge: nVidia Corporation MCP55 PCI bridge (rev a2)
00:06.1 Audio device: nVidia Corporation MCP55 High Definition Audio (rev a2)
00:08.0 Bridge: nVidia Corporation MCP55 Ethernet (rev a2)
00:09.0 Bridge: nVidia Corporation MCP55 Ethernet (rev a2)
00:0a.0 PCI bridge: nVidia Corporation MCP55 PCI Express bridge (rev a2)
00:0b.0 PCI bridge: nVidia Corporation MCP55 PCI Express bridge (rev a2)
00:0c.0 PCI bridge: nVidia Corporation MCP55 PCI Express bridge (rev a2)
00:0d.0 PCI bridge: nVidia Corporation MCP55 PCI Express bridge (rev a2)
00:0e.0 PCI bridge: nVidia Corporation MCP55 PCI Express bridge (rev a2)
00:0f.0 PCI bridge: nVidia Corporation MCP55 PCI Express bridge (rev a2)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:04.0 FireWire (IEEE 1394): VIA Technologies, Inc. VT6306 Fire II IEEE 1394 OHCI Link Layer Controller (rev 80)
**02:00.0 VGA compatible controller: nVidia Corporation G98 [GeForce 8400 GS] (rev a1)**

```

Thanks brilliant and helpful forum folks

---

### Post by carverj on 2012-04-28
Fixed with:
```
sudo apt-get install ubuntu-desktop
```

---

