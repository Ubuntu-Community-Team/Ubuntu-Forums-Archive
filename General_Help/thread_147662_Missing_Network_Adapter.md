---
title: "Missing Network Adapter"
date: 2006-03-20
forum: General Help
---

### Post by mortalfunk on 2006-03-20
Hi.
When I installed a fresh install of Ubuntu it showed both network adapters on install and asked for the default. I chose the one with the internet (eth1).

On boot though I can only find eth1 not eth0... In firestarter and other networking programs it just doesn't exist.

Here is the output of lspci: The USB Controller is a Bluetooth device but I'm assuming the Ethernet controller: Unknown decide is causing the problems?

0000:00:00.0 Host bridge: VIA Technologies, Inc. VT8378 [KM400/A] Chipset Host Bridge
0000:00:01.0 PCI bridge: VIA Technologies, Inc. VT8237 PCI Bridge
0000:00:05.0 Ethernet controller: Unknown device f52b:1400 (rev 11)
0000:00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
0000:00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
0000:00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
0000:00:10.3 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 82)
0000:00:11.0 ISA bridge: VIA Technologies, Inc. VT8235 ISA Bridge
0000:00:11.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
0000:00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 50)
0000:00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 74)
0000:01:00.0 VGA compatible controller: nVidia Corporation NV34 [GeForce FX 5500] (rev a1)


What can I do from here to get it working?

---

