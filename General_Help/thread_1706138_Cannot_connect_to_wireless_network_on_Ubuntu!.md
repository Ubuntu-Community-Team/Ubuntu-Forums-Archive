---
title: "Cannot connect to wireless network on Ubuntu!"
date: 2011-03-13
forum: General Help
---

### Post by crob26 on 2011-03-13
Hello, first off, I am a newbie so please be patient and use step by step instructions, thanks.

So i am running Ubuntu off my USB on my dell PC, please note that i did not install ubuntu, i am just running it for now.

when on ubuntu, when i click on the network symbol with the red exclamation point on the top toolbar, it reads "Wireless Network: Device not ready (Firmware Missing)"

So i just want to know how to connect to my wireless network. Any help is appreciated, Thanks!

---

### Post by gyyug78fg87ogguiioioioioi on 2011-03-13
you cannot connect to wireless probably because you dont have the drivers installed probably.

write in terminal
```
lcpci
``` 
and find your "Network controller"s name and try to search for it on google or this forum and you will probably find some way how to install it

---

### Post by leviathan8 on 2011-03-13
Hook up an ethernet cable and launch 
```
jockey-gtk
```
then download the necessary wireless driver (if present). But I'd suggest you first install it since installing the wlan driver requires a reboot...

---

### Post by crob26 on 2011-03-15
> **gyyug78fg87ogguiioioioioi said:**
> write in terminal
```
lcpci
```and find your "Network controller"s name and try to search for it on google or this forum and you will probably find some way how to install it

this is what came up from "lspci"


00:00.0 RAM memory: nVidia Corporation MCP61 Memory Controller (rev a1)
00:01.0 ISA bridge: nVidia Corporation MCP61 LPC Bridge (rev a2)
00:01.1 SMBus: nVidia Corporation MCP61 SMBus (rev a2)
00:01.2 RAM memory: nVidia Corporation MCP61 Memory Controller (rev a2)
00:02.0 USB Controller: nVidia Corporation MCP61 USB Controller (rev a3)
00:02.1 USB Controller: nVidia Corporation MCP61 USB Controller (rev a3)
00:04.0 PCI bridge: nVidia Corporation MCP61 PCI bridge (rev a1)
00:05.0 Audio device: nVidia Corporation MCP61 High Definition Audio (rev a2)
00:06.0 IDE interface: nVidia Corporation MCP61 IDE (rev a2)
00:07.0 Bridge: nVidia Corporation MCP61 Ethernet (rev a2)
00:08.0 IDE interface: nVidia Corporation MCP61 SATA Controller (rev a2)
00:08.1 IDE interface: nVidia Corporation MCP61 SATA Controller (rev a2)
00:09.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2)
00:0b.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2)
00:0d.0 VGA compatible controller: nVidia Corporation C61 [GeForce 6150SE nForce 430] (rev a2)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:09.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)

---

