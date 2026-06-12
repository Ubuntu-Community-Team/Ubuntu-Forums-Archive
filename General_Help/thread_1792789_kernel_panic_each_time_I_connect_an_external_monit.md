---
title: "kernel panic each time I connect an external monitor (fglrx)"
date: 2011-06-28
forum: General Help
---

### Post by gioby on 2011-06-28
Hello,
I have a freshly installed Ubuntu 11.04 on a laptop computer with an ATI card.

I have installed the latest ATI proprietary drivers 11-6 manually, by downloading them from the ATI website, creating .deb packages and installing them.

Everytime I connect an external monitor, the system seems to go into kernel panic. The laptop monitor becomes black; I can see the mouse cursor, but it does not move. The external monitor also remains black.
The system does not respond to any command, neither Alt-Ctrl-F1 nor the Elephants key.

I have looked at /var/log/syslog and /var/log/Xorg.log*, but none of these end with an error.

Any idea on how to proceed? I have looked in Internet, but it seems nobody is having the same problem.

---

### Post by Kollad on 2011-08-02
I have the same problem too. And i didn't find any solution also. One thing i can say, it's when monitor is plugged before power on the laptop, it works, but only in "mirror mode". Changing monitor settings cause system hang

---

### Post by dallgood on 2011-08-07
I get the same problem on my Toshiba Portege. Is there something I should do to try to diagnose the problem?

Below is my lspci:

```

lspci -v 
00:00.0 Host bridge: Intel Corporation 2nd Generation Core Processor Family DRAM Controller (rev 09)
    Subsystem: Toshiba America Info Systems Device 0001
    Flags: bus master, fast devsel, latency 0
    Capabilities: <access denied>
    Kernel driver in use: agpgart-intel

00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09) (prog-if 00 [VGA controller])
    Subsystem: Toshiba America Info Systems Device 0005
    Flags: bus master, fast devsel, latency 0, IRQ 48
    Memory at c0000000 (64-bit, non-prefetchable) [size=4M]
    Memory at b0000000 (64-bit, prefetchable) [size=256M]
    I/O ports at 3000 [size=64]
    Expansion ROM at <unassigned> [disabled]
    Capabilities: <access denied>
    Kernel driver in use: i915
    Kernel modules: i915

00:16.0 Communication controller: Intel Corporation 6 Series Chipset Family MEI Controller #1 (rev 04)
    Subsystem: Toshiba America Info Systems Device 0001
    Flags: bus master, fast devsel, latency 0, IRQ 11
    Memory at c4824000 (64-bit, non-prefetchable) [size=16]
    Capabilities: <access denied>

00:19.0 Ethernet controller: Intel Corporation 82579V Gigabit Network Connection (rev 04)
    Subsystem: Toshiba America Info Systems Device 0001
    Flags: bus master, fast devsel, latency 0, IRQ 49
    Memory at c4800000 (32-bit, non-prefetchable) [size=128K]
    Memory at c482a000 (32-bit, non-prefetchable) [size=4K]
    I/O ports at 3060 [size=32]
    Capabilities: <access denied>
    Kernel driver in use: e1000e
    Kernel modules: e1000e

00:1a.0 USB Controller: Intel Corporation 6 Series Chipset Family USB Enhanced Host Controller #2 (rev 04) (prog-if 20 [EHCI])
    Subsystem: Toshiba America Info Systems Device 0001
    Flags: bus master, medium devsel, latency 0, IRQ 16
    Memory at c4829000 (32-bit, non-prefetchable) [size=1K]
    Capabilities: <access denied>
    Kernel driver in use: ehci_hcd

00:1b.0 Audio device: Intel Corporation 6 Series Chipset Family High Definition Audio Controller (rev 04)
    Subsystem: Toshiba America Info Systems Device 0001
    Flags: bus master, fast devsel, latency 0, IRQ 40
    Memory at c4820000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel

00:1c.0 PCI bridge: Intel Corporation 6 Series Chipset Family PCI Express Root Port 1 (rev b4) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
    Memory behind bridge: c4700000-c47fffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1c.1 PCI bridge: Intel Corporation 6 Series Chipset Family PCI Express Root Port 2 (rev b4) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=02, subordinate=03, sec-latency=0
    I/O behind bridge: 00002000-00002fff
    Memory behind bridge: c2700000-c46fffff
    Prefetchable memory behind bridge: 00000000c0400000-00000000c23fffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1c.2 PCI bridge: Intel Corporation 6 Series Chipset Family PCI Express Root Port 3 (rev b4) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=04, subordinate=04, sec-latency=0
    Memory behind bridge: c2600000-c26fffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1c.4 PCI bridge: Intel Corporation 6 Series Chipset Family PCI Express Root Port 5 (rev b4) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=05, subordinate=05, sec-latency=0
    Memory behind bridge: c2500000-c25fffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1c.5 PCI bridge: Intel Corporation 6 Series Chipset Family PCI Express Root Port 6 (rev b4) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=06, subordinate=06, sec-latency=0
    I/O behind bridge: 00004000-00004fff
    Memory behind bridge: c2400000-c24fffff
    Prefetchable memory behind bridge: 00000000afb00000-00000000afcfffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1c.6 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev b4) (prog-if 01 [Subtractive decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=07, subordinate=07, sec-latency=0
    Capabilities: <access denied>

00:1d.0 USB Controller: Intel Corporation 6 Series Chipset Family USB Enhanced Host Controller #1 (rev 04) (prog-if 20 [EHCI])
    Subsystem: Toshiba America Info Systems Device 0001
    Flags: bus master, medium devsel, latency 0, IRQ 23
    Memory at c4828000 (32-bit, non-prefetchable) [size=1K]
    Capabilities: <access denied>
    Kernel driver in use: ehci_hcd

00:1f.0 ISA bridge: Intel Corporation HM65 Express Chipset Family LPC Controller (rev 04)
    Subsystem: Toshiba America Info Systems Device 0001
    Flags: bus master, medium devsel, latency 0
    Capabilities: <access denied>
    Kernel modules: iTCO_wdt

00:1f.2 SATA controller: Intel Corporation 6 Series Chipset Family 6 port SATA AHCI Controller (rev 04) (prog-if 01 [AHCI 1.0])
    Subsystem: Toshiba America Info Systems Device 0001
    Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 46
    I/O ports at 3088 [size=8]
    I/O ports at 309c [size=4]
    I/O ports at 3080 [size=8]
    I/O ports at 3098 [size=4]
    I/O ports at 3040 [size=32]
    Memory at c4827000 (32-bit, non-prefetchable) [size=2K]
    Capabilities: <access denied>
    Kernel driver in use: ahci
    Kernel modules: ahci

01:00.0 System peripheral: Ricoh Co Ltd Device e823 (rev 04) (prog-if 01)
    Subsystem: Toshiba America Info Systems Device 0001
    Flags: bus master, fast devsel, latency 0, IRQ 16
    Memory at c4700000 (32-bit, non-prefetchable) [size=256]
    Capabilities: <access denied>
    Kernel driver in use: sdhci-pci
    Kernel modules: sdhci-pci

04:00.0 Network controller: Intel Corporation Centrino Wireless-N 1000
    Subsystem: Intel Corporation Centrino Wireless-N 1000 BGN
    Flags: bus master, fast devsel, latency 0, IRQ 47
    Memory at c2600000 (64-bit, non-prefetchable) [size=8K]
    Capabilities: <access denied>
    Kernel driver in use: iwlagn
    Kernel modules: iwlagn

05:00.0 USB Controller: NEC Corporation uPD720200 USB 3.0 Host Controller (rev 04) (prog-if 30 [XHCI])
    Subsystem: Toshiba America Info Systems Device 0001
    Flags: bus master, fast devsel, latency 0, IRQ 16
    Memory at c2500000 (64-bit, non-prefetchable) [size=8K]
    Capabilities: <access denied>
    Kernel driver in use: xhci_hcd
    Kernel modules: xhci-hcd



```

---

