---
title: "Halt or freeze too often"
date: 2011-09-19
forum: General Help
---

### Post by romanegloo on 2011-09-19
I don't know where to start. My ubuntu (11.04 on LG xnote p210) frequently stops with no reason. Sometimes it stops while it plays musics, sometimes stops while trying to find a wireless networks. I can't tell you the specific moment it stops. Please guide me where to find the problem from. I can post whatever you guys want me to. Help!

I am not sure if this can help to find the problem. Following is dmesg.
```

[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.38-11-generic-pae (buildd@rothera) (gcc version 4.5.2 (Ubuntu/Linaro 4.5.2-8ubuntu4) ) #48-Ubuntu SMP Fri Jul 29 20:51:21 UTC 2011 (Ubuntu 2.6.38-11.48-generic-pae 2.6.38.8)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009c400 (usable)
[    0.000000]  BIOS-e820: 000000000009c400 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 00000000bb27c000 (usable)
[    0.000000]  BIOS-e820: 00000000bb27c000 - 00000000bb282000 (reserved)
[    0.000000]  BIOS-e820: 00000000bb282000 - 00000000bb3ee000 (usable)
[    0.000000]  BIOS-e820: 00000000bb3ee000 - 00000000bb40f000 (reserved)
[    0.000000]  BIOS-e820: 00000000bb40f000 - 00000000bb46f000 (usable)
[    0.000000]  BIOS-e820: 00000000bb46f000 - 00000000bb470000 (reserved)
[    0.000000]  BIOS-e820: 00000000bb470000 - 00000000bb4f1000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000bb4f1000 - 00000000bb70f000 (reserved)
[    0.000000]  BIOS-e820: 00000000bb70f000 - 00000000bb718000 (usable)
[    0.000000]  BIOS-e820: 00000000bb718000 - 00000000bb71f000 (reserved)
[    0.000000]  BIOS-e820: 00000000bb71f000 - 00000000bb780000 (usable)
[    0.000000]  BIOS-e820: 00000000bb780000 - 00000000bb79f000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000bb79f000 - 00000000bb7cd000 (usable)
[    0.000000]  BIOS-e820: 00000000bb7cd000 - 00000000bb7ff000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000bb7ff000 - 00000000bb800000 (usable)
[    0.000000]  BIOS-e820: 00000000bb800000 - 00000000c0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000f080a000 - 00000000f080b000 (reserved)
[    0.000000]  BIOS-e820: 00000000feaff000 - 00000000feb00000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed00000 - 00000000fed00400 (reserved)
[    0.000000]  BIOS-e820: 00000000fed1c000 - 00000000fed90000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000ff000000 - 0000000100000000 (reserved)
[    0.000000]  BIOS-e820: 0000000100000000 - 0000000138000000 (usable)
[    0.000000] NX (Execute Disable) protection: active
[    0.000000] DMI present.
[    0.000000] DMI: LG Electronics Inc. P210-GE30K/PLUTO                           , BIOS PLUTSF07 12/31/2010
[    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
[    0.000000] e820 remove range: 00000000000a0000 - 0000000000100000 (usable)
[    0.000000] last_pfn = 0x138000 max_arch_pfn = 0x1000000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-CFFFF write-protect
[    0.000000]   D0000-DBFFF uncachable
[    0.000000]   DC000-FFFFF write-through
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 disabled
[    0.000000]   1 base 000000000 mask F80000000 write-back
[    0.000000]   2 base 080000000 mask FC0000000 write-back
[    0.000000]   3 base 100000000 mask FC0000000 write-back
[    0.000000]   4 base 138000000 mask FF8000000 uncachable
[    0.000000]   5 base 0BC000000 mask FFC000000 uncachable
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] e820 update range: 00000000bc000000 - 0000000100000000 (usable) ==> (reserved)
[    0.000000] found SMP MP-table at [c00f6990] f6990
[    0.000000] initial memory mapped : 0 - 01e00000
[    0.000000] init_memory_mapping: 0000000000000000-0000000037bfe000
[    0.000000]  0000000000 - 0000200000 page 4k
[    0.000000]  0000200000 - 0037a00000 page 2M
[    0.000000]  0037a00000 - 0037bfe000 page 4k
[    0.000000] kernel direct mapping tables up to 37bfe000 @ 1dfb000-1e00000
[    0.000000] RAMDISK: 366e2000 - 37369000
[    0.000000] ACPI: RSDP 000f68d0 00024 (v02 PTLTD )
[    0.000000] ACPI: XSDT bb7ef03f 0005C (v01 LGE    LGPC     06040000  LTP 00000000)
[    0.000000] ACPI: FACP bb7cf000 000F4 (v03 INTEL  CALPELLA 06040000 PTEC 00000001)
[    0.000000] ACPI: DSDT bb7d0000 0FB2F (v02 LGE    PLUTO    06040000 INTL 20060912)
[    0.000000] ACPI: FACS bb79bfc0 00040
[    0.000000] ACPI: SLIC bb7fed6a 00176 (v01 LGE    LGPC     06040000 YSB  00000001)
[    0.000000] ACPI: HPET bb7feee0 00038 (v01 INTEL  CALPELLA 06040000 PTEC 00000001)
[    0.000000] ACPI: MCFG bb7fef18 0003C (v01 INTEL  CALPELLA 06040000 PTEC 00000001)
[    0.000000] ACPI: APIC bb7fef54 00084 (v01 PTLTD  ? APIC   06040000  LTP 00000000)
[    0.000000] ACPI: BOOT bb7fefd8 00028 (v01 PTLTD  $SBFTBL$ 06040000  LTP 00000001)
[    0.000000] ACPI: SSDT bb7ce000 009F1 (v01  PmRef    CpuPm 00003000 INTL 20050624)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] 4100MB HIGHMEM available.
[    0.000000] 891MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 37bfe000
[    0.000000]   low ram: 0 - 37bfe000
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000010 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x00037bfe
[    0.000000]   HighMem  0x00037bfe -> 0x00138000
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[9] active PFN ranges
[    0.000000]     0: 0x00000010 -> 0x0000009c
[    0.000000]     0: 0x00000100 -> 0x000bb27c
[    0.000000]     0: 0x000bb282 -> 0x000bb3ee
[    0.000000]     0: 0x000bb40f -> 0x000bb46f
[    0.000000]     0: 0x000bb70f -> 0x000bb718
[    0.000000]     0: 0x000bb71f -> 0x000bb780
[    0.000000]     0: 0x000bb79f -> 0x000bb7cd
[    0.000000]     0: 0x000bb7ff -> 0x000bb800
[    0.000000]     0: 0x00100000 -> 0x00138000
[    0.000000] On node 0 totalpages: 996461
[    0.000000] free_area_init_node: node 0, pgdat c17bac40, node_mem_map f3fe2200
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3948 pages, LIFO batch:0
[    0.000000]   Normal zone: 1752 pages used for memmap
[    0.000000]   Normal zone: 222502 pages, LIFO batch:31
[    0.000000]   HighMem zone: 8201 pages used for memmap
[    0.000000]   HighMem zone: 760026 pages, LIFO batch:31
[    0.000000] Using APIC driver default
[    0.000000] ACPI: PM-Timer IO Port: 0x408
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x04] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x05] enabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x02] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x03] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 high edge)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x8086a701 base: 0xfed00000
[    0.000000] SMP: Allowing 4 CPUs, 0 hotplug CPUs
[    0.000000] nr_irqs_gsi: 40
[    0.000000] PM: Registered nosave memory: 000000000009c000 - 000000000009d000
[    0.000000] PM: Registered nosave memory: 000000000009d000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
[    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at c0000000 (gap: c0000000:20000000)
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] setup_percpu: NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:4 nr_node_ids:1
[    0.000000] PERCPU: Embedded 13 pages/cpu @f7800000 s32320 r0 d20928 u524288
[    0.000000] pcpu-alloc: s32320 r0 d20928 u524288 alloc=1*2097152
[    0.000000] pcpu-alloc: [0] 0 1 2 3 
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 986476
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.38-11-generic-pae root=UUID=97be886e-5166-4573-8b92-91247ddc8607 ro quiet splash vt.handoff=7
[    0.000000] PID hash table entries: 4096 (order: 2, 16384 bytes)
[    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.000000] Initializing CPU#0
[    0.000000] allocated 25558720 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] Initializing HighMem for node 0 (00037bfe:00138000)
[    0.000000] Memory: 3897396k/5111808k available (5351k kernel code, 88448k reserved, 2597k data, 720k init, 3072908k highmem)
[    0.000000] virtual kernel memory layout:
[    0.000000]     fixmap  : 0xfff16000 - 0xfffff000   ( 932 kB)
[    0.000000]     pkmap   : 0xffc00000 - 0xffe00000   (2048 kB)
[    0.000000]     vmalloc : 0xf83fe000 - 0xffbfe000   ( 120 MB)
[    0.000000]     lowmem  : 0xc0000000 - 0xf7bfe000   ( 891 MB)
[    0.000000]       .init : 0xc17c4000 - 0xc1878000   ( 720 kB)
[    0.000000]       .data : 0xc1539e95 - 0xc17c35c0   (2597 kB)
[    0.000000]       .text : 0xc1000000 - 0xc1539e95   (5351 kB)
[    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.000000] SLUB: Genslabs=15, HWalign=64, Order=0-3, MinObjects=0, CPUs=4, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000] 	RCU dyntick-idle grace-period acceleration is enabled.
[    0.000000] 	RCU-based detection of stalled CPUs is disabled.
[    0.000000] NR_IRQS:2304 nr_irqs:712 16
[    0.000000] CPU 0 irqstacks, hard=f7408000 soft=f740a000
[    0.000000] Extended CMOS year: 2000
[    0.000000] vt handoff: transparent VT on vt#7
[    0.000000] Console: colour dummy device 80x25
[    0.000000] console [tty0] enabled
[    0.000000] hpet clockevent registered
[    0.000000] Fast TSC calibration using PIT
[    0.004000] Detected 1333.273 MHz processor.
[    0.000003] Calibrating delay loop (skipped), value calculated using timer frequency.. 2666.54 BogoMIPS (lpj=5333092)
[    0.000009] pid_max: default: 32768 minimum: 301
[    0.000034] Security Framework initialized
[    0.000051] AppArmor: AppArmor initialized
[    0.000053] Yama: becoming mindful.
[    0.000126] Mount-cache hash table entries: 512
[    0.000274] Initializing cgroup subsys ns
[    0.000279] ns_cgroup deprecated: consider using the 'clone_children' flag without the ns_cgroup.
[    0.000282] Initializing cgroup subsys cpuacct
[    0.000288] Initializing cgroup subsys memory
[    0.000297] Initializing cgroup subsys devices
[    0.000300] Initializing cgroup subsys freezer
[    0.000303] Initializing cgroup subsys net_cls
[    0.000305] Initializing cgroup subsys blkio
[    0.000345] CPU: Physical Processor ID: 0
[    0.000347] CPU: Processor Core ID: 0
[    0.000354] mce: CPU supports 9 MCE banks
[    0.000366] CPU0: Thermal monitoring handled by SMI
[    0.000375] using mwait in idle threads.
[    0.003634] ACPI: Core revision 20110112
[    0.023938] ftrace: allocating 24259 entries in 48 pages
[    0.034973] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.035388] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.075073] CPU0: Intel(R) Core(TM) i5 CPU       U 470  @ 1.33GHz stepping 05
[    0.179220] Performance Events: PEBS fmt1+, Westmere events, Intel PMU driver.
[    0.179229] ... version:                3
[    0.179230] ... bit width:              48
[    0.179232] ... generic registers:      4
[    0.179234] ... value mask:             0000ffffffffffff
[    0.179236] ... max period:             000000007fffffff
[    0.179238] ... fixed-purpose events:   3
[    0.179240] ... event mask:             000000070000000f
[    0.179771] CPU 1 irqstacks, hard=f74d0000 soft=f74d2000
[    0.179776] Booting Node   0, Processors  #1
[    0.190102] Initializing CPU#1
[    0.267240] CPU1: Thermal monitoring handled by SMI
[    0.287408] CPU 2 irqstacks, hard=f74dc000 soft=f74de000
[    0.287413]  #2
[    0.297588] Initializing CPU#2
[    0.375239] CPU2: Thermal monitoring handled by SMI
[    0.395484] CPU 3 irqstacks, hard=f750a000 soft=f750c000
[    0.395489]  #3 Ok.
[    0.405665] Initializing CPU#3
[    0.483232] CPU3: Thermal monitoring handled by SMI
[    0.503322] Brought up 4 CPUs
[    0.503326] Total of 4 processors activated (10666.32 BogoMIPS).
[    0.506466] devtmpfs: initialized
[    0.508094] print_constraints: dummy: 
[    0.508126] Time:  2:19:28  Date: 09/20/11
[    0.508175] NET: Registered protocol family 16
[    0.508306] Trying to unpack rootfs image as initramfs...
[    0.508309] EISA bus registered
[    0.508335] ACPI: bus type pci registered
[    0.508429] PCI: MMCONFIG for domain 0000 [bus 00-ff] at [mem 0xe0000000-0xefffffff] (base 0xe0000000)
[    0.508433] PCI: MMCONFIG at [mem 0xe0000000-0xefffffff] reserved in E820
[    0.508435] PCI: Using MMCONFIG for extended config space
[    0.508438] PCI: Using configuration type 1 for base access
[    0.509597] bio: create slab <bio-0> at 0
[    0.513151] ACPI: EC: Look up EC in DSDT
[    0.523917] [Firmware Bug]: ACPI: BIOS _OSI(Linux) query ignored
[    0.524463] ACPI: SSDT bb71aa98 002E8 (v01  PmRef  Cpu0Ist 00003000 INTL 20050624)
[    0.525299] ACPI: Dynamic OEM Table Load:
[    0.525303] ACPI: SSDT   (null) 002E8 (v01  PmRef  Cpu0Ist 00003000 INTL 20050624)
[    0.525528] ACPI: SSDT bb719018 008A0 (v01  PmRef  Cpu0Cst 00003001 INTL 20050624)
[    0.526306] ACPI: Dynamic OEM Table Load:
[    0.526309] ACPI: SSDT   (null) 008A0 (v01  PmRef  Cpu0Cst 00003001 INTL 20050624)
[    0.567796] ACPI: SSDT bb71a718 00303 (v01  PmRef    ApIst 00003000 INTL 20050624)
[    0.568688] ACPI: Dynamic OEM Table Load:
[    0.568691] ACPI: SSDT   (null) 00303 (v01  PmRef    ApIst 00003000 INTL 20050624)
[    0.603557] ACPI: SSDT bb718d98 00119 (v01  PmRef    ApCst 00003000 INTL 20050624)
[    0.604420] ACPI: Dynamic OEM Table Load:
[    0.604424] ACPI: SSDT   (null) 00119 (v01  PmRef    ApCst 00003000 INTL 20050624)
[    0.898142] Freeing initrd memory: 12828k freed
[    1.535476] ACPI: Interpreter enabled
[    1.535490] ACPI: (supports S0 S3 S4 S5)
[    1.535529] ACPI: Using IOAPIC for interrupt routing
[    1.548484] ACPI: EC: GPE = 0x17, I/O: command/status = 0x66, data = 0x62
[    1.571613] ACPI: No dock devices found.
[    1.571616] HEST: Table not found.
[    1.571621] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
[    1.572193] \_SB_.PCI0:_OSC invalid UUID
[    1.572195] _OSC request data:1 8 1f 
[    1.572202] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-fe])
[    1.573093] pci_root PNP0A08:00: host bridge window [io  0x0000-0x0cf7]
[    1.573096] pci_root PNP0A08:00: host bridge window [io  0x0d00-0xffff]
[    1.573099] pci_root PNP0A08:00: host bridge window [mem 0x000a0000-0x000bffff]
[    1.573103] pci_root PNP0A08:00: host bridge window [mem 0x000d0000-0x000d3fff]
[    1.573106] pci_root PNP0A08:00: host bridge window [mem 0x000d4000-0x000d7fff]
[    1.573109] pci_root PNP0A08:00: host bridge window [mem 0x000d8000-0x000dbfff]
[    1.573112] pci_root PNP0A08:00: host bridge window [mem 0x000dc000-0x000dffff]
[    1.573115] pci_root PNP0A08:00: host bridge window [mem 0xc0000000-0xfeafffff]
[    1.573136] pci 0000:00:00.0: [8086:0044] type 0 class 0x000600
[    1.573166] DMAR: BIOS has allocated no shadow GTT; disabling IOMMU for graphics
[    1.573192] pci 0000:00:02.0: [8086:0046] type 0 class 0x000300
[    1.573209] pci 0000:00:02.0: reg 10: [mem 0xf0000000-0xf03fffff 64bit]
[    1.573219] pci 0000:00:02.0: reg 18: [mem 0xd0000000-0xdfffffff 64bit pref]
[    1.573226] pci 0000:00:02.0: reg 20: [io  0x1800-0x1807]
[    1.573310] pci 0000:00:16.0: [8086:3b64] type 0 class 0x000780
[    1.573349] pci 0000:00:16.0: reg 10: [mem 0xf0804000-0xf080400f 64bit]
[    1.573447] pci 0000:00:16.0: PME# supported from D0 D3hot D3cold
[    1.573454] pci 0000:00:16.0: PME# disabled
[    1.573505] pci 0000:00:1a.0: [8086:3b3c] type 0 class 0x000c03
[    1.573536] pci 0000:00:1a.0: reg 10: [mem 0xf0806000-0xf08063ff]
[    1.573643] pci 0000:00:1a.0: PME# supported from D0 D3hot D3cold
[    1.573649] pci 0000:00:1a.0: PME# disabled
[    1.573686] pci 0000:00:1b.0: [8086:3b56] type 0 class 0x000403
[    1.573713] pci 0000:00:1b.0: reg 10: [mem 0xf0800000-0xf0803fff 64bit]
[    1.573808] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    1.573814] pci 0000:00:1b.0: PME# disabled
[    1.573848] pci 0000:00:1c.0: [8086:3b42] type 1 class 0x000604
[    1.573946] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    1.573952] pci 0000:00:1c.0: PME# disabled
[    1.573986] pci 0000:00:1c.1: [8086:3b44] type 1 class 0x000604
[    1.574083] pci 0000:00:1c.1: PME# supported from D0 D3hot D3cold
[    1.574089] pci 0000:00:1c.1: PME# disabled
[    1.574141] pci 0000:00:1d.0: [8086:3b34] type 0 class 0x000c03
[    1.574172] pci 0000:00:1d.0: reg 10: [mem 0xf0807000-0xf08073ff]
[    1.574280] pci 0000:00:1d.0: PME# supported from D0 D3hot D3cold
[    1.574286] pci 0000:00:1d.0: PME# disabled
[    1.574315] pci 0000:00:1e.0: [8086:2448] type 1 class 0x000604
[    1.574408] pci 0000:00:1f.0: [8086:3b09] type 0 class 0x000601
[    1.574554] pci 0000:00:1f.2: [8086:3b29] type 0 class 0x000106
[    1.574587] pci 0000:00:1f.2: reg 10: [io  0x1818-0x181f]
[    1.574601] pci 0000:00:1f.2: reg 14: [io  0x180c-0x180f]
[    1.574614] pci 0000:00:1f.2: reg 18: [io  0x1810-0x1817]
[    1.574629] pci 0000:00:1f.2: reg 1c: [io  0x1808-0x180b]
[    1.574643] pci 0000:00:1f.2: reg 20: [io  0x1820-0x183f]
[    1.574657] pci 0000:00:1f.2: reg 24: [mem 0xf0808000-0xf08087ff]
[    1.574716] pci 0000:00:1f.2: PME# supported from D3hot
[    1.574721] pci 0000:00:1f.2: PME# disabled
[    1.574750] pci 0000:00:1f.3: [8086:3b30] type 0 class 0x000c05
[    1.574777] pci 0000:00:1f.3: reg 10: [mem 0xf0809000-0xf08090ff 64bit]
[    1.574813] pci 0000:00:1f.3: reg 20: [io  0x1840-0x185f]
[    1.574871] pci 0000:00:1f.6: [8086:3b32] type 0 class 0x001180
[    1.574905] pci 0000:00:1f.6: reg 10: [mem 0xf080a000-0xf080afff 64bit]
[    1.575116] pci 0000:02:00.0: [1814:3090] type 0 class 0x000280
[    1.575144] pci 0000:02:00.0: reg 10: [mem 0xf0500000-0xf050ffff]
[    1.583298] pci 0000:00:1c.0: PCI bridge to [bus 02-03]
[    1.583306] pci 0000:00:1c.0:   bridge window [io  0x2000-0x2fff]
[    1.583312] pci 0000:00:1c.0:   bridge window [mem 0xf0500000-0xf05fffff]
[    1.583322] pci 0000:00:1c.0:   bridge window [mem 0xf0c00000-0xf0dfffff 64bit pref]
[    1.583464] pci 0000:04:00.0: [10ec:8136] type 0 class 0x000200
[    1.583537] pci 0000:04:00.0: reg 10: [io  0x3000-0x30ff]
[    1.583661] pci 0000:04:00.0: reg 18: [mem 0xf0900000-0xf0900fff 64bit pref]
[    1.583737] pci 0000:04:00.0: reg 20: [mem 0xf0a10000-0xf0a1ffff 64bit pref]
[    1.583787] pci 0000:04:00.0: reg 30: [mem 0x00000000-0x0001ffff pref]
[    1.583962] pci 0000:04:00.0: supports D1 D2
[    1.583965] pci 0000:04:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    1.583993] pci 0000:04:00.0: PME# disabled
[    1.584165] pci 0000:00:1c.1: PCI bridge to [bus 04-05]
[    1.584171] pci 0000:00:1c.1:   bridge window [io  0x3000-0x3fff]
[    1.584177] pci 0000:00:1c.1:   bridge window [mem 0xf0400000-0xf04fffff]
[    1.584186] pci 0000:00:1c.1:   bridge window [mem 0xf0900000-0xf0bfffff 64bit pref]
[    1.584277] pci 0000:00:1e.0: PCI bridge to [bus 06-06] (subtractive decode)
[    1.584284] pci 0000:00:1e.0:   bridge window [io  0xf000-0x0000] (disabled)
[    1.584291] pci 0000:00:1e.0:   bridge window [mem 0xfff00000-0x000fffff] (disabled)
[    1.584300] pci 0000:00:1e.0:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    1.584304] pci 0000:00:1e.0:   bridge window [io  0x0000-0x0cf7] (subtractive decode)
[    1.584307] pci 0000:00:1e.0:   bridge window [io  0x0d00-0xffff] (subtractive decode)
[    1.584310] pci 0000:00:1e.0:   bridge window [mem 0x000a0000-0x000bffff] (subtractive decode)
[    1.584313] pci 0000:00:1e.0:   bridge window [mem 0x000d0000-0x000d3fff] (subtractive decode)
[    1.584316] pci 0000:00:1e.0:   bridge window [mem 0x000d4000-0x000d7fff] (subtractive decode)
[    1.584319] pci 0000:00:1e.0:   bridge window [mem 0x000d8000-0x000dbfff] (subtractive decode)
[    1.584323] pci 0000:00:1e.0:   bridge window [mem 0x000dc000-0x000dffff] (subtractive decode)
[    1.584326] pci 0000:00:1e.0:   bridge window [mem 0xc0000000-0xfeafffff] (subtractive decode)
[    1.584351] pci_bus 0000:00: on NUMA node 0
[    1.584355] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    1.584706] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P1._PRT]
[    1.584932] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP01._PRT]
[    1.585020] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP02._PRT]
[    1.585205] \_SB_.PCI0:_OSC invalid UUID
[    1.585207] _OSC request data:1 1f 1f 
[    1.585214]  pci0000:00: Requesting ACPI _OSC control (0x1d)
[    1.585263] \_SB_.PCI0:_OSC invalid UUID
[    1.585265] _OSC request data:1 0 1d 
[    1.592232] ACPI: PCI Root Bridge [CPBG] (domain 0000 [bus ff])
[    1.592329] pci 0000:ff:00.0: [8086:2c62] type 0 class 0x000600
[    1.592360] pci 0000:ff:00.1: [8086:2d01] type 0 class 0x000600
[    1.592391] pci 0000:ff:02.0: [8086:2d10] type 0 class 0x000600
[    1.592416] pci 0000:ff:02.1: [8086:2d11] type 0 class 0x000600
[    1.592442] pci 0000:ff:02.2: [8086:2d12] type 0 class 0x000600
[    1.592468] pci 0000:ff:02.3: [8086:2d13] type 0 class 0x000600
[    1.592508] pci_bus 0000:ff: on NUMA node 0
[    1.592519]  pci0000:ff: Requesting ACPI _OSC control (0x1d)
[    1.592865] ACPI: PCI Interrupt Link [LNKA] (IRQs 1 3 4 5 6 7 10 12 14 15) *11
[    1.592934] ACPI: PCI Interrupt Link [LNKB] (IRQs 1 3 4 5 6 7 11 12 14 15) *10
[    1.593001] ACPI: PCI Interrupt Link [LNKC] (IRQs 1 3 4 5 6 7 *10 12 14 15)
[    1.593066] ACPI: PCI Interrupt Link [LNKD] (IRQs 1 3 4 *5 6 7 11 12 14 15)
[    1.593132] ACPI: PCI Interrupt Link [LNKE] (IRQs 1 3 4 5 6 7 10 12 14 15) *0, disabled.
[    1.593201] ACPI: PCI Interrupt Link [LNKF] (IRQs 1 3 4 5 6 7 11 12 14 15) *0, disabled.
[    1.593268] ACPI: PCI Interrupt Link [LNKG] (IRQs 1 3 4 5 6 *7 10 12 14 15)
[    1.593333] ACPI: PCI Interrupt Link [LNKH] (IRQs 1 3 4 5 6 7 *11 12 14 15)
[    1.593476] vgaarb: device added: PCI:0000:00:02.0,decodes=io+mem,owns=io+mem,locks=none
[    1.593489] vgaarb: loaded
[    1.593735] SCSI subsystem initialized
[    1.593805] libata version 3.00 loaded.
[    1.593859] usbcore: registered new interface driver usbfs
[    1.593872] usbcore: registered new interface driver hub
[    1.593904] usbcore: registered new device driver usb
[    1.594248] wmi: Mapper loaded
[    1.594251] PCI: Using ACPI for IRQ routing
[    1.594254] PCI: pci_cache_line_size set to 64 bytes
[    1.594395] reserve RAM buffer: 000000000009c400 - 000000000009ffff 
[    1.594399] reserve RAM buffer: 00000000bb27c000 - 00000000bbffffff 
[    1.594406] reserve RAM buffer: 00000000bb3ee000 - 00000000bbffffff 
[    1.594413] reserve RAM buffer: 00000000bb46f000 - 00000000bbffffff 
[    1.594419] reserve RAM buffer: 00000000bb718000 - 00000000bbffffff 
[    1.594423] reserve RAM buffer: 00000000bb780000 - 00000000bbffffff 
[    1.594427] reserve RAM buffer: 00000000bb7cd000 - 00000000bbffffff 
[    1.594430] reserve RAM buffer: 00000000bb800000 - 00000000bbffffff 
[    1.594555] NetLabel: Initializing
[    1.594558] NetLabel:  domain hash size = 128
[    1.594559] NetLabel:  protocols = UNLABELED CIPSOv4
[    1.594573] NetLabel:  unlabeled traffic allowed by default
[    1.594624] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0, 0, 0, 0, 0
[    1.594632] hpet0: 8 comparators, 64-bit 14.318180 MHz counter
[    1.596663] Switching to clocksource hpet
[    1.599178] Switched to NOHz mode on CPU #0
[    1.599254] Switched to NOHz mode on CPU #1
[    1.599280] Switched to NOHz mode on CPU #3
[    1.599321] Switched to NOHz mode on CPU #2
[    1.605330] AppArmor: AppArmor Filesystem Enabled
[    1.605361] pnp: PnP ACPI init
[    1.605383] ACPI: bus type pnp registered
[    1.605875] pnp 00:00: [bus 00-fe]
[    1.605879] pnp 00:00: [io  0x0000-0x0cf7 window]
[    1.605882] pnp 00:00: [io  0x0cf8-0x0cff]
[    1.605885] pnp 00:00: [io  0x0d00-0xffff window]
[    1.605888] pnp 00:00: [mem 0x000a0000-0x000bffff window]
[    1.605891] pnp 00:00: [mem 0x000c0000-0x000c3fff window]
[    1.605894] pnp 00:00: [mem 0x000c4000-0x000c7fff window]
[    1.605896] pnp 00:00: [mem 0x000c8000-0x000cbfff window]
[    1.605899] pnp 00:00: [mem 0x000cc000-0x000cffff window]
[    1.605902] pnp 00:00: [mem 0x000d0000-0x000d3fff window]
[    1.605905] pnp 00:00: [mem 0x000d4000-0x000d7fff window]
[    1.605907] pnp 00:00: [mem 0x000d8000-0x000dbfff window]
[    1.605910] pnp 00:00: [mem 0x000dc000-0x000dffff window]
[    1.605913] pnp 00:00: [mem 0x000e0000-0x000e3fff window]
[    1.605916] pnp 00:00: [mem 0x000e4000-0x000e7fff window]
[    1.605919] pnp 00:00: [mem 0x000e8000-0x000ebfff window]
[    1.605921] pnp 00:00: [mem 0x000ec000-0x000effff window]
[    1.605924] pnp 00:00: [mem 0x000f0000-0x000fffff window]
[    1.605927] pnp 00:00: [mem 0xc0000000-0xfeafffff window]
[    1.605930] pnp 00:00: [mem 0xfed40000-0xfed44fff window]
[    1.606039] pnp 00:00: Plug and Play ACPI device, IDs PNP0a08 PNP0a03 (active)
[    1.606091] pnp 00:01: [io  0x0000-0x001f]
[    1.606093] pnp 00:01: [io  0x0081-0x0091]
[    1.606096] pnp 00:01: [io  0x0093-0x009f]
[    1.606098] pnp 00:01: [io  0x00c0-0x00df]
[    1.606101] pnp 00:01: [dma 4]
[    1.606138] pnp 00:01: Plug and Play ACPI device, IDs PNP0200 (active)
[    1.606149] pnp 00:02: [mem 0xff000000-0xffffffff]
[    1.606184] pnp 00:02: Plug and Play ACPI device, IDs INT0800 (active)
[    1.606287] pnp 00:03: [irq 0 disabled]
[    1.606301] pnp 00:03: [irq 8]
[    1.606304] pnp 00:03: [mem 0xfed00000-0xfed003ff]
[    1.606343] pnp 00:03: Plug and Play ACPI device, IDs PNP0103 (active)
[    1.606358] pnp 00:04: [io  0x00f0]
[    1.606365] pnp 00:04: [irq 13]
[    1.606402] pnp 00:04: Plug and Play ACPI device, IDs PNP0c04 (active)
[    1.606418] pnp 00:05: [io  0x002e-0x002f]
[    1.606420] pnp 00:05: [io  0x004e-0x004f]
[    1.606423] pnp 00:05: [io  0x0061]
[    1.606425] pnp 00:05: [io  0x0063]
[    1.606427] pnp 00:05: [io  0x0065]
[    1.606429] pnp 00:05: [io  0x0067]
[    1.606432] pnp 00:05: [io  0x0070]
[    1.606434] pnp 00:05: [io  0x0080]
[    1.606436] pnp 00:05: [io  0x0092]
[    1.606438] pnp 00:05: [io  0x00b2-0x00b3]
[    1.606441] pnp 00:05: [io  0x0680-0x069f]
[    1.606443] pnp 00:05: [io  0x0500-0x050f]
[    1.606446] pnp 00:05: [io  0x0600-0x0603]
[    1.606448] pnp 00:05: [io  0xffff]
[    1.606450] pnp 00:05: [io  0x0400-0x047f]
[    1.606453] pnp 00:05: [io  0x1180-0x11ff]
[    1.606455] pnp 00:05: [io  0x164e-0x164f]
[    1.606458] pnp 00:05: [io  0xfe00]
[    1.606543] system 00:05: [io  0x0680-0x069f] has been reserved
[    1.606546] system 00:05: [io  0x0500-0x050f] has been reserved
[    1.606550] system 00:05: [io  0x0600-0x0603] has been reserved
[    1.606553] system 00:05: [io  0xffff] has been reserved
[    1.606556] system 00:05: [io  0x0400-0x047f] has been reserved
[    1.606559] system 00:05: [io  0x1180-0x11ff] has been reserved
[    1.606563] system 00:05: [io  0x164e-0x164f] has been reserved
[    1.606566] system 00:05: [io  0xfe00] has been reserved
[    1.606570] system 00:05: Plug and Play ACPI device, IDs PNP0c02 (active)
[    1.606611] pnp 00:06: [io  0x06a0-0x06af]
[    1.606614] pnp 00:06: [io  0x06b0-0x06ff]
[    1.606675] system 00:06: [io  0x06a0-0x06af] has been reserved
[    1.606678] system 00:06: [io  0x06b0-0x06ff] has been reserved
[    1.606682] system 00:06: Plug and Play ACPI device, IDs PNP0c02 (active)
[    1.606722] pnp 00:07: [io  0x0070-0x0077]
[    1.606762] pnp 00:07: Plug and Play ACPI device, IDs PNP0b00 (active)
[    1.606837] pnp 00:08: [io  0x0060]
[    1.606841] pnp 00:08: [io  0x0064]
[    1.606848] pnp 00:08: [irq 1]
[    1.606891] pnp 00:08: Plug and Play ACPI device, IDs PNP0303 (active)
[    1.606907] pnp 00:09: [irq 12]
[    1.606946] pnp 00:09: Plug and Play ACPI device, IDs PNP0f13 (active)
[    1.607403] pnp 00:0a: [mem 0xfed1c000-0xfed1ffff]
[    1.607407] pnp 00:0a: [mem 0xfed10000-0xfed13fff]
[    1.607409] pnp 00:0a: [mem 0xfed18000-0xfed18fff]
[    1.607412] pnp 00:0a: [mem 0xfed19000-0xfed19fff]
[    1.607415] pnp 00:0a: [mem 0xe0000000-0xefffffff]
[    1.607417] pnp 00:0a: [mem 0x00000000-0xffffffffffffffff disabled]
[    1.607420] pnp 00:0a: [mem 0xfeaff000-0xfeafffff]
[    1.607423] pnp 00:0a: [mem 0xfed20000-0xfed3ffff]
[    1.607426] pnp 00:0a: [mem 0xfed90000-0xfed8ffff disabled]
[    1.607428] pnp 00:0a: [mem 0xfed40000-0xfed44fff]
[    1.607431] pnp 00:0a: [mem 0xfed45000-0xfed8ffff]
[    1.607433] pnp 00:0a: [mem 0xff000000-0xffffffff]
[    1.607436] pnp 00:0a: [mem 0xfee00000-0xfeefffff]
[    1.607535] system 00:0a: [mem 0xfed1c000-0xfed1ffff] has been reserved
[    1.607539] system 00:0a: [mem 0xfed10000-0xfed13fff] has been reserved
[    1.607543] system 00:0a: [mem 0xfed18000-0xfed18fff] has been reserved
[    1.607546] system 00:0a: [mem 0xfed19000-0xfed19fff] has been reserved
[    1.607550] system 00:0a: [mem 0xe0000000-0xefffffff] has been reserved
[    1.607553] system 00:0a: [mem 0xfeaff000-0xfeafffff] has been reserved
[    1.607557] system 00:0a: [mem 0xfed20000-0xfed3ffff] has been reserved
[    1.607560] system 00:0a: [mem 0xfed40000-0xfed44fff] has been reserved
[    1.607564] system 00:0a: [mem 0xfed45000-0xfed8ffff] has been reserved
[    1.607567] system 00:0a: [mem 0xff000000-0xffffffff] has been reserved
[    1.607571] system 00:0a: [mem 0xfee00000-0xfeefffff] could not be reserved
[    1.607575] system 00:0a: Plug and Play ACPI device, IDs PNP0c02 (active)
[    1.608122] pnp 00:0b: [bus ff]
[    1.608248] pnp 00:0b: Plug and Play ACPI device, IDs PNP0a03 (active)
[    1.608266] pnp: PnP ACPI: found 12 devices
[    1.608268] ACPI: ACPI bus type pnp unregistered
[    1.608273] PnPBIOS: Disabled by ACPI PNP
[    1.644965] pci 0000:00:1c.0: PCI bridge to [bus 02-03]
[    1.644971] pci 0000:00:1c.0:   bridge window [io  0x2000-0x2fff]
[    1.644979] pci 0000:00:1c.0:   bridge window [mem 0xf0500000-0xf05fffff]
[    1.644986] pci 0000:00:1c.0:   bridge window [mem 0xf0c00000-0xf0dfffff 64bit pref]
[    1.645001] pci 0000:04:00.0: BAR 6: assigned [mem 0xf0920000-0xf093ffff pref]
[    1.645004] pci 0000:00:1c.1: PCI bridge to [bus 04-05]
[    1.645009] pci 0000:00:1c.1:   bridge window [io  0x3000-0x3fff]
[    1.645017] pci 0000:00:1c.1:   bridge window [mem 0xf0400000-0xf04fffff]
[    1.645023] pci 0000:00:1c.1:   bridge window [mem 0xf0900000-0xf0bfffff 64bit pref]
[    1.645033] pci 0000:00:1e.0: PCI bridge to [bus 06-06]
[    1.645035] pci 0000:00:1e.0:   bridge window [io  disabled]
[    1.645042] pci 0000:00:1e.0:   bridge window [mem disabled]
[    1.645048] pci 0000:00:1e.0:   bridge window [mem pref disabled]
[    1.645076] pci 0000:00:1c.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.645084] pci 0000:00:1c.0: setting latency timer to 64
[    1.645098] pci 0000:00:1c.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    1.645104] pci 0000:00:1c.1: setting latency timer to 64
[    1.645115] pci 0000:00:1e.0: setting latency timer to 64
[    1.645121] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
[    1.645124] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff]
[    1.645127] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
[    1.645130] pci_bus 0000:00: resource 7 [mem 0x000d0000-0x000d3fff]
[    1.645132] pci_bus 0000:00: resource 8 [mem 0x000d4000-0x000d7fff]
[    1.645135] pci_bus 0000:00: resource 9 [mem 0x000d8000-0x000dbfff]
[    1.645138] pci_bus 0000:00: resource 10 [mem 0x000dc000-0x000dffff]
[    1.645141] pci_bus 0000:00: resource 11 [mem 0xc0000000-0xfeafffff]
[    1.645144] pci_bus 0000:02: resource 0 [io  0x2000-0x2fff]
[    1.645147] pci_bus 0000:02: resource 1 [mem 0xf0500000-0xf05fffff]
[    1.645150] pci_bus 0000:02: resource 2 [mem 0xf0c00000-0xf0dfffff 64bit pref]
[    1.645153] pci_bus 0000:04: resource 0 [io  0x3000-0x3fff]
[    1.645156] pci_bus 0000:04: resource 1 [mem 0xf0400000-0xf04fffff]
[    1.645159] pci_bus 0000:04: resource 2 [mem 0xf0900000-0xf0bfffff 64bit pref]
[    1.645163] pci_bus 0000:06: resource 4 [io  0x0000-0x0cf7]
[    1.645166] pci_bus 0000:06: resource 5 [io  0x0d00-0xffff]
[    1.645168] pci_bus 0000:06: resource 6 [mem 0x000a0000-0x000bffff]
[    1.645171] pci_bus 0000:06: resource 7 [mem 0x000d0000-0x000d3fff]
[    1.645174] pci_bus 0000:06: resource 8 [mem 0x000d4000-0x000d7fff]
[    1.645177] pci_bus 0000:06: resource 9 [mem 0x000d8000-0x000dbfff]
[    1.645180] pci_bus 0000:06: resource 10 [mem 0x000dc000-0x000dffff]
[    1.645183] pci_bus 0000:06: resource 11 [mem 0xc0000000-0xfeafffff]
[    1.645222] NET: Registered protocol family 2
[    1.645293] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    1.645541] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    1.645942] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    1.646123] TCP: Hash tables configured (established 131072 bind 65536)
[    1.646126] TCP reno registered
[    1.646129] UDP hash table entries: 512 (order: 2, 16384 bytes)
[    1.646137] UDP-Lite hash table entries: 512 (order: 2, 16384 bytes)
[    1.646225] NET: Registered protocol family 1
[    1.646241] pci 0000:00:02.0: Boot video device
[    1.646356] PCI: CLS 64 bytes, default 64
[    1.646382] Simple Boot Flag at 0x36 set to 0x1
[    1.646768] cpufreq-nforce2: No nForce2 chipset.
[    1.646971] audit: initializing netlink socket (disabled)
[    1.646982] type=2000 audit(1316485169.472:1): initialized
[    1.660501] highmem bounce pool size: 64 pages
[    1.660508] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    1.662676] VFS: Disk quotas dquot_6.5.2
[    1.662749] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    1.663563] fuse init (API version 7.16)
[    1.663677] msgmni has been set to 1635
[    1.663971] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    1.664006] io scheduler noop registered
[    1.664009] io scheduler deadline registered
[    1.664028] io scheduler cfq registered (default)
[    1.664311] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    1.664340] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    1.664420] intel_idle: MWAIT substates: 0x1120
[    1.664423] intel_idle: v0.4 model 0x25
[    1.664424] intel_idle: lapic_timer_reliable_states 0xffffffff
[    1.664828] ACPI: Deprecated procfs I/F for AC is loaded, please retry with CONFIG_ACPI_PROCFS_POWER cleared
[    1.665166] ACPI: AC Adapter [AC] (on-line)
[    1.665361] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input0
[    1.728612] ACPI: Lid Switch [LID0]
[    1.728715] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1
[    1.752673] ACPI: Power Button [PWRB]
[    1.752743] input: Sleep Button as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input2
[    1.752747] ACPI: Sleep Button [SLPB]
[    1.752799] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input3
[    1.752803] ACPI: Power Button [PWRF]
[    1.753117] ACPI: acpi_idle yielding to intel_idle
[    1.759053] thermal LNXTHERM:00: registered as thermal_zone0
[    1.759057] ACPI: Thermal Zone [TZ00] (57 C)
[    1.759186] ERST: Table is not found!
[    1.759296] isapnp: Scanning for PnP cards...
[    1.759355] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    2.113990] isapnp: No Plug & Play device found
[    2.644624] Refined TSC clocksource calibration: 1333.332 MHz.
[    2.644631] Switching to clocksource tsc
[    2.766047] ACPI: Deprecated procfs I/F for battery is loaded, please retry with CONFIG_ACPI_PROCFS_POWER cleared
[    2.766054] ACPI: Battery Slot [CMB0] (battery present)
[    2.770086] Linux agpgart interface v0.103
[    2.770210] agpgart-intel 0000:00:00.0: Intel HD Graphics Chipset
[    2.770405] agpgart-intel 0000:00:00.0: detected gtt size: 2097152K total, 262144K mappable
[    2.771658] agpgart-intel 0000:00:00.0: detected 32768K stolen memory
[    2.771830] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0xd0000000
[    2.773376] brd: module loaded
[    2.774095] loop: module loaded
[    2.774209] i2c-core: driver [adp5520] using legacy suspend method
[    2.774212] i2c-core: driver [adp5520] using legacy resume method
[    2.774752] Fixed MDIO Bus: probed
[    2.774789] PPP generic driver version 2.4.2
[    2.774834] tun: Universal TUN/TAP device driver, 1.6
[    2.774836] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    2.774936] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    2.774963] ehci_hcd 0000:00:1a.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    2.774988] ehci_hcd 0000:00:1a.0: setting latency timer to 64
[    2.774993] ehci_hcd 0000:00:1a.0: EHCI Host Controller
[    2.775040] ehci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 1
[    2.775114] ehci_hcd 0000:00:1a.0: debug port 2
[    2.779006] ehci_hcd 0000:00:1a.0: cache line size of 64 is not supported
[    2.779032] ehci_hcd 0000:00:1a.0: irq 16, io mem 0xf0806000
[    2.792612] ehci_hcd 0000:00:1a.0: USB 2.0 started, EHCI 1.00
[    2.792800] hub 1-0:1.0: USB hub found
[    2.792806] hub 1-0:1.0: 3 ports detected
[    2.792901] ehci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    2.792917] ehci_hcd 0000:00:1d.0: setting latency timer to 64
[    2.792922] ehci_hcd 0000:00:1d.0: EHCI Host Controller
[    2.792977] ehci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    2.793034] ehci_hcd 0000:00:1d.0: debug port 2
[    2.797020] ehci_hcd 0000:00:1d.0: cache line size of 64 is not supported
[    2.797038] ehci_hcd 0000:00:1d.0: irq 23, io mem 0xf0807000
[    2.812611] ehci_hcd 0000:00:1d.0: USB 2.0 started, EHCI 1.00
[    2.812784] hub 2-0:1.0: USB hub found
[    2.812789] hub 2-0:1.0: 3 ports detected
[    2.812876] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    2.812891] uhci_hcd: USB Universal Host Controller Interface driver
[    2.812989] i8042: PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    2.815504] i8042: Detected active multiplexing controller, rev 1.1
[    2.818379] serio: i8042 KBD port at 0x60,0x64 irq 1
[    2.818387] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[    2.818425] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[    2.818455] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[    2.818488] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[    2.818624] mousedev: PS/2 mouse device common for all mice
[    2.820712] rtc_cmos 00:07: rtc core: registered rtc_cmos as rtc0
[    2.820747] rtc0: alarms up to one month, y3k, 242 bytes nvram, hpet irqs
[    2.820839] device-mapper: uevent: version 1.0.3
[    2.820933] device-mapper: ioctl: 4.19.1-ioctl (2011-01-07) initialised: dm-devel@redhat.com
[    2.821015] device-mapper: multipath: version 1.2.0 loaded
[    2.821020] device-mapper: multipath round-robin: version 1.0.0 loaded
[    2.821103] EISA: Probing bus 0 at eisa.0
[    2.821106] EISA: Cannot allocate resource for mainboard
[    2.821109] Cannot allocate resource for EISA slot 1
[    2.821111] Cannot allocate resource for EISA slot 2
[    2.821113] Cannot allocate resource for EISA slot 3
[    2.821115] Cannot allocate resource for EISA slot 4
[    2.821117] Cannot allocate resource for EISA slot 5
[    2.821119] Cannot allocate resource for EISA slot 6
[    2.821121] Cannot allocate resource for EISA slot 7
[    2.821123] Cannot allocate resource for EISA slot 8
[    2.821125] EISA: Detected 0 cards.
[    2.821307] cpuidle: using governor ladder
[    2.821510] cpuidle: using governor menu
[    2.821823] TCP cubic registered
[    2.821978] NET: Registered protocol family 10
[    2.822614] NET: Registered protocol family 17
[    2.822631] Registering the dns_resolver key type
[    2.825036] Using IPI No-Shortcut mode
[    2.825141] PM: Hibernation image not present or could not be loaded.
[    2.825153] registered taskstats version 1
[    2.825522]   Magic number: 11:2:309
[    2.825545] tty tty38: hash matches
[    2.825668] rtc_cmos 00:07: setting system clock to 2011-09-20 02:19:31 UTC (1316485171)
[    2.825672] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    2.825674] EDD information not available.
[    2.826011] Freeing unused kernel memory: 720k freed
[    2.826316] Write protecting the kernel text: 5352k
[    2.826425] Write protecting the kernel read-only data: 2192k
[    2.826426] NX-protecting the kernel data: 4888k
[    2.829410] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input4
[    2.852342] <30>udev[71]: starting version 167
[    2.904793] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    2.904856] r8169 0000:04:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    2.904994] r8169 0000:04:00.0: setting latency timer to 64
[    2.905243] r8169 0000:04:00.0: irq 40 for MSI/MSI-X
[    2.906252] r8169 0000:04:00.0: eth0: RTL8102e at 0xf8442000, 00:e0:91:26:40:8a, XID 14c00000 IRQ 40
[    2.944961] ahci 0000:00:1f.2: version 3.0
[    2.944994] ahci 0000:00:1f.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    2.945063] ahci 0000:00:1f.2: irq 41 for MSI/MSI-X
[    2.945108] ahci: SSS flag set, parallel bus scan disabled
[    2.945143] ahci 0000:00:1f.2: AHCI 0001.0300 32 slots 4 ports 3 Gbps 0x1 impl SATA mode
[    2.945147] ahci 0000:00:1f.2: flags: 64bit ncq sntf ilck stag pm led clo pio slum part ems apst 
[    2.945154] ahci 0000:00:1f.2: setting latency timer to 64
[    2.945763] scsi0 : ahci
[    2.946046] scsi1 : ahci
[    2.946151] scsi2 : ahci
[    2.946262] scsi3 : ahci
[    2.946343] ata1: SATA max UDMA/133 abar m2048@0xf0808000 port 0xf0808100 irq 41
[    2.946346] ata2: DUMMY
[    2.946348] ata3: DUMMY
[    2.946349] ata4: DUMMY
[    3.104679] usb 1-1: new high speed USB device using ehci_hcd and address 2
[    3.237342] hub 1-1:1.0: USB hub found
[    3.237522] hub 1-1:1.0: 6 ports detected
[    3.264690] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    3.265726] ata1.00: ATA-8: Hitachi HTS543232A7A384, ES2OA60W, max UDMA/133
[    3.265732] ata1.00: 625142448 sectors, multi 16: LBA48 NCQ (depth 31/32), AA
[    3.266965] ata1.00: configured for UDMA/133
[    3.267233] scsi 0:0:0:0: Direct-Access     ATA      Hitachi HTS54323 ES2O PQ: 0 ANSI: 5
[    3.267518] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    3.267537] sd 0:0:0:0: [sda] 625142448 512-byte logical blocks: (320 GB/298 GiB)
[    3.267637] sd 0:0:0:0: [sda] Write Protect is off
[    3.267643] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    3.267682] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    3.330587]  sda: sda1 sda2 < sda5 >
[    3.331069] sd 0:0:0:0: [sda] Attached SCSI disk
[    3.348747] usb 2-1: new high speed USB device using ehci_hcd and address 2
[    3.481691] hub 2-1:1.0: USB hub found
[    3.481870] hub 2-1:1.0: 8 ports detected
[    3.552963] usb 1-1.1: new full speed USB device using ehci_hcd and address 3
[    3.719963] PM: Marking nosave pages: 000000000009c000 - 0000000000100000
[    3.719968] PM: Basic memory bitmaps created
[    3.743353] PM: Basic memory bitmaps freed
[    3.791441] EXT4-fs (sda1): INFO: recovery required on readonly filesystem
[    3.791445] EXT4-fs (sda1): write access will be enabled during recovery
[    3.912976] usb 1-1.6: new high speed USB device using ehci_hcd and address 4
[    4.088837] usb 2-1.2: new full speed USB device using ehci_hcd and address 3
[    4.220921] input: Microsoft Microsoft® Nano Transceiver v2.0 as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.2/2-1.2:1.0/input/input5
[    4.221088] generic-usb 0003:045E:0745.0001: input,hidraw0: USB HID v1.11 Keyboard [Microsoft Microsoft® Nano Transceiver v2.0] on usb-0000:00:1d.0-1.2/input0
[    4.226560] input: Microsoft Microsoft® Nano Transceiver v2.0 as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.2/2-1.2:1.1/input/input6
[    4.226809] generic-usb 0003:045E:0745.0002: input,hidraw1: USB HID v1.11 Mouse [Microsoft Microsoft® Nano Transceiver v2.0] on usb-0000:00:1d.0-1.2/input1
[    4.244314] input: Microsoft Microsoft® Nano Transceiver v2.0 as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.2/2-1.2:1.2/input/input7
[    4.244705] generic-usb 0003:045E:0745.0003: input,hiddev0,hidraw2: USB HID v1.11 Device [Microsoft Microsoft® Nano Transceiver v2.0] on usb-0000:00:1d.0-1.2/input2
[    4.244733] usbcore: registered new interface driver usbhid
[    4.244736] usbhid: USB HID core driver
[    4.661888] EXT4-fs (sda1): orphan cleanup on readonly fs
[    4.661898] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 14683530
[    4.661982] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 2360323
[    4.661992] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 14421428
[    4.662007] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 14421604
[    4.662056] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 2360217
[    4.662070] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 14422489
[    4.662083] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 14418666
[    4.662096] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 7865254
[    4.662110] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 14422469
[    4.662124] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 14422297
[    4.662137] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 7865176
[    4.662152] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 7865080
[    4.662165] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 7865038
[    4.662177] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 7865035
[    4.662189] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 7865034
[    4.662201] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 7865018
[    4.662213] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 7864848
[    4.662225] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 7864663
[    4.662238] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 2360179
[    4.662251] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 14422448
[    4.662263] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 14422477
[    4.662275] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 14422465
[    4.662287] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 14422490
[    4.662299] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 2360202
[    4.662319] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 2360201
[    4.662331] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 2360194
[    4.662343] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 2360166
[    4.662355] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 2360163
[    4.662366] EXT4-fs (sda1): 28 orphan inodes deleted
[    4.662368] EXT4-fs (sda1): recovery complete
[    4.860672] EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: (null)
[   16.997668] <30>udev[328]: starting version 167
[   17.029747] Adding 3984380k swap on /dev/sda5.  Priority:-1 extents:1 across:3984380k 
[   17.039517] lp: driver loaded but no devices found
[   17.140191] Disabling lock debugging due to kernel taint
[   17.172744] ndiswrapper version 1.56 loaded (smp=yes, preempt=no)
[   17.225568] Bluetooth: Core ver 2.15
[   17.225652] NET: Registered protocol family 31
[   17.225655] Bluetooth: HCI device and connection manager initialized
[   17.225659] Bluetooth: HCI socket layer initialized
[   17.233306] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,user_xattr
[   17.263013] [drm] Initialized drm 1.1.0 20060810
[   17.277518] type=1400 audit(1316485185.949:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=590 comm="apparmor_parser"
[   17.278646] type=1400 audit(1316485185.949:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=590 comm="apparmor_parser"
[   17.279362] type=1400 audit(1316485185.949:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=590 comm="apparmor_parser"
[   17.280057] Bluetooth: Generic Bluetooth USB driver ver 0.6
[   17.285613] intel ips 0000:00:1f.6: CPU TDP doesn't match expected value (found 11, expected 14)
[   17.285658] intel ips 0000:00:1f.6: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[   17.285952] intel ips 0000:00:1f.6: failed to get i915 symbols, graphics turbo disabled
[   17.292651] intel ips 0000:00:1f.6: IPS driver initialized, MCP temp limit 90
[   17.306904] Linux video capture interface: v2.00
[   17.313044] usbcore: registered new interface driver btusb
[   17.423825] type=1400 audit(1316485186.093:5): apparmor="STATUS" operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" pid=735 comm="apparmor_parser"
[   17.426220] type=1400 audit(1316485186.097:6): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=732 comm="apparmor_parser"
[   17.427974] type=1400 audit(1316485186.097:7): apparmor="STATUS" operation="profile_load" name="/usr/sbin/cupsd" pid=735 comm="apparmor_parser"
[   17.433888] type=1400 audit(1316485186.105:8): apparmor="STATUS" operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" pid=731 comm="apparmor_parser"
[   17.443899] type=1400 audit(1316485186.113:9): apparmor="STATUS" operation="profile_load" name="/usr/sbin/tcpdump" pid=739 comm="apparmor_parser"
[   17.448225] type=1400 audit(1316485186.117:10): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=732 comm="apparmor_parser"
[   17.459753] type=1400 audit(1316485186.129:11): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=732 comm="apparmor_parser"
[   17.484735] i915 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   17.484745] i915 0000:00:02.0: setting latency timer to 64
[   17.494298] ndiswrapper: driver rt2860 (Ralink Technology, Corp.,06/01/2010, 3.01.05.0001) loaded
[   17.494775] ndiswrapper 0000:02:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   17.511075] uvcvideo: Found UVC 1.00 device USB2.0 UVC 1.3M WebCam (13d3:5135)
[   17.524915] input: USB2.0 UVC 1.3M WebCam as /devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.6/1-1.6:1.0/input/input8
[   17.525144] usbcore: registered new interface driver uvcvideo
[   17.525149] USB Video Class driver (v1.0.0)
[   17.568698] i915 0000:00:02.0: irq 42 for MSI/MSI-X
[   17.568708] [drm] Supports vblank timestamp caching Rev 1 (10.10.2010).
[   17.568711] [drm] Driver supports precise vblank timestamp query.
[   17.612879] Bluetooth: L2CAP ver 2.15
[   17.612883] Bluetooth: L2CAP socket layer initialized
[   17.629044] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   17.629049] Bluetooth: BNEP filters: protocol multicast
[   17.677065] Bluetooth: SCO (Voice Link) ver 0.6
[   17.677069] Bluetooth: SCO socket layer initialized
[   17.731259] vgaarb: device changed decodes: PCI:0000:00:02.0,olddecodes=io+mem,decodes=io+mem:owns=io+mem
[   17.772565] r8169 0000:04:00.0: eth0: link down
[   17.772875] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   17.795021] fbcon: inteldrmfb (fb0) is primary device
[   17.795206] Console: switching to colour frame buffer device 170x48
[   17.795247] fb0: inteldrmfb frame buffer device
[   17.795249] drm: registered panic notifier
[   17.813975] ACPI Warning: _BQC returned an invalid level (20110112/video-473)
[   17.814237] acpi device:04: registered as cooling_device4
[   17.814888] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/LNXVIDEO:00/input/input9
[   17.815087] ACPI: Video Device [GFX0] (multi-head: yes  rom: no  post: no)
[   17.815818] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
[   17.815963] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[   17.816056] HDA Intel 0000:00:1b.0: irq 43 for MSI/MSI-X
[   17.816100] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   17.893031] Bluetooth: RFCOMM TTY layer initialized
[   17.893040] Bluetooth: RFCOMM socket layer initialized
[   17.893043] Bluetooth: RFCOMM ver 1.11
[   17.897786] hda_codec: ALC269: BIOS auto-probing.
[   17.917063] input: HDA Intel Headphone as /devices/pci0000:00/0000:00:1b.0/sound/card0/input10
[   18.020727] ndiswrapper 0000:02:00.0: setting latency timer to 64
[   18.108483] Synaptics Touchpad, model: 1, fw: 7.2, id: 0x1c0b1, caps: 0xd04733/0xa40000/0xa0000
[   18.154310] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio2/input/input11
[   18.623641] ndiswrapper: using IRQ 16
[   18.857391] wlan0: ethernet device e0:b9:a5:11:5f:b9 using serialized NDIS driver: rt2860, version: 0x0, NDIS version: 0x500, vendor: 'IEEE 802.11 Wireless Card.', 1814:3090.5.conf
[   18.857450] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2PSK; AES/CCMP with WPA, WPA2, WPA2PSK
[   18.867475] usbcore: registered new interface driver ndiswrapper
[   18.894490] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   18.937309] ppdev: user-space parallel port driver
[   20.448878] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,user_xattr,commit=0
[   21.820287] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,user_xattr,commit=0
[   22.497622] intel ips 0000:00:1f.6: i915 driver attached, reenabling gpu turbo
[  100.020386] Bluetooth: HIDP (Human Interface Emulation) ver 1.2
[  174.476496] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  185.112476] wlan0: no IPv6 routers present
[  189.449419] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  189.646904] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  189.995430] r8169 0000:04:00.0: eth0: link down
[  189.996042] ADDRCONF(NETDEV_UP): eth0: link is not ready
[  199.664452] wlan0: no IPv6 routers present
```

---

