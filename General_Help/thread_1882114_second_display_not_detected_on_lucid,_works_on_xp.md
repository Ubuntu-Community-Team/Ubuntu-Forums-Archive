---
title: "second display not detected on lucid, works on xp"
date: 2011-11-16
forum: General Help
---

### Post by |{urse on 2011-11-16
Title kind of says it all, sudo nvidia-settings shows only one connected monitor (though 2 are in fact connected, screen:1 via pci geforce fx5500, the other screen via onboard) I know that sometimes on asus boards the bios will disable one or the other but as I mentioned it works on the xp side. xrandr reports only one connected monitor also. Any ideas?

---

### Post by |{urse on 2011-11-16
I am using the proprietary nvidia driver.

---

### Post by |{urse on 2011-11-16
Or even if someone knows of a software like maxivista that gives you an extended desktop on a remote machine, that would be cool too. 

Let me clarify, not a virtual kvm software like synergy or xdmx. I need to be able to drag my text editor to the other screen so I can code on one screen and test on the other.

---

### Post by |{urse on 2011-11-27
One week bump.. anyone?

---

### Post by cwwilson721 on 2011-11-27
What, EXACTLY, is the 'onboard' videochip?

Not enough info to even hazard a guess.

(Use 'lspci' in a terminal to get the info)

---

### Post by |{urse on 2011-11-28
Not a problem, me and lspci are good friends.

> 00:00.0 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
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
03:05.0 FireWire (IEEE 1394): Agere Systems FW322/323 (rev 70)
03:09.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8185 IEEE 802.11a/b/g Wireless LAN Controller (rev 20)
03:0a.0 VGA compatible controller: nVidia Corporation NV34 [GeForce FX 5500] (rev a1)

---

