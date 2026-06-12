---
title: "Wireless problem"
date: 2011-03-22
forum: General Help
---

### Post by sanilm on 2011-03-22
Hello,

sorry if I am posting in a wrong category. It's my first time here...

I just installed Ubuntu 10.04 on a my laptop with a built-in wireless card. I also installed drivers using "ndiswrapper", but I can't make the card work.
When I type "iwconfig" in the Terminal, I don't have the wlan0 listed. In the wireless network drivers, I see the driver I installed and it says: "Hardware present: Yes"

What should I do?

Thank you!

---

### Post by walt.smith1960 on 2011-03-22
Perhaps start by posting the output of the terminal command "lspci".

---

### Post by MARP1961 on 2011-03-22
Do you have a wireless on/off toggle switch? If you still have a Windows installation on your laptop have you checked whether wireless is switched on in Windows?

---

### Post by sanilm on 2011-03-22
This is the "lspci" output:
> 00:00.0 Host bridge: VIA Technologies, Inc. K8M890CE Host Bridge
00:00.1 Host bridge: VIA Technologies, Inc. K8M890CE Host Bridge
00:00.2 Host bridge: VIA Technologies, Inc. K8M890CE Host Bridge
00:00.3 Host bridge: VIA Technologies, Inc. K8M890CE Host Bridge
00:00.4 Host bridge: VIA Technologies, Inc. K8M890CE Host Bridge
00:00.5 PIC: VIA Technologies, Inc. K8M890CE I/O APIC Interrupt Controller
00:00.7 Host bridge: VIA Technologies, Inc. K8M890CE Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237 PCI bridge [K8T800/K8T890 South]
00:02.0 PCI bridge: VIA Technologies, Inc. K8T890 PCI to PCI Bridge Controller
00:03.0 PCI bridge: VIA Technologies, Inc. K8T890 PCI to PCI Bridge Controller
00:0f.0 IDE interface: VIA Technologies, Inc. VT8237A SATA 2-Port Controller (rev 80)
00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 07)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0)
00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0)
00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8237A PCI to ISA Bridge
00:11.7 Host bridge: VIA Technologies, Inc. VT8251 Ultra VLINK Controller
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 7c)
00:13.0 PCI bridge: VIA Technologies, Inc. VT8237A Host Bridge
00:13.1 PCI bridge: VIA Technologies, Inc. VT8237A PCI to PCI Bridge
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:00.0 VGA compatible controller: VIA Technologies, Inc. K8M890CE/K8N890CE [Chrome 9] (rev 01)
04:01.0 Audio device: VIA Technologies, Inc. VT1708/A [Azalia HDAC] (VIA High Definition Audio Controller) (rev 10)

Yes, my laptop is multi-boot. I have Windows XP and Ubuntu. It did not work on Windows neither: for some reason it did not find my wireless network. That's why I decided to try with ubuntu

---

### Post by walt.smith1960 on 2011-03-24
I don't see a wireless device listed.  
**00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 7c) **is your wired ethernet controller. I would expect to see something like "Network Controller" or a line referencing a manufacturer like Atheros, Broadcom, Intel, Ralink, RealTek or something like that. Your wireless device isn't a USB dongle, is it?  If so, it would show up with the command "lsusb".  Doesn't work in Windows either?  Could you go to Device Manager, look under networking and see what your wireless device is called?  I wonder if either you don't really have a wireless card or it's dead or disabled.

---

