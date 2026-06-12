---
title: "How do I know which graphics card I am using?"
date: 2012-10-06
forum: General Help
---

### Post by MceraWV on 2012-10-06
Hey guys.  This is my first post in ubuntuforums so I hope you guys can help me out!
I too was curious about my graphics card.  I dont know what it is, but by the looks of it, it isn't a very good one:

mcerawv@McDesktop:~$ lspci -v
```
00:00.0 Host bridge: Silicon Integrated Systems [SiS] 661FX/M661FX/M661MX Host (rev 11)
    Subsystem: Foxconn International, Inc. Device 0c56
    Flags: bus master, medium devsel, latency 32
    Memory at e8000000 (32-bit, non-prefetchable) [size=64M]
    Capabilities: <access denied>
    Kernel driver in use: agpgart-sis
    Kernel modules: sis-agp

00:01.0 PCI bridge: Silicon Integrated Systems [SiS] SiS AGP Port (virtual PCI-to-PCI bridge) (prog-if 00 [Normal decode])
    Flags: bus master, 66MHz, fast devsel, latency 64
    Bus: primary=00, secondary=01, subordinate=01, sec-latency=32
    I/O behind bridge: 0000c000-0000cfff
    Memory behind bridge: ed000000-ed0fffff
    Prefetchable memory behind bridge: e0000000-e7ffffff
    Kernel modules: shpchp

00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS963 [MuTIOL Media IO] (rev 25)
    Flags: bus master, medium devsel, latency 0

00:02.1 SMBus: Silicon Integrated Systems [SiS] SiS961/2 SMBus Controller
    Flags: medium devsel
    I/O ports at 10c0 [size=32]
    Kernel driver in use: sis96x_smbus
    Kernel modules: i2c-sis96x

00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE] (prog-if 80 [Master])
    Subsystem: Foxconn International, Inc. Device 0c56
    Flags: bus master, medium devsel, latency 128, IRQ 16
    [virtual] Memory at 000001f0 (32-bit, non-prefetchable) [size=8]
    [virtual] Memory at 000003f0 (type 3, non-prefetchable) [size=1]
    [virtual] Memory at 00000170 (32-bit, non-prefetchable) [size=8]
    [virtual] Memory at 00000370 (type 3, non-prefetchable) [size=1]
    I/O ports at 4000 [size=16]
    Capabilities: <access denied>
    Kernel driver in use: pata_sis

00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] AC'97 Sound Controller (rev a0)
    Subsystem: Foxconn International, Inc. Device 0c56
    Flags: bus master, medium devsel, latency 32, IRQ 18
    I/O ports at d000 [size=256]
    I/O ports at d400 [size=128]
    Capabilities: <access denied>
    Kernel driver in use: Intel ICH
    Kernel modules: snd-intel8x0

00:03.0 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f) (prog-if 10 [OHCI])
    Subsystem: Foxconn International, Inc. Device 0c56
    Flags: bus master, medium devsel, latency 32, IRQ 20
    Memory at ed121000 (32-bit, non-prefetchable) [size=4K]
    Kernel driver in use: ohci_hcd

00:03.1 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f) (prog-if 10 [OHCI])
    Subsystem: Foxconn International, Inc. Device 0c56
    Flags: bus master, medium devsel, latency 32, IRQ 21
    Memory at ed122000 (32-bit, non-prefetchable) [size=4K]
    Kernel driver in use: ohci_hcd

00:03.3 USB Controller: Silicon Integrated Systems [SiS] USB 2.0 Controller (prog-if 20 [EHCI])
    Subsystem: Foxconn International, Inc. Device 7002
    Flags: bus master, medium devsel, latency 32, IRQ 23
    Memory at ed123000 (32-bit, non-prefetchable) [size=4K]
    Capabilities: <access denied>
    Kernel driver in use: ehci_hcd

00:04.0 Ethernet controller: Silicon Integrated Systems [SiS] SiS900 PCI Fast Ethernet (rev 91)
    Subsystem: Foxconn International, Inc. Device 0c56
    Flags: bus master, medium devsel, latency 32, IRQ 19
    I/O ports at d800 [size=256]
    Memory at ed120000 (32-bit, non-prefetchable) [size=4K]
    [virtual] Expansion ROM at 40000000 [disabled] [size=128K]
    Capabilities: <access denied>
    Kernel driver in use: sis900
    Kernel modules: sis900

00:08.0 Communication controller: Conexant Systems, Inc. HSF 56k HSFi Modem (rev 01)
    Subsystem: Mac System Co Ltd Device 8d8b
    Flags: bus master, medium devsel, latency 32, IRQ 3
    Memory at ed100000 (32-bit, non-prefetchable) [size=64K]
    I/O ports at dc00 [size=8]
    Capabilities: <access denied>

00:09.0 Ethernet controller: Atheros Communications Inc. Atheros AR5001X+ Wireless Network Adapter (rev 01)
    Subsystem: D-Link System Inc AirPlus DWL-G520 Wireless PCI Adapter (rev. A)
    Flags: bus master, medium devsel, latency 168, IRQ 18
    Memory at ed110000 (32-bit, non-prefetchable) [size=64K]
    Capabilities: <access denied>
    Kernel driver in use: ath5k
    Kernel modules: ath5k

00:0a.0 Multimedia audio controller: Creative Labs SB Live! EMU10k1 (rev 08)
    Subsystem: Creative Labs CT4780 SBLive! Value
    Flags: bus master, medium devsel, latency 32, IRQ 19
    I/O ports at e000 [size=32]
    Capabilities: <access denied>
    Kernel driver in use: EMU10K1_Audigy
    Kernel modules: snd-emu10k1

00:0a.1 Input device controller: Creative Labs SB Live! Game Port (rev 08)
    Subsystem: Creative Labs Gameport Joystick
    Flags: bus master, medium devsel, latency 32
    I/O ports at e400 [size=8]
    Capabilities: <access denied>
    Kernel driver in use: Emu10k1_gameport
    Kernel modules: emu10k1-gp

01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 661/741/760 PCI/AGP or 662/761Gx PCIE VGA Display Adapter (prog-if 00 [VGA controller])
    Subsystem: Foxconn International, Inc. Device 0c56
    Flags: 66MHz, medium devsel, IRQ 5
    BIST result: 00
    Memory at e0000000 (32-bit, prefetchable) [size=128M]
    Memory at ed000000 (32-bit, non-prefetchable) [size=128K]
    I/O ports at c000 [size=128]
    Expansion ROM at <unassigned> [disabled]
    Capabilities: <access denied>
    Kernel modules: sisfb

mcerawv@McDesktop:~$ 
```

Hope you guys can tell me what kind it is!
-Mc

PS; sorry for reviving a 4 year-old post.... didnt realize how old it was.....

---

### Post by howefield on 2012-10-06
Post moved to own thread.

---

### Post by jrog on 2012-10-06
> **MceraWV said:**
> 01:00.0 VGA compatible controller: **Silicon Integrated Systems [SiS] 661/741/760 PCI/AGP or 662/761Gx PCIE VGA Display Adapter** (prog-if 00 [VGA controller])
    Subsystem: Foxconn International, Inc. Device 0c56
    Flags: 66MHz, medium devsel, IRQ 5
    BIST result: 00
    Memory at e0000000 (32-bit, prefetchable) [size=128M]
    Memory at ed000000 (32-bit, non-prefetchable) [size=128K]
    I/O ports at c000 [size=128]
    Expansion ROM at <unassigned> [disabled]
    Capabilities: <access denied>
    Kernel modules: sisfb
That's your graphics card.

EDIT: Apparently the support for this type of card in Linux is not very good, BTW.

---

### Post by |{urse on 2012-10-06
lspci | grep "VGA"

---

### Post by gordintoronto on 2012-10-06
I found a 10-year-old Windows driver for that graphics adapter. The whole point of SiS graphics was to reduce cost, so your graphics adapter wasn't very good -- 10 years ago.

---

### Post by MceraWV on 2012-10-06
Thx howefield for making a new topic!
it makes sense the card is old because I built the computer from parts out of the 
Junkyard!  Really appreciate the help guys.

Thx a whole lot!
-Mc

EDIT:  Would this card be able to run minecraft?

---

