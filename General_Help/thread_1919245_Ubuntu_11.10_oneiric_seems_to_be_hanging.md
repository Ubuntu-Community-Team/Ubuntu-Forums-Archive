---
title: "Ubuntu 11.10 oneiric seems to be hanging"
date: 2012-02-02
forum: General Help
---

### Post by levidurfee on 2012-02-02
I was running 11.04, but I went to reboot and it started hanging. So after several reboots I was able to get into the recovery mode with networking and do the upgrade to 11.10. After the upgrade, the computer was doing the same thing. This computer is acts as a file server, I am able to SSH into the box and also access the drives since they are shared through samba. 

The computer is only 7 months old, 8GB of RAM...

Here is a screen shot of the monitor (it's been this way for about 16 hours), but I'm still able to access it via SSH.

[http://6c657669.info/images/ubuntu-ss-2012-02-02.jpg](http://6c657669.info/images/ubuntu-ss-2012-02-02.jpg)


Here is my dmesg
```
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 3.0.0-15-generic (buildd@crested) (gcc version 4.6.1 (Ubuntu/Linaro 4.6.1-9ubuntu3) ) #26-Ubuntu SMP Fri Jan 20 17:23:00 UTC 2012 (Ubuntu 3.0.0-15.26-generic 3.0.13)
[    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-3.0.0-15-generic root=UUID=e9b57420-f144-400c-973d-441fda128b2f ro text
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   Centaur CentaurHauls
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009c000 (usable)
[    0.000000]  BIOS-e820: 000000000009c000 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 00000000befc3000 (usable)
[    0.000000]  BIOS-e820: 00000000befc3000 - 00000000bf017000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000bf017000 - 00000000bf5a5000 (reserved)
[    0.000000]  BIOS-e820: 00000000bf5a5000 - 00000000bf5b6000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000bf5b6000 - 00000000bf5cd000 (reserved)
[    0.000000]  BIOS-e820: 00000000bf5cd000 - 00000000bf5cf000 (usable)
[    0.000000]  BIOS-e820: 00000000bf5cf000 - 00000000bf5d0000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000bf5d0000 - 00000000bf5d8000 (reserved)
[    0.000000]  BIOS-e820: 00000000bf5d8000 - 00000000bf5e2000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000bf5e2000 - 00000000bf63e000 (reserved)
[    0.000000]  BIOS-e820: 00000000bf63e000 - 00000000bf681000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000bf681000 - 00000000bf800000 (usable)
[    0.000000]  BIOS-e820: 00000000fed1c000 - 00000000fed20000 (reserved)
[    0.000000]  BIOS-e820: 00000000ff000000 - 0000000100000000 (reserved)
[    0.000000]  BIOS-e820: 0000000100000000 - 000000023f800000 (usable)
[    0.000000] NX (Execute Disable) protection: active
[    0.000000] DMI 2.6 present.
[    0.000000] DMI: System manufacturer System Product Name/P8P67 DELUXE, BIOS 1502 03/02/2011
[    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
[    0.000000] e820 remove range: 00000000000a0000 - 0000000000100000 (usable)
[    0.000000] No AGP bridge found
[    0.000000] last_pfn = 0x23f800 max_arch_pfn = 0x400000000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-D3FFF write-protect
[    0.000000]   D4000-E7FFF uncachable
[    0.000000]   E8000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000 mask E00000000 write-back
[    0.000000]   1 base 200000000 mask FC0000000 write-back
[    0.000000]   2 base 0C0000000 mask FC0000000 uncachable
[    0.000000]   3 base 23F800000 mask FFF800000 uncachable
[    0.000000]   4 disabled
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000]   8 disabled
[    0.000000]   9 disabled
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] original variable MTRRs
[    0.000000] reg 0, base: 0GB, range: 8GB, type WB
[    0.000000] reg 1, base: 8GB, range: 1GB, type WB
[    0.000000] reg 2, base: 3GB, range: 1GB, type UC
[    0.000000] reg 3, base: 9208MB, range: 8MB, type UC
[    0.000000] total RAM covered: 8184M
[    0.000000] Found optimal setting for mtrr clean up
[    0.000000]  gran_size: 64K     chunk_size: 16M     num_reg: 5      lose cover RAM: 0G
[    0.000000] New variable MTRRs
[    0.000000] reg 0, base: 0GB, range: 2GB, type WB
[    0.000000] reg 1, base: 2GB, range: 1GB, type WB
[    0.000000] reg 2, base: 4GB, range: 4GB, type WB
[    0.000000] reg 3, base: 8GB, range: 1GB, type WB
[    0.000000] reg 4, base: 9208MB, range: 8MB, type UC
[    0.000000] e820 update range: 00000000c0000000 - 0000000100000000 (usable) ==> (reserved)
[    0.000000] last_pfn = 0xbf800 max_arch_pfn = 0x400000000
[    0.000000] found SMP MP-table at [ffff8800000fce20] fce20
[    0.000000] initial memory mapped : 0 - 20000000
[    0.000000] Base memory trampoline at [ffff880000097000] 97000 size 20480
[    0.000000] init_memory_mapping: 0000000000000000-00000000bf800000
[    0.000000]  0000000000 - 00bf800000 page 2M
[    0.000000] kernel direct mapping tables up to bf800000 @ 1fffc000-20000000
[    0.000000] init_memory_mapping: 0000000100000000-000000023f800000
[    0.000000]  0100000000 - 023f800000 page 2M
[    0.000000] kernel direct mapping tables up to 23f800000 @ bf7f6000-bf800000
[    0.000000] RAMDISK: 35916000 - 36c83000
[    0.000000] ACPI: RSDP 00000000000f0420 00024 (v02 ALASKA)
[    0.000000] ACPI: XSDT 00000000bf00e068 0004C (v01 ALASKA    A M I 01072009 AMI  00010013)
[    0.000000] ACPI: FACP 00000000bf0165e0 000F4 (v04 ALASKA    A M I 01072009 AMI  00010013)
[    0.000000] ACPI: DSDT 00000000bf00e140 0849C (v02 ALASKA    A M I 00000000 INTL 20051117)
[    0.000000] ACPI: FACS 00000000bf5d9f80 00040
[    0.000000] ACPI: APIC 00000000bf0166d8 00072 (v03 ALASKA    A M I 01072009 AMI  00010013)
[    0.000000] ACPI: SSDT 00000000bf016750 00102 (v01 AMICPU     PROC 00000001 MSFT 03000001)
[    0.000000] ACPI: MCFG 00000000bf016858 0003C (v01 ALASKA    A M I 01072009 MSFT 00000097)
[    0.000000] ACPI: HPET 00000000bf016898 00038 (v01 ALASKA    A M I 01072009 AMI. 00000004)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] No NUMA configuration found
[    0.000000] Faking a node at 0000000000000000-000000023f800000
[    0.000000] Initmem setup node 0 0000000000000000-000000023f800000
[    0.000000]   NODE_DATA [000000023f7fb000 - 000000023f7fffff]
[    0.000000]  [ffffea0000000000-ffffea0007dfffff] PMD -> [ffff880236e00000-ffff88023ddfffff] on node 0
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000010 -> 0x00001000
[    0.000000]   DMA32    0x00001000 -> 0x00100000
[    0.000000]   Normal   0x00100000 -> 0x0023f800
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[5] active PFN ranges
[    0.000000]     0: 0x00000010 -> 0x0000009c
[    0.000000]     0: 0x00000100 -> 0x000befc3
[    0.000000]     0: 0x000bf5cd -> 0x000bf5cf
[    0.000000]     0: 0x000bf681 -> 0x000bf800
[    0.000000]     0: 0x00100000 -> 0x0023f800
[    0.000000] On node 0 totalpages: 2091216
[    0.000000]   DMA zone: 56 pages used for memmap
[    0.000000]   DMA zone: 5 pages reserved
[    0.000000]   DMA zone: 3919 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 14280 pages used for memmap
[    0.000000]   DMA32 zone: 764284 pages, LIFO batch:31
[    0.000000]   Normal zone: 17892 pages used for memmap
[    0.000000]   Normal zone: 1290780 pages, LIFO batch:31
[    0.000000] ACPI: PM-Timer IO Port: 0x408
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x02] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x04] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x06] enabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0xff] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x00] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 0, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x8086a701 base: 0xfed00000
[    0.000000] SMP: Allowing 4 CPUs, 0 hotplug CPUs
[    0.000000] nr_irqs_gsi: 40
[    0.000000] PM: Registered nosave memory: 000000000009c000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
[    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
[    0.000000] PM: Registered nosave memory: 00000000befc3000 - 00000000bf017000
[    0.000000] PM: Registered nosave memory: 00000000bf017000 - 00000000bf5a5000
[    0.000000] PM: Registered nosave memory: 00000000bf5a5000 - 00000000bf5b6000
[    0.000000] PM: Registered nosave memory: 00000000bf5b6000 - 00000000bf5cd000
[    0.000000] PM: Registered nosave memory: 00000000bf5cf000 - 00000000bf5d0000
[    0.000000] PM: Registered nosave memory: 00000000bf5d0000 - 00000000bf5d8000
[    0.000000] PM: Registered nosave memory: 00000000bf5d8000 - 00000000bf5e2000
[    0.000000] PM: Registered nosave memory: 00000000bf5e2000 - 00000000bf63e000
[    0.000000] PM: Registered nosave memory: 00000000bf63e000 - 00000000bf681000
[    0.000000] PM: Registered nosave memory: 00000000bf800000 - 00000000fed1c000
[    0.000000] PM: Registered nosave memory: 00000000fed1c000 - 00000000fed20000
[    0.000000] PM: Registered nosave memory: 00000000fed20000 - 00000000ff000000
[    0.000000] PM: Registered nosave memory: 00000000ff000000 - 0000000100000000
[    0.000000] Allocating PCI resources starting at bf800000 (gap: bf800000:3f51c000)
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] setup_percpu: NR_CPUS:256 nr_cpumask_bits:256 nr_cpu_ids:4 nr_node_ids:1
[    0.000000] PERCPU: Embedded 27 pages/cpu @ffff88023f400000 s79616 r8192 d22784 u524288
[    0.000000] pcpu-alloc: s79616 r8192 d22784 u524288 alloc=1*2097152
[    0.000000] pcpu-alloc: [0] 0 1 2 3 
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 2058983
[    0.000000] Policy zone: Normal
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.0.0-15-generic root=UUID=e9b57420-f144-400c-973d-441fda128b2f ro text
[    0.000000] PID hash table entries: 4096 (order: 3, 32768 bytes)
[    0.000000] xsave/xrstor: enabled xstate_bv 0x7, cntxt size 0x340
[    0.000000] Checking aperture...
[    0.000000] No AGP bridge found
[    0.000000] Calgary: detecting Calgary via BIOS EBDA area
[    0.000000] Calgary: Unable to locate Rio Grande table in EBDA - bailing!
[    0.000000] Memory: 8148160k/9428992k available (6136k kernel code, 1064128k absent, 216704k reserved, 6898k data, 988k init)
[    0.000000] SLUB: Genslabs=15, HWalign=64, Order=0-3, MinObjects=0, CPUs=4, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000]     RCU dyntick-idle grace-period acceleration is enabled.
[    0.000000] NR_IRQS:16640 nr_irqs:712 16
[    0.000000] Extended CMOS year: 2000
[    0.000000] Console: colour VGA+ 80x25
[    0.000000] console [tty0] enabled
[    0.000000] allocated 67108864 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] hpet clockevent registered
[    0.000000] Fast TSC calibration using PIT
[    0.004000] Detected 3194.173 MHz processor.
[    0.000001] Calibrating delay loop (skipped), value calculated using timer frequency.. 6388.34 BogoMIPS (lpj=12776692)
[    0.000060] pid_max: default: 32768 minimum: 301
[    0.000102] Security Framework initialized
[    0.000138] AppArmor: AppArmor initialized
[    0.000166] Yama: becoming mindful.
[    0.000747] Dentry cache hash table entries: 1048576 (order: 11, 8388608 bytes)
[    0.002064] Inode-cache hash table entries: 524288 (order: 10, 4194304 bytes)
[    0.002604] Mount-cache hash table entries: 256
[    0.002697] Initializing cgroup subsys cpuacct
[    0.002728] Initializing cgroup subsys memory
[    0.002759] Initializing cgroup subsys devices
[    0.002787] Initializing cgroup subsys freezer
[    0.002816] Initializing cgroup subsys net_cls
[    0.002844] Initializing cgroup subsys blkio
[    0.002874] Initializing cgroup subsys perf_event
[    0.002919] CPU: Physical Processor ID: 0
[    0.002947] CPU: Processor Core ID: 0
[    0.002977] ENERGY_PERF_BIAS: Set to 'normal', was 'performance'
[    0.002977] ENERGY_PERF_BIAS: View and update with x86_energy_perf_policy(8)
[    0.003036] mce: CPU supports 9 MCE banks
[    0.003073] CPU0: Thermal monitoring enabled (TM1)
[    0.003106] using mwait in idle threads.
[    0.004867] ACPI: Core revision 20110413
[    0.108255] ftrace: allocating 25728 entries in 101 pages
[    0.115278] x2apic not enabled, IRQ remapping init failed
[    0.115694] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.155334] CPU0: Intel(R) Core(TM) i5-2400 CPU @ 3.10GHz stepping 07
[    0.260021] Performance Events: PEBS fmt1+, SandyBridge events, Intel PMU driver.
[    0.260120] ... version:                3
[    0.260148] ... bit width:              48
[    0.260176] ... generic registers:      8
[    0.260204] ... value mask:             0000ffffffffffff
[    0.260232] ... max period:             000000007fffffff
[    0.260261] ... fixed-purpose events:   3
[    0.260288] ... event mask:             00000007000000ff
[    0.260584] Booting Node   0, Processors  #1
[    0.260629] smpboot cpu 1: start_ip = 97000
[    0.367939]  #2
[    0.367963] smpboot cpu 2: start_ip = 97000
[    0.475768]  #3 Ok.
[    0.475796] smpboot cpu 3: start_ip = 97000
[    0.583430] Brought up 4 CPUs
[    0.583459] Total of 4 processors activated (25549.46 BogoMIPS).
[    0.585278] devtmpfs: initialized
[    0.585385] PM: Registering ACPI NVS region at befc3000 (344064 bytes)
[    0.585418] PM: Registering ACPI NVS region at bf5a5000 (69632 bytes)
[    0.585448] PM: Registering ACPI NVS region at bf5cf000 (4096 bytes)
[    0.585477] PM: Registering ACPI NVS region at bf5d8000 (40960 bytes)
[    0.585507] PM: Registering ACPI NVS region at bf63e000 (274432 bytes)
[    0.586457] print_constraints: dummy: 
[    0.586507] Time:  1:24:55  Date: 02/02/12
[    0.586553] NET: Registered protocol family 16
[    0.586640] ACPI: bus type pci registered
[    0.586643] Trying to unpack rootfs image as initramfs...
[    0.586728] PCI: MMCONFIG for domain 0000 [bus 00-3f] at [mem 0xe0000000-0xe3ffffff] (base 0xe0000000)
[    0.586764] PCI: not using MMCONFIG
[    0.586792] PCI: Using configuration type 1 for base access
[    0.587216] bio: create slab <bio-0> at 0
[    0.587983] ACPI: EC: Look up EC in DSDT
[    0.588643] ACPI: Executed 1 blocks of module-level executable AML code
[    0.590102] ACPI Error: [RAMB] Namespace lookup failure, AE_NOT_FOUND (20110413/psargs-359)
[    0.590202] ACPI Exception: AE_NOT_FOUND, Could not execute arguments for [RAMW] (Region) (20110413/nsinit-349)
[    0.590437] ACPI: SSDT 00000000bf5d8c18 0038C (v01    AMI      IST 00000001 MSFT 03000001)
[    0.590713] ACPI: Dynamic OEM Table Load:
[    0.590783] ACPI: SSDT           (null) 0038C (v01    AMI      IST 00000001 MSFT 03000001)
[    0.590872] ACPI: SSDT 00000000bf5d9e18 00084 (v01    AMI      CST 00000001 MSFT 03000001)
[    0.591684] ACPI: Dynamic OEM Table Load:
[    0.591754] ACPI: SSDT           (null) 00084 (v01    AMI      CST 00000001 MSFT 03000001)
[    0.592117] ACPI: Interpreter enabled
[    0.592146] ACPI: (supports S0 S1 S3 S4 S5)
[    0.592288] ACPI: Using IOAPIC for interrupt routing
[    0.592330] PCI: MMCONFIG for domain 0000 [bus 00-3f] at [mem 0xe0000000-0xe3ffffff] (base 0xe0000000)
[    0.592407] PCI: MMCONFIG at [mem 0xe0000000-0xe3ffffff] reserved in ACPI motherboard resources
[    0.602307] [Firmware Bug]: ACPI: BIOS _OSI(Linux) query ignored
[    0.605357] ACPI: EC: GPE = 0x18, I/O: command/status = 0x66, data = 0x62
[    0.605492] ACPI: No dock devices found.
[    0.605520] HEST: Table not found.
[    0.605549] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
[    0.605699] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-ff])
[    0.605854] pci_root PNP0A08:00: host bridge window [io  0x0000-0x0cf7]
[    0.605884] pci_root PNP0A08:00: host bridge window [io  0x0d00-0xffff]
[    0.605913] pci_root PNP0A08:00: host bridge window [mem 0x000a0000-0x000bffff]
[    0.605948] pci_root PNP0A08:00: host bridge window [mem 0x000c8000-0x000dffff]
[    0.605982] pci_root PNP0A08:00: host bridge window [mem 0xc0000000-0xffffffff]
[    0.606019] pci_root PNP0A08:00: address space collision: host bridge window [mem 0x000c8000-0x000dffff] conflicts with Video ROM [mem 0x000c0000-0x000cf1ff]
[    0.606062] pci 0000:00:00.0: [8086:0100] type 0 class 0x000600
[    0.606086] pci 0000:00:01.0: [8086:0101] type 1 class 0x000604
[    0.606105] pci 0000:00:01.0: PME# supported from D0 D3hot D3cold
[    0.606107] pci 0000:00:01.0: PME# disabled
[    0.606143] pci 0000:00:16.0: [8086:1c3a] type 0 class 0x000780
[    0.606163] pci 0000:00:16.0: reg 10: [mem 0xfe729000-0xfe72900f 64bit]
[    0.606219] pci 0000:00:16.0: PME# supported from D0 D3hot D3cold
[    0.606223] pci 0000:00:16.0: PME# disabled
[    0.606247] pci 0000:00:19.0: [8086:1503] type 0 class 0x000200
[    0.606262] pci 0000:00:19.0: reg 10: [mem 0xfe700000-0xfe71ffff]
[    0.606269] pci 0000:00:19.0: reg 14: [mem 0xfe728000-0xfe728fff]
[    0.606277] pci 0000:00:19.0: reg 18: [io  0xf040-0xf05f]
[    0.606320] pci 0000:00:19.0: PME# supported from D0 D3hot D3cold
[    0.606323] pci 0000:00:19.0: PME# disabled
[    0.606342] pci 0000:00:1a.0: [8086:1c2d] type 0 class 0x000c03
[    0.606361] pci 0000:00:1a.0: reg 10: [mem 0xfe727000-0xfe7273ff]
[    0.606426] pci 0000:00:1a.0: PME# supported from D0 D3hot D3cold
[    0.606429] pci 0000:00:1a.0: PME# disabled
[    0.606448] pci 0000:00:1b.0: [8086:1c20] type 0 class 0x000403
[    0.606461] pci 0000:00:1b.0: reg 10: [mem 0xfe720000-0xfe723fff 64bit]
[    0.606508] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    0.606511] pci 0000:00:1b.0: PME# disabled
[    0.606528] pci 0000:00:1c.0: [8086:1c10] type 1 class 0x000604
[    0.606582] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    0.606585] pci 0000:00:1c.0: PME# disabled
[    0.606607] pci 0000:00:1c.4: [8086:1c18] type 1 class 0x000604
[    0.606662] pci 0000:00:1c.4: PME# supported from D0 D3hot D3cold
[    0.606665] pci 0000:00:1c.4: PME# disabled
[    0.606685] pci 0000:00:1c.6: [8086:1c1c] type 1 class 0x000604
[    0.606740] pci 0000:00:1c.6: PME# supported from D0 D3hot D3cold
[    0.606743] pci 0000:00:1c.6: PME# disabled
[    0.606761] pci 0000:00:1c.7: [8086:1c1e] type 1 class 0x000604
[    0.606816] pci 0000:00:1c.7: PME# supported from D0 D3hot D3cold
[    0.606819] pci 0000:00:1c.7: PME# disabled
[    0.606842] pci 0000:00:1d.0: [8086:1c26] type 0 class 0x000c03
[    0.606860] pci 0000:00:1d.0: reg 10: [mem 0xfe726000-0xfe7263ff]
[    0.606926] pci 0000:00:1d.0: PME# supported from D0 D3hot D3cold
[    0.606929] pci 0000:00:1d.0: PME# disabled
[    0.606949] pci 0000:00:1f.0: [8086:1c46] type 0 class 0x000601
[    0.607052] pci 0000:00:1f.2: [8086:1c02] type 0 class 0x000106
[    0.607067] pci 0000:00:1f.2: reg 10: [io  0xf090-0xf097]
[    0.607074] pci 0000:00:1f.2: reg 14: [io  0xf080-0xf083]
[    0.607080] pci 0000:00:1f.2: reg 18: [io  0xf070-0xf077]
[    0.607086] pci 0000:00:1f.2: reg 1c: [io  0xf060-0xf063]
[    0.607093] pci 0000:00:1f.2: reg 20: [io  0xf020-0xf03f]
[    0.607099] pci 0000:00:1f.2: reg 24: [mem 0xfe725000-0xfe7257ff]
[    0.607127] pci 0000:00:1f.2: PME# supported from D3hot
[    0.607130] pci 0000:00:1f.2: PME# disabled
[    0.607142] pci 0000:00:1f.3: [8086:1c22] type 0 class 0x000c05
[    0.607155] pci 0000:00:1f.3: reg 10: [mem 0xfe724000-0xfe7240ff 64bit]
[    0.607174] pci 0000:00:1f.3: reg 20: [io  0xf000-0xf01f]
[    0.607216] pci 0000:01:00.0: [1002:9552] type 0 class 0x000300
[    0.607226] pci 0000:01:00.0: reg 10: [mem 0xc0000000-0xcfffffff 64bit pref]
[    0.607235] pci 0000:01:00.0: reg 18: [mem 0xfe620000-0xfe62ffff 64bit]
[    0.607240] pci 0000:01:00.0: reg 20: [io  0xe000-0xe0ff]
[    0.607251] pci 0000:01:00.0: reg 30: [mem 0xfe600000-0xfe61ffff pref]
[    0.607265] pci 0000:01:00.0: supports D1 D2
[    0.607280] pci 0000:01:00.1: [1002:aa38] type 0 class 0x000403
[    0.607290] pci 0000:01:00.1: reg 10: [mem 0xfe630000-0xfe633fff 64bit]
[    0.607330] pci 0000:01:00.1: supports D1 D2
[    0.615309] pci 0000:00:01.0: PCI bridge to [bus 01-01]
[    0.615339] pci 0000:00:01.0:   bridge window [io  0xe000-0xefff]
[    0.615341] pci 0000:00:01.0:   bridge window [mem 0xfe600000-0xfe6fffff]
[    0.615344] pci 0000:00:01.0:   bridge window [mem 0xc0000000-0xcfffffff 64bit pref]
[    0.615383] pci 0000:00:1c.0: PCI bridge to [bus 02-02]
[    0.615414] pci 0000:00:1c.0:   bridge window [io  0xf000-0x0000] (disabled)
[    0.615417] pci 0000:00:1c.0:   bridge window [mem 0xfff00000-0x000fffff] (disabled)
[    0.615423] pci 0000:00:1c.0:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    0.615483] pci 0000:03:00.0: [1033:0194] type 0 class 0x000c03
[    0.615508] pci 0000:03:00.0: reg 10: [mem 0xfe500000-0xfe501fff 64bit]
[    0.615609] pci 0000:03:00.0: PME# supported from D0 D3hot D3cold
[    0.615613] pci 0000:03:00.0: PME# disabled
[    0.623296] pci 0000:00:1c.4: PCI bridge to [bus 03-03]
[    0.623327] pci 0000:00:1c.4:   bridge window [io  0xf000-0x0000] (disabled)
[    0.623331] pci 0000:00:1c.4:   bridge window [mem 0xfe500000-0xfe5fffff]
[    0.623336] pci 0000:00:1c.4:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    0.623397] pci 0000:04:00.0: [1033:0194] type 0 class 0x000c03
[    0.623422] pci 0000:04:00.0: reg 10: [mem 0xfe400000-0xfe401fff 64bit]
[    0.623523] pci 0000:04:00.0: PME# supported from D0 D3hot D3cold
[    0.623528] pci 0000:04:00.0: PME# disabled
[    0.631281] pci 0000:00:1c.6: PCI bridge to [bus 04-04]
[    0.631313] pci 0000:00:1c.6:   bridge window [io  0xf000-0x0000] (disabled)
[    0.631316] pci 0000:00:1c.6:   bridge window [mem 0xfe400000-0xfe4fffff]
[    0.631321] pci 0000:00:1c.6:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    0.631378] pci 0000:05:00.0: [10b5:8608] type 1 class 0x000604
[    0.631395] pci 0000:05:00.0: reg 10: [mem 0xfe300000-0xfe31ffff]
[    0.631469] pci 0000:05:00.0: PME# supported from D0 D3hot D3cold
[    0.631473] pci 0000:05:00.0: PME# disabled
[    0.639261] pci 0000:00:1c.7: PCI bridge to [bus 05-0e]
[    0.639293] pci 0000:00:1c.7:   bridge window [io  0xa000-0xdfff]
[    0.639296] pci 0000:00:1c.7:   bridge window [mem 0xfe000000-0xfe3fffff]
[    0.639301] pci 0000:00:1c.7:   bridge window [mem 0xd0000000-0xd00fffff 64bit pref]
[    0.639387] pci 0000:06:01.0: [10b5:8608] type 1 class 0x000604
[    0.639478] pci 0000:06:01.0: PME# supported from D0 D3hot D3cold
[    0.639483] pci 0000:06:01.0: PME# disabled
[    0.639528] pci 0000:06:04.0: [10b5:8608] type 1 class 0x000604
[    0.639620] pci 0000:06:04.0: PME# supported from D0 D3hot D3cold
[    0.639624] pci 0000:06:04.0: PME# disabled
[    0.639668] pci 0000:06:05.0: [10b5:8608] type 1 class 0x000604
[    0.639758] pci 0000:06:05.0: PME# supported from D0 D3hot D3cold
[    0.639762] pci 0000:06:05.0: PME# disabled
[    0.639807] pci 0000:06:06.0: [10b5:8608] type 1 class 0x000604
[    0.639897] pci 0000:06:06.0: PME# supported from D0 D3hot D3cold
[    0.639901] pci 0000:06:06.0: PME# disabled
[    0.639949] pci 0000:06:07.0: [10b5:8608] type 1 class 0x000604
[    0.640039] pci 0000:06:07.0: PME# supported from D0 D3hot D3cold
[    0.640043] pci 0000:06:07.0: PME# disabled
[    0.640092] pci 0000:06:08.0: [10b5:8608] type 1 class 0x000604
[    0.640181] pci 0000:06:08.0: PME# supported from D0 D3hot D3cold
[    0.640185] pci 0000:06:08.0: PME# disabled
[    0.640235] pci 0000:06:09.0: [10b5:8608] type 1 class 0x000604
[    0.640325] pci 0000:06:09.0: PME# supported from D0 D3hot D3cold
[    0.640329] pci 0000:06:09.0: PME# disabled
[    0.640397] pci 0000:05:00.0: PCI bridge to [bus 06-0e]
[    0.640431] pci 0000:05:00.0:   bridge window [io  0xa000-0xdfff]
[    0.640436] pci 0000:05:00.0:   bridge window [mem 0xfe000000-0xfe2fffff]
[    0.640443] pci 0000:05:00.0:   bridge window [mem 0xd0000000-0xd00fffff 64bit pref]
[    0.640532] pci 0000:07:00.0: [1106:3403] type 0 class 0x000c00
[    0.640563] pci 0000:07:00.0: reg 10: [mem 0xfe200000-0xfe2007ff 64bit]
[    0.640579] pci 0000:07:00.0: reg 18: [io  0xd000-0xd0ff]
[    0.640683] pci 0000:07:00.0: supports D2
[    0.640684] pci 0000:07:00.0: PME# supported from D2 D3hot D3cold
[    0.640689] pci 0000:07:00.0: PME# disabled
[    0.647251] pci 0000:06:01.0: PCI bridge to [bus 07-07]
[    0.647286] pci 0000:06:01.0:   bridge window [io  0xd000-0xdfff]
[    0.647290] pci 0000:06:01.0:   bridge window [mem 0xfe200000-0xfe2fffff]
[    0.647298] pci 0000:06:01.0:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    0.647368] pci 0000:06:04.0: PCI bridge to [bus 08-08]
[    0.647402] pci 0000:06:04.0:   bridge window [io  0xfff000-0x0000] (disabled)
[    0.647407] pci 0000:06:04.0:   bridge window [mem 0xfff00000-0x000fffff] (disabled)
[    0.647415] pci 0000:06:04.0:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    0.647504] pci 0000:09:00.0: [197b:2362] type 0 class 0x000101
[    0.647543] pci 0000:09:00.0: reg 10: [io  0xc040-0xc047]
[    0.647561] pci 0000:09:00.0: reg 14: [io  0xc030-0xc033]
[    0.647579] pci 0000:09:00.0: reg 18: [io  0xc020-0xc027]
[    0.647597] pci 0000:09:00.0: reg 1c: [io  0xc010-0xc013]
[    0.647615] pci 0000:09:00.0: reg 20: [io  0xc000-0xc00f]
[    0.647633] pci 0000:09:00.0: reg 24: [mem 0xfe110000-0xfe1101ff]
[    0.647651] pci 0000:09:00.0: reg 30: [mem 0x00000000-0x0000ffff pref]
[    0.647693] pci 0000:09:00.0: PME# supported from D3hot
[    0.647699] pci 0000:09:00.0: PME# disabled
[    0.655234] pci 0000:06:05.0: PCI bridge to [bus 09-09]
[    0.655270] pci 0000:06:05.0:   bridge window [io  0xc000-0xcfff]
[    0.655274] pci 0000:06:05.0:   bridge window [mem 0xfe100000-0xfe1fffff]
[    0.655281] pci 0000:06:05.0:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    0.655370] pci 0000:0a:00.0: [1b4b:9130] type 0 class 0x000106
[    0.655390] pci 0000:0a:00.0: reg 10: [io  0xb090-0xb097]
[    0.655404] pci 0000:0a:00.0: reg 14: [io  0xb080-0xb083]
[    0.655418] pci 0000:0a:00.0: reg 18: [io  0xb070-0xb077]
[    0.655432] pci 0000:0a:00.0: reg 1c: [io  0xb060-0xb063]
[    0.655446] pci 0000:0a:00.0: reg 20: [io  0xb050-0xb05f]
[    0.655460] pci 0000:0a:00.0: reg 24: [mem 0xfe021000-0xfe0217ff]
[    0.655474] pci 0000:0a:00.0: reg 30: [mem 0xfe010000-0xfe01ffff pref]
[    0.655514] pci 0000:0a:00.0: PME# supported from D3hot
[    0.655519] pci 0000:0a:00.0: PME# disabled
[    0.655563] pci 0000:06:06.0: PCI bridge to [bus 0a-0a]
[    0.655598] pci 0000:06:06.0:   bridge window [io  0xb000-0xbfff]
[    0.655602] pci 0000:06:06.0:   bridge window [mem 0xfe000000-0xfe0fffff]
[    0.655610] pci 0000:06:06.0:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    0.655679] pci 0000:06:07.0: PCI bridge to [bus 0b-0b]
[    0.655714] pci 0000:06:07.0:   bridge window [io  0xfff000-0x0000] (disabled)
[    0.655718] pci 0000:06:07.0:   bridge window [mem 0xfff00000-0x000fffff] (disabled)
[    0.655726] pci 0000:06:07.0:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    0.655823] pci 0000:0c:00.0: [1b21:1080] type 1 class 0x000604
[    0.655963] pci 0000:0c:00.0: supports D1 D2
[    0.655964] pci 0000:0c:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.655970] pci 0000:0c:00.0: PME# disabled
[    0.663215] pci 0000:06:08.0: PCI bridge to [bus 0c-0d]
[    0.663251] pci 0000:06:08.0:   bridge window [io  0xfff000-0x0000] (disabled)
[    0.663256] pci 0000:06:08.0:   bridge window [mem 0xfff00000-0x000fffff] (disabled)
[    0.663263] pci 0000:06:08.0:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    0.663447] pci 0000:0c:00.0: PCI bridge to [bus 0d-0d]
[    0.663485] pci 0000:0c:00.0:   bridge window [io  0xfff000-0x0000] (disabled)
[    0.663492] pci 0000:0c:00.0:   bridge window [mem 0xfff00000-0x000fffff] (disabled)
[    0.663502] pci 0000:0c:00.0:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    0.663607] pci 0000:0e:00.0: [10ec:8168] type 0 class 0x000200
[    0.663630] pci 0000:0e:00.0: reg 10: [io  0xa000-0xa0ff]
[    0.663669] pci 0000:0e:00.0: reg 18: [mem 0xd0004000-0xd0004fff 64bit pref]
[    0.663694] pci 0000:0e:00.0: reg 20: [mem 0xd0000000-0xd0003fff 64bit pref]
[    0.663764] pci 0000:0e:00.0: supports D1 D2
[    0.663765] pci 0000:0e:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.663771] pci 0000:0e:00.0: PME# disabled
[    0.671204] pci 0000:06:09.0: PCI bridge to [bus 0e-0e]
[    0.671240] pci 0000:06:09.0:   bridge window [io  0xa000-0xafff]
[    0.671244] pci 0000:06:09.0:   bridge window [mem 0xfff00000-0x000fffff] (disabled)
[    0.671252] pci 0000:06:09.0:   bridge window [mem 0xd0000000-0xd00fffff 64bit pref]
[    0.671327] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.671395] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P1._PRT]
[    0.671413] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEX0._PRT]
[    0.671430] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEX4._PRT]
[    0.671447] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEX6._PRT]
[    0.671462] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEX7._PRT]
[    0.671514] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEX7.BR24.BR30.BR31._PRT]
[    0.671602]  pci0000:00: Requesting ACPI _OSC control (0x1d)
[    0.671757]  pci0000:00: ACPI _OSC control (0x1c) granted
[    0.674071] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 10 *11 12 14 15)
[    0.674374] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 *10 11 12 14 15)
[    0.674676] ACPI: PCI Interrupt Link [LNKC] (IRQs *3 4 5 6 10 11 12 14 15)
[    0.674956] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 *10 11 12 14 15)
[    0.675240] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 *5 6 7 10 11 12 14 15)
[    0.675541] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 *5 6 7 10 11 12 14 15)
[    0.675842] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 10 *11 12 14 15)
[    0.676144] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 *7 10 11 12 14 15)
[    0.676482] vgaarb: device added: PCI:0000:01:00.0,decodes=io+mem,owns=io+mem,locks=none
[    0.676521] vgaarb: loaded
[    0.676548] vgaarb: bridge control possible 0000:01:00.0
[    0.676671] SCSI subsystem initialized
[    0.676728] libata version 3.00 loaded.
[    0.676752] usbcore: registered new interface driver usbfs
[    0.676785] usbcore: registered new interface driver hub
[    0.676823] usbcore: registered new device driver usb
[    0.676893] PCI: Using ACPI for IRQ routing
[    0.678052] PCI: pci_cache_line_size set to 64 bytes
[    0.678156] reserve RAM buffer: 000000000009c000 - 000000000009ffff 
[    0.678158] reserve RAM buffer: 00000000befc3000 - 00000000bfffffff 
[    0.678160] reserve RAM buffer: 00000000bf5cf000 - 00000000bfffffff 
[    0.678161] reserve RAM buffer: 00000000bf800000 - 00000000bfffffff 
[    0.678163] reserve RAM buffer: 000000023f800000 - 000000023fffffff 
[    0.678217] NetLabel: Initializing
[    0.678244] NetLabel:  domain hash size = 128
[    0.678272] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.678306] NetLabel:  unlabeled traffic allowed by default
[    0.678358] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0, 0, 0, 0, 0
[    0.678575] hpet0: 8 comparators, 64-bit 14.318180 MHz counter
[    0.680615] Switching to clocksource hpet
[    0.683166] Switched to NOHz mode on CPU #0
[    0.683232] Switched to NOHz mode on CPU #3
[    0.683256] Switched to NOHz mode on CPU #1
[    0.683304] Switched to NOHz mode on CPU #2
[    0.684034] AppArmor: AppArmor Filesystem Enabled
[    0.684076] pnp: PnP ACPI init
[    0.684110] ACPI: bus type pnp registered
[    0.684226] pnp 00:00: [bus 00-ff]
[    0.684227] pnp 00:00: [io  0x0cf8-0x0cff]
[    0.684229] pnp 00:00: [io  0x0000-0x0cf7 window]
[    0.684230] pnp 00:00: [io  0x0d00-0xffff window]
[    0.684231] pnp 00:00: [mem 0x000a0000-0x000bffff window]
[    0.684233] pnp 00:00: [mem 0x000c8000-0x000dffff window]
[    0.684234] pnp 00:00: [mem 0xc0000000-0xffffffff window]
[    0.684235] pnp 00:00: [mem 0x00000000 window]
[    0.684276] pnp 00:00: Plug and Play ACPI device, IDs PNP0a08 PNP0a03 (active)
[    0.684310] pnp 00:01: [mem 0xfed10000-0xfed19fff]
[    0.684311] pnp 00:01: [mem 0xe0000000-0xe3ffffff]
[    0.684312] pnp 00:01: [mem 0xfed90000-0xfed93fff]
[    0.684313] pnp 00:01: [mem 0xfed20000-0xfed3ffff]
[    0.684314] pnp 00:01: [mem 0xfee00000-0xfee0ffff]
[    0.684345] system 00:01: [mem 0xfed10000-0xfed19fff] has been reserved
[    0.684375] system 00:01: [mem 0xe0000000-0xe3ffffff] has been reserved
[    0.684404] system 00:01: [mem 0xfed90000-0xfed93fff] has been reserved
[    0.684434] system 00:01: [mem 0xfed20000-0xfed3ffff] has been reserved
[    0.684464] system 00:01: [mem 0xfee00000-0xfee0ffff] has been reserved
[    0.684494] system 00:01: Plug and Play ACPI device, IDs PNP0c01 (active)
[    0.684532] pnp 00:02: [io  0x0000-0xffffffffffffffff disabled]
[    0.684534] pnp 00:02: [io  0x0000-0xffffffffffffffff disabled]
[    0.684535] pnp 00:02: [io  0x0290-0x029f]
[    0.684536] pnp 00:02: [io  0x0000-0xffffffffffffffff disabled]
[    0.684561] system 00:02: [io  0x0290-0x029f] has been reserved
[    0.684591] system 00:02: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.684599] pnp 00:03: [dma 4]
[    0.684600] pnp 00:03: [io  0x0000-0x000f]
[    0.684601] pnp 00:03: [io  0x0081-0x0083]
[    0.684602] pnp 00:03: [io  0x0087]
[    0.684603] pnp 00:03: [io  0x0089-0x008b]
[    0.684604] pnp 00:03: [io  0x008f]
[    0.684605] pnp 00:03: [io  0x00c0-0x00df]
[    0.684616] pnp 00:03: Plug and Play ACPI device, IDs PNP0200 (active)
[    0.684623] pnp 00:04: [io  0x0070-0x0071]
[    0.684629] pnp 00:04: [irq 8]
[    0.684640] pnp 00:04: Plug and Play ACPI device, IDs PNP0b00 (active)
[    0.684645] pnp 00:05: [io  0x0061]
[    0.684658] pnp 00:05: Plug and Play ACPI device, IDs PNP0800 (active)
[    0.684667] pnp 00:06: [io  0x0010-0x001f]
[    0.684668] pnp 00:06: [io  0x0022-0x003f]
[    0.684669] pnp 00:06: [io  0x0044-0x005f]
[    0.684670] pnp 00:06: [io  0x0063]
[    0.684671] pnp 00:06: [io  0x0065]
[    0.684673] pnp 00:06: [io  0x0067-0x006f]
[    0.684674] pnp 00:06: [io  0x0072-0x007f]
[    0.684675] pnp 00:06: [io  0x0080]
[    0.684681] pnp 00:06: [io  0x0084-0x0086]
[    0.684682] pnp 00:06: [io  0x0088]
[    0.684683] pnp 00:06: [io  0x008c-0x008e]
[    0.684684] pnp 00:06: [io  0x0090-0x009f]
[    0.684685] pnp 00:06: [io  0x00a2-0x00bf]
[    0.684686] pnp 00:06: [io  0x00e0-0x00ef]
[    0.684688] pnp 00:06: [io  0x04d0-0x04d1]
[    0.684717] system 00:06: [io  0x04d0-0x04d1] has been reserved
[    0.684747] system 00:06: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.684752] pnp 00:07: [io  0x00f0-0x00ff]
[    0.684755] pnp 00:07: [irq 13]
[    0.684766] pnp 00:07: Plug and Play ACPI device, IDs PNP0c04 (active)
[    0.684920] pnp 00:08: [io  0x03f8-0x03ff]
[    0.684924] pnp 00:08: [irq 4]
[    0.684925] pnp 00:08: [dma 0 disabled]
[    0.684955] pnp 00:08: Plug and Play ACPI device, IDs PNP0501 (active)
[    0.685032] pnp 00:09: [io  0x0400-0x0453]
[    0.685034] pnp 00:09: [io  0x0458-0x047f]
[    0.685035] pnp 00:09: [io  0x0000-0xffffffffffffffff disabled]
[    0.685036] pnp 00:09: [io  0x0500-0x057f]
[    0.685037] pnp 00:09: [mem 0xfed1c000-0xfed1ffff]
[    0.685038] pnp 00:09: [mem 0xfec00000-0xfecfffff]
[    0.685040] pnp 00:09: [mem 0xfed08000-0xfed08fff]
[    0.685041] pnp 00:09: [mem 0xff000000-0xffffffff]
[    0.685067] system 00:09: [io  0x0400-0x0453] has been reserved
[    0.685096] system 00:09: [io  0x0458-0x047f] has been reserved
[    0.685126] system 00:09: [io  0x0500-0x057f] has been reserved
[    0.685155] system 00:09: [mem 0xfed1c000-0xfed1ffff] has been reserved
[    0.685185] system 00:09: [mem 0xfec00000-0xfecfffff] could not be reserved
[    0.685215] system 00:09: [mem 0xfed08000-0xfed08fff] has been reserved
[    0.685245] system 00:09: [mem 0xff000000-0xffffffff] has been reserved
[    0.685275] system 00:09: Plug and Play ACPI device, IDs PNP0c01 (active)
[    0.685299] pnp 00:0a: [io  0x0454-0x0457]
[    0.685321] system 00:0a: [io  0x0454-0x0457] has been reserved
[    0.685351] system 00:0a: Plug and Play ACPI device, IDs INT3f0d PNP0c02 (active)
[    0.685430] pnp 00:0b: [mem 0xfed00000-0xfed003ff]
[    0.685452] pnp 00:0b: Plug and Play ACPI device, IDs PNP0103 (active)
[    0.685532] pnp: PnP ACPI: found 12 devices
[    0.685560] ACPI: ACPI bus type pnp unregistered
[    0.690785] PCI: max bus depth: 4 pci_try_num: 5
[    0.690904] pci 0000:00:01.0: PCI bridge to [bus 01-01]
[    0.690934] pci 0000:00:01.0:   bridge window [io  0xe000-0xefff]
[    0.690964] pci 0000:00:01.0:   bridge window [mem 0xfe600000-0xfe6fffff]
[    0.690994] pci 0000:00:01.0:   bridge window [mem 0xc0000000-0xcfffffff 64bit pref]
[    0.691030] pci 0000:00:1c.0: PCI bridge to [bus 02-02]
[    0.691059] pci 0000:00:1c.0:   bridge window [io  disabled]
[    0.691090] pci 0000:00:1c.0:   bridge window [mem disabled]
[    0.691121] pci 0000:00:1c.0:   bridge window [mem pref disabled]
[    0.691154] pci 0000:00:1c.4: PCI bridge to [bus 03-03]
[    0.691183] pci 0000:00:1c.4:   bridge window [io  disabled]
[    0.691214] pci 0000:00:1c.4:   bridge window [mem 0xfe500000-0xfe5fffff]
[    0.691246] pci 0000:00:1c.4:   bridge window [mem pref disabled]
[    0.691278] pci 0000:00:1c.6: PCI bridge to [bus 04-04]
[    0.691307] pci 0000:00:1c.6:   bridge window [io  disabled]
[    0.691339] pci 0000:00:1c.6:   bridge window [mem 0xfe400000-0xfe4fffff]
[    0.691370] pci 0000:00:1c.6:   bridge window [mem pref disabled]
[    0.691406] pci 0000:06:05.0: BAR 15: can't assign mem pref (size 0x100000)
[    0.691436] pci 0000:06:01.0: PCI bridge to [bus 07-07]
[    0.691466] pci 0000:06:01.0:   bridge window [io  0xd000-0xdfff]
[    0.691500] pci 0000:06:01.0:   bridge window [mem 0xfe200000-0xfe2fffff]
[    0.691532] pci 0000:06:01.0:   bridge window [mem pref disabled]
[    0.691567] pci 0000:06:04.0: PCI bridge to [bus 08-08]
[    0.691596] pci 0000:06:04.0:   bridge window [io  disabled]
[    0.691629] pci 0000:06:04.0:   bridge window [mem disabled]
[    0.691661] pci 0000:06:04.0:   bridge window [mem pref disabled]
[    0.691697] pci 0000:09:00.0: BAR 6: assigned [mem 0xfe100000-0xfe10ffff pref]
[    0.691731] pci 0000:06:05.0: PCI bridge to [bus 09-09]
[    0.691761] pci 0000:06:05.0:   bridge window [io  0xc000-0xcfff]
[    0.691795] pci 0000:06:05.0:   bridge window [mem 0xfe100000-0xfe1fffff]
[    0.691828] pci 0000:06:05.0:   bridge window [mem pref disabled]
[    0.691863] pci 0000:06:06.0: PCI bridge to [bus 0a-0a]
[    0.691893] pci 0000:06:06.0:   bridge window [io  0xb000-0xbfff]
[    0.691927] pci 0000:06:06.0:   bridge window [mem 0xfe000000-0xfe0fffff]
[    0.691959] pci 0000:06:06.0:   bridge window [mem pref disabled]
[    0.691994] pci 0000:06:07.0: PCI bridge to [bus 0b-0b]
[    0.692023] pci 0000:06:07.0:   bridge window [io  disabled]
[    0.692056] pci 0000:06:07.0:   bridge window [mem disabled]
[    0.692088] pci 0000:06:07.0:   bridge window [mem pref disabled]
[    0.692124] pci 0000:0c:00.0: PCI bridge to [bus 0d-0d]
[    0.692152] pci 0000:0c:00.0:   bridge window [io  disabled]
[    0.692188] pci 0000:0c:00.0:   bridge window [mem disabled]
[    0.692221] pci 0000:0c:00.0:   bridge window [mem pref disabled]
[    0.692259] pci 0000:06:08.0: PCI bridge to [bus 0c-0d]
[    0.692288] pci 0000:06:08.0:   bridge window [io  disabled]
[    0.692321] pci 0000:06:08.0:   bridge window [mem disabled]
[    0.692353] pci 0000:06:08.0:   bridge window [mem pref disabled]
[    0.692388] pci 0000:06:09.0: PCI bridge to [bus 0e-0e]
[    0.692418] pci 0000:06:09.0:   bridge window [io  0xa000-0xafff]
[    0.692452] pci 0000:06:09.0:   bridge window [mem disabled]
[    0.692484] pci 0000:06:09.0:   bridge window [mem 0xd0000000-0xd00fffff 64bit pref]
[    0.692525] pci 0000:05:00.0: PCI bridge to [bus 06-0e]
[    0.692555] pci 0000:05:00.0:   bridge window [io  0xa000-0xdfff]
[    0.692589] pci 0000:05:00.0:   bridge window [mem 0xfe000000-0xfe2fffff]
[    0.692621] pci 0000:05:00.0:   bridge window [mem 0xd0000000-0xd00fffff 64bit pref]
[    0.692667] pci 0000:00:1c.7: PCI bridge to [bus 05-0e]
[    0.692696] pci 0000:00:1c.7:   bridge window [io  0xa000-0xdfff]
[    0.692728] pci 0000:00:1c.7:   bridge window [mem 0xfe000000-0xfe3fffff]
[    0.692760] pci 0000:00:1c.7:   bridge window [mem 0xd0000000-0xd00fffff 64bit pref]
[    0.692805] pci 0000:00:01.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.692835] pci 0000:00:01.0: setting latency timer to 64
[    0.692841] pci 0000:00:1c.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    0.692873] pci 0000:00:1c.0: setting latency timer to 64
[    0.692878] pci 0000:00:1c.4: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    0.692909] pci 0000:00:1c.4: setting latency timer to 64
[    0.692915] pci 0000:00:1c.6: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.692946] pci 0000:00:1c.6: setting latency timer to 64
[    0.692952] pci 0000:00:1c.7: PCI INT D -> GSI 19 (level, low) -> IRQ 19
[    0.692984] pci 0000:00:1c.7: setting latency timer to 64
[    0.692990] pci 0000:05:00.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    0.693023] pci 0000:05:00.0: setting latency timer to 64
[    0.693029] pci 0000:06:01.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.693062] pci 0000:06:01.0: setting latency timer to 64
[    0.693069] pci 0000:06:04.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    0.693101] pci 0000:06:04.0: setting latency timer to 64
[    0.693107] pci 0000:06:05.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.693140] pci 0000:06:05.0: setting latency timer to 64
[    0.693146] pci 0000:06:06.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    0.693179] pci 0000:06:06.0: setting latency timer to 64
[    0.693186] pci 0000:06:07.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    0.693218] pci 0000:06:07.0: setting latency timer to 64
[    0.693225] pci 0000:06:08.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    0.693257] pci 0000:06:08.0: setting latency timer to 64
[    0.693265] pci 0000:0c:00.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    0.693300] pci 0000:0c:00.0: setting latency timer to 64
[    0.693307] pci 0000:06:09.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.693340] pci 0000:06:09.0: setting latency timer to 64
[    0.693343] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
[    0.693344] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff]
[    0.693346] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
[    0.693347] pci_bus 0000:00: resource 7 [mem 0xc0000000-0xffffffff]
[    0.693349] pci_bus 0000:01: resource 0 [io  0xe000-0xefff]
[    0.693350] pci_bus 0000:01: resource 1 [mem 0xfe600000-0xfe6fffff]
[    0.693351] pci_bus 0000:01: resource 2 [mem 0xc0000000-0xcfffffff 64bit pref]
[    0.693353] pci_bus 0000:03: resource 1 [mem 0xfe500000-0xfe5fffff]
[    0.693354] pci_bus 0000:04: resource 1 [mem 0xfe400000-0xfe4fffff]
[    0.693356] pci_bus 0000:05: resource 0 [io  0xa000-0xdfff]
[    0.693357] pci_bus 0000:05: resource 1 [mem 0xfe000000-0xfe3fffff]
[    0.693358] pci_bus 0000:05: resource 2 [mem 0xd0000000-0xd00fffff 64bit pref]
[    0.693360] pci_bus 0000:06: resource 0 [io  0xa000-0xdfff]
[    0.693361] pci_bus 0000:06: resource 1 [mem 0xfe000000-0xfe2fffff]
[    0.693363] pci_bus 0000:06: resource 2 [mem 0xd0000000-0xd00fffff 64bit pref]
[    0.693364] pci_bus 0000:07: resource 0 [io  0xd000-0xdfff]
[    0.693365] pci_bus 0000:07: resource 1 [mem 0xfe200000-0xfe2fffff]
[    0.693367] pci_bus 0000:09: resource 0 [io  0xc000-0xcfff]
[    0.693368] pci_bus 0000:09: resource 1 [mem 0xfe100000-0xfe1fffff]
[    0.693370] pci_bus 0000:0a: resource 0 [io  0xb000-0xbfff]
[    0.693371] pci_bus 0000:0a: resource 1 [mem 0xfe000000-0xfe0fffff]
[    0.693372] pci_bus 0000:0e: resource 0 [io  0xa000-0xafff]
[    0.693374] pci_bus 0000:0e: resource 2 [mem 0xd0000000-0xd00fffff 64bit pref]
[    0.693392] NET: Registered protocol family 2
[    0.693573] IP route cache hash table entries: 262144 (order: 9, 2097152 bytes)
[    0.694257] TCP established hash table entries: 524288 (order: 11, 8388608 bytes)
[    0.695215] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[    0.695348] TCP: Hash tables configured (established 524288 bind 65536)
[    0.695378] TCP reno registered
[    0.695415] UDP hash table entries: 4096 (order: 5, 131072 bytes)
[    0.695469] UDP-Lite hash table entries: 4096 (order: 5, 131072 bytes)
[    0.695563] NET: Registered protocol family 1
[    0.952165] pci 0000:01:00.0: Boot video device
[    0.952245] PCI: CLS 64 bytes, default 64
[    0.952246] PCI-DMA: Using software bounce buffering for IO (SWIOTLB)
[    0.952278] Placing 64MB software IO TLB between ffff8800bafc3000 - ffff8800befc3000
[    0.952312] software IO TLB at phys 0xbafc3000 - 0xbefc3000
[    0.952600] audit: initializing netlink socket (disabled)
[    0.952634] type=2000 audit(1328145894.704:1): initialized
[    0.974025] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    0.987574] VFS: Disk quotas dquot_6.5.2
[    0.987635] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    0.987986] fuse init (API version 7.16)
[    0.988059] msgmni has been set to 15914
[    0.988283] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.988330] io scheduler noop registered
[    0.988359] io scheduler deadline registered
[    0.988406] io scheduler cfq registered (default)
[    0.988502] pcieport 0000:00:01.0: setting latency timer to 64
[    0.988520] pcieport 0000:00:01.0: irq 40 for MSI/MSI-X
[    0.988557] pcieport 0000:00:1c.0: setting latency timer to 64
[    0.988591] pcieport 0000:00:1c.0: irq 41 for MSI/MSI-X
[    0.988643] pcieport 0000:00:1c.4: setting latency timer to 64
[    0.988677] pcieport 0000:00:1c.4: irq 42 for MSI/MSI-X
[    0.988728] pcieport 0000:00:1c.6: setting latency timer to 64
[    0.988762] pcieport 0000:00:1c.6: irq 43 for MSI/MSI-X
[    0.988814] pcieport 0000:00:1c.7: setting latency timer to 64
[    0.988848] pcieport 0000:00:1c.7: irq 44 for MSI/MSI-X
[    0.988912] pcieport 0000:05:00.0: setting latency timer to 64
[    0.988972] pcieport 0000:05:00.0: irq 45 for MSI/MSI-X
[    0.989060] pcieport 0000:06:01.0: setting latency timer to 64
[    0.989120] pcieport 0000:06:01.0: irq 46 for MSI/MSI-X
[    0.989210] pcieport 0000:06:04.0: setting latency timer to 64
[    0.989269] pcieport 0000:06:04.0: irq 47 for MSI/MSI-X
[    0.989360] pcieport 0000:06:05.0: setting latency timer to 64
[    0.989420] pcieport 0000:06:05.0: irq 48 for MSI/MSI-X
[    0.989508] pcieport 0000:06:06.0: setting latency timer to 64
[    0.989568] pcieport 0000:06:06.0: irq 49 for MSI/MSI-X
[    0.989657] pcieport 0000:06:07.0: setting latency timer to 64
[    0.989717] pcieport 0000:06:07.0: irq 50 for MSI/MSI-X
[    0.989805] pcieport 0000:06:08.0: setting latency timer to 64
[    0.989864] pcieport 0000:06:08.0: irq 51 for MSI/MSI-X
[    0.989953] pcieport 0000:06:09.0: setting latency timer to 64
[    0.990013] pcieport 0000:06:09.0: irq 52 for MSI/MSI-X
[    0.990104] pcieport 0000:00:01.0: Signaling PME through PCIe PME interrupt
[    0.990135] pci 0000:01:00.0: Signaling PME through PCIe PME interrupt
[    0.990164] pci 0000:01:00.1: Signaling PME through PCIe PME interrupt
[    0.990194] pcie_pme 0000:00:01.0:pcie01: service driver pcie_pme loaded
[    0.990208] pcieport 0000:00:1c.0: Signaling PME through PCIe PME interrupt
[    0.990240] pcie_pme 0000:00:1c.0:pcie01: service driver pcie_pme loaded
[    0.990252] pcieport 0000:00:1c.4: Signaling PME through PCIe PME interrupt
[    0.990282] pci 0000:03:00.0: Signaling PME through PCIe PME interrupt
[    0.990313] pcie_pme 0000:00:1c.4:pcie01: service driver pcie_pme loaded
[    0.990326] pcieport 0000:00:1c.6: Signaling PME through PCIe PME interrupt
[    0.990356] pci 0000:04:00.0: Signaling PME through PCIe PME interrupt
[    0.990388] pcie_pme 0000:00:1c.6:pcie01: service driver pcie_pme loaded
[    0.990401] pcieport 0000:00:1c.7: Signaling PME through PCIe PME interrupt
[    0.990430] pcieport 0000:05:00.0: Signaling PME through PCIe PME interrupt
[    0.990460] pcieport 0000:06:01.0: Signaling PME through PCIe PME interrupt
[    0.990490] pci 0000:07:00.0: Signaling PME through PCIe PME interrupt
[    0.990519] pcieport 0000:06:04.0: Signaling PME through PCIe PME interrupt
[    0.990549] pcieport 0000:06:05.0: Signaling PME through PCIe PME interrupt
[    0.990578] pci 0000:09:00.0: Signaling PME through PCIe PME interrupt
[    0.990608] pcieport 0000:06:06.0: Signaling PME through PCIe PME interrupt
[    0.990637] pci 0000:0a:00.0: Signaling PME through PCIe PME interrupt
[    0.990667] pcieport 0000:06:07.0: Signaling PME through PCIe PME interrupt
[    0.990696] pcieport 0000:06:08.0: Signaling PME through PCIe PME interrupt
[    0.990726] pci 0000:0c:00.0: Signaling PME through PCIe PME interrupt
[    0.990755] pcieport 0000:06:09.0: Signaling PME through PCIe PME interrupt
[    0.990785] pci 0000:0e:00.0: Signaling PME through PCIe PME interrupt
[    0.990816] pcie_pme 0000:00:1c.7:pcie01: service driver pcie_pme loaded
[    0.990826] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.990867] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.990919] intel_idle: MWAIT substates: 0x1120
[    0.990920] intel_idle: v0.4 model 0x2A
[    0.990921] intel_idle: lapic_timer_reliable_states 0xffffffff
[    0.990983] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0
[    0.991020] ACPI: Power Button [PWRB]
[    0.991068] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
[    0.991103] ACPI: Power Button [PWRF]
[    0.991146] ACPI: acpi_idle yielding to intel_idle
[    0.992324] ERST: Table is not found!
[    0.992384] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    1.012757] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    1.062471] Freeing initrd memory: 19892k freed
[    1.204112] 00:08: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    1.204308] Linux agpgart interface v0.103
[    1.204943] brd: module loaded
[    1.205212] loop: module loaded
[    1.205459] Fixed MDIO Bus: probed
[    1.205497] PPP generic driver version 2.4.2
[    1.205542] tun: Universal TUN/TAP device driver, 1.6
[    1.205570] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    1.205638] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    1.205682] ehci_hcd 0000:00:1a.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    1.205725] ehci_hcd 0000:00:1a.0: setting latency timer to 64
[    1.205728] ehci_hcd 0000:00:1a.0: EHCI Host Controller
[    1.205775] ehci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 1
[    1.205830] ehci_hcd 0000:00:1a.0: debug port 2
[    1.209736] ehci_hcd 0000:00:1a.0: cache line size of 64 is not supported
[    1.209747] ehci_hcd 0000:00:1a.0: irq 23, io mem 0xfe727000
[    1.223605] ehci_hcd 0000:00:1a.0: USB 2.0 started, EHCI 1.00
[    1.223732] hub 1-0:1.0: USB hub found
[    1.223761] hub 1-0:1.0: 2 ports detected
[    1.223826] ehci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    1.223863] ehci_hcd 0000:00:1d.0: setting latency timer to 64
[    1.223865] ehci_hcd 0000:00:1d.0: EHCI Host Controller
[    1.223910] ehci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    1.223959] ehci_hcd 0000:00:1d.0: debug port 2
[    1.227857] ehci_hcd 0000:00:1d.0: cache line size of 64 is not supported
[    1.227860] ehci_hcd 0000:00:1d.0: irq 23, io mem 0xfe726000
[    1.243564] ehci_hcd 0000:00:1d.0: USB 2.0 started, EHCI 1.00
[    1.243681] hub 2-0:1.0: USB hub found
[    1.243711] hub 2-0:1.0: 2 ports detected
[    1.243771] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    1.243805] uhci_hcd: USB Universal Host Controller Interface driver
[    1.243864] i8042: PNP: No PS/2 controller found. Probing ports directly.
[    1.246653] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.246684] serio: i8042 AUX port at 0x60,0x64 irq 12
[    1.246763] mousedev: PS/2 mouse device common for all mice
[    1.246852] rtc_cmos 00:04: RTC can wake from S4
[    1.246950] rtc_cmos 00:04: rtc core: registered rtc_cmos as rtc0
[    1.247002] rtc0: alarms up to one month, y3k, 114 bytes nvram, hpet irqs
[    1.247083] device-mapper: uevent: version 1.0.3
[    1.247147] device-mapper: ioctl: 4.20.0-ioctl (2011-02-02) initialised: dm-devel@redhat.com
[    1.247235] cpuidle: using governor ladder
[    1.247341] cpuidle: using governor menu
[    1.247369] EFI Variables Facility v0.08 2004-May-17
[    1.247512] TCP cubic registered
[    1.247613] NET: Registered protocol family 10
[    1.247870] NET: Registered protocol family 17
[    1.247906] Registering the dns_resolver key type
[    1.247979] PM: Hibernation image not present or could not be loaded.
[    1.247986] registered taskstats version 1
[    1.259239]   Magic number: 0:600:406
[    1.259367] rtc_cmos 00:04: setting system clock to 2012-02-02 01:24:55 UTC (1328145895)
[    1.259974] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.260002] EDD information not available.
[    1.260929] Freeing unused kernel memory: 988k freed
[    1.261021] Write protecting the kernel read-only data: 12288k
[    1.264469] Freeing unused kernel memory: 2036k freed
[    1.266935] Freeing unused kernel memory: 1388k freed
[    1.276599] udevd[88]: starting version 173
[    1.286395] ahci 0000:00:1f.2: version 3.0
[    1.286409] ahci 0000:00:1f.2: PCI INT B -> GSI 20 (level, low) -> IRQ 20
[    1.286468] ahci 0000:00:1f.2: irq 53 for MSI/MSI-X
[    1.288714] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    1.288757] r8169 0000:0e:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.288825] r8169 0000:0e:00.0: setting latency timer to 64
[    1.288897] r8169 0000:0e:00.0: irq 54 for MSI/MSI-X
[    1.289100] r8169 0000:0e:00.0: eth0: RTL8168e/8111e at 0xffffc90000c6c000, f4:6d:04:99:f7:42, XID 0c200000 IRQ 54
[    1.291215] xhci_hcd 0000:03:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.291260] xhci_hcd 0000:03:00.0: setting latency timer to 64
[    1.291264] xhci_hcd 0000:03:00.0: xHCI Host Controller
[    1.291320] xhci_hcd 0000:03:00.0: new USB bus registered, assigned bus number 3
[    1.291689] xhci_hcd 0000:03:00.0: irq 16, io mem 0xfe500000
[    1.291775] xhci_hcd 0000:03:00.0: irq 55 for MSI/MSI-X
[    1.291778] xhci_hcd 0000:03:00.0: irq 56 for MSI/MSI-X
[    1.291780] xhci_hcd 0000:03:00.0: irq 57 for MSI/MSI-X
[    1.291782] xhci_hcd 0000:03:00.0: irq 58 for MSI/MSI-X
[    1.291784] xhci_hcd 0000:03:00.0: irq 59 for MSI/MSI-X
[    1.291897] xHCI xhci_add_endpoint called for root hub
[    1.291898] xHCI xhci_check_bandwidth called for root hub
[    1.291912] hub 3-0:1.0: USB hub found
[    1.291945] hub 3-0:1.0: 2 ports detected
[    1.292011] xhci_hcd 0000:03:00.0: xHCI Host Controller
[    1.292055] xhci_hcd 0000:03:00.0: new USB bus registered, assigned bus number 4
[    1.293880] e1000e: Intel(R) PRO/1000 Network Driver - 1.3.10-k2
[    1.293933] e1000e: Copyright(c) 1999 - 2011 Intel Corporation.
[    1.295150] xHCI xhci_add_endpoint called for root hub
[    1.295151] xHCI xhci_check_bandwidth called for root hub
[    1.295174] hub 4-0:1.0: USB hub found
[    1.295207] hub 4-0:1.0: 2 ports detected
[    1.295278] xhci_hcd 0000:04:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    1.295325] xhci_hcd 0000:04:00.0: setting latency timer to 64
[    1.295328] xhci_hcd 0000:04:00.0: xHCI Host Controller
[    1.295375] xhci_hcd 0000:04:00.0: new USB bus registered, assigned bus number 5
[    1.295563] xhci_hcd 0000:04:00.0: irq 18, io mem 0xfe400000
[    1.295646] xhci_hcd 0000:04:00.0: irq 60 for MSI/MSI-X
[    1.295648] xhci_hcd 0000:04:00.0: irq 61 for MSI/MSI-X
[    1.295650] xhci_hcd 0000:04:00.0: irq 62 for MSI/MSI-X
[    1.295653] xhci_hcd 0000:04:00.0: irq 63 for MSI/MSI-X
[    1.295656] xhci_hcd 0000:04:00.0: irq 64 for MSI/MSI-X
[    1.295758] xHCI xhci_add_endpoint called for root hub
[    1.295759] xHCI xhci_check_bandwidth called for root hub
[    1.295771] hub 5-0:1.0: USB hub found
[    1.295803] hub 5-0:1.0: 2 ports detected
[    1.295865] xhci_hcd 0000:04:00.0: xHCI Host Controller
[    1.295970] xhci_hcd 0000:04:00.0: new USB bus registered, assigned bus number 6
[    1.297069] wmi: Mapper loaded
[    1.299086] xHCI xhci_add_endpoint called for root hub
[    1.299087] xHCI xhci_check_bandwidth called for root hub
[    1.299102] hub 6-0:1.0: USB hub found
[    1.299135] hub 6-0:1.0: 2 ports detected
[    1.299544] ahci 0000:00:1f.2: AHCI 0001.0300 32 slots 6 ports 6 Gbps 0x30 impl SATA mode
[    1.299579] ahci 0000:00:1f.2: flags: 64bit ncq sntf pm led clo pio slum part ems apst 
[    1.299614] ahci 0000:00:1f.2: setting latency timer to 64
[    1.302578] firewire_ohci 0000:07:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.302619] firewire_ohci 0000:07:00.0: setting latency timer to 64
[    1.307737] scsi0 : ahci
[    1.307824] scsi1 : ahci
[    1.307890] scsi2 : ahci
[    1.307948] scsi3 : ahci
[    1.308023] scsi4 : ahci
[    1.308080] scsi5 : ahci
[    1.308175] ata1: DUMMY
[    1.308201] ata2: DUMMY
[    1.308226] ata3: DUMMY
[    1.308251] ata4: DUMMY
[    1.308278] ata5: SATA max UDMA/133 abar m2048@0xfe725000 port 0xfe725300 irq 53
[    1.308310] ata6: SATA max UDMA/133 abar m2048@0xfe725000 port 0xfe725380 irq 53
[    1.308359] e1000e 0000:00:19.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    1.308365] ahci 0000:09:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.308442] e1000e 0000:00:19.0: setting latency timer to 64
[    1.308538] ahci 0000:09:00.0: AHCI 0001.0100 32 slots 2 ports 3 Gbps 0x3 impl SATA mode
[    1.308563] e1000e 0000:00:19.0: irq 65 for MSI/MSI-X
[    1.308583] ahci 0000:09:00.0: flags: 64bit ncq pm led clo pmp pio slum part 
[    1.308617] ahci 0000:09:00.0: setting latency timer to 64
[    1.308766] scsi6 : ahci
[    1.308824] scsi7 : ahci
[    1.308887] ata7: SATA max UDMA/133 abar m512@0xfe110000 port 0xfe110100 irq 16
[    1.308922] ata8: SATA max UDMA/133 abar m512@0xfe110000 port 0xfe110180 irq 16
[    1.308964] ahci 0000:0a:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    1.309076] ahci 0000:0a:00.0: irq 66 for MSI/MSI-X
[    1.323543] ahci 0000:0a:00.0: AHCI 0001.0200 32 slots 8 ports 6 Gbps 0xff impl SATA mode
[    1.323576] ahci 0000:0a:00.0: flags: 64bit ncq pio 
[    1.323607] ahci 0000:0a:00.0: setting latency timer to 64
[    1.324145] scsi8 : ahci
[    1.324306] scsi9 : ahci
[    1.324421] scsi10 : ahci
[    1.324536] scsi11 : ahci
[    1.324651] scsi12 : ahci
[    1.325328] scsi13 : ahci
[    1.325442] scsi14 : ahci
[    1.325546] scsi15 : ahci
[    1.325597] ata9: SATA max UDMA/133 abar m2048@0xfe021000 port 0xfe021100 irq 66
[    1.325631] ata10: SATA max UDMA/133 abar m2048@0xfe021000 port 0xfe021180 irq 66
[    1.325665] ata11: SATA max UDMA/133 abar m2048@0xfe021000 port 0xfe021200 irq 66
[    1.325698] ata12: SATA max UDMA/133 abar m2048@0xfe021000 port 0xfe021280 irq 66
[    1.325731] ata13: SATA max UDMA/133 abar m2048@0xfe021000 port 0xfe021300 irq 66
[    1.325765] ata14: SATA max UDMA/133 abar m2048@0xfe021000 port 0xfe021380 irq 66
[    1.325798] ata15: SATA max UDMA/133 abar m2048@0xfe021000 port 0xfe021400 irq 66
[    1.325831] ata16: SATA max UDMA/133 abar m2048@0xfe021000 port 0xfe021480 irq 66
[    1.363445] firewire_ohci: Added fw-ohci device 0000:07:00.0, OHCI v1.10, 4 IR + 8 IT contexts, quirks 0x11
[    1.535023] usb 1-1: new high speed USB device number 2 using ehci_hcd
[    1.621668] e1000e 0000:00:19.0: eth1: (PCI Express:2.5GT/s:Width x1) f4:6d:04:9a:1d:d5
[    1.621702] e1000e 0000:00:19.0: eth1: Intel(R) PRO/1000 Network Connection
[    1.621757] e1000e 0000:00:19.0: eth1: MAC: 10, PHY: 11, PBA No: FFFFFF-0FF
[    1.626860] ata5: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    1.626888] ata8: SATA link down (SStatus 0 SControl 300)
[    1.626962] ata7: SATA link down (SStatus 0 SControl 300)
[    1.627059] ata6: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    1.627854] ata6.00: ATA-8: ST2000DL003-9VT166, CC32, max UDMA/133
[    1.627896] ata6.00: 3907029168 sectors, multi 16: LBA48 NCQ (depth 31/32)
[    1.627945] ata5.00: ATA-8: ST2000DL003-9VT166, CC32, max UDMA/133
[    1.627972] ata5.00: 3907029168 sectors, multi 16: LBA48 NCQ (depth 31/32)
[    1.628820] ata6.00: configured for UDMA/133
[    1.628871] ata5.00: configured for UDMA/133
[    1.629054] scsi 4:0:0:0: Direct-Access     ATA      ST2000DL003-9VT1 CC32 PQ: 0 ANSI: 5
[    1.629156] sd 4:0:0:0: Attached scsi generic sg0 type 0
[    1.629338] sd 4:0:0:0: [sda] 3907029168 512-byte logical blocks: (2.00 TB/1.81 TiB)
[    1.629378] scsi 5:0:0:0: Direct-Access     ATA      ST2000DL003-9VT1 CC32 PQ: 0 ANSI: 5
[    1.629472] sd 5:0:0:0: Attached scsi generic sg1 type 0
[    1.629568] sd 4:0:0:0: [sda] Write Protect is off
[    1.629572] sd 5:0:0:0: [sdb] 3907029168 512-byte logical blocks: (2.00 TB/1.81 TiB)
[    1.629604] sd 5:0:0:0: [sdb] Write Protect is off
[    1.629606] sd 5:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[    1.629672] sd 5:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.629712] sd 4:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.629817] sd 4:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.650522]  sda: sda1
[    1.650781] ata15: SATA link down (SStatus 0 SControl 300)
[    1.650842] ata14: SATA link down (SStatus 0 SControl 300)
[    1.650906] ata12: SATA link down (SStatus 0 SControl 300)
[    1.650966] ata11: SATA link down (SStatus 0 SControl 300)
[    1.651025] ata10: SATA link down (SStatus 0 SControl 300)
[    1.651088] ata16: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    1.651147] ata9: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    1.651152] sd 4:0:0:0: [sda] Attached SCSI disk
[    1.651255] ata13: SATA link down (SStatus 0 SControl 300)
[    1.651297] ata16.00: ATAPI: MARVELL VIRTUALL, 1.09, max UDMA/66
[    1.651579] ata16.00: configured for UDMA/66
[    1.655665]  sdb: sdb1
[    1.656017] sd 5:0:0:0: [sdb] Attached SCSI disk
[    1.662837] ata9.00: ATA-8: MKNSSDCL40GB-DX, 360A13F0, max UDMA/133
[    1.662879] ata9.00: 78161328 sectors, multi 1: LBA48 NCQ (depth 31/32), AA
[    1.667423] hub 1-1:1.0: USB hub found
[    1.667520] hub 1-1:1.0: 6 ports detected
[    1.672828] ata9.00: configured for UDMA/133
[    1.673003] scsi 8:0:0:0: Direct-Access     ATA      MKNSSDCL40GB-DX  360A PQ: 0 ANSI: 5
[    1.673106] sd 8:0:0:0: Attached scsi generic sg2 type 0
[    1.673162] sd 8:0:0:0: [sdc] 78161328 512-byte logical blocks: (40.0 GB/37.2 GiB)
[    1.673402] scsi 15:0:0:0: Processor         Marvell  91xx Config      1.01 PQ: 0 ANSI: 5
[    1.673405] sd 8:0:0:0: [sdc] Write Protect is off
[    1.673407] sd 8:0:0:0: [sdc] Mode Sense: 00 3a 00 00
[    1.673451] sd 8:0:0:0: [sdc] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.673591] scsi 15:0:0:0: Attached scsi generic sg3 type 3
[    1.674172]  sdc: sdc1 sdc2 < sdc5 sdc6 >
[    1.674446] sd 8:0:0:0: [sdc] Attached SCSI disk
[    1.786484] usb 2-1: new high speed USB device number 2 using ehci_hcd
[    1.817869] md: bind<sda>
[    1.870409] firewire_core: created device fw0: GUID 001e8c0000461692, S400
[    1.922752] hub 2-1:1.0: USB hub found
[    1.922861] hub 2-1:1.0: 8 ports detected
[    1.950164] Refined TSC clocksource calibration: 3193.583 MHz.
[    1.950207] Switching to clocksource tsc
[    1.988586] md: bind<sdb>
[    1.989780] md: raid1 personality registered for level 1
[    1.989866] bio: create slab <bio-1> at 1
[    1.989920] md/raid1:md0: active with 2 out of 2 mirrors
[    1.989955] md0: detected capacity change from 0 to 2000397746176
[    2.020061]  md0: unknown partition table
[    2.193885] usb 2-1.2: new low speed USB device number 3 using ehci_hcd
[    2.298401] input: Dell Dell USB Keyboard as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.2/2-1.2:1.0/input/input2
[    2.298475] generic-usb 0003:413C:2003.0001: input,hidraw0: USB HID v1.10 Keyboard [Dell Dell USB Keyboard] on usb-0000:00:1d.0-1.2/input0
[    2.298516] usbcore: registered new interface driver usbhid
[    2.298543] usbhid: USB HID core driver
[    2.365538] usb 2-1.3: new low speed USB device number 4 using ehci_hcd
[    2.467562] input: Dell Dell USB Mouse as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.3/2-1.3:1.0/input/input3
[    2.467640] generic-usb 0003:413C:3200.0002: input,hidraw1: USB HID v1.10 Mouse [Dell Dell USB Mouse] on usb-0000:00:1d.0-1.3/input0
[    2.537192] usb 2-1.7: new full speed USB device number 5 using ehci_hcd
[    3.448649] Btrfs loaded
[    3.451199] xor: automatically using best checksumming function: generic_sse
[    3.471081]    generic_sse: 17430.000 MB/sec
[    3.471092] xor: using function: generic_sse (17430.000 MB/sec)
[    3.471509] device-mapper: dm-raid45: initialized v0.2594b
[    3.472464] md: linear personality registered for level -1
[    3.473355] md: multipath personality registered for level -4
[    3.474114] md: raid0 personality registered for level 0
[    3.475580] async_tx: api initialized (async)
[    3.542957] raid6: int64x1   3775 MB/s
[    3.610800] raid6: int64x2   4701 MB/s
[    3.678673] raid6: int64x4   4028 MB/s
[    3.746553] raid6: int64x8   3186 MB/s
[    3.814390] raid6: sse2x1   10525 MB/s
[    3.882265] raid6: sse2x2   12876 MB/s
[    3.950120] raid6: sse2x4   14918 MB/s
[    3.950131] raid6: using algorithm sse2x4 (14918 MB/s)
[    3.950963] md: raid6 personality registered for level 6
[    3.950970] md: raid5 personality registered for level 5
[    3.950982] md: raid4 personality registered for level 4
[    3.953423] md: raid10 personality registered for level 10
[    4.188362] EXT4-fs (sdc1): mounted filesystem with ordered data mode. Opts: (null)
[    4.593753] udevd[493]: starting version 173
[    9.881107] lp: driver loaded but no devices found
[   11.162295] Adding 7811068k swap on /dev/sdc5.  Priority:-1 extents:1 across:7811068k SS
[   11.166705] bonding: Ethernet Channel Bonding Driver: v3.7.1 (April 27, 2011)
[   11.166708] bonding: MII link monitoring set to 100 ms
[   11.203749] mei: module is from the staging directory, the quality is unknown, you have been warned.
[   11.203943] mei 0000:00:16.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[   11.203947] mei 0000:00:16.0: setting latency timer to 64
[   11.212981] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
[   11.212983] Disabling lock debugging due to kernel taint
[   11.226163] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   11.228370] type=1400 audit(1328145905.485:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=694 comm="apparmor_parser"
[   11.228578] type=1400 audit(1328145905.485:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=694 comm="apparmor_parser"
[   11.228709] type=1400 audit(1328145905.485:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=694 comm="apparmor_parser"
[   11.228931] type=1400 audit(1328145905.485:5): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=695 comm="apparmor_parser"
[   11.229138] type=1400 audit(1328145905.485:6): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=695 comm="apparmor_parser"
[   11.229268] type=1400 audit(1328145905.485:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=695 comm="apparmor_parser"
[   11.232768] EXT4-fs (sdc1): re-mounted. Opts: errors=remount-ro
[   11.255195] [fglrx] Maximum main memory to use for locked dma buffers: 7747 MBytes.
[   11.256159] Bluetooth: Core ver 2.16
[   11.256170] NET: Registered protocol family 31
[   11.256171] Bluetooth: HCI device and connection manager initialized
[   11.256172] Bluetooth: HCI socket layer initialized
[   11.256173] Bluetooth: L2CAP socket layer initialized
[   11.256243] [fglrx]   vendor: 1002 device: 9552 count: 1
[   11.256526] [fglrx] ioport: bar 4, base 0xe000, size: 0x100
[   11.256533] pci 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   11.256536] pci 0000:01:00.0: setting latency timer to 64
[   11.256699] [fglrx] Kernel PAT support is enabled
[   11.256709] [fglrx] module loaded - fglrx 8.88.7 [Jul 28 2011] with 1 minors
[   11.258648] Bluetooth: SCO socket layer initialized
[   11.259367] EXT4-fs (sdc6): mounted filesystem with ordered data mode. Opts: (null)
[   11.261798] Bluetooth: Generic Bluetooth USB driver ver 0.6
[   11.264187] usbcore: registered new interface driver btusb
[   11.283266] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[   11.283312] HDA Intel 0000:00:1b.0: irq 67 for MSI/MSI-X
[   11.283332] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   11.287291] asus_wmi: ASUS WMI generic driver loaded
[   11.293738] ADDRCONF(NETDEV_UP): bond0: link is not ready
[   11.294021] asus_wmi: Initialization: 0x0
[   11.294035] asus_wmi: BIOS WMI version: 0.9
[   11.294057] asus_wmi: SFUN value: 0x0
[   11.294348] input: Eee PC WMI hotkeys as /devices/platform/eeepc-wmi/input/input4
[   11.299891] RPC: Registered named UNIX socket transport module.
[   11.299893] RPC: Registered udp transport module.
[   11.299894] RPC: Registered tcp transport module.
[   11.299895] RPC: Registered tcp NFSv4.1 backchannel transport module.
[   11.310792] FS-Cache: Loaded
[   11.319967] FS-Cache: Netfs 'nfs' registered for caching
[   11.327735] hda_codec: ALC889: BIOS auto-probing.
[   11.331666] Installing knfsd (copyright (C) 1996 okir@monad.swb.de).
[   11.333259] input: HDA Intel PCH Headphone as /devices/pci0000:00/0000:00:1b.0/sound/card0/input5
[   11.333322] HDA Intel 0000:01:00.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[   11.333377] HDA Intel 0000:01:00.1: irq 68 for MSI/MSI-X
[   11.333393] HDA Intel 0000:01:00.1: setting latency timer to 64
[   11.359891] HDMI status: Pin=3 Presence_Detect=0 ELD_Valid=0
[   11.360013] input: HDA ATI HDMI HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:01.0/0000:01:00.1/sound/card1/input6
[   11.454798] r8169 0000:0e:00.0: eth0: link down
[   11.454803] r8169 0000:0e:00.0: eth0: link down
[   11.455846] bonding: bond0: enslaving eth0 as an active interface with a down link.
[   11.604329] e1000e 0000:00:19.0: irq 65 for MSI/MSI-X
[   11.630369] ppdev: user-space parallel port driver
[   11.637139] type=1400 audit(1328145905.893:8): apparmor="STATUS" operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" pid=1187 comm="apparmor_parser"
[   11.637381] type=1400 audit(1328145905.893:9): apparmor="STATUS" operation="profile_load" name="/usr/sbin/cupsd" pid=1187 comm="apparmor_parser"
[   11.658725] e1000e 0000:00:19.0: irq 65 for MSI/MSI-X
[   11.659142] bonding: bond0: enslaving eth1 as an active interface with a down link.
[   11.659720] init: udev-fallback-graphics main process (1163) terminated with status 1
[   13.835890] r8169 0000:0e:00.0: eth0: link up
[   13.886957] bonding: bond0: link status definitely up for interface eth0, 1000 Mbps full duplex.
[   13.887235] ADDRCONF(NETDEV_CHANGE): bond0: link becomes ready
[   15.260273] e1000e: eth1 NIC Link is Up 1000 Mbps Full Duplex, Flow Control: None
[   15.283368] bonding: bond0: link status definitely up for interface eth1, 1000 Mbps full duplex.
[   17.918961] init: ssh main process (1006) terminated with status 255
[   17.960274] init: failsafe main process (981) killed by TERM signal
[   17.977362] type=1400 audit(1328145912.245:10): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=1298 comm="apparmor_parser"
[   17.977577] type=1400 audit(1328145912.245:11): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=1298 comm="apparmor_parser"
[   17.977708] type=1400 audit(1328145912.245:12): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=1298 comm="apparmor_parser"
[   17.978403] type=1400 audit(1328145912.249:13): apparmor="STATUS" operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" pid=1296 comm="apparmor_parser"
[   17.978683] type=1400 audit(1328145912.249:14): apparmor="STATUS" operation="profile_load" name="/usr/lib/lightdm/lightdm-guest-session-wrapper" pid=1297 comm="apparmor_parser"
[   17.979847] type=1400 audit(1328145912.249:15): apparmor="STATUS" operation="profile_replace" name="/usr/lib/cups/backend/cups-pdf" pid=1302 comm="apparmor_parser"
[   17.980102] type=1400 audit(1328145912.249:16): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/cupsd" pid=1302 comm="apparmor_parser"
[   17.981021] type=1400 audit(1328145912.249:17): apparmor="STATUS" operation="profile_load" name="/usr/sbin/mysqld" pid=1303 comm="apparmor_parser"
[   17.981511] type=1400 audit(1328145912.249:18): apparmor="STATUS" operation="profile_load" name="/usr/lib/telepathy/mission-control-5" pid=1301 comm="apparmor_parser"
[   17.981747] type=1400 audit(1328145912.249:19): apparmor="STATUS" operation="profile_load" name="/usr/lib/telepathy/telepathy-*" pid=1301 comm="apparmor_parser"
[   18.030900] init: apport pre-start process (1335) terminated with status 1
[   18.035459] init: apport post-stop process (1371) terminated with status 1
[   18.052301] init: oem-config main process (1356) killed by TERM signal
[   18.052502] init: lightdm main process (1345) killed by TERM signal
[   18.056942] init: gdm main process (1416) killed by TERM signal
[   18.079048] NFSD: Using /var/lib/nfs/v4recovery as the NFSv4 state recovery directory
[   18.079311] NFSD: starting 90-second grace period
[   24.420991] bond0: no IPv6 routers present
[   80.393861] Bluetooth: RFCOMM TTY layer initialized
[   80.393863] Bluetooth: RFCOMM socket layer initialized
[   80.393864] Bluetooth: RFCOMM ver 1.11
[   80.394951] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   80.394952] Bluetooth: BNEP filters: protocol multicast
[   80.598874] EXT4-fs (sdc1): re-mounted. Opts: errors=remount-ro,commit=0
[   80.600296] EXT4-fs (sdc6): re-mounted. Opts: commit=0
[   83.445574] vga16fb: initializing
[   83.445576] vga16fb: mapped to 0xffff8800000a0000
[   83.555576] Console: switching to colour frame buffer device 80x30
[   83.557661] fb0: VGA16 VGA frame buffer device
[   83.657349] do_trap: 15 callbacks suppressed
[   83.657351] bterm[2247] trap stack segment ip:404349 sp:7fff68e27518 error:0
[   84.641453] bterm[2263] trap stack segment ip:404349 sp:7fffba97f498 error:0
[   85.611460] bterm[2276] trap stack segment ip:404349 sp:7ffffebc15d8 error:0
[   86.661349] bterm[2289] trap stack segment ip:404349 sp:7fffd7529c18 error:0
[   87.675342] bterm[2302] trap stack segment ip:404349 sp:7fff2417b068 error:0
[  176.231390] EXT3-fs: barriers not enabled
[  176.263560] kjournald starting.  Commit interval 5 seconds
[  176.263789] EXT3-fs (md0): warning: checktime reached, running e2fsck is recommended
[  176.303599] EXT3-fs (md0): using internal journal
[  176.303605] EXT3-fs (md0): mounted filesystem with ordered data mode
[53473.149580] usb 3-2: new high speed USB device number 2 using xhci_hcd
[53473.168030] xhci_hcd 0000:03:00.0: WARN: short transfer on control ep
[53473.168529] xhci_hcd 0000:03:00.0: WARN: short transfer on control ep
[53473.169013] xhci_hcd 0000:03:00.0: WARN: short transfer on control ep
[53473.169493] xhci_hcd 0000:03:00.0: WARN: short transfer on control ep
[53473.302012] usbcore: registered new interface driver uas
[53473.304102] Initializing USB Mass Storage driver...
[53473.304179] usbcore: registered new interface driver usb-storage
[53473.304181] USB Mass Storage support registered.
[53473.304902] scsi16 : usb-storage 3-2:1.0
[53473.305004] usbcore: registered new interface driver ums-cypress
[53474.301822] scsi 16:0:0:0: Direct-Access     WDC WD25 00JB-00REA0      0000 PQ: 0 ANSI: 0
[53474.327450] sd 16:0:0:0: Attached scsi generic sg4 type 0
[53474.327835] sd 16:0:0:0: [sdd] 488397168 512-byte logical blocks: (250 GB/232 GiB)
[53474.329266] sd 16:0:0:0: [sdd] Write Protect is off
[53474.329271] sd 16:0:0:0: [sdd] Mode Sense: 27 00 00 00
[53474.330051] sd 16:0:0:0: [sdd] No Caching mode page present
[53474.330059] sd 16:0:0:0: [sdd] Assuming drive cache: write through
[53474.332221] sd 16:0:0:0: [sdd] No Caching mode page present
[53474.332228] sd 16:0:0:0: [sdd] Assuming drive cache: write through
[53474.338119]  sdd: sdd1
[53474.340242] sd 16:0:0:0: [sdd] No Caching mode page present
[53474.340249] sd 16:0:0:0: [sdd] Assuming drive cache: write through
[53474.340253] sd 16:0:0:0: [sdd] Attached SCSI disk
[53610.527029] EXT3-fs: barriers not enabled
[53610.541662] kjournald starting.  Commit interval 5 seconds
[53610.541756] EXT3-fs (sdd1): warning: checktime reached, running e2fsck is recommended
[53610.542360] EXT3-fs (sdd1): using internal journal
[53610.542366] EXT3-fs (sdd1): mounted filesystem with ordered data mode

```Here is lsb_release -a
```
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 11.10
Release:        11.10
Codename:       oneiric

```uname -a 
```
Linux ubuntu-serv 3.0.0-15-generic #26-Ubuntu SMP Fri Jan 20 17:23:00 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux
```

---

