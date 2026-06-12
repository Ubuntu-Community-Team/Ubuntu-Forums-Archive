---
title: "Does anyone recognize these boot messages at all?"
date: 2010-10-28
forum: General Help
---

### Post by TheBuzzSaw on 2010-10-28
About half the time, my system fails to boot, and displays this nonsense (see attachment).

Help?

---

### Post by linuxpyro on 2010-10-28
Is this a fresh install?  Did you add any hardware?  Looks like it might be a kernel panic.  If you can get it to log in, try doing a dmesg into a text file or stick it into pastebin.

---

### Post by TheBuzzSaw on 2010-10-28
Fresh install *after* installing new hardware.

It does this ~50% of the time. I can get into the system the other 50% of the time. (I'm posting from it right now.)

[http://pastebin.com/JB28Nrjm](http://pastebin.com/JB28Nrjm)

Or see below:

```

[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.35-22-generic (buildd@yellow) (gcc version 4.4.5 (Ubuntu/Linaro 4.4.4-14ubuntu5) ) #35-Ubuntu SMP Sat Oct 16 20:45:36 UTC 2010 (Ubuntu 2.6.35-22.35-generic 2.6.35.4)
[    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-2.6.35-22-generic root=UUID=b0da82d7-7c15-485a-8ffe-60104f9c12a2 ro quiet splash
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009e800 (usable)
[    0.000000]  BIOS-e820: 000000000009e800 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e4000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 00000000bf770000 (usable)
[    0.000000]  BIOS-e820: 00000000bf770000 - 00000000bf788000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000bf788000 - 00000000bf7dc000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000bf7dc000 - 00000000c0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000ffe00000 - 0000000100000000 (reserved)
[    0.000000]  BIOS-e820: 0000000100000000 - 0000000140000000 (usable)
[    0.000000] NX (Execute Disable) protection: active
[    0.000000] DMI 2.6 present.
[    0.000000] AMI BIOS detected: BIOS may corrupt low RAM, working around it.
[    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
[    0.000000] e820 update range: 0000000000000000 - 0000000000001000 (usable) ==> (reserved)
[    0.000000] e820 remove range: 00000000000a0000 - 0000000000100000 (usable)
[    0.000000] No AGP bridge found
[    0.000000] last_pfn = 0x140000 max_arch_pfn = 0x400000000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-CFFFF write-protect
[    0.000000]   D0000-DFFFF uncachable
[    0.000000]   E0000-E7FFF write-through
[    0.000000]   E8000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000 mask F00000000 write-back
[    0.000000]   1 base 100000000 mask FC0000000 write-back
[    0.000000]   2 base 0C0000000 mask FC0000000 uncachable
[    0.000000]   3 base 0FFFE0000 mask FFFFF0000 write-protect
[    0.000000]   4 disabled
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] last_pfn = 0xbf770 max_arch_pfn = 0x400000000
[    0.000000] Scanning 0 areas for low memory corruption
[    0.000000] modified physical RAM map:
[    0.000000]  modified: 0000000000000000 - 0000000000010000 (reserved)
[    0.000000]  modified: 0000000000010000 - 000000000009e800 (usable)
[    0.000000]  modified: 000000000009e800 - 00000000000a0000 (reserved)
[    0.000000]  modified: 00000000000e4000 - 0000000000100000 (reserved)
[    0.000000]  modified: 0000000000100000 - 00000000bf770000 (usable)
[    0.000000]  modified: 00000000bf770000 - 00000000bf788000 (ACPI data)
[    0.000000]  modified: 00000000bf788000 - 00000000bf7dc000 (ACPI NVS)
[    0.000000]  modified: 00000000bf7dc000 - 00000000c0000000 (reserved)
[    0.000000]  modified: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  modified: 00000000ffe00000 - 0000000100000000 (reserved)
[    0.000000]  modified: 0000000100000000 - 0000000140000000 (usable)
[    0.000000] initial memory mapped : 0 - 20000000
[    0.000000] found SMP MP-table at [ffff8800000ff780] ff780
[    0.000000] init_memory_mapping: 0000000000000000-00000000bf770000
[    0.000000]  0000000000 - 00bf600000 page 2M
[    0.000000]  00bf600000 - 00bf770000 page 4k
[    0.000000] kernel direct mapping tables up to bf770000 @ 16000-1b000
[    0.000000] init_memory_mapping: 0000000100000000-0000000140000000
[    0.000000]  0100000000 - 0140000000 page 2M
[    0.000000] kernel direct mapping tables up to 140000000 @ 19000-1f000
[    0.000000] RAMDISK: 37571000 - 37ff0000
[    0.000000] ACPI: RSDP 00000000000fba20 00024 (v02 ACPIAM)
[    0.000000] ACPI: XSDT 00000000bf770100 00054 (v01 100909 XSDT1347 20091009 MSFT 00000097)
[    0.000000] ACPI: FACP 00000000bf770290 000F4 (v03 100909 FACP1347 20091009 MSFT 00000097)
[    0.000000] ACPI: DSDT 00000000bf7704a0 0911F (v01  A1474 A1474001 00000001 INTL 20060113)
[    0.000000] ACPI: FACS 00000000bf788000 00040
[    0.000000] ACPI: APIC 00000000bf770390 000CC (v01 100909 APIC1347 20091009 MSFT 00000097)
[    0.000000] ACPI: MCFG 00000000bf770460 0003C (v01 100909 OEMMCFG  20091009 MSFT 00000097)
[    0.000000] ACPI: OEMB 00000000bf788040 00072 (v01 100909 OEMB1347 20091009 MSFT 00000097)
[    0.000000] ACPI: HPET 00000000bf77f4a0 00038 (v01 100909 OEMHPET  20091009 MSFT 00000097)
[    0.000000] ACPI: SSDT 00000000bf7896d0 00363 (v01 DpgPmm    CpuPm 00000012 INTL 20060113)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] No NUMA configuration found
[    0.000000] Faking a node at 0000000000000000-0000000140000000
[    0.000000] Initmem setup node 0 0000000000000000-0000000140000000
[    0.000000]   NODE_DATA [0000000100000000 - 0000000100004fff]
[    0.000000]  [ffffea0000000000-ffffea00045fffff] PMD -> [ffff880100200000-ffff8801039fffff] on node 0
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000010 -> 0x00001000
[    0.000000]   DMA32    0x00001000 -> 0x00100000
[    0.000000]   Normal   0x00100000 -> 0x00140000
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[3] active PFN ranges
[    0.000000]     0: 0x00000010 -> 0x0000009e
[    0.000000]     0: 0x00000100 -> 0x000bf770
[    0.000000]     0: 0x00100000 -> 0x00140000
[    0.000000] On node 0 totalpages: 1046270
[    0.000000]   DMA zone: 56 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3926 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 14280 pages used for memmap
[    0.000000]   DMA32 zone: 765864 pages, LIFO batch:31
[    0.000000]   Normal zone: 3584 pages used for memmap
[    0.000000]   Normal zone: 258560 pages, LIFO batch:31
[    0.000000] ACPI: PM-Timer IO Port: 0x808
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x02] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x04] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x06] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x05] lapic_id[0x84] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x06] lapic_id[0x85] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x07] lapic_id[0x86] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x08] lapic_id[0x87] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x09] lapic_id[0x88] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x0a] lapic_id[0x89] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x0b] lapic_id[0x8a] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x0c] lapic_id[0x8b] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x0d] lapic_id[0x8c] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x0e] lapic_id[0x8d] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x0f] lapic_id[0x8e] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x10] lapic_id[0x8f] disabled)
[    0.000000] ACPI: IOAPIC (id[0x07] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 7, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x8086a701 base: 0xfed00000
[    0.000000] SMP: Allowing 16 CPUs, 12 hotplug CPUs
[    0.000000] nr_irqs_gsi: 40
[    0.000000] early_res array is doubled to 64 at [1a000 - 1a7ff]
[    0.000000] PM: Registered nosave memory: 000000000009e000 - 000000000009f000
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e4000
[    0.000000] PM: Registered nosave memory: 00000000000e4000 - 0000000000100000
[    0.000000] PM: Registered nosave memory: 00000000bf770000 - 00000000bf788000
[    0.000000] PM: Registered nosave memory: 00000000bf788000 - 00000000bf7dc000
[    0.000000] PM: Registered nosave memory: 00000000bf7dc000 - 00000000c0000000
[    0.000000] PM: Registered nosave memory: 00000000c0000000 - 00000000fee00000
[    0.000000] PM: Registered nosave memory: 00000000fee00000 - 00000000fee01000
[    0.000000] PM: Registered nosave memory: 00000000fee01000 - 00000000ffe00000
[    0.000000] PM: Registered nosave memory: 00000000ffe00000 - 0000000100000000
[    0.000000] Allocating PCI resources starting at c0000000 (gap: c0000000:3ee00000)
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] setup_percpu: NR_CPUS:64 nr_cpumask_bits:64 nr_cpu_ids:16 nr_node_ids:1
[    0.000000] early_res array is doubled to 128 at [1a800 - 1b7ff]
[    0.000000] PERCPU: Embedded 30 pages/cpu @ffff880001e00000 s91520 r8192 d23168 u131072
[    0.000000] pcpu-alloc: s91520 r8192 d23168 u131072 alloc=1*2097152
[    0.000000] pcpu-alloc: [0] 00 01 02 03 04 05 06 07 08 09 10 11 12 13 14 15 
[    0.000000] Built 1 zonelists in Node order, mobility grouping on.  Total pages: 1028350
[    0.000000] Policy zone: Normal
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.35-22-generic root=UUID=b0da82d7-7c15-485a-8ffe-60104f9c12a2 ro quiet splash
[    0.000000] PID hash table entries: 4096 (order: 3, 32768 bytes)
[    0.000000] Checking aperture...
[    0.000000] No AGP bridge found
[    0.000000] Calgary: detecting Calgary via BIOS EBDA area
[    0.000000] Calgary: Unable to locate Rio Grande table in EBDA - bailing!
[    0.000000] Subtract (68 early reservations)
[    0.000000]   #1 [0001000000 - 0001d17114]   TEXT DATA BSS
[    0.000000]   #2 [0037571000 - 0037ff0000]         RAMDISK
[    0.000000]   #3 [0001d18000 - 0001d182be]             BRK
[    0.000000]   #4 [00000ff790 - 0000100000]   BIOS reserved
[    0.000000]   #5 [00000ff780 - 00000ff790]    MP-table mpf
[    0.000000]   #6 [000009e800 - 00000f1310]   BIOS reserved
[    0.000000]   #7 [00000f14a4 - 00000ff780]   BIOS reserved
[    0.000000]   #8 [00000f1310 - 00000f14a4]    MP-table mpc
[    0.000000]   #9 [0000010000 - 0000012000]      TRAMPOLINE
[    0.000000]   #10 [0000012000 - 0000016000]     ACPI WAKEUP
[    0.000000]   #11 [0000016000 - 0000019000]         PGTABLE
[    0.000000]   #12 [0000019000 - 000001a000]         PGTABLE
[    0.000000]   #13 [0100000000 - 0100005000]       NODE_DATA
[    0.000000]   #14 [0001d182c0 - 0001d192c0]         BOOTMEM
[    0.000000]   #15 [0001d17140 - 0001d17440]         BOOTMEM
[    0.000000]   #16 [0100005000 - 0100006000]         BOOTMEM
[    0.000000]   #17 [0100006000 - 0100007000]         BOOTMEM
[    0.000000]   #18 [0100200000 - 0103a00000]        MEMMAP 0
[    0.000000]   #19 [0001d17440 - 0001d175c0]         BOOTMEM
[    0.000000]   #20 [0001d192c0 - 0001d312c0]         BOOTMEM
[    0.000000]   #21 [0001d312c0 - 0001d372c0]         BOOTMEM
[    0.000000]   #22 [0001d38000 - 0001d39000]         BOOTMEM
[    0.000000]   #23 [0001d175c0 - 0001d17601]         BOOTMEM
[    0.000000]   #24 [0001d17640 - 0001d17683]         BOOTMEM
[    0.000000]   #25 [0001d176c0 - 0001d17928]         BOOTMEM
[    0.000000]   #26 [0001d17940 - 0001d179a8]         BOOTMEM
[    0.000000]   #27 [0001d179c0 - 0001d17a28]         BOOTMEM
[    0.000000]   #28 [0001d17a40 - 0001d17aa8]         BOOTMEM
[    0.000000]   #29 [0001d17ac0 - 0001d17b28]         BOOTMEM
[    0.000000]   #30 [0001d17b40 - 0001d17ba8]         BOOTMEM
[    0.000000]   #31 [0001d17bc0 - 0001d17c28]         BOOTMEM
[    0.000000]   #32 [0001d17c40 - 0001d17ca8]         BOOTMEM
[    0.000000]   #33 [0001d17cc0 - 0001d17d28]         BOOTMEM
[    0.000000]   #34 [0001d17d40 - 0001d17da8]         BOOTMEM
[    0.000000]   #35 [0001d17dc0 - 0001d17e28]         BOOTMEM
[    0.000000]   #36 [0001d17e40 - 0001d17e60]         BOOTMEM
[    0.000000]   #37 [0001d17e80 - 0001d17ea0]         BOOTMEM
[    0.000000]   #38 [0001d17ec0 - 0001d17f2a]         BOOTMEM
[    0.000000]   #39 [0001d17f40 - 0001d17faa]         BOOTMEM
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
[    0.000000]   #56 [0001d17fc0 - 0001d17fc8]         BOOTMEM
[    0.000000]   #57 [0001d372c0 - 0001d372c8]         BOOTMEM
[    0.000000]   #58 [0001d37300 - 0001d37340]         BOOTMEM
[    0.000000]   #59 [0001d37340 - 0001d373c0]         BOOTMEM
[    0.000000]   #60 [0001d373c0 - 0001d374d0]         BOOTMEM
[    0.000000]   #61 [0001d37500 - 0001d37548]         BOOTMEM
[    0.000000]   #62 [0001d37580 - 0001d375c8]         BOOTMEM
[    0.000000]   #63 [0001d39000 - 0001d41000]         BOOTMEM
[    0.000000]   #64 [0001ffe000 - 0005ffe000]         BOOTMEM
[    0.000000]   #65 [0001d41000 - 0001d61000]         BOOTMEM
[    0.000000]   #66 [0001d61000 - 0001da1000]         BOOTMEM
[    0.000000]   #67 [000001b800 - 0000023800]         BOOTMEM
[    0.000000] Memory: 4035472k/5242880k available (5708k kernel code, 1057800k absent, 149608k reserved, 5382k data, 908k init)
[    0.000000] SLUB: Genslabs=14, HWalign=64, Order=0-3, MinObjects=0, CPUs=16, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000] 	RCU dyntick-idle grace-period acceleration is enabled.
[    0.000000] 	RCU-based detection of stalled CPUs is disabled.
[    0.000000] 	Verbose stalled-CPUs detection is disabled.
[    0.000000] NR_IRQS:4352 nr_irqs:808
[    0.000000] Extended CMOS year: 2000
[    0.000000] Console: colour VGA+ 80x25
[    0.000000] console [tty0] enabled
[    0.000000] allocated 41943040 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] hpet clockevent registered
[    0.000000] Fast TSC calibration using PIT
[    0.010000] Detected 2799.864 MHz processor.
[    0.000006] Calibrating delay loop (skipped), value calculated using timer frequency.. 5599.72 BogoMIPS (lpj=27998640)
[    0.000009] pid_max: default: 32768 minimum: 301
[    0.000026] Security Framework initialized
[    0.000037] AppArmor: AppArmor initialized
[    0.000038] Yama: becoming mindful.
[    0.000364] Dentry cache hash table entries: 524288 (order: 10, 4194304 bytes)
[    0.001134] Inode-cache hash table entries: 262144 (order: 9, 2097152 bytes)
[    0.001443] Mount-cache hash table entries: 256
[    0.001528] Initializing cgroup subsys ns
[    0.001531] Initializing cgroup subsys cpuacct
[    0.001534] Initializing cgroup subsys memory
[    0.001540] Initializing cgroup subsys devices
[    0.001542] Initializing cgroup subsys freezer
[    0.001543] Initializing cgroup subsys net_cls
[    0.001560] CPU: Physical Processor ID: 0
[    0.001561] CPU: Processor Core ID: 0
[    0.001565] mce: CPU supports 9 MCE banks
[    0.001574] CPU0: Thermal monitoring enabled (TM1)
[    0.001579] using mwait in idle threads.
[    0.001580] Performance Events: PEBS fmt1+, Nehalem events, Intel PMU driver.
[    0.001585] ... version:                3
[    0.001586] ... bit width:              48
[    0.001587] ... generic registers:      4
[    0.001588] ... value mask:             0000ffffffffffff
[    0.001589] ... max period:             000000007fffffff
[    0.001591] ... fixed-purpose events:   3
[    0.001592] ... event mask:             000000070000000f
[    0.003237] ACPI: Core revision 20100428
[    0.032383] ftrace: converting mcount calls to 0f 1f 44 00 00
[    0.032386] ftrace: allocating 22680 entries in 89 pages
[    0.038308] Setting APIC routing to physical flat
[    0.038638] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.138448] CPU0: Intel(R) Core(TM) i5 CPU         760  @ 2.80GHz stepping 05
[    0.258180] Booting Node   0, Processors  #1 #2 #3
[    0.797090] Brought up 4 CPUs
[    0.797092] Total of 4 processors activated (22399.37 BogoMIPS).
[    0.798484] devtmpfs: initialized
[    0.799244] regulator: core version 0.5
[    0.799268] Time: 12:15:04  Date: 10/28/10
[    0.799293] NET: Registered protocol family 16
[    0.799353] Trying to unpack rootfs image as initramfs...
[    0.799365] ACPI: bus type pci registered
[    0.799416] PCI: MMCONFIG for domain 0000 [bus 00-ff] at [mem 0xe0000000-0xefffffff] (base 0xe0000000)
[    0.799418] PCI: not using MMCONFIG
[    0.799419] PCI: Using configuration type 1 for base access
[    0.799929] bio: create slab <bio-0> at 0
[    0.801038] ACPI: EC: Look up EC in DSDT
[    0.802203] ACPI: Executed 1 blocks of module-level executable AML code
[    0.809197] ACPI: SSDT 00000000bf7880c0 01130 (v01 DpgPmm  P001Ist 00000011 INTL 20060113)
[    0.809524] ACPI: Dynamic OEM Table Load:
[    0.809527] ACPI: SSDT (null) 01130 (v01 DpgPmm  P001Ist 00000011 INTL 20060113)
[    0.809686] ACPI: SSDT 00000000bf7891f0 004D5 (v01  PmRef  P001Cst 00003001 INTL 20060113)
[    0.809973] ACPI: Dynamic OEM Table Load:
[    0.809975] ACPI: SSDT (null) 004D5 (v01  PmRef  P001Cst 00003001 INTL 20060113)
[    0.810139] ACPI: Interpreter enabled
[    0.810141] ACPI: (supports S0 S1 S3 S4 S5)
[    0.810157] ACPI: Using IOAPIC for interrupt routing
[    0.810197] PCI: MMCONFIG for domain 0000 [bus 00-ff] at [mem 0xe0000000-0xefffffff] (base 0xe0000000)
[    0.811878] PCI: MMCONFIG at [mem 0xe0000000-0xefffffff] reserved in ACPI motherboard resources
[    0.846111] ACPI: No dock devices found.
[    0.846115] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
[    0.846375] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-ff])
[    0.846610] pci_root PNP0A08:00: host bridge window [io  0x0000-0x0cf7]
[    0.846612] pci_root PNP0A08:00: host bridge window [io  0x0d00-0xffff]
[    0.846614] pci_root PNP0A08:00: host bridge window [mem 0x000a0000-0x000bffff]
[    0.846615] pci_root PNP0A08:00: host bridge window [mem 0x000d0000-0x000dffff]
[    0.846617] pci_root PNP0A08:00: host bridge window [mem 0xc0000000-0xdfffffff]
[    0.846619] pci_root PNP0A08:00: host bridge window [mem 0xf0000000-0xfed8ffff]
[    0.846696] pci 0000:00:03.0: PME# supported from D0 D3hot D3cold
[    0.846699] pci 0000:00:03.0: PME# disabled
[    0.846930] pci 0000:00:1a.0: reg 10: [mem 0xf7ffe000-0xf7ffe3ff]
[    0.846978] pci 0000:00:1a.0: PME# supported from D0 D3hot D3cold
[    0.846981] pci 0000:00:1a.0: PME# disabled
[    0.847010] pci 0000:00:1b.0: reg 10: [mem 0xf7ff8000-0xf7ffbfff 64bit]
[    0.847046] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    0.847049] pci 0000:00:1b.0: PME# disabled
[    0.847105] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    0.847108] pci 0000:00:1c.0: PME# disabled
[    0.847167] pci 0000:00:1c.4: PME# supported from D0 D3hot D3cold
[    0.847170] pci 0000:00:1c.4: PME# disabled
[    0.847226] pci 0000:00:1c.5: PME# supported from D0 D3hot D3cold
[    0.847229] pci 0000:00:1c.5: PME# disabled
[    0.847287] pci 0000:00:1c.6: PME# supported from D0 D3hot D3cold
[    0.847290] pci 0000:00:1c.6: PME# disabled
[    0.847345] pci 0000:00:1c.7: PME# supported from D0 D3hot D3cold
[    0.847348] pci 0000:00:1c.7: PME# disabled
[    0.847385] pci 0000:00:1d.0: reg 10: [mem 0xf7ffd000-0xf7ffd3ff]
[    0.847432] pci 0000:00:1d.0: PME# supported from D0 D3hot D3cold
[    0.847436] pci 0000:00:1d.0: PME# disabled
[    0.847583] pci 0000:00:1f.2: reg 10: [io  0xb880-0xb887]
[    0.847587] pci 0000:00:1f.2: reg 14: [io  0xb800-0xb803]
[    0.847592] pci 0000:00:1f.2: reg 18: [io  0xb480-0xb487]
[    0.847596] pci 0000:00:1f.2: reg 1c: [io  0xb400-0xb403]
[    0.847601] pci 0000:00:1f.2: reg 20: [io  0xb080-0xb09f]
[    0.847605] pci 0000:00:1f.2: reg 24: [mem 0xf7ff7000-0xf7ff77ff]
[    0.847632] pci 0000:00:1f.2: PME# supported from D3hot
[    0.847635] pci 0000:00:1f.2: PME# disabled
[    0.847658] pci 0000:00:1f.3: reg 10: [mem 0xf7ffc000-0xf7ffc0ff 64bit]
[    0.847669] pci 0000:00:1f.3: reg 20: [io  0x0400-0x041f]
[    0.847725] pci 0000:01:00.0: reg 10: [mem 0xfa000000-0xfaffffff]
[    0.847732] pci 0000:01:00.0: reg 14: [mem 0xd0000000-0xdfffffff 64bit pref]
[    0.847740] pci 0000:01:00.0: reg 1c: [mem 0xf8000000-0xf9ffffff 64bit]
[    0.847744] pci 0000:01:00.0: reg 24: [io  0xcc00-0xcc7f]
[    0.847748] pci 0000:01:00.0: reg 30: [mem 0xfbc80000-0xfbcfffff pref]
[    0.866897] pci 0000:00:03.0: PCI bridge to [bus 01-01]
[    0.866899] pci 0000:00:03.0:   bridge window [io  0xc000-0xcfff]
[    0.866902] pci 0000:00:03.0:   bridge window [mem 0xf8000000-0xfbcfffff]
[    0.866906] pci 0000:00:03.0:   bridge window [mem 0xd0000000-0xdfffffff 64bit pref]
[    0.866941] pci 0000:00:1c.0: PCI bridge to [bus 06-06]
[    0.866944] pci 0000:00:1c.0:   bridge window [io  0xf000-0x0000] (disabled)
[    0.866948] pci 0000:00:1c.0:   bridge window [mem 0xfff00000-0x000fffff] (disabled)
[    0.866953] pci 0000:00:1c.0:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    0.866988] pci 0000:00:1c.4: PCI bridge to [bus 05-05]
[    0.866991] pci 0000:00:1c.4:   bridge window [io  0xf000-0x0000] (disabled)
[    0.866994] pci 0000:00:1c.4:   bridge window [mem 0xfff00000-0x000fffff] (disabled)
[    0.866999] pci 0000:00:1c.4:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    0.867033] pci 0000:00:1c.5: PCI bridge to [bus 04-04]
[    0.867036] pci 0000:00:1c.5:   bridge window [io  0xf000-0x0000] (disabled)
[    0.867039] pci 0000:00:1c.5:   bridge window [mem 0xfff00000-0x000fffff] (disabled)
[    0.867044] pci 0000:00:1c.5:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    0.867104] pci 0000:03:00.0: reg 10: [io  0xec00-0xec07]
[    0.867111] pci 0000:03:00.0: reg 14: [io  0xe880-0xe883]
[    0.867118] pci 0000:03:00.0: reg 18: [io  0xe800-0xe807]
[    0.867125] pci 0000:03:00.0: reg 1c: [io  0xe480-0xe483]
[    0.867132] pci 0000:03:00.0: reg 20: [io  0xe400-0xe40f]
[    0.867144] pci 0000:03:00.0: reg 30: [mem 0xfbef0000-0xfbefffff pref]
[    0.867177] pci 0000:03:00.0: supports D1 D2
[    0.867179] pci 0000:03:00.0: PME# supported from D1 D2 D3hot
[    0.867183] pci 0000:03:00.0: PME# disabled
[    0.886859] pci 0000:00:1c.6: PCI bridge to [bus 03-03]
[    0.886863] pci 0000:00:1c.6:   bridge window [io  0xe000-0xefff]
[    0.886866] pci 0000:00:1c.6:   bridge window [mem 0xfbe00000-0xfbefffff]
[    0.886871] pci 0000:00:1c.6:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    0.886933] pci 0000:02:00.0: reg 10: [io  0xd800-0xd8ff]
[    0.886951] pci 0000:02:00.0: reg 18: [mem 0xf6fff000-0xf6ffffff 64bit pref]
[    0.886964] pci 0000:02:00.0: reg 20: [mem 0xf6ff8000-0xf6ffbfff 64bit pref]
[    0.886971] pci 0000:02:00.0: reg 30: [mem 0xfbdf0000-0xfbdfffff pref]
[    0.887009] pci 0000:02:00.0: supports D1 D2
[    0.887010] pci 0000:02:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.887015] pci 0000:02:00.0: PME# disabled
[    0.906822] pci 0000:00:1c.7: PCI bridge to [bus 02-02]
[    0.906826] pci 0000:00:1c.7:   bridge window [io  0xd000-0xdfff]
[    0.906829] pci 0000:00:1c.7:   bridge window [mem 0xfbd00000-0xfbdfffff]
[    0.906834] pci 0000:00:1c.7:   bridge window [mem 0xf6f00000-0xf6ffffff 64bit pref]
[    0.906889] pci 0000:00:1e.0: PCI bridge to [bus 07-07] (subtractive decode)
[    0.906892] pci 0000:00:1e.0:   bridge window [io  0xf000-0x0000] (disabled)
[    0.906895] pci 0000:00:1e.0:   bridge window [mem 0xfff00000-0x000fffff] (disabled)
[    0.906900] pci 0000:00:1e.0:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    0.906902] pci 0000:00:1e.0:   bridge window [io  0x0000-0x0cf7] (subtractive decode)
[    0.906904] pci 0000:00:1e.0:   bridge window [io  0x0d00-0xffff] (subtractive decode)
[    0.906906] pci 0000:00:1e.0:   bridge window [mem 0x000a0000-0x000bffff] (subtractive decode)
[    0.906908] pci 0000:00:1e.0:   bridge window [mem 0x000d0000-0x000dffff] (subtractive decode)
[    0.906910] pci 0000:00:1e.0:   bridge window [mem 0xc0000000-0xdfffffff] (subtractive decode)
[    0.906911] pci 0000:00:1e.0:   bridge window [mem 0xf0000000-0xfed8ffff] (subtractive decode)
[    0.906944] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.907100] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.BR1E._PRT]
[    0.907207] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P3._PRT]
[    0.907260] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.BR20._PRT]
[    0.907307] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.BR24._PRT]
[    0.907352] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.BR25._PRT]
[    0.907397] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.BR26._PRT]
[    0.907448] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.BR27._PRT]
[    0.924748] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 6 7 *10 11 12 14 15)
[    0.924844] ACPI: PCI Interrupt Link [LNKB] (IRQs *5)
[    0.924935] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 6 7 10 11 12 14 *15)
[    0.925029] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 6 7 10 *11 12 14 15)
[    0.925122] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 6 7 10 11 12 14 15) *0, disabled.
[    0.925216] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 6 7 10 11 12 *14 15)
[    0.925309] ACPI: PCI Interrupt Link [LNKG] (IRQs *3 4 6 7 10 11 12 14 15)
[    0.925403] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 6 *7 10 11 12 14 15)
[    0.925443] HEST: Table is not found!
[    0.925494] vgaarb: device added: PCI:0000:01:00.0,decodes=io+mem,owns=io+mem,locks=none
[    0.925496] vgaarb: loaded
[    0.925584] SCSI subsystem initialized
[    0.925654] libata version 3.00 loaded.
[    0.925686] usbcore: registered new interface driver usbfs
[    0.925693] usbcore: registered new interface driver hub
[    0.925707] usbcore: registered new device driver usb
[    0.925784] ACPI: WMI: Mapper loaded
[    0.925785] PCI: Using ACPI for IRQ routing
[    0.925787] PCI: pci_cache_line_size set to 64 bytes
[    0.925848] reserve RAM buffer: 000000000009e800 - 000000000009ffff 
[    0.925850] reserve RAM buffer: 00000000bf770000 - 00000000bfffffff 
[    0.925912] NetLabel: Initializing
[    0.925913] NetLabel:  domain hash size = 128
[    0.925914] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.925923] NetLabel:  unlabeled traffic allowed by default
[    0.925944]   alloc irq_desc for 40 on node 0
[    0.925945]   alloc kstat_irqs on node 0
[    0.925952]   alloc irq_desc for 41 on node 0
[    0.925954]   alloc kstat_irqs on node 0
[    0.925956]   alloc irq_desc for 42 on node 0
[    0.925957]   alloc kstat_irqs on node 0
[    0.925960]   alloc irq_desc for 43 on node 0
[    0.925961]   alloc kstat_irqs on node 0
[    0.925964]   alloc irq_desc for 44 on node 0
[    0.925965]   alloc kstat_irqs on node 0
[    0.925967] HPET: 8 timers in total, 5 timers will be used for per-cpu timer
[    0.925973] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 40, 41, 42, 43, 44, 0
[    0.925978] hpet0: 8 comparators, 64-bit 14.318180 MHz counter
[    0.936762] hpet: hpet2 irq 40 for MSI
[    0.936870] hpet: hpet3 irq 41 for MSI
[    0.946853] hpet: hpet4 irq 42 for MSI
[    0.956794] hpet: hpet5 irq 43 for MSI
[    0.956814] Switching to clocksource tsc
[    0.962603] AppArmor: AppArmor Filesystem Enabled
[    0.962614] pnp: PnP ACPI init
[    0.962625] ACPI: bus type pnp registered
[    0.965115] pnp: PnP ACPI: found 15 devices
[    0.965116] ACPI: ACPI bus type pnp unregistered
[    0.965125] system 00:01: [mem 0xfc000000-0xfcffffff] has been reserved
[    0.965127] system 00:01: [mem 0xfd000000-0xfdffffff] has been reserved
[    0.965129] system 00:01: [mem 0xfe000000-0xfebfffff] has been reserved
[    0.965131] system 00:01: [mem 0xfed14000-0xfed19fff] has been reserved
[    0.965135] system 00:06: [io  0x0290-0x029f] has been reserved
[    0.965139] system 00:07: [io  0x04d0-0x04d1] has been reserved
[    0.965141] system 00:07: [io  0x0800-0x087f] has been reserved
[    0.965142] system 00:07: [io  0x0500-0x057f] has been reserved
[    0.965144] system 00:07: [mem 0xfed1c000-0xfed1ffff] has been reserved
[    0.965146] system 00:07: [mem 0xfed20000-0xfed3ffff] has been reserved
[    0.965148] system 00:07: [mem 0xfed40000-0xfed8ffff] has been reserved
[    0.965152] system 00:0a: [mem 0xffc00000-0xffdfffff] has been reserved
[    0.965155] system 00:0c: [mem 0xfec00000-0xfec00fff] could not be reserved
[    0.965157] system 00:0c: [mem 0xfee00000-0xfee00fff] has been reserved
[    0.965160] system 00:0d: [mem 0xe0000000-0xefffffff] has been reserved
[    0.965164] system 00:0e: [mem 0x00000000-0x0009ffff] could not be reserved
[    0.965166] system 00:0e: [mem 0x000c0000-0x000cffff] has been reserved
[    0.965168] system 00:0e: [mem 0x000e0000-0x000fffff] could not be reserved
[    0.965170] system 00:0e: [mem 0x00100000-0xbfffffff] could not be reserved
[    0.965172] system 00:0e: [mem 0xfed90000-0xffffffff] could not be reserved
[    0.970599] pci 0000:00:1c.0: BAR 14: assigned [mem 0xc0000000-0xc01fffff]
[    0.970602] pci 0000:00:1c.0: BAR 15: assigned [mem 0xc0200000-0xc03fffff 64bit pref]
[    0.970604] pci 0000:00:1c.4: BAR 14: assigned [mem 0xc0400000-0xc05fffff]
[    0.970606] pci 0000:00:1c.4: BAR 15: assigned [mem 0xc0600000-0xc07fffff 64bit pref]
[    0.970608] pci 0000:00:1c.5: BAR 14: assigned [mem 0xc0800000-0xc09fffff]
[    0.970610] pci 0000:00:1c.5: BAR 15: assigned [mem 0xc0a00000-0xc0bfffff 64bit pref]
[    0.970612] pci 0000:00:1c.0: BAR 13: assigned [io  0x1000-0x1fff]
[    0.970614] pci 0000:00:1c.4: BAR 13: assigned [io  0x2000-0x2fff]
[    0.970616] pci 0000:00:1c.5: BAR 13: assigned [io  0x3000-0x3fff]
[    0.970618] pci 0000:00:03.0: PCI bridge to [bus 01-01]
[    0.970620] pci 0000:00:03.0:   bridge window [io  0xc000-0xcfff]
[    0.970623] pci 0000:00:03.0:   bridge window [mem 0xf8000000-0xfbcfffff]
[    0.970626] pci 0000:00:03.0:   bridge window [mem 0xd0000000-0xdfffffff 64bit pref]
[    0.970630] pci 0000:00:1c.0: PCI bridge to [bus 06-06]
[    0.970632] pci 0000:00:1c.0:   bridge window [io  0x1000-0x1fff]
[    0.970636] pci 0000:00:1c.0:   bridge window [mem 0xc0000000-0xc01fffff]
[    0.970639] pci 0000:00:1c.0:   bridge window [mem 0xc0200000-0xc03fffff 64bit pref]
[    0.970644] pci 0000:00:1c.4: PCI bridge to [bus 05-05]
[    0.970646] pci 0000:00:1c.4:   bridge window [io  0x2000-0x2fff]
[    0.970650] pci 0000:00:1c.4:   bridge window [mem 0xc0400000-0xc05fffff]
[    0.970653] pci 0000:00:1c.4:   bridge window [mem 0xc0600000-0xc07fffff 64bit pref]
[    0.970658] pci 0000:00:1c.5: PCI bridge to [bus 04-04]
[    0.970660] pci 0000:00:1c.5:   bridge window [io  0x3000-0x3fff]
[    0.970664] pci 0000:00:1c.5:   bridge window [mem 0xc0800000-0xc09fffff]
[    0.970667] pci 0000:00:1c.5:   bridge window [mem 0xc0a00000-0xc0bfffff 64bit pref]
[    0.970672] pci 0000:00:1c.6: PCI bridge to [bus 03-03]
[    0.970674] pci 0000:00:1c.6:   bridge window [io  0xe000-0xefff]
[    0.970677] pci 0000:00:1c.6:   bridge window [mem 0xfbe00000-0xfbefffff]
[    0.970680] pci 0000:00:1c.6:   bridge window [mem pref disabled]
[    0.970685] pci 0000:00:1c.7: PCI bridge to [bus 02-02]
[    0.970687] pci 0000:00:1c.7:   bridge window [io  0xd000-0xdfff]
[    0.970691] pci 0000:00:1c.7:   bridge window [mem 0xfbd00000-0xfbdfffff]
[    0.970694] pci 0000:00:1c.7:   bridge window [mem 0xf6f00000-0xf6ffffff 64bit pref]
[    0.970699] pci 0000:00:1e.0: PCI bridge to [bus 07-07]
[    0.970700] pci 0000:00:1e.0:   bridge window [io  disabled]
[    0.970704] pci 0000:00:1e.0:   bridge window [mem disabled]
[    0.970707] pci 0000:00:1e.0:   bridge window [mem pref disabled]
[    0.970717]   alloc irq_desc for 16 on node -1
[    0.970718]   alloc kstat_irqs on node -1
[    0.970722] pci 0000:00:03.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.970725] pci 0000:00:03.0: setting latency timer to 64
[    0.970731] pci 0000:00:1c.0: enabling device (0104 -> 0107)
[    0.970733]   alloc irq_desc for 17 on node -1
[    0.970734]   alloc kstat_irqs on node -1
[    0.970737] pci 0000:00:1c.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    0.970740] pci 0000:00:1c.0: setting latency timer to 64
[    0.970746] pci 0000:00:1c.4: enabling device (0104 -> 0107)
[    0.970749] pci 0000:00:1c.4: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    0.970752] pci 0000:00:1c.4: setting latency timer to 64
[    0.970758] pci 0000:00:1c.5: enabling device (0104 -> 0107)
[    0.970760] pci 0000:00:1c.5: PCI INT B -> GSI 16 (level, low) -> IRQ 16
[    0.970763] pci 0000:00:1c.5: setting latency timer to 64
[    0.970769]   alloc irq_desc for 18 on node -1
[    0.970770]   alloc kstat_irqs on node -1
[    0.970773] pci 0000:00:1c.6: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.970776] pci 0000:00:1c.6: setting latency timer to 64
[    0.970782]   alloc irq_desc for 19 on node -1
[    0.970783]   alloc kstat_irqs on node -1
[    0.970785] pci 0000:00:1c.7: PCI INT D -> GSI 19 (level, low) -> IRQ 19
[    0.970788] pci 0000:00:1c.7: setting latency timer to 64
[    0.970793] pci 0000:00:1e.0: setting latency timer to 64
[    0.970796] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
[    0.970798] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff]
[    0.970799] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
[    0.970801] pci_bus 0000:00: resource 7 [mem 0x000d0000-0x000dffff]
[    0.970802] pci_bus 0000:00: resource 8 [mem 0xc0000000-0xdfffffff]
[    0.970804] pci_bus 0000:00: resource 9 [mem 0xf0000000-0xfed8ffff]
[    0.970805] pci_bus 0000:01: resource 0 [io  0xc000-0xcfff]
[    0.970807] pci_bus 0000:01: resource 1 [mem 0xf8000000-0xfbcfffff]
[    0.970808] pci_bus 0000:01: resource 2 [mem 0xd0000000-0xdfffffff 64bit pref]
[    0.970810] pci_bus 0000:06: resource 0 [io  0x1000-0x1fff]
[    0.970812] pci_bus 0000:06: resource 1 [mem 0xc0000000-0xc01fffff]
[    0.970813] pci_bus 0000:06: resource 2 [mem 0xc0200000-0xc03fffff 64bit pref]
[    0.970815] pci_bus 0000:05: resource 0 [io  0x2000-0x2fff]
[    0.970816] pci_bus 0000:05: resource 1 [mem 0xc0400000-0xc05fffff]
[    0.970818] pci_bus 0000:05: resource 2 [mem 0xc0600000-0xc07fffff 64bit pref]
[    0.970820] pci_bus 0000:04: resource 0 [io  0x3000-0x3fff]
[    0.970821] pci_bus 0000:04: resource 1 [mem 0xc0800000-0xc09fffff]
[    0.970823] pci_bus 0000:04: resource 2 [mem 0xc0a00000-0xc0bfffff 64bit pref]
[    0.970824] pci_bus 0000:03: resource 0 [io  0xe000-0xefff]
[    0.970826] pci_bus 0000:03: resource 1 [mem 0xfbe00000-0xfbefffff]
[    0.970827] pci_bus 0000:02: resource 0 [io  0xd000-0xdfff]
[    0.970829] pci_bus 0000:02: resource 1 [mem 0xfbd00000-0xfbdfffff]
[    0.970830] pci_bus 0000:02: resource 2 [mem 0xf6f00000-0xf6ffffff 64bit pref]
[    0.970832] pci_bus 0000:07: resource 4 [io  0x0000-0x0cf7]
[    0.970834] pci_bus 0000:07: resource 5 [io  0x0d00-0xffff]
[    0.970835] pci_bus 0000:07: resource 6 [mem 0x000a0000-0x000bffff]
[    0.970837] pci_bus 0000:07: resource 7 [mem 0x000d0000-0x000dffff]
[    0.970838] pci_bus 0000:07: resource 8 [mem 0xc0000000-0xdfffffff]
[    0.970840] pci_bus 0000:07: resource 9 [mem 0xf0000000-0xfed8ffff]
[    0.970860] NET: Registered protocol family 2
[    0.970974] IP route cache hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.971747] TCP established hash table entries: 524288 (order: 11, 8388608 bytes)
[    0.973952] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[    0.974218] TCP: Hash tables configured (established 524288 bind 65536)
[    0.974220] TCP reno registered
[    0.974228] UDP hash table entries: 2048 (order: 4, 65536 bytes)
[    0.974258] UDP-Lite hash table entries: 2048 (order: 4, 65536 bytes)
[    0.974364] NET: Registered protocol family 1
[    0.974449] pci 0000:01:00.0: Boot video device
[    0.974456] PCI: CLS 32 bytes, default 64
[    0.974458] PCI-DMA: Using software bounce buffering for IO (SWIOTLB)
[    0.974459] Placing 64MB software IO TLB between ffff880001ffe000 - ffff880005ffe000
[    0.974461] software IO TLB at phys 0x1ffe000 - 0x5ffe000
[    0.974663] Scanning for low memory corruption every 60 seconds
[    0.974748] audit: initializing netlink socket (disabled)
[    0.974755] type=2000 audit(1288268103.810:1): initialized
[    0.983680] Freeing initrd memory: 10748k freed
[    0.986037] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    0.987059] VFS: Disk quotas dquot_6.5.2
[    0.987105] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    0.987513] fuse init (API version 7.14)
[    0.987571] msgmni has been set to 7902
[    0.989038] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.989041] io scheduler noop registered
[    0.989042] io scheduler deadline registered
[    0.989070] io scheduler cfq registered (default)
[    0.989140] pcieport 0000:00:03.0: setting latency timer to 64
[    0.989163]   alloc irq_desc for 45 on node -1
[    0.989164]   alloc kstat_irqs on node -1
[    0.989171] pcieport 0000:00:03.0: irq 45 for MSI/MSI-X
[    0.989219] pcieport 0000:00:1c.0: setting latency timer to 64
[    0.989245]   alloc irq_desc for 46 on node -1
[    0.989246]   alloc kstat_irqs on node -1
[    0.989251] pcieport 0000:00:1c.0: irq 46 for MSI/MSI-X
[    0.989303] pcieport 0000:00:1c.4: setting latency timer to 64
[    0.989329]   alloc irq_desc for 47 on node -1
[    0.989330]   alloc kstat_irqs on node -1
[    0.989335] pcieport 0000:00:1c.4: irq 47 for MSI/MSI-X
[    0.989386] pcieport 0000:00:1c.5: setting latency timer to 64
[    0.989412]   alloc irq_desc for 48 on node -1
[    0.989413]   alloc kstat_irqs on node -1
[    0.989418] pcieport 0000:00:1c.5: irq 48 for MSI/MSI-X
[    0.989471] pcieport 0000:00:1c.6: setting latency timer to 64
[    0.989496]   alloc irq_desc for 49 on node -1
[    0.989497]   alloc kstat_irqs on node -1
[    0.989503] pcieport 0000:00:1c.6: irq 49 for MSI/MSI-X
[    0.989547] pcieport 0000:00:1c.7: setting latency timer to 64
[    0.989573]   alloc irq_desc for 50 on node -1
[    0.989574]   alloc kstat_irqs on node -1
[    0.989579] pcieport 0000:00:1c.7: irq 50 for MSI/MSI-X
[    0.989630] Firmware did not grant requested _OSC control
[    0.989631] aer 0000:00:03.0:pcie02: AER service couldn't init device: no _OSC support
[    0.989645] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.989653] Firmware did not grant requested _OSC control
[    0.989658] Firmware did not grant requested _OSC control
[    0.989662] Firmware did not grant requested _OSC control
[    0.989673] Firmware did not grant requested _OSC control
[    0.989677] Firmware did not grant requested _OSC control
[    0.989681] Firmware did not grant requested _OSC control
[    0.989686] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.989732] intel_idle: MWAIT substates: 0x1120
[    0.989734] intel_idle: v0.4 model 0x1E
[    0.989735] intel_idle: lapic_timer_reliable_states 0x2
[    0.989820] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0
[    0.989824] ACPI: Power Button [PWRB]
[    0.989852] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
[    0.989854] ACPI: Power Button [PWRF]
[    0.990110] ACPI: acpi_idle yielding to intel_idle
[    0.992440] ERST: Table is not found!
[    0.992577] Linux agpgart interface v0.103
[    0.992589] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    0.992680] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.992941] 00:0b: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.993646] brd: module loaded
[    0.993970] loop: module loaded
[    0.994097] pata_acpi 0000:03:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    0.994116] pata_acpi 0000:03:00.0: setting latency timer to 64
[    0.994126] pata_acpi 0000:03:00.0: PCI INT A disabled
[    0.994294] Fixed MDIO Bus: probed
[    0.994314] PPP generic driver version 2.4.2
[    0.994334] tun: Universal TUN/TAP device driver, 1.6
[    0.994336] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.994381] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.994395] ehci_hcd 0000:00:1a.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.994409] ehci_hcd 0000:00:1a.0: setting latency timer to 64
[    0.994411] ehci_hcd 0000:00:1a.0: EHCI Host Controller
[    0.994435] ehci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 1
[    0.994458] ehci_hcd 0000:00:1a.0: debug port 2
[    0.998326] ehci_hcd 0000:00:1a.0: cache line size of 32 is not supported
[    0.998338] ehci_hcd 0000:00:1a.0: irq 16, io mem 0xf7ffe000
[    1.016886] ehci_hcd 0000:00:1a.0: USB 2.0 started, EHCI 1.00
[    1.016984] hub 1-0:1.0: USB hub found
[    1.016987] hub 1-0:1.0: 2 ports detected
[    1.017027]   alloc irq_desc for 23 on node -1
[    1.017029]   alloc kstat_irqs on node -1
[    1.017033] ehci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    1.017042] ehci_hcd 0000:00:1d.0: setting latency timer to 64
[    1.017045] ehci_hcd 0000:00:1d.0: EHCI Host Controller
[    1.017068] ehci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    1.017087] ehci_hcd 0000:00:1d.0: debug port 2
[    1.020951] ehci_hcd 0000:00:1d.0: cache line size of 32 is not supported
[    1.020961] ehci_hcd 0000:00:1d.0: irq 23, io mem 0xf7ffd000
[    1.036829] ehci_hcd 0000:00:1d.0: USB 2.0 started, EHCI 1.00
[    1.036924] hub 2-0:1.0: USB hub found
[    1.036927] hub 2-0:1.0: 2 ports detected
[    1.036963] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    1.036971] uhci_hcd: USB Universal Host Controller Interface driver
[    1.037039] PNP: No PS/2 controller found. Probing ports directly.
[    1.039722] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.039726] serio: i8042 AUX port at 0x60,0x64 irq 12
[    1.039771] mice: PS/2 mouse device common for all mice
[    1.039835] rtc_cmos 00:03: RTC can wake from S4
[    1.039858] rtc_cmos 00:03: rtc core: registered rtc_cmos as rtc0
[    1.039881] rtc0: alarms up to one month, y3k, 114 bytes nvram, hpet irqs
[    1.039949] device-mapper: uevent: version 1.0.3
[    1.040006] device-mapper: ioctl: 4.17.0-ioctl (2010-03-05) initialised: dm-devel@redhat.com
[    1.040062] device-mapper: multipath: version 1.1.1 loaded
[    1.040064] device-mapper: multipath round-robin: version 1.0.0 loaded
[    1.040249] cpuidle: using governor ladder
[    1.040353] cpuidle: using governor menu
[    1.040543] TCP cubic registered
[    1.040630] NET: Registered protocol family 10
[    1.040899] lo: Disabled Privacy Extensions
[    1.041036] NET: Registered protocol family 17
[    1.042243] PM: Resume from disk failed.
[    1.042249] registered taskstats version 1
[    1.042503]   Magic number: 14:121:280
[    1.042514] tty tty17: hash matches
[    1.042556] rtc_cmos 00:03: setting system clock to 2010-10-28 12:15:04 UTC (1288268104)
[    1.042559] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.042560] EDD information not available.
[    1.042602] Freeing unused kernel memory: 908k freed
[    1.042725] Write protecting the kernel read-only data: 10240k
[    1.042858] Freeing unused kernel memory: 416k freed
[    1.043003] Freeing unused kernel memory: 1644k freed
[    1.052529] udev[98]: starting version 163
[    1.074563] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    1.074580] r8169 0000:02:00.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    1.074619] r8169 0000:02:00.0: setting latency timer to 64
[    1.074658]   alloc irq_desc for 51 on node -1
[    1.074660]   alloc kstat_irqs on node -1
[    1.074671] r8169 0000:02:00.0: irq 51 for MSI/MSI-X
[    1.075011] r8169 0000:02:00.0: eth0: RTL8168d/8111d at 0xffffc9000067c000, 90:e6:ba:ce:48:ba, XID 083000c0 IRQ 51
[    1.078244] ahci 0000:00:1f.2: version 3.0
[    1.078256]   alloc irq_desc for 21 on node -1
[    1.078257]   alloc kstat_irqs on node -1
[    1.078262] ahci 0000:00:1f.2: PCI INT D -> GSI 21 (level, low) -> IRQ 21
[    1.078292]   alloc irq_desc for 52 on node -1
[    1.078294]   alloc kstat_irqs on node -1
[    1.078300] ahci 0000:00:1f.2: irq 52 for MSI/MSI-X
[    1.078325] ahci: SSS flag set, parallel bus scan disabled
[    1.096733] ahci 0000:00:1f.2: AHCI 0001.0300 32 slots 6 ports 3 Gbps 0x3f impl SATA mode
[    1.096736] ahci 0000:00:1f.2: flags: 64bit ncq sntf stag pm led clo pmp pio slum part ems sxs apst 
[    1.096740] ahci 0000:00:1f.2: setting latency timer to 64
[    1.096885] pata_via 0000:03:00.0: version 0.3.4
[    1.096895] pata_via 0000:03:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    1.096927] pata_via 0000:03:00.0: setting latency timer to 64
[    1.096979] scsi0 : pata_via
[    1.097050] scsi1 : pata_via
[    1.097224] ata1: PATA max UDMA/133 cmd 0xec00 ctl 0xe880 bmdma 0xe400 irq 18
[    1.097226] ata2: PATA max UDMA/133 cmd 0xe800 ctl 0xe480 bmdma 0xe408 irq 18
[    1.196912] scsi2 : ahci
[    1.197015] scsi3 : ahci
[    1.197113] scsi4 : ahci
[    1.197246] scsi5 : ahci
[    1.197370] scsi6 : ahci
[    1.197433] scsi7 : ahci
[    1.197553] ata3: SATA max UDMA/133 abar m2048@0xf7ff7000 port 0xf7ff7100 irq 52
[    1.197555] ata4: SATA max UDMA/133 abar m2048@0xf7ff7000 port 0xf7ff7180 irq 52
[    1.197558] ata5: SATA max UDMA/133 abar m2048@0xf7ff7000 port 0xf7ff7200 irq 52
[    1.197560] ata6: SATA max UDMA/133 abar m2048@0xf7ff7000 port 0xf7ff7280 irq 52
[    1.197562] ata7: SATA max UDMA/133 abar m2048@0xf7ff7000 port 0xf7ff7300 irq 52
[    1.197564] ata8: SATA max UDMA/133 abar m2048@0xf7ff7000 port 0xf7ff7380 irq 52
[    1.336325] usb 1-1: new high speed USB device using ehci_hcd and address 2
[    1.486795] hub 1-1:1.0: USB hub found
[    1.486996] hub 1-1:1.0: 6 ports detected
[    1.605782] usb 2-1: new high speed USB device using ehci_hcd and address 2
[    1.726456] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    1.727090] ata3.00: ATAPI: TSSTcorp CDDVDW TS-H653Z, 4403, max UDMA/33
[    1.728012] ata3.00: configured for UDMA/33
[    1.756279] scsi 2:0:0:0: CD-ROM            TSSTcorp CDDVDW TS-H653Z  4403 PQ: 0 ANSI: 5
[    1.756377] hub 2-1:1.0: USB hub found
[    1.756608] hub 2-1:1.0: 8 ports detected
[    1.761219] sr0: scsi3-mmc drive: 40x/40x writer dvd-ram cd/rw xa/form2 cdda tray
[    1.761224] Uniform CD-ROM driver Revision: 3.20
[    1.761364] sr 2:0:0:0: Attached scsi CD-ROM sr0
[    1.761401] sr 2:0:0:0: Attached scsi generic sg0 type 5
[    2.035073] usb 2-1.1: new full speed USB device using ehci_hcd and address 3
[    2.224690] usb 2-1.7: new high speed USB device using ehci_hcd and address 4
[    2.534105] usb 2-1.8: new low speed USB device using ehci_hcd and address 5
[    2.683594] ata4: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    2.696117] usbcore: registered new interface driver hiddev
[    2.697872] input: Razer Razer DeathAdder   as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.1/2-1.1:1.0/input/input2
[    2.697924] generic-usb 0003:1532:0016.0001: input,hidraw0: USB HID v1.11 Mouse [Razer Razer DeathAdder  ] on usb-0000:00:1d.0-1.1/input0
[    2.707804] ata4.00: ATA-8: WDC WD1001FALS-00E8B0, 05.00K05, max UDMA/133
[    2.707810] ata4.00: 1953525168 sectors, multi 0: LBA48 NCQ (depth 31/32), AA
[    2.708884] ata4.00: configured for UDMA/133
[    2.709031] input: Chicony Saitek Eclipse Keyboard as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.8/2-1.8:1.0/input/input3
[    2.709080] generic-usb 0003:06A3:8020.0002: input,hidraw1: USB HID v1.11 Keyboard [Chicony Saitek Eclipse Keyboard] on usb-0000:00:1d.0-1.8/input0
[    2.723802] scsi 3:0:0:0: Direct-Access     ATA      WDC WD1001FALS-0 05.0 PQ: 0 ANSI: 5
[    2.723982] sd 3:0:0:0: Attached scsi generic sg1 type 0
[    2.724059] sd 3:0:0:0: [sda] 1953525168 512-byte logical blocks: (1.00 TB/931 GiB)
[    2.724493] sd 3:0:0:0: [sda] Write Protect is off
[    2.724499] sd 3:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    2.724690] sd 3:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.725555]  sda:
[    2.733760] input: Chicony Saitek Eclipse Keyboard as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.8/2-1.8:1.1/input/input4
[    2.733874] generic-usb 0003:06A3:8020.0003: input,hiddev96,hidraw2: USB HID v1.11 Device [Chicony Saitek Eclipse Keyboard] on usb-0000:00:1d.0-1.8/input1
[    2.733884] usbcore: registered new interface driver usbhid
[    2.733885] usbhid: USB HID core driver
[    2.735757]  sda1 sda2 sda3 < sda5 sda6 >
[    2.764674] sd 3:0:0:0: [sda] Attached SCSI disk
[    3.072839] ata5: SATA link down (SStatus 0 SControl 300)
[    3.442102] ata6: SATA link down (SStatus 0 SControl 300)
[    3.821338] ata7: SATA link down (SStatus 0 SControl 300)
[    4.190644] ata8: SATA link down (SStatus 0 SControl 300)
[    4.597609] EXT4-fs (sda5): mounted filesystem with ordered data mode. Opts: (null)
[   14.130985] udev[390]: starting version 163
[   14.134286] Adding 9962492k swap on /dev/sda6.  Priority:-1 extents:1 across:9962492k 
[   14.139240] lp: driver loaded but no devices found
[   14.190135] nvidia: module license 'NVIDIA' taints kernel.
[   14.190138] Disabling lock debugging due to kernel taint
[   14.220938] Linux video capture interface: v2.00
[   14.223406] uvcvideo: Found UVC 1.00 device <unnamed> (046d:080f)
[   14.242531] input: UVC Camera (046d:080f) as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.7/2-1.7:1.0/input/input5
[   14.242572] usbcore: registered new interface driver uvcvideo
[   14.242573] USB Video Class driver (v0.1.0)
[   14.289052]   alloc irq_desc for 22 on node -1
[   14.289054]   alloc kstat_irqs on node -1
[   14.289060] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[   14.289129]   alloc irq_desc for 53 on node -1
[   14.289131]   alloc kstat_irqs on node -1
[   14.289138] HDA Intel 0000:00:1b.0: irq 53 for MSI/MSI-X
[   14.289160] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   14.302205] type=1400 audit(1288289717.778:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient3" pid=666 comm="apparmor_parser"
[   14.302590] type=1400 audit(1288289717.778:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=666 comm="apparmor_parser"
[   14.302800] type=1400 audit(1288289717.778:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=666 comm="apparmor_parser"
[   14.504243] nvidia 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   14.504250] nvidia 0000:01:00.0: setting latency timer to 64
[   14.504254] vgaarb: device changed decodes: PCI:0000:01:00.0,olddecodes=io+mem,decodes=none:owns=io+mem
[   14.504575] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  260.19.12  Fri Oct  8 11:17:08 PDT 2010
[   14.911665] EXT4-fs (sda5): re-mounted. Opts: errors=remount-ro
[   15.010353] r8169 0000:02:00.0: eth0: link up
[   15.010359] r8169 0000:02:00.0: eth0: link up
[   15.012785] type=1400 audit(1288289718.488:5): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient3" pid=979 comm="apparmor_parser"
[   15.013204] type=1400 audit(1288289718.488:6): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=979 comm="apparmor_parser"
[   15.013455] type=1400 audit(1288289718.488:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=979 comm="apparmor_parser"
[   15.013622] type=1400 audit(1288289718.488:8): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince" pid=980 comm="apparmor_parser"
[   15.014618] type=1400 audit(1288289718.488:9): apparmor="STATUS" operation="profile_load" name="/usr/sbin/tcpdump" pid=984 comm="apparmor_parser"
[   15.015199] type=1400 audit(1288289718.488:10): apparmor="STATUS" operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" pid=982 comm="apparmor_parser"
[   15.015235] type=1400 audit(1288289718.488:11): apparmor="STATUS" operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" pid=977 comm="apparmor_parser"
[   15.030168] ppdev: user-space parallel port driver
[   18.492511] EXT4-fs (sda5): re-mounted. Opts: errors=remount-ro,commit=0
[   25.633567] eth0: no IPv6 routers present
[   32.277007] usb 1-1.6: new high speed USB device using ehci_hcd and address 3
[   32.476877] Initializing USB Mass Storage driver...
[   32.477180] scsi8 : usb-storage 1-1.6:1.0
[   32.477499] usbcore: registered new interface driver usb-storage
[   32.477503] USB Mass Storage support registered.
[   33.476140] scsi 8:0:0:0: Direct-Access     SanDisk  SDDR-113         9412 PQ: 0 ANSI: 0
[   33.478314] sd 8:0:0:0: Attached scsi generic sg2 type 0
[   33.629710] sd 8:0:0:0: [sdb] 7959552 512-byte logical blocks: (4.07 GB/3.79 GiB)
[   33.631023] sd 8:0:0:0: [sdb] Write Protect is off
[   33.631029] sd 8:0:0:0: [sdb] Mode Sense: 03 00 00 00
[   33.631033] sd 8:0:0:0: [sdb] Assuming drive cache: write through
[   33.634120] sd 8:0:0:0: [sdb] Assuming drive cache: write through
[   33.634127]  sdb: sdb1
[   33.638978] sd 8:0:0:0: [sdb] Assuming drive cache: write through
[   33.638981] sd 8:0:0:0: [sdb] Attached SCSI removable disk
[   71.868736] WARNING! power/level is deprecated; use power/control instead
[   71.968822] usb 1-1.6: USB disconnect, address 3

```

---

### Post by linuxpyro on 2010-10-28
What hardware did you add?

---

### Post by tripmix on 2010-10-28
Is that the output when it fails? Does it fail right after the disconnect usb message? Everything looks fine to me, all I could see was some missing/broken firmware for some pci device. The picture you took looks different but it's not really useful.

---

### Post by TheBuzzSaw on 2010-10-28
> **linuxpyro said:**
> What hardware did you add?
ASUS P7P55 LX
Core i5 Quad 2.8GHz
4 GB DDR3 RAM (Corsair)
1 TB Caviar Black

> **tripmix said:**
> Is that the output when it fails? Does it fail right after the disconnect usb message? Everything looks fine to me, all I could see was some missing/broken firmware for some pci device. The picture you took looks different but it's not really useful.
The messages in the photograph are what shows when it fails. The text block above is the requested information from dmesg.

---

### Post by TheBuzzSaw on 2010-11-12
I think I may have found the solution:
[http://ubuntuforums.org/showpost.php?p=10107400&postcount=17](http://ubuntuforums.org/showpost.php?p=10107400&postcount=17)

---

