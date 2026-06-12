---
title: "Screen resolution messed up in Wubi"
date: 2012-01-21
forum: General Help
---

### Post by kvvv on 2012-01-21
Hi,

I just installed the Xubuntu version of Wubi on this laptop, and the screen resolution is messed up.

When I do  "xrandr -q", the maximum resolution that shows up is 1024 x 768, when I believe it should be 1280 x 800 or something. As a result, everything on my screen is stretched out horizontally.

Any idea how I can fix this?


Output of lspci

```

00:00.0 Host bridge: Silicon Integrated Systems [SiS] 671MX
    Subsystem: ASUSTeK Computer Inc. Device 181c
    Flags: bus master, medium devsel, latency 64
    Memory at f0000000 (32-bit, non-prefetchable) [size=128M]
    Capabilities: <access denied>
    Kernel driver in use: agpgart-sis
    Kernel modules: sis-agp

00:01.0 PCI bridge: Silicon Integrated Systems [SiS] AGP Port (virtual PCI-to-PCI bridge) (prog-if 00 [Normal decode])
    Flags: bus master, 66MHz, fast devsel, latency 0
    Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
    I/O behind bridge: 0000d000-0000dfff
    Memory behind bridge: fd600000-fd6fffff
    Prefetchable memory behind bridge: c0000000-cfffffff
    Kernel modules: shpchp

00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS968 [MuTIOL Media IO] (rev 01)
    Subsystem: ASUSTeK Computer Inc. Device 181c
    Flags: bus master, medium devsel, latency 0

00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE] (rev 01) (prog-if 80 [Master])
    Subsystem: ASUSTeK Computer Inc. Device 181c
    Flags: bus master, medium devsel, latency 128
    I/O ports at 01f0 [size=8]
    I/O ports at 03f4 [size=1]
    I/O ports at 0170 [size=8]
    I/O ports at 0374 [size=1]
    I/O ports at ffe0 [size=16]
    Capabilities: <access denied>
    Kernel driver in use: pata_sis

00:03.0 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f) (prog-if 10 [OHCI])
    Subsystem: ASUSTeK Computer Inc. Device 181c
    Flags: bus master, medium devsel, latency 64, IRQ 20
    Memory at fd5ff000 (32-bit, non-prefetchable) [size=4K]
    Kernel driver in use: ohci_hcd

00:03.1 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f) (prog-if 10 [OHCI])
    Subsystem: ASUSTeK Computer Inc. Device 181c
    Flags: bus master, medium devsel, latency 64, IRQ 21
    Memory at fd5fe000 (32-bit, non-prefetchable) [size=4K]
    Kernel driver in use: ohci_hcd

00:03.3 USB Controller: Silicon Integrated Systems [SiS] USB 2.0 Controller (prog-if 20 [EHCI])
    Subsystem: ASUSTeK Computer Inc. Device 181c
    Flags: bus master, medium devsel, latency 64, IRQ 22
    Memory at fd5fd000 (32-bit, non-prefetchable) [size=4K]
    Capabilities: <access denied>
    Kernel driver in use: ehci_hcd

00:04.0 Ethernet controller: Silicon Integrated Systems [SiS] 191 Gigabit Ethernet Adapter (rev 02)
    Subsystem: ASUSTeK Computer Inc. Device 181c
    Flags: bus master, medium devsel, latency 0, IRQ 19
    Memory at fd5fcc00 (32-bit, non-prefetchable) [size=128]
    I/O ports at cc00 [size=128]
    Capabilities: <access denied>
    Kernel driver in use: sis190
    Kernel modules: sis190

00:05.0 IDE interface: Silicon Integrated Systems [SiS] SATA Controller / IDE mode (rev 03) (prog-if 85 [Master SecO PriO])
    Subsystem: ASUSTeK Computer Inc. Device 181c
    Flags: bus master, medium devsel, latency 64, IRQ 17
    I/O ports at c800 [size=8]
    I/O ports at c400 [size=4]
    I/O ports at c000 [size=8]
    I/O ports at bc00 [size=4]
    I/O ports at b800 [size=16]
    I/O ports at b400 [size=128]
    Capabilities: <access denied>
    Kernel driver in use: sata_sis
    Kernel modules: sata_sis

00:06.0 PCI bridge: Silicon Integrated Systems [SiS] PCI-to-PCI bridge (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
    Memory behind bridge: fd700000-fd7fffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:07.0 PCI bridge: Silicon Integrated Systems [SiS] PCI-to-PCI bridge (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=03, subordinate=05, sec-latency=0
    Memory behind bridge: fd800000-fe3fffff
    Prefetchable memory behind bridge: 00000000de000000-00000000dfffffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:0d.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev b4)
    Subsystem: ASUSTeK Computer Inc. Device 181c
    Flags: bus master, medium devsel, latency 168, IRQ 17
    Memory at d4000000 (32-bit, non-prefetchable) [size=4K]
    Bus: primary=00, secondary=06, subordinate=09, sec-latency=176
    Memory window 0: bc000000-bffff000 (prefetchable)
    Memory window 1: d0000000-d3fff000
    I/O window 0: 00001000-000010ff
    I/O window 1: 00001400-000014ff
    16-bit legacy interface ports at 0001
    Kernel driver in use: yenta_cardbus
    Kernel modules: yenta_socket

00:0d.1 FireWire (IEEE 1394): Ricoh Co Ltd R5C552 IEEE 1394 Controller (rev 09) (prog-if 10 [OHCI])
    Subsystem: ASUSTeK Computer Inc. Device 181c
    Flags: bus master, medium devsel, latency 64, IRQ 18
    Memory at fd5fc000 (32-bit, non-prefetchable) [size=2K]
    Capabilities: <access denied>
    Kernel driver in use: firewire_ohci
    Kernel modules: firewire-ohci

00:0d.2 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 18)
    Subsystem: ASUSTeK Computer Inc. Device 181c
    Flags: bus master, medium devsel, latency 64, IRQ 19
    Memory at fd5fc800 (32-bit, non-prefetchable) [size=256]
    Capabilities: <access denied>
    Kernel driver in use: sdhci-pci
    Kernel modules: sdhci-pci

00:0d.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 09)
    Subsystem: ASUSTeK Computer Inc. Device 181c
    Flags: medium devsel, IRQ 19
    Memory at fd5f7800 (32-bit, non-prefetchable) [size=256]
    Capabilities: <access denied>
    Kernel driver in use: r592
    Kernel modules: r592

00:0f.0 Audio device: Silicon Integrated Systems [SiS] Azalia Audio Controller
    Subsystem: ASUSTeK Computer Inc. Device 1339
    Flags: bus master, medium devsel, latency 0, IRQ 18
    Memory at fd5f0000 (32-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel

01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 771/671 PCIE VGA Display Adapter (rev 10) (prog-if 00 [VGA controller])
    Subsystem: ASUSTeK Computer Inc. Device 181c
    Flags: 66MHz, medium devsel, IRQ 10
    BIST result: 00
    Memory at c0000000 (32-bit, prefetchable) [size=256M]
    Memory at fd6e0000 (32-bit, non-prefetchable) [size=128K]
    I/O ports at dc00 [size=128]
    Expansion ROM at <unassigned> [disabled]
    Capabilities: <access denied>

02:00.0 Ethernet controller: Atheros Communications Inc. AR242x / AR542x Wireless Network Adapter (PCI-Express) (rev 01)
    Subsystem: AzureWave AR5007EG 802.11bg Wi-Fi mini PCI express card
    Flags: bus master, fast devsel, latency 0, IRQ 18
    Memory at fd7f0000 (64-bit, non-prefetchable) [size=64K]
    Capabilities: <access denied>
    Kernel driver in use: ath5k
    Kernel modules: ath5k



```

---

### Post by kvvv on 2012-01-22
Bump :\

This worked for me:
[http://ubuntuforums.org/showpost.php?p=11357732&postcount=750](http://ubuntuforums.org/showpost.php?p=11357732&postcount=750)

---

