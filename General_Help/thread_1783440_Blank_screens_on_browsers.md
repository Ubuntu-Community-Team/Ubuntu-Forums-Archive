---
title: "Blank screens on browsers"
date: 2011-06-15
forum: General Help
---

### Post by joelstitch on 2011-06-15
Every time I try to upload an image to the forum or image shack or If I put VLC on fullscreen it doesn't work. When I click the browse button to look for the image I want to upload it opens the File Upload window but its completely white. I just upgraded to Ubuntu 11.04 and I have been noticing a lot of bugs.

---

### Post by DirtyPC on 2011-06-15
Video driver/ Codec issue maybe. run lspci to determine your graphics driver

---

### Post by joelstitch on 2011-06-15
> **harrylucas1 said:**
> Video driver/ Codec issue maybe. run lspci to determine your graphics driver

```
00:00.0 RAM memory: nVidia Corporation MCP67 Memory Controller (rev a2)
00:01.0 ISA bridge: nVidia Corporation MCP67 ISA Bridge (rev a2)
00:01.1 SMBus: nVidia Corporation MCP67 SMBus (rev a2)
00:01.2 RAM memory: nVidia Corporation MCP67 Memory Controller (rev a2)
00:01.3 Co-processor: nVidia Corporation MCP67 Co-processor (rev a2)
00:02.0 USB Controller: nVidia Corporation MCP67 OHCI USB 1.1 Controller (rev a2)
00:02.1 USB Controller: nVidia Corporation MCP67 EHCI USB 2.0 Controller (rev a2)
00:04.0 USB Controller: nVidia Corporation MCP67 OHCI USB 1.1 Controller (rev a2)
00:04.1 USB Controller: nVidia Corporation MCP67 EHCI USB 2.0 Controller (rev a2)
00:06.0 IDE interface: nVidia Corporation MCP67 IDE Controller (rev a1)
00:07.0 Audio device: nVidia Corporation MCP67 High Definition Audio (rev a1)
00:08.0 PCI bridge: nVidia Corporation MCP67 PCI Bridge (rev a2)
00:09.0 IDE interface: nVidia Corporation MCP67 AHCI Controller (rev a2)
00:0a.0 Ethernet controller: nVidia Corporation MCP67 Ethernet (rev a2)
00:0c.0 PCI bridge: nVidia Corporation MCP67 PCI Express Bridge (rev a2)
00:0d.0 PCI bridge: nVidia Corporation MCP67 PCI Express Bridge (rev a2)
00:12.0 VGA compatible controller: nVidia Corporation C67 [GeForce 7150M / nForce 630M] (rev a2)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
02:05.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
02:05.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
02:05.2 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
02:05.3 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 12)
03:00.0 Network controller: Broadcom Corporation BCM4311 802.11b/g WLAN (rev 02)

```

---

### Post by DirtyPC on 2011-06-15
You've got a bug: See here: [https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers/+bug/747717](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers/+bug/747717)

to disable compiz:  killall -9 compiz

---

### Post by joelstitch on 2011-06-15
Yeah i notice that awitching to Metacity fixes it. But how do I fix it if I want to keep using Compiz? I like Compiz a lot and want to keep using it.

---

### Post by wildmanne39 on 2011-06-16
Hi, I fixed mine while I was still beta testing it, it is the newer nvidia drivers just use the 173 in additional drivers for the 6100 series cards, I even have the cube and effects and all is great. If you installed drivers from third party go into synaptic and uninstall them other wise you will have two installed at the same time but it will only show one in additional drivers as active, also it will show driver not being use but that is a bug it really is being used if you activated it.

---

### Post by joelstitch on 2011-06-16
> **wildmanne39 said:**
> Hi, I fixed mine while I was still beta testing it, it is the newer nvidia drivers just use the 173 in additional drivers for the 6100 series cards, I even have the cube and effects and all is great. If you installed drivers from third party go into synaptic and uninstall them other wise you will have two installed at the same time but it will only show one in additional drivers as active, also it will show driver not being use but that is a bug it really is being used if you activated it.

So far it seems like that helped. Thanks a lot!

---

### Post by wildmanne39 on 2011-06-16
> **joelstitch said:**
> So far it seems like that helped. Thanks a lot!

Hi, your welcome, glad I could help.

---

