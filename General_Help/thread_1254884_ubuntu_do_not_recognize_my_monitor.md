---
title: "ubuntu do not recognize my monitor"
date: 2009-08-31
forum: General Help
---

### Post by hotashes02 on 2009-08-31
my monitor is a Acer X183H

---

### Post by RedSingularity on 2009-08-31
Do you have a graphics driver installed?

---

### Post by hotashes02 on 2009-08-31
no 

i have a SiS graphic card

```
01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 661/741/760 PCI/AGP or 662/761Gx PCIE VGA Display Adapter
```

---

### Post by RedSingularity on 2009-08-31
What is your output of 

lspci

in the terminal?

---

### Post by hotashes02 on 2009-08-31
lspci

```

00:00.0 Host bridge: Silicon Integrated Systems [SiS] 760/M760 Host (rev 02)
00:01.0 PCI bridge: Silicon Integrated Systems [SiS] SG86C202
00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS964 [MuTIOL Media IO] (rev 36)
00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE] (rev 01)
00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] AC'97 Sound Controller (rev a0)
00:03.0 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.1 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.2 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.3 USB Controller: Silicon Integrated Systems [SiS] USB 2.0 Controller
00:04.0 Ethernet controller: Silicon Integrated Systems [SiS] SiS900 PCI Fast Ethernet (rev 90)
00:05.0 IDE interface: Silicon Integrated Systems [SiS] RAID bus controller 180 SATA/PATA  [SiS] (rev 01)
00:0a.0 Communication controller: Agere Systems V.92 56K WinModem (rev 03)
00:0b.0 FireWire (IEEE 1394): VIA Technologies, Inc. VT6306 Fire II IEEE 1394 OHCI Link Layer Controller (rev 80)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 661/741/760 PCI/AGP or 662/761Gx PCIE VGA Display Adapter
```

---

### Post by RedSingularity on 2009-08-31
I does not look like SIS provides a driver for the open source linux community to use.  As it looks now there is a minor problem detecting the screen with that on board card as linux has no drivers that support it fully.  Of course you can still adjust screen resolution and what not but as for the screen......i dont think there is much you can do about that.  I had the same problem with a onboard ATI card.  Once i upgraded to Nvidia and started using their drivers that problem corrected itself.  I wouldnt worry about it too much though as long as it doesnt effect your graphic environment.

---

### Post by Bölvaður on 2009-08-31
this probably will not help but what is the output of
```
glxinfo | grep vendor

```

also have you tried going to System &#8594; Administration &#8594; Hardware Drivers and see if something is there?

---

### Post by hotashes02 on 2009-08-31
[Shadow121]("http://ubuntuforums.org/member.php?u=677095") Thank a lot :P

---

### Post by RedSingularity on 2009-08-31
Oh one more thing.  Can i see your /etc/X11/xorg.conf  file?

---

### Post by hotashes02 on 2009-08-31
glxinfo | grep vendor
```
server glx vendor string: SGI
client glx vendor string: SGI
OpenGL vendor string: Mesa Project
```

no nothing in System &#8594; Administration &#8594; Hardware Drivers

---

### Post by hotashes02 on 2009-08-31
xorg.conf
```
Section "Device"
    Identifier    "Configured Video Device"
EndSection

Section "Monitor"
    Identifier    "Configured Monitor"
        Option          "DDC"      "false"
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
EndSection
```

---

### Post by RedSingularity on 2009-08-31
Try adding  under [U]Section "Device"

[/U]```
Section "Device"
    Identifier    "Configured Video Device"
    Driver        "sis"
EndSection

```

And reboot.

---

### Post by hotashes02 on 2009-08-31
when i restart the computer a window pop out it said ubuntu in low-graphic, everthing look so big and ubuntu still no recognize my monitor :([URL="http://ubuntuforums.org/showthread.php?p=7878640#post7878640"] 
[/URL]

---

### Post by SunnyRabbiera on 2009-08-31
> **hotashes02 said:**
> when i restart the computer a window pop out it said ubuntu in low-graphic, everthing look so big and ubuntu still no recognize my monitor :([URL="http://ubuntuforums.org/showthread.php?p=7878640#post7878640"] 
[/URL]

The issue might be your SIS card, more then the monitor.
I heard people have issues with SIS cards

---

### Post by RedSingularity on 2009-08-31
> **hotashes02 said:**
> when i restart the computer a window pop out it said ubuntu in low-graphic, everthing look so big and ubuntu still no recognize my monitor :([URL="http://ubuntuforums.org/showthread.php?p=7878640#post7878640"] 
[/URL]


Ah.  Did you have a problem fixing it or are you ok?

---

### Post by hotashes02 on 2009-08-31
> **SunnyRabbiera said:**
> The issue might be your SIS card, more then the monitor.
I heard people have issues with SIS cards
I can't active the visual effects extras now this, ubuntu keep desappointing me :(

---

### Post by hotashes02 on 2009-08-31
> **Shadow121 said:**
> Ah.  Did you have a problem fixing it or are you ok?
I erase the line that I add in the xorg.conf and restart the computer again and everything go back to normal

---

### Post by RedSingularity on 2009-08-31
> **hotashes02 said:**
> I can't active the visual effects extras now this, ubuntu keep desappointing me :(

I know.  Its a shame that many companies dont give linux developers the open source they require to utilize some hardware.  If you want effects you could always buy a cheap nvidia card.

> I erase the line that I add in the xorg.conf and restart the computer again and everything go back to normal

Ok good.  I didnt want to leave you with a busted system.

---

### Post by hotashes02 on 2009-09-01
> **Shadow121 said:**
> I know.  Its a shame that many companies dont give linux developers the open source they require to utilize some hardware.  If you want effects you could always buy a cheap nvidia card.



Ok good.  I didnt want to leave you with a busted system.

Thank for everything

---

