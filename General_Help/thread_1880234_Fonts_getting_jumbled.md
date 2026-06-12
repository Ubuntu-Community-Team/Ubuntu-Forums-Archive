---
title: "Fonts getting jumbled"
date: 2011-11-13
forum: General Help
---

### Post by benlyboy on 2011-11-13
Hi all 
I'm not a great fan on the latest versions of ubuntu. Ever since I updated first to 11.04 and now 11.10 it feels more like windows in that if I leave the system on for more than a few days it starts to slow down, I also often start to see a video pixilation (by that I mean my video starts to look like it is made up of pixels that are about 3 cm square )

But the thing I want to deal with in this post is something else that has been happening, again after the system has been on for more than a few days. the fonts get mixed up,  all the letters and numbers are jumbled.

 From what I can see a "c" may be turned into a "&" you will then see a "&" every where you would see a "c" 

This includes all buttons, tabs, browser windows and anything you type. The first time I saw it I thought it had switched to Greek or something 

Can anyone shine any light on this...?

Thanks

---

### Post by bazcor on 2011-11-13
Sounds as if you have some hardware problem. I would use memtest to check the ram as a first approach.

Good luck.

---

### Post by BillyBoa on 2011-11-13
Maybe you have a video drive problem. Try to play with your video drivers.

[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)

[https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)

---

### Post by DirtyPC on 2011-11-13
BillyBoa I think, is right. I was having this problem back on 10.04 with ATI and VIA video drivers, just had to install them and the problem went away. Did yours start bt initiating firefox?

---

### Post by benlyboy on 2011-11-13
Hi I'm just using the on board video on my old Dell desktop not really sure what the video is 

I ran "lspci -v" and got this

> 

00:00.0 Host bridge: Intel Corporation 82915G/P/GV/GL/PL/910GL Memory Controller Hub (rev 04)
	Subsystem: Dell Device 0179
	Flags: bus master, fast devsel, latency 0
	Capabilities: <access denied>
	Kernel driver in use: agpgart-intel

00:01.0 PCI bridge: Intel Corporation 82915G/P/GV/GL/PL/910GL PCI Express Root Port (rev 04) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
	Memory behind bridge: dfd00000-dfdfffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:02.0 VGA compatible controller: Intel Corporation 82915G/GV/910GL Integrated Graphics Controller (rev 04) (prog-if 00 [VGA controller])
	Subsystem: Dell Device 0179
	Flags: bus master, fast devsel, latency 0, IRQ 16
	Memory at dff00000 (32-bit, non-prefetchable) [size=512K]
	I/O ports at e898 [size=8]
	Memory at c0000000 (32-bit, prefetchable) [size=256M]
	Memory at dfec0000 (32-bit, non-prefetchable) [size=256K]
	Expansion ROM at <unassigned> [disabled]
	Capabilities: <access denied>
	Kernel driver in use: i915
	Kernel modules: intelfb, i915

00:02.1 Display controller: Intel Corporation 82915G Integrated Graphics Controller (rev 04)
	Subsystem: Dell Device 0179
	Flags: bus master, fast devsel, latency 0
	Memory at dff80000 (32-bit, non-prefetchable) [size=512K]
	Capabilities: <access denied>

00:1c.0 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 03) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
	I/O behind bridge: 00001000-00001fff
	Memory behind bridge: dfc00000-dfcfffff
	Prefetchable memory behind bridge: 0000000040000000-00000000401fffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:1c.1 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 2 (rev 03) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
	Memory behind bridge: dfb00000-dfbfffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03) (prog-if 00 [UHCI])
	Subsystem: Dell Optiplex GX280
	Flags: bus master, medium devsel, latency 0, IRQ 21
	I/O ports at ff80 [size=32]
	Kernel driver in use: uhci_hcd

00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03) (prog-if 00 [UHCI])
	Subsystem: Dell Optiplex GX280
	Flags: bus master, medium devsel, latency 0, IRQ 22
	I/O ports at ff60 [size=32]
	Kernel driver in use: uhci_hcd

00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03) (prog-if 00 [UHCI])
	Subsystem: Dell Optiplex GX280
	Flags: bus master, medium devsel, latency 0, IRQ 18
	I/O ports at ff40 [size=32]
	Kernel driver in use: uhci_hcd

00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03) (prog-if 00 [UHCI])
	Subsystem: Dell Optiplex GX280
	Flags: bus master, medium devsel, latency 0, IRQ 23
	I/O ports at ff20 [size=32]
	Kernel driver in use: uhci_hcd

00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03) (prog-if 20 [EHCI])
	Subsystem: Dell Optiplex GX280
	Flags: bus master, medium devsel, latency 0, IRQ 21
	Memory at ffa80800 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>
	Kernel driver in use: ehci_hcd

00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev d3) (prog-if 01 [Subtractive decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=04, subordinate=04, sec-latency=32
	Capabilities: <access denied>

00:1e.2 Multimedia audio controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 03)
	Subsystem: Dell Optiplex GX280
	Flags: bus master, medium devsel, latency 0, IRQ 23
	I/O ports at ec00 [size=256]
	I/O ports at e8c0 [size=64]
	Memory at dfebfe00 (32-bit, non-prefetchable) [size=512]
	Memory at dfebfd00 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>
	Kernel driver in use: Intel ICH
	Kernel modules: snd-intel8x0

00:1f.0 ISA bridge: Intel Corporation 82801FB/FR (ICH6/ICH6R) LPC Interface Bridge (rev 03)
	Flags: bus master, medium devsel, latency 0
	Kernel modules: iTCO_wdt, intel-rng

00:1f.1 IDE interface: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 03) (prog-if 8a [Master SecP PriP])
	Subsystem: Dell Device 0179
	Flags: bus master, medium devsel, latency 0, IRQ 16
	I/O ports at 01f0 [size=8]
	I/O ports at 03f4 [size=1]
	I/O ports at 0170 [size=8]
	I/O ports at 0374 [size=1]
	I/O ports at ffa0 [size=16]
	Kernel driver in use: ata_piix

00:1f.2 IDE interface: Intel Corporation 82801FB/FW (ICH6/ICH6W) SATA Controller (rev 03) (prog-if 8f [Master SecP SecO PriP PriO])
	Subsystem: Dell Optiplex GX280
	Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 20
	I/O ports at fe00 [size=8]
	I/O ports at fe10 [size=4]
	I/O ports at fe20 [size=8]
	I/O ports at fe30 [size=4]
	I/O ports at fea0 [size=16]
	Capabilities: <access denied>
	Kernel driver in use: ata_piix

00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 03)
	Subsystem: Dell Optiplex GX280
	Flags: medium devsel, IRQ 10
	I/O ports at e8a0 [size=32]
	Kernel modules: i2c-i801

02:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5751 Gigabit Ethernet PCI Express (rev 01)
	Subsystem: Dell Optiplex GX280
	Flags: bus master, fast devsel, latency 0, IRQ 16
	Memory at dfcf0000 (64-bit, non-prefetchable) [size=64K]
	Expansion ROM at <ignored> [disabled]
	Capabilities: <access denied>
	Kernel driver in use: tg3
	Kernel modules: tg3

any idea where I should go next...?

---

### Post by benlyboy on 2011-11-14
bump

---

### Post by benlyboy on 2011-11-19
bump

---

### Post by benlyboy on 2011-11-23
bump

---

