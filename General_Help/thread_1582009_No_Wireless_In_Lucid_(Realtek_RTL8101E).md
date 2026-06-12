---
title: "No Wireless In Lucid (Realtek RTL8101E)"
date: 2010-09-25
forum: General Help
---

### Post by trstncmpbll on 2010-09-25
I put ubuntu on my sisters laptop and I cannot get the wireless working for the life of me. i have read every forum and post on the subjest but it just wont work. she has a realtek RTL8101E pci card and shes running ubuntu lucid. has anyone been able to make the driver work for it? pleases and thank yous

---

### Post by 666f6f on 2010-09-25
I believe the Realtek RTL8101E chipset corresponds to a wired network card. Can you post the ```
sudo lspci
``` output?

---

### Post by trstncmpbll on 2010-09-25
00:00.0 Host bridge: ATI Technologies Inc RS690 Host Bridge
00:01.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (Internal gfx)
00:05.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Port 1)
00:07.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Port 3)
00:12.0 SATA controller: ATI Technologies Inc SB600 Non-Raid-5 SATA
00:13.0 USB Controller: ATI Technologies Inc SB600 USB (OHCI0)
00:13.1 USB Controller: ATI Technologies Inc SB600 USB (OHCI1)
00:13.2 USB Controller: ATI Technologies Inc SB600 USB (OHCI2)
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
01:05.2 Audio device: ATI Technologies Inc Radeon X1200 Series Audio Controller
08:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 01)

---

### Post by 666f6f on 2010-09-25
I don't see a wireless adapter in your system. Are you using an external USB Wireless adapter? 

It is generally considered difficult to connect to a wireless network without a wireless adapter.

---

### Post by hrickh on 2010-09-25
It's an ongoing bug ([https://bugs.launchpad.net/ubuntu/+source/linux/+bug/534536](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/534536) - among other reports).

Your best bet is to install ndiswrapper and use the Windows driver (yeah, sucks to do that, but it works).

R.
==

---

### Post by 666f6f on 2010-09-25
> **hrickh said:**
> It's an ongoing bug ([https://bugs.launchpad.net/ubuntu/+source/linux/+bug/534536](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/534536) - among other reports).

Your best bet is to install ndiswrapper and use the Windows driver (yeah, sucks to do that, but it works).

R.
==

I still think that the main problem is the lack of a wireless adapter.. (+ the bug is not confirmed yet, maybe it is invalid)

---

### Post by trstncmpbll on 2010-09-25
> **hrickh said:**
> It's an ongoing bug ([https://bugs.launchpad.net/ubuntu/+source/linux/+bug/534536](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/534536) - among other reports).

Your best bet is to install ndiswrapper and use the Windows driver (yeah, sucks to do that, but it works).

R.
==

im new to ndiswrapper. so i went to realtek and downloaded the .zip driver for windows xp. how do i do it?

---

### Post by hrickh on 2010-09-26
> **trstncmpbll said:**
> im new to ndiswrapper. so i went to realtek and downloaded the .zip driver for windows xp. how do i do it?
Now that you have the Win driver, open Synaptic/Software Center and install "Windows Wireless Drivers".

Disable preinstalled Realtek drivers if they're installed by typing "sudo rmmod rtl8101" (I think that's the module name - I don't have that particular one on my system).

Install the Win drivers by unzipping the file you downloaded, then navigating to the unzipped folder. There should be a file called something like "Netrtuw.inf" in that folder. that's the file you're going to load.

Go to "System, Administration, Windows Wireless Drivers. Click "+ Install New Driver"
Drag the "Netrtuw.inf" file to where it says (none).

Click "Install".

It should then be installed and working.

I can't remember where I found these instructions, but I made a note of them and used them successfully to get my own Realtek 8187 driver working.

R.
==

---

