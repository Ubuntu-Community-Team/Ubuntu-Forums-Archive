---
title: "unity 2d with live usb . . . how?"
date: 2011-10-14
forum: General Help
---

### Post by cloyd on 2011-10-14
My old Gateway netbook is currently running on 10.04. It works well enough, but I really do like Unity. I've tried booting 11.10 with a live usb, but there are severe graphics issues which make it unusable. I've read of Unity 2d and wonder if the machine would run on it? I understand it is included in 11.10, but how do I get to it?  How do I access a menu which will let me access it with the live cd?  I really want to work with the live USB to make sure other things (like wireless) work before doing a full install.

---

### Post by cloyd on 2011-10-16
bump

---

### Post by gandaran on 2011-10-16
> **cloyd said:**
> My old Gateway netbook is currently running on 10.04. It works well enough, but I really do like Unity. I've tried booting 11.10 with a live usb, but there are severe graphics issues which make it unusable. I've read of Unity 2d and wonder if the machine would run on it? I understand it is included in 11.10, but how do I get to it?  How do I access a menu which will let me access it with the live cd?  I really want to work with the live USB to make sure other things (like wireless) work before doing a full install.
ubuntu should fall back to unity 2D automatically if the video card doesn't support 3D when installing.
I really don't know if from the live usb you can login on change sessions but if it's possible the option to choose unity 2D is in the login username tools button.
try posting the netbook specifications.

---

### Post by cloyd on 2011-10-17
Here is output of lspci.

lspci
00:00.0 Host bridge: ATI Technologies Inc RS690 Host Bridge
00:01.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (Internal gfx)
00:05.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Port 1)
00:06.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Port 2)
00:12.0 SATA controller: ATI Technologies Inc SB600 Non-Raid-5 SATA
00:13.0 USB Controller: ATI Technologies Inc SB600 USB (OHCI0)
00:13.1 USB Controller: ATI Technologies Inc SB600 USB (OHCI1)
00:13.3 USB Controller: ATI Technologies Inc SB600 USB (OHCI3)
00:13.4 USB Controller: ATI Technologies Inc SB600 USB (OHCI4)
00:13.5 USB Controller: ATI Technologies Inc SB600 USB Controller (EHCI)
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 14)
00:14.1 IDE interface: ATI Technologies Inc SB600 IDE
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
00:14.3 ISA bridge: ATI Technologies Inc SB600 PCI to LPC Bridge
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 VGA compatible controller: ATI Technologies Inc RS690M [Radeon X1200 Series]
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)
04:00.0 Network controller: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) (rev 01)

If another system command would give more information, I'll run it and post it. 

Here is the output of another command (I forgot what it was . . . ran it and and saved the output  . . . thought I'd need it in the future).

Machine is a Gateway LT3103u


  	 	 	 	p { margin-bottom: 0.08in; }  HID compliant mouse
 Synaptics PS/2 Port touchPad
 Generic PnP Monitor
 Atheros AR5B95 Wireless Network Adapter  9285
 Reltek PCIe FE Family Controller
 AMD Athlon(tm) Processor L110
 Realtgek High Definition Audio
 Microsoft iSCISI Initator
 

 


In booting with live usb, I get no login screen . . .

Thanks for the help

---

### Post by cloyd on 2011-10-18
bump

---

