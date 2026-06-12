---
title: "wireless adapter problem"
date: 2010-02-16
forum: General Help
---

### Post by fermat06 on 2010-02-16
Hello, i am a new user of ubuntu. i installed ubuntu 9.10 yesterday. but i couldnt log in wireless internet while it was possible by cable. i couldnt install my wireless usb adapter driver. Here is some outputs:

ayhan@ayhan-desktop:~$ lspci
00:00.0 RAM memory: nVidia Corporation MCP55 Memory Controller (rev a1)
00:01.0 ISA bridge: nVidia Corporation MCP55 LPC Bridge (rev a2)
00:01.1 SMBus: nVidia Corporation MCP55 SMBus (rev a2)
00:02.0 USB Controller: nVidia Corporation MCP55 USB Controller (rev a1)
00:02.1 USB Controller: nVidia Corporation MCP55 USB Controller (rev a2)
00:04.0 IDE interface: nVidia Corporation MCP55 IDE (rev a1)
00:05.0 IDE interface: nVidia Corporation MCP55 SATA Controller (rev a2)
00:05.1 IDE interface: nVidia Corporation MCP55 SATA Controller (rev a2)
00:06.0 PCI bridge: nVidia Corporation MCP55 PCI bridge (rev a2)
00:06.1 Audio device: nVidia Corporation MCP55 High Definition Audio (rev a2)
00:08.0 Bridge: nVidia Corporation MCP55 Ethernet (rev a2)
00:0b.0 PCI bridge: nVidia Corporation MCP55 PCI Express bridge (rev a2)
00:0c.0 PCI bridge: nVidia Corporation MCP55 PCI Express bridge (rev a2)
00:0d.0 PCI bridge: nVidia Corporation MCP55 PCI Express bridge (rev a2)
00:0e.0 PCI bridge: nVidia Corporation MCP55 PCI Express bridge (rev a2)
00:0f.0 PCI bridge: nVidia Corporation MCP55 PCI Express bridge (rev a2)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
06:00.0 VGA compatible controller: nVidia Corporation G73 [GeForce 7600 GS] (rev a1)
ayhan@ayhan-desktop:~$ lspci | grep Ethernet
00:08.0 Bridge: nVidia Corporation MCP55 Ethernet (rev a2)
ayhan@ayhan-desktop:~$ lsusb
Bus 001 Device 002: ID 0586:3408 ZyXEL Communications Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
ayhan@ayhan-desktop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

ayhan@ayhan-desktop:~$ 

If someone could help me about that problem, i d be grateful. thank u.ayhan.

---

### Post by labinnsw on 2010-02-23
[A very good tutorial can be found here]("https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper")

---

