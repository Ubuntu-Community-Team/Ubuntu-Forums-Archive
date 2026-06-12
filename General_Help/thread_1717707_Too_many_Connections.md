---
title: "Too many Connections"
date: 2011-03-30
forum: General Help
---

### Post by conradin on 2011-03-30
Hi all,
I get a message on boot that I have too many connections. 
so I looked ate the dmesg file
but I have no idea what is going on. can some one enlighten me?

My system is a i7-960 cpu on a saber tooth x58 asus motherboard, with 12 GB of DDR3 (4GB per channel) running the 64 bit version of maverick Ubuntu.

```
$ cat /var/log/dmesg
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.35-28-generic (buildd@allspice) (gcc version 4.4.5 (Ubuntu/Linaro 4.4.4-14ubuntu5) ) #49-Ubuntu SMP Tue Mar 1 14:39:03 UTC 2011 (Ubuntu 2.6.35-28.49-generic 2.6.35.11)
[    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-2.6.35-28-generic root=UUID=4a71cb65-5c78-4059-8810-0466baeda2d1 ro quiet splash
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e2c00 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 00000000bf780000 (usable)
[    0.000000]  BIOS-e820: 00000000bf780000 - 00000000bf798000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000bf798000 - 00000000bf7da000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000bf7da000 - 00000000c0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000ffe00000 - 0000000100000000 (reserved)
[    0.000000]  BIOS-e820: 0000000100000000 - 0000000340000000 (usable)
[    0.000000] NX (Execute Disable) protection: active
[    0.000000] DMI 2.5 present.
[    0.000000] AMI BIOS detected: BIOS may corrupt low RAM, working around it.
[    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
[    0.000000] e820 update range: 0000000000000000 - 0000000000001000 (usable) ==> (reserved)
[    0.000000] e820 remove range: 00000000000a0000 - 0000000000100000 (usable)
[    0.000000] No AGP bridge found
[    0.000000] last_pfn = 0x340000 max_arch_pfn = 0x400000000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-DFFFF write-protect
[    0.000000]   E0000-EBFFF write-through
[    0.000000]   EC000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000 mask E00000000 write-back
[    0.000000]   1 base 200000000 mask F00000000 write-back
[    0.000000]   2 base 300000000 mask FC0000000 write-back
[    0.000000]   3 base 0C0000000 mask FC0000000 uncachable
[    0.000000]   4 base 0BF800000 mask FFF800000 uncachable
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] e820 update range: 00000000bf800000 - 0000000100000000 (usable) ==> (reserved)
[    0.000000] last_pfn = 0xbf780 max_arch_pfn = 0x400000000
[    0.000000] Scanning 0 areas for low memory corruption
[    0.000000] modified physical RAM map:
[    0.000000]  modified: 0000000000000000 - 0000000000010000 (reserved)
[    0.000000]  modified: 0000000000010000 - 000000000009fc00 (usable)
[    0.000000]  modified: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  modified: 00000000000e2c00 - 0000000000100000 (reserved)
[    0.000000]  modified: 0000000000100000 - 00000000bf780000 (usable)
[    0.000000]  modified: 00000000bf780000 - 00000000bf798000 (ACPI data)
[    0.000000]  modified: 00000000bf798000 - 00000000bf7da000 (ACPI NVS)
[    0.000000]  modified: 00000000bf7da000 - 00000000c0000000 (reserved)
[    0.000000]  modified: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  modified: 00000000ffe00000 - 0000000100000000 (reserved)
[    0.000000]  modified: 0000000100000000 - 0000000340000000 (usable)
[    0.000000] initial memory mapped : 0 - 20000000
[    0.000000] found SMP MP-table at [ffff8800000ff780] ff780
[    0.000000] init_memory_mapping: 0000000000000000-00000000bf780000
[    0.000000]  0000000000 - 00bf600000 page 2M
[    0.000000]  00bf600000 - 00bf780000 page 4k
[    0.000000] kernel direct mapping tables up to bf780000 @ 16000-1b000
[    0.000000] init_memory_mapping: 0000000100000000-0000000340000000
[    0.000000]  0100000000 - 0340000000 page 2M
[    0.000000] kernel direct mapping tables up to 340000000 @ 19000-27000
[    0.000000] RAMDISK: 3756f000 - 37ff0000
[    0.000000] ACPI: RSDP 00000000000fb940 00014 (v00 ACPIAM)
[    0.000000] ACPI: RSDT 00000000bf780000 00044 (v01 122110 RSDT2214 20101221 MSFT 00000097)
[    0.000000] ACPI: FACP 00000000bf780200 00084 (v01 122110 FACP2214 20101221 MSFT 00000097)
[    0.000000] ACPI: DSDT 00000000bf7804b0 0C469 (v01  A1682 A1682001 00000001 INTL 20060113)
[    0.000000] ACPI: FACS 00000000bf798000 00040
[    0.000000] ACPI: APIC 00000000bf780390 000D8 (v01 122110 APIC2214 20101221 MSFT 00000097)
[    0.000000] ACPI: MCFG 00000000bf780470 0003C (v01 122110 OEMMCFG  20101221 MSFT 00000097)
[    0.000000] ACPI: OEMB 00000000bf798040 00072 (v01 122110 OEMB2214 20101221 MSFT 00000097)
[    0.000000] ACPI: HPET 00000000bf78f4b0 00038 (v01 122110 OEMHPET  20101221 MSFT 00000097)
[    0.000000] ACPI: ASPT 00000000bf798360 00034 (v06 122110 PerfTune 20101221 MSFT 00000097)
[    0.000000] ACPI: OSFR 00000000bf78f4f0 000B0 (v01 122110 OEMOSFR  20101221 MSFT 00000097)
[    0.000000] ACPI: SSDT 00000000bf79a7f0 00363 (v01 DpgPmm    CpuPm 00000012 INTL 20060113)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] No NUMA configuration found
[    0.000000] Faking a node at 0000000000000000-0000000340000000
[    0.000000] Initmem setup node 0 0000000000000000-0000000340000000
[    0.000000]   NODE_DATA [0000000100000000 - 0000000100004fff]
[    0.000000]  [ffffea0000000000-ffffea000b5fffff] PMD -> [ffff880100200000-ffff88010a9fffff] on node 0
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000010 -> 0x00001000
[    0.000000]   DMA32    0x00001000 -> 0x00100000
[    0.000000]   Normal   0x00100000 -> 0x00340000
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[3] active PFN ranges
[    0.000000]     0: 0x00000010 -> 0x0000009f
[    0.000000]     0: 0x00000100 -> 0x000bf780
[    0.000000]     0: 0x00100000 -> 0x00340000
[    0.000000] On node 0 totalpages: 3143439
[    0.000000]   DMA zone: 56 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3927 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 14280 pages used for memmap
[    0.000000]   DMA32 zone: 765880 pages, LIFO batch:31
[    0.000000]   Normal zone: 32256 pages used for memmap
[    0.000000]   Normal zone: 2327040 pages, LIFO batch:31
[    0.000000] ACPI: PM-Timer IO Port: 0x808
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x02] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x04] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x06] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x05] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x06] lapic_id[0x03] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x07] lapic_id[0x05] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x08] lapic_id[0x07] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x09] lapic_id[0x88] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x0a] lapic_id[0x89] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x0b] lapic_id[0x8a] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x0c] lapic_id[0x8b] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x0d] lapic_id[0x8c] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x0e] lapic_id[0x8d] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x0f] lapic_id[0x8e] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x10] lapic_id[0x8f] disabled)
[    0.000000] ACPI: IOAPIC (id[0x08] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 8, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: IOAPIC (id[0x09] address[0xfec8a000] gsi_base[24])
[    0.000000] IOAPIC[1]: apic_id 9, version 32, address 0xfec8a000, GSI 24-47
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x8086a301 base: 0xfed00000
[    0.000000] SMP: Allowing 16 CPUs, 8 hotplug CPUs
[    0.000000] nr_irqs_gsi: 64
[    0.000000] early_res array is doubled to 64 at [22000 - 227ff]
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e3000
[    0.000000] PM: Registered nosave memory: 00000000000e3000 - 0000000000100000
[    0.000000] PM: Registered nosave memory: 00000000bf780000 - 00000000bf798000
[    0.000000] PM: Registered nosave memory: 00000000bf798000 - 00000000bf7da000
[    0.000000] PM: Registered nosave memory: 00000000bf7da000 - 00000000c0000000
[    0.000000] PM: Registered nosave memory: 00000000c0000000 - 00000000fee00000
[    0.000000] PM: Registered nosave memory: 00000000fee00000 - 00000000fee01000
[    0.000000] PM: Registered nosave memory: 00000000fee01000 - 00000000ffe00000
[    0.000000] PM: Registered nosave memory: 00000000ffe00000 - 0000000100000000
[    0.000000] Allocating PCI resources starting at c0000000 (gap: c0000000:3ee00000)
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] setup_percpu: NR_CPUS:64 nr_cpumask_bits:64 nr_cpu_ids:16 nr_node_ids:1
[    0.000000] early_res array is doubled to 128 at [22800 - 237ff]
[    0.000000] PERCPU: Embedded 30 pages/cpu @ffff880001e00000 s91520 r8192 d23168 u131072
[    0.000000] pcpu-alloc: s91520 r8192 d23168 u131072 alloc=1*2097152
[    0.000000] pcpu-alloc: [0] 00 01 02 03 04 05 06 07 08 09 10 11 12 13 14 15 
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 3096847
[    0.000000] Policy zone: Normal
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.35-28-generic root=UUID=4a71cb65-5c78-4059-8810-0466baeda2d1 ro quiet splash
[    0.000000] PID hash table entries: 4096 (order: 3, 32768 bytes)
[    0.000000] Checking aperture...
[    0.000000] No AGP bridge found
[    0.000000] Calgary: detecting Calgary via BIOS EBDA area
[    0.000000] Calgary: Unable to locate Rio Grande table in EBDA - bailing!
[    0.000000] Subtract (68 early reservations)
[    0.000000]   #1 [0001000000 - 0001d18114]   TEXT DATA BSS
[    0.000000]   #2 [003756f000 - 0037ff0000]         RAMDISK
[    0.000000]   #3 [0001d19000 - 0001d19294]             BRK
[    0.000000]   #4 [00000ff790 - 0000100000]   BIOS reserved
[    0.000000]   #5 [00000ff780 - 00000ff790]    MP-table mpf
[    0.000000]   #6 [000009fc00 - 00000f1300]   BIOS reserved
[    0.000000]   #7 [00000f14bc - 00000ff780]   BIOS reserved
[    0.000000]   #8 [00000f1300 - 00000f14bc]    MP-table mpc
[    0.000000]   #9 [0000010000 - 0000012000]      TRAMPOLINE
[    0.000000]   #10 [0000012000 - 0000016000]     ACPI WAKEUP
[    0.000000]   #11 [0000016000 - 0000019000]         PGTABLE
[    0.000000]   #12 [0000019000 - 0000022000]         PGTABLE
[    0.000000]   #13 [0100000000 - 0100005000]       NODE_DATA
[    0.000000]   #14 [0001d192c0 - 0001d1a2c0]         BOOTMEM
[    0.000000]   #15 [0001d18140 - 0001d18a40]         BOOTMEM
[    0.000000]   #16 [0100005000 - 0100006000]         BOOTMEM
[    0.000000]   #17 [0100006000 - 0100007000]         BOOTMEM
[    0.000000]   #18 [0100200000 - 010aa00000]        MEMMAP 0
[    0.000000]   #19 [0001d18a40 - 0001d18bc0]         BOOTMEM
[    0.000000]   #20 [0001d1a2c0 - 0001d322c0]         BOOTMEM
[    0.000000]   #21 [0001d322c0 - 0001d4a2c0]         BOOTMEM
[    0.000000]   #22 [0001d4b000 - 0001d4c000]         BOOTMEM
[    0.000000]   #23 [0001d18bc0 - 0001d18c01]         BOOTMEM
[    0.000000]   #24 [0001d18c40 - 0001d18cc6]         BOOTMEM
[    0.000000]   #25 [0001d18d00 - 0001d18f68]         BOOTMEM
[    0.000000]   #26 [0001d18f80 - 0001d18fe8]         BOOTMEM
[    0.000000]   #27 [0001d4a2c0 - 0001d4a328]         BOOTMEM
[    0.000000]   #28 [0001d4a340 - 0001d4a3a8]         BOOTMEM
[    0.000000]   #29 [0001d4a3c0 - 0001d4a428]         BOOTMEM
[    0.000000]   #30 [0001d4a440 - 0001d4a4a8]         BOOTMEM
[    0.000000]   #31 [0001d4a4c0 - 0001d4a528]         BOOTMEM
[    0.000000]   #32 [0001d4a540 - 0001d4a5a8]         BOOTMEM
[    0.000000]   #33 [0001d4a5c0 - 0001d4a628]         BOOTMEM
[    0.000000]   #34 [0001d4a640 - 0001d4a6a8]         BOOTMEM
[    0.000000]   #35 [0001d4a6c0 - 0001d4a728]         BOOTMEM
[    0.000000]   #36 [0001d4a740 - 0001d4a760]         BOOTMEM
[    0.000000]   #37 [0001d4a780 - 0001d4a7a0]         BOOTMEM
[    0.000000]   #38 [0001d4a7c0 - 0001d4a82a]         BOOTMEM
[    0.000000]   #39 [0001d4a840 - 0001d4a8aa]         BOOTMEM
[    0.000000]   #40 [0001e00000 - 0001e1e000]         BOOTMEM
[    0.000000]   #41 [0001e20000 - 0001e3e000]         BOOTMEM
[    0.000000]   #42 [0001e40000 - 0001e5e000]         BOOTMEM
[    0.000000]   #43 [0001e60000 - 0001e7e000]         BOOTMEM
[    0.000000]   #44 [0001e80000 - 0001e9e000]         BOOTMEM
[    0.000000]   #45 [0001ea0000 - 0001ebe000]         BOOTMEM
[    0.000000]   #46 [0001ec0000 - 0001ede000]         BOOTMEM
[    0.000000]   #47 [0001ee0000 - 0001efe000]         BOOTMEM
[    0.000000]   #48 [0001f00000 - 0001f1e000]         BOOTMEM
[    0.000000]   #49 [0001f20000 - 0001f3e000]         BOOTMEM
[    0.000000]   #50 [0001f40000 - 0001f5e000]         BOOTMEM
[    0.000000]   #51 [0001f60000 - 0001f7e000]         BOOTMEM
[    0.000000]   #52 [0001f80000 - 0001f9e000]         BOOTMEM
[    0.000000]   #53 [0001fa0000 - 0001fbe000]         BOOTMEM
[    0.000000]   #54 [0001fc0000 - 0001fde000]         BOOTMEM
[    0.000000]   #55 [0001fe0000 - 0001ffe000]         BOOTMEM
[    0.000000]   #56 [0001d4a8c0 - 0001d4a8c8]         BOOTMEM
[    0.000000]   #57 [0001d4a900 - 0001d4a908]         BOOTMEM
[    0.000000]   #58 [0001d4a940 - 0001d4a980]         BOOTMEM
[    0.000000]   #59 [0001d4a980 - 0001d4aa00]         BOOTMEM
[    0.000000]   #60 [0001d4aa00 - 0001d4ab10]         BOOTMEM
[    0.000000]   #61 [0001d4ab40 - 0001d4ab88]         BOOTMEM
[    0.000000]   #62 [0001d4abc0 - 0001d4ac08]         BOOTMEM
[    0.000000]   #63 [0001d4c000 - 0001d54000]         BOOTMEM
[    0.000000]   #64 [0001ffe000 - 0005ffe000]         BOOTMEM
[    0.000000]   #65 [0001d54000 - 0001d74000]         BOOTMEM
[    0.000000]   #66 [0001d74000 - 0001db4000]         BOOTMEM
[    0.000000]   #67 [0000023800 - 000002b800]         BOOTMEM
[    0.000000] Memory: 12309344k/13631488k available (5716k kernel code, 1057732k absent, 264412k reserved, 5375k data, 912k init)
[    0.000000] SLUB: Genslabs=14, HWalign=64, Order=0-3, MinObjects=0, CPUs=16, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000] 	RCU dyntick-idle grace-period acceleration is enabled.
[    0.000000] 	RCU-based detection of stalled CPUs is disabled.
[    0.000000] 	Verbose stalled-CPUs detection is disabled.
[    0.000000] NR_IRQS:4352 nr_irqs:1216
[    0.000000] Console: colour VGA+ 80x25
[    0.000000] console [tty0] enabled
[    0.000000] allocated 125829120 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] hpet clockevent registered
[    0.000000] Fast TSC calibration failed
[    0.010000] TSC: PIT calibration matches HPET. 1 loops
[    0.010000] Detected 3207.382 MHz processor.
[    0.000007] Calibrating delay loop (skipped), value calculated using timer frequency.. 6414.76 BogoMIPS (lpj=32073820)
[    0.000011] pid_max: default: 32768 minimum: 301
[    0.000036] Security Framework initialized
[    0.000047] AppArmor: AppArmor initialized
[    0.000048] Yama: becoming mindful.
[    0.001270] Dentry cache hash table entries: 2097152 (order: 12, 16777216 bytes)
[    0.004193] Inode-cache hash table entries: 1048576 (order: 11, 8388608 bytes)
[    0.008072] Mount-cache hash table entries: 256
[    0.008164] Initializing cgroup subsys ns
[    0.008167] Initializing cgroup subsys cpuacct
[    0.008171] Initializing cgroup subsys memory
[    0.008177] Initializing cgroup subsys devices
[    0.008179] Initializing cgroup subsys freezer
[    0.008180] Initializing cgroup subsys net_cls
[    0.008200] CPU: Physical Processor ID: 0
[    0.008201] CPU: Processor Core ID: 0
[    0.008205] mce: CPU supports 9 MCE banks
[    0.008218] CPU0: Thermal monitoring enabled (TM1)
[    0.008226] using mwait in idle threads.
[    0.008227] Performance Events: PEBS fmt1+, Nehalem events, Intel PMU driver.
[    0.008233] ... version:                3
[    0.008234] ... bit width:              48
[    0.008235] ... generic registers:      4
[    0.008236] ... value mask:             0000ffffffffffff
[    0.008237] ... max period:             000000007fffffff
[    0.008238] ... fixed-purpose events:   3
[    0.008239] ... event mask:             000000070000000f
[    0.009984] ACPI: Core revision 20100428
[    0.047196] ftrace: converting mcount calls to 0f 1f 44 00 00
[    0.047202] ftrace: allocating 22688 entries in 89 pages
[    0.052801] Setting APIC routing to physical flat
[    0.053242] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.162565] CPU0: Intel(R) Core(TM) i7 CPU         960  @ 3.20GHz stepping 05
[    0.274456] Booting Node   0, Processors  #1 #2 #3 #4 #5 #6 #7
[    1.533341] Brought up 8 CPUs
[    1.533343] Total of 8 processors activated (51348.71 BogoMIPS).
[    1.536912] devtmpfs: initialized
[    1.540211] regulator: core version 0.5
[    1.540235] Time: 13:31:06  Date: 03/30/11
[    1.540268] NET: Registered protocol family 16
[    1.540350] Trying to unpack rootfs image as initramfs...
[    1.540354] ACPI: bus type pci registered
[    1.540402] PCI: MMCONFIG for domain 0000 [bus 00-ff] at [mem 0xe0000000-0xefffffff] (base 0xe0000000)
[    1.540404] PCI: not using MMCONFIG
[    1.540405] PCI: Using configuration type 1 for base access
[    1.540925] bio: create slab <bio-0> at 0
[    1.542044] ACPI: EC: Look up EC in DSDT
[    1.543158] ACPI: Executed 1 blocks of module-level executable AML code
[    1.581629] ACPI: SSDT 00000000bf7983a0 0244C (v01 DpgPmm  P001Ist 00000011 INTL 20060113)
[    1.581996] ACPI: Dynamic OEM Table Load:
[    1.581998] ACPI: SSDT (null) 0244C (v01 DpgPmm  P001Ist 00000011 INTL 20060113)
[    1.582307] ACPI: Interpreter enabled
[    1.582309] ACPI: (supports S0 S1 S3 S4 S5)
[    1.582324] ACPI: Using IOAPIC for interrupt routing
[    1.582365] PCI: MMCONFIG for domain 0000 [bus 00-ff] at [mem 0xe0000000-0xefffffff] (base 0xe0000000)
[    1.583960] PCI: MMCONFIG at [mem 0xe0000000-0xefffffff] reserved in ACPI motherboard resources
[    1.619386] ACPI: No dock devices found.
[    1.619389] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
[    1.619500] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-ff])
[    1.619719] pci_root PNP0A08:00: host bridge window [io  0x0000-0x0cf7]
[    1.619721] pci_root PNP0A08:00: host bridge window [io  0x0d00-0xffff]
[    1.619723] pci_root PNP0A08:00: host bridge window [mem 0x000a0000-0x000bffff]
[    1.619724] pci_root PNP0A08:00: host bridge window [mem 0x000d0000-0x000dffff]
[    1.619726] pci_root PNP0A08:00: host bridge window [mem 0xc0000000-0xdfffffff]
[    1.619727] pci_root PNP0A08:00: host bridge window [mem 0xf0000000-0xfed8ffff]
[    1.619775] pci 0000:00:00.0: PME# supported from D0 D3hot D3cold
[    1.619777] pci 0000:00:00.0: PME# disabled
[    1.619829] pci 0000:00:01.0: PME# supported from D0 D3hot D3cold
[    1.619831] pci 0000:00:01.0: PME# disabled
[    1.619880] pci 0000:00:02.0: PME# supported from D0 D3hot D3cold
[    1.619882] pci 0000:00:02.0: PME# disabled
[    1.619930] pci 0000:00:03.0: PME# supported from D0 D3hot D3cold
[    1.619932] pci 0000:00:03.0: PME# disabled
[    1.619983] pci 0000:00:07.0: PME# supported from D0 D3hot D3cold
[    1.619986] pci 0000:00:07.0: PME# disabled
[    1.620179] pci 0000:00:1a.0: reg 20: [io  0xa800-0xa81f]
[    1.620234] pci 0000:00:1a.1: reg 20: [io  0xa880-0xa89f]
[    1.620290] pci 0000:00:1a.2: reg 20: [io  0xac00-0xac1f]
[    1.620344] pci 0000:00:1a.7: reg 10: [mem 0xf7dff000-0xf7dff3ff]
[    1.620392] pci 0000:00:1a.7: PME# supported from D0 D3hot D3cold
[    1.620395] pci 0000:00:1a.7: PME# disabled
[    1.620424] pci 0000:00:1b.0: reg 10: [mem 0xf7df8000-0xf7dfbfff 64bit]
[    1.620459] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    1.620462] pci 0000:00:1b.0: PME# disabled
[    1.620517] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    1.620520] pci 0000:00:1c.0: PME# disabled
[    1.620579] pci 0000:00:1c.4: PME# supported from D0 D3hot D3cold
[    1.620582] pci 0000:00:1c.4: PME# disabled
[    1.620625] pci 0000:00:1d.0: reg 20: [io  0xa080-0xa09f]
[    1.620682] pci 0000:00:1d.1: reg 20: [io  0xa400-0xa41f]
[    1.620738] pci 0000:00:1d.2: reg 20: [io  0xa480-0xa49f]
[    1.620792] pci 0000:00:1d.7: reg 10: [mem 0xf7dfe000-0xf7dfe3ff]
[    1.620840] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
[    1.620843] pci 0000:00:1d.7: PME# disabled
[    1.620943] pci 0000:00:1f.0: quirk: [io  0x0800-0x087f] claimed by ICH6 ACPI/GPIO/TCO
[    1.620945] pci 0000:00:1f.0: quirk: [io  0x0500-0x053f] claimed by ICH6 GPIO
[    1.620948] pci 0000:00:1f.0: ICH7 LPC Generic IO decode 1 PIO at 0294 (mask 0003)
[    1.620990] pci 0000:00:1f.2: reg 10: [io  0x9000-0x9007]
[    1.620995] pci 0000:00:1f.2: reg 14: [io  0x8c00-0x8c03]
[    1.620999] pci 0000:00:1f.2: reg 18: [io  0x8880-0x8887]
[    1.621003] pci 0000:00:1f.2: reg 1c: [io  0x8800-0x8803]
[    1.621007] pci 0000:00:1f.2: reg 20: [io  0x8480-0x848f]
[    1.621011] pci 0000:00:1f.2: reg 24: [io  0x8400-0x840f]
[    1.621049] pci 0000:00:1f.3: reg 10: [mem 0xf7dfd000-0xf7dfd0ff 64bit]
[    1.621060] pci 0000:00:1f.3: reg 20: [io  0x1000-0x101f]
[    1.621092] pci 0000:00:1f.5: reg 10: [io  0xa000-0xa007]
[    1.621096] pci 0000:00:1f.5: reg 14: [io  0x9c00-0x9c03]
[    1.621100] pci 0000:00:1f.5: reg 18: [io  0x9880-0x9887]
[    1.621104] pci 0000:00:1f.5: reg 1c: [io  0x9800-0x9803]
[    1.621109] pci 0000:00:1f.5: reg 20: [io  0x9480-0x948f]
[    1.621113] pci 0000:00:1f.5: reg 24: [io  0x9400-0x940f]
[    1.621183] pci 0000:01:00.0: reg 10: [io  0xbc00-0xbc07]
[    1.621187] pci 0000:01:00.0: reg 14: [io  0xb880-0xb883]
[    1.621191] pci 0000:01:00.0: reg 18: [io  0xb800-0xb807]
[    1.621195] pci 0000:01:00.0: reg 1c: [io  0xb480-0xb483]
[    1.621199] pci 0000:01:00.0: reg 20: [io  0xb400-0xb40f]
[    1.621203] pci 0000:01:00.0: reg 24: [mem 0xf7eff800-0xf7efffff]
[    1.621208] pci 0000:01:00.0: reg 30: [mem 0xf7ee0000-0xf7eeffff pref]
[    1.621226] pci 0000:01:00.0: PME# supported from D3hot
[    1.621228] pci 0000:01:00.0: PME# disabled
[    1.633158] pci 0000:00:01.0: PCI bridge to [bus 01-01]
[    1.633162] pci 0000:00:01.0:   bridge window [io  0xb000-0xbfff]
[    1.633165] pci 0000:00:01.0:   bridge window [mem 0xf7e00000-0xf7efffff]
[    1.633169] pci 0000:00:01.0:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    1.633228] pci 0000:02:00.0: reg 10: [mem 0xf7ffe000-0xf7ffffff 64bit]
[    1.633275] pci 0000:02:00.0: PME# supported from D0 D3hot D3cold
[    1.633278] pci 0000:02:00.0: PME# disabled
[    1.653133] pci 0000:00:02.0: PCI bridge to [bus 02-02]
[    1.653136] pci 0000:00:02.0:   bridge window [io  0xf000-0x0000] (disabled)
[    1.653140] pci 0000:00:02.0:   bridge window [mem 0xf7f00000-0xf7ffffff]
[    1.653143] pci 0000:00:02.0:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    1.653192] pci 0000:03:00.0: reg 10: [mem 0xf8000000-0xf9ffffff]
[    1.653199] pci 0000:03:00.0: reg 14: [mem 0xd8000000-0xdfffffff 64bit pref]
[    1.653206] pci 0000:03:00.0: reg 1c: [mem 0xd4000000-0xd7ffffff 64bit pref]
[    1.653210] pci 0000:03:00.0: reg 24: [io  0xcc00-0xcc7f]
[    1.653214] pci 0000:03:00.0: reg 30: [mem 0xfbc00000-0xfbc7ffff pref]
[    1.653259] pci 0000:03:00.1: reg 10: [mem 0xfbcfc000-0xfbcfffff]
[    1.673117] pci 0000:00:03.0: PCI bridge to [bus 03-03]
[    1.673121] pci 0000:00:03.0:   bridge window [io  0xc000-0xcfff]
[    1.673124] pci 0000:00:03.0:   bridge window [mem 0xf8000000-0xfbcfffff]
[    1.673128] pci 0000:00:03.0:   bridge window [mem 0xd4000000-0xdfffffff 64bit pref]
[    1.673161] pci 0000:00:07.0: PCI bridge to [bus 04-04]
[    1.673164] pci 0000:00:07.0:   bridge window [io  0xf000-0x0000] (disabled)
[    1.673166] pci 0000:00:07.0:   bridge window [mem 0xfff00000-0x000fffff] (disabled)
[    1.673170] pci 0000:00:07.0:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    1.673205] pci 0000:00:1c.0: PCI bridge to [bus 06-06]
[    1.673208] pci 0000:00:1c.0:   bridge window [io  0xf000-0x0000] (disabled)
[    1.673211] pci 0000:00:1c.0:   bridge window [mem 0xfff00000-0x000fffff] (disabled)
[    1.673215] pci 0000:00:1c.0:   bridge window [mem 0xf6f00000-0xf6ffffff 64bit pref]
[    1.673288] pci 0000:05:00.0: reg 10: [io  0xdc00-0xdc07]
[    1.673295] pci 0000:05:00.0: reg 14: [io  0xd880-0xd883]
[    1.673303] pci 0000:05:00.0: reg 18: [io  0xd800-0xd807]
[    1.673311] pci 0000:05:00.0: reg 1c: [io  0xd480-0xd483]
[    1.673318] pci 0000:05:00.0: reg 20: [io  0xd400-0xd40f]
[    1.673326] pci 0000:05:00.0: reg 24: [mem 0xfbdffc00-0xfbdffdff]
[    1.673334] pci 0000:05:00.0: reg 30: [mem 0x00000000-0x0000ffff pref]
[    1.673365] pci 0000:05:00.0: PME# supported from D3hot
[    1.673370] pci 0000:05:00.0: PME# disabled
[    1.694123] pci 0000:00:1c.4: PCI bridge to [bus 05-05]
[    1.694127] pci 0000:00:1c.4:   bridge window [io  0xd000-0xdfff]
[    1.694130] pci 0000:00:1c.4:   bridge window [mem 0xfbd00000-0xfbdfffff]
[    1.694134] pci 0000:00:1c.4:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    1.694182] pci 0000:07:01.0: reg 10: [io  0xe800-0xe8ff]
[    1.694187] pci 0000:07:01.0: reg 14: [mem 0xfbeffc00-0xfbeffcff]
[    1.694209] pci 0000:07:01.0: reg 30: [mem 0xfbec0000-0xfbedffff pref]
[    1.694231] pci 0000:07:01.0: supports D1 D2
[    1.694233] pci 0000:07:01.0: PME# supported from D1 D2 D3hot D3cold
[    1.694236] pci 0000:07:01.0: PME# disabled
[    1.694263] pci 0000:07:02.0: reg 10: [mem 0xfbefe000-0xfbefe7ff]
[    1.694268] pci 0000:07:02.0: reg 14: [io  0xec00-0xec7f]
[    1.694306] pci 0000:07:02.0: supports D2
[    1.694308] pci 0000:07:02.0: PME# supported from D2 D3hot D3cold
[    1.694311] pci 0000:07:02.0: PME# disabled
[    1.694348] pci 0000:00:1e.0: PCI bridge to [bus 07-07] (subtractive decode)
[    1.694351] pci 0000:00:1e.0:   bridge window [io  0xe000-0xefff]
[    1.694354] pci 0000:00:1e.0:   bridge window [mem 0xfbe00000-0xfbefffff]
[    1.694359] pci 0000:00:1e.0:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    1.694361] pci 0000:00:1e.0:   bridge window [io  0x0000-0x0cf7] (subtractive decode)
[    1.694362] pci 0000:00:1e.0:   bridge window [io  0x0d00-0xffff] (subtractive decode)
[    1.694364] pci 0000:00:1e.0:   bridge window [mem 0x000a0000-0x000bffff] (subtractive decode)
[    1.694365] pci 0000:00:1e.0:   bridge window [mem 0x000d0000-0x000dffff] (subtractive decode)
[    1.694367] pci 0000:00:1e.0:   bridge window [mem 0xc0000000-0xdfffffff] (subtractive decode)
[    1.694368] pci 0000:00:1e.0:   bridge window [mem 0xf0000000-0xfed8ffff] (subtractive decode)
[    1.694399] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    1.694618] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P1._PRT]
[    1.694700] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P4._PRT]
[    1.694749] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P8._PRT]
[    1.694802] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.NPE1._PRT]
[    1.694845] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.NPE2._PRT]
[    1.694886] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.NPE3._PRT]
[    1.694926] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.NPE7._PRT]
[    1.716149] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 6 7 10 *11 12 14 15)
[    1.716240] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 6 7 *10 11 12 14 15)
[    1.716328] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 6 7 10 11 12 *14 15)
[    1.716416] ACPI: PCI Interrupt Link [LNKD] (IRQs *3 4 6 7 10 11 12 14 15)
[    1.716504] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 6 7 10 11 12 14 *15)
[    1.716591] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 6 *7 10 11 12 14 15)
[    1.716683] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 *6 7 10 11 12 14 15)
[    1.716771] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 6 7 *10 11 12 14 15)
[    1.716808] HEST: Table is not found!
[    1.716860] vgaarb: device added: PCI:0000:03:00.0,decodes=io+mem,owns=io+mem,locks=none
[    1.716862] vgaarb: loaded
[    1.716946] SCSI subsystem initialized
[    1.717055] libata version 3.00 loaded.
[    1.717083] usbcore: registered new interface driver usbfs
[    1.717091] usbcore: registered new interface driver hub
[    1.717107] usbcore: registered new device driver usb
[    1.717201] ACPI: WMI: Mapper loaded
[    1.717203] PCI: Using ACPI for IRQ routing
[    1.717204] PCI: pci_cache_line_size set to 64 bytes
[    1.717288] reserve RAM buffer: 000000000009fc00 - 000000000009ffff 
[    1.717290] reserve RAM buffer: 00000000bf780000 - 00000000bfffffff 
[    1.717351] NetLabel: Initializing
[    1.717352] NetLabel:  domain hash size = 128
[    1.717353] NetLabel:  protocols = UNLABELED CIPSOv4
[    1.717361] NetLabel:  unlabeled traffic allowed by default
[    1.717379] HPET: 4 timers in total, 0 timers will be used for per-cpu timer
[    1.717384] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0
[    1.717386] hpet0: 4 comparators, 64-bit 14.318180 MHz counter
[    1.754503] Freeing initrd memory: 10756k freed
[    1.773165] Switching to clocksource tsc
[    1.778298] AppArmor: AppArmor Filesystem Enabled
[    1.778308] pnp: PnP ACPI init
[    1.778318] ACPI: bus type pnp registered
[    1.783262] pnp: PnP ACPI: found 15 devices
[    1.783263] ACPI: ACPI bus type pnp unregistered
[    1.783273] system 00:01: [mem 0xfbf00000-0xfbffffff] has been reserved
[    1.783274] system 00:01: [mem 0xfc000000-0xfcffffff] has been reserved
[    1.783276] system 00:01: [mem 0xfd000000-0xfdffffff] has been reserved
[    1.783277] system 00:01: [mem 0xfe000000-0xfebfffff] has been reserved
[    1.783279] system 00:01: [mem 0xfec8a000-0xfec8afff] could not be reserved
[    1.783281] system 00:01: [mem 0xfed10000-0xfed10fff] has been reserved
[    1.783286] system 00:06: [io  0x0290-0x029f] has been reserved
[    1.783290] system 00:07: [io  0x04d0-0x04d1] has been reserved
[    1.783291] system 00:07: [io  0x0800-0x087f] has been reserved
[    1.783293] system 00:07: [io  0x0500-0x057f] could not be reserved
[    1.783294] system 00:07: [io  0x0600-0x0607] has been reserved
[    1.783296] system 00:07: [mem 0xfed1c000-0xfed1ffff] has been reserved
[    1.783298] system 00:07: [mem 0xfed20000-0xfed3ffff] has been reserved
[    1.783299] system 00:07: [mem 0xfed40000-0xfed8ffff] has been reserved
[    1.783305] system 00:0a: [mem 0xffc00000-0xffdfffff] has been reserved
[    1.783308] system 00:0b: [mem 0xfec00000-0xfec00fff] could not be reserved
[    1.783309] system 00:0b: [mem 0xfee00000-0xfee00fff] has been reserved
[    1.783312] system 00:0d: [mem 0xe0000000-0xefffffff] has been reserved
[    1.783315] system 00:0e: [mem 0x00000000-0x0009ffff] could not be reserved
[    1.783317] system 00:0e: [mem 0x000c0000-0x000cffff] has been reserved
[    1.783318] system 00:0e: [mem 0x000e0000-0x000fffff] could not be reserved
[    1.783320] system 00:0e: [mem 0x00100000-0xbfffffff] could not be reserved
[    1.783321] system 00:0e: [mem 0xfed90000-0xffffffff] could not be reserved
[    1.788679] pci 0000:00:1c.0: BAR 14: assigned [mem 0xc0000000-0xc03fffff]
[    1.788681] pci 0000:00:1c.4: BAR 15: assigned [mem 0xc0400000-0xc05fffff pref]
[    1.788683] pci 0000:00:1c.0: BAR 13: assigned [io  0x2000-0x2fff]
[    1.788685] pci 0000:00:01.0: PCI bridge to [bus 01-01]
[    1.788687] pci 0000:00:01.0:   bridge window [io  0xb000-0xbfff]
[    1.788690] pci 0000:00:01.0:   bridge window [mem 0xf7e00000-0xf7efffff]
[    1.788692] pci 0000:00:01.0:   bridge window [mem pref disabled]
[    1.788696] pci 0000:00:02.0: PCI bridge to [bus 02-02]
[    1.788697] pci 0000:00:02.0:   bridge window [io  disabled]
[    1.788700] pci 0000:00:02.0:   bridge window [mem 0xf7f00000-0xf7ffffff]
[    1.788703] pci 0000:00:02.0:   bridge window [mem pref disabled]
[    1.788707] pci 0000:00:03.0: PCI bridge to [bus 03-03]
[    1.788708] pci 0000:00:03.0:   bridge window [io  0xc000-0xcfff]
[    1.788712] pci 0000:00:03.0:   bridge window [mem 0xf8000000-0xfbcfffff]
[    1.788714] pci 0000:00:03.0:   bridge window [mem 0xd4000000-0xdfffffff 64bit pref]
[    1.788718] pci 0000:00:07.0: PCI bridge to [bus 04-04]
[    1.788719] pci 0000:00:07.0:   bridge window [io  disabled]
[    1.788722] pci 0000:00:07.0:   bridge window [mem disabled]
[    1.788724] pci 0000:00:07.0:   bridge window [mem pref disabled]
[    1.788728] pci 0000:00:1c.0: PCI bridge to [bus 06-06]
[    1.788730] pci 0000:00:1c.0:   bridge window [io  0x2000-0x2fff]
[    1.788734] pci 0000:00:1c.0:   bridge window [mem 0xc0000000-0xc03fffff]
[    1.788737] pci 0000:00:1c.0:   bridge window [mem 0xf6f00000-0xf6ffffff 64bit pref]
[    1.788742] pci 0000:05:00.0: BAR 6: assigned [mem 0xc0400000-0xc040ffff pref]
[    1.788743] pci 0000:00:1c.4: PCI bridge to [bus 05-05]
[    1.788745] pci 0000:00:1c.4:   bridge window [io  0xd000-0xdfff]
[    1.788749] pci 0000:00:1c.4:   bridge window [mem 0xfbd00000-0xfbdfffff]
[    1.788751] pci 0000:00:1c.4:   bridge window [mem 0xc0400000-0xc05fffff pref]
[    1.788756] pci 0000:00:1e.0: PCI bridge to [bus 07-07]
[    1.788758] pci 0000:00:1e.0:   bridge window [io  0xe000-0xefff]
[    1.788761] pci 0000:00:1e.0:   bridge window [mem 0xfbe00000-0xfbefffff]
[    1.788764] pci 0000:00:1e.0:   bridge window [mem pref disabled]
[    1.788775] pci 0000:00:01.0: setting latency timer to 64
[    1.788781] pci 0000:00:02.0: setting latency timer to 64
[    1.788787] pci 0000:00:03.0: setting latency timer to 64
[    1.788793] pci 0000:00:07.0: setting latency timer to 64
[    1.788799] pci 0000:00:1c.0: enabling device (0106 -> 0107)
[    1.788803]   alloc irq_desc for 17 on node -1
[    1.788804]   alloc kstat_irqs on node -1
[    1.788808] pci 0000:00:1c.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    1.788811] pci 0000:00:1c.0: setting latency timer to 64
[    1.788817] pci 0000:00:1c.4: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    1.788819] pci 0000:00:1c.4: setting latency timer to 64
[    1.788824] pci 0000:00:1e.0: setting latency timer to 64
[    1.788827] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
[    1.788828] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff]
[    1.788829] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
[    1.788831] pci_bus 0000:00: resource 7 [mem 0x000d0000-0x000dffff]
[    1.788832] pci_bus 0000:00: resource 8 [mem 0xc0000000-0xdfffffff]
[    1.788833] pci_bus 0000:00: resource 9 [mem 0xf0000000-0xfed8ffff]
[    1.788835] pci_bus 0000:01: resource 0 [io  0xb000-0xbfff]
[    1.788836] pci_bus 0000:01: resource 1 [mem 0xf7e00000-0xf7efffff]
[    1.788837] pci_bus 0000:02: resource 1 [mem 0xf7f00000-0xf7ffffff]
[    1.788839] pci_bus 0000:03: resource 0 [io  0xc000-0xcfff]
[    1.788840] pci_bus 0000:03: resource 1 [mem 0xf8000000-0xfbcfffff]
[    1.788841] pci_bus 0000:03: resource 2 [mem 0xd4000000-0xdfffffff 64bit pref]
[    1.788843] pci_bus 0000:06: resource 0 [io  0x2000-0x2fff]
[    1.788844] pci_bus 0000:06: resource 1 [mem 0xc0000000-0xc03fffff]
[    1.788845] pci_bus 0000:06: resource 2 [mem 0xf6f00000-0xf6ffffff 64bit pref]
[    1.788847] pci_bus 0000:05: resource 0 [io  0xd000-0xdfff]
[    1.788848] pci_bus 0000:05: resource 1 [mem 0xfbd00000-0xfbdfffff]
[    1.788849] pci_bus 0000:05: resource 2 [mem 0xc0400000-0xc05fffff pref]
[    1.788851] pci_bus 0000:07: resource 0 [io  0xe000-0xefff]
[    1.788852] pci_bus 0000:07: resource 1 [mem 0xfbe00000-0xfbefffff]
[    1.788853] pci_bus 0000:07: resource 4 [io  0x0000-0x0cf7]
[    1.788854] pci_bus 0000:07: resource 5 [io  0x0d00-0xffff]
[    1.788856] pci_bus 0000:07: resource 6 [mem 0x000a0000-0x000bffff]
[    1.788857] pci_bus 0000:07: resource 7 [mem 0x000d0000-0x000dffff]
[    1.788858] pci_bus 0000:07: resource 8 [mem 0xc0000000-0xdfffffff]
[    1.788859] pci_bus 0000:07: resource 9 [mem 0xf0000000-0xfed8ffff]
[    1.788881] NET: Registered protocol family 2
[    1.789163] IP route cache hash table entries: 524288 (order: 10, 4194304 bytes)
[    1.790101] TCP established hash table entries: 524288 (order: 11, 8388608 bytes)
[    1.791266] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[    1.791393] TCP: Hash tables configured (established 524288 bind 65536)
[    1.791394] TCP reno registered
[    1.791413] UDP hash table entries: 8192 (order: 6, 262144 bytes)
[    1.791467] UDP-Lite hash table entries: 8192 (order: 6, 262144 bytes)
[    1.791581] NET: Registered protocol family 1
[    1.793780] pci 0000:02:00.0: xHCI HW did not halt within 2000 usec status = 0x0
[    1.793794] pci 0000:03:00.0: Boot video device
[    1.793807] PCI: CLS mismatch (256 != 64), using 64 bytes
[    1.793810] PCI-DMA: Using software bounce buffering for IO (SWIOTLB)
[    1.793811] Placing 64MB software IO TLB between ffff880001ffe000 - ffff880005ffe000
[    1.793813] software IO TLB at phys 0x1ffe000 - 0x5ffe000
[    1.794128] Scanning for low memory corruption every 60 seconds
[    1.794209] audit: initializing netlink socket (disabled)
[    1.794214] type=2000 audit(1301491865.600:1): initialized
[    4.637789] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    4.638716] VFS: Disk quotas dquot_6.5.2
[    4.638755] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    4.639126] fuse init (API version 7.14)
[    4.639179] msgmni has been set to 24062
[    4.640586] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    4.640588] io scheduler noop registered
[    4.640589] io scheduler deadline registered
[    4.640613] io scheduler cfq registered (default)
[    4.640689] pcieport 0000:00:01.0: setting latency timer to 64
[    4.640713]   alloc irq_desc for 64 on node -1
[    4.640714]   alloc kstat_irqs on node -1
[    4.640725] pcieport 0000:00:01.0: irq 64 for MSI/MSI-X
[    4.640773] pcieport 0000:00:02.0: setting latency timer to 64
[    4.640795]   alloc irq_desc for 65 on node -1
[    4.640796]   alloc kstat_irqs on node -1
[    4.640800] pcieport 0000:00:02.0: irq 65 for MSI/MSI-X
[    4.640846] pcieport 0000:00:03.0: setting latency timer to 64
[    4.640868]   alloc irq_desc for 66 on node -1
[    4.640869]   alloc kstat_irqs on node -1
[    4.640873] pcieport 0000:00:03.0: irq 66 for MSI/MSI-X
[    4.640918] pcieport 0000:00:07.0: setting latency timer to 64
[    4.640940]   alloc irq_desc for 67 on node -1
[    4.640941]   alloc kstat_irqs on node -1
[    4.640945] pcieport 0000:00:07.0: irq 67 for MSI/MSI-X
[    4.640991] pcieport 0000:00:1c.0: setting latency timer to 64
[    4.641017]   alloc irq_desc for 68 on node -1
[    4.641018]   alloc kstat_irqs on node -1
[    4.641022] pcieport 0000:00:1c.0: irq 68 for MSI/MSI-X
[    4.641077] pcieport 0000:00:1c.4: setting latency timer to 64
[    4.641102]   alloc irq_desc for 69 on node -1
[    4.641103]   alloc kstat_irqs on node -1
[    4.641108] pcieport 0000:00:1c.4: irq 69 for MSI/MSI-X
[    4.641170] aer 0000:00:01.0:pcie02: AER service couldn't init device: no _OSC support
[    4.641174] aer 0000:00:02.0:pcie02: AER service couldn't init device: no _OSC support
[    4.641177] aer 0000:00:03.0:pcie02: AER service couldn't init device: no _OSC support
[    4.641180] aer 0000:00:07.0:pcie02: AER service couldn't init device: no _OSC support
[    4.641190] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    4.641236] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    4.641281] intel_idle: MWAIT substates: 0x1120
[    4.641282] intel_idle: v0.4 model 0x1A
[    4.641283] intel_idle: lapic_timer_reliable_states 0x2
[    4.641367] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0
[    4.641371] ACPI: Power Button [PWRB]
[    4.641395] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
[    4.641397] ACPI: Power Button [PWRF]
[    4.641646] ACPI: acpi_idle yielding to intel_idle
[    4.643620] ERST: Table is not found!
[    4.643750] Linux agpgart interface v0.103
[    4.643762] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    4.643848] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    4.644091] 00:0c: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    4.644716] brd: module loaded
[    4.648215] loop: module loaded
[    4.648346] ata_piix 0000:00:1f.2: version 2.13
[    4.648359]   alloc irq_desc for 20 on node -1
[    4.648360]   alloc kstat_irqs on node -1
[    4.648366] ata_piix 0000:00:1f.2: PCI INT B -> GSI 20 (level, low) -> IRQ 20
[    4.648371] ata_piix 0000:00:1f.2: MAP [ P0 P2 P1 P3 ]
[    4.648397] ata_piix 0000:00:1f.2: setting latency timer to 64
[    4.648455] scsi0 : ata_piix
[    4.648502] scsi1 : ata_piix
[    4.649394] ata1: SATA max UDMA/133 cmd 0x9000 ctl 0x8c00 bmdma 0x8480 irq 20
[    4.649399] ata2: SATA max UDMA/133 cmd 0x8880 ctl 0x8800 bmdma 0x8488 irq 20
[    4.649415] ata_piix 0000:00:1f.5: PCI INT B -> GSI 20 (level, low) -> IRQ 20
[    4.649419] ata_piix 0000:00:1f.5: MAP [ P0 -- P1 -- ]
[    4.649444] ata_piix 0000:00:1f.5: setting latency timer to 64
[    4.649468] scsi2 : ata_piix
[    4.649502] scsi3 : ata_piix
[    4.650280] ata3: SATA max UDMA/133 cmd 0xa000 ctl 0x9c00 bmdma 0x9480 irq 20
[    4.650283] ata4: SATA max UDMA/133 cmd 0x9880 ctl 0x9800 bmdma 0x9488 irq 20
[    4.650321]   alloc irq_desc for 28 on node -1
[    4.650322]   alloc kstat_irqs on node -1
[    4.650327] pata_acpi 0000:01:00.0: PCI INT A -> GSI 28 (level, low) -> IRQ 28
[    4.650340] pata_acpi 0000:01:00.0: setting latency timer to 64
[    4.650348] pata_acpi 0000:01:00.0: PCI INT A disabled
[    4.650500] Fixed MDIO Bus: probed
[    4.650516] PPP generic driver version 2.4.2
[    4.650537] tun: Universal TUN/TAP device driver, 1.6
[    4.650538] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    4.650582] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    4.650594]   alloc irq_desc for 18 on node -1
[    4.650595]   alloc kstat_irqs on node -1
[    4.650598] ehci_hcd 0000:00:1a.7: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    4.650619] ehci_hcd 0000:00:1a.7: setting latency timer to 64
[    4.650622] ehci_hcd 0000:00:1a.7: EHCI Host Controller
[    4.650645] ehci_hcd 0000:00:1a.7: new USB bus registered, assigned bus number 1
[    4.650666] ehci_hcd 0000:00:1a.7: debug port 1
[    4.654559] ehci_hcd 0000:00:1a.7: cache line size of 64 is not supported
[    4.654569] ehci_hcd 0000:00:1a.7: irq 18, io mem 0xf7dff000
[    4.672061] ehci_hcd 0000:00:1a.7: USB 2.0 started, EHCI 1.00
[    4.672187] hub 1-0:1.0: USB hub found
[    4.672190] hub 1-0:1.0: 6 ports detected
[    4.672248]   alloc irq_desc for 23 on node -1
[    4.672249]   alloc kstat_irqs on node -1
[    4.672255] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    4.672273] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    4.672275] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    4.672301] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 2
[    4.672320] ehci_hcd 0000:00:1d.7: debug port 1
[    4.676207] ehci_hcd 0000:00:1d.7: cache line size of 64 is not supported
[    4.676220] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xf7dfe000
[    4.692041] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    4.692166] hub 2-0:1.0: USB hub found
[    4.692169] hub 2-0:1.0: 6 ports detected
[    4.692225] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    4.692234] uhci_hcd: USB Universal Host Controller Interface driver
[    4.692280]   alloc irq_desc for 16 on node -1
[    4.692281]   alloc kstat_irqs on node -1
[    4.692287] uhci_hcd 0000:00:1a.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    4.692292] uhci_hcd 0000:00:1a.0: setting latency timer to 64
[    4.692295] uhci_hcd 0000:00:1a.0: UHCI Host Controller
[    4.692317] uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 3
[    4.692347] uhci_hcd 0000:00:1a.0: irq 16, io base 0x0000a800
[    4.692414] hub 3-0:1.0: USB hub found
[    4.692417] hub 3-0:1.0: 2 ports detected
[    4.692455]   alloc irq_desc for 21 on node -1
[    4.692456]   alloc kstat_irqs on node -1
[    4.692459] uhci_hcd 0000:00:1a.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[    4.692463] uhci_hcd 0000:00:1a.1: setting latency timer to 64
[    4.692465] uhci_hcd 0000:00:1a.1: UHCI Host Controller
[    4.692484] uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus number 4
[    4.692512] uhci_hcd 0000:00:1a.1: irq 21, io base 0x0000a880
[    4.692575] hub 4-0:1.0: USB hub found
[    4.692577] hub 4-0:1.0: 2 ports detected
[    4.692614]   alloc irq_desc for 19 on node -1
[    4.692615]   alloc kstat_irqs on node -1
[    4.692618] uhci_hcd 0000:00:1a.2: PCI INT D -> GSI 19 (level, low) -> IRQ 19
[    4.692622] uhci_hcd 0000:00:1a.2: setting latency timer to 64
[    4.692624] uhci_hcd 0000:00:1a.2: UHCI Host Controller
[    4.692644] uhci_hcd 0000:00:1a.2: new USB bus registered, assigned bus number 5
[    4.692670] uhci_hcd 0000:00:1a.2: irq 19, io base 0x0000ac00
[    4.692737] hub 5-0:1.0: USB hub found
[    4.692739] hub 5-0:1.0: 2 ports detected
[    4.692775] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    4.692779] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    4.692781] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    4.692801] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 6
[    4.692822] uhci_hcd 0000:00:1d.0: irq 23, io base 0x0000a080
[    4.692886] hub 6-0:1.0: USB hub found
[    4.692888] hub 6-0:1.0: 2 ports detected
[    4.692927] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    4.692931] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    4.692933] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    4.692952] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 7
[    4.692971] uhci_hcd 0000:00:1d.1: irq 19, io base 0x0000a400
[    4.693035] hub 7-0:1.0: USB hub found
[    4.693037] hub 7-0:1.0: 2 ports detected
[    4.693073] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    4.693078] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    4.693080] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    4.693097] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 8
[    4.693118] uhci_hcd 0000:00:1d.2: irq 18, io base 0x0000a480
[    4.693179] hub 8-0:1.0: USB hub found
[    4.693181] hub 8-0:1.0: 2 ports detected
[    4.693254] PNP: No PS/2 controller found. Probing ports directly.
[    4.696131] serio: i8042 KBD port at 0x60,0x64 irq 1
[    4.696135] serio: i8042 AUX port at 0x60,0x64 irq 12
[    4.696185] mice: PS/2 mouse device common for all mice
[    4.696245] rtc_cmos 00:03: RTC can wake from S4
[    4.696267] rtc_cmos 00:03: rtc core: registered rtc_cmos as rtc0
[    4.696289] rtc0: alarms up to one month, y3k, 114 bytes nvram, hpet irqs
[    4.696347] device-mapper: uevent: version 1.0.3
[    4.696418] device-mapper: ioctl: 4.17.0-ioctl (2010-03-05) initialised: dm-devel@redhat.com
[    4.696515] device-mapper: multipath: version 1.1.1 loaded
[    4.696517] device-mapper: multipath round-robin: version 1.0.0 loaded
[    4.696832] cpuidle: using governor ladder
[    4.697017] cpuidle: using governor menu
[    4.697192] TCP cubic registered
[    4.697265] NET: Registered protocol family 10
[    4.697507] lo: Disabled Privacy Extensions
[    4.697629] NET: Registered protocol family 17
[    4.702950] PM: Resume from disk failed.
[    4.702957] registered taskstats version 1
[    4.703271]   Magic number: 3:93:535
[    4.703285] bdi 1:13: hash matches
[    4.703447] rtc_cmos 00:03: setting system clock to 2011-03-30 13:31:09 UTC (1301491869)
[    4.703452] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    4.703455] EDD information not available.
[    5.003825] ata4: SATA link down (SStatus 0 SControl 300)
[    5.016617] ata3: SATA link down (SStatus 0 SControl 300)
[    5.290425] usb 8-1: new low speed USB device using uhci_hcd and address 2
[    5.354063] ata2.00: SATA link down (SStatus 0 SControl 300)
[    5.354076] ata2.01: SATA link down (SStatus 0 SControl 300)
[    5.510234] ata1.00: SATA link down (SStatus 0 SControl 300)
[    5.510248] ata1.01: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    5.542840] ata1.01: ATA-8: Hitachi HDS721050CLA362, JP2OA3MA, max UDMA/133
[    5.542843] ata1.01: 976773168 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    5.580491] ata1.01: configured for UDMA/133
[    5.580792] scsi 0:0:1:0: Direct-Access     ATA      Hitachi HDS72105 JP2O PQ: 0 ANSI: 5
[    5.580957] sd 0:0:1:0: Attached scsi generic sg0 type 0
[    5.581012] sd 0:0:1:0: [sda] 976773168 512-byte logical blocks: (500 GB/465 GiB)
[    5.581101] sd 0:0:1:0: [sda] Write Protect is off
[    5.581105] sd 0:0:1:0: [sda] Mode Sense: 00 3a 00 00
[    5.581146] sd 0:0:1:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    5.581366]  sda: sda1 sda2 < sda5 >
[    5.626189] sd 0:0:1:0: [sda] Attached SCSI disk
[    5.626284] Freeing unused kernel memory: 912k freed
[    5.626434] Write protecting the kernel read-only data: 10240k
[    5.627233] Freeing unused kernel memory: 408k freed
[    5.627826] Freeing unused kernel memory: 1640k freed
[    5.644860] udev[155]: starting version 163
[    5.690566] firewire_ohci 0000:07:02.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    5.690638] ahci 0000:05:00.0: version 3.0
[    5.690652] ahci 0000:05:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    5.690733] ahci 0000:05:00.0: AHCI 0001.0100 32 slots 2 ports 3 Gbps 0x3 impl SATA mode
[    5.690735] ahci 0000:05:00.0: flags: 64bit ncq pm led clo pmp pio slum part 
[    5.690740] ahci 0000:05:00.0: setting latency timer to 64
[    5.690882] scsi4 : ahci
[    5.690935] scsi5 : ahci
[    5.690995] ata5: SATA max UDMA/133 abar m512@0xfbdffc00 port 0xfbdffd00 irq 16
[    5.690998] ata6: SATA max UDMA/133 abar m512@0xfbdffc00 port 0xfbdffd80 irq 16
[    5.692063] usbcore: registered new interface driver hiddev
[    5.705466] input: PIXART USB OPTICAL MOUSE as /devices/pci0000:00/0000:00:1d.2/usb8/8-1/8-1:1.0/input/input2
[    5.705544] generic-usb 0003:093A:2510.0001: input,hidraw0: USB HID v1.11 Mouse [PIXART USB OPTICAL MOUSE] on usb-0000:00:1d.2-1/input0
[    5.705562] usbcore: registered new interface driver usbhid
[    5.705564] usbhid: USB HID core driver
[    5.771221] usb 8-2: new low speed USB device using uhci_hcd and address 3
[    5.851114] firewire_ohci: Added fw-ohci device 0000:07:02.0, OHCI v1.10, 4 IR + 8 IT contexts, quirks 0x1
[    5.851204] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    5.851227] r8169 0000:07:01.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    5.851454] r8169 0000:07:01.0: (unregistered net_device): no PCI Express capability
[    5.851760] r8169 0000:07:01.0: eth0: RTL8169sc/8110sc at 0xffffc90001874c00, bc:ae:c5:5e:48:52, XID 18000000 IRQ 19
[    5.990290] input: Generic USB Keyboard as /devices/pci0000:00/0000:00:1d.2/usb8/8-2/8-2:1.0/input/input3
[    5.990417] generic-usb 0003:040B:2000.0002: input,hidraw1: USB HID v1.10 Keyboard [Generic USB Keyboard] on usb-0000:00:1d.2-2/input0
[    5.995733] EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: (null)
[    6.027093] input: Generic USB Keyboard as /devices/pci0000:00/0000:00:1d.2/usb8/8-2/8-2:1.1/input/input4
[    6.027192] generic-usb 0003:040B:2000.0003: input,hidraw2: USB HID v1.10 Mouse [Generic USB Keyboard] on usb-0000:00:1d.2-2/input1
[    6.041366] ata5: SATA link down (SStatus 0 SControl 300)
[    6.041403] ata6: SATA link down (SStatus 0 SControl 300)
[    6.332191] firewire_core: created device fw0: GUID 001fc600000ccc2c, S400
[   14.716657] udev[440]: starting version 163
[   14.724003] lp: driver loaded but no devices found
[   14.730100] coretemp coretemp.0: TjMax is 100 C.
[   14.730140] coretemp coretemp.1: TjMax is 100 C.
[   14.730175] coretemp coretemp.2: TjMax is 100 C.
[   14.730557] coretemp coretemp.3: TjMax is 100 C.
[   14.739100]   alloc irq_desc for 29 on node -1
[   14.739103]   alloc kstat_irqs on node -1
[   14.739111] xhci_hcd 0000:02:00.0: PCI INT A -> GSI 29 (level, low) -> IRQ 29
[   14.739143] xhci_hcd 0000:02:00.0: setting latency timer to 64
[   14.739146] xhci_hcd 0000:02:00.0: xHCI Host Controller
[   14.739204] xhci_hcd 0000:02:00.0: new USB bus registered, assigned bus number 9
[   14.739330] xhci_hcd 0000:02:00.0: irq 29, io mem 0xf7ffe000
[   14.740204] EDAC MC: Ver: 2.1.0 Mar  1 2011
[   14.742682] usb usb9: No SuperSpeed endpoint companion for config 1  interface 0 altsetting 0 ep 129: using minimum values
[   14.742785] xHCI xhci_add_endpoint called for root hub
[   14.742805] xHCI xhci_check_bandwidth called for root hub
[   14.776663] w83627ehf: Found W83667HG chip at 0x290
[   14.776690] ACPI: resource w83627ehf [io  0x0295-0x0296] conflicts with ACPI region HWRE [io  0x0290-0x0299 64bit pref window disabled]
[   14.776693] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[   14.778742] PCI: Discovered peer bus ff
[   14.780216] EDAC MC0: Giving out device to 'i7core_edac.c' 'i7 core #0': DEV 0000:ff:03.0
[   14.780252] EDAC PCI0: Giving out device to module 'i7core_edac' controller 'EDAC PCI controller': DEV '0000:ff:03.0' (POLLED)
[   14.780253] EDAC i7core: Driver loaded.
[   14.780710] hub 9-0:1.0: USB hub found
[   14.781420] hub 9-0:1.0: 4 ports detected
[   14.782282] [drm] Initialized drm 1.1.0 20060810
[   14.786436] udev[480]: renamed network interface eth0 to eth2
[   14.807431] Adding 19803132k swap on /dev/sda5.  Priority:-1 extents:1 across:19803132k 
[   14.816274] w83627ehf: Found W83667HG chip at 0x290
[   14.816299] ACPI: resource w83627ehf [io  0x0295-0x0296] conflicts with ACPI region HWRE [io  0x0290-0x0299 64bit pref window disabled]
[   14.816301] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[   14.829368]   alloc irq_desc for 24 on node -1
[   14.829371]   alloc kstat_irqs on node -1
[   14.829378] nouveau 0000:03:00.0: PCI INT A -> GSI 24 (level, low) -> IRQ 24
[   14.829382] nouveau 0000:03:00.0: setting latency timer to 64
[   14.831568] [drm] nouveau 0000:03:00.0: Unsupported chipset 0x0c4180a1
[   14.831667] nouveau 0000:03:00.0: PCI INT A disabled
[   14.831672] nouveau: probe of 0000:03:00.0 failed with error -22
[   14.845606] nvidia: module license 'NVIDIA' taints kernel.
[   14.845609] Disabling lock debugging due to kernel taint
[   14.926804] type=1400 audit(1301491879.720:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient3" pid=757 comm="apparmor_parser"
[   14.926859] type=1400 audit(1301491879.720:3): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient3" pid=715 comm="apparmor_parser"
[   14.927143] type=1400 audit(1301491879.720:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=757 comm="apparmor_parser"
[   14.927255] type=1400 audit(1301491879.720:5): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=715 comm="apparmor_parser"
[   14.927324] type=1400 audit(1301491879.720:6): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=757 comm="apparmor_parser"
[   14.927479] type=1400 audit(1301491879.720:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=715 comm="apparmor_parser"
[   14.941288]   alloc irq_desc for 22 on node -1
[   14.941290]   alloc kstat_irqs on node -1
[   14.941295] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[   14.943835]   alloc irq_desc for 70 on node -1
[   14.943836]   alloc kstat_irqs on node -1
[   14.943846] HDA Intel 0000:00:1b.0: irq 70 for MSI/MSI-X
[   14.943866] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   15.051214] hda_codec: ALC892: BIOS auto-probing.
[   15.056316] Too many connections
[   15.057604]   alloc irq_desc for 34 on node -1
[   15.057605]   alloc kstat_irqs on node -1
[   15.057612] HDA Intel 0000:03:00.1: PCI INT B -> GSI 34 (level, low) -> IRQ 34
[   15.057614] hda_intel: Disable MSI for Nvidia chipset
[   15.057827] HDA Intel 0000:03:00.1: setting latency timer to 64
[   15.377587] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
[   15.529886] r8169 0000:07:01.0: eth2: link down
[   15.530795] ADDRCONF(NETDEV_UP): eth2: link is not ready
[   15.532379] type=1400 audit(1301491880.330:8): apparmor="STATUS" operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" pid=983 comm="apparmor_parser"
[   15.532538] type=1400 audit(1301491880.330:9): apparmor="STATUS" operation="profile_load" name="/usr/sbin/tcpdump" pid=988 comm="apparmor_parser"
[   15.532672] type=1400 audit(1301491880.330:10): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient3" pid=984 comm="apparmor_parser"
[   15.533004] type=1400 audit(1301491880.330:11): apparmor="STATUS" operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" pid=987 comm="apparmor_parser"
 
```

---

### Post by PCNetSpec on 2011-03-30
Maybe this will help ?

[http://ubuntuforums.org/showthread.php?t=1635278](http://ubuntuforums.org/showthread.php?t=1635278)

---

### Post by Kirboosy on 2011-03-30
I really wouldn't worry about it. With my Asus board I get the same error. It doesn't affect my performance in any way. I've read its related to the sound card but my sound works properly.

What about you? Does everything work properly?

---

### Post by conradin on 2011-04-01
yeah It seems like everything works, although I haven't benchmarked the sata controller. I have recently found a solution via bugzilla which suggests its the marvel sata controller giving out that result, and that it will require recompiling my kernel. Ill port the link when I'm at my other computer. I'll mark it as solved just as soon as i recompile the kernel.

---

