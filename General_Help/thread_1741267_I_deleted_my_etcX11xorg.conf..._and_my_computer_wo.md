---
title: "I deleted my /etc/X11/xorg.conf... and my computer works BETTER? How does that work?"
date: 2011-04-27
forum: General Help
---

### Post by yanom on 2011-04-27
So, I installed the FGLRX proprietary driver, and it totally screwed it up, reverting it to command-line only. I uninstalled FGLRX, installed the open-source ATI driver, but it was still command-line only. I was able to make my graphical systems work again by deleting the file /etc/X11/xorg.conf, on a forum poster's advice. My computer works fine now, I think on open-source drivers, but I'm curious... if /etc/X11/xorg.conf stores all X window system configuration, how does X work without it? Is there some file somewhere that it's fallen back on? Thanks.

---

### Post by Telengard C64 on 2011-04-27
I was reading about this somewhere not long ago. IIRC Xorg dynamically autoconfigures itself now. So apparently Xorg is intelligent enough to choose a configuration that works well with your system. Good news  :)

**_Edit_**
[https://help.ubuntu.com/community/XORGHardy](https://help.ubuntu.com/community/XORGHardy)

---

### Post by idoitprone on 2011-04-27
try using lspci -v for info

---

### Post by yanom on 2011-04-28
It doesn't use xorg.conf anymore? Than how did deleting it have any effect on my system?

---

### Post by Lateralis on 2011-04-28
As I understand it, if xorg.conf exists, xorg will use that configuration file.  If it doesn't then it won't.  But xorg no longer requires xorg.conf to exist.  (As far as I know!)

---

### Post by el_koraco on 2011-04-28
> **yanom said:**
> It doesn't use xorg.conf anymore? Than how did deleting it have any effect on my system?

The radon driver does not need the xorg.conf file to work. Actually, in some cases, that is the exact thing that might be stopping it. The file was created during the installation of fglrx.

If you do this again, don't delete the file, just rename it. That way it will still be there in case you need it for troubleshooting.

---

### Post by Telengard C64 on 2011-04-28
> **el_koraco said:**
> If you do this again, don't delete the file, just rename it. That way it will still be there in case you need it for troubleshooting.

^ sage advice

---

### Post by yanom on 2011-04-28
> **Telengard C64 said:**
> ^ sage advice

oops.

---

### Post by yanom on 2011-04-28
Here's the output of lspci -v. 

```
00:00.0 Host bridge: Intel Corporation 5520/5500/X58 I/O Hub to ESI Port (rev 13)
	Subsystem: ASUSTeK Computer Inc. Device 836b
	Flags: fast devsel
	Capabilities: [60] MSI: Enable- Count=1/2 Maskable+ 64bit-
	Capabilities: [90] Express Root Port (Slot-), MSI 00
	Capabilities: [e0] Power Management version 3
	Capabilities: [100] Advanced Error Reporting
	Capabilities: [150] Access Control Services
	Capabilities: [160] Vendor Specific Information: ID=0002 Rev=0 Len=00c <?>

00:01.0 PCI bridge: Intel Corporation 5520/5500/X58 I/O Hub PCI Express Root Port 1 (rev 13) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
	I/O behind bridge: 0000b000-0000bfff
	Memory behind bridge: fba00000-fbafffff
	Capabilities: [40] Subsystem: ASUSTeK Computer Inc. Device 836b
	Capabilities: [60] MSI: Enable+ Count=1/2 Maskable+ 64bit-
	Capabilities: [90] Express Root Port (Slot+), MSI 00
	Capabilities: [e0] Power Management version 3
	Capabilities: [100] Advanced Error Reporting
	Capabilities: [150] Access Control Services
	Capabilities: [160] Vendor Specific Information: ID=0002 Rev=0 Len=00c <?>
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:02.0 PCI bridge: Intel Corporation 5520/5500/X58 I/O Hub PCI Express Root Port 2 (rev 13) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
	Memory behind bridge: fbb00000-fbbfffff
	Capabilities: [40] Subsystem: ASUSTeK Computer Inc. Device 836b
	Capabilities: [60] MSI: Enable+ Count=1/2 Maskable+ 64bit-
	Capabilities: [90] Express Root Port (Slot+), MSI 00
	Capabilities: [e0] Power Management version 3
	Capabilities: [100] Advanced Error Reporting
	Capabilities: [150] Access Control Services
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:03.0 PCI bridge: Intel Corporation 5520/5500/X58 I/O Hub PCI Express Root Port 3 (rev 13) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
	I/O behind bridge: 0000c000-0000cfff
	Memory behind bridge: fbc00000-fbcfffff
	Prefetchable memory behind bridge: 00000000d0000000-00000000dfffffff
	Capabilities: [40] Subsystem: ASUSTeK Computer Inc. Device 836b
	Capabilities: [60] MSI: Enable+ Count=1/2 Maskable+ 64bit-
	Capabilities: [90] Express Root Port (Slot+), MSI 00
	Capabilities: [e0] Power Management version 3
	Capabilities: [100] Advanced Error Reporting
	Capabilities: [150] Access Control Services
	Capabilities: [160] Vendor Specific Information: ID=0002 Rev=0 Len=00c <?>
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:07.0 PCI bridge: Intel Corporation 5520/5500/X58 I/O Hub PCI Express Root Port 7 (rev 13) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=04, subordinate=04, sec-latency=0
	Capabilities: [40] Subsystem: ASUSTeK Computer Inc. Device 836b
	Capabilities: [60] MSI: Enable+ Count=1/2 Maskable+ 64bit-
	Capabilities: [90] Express Root Port (Slot+), MSI 00
	Capabilities: [e0] Power Management version 3
	Capabilities: [100] Advanced Error Reporting
	Capabilities: [150] Access Control Services
	Capabilities: [160] Vendor Specific Information: ID=0002 Rev=0 Len=00c <?>
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:14.0 PIC: Intel Corporation 5520/5500/X58 I/O Hub System Management Registers (rev 13) (prog-if 00 [8259])
	Flags: fast devsel
	Capabilities: [40] Express Root Complex Integrated Endpoint, MSI 00
	Kernel driver in use: i7core_edac
	Kernel modules: i7core_edac

00:14.1 PIC: Intel Corporation 5520/5500/X58 I/O Hub GPIO and Scratch Pad Registers (rev 13) (prog-if 00 [8259])
	Flags: fast devsel
	Capabilities: [40] Express Root Complex Integrated Endpoint, MSI 00
	Kernel modules: mce-xeon75xx

00:14.2 PIC: Intel Corporation 5520/5500/X58 I/O Hub Control Status and RAS Registers (rev 13) (prog-if 00 [8259])
	Flags: fast devsel
	Capabilities: [40] Express Root Complex Integrated Endpoint, MSI 00

00:14.3 PIC: Intel Corporation 5520/5500/X58 I/O Hub Throttle Registers (rev 13) (prog-if 00 [8259])
	Flags: fast devsel

00:1a.0 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #4 (prog-if 00 [UHCI])
	Subsystem: ASUSTeK Computer Inc. Device 82d4
	Flags: bus master, medium devsel, latency 0, IRQ 16
	I/O ports at a800 [size=32]
	Capabilities: [50] PCI Advanced Features
	Kernel driver in use: uhci_hcd

00:1a.1 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #5 (prog-if 00 [UHCI])
	Subsystem: ASUSTeK Computer Inc. Device 82d4
	Flags: bus master, medium devsel, latency 0, IRQ 21
	I/O ports at a880 [size=32]
	Capabilities: [50] PCI Advanced Features
	Kernel driver in use: uhci_hcd

00:1a.2 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #6 (prog-if 00 [UHCI])
	Subsystem: ASUSTeK Computer Inc. Device 82d4
	Flags: bus master, medium devsel, latency 0, IRQ 19
	I/O ports at ac00 [size=32]
	Capabilities: [50] PCI Advanced Features
	Kernel driver in use: uhci_hcd

00:1a.7 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB2 EHCI Controller #2 (prog-if 20 [EHCI])
	Subsystem: ASUSTeK Computer Inc. Device 82d4
	Flags: bus master, medium devsel, latency 0, IRQ 18
	Memory at fb9ff000 (32-bit, non-prefetchable) [size=1K]
	Capabilities: [50] Power Management version 2
	Capabilities: [58] Debug port: BAR=1 offset=00a0
	Capabilities: [98] PCI Advanced Features
	Kernel driver in use: ehci_hcd

00:1b.0 Audio device: Intel Corporation 82801JI (ICH10 Family) HD Audio Controller
	Subsystem: ASUSTeK Computer Inc. Device 8436
	Flags: bus master, fast devsel, latency 0, IRQ 72
	Memory at fb9f8000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: [50] Power Management version 2
	Capabilities: [60] MSI: Enable+ Count=1/1 Maskable- 64bit+
	Capabilities: [70] Express Root Complex Integrated Endpoint, MSI 00
	Capabilities: [100] Virtual Channel
	Capabilities: [130] Root Complex Link
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel

00:1c.0 PCI bridge: Intel Corporation 82801JI (ICH10 Family) PCI Express Root Port 1 (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=06, subordinate=06, sec-latency=0
	I/O behind bridge: 00002000-00002fff
	Memory behind bridge: c0000000-c03fffff
	Prefetchable memory behind bridge: 00000000faf00000-00000000faffffff
	Capabilities: [40] Express Root Port (Slot+), MSI 00
	Capabilities: [80] MSI: Enable+ Count=1/1 Maskable- 64bit-
	Capabilities: [90] Subsystem: ASUSTeK Computer Inc. Device 8436
	Capabilities: [a0] Power Management version 2
	Capabilities: [100] Virtual Channel
	Capabilities: [180] Root Complex Link
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:1c.4 PCI bridge: Intel Corporation 82801JI (ICH10 Family) PCI Express Root Port 5 (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=05, subordinate=05, sec-latency=0
	I/O behind bridge: 0000d000-0000dfff
	Memory behind bridge: fbd00000-fbdfffff
	Prefetchable memory behind bridge: 00000000c0400000-00000000c05fffff
	Capabilities: [40] Express Root Port (Slot+), MSI 00
	Capabilities: [80] MSI: Enable+ Count=1/1 Maskable- 64bit-
	Capabilities: [90] Subsystem: ASUSTeK Computer Inc. Device 8436
	Capabilities: [a0] Power Management version 2
	Capabilities: [100] Virtual Channel
	Capabilities: [180] Root Complex Link
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:1d.0 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #1 (prog-if 00 [UHCI])
	Subsystem: ASUSTeK Computer Inc. Device 82d4
	Flags: bus master, medium devsel, latency 0, IRQ 23
	I/O ports at a080 [size=32]
	Capabilities: [50] PCI Advanced Features
	Kernel driver in use: uhci_hcd

00:1d.1 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #2 (prog-if 00 [UHCI])
	Subsystem: ASUSTeK Computer Inc. Device 82d4
	Flags: bus master, medium devsel, latency 0, IRQ 19
	I/O ports at a400 [size=32]
	Capabilities: [50] PCI Advanced Features
	Kernel driver in use: uhci_hcd

00:1d.2 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #3 (prog-if 00 [UHCI])
	Subsystem: ASUSTeK Computer Inc. Device 82d4
	Flags: bus master, medium devsel, latency 0, IRQ 18
	I/O ports at a480 [size=32]
	Capabilities: [50] PCI Advanced Features
	Kernel driver in use: uhci_hcd

00:1d.7 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB2 EHCI Controller #1 (prog-if 20 [EHCI])
	Subsystem: ASUSTeK Computer Inc. Device 82d4
	Flags: bus master, medium devsel, latency 0, IRQ 23
	Memory at fb9fe000 (32-bit, non-prefetchable) [size=1K]
	Capabilities: [50] Power Management version 2
	Capabilities: [58] Debug port: BAR=1 offset=00a0
	Capabilities: [98] PCI Advanced Features
	Kernel driver in use: ehci_hcd

00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 90) (prog-if 01 [Subtractive decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=07, subordinate=07, sec-latency=32
	I/O behind bridge: 0000e000-0000efff
	Memory behind bridge: fbe00000-fbefffff
	Capabilities: [50] Subsystem: ASUSTeK Computer Inc. Device 82d4

00:1f.0 ISA bridge: Intel Corporation 82801JIR (ICH10R) LPC Interface Controller
	Subsystem: ASUSTeK Computer Inc. Device 82d4
	Flags: bus master, medium devsel, latency 0
	Capabilities: [e0] Vendor Specific Information: Len=0c <?>
	Kernel modules: iTCO_wdt

00:1f.2 SATA controller: Intel Corporation 82801JI (ICH10 Family) SATA AHCI Controller (prog-if 01 [AHCI 1.0])
	Subsystem: ASUSTeK Computer Inc. P5Q Deluxe Motherboard
	Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 70
	I/O ports at 9c00 [size=8]
	I/O ports at 9880 [size=4]
	I/O ports at 9800 [size=8]
	I/O ports at 9480 [size=4]
	I/O ports at 9400 [size=32]
	Memory at fb9fc000 (32-bit, non-prefetchable) [size=2K]
	Capabilities: [80] MSI: Enable+ Count=1/16 Maskable- 64bit-
	Capabilities: [70] Power Management version 3
	Capabilities: [a8] SATA HBA v1.0
	Capabilities: [b0] PCI Advanced Features
	Kernel driver in use: ahci
	Kernel modules: ahci

00:1f.3 SMBus: Intel Corporation 82801JI (ICH10 Family) SMBus Controller
	Subsystem: ASUSTeK Computer Inc. Device 82d4
	Flags: medium devsel, IRQ 14
	Memory at fb9fd000 (64-bit, non-prefetchable) [size=256]
	I/O ports at 1000 [size=32]
	Kernel modules: i2c-i801

01:00.0 SATA controller: Marvell Technology Group Ltd. 88SE9123 PCIe SATA 6.0 Gb/s controller (rev 11) (prog-if 01 [AHCI 1.0])
	Subsystem: ASUSTeK Computer Inc. Device 8438
	Flags: bus master, fast devsel, latency 0, IRQ 71
	I/O ports at bc00 [size=8]
	I/O ports at b880 [size=4]
	I/O ports at b800 [size=8]
	I/O ports at b480 [size=4]
	I/O ports at b400 [size=16]
	Memory at fbaff800 (32-bit, non-prefetchable) [size=2K]
	Expansion ROM at fbae0000 [disabled] [size=64K]
	Capabilities: [40] Power Management version 3
	Capabilities: [50] MSI: Enable+ Count=1/1 Maskable- 64bit-
	Capabilities: [70] Express Legacy Endpoint, MSI 00
	Capabilities: [100] Advanced Error Reporting
	Kernel driver in use: ahci
	Kernel modules: ahci

02:00.0 USB Controller: NEC Corporation uPD720200 USB 3.0 Host Controller (rev 03) (prog-if 30)
	Subsystem: ASUSTeK Computer Inc. Device 8413
	Flags: bus master, fast devsel, latency 0, IRQ 29
	Memory at fbbfe000 (64-bit, non-prefetchable) [size=8K]
	Capabilities: [50] Power Management version 3
	Capabilities: [70] MSI: Enable- Count=1/8 Maskable- 64bit+
	Capabilities: [90] MSI-X: Enable- Count=8 Masked-
	Capabilities: [a0] Express Endpoint, MSI 00
	Capabilities: [100] Advanced Error Reporting
	Capabilities: [140] Device Serial Number ff-ff-ff-ff-ff-ff-ff-ff
	Capabilities: [150] #18
	Kernel driver in use: xhci_hcd
	Kernel modules: xhci-hcd

03:00.0 VGA compatible controller: ATI Technologies Inc Device 6738 (prog-if 00 [VGA controller])
	Subsystem: Hightech Information System Ltd. Device 2010
	Flags: bus master, fast devsel, latency 0, IRQ 11
	Memory at d0000000 (64-bit, prefetchable) [size=256M]
	Memory at fbcc0000 (64-bit, non-prefetchable) [size=128K]
	I/O ports at c000 [size=256]
	Expansion ROM at fbca0000 [disabled] [size=128K]
	Capabilities: [50] Power Management version 3
	Capabilities: [58] Express Legacy Endpoint, MSI 00
	Capabilities: [a0] MSI: Enable- Count=1/1 Maskable- 64bit+
	Capabilities: [100] Vendor Specific Information: ID=0001 Rev=1 Len=010 <?>
	Capabilities: [150] Advanced Error Reporting

03:00.1 Audio device: ATI Technologies Inc Device aa88
	Subsystem: Hightech Information System Ltd. Device aa88
	Flags: bus master, fast devsel, latency 0, IRQ 73
	Memory at fbcfc000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: [50] Power Management version 3
	Capabilities: [58] Express Legacy Endpoint, MSI 00
	Capabilities: [a0] MSI: Enable+ Count=1/1 Maskable- 64bit+
	Capabilities: [100] Vendor Specific Information: ID=0001 Rev=1 Len=010 <?>
	Capabilities: [150] Advanced Error Reporting
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel

05:00.0 SATA controller: JMicron Technology Corp. JMB362 AHCI Controller (rev 10) (prog-if 01 [AHCI 1.0])
	Subsystem: ASUSTeK Computer Inc. Device 8460
	Flags: bus master, fast devsel, latency 0, IRQ 16
	I/O ports at dc00 [size=8]
	I/O ports at d880 [size=4]
	I/O ports at d800 [size=8]
	I/O ports at d480 [size=4]
	I/O ports at d400 [size=16]
	Memory at fbdffc00 (32-bit, non-prefetchable) [size=512]
	[virtual] Expansion ROM at c0400000 [disabled] [size=64K]
	Capabilities: [8c] Power Management version 3
	Capabilities: [50] Express Legacy Endpoint, MSI 00
	Kernel driver in use: ahci
	Kernel modules: ahci

07:01.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8110SC/8169SC Gigabit Ethernet (rev 10)
	Subsystem: ASUSTeK Computer Inc. Device 820d
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 19
	I/O ports at e800 [size=256]
	Memory at fbeffc00 (32-bit, non-prefetchable) [size=256]
	Expansion ROM at fbec0000 [disabled] [size=128K]
	Capabilities: [dc] Power Management version 2
	Capabilities: [60] Vital Product Data
	Kernel driver in use: r8169
	Kernel modules: r8169

07:02.0 FireWire (IEEE 1394): VIA Technologies, Inc. VT6306/7/8 [Fire II(M)] IEEE 1394 OHCI Controller (rev c0) (prog-if 10 [OHCI])
	Subsystem: ASUSTeK Computer Inc. M4A series motherboard
	Flags: bus master, medium devsel, latency 64, IRQ 18
	Memory at fbefe000 (32-bit, non-prefetchable) [size=2K]
	I/O ports at ec00 [size=128]
	Capabilities: [50] Power Management version 2
	Kernel driver in use: firewire_ohci
	Kernel modules: firewire-ohci, ohci1394

ff:00.0 Host bridge: Intel Corporation Xeon 5500/Core i7 QuickPath Architecture Generic Non-Core Registers (rev 05)
	Subsystem: Intel Corporation Device 8086
	Flags: bus master, fast devsel, latency 0

ff:00.1 Host bridge: Intel Corporation Xeon 5500/Core i7 QuickPath Architecture System Address Decoder (rev 05)
	Subsystem: Intel Corporation Device 8086
	Flags: bus master, fast devsel, latency 0

ff:02.0 Host bridge: Intel Corporation Xeon 5500/Core i7 QPI Link 0 (rev 05)
	Subsystem: Intel Corporation Device 8086
	Flags: bus master, fast devsel, latency 0

ff:02.1 Host bridge: Intel Corporation Xeon 5500/Core i7 QPI Physical 0 (rev 05)
	Subsystem: Intel Corporation Device 8086
	Flags: bus master, fast devsel, latency 0

ff:03.0 Host bridge: Intel Corporation Xeon 5500/Core i7 Integrated Memory Controller (rev 05)
	Subsystem: Intel Corporation Device 8086
	Flags: bus master, fast devsel, latency 0

ff:03.1 Host bridge: Intel Corporation Xeon 5500/Core i7 Integrated Memory Controller Target Address Decoder (rev 05)
	Subsystem: Intel Corporation Device 8086
	Flags: bus master, fast devsel, latency 0

ff:03.4 Host bridge: Intel Corporation Xeon 5500/Core i7 Integrated Memory Controller Test Registers (rev 05)
	Subsystem: Intel Corporation Device 8086
	Flags: bus master, fast devsel, latency 0

ff:04.0 Host bridge: Intel Corporation Xeon 5500/Core i7 Integrated Memory Controller Channel 0 Control Registers (rev 05)
	Subsystem: Intel Corporation Device 8086
	Flags: bus master, fast devsel, latency 0

ff:04.1 Host bridge: Intel Corporation Xeon 5500/Core i7 Integrated Memory Controller Channel 0 Address Registers (rev 05)
	Subsystem: Intel Corporation Device 8086
	Flags: bus master, fast devsel, latency 0

ff:04.2 Host bridge: Intel Corporation Xeon 5500/Core i7 Integrated Memory Controller Channel 0 Rank Registers (rev 05)
	Subsystem: Intel Corporation Device 8086
	Flags: bus master, fast devsel, latency 0

ff:04.3 Host bridge: Intel Corporation Xeon 5500/Core i7 Integrated Memory Controller Channel 0 Thermal Control Registers (rev 05)
	Subsystem: Intel Corporation Device 8086
	Flags: bus master, fast devsel, latency 0

ff:05.0 Host bridge: Intel Corporation Xeon 5500/Core i7 Integrated Memory Controller Channel 1 Control Registers (rev 05)
	Subsystem: Intel Corporation Device 8086
	Flags: bus master, fast devsel, latency 0

ff:05.1 Host bridge: Intel Corporation Xeon 5500/Core i7 Integrated Memory Controller Channel 1 Address Registers (rev 05)
	Subsystem: Intel Corporation Device 8086
	Flags: bus master, fast devsel, latency 0

ff:05.2 Host bridge: Intel Corporation Xeon 5500/Core i7 Integrated Memory Controller Channel 1 Rank Registers (rev 05)
	Subsystem: Intel Corporation Device 8086
	Flags: bus master, fast devsel, latency 0

ff:05.3 Host bridge: Intel Corporation Xeon 5500/Core i7 Integrated Memory Controller Channel 1 Thermal Control Registers (rev 05)
	Subsystem: Intel Corporation Device 8086
	Flags: bus master, fast devsel, latency 0

ff:06.0 Host bridge: Intel Corporation Xeon 5500/Core i7 Integrated Memory Controller Channel 2 Control Registers (rev 05)
	Subsystem: Intel Corporation Device 8086
	Flags: bus master, fast devsel, latency 0

ff:06.1 Host bridge: Intel Corporation Xeon 5500/Core i7 Integrated Memory Controller Channel 2 Address Registers (rev 05)
	Subsystem: Intel Corporation Device 8086
	Flags: bus master, fast devsel, latency 0

ff:06.2 Host bridge: Intel Corporation Xeon 5500/Core i7 Integrated Memory Controller Channel 2 Rank Registers (rev 05)
	Subsystem: Intel Corporation Device 8086
	Flags: bus master, fast devsel, latency 0

ff:06.3 Host bridge: Intel Corporation Xeon 5500/Core i7 Integrated Memory Controller Channel 2 Thermal Control Registers (rev 05)
	Subsystem: Intel Corporation Device 8086
	Flags: bus master, fast devsel, latency 0


```

Can anyone tell me what that means? Also, how do i tell what driver my system is using? And, where is it's configuration data if xorg.conf is gone? Thanks.

---

### Post by Lolpanda on 2011-04-28
As others have said. Around the time of 9.10 or 10.04 (I believe), Xorg was updated to automatically query HAL/udev for the hardware specs. Based off HAL/udev's response Xorg will automatically load what it believes is the correct driver.

Typically it gets it right, but every once and awhile it gets it wrong.

Xorg.conf has essentially been depreciated unless you use proprietary drivers since Xorg defaults to the community drivers.

If xorg.conf exists, Xorg will do whatever it says (even if its an impossible situation. like loading the Nvidia driver on an AMD card) , but if it doesn't, it just, essentially, best guesses the correct settings. 

On a seperate note... has anyone else been having problems with FGLRX not correctly picking screen resolution / refresh rate? For the last like 4 releases (11.04 included) fglrx always picks an out of range resolution and so my monitor says "Oops, can't display the specified video mode" until I specify it in xorg.conf

The above's not a help request, I know the solution, I'm just wondering if its affecting anyone else.

---

### Post by yanom on 2011-04-28
ok, so it's probably running off of the ATI driver. I tried specifing driver "fglrx" in the xorg.conf before I deleted it, but that didn't work. Now I have to get a working FGLRX install... but how?

---

### Post by Lolpanda on 2011-04-28
What actually HAPPENED when you installed FGLRX the first time? you said it reverted to commandline only but did it give an errors ("Cannot display this video mode/type/output")?

did you try running

```
startx
``` after hitting command line? That tells X to start, (go figure) and if its failing you'll get a nice long list of errors and hopefully why since you're actually viewing command line

---

### Post by yanom on 2011-04-28
> **Lolpanda said:**
> What actually HAPPENED when you installed FGLRX the first time? you said it reverted to commandline only but did it give an errors ("Cannot display this video mode/type/output")?

did you try running

```
startx
``` after hitting command line? That tells X to start, (go figure) and if its failing you'll get a nice long list of errors and hopefully why since you're actually viewing command line

startx gives error "no screens found" or something to that effect.

---

### Post by yanom on 2011-04-29
bump

---

### Post by Lolpanda on 2011-04-29
Install the propriatery drives again, before you reboot run

```
sudo aticonfig --initial
```

if it errors, try: ```
sudo aticonfig --initial -f
```

Reboot. Do you get a desktop this time? If not, login from command line. try ```
startx
``` again. If it fails with the same error then do

```
cd /etc/X11/

sudo mv xorg.conf xorg.conf.noscreens
```

That will rename your xorg.conf to xorg.conf.noscreens. Reboot. Find that file again under /etc/X11/ and post it here so we can try to figure out whats going wrong.

---

