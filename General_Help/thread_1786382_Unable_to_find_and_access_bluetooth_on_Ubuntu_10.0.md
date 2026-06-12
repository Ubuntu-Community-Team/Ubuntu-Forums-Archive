---
title: "Unable to find and access bluetooth on Ubuntu 10.04"
date: 2011-06-19
forum: General Help
---

### Post by samvedan on 2011-06-19
I was able to see the bluetooth icon in notification area and it was working. Today i noticed that it is not there and when i am trying to open bluetooth from System -> preferences, it shows the note--- No bluetooth adapter present; your computer doesnot have bluetooth adapters plugged in.  When i open bluetooth manager , the note comes ---- bluez daemon is not running.

When i run the command --- lspci -v on terminal, the following things come up:

[I]00:00.0 Host bridge: Intel Corporation N10 Family DMI Bridge
    Subsystem: Dell Device 048e
    Flags: bus master, fast devsel, latency 0
    Capabilities: <access denied>
    Kernel driver in use: agpgart-intel
    Kernel modules: intel-agp

00:02.0 VGA compatible controller: Intel Corporation N10 Family Integrated Graphics Controller
    Subsystem: Dell Device 048e
    Flags: bus master, fast devsel, latency 0, IRQ 28
    Memory at f0200000 (32-bit, non-prefetchable) [size=512K]
    I/O ports at 18d0 [size=8]
    Memory at d0000000 (32-bit, prefetchable) [size=256M]
    Memory at f0000000 (32-bit, non-prefetchable) [size=1M]
    Capabilities: <access denied>
    Kernel driver in use: i915
    Kernel modules: i915

00:02.1 Display controller: Intel Corporation N10 Family Integrated Graphics Controller
    Subsystem: Dell Device 048e
    Flags: bus master, fast devsel, latency 0
    Memory at f0280000 (32-bit, non-prefetchable) [size=512K]
    Capabilities: <access denied>

00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 02)
    Subsystem: Dell Device 048e
    Flags: bus master, fast devsel, latency 0, IRQ 22
    Memory at f0300000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel

00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 02)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=05, subordinate=05, sec-latency=0
    I/O behind bridge: 00002000-00002fff
    Memory behind bridge: 80000000-803fffff
    Prefetchable memory behind bridge: 00000000f0f00000-00000000f0ffffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1c.1 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 2 (rev 02)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=07, subordinate=07, sec-latency=0
    I/O behind bridge: 00003000-00003fff
    Memory behind bridge: f0100000-f01fffff
    Prefetchable memory behind bridge: 0000000080400000-00000000805fffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1d.0 USB Controller: Intel Corporation N10/ICH7 Family USB UHCI Controller #1 (rev 02)
    Subsystem: Dell Device 048e
    Flags: bus master, medium devsel, latency 0, IRQ 23
    I/O ports at 1820 [size=32]
    Kernel driver in use: uhci_hcd

00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 02)
    Subsystem: Dell Device 048e
    Flags: bus master, medium devsel, latency 0, IRQ 19
    I/O ports at 1840 [size=32]
    Kernel driver in use: uhci_hcd

00:1d.2 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 02)
    Subsystem: Dell Device 048e
    Flags: bus master, medium devsel, latency 0, IRQ 18
    I/O ports at 1860 [size=32]
    Kernel driver in use: uhci_hcd

00:1d.3 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 02)
    Subsystem: Dell Device 048e
    Flags: bus master, medium devsel, latency 0, IRQ 16
    I/O ports at 1880 [size=32]
    Kernel driver in use: uhci_hcd

00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 02) (prog-if 20)
    Subsystem: Dell Device 048e
    Flags: bus master, medium devsel, latency 0, IRQ 23
    Memory at f0504000 (32-bit, non-prefetchable) [size=1K]
    Capabilities: <access denied>
    Kernel driver in use: ehci_hcd

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2) (prog-if 01)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=11, subordinate=11, sec-latency=32
    Capabilities: <access denied>

00:1f.0 ISA bridge: Intel Corporation NM10 Family LPC Controller (rev 02)
    Subsystem: Dell Device 048e
    Flags: bus master, medium devsel, latency 0
    Capabilities: <access denied>

00:1f.2 SATA controller: Intel Corporation N10/ICH7 Family SATA AHCI Controller (rev 02) (prog-if 01)
    Subsystem: Dell Device 048e
    Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 26
    I/O ports at 18e8 [size=8]
    I/O ports at 18dc [size=4]
    I/O ports at 18e0 [size=8]
    I/O ports at 18d8 [size=4]
    I/O ports at 18c0 [size=16]
    Memory at f0504400 (32-bit, non-prefetchable) [size=1K]
    Capabilities: <access denied>
    Kernel driver in use: ahci
    Kernel modules: ahci

00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 02)
    Subsystem: Dell Device 048e
    Flags: medium devsel, IRQ 10
    I/O ports at 18a0 [size=32]
    Kernel modules: i2c-i801

05:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 05)
    Subsystem: Dell Device 048e
    Flags: bus master, fast devsel, latency 0, IRQ 27
    I/O ports at 2000 [size=256]
    Memory at f0f2c000 (64-bit, prefetchable) [size=4K]
    Memory at f0f18000 (64-bit, prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: r8169
    Kernel modules: r8169

07:00.0 Network controller: Realtek Semiconductor Co., Ltd. Device 8176 (rev 01)
    Subsystem: Dell Device 9198
    Flags: bus master, fast devsel, latency 0, IRQ 4
    I/O ports at 3000 [size=256]
    Memory at f0100000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel modules: r8192ce_pci
[/I]
Please help me to locate bluetooth or the probleam and how did it arise in my mini laptop?

---

