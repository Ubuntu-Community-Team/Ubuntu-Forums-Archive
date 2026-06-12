---
title: "Ubuntu 11.04 now hangs on Acer Aspire Revo 3700"
date: 2011-05-26
forum: General Help
---

### Post by mmcmonster on 2011-05-26
Hi.
  My Acer Aspire Revo 3700 installed fine.  I did the commands on [this page]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/541620/comments/103") to prevent the system from hanging on shutdown and reboot, and it went fine.

  Against my better judgement, I allowed the system to install a new nvidia driver a couple days ago.  Some other stuff was updated as well, so I don't know where to pin the problem.

The Problem:  Now, when I shutdown or reboot the system, the system hangs with the Ubuntu logo on screen.

Any idea how to troubleshoot this?

Copy of my dmesg:
```
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.38-8-generic (buildd@vernadsky) (gcc version 4.5.2 (Ubuntu/Linaro 4.5.2-8ubuntu3) ) #42-Ubuntu SMP Mon Apr 11 03:31:50 UTC 2011 (Ubuntu 2.6.38-8.42-generic 2.6.38.2)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009e000 (usable)
[    0.000000]  BIOS-e820: 000000000009e000 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000007ff90000 (usable)
[    0.000000]  BIOS-e820: 000000007ff90000 - 000000007ff9e000 (ACPI data)
[    0.000000]  BIOS-e820: 000000007ff9e000 - 000000007ffe0000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000007ffe0000 - 0000000080000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000ffb00000 - 0000000100000000 (reserved)
[    0.000000] Notice: NX (Execute Disable) protection cannot be enabled in hardware: non-PAE kernel!
[    0.000000] NX (Execute Disable) protection: approximated by x86 segment limits
[    0.000000] DMI present.
[    0.000000] DMI: Acer Aspire R3700/TDPS05 R3700, BIOS P01-A1 07/12/2010
[    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
[    0.000000] e820 remove range: 00000000000a0000 - 0000000000100000 (usable)
[    0.000000] last_pfn = 0x7ff90 max_arch_pfn = 0x100000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-CFFFF write-protect
[    0.000000]   D0000-DFFFF uncachable
[    0.000000]   E0000-EFFFF write-through
[    0.000000]   F0000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000 mask F80000000 write-back
[    0.000000]   1 disabled
[    0.000000]   2 disabled
[    0.000000]   3 disabled
[    0.000000]   4 disabled
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] found SMP MP-table at [c00ff780] ff780
[    0.000000] initial memory mapped : 0 - 01c00000
[    0.000000] init_memory_mapping: 0000000000000000-00000000377fe000
[    0.000000]  0000000000 - 0000400000 page 4k
[    0.000000]  0000400000 - 0037400000 page 2M
[    0.000000]  0037400000 - 00377fe000 page 4k
[    0.000000] kernel direct mapping tables up to 377fe000 @ 1bfb000-1c00000
[    0.000000] RAMDISK: 3677c000 - 373b6000
[    0.000000] ACPI: RSDP 000fab60 00024 (v02 ACPIAM)
[    0.000000] ACPI: XSDT 7ff90100 00064 (v01 ACRSYS ACRPRDCT 20100712 MSFT 00000097)
[    0.000000] ACPI: FACP 7ff90290 000F4 (v04 071210 FACP1356 20100712 MSFT 00000097)
[    0.000000] ACPI: DSDT 7ff905c0 05A17 (v02  A42A1 A42A1012 00000012 INTL 20051117)
[    0.000000] ACPI: FACS 7ff9e000 00040
[    0.000000] ACPI: APIC 7ff90390 0006C (v02 071210 APIC1356 20100712 MSFT 00000097)
[    0.000000] ACPI: MCFG 7ff90400 0003C (v01 071210 OEMMCFG  20100712 MSFT 00000097)
[    0.000000] ACPI: SLIC 7ff90440 00176 (v01 ACRSYS ACRPRDCT 20100712 MSFT 00000097)
[    0.000000] ACPI: OEMB 7ff9e040 00072 (v01 071210 OEMB1356 20100712 MSFT 00000097)
[    0.000000] ACPI: HPET 7ff9a5c0 00038 (v01 071210 OEMHPET  20100712 MSFT 00000097)
[    0.000000] ACPI: ASF! 7ff9a600 00099 (v32 ACRSYS I865PASF 00000001 INTL 20051117)
[    0.000000] ACPI: AWMI 7ff9e0c0 00236 (v01 071210 OEMB1356 20100712 MSFT 00000097)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] 1159MB HIGHMEM available.
[    0.000000] 887MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 377fe000
[    0.000000]   low ram: 0 - 377fe000
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000010 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x000377fe
[    0.000000]   HighMem  0x000377fe -> 0x0007ff90
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[2] active PFN ranges
[    0.000000]     0: 0x00000010 -> 0x0000009e
[    0.000000]     0: 0x00000100 -> 0x0007ff90
[    0.000000] On node 0 totalpages: 524062
[    0.000000] free_area_init_node: node 0, pgdat c1784100, node_mem_map f577c200
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3950 pages, LIFO batch:0
[    0.000000]   Normal zone: 1744 pages used for memmap
[    0.000000]   Normal zone: 221486 pages, LIFO batch:31
[    0.000000]   HighMem zone: 2320 pages used for memmap
[    0.000000]   HighMem zone: 294530 pages, LIFO batch:31
[    0.000000] Using APIC driver default
[    0.000000] ACPI: PM-Timer IO Port: 0x808
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x02] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x03] enabled)
[    0.000000] ACPI: IOAPIC (id[0x04] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 4, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000
[    0.000000] SMP: Allowing 4 CPUs, 0 hotplug CPUs
[    0.000000] nr_irqs_gsi: 40
[    0.000000] PM: Registered nosave memory: 000000000009e000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
[    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 80000000 (gap: 80000000:7ee00000)
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] setup_percpu: NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:4 nr_node_ids:1
[    0.000000] PERCPU: Embedded 13 pages/cpu @f5000000 s28800 r0 d24448 u1048576
[    0.000000] pcpu-alloc: s28800 r0 d24448 u1048576 alloc=1*4194304
[    0.000000] pcpu-alloc: [0] 0 1 2 3 
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 519966
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.38-8-generic root=UUID=e3b5ec72-4d8b-47cf-ae82-1963292272e9 ro quiet splash vt.handoff=7
[    0.000000] PID hash table entries: 4096 (order: 2, 16384 bytes)
[    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.000000] Initializing CPU#0
[    0.000000] allocated 10483200 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] Initializing HighMem for node 0 (000377fe:0007ff90)
[    0.000000] Memory: 2046684k/2096704k available (5188k kernel code, 49564k reserved, 2540k data, 700k init, 1187400k highmem)
[    0.000000] virtual kernel memory layout:
[    0.000000]     fixmap  : 0xfff16000 - 0xfffff000   ( 932 kB)
[    0.000000]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[    0.000000]     vmalloc : 0xf7ffe000 - 0xff7fe000   ( 120 MB)
[    0.000000]     lowmem  : 0xc0000000 - 0xf77fe000   ( 887 MB)
[    0.000000]       .init : 0xc178d000 - 0xc183c000   ( 700 kB)
[    0.000000]       .data : 0xc15112a1 - 0xc178c480   (2540 kB)
[    0.000000]       .text : 0xc1000000 - 0xc15112a1   (5188 kB)
[    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.000000] SLUB: Genslabs=15, HWalign=64, Order=0-3, MinObjects=0, CPUs=4, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000]     RCU dyntick-idle grace-period acceleration is enabled.
[    0.000000]     RCU-based detection of stalled CPUs is disabled.
[    0.000000] NR_IRQS:2304 nr_irqs:712 16
[    0.000000] CPU 0 irqstacks, hard=f4008000 soft=f400a000
[    0.000000] Extended CMOS year: 2000
[    0.000000] vt handoff: transparent VT on vt#7
[    0.000000] Console: colour dummy device 80x25
[    0.000000] console [tty0] enabled
[    0.000000] hpet clockevent registered
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 1795.194 MHz processor.
[    0.004005] Calibrating delay loop (skipped), value calculated using timer frequency.. 3590.38 BogoMIPS (lpj=7180776)
[    0.004016] pid_max: default: 32768 minimum: 301
[    0.004065] Security Framework initialized
[    0.004096] AppArmor: AppArmor initialized
[    0.004100] Yama: becoming mindful.
[    0.004212] Mount-cache hash table entries: 512
[    0.004455] Initializing cgroup subsys ns
[    0.004463] ns_cgroup deprecated: consider using the 'clone_children' flag without the ns_cgroup.
[    0.004470] Initializing cgroup subsys cpuacct
[    0.004481] Initializing cgroup subsys memory
[    0.004498] Initializing cgroup subsys devices
[    0.004504] Initializing cgroup subsys freezer
[    0.004509] Initializing cgroup subsys net_cls
[    0.004514] Initializing cgroup subsys blkio
[    0.004575] CPU: Physical Processor ID: 0
[    0.004580] CPU: Processor Core ID: 0
[    0.004585] mce: CPU supports 5 MCE banks
[    0.004598] CPU0: Thermal monitoring enabled (TM1)
[    0.004606] using mwait in idle threads.
[    0.010588] ACPI: Core revision 20110112
[    0.020030] ftrace: allocating 23640 entries in 47 pages
[    0.024090] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.024415] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.067273] CPU0: Intel(R) Atom(TM) CPU D525   @ 1.80GHz stepping 0a
[    0.068003] Performance Events: PEBS fmt0+, Atom events, Intel PMU driver.
[    0.068003] ... version:                3
[    0.068003] ... bit width:              40
[    0.068003] ... generic registers:      2
[    0.068003] ... value mask:             000000ffffffffff
[    0.068003] ... max period:             000000007fffffff
[    0.068003] ... fixed-purpose events:   3
[    0.068003] ... event mask:             0000000700000003
[    0.068003] CPU 1 irqstacks, hard=f40b2000 soft=f40b4000
[    0.068003] Booting Node   0, Processors  #1
[    0.008000] Initializing CPU#1
[    0.156183] CPU 2 irqstacks, hard=f40dc000 soft=f40de000
[    0.156192]  #2
[    0.008000] Initializing CPU#2
[    0.248217] CPU 3 irqstacks, hard=f40e8000 soft=f40ea000
[    0.248228]  #3 Ok.
[    0.008000] Initializing CPU#3
[    0.340039] Brought up 4 CPUs
[    0.340045] Total of 4 processors activated (14363.35 BogoMIPS).
[    0.341636] devtmpfs: initialized
[    0.345165] print_constraints: dummy: 
[    0.345200] Time: 16:33:58  Date: 05/26/11
[    0.345278] NET: Registered protocol family 16
[    0.345300] Trying to unpack rootfs image as initramfs...
[    0.345580] EISA bus registered
[    0.345605] ACPI: bus type pci registered
[    0.345788] PCI: MMCONFIG for domain 0000 [bus 00-ff] at [mem 0xe0000000-0xefffffff] (base 0xe0000000)
[    0.345798] PCI: not using MMCONFIG
[    0.346014] PCI: PCI BIOS revision 3.00 entry at 0xf0031, last bus=4
[    0.346020] PCI: Using configuration type 1 for base access
[    0.348903] bio: create slab <bio-0> at 0
[    0.352858] ACPI: EC: Look up EC in DSDT
[    0.357556] ACPI: Executed 1 blocks of module-level executable AML code
[    0.365609] ACPI: Interpreter enabled
[    0.365621] ACPI: (supports S0 S3 S4 S5)
[    0.365678] ACPI: Using IOAPIC for interrupt routing
[    0.365756] PCI: MMCONFIG for domain 0000 [bus 00-ff] at [mem 0xe0000000-0xefffffff] (base 0xe0000000)
[    0.371256] PCI: MMCONFIG at [mem 0xe0000000-0xefffffff] reserved in ACPI motherboard resources
[    0.371266] PCI: Using MMCONFIG for extended config space
[    0.387645] ACPI: No dock devices found.
[    0.387655] HEST: Table not found.
[    0.387666] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
[    0.388417] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-ff])
[    0.389071] pci_root PNP0A08:00: host bridge window [io  0x0000-0x0cf7]
[    0.389082] pci_root PNP0A08:00: host bridge window [io  0x0d00-0xffff]
[    0.389091] pci_root PNP0A08:00: host bridge window [mem 0x000a0000-0x000bffff]
[    0.389101] pci_root PNP0A08:00: host bridge window [mem 0x000d0000-0x000dffff]
[    0.389110] pci_root PNP0A08:00: host bridge window [mem 0x80000000-0xdfffffff]
[    0.389119] pci_root PNP0A08:00: host bridge window [mem 0xf0000000-0xfed8ffff]
[    0.389151] pci 0000:00:00.0: [8086:a000] type 0 class 0x000600
[    0.389256] pci 0000:00:1b.0: [8086:27d8] type 0 class 0x000403
[    0.389282] pci 0000:00:1b.0: reg 10: [mem 0xfeafc000-0xfeafffff 64bit]
[    0.389354] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    0.389364] pci 0000:00:1b.0: PME# disabled
[    0.389396] pci 0000:00:1c.0: [8086:27d0] type 1 class 0x000604
[    0.389468] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    0.389478] pci 0000:00:1c.0: PME# disabled
[    0.389513] pci 0000:00:1c.2: [8086:27d4] type 1 class 0x000604
[    0.389585] pci 0000:00:1c.2: PME# supported from D0 D3hot D3cold
[    0.389594] pci 0000:00:1c.2: PME# disabled
[    0.389628] pci 0000:00:1c.3: [8086:27d6] type 1 class 0x000604
[    0.389705] pci 0000:00:1c.3: PME# supported from D0 D3hot D3cold
[    0.389716] pci 0000:00:1c.3: PME# disabled
[    0.389755] pci 0000:00:1d.0: [8086:27c8] type 0 class 0x000c03
[    0.389812] pci 0000:00:1d.0: reg 20: [io  0xcc00-0xcc1f]
[    0.389861] pci 0000:00:1d.1: [8086:27c9] type 0 class 0x000c03
[    0.389914] pci 0000:00:1d.1: reg 20: [io  0xc880-0xc89f]
[    0.389959] pci 0000:00:1d.2: [8086:27ca] type 0 class 0x000c03
[    0.390011] pci 0000:00:1d.2: reg 20: [io  0xc800-0xc81f]
[    0.390056] pci 0000:00:1d.3: [8086:27cb] type 0 class 0x000c03
[    0.390108] pci 0000:00:1d.3: reg 20: [io  0xc480-0xc49f]
[    0.390163] pci 0000:00:1d.7: [8086:27cc] type 0 class 0x000c03
[    0.390191] pci 0000:00:1d.7: reg 10: [mem 0xfeafbc00-0xfeafbfff]
[    0.390276] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
[    0.390286] pci 0000:00:1d.7: PME# disabled
[    0.390315] pci 0000:00:1e.0: [8086:2448] type 1 class 0x000604
[    0.390399] pci 0000:00:1f.0: [8086:27bc] type 0 class 0x000601
[    0.390496] pci 0000:00:1f.0: [Firmware Bug]: TigerPoint LPC.BM_STS cleared
[    0.390550] pci 0000:00:1f.2: [8086:27c1] type 0 class 0x000106
[    0.390577] pci 0000:00:1f.2: reg 10: [io  0xb880-0xb887]
[    0.390592] pci 0000:00:1f.2: reg 14: [io  0xc400-0xc403]
[    0.390607] pci 0000:00:1f.2: reg 18: [io  0xc080-0xc087]
[    0.390622] pci 0000:00:1f.2: reg 1c: [io  0xc000-0xc003]
[    0.390637] pci 0000:00:1f.2: reg 20: [io  0xbc00-0xbc1f]
[    0.390652] pci 0000:00:1f.2: reg 24: [mem 0xfeafb800-0xfeafbbff]
[    0.390694] pci 0000:00:1f.2: PME# supported from D3hot
[    0.390704] pci 0000:00:1f.2: PME# disabled
[    0.390738] pci 0000:00:1f.3: [8086:27da] type 0 class 0x000c05
[    0.390801] pci 0000:00:1f.3: reg 20: [io  0x0400-0x041f]
[    0.390914] pci 0000:01:00.0: [10de:0a64] type 0 class 0x000300
[    0.390940] pci 0000:01:00.0: reg 10: [mem 0xfd000000-0xfdffffff]
[    0.390966] pci 0000:01:00.0: reg 14: [mem 0xd0000000-0xdfffffff 64bit pref]
[    0.390994] pci 0000:01:00.0: reg 1c: [mem 0xce000000-0xcfffffff 64bit pref]
[    0.391014] pci 0000:01:00.0: reg 24: [io  0xdc00-0xdc7f]
[    0.391035] pci 0000:01:00.0: reg 30: [mem 0xfcf80000-0xfcffffff pref]
[    0.391134] pci 0000:01:00.1: [10de:0be3] type 0 class 0x000403
[    0.391161] pci 0000:01:00.1: reg 10: [mem 0xfcf7c000-0xfcf7ffff]
[    0.396087] pci 0000:00:1c.0: PCI bridge to [bus 01-01]
[    0.396102] pci 0000:00:1c.0:   bridge window [io  0xd000-0xdfff]
[    0.396113] pci 0000:00:1c.0:   bridge window [mem 0xfcf00000-0xfdffffff]
[    0.396127] pci 0000:00:1c.0:   bridge window [mem 0xce000000-0xdfffffff 64bit pref]
[    0.396212] pci 0000:02:00.0: [1814:3090] type 0 class 0x000280
[    0.396240] pci 0000:02:00.0: reg 10: [mem 0xfebf0000-0xfebfffff]
[    0.404088] pci 0000:00:1c.2: PCI bridge to [bus 02-02]
[    0.404102] pci 0000:00:1c.2:   bridge window [io  0xf000-0x0000] (disabled)
[    0.404115] pci 0000:00:1c.2:   bridge window [mem 0xfeb00000-0xfebfffff]
[    0.404129] pci 0000:00:1c.2:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    0.404216] pci 0000:03:00.0: [10ec:8168] type 0 class 0x000200
[    0.404245] pci 0000:03:00.0: reg 10: [io  0xe800-0xe8ff]
[    0.404283] pci 0000:03:00.0: reg 18: [mem 0xfbffb000-0xfbffbfff 64bit pref]
[    0.404310] pci 0000:03:00.0: reg 20: [mem 0xfbffc000-0xfbffffff 64bit pref]
[    0.404377] pci 0000:03:00.0: supports D1 D2
[    0.404384] pci 0000:03:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.404395] pci 0000:03:00.0: PME# disabled
[    0.412083] pci 0000:00:1c.3: PCI bridge to [bus 03-03]
[    0.412098] pci 0000:00:1c.3:   bridge window [io  0xe000-0xefff]
[    0.412109] pci 0000:00:1c.3:   bridge window [mem 0xfff00000-0x000fffff] (disabled)
[    0.412123] pci 0000:00:1c.3:   bridge window [mem 0xfbf00000-0xfbffffff 64bit pref]
[    0.412221] pci 0000:00:1e.0: PCI bridge to [bus 04-04] (subtractive decode)
[    0.412233] pci 0000:00:1e.0:   bridge window [io  0xf000-0x0000] (disabled)
[    0.412243] pci 0000:00:1e.0:   bridge window [mem 0xfff00000-0x000fffff] (disabled)
[    0.412256] pci 0000:00:1e.0:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    0.412266] pci 0000:00:1e.0:   bridge window [io  0x0000-0x0cf7] (subtractive decode)
[    0.412274] pci 0000:00:1e.0:   bridge window [io  0x0d00-0xffff] (subtractive decode)
[    0.412283] pci 0000:00:1e.0:   bridge window [mem 0x000a0000-0x000bffff] (subtractive decode)
[    0.412293] pci 0000:00:1e.0:   bridge window [mem 0x000d0000-0x000dffff] (subtractive decode)
[    0.412302] pci 0000:00:1e.0:   bridge window [mem 0x80000000-0xdfffffff] (subtractive decode)
[    0.412311] pci 0000:00:1e.0:   bridge window [mem 0xf0000000-0xfed8ffff] (subtractive decode)
[    0.412341] pci_bus 0000:00: on NUMA node 0
[    0.412355] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.412611] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P1._PRT]
[    0.412774] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P4._PRT]
[    0.412895] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P6._PRT]
[    0.413008] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P7._PRT]
[    0.414807]  pci0000:00: Requesting ACPI _OSC control (0x1d)
[    0.415518]  pci0000:00: ACPI _OSC control (0x1d) granted
[    0.432572] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 7 *10 11 12 14 15)
[    0.432743] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 7 10 11 12 *14 15)
[    0.432897] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 7 10 *11 12 14 15)
[    0.433051] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 *5 7 10 11 12 14 15)
[    0.433205] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 7 10 11 12 14 15) *0, disabled.
[    0.433376] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 7 10 11 12 14 15) *0, disabled.
[    0.433555] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 7 10 11 12 14 15) *0, disabled.
[    0.433726] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 7 10 11 12 14 *15)
[    0.434044] vgaarb: device added: PCI:0000:01:00.0,decodes=io+mem,owns=io+mem,locks=none
[    0.434057] vgaarb: loaded
[    0.434669] SCSI subsystem initialized
[    0.434803] libata version 3.00 loaded.
[    0.434939] usbcore: registered new interface driver usbfs
[    0.434979] usbcore: registered new interface driver hub
[    0.435049] usbcore: registered new device driver usb
[    0.435647] wmi: Mapper loaded
[    0.435653] PCI: Using ACPI for IRQ routing
[    0.435664] PCI: pci_cache_line_size set to 64 bytes
[    0.435786] reserve RAM buffer: 000000000009e000 - 000000000009ffff 
[    0.435794] reserve RAM buffer: 000000007ff90000 - 000000007fffffff 
[    0.436104] NetLabel: Initializing
[    0.436111] NetLabel:  domain hash size = 128
[    0.436116] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.436144] NetLabel:  unlabeled traffic allowed by default
[    0.436257] HPET: 3 timers in total, 0 timers will be used for per-cpu timer
[    0.436268] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[    0.436282] hpet0: 3 comparators, 64-bit 14.318180 MHz counter
[    0.448092] Switching to clocksource hpet
[    0.451386] Switched to NOHz mode on CPU #0
[    0.451431] Switched to NOHz mode on CPU #2
[    0.451488] Switched to NOHz mode on CPU #1
[    0.451493] Switched to NOHz mode on CPU #3
[    0.468845] AppArmor: AppArmor Filesystem Enabled
[    0.468907] pnp: PnP ACPI init
[    0.468959] ACPI: bus type pnp registered
[    0.469307] pnp 00:00: [bus 00-ff]
[    0.469316] pnp 00:00: [io  0x0cf8-0x0cff]
[    0.469324] pnp 00:00: [io  0x0000-0x0cf7 window]
[    0.469332] pnp 00:00: [io  0x0d00-0xffff window]
[    0.469340] pnp 00:00: [mem 0x000a0000-0x000bffff window]
[    0.469348] pnp 00:00: [mem 0x000d0000-0x000dffff window]
[    0.469356] pnp 00:00: [mem 0x80000000-0xdfffffff window]
[    0.469364] pnp 00:00: [mem 0xf0000000-0xfed8ffff window]
[    0.469519] pnp 00:00: Plug and Play ACPI device, IDs PNP0a08 PNP0a03 (active)
[    0.469561] pnp 00:01: [mem 0xfed14000-0xfed19fff]
[    0.469570] pnp 00:01: [mem 0xfed90000-0xfed93fff]
[    0.469695] system 00:01: [mem 0xfed14000-0xfed19fff] has been reserved
[    0.469705] system 00:01: [mem 0xfed90000-0xfed93fff] has been reserved
[    0.469716] system 00:01: Plug and Play ACPI device, IDs PNP0c01 (active)
[    0.469818] pnp 00:02: [dma 4]
[    0.469826] pnp 00:02: [io  0x0000-0x000f]
[    0.469833] pnp 00:02: [io  0x0081-0x0083]
[    0.469839] pnp 00:02: [io  0x0087]
[    0.469846] pnp 00:02: [io  0x0089-0x008b]
[    0.469852] pnp 00:02: [io  0x008f]
[    0.469859] pnp 00:02: [io  0x00c0-0x00df]
[    0.469942] pnp 00:02: Plug and Play ACPI device, IDs PNP0200 (active)
[    0.469985] pnp 00:03: [io  0x0070-0x0071]
[    0.470007] pnp 00:03: [irq 8]
[    0.470102] pnp 00:03: Plug and Play ACPI device, IDs PNP0b00 (active)
[    0.470262] pnp 00:04: [io  0x0061]
[    0.470350] pnp 00:04: Plug and Play ACPI device, IDs PNP0800 (active)
[    0.470383] pnp 00:05: [io  0x00f0-0x00ff]
[    0.470400] pnp 00:05: [irq 13]
[    0.470487] pnp 00:05: Plug and Play ACPI device, IDs PNP0c04 (active)
[    0.471868] pnp 00:06: [io  0x0000-0xffffffff disabled]
[    0.471878] pnp 00:06: [io  0x0a00-0x0a0f]
[    0.471886] pnp 00:06: [io  0x0a10-0x0a1f]
[    0.471892] pnp 00:06: [io  0x0a20-0x0a2f]
[    0.471899] pnp 00:06: [io  0x0a30-0x0a3f]
[    0.472093] system 00:06: [io  0x0a00-0x0a0f] has been reserved
[    0.472103] system 00:06: [io  0x0a10-0x0a1f] has been reserved
[    0.472112] system 00:06: [io  0x0a20-0x0a2f] has been reserved
[    0.472121] system 00:06: [io  0x0a30-0x0a3f] has been reserved
[    0.472132] system 00:06: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.472413] pnp 00:07: [io  0x0010-0x001f]
[    0.472422] pnp 00:07: [io  0x0022-0x003f]
[    0.472429] pnp 00:07: [io  0x0044-0x005f]
[    0.472436] pnp 00:07: [io  0x0062-0x0063]
[    0.472443] pnp 00:07: [io  0x0065-0x006f]
[    0.472451] pnp 00:07: [io  0x0072-0x007f]
[    0.472458] pnp 00:07: [io  0x0080]
[    0.472465] pnp 00:07: [io  0x0084-0x0086]
[    0.472472] pnp 00:07: [io  0x0088]
[    0.472479] pnp 00:07: [io  0x008c-0x008e]
[    0.472487] pnp 00:07: [io  0x0090-0x009f]
[    0.472494] pnp 00:07: [io  0x00a2-0x00bf]
[    0.472501] pnp 00:07: [io  0x00e0-0x00ef]
[    0.472508] pnp 00:07: [io  0x04d0-0x04d1]
[    0.472516] pnp 00:07: [io  0x0800-0x087f]
[    0.472524] pnp 00:07: [io  0x0000-0xffffffff disabled]
[    0.472532] pnp 00:07: [io  0x0480-0x04bf]
[    0.472541] pnp 00:07: [mem 0xfed1c000-0xfed1ffff]
[    0.472548] pnp 00:07: [mem 0xfed20000-0xfed8ffff]
[    0.472735] system 00:07: [io  0x04d0-0x04d1] has been reserved
[    0.472745] system 00:07: [io  0x0800-0x087f] has been reserved
[    0.472754] system 00:07: [io  0x0480-0x04bf] has been reserved
[    0.472765] system 00:07: [mem 0xfed1c000-0xfed1ffff] has been reserved
[    0.472774] system 00:07: [mem 0xfed20000-0xfed8ffff] has been reserved
[    0.472785] system 00:07: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.472996] pnp 00:08: [mem 0xfed00000-0xfed003ff]
[    0.473089] pnp 00:08: Plug and Play ACPI device, IDs PNP0103 (active)
[    0.473271] pnp 00:09: [mem 0xffb00000-0xffbfffff]
[    0.473281] pnp 00:09: [mem 0xfff00000-0xffffffff]
[    0.473390] pnp 00:09: Plug and Play ACPI device, IDs INT0800 (active)
[    0.473541] pnp 00:0a: [mem 0xffc00000-0xffefffff]
[    0.473677] system 00:0a: [mem 0xffc00000-0xffefffff] has been reserved
[    0.473688] system 00:0a: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.473979] pnp 00:0b: [io  0x0060]
[    0.473987] pnp 00:0b: [io  0x0064]
[    0.473994] pnp 00:0b: [mem 0xfec00000-0xfec00fff]
[    0.474002] pnp 00:0b: [mem 0xfee00000-0xfee00fff]
[    0.474139] system 00:0b: [mem 0xfec00000-0xfec00fff] could not be reserved
[    0.474149] system 00:0b: [mem 0xfee00000-0xfee00fff] has been reserved
[    0.474160] system 00:0b: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.474326] pnp 00:0c: [mem 0xe0000000-0xefffffff]
[    0.474467] system 00:0c: [mem 0xe0000000-0xefffffff] has been reserved
[    0.474478] system 00:0c: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.475099] pnp 00:0d: [mem 0x00000000-0x0009ffff]
[    0.475109] pnp 00:0d: [mem 0x000c0000-0x000cffff]
[    0.475117] pnp 00:0d: [mem 0x000e0000-0x000fffff]
[    0.475125] pnp 00:0d: [mem 0x00100000-0x7fffffff]
[    0.475132] pnp 00:0d: [mem 0xfed90000-0xffffffff]
[    0.475307] system 00:0d: [mem 0x00000000-0x0009ffff] could not be reserved
[    0.475318] system 00:0d: [mem 0x000c0000-0x000cffff] could not be reserved
[    0.475328] system 00:0d: [mem 0x000e0000-0x000fffff] could not be reserved
[    0.475337] system 00:0d: [mem 0x00100000-0x7fffffff] could not be reserved
[    0.475347] system 00:0d: [mem 0xfed90000-0xffffffff] could not be reserved
[    0.475358] system 00:0d: Plug and Play ACPI device, IDs PNP0c01 (active)
[    0.475805] pnp: PnP ACPI: found 14 devices
[    0.475812] ACPI: ACPI bus type pnp unregistered
[    0.475821] PnPBIOS: Disabled by ACPI PNP
[    0.516583] pci 0000:00:1c.2: BAR 15: assigned [mem 0x80000000-0x801fffff 64bit pref]
[    0.516598] pci 0000:00:1c.3: BAR 14: assigned [mem 0x80200000-0x805fffff]
[    0.516610] pci 0000:00:1c.2: BAR 13: assigned [io  0x1000-0x1fff]
[    0.516619] pci 0000:00:1c.0: PCI bridge to [bus 01-01]
[    0.516628] pci 0000:00:1c.0:   bridge window [io  0xd000-0xdfff]
[    0.516639] pci 0000:00:1c.0:   bridge window [mem 0xfcf00000-0xfdffffff]
[    0.516650] pci 0000:00:1c.0:   bridge window [mem 0xce000000-0xdfffffff 64bit pref]
[    0.516663] pci 0000:00:1c.2: PCI bridge to [bus 02-02]
[    0.516671] pci 0000:00:1c.2:   bridge window [io  0x1000-0x1fff]
[    0.516682] pci 0000:00:1c.2:   bridge window [mem 0xfeb00000-0xfebfffff]
[    0.516693] pci 0000:00:1c.2:   bridge window [mem 0x80000000-0x801fffff 64bit pref]
[    0.516705] pci 0000:00:1c.3: PCI bridge to [bus 03-03]
[    0.516714] pci 0000:00:1c.3:   bridge window [io  0xe000-0xefff]
[    0.516724] pci 0000:00:1c.3:   bridge window [mem 0x80200000-0x805fffff]
[    0.516735] pci 0000:00:1c.3:   bridge window [mem 0xfbf00000-0xfbffffff 64bit pref]
[    0.516747] pci 0000:00:1e.0: PCI bridge to [bus 04-04]
[    0.516754] pci 0000:00:1e.0:   bridge window [io  disabled]
[    0.516763] pci 0000:00:1e.0:   bridge window [mem disabled]
[    0.516772] pci 0000:00:1e.0:   bridge window [mem pref disabled]
[    0.516818] pci 0000:00:1c.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.516830] pci 0000:00:1c.0: setting latency timer to 64
[    0.516843] pci 0000:00:1c.2: enabling device (0106 -> 0107)
[    0.516865] pci 0000:00:1c.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.516875] pci 0000:00:1c.2: setting latency timer to 64
[    0.516906] pci 0000:00:1c.3: PCI INT D -> GSI 19 (level, low) -> IRQ 19
[    0.516917] pci 0000:00:1c.3: setting latency timer to 64
[    0.516931] pci 0000:00:1e.0: setting latency timer to 64
[    0.516941] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
[    0.516949] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff]
[    0.516957] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
[    0.516965] pci_bus 0000:00: resource 7 [mem 0x000d0000-0x000dffff]
[    0.516974] pci_bus 0000:00: resource 8 [mem 0x80000000-0xdfffffff]
[    0.516982] pci_bus 0000:00: resource 9 [mem 0xf0000000-0xfed8ffff]
[    0.516991] pci_bus 0000:01: resource 0 [io  0xd000-0xdfff]
[    0.516999] pci_bus 0000:01: resource 1 [mem 0xfcf00000-0xfdffffff]
[    0.517007] pci_bus 0000:01: resource 2 [mem 0xce000000-0xdfffffff 64bit pref]
[    0.517016] pci_bus 0000:02: resource 0 [io  0x1000-0x1fff]
[    0.517024] pci_bus 0000:02: resource 1 [mem 0xfeb00000-0xfebfffff]
[    0.517032] pci_bus 0000:02: resource 2 [mem 0x80000000-0x801fffff 64bit pref]
[    0.517041] pci_bus 0000:03: resource 0 [io  0xe000-0xefff]
[    0.517049] pci_bus 0000:03: resource 1 [mem 0x80200000-0x805fffff]
[    0.517057] pci_bus 0000:03: resource 2 [mem 0xfbf00000-0xfbffffff 64bit pref]
[    0.517066] pci_bus 0000:04: resource 4 [io  0x0000-0x0cf7]
[    0.517074] pci_bus 0000:04: resource 5 [io  0x0d00-0xffff]
[    0.517082] pci_bus 0000:04: resource 6 [mem 0x000a0000-0x000bffff]
[    0.517090] pci_bus 0000:04: resource 7 [mem 0x000d0000-0x000dffff]
[    0.517099] pci_bus 0000:04: resource 8 [mem 0x80000000-0xdfffffff]
[    0.517107] pci_bus 0000:04: resource 9 [mem 0xf0000000-0xfed8ffff]
[    0.517189] NET: Registered protocol family 2
[    0.517384] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.517955] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.518951] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.519450] TCP: Hash tables configured (established 131072 bind 65536)
[    0.519459] TCP reno registered
[    0.519471] UDP hash table entries: 512 (order: 2, 16384 bytes)
[    0.519493] UDP-Lite hash table entries: 512 (order: 2, 16384 bytes)
[    0.519765] NET: Registered protocol family 1
[    0.519963] pci 0000:01:00.0: Boot video device
[    0.520034] PCI: CLS 32 bytes, default 64
[    0.520803] cpufreq-nforce2: No nForce2 chipset.
[    0.521164] audit: initializing netlink socket (disabled)
[    0.521187] type=2000 audit(1306427638.516:1): initialized
[    0.543189] highmem bounce pool size: 64 pages
[    0.543205] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    0.548998] VFS: Disk quotas dquot_6.5.2
[    0.549189] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.551431] fuse init (API version 7.16)
[    0.551756] msgmni has been set to 1678
[    0.552503] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.552581] io scheduler noop registered
[    0.552588] io scheduler deadline registered
[    0.552647] io scheduler cfq registered (default)
[    0.552935] pcieport 0000:00:1c.0: setting latency timer to 64
[    0.553006] pcieport 0000:00:1c.0: irq 40 for MSI/MSI-X
[    0.553234] pcieport 0000:00:1c.2: setting latency timer to 64
[    0.553291] pcieport 0000:00:1c.2: irq 41 for MSI/MSI-X
[    0.553518] pcieport 0000:00:1c.3: setting latency timer to 64
[    0.553574] pcieport 0000:00:1c.3: irq 42 for MSI/MSI-X
[    0.553872] pcieport 0000:00:1c.0: Signaling PME through PCIe PME interrupt
[    0.553882] pci 0000:01:00.0: Signaling PME through PCIe PME interrupt
[    0.553889] pci 0000:01:00.1: Signaling PME through PCIe PME interrupt
[    0.553900] pcie_pme 0000:00:1c.0:pcie01: service driver pcie_pme loaded
[    0.553946] pcieport 0000:00:1c.2: Signaling PME through PCIe PME interrupt
[    0.553955] pci 0000:02:00.0: Signaling PME through PCIe PME interrupt
[    0.553965] pcie_pme 0000:00:1c.2:pcie01: service driver pcie_pme loaded
[    0.554009] pcieport 0000:00:1c.3: Signaling PME through PCIe PME interrupt
[    0.554017] pci 0000:03:00.0: Signaling PME through PCIe PME interrupt
[    0.554026] pcie_pme 0000:00:1c.3:pcie01: service driver pcie_pme loaded
[    0.554086] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.554198] pciehp 0000:00:1c.0:pcie04: HPC vendor_id 8086 device_id 27d0 ss_vid 1025 ss_did 47a
[    0.554250] pciehp 0000:00:1c.0:pcie04: service driver pciehp loaded
[    0.554274] pciehp 0000:00:1c.2:pcie04: HPC vendor_id 8086 device_id 27d4 ss_vid 1025 ss_did 47a
[    0.554320] pciehp 0000:00:1c.2:pcie04: service driver pciehp loaded
[    0.554344] pciehp 0000:00:1c.3:pcie04: HPC vendor_id 8086 device_id 27d6 ss_vid 1025 ss_did 47a
[    0.554390] pciehp 0000:00:1c.3:pcie04: service driver pciehp loaded
[    0.554413] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.554587] intel_idle: MWAIT substates: 0x10
[    0.554608] intel_idle: v0.4 model 0x1C
[    0.554613] intel_idle: lapic_timer_reliable_states 0x2
[    0.554944] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0
[    0.554958] ACPI: Power Button [PWRB]
[    0.555107] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
[    0.555118] ACPI: Power Button [PWRF]
[    0.555535] ACPI: acpi_idle yielding to intel_idle
[    0.561706] thermal LNXTHERM:00: registered as thermal_zone0
[    0.561716] ACPI: Thermal Zone [THRM] (50 C)
[    0.562188] thermal LNXTHERM:01: registered as thermal_zone1
[    0.562196] ACPI: Thermal Zone [THRS] (49 C)
[    0.562344] ERST: Table is not found!
[    0.562549] isapnp: Scanning for PnP cards...
[    0.562563] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    0.900786] Freeing initrd memory: 12520k freed
[    0.915848] isapnp: No Plug & Play device found
[    0.947960] Linux agpgart interface v0.103
[    0.951024] brd: module loaded
[    0.952401] loop: module loaded
[    0.952608] i2c-core: driver [adp5520] using legacy suspend method
[    0.952614] i2c-core: driver [adp5520] using legacy resume method
[    0.953572] Fixed MDIO Bus: probed
[    0.953660] PPP generic driver version 2.4.2
[    0.953755] tun: Universal TUN/TAP device driver, 1.6
[    0.953760] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.953948] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.954008] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    0.954034] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    0.954042] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    0.954147] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 1
[    0.954245] ehci_hcd 0000:00:1d.7: using broken periodic workaround
[    0.954260] ehci_hcd 0000:00:1d.7: debug port 1
[    0.958134] ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported
[    0.958164] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xfeafbc00
[    0.972023] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    0.972307] hub 1-0:1.0: USB hub found
[    0.972317] hub 1-0:1.0: 8 ports detected
[    0.972484] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.972519] uhci_hcd: USB Universal Host Controller Interface driver
[    0.972585] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    0.972600] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    0.972606] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    0.972702] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    0.972782] uhci_hcd 0000:00:1d.0: irq 23, io base 0x0000cc00
[    0.973064] hub 2-0:1.0: USB hub found
[    0.973074] hub 2-0:1.0: 2 ports detected
[    0.973202] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    0.973213] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    0.973220] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    0.973315] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 3
[    0.973403] uhci_hcd 0000:00:1d.1: irq 19, io base 0x0000c880
[    0.973687] hub 3-0:1.0: USB hub found
[    0.973697] hub 3-0:1.0: 2 ports detected
[    0.973828] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.973840] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    0.973847] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    0.973940] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 4
[    0.976085] uhci_hcd 0000:00:1d.2: irq 18, io base 0x0000c800
[    0.976369] hub 4-0:1.0: USB hub found
[    0.976379] hub 4-0:1.0: 2 ports detected
[    0.976511] uhci_hcd 0000:00:1d.3: PCI INT D -> GSI 16 (level, low) -> IRQ 16
[    0.976522] uhci_hcd 0000:00:1d.3: setting latency timer to 64
[    0.976528] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[    0.976616] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 5
[    0.976699] uhci_hcd 0000:00:1d.3: irq 16, io base 0x0000c480
[    0.976983] hub 5-0:1.0: USB hub found
[    0.976993] hub 5-0:1.0: 2 ports detected
[    0.977257] i8042: PNP: No PS/2 controller found. Probing ports directly.
[    0.977692] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.977706] serio: i8042 AUX port at 0x60,0x64 irq 12
[    0.978080] mousedev: PS/2 mouse device common for all mice
[    0.978383] rtc_cmos 00:03: RTC can wake from S4
[    0.996124] rtc_cmos 00:03: rtc core: registered rtc_cmos as rtc0
[    0.996159] rtc0: alarms up to one month, y3k, 114 bytes nvram, hpet irqs
[    0.996390] device-mapper: uevent: version 1.0.3
[    0.996590] device-mapper: ioctl: 4.19.1-ioctl (2011-01-07) initialised: dm-devel@redhat.com
[    0.996774] device-mapper: multipath: version 1.2.0 loaded
[    0.996780] device-mapper: multipath round-robin: version 1.0.0 loaded
[    0.996974] EISA: Probing bus 0 at eisa.0
[    0.996980] EISA: Cannot allocate resource for mainboard
[    0.996985] Cannot allocate resource for EISA slot 1
[    0.996991] Cannot allocate resource for EISA slot 2
[    0.996996] Cannot allocate resource for EISA slot 3
[    0.997001] Cannot allocate resource for EISA slot 4
[    0.997006] Cannot allocate resource for EISA slot 5
[    0.997011] Cannot allocate resource for EISA slot 6
[    0.997016] Cannot allocate resource for EISA slot 7
[    0.997021] Cannot allocate resource for EISA slot 8
[    0.997025] EISA: Detected 0 cards.
[    0.997304] cpuidle: using governor ladder
[    0.997572] cpuidle: using governor menu
[    0.998159] TCP cubic registered
[    0.998471] NET: Registered protocol family 10
[    0.999618] NET: Registered protocol family 17
[    0.999661] Registering the dns_resolver key type
[    0.999765] Using IPI No-Shortcut mode
[    1.000043] PM: Hibernation image not present or could not be loaded.
[    1.000066] registered taskstats version 1
[    1.000474]   Magic number: 11:673:591
[    1.000592] rtc_cmos 00:03: setting system clock to 2011-05-26 16:33:59 UTC (1306427639)
[    1.000600] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.000603] EDD information not available.
[    1.000790] Freeing unused kernel memory: 700k freed
[    1.001173] Write protecting the kernel text: 5192k
[    1.001254] Write protecting the kernel read-only data: 2148k
[    1.050733] <30>udev[71]: starting version 167
[    1.202212] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    1.202265] r8169 0000:03:00.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    1.202327] r8169 0000:03:00.0: setting latency timer to 64
[    1.202339] r8169 0000:03:00.0: (unregistered net_device): unknown MAC, using family default
[    1.202429] r8169 0000:03:00.0: irq 43 for MSI/MSI-X
[    1.203933] r8169 0000:03:00.0: eth0: RTL8168b/8111b at 0xf8006000, d0:27:88:32:53:d1, XID 0c200000 IRQ 43
[    1.208211] ahci 0000:00:1f.2: version 3.0
[    1.208243] ahci 0000:00:1f.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    1.208334] ahci 0000:00:1f.2: irq 44 for MSI/MSI-X
[    1.208452] ahci 0000:00:1f.2: AHCI 0001.0100 32 slots 4 ports 3 Gbps 0xf impl SATA mode
[    1.208464] ahci 0000:00:1f.2: flags: 64bit ncq pm led clo pio slum part 
[    1.208476] ahci 0000:00:1f.2: setting latency timer to 64
[    1.211032] scsi0 : ahci
[    1.211426] scsi1 : ahci
[    1.211701] scsi2 : ahci
[    1.211977] scsi3 : ahci
[    1.212459] ata1: SATA max UDMA/133 abar m1024@0xfeafb800 port 0xfeafb900 irq 44
[    1.212471] ata2: SATA max UDMA/133 abar m1024@0xfeafb800 port 0xfeafb980 irq 44
[    1.212480] ata3: SATA max UDMA/133 abar m1024@0xfeafb800 port 0xfeafba00 irq 44
[    1.212489] ata4: SATA max UDMA/133 abar m1024@0xfeafb800 port 0xfeafba80 irq 44
[    1.520049] Refined TSC clocksource calibration: 1795.499 MHz.
[    1.520061] Switching to clocksource tsc
[    1.532035] ata3: SATA link down (SStatus 0 SControl 300)
[    1.532070] ata2: SATA link down (SStatus 0 SControl 300)
[    1.532106] ata4: SATA link down (SStatus 0 SControl 300)
[    1.532138] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    1.544785] ata1.00: ATA-8: Hitachi HTS545025B9A300, PB2OC60F, max UDMA/133
[    1.544792] ata1.00: 488397168 sectors, multi 0: LBA48 NCQ (depth 31/32), AA
[    1.546242] ata1.00: configured for UDMA/133
[    1.546479] scsi 0:0:0:0: Direct-Access     ATA      Hitachi HTS54502 PB2O PQ: 0 ANSI: 5
[    1.547028] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    1.547116] sd 0:0:0:0: [sda] 488397168 512-byte logical blocks: (250 GB/232 GiB)
[    1.547354] sd 0:0:0:0: [sda] Write Protect is off
[    1.547364] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.547466] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.583292]  sda: sda1 sda2 < sda5 sda6 >
[    1.584270] sd 0:0:0:0: [sda] Attached SCSI disk
[    1.632035] usb 2-1: new full speed USB device using uhci_hcd and address 2
[    2.068046] usb 4-2: new low speed USB device using uhci_hcd and address 2
[    2.086886] EXT4-fs (sda1): INFO: recovery required on readonly filesystem
[    2.086894] EXT4-fs (sda1): write access will be enabled during recovery
[    2.211461] EXT4-fs (sda1): recovery complete
[    2.211794] EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: (null)
[   11.520186] <30>udev[266]: starting version 167
[   11.565212] Adding 6037500k swap on /dev/sda5.  Priority:-1 extents:1 across:6037500k 
[   11.568890] lp: driver loaded but no devices found
[   11.710252] rt2860sta: module is from the staging directory, the quality is unknown, you have been warned.
[   11.808287] type=1400 audit(1306427650.304:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=420 comm="apparmor_parser"
[   11.809310] type=1400 audit(1306427650.304:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=420 comm="apparmor_parser"
[   11.809965] type=1400 audit(1306427650.304:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=420 comm="apparmor_parser"
[   11.925751] nvidia: module license 'NVIDIA' taints kernel.
[   11.925761] Disabling lock debugging due to kernel taint
[   11.936159] rt2860 0000:02:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[   11.936226] rt2860 0000:02:00.0: setting latency timer to 64
[   11.937156] === pAd = f8de2000, size = 484312 ===
[   11.937165] <-- RTMPAllocAdapterBlock, Status=0
[   11.937172] pAd->CSRBaseAddress =0xf8200000, csr_addr=0xf8200000!
[   11.950171] IR NEC protocol handler initialized
[   11.972522] IR RC5(x) protocol handler initialized
[   11.983616] IR RC6 protocol handler initialized
[   11.999384] IR JVC protocol handler initialized
[   12.009518] Registered IR keymap rc-rc6-mce
[   12.009774] IR Sony protocol handler initialized
[   12.010408] input: Media Center Ed. eHome Infrared Remote Transceiver (1784:0011) as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1:1.0/rc/rc0/input2
[   12.010586] rc0: Media Center Ed. eHome Infrared Remote Transceiver (1784:0011) as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1:1.0/rc/rc0
[   12.016917] mceusb 2-1:1.0: Registered Topseed Technology Corp. eHome Infrared Transceiver on usb2:2
[   12.017089] usbcore: registered new interface driver mceusb
[   12.027187] lirc_dev: IR Remote Control driver registered, major 251 
[   12.036465] rc rc0: lirc_dev: driver ir-lirc-codec (mceusb) registered at minor = 0
[   12.036475] IR LIRC bridge handler initialized
[   12.418127] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   12.418225] HDA Intel 0000:00:1b.0: irq 45 for MSI/MSI-X
[   12.418272] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   12.479845] hda_codec: ALC662 rev1: BIOS auto-probing.
[   12.492540] HDA Intel 0000:01:00.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[   12.492551] hda_intel: Disable MSI for Nvidia chipset
[   12.492631] HDA Intel 0000:01:00.1: setting latency timer to 64
[   15.342197] nvidia 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   15.342214] nvidia 0000:01:00.0: setting latency timer to 64
[   15.342224] vgaarb: device changed decodes: PCI:0000:01:00.0,olddecodes=io+mem,decodes=none:owns=io+mem
[   15.342454] NVRM: loading NVIDIA UNIX x86 Kernel Module  270.41.19  Mon May 16 23:31:36 PDT 2011
[   15.352914] input: Chicony 2.4G Multimedia Wireless Kit as /devices/pci0000:00/0000:00:1d.2/usb4/4-2/4-2:1.0/input/input3
[   15.353817] generic-usb 0003:04F2:0963.0001: input,hidraw0: USB HID v1.11 Keyboard [Chicony 2.4G Multimedia Wireless Kit] on usb-0000:00:1d.2-2/input0
[   15.421433] input: Chicony 2.4G Multimedia Wireless Kit as /devices/pci0000:00/0000:00:1d.2/usb4/4-2/4-2:1.1/input/input4
[   15.422721] generic-usb 0003:04F2:0963.0002: input,hiddev0,hidraw1: USB HID v1.11 Mouse [Chicony 2.4G Multimedia Wireless Kit] on usb-0000:00:1d.2-2/input1
[   15.423734] usbcore: registered new interface driver usbhid
[   15.423744] usbhid: USB HID core driver
[   15.533375] vesafb: framebuffer at 0xcf000000, mapped to 0xf8400000, using 1216k, total 1216k
[   15.533387] vesafb: mode is 640x480x32, linelength=2560, pages=0
[   15.533394] vesafb: scrolling: redraw
[   15.533404] vesafb: Truecolor: size=8:8:8:8, shift=24:16:8:0
[   15.534874] Console: switching to colour frame buffer device 80x30
[   15.534926] fb0: VESA VGA frame buffer device
[   20.621749] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
[   20.761799] EXT4-fs (sda6): mounted filesystem with ordered data mode. Opts: (null)
[   21.304347] ppdev: user-space parallel port driver
[   21.343282] type=1400 audit(1306427659.836:5): apparmor="STATUS" operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" pid=762 comm="apparmor_parser"
[   21.359661] type=1400 audit(1306427659.852:6): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=763 comm="apparmor_parser"
[   21.360767] type=1400 audit(1306427659.856:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=763 comm="apparmor_parser"
[   21.361450] type=1400 audit(1306427659.856:8): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=763 comm="apparmor_parser"
[   21.369523] type=1400 audit(1306427659.864:9): apparmor="STATUS" operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" pid=773 comm="apparmor_parser"
[   21.372730] type=1400 audit(1306427659.868:10): apparmor="STATUS" operation="profile_replace" name="/usr/lib/cups/backend/cups-pdf" pid=776 comm="apparmor_parser"
[   21.374031] type=1400 audit(1306427659.868:11): apparmor="STATUS" operation="profile_load" name="/usr/sbin/cupsd" pid=773 comm="apparmor_parser"
[   21.375368] type=1400 audit(1306427659.868:12): apparmor="STATUS" operation="profile_load" name="/usr/sbin/tcpdump" pid=774 comm="apparmor_parser"
[   21.376932] type=1400 audit(1306427659.872:13): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/cupsd" pid=776 comm="apparmor_parser"
[   21.398091] type=1400 audit(1306427659.892:14): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince" pid=764 comm="apparmor_parser"
[   21.595356] RX DESC f14b8000  size = 2048
[   21.595994] <-- RTMPAllocTxRxRingMemory, Status=0
[   21.598598] 1. Phy Mode = 0
[   21.598607] 2. Phy Mode = 0
[   21.598614] NVM is Efuse and its size =2d[2d0-2fc] 
[   21.599841] 3. Phy Mode = 0
[   21.622582] RTMPSetPhyMode: channel is out of range, use first channel=1 
[   21.622594] MCS Set = 00 00 00 00 00
[   21.638591] <==== rt28xx_init, Status=0
[   21.638664] 0x1300 = 00073200
[   21.638683]  AUX_CTRL = 0x                             c02
[   21.638692]  Read AUX_CTRL = 0xc02
[   21.638698]  Write AUX_CTRL = 0x1c02
[   21.638704]  OSC_CTRL = 0x3ff11
[   21.639204] ====> rt30xx Read PowerLevelMode =  0x3.
[   21.639212] ====> rt30xx F Write 0x83 Command = 0x3.
[   21.671580] RX DESC f14b8000  size = 2048
[   21.672681] <-- RTMPAllocTxRxRingMemory, Status=0
[   21.675229] 1. Phy Mode = 0
[   21.675239] 2. Phy Mode = 0
[   21.675247] NVM is Efuse and its size =2d[2d0-2fc] 
[   21.676611] 3. Phy Mode = 0
[   21.678970] MCS Set = 00 00 00 00 00
[   21.695113] <==== rt28xx_init, Status=0
[   21.695185] 0x1300 = 00073200
[   21.695207]  AUX_CTRL = 0x                            1d42
[   21.695216]  Read AUX_CTRL = 0x1d42
[   21.695222]  Write AUX_CTRL = 0x1d42
[   21.695227]  OSC_CTRL = 0x3ff11
[   21.695965] ====> rt30xx Read PowerLevelMode =  0x3.
[   21.695973] ====> rt30xx F Write 0x83 Command = 0x3.
[   21.713130] r8169 0000:03:00.0: eth0: link down
[   21.713768] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   22.461162] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,commit=0
[   22.564836] EXT4-fs (sda6): re-mounted. Opts: commit=0
[   23.414452] HDMI hot plug event: Pin=5 Presence_Detect=1 ELD_Valid=0
[   23.439161] HDMI hot plug event: Pin=5 Presence_Detect=1 ELD_Valid=1
[   24.228050] HDMI: detected monitor LG TV
[   24.228056]        at connection type HDMI
[   24.228069] HDMI: supports coding type LPCM: channels = 2, rates = 44100 48000 88200, bits = 16 20 24
[   25.004028] HDMI: detected monitor LG TV
[   25.004032]        at connection type HDMI
[   25.004043] HDMI: supports coding type LPCM: channels = 2, rates = 44100 48000 88200, bits = 16 20 24
[   25.112357] HDMI hot plug event: Pin=5 Presence_Detect=1 ELD_Valid=0
[   25.156884] HDMI hot plug event: Pin=5 Presence_Detect=1 ELD_Valid=1
[   25.940077] HDMI: detected monitor LG TV
[   25.940084]        at connection type HDMI
[   25.940099] HDMI: supports coding type LPCM: channels = 2, rates = 44100 48000 88200, bits = 16 20 24
[   26.724080] HDMI: detected monitor LG TV
[   26.724087]        at connection type HDMI
[   26.724102] HDMI: supports coding type LPCM: channels = 2, rates = 44100 48000 88200, bits = 16 20 24
[   27.008210] ===>rt_ioctl_giwscan. 2(2) BSS returned, data->length = 243
[   27.176983] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,commit=0
[   27.665713] EXT4-fs (sda6): re-mounted. Opts: commit=0
[   28.482179] hda-intel: IRQ timing workaround is activated for card #1. Suggest a bigger bdl_pos_adj.
[   32.352015] wlan0: no IPv6 routers present
[   33.422663] ===>rt_ioctl_giwscan. 2(2) BSS returned, data->length = 243
[   33.423442] ==>rt_ioctl_siwfreq::SIOCSIWFREQ[cmd=0x8b04] (Channel=1)
[   35.495768] CIFS: Unknown mount option codepage
[   35.495781] CIFS: Unknown mount option unicode
[   35.520487] CIFS: Unknown mount option codepage
[   35.520499] CIFS: Unknown mount option unicode
[   35.528537] CIFS: Unknown mount option codepage
[   35.528550] CIFS: Unknown mount option unicode
[   35.528583] CIFS: Unknown mount option codepage
[   35.528596] CIFS: Unknown mount option unicode
[   47.536164] ===>rt_ioctl_giwscan. 1(1) BSS returned, data->length = 137
[   87.017557] ===>rt_ioctl_giwscan. 2(2) BSS returned, data->length = 243
[  147.017299] ===>rt_ioctl_giwscan. 2(2) BSS returned, data->length = 243
[  227.013204] ===>rt_ioctl_giwscan. 2(2) BSS returned, data->length = 243
[  327.013687] ===>rt_ioctl_giwscan. 2(2) BSS returned, data->length = 243
[  447.014127] ===>rt_ioctl_giwscan. 2(2) BSS returned, data->length = 243
[  567.011563] ===>rt_ioctl_giwscan. 2(2) BSS returned, data->length = 243
[  687.016279] ===>rt_ioctl_giwscan. 1(1) BSS returned, data->length = 137
[  807.013734] ===>rt_ioctl_giwscan. 2(2) BSS returned, data->length = 243
[  927.012180] ===>rt_ioctl_giwscan. 1(1) BSS returned, data->length = 137
[ 1047.016623] ===>rt_ioctl_giwscan. 1(1) BSS returned, data->length = 137
[ 1167.015410] ===>rt_ioctl_giwscan. 1(1) BSS returned, data->length = 137
[ 1287.016156] ===>rt_ioctl_giwscan. 1(1) BSS returned, data->length = 137
[ 1407.015223] ===>rt_ioctl_giwscan. 2(2) BSS returned, data->length = 243

```

---

### Post by mmcmonster on 2011-05-26
Actually, the system takes a really long time to shutdown or end the shutdown portion of the reboot cycle.  After about 2-3 minutes, the system completes the shutdown or starts rebooting like normal.

So whatever the problem is, it manages to fix itself within a couple minutes.

Any idea how to diagnose the problem?  Or anyone run into this before and have a fix?

---

### Post by mmcmonster on 2011-05-27
(Bump!)

Anyone with any ideas?

Actually, if anyone could tell me how to find the log of the shutdown process, that would be useful.

Google actually doesn't work, as I can't seem to search for log without looking for logging into or out of an account.

---

### Post by mmcmonster on 2011-05-30
(Bump!)

Anyone with ideas?  Surely there must be a way to read the shutdown logs, so at least I can figure out where the problem is...

---

### Post by timgood on 2011-05-30
I have 11.04 working fine on my Revo 3700 so I know it is not a hardware problem. I have also applied the fix shown. Also, all the updates have worked on my machine without a problem. I can only assume it must be something else. Try a re-install?

---

### Post by mmcmonster on 2011-05-31
I would hate to reinstall for no particular reason.

Other than the really long time to shutdown or restart, the system is working perfectly. (Plus, "reinstall to see if that helps" seems like the Microsoft Windows idea of "reboot to see if it helps", rather than the Linux/Unix idea of figuring out what the problem really is.)

I'm interested in figuring out how to troubleshoot this.

Anyone have ideas on how to troubleshoot (or profile) shutdown issues?

---

### Post by mmcmonster on 2011-06-01
Bump!

---

### Post by pnewman on 2011-06-05
Just to say, I have the same problem, on the same setup. Was on 10.10, worked fine, did a clean install of 11.04, now hangs every time on shutdown. Waited 10 minutes before I gave up waiting. Only other hardware attached is a Logitech wireless keyboard an mouse. Using proprietary NVidia driver.

---

### Post by youlikeicecream on 2011-06-16
Same problem here. I have a brand new Aspire Revo R3700.

installed 10.10 : all works fine except for that it hangs as soon as you click restart or shutdown. the machine has completely halted, CTRL+ALT+F1(2,3,4,5,6) does nothing. Kernel Panic I think.

I tried the "modprobe -rf" stuff but the machine hangs when trying to "modprobe rt2860sta".

I installed 10.04 fresh and it all worked except the wireless card would not find any access points. Restart/Shutdown did not hang.

upgraded to 10.10 from the 10.04 installation and immediately it hangs on clicking restart or shutdown.

I am going to try 11.04 and see if that works.

---

### Post by youlikeicecream on 2011-06-16
my Bad, placing "blacklist rt2800pci" at the bottom of /etc/modprobe.d/blacklist.conf  has stopped the machine from hanging on restart (using Ubuntu 11.04). I will now try to go back to 10.10 and see if works too.

---

### Post by TheDrizzle808 on 2011-07-27
Anyone have any luck with this? I tried adding the blacklist but that just caused my wireless to mess up and eventually lock up my system.

---

### Post by TheDrizzle808 on 2011-07-27
> **TheDrizzle808 said:**
> Anyone have any luck with this? I tried adding the blacklist but that just caused my wireless to mess up and eventually lock up my system.

I found a solution that works for me:

> Originally Posted by fabio.hipolito  
Hi,

I'm running Ubuntu 11.04 amd64 on a Dell Optiplex 990, which had the same problem and none of the solutions above worked for me. I found a solution in bug report in launchpad

Just add the option "reboot=pci" to GRUB_CMDLINE_LINUX in /etc/default/grub
to do this
Code:
sudo gedit /etc/default/grub
look for

GRUB_CMDLINE_LINUX=""

and change it to

GRUB_CMDLINE_LINUX="reboot=pci"

save, exit and update grub
Code:
sudo update-grub
Sorry for being bothering a solved thread.
Best regards.

Here's the link to the thread.

[http://ubuntuforums.org/showthread.php?t=1741668&page=7]("http://ubuntuforums.org/showthread.php?t=1741668&page=7")

Hope this helps someone.

---

### Post by VeRychard on 2012-04-17
I SOLVED IT!!!!!

If you have an Asus laptop, or you have this option in BIOS CHECK IT!!!!!

Go to bios >
Security> I / O interface Security> [COLOR=red]"New interface card"[/COLOR] or so. SET IT TO LOCKED!!! 

After that everything went fine for me ^^

Booted properly

Hope it helps :)

---

