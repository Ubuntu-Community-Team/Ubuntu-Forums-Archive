---
title: "will these computer last for long?"
date: 2010-08-18
forum: General Help
---

### Post by enhu on 2010-08-18
there's just too much error in it. this is the dmesg:
anything to solve these?

> [    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.32-21-generic (buildd@rothera) (gcc version 4.4.3 (Ubuntu 4.4.3-4ubuntu5) ) #32-Ubuntu SMP Fri Apr 16 08:10:02 UTC 2010 (Ubuntu 2.6.32-21.32-generic 2.6.32.11+drm33.2)
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
[    0.000000]  BIOS-e820: 00000000000e7400 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000001ff70000 (usable)
[    0.000000]  BIOS-e820: 000000001ff70000 - 000000001ff7fc00 (ACPI data)
[    0.000000]  BIOS-e820: 000000001ff7fc00 - 000000001ff80000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000001ff80000 - 0000000020000000 (reserved)
[    0.000000]  BIOS-e820: 00000000ffb80000 - 00000000ffc00000 (reserved)
[    0.000000]  BIOS-e820: 00000000fff00000 - 0000000100000000 (reserved)
[    0.000000] DMI 2.3 present.
[    0.000000] Phoenix BIOS detected: BIOS may corrupt low RAM, working around it.
[    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
[    0.000000] last_pfn = 0x1ff70 max_arch_pfn = 0x100000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-C7FFF write-protect
[    0.000000]   C8000-EFFFF uncachable
[    0.000000]   F0000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000 mask FE0000000 write-back
[    0.000000]   1 disabled
[    0.000000]   2 disabled
[    0.000000]   3 disabled
[    0.000000]   4 disabled
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] PAT not supported by CPU.
[    0.000000] Scanning 0 areas for low memory corruption
[    0.000000] modified physical RAM map:
[    0.000000]  modified: 0000000000000000 - 0000000000010000 (reserved)
[    0.000000]  modified: 0000000000010000 - 000000000009f800 (usable)
[    0.000000]  modified: 000000000009f800 - 00000000000a0000 (reserved)
[    0.000000]  modified: 00000000000e7400 - 0000000000100000 (reserved)
[    0.000000]  modified: 0000000000100000 - 000000001ff70000 (usable)
[    0.000000]  modified: 000000001ff70000 - 000000001ff7fc00 (ACPI data)
[    0.000000]  modified: 000000001ff7fc00 - 000000001ff80000 (ACPI NVS)
[    0.000000]  modified: 000000001ff80000 - 0000000020000000 (reserved)
[    0.000000]  modified: 00000000ffb80000 - 00000000ffc00000 (reserved)
[    0.000000]  modified: 00000000fff00000 - 0000000100000000 (reserved)
[    0.000000] initial memory mapped : 0 - 00c00000
[    0.000000] init_memory_mapping: 0000000000000000-000000001ff70000
[    0.000000] Using x86 segment limits to approximate NX protection
[    0.000000]  0000000000 - 0000400000 page 4k
[    0.000000]  0000400000 - 001fc00000 page 2M
[    0.000000]  001fc00000 - 001ff70000 page 4k
[    0.000000] kernel direct mapping tables up to 1ff70000 @ 10000-15000
[    0.000000] RAMDISK: 1783c000 - 17fd3d33
[    0.000000] ACPI: RSDP 000f65a0 00014 (v00 PTLTD )
[    0.000000] ACPI: RSDT 1ff7c715 00028 (v01 PTLTD  ? RSDT   06040000  LTP 00000000)
[    0.000000] ACPI: FACP 1ff7fb8c 00074 (v01 INTEL  Solano   06040000 PTL  000F4240)
[    0.000000] ACPI: DSDT 1ff7c73d 0344F (v01  INTEL   Solano 06040000 MSFT 0100000B)
[    0.000000] ACPI: FACS 1ff7ffc0 00040
[    0.000000] 0MB HIGHMEM available.
[    0.000000] 511MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 1ff70000
[    0.000000]   low ram: 0 - 1ff70000
[    0.000000]   node 0 low ram: 00000000 - 1ff70000
[    0.000000]   node 0 bootmap 00011000 - 00014ff0
[    0.000000] (9 early reservations) ==> bootmem [0000000000 - 001ff70000]
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
[    0.000000]   #1 [0000001000 - 0000002000]    EX TRAMPOLINE ==> [0000001000 - 0000002000]
[    0.000000]   #2 [0000006000 - 0000007000]       TRAMPOLINE ==> [0000006000 - 0000007000]
[    0.000000]   #3 [0000100000 - 00008d9e98]    TEXT DATA BSS ==> [0000100000 - 00008d9e98]
[    0.000000]   #4 [001783c000 - 0017fd3d33]          RAMDISK ==> [001783c000 - 0017fd3d33]
[    0.000000]   #5 [000009f800 - 0000100000]    BIOS reserved ==> [000009f800 - 0000100000]
[    0.000000]   #6 [00008da000 - 00008dd128]              BRK ==> [00008da000 - 00008dd128]
[    0.000000]   #7 [0000010000 - 0000011000]          PGTABLE ==> [0000010000 - 0000011000]
[    0.000000]   #8 [0000011000 - 0000015000]          BOOTMAP ==> [0000011000 - 0000015000]
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000010 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x0001ff70
[    0.000000]   HighMem  0x0001ff70 -> 0x0001ff70
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[2] active PFN ranges
[    0.000000]     0: 0x00000010 -> 0x0000009f
[    0.000000]     0: 0x00000100 -> 0x0001ff70
[    0.000000] On node 0 totalpages: 130815
[    0.000000] free_area_init_node: node 0, pgdat c0798720, node_mem_map c1001200
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3951 pages, LIFO batch:0
[    0.000000]   Normal zone: 991 pages used for memmap
[    0.000000]   Normal zone: 125841 pages, LIFO batch:31
[    0.000000] Using APIC driver default
[    0.000000] ACPI: PM-Timer IO Port: 0x1008
[    0.000000] SMP: Allowing 1 CPUs, 0 hotplug CPUs
[    0.000000] Local APIC disabled by BIOS -- you can enable it with "lapic"
[    0.000000] APIC: disable apic facility
[    0.000000] nr_irqs_gsi: 16
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e8000
[    0.000000] PM: Registered nosave memory: 00000000000e8000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 20000000 (gap: 20000000:dfb80000)
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:1 nr_node_ids:1
[    0.000000] PERCPU: Embedded 14 pages/cpu @c1800000 s36024 r0 d21320 u4194304
[    0.000000] pcpu-alloc: s36024 r0 d21320 u4194304 alloc=1*4194304
[    0.000000] pcpu-alloc: [0] 0 
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 129792
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.32-21-generic root=UUID=e9cd6882-9c25-4bac-858f-83a4ce457985 ro quiet splash
[    0.000000] PID hash table entries: 2048 (order: 1, 8192 bytes)
[    0.000000] Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.000000] Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] allocated 2618240 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] Initializing HighMem for node 0 (00000000:00000000)
[    0.000000] Memory: 499888k/523712k available (4673k kernel code, 22980k reserved, 2122k data, 656k init, 0k highmem)
[    0.000000] virtual kernel memory layout:
[    0.000000]     fixmap  : 0xfff1d000 - 0xfffff000   ( 904 kB)
[    0.000000]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[    0.000000]     vmalloc : 0xe0770000 - 0xff7fe000   ( 496 MB)
[    0.000000]     lowmem  : 0xc0000000 - 0xdff70000   ( 511 MB)
[    0.000000]       .init : 0xc07a3000 - 0xc0847000   ( 656 kB)
[    0.000000]       .data : 0xc0590613 - 0xc07a2e48   (2122 kB)
[    0.000000]       .text : 0xc0100000 - 0xc0590613   (4673 kB)
[    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.000000] SLUB: Genslabs=13, HWalign=32, Order=0-3, MinObjects=0, CPUs=1, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000] NR_IRQS:2304 nr_irqs:256
[    0.000000] Console: colour VGA+ 80x25
[    0.000000] console [tty0] enabled
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 897.416 MHz processor.
[    0.004013] Calibrating delay loop (skipped), value calculated using timer frequency.. 1794.83 BogoMIPS (lpj=3589664)
[    0.004075] Security Framework initialized
[    0.004157] AppArmor: AppArmor initialized
[    0.004185] Mount-cache hash table entries: 512
[    0.004592] Initializing cgroup subsys ns
[    0.004610] Initializing cgroup subsys cpuacct
[    0.004622] Initializing cgroup subsys memory
[    0.004653] Initializing cgroup subsys devices
[    0.004661] Initializing cgroup subsys freezer
[    0.004668] Initializing cgroup subsys net_cls
[    0.004735] CPU: L1 I cache: 16K, L1 D cache: 16K
[    0.004744] CPU: L2 cache: 128K
[    0.004760] mce: CPU supports 5 MCE banks
[    0.004808] Performance Events: 
[    0.004816] no APIC, boot with the "lapic" boot parameter to force-enable it.
[    0.004823] no hardware sampling interrupt available.
[    0.004829] p6 PMU driver.
[    0.004865] ... version:                0
[    0.004870] ... bit width:              32
[    0.004876] ... generic registers:      2
[    0.004882] ... value mask:             00000000ffffffff
[    0.004889] ... max period:             000000007fffffff
[    0.004895] ... fixed-purpose events:   0
[    0.004900] ... event mask:             0000000000000003
[    0.004916] Checking 'hlt' instruction... OK.
[    0.021459] SMP alternatives: switching to UP code
[    0.035611] Freeing SMP alternatives: 19k freed
[    0.035695] ACPI: Core revision 20090903
[    0.043357] ACPI: setting ELCR to 0200 (from 0e00)
[    0.043494] ftrace: converting mcount calls to 0f 1f 44 00 00
[    0.043517] ftrace: allocating 21771 entries in 43 pages
[    0.048345] Enabling APIC mode:  Flat.  Using 0 I/O APICs
[    0.048362] weird, boot CPU (#0) not listed by the BIOS.
[    0.048369] SMP motherboard not detected.
[    0.048377] Local APIC not detected. Using dummy APIC emulation.
[    0.048383] SMP disabled
[    0.049264] Brought up 1 CPUs
[    0.049280] Total of 1 processors activated (1794.83 BogoMIPS).
[    0.050051] CPU0 attaching NULL sched-domain.
[    0.050577] devtmpfs: initialized
[    0.052435] regulator: core version 0.5
[    0.052490] Time:  9:40:40  Date: 08/18/10
[    0.052693] NET: Registered protocol family 16
[    0.053097] EISA bus registered
[    0.053151] ACPI: bus type pci registered
[    0.054576] PCI: PCI BIOS revision 2.10 entry at 0xfd981, last bus=2
[    0.054586] PCI: Using configuration type 1 for base access
[    0.057766] bio: create slab <bio-0> at 0
[    0.059157] ACPI: EC: Look up EC in DSDT
[    0.065217] ACPI: Interpreter enabled
[    0.065251] ACPI: (supports S0 S1 S5)
[    0.065299] ACPI: Using PIC for interrupt routing
[    0.073410] ACPI: No dock devices found.
[    0.076325] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.076491] pci 0000:00:00.0: reg 10 32bit mmio pref: [0xf8000000-0xfbffffff]
[    0.076753] pci 0000:00:1f.0: quirk: region 1000-107f claimed by ICH4 ACPI/GPIO/TCO
[    0.076763] pci 0000:00:1f.0: quirk: region 1180-11bf claimed by ICH4 GPIO
[    0.076826] pci 0000:00:1f.1: reg 20 io port: [0x1800-0x180f]
[    0.076908] pci 0000:00:1f.2: reg 20 io port: [0x1820-0x183f]
[    0.077014] pci 0000:01:00.0: reg 10 32bit mmio: [0xf4000000-0xf4ffffff]
[    0.077028] pci 0000:01:00.0: reg 14 32bit mmio pref: [0xf6000000-0xf7ffffff]
[    0.077059] pci 0000:01:00.0: reg 30 32bit mmio pref: [0x000000-0x00ffff]
[    0.077147] pci 0000:00:01.0: bridge 32bit mmio: [0xf4000000-0xf4ffffff]
[    0.077158] pci 0000:00:01.0: bridge 32bit mmio pref: [0xf6000000-0xf7ffffff]
[    0.077227] pci 0000:02:08.0: reg 10 32bit mmio: [0xf5010000-0xf5010fff]
[    0.077241] pci 0000:02:08.0: reg 14 32bit mmio: [0xf5000000-0xf500ffff]
[    0.077296] pci 0000:02:08.0: supports D1 D2
[    0.077303] pci 0000:02:08.0: PME# supported from D0 D1 D2 D3hot
[    0.077313] pci 0000:02:08.0: PME# disabled
[    0.077369] pci 0000:02:0d.0: reg 10 io port: [0x2000-0x207f]
[    0.077383] pci 0000:02:0d.0: reg 14 32bit mmio: [0xf5011000-0xf501107f]
[    0.077417] pci 0000:02:0d.0: reg 30 32bit mmio pref: [0x000000-0x01ffff]
[    0.077445] pci 0000:02:0d.0: supports D1 D2
[    0.077451] pci 0000:02:0d.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.077460] pci 0000:02:0d.0: PME# disabled
[    0.077499] pci 0000:00:1e.0: transparent bridge
[    0.077509] pci 0000:00:1e.0: bridge io port: [0x2000-0x2fff]
[    0.077519] pci 0000:00:1e.0: bridge 32bit mmio: [0xf5000000-0xf50fffff]
[    0.077542] pci_bus 0000:00: on NUMA node 0
[    0.077561] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.077717] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.AGP_._PRT]
[    0.077800] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.HUB_._PRT]
[    0.080307] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 7 9 10 *11 12 14 15)
[    0.080564] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 7 9 *10 11 12 14 15)
[    0.080790] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 7 9 10 11 12 14 15) *0, disabled.
[    0.081017] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 7 *9 10 11 12 14 15)
[    0.081443] vgaarb: device added: PCI:0000:01:00.0,decodes=io+mem,owns=io+mem,locks=none
[    0.081458] vgaarb: loaded
[    0.081900] SCSI subsystem initialized
[    0.082220] libata version 3.00 loaded.
[    0.082577] usbcore: registered new interface driver usbfs
[    0.082619] usbcore: registered new interface driver hub
[    0.082774] usbcore: registered new device driver usb
[    0.083386] ACPI: WMI: Mapper loaded
[    0.083396] PCI: Using ACPI for IRQ routing
[    0.083794] NetLabel: Initializing
[    0.083804] NetLabel:  domain hash size = 128
[    0.083809] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.083850] NetLabel:  unlabeled traffic allowed by default
[    0.084047] Switching to clocksource tsc
[    0.090908] AppArmor: AppArmor Filesystem Enabled
[    0.090998] pnp: PnP ACPI init
[    0.091067] ACPI: bus type pnp registered
[    0.100416] ACPI Error: Field [ALB2] at 120 exceeds Buffer [CRSA] size 104 (bits) (20090903/dsopcode-596)
[    0.100441] ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.PCI0.LPC0.SIO_.LPT_._CRS] (Node df814228), AE_AML_BUFFER_LIMIT
[    0.100505] ACPI Error (uteval-0250): Method execution failed [\_SB_.PCI0.LPC0.SIO_.LPT_._CRS] (Node df814228), AE_AML_BUFFER_LIMIT
[    0.100528] pnp 00:0b: can't evaluate _CRS: 12298
[    0.101580] pnp: PnP ACPI: found 12 devices
[    0.101592] ACPI: ACPI bus type pnp unregistered
[    0.101604] PnPBIOS: Disabled by ACPI PNP
[    0.101666] system 00:02: ioport range 0x1000-0x107f has been reserved
[    0.101676] system 00:02: ioport range 0x1180-0x11bf has been reserved
[    0.101686] system 00:02: ioport range 0x4d0-0x4d1 has been reserved
[    0.101698] system 00:02: iomem range 0xff800000-0xffffffff could not be reserved
[    0.136906] pci 0000:01:00.0: BAR 6: can't allocate mem resource [0xf8000000-0xf7ffffff]
[    0.136919] pci 0000:00:01.0: PCI bridge, secondary bus 0000:01
[    0.136926] pci 0000:00:01.0:   IO window: disabled
[    0.136937] pci 0000:00:01.0:   MEM window: 0xf4000000-0xf4ffffff
[    0.136948] pci 0000:00:01.0:   PREFETCH window: 0xf6000000-0xf7ffffff
[    0.136963] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:02
[    0.136971] pci 0000:00:1e.0:   IO window: 0x2000-0x2fff
[    0.136983] pci 0000:00:1e.0:   MEM window: 0xf5000000-0xf50fffff
[    0.136993] pci 0000:00:1e.0:   PREFETCH window: 0x20000000-0x200fffff
[    0.137029] pci 0000:00:1e.0: setting latency timer to 64
[    0.137041] pci_bus 0000:00: resource 0 io:  [0x00-0xffff]
[    0.137048] pci_bus 0000:00: resource 1 mem: [0x000000-0xffffffff]
[    0.137057] pci_bus 0000:01: resource 1 mem: [0xf4000000-0xf4ffffff]
[    0.137065] pci_bus 0000:01: resource 2 pref mem [0xf6000000-0xf7ffffff]
[    0.137073] pci_bus 0000:02: resource 0 io:  [0x2000-0x2fff]
[    0.137081] pci_bus 0000:02: resource 1 mem: [0xf5000000-0xf50fffff]
[    0.137088] pci_bus 0000:02: resource 2 pref mem [0x20000000-0x200fffff]
[    0.137096] pci_bus 0000:02: resource 3 io:  [0x00-0xffff]
[    0.137104] pci_bus 0000:02: resource 4 mem: [0x000000-0xffffffff]
[    0.137222] NET: Registered protocol family 2
[    0.137542] IP route cache hash table entries: 4096 (order: 2, 16384 bytes)
[    0.138533] TCP established hash table entries: 16384 (order: 5, 131072 bytes)
[    0.138978] TCP bind hash table entries: 16384 (order: 5, 131072 bytes)
[    0.139681] TCP: Hash tables configured (established 16384 bind 16384)
[    0.139819] TCP reno registered
[    0.140252] NET: Registered protocol family 1
[    0.140384] pci 0000:01:00.0: Boot video device
[    0.140944] cpufreq-nforce2: No nForce2 chipset.
[    0.141029] Scanning for low memory corruption every 60 seconds
[    0.141445] audit: initializing netlink socket (disabled)
[    0.141496] type=2000 audit(1282124440.139:1): initialized
[    0.166355] Trying to unpack rootfs image as initramfs...
[    0.192365] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    0.207879] VFS: Disk quotas dquot_6.5.2
[    0.208214] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.210501] fuse init (API version 7.13)
[    0.210892] msgmni has been set to 977
[    0.211996] alg: No test for stdrng (krng)
[    0.212227] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.212239] io scheduler noop registered
[    0.212245] io scheduler anticipatory registered
[    0.212250] io scheduler deadline registered
[    0.212419] io scheduler cfq registered (default)
[    0.212746] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.212819] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.213110] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0
[    0.213132] ACPI: Power Button [PWRB]
[    0.213269] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
[    0.213278] ACPI: Power Button [PWRF]
[    0.213589] ACPI: Invalid PBLK length [5]
[    0.213730] processor LNXCPU:00: registered as cooling_device0
[    0.227574] isapnp: Scanning for PnP cards...
[    0.236956] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    0.237175] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.237404] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[    0.238265] 00:08: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.238620] 00:09: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[    0.290393] brd: module loaded
[    0.296712] loop: module loaded
[    0.297114] input: Macintosh mouse button emulation as /devices/virtual/input/input2
[    0.297508] ata_piix 0000:00:1f.1: version 2.13
[    0.297925] ata_piix 0000:00:1f.1: power state changed by ACPI to D0
[    0.298081] ata_piix 0000:00:1f.1: setting latency timer to 64
[    0.303828] scsi0 : ata_piix
[    0.304384] scsi1 : ata_piix
[    0.306365] ata1: PATA max UDMA/66 cmd 0x1f0 ctl 0x3f6 bmdma 0x1800 irq 14
[    0.306377] ata2: PATA max UDMA/66 cmd 0x170 ctl 0x376 bmdma 0x1808 irq 15
[    0.307651] Fixed MDIO Bus: probed
[    0.312027] PPP generic driver version 2.4.2
[    0.312333] tun: Universal TUN/TAP device driver, 1.6
[    0.312342] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.312712] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.312789] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.312831] uhci_hcd: USB Universal Host Controller Interface driver
[    0.313526] ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 9
[    0.313538] PCI: setting IRQ 9 as level-triggered
[    0.313549] uhci_hcd 0000:00:1f.2: PCI INT D -> Link[LNKD] -> GSI 9 (level, low) -> IRQ 9
[    0.313572] uhci_hcd 0000:00:1f.2: setting latency timer to 64
[    0.313582] uhci_hcd 0000:00:1f.2: UHCI Host Controller
[    0.313793] uhci_hcd 0000:00:1f.2: new USB bus registered, assigned bus number 1
[    0.313849] uhci_hcd 0000:00:1f.2: irq 9, io base 0x00001820
[    0.314235] usb usb1: configuration #1 chosen from 1 choice
[    0.314335] hub 1-0:1.0: USB hub found
[    0.314376] hub 1-0:1.0: 2 ports detected
[    0.314691] PNP: PS/2 Controller [PNP0303:KBC0] at 0x60,0x64 irq 1
[    0.314701] PNP: PS/2 appears to have AUX port disabled, if this is incorrect please boot with i8042.nopnp
[    0.315566] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.320229] mice: PS/2 mouse device common for all mice
[    0.320964] rtc_cmos 00:05: rtc core: registered rtc_cmos as rtc0
[    0.321011] rtc0: alarms up to one month, y3k, 114 bytes nvram
[    0.321371] device-mapper: uevent: version 1.0.3
[    0.321992] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: [email]dm-devel@redhat.com[/email]
[    0.324013] device-mapper: multipath: version 1.1.0 loaded
[    0.324030] device-mapper: multipath round-robin: version 1.0.0 loaded
[    0.326172] EISA: Probing bus 0 at eisa.0
[    0.326193] Cannot allocate resource for EISA slot 1
[    0.326200] Cannot allocate resource for EISA slot 2
[    0.326234] EISA: Detected 0 cards.
[    0.330731] cpuidle: using governor ladder
[    0.330745] cpuidle: using governor menu
[    0.332443] TCP cubic registered
[    0.333025] NET: Registered protocol family 10
[    0.334774] lo: Disabled Privacy Extensions
[    0.335910] NET: Registered protocol family 17
[    0.337570] Using IPI No-Shortcut mode
[    0.337964] PM: Resume from disk failed.
[    0.338034] registered taskstats version 1
[    0.338377]   Magic number: 6:450:677
[    0.338550] rtc_cmos 00:05: setting system clock to 2010-08-18 09:40:40 UTC (1282124440)
[    0.338559] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.338565] EDD information not available.
[    0.344080] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input3
[    0.663930] usb 1-2: new low speed USB device using uhci_hcd and address 2
[    0.688126] ata1.00: HPA unlocked: 39177839 -> 39179952, native 39179952
[    0.688149] ata1.00: ATA-6: SAMSUNG SV2001H, QN100-07, max UDMA/100
[    0.688157] ata1.00: 39179952 sectors, multi 16: LBA 
[    0.688264] ata1.01: ATAPI: LITE-ON LTR-48246S, SS0A, max UDMA/33
[    0.688329] ata1.00: limited to UDMA/33 due to 40-wire cable
[    0.696871] ata1.00: configured for UDMA/33
[    0.712268] ata1.01: configured for UDMA/33
[    0.927496] isapnp: No Plug & Play device found
[    0.928098] scsi 0:0:0:0: Direct-Access     ATA      SAMSUNG SV2001H  QN10 PQ: 0 ANSI: 5
[    0.928682] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    0.934696] scsi 0:0:1:0: CD-ROM            LITE-ON  LTR-48246S       SS0A PQ: 0 ANSI: 5
[    0.977091] usb 1-2: configuration #1 chosen from 1 choice
[    1.312441] Freeing initrd memory: 7775k freed
[   31.816127] ata1.01: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6 frozen
[   31.816144] sr 0:0:1:0: CDB: Mode Sense(10): 5a 00 2a 00 00 00 00 00 80 00
[   31.816182] ata1.01: cmd a0/01:00:00:80:00/00:00:00:00:00/b0 tag 0 dma 16512 in
[   31.816186]          res 40/00:03:00:00:00/00:00:00:00:00/b0 Emask 0x4 (timeout)
[   31.816196] ata1.01: status: { DRDY }
[   36.856051] ata1: link is slow to respond, please be patient (ready=0)
[   41.840044] ata1: device not ready (errno=-16), forcing hardreset
[   41.840058] ata1: soft resetting link
[   42.212415] ata1.00: configured for UDMA/33
[   42.228265] ata1.01: configured for UDMA/33
[   42.236810] ata1: EH complete
[   42.237015] sd 0:0:0:0: [sda] 39179952 512-byte logical blocks: (20.0 GB/18.6 GiB)
[   72.816112] ata1.01: limiting speed to UDMA/25:PIO4
[   72.816126] ata1.01: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6 frozen
[   72.816137] sr 0:0:1:0: CDB: Mode Sense(10): 5a 00 2a 00 00 00 00 00 80 00
[   72.816173] ata1.01: cmd a0/01:00:00:80:00/00:00:00:00:00/b0 tag 0 dma 16512 in
[   72.816177]          res 40/00:03:00:00:00/00:00:00:00:00/b0 Emask 0x4 (timeout)
[   72.816186] ata1.01: status: { DRDY }
[   77.856043] ata1: link is slow to respond, please be patient (ready=0)
[   82.840042] ata1: device not ready (errno=-16), forcing hardreset
[   82.840056] ata1: soft resetting link
[   83.212431] ata1.00: configured for UDMA/33
[   83.228266] ata1.01: configured for UDMA/25
[   83.236749] ata1: EH complete
[  113.816106] ata1.01: limiting speed to PIO4
[  113.816119] ata1.01: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6 frozen
[  113.816131] sr 0:0:1:0: CDB: Mode Sense(10): 5a 00 2a 00 00 00 00 00 80 00
[  113.816167] ata1.01: cmd a0/01:00:00:80:00/00:00:00:00:00/b0 tag 0 dma 16512 in
[  113.816171]          res 40/00:03:00:00:00/00:00:00:00:00/b0 Emask 0x4 (timeout)
[  113.816180] ata1.01: status: { DRDY }
[  118.856042] ata1: link is slow to respond, please be patient (ready=0)
[  123.840043] ata1: device not ready (errno=-16), forcing hardreset
[  123.840057] ata1: soft resetting link
[  124.212411] ata1.00: configured for UDMA/33
[  124.228267] ata1.01: configured for PIO4
[  124.236731] ata1: EH complete
[  124.244855] sr0: scsi3-mmc drive: 48x/48x writer cd/rw xa/form2 cdda tray
[  124.244867] Uniform CD-ROM driver Revision: 3.20
[  124.245283] sr 0:0:1:0: Attached scsi CD-ROM sr0
[  124.245533] sr 0:0:1:0: Attached scsi generic sg1 type 5
[  124.245919] sd 0:0:0:0: [sda] Write Protect is off
[  124.245935] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[  124.246060] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[  124.246717]  sda: sda1 sda2 sda3 sda4
[  124.265885] sd 0:0:0:0: [sda] Attached SCSI disk
[  124.265949] Freeing unused kernel memory: 656k freed
[  124.269478] Write protecting the kernel text: 4676k
[  124.269580] Write protecting the kernel read-only data: 1840k
[  124.355882] udev: starting version 151
[  125.066529] FDC 0 is a post-1991 82077
[  125.182374] ACPI: PCI Interrupt Link [LNKB] enabled at IRQ 10
[  125.182387] PCI: setting IRQ 10 as level-triggered
[  125.182400] 3c59x 0000:02:0d.0: PCI INT A -> Link[LNKB] -> GSI 10 (level, low) -> IRQ 10
[  125.182432] 3c59x: Donald Becker and others.
[  125.182452] 0000:02:0d.0: 3Com PCI 3c905C Tornado at e080a000.
[  125.263440] usbcore: registered new interface driver hiddev
[  125.280468] input: USB U+P Mouse as /devices/pci0000:00/0000:00:1f.2/usb1/1-2/1-2:1.0/input/input4
[  125.281925] generic-usb 0003:1C4F:0003.0001: input,hidraw0: USB HID v1.10 Mouse [USB U+P Mouse] on usb-0000:00:1f.2-2/input0
[  125.282065] usbcore: registered new interface driver usbhid
[  125.282658] usbhid: v2.6:USB HID core driver
[  130.695298] kjournald starting.  Commit interval 5 seconds
[  130.695347] EXT3-fs: mounted filesystem with ordered data mode.
[  146.584818] udev: starting version 151
[  147.391786] lp: driver loaded but no devices found
[  147.819275] Linux agpgart interface v0.103
[  147.858996] EXT3 FS on sda2, internal journal
[  147.955756] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[  147.974971] intel_rng: FWH not detected
[  148.227495] parport_pc: probe of 00:0b failed with error -22
[  148.227816] parport0: PC-style at 0x378 (0x778) [PCSPP,TRISTATE]
[  148.228405] parport0: irq 7 detected
[  148.324736] lp0: using parport0 (polling).
[  148.379733] agpgart-intel 0000:00:00.0: Intel i815 Chipset
[  148.430571] agpgart-intel 0000:00:00.0: AGP aperture is 64M @ 0xf8000000
[  148.489571] ppdev: user-space parallel port driver
[  149.005810] type=1505 audit(1282124589.165:2):  operation="profile_load" pid=467 name="/sbin/dhclient3"
[  149.007292] type=1505 audit(1282124589.165:3):  operation="profile_load" pid=467 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[  149.008883] type=1505 audit(1282124589.169:4):  operation="profile_load" pid=467 name="/usr/lib/connman/scripts/dhclient-script"
[  149.046492] [drm] Initialized drm 1.1.0 20060810
[  150.110513] type=1505 audit(1282124590.269:5):  operation="profile_replace" pid=548 name="/sbin/dhclient3"
[  150.112165] type=1505 audit(1282124590.269:6):  operation="profile_replace" pid=548 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[  150.126534] type=1505 audit(1282124590.285:7):  operation="profile_replace" pid=548 name="/usr/lib/connman/scripts/dhclient-script"
[  150.199104] ACPI: PCI Interrupt Link [LNKA] enabled at IRQ 11
[  150.199119] PCI: setting IRQ 11 as level-triggered
[  150.199131] nouveau 0000:01:00.0: PCI INT A -> Link[LNKA] -> GSI 11 (level, low) -> IRQ 11
[  150.249530] type=1505 audit(1282124590.409:8):  operation="profile_load" pid=549 name="/usr/bin/evince"
[  150.276971] [drm] nouveau 0000:01:00.0: Detected an NV 0 generation card (0x20154000)
[  150.277176] [drm] nouveau 0000:01:00.0: Attempting to load BIOS image from PROM
[  150.392486] [drm] nouveau 0000:01:00.0: ... appears to be valid
[  150.393183] [drm] nouveau 0000:01:00.0: BMP BIOS found
[  150.393191] [drm] nouveau 0000:01:00.0: BMP version 2.1
[  150.393199] [drm] nouveau 0000:01:00.0: Bios version 02.05.13.04
[  150.393207] [drm] nouveau 0000:01:00.0: Assuming a CRT output exists
[  150.393215] [drm] nouveau 0000:01:00.0: Probing TV encoders on I2C bus: 1
[  150.399364] eth0:  setting full-duplex.
[  150.494891] type=1505 audit(1282124590.653:9):  operation="profile_load" pid=549 name="/usr/bin/evince-previewer"
[  150.583575] type=1505 audit(1282124590.741:10):  operation="profile_load" pid=549 name="/usr/bin/evince-thumbnailer"
[  150.702151] type=1505 audit(1282124590.861:11):  operation="profile_load" pid=563 name="/usr/lib/cups/backend/cups-pdf"
[  150.797170] [drm] nouveau 0000:01:00.0: No TV encoders found.
[  150.831633] [TTM] Zone  kernel: Available graphics memory: 254366 kiB.
[  150.831683] [drm] nouveau 0000:01:00.0: 32 MiB VRAM
[  150.831817] agpgart-intel 0000:00:00.0: AGP 2.0 bridge
[  150.831856] agpgart-intel 0000:00:00.0: putting AGP V2 device into 4x mode
[  150.831889] nouveau 0000:01:00.0: putting AGP V2 device into 4x mode
[  150.831915] [drm] nouveau 0000:01:00.0: 64 MiB GART (aperture)
[  150.833955] [drm] nouveau 0000:01:00.0: Allocating FIFO number 0
[  150.835734] [drm] nouveau 0000:01:00.0: nouveau_channel_alloc: initialised FIFO 0
[  150.835766] [drm] nouveau 0000:01:00.0: Saving VGA fonts
[  151.026515] [drm] nouveau 0000:01:00.0: Detected a VGA connector
[  151.028160] [drm] nouveau 0000:01:00.0: Setting dpms mode 3 on vga encoder (output 0)
[  151.378047] [drm] nouveau 0000:01:00.0: allocated 1024x768 fb: 0x45000, bo dbf2a000
[  151.381038] fb0: nouveaufb frame buffer device
[  151.381048] registered panic notifier
[  151.381070] [drm] Initialized nouveau 0.0.15 20090420 for 0000:01:00.0 on minor 0
[  151.451149] vga16fb: initializing
[  151.451175] vga16fb: mapped to 0xc00a0000
[  151.451194] vga16fb: not registering due to another framebuffer present
[  151.727612] CS4281 0000:02:08.0: PCI INT A -> Link[LNKD] -> GSI 9 (level, low) -> IRQ 9
[  151.906333] [drm] nouveau 0000:01:00.0: Setting dpms mode 0 on vga encoder (output 0)
[  151.906350] [drm] nouveau 0000:01:00.0: Output VGA-1 is running on CRTC 0 using output @
[  151.951194] Console: switching to colour frame buffer device 128x48
[  152.454710] gameport: CS4281 Gameport is pci0000:02:08.0/gameport0, speed 1612kHz
[  154.317423] [drm] nouveau 0000:01:00.0: Allocating FIFO number 1
[  154.319400] [drm] nouveau 0000:01:00.0: nouveau_channel_alloc: initialised FIFO 1
[  160.652093] eth0: no IPv6 routers present
[ 1390.456157] usb 1-2: USB disconnect, address 2
[ 1392.228115] usb 1-2: new low speed USB device using uhci_hcd and address 3
[ 1392.437253] usb 1-2: configuration #1 chosen from 1 choice
[ 1392.455131] input: USB U+P Mouse as /devices/pci0000:00/0000:00:1f.2/usb1/1-2/1-2:1.0/input/input5
[ 1392.460606] generic-usb 0003:1C4F:0003.0002: input,hidraw0: USB HID v1.10 Mouse [USB U+P Mouse] on usb-0000:00:1f.2-2/input0
[ 2624.752158] usb 1-2: USB disconnect, address 3
[ 2627.748133] usb 1-2: new low speed USB device using uhci_hcd and address 4
[ 2627.958387] usb 1-2: configuration #1 chosen from 1 choice
[ 2627.977289] input: USB U+P Mouse as /devices/pci0000:00/0000:00:1f.2/usb1/1-2/1-2:1.0/input/input6
[ 2627.978746] generic-usb 0003:1C4F:0003.0003: input,hidraw0: USB HID v1.10 Mouse [USB U+P Mouse] on usb-0000:00:1f.2-2/input0
[ 3547.808146] usb 1-2: USB disconnect, address 4
[ 3551.152123] usb 1-1: new low speed USB device using uhci_hcd and address 5
[ 3551.363087] usb 1-1: configuration #1 chosen from 1 choice
[ 3551.380362] input: USB U+P Mouse as /devices/pci0000:00/0000:00:1f.2/usb1/1-1/1-1:1.0/input/input7
[ 3551.394240] generic-usb 0003:1C4F:0003.0004: input,hidraw0: USB HID v1.10 Mouse [USB U+P Mouse] on usb-0000:00:1f.2-1/input0
[ 3583.272247] usb 1-1: USB disconnect, address 5
[ 3589.232077] usb 1-1: new low speed USB device using uhci_hcd and address 6
[ 3589.442921] usb 1-1: configuration #1 chosen from 1 choice
[ 3589.461353] input: USB U+P Mouse as /devices/pci0000:00/0000:00:1f.2/usb1/1-1/1-1:1.0/input/input8
[ 3589.471177] generic-usb 0003:1C4F:0003.0005: input,hidraw0: USB HID v1.10 Mouse [USB U+P Mouse] on usb-0000:00:1f.2-1/input0
[ 3649.488187] usb 1-1: USB disconnect, address 6
[ 3651.768162] usb 1-2: new low speed USB device using uhci_hcd and address 7
[ 3651.975827] usb 1-2: configuration #1 chosen from 1 choice
[ 3651.994568] input: USB U+P Mouse as /devices/pci0000:00/0000:00:1f.2/usb1/1-2/1-2:1.0/input/input9
[ 3651.996800] generic-usb 0003:1C4F:0003.0006: input,hidraw0: USB HID v1.10 Mouse [USB U+P Mouse] on usb-0000:00:1f.2-2/input0
[ 5440.792153] usb 1-2: USB disconnect, address 7
[ 5443.100093] usb 1-2: new low speed USB device using uhci_hcd and address 8
[ 5443.308850] usb 1-2: configuration #1 chosen from 1 choice
[ 5443.326998] input: USB U+P Mouse as /devices/pci0000:00/0000:00:1f.2/usb1/1-2/1-2:1.0/input/input10
[ 5443.334880] generic-usb 0003:1C4F:0003.0007: input,hidraw0: USB HID v1.10 Mouse [USB U+P Mouse] on usb-0000:00:1f.2-2/input0
[ 5742.360248] usb 1-2: USB disconnect, address 8
[ 5744.460128] usb 1-2: new low speed USB device using uhci_hcd and address 9
[ 5744.669165] usb 1-2: configuration #1 chosen from 1 choice
[ 5744.687517] input: USB U+P Mouse as /devices/pci0000:00/0000:00:1f.2/usb1/1-2/1-2:1.0/input/input11
[ 5744.693107] generic-usb 0003:1C4F:0003.0008: input,hidraw0: USB HID v1.10 Mouse [USB U+P Mouse] on usb-0000:00:1f.2-2/input0
[ 7373.704155] usb 1-2: USB disconnect, address 9
[ 7375.652100] usb 1-2: new low speed USB device using uhci_hcd and address 10
[ 7375.861099] usb 1-2: configuration #1 chosen from 1 choice
[ 7375.879465] input: USB U+P Mouse as /devices/pci0000:00/0000:00:1f.2/usb1/1-2/1-2:1.0/input/input12
[ 7375.882702] generic-usb 0003:1C4F:0003.0009: input,hidraw0: USB HID v1.10 Mouse [USB U+P Mouse] on usb-0000:00:1f.2-2/input0
[ 7424.048137] usb 1-2: USB disconnect, address 10
[ 7426.576120] usb 1-1: new low speed USB device using uhci_hcd and address 11
[ 7426.786198] usb 1-1: configuration #1 chosen from 1 choice:D
[ 7426.804386] input: USB U+P Mouse as /devices/pci0000:00/0000:00:1f.2/usb1/1-1/1-1:1.0/input/input13
[ 7426.812669] generic-usb 0003:1C4F:0003.000A: input,hidraw0: USB HID v1.10 Mouse [USB U+P Mouse] on usb-0000:00:1f.2-1/input0


---

### Post by kostkon on 2010-08-18
Hmm, I can see some problems with your ACPI, maybe your BIOS is buggy. And it seems there is a problem with your Lite-On CD/DVD drive, it's time to replace it :P

Is this an old computer?

---

### Post by enhu on 2010-08-18
definitely a very old one. i'm using xubuntu 10.4

enhu-xubuntu:/proc$ cat cpuinfo 
processor	: 0
vendor_id	: GenuineIntel
cpu family	: 6
model		: 8
model name	: Celeron (Coppermine)
stepping	: 10
cpu MHz		: 897.416
cache size	: 128 KB
fdiv_bug	: no
hlt_bug		: no
f00f_bug	: no
coma_bug	: no
fpu		: yes
fpu_exception	: yes
cpuid level	: 2
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 mtrr pge mca cmov pse36 mmx fxsr sse up
bogomips	: 1794.83
clflush size	: 32
cache_alignment	: 32
address sizes	: 36 bits physical, 32 bits virtual
power management:

enhu@enhu-xubuntu:/proc$ 


dyou think it will last till this LTS edition? :D

---

