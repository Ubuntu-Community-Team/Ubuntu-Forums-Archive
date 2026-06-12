---
title: "Input signal out of range!!!!"
date: 2010-11-07
forum: General Help
---

### Post by extremejosh on 2010-11-07
I have searched for some time for a solution to this problem but haven't found one yet.
on all my 3d games my monitor goes blank and outputs 
[B]Input signal out of range Change settings to 1366x768-60Hz
[/B]i have tried a couple fixes but so far nothing has helped. The only thing i can fix this on is games i run through wine by using a virtual desktop but it doesn't look the same as playing full screen so help would be appreciated

---

### Post by efflandt on 2010-11-07
If you want help, you might provide some information:

What is the native resolution of your monitor/TV and what video modes does it support?  For example does it support normal PC video modes like 640x480, 1024x768, 1280x1024?  If it says its native resolution is 1366x768, it will usually run 1360x768 or close to that (WinXP picked 1360x764 and 1360x765 seemed optimum in Linux).

What resolution is set in the games?  Do they run in a window vs. full screen or are they console games that do not run under X?  The name of games might help too.

What video card/chip do you have and are you running default or proprietary drivers.  The part of **sudo lspci -v** related to your video would help.  Highlight that and wrap it in code tags by clicking on **#** in message window.

---

### Post by extremejosh on 2010-11-07
> **efflandt said:**
> If you want help, you might provide some information:

What is the native resolution of your monitor/TV and what video modes does it support?  For example does it support normal PC video modes like 640x480, 1024x768, 1280x1024?  If it says its native resolution is 1366x768, it will usually run 1360x768 or close to that (WinXP picked 1360x764 and 1360x765 seemed optimum in Linux).

What resolution is set in the games?  Do they run in a window vs. full screen or are they console games that do not run under X?  The name of games might help too.

What video card/chip do you have and are you running default or proprietary drivers.  The part of **sudo lspci -v** related to your video would help.  Highlight that and wrap it in code tags by clicking on **#** in message window.
my native resolution is 1366x768 it supports all of the above you mentioned. i tried playing urban terror but it gave me input signal out of range message i installed diablo through wine and it does the same unless i config wine to run virtual desktop then i can play it but it doesn't look right so i installed and play a random game called blob and conquer and thats in window mode so it started playing but after a while i made it full screen and then i got the input signal out of range my video card is a geforce 7350 le  im using  proprietary drivers from the repository 
```
sudo lspci -v
[sudo] password for joshua: 
00:00.0 Host bridge: Intel Corporation 82945G/GZ/P/PL Memory Controller Hub (rev 02)
    Subsystem: Hewlett-Packard Company Device 2a50
    Flags: bus master, fast devsel, latency 0
    Capabilities: [e0] Vendor Specific Information: Len=09 <?>
    Kernel modules: intel-agp

00:01.0 PCI bridge: Intel Corporation 82945G/GZ/P/PL PCI Express Root Port (rev 02) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
    Memory behind bridge: fa000000-fcffffff
    Prefetchable memory behind bridge: 00000000d0000000-00000000dfffffff
    Capabilities: [88] Subsystem: Intel Corporation 82945G/GZ/P/PL PCI Express Root Port
    Capabilities: [80] Power Management version 2
    Capabilities: [90] MSI: Enable+ Count=1/1 Maskable- 64bit-
    Capabilities: [a0] Express Root Port (Slot+), MSI 00
    Capabilities: [100] Virtual Channel
    Capabilities: [140] Root Complex Link
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 01)
    Subsystem: Hewlett-Packard Company Device 2a50
    Flags: bus master, fast devsel, latency 0, IRQ 41
    Memory at fdff8000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: [50] Power Management version 2
    Capabilities: [60] MSI: Enable+ Count=1/1 Maskable- 64bit+
    Capabilities: [70] Express Root Complex Integrated Endpoint, MSI 00
    Capabilities: [100] Virtual Channel
    Capabilities: [130] Root Complex Link
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel

00:1d.0 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #1 (rev 01) (prog-if 00 [UHCI])
    Subsystem: Hewlett-Packard Company Device 2a50
    Flags: bus master, medium devsel, latency 0, IRQ 23
    I/O ports at ff00 [size=32]
    Kernel driver in use: uhci_hcd

00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 01) (prog-if 00 [UHCI])
    Subsystem: Hewlett-Packard Company Device 2a50
    Flags: bus master, medium devsel, latency 0, IRQ 19
    I/O ports at fe00 [size=32]
    Kernel driver in use: uhci_hcd

00:1d.2 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 01) (prog-if 00 [UHCI])
    Subsystem: Hewlett-Packard Company Device 2a50
    Flags: bus master, medium devsel, latency 0, IRQ 18
    I/O ports at fd00 [size=32]
    Kernel driver in use: uhci_hcd

00:1d.3 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 01) (prog-if 00 [UHCI])
    Subsystem: Hewlett-Packard Company Device 2a50
    Flags: bus master, medium devsel, latency 0, IRQ 16
    I/O ports at fc00 [size=32]
    Kernel driver in use: uhci_hcd

00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 01) (prog-if 20 [EHCI])
    Subsystem: Hewlett-Packard Company Device 2a50
    Flags: bus master, medium devsel, latency 0, IRQ 23
    Memory at fdfff000 (32-bit, non-prefetchable) [size=1K]
    Capabilities: [50] Power Management version 2
    Kernel driver in use: ehci_hcd

00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1) (prog-if 01 [Subtractive decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=02, subordinate=02, sec-latency=32
    I/O behind bridge: 0000e000-0000efff
    Memory behind bridge: e8000000-efffffff
    Capabilities: [50] Subsystem: Hewlett-Packard Company Device 2a50

00:1f.0 ISA bridge: Intel Corporation 82801GH (ICH7DH) LPC Interface Bridge (rev 01)
    Subsystem: Hewlett-Packard Company Device 2a50
    Flags: bus master, medium devsel, latency 0
    Capabilities: [e0] Vendor Specific Information: Len=0c <?>
    Kernel modules: leds-ss4200, iTCO_wdt

00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01) (prog-if 8a [Master SecP PriP])
    Subsystem: Hewlett-Packard Company Device 2a50
    Flags: bus master, medium devsel, latency 0, IRQ 18
    I/O ports at 01f0 [size=8]
    I/O ports at 03f4 [size=1]
    I/O ports at 0170 [size=8]
    I/O ports at 0374 [size=1]
    I/O ports at fb00 [size=16]
    Kernel driver in use: ata_piix

00:1f.2 IDE interface: Intel Corporation N10/ICH7 Family SATA IDE Controller (rev 01) (prog-if 8f [Master SecP SecO PriP PriO])
    Subsystem: Hewlett-Packard Company Device 2a50
    Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 19
    I/O ports at fa00 [size=8]
    I/O ports at f900 [size=4]
    I/O ports at f800 [size=8]
    I/O ports at f700 [size=4]
    I/O ports at f600 [size=16]
    Memory at fdffe000 (32-bit, non-prefetchable) [size=1K]
    Capabilities: [70] Power Management version 2
    Kernel driver in use: ata_piix

00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 01)
    Subsystem: Hewlett-Packard Company Device 2a50
    Flags: medium devsel, IRQ 11
    I/O ports at 0500 [size=32]
    Kernel modules: i2c-i801

01:00.0 VGA compatible controller: nVidia Corporation G72 [GeForce 7350 LE] (rev a1) (prog-if 00 [VGA controller])
    Subsystem: Micro-Star International Co., Ltd. Device 0563
    Flags: bus master, fast devsel, latency 0, IRQ 16
    Memory at fa000000 (32-bit, non-prefetchable) [size=16M]
    Memory at d0000000 (64-bit, prefetchable) [size=256M]
    Memory at fb000000 (64-bit, non-prefetchable) [size=16M]
    [virtual] Expansion ROM at fcfe0000 [disabled] [size=128K]
    Capabilities: [60] Power Management version 2
    Capabilities: [68] MSI: Enable- Count=1/1 Maskable- 64bit+
    Capabilities: [78] Express Endpoint, MSI 00
    Capabilities: [100] Virtual Channel
    Capabilities: [128] Power Budgeting <?>
    Kernel driver in use: nvidia
    Kernel modules: nvidia-current, nouveau, nvidiafb

02:03.0 Ethernet controller: Atheros Communications Inc. AR5413 802.11abg NIC (rev 01)
    Subsystem: Lite-On Communications Inc Device 5001
    Flags: bus master, medium devsel, latency 168, IRQ 19
    Memory at effd0000 (32-bit, non-prefetchable) [size=64K]
    Capabilities: [44] Power Management version 2
    Kernel driver in use: ath5k
    Kernel modules: ath5k

02:04.0 Multimedia video controller: Conexant Systems, Inc. CX23418 Single-Chip MPEG-2 Encoder with Integrated Analog Video/Broadcast Audio Decoder
    Subsystem: Hauppauge computer works Inc. Device 7400
    Flags: bus master, medium devsel, latency 64, IRQ 16
    Memory at e8000000 (32-bit, non-prefetchable) [size=64M]
    Capabilities: [44] Vital Product Data
    Capabilities: [4c] Power Management version 2
    Kernel driver in use: cx18
    Kernel modules: cx18

02:05.0 Communication controller: Conexant Systems, Inc. HSF 56k Data/Fax Modem
    Subsystem: Conexant Systems, Inc. Soft Data Fax Modem with SmartCP
    Flags: bus master, medium devsel, latency 32, IRQ 7
    Memory at effe0000 (32-bit, non-prefetchable) [size=64K]
    I/O ports at ef00 [size=8]
    Capabilities: [40] Power Management version 2

02:08.0 Ethernet controller: Intel Corporation N10/ICH 7 Family LAN Controller (rev 01)
    Subsystem: Hewlett-Packard Company Device 2a50
    Flags: bus master, medium devsel, latency 32, IRQ 20
    Memory at effff000 (32-bit, non-prefetchable) [size=4K]
    I/O ports at ee00 [size=64]
    Capabilities: [dc] Power Management version 2
    Kernel driver in use: e100
    Kernel modules: e100

```

EDIT: i installed a few other random games some worked some didn't

---

### Post by extremejosh on 2010-11-07
bump:)

---

### Post by extremejosh on 2010-11-08
ok update i found out by changing my resolution in the nvidia x server settings thing that i cant use certain
resolutions so maybe that is whats stopping me from being able to play some of these games so how can i make so i can use other resolutions?

---

### Post by dino99 on 2010-11-08
you might have nvidia-current activated into: system admin additional driver

actual kernel directly drive X, so no need of xorg.conf

sudo rm -f /etc/X11/xorg.conf

---

### Post by extremejosh on 2010-11-08
> **dino99 said:**
> you might have nvidia-current activated into: system admin additional driver

actual kernel directly drive X, so no need of xorg.conf

sudo rm -f /etc/X11/xorg.conf

hey that was helpful it cleared up the issue with the input signal but it stopped my restricted drivers from working right so i couldn't play certain games

---

### Post by dino99 on 2010-11-08
those games are directly played with ubuntu or with wine ?

---

### Post by extremejosh on 2010-11-08
> **dino99 said:**
> those games are directly played with ubuntu or with wine ?

wine mostly but i was having same problem on some random linux games that i was trying to see if worked im hoping i can fix this issue with all games but if i can only fix it with diablo and wow for now then thats ok

---

### Post by extremejosh on 2010-11-08
Bump :)

---

### Post by extremejosh on 2010-11-08
just want to add that changing my resolution manually  resolutions that i should be able to do i can't like i can change it to 640x480  but then again i cant change to 800x600 my native is 1366x768

---

### Post by extremejosh on 2010-11-08
Just adding that i can also do 1024x768 so if i can do the higher resolutions why cant i do some of the lower and if i find out how to do the lower ones will that allow me to play these games?

---

### Post by extremejosh on 2010-11-10
Ok i mostly fixed my issue 90% by editing the config file for each individual game to fit my resolution but i cant get any of my wine games to work namely diablo 2 without runing it in virtual desktop so if anyone knows a fix for this problem id like to hear it

---

