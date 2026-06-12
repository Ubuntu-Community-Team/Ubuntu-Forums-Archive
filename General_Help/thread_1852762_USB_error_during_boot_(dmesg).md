---
title: "USB error during boot (dmesg)"
date: 2011-09-30
forum: General Help
---

### Post by pqwoerituytrueiwoq on 2011-09-30
in addition to eating boot time i think is results in my key board not working after coming out of sleep mode

Boot Chart:
[[IMG]http://i.imgur.com/GXVVas.jpg[/IMG]]("http://i.imgur.com/GXVVa.png")
Dmesg: (look at ***[   12.031850]*** )
```
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.32-34-generic (buildd@yellow) (gcc version 4.4.3 (Ubuntu 4.4.3-4ubuntu5) ) #77-Ubuntu SMP Tue Sep 13 19:39:17 UTC 2011 (Ubuntu 2.6.32-34.77-generic 2.6.32.44+drm33.19)
[    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-2.6.32-34-generic root=UUID=8497a121-ebea-42e5-af82-8b15ad546005 ro quiet splash nomodeset video=uvesafb:mode_option=1152x864-24,mtrr=3,scroll=ywrap
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   Centaur CentaurHauls
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f000 (usable)
[    0.000000]  BIOS-e820: 000000000009f000 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e4000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 00000000cfe90000 (usable)
[    0.000000]  BIOS-e820: 00000000cfe90000 - 00000000cfea8000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000cfea8000 - 00000000cfed0000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000cfed0000 - 00000000cff00000 (reserved)
[    0.000000]  BIOS-e820: 00000000fff00000 - 0000000100000000 (reserved)
[    0.000000]  BIOS-e820: 0000000100000000 - 0000000120000000 (usable)
[    0.000000] DMI present.
[    0.000000] AMI BIOS detected: BIOS may corrupt low RAM, working around it.
[    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
[    0.000000] last_pfn = 0x120000 max_arch_pfn = 0x400000000
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
[    0.000000] last_pfn = 0xcfe90 max_arch_pfn = 0x400000000
[    0.000000] Scanning 0 areas for low memory corruption
[    0.000000] modified physical RAM map:
[    0.000000]  modified: 0000000000000000 - 0000000000010000 (reserved)
[    0.000000]  modified: 0000000000010000 - 000000000009f000 (usable)
[    0.000000]  modified: 000000000009f000 - 00000000000a0000 (reserved)
[    0.000000]  modified: 00000000000e4000 - 0000000000100000 (reserved)
[    0.000000]  modified: 0000000000100000 - 00000000cfe90000 (usable)
[    0.000000]  modified: 00000000cfe90000 - 00000000cfea8000 (ACPI data)
[    0.000000]  modified: 00000000cfea8000 - 00000000cfed0000 (ACPI NVS)
[    0.000000]  modified: 00000000cfed0000 - 00000000cff00000 (reserved)
[    0.000000]  modified: 00000000fff00000 - 0000000100000000 (reserved)
[    0.000000]  modified: 0000000100000000 - 0000000120000000 (usable)
[    0.000000] initial memory mapped : 0 - 20000000
[    0.000000] Using GB pages for direct mapping
[    0.000000] init_memory_mapping: 0000000000000000-00000000cfe90000
[    0.000000] NX (Execute Disable) protection: active
[    0.000000]  0000000000 - 00c0000000 page 1G
[    0.000000]  00c0000000 - 00cfe00000 page 2M
[    0.000000]  00cfe00000 - 00cfe90000 page 4k
[    0.000000] kernel direct mapping tables up to cfe90000 @ 10000-13000
[    0.000000] init_memory_mapping: 0000000100000000-0000000120000000
[    0.000000] NX (Execute Disable) protection: active
[    0.000000]  0100000000 - 0120000000 page 2M
[    0.000000] kernel direct mapping tables up to 120000000 @ 12000-14000
[    0.000000] RAMDISK: 3730b000 - 37fef30f
[    0.000000] ACPI: RSDP 00000000000fb470 00024 (v02 ACPIAM)
[    0.000000] ACPI: XSDT 00000000cfe90100 0005C (v01 082410 XSDT1744 20100824 MSFT 00000097)
[    0.000000] ACPI: FACP 00000000cfe90290 000F4 (v03 082410 FACP1744 20100824 MSFT 00000097)
[    0.000000] ACPI Warning: Optional field Pm2ControlBlock has zero address or length: 0000000000000000/1 (20090903/tbfadt-557)
[    0.000000] ACPI: DSDT 00000000cfe90450 0D9D3 (v01  A1501 A1501001 00000001 INTL 20060113)
[    0.000000] ACPI: FACS 00000000cfea8000 00040
[    0.000000] ACPI: APIC 00000000cfe90390 0007C (v01 082410 APIC1744 20100824 MSFT 00000097)
[    0.000000] ACPI: MCFG 00000000cfe90410 0003C (v01 082410 OEMMCFG  20100824 MSFT 00000097)
[    0.000000] ACPI: OEMB 00000000cfea8040 00072 (v01 082410 OEMB1744 20100824 MSFT 00000097)
[    0.000000] ACPI: SRAT 00000000cfe9f450 000C8 (v01 AMD    FAM_F_10 00000002 AMD  00000001)
[    0.000000] ACPI: HPET 00000000cfe9f520 00038 (v01 082410 OEMHPET  20100824 MSFT 00000097)
[    0.000000] ACPI: SSDT 00000000cfe9f560 00458 (v01 A M I  POWERNOW 00000001 AMD  00000001)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] SRAT: PXM 0 -> APIC 0 -> Node 0
[    0.000000] SRAT: PXM 0 -> APIC 1 -> Node 0
[    0.000000] SRAT: Node 0 PXM 0 0-a0000
[    0.000000] SRAT: Node 0 PXM 0 100000-d0000000
[    0.000000] SRAT: Node 0 PXM 0 100000000-130000000
[    0.000000] NUMA: Allocated memnodemap from 13000 - 15640
[    0.000000] NUMA: Using 20 for the hash shift.
[    0.000000] Bootmem setup node 0 0000000000000000-0000000120000000
[    0.000000]   NODE_DATA [0000000000015640 - 000000000001a63f]
[    0.000000]   bootmap [000000000001b000 -  000000000003efff] pages 24
[    0.000000] (9 early reservations) ==> bootmem [0000000000 - 0120000000]
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
[    0.000000]   #1 [0000006000 - 0000008000]       TRAMPOLINE ==> [0000006000 - 0000008000]
[    0.000000]   #2 [0001000000 - 0001a30aa4]    TEXT DATA BSS ==> [0001000000 - 0001a30aa4]
[    0.000000]   #3 [003730b000 - 0037fef30f]          RAMDISK ==> [003730b000 - 0037fef30f]
[    0.000000]   #4 [000009f000 - 0000100000]    BIOS reserved ==> [000009f000 - 0000100000]
[    0.000000]   #5 [0001a31000 - 0001a31350]              BRK ==> [0001a31000 - 0001a31350]
[    0.000000]   #6 [0000010000 - 0000012000]          PGTABLE ==> [0000010000 - 0000012000]
[    0.000000]   #7 [0000012000 - 0000013000]          PGTABLE ==> [0000012000 - 0000013000]
[    0.000000]   #8 [0000013000 - 0000015640]       MEMNODEMAP ==> [0000013000 - 0000015640]
[    0.000000] found SMP MP-table at [ffff8800000ff780] ff780
[    0.000000]  [ffffea0000000000-ffffea0003ffffff] PMD -> [ffff880028600000-ffff88002bbfffff] on node 0
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000010 -> 0x00001000
[    0.000000]   DMA32    0x00001000 -> 0x00100000
[    0.000000]   Normal   0x00100000 -> 0x00120000
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[3] active PFN ranges
[    0.000000]     0: 0x00000010 -> 0x0000009f
[    0.000000]     0: 0x00000100 -> 0x000cfe90
[    0.000000]     0: 0x00100000 -> 0x00120000
[    0.000000] On node 0 totalpages: 982559
[    0.000000]   DMA zone: 56 pages used for memmap
[    0.000000]   DMA zone: 105 pages reserved
[    0.000000]   DMA zone: 3822 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 14280 pages used for memmap
[    0.000000]   DMA32 zone: 833224 pages, LIFO batch:31
[    0.000000]   Normal zone: 1792 pages used for memmap
[    0.000000]   Normal zone: 129280 pages, LIFO batch:31
[    0.000000] ACPI: PM-Timer IO Port: 0x808
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x82] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x83] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x05] lapic_id[0x84] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x06] lapic_id[0x85] disabled)
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 33, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 low level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x8300 base: 0xfed00000
[    0.000000] SMP: Allowing 6 CPUs, 4 hotplug CPUs
[    0.000000] nr_irqs_gsi: 24
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e4000
[    0.000000] PM: Registered nosave memory: 00000000000e4000 - 0000000000100000
[    0.000000] PM: Registered nosave memory: 00000000cfe90000 - 00000000cfea8000
[    0.000000] PM: Registered nosave memory: 00000000cfea8000 - 00000000cfed0000
[    0.000000] PM: Registered nosave memory: 00000000cfed0000 - 00000000cff00000
[    0.000000] PM: Registered nosave memory: 00000000cff00000 - 00000000fff00000
[    0.000000] PM: Registered nosave memory: 00000000fff00000 - 0000000100000000
[    0.000000] Allocating PCI resources starting at cff00000 (gap: cff00000:30000000)
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] NR_CPUS:64 nr_cpumask_bits:64 nr_cpu_ids:6 nr_node_ids:1
[    0.000000] PERCPU: Embedded 30 pages/cpu @ffff880028200000 s91864 r8192 d22824 u262144
[    0.000000] pcpu-alloc: s91864 r8192 d22824 u262144 alloc=1*2097152
[    0.000000] pcpu-alloc: [0] 0 1 2 3 4 5 - - 
[    0.000000] Built 1 zonelists in Node order, mobility grouping on.  Total pages: 966326
[    0.000000] Policy zone: Normal
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.32-34-generic root=UUID=8497a121-ebea-42e5-af82-8b15ad546005 ro quiet splash nomodeset video=uvesafb:mode_option=1152x864-24,mtrr=3,scroll=ywrap
[    0.000000] PID hash table entries: 4096 (order: 3, 32768 bytes)
[    0.000000] Initializing CPU#0
[    0.000000] Checking aperture...
[    0.000000] No AGP bridge found
[    0.000000] Node 0: aperture @ 20000000 size 32 MB
[    0.000000] Aperture pointing to e820 RAM. Ignoring.
[    0.000000] Your BIOS doesn't leave a aperture memory hole
[    0.000000] Please enable the IOMMU option in the BIOS setup
[    0.000000] This costs you 64 MB of RAM
[    0.000000] Mapping aperture over 65536 KB of RAM @ 20000000
[    0.000000] PM: Registered nosave memory: 0000000020000000 - 0000000024000000
[    0.000000] Memory: 3784796k/4718592k available (5415k kernel code, 788356k absent, 145440k reserved, 2977k data, 888k init)
[    0.000000] SLUB: Genslabs=14, HWalign=64, Order=0-3, MinObjects=0, CPUs=6, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000] NR_IRQS:4352 nr_irqs:456
[    0.000000] Extended CMOS year: 2000
[    0.000000] spurious 8259A interrupt: IRQ7.
[    0.000000] Console: colour VGA+ 80x25
[    0.000000] console [tty0] enabled
[    0.000000] allocated 39321600 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] hpet clockevent registered
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 3013.729 MHz processor.
[    0.020004] Calibrating delay loop (skipped), value calculated using timer frequency.. 6027.45 BogoMIPS (lpj=30137250)
[    0.020022] Security Framework initialized
[    0.020036] AppArmor: AppArmor initialized
[    0.020282] Dentry cache hash table entries: 524288 (order: 10, 4194304 bytes)
[    0.021612] Inode-cache hash table entries: 262144 (order: 9, 2097152 bytes)
[    0.022238] Mount-cache hash table entries: 256
[    0.022337] Initializing cgroup subsys ns
[    0.022339] Initializing cgroup subsys cpuacct
[    0.022342] Initializing cgroup subsys memory
[    0.022348] Initializing cgroup subsys devices
[    0.022349] Initializing cgroup subsys freezer
[    0.022351] Initializing cgroup subsys net_cls
[    0.022365] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[    0.022367] CPU: L2 Cache: 1024K (64 bytes/line)
[    0.022369] CPU 0/0x0 -> Node 0
[    0.022371] tseg: 0000000000
[    0.022382] CPU: Physical Processor ID: 0
[    0.022383] CPU: Processor Core ID: 0
[    0.022385] mce: CPU supports 6 MCE banks
[    0.022393] Performance Events: AMD PMU driver.
[    0.022396] ... version:                0
[    0.022398] ... bit width:              48
[    0.022399] ... generic registers:      4
[    0.022400] ... value mask:             0000ffffffffffff
[    0.022401] ... max period:             00007fffffffffff
[    0.022402] ... fixed-purpose events:   0
[    0.022403] ... event mask:             000000000000000f
[    0.023589] ACPI: Core revision 20090903
[    0.047447] ftrace: converting mcount calls to 0f 1f 44 00 00
[    0.047450] ftrace: allocating 22484 entries in 89 pages
[    0.050073] Setting APIC routing to flat
[    0.050367] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.152664] CPU0: AMD Athlon(tm) II X2 250 Processor stepping 03
[    0.160000] Booting processor 1 APIC 0x1 ip 0x6000
[    0.030000] Initializing CPU#1
[    0.030000] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[    0.030000] CPU: L2 Cache: 1024K (64 bytes/line)
[    0.030000] CPU 1/0x1 -> Node 0
[    0.030000] CPU: Physical Processor ID: 0
[    0.030000] CPU: Processor Core ID: 1
[    0.310078] CPU1: AMD Athlon(tm) II X2 250 Processor stepping 03
[    0.310084] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
[    0.320011] Brought up 2 CPUs
[    0.320013] Total of 2 processors activated (12054.56 BogoMIPS).
[    0.320353] CPU0 attaching sched-domain:
[    0.320356]  domain 0: span 0-1 level MC
[    0.320358]   groups: 0 1
[    0.320362] CPU1 attaching sched-domain:
[    0.320363]  domain 0: span 0-1 level MC
[    0.320364]   groups: 1 0
[    0.320417] devtmpfs: initialized
[    0.320417] regulator: core version 0.5
[    0.320417] Time:  0:40:29  Date: 10/01/11
[    0.320417] NET: Registered protocol family 16
[    0.320417] node 0 link 0: io port [1000, ffffff]
[    0.320417] TOM: 00000000d0000000 aka 3328M
[    0.320417] Fam 10h mmconf [e0000000, efffffff]
[    0.320417] node 0 link 0: mmio [a0000, bffff]
[    0.320417] node 0 link 0: mmio [d0000000, efffffff] ==> [d0000000, dfffffff]
[    0.320417] node 0 link 0: mmio [f0000000, fe8fffff]
[    0.320417] node 0 link 0: mmio [fe900000, feafffff]
[    0.320417] node 0 link 0: mmio [feb00000, ffefffff]
[    0.320417] TOM2: 0000000130000000 aka 4864M
[    0.320417] bus: [00,07] on node 0 link 0
[    0.320417] bus: 00 index 0 io port: [0, ffff]
[    0.320417] bus: 00 index 1 mmio: [a0000, bffff]
[    0.320417] bus: 00 index 2 mmio: [d0000000, dfffffff]
[    0.320417] bus: 00 index 3 mmio: [f0000000, ffffffff]
[    0.320417] bus: 00 index 4 mmio: [130000000, fcffffffff]
[    0.320417] ACPI: bus type pci registered
[    0.320417] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 255
[    0.320417] PCI: Not using MMCONFIG.
[    0.320417] PCI: Using configuration type 1 for base access
[    0.320417] PCI: Using configuration type 1 for extended access
[    0.320689] Trying to unpack rootfs image as initramfs...
[    0.330022] bio: create slab <bio-0> at 0
[    0.350653] ACPI: EC: Look up EC in DSDT
[    0.352679] ACPI Error (psargs-0359): [ECEN] Namespace lookup failure, AE_NOT_FOUND
[    0.352684] ACPI Error (psparse-0537): Method parse/execution failed [\] (Node ffffffff81a0f080), AE_NOT_FOUND
[    0.352758] ACPI Error (dswload-0781): [PRID] Namespace lookup failure, AE_ALREADY_EXISTS
[    0.352761] ACPI Exception: AE_ALREADY_EXISTS, During name lookup/catalog (20090903/psloop-230)
[    0.352765] ACPI Error (psparse-0537): Method parse/execution failed [\] (Node ffffffff81a0f080), AE_ALREADY_EXISTS
[    0.352768] ACPI: Marking method \___ as Serialized because of AE_ALREADY_EXISTS error
[    0.352817] ACPI: Executed 3 blocks of module-level executable AML code
[    0.432222] ACPI: Interpreter enabled
[    0.432226] ACPI: (supports S0 S1 S3 S4 S5)
[    0.432245] ACPI: Using IOAPIC for interrupt routing
[    0.432296] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 255
[    0.436332] PCI: MCFG area at e0000000 reserved in ACPI motherboard resources
[    0.441737] PCI: Using MMCONFIG at e0000000 - efffffff
[    0.447418] ACPI Warning: Incorrect checksum in table [OEMB] - F8, should be F3 (20090903/tbutils-314)
[    0.447510] ACPI: No dock devices found.
[    0.447632] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.447738] pci 0000:00:0a.0: PME# supported from D0 D3hot D3cold
[    0.447740] pci 0000:00:0a.0: PME# disabled
[    0.447786] pci 0000:00:11.0: reg 10 io port: [0xc000-0xc007]
[    0.447792] pci 0000:00:11.0: reg 14 io port: [0xb000-0xb003]
[    0.447798] pci 0000:00:11.0: reg 18 io port: [0xa000-0xa007]
[    0.447804] pci 0000:00:11.0: reg 1c io port: [0x9000-0x9003]
[    0.447810] pci 0000:00:11.0: reg 20 io port: [0x8000-0x800f]
[    0.447816] pci 0000:00:11.0: reg 24 32bit mmio: [0xfe8ffc00-0xfe8fffff]
[    0.447832] pci 0000:00:11.0: set SATA to AHCI mode
[    0.447872] pci 0000:00:12.0: reg 10 32bit mmio: [0xfe8fe000-0xfe8fefff]
[    0.447921] pci 0000:00:12.1: reg 10 32bit mmio: [0xfe8fd000-0xfe8fdfff]
[    0.447986] pci 0000:00:12.2: reg 10 32bit mmio: [0xfe8ff800-0xfe8ff8ff]
[    0.448033] pci 0000:00:12.2: supports D1 D2
[    0.448034] pci 0000:00:12.2: PME# supported from D0 D1 D2 D3hot
[    0.448037] pci 0000:00:12.2: PME# disabled
[    0.448066] pci 0000:00:13.0: reg 10 32bit mmio: [0xfe8fc000-0xfe8fcfff]
[    0.448114] pci 0000:00:13.1: reg 10 32bit mmio: [0xfe8fb000-0xfe8fbfff]
[    0.448179] pci 0000:00:13.2: reg 10 32bit mmio: [0xfe8ff400-0xfe8ff4ff]
[    0.448226] pci 0000:00:13.2: supports D1 D2
[    0.448227] pci 0000:00:13.2: PME# supported from D0 D1 D2 D3hot
[    0.448231] pci 0000:00:13.2: PME# disabled
[    0.448337] pci 0000:00:14.1: reg 10 io port: [0x00-0x07]
[    0.448343] pci 0000:00:14.1: reg 14 io port: [0x00-0x03]
[    0.448349] pci 0000:00:14.1: reg 18 io port: [0x00-0x07]
[    0.448354] pci 0000:00:14.1: reg 1c io port: [0x00-0x03]
[    0.448360] pci 0000:00:14.1: reg 20 io port: [0xff00-0xff0f]
[    0.448419] pci 0000:00:14.2: reg 10 64bit mmio: [0xfe8f4000-0xfe8f7fff]
[    0.448458] pci 0000:00:14.2: PME# supported from D0 D3hot D3cold
[    0.448461] pci 0000:00:14.2: PME# disabled
[    0.448556] pci 0000:00:14.5: reg 10 32bit mmio: [0xfe8fa000-0xfe8fafff]
[    0.448673] pci 0000:01:05.0: reg 10 32bit mmio pref: [0xd0000000-0xdfffffff]
[    0.448676] pci 0000:01:05.0: reg 14 io port: [0xd000-0xd0ff]
[    0.448679] pci 0000:01:05.0: reg 18 32bit mmio: [0xfeaf0000-0xfeafffff]
[    0.448684] pci 0000:01:05.0: reg 24 32bit mmio: [0xfe900000-0xfe9fffff]
[    0.448694] pci 0000:01:05.0: supports D1 D2
[    0.448709] pci 0000:01:05.1: reg 10 32bit mmio: [0xfeae8000-0xfeaebfff]
[    0.448725] pci 0000:01:05.1: supports D1 D2
[    0.448760] pci 0000:00:01.0: bridge io port: [0xd000-0xdfff]
[    0.448763] pci 0000:00:01.0: bridge 32bit mmio: [0xfe900000-0xfeafffff]
[    0.448766] pci 0000:00:01.0: bridge 64bit mmio pref: [0xd0000000-0xdfffffff]
[    0.448796] pci 0000:02:00.0: reg 10 io port: [0xe800-0xe8ff]
[    0.448809] pci 0000:02:00.0: reg 18 64bit mmio pref: [0xfdfff000-0xfdffffff]
[    0.448819] pci 0000:02:00.0: reg 20 64bit mmio pref: [0xfdff8000-0xfdffbfff]
[    0.448824] pci 0000:02:00.0: reg 30 32bit mmio pref: [0xfebf0000-0xfebfffff]
[    0.448850] pci 0000:02:00.0: supports D1 D2
[    0.448851] pci 0000:02:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.448855] pci 0000:02:00.0: PME# disabled
[    0.448908] pci 0000:00:0a.0: bridge io port: [0xe000-0xefff]
[    0.448910] pci 0000:00:0a.0: bridge 32bit mmio: [0xfeb00000-0xfebfffff]
[    0.448913] pci 0000:00:0a.0: bridge 64bit mmio pref: [0xfdf00000-0xfdffffff]
[    0.448965] pci 0000:00:14.4: transparent bridge
[    0.448983] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.449148] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P1._PRT]
[    0.449207] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCEA._PRT]
[    0.449264] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0PC._PRT]
[    0.452756] ACPI: PCI Interrupt Link [LNKA] (IRQs 4 7 *10 11 12 14 15)
[    0.452842] ACPI: PCI Interrupt Link [LNKB] (IRQs 4 7 10 *11 12 14 15)
[    0.452931] ACPI: PCI Interrupt Link [LNKC] (IRQs 4 7 *10 11 12 14 15)
[    0.453017] ACPI: PCI Interrupt Link [LNKD] (IRQs 4 7 *10 11 12 14 15)
[    0.453102] ACPI: PCI Interrupt Link [LNKE] (IRQs 4 7 10 11 12 14 15) *0, disabled.
[    0.453187] ACPI: PCI Interrupt Link [LNKF] (IRQs 4 7 10 11 12 14 15) *0, disabled.
[    0.453273] ACPI: PCI Interrupt Link [LNKG] (IRQs 4 7 10 *11 12 14 15)
[    0.453358] ACPI: PCI Interrupt Link [LNKH] (IRQs 4 7 10 11 12 14 15) *0, disabled.
[    0.453448] vgaarb: device added: PCI:0000:01:05.0,decodes=io+mem,owns=io+mem,locks=none
[    0.453450] vgaarb: loaded
[    0.453521] SCSI subsystem initialized
[    0.453594] libata version 3.00 loaded.
[    0.453643] usbcore: registered new interface driver usbfs
[    0.453651] usbcore: registered new interface driver hub
[    0.453670] usbcore: registered new device driver usb
[    0.453773] ACPI: WMI: Mapper loaded
[    0.453774] PCI: Using ACPI for IRQ routing
[    0.453880] NetLabel: Initializing
[    0.453882] NetLabel:  domain hash size = 128
[    0.453883] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.453893] NetLabel:  unlabeled traffic allowed by default
[    0.453917] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0
[    0.453920] hpet0: 4 comparators, 32-bit 14.318180 MHz counter
[    0.455941] Switching to clocksource tsc
[    0.456095] AppArmor: AppArmor Filesystem Enabled
[    0.456095] pnp: PnP ACPI init
[    0.456095] ACPI: bus type pnp registered
[    0.456095] pnp: PnP ACPI: found 14 devices
[    0.456095] ACPI: ACPI bus type pnp unregistered
[    0.456095] system 00:09: iomem range 0xfec00000-0xfec00fff could not be reserved
[    0.456095] system 00:09: iomem range 0xfee00000-0xfee00fff has been reserved
[    0.456095] system 00:0a: ioport range 0x4d0-0x4d1 has been reserved
[    0.456095] system 00:0a: ioport range 0x40b-0x40b has been reserved
[    0.456095] system 00:0a: ioport range 0x4d6-0x4d6 has been reserved
[    0.456095] system 00:0a: ioport range 0xc00-0xc01 has been reserved
[    0.456095] system 00:0a: ioport range 0xc14-0xc14 has been reserved
[    0.456095] system 00:0a: ioport range 0xc50-0xc51 has been reserved
[    0.456095] system 00:0a: ioport range 0xc52-0xc52 has been reserved
[    0.456095] system 00:0a: ioport range 0xc6c-0xc6c has been reserved
[    0.456095] system 00:0a: ioport range 0xc6f-0xc6f has been reserved
[    0.456095] system 00:0a: ioport range 0xcd0-0xcd1 has been reserved
[    0.456095] system 00:0a: ioport range 0xcd2-0xcd3 has been reserved
[    0.456095] system 00:0a: ioport range 0xcd4-0xcd5 has been reserved
[    0.456095] system 00:0a: ioport range 0xcd6-0xcd7 has been reserved
[    0.456095] system 00:0a: ioport range 0xcd8-0xcdf has been reserved
[    0.456095] system 00:0a: ioport range 0xb00-0xb3f has been reserved
[    0.456095] system 00:0a: ioport range 0x800-0x89f has been reserved
[    0.456095] system 00:0a: ioport range 0xb00-0xb0f has been reserved
[    0.456095] system 00:0a: ioport range 0xb20-0xb3f has been reserved
[    0.456095] system 00:0a: ioport range 0x900-0x90f has been reserved
[    0.456095] system 00:0a: ioport range 0x910-0x91f has been reserved
[    0.456095] system 00:0a: ioport range 0xfe00-0xfefe has been reserved
[    0.456095] system 00:0a: iomem range 0xcff00000-0xcfffffff could not be reserved
[    0.456095] system 00:0a: iomem range 0xffb80000-0xffbfffff has been reserved
[    0.456095] system 00:0a: iomem range 0xfec10000-0xfec1001f has been reserved
[    0.456095] system 00:0a: iomem range 0xfed40000-0xfed44fff has been reserved
[    0.456095] system 00:0b: ioport range 0x230-0x23f has been reserved
[    0.456095] system 00:0b: ioport range 0x290-0x29f has been reserved
[    0.456095] system 00:0b: ioport range 0x300-0x30f has been reserved
[    0.456095] system 00:0b: ioport range 0xa30-0xa3f has been reserved
[    0.456095] system 00:0c: iomem range 0xe0000000-0xefffffff has been reserved
[    0.456095] system 00:0d: iomem range 0x0-0x9ffff could not be reserved
[    0.456095] system 00:0d: iomem range 0xc0000-0xcffff has been reserved
[    0.456095] system 00:0d: iomem range 0xe0000-0xfffff could not be reserved
[    0.456095] system 00:0d: iomem range 0x100000-0xcfefffff could not be reserved
[    0.456095] system 00:0d: iomem range 0xfec00000-0xffffffff could not be reserved
[    0.459413] pci 0000:00:01.0: PCI bridge, secondary bus 0000:01
[    0.459415] pci 0000:00:01.0:   IO window: 0xd000-0xdfff
[    0.459417] pci 0000:00:01.0:   MEM window: 0xfe900000-0xfeafffff
[    0.459420] pci 0000:00:01.0:   PREFETCH window: 0x000000d0000000-0x000000dfffffff
[    0.459423] pci 0000:00:0a.0: PCI bridge, secondary bus 0000:02
[    0.459425] pci 0000:00:0a.0:   IO window: 0xe000-0xefff
[    0.459427] pci 0000:00:0a.0:   MEM window: 0xfeb00000-0xfebfffff
[    0.459430] pci 0000:00:0a.0:   PREFETCH window: 0x000000fdf00000-0x000000fdffffff
[    0.459433] pci 0000:00:14.4: PCI bridge, secondary bus 0000:03
[    0.459434] pci 0000:00:14.4:   IO window: disabled
[    0.459438] pci 0000:00:14.4:   MEM window: disabled
[    0.459441] pci 0000:00:14.4:   PREFETCH window: disabled
[    0.459454]   alloc irq_desc for 18 on node 0
[    0.459455]   alloc kstat_irqs on node 0
[    0.459459] pci 0000:00:0a.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    0.459461] pci 0000:00:0a.0: setting latency timer to 64
[    0.459468] pci_bus 0000:00: resource 0 io:  [0x00-0xffff]
[    0.459469] pci_bus 0000:00: resource 1 mem: [0x000000-0xffffffffffffffff]
[    0.459471] pci_bus 0000:01: resource 0 io:  [0xd000-0xdfff]
[    0.459473] pci_bus 0000:01: resource 1 mem: [0xfe900000-0xfeafffff]
[    0.459475] pci_bus 0000:01: resource 2 pref mem [0xd0000000-0xdfffffff]
[    0.459477] pci_bus 0000:02: resource 0 io:  [0xe000-0xefff]
[    0.459478] pci_bus 0000:02: resource 1 mem: [0xfeb00000-0xfebfffff]
[    0.459480] pci_bus 0000:02: resource 2 pref mem [0xfdf00000-0xfdffffff]
[    0.459482] pci_bus 0000:03: resource 3 io:  [0x00-0xffff]
[    0.459483] pci_bus 0000:03: resource 4 mem: [0x000000-0xffffffffffffffff]
[    0.459507] NET: Registered protocol family 2
[    0.459627] IP route cache hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.460510] TCP established hash table entries: 524288 (order: 11, 8388608 bytes)
[    0.463179] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[    0.463522] TCP: Hash tables configured (established 524288 bind 65536)
[    0.463524] TCP reno registered
[    0.463609] NET: Registered protocol family 1
[    1.188904] Freeing initrd memory: 13200k freed
[    1.233906] pci 0000:01:05.0: Boot video device
[    1.234565] PCI-DMA: Disabling AGP.
[    1.234636] PCI-DMA: aperture base @ 20000000 size 65536 KB
[    1.234638] PCI-DMA: using GART IOMMU.
[    1.234640] PCI-DMA: Reserving 64MB of IOMMU area in the AGP aperture
[    1.235680] Scanning for low memory corruption every 60 seconds
[    1.235761] audit: initializing netlink socket (disabled)
[    1.235773] type=2000 audit(1317429629.233:1): initialized
[    1.241631] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    1.242500] VFS: Disk quotas dquot_6.5.2
[    1.242536] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    1.242961] fuse init (API version 7.13)
[    1.243061] msgmni has been set to 7417
[    1.243265] alg: No test for stdrng (krng)
[    1.243335] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    1.243340] io scheduler noop registered
[    1.243341] io scheduler anticipatory registered
[    1.243343] io scheduler deadline registered
[    1.243366] io scheduler cfq registered (default)
[    1.243540]   alloc irq_desc for 24 on node 0
[    1.243541]   alloc kstat_irqs on node 0
[    1.243547] pcieport 0000:00:0a.0: irq 24 for MSI/MSI-X
[    1.243551] pcieport 0000:00:0a.0: setting latency timer to 64
[    1.243636] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    1.243657] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    1.243729] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0
[    1.243731] ACPI: Power Button [PWRB]
[    1.243759] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
[    1.243760] ACPI: Power Button [PWRF]
[    1.244240] processor LNXCPU:00: registered as cooling_device0
[    1.244430] processor LNXCPU:01: registered as cooling_device1
[    1.247142] Linux agpgart interface v0.103
[    1.247165] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    1.247263] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    1.247486] 00:08: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    1.248058] brd: module loaded
[    1.248319] loop: module loaded
[    1.248369] input: Macintosh mouse button emulation as /devices/virtual/input/input2
[    1.248524]   alloc irq_desc for 16 on node 0
[    1.248526]   alloc kstat_irqs on node 0
[    1.248531] pata_acpi 0000:00:14.1: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.248554] pata_acpi 0000:00:14.1: setting latency timer to 64
[    1.248865] Fixed MDIO Bus: probed
[    1.248887] PPP generic driver version 2.4.2
[    1.248924] tun: Universal TUN/TAP device driver, 1.6
[    1.248925] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    1.248982] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    1.249049]   alloc irq_desc for 17 on node 0
[    1.249052]   alloc kstat_irqs on node 0
[    1.249058] ehci_hcd 0000:00:12.2: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    1.249091] ehci_hcd 0000:00:12.2: EHCI Host Controller
[    1.249154] ehci_hcd 0000:00:12.2: new USB bus registered, assigned bus number 1
[    1.249183] ehci_hcd 0000:00:12.2: debug port 1
[    1.249202] ehci_hcd 0000:00:12.2: irq 17, io mem 0xfe8ff800
[    1.263914] ehci_hcd 0000:00:12.2: USB 2.0 started, EHCI 1.00
[    1.264011] usb usb1: configuration #1 chosen from 1 choice
[    1.264029] hub 1-0:1.0: USB hub found
[    1.264034] hub 1-0:1.0: 6 ports detected
[    1.264144]   alloc irq_desc for 19 on node 0
[    1.264145]   alloc kstat_irqs on node 0
[    1.264150] ehci_hcd 0000:00:13.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    1.264167] ehci_hcd 0000:00:13.2: EHCI Host Controller
[    1.264192] ehci_hcd 0000:00:13.2: new USB bus registered, assigned bus number 2
[    1.264218] ehci_hcd 0000:00:13.2: debug port 1
[    1.264236] ehci_hcd 0000:00:13.2: irq 19, io mem 0xfe8ff400
[    1.283884] ehci_hcd 0000:00:13.2: USB 2.0 started, EHCI 1.00
[    1.283980] usb usb2: configuration #1 chosen from 1 choice
[    1.283997] hub 2-0:1.0: USB hub found
[    1.284002] hub 2-0:1.0: 6 ports detected
[    1.284085] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    1.284147] ohci_hcd 0000:00:12.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.284167] ohci_hcd 0000:00:12.0: OHCI Host Controller
[    1.284198] ohci_hcd 0000:00:12.0: new USB bus registered, assigned bus number 3
[    1.284223] ohci_hcd 0000:00:12.0: irq 16, io mem 0xfe8fe000
[    1.347974] usb usb3: configuration #1 chosen from 1 choice
[    1.347992] hub 3-0:1.0: USB hub found
[    1.348000] hub 3-0:1.0: 3 ports detected
[    1.348109] ohci_hcd 0000:00:12.1: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.348126] ohci_hcd 0000:00:12.1: OHCI Host Controller
[    1.348151] ohci_hcd 0000:00:12.1: new USB bus registered, assigned bus number 4
[    1.348173] ohci_hcd 0000:00:12.1: irq 16, io mem 0xfe8fd000
[    1.407967] usb usb4: configuration #1 chosen from 1 choice
[    1.407989] hub 4-0:1.0: USB hub found
[    1.407998] hub 4-0:1.0: 3 ports detected
[    1.408107] ohci_hcd 0000:00:13.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    1.408126] ohci_hcd 0000:00:13.0: OHCI Host Controller
[    1.408152] ohci_hcd 0000:00:13.0: new USB bus registered, assigned bus number 5
[    1.408175] ohci_hcd 0000:00:13.0: irq 18, io mem 0xfe8fc000
[    1.467971] usb usb5: configuration #1 chosen from 1 choice
[    1.467992] hub 5-0:1.0: USB hub found
[    1.468001] hub 5-0:1.0: 3 ports detected
[    1.468107] ohci_hcd 0000:00:13.1: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    1.468125] ohci_hcd 0000:00:13.1: OHCI Host Controller
[    1.468157] ohci_hcd 0000:00:13.1: new USB bus registered, assigned bus number 6
[    1.468174] ohci_hcd 0000:00:13.1: irq 18, io mem 0xfe8fb000
[    1.527965] usb usb6: configuration #1 chosen from 1 choice
[    1.527983] hub 6-0:1.0: USB hub found
[    1.527991] hub 6-0:1.0: 3 ports detected
[    1.528102] ohci_hcd 0000:00:14.5: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    1.528121] ohci_hcd 0000:00:14.5: OHCI Host Controller
[    1.528152] ohci_hcd 0000:00:14.5: new USB bus registered, assigned bus number 7
[    1.528169] ohci_hcd 0000:00:14.5: irq 18, io mem 0xfe8fa000
[    1.587961] usb usb7: configuration #1 chosen from 1 choice
[    1.587980] hub 7-0:1.0: USB hub found
[    1.587988] hub 7-0:1.0: 2 ports detected
[    1.588066] uhci_hcd: USB Universal Host Controller Interface driver
[    1.588128] PNP: No PS/2 controller found. Probing ports directly.
[    1.588470] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.588480] serio: i8042 AUX port at 0x60,0x64 irq 12
[    1.588555] mice: PS/2 mouse device common for all mice
[    1.588616] rtc_cmos 00:03: RTC can wake from S4
[    1.588642] rtc_cmos 00:03: rtc core: registered rtc_cmos as rtc0
[    1.588664] rtc0: alarms up to one month, y3k, 114 bytes nvram, hpet irqs
[    1.588747] device-mapper: uevent: version 1.0.3
[    1.588836] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: dm-devel@redhat.com
[    1.588927] device-mapper: multipath: version 1.1.0 loaded
[    1.588929] device-mapper: multipath round-robin: version 1.0.0 loaded
[    1.589108] cpuidle: using governor ladder
[    1.589110] cpuidle: using governor menu
[    1.589353] TCP cubic registered
[    1.589439] NET: Registered protocol family 10
[    1.589906] NET: Registered protocol family 17
[    1.589936] powernow-k8: Found 1 AMD Athlon(tm) II X2 250 Processor processors (2 cpu cores) (version 2.20.00)
[    1.589969] powernow-k8:    0 : pstate 0 (3000 MHz)
[    1.589971] powernow-k8:    1 : pstate 1 (2300 MHz)
[    1.589972] powernow-k8:    2 : pstate 2 (1800 MHz)
[    1.589973] powernow-k8:    3 : pstate 3 (800 MHz)
[    1.590382] PM: Resume from disk failed.
[    1.590390] registered taskstats version 1
[    1.590622]   Magic number: 15:227:657
[    1.590635] block ram10: hash matches
[    1.590695] rtc_cmos 00:03: setting system clock to 2011-10-01 00:40:30 UTC (1317429630)
[    1.590697] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.590699] EDD information not available.
[    1.590732] Freeing unused kernel memory: 888k freed
[    1.590952] Write protecting the kernel read-only data: 7692k
[    1.618015] udev: starting version 151
[    1.669618] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    1.669636] r8169 0000:02:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    1.681794] r8169 0000:02:00.0: setting latency timer to 64
[    1.682701] ahci 0000:00:11.0: version 3.0
[    1.682715]   alloc irq_desc for 22 on node 0
[    1.682717]   alloc kstat_irqs on node 0
[    1.682722] ahci 0000:00:11.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[    1.682821] ahci 0000:00:11.0: AHCI 0001.0100 32 slots 4 ports 3 Gbps 0xf impl SATA mode
[    1.682824] ahci 0000:00:11.0: flags: 64bit ncq sntf ilck pm led clo pmp pio slum part ccc 
[    1.686150] scsi0 : ahci
[    1.691851] scsi1 : ahci
[    1.701491] scsi2 : ahci
[    1.708949] scsi3 : ahci
[    1.709004] ata1: SATA max UDMA/133 abar m1024@0xfe8ffc00 port 0xfe8ffd00 irq 22
[    1.709008] ata2: SATA max UDMA/133 abar m1024@0xfe8ffc00 port 0xfe8ffd80 irq 22
[    1.709010] ata3: SATA max UDMA/133 abar m1024@0xfe8ffc00 port 0xfe8ffe00 irq 22
[    1.709013] ata4: SATA max UDMA/133 abar m1024@0xfe8ffc00 port 0xfe8ffe80 irq 22
[    1.710971] scsi4 : pata_atiixp
[    1.711291] scsi5 : pata_atiixp
[    1.712262] ata5: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xff00 irq 14
[    1.712264] ata6: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xff08 irq 15
[    1.712297]   alloc irq_desc for 25 on node 0
[    1.712299]   alloc kstat_irqs on node 0
[    1.712309] r8169 0000:02:00.0: irq 25 for MSI/MSI-X
[    1.712706] eth0: RTL8168d/8111d at 0xffffc90000676000, f4:6d:04:39:ba:78, XID 083000c0 IRQ 25
[    1.820867] usb 4-2: new low speed USB device using ohci_hcd and address 2
[    2.021947] usb 4-2: configuration #1 chosen from 1 choice
[    2.030436] usbcore: registered new interface driver hiddev
[    2.034026] input: USB USB Keykoard as /devices/pci0000:00/0000:00:12.1/usb4/4-2/4-2:1.0/input/input3
[    2.034089] generic-usb 0003:1C4F:0002.0001: input,hidraw0: USB HID v1.10 Keyboard [USB USB Keykoard] on usb-0000:00:12.1-2/input0
[    2.060909] ata4: SATA link down (SStatus 0 SControl 300)
[    2.070048] ata2: SATA link down (SStatus 0 SControl 300)
[    2.240063] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    2.240068] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    2.241816] ata1.00: ATA-8: WDC WD1600AAJS-60B4A0, 02.03A02, max UDMA/100
[    2.241819] ata1.00: 312581808 sectors, multi 16: LBA48 NCQ (depth 31/32), AA
[    2.242551] ata3.00: ATAPI: ASUS    DRW-24B1ST   a, 1.04, max UDMA/100
[    2.242741] ata1.00: configured for UDMA/100
[    2.243399] ata3.00: configured for UDMA/100
[    2.260152] scsi 0:0:0:0: Direct-Access     ATA      WDC WD1600AAJS-6 02.0 PQ: 0 ANSI: 5
[    2.260274] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    2.260349] sd 0:0:0:0: [sda] 312581808 512-byte logical blocks: (160 GB/149 GiB)
[    2.260385] sd 0:0:0:0: [sda] Write Protect is off
[    2.260387] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    2.260410] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.260518]  sda:
[    2.263722] scsi 2:0:0:0: CD-ROM            ASUS     DRW-24B1ST   a   1.04 PQ: 0 ANSI: 5
[    2.269740] sr0: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
[    2.269744] Uniform CD-ROM driver Revision: 3.20
[    2.269840] sr 2:0:0:0: Attached scsi CD-ROM sr0
[    2.269883] sr 2:0:0:0: Attached scsi generic sg1 type 5
[    2.279782]  sda1 sda2 < sda5 sda6 sda7 >
[    2.314406] sd 0:0:0:0: [sda] Attached SCSI disk
[    2.330894] usb 4-3: new low speed USB device using ohci_hcd and address 3
[    2.522896] usb 4-3: configuration #1 chosen from 1 choice
[   12.031850] /build/buildd/linux-2.6.32/drivers/hid/usbhid/hid-core.c: usb_submit_urb(ctrl) failed
[   12.031863] generic-usb 0003:1C4F:0002.0002: timeout initializing reports
[   12.031942] input: USB USB Keykoard as /devices/pci0000:00/0000:00:12.1/usb4/4-2/4-2:1.1/input/input4
[   12.032011] generic-usb 0003:1C4F:0002.0002: input,hidraw1: USB HID v1.10 Device [USB USB Keykoard] on usb-0000:00:12.1-2/input1
[   12.036009] input:  USB OPTICAL MOUSE as /devices/pci0000:00/0000:00:12.1/usb4/4-3/4-3:1.0/input/input5
[   12.036075] generic-usb 0003:15D9:0A4C.0003: input,hidraw2: USB HID v1.11 Mouse [ USB OPTICAL MOUSE] on usb-0000:00:12.1-3/input0
[   12.036094] usbcore: registered new interface driver usbhid
[   12.036096] usbhid: v2.6:USB HID core driver
[   12.076378] uvesafb: (C) 1988-2005, ATI Technologies Inc. , RS780, 01.00, OEM: ATI ATOMBIOS, VBE v3.0
[   12.099710] uvesafb: VBIOS/hardware supports DDC2 transfers
[   12.278117] uvesafb: monitor limits: vf = 75 Hz, hf = 85 kHz, clk = 170 MHz
[   12.278289] uvesafb: scrolling: redraw
[   12.278880] uvesafb: framebuffer at 0xd0000000, mapped to 0xffffc90011100000, using 16384k, total 16384k
[   12.278882] fb0: VESA VGA frame buffer device
[   12.283739] uvesafb: mode switch failed (eax=0x34f, err=0). Trying again with default timings.
[   12.734044] uvesafb: mode switch failed (eax=0x34f, err=0). Trying again with default timings.
[   13.168417] Console: switching to colour frame buffer device 144x54
[   13.168576] uvesafb: mode switch failed (eax=0x34f, err=0). Trying again with default timings.
[   13.736176] uvesafb: mode switch failed (eax=0x34f, err=0). Trying again with default timings.
[   14.379228] EXT4-fs (sda1): mounted filesystem with ordered data mode
[   21.319553] udev: starting version 151
[   21.468661] Adding 8385920k swap on /dev/sda5.  Priority:-1 extents:1 across:8385920k 
[   21.502535] type=1505 audit(1317429650.410:2):  operation="profile_load" pid=749 name="/sbin/dhclient3"
[   21.502553] type=1505 audit(1317429650.410:3):  operation="profile_replace" pid=754 name="/sbin/dhclient3"
[   21.502730] type=1505 audit(1317429650.410:4):  operation="profile_load" pid=749 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[   21.502758] type=1505 audit(1317429650.410:5):  operation="profile_replace" pid=754 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[   21.502841] type=1505 audit(1317429650.410:6):  operation="profile_load" pid=749 name="/usr/lib/connman/scripts/dhclient-script"
[   21.502874] type=1505 audit(1317429650.410:7):  operation="profile_replace" pid=754 name="/usr/lib/connman/scripts/dhclient-script"
[   21.847905] lp: driver loaded but no devices found
[   21.887620] ACPI: resource piix4_smbus [0xb00-0xb07] conflicts with ACPI region SOR1 [0x000b00-0x000b0f]
[   21.887623] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[   21.910668] parport_pc 00:06: reported by Plug and Play ACPI
[   21.910721] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
[   21.912035] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   21.922461] EDAC MC: Ver: 2.1.0 Sep 13 2011
[   21.952853] ppdev: user-space parallel port driver
[   21.991008] lp0: using parport0 (interrupt-driven).
[   22.019803] it87: Found IT8712F chip at 0x290, revision 8
[   22.019811] it87: in3 is VCC (+5V)
[   22.019813] it87: in7 is VCCH (+5V Stand-By)
[   22.019838] ACPI: resource it87 [0x295-0x296] conflicts with ACPI region SIOE [0x290-0x2af]
[   22.019839] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[   22.022326] ip_tables: (C) 2000-2006 Netfilter Core Team
[   22.041398] EDAC amd64_edac:  Ver: 3.2.0 Sep 13 2011
[   22.041814] EDAC amd64: This node reports that Memory ECC is currently disabled, set F3x44[22] (0000:00:18.3).
[   22.041821] EDAC amd64: ECC disabled in the BIOS or no ECC capability, module will not load.
[   22.041822]  Either enable ECC checking or force module loading by setting 'ecc_enable_override'.
[   22.041823]  (Note that use of the override may cause unknown side effects.)
[   22.041835] amd64_edac: probe of 0000:00:18.2 failed with error -22
[   22.042695] vga16fb: initializing
[   22.042700] vga16fb: mapped to 0xffff8800000a0000
[   22.042704] vga16fb: not registering due to another framebuffer present
[   22.152199] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
[   22.152202] Disabling lock debugging due to kernel taint
[   22.203122] [fglrx] Maximum main memory to use for locked dma buffers: 3551 MBytes.
[   22.203163] [fglrx]   vendor: 1002 device: 9616 count: 1
[   22.203440] [fglrx] ioport: bar 1, base 0xd000, size: 0x100
[   22.203451] pci 0000:01:05.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[   22.203454] pci 0000:01:05.0: setting latency timer to 64
[   22.203721] [fglrx] Kernel PAT support is enabled
[   22.203737] [fglrx] module loaded - fglrx 8.80.5 [Nov 25 2010] with 1 minors
[   22.467622] nf_conntrack version 0.5.0 (16384 buckets, 65536 max)
[   22.467781] CONFIG_NF_CT_ACCT is deprecated and will be removed soon. Please use
[   22.467783] nf_conntrack.acct=1 kernel parameter, acct=1 nf_conntrack module option or
[   22.467784] sysctl net.netfilter.nf_conntrack_acct=1 to enable it.
[   22.620129] ip6_tables: (C) 2000-2006 Netfilter Core Team
[   22.708255] HDA Intel 0000:00:14.2: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   22.850138] HDA Intel 0000:01:05.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[   22.850191] HDA Intel 0000:01:05.1: setting latency timer to 64
[   23.190361] EXT4-fs (sda7): mounted filesystem with ordered data mode
[   23.854005] EXT4-fs (sda6): mounted filesystem with ordered data mode
[   23.936121] type=1505 audit(1317429652.840:8):  operation="profile_load" pid=1202 name="/usr/share/gdm/guest-session/Xsession"
[   23.940304] type=1505 audit(1317429652.840:9):  operation="profile_replace" pid=1203 name="/sbin/dhclient3"
[   23.940464] r8169: eth0: link up
[   23.940447] r8169: eth0: link up
[   23.940521] type=1505 audit(1317429652.840:10):  operation="profile_replace" pid=1203 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[   23.940639] type=1505 audit(1317429652.840:11):  operation="profile_replace" pid=1203 name="/usr/lib/connman/scripts/dhclient-script"
[   24.416581] CPUFREQ: Per core ondemand sysfs interface is deprecated - ignore_nice_load
[   24.517714] [fglrx] GART Table is not in FRAME_BUFFER range 
[   24.517863]   alloc irq_desc for 26 on node 0
[   24.517865]   alloc kstat_irqs on node 0
[   24.517871] fglrx_pci 0000:01:05.0: irq 26 for MSI/MSI-X
[   24.518369] [fglrx] Firegl kernel thread PID: 1449
[   24.518877] [fglrx] IRQ 26 Enabled
[   24.695873] vboxdrv: Trying to deactivate the NMI watchdog permanently...
[   24.695875] vboxdrv: Successfully done.
[   24.695877] vboxdrv: Found 2 processor cores.
[   24.695952] VBoxDrv: dbg - g_abExecMemory=ffffffffa04b9a20
[   24.695971] vboxdrv: fAsync=0 offMin=0x30e offMax=0x97e
[   24.696301] vboxdrv: TSC mode is 'synchronous', kernel timer mode is 'normal'.
[   24.696302] vboxdrv: Successfully loaded version 3.1.6_OSE (interface 0x00100001).
[   25.076546] CPU0 attaching NULL sched-domain.
[   25.076553] CPU1 attaching NULL sched-domain.
[   25.131114] CPU0 attaching sched-domain:
[   25.131123]  domain 0: span 0-1 level MC
[   25.131129]   groups: 0 1
[   25.131141] CPU1 attaching sched-domain:
[   25.131146]  domain 0: span 0-1 level MC
[   25.131151]   groups: 1 0
[   26.003758] [fglrx] Gart USWC size:1160 M.
[   26.003761] [fglrx] Gart cacheable size:459 M.
[   26.003765] [fglrx] Reserved FB block: Shared offset:0, size:1000000 
[   26.003767] [fglrx] Reserved FB block: Unshared offset:fffc000, size:4000 
[   28.608909] CPU0 attaching NULL sched-domain.
[   28.608914] CPU1 attaching NULL sched-domain.
[   28.641012] CPU0 attaching sched-domain:
[   28.641017]  domain 0: span 0-1 level MC
[   28.641020]   groups: 0 1
[   28.641026] CPU1 attaching sched-domain:
[   28.641028]  domain 0: span 0-1 level MC
[   28.641030]   groups: 1 0
[   29.169065] hda-intel: IRQ timing workaround is activated for card #1. Suggest a bigger bdl_pos_adj.
[   34.880004] eth0: no IPv6 routers present
```Hardware:
```
00:00.0 Host bridge: Advanced Micro Devices [AMD] RS780 Host Bridge
00:01.0 PCI bridge: ASUSTeK Computer Inc. RS880 PCI to PCI bridge (int gfx)
    Kernel modules: shpchp
00:0a.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 5)
    Kernel driver in use: pcieport
    Kernel modules: shpchp
00:11.0 SATA controller: ATI Technologies Inc SB700/SB800 SATA Controller [IDE mode]
    Kernel driver in use: ahci
    Kernel modules: ahci
00:12.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
    Kernel driver in use: ohci_hcd
00:12.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller
    Kernel driver in use: ohci_hcd
00:12.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
    Kernel driver in use: ehci_hcd
00:13.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
    Kernel driver in use: ohci_hcd
00:13.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller
    Kernel driver in use: ohci_hcd
00:13.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
    Kernel driver in use: ehci_hcd
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 3c)
    Kernel modules: i2c-piix4
00:14.1 IDE interface: ATI Technologies Inc SB700/SB800 IDE Controller
    Kernel driver in use: pata_atiixp
    Kernel modules: pata_atiixp
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel
00:14.3 ISA bridge: ATI Technologies Inc SB700/SB800 LPC host controller
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:14.5 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI2 Controller
    Kernel driver in use: ohci_hcd
00:18.0 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] HyperTransport Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] DRAM Controller
    Kernel modules: amd64_edac_mod
00:18.3 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] Link Control
01:05.0 VGA compatible controller: ATI Technologies Inc 760G [Radeon 3000]
    Kernel driver in use: fglrx_pci
    Kernel modules: fglrx, radeon
01:05.1 Audio device: ATI Technologies Inc RS780 Azalia controller
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 03)
    Kernel driver in use: r8169
    Kernel modules: r8169
```USB devices:
```
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 003: ID 15d9:0a4c Dexon 
Bus 004 Device 002: ID 1c4f:0002 SiGma Micro 
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```lsmod output:```
lsmod
Module                  Size  Used by
ipt_MASQUERADE          1863  1 
iptable_nat             4268  1 
binfmt_misc             7960  1 
vboxnetadp              5235  0 
vboxnetflt             12242  0 
vboxdrv              1768311  2 vboxnetadp,vboxnetflt
snd_hda_codec_atihdmi     3023  1 
snd_hda_codec_via      33207  1 
ipt_REJECT              2384  1 
ipt_LOG                 5370  5 
xt_multiport            2794  1 
xt_limit                2180  7 
xt_tcpudp               2667  11 
ipt_addrtype            2055  4 
xt_state                1490  7 
ip6table_filter         1712  1 
ip6_tables             19428  1 ip6table_filter
snd_hda_intel          25805  2 
snd_hda_codec          85759  3 snd_hda_codec_atihdmi,snd_hda_codec_via,snd_hda_intel
snd_hwdep               6924  1 snd_hda_codec
snd_pcm_oss            41394  0 
snd_mixer_oss          16299  1 snd_pcm_oss
nf_nat_irc              1577  0 
snd_seq_dummy           1782  0 
snd_pcm                87946  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
nf_conntrack_irc        4429  1 nf_nat_irc
snd_seq_oss            31191  0 
nf_nat_ftp              2513  0 
nf_nat                 19286  4 ipt_MASQUERADE,iptable_nat,nf_nat_irc,nf_nat_ftp
nf_conntrack_ipv4      12742  10 iptable_nat,nf_nat
snd_seq_midi            5829  0 
nf_defrag_ipv4          1481  1 nf_conntrack_ipv4
snd_rawmidi            23420  1 snd_seq_midi
nf_conntrack_ftp        7126  1 nf_nat_ftp
snd_seq_midi_event      7267  2 snd_seq_oss,snd_seq_midi
nf_conntrack           73326  9 ipt_MASQUERADE,iptable_nat,xt_state,nf_nat_irc,nf_conntrack_irc,nf_nat_ftp,nf_nat,nf_conntrack_ipv4,nf_conntrack_ftp
snd_seq                57481  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
iptable_filter          1841  1 
snd_timer              23649  2 snd_pcm,snd_seq
snd_seq_device          6888  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
ip_tables              18201  2 iptable_nat,iptable_filter
ppdev                   6375  0 
fglrx                2562903  39 
vga16fb                12757  0 
hwmon_vid               3130  0 
x_tables               22361  11 ipt_MASQUERADE,iptable_nat,ipt_REJECT,ipt_LOG,xt_multiport,xt_limit,xt_tcpudp,ipt_addrtype,xt_state,ip6_tables,ip_tables
parport_pc             29958  1 
asus_atk0110           10033  0 
joydev                 11104  0 
vgastate                9857  1 vga16fb
snd                    71283  15 snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
psmouse                65040  0 
serio_raw               4918  0 
edac_core              45423  0 
edac_mce_amd            9278  0 
i2c_piix4               9639  0 
soundcore               8052  1 snd
snd_page_alloc          8500  2 snd_hda_intel,snd_pcm
shpchp                 33711  0 
lp                      9336  0 
parport                37160  3 ppdev,parport_pc,lp
fbcon                  39270  71 
tileblit                2487  1 fbcon
font                    8053  1 fbcon
bitblit                 5811  1 fbcon
softcursor              1565  1 bitblit
uvesafb                24962  1 
usbhid                 41116  0 
hid                    83888  1 usbhid
pata_atiixp             4209  0 
r8169                  39714  0 
mii                     5237  1 r8169
ahci                   38030  6
```

---

### Post by pqwoerituytrueiwoq on 2011-10-01
any suggestions
the mouse tends to jump to a edge of a screen and not want to come off will i pick the mouse up and put it down could this be a driver issue with the mouse or just be the mouse hating the cute kitten mouse pad

---

### Post by pqwoerituytrueiwoq on 2011-10-06
it would be nice to know how to fix this...
oh look, paint is drying
:popcorn:

---

### Post by pqwoerituytrueiwoq on 2011-10-10
the keyboard really acts up after suspend (have to type slow and numlock stops working)

---

### Post by linuxford on 2011-10-10
This doesn't really address your question, but if you are new like me then perhaps it might be indirectly helpful. Oooppsss, I see you have 1600+ beans, oohh... well it is a cool tutorial anyhow, so here it is:

[http://www.linuxplanet.com/linuxplanet/tutorials/1019/1]("http://www.linuxplanet.com/linuxplanet/tutorials/1019/1")

---

### Post by pqwoerituytrueiwoq on 2011-10-15
after i wake from suspend it happens again but it messes up my keyboard (forced to type really slow/no keyboard lights/no keyboard shortcuts)
keyboard is a [RK-700M]("http://www.newegg.com/Product/Product.aspx?Item=N82E16823201039")
```
[  146.740539] ACPI: Waking up from system sleep state S3
[  146.742132] pci 0000:00:01.0: restoring config space at offset 0x7 (was 0x2220d1d1, writing 0x220d1d1)
[  146.742150] pcieport 0000:00:0a.0: restoring config space at offset 0x1 (was 0x100107, writing 0x100507)
[  146.742170] ahci 0000:00:11.0: restoring config space at offset 0xf (was 0x100, writing 0x10b)
[  146.742186] ahci 0000:00:11.0: restoring config space at offset 0x2 (was 0x1018f00, writing 0x1060100)
[  146.742204] ahci 0000:00:11.0: set SATA to AHCI mode
[  146.742229] ohci_hcd 0000:00:12.0: wake-up capability disabled by ACPI
[  146.742252] ohci_hcd 0000:00:12.1: wake-up capability disabled by ACPI
[  146.760885] ehci_hcd 0000:00:12.2: restoring config space at offset 0x1 (was 0x2b00000, writing 0x2b00112)
[  146.760904] ehci_hcd 0000:00:12.2: wake-up capability disabled by ACPI
[  146.760908] ehci_hcd 0000:00:12.2: PME# disabled
[  146.760932] ohci_hcd 0000:00:13.0: wake-up capability disabled by ACPI
[  146.760955] ohci_hcd 0000:00:13.1: wake-up capability disabled by ACPI
[  146.780885] ehci_hcd 0000:00:13.2: restoring config space at offset 0x1 (was 0x2b00000, writing 0x2b00112)
[  146.780904] ehci_hcd 0000:00:13.2: wake-up capability disabled by ACPI
[  146.780907] ehci_hcd 0000:00:13.2: PME# disabled
[  146.780954] pata_atiixp 0000:00:14.1: restoring config space at offset 0x3 (was 0x0, writing 0x4000)
[  146.780972] HDA Intel 0000:00:14.2: restoring config space at offset 0xf (was 0x10a, writing 0xa)
[  146.780989] HDA Intel 0000:00:14.2: restoring config space at offset 0x1 (was 0x4100006, writing 0x4100002)
[  146.781059] ohci_hcd 0000:00:14.5: wake-up capability disabled by ACPI
[  146.781083] fglrx_pci 0000:01:05.0: restoring config space at offset 0xf (was 0x1ff, writing 0x10a)
[  146.781091] fglrx_pci 0000:01:05.0: restoring config space at offset 0x3 (was 0x800000, writing 0x800010)
[  146.781094] fglrx_pci 0000:01:05.0: restoring config space at offset 0x1 (was 0x40100107, writing 0x100503)
[  146.781109] HDA Intel 0000:01:05.1: restoring config space at offset 0xf (was 0x2ff, writing 0x20a)
[  146.781116] HDA Intel 0000:01:05.1: restoring config space at offset 0x4 (was 0x0, writing 0xfeae8000)
[  146.781118] HDA Intel 0000:01:05.1: restoring config space at offset 0x3 (was 0x800000, writing 0x800010)
[  146.781121] HDA Intel 0000:01:05.1: restoring config space at offset 0x1 (was 0x100000, writing 0x100103)
[  146.781143] r8169 0000:02:00.0: restoring config space at offset 0xf (was 0x1ff, writing 0x10a)
[  146.781149] r8169 0000:02:00.0: restoring config space at offset 0xc (was 0x0, writing 0xfebf0000)
[  146.781155] r8169 0000:02:00.0: restoring config space at offset 0x8 (was 0xc, writing 0xfdff800c)
[  146.781159] r8169 0000:02:00.0: restoring config space at offset 0x6 (was 0xc, writing 0xfdfff00c)
[  146.781164] r8169 0000:02:00.0: restoring config space at offset 0x4 (was 0x1, writing 0xe801)
[  146.781167] r8169 0000:02:00.0: restoring config space at offset 0x3 (was 0x0, writing 0x10)
[  146.781171] r8169 0000:02:00.0: restoring config space at offset 0x1 (was 0x100000, writing 0x100507)
[  146.781229] PM: early resume of devices complete after 39.121 msecs
[  146.781290] ahci 0000:00:11.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[  146.781388] ohci_hcd 0000:00:12.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[  146.810868] ohci_hcd 0000:00:12.1: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[  146.840029] ehci_hcd 0000:00:12.2: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[  146.840040] ohci_hcd 0000:00:13.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[  146.870034] ohci_hcd 0000:00:13.1: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[  146.900029] ehci_hcd 0000:00:13.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[  146.900058] HDA Intel 0000:00:14.2: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[  146.900086] ohci_hcd 0000:00:14.5: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[  146.930042] fglrx_pci 0000:01:05.0: setting latency timer to 64
[  146.933128] [fglrx] Power up the ASIC
[  146.933146] [fglrx] Preparing resume fglrx in kernel.
[  146.964744] [fglrx] Resuming fglrx in kernel completed.
[  146.964933] [fglrx] IRQ 26 Enabled
[  146.964945] HDA Intel 0000:01:05.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[  146.964948] HDA Intel 0000:01:05.1: setting latency timer to 64
[  146.964962] r8169 0000:02:00.0: PME# disabled
[  146.966780] parport_pc 00:06: activated
[  146.968053] serial 00:08: activated
[  147.120874] ata4: SATA link down (SStatus 0 SControl 300)
[  147.130047] ata2: SATA link down (SStatus 0 SControl 300)
[  147.130875] PM: resume of drv:usb dev:usb1 complete after 162.748 msecs
[  147.300041] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[  147.301187] ata3.00: configured for UDMA/100
[  147.390029] PM: resume of drv:usb dev:usb4 complete after 219.986 msecs
[  147.700025] usb 4-2: reset low speed USB device using ohci_hcd and address 2
[  148.042625] PM: resume of drv:usb dev:4-2 complete after 652.518 msecs
[  148.042641] sd 0:0:0:0: [sda] Starting disk
[  151.140046] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[  151.141767] ata1.00: configured for UDMA/100
[  151.189179] PM: resume of drv:sd dev:0:0:0:0 complete after 3146.535 msecs
[  151.241225] PM: resume of devices complete after 4459.971 msecs
[  151.241345] PM: resume devices took 4.460 seconds
[  151.241368] PM: Finishing wakeup.
[  151.241369] Restarting tasks ... done.
[  151.538873] r8169: eth0: link up
[  152.113809] CPU0 attaching NULL sched-domain.
[  152.113813] CPU1 attaching NULL sched-domain.
[  152.171058] CPU0 attaching sched-domain:
[  152.171067]  domain 0: span 0-1 level MC
[  152.171074]   groups: 0 1
[  152.171085] CPU1 attaching sched-domain:
[  152.171090]  domain 0: span 0-1 level MC
[  152.171095]   groups: 1 0
[  162.500025] eth0: no IPv6 routers present
[  243.694999] usb 4-2: ctrl urb status -62 received
[  243.695988] usb 4-2: ctrl urb status -62 received
[  243.696356] usb 4-2: USB disconnect, address 2
[  243.696987] usb 4-2: ctrl urb status -62 received
[  243.696996] /build/buildd/linux-2.6.32/drivers/hid/usbhid/hid-core.c: usb_submit_urb(ctrl) failed
[  247.680908] usb 4-2: new low speed USB device using ohci_hcd and address 4
[  247.891576] usb 4-2: configuration #1 chosen from 1 choice
[  247.899528] input: USB USB Keykoard as /devices/pci0000:00/0000:00:12.1/usb4/4-2/4-2:1.0/input/input6
[  247.907730] generic-usb 0003:1C4F:0002.0004: input,hidraw0: USB HID v1.10 Keyboard [USB USB Keykoard] on usb-0000:00:12.1-2/input0
[  257.911009] /build/buildd/linux-2.6.32/drivers/hid/usbhid/hid-core.c: usb_submit_urb(ctrl) failed
[  257.911048] generic-usb 0003:1C4F:0002.0005: timeout initializing reports
[  257.911286] input: USB USB Keykoard as /devices/pci0000:00/0000:00:12.1/usb4/4-2/4-2:1.1/input/input7
[  257.911469] generic-usb 0003:1C4F:0002.0005: input,hidraw1: USB HID v1.10 Device [USB USB Keykoard] on usb-0000:00:12.1-2/input1
```the only way i have found to get the keyboard to work properly is to either reboot or unplug the keyboard and plug it back in

---

### Post by pqwoerituytrueiwoq on 2011-10-30
ideas anyone?

---

### Post by pqwoerituytrueiwoq on 2011-12-06
anyone know a way i can reset the keyboard (like simulate unpluging and plugging it back in) when it comes out of supend?
edit is it a USB keyboard

---

### Post by pqwoerituytrueiwoq on 2011-12-10
is a work around too much to ask?

---

### Post by pqwoerituytrueiwoq on 2011-12-13
great now the number keypad wants to not work without unplugging it and plugging it back in
how can i update the keyboard driver on lucid?
the keyboard is labeled as compatible with windows 2000 through vista and it has no cd

---

