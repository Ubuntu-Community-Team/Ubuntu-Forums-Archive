---
title: "Clocksource tsc unstable on Ubuntu 10.04"
date: 2010-05-28
forum: General Help
---

### Post by Kurdistan on 2010-05-28
Hey I newly made clean installation of Ubuntu 10.04 and I previews had Ubuntu 9.10 installed. When I made clean installation of Ubuntu 10.04 and looked into syslog, dmesg and kern.log I could see clocksource tsc unstable and CE: hpet increasing min_delta_ns. In every boot. Help  appreciated!

Here is some information:

dmesg:
```
[    0.176965] ACPI: Interpreter enabled
[    0.176974] ACPI: (supports S0 S3 S4 S5)
[    0.176998] ACPI: Using IOAPIC for interrupt routing
[    0.180063] [Firmware Bug]: ACPI: ACPI brightness control misses _BQC function
[    0.183061] ACPI: Power Resource [FN10] (off)
[    0.183508] ACPI: Power Resource [FN11] (off)
[    0.183909] ACPI: No dock devices found.
[    0.184051] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.184358] pci 0000:00:02.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.184363] pci 0000:00:02.0: PME# disabled
[    0.184406] pci 0000:00:03.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.184410] pci 0000:00:03.0: PME# disabled
[    0.184452] pci 0000:00:04.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.184456] pci 0000:00:04.0: PME# disabled
[    0.184711] pci 0000:00:0a.1: reg 20 io port: [0x3040-0x307f]
[    0.184718] pci 0000:00:0a.1: reg 24 io port: [0x3000-0x303f]
[    0.184743] pci 0000:00:0a.1: PME# supported from D3hot D3cold
[    0.184750] pci 0000:00:0a.1: PME# disabled
[    0.184786] pci 0000:00:0a.3: reg 10 32bit mmio: [0xc0040000-0xc007ffff]
[    0.184881] pci 0000:00:0b.0: reg 10 32bit mmio: [0xc0004000-0xc0004fff]
[    0.184913] pci 0000:00:0b.0: supports D1 D2
[    0.184916] pci 0000:00:0b.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.184921] pci 0000:00:0b.0: PME# disabled
[    0.184950] pci 0000:00:0b.1: reg 10 32bit mmio: [0xc0005000-0xc00050ff]
[    0.184984] pci 0000:00:0b.1: supports D1 D2
[    0.184987] pci 0000:00:0b.1: PME# supported from D0 D1 D2 D3hot D3cold
[    0.184991] pci 0000:00:0b.1: PME# disabled
``````
[    0.185034] pci 0000:00:0d.0: reg 20 io port: [0x3080-0x308f]
[    0.185083] pci 0000:00:0e.0: reg 10 io port: [0x30b0-0x30b7]
[    0.185089] pci 0000:00:0e.0: reg 14 io port: [0x30a4-0x30a7]
[    0.185095] pci 0000:00:0e.0: reg 18 io port: [0x30a8-0x30af]
[    0.185101] pci 0000:00:0e.0: reg 1c io port: [0x30a0-0x30a3]
[    0.185107] pci 0000:00:0e.0: reg 20 io port: [0x3090-0x309f]
[    0.185113] pci 0000:00:0e.0: reg 24 32bit mmio: [0xc0006000-0xc0006fff]
[    0.185214] pci 0000:00:10.1: reg 10 32bit mmio: [0xc0000000-0xc0003fff]
[    0.185252] pci 0000:00:10.1: PME# supported from D3hot D3cold
[    0.185256] pci 0000:00:10.1: PME# disabled
[    0.185293] pci 0000:00:14.0: reg 10 32bit mmio: [0xc0007000-0xc0007fff]
[    0.185299] pci 0000:00:14.0: reg 14 io port: [0x30b8-0x30bf]
[    0.185326] pci 0000:00:14.0: supports D1 D2
[    0.185328] pci 0000:00:14.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.185333] pci 0000:00:14.0: PME# disabled
[    0.185467] pci 0000:00:02.0: bridge io port: [0x4000-0x4fff]
[    0.185472] pci 0000:00:02.0: bridge 32bit mmio: [0xc0200000-0xc03fffff]
[    0.185477] pci 0000:00:02.0: bridge 64bit mmio pref: [0xc3200000-0xc33fffff]
[    0.185516] pci 0000:03:00.0: reg 10 64bit mmio: [0xc0400000-0xc040ffff]
[    0.185610] pci 0000:00:03.0: bridge 32bit mmio: [0xc0400000-0xc04fffff]
[    0.185653] pci 0000:05:00.0: reg 10 32bit mmio: [0xc2000000-0xc2ffffff]
[    0.185665] pci 0000:05:00.0: reg 14 64bit mmio pref: [0xd0000000-0xdfffffff]
[    0.185678] pci 0000:05:00.0: reg 1c 64bit mmio: [0xc1000000-0xc1ffffff]
[    0.185690] pci 0000:05:00.0: reg 30 32bit mmio pref: [0x000000-0x01ffff]
[    0.185766] pci 0000:00:04.0: bridge 32bit mmio: [0xc1000000-0xc2ffffff]
[    0.185771] pci 0000:00:04.0: bridge 64bit mmio pref: [0xd0000000-0xdfffffff]
[    0.185810] pci 0000:07:06.0: reg 10 32bit mmio: [0xc3000000-0xc30007ff]
[    0.185817] pci 0000:07:06.0: reg 14 io port: [0x5000-0x507f]
[    0.185855] pci 0000:07:06.0: supports D2
``````
[    0.185858] pci 0000:07:06.0: PME# supported from D2 D3hot D3cold
[    0.185862] pci 0000:07:06.0: PME# disabled
[    0.185896] pci 0000:00:10.0: transparent bridge
[    0.185900] pci 0000:00:10.0: bridge io port: [0x5000-0x5fff]
[    0.185904] pci 0000:00:10.0: bridge 32bit mmio: [0xc3000000-0xc30fffff]
[    0.185917] pci_bus 0000:00: on NUMA node 0
[    0.185921] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.186022] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P2P0._PRT]
[    0.186046] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.XVR0._PRT]
[    0.186084] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.XVR1._PRT]
[    0.186120] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.XVR2._PRT]
[    0.212084] ACPI: PCI Interrupt Link [LNK1] (IRQs 5 7 10 11 14 15) *0, disabled.
[    0.212277] ACPI: PCI Interrupt Link [LNK2] (IRQs 5 7 10 *11 14 15)
[    0.212462] ACPI: PCI Interrupt Link [LNK3] (IRQs 5 7 *10 11 14 15)
[    0.212646] ACPI: PCI Interrupt Link [LNK4] (IRQs 5 7 10 11 14 15) *0, disabled.
[    0.212836] ACPI: PCI Interrupt Link [LK1E] (IRQs 16 17 18 19 20 21 22 23) *10
[    0.213022] ACPI: PCI Interrupt Link [LK2E] (IRQs 16 17 18 19 20 21 22 23) *0, disabled.
[    0.213208] ACPI: PCI Interrupt Link [LK3E] (IRQs 16 17 18 19 20 21 22 23) *0, disabled.
[    0.213394] ACPI: PCI Interrupt Link [LK4E] (IRQs 16 17 18 19 20 21 22 23) *0, disabled.
[    0.213580] ACPI: PCI Interrupt Link [LSMB] (IRQs 16 17 18 19 20 21 22 23) *10
[    0.213773] ACPI: PCI Interrupt Link [LPMU] (IRQs 16 17 18 19 20 21 22 23) *11
[    0.213959] ACPI: PCI Interrupt Link [LUS0] (IRQs 16 17 18 19 20 21 22 23) *11
[    0.214144] ACPI: PCI Interrupt Link [LUS2] (IRQs 16 17 18 19 20 21 22 23) *7
[    0.214331] ACPI: PCI Interrupt Link [LMAC] (IRQs 16 17 18 19 20 21 22 23) *11
[    0.214521] ACPI: PCI Interrupt Link [LAZA] (IRQs 16 17 18 19 20 21 22 23) *0, disabled.
``````
[    0.214707] ACPI: PCI Interrupt Link [LPID] (IRQs 16 17 18 19 20 21 22 23) *0, disabled.
[    0.214902] ACPI: PCI Interrupt Link [LTID] (IRQs 16 17 18 19 20 21 22 23) *5
[    0.215088] ACPI: PCI Interrupt Link [LSI1] (IRQs 16 17 18 19 20 21 22 23) *0, disabled.
[    0.215243] vgaarb: device added: PCI:0000:05:00.0,decodes=io+mem,owns=io+mem,locks=none
[    0.215247] vgaarb: loaded
[    0.215389] SCSI subsystem initialized
[    0.215516] libata version 3.00 loaded.
[    0.215610] usbcore: registered new interface driver usbfs
[    0.215627] usbcore: registered new interface driver hub
[    0.215659] usbcore: registered new device driver usb
[    0.215842] ACPI: WMI: Mapper loaded
[    0.215844] PCI: Using ACPI for IRQ routing
[    0.216094] NetLabel: Initializing
[    0.216096] NetLabel:  domain hash size = 128
[    0.216099] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.216116] NetLabel:  unlabeled traffic allowed by default
[    0.216169] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 31
[    0.216177] hpet0: 3 comparators, 32-bit 25.000000 MHz counter
[    0.224006] Switching to clocksource hpet
[    0.226378] AppArmor: AppArmor Filesystem Enabled
[    0.226407] pnp: PnP ACPI init
[    0.226429] ACPI: bus type pnp registered
[    0.229167] pnp: PnP ACPI: found 12 devices
[    0.229171] ACPI: ACPI bus type pnp unregistered
[    0.229175] PnPBIOS: Disabled by ACPI PNP
[    0.229189] system 00:00: iomem range 0xffc00000-0xffffffff could not be reserved
[    0.229194] system 00:00: iomem range 0xfec00000-0xfec00fff could not be reserved
[    0.229199] system 00:00: iomem range 0xfee00000-0xfeefffff could not be reserved
[    0.229203] system 00:00: iomem range 0xfed00000-0xfed00fff has been reserved
[    0.229211] system 00:02: iomem range 0xe0000000-0xefffffff has been reserved
[    0.229219] system 00:03: ioport range 0x1000-0x107f has been reserved
[    0.229223] system 00:03: ioport range 0x1080-0x10ff has been reserved
[    0.229227] system 00:03: ioport range 0x1400-0x147f has been reserved
[    0.229231] system 00:03: ioport range 0x1480-0x14ff has been reserved
[    0.229235] system 00:03: ioport range 0x1800-0x187f has been reserved
[    0.229239] system 00:03: ioport range 0x1880-0x18ff has been reserved
[    0.229243] system 00:03: ioport range 0x3040-0x307f has been reserved
[    0.229251] system 00:03: ioport range 0x3000-0x303f has been reserved
[    0.229255] system 00:03: ioport range 0x2000-0x203f has been reserved
[    0.229266] system 00:0b: ioport range 0x360-0x361 has been reserved
[    0.229270] system 00:0b: ioport range 0x4d0-0x4d1 has been reserved
[    0.264055] pci 0000:00:02.0: PCI bridge, secondary bus 0000:01
[    0.264059] pci 0000:00:02.0:   IO window: 0x4000-0x4fff
[    0.264064] pci 0000:00:02.0:   MEM window: 0xc0200000-0xc03fffff
[    0.264068] pci 0000:00:02.0:   PREFETCH window: 0x000000c3200000-0x000000c33fffff
[    0.264074] pci 0000:00:03.0: PCI bridge, secondary bus 0000:03
[    0.264076] pci 0000:00:03.0:   IO window: disabled
[    0.264080] pci 0000:00:03.0:   MEM window: 0xc0400000-0xc04fffff
[    0.264084] pci 0000:00:03.0:   PREFETCH window: disabled
[    0.264093] pci 0000:05:00.0: BAR 6: can't allocate mem resource [0xe0000000-0xdfffffff]
``````
[    0.264096] pci 0000:00:04.0: PCI bridge, secondary bus 0000:05
[    0.264099] pci 0000:00:04.0:   IO window: disabled
[    0.264103] pci 0000:00:04.0:   MEM window: 0xc1000000-0xc2ffffff
[    0.264107] pci 0000:00:04.0:   PREFETCH window: 0x000000d0000000-0x000000dfffffff
[    0.264112] pci 0000:00:10.0: PCI bridge, secondary bus 0000:07
[    0.264116] pci 0000:00:10.0:   IO window: 0x5000-0x5fff
[    0.264121] pci 0000:00:10.0:   MEM window: 0xc3000000-0xc30fffff
[    0.264125] pci 0000:00:10.0:   PREFETCH window: disabled
[    0.264138] pci 0000:00:02.0: setting latency timer to 64
[    0.264144] pci 0000:00:03.0: setting latency timer to 64
[    0.264150] pci 0000:00:04.0: setting latency timer to 64
[    0.264156] pci 0000:00:10.0: setting latency timer to 64
[    0.264160] pci_bus 0000:00: resource 0 io:  [0x00-0xffff]
[    0.264164] pci_bus 0000:00: resource 1 mem: [0x000000-0xffffffff]
[    0.264168] pci_bus 0000:01: resource 0 io:  [0x4000-0x4fff]
[    0.264171] pci_bus 0000:01: resource 1 mem: [0xc0200000-0xc03fffff]
[    0.264175] pci_bus 0000:01: resource 2 pref mem [0xc3200000-0xc33fffff]
[    0.264179] pci_bus 0000:03: resource 1 mem: [0xc0400000-0xc04fffff]
[    0.264183] pci_bus 0000:05: resource 1 mem: [0xc1000000-0xc2ffffff]
[    0.264186] pci_bus 0000:05: resource 2 pref mem [0xd0000000-0xdfffffff]
[    0.264190] pci_bus 0000:07: resource 0 io:  [0x5000-0x5fff]
[    0.264194] pci_bus 0000:07: resource 1 mem: [0xc3000000-0xc30fffff]
[    0.264197] pci_bus 0000:07: resource 3 io:  [0x00-0xffff]
[    0.264201] pci_bus 0000:07: resource 4 mem: [0x000000-0xffffffff]
[    0.264245] NET: Registered protocol family 2
[    0.264361] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.264772] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.265635] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.266047] TCP: Hash tables configured (established 131072 bind 65536)
[    0.266051] TCP reno registered
[    0.266164] NET: Registered protocol family 1
[    0.266232] pci 0000:00:00.0: Found enabled HT MSI Mapping
[    0.266261] pci 0000:00:00.0: Found enabled HT MSI Mapping
[    0.266294] pci 0000:00:00.0: Found enabled HT MSI Mapping
[    0.468776] pci 0000:00:09.0: Found enabled HT MSI Mapping
[    0.468836] pci 0000:00:09.0: Found enabled HT MSI Mapping
[    0.468897] pci 0000:00:09.0: Found enabled HT MSI Mapping
[    0.468928] pci 0000:05:00.0: Boot video device
[    0.468962] Simple Boot Flag at 0x36 set to 0x1
[    0.469193] cpufreq-nforce2: No nForce2 chipset.
[    0.469231] Scanning for low memory corruption every 60 seconds
[    0.469385] audit: initializing netlink socket (disabled)
[    0.469398] type=2000 audit(1274790642.468:1): initialized
[    0.482139] highmem bounce pool size: 64 pages
[    0.482146] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    0.484216] VFS: Disk quotas dquot_6.5.2
[    0.484295] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.485025] fuse init (API version 7.13)
[    0.485134] msgmni has been set to 1690
[    0.485432] alg: No test for stdrng (krng)
[    0.485507] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.485511] io scheduler noop registered
[    0.485514] io scheduler anticipatory registered
[    0.485517] io scheduler deadline registered
[    0.485571] io scheduler cfq registered (default)
[    0.485761]   alloc irq_desc for 24 on node -1
[    0.485764]   alloc kstat_irqs on node -1
[    0.485776] pcieport 0000:00:02.0: irq 24 for MSI/MSI-X
[    0.485783] pcieport 0000:00:02.0: setting latency timer to 64
[    0.485878]   alloc irq_desc for 25 on node -1
[    0.485881]   alloc kstat_irqs on node -1
[    0.485888] pcieport 0000:00:03.0: irq 25 for MSI/MSI-X
[    0.485894] pcieport 0000:00:03.0: setting latency timer to 64
[    0.485981]   alloc irq_desc for 26 on node -1
[    0.485984]   alloc kstat_irqs on node -1
[    0.485990] pcieport 0000:00:04.0: irq 26 for MSI/MSI-X
[    0.485996] pcieport 0000:00:04.0: setting latency timer to 64
[    0.486067] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.486100] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.486691] ACPI: AC Adapter [ACAD] (on-line)
[    0.486790] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0
[    0.486797] ACPI: Power Button [PWRB]
[    0.486870] input: Lid Switch as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0D:00/input/input1
[    0.486909] ACPI: Lid Switch [LID]
[    0.486965] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input2
[    0.486969] ACPI: Power Button [PWRF]
[    0.488042] fan PNP0C0B:00: registered as cooling_device0
[    0.488050] ACPI: Fan [FN1] (off)
[    0.489026] fan PNP0C0B:01: registered as cooling_device1
[    0.489033] ACPI: Fan [FN2] (off)
[    0.489260] ACPI: processor limited to max C-state 1
[    0.489284] processor LNXCPU:00: registered as cooling_device2
[    0.489331] processor LNXCPU:01: registered as cooling_device3
[    0.507205] thermal LNXTHERM:01: registered as thermal_zone0
[    0.507215] ACPI: Thermal Zone [THRM] (67 C)
[    0.509338] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    0.510980] brd: module loaded
[    0.511588] loop: module loaded
[    0.511716] input: Macintosh mouse button emulation as /devices/virtual/input/input3
[    0.511959] pata_acpi 0000:00:0d.0: setting latency timer to 64
[    0.511990] pata_acpi 0000:00:0e.0: enabling device (0005 -> 0007)
[    0.512392] ACPI: PCI Interrupt Link [LTID] enabled at IRQ 23
[    0.512398]   alloc irq_desc for 23 on node -1
[    0.512401]   alloc kstat_irqs on node -1
[    0.512415] pata_acpi 0000:00:0e.0: PCI INT A -> Link[LTID] -> GSI 23 (level, low) -> IRQ 23
[    0.512437] pata_acpi 0000:00:0e.0: setting latency timer to 64
[    0.512448] pata_acpi 0000:00:0e.0: PCI INT A disabled
[    0.512854] Fixed MDIO Bus: probed
[    0.512897] PPP generic driver version 2.4.2
[    0.512959] tun: Universal TUN/TAP device driver, 1.6
[    0.512962] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.513130] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.513187] isapnp: Scanning for PnP cards...
[    0.649552] ACPI: PCI Interrupt Link [LUS2] enabled at IRQ 22
[    0.649557]   alloc irq_desc for 22 on node -1
[    0.649560]   alloc kstat_irqs on node -1
[    0.649573] ehci_hcd 0000:00:0b.1: PCI INT B -> Link[LUS2] -> GSI 22 (level, low) -> IRQ 22
``````
[    0.649594] ehci_hcd 0000:00:0b.1: setting latency timer to 64
[    0.649598] ehci_hcd 0000:00:0b.1: EHCI Host Controller
[    0.649665] ehci_hcd 0000:00:0b.1: new USB bus registered, assigned bus number 1
[    0.649696] ehci_hcd 0000:00:0b.1: debug port 1
[    0.649708] ehci_hcd 0000:00:0b.1: cache line size of 64 is not supported
[    0.649738] ehci_hcd 0000:00:0b.1: irq 22, io mem 0xc0005000
[    0.658782] ACPI: Battery Slot [BAT0] (battery present)
[    0.660155] Freeing initrd memory: 7788k freed
[    0.693258] ehci_hcd 0000:00:0b.1: USB 2.0 started, EHCI 1.00
[    0.693385] usb usb1: configuration #1 chosen from 1 choice
[    0.693424] hub 1-0:1.0: USB hub found
[    0.693435] hub 1-0:1.0: 8 ports detected
[    0.693526] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.693912] ACPI: PCI Interrupt Link [LUS0] enabled at IRQ 21
[    0.693918]   alloc irq_desc for 21 on node -1
[    0.693921]   alloc kstat_irqs on node -1
[    0.693935] ohci_hcd 0000:00:0b.0: PCI INT A -> Link[LUS0] -> GSI 21 (level, low) -> IRQ 21
[    0.693950] ohci_hcd 0000:00:0b.0: setting latency timer to 64
[    0.693954] ohci_hcd 0000:00:0b.0: OHCI Host Controller
[    0.694008] ohci_hcd 0000:00:0b.0: new USB bus registered, assigned bus number 2
[    0.694045] ohci_hcd 0000:00:0b.0: irq 21, io mem 0xc0004000
[    0.755204] usb usb2: configuration #1 chosen from 1 choice
[    0.755244] hub 2-0:1.0: USB hub found
[    0.755259] hub 2-0:1.0: 8 ports detected
[    0.755346] uhci_hcd: USB Universal Host Controller Interface driver
[    0.755458] PNP: PS/2 Controller [PNP0303:KBC0,PNP0f13:MSE0] at 0x60,0x64 irq 1,12
[    0.757603] i8042.c: Detected active multiplexing controller, rev 1.1.
[    0.758724] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.758738] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[    0.758743] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[    0.758747] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[    0.758752] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[    0.758851] mice: PS/2 mouse device common for all mice
[    0.759005] rtc_cmos 00:09: RTC can wake from S4
[    0.759051] rtc_cmos 00:09: rtc core: registered rtc_cmos as rtc0
[    0.759091] rtc0: alarms up to one year, y3k, 114 bytes nvram, hpet irqs
[    0.759219] device-mapper: uevent: version 1.0.3
[    0.759371] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: [EMAIL="dm-devel@redhat.com"]dm-devel@redhat.com[/EMAIL]
[    0.759453] device-mapper: multipath: version 1.1.0 loaded
[    0.759457] device-mapper: multipath round-robin: version 1.0.0 loaded
[    0.759608] EISA: Probing bus 0 at eisa.0
[    0.759615] Cannot allocate resource for EISA slot 1
[    0.759619] Cannot allocate resource for EISA slot 2
[    0.759622] Cannot allocate resource for EISA slot 3
[    0.759626] Cannot allocate resource for EISA slot 4
[    0.759629] Cannot allocate resource for EISA slot 5
[    0.759642] EISA: Detected 0 cards.
[    0.759731] cpuidle: using governor ladder
[    0.759734] cpuidle: using governor menu
[    0.760300] TCP cubic registered
[    0.760495] NET: Registered protocol family 10
[    0.761089] lo: Disabled Privacy Extensions
[    0.761501] NET: Registered protocol family 17
[    0.761547] powernow-k8: Found 1 AMD Turion(tm) 64 X2 Mobile Technology TL-50 processors (2 cpu cores) (version 2.20.00)
[    0.761593] powernow-k8:    0 : fid 0x8 (1600 MHz), vid 0x13
[    0.761597] powernow-k8:    1 : fid 0x0 (800 MHz), vid 0x1e
[    0.781379] Using IPI No-Shortcut mode
[    0.781476] PM: Resume from disk failed.
[    0.781492] registered taskstats version 1
[    0.781891]   Magic number: 10:621:532
[    0.781907] bdi 1:10: hash matches
[    0.781996] rtc_cmos 00:09: setting system clock to 2010-05-25 12:30:43 UTC (1274790643)
[    0.782000] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.782002] EDD information not available.
[    0.801965] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input4
[    0.870691] isapnp: No Plug & Play device found
[    0.870719] Freeing unused kernel memory: 656k freed
[    0.871324] Write protecting the kernel text: 4676k
[    0.871373] Write protecting the kernel read-only data: 1840k
[    0.897328] udev: starting version 151
[    1.010385] pata_amd 0000:00:0d.0: version 0.4.1
[    1.010440] pata_amd 0000:00:0d.0: setting latency timer to 64
[    1.039204] scsi0 : pata_amd
[    1.060587] scsi1 : pata_amd
[    1.061434] ata1: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0x3080 irq 14
[    1.061438] ata2: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0x3088 irq 15
[    1.061513] sata_nv 0000:00:0e.0: version 3.5
[    1.061526] sata_nv 0000:00:0e.0: PCI INT A -> Link[LTID] -> GSI 23 (level, low) -> IRQ 23
[    1.061530] sata_nv 0000:00:0e.0: Using SWNCQ mode
[    1.061590] sata_nv 0000:00:0e.0: setting latency timer to 64
[    1.063817] scsi2 : sata_nv
[    1.063952] scsi3 : sata_nv
[    1.064149] ata3: SATA max UDMA/133 cmd 0x30b0 ctl 0x30a4 bmdma 0x3090 irq 23
[    1.064154] ata4: SATA max UDMA/133 cmd 0x30a8 ctl 0x30a0 bmdma 0x3098 irq 23
[    1.064214] forcedeth: Reverse Engineered nForce ethernet driver. Version 0.64.
[    1.064579] ACPI: PCI Interrupt Link [LMAC] enabled at IRQ 20
[    1.064585]   alloc irq_desc for 20 on node -1
[    1.064588]   alloc kstat_irqs on node -1
[    1.064601] forcedeth 0000:00:14.0: PCI INT A -> Link[LMAC] -> GSI 20 (level, low) -> IRQ 20
[    1.064607] forcedeth 0000:00:14.0: setting latency timer to 64
[    1.064662] nv_probe: set workaround bit for reversed mac addr
[    1.224492] ata1.00: ATAPI: Optiarc DVD RW AD-7540A, 1.42, max UDMA/33
[    1.224528] ata1: nv_mode_filter: 0x739f&0x739f->0x739f, BIOS=0x7000 (0xc000c700) ACPI=0x701f (60:600:0x13)
[    1.240066] usb 2-1: new low speed USB device using ohci_hcd and address 2
[    1.240460] ata1.00: configured for UDMA/33
[    1.241834] scsi 0:0:0:0: CD-ROM            Optiarc  DVD RW AD-7540A  1.42 PQ: 0 ANSI: 5
[    1.244794] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[    1.244800] Uniform CD-ROM driver Revision: 3.20
[    1.244954] sr 0:0:0:0: Attached scsi CD-ROM sr0
[    1.245034] sr 0:0:0:0: Attached scsi generic sg0 type 5
[    1.452190] usb 2-1: configuration #1 chosen from 1 choice
[    1.528095] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    1.584929] ata3.00: ATA-7: WDC WD1600BEVS-22RST0, 04.01G04, max UDMA/133
[    1.584935] ata3.00: 312581808 sectors, multi 16: LBA48 NCQ (depth 31/32)
[    1.585080] forcedeth 0000:00:14.0: ifname eth0, PHY OUI 0x5043 @ 1, addr 00:14:0b:0c:cc:1a
[    1.585085] forcedeth 0000:00:14.0: highdma pwrctl lnktim desc-v3
[    1.601515] ata3.00: configured for UDMA/133
[    1.601650] scsi 2:0:0:0: Direct-Access     ATA      WDC WD1600BEVS-2 04.0 PQ: 0 ANSI: 5
[    1.601883] sd 2:0:0:0: Attached scsi generic sg1 type 0
[    1.601892] sd 2:0:0:0: [sda] 312581808 512-byte logical blocks: (160 GB/149 GiB)
[    1.601987] sd 2:0:0:0: [sda] Write Protect is off
[    1.601992] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.602024] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.602312]  sda: sda1 sda2 < sda5 >
[    1.637866] sd 2:0:0:0: [sda] Attached SCSI disk
[    1.923014] ata4: SATA link down (SStatus 0 SControl 300)
[    1.928848] usbcore: registered new interface driver hiddev
[    1.933753] ACPI: PCI Interrupt Link [LNK1] enabled at IRQ 11
[    1.933773] ohci1394 0000:07:06.0: PCI INT A -> Link[LNK1] -> GSI 11 (level, low) -> IRQ 11
[    1.936486] input: USB Optical Mouse as /devices/pci0000:00/0000:00:0b.0/usb2/2-1/2-1:1.0/input/input5
[    1.936724] generic-usb 0003:15CA:00C3.0001: input,hidraw0: USB HID v1.10 Mouse [USB Optical Mouse] on usb-0000:00:0b.0-1/input0
[    1.936759] usbcore: registered new interface driver usbhid
[    1.936764] usbhid: v2.6:USB HID core driver
[    1.990072] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[11]  MMIO=[c3000000-c30007ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[    2.278035] EXT4-fs (sda1): mounted filesystem with ordered data mode
[    3.264361] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[0040ca013f01a850]
[   17.133865] udev: starting version 151
[   17.142608] Adding 6037496k swap on /dev/sda5.  Priority:-1 extents:1 across:6037496k 
[   17.321378] lp: driver loaded but no devices found
[   17.483126] i2c i2c-0: nForce2 SMBus adapter at 0x3040
[   17.483156] i2c i2c-1: nForce2 SMBus adapter at 0x3000
[   17.488492] k8temp 0000:00:18.3: Temperature readouts might be wrong - check erratum #141
[   17.490944] cfg80211: Calling CRDA to update world regulatory domain
[   17.495901] vga16fb: initializing
[   17.495907] vga16fb: mapped to 0xc00a0000
[   17.495990] fb0: VGA16 VGA frame buffer device
[   17.502777] [Firmware Bug]: ACPI(VGA) defines _DOD but not _DOS
[   17.502893] [Firmware Bug]: ACPI: ACPI brightness control misses _BQC function
[   17.503542] acpi device:18: registered as cooling_device4
[   17.503922] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A03:00/device:16/LNXVIDEO:00/input/input6
[   17.504076] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[   17.519940] Linux agpgart interface v0.103
[   17.567775] cfg80211: World regulatory domain updated:
[   17.567780]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   17.567784]     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   17.567788]     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   17.567791]     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   17.567794]     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   17.567798]     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   17.582319] ACPI: PCI Interrupt Link [LK1E] enabled at IRQ 19
[   17.582326]   alloc irq_desc for 19 on node -1
[   17.582328]   alloc kstat_irqs on node -1
[   17.582343] ath5k 0000:03:00.0: PCI INT A -> Link[LK1E] -> GSI 19 (level, low) -> IRQ 19
[   17.582353] ath5k 0000:03:00.0: setting latency timer to 64
[   17.582397] ath5k 0000:03:00.0: registered as 'phy0'
[   17.795047] type=1505 audit(1274790660.511:2):  operation="profile_load" pid=597 name="/sbin/dhclient3"
[   17.795402] type=1505 audit(1274790660.511:3):  operation="profile_load" pid=597 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[   17.795598] type=1505 audit(1274790660.511:4):  operation="profile_load" pid=597 name="/usr/lib/connman/scripts/dhclient-script"
[   17.909392] psmouse serio4: ID: 10 00 64
[   18.001631] ACPI: PCI Interrupt Link [LAZA] enabled at IRQ 18
[   18.001638]   alloc irq_desc for 18 on node -1
[   18.001641]   alloc kstat_irqs on node -1
[   18.001653] HDA Intel 0000:00:10.1: PCI INT B -> Link[LAZA] -> GSI 18 (level, low) -> IRQ 18
[   18.001657] hda_intel: Disable MSI for Nvidia chipset
[   18.001703] HDA Intel 0000:00:10.1: setting latency timer to 64
[   18.071421] Console: switching to colour frame buffer device 80x30
[   18.110694] ath: EEPROM regdomain: 0x30
[   18.110699] ath: EEPROM indicates we should expect a direct regpair map
[   18.110703] ath: Country alpha2 being used: AM
[   18.110705] ath: Regpair used: 0x30
[   18.203946] Finger Sensing Pad, hw: 9.0.1, sw: 1.0.0-K, buttons: 2
[   18.247811] type=1505 audit(1274790660.963:5):  operation="profile_load" pid=740 name="/usr/share/gdm/guest-session/Xsession"
[   18.250211] type=1505 audit(1274790660.967:6):  operation="profile_replace" pid=741 name="/sbin/dhclient3"
[   18.250884] type=1505 audit(1274790660.967:7):  operation="profile_replace" pid=741 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[   18.251081] type=1505 audit(1274790660.967:8):  operation="profile_replace" pid=741 name="/usr/lib/connman/scripts/dhclient-script"
[   18.255553] type=1505 audit(1274790660.971:9):  operation="profile_load" pid=742 name="/usr/bin/evince"
[   18.260167] type=1505 audit(1274790660.975:10):  operation="profile_load" pid=742 name="/usr/bin/evince-previewer"
[   18.263070] type=1505 audit(1274790660.979:11):  operation="profile_load" pid=742 name="/usr/bin/evince-thumbnailer"
[   18.561686] nvidia: module license 'NVIDIA' taints kernel.
[   18.561692] Disabling lock debugging due to kernel taint
[   18.595914] input: FSPPS/2 Sentelic FingerSensingPad as /devices/platform/i8042/serio4/input/input7
[   19.981318] ppdev: user-space parallel port driver
[   20.015317] phy0: Selected rate control algorithm 'minstrel'
[   20.016383] ath5k phy0: Atheros AR5414 chip found (MAC: 0xa0, PHY: 0x61)
[   20.017272] cfg80211: Calling CRDA for country: AM
[   20.148045] hda_codec: ALC883: BIOS auto-probing.
[   20.177470] cfg80211: Regulatory domain changed to country: AM
[   20.177476]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   20.177480]     (2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A, 2000 mBm)
[   20.177484]     (5170000 KHz - 5250000 KHz @ 20000 KHz), (N/A, 1800 mBm)
[   20.177487]     (5250000 KHz - 5330000 KHz @ 20000 KHz), (N/A, 1800 mBm)
[   20.204732] nvidia 0000:05:00.0: PCI INT A -> Link[LK1E] -> GSI 19 (level, low) -> IRQ 19
``````
[   20.204747] nvidia 0000:05:00.0: setting latency timer to 64
[   20.204755] vgaarb: device changed decodes: PCI:0000:05:00.0,olddecodes=io+mem,decodes=none:owns=io+mem
[   20.205141] NVRM: loading NVIDIA UNIX x86 Kernel Module  195.36.15  Thu Mar 11 21:41:46 PST 2010
[   20.316197] input: HDA Digital PCBeep as /devices/pci0000:00/0000:00:10.1/input/input8
[   20.532908] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   28.924020] eth0: no IPv6 routers present
[   28.924020] eth0: no IPv6 routers present
[   81.004077] Clocksource tsc unstable (delta = -163550885 ns[/CODE

syslog:
[CODE]May 25 14:31:08 -laptop pulseaudio[1273]: pid.c: Daemon already running.
May 25 14:31:09 -laptop acpid: client connected from 1344[108:114]
May 25 14:31:09 -laptop acpid: 1 client rule loaded
May 25 14:31:11 -laptop kernel: [   28.924020] eth0: no IPv6 routers present
May 25 14:32:03 -laptop kernel: [   81.004077] Clocksource tsc unstable (delta = -163550885 ns)
May 25 14:32:12 -laptop AptDaemon: INFO: Initializing daemon
May 25 14:37:13 -laptop AptDaemon: INFO: Quiting due to inactivity
May 25 14:37:13 -laptop AptDaemon: INFO: Shutdown was requested
May 25 14:37:53 -laptop kernel: [  430.573026] CE: hpet increasing min_delta_ns to 15000 nsec


May 25 14:38:45 -laptop kernel: [  482.685025] CE: hpet increasing min_delta_ns to 22500 nsec
[   81.004077] Clocksource tsc unstable (delta = -163550885 ns)
```hwinfo --short:
```
cpu:                                                            
                       AMD Turion(tm) 64 X2 Mobile Technology TL-50, 800 MHz
                       AMD Turion(tm) 64 X2 Mobile Technology TL-50, 800 MHz
keyboard:
  /dev/input/event4    AT Translated Set 2 keyboard
mouse:
  /dev/input/mice      USB Optical Mouse
  /dev/input/mice      Macintosh mouse button emulation
  /dev/input/mice      FSPPS/2 Sentelic FingerSensingPad
graphics card:
                       nVidia GeForce Go 7400
sound:
                       nVidia MCP51 High Definition Audio
storage:
                       nVidia MCP51 IDE
                       nVidia MCP51 Serial ATA Controller
network:
  eth0                 nVidia MCP51 Ethernet Controller
  wlan0                Atheros AR5006EG 802.11bg NIC (2.4GHz, PCI Express)
network interface:
  lo                   Loopback network interface
  eth0                 Ethernet network interface
  wlan0                WLAN network interface
disk:
  /dev/ramzswap0       Disk
  /dev/sda             WDC WD1600BEVS-2
partition:
  /dev/sda1            Partition
  /dev/sda2            Partition
  /dev/sda3            Partition
  /dev/sda5            Partition
cdrom:
  /dev/sr0             Optiarc DVD RW AD-7540A
usb controller:
                       nVidia MCP51 USB Controller
                       nVidia MCP51 USB Controller
bios:
                       BIOS
bridge:
                       nVidia C51 PCI Express Bridge
                       nVidia C51 PCI Express Bridge
                       nVidia C51 PCI Express Bridge
                       nVidia MCP51 LPC Bridge
                       nVidia MCP51 PCI Bridge
                       AMD K8 [Athlon64/Opteron] HyperTransport Technology Configuration
                       AMD K8 [Athlon64/Opteron] Address Map
                       AMD K8 [Athlon64/Opteron] DRAM Controller
                       AMD K8 [Athlon64/Opteron] Miscellaneous Control
hub:
                       Linux 2.6.32-22-generic ehci_hcd EHCI Host Controller
                       Linux 2.6.32-22-generic ohci_hcd OHCI Host Controller
memory:
                       Main Memory
firewire controller:
                       VIA VT6306 Fire II IEEE 1394 OHCI Link Layer Controller
unknown:
                       FPU
                       DMA controller
                       PIC
                       Timer
                       Keyboard controller
                       nVidia C51 Host Bridge
                       nVidia C51 Memory Controller 0
                       nVidia C51 Memory Controller 1
                       nVidia C51 Memory Controller 5
                       nVidia C51 Memory Controller 4
                       nVidia C51 Host Bridge
                       nVidia C51 Memory Controller 3
                       nVidia C51 Memory Controller 2
                       nVidia MCP51 Host Bridge
                       nVidia MCP51 SMBus
                       nVidia MCP51 PMU
                       Unclassified device
                       Unclassified device
                       Unclassified device
                       Unclassified device
                       Unclassified device
                       Unclassified device
                       Unclassified device
                       Unclassified device
                       Unclassified device
                       Unclassified device
                       Unclassified device
                       Unclassified device

```I have tested:
sudo gedit /etc/default/grub

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash hpet=disable"
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash apci=off" 
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash clocksource=hpet"
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash clocksource= apci_pm"

Info:
sudo cat  /sys/devices/system/clocksource/clocksource0/available_clocksource

acpi_pm

sudo cat  /sys/devices/system/clocksource/clocksource0/current_clocksource

hpet

---

### Post by Kurdistan on 2010-05-29
Please help!

---

