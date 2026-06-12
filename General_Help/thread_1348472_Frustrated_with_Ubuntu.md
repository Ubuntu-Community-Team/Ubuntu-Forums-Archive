---
title: "Frustrated with Ubuntu"
date: 2009-12-07
forum: General Help
---

### Post by GeorgeOfTheBush on 2009-12-07
Ubuntu Freezes/Hangs every now and then. This problem started while I was using Ubuntu 9.04. I then upgraded to 9.10 expecting the problem to have got resolved. But the problem has become worse. The mouse cursor just moves while the background is frozen. All I can do is switch off with the power on/off switch and restart.

The application that I use mostly is **Firefox**. And the crash happens most of the time while scrolling up/down. So is the problem related to Firefox alone or is it with Ubuntu itself??

Any suggestions would be very helpful.

Thanks.

---

### Post by dansar99 on 2009-12-07
I use SeaMonkey which is a mozilla browser too but seems to work much better than FireFox for me. Also the Opera browser works fine also. Dan

---

### Post by abhilashm86 on 2009-12-07
> **GeorgeOfTheBush said:**
> Ubuntu Freezes/Hangs every now and then. This problem started while I was using Ubuntu 9.04. I then upgraded to 9.10 expecting the problem to have got resolved. But the problem has become worse. The mouse cursor just moves while the background is frozen. All I can do is switch off with the power on/off switch and restart.

The application that I use mostly is **Firefox**. And the crash happens most of the time while scrolling up/down. So is the problem related to Firefox alone or is it with Ubuntu itself??

Any suggestions would be very helpful.

Thanks.

while your older version 9.04 had some problems, what were they? is your graphics card supported? did you check hardware drivers? 

when you upgrade, you need to know how to tweek and set things up, maybe the not working files would be related to more things and made things worse......

---

### Post by abhilashm86 on 2009-12-07
> **GeorgeOfTheBush said:**
> Ubuntu Freezes/Hangs every now and then. This problem started while I was using Ubuntu 9.04. I then upgraded to 9.10 expecting the problem to have got resolved. But the problem has become worse. The mouse cursor just moves while the background is frozen. All I can do is switch off with the power on/off switch and restart.

The application that I use mostly is **Firefox**. And the crash happens most of the time while scrolling up/down. So is the problem related to Firefox alone or is it with Ubuntu itself??

Any suggestions would be very helpful.

Thanks.

i suggest you work in a ubuntu live CD, see that your system behaves properly, then you can go ahead with install,
make sure the graphics card is fully supported, if not don't install 
compiz and others.

i have never had firefox crash in 2 years!! trust me ubuntu is stable, just you need to master the art of tweaking things:) all the best

for now you can make a clean install of ubuntu 9.10, install all updates and start working...........

---

### Post by GeorgeOfTheBush on 2009-12-07
Thanks a lot for your super quick responses.

How do I check if my graphics card is fully supported? Also, how to check whether I am using compiz?

I must admit that I have not installed any of the Ubuntu 9.10 updates reported by the Ubuntu Update manager.

---

### Post by ST3ALTHPSYCH0 on 2009-12-07
I would start by installing the updates, as Karmic has had 3 kernel updates, and countless updates that have improved stability. 
Second, you can make EXT filesystems unbootable by doing a hard power off. What you should do is hold alt+prnt scrn+(this is a sequence)r-e-i-s-u-b. that final b tells the computer to shutdown, but it's never worked for me, you can replace it with "o" and restart though.

EDIT:
oops, uhh "b" is reboot, "o" is shutdown. I never have gotten reboot to work, but shutdown does. My bad.

---

### Post by abhilashm86 on 2009-12-07
> **GeorgeOfTheBush said:**
> Thanks a lot for your super quick responses.

How do I check if my graphics card is fully supported? Also, how to check whether I am using compiz?

I must admit that I have not installed any of the Ubuntu 9.10 updates reported by the Ubuntu Update manager.

hi George, 
see you need to install some 105MB of updates, they are important, it has bugs clear, new libraries, thats why updates are huge, if you see......
for firedox almost 10 MB and more things for easy use and smooth running, 
better install updates and enjoy ubuntu....

once my friend told, i off updates in windows, they catch him coz he runs pirated version!!
but in ubuntu also his mind din't change, din't install updates in 8.04!! so faced loads of problem, then he installed, now he teaches ubuntu others!! 
all the best

for checking graphics drivers,
see 
system->administration->hardware drivers 
anything there, install.......

if you have nvidia card, in terminal, you can use,```
lspci | grep -i nvidia
```

or if no nvidia,
then ```
lspci -v
``` 
will tell about graphics card, here command means searching and ls means list all present, pci means peripheral control interfaces :) 
all d best!!

---

### Post by GeorgeOfTheBush on 2009-12-08
I have installed all the updates reported by ubuntu 9.10 Update Manager. But the problem has not got resolved.

Any other suggestions, abhilash, dan?

**Hardware drivers output** > No proprietary drivers installed.

**lspci -v output:**

[INDENT]00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 03)
    Subsystem: Hewlett-Packard Company Device 3080
    Flags: bus master, fast devsel, latency 0
    Capabilities: <access denied>
    Kernel driver in use: agpgart-intel
    Kernel modules: intel-agp

00:02.0 VGA compatible controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
    Subsystem: Hewlett-Packard Company Device 3080
    Flags: bus master, fast devsel, latency 0, IRQ 16
    Memory at b0080000 (32-bit, non-prefetchable) [size=512K]
    I/O ports at 1800 [size=8]
    Memory at c0000000 (32-bit, prefetchable) [size=256M]
    Memory at b0000000 (32-bit, non-prefetchable) [size=256K]
    Capabilities: <access denied>
    Kernel driver in use: i915
    Kernel modules: i915

00:02.1 Display controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
    Subsystem: Hewlett-Packard Company Device 3080
    Flags: fast devsel
    Memory at 44000000 (32-bit, non-prefetchable) [disabled] [size=512K]
    Capabilities: <access denied>

00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03)
    Subsystem: Hewlett-Packard Company Device 3080
    Flags: bus master, medium devsel, latency 0, IRQ 23
    I/O ports at 1820 [size=32]
    Kernel driver in use: uhci_hcd

00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03)
    Subsystem: Hewlett-Packard Company Device 3080
    Flags: bus master, medium devsel, latency 0, IRQ 19
    I/O ports at 1840 [size=32]
    Kernel driver in use: uhci_hcd

00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03)
    Subsystem: Hewlett-Packard Company Device 3080
    Flags: bus master, medium devsel, latency 0, IRQ 18
    I/O ports at 1860 [size=32]
    Kernel driver in use: uhci_hcd

00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03)
    Subsystem: Hewlett-Packard Company Device 3080
    Flags: bus master, medium devsel, latency 0, IRQ 16
    I/O ports at 1880 [size=32]
    Kernel driver in use: uhci_hcd

00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03) (prog-if 20)
    Subsystem: Hewlett-Packard Company Device 3080
    Flags: bus master, medium devsel, latency 0, IRQ 23
    Memory at b0040000 (32-bit, non-prefetchable) [size=1K]
    Capabilities: <access denied>
    Kernel driver in use: ehci_hcd

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev d3) (prog-if 01)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=06, subordinate=0a, sec-latency=216
    I/O behind bridge: 00003000-00003fff
    Memory behind bridge: b0100000-b01fffff
    Prefetchable memory behind bridge: 0000000040000000-0000000043ffffff
    Capabilities: <access denied>

00:1e.2 Multimedia audio controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 03)
    Subsystem: Hewlett-Packard Company Device 3080
    Flags: bus master, medium devsel, latency 0, IRQ 17
    I/O ports at 1c00 [size=256]
    I/O ports at 18c0 [size=64]
    Memory at b0040800 (32-bit, non-prefetchable) [size=512]
    Memory at b0040400 (32-bit, non-prefetchable) [size=256]
    Capabilities: <access denied>
    Kernel driver in use: Intel ICH
    Kernel modules: snd-intel8x0

00:1e.3 Modem: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Modem Controller (rev 03)
    Subsystem: Hewlett-Packard Company Device 3080
    Flags: medium devsel, IRQ 20
    I/O ports at 2400 [size=256]
    I/O ports at 2000 [size=128]
    Capabilities: <access denied>
    Kernel modules: snd-intel8x0m

00:1f.0 ISA bridge: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge (rev 03)
    Subsystem: Hewlett-Packard Company Device 3080
    Flags: bus master, medium devsel, latency 0
    Kernel modules: iTCO_wdt, intel-rng

00:1f.1 IDE interface: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 03) (prog-if 8a [Master SecP PriP])
    Subsystem: Hewlett-Packard Company Device 3080
    Flags: bus master, medium devsel, latency 0, IRQ 18
    I/O ports at 01f0 [size=8]
    I/O ports at 03f4 [size=1]
    I/O ports at 0170 [size=8]
    I/O ports at 0374 [size=1]
    I/O ports at 1810 [size=16]
    Kernel driver in use: ata_piix

00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 03)
    Subsystem: Hewlett-Packard Company Device 3080
    Flags: medium devsel, IRQ 3
    I/O ports at 20a0 [size=32]
    Kernel modules: i2c-i801

06:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
    Subsystem: Hewlett-Packard Company Device 3080
    Flags: bus master, medium devsel, latency 64, IRQ 16
    I/O ports at 3000 [size=256]
    Memory at b0106000 (32-bit, non-prefetchable) [size=256]
    Capabilities: <access denied>
    Kernel driver in use: 8139too
    Kernel modules: epl, 8139too, 8139cp

06:06.0 Network controller: Intel Corporation PRO/Wireless 2200BG [Calexico2] Network Connection (rev 05)
    Subsystem: Hewlett-Packard Company Device 12f5
    Flags: bus master, medium devsel, latency 32, IRQ 18
    Memory at b0107000 (32-bit, non-prefetchable) [size=4K]
    Capabilities: <access denied>
    Kernel driver in use: ipw2200
    Kernel modules: ipw2200

06:09.0 CardBus bridge: Texas Instruments PCIxx21/x515 Cardbus Controller
    Subsystem: Hewlett-Packard Company Device 3080
    Flags: bus master, medium devsel, latency 168, IRQ 20
    Memory at b0109000 (32-bit, non-prefetchable) [size=4K]
    Bus: primary=06, secondary=07, subordinate=0a, sec-latency=176
    Memory window 0: 40000000-43fff000 (prefetchable)
    Memory window 1: 48000000-4bfff000
    I/O window 0: 00003400-000034ff
    I/O window 1: 00003800-000038ff
    16-bit legacy interface ports at 0001
    Kernel driver in use: yenta_cardbus
    Kernel modules: yenta_socket

06:09.2 FireWire (IEEE 1394): Texas Instruments OHCI Compliant IEEE 1394 Host Controller (prog-if 10)
    Subsystem: Hewlett-Packard Company Device 3080
    Flags: bus master, medium devsel, latency 32, IRQ 22
    Memory at b0106800 (32-bit, non-prefetchable) [size=2K]
    Memory at b0100000 (32-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: ohci1394
    Kernel modules: firewire-ohci, ohci1394

06:09.3 Mass storage controller: Texas Instruments PCIxx21 Integrated FlashMedia Controller
    Subsystem: Hewlett-Packard Company Device 3080
    Flags: bus master, medium devsel, latency 57, IRQ 20
    Memory at b0104000 (32-bit, non-prefetchable) [size=8K]
    Capabilities: <access denied>
    Kernel driver in use: tifm_7xx1
    Kernel modules: tifm_7xx1

06:09.4 SD Host controller: Texas Instruments PCI6411/6421/6611/6621/7411/7421/7611/7621 Secure Digital Controller
    Subsystem: Hewlett-Packard Company Device 3080
    Flags: bus master, medium devsel, latency 57, IRQ 20
    Memory at b0108400 (32-bit, non-prefetchable) [size=256]
    Memory at b0108000 (32-bit, non-prefetchable) [size=256]
    Memory at b0106400 (32-bit, non-prefetchable) [size=256]
    Capabilities: <access denied>
    Kernel driver in use: sdhci-pci
    Kernel modules: sdhci-pci

[/INDENT]

---

### Post by GeorgeOfTheBush on 2009-12-10
My Frustration keeps going up.:frown:

I have Ubuntu 9.10 installed through Wubi on a Winxp based HP laptop.

HELP!

---

