---
title: "Aspir one D255"
date: 2011-05-29
forum: General Help
---

### Post by newtoalldis on 2011-05-29
OK so Ubuntu is installed but I have neither wired or wireless connectivity.

Can anyone please help before I commit the 'return to windows' sin..?

Thx

---

### Post by MoebusNet on 2011-05-29
I haven't tried installing any Linux OS's to my Acer Aspire One D255-2301's hard drive, but Mint 10, Lubuntu 11.04, and Puppy Linux all work well as Live-USB OS's for me.

---

### Post by sbraz on 2011-05-29
which version of ubuntu? :)

did your network cards work when you were in "live" mode after booting from usb?

please post the results of the command **sudo lspci -v**. you have to run this command from a terminal.

---

### Post by newtoalldis on 2011-05-30
Apologies - Lucid linux

I am at work right now and am unable to access to the too quick.
I will paste the results in a few hours (I hope!)

Live mode was not applied - I bought the machine with Meego installed, but the OS was replaced with Ubuntu by the shop.

---

### Post by iclestu on 2011-05-30
> **newtoalldis said:**
> ........ but the OS was replaced with Ubuntu by the shop.

Can't you just take it back to the shop? Im sure peeps here can help but if you are PAYING for a service... I'd have it back at the shop

---

### Post by newtoalldis on 2011-05-30
This is Thailand - may be easier to get help on here...

---

### Post by newtoalldis on 2011-05-30
Host bridge: Intel Corporation N10 Family DMI Bridge
	Subsystem: Acer Incorporated [ALI] Device 0349
	Flags: bus master, fast devsel, latency 0
	Capabilities: [e0] Vendor Specific Information <?>
	Kernel driver in use: agpgart-intel
	Kernel modules: intel-agp

00:02.0 VGA compatible controller: Intel Corporation N10 Family Integrated Graphics Controller
	Subsystem: Acer Incorporated [ALI] Device 0349
	Flags: bus master, fast devsel, latency 0, IRQ 27
	Memory at 58180000 (32-bit, non-prefetchable) [size=512K]
	I/O ports at 60c0 [size=8]
	Memory at 40000000 (32-bit, prefetchable) [size=256M]
	Memory at 58000000 (32-bit, non-prefetchable) [size=1M]
	Capabilities: [90] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable+
	Capabilities: [d0] Power Management version 2
	Kernel driver in use: i915
	Kernel modules: i915

00:02.1 Display controller: Intel Corporation N10 Family Integrated Graphics Controller
	Subsystem: Acer Incorporated [ALI] Device 0349
	Flags: bus master, fast devsel, latency 0
	Memory at 58100000 (32-bit, non-prefetchable) [size=512K]
	Capabilities: [d0] Power Management version 2

00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 02)
	Subsystem: Acer Incorporated [ALI] Device 0349
	Flags: bus master, fast devsel, latency 0, IRQ 19
	Memory at 58200000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: [50] Power Management version 2
	Capabilities: [60] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
	Capabilities: [70] Express Root Complex Integrated Endpoint, MSI 00
	Capabilities: [100] Virtual Channel <?>
	Capabilities: [130] Root Complex Link <?>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel

00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 02)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
	I/O behind bridge: 00005000-00005fff
	Memory behind bridge: 57000000-57ffffff
	Prefetchable memory behind bridge: 0000000050000000-0000000050ffffff
	Capabilities: [40] Express Root Port (Slot+), MSI 00
	Capabilities: [80] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable+
	Capabilities: [90] Subsystem: Acer Incorporated [ALI] Device 0349
	Capabilities: [a0] Power Management version 2
	Capabilities: [100] Virtual Channel <?>
	Capabilities: [180] Root Complex Link <?>
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:1c.1 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 2 (rev 02)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
	I/O behind bridge: 00004000-00004fff
	Memory behind bridge: 56000000-56ffffff
	Prefetchable memory behind bridge: 0000000051000000-0000000051ffffff
	Capabilities: [40] Express Root Port (Slot+), MSI 00
	Capabilities: [80] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable+
	Capabilities: [90] Subsystem: Acer Incorporated [ALI] Device 0349
	Capabilities: [a0] Power Management version 2
	Capabilities: [100] Virtual Channel <?>
	Capabilities: [180] Root Complex Link <?>
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:1d.0 USB Controller: Intel Corporation N10/ICH7 Family USB UHCI Controller #1 (rev 02)
	Subsystem: Acer Incorporated [ALI] Device 0349
	Flags: bus master, medium devsel, latency 0, IRQ 18
	I/O ports at 6080 [size=32]
	Kernel driver in use: uhci_hcd

00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 02)
	Subsystem: Acer Incorporated [ALI] Device 0349
	Flags: bus master, medium devsel, latency 0, IRQ 20
	I/O ports at 6060 [size=32]
	Kernel driver in use: uhci_hcd

00:1d.2 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 02)
	Subsystem: Acer Incorporated [ALI] Device 0349
	Flags: bus master, medium devsel, latency 0, IRQ 21
	I/O ports at 6040 [size=32]
	Kernel driver in use: uhci_hcd

00:1d.3 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 02)
	Subsystem: Acer Incorporated [ALI] Device 0349
	Flags: bus master, medium devsel, latency 0, IRQ 22
	I/O ports at 6020 [size=32]
	Kernel driver in use: uhci_hcd

00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 02) (prog-if 20)
	Subsystem: Acer Incorporated [ALI] Device 0349
	Flags: bus master, medium devsel, latency 0, IRQ 22
	Memory at 58204400 (32-bit, non-prefetchable) [size=1K]
	Capabilities: [50] Power Management version 2
	Capabilities: [58] Debug port: BAR=1 offset=00a0
	Kernel driver in use: ehci_hcd

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2) (prog-if 01)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=05, subordinate=05, sec-latency=32
	Capabilities: [50] Subsystem: Acer Incorporated [ALI] Device 0349

00:1f.0 ISA bridge: Intel Corporation NM10 Family LPC Controller (rev 02)
	Subsystem: Acer Incorporated [ALI] Device 0349
	Flags: bus master, medium devsel, latency 0
	Capabilities: [e0] Vendor Specific Information <?>

00:1f.2 SATA controller: Intel Corporation N10/ICH7 Family SATA AHCI Controller (rev 02) (prog-if 01)
	Subsystem: Acer Incorporated [ALI] Device 0349
	Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 26
	I/O ports at 60b8 [size=8]
	I/O ports at 60cc [size=4]
	I/O ports at 60b0 [size=8]
	I/O ports at 60c8 [size=4]
	I/O ports at 60a0 [size=16]
	Memory at 58204000 (32-bit, non-prefetchable) [size=1K]
	Capabilities: [80] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable+
	Capabilities: [70] Power Management version 2
	Kernel driver in use: ahci
	Kernel modules: ahci

00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 02)
	Subsystem: Acer Incorporated [ALI] Device 0349
	Flags: medium devsel, IRQ 10
	I/O ports at 6000 [size=32]
	Kernel modules: i2c-i801

01:00.0 Ethernet controller: Atheros Communications AR8152 v1.1 Fast Ethernet (rev c1)
	Subsystem: Acer Incorporated [ALI] Device 0349
	Flags: bus master, fast devsel, latency 0, IRQ 11
	Memory at 57000000 (64-bit, non-prefetchable) [size=256K]
	I/O ports at 5000 [size=128]
	Capabilities: [40] Power Management version 3
	Capabilities: [48] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
	Capabilities: [58] Express Endpoint, MSI 00
	Capabilities: [6c] Vital Product Data <?>
	Capabilities: [100] Advanced Error Reporting <?>
	Capabilities: [180] Device Serial Number ff-08-75-1c-9f-76-c4-ff

02:00.0 Network controller: Broadcom Corporation Device 4727 (rev 01)
	Subsystem: Broadcom Corporation Device 0510
	Flags: bus master, fast devsel, latency 0, IRQ 10
	Memory at 56000000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: [40] Power Management version 3
	Capabilities: [58] Vendor Specific Information <?>
	Capabilities: [48] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
	Capabilities: [d0] Express Endpoint, MSI 00
	Capabilities: [100] Advanced Error Reporting <?>
	Capabilities: [13c] Virtual Channel <?>
	Capabilities: [160] Device Serial Number 9f-88-42-ff-ff-fa-00-00
	Capabilities: [16c] Power Budgeting <?>

---

### Post by sbraz on 2011-05-30
it seems both wired and wlan doesn't have a driver installed, i had similar problems with lucid months ago.

a kernel upgrade might solve the problem about the wired card, as lucid uses a fairly old kernel 2.6.32 by default. installing a new kernel from a repository might be a problem if as of now it can't connect to the internet. compiling a new one seems to me a bit out of the scope of this topic.

a viable option could be borrowing a usb wireless/wired card supported by your current kernel, install the latest kernel available from ppa to restore wired network functionality, then work your way out from there.

you could also install the newer ubuntu 10.10 or 11.04 which should work out of the box with the exception of the wireless card which might require to download a proprietary driver to work using the "additional drivers" administration tool (not linux's fault, opensource drivers for broad are currently being developed).

> Can't you just take it back to the shop?
i agree. it's an issue not seen by whoever installed the os: if there's no network connection available means that the os were just installed without cheching if everything worked and/or if there were updates for the os.
since you paid for a _working_ computer it's your right to receive assistance.

---

### Post by newtoalldis on 2011-05-30
I am installing 11.04 as I type

Tested the live cd and all is 100% - fingers crossed..!

---

### Post by newtoalldis on 2011-05-30
Mind you it's taking a looooooong time to Save Installed Packages!

Maybe should not have done upgrade - just a new install?

---

### Post by sbraz on 2011-05-30
> **newtoalldis said:**
> Maybe should not have done upgrade - just a new install?

maybe a clean install would have been a wiser choice but it is very possible that the upgrade is cool too. :)

---

