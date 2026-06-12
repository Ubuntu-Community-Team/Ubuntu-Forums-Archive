---
title: "Does not always fully load"
date: 2012-06-13
forum: General Help
---

### Post by christon74 on 2012-06-13
Hello everyone :)

Sometimes Ubuntu does not load completely. I get the screen and icons, but when I click on any of them, nothing happens. No connection, no wp, no mail, no nothing and everything is kind of 'frozen':confused:. I then need restart the computer and hope wicd asks for my password to connect or start any application. Why? 

Thanks in advance for any piece of advice.

C.NAUD

---

### Post by Kira_Belka on 2012-06-14
> **christon74 said:**
> Hello everyone :)

Sometimes Ubuntu does not load completely. I get the screen and icons, but when I click on any of them, nothing happens. No connection, no wp, no mail, no nothing and everything is kind of 'frozen':confused:. I then need restart the computer and hope wicd asks for my password to connect or start any application. Why? 

Thanks in advance for any piece of advice.

C.NAUD
post result of 
> dmesg
please.

---

### Post by christon74 on 2012-06-14
Hello Kira :)

But err... what is 'dmesg'? I have no bluetooth peripherals connected to this PC......
Anyway, I have just typed the command to the terminal and I just have to wait and see what happens next time I turn the computer back on.....

---

### Post by codingman on 2012-06-14
Please reread Kira_Belka's post. You were supposed to post the output of it.

---

### Post by codingman on 2012-06-14
Oh, and by the way, are you in Unity?
If so, try doing ```
unity --reset
```

---

### Post by christon74 on 2012-06-14
aaaah, ok! result of dmesg follows. 'Unity'? what is unity?  sorry but I am rather new to Ubuntu. I started with Maverick Meerkat a wee while ago.....
[    0.434451] NetLabel: Initializing
[    0.434509] NetLabel:  domain hash size = 128
[    0.436042] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.436126] NetLabel:  unlabeled traffic allowed by default
[    0.436250] HPET: 3 timers in total, 0 timers will be used for per-cpu timer
[    0.436250] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[    0.436326] hpet0: 3 comparators, 64-bit 14.318180 MHz counter
[    0.448199] Switching to clocksource hpet
[    0.470386] AppArmor: AppArmor Filesystem Enabled
[    0.470519] pnp: PnP ACPI init
[    0.470611] ACPI: bus type pnp registered
[    0.470971] pnp 00:00: [bus 00-ff]
[    0.470980] pnp 00:00: [io  0x0cf8-0x0cff]
[    0.470988] pnp 00:00: [io  0x0000-0x0cf7 window]
[    0.470996] pnp 00:00: [io  0x0d00-0xffff window]
[    0.471004] pnp 00:00: [mem 0x000a0000-0x000bffff window]
[    0.471012] pnp 00:00: [mem 0x000d0000-0x000dffff window]
[    0.471021] pnp 00:00: [mem 0x3f700000-0xdfffffff window]
[    0.471029] pnp 00:00: [mem 0xf0000000-0xfed8ffff window]
[    0.471166] pnp 00:00: Plug and Play ACPI device, IDs PNP0a08 PNP0a03 (active)
[    0.471204] pnp 00:01: [mem 0xfed14000-0xfed19fff]
[    0.471213] pnp 00:01: [mem 0xfed90000-0xfed93fff]
[    0.471343] system 00:01: [mem 0xfed14000-0xfed19fff] has been reserved
[    0.471413] system 00:01: [mem 0xfed90000-0xfed93fff] has been reserved
[    0.471480] system 00:01: Plug and Play ACPI device, IDs PNP0c01 (active)
[    0.471583] pnp 00:02: [dma 4]
[    0.471591] pnp 00:02: [io  0x0000-0x000f]
[    0.471598] pnp 00:02: [io  0x0081-0x0083]
[    0.471605] pnp 00:02: [io  0x0087]
[    0.471612] pnp 00:02: [io  0x0089-0x008b]
[    0.471618] pnp 00:02: [io  0x008f]
[    0.471625] pnp 00:02: [io  0x00c0-0x00df]
[    0.471708] pnp 00:02: Plug and Play ACPI device, IDs PNP0200 (active)
[    0.471746] pnp 00:03: [io  0x0070-0x0071]
[    0.471767] pnp 00:03: [irq 8]
[    0.471852] pnp 00:03: Plug and Play ACPI device, IDs PNP0b00 (active)
[    0.471884] pnp 00:04: [io  0x0061]
[    0.471969] pnp 00:04: Plug and Play ACPI device, IDs PNP0800 (active)
[    0.472038] pnp 00:05: [io  0x00f0-0x00ff]
[    0.472055] pnp 00:05: [irq 13]
[    0.472142] pnp 00:05: Plug and Play ACPI device, IDs PNP0c04 (active)
[    0.473926] pnp 00:06: [io  0x03f8-0x03ff]
[    0.473948] pnp 00:06: [irq 4]
[    0.473956] pnp 00:06: [dma 0 disabled]
[    0.474281] pnp 00:06: Plug and Play ACPI device, IDs PNP0501 (active)
[    0.476085] pnp 00:07: [io  0x02f8-0x02ff]
[    0.476106] pnp 00:07: [irq 3]
[    0.476113] pnp 00:07: [dma 0 disabled]
[    0.476446] pnp 00:07: Plug and Play ACPI device, IDs PNP0501 (active)
[    0.480587] pnp 00:08: [io  0x0378-0x037f]
[    0.480610] pnp 00:08: [irq 7]
[    0.480618] pnp 00:08: [dma 0 disabled]
[    0.481585] pnp 00:08: Plug and Play ACPI device, IDs PNP0400 (active)
[    0.481977] pnp 00:09: [io  0x0010-0x001f]
[    0.481986] pnp 00:09: [io  0x0022-0x003f]
[    0.481993] pnp 00:09: [io  0x0044-0x005f]
[    0.482000] pnp 00:09: [io  0x0062-0x0063]
[    0.482007] pnp 00:09: [io  0x0065-0x006f]
[    0.482014] pnp 00:09: [io  0x0072-0x007f]
[    0.482020] pnp 00:09: [io  0x0080]
[    0.482027] pnp 00:09: [io  0x0084-0x0086]
[    0.482034] pnp 00:09: [io  0x0088]
[    0.482046] pnp 00:09: [io  0x008c-0x008e]
[    0.482053] pnp 00:09: [io  0x0090-0x009f]
[    0.482060] pnp 00:09: [io  0x00a2-0x00bf]
[    0.482067] pnp 00:09: [io  0x00e0-0x00ef]
[    0.482074] pnp 00:09: [io  0x04d0-0x04d1]
[    0.482081] pnp 00:09: [io  0x0800-0x087f]
[    0.482089] pnp 00:09: [io  0x0000-0xffffffffffffffff disabled]
[    0.482097] pnp 00:09: [io  0x0480-0x04bf]
[    0.482104] pnp 00:09: [mem 0xfed1c000-0xfed1ffff]
[    0.482112] pnp 00:09: [mem 0xfed20000-0xfed3ffff]
[    0.482119] pnp 00:09: [mem 0xfed40000-0xfed8ffff]
[    0.482299] system 00:09: [io  0x04d0-0x04d1] has been reserved
[    0.482369] system 00:09: [io  0x0800-0x087f] has been reserved
[    0.482433] system 00:09: [io  0x0480-0x04bf] has been reserved
[    0.482498] system 00:09: [mem 0xfed1c000-0xfed1ffff] has been reserved
[    0.482564] system 00:09: [mem 0xfed20000-0xfed3ffff] has been reserved
[    0.482629] system 00:09: [mem 0xfed40000-0xfed8ffff] has been reserved
[    0.482697] system 00:09: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.482898] pnp 00:0a: [mem 0xfed00000-0xfed003ff]
[    0.482998] pnp 00:0a: Plug and Play ACPI device, IDs PNP0103 (active)
[    0.483165] pnp 00:0b: [mem 0xffb00000-0xffbfffff]
[    0.483174] pnp 00:0b: [mem 0xfff00000-0xffffffff]
[    0.483264] pnp 00:0b: Plug and Play ACPI device, IDs INT0800 (active)
[    0.483401] pnp 00:0c: [mem 0xffc00000-0xffefffff]
[    0.483532] system 00:0c: [mem 0xffc00000-0xffefffff] has been reserved
[    0.483602] system 00:0c: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.483912] pnp 00:0d: [mem 0xfec00000-0xfec00fff]
[    0.483921] pnp 00:0d: [mem 0xfee00000-0xfee00fff]
[    0.484107] system 00:0d: [mem 0xfec00000-0xfec00fff] could not be reserved
[    0.484181] system 00:0d: [mem 0xfee00000-0xfee00fff] has been reserved
[    0.484250] system 00:0d: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.484351] pnp 00:0e: [io  0x0060]
[    0.484359] pnp 00:0e: [io  0x0064]
[    0.484380] pnp 00:0e: [irq 1]
[    0.484495] pnp 00:0e: Plug and Play ACPI device, IDs PNP0303 PNP030b (active)
[    0.484644] pnp 00:0f: [irq 12]
[    0.484750] pnp 00:0f: Plug and Play ACPI device, IDs PNP0f03 PNP0f13 (active)
[    0.485226] pnp 00:10: [io  0x0000-0xffffffffffffffff disabled]
[    0.485236] pnp 00:10: [io  0x0a00-0x0a0f]
[    0.485243] pnp 00:10: [io  0x0a10-0x0a1f]
[    0.485250] pnp 00:10: [io  0x0a20-0x0a2f]
[    0.485257] pnp 00:10: [io  0x0a30-0x0a3f]
[    0.485391] system 00:10: [io  0x0a00-0x0a0f] has been reserved
[    0.485467] system 00:10: [io  0x0a10-0x0a1f] has been reserved
[    0.485531] system 00:10: [io  0x0a20-0x0a2f] has been reserved
[    0.485594] system 00:10: [io  0x0a30-0x0a3f] has been reserved
[    0.485659] system 00:10: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.485816] pnp 00:11: [mem 0xe0000000-0xefffffff]
[    0.485957] system 00:11: [mem 0xe0000000-0xefffffff] has been reserved
[    0.486026] system 00:11: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.486573] pnp 00:12: [mem 0x00000000-0x0009ffff]
[    0.486583] pnp 00:12: [mem 0x000c0000-0x000cffff]
[    0.486591] pnp 00:12: [mem 0x000e0000-0x000fffff]
[    0.486598] pnp 00:12: [mem 0x00100000-0x3f6fffff]
[    0.486606] pnp 00:12: [mem 0xfed90000-0xffffffff]
[    0.486765] system 00:12: [mem 0x00000000-0x0009ffff] could not be reserved
[    0.486836] system 00:12: [mem 0x000c0000-0x000cffff] could not be reserved
[    0.486903] system 00:12: [mem 0x000e0000-0x000fffff] could not be reserved
[    0.486970] system 00:12: [mem 0x00100000-0x3f6fffff] could not be reserved
[    0.487048] system 00:12: [mem 0xfed90000-0xffffffff] could not be reserved
[    0.487118] system 00:12: Plug and Play ACPI device, IDs PNP0c01 (active)
[    0.487543] pnp: PnP ACPI: found 19 devices
[    0.487599] ACPI: ACPI bus type pnp unregistered
[    0.487657] PnPBIOS: Disabled by ACPI PNP
[    0.529864] PCI: max bus depth: 1 pci_try_num: 2
[    0.529923] pci 0000:00:1c.0: BAR 14: assigned [mem 0x40000000-0x401fffff]
[    0.530002] pci 0000:00:1c.0: BAR 15: assigned [mem 0x40200000-0x403fffff 64bit pref]
[    0.530093] pci 0000:00:1c.0: BAR 13: assigned [io  0x1000-0x1fff]
[    0.530156] pci 0000:00:1c.0: PCI bridge to [bus 01-01]
[    0.530216] pci 0000:00:1c.0:   bridge window [io  0x1000-0x1fff]
[    0.530282] pci 0000:00:1c.0:   bridge window [mem 0x40000000-0x401fffff]
[    0.530349] pci 0000:00:1c.0:   bridge window [mem 0x40200000-0x403fffff 64bit pref]
[    0.530438] pci 0000:00:1c.1: PCI bridge to [bus 02-02]
[    0.530497] pci 0000:00:1c.1:   bridge window [io  0xe000-0xefff]
[    0.530563] pci 0000:00:1c.1:   bridge window [mem 0xfeb00000-0xfebfffff]
[    0.530640] pci 0000:00:1c.1:   bridge window [mem 0xfdf00000-0xfdffffff 64bit pref]
[    0.530730] pci 0000:00:1e.0: PCI bridge to [bus 03-03]
[    0.530807] pci 0000:00:1c.0: enabling device (0104 -> 0107)
[    0.530896] pci 0000:00:1c.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.530965] pci 0000:00:1c.0: setting latency timer to 64
[    0.530993] pci 0000:00:1c.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    0.531060] pci 0000:00:1c.1: setting latency timer to 64
[    0.531075] pci 0000:00:1e.0: setting latency timer to 64
[    0.531086] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
[    0.531094] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff]
[    0.531102] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
[    0.531111] pci_bus 0000:00: resource 7 [mem 0x000d0000-0x000dffff]
[    0.531119] pci_bus 0000:00: resource 8 [mem 0x3f700000-0xdfffffff]
[    0.531128] pci_bus 0000:00: resource 9 [mem 0xf0000000-0xfed8ffff]
[    0.531136] pci_bus 0000:01: resource 0 [io  0x1000-0x1fff]
[    0.531144] pci_bus 0000:01: resource 1 [mem 0x40000000-0x401fffff]
[    0.531153] pci_bus 0000:01: resource 2 [mem 0x40200000-0x403fffff 64bit pref]
[    0.531162] pci_bus 0000:02: resource 0 [io  0xe000-0xefff]
[    0.531170] pci_bus 0000:02: resource 1 [mem 0xfeb00000-0xfebfffff]
[    0.531179] pci_bus 0000:02: resource 2 [mem 0xfdf00000-0xfdffffff 64bit pref]
[    0.531188] pci_bus 0000:03: resource 4 [io  0x0000-0x0cf7]
[    0.531196] pci_bus 0000:03: resource 5 [io  0x0d00-0xffff]
[    0.531204] pci_bus 0000:03: resource 6 [mem 0x000a0000-0x000bffff]
[    0.531213] pci_bus 0000:03: resource 7 [mem 0x000d0000-0x000dffff]
[    0.531222] pci_bus 0000:03: resource 8 [mem 0x3f700000-0xdfffffff]
[    0.531231] pci_bus 0000:03: resource 9 [mem 0xf0000000-0xfed8ffff]
[    0.531342] NET: Registered protocol family 2
[    0.531586] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.532274] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.533345] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.533905] TCP: Hash tables configured (established 131072 bind 65536)
[    0.533996] TCP reno registered
[    0.534058] UDP hash table entries: 512 (order: 2, 16384 bytes)
[    0.534145] UDP-Lite hash table entries: 512 (order: 2, 16384 bytes)
[    0.534422] NET: Registered protocol family 1
[    0.534517] pci 0000:00:02.0: Boot video device
[    0.534573] pci 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    0.534657] pci 0000:00:1d.0: PCI INT A disabled
[    0.534739] pci 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    0.534819] pci 0000:00:1d.1: PCI INT B disabled
[    0.534905] pci 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.534993] pci 0000:00:1d.2: PCI INT C disabled
[    0.535063] pci 0000:00:1d.3: PCI INT D -> GSI 16 (level, low) -> IRQ 16
[    0.535143] pci 0000:00:1d.3: PCI INT D disabled
[    0.535212] pci 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    0.535313] pci 0000:00:1d.7: PCI INT A disabled
[    0.535394] PCI: CLS 32 bytes, default 64
[    0.536670] audit: initializing netlink socket (disabled)
[    0.536757] type=2000 audit(1339691250.532:1): initialized
[    0.594133] highmem bounce pool size: 64 pages
[    0.594205] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    0.604619] VFS: Disk quotas dquot_6.5.2
[    0.604866] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.606686] fuse init (API version 7.17)
[    0.607060] msgmni has been set to 1710
[    0.608249] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.608428] io scheduler noop registered
[    0.608485] io scheduler deadline registered
[    0.608572] io scheduler cfq registered (default)
[    0.608907] pcieport 0000:00:1c.0: setting latency timer to 64
[    0.608974] pcieport 0000:00:1c.0: irq 40 for MSI/MSI-X
[    0.609093] pcieport 0000:00:1c.1: setting latency timer to 64
[    0.609149] pcieport 0000:00:1c.1: irq 41 for MSI/MSI-X
[    0.609348] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.609492] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.609742] intel_idle: MWAIT substates: 0x10
[    0.609763] intel_idle: v0.4 model 0x1C
[    0.609768] intel_idle: lapic_timer_reliable_states 0x2
[    0.610056] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0
[    0.610159] ACPI: Power Button [PWRB]
[    0.610371] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
[    0.610459] ACPI: Power Button [PWRF]
[    0.621101] thermal LNXTHERM:00: registered as thermal_zone0
[    0.621169] ACPI: Thermal Zone [THRM] (40 C)
[    0.621329] ERST: Table is not found!
[    0.621389] GHES: HEST is not enabled!
[    0.621640] isapnp: Scanning for PnP cards...
[    0.621768] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    0.642279] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.740409] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[    0.974763] isapnp: No Plug & Play device found
[    0.996713] Freeing initrd memory: 13796k freed
[    1.252830] 00:06: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    1.320440] 00:07: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[    1.364729] Linux agpgart interface v0.103
[    1.364933] agpgart-intel 0000:00:00.0: Intel GMA3150 Chipset
[    1.365148] agpgart-intel 0000:00:00.0: detected gtt size: 524288K total, 262144K mappable
[    1.365470] agpgart-intel 0000:00:00.0: detected 8192K stolen memory
[    1.365793] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0xd0000000
[    1.369554] brd: module loaded
[    1.371501] loop: module loaded
[    1.371907] ata_piix 0000:00:1f.2: version 2.13
[    1.371931] ata_piix 0000:00:1f.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    1.371996] ata_piix 0000:00:1f.2: MAP [ P0 P2 P1 P3 ]
[    1.372222] ata_piix 0000:00:1f.2: setting latency timer to 64
[    1.372909] scsi0 : ata_piix
[    1.373145] scsi1 : ata_piix
[    1.375678] ata1: SATA max UDMA/133 cmd 0xd080 ctl 0xd000 bmdma 0xc800 irq 19
[    1.375741] ata2: SATA max UDMA/133 cmd 0xcc00 ctl 0xc880 bmdma 0xc808 irq 19
[    1.376656] Fixed MDIO Bus: probed
[    1.376750] tun: Universal TUN/TAP device driver, 1.6
[    1.376803] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    1.376981] PPP generic driver version 2.4.2
[    1.377275] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    1.377367] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    1.377456] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    1.377463] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    1.377615] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 1
[    1.377722] ehci_hcd 0000:00:1d.7: using broken periodic workaround
[    1.377789] ehci_hcd 0000:00:1d.7: debug port 1
[    1.381715] ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported
[    1.381749] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xfea77c00
[    1.396032] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    1.396371] hub 1-0:1.0: USB hub found
[    1.396427] hub 1-0:1.0: 8 ports detected
[    1.397286] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    1.397370] uhci_hcd: USB Universal Host Controller Interface driver
[    1.397466] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    1.397535] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    1.397541] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    1.397703] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    1.397810] uhci_hcd 0000:00:1d.0: irq 23, io base 0x0000d880
[    1.398152] hub 2-0:1.0: USB hub found
[    1.398209] hub 2-0:1.0: 2 ports detected
[    1.398377] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    1.398446] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    1.398453] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    1.398610] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 3
[    1.398721] uhci_hcd 0000:00:1d.1: irq 19, io base 0x0000d800
[    1.399058] hub 3-0:1.0: USB hub found
[    1.399114] hub 3-0:1.0: 2 ports detected
[    1.399281] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    1.399348] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    1.399354] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    1.399511] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 4
[    1.399633] uhci_hcd 0000:00:1d.2: irq 18, io base 0x0000d480
[    1.399964] hub 4-0:1.0: USB hub found
[    1.400044] hub 4-0:1.0: 2 ports detected
[    1.400230] uhci_hcd 0000:00:1d.3: PCI INT D -> GSI 16 (level, low) -> IRQ 16
[    1.400299] uhci_hcd 0000:00:1d.3: setting latency timer to 64
[    1.400305] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[    1.400466] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 5
[    1.400586] uhci_hcd 0000:00:1d.3: irq 16, io base 0x0000d400
[    1.400919] hub 5-0:1.0: USB hub found
[    1.400975] hub 5-0:1.0: 2 ports detected
[    1.401270] usbcore: registered new interface driver libusual
[    1.401448] i8042: PNP: PS/2 Controller [PNP0303:PS2K,PNP0f03:PS2M] at 0x60,0x64 irq 1,12
[    1.401973] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.402046] serio: i8042 AUX port at 0x60,0x64 irq 12
[    1.402471] mousedev: PS/2 mouse device common for all mice
[    1.402861] rtc_cmos 00:03: RTC can wake from S4
[    1.403094] rtc_cmos 00:03: rtc core: registered rtc_cmos as rtc0
[    1.403181] rtc0: alarms up to one month, y3k, 114 bytes nvram, hpet irqs
[    1.403379] device-mapper: uevent: version 1.0.3
[    1.403607] device-mapper: ioctl: 4.22.0-ioctl (2011-10-19) initialised: [email]dm-devel@redhat.com[/email]
[    1.403776] EISA: Probing bus 0 at eisa.0
[    1.403828] EISA: Cannot allocate resource for mainboard
[    1.403883] Cannot allocate resource for EISA slot 1
[    1.403937] Cannot allocate resource for EISA slot 2
[    1.403989] Cannot allocate resource for EISA slot 3
[    1.404072] Cannot allocate resource for EISA slot 4
[    1.404126] Cannot allocate resource for EISA slot 5
[    1.404179] Cannot allocate resource for EISA slot 6
[    1.404232] Cannot allocate resource for EISA slot 7
[    1.404284] Cannot allocate resource for EISA slot 8
[    1.404336] EISA: Detected 0 cards.
[    1.404397] cpufreq-nforce2: No nForce2 chipset.
[    1.404609] cpuidle: using governor ladder
[    1.404922] cpuidle: using governor menu
[    1.404972] EFI Variables Facility v0.08 2004-May-17
[    1.405540] TCP cubic registered
[    1.405865] NET: Registered protocol family 10
[    1.407075] NET: Registered protocol family 17
[    1.407187] Registering the dns_resolver key type
[    1.407285] Using IPI No-Shortcut mode
[    1.407630] PM: Hibernation image not present or could not be loaded.
[    1.407652] registered taskstats version 1
[    1.425199]   Magic number: 0:674:489
[    1.425375] rtc_cmos 00:03: setting system clock to 2012-06-14 16:27:31 UTC (1339691251)
[    1.425508] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.425564] EDD information not available.
[    1.427438] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input2
[    1.532161] ata2.01: NODEV after polling detection
[    1.536345] ata1.00: ATA-8: Hitachi HDS721050CLA362, JP2OA3EA, max UDMA/133
[    1.536409] ata1.00: 976773168 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    1.540150] ata2.00: ATAPI: HL-DT-ST DVDRAM GH22NS50, TN02, max UDMA/100
[    1.552351] ata1.00: configured for UDMA/133
[    1.552683] scsi 0:0:0:0: Direct-Access     ATA      Hitachi HDS72105 JP2O PQ: 0 ANSI: 5
[    1.553125] sd 0:0:0:0: [sda] 976773168 512-byte logical blocks: (500 GB/465 GiB)
[    1.553156] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    1.553470] sd 0:0:0:0: [sda] Write Protect is off
[    1.553526] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.553608] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.556171] ata2.00: configured for UDMA/100
[    1.565484] scsi 1:0:0:0: CD-ROM            HL-DT-ST DVDRAM GH22NS50  TN02 PQ: 0 ANSI: 5
[    1.574616] sr0: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
[    1.574697] cdrom: Uniform CD-ROM driver Revision: 3.20
[    1.575022] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    1.575318] sr 1:0:0:0: Attached scsi generic sg1 type 5
[    1.610643]  sda: sda1 sda2 < sda5 sda6 >
[    1.611718] sd 0:0:0:0: [sda] Attached SCSI disk
[    1.611906] Freeing unused kernel memory: 740k freed
[    1.612507] Write protecting the kernel text: 5832k
[    1.612608] Write protecting the kernel read-only data: 2380k
[    1.612664] NX-protecting the kernel data: 4408k
[    1.678419] udevd[116]: starting version 175
[    1.708146] usb 1-7: new high-speed USB device number 2 using ehci_hcd
[    1.770774] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    1.770915] r8169 0000:02:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    1.771049] r8169 0000:02:00.0: setting latency timer to 64
[    1.771145] r8169 0000:02:00.0: irq 42 for MSI/MSI-X
[    1.772730] r8169 0000:02:00.0: eth0: RTL8168d/8111d at 0xf841e000, d0:27:88:05:b1:32, XID 083000c0 IRQ 42
[    1.772859] r8169 0000:02:00.0: eth0: jumbo features [frames: 9200 bytes, tx checksumming: ko]
[    1.845525] Initializing USB Mass Storage driver...
[    1.845919] scsi2 : usb-storage 1-7:1.0
[    1.846178] usbcore: registered new interface driver usb-storage
[    1.846252] USB Mass Storage support registered.
[    2.116078] EXT4-fs (sda6): INFO: recovery required on readonly filesystem
[    2.116146] EXT4-fs (sda6): write access will be enabled during recovery
[    2.376099] usb 5-2: new full-speed USB device number 2 using uhci_hcd
[    2.846534] scsi 2:0:0:0: Direct-Access     WD       My Book 1110     2018 PQ: 0 ANSI: 4
[    2.848785] scsi 2:0:0:1: CD-ROM            WD       Virtual CD 1110  2018 PQ: 0 ANSI: 4
[    2.851029] scsi 2:0:0:2: Enclosure         WD       SES Device       2018 PQ: 0 ANSI: 4
[    2.852961] sd 2:0:0:0: Attached scsi generic sg2 type 0
[    2.854808] sd 2:0:0:0: [sdb] 1463775232 512-byte logical blocks: (749 GB/697 GiB)
[    2.856665] sr1: scsi3-mmc drive: 51x/51x caddy
[    2.857105] sr 2:0:0:1: Attached scsi CD-ROM sr1
[    2.857393] sr 2:0:0:1: Attached scsi generic sg3 type 5
[    2.858038] scsi 2:0:0:2: Attached scsi generic sg4 type 13
[    2.858650] sd 2:0:0:0: [sdb] Write Protect is off
[    2.858730] sd 2:0:0:0: [sdb] Mode Sense: 2b 00 10 08
[    2.861565] sd 2:0:0:0: [sdb] No Caching mode page present
[    2.861636] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[    2.867771] sd 2:0:0:0: [sdb] No Caching mode page present
[    2.867839] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[    2.906534]  sdb: sdb1 sdb2 < sdb5 sdb6 >
[    2.912890] sd 2:0:0:0: [sdb] No Caching mode page present
[    2.912972] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[    2.913039] sd 2:0:0:0: [sdb] Attached SCSI disk
[    2.926828] EXT4-fs (sda6): orphan cleanup on readonly fs
[    2.926909] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 8917542
[    2.927077] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 8917541
[    2.927253] EXT4-fs (sda6): 2 orphan inodes deleted
[    2.927333] EXT4-fs (sda6): recovery complete
[    2.958929] ses 2:0:0:2: Attached Enclosure device
[    3.136059] EXT4-fs (sda6): mounted filesystem with ordered data mode. Opts: (null)
[    6.300643] udevd[303]: starting version 175
[    8.872292] parport_pc 00:08: reported by Plug and Play ACPI
[    8.872438] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
[    8.962537] ppdev: user-space parallel port driver
[    8.983950] input: GenPS/2 Genius Mouse as /devices/platform/i8042/serio1/input/input3
[    9.260520] [drm] Initialized drm 1.1.0 20060810
[    9.601956] pci 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    9.602039] pci 0000:00:02.0: setting latency timer to 64
[    9.640657] pci 0000:00:02.0: irq 43 for MSI/MSI-X
[    9.640668] [drm] Supports vblank timestamp caching Rev 1 (10.10.2010).
[    9.640731] [drm] No driver support for vblank timestamp query.
[    9.640877] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
[    9.848704] ADDRCONF(NETDEV_UP): eth0: link is not ready
[    9.940304] snd_hda_intel 0000:00:1b.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    9.940409] snd_hda_intel 0000:00:1b.0: irq 44 for MSI/MSI-X
[    9.940454] snd_hda_intel 0000:00:1b.0: setting latency timer to 64
[   10.025642] input: HDA Intel Line as /devices/pci0000:00/0000:00:1b.0/sound/card0/input4
[   10.025871] input: HDA Intel Front Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input5
[   10.026060] input: HDA Intel Rear Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input6
[   10.026248] input: HDA Intel Front Headphone as /devices/pci0000:00/0000:00:1b.0/sound/card0/input7
[   10.026437] input: HDA Intel Line-Out as /devices/pci0000:00/0000:00:1b.0/sound/card0/input8
[   19.982417] Adding 3068924k swap on /dev/sda5.  Priority:-1 extents:1 across:3068924k 
[   20.236978] EXT4-fs (sda6): re-mounted. Opts: errors=remount-ro
[  133.898107] lp0: using parport0 (interrupt-driven).
[  148.035810] init: udev-fallback-graphics main process (1274) terminated with status 1
[  148.510118] init: failsafe main process (1353) killed by TERM signal
[  148.695707] init: friendly-recovery post-stop process (1019) terminated with status 1
[  150.716588] type=1400 audit(1339691400.787:2): apparmor="STATUS" operation="profile_load" name="/usr/lib/lightdm/lightdm/lightdm-guest-session-wrapper" pid=1526 comm="apparmor_parser"
[  150.893881] type=1400 audit(1339691400.963:3): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=1527 comm="apparmor_parser"
[  150.894786] type=1400 audit(1339691400.963:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=1527 comm="apparmor_parser"
[  150.895291] type=1400 audit(1339691400.963:5): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=1527 comm="apparmor_parser"
[  150.934011] type=1400 audit(1339691401.003:6): apparmor="STATUS" operation="profile_load" name="/usr/bin/freshclam" pid=1530 comm="apparmor_parser"
[  150.974021] type=1400 audit(1339691401.043:7): apparmor="STATUS" operation="profile_load" name="/usr/lib/telepathy/mission-control-5" pid=1532 comm="apparmor_parser"
[  150.975055] type=1400 audit(1339691401.043:8): apparmor="STATUS" operation="profile_load" name="/usr/lib/telepathy/telepathy-*" pid=1532 comm="apparmor_parser"
[  151.004564] type=1400 audit(1339691401.075:9): apparmor="STATUS" operation="profile_load" name="/usr/sbin/clamd" pid=1533 comm="apparmor_parser"
[  151.028041] type=1400 audit(1339691401.095:10): apparmor="STATUS" operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" pid=1534 comm="apparmor_parser"
[  151.029598] type=1400 audit(1339691401.099:11): apparmor="STATUS" operation="profile_load" name="/usr/sbin/cupsd" pid=1534 comm="apparmor_parser"
[  153.892675] init: kdm main process (1629) killed by TERM signal
[  154.658690] Bluetooth: Core ver 2.16
[  154.658750] NET: Registered protocol family 31
[  154.658757] Bluetooth: HCI device and connection manager initialized
[  154.658766] Bluetooth: HCI socket layer initialized
[  154.658772] Bluetooth: L2CAP socket layer initialized
[  154.658791] Bluetooth: SCO socket layer initialized
[  154.792362] Bluetooth: RFCOMM TTY layer initialized
[  154.792378] Bluetooth: RFCOMM socket layer initialized
[  154.792385] Bluetooth: RFCOMM ver 1.11
[  155.431947] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[  155.431957] Bluetooth: BNEP filters: protocol multicast
[  155.521730] r8169 0000:02:00.0: eth0: link down
[  155.521751] r8169 0000:02:00.0: eth0: link down
[  155.522422] ADDRCONF(NETDEV_UP): eth0: link is not ready
[  155.523575] ADDRCONF(NETDEV_UP): eth0: link is not ready
[  157.156580] r8169 0000:02:00.0: eth0: link up
[  157.157078] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[  167.408044] eth0: no IPv6 routers present
[  172.913205] UDF-fs: Partition marked readonly; forcing readonly mount
[  172.913848] UDF-fs: INFO Mounting volume 'WD SmartWare', timestamp 2009/11/14 02:34 (1078)
[  173.515750] EXT4-fs (sdb5): warning: maximal mount count reached, running e2fsck is recommended
[  173.611309] EXT4-fs (sdb5): recovery complete
[  173.611320] EXT4-fs (sdb5): mounted filesystem with ordered data mode. Opts: (null)
[  188.431081] init: plymouth-stop pre-start process (2779) terminated with status 1
christon74@christophe-TPS01:~$

---

### Post by christon74 on 2012-06-26
> **codingman said:**
> Please reread Kira_Belka's post. You were supposed to post the output of it.

[FONT=Courier New][COLOR=green]Lets not Whine Please!

whining? But I should be fuming, yes: I have got rid of Unity. Now I can no longer log on to Ununtu because my password is not recognized!!! uh!! I have not changed it. I have tried a rescue and now I find myself with a pink screen with a white strip at the bottom and two # at the bottom left corner (I have pressed the enter twice). I am starting to think I should do a fresh install... and lose all the data I have already stored. Thank you very much.
[/COLOR][/FONT]

---

### Post by Cheesemill on 2012-06-26
> **christon74 said:**
> [FONT=Courier New][COLOR=green]Lets not Whine Please!

whining? But I should be fuming, yes: I have got rid of Unity. Now I can no longer log on to Ununtu because my password is not recognized!!! uh!! I have not changed it. I have tried a rescue and now I find myself with a pink screen with a white strip at the bottom and two # at the bottom left corner (I have pressed the enter twice). I am starting to think I should do a fresh install... and lose all the data I have already stored. Thank you very much.
[/COLOR][/FONT]

Who told you to un-install Unity?

The command posted above, 'unity --reset' just resets Unity to a clean state.

---

### Post by christon74 on 2012-06-26
conclusion: Think carefully before uninstalling Unity... or you might find yourself in the deep blue sea.

---

### Post by idoitprone on 2012-06-26
> **christon74 said:**
> [FONT=Courier New][COLOR=green]Lets not Whine Please!

whining? But I should be fuming, yes: I have got rid of Unity. Now I can no longer log on to Ununtu because my password is not recognized!!! uh!! I have not changed it. I have tried a rescue and now I find myself with a pink screen with a white strip at the bottom and two # at the bottom left corner (I have pressed the enter twice). I am starting to think I should do a fresh install... and lose all the data I have already stored. Thank you very much.
[/COLOR][/FONT]

linux by default does not protect their users. If you want to be protected buy a mac. Of course, you will lose all your rights to Tim Cook, who doesnt care about user choice anymore

If you remove unity-desktop, then you do not have a working desktop

hit```
 ctrl+alt+f2
```enter you user name and pass word

reinstall you desktop

Here you have a choice

[http://xubuntu.org/](http://xubuntu.org/)

enter this command
```
sudo apt-get install xubuntu-desktop
```[http://lubuntu.net/](http://lubuntu.net/)
```
sudo apt-get install lubuntu-desktop
```[http://www.kubuntu.org/](http://www.kubuntu.org/)

```
sudo apt-get install kubuntu-desktop
```gnome 3http://www.google.com/imgres?imgurl=http://cdn2.sudobits.com/wp-content/uploads/2011/03/gnome-3-snapshot.jpg&imgrefurl=http://blog.sudobits.com/2011/04/26/how-to-install-gnome-3-on-ubuntu-11-04/&h=415&w=519&sz=40&tbnid=e-bzeeAkuE7R9M:&tbnh=90&tbnw=113&prev=/search%3Fq%3Dgnome%2B3%2Bubuntu%2Bwiki%26tbm%3Disch%26tbo%3Du&zoom=1&q=gnome+3+ubuntu+wiki&usg=__UQyUxv4EbdlsPHXgKLtfEf6PMVE=&docid=HL9sC3OGRKFGkM&hl=en&sa=X&ei=PgXqT_DIBOW22gXPudXiCA&ved=0CHIQ9QEwBw&dur=552

```
sudo apt-get install gnome-desktop-environment
```or unity the desktop that you just removed

```
sudo apt-get --reinstall ubuntu-desktop
```then reboot

```
sudo shutdown -r now
```

---

### Post by christon74 on 2012-06-27
Too late. sorry, I have done a fresh install

---

### Post by christon74 on 2012-06-27
"remove your unity' has written codingman. And there is a link to this page:
[http://ubuntublog.org/how-to-remove-unity-desktop-in-ubuntu-12-04.htm](http://ubuntublog.org/how-to-remove-unity-desktop-in-ubuntu-12-04.htm)
suggesting that you uninstall unity to use GNOME desktop instead

---

### Post by christon74 on 2012-06-27
There, there. Nearly everything is back to normal now. I have lost some documents and some data but at least I can log back on to Ubuntu. I have been taught a lesson and I will NEVER again try to remove Unity.

---

