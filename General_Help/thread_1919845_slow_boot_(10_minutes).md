---
title: "slow boot (10 minutes)"
date: 2012-02-03
forum: General Help
---

### Post by PRSnow on 2012-02-03
**[COLOR=red]**UPDATE**[/COLOR]**
[COLOR=red]*The slow boot time was solved after disabling ACHI support for the SATA controller in the BIOS. Is this a bug? I thought Ubuntu fully supported ACHI. There are benefits of keeping this enabled, so I'd like to keep it turned on. Any suggestions on how to correct this?*[/COLOR]
  
 
 
Running a fresh install of 11.10 on a netbook with an Intel Atom CPU N450 @ 1.66GHz and 2gigs RAM. Takes about 10 minutes to boot. Booting off a USB flash drive was much faster. I noticed a gap from about 30 seconds to 600 , but I don't know what those lines are referring to. 
 
Here is the info from dmesg:
 
```

[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 3.0.0-15-generic (buildd@zirconium) (gcc version 4.6.1 (Ubuntu/Linaro 4.6.1-9ubuntu3) ) #26-Ubuntu SMP Fri Jan 20 15:59:53 UTC 2012 (Ubuntu 3.0.0-15.26-generic 3.0.13)
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
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009dc00 (usable)
[    0.000000]  BIOS-e820: 000000000009dc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000dc000 - 00000000000e0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e4000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000007f5d0000 (usable)
[    0.000000]  BIOS-e820: 000000007f5d0000 - 000000007f5e0000 (ACPI data)
[    0.000000]  BIOS-e820: 000000007f5e0000 - 000000007f5e3000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000007f5e3000 - 0000000080000000 (reserved)
[    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000ff000000 - 0000000100000000 (reserved)
[    0.000000] Notice: NX (Execute Disable) protection cannot be enabled in hardware: non-PAE kernel!
[    0.000000] NX (Execute Disable) protection: approximated by x86 segment limits
[    0.000000] DMI present.
[    0.000000] DMI: TOSHIBA TOSHIBA NB305/NPVAA, BIOS V1.70 06/03/2010
[    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
[    0.000000] e820 remove range: 00000000000a0000 - 0000000000100000 (usable)
[    0.000000] last_pfn = 0x7f5d0 max_arch_pfn = 0x100000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-CFFFF write-protect
[    0.000000]   D0000-DFFFF uncachable
[    0.000000]   E0000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000 mask 080000000 write-back
[    0.000000]   1 base 07F600000 mask 0FFE00000 uncachable
[    0.000000]   2 base 07F800000 mask 0FF800000 uncachable
[    0.000000]   3 disabled
[    0.000000]   4 disabled
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] original variable MTRRs
[    0.000000] reg 0, base: 0GB, range: 2GB, type WB
[    0.000000] reg 1, base: 2038MB, range: 2MB, type UC
[    0.000000] reg 2, base: 2040MB, range: 8MB, type UC
[    0.000000] total RAM covered: 2038M
[    0.000000] Found optimal setting for mtrr clean up
[    0.000000]  gran_size: 64K     chunk_size: 16M     num_reg: 3      lose cover RAM: 0G
[    0.000000] New variable MTRRs
[    0.000000] reg 0, base: 0GB, range: 2GB, type WB
[    0.000000] reg 1, base: 2038MB, range: 2MB, type UC
[    0.000000] reg 2, base: 2040MB, range: 8MB, type UC
[    0.000000] found SMP MP-table at [c00f7d60] f7d60
[    0.000000] initial memory mapped : 0 - 01c00000
[    0.000000] Base memory trampoline at [c0099000] 99000 size 16384
[    0.000000] init_memory_mapping: 0000000000000000-00000000377fe000
[    0.000000]  0000000000 - 0000400000 page 4k
[    0.000000]  0000400000 - 0037400000 page 2M
[    0.000000]  0037400000 - 00377fe000 page 4k
[    0.000000] kernel direct mapping tables up to 377fe000 @ 1bfb000-1c00000
[    0.000000] RAMDISK: 365ee000 - 372ef000
[    0.000000] ACPI: RSDP 000f7cc0 00024 (v02 TOSCPL)
[    0.000000] ACPI: XSDT 7f5d4f1d 00074 (v01 TOSCPL TOSCPL00 06040000  LTP 00000000)
[    0.000000] ACPI: FACP 7f5dfc60 000F4 (v03 TOSCPL TOSCPL00 06040000 PTL  00000002)
[    0.000000] ACPI: DSDT 7f5d60b3 09B39 (v01 TOSCPL TOSCPL00 06040000 MSFT 03000000)
[    0.000000] ACPI: FACS 7f5e2fc0 00040
[    0.000000] ACPI: TCPA 7f5dfd54 00032 (v01 Phoeni  x       06040000  TL  00000000)
[    0.000000] ACPI: HPET 7f5dfd86 00038 (v01 DELL   M09      06040000 LOHR 0000005A)
[    0.000000] ACPI: MCFG 7f5dfdbe 0003C (v01 INTEL  CRESTLNE 06040000 LOHR 0000005A)
[    0.000000] ACPI: SLIC 7f5dfdfa 00176 (v01 TOSCPL TOSCPL00 06040000 LOHR 00000000)
[    0.000000] ACPI: APIC 7f5dff70 00068 (v01 TOSCPL TOSCPL00 06040000  LTP 00000000)
[    0.000000] ACPI: BOOT 7f5dffd8 00028 (v01 TOSCPL TOSCPL00 06040000  LTP 00000001)
[    0.000000] ACPI: SSDT 7f5d5513 0025F (v01  PmRef  Cpu0Tst 00003000 INTL 20050624)
[    0.000000] ACPI: SSDT 7f5d546d 000A6 (v01  PmRef  Cpu1Tst 00003000 INTL 20050624)
[    0.000000] ACPI: SSDT 7f5d4f91 004DC (v02  PmRef    CpuPm 00003000 INTL 20050624)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] 1149MB HIGHMEM available.
[    0.000000] 887MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 377fe000
[    0.000000]   low ram: 0 - 377fe000
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000010 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x000377fe
[    0.000000]   HighMem  0x000377fe -> 0x0007f5d0
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[2] active PFN ranges
[    0.000000]     0: 0x00000010 -> 0x0000009d
[    0.000000]     0: 0x00000100 -> 0x0007f5d0
[    0.000000] On node 0 totalpages: 521565
[    0.000000] free_area_init_node: node 0, pgdat c17b5400, node_mem_map f55fe200
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3949 pages, LIFO batch:0
[    0.000000]   Normal zone: 1744 pages used for memmap
[    0.000000]   Normal zone: 221486 pages, LIFO batch:31
[    0.000000]   HighMem zone: 2300 pages used for memmap
[    0.000000]   HighMem zone: 292054 pages, LIFO batch:31
[    0.000000] Using APIC driver default
[    0.000000] ACPI: PM-Timer IO Port: 0x1008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 high edge)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000
[    0.000000] SMP: Allowing 2 CPUs, 0 hotplug CPUs
[    0.000000] nr_irqs_gsi: 40
[    0.000000] PM: Registered nosave memory: 000000000009d000 - 000000000009e000
[    0.000000] PM: Registered nosave memory: 000000000009e000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000dc000
[    0.000000] PM: Registered nosave memory: 00000000000dc000 - 00000000000e0000
[    0.000000] PM: Registered nosave memory: 00000000000e0000 - 00000000000e4000
[    0.000000] PM: Registered nosave memory: 00000000000e4000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 80000000 (gap: 80000000:60000000)
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] setup_percpu: NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:2 nr_node_ids:1
[    0.000000] PERCPU: Embedded 12 pages/cpu @f5000000 s26240 r0 d22912 u2097152
[    0.000000] pcpu-alloc: s26240 r0 d22912 u2097152 alloc=1*4194304
[    0.000000] pcpu-alloc: [0] 0 1 
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 517489
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.0.0-15-generic root=UUID=d97334a4-4ab1-4dfc-af71-081ac557739f ro
[    0.000000] PID hash table entries: 4096 (order: 2, 16384 bytes)
[    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.000000] Initializing CPU#0
[    0.000000] allocated 8346624 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] Initializing HighMem for node 0 (000377fe:0007f5d0)
[    0.000000] Memory: 2037972k/2086720k available (5336k kernel code, 48288k reserved, 2599k data, 696k init, 1177416k highmem)
[    0.000000] virtual kernel memory layout:
[    0.000000]     fixmap  : 0xfff16000 - 0xfffff000   ( 932 kB)
[    0.000000]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[    0.000000]     vmalloc : 0xf7ffe000 - 0xff7fe000   ( 120 MB)
[    0.000000]     lowmem  : 0xc0000000 - 0xf77fe000   ( 887 MB)
[    0.000000]       .init : 0xc17c1000 - 0xc186f000   ( 696 kB)
[    0.000000]       .data : 0xc1536144 - 0xc17c0080   (2599 kB)
[    0.000000]       .text : 0xc1000000 - 0xc1536144   (5336 kB)
[    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.000000] SLUB: Genslabs=15, HWalign=64, Order=0-3, MinObjects=0, CPUs=2, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000]     RCU dyntick-idle grace-period acceleration is enabled.
[    0.000000] NR_IRQS:2304 nr_irqs:512 16
[    0.000000] CPU 0 irqstacks, hard=f4408000 soft=f440a000
[    0.000000] Extended CMOS year: 2000
[    0.000000] Console: colour dummy device 80x25
[    0.000000] console [tty0] enabled
[    0.000000] hpet clockevent registered
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 1662.598 MHz processor.
[    0.004005] Calibrating delay loop (skipped), value calculated using timer frequency.. 3325.19 BogoMIPS (lpj=6650392)
[    0.004030] pid_max: default: 32768 minimum: 301
[    0.004084] Security Framework initialized
[    0.004124] AppArmor: AppArmor initialized
[    0.004135] Yama: becoming mindful.
[    0.004257] Mount-cache hash table entries: 512
[    0.008197] Initializing cgroup subsys cpuacct
[    0.008221] Initializing cgroup subsys memory
[    0.008244] Initializing cgroup subsys devices
[    0.008256] Initializing cgroup subsys freezer
[    0.008268] Initializing cgroup subsys net_cls
[    0.008279] Initializing cgroup subsys blkio
[    0.008300] Initializing cgroup subsys perf_event
[    0.008363] CPU: Physical Processor ID: 0
[    0.008375] CPU: Processor Core ID: 0
[    0.008386] mce: CPU supports 5 MCE banks
[    0.008407] CPU0: Thermal monitoring handled by SMI
[    0.008415] using mwait in idle threads.
[    0.011925] ACPI: Core revision 20110413
[    0.024029] ftrace: allocating 24882 entries in 49 pages
[    0.028098] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.028528] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.071513] CPU0: Intel(R) Atom(TM) CPU N450   @ 1.66GHz stepping 0a
[    0.072003] Performance Events: PEBS fmt0+, Atom events, Intel PMU driver.
[    0.072003] ... version:                3
[    0.072003] ... bit width:              40
[    0.072003] ... generic registers:      2
[    0.072003] ... value mask:             000000ffffffffff
[    0.072003] ... max period:             000000007fffffff
[    0.072003] ... fixed-purpose events:   3
[    0.072003] ... event mask:             0000000700000003
[    0.072003] CPU 1 irqstacks, hard=f44ca000 soft=f44cc000
[    0.072003] Booting Node   0, Processors  #1 Ok.
[    0.072003] smpboot cpu 1: start_ip = 99000
[    0.008000] Initializing CPU#1
[    0.008000] CPU0: Thermal monitoring enabled (TM1)
[    0.168040] Brought up 2 CPUs
[    0.168071] Total of 2 processors activated (6650.13 BogoMIPS).
[    0.168587] devtmpfs: initialized
[    0.168587] PM: Registering ACPI NVS region at 7f5e0000 (12288 bytes)
[    0.174593] print_constraints: dummy: 
[    0.174640] Time: 13:34:44  Date: 02/03/12
[    0.174739] NET: Registered protocol family 16
[    0.174769] Trying to unpack rootfs image as initramfs...
[    0.175081] EISA bus registered
[    0.175115] ACPI: bus type pci registered
[    0.175300] PCI: MMCONFIG for domain 0000 [bus 00-ff] at [mem 0xe0000000-0xefffffff] (base 0xe0000000)
[    0.175327] PCI: MMCONFIG at [mem 0xe0000000-0xefffffff] reserved in E820
[    0.175343] PCI: Using MMCONFIG for extended config space
[    0.175358] PCI: Using configuration type 1 for base access
[    0.178548] bio: create slab <bio-0> at 0
[    0.182804] ACPI: EC: Look up EC in DSDT
[    0.195713] ACPI: SSDT 7f5d5ddc 00203 (v02  PmRef  Cpu0Ist 00003000 INTL 20050624)
[    0.196766] ACPI: Dynamic OEM Table Load:
[    0.196788] ACPI: SSDT   (null) 00203 (v02  PmRef  Cpu0Ist 00003000 INTL 20050624)
[    0.197295] ACPI: SSDT 7f5d5772 005E5 (v02  PmRef  Cpu0Cst 00003001 INTL 20050624)
[    0.198269] ACPI: Dynamic OEM Table Load:
[    0.198292] ACPI: SSDT   (null) 005E5 (v02  PmRef  Cpu0Cst 00003001 INTL 20050624)
[    0.199129] ACPI: SSDT 7f5d5fdf 000D4 (v02  PmRef  Cpu1Ist 00003000 INTL 20050624)
[    0.200163] ACPI: Dynamic OEM Table Load:
[    0.200185] ACPI: SSDT   (null) 000D4 (v02  PmRef  Cpu1Ist 00003000 INTL 20050624)
[    0.200528] ACPI: SSDT 7f5d5d57 00085 (v02  PmRef  Cpu1Cst 00003000 INTL 20050624)
[    0.201504] ACPI: Dynamic OEM Table Load:
[    0.201525] ACPI: SSDT   (null) 00085 (v02  PmRef  Cpu1Cst 00003000 INTL 20050624)
[    0.204259] ACPI: Interpreter enabled
[    0.204284] ACPI: (supports S0 S3 S4 S5)
[    0.204354] ACPI: Using IOAPIC for interrupt routing
[    0.255882] ACPI: EC: GPE = 0x19, I/O: command/status = 0x66, data = 0x62
[    0.256410] ACPI: No dock devices found.
[    0.256431] HEST: Table not found.
[    0.256450] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
[    0.258890] ACPI Error: [CAPB] Namespace lookup failure, AE_ALREADY_EXISTS (20110413/dsfield-143)
[    0.258936] ACPI Error: Method parse/execution failed [\_SB_.PCI0._OSC] (Node f44252b8), AE_ALREADY_EXISTS (20110413/psparse-536)
[    0.258983] ACPI: Marking method _OSC as Serialized because of AE_ALREADY_EXISTS error
[    0.259024] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-3f])
[    0.263636] pci_root PNP0A08:00: host bridge window [io  0x0000-0x0cf7]
[    0.263662] pci_root PNP0A08:00: host bridge window [mem 0x000a0000-0x000bffff]
[    0.263686] pci_root PNP0A08:00: host bridge window [mem 0x000d0000-0x000d3fff]
[    0.263708] pci_root PNP0A08:00: host bridge window [mem 0x000d4000-0x000d7fff]
[    0.263733] pci_root PNP0A08:00: host bridge window [mem 0x000d8000-0x000dbfff]
[    0.263757] pci_root PNP0A08:00: host bridge window [mem 0x000e0000-0x000e3fff]
[    0.263784] pci_root PNP0A08:00: host bridge window [mem 0x80000000-0xf7ffffff]
[    0.263806] pci_root PNP0A08:00: host bridge window [io  0x0d00-0xfdff]
[    0.263858] pci 0000:00:00.0: [8086:a010] type 0 class 0x000600
[    0.263938] pci 0000:00:02.0: [8086:a011] type 0 class 0x000300
[    0.263962] pci 0000:00:02.0: reg 10: [mem 0xf0200000-0xf027ffff]
[    0.263976] pci 0000:00:02.0: reg 14: [io  0x18d0-0x18d7]
[    0.263990] pci 0000:00:02.0: reg 18: [mem 0xd0000000-0xdfffffff pref]
[    0.264005] pci 0000:00:02.0: reg 1c: [mem 0xf0000000-0xf00fffff]
[    0.264078] pci 0000:00:02.1: [8086:a012] type 0 class 0x000380
[    0.264098] pci 0000:00:02.1: reg 10: [mem 0xf0280000-0xf02fffff]
[    0.264223] pci 0000:00:1b.0: [8086:27d8] type 0 class 0x000403
[    0.264255] pci 0000:00:1b.0: reg 10: [mem 0xf0500000-0xf0503fff 64bit]
[    0.264351] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    0.264363] pci 0000:00:1b.0: PME# disabled
[    0.264402] pci 0000:00:1c.0: [8086:27d0] type 1 class 0x000604
[    0.264505] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    0.264517] pci 0000:00:1c.0: PME# disabled
[    0.264565] pci 0000:00:1c.1: [8086:27d2] type 1 class 0x000604
[    0.264668] pci 0000:00:1c.1: PME# supported from D0 D3hot D3cold
[    0.264681] pci 0000:00:1c.1: PME# disabled
[    0.264729] pci 0000:00:1c.2: [8086:27d4] type 1 class 0x000604
[    0.264831] pci 0000:00:1c.2: PME# supported from D0 D3hot D3cold
[    0.264843] pci 0000:00:1c.2: PME# disabled
[    0.264889] pci 0000:00:1d.0: [8086:27c8] type 0 class 0x000c03
[    0.264958] pci 0000:00:1d.0: reg 20: [io  0x1820-0x183f]
[    0.265014] pci 0000:00:1d.1: [8086:27c9] type 0 class 0x000c03
[    0.265083] pci 0000:00:1d.1: reg 20: [io  0x1840-0x185f]
[    0.265139] pci 0000:00:1d.2: [8086:27ca] type 0 class 0x000c03
[    0.265208] pci 0000:00:1d.2: reg 20: [io  0x1860-0x187f]
[    0.265263] pci 0000:00:1d.3: [8086:27cb] type 0 class 0x000c03
[    0.265332] pci 0000:00:1d.3: reg 20: [io  0x1880-0x189f]
[    0.265401] pci 0000:00:1d.7: [8086:27cc] type 0 class 0x000c03
[    0.265436] pci 0000:00:1d.7: reg 10: [mem 0xf0504000-0xf05043ff]
[    0.265549] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
[    0.265563] pci 0000:00:1d.7: PME# disabled
[    0.265608] pci 0000:00:1e.0: [8086:2448] type 1 class 0x000604
[    0.265716] pci 0000:00:1f.0: [8086:27bc] type 0 class 0x000601
[    0.265826] pci 0000:00:1f.0: [Firmware Bug]: TigerPoint LPC.BM_STS cleared
[    0.265902] pci 0000:00:1f.2: [8086:27c1] type 0 class 0x000106
[    0.265934] pci 0000:00:1f.2: reg 10: [io  0x18e8-0x18ef]
[    0.265953] pci 0000:00:1f.2: reg 14: [io  0x18dc-0x18df]
[    0.265972] pci 0000:00:1f.2: reg 18: [io  0x18e0-0x18e7]
[    0.265990] pci 0000:00:1f.2: reg 1c: [io  0x18d8-0x18db]
[    0.266008] pci 0000:00:1f.2: reg 20: [io  0x18c0-0x18cf]
[    0.266027] pci 0000:00:1f.2: reg 24: [mem 0xf0504400-0xf05047ff]
[    0.266079] pci 0000:00:1f.2: PME# supported from D3hot
[    0.266089] pci 0000:00:1f.2: PME# disabled
[    0.266119] pci 0000:00:1f.3: [8086:27da] type 0 class 0x000c05
[    0.266190] pci 0000:00:1f.3: reg 20: [io  0x18a0-0x18bf]
[    0.266308] pci 0000:00:1c.0: PCI bridge to [bus 05-05]
[    0.266330] pci 0000:00:1c.0:   bridge window [io  0x0000-0x0000] (disabled)
[    0.266342] pci 0000:00:1c.0:   bridge window [mem 0xfff00000-0x000fffff] (disabled)
[    0.266357] pci 0000:00:1c.0:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    0.266475] pci 0000:07:00.0: [168c:002b] type 0 class 0x000280
[    0.266534] pci 0000:07:00.0: reg 10: [mem 0xf0100000-0xf010ffff 64bit]
[    0.266708] pci 0000:07:00.0: supports D1
[    0.266716] pci 0000:07:00.0: PME# supported from D0 D1 D3hot
[    0.266730] pci 0000:07:00.0: PME# disabled
[    0.272075] pci 0000:00:1c.1: PCI bridge to [bus 07-07]
[    0.272102] pci 0000:00:1c.1:   bridge window [io  0xf000-0x0000] (disabled)
[    0.272116] pci 0000:00:1c.1:   bridge window [mem 0xf0100000-0xf01fffff]
[    0.272131] pci 0000:00:1c.1:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    0.272286] pci 0000:09:00.0: [10ec:8136] type 0 class 0x000200
[    0.272361] pci 0000:09:00.0: reg 10: [io  0x2000-0x20ff]
[    0.272482] pci 0000:09:00.0: reg 18: [mem 0xf0520000-0xf0520fff 64bit pref]
[    0.272559] pci 0000:09:00.0: reg 20: [mem 0xf0510000-0xf051ffff 64bit pref]
[    0.272613] pci 0000:09:00.0: reg 30: [mem 0x00000000-0x0001ffff pref]
[    0.272792] pci 0000:09:00.0: supports D1 D2
[    0.272800] pci 0000:09:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.272821] pci 0000:09:00.0: PME# disabled
[    0.273004] pci 0000:00:1c.2: PCI bridge to [bus 09-09]
[    0.273026] pci 0000:00:1c.2:   bridge window [io  0x2000-0x2fff]
[    0.273038] pci 0000:00:1c.2:   bridge window [mem 0xfff00000-0x000fffff] (disabled)
[    0.273054] pci 0000:00:1c.2:   bridge window [mem 0xf0500000-0xf05fffff 64bit pref]
[    0.273155] pci 0000:00:1e.0: PCI bridge to [bus 11-11] (subtractive decode)
[    0.273177] pci 0000:00:1e.0:   bridge window [io  0xf000-0x0000] (disabled)
[    0.273189] pci 0000:00:1e.0:   bridge window [mem 0xfff00000-0x000fffff] (disabled)
[    0.273205] pci 0000:00:1e.0:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    0.273215] pci 0000:00:1e.0:   bridge window [io  0x0000-0x0cf7] (subtractive decode)
[    0.273224] pci 0000:00:1e.0:   bridge window [mem 0x000a0000-0x000bffff] (subtractive decode)
[    0.273234] pci 0000:00:1e.0:   bridge window [mem 0x000d0000-0x000d3fff] (subtractive decode)
[    0.273244] pci 0000:00:1e.0:   bridge window [mem 0x000d4000-0x000d7fff] (subtractive decode)
[    0.273254] pci 0000:00:1e.0:   bridge window [mem 0x000d8000-0x000dbfff] (subtractive decode)
[    0.273264] pci 0000:00:1e.0:   bridge window [mem 0x000e0000-0x000e3fff] (subtractive decode)
[    0.273273] pci 0000:00:1e.0:   bridge window [mem 0x80000000-0xf7ffffff] (subtractive decode)
[    0.273283] pci 0000:00:1e.0:   bridge window [io  0x0d00-0xfdff] (subtractive decode)
[    0.273320] pci_bus 0000:00: on NUMA node 0
[    0.273337] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.273596] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.EXP1._PRT]
[    0.273735] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.EXP2._PRT]
[    0.273867] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.EXP3._PRT]
[    0.274008] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCIB._PRT]
[    0.274436] ACPI Error: [CAPB] Namespace lookup failure, AE_ALREADY_EXISTS (20110413/dsfield-143)
[    0.274478] ACPI Error: Method parse/execution failed [\_SB_.PCI0._OSC] (Node f44252b8), AE_ALREADY_EXISTS (20110413/psparse-536)
[    0.274541]  pci0000:00: Requesting ACPI _OSC control (0x1d)
[    0.274761] ACPI Error: [CAPB] Namespace lookup failure, AE_ALREADY_EXISTS (20110413/dsfield-143)
[    0.274799] ACPI Error: Method parse/execution failed [\_SB_.PCI0._OSC] (Node f44252b8), AE_ALREADY_EXISTS (20110413/psparse-536)
[    0.274855]  pci0000:00: ACPI _OSC request failed (AE_ALREADY_EXISTS), returned control mask: 0x1d
[    0.274877] ACPI _OSC control for PCIe not granted, disabling ASPM
[    0.287943] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 *7 10 11 12 14 15)
[    0.288183] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 10 *11 12 14 15)
[    0.288373] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 *5 6 7 10 11 12 14 15)
[    0.288560] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 *10 11 12 14 15)
[    0.288765] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[    0.288984] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[    0.289193] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 *10 11 12 14 15)
[    0.289392] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 10 *11 12 14 15)
[    0.289720] vgaarb: device added: PCI:0000:00:02.0,decodes=io+mem,owns=io+mem,locks=none
[    0.289770] vgaarb: loaded
[    0.289785] vgaarb: bridge control possible 0000:00:02.0
[    0.290491] SCSI subsystem initialized
[    0.290670] libata version 3.00 loaded.
[    0.290830] usbcore: registered new interface driver usbfs
[    0.290881] usbcore: registered new interface driver hub
[    0.290991] usbcore: registered new device driver usb
[    0.291283] PCI: Using ACPI for IRQ routing
[    0.305600] PCI: pci_cache_line_size set to 64 bytes
[    0.305645] pci 0000:00:1b.0: address space collision: [mem 0xf0500000-0xf0503fff 64bit] conflicts with PCI Bus 0000:09 [mem 0xf0500000-0xf05fffff 64bit pref]
[    0.305717] pci 0000:00:1d.7: address space collision: [mem 0xf0504000-0xf05043ff] conflicts with PCI Bus 0000:09 [mem 0xf0500000-0xf05fffff 64bit pref]
[    0.305765] pci 0000:00:1f.2: address space collision: [mem 0xf0504400-0xf05047ff] conflicts with PCI Bus 0000:09 [mem 0xf0500000-0xf05fffff 64bit pref]
[    0.305870] reserve RAM buffer: 000000000009dc00 - 000000000009ffff 
[    0.305878] reserve RAM buffer: 000000007f5d0000 - 000000007fffffff 
[    0.306211] NetLabel: Initializing
[    0.306226] NetLabel:  domain hash size = 128
[    0.306238] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.306277] NetLabel:  unlabeled traffic allowed by default
[    0.306436] HPET: 3 timers in total, 0 timers will be used for per-cpu timer
[    0.306462] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[    0.306487] hpet0: 3 comparators, 64-bit 14.318180 MHz counter
[    0.316193] Switching to clocksource hpet
[    0.319630] Switched to NOHz mode on CPU #0
[    0.319775] Switched to NOHz mode on CPU #1
[    0.336874] AppArmor: AppArmor Filesystem Enabled
[    0.336961] pnp: PnP ACPI init
[    0.337015] ACPI: bus type pnp registered
[    0.339183] pnp 00:00: [bus 00-3f]
[    0.339194] pnp 00:00: [io  0x0cf8-0x0cff]
[    0.339204] pnp 00:00: [io  0x0000-0x0cf7 window]
[    0.339213] pnp 00:00: [mem 0x000a0000-0x000bffff window]
[    0.339223] pnp 00:00: [mem 0x000c0000-0x000c3fff window]
[    0.339232] pnp 00:00: [mem 0x000c4000-0x000c7fff window]
[    0.339240] pnp 00:00: [mem 0x000c8000-0x000cbfff window]
[    0.339248] pnp 00:00: [mem 0x000cc000-0x000cffff window]
[    0.339257] pnp 00:00: [mem 0x000d0000-0x000d3fff window]
[    0.339265] pnp 00:00: [mem 0x000d4000-0x000d7fff window]
[    0.339274] pnp 00:00: [mem 0x000d8000-0x000dbfff window]
[    0.339282] pnp 00:00: [mem 0x000dc000-0x000dffff window]
[    0.339291] pnp 00:00: [mem 0x000e0000-0x000e3fff window]
[    0.339299] pnp 00:00: [mem 0x000e4000-0x000e7fff window]
[    0.339307] pnp 00:00: [mem 0x000e8000-0x000ebfff window]
[    0.339316] pnp 00:00: [mem 0x000ec000-0x000effff window]
[    0.339324] pnp 00:00: [mem 0x000f0000-0x000fffff window]
[    0.339333] pnp 00:00: [mem 0x80000000-0xf7ffffff window]
[    0.339342] pnp 00:00: [io  0x0d00-0xfdff window]
[    0.339349] pnp 00:00: [mem 0x00000000 window]
[    0.339358] pnp 00:00: [mem 0xfed40000-0xfed44fff window]
[    0.339550] pnp 00:00: Plug and Play ACPI device, IDs PNP0a08 PNP0a03 (active)
[    0.339929] pnp 00:01: [io  0x0010-0x001f]
[    0.339938] pnp 00:01: [io  0x0024-0x0025]
[    0.339946] pnp 00:01: [io  0x0028-0x0029]
[    0.339954] pnp 00:01: [io  0x002c-0x002d]
[    0.339961] pnp 00:01: [io  0x0030-0x0031]
[    0.339969] pnp 00:01: [io  0x0034-0x0035]
[    0.339977] pnp 00:01: [io  0x0038-0x0039]
[    0.339984] pnp 00:01: [io  0x003c-0x003d]
[    0.339991] pnp 00:01: [io  0x0068]
[    0.340040] pnp 00:01: [io  0x006c]
[    0.340056] pnp 00:01: [io  0x0072-0x0077]
[    0.340064] pnp 00:01: [io  0x0080]
[    0.340072] pnp 00:01: [io  0x0090-0x009f]
[    0.340079] pnp 00:01: [io  0x00a4-0x00a5]
[    0.340086] pnp 00:01: [io  0x00a8-0x00a9]
[    0.340093] pnp 00:01: [io  0x00ac-0x00ad]
[    0.340100] pnp 00:01: [io  0x00b0-0x00b5]
[    0.340107] pnp 00:01: [io  0x00b8-0x00b9]
[    0.340115] pnp 00:01: [io  0x00bc-0x00bd]
[    0.340123] pnp 00:01: [io  0x0800-0x080f]
[    0.340130] pnp 00:01: [io  0x1000-0x107f]
[    0.340138] pnp 00:01: [io  0x1180-0x11bf]
[    0.340146] pnp 00:01: [io  0x002e-0x002f]
[    0.340153] pnp 00:01: [io  0x04d0-0x04d1]
[    0.340161] pnp 00:01: [io  0xfe00]
[    0.340169] pnp 00:01: [io  0x164e-0x174c]
[    0.340177] pnp 00:01: [mem 0xe0000000-0xefffffff]
[    0.340186] pnp 00:01: [mem 0xfed14000-0xfed17fff]
[    0.340195] pnp 00:01: [mem 0xf8000000-0xfbffffff]
[    0.340203] pnp 00:01: [mem 0xfef00000-0xfeffffff]
[    0.340433] system 00:01: [io  0x0800-0x080f] has been reserved
[    0.340457] system 00:01: [io  0x1000-0x107f] has been reserved
[    0.340476] system 00:01: [io  0x1180-0x11bf] has been reserved
[    0.340495] system 00:01: [io  0x04d0-0x04d1] has been reserved
[    0.340513] system 00:01: [io  0xfe00] has been reserved
[    0.340531] system 00:01: [io  0x164e-0x174c] has been reserved
[    0.340551] system 00:01: [mem 0xe0000000-0xefffffff] has been reserved
[    0.340571] system 00:01: [mem 0xfed14000-0xfed17fff] has been reserved
[    0.340590] system 00:01: [mem 0xf8000000-0xfbffffff] has been reserved
[    0.340610] system 00:01: [mem 0xfef00000-0xfeffffff] has been reserved
[    0.340632] system 00:01: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.340675] pnp 00:02: [io  0x0000-0x000f]
[    0.340683] pnp 00:02: [io  0x0081-0x008f]
[    0.340691] pnp 00:02: [io  0x00c0-0x00df]
[    0.340699] pnp 00:02: [dma 4]
[    0.340786] pnp 00:02: Plug and Play ACPI device, IDs PNP0200 (active)
[    0.340821] pnp 00:03: [io  0x00f0-0x00fe]
[    0.340844] pnp 00:03: [irq 13]
[    0.340952] pnp 00:03: Plug and Play ACPI device, IDs PNP0c04 (active)
[    0.341081] pnp 00:04: [io  0x0070-0x0071]
[    0.341101] pnp 00:04: [irq 8]
[    0.341203] pnp 00:04: Plug and Play ACPI device, IDs PNP0b00 (active)
[    0.341239] pnp 00:05: [io  0x0061]
[    0.341328] pnp 00:05: Plug and Play ACPI device, IDs PNP0800 (active)
[    0.360203] pnp 00:06: [io  0x0060]
[    0.360213] pnp 00:06: [io  0x0064]
[    0.360236] pnp 00:06: [irq 1]
[    0.360386] pnp 00:06: Plug and Play ACPI device, IDs PNP0303 (active)
[    0.360432] pnp 00:07: [irq 12]
[    0.360550] pnp 00:07: Plug and Play ACPI device, IDs SYN071a SYN0700 SYN0002 PNP0f13 (active)
[    0.361171] pnp: PnP ACPI: found 8 devices
[    0.361190] ACPI: ACPI bus type pnp unregistered
[    0.361207] PnPBIOS: Disabled by ACPI PNP
[    0.401404] PCI: max bus depth: 1 pci_try_num: 2
[    0.401486] pci 0000:00:1c.2: BAR 14: assigned [mem 0x80000000-0x800fffff]
[    0.401514] pci 0000:00:1b.0: BAR 0: assigned [mem 0x80100000-0x80103fff 64bit]
[    0.401546] pci 0000:00:1b.0: BAR 0: set to [mem 0x80100000-0x80103fff 64bit] (PCI address [0x80100000-0x80103fff])
[    0.401576] pci 0000:00:1d.7: BAR 0: assigned [mem 0x80104000-0x801043ff]
[    0.401599] pci 0000:00:1d.7: BAR 0: set to [mem 0x80104000-0x801043ff] (PCI address [0x80104000-0x801043ff])
[    0.401629] pci 0000:00:1f.2: BAR 5: assigned [mem 0x80104400-0x801047ff]
[    0.401652] pci 0000:00:1f.2: BAR 5: set to [mem 0x80104400-0x801047ff] (PCI address [0x80104400-0x801047ff])
[    0.401684] pci 0000:00:1c.1: BAR 15: assigned [mem 0x80200000-0x803fffff 64bit pref]
[    0.401712] pci 0000:00:1c.1: BAR 13: assigned [io  0x3000-0x3fff]
[    0.401735] pci 0000:00:1c.0: BAR 14: assigned [mem 0x80400000-0x805fffff]
[    0.401759] pci 0000:00:1c.0: BAR 15: assigned [mem 0x80600000-0x807fffff 64bit pref]
[    0.401787] pci 0000:00:1c.0: BAR 13: assigned [io  0x4000-0x4fff]
[    0.401806] pci 0000:00:1c.0: PCI bridge to [bus 05-05]
[    0.401823] pci 0000:00:1c.0:   bridge window [io  0x4000-0x4fff]
[    0.401845] pci 0000:00:1c.0:   bridge window [mem 0x80400000-0x805fffff]
[    0.401867] pci 0000:00:1c.0:   bridge window [mem 0x80600000-0x807fffff 64bit pref]
[    0.401896] pci 0000:00:1c.1: PCI bridge to [bus 07-07]
[    0.401913] pci 0000:00:1c.1:   bridge window [io  0x3000-0x3fff]
[    0.401937] pci 0000:00:1c.1:   bridge window [mem 0xf0100000-0xf01fffff]
[    0.401960] pci 0000:00:1c.1:   bridge window [mem 0x80200000-0x803fffff 64bit pref]
[    0.401996] pci 0000:09:00.0: BAR 6: assigned [mem 0xf0540000-0xf055ffff pref]
[    0.402020] pci 0000:00:1c.2: PCI bridge to [bus 09-09]
[    0.402038] pci 0000:00:1c.2:   bridge window [io  0x2000-0x2fff]
[    0.402059] pci 0000:00:1c.2:   bridge window [mem 0x80000000-0x800fffff]
[    0.402081] pci 0000:00:1c.2:   bridge window [mem 0xf0500000-0xf05fffff 64bit pref]
[    0.402109] pci 0000:00:1e.0: PCI bridge to [bus 11-11]
[    0.402124] pci 0000:00:1e.0:   bridge window [io  disabled]
[    0.402144] pci 0000:00:1e.0:   bridge window [mem disabled]
[    0.402162] pci 0000:00:1e.0:   bridge window [mem pref disabled]
[    0.402195] pci 0000:00:1c.0: enabling device (0000 -> 0003)
[    0.402241] pci 0000:00:1c.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.402266] pci 0000:00:1c.0: setting latency timer to 64
[    0.402295] pci 0000:00:1c.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    0.402317] pci 0000:00:1c.1: setting latency timer to 64
[    0.402346] pci 0000:00:1c.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.402368] pci 0000:00:1c.2: setting latency timer to 64
[    0.402384] pci 0000:00:1e.0: setting latency timer to 64
[    0.402395] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
[    0.402404] pci_bus 0000:00: resource 5 [mem 0x000a0000-0x000bffff]
[    0.402413] pci_bus 0000:00: resource 6 [mem 0x000d0000-0x000d3fff]
[    0.402422] pci_bus 0000:00: resource 7 [mem 0x000d4000-0x000d7fff]
[    0.402431] pci_bus 0000:00: resource 8 [mem 0x000d8000-0x000dbfff]
[    0.402440] pci_bus 0000:00: resource 9 [mem 0x000e0000-0x000e3fff]
[    0.402449] pci_bus 0000:00: resource 10 [mem 0x80000000-0xf7ffffff]
[    0.402458] pci_bus 0000:00: resource 11 [io  0x0d00-0xfdff]
[    0.402467] pci_bus 0000:05: resource 0 [io  0x4000-0x4fff]
[    0.402475] pci_bus 0000:05: resource 1 [mem 0x80400000-0x805fffff]
[    0.402485] pci_bus 0000:05: resource 2 [mem 0x80600000-0x807fffff 64bit pref]
[    0.402494] pci_bus 0000:07: resource 0 [io  0x3000-0x3fff]
[    0.402503] pci_bus 0000:07: resource 1 [mem 0xf0100000-0xf01fffff]
[    0.402512] pci_bus 0000:07: resource 2 [mem 0x80200000-0x803fffff 64bit pref]
[    0.402521] pci_bus 0000:09: resource 0 [io  0x2000-0x2fff]
[    0.402530] pci_bus 0000:09: resource 1 [mem 0x80000000-0x800fffff]
[    0.402539] pci_bus 0000:09: resource 2 [mem 0xf0500000-0xf05fffff 64bit pref]
[    0.402549] pci_bus 0000:11: resource 4 [io  0x0000-0x0cf7]
[    0.402558] pci_bus 0000:11: resource 5 [mem 0x000a0000-0x000bffff]
[    0.402567] pci_bus 0000:11: resource 6 [mem 0x000d0000-0x000d3fff]
[    0.402576] pci_bus 0000:11: resource 7 [mem 0x000d4000-0x000d7fff]
[    0.402584] pci_bus 0000:11: resource 8 [mem 0x000d8000-0x000dbfff]
[    0.402593] pci_bus 0000:11: resource 9 [mem 0x000e0000-0x000e3fff]
[    0.402602] pci_bus 0000:11: resource 10 [mem 0x80000000-0xf7ffffff]
[    0.402611] pci_bus 0000:11: resource 11 [io  0x0d00-0xfdff]
[    0.402717] NET: Registered protocol family 2
[    0.402918] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.403570] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.404745] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.405294] TCP: Hash tables configured (established 131072 bind 65536)
[    0.405315] TCP reno registered
[    0.405337] UDP hash table entries: 512 (order: 2, 16384 bytes)
[    0.405371] UDP-Lite hash table entries: 512 (order: 2, 16384 bytes)
[    0.405686] NET: Registered protocol family 1
[    0.405747] pci 0000:00:02.0: Boot video device
[    0.405925] PCI: CLS 32 bytes, default 64
[    0.405938] Simple Boot Flag at 0x35 set to 0x1
[    0.406843] audit: initializing netlink socket (disabled)
[    0.406881] type=2000 audit(1328276084.400:1): initialized
[    0.466983] highmem bounce pool size: 64 pages
[    0.467012] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    0.482894] VFS: Disk quotas dquot_6.5.2
[    0.483124] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.485556] fuse init (API version 7.16)
[    0.485925] msgmni has been set to 1680
[    0.487114] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.487236] io scheduler noop registered
[    0.487251] io scheduler deadline registered
[    0.487322] io scheduler cfq registered (default)
[    0.487641] pcieport 0000:00:1c.0: setting latency timer to 64
[    0.487724] pcieport 0000:00:1c.0: irq 40 for MSI/MSI-X
[    0.487857] pcieport 0000:00:1c.1: setting latency timer to 64
[    0.487928] pcieport 0000:00:1c.1: irq 41 for MSI/MSI-X
[    0.488091] pcieport 0000:00:1c.2: setting latency timer to 64
[    0.488169] pcieport 0000:00:1c.2: irq 42 for MSI/MSI-X
[    0.488373] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.488461] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.488623] intel_idle: MWAIT substates: 0x20220
[    0.488639] intel_idle: v0.4 model 0x1C
[    0.488645] intel_idle: lapic_timer_reliable_states 0x2
[    0.488663] Marking TSC unstable due to TSC halts in idle states deeper than C2
[    0.489074] ACPI: Deprecated procfs I/F for AC is loaded, please retry with CONFIG_ACPI_PROCFS_POWER cleared
[    0.489534] ACPI: AC Adapter [ACAD] (off-line)
[    0.489762] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:0d/PNP0C0D:00/input/input0
[    0.489844] ACPI: Lid Switch [LID0]
[    0.489998] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0A08:00/PNP0C0C:00/input/input1
[    0.490029] ACPI: Power Button [PWRB]
[    0.490180] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input2
[    0.490207] ACPI: Power Button [PWRF]
[    0.490292] ACPI: acpi_idle yielding to intel_idle
[    0.518202] ACPI: Deprecated procfs I/F for battery is loaded, please retry with CONFIG_ACPI_PROCFS_POWER cleared
[    0.518296] ERST: Table is not found!
[    0.518557] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    0.519280] isapnp: Scanning for PnP cards...
[    0.873673] isapnp: No Plug & Play device found
[    0.926559] Freeing initrd memory: 13316k freed
[    1.180906] Linux agpgart interface v0.103
[    1.181078] agpgart-intel 0000:00:00.0: Intel GMA3150 Chipset
[    1.181283] agpgart-intel 0000:00:00.0: detected gtt size: 524288K total, 262144K mappable
[    1.181540] agpgart-intel 0000:00:00.0: detected 8192K stolen memory
[    1.181760] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0xd0000000
[    1.184691] brd: module loaded
[    1.186088] loop: module loaded
[    1.187135] Fixed MDIO Bus: probed
[    1.187200] PPP generic driver version 2.4.2
[    1.187314] tun: Universal TUN/TAP device driver, 1.6
[    1.187325] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    1.187539] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    1.187615] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    1.187657] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    1.187665] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    1.187769] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 1
[    1.187815] ehci_hcd 0000:00:1d.7: using broken periodic workaround
[    1.187839] ehci_hcd 0000:00:1d.7: debug port 1
[    1.191745] ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported
[    1.191783] ehci_hcd 0000:00:1d.7: irq 23, io mem 0x80104000
[    1.196573] ACPI: Battery Slot [BAT1] (battery present)
[    1.204034] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    1.204351] hub 1-0:1.0: USB hub found
[    1.204369] hub 1-0:1.0: 8 ports detected
[    1.204530] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    1.204568] uhci_hcd: USB Universal Host Controller Interface driver
[    1.204647] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    1.204668] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    1.204676] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    1.204781] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    1.204834] uhci_hcd 0000:00:1d.0: irq 23, io base 0x00001820
[    1.205117] hub 2-0:1.0: USB hub found
[    1.205134] hub 2-0:1.0: 2 ports detected
[    1.205286] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    1.205307] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    1.205314] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    1.205407] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 3
[    1.205476] uhci_hcd 0000:00:1d.1: irq 19, io base 0x00001840
[    1.205767] hub 3-0:1.0: USB hub found
[    1.205784] hub 3-0:1.0: 2 ports detected
[    1.205919] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    1.205939] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    1.205946] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    1.206042] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 4
[    1.206106] uhci_hcd 0000:00:1d.2: irq 18, io base 0x00001860
[    1.206391] hub 4-0:1.0: USB hub found
[    1.206408] hub 4-0:1.0: 2 ports detected
[    1.206535] uhci_hcd 0000:00:1d.3: PCI INT D -> GSI 16 (level, low) -> IRQ 16
[    1.206561] uhci_hcd 0000:00:1d.3: setting latency timer to 64
[    1.206568] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[    1.206668] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 5
[    1.206730] uhci_hcd 0000:00:1d.3: irq 16, io base 0x00001880
[    1.207006] hub 5-0:1.0: USB hub found
[    1.207023] hub 5-0:1.0: 2 ports detected
[    1.207251] i8042: PNP: PS/2 Controller [PNP0303:KBC0,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    1.241974] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.242001] serio: i8042 AUX port at 0x60,0x64 irq 12
[    1.242289] mousedev: PS/2 mouse device common for all mice
[    1.244719] rtc_cmos 00:04: RTC can wake from S4
[    1.244896] rtc_cmos 00:04: rtc core: registered rtc_cmos as rtc0
[    1.244942] rtc0: alarms up to one month, y3k, 114 bytes nvram, hpet irqs
[    1.245185] device-mapper: uevent: version 1.0.3
[    1.245396] device-mapper: ioctl: 4.20.0-ioctl (2011-02-02) initialised: [EMAIL="dm-devel@redhat.com"]dm-devel@redhat.com[/EMAIL]
[    1.245480] EISA: Probing bus 0 at eisa.0
[    1.245491] EISA: Cannot allocate resource for mainboard
[    1.245502] Cannot allocate resource for EISA slot 1
[    1.245512] Cannot allocate resource for EISA slot 2
[    1.245522] Cannot allocate resource for EISA slot 3
[    1.245531] Cannot allocate resource for EISA slot 4
[    1.245541] Cannot allocate resource for EISA slot 5
[    1.245551] Cannot allocate resource for EISA slot 6
[    1.245561] Cannot allocate resource for EISA slot 7
[    1.245570] Cannot allocate resource for EISA slot 8
[    1.245580] EISA: Detected 0 cards.
[    1.245601] cpufreq-nforce2: No nForce2 chipset.
[    1.245737] cpuidle: using governor ladder
[    1.245949] cpuidle: using governor menu
[    1.245960] EFI Variables Facility v0.08 2004-May-17
[    1.246595] TCP cubic registered
[    1.246929] NET: Registered protocol family 10
[    1.248266] NET: Registered protocol family 17
[    1.248320] Registering the dns_resolver key type
[    1.248368] Using IPI No-Shortcut mode
[    1.248602] PM: Hibernation image not present or could not be loaded.
[    1.248636] registered taskstats version 1
[    1.268815]   Magic number: 0:606:583
[    1.268958] rtc_cmos 00:04: setting system clock to 2012-02-03 13:34:46 UTC (1328276086)
[    1.269723] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.269736] EDD information not available.
[    1.270003] Freeing unused kernel memory: 696k freed
[    1.270417] Write protecting the kernel text: 5340k
[    1.270548] Write protecting the kernel read-only data: 2192k
[    1.270746] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input3
[    1.313199] udevd[83]: starting version 173
[    1.516102] usb 1-4: new high speed USB device number 2 using ehci_hcd
[    1.544782] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    1.544844] r8169 0000:09:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    1.544927] r8169 0000:09:00.0: setting latency timer to 64
[    1.545019] r8169 0000:09:00.0: irq 43 for MSI/MSI-X
[    1.546644] r8169 0000:09:00.0: eth0: RTL8102e at 0xf8020000, 00:26:22:f0:08:a4, XID 04e00000 IRQ 43
[    1.586014] ahci 0000:00:1f.2: version 3.0
[    1.586049] ahci 0000:00:1f.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    1.586162] ahci 0000:00:1f.2: irq 44 for MSI/MSI-X
[    1.586288] ahci 0000:00:1f.2: AHCI 0001.0100 32 slots 4 ports 3 Gbps 0xf impl SATA mode
[    1.586318] ahci 0000:00:1f.2: flags: 64bit ncq pm led clo pio slum part 
[    1.586339] ahci 0000:00:1f.2: setting latency timer to 64
[    1.589015] scsi0 : ahci
[    1.589412] scsi1 : ahci
[    1.593179] scsi2 : ahci
[    1.594089] scsi3 : ahci
[    1.594562] ata1: SATA max UDMA/133 abar m1024@0x80104400 port 0x80104500 irq 44
[    1.594591] ata2: SATA max UDMA/133 abar m1024@0x80104400 port 0x80104580 irq 44
[    1.594614] ata3: SATA max UDMA/133 abar m1024@0x80104400 port 0x80104600 irq 44
[    1.594637] ata4: SATA max UDMA/133 abar m1024@0x80104400 port 0x80104680 irq 44
[    1.908562] usbcore: registered new interface driver uas
[    1.912141] ata2: SATA link down (SStatus 0 SControl 300)
[    1.912204] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    1.912244] ata3: SATA link down (SStatus 0 SControl 300)
[    1.912286] ata4: SATA link down (SStatus 0 SControl 300)
[    1.924089] ata1.00: ATA-8: Hitachi HTS545025B9A300, PB2OC64G, max UDMA/133
[    1.924120] ata1.00: 488397168 sectors, multi 16: LBA48 NCQ (depth 31/32), AA
[    1.932078] ata1.00: configured for UDMA/133
[    1.932349] scsi 0:0:0:0: Direct-Access     ATA      Hitachi HTS54502 PB2O PQ: 0 ANSI: 5
[    1.932844] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    1.932981] sd 0:0:0:0: [sda] 488397168 512-byte logical blocks: (250 GB/232 GiB)
[    1.933240] sd 0:0:0:0: [sda] Write Protect is off
[    1.933262] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.933366] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.016056] usb 1-8: new high speed USB device number 3 using ehci_hcd
[    2.648715]  sda: sda1 sda2 sda3 < sda5 sda6 >
[    2.649886] sd 0:0:0:0: [sda] Attached SCSI disk
[    2.658891] Initializing USB Mass Storage driver...
[    2.659159] usbcore: registered new interface driver usb-storage
[    2.659180] USB Mass Storage support registered.
[    2.673780] usb 1-4: USB disconnect, device number 2
[    2.675946] scsi4 : usb-storage 1-4:1.0
[    2.676422] usbcore: registered new interface driver ums-realtek
[   29.914702] EXT4-fs (sda5): mounted filesystem with ordered data mode. Opts: (null)
[  610.147178] udevd[296]: starting version 173
[  610.224170] lp: driver loaded but no devices found
[  610.228546] Adding 2085884k swap on /dev/sda6.  Priority:-1 extents:1 across:2085884k 
[  610.861387] EXT4-fs (sda5): re-mounted. Opts: errors=remount-ro
[  611.090669] [drm] Initialized drm 1.1.0 20060810
[  611.209912] cfg80211: Calling CRDA to update world regulatory domain
[  611.278885] type=1400 audit(1328301896.504:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=521 comm="apparmor_parser"
[  611.301165] type=1400 audit(1328301896.528:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=521 comm="apparmor_parser"
[  611.302062] type=1400 audit(1328301896.528:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=521 comm="apparmor_parser"
[  611.312144] type=1400 audit(1328301896.540:5): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=535 comm="apparmor_parser"
[  611.321579] type=1400 audit(1328301896.548:6): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=535 comm="apparmor_parser"
[  611.322544] type=1400 audit(1328301896.548:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=535 comm="apparmor_parser"
[  611.543651] ath9k 0000:07:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[  611.543687] ath9k 0000:07:00.0: setting latency timer to 64
[  611.622053] ath: EEPROM regdomain: 0x65
[  611.622063] ath: EEPROM indicates we should expect a direct regpair map
[  611.622075] ath: Country alpha2 being used: 00
[  611.622081] ath: Regpair used: 0x65
[  611.622091] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
[  611.622102] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
[  611.622110] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
[  611.622120] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
[  611.622128] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
[  611.622138] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
[  611.622147] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
[  611.622156] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
[  611.622165] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
[  611.622175] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
[  611.622183] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
[  611.622193] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
[  611.622201] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
[  611.622210] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
[  611.622218] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
[  611.622227] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
[  611.622235] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
[  611.622245] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
[  611.622254] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
[  611.622264] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
[  611.622271] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
[  611.622281] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
[  611.622290] cfg80211: Updating information on frequency 2467 MHz for a 20 MHz width channel with regulatory rule:
[  611.622299] cfg80211: 2457000 KHz - 2482000 KHz @  KHz), (N/A mBi, 2000 mBm)
[  611.622307] cfg80211: Updating information on frequency 2472 MHz for a 20 MHz width channel with regulatory rule:
[  611.622317] cfg80211: 2457000 KHz - 2482000 KHz @  KHz), (N/A mBi, 2000 mBm)
[  611.622326] cfg80211: Disabling freq 2484 MHz as custom regd has no rule that fits a 20 MHz wide channel
[  611.651014] Linux video capture interface: v2.00
[  611.672255] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain 
[  611.674248] uvcvideo: Found UVC 1.00 device Chicony USB 2.0 Camera (04f2:b15d)
[  611.698083] input: Chicony USB 2.0 Camera as /devices/pci0000:00/0000:00:1d.7/usb1/1-8/1-8:1.0/input/input4
[  611.698577] usbcore: registered new interface driver uvcvideo
[  611.698586] USB Video Class driver (v1.1.0)
[  611.719492] ieee80211 phy0: Selected rate control algorithm 'ath9k_rate_control'
[  611.722439] i915 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[  611.722455] i915 0000:00:02.0: setting latency timer to 64
[  611.744170] Registered led device: ath9k-phy0
[  611.744200] ieee80211 phy0: Atheros AR9285 Rev:2 mem=0xf82a0000, irq=17
[  611.844192] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  611.881182] r8169 0000:09:00.0: eth0: link down
[  611.882510] ADDRCONF(NETDEV_UP): eth0: link is not ready
[  612.097796] type=1400 audit(1328301897.325:8): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=658 comm="apparmor_parser"
[  612.101692] type=1400 audit(1328301897.329:9): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=658 comm="apparmor_parser"
[  612.102632] type=1400 audit(1328301897.329:10): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=658 comm="apparmor_parser"
[  612.120351] type=1400 audit(1328301897.349:11): apparmor="STATUS" operation="profile_load" name="/usr/lib/lightdm/lightdm-guest-session-wrapper" pid=657 comm="apparmor_parser"
[  612.577908] init: failsafe main process (705) killed by TERM signal
[  612.580851] init: apport pre-start process (728) terminated with status 1
[  612.583200] init: alsa-restore main process (738) terminated with status 19
[  612.634885] init: apport post-stop process (757) terminated with status 1
[  612.776650] Synaptics Touchpad, model: 1, fw: 7.2, id: 0x1c0b1, caps: 0xd04733/0xa40000/0xa0000
[  612.883474] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input5
[  612.993303] i915 0000:00:02.0: irq 45 for MSI/MSI-X
[  612.993318] [drm] Supports vblank timestamp caching Rev 1 (10.10.2010).
[  612.993325] [drm] Driver supports precise vblank timestamp query.
[  613.031620] vgaarb: device changed decodes: PCI:0000:00:02.0,olddecodes=io+mem,decodes=io+mem:owns=io+mem
[  613.090976] fixme: max PWM is zero.
[  613.199657] Bluetooth: Core ver 2.16
[  613.200250] NET: Registered protocol family 31
[  613.200258] Bluetooth: HCI device and connection manager initialized
[  613.200267] Bluetooth: HCI socket layer initialized
[  613.200273] Bluetooth: L2CAP socket layer initialized
[  613.204631] Bluetooth: SCO socket layer initialized
[  613.233224] Bluetooth: RFCOMM TTY layer initialized
[  613.233242] Bluetooth: RFCOMM socket layer initialized
[  613.233249] Bluetooth: RFCOMM ver 1.11
[  613.238137] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[  613.238147] Bluetooth: BNEP filters: protocol multicast
[  613.254366] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain 
[  613.254380] cfg80211: World regulatory domain updated:
[  613.254386] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[  613.254397] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  613.254406] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[  613.254415] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[  613.254425] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  613.254435] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  613.369496] [drm] initialized overlay support
[  613.424111] fbcon: inteldrmfb (fb0) is primary device
[  613.480853] Console: switching to colour frame buffer device 128x37
[  613.490802] fb0: inteldrmfb frame buffer device
[  613.490811] drm: registered panic notifier
[  613.500494] acpi device:01: registered as cooling_device2
[  613.502795] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/LNXVIDEO:00/input/input6
[  613.503309] ACPI: Video Device [IGD0] (multi-head: yes  rom: no  post: no)
[  613.505515] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
[  613.505637] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[  613.505751] HDA Intel 0000:00:1b.0: irq 46 for MSI/MSI-X
[  613.505814] HDA Intel 0000:00:1b.0: setting latency timer to 64
[  613.636544] hda_codec: ALC272: BIOS auto-probing.
[  613.691183] input: HDA Intel Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input7
[  613.692430] input: HDA Intel Headphone as /devices/pci0000:00/0000:00:1b.0/sound/card0/input8
[  614.011146] ppdev: user-space parallel port driver
[  614.530824] init: plymouth-upstart-bridge main process (530) killed by TERM signal
[  615.314219] wlan0: authenticate with 90:e6:ba:8c:41:73 (try 1)
[  615.316339] wlan0: authenticated
[  615.376850] wlan0: associate with 90:e6:ba:8c:41:73 (try 1)
[  615.377025] EXT4-fs (sda5): re-mounted. Opts: errors=remount-ro,commit=600
[  615.384146] wlan0: RX AssocResp from 90:e6:ba:8c:41:73 (capab=0x411 status=0 aid=1)
[  615.384158] wlan0: associated
[  615.391899] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  615.795416] init: plymouth-stop pre-start process (1154) terminated with status 1
[  617.714220] EXT4-fs (sda5): re-mounted. Opts: errors=remount-ro,commit=600
[  625.888036] wlan0: no IPv6 routers present

```

---

