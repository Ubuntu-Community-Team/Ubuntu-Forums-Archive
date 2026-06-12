---
title: "Reduce boot time"
date: 2011-10-06
forum: General Help
---

### Post by viraf87 on 2011-10-06
Hi guys, I don't know if anyone will be able to help but my boot time is fairly slow (~70s).  I've trawled the forums and have followed many of the tips however cannot reduce it.  I've read that some people have boot times of ~15s but I assume that's with an SSD.

I've just got a normal HDD and I'm sure that 10.04 and 10.10 used to boot quicker.  Anyway, for those interested here's my dmesg and bootchart.  

Hopefully someone can help

Viraf

```
viraf@viraf-desktop:~$ dmesg
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.38-11-generic (buildd@allspice) (gcc version 4.5.2 (Ubuntu/Linaro 4.5.2-8ubuntu4) ) #50-Ubuntu SMP Mon Sep 12 21:17:25 UTC 2011 (Ubuntu 2.6.38-11.50-generic 2.6.38.8)
[    0.000000] Command line: root=UUID=1d040738-a48a-4ecb-90b3-6161f5401802 ro quiet splash vga=769 
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009ec00 (usable)
[    0.000000]  BIOS-e820: 000000000009ec00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e3000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 00000000cff90000 (usable)
[    0.000000]  BIOS-e820: 00000000cff90000 - 00000000cffa8000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000cffa8000 - 00000000cffe0000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000cffe0000 - 00000000cffee000 (reserved)
[    0.000000]  BIOS-e820: 00000000cfff0000 - 00000000d0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fef00000 (reserved)
[    0.000000]  BIOS-e820: 00000000fff00000 - 0000000100000000 (reserved)
[    0.000000]  BIOS-e820: 0000000100000000 - 0000000130000000 (usable)
[    0.000000] NX (Execute Disable) protection: active
[    0.000000] DMI present.
[    0.000000] DMI: System manufacturer System Product Name/M4N78, BIOS 0803    06/09/2009
[    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
[    0.000000] e820 remove range: 00000000000a0000 - 0000000000100000 (usable)
[    0.000000] No AGP bridge found
[    0.000000] last_pfn = 0x130000 max_arch_pfn = 0x400000000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-EFFFF uncachable
[    0.000000]   F0000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000000 mask FFFF80000000 write-back
[    0.000000]   1 base 000080000000 mask FFFFC0000000 write-back
[    0.000000]   2 base 0000C0000000 mask FFFFF0000000 write-back
[    0.000000]   3 disabled
[    0.000000]   4 disabled
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] TOM2: 0000000130000000 aka 4864M
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] e820 update range: 00000000d0000000 - 0000000100000000 (usable) ==> (reserved)
[    0.000000] last_pfn = 0xcff90 max_arch_pfn = 0x400000000
[    0.000000] found SMP MP-table at [ffff8800000ff780] ff780
[    0.000000] initial memory mapped : 0 - 20000000
[    0.000000] Using GB pages for direct mapping
[    0.000000] init_memory_mapping: 0000000000000000-00000000cff90000
[    0.000000]  0000000000 - 00c0000000 page 1G
[    0.000000]  00c0000000 - 00cfe00000 page 2M
[    0.000000]  00cfe00000 - 00cff90000 page 4k
[    0.000000] kernel direct mapping tables up to cff90000 @ 1fffd000-20000000
[    0.000000] init_memory_mapping: 0000000100000000-0000000130000000
[    0.000000]  0100000000 - 0130000000 page 2M
[    0.000000] kernel direct mapping tables up to 130000000 @ cff8e000-cff90000
[    0.000000] RAMDISK: 37362000 - 37ff0000
[    0.000000] ACPI: RSDP 00000000000fb830 00014 (v00 ACPIAM)
[    0.000000] ACPI: RSDT 00000000cff90000 00044 (v01 060909 RSDT1732 20090609 MSFT 00000097)
[    0.000000] ACPI: FACP 00000000cff90200 00084 (v01 060909 FACP1732 20090609 MSFT 00000097)
[    0.000000] ACPI: DSDT 00000000cff90450 09D33 (v01  A1257 A1257000 00000000 INTL 20060113)
[    0.000000] ACPI: FACS 00000000cffa8000 00040
[    0.000000] ACPI: APIC 00000000cff90390 00080 (v01 060909 APIC1732 20090609 MSFT 00000097)
[    0.000000] ACPI: MCFG 00000000cff90410 0003C (v01 060909 OEMMCFG  20090609 MSFT 00000097)
[    0.000000] ACPI: OEMB 00000000cffa8040 0007A (v01 060909 OEMB1732 20090609 MSFT 00000097)
[    0.000000] ACPI: HPET 00000000cff9a190 00038 (v01 060909 OEMHPET0 20090609 MSFT 00000097)
[    0.000000] ACPI: INFO 00000000cffa80c0 00124 (v01 060909 AMDINFO  20090609 MSFT 00000097)
[    0.000000] ACPI: NVHD 00000000cffa81f0 00284 (v01 060909  NVHDCP  20090609 MSFT 00000097)
[    0.000000] ACPI: SSDT 00000000cff9a1d0 002B4 (v01 A M I  POWERNOW 00000001 AMD  00000001)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] Scanning NUMA topology in Northbridge 24
[    0.000000] No NUMA configuration found
[    0.000000] Faking a node at 0000000000000000-0000000130000000
[    0.000000] Initmem setup node 0 0000000000000000-0000000130000000
[    0.000000]   NODE_DATA [000000012fffb000 - 000000012fffffff]
[    0.000000]  [ffffea0000000000-ffffea00043fffff] PMD -> [ffff88012be00000-ffff88012f7fffff] on node 0
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000010 -> 0x00001000
[    0.000000]   DMA32    0x00001000 -> 0x00100000
[    0.000000]   Normal   0x00100000 -> 0x00130000
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[3] active PFN ranges
[    0.000000]     0: 0x00000010 -> 0x0000009e
[    0.000000]     0: 0x00000100 -> 0x000cff90
[    0.000000]     0: 0x00100000 -> 0x00130000
[    0.000000] On node 0 totalpages: 1048350
[    0.000000]   DMA zone: 56 pages used for memmap
[    0.000000]   DMA zone: 6 pages reserved
[    0.000000]   DMA zone: 3920 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 14280 pages used for memmap
[    0.000000]   DMA32 zone: 833480 pages, LIFO batch:31
[    0.000000]   Normal zone: 2688 pages used for memmap
[    0.000000]   Normal zone: 193920 pages, LIFO batch:31
[    0.000000] ACPI: PM-Timer IO Port: 0x508
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x82] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x83] disabled)
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 17, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 14 global_irq 14 high edge)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 15 global_irq 15 high edge)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] ACPI: IRQ14 used by override.
[    0.000000] ACPI: IRQ15 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x10de8201 base: 0xfed00000
[    0.000000] SMP: Allowing 4 CPUs, 2 hotplug CPUs
[    0.000000] nr_irqs_gsi: 40
[    0.000000] PM: Registered nosave memory: 000000000009e000 - 000000000009f000
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e3000
[    0.000000] PM: Registered nosave memory: 00000000000e3000 - 0000000000100000
[    0.000000] PM: Registered nosave memory: 00000000cff90000 - 00000000cffa8000
[    0.000000] PM: Registered nosave memory: 00000000cffa8000 - 00000000cffe0000
[    0.000000] PM: Registered nosave memory: 00000000cffe0000 - 00000000cffee000
[    0.000000] PM: Registered nosave memory: 00000000cffee000 - 00000000cfff0000
[    0.000000] PM: Registered nosave memory: 00000000cfff0000 - 00000000d0000000
[    0.000000] PM: Registered nosave memory: 00000000d0000000 - 00000000fec00000
[    0.000000] PM: Registered nosave memory: 00000000fec00000 - 00000000fec01000
[    0.000000] PM: Registered nosave memory: 00000000fec01000 - 00000000fee00000
[    0.000000] PM: Registered nosave memory: 00000000fee00000 - 00000000fef00000
[    0.000000] PM: Registered nosave memory: 00000000fef00000 - 00000000fff00000
[    0.000000] PM: Registered nosave memory: 00000000fff00000 - 0000000100000000
[    0.000000] Allocating PCI resources starting at d0000000 (gap: d0000000:2ec00000)
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] setup_percpu: NR_CPUS:256 nr_cpumask_bits:256 nr_cpu_ids:4 nr_node_ids:1
[    0.000000] PERCPU: Embedded 28 pages/cpu @ffff8800cfc00000 s84416 r8192 d22080 u524288
[    0.000000] pcpu-alloc: s84416 r8192 d22080 u524288 alloc=1*2097152
[    0.000000] pcpu-alloc: [0] 0 1 2 3 
[    0.000000] Built 1 zonelists in Node order, mobility grouping on.  Total pages: 1031320
[    0.000000] Policy zone: Normal
[    0.000000] Kernel command line: root=UUID=1d040738-a48a-4ecb-90b3-6161f5401802 ro quiet splash vga=769 
[    0.000000] PID hash table entries: 4096 (order: 3, 32768 bytes)
[    0.000000] Checking aperture...
[    0.000000] No AGP bridge found
[    0.000000] Node 0: aperture @ 900000000 size 32 MB
[    0.000000] Aperture beyond 4GB. Ignoring.
[    0.000000] Your BIOS doesn't leave a aperture memory hole
[    0.000000] Please enable the IOMMU option in the BIOS setup
[    0.000000] This costs you 64 MB of RAM
[    0.000000] Mapping aperture over 65536 KB of RAM @ c4000000
[    0.000000] PM: Registered nosave memory: 00000000c4000000 - 00000000c8000000
[    0.000000] Memory: 3975668k/4980736k available (5943k kernel code, 787336k absent, 217732k reserved, 5015k data, 956k init)
[    0.000000] SLUB: Genslabs=15, HWalign=64, Order=0-3, MinObjects=0, CPUs=4, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000] 	RCU dyntick-idle grace-period acceleration is enabled.
[    0.000000] 	RCU-based detection of stalled CPUs is disabled.
[    0.000000] NR_IRQS:16640 nr_irqs:712 16
[    0.000000] spurious 8259A interrupt: IRQ7.
[    0.000000] Console: colour dummy device 80x25
[    0.000000] console [tty0] enabled
[    0.000000] allocated 41943040 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] hpet clockevent registered
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 2800.057 MHz processor.
[    0.010003] Calibrating delay loop (skipped), value calculated using timer frequency.. 5600.11 BogoMIPS (lpj=28000570)
[    0.010007] pid_max: default: 32768 minimum: 301
[    0.010030] Security Framework initialized
[    0.010045] AppArmor: AppArmor initialized
[    0.010046] Yama: becoming mindful.
[    0.010401] Dentry cache hash table entries: 524288 (order: 10, 4194304 bytes)
[    0.011880] Inode-cache hash table entries: 262144 (order: 9, 2097152 bytes)
[    0.012542] Mount-cache hash table entries: 256
[    0.012662] Initializing cgroup subsys ns
[    0.012665] ns_cgroup deprecated: consider using the 'clone_children' flag without the ns_cgroup.
[    0.012667] Initializing cgroup subsys cpuacct
[    0.012671] Initializing cgroup subsys memory
[    0.012679] Initializing cgroup subsys devices
[    0.012681] Initializing cgroup subsys freezer
[    0.012683] Initializing cgroup subsys net_cls
[    0.012684] Initializing cgroup subsys blkio
[    0.012713] tseg: 0000000000
[    0.012727] CPU: Physical Processor ID: 0
[    0.012728] CPU: Processor Core ID: 0
[    0.012730] mce: CPU supports 6 MCE banks
[    0.012739] using C1E aware idle routine
[    0.014159] ACPI: Core revision 20110112
[    0.022427] ftrace: allocating 24328 entries in 96 pages
[    0.028762] Setting APIC routing to flat
[    0.029232] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.129257] CPU0: AMD Athlon(tm) 7850 Dual-Core Processor stepping 03
[    0.130000] Performance Events: AMD PMU driver.
[    0.130000] ... version:                0
[    0.130000] ... bit width:              48
[    0.130000] ... generic registers:      4
[    0.130000] ... value mask:             0000ffffffffffff
[    0.130000] ... max period:             00007fffffffffff
[    0.130000] ... fixed-purpose events:   0
[    0.130000] ... event mask:             000000000000000f
[    0.130000] Booting Node   0, Processors  #1
[    0.290009] Brought up 2 CPUs
[    0.290011] Total of 2 processors activated (11200.11 BogoMIPS).
[    0.290779] devtmpfs: initialized
[    0.290797] print_constraints: dummy: 
[    0.290854] Time: 19:32:45  Date: 10/06/11
[    0.290887] NET: Registered protocol family 16
[    0.290914] Trying to unpack rootfs image as initramfs...
[    0.290980] node 0 link 0: io port [1000, ffffff]
[    0.290982] node 0 link 0: io port [1000, 1fff]
[    0.290984] TOM: 00000000d0000000 aka 3328M
[    0.290986] Fam 10h mmconf [e0000000, efffffff]
[    0.290987] node 0 link 0: mmio [e0000000, efffffff] ==> none
[    0.290990] node 0 link 0: mmio [a0000, bffff]
[    0.290992] node 0 link 0: mmio [d0000000, fe0bffff] ==> [d0000000, dfffffff] and [f0000000, fe0bffff]
[    0.290996] TOM2: 0000000130000000 aka 4864M
[    0.290998] bus: [00, 07] on node 0 link 0
[    0.291000] bus: 00 index 0 [io  0x0000-0xffff]
[    0.291002] bus: 00 index 1 [mem 0x000a0000-0x000bffff]
[    0.291003] bus: 00 index 2 [mem 0xd0000000-0xdfffffff]
[    0.291005] bus: 00 index 3 [mem 0xf0000000-0xffffffff]
[    0.291006] bus: 00 index 4 [mem 0x130000000-0xfcffffffff]
[    0.291014] Extended Config Space enabled on 1 nodes
[    0.291024] ACPI: bus type pci registered
[    0.291086] PCI: MMCONFIG for domain 0000 [bus 00-ff] at [mem 0xe0000000-0xefffffff] (base 0xe0000000)
[    0.291089] PCI: not using MMCONFIG
[    0.291090] PCI: Using configuration type 1 for base access
[    0.291091] PCI: Using configuration type 1 for extended access
[    0.300274] bio: create slab <bio-0> at 0
[    0.301479] ACPI: EC: Look up EC in DSDT
[    0.302846] ACPI: Executed 1 blocks of module-level executable AML code
[    0.420432] ACPI: Interpreter enabled
[    0.420436] ACPI: (supports S0 S1 S3 S4 S5)
[    0.420453] ACPI: Using IOAPIC for interrupt routing
[    0.420473] PCI: MMCONFIG for domain 0000 [bus 00-ff] at [mem 0xe0000000-0xefffffff] (base 0xe0000000)
[    0.421551] PCI: MMCONFIG at [mem 0xe0000000-0xefffffff] reserved in ACPI motherboard resources
[    0.446764] ACPI: No dock devices found.
[    0.446767] HEST: Table not found.
[    0.446771] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
[    0.446933] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-ff])
[    0.447085] pci_root PNP0A03:00: host bridge window [io  0x0000-0x0cf7]
[    0.447087] pci_root PNP0A03:00: host bridge window [io  0x0d00-0xffff]
[    0.447089] pci_root PNP0A03:00: host bridge window [mem 0x000a0000-0x000bffff]
[    0.447091] pci_root PNP0A03:00: host bridge window [mem 0x000d0000-0x000dffff]
[    0.447093] pci_root PNP0A03:00: host bridge window [mem 0xd0000000-0xdfffffff]
[    0.447095] pci_root PNP0A03:00: host bridge window [mem 0xf0000000-0xfebfffff]
[    0.447132] pci 0000:00:00.0: [10de:0754] type 0 class 0x000500
[    0.447353] pci 0000:00:01.0: [10de:075c] type 0 class 0x000601
[    0.447360] pci 0000:00:01.0: reg 10: [io  0x0900-0x09ff]
[    0.447395] pci 0000:00:01.1: [10de:0752] type 0 class 0x000c05
[    0.447406] pci 0000:00:01.1: reg 10: [io  0x0e00-0x0e3f]
[    0.447422] pci 0000:00:01.1: reg 20: [io  0x0600-0x063f]
[    0.447427] pci 0000:00:01.1: reg 24: [io  0x0700-0x073f]
[    0.447448] pci 0000:00:01.1: PME# supported from D3hot D3cold
[    0.447453] pci 0000:00:01.1: PME# disabled
[    0.447465] pci 0000:00:01.2: [10de:0751] type 0 class 0x000500
[    0.447511] pci 0000:00:01.3: [10de:0753] type 0 class 0x000b40
[    0.447528] pci 0000:00:01.3: reg 10: [mem 0xfbd80000-0xfbdfffff]
[    0.447633] pci 0000:00:01.4: [10de:0568] type 0 class 0x000500
[    0.447701] pci 0000:00:02.0: [10de:077b] type 0 class 0x000c03
[    0.447709] pci 0000:00:02.0: reg 10: [mem 0xfbd7e000-0xfbd7efff]
[    0.447741] pci 0000:00:02.0: supports D1 D2
[    0.447742] pci 0000:00:02.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.447745] pci 0000:00:02.0: PME# disabled
[    0.447756] pci 0000:00:02.1: [10de:077c] type 0 class 0x000c03
[    0.447767] pci 0000:00:02.1: reg 10: [mem 0xfbd7fc00-0xfbd7fcff]
[    0.447802] pci 0000:00:02.1: supports D1 D2
[    0.447804] pci 0000:00:02.1: PME# supported from D0 D1 D2 D3hot D3cold
[    0.447807] pci 0000:00:02.1: PME# disabled
[    0.447824] pci 0000:00:04.0: [10de:077d] type 0 class 0x000c03
[    0.447832] pci 0000:00:04.0: reg 10: [mem 0xfbd7d000-0xfbd7dfff]
[    0.447863] pci 0000:00:04.0: supports D1 D2
[    0.447865] pci 0000:00:04.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.447868] pci 0000:00:04.0: PME# disabled
[    0.447879] pci 0000:00:04.1: [10de:077e] type 0 class 0x000c03
[    0.447889] pci 0000:00:04.1: reg 10: [mem 0xfbd7f800-0xfbd7f8ff]
[    0.447924] pci 0000:00:04.1: supports D1 D2
[    0.447926] pci 0000:00:04.1: PME# supported from D0 D1 D2 D3hot D3cold
[    0.447929] pci 0000:00:04.1: PME# disabled
[    0.447946] pci 0000:00:06.0: [10de:0759] type 0 class 0x000101
[    0.447969] pci 0000:00:06.0: reg 20: [io  0xffa0-0xffaf]
[    0.447996] pci 0000:00:07.0: [10de:0774] type 0 class 0x000403
[    0.448005] pci 0000:00:07.0: reg 10: [mem 0xfbd78000-0xfbd7bfff]
[    0.448036] pci 0000:00:07.0: PME# supported from D3hot D3cold
[    0.448039] pci 0000:00:07.0: PME# disabled
[    0.448049] pci 0000:00:08.0: [10de:075a] type 1 class 0x000604
[    0.448085] pci 0000:00:09.0: [10de:0ad0] type 0 class 0x000101
[    0.448095] pci 0000:00:09.0: reg 10: [io  0xd480-0xd487]
[    0.448099] pci 0000:00:09.0: reg 14: [io  0xd400-0xd403]
[    0.448103] pci 0000:00:09.0: reg 18: [io  0xd080-0xd087]
[    0.448107] pci 0000:00:09.0: reg 1c: [io  0xd000-0xd003]
[    0.448111] pci 0000:00:09.0: reg 20: [io  0xcc00-0xcc0f]
[    0.448116] pci 0000:00:09.0: reg 24: [mem 0xfbd76000-0xfbd77fff]
[    0.448142] pci 0000:00:0a.0: [10de:0760] type 0 class 0x000200
[    0.448152] pci 0000:00:0a.0: reg 10: [mem 0xfbd7c000-0xfbd7cfff]
[    0.448157] pci 0000:00:0a.0: reg 14: [io  0xc880-0xc887]
[    0.448161] pci 0000:00:0a.0: reg 18: [mem 0xfbd7f400-0xfbd7f4ff]
[    0.448165] pci 0000:00:0a.0: reg 1c: [mem 0xfbd7f000-0xfbd7f00f]
[    0.448188] pci 0000:00:0a.0: supports D1 D2
[    0.448190] pci 0000:00:0a.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.448194] pci 0000:00:0a.0: PME# disabled
[    0.448248] pci 0000:00:10.0: [10de:0778] type 1 class 0x000604
[    0.448416] pci 0000:00:10.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.448423] pci 0000:00:10.0: PME# disabled
[    0.448507] pci 0000:00:12.0: [10de:075b] type 1 class 0x000604
[    0.448674] pci 0000:00:12.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.448681] pci 0000:00:12.0: PME# disabled
[    0.448763] pci 0000:00:13.0: [10de:077a] type 1 class 0x000604
[    0.448930] pci 0000:00:13.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.448937] pci 0000:00:13.0: PME# disabled
[    0.448982] pci 0000:00:18.0: [1022:1200] type 0 class 0x000600
[    0.448998] pci 0000:00:18.1: [1022:1201] type 0 class 0x000600
[    0.449010] pci 0000:00:18.2: [1022:1202] type 0 class 0x000600
[    0.449022] pci 0000:00:18.3: [1022:1203] type 0 class 0x000600
[    0.449036] pci 0000:00:18.4: [1022:1204] type 0 class 0x000600
[    0.449084] pci 0000:01:08.0: [11c1:5811] type 0 class 0x000c00
[    0.449096] pci 0000:01:08.0: reg 10: [mem 0xfbeff000-0xfbefffff]
[    0.449142] pci 0000:01:08.0: supports D1 D2
[    0.449144] pci 0000:01:08.0: PME# supported from D0 D1 D2 D3hot
[    0.449147] pci 0000:01:08.0: PME# disabled
[    0.449173] pci 0000:00:08.0: PCI bridge to [bus 01-01] (subtractive decode)
[    0.449176] pci 0000:00:08.0:   bridge window [io  0xf000-0x0000] (disabled)
[    0.449179] pci 0000:00:08.0:   bridge window [mem 0xfbe00000-0xfbefffff]
[    0.449183] pci 0000:00:08.0:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    0.449185] pci 0000:00:08.0:   bridge window [io  0x0000-0x0cf7] (subtractive decode)
[    0.449187] pci 0000:00:08.0:   bridge window [io  0x0d00-0xffff] (subtractive decode)
[    0.449189] pci 0000:00:08.0:   bridge window [mem 0x000a0000-0x000bffff] (subtractive decode)
[    0.449191] pci 0000:00:08.0:   bridge window [mem 0x000d0000-0x000dffff] (subtractive decode)
[    0.449193] pci 0000:00:08.0:   bridge window [mem 0xd0000000-0xdfffffff] (subtractive decode)
[    0.449195] pci 0000:00:08.0:   bridge window [mem 0xf0000000-0xfebfffff] (subtractive decode)
[    0.449352] pci 0000:02:00.0: [1002:9442] type 0 class 0x000300
[    0.449364] pci 0000:02:00.0: reg 10: [mem 0xd0000000-0xdfffffff 64bit pref]
[    0.449373] pci 0000:02:00.0: reg 18: [mem 0xfbfe0000-0xfbfeffff 64bit]
[    0.449379] pci 0000:02:00.0: reg 20: [io  0xe800-0xe8ff]
[    0.449389] pci 0000:02:00.0: reg 30: [mem 0xfbfc0000-0xfbfdffff pref]
[    0.449404] pci 0000:02:00.0: supports D1 D2
[    0.449419] pci 0000:02:00.1: [1002:aa30] type 0 class 0x000403
[    0.449430] pci 0000:02:00.1: reg 10: [mem 0xfbffc000-0xfbffffff 64bit]
[    0.449465] pci 0000:02:00.1: supports D1 D2
[    0.460020] pci 0000:00:10.0: PCI bridge to [bus 02-02]
[    0.460033] pci 0000:00:10.0:   bridge window [io  0xe000-0xefff]
[    0.460041] pci 0000:00:10.0:   bridge window [mem 0xfbf00000-0xfbffffff]
[    0.460054] pci 0000:00:10.0:   bridge window [mem 0xd0000000-0xdfffffff 64bit pref]
[    0.460206] pci 0000:00:12.0: PCI bridge to [bus 03-03]
[    0.460219] pci 0000:00:12.0:   bridge window [io  0xf000-0x0000] (disabled)
[    0.460227] pci 0000:00:12.0:   bridge window [mem 0xfff00000-0x000fffff] (disabled)
[    0.460240] pci 0000:00:12.0:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    0.460392] pci 0000:00:13.0: PCI bridge to [bus 04-04]
[    0.460405] pci 0000:00:13.0:   bridge window [io  0xf000-0x0000] (disabled)
[    0.460412] pci 0000:00:13.0:   bridge window [mem 0xfff00000-0x000fffff] (disabled)
[    0.460425] pci 0000:00:13.0:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    0.460465] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.460648] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P1._PRT]
[    0.460704] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.MXR0._PRT]
[    0.460734] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.BR12._PRT]
[    0.460759] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.BR13._PRT]
[    0.460866]  pci0000:00: Requesting ACPI _OSC control (0x1d)
[    0.466840] ACPI: PCI Interrupt Link [LNKA] (IRQs 16 17 18 19) *0, disabled.
[    0.466914] ACPI: PCI Interrupt Link [LNKB] (IRQs 16 17 18 19) *0, disabled.
[    0.466987] ACPI: PCI Interrupt Link [LNKC] (IRQs 16 17 18 19) *10
[    0.467061] ACPI: PCI Interrupt Link [LNKD] (IRQs 16 17 18 19) *0, disabled.
[    0.467133] ACPI: PCI Interrupt Link [LN0A] (IRQs 16 17 18 19) *10
[    0.467205] ACPI: PCI Interrupt Link [LN0B] (IRQs 16 17 18 19) *11
[    0.467276] ACPI: PCI Interrupt Link [LN0C] (IRQs 16 17 18 19) *0, disabled.
[    0.467347] ACPI: PCI Interrupt Link [LN0D] (IRQs 16 17 18 19) *0, disabled.
[    0.467417] ACPI: PCI Interrupt Link [LN1A] (IRQs 16 17 18 19) *0, disabled.
[    0.467488] ACPI: PCI Interrupt Link [LN1B] (IRQs 16 17 18 19) *0, disabled.
[    0.467559] ACPI: PCI Interrupt Link [LN1C] (IRQs 16 17 18 19) *0, disabled.
[    0.467629] ACPI: PCI Interrupt Link [LN1D] (IRQs 16 17 18 19) *0, disabled.
[    0.467701] ACPI: PCI Interrupt Link [LN2A] (IRQs 16 17 18 19) *11
[    0.467772] ACPI: PCI Interrupt Link [LN2B] (IRQs 16 17 18 19) *0, disabled.
[    0.467843] ACPI: PCI Interrupt Link [LN2C] (IRQs 16 17 18 19) *0, disabled.
[    0.467914] ACPI: PCI Interrupt Link [LN2D] (IRQs 16 17 18 19) *0, disabled.
[    0.467986] ACPI: PCI Interrupt Link [LN3A] (IRQs 16 17 18 19) *15
[    0.468057] ACPI: PCI Interrupt Link [LN3B] (IRQs 16 17 18 19) *0, disabled.
[    0.468128] ACPI: PCI Interrupt Link [LN3C] (IRQs 16 17 18 19) *0, disabled.
[    0.468199] ACPI: PCI Interrupt Link [LN3D] (IRQs 16 17 18 19) *0, disabled.
[    0.468270] ACPI: PCI Interrupt Link [LN4A] (IRQs 16 17 18 19) *0, disabled.
[    0.468340] ACPI: PCI Interrupt Link [LN4B] (IRQs 16 17 18 19) *0, disabled.
[    0.468412] ACPI: PCI Interrupt Link [LN4C] (IRQs 16 17 18 19) *0, disabled.
[    0.468485] ACPI: PCI Interrupt Link [LN4D] (IRQs 16 17 18 19) *0, disabled.
[    0.468560] ACPI: PCI Interrupt Link [LN5A] (IRQs 16 17 18 19) *0, disabled.
[    0.468632] ACPI: PCI Interrupt Link [LN5B] (IRQs 16 17 18 19) *0, disabled.
[    0.468703] ACPI: PCI Interrupt Link [LN5C] (IRQs 16 17 18 19) *0, disabled.
[    0.468775] ACPI: PCI Interrupt Link [LN5D] (IRQs 16 17 18 19) *0, disabled.
[    0.468849] ACPI: PCI Interrupt Link [LN6A] (IRQs 16 17 18 19) *0, disabled.
[    0.468923] ACPI: PCI Interrupt Link [LN6B] (IRQs 16 17 18 19) *0, disabled.
[    0.468994] ACPI: PCI Interrupt Link [LN6C] (IRQs 16 17 18 19) *0, disabled.
[    0.469066] ACPI: PCI Interrupt Link [LN6D] (IRQs 16 17 18 19) *0, disabled.
[    0.469137] ACPI: PCI Interrupt Link [LN7A] (IRQs 16 17 18 19) *0, disabled.
[    0.469209] ACPI: PCI Interrupt Link [LN7B] (IRQs 16 17 18 19) *0, disabled.
[    0.469280] ACPI: PCI Interrupt Link [LN7C] (IRQs 16 17 18 19) *0, disabled.
[    0.469352] ACPI: PCI Interrupt Link [LN7D] (IRQs 16 17 18 19) *0, disabled.
[    0.469425] ACPI: PCI Interrupt Link [LUB0] (IRQs 20 21 22 23) *10
[    0.469498] ACPI: PCI Interrupt Link [LUB2] (IRQs 20 21 22 23) *15
[    0.469571] ACPI: PCI Interrupt Link [LMAC] (IRQs 20 21 22 23) *10
[    0.469644] ACPI: PCI Interrupt Link [LAZA] (IRQs 20 21 22 23) *15
[    0.469716] ACPI: PCI Interrupt Link [SGRU] (IRQs 20 21 22 23) *0, disabled.
[    0.469790] ACPI: PCI Interrupt Link [LSMB] (IRQs 20 21 22 23) *11
[    0.469862] ACPI: PCI Interrupt Link [LPMU] (IRQs 20 21 22 23) *10
[    0.469935] ACPI: PCI Interrupt Link [LSA0] (IRQs 20 21 22 23) *5
[    0.470047] ACPI: PCI Interrupt Link [LATA] (IRQs 20 21 22 23) *0, disabled.
[    0.470121] ACPI: PCI Interrupt Link [UB11] (IRQs 20 21 22 23) *11
[    0.470200] ACPI: PCI Interrupt Link [UB12] (IRQs 20 21 22 23) *10
[    0.470311] vgaarb: device added: PCI:0000:02:00.0,decodes=io+mem,owns=io+mem,locks=none
[    0.470313] vgaarb: loaded
[    0.470459] SCSI subsystem initialized
[    0.470519] libata version 3.00 loaded.
[    0.470553] usbcore: registered new interface driver usbfs
[    0.470561] usbcore: registered new interface driver hub
[    0.470584] usbcore: registered new device driver usb
[    0.470669] wmi: Mapper loaded
[    0.470671] PCI: Using ACPI for IRQ routing
[    0.470674] PCI: pci_cache_line_size set to 64 bytes
[    0.470750] reserve RAM buffer: 000000000009ec00 - 000000000009ffff 
[    0.470752] reserve RAM buffer: 00000000cff90000 - 00000000cfffffff 
[    0.470833] NetLabel: Initializing
[    0.470834] NetLabel:  domain hash size = 128
[    0.470835] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.470845] NetLabel:  unlabeled traffic allowed by default
[    0.470874] HPET: 3 timers in total, 0 timers will be used for per-cpu timer
[    0.470879] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 31
[    0.470883] hpet0: 3 comparators, 32-bit 25.000000 MHz counter
[    0.490045] Switching to clocksource hpet
[    0.495650] AppArmor: AppArmor Filesystem Enabled
[    0.495681] pnp: PnP ACPI init
[    0.495699] ACPI: bus type pnp registered
[    0.495822] pnp 00:00: [bus 00-ff]
[    0.495825] pnp 00:00: [io  0x0cf8-0x0cff]
[    0.495826] pnp 00:00: [io  0x0000-0x0cf7 window]
[    0.495828] pnp 00:00: [io  0x0d00-0xffff window]
[    0.495830] pnp 00:00: [mem 0x000a0000-0x000bffff window]
[    0.495832] pnp 00:00: [mem 0x000d0000-0x000dffff window]
[    0.495834] pnp 00:00: [mem 0xd0000000-0xdfffffff window]
[    0.495836] pnp 00:00: [mem 0xf0000000-0xfebfffff window]
[    0.495918] pnp 00:00: Plug and Play ACPI device, IDs PNP0a03 (active)
[    0.495946] pnp 00:01: [dma 4]
[    0.495947] pnp 00:01: [io  0x0000-0x000f]
[    0.495949] pnp 00:01: [io  0x0081-0x0083]
[    0.495950] pnp 00:01: [io  0x0087]
[    0.495952] pnp 00:01: [io  0x0089-0x008b]
[    0.495953] pnp 00:01: [io  0x008f]
[    0.495955] pnp 00:01: [io  0x00c0-0x00df]
[    0.495973] pnp 00:01: Plug and Play ACPI device, IDs PNP0200 (active)
[    0.495979] pnp 00:02: [io  0x0061]
[    0.495994] pnp 00:02: Plug and Play ACPI device, IDs PNP0800 (active)
[    0.496000] pnp 00:03: [io  0x00f0-0x00ff]
[    0.496015] pnp 00:03: [irq 13]
[    0.496036] pnp 00:03: Plug and Play ACPI device, IDs PNP0c04 (active)
[    0.496409] Freeing initrd memory: 12856k freed
[    0.496633] pnp 00:04: [io  0x0378-0x037f]
[    0.496642] pnp 00:04: [irq 7]
[    0.496643] pnp 00:04: [dma 0 disabled]
[    0.496854] pnp 00:04: Plug and Play ACPI device, IDs PNP0400 (active)
[    0.497121] pnp 00:05: [mem 0x000d0000-0x000d3fff window]
[    0.497123] pnp 00:05: [mem 0x000d4000-0x000d7fff window]
[    0.497125] pnp 00:05: [mem 0x000de000-0x000dffff window]
[    0.497127] pnp 00:05: [io  0x0010-0x001f]
[    0.497128] pnp 00:05: [io  0x0022-0x003f]
[    0.497130] pnp 00:05: [io  0x0044-0x004d]
[    0.497131] pnp 00:05: [io  0x0050-0x005f]
[    0.497133] pnp 00:05: [io  0x0062-0x0063]
[    0.497134] pnp 00:05: [io  0x0065-0x006f]
[    0.497136] pnp 00:05: [io  0x0072-0x007f]
[    0.497137] pnp 00:05: [io  0x0080]
[    0.497139] pnp 00:05: [io  0x0084-0x0086]
[    0.497140] pnp 00:05: [io  0x0088]
[    0.497142] pnp 00:05: [io  0x008c-0x008e]
[    0.497143] pnp 00:05: [io  0x0090-0x009f]
[    0.497147] pnp 00:05: [io  0x00a2-0x00bf]
[    0.497149] pnp 00:05: [io  0x00e0-0x00ef]
[    0.497150] pnp 00:05: [io  0x04d0-0x04d1]
[    0.497152] pnp 00:05: [io  0x0800-0x080f]
[    0.497154] pnp 00:05: [io  0x0500-0x057f]
[    0.497155] pnp 00:05: [io  0x0580-0x05ff]
[    0.497157] pnp 00:05: [io  0x0800-0x087f]
[    0.497158] pnp 00:05: [io  0x0880-0x08ff]
[    0.497160] pnp 00:05: [io  0x0d00-0x0d7f]
[    0.497161] pnp 00:05: [io  0x0d80-0x0dff]
[    0.497163] pnp 00:05: [io  0x0900-0x097f]
[    0.497164] pnp 00:05: [io  0x0980-0x09ff]
[    0.497167] pnp 00:05: [mem 0x00000000-0xffffffffffffffff disabled]
[    0.497169] pnp 00:05: [mem 0x00000000-0xffffffffffffffff disabled]
[    0.497171] pnp 00:05: [mem 0xfed04000-0xfed04fff]
[    0.497172] pnp 00:05: [mem 0xfee01000-0xfeefffff]
[    0.497181] pnp 00:05: disabling [io  0x0900-0x097f] because it overlaps 0000:00:01.0 BAR 0 [io  0x0900-0x09ff]
[    0.497184] pnp 00:05: disabling [io  0x0980-0x09ff] because it overlaps 0000:00:01.0 BAR 0 [io  0x0900-0x09ff]
[    0.497268] system 00:05: [io  0x04d0-0x04d1] has been reserved
[    0.497270] system 00:05: [io  0x0800-0x080f] has been reserved
[    0.497272] system 00:05: [io  0x0500-0x057f] has been reserved
[    0.497274] system 00:05: [io  0x0580-0x05ff] has been reserved
[    0.497277] system 00:05: [io  0x0800-0x087f] could not be reserved
[    0.497279] system 00:05: [io  0x0880-0x08ff] has been reserved
[    0.497281] system 00:05: [io  0x0d00-0x0d7f] has been reserved
[    0.497283] system 00:05: [io  0x0d80-0x0dff] has been reserved
[    0.497287] system 00:05: [mem 0x000d0000-0x000d3fff window] has been reserved
[    0.497289] system 00:05: [mem 0x000d4000-0x000d7fff window] has been reserved
[    0.497292] system 00:05: [mem 0x000de000-0x000dffff window] has been reserved
[    0.497294] system 00:05: [mem 0xfed04000-0xfed04fff] has been reserved
[    0.497298] system 00:05: [mem 0xfee01000-0xfeefffff] has been reserved
[    0.497301] system 00:05: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.497393] pnp 00:06: [mem 0xfed00000-0xfed00fff]
[    0.497395] pnp 00:06: [irq 2 disabled]
[    0.497403] pnp 00:06: [irq 8]
[    0.497422] pnp 00:06: Plug and Play ACPI device, IDs PNP0103 (active)
[    0.497440] pnp 00:07: [io  0x0070-0x0071]
[    0.497462] pnp 00:07: Plug and Play ACPI device, IDs PNP0b00 (active)
[    0.497537] pnp 00:08: [io  0x0060]
[    0.497539] pnp 00:08: [io  0x0064]
[    0.497540] pnp 00:08: [mem 0xfec00000-0xfec00fff]
[    0.497542] pnp 00:08: [mem 0xfee00000-0xfee00fff]
[    0.497577] system 00:08: [mem 0xfec00000-0xfec00fff] could not be reserved
[    0.497580] system 00:08: [mem 0xfee00000-0xfee00fff] has been reserved
[    0.497582] system 00:08: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.497733] pnp 00:09: [io  0x0000-0xffffffffffffffff disabled]
[    0.497735] pnp 00:09: [io  0x0230-0x023f]
[    0.497737] pnp 00:09: [io  0x0290-0x029f]
[    0.497738] pnp 00:09: [io  0x0a00-0x0a0f]
[    0.497740] pnp 00:09: [io  0x0a10-0x0a1f]
[    0.497782] system 00:09: [io  0x0230-0x023f] has been reserved
[    0.497784] system 00:09: [io  0x0290-0x029f] has been reserved
[    0.497787] system 00:09: [io  0x0a00-0x0a0f] has been reserved
[    0.497789] system 00:09: [io  0x0a10-0x0a1f] has been reserved
[    0.497791] system 00:09: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.498209] pnp 00:0a: [io  0x03f8-0x03ff]
[    0.498217] pnp 00:0a: [irq 4]
[    0.498219] pnp 00:0a: [dma 0 disabled]
[    0.498263] pnp 00:0a: Plug and Play ACPI device, IDs PNP0501 (active)
[    0.498301] pnp 00:0b: [mem 0xe0000000-0xefffffff]
[    0.498338] system 00:0b: [mem 0xe0000000-0xefffffff] has been reserved
[    0.498341] system 00:0b: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.498458] pnp 00:0c: [mem 0x00000000-0x0009ffff]
[    0.498460] pnp 00:0c: [mem 0x000c0000-0x000cffff]
[    0.498461] pnp 00:0c: [mem 0x000e0000-0x000fffff]
[    0.498463] pnp 00:0c: [mem 0x00100000-0xcfffffff]
[    0.498465] pnp 00:0c: [mem 0xfec00000-0xffffffff]
[    0.498511] system 00:0c: [mem 0x00000000-0x0009ffff] could not be reserved
[    0.498513] system 00:0c: [mem 0x000c0000-0x000cffff] has been reserved
[    0.498515] system 00:0c: [mem 0x000e0000-0x000fffff] could not be reserved
[    0.498518] system 00:0c: [mem 0x00100000-0xcfffffff] could not be reserved
[    0.498520] system 00:0c: [mem 0xfec00000-0xffffffff] could not be reserved
[    0.498522] system 00:0c: Plug and Play ACPI device, IDs PNP0c01 (active)
[    0.499037] pnp: PnP ACPI: found 13 devices
[    0.499039] ACPI: ACPI bus type pnp unregistered
[    0.499861] Switched to NOHz mode on CPU #0
[    0.499961] Switched to NOHz mode on CPU #1
[    0.505021] pci 0000:00:08.0: PCI bridge to [bus 01-01]
[    0.505023] pci 0000:00:08.0:   bridge window [io  disabled]
[    0.505027] pci 0000:00:08.0:   bridge window [mem 0xfbe00000-0xfbefffff]
[    0.505030] pci 0000:00:08.0:   bridge window [mem pref disabled]
[    0.505035] pci 0000:00:10.0: PCI bridge to [bus 02-02]
[    0.505039] pci 0000:00:10.0:   bridge window [io  0xe000-0xefff]
[    0.505049] pci 0000:00:10.0:   bridge window [mem 0xfbf00000-0xfbffffff]
[    0.505056] pci 0000:00:10.0:   bridge window [mem 0xd0000000-0xdfffffff 64bit pref]
[    0.505068] pci 0000:00:12.0: PCI bridge to [bus 03-03]
[    0.505070] pci 0000:00:12.0:   bridge window [io  disabled]
[    0.505079] pci 0000:00:12.0:   bridge window [mem disabled]
[    0.505085] pci 0000:00:12.0:   bridge window [mem pref disabled]
[    0.505097] pci 0000:00:13.0: PCI bridge to [bus 04-04]
[    0.505099] pci 0000:00:13.0:   bridge window [io  disabled]
[    0.505108] pci 0000:00:13.0:   bridge window [mem disabled]
[    0.505114] pci 0000:00:13.0:   bridge window [mem pref disabled]
[    0.505132] pci 0000:00:08.0: setting latency timer to 64
[    0.505296] ACPI: PCI Interrupt Link [LN0A] enabled at IRQ 19
[    0.505311] pci 0000:00:10.0: PCI INT A -> Link[LN0A] -> GSI 19 (level, low) -> IRQ 19
[    0.505319] pci 0000:00:10.0: setting latency timer to 64
[    0.505442] ACPI: PCI Interrupt Link [LN2A] enabled at IRQ 18
[    0.505451] pci 0000:00:12.0: PCI INT A -> Link[LN2A] -> GSI 18 (level, low) -> IRQ 18
[    0.505459] pci 0000:00:12.0: setting latency timer to 64
[    0.505579] ACPI: PCI Interrupt Link [LN3A] enabled at IRQ 17
[    0.505587] pci 0000:00:13.0: PCI INT A -> Link[LN3A] -> GSI 17 (level, low) -> IRQ 17
[    0.505594] pci 0000:00:13.0: setting latency timer to 64
[    0.505599] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
[    0.505602] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff]
[    0.505604] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
[    0.505605] pci_bus 0000:00: resource 7 [mem 0x000d0000-0x000dffff]
[    0.505607] pci_bus 0000:00: resource 8 [mem 0xd0000000-0xdfffffff]
[    0.505609] pci_bus 0000:00: resource 9 [mem 0xf0000000-0xfebfffff]
[    0.505612] pci_bus 0000:01: resource 1 [mem 0xfbe00000-0xfbefffff]
[    0.505614] pci_bus 0000:01: resource 4 [io  0x0000-0x0cf7]
[    0.505615] pci_bus 0000:01: resource 5 [io  0x0d00-0xffff]
[    0.505617] pci_bus 0000:01: resource 6 [mem 0x000a0000-0x000bffff]
[    0.505619] pci_bus 0000:01: resource 7 [mem 0x000d0000-0x000dffff]
[    0.505621] pci_bus 0000:01: resource 8 [mem 0xd0000000-0xdfffffff]
[    0.505623] pci_bus 0000:01: resource 9 [mem 0xf0000000-0xfebfffff]
[    0.505625] pci_bus 0000:02: resource 0 [io  0xe000-0xefff]
[    0.505627] pci_bus 0000:02: resource 1 [mem 0xfbf00000-0xfbffffff]
[    0.505629] pci_bus 0000:02: resource 2 [mem 0xd0000000-0xdfffffff 64bit pref]
[    0.505663] NET: Registered protocol family 2
[    0.505791] IP route cache hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.506834] TCP established hash table entries: 524288 (order: 11, 8388608 bytes)
[    0.509579] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[    0.509922] TCP: Hash tables configured (established 524288 bind 65536)
[    0.509924] TCP reno registered
[    0.509932] UDP hash table entries: 2048 (order: 4, 65536 bytes)
[    0.509964] UDP-Lite hash table entries: 2048 (order: 4, 65536 bytes)
[    0.510110] NET: Registered protocol family 1
[    0.560133] pci 0000:00:08.0: Enabling HT MSI Mapping
[    0.560235] pci 0000:00:09.0: Enabling HT MSI Mapping
[    0.560342] pci 0000:00:0a.0: Enabling HT MSI Mapping
[    0.560528] pci 0000:02:00.0: Boot video device
[    0.560532] PCI: CLS 64 bytes, default 64
[    0.561786] PCI-DMA: Disabling AGP.
[    0.561881] PCI-DMA: aperture base @ c4000000 size 65536 KB
[    0.561883] PCI-DMA: using GART IOMMU.
[    0.561885] PCI-DMA: Reserving 64MB of IOMMU area in the AGP aperture
[    0.565462] audit: initializing netlink socket (disabled)
[    0.565473] type=2000 audit(1317929565.560:1): initialized
[    0.575697] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    0.577111] VFS: Disk quotas dquot_6.5.2
[    0.577157] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    0.577656] fuse init (API version 7.16)
[    0.577730] msgmni has been set to 7918
[    0.577976] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.578012] io scheduler noop registered
[    0.578014] io scheduler deadline registered
[    0.578049] io scheduler cfq registered (default)
[    0.578596] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.578614] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.578738] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0
[    0.578743] ACPI: Power Button [PWRB]
[    0.578784] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
[    0.578786] ACPI: Power Button [PWRF]
[    0.578920] ACPI: acpi_idle registered with cpuidle
[    0.580956] ERST: Table is not found!
[    0.581008] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    0.601525] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    1.000611] 00:0a: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    1.000899] Linux agpgart interface v0.103
[    1.001708] brd: module loaded
[    1.002076] loop: module loaded
[    1.002151] i2c-core: driver [adp5520] using legacy suspend method
[    1.002152] i2c-core: driver [adp5520] using legacy resume method
[    1.002312] pata_acpi 0000:00:06.0: setting latency timer to 64
[    1.002513] ACPI: PCI Interrupt Link [LSA0] enabled at IRQ 23
[    1.002528] pata_acpi 0000:00:09.0: PCI INT A -> Link[LSA0] -> GSI 23 (level, low) -> IRQ 23
[    1.002542] pata_acpi 0000:00:09.0: setting latency timer to 64
[    1.002547] pata_acpi 0000:00:09.0: PCI INT A disabled
[    1.002865] Fixed MDIO Bus: probed
[    1.002888] PPP generic driver version 2.4.2
[    1.002919] tun: Universal TUN/TAP device driver, 1.6
[    1.002920] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    1.002987] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    1.003139] ACPI: PCI Interrupt Link [LUB2] enabled at IRQ 22
[    1.003148] ehci_hcd 0000:00:02.1: PCI INT B -> Link[LUB2] -> GSI 22 (level, low) -> IRQ 22
[    1.003164] ehci_hcd 0000:00:02.1: setting latency timer to 64
[    1.003167] ehci_hcd 0000:00:02.1: EHCI Host Controller
[    1.003210] ehci_hcd 0000:00:02.1: new USB bus registered, assigned bus number 1
[    1.030042] ehci_hcd 0000:00:02.1: debug port 1
[    1.030050] ehci_hcd 0000:00:02.1: cache line size of 64 is not supported
[    1.030070] ehci_hcd 0000:00:02.1: irq 22, io mem 0xfbd7fc00
[    1.050017] ehci_hcd 0000:00:02.1: USB 2.0 started, EHCI 1.00
[    1.050109] hub 1-0:1.0: USB hub found
[    1.050112] hub 1-0:1.0: 6 ports detected
[    1.050323] ACPI: PCI Interrupt Link [UB12] enabled at IRQ 21
[    1.050333] ehci_hcd 0000:00:04.1: PCI INT B -> Link[UB12] -> GSI 21 (level, low) -> IRQ 21
[    1.050341] ehci_hcd 0000:00:04.1: setting latency timer to 64
[    1.050343] ehci_hcd 0000:00:04.1: EHCI Host Controller
[    1.050372] ehci_hcd 0000:00:04.1: new USB bus registered, assigned bus number 2
[    1.050410] ehci_hcd 0000:00:04.1: debug port 1
[    1.050416] ehci_hcd 0000:00:04.1: cache line size of 64 is not supported
[    1.050432] ehci_hcd 0000:00:04.1: irq 21, io mem 0xfbd7f800
[    1.070014] ehci_hcd 0000:00:04.1: USB 2.0 started, EHCI 1.00
[    1.070084] hub 2-0:1.0: USB hub found
[    1.070087] hub 2-0:1.0: 6 ports detected
[    1.070152] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    1.070307] ACPI: PCI Interrupt Link [LUB0] enabled at IRQ 20
[    1.070316] ohci_hcd 0000:00:02.0: PCI INT A -> Link[LUB0] -> GSI 20 (level, low) -> IRQ 20
[    1.070324] ohci_hcd 0000:00:02.0: setting latency timer to 64
[    1.070327] ohci_hcd 0000:00:02.0: OHCI Host Controller
[    1.070356] ohci_hcd 0000:00:02.0: new USB bus registered, assigned bus number 3
[    1.070394] ohci_hcd 0000:00:02.0: irq 20, io mem 0xfbd7e000
[    1.132082] hub 3-0:1.0: USB hub found
[    1.132087] hub 3-0:1.0: 6 ports detected
[    1.132292] ACPI: PCI Interrupt Link [UB11] enabled at IRQ 23
[    1.132295] ohci_hcd 0000:00:04.0: PCI INT A -> Link[UB11] -> GSI 23 (level, low) -> IRQ 23
[    1.132304] ohci_hcd 0000:00:04.0: setting latency timer to 64
[    1.132306] ohci_hcd 0000:00:04.0: OHCI Host Controller
[    1.132335] ohci_hcd 0000:00:04.0: new USB bus registered, assigned bus number 4
[    1.132372] ohci_hcd 0000:00:04.0: irq 23, io mem 0xfbd7d000
[    1.192080] hub 4-0:1.0: USB hub found
[    1.192084] hub 4-0:1.0: 6 ports detected
[    1.192148] uhci_hcd: USB Universal Host Controller Interface driver
[    1.192227] i8042: PNP: No PS/2 controller found. Probing ports directly.
[    1.192628] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.192632] serio: i8042 AUX port at 0x60,0x64 irq 12
[    1.192716] mousedev: PS/2 mouse device common for all mice
[    1.192810] rtc_cmos 00:07: RTC can wake from S4
[    1.230064] rtc_cmos 00:07: rtc core: registered rtc_cmos as rtc0
[    1.230117] rtc0: alarms up to one year, y3k, 114 bytes nvram, hpet irqs
[    1.230185] device-mapper: uevent: version 1.0.3
[    1.230241] device-mapper: ioctl: 4.19.1-ioctl (2011-01-07) initialised: dm-devel@redhat.com
[    1.230306] device-mapper: multipath: version 1.2.0 loaded
[    1.230309] device-mapper: multipath round-robin: version 1.0.0 loaded
[    1.230506] cpuidle: using governor ladder
[    1.230508] cpuidle: using governor menu
[    1.230697] TCP cubic registered
[    1.230788] NET: Registered protocol family 10
[    1.231156] NET: Registered protocol family 17
[    1.231170] Registering the dns_resolver key type
[    1.231189] powernow-k8: Found 1 AMD Athlon(tm) 7850 Dual-Core Processor (2 cpu cores) (version 2.20.00)
[    1.231213] powernow-k8:    0 : pstate 0 (2800 MHz)
[    1.231215] powernow-k8:    1 : pstate 1 (1400 MHz)
[    1.231359] PM: Hibernation image not present or could not be loaded.
[    1.231369] registered taskstats version 1
[    1.231685]   Magic number: 15:966:545
[    1.231698] tty ttyS21: hash matches
[    1.231800] rtc_cmos 00:07: setting system clock to 2011-10-06 19:32:46 UTC (1317929566)
[    1.231802] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.231804] EDD information not available.
[    1.233139] Freeing unused kernel memory: 956k freed
[    1.233425] Write protecting the kernel read-only data: 10240k
[    1.234027] Freeing unused kernel memory: 184k freed
[    1.237989] Freeing unused kernel memory: 1440k freed
[    1.262114] <30>udev[116]: starting version 167
[    1.350226] pata_amd 0000:00:06.0: version 0.4.1
[    1.350265] pata_amd 0000:00:06.0: setting latency timer to 64
[    1.351150] scsi0 : pata_amd
[    1.356010] scsi1 : pata_amd
[    1.356625] ata1: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xffa0 irq 14
[    1.356627] ata2: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xffa8 irq 15
[    1.356851] ACPI: PCI Interrupt Link [LNKC] enabled at IRQ 16
[    1.356868] firewire_ohci 0000:01:08.0: PCI INT A -> Link[LNKC] -> GSI 16 (level, low) -> IRQ 16
[    1.356935] ahci 0000:00:09.0: version 3.0
[    1.356941] ahci 0000:00:09.0: PCI INT A -> Link[LSA0] -> GSI 23 (level, low) -> IRQ 23
[    1.356971] ahci 0000:00:09.0: irq 40 for MSI/MSI-X
[    1.356976] ahci 0000:00:09.0: controller can't do PMP, turning off CAP_PMP
[    1.357028] ahci 0000:00:09.0: AHCI 0001.0200 32 slots 6 ports 3 Gbps 0x3f impl IDE mode
[    1.357031] ahci 0000:00:09.0: flags: 64bit ncq sntf led clo pio boh 
[    1.357034] ahci 0000:00:09.0: setting latency timer to 64
[    1.357785] scsi2 : ahci
[    1.357852] scsi3 : ahci
[    1.357913] scsi4 : ahci
[    1.357973] scsi5 : ahci
[    1.358036] scsi6 : ahci
[    1.358096] scsi7 : ahci
[    1.358202] ata3: SATA max UDMA/133 abar m8192@0xfbd76000 port 0xfbd76100 irq 40
[    1.358204] ata4: SATA max UDMA/133 abar m8192@0xfbd76000 port 0xfbd76180 irq 40
[    1.358206] ata5: SATA max UDMA/133 abar m8192@0xfbd76000 port 0xfbd76200 irq 40
[    1.358209] ata6: SATA max UDMA/133 abar m8192@0xfbd76000 port 0xfbd76280 irq 40
[    1.358211] ata7: SATA max UDMA/133 abar m8192@0xfbd76000 port 0xfbd76300 irq 40
[    1.358213] ata8: SATA max UDMA/133 abar m8192@0xfbd76000 port 0xfbd76380 irq 40
[    1.358438] forcedeth: Reverse Engineered nForce ethernet driver. Version 0.64.
[    1.358598] ACPI: PCI Interrupt Link [LMAC] enabled at IRQ 22
[    1.358602] forcedeth 0000:00:0a.0: PCI INT A -> Link[LMAC] -> GSI 22 (level, low) -> IRQ 22
[    1.358605] forcedeth 0000:00:0a.0: setting latency timer to 64
[    1.410099] firewire_ohci: Added fw-ohci device 0000:01:08.0, OHCI v1.0, 8 IR + 8 IT contexts, quirks 0x0
[    1.431178] forcedeth 0000:00:0a.0: ifname eth0, PHY OUI 0x732 @ 3, addr 00:26:18:50:ec:99
[    1.431182] forcedeth 0000:00:0a.0: highdma csum pwrctl mgmt gbit lnktim msi desc-v3
[    1.521167] ata2: port disabled. ignoring.
[    1.560018] Refined TSC clocksource calibration: 2799.999 MHz.
[    1.560023] Switching to clocksource tsc
[    1.650014] usb 3-6: new low speed USB device using ohci_hcd and address 2
[    1.700013] ata5: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    1.700025] ata6: SATA link down (SStatus 0 SControl 300)
[    1.700039] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    1.700053] ata4: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    1.700063] ata8: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    1.700073] ata7: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    1.702586] ata8.00: ATAPI: HL-DT-ST DVDRAM GH22LS50, TL01, max UDMA/100
[    1.703061] ata4.00: ATAPI: HL-DT-ST BDDVDRW CH08LS10, 2.00, max UDMA/133
[    1.706321] ata8.00: configured for UDMA/100
[    1.707033] ata4.00: configured for UDMA/133
[    1.717191] ata7.00: ATA-8: Hitachi HDT721010SLA360, ST6OA3AA, max UDMA/133
[    1.717193] ata7.00: 1953525168 sectors, multi 0: LBA48 NCQ (depth 31/32)
[    1.718033] ata7.00: configured for UDMA/133
[    1.720539] ata5.00: ATA-8: SAMSUNG HD501LJ, CR100-10, max UDMA7
[    1.720541] ata5.00: 976773168 sectors, multi 16: LBA48 NCQ (depth 31/32)
[    1.722479] ata5.00: configured for UDMA/133
[    1.737151] ata3.00: ATA-7: ST380815AS, 3.AAD, max UDMA/133
[    1.737153] ata3.00: 156301488 sectors, multi 16: LBA48 NCQ (depth 31/32)
[    1.795460] ata3.00: configured for UDMA/133
[    1.795590] scsi 2:0:0:0: Direct-Access     ATA      ST380815AS       3.AA PQ: 0 ANSI: 5
[    1.795723] sd 2:0:0:0: [sda] 156301488 512-byte logical blocks: (80.0 GB/74.5 GiB)
[    1.795744] sd 2:0:0:0: Attached scsi generic sg0 type 0
[    1.795758] sd 2:0:0:0: [sda] Write Protect is off
[    1.795760] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.795775] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.799379] scsi 3:0:0:0: CD-ROM            HL-DT-ST BDDVDRW CH08LS10 2.00 PQ: 0 ANSI: 5
[    1.808405] sr0: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
[    1.808407] cdrom: Uniform CD-ROM driver Revision: 3.20
[    1.808501] sr 3:0:0:0: Attached scsi CD-ROM sr0
[    1.808547] sr 3:0:0:0: Attached scsi generic sg1 type 5
[    1.808664] scsi 4:0:0:0: Direct-Access     ATA      SAMSUNG HD501LJ  CR10 PQ: 0 ANSI: 5
[    1.808764] sd 4:0:0:0: Attached scsi generic sg2 type 0
[    1.808816] sd 4:0:0:0: [sdb] 976773168 512-byte logical blocks: (500 GB/465 GiB)
[    1.808851] sd 4:0:0:0: [sdb] Write Protect is off
[    1.808854] sd 4:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[    1.808872] scsi 6:0:0:0: Direct-Access     ATA      Hitachi HDT72101 ST6O PQ: 0 ANSI: 5
[    1.808874] sd 4:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.809022] sd 6:0:0:0: Attached scsi generic sg3 type 0
[    1.809052] sd 6:0:0:0: [sdc] 1953525168 512-byte logical blocks: (1.00 TB/931 GiB)
[    1.809082] sd 6:0:0:0: [sdc] Write Protect is off
[    1.809084] sd 6:0:0:0: [sdc] Mode Sense: 00 3a 00 00
[    1.809098] sd 6:0:0:0: [sdc] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.811968] scsi 7:0:0:0: CD-ROM            HL-DT-ST DVDRAM GH22LS50  TL01 PQ: 0 ANSI: 5
[    1.815730] sr1: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
[    1.815803] sr 7:0:0:0: Attached scsi CD-ROM sr1
[    1.815854] sr 7:0:0:0: Attached scsi generic sg4 type 5
[    1.824721]  sdc: sdc1 sdc2
[    1.824937] sd 6:0:0:0: [sdc] Attached SCSI disk
[    1.860398]  sda: sda1 sda2 sda3 sda4 < sda5 >
[    1.860649] sd 2:0:0:0: [sda] Attached SCSI disk
[    1.891908]  sdb: sdb1
[    1.892150] sd 4:0:0:0: [sdb] Attached SCSI disk
[    1.910111] firewire_core: created device fw0: GUID 000a0a00000033a4, S400
[    1.930226] input: Microsoft Microsoft® 2.4GHz Transceiver V1.0 as /devices/pci0000:00/0000:00:02.0/usb3/3-6/3-6:1.0/input/input2
[    1.930318] generic-usb 0003:045E:071D.0001: input,hidraw0: USB HID v1.11 Keyboard [Microsoft Microsoft® 2.4GHz Transceiver V1.0] on usb-0000:00:02.0-6/input0
[    2.000210] input: Microsoft Microsoft® 2.4GHz Transceiver V1.0 as /devices/pci0000:00/0000:00:02.0/usb3/3-6/3-6:1.1/input/input3
[    2.000321] generic-usb 0003:045E:071D.0002: input,hidraw1: USB HID v1.11 Mouse [Microsoft Microsoft® 2.4GHz Transceiver V1.0] on usb-0000:00:02.0-6/input1
[    2.000341] usbcore: registered new interface driver usbhid
[    2.000343] usbhid: USB HID core driver
[    2.358229] JFS: nTxBlock = 8192, nTxLock = 65536
[   26.727397] Adding 3215416k swap on /dev/sda5.  Priority:-1 extents:1 across:3215416k 
[   29.020380] <30>udev[464]: starting version 167
[   32.419259] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
[   32.419264] Disabling lock debugging due to kernel taint
[   32.457539] [fglrx] Maximum main memory to use for locked dma buffers: 3799 MBytes.
[   32.457729] [fglrx]   vendor: 1002 device: 9442 count: 1
[   32.458085] [fglrx] ioport: bar 4, base 0xe800, size: 0x100
[   32.458099] pci 0000:02:00.0: PCI INT A -> Link[LN0A] -> GSI 19 (level, low) -> IRQ 19
[   32.458104] pci 0000:02:00.0: setting latency timer to 64
[   32.458300] [fglrx] Kernel PAT support is enabled
[   32.458320] [fglrx] module loaded - fglrx 8.84.5 [Apr  5 2011] with 1 minors
[   32.643731] k10temp 0000:00:18.3: unreliable CPU thermal sensor; check erratum 319
[   32.924718] ACPI: resource nForce2_smbus [io  0x0600-0x063f] conflicts with ACPI region SMRG [io 0x600-0x6ff]
[   32.924722] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[   32.924726] ACPI: resource nForce2_smbus [io  0x0700-0x073f] conflicts with ACPI region SM00 [io 0x700-0x73f]
[   32.924728] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[   33.013903] type=1400 audit(1317925998.276:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=649 comm="apparmor_parser"
[   33.013919] type=1400 audit(1317925998.276:3): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=648 comm="apparmor_parser"
[   33.014186] type=1400 audit(1317925998.276:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=649 comm="apparmor_parser"
[   33.014208] type=1400 audit(1317925998.276:5): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=648 comm="apparmor_parser"
[   33.014370] type=1400 audit(1317925998.276:6): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=649 comm="apparmor_parser"
[   33.014399] type=1400 audit(1317925998.276:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=648 comm="apparmor_parser"
[   33.147832] MCE: In-kernel MCE decoding enabled.
[   33.194946] EDAC MC: Ver: 2.1.0 Sep 12 2011
[   33.248126] lp: driver loaded but no devices found
[   33.279674] EDAC amd64_edac: v3.3.0
[   33.279851] EDAC amd64: DRAM ECC disabled.
[   33.279857] EDAC amd64: ECC disabled in the BIOS or no ECC capability, module will not load.
[   33.279858]  Either enable ECC checking or force module loading by setting 'ecc_enable_override'.
[   33.279859]  (Note that use of the override may cause unknown side effects.)
[   33.359237] parport_pc 00:04: reported by Plug and Play ACPI
[   33.359285] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
[   33.398584] ppdev: user-space parallel port driver
[   33.430180] lp0: using parport0 (interrupt-driven).
[   34.009437] HDA Intel 0000:00:07.0: power state changed by ACPI to D0
[   34.009442] HDA Intel 0000:00:07.0: power state changed by ACPI to D0
[   34.009594] ACPI: PCI Interrupt Link [LAZA] enabled at IRQ 21
[   34.009598] HDA Intel 0000:00:07.0: PCI INT A -> Link[LAZA] -> GSI 21 (level, low) -> IRQ 21
[   34.009601] hda_intel: Disable MSI for Nvidia chipset
[   34.009635] HDA Intel 0000:00:07.0: setting latency timer to 64
[   34.042119] it87: Found IT8712F chip at 0x290, revision 8
[   34.042130] it87: VID is disabled (pins used for GPIO)
[   34.042177] ACPI: resource it87 [io  0x0295-0x0296] conflicts with ACPI region SIOE [io 0x290-0x2af]
[   34.042179] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[   34.092949] it87: Found IT8712F chip at 0x290, revision 8
[   34.092960] it87: VID is disabled (pins used for GPIO)
[   34.093059] ACPI: resource it87 [io  0x0295-0x0296] conflicts with ACPI region SIOE [io 0x290-0x2af]
[   34.093061] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[   35.850010] hda_codec: ALC887: BIOS auto-probing.
[   37.220546] input: HDA NVidia Headphone as /devices/pci0000:00/0000:00:07.0/sound/card0/input4
[   37.224895] ACPI: PCI Interrupt Link [LN0B] enabled at IRQ 19
[   37.224902] HDA Intel 0000:02:00.1: PCI INT B -> Link[LN0B] -> GSI 19 (level, low) -> IRQ 19
[   37.224970] HDA Intel 0000:02:00.1: irq 41 for MSI/MSI-X
[   37.224992] HDA Intel 0000:02:00.1: setting latency timer to 64
[   37.260075] hda-intel: Enable sync_write for AMD chipset
[   39.553578] vesafb: framebuffer at 0xd0000000, mapped to 0xffffc90011300000, using 600k, total 16384k
[   39.553582] vesafb: mode is 640x480x8, linelength=640, pages=50
[   39.553584] vesafb: scrolling: redraw
[   39.553586] vesafb: Pseudocolor: size=8:8:8:8, shift=0:0:0:0
[   39.553720] Console: switching to colour frame buffer device 80x30
[   39.554945] fb0: VESA VGA frame buffer device
[   42.936010] type=1400 audit(1317926008.196:8): apparmor="STATUS" operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" pid=1009 comm="apparmor_parser"
[   42.936364] type=1400 audit(1317926008.196:9): apparmor="STATUS" operation="profile_load" name="/usr/sbin/cupsd" pid=1009 comm="apparmor_parser"
[   43.680878] type=1400 audit(1317926008.946:10): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=1020 comm="apparmor_parser"
[   43.681174] type=1400 audit(1317926008.946:11): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=1020 comm="apparmor_parser"
[   43.681363] type=1400 audit(1317926008.946:12): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=1020 comm="apparmor_parser"
[   43.738628] type=1400 audit(1317926008.996:13): apparmor="STATUS" operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" pid=1019 comm="apparmor_parser"
[   44.678745] type=1400 audit(1317926009.936:14): apparmor="STATUS" operation="profile_replace" name="/usr/lib/cups/backend/cups-pdf" pid=1026 comm="apparmor_parser"
[   44.679108] type=1400 audit(1317926009.936:15): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/cupsd" pid=1026 comm="apparmor_parser"
[   44.845142] type=1400 audit(1317926010.106:16): apparmor="STATUS" operation="profile_load" name="/usr/sbin/mysqld-akonadi" pid=1027 comm="apparmor_parser"
[   44.845337] type=1400 audit(1317926010.106:17): apparmor="STATUS" operation="profile_load" name="/usr/sbin/mysqld-akonadi///usr/sbin/mysqld" pid=1027 comm="apparmor_parser"
[   46.477732] forcedeth 0000:00:0a.0: irq 42 for MSI/MSI-X
[   51.489189] fglrx_pci 0000:02:00.0: irq 43 for MSI/MSI-X
[   51.489690] [fglrx] Firegl kernel thread PID: 1421
[   51.489733] [fglrx] Firegl kernel thread PID: 1422
[   51.489774] [fglrx] Firegl kernel thread PID: 1423
[   51.489945] [fglrx] IRQ 43 Enabled
[   53.890545] vboxdrv: Found 2 processor cores.
[   53.891247] vboxdrv: fAsync=0 offMin=0x4c0 offMax=0x1289
[   53.891996] vboxdrv: TSC mode is 'synchronous', kernel timer mode is 'normal'.
[   53.891999] vboxdrv: Successfully loaded version 4.0.4_OSE (interface 0x00160000).
[   54.226501] [fglrx] Gart USWC size:1240 M.
[   54.226504] [fglrx] Gart cacheable size:491 M.
[   54.226509] [fglrx] Reserved FB block: Shared offset:0, size:1000000 
[   54.226511] [fglrx] Reserved FB block: Unshared offset:fc1f000, size:3e1000 
[   54.226513] [fglrx] Reserved FB block: Unshared offset:1fffb000, size:5000 
[   54.713453] HDMI hot plug event: Pin=3 Presence_Detect=0 ELD_Valid=0
[   56.528343] HDMI hot plug event: Pin=3 Presence_Detect=1 ELD_Valid=0
[   57.000006] eth0: no IPv6 routers present
[   60.328336] HDMI hot plug event: Pin=3 Presence_Detect=0 ELD_Valid=0
[   60.328351] HDMI hot plug event: Pin=3 Presence_Detect=0 ELD_Valid=0
[   60.347486] HDMI hot plug event: Pin=3 Presence_Detect=0 ELD_Valid=0
[   60.368108] HDMI hot plug event: Pin=3 Presence_Detect=1 ELD_Valid=0
[   68.896480] hda-intel: IRQ timing workaround is activated for card #1. Suggest a bigger bdl_pos_adj.
```

---

### Post by oldfred on 2011-10-06
I looks like 24 sec is here. Is there something about your jfs partition that is huge or has issues that it takes so long?
> 
[    2.358229] JFS: nTxBlock = 8192, nTxLock = 65536
[   26.727397] Adding 3215416k swap on /dev/sda5.  Priority:-1 extents:1 across:3215416k 


---

### Post by Cavsfan on 2011-10-06
Just my 2cents but, my system boots up in ~ 10 seconds - 10.04 and I have a SATA drive. 
I have a conky on the right side and it is set to delay 15 seconds 
because it will permanently be on top of everything w/o the delay. I actually have to wait for it to appear.
I have a quad core 2.83Ghz with 4GB Ram.

---

### Post by blueridgedog on 2011-10-06
> **oldfred said:**
> I looks like 24 sec is here. Is there something about your jfs partition that is huge or has issues that it takes so long?

I would be curious about the use of JFS and what the partition is as well.  Did that become standard in 11.04?  I see it rarely.

---

### Post by viperdvman on 2011-10-06
[LEFT]I have no problems booting Ubuntu 11.04 on both my AMD V105-powered netbook and my Core 2-powered desktop. I haven't timed the bootup times from the moment the bootloader begins the boot to desktop, but on both computers they boot up AND shut down much faster than the Windows installations they dual-boot with. And I run regular SATA hard drives on both computers... no SSD's... yet.

What kind of hardware do you run on your computer?
[/LEFT]

---

### Post by viraf87 on 2011-10-06
I've got a dual core Athlon 7850 with 3 HDDs. The system files are all on an 80Gb drive and my home drive is on a different partition (I read somewhere back on a Hardy (my first adventure into Ubuntu, and the last time I used Windows) thread that it serves well to keep them separate for upgrades).

I've upgraded since Jaunty on my current install (issues with Intrepid) rather than clean installs.

Back when jfs came about (I'm pretty sure it was popular in the days of Jaunty) I read it was much faster as a format.

Would you advise a clean install of Natty with a different format? If there are problems with the jfs drive is there a way of fixing the problems or would a clean install be best?

I'm not adverse to a clean install but naturally it isn't the first option.  Thanks for the responses guys, always been impressed by the community Ubuntu has.  

Viraf

PS if you need anymore hardware details (specific information from terminal) just ask, I'll be happy to provide all I can to sort this.  Thanks again

---

### Post by oldfred on 2011-10-06
I know nothing about jfs. But the more partitions you have the longer boot takes. Having a separate /home is a good idea for clean reinstalls rather than upgrades in place as you can reuse your /home and not lose data & reuse settings. But I prefer to have a system completely on one drive and a different system on every drive. 

[http://phoronix.com/forums/showthread.php?54393-Linux-2.6.39-XFS-Speeds-Up-EXT4-amp-Btrfs-Unchanged](http://phoronix.com/forums/showthread.php?54393-Linux-2.6.39-XFS-Speeds-Up-EXT4-amp-Btrfs-Unchanged)

---

### Post by dcstar on 2011-10-07
> **oldfred said:**
> I looks like 24 sec is here. Is there something about your jfs partition that is huge or has issues that it takes so long?

Give the man a cigar...... AFAIK setting the fsck check flag for JFS means a thorough check on each and every mount.

Edit the /etc/fstab file and set the JFS partition flag (the last digit on the line) to 0 and see how it boots then.

I had this issue with some Reiserfs partitions a few years ago, most annoying......     ;)

---

### Post by amjjawad on 2011-10-07
Gigabyte MB - P4 CPU 3.0GHz and 2MB L2 Cashe - 2GB RAM (DDR2 I guess?) - 40GB IDE HDD with 7 total partitions - Lubuntu 11.04.

Booting time according to Bootchart is 70seconds while it takes 45seconds when I check that on a stopwatch.

---

### Post by viraf87 on 2011-10-07
> **dcstar said:**
> Give the man a cigar...... AFAIK setting the fsck check flag for JFS means a thorough check on each and every mount.

Edit the /etc/fstab file and set the JFS partition flag (the last digit on the line) to 0 and see how it boots then.

I had this issue with some Reiserfs partitions a few years ago, most annoying......     ;)

Thanks David, unfortunately it didn't work.  Any more ideas?

> Gigabyte MB - P4 CPU 3.0GHz and 2MB L2 Cashe - 2GB RAM (DDR2 I guess?) - 40GB IDE HDD with 7 total partitions - Lubuntu 11.04.

Booting time according to Bootchart is 70seconds while it takes 45seconds when I check that on a stopwatch.

I've noted the time on both a stopwatch and bootchart; they match.  Are your partitions jfs?

> [http://phoronix.com/forums/showthrea...trfs-Unchanged](http://phoronix.com/forums/showthrea...trfs-Unchanged)

Thanks for the link, it's interesting that jfs is being phased out.  If I do a clean install, I'll be sure to change the file system.  Is there one you'd recommend oldfred?  I think I might wait for Oneiric, although I notice a lot of you guys are running Lucid or Maverick.  I was really happy with Lucid but obviously because it wasn't broken it had to be fixed... ;)

Viraf

---

### Post by amjjawad on 2011-10-07
> **viraf87 said:**
> I've noted the time on both a stopwatch and bootchart; they match.  Are your partitions jfs?

Never used it. I always use **ext4** and sometimes ext3 with some distributions which I haven't used in long time.

For me, Bootchart time is longer. With Stopwatch, I start counting from the moment I press ON Button on my case until I got a working desktop.

---

### Post by oldfred on 2011-10-07
I am no expert on partition formats, some have posted various advice for different type for different purposes. Small files or large files, Video etc. 

But I, like amjjawad, stay with ext4 or ext3 as general use files systems. Most reviews show ext4 as good as or better for most types of things and they seem to have resolved the issues it originally had.

My boot time just dropped immensely. I bought a SSD :) and it is under 20 sec before even trying to adjust things. But my standard drives take about 50-60 sec as I mount several partitions and I understand the NTFS mounts slow. I do not normally do much tuning as I find that fast since my XP used to take 3 to 5 minutes.

---

### Post by viperdvman on 2011-10-07
Even my current XP install on my desktop computer isn't that slow... nowadays. **But**, it was before I wiped the hard drive to reinstall Windows and do a permanent install of Ubuntu 11.04 when my Windows XP had a slow time booting up. I still have no clue to this day what caused programs on WinXP to run so slow then. 

Like I said, I haven't timed my boot-up times for WinXP and Ubuntu on my desktop, and Win7 and Ubuntu on my netbook. I just know that in both instances, my Ubuntu boots up and shuts down quicker than both Windows installs... and both my Ubuntu partitions are **ext4** file systems.

I'll have to time them sometime. I can very easily time mine from the moment the bootloader starts  loading Windows or Ubuntu since I have my Windows bootloaders set up to  choose between either. However, do you guys time it from the moment you turn on your computers, or from the moment your bootloader starts loading said OS?

---

### Post by amjjawad on 2011-10-07
> **viperdvman said:**
> do you guys time it **from the moment you turn on your computers**, or from the moment your bootloader starts loading said OS?

The Bold answer ;)

---

### Post by viraf87 on 2011-10-08
So... I reinstalled 11.04 (converting to ext4) and the boot time has reduced.  However, there are now significantly more problems with my system.  A major one is that I can't open nautilus.  

```
(nautilus:21691): Unique-DBus-WARNING **: Error while sending message: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.

```

Also I can't change the volume of my system (I now get the waiting for sound system window).

I can't believe it.

---

### Post by viraf87 on 2011-10-08
Also my processor is now running at 80% all the time.  Rather than 0%.  System monitor says nothing is using CPU so I don't know what the hell's going on.  

What should've taken about an hour has now taken all day.

---

### Post by blueridgedog on 2011-10-08
Did you install all updates?

The command "top" will show you what is eating your cpu.

---

### Post by jonnyboysmithy on 2011-10-08
> **viraf87 said:**
> So... I reinstalled 11.04 (converting to ext4) and the boot time has reduced.  However, there are now significantly more problems with my system.  A major one is that I can't open nautilus.  

```
(nautilus:21691): Unique-DBus-WARNING **: Error while sending message: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.

```Also I can't change the volume of my system (I now get the waiting for sound system window).

I can't believe it.
There's a reason a lot of us run 10.04.
I like it because my drivers work properly and its faster on an older pc like mine

---

### Post by viraf87 on 2011-10-09
I managed to sort out the problems (once again the forums came to my rescue).  Ubuntu One was devouring my CPU so I removed it.  

The sound problem was fixed by

[http://turbolinux.org/tag/ubuntu-waiting-for-sound-system-to-respond/](http://turbolinux.org/tag/ubuntu-waiting-for-sound-system-to-respond/)

So far I'm one day in on the new install and following the bumpy ride at the start all seems to be going well now.  Hopefully this'll continue.

Thanks everyone for the tips and help

Viraf

---

### Post by viperdvman on 2011-10-09
> **amjjawad said:**
> The Bold answer ;)

Well that's kind of unfair for those of us who dual-boot. It takes time for the BIOS to load up, then you gotta select Ubuntu in your bootloader (Windows or GRUB or LILO), and then let Ubuntu do its booting.

That's why I time it from the moment my bootloader starts loading Ubuntu. But, I could time it from the moment I turn my computer on too.

---

### Post by amjjawad on 2011-10-09
> **viperdvman said:**
> Well that's kind of **unfair **for those of us who dual-boot. It takes time for the BIOS to load up, then you gotta select Ubuntu in your bootloader (Windows or GRUB or LILO), and then let Ubuntu do its booting.

That's why I time it from the moment my bootloader starts loading Ubuntu. But, I could time it from the moment I turn my computer on too.

Unfair? I don't see that as "unfair" at all :)
What you are doing is you are ignoring the "Booting Time" and you are just calculating/timing the "OS Loading Time" which is IMHO is not what we were talking about :)

If you are Dual-Booting, I'm Multi-Booting (XP, Ubuntu 11.04, Lubuntu 11.04 and Lubuntu 11.10). I wouldn't call that unfair :P

Anyway, I'm using IDE HDD, that's why my overall booting time is long (60-70 seconds).
SATA must be faster, I guess. I can't connect my SATA HDD because I'm using my PC for testing only these days.

---

### Post by viperdvman on 2011-10-10
Well of course computers that run only one OS are going to boot up a little faster than ones that dual- or multi-boot. That extra few seconds that you have to select your operating system does come into play. That's just the few seconds that's human-controlled :)

Like I said, when I can, I'll time both my computer bootup and OS bootup. :D

---

### Post by amjjawad on 2011-10-10
> **viperdvman said:**
> Like I said, when I can, I'll time both my computer bootup and OS bootup. :D

Yes, you right. I misread your last line in your last post :P

---

