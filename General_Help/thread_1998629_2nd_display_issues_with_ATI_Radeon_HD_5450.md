---
title: "2nd display issues with ATI Radeon HD 5450"
date: 2012-06-07
forum: General Help
---

### Post by dheerajjotwani on 2012-06-07
Hardware:
HP N36L Microserver
AMD Athlon(tm) II Neo N36L Dual-Core Processor × 2
4GB DDR3 Ram
RADEON HD 5450 1 GB DDR3

Software:
Ubuntu 12.04 64bit
XBMC Eden
AMDCCCLE
FGLRX

recently bought this and setup ubuntu. installed the hd5450 and redid the drivers. being a noob, followed the written letter to the last dot. rightfully so, the drivers seem to be installed properly cause i can change settings. the issue arose with the desire to add a hdmi output to the lcd tv for use with xbmc.

amdcccle shows both the primary display, a samsung 19" TFT cinnected via dvi-vga, and the lcd tv, samsung la32b530 via hdmi, correctly configured with resolution on 1440x900 and 1920x1080. the display setting however show only the tft monitor. and no second display whatsoever.

OUTPUTS

1. lspci -v
```
00:00.0 Host bridge: Advanced Micro Devices [AMD] RS880 Host Bridge
	Subsystem: Hewlett-Packard Company Device 1609
	Flags: bus master, 66MHz, medium devsel, latency 0
	Capabilities: [c4] HyperTransport: Slave or Primary Interface
	Capabilities: [54] HyperTransport: UnitID Clumping
	Capabilities: [40] HyperTransport: Retry Mode
	Capabilities: [9c] HyperTransport: #1a
	Capabilities: [f8] HyperTransport: #1c

00:02.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (ext gfx port 0) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
	I/O behind bridge: 0000e000-0000efff
	Memory behind bridge: fe800000-fe8fffff
	Prefetchable memory behind bridge: 00000000d0000000-00000000dfffffff
	Capabilities: [50] Power Management version 3
	Capabilities: [58] Express Root Port (Slot+), MSI 00
	Capabilities: [a0] MSI: Enable+ Count=1/1 Maskable- 64bit-
	Capabilities: [b0] Subsystem: Hewlett-Packard Company Device 1609
	Capabilities: [b8] HyperTransport: MSI Mapping Enable+ Fixed+
	Capabilities: [100] Vendor Specific Information: ID=0001 Rev=1 Len=010 <?>
	Capabilities: [110] Virtual Channel
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:06.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 2) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
	Memory behind bridge: fe900000-fe9fffff
	Capabilities: [50] Power Management version 3
	Capabilities: [58] Express Root Port (Slot-), MSI 00
	Capabilities: [a0] MSI: Enable+ Count=1/1 Maskable- 64bit-
	Capabilities: [b0] Subsystem: Hewlett-Packard Company Device 1609
	Capabilities: [b8] HyperTransport: MSI Mapping Enable+ Fixed+
	Capabilities: [100] Vendor Specific Information: ID=0001 Rev=1 Len=010 <?>
	Capabilities: [110] Virtual Channel
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:11.0 SATA controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 SATA Controller [AHCI mode] (rev 40) (prog-if 01 [AHCI 1.0])
	Subsystem: Hewlett-Packard Company Device 1609
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 42
	I/O ports at d000 [size=8]
	I/O ports at c000 [size=4]
	I/O ports at b000 [size=8]
	I/O ports at a000 [size=4]
	I/O ports at 9000 [size=16]
	Memory at fe7ffc00 (32-bit, non-prefetchable) [size=1K]
	Capabilities: [50] MSI: Enable+ Count=1/8 Maskable- 64bit+
	Capabilities: [70] SATA HBA v1.0
	Capabilities: [a4] PCI Advanced Features
	Kernel driver in use: ahci

00:12.0 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB OHCI0 Controller (prog-if 10 [OHCI])
	Subsystem: Hewlett-Packard Company Device 1609
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 18
	Memory at fe7fe000 (32-bit, non-prefetchable) [size=4K]
	Kernel driver in use: ohci_hcd

00:12.2 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB EHCI Controller (prog-if 20 [EHCI])
	Subsystem: Hewlett-Packard Company Device 1609
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 17
	Memory at fe7ff800 (32-bit, non-prefetchable) [size=256]
	Capabilities: [c0] Power Management version 2
	Capabilities: [e4] Debug port: BAR=1 offset=00e0
	Kernel driver in use: ehci_hcd

00:13.0 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB OHCI0 Controller (prog-if 10 [OHCI])
	Subsystem: Hewlett-Packard Company Device 1609
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 18
	Memory at fe7fd000 (32-bit, non-prefetchable) [size=4K]
	Kernel driver in use: ohci_hcd

00:13.2 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB EHCI Controller (prog-if 20 [EHCI])
	Subsystem: Hewlett-Packard Company Device 1609
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 17
	Memory at fe7ff400 (32-bit, non-prefetchable) [size=256]
	Capabilities: [c0] Power Management version 2
	Capabilities: [e4] Debug port: BAR=1 offset=00e0
	Kernel driver in use: ehci_hcd

00:14.0 SMBus: Advanced Micro Devices [AMD] nee ATI SBx00 SMBus Controller (rev 41)
	Flags: 66MHz, medium devsel
	Kernel driver in use: piix4_smbus
	Kernel modules: sp5100_tco, i2c-piix4

00:14.3 ISA bridge: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 LPC host controller (rev 40)
	Subsystem: Hewlett-Packard Company Device 1609
	Flags: bus master, 66MHz, medium devsel, latency 0

00:14.4 PCI bridge: Advanced Micro Devices [AMD] nee ATI SBx00 PCI to PCI Bridge (rev 40) (prog-if 01 [Subtractive decode])
	Flags: bus master, 66MHz, medium devsel, latency 64
	Bus: primary=00, secondary=03, subordinate=03, sec-latency=64

00:16.0 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB OHCI0 Controller (prog-if 10 [OHCI])
	Subsystem: Hewlett-Packard Company Device 1609
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 18
	Memory at fe7fc000 (32-bit, non-prefetchable) [size=4K]
	Kernel driver in use: ohci_hcd

00:16.2 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB EHCI Controller (prog-if 20 [EHCI])
	Subsystem: Hewlett-Packard Company Device 1609
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 17
	Memory at fe7ff000 (32-bit, non-prefetchable) [size=256]
	Capabilities: [c0] Power Management version 2
	Capabilities: [e4] Debug port: BAR=1 offset=00e0
	Kernel driver in use: ehci_hcd

00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor HyperTransport Configuration
	Flags: fast devsel
	Capabilities: [80] HyperTransport: Host or Secondary Interface

00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Address Map
	Flags: fast devsel

00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor DRAM Controller
	Flags: fast devsel
	Kernel modules: amd64_edac_mod

00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Miscellaneous Control
	Flags: fast devsel
	Capabilities: [f0] Secure device <?>
	Kernel driver in use: k10temp
	Kernel modules: k10temp

00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Link Control
	Flags: fast devsel

01:00.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI Cedar PRO [Radeon HD 5450] (prog-if 00 [VGA controller])
	Subsystem: PC Partner Limited Device e164
	Flags: bus master, fast devsel, latency 0, IRQ 45
	Memory at d0000000 (64-bit, prefetchable) [size=256M]
	Memory at fe8e0000 (64-bit, non-prefetchable) [size=128K]
	I/O ports at e000 [size=256]
	Expansion ROM at fe8c0000 [disabled] [size=128K]
	Capabilities: [50] Power Management version 3
	Capabilities: [58] Express Legacy Endpoint, MSI 00
	Capabilities: [a0] MSI: Enable+ Count=1/1 Maskable- 64bit+
	Capabilities: [100] Vendor Specific Information: ID=0001 Rev=1 Len=010 <?>
	Capabilities: [150] Advanced Error Reporting
	Kernel driver in use: fglrx_pci
	Kernel modules: fglrx, radeon

01:00.1 Audio device: Advanced Micro Devices [AMD] nee ATI Cedar HDMI Audio [Radeon HD 5400/6300 Series]
	Subsystem: PC Partner Limited Device aa68
	Flags: bus master, fast devsel, latency 0, IRQ 43
	Memory at fe8bc000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: [50] Power Management version 3
	Capabilities: [58] Express Legacy Endpoint, MSI 00
	Capabilities: [a0] MSI: Enable+ Count=1/1 Maskable- 64bit+
	Capabilities: [100] Vendor Specific Information: ID=0001 Rev=1 Len=010 <?>
	Capabilities: [150] Advanced Error Reporting
	Kernel driver in use: snd_hda_intel
	Kernel modules: snd-hda-intel

02:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5723 Gigabit Ethernet PCIe (rev 10)
	Subsystem: Hewlett-Packard Company NC107i Integrated PCI Express Gigabit Server Adapter
	Flags: bus master, fast devsel, latency 0, IRQ 44
	Memory at fe9f0000 (64-bit, non-prefetchable) [size=64K]
	Capabilities: [48] Power Management version 3
	Capabilities: [40] Vital Product Data
	Capabilities: [60] Vendor Specific Information: Len=6c <?>
	Capabilities: [50] MSI: Enable+ Count=1/1 Maskable- 64bit+
	Capabilities: [cc] Express Endpoint, MSI 00
	Capabilities: [100] Advanced Error Reporting
	Capabilities: [13c] Virtual Channel
	Capabilities: [160] Device Serial Number d4-85-64-ff-fe-6a-af-88
	Capabilities: [16c] Power Budgeting <?>
	Kernel driver in use: tg3
	Kernel modules: tg3

```

2. Xorg.conf
```
Section "ServerLayout"
	Identifier     "amdcccle Layout"
	Screen      0  "amdcccle-Screen[1]-0" 0 0
	Screen         "amdcccle-Screen[1]-1" 1440 0
EndSection

Section "Module"
	Load  "glx"
EndSection

Section "ServerFlags"
	Option	    "Xinerama" "off"
EndSection

Section "Monitor"
	Identifier   "0-DFP1"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
	Option	    "TargetRefresh" "60"
	Option	    "Position" "0 0"
	Option	    "Rotate" "normal"
	Option	    "Disable" "false"
	Option	    "PreferredMode" "1920x1080"
EndSection

Section "Monitor"
	Identifier   "0-CRT1"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
	Option	    "PreferredMode" "1440x900"
	Option	    "TargetRefresh" "60"
	Option	    "Position" "0 0"
	Option	    "Rotate" "normal"
	Option	    "Disable" "false"
EndSection

Section "Device"
	Identifier  "amdcccle-Device[1]-0"
	Driver      "fglrx"
	Option	    "Monitor-CRT1" "0-CRT1"
	BusID       "PCI:1:0:0"
EndSection

Section "Device"
	Identifier  "amdcccle-Device[1]-1"
	Driver      "fglrx"
	Option	    "Monitor-DFP1" "0-DFP1"
	BusID       "PCI:1:0:0"
	Screen      1
EndSection

Section "Screen"
	Identifier "Default Screen"
	DefaultDepth     24
EndSection

Section "Screen"
	Identifier "amdcccle-Screen[1]-0"
	Device     "amdcccle-Device[1]-0"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

Section "Screen"
	Identifier "amdcccle-Screen[1]-1"
	Device     "amdcccle-Device[1]-1"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

```

3. xrandr --prop
```
Screen 0: minimum 320 x 200, current 1440 x 900, maximum 1920 x 1920
DFP1 connected (normal left inverted right x axis y axis)
	EDID_DATA:
		00ffffffffffff004c2dfb0400000000
		2f120103801009780aee91a3544c9926
		0f5054bdef80714f8100814081809500
		950fb300a940023a801871382d40582c
		4500a05a0000001e662150b051001b30
		40703600a05a0000001e000000fd0018
		4b1a5117000a202020202020000000fc
		0053414d53554e470a20202020200199
	SignalFormat:	TMDS
	ConnectorType:	HDMI
   1440x900       60.0 +
   1920x1080      60.0 +   50.0     59.9     30.0     25.0     25.0     24.0     30.0     30.0  
   1776x1000      50.0     59.9     25.0     25.0     24.0     30.0     30.0  
   1680x1050      60.0  
   1400x1050      60.0  
   1600x900       60.0  
   1280x1024      60.0  
   1280x960       60.0  
   1360x768       60.0  
   1280x800       60.0  
   1152x864       60.0  
   1280x768       60.0  
   1280x720       50.0     59.9  
   1024x768       60.0  
   1152x648       50.0     59.9  
   800x600        60.0  
   720x480        60.0  
   640x480        60.0  
DFP2 disconnected (normal left inverted right x axis y axis)
	SignalFormat:	TMDS
	ConnectorType:	DVI-I
CRT1 connected 1440x900+0+0 (normal left inverted right x axis y axis) 410mm x 257mm
	EDID_DATA:
		00ffffffffffff004c2d850239314148
		0f1101030e291a872ad7a5a2594a9624
		145054bfef809500950f81808140714f
		0101010101019a29a0d0518422305098
		36009a011100001c000000fd00384b1e
		510e000a202020202020000000fc0053
		796e634d61737465720a2020000000ff
		00484d44503430373438360a202000c6
	SignalFormat:	VGA
	ConnectorType:	DVI-I
   1440x900       59.9*+   75.0  
   1280x1024      75.0     60.0  
   1280x960       60.0  
   1280x800       60.0  
   1152x864       75.0     59.9  
   1280x768       60.0  
   1280x720       60.0  
   1024x768       75.0     70.1     60.0  
   800x600        72.2     75.0     60.3     56.2  
   640x480        75.0     72.8     67.0     59.9  
CRT2 disconnected (normal left inverted right x axis y axis)
	SignalFormat:	VGA
	ConnectorType:	VGA

```

Gurus, please guide and help me resolve an output to the lcd tv from xbmc. 

thanks and appreciated

---

