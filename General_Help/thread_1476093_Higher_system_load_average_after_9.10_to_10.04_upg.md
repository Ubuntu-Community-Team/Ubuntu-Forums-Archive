---
title: "Higher system load average after 9.10 to 10.04 upgrade"
date: 2010-05-07
forum: General Help
---

### Post by Tamale on 2010-05-07
All,

A server of mine previously running ubuntu 9.10 used to be between 0.01 and 0.10 load average during the normal load of users using various server programs on it (mostly apache with php scripts).

Now, after upgrading to 10.04 (which went smoothly for the most part), the load average is much greater under the same user workload, hovering between 0.1 and 0.3 under very light work and up to and over 1 regularly when more users are accessing the same scripts.

Are there any known issues that would cause greater usage of the same resources in lucid, or are there any ways I can trace what's causing the higher load? Downgrading or starting with a fresh install are last resorts, as there are a lot of customized options specifically set up for this server and I'd rather not go through backing them all up and restoring them after a complete wipe.

Thanks in advance...

---

### Post by CryptoPaul on 2010-05-07
Noticed the same running i386 desktop:

[http://ubuntuforums.org/showthread.php?t=1461560](http://ubuntuforums.org/showthread.php?t=1461560)

At the time I was running from the liveCD. I now have it installed and there is no change, still noticeably higher load averages.

I'm surprised that there have not been more comments about it...


Paul

---

### Post by Tamale on 2010-05-07
Thanks for confirming.

Here is LSPCI output:


```
00:00.0 Host bridge: Advanced Micro Devices [AMD] AMD-8151 System Controller (rev 13)
00:01.0 PCI bridge: Advanced Micro Devices [AMD] AMD-8151 AGP Bridge (rev 13)
00:06.0 PCI bridge: Advanced Micro Devices [AMD] AMD-8111 PCI (rev 07)
00:07.0 ISA bridge: Advanced Micro Devices [AMD] AMD-8111 LPC (rev 05)
00:07.1 IDE interface: Advanced Micro Devices [AMD] AMD-8111 IDE (rev 03)
00:07.2 SMBus: Advanced Micro Devices [AMD] AMD-8111 SMBus 2.0 (rev 02)
00:07.3 Bridge: Advanced Micro Devices [AMD] AMD-8111 ACPI (rev 05)
00:07.5 Multimedia audio controller: Advanced Micro Devices [AMD] AMD-8111 AC97 Audio (rev 03)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
00:19.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:19.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:19.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:19.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:00.0 VGA compatible controller: nVidia Corporation NV34 [GeForce FX 5500] (rev a1)
02:00.0 USB Controller: Advanced Micro Devices [AMD] AMD-8111 USB OHCI (rev 0b)
02:00.1 USB Controller: Advanced Micro Devices [AMD] AMD-8111 USB OHCI (rev 0b)
02:03.0 Ethernet controller: Intel Corporation 82541GI Gigabit Ethernet Controller
02:04.0 RAID bus controller: 3ware Inc 7xxx/8xxx-series PATA/SATA-RAID (rev 01)
02:05.0 Mass storage controller: Silicon Image, Inc. SiI 3114 [SATALink/SATARaid] Serial ATA Controller (rev 02)
02:0a.0 FireWire (IEEE 1394): VIA Technologies, Inc. VT6306/7/8 [Fire II(M)] IEEE 1394 OHCI Controller (rev 80)
02:0b.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 61)
02:0b.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 61)
02:0b.2 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 63)

```

---

### Post by dolson on 2010-05-07
I have the exact same problem on two of my PCs, and possibly my netbook (didn't check this one, though).

One of them has a PCI NVIDIA GeForceFX, and the other has an AGP GeForceFX. Doesn't make a difference if I use the default driver or install one of the two official NVIDIA drivers...

I've fully updated everything. Here's my lspci from one of the systems - fresh install and update just today, if it helps at all:

```
00:00.0 Host bridge: Silicon Integrated Systems [SiS] 661FX/M661FX/M661MX Host (rev 11)
00:01.0 PCI bridge: Silicon Integrated Systems [SiS] SiS AGP Port (virtual PCI-to-PCI bridge)
00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS964 [MuTIOL Media IO] (rev 36)
00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE] (rev 01)
00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] AC'97 Sound Controller (rev a0)
00:03.0 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.1 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.2 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:04.0 Ethernet controller: Silicon Integrated Systems [SiS] SiS900 PCI Fast Ethernet (rev 91)
01:00.0 VGA compatible controller: nVidia Corporation NV34 [GeForce FX 5200] (rev a1)
```

This is worrisome.

---

### Post by Tamale on 2010-05-07
Agreed, it's extremely worrisome. I don't want to keep using ubuntu if it's going to start taxing my system more for unknown reasons. I need a fast and responsive server more than I need ubuntu :\

---

### Post by Tamale on 2010-05-11
this is starting to become a common complaint.. someone please help!

we're not talking small beans here.. most users including myself raising this complaint are noticing load average TEN TIMES higher than in any previous version of ubuntu under the same workloads.

[http://ubuntuforums.org/showthread.php?t=1471010](http://ubuntuforums.org/showthread.php?t=1471010)

---

