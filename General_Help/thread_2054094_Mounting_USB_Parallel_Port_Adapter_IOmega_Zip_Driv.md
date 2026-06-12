---
title: "Mounting USB Parallel Port Adapter IOmega Zip Drive"
date: 2012-09-06
forum: General Help
---

### Post by afrodeity on 2012-09-06
How do I mount this

```

lsusb

Bus 003 Device 003: ID 067b:2305 Prolific Technology, Inc. PL2305 Parallel Port
```

It is connected to an IOMEGA 100 Zipdrive.

---

### Post by afrodeity on 2012-09-07
this looks promising [https://launchpad.net/ubuntu/natty/+package/jazip](https://launchpad.net/ubuntu/natty/+package/jazip)

"Mount and unmount Iomega Zip and/or Jaz drives
 It combines Grant Guenther's original command line utility, ziptool, with
 Jaz drive support, a nice X interface and additional utilities to allow
 users to easily mount and unmount disks formatted in either ext2 or fat.
 .
 It supports the Iomega Zip drive with USB, parallel, SCSI or ATAPI
 interfaces, but ATAPI Zip drives are supported only when using kernel SCSI
 emulation. I don't know about the Zip-plus version (someone please tell
 me). The SCSI Jaz drive is supported in both the 1G and 2G capacities. It
 does not support the much older IDE (non-ATAPI) interface drives, nor
 Syquest drives.
 .
 The package also includes jazipconfig, a configuration tool."

Am running jazipconfig, it doesn't detect anything but allows onw to create an entry from scratch, so where is the usb mounted in /dev?

---

### Post by afrodeity on 2012-09-07
output of dmesg

```

[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 3.2.0-29-generic (buildd@roseapple) (gcc version 4.6.3 (Ubuntu/Linaro 4.6.3-1ubuntu5) ) #46-Ubuntu SMP Fri Jul 27 17:04:05 UTC 2012 (Ubuntu 3.2.0-29.46-generic 3.2.24)
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
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f000 (usable)
[    0.000000]  BIOS-e820: 000000000009f000 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 00000000bffa0000 (usable)
[    0.000000]  BIOS-e820: 00000000bffa0000 - 00000000bffae000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000bffae000 - 00000000bfff0000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000bfff0000 - 00000000c0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fff00000 - 0000000100000000 (reserved)
[    0.000000]  BIOS-e820: 0000000100000000 - 0000000140000000 (usable)
[    0.000000] Notice: NX (Execute Disable) protection cannot be enabled in hardware: non-PAE kernel!
[    0.000000] NX (Execute Disable) protection: approximated by x86 segment limits
[    0.000000] DMI present.
[    0.000000] DMI: BIOSTAR Group G41D3/G41D3, BIOS 080015  12/24/2009
[    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
[    0.000000] e820 remove range: 00000000000a0000 - 0000000000100000 (usable)
[    0.000000] last_pfn = 0xbffa0 max_arch_pfn = 0x100000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-CFFFF write-protect
[    0.000000]   D0000-DFFFF uncachable
[    0.000000]   E0000-EFFFF write-through
[    0.000000]   F0000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000 mask F00000000 write-back
[    0.000000]   1 base 100000000 mask FC0000000 write-back
[    0.000000]   2 base 0C0000000 mask FC0000000 uncachable
[    0.000000]   3 disabled
[    0.000000]   4 disabled
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] original variable MTRRs
[    0.000000] reg 0, base: 0GB, range: 4GB, type WB
[    0.000000] reg 1, base: 4GB, range: 1GB, type WB
[    0.000000] reg 2, base: 3GB, range: 1GB, type UC
[    0.000000] total RAM covered: 4096M
[    0.000000] Found optimal setting for mtrr clean up
[    0.000000]  gran_size: 64K 	chunk_size: 64K 	num_reg: 3  	lose cover RAM: 0G
[    0.000000] New variable MTRRs
[    0.000000] reg 0, base: 0GB, range: 2GB, type WB
[    0.000000] reg 1, base: 2GB, range: 1GB, type WB
[    0.000000] reg 2, base: 4GB, range: 1GB, type WB
[    0.000000] e820 update range: 00000000c0000000 - 0000000100000000 (usable) ==> (reserved)
[    0.000000] found SMP MP-table at [c00ff780] ff780
[    0.000000] initial memory mapped : 0 - 01c00000
[    0.000000] Base memory trampoline at [c009b000] 9b000 size 16384
[    0.000000] init_memory_mapping: 0000000000000000-00000000377fe000
[    0.000000]  0000000000 - 0000400000 page 4k
[    0.000000]  0000400000 - 0037400000 page 2M
[    0.000000]  0037400000 - 00377fe000 page 4k
[    0.000000] kernel direct mapping tables up to 377fe000 @ 1bfb000-1c00000
[    0.000000] RAMDISK: 35b94000 - 36dc2000
[    0.000000] ACPI: RSDP 000f8ed0 00014 (v00 ACPIAM)
[    0.000000] ACPI: RSDT bffa0000 00040 (v01 122409 RSDT1146 20091224 MSFT 00000097)
[    0.000000] ACPI: FACP bffa0200 00084 (v01 122409 FACP1146 20091224 MSFT 00000097)
[    0.000000] ACPI: DSDT bffa0440 05C8C (v01  G41EM G41EMC24 00000005 INTL 20051117)
[    0.000000] ACPI: FACS bffae000 00040
[    0.000000] ACPI: APIC bffa0390 0006C (v01 122409 APIC1146 20091224 MSFT 00000097)
[    0.000000] ACPI: MCFG bffa0400 0003C (v01 122409 OEMMCFG  20091224 MSFT 00000097)
[    0.000000] ACPI: OEMB bffae040 00072 (v01 122409 OEMB1146 20091224 MSFT 00000097)
[    0.000000] ACPI: HPET bffa8440 00038 (v01 122409 OEMHPET  20091224 MSFT 00000097)
[    0.000000] ACPI: GSCI bffae0c0 02024 (v01 122409 GMCHSCI  20091224 MSFT 00000097)
[    0.000000] ACPI: SSDT bffb0a20 00363 (v01 DpgPmm    CpuPm 00000012 INTL 20051117)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] 2183MB HIGHMEM available.
[    0.000000] 887MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 377fe000
[    0.000000]   low ram: 0 - 377fe000
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000010 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x000377fe
[    0.000000]   HighMem  0x000377fe -> 0x000bffa0
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[2] active PFN ranges
[    0.000000]     0: 0x00000010 -> 0x0000009f
[    0.000000]     0: 0x00000100 -> 0x000bffa0
[    0.000000] On node 0 totalpages: 786223
[    0.000000] free_area_init_node: node 0, pgdat c1822e80, node_mem_map f4394200
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3951 pages, LIFO batch:0
[    0.000000]   Normal zone: 1744 pages used for memmap
[    0.000000]   Normal zone: 221486 pages, LIFO batch:31
[    0.000000]   HighMem zone: 4368 pages used for memmap
[    0.000000]   HighMem zone: 554642 pages, LIFO batch:31
[    0.000000] Using APIC driver default
[    0.000000] ACPI: PM-Timer IO Port: 0x808
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x82] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x83] disabled)
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 20 low level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0xffffffff base: 0xfed00000
[    0.000000] SMP: Allowing 4 CPUs, 2 hotplug CPUs
[    0.000000] nr_irqs_gsi: 40
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
[    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at c0000000 (gap: c0000000:3ee00000)
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] setup_percpu: NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:4 nr_node_ids:1
[    0.000000] PERCPU: Embedded 13 pages/cpu @f77b7000 s31616 r0 d21632 u53248
[    0.000000] pcpu-alloc: s31616 r0 d21632 u53248 alloc=13*4096
[    0.000000] pcpu-alloc: [0] 0 [0] 1 [0] 2 [0] 3 
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 780079
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.2.0-29-generic root=UUID=8b24c5f3-1993-4bee-97a4-95a976cffc34 ro quiet splash nomodeset video=uvesafb:mode_option=1600x1200-24,mtrr=3,scroll=ywrap vt.handoff=7
[    0.000000] PID hash table entries: 4096 (order: 2, 16384 bytes)
[    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.000000] Initializing CPU#0
[    0.000000] xsave/xrstor: enabled xstate_bv 0x3, cntxt size 0x240
[    0.000000] allocated 12581120 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] Initializing HighMem for node 0 (000377fe:000bffa0)
[    0.000000] Memory: 3078312k/3145344k available (5615k kernel code, 66580k reserved, 2765k data, 712k init, 2236040k highmem)
[    0.000000] virtual kernel memory layout:
[    0.000000]     fixmap  : 0xfff16000 - 0xfffff000   ( 932 kB)
[    0.000000]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[    0.000000]     vmalloc : 0xf7ffe000 - 0xff7fe000   ( 120 MB)
[    0.000000]     lowmem  : 0xc0000000 - 0xf77fe000   ( 887 MB)
[    0.000000]       .init : 0xc1830000 - 0xc18e2000   ( 712 kB)
[    0.000000]       .data : 0xc157be04 - 0xc182f580   (2765 kB)
[    0.000000]       .text : 0xc1000000 - 0xc157be04   (5615 kB)
[    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.000000] SLUB: Genslabs=15, HWalign=64, Order=0-3, MinObjects=0, CPUs=4, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000] 	RCU dyntick-idle grace-period acceleration is enabled.
[    0.000000] NR_IRQS:2304 nr_irqs:712 16
[    0.000000] CPU 0 irqstacks, hard=f700a000 soft=f700c000
[    0.000000] vt handoff: transparent VT on vt#7
[    0.000000] Console: colour dummy device 80x25
[    0.000000] console [tty0] enabled
[    0.000000] hpet clockevent registered
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 3386.272 MHz processor.
[    0.004001] Calibrating delay loop (skipped), value calculated using timer frequency.. 6772.54 BogoMIPS (lpj=13545088)
[    0.004005] pid_max: default: 32768 minimum: 301
[    0.004021] Security Framework initialized
[    0.004032] AppArmor: AppArmor initialized
[    0.004034] Yama: becoming mindful.
[    0.004073] Mount-cache hash table entries: 512
[    0.004172] Initializing cgroup subsys cpuacct
[    0.004176] Initializing cgroup subsys memory
[    0.004181] Initializing cgroup subsys devices
[    0.004183] Initializing cgroup subsys freezer
[    0.004184] Initializing cgroup subsys blkio
[    0.004189] Initializing cgroup subsys perf_event
[    0.004208] CPU: Physical Processor ID: 0
[    0.004209] CPU: Processor Core ID: 0
[    0.004211] mce: CPU supports 6 MCE banks
[    0.004217] CPU0: Thermal monitoring enabled (TM2)
[    0.004220] using mwait in idle threads.
[    0.008573] ACPI: Core revision 20110623
[    0.011026] ftrace: allocating 25891 entries in 51 pages
[    0.012037] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.012387] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.054464] CPU0: Intel Pentium(R) Dual-Core  CPU      E5400  @ 2.70GHz stepping 0a
[    0.056003] Performance Events: PEBS fmt0+, Core2 events, Intel PMU driver.
[    0.056003] ... version:                2
[    0.056003] ... bit width:              40
[    0.056003] ... generic registers:      2
[    0.056003] ... value mask:             000000ffffffffff
[    0.056003] ... max period:             000000007fffffff
[    0.056003] ... fixed-purpose events:   3
[    0.056003] ... event mask:             0000000700000003
[    0.056003] NMI watchdog enabled, takes one hw-pmu counter.
[    0.056003] CPU 1 irqstacks, hard=f7112000 soft=f7114000
[    0.056003] Booting Node   0, Processors  #1
[    0.056003] smpboot cpu 1: start_ip = 9b000
[    0.008000] Initializing CPU#1
[    0.144029] NMI watchdog enabled, takes one hw-pmu counter.
[    0.144056] Brought up 2 CPUs
[    0.144058] Total of 2 processors activated (13545.03 BogoMIPS).
[    0.145116] devtmpfs: initialized
[    0.145116] EVM: security.selinux
[    0.145116] EVM: security.SMACK64
[    0.145116] EVM: security.capability
[    0.145116] PM: Registering ACPI NVS region at bffae000 (270336 bytes)
[    0.145116] print_constraints: dummy: 
[    0.145116] RTC time: 21:23:14, date: 09/06/12
[    0.145116] NET: Registered protocol family 16
[    0.145116] Trying to unpack rootfs image as initramfs...
[    0.145116] EISA bus registered
[    0.145116] ACPI: bus type pci registered
[    0.145116] PCI: MMCONFIG for domain 0000 [bus 00-ff] at [mem 0xe0000000-0xefffffff] (base 0xe0000000)
[    0.145116] PCI: not using MMCONFIG
[    0.145116] PCI: Using configuration type 1 for base access
[    0.145879] bio: create slab <bio-0> at 0
[    0.145936] ACPI: Added _OSI(Module Device)
[    0.145938] ACPI: Added _OSI(Processor Device)
[    0.145939] ACPI: Added _OSI(3.0 _SCP Extensions)
[    0.145941] ACPI: Added _OSI(Processor Aggregator Device)
[    0.148141] ACPI: EC: Look up EC in DSDT
[    0.149400] ACPI: Executed 1 blocks of module-level executable AML code
[    0.151054] ACPI: SSDT bffb00f0 00406 (v01 DpgPmm  P001Ist 00000011 INTL 20051117)
[    0.151269] ACPI: Dynamic OEM Table Load:
[    0.151272] ACPI: SSDT   (null) 00406 (v01 DpgPmm  P001Ist 00000011 INTL 20051117)
[    0.151337] ACPI: SSDT bffb0500 00513 (v01  PmRef  P001Cst 00003001 INTL 20051117)
[    0.151531] ACPI: Dynamic OEM Table Load:
[    0.151533] ACPI: SSDT   (null) 00513 (v01  PmRef  P001Cst 00003001 INTL 20051117)
[    0.152027] ACPI: Interpreter enabled
[    0.152034] ACPI: (supports S0 S1 S3 S4 S5)
[    0.152051] ACPI: Using IOAPIC for interrupt routing
[    0.152068] PCI: MMCONFIG for domain 0000 [bus 00-ff] at [mem 0xe0000000-0xefffffff] (base 0xe0000000)
[    0.153529] PCI: MMCONFIG at [mem 0xe0000000-0xefffffff] reserved in ACPI motherboard resources
[    0.153531] PCI: Using MMCONFIG for extended config space
[    0.158355] ACPI: No dock devices found.
[    0.158357] HEST: Table not found.
[    0.158361] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
[    0.158419] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-ff])
[    0.158542] pci_root PNP0A08:00: host bridge window [io  0x0000-0x0cf7]
[    0.158544] pci_root PNP0A08:00: host bridge window [io  0x0d00-0xffff]
[    0.158546] pci_root PNP0A08:00: host bridge window [mem 0x000a0000-0x000bffff]
[    0.158547] pci_root PNP0A08:00: host bridge window [mem 0x000d0000-0x000dffff]
[    0.158549] pci_root PNP0A08:00: host bridge window [mem 0xc0000000-0xdfffffff]
[    0.158551] pci_root PNP0A08:00: host bridge window [mem 0xf0000000-0xffffffff]
[    0.158561] pci 0000:00:00.0: [8086:2e30] type 0 class 0x000600
[    0.158600] pci 0000:00:01.0: [8086:2e31] type 1 class 0x000604
[    0.158631] pci 0000:00:01.0: PME# supported from D0 D3hot D3cold
[    0.158633] pci 0000:00:01.0: PME# disabled
[    0.158669] pci 0000:00:1b.0: [8086:27d8] type 0 class 0x000403
[    0.158681] pci 0000:00:1b.0: reg 10: [mem 0xf9ffc000-0xf9ffffff 64bit]
[    0.158737] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    0.158740] pci 0000:00:1b.0: PME# disabled
[    0.158756] pci 0000:00:1c.0: [8086:27d0] type 1 class 0x000604
[    0.158816] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    0.158819] pci 0000:00:1c.0: PME# disabled
[    0.158837] pci 0000:00:1c.1: [8086:27d2] type 1 class 0x000604
[    0.158895] pci 0000:00:1c.1: PME# supported from D0 D3hot D3cold
[    0.158898] pci 0000:00:1c.1: PME# disabled
[    0.158917] pci 0000:00:1d.0: [8086:27c8] type 0 class 0x000c03
[    0.158950] pci 0000:00:1d.0: reg 20: [io  0xbc00-0xbc1f]
[    0.158976] pci 0000:00:1d.1: [8086:27c9] type 0 class 0x000c03
[    0.159009] pci 0000:00:1d.1: reg 20: [io  0xb880-0xb89f]
[    0.159035] pci 0000:00:1d.2: [8086:27ca] type 0 class 0x000c03
[    0.159071] pci 0000:00:1d.2: reg 20: [io  0xb800-0xb81f]
[    0.159096] pci 0000:00:1d.3: [8086:27cb] type 0 class 0x000c03
[    0.159130] pci 0000:00:1d.3: reg 20: [io  0xb480-0xb49f]
[    0.159163] pci 0000:00:1d.7: [8086:27cc] type 0 class 0x000c03
[    0.159179] pci 0000:00:1d.7: reg 10: [mem 0xf9ffbc00-0xf9ffbfff]
[    0.159252] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
[    0.159256] pci 0000:00:1d.7: PME# disabled
[    0.159270] pci 0000:00:1e.0: [8086:244e] type 1 class 0x000604
[    0.159322] pci 0000:00:1f.0: [8086:27b8] type 0 class 0x000601
[    0.159396] pci 0000:00:1f.0: ICH7 LPC Generic IO decode 1 PIO at 0a00 (mask 00ff)
[    0.159436] pci 0000:00:1f.1: [8086:27df] type 0 class 0x000101
[    0.159446] pci 0000:00:1f.1: reg 10: [io  0x0000-0x0007]
[    0.159454] pci 0000:00:1f.1: reg 14: [io  0x0000-0x0003]
[    0.159462] pci 0000:00:1f.1: reg 18: [io  0x08f0-0x08f7]
[    0.159469] pci 0000:00:1f.1: reg 1c: [io  0x08f8-0x08fb]
[    0.159477] pci 0000:00:1f.1: reg 20: [io  0xffa0-0xffaf]
[    0.159506] pci 0000:00:1f.2: [8086:27c0] type 0 class 0x000101
[    0.159517] pci 0000:00:1f.2: reg 10: [io  0xb400-0xb407]
[    0.159524] pci 0000:00:1f.2: reg 14: [io  0xb080-0xb083]
[    0.159531] pci 0000:00:1f.2: reg 18: [io  0xb000-0xb007]
[    0.159539] pci 0000:00:1f.2: reg 1c: [io  0xac00-0xac03]
[    0.159545] pci 0000:00:1f.2: reg 20: [io  0xa880-0xa88f]
[    0.159575] pci 0000:00:1f.2: PME# supported from D3hot
[    0.159577] pci 0000:00:1f.2: PME# disabled
[    0.159588] pci 0000:00:1f.3: [8086:27da] type 0 class 0x000c05
[    0.159633] pci 0000:00:1f.3: reg 20: [io  0x0400-0x041f]
[    0.159691] pci 0000:01:00.0: [10de:06e4] type 0 class 0x000300
[    0.159701] pci 0000:01:00.0: reg 10: [mem 0xfd000000-0xfdffffff]
[    0.159711] pci 0000:01:00.0: reg 14: [mem 0xd0000000-0xdfffffff 64bit pref]
[    0.159720] pci 0000:01:00.0: reg 1c: [mem 0xfa000000-0xfbffffff 64bit]
[    0.159727] pci 0000:01:00.0: reg 24: [io  0xcc00-0xcc7f]
[    0.159733] pci 0000:01:00.0: reg 30: [mem 0xfe9e0000-0xfe9fffff pref]
[    0.159780] pci 0000:00:01.0: PCI bridge to [bus 01-01]
[    0.159782] pci 0000:00:01.0:   bridge window [io  0xc000-0xcfff]
[    0.159785] pci 0000:00:01.0:   bridge window [mem 0xfa000000-0xfe9fffff]
[    0.159788] pci 0000:00:01.0:   bridge window [mem 0xd0000000-0xdfffffff 64bit pref]
[    0.159820] pci 0000:00:1c.0: PCI bridge to [bus 02-02]
[    0.159877] pci 0000:03:00.0: [10ec:8136] type 0 class 0x000200
[    0.159892] pci 0000:03:00.0: reg 10: [io  0xd800-0xd8ff]
[    0.159917] pci 0000:03:00.0: reg 18: [mem 0xf8fff000-0xf8ffffff 64bit pref]
[    0.159933] pci 0000:03:00.0: reg 20: [mem 0xf8fe0000-0xf8feffff 64bit pref]
[    0.159944] pci 0000:03:00.0: reg 30: [mem 0xfeae0000-0xfeafffff pref]
[    0.160018] pci 0000:03:00.0: supports D1 D2
[    0.160020] pci 0000:03:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.160024] pci 0000:03:00.0: PME# disabled
[    0.168030] pci 0000:00:1c.1: PCI bridge to [bus 03-03]
[    0.168035] pci 0000:00:1c.1:   bridge window [io  0xd000-0xdfff]
[    0.168038] pci 0000:00:1c.1:   bridge window [mem 0xfea00000-0xfeafffff]
[    0.168042] pci 0000:00:1c.1:   bridge window [mem 0xf8f00000-0xf8ffffff 64bit pref]
[    0.168075] pci 0000:04:02.0: [14f1:2f50] type 0 class 0x000780
[    0.168090] pci 0000:04:02.0: reg 10: [mem 0xfebf0000-0xfebfffff]
[    0.168098] pci 0000:04:02.0: reg 14: [io  0xec00-0xec07]
[    0.168159] pci 0000:04:02.0: PME# supported from D3hot D3cold
[    0.168163] pci 0000:04:02.0: PME# disabled
[    0.168201] pci 0000:00:1e.0: PCI bridge to [bus 04-04] (subtractive decode)
[    0.168204] pci 0000:00:1e.0:   bridge window [io  0xe000-0xefff]
[    0.168207] pci 0000:00:1e.0:   bridge window [mem 0xfeb00000-0xfebfffff]
[    0.168211] pci 0000:00:1e.0:   bridge window [io  0x0000-0x0cf7] (subtractive decode)
[    0.168213] pci 0000:00:1e.0:   bridge window [io  0x0d00-0xffff] (subtractive decode)
[    0.168215] pci 0000:00:1e.0:   bridge window [mem 0x000a0000-0x000bffff] (subtractive decode)
[    0.168217] pci 0000:00:1e.0:   bridge window [mem 0x000d0000-0x000dffff] (subtractive decode)
[    0.168219] pci 0000:00:1e.0:   bridge window [mem 0xc0000000-0xdfffffff] (subtractive decode)
[    0.168220] pci 0000:00:1e.0:   bridge window [mem 0xf0000000-0xffffffff] (subtractive decode)
[    0.168235] pci_bus 0000:00: on NUMA node 0
[    0.168241] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.168358] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P2._PRT]
[    0.168386] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P1._PRT]
[    0.168451] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P4._PRT]
[    0.168477] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P5._PRT]
[    0.168509]  pci0000:00: Requesting ACPI _OSC control (0x1d)
[    0.168511]  pci0000:00: ACPI _OSC request failed (AE_NOT_FOUND), returned control mask: 0x1d
[    0.168512] ACPI _OSC control for PCIe not granted, disabling ASPM
[    0.172335] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 *10 11 12 14 15)
[    0.172371] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 10 *11 12 14 15)
[    0.172404] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 *6 7 10 11 12 14 15)
[    0.172437] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 *5 6 7 10 11 12 14 15)
[    0.172474] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[    0.172509] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[    0.172543] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[    0.172577] ACPI: PCI Interrupt Link [LNKH] (IRQs *3 4 5 6 7 10 11 12 14 15)
[    0.172657] vgaarb: device added: PCI:0000:01:00.0,decodes=io+mem,owns=io+mem,locks=none
[    0.172659] vgaarb: loaded
[    0.172660] vgaarb: bridge control possible 0000:01:00.0
[    0.172745] i2c-core: driver [aat2870] using legacy suspend method
[    0.172746] i2c-core: driver [aat2870] using legacy resume method
[    0.172807] SCSI subsystem initialized
[    0.172848] libata version 3.00 loaded.
[    0.172885] usbcore: registered new interface driver usbfs
[    0.172893] usbcore: registered new interface driver hub
[    0.172911] usbcore: registered new device driver usb
[    0.172975] PCI: Using ACPI for IRQ routing
[    0.178073] PCI: pci_cache_line_size set to 64 bytes
[    0.178132] reserve RAM buffer: 000000000009f000 - 000000000009ffff 
[    0.178134] reserve RAM buffer: 00000000bffa0000 - 00000000bfffffff 
[    0.178219] NetLabel: Initializing
[    0.178221] NetLabel:  domain hash size = 128
[    0.178222] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.178230] NetLabel:  unlabeled traffic allowed by default
[    0.178269] HPET: 3 timers in total, 0 timers will be used for per-cpu timer
[    0.178273] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[    0.178276] hpet0: 3 comparators, 64-bit 14.318180 MHz counter
[    0.184109] Switching to clocksource hpet
[    0.189870] AppArmor: AppArmor Filesystem Enabled
[    0.189896] pnp: PnP ACPI init
[    0.189912] ACPI: bus type pnp registered
[    0.190007] pnp 00:00: [bus 00-ff]
[    0.190009] pnp 00:00: [io  0x0cf8-0x0cff]
[    0.190011] pnp 00:00: [io  0x0000-0x0cf7 window]
[    0.190012] pnp 00:00: [io  0x0d00-0xffff window]
[    0.190014] pnp 00:00: [mem 0x000a0000-0x000bffff window]
[    0.190015] pnp 00:00: [mem 0x000d0000-0x000dffff window]
[    0.190017] pnp 00:00: [mem 0xc0000000-0xdfffffff window]
[    0.190018] pnp 00:00: [mem 0xf0000000-0xffffffff window]
[    0.190062] pnp 00:00: Plug and Play ACPI device, IDs PNP0a08 PNP0a03 (active)
[    0.190069] pnp 00:01: [mem 0xfed14000-0xfed19fff]
[    0.190070] pnp 00:01: [mem 0xfed90000-0xfed93fff]
[    0.190110] system 00:01: [mem 0xfed14000-0xfed19fff] has been reserved
[    0.190112] system 00:01: [mem 0xfed90000-0xfed93fff] has been reserved
[    0.190114] system 00:01: Plug and Play ACPI device, IDs PNP0c01 (active)
[    0.190140] pnp 00:02: [dma 4]
[    0.190142] pnp 00:02: [io  0x0000-0x000f]
[    0.190143] pnp 00:02: [io  0x0081-0x0083]
[    0.190145] pnp 00:02: [io  0x0087]
[    0.190146] pnp 00:02: [io  0x0089-0x008b]
[    0.190147] pnp 00:02: [io  0x008f]
[    0.190149] pnp 00:02: [io  0x00c0-0x00df]
[    0.190170] pnp 00:02: Plug and Play ACPI device, IDs PNP0200 (active)
[    0.190177] pnp 00:03: [io  0x0070-0x0071]
[    0.190187] pnp 00:03: [irq 8]
[    0.190208] pnp 00:03: Plug and Play ACPI device, IDs PNP0b00 (active)
[    0.190214] pnp 00:04: [io  0x0061]
[    0.190233] pnp 00:04: Plug and Play ACPI device, IDs PNP0800 (active)
[    0.190239] pnp 00:05: [io  0x00f0-0x00ff]
[    0.190242] pnp 00:05: [irq 13]
[    0.190263] pnp 00:05: Plug and Play ACPI device, IDs PNP0c04 (active)
[    0.190673] pnp 00:06: [io  0x03f8-0x03ff]
[    0.190677] pnp 00:06: [irq 4]
[    0.190679] pnp 00:06: [dma 0 disabled]
[    0.190746] pnp 00:06: Plug and Play ACPI device, IDs PNP0501 (active)
[    0.191504] pnp 00:07: [io  0x0378-0x037f]
[    0.191508] pnp 00:07: [irq 7]
[    0.191509] pnp 00:07: [dma 0 disabled]
[    0.191719] pnp 00:07: Plug and Play ACPI device, IDs PNP0400 (active)
[    0.191759] pnp 00:08: [io  0x0060]
[    0.191760] pnp 00:08: [io  0x0064]
[    0.191764] pnp 00:08: [irq 12]
[    0.191789] pnp 00:08: Plug and Play ACPI device, IDs PNP0f03 PNP0f13 (active)
[    0.191882] pnp 00:09: [io  0x0000-0xffffffff disabled]
[    0.191883] pnp 00:09: [io  0x0a00-0x0a0f]
[    0.191885] pnp 00:09: [io  0x0a10-0x0a1f]
[    0.191886] pnp 00:09: [io  0x0a20-0x0a2f]
[    0.191887] pnp 00:09: [io  0x0a30-0x0a3f]
[    0.191923] system 00:09: [io  0x0a00-0x0a0f] has been reserved
[    0.191925] system 00:09: [io  0x0a10-0x0a1f] has been reserved
[    0.191927] system 00:09: [io  0x0a20-0x0a2f] has been reserved
[    0.191929] system 00:09: [io  0x0a30-0x0a3f] has been reserved
[    0.191931] system 00:09: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.191981] pnp 00:0a: [io  0x0010-0x001f]
[    0.191983] pnp 00:0a: [io  0x0022-0x003f]
[    0.191984] pnp 00:0a: [io  0x0044-0x005f]
[    0.191986] pnp 00:0a: [io  0x0062-0x0063]
[    0.191987] pnp 00:0a: [io  0x0065-0x006f]
[    0.191988] pnp 00:0a: [io  0x0072-0x007f]
[    0.191990] pnp 00:0a: [io  0x0080]
[    0.191991] pnp 00:0a: [io  0x0084-0x0086]
[    0.191992] pnp 00:0a: [io  0x0088]
[    0.191994] pnp 00:0a: [io  0x008c-0x008e]
[    0.192017] pnp 00:0a: [io  0x0090-0x009f]
[    0.192019] pnp 00:0a: [io  0x00a2-0x00bf]
[    0.192020] pnp 00:0a: [io  0x00e0-0x00ef]
[    0.192021] pnp 00:0a: [io  0x04d0-0x04d1]
[    0.192023] pnp 00:0a: [io  0x0800-0x087f]
[    0.192024] pnp 00:0a: [io  0x0000-0xffffffff disabled]
[    0.192026] pnp 00:0a: [io  0x0480-0x04bf]
[    0.192027] pnp 00:0a: [mem 0xfed1c000-0xfed1ffff]
[    0.192029] pnp 00:0a: [mem 0xfed20000-0xfed8ffff]
[    0.192070] system 00:0a: [io  0x04d0-0x04d1] has been reserved
[    0.192072] system 00:0a: [io  0x0800-0x087f] has been reserved
[    0.192074] system 00:0a: [io  0x0480-0x04bf] has been reserved
[    0.192076] system 00:0a: [mem 0xfed1c000-0xfed1ffff] has been reserved
[    0.192078] system 00:0a: [mem 0xfed20000-0xfed8ffff] has been reserved
[    0.192080] system 00:0a: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.192120] pnp 00:0b: [mem 0xfed00000-0xfed003ff]
[    0.192142] pnp 00:0b: Plug and Play ACPI device, IDs PNP0103 (active)
[    0.192176] pnp 00:0c: [mem 0xffb00000-0xffbfffff]
[    0.192177] pnp 00:0c: [mem 0xfff00000-0xffffffff]
[    0.192202] pnp 00:0c: Plug and Play ACPI device, IDs INT0800 (active)
[    0.192229] pnp 00:0d: [mem 0xffc00000-0xffefffff]
[    0.192261] system 00:0d: [mem 0xffc00000-0xffefffff] has been reserved
[    0.192263] system 00:0d: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.192317] pnp 00:0e: [mem 0xfec00000-0xfec00fff]
[    0.192319] pnp 00:0e: [mem 0xfee00000-0xfee00fff]
[    0.192353] system 00:0e: [mem 0xfec00000-0xfec00fff] could not be reserved
[    0.192355] system 00:0e: [mem 0xfee00000-0xfee00fff] has been reserved
[    0.192357] system 00:0e: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.192382] pnp 00:0f: [mem 0xe0000000-0xefffffff]
[    0.192414] system 00:0f: [mem 0xe0000000-0xefffffff] has been reserved
[    0.192416] system 00:0f: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.192527] pnp 00:10: [mem 0x00000000-0x0009ffff]
[    0.192529] pnp 00:10: [mem 0x000c0000-0x000cffff]
[    0.192530] pnp 00:10: [mem 0x000e0000-0x000fffff]
[    0.192532] pnp 00:10: [mem 0x00100000-0xbfffffff]
[    0.192533] pnp 00:10: [mem 0x00000000-0xffffffff disabled]
[    0.192573] system 00:10: [mem 0x00000000-0x0009ffff] could not be reserved
[    0.192575] system 00:10: [mem 0x000c0000-0x000cffff] could not be reserved
[    0.192577] system 00:10: [mem 0x000e0000-0x000fffff] could not be reserved
[    0.192579] system 00:10: [mem 0x00100000-0xbfffffff] could not be reserved
[    0.192581] system 00:10: Plug and Play ACPI device, IDs PNP0c01 (active)
[    0.192671] pnp: PnP ACPI: found 17 devices
[    0.192672] ACPI: ACPI bus type pnp unregistered
[    0.192674] PnPBIOS: Disabled by ACPI PNP
[    0.228503] PCI: max bus depth: 1 pci_try_num: 2
[    0.228538] pci 0000:00:1c.0: BAR 14: assigned [mem 0xc0000000-0xc01fffff]
[    0.228540] pci 0000:00:1c.0: BAR 15: assigned [mem 0xc0200000-0xc03fffff 64bit pref]
[    0.228544] pci 0000:00:1c.0: BAR 13: assigned [io  0x1000-0x1fff]
[    0.228546] pci 0000:00:01.0: PCI bridge to [bus 01-01]
[    0.228548] pci 0000:00:01.0:   bridge window [io  0xc000-0xcfff]
[    0.228551] pci 0000:00:01.0:   bridge window [mem 0xfa000000-0xfe9fffff]
[    0.228553] pci 0000:00:01.0:   bridge window [mem 0xd0000000-0xdfffffff 64bit pref]
[    0.228557] pci 0000:00:1c.0: PCI bridge to [bus 02-02]
[    0.228559] pci 0000:00:1c.0:   bridge window [io  0x1000-0x1fff]
[    0.228563] pci 0000:00:1c.0:   bridge window [mem 0xc0000000-0xc01fffff]
[    0.228566] pci 0000:00:1c.0:   bridge window [mem 0xc0200000-0xc03fffff 64bit pref]
[    0.228570] pci 0000:00:1c.1: PCI bridge to [bus 03-03]
[    0.228573] pci 0000:00:1c.1:   bridge window [io  0xd000-0xdfff]
[    0.228576] pci 0000:00:1c.1:   bridge window [mem 0xfea00000-0xfeafffff]
[    0.228579] pci 0000:00:1c.1:   bridge window [mem 0xf8f00000-0xf8ffffff 64bit pref]
[    0.228584] pci 0000:00:1e.0: PCI bridge to [bus 04-04]
[    0.228586] pci 0000:00:1e.0:   bridge window [io  0xe000-0xefff]
[    0.228590] pci 0000:00:1e.0:   bridge window [mem 0xfeb00000-0xfebfffff]
[    0.228612] pci 0000:00:01.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.228615] pci 0000:00:01.0: setting latency timer to 64
[    0.228620] pci 0000:00:1c.0: enabling device (0104 -> 0107)
[    0.228623] pci 0000:00:1c.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.228626] pci 0000:00:1c.0: setting latency timer to 64
[    0.228633] pci 0000:00:1c.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    0.228636] pci 0000:00:1c.1: setting latency timer to 64
[    0.228641] pci 0000:00:1e.0: setting latency timer to 64
[    0.228644] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
[    0.228645] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff]
[    0.228647] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
[    0.228649] pci_bus 0000:00: resource 7 [mem 0x000d0000-0x000dffff]
[    0.228650] pci_bus 0000:00: resource 8 [mem 0xc0000000-0xdfffffff]
[    0.228652] pci_bus 0000:00: resource 9 [mem 0xf0000000-0xffffffff]
[    0.228654] pci_bus 0000:01: resource 0 [io  0xc000-0xcfff]
[    0.228655] pci_bus 0000:01: resource 1 [mem 0xfa000000-0xfe9fffff]
[    0.228657] pci_bus 0000:01: resource 2 [mem 0xd0000000-0xdfffffff 64bit pref]
[    0.228659] pci_bus 0000:02: resource 0 [io  0x1000-0x1fff]
[    0.228660] pci_bus 0000:02: resource 1 [mem 0xc0000000-0xc01fffff]
[    0.228662] pci_bus 0000:02: resource 2 [mem 0xc0200000-0xc03fffff 64bit pref]
[    0.228664] pci_bus 0000:03: resource 0 [io  0xd000-0xdfff]
[    0.228665] pci_bus 0000:03: resource 1 [mem 0xfea00000-0xfeafffff]
[    0.228667] pci_bus 0000:03: resource 2 [mem 0xf8f00000-0xf8ffffff 64bit pref]
[    0.228669] pci_bus 0000:04: resource 0 [io  0xe000-0xefff]
[    0.228670] pci_bus 0000:04: resource 1 [mem 0xfeb00000-0xfebfffff]
[    0.228672] pci_bus 0000:04: resource 4 [io  0x0000-0x0cf7]
[    0.228674] pci_bus 0000:04: resource 5 [io  0x0d00-0xffff]
[    0.228675] pci_bus 0000:04: resource 6 [mem 0x000a0000-0x000bffff]
[    0.228677] pci_bus 0000:04: resource 7 [mem 0x000d0000-0x000dffff]
[    0.228679] pci_bus 0000:04: resource 8 [mem 0xc0000000-0xdfffffff]
[    0.228680] pci_bus 0000:04: resource 9 [mem 0xf0000000-0xffffffff]
[    0.228713] NET: Registered protocol family 2
[    0.228770] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.228950] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.229332] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.229524] TCP: Hash tables configured (established 131072 bind 65536)
[    0.229525] TCP reno registered
[    0.229527] UDP hash table entries: 512 (order: 2, 16384 bytes)
[    0.229536] UDP-Lite hash table entries: 512 (order: 2, 16384 bytes)
[    0.229600] NET: Registered protocol family 1
[    0.229642] pci 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    0.229658] pci 0000:00:1d.0: PCI INT A disabled
[    0.229666] pci 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    0.229680] pci 0000:00:1d.1: PCI INT B disabled
[    0.229687] pci 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.229701] pci 0000:00:1d.2: PCI INT C disabled
[    0.229706] pci 0000:00:1d.3: PCI INT D -> GSI 16 (level, low) -> IRQ 16
[    0.229719] pci 0000:00:1d.3: PCI INT D disabled
[    0.229726] pci 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    0.256036] pci 0000:00:1d.7: PCI INT A disabled
[    0.256059] pci 0000:01:00.0: Boot video device
[    0.256065] PCI: CLS 32 bytes, default 64
[    0.256333] audit: initializing netlink socket (disabled)
[    0.256341] type=2000 audit(1346966593.252:1): initialized
[    0.274988] highmem bounce pool size: 64 pages
[    0.274991] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    0.284407] VFS: Disk quotas dquot_6.5.2
[    0.284459] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.284847] fuse init (API version 7.17)
[    0.284912] msgmni has been set to 1645
[    0.285128] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.285145] io scheduler noop registered
[    0.285146] io scheduler deadline registered
[    0.285151] io scheduler cfq registered (default)
[    0.285237] pcieport 0000:00:01.0: setting latency timer to 64
[    0.285260] pcieport 0000:00:01.0: irq 40 for MSI/MSI-X
[    0.285294] pcieport 0000:00:1c.0: setting latency timer to 64
[    0.285323] pcieport 0000:00:1c.0: irq 41 for MSI/MSI-X
[    0.285370] pcieport 0000:00:1c.1: setting latency timer to 64
[    0.285399] pcieport 0000:00:1c.1: irq 42 for MSI/MSI-X
[    0.285460] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.285477] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.285535] intel_idle: MWAIT substates: 0x22220
[    0.285536] intel_idle: does not run on family 6 model 23
[    0.285599] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0
[    0.285604] ACPI: Power Button [PWRB]
[    0.285636] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
[    0.285639] ACPI: Power Button [PWRF]
[    0.285749] Monitor-Mwait will be used to enter C-1 state
[    0.285767] Monitor-Mwait will be used to enter C-2 state
[    0.285782] Monitor-Mwait will be used to enter C-3 state
[    0.285785] Marking TSC unstable due to TSC halts in idle
[    0.285792] ACPI: acpi_idle registered with cpuidle
[    0.298048] thermal LNXTHERM:00: registered as thermal_zone0
[    0.298050] ACPI: Thermal Zone [THRM] (34 C)
[    0.298078] ERST: Table is not found!
[    0.298079] GHES: HEST is not enabled!
[    0.298155] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    0.318514] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.318641] isapnp: Scanning for PnP cards...
[    0.436395] Freeing initrd memory: 18616k freed
[    0.671427] isapnp: No Plug & Play device found
[    0.740537] 00:06: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.752358] Linux agpgart interface v0.103
[    0.753576] brd: module loaded
[    0.754154] loop: module loaded
[    0.754264] ata_piix 0000:00:1f.1: version 2.13
[    0.754274] ata_piix 0000:00:1f.1: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    0.754302] ata_piix 0000:00:1f.1: setting latency timer to 64
[    0.754538] scsi0 : ata_piix
[    0.754597] scsi1 : ata_piix
[    0.755391] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xffa0 irq 14
[    0.755393] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xffa8 irq 15
[    0.755409] ata_piix 0000:00:1f.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    0.755413] ata_piix 0000:00:1f.2: MAP [ P0 P2 P1 P3 ]
[    0.755443] ata_piix 0000:00:1f.2: setting latency timer to 64
[    0.755727] scsi2 : ata_piix
[    0.755780] scsi3 : ata_piix
[    0.756813] ata3: SATA max UDMA/133 cmd 0xb400 ctl 0xb080 bmdma 0xa880 irq 19
[    0.756815] ata4: SATA max UDMA/133 cmd 0xb000 ctl 0xac00 bmdma 0xa888 irq 19
[    0.757093] Fixed MDIO Bus: probed
[    0.757108] tun: Universal TUN/TAP device driver, 1.6
[    0.757109] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.757150] PPP generic driver version 2.4.2
[    0.757227] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.757238] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    0.757248] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    0.757251] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    0.757282] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 1
[    0.757296] ehci_hcd 0000:00:1d.7: using broken periodic workaround
[    0.757304] ehci_hcd 0000:00:1d.7: debug port 1
[    0.761177] ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported
[    0.761188] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xf9ffbc00
[    0.776018] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    0.776180] hub 1-0:1.0: USB hub found
[    0.776183] hub 1-0:1.0: 8 ports detected
[    0.776243] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.776252] uhci_hcd: USB Universal Host Controller Interface driver
[    0.776264] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    0.776271] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    0.776273] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    0.776309] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    0.776327] uhci_hcd 0000:00:1d.0: irq 23, io base 0x0000bc00
[    0.776415] hub 2-0:1.0: USB hub found
[    0.776418] hub 2-0:1.0: 2 ports detected
[    0.776462] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    0.776467] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    0.776469] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    0.776499] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 3
[    0.776517] uhci_hcd 0000:00:1d.1: irq 19, io base 0x0000b880
[    0.776606] hub 3-0:1.0: USB hub found
[    0.776610] hub 3-0:1.0: 2 ports detected
[    0.776655] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.776660] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    0.776662] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    0.776693] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 4
[    0.776718] uhci_hcd 0000:00:1d.2: irq 18, io base 0x0000b800
[    0.776806] hub 4-0:1.0: USB hub found
[    0.776808] hub 4-0:1.0: 2 ports detected
[    0.776853] uhci_hcd 0000:00:1d.3: PCI INT D -> GSI 16 (level, low) -> IRQ 16
[    0.776858] uhci_hcd 0000:00:1d.3: setting latency timer to 64
[    0.776860] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[    0.776892] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 5
[    0.776917] uhci_hcd 0000:00:1d.3: irq 16, io base 0x0000b480
[    0.777004] hub 5-0:1.0: USB hub found
[    0.777007] hub 5-0:1.0: 2 ports detected
[    0.777083] usbcore: registered new interface driver libusual
[    0.777123] i8042: PNP: PS/2 Controller [PNP0f03:PS2M] at 0x60,0x64 irq 12
[    0.777124] i8042: PNP: PS/2 controller doesn't have KBD irq; using default 1
[    0.777479] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.777487] serio: i8042 AUX port at 0x60,0x64 irq 12
[    0.777670] mousedev: PS/2 mouse device common for all mice
[    0.777793] rtc_cmos 00:03: RTC can wake from S4
[    0.777884] rtc_cmos 00:03: rtc core: registered rtc_cmos as rtc0
[    0.777904] rtc0: alarms up to one month, y3k, 114 bytes nvram, hpet irqs
[    0.777951] device-mapper: uevent: version 1.0.3
[    0.778003] device-mapper: ioctl: 4.22.0-ioctl (2011-10-19) initialised: dm-devel@redhat.com
[    0.778027] EISA: Probing bus 0 at eisa.0
[    0.778029] EISA: Cannot allocate resource for mainboard
[    0.778031] Cannot allocate resource for EISA slot 1
[    0.778032] Cannot allocate resource for EISA slot 2
[    0.778033] Cannot allocate resource for EISA slot 3
[    0.778034] Cannot allocate resource for EISA slot 4
[    0.778035] Cannot allocate resource for EISA slot 5
[    0.778037] Cannot allocate resource for EISA slot 6
[    0.778038] Cannot allocate resource for EISA slot 7
[    0.778039] Cannot allocate resource for EISA slot 8
[    0.778040] EISA: Detected 0 cards.
[    0.778047] cpufreq-nforce2: No nForce2 chipset.
[    0.778090] cpuidle: using governor ladder
[    0.778158] cpuidle: using governor menu
[    0.778160] EFI Variables Facility v0.08 2004-May-17
[    0.778342] TCP cubic registered
[    0.778428] NET: Registered protocol family 10
[    0.778838] NET: Registered protocol family 17
[    0.778841] Registering the dns_resolver key type
[    0.778856] Using IPI No-Shortcut mode
[    0.778961] PM: Hibernation image not present or could not be loaded.
[    0.778969] registered taskstats version 1
[    0.787725]   Magic number: 12:519:398
[    0.787800] rtc_cmos 00:03: setting system clock to 2012-09-06 21:23:14 UTC (1346966594)
[    0.788085] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.788086] EDD information not available.
[    0.924356] ata1.00: ATAPI: TSSTcorp CDDVDW SH-S202N, SB01, max UDMA/66
[    0.924360] ata1.00: limited to UDMA/33 due to 40-wire cable
[    0.924602] ata4.00: HPA detected: current 976771055, native 976773168
[    0.924605] ata4.00: ATA-8: ST3500413AS, JC45, max UDMA/133
[    0.924607] ata4.00: 976771055 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    0.932325] ata3.00: ATA-7: SAMSUNG HD200HJ, KF100-06, max UDMA7
[    0.932327] ata3.00: 390721968 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    0.932603] ata3.01: ATA-8: ST500DM002-1BD142, KC45, max UDMA/133
[    0.932607] ata3.01: 976773168 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    0.940193] ata1.00: configured for UDMA/33
[    0.940512] ata3.00: configured for UDMA/133
[    0.940597] ata4.00: configured for UDMA/133
[    0.941342] scsi 0:0:0:0: CD-ROM            TSSTcorp CDDVDW SH-S202N  SB01 PQ: 0 ANSI: 5
[    0.943706] sr0: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
[    0.943710] cdrom: Uniform CD-ROM driver Revision: 3.20
[    0.943832] sr 0:0:0:0: Attached scsi CD-ROM sr0
[    0.943941] sr 0:0:0:0: Attached scsi generic sg0 type 5
[    0.948402] ata3.01: configured for UDMA/133
[    0.948481] scsi 2:0:0:0: Direct-Access     ATA      SAMSUNG HD200HJ  KF10 PQ: 0 ANSI: 5
[    0.948560] sd 2:0:0:0: [sda] 390721968 512-byte logical blocks: (200 GB/186 GiB)
[    0.948574] sd 2:0:0:0: Attached scsi generic sg1 type 0
[    0.948593] sd 2:0:0:0: [sda] Write Protect is off
[    0.948595] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    0.948610] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    0.948643] scsi 2:0:1:0: Direct-Access     ATA      ST500DM002-1BD14 KC45 PQ: 0 ANSI: 5
[    0.948717] sd 2:0:1:0: [sdb] 976773168 512-byte logical blocks: (500 GB/465 GiB)
[    0.948718] sd 2:0:1:0: [sdb] 4096-byte physical blocks
[    0.948739] sd 2:0:1:0: Attached scsi generic sg2 type 0
[    0.948811] scsi 3:0:0:0: Direct-Access     ATA      ST3500413AS      JC45 PQ: 0 ANSI: 5
[    0.948906] sd 3:0:0:0: Attached scsi generic sg3 type 0
[    0.948932] sd 3:0:0:0: [sdc] 976771055 512-byte logical blocks: (500 GB/465 GiB)
[    0.948991] sd 3:0:0:0: [sdc] Write Protect is off
[    0.948993] sd 3:0:0:0: [sdc] Mode Sense: 00 3a 00 00
[    0.949018] sd 3:0:0:0: [sdc] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    0.951069]  sdc: sdc1
[    0.951244] sd 3:0:0:0: [sdc] Attached SCSI disk
[    0.955979] sd 2:0:1:0: [sdb] Write Protect is off
[    0.955984] sd 2:0:1:0: [sdb] Mode Sense: 00 3a 00 00
[    0.956158] sd 2:0:1:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.024987]  sda: sda1 sda2
[    1.049881]  sdb: sdb1 sdb2 < sdb5 sdb6 >
[    1.049993] sd 2:0:0:0: [sda] Attached SCSI disk
[    1.050209] sd 2:0:1:0: [sdb] Attached SCSI disk
[    1.050231] Freeing unused kernel memory: 712k freed
[    1.050421] Write protecting the kernel text: 5616k
[    1.050454] Write protecting the kernel read-only data: 2324k
[    1.062019] udevd[102]: starting version 175
[    1.101137] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    1.101155] r8169 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    1.101272] r8169 0000:03:00.0: setting latency timer to 64
[    1.101558] r8169 0000:03:00.0: irq 43 for MSI/MSI-X
[    1.102277] r8169 0000:03:00.0: eth0: RTL8102e at 0xf8018000, 00:30:67:55:f4:0e, XID 04a00000 IRQ 43
[    1.574108] uvesafb: NVIDIA Corporation, G98 Board - 5610002u, Chip Rev   , OEM: NVIDIA, VBE v3.0
[    1.582605] uvesafb: protected mode interface info at c000:cb80
[    1.582606] uvesafb: pmi: set display start = c00ccbe3, set palette = c00ccc3e
[    1.582608] uvesafb: pmi: ports = 3b4 3b5 3ba 3c0 3c1 3c4 3c5 3c6 3c7 3c8 3c9 3cc 3ce 3cf 3d0 3d1 3d2 3d3 3d4 3d5 3da 
[    1.596022] usb 1-7: new high-speed USB device number 7 using ehci_hcd
[    1.645785] uvesafb: VBIOS/hardware doesn't support DDC transfers
[    1.645786] uvesafb: no monitor limits have been set, default refresh rate will be used
[    1.645883] uvesafb: scrolling: ywrap using protected mode interface, yres_virtual=2293
[    1.647581] fbcon: VESA VGA (fb0) is primary device
[    1.648399] Console: switching to colour frame buffer device 200x75
[    1.648431] uvesafb: framebuffer at 0xfb000000, mapped to 0xf8080000, using 14336k, total 14336k
[    1.648432] fb0: VESA VGA frame buffer device
[    1.856509] EXT4-fs (sdb5): mounted filesystem with ordered data mode. Opts: (null)
[    2.036025] usb 2-1: new low-speed USB device number 2 using uhci_hcd
[    2.436030] usb 2-2: new full-speed USB device number 3 using uhci_hcd
[    2.868027] usb 3-1: new full-speed USB device number 2 using uhci_hcd
[    3.268041] usb 3-2: new full-speed USB device number 3 using uhci_hcd
[    3.692028] usb 4-2: new full-speed USB device number 2 using uhci_hcd
[    4.112033] usb 5-2: new low-speed USB device number 2 using uhci_hcd
[   17.905354] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   17.927555] udevd[367]: starting version 175
[   17.961115] lp: driver loaded but no devices found
[   17.963829] it87: Found IT8718F chip at 0xa10, revision 5
[   17.963835] it87: VID is disabled (pins used for GPIO)
[   17.963863] ACPI: resource it87 [io  0x0a15-0x0a16] conflicts with ACPI region IP__ [io 0xa15-0xa16]
[   17.963864] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[   17.978810] intel_rng: FWH not detected
[   17.993891] leds_ss4200: no LED devices found
[   18.016625] ppa: Version 2.07 (for Linux 2.4.x)
[   18.021961] Adding 3404796k swap on /dev/sdb6.  Priority:-1 extents:1 across:3404796k 
[   18.077112] parport_pc 00:07: reported by Plug and Play ACPI
[   18.077154] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
[   18.090422] nvidia: module license 'NVIDIA' taints kernel.
[   18.090424] Disabling lock debugging due to kernel taint
[   18.212920] type=1400 audit(1346959411.922:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=616 comm="apparmor_parser"
[   18.213209] type=1400 audit(1346959411.922:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=616 comm="apparmor_parser"
[   18.213373] type=1400 audit(1346959411.922:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=616 comm="apparmor_parser"
[   18.215043] type=1400 audit(1346959411.922:5): apparmor="STATUS" operation="profile_load" name="/usr/sbin/ntpd" pid=658 comm="apparmor_parser"
[   18.341145] nvidia 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   18.341153] nvidia 0000:01:00.0: setting latency timer to 64
[   18.341158] vgaarb: device changed decodes: PCI:0000:01:00.0,olddecodes=io+mem,decodes=none:owns=io+mem
[   18.341179] lp0: using parport0 (interrupt-driven).
[   18.349005] NVRM: loading NVIDIA UNIX x86 Kernel Module  295.49  Mon Apr 30 23:30:07 PDT 2012
[   18.443925] Bluetooth: Core ver 2.16
[   18.444789] NET: Registered protocol family 31
[   18.444791] Bluetooth: HCI device and connection manager initialized
[   18.444793] Bluetooth: HCI socket layer initialized
[   18.444794] Bluetooth: L2CAP socket layer initialized
[   18.444965] Bluetooth: SCO socket layer initialized
[   18.445321] Bluetooth: Generic Bluetooth USB driver ver 0.6
[   18.449608] usbcore: registered new interface driver btusb
[   18.481612] cfg80211: Calling CRDA to update world regulatory domain
[   18.483011] Linux video capture interface: v2.00
[   18.484186] gspca_main: v2.14.0 registered
[   18.484625] gspca_main: sonixj-2.14.0 probing 0c45:613b
[   18.499445] usblp0: USB Bidirectional printer dev 3 if 1 alt 0 proto 2 vid 0x043D pid 0x011D
[   18.499478] usbcore: registered new interface driver usblp
[   18.499991] input: sonixj as /devices/pci0000:00/0000:00:1d.1/usb3/3-1/input/input2
[   18.500703] usbcore: registered new interface driver sonixj
[   18.525614] cfg80211: World regulatory domain updated:
[   18.525617] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   18.525619] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   18.525621] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   18.525623] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   18.525624] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   18.525626] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   18.528144] ppdev: user-space parallel port driver
[   18.567753] snd_hda_intel 0000:00:1b.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   18.567793] snd_hda_intel 0000:00:1b.0: irq 44 for MSI/MSI-X
[   18.567811] snd_hda_intel 0000:00:1b.0: setting latency timer to 64
[   18.569748] input: HID 04f3:0103 as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1:1.0/input/input3
[   18.570642] generic-usb 0003:04F3:0103.0001: input,hidraw0: USB HID v1.10 Keyboard [HID 04f3:0103] on usb-0000:00:1d.0-1/input0
[   18.593586] input: HID 04f3:0103 as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1:1.1/input/input4
[   18.593929] generic-usb 0003:04F3:0103.0002: input,hidraw1: USB HID v1.10 Device [HID 04f3:0103] on usb-0000:00:1d.0-1/input1
[   18.602573] generic-usb 0003:043D:011D.0003: hiddev0,hidraw2: USB HID v1.00 Device [Lexmark  2600 Series] on usb-0000:00:1d.0-2/input2
[   18.617341] input: SONiX USB Device as /devices/pci0000:00/0000:00:1d.3/usb5/5-2/5-2:1.0/input/input5
[   18.617562] generic-usb 0003:0C45:7401.0004: input,hidraw3: USB HID v1.00 Mouse [SONiX USB Device] on usb-0000:00:1d.3-2/input0
[   18.617616] usbcore: registered new interface driver usbhid
[   18.617617] usbhid: USB HID core driver
[   18.634252] rtl8192cu: MAC address: 78:44:76:93:f8:83
[   18.634259] rtl8192cu: Board Type 0
[   18.660421] rtlwifi: rx_max_size 15360, rx_urb_num 8, in_ep 1
[   18.660426] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
[   18.660428] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   18.660430] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
[   18.660431] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   18.660433] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
[   18.660435] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   18.660436] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
[   18.660438] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   18.660439] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
[   18.660441] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   18.660443] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
[   18.660445] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   18.660446] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
[   18.660448] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   18.660449] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
[   18.660451] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   18.660452] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
[   18.660454] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   18.660456] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
[   18.660458] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   18.660459] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
[   18.660461] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   18.660462] cfg80211: Disabling freq 2467 MHz as custom regd has no rule that fits a 20 MHz wide channel
[   18.660464] cfg80211: Disabling freq 2472 MHz as custom regd has no rule that fits a 20 MHz wide channel
[   18.660465] cfg80211: Disabling freq 2484 MHz as custom regd has no rule that fits a 20 MHz wide channel
[   18.660519] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain
[   18.663545] ieee80211 phy0: Selected rate control algorithm 'rtl_rc'
[   18.664026] usbcore: registered new interface driver rtl8192cu
[   18.667869] rtw driver version=v3.4.3_4369.20120622 
[   18.667872] Build at: Aug 25 2012 21:06:10
[   18.667875] Error: Driver 'rtl8192cu' is already registered, aborting...
[   18.684852] hsfpcibasic2 0000:04:02.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   18.698744] rtl8192cu: MAC auto ON okay!
[   18.732463] rtl8192cu: Tx queue select: 0x05
[   18.733141] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cufw.bin
[   19.134781] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   19.158565] init: plymouth main process (296) killed by ABRT signal
[   19.158754] init: plymouth-splash main process (736) terminated with status 2
[   19.453910] EXT4-fs (sdb5): re-mounted. Opts: errors=remount-ro
[   19.648250] EXT4-fs (sdc1): mounted filesystem with ordered data mode. Opts: (null)
[   19.660225] ttySHSF0 at I/O 0xec00 (irq = 17) is a Conexant HSF softmodem (PCI-14f1:2f50-14f1:205f)
[   19.981380] init: failsafe main process (1119) killed by TERM signal
[   19.984097] init: plymouth-log main process (1118) terminated with status 1
[   20.035650] Bluetooth: RFCOMM TTY layer initialized
[   20.035653] Bluetooth: RFCOMM socket layer initialized
[   20.035655] Bluetooth: RFCOMM ver 1.11
[   20.039897] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   20.039899] Bluetooth: BNEP filters: protocol multicast
[   20.040753] init: plymouth-upstart-bridge main process (1149) terminated with status 1
[   20.066842] type=1400 audit(1346959413.774:6): apparmor="STATUS" operation="profile_load" name="/usr/lib/lightdm/lightdm/lightdm-guest-session-wrapper" pid=1204 comm="apparmor_parser"
[   20.067008] type=1400 audit(1346959413.774:7): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=1205 comm="apparmor_parser"
[   20.067304] type=1400 audit(1346959413.774:8): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=1205 comm="apparmor_parser"
[   20.067469] type=1400 audit(1346959413.774:9): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=1205 comm="apparmor_parser"
[   20.073342] type=1400 audit(1346959413.782:10): apparmor="STATUS" operation="profile_load" name="/usr/lib/telepathy/mission-control-5" pid=1209 comm="apparmor_parser"
[   20.073696] type=1400 audit(1346959413.782:11): apparmor="STATUS" operation="profile_load" name="/usr/lib/telepathy/telepathy-*" pid=1209 comm="apparmor_parser"
[   20.263401] init: Failed to spawn hybrid-gfx main process: unable to execute: No such file or directory
[   20.267883] init: alsa-restore main process (1267) terminated with status 19
[   20.300027] r8169 0000:03:00.0: eth0: link down
[   20.300032] r8169 0000:03:00.0: eth0: link down
[   20.303579] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   20.303877] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   20.465795] cnxthsf_7800206full_DcpDestroy: units still active, waiting..
[   20.465809] cnxthsf_7800206full_DcpDestroy: units still active, waiting..
[   20.465821] cnxthsf_7800206full_DcpDestroy: units still active, waiting..
[   20.465833] cnxthsf_7800206full_DcpDestroy: units still active, waiting..
[   20.465845] cnxthsf_7800206full_DcpDestroy: units still active, waiting..
[   20.465857] cnxthsf_7800206full_DcpDestroy: units still active, waiting..
[   20.465868] cnxthsf_7800206full_DcpDestroy: units still active, waiting..
[   20.465879] cnxthsf_7800206full_DcpDestroy: units still active, waiting..
[   20.465890] cnxthsf_7800206full_DcpDestroy: units still active, waiting..
[   20.465901] cnxthsf_7800206full_DcpDestroy: units still active, waiting..
[   20.465912] cnxthsf_7800206full_DcpDestroy: units still active, waiting..
[   20.465923] cnxthsf_7800206full_DcpDestroy: units still active, waiting..
[   20.465934] cnxthsf_7800206full_DcpDestroy: units still active, waiting..
[   20.465945] cnxthsf_7800206full_DcpDestroy: units still active, waiting..
[   20.465956] cnxthsf_7800206full_DcpDestroy: units still active, waiting..
[   20.465967] cnxthsf_7800206full_DcpDestroy: units still active, waiting..
[   20.465977] cnxthsf_7800206full_DcpDestroy: units still active, waiting..
[   20.465988] cnxthsf_7800206full_DcpDestroy: units still active, waiting..
[   20.465999] cnxthsf_7800206full_DcpDestroy: units still active, waiting..
[   20.466010] cnxthsf_7800206full_DcpDestroy: units still active, waiting..
[   20.466021] cnxthsf_7800206full_DcpDestroy: units still active, waiting..
[   20.466032] cnxthsf_7800206full_DcpDestroy: units still active, waiting..
[   20.466043] cnxthsf_7800206full_DcpDestroy: units still active, waiting..
[   20.466054] cnxthsf_7800206full_DcpDestroy: units still active, waiting..
[   20.466065] cnxthsf_7800206full_DcpDestroy: units still active, waiting..
[   20.466076] cnxthsf_7800206full_DcpDestroy: units still active, waiting..
[   20.466087] cnxthsf_7800206full_DcpDestroy: units still active, waiting..
[   20.466098] cnxthsf_7800206full_DcpDestroy: units still active, waiting..
[   20.466109] cnxthsf_7800206full_DcpDestroy: units still active, waiting..
[   20.466120] cnxthsf_7800206full_DcpDestroy: units still active, waiting..
[   20.466131] cnxthsf_7800206full_DcpDestroy: units still active, waiting..
[   20.478654] hsfpcibasic2 0000:04:02.0: PCI INT A disabled
[   20.796784] hsfpcibasic2 0000:04:02.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   21.305562] ttySHSF0 at I/O 0xec00 (irq = 17) is a Conexant HSF softmodem (PCI-14f1:2f50-14f1:205f)
[   21.608019] hda-intel: azx_get_response timeout, switching to polling mode: last cmd=0x100f0000
[   21.666846] usbcore: registered new interface driver hsfusbcd2
[   22.050273] r8169 0000:03:00.0: eth0: link up
[   22.050419] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   22.612018] hda-intel: No response from codec, disabling MSI: last cmd=0x100f0000
[   23.469448] usb 3-2: usbfs: USBDEVFS_CONTROL failed cmd udev-configure- rqt 161 rq 0 len 1024 ret -110
[   23.616025] hda-intel: Codec #1 probe error; disabling it...
[   23.658893] input: HDA Intel Line as /devices/pci0000:00/0000:00:1b.0/sound/card0/input6
[   23.658981] input: HDA Intel Front Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input7
[   23.659087] input: HDA Intel Rear Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input8
[   23.659182] input: HDA Intel Front Headphone as /devices/pci0000:00/0000:00:1b.0/sound/card0/input9
[   23.659280] input: HDA Intel Line-Out as /devices/pci0000:00/0000:00:1b.0/sound/card0/input10
[   28.469307] usb 3-2: usbfs: USBDEVFS_CONTROL failed cmd udev-configure- rqt 161 rq 0 len 1024 ret -110
[   29.816077] usblp0: removed
[   29.829945] usblp0: USB Bidirectional printer dev 3 if 1 alt 0 proto 2 vid 0x043D pid 0x011D
[   32.640016] eth0: no IPv6 routers present
[   34.188926] vboxdrv: Found 2 processor cores.
[   34.190533] vboxdrv: fAsync=0 offMin=0x1cb offMax=0x87d
[   34.191430] vboxdrv: TSC mode is 'synchronous', kernel timer mode is 'normal'.
[   34.191432] vboxdrv: Successfully loaded version 4.1.12_Ubuntu (interface 0x00190000).
[   34.206145] vboxpci: IOMMU not found (not registered)
[   41.613580] usb 3-2: usbfs: USBDEVFS_CONTROL failed cmd udev-configure- rqt 161 rq 0 len 1024 ret -110
[   46.613936] usb 3-2: usbfs: USBDEVFS_CONTROL failed cmd udev-configure- rqt 161 rq 0 len 1024 ret -110
[   51.621279] usb 3-2: usbfs: USBDEVFS_CONTROL failed cmd udev-configure- rqt 161 rq 0 len 1024 ret -110
[   56.621643] usb 3-2: usbfs: USBDEVFS_CONTROL failed cmd udev-configure- rqt 161 rq 0 len 1024 ret -110
[45557.191378] r8169 0000:03:00.0: eth0: link down
[45560.216547] r8169 0000:03:00.0: eth0: link up
```

---

### Post by afrodeity on 2012-09-07
I've tried /dev/sg1 /dev/sg2 and /dev/sg3

but this output:
There is no such device. Please try again.

This link has some info on jazip, but nothing on tackling usb interfaces:
[http://structbio.vanderbilt.edu/~jsmith/jazip/](http://structbio.vanderbilt.edu/~jsmith/jazip/)

---

