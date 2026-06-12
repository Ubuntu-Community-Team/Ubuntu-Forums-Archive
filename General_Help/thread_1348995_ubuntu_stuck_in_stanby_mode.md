---
title: "ubuntu stuck in stanby mode"
date: 2009-12-07
forum: General Help
---

### Post by blue4paper on 2009-12-07
Whenever my laptop running ubuntu 9.10 goes into standby mode, I can never never get out no matter which keys I press, which forces me to shutdown the reboot the laptop.

Any suggestions would be appreciated.

thanks, 
blue

---

### Post by jbrown96 on 2009-12-07
Typically, there are three ways to get out of suspend (although some laptops might not support all three). 

1) There is a sensor on the lid. When the lid opens, the switch triggers and suspend exits.
2) Press the Fn key (usually bottom left of keyboard)
3) Power buttom. I'm guessing this doesn't work if you have to hard cycle it.

Or... Am I misunderstanding you? Will it go into sleep mode, then starts to come out (typically you can see the display backlight is on)?

If that's the case, then it is essential to know your hardware. run the following command in a terminal (applications-->accessories) ```
lspci
``` Just post that back here.

---

### Post by blue4paper on 2009-12-07
lspci output:

> 00:00.0 Host bridge: Silicon Integrated Systems [SiS] 661FX/M661FX/M661MX Host (rev 11)
00:01.0 PCI bridge: Silicon Integrated Systems [SiS] SiS AGP Port (virtual PCI-to-PCI bridge)
00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS963 [MuTIOL Media IO] (rev 25)
00:02.1 SMBus: Silicon Integrated Systems [SiS] SiS961/2 SMBus Controller
00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE]
00:02.6 Modem: Silicon Integrated Systems [SiS] AC'97 Modem Controller (rev a0)
00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] AC'97 Sound Controller (rev a0)
00:03.0 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.1 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.3 USB Controller: Silicon Integrated Systems [SiS] USB 2.0 Controller
00:04.0 Ethernet controller: Silicon Integrated Systems [SiS] SiS900 PCI Fast Ethernet (rev 91)
00:06.0 CardBus bridge: ENE Technology Inc CB1410 Cardbus Controller (rev 01)
00:0b.0 Ethernet controller: Atheros Communications Inc. AR2413 802.11bg NIC (rev 01)
01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 661/741/760 PCI/AGP or 662/761Gx PCIE VGA Display Adapter

I should've mentioned, but whenever it goes into "stanby" i can still click on everything. Only the screen goes black.

---

