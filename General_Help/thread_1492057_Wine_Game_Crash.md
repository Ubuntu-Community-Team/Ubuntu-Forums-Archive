---
title: "Wine Game Crash"
date: 2010-05-24
forum: General Help
---

### Post by fabis94 on 2010-05-24
Ok im trying to play Counter Strike 1.6, but it crashes when i join a server. 

The Video is set to OpenGL and when i set it to "Software" it started working (but the quality was really shitty so i want OpenGL).

I have this video card VGA compatible controller [0300]: ATI Technologies Inc RS480 [Radeon Xpress 200G Series]

And when the game crashed i got this error:

```
Allocating 16 x 16 radeon RBO (pitch 16)
Allocating 16 x 16 radeon RBO (pitch 16)
Allocating 16 x 16 radeon RBO (pitch 16)
Allocating 16 x 16 radeon RBO (pitch 16)
Allocating 16 x 16 radeon RBO (pitch 16)
Allocating 16 x 16 radeon RBO (pitch 16)
Allocating 16 x 16 radeon RBO (pitch 16)
Allocating 16 x 16 radeon RBO (pitch 16)
Allocating 16 x 16 radeon RBO (pitch 16)
Allocating 16 x 16 radeon RBO (pitch 16)
Allocating 16 x 16 radeon RBO (pitch 16)
Allocating 16 x 16 radeon RBO (pitch 16)
Allocating 16 x 16 radeon RBO (pitch 16)
Allocating 16 x 16 radeon RBO (pitch 16)
Allocating 16 x 16 radeon RBO (pitch 16)
Allocating 16 x 16 radeon RBO (pitch 16)
Allocating 16 x 16 radeon RBO (pitch 16)
Allocating 16 x 16 radeon RBO (pitch 16)
Allocating 16 x 16 radeon RBO (pitch 16)
Allocating 16 x 16 radeon RBO (pitch 16)
fixme:win:EnumDisplayDevicesW ((null),0,0x32f370,0x00000000), stub!
fixme:shdocvw:ViewObject_SetAdvise (0x19dfe8)->(1 00000002 0x123b0a8)
fixme:shdocvw:PersistStreamInit_InitNew (0x19dfe8)
fixme:shdocvw:WebBrowser_put_RegisterAsBrowser (0x19dfe8)->(ffffffff)
fixme:shdocvw:WebBrowser_put_RegisterAsDropTarget (0x19dfe8)->(ffffffff)
fixme:dsalsa:IDsDriverBufferImpl_SetVolumePan (0x1a6db0,0x1a71d8): stub
fixme:shdocvw:ViewObject_SetAdvise (0x6a6b060)->(1 00000002 0x1077b90)
fixme:shdocvw:PersistStreamInit_InitNew (0x6a6b060)
fixme:shdocvw:WebBrowser_put_RegisterAsBrowser (0x6a6b060)->(ffffffff)
fixme:shdocvw:WebBrowser_put_RegisterAsDropTarget (0x6a6b060)->(ffffffff)
fixme:shdocvw:ViewObject_Draw (0x6a6b060)->(1 -1 (nil) (nil) 0xc10 0xc2c 0x32f600 (nil) (nil) 00000000)
fixme:shdocvw:ViewObject_SetAdvise (0x6a4ae30)->(1 00000002 0x1077fb0)
fixme:shdocvw:PersistStreamInit_InitNew (0x6a4ae30)
fixme:shdocvw:WebBrowser_put_RegisterAsBrowser (0x6a4ae30)->(ffffffff)
fixme:shdocvw:WebBrowser_put_RegisterAsDropTarget (0x6a4ae30)->(ffffffff)
fixme:shdocvw:OleInPlaceObject_InPlaceDeactivate (0x6a6b060)
fixme:shdocvw:OleInPlaceObject_UIDeactivate (0x6a6b060)
fixme:shdocvw:OleObject_Close (0x6a6b060)->(1)
fixme:shdocvw:ViewObject_Draw (0x6a4ae30)->(1 -1 (nil) (nil) 0xc10 0xcc8 0x31f65c (nil) (nil) 00000000)
fixme:shdocvw:OleInPlaceObject_InPlaceDeactivate (0x6a4ae30)
fixme:shdocvw:OleInPlaceObject_UIDeactivate (0x6a4ae30)
fixme:shdocvw:OleObject_Close (0x6a4ae30)->(1)
fixme:shdocvw:ViewObject_SetAdvise (0x6a6b290)->(1 00000002 0x1077bc0)
fixme:shdocvw:PersistStreamInit_InitNew (0x6a6b290)
fixme:shdocvw:WebBrowser_put_RegisterAsBrowser (0x6a6b290)->(ffffffff)
fixme:shdocvw:WebBrowser_put_RegisterAsDropTarget (0x6a6b290)->(ffffffff)
fixme:shdocvw:ViewObject_Draw (0x6a6b290)->(1 -1 (nil) (nil) 0xc10 0xd88 0x32f600 (nil) (nil) 00000000)
drmRadeonCmdBuffer: -12. Kernel failed to parse or rejected command stream. See dmesg for more info.

```

dmesg returned this:

```
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.32-22-generic (buildd@rothera) (gcc version 4.4.3 (Ubuntu 4.4.3-4ubuntu5) ) #33-Ubuntu SMP Wed Apr 28 13:27:30 UTC 2010 (Ubuntu 2.6.32-22.33-generic 2.6.32.11+drm33.2)
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   NSC Geode by NSC
[    0.000000]   Cyrix CyrixInstead
[    0.000000]   Centaur CentaurHauls
[    0.000000]   Transmeta GenuineTMx86
[    0.000000]   Transmeta TransmetaCPU
[    0.000000]   UMC UMC UMC UMC
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
[    0.000000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000001bef0000 (usable)
[    0.000000]  BIOS-e820: 000000001bef0000 - 000000001bef3000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000001bef3000 - 000000001bf00000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000ffff0000 - 0000000100000000 (reserved)
[    0.000000] DMI 2.4 present.
[    0.000000] Phoenix BIOS detected: BIOS may corrupt low RAM, working around it.
[    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
[    0.000000] last_pfn = 0x1bef0 max_arch_pfn = 0x100000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-C7FFF write-protect
[    0.000000]   C8000-CBFFF uncachable
[    0.000000]   CC000-CFFFF write-back
[    0.000000]   D0000-FFFFF uncachable
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 0000000000 mask FFF0000000 write-back
[    0.000000]   1 base 0010000000 mask FFF8000000 write-back
[    0.000000]   2 base 0018000000 mask FFFC000000 write-back
[    0.000000]   3 base 001BF00000 mask FFFFF00000 uncachable
[    0.000000]   4 disabled
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] Scanning 0 areas for low memory corruption
[    0.000000] modified physical RAM map:
[    0.000000]  modified: 0000000000000000 - 0000000000010000 (reserved)
[    0.000000]  modified: 0000000000010000 - 000000000009f800 (usable)
[    0.000000]  modified: 000000000009f800 - 00000000000a0000 (reserved)
[    0.000000]  modified: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  modified: 0000000000100000 - 000000001bef0000 (usable)
[    0.000000]  modified: 000000001bef0000 - 000000001bef3000 (ACPI NVS)
[    0.000000]  modified: 000000001bef3000 - 000000001bf00000 (ACPI data)
[    0.000000]  modified: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  modified: 00000000fec00000 - 00000000fec01000 (reserved)
[    0.000000]  modified: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  modified: 00000000ffff0000 - 0000000100000000 (reserved)
[    0.000000] initial memory mapped : 0 - 00c00000
[    0.000000] init_memory_mapping: 0000000000000000-000000001bef0000
[    0.000000] Using x86 segment limits to approximate NX protection
[    0.000000]  0000000000 - 0000400000 page 4k
[    0.000000]  0000400000 - 001bc00000 page 2M
[    0.000000]  001bc00000 - 001bef0000 page 4k
[    0.000000] kernel direct mapping tables up to 1bef0000 @ 10000-15000
[    0.000000] RAMDISK: 147de000 - 14f73ec4
[    0.000000] ACPI: RSDP 000f8600 00014 (v00 HP    )
[    0.000000] ACPI: RSDT 1bef3040 00034 (v01 HP     AWRDACPI 42302E31 AWRD 00000000)
[    0.000000] ACPI: FACP 1bef30c0 00084 (v02 HP     AWRDACPI 42302E31 AWRD 00000000)
[    0.000000] ACPI: DSDT 1bef31c0 031DA (v01 HP     AWRDACPI 00001000 MSFT 0100000E)
[    0.000000] ACPI: FACS 1bef0000 00040
[    0.000000] ACPI: ASF! 1bef64c0 00052 (v16 HP     AWRDACPI 42302E31 AWRD 00000000)
[    0.000000] ACPI: MCFG 1bef6580 0003C (v01 HP     AWRDACPI 42302E31 AWRD 00000000)
[    0.000000] ACPI: APIC 1bef6400 00050 (v01 HP     AWRDACPI 42302E31 AWRD 00000000)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] 0MB HIGHMEM available.
[    0.000000] 446MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 1bef0000
[    0.000000]   low ram: 0 - 1bef0000
[    0.000000]   node 0 low ram: 00000000 - 1bef0000
[    0.000000]   node 0 bootmap 00011000 - 000147e0
[    0.000000] (9 early reservations) ==> bootmem [0000000000 - 001bef0000]
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
[    0.000000]   #1 [0000001000 - 0000002000]    EX TRAMPOLINE ==> [0000001000 - 0000002000]
[    0.000000]   #2 [0000006000 - 0000007000]       TRAMPOLINE ==> [0000006000 - 0000007000]
[    0.000000]   #3 [0000100000 - 00008d9e98]    TEXT DATA BSS ==> [0000100000 - 00008d9e98]
[    0.000000]   #4 [00147de000 - 0014f73ec4]          RAMDISK ==> [00147de000 - 0014f73ec4]
[    0.000000]   #5 [000009f800 - 0000100000]    BIOS reserved ==> [000009f800 - 0000100000]
[    0.000000]   #6 [00008da000 - 00008dd0e0]              BRK ==> [00008da000 - 00008dd0e0]
[    0.000000]   #7 [0000010000 - 0000011000]          PGTABLE ==> [0000010000 - 0000011000]
[    0.000000]   #8 [0000011000 - 0000015000]          BOOTMAP ==> [0000011000 - 0000015000]
[    0.000000] found SMP MP-table at [c00f4350] f4350
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000010 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x0001bef0
[    0.000000]   HighMem  0x0001bef0 -> 0x0001bef0
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[2] active PFN ranges
[    0.000000]     0: 0x00000010 -> 0x0000009f
[    0.000000]     0: 0x00000100 -> 0x0001bef0
[    0.000000] On node 0 totalpages: 114303
[    0.000000] free_area_init_node: node 0, pgdat c0798720, node_mem_map c1001200
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3951 pages, LIFO batch:0
[    0.000000]   Normal zone: 862 pages used for memmap
[    0.000000]   Normal zone: 109458 pages, LIFO batch:31
[    0.000000] Using APIC driver default
[    0.000000] SB4X0 revision 0x10
[    0.000000] Ignoring ACPI timer override.
[    0.000000] If you got timer trouble try acpi_use_timer_override
[    0.000000] ACPI: PM-Timer IO Port: 0x4008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 33, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 21 low level)
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] SMP: Allowing 1 CPUs, 0 hotplug CPUs
[    0.000000] nr_irqs_gsi: 24
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000f0000
[    0.000000] PM: Registered nosave memory: 00000000000f0000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 1bf00000 (gap: 1bf00000:c4100000)
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:1 nr_node_ids:1
[    0.000000] PERCPU: Embedded 14 pages/cpu @c1400000 s36024 r0 d21320 u4194304
[    0.000000] pcpu-alloc: s36024 r0 d21320 u4194304 alloc=1*4194304
[    0.000000] pcpu-alloc: [0] 0 
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 113409
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.32-22-generic root=UUID=e1885df7-b6d8-4d3c-80ff-40f5d47f5dae ro quiet splash
[    0.000000] PID hash table entries: 2048 (order: 1, 8192 bytes)
[    0.000000] Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.000000] Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] allocated 2288000 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] Initializing HighMem for node 0 (00000000:00000000)
[    0.000000] Memory: 434736k/457664k available (4673k kernel code, 22136k reserved, 2121k data, 656k init, 0k highmem)
[    0.000000] virtual kernel memory layout:
[    0.000000]     fixmap  : 0xfff1d000 - 0xfffff000   ( 904 kB)
[    0.000000]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[    0.000000]     vmalloc : 0xdc6f0000 - 0xff7fe000   ( 561 MB)
[    0.000000]     lowmem  : 0xc0000000 - 0xdbef0000   ( 446 MB)
[    0.000000]       .init : 0xc07a3000 - 0xc0847000   ( 656 kB)
[    0.000000]       .data : 0xc0590653 - 0xc07a2e48   (2121 kB)
[    0.000000]       .text : 0xc0100000 - 0xc0590653   (4673 kB)
[    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.000000] SLUB: Genslabs=13, HWalign=64, Order=0-3, MinObjects=0, CPUs=1, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000] NR_IRQS:2304 nr_irqs:256
[    0.000000] spurious 8259A interrupt: IRQ7.
[    0.000000] Console: colour VGA+ 80x25
[    0.000000] console [tty0] enabled
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 997.152 MHz processor.
[    0.008005] Calibrating delay loop (skipped), value calculated using timer frequency.. 1994.30 BogoMIPS (lpj=3988608)
[    0.008037] Security Framework initialized
[    0.008073] AppArmor: AppArmor initialized
[    0.008087] Mount-cache hash table entries: 512
[    0.008270] Initializing cgroup subsys ns
[    0.008276] Initializing cgroup subsys cpuacct
[    0.008284] Initializing cgroup subsys memory
[    0.008298] Initializing cgroup subsys devices
[    0.008303] Initializing cgroup subsys freezer
[    0.008308] Initializing cgroup subsys net_cls
[    0.008337] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[    0.008342] CPU: L2 Cache: 128K (64 bytes/line)
[    0.008349] mce: CPU supports 5 MCE banks
[    0.008371] Performance Events: AMD PMU driver.
[    0.008394] ... version:                0
[    0.008398] ... bit width:              48
[    0.008402] ... generic registers:      4
[    0.008406] ... value mask:             0000ffffffffffff
[    0.008411] ... max period:             00007fffffffffff
[    0.008415] ... fixed-purpose events:   0
[    0.008419] ... event mask:             000000000000000f
[    0.008426] Checking 'hlt' instruction... OK.
[    0.025291] SMP alternatives: switching to UP code
[    0.036903] Freeing SMP alternatives: 19k freed
[    0.036931] ACPI: Core revision 20090903
[    0.044033] ftrace: converting mcount calls to 0f 1f 44 00 00
[    0.044049] ftrace: allocating 21771 entries in 43 pages
[    0.048115] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.048670]   alloc irq_desc for 21 on node 0
[    0.048674]   alloc kstat_irqs on node 0
[    0.048828] ..TIMER: vector=0x30 apic1=0 pin1=0 apic2=-1 pin2=-1
[    0.088676] CPU0: AMD Sempron(tm) Processor 3000+ stepping 00
[    0.092001] Brought up 1 CPUs
[    0.092001] Total of 1 processors activated (1994.30 BogoMIPS).
[    0.092001] CPU0 attaching NULL sched-domain.
[    0.092001] devtmpfs: initialized
[    0.092001] regulator: core version 0.5
[    0.092001] Time: 16:59:40  Date: 05/24/10
[    0.092001] NET: Registered protocol family 16
[    0.092001] EISA bus registered
[    0.092001] ACPI: bus type pci registered
[    0.092001] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 255
[    0.092001] PCI: MCFG area at e0000000 reserved in E820
[    0.092001] PCI: Using MMCONFIG for extended config space
[    0.092001] PCI: Using configuration type 1 for base access
[    0.092001] bio: create slab <bio-0> at 0
[    0.092082] ACPI: EC: Look up EC in DSDT
[    0.094213] ACPI Warning: Package List length (0x5) larger than NumElements count (0x2), truncated
[    0.094223]  (20090903/dsobject-515)
[    0.097878] ACPI: Interpreter enabled
[    0.097892] ACPI: (supports S0 S3 S4 S5)
[    0.097934] ACPI: Using IOAPIC for interrupt routing
[    0.103500] ACPI: No dock devices found.
[    0.103679] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.103754] pci 0000:00:00.0: reg 1c 64bit mmio: [0xe0000000-0xffffffff]
[    0.103867] pci 0000:00:05.0: PME# supported from D0 D3hot D3cold
[    0.103874] pci 0000:00:05.0: PME# disabled
[    0.103966] pci 0000:00:12.0: reg 10 io port: [0xfc00-0xfc07]
[    0.103979] pci 0000:00:12.0: reg 14 io port: [0xf800-0xf803]
[    0.104013] pci 0000:00:12.0: reg 18 io port: [0xf400-0xf407]
[    0.104027] pci 0000:00:12.0: reg 1c io port: [0xf000-0xf003]
[    0.104040] pci 0000:00:12.0: reg 20 io port: [0xec00-0xec0f]
[    0.104053] pci 0000:00:12.0: reg 24 32bit mmio: [0xfe02f000-0xfe02f1ff]
[    0.104067] pci 0000:00:12.0: reg 30 32bit mmio pref: [0x000000-0x07ffff]
[    0.104108] pci 0000:00:12.0: supports D1 D2
[    0.104166] pci 0000:00:13.0: reg 10 32bit mmio: [0xfe02e000-0xfe02efff]
[    0.104290] pci 0000:00:13.1: reg 10 32bit mmio: [0xfe02d000-0xfe02dfff]
[    0.104428] pci 0000:00:13.2: reg 10 32bit mmio: [0xfe02c000-0xfe02cfff]
[    0.104508] pci 0000:00:13.2: supports D1 D2
[    0.104513] pci 0000:00:13.2: PME# supported from D0 D1 D2 D3hot
[    0.104522] pci 0000:00:13.2: PME# disabled
[    0.104587] pci 0000:00:14.0: reg 10 io port: [0x500-0x50f]
[    0.104600] pci 0000:00:14.0: reg 14 32bit mmio: [0xfe02b000-0xfe02b3ff]
[    0.104643] HPET not enabled in BIOS. You might try hpet=force boot option
[    0.104721] pci 0000:00:14.1: reg 10 io port: [0x00-0x07]
[    0.104734] pci 0000:00:14.1: reg 14 io port: [0x00-0x03]
[    0.104747] pci 0000:00:14.1: reg 18 io port: [0x00-0x07]
[    0.104759] pci 0000:00:14.1: reg 1c io port: [0x00-0x03]
[    0.104773] pci 0000:00:14.1: reg 20 io port: [0xe400-0xe40f]
[    0.104995] pci 0000:00:14.5: reg 10 32bit mmio: [0xfe02a000-0xfe02a0ff]
[    0.105224] pci 0000:01:05.0: reg 10 32bit mmio pref: [0xd0000000-0xd7ffffff]
[    0.105233] pci 0000:01:05.0: reg 14 io port: [0xcc00-0xccff]
[    0.105242] pci 0000:01:05.0: reg 18 32bit mmio: [0xfdaf0000-0xfdafffff]
[    0.105258] pci 0000:01:05.0: reg 30 32bit mmio pref: [0x000000-0x01ffff]
[    0.105274] pci 0000:01:05.0: supports D1 D2
[    0.105298] pci 0000:01:05.1: reg 10 32bit mmio pref: [0xc8000000-0xcfffffff]
[    0.105308] pci 0000:01:05.1: reg 14 32bit mmio: [0xfdae0000-0xfdaeffff]
[    0.105334] pci 0000:01:05.1: supports D1 D2
[    0.105363] pci 0000:00:01.0: bridge io port: [0xc000-0xcfff]
[    0.105370] pci 0000:00:01.0: bridge 32bit mmio: [0xfda00000-0xfdafffff]
[    0.105379] pci 0000:00:01.0: bridge 64bit mmio pref: [0xc8000000-0xd7ffffff]
[    0.105449] pci 0000:02:00.0: reg 10 64bit mmio: [0xfdbf0000-0xfdbfffff]
[    0.105528] pci 0000:02:00.0: PME# supported from D3hot D3cold
[    0.105536] pci 0000:02:00.0: PME# disabled
[    0.105618] pci 0000:00:05.0: bridge io port: [0xd000-0xdfff]
[    0.105625] pci 0000:00:05.0: bridge 32bit mmio: [0xfde00000-0xfdefffff]
[    0.105635] pci 0000:00:05.0: bridge 32bit mmio pref: [0xfdb00000-0xfdbfffff]
[    0.105721] pci 0000:00:14.4: transparent bridge
[    0.105734] pci 0000:00:14.4: bridge io port: [0xb000-0xbfff]
[    0.105744] pci 0000:00:14.4: bridge 32bit mmio: [0xfdd00000-0xfddfffff]
[    0.105754] pci 0000:00:14.4: bridge 32bit mmio pref: [0xfdc00000-0xfdcfffff]
[    0.105774] pci_bus 0000:00: on NUMA node 0
[    0.105783] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.106071] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P2P_._PRT]
[    0.106208] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.AGP_._PRT]
[    0.127884] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 10 11) *0, disabled.
[    0.128055] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 10 11) *0, disabled.
[    0.128210] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 10 11) *0, disabled.
[    0.128364] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 10 11) *0, disabled.
[    0.128519] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 10 11) *0, disabled.
[    0.128672] ACPI: PCI Interrupt Link [LNKF] (IRQs 9) *0, disabled.
[    0.128821] ACPI: PCI Interrupt Link [LNK0] (IRQs 3 4 5 6 7 10 11) *0, disabled.
[    0.128976] ACPI: PCI Interrupt Link [LNK1] (IRQs 3 4 *5 6 7 10 11)
[    0.129165] vgaarb: device added: PCI:0000:01:05.0,decodes=io+mem,owns=io+mem,locks=none
[    0.129172] vgaarb: loaded
[    0.129378] SCSI subsystem initialized
[    0.129487] libata version 3.00 loaded.
[    0.129619] usbcore: registered new interface driver usbfs
[    0.129643] usbcore: registered new interface driver hub
[    0.129687] usbcore: registered new device driver usb
[    0.129909] ACPI: WMI: Mapper loaded
[    0.129914] PCI: Using ACPI for IRQ routing
[    0.129936] pci 0000:00:00.0: BAR 3: address space collision on of device [0xe0000000-0xffffffff]
[    0.129943] pci 0000:00:00.0: BAR 3: can't allocate resource
[    0.129999] pci 0000:02:00.0: BAR 0: no parent found for of device [0xfdbf0000-0xfdbfffff]
[    0.130006] pci 0000:02:00.0: BAR 0: can't allocate resource
[    0.130209] NetLabel: Initializing
[    0.130213] NetLabel:  domain hash size = 128
[    0.130216] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.130239] NetLabel:  unlabeled traffic allowed by default
[    0.130300] Switching to clocksource tsc
[    0.132001] AppArmor: AppArmor Filesystem Enabled
[    0.132001] pnp: PnP ACPI init
[    0.132001] ACPI: bus type pnp registered
[    0.135364] pnp 00:0c: mem resource (0xcc000-0xcffff) overlaps 0000:00:00.0 BAR 3 (0x0-0x1fffffff), disabling
[    0.135374] pnp 00:0c: mem resource (0xf0000-0xf7fff) overlaps 0000:00:00.0 BAR 3 (0x0-0x1fffffff), disabling
[    0.135382] pnp 00:0c: mem resource (0xf8000-0xfbfff) overlaps 0000:00:00.0 BAR 3 (0x0-0x1fffffff), disabling
[    0.135389] pnp 00:0c: mem resource (0xfc000-0xfffff) overlaps 0000:00:00.0 BAR 3 (0x0-0x1fffffff), disabling
[    0.135397] pnp 00:0c: mem resource (0x1bf00000-0x1bffffff) overlaps 0000:00:00.0 BAR 3 (0x0-0x1fffffff), disabling
[    0.135405] pnp 00:0c: mem resource (0x1bef0000-0x1befffff) overlaps 0000:00:00.0 BAR 3 (0x0-0x1fffffff), disabling
[    0.135413] pnp 00:0c: mem resource (0x0-0x9ffff) overlaps 0000:00:00.0 BAR 3 (0x0-0x1fffffff), disabling
[    0.135420] pnp 00:0c: mem resource (0x100000-0x1beeffff) overlaps 0000:00:00.0 BAR 3 (0x0-0x1fffffff), disabling
[    0.135428] pnp 00:0c: mem resource (0x1c000000-0x1fffffff) overlaps 0000:00:00.0 BAR 3 (0x0-0x1fffffff), disabling
[    0.135528] pnp: PnP ACPI: found 13 devices
[    0.135532] ACPI: ACPI bus type pnp unregistered
[    0.135538] PnPBIOS: Disabled by ACPI PNP
[    0.135558] system 00:01: ioport range 0x228-0x22f has been reserved
[    0.135565] system 00:01: ioport range 0x40b-0x40b has been reserved
[    0.135571] system 00:01: ioport range 0x4d6-0x4d6 has been reserved
[    0.135577] system 00:01: ioport range 0xc00-0xc01 has been reserved
[    0.135583] system 00:01: ioport range 0xc14-0xc14 has been reserved
[    0.135589] system 00:01: ioport range 0xc50-0xc52 has been reserved
[    0.135596] system 00:01: ioport range 0xc6c-0xc6d has been reserved
[    0.135602] system 00:01: ioport range 0xc6f-0xc6f has been reserved
[    0.135608] system 00:01: ioport range 0xcd4-0xcdf has been reserved
[    0.135614] system 00:01: ioport range 0x4000-0x40fe has been reserved
[    0.135621] system 00:01: ioport range 0x4210-0x4217 has been reserved
[    0.135635] system 00:06: ioport range 0x4d0-0x4d1 has been reserved
[    0.135641] system 00:06: ioport range 0x800-0x87f has been reserved
[    0.135647] system 00:06: ioport range 0x900-0x90f has been reserved
[    0.135660] system 00:0b: iomem range 0xe0000000-0xefffffff has been reserved
[    0.135673] system 00:0c: iomem range 0xffff0000-0xffffffff has been reserved
[    0.135680] system 00:0c: iomem range 0xfec00000-0xfec00fff could not be reserved
[    0.135687] system 00:0c: iomem range 0xfee00000-0xfee00fff has been reserved
[    0.135693] system 00:0c: iomem range 0xfff80000-0xfffeffff has been reserved
[    0.170559] pci 0000:00:01.0: PCI bridge, secondary bus 0000:01
[    0.170565] pci 0000:00:01.0:   IO window: 0xc000-0xcfff
[    0.170572] pci 0000:00:01.0:   MEM window: 0xfda00000-0xfdafffff
[    0.170579] pci 0000:00:01.0:   PREFETCH window: 0x000000c8000000-0x000000d7ffffff
[    0.170594] pci 0000:00:05.0: PCI bridge, secondary bus 0000:02
[    0.170600] pci 0000:00:05.0:   IO window: 0xd000-0xdfff
[    0.170606] pci 0000:00:05.0:   MEM window: 0xfde00000-0xfdefffff
[    0.170613] pci 0000:00:05.0:   PREFETCH window: 0xfdb00000-0xfdbfffff
[    0.170620] pci 0000:00:14.4: PCI bridge, secondary bus 0000:03
[    0.170627] pci 0000:00:14.4:   IO window: 0xb000-0xbfff
[    0.170637] pci 0000:00:14.4:   MEM window: 0xfdd00000-0xfddfffff
[    0.170645] pci 0000:00:14.4:   PREFETCH window: 0xfdc00000-0xfdcfffff
[    0.170670] pci 0000:00:05.0: setting latency timer to 64
[    0.170685] pci_bus 0000:00: resource 0 io:  [0x00-0xffff]
[    0.170690] pci_bus 0000:00: resource 1 mem: [0x000000-0xffffffff]
[    0.170696] pci_bus 0000:01: resource 0 io:  [0xc000-0xcfff]
[    0.170702] pci_bus 0000:01: resource 1 mem: [0xfda00000-0xfdafffff]
[    0.170708] pci_bus 0000:01: resource 2 pref mem [0xc8000000-0xd7ffffff]
[    0.170714] pci_bus 0000:02: resource 0 io:  [0xd000-0xdfff]
[    0.170719] pci_bus 0000:02: resource 1 mem: [0xfde00000-0xfdefffff]
[    0.170725] pci_bus 0000:02: resource 2 pref mem [0xfdb00000-0xfdbfffff]
[    0.170731] pci_bus 0000:03: resource 0 io:  [0xb000-0xbfff]
[    0.170737] pci_bus 0000:03: resource 1 mem: [0xfdd00000-0xfddfffff]
[    0.170743] pci_bus 0000:03: resource 2 pref mem [0xfdc00000-0xfdcfffff]
[    0.170748] pci_bus 0000:03: resource 3 io:  [0x00-0xffff]
[    0.170754] pci_bus 0000:03: resource 4 mem: [0x000000-0xffffffff]
[    0.170814] NET: Registered protocol family 2
[    0.170979] IP route cache hash table entries: 4096 (order: 2, 16384 bytes)
[    0.171487] TCP established hash table entries: 16384 (order: 5, 131072 bytes)
[    0.171631] TCP bind hash table entries: 16384 (order: 5, 131072 bytes)
[    0.171786] TCP: Hash tables configured (established 16384 bind 16384)
[    0.171790] TCP reno registered
[    0.171930] NET: Registered protocol family 1
[    0.171955] pci 0000:00:00.0: MSI quirk detected; MSI disabled
[    0.171963] pci 0000:00:01.0: MSI quirk detected; subordinate MSI disabled
[    0.221669] pci 0000:01:05.0: Boot video device
[    0.221957] cpufreq-nforce2: No nForce2 chipset.
[    0.222003] Scanning for low memory corruption every 60 seconds
[    0.222194] audit: initializing netlink socket (disabled)
[    0.222217] type=2000 audit(1274720380.221:1): initialized
[    0.242440] Trying to unpack rootfs image as initramfs...
[    0.266240] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    0.268980] VFS: Disk quotas dquot_6.5.2
[    0.269096] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.270186] fuse init (API version 7.13)
[    0.270356] msgmni has been set to 849
[    0.274422] alg: No test for stdrng (krng)
[    0.274554] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.274560] io scheduler noop registered
[    0.274564] io scheduler anticipatory registered
[    0.274568] io scheduler deadline registered
[    0.274653] io scheduler cfq registered (default)
[    0.274866] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.274906] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.275054] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0
[    0.275063] ACPI: Power Button [PWRB]
[    0.275156] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
[    0.275162] ACPI: Power Button [PWRF]
[    0.275545] processor LNXCPU:00: registered as cooling_device0
[    0.282894] thermal LNXTHERM:01: registered as thermal_zone0
[    0.282909] ACPI: Thermal Zone [THRM] (27 C)
[    0.285243] isapnp: Scanning for PnP cards...
[    0.291105] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    0.291272] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.291825] 00:08: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.298183] brd: module loaded
[    0.299056] loop: module loaded
[    0.299222] input: Macintosh mouse button emulation as /devices/virtual/input/input2
[    0.299465]   alloc irq_desc for 23 on node -1
[    0.299470]   alloc kstat_irqs on node -1
[    0.299489] pata_acpi 0000:00:12.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    0.299579]   alloc irq_desc for 16 on node -1
[    0.299583]   alloc kstat_irqs on node -1
[    0.299596] pata_acpi 0000:00:14.1: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.300175] Fixed MDIO Bus: probed
[    0.300243] PPP generic driver version 2.4.2
[    0.300330] tun: Universal TUN/TAP device driver, 1.6
[    0.300335] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.300494] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.300526]   alloc irq_desc for 19 on node -1
[    0.300530]   alloc kstat_irqs on node -1
[    0.300546] ehci_hcd 0000:00:13.2: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    0.300574] ehci_hcd 0000:00:13.2: EHCI Host Controller
[    0.300629] ehci_hcd 0000:00:13.2: new USB bus registered, assigned bus number 1
[    0.300731] ehci_hcd 0000:00:13.2: irq 19, io mem 0xfe02c000
[    0.344425] ehci_hcd 0000:00:13.2: USB 2.0 started, EHCI 1.00
[    0.344604] usb usb1: configuration #1 chosen from 1 choice
[    0.344656] hub 1-0:1.0: USB hub found
[    0.344678] hub 1-0:1.0: 8 ports detected
[    0.344794] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.344822] ohci_hcd 0000:00:13.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    0.344846] ohci_hcd 0000:00:13.0: OHCI Host Controller
[    0.344907] ohci_hcd 0000:00:13.0: new USB bus registered, assigned bus number 2
[    0.344938] ohci_hcd 0000:00:13.0: irq 19, io mem 0xfe02e000
[    0.441884] usb usb2: configuration #1 chosen from 1 choice
[    0.441940] hub 2-0:1.0: USB hub found
[    0.441961] hub 2-0:1.0: 4 ports detected
[    0.442057] ohci_hcd 0000:00:13.1: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    0.442085] ohci_hcd 0000:00:13.1: OHCI Host Controller
[    0.442152] ohci_hcd 0000:00:13.1: new USB bus registered, assigned bus number 3
[    0.442185] ohci_hcd 0000:00:13.1: irq 19, io mem 0xfe02d000
[    0.529547] usb usb3: configuration #1 chosen from 1 choice
[    0.529601] hub 3-0:1.0: USB hub found
[    0.534193] hub 3-0:1.0: 4 ports detected
[    0.534329] uhci_hcd: USB Universal Host Controller Interface driver
[    0.534472] PNP: PS/2 Controller [PNP0f13:PS2M] at 0x60,0x64 irq 12
[    0.534477] PNP: PS/2 controller doesn't have KBD irq; using default 1
[    0.538149] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.538163] serio: i8042 AUX port at 0x60,0x64 irq 12
[    0.538426] mice: PS/2 mouse device common for all mice
[    0.538634] rtc_cmos 00:03: RTC can wake from S4
[    0.538704] rtc_cmos 00:03: rtc core: registered rtc_cmos as rtc0
[    0.538754] rtc0: alarms up to one month, 242 bytes nvram
[    0.538960] device-mapper: uevent: version 1.0.3
[    0.541993] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: dm-devel@redhat.com
[    0.545670] device-mapper: multipath: version 1.1.0 loaded
[    0.545677] device-mapper: multipath round-robin: version 1.0.0 loaded
[    0.545959] EISA: Probing bus 0 at eisa.0
[    0.545987] Cannot allocate resource for EISA slot 4
[    0.546013] EISA: Detected 0 cards.
[    0.546097] cpuidle: using governor ladder
[    0.546100] cpuidle: using governor menu
[    0.546899] TCP cubic registered
[    0.547202] NET: Registered protocol family 10
[    0.548012] lo: Disabled Privacy Extensions
[    0.548608] NET: Registered protocol family 17
[    0.548665] powernow-k8: Found 1 AMD Sempron(tm) Processor 3000+ processors (1 cpu cores) (version 2.20.00)
[    0.548730] powernow-k8:    0 : fid 0xa (1800 MHz), vid 0x6
[    0.548736] powernow-k8:    1 : fid 0x2 (1000 MHz), vid 0x12
[    0.548785] Marking TSC unstable due to cpufreq changes
[    0.563226] Switching to clocksource acpi_pm
[    0.572509] Using IPI No-Shortcut mode
[    0.572627] PM: Resume from disk failed.
[    0.572640] registered taskstats version 1
[    0.572941]   Magic number: 10:935:995
[    0.573033] rtc_cmos 00:03: setting system clock to 2010-05-24 16:59:41 UTC (1274720381)
[    0.573037] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.573039] EDD information not available.
[    0.904576] Freeing initrd memory: 7767k freed
[    0.955943] isapnp: No Plug & Play device found
[    0.955962] usb 3-1: new low speed USB device using ohci_hcd and address 2
[    0.956016] Freeing unused kernel memory: 656k freed
[    0.956738] Write protecting the kernel text: 4676k
[    0.956773] Write protecting the kernel read-only data: 1840k
[    0.981924] udev: starting version 151
[    1.166176] usb 3-1: configuration #1 chosen from 1 choice
[    1.178436] Floppy drive(s): fd0 is 1.44M
[    1.196086] FDC 0 is a post-1991 82077
[    1.217685] tg3.c:v3.102 (September 1, 2009)
[    1.217706]   alloc irq_desc for 17 on node -1
[    1.217709]   alloc kstat_irqs on node -1
[    1.217721] tg3 0000:02:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    1.217731] tg3 0000:02:00.0: setting latency timer to 64
[    1.222969] scsi0 : pata_atiixp
[    1.230293] scsi1 : pata_atiixp
[    1.231155] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xe400 irq 14
[    1.231159] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xe408 irq 15
[    1.231224] sata_sil 0000:00:12.0: version 2.4
[    1.240149] scsi2 : sata_sil
[    1.241999] scsi3 : sata_sil
[    1.242066] ata3: SATA max UDMA/100 mmio m512@0xfe02f000 tf 0xfe02f080 irq 23
[    1.242071] ata4: SATA max UDMA/100 mmio m512@0xfe02f000 tf 0xfe02f0c0 irq 23
[    1.243583] eth0: Tigon3 [partno(BCM95751) rev 4200] (PCI Express) MAC address 00:13:d3:2a:bd:df
[    1.243589] eth0: attached PHY is 5750 (10/100/1000Base-T Ethernet) (WireSpeed[1])
[    1.243593] eth0: RXcsums[1] LinkChgREG[0] MIirq[0] ASF[0] TSOcap[1]
[    1.243596] eth0: dma_rwctrl[76180000] dma_mask[64-bit]
[    1.392758] ata1.00: ATAPI: HL-DT-STDVDRRW GWA-4161B, 1.17, max UDMA/44
[    1.392786] ata1.00: limited to UDMA/33 due to 40-wire cable
[    1.408709] ata1.00: configured for UDMA/33
[    1.411883] scsi 0:0:0:0: CD-ROM            HL-DT-ST DVDRRW GWA-4161B 1.17 PQ: 0 ANSI: 5
[    1.417541] sr0: scsi3-mmc drive: 24x/40x writer cd/rw xa/form2 cdda tray
[    1.417546] Uniform CD-ROM driver Revision: 3.20
[    1.417894] sr 0:0:0:0: Attached scsi CD-ROM sr0
[    1.418065] sr 0:0:0:0: Attached scsi generic sg0 type 5
[    1.560066] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    1.568333] ata3.00: ATA-7: ST380013AS, 3.43, max UDMA/100
[    1.568337] ata3.00: 156301488 sectors, multi 16: LBA48 
[    1.584346] ata3.00: configured for UDMA/100
[    1.584471] scsi 2:0:0:0: Direct-Access     ATA      ST380013AS       3.43 PQ: 0 ANSI: 5
[    1.584801] sd 2:0:0:0: Attached scsi generic sg1 type 0
[    1.585011] sd 2:0:0:0: [sda] 156301488 512-byte logical blocks: (80.0 GB/74.5 GiB)
[    1.585060] sd 2:0:0:0: [sda] Write Protect is off
[    1.585064] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.585088] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.585246]  sda: sda1 sda2 < sda5 >
[    1.613946] sd 2:0:0:0: [sda] Attached SCSI disk
[    1.904048] ata4: SATA link down (SStatus 0 SControl 300)
[    1.915895] usbcore: registered new interface driver hiddev
[    1.921499] input: Logitech Logitech USB Keyboard as /devices/pci0000:00/0000:00:13.1/usb3/3-1/3-1:1.0/input/input3
[    1.921597] generic-usb 0003:046D:C315.0001: input,hidraw0: USB HID v1.10 Keyboard [Logitech Logitech USB Keyboard] on usb-0000:00:13.1-1/input0
[    1.921625] usbcore: registered new interface driver usbhid
[    1.921629] usbhid: v2.6:USB HID core driver
[    2.232484] EXT4-fs (sda1): mounted filesystem with ordered data mode
[    8.506050] Adding 1297400k swap on /dev/sda5.  Priority:-1 extents:1 across:1297400k 
[    8.517396] udev: starting version 151
[    8.621993] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[    8.677008] lp: driver loaded but no devices found
[    8.750097] Linux agpgart interface v0.103
[    8.854085] parport_pc 00:09: reported by Plug and Play ACPI
[    8.854166] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
[    8.992426] lp0: using parport0 (interrupt-driven).
[    9.136657] piix4_smbus 0000:00:14.0: SMBus Host Controller at 0x500, revision 0
[    9.143403] [drm] Initialized drm 1.1.0 20060810
[    9.146448] ppdev: user-space parallel port driver
[    9.219639] type=1505 audit(1274709590.142:2):  operation="profile_load" pid=495 name="/sbin/dhclient3"
[    9.219964] type=1505 audit(1274709590.142:3):  operation="profile_load" pid=495 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[    9.220196] type=1505 audit(1274709590.146:4):  operation="profile_load" pid=495 name="/usr/lib/connman/scripts/dhclient-script"
[    9.339600] psmouse serio1: ID: 10 00 64
[    9.358706] [drm] radeon defaulting to kernel modesetting.
[    9.358713] [drm] radeon kernel modesetting enabled.
[    9.358796] radeon 0000:01:05.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    9.367303] [drm] radeon: Initializing kernel modesetting.
[    9.377284] [drm] register mmio base: 0xFDAF0000
[    9.377288] [drm] register mmio size: 65536
[    9.377936] [drm] GPU reset succeed (RBBM_STATUS=0x00000140)
[    9.378027] [drm:rs400_gart_adjust_size] *ERROR* Forcing to 32M GART size (because of ASIC bug ?)
[    9.378072] [drm] Generation 2 PCI interface, using max accessible memory
[    9.378075] [drm] radeon: VRAM 64M
[    9.378078] [drm] radeon: VRAM from 0x1C000000 to 0x1FFFFFFF
[    9.378080] [drm] radeon: GTT 32M
[    9.378082] [drm] radeon: GTT from 0x20000000 to 0x21FFFFFF
[    9.378130] [drm] radeon: irq initialized.
[    9.378199] [drm] Detected VRAM RAM=64M, BAR=128M
[    9.378205] [drm] RAM width 128bits DDR
[    9.381326] [TTM] Zone  kernel: Available graphics memory: 221760 kiB.
[    9.381350] [drm] radeon: 64M of VRAM memory ready
[    9.381353] [drm] radeon: 32M of GTT memory ready.
[    9.381377] [drm] GART: num cpu pages 8192, num gpu pages 8192
[    9.381795] [drm] radeon: 3 quad pipes, 1 z pipes initialized.
[    9.381810] [drm] radeon: cp idle (0x10000C03)
[    9.381953] [drm] Loading R300 Microcode
[    9.382340] platform radeon_cp.0: firmware: requesting radeon/R300_cp.bin
[    9.401599] [drm] radeon: ring at 0x0000000020000000
[    9.401620] [drm] ring test succeeded in 1 usecs
[    9.401735] [drm] radeon: ib pool ready.
[    9.401806] [drm] ib test succeeded in 0 usecs
[    9.401927] [drm] GPIO Table revision: 0
[    9.401991] [drm:radeon_get_legacy_connector_info_from_bios] *ERROR* Unknown connector type: 8
[    9.402039] [drm] Radeon Display Connectors
[    9.402041] [drm] Connector 0:
[    9.402043] [drm]   VGA
[    9.402046] [drm]   DDC: 0x68 0x68 0x68 0x68 0x68 0x68 0x68 0x68
[    9.402049] [drm]   Encoders:
[    9.402050] [drm]     CRT1: INTERNAL_DAC2
[    9.402053] [drm] Connector 1:
[    9.402054] [drm]   DVI-D
[    9.402056] [drm]   HPD1
[    9.402059] [drm]   DDC: 0x198 0x198 0x19c 0x19c 0x1a0 0x1a0 0x1a4 0x1a4
[    9.402062] [drm]   Encoders:
[    9.402064] [drm]     DFP1: INTERNAL_DVO1
[    9.612679] type=1505 audit(1274709590.538:5):  operation="profile_replace" pid=609 name="/sbin/dhclient3"
[    9.613011] type=1505 audit(1274709590.538:6):  operation="profile_replace" pid=609 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[    9.613196] type=1505 audit(1274709590.538:7):  operation="profile_replace" pid=609 name="/usr/lib/connman/scripts/dhclient-script"
[    9.657860] type=1505 audit(1274709590.582:8):  operation="profile_load" pid=612 name="/usr/bin/evince"
[    9.681516] type=1505 audit(1274709590.606:9):  operation="profile_load" pid=612 name="/usr/bin/evince-previewer"
[    9.684232] type=1505 audit(1274709590.610:10):  operation="profile_load" pid=612 name="/usr/bin/evince-thumbnailer"
[    9.723676] ATI IXP AC97 controller 0000:00:14.5: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    9.749736] type=1505 audit(1274709590.674:11):  operation="profile_load" pid=617 name="/usr/lib/cups/backend/cups-pdf"
[    9.894738] [drm] fb mappable at 0xD0040000
[    9.894742] [drm] vram apper at 0xD0000000
[    9.894744] [drm] size 5242880
[    9.894746] [drm] fb depth is 24
[    9.894748] [drm]    pitch is 5120
[    9.899767] fb0: radeondrmfb frame buffer device
[    9.899771] registered panic notifier
[    9.899779] [drm] Initialized radeon 2.0.0 20080528 for 0000:01:05.0 on minor 0
[    9.908550] vga16fb: initializing
[    9.908559] vga16fb: mapped to 0xc00a0000
[    9.908565] vga16fb: not registering due to another framebuffer present
[   10.024179] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   10.057537] Console: switching to colour frame buffer device 160x64
[   10.072405] input: ImPS/2 Logitech Wheel Mouse as /devices/platform/i8042/serio1/input/input4
[   11.395235] tg3: eth0: Link is up at 100 Mbps, full duplex.
[   11.395239] tg3: eth0: Flow control is on for TX and on for RX.
[   11.395295] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   22.200016] eth0: no IPv6 routers present
[   35.551635] process `skype' is using obsolete setsockopt SO_BSDCOMPAT
[   68.046768] end_request: I/O error, dev fd0, sector 0
[  106.082203] end_request: I/O error, dev fd0, sector 0
[  517.619381] NET: Registered protocol family 4
[  561.817043] [drm:radeon_cs_ioctl] *ERROR* Failed to parse relocation -12!
[  625.559086] [drm:radeon_cs_ioctl] *ERROR* Failed to parse relocation -12!
[  733.432936] [drm:radeon_cs_ioctl] *ERROR* Failed to parse relocation -12!
[  825.452019] hrtimer: interrupt took 29333 ns
[  835.501651] [drm:radeon_cs_ioctl] *ERROR* Failed to parse relocation -12!

```

---

