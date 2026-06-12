---
title: "Motherboard swap"
date: 2011-01-16
forum: General Help
---

### Post by saur0 on 2011-01-16
Hi all, I have just swapped out the motherboard of a machine I am running Ubuntu on. Everything seems to have worked fine apart from the on board network card. 

I have installed an [ASUS A8N-E]("http://usa.asus.com/product.aspx?P_ID=DzbA8hgqchMBOVRz") and the website says the network card is a > nForce4 built-in   Gigabit/ MAC with external PHYI get the following from lspci 

> 00:00.0 Memory controller: nVidia Corporation CK804 Memory Controller (rev a3)
00:01.0 ISA bridge: nVidia Corporation CK804 ISA Bridge (rev a3)
00:01.1 SMBus: nVidia Corporation CK804 SMBus (rev a2)
00:02.0 USB Controller: nVidia Corporation CK804 USB Controller (rev a2)
00:02.1 USB Controller: nVidia Corporation CK804 USB Controller (rev a3)
00:04.0 Multimedia audio controller: nVidia Corporation CK804 AC'97 Audio Controller (rev a2)
00:06.0 IDE interface: nVidia Corporation CK804 IDE (rev f2)
00:07.0 IDE interface: nVidia Corporation CK804 Serial ATA Controller (rev f3)
00:08.0 IDE interface: nVidia Corporation CK804 Serial ATA Controller (rev f3)
00:09.0 PCI bridge: nVidia Corporation CK804 PCI Bridge (rev a2)
00:0a.0 Bridge: nVidia Corporation CK804 Ethernet Controller (rev a3)
00:0b.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
00:0c.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
00:0d.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
00:0e.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:00.0 VGA compatible controller: ATI Technologies Inc RV410 [Radeon X700 (PCIE)]
01:00.1 Display controller: ATI Technologies Inc RV410 [Radeon X700 (PCIE)] (Secondary)
05:07.0 RAID bus controller: Adaptec AAC-RAID (rev 01)
05:08.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8169 Gigabit Ethernet (rev 10)
How do I go about updating / changing the drivers ? I have had a look around and couldn't find anything that helped, I have also run an update. 

Any help or suggestions greatly appreciated.

---

### Post by fabricator4 on 2011-01-16
> **saur0 said:**
> nForce4 built-in Gigabit/ MAC with external PHY 

Any help or suggestions greatly appreciated.

While I'm far from expert at this, make sure that the Linux header file is the same version as the installed kernal.

```
System &#9656; Administration &#9656; Update Manager
```

You can find out the current kernel release by opening a terminal window and typing:

```
uname -r
```


Next, see if the system can find a proprietary driver available. First, make sure you have third party drivers enabled in the software sources:

```
 System &#9656; Administration &#9656; Software Sources
```

Then get the system to search for drivers:

```
 System &#9656; Administration &#9656; Hardware Drivers.
```.

Failing this you might have to search the board and/or the chip manufacturers site for some linux drivers, but hopefully it won't come to that.

Chris.

---

