---
title: "Display color problem"
date: 2011-09-22
forum: General Help
---

### Post by Overweight on 2011-09-22
Greetings,

the past 2 hours I'm an ubuntu user and I'm having a problem with some colors on the display.
I installed ubuntu on an old laptop i have Clevo model: m3sw. I removed its hdd so i installed ubuntu on a 8Gb flash drive. I expiriecning problems with the colors I've added some attachment so you can see what I'm talking about. Are they any drivers I can install? Or any command i have to type to fix this?

Thank you in advance :)

---

### Post by Frogs Hair on 2011-09-22
Hello and Welcome

Drivers if available can be found in System > Administration > Additional Drivers .  Drivers may not be the problem because the Ubuntu installed driver should not cause the display to look this way . I know nothing about using Ubuntu without a hard-drive so you may have problems I can't help with .

The command below will display graphics card / controller  information .```
lspci
```

---

### Post by Overweight on 2011-09-22
This is what i got. Also nothing at additional drivers.

00:00.0 Host bridge: Silicon Integrated Systems [SiS] 661FX/M661FX/M661MX Host (rev 11)
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
00:0e.0 CardBus bridge: ENE Technology Inc CB1410 Cardbus Controller (rev 01)
01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 661/741/760 PCI/AGP or 662/761Gx PCIE VGA Display Adapter

---

### Post by Mark Phelps on 2011-09-22
Sorry to tell you this, but SiS chipsets are pretty old and generally poorly supported, if at all, in Linux distros.

A default open-source driver is installed by Ubuntu during setup and, as far as I know, that is the ONLY driver available anymore.

The only way to improve your display would be to replace the card with something newer.

Also, the Additional Drivers option is limited to AMD/ATI and Nvidia cards/chipsets in terms of video drivers -- and since yours is neither of these, it's not going to do anything for you.

---

### Post by Frogs Hair on 2011-09-22
The line below bothers me a bit because this is usually a reference to a hard-drive or storage device .
```
 00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE] 
```

---

### Post by Mark Phelps on 2011-09-22
That's because, in the "old" days, PC chipsets came from manufacturers other than Intel and AMD.  

There were VIA and SiS chipsets, to name a couple.

---

### Post by Overweight on 2011-09-22
I see, well thank  you all again for your reply's they where educating :)

---

