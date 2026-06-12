---
title: "restricted items don't initialize fully"
date: 2010-02-10
forum: General Help
---

### Post by BentFX on 2010-02-10
Okay here's the deal... It was working good, then something happened, I don't know what, and now it's broke... Help Me!!!

It's my CPU scaling and dual mode modem that aren't initializing properly on startup. The CPU scaling starts up in 'performance' mode and doesn't throttle back to 'on demand' like it should, and like it used to. Also the modem starts up as a usb mass storage device and the boot process should, and used to, toggle it into modem mode.

It certainly looks like it is a user rights issue as both devices require me to sudo the change from userspace. I'm on 9.10 64bit with a fairly new install, I havent done anything abnormal to the system except change the default lang from UTF-8 to ISO-8859. other than that I've only installed packages from synaptic, and done the recommended updates. I don't know exactly where the problem started.

I'm a noobee at reading log files. I generally only get about a half a screenfull read before I realize my eyes are crossing and my brain has gone completely non-functional. Here is the output from dmesg... Very near the end I see it recognize the Cricket(modem) device, but I see no errors...
```

[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.31-19-generic (buildd@crested) (gcc version 4.4.1 (Ubuntu 4.4.1-4ubuntu8) ) #56-Ubuntu SMP Thu Jan 28 02:39:34 UTC 2010 (Ubuntu 2.6.31-19.56-generic)
[    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-2.6.31-19-generic root=UUID=fa965c33-cd5d-4327-b3ca-e838a0b5fab1 ro quiet splash
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   Centaur CentaurHauls
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e1000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 00000000bffa0000 (usable)
[    0.000000]  BIOS-e820: 00000000bffa0000 - 00000000bffaf000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000bffaf000 - 00000000bffe0000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000bffe0000 - 00000000c0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fff00000 - 0000000100000000 (reserved)
[    0.000000]  BIOS-e820: 0000000100000000 - 0000000140000000 (usable)
[    0.000000] DMI 2.5 present.
[    0.000000] AMI BIOS detected: BIOS may corrupt low RAM, working around it.
[    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
[    0.000000] last_pfn = 0x140000 max_arch_pfn = 0x400000000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-CFFFF write-protect
[    0.000000]   D0000-DFFFF uncachable
[    0.000000]   E0000-EFFFF write-through
[    0.000000]   F0000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000 mask F00000000 write-back
[    0.000000]   1 base 100000000 mask FC0000000 write-back
[    0.000000]   2 base 0C0000000 mask FC0000000 uncachable
[    0.000000]   3 disabled
[    0.000000]   4 disabled
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] e820 update range: 00000000c0000000 - 0000000100000000 (usable) ==> (reserved)
[    0.000000] last_pfn = 0xbffa0 max_arch_pfn = 0x400000000
[    0.000000] Scanning 0 areas for low memory corruption
[    0.000000] modified physical RAM map:
[    0.000000]  modified: 0000000000000000 - 0000000000010000 (reserved)
[    0.000000]  modified: 0000000000010000 - 000000000009fc00 (usable)
[    0.000000]  modified: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  modified: 00000000000e1000 - 0000000000100000 (reserved)
[    0.000000]  modified: 0000000000100000 - 00000000bffa0000 (usable)
[    0.000000]  modified: 00000000bffa0000 - 00000000bffaf000 (ACPI data)
[    0.000000]  modified: 00000000bffaf000 - 00000000bffe0000 (ACPI NVS)
[    0.000000]  modified: 00000000bffe0000 - 00000000c0000000 (reserved)
[    0.000000]  modified: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  modified: 00000000fff00000 - 0000000100000000 (reserved)
[    0.000000]  modified: 0000000100000000 - 0000000140000000 (usable)
[    0.000000] initial memory mapped : 0 - 20000000
[    0.000000] init_memory_mapping: 0000000000000000-00000000bffa0000
[    0.000000] NX (Execute Disable) protection: active
[    0.000000]  0000000000 - 00bfe00000 page 2M
[    0.000000]  00bfe00000 - 00bffa0000 page 4k
[    0.000000] kernel direct mapping tables up to bffa0000 @ 10000-15000
[    0.000000] init_memory_mapping: 0000000100000000-0000000140000000
[    0.000000] NX (Execute Disable) protection: active
[    0.000000]  0100000000 - 0140000000 page 2M
[    0.000000] kernel direct mapping tables up to 140000000 @ 13000-19000
[    0.000000] RAMDISK: 3786d000 - 37fefc52
[    0.000000] ACPI: RSDP 00000000000f92f0 00024 (v02 ACPIAM)
[    0.000000] ACPI: XSDT 00000000bffa0100 0007C (v01 _ASUS_ Notebook 20081107 MSFT 00000097)
[    0.000000] ACPI: FACP 00000000bffa0290 000F4 (v03 110708 FACP1017 20081107 MSFT 00000097)
[    0.000000] ACPI: DSDT 00000000bffa0690 0B7DE (v01  G50V0 G50V0100 00000100 INTL 20051117)
[    0.000000] ACPI: FACS 00000000bffaf000 00040
[    0.000000] ACPI: APIC 00000000bffa0390 0006C (v01 110708 APIC1017 20081107 MSFT 00000097)
[    0.000000] ACPI: MCFG 00000000bffa0440 0003C (v01 110708 OEMMCFG  20081107 MSFT 00000097)
[    0.000000] ACPI: SLIC 00000000bffa0480 00176 (v01 _ASUS_ Notebook 20081107 MSFT 00000097)
[    0.000000] ACPI: ECDT 00000000bffa0630 00054 (v01 110708 OEMECDT  20081107 MSFT 00000097)
[    0.000000] ACPI: DBGP 00000000bffa0400 00034 (v01 110708 DBGP1017 20081107 MSFT 00000097)
[    0.000000] ACPI: BOOT 00000000bffa0600 00028 (v01 110708 BOOT1017 20081107 MSFT 00000097)
[    0.000000] ACPI: OEMB 00000000bffaf040 00071 (v01 110708 OEMB1017 20081107 MSFT 00000097)
[    0.000000] ACPI: HPET 00000000bffabe70 00038 (v01 110708 OEMHPET  20081107 MSFT 00000097)
[    0.000000] ACPI: ATKG 00000000bffaf2c0 08024 (v01 110708  OEMATKG 20081107 MSFT 00000097)
[    0.000000] ACPI: SSDT 00000000bffb7dd0 004F0 (v01  PmRef    CpuPm 00003000 INTL 20051117)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] No NUMA configuration found
[    0.000000] Faking a node at 0000000000000000-0000000140000000
[    0.000000] Bootmem setup node 0 0000000000000000-0000000140000000
[    0.000000]   NODE_DATA [0000000000014000 - 0000000000018fff]
[    0.000000]   bootmap [0000000000019000 -  0000000000040fff] pages 28
[    0.000000] (8 early reservations) ==> bootmem [0000000000 - 0140000000]
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
[    0.000000]   #1 [0000006000 - 0000008000]       TRAMPOLINE ==> [0000006000 - 0000008000]
[    0.000000]   #2 [0001000000 - 00019e4ccc]    TEXT DATA BSS ==> [0001000000 - 00019e4ccc]
[    0.000000]   #3 [003786d000 - 0037fefc52]          RAMDISK ==> [003786d000 - 0037fefc52]
[    0.000000]   #4 [000009fc00 - 0000100000]    BIOS reserved ==> [000009fc00 - 0000100000]
[    0.000000]   #5 [00019e5000 - 00019e5334]              BRK ==> [00019e5000 - 00019e5334]
[    0.000000]   #6 [0000010000 - 0000013000]          PGTABLE ==> [0000010000 - 0000013000]
[    0.000000]   #7 [0000013000 - 0000014000]          PGTABLE ==> [0000013000 - 0000014000]
[    0.000000] found SMP MP-table at [ffff8800000ff780] ff780
[    0.000000]  [ffffea0000000000-ffffea00045fffff] PMD -> [ffff880028600000-ffff88002bdfffff] on node 0
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000010 -> 0x00001000
[    0.000000]   DMA32    0x00001000 -> 0x00100000
[    0.000000]   Normal   0x00100000 -> 0x00140000
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[3] active PFN ranges
[    0.000000]     0: 0x00000010 -> 0x0000009f
[    0.000000]     0: 0x00000100 -> 0x000bffa0
[    0.000000]     0: 0x00100000 -> 0x00140000
[    0.000000] On node 0 totalpages: 1048367
[    0.000000]   DMA zone: 56 pages used for memmap
[    0.000000]   DMA zone: 103 pages reserved
[    0.000000]   DMA zone: 3824 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 14280 pages used for memmap
[    0.000000]   DMA32 zone: 767960 pages, LIFO batch:31
[    0.000000]   Normal zone: 3584 pages used for memmap
[    0.000000]   Normal zone: 258560 pages, LIFO batch:31
[    0.000000] ACPI: PM-Timer IO Port: 0x808
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x82] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x83] disabled)
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x8086a301 base: 0xfed00000
[    0.000000] SMP: Allowing 4 CPUs, 2 hotplug CPUs
[    0.000000] nr_irqs_gsi: 24
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e1000
[    0.000000] PM: Registered nosave memory: 00000000000e1000 - 0000000000100000
[    0.000000] PM: Registered nosave memory: 00000000bffa0000 - 00000000bffaf000
[    0.000000] PM: Registered nosave memory: 00000000bffaf000 - 00000000bffe0000
[    0.000000] PM: Registered nosave memory: 00000000bffe0000 - 00000000c0000000
[    0.000000] PM: Registered nosave memory: 00000000c0000000 - 00000000fee00000
[    0.000000] PM: Registered nosave memory: 00000000fee00000 - 00000000fee01000
[    0.000000] PM: Registered nosave memory: 00000000fee01000 - 00000000fff00000
[    0.000000] PM: Registered nosave memory: 00000000fff00000 - 0000000100000000
[    0.000000] Allocating PCI resources starting at c0000000 (gap: c0000000:3ee00000)
[    0.000000] NR_CPUS:64 nr_cpumask_bits:64 nr_cpu_ids:4 nr_node_ids:1
[    0.000000] PERCPU: Embedded 30 pages at ffff880028022000, static data 90720 bytes
[    0.000000] Built 1 zonelists in Node order, mobility grouping on.  Total pages: 1030344
[    0.000000] Policy zone: Normal
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.31-19-generic root=UUID=fa965c33-cd5d-4327-b3ca-e838a0b5fab1 ro quiet splash
[    0.000000] PID hash table entries: 4096 (order: 12, 32768 bytes)
[    0.000000] Initializing CPU#0
[    0.000000] Checking aperture...
[    0.000000] No AGP bridge found
[    0.000000] Calgary: detecting Calgary via BIOS EBDA area
[    0.000000] Calgary: Unable to locate Rio Grande table in EBDA - bailing!
[    0.000000] PCI-DMA: Using software bounce buffering for IO (SWIOTLB)
[    0.000000] Placing 64MB software IO TLB between ffff880020000000 - ffff880024000000
[    0.000000] software IO TLB at phys 0x20000000 - 0x24000000
[    0.000000] Memory: 4051628k/5242880k available (5315k kernel code, 1049412k absent, 141840k reserved, 3017k data, 660k init)
[    0.000000] SLUB: Genslabs=14, HWalign=64, Order=0-3, MinObjects=0, CPUs=4, Nodes=1
[    0.000000] NR_IRQS:4352 nr_irqs:440
[    0.000000] Extended CMOS year: 2000
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 2128.034 MHz processor.
[    0.006227] Console: colour VGA+ 80x25
[    0.006230] console [tty0] enabled
[    0.010000] allocated 41943040 bytes of page_cgroup
[    0.010000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.010000] hpet clockevent registered
[    0.010000] HPET: 4 timers in total, 0 timers will be used for per-cpu timer
[    0.010000] Calibrating delay loop (skipped), value calculated using timer frequency.. 4256.06 BogoMIPS (lpj=21280340)
[    0.010000] Security Framework initialized
[    0.010000] AppArmor: AppArmor initialized
[    0.010000] Dentry cache hash table entries: 524288 (order: 10, 4194304 bytes)
[    0.010000] Inode-cache hash table entries: 262144 (order: 9, 2097152 bytes)
[    0.010000] Mount-cache hash table entries: 256
[    0.010000] Initializing cgroup subsys ns
[    0.010000] Initializing cgroup subsys cpuacct
[    0.010000] Initializing cgroup subsys memory
[    0.010000] Initializing cgroup subsys freezer
[    0.010000] Initializing cgroup subsys net_cls
[    0.010000] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.010000] CPU: L2 cache: 3072K
[    0.010000] CPU 0/0x0 -> Node 0
[    0.010000] CPU: Physical Processor ID: 0
[    0.010000] CPU: Processor Core ID: 0
[    0.010000] mce: CPU supports 6 MCE banks
[    0.010000] CPU0: Thermal monitoring enabled (TM2)
[    0.010000] using mwait in idle threads.
[    0.010000] Performance Counters: Core2 events, Intel PMU driver.
[    0.010000] ... version:                 2
[    0.010000] ... bit width:               40
[    0.010000] ... generic counters:        2
[    0.010000] ... value mask:              000000ffffffffff
[    0.010000] ... max period:              000000007fffffff
[    0.010000] ... fixed-purpose counters:  3
[    0.010000] ... counter mask:            0000000700000003
[    0.010000] ACPI: Core revision 20090521
[    0.030056] Setting APIC routing to flat
[    0.030404] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.142628] CPU0: Intel(R) Core(TM)2 Duo CPU     P7450  @ 2.13GHz stepping 06
[    0.150000] Booting processor 1 APIC 0x1 ip 0x6000
[    0.010000] Initializing CPU#1
[    0.010000] Calibrating delay using timer specific routine.. 4256.00 BogoMIPS (lpj=21280025)
[    0.010000] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.010000] CPU: L2 cache: 3072K
[    0.010000] CPU 1/0x1 -> Node 0
[    0.010000] CPU: Physical Processor ID: 0
[    0.010000] CPU: Processor Core ID: 1
[    0.010000] mce: CPU supports 6 MCE banks
[    0.010000] CPU1: Thermal monitoring enabled (TM2)
[    0.010000] x86 PAT enabled: cpu 1, old 0x7040600070406, new 0x7010600070106
[    0.301499] CPU1: Intel(R) Core(TM)2 Duo CPU     P7450  @ 2.13GHz stepping 06
[    0.301508] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
[    0.310024] Brought up 2 CPUs
[    0.310026] Total of 2 processors activated (8512.07 BogoMIPS).
[    0.310079] CPU0 attaching sched-domain:
[    0.310081]  domain 0: span 0-1 level MC
[    0.310084]   groups: 0 1
[    0.310088] CPU1 attaching sched-domain:
[    0.310090]  domain 0: span 0-1 level MC
[    0.310092]   groups: 1 0
[    0.310162] Booting paravirtualized kernel on bare hardware
[    0.310162] regulator: core version 0.5
[    0.310162] Time: 11:52:51  Date: 02/10/10
[    0.310162] NET: Registered protocol family 16
[    0.310204] ACPI FADT declares the system doesn't support PCIe ASPM, so disable it
[    0.310207] ACPI: bus type pci registered
[    0.310277] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 255
[    0.310279] PCI: Not using MMCONFIG.
[    0.310281] PCI: Using configuration type 1 for base access
[    0.311055] bio: create slab <bio-0> at 0
[    0.311178] ACPI: EC: EC description table is found, configuring boot EC
[    0.311187] ACPI: EC: Look up EC in DSDT
[    0.316440] ACPI: BIOS _OSI(Linux) query ignored
[    0.323052] ACPI: Interpreter enabled
[    0.323055] ACPI: (supports S0 S1 S3 S4 S5)
[    0.323080] ACPI: Using IOAPIC for interrupt routing
[    0.323173] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 255
[    0.325570] PCI: MCFG area at e0000000 reserved in ACPI motherboard resources
[    0.336455] PCI: Using MMCONFIG at e0000000 - efffffff
[    0.346291] ACPI: EC: GPE = 0x1b, I/O: command/status = 0x66, data = 0x62
[    0.346293] ACPI: EC: driver started in poll mode
[    0.349144] ACPI Warning: Incorrect checksum in table [ATKG] - 75, should be EA 20090521 tbutils-246
[    0.349365] ACPI: No dock devices found.
[    0.349904] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.350010] pci 0000:00:01.0: PME# supported from D0 D3hot D3cold
[    0.350014] pci 0000:00:01.0: PME# disabled
[    0.350117] pci 0000:00:1a.0: reg 20 io port: [0xbc00-0xbc1f]
[    0.350216] pci 0000:00:1a.1: reg 20 io port: [0xb880-0xb89f]
[    0.350315] pci 0000:00:1a.2: reg 20 io port: [0xb800-0xb81f]
[    0.350414] pci 0000:00:1a.7: reg 10 32bit mmio: [0xf9fffc00-0xf9ffffff]
[    0.350485] pci 0000:00:1a.7: PME# supported from D0 D3hot D3cold
[    0.350490] pci 0000:00:1a.7: PME# disabled
[    0.350549] pci 0000:00:1b.0: reg 10 64bit mmio: [0xf9ff8000-0xf9ffbfff]
[    0.350612] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    0.350617] pci 0000:00:1b.0: PME# disabled
[    0.350703] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    0.350708] pci 0000:00:1c.0: PME# disabled
[    0.350799] pci 0000:00:1c.1: PME# supported from D0 D3hot D3cold
[    0.350803] pci 0000:00:1c.1: PME# disabled
[    0.350894] pci 0000:00:1c.2: PME# supported from D0 D3hot D3cold
[    0.350898] pci 0000:00:1c.2: PME# disabled
[    0.350992] pci 0000:00:1c.5: PME# supported from D0 D3hot D3cold
[    0.350996] pci 0000:00:1c.5: PME# disabled
[    0.351076] pci 0000:00:1d.0: reg 20 io port: [0xb480-0xb49f]
[    0.351175] pci 0000:00:1d.1: reg 20 io port: [0xb400-0xb41f]
[    0.351273] pci 0000:00:1d.2: reg 20 io port: [0xb080-0xb09f]
[    0.351372] pci 0000:00:1d.7: reg 10 32bit mmio: [0xf9fff800-0xf9fffbff]
[    0.351443] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
[    0.351448] pci 0000:00:1d.7: PME# disabled
[    0.351679] pci 0000:00:1f.2: reg 10 io port: [0xb000-0xb007]
[    0.351687] pci 0000:00:1f.2: reg 14 io port: [0xac00-0xac03]
[    0.351694] pci 0000:00:1f.2: reg 18 io port: [0xa880-0xa887]
[    0.351702] pci 0000:00:1f.2: reg 1c io port: [0xa800-0xa803]
[    0.351710] pci 0000:00:1f.2: reg 20 io port: [0xa480-0xa48f]
[    0.351718] pci 0000:00:1f.2: reg 24 io port: [0xa400-0xa40f]
[    0.351806] pci 0000:00:1f.5: reg 10 io port: [0xa000-0xa007]
[    0.351813] pci 0000:00:1f.5: reg 14 io port: [0x9c00-0x9c03]
[    0.351821] pci 0000:00:1f.5: reg 18 io port: [0x9880-0x9887]
[    0.351829] pci 0000:00:1f.5: reg 1c io port: [0x9800-0x9803]
[    0.351837] pci 0000:00:1f.5: reg 20 io port: [0x9480-0x948f]
[    0.351845] pci 0000:00:1f.5: reg 24 io port: [0x9400-0x940f]
[    0.351963] pci 0000:01:00.0: reg 10 32bit mmio: [0xfc000000-0xfcffffff]
[    0.351984] pci 0000:01:00.0: reg 14 64bit mmio: [0xd0000000-0xdfffffff]
[    0.352010] pci 0000:01:00.0: reg 1c 64bit mmio: [0xfa000000-0xfbffffff]
[    0.352024] pci 0000:01:00.0: reg 24 io port: [0xcc00-0xcc7f]
[    0.352039] pci 0000:01:00.0: reg 30 32bit mmio: [0x000000-0x07ffff]
[    0.352190] pci 0000:00:01.0: bridge io port: [0xc000-0xcfff]
[    0.352193] pci 0000:00:01.0: bridge 32bit mmio: [0xfa000000-0xfdefffff]
[    0.352197] pci 0000:00:01.0: bridge 64bit mmio pref: [0xd0000000-0xdfffffff]
[    0.352393] pci 0000:03:00.0: reg 10 64bit mmio: [0xfdffe000-0xfdffffff]
[    0.352523] pci 0000:03:00.0: PME# supported from D0 D3hot D3cold
[    0.352544] pci 0000:03:00.0: PME# disabled
[    0.352640] pci 0000:00:1c.1: bridge 32bit mmio: [0xfdf00000-0xfdffffff]
[    0.352707] pci 0000:00:1c.2: bridge io port: [0xd000-0xdfff]
[    0.352712] pci 0000:00:1c.2: bridge 32bit mmio: [0xfe000000-0xfe9fffff]
[    0.352720] pci 0000:00:1c.2: bridge 64bit mmio pref: [0xf6000000-0xf8efffff]
[    0.352886] pci 0000:06:00.0: reg 10 io port: [0xe800-0xe8ff]
[    0.352962] pci 0000:06:00.0: reg 18 64bit mmio: [0xf8fff000-0xf8ffffff]
[    0.353009] pci 0000:06:00.0: reg 20 64bit mmio: [0xf8fe0000-0xf8feffff]
[    0.353036] pci 0000:06:00.0: reg 30 32bit mmio: [0xfeaf0000-0xfeafffff]
[    0.353189] pci 0000:06:00.0: supports D1 D2
[    0.353191] pci 0000:06:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.353205] pci 0000:06:00.0: PME# disabled
[    0.353344] pci 0000:00:1c.5: bridge io port: [0xe000-0xefff]
[    0.353349] pci 0000:00:1c.5: bridge 32bit mmio: [0xfea00000-0xfeafffff]
[    0.353357] pci 0000:00:1c.5: bridge 64bit mmio pref: [0xf8f00000-0xf8ffffff]
[    0.353401] pci 0000:07:01.0: reg 10 32bit mmio: [0xfebff800-0xfebfffff]
[    0.353460] pci 0000:07:01.0: PME# supported from D0 D3hot D3cold
[    0.353464] pci 0000:07:01.0: PME# disabled
[    0.353506] pci 0000:07:01.1: reg 10 32bit mmio: [0xfebff400-0xfebff4ff]
[    0.353564] pci 0000:07:01.1: supports D1 D2
[    0.353566] pci 0000:07:01.1: PME# supported from D0 D1 D2 D3hot D3cold
[    0.353571] pci 0000:07:01.1: PME# disabled
[    0.353612] pci 0000:07:01.2: reg 10 32bit mmio: [0xfebff000-0xfebff0ff]
[    0.353671] pci 0000:07:01.2: supports D1 D2
[    0.353673] pci 0000:07:01.2: PME# supported from D0 D1 D2 D3hot D3cold
[    0.353678] pci 0000:07:01.2: PME# disabled
[    0.353719] pci 0000:07:01.3: reg 10 32bit mmio: [0xfebfec00-0xfebfecff]
[    0.353777] pci 0000:07:01.3: supports D1 D2
[    0.353779] pci 0000:07:01.3: PME# supported from D0 D1 D2 D3hot D3cold
[    0.353784] pci 0000:07:01.3: PME# disabled
[    0.353825] pci 0000:07:01.4: reg 10 32bit mmio: [0xfebfe800-0xfebfe8ff]
[    0.353883] pci 0000:07:01.4: supports D1 D2
[    0.353885] pci 0000:07:01.4: PME# supported from D0 D1 D2 D3hot D3cold
[    0.353890] pci 0000:07:01.4: PME# disabled
[    0.353953] pci 0000:00:1e.0: transparent bridge
[    0.353961] pci 0000:00:1e.0: bridge 32bit mmio: [0xfeb00000-0xfebfffff]
[    0.354006] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.354190] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P1._PRT]
[    0.354263] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P3._PRT]
[    0.354328] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P4._PRT]
[    0.354455] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P8._PRT]
[    0.354518] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P9._PRT]
[    0.377226] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 *10 11 12)
[    0.377370] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 *5 10 12)
[    0.377511] ACPI: PCI Interrupt Link [LNKC] (IRQs *6)
[    0.377650] ACPI: PCI Interrupt Link [LNKD] (IRQs *3 4 5 7 10 12)
[    0.377791] ACPI: PCI Interrupt Link [LNKE] (IRQs 6) *0, disabled.
[    0.377930] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 *7 10 12)
[    0.378071] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 *4 5 6 7 10 12)
[    0.378212] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 *10 12)
[    0.378386] SCSI subsystem initialized
[    0.378409] libata version 3.00 loaded.
[    0.378409] usbcore: registered new interface driver usbfs
[    0.378409] usbcore: registered new interface driver hub
[    0.378409] usbcore: registered new device driver usb
[    0.378409] ACPI: WMI: Mapper loaded
[    0.378409] PCI: Using ACPI for IRQ routing
[    0.410007] Bluetooth: Core ver 2.15
[    0.410020] NET: Registered protocol family 31
[    0.410020] Bluetooth: HCI device and connection manager initialized
[    0.410020] Bluetooth: HCI socket layer initialized
[    0.410020] NetLabel: Initializing
[    0.410020] NetLabel:  domain hash size = 128
[    0.410020] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.410031] NetLabel:  unlabeled traffic allowed by default
[    0.410075] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0
[    0.410080] hpet0: 4 comparators, 64-bit 14.318180 MHz counter
[    0.450006] pnp: PnP ACPI init
[    0.450015] ACPI: bus type pnp registered
[    0.452809] pnp: PnP ACPI: found 14 devices
[    0.452811] ACPI: ACPI bus type pnp unregistered
[    0.452820] system 00:01: iomem range 0xfed10000-0xfed19fff has been reserved
[    0.452829] system 00:08: ioport range 0x4d0-0x4d1 has been reserved
[    0.452831] system 00:08: ioport range 0x800-0x87f has been reserved
[    0.452834] system 00:08: ioport range 0x400-0x41f has been reserved
[    0.452836] system 00:08: ioport range 0x500-0x57f has been reserved
[    0.452839] system 00:08: iomem range 0xfed1c000-0xfed1ffff has been reserved
[    0.452842] system 00:08: iomem range 0xfed20000-0xfed3ffff has been reserved
[    0.452845] system 00:08: iomem range 0xfed45000-0xfed89fff has been reserved
[    0.452848] system 00:08: iomem range 0xfed90000-0xfed90fff has been reserved
[    0.452850] system 00:08: iomem range 0xfed91000-0xfed91fff has been reserved
[    0.452853] system 00:08: iomem range 0xfed92000-0xfed92fff has been reserved
[    0.452856] system 00:08: iomem range 0xfed93000-0xfed93fff has been reserved
[    0.452858] system 00:08: iomem range 0xffb00000-0xffbfffff has been reserved
[    0.452861] system 00:08: iomem range 0xfff00000-0xffffffff has been reserved
[    0.452868] system 00:0a: ioport range 0x250-0x253 has been reserved
[    0.452871] system 00:0a: ioport range 0x256-0x25f has been reserved
[    0.452874] system 00:0a: iomem range 0xfec00000-0xfec00fff could not be reserved
[    0.452877] system 00:0a: iomem range 0xfee00000-0xfee00fff has been reserved
[    0.452879] system 00:0a: iomem range 0xfec10000-0xfec17fff has been reserved
[    0.452882] system 00:0a: iomem range 0xfec18000-0xfec1ffff has been reserved
[    0.452884] system 00:0a: iomem range 0xfec20000-0xfec27fff has been reserved
[    0.452887] system 00:0a: iomem range 0xfec38000-0xfec3ffff has been reserved
[    0.452892] system 00:0c: iomem range 0xe0000000-0xefffffff has been reserved
[    0.452897] system 00:0d: iomem range 0x0-0x9ffff could not be reserved
[    0.452900] system 00:0d: iomem range 0xc0000-0xcffff has been reserved
[    0.452902] system 00:0d: iomem range 0xe0000-0xfffff could not be reserved
[    0.452905] system 00:0d: iomem range 0x100000-0xbfffffff could not be reserved
[    0.457576] AppArmor: AppArmor Filesystem Enabled
[    0.457649] pci 0000:00:01.0: PCI bridge, secondary bus 0000:01
[    0.457652] pci 0000:00:01.0:   IO window: 0xc000-0xcfff
[    0.457656] pci 0000:00:01.0:   MEM window: 0xfa000000-0xfdefffff
[    0.457659] pci 0000:00:01.0:   PREFETCH window: 0x000000d0000000-0x000000dfffffff
[    0.457664] pci 0000:00:1c.0: PCI bridge, secondary bus 0000:02
[    0.457666] pci 0000:00:1c.0:   IO window: disabled
[    0.457672] pci 0000:00:1c.0:   MEM window: disabled
[    0.457676] pci 0000:00:1c.0:   PREFETCH window: disabled
[    0.457681] pci 0000:00:1c.1: PCI bridge, secondary bus 0000:03
[    0.457683] pci 0000:00:1c.1:   IO window: disabled
[    0.457689] pci 0000:00:1c.1:   MEM window: 0xfdf00000-0xfdffffff
[    0.457694] pci 0000:00:1c.1:   PREFETCH window: disabled
[    0.457699] pci 0000:00:1c.2: PCI bridge, secondary bus 0000:04
[    0.457702] pci 0000:00:1c.2:   IO window: 0xd000-0xdfff
[    0.457708] pci 0000:00:1c.2:   MEM window: 0xfe000000-0xfe9fffff
[    0.457713] pci 0000:00:1c.2:   PREFETCH window: 0x000000f6000000-0x000000f8efffff
[    0.457721] pci 0000:00:1c.5: PCI bridge, secondary bus 0000:06
[    0.457725] pci 0000:00:1c.5:   IO window: 0xe000-0xefff
[    0.457731] pci 0000:00:1c.5:   MEM window: 0xfea00000-0xfeafffff
[    0.457736] pci 0000:00:1c.5:   PREFETCH window: 0x000000f8f00000-0x000000f8ffffff
[    0.457744] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:07
[    0.457746] pci 0000:00:1e.0:   IO window: disabled
[    0.457752] pci 0000:00:1e.0:   MEM window: 0xfeb00000-0xfebfffff
[    0.457757] pci 0000:00:1e.0:   PREFETCH window: disabled
[    0.457767]   alloc irq_desc for 16 on node 0
[    0.457769]   alloc kstat_irqs on node 0
[    0.457773] pci 0000:00:01.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.457777] pci 0000:00:01.0: setting latency timer to 64
[    0.457785] pci 0000:00:1c.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.457790] pci 0000:00:1c.0: setting latency timer to 64
[    0.457798]   alloc irq_desc for 17 on node 0
[    0.457800]   alloc kstat_irqs on node 0
[    0.457803] pci 0000:00:1c.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    0.457807] pci 0000:00:1c.1: setting latency timer to 64
[    0.457816]   alloc irq_desc for 18 on node 0
[    0.457817]   alloc kstat_irqs on node 0
[    0.457820] pci 0000:00:1c.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.457825] pci 0000:00:1c.2: setting latency timer to 64
[    0.457834] pci 0000:00:1c.5: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    0.457839] pci 0000:00:1c.5: setting latency timer to 64
[    0.457847] pci 0000:00:1e.0: setting latency timer to 64
[    0.457851] pci_bus 0000:00: resource 0 io:  [0x00-0xffff]
[    0.457854] pci_bus 0000:00: resource 1 mem: [0x000000-0xffffffffffffffff]
[    0.457856] pci_bus 0000:01: resource 0 io:  [0xc000-0xcfff]
[    0.457858] pci_bus 0000:01: resource 1 mem: [0xfa000000-0xfdefffff]
[    0.457860] pci_bus 0000:01: resource 2 pref mem [0xd0000000-0xdfffffff]
[    0.457863] pci_bus 0000:03: resource 1 mem: [0xfdf00000-0xfdffffff]
[    0.457865] pci_bus 0000:04: resource 0 io:  [0xd000-0xdfff]
[    0.457867] pci_bus 0000:04: resource 1 mem: [0xfe000000-0xfe9fffff]
[    0.457869] pci_bus 0000:04: resource 2 pref mem [0xf6000000-0xf8efffff]
[    0.457872] pci_bus 0000:06: resource 0 io:  [0xe000-0xefff]
[    0.457874] pci_bus 0000:06: resource 1 mem: [0xfea00000-0xfeafffff]
[    0.457876] pci_bus 0000:06: resource 2 pref mem [0xf8f00000-0xf8ffffff]
[    0.457878] pci_bus 0000:07: resource 1 mem: [0xfeb00000-0xfebfffff]
[    0.457881] pci_bus 0000:07: resource 3 io:  [0x00-0xffff]
[    0.457883] pci_bus 0000:07: resource 4 mem: [0x000000-0xffffffffffffffff]
[    0.457911] NET: Registered protocol family 2
[    0.458064] IP route cache hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.459172] TCP established hash table entries: 524288 (order: 11, 8388608 bytes)
[    0.462935] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[    0.463425] TCP: Hash tables configured (established 524288 bind 65536)
[    0.463428] TCP reno registered
[    0.463545] NET: Registered protocol family 1
[    0.463612] Trying to unpack rootfs image as initramfs...
[    0.501536] Switched to high resolution mode on CPU 1
[    0.510007] Switched to high resolution mode on CPU 0
[    0.635796] Freeing initrd memory: 7691k freed
[    0.638559] Simple Boot Flag at 0x51 set to 0x1
[    0.638744] Scanning for low memory corruption every 60 seconds
[    0.638879] audit: initializing netlink socket (disabled)
[    0.638894] type=2000 audit(1265802770.630:1): initialized
[    0.648308] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    0.649617] VFS: Disk quotas dquot_6.5.2
[    0.649666] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    0.650212] fuse init (API version 7.12)
[    0.650289] msgmni has been set to 7928
[    0.650473] alg: No test for stdrng (krng)
[    0.650485] io scheduler noop registered
[    0.650487] io scheduler anticipatory registered
[    0.650489] io scheduler deadline registered
[    0.650527] io scheduler cfq registered (default)
[    0.650723] pci 0000:01:00.0: Boot video device
[    0.650862]   alloc irq_desc for 24 on node 0
[    0.650864]   alloc kstat_irqs on node 0
[    0.650873] pcieport-driver 0000:00:01.0: irq 24 for MSI/MSI-X
[    0.650879] pcieport-driver 0000:00:01.0: setting latency timer to 64
[    0.651023]   alloc irq_desc for 25 on node 0
[    0.651025]   alloc kstat_irqs on node 0
[    0.651034] pcieport-driver 0000:00:1c.0: irq 25 for MSI/MSI-X
[    0.651045] pcieport-driver 0000:00:1c.0: setting latency timer to 64
[    0.651208]   alloc irq_desc for 26 on node 0
[    0.651210]   alloc kstat_irqs on node 0
[    0.651218] pcieport-driver 0000:00:1c.1: irq 26 for MSI/MSI-X
[    0.651229] pcieport-driver 0000:00:1c.1: setting latency timer to 64
[    0.651392]   alloc irq_desc for 27 on node 0
[    0.651394]   alloc kstat_irqs on node 0
[    0.651402] pcieport-driver 0000:00:1c.2: irq 27 for MSI/MSI-X
[    0.651413] pcieport-driver 0000:00:1c.2: setting latency timer to 64
[    0.651584]   alloc irq_desc for 28 on node 0
[    0.651586]   alloc kstat_irqs on node 0
[    0.651594] pcieport-driver 0000:00:1c.5: irq 28 for MSI/MSI-X
[    0.651605] pcieport-driver 0000:00:1c.5: setting latency timer to 64
[    0.651706] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.652050] pciehp 0000:00:01.0:pcie04: HPC vendor_id 8086 device_id 2a41 ss_vid 0 ss_did 0
[    0.652081] pciehp 0000:00:01.0:pcie04: service driver pciehp loaded
[    0.652104] pciehp 0000:00:1c.2:pcie04: HPC vendor_id 8086 device_id 2944 ss_vid 0 ss_did 0
[    0.652143] pciehp 0000:00:1c.2:pcie04: service driver pciehp loaded
[    0.652151] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.652325] ACPI: AC Adapter [AC0] (on-line)
[    0.652381] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input0
[    0.652385] ACPI: Power Button [PWRF]
[    0.652444] input: Sleep Button as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input1
[    0.652451] ACPI: Sleep Button [SLPB]
[    0.652491] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input2
[    0.652719] ACPI: EC: non-query interrupt received, switching to interrupt mode
[    0.674273] ACPI: Lid Switch [LID]
[    0.675277] ACPI: SSDT 00000000bffb73c0 00206 (v01  PmRef  Cpu0Ist 00003000 INTL 20051117)
[    0.675977] ACPI: SSDT 00000000bffb7660 00765 (v01  PmRef  Cpu0Cst 00003001 INTL 20051117)
[    0.676710] Monitor-Mwait will be used to enter C-1 state
[    0.676732] Monitor-Mwait will be used to enter C-3 state
[    0.676745] Marking TSC unstable due to TSC halts in idle
[    0.676757] ACPI: CPU0 (power states: C1[C1] C2[C3])
[    0.676778] processor LNXCPU:00: registered as cooling_device0
[    0.676781] ACPI: Processor [CPU0] (supports 8 throttling states)
[    0.677134] ACPI: SSDT 00000000bffb72f0 000CC (v01  PmRef  Cpu1Ist 00003000 INTL 20051117)
[    0.677535] ACPI: SSDT 00000000bffb75d0 00085 (v01  PmRef  Cpu1Cst 00003000 INTL 20051117)
[    0.678349] ACPI: CPU1 (power states: C1[C1] C2[C3])
[    0.678366] processor LNXCPU:01: registered as cooling_device1
[    0.678369] ACPI: Processor [CPU1] (supports 8 throttling states)
[    0.688148] thermal LNXTHERM:01: registered as thermal_zone0
[    0.688155] ACPI: Thermal Zone [THRM] (30 C)
[    0.689218] Linux agpgart interface v0.103
[    0.689226] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    0.690407] brd: module loaded
[    0.690817] loop: module loaded
[    0.690876] input: Macintosh mouse button emulation as /devices/virtual/input/input3
[    0.691282] ata_piix 0000:00:1f.2: version 2.13
[    0.691295]   alloc irq_desc for 19 on node 0
[    0.691297]   alloc kstat_irqs on node 0
[    0.691302] ata_piix 0000:00:1f.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    0.691308] ata_piix 0000:00:1f.2: MAP [ P0 -- P1 -- ]
[    0.691350] ata_piix 0000:00:1f.2: setting latency timer to 64
[    0.691403] scsi0 : ata_piix
[    0.691474] scsi1 : ata_piix
[    0.692908] ata1: SATA max UDMA/133 cmd 0xb000 ctl 0xac00 bmdma 0xa480 irq 19
[    0.692913] ata2: SATA max UDMA/133 cmd 0xa880 ctl 0xa800 bmdma 0xa488 irq 19
[    0.693024] ata_piix 0000:00:1f.5: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    0.693029] ata_piix 0000:00:1f.5: MAP [ P0 -- P1 -- ]
[    0.693058] ata_piix 0000:00:1f.5: SCR access via SIDPR is available but doesn't work
[    0.693069] ata_piix 0000:00:1f.5: setting latency timer to 64
[    0.693103] scsi2 : ata_piix
[    0.693149] scsi3 : ata_piix
[    0.693180] ata3: SATA max UDMA/133 cmd 0xa000 ctl 0x9c00 bmdma 0x9480 irq 19
[    0.693183] ata4: SATA max UDMA/133 cmd 0x9880 ctl 0x9800 bmdma 0x9488 irq 19
[    0.693961] Fixed MDIO Bus: probed
[    0.693993] PPP generic driver version 2.4.2
[    0.694071] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.694172] ehci_hcd 0000:00:1a.7: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.694224] ehci_hcd 0000:00:1a.7: setting latency timer to 64
[    0.694228] ehci_hcd 0000:00:1a.7: EHCI Host Controller
[    0.694274] ehci_hcd 0000:00:1a.7: new USB bus registered, assigned bus number 1
[    0.698193] ehci_hcd 0000:00:1a.7: debug port 1
[    0.698200] ehci_hcd 0000:00:1a.7: cache line size of 32 is not supported
[    0.698212] ehci_hcd 0000:00:1a.7: irq 18, io mem 0xf9fffc00
[    0.720014] ehci_hcd 0000:00:1a.7: USB 2.0 started, EHCI 1.00
[    0.720113] usb usb1: configuration #1 chosen from 1 choice
[    0.720139] hub 1-0:1.0: USB hub found
[    0.720146] hub 1-0:1.0: 6 ports detected
[    0.720233]   alloc irq_desc for 23 on node 0
[    0.720235]   alloc kstat_irqs on node 0
[    0.720239] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    0.720250] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    0.720254] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    0.720283] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 2
[    0.724225] ehci_hcd 0000:00:1d.7: debug port 1
[    0.724232] ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported
[    0.724243] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xf9fff800
[    0.740021] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    0.740081] usb usb2: configuration #1 chosen from 1 choice
[    0.740104] hub 2-0:1.0: USB hub found
[    0.740110] hub 2-0:1.0: 6 ports detected
[    0.740421] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.740436] uhci_hcd: USB Universal Host Controller Interface driver
[    0.740508] uhci_hcd 0000:00:1a.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.740515] uhci_hcd 0000:00:1a.0: setting latency timer to 64
[    0.740519] uhci_hcd 0000:00:1a.0: UHCI Host Controller
[    0.740548] uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 3
[    0.740581] uhci_hcd 0000:00:1a.0: irq 16, io base 0x0000bc00
[    0.740655] usb usb3: configuration #1 chosen from 1 choice
[    0.740680] hub 3-0:1.0: USB hub found
[    0.740686] hub 3-0:1.0: 2 ports detected
[    0.740754]   alloc irq_desc for 21 on node 0
[    0.740756]   alloc kstat_irqs on node 0
[    0.740759] uhci_hcd 0000:00:1a.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[    0.740766] uhci_hcd 0000:00:1a.1: setting latency timer to 64
[    0.740769] uhci_hcd 0000:00:1a.1: UHCI Host Controller
[    0.740803] uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus number 4
[    0.740834] uhci_hcd 0000:00:1a.1: irq 21, io base 0x0000b880
[    0.740904] usb usb4: configuration #1 chosen from 1 choice
[    0.740929] hub 4-0:1.0: USB hub found
[    0.740934] hub 4-0:1.0: 2 ports detected
[    0.741004] uhci_hcd 0000:00:1a.2: PCI INT D -> GSI 19 (level, low) -> IRQ 19
[    0.741010] uhci_hcd 0000:00:1a.2: setting latency timer to 64
[    0.741014] uhci_hcd 0000:00:1a.2: UHCI Host Controller
[    0.741043] uhci_hcd 0000:00:1a.2: new USB bus registered, assigned bus number 5
[    0.741067] uhci_hcd 0000:00:1a.2: irq 19, io base 0x0000b800
[    0.741140] usb usb5: configuration #1 chosen from 1 choice
[    0.741163] hub 5-0:1.0: USB hub found
[    0.741168] hub 5-0:1.0: 2 ports detected
[    0.741243] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    0.741249] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    0.741253] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    0.741282] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 6
[    0.741308] uhci_hcd 0000:00:1d.0: irq 23, io base 0x0000b480
[    0.741376] usb usb6: configuration #1 chosen from 1 choice
[    0.741398] hub 6-0:1.0: USB hub found
[    0.741403] hub 6-0:1.0: 2 ports detected
[    0.741474] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    0.741480] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    0.741483] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    0.741510] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 7
[    0.741534] uhci_hcd 0000:00:1d.1: irq 19, io base 0x0000b400
[    0.741604] usb usb7: configuration #1 chosen from 1 choice
[    0.741627] hub 7-0:1.0: USB hub found
[    0.741636] hub 7-0:1.0: 2 ports detected
[    0.741706] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.741712] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    0.741715] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    0.741744] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 8
[    0.741769] uhci_hcd 0000:00:1d.2: irq 18, io base 0x0000b080
[    0.741869] usb usb8: configuration #1 chosen from 1 choice
[    0.741895] hub 8-0:1.0: USB hub found
[    0.741902] hub 8-0:1.0: 2 ports detected
[    0.741994] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f03:PS2M] at 0x60,0x64 irq 1,12
[    0.754173] i8042.c: Detected active multiplexing controller, rev 1.1.
[    0.755149] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.755154] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[    0.755188] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[    0.755191] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[    0.755193] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[    0.755240] mice: PS/2 mouse device common for all mice
[    0.755365] rtc_cmos 00:03: RTC can wake from S4
[    0.755397] rtc_cmos 00:03: rtc core: registered rtc_cmos as rtc0
[    0.755425] rtc0: alarms up to one month, y3k, 114 bytes nvram, hpet irqs
[    0.755536] device-mapper: uevent: version 1.0.3
[    0.755611] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: dm-devel@redhat.com
[    0.756419] device-mapper: multipath: version 1.1.0 loaded
[    0.756422] device-mapper: multipath round-robin: version 1.0.0 loaded
[    0.756603] cpuidle: using governor ladder
[    0.756682] cpuidle: using governor menu
[    0.757039] TCP cubic registered
[    0.757151] NET: Registered protocol family 10
[    0.757551] lo: Disabled Privacy Extensions
[    0.757815] NET: Registered protocol family 17
[    0.757835] Bluetooth: L2CAP ver 2.13
[    0.757837] Bluetooth: L2CAP socket layer initialized
[    0.757840] Bluetooth: SCO (Voice Link) ver 0.6
[    0.757842] Bluetooth: SCO socket layer initialized
[    0.757863] Bluetooth: RFCOMM TTY layer initialized
[    0.757866] Bluetooth: RFCOMM socket layer initialized
[    0.757868] Bluetooth: RFCOMM ver 1.11
[    0.758535] PM: Resume from disk failed.
[    0.758553] registered taskstats version 1
[    0.758684]   Magic number: 14:230:883
[    0.758778] rtc_cmos 00:03: setting system clock to 2010-02-10 11:52:51 UTC (1265802771)
[    0.758781] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.758782] EDD information not available.
[    0.956211] ACPI: Battery Slot [BAT0] (battery present)
[    1.000177] Clocksource tsc unstable (delta = -178053760 ns)
[    1.014628] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input4
[    1.040104] usb 1-4: new high speed USB device using ehci_hcd and address 2
[    1.190394] usb 1-4: config 1 interface 0 altsetting 0 endpoint 0x81 has an invalid bInterval 0, changing to 9
[    1.190398] usb 1-4: config 1 interface 0 altsetting 0 endpoint 0x2 has an invalid bInterval 0, changing to 9
[    1.190812] usb 1-4: configuration #1 chosen from 1 choice
[    1.200078] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    1.200259] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    1.220603] ata2.00: ATAPI: HL-DT-ST DVDRAM GSA-T50L, SR04, max UDMA/133
[    1.260306] ata2.00: configured for UDMA/133
[    1.293677] ata1.00: ATA-8: ST9320421AS, SD13, max UDMA/133
[    1.293681] ata1.00: 625142448 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    1.369058] ata1.00: configured for UDMA/133
[    1.369160] scsi 0:0:0:0: Direct-Access     ATA      ST9320421AS      SD13 PQ: 0 ANSI: 5
[    1.369259] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    1.369280] sd 0:0:0:0: [sda] 625142448 512-byte logical blocks: (320 GB/298 GiB)
[    1.369321] sd 0:0:0:0: [sda] Write Protect is off
[    1.369324] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.369345] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.369463]  sda:
[    1.371285] usb 2-5: new high speed USB device using ehci_hcd and address 3
[    1.377643] scsi 1:0:0:0: CD-ROM            HL-DT-ST DVDRAM GSA-T50L  SR04 PQ: 0 ANSI: 5
[    1.421670]  sda1 sda2 sda3 sda4
[    1.456253] sd 0:0:0:0: [sda] Attached SCSI disk
[    1.533851] usb 2-5: configuration #1 chosen from 1 choice
[    1.707858] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[    1.707861] Uniform CD-ROM driver Revision: 3.20
[    1.707928] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    1.707964] sr 1:0:0:0: Attached scsi generic sg1 type 5
[    1.708017] Freeing unused kernel memory: 660k freed
[    1.708200] Write protecting the kernel read-only data: 7584k
[    1.871978] ohci1394 0000:07:01.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.875181] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    1.875208] r8169 0000:06:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    1.875307] r8169 0000:06:00.0: setting latency timer to 64
[    1.875449]   alloc irq_desc for 29 on node 0
[    1.875451]   alloc kstat_irqs on node 0
[    1.875488] r8169 0000:06:00.0: irq 29 for MSI/MSI-X
[    1.876081] eth0: RTL8168c/8111c at 0xffffc90000674000, 00:23:54:84:2b:cd, XID 3c4000c0 IRQ 29
[    1.878627] usbcore: registered new interface driver hiddev
[    1.878668] usbcore: registered new interface driver usbhid
[    1.878671] usbhid: v2.6:USB HID core driver
[    1.885740] acpi device:1e: registered as cooling_device2
[    1.885868] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:19/device:1a/input/input5
[    1.885904] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[    1.932174] ohci1394: fw-host0: OHCI-1394 1.0 (PCI): IRQ=[16]  MMIO=[febff800-febfffff]  Max Packet=[2048]  IR/IT contexts=[4/4]
[    1.951288] usb 6-1: new low speed USB device using uhci_hcd and address 2
[    2.131436] usb 6-1: configuration #1 chosen from 1 choice
[    2.158611] input: Microsoft Compact Optical Mouse 500 as /devices/pci0000:00/0000:00:1d.0/usb6/6-1/6-1:1.0/input/input6
[    2.158681] generic-usb 0003:045E:0737.0001: input,hidraw0: USB HID v1.11 Mouse [Microsoft Compact Optical Mouse 500] on usb-0000:00:1d.0-1/input0
[    2.430091] usb 8-2: new full speed USB device using uhci_hcd and address 2
[    2.660075] usb 8-2: configuration #1 chosen from 1 choice
[    2.667549] Initializing USB Mass Storage driver...
[    2.680075] scsi4 : SCSI emulation for USB Mass Storage devices
[    2.690082] usbcore: registered new interface driver usb-storage
[    2.690085] USB Mass Storage support registered.
[    2.690176] usb-storage: device found at 2
[    2.690178] usb-storage: waiting for device to settle before scanning
[    3.291386] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[001e8c0001ab7f1a]
[    3.841644] PM: Starting manual resume from disk
[    3.841648] PM: Resume from partition 8:4
[    3.841649] PM: Checking hibernation image.
[    3.841966] PM: Resume from disk failed.
[    3.920712] EXT4-fs (sda3): barriers enabled
[    3.946583] kjournald2 starting: pid 437, dev sda3:8, commit interval 5 seconds
[    3.946593] EXT4-fs (sda3): delayed allocation enabled
[    3.946597] EXT4-fs: file extents enabled
[    3.951801] EXT4-fs: mballoc enabled
[    3.951813] EXT4-fs (sda3): mounted filesystem with ordered data mode
[    4.663762] type=1505 audit(1265802775.402:2): operation="profile_load" pid=460 name=/usr/share/gdm/guest-session/Xsession
[    4.666127] type=1505 audit(1265802775.402:3): operation="profile_load" pid=461 name=/sbin/dhclient3
[    4.666800] type=1505 audit(1265802775.402:4): operation="profile_load" pid=461 name=/usr/lib/NetworkManager/nm-dhcp-client.action
[    4.667165] type=1505 audit(1265802775.402:5): operation="profile_load" pid=461 name=/usr/lib/connman/scripts/dhclient-script
[    4.703050] type=1505 audit(1265802775.441:6): operation="profile_load" pid=462 name=/usr/bin/evince
[    4.713289] type=1505 audit(1265802775.451:7): operation="profile_load" pid=462 name=/usr/bin/evince-previewer
[    4.719453] type=1505 audit(1265802775.451:8): operation="profile_load" pid=462 name=/usr/bin/evince-thumbnailer
[    4.739864] type=1505 audit(1265802775.471:9): operation="profile_load" pid=464 name=/usr/lib/cups/backend/cups-pdf
[    5.700430] Adding 16940080k swap on /dev/sda4.  Priority:-1 extents:1 across:16940080k 
[    5.937177] EXT4-fs (sda3): internal journal on sda3:8
[    7.175133] udev: starting version 147
[    7.692864] usb-storage: device scan complete
[    7.695835] scsi 4:0:0:0: Direct-Access     Cricket  T-Flash Disk     2.31 PQ: 0 ANSI: 2
[    7.698841] scsi 4:0:0:1: CD-ROM            Cal-Comp CD INSTALLER     2.31 PQ: 0 ANSI: 0
[    7.699350] sd 4:0:0:0: Attached scsi generic sg2 type 0
[    8.068418] __ratelimit: 6 callbacks suppressed
[    8.068421] type=1505 audit(1265831578.801:12): operation="profile_replace" pid=795 name=/usr/share/gdm/guest-session/Xsession
[    8.069864] type=1505 audit(1265831578.801:13): operation="profile_replace" pid=796 name=/sbin/dhclient3
[    8.070594] type=1505 audit(1265831578.811:14): operation="profile_replace" pid=796 name=/usr/lib/NetworkManager/nm-dhcp-client.action
[    8.070961] type=1505 audit(1265831578.811:15): operation="profile_replace" pid=796 name=/usr/lib/connman/scripts/dhclient-script
[    8.074099] type=1505 audit(1265831578.811:16): operation="profile_replace" pid=797 name=/usr/bin/evince
[    8.084689] type=1505 audit(1265831578.821:17): operation="profile_replace" pid=797 name=/usr/bin/evince-previewer
[    8.090843] type=1505 audit(1265831578.831:18): operation="profile_replace" pid=797 name=/usr/bin/evince-thumbnailer
[    8.100199] type=1505 audit(1265831578.841:19): operation="profile_replace" pid=799 name=/usr/lib/cups/backend/cups-pdf
[    8.100989] type=1505 audit(1265831578.841:20): operation="profile_replace" pid=799 name=/usr/sbin/cupsd
[    8.103474] type=1505 audit(1265831578.841:21): operation="profile_replace" pid=800 name=/usr/sbin/tcpdump
[    9.339837] sr1: scsi3-mmc drive: 0x/0x caddy
[    9.339962] sr 4:0:0:1: Attached scsi CD-ROM sr1
[    9.340032] sr 4:0:0:1: Attached scsi generic sg3 type 5
[    9.353832] sd 4:0:0:0: [sdb] Attached SCSI removable disk
[    9.461834] sr1: CDROM (ioctl) error, command: Get configuration 46 00 00 00 00 00 00 00 20 00
[    9.461845] sr: Sense Key : Hardware Error [current] 
[    9.461848] sr: Add. Sense: No additional sense information
[    9.671829] sr1: CDROM (ioctl) error, command: Get configuration 46 00 00 00 00 00 00 00 20 00
[    9.671840] sr: Sense Key : Hardware Error [current] 
[    9.671843] sr: Add. Sense: No additional sense information
[   10.011809] nvidia: module license 'NVIDIA' taints kernel.
[   10.011813] Disabling lock debugging due to kernel taint
[   10.266337] nvidia 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   10.266359] nvidia 0000:01:00.0: setting latency timer to 64
[   10.266638] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  185.18.36  Fri Aug 14 17:35:21 PDT 2009
[   10.267379] r8169: eth0: link up
[   10.267387] r8169: eth0: link up
[   10.313455] ip_tables: (C) 2000-2006 Netfilter Core Team
[   10.631342] cfg80211: Calling CRDA to update world regulatory domain
[   10.766824] sr1: CDROM (ioctl) error, command: Get configuration 46 00 00 00 00 00 00 00 20 00
[   10.766835] sr: Sense Key : Hardware Error [current] 
[   10.766838] sr: Add. Sense: No additional sense information
[   11.186732] cfg80211: World regulatory domain updated:
[   11.186735] 	(start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   11.186738] 	(2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   11.186740] 	(2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   11.186743] 	(2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   11.186745] 	(5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   11.186747] 	(5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   11.954758]   alloc irq_desc for 22 on node 0
[   11.954762]   alloc kstat_irqs on node 0
[   11.954768] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[   11.954829] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   12.172825] sr1: CDROM (ioctl) error, command: Get configuration 46 00 00 00 00 00 00 00 20 00
[   12.172835] sr: Sense Key : Hardware Error [current] 
[   12.172839] sr: Add. Sense: No additional sense information
[   12.224087] input: HDA Digital PCBeep as /devices/pci0000:00/0000:00:1b.0/input/input7
[   14.135531] asus_oled: module is from the staging directory, the quality is unknown, you have been warned.
[   14.136577] asus-oled 1-4:1.0: Attached Asus OLED device: G50 [width 256, pack_mode 1]
[   14.136597] usbcore: registered new interface driver asus-oled
[   14.561023] ricoh-mmc: Ricoh MMC Controller disabling driver
[   14.561026] ricoh-mmc: Copyright(c) Philip Langdale
[   14.561149] ricoh-mmc: Ricoh MMC controller found at 0000:07:01.2 [1180:0843] (rev 12)
[   14.561165] ricoh-mmc: Controller is now disabled.
[   14.576657] lp: driver loaded but no devices found
[   14.591904] sdhci: Secure Digital Host Controller Interface driver
[   14.591907] sdhci: Copyright(c) Pierre Ossman
[   14.665823] sr1: CDROM (ioctl) error, command: Get configuration 46 00 00 00 00 00 00 00 20 00
[   14.665835] sr: Sense Key : Hardware Error [current] 
[   14.665838] sr: Add. Sense: No additional sense information
[   14.703850] Linux video capture interface: v2.00
[   14.712995] uvcvideo: Found UVC 1.00 device USB2.0 1.3M UVC WebCam  (04f2:b012)
[   14.716158] input: USB2.0 1.3M UVC WebCam  as /devices/pci0000:00/0000:00:1d.7/usb2/2-5/2-5:1.0/input/input8
[   14.716204] usbcore: registered new interface driver uvcvideo
[   14.716207] USB Video Class driver (v0.1.0)
[   15.011903] sdhci-pci 0000:07:01.1: SDHCI controller found [1180:0822] (rev 22)
[   15.011920] sdhci-pci 0000:07:01.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[   15.012982] sdhci-pci 0000:07:01.1: Will use DMA mode even though HW doesn't fully claim to support it.
[   15.014036] Registered led device: mmc0::
[   15.015070] mmc0: SDHCI controller on PCI [0000:07:01.1] using DMA
[   15.016545] asus_laptop: Asus Laptop Support version 0.42
[   15.022197] asus_laptop:   G50VT model detected
[   15.023041] input: Asus Laptop extra buttons as /devices/virtual/input/input9
[   15.024063] Registered led device: asus::touchpad
[   15.024093] asus_laptop: Brightness ignored, must be controlled by ACPI video driver
[   15.279517] Synaptics Touchpad, model: 1, fw: 6.5, id: 0x1c0b1, caps: 0xa04711/0xa00000
[   15.317700] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio4/input/input10
[   15.447836] sr1: CDROM (ioctl) error, command: Get configuration 46 00 00 00 00 00 00 00 20 00
[   15.447847] sr: Sense Key : Hardware Error [current] 
[   15.447850] sr: Add. Sense: No additional sense information
[   15.591299] usb 8-2: reset full speed USB device using uhci_hcd and address 2
[   15.870035] usb 8-2: reset full speed USB device using uhci_hcd and address 2
[   16.081069] iwlagn: Intel(R) Wireless WiFi Link AGN driver for Linux, 1.3.27k
[   16.081073] iwlagn: Copyright(c) 2003-2009 Intel Corporation
[   16.081664] iwlagn 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   16.081693] iwlagn 0000:03:00.0: setting latency timer to 64
[   16.081787] iwlagn 0000:03:00.0: Detected Intel Wireless WiFi Link 5100AGN REV=0x54
[   16.128576] iwlagn 0000:03:00.0: Tunable channels: 13 802.11bg, 24 802.11a channels
[   16.128640]   alloc irq_desc for 30 on node 0
[   16.128642]   alloc kstat_irqs on node 0
[   16.128663] iwlagn 0000:03:00.0: irq 30 for MSI/MSI-X
[   16.151294] usb 8-2: reset full speed USB device using uhci_hcd and address 2
[   16.196956] phy0: Selected rate control algorithm 'iwl-agn-rs'
[   16.461531] usb 8-2: reset full speed USB device using uhci_hcd and address 2
[   16.554687] iwlagn 0000:03:00.0: firmware: requesting iwlwifi-5000-2.ucode
[   16.614961] ppdev: user-space parallel port driver
[   16.638660] iwlagn 0000:03:00.0: loaded firmware version 8.24.2.12
[   16.796484] Registered led device: iwl-phy0::radio
[   16.796503] Registered led device: iwl-phy0::assoc
[   16.796519] Registered led device: iwl-phy0::RX
[   16.796538] Registered led device: iwl-phy0::TX
[   16.831030] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   16.880048] usb 8-2: reset full speed USB device using uhci_hcd and address 2
[   17.310036] usb 8-2: reset full speed USB device using uhci_hcd and address 2
[   19.011996] usplash:400 freeing invalid memtype fffffffffb000000-fffffffffbe00000
[   21.171345] eth0: no IPv6 routers present
[   27.315906] CPU0 attaching NULL sched-domain.
[   27.315911] CPU1 attaching NULL sched-domain.
[   27.361343] CPU0 attaching sched-domain:
[   27.361347]  domain 0: span 0-1 level MC
[   27.361350]   groups: 0 1
[   27.361355] CPU1 attaching sched-domain:
[   27.361357]  domain 0: span 0-1 level MC
[   27.361359]   groups: 1 0
[   32.018529] CPU0 attaching NULL sched-domain.
[   32.018534] CPU1 attaching NULL sched-domain.
[   32.060125] CPU0 attaching sched-domain:
[   32.060128]  domain 0: span 0-1 level MC
[   32.060131]   groups: 0 1
[   32.060136] CPU1 attaching sched-domain:
[   32.060138]  domain 0: span 0-1 level MC
[   32.060140]   groups: 1 0
[   41.945123] wlan0: authenticate with AP 00:30:ab:24:5b:87
[   41.947319] wlan0: authenticated
[   41.947322] wlan0: associate with AP 00:30:ab:24:5b:87
[   41.950429] wlan0: RX AssocResp from 00:30:ab:24:5b:87 (capab=0x1 status=0 aid=1)
[   41.950432] wlan0: associated
[   41.961537] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   45.202833] sr1: CDROM (ioctl) error, command: Get configuration 46 00 00 00 00 00 00 00 20 00
[   45.202843] sr: Sense Key : Hardware Error [current] 
[   45.202847] sr: Add. Sense: No additional sense information
[   45.238854] sr1: CDROM (ioctl) error, command: Get configuration 46 00 00 28 00 00 00 00 10 00
[   45.238864] sr: Sense Key : Hardware Error [current] 
[   45.238868] sr: Add. Sense: No additional sense information
[   45.286086] sr1: CDROM (ioctl) error, command: Get configuration 46 00 00 20 00 00 00 00 18 00
[   45.286098] sr: Sense Key : Hardware Error [current] 
[   45.286102] sr: Add. Sense: No additional sense information
[   45.418867] sr1: CDROM (ioctl) error, command: Get configuration 46 00 00 00 00 00 00 00 20 00
[   45.418879] sr: Sense Key : Hardware Error [current] 
[   45.418882] sr: Add. Sense: No additional sense information
[   52.291322] wlan0: no IPv6 routers present
[   66.792710] wlan0: disassociating by local choice (reason=3)
[  129.298358] scsi 4:0:0:1: rejecting I/O to offline device
[  129.319717] scsi 4:0:0:1: rejecting I/O to dead device
[  129.790191] usb 8-2: USB disconnect, address 2
[  135.061312] usb 8-2: new full speed USB device using uhci_hcd and address 3
[  135.225338] usb 8-2: configuration #1 chosen from 1 choice
[  135.250234] scsi5 : SCSI emulation for USB Mass Storage devices
[  135.250849] usb-storage: device found at 3
[  135.250851] usb-storage: waiting for device to settle before scanning
[  135.255798] cdc_acm 8-2:1.0: ttyACM0: USB ACM device
[  135.257222] usbcore: registered new interface driver cdc_acm
[  135.257225] cdc_acm: v0.26:USB Abstract Control Model driver for USB modems and ISDN adapters
[  140.242269] usb-storage: device scan complete
[  140.245217] scsi 5:0:0:0: Direct-Access     Cricket  T-Flash Disk     2.31 PQ: 0 ANSI: 2
[  140.246371] sd 5:0:0:0: Attached scsi generic sg2 type 0
[  140.263215] sd 5:0:0:0: [sdb] Attached SCSI removable disk
[  145.620135] usb 8-2: reset full speed USB device using uhci_hcd and address 3
[  145.772251] cdc_acm 8-2:1.0: ttyACM0: USB ACM device
[  195.281112] PPP BSD Compression module registered
[  195.288933] PPP Deflate Compression module registered
[  615.081351] CE: hpet increasing min_delta_ns to 15000 nsec
[ 2282.261367] CE: hpet increasing min_delta_ns to 22500 nsec

```
grep for 'error' shows several hits for a problem with the cd-rom, yet it appears to work properly.

Like I said, I'm confident that it is a user rights issue, and to me it appears that the problem rises after dmesg thinks we're done booting. Any direction that could be given would be greatly appreciated.

---

### Post by BentFX on 2010-02-11
[sarcasm]Gee Fellas, and ladies, thanks for all the help![/sarcasm] :)

I'm Sorry!

I'll mark this solved... The CPU throttling IS dropping back to lower settings, it just takes about minute after activity for it to settle down. I'm sorry I hadn't given it a decent test before posting.

The dual mode usb stick modem is a relatively young device. The OS support is new to 9.10. As it matures I'm sure it will also settle down. I CAN control it manually.

Again... It's my bad :)
Thnx

---

