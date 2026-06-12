---
title: "Skype call issues"
date: 2010-10-12
forum: General Help
---

### Post by playcat on 2010-10-12
Hello,

I'm sorry if I wrongly placed this post, since skype is 3rd party software, but I hope to get some answers, anyway.

The problem I'm encountering is, actually, quite old with me and skype on ubuntu :). I have windows 7 and ubuntu 10.10 (from yesterday) on my laptop. Laptop itself is HP 6735s. Not a 'beast', but works just fine for everything I need - from development to surfing / movies / ... (I'll attach my dmesg output at the bottom of the message).

When I boot to windows, everything works good - sound is great on both ends. However, situation is totally opposite when ubuntu skype version is used - sound 'breaks', there is occasional noise, echo, etc. 
When I call skype test, everything goes well (more or less). Even if there are some problems, there are tolerable.

Any ideas???

Thx,
Dan

DMESG:
> [    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.35-22-generic (buildd@crested) (gcc version 4.4.5 (Ubuntu/Linaro 4.4.4-14ubuntu5) ) #34-Ubuntu SMP Sun Oct 10 09:26:05 UTC 2010 (Ubuntu 2.6.35-22.34-generic 2.6.35.4)
[    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-2.6.35-22-generic root=UUID=0753499a-c2ae-4de0-a4ba-2e3eb40cb814 ro quiet splash
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000ef000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 00000000acb70000 (usable)
[    0.000000]  BIOS-e820: 00000000acb70000 - 00000000acb80000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000acb80000 - 00000000afd4f000 (usable)
[    0.000000]  BIOS-e820: 00000000afd4f000 - 00000000afdcf000 (reserved)
[    0.000000]  BIOS-e820: 00000000afdcf000 - 00000000afecf000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000afecf000 - 00000000afeff000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000afeff000 - 00000000aff00000 (usable)
[    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000feb00000 - 00000000feb01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000ffe00000 - 0000000100000000 (reserved)
[    0.000000]  BIOS-e820: 0000000100000000 - 0000000140000000 (usable)
[    0.000000] NX (Execute Disable) protection: active
[    0.000000] DMI 2.4 present.
[    0.000000] e820 update range: 0000000000000000 - 0000000000001000 (usable) ==> (reserved)
[    0.000000] e820 remove range: 00000000000a0000 - 0000000000100000 (usable)
[    0.000000] No AGP bridge found
[    0.000000] last_pfn = 0x140000 max_arch_pfn = 0x400000000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 0000000000 mask FF80000000 write-back
[    0.000000]   1 base 0080000000 mask FFE0000000 write-back
[    0.000000]   2 base 00A0000000 mask FFF0000000 write-back
[    0.000000]   3 base 0100000000 mask FFC0000000 write-back
[    0.000000]   4 base 00FFE00000 mask FFFFE00000 write-protect
[    0.000000]   5 base 00FFF40000 mask FFFFFF0000 write-protect
[    0.000000]   6 base 00ACB70000 mask FFFFFF0000 uncachable
[    0.000000]   7 disabled
[    0.000000] TOM2: 0000000140000000 aka 5120M
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] last_pfn = 0xaff00 max_arch_pfn = 0x400000000
[    0.000000] e820 update range: 0000000000001000 - 0000000000010000 (usable) ==> (reserved)
[    0.000000] Scanning 1 areas for low memory corruption
[    0.000000] modified physical RAM map:
[    0.000000]  modified: 0000000000000000 - 0000000000010000 (reserved)
[    0.000000]  modified: 0000000000010000 - 000000000009fc00 (usable)
[    0.000000]  modified: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  modified: 00000000000ef000 - 0000000000100000 (reserved)
[    0.000000]  modified: 0000000000100000 - 00000000acb70000 (usable)
[    0.000000]  modified: 00000000acb70000 - 00000000acb80000 (ACPI NVS)
[    0.000000]  modified: 00000000acb80000 - 00000000afd4f000 (usable)
[    0.000000]  modified: 00000000afd4f000 - 00000000afdcf000 (reserved)
[    0.000000]  modified: 00000000afdcf000 - 00000000afecf000 (ACPI NVS)
[    0.000000]  modified: 00000000afecf000 - 00000000afeff000 (ACPI data)
[    0.000000]  modified: 00000000afeff000 - 00000000aff00000 (usable)
[    0.000000]  modified: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  modified: 00000000feb00000 - 00000000feb01000 (reserved)
[    0.000000]  modified: 00000000fec00000 - 00000000fec01000 (reserved)
[    0.000000]  modified: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  modified: 00000000ffe00000 - 0000000100000000 (reserved)
[    0.000000]  modified: 0000000100000000 - 0000000140000000 (usable)
[    0.000000] initial memory mapped : 0 - 20000000
[    0.000000] init_memory_mapping: 0000000000000000-00000000aff00000
[    0.000000]  0000000000 - 00afe00000 page 2M
[    0.000000]  00afe00000 - 00aff00000 page 4k
[    0.000000] kernel direct mapping tables up to aff00000 @ 16000-1b000
[    0.000000] init_memory_mapping: 0000000100000000-0000000140000000
[    0.000000]  0100000000 - 0140000000 page 2M
[    0.000000] kernel direct mapping tables up to 140000000 @ 19000-1f000
[    0.000000] RAMDISK: 37571000 - 37ff0000
[    0.000000] ACPI: RSDP 00000000000f68c0 00014 (v00 HP    )
[    0.000000] ACPI: RSDT 00000000afefe038 00038 (v01 HPQOEM SLIC-MPC 00000003      01000013)
[    0.000000] ACPI: FACP 00000000afefd000 00074 (v01 HP     0944     00000003 HP   00000001)
[    0.000000] ACPI: DSDT 00000000afee3000 164D6 (v01 HP     0944     00000001 HP   00000001)
[    0.000000] ACPI: FACS 00000000afea1000 00040
[    0.000000] ACPI: APIC 00000000afefc000 00084 (v01 HP     0944     00000001 HP   00000001)
[    0.000000] ACPI: MCFG 00000000afefb000 0003C (v01 HP     0944     00000001 HP   00000001)
[    0.000000] ACPI: HPET 00000000afee1000 00038 (v01 HP     0944     00000001 HP   00000001)
[    0.000000] ACPI: SSDT 00000000afee0000 00386 (v01 AMD    PowerNow 00000001 AMD  00000001)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] Scanning NUMA topology in Northbridge 24
[    0.000000] No NUMA configuration found
[    0.000000] Faking a node at 0000000000000000-0000000140000000
[    0.000000] Initmem setup node 0 0000000000000000-0000000140000000
[    0.000000]   NODE_DATA [0000000100000000 - 0000000100004fff]
[    0.000000]  [ffffea0000000000-ffffea00045fffff] PMD -> [ffff880100200000-ffff8801037fffff] on node 0
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000010 -> 0x00001000
[    0.000000]   DMA32    0x00001000 -> 0x00100000
[    0.000000]   Normal   0x00100000 -> 0x00140000
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[5] active PFN ranges
[    0.000000]     0: 0x00000010 -> 0x0000009f
[    0.000000]     0: 0x00000100 -> 0x000acb70
[    0.000000]     0: 0x000acb80 -> 0x000afd4f
[    0.000000]     0: 0x000afeff -> 0x000aff00
[    0.000000]     0: 0x00100000 -> 0x00140000
[    0.000000] On node 0 totalpages: 982223
[    0.000000]   DMA zone: 56 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3927 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 14280 pages used for memmap
[    0.000000]   DMA32 zone: 701816 pages, LIFO batch:31
[    0.000000]   Normal zone: 3584 pages used for memmap
[    0.000000]   Normal zone: 258560 pages, LIFO batch:31
[    0.000000] ACPI: PM-Timer IO Port: 0x408
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x00] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x00] disabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x02] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x03] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x04] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x04] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 4, version 33, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 low level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x43538301 base: 0xfed00000
[    0.000000] SMP: Allowing 4 CPUs, 2 hotplug CPUs
[    0.000000] nr_irqs_gsi: 40
[    0.000000] early_res array is doubled to 64 at [1a000 - 1a7ff]
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000ef000
[    0.000000] PM: Registered nosave memory: 00000000000ef000 - 0000000000100000
[    0.000000] PM: Registered nosave memory: 00000000acb70000 - 00000000acb80000
[    0.000000] PM: Registered nosave memory: 00000000afd4f000 - 00000000afdcf000
[    0.000000] PM: Registered nosave memory: 00000000afdcf000 - 00000000afecf000
[    0.000000] PM: Registered nosave memory: 00000000afecf000 - 00000000afeff000
[    0.000000] PM: Registered nosave memory: 00000000aff00000 - 00000000e0000000
[    0.000000] PM: Registered nosave memory: 00000000e0000000 - 00000000f0000000
[    0.000000] PM: Registered nosave memory: 00000000f0000000 - 00000000feb00000
[    0.000000] PM: Registered nosave memory: 00000000feb00000 - 00000000feb01000
[    0.000000] PM: Registered nosave memory: 00000000feb01000 - 00000000fec00000
[    0.000000] PM: Registered nosave memory: 00000000fec00000 - 00000000fec01000
[    0.000000] PM: Registered nosave memory: 00000000fec01000 - 00000000fee00000
[    0.000000] PM: Registered nosave memory: 00000000fee00000 - 00000000fee01000
[    0.000000] PM: Registered nosave memory: 00000000fee01000 - 00000000ffe00000
[    0.000000] PM: Registered nosave memory: 00000000ffe00000 - 0000000100000000
[    0.000000] Allocating PCI resources starting at aff00000 (gap: aff00000:30100000)
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] setup_percpu: NR_CPUS:64 nr_cpumask_bits:64 nr_cpu_ids:4 nr_node_ids:1
[    0.000000] PERCPU: Embedded 30 pages/cpu @ffff880001e00000 s91520 r8192 d23168 u524288
[    0.000000] pcpu-alloc: s91520 r8192 d23168 u524288 alloc=1*2097152
[    0.000000] pcpu-alloc: [0] 0 1 2 3 
[    0.000000] early_res array is doubled to 128 at [1a800 - 1b7ff]
[    0.000000] Built 1 zonelists in Node order, mobility grouping on.  Total pages: 964303
[    0.000000] Policy zone: Normal
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.35-22-generic root=UUID=0753499a-c2ae-4de0-a4ba-2e3eb40cb814 ro quiet splash
[    0.000000] PID hash table entries: 4096 (order: 3, 32768 bytes)
[    0.000000] Checking aperture...
[    0.000000] No AGP bridge found
[    0.000000] Calgary: detecting Calgary via BIOS EBDA area
[    0.000000] Calgary: Unable to locate Rio Grande table in EBDA - bailing!
[    0.000000] Subtract (60 early reservations)
[    0.000000]   #1 [0001000000 - 0001d17114]   TEXT DATA BSS
[    0.000000]   #2 [0037571000 - 0037ff0000]         RAMDISK
[    0.000000]   #3 [000009fc00 - 0000100000]   BIOS reserved
[    0.000000]   #4 [0001d18000 - 0001d181dc]             BRK
[    0.000000]   #5 [0000010000 - 0000012000]      TRAMPOLINE
[    0.000000]   #6 [0000012000 - 0000016000]     ACPI WAKEUP
[    0.000000]   #7 [0000016000 - 0000019000]         PGTABLE
[    0.000000]   #8 [0000019000 - 000001a000]         PGTABLE
[    0.000000]   #9 [0100000000 - 0100005000]       NODE_DATA
[    0.000000]   #10 [0001d18200 - 0001d19200]         BOOTMEM
[    0.000000]   #11 [0001d17140 - 0001d17410]         BOOTMEM
[    0.000000]   #12 [0100005000 - 0100006000]         BOOTMEM
[    0.000000]   #13 [0100006000 - 0100007000]         BOOTMEM
[    0.000000]   #14 [0100200000 - 0103800000]        MEMMAP 0
[    0.000000]   #15 [0001d17440 - 0001d175c0]         BOOTMEM
[    0.000000]   #16 [0001d19200 - 0001d31200]         BOOTMEM
[    0.000000]   #17 [0001d31200 - 0001d37200]         BOOTMEM
[    0.000000]   #18 [0001d38000 - 0001d39000]         BOOTMEM
[    0.000000]   #19 [0001d175c0 - 0001d17601]         BOOTMEM
[    0.000000]   #20 [0001d17640 - 0001d17683]         BOOTMEM
[    0.000000]   #21 [0001d176c0 - 0001d17a78]         BOOTMEM
[    0.000000]   #22 [0001d17a80 - 0001d17ae8]         BOOTMEM
[    0.000000]   #23 [0001d17b00 - 0001d17b68]         BOOTMEM
[    0.000000]   #24 [0001d17b80 - 0001d17be8]         BOOTMEM
[    0.000000]   #25 [0001d17c00 - 0001d17c68]         BOOTMEM
[    0.000000]   #26 [0001d17c80 - 0001d17ce8]         BOOTMEM
[    0.000000]   #27 [0001d17d00 - 0001d17d68]         BOOTMEM
[    0.000000]   #28 [0001d17d80 - 0001d17de8]         BOOTMEM
[    0.000000]   #29 [0001d17e00 - 0001d17e68]         BOOTMEM
[    0.000000]   #30 [0001d17e80 - 0001d17ee8]         BOOTMEM
[    0.000000]   #31 [0001d17f00 - 0001d17f68]         BOOTMEM
[    0.000000]   #32 [0001d17f80 - 0001d17fe8]         BOOTMEM
[    0.000000]   #33 [0001d37200 - 0001d37268]         BOOTMEM
[    0.000000]   #34 [0001d37280 - 0001d372e8]         BOOTMEM
[    0.000000]   #35 [0001d37300 - 0001d37368]         BOOTMEM
[    0.000000]   #36 [0001d37380 - 0001d373e8]         BOOTMEM
[    0.000000]   #37 [0001d37400 - 0001d37468]         BOOTMEM
[    0.000000]   #38 [0001d37480 - 0001d374a0]         BOOTMEM
[    0.000000]   #39 [0001d374c0 - 0001d374e0]         BOOTMEM
[    0.000000]   #40 [0001d37500 - 0001d37520]         BOOTMEM
[    0.000000]   #41 [0001d37540 - 0001d37560]         BOOTMEM
[    0.000000]   #42 [0001d37580 - 0001d375ea]         BOOTMEM
[    0.000000]   #43 [0001d37600 - 0001d3766a]         BOOTMEM
[    0.000000]   #44 [0001e00000 - 0001e1e000]         BOOTMEM
[    0.000000]   #45 [0001e80000 - 0001e9e000]         BOOTMEM
[    0.000000]   #46 [0001f00000 - 0001f1e000]         BOOTMEM
[    0.000000]   #47 [0001f80000 - 0001f9e000]         BOOTMEM
[    0.000000]   #48 [0001d37680 - 0001d37688]         BOOTMEM
[    0.000000]   #49 [0001d376c0 - 0001d376c8]         BOOTMEM
[    0.000000]   #50 [0001d37700 - 0001d37710]         BOOTMEM
[    0.000000]   #51 [0001d37740 - 0001d37760]         BOOTMEM
[    0.000000]   #52 [0001d37780 - 0001d378b0]         BOOTMEM
[    0.000000]   #53 [0001d378c0 - 0001d37910]         BOOTMEM
[    0.000000]   #54 [0001d37940 - 0001d37990]         BOOTMEM
[    0.000000]   #55 [0001d39000 - 0001d41000]         BOOTMEM
[    0.000000]   #56 [0001f9e000 - 0005f9e000]         BOOTMEM
[    0.000000]   #57 [0001d41000 - 0001d61000]         BOOTMEM
[    0.000000]   #58 [0001d61000 - 0001da1000]         BOOTMEM
[    0.000000]   #59 [000001b800 - 0000023800]         BOOTMEM
[    0.000000] Memory: 3782772k/5242880k available (5708k kernel code, 1313988k absent, 146120k reserved, 5382k data, 908k init)
[    0.000000] SLUB: Genslabs=14, HWalign=64, Order=0-3, MinObjects=0, CPUs=4, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000] 	RCU dyntick-idle grace-period acceleration is enabled.
[    0.000000] 	RCU-based detection of stalled CPUs is disabled.
[    0.000000] 	Verbose stalled-CPUs detection is disabled.
[    0.000000] NR_IRQS:4352 nr_irqs:712
[    0.000000] spurious 8259A interrupt: IRQ7.
[    0.000000] Console: colour VGA+ 80x25
[    0.000000] console [tty0] enabled
[    0.000000] allocated 39321600 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] hpet clockevent registered
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 2000.176 MHz processor.
[    0.030010] Calibrating delay loop (skipped), value calculated using timer frequency.. 4000.34 BogoMIPS (lpj=20001730)
[    0.030016] pid_max: default: 32768 minimum: 301
[    0.030059] Security Framework initialized
[    0.030080] AppArmor: AppArmor initialized
[    0.030082] Yama: becoming mindful.
[    0.030626] Dentry cache hash table entries: 524288 (order: 10, 4194304 bytes)
[    0.033282] Inode-cache hash table entries: 262144 (order: 9, 2097152 bytes)
[    0.034506] Mount-cache hash table entries: 256
[    0.034668] Initializing cgroup subsys ns
[    0.034672] Initializing cgroup subsys cpuacct
[    0.034678] Initializing cgroup subsys memory
[    0.034689] Initializing cgroup subsys devices
[    0.034691] Initializing cgroup subsys freezer
[    0.034694] Initializing cgroup subsys net_cls
[    0.034725] tseg: 00aff00000
[    0.034728] CPU: Physical Processor ID: 0
[    0.034730] CPU: Processor Core ID: 0
[    0.034732] mce: CPU supports 5 MCE banks
[    0.034745] Performance Events: AMD PMU driver.
[    0.034751] ... version:                0
[    0.034753] ... bit width:              48
[    0.034755] ... generic registers:      4
[    0.034757] ... value mask:             0000ffffffffffff
[    0.034759] ... max period:             00007fffffffffff
[    0.034761] ... fixed-purpose events:   0
[    0.034762] ... event mask:             000000000000000f
[    0.037224] ACPI: Core revision 20100428
[    0.060041] ftrace: converting mcount calls to 0f 1f 44 00 00
[    0.060054] ftrace: allocating 22680 entries in 89 pages
[    0.070102] Setting APIC routing to flat
[    0.070501] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.177139] CPU0: AMD Turion(tm)X2 Dual Core Mobile RM-70 stepping 01
[    0.180000] Booting Node   0, Processors  #1
[    0.340000] TSC synchronization [CPU#0 -> CPU#1]:
[    0.340000] Measured 16893145 cycles TSC warp between CPUs, turning off TSC clock.
[    0.340000] Marking TSC unstable due to check_tsc_sync_source failed
[    0.340010] Brought up 2 CPUs
[    0.340012] Total of 2 processors activated (7990.36 BogoMIPS).
[    0.340280] devtmpfs: initialized
[    0.340999] regulator: core version 0.5
[    0.341066] Time: 20:46:43  Date: 10/12/10
[    0.341124] NET: Registered protocol family 16
[    0.341288] TOM: 00000000c0000000 aka 3072M
[    0.341291] Fam 10h mmconf [e0000000, efffffff]
[    0.341300] TOM2: 0000000140000000 aka 5120M
[    0.341312] ACPI: bus type pci registered
[    0.341437] PCI: MMCONFIG for domain 0000 [bus 00-ff] at [mem 0xe0000000-0xefffffff] (base 0xe0000000)
[    0.341441] PCI: MMCONFIG at [mem 0xe0000000-0xefffffff] reserved in E820
[    0.374150] Trying to unpack rootfs image as initramfs...
[    0.378164] PCI: Using configuration type 1 for base access
[    0.390358] bio: create slab <bio-0> at 0
[    0.392637] ACPI: EC: Look up EC in DSDT
[    0.664729] Freeing initrd memory: 10748k freed
[    1.050176] ACPI: Interpreter enabled
[    1.050183] ACPI: (supports S0 S3 S4 S5)
[    1.050209] ACPI: Using IOAPIC for interrupt routing
[    1.073402] ACPI: EC: GPE = 0x11, I/O: command/status = 0x66, data = 0x62
[    1.080071] ACPI: Power Resource [APPR] (off)
[    1.080172] ACPI: Power Resource [PFN0] (off)
[    1.080261] ACPI: Power Resource [PFN1] (off)
[    1.080350] ACPI: Power Resource [PFN2] (off)
[    1.080439] ACPI: Power Resource [PFN3] (off)
[    1.080977] ACPI: No dock devices found.
[    1.080982] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
[    1.081207] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-ff])
[    1.081648] pci_root PNP0A03:00: host bridge window [io  0x0000-0x0cf7]
[    1.081651] pci_root PNP0A03:00: host bridge window [io  0x0d00-0xffff]
[    1.081654] pci_root PNP0A03:00: host bridge window [mem 0x000a0000-0x000bffff]
[    1.081657] pci_root PNP0A03:00: host bridge window [mem 0x000c0000-0x000c3fff]
[    1.081660] pci_root PNP0A03:00: host bridge window [mem 0x000c4000-0x000c7fff]
[    1.081663] pci_root PNP0A03:00: host bridge window [mem 0x000c8000-0x000cbfff]
[    1.081666] pci_root PNP0A03:00: host bridge window [mem 0x000cc000-0x000cffff]
[    1.081668] pci_root PNP0A03:00: host bridge window [mem 0x000d0000-0x000d3fff]
[    1.081671] pci_root PNP0A03:00: host bridge window [mem 0x000d4000-0x000d7fff]
[    1.081674] pci_root PNP0A03:00: host bridge window [mem 0x000d8000-0x000dbfff]
[    1.081677] pci_root PNP0A03:00: host bridge window [mem 0x000dc000-0x000dffff]
[    1.081680] pci_root PNP0A03:00: host bridge window [mem 0x000e0000-0x000e3fff]
[    1.081683] pci_root PNP0A03:00: host bridge window [mem 0x000e4000-0x000e7fff]
[    1.081686] pci_root PNP0A03:00: host bridge window [mem 0x000e8000-0x000ebfff]
[    1.081689] pci_root PNP0A03:00: address space collision: host bridge window [mem 0x000ec000-0x000effff] conflicts with reserved [mem 0x000ef000-0x000fffff]
[    1.081693] pci_root PNP0A03:00: host bridge window [mem 0xc0000000-0xdfffffff]
[    1.081696] pci_root PNP0A03:00: host bridge window [mem 0xf0000000-0xfffdffff]
[    1.081700] pci_root PNP0A03:00: address space collision: host bridge window [mem 0xffe00000-0xffffffff] conflicts with PCI Bus 0000:00 [mem 0xf0000000-0xfffdffff]
[    1.081910] pci 0000:00:04.0: PME# supported from D0 D3hot D3cold
[    1.081914] pci 0000:00:04.0: PME# disabled
[    1.082011] pci 0000:00:07.0: PME# supported from D0 D3hot D3cold
[    1.082015] pci 0000:00:07.0: PME# disabled
[    1.082110] pci 0000:00:09.0: PME# supported from D0 D3hot D3cold
[    1.082114] pci 0000:00:09.0: PME# disabled
[    1.082205] pci 0000:00:11.0: reg 10: [io  0x6018-0x601f]
[    1.082214] pci 0000:00:11.0: reg 14: [io  0x6024-0x6027]
[    1.082222] pci 0000:00:11.0: reg 18: [io  0x6010-0x6017]
[    1.082230] pci 0000:00:11.0: reg 1c: [io  0x6020-0x6023]
[    1.082239] pci 0000:00:11.0: reg 20: [io  0x6000-0x600f]
[    1.082247] pci 0000:00:11.0: reg 24: [mem 0xd4409000-0xd44093ff]
[    1.082270] pci 0000:00:11.0: set SATA to AHCI mode
[    1.082324] pci 0000:00:12.0: reg 10: [mem 0xd4408000-0xd4408fff]
[    1.082391] pci 0000:00:12.1: reg 10: [mem 0xd4407000-0xd4407fff]
[    1.082473] pci 0000:00:12.2: reg 10: [mem 0xd4409500-0xd44095ff]
[    1.082537] pci 0000:00:12.2: supports D1 D2
[    1.082539] pci 0000:00:12.2: PME# supported from D0 D1 D2 D3hot
[    1.082545] pci 0000:00:12.2: PME# disabled
[    1.082583] pci 0000:00:13.0: reg 10: [mem 0xd4406000-0xd4406fff]
[    1.082650] pci 0000:00:13.1: reg 10: [mem 0xd4405000-0xd4405fff]
[    1.082733] pci 0000:00:13.2: reg 10: [mem 0xd4409400-0xd44094ff]
[    1.082797] pci 0000:00:13.2: supports D1 D2
[    1.082800] pci 0000:00:13.2: PME# supported from D0 D1 D2 D3hot
[    1.082805] pci 0000:00:13.2: PME# disabled
[    1.082948] pci 0000:00:14.2: reg 10: [mem 0xd4400000-0xd4403fff 64bit]
[    1.083001] pci 0000:00:14.2: PME# supported from D0 D3hot D3cold
[    1.083006] pci 0000:00:14.2: PME# disabled
[    1.083134] pci 0000:00:14.5: reg 10: [mem 0xd4404000-0xd4404fff]
[    1.083434] pci 0000:01:05.0: reg 10: [mem 0xc0000000-0xcfffffff pref]
[    1.083440] pci 0000:01:05.0: reg 14: [io  0x5000-0x50ff]
[    1.083445] pci 0000:01:05.0: reg 18: [mem 0xd4300000-0xd430ffff]
[    1.083456] pci 0000:01:05.0: reg 24: [mem 0xd4200000-0xd42fffff]
[    1.083475] pci 0000:01:05.0: supports D1 D2
[    1.083561] pci 0000:00:01.0: PCI bridge to [bus 01-01]
[    1.083566] pci 0000:00:01.0:   bridge window [io  0x5000-0x5fff]
[    1.083571] pci 0000:00:01.0:   bridge window [mem 0xd4200000-0xd43fffff]
[    1.083576] pci 0000:00:01.0:   bridge window [mem 0xc0000000-0xcfffffff 64bit pref]
[    1.083674] pci 0000:02:00.0: reg 10: [mem 0xd3100000-0xd3103fff 64bit]
[    1.083703] pci 0000:02:00.0: reg 18: [io  0x3000-0x30ff]
[    1.083789] pci 0000:02:00.0: supports D1 D2
[    1.083791] pci 0000:02:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    1.083797] pci 0000:02:00.0: PME# disabled
[    2.100004] pci 0000:00:04.0: ASPM: Could not configure common clock
[    2.100041] pci 0000:00:04.0: PCI bridge to [bus 02-02]
[    2.100047] pci 0000:00:04.0:   bridge window [io  0x3000-0x4fff]
[    2.100051] pci 0000:00:04.0:   bridge window [mem 0xd3100000-0xd41fffff]
[    2.100056] pci 0000:00:04.0:   bridge window [mem 0xd0000000-0xd0ffffff 64bit pref]
[    2.100096] pci 0000:00:07.0: PCI bridge to [bus 03-05]
[    2.100101] pci 0000:00:07.0:   bridge window [io  0x2000-0x2fff]
[    2.100105] pci 0000:00:07.0:   bridge window [mem 0xd2100000-0xd30fffff]
[    2.100111] pci 0000:00:07.0:   bridge window [mem 0xd1000000-0xd1ffffff 64bit pref]
[    2.100225] pci 0000:06:00.0: reg 10: [mem 0xd2000000-0xd2003fff 64bit]
[    2.100292] pci 0000:06:00.0: supports D1 D2
[    2.120049] pci 0000:00:09.0: PCI bridge to [bus 06-06]
[    2.120055] pci 0000:00:09.0:   bridge window [io  0xfffffffffffff000-0x0000] (disabled)
[    2.120059] pci 0000:00:09.0:   bridge window [mem 0xd2000000-0xd20fffff]
[    2.120065] pci 0000:00:09.0:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    2.120174] pci 0000:00:14.4: PCI bridge to [bus 80-8f] (subtractive decode)
[    2.120179] pci 0000:00:14.4:   bridge window [io  0x1000-0x1fff]
[    2.120185] pci 0000:00:14.4:   bridge window [mem 0xfff00000-0x000fffff] (disabled)
[    2.120191] pci 0000:00:14.4:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    2.120194] pci 0000:00:14.4:   bridge window [io  0x0000-0x0cf7] (subtractive decode)
[    2.120197] pci 0000:00:14.4:   bridge window [io  0x0d00-0xffff] (subtractive decode)
[    2.120200] pci 0000:00:14.4:   bridge window [mem 0x000a0000-0x000bffff] (subtractive decode)
[    2.120203] pci 0000:00:14.4:   bridge window [mem 0x000c0000-0x000c3fff] (subtractive decode)
[    2.120206] pci 0000:00:14.4:   bridge window [mem 0x000c4000-0x000c7fff] (subtractive decode)
[    2.120209] pci 0000:00:14.4:   bridge window [mem 0x000c8000-0x000cbfff] (subtractive decode)
[    2.120212] pci 0000:00:14.4:   bridge window [mem 0x000cc000-0x000cffff] (subtractive decode)
[    2.120215] pci 0000:00:14.4:   bridge window [mem 0x000d0000-0x000d3fff] (subtractive decode)
[    2.120217] pci 0000:00:14.4:   bridge window [mem 0x000d4000-0x000d7fff] (subtractive decode)
[    2.120220] pci 0000:00:14.4:   bridge window [mem 0x000d8000-0x000dbfff] (subtractive decode)
[    2.120223] pci 0000:00:14.4:   bridge window [mem 0x000dc000-0x000dffff] (subtractive decode)
[    2.120226] pci 0000:00:14.4:   bridge window [mem 0x000e0000-0x000e3fff] (subtractive decode)
[    2.120229] pci 0000:00:14.4:   bridge window [mem 0x000e4000-0x000e7fff] (subtractive decode)
[    2.120232] pci 0000:00:14.4:   bridge window [mem 0x000e8000-0x000ebfff] (subtractive decode)
[    2.120235] pci 0000:00:14.4:   bridge window [mem 0xc0000000-0xdfffffff] (subtractive decode)
[    2.120238] pci 0000:00:14.4:   bridge window [mem 0xf0000000-0xfffdffff] (subtractive decode)
[    2.120300] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    2.120415] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEGP._PRT]
[    2.120507] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PB4_._PRT]
[    2.120618] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PB9_._PRT]
[    2.120722] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PB7_._PRT]
[    2.120941] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P2P_._PRT]
[    2.135361] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 7 10 11 12 14 15) *0, disabled.
[    2.135589] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 7 10 11 12 14 15) *0, disabled.
[    2.135814] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 7 10 11 12 14 15) *0, disabled.
[    2.136034] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 7 10 11 12 14 15) *0, disabled.
[    2.136254] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 7 10 11 12 14 15) *0, disabled.
[    2.136474] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 7 10 11 12 14 15) *0, disabled.
[    2.136693] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 7 10 11 12 14 15) *0, disabled.
[    2.136913] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 7 10 11 12 14 15) *0, disabled.
[    2.137006] HEST: Table is not found!
[    2.137119] vgaarb: device added: PCI:0000:01:05.0,decodes=io+mem,owns=io+mem,locks=none
[    2.137122] vgaarb: loaded
[    2.137292] SCSI subsystem initialized
[    2.137315] libata version 3.00 loaded.
[    2.137315] usbcore: registered new interface driver usbfs
[    2.137315] usbcore: registered new interface driver hub
[    2.137315] usbcore: registered new device driver usb
[    2.137315] ACPI: WMI: Mapper loaded
[    2.137315] PCI: Using ACPI for IRQ routing
[    2.137315] PCI: pci_cache_line_size set to 64 bytes
[    2.137315] Expanded resource reserved due to conflict with PCI Bus 0000:00
[    2.137315] reserve RAM buffer: 000000000009fc00 - 000000000009ffff 
[    2.137315] reserve RAM buffer: 00000000acb70000 - 00000000afffffff 
[    2.137315] reserve RAM buffer: 00000000afd4f000 - 00000000afffffff 
[    2.137315] reserve RAM buffer: 00000000aff00000 - 00000000afffffff 
[    2.137315] NetLabel: Initializing
[    2.137315] NetLabel:  domain hash size = 128
[    2.137315] NetLabel:  protocols = UNLABELED CIPSOv4
[    2.137315] NetLabel:  unlabeled traffic allowed by default
[    2.137315] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0
[    2.137315] hpet0: 4 comparators, 32-bit 14.318180 MHz counter
[    2.141026] Switching to clocksource hpet
[    2.150733] AppArmor: AppArmor Filesystem Enabled
[    2.150753] pnp: PnP ACPI init
[    2.150776] ACPI: bus type pnp registered
[    2.153269]   alloc irq_desc for 23 on node 0
[    2.153272]   alloc kstat_irqs on node 0
[    2.154382] pnp: PnP ACPI: found 11 devices
[    2.154384] ACPI: ACPI bus type pnp unregistered
[    2.154404] system 00:04: [io  0x0400-0x04cf] has been reserved
[    2.154407] system 00:04: [io  0x04d0-0x04d1] has been reserved
[    2.154410] system 00:04: [io  0x04d6] has been reserved
[    2.154413] system 00:04: [io  0x0680-0x06ff] has been reserved
[    2.154416] system 00:04: [io  0x077a] has been reserved
[    2.154419] system 00:04: [io  0x0c00-0x0c01] has been reserved
[    2.154422] system 00:04: [io  0x0c14] has been reserved
[    2.154425] system 00:04: [io  0x0c50-0x0c52] has been reserved
[    2.154428] system 00:04: [io  0x0c6c] has been reserved
[    2.154431] system 00:04: [io  0x0c6f] has been reserved
[    2.154435] system 00:04: [io  0x0cd0-0x0cdb] has been reserved
[    2.154438] system 00:04: [io  0x0220-0x0227] has been reserved
[    2.154441] system 00:04: [io  0x0260-0x0273] has been reserved
[    2.154444] system 00:04: [io  0x0800] has been reserved
[    2.154447] system 00:04: [io  0x0804] has been reserved
[    2.154450] system 00:04: [io  0x087f] has been reserved
[    2.154453] system 00:04: [io  0x0cdc-0x0cdf] has been reserved
[    2.154456] system 00:04: [io  0x0b00-0x0b0f] has been reserved
[    2.154459] system 00:04: [io  0x0b20-0x0b3f] has been reserved
[    2.154463] system 00:04: [io  0x0200-0x027f] could not be reserved
[    2.154470] system 00:05: [mem 0x00000000-0x0009ffff] could not be reserved
[    2.154473] system 00:05: [mem 0x000ec000-0x000fffff] could not be reserved
[    2.154477] system 00:05: [mem 0x00100000-0xbfffffff] could not be reserved
[    2.154480] system 00:05: [mem 0xe0000000-0xefffffff] has been reserved
[    2.154484] system 00:05: [mem 0xfeb00000-0xfeb00fff] has been reserved
[    2.154487] system 00:05: [mem 0xfec00000-0xfec00fff] could not be reserved
[    2.154490] system 00:05: [mem 0xfee00000-0xfee00fff] has been reserved
[    2.154494] system 00:05: [mem 0xffe00000-0xffffffff] could not be reserved
[    2.161091] pci 0000:00:01.0: PCI bridge to [bus 01-01]
[    2.161097] pci 0000:00:01.0:   bridge window [io  0x5000-0x5fff]
[    2.161102] pci 0000:00:01.0:   bridge window [mem 0xd4200000-0xd43fffff]
[    2.161107] pci 0000:00:01.0:   bridge window [mem 0xc0000000-0xcfffffff 64bit pref]
[    2.161113] pci 0000:00:04.0: PCI bridge to [bus 02-02]
[    2.161116] pci 0000:00:04.0:   bridge window [io  0x3000-0x4fff]
[    2.161121] pci 0000:00:04.0:   bridge window [mem 0xd3100000-0xd41fffff]
[    2.161125] pci 0000:00:04.0:   bridge window [mem 0xd0000000-0xd0ffffff 64bit pref]
[    2.161131] pci 0000:00:07.0: PCI bridge to [bus 03-05]
[    2.161134] pci 0000:00:07.0:   bridge window [io  0x2000-0x2fff]
[    2.161139] pci 0000:00:07.0:   bridge window [mem 0xd2100000-0xd30fffff]
[    2.161143] pci 0000:00:07.0:   bridge window [mem 0xd1000000-0xd1ffffff 64bit pref]
[    2.161149] pci 0000:00:09.0: PCI bridge to [bus 06-06]
[    2.161151] pci 0000:00:09.0:   bridge window [io  disabled]
[    2.161156] pci 0000:00:09.0:   bridge window [mem 0xd2000000-0xd20fffff]
[    2.161159] pci 0000:00:09.0:   bridge window [mem pref disabled]
[    2.161165] pci 0000:00:14.4: PCI bridge to [bus 80-8f]
[    2.161202] pci 0000:00:14.4:   bridge window [io  0x1000-0x1fff]
[    2.161209] pci 0000:00:14.4:   bridge window [mem disabled]
[    2.161214] pci 0000:00:14.4:   bridge window [mem pref disabled]
[    2.161230] pci 0000:00:01.0: setting latency timer to 64
[    2.161239] pci 0000:00:04.0: setting latency timer to 64
[    2.161247] pci 0000:00:07.0: setting latency timer to 64
[    2.161258] pci 0000:00:09.0: setting latency timer to 64
[    2.161268] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
[    2.161270] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff]
[    2.161273] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
[    2.161276] pci_bus 0000:00: resource 7 [mem 0x000c0000-0x000c3fff]
[    2.161279] pci_bus 0000:00: resource 8 [mem 0x000c4000-0x000c7fff]
[    2.161282] pci_bus 0000:00: resource 9 [mem 0x000c8000-0x000cbfff]
[    2.161284] pci_bus 0000:00: resource 10 [mem 0x000cc000-0x000cffff]
[    2.161287] pci_bus 0000:00: resource 11 [mem 0x000d0000-0x000d3fff]
[    2.161290] pci_bus 0000:00: resource 12 [mem 0x000d4000-0x000d7fff]
[    2.161293] pci_bus 0000:00: resource 13 [mem 0x000d8000-0x000dbfff]
[    2.161296] pci_bus 0000:00: resource 14 [mem 0x000dc000-0x000dffff]
[    2.161299] pci_bus 0000:00: resource 15 [mem 0x000e0000-0x000e3fff]
[    2.161302] pci_bus 0000:00: resource 16 [mem 0x000e4000-0x000e7fff]
[    2.161304] pci_bus 0000:00: resource 17 [mem 0x000e8000-0x000ebfff]
[    2.161307] pci_bus 0000:00: resource 18 [mem 0xc0000000-0xdfffffff]
[    2.161310] pci_bus 0000:00: resource 19 [mem 0xf0000000-0xfffdffff]
[    2.161313] pci_bus 0000:01: resource 0 [io  0x5000-0x5fff]
[    2.161316] pci_bus 0000:01: resource 1 [mem 0xd4200000-0xd43fffff]
[    2.161319] pci_bus 0000:01: resource 2 [mem 0xc0000000-0xcfffffff 64bit pref]
[    2.161322] pci_bus 0000:02: resource 0 [io  0x3000-0x4fff]
[    2.161325] pci_bus 0000:02: resource 1 [mem 0xd3100000-0xd41fffff]
[    2.161328] pci_bus 0000:02: resource 2 [mem 0xd0000000-0xd0ffffff 64bit pref]
[    2.161331] pci_bus 0000:03: resource 0 [io  0x2000-0x2fff]
[    2.161333] pci_bus 0000:03: resource 1 [mem 0xd2100000-0xd30fffff]
[    2.161336] pci_bus 0000:03: resource 2 [mem 0xd1000000-0xd1ffffff 64bit pref]
[    2.161340] pci_bus 0000:06: resource 1 [mem 0xd2000000-0xd20fffff]
[    2.161343] pci_bus 0000:80: resource 0 [io  0x1000-0x1fff]
[    2.161345] pci_bus 0000:80: resource 4 [io  0x0000-0x0cf7]
[    2.161348] pci_bus 0000:80: resource 5 [io  0x0d00-0xffff]
[    2.161351] pci_bus 0000:80: resource 6 [mem 0x000a0000-0x000bffff]
[    2.161354] pci_bus 0000:80: resource 7 [mem 0x000c0000-0x000c3fff]
[    2.161356] pci_bus 0000:80: resource 8 [mem 0x000c4000-0x000c7fff]
[    2.161359] pci_bus 0000:80: resource 9 [mem 0x000c8000-0x000cbfff]
[    2.161362] pci_bus 0000:80: resource 10 [mem 0x000cc000-0x000cffff]
[    2.161364] pci_bus 0000:80: resource 11 [mem 0x000d0000-0x000d3fff]
[    2.161367] pci_bus 0000:80: resource 12 [mem 0x000d4000-0x000d7fff]
[    2.161370] pci_bus 0000:80: resource 13 [mem 0x000d8000-0x000dbfff]
[    2.161372] pci_bus 0000:80: resource 14 [mem 0x000dc000-0x000dffff]
[    2.161375] pci_bus 0000:80: resource 15 [mem 0x000e0000-0x000e3fff]
[    2.161378] pci_bus 0000:80: resource 16 [mem 0x000e4000-0x000e7fff]
[    2.161380] pci_bus 0000:80: resource 17 [mem 0x000e8000-0x000ebfff]
[    2.161383] pci_bus 0000:80: resource 18 [mem 0xc0000000-0xdfffffff]
[    2.161386] pci_bus 0000:80: resource 19 [mem 0xf0000000-0xfffdffff]
[    2.161429] NET: Registered protocol family 2
[    2.161628] IP route cache hash table entries: 131072 (order: 8, 1048576 bytes)
[    2.163412] TCP established hash table entries: 524288 (order: 11, 8388608 bytes)
[    2.168128] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[    2.168702] TCP: Hash tables configured (established 524288 bind 65536)
[    2.168705] TCP reno registered
[    2.168724] UDP hash table entries: 2048 (order: 4, 65536 bytes)
[    2.168775] UDP-Lite hash table entries: 2048 (order: 4, 65536 bytes)
[    2.168925] NET: Registered protocol family 1
[    2.168943] pci 0000:00:01.0: MSI quirk detected; subordinate MSI disabled
[    2.169248] PCI: CLS mismatch (64 != 32), using 64 bytes
[    2.169390] pci 0000:01:05.0: Boot video device
[    2.169397] PCI-DMA: Using software bounce buffering for IO (SWIOTLB)
[    2.169400] Placing 64MB software IO TLB between ffff880001f9e000 - ffff880005f9e000
[    2.169403] software IO TLB at phys 0x1f9e000 - 0x5f9e000
[    2.169739] Scanning for low memory corruption every 60 seconds
[    2.169928] audit: initializing netlink socket (disabled)
[    2.169939] type=2000 audit(1286916404.159:1): initialized
[    2.185286] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    2.187402] VFS: Disk quotas dquot_6.5.2
[    2.187472] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    2.188339] fuse init (API version 7.14)
[    2.188476] msgmni has been set to 7409
[    2.192276] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    2.192280] io scheduler noop registered
[    2.192283] io scheduler deadline registered
[    2.192332] io scheduler cfq registered (default)
[    2.192479] pcieport 0000:00:04.0: setting latency timer to 64
[    2.192512]   alloc irq_desc for 40 on node -1
[    2.192515]   alloc kstat_irqs on node -1
[    2.192527] pcieport 0000:00:04.0: irq 40 for MSI/MSI-X
[    2.192605] pcieport 0000:00:07.0: setting latency timer to 64
[    2.192633]   alloc irq_desc for 41 on node -1
[    2.192634]   alloc kstat_irqs on node -1
[    2.192640] pcieport 0000:00:07.0: irq 41 for MSI/MSI-X
[    2.192724] pcieport 0000:00:09.0: setting latency timer to 64
[    2.192757]   alloc irq_desc for 42 on node -1
[    2.192759]   alloc kstat_irqs on node -1
[    2.192765] pcieport 0000:00:09.0: irq 42 for MSI/MSI-X
[    2.192852] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    2.192924] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    2.197603] ACPI: AC Adapter [AC] (on-line)
[    2.197725] input: Sleep Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0E:00/input/input0
[    2.197732] ACPI: Sleep Button [SLPB]
[    2.197775] input: Lid Switch as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0D:00/input/input1
[    2.197888] ACPI: Lid Switch [LID]
[    2.197940] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input2
[    2.197944] ACPI: Power Button [PWRF]
[    2.198214] ACPI: Fan [FAN0] (off)
[    2.198406] ACPI: Fan [FAN1] (off)
[    2.198598] ACPI: Fan [FAN2] (off)
[    2.198796] ACPI: Fan [FAN3] (off)
[    2.199085] ACPI: acpi_idle registered with cpuidle
[    2.214248] thermal LNXTHERM:01: registered as thermal_zone0
[    2.214260] ACPI: Thermal Zone [CPUZ] (73 C)
[    2.214374] ERST: Table is not found!
[    2.214854] Linux agpgart interface v0.103
[    2.214885] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    2.216448] brd: module loaded
[    2.217028] loop: module loaded
[    2.217657] Fixed MDIO Bus: probed
[    2.217693] PPP generic driver version 2.4.2
[    2.217730] tun: Universal TUN/TAP device driver, 1.6
[    2.217732] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    2.217815] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    2.217877]   alloc irq_desc for 17 on node -1
[    2.217880]   alloc kstat_irqs on node -1
[    2.217890] ehci_hcd 0000:00:12.2: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    2.217928] ehci_hcd 0000:00:12.2: setting latency timer to 64
[    2.217933] ehci_hcd 0000:00:12.2: EHCI Host Controller
[    2.217971] ehci_hcd 0000:00:12.2: new USB bus registered, assigned bus number 1
[    2.218047] ehci_hcd 0000:00:12.2: applying AMD SB600/SB700 USB freeze workaround
[    2.218085] ehci_hcd 0000:00:12.2: debug port 1
[    2.218116] ehci_hcd 0000:00:12.2: irq 17, io mem 0xd4409500
[    2.231272] ehci_hcd 0000:00:12.2: USB 2.0 started, EHCI 1.00
[    2.231425] hub 1-0:1.0: USB hub found
[    2.231431] hub 1-0:1.0: 6 ports detected
[    2.231586]   alloc irq_desc for 19 on node -1
[    2.231588]   alloc kstat_irqs on node -1
[    2.231594] ehci_hcd 0000:00:13.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    2.231613] ehci_hcd 0000:00:13.2: setting latency timer to 64
[    2.231617] ehci_hcd 0000:00:13.2: EHCI Host Controller
[    2.231659] ehci_hcd 0000:00:13.2: new USB bus registered, assigned bus number 2
[    2.231722] ehci_hcd 0000:00:13.2: applying AMD SB600/SB700 USB freeze workaround
[    2.231738] ehci_hcd 0000:00:13.2: debug port 1
[    2.231764] ehci_hcd 0000:00:13.2: irq 19, io mem 0xd4409400
[    2.251306] ehci_hcd 0000:00:13.2: USB 2.0 started, EHCI 1.00
[    2.251427] hub 2-0:1.0: USB hub found
[    2.251432] hub 2-0:1.0: 6 ports detected
[    2.251546] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    2.251601]   alloc irq_desc for 16 on node -1
[    2.251603]   alloc kstat_irqs on node -1
[    2.251609] ohci_hcd 0000:00:12.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    2.251627] ohci_hcd 0000:00:12.0: setting latency timer to 64
[    2.251631] ohci_hcd 0000:00:12.0: OHCI Host Controller
[    2.251671] ohci_hcd 0000:00:12.0: new USB bus registered, assigned bus number 3
[    2.251742] ohci_hcd 0000:00:12.0: irq 16, io mem 0xd4408000
[    2.268849] ACPI: Battery Slot [BAT0] (battery present)
[    2.314172] hub 3-0:1.0: USB hub found
[    2.314212] hub 3-0:1.0: 3 ports detected
[    2.314285] ohci_hcd 0000:00:12.1: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    2.314301] ohci_hcd 0000:00:12.1: setting latency timer to 64
[    2.314305] ohci_hcd 0000:00:12.1: OHCI Host Controller
[    2.314345] ohci_hcd 0000:00:12.1: new USB bus registered, assigned bus number 4
[    2.314402] ohci_hcd 0000:00:12.1: irq 16, io mem 0xd4407000
[    2.374166] hub 4-0:1.0: USB hub found
[    2.374207] hub 4-0:1.0: 3 ports detected
[    2.374287] ohci_hcd 0000:00:13.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    2.374301] ohci_hcd 0000:00:13.0: setting latency timer to 64
[    2.374305] ohci_hcd 0000:00:13.0: OHCI Host Controller
[    2.374340] ohci_hcd 0000:00:13.0: new USB bus registered, assigned bus number 5
[    2.374401] ohci_hcd 0000:00:13.0: irq 17, io mem 0xd4406000
[    2.434165] hub 5-0:1.0: USB hub found
[    2.434206] hub 5-0:1.0: 3 ports detected
[    2.434271] ohci_hcd 0000:00:13.1: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    2.434284] ohci_hcd 0000:00:13.1: setting latency timer to 64
[    2.434288] ohci_hcd 0000:00:13.1: OHCI Host Controller
[    2.434338] ohci_hcd 0000:00:13.1: new USB bus registered, assigned bus number 6
[    2.434389] ohci_hcd 0000:00:13.1: irq 17, io mem 0xd4405000
[    2.494176] hub 6-0:1.0: USB hub found
[    2.494216] hub 6-0:1.0: 3 ports detected
[    2.494280]   alloc irq_desc for 18 on node -1
[    2.494283]   alloc kstat_irqs on node -1
[    2.494291] ohci_hcd 0000:00:14.5: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    2.494307] ohci_hcd 0000:00:14.5: setting latency timer to 64
[    2.494311] ohci_hcd 0000:00:14.5: OHCI Host Controller
[    2.494349] ohci_hcd 0000:00:14.5: new USB bus registered, assigned bus number 7
[    2.494419] ohci_hcd 0000:00:14.5: irq 18, io mem 0xd4404000
[    2.555400] hub 7-0:1.0: USB hub found
[    2.555440] hub 7-0:1.0: 2 ports detected
[    2.555511] uhci_hcd: USB Universal Host Controller Interface driver
[    2.555648] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    2.557591] i8042.c: Detected active multiplexing controller, rev 1.1.
[    2.558686] serio: i8042 KBD port at 0x60,0x64 irq 1
[    2.558694] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[    2.558697] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[    2.558701] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[    2.558704] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[    2.558799] mice: PS/2 mouse device common for all mice
[    2.558940] rtc_cmos 00:06: RTC can wake from S4
[    2.558985] rtc_cmos 00:06: rtc core: registered rtc_cmos as rtc0
[    2.559048] rtc0: alarms up to one day, 114 bytes nvram, hpet irqs
[    2.559158] device-mapper: uevent: version 1.0.3
[    2.559425] device-mapper: ioctl: 4.17.0-ioctl (2010-03-05) initialised: [email]dm-devel@redhat.com[/email]
[    2.559835] device-mapper: multipath: version 1.1.1 loaded
[    2.559838] device-mapper: multipath round-robin: version 1.0.0 loaded
[    2.560558] cpuidle: using governor ladder
[    2.560561] cpuidle: using governor menu
[    2.560867] TCP cubic registered
[    2.561012] NET: Registered protocol family 10
[    2.561489] lo: Disabled Privacy Extensions
[    2.561708] NET: Registered protocol family 17
[    2.561787] powernow-k8: Found 1 AMD Turion(tm)X2 Dual Core Mobile RM-70 (2 cpu cores) (version 2.20.00)
[    2.561940] powernow-k8:    0 : pstate 0 (2000 MHz)
[    2.561942] powernow-k8:    1 : pstate 1 (1000 MHz)
[    2.561944] powernow-k8:    2 : pstate 2 (500 MHz)
[    2.563478] PM: Resume from disk failed.
[    2.563493] registered taskstats version 1
[    2.563888]   Magic number: 14:284:801
[    2.564044] rtc_cmos 00:06: setting system clock to 2010-10-12 20:46:45 UTC (1286916405)
[    2.564047] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    2.564049] EDD information not available.
[    2.564161] Freeing unused kernel memory: 908k freed
[    2.564598] Write protecting the kernel read-only data: 10240k
[    2.564893] Freeing unused kernel memory: 416k freed
[    2.565261] Freeing unused kernel memory: 1644k freed
[    2.580939] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input3
[    2.592573] udev[75]: starting version 163
[    2.696221] sky2: driver version 1.28
[    2.696291] sky2 0000:02:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    2.696339] sky2 0000:02:00.0: setting latency timer to 64
[    2.696485] sky2 0000:02:00.0: Yukon-2 FE+ chip revision 0
[    2.696658]   alloc irq_desc for 43 on node -1
[    2.696661]   alloc kstat_irqs on node -1
[    2.696752] sky2 0000:02:00.0: irq 43 for MSI/MSI-X
[    2.763979] sky2 0000:02:00.0: eth0: addr 00:24:81:3a:11:7a
[    2.795407] ahci 0000:00:11.0: version 3.0
[    2.795464]   alloc irq_desc for 20 on node -1
[    2.795467]   alloc kstat_irqs on node -1
[    2.795478] ahci 0000:00:11.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    2.795710] ahci 0000:00:11.0: AHCI 0001.0100 32 slots 4 ports 3 Gbps 0xf impl SATA mode
[    2.795715] ahci 0000:00:11.0: flags: 64bit ncq sntf ilck pm led clo pio ccc 
[    2.810647] scsi0 : ahci
[    2.810850] scsi1 : ahci
[    2.810956] scsi2 : ahci
[    2.811059] scsi3 : ahci
[    2.811392] ata1: SATA max UDMA/133 abar m1024@0xd4409000 port 0xd4409100 irq 20
[    2.811396] ata2: SATA max UDMA/133 abar m1024@0xd4409000 port 0xd4409180 irq 20
[    2.811401] ata3: SATA max UDMA/133 abar m1024@0xd4409000 port 0xd4409200 irq 20
[    2.811405] ata4: SATA max UDMA/133 abar m1024@0xd4409000 port 0xd4409280 irq 20
[    2.831368] usb 3-1: new low speed USB device using ohci_hcd and address 2
[    3.140072] usb 2-2: new high speed USB device using ehci_hcd and address 2
[    3.160081] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    3.160116] ata3: SATA link down (SStatus 0 SControl 300)
[    3.160146] ata4: SATA link down (SStatus 0 SControl 300)
[    3.160177] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    3.160961] ata1.00: ATA-8: WDC WD3200BEVT-60ZCT0, 11.01A11, max UDMA/100
[    3.160965] ata1.00: 625142448 sectors, multi 16: LBA48 NCQ (depth 31/32), AA
[    3.161910] ata1.00: configured for UDMA/100
[    3.179488] ata2.00: ATAPI: HL-DT-ST DVDRAM GSA-T50L, SC04, max UDMA/100
[    3.181741] scsi 0:0:0:0: Direct-Access     ATA      WDC WD3200BEVT-6 11.0 PQ: 0 ANSI: 5
[    3.181933] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    3.182031] sd 0:0:0:0: [sda] 625142448 512-byte logical blocks: (320 GB/298 GiB)
[    3.182122] sd 0:0:0:0: [sda] Write Protect is off
[    3.182125] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    3.182174] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    3.182926]  sda:
[    3.184311] ata2.00: configured for UDMA/100
[    3.209791]  sda1 sda2 < sda5 sda6 sda7 > sda3
[    3.246731] sd 0:0:0:0: [sda] Attached SCSI disk
[    3.313283] scsi 1:0:0:0: CD-ROM            HL-DT-ST DVDRAM GSA-T50L  SC04 PQ: 0 ANSI: 5
[    3.640391] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[    3.640396] Uniform CD-ROM driver Revision: 3.20
[    3.640549] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    3.640637] sr 1:0:0:0: Attached scsi generic sg1 type 5
[    3.648440] usbcore: registered new interface driver hiddev
[    3.654572] input: Logitech USB-PS/2 Optical Mouse as /devices/pci0000:00/0000:00:12.0/usb3/3-1/3-1:1.0/input/input4
[    3.654798] generic-usb 0003:046D:C03E.0001: input,hidraw0: USB HID v1.10 Mouse [Logitech USB-PS/2 Optical Mouse] on usb-0000:00:12.0-1/input0
[    3.655111] usbcore: registered new interface driver usbhid
[    3.655114] usbhid: USB HID core driver
[    3.781287] usb 6-3: new full speed USB device using ohci_hcd and address 2
[    4.293882] EXT4-fs (sda7): mounted filesystem with ordered data mode. Opts: (null)
[   13.298306] udev[438]: starting version 163
[   13.321737] lp: driver loaded but no devices found
[   13.396009] Adding 1999868k swap on /dev/sda6.  Priority:-1 extents:1 across:1999868k 
[   13.479903] piix4_smbus 0000:00:14.0: SMBus Host Controller at 0xb00, revision 0
[   13.480657] shpchp 0000:00:01.0: HPC vendor_id 1022 device_id 9602 ss_vid 1022 ss_did 9602
[   13.480663] shpchp 0000:00:01.0: Cannot reserve MMIO region
[   13.480764] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   13.506272] lib80211: common routines for IEEE802.11 drivers
[   13.506277] lib80211_crypt: registered algorithm 'NULL'
[   13.569880] wl: module license 'MIXED/Proprietary' taints kernel.
[   13.569885] Disabling lock debugging due to kernel taint
[   13.589372] lis3lv02d: laptop model unknown, using default axes configuration
[   13.590145] lis3lv02d: 8 bits sensor found
[   13.594836] EDAC MC: Ver: 2.1.0 Oct 10 2010
[   13.644265] EDAC amd64_edac:  Ver: 3.3.0 Oct 10 2010
[   13.644328] EDAC amd64: This node reports that Memory ECC is currently disabled, set F3x44[22] (0000:00:18.3).
[   13.644339] EDAC amd64: ECC disabled in the BIOS or no ECC capability, module will not load.
[   13.644340]  Either enable ECC checking or force module loading by setting 'ecc_enable_override'.
[   13.644342]  (Note that use of the override may cause unknown side effects.)
[   13.644350] amd64_edac: probe of 0000:00:18.2 failed with error -22
[   13.690212] wl 0000:06:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   13.690222] wl 0000:06:00.0: setting latency timer to 64
[   13.831480] input: ST LIS3LV02DL Accelerometer as /devices/platform/lis3lv02d/input/input5
[   13.831772] acpi device:01: registered as cooling_device6
[   13.832407] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A03:00/device:00/LNXVIDEO:00/input/input6
[   13.832453] ACPI: Video Device [IGFX] (multi-head: yes  rom: no  post: no)
[   13.857884] Registered led device: hp::hddprotect
[   13.857912] lis3lv02d driver loaded.
[   13.860730] type=1400 audit(1286909216.788:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient3" pid=744 comm="apparmor_parser"
[   13.861043] type=1400 audit(1286909216.788:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=744 comm="apparmor_parser"
[   13.861348] type=1400 audit(1286909216.788:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=744 comm="apparmor_parser"
[   13.903094] input: HP WMI hotkeys as /devices/virtual/input/input7
[   13.919364] Linux video capture interface: v2.00
[   13.923985] uvcvideo: Found UVC 1.00 device CKF7063 (04f2:b083)
[   13.924262] Bluetooth: Core ver 2.15
[   13.924293] NET: Registered protocol family 31
[   13.924295] Bluetooth: HCI device and connection manager initialized
[   13.924299] Bluetooth: HCI socket layer initialized
[   13.926473] Bluetooth: Generic Bluetooth USB driver ver 0.6
[   13.927375] [drm] Initialized drm 1.1.0 20060810
[   13.941826] usbcore: registered new interface driver btusb
[   13.966046] EXT4-fs (sda7): re-mounted. Opts: errors=remount-ro
[   13.971384] input: CKF7063 as /devices/pci0000:00/0000:00:13.2/usb2/2-2/2-2:1.0/input/input8
[   13.971504] usbcore: registered new interface driver uvcvideo
[   13.971506] USB Video Class driver (v0.1.0)
[   13.972688] lib80211_crypt: registered algorithm 'TKIP'
[   13.972932] eth1: Broadcom BCM432b 802.11 Hybrid Wireless Controller 5.60.48.36 
[   14.081423] [drm] radeon defaulting to kernel modesetting.
[   14.081424] [drm] radeon kernel modesetting enabled.
[   14.081534] radeon 0000:01:05.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[   14.081539] radeon 0000:01:05.0: setting latency timer to 64
[   14.093781] [drm] initializing kernel modesetting (RS780 0x1002:0x9612).
[   14.098905] [drm] register mmio base: 0xD4300000
[   14.098908] [drm] register mmio size: 65536
[   14.099052] ATOM BIOS: HP_PrincePearl
[   14.099074] [drm] Clocks initialized !
[   14.099086] radeon 0000:01:05.0: VRAM: 256M 0xC0000000 - 0xCFFFFFFF (256M used)
[   14.099089] radeon 0000:01:05.0: GTT: 512M 0xA0000000 - 0xBFFFFFFF
[   14.099314] [drm] Detected VRAM RAM=256M, BAR=256M
[   14.099319] [drm] RAM width 32bits DDR
[   14.105374] [TTM] Zone  kernel: Available graphics memory: 1898244 kiB.
[   14.105379] [TTM] Initializing pool allocator.
[   14.105406] [drm] radeon: 256M of VRAM memory ready
[   14.105408] [drm] radeon: 512M of GTT memory ready.
[   14.105450] [drm] radeon: irq initialized.
[   14.105454] [drm] GART: num cpu pages 131072, num gpu pages 131072
[   14.107201] [drm] Loading RS780 Microcode
[   14.181176] [drm] ring test succeeded in 1 usecs
[   14.181443] [drm] radeon: ib pool ready.
[   14.181544] [drm] ib test succeeded in 0 usecs
[   14.181548] [drm] Enabling audio support
[   14.181600] [drm] Default TV standard: NTSC
[   14.191453] [drm] Radeon Display Connectors
[   14.191457] [drm] Connector 0:
[   14.191460] [drm]   VGA
[   14.191463] [drm]   DDC: 0x7e40 0x7e40 0x7e44 0x7e44 0x7e48 0x7e48 0x7e4c 0x7e4c
[   14.191465] [drm]   Encoders:
[   14.191467] [drm]     CRT1: INTERNAL_KLDSCP_DAC1
[   14.191469] [drm] Connector 1:
[   14.191470] [drm]   LVDS
[   14.191473] [drm]   DDC: 0x7e50 0x7e50 0x7e54 0x7e54 0x7e58 0x7e58 0x7e5c 0x7e5c
[   14.191475] [drm]   Encoders:
[   14.191477] [drm]     LCD1: INTERNAL_KLDSCP_LVTMA
[   14.205521] HDA Intel 0000:00:14.2: power state changed by ACPI to D0
[   14.205614] HDA Intel 0000:00:14.2: power state changed by ACPI to D0
[   14.205658] HDA Intel 0000:00:14.2: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   14.261246] [drm] radeon: power management initialized
[   14.334116] Synaptics Touchpad, model: 1, fw: 6.3, id: 0x1a0b1, caps: 0xa04711/0x200000/0x0
[   14.341410] [drm] fb mappable at 0xC0141000
[   14.341413] [drm] vram apper at 0xC0000000
[   14.341415] [drm] size 4096000
[   14.341417] [drm] fb depth is 24
[   14.341418] [drm]    pitch is 5120
[   14.374366] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio4/input/input9
[   14.543661] EXT4-fs (sda5): mounted filesystem with ordered data mode. Opts: (null)
[   15.166890] Console: switching to colour frame buffer device 160x50
[   15.183687] fb0: radeondrmfb frame buffer device
[   15.183689] drm: registered panic notifier
[   15.183706] Slow work thread pool: Starting up
[   15.183928] Slow work thread pool: Ready
[   15.183937] [drm] Initialized radeon 2.5.0 20080528 for 0000:01:05.0 on minor 0
[   15.298027] type=1400 audit(1286909218.218:5): apparmor="STATUS" operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" pid=1027 comm="apparmor_parser"
[   15.306935] type=1400 audit(1286909218.228:6): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince" pid=1030 comm="apparmor_parser"
[   15.309187] type=1400 audit(1286909218.228:7): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient3" pid=1028 comm="apparmor_parser"
[   15.309501] type=1400 audit(1286909218.228:8): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=1028 comm="apparmor_parser"
[   15.309677] type=1400 audit(1286909218.228:9): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=1028 comm="apparmor_parser"
[   15.324702] sky2 0000:02:00.0: eth0: enabling interface
[   15.325402] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   15.331899] type=1400 audit(1286909218.258:10): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince-previewer" pid=1030 comm="apparmor_parser"
[   15.346851] type=1400 audit(1286909218.268:11): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince-thumbnailer" pid=1030 comm="apparmor_parser"
[   15.382953] ppdev: user-space parallel port driver
[   15.398921] HP WMI: Unknown key pressed - 0
[   15.399013] HP WMI: Unknown key pressed - 0
[   15.945879] Bluetooth: L2CAP ver 2.14
[   15.945884] Bluetooth: L2CAP socket layer initialized
[   15.953609] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   15.953614] Bluetooth: BNEP filters: protocol multicast
[   15.959430] Bluetooth: SCO (Voice Link) ver 0.6
[   15.959434] Bluetooth: SCO socket layer initialized
[   16.054813] Bluetooth: RFCOMM TTY layer initialized
[   16.054822] Bluetooth: RFCOMM socket layer initialized
[   16.054825] Bluetooth: RFCOMM ver 1.11
[   16.823821] EXT4-fs (sda7): re-mounted. Opts: errors=remount-ro,commit=0
[   16.907007] EXT4-fs (sda5): re-mounted. Opts: commit=0
[   18.312447] EXT4-fs (sda7): re-mounted. Opts: errors=remount-ro,commit=0
[   18.327628] EXT4-fs (sda5): re-mounted. Opts: commit=0
[   26.400035] eth1: no IPv6 routers present
[   87.212270] lo: Disabled Privacy Extensions
[  302.995657] process `skype' is using obsolete setsockopt SO_BSDCOMPAT
[  694.774668] lo: Disabled Privacy Extensions
[ 5886.100065] usb 1-6: new high speed USB device using ehci_hcd and address 3
[ 5886.358515] Initializing USB Mass Storage driver...
[ 5886.358709] scsi4 : usb-storage 1-6:1.0
[ 5886.358834] usbcore: registered new interface driver usb-storage
[ 5886.358836] USB Mass Storage support registered.
[ 5887.351941] scsi 4:0:0:0: Direct-Access     Kingston DataTraveler 2.0 1.00 PQ: 0 ANSI: 2
[ 5887.354166] sd 4:0:0:0: Attached scsi generic sg2 type 0
[ 5887.357406] sd 4:0:0:0: [sdb] 3930112 512-byte logical blocks: (2.01 GB/1.87 GiB)
[ 5887.358187] sd 4:0:0:0: [sdb] Write Protect is off
[ 5887.358202] sd 4:0:0:0: [sdb] Mode Sense: 23 00 00 00
[ 5887.358212] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[ 5887.366727] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[ 5887.366756]  sdb: sdb1
[ 5887.501224] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[ 5887.501298] sd 4:0:0:0: [sdb] Attached SCSI removable disk
[ 6262.187797] lo: Disabled Privacy Extensions
[ 6443.300458] usb 1-6: USB disconnect, address 3

---

