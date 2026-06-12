---
title: "No sound : *("
date: 2010-02-24
forum: General Help
---

### Post by skoalman88 on 2010-02-24
I am getting no sound after upgrading to 9.10 Below is the lspci-v output.

Thanks


lspci -v

00:00.0 Host bridge: Intel Corporation 82945G/GZ/P/PL Memory Controller Hub (rev 02)

	Subsystem: Elitegroup Computer Systems Device 1b76

	Flags: bus master, fast devsel, latency 0

	Capabilities: <access denied>

	Kernel driver in use: agpgart-intel

	Kernel modules: intel-agp



00:02.0 VGA compatible controller: Intel Corporation 82945G/GZ Integrated Graphics Controller (rev 02)

	Subsystem: Elitegroup Computer Systems Device 1b76

	Flags: bus master, fast devsel, latency 0, IRQ 16

	Memory at fdf00000 (32-bit, non-prefetchable) [size=512K]

	I/O ports at ff00 [size=8]

	Memory at d0000000 (32-bit, prefetchable) [size=256M]

	Memory at fdf80000 (32-bit, non-prefetchable) [size=256K]

	Capabilities: <access denied>

	Kernel modules: intelfb



00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)

	Subsystem: Elitegroup Computer Systems Device 2932

	Flags: bus master, fast devsel, latency 0, IRQ 16

	Memory at fdff8000 (64-bit, non-prefetchable) [size=16K]

	Capabilities: <access denied>

	Kernel driver in use: HDA Intel

	Kernel modules: snd-hda-intel



00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 01)

	Subsystem: Elitegroup Computer Systems Device 1b76

	Flags: bus master, medium devsel, latency 0, IRQ 23

	I/O ports at fe00 [size=32]

	Kernel driver in use: uhci_hcd



00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 01)

	Subsystem: Elitegroup Computer Systems Device 1b76

	Flags: bus master, medium devsel, latency 0, IRQ 19

	I/O ports at fd00 [size=32]

	Kernel driver in use: uhci_hcd



00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 01)

	Subsystem: Elitegroup Computer Systems Device 1b76

	Flags: bus master, medium devsel, latency 0, IRQ 18

	I/O ports at fc00 [size=32]

	Kernel driver in use: uhci_hcd



00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 01)

	Subsystem: Elitegroup Computer Systems Device 1b76

	Flags: bus master, medium devsel, latency 0, IRQ 16

	I/O ports at fb00 [size=32]

	Kernel driver in use: uhci_hcd



00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01) (prog-if 20)

	Subsystem: Elitegroup Computer Systems Device 1b76

	Flags: bus master, medium devsel, latency 0, IRQ 23

	Memory at fdfff000 (32-bit, non-prefetchable) [size=1K]

	Capabilities: <access denied>

	Kernel driver in use: ehci_hcd



00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1) (prog-if 01)

	Flags: bus master, fast devsel, latency 0

	Bus: primary=00, secondary=01, subordinate=01, sec-latency=32

	I/O behind bridge: 0000e000-0000efff

	Memory behind bridge: fde00000-fdefffff

	Prefetchable memory behind bridge: 00000000fdd00000-00000000fddfffff

	Capabilities: <access denied>



00:1f.0 ISA bridge: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge (rev 01)

	Subsystem: Elitegroup Computer Systems Device 1b76

	Flags: bus master, medium devsel, latency 0

	Capabilities: <access denied>

	Kernel modules: iTCO_wdt, intel-rng



00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01) (prog-if 8a [Master SecP PriP])

	Subsystem: Elitegroup Computer Systems Device 1b76

	Flags: bus master, medium devsel, latency 0, IRQ 18

	I/O ports at 01f0 [size=8]

	I/O ports at 03f4 [size=1]

	I/O ports at 0170 [size=8]

	I/O ports at 0374 [size=1]

	I/O ports at fa00 [size=16]

	Kernel driver in use: ata_piix



00:1f.2 IDE interface: Intel Corporation 82801GB/GR/GH (ICH7 Family) SATA IDE Controller (rev 01) (prog-if 8f [Master SecP SecO PriP PriO])

	Subsystem: Elitegroup Computer Systems Device 1b76

	Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 19

	I/O ports at f900 [size=8]

	I/O ports at f800 [size=4]

	I/O ports at f700 [size=8]

	I/O ports at f600 [size=4]

	I/O ports at f500 [size=16]

	Capabilities: <access denied>

	Kernel driver in use: ata_piix



00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)

	Subsystem: Elitegroup Computer Systems Device 1b76

	Flags: medium devsel, IRQ 15

	I/O ports at 0500 [size=32]

	Kernel modules: i2c-i801



01:03.0 Communication controller: Conexant Systems, Inc. Device 2f40

	Subsystem: Conexant Systems, Inc. Device 2000

	Flags: bus master, medium devsel, latency 32, IRQ 11

	Memory at fdee0000 (32-bit, non-prefetchable) [size=64K]

	I/O ports at ef00 [size=8]

	Capabilities: <access denied>



01:05.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)

	Subsystem: Elitegroup Computer Systems Device 8139

	Flags: bus master, medium devsel, latency 32, IRQ 20

	I/O ports at ec00 [size=256]

	Memory at fdeff000 (32-bit, non-prefetchable) [size=256]

	Capabilities: <access denied>

	Kernel driver in use: 8139too

	Kernel modules: 8139too, 8139cp

---

### Post by mörgæs on 2010-02-25
[https://wiki.ubuntu.com/DebuggingSoundProblems/KarmicCaveats](https://wiki.ubuntu.com/DebuggingSoundProblems/KarmicCaveats)

- or just stay with your previous version of Ubuntu :-)

---

