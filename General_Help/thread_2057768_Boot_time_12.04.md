---
title: "Boot time 12.04"
date: 2012-09-14
forum: General Help
---

### Post by ranger1021994 on 2012-09-14
Guys my boot is very slow,
so i ran ```
dmesg
```
and here is the output :


```
[    0.529568] pci 0000:03:03.0: reg 14: [mem 0xf0000000-0xf0003fff]
[    0.529641] pci 0000:03:03.0: supports D1 D2
[    0.529643] pci 0000:03:03.0: PME# supported from D0 D1 D2 D3hot
[    0.529650] pci 0000:03:03.0: PME# disabled
[    0.529692] pci 0000:00:1e.0: PCI bridge to [bus 03-03] (subtractive decode)
[    0.529701] pci 0000:00:1e.0:   bridge window [mem 0xf0000000-0xf00fffff]
[    0.529711] pci 0000:00:1e.0:   bridge window [io  0x0000-0x0cf7] (subtractive decode)
[    0.529713] pci 0000:00:1e.0:   bridge window [io  0x0d00-0xffff] (subtractive decode)
[    0.529715] pci 0000:00:1e.0:   bridge window [mem 0x000a0000-0x000bffff] (subtractive decode)
[    0.529717] pci 0000:00:1e.0:   bridge window [mem 0xe0000000-0xf7ffffff] (subtractive decode)
[    0.529739] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.529967] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P32_._PRT]
[    0.530042] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEX0._PRT]
[    0.530100] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEG3._PRT]
[    0.530186]  pci0000:00: Requesting ACPI _OSC control (0x1d)
[    0.530345]  pci0000:00: ACPI _OSC control (0x19) granted
[    0.534127] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 7 9 10 *11 12)
[    0.534181] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 7 *9 10 11 12)
[    0.534236] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 7 9 10 *11 12)
[    0.534290] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 7 9 *10 11 12)
[    0.534344] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 7 9 10 *11 12)
[    0.534397] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 7 9 10 11 12) *0, disabled.
[    0.534453] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 7 *9 10 11 12)
[    0.534506] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 7 9 *10 11 12)
[    0.534601] vgaarb: device added: PCI:0000:01:00.0,decodes=io+mem,owns=io+mem,locks=none
[    0.534603] vgaarb: loaded
[    0.534604] vgaarb: bridge control possible 0000:01:00.0
[    0.534680] i2c-core: driver [aat2870] using legacy suspend method
[    0.534681] i2c-core: driver [aat2870] using legacy resume method
[    0.534733] SCSI subsystem initialized
[    0.534773] libata version 3.00 loaded.
[    0.534805] usbcore: registered new interface driver usbfs
[    0.534812] usbcore: registered new interface driver hub
[    0.534830] usbcore: registered new device driver usb
[    0.534890] PCI: Using ACPI for IRQ routing
[    0.536250] PCI: Discovered peer bus 3f
[    0.536275] pci 0000:3f:00.0: [8086:2c51] type 0 class 0x000600
[    0.536293] pci 0000:3f:00.1: [8086:2c81] type 0 class 0x000600
[    0.536311] pci 0000:3f:02.0: [8086:2c90] type 0 class 0x000600
[    0.536326] pci 0000:3f:02.1: [8086:2c91] type 0 class 0x000600
[    0.536343] pci 0000:3f:03.0: [8086:2c98] type 0 class 0x000600
[    0.536358] pci 0000:3f:03.1: [8086:2c99] type 0 class 0x000600
[    0.536373] pci 0000:3f:03.4: [8086:2c9c] type 0 class 0x000600
[    0.536389] pci 0000:3f:04.0: [8086:2ca0] type 0 class 0x000600
[    0.536404] pci 0000:3f:04.1: [8086:2ca1] type 0 class 0x000600
[    0.536420] pci 0000:3f:04.2: [8086:2ca2] type 0 class 0x000600
[    0.536435] pci 0000:3f:04.3: [8086:2ca3] type 0 class 0x000600
[    0.536452] pci 0000:3f:05.0: [8086:2ca8] type 0 class 0x000600
[    0.536467] pci 0000:3f:05.1: [8086:2ca9] type 0 class 0x000600
[    0.536482] pci 0000:3f:05.2: [8086:2caa] type 0 class 0x000600
[    0.536497] pci 0000:3f:05.3: [8086:2cab] type 0 class 0x000600
[    0.536792] PCI: pci_cache_line_size set to 64 bytes
[    0.536898] reserve RAM buffer: 000000000008f000 - 000000000008ffff 
[    0.536900] reserve RAM buffer: 00000000df62d000 - 00000000dfffffff 
[    0.536903] reserve RAM buffer: 00000000df66f000 - 00000000dfffffff 
[    0.536905] reserve RAM buffer: 00000000df6f4000 - 00000000dfffffff 
[    0.536907] reserve RAM buffer: 00000000df7e7000 - 00000000dfffffff 
[    0.536909] reserve RAM buffer: 00000000df7f3000 - 00000000dfffffff 
[    0.536911] reserve RAM buffer: 00000000df800000 - 00000000dfffffff 
[    0.536983] NetLabel: Initializing
[    0.536984] NetLabel:  domain hash size = 128
[    0.536985] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.536994] NetLabel:  unlabeled traffic allowed by default
[    0.537067] HPET: 8 timers in total, 5 timers will be used for per-cpu timer
[    0.537076] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 40, 41, 42, 43, 44, 0
[    0.537080] hpet0: 8 comparators, 64-bit 14.318180 MHz counter
[    0.541447] hpet: hpet2 irq 40 for MSI
[    0.541806] hpet: hpet3 irq 41 for MSI
[    0.545567] hpet: hpet4 irq 42 for MSI
[    0.549609] hpet: hpet5 irq 43 for MSI
[    0.549636] Switching to clocksource hpet
[    0.554829] AppArmor: AppArmor Filesystem Enabled
[    0.554848] pnp: PnP ACPI init
[    0.554862] ACPI: bus type pnp registered
[    0.554965] pnp 00:00: [bus 00-3e]
[    0.554967] pnp 00:00: [io  0x0cf8-0x0cff]
[    0.554969] pnp 00:00: [io  0x0000-0x0cf7 window]
[    0.554970] pnp 00:00: [io  0x0d00-0xffff window]
[    0.554972] pnp 00:00: [mem 0x000a0000-0x000bffff window]
[    0.554974] pnp 00:00: [mem 0xe0000000-0xf7ffffff window]
[    0.555019] pnp 00:00: Plug and Play ACPI device, IDs PNP0a08 PNP0a03 (active)
[    0.555032] pnp 00:01: [mem 0xf8000000-0xffffffff]
[    0.555073] system 00:01: [mem 0xf8000000-0xffffffff] could not be reserved
[    0.555076] system 00:01: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.555191] pnp 00:02: [io  0x0000-0x000f]
[    0.555192] pnp 00:02: [io  0x0081-0x0083]
[    0.555195] pnp 00:02: [io  0x0087]
[    0.555197] pnp 00:02: [io  0x0089-0x008b]
[    0.555198] pnp 00:02: [io  0x008f]
[    0.555199] pnp 00:02: [io  0x00c0-0x00df]
[    0.555201] pnp 00:02: [dma 4]
[    0.555222] pnp 00:02: Plug and Play ACPI device, IDs PNP0200 (active)
[    0.555228] pnp 00:03: [io  0x0070-0x0071]
[    0.555230] pnp 00:03: [io  0x0074-0x0077]
[    0.555241] pnp 00:03: [irq 8]
[    0.555259] pnp 00:03: Plug and Play ACPI device, IDs PNP0b00 (active)
[    0.555267] pnp 00:04: [io  0x00f0]
[    0.555275] pnp 00:04: [irq 13]
[    0.555295] pnp 00:04: Plug and Play ACPI device, IDs PNP0c04 (active)
[    0.555303] pnp 00:05: [io  0x0061]
[    0.555323] pnp 00:05: Plug and Play ACPI device, IDs PNP0800 (active)
[    0.555330] pnp 00:06: [io  0x0500-0x057f]
[    0.555332] pnp 00:06: [io  0x0400-0x047f]
[    0.555333] pnp 00:06: [io  0x0092]
[    0.555334] pnp 00:06: [io  0x0062]
[    0.555336] pnp 00:06: [io  0x0066]
[    0.555337] pnp 00:06: [io  0x0680-0x06ff]
[    0.555338] pnp 00:06: [io  0x0010-0x001f]
[    0.555340] pnp 00:06: [io  0x0072-0x0073]
[    0.555341] pnp 00:06: [io  0x0080]
[    0.555342] pnp 00:06: [io  0x0084-0x0086]
[    0.555344] pnp 00:06: [io  0x0088]
[    0.555345] pnp 00:06: [io  0x008c-0x008e]
[    0.555346] pnp 00:06: [io  0x0090-0x009f]
[    0.555387] system 00:06: [io  0x0500-0x057f] has been reserved
[    0.555389] system 00:06: [io  0x0400-0x047f] has been reserved
[    0.555391] system 00:06: [io  0x0680-0x06ff] has been reserved
[    0.555394] system 00:06: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.555426] pnp 00:07: [io  0x0060]
[    0.555427] pnp 00:07: [io  0x0064]
[    0.555463] system 00:07: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.555483] pnp 00:08: [mem 0xfec00000-0xfec000ff]
[    0.555506] pnp 00:08: Plug and Play ACPI device, IDs PNP0003 (active)
[    0.555571] pnp 00:09: [mem 0xfed00000-0xfed03fff]
[    0.555605] pnp 00:09: Plug and Play ACPI device, IDs PNP0103 (active)
[    0.555612] pnp: PnP ACPI: found 10 devices
[    0.555613] ACPI: ACPI bus type pnp unregistered
[    0.562811] pci 0000:01:00.0: no compatible bridge window for [mem 0xfffe0000-0xffffffff pref]
[    0.562820] PCI: max bus depth: 1 pci_try_num: 2
[    0.562846] pci 0000:00:1c.0: BAR 14: assigned [mem 0xf0300000-0xf04fffff]
[    0.562849] pci 0000:00:1c.0: BAR 15: assigned [mem 0xf0500000-0xf06fffff 64bit pref]
[    0.562852] pci 0000:00:1c.0: BAR 13: assigned [io  0x3000-0x3fff]
[    0.562854] pci 0000:01:00.0: BAR 6: assigned [mem 0xf0120000-0xf013ffff pref]
[    0.562857] pci 0000:00:03.0: PCI bridge to [bus 01-01]
[    0.562859] pci 0000:00:03.0:   bridge window [io  0x1000-0x1fff]
[    0.562862] pci 0000:00:03.0:   bridge window [mem 0xf0100000-0xf01fffff]
[    0.562865] pci 0000:00:03.0:   bridge window [mem 0xe0000000-0xefffffff 64bit pref]
[    0.562869] pci 0000:00:1c.0: PCI bridge to [bus 02-02]
[    0.562872] pci 0000:00:1c.0:   bridge window [io  0x3000-0x3fff]
[    0.562880] pci 0000:00:1c.0:   bridge window [mem 0xf0300000-0xf04fffff]
[    0.562888] pci 0000:00:1c.0:   bridge window [mem 0xf0500000-0xf06fffff 64bit pref]
[    0.562893] pci 0000:00:1e.0: PCI bridge to [bus 03-03]
[    0.562901] pci 0000:00:1e.0:   bridge window [mem 0xf0000000-0xf00fffff]
[    0.562922] pci 0000:00:03.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.562925] pci 0000:00:03.0: setting latency timer to 64
[    0.562939] pci 0000:00:1c.0: enabling device (0000 -> 0003)
[    0.562950] pci 0000:00:1c.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    0.562956] pci 0000:00:1c.0: setting latency timer to 64
[    0.562969] pci 0000:00:1e.0: setting latency timer to 64
[    0.562977] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
[    0.562979] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff]
[    0.562980] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
[    0.562982] pci_bus 0000:00: resource 7 [mem 0xe0000000-0xf7ffffff]
[    0.562984] pci_bus 0000:01: resource 0 [io  0x1000-0x1fff]
[    0.562986] pci_bus 0000:01: resource 1 [mem 0xf0100000-0xf01fffff]
[    0.562988] pci_bus 0000:01: resource 2 [mem 0xe0000000-0xefffffff 64bit pref]
[    0.562990] pci_bus 0000:02: resource 0 [io  0x3000-0x3fff]
[    0.562992] pci_bus 0000:02: resource 1 [mem 0xf0300000-0xf04fffff]
[    0.562994] pci_bus 0000:02: resource 2 [mem 0xf0500000-0xf06fffff 64bit pref]
[    0.562996] pci_bus 0000:03: resource 1 [mem 0xf0000000-0xf00fffff]
[    0.562998] pci_bus 0000:03: resource 4 [io  0x0000-0x0cf7]
[    0.562999] pci_bus 0000:03: resource 5 [io  0x0d00-0xffff]
[    0.563001] pci_bus 0000:03: resource 6 [mem 0x000a0000-0x000bffff]
[    0.563003] pci_bus 0000:03: resource 7 [mem 0xe0000000-0xf7ffffff]
[    0.563005] pci_bus 0000:3f: resource 0 [io  0x0000-0xffff]
[    0.563007] pci_bus 0000:3f: resource 1 [mem 0x00000000-0xfffffffff]
[    0.563035] NET: Registered protocol family 2
[    0.563191] IP route cache hash table entries: 262144 (order: 9, 2097152 bytes)
[    0.563946] TCP established hash table entries: 524288 (order: 11, 8388608 bytes)
[    0.566309] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[    0.566591] TCP: Hash tables configured (established 524288 bind 65536)
[    0.566593] TCP reno registered
[    0.566603] UDP hash table entries: 4096 (order: 5, 131072 bytes)
[    0.566663] UDP-Lite hash table entries: 4096 (order: 5, 131072 bytes)
[    0.566780] NET: Registered protocol family 1
[    0.566823] pci 0000:00:1a.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.581809] pci 0000:00:1a.0: PCI INT A disabled
[    0.581848] pci 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    0.597788] pci 0000:00:1d.0: PCI INT A disabled
[    0.597827] pci 0000:01:00.0: Boot video device
[    0.597853] PCI: CLS 64 bytes, default 64
[    0.597855] PCI-DMA: Using software bounce buffering for IO (SWIOTLB)
[    0.597857] Placing 64MB software IO TLB between ffff8800db62d000 - ffff8800df62d000
[    0.597859] software IO TLB at phys 0xdb62d000 - 0xdf62d000
[    0.598286] audit: initializing netlink socket (disabled)
[    0.598296] type=2000 audit(1347640054.444:1): initialized
[    0.618952] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    0.620714] VFS: Disk quotas dquot_6.5.2
[    0.620759] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    0.621169] fuse init (API version 7.17)
[    0.621245] msgmni has been set to 11876
[    0.621633] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.621662] io scheduler noop registered
[    0.621663] io scheduler deadline registered
[    0.621688] io scheduler cfq registered (default)
[    0.621800] pcieport 0000:00:03.0: setting latency timer to 64
[    0.621831] pcieport 0000:00:03.0: irq 45 for MSI/MSI-X
[    0.621883] pcieport 0000:00:1c.0: setting latency timer to 64
[    0.621924] pcieport 0000:00:1c.0: irq 46 for MSI/MSI-X
[    0.622003] aer 0000:00:03.0:pcie02: service driver aer loaded
[    0.622020] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.622054] pciehp 0000:00:1c.0:pcie04: HPC vendor_id 8086 device_id 3b42 ss_vid 8086 ss_did 4257
[    0.622083] pciehp 0000:00:1c.0:pcie04: service driver pciehp loaded
[    0.622088] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.622131] intel_idle: MWAIT substates: 0x1120
[    0.622141] intel_idle: v0.4 model 0x1E
[    0.622142] intel_idle: lapic_timer_reliable_states 0x2
[    0.622221] input: Sleep Button as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input0
[    0.622225] ACPI: Sleep Button [SLPB]
[    0.622262] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
[    0.622265] ACPI: Power Button [PWRF]
[    0.626755] ERST: Table is not found!
[    0.626756] GHES: HEST is not enabled!
[    0.626821] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    0.812545] Freeing initrd memory: 19844k freed
[    0.910310] Linux agpgart interface v0.103
[    0.911630] brd: module loaded
[    0.912321] loop: module loaded
[    0.912445] ata_piix 0000:00:1f.2: version 2.13
[    0.912471] ata_piix 0000:00:1f.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    0.912476] ata_piix 0000:00:1f.2: MAP [ P0 P2 P1 P3 ]
[    0.912524] ata_piix 0000:00:1f.2: setting latency timer to 64
[    0.912775] scsi0 : ata_piix
[    0.912849] scsi1 : ata_piix
[    0.912947] ata1: SATA max UDMA/133 cmd 0x2098 ctl 0x20ac bmdma 0x2070 irq 19
[    0.912956] ata2: SATA max UDMA/133 cmd 0x2090 ctl 0x20a8 bmdma 0x2078 irq 19
[    0.912969] ata_piix 0000:00:1f.5: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    0.912976] ata_piix 0000:00:1f.5: MAP [ P0 -- P1 -- ]
[    0.913005] ata_piix 0000:00:1f.5: setting latency timer to 64
[    0.913172] scsi2 : ata_piix
[    0.913247] scsi3 : ata_piix
[    0.913314] ata3: SATA max UDMA/133 cmd 0x2088 ctl 0x20a4 bmdma 0x2050 irq 19
[    0.913322] ata4: SATA max UDMA/133 cmd 0x2080 ctl 0x20a0 bmdma 0x2058 irq 19
[    0.913561] Fixed MDIO Bus: probed
[    0.913576] tun: Universal TUN/TAP device driver, 1.6
[    0.913577] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.913625] PPP generic driver version 2.4.2
[    0.913706] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.913726] ehci_hcd 0000:00:1a.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.913751] ehci_hcd 0000:00:1a.0: setting latency timer to 64
[    0.913758] ehci_hcd 0000:00:1a.0: EHCI Host Controller
[    0.913800] ehci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 1
[    0.913830] ehci_hcd 0000:00:1a.0: debug port 2
[    0.917809] ehci_hcd 0000:00:1a.0: cache line size of 64 is not supported
[    0.917821] ehci_hcd 0000:00:1a.0: irq 16, io mem 0xf0225400
[    0.933795] ehci_hcd 0000:00:1a.0: USB 2.0 started, EHCI 1.00
[    0.933928] hub 1-0:1.0: USB hub found
[    0.933931] hub 1-0:1.0: 3 ports detected
[    0.933998] ehci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    0.934013] ehci_hcd 0000:00:1d.0: setting latency timer to 64
[    0.934020] ehci_hcd 0000:00:1d.0: EHCI Host Controller
[    0.934059] ehci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    0.934090] ehci_hcd 0000:00:1d.0: debug port 2
[    0.938060] ehci_hcd 0000:00:1d.0: cache line size of 64 is not supported
[    0.938075] ehci_hcd 0000:00:1d.0: irq 23, io mem 0xf0225000
[    0.953799] ehci_hcd 0000:00:1d.0: USB 2.0 started, EHCI 1.00
[    0.953915] hub 2-0:1.0: USB hub found
[    0.953918] hub 2-0:1.0: 3 ports detected
[    0.953969] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.953979] uhci_hcd: USB Universal Host Controller Interface driver
[    0.954014] usbcore: registered new interface driver libusual
[    0.954038] i8042: PNP: No PS/2 controller found. Probing ports directly.
[    0.955010] i8042: No controller found
[    0.955074] mousedev: PS/2 mouse device common for all mice
[    0.955191] rtc_cmos 00:03: RTC can wake from S4
[    0.955291] rtc_cmos 00:03: rtc core: registered rtc_cmos as rtc0
[    0.955327] rtc0: alarms up to one month, y3k, 114 bytes nvram, hpet irqs
[    0.955385] device-mapper: uevent: version 1.0.3
[    0.955441] device-mapper: ioctl: 4.22.0-ioctl (2011-10-19) initialised: dm-devel@redhat.com
[    0.955522] cpuidle: using governor ladder
[    0.955640] cpuidle: using governor menu
[    0.955641] EFI Variables Facility v0.08 2004-May-17
[    0.955814] TCP cubic registered
[    0.955816] IPv6: Loaded, but administratively disabled, reboot required to enable
[    0.955818] NET: Registered protocol family 17
[    0.955821] Registering the dns_resolver key type
[    0.956040] PM: Hibernation image not present or could not be loaded.
[    0.956048] registered taskstats version 1
[    0.964295]   Magic number: 12:692:489
[    0.964431] rtc_cmos 00:03: setting system clock to 2012-09-14 16:27:35 UTC (1347640055)
[    0.964959] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.964960] EDD information not available.
[    1.245182] ata4: SATA link down (SStatus 0 SControl 300)
[    1.260160] ata3: SATA link down (SStatus 0 SControl 300)
[    1.260221] usb 1-1: new high-speed USB device number 2 using ehci_hcd
[    1.390731] hub 1-1:1.0: USB hub found
[    1.390923] hub 1-1:1.0: 6 ports detected
[    1.502029] usb 2-1: new high-speed USB device number 2 using ehci_hcd
[    1.597936] Refined TSC clocksource calibration: 2666.759 MHz.
[    1.597943] Switching to clocksource tsc
[    1.634985] hub 2-1:1.0: USB hub found
[    1.635177] hub 2-1:1.0: 8 ports detected
[    1.706080] ata2.00: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    1.706132] ata2.01: SATA link down (SStatus 0 SControl 300)
[    1.706141] usb 1-1.1: new low-speed USB device number 3 using ehci_hcd
[    1.706143] ata2.01: link offline, clearing class 3 to NONE
[    1.706260] ata1.00: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    1.706273] ata1.01: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    1.714162] ata2.00: ATAPI: ASUS    DRW-1814BLT, 1.13, max UDMA/66
[    1.730123] ata2.00: configured for UDMA/66
[    1.754562] ata1.00: ATA-8: WDC WD5000AAKS-00V6A0, 05.01D05, max UDMA/133
[    1.754568] ata1.00: 976773168 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    1.754872] ata1.01: ATA-8: ST3250318AS, CC38, max UDMA/133
[    1.754878] ata1.01: 488397168 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    1.762544] ata1.00: configured for UDMA/133
[    1.778477] ata1.01: configured for UDMA/133
[    1.778924] scsi 0:0:0:0: Direct-Access     ATA      WDC WD5000AAKS-0 05.0 PQ: 0 ANSI: 5
[    1.779293] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    1.779299] sd 0:0:0:0: [sda] 976773168 512-byte logical blocks: (500 GB/465 GiB)
[    1.779634] scsi 0:0:1:0: Direct-Access     ATA      ST3250318AS      CC38 PQ: 0 ANSI: 5
[    1.779717] sd 0:0:0:0: [sda] Write Protect is off
[    1.779720] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.779830] sd 0:0:1:0: Attached scsi generic sg1 type 0
[    1.779835] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.779904] sd 0:0:1:0: [sdb] 488397168 512-byte logical blocks: (250 GB/232 GiB)
[    1.780174] sd 0:0:1:0: [sdb] Write Protect is off
[    1.780181] sd 0:0:1:0: [sdb] Mode Sense: 00 3a 00 00
[    1.780337] sd 0:0:1:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.780684] scsi 1:0:0:0: CD-ROM            ASUS     DRW-1814BLT      1.13 PQ: 0 ANSI: 5
[    1.783443] sr0: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
[    1.783448] cdrom: Uniform CD-ROM driver Revision: 3.20
[    1.783716] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    1.783894] sr 1:0:0:0: Attached scsi generic sg2 type 5
[    1.786641]  sda: sda1 sda2 sda3
[    1.813862]  sdb: sdb1 sdb2 < sdb5 >
[    1.814108] sd 0:0:0:0: [sda] Attached SCSI disk
[    1.815150] sd 0:0:1:0: [sdb] Attached SCSI disk
[    1.816399] Freeing unused kernel memory: 920k freed
[    1.816519] Write protecting the kernel read-only data: 12288k
[    1.820465] Freeing unused kernel memory: 1616k freed
[    1.823556] Freeing unused kernel memory: 1200k freed
[    1.874028] usb 1-1.4: new low-speed USB device number 4 using ehci_hcd
[    1.883116] udevd[176]: starting version 175
[    1.901586] e1000e: Intel(R) PRO/1000 Network Driver - 1.5.1-k
[    1.901588] e1000e: Copyright(c) 1999 - 2011 Intel Corporation.
[    1.901622] e1000e 0000:00:19.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    1.901634] e1000e 0000:00:19.0: setting latency timer to 64
[    1.901738] e1000e 0000:00:19.0: irq 47 for MSI/MSI-X
[    1.905393] firewire_ohci 0000:03:03.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    1.909881] input: Logitech USB Optical Mouse as /devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.1/1-1.1:1.0/input/input2
[    1.909971] generic-usb 0003:046D:C05A.0001: input,hidraw0: USB HID v1.11 Mouse [Logitech USB Optical Mouse] on usb-0000:00:1a.0-1.1/input0
[    1.909984] usbcore: registered new interface driver usbhid
[    1.909986] usbhid: USB HID core driver
[    1.958026] firewire_ohci: Added fw-ohci device 0000:03:03.0, OHCI v1.10, 4 IR + 8 IT contexts, quirks 0x2
[    1.980505] input: BTC USB Multimedia Keyboard as /devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.4/1-1.4:1.0/input/input3
[    1.980761] generic-usb 0003:046D:C312.0002: input,hidraw1: USB HID v1.10 Keyboard [BTC USB Multimedia Keyboard] on usb-0000:00:1a.0-1.4/input0
[    1.987441] input: BTC USB Multimedia Keyboard as /devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.4/1-1.4:1.1/input/input4
[    1.987758] generic-usb 0003:046D:C312.0003: input,hiddev0,hidraw2: USB HID v1.10 Device [BTC USB Multimedia Keyboard] on usb-0000:00:1a.0-1.4/input1
[    2.062150] usb 2-1.1: new full-speed USB device number 3 using ehci_hcd
[    2.151262] e1000e 0000:00:19.0: eth0: (PCI Express:2.5GT/s:Width x1) 00:27:0e:19:10:68
[    2.151264] e1000e 0000:00:19.0: eth0: Intel(R) PRO/1000 Network Connection
[    2.151339] e1000e 0000:00:19.0: eth0: MAC: 9, PHY: 9, PBA No: FFFFFF-0FF
[    2.458229] firewire_core: created device fw0: GUID 0090270002656064, S400
[    3.604658] vesafb: mode is 1600x1200x32, linelength=6400, pages=0
[    3.604660] vesafb: scrolling: redraw
[    3.604662] vesafb: Truecolor: size=0:8:8:8, shift=0:16:8:0
[    3.608333] vesafb: framebuffer at 0xe0000000, mapped to 0xffffc90005c00000, using 7552k, total 7552k
[    3.608488] Console: switching to colour frame buffer device 200x75
[    3.608514] fb0: VESA VGA frame buffer device
[    3.869168] EXT4-fs (sdb5): mounted filesystem with ordered data mode. Opts: (null)
[   20.210223] udevd[665]: starting version 175
[   20.315652] Adding 3998716k swap on /dev/sdb1.  Priority:-1 extents:1 across:3998716k 
[   21.549333] e4rat-preload: plymouth main process (427) killed by ABRT signal
[   21.549559] e4rat-preload: plymouth-splash main process (1167) terminated with status 2
[   24.728209] EDAC MC: Ver: 2.1.0
[   24.746279] EDAC MC0: Giving out device to 'i7core_edac.c' 'i7 core #0': DEV 0000:3f:03.0
[   24.746292] EDAC PCI0: Giving out device to module 'i7core_edac' controller 'EDAC PCI controller': DEV '0000:3f:03.0' (POLLED)
[   24.746400] EDAC i7core: Driver loaded, 1 memory controller(s) found.
[   25.148486] i801_smbus 0000:00:1f.3: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[   25.911205] Bluetooth: Core ver 2.16
[   25.911220] NET: Registered protocol family 31
[   25.911222] Bluetooth: HCI device and connection manager initialized
[   25.911223] Bluetooth: HCI socket layer initialized
[   25.911225] Bluetooth: L2CAP socket layer initialized
[   25.911229] Bluetooth: SCO socket layer initialized
[   26.266351] Bluetooth: Generic Bluetooth USB driver ver 0.6
[   26.266474] usbcore: registered new interface driver btusb
[   26.675027] adt7475 0-002c: ADT7490 device, revision 3
[   26.675029] adt7475 0-002c: Optional features: in0 in4 fan4 pwm2
[   27.047688] type=1400 audit(1347620281.579:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=1160 comm="apparmor_parser"
[   27.047696] type=1400 audit(1347620281.579:3): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=1161 comm="apparmor_parser"
[   27.047954] type=1400 audit(1347620281.579:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=1161 comm="apparmor_parser"
[   27.048014] type=1400 audit(1347620281.579:5): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=1160 comm="apparmor_parser"
[   27.048103] type=1400 audit(1347620281.579:6): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=1161 comm="apparmor_parser"
[   27.048166] type=1400 audit(1347620281.579:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=1160 comm="apparmor_parser"
[   27.379077] ip_tables: (C) 2000-2006 Netfilter Core Team
[   27.451022] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
[   27.451025] Disabling lock debugging due to kernel taint
[   27.465469] [fglrx] Maximum main memory to use for locked dma buffers: 5764 MBytes.
[   27.465679] [fglrx]   vendor: 1002 device: 954f count: 1
[   27.466159] [fglrx] ioport: bar 4, base 0x1000, size: 0x100
[   27.466169] pci 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   27.466173] pci 0000:01:00.0: setting latency timer to 64
[   27.466467] [fglrx] Kernel PAT support is enabled
[   27.466480] [fglrx] module loaded - fglrx 8.96.4 [Mar 12 2012] with 1 minors
[   27.667307] snd_hda_intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[   27.667349] snd_hda_intel 0000:00:1b.0: irq 48 for MSI/MSI-X
[   27.667369] snd_hda_intel 0000:00:1b.0: setting latency timer to 64
[   27.698494] nf_conntrack version 0.5.0 (16384 buckets, 65536 max)
[   27.801159] hda_codec: ALC888: BIOS auto-probing.
[   27.801163] hda_codec: ALC888: SKU not ready 0x411111f0
[   27.807889] input: HDA Intel Line as /devices/pci0000:00/0000:00:1b.0/sound/card0/input5
[   27.808095] input: HDA Intel Rear Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input6
[   27.808149] input: HDA Intel Line-Out as /devices/pci0000:00/0000:00:1b.0/sound/card0/input7
[   27.808769] snd_hda_intel 0000:01:00.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[   27.808821] snd_hda_intel 0000:01:00.1: irq 49 for MSI/MSI-X
[   27.808840] snd_hda_intel 0000:01:00.1: setting latency timer to 64
[   27.882885] HDMI status: Codec=0 Pin=3 Presence_Detect=0 ELD_Valid=0
[   27.882947] input: HDA ATI HDMI HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:03.0/0000:01:00.1/sound/card1/input8
[   27.930259] EXT4-fs (sdb5): re-mounted. Opts: errors=remount-ro
[   28.414755] e4rat-preload: failsafe main process (1419) killed by TERM signal
[   28.549386] e4rat-preload: plymouth-log main process (1415) terminated with status 1
[   28.711351] ppdev: user-space parallel port driver
[   28.731116] e4rat-preload: plymouth-upstart-bridge main process (1458) terminated with status 1
[   28.751341] type=1400 audit(1347620283.283:8): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=1511 comm="apparmor_parser"
[   28.751641] type=1400 audit(1347620283.283:9): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=1511 comm="apparmor_parser"
[   28.751813] type=1400 audit(1347620283.283:10): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=1511 comm="apparmor_parser"
[   28.756356] type=1400 audit(1347620283.287:11): apparmor="STATUS" operation="profile_load" name="/usr/lib/lightdm/lightdm/lightdm-guest-session-wrapper" pid=1510 comm="apparmor_parser"
[   29.351143] e1000e 0000:00:19.0: irq 47 for MSI/MSI-X
[   29.407013] e1000e 0000:00:19.0: irq 47 for MSI/MSI-X
[   30.888426] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: Rx
[   30.888430] e1000e 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[   31.287001] device eth0 entered promiscuous mode
[   31.587354] fglrx_pci 0000:01:00.0: irq 50 for MSI/MSI-X
[   31.587981] [fglrx] Firegl kernel thread PID: 1795
[   31.588136] [fglrx] Firegl kernel thread PID: 1796
[   31.588241] [fglrx] Firegl kernel thread PID: 1797
[   31.588358] [fglrx] IRQ 50 Enabled
[   32.419172] [fglrx] Gart USWC size:1280 M.
[   32.419175] [fglrx] Gart cacheable size:508 M.
[   32.419178] [fglrx] Reserved FB block: Shared offset:0, size:1000000 
[   32.419180] [fglrx] Reserved FB block: Unshared offset:fbfd000, size:403000 
[   32.419181] [fglrx] Reserved FB block: Unshared offset:3fffb000, size:5000 
```


udevd takes too much time and sometimes adding swap takes too much time (i have added swap partition though i have 6GB RAM)


Any suggestions to cut boot time ?

---

### Post by shreepads on 2012-09-14
Post complete system specs and bootchart...

See:
[https://wiki.ubuntu.com/BootCharting](https://wiki.ubuntu.com/BootCharting)

---

