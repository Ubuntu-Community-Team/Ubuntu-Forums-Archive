---
title: "internet connection"
date: 2010-06-16
forum: General Help
---

### Post by jimmason on 2010-06-16
Hi guys very new to this, have installed ubuntu 10.4 on my laptop which is a sony vaio AR51E, but every time i log in i can't get a connection , i am connecting with a wireless router, the icon just keeps spinning round it finds my internet in the wireless connection drop down box but just does not connect, any ideas

---

### Post by cariboo on 2010-06-17
It would help if you let us know what wireless chipset your laptops uses. You can find out what the chipset is by opening an Applications->Accessories->Terminal and typing:

```
lspci
```

This will give you a listing of all your pci devices, it will look something like this:

```
lspci
00:00.0 RAM memory: nVidia Corporation MCP61 Memory Controller (rev a1)
00:01.0 ISA bridge: nVidia Corporation MCP61 LPC Bridge (rev a2)
00:01.1 SMBus: nVidia Corporation MCP61 SMBus (rev a2)
00:01.2 RAM memory: nVidia Corporation MCP61 Memory Controller (rev a2)
00:01.3 Co-processor: nVidia Corporation MCP61 SMU (rev a2)
00:02.0 USB Controller: nVidia Corporation MCP61 USB Controller (rev a3)
00:02.1 USB Controller: nVidia Corporation MCP61 USB Controller (rev a3)
00:04.0 PCI bridge: nVidia Corporation MCP61 PCI bridge (rev a1)
00:05.0 Audio device: nVidia Corporation MCP61 High Definition Audio (rev a2)
00:06.0 IDE interface: nVidia Corporation MCP61 IDE (rev a2)
00:07.0 Bridge: **nVidia Corporation MCP61 Ethernet** (rev a2)
00:08.0 IDE interface: nVidia Corporation MCP61 SATA Controller (rev a2)
00:09.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2)
00:0b.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2)
00:0c.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2)
00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor HyperTransport Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Link Control
02:00.0 VGA compatible controller: nVidia Corporation GT218 [GeForce 210] (rev a2)
02:00.1 Audio device: nVidia Corporation High Definition Audio Controller (rev a1)
```

Look for something like the section I've bolded above.

Please post back with the results.

---

### Post by jimmason on 2010-06-20
Sorry for delay have been on holiday will do as you say and post results back soon, many thanks

---

