---
title: "system halt no shutdown ubuntu 9.10"
date: 2009-10-30
forum: General Help
---

### Post by electricroo on 2009-10-30
I did a clean install this time of 9.10. Interesting when shutting down I get a "system halt" message and have to press the power button to turn off the PC. Never had that happen in previous versions. 
I'm sure sooner or later someone will figure it out.

---

### Post by P4man on 2009-10-30
Sounds like acpi is disabled. Either deliberately because its broken on your machine, or because the kernel is not detecting it properly. You could try forcing it, but perhaps post the output of ```
dmesg
``` first,and tell us what system you have?

---

### Post by electricroo on 2009-11-01
Well, actually this is the first time I ran Ubuntu on this board. My other died so I threw this older Chaintech SPT800 with a 2.8g P4 800mhz FSB CPU in. Had XP on it for awhile, was waiting until Ubuntu 9.10 was released before I re-installed. Anyway ACPI is enabled in the Bios, but hey, this board could be hinky also, so I can put up with it!

Here is the text from dmesg.

[    0.000000]   DMA      0x00000000 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x000377fe
[    0.000000]   HighMem  0x000377fe -> 0x0007fff0
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[3] active PFN ranges
[    0.000000]     0: 0x00000000 -> 0x00000002
[    0.000000]     0: 0x00000006 -> 0x0000009f
[    0.000000]     0: 0x00000100 -> 0x0007fff0
[    0.000000] On node 0 totalpages: 524171
[    0.000000] free_area_init_node: node 0, pgdat c0784900, node_mem_map c1000000
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3963 pages, LIFO batch:0
[    0.000000]   Normal zone: 1744 pages used for memmap
[    0.000000]   Normal zone: 221486 pages, LIFO batch:31
[    0.000000]   HighMem zone: 2320 pages used for memmap
[    0.000000]   HighMem zone: 294626 pages, LIFO batch:31
[    0.000000] Using APIC driver default
[    0.000000] Intel MultiProcessor Specification v1.4
[    0.000000]     Virtual Wire compatibility mode.
[    0.000000] MPTABLE: OEM ID: OEM00000
[    0.000000] MPTABLE: Product ID: PROD00000000
[    0.000000] MPTABLE: APIC at: 0xFEE00000
[    0.000000] Processor #0 (Bootup-CPU)
[    0.000000] I/O APIC #2 Version 17 at 0xFEC00000.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] Processors: 1
[    0.000000] SMP: Allowing 1 CPUs, 0 hotplug CPUs
[    0.000000] nr_irqs_gsi: 24
[    0.000000] PM: Registered nosave memory: 0000000000002000 - 0000000000006000
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000f0000
[    0.000000] PM: Registered nosave memory: 00000000000f0000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 80000000 (gap: 80000000:7ec00000)
[    0.000000] NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:1 nr_node_ids:1
[    0.000000] PERCPU: Embedded 14 pages at c200a000, static data 35612 bytes
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 520075
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.31-14-generic root=UUID=7ff998d6-7ac2-40e6-be72-d0ea5f8d9585 ro quiet splash
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] allocated 10485440 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] Initializing HighMem for node 0 (000377fe:0007fff0)
[    0.000000] Memory: 2052948k/2097088k available (4565k kernel code, 42868k reserved, 2143k data, 540k init, 1187784k highmem)
[    0.000000] virtual kernel memory layout:
[    0.000000]     fixmap  : 0xfff1d000 - 0xfffff000   ( 904 kB)
[    0.000000]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[    0.000000]     vmalloc : 0xf7ffe000 - 0xff7fe000   ( 120 MB)
[    0.000000]     lowmem  : 0xc0000000 - 0xf77fe000   ( 887 MB)
[    0.000000]       .init : 0xc078e000 - 0xc0815000   ( 540 kB)
[    0.000000]       .data : 0xc0575554 - 0xc078d308   (2143 kB)
[    0.000000]       .text : 0xc0100000 - 0xc0575554   (4565 kB)
[    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.000000] SLUB: Genslabs=13, HWalign=128, Order=0-3, MinObjects=0, CPUs=1, Nodes=1
[    0.000000] NR_IRQS:2304 nr_irqs:256
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 2827.471 MHz processor.
[    0.002337] Console: colour VGA+ 80x25
[    0.002343] console [tty0] enabled
[    0.004013] Calibrating delay loop (skipped), value calculated using timer frequency.. 5654.94 BogoMIPS (lpj=11309884)
[    0.004041] Security Framework initialized
[    0.004076] AppArmor: AppArmor initialized
[    0.004087] Mount-cache hash table entries: 512
[    0.004272] Initializing cgroup subsys ns
[    0.004280] Initializing cgroup subsys cpuacct
[    0.004286] Initializing cgroup subsys memory
[    0.004299] Initializing cgroup subsys freezer
[    0.004303] Initializing cgroup subsys net_cls
[    0.004330] CPU: Trace cache: 12K uops, L1 D cache: 16K
[    0.004334] CPU: L2 cache: 1024K
[    0.004338] CPU: Unsupported number of siblings 2
[    0.004342] mce: CPU supports 4 MCE banks
[    0.004358] CPU0: Thermal monitoring enabled (TM1)
[    0.004365] using mwait in idle threads.
[    0.004375] Performance Counters: no PMU driver, software counters only.
[    0.004384] Checking 'hlt' instruction... OK.
[    0.021144] SMP alternatives: switching to UP code
[    0.032019] Freeing SMP alternatives: 19k freed
[    0.032380] ExtINT not setup in hardware but reported by MP table
[    0.033028]   alloc irq_desc for 16 on node 0
[    0.033032]   alloc kstat_irqs on node 0
[    0.033037]   alloc irq_desc for 19 on node 0
[    0.033039]   alloc kstat_irqs on node 0
[    0.033043]   alloc irq_desc for 20 on node 0
[    0.033045]   alloc kstat_irqs on node 0
[    0.033048]   alloc irq_desc for 21 on node 0
[    0.033050]   alloc kstat_irqs on node 0
[    0.033054]   alloc irq_desc for 22 on node 0
[    0.033056]   alloc kstat_irqs on node 0
[    0.033059]   alloc irq_desc for 23 on node 0
[    0.033061]   alloc kstat_irqs on node 0
[    0.033236] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=0 pin2=0
[    0.073555] CPU0: Intel(R) Pentium(R) 4 CPU 2.80GHz stepping 03
[    0.180208] Brought up 1 CPUs
[    0.180212] Total of 1 processors activated (5654.94 BogoMIPS).
[    0.180506] CPU0 attaching NULL sched-domain.
[    0.180798] Booting paravirtualized kernel on bare hardware
[    0.181078] regulator: core version 0.5
[    0.181117] Time: 21:39:15  Date: 11/01/09
[    0.181182] NET: Registered protocol family 16
[    0.181348] EISA bus registered
[    0.188778] PCI: PCI BIOS revision 2.10 entry at 0xfad20, last bus=1
[    0.188781] PCI: Using configuration type 1 for base access
[    0.190009] bio: create slab <bio-0> at 0
[    0.190085] ACPI: Interpreter disabled.
[    0.190264] SCSI subsystem initialized
[    0.190313] libata version 3.00 loaded.
[    0.190401] usbcore: registered new interface driver usbfs
[    0.190421] usbcore: registered new interface driver hub
[    0.190455] usbcore: registered new device driver usb
[    0.190595] PCI: Probing PCI hardware
[    0.190600] PCI: Probing PCI hardware (bus 00)
[    0.190650] pci 0000:00:00.0: reg 10 32bit mmio: [0xe0000000-0xe7ffffff]
[    0.190972] pci 0000:00:01.0: supports D1
[    0.191020] pci 0000:00:0c.0: reg 10 32bit mmio: [0xeb000000-0xeb00ffff]
[    0.191029] pci 0000:00:0c.0: reg 14 io port: [0xe000-0xe007]
[    0.191072] pci 0000:00:0c.0: PME# supported from D3hot D3cold
[    0.191077] pci 0000:00:0c.0: PME# disabled
[    0.191119] pci 0000:00:0f.0: reg 10 io port: [0xe100-0xe107]
[    0.191127] pci 0000:00:0f.0: reg 14 io port: [0xe200-0xe203]
[    0.191135] pci 0000:00:0f.0: reg 18 io port: [0xe300-0xe307]
[    0.191143] pci 0000:00:0f.0: reg 1c io port: [0xe400-0xe403]
[    0.191150] pci 0000:00:0f.0: reg 20 io port: [0xe500-0xe50f]
[    0.191158] pci 0000:00:0f.0: reg 24 io port: [0xe600-0xe6ff]
[    0.191239] pci 0000:00:0f.1: reg 20 io port: [0xe700-0xe70f]
[    0.191331] pci 0000:00:10.0: reg 20 io port: [0xe800-0xe81f]
[    0.191360] pci 0000:00:10.0: supports D1 D2
[    0.191363] pci 0000:00:10.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.191368] pci 0000:00:10.0: PME# disabled
[    0.191421] pci 0000:00:10.1: reg 20 io port: [0xe900-0xe91f]
[    0.191451] pci 0000:00:10.1: supports D1 D2
[    0.191453] pci 0000:00:10.1: PME# supported from D0 D1 D2 D3hot D3cold
[    0.191458] pci 0000:00:10.1: PME# disabled
[    0.191513] pci 0000:00:10.2: reg 20 io port: [0xea00-0xea1f]
[    0.191543] pci 0000:00:10.2: supports D1 D2
[    0.191546] pci 0000:00:10.2: PME# supported from D0 D1 D2 D3hot D3cold
[    0.191551] pci 0000:00:10.2: PME# disabled
[    0.191604] pci 0000:00:10.3: reg 20 io port: [0xeb00-0xeb1f]
[    0.191633] pci 0000:00:10.3: supports D1 D2
[    0.191636] pci 0000:00:10.3: PME# supported from D0 D1 D2 D3hot D3cold
[    0.191641] pci 0000:00:10.3: PME# disabled
[    0.191678] pci 0000:00:10.4: reg 10 32bit mmio: [0xeb010000-0xeb0100ff]
[    0.191726] pci 0000:00:10.4: supports D1 D2
[    0.191728] pci 0000:00:10.4: PME# supported from D0 D1 D2 D3hot D3cold
[    0.191733] pci 0000:00:10.4: PME# disabled
[    0.191804] HPET not enabled in BIOS. You might try hpet=force boot option
[    0.191865] pci 0000:00:11.5: reg 10 io port: [0xec00-0xecff]
[    0.191914] pci 0000:00:11.5: supports D1 D2
[    0.191954] pci 0000:00:12.0: reg 10 io port: [0xed00-0xedff]
[    0.191962] pci 0000:00:12.0: reg 14 32bit mmio: [0xeb011000-0xeb0110ff]
[    0.192011] pci 0000:00:12.0: supports D1 D2
[    0.192014] pci 0000:00:12.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.192019] pci 0000:00:12.0: PME# disabled
[    0.192086] pci 0000:01:00.0: reg 10 32bit mmio: [0xe8000000-0xe8ffffff]
[    0.192093] pci 0000:01:00.0: reg 14 32bit mmio: [0xd0000000-0xdfffffff]
[    0.192100] pci 0000:01:00.0: reg 18 32bit mmio: [0xe9000000-0xe9ffffff]
[    0.192119] pci 0000:01:00.0: reg 30 32bit mmio: [0x000000-0x01ffff]
[    0.192182] pci 0000:00:01.0: bridge 32bit mmio: [0xe8000000-0xeaffffff]
[    0.192188] pci 0000:00:01.0: bridge 32bit mmio pref: [0xd0000000-0xdfffffff]
[    0.192749] pci 0000:00:11.0: VIA IRQ router [1106:3227]
[    0.192921] Bluetooth: Core ver 2.15
[    0.192958] NET: Registered protocol family 31
[    0.192961] Bluetooth: HCI device and connection manager initialized
[    0.192964] Bluetooth: HCI socket layer initialized
[    0.192967] NetLabel: Initializing
[    0.192969] NetLabel:  domain hash size = 128
[    0.192971] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.192989] NetLabel:  unlabeled traffic allowed by default
[    0.194914] pnp: PnP ACPI: disabled
[    0.194922] PnPBIOS: Scanning system for PnP BIOS support...
[    0.194990] PnPBIOS: Found PnP BIOS installation structure at 0xc00fb800
[    0.194994] PnPBIOS: PnP BIOS version 1.0, entry 0xf0000:0xb830, dseg 0xf0000
[    0.195854] PnPBIOS: 17 nodes reported by PnP BIOS; 17 recorded by driver
[    0.195872] system 00:07: iomem range 0x0-0x9ffff could not be reserved
[    0.195877] system 00:07: iomem range 0xfffe0000-0xffffffff has been reserved
[    0.195881] system 00:07: iomem range 0xfec00000-0xfec0ffff could not be reserved
[    0.195885] system 00:07: iomem range 0xfee00000-0xfee0ffff has been reserved
[    0.195889] system 00:07: iomem range 0x100000-0xffffff could not be reserved
[    0.195897] system 00:08: iomem range 0xf0000-0xf3fff could not be reserved
[    0.195901] system 00:08: iomem range 0xf4000-0xf7fff could not be reserved
[    0.195904] system 00:08: iomem range 0xf8000-0xfffff could not be reserved
[    0.195908] system 00:08: iomem range 0xcec00-0xcffff has been reserved
[    0.196136] AppArmor: AppArmor Filesystem Enabled
[    0.196164] pci 0000:00:01.0: PCI bridge, secondary bus 0000:01
[    0.196167] pci 0000:00:01.0:   IO window: disabled
[    0.196175] pci 0000:00:01.0:   MEM window: 0xe8000000-0xeaffffff
[    0.196181] pci 0000:00:01.0:   PREFETCH window: 0xd0000000-0xdfffffff
[    0.196197] pci 0000:00:01.0: setting latency timer to 64
[    0.196203] pci_bus 0000:00: resource 0 io:  [0x00-0xffff]
[    0.196206] pci_bus 0000:00: resource 1 mem: [0x000000-0xffffffff]
[    0.196210] pci_bus 0000:01: resource 1 mem: [0xe8000000-0xeaffffff]
[    0.196213] pci_bus 0000:01: resource 2 pref mem [0xd0000000-0xdfffffff]
[    0.196260] NET: Registered protocol family 2
[    0.196393] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.196878] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.197736] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.198263] TCP: Hash tables configured (established 131072 bind 65536)
[    0.198267] TCP reno registered
[    0.198432] NET: Registered protocol family 1
[    0.198536] Trying to unpack rootfs image as initramfs...
[    0.448359] Freeing initrd memory: 7468k freed
[    0.457148] cpufreq-nforce2: No nForce2 chipset.
[    0.457189] Scanning for low memory corruption every 60 seconds
[    0.457336] audit: initializing netlink socket (disabled)
[    0.457361] type=2000 audit(1257111555.456:1): initialized
[    0.466982] highmem bounce pool size: 64 pages
[    0.466991] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    0.468598] VFS: Disk quotas dquot_6.5.2
[    0.468673] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.469354] fuse init (API version 7.12)
[    0.469455] msgmni has been set to 1706
[    0.469699] alg: No test for stdrng (krng)
[    0.469719] io scheduler noop registered
[    0.469723] io scheduler anticipatory registered
[    0.469725] io scheduler deadline registered
[    0.469780] io scheduler cfq registered (default)
[    0.469800] pci 0000:00:01.0: disabling DAC on VIA PCI bridge
[    0.469882] pci 0000:00:11.0: Bypassing VIA 8237 APIC De-Assert Message
[    0.469900] pci 0000:01:00.0: Boot video device
[    0.470004] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.470037] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.470156] isapnp: Scanning for PnP cards...
[    0.824170] isapnp: No Plug & Play device found
[    0.825581] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    0.825694] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.825795] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[    0.826234] 00:0b: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.826415] 00:0f: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[    0.827612] brd: module loaded
[    0.828173] loop: module loaded
[    0.828267] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[    0.828950] pata_via 0000:00:0f.1: version 0.3.4
[    0.828976] pata_via 0000:00:0f.1: PCI->APIC IRQ transform: INT A -> IRQ 20
[    0.829181] scsi0 : pata_via
[    0.829294] scsi1 : pata_via
[    0.829336] ata1: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xe700 irq 14
[    0.829340] ata2: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xe708 irq 15
[    0.829449] pata_acpi 0000:00:0f.0: PCI->APIC IRQ transform: INT B -> IRQ 20
[    0.829883] Fixed MDIO Bus: probed
[    0.829933] PPP generic driver version 2.4.2
[    0.830046] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.830071] ehci_hcd 0000:00:10.4: PCI->APIC IRQ transform: INT C -> IRQ 21
[    0.830090] ehci_hcd 0000:00:10.4: EHCI Host Controller
[    0.830156] ehci_hcd 0000:00:10.4: new USB bus registered, assigned bus number 1
[    0.830248] ehci_hcd 0000:00:10.4: irq 21, io mem 0xeb010000
[    0.840123] ehci_hcd 0000:00:10.4: USB 2.0 started, EHCI 1.00
[    0.840220] usb usb1: configuration #1 chosen from 1 choice
[    0.840260] hub 1-0:1.0: USB hub found
[    0.840271] hub 1-0:1.0: 8 ports detected
[    0.840345] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.840366] uhci_hcd: USB Universal Host Controller Interface driver
[    0.840404] uhci_hcd 0000:00:10.0: PCI->APIC IRQ transform: INT A -> IRQ 21
[    0.840412] uhci_hcd 0000:00:10.0: UHCI Host Controller
[    0.840451] uhci_hcd 0000:00:10.0: new USB bus registered, assigned bus number 2
[    0.840476] uhci_hcd 0000:00:10.0: irq 21, io base 0x0000e800
[    0.840569] usb usb2: configuration #1 chosen from 1 choice
[    0.840605] hub 2-0:1.0: USB hub found
[    0.840616] hub 2-0:1.0: 2 ports detected
[    0.840673] uhci_hcd 0000:00:10.1: PCI->APIC IRQ transform: INT A -> IRQ 21
[    0.840681] uhci_hcd 0000:00:10.1: UHCI Host Controller
[    0.840724] uhci_hcd 0000:00:10.1: new USB bus registered, assigned bus number 3
[    0.840747] uhci_hcd 0000:00:10.1: irq 21, io base 0x0000e900
[    0.840853] usb usb3: configuration #1 chosen from 1 choice
[    0.840888] hub 3-0:1.0: USB hub found
[    0.840899] hub 3-0:1.0: 2 ports detected
[    0.840953] uhci_hcd 0000:00:10.2: PCI->APIC IRQ transform: INT B -> IRQ 21
[    0.840961] uhci_hcd 0000:00:10.2: UHCI Host Controller
[    0.840998] uhci_hcd 0000:00:10.2: new USB bus registered, assigned bus number 4
[    0.841022] uhci_hcd 0000:00:10.2: irq 21, io base 0x0000ea00
[    0.841116] usb usb4: configuration #1 chosen from 1 choice
[    0.841150] hub 4-0:1.0: USB hub found
[    0.841161] hub 4-0:1.0: 2 ports detected
[    0.841215] uhci_hcd 0000:00:10.3: PCI->APIC IRQ transform: INT B -> IRQ 21
[    0.841222] uhci_hcd 0000:00:10.3: UHCI Host Controller
[    0.841260] uhci_hcd 0000:00:10.3: new USB bus registered, assigned bus number 5
[    0.841284] uhci_hcd 0000:00:10.3: irq 21, io base 0x0000eb00
[    0.841378] usb usb5: configuration #1 chosen from 1 choice
[    0.841412] hub 5-0:1.0: USB hub found
[    0.841423] hub 5-0:1.0: 2 ports detected
[    0.841560] PNP: PS/2 Controller [PNP0303,PNP0f13] at 0x60,0x64 irq 1,12
[    0.841973] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.841982] serio: i8042 AUX port at 0x60,0x64 irq 12
[    0.842060] mice: PS/2 mouse device common for all mice
[    0.842144] rtc_cmos 00:03: rtc core: registered rtc_cmos as rtc0
[    0.842196] rtc0: alarms up to one day, 114 bytes nvram
[    0.842334] device-mapper: uevent: version 1.0.3
[    0.842440] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: [email]dm-devel@redhat.com[/email]
[    0.842542] device-mapper: multipath: version 1.1.0 loaded
[    0.842546] device-mapper: multipath round-robin: version 1.0.0 loaded
[    0.842690] EISA: Probing bus 0 at eisa.0
[    0.842730] EISA: Detected 0 cards.
[    0.842788] cpuidle: using governor ladder
[    0.842792] cpuidle: using governor menu
[    0.843391] TCP cubic registered
[    0.843548] NET: Registered protocol family 10
[    0.844095] lo: Disabled Privacy Extensions
[    0.844512] NET: Registered protocol family 17
[    0.844536] Bluetooth: L2CAP ver 2.13
[    0.844539] Bluetooth: L2CAP socket layer initialized
[    0.844542] Bluetooth: SCO (Voice Link) ver 0.6
[    0.844544] Bluetooth: SCO socket layer initialized
[    0.844577] Bluetooth: RFCOMM TTY layer initialized
[    0.844581] Bluetooth: RFCOMM socket layer initialized
[    0.844584] Bluetooth: RFCOMM ver 1.11
[    0.844603] Using IPI No-Shortcut mode
[    0.844683] PM: Resume from disk failed.
[    0.844700] registered taskstats version 1
[    0.844813]   Magic number: 1:466:701
[    0.844888] rtc_cmos 00:03: setting system clock to 2009-11-01 21:39:16 UTC (1257111556)
[    0.844893] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.844895] EDD information not available.
[    0.861310] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
[    1.012479] ata1.00: HPA unlocked: 78125000 -> 78165360, native 78165360
[    1.012486] ata1.00: ATA-5: WDC WD400BB-75DEA0, 05.03E05, max UDMA/100
[    1.012490] ata1.00: 78165360 sectors, multi 16: LBA 
[    1.012669] ata1.01: ATA-6: WDC WD400BB-75FJA1, 14.03G14, max UDMA/100
[    1.012673] ata1.01: 78125000 sectors, multi 16: LBA 
[    1.029472] ata1.00: configured for UDMA/100
[    1.044557] ata1.01: configured for UDMA/100
[    1.044710] scsi 0:0:0:0: Direct-Access     ATA      WDC WD400BB-75DE 05.0 PQ: 0 ANSI: 5
[    1.044861] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    1.044955] scsi 0:0:1:0: Direct-Access     ATA      WDC WD400BB-75FJ 14.0 PQ: 0 ANSI: 5
[    1.045078] sd 0:0:1:0: Attached scsi generic sg1 type 0
[    1.045130] sd 0:0:0:0: [sda] 78165360 512-byte logical blocks: (40.0 GB/37.2 GiB)
[    1.045201] sd 0:0:0:0: [sda] Write Protect is off
[    1.045205] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.045240] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.045423]  sda:
[    1.062794] sd 0:0:1:0: [sdb] 78125000 512-byte logical blocks: (40.0 GB/37.2 GiB)
[    1.062864] sd 0:0:1:0: [sdb] Write Protect is off
[    1.062867] sd 0:0:1:0: [sdb] Mode Sense: 00 3a 00 00
[    1.062902] sd 0:0:1:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.063069]  sdb: sda1 sda2 < sdb1
[    1.117127]  sda5 >
[    1.117419] sd 0:0:0:0: [sda] Attached SCSI disk
[    1.117544] sd 0:0:1:0: [sdb] Attached SCSI disk
[    1.224540] ata2.00: ATAPI: SONY    CD-RW  CRX230EE, 2YS3, max UDMA/33
[    1.256443] ata2.00: configured for UDMA/33
[    1.257878] scsi 1:0:0:0: CD-ROM            SONY     CD-RW  CRX230EE  2YS3 PQ: 0 ANSI: 5
[    1.263069] sr0: scsi3-mmc drive: 52x/52x writer cd/rw xa/form2 cdda tray
[    1.263073] Uniform CD-ROM driver Revision: 3.20
[    1.263161] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    1.263223] sr 1:0:0:0: Attached scsi generic sg2 type 5
[    1.263249] Freeing unused kernel memory: 540k freed
[    1.263794] Write protecting the kernel text: 4568k
[    1.263826] Write protecting the kernel read-only data: 1836k
[    1.413979] Linux agpgart interface v0.103
[    1.416912] agpgart: Detected VIA PT880 chipset
[    1.462473] agpgart-via 0000:00:00.0: AGP aperture is 128M @ 0xe0000000
[    1.489338] sata_via 0000:00:0f.0: version 2.4
[    1.489355] sata_via 0000:00:0f.0: PCI->APIC IRQ transform: INT B -> IRQ 20
[    1.489404] sata_via 0000:00:0f.0: routed to hard irq line 11
[    1.489525] scsi2 : sata_via
[    1.489621] scsi3 : sata_via
[    1.489671] ata3: SATA max UDMA/133 cmd 0xe100 ctl 0xe200 bmdma 0xe500 irq 20
[    1.489676] ata4: SATA max UDMA/133 cmd 0xe300 ctl 0xe400 bmdma 0xe508 irq 20
[    1.509314] usb 2-1: new full speed USB device using uhci_hcd and address 2
[    1.511469] via-rhine.c:v1.10-LK1.4.3 2007-03-06 Written by Donald Becker
[    1.511534] via-rhine 0000:00:12.0: PCI->APIC IRQ transform: INT A -> IRQ 23
[    1.516331] eth0: VIA Rhine II at 0xeb011000, 00:50:70:f7:0a:d9, IRQ 23.
[    1.517034] eth0: MII PHY found at address 1, status 0x7849 advertising 05e1 Link 0000.
[    1.674745] usb 2-1: configuration #1 chosen from 1 choice
[    1.692537] ata3: SATA link down 1.5 Gbps (SStatus 0 SControl 300)
[    1.904424] ata4: SATA link down 1.5 Gbps (SStatus 0 SControl 300)
[    1.928344] usb 2-2: new full speed USB device using uhci_hcd and address 3
[    2.112482] usb 2-2: configuration #1 chosen from 1 choice
[    2.928517] Clocksource tsc unstable (delta = 240111361 ns)
[    3.081260] PM: Starting manual resume from disk
[    3.081265] PM: Resume from partition 8:5
[    3.081267] PM: Checking hibernation image.
[    3.081368] PM: Resume from disk failed.
[    3.112613] EXT4-fs (sda1): barriers enabled
[    3.145572] kjournald2 starting: pid 324, dev sda1:8, commit interval 5 seconds
[    3.145572] EXT4-fs (sda1): delayed allocation enabled
[    3.145572] EXT4-fs: file extents enabled
[    3.149018] EXT4-fs: mballoc enabled
[    3.149037] EXT4-fs (sda1): mounted filesystem with ordered data mode
[    4.016632] type=1505 audit(1257111559.671:2): operation="profile_load" pid=347 name=/usr/share/gdm/guest-session/Xsession
[    4.022290] type=1505 audit(1257111559.675:3): operation="profile_load" pid=348 name=/sbin/dhclient3
[    4.022290] type=1505 audit(1257111559.675:4): operation="profile_load" pid=348 name=/usr/lib/NetworkManager/nm-dhcp-client.action
[    4.022290] type=1505 audit(1257111559.675:5): operation="profile_load" pid=348 name=/usr/lib/connman/scripts/dhclient-script
[    4.082368] type=1505 audit(1257111559.735:6): operation="profile_load" pid=349 name=/usr/bin/evince
[    4.096170] type=1505 audit(1257111559.747:7): operation="profile_load" pid=349 name=/usr/bin/evince-previewer
[    4.103427] type=1505 audit(1257111559.755:8): operation="profile_load" pid=349 name=/usr/bin/evince-thumbnailer
[    4.124742] type=1505 audit(1257111559.779:9): operation="profile_load" pid=351 name=/usr/lib/cups/backend/cups-pdf
[    4.125652] type=1505 audit(1257111559.779:10): operation="profile_load" pid=351 name=/usr/sbin/cupsd
[    5.597585] Adding 1646620k swap on /dev/sda5.  Priority:-1 extents:1 across:1646620k 
[    5.683802] udev: starting version 147
[    6.452606] EXT4-fs (sda1): internal journal on sda1:8
[    6.651241] usbcore: registered new interface driver usbserial
[    6.651261] USB Serial support registered for generic
[    6.651306] usbcore: registered new interface driver usbserial_generic
[    6.651309] usbserial: USB Serial Driver core
[    6.706844] USB Serial support registered for GSM modem (1-port)
[    6.706896] option 2-1:1.0: GSM modem (1-port) converter detected
[    6.707001] usb 2-1: GSM modem (1-port) converter now attached to ttyUSB0
[    6.707018] option 2-1:1.1: GSM modem (1-port) converter detected
[    6.707085] usb 2-1: GSM modem (1-port) converter now attached to ttyUSB1
[    6.707109] usbcore: registered new interface driver option
[    6.707112] option: v0.7.2:USB Driver for GSM modems
[    6.752522] psmouse serio1: ID: 00 00 3c
[    6.827060] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[    6.859510] lp: driver loaded but no devices found
[    7.420617] input: ImPS/2 Logitech Wheel Mouse as /devices/platform/i8042/serio1/input/input2
[    8.312943] ip_tables: (C) 2000-2006 Netfilter Core Team
[    8.516763] VIA 82xx Audio 0000:00:11.5: PCI->APIC IRQ transform: INT C -> IRQ 22
[    8.516939] VIA 82xx Audio 0000:00:11.5: setting latency timer to 64
[    9.206106] nvidia: module license 'NVIDIA' taints kernel.
[    9.206113] Disabling lock debugging due to kernel taint
[    9.478367] nvidia 0000:01:00.0: PCI->APIC IRQ transform: INT A -> IRQ 16
[    9.478667] NVRM: loading NVIDIA UNIX x86 Kernel Module  185.18.36  Fri Aug 14 17:18:04 PDT 2009
[    9.948235] __ratelimit: 3 callbacks suppressed
[    9.948241] type=1505 audit(1257111565.599:12): operation="profile_replace" pid=717 name=/usr/share/gdm/guest-session/Xsession
[    9.950834] type=1505 audit(1257111565.603:13): operation="profile_replace" pid=718 name=/sbin/dhclient3
[    9.951620] type=1505 audit(1257111565.603:14): operation="profile_replace" pid=718 name=/usr/lib/NetworkManager/nm-dhcp-client.action
[    9.952050] type=1505 audit(1257111565.603:15): operation="profile_replace" pid=718 name=/usr/lib/connman/scripts/dhclient-script
[    9.967384] type=1505 audit(1257111565.619:16): operation="profile_replace" pid=725 name=/usr/bin/evince
[    9.987771] type=1505 audit(1257111565.639:17): operation="profile_replace" pid=725 name=/usr/bin/evince-previewer
[    9.998165] type=1505 audit(1257111565.651:18): operation="profile_replace" pid=725 name=/usr/bin/evince-thumbnailer
[   10.009402] type=1505 audit(1257111565.663:19): operation="profile_replace" pid=734 name=/usr/lib/cups/backend/cups-pdf
[   10.010315] type=1505 audit(1257111565.663:20): operation="profile_replace" pid=734 name=/usr/sbin/cupsd
[   10.013651] type=1505 audit(1257111565.667:21): operation="profile_replace" pid=735 name=/usr/sbin/tcpdump
[   10.284990] nf_conntrack version 0.5.0 (16384 buckets, 65536 max)
[   10.285258] CONFIG_NF_CT_ACCT is deprecated and will be removed soon. Please use
[   10.285262] nf_conntrack.acct=1 kernel parameter, acct=1 nf_conntrack module option or
[   10.285264] sysctl net.netfilter.nf_conntrack_acct=1 to enable it.
[   13.264884] usblp0: USB Bidirectional printer dev 3 if 0 alt 0 proto 2 vid 0x04A9 pid 0x1072
[   13.264884] usbcore: registered new interface driver usblp
[   15.624751] eth0: link down
[   15.624982] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   21.258439] vboxdrv: Trying to deactivate the NMI watchdog permanently...
[   21.258444] vboxdrv: Successfully done.
[   21.258446] vboxdrv: Found 1 processor cores.
[   21.258580] vboxdrv: TSC mode is 'synchronous', kernel timer mode is 'normal'.
[   21.258583] vboxdrv: Successfully loaded version 3.0.10 (interface 0x000e0001).
[   21.629641] ppdev: user-space parallel port driver
[   22.880505] NVRM: failed to register with the ACPI subsystem!
[   23.269512] agpgart-via 0000:00:00.0: AGP 3.5 bridge
[   23.269534] agpgart-via 0000:00:00.0: putting AGP V3 device into 8x mode
[   23.269615] nvidia 0000:01:00.0: putting AGP V3 device into 8x mode
[   23.754987] usb 2-2: usbfs: interface 0 claimed by usblp while 'usb' sets config #1
[   23.759845] type=1503 audit(1257111579.411:22): operation="open" pid=1508 parent=1504 profile="/usr/sbin/cupsd" requested_mask="w::" denied_mask="w::" fsuid=0 ouid=0 name="/dev/ttyUSB0"
[   23.759876] type=1503 audit(1257111579.411:23): operation="open" pid=1508 parent=1504 profile="/usr/sbin/cupsd" requested_mask="w::" denied_mask="w::" fsuid=0 ouid=0 name="/dev/ttyUSB1"
[  749.836813] PPP BSD Compression module registered
[  749.868531] PPP Deflate Compression module registered

---

