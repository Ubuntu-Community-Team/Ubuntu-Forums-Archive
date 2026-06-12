---
title: "Ricoh card reader not working"
date: 2010-08-03
forum: General Help
---

### Post by Punkristo on 2010-08-03
I have a HP Pavilion dv6629us with a Ricoh card reader. When I insert a card (Memory Stick Duo) nothing happens. Anybody knows how to make this work?

---

### Post by little_penguin on 2010-08-08
Is the card definitely compatible with the reader? I ask because I just checked the technical data for your laptop and it said:

5-in-1 integrated Digital Media Reader for Secure Digital cards,  MultiMedia cards, Memory Stick, Memory Stick Pro, or xD Picture cards

Memory stick duo isn't listed - unless it's the same as Memory stick pro? Have you read the card in the reader before (i.e. before you switched to Ubuntu)?

---

### Post by Punkristo on 2010-08-08
> **little_penguin said:**
> Is the card definitely compatible with the reader? I ask because I just checked the technical data for your laptop and it said:

5-in-1 integrated Digital Media Reader for Secure Digital cards,  MultiMedia cards, Memory Stick, Memory Stick Pro, or xD Picture cards

Memory stick duo isn't listed - unless it's the same as Memory stick pro? Have you read the card in the reader before (i.e. before you switched to Ubuntu)?

I have an adapter that makes it into a Memory Stick Pro, sorry for not explaining.

---

### Post by little_penguin on 2010-08-08
Have you seen this thread:

[http://ubuntuforums.org/showthread.php?t=797031](http://ubuntuforums.org/showthread.php?t=797031)

Some people, but not all, have reported success - could be worth trying.

---

### Post by Punkristo on 2010-08-08
That is for a PCI card reader and I have a Ricoh card reader.

---

### Post by little_penguin on 2010-08-08
Oops I assumed PCI just referred to its interface as opposed to model name, but thought I saw Ricoh mentioned somewhere. I got it mixed up with another thread I think. Anyway, found this thread and it explicitly mentions the Ricoh reader:

[http://ubuntuforums.org/archive/index.php/t-1152076.html](http://ubuntuforums.org/archive/index.php/t-1152076.html)

If that doesn't work, could you post the output of the following command:

```
lspci
```

I am assuming here that you are using the laptop's built-in reader? Or are you connecting an external memory card reader via usb? In that case, please post the output of this command:

```
lsusb
```

---

### Post by Punkristo on 2010-08-08
This is what I get

> 00:00.0 RAM memory: nVidia Corporation MCP67 Memory Controller (rev a2)
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
02:05.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 12)
02:05.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
02:05.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev ff)
03:00.0 Network controller: Broadcom Corporation BCM4311 802.11b/g WLAN (rev 02)


---

### Post by little_penguin on 2010-08-08
Ok, so the Ricoh card reader uses chipset R5C822:

02:05.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)

I've trawled the Internet for threads, and it seems that in linux, SD cards mostly work okay with this model of reader but there is no support for Memory Sticks (yet).

Your best bet is to add to or track the following bug report on Launchpad, to raise awareness of the issue.
And hopefully a developer might be able to help you further.

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/238208](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/238208)

Failing that, you might be better off just buying a compatible external card reader (USB) and have done with it. They don't cost all that much. I'll keep my fingers crossed anyway.

---

### Post by Punkristo on 2010-08-08
Thanks I will check it out.

---

