---
title: "computer just started crashing!"
date: 2012-04-16
forum: General Help
---

### Post by cybergalvez on 2012-04-16
Hi all, I am trying to do a backup and the last couple of days my comptuer crashes (and reboots) itslef before the backup is done. Any help would be great.
here is my dmesg log hopping someone can point me in the right direction.

```

[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 3.0.0-17-generic (buildd@yellow) (gcc version 4.6.1 (Ubuntu/Linaro 4.6.1-9ubuntu3) ) #30-Ubuntu SMP Thu Mar 8 20:45:39 UTC 2012 (Ubuntu 3.0.0-17.30-generic 3.0.22)
[    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-3.0.0-17-generic root=UUID=36c32bdc-826b-42e1-8bdc-8983451a84c8 ro quiet splash vt.handoff=7
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   Centaur CentaurHauls
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
[    0.000000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 00000000cfdf0000 (usable)
[    0.000000]  BIOS-e820: 00000000cfdf0000 - 00000000cfdf1000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000cfdf1000 - 00000000cfe00000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000cfe00000 - 00000000cff00000 (reserved)
[    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 0000000100000000 (reserved)
[    0.000000]  BIOS-e820: 0000000100000000 - 0000000230000000 (usable)
[    0.000000] NX (Execute Disable) protection: active
[    0.000000] DMI 2.4 present.
[    0.000000] DMI: Gigabyte Technology Co., Ltd. GA-880GA-UD3H/GA-880GA-UD3H, BIOS FF 03/07/2011
[    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
[    0.000000] e820 remove range: 00000000000a0000 - 0000000000100000 (usable)
[    0.000000] No AGP bridge found
[    0.000000] last_pfn = 0x230000 max_arch_pfn = 0x400000000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-C7FFF write-protect
[    0.000000]   C8000-FFFFF uncachable
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000000 mask FFFF80000000 write-back
[    0.000000]   1 base 000080000000 mask FFFFC0000000 write-back
[    0.000000]   2 base 0000C0000000 mask FFFFF0000000 write-back
[    0.000000]   3 base 0000CFE00000 mask FFFFFFE00000 uncachable
[    0.000000]   4 base 000100000000 mask FFFF00000000 write-back
[    0.000000]   5 base 000200000000 mask FFFFE0000000 write-back
[    0.000000]   6 base 000220000000 mask FFFFF0000000 write-back
[    0.000000]   7 disabled
[    0.000000] TOM2: 0000000230000000 aka 8960M
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] original variable MTRRs
[    0.000000] reg 0, base: 0GB, range: 2GB, type WB
[    0.000000] reg 1, base: 2GB, range: 1GB, type WB
[    0.000000] reg 2, base: 3GB, range: 256MB, type WB
[    0.000000] reg 3, base: 3326MB, range: 2MB, type UC
[    0.000000] reg 4, base: 4GB, range: 4GB, type WB
[    0.000000] reg 5, base: 8GB, range: 512MB, type WB
[    0.000000] reg 6, base: 8704MB, range: 256MB, type WB
[    0.000000] total RAM covered: 3326M
[    0.000000] Found optimal setting for mtrr clean up
[    0.000000]  gran_size: 64K 	chunk_size: 4M 	num_reg: 4  	lose cover RAM: 0G
[    0.000000] New variable MTRRs
[    0.000000] reg 0, base: 0GB, range: 2GB, type WB
[    0.000000] reg 1, base: 2GB, range: 1GB, type WB
[    0.000000] reg 2, base: 3GB, range: 256MB, type WB
[    0.000000] reg 3, base: 3326MB, range: 2MB, type UC
[    0.000000] e820 update range: 00000000cfe00000 - 0000000100000000 (usable) ==> (reserved)
[    0.000000] last_pfn = 0xcfdf0 max_arch_pfn = 0x400000000
[    0.000000] found SMP MP-table at [ffff8800000f4a20] f4a20
[    0.000000] initial memory mapped : 0 - 20000000
[    0.000000] Base memory trampoline at [ffff88000009a000] 9a000 size 20480
[    0.000000] Using GB pages for direct mapping
[    0.000000] init_memory_mapping: 0000000000000000-00000000cfdf0000
[    0.000000]  0000000000 - 00c0000000 page 1G
[    0.000000]  00c0000000 - 00cfc00000 page 2M
[    0.000000]  00cfc00000 - 00cfdf0000 page 4k
[    0.000000] kernel direct mapping tables up to cfdf0000 @ 1fffd000-20000000
[    0.000000] init_memory_mapping: 0000000100000000-0000000230000000
[    0.000000]  0100000000 - 0200000000 page 1G
[    0.000000]  0200000000 - 0230000000 page 2M
[    0.000000] kernel direct mapping tables up to 230000000 @ cfdee000-cfdf0000
[    0.000000] RAMDISK: 365bc000 - 372d6000
[    0.000000] ACPI: RSDP 00000000000f6470 00014 (v00 GBT   )
[    0.000000] ACPI: RSDT 00000000cfdf1000 00040 (v01 GBT    GBTUACPI 42302E31 GBTU 01010101)
[    0.000000] ACPI: FACP 00000000cfdf1080 00074 (v01 GBT    GBTUACPI 42302E31 GBTU 01010101)
[    0.000000] ACPI: DSDT 00000000cfdf1100 076DC (v01 GBT    GBTUACPI 00001000 MSFT 03000000)
[    0.000000] ACPI: FACS 00000000cfdf0000 00040
[    0.000000] ACPI: SSDT 00000000cfdf88c0 00EDC (v01 PTLTD  POWERNOW 00000001  LTP 00000001)
[    0.000000] ACPI: HPET 00000000cfdf97c0 00038 (v01 GBT    GBTUACPI 42302E31 GBTU 00000098)
[    0.000000] ACPI: MCFG 00000000cfdf9800 0003C (v01 GBT    GBTUACPI 42302E31 GBTU 01010101)
[    0.000000] ACPI: MATS 00000000cfdf9840 00034 (v01 GBT             00000000      00000000)
[    0.000000] ACPI: TAMG 00000000cfdf98b0 00202 (v01 GBT    GBT   B0 5455312E BG?? 53450101)
[    0.000000] ACPI: APIC 00000000cfdf8800 000BC (v01 GBT    GBTUACPI 42302E31 GBTU 01010101)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] Scanning NUMA topology in Northbridge 24
[    0.000000] No NUMA configuration found
[    0.000000] Faking a node at 0000000000000000-0000000230000000
[    0.000000] Initmem setup node 0 0000000000000000-0000000230000000
[    0.000000]   NODE_DATA [000000022fffb000 - 000000022fffffff]
[    0.000000]  [ffffea0000000000-ffffea0007bfffff] PMD -> [ffff880227600000-ffff88022e7fffff] on node 0
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000010 -> 0x00001000
[    0.000000]   DMA32    0x00001000 -> 0x00100000
[    0.000000]   Normal   0x00100000 -> 0x00230000
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[3] active PFN ranges
[    0.000000]     0: 0x00000010 -> 0x0000009f
[    0.000000]     0: 0x00000100 -> 0x000cfdf0
[    0.000000]     0: 0x00100000 -> 0x00230000
[    0.000000] On node 0 totalpages: 2096511
[    0.000000]   DMA zone: 56 pages used for memmap
[    0.000000]   DMA zone: 5 pages reserved
[    0.000000]   DMA zone: 3922 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 14280 pages used for memmap
[    0.000000]   DMA32 zone: 833064 pages, LIFO batch:31
[    0.000000]   Normal zone: 17024 pages used for memmap
[    0.000000]   Normal zone: 1228160 pages, LIFO batch:31
[    0.000000] ACPI: PM-Timer IO Port: 0x4008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x02] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x03] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x04] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x05] lapic_id[0x05] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x06] lapic_id[0x06] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x07] lapic_id[0x07] disabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] dfl dfl lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] dfl dfl lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x02] dfl dfl lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x03] dfl dfl lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x04] dfl dfl lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x05] dfl dfl lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x06] dfl dfl lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x07] dfl dfl lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x08] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 8, version 33, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 low level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x10b9a201 base: 0xfed00000
[    0.000000] SMP: Allowing 8 CPUs, 2 hotplug CPUs
[    0.000000] nr_irqs_gsi: 40
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000f0000
[    0.000000] PM: Registered nosave memory: 00000000000f0000 - 0000000000100000
[    0.000000] PM: Registered nosave memory: 00000000cfdf0000 - 00000000cfdf1000
[    0.000000] PM: Registered nosave memory: 00000000cfdf1000 - 00000000cfe00000
[    0.000000] PM: Registered nosave memory: 00000000cfe00000 - 00000000cff00000
[    0.000000] PM: Registered nosave memory: 00000000cff00000 - 00000000e0000000
[    0.000000] PM: Registered nosave memory: 00000000e0000000 - 00000000f0000000
[    0.000000] PM: Registered nosave memory: 00000000f0000000 - 00000000fec00000
[    0.000000] PM: Registered nosave memory: 00000000fec00000 - 0000000100000000
[    0.000000] Allocating PCI resources starting at cff00000 (gap: cff00000:10100000)
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] setup_percpu: NR_CPUS:256 nr_cpumask_bits:256 nr_cpu_ids:8 nr_node_ids:1
[    0.000000] PERCPU: Embedded 27 pages/cpu @ffff88022fc00000 s79616 r8192 d22784 u262144
[    0.000000] pcpu-alloc: s79616 r8192 d22784 u262144 alloc=1*2097152
[    0.000000] pcpu-alloc: [0] 0 1 2 3 4 5 6 7 
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 2065146
[    0.000000] Policy zone: Normal
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.0.0-17-generic root=UUID=36c32bdc-826b-42e1-8bdc-8983451a84c8 ro quiet splash vt.handoff=7
[    0.000000] PID hash table entries: 4096 (order: 3, 32768 bytes)
[    0.000000] Checking aperture...
[    0.000000] No AGP bridge found
[    0.000000] Node 0: aperture @ c4000000 size 32 MB
[    0.000000] Aperture pointing to e820 RAM. Ignoring.
[    0.000000] Your BIOS doesn't leave a aperture memory hole
[    0.000000] Please enable the IOMMU option in the BIOS setup
[    0.000000] This costs you 64 MB of RAM
[    0.000000] Mapping aperture over 65536 KB of RAM @ c4000000
[    0.000000] PM: Registered nosave memory: 00000000c4000000 - 00000000c8000000
[    0.000000] Memory: 8107824k/9175040k available (6140k kernel code, 788996k absent, 278220k reserved, 6894k data, 988k init)
[    0.000000] SLUB: Genslabs=15, HWalign=64, Order=0-3, MinObjects=0, CPUs=8, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000] 	RCU dyntick-idle grace-period acceleration is enabled.
[    0.000000] NR_IRQS:16640 nr_irqs:744 16
[    0.000000] spurious 8259A interrupt: IRQ7.
[    0.000000] vt handoff: transparent VT on vt#7
[    0.000000] Console: colour dummy device 80x25
[    0.000000] console [tty0] enabled
[    0.000000] allocated 67108864 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] hpet clockevent registered
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 2812.248 MHz processor.
[    0.004004] Calibrating delay loop (skipped), value calculated using timer frequency.. 5624.49 BogoMIPS (lpj=11248992)
[    0.004008] pid_max: default: 32768 minimum: 301
[    0.004028] Security Framework initialized
[    0.004039] AppArmor: AppArmor initialized
[    0.004040] Yama: becoming mindful.
[    0.004607] Dentry cache hash table entries: 1048576 (order: 11, 8388608 bytes)
[    0.008698] Inode-cache hash table entries: 524288 (order: 10, 4194304 bytes)
[    0.009769] Mount-cache hash table entries: 256
[    0.009875] Initializing cgroup subsys cpuacct
[    0.009879] Initializing cgroup subsys memory
[    0.009886] Initializing cgroup subsys devices
[    0.009888] Initializing cgroup subsys freezer
[    0.009889] Initializing cgroup subsys net_cls
[    0.009891] Initializing cgroup subsys blkio
[    0.009896] Initializing cgroup subsys perf_event
[    0.009918] tseg: 00cff00000
[    0.009920] CPU: Physical Processor ID: 0
[    0.009921] CPU: Processor Core ID: 0
[    0.009922] mce: CPU supports 6 MCE banks
[    0.009930] using AMD E400 aware idle routine
[    0.011004] ACPI: Core revision 20110413
[    0.016033] ftrace: allocating 25750 entries in 101 pages
[    0.020582] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.060320] CPU0: AMD Phenom(tm) II X6 1055T Processor stepping 00
[    0.064003] Performance Events: AMD PMU driver.
[    0.064003] ... version:                0
[    0.064003] ... bit width:              48
[    0.064003] ... generic registers:      4
[    0.064003] ... value mask:             0000ffffffffffff
[    0.064003] ... max period:             00007fffffffffff
[    0.064003] ... fixed-purpose events:   0
[    0.064003] ... event mask:             000000000000000f
[    0.064003] Booting Node   0, Processors  #1
[    0.064003] smpboot cpu 1: start_ip = 9a000
[    0.152020] System has AMD C1E enabled
[    0.152035] Switch to broadcast mode on CPU1
[    0.152058]  #2
[    0.152059] smpboot cpu 2: start_ip = 9a000
[    0.244028] Switch to broadcast mode on CPU2
[    0.244071]  #3
[    0.244072] smpboot cpu 3: start_ip = 9a000
[    0.336049] Switch to broadcast mode on CPU3
[    0.336095]  #4
[    0.336096] smpboot cpu 4: start_ip = 9a000
[    0.428052] Switch to broadcast mode on CPU4
[    0.428107]  #5
[    0.428108] smpboot cpu 5: start_ip = 9a000
[    0.520062] Brought up 6 CPUs
[    0.520071] Total of 6 processors activated (33748.29 BogoMIPS).
[    0.520047] Switch to broadcast mode on CPU5
[    0.523858] Switch to broadcast mode on CPU0
[    0.523858] devtmpfs: initialized
[    0.523858] PM: Registering ACPI NVS region at cfdf0000 (4096 bytes)
[    0.525003] print_constraints: dummy: 
[    0.525023] Time: 16:29:10  Date: 04/16/12
[    0.525048] NET: Registered protocol family 16
[    0.525154] node 0 link 0: io port [9000, ffff]
[    0.525157] TOM: 00000000d0000000 aka 3328M
[    0.525160] Fam 10h mmconf [mem 0xe0000000-0xe00fffff]
[    0.525162] node 0 link 0: mmio [a0000, bffff]
[    0.525164] node 0 link 0: mmio [d0000000, dfffffff]
[    0.525166] node 0 link 0: mmio [f0000000, fe02ffff]
[    0.525168] node 0 link 0: mmio [e0000000, e06fffff] ==> [e0100000, e06fffff]
[    0.525171] TOM2: 0000000230000000 aka 8960M
[    0.525173] bus: [00, 06] on node 0 link 0
[    0.525174] bus: 00 index 0 [io  0x0000-0xffff]
[    0.525176] bus: 00 index 1 [mem 0x000a0000-0x000bffff]
[    0.525177] bus: 00 index 2 [mem 0xd0000000-0xdfffffff]
[    0.525179] bus: 00 index 3 [mem 0xe0700000-0xffffffff]
[    0.525180] bus: 00 index 4 [mem 0xe0100000-0xe06fffff]
[    0.525182] bus: 00 index 5 [mem 0x230000000-0xfcffffffff]
[    0.525190] Extended Config Space enabled on 1 nodes
[    0.525225] ACPI: bus type pci registered
[    0.525055] Trying to unpack rootfs image as initramfs...
[    0.525271] PCI: MMCONFIG for domain 0000 [bus 00-ff] at [mem 0xe0000000-0xefffffff] (base 0xe0000000)
[    0.525273] PCI: MMCONFIG at [mem 0xe0000000-0xefffffff] reserved in E820
[    0.541588] PCI: Using configuration type 1 for base access
[    0.542035] bio: create slab <bio-0> at 0
[    0.542035] ACPI: EC: Look up EC in DSDT
[    0.542035] ACPI: Actual Package length (1) is larger than NumElements field (0), truncated
[    0.542035] 
[    0.542035] ACPI: Actual Package length (1) is larger than NumElements field (0), truncated
[    0.542035] 
[    0.542035] ACPI: Actual Package length (1) is larger than NumElements field (0), truncated
[    0.542035] 
[    0.542035] ACPI: Actual Package length (1) is larger than NumElements field (0), truncated
[    0.542035] 
[    0.548128] ACPI Warning: Incorrect checksum in table [TAMG] - 0x45, should be 0x44 (20110413/tbutils-314)
[    0.548233] ACPI: Interpreter enabled
[    0.548236] ACPI: (supports S0 S3 S4 S5)
[    0.548251] ACPI: Using IOAPIC for interrupt routing
[    0.707379] Freeing initrd memory: 13416k freed
[    0.721518] ACPI: No dock devices found.
[    0.721520] HEST: Table not found.
[    0.721523] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
[    0.721563] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-ff])
[    0.721639] pci_root PNP0A03:00: host bridge window [io  0x0000-0x0cf7]
[    0.721641] pci_root PNP0A03:00: host bridge window [io  0x0d00-0xffff]
[    0.721643] pci_root PNP0A03:00: host bridge window [mem 0x000a0000-0x000bffff]
[    0.721644] pci_root PNP0A03:00: host bridge window [mem 0x000c0000-0x000dffff]
[    0.721646] pci_root PNP0A03:00: host bridge window [mem 0xd0000000-0xfebfffff]
[    0.721657] pci 0000:00:00.0: [1022:9601] type 0 class 0x000600
[    0.721667] pci 0000:00:00.0: reg 1c: [mem 0xe0000000-0xffffffff 64bit]
[    0.721701] pci 0000:00:02.0: [1022:9603] type 1 class 0x000604
[    0.721730] pci 0000:00:02.0: PME# supported from D0 D3hot D3cold
[    0.721732] pci 0000:00:02.0: PME# disabled
[    0.721748] pci 0000:00:09.0: [1022:9608] type 1 class 0x000604
[    0.721775] pci 0000:00:09.0: PME# supported from D0 D3hot D3cold
[    0.721777] pci 0000:00:09.0: PME# disabled
[    0.721787] pci 0000:00:0a.0: [1022:9609] type 1 class 0x000604
[    0.721814] pci 0000:00:0a.0: PME# supported from D0 D3hot D3cold
[    0.721815] pci 0000:00:0a.0: PME# disabled
[    0.721837] pci 0000:00:11.0: [1002:4390] type 0 class 0x000101
[    0.721853] pci 0000:00:11.0: reg 10: [io  0xff00-0xff07]
[    0.721861] pci 0000:00:11.0: reg 14: [io  0xfe00-0xfe03]
[    0.721869] pci 0000:00:11.0: reg 18: [io  0xfd00-0xfd07]
[    0.721877] pci 0000:00:11.0: reg 1c: [io  0xfc00-0xfc03]
[    0.721885] pci 0000:00:11.0: reg 20: [io  0xfb00-0xfb0f]
[    0.721893] pci 0000:00:11.0: reg 24: [mem 0xfe02f000-0xfe02f3ff]
[    0.721910] pci 0000:00:11.0: set SATA to AHCI mode
[    0.721952] pci 0000:00:12.0: [1002:4397] type 0 class 0x000c03
[    0.721963] pci 0000:00:12.0: reg 10: [mem 0xfe02e000-0xfe02efff]
[    0.722025] pci 0000:00:12.2: [1002:4396] type 0 class 0x000c03
[    0.722041] pci 0000:00:12.2: reg 10: [mem 0xfe02d000-0xfe02d0ff]
[    0.722112] pci 0000:00:12.2: supports D1 D2
[    0.722113] pci 0000:00:12.2: PME# supported from D0 D1 D2 D3hot
[    0.722116] pci 0000:00:12.2: PME# disabled
[    0.722133] pci 0000:00:13.0: [1002:4397] type 0 class 0x000c03
[    0.722144] pci 0000:00:13.0: reg 10: [mem 0xfe02c000-0xfe02cfff]
[    0.722205] pci 0000:00:13.2: [1002:4396] type 0 class 0x000c03
[    0.722221] pci 0000:00:13.2: reg 10: [mem 0xfe02b000-0xfe02b0ff]
[    0.722291] pci 0000:00:13.2: supports D1 D2
[    0.722292] pci 0000:00:13.2: PME# supported from D0 D1 D2 D3hot
[    0.722295] pci 0000:00:13.2: PME# disabled
[    0.722312] pci 0000:00:14.0: [1002:4385] type 0 class 0x000c05
[    0.722375] pci 0000:00:14.1: [1002:439c] type 0 class 0x000101
[    0.722386] pci 0000:00:14.1: reg 10: [io  0x0000-0x0007]
[    0.722394] pci 0000:00:14.1: reg 14: [io  0x0000-0x0003]
[    0.722402] pci 0000:00:14.1: reg 18: [io  0x0000-0x0007]
[    0.722410] pci 0000:00:14.1: reg 1c: [io  0x0000-0x0003]
[    0.722418] pci 0000:00:14.1: reg 20: [io  0xfa00-0xfa0f]
[    0.722449] pci 0000:00:14.2: [1002:4383] type 0 class 0x000403
[    0.722467] pci 0000:00:14.2: reg 10: [mem 0xfe024000-0xfe027fff 64bit]
[    0.722524] pci 0000:00:14.2: PME# supported from D0 D3hot D3cold
[    0.722527] pci 0000:00:14.2: PME# disabled
[    0.722537] pci 0000:00:14.3: [1002:439d] type 0 class 0x000601
[    0.722602] pci 0000:00:14.4: [1002:4384] type 1 class 0x000604
[    0.722638] pci 0000:00:14.5: [1002:4399] type 0 class 0x000c03
[    0.722649] pci 0000:00:14.5: reg 10: [mem 0xfe02a000-0xfe02afff]
[    0.722709] pci 0000:00:15.0: [1002:43a0] type 1 class 0x000604
[    0.722774] pci 0000:00:15.0: supports D1 D2
[    0.722794] pci 0000:00:15.1: [1002:43a1] type 1 class 0x000604
[    0.722858] pci 0000:00:15.1: supports D1 D2
[    0.722881] pci 0000:00:16.0: [1002:4397] type 0 class 0x000c03
[    0.722892] pci 0000:00:16.0: reg 10: [mem 0xfe029000-0xfe029fff]
[    0.722953] pci 0000:00:16.2: [1002:4396] type 0 class 0x000c03
[    0.722969] pci 0000:00:16.2: reg 10: [mem 0xfe028000-0xfe0280ff]
[    0.723039] pci 0000:00:16.2: supports D1 D2
[    0.723040] pci 0000:00:16.2: PME# supported from D0 D1 D2 D3hot
[    0.723043] pci 0000:00:16.2: PME# disabled
[    0.723059] pci 0000:00:18.0: [1022:1200] type 0 class 0x000600
[    0.723072] pci 0000:00:18.1: [1022:1201] type 0 class 0x000600
[    0.723082] pci 0000:00:18.2: [1022:1202] type 0 class 0x000600
[    0.723094] pci 0000:00:18.3: [1022:1203] type 0 class 0x000600
[    0.723106] pci 0000:00:18.4: [1022:1204] type 0 class 0x000600
[    0.723148] pci 0000:01:00.0: [10de:0de0] type 0 class 0x000300
[    0.723157] pci 0000:01:00.0: reg 10: [mem 0xfb000000-0xfbffffff]
[    0.723166] pci 0000:01:00.0: reg 14: [mem 0xd0000000-0xd7ffffff 64bit pref]
[    0.723175] pci 0000:01:00.0: reg 1c: [mem 0xde000000-0xdfffffff 64bit pref]
[    0.723182] pci 0000:01:00.0: reg 24: [io  0xef00-0xef7f]
[    0.723188] pci 0000:01:00.0: reg 30: [mem 0x00000000-0x0007ffff pref]
[    0.723238] pci 0000:01:00.1: [10de:0bea] type 0 class 0x000403
[    0.723246] pci 0000:01:00.1: reg 10: [mem 0xfcffc000-0xfcffffff]
[    0.728066] pci 0000:00:02.0: PCI bridge to [bus 01-01]
[    0.728071] pci 0000:00:02.0:   bridge window [io  0xe000-0xefff]
[    0.728074] pci 0000:00:02.0:   bridge window [mem 0xfb000000-0xfcffffff]
[    0.728077] pci 0000:00:02.0:   bridge window [mem 0xd0000000-0xdfffffff 64bit pref]
[    0.728113] pci 0000:02:00.0: [1033:0194] type 0 class 0x000c03
[    0.728127] pci 0000:02:00.0: reg 10: [mem 0xfd6fe000-0xfd6fffff 64bit]
[    0.728197] pci 0000:02:00.0: PME# supported from D0 D3hot D3cold
[    0.728200] pci 0000:02:00.0: PME# disabled
[    0.736065] pci 0000:00:09.0: PCI bridge to [bus 02-02]
[    0.736070] pci 0000:00:09.0:   bridge window [io  0xd000-0xdfff]
[    0.736072] pci 0000:00:09.0:   bridge window [mem 0xfd600000-0xfd6fffff]
[    0.736075] pci 0000:00:09.0:   bridge window [mem 0xfdf00000-0xfdffffff 64bit pref]
[    0.736110] pci 0000:03:00.0: [10ec:8168] type 0 class 0x000200
[    0.736123] pci 0000:03:00.0: reg 10: [io  0xce00-0xceff]
[    0.736143] pci 0000:03:00.0: reg 18: [mem 0xfd7ff000-0xfd7fffff 64bit pref]
[    0.736155] pci 0000:03:00.0: reg 20: [mem 0xfd7f8000-0xfd7fbfff 64bit pref]
[    0.736209] pci 0000:03:00.0: supports D1 D2
[    0.736210] pci 0000:03:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.736214] pci 0000:03:00.0: PME# disabled
[    0.744065] pci 0000:00:0a.0: PCI bridge to [bus 03-03]
[    0.744069] pci 0000:00:0a.0:   bridge window [io  0xc000-0xcfff]
[    0.744071] pci 0000:00:0a.0:   bridge window [mem 0xfdc00000-0xfdcfffff]
[    0.744075] pci 0000:00:0a.0:   bridge window [mem 0xfd700000-0xfd7fffff 64bit pref]
[    0.744108] pci 0000:04:06.0: [10ec:8185] type 0 class 0x000200
[    0.744128] pci 0000:04:06.0: reg 10: [io  0xbe00-0xbeff]
[    0.744139] pci 0000:04:06.0: reg 14: [mem 0xfdeff000-0xfdeff3ff]
[    0.744221] pci 0000:04:06.0: supports D1 D2
[    0.744222] pci 0000:04:06.0: PME# supported from D1 D2 D3hot D3cold
[    0.744227] pci 0000:04:06.0: PME# disabled
[    0.744255] pci 0000:04:0e.0: [104c:8024] type 0 class 0x000c00
[    0.744276] pci 0000:04:0e.0: reg 10: [mem 0xfdefe000-0xfdefe7ff]
[    0.744287] pci 0000:04:0e.0: reg 14: [mem 0xfdef8000-0xfdefbfff]
[    0.744371] pci 0000:04:0e.0: supports D1 D2
[    0.744372] pci 0000:04:0e.0: PME# supported from D0 D1 D2 D3hot
[    0.744376] pci 0000:04:0e.0: PME# disabled
[    0.744407] pci 0000:00:14.4: PCI bridge to [bus 04-04] (subtractive decode)
[    0.744410] pci 0000:00:14.4:   bridge window [io  0xb000-0xbfff]
[    0.744414] pci 0000:00:14.4:   bridge window [mem 0xfde00000-0xfdefffff]
[    0.744417] pci 0000:00:14.4:   bridge window [mem 0xfdd00000-0xfddfffff pref]
[    0.744420] pci 0000:00:14.4:   bridge window [io  0x0000-0x0cf7] (subtractive decode)
[    0.744421] pci 0000:00:14.4:   bridge window [io  0x0d00-0xffff] (subtractive decode)
[    0.744423] pci 0000:00:14.4:   bridge window [mem 0x000a0000-0x000bffff] (subtractive decode)
[    0.744425] pci 0000:00:14.4:   bridge window [mem 0x000c0000-0x000dffff] (subtractive decode)
[    0.744427] pci 0000:00:14.4:   bridge window [mem 0xd0000000-0xfebfffff] (subtractive decode)
[    0.744489] pci 0000:05:00.0: [197b:2363] type 0 class 0x000101
[    0.744584] pci 0000:05:00.0: reg 24: [mem 0xfdbfe000-0xfdbfffff]
[    0.744646] pci 0000:05:00.0: PME# supported from D3hot
[    0.744651] pci 0000:05:00.0: PME# disabled
[    0.744678] pci 0000:05:00.1: [197b:2363] type 0 class 0x000101
[    0.744701] pci 0000:05:00.1: reg 10: [io  0xaf00-0xaf07]
[    0.744714] pci 0000:05:00.1: reg 14: [io  0xae00-0xae03]
[    0.744727] pci 0000:05:00.1: reg 18: [io  0xad00-0xad07]
[    0.744740] pci 0000:05:00.1: reg 1c: [io  0xac00-0xac03]
[    0.744753] pci 0000:05:00.1: reg 20: [io  0xab00-0xab0f]
[    0.744835] pci 0000:05:00.0: disabling ASPM on pre-1.1 PCIe device.  You can enable it with 'pcie_aspm=force'
[    0.744847] pci 0000:00:15.0: PCI bridge to [bus 05-05]
[    0.744851] pci 0000:00:15.0:   bridge window [io  0xa000-0xafff]
[    0.744854] pci 0000:00:15.0:   bridge window [mem 0xfdb00000-0xfdbfffff]
[    0.744859] pci 0000:00:15.0:   bridge window [mem 0xfda00000-0xfdafffff 64bit pref]
[    0.744900] pci 0000:00:15.1: PCI bridge to [bus 06-06]
[    0.744904] pci 0000:00:15.1:   bridge window [io  0x9000-0x9fff]
[    0.744907] pci 0000:00:15.1:   bridge window [mem 0xfd900000-0xfd9fffff]
[    0.744912] pci 0000:00:15.1:   bridge window [mem 0xfd800000-0xfd8fffff 64bit pref]
[    0.744931] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.745094] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEX0._PRT]
[    0.745113] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEX1._PRT]
[    0.745134] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P2P_._PRT]
[    0.745176] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCE2._PRT]
[    0.745199] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCE9._PRT]
[    0.745216] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCEA._PRT]
[    0.745235]  pci0000:00: Requesting ACPI _OSC control (0x1d)
[    0.745237]  pci0000:00: ACPI _OSC request failed (AE_NOT_FOUND), returned control mask: 0x1d
[    0.745238] ACPI _OSC control for PCIe not granted, disabling ASPM
[    0.752632] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 10 11) *0
[    0.752659] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 10 11) *0
[    0.752683] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 10 11) *0
[    0.752707] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 10 11) *0
[    0.752733] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 10 11) *0
[    0.752758] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 10 11) *0
[    0.752782] ACPI: PCI Interrupt Link [LNK0] (IRQs 3 4 5 6 7 10 11) *0
[    0.752805] ACPI: PCI Interrupt Link [LNK1] (IRQs 3 4 5 6 7 10 11) *0
[    0.752878] vgaarb: device added: PCI:0000:01:00.0,decodes=io+mem,owns=io+mem,locks=none
[    0.752882] vgaarb: loaded
[    0.752883] vgaarb: bridge control possible 0000:01:00.0
[    0.753003] SCSI subsystem initialized
[    0.753025] libata version 3.00 loaded.
[    0.753025] usbcore: registered new interface driver usbfs
[    0.753025] usbcore: registered new interface driver hub
[    0.753025] usbcore: registered new device driver usb
[    0.753025] PCI: Using ACPI for IRQ routing
[    0.760616] PCI: pci_cache_line_size set to 64 bytes
[    0.760622] pci 0000:00:00.0: no compatible bridge window for [mem 0xe0000000-0xffffffff 64bit]
[    0.760698] reserve RAM buffer: 000000000009f800 - 000000000009ffff 
[    0.760700] reserve RAM buffer: 00000000cfdf0000 - 00000000cfffffff 
[    0.760765] NetLabel: Initializing
[    0.760766] NetLabel:  domain hash size = 128
[    0.760767] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.760776] NetLabel:  unlabeled traffic allowed by default
[    0.760802] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[    0.760805] hpet0: 3 comparators, 32-bit 14.318180 MHz counter
[    0.762841] Switching to clocksource hpet
[    0.762860] Switched to NOHz mode on CPU #5
[    0.762850] Switched to NOHz mode on CPU #2
[    0.762859] Switched to NOHz mode on CPU #4
[    0.762902] Switched to NOHz mode on CPU #0
[    0.762844] Switched to NOHz mode on CPU #1
[    0.762854] Switched to NOHz mode on CPU #3
[    0.764125] AppArmor: AppArmor Filesystem Enabled
[    0.764140] pnp: PnP ACPI init
[    0.764150] ACPI: bus type pnp registered
[    0.764212] pnp 00:00: [bus 00-ff]
[    0.764214] pnp 00:00: [io  0x0cf8-0x0cff]
[    0.764216] pnp 00:00: [io  0x0000-0x0cf7 window]
[    0.764217] pnp 00:00: [io  0x0d00-0xffff window]
[    0.764219] pnp 00:00: [mem 0x000a0000-0x000bffff window]
[    0.764220] pnp 00:00: [mem 0x000c0000-0x000dffff window]
[    0.764222] pnp 00:00: [mem 0xd0000000-0xfebfffff window]
[    0.764250] pnp 00:00: Plug and Play ACPI device, IDs PNP0a03 (active)
[    0.764257] pnp 00:01: [io  0x0010-0x001f]
[    0.764259] pnp 00:01: [io  0x0022-0x003f]
[    0.764260] pnp 00:01: [io  0x0044-0x005f]
[    0.764261] pnp 00:01: [io  0x0062-0x0063]
[    0.764263] pnp 00:01: [io  0x0065-0x006f]
[    0.764264] pnp 00:01: [io  0x0074-0x007f]
[    0.764265] pnp 00:01: [io  0x0091-0x0093]
[    0.764266] pnp 00:01: [io  0x00a2-0x00bf]
[    0.764268] pnp 00:01: [io  0x00e0-0x00ef]
[    0.764269] pnp 00:01: [io  0x04d0-0x04d1]
[    0.764270] pnp 00:01: [io  0x0220-0x0225]
[    0.764271] pnp 00:01: [io  0x0290-0x0294]
[    0.764310] system 00:01: [io  0x04d0-0x04d1] has been reserved
[    0.764312] system 00:01: [io  0x0220-0x0225] has been reserved
[    0.764314] system 00:01: [io  0x0290-0x0294] has been reserved
[    0.764316] system 00:01: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.764757] pnp 00:02: [io  0x4100-0x411f]
[    0.764761] pnp 00:02: [io  0x0228-0x022f]
[    0.764763] pnp 00:02: [io  0x040b]
[    0.764764] pnp 00:02: [io  0x04d6]
[    0.764765] pnp 00:02: [io  0x0c00-0x0c01]
[    0.764767] pnp 00:02: [io  0x0c14]
[    0.764768] pnp 00:02: [io  0x0c50-0x0c52]
[    0.764770] pnp 00:02: [io  0x0c6c-0x0c6d]
[    0.764771] pnp 00:02: [io  0x0c6f]
[    0.764773] pnp 00:02: [io  0x0cd0-0x0cd1]
[    0.764774] pnp 00:02: [io  0x0cd2-0x0cd3]
[    0.764776] pnp 00:02: [io  0x0cd4-0x0cdf]
[    0.764777] pnp 00:02: [io  0x4000-0x40fe]
[    0.764779] pnp 00:02: [io  0x4210-0x4217]
[    0.764780] pnp 00:02: [io  0x0b00-0x0b0f]
[    0.764782] pnp 00:02: [io  0x0b10-0x0b1f]
[    0.764783] pnp 00:02: [io  0x0b20-0x0b3f]
[    0.764785] pnp 00:02: [mem 0x00000000-0x00000fff window]
[    0.764787] pnp 00:02: [mem 0xfee00400-0xfee00fff window]
[    0.764791] pnp 00:02: disabling [mem 0x00000000-0x00000fff window] because it overlaps 0000:00:00.0 BAR 3 [mem 0x00000000-0x1fffffff 64bit]
[    0.764815] pnp 00:02: disabling [mem 0x00000000-0x00000fff window disabled] because it overlaps 0000:01:00.0 BAR 6 [mem 0x00000000-0x0007ffff pref]
[    0.764843] system 00:02: [io  0x4100-0x411f] has been reserved
[    0.764845] system 00:02: [io  0x0228-0x022f] has been reserved
[    0.764847] system 00:02: [io  0x040b] has been reserved
[    0.764849] system 00:02: [io  0x04d6] has been reserved
[    0.764851] system 00:02: [io  0x0c00-0x0c01] has been reserved
[    0.764853] system 00:02: [io  0x0c14] has been reserved
[    0.764855] system 00:02: [io  0x0c50-0x0c52] has been reserved
[    0.764857] system 00:02: [io  0x0c6c-0x0c6d] has been reserved
[    0.764859] system 00:02: [io  0x0c6f] has been reserved
[    0.764861] system 00:02: [io  0x0cd0-0x0cd1] has been reserved
[    0.764863] system 00:02: [io  0x0cd2-0x0cd3] has been reserved
[    0.764865] system 00:02: [io  0x0cd4-0x0cdf] has been reserved
[    0.764867] system 00:02: [io  0x4000-0x40fe] has been reserved
[    0.764869] system 00:02: [io  0x4210-0x4217] has been reserved
[    0.764871] system 00:02: [io  0x0b00-0x0b0f] has been reserved
[    0.764873] system 00:02: [io  0x0b10-0x0b1f] has been reserved
[    0.764875] system 00:02: [io  0x0b20-0x0b3f] has been reserved
[    0.764878] system 00:02: [mem 0xfee00400-0xfee00fff window] has been reserved
[    0.764880] system 00:02: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.764948] pnp 00:03: [dma 4]
[    0.764950] pnp 00:03: [io  0x0000-0x000f]
[    0.764951] pnp 00:03: [io  0x0080-0x0090]
[    0.764953] pnp 00:03: [io  0x0094-0x009f]
[    0.764954] pnp 00:03: [io  0x00c0-0x00df]
[    0.764978] pnp 00:03: Plug and Play ACPI device, IDs PNP0200 (active)
[    0.765009] pnp 00:04: [io  0x0070-0x0073]
[    0.765021] pnp 00:04: [irq 8]
[    0.765039] pnp 00:04: Plug and Play ACPI device, IDs PNP0b00 (active)
[    0.765044] pnp 00:05: [io  0x0061]
[    0.765060] pnp 00:05: Plug and Play ACPI device, IDs PNP0800 (active)
[    0.765065] pnp 00:06: [io  0x00f0-0x00ff]
[    0.765071] pnp 00:06: [irq 13]
[    0.765087] pnp 00:06: Plug and Play ACPI device, IDs PNP0c04 (active)
[    0.765265] pnp 00:07: [io  0x03f8-0x03ff]
[    0.765272] pnp 00:07: [irq 4]
[    0.765308] pnp 00:07: Plug and Play ACPI device, IDs PNP0501 (active)
[    0.765342] pnp 00:08: [mem 0xe0000000-0xefffffff]
[    0.765374] system 00:08: [mem 0xe0000000-0xefffffff] has been reserved
[    0.765376] system 00:08: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.765469] pnp 00:09: [mem 0x000cda00-0x000cffff]
[    0.765471] pnp 00:09: [mem 0x000f0000-0x000f7fff]
[    0.765472] pnp 00:09: [mem 0x000f8000-0x000fbfff]
[    0.765476] pnp 00:09: [mem 0x000fc000-0x000fffff]
[    0.765477] pnp 00:09: [mem 0xcfdf0000-0xcfdfffff]
[    0.765479] pnp 00:09: [mem 0xffff0000-0xffffffff]
[    0.765480] pnp 00:09: [mem 0x00000000-0x0009ffff]
[    0.765482] pnp 00:09: [mem 0x00100000-0xcfdeffff]
[    0.765483] pnp 00:09: [mem 0xcfe00000-0xcfefffff]
[    0.765484] pnp 00:09: [mem 0xcff00000-0xcfffffff]
[    0.765486] pnp 00:09: [mem 0x00000000-0xffffffffffffffff disabled]
[    0.765488] pnp 00:09: [mem 0xfec00000-0xfec00fff]
[    0.765489] pnp 00:09: [mem 0xfee00000-0xfee00fff]
[    0.765490] pnp 00:09: [mem 0xfff80000-0xfffeffff]
[    0.765493] pnp 00:09: disabling [mem 0x000cda00-0x000cffff] because it overlaps 0000:00:00.0 BAR 3 [mem 0x00000000-0x1fffffff 64bit]
[    0.765496] pnp 00:09: disabling [mem 0x000f0000-0x000f7fff] because it overlaps 0000:00:00.0 BAR 3 [mem 0x00000000-0x1fffffff 64bit]
[    0.765499] pnp 00:09: disabling [mem 0x000f8000-0x000fbfff] because it overlaps 0000:00:00.0 BAR 3 [mem 0x00000000-0x1fffffff 64bit]
[    0.765501] pnp 00:09: disabling [mem 0x000fc000-0x000fffff] because it overlaps 0000:00:00.0 BAR 3 [mem 0x00000000-0x1fffffff 64bit]
[    0.765504] pnp 00:09: disabling [mem 0x00000000-0x0009ffff] because it overlaps 0000:00:00.0 BAR 3 [mem 0x00000000-0x1fffffff 64bit]
[    0.765507] pnp 00:09: disabling [mem 0x00100000-0xcfdeffff] because it overlaps 0000:00:00.0 BAR 3 [mem 0x00000000-0x1fffffff 64bit]
[    0.765531] pnp 00:09: [Firmware Bug]: [mem 0x00000000-0xffffffffffffffff disabled] covers only part of AMD MMCONFIG area [mem 0xe0000000-0xe00fffff]; adding more reservations
[    0.765553] system 00:09: [mem 0xcfdf0000-0xcfdfffff] could not be reserved
[    0.765555] system 00:09: [mem 0xffff0000-0xffffffff] has been reserved
[    0.765558] system 00:09: [mem 0xcfe00000-0xcfefffff] has been reserved
[    0.765559] system 00:09: [mem 0xcff00000-0xcfffffff] could not be reserved
[    0.765561] system 00:09: [mem 0xfec00000-0xfec00fff] could not be reserved
[    0.765563] system 00:09: [mem 0xfee00000-0xfee00fff] could not be reserved
[    0.765565] system 00:09: [mem 0xfff80000-0xfffeffff] has been reserved
[    0.765567] system 00:09: Plug and Play ACPI device, IDs PNP0c01 (active)
[    0.765582] pnp: PnP ACPI: found 10 devices
[    0.765583] ACPI: ACPI bus type pnp unregistered
[    0.770958] PCI: max bus depth: 1 pci_try_num: 2
[    0.770986] pci 0000:01:00.0: BAR 6: assigned [mem 0xd8000000-0xd807ffff pref]
[    0.770989] pci 0000:00:02.0: PCI bridge to [bus 01-01]
[    0.770991] pci 0000:00:02.0:   bridge window [io  0xe000-0xefff]
[    0.770993] pci 0000:00:02.0:   bridge window [mem 0xfb000000-0xfcffffff]
[    0.770996] pci 0000:00:02.0:   bridge window [mem 0xd0000000-0xdfffffff 64bit pref]
[    0.770999] pci 0000:00:09.0: PCI bridge to [bus 02-02]
[    0.771001] pci 0000:00:09.0:   bridge window [io  0xd000-0xdfff]
[    0.771003] pci 0000:00:09.0:   bridge window [mem 0xfd600000-0xfd6fffff]
[    0.771005] pci 0000:00:09.0:   bridge window [mem 0xfdf00000-0xfdffffff 64bit pref]
[    0.771008] pci 0000:00:0a.0: PCI bridge to [bus 03-03]
[    0.771010] pci 0000:00:0a.0:   bridge window [io  0xc000-0xcfff]
[    0.771013] pci 0000:00:0a.0:   bridge window [mem 0xfdc00000-0xfdcfffff]
[    0.771015] pci 0000:00:0a.0:   bridge window [mem 0xfd700000-0xfd7fffff 64bit pref]
[    0.771018] pci 0000:00:14.4: PCI bridge to [bus 04-04]
[    0.771021] pci 0000:00:14.4:   bridge window [io  0xb000-0xbfff]
[    0.771025] pci 0000:00:14.4:   bridge window [mem 0xfde00000-0xfdefffff]
[    0.771028] pci 0000:00:14.4:   bridge window [mem 0xfdd00000-0xfddfffff pref]
[    0.771034] pci 0000:00:15.0: PCI bridge to [bus 05-05]
[    0.771036] pci 0000:00:15.0:   bridge window [io  0xa000-0xafff]
[    0.771040] pci 0000:00:15.0:   bridge window [mem 0xfdb00000-0xfdbfffff]
[    0.771043] pci 0000:00:15.0:   bridge window [mem 0xfda00000-0xfdafffff 64bit pref]
[    0.771048] pci 0000:00:15.1: PCI bridge to [bus 06-06]
[    0.771050] pci 0000:00:15.1:   bridge window [io  0x9000-0x9fff]
[    0.771054] pci 0000:00:15.1:   bridge window [mem 0xfd900000-0xfd9fffff]
[    0.771057] pci 0000:00:15.1:   bridge window [mem 0xfd800000-0xfd8fffff 64bit pref]
[    0.771073] pci 0000:00:02.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    0.771076] pci 0000:00:02.0: setting latency timer to 64
[    0.771086] pci 0000:00:09.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    0.771088] pci 0000:00:09.0: setting latency timer to 64
[    0.771092] pci 0000:00:0a.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    0.771094] pci 0000:00:0a.0: setting latency timer to 64
[    0.771102] pci 0000:00:15.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    0.771105] pci 0000:00:15.0: setting latency timer to 64
[    0.771110] pci 0000:00:15.1: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    0.771113] pci 0000:00:15.1: setting latency timer to 64
[    0.771116] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
[    0.771117] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff]
[    0.771119] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
[    0.771121] pci_bus 0000:00: resource 7 [mem 0x000c0000-0x000dffff]
[    0.771122] pci_bus 0000:00: resource 8 [mem 0xd0000000-0xfebfffff]
[    0.771124] pci_bus 0000:01: resource 0 [io  0xe000-0xefff]
[    0.771126] pci_bus 0000:01: resource 1 [mem 0xfb000000-0xfcffffff]
[    0.771128] pci_bus 0000:01: resource 2 [mem 0xd0000000-0xdfffffff 64bit pref]
[    0.771129] pci_bus 0000:02: resource 0 [io  0xd000-0xdfff]
[    0.771131] pci_bus 0000:02: resource 1 [mem 0xfd600000-0xfd6fffff]
[    0.771133] pci_bus 0000:02: resource 2 [mem 0xfdf00000-0xfdffffff 64bit pref]
[    0.771135] pci_bus 0000:03: resource 0 [io  0xc000-0xcfff]
[    0.771136] pci_bus 0000:03: resource 1 [mem 0xfdc00000-0xfdcfffff]
[    0.771138] pci_bus 0000:03: resource 2 [mem 0xfd700000-0xfd7fffff 64bit pref]
[    0.771140] pci_bus 0000:04: resource 0 [io  0xb000-0xbfff]
[    0.771141] pci_bus 0000:04: resource 1 [mem 0xfde00000-0xfdefffff]
[    0.771143] pci_bus 0000:04: resource 2 [mem 0xfdd00000-0xfddfffff pref]
[    0.771145] pci_bus 0000:04: resource 4 [io  0x0000-0x0cf7]
[    0.771146] pci_bus 0000:04: resource 5 [io  0x0d00-0xffff]
[    0.771148] pci_bus 0000:04: resource 6 [mem 0x000a0000-0x000bffff]
[    0.771150] pci_bus 0000:04: resource 7 [mem 0x000c0000-0x000dffff]
[    0.771151] pci_bus 0000:04: resource 8 [mem 0xd0000000-0xfebfffff]
[    0.771153] pci_bus 0000:05: resource 0 [io  0xa000-0xafff]
[    0.771154] pci_bus 0000:05: resource 1 [mem 0xfdb00000-0xfdbfffff]
[    0.771156] pci_bus 0000:05: resource 2 [mem 0xfda00000-0xfdafffff 64bit pref]
[    0.771158] pci_bus 0000:06: resource 0 [io  0x9000-0x9fff]
[    0.771160] pci_bus 0000:06: resource 1 [mem 0xfd900000-0xfd9fffff]
[    0.771161] pci_bus 0000:06: resource 2 [mem 0xfd800000-0xfd8fffff 64bit pref]
[    0.771188] NET: Registered protocol family 2
[    0.771355] IP route cache hash table entries: 262144 (order: 9, 2097152 bytes)
[    0.772473] TCP established hash table entries: 524288 (order: 11, 8388608 bytes)
[    0.774714] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[    0.774991] TCP: Hash tables configured (established 524288 bind 65536)
[    0.774993] TCP reno registered
[    0.775005] UDP hash table entries: 4096 (order: 5, 131072 bytes)
[    0.775052] UDP-Lite hash table entries: 4096 (order: 5, 131072 bytes)
[    0.775186] NET: Registered protocol family 1
[    1.064192] pci 0000:01:00.0: Boot video device
[    1.064243] PCI: CLS 4 bytes, default 64
[    1.066132] PCI-DMA: Disabling AGP.
[    1.066243] PCI-DMA: aperture base @ c4000000 size 65536 KB
[    1.066244] PCI-DMA: using GART IOMMU.
[    1.066247] PCI-DMA: Reserving 64MB of IOMMU area in the AGP aperture
[    1.069622] audit: initializing netlink socket (disabled)
[    1.069637] type=2000 audit(1334593749.064:1): initialized
[    1.099609] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    1.130776] VFS: Disk quotas dquot_6.5.2
[    1.130824] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    1.131281] fuse init (API version 7.16)
[    1.131335] msgmni has been set to 15990
[    1.131786] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    1.131819] io scheduler noop registered
[    1.131820] io scheduler deadline registered
[    1.131844] io scheduler cfq registered (default)
[    1.131960] pcieport 0000:00:02.0: setting latency timer to 64
[    1.131984] pcieport 0000:00:02.0: irq 40 for MSI/MSI-X
[    1.132119] pcieport 0000:00:09.0: setting latency timer to 64
[    1.132139] pcieport 0000:00:09.0: irq 41 for MSI/MSI-X
[    1.132216] pcieport 0000:00:0a.0: setting latency timer to 64
[    1.132235] pcieport 0000:00:0a.0: irq 42 for MSI/MSI-X
[    1.132474] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    1.132500] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    1.132598] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0
[    1.132603] ACPI: Power Button [PWRB]
[    1.132636] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
[    1.132639] ACPI: Power Button [PWRF]
[    1.132657] ACPI: acpi_idle registered with cpuidle
[    1.132675] ACPI: processor limited to max C-state 1
[    1.324701] ERST: Table is not found!
[    1.324748] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    1.345151] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    1.377392] 00:07: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    1.377564] Linux agpgart interface v0.103
[    1.378190] brd: module loaded
[    1.378481] loop: module loaded
[    1.378687] pata_acpi 0000:00:14.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    1.378782] pata_acpi 0000:05:00.1: enabling device (0000 -> 0001)
[    1.378787] pata_acpi 0000:05:00.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    1.378806] pata_acpi 0000:05:00.1: setting latency timer to 64
[    1.378815] pata_acpi 0000:05:00.1: PCI INT B disabled
[    1.379116] Fixed MDIO Bus: probed
[    1.379133] PPP generic driver version 2.4.2
[    1.379157] tun: Universal TUN/TAP device driver, 1.6
[    1.379159] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    1.379210] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    1.379313] ehci_hcd 0000:00:12.2: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    1.379349] ehci_hcd 0000:00:12.2: EHCI Host Controller
[    1.379392] ehci_hcd 0000:00:12.2: new USB bus registered, assigned bus number 1
[    1.379400] ehci_hcd 0000:00:12.2: applying AMD SB700/SB800/Hudson-2/3 EHCI dummy qh workaround
[    1.379415] QUIRK: Enable AMD PLL fix
[    1.379425] ehci_hcd 0000:00:12.2: debug port 1
[    1.379451] ehci_hcd 0000:00:12.2: irq 17, io mem 0xfe02d000
[    1.388095] ehci_hcd 0000:00:12.2: USB 2.0 started, EHCI 1.00
[    1.388186] hub 1-0:1.0: USB hub found
[    1.388189] hub 1-0:1.0: 5 ports detected
[    1.388337] ehci_hcd 0000:00:13.2: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    1.388350] ehci_hcd 0000:00:13.2: EHCI Host Controller
[    1.388375] ehci_hcd 0000:00:13.2: new USB bus registered, assigned bus number 2
[    1.388382] ehci_hcd 0000:00:13.2: applying AMD SB700/SB800/Hudson-2/3 EHCI dummy qh workaround
[    1.388399] ehci_hcd 0000:00:13.2: debug port 1
[    1.388411] ehci_hcd 0000:00:13.2: irq 17, io mem 0xfe02b000
[    1.400094] ehci_hcd 0000:00:13.2: USB 2.0 started, EHCI 1.00
[    1.400176] hub 2-0:1.0: USB hub found
[    1.400179] hub 2-0:1.0: 5 ports detected
[    1.400320] ehci_hcd 0000:00:16.2: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    1.400331] ehci_hcd 0000:00:16.2: EHCI Host Controller
[    1.400359] ehci_hcd 0000:00:16.2: new USB bus registered, assigned bus number 3
[    1.400365] ehci_hcd 0000:00:16.2: applying AMD SB700/SB800/Hudson-2/3 EHCI dummy qh workaround
[    1.400384] ehci_hcd 0000:00:16.2: debug port 1
[    1.400395] ehci_hcd 0000:00:16.2: irq 17, io mem 0xfe028000
[    1.412094] ehci_hcd 0000:00:16.2: USB 2.0 started, EHCI 1.00
[    1.412174] hub 3-0:1.0: USB hub found
[    1.412177] hub 3-0:1.0: 4 ports detected
[    1.412250] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    1.412335] ohci_hcd 0000:00:12.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    1.412346] ohci_hcd 0000:00:12.0: OHCI Host Controller
[    1.412373] ohci_hcd 0000:00:12.0: new USB bus registered, assigned bus number 4
[    1.412401] ohci_hcd 0000:00:12.0: irq 18, io mem 0xfe02e000
[    1.472139] hub 4-0:1.0: USB hub found
[    1.472145] hub 4-0:1.0: 5 ports detected
[    1.472305] ohci_hcd 0000:00:13.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    1.472318] ohci_hcd 0000:00:13.0: OHCI Host Controller
[    1.472342] ohci_hcd 0000:00:13.0: new USB bus registered, assigned bus number 5
[    1.472356] ohci_hcd 0000:00:13.0: irq 18, io mem 0xfe02c000
[    1.532148] hub 5-0:1.0: USB hub found
[    1.532153] hub 5-0:1.0: 5 ports detected
[    1.532312] ohci_hcd 0000:00:14.5: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    1.532324] ohci_hcd 0000:00:14.5: OHCI Host Controller
[    1.532349] ohci_hcd 0000:00:14.5: new USB bus registered, assigned bus number 6
[    1.532365] ohci_hcd 0000:00:14.5: irq 18, io mem 0xfe02a000
[    1.592147] hub 6-0:1.0: USB hub found
[    1.592152] hub 6-0:1.0: 2 ports detected
[    1.592302] ohci_hcd 0000:00:16.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    1.592316] ohci_hcd 0000:00:16.0: OHCI Host Controller
[    1.592343] ohci_hcd 0000:00:16.0: new USB bus registered, assigned bus number 7
[    1.592356] ohci_hcd 0000:00:16.0: irq 18, io mem 0xfe029000
[    1.652137] hub 7-0:1.0: USB hub found
[    1.652142] hub 7-0:1.0: 4 ports detected
[    1.652216] uhci_hcd: USB Universal Host Controller Interface driver
[    1.652260] i8042: PNP: No PS/2 controller found. Probing ports directly.
[    1.686336] i8042: Failed to disable AUX port, but continuing anyway... Is this a SiS?
[    1.686337] i8042: If AUX port is really absent please use the 'i8042.noaux' option
[    1.700087] usb 1-2: new high speed USB device number 2 using ehci_hcd
[    1.936175] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.936250] mousedev: PS/2 mouse device common for all mice
[    1.936334] rtc_cmos 00:04: RTC can wake from S4
[    1.936400] rtc_cmos 00:04: rtc core: registered rtc_cmos as rtc0
[    1.936428] rtc0: alarms up to one month, 242 bytes nvram, hpet irqs
[    1.936492] device-mapper: uevent: version 1.0.3
[    1.936533] device-mapper: ioctl: 4.20.0-ioctl (2011-02-02) initialised: dm-devel@redhat.com
[    1.936539] cpuidle: using governor ladder
[    1.936540] cpuidle: using governor menu
[    1.936541] EFI Variables Facility v0.08 2004-May-17
[    1.936682] TCP cubic registered
[    1.936758] NET: Registered protocol family 10
[    1.937065] NET: Registered protocol family 17
[    1.937074] Registering the dns_resolver key type
[    1.937126] PM: Hibernation image not present or could not be loaded.
[    1.937133] registered taskstats version 1
[    1.957420]   Magic number: 8:811:489
[    1.957550] rtc_cmos 00:04: setting system clock to 2012-04-16 16:29:11 UTC (1334593751)
[    1.957576] powernow-k8: Found 1 AMD Phenom(tm) II X6 1055T Processor (6 cpu cores) (version 2.20.00)
[    1.957593] powernow-k8: Core Performance Boosting: on.
[    1.957628] powernow-k8:    0 : pstate 0 (2800 MHz)
[    1.957629] powernow-k8:    1 : pstate 1 (2200 MHz)
[    1.957631] powernow-k8:    2 : pstate 2 (1500 MHz)
[    1.957632] powernow-k8:    3 : pstate 3 (800 MHz)
[    1.958050] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.958053] EDD information not available.
[    1.959241] Freeing unused kernel memory: 988k freed
[    1.959412] Write protecting the kernel read-only data: 12288k
[    1.964547] Freeing unused kernel memory: 2032k freed
[    1.968391] Freeing unused kernel memory: 1388k freed
[    1.981912] udevd[141]: starting version 173
[    1.995588] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    1.995612] r8169 0000:03:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    1.995649] r8169 0000:03:00.0: setting latency timer to 64
[    1.995692] r8169 0000:03:00.0: irq 43 for MSI/MSI-X
[    1.996116] r8169 0000:03:00.0: eth0: RTL8168e/8111e at 0xffffc90000c74000, 50:e5:49:35:b4:fd, XID 0c200000 IRQ 43
[    1.996138] ahci 0000:00:11.0: version 3.0
[    1.996153] ahci 0000:00:11.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    1.996247] ahci 0000:00:11.0: AHCI 0001.0200 32 slots 4 ports 6 Gbps 0xf impl SATA mode
[    1.996251] ahci 0000:00:11.0: flags: 64bit ncq sntf ilck pm led clo pmp pio slum part 
[    1.996763] xhci_hcd 0000:02:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    1.996779] xhci_hcd 0000:02:00.0: setting latency timer to 64
[    1.996783] xhci_hcd 0000:02:00.0: xHCI Host Controller
[    1.996844] xhci_hcd 0000:02:00.0: new USB bus registered, assigned bus number 8
[    1.996963] xhci_hcd 0000:02:00.0: irq 17, io mem 0xfd6fe000
[    1.997006] xhci_hcd 0000:02:00.0: irq 44 for MSI/MSI-X
[    1.997012] xhci_hcd 0000:02:00.0: irq 45 for MSI/MSI-X
[    1.997016] xhci_hcd 0000:02:00.0: irq 46 for MSI/MSI-X
[    1.997020] xhci_hcd 0000:02:00.0: irq 47 for MSI/MSI-X
[    1.997024] xhci_hcd 0000:02:00.0: irq 48 for MSI/MSI-X
[    1.997029] xhci_hcd 0000:02:00.0: irq 49 for MSI/MSI-X
[    1.997033] xhci_hcd 0000:02:00.0: irq 50 for MSI/MSI-X
[    1.997197] xHCI xhci_add_endpoint called for root hub
[    1.997200] xHCI xhci_check_bandwidth called for root hub
[    1.997225] hub 8-0:1.0: USB hub found
[    1.997231] hub 8-0:1.0: 2 ports detected
[    1.997289] xhci_hcd 0000:02:00.0: xHCI Host Controller
[    1.997314] xhci_hcd 0000:02:00.0: new USB bus registered, assigned bus number 9
[    2.000101] usb 2-1: new high speed USB device number 2 using ehci_hcd
[    2.000462] xHCI xhci_add_endpoint called for root hub
[    2.000464] xHCI xhci_check_bandwidth called for root hub
[    2.000488] hub 9-0:1.0: USB hub found
[    2.000493] hub 9-0:1.0: 2 ports detected
[    2.000559] scsi0 : ahci
[    2.000981] scsi1 : ahci
[    2.001133] scsi2 : ahci
[    2.001222] scsi3 : ahci
[    2.001317] ata1: SATA max UDMA/133 abar m1024@0xfe02f000 port 0xfe02f100 irq 19
[    2.001320] ata2: SATA max UDMA/133 abar m1024@0xfe02f000 port 0xfe02f180 irq 19
[    2.001323] ata3: SATA max UDMA/133 abar m1024@0xfe02f000 port 0xfe02f200 irq 19
[    2.001326] ata4: SATA max UDMA/133 abar m1024@0xfe02f000 port 0xfe02f280 irq 19
[    2.001436] ahci 0000:05:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    2.005129] usbcore: registered new interface driver uas
[    2.006252] scsi4 : pata_atiixp
[    2.006306] scsi5 : pata_atiixp
[    2.006740] ata5: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xfa00 irq 14
[    2.006742] ata6: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xfa08 irq 15
[    2.020153] ahci 0000:05:00.0: AHCI 0001.0000 32 slots 2 ports 3 Gbps 0x3 impl SATA mode
[    2.020157] ahci 0000:05:00.0: flags: 64bit ncq pm led clo pmp pio slum part 
[    2.020164] ahci 0000:05:00.0: setting latency timer to 64
[    2.020463] scsi6 : ahci
[    2.020612] scsi7 : ahci
[    2.020820] ata7: SATA max UDMA/133 abar m8192@0xfdbfe000 port 0xfdbfe100 irq 17
[    2.020823] ata8: SATA max UDMA/133 abar m8192@0xfdbfe000 port 0xfdbfe180 irq 17
[    2.021166] pata_jmicron 0000:05:00.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    2.021212] pata_jmicron 0000:05:00.1: setting latency timer to 64
[    2.021451] scsi8 : pata_jmicron
[    2.021512] scsi9 : pata_jmicron
[    2.021539] ata9: PATA max UDMA/100 cmd 0xaf00 ctl 0xae00 bmdma 0xab00 irq 17
[    2.021541] ata10: PATA max UDMA/100 cmd 0xad00 ctl 0xac00 bmdma 0xab08 irq 17
[    2.068124] Refined TSC clocksource calibration: 2812.397 MHz.
[    2.068128] Switching to clocksource tsc
[    2.320129] ata4: SATA link down (SStatus 0 SControl 300)
[    2.320180] ata3: SATA link down (SStatus 0 SControl 300)
[    2.344104] ata7: SATA link down (SStatus 0 SControl 300)
[    2.344146] ata8: SATA link down (SStatus 0 SControl 300)
[    2.416081] usb 4-5: new low speed USB device number 2 using ohci_hcd
[    2.492087] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    2.492110] ata1: SATA link up 6.0 Gbps (SStatus 133 SControl 300)
[    2.492656] ata2.00: ATAPI: TSSTcorp CDDVDW SH-222AB, SB01, max UDMA/100
[    2.493455] ata2.00: configured for UDMA/100
[    2.495030] ata1.00: ATA-8: WDC WD10EALX-009BA0, 15.01H15, max UDMA/133
[    2.495033] ata1.00: 1953525168 sectors, multi 16: LBA48 NCQ (depth 31/32), AA
[    2.497148] ata1.00: configured for UDMA/133
[    2.497320] scsi 0:0:0:0: Direct-Access     ATA      WDC WD10EALX-009 15.0 PQ: 0 ANSI: 5
[    2.497443] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    2.497451] sd 0:0:0:0: [sda] 1953525168 512-byte logical blocks: (1.00 TB/931 GiB)
[    2.497482] sd 0:0:0:0: [sda] Write Protect is off
[    2.497488] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    2.497501] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.498053] scsi 1:0:0:0: CD-ROM            TSSTcorp CDDVDW SH-222AB  SB01 PQ: 0 ANSI: 5
[    2.500589] sr0: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
[    2.500592] cdrom: Uniform CD-ROM driver Revision: 3.20
[    2.500677] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    2.500745] sr 1:0:0:0: Attached scsi generic sg1 type 5
[    2.519963]  sda: sda1 < sda5 > sda2
[    2.520172] sd 0:0:0:0: [sda] Attached SCSI disk
[    2.636561] usbcore: registered new interface driver usbhid
[    2.636563] usbhid: USB HID core driver
[    2.668583] Initializing USB Mass Storage driver...
[    2.669198] scsi10 : usb-storage 1-2:1.3
[    2.669208] firewire_ohci 0000:04:0e.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[    2.669299] usbcore: registered new interface driver usb-storage
[    2.669300] USB Mass Storage support registered.
[    2.673363] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:12.0/usb4/4-5/4-5:1.0/input/input2
[    2.673439] logitech 0003:046D:C517.0001: input,hidraw0: USB HID v1.10 Keyboard [Logitech USB Receiver] on usb-0000:00:12.0-5/input0
[    2.681123] logitech 0003:046D:C517.0002: fixing up Logitech keyboard report descriptor
[    2.681537] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:12.0/usb4/4-5/4-5:1.1/input/input3
[    2.681640] logitech 0003:046D:C517.0002: input,hiddev0,hidraw1: USB HID v1.10 Mouse [Logitech USB Receiver] on usb-0000:00:12.0-5/input1
[    2.704091] usb 8-1: new high speed USB device number 2 using xhci_hcd
[    2.728177] firewire_ohci: Added fw-ohci device 0000:04:0e.0, OHCI v1.10, 4 IR + 8 IT contexts, quirks 0x2
[    2.732026] scsi11 : usb-storage 8-1:1.0
[    2.884048] EXT4-fs (sda2): INFO: recovery required on readonly filesystem
[    2.884051] EXT4-fs (sda2): write access will be enabled during recovery
[    3.228144] firewire_core: created device fw0: GUID 0000bf440050e549, S400
[    3.668691] scsi 10:0:0:0: Direct-Access     HP       Photosmart C5180 1.00 PQ: 0 ANSI: 2
[    3.735690] scsi 11:0:0:0: Direct-Access     WDC WD10 01FALS-00J7B0         PQ: 0 ANSI: 2
[    4.180234] sd 10:0:0:0: Attached scsi generic sg2 type 0
[    4.181607] sd 10:0:0:0: [sdb] Attached SCSI removable disk
[    4.200240] sd 11:0:0:0: Attached scsi generic sg3 type 0
[    4.200745] sd 11:0:0:0: [sdc] 1953525168 512-byte logical blocks: (1.00 TB/931 GiB)
[    4.202913] sd 11:0:0:0: [sdc] Write Protect is off
[    4.202916] sd 11:0:0:0: [sdc] Mode Sense: 38 00 00 00
[    4.205214] sd 11:0:0:0: [sdc] No Caching mode page present
[    4.205217] sd 11:0:0:0: [sdc] Assuming drive cache: write through
[    4.210287] sd 11:0:0:0: [sdc] No Caching mode page present
[    4.210289] sd 11:0:0:0: [sdc] Assuming drive cache: write through
[    5.517080] EXT4-fs (sda2): orphan cleanup on readonly fs
[    5.517088] EXT4-fs (sda2): ext4_orphan_cleanup: truncating inode 16515341 to 0 bytes
[    5.517136] EXT4-fs (sda2): ext4_orphan_cleanup: deleting unreferenced inode 14950904
[    5.517160] EXT4-fs (sda2): ext4_orphan_cleanup: deleting unreferenced inode 14950903
[    5.517184] EXT4-fs (sda2): ext4_orphan_cleanup: deleting unreferenced inode 14950881
[    5.517198] EXT4-fs (sda2): ext4_orphan_cleanup: deleting unreferenced inode 14950892
[    5.517212] EXT4-fs (sda2): ext4_orphan_cleanup: deleting unreferenced inode 14950857
[    5.517220] EXT4-fs (sda2): ext4_orphan_cleanup: deleting unreferenced inode 14950868
[    5.517228] EXT4-fs (sda2): ext4_orphan_cleanup: deleting unreferenced inode 14950860
[    5.517235] EXT4-fs (sda2): ext4_orphan_cleanup: deleting unreferenced inode 14950862
[    5.517243] EXT4-fs (sda2): ext4_orphan_cleanup: deleting unreferenced inode 14950707
[    5.517251] EXT4-fs (sda2): ext4_orphan_cleanup: deleting unreferenced inode 14950312
[    5.517259] EXT4-fs (sda2): ext4_orphan_cleanup: deleting unreferenced inode 23199813
[    5.517264] EXT4-fs (sda2): ext4_orphan_cleanup: deleting unreferenced inode 14950321
[    5.517272] EXT4-fs (sda2): ext4_orphan_cleanup: deleting unreferenced inode 14945976
[    5.517280] EXT4-fs (sda2): ext4_orphan_cleanup: deleting unreferenced inode 14949817
[    5.517287] EXT4-fs (sda2): ext4_orphan_cleanup: deleting unreferenced inode 14948500
[    5.517295] EXT4-fs (sda2): ext4_orphan_cleanup: deleting unreferenced inode 14948573
[    5.517303] EXT4-fs (sda2): ext4_orphan_cleanup: deleting unreferenced inode 14943124
[    5.517310] EXT4-fs (sda2): ext4_orphan_cleanup: deleting unreferenced inode 14943150
[    5.517318] EXT4-fs (sda2): ext4_orphan_cleanup: deleting unreferenced inode 14945974
[    5.517325] EXT4-fs (sda2): ext4_orphan_cleanup: deleting unreferenced inode 23199773
[    5.517332] EXT4-fs (sda2): 20 orphan inodes deleted
[    5.517334] EXT4-fs (sda2): 1 truncate cleaned up
[    5.517335] EXT4-fs (sda2): recovery complete
[    5.918341] EXT4-fs (sda2): mounted filesystem with ordered data mode. Opts: (null)
[    9.744823]  sdc: sdc1
[    9.750005] sd 11:0:0:0: [sdc] No Caching mode page present
[    9.750008] sd 11:0:0:0: [sdc] Assuming drive cache: write through
[    9.750010] sd 11:0:0:0: [sdc] Attached SCSI disk
[   18.755819] udevd[418]: starting version 173
[   18.789112] lp: driver loaded but no devices found
[   18.792053] wmi: Mapper loaded
[   18.806672] ACPI: resource piix4_smbus [io  0x0b00-0x0b07] conflicts with ACPI region SOR1 [io 0xb00-0xb0f]
[   18.806676] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[   18.807627] SP5100 TCO timer: SP5100 TCO WatchDog Timer Driver v0.01
[   18.807726] SP5100 TCO timer: mmio address 0xb8fe00 already in use
[   18.811179] nvidia: module license 'NVIDIA' taints kernel.
[   18.811183] Disabling lock debugging due to kernel taint
[   18.815321] MCE: In-kernel MCE decoding enabled.
[   18.816663] cfg80211: Calling CRDA to update world regulatory domain
[   18.817573] EDAC MC: Ver: 2.1.0
[   18.820405] AMD64 EDAC driver v3.4.0
[   18.821675] EDAC amd64: DRAM ECC disabled.
[   18.821685] EDAC amd64: ECC disabled in the BIOS or no ECC capability, module will not load.
[   18.821686]  Either enable ECC checking or force module loading by setting 'ecc_enable_override'.
[   18.821687]  (Note that use of the override may cause unknown side effects.)
[   18.837037] rtl8180 0000:04:06.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[   18.846720] HDA Intel 0000:00:14.2: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   18.859316] Adding 31996924k swap on /dev/sda5.  Priority:-1 extents:1 across:31996924k 
[   18.874103] nvidia 0000:01:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[   18.874112] nvidia 0000:01:00.0: setting latency timer to 64
[   18.874117] vgaarb: device changed decodes: PCI:0000:01:00.0,olddecodes=io+mem,decodes=none:owns=io+mem
[   18.874424] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  295.40  Thu Apr  5 21:37:00 PDT 2012
[   18.881447] cfg80211: World regulatory domain updated:
[   18.881450] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   18.881452] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   18.881454] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   18.881456] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   18.881458] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   18.881459] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   18.882096] type=1400 audit(1334593768.421:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=472 comm="apparmor_parser"
[   18.882123] type=1400 audit(1334593768.421:3): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=673 comm="apparmor_parser"
[   18.882437] type=1400 audit(1334593768.421:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=472 comm="apparmor_parser"
[   18.882461] type=1400 audit(1334593768.421:5): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=673 comm="apparmor_parser"
[   18.882641] type=1400 audit(1334593768.421:6): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=472 comm="apparmor_parser"
[   18.882668] type=1400 audit(1334593768.421:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=673 comm="apparmor_parser"
[   18.894739] hda_codec: ALC889: BIOS auto-probing.
[   18.908826] input: HDA ATI SB Headphone as /devices/pci0000:00/0000:00:14.2/sound/card0/input4
[   18.909014] HDA Intel 0000:01:00.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[   18.909017] hda_intel: Disabling MSI
[   18.909065] HDA Intel 0000:01:00.1: setting latency timer to 64
[   18.956970] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
[   18.956974] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[   18.956975] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
[   18.956978] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[   18.956979] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
[   18.956981] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[   18.956983] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
[   18.956984] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[   18.956986] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
[   18.956988] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[   18.956989] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
[   18.956991] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[   18.956993] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
[   18.956994] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[   18.956996] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
[   18.956998] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[   18.956999] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
[   18.957001] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[   18.957003] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
[   18.957005] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[   18.957006] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
[   18.957008] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[   18.957009] cfg80211: Updating information on frequency 2467 MHz for a 20 MHz width channel with regulatory rule:
[   18.957011] cfg80211: 2457000 KHz - 2482000 KHz @  KHz), (300 mBi, 2000 mBm)
[   18.957013] cfg80211: Updating information on frequency 2472 MHz for a 20 MHz width channel with regulatory rule:
[   18.957015] cfg80211: 2457000 KHz - 2482000 KHz @  KHz), (300 mBi, 2000 mBm)
[   18.957016] cfg80211: Updating information on frequency 2484 MHz for a 20 MHz width channel with regulatory rule:
[   18.957018] cfg80211: 2474000 KHz - 2494000 KHz @  KHz), (300 mBi, 2000 mBm)
[   18.959114] ieee80211 phy0: Selected rate control algorithm 'minstrel_ht'
[   18.959475] ieee80211 phy0: hwaddr 0014d1eb37e7, RTL8185vD + rtl8225z2
[   18.976388] udevd[429]: renamed network interface wlan0 to wlan1
[   19.099669] Linux video capture interface: v2.00
[   19.145604] EXT4-fs (sda2): re-mounted. Opts: errors=remount-ro,user_xattr
[   19.184996] init: Failed to spawn network-manager main process: unable to execute: No such file or directory
[   19.185463] init: modemmanager main process (1158) killed by TERM signal
[   19.198563] type=1400 audit(1334593768.737:8): apparmor="STATUS" operation="profile_load" name="/usr/lib/lightdm/lightdm-guest-session-wrapper" pid=1174 comm="apparmor_parser"
[   19.198689] type=1400 audit(1334593768.737:9): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=1175 comm="apparmor_parser"
[   19.199054] type=1400 audit(1334593768.737:10): apparmor="STATUS" operation="profile_load" name="/usr/lib/telepathy/mission-control-5" pid=1178 comm="apparmor_parser"
[   19.199069] type=1400 audit(1334593768.737:11): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=1175 comm="apparmor_parser"
[   19.312223] init: failsafe main process (1122) killed by TERM signal
[   19.312692] init: apport pre-start process (1225) terminated with status 1
[   19.316983] init: apport post-stop process (1247) terminated with status 1



```

---

### Post by roelforg on 2012-04-16
jjgalves... Is that you? </starwars>

But really, that log is from the current boot.
You need /var/log/dmesg.0
that one is from the prev. boot

---

### Post by 2F4U on 2012-04-16
I would think that if the computer doesn't crash during the boot, but later on, you would need /var/log/syslog.

---

### Post by roelforg on 2012-04-16
> **2F4U said:**
> I would think that if the computer doesn't crash during the boot, but later on, you would need /var/log/syslog.

I was thinking about overheating or hw issues...
Might be indeed a good idea to check the syslog for apps as well...

---

### Post by 2F4U on 2012-04-16
Besides overheating it may be worth checking that the RAM is working properly. Bad RAM is often involved if a computer suddenly crashes.

---

### Post by roelforg on 2012-04-16
> **2F4U said:**
> Besides overheating it may be worth checking that the RAM is working properly. Bad RAM is often involved if a computer suddenly crashes.
Good catch!

---

### Post by RJARRRPCGP on 2012-04-16
Looks like it may be logging out on you. Possibly low battery, if on a laptop.

A "TERM" signal is a graceful shutdown and it may have sent the "TERM" signal because of a low battery. 

And it appears possible that it can be configured to self-hibernate when the battery is low.

I dunno if it can be configured to do the same for high core temps.

---

### Post by roelforg on 2012-04-16
> **RJARRRPCGP said:**
> Looks like it may be logging out on you. Possibly low battery, if on a laptop.

A "TERM" signal is a graceful shutdown and it may have sent the "TERM" signal because of a low battery. 

And it appears possible that it can be configured to self-hibernate when the battery is low.

I dunno if it can be configured to do the same for high core temps.

My server is set to shutdown at a certain temp, you might be able to customize that depending on bios

---

### Post by cybergalvez on 2012-04-16
Hi all, thanks so far for the help.  I initally thought it was the memeory, so I spent some time the other day testing it and it appears good, although I only tested each stick for a couple of passes.

I will check the bio temp setting to see if that is set too low. 
FYI here are the computer specs (its a desktop)

MB GA-880GA-UD3H
AMD Phenom(tm) II X6 1055T
8 GB of Crutial

Also here is my syslog (attached)

---

### Post by Bobhuber on 2012-04-16
> **cybergalvez said:**
> Hi all, thanks so far for the help.  I initally thought it was the memeory, so I spent some time the other day testing it and it appears good, although I only tested each stick for a couple of passes.

I will check the bio temp setting to see if that is set too low. 
FYI here are the computer specs (its a desktop)

MB GA-880GA-UD3H
AMD Phenom(tm) II X6 1055T
8 GB of Crutial

Also here is my syslog (attached)
Looking at the above post (not the sys log)would suggest you have a problem with overclocking ??

---

### Post by RJARRRPCGP on 2012-04-16
> **roelforg said:**
> My server is set to shutdown at a certain temp, you might be able to customize that depending on bios

But, a BIOS shutdown will forcefully shutdown the PC (no chance for the OS to gracefully shutdown) and thus expect some lost work.

---

### Post by cybergalvez on 2012-04-16
> **Bobhuber said:**
> Looking at the above post (not the sys log)would suggest you have a problem with overclocking ??

Overclocking thats interesting, I have not overclocked the system at all. What from the post suggests overclocking?

---

### Post by cybergalvez on 2012-04-16
> **RJARRRPCGP said:**
> But, a BIOS shutdown will forcefully shutdown the PC (no chance for the OS to gracefully shutdown) and thus expect some lost work.

I've been monitoring the temp pretty closely as I attempt to do the full backup again, and my CPU temp never gets above 41C so I don't think it's an issue with overheatig. 

even if the backup succeeds I will most likely run the memory check all night long to see if I get any errors during the night

---

### Post by RJARRRPCGP on 2012-04-16
> **cybergalvez said:**
> Overclocking thats interesting, I have not overclocked the system at all. What from the post suggests overclocking?

Did you get a kernel panic. Did the caps lock and scroll lock lights on the keyboard start blinking when it froze?

---

### Post by Bobhuber on 2012-04-16
> **cybergalvez said:**
> Overclocking thats interesting, I have not overclocked the system at all. What from the post suggests overclocking?
Because you are getting both firmware and memory errors typical of what I have seen while messing with my system. If your not overclocking check your memory and cpu voltage settings in the bios . My default bios settings were originally too high which caused all kinds of problems under load even at stock frequencies. Just some things to look at. Hope it helps.

---

### Post by cybergalvez on 2012-04-17
> **RJARRRPCGP said:**
> Did you get a kernel panic. Did the caps lock and scroll lock lights on the keyboard start blinking when it froze?

no  kermel panic that I saw, on the keyboard nothing, this stupid keyboard doesn't ahve lights on it so I wouldn't see them anyway.

---

### Post by cybergalvez on 2012-04-17
> **Bobhuber said:**
> Because you are getting both firmware and memory errors typical of what I have seen while messing with my system. If your not overclocking check your memory and cpu voltage settings in the bios . My default bios settings were originally too high which caused all kinds of problems under load even at stock frequencies. Just some things to look at. Hope it helps.

Which lines point to memory and firmware issues? Any way I booted into Memtest86 last night and left if running, this morning it looks like it was frozen and it had riacked up 60 errors. Going to call Crutial this morning to see what they say. I think I will also check the memory setting on the MB, just to cmake sure too. They are all set to auto.

---

### Post by davidvandoren on 2012-04-17
I had a similar problem with all different versions of linux with my msi motherboard. 

After disabling the on-board HD audio chip in the BIOS all the crashes, logouts,restarts and application snapping have vanished completely for over a month now. 

Try disabling your audio card in the BIOS and see if it makes a difference. 

I had a problem with the Realtek ALC889 audio codec which I kind of noticed something in your file,too.

---

### Post by cybergalvez on 2012-04-17
Called corsair (Thought I had bought crucial it is actually corsair) and I am going to RMA the memeory. I'll update everyone once I get the new memory and give it a test run

---

