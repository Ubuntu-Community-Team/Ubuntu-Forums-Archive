---
title: "About Loading Time"
date: 2011-05-08
forum: General Help
---

### Post by wua on 2011-05-08
Ubuntu 10.10 is NOT loading fast on startup. What can I do please help me..



```
[    0.131863] pnp 00:00: [io  0x03b0-0x03df window]
[    0.131866] pnp 00:00: [mem 0x000a0000-0x000bffff window]
[    0.131870] pnp 00:00: [mem 0x40000000-0xdfffffff window]
[    0.131873] pnp 00:00: [mem 0xf0000000-0xfe02ffff window]
[    0.131876] pnp 00:00: [mem 0xfeb00000-0xfebfffff window]
[    0.131956] pnp 00:00: Plug and Play ACPI device, IDs PNP0a08 PNP0a03 (active)
[    0.131979] pnp 00:01: [io  0x1000-0x107f]
[    0.131982] pnp 00:01: [io  0x1080-0x10ff]
[    0.131984] pnp 00:01: [io  0x1400-0x147f]
[    0.131987] pnp 00:01: [io  0x1480-0x14ff]
[    0.131989] pnp 00:01: [io  0x1800-0x187f]
[    0.131992] pnp 00:01: [io  0x1880-0x18ff]
[    0.132072] system 00:01: [io  0x1000-0x107f] has been reserved
[    0.132076] system 00:01: [io  0x1080-0x10ff] has been reserved
[    0.132079] system 00:01: [io  0x1400-0x147f] has been reserved
[    0.132082] system 00:01: [io  0x1480-0x14ff] has been reserved
[    0.132086] system 00:01: [io  0x1800-0x187f] has been reserved
[    0.132089] system 00:01: [io  0x1880-0x18ff] has been reserved
[    0.132094] system 00:01: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.132686] pnp 00:02: [io  0x0010-0x001f]
[    0.132689] pnp 00:02: [io  0x0022-0x003f]
[    0.132691] pnp 00:02: [io  0x0044-0x005f]
[    0.132694] pnp 00:02: [io  0x0062-0x0063]
[    0.132696] pnp 00:02: [io  0x0065-0x006f]
[    0.132699] pnp 00:02: [io  0x0074-0x007f]
[    0.132702] pnp 00:02: [io  0x0091-0x0093]
[    0.132704] pnp 00:02: [io  0x00a2-0x00bf]
[    0.132707] pnp 00:02: [io  0x00e0-0x00ef]
[    0.132710] pnp 00:02: [io  0x04d0-0x04d1]
[    0.132712] pnp 00:02: [io  0x0800-0x0805]
[    0.132715] pnp 00:02: [io  0x0295-0x0296]
[    0.132793] system 00:02: [io  0x04d0-0x04d1] has been reserved
[    0.132797] system 00:02: [io  0x0800-0x0805] has been reserved
[    0.132801] system 00:02: [io  0x0295-0x0296] has been reserved
[    0.132805] system 00:02: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.132820] pnp 00:03: [dma 4]
[    0.132822] pnp 00:03: [io  0x0000-0x000f]
[    0.132825] pnp 00:03: [io  0x0080-0x0090]
[    0.132828] pnp 00:03: [io  0x0094-0x009f]
[    0.132830] pnp 00:03: [io  0x00c0-0x00df]
[    0.132880] pnp 00:03: Plug and Play ACPI device, IDs PNP0200 (active)
[    0.132893] pnp 00:04: [io  0x0070-0x0073]
[    0.132907] pnp 00:04: [irq 8]
[    0.132955] pnp 00:04: Plug and Play ACPI device, IDs PNP0b00 (active)
[    0.132965] pnp 00:05: [io  0x0061]
[    0.133013] pnp 00:05: Plug and Play ACPI device, IDs PNP0800 (active)
[    0.133024] pnp 00:06: [io  0x00f0-0x00ff]
[    0.133030] pnp 00:06: [irq 13]
[    0.133082] pnp 00:06: Plug and Play ACPI device, IDs PNP0c04 (active)
[    0.133202] pnp 00:07: [io  0x03f0-0x03f5]
[    0.133205] pnp 00:07: [io  0x03f7]
[    0.133211] pnp 00:07: [irq 6]
[    0.133214] pnp 00:07: [dma 2]
[    0.133279] pnp 00:07: Plug and Play ACPI device, IDs PNP0700 (active)
[    0.133451] pnp 00:08: [io  0x03f8-0x03ff]
[    0.133458] pnp 00:08: [irq 4]
[    0.133541] pnp 00:08: Plug and Play ACPI device, IDs PNP0501 (active)
[    0.133933] pnp 00:09: [io  0x0378-0x037f]
[    0.133936] pnp 00:09: [io  0x0778-0x077b]
[    0.133943] pnp 00:09: [irq 7]
[    0.134026] pnp 00:09: Plug and Play ACPI device, IDs PNP0400 (active)
[    0.134120] pnp 00:0a: [irq 12]
[    0.134170] pnp 00:0a: Plug and Play ACPI device, IDs PNP0f13 (active)
[    0.134244] pnp 00:0b: [io  0x0060]
[    0.134247] pnp 00:0b: [io  0x0064]
[    0.134253] pnp 00:0b: [irq 1]
[    0.134303] pnp 00:0b: Plug and Play ACPI device, IDs PNP0303 (active)
[    0.134324] pnp 00:0c: [mem 0xe0000000-0xefffffff]
[    0.134392] system 00:0c: [mem 0xe0000000-0xefffffff] has been reserved
[    0.134397] system 00:0c: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.134505] pnp 00:0d: [mem 0x000f0000-0x000f3fff]
[    0.134508] pnp 00:0d: [mem 0x000f4000-0x000f7fff]
[    0.134511] pnp 00:0d: [mem 0x000f8000-0x000fbfff]
[    0.134514] pnp 00:0d: [mem 0x000fc000-0x000fffff]
[    0.134516] pnp 00:0d: [mem 0x3fff0000-0x3fffffff]
[    0.134519] pnp 00:0d: [mem 0xffff0000-0xffffffff]
[    0.134522] pnp 00:0d: [mem 0x00000000-0x0009ffff]
[    0.134525] pnp 00:0d: [mem 0x00100000-0x3ffeffff]
[    0.134528] pnp 00:0d: [mem 0xfec00000-0xfec00fff]
[    0.134531] pnp 00:0d: [mem 0xfee00000-0xfeefffff]
[    0.134534] pnp 00:0d: [mem 0xfefff000-0xfeffffff]
[    0.134536] pnp 00:0d: [mem 0xfff80000-0xfff80fff]
[    0.134539] pnp 00:0d: [mem 0xfff90000-0xfffbffff]
[    0.134542] pnp 00:0d: [mem 0xfffed000-0xfffeffff]
[    0.134626] system 00:0d: [mem 0x000f0000-0x000f3fff] could not be reserved
[    0.134630] system 00:0d: [mem 0x000f4000-0x000f7fff] could not be reserved
[    0.134634] system 00:0d: [mem 0x000f8000-0x000fbfff] could not be reserved
[    0.134638] system 00:0d: [mem 0x000fc000-0x000fffff] could not be reserved
[    0.134641] system 00:0d: [mem 0x3fff0000-0x3fffffff] could not be reserved
[    0.134645] system 00:0d: [mem 0xffff0000-0xffffffff] has been reserved
[    0.134649] system 00:0d: [mem 0x00000000-0x0009ffff] could not be reserved
[    0.134653] system 00:0d: [mem 0x00100000-0x3ffeffff] could not be reserved
[    0.134657] system 00:0d: [mem 0xfec00000-0xfec00fff] could not be reserved
[    0.134660] system 00:0d: [mem 0xfee00000-0xfeefffff] has been reserved
[    0.134664] system 00:0d: [mem 0xfefff000-0xfeffffff] has been reserved
[    0.134668] system 00:0d: [mem 0xfff80000-0xfff80fff] has been reserved
[    0.134672] system 00:0d: [mem 0xfff90000-0xfffbffff] has been reserved
[    0.134675] system 00:0d: [mem 0xfffed000-0xfffeffff] has been reserved
[    0.134679] system 00:0d: Plug and Play ACPI device, IDs PNP0c01 (active)
[    0.134692] pnp: PnP ACPI: found 14 devices
[    0.134694] ACPI: ACPI bus type pnp unregistered
[    0.134698] PnPBIOS: Disabled by ACPI PNP
[    0.171408] Switching to clocksource acpi_pm
[    0.171462] pci 0000:00:09.0: PCI bridge to [bus 01-01]
[    0.171467] pci 0000:00:09.0:   bridge window [io  0xa000-0xafff]
[    0.171471] pci 0000:00:09.0:   bridge window [mem 0xfde00000-0xfdefffff]
[    0.171475] pci 0000:00:09.0:   bridge window [mem 0xfdf00000-0xfdffffff pref]
[    0.171480] pci 0000:00:0b.0: PCI bridge to [bus 02-02]
[    0.171483] pci 0000:00:0b.0:   bridge window [io  0x9000-0x9fff]
[    0.171487] pci 0000:00:0b.0:   bridge window [mem 0xfdd00000-0xfddfffff]
[    0.171491] pci 0000:00:0b.0:   bridge window [mem 0xfdc00000-0xfdcfffff 64bit pref]
[    0.171499] pci 0000:03:00.0: BAR 6: assigned [mem 0xfda00000-0xfda0ffff pref]
[    0.171503] pci 0000:00:0c.0: PCI bridge to [bus 03-03]
[    0.171507] pci 0000:00:0c.0:   bridge window [io  0x8000-0x8fff]
[    0.171511] pci 0000:00:0c.0:   bridge window [mem 0xfdb00000-0xfdbfffff]
[    0.171515] pci 0000:00:0c.0:   bridge window [mem 0xfda00000-0xfdafffff 64bit pref]
[    0.171519] pci 0000:00:0d.0: PCI bridge to [bus 04-04]
[    0.171523] pci 0000:00:0d.0:   bridge window [io  0x7000-0x7fff]
[    0.171527] pci 0000:00:0d.0:   bridge window [mem 0xfd900000-0xfd9fffff]
[    0.171531] pci 0000:00:0d.0:   bridge window [mem 0xfd800000-0xfd8fffff 64bit pref]
[    0.171538] pci 0000:05:00.0: BAR 6: assigned [mem 0xfc000000-0xfc01ffff pref]
[    0.171541] pci 0000:00:0e.0: PCI bridge to [bus 05-05]
[    0.171544] pci 0000:00:0e.0:   bridge window [io  0x6000-0x6fff]
[    0.171548] pci 0000:00:0e.0:   bridge window [mem 0xfa000000-0xfcffffff]
[    0.171552] pci 0000:00:0e.0:   bridge window [mem 0xd0000000-0xdfffffff 64bit pref]
[    0.171563] pci 0000:00:09.0: setting latency timer to 64
[    0.171569] pci 0000:00:0b.0: setting latency timer to 64
[    0.171574] pci 0000:00:0c.0: setting latency timer to 64
[    0.171579] pci 0000:00:0d.0: setting latency timer to 64
[    0.171585] pci 0000:00:0e.0: setting latency timer to 64
[    0.171589] pci_bus 0000:00: resource 4 [io  0x0000-0xffff]
[    0.171592] pci_bus 0000:00: resource 5 [mem 0x000a0000-0x000bffff]
[    0.171595] pci_bus 0000:00: resource 6 [mem 0xfe030000-0xffffffff]
[    0.171600] pci_bus 0000:00: resource 7 [mem 0x40000000-0xefffffff]
[    0.171604] pci_bus 0000:00: resource 8 [mem 0xf0000000-0xfe02ffff]
[    0.171607] pci_bus 0000:01: resource 0 [io  0xa000-0xafff]
[    0.171610] pci_bus 0000:01: resource 1 [mem 0xfde00000-0xfdefffff]
[    0.171614] pci_bus 0000:01: resource 2 [mem 0xfdf00000-0xfdffffff pref]
[    0.171617] pci_bus 0000:01: resource 4 [io  0x0000-0xffff]
[    0.171620] pci_bus 0000:01: resource 5 [mem 0x000a0000-0x000bffff]
[    0.171624] pci_bus 0000:01: resource 6 [mem 0xfe030000-0xffffffff]
[    0.171627] pci_bus 0000:01: resource 7 [mem 0x40000000-0xefffffff]
[    0.171630] pci_bus 0000:01: resource 8 [mem 0xf0000000-0xfe02ffff]
[    0.171633] pci_bus 0000:02: resource 0 [io  0x9000-0x9fff]
[    0.171637] pci_bus 0000:02: resource 1 [mem 0xfdd00000-0xfddfffff]
[    0.171640] pci_bus 0000:02: resource 2 [mem 0xfdc00000-0xfdcfffff 64bit pref]
[    0.171644] pci_bus 0000:03: resource 0 [io  0x8000-0x8fff]
[    0.171647] pci_bus 0000:03: resource 1 [mem 0xfdb00000-0xfdbfffff]
[    0.171650] pci_bus 0000:03: resource 2 [mem 0xfda00000-0xfdafffff 64bit pref]
[    0.171654] pci_bus 0000:04: resource 0 [io  0x7000-0x7fff]
[    0.171657] pci_bus 0000:04: resource 1 [mem 0xfd900000-0xfd9fffff]
[    0.171660] pci_bus 0000:04: resource 2 [mem 0xfd800000-0xfd8fffff 64bit pref]
[    0.171664] pci_bus 0000:05: resource 0 [io  0x6000-0x6fff]
[    0.171667] pci_bus 0000:05: resource 1 [mem 0xfa000000-0xfcffffff]
[    0.171671] pci_bus 0000:05: resource 2 [mem 0xd0000000-0xdfffffff 64bit pref]
[    0.171721] NET: Registered protocol family 2
[    0.171796] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.171796] Switched to NOHz mode on CPU #0
[    0.171796] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.171796] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.171796] TCP: Hash tables configured (established 131072 bind 65536)
[    0.171796] TCP reno registered
[    0.171796] UDP hash table entries: 512 (order: 2, 16384 bytes)
[    0.171796] UDP-Lite hash table entries: 512 (order: 2, 16384 bytes)
[    0.171796] NET: Registered protocol family 1
[    1.788018] pci 0000:00:02.1: EHCI: BIOS handoff failed (BIOS bug?) 01010001
[    1.788073] pci 0000:00:00.0: Found enabled HT MSI Mapping
[    1.788079] pci 0000:00:0b.0: Found disabled HT MSI Mapping
[    1.788087] pci 0000:00:00.0: Found enabled HT MSI Mapping
[    1.788092] pci 0000:00:0b.0: Linking AER extended capability
[    1.788129] pci 0000:00:00.0: Found enabled HT MSI Mapping
[    1.788135] pci 0000:00:0c.0: Found disabled HT MSI Mapping
[    1.788143] pci 0000:00:00.0: Found enabled HT MSI Mapping
[    1.788147] pci 0000:00:0c.0: Linking AER extended capability
[    1.788187] pci 0000:00:00.0: Found enabled HT MSI Mapping
[    1.788193] pci 0000:00:0d.0: Found disabled HT MSI Mapping
[    1.788201] pci 0000:00:00.0: Found enabled HT MSI Mapping
[    1.788204] pci 0000:00:0d.0: Linking AER extended capability
[    1.788248] pci 0000:00:00.0: Found enabled HT MSI Mapping
[    1.788254] pci 0000:00:0e.0: Found disabled HT MSI Mapping
[    1.788262] pci 0000:00:00.0: Found enabled HT MSI Mapping
[    1.788265] pci 0000:00:0e.0: Linking AER extended capability
[    1.788285] pci 0000:05:00.0: Boot video device
[    1.788288] PCI: CLS 32 bytes, default 64
[    1.788542] cpufreq-nforce2: No nForce2 chipset.
[    1.788713] audit: initializing netlink socket (disabled)
[    1.788725] type=2000 audit(1304804833.787:1): initialized
[    1.801175] Trying to unpack rootfs image as initramfs...
[    1.820710] highmem bounce pool size: 64 pages
[    1.820718] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    1.828353] VFS: Disk quotas dquot_6.5.2
[    1.828473] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    1.829317] fuse init (API version 7.16)
[    1.829430] msgmni has been set to 1704
[    1.836562] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    1.836599] io scheduler noop registered
[    1.836601] io scheduler deadline registered
[    1.836623] io scheduler cfq registered (default)
[    1.836761] pcieport 0000:00:0b.0: setting latency timer to 64
[    1.836792] pcieport 0000:00:0b.0: irq 40 for MSI/MSI-X
[    1.836842] pcieport 0000:00:0c.0: setting latency timer to 64
[    1.836861] pcieport 0000:00:0c.0: irq 41 for MSI/MSI-X
[    1.836906] pcieport 0000:00:0d.0: setting latency timer to 64
[    1.836925] pcieport 0000:00:0d.0: irq 42 for MSI/MSI-X
[    1.836970] pcieport 0000:00:0e.0: setting latency timer to 64
[    1.836988] pcieport 0000:00:0e.0: irq 43 for MSI/MSI-X
[    1.837065] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    1.837101] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    1.837289] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0
[    1.837295] ACPI: Power Button [PWRB]
[    1.837371] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
[    1.837375] ACPI: Power Button [PWRF]
[    1.837440] ACPI: Fan [FAN] (on)
[    1.837752] ACPI: acpi_idle registered with cpuidle
[    1.840313] thermal LNXTHERM:00: registered as thermal_zone0
[    1.840317] ACPI: Thermal Zone [THRM] (43 C)
[    1.840385] ERST: Table is not found!
[    1.840542] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    1.860871] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    1.864177] isapnp: Scanning for PnP cards...
[    1.953570] 00:08: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    1.972806] Linux agpgart interface v0.103
[    1.974482] brd: module loaded
[    1.975195] loop: module loaded
[    1.975350] i2c-core: driver [adp5520] using legacy suspend method
[    1.975353] i2c-core: driver [adp5520] using legacy resume method
[    1.975589] pata_acpi 0000:00:06.0: setting latency timer to 64
[    1.975856] ACPI: PCI Interrupt Link [APSI] enabled at IRQ 23
[    1.975877] pata_acpi 0000:00:07.0: PCI INT A -> Link[APSI] -> GSI 23 (level, low) -> IRQ 23
[    1.975895] pata_acpi 0000:00:07.0: setting latency timer to 64
[    1.975903] pata_acpi 0000:00:07.0: PCI INT A disabled
[    1.980320] ACPI: PCI Interrupt Link [APSJ] enabled at IRQ 22
[    1.980344] pata_acpi 0000:00:08.0: PCI INT A -> Link[APSJ] -> GSI 22 (level, low) -> IRQ 22
[    1.980391] pata_acpi 0000:00:08.0: setting latency timer to 64
[    1.980405] pata_acpi 0000:00:08.0: PCI INT A disabled
[    1.980916] Fixed MDIO Bus: probed
[    1.980972] PPP generic driver version 2.4.2
[    1.981057] tun: Universal TUN/TAP device driver, 1.6
[    1.981060] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    1.981172] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    1.981358] ACPI: PCI Interrupt Link [APCL] enabled at IRQ 21
[    1.981376] ehci_hcd 0000:00:02.1: PCI INT B -> Link[APCL] -> GSI 21 (level, low) -> IRQ 21
[    1.981395] ehci_hcd 0000:00:02.1: setting latency timer to 64
[    1.981399] ehci_hcd 0000:00:02.1: EHCI Host Controller
[    1.981448] ehci_hcd 0000:00:02.1: new USB bus registered, assigned bus number 1
[    1.981485] ehci_hcd 0000:00:02.1: debug port 1
[    1.981491] ehci_hcd 0000:00:02.1: cache line size of 32 is not supported
[    1.981515] ehci_hcd 0000:00:02.1: irq 21, io mem 0xfeb00000
[    2.031681] ehci_hcd 0000:00:02.1: USB 2.0 started, EHCI 1.00
[    2.031901] hub 1-0:1.0: USB hub found
[    2.031907] hub 1-0:1.0: 10 ports detected
[    2.112130] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    2.112360] ACPI: PCI Interrupt Link [APCF] enabled at IRQ 20
[    2.112381] ohci_hcd 0000:00:02.0: PCI INT A -> Link[APCF] -> GSI 20 (level, low) -> IRQ 20
[    2.112402] ohci_hcd 0000:00:02.0: setting latency timer to 64
[    2.112406] ohci_hcd 0000:00:02.0: OHCI Host Controller
[    2.112493] ohci_hcd 0000:00:02.0: new USB bus registered, assigned bus number 2
[    2.112528] ohci_hcd 0000:00:02.0: irq 20, io mem 0xfe02f000
[    2.170453] hub 2-0:1.0: USB hub found
[    2.170462] hub 2-0:1.0: 10 ports detected
[    2.170564] uhci_hcd: USB Universal Host Controller Interface driver
[    2.170691] i8042: PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    2.220175] serio: i8042 KBD port at 0x60,0x64 irq 1
[    2.220190] serio: i8042 AUX port at 0x60,0x64 irq 12
[    2.220329] mousedev: PS/2 mouse device common for all mice
[    2.220478] rtc_cmos 00:04: RTC can wake from S4
[    2.220536] rtc_cmos 00:04: rtc core: registered rtc_cmos as rtc0
[    2.220560] rtc0: alarms up to one year, y3k, 242 bytes nvram
[    2.220690] device-mapper: uevent: version 1.0.3
[    2.220785] device-mapper: ioctl: 4.19.1-ioctl (2011-01-07) initialised: dm-devel@redhat.com
[    2.224187] device-mapper: multipath: version 1.2.0 loaded
[    2.224193] device-mapper: multipath round-robin: version 1.0.0 loaded
[    2.224351] EISA: Probing bus 0 at eisa.0
[    2.224355] EISA: Cannot allocate resource for mainboard
[    2.224358] Cannot allocate resource for EISA slot 1
[    2.224361] Cannot allocate resource for EISA slot 2
[    2.224364] Cannot allocate resource for EISA slot 3
[    2.224367] Cannot allocate resource for EISA slot 4
[    2.224370] Cannot allocate resource for EISA slot 5
[    2.224372] Cannot allocate resource for EISA slot 6
[    2.224375] Cannot allocate resource for EISA slot 7
[    2.224378] Cannot allocate resource for EISA slot 8
[    2.224380] EISA: Detected 0 cards.
[    2.224463] cpuidle: using governor ladder
[    2.224465] cpuidle: using governor menu
[    2.224779] TCP cubic registered
[    2.224946] NET: Registered protocol family 10
[    2.225604] NET: Registered protocol family 17
[    2.225631] Registering the dns_resolver key type
[    2.225655] powernow-k8: Found 1 AMD Sempron(tm) Processor 3400+ (1 cpu cores) (version 2.20.00)
[    2.225699] powernow-k8:    0 : fid 0xa (1800 MHz), vid 0x6
[    2.225702] powernow-k8:    1 : fid 0x2 (1000 MHz), vid 0x12
[    2.225745] Using IPI No-Shortcut mode
[    2.225893] PM: Hibernation image not present or could not be loaded.
[    2.225909] registered taskstats version 1
[    2.226136]   Magic number: 11:981:802
[    2.226248] rtc_cmos 00:04: setting system clock to 2011-05-07 21:47:14 UTC (1304804834)
[    2.226252] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    2.226254] EDD information not available.
[    2.308649] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input2
[    2.407546] isapnp: No Plug & Play device found
[    2.432442] usb 1-2: new high speed USB device using ehci_hcd and address 2
[    2.602161] Freeing initrd memory: 12512k freed
[    2.613199] Freeing unused kernel memory: 700k freed
[    2.613778] Write protecting the kernel text: 5192k
[    2.613821] Write protecting the kernel read-only data: 2148k
[    2.648605] <30>udev[61]: starting version 167
[    2.740083] usb 1-5: new high speed USB device using ehci_hcd and address 4
[    2.858123] Floppy drive(s): fd0 is 1.44M
[    2.865164] pata_amd 0000:00:06.0: version 0.4.1
[    2.865217] pata_amd 0000:00:06.0: setting latency timer to 64
[    2.888053] scsi0 : pata_amd
[    2.890328] scsi1 : pata_amd
[    2.892106] FDC 0 is a post-1991 82077
[    2.912834] ata1: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xe800 irq 14
[    2.912840] ata2: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xe808 irq 15
[    2.932190] sata_nv 0000:00:07.0: version 3.5
[    2.932208] sata_nv 0000:00:07.0: PCI INT A -> Link[APSI] -> GSI 23 (level, low) -> IRQ 23
[    2.932267] sata_nv 0000:00:07.0: setting latency timer to 64
[    2.934710] scsi2 : sata_nv
[    2.938210] usbcore: registered new interface driver uas
[    2.938242] scsi3 : sata_nv
[    2.938412] ata3: SATA max UDMA/133 cmd 0x9f0 ctl 0xbf0 bmdma 0xd400 irq 23
[    2.938416] ata4: SATA max UDMA/133 cmd 0x970 ctl 0xb70 bmdma 0xd408 irq 23
[    2.938486] sata_nv 0000:00:08.0: PCI INT A -> Link[APSJ] -> GSI 22 (level, low) -> IRQ 22
[    2.938542] sata_nv 0000:00:08.0: setting latency timer to 64
[    2.940609] scsi4 : sata_nv
[    2.942200] scsi5 : sata_nv
[    2.942383] ata5: SATA max UDMA/133 cmd 0x9e0 ctl 0xbe0 bmdma 0xc000 irq 22
[    2.942387] ata6: SATA max UDMA/133 cmd 0x960 ctl 0xb60 bmdma 0xc008 irq 22
[    2.970149] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    2.970301] ACPI: PCI Interrupt Link [APC1] enabled at IRQ 16
[    2.970319] r8169 0000:03:00.0: PCI INT A -> Link[APC1] -> GSI 16 (level, low) -> IRQ 16
[    2.970359] r8169 0000:03:00.0: setting latency timer to 64
[    2.970411] r8169 0000:03:00.0: irq 44 for MSI/MSI-X
[    2.970979] r8169 0000:03:00.0: eth0: RTL8168b/8111b at 0xf802c000, 00:04:61:44:c4:bb, XID 18000000 IRQ 44
[    3.015354] Initializing USB Mass Storage driver...
[    3.015477] scsi6 : usb-storage 1-2:1.0
[    3.015713] scsi7 : usb-storage 1-5:1.0
[    3.016164] usbcore: registered new interface driver usb-storage
[    3.016168] USB Mass Storage support registered.
[    3.176023] usb 2-4: new low speed USB device using ohci_hcd and address 2
[    3.240253] ata2.00: ATAPI: HL-DT-ST DVDRAM GSA-H10N, JL10, max UDMA/33
[    3.240262] ata2: nv_mode_filter: 0x739f&0x739f->0x739f, BIOS=0x7000 (0xc000) ACPI=0x701f (60:600:0x13)
[    3.252019] ata3: SATA link down (SStatus 0 SControl 300)
[    3.252038] ata5: SATA link down (SStatus 0 SControl 300)
[    3.256176] ata2.00: configured for UDMA/33
[    3.261902] scsi 1:0:0:0: CD-ROM            HL-DT-ST DVDRAM GSA-H10N  JL10 PQ: 0 ANSI: 5
[    3.268034] sr0: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
[    3.268038] cdrom: Uniform CD-ROM driver Revision: 3.20
[    3.268196] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    3.268287] sr 1:0:0:0: Attached scsi generic sg0 type 5
[    3.736029] ata4: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    3.744210] ata4.00: ATA-7: SAMSUNG HD160JJ, ZM100-41, max UDMA7
[    3.744214] ata4.00: 312581808 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    3.784198] ata4.00: configured for UDMA/133
[    3.784332] scsi 3:0:0:0: Direct-Access     ATA      SAMSUNG HD160JJ  ZM10 PQ: 0 ANSI: 5
[    3.784556] sd 3:0:0:0: Attached scsi generic sg1 type 0
[    3.784690] sd 3:0:0:0: [sda] 312581808 512-byte logical blocks: (160 GB/149 GiB)
[    3.784746] sd 3:0:0:0: [sda] Write Protect is off
[    3.784750] sd 3:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    3.784775] sd 3:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    3.816066]  sda: sda1 sda2 < sda5 sda6 >
[    3.816471] sd 3:0:0:0: [sda] Attached SCSI disk
[    4.017945] scsi 7:0:0:0: Direct-Access     SanDisk  Cruzer           4.05 PQ: 0 ANSI: 2
[    4.054433] scsi 6:0:0:0: Direct-Access     SAMSUNG  HM321HI               PQ: 0 ANSI: 2 CCS
[    4.054897] sd 6:0:0:0: Attached scsi generic sg2 type 0
[    4.055495] sd 7:0:0:0: Attached scsi generic sg3 type 0
[    4.056175] sd 6:0:0:0: [sdb] 625142448 512-byte logical blocks: (320 GB/298 GiB)
[    4.056919] sd 7:0:0:0: [sdc] 8027789 512-byte logical blocks: (4.11 GB/3.82 GiB)
[    4.057421] sd 7:0:0:0: [sdc] Write Protect is off
[    4.057426] sd 7:0:0:0: [sdc] Mode Sense: 03 00 00 00
[    4.057545] sd 6:0:0:0: [sdb] Write Protect is off
[    4.057548] sd 6:0:0:0: [sdb] Mode Sense: 28 00 00 00
[    4.058169] sd 7:0:0:0: [sdc] No Caching mode page present
[    4.058173] sd 7:0:0:0: [sdc] Assuming drive cache: write through
[    4.059551] sd 6:0:0:0: [sdb] Incomplete mode parameter data
[    4.059557] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[    4.061295] sd 7:0:0:0: [sdc] No Caching mode page present
[    4.061299] sd 7:0:0:0: [sdc] Assuming drive cache: write through
[    4.061994]  sdc: sdc1
[    4.064293] sd 7:0:0:0: [sdc] No Caching mode page present
[    4.064298] sd 7:0:0:0: [sdc] Assuming drive cache: write through
[    4.064301] sd 7:0:0:0: [sdc] Attached SCSI removable disk
[    4.064667] sd 6:0:0:0: [sdb] Incomplete mode parameter data
[    4.064670] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[    4.065236]  sdb: sdb1
[    4.069669] sd 6:0:0:0: [sdb] Incomplete mode parameter data
[    4.069673] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[    4.069677] sd 6:0:0:0: [sdb] Attached SCSI disk
[    4.096023] ata6: SATA link down (SStatus 0 SControl 300)
[    4.138371] usbcore: registered new interface driver usbhid
[    4.138376] usbhid: USB HID core driver
[    4.160892] input: A4Tech USB Mouse as /devices/pci0000:00/0000:00:02.0/usb2/2-4/2-4:1.0/input/input3
[    4.161354] a4tech 0003:09DA:000A.0001: input,hidraw0: USB HID v1.10 Mouse [A4Tech USB Mouse] on usb-0000:00:02.0-4/input0
[    4.560616] EXT4-fs (sda6): mounted filesystem with ordered data mode. Opts: (null)
[   16.698498] Adding 1897468k swap on /dev/sda5.  Priority:-1 extents:1 across:1897468k 
[   16.764709] <30>udev[333]: starting version 167
[   16.859187] lp: driver loaded but no devices found
[   16.897681] EXT4-fs (sda6): re-mounted. Opts: errors=remount-ro
[   17.203517] i2c i2c-0: nForce2 SMBus adapter at 0xf800
[   17.205928] i2c i2c-1: nForce2 SMBus adapter at 0xf400
[   17.253681] type=1400 audit(1304794049.521:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=530 comm="apparmor_parser"
[   17.268252] type=1400 audit(1304794049.537:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=530 comm="apparmor_parser"
[   17.268553] type=1400 audit(1304794049.537:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=530 comm="apparmor_parser"
[   17.563238] parport_pc 00:09: reported by Plug and Play ACPI
[   17.563285] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
[   17.578308] r8169 0000:03:00.0: eth0: link down
[   17.584325] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   17.652059] lp0: using parport0 (interrupt-driven).
[   17.864266] k8temp 0000:00:18.3: Temperature readouts might be wrong - check erratum #141
[   18.332104] type=1400 audit(1304794050.601:5): apparmor="STATUS" operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" pid=744 comm="apparmor_parser"
[   18.339547] type=1400 audit(1304794050.605:6): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=745 comm="apparmor_parser"
[   18.344604] type=1400 audit(1304794050.613:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=745 comm="apparmor_parser"
[   18.344913] type=1400 audit(1304794050.613:8): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=745 comm="apparmor_parser"
[   18.364747] type=1400 audit(1304794050.633:9): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince" pid=746 comm="apparmor_parser"
[   18.400504] type=1400 audit(1304794050.669:10): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince-previewer" pid=746 comm="apparmor_parser"
[   18.406771] type=1400 audit(1304794050.673:11): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince-thumbnailer" pid=746 comm="apparmor_parser"
[   18.879706] nvidia: module license 'NVIDIA' taints kernel.
[   18.879712] Disabling lock debugging due to kernel taint
[   18.984260] ppdev: user-space parallel port driver
[   19.717436] r8169 0000:03:00.0: eth0: link up
[   19.781950] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   19.837988] ACPI: PCI Interrupt Link [APC3] enabled at IRQ 18
[   19.838011] nvidia 0000:05:00.0: PCI INT A -> Link[APC3] -> GSI 18 (level, low) -> IRQ 18
[   19.838020] nvidia 0000:05:00.0: setting latency timer to 64
[   19.838026] vgaarb: device changed decodes: PCI:0000:05:00.0,olddecodes=io+mem,decodes=none:owns=io+mem
[   19.846764] NVRM: loading NVIDIA UNIX x86 Kernel Module  173.14.30  Thu Apr 14 08:47:14 PDT 2011
[   19.954570] ACPI: PCI Interrupt Link [APCJ] enabled at IRQ 23
[   19.954579] Intel ICH 0000:00:04.0: PCI INT A -> Link[APCJ] -> GSI 23 (level, low) -> IRQ 23
[   19.954609] Intel ICH 0000:00:04.0: setting latency timer to 64
[   20.275764] EXT4-fs (sda6): re-mounted. Opts: errors=remount-ro,commit=0
[   20.276192] intel8x0_measure_ac97_clock: measured 54798 usecs (2688 samples)
[   20.276197] intel8x0: clocking to 46970
[   20.698609] vesafb: framebuffer at 0xd0000000, mapped to 0xf8280000, using 5120k, total 5120k
[   20.698615] vesafb: mode is 1280x1024x32, linelength=5120, pages=0
[   20.698618] vesafb: scrolling: redraw
[   20.698622] vesafb: Truecolor: size=8:8:8:8, shift=24:16:8:0
[   20.698912] Console: switching to colour frame buffer device 160x64
[   20.698961] fb0: VESA VGA frame buffer device
[   25.192399] EXT4-fs (sda6): re-mounted. Opts: errors=remount-ro,commit=0
[   30.160021] eth0: no IPv6 routers present
[  398.114827] show_signal_msg: 15 callbacks suppressed
[  398.114839] polkit-gnome-au[1474]: segfault at 1c ip 00208ec8 sp bfd105d0 error 4 in libglib-2.0.so.0.2800.6[1e5000+d5000]
```

---

### Post by wua on 2011-05-09
Anything?

---

