---
title: "Slow boot (Ubuntu 10.04)"
date: 2010-05-06
forum: General Help
---

### Post by josedb on 2010-05-06
The process is slow now after severals updates.

here is bootchart image:

[IMG]http://img20.imageshack.us/img20/6819/joselaptoplucid20100506.png[/IMG]

---

### Post by josedb on 2010-05-06
dmesg:

```
jose@jose-laptop:~$ dmesg 
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.32-22-generic (buildd@yellow) (gcc version 4.4.3 (Ubuntu 4.4.3-4ubuntu5) ) #33-Ubuntu SMP Wed Apr 28 13:28:05 UTC 2010 (Ubuntu 2.6.32-22.33-generic 2.6.32.11+drm33.2)
[    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-2.6.32-22-generic root=UUID=349c2860-f26f-46a0-b71c-d34cb5265072 ro quiet splash fastboot
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   Centaur CentaurHauls
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009dc00 (usable)
[    0.000000]  BIOS-e820: 000000000009dc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000d0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 00000000b7ec0000 (usable)
[    0.000000]  BIOS-e820: 00000000b7ec0000 - 00000000b7ed8000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000b7ed8000 - 00000000b7eda000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000b7eda000 - 00000000c8000000 (reserved)
[    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fff00000 - 0000000100000000 (reserved)
[    0.000000]  BIOS-e820: 0000000100000000 - 0000000138000000 (usable)
[    0.000000] DMI present.
[    0.000000] Phoenix BIOS detected: BIOS may corrupt low RAM, working around it.
[    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
[    0.000000] last_pfn = 0x138000 max_arch_pfn = 0x400000000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-CFFFF write-protect
[    0.000000]   D0000-DFFFF uncachable
[    0.000000]   E0000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000000 mask FFFF80000000 write-back
[    0.000000]   1 base 000080000000 mask FFFFE0000000 write-back
[    0.000000]   2 base 0000A0000000 mask FFFFF0000000 write-back
[    0.000000]   3 base 0000B0000000 mask FFFFF8000000 write-back
[    0.000000]   4 base 0000B8000000 mask FFFFFC000000 write-back
[    0.000000]   5 base 0000BC000000 mask FFFFFE000000 write-back
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] TOM2: 0000000138000000 aka 4992M
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] e820 update range: 00000000be000000 - 0000000100000000 (usable) ==> (reserved)
[    0.000000] last_pfn = 0xb7ec0 max_arch_pfn = 0x400000000
[    0.000000] Scanning 0 areas for low memory corruption
[    0.000000] modified physical RAM map:
[    0.000000]  modified: 0000000000000000 - 0000000000010000 (reserved)
[    0.000000]  modified: 0000000000010000 - 000000000009dc00 (usable)
[    0.000000]  modified: 000000000009dc00 - 00000000000a0000 (reserved)
[    0.000000]  modified: 00000000000d0000 - 0000000000100000 (reserved)
[    0.000000]  modified: 0000000000100000 - 00000000b7ec0000 (usable)
[    0.000000]  modified: 00000000b7ec0000 - 00000000b7ed8000 (ACPI data)
[    0.000000]  modified: 00000000b7ed8000 - 00000000b7eda000 (ACPI NVS)
[    0.000000]  modified: 00000000b7eda000 - 00000000c8000000 (reserved)
[    0.000000]  modified: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  modified: 00000000fec00000 - 00000000fec10000 (reserved)
[    0.000000]  modified: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  modified: 00000000fff00000 - 0000000100000000 (reserved)
[    0.000000]  modified: 0000000100000000 - 0000000138000000 (usable)
[    0.000000] initial memory mapped : 0 - 20000000
[    0.000000] Using GB pages for direct mapping
[    0.000000] init_memory_mapping: 0000000000000000-00000000b7ec0000
[    0.000000] NX (Execute Disable) protection: active
[    0.000000]  0000000000 - 0080000000 page 1G
[    0.000000]  0080000000 - 00b7e00000 page 2M
[    0.000000]  00b7e00000 - 00b7ec0000 page 4k
[    0.000000] kernel direct mapping tables up to b7ec0000 @ 10000-13000
[    0.000000] init_memory_mapping: 0000000100000000-0000000138000000
[    0.000000] NX (Execute Disable) protection: active
[    0.000000]  0100000000 - 0138000000 page 2M
[    0.000000] kernel direct mapping tables up to 138000000 @ 12000-14000
[    0.000000] RAMDISK: 377fd000 - 37fef75c
[    0.000000] ACPI: RSDP 00000000000f8030 00024 (v02 PTLTD )
[    0.000000] ACPI: XSDT 00000000b7ecb242 00054 (v01 ACRSYS ACRPRDCT 06040000 INNA 00000000)
[    0.000000] ACPI: FACP 00000000b7ed7726 000F4 (v03 AMD    ANT      06040000 ATI  000F4240)
[    0.000000] ACPI: DSDT 00000000b7ecb296 0C490 (v01    ATI    SB700 06040000 MSFT 03000001)
[    0.000000] ACPI: FACS 00000000b7ed9fc0 00040
[    0.000000] ACPI: SLIC 00000000b7ed788e 00176 (v01 ACRSYS ACRPRDCT 06040000 ANNI 00000001)
[    0.000000] ACPI: SSDT 00000000b7ed7a04 0052A (v01 AMD    POWERNOW 06040000 AMD  00000001)
[    0.000000] ACPI: APIC 00000000b7ed7f2e 0005E (v01 PTLTD  ? APIC   06040000  LTP 00000000)
[    0.000000] ACPI: MCFG 00000000b7ed7f8c 0003C (v01 PTLTD    MCFG   06040000  LTP 00000000)
[    0.000000] ACPI: HPET 00000000b7ed7fc8 00038 (v01 PTLTD  HPETTBL  06040000  LTP 00000001)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] Scanning NUMA topology in Northbridge 24
[    0.000000] No NUMA configuration found
[    0.000000] Faking a node at 0000000000000000-0000000138000000
[    0.000000] Bootmem setup node 0 0000000000000000-0000000138000000
[    0.000000]   NODE_DATA [0000000000013000 - 0000000000017fff]
[    0.000000]   bootmap [0000000000018000 -  000000000003efff] pages 27
[    0.000000] (8 early reservations) ==> bootmem [0000000000 - 0138000000]
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
[    0.000000]   #1 [0000006000 - 0000008000]       TRAMPOLINE ==> [0000006000 - 0000008000]
[    0.000000]   #2 [0001000000 - 0001a29e64]    TEXT DATA BSS ==> [0001000000 - 0001a29e64]
[    0.000000]   #3 [00377fd000 - 0037fef75c]          RAMDISK ==> [00377fd000 - 0037fef75c]
[    0.000000]   #4 [000009dc00 - 0000100000]    BIOS reserved ==> [000009dc00 - 0000100000]
[    0.000000]   #5 [0001a2a000 - 0001a2a1dc]              BRK ==> [0001a2a000 - 0001a2a1dc]
[    0.000000]   #6 [0000010000 - 0000012000]          PGTABLE ==> [0000010000 - 0000012000]
[    0.000000]   #7 [0000012000 - 0000013000]          PGTABLE ==> [0000012000 - 0000013000]
[    0.000000] found SMP MP-table at [ffff8800000f8170] f8170
[    0.000000]  [ffffea0000000000-ffffea00045fffff] PMD -> [ffff880028600000-ffff88002bdfffff] on node 0
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000010 -> 0x00001000
[    0.000000]   DMA32    0x00001000 -> 0x00100000
[    0.000000]   Normal   0x00100000 -> 0x00138000
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[3] active PFN ranges
[    0.000000]     0: 0x00000010 -> 0x0000009d
[    0.000000]     0: 0x00000100 -> 0x000b7ec0
[    0.000000]     0: 0x00100000 -> 0x00138000
[    0.000000] On node 0 totalpages: 982605
[    0.000000]   DMA zone: 56 pages used for memmap
[    0.000000]   DMA zone: 104 pages reserved
[    0.000000]   DMA zone: 3821 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 14280 pages used for memmap
[    0.000000]   DMA32 zone: 734968 pages, LIFO batch:31
[    0.000000]   Normal zone: 3136 pages used for memmap
[    0.000000]   Normal zone: 226240 pages, LIFO batch:31
[    0.000000] ACPI: PM-Timer IO Port: 0x8008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 33, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 low level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x43538301 base: 0xfed00000
[    0.000000] SMP: Allowing 2 CPUs, 0 hotplug CPUs
[    0.000000] nr_irqs_gsi: 24
[    0.000000] PM: Registered nosave memory: 000000000009d000 - 000000000009e000
[    0.000000] PM: Registered nosave memory: 000000000009e000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000d0000
[    0.000000] PM: Registered nosave memory: 00000000000d0000 - 0000000000100000
[    0.000000] PM: Registered nosave memory: 00000000b7ec0000 - 00000000b7ed8000
[    0.000000] PM: Registered nosave memory: 00000000b7ed8000 - 00000000b7eda000
[    0.000000] PM: Registered nosave memory: 00000000b7eda000 - 00000000c8000000
[    0.000000] PM: Registered nosave memory: 00000000c8000000 - 00000000e0000000
[    0.000000] PM: Registered nosave memory: 00000000e0000000 - 00000000f0000000
[    0.000000] PM: Registered nosave memory: 00000000f0000000 - 00000000fec00000
[    0.000000] PM: Registered nosave memory: 00000000fec00000 - 00000000fec10000
[    0.000000] PM: Registered nosave memory: 00000000fec10000 - 00000000fee00000
[    0.000000] PM: Registered nosave memory: 00000000fee00000 - 00000000fee01000
[    0.000000] PM: Registered nosave memory: 00000000fee01000 - 00000000fff00000
[    0.000000] PM: Registered nosave memory: 00000000fff00000 - 0000000100000000
[    0.000000] Allocating PCI resources starting at c8000000 (gap: c8000000:18000000)
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] NR_CPUS:64 nr_cpumask_bits:64 nr_cpu_ids:2 nr_node_ids:1
[    0.000000] PERCPU: Embedded 30 pages/cpu @ffff880028200000 s91544 r8192 d23144 u1048576
[    0.000000] pcpu-alloc: s91544 r8192 d23144 u1048576 alloc=1*2097152
[    0.000000] pcpu-alloc: [0] 0 1 
[    0.000000] Built 1 zonelists in Node order, mobility grouping on.  Total pages: 965029
[    0.000000] Policy zone: Normal
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.32-22-generic root=UUID=349c2860-f26f-46a0-b71c-d34cb5265072 ro quiet splash fastboot
[    0.000000] PID hash table entries: 4096 (order: 3, 32768 bytes)
[    0.000000] Initializing CPU#0
[    0.000000] Checking aperture...
[    0.000000] No AGP bridge found
[    0.000000] Node 0: aperture @ 3ffe000000 size 32 MB
[    0.000000] Aperture beyond 4GB. Ignoring.
[    0.000000] Your BIOS doesn't leave a aperture memory hole
[    0.000000] Please enable the IOMMU option in the BIOS setup
[    0.000000] This costs you 64 MB of RAM
[    0.000000] Mapping aperture over 65536 KB of RAM @ 20000000
[    0.000000] PM: Registered nosave memory: 0000000020000000 - 0000000024000000
[    0.000000] Memory: 3788504k/5111808k available (5409k kernel code, 1181388k absent, 141916k reserved, 2976k data, 876k init)
[    0.000000] SLUB: Genslabs=14, HWalign=64, Order=0-3, MinObjects=0, CPUs=2, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000] NR_IRQS:4352 nr_irqs:424
[    0.000000] spurious 8259A interrupt: IRQ7.
[    0.000000] Console: colour VGA+ 80x25
[    0.000000] console [tty0] enabled
[    0.000000] allocated 39321600 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] hpet clockevent registered
[    0.000000]   alloc irq_desc for 24 on node 0
[    0.000000]   alloc kstat_irqs on node 0
[    0.000000] HPET: 4 timers in total, 1 timers will be used for per-cpu timer
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 2194.540 MHz processor.
[    0.030006] Calibrating delay loop (skipped), value calculated using timer frequency.. 4389.07 BogoMIPS (lpj=21945370)
[    0.030026] Security Framework initialized
[    0.030038] AppArmor: AppArmor initialized
[    0.030348] Dentry cache hash table entries: 524288 (order: 10, 4194304 bytes)
[    0.031828] Inode-cache hash table entries: 262144 (order: 9, 2097152 bytes)
[    0.032503] Mount-cache hash table entries: 256
[    0.032622] Initializing cgroup subsys ns
[    0.032627] Initializing cgroup subsys cpuacct
[    0.032630] Initializing cgroup subsys memory
[    0.032638] Initializing cgroup subsys devices
[    0.032640] Initializing cgroup subsys freezer
[    0.032643] Initializing cgroup subsys net_cls
[    0.032661] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[    0.032663] CPU: L2 Cache: 512K (64 bytes/line)
[    0.032666] CPU 0/0x0 -> Node 0
[    0.032669] tseg: 00b7f00000
[    0.032671] CPU: Physical Processor ID: 0
[    0.032672] CPU: Processor Core ID: 0
[    0.032675] mce: CPU supports 6 MCE banks
[    0.032685] using C1E aware idle routine
[    0.032687] Performance Events: AMD PMU driver.
[    0.032691] ... version:                0
[    0.032693] ... bit width:              48
[    0.032694] ... generic registers:      4
[    0.032696] ... value mask:             0000ffffffffffff
[    0.032698] ... max period:             00007fffffffffff
[    0.032700] ... fixed-purpose events:   0
[    0.032701] ... event mask:             000000000000000f
[    0.040933] ACPI: Core revision 20090903
[    0.060025] ftrace: converting mcount calls to 0f 1f 44 00 00
[    0.060034] ftrace: allocating 22518 entries in 89 pages
[    0.070118] Setting APIC routing to flat
[    0.070455] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.171765] CPU0: AMD Turion(tm) II Dual-Core Mobile M500 stepping 02
[    0.180000] Booting processor 1 APIC 0x1 ip 0x6000
[    0.040000] Initializing CPU#1
[    0.040000] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[    0.040000] CPU: L2 Cache: 512K (64 bytes/line)
[    0.040000] CPU 1/0x1 -> Node 0
[    0.040000] CPU: Physical Processor ID: 0
[    0.040000] CPU: Processor Core ID: 1
[    0.330070] CPU1: AMD Turion(tm) II Dual-Core Mobile M500 stepping 02
[    0.330110] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
[    0.340011] Brought up 2 CPUs
[    0.340014] Total of 2 processors activated (8778.09 BogoMIPS).
[    0.340020] System has AMD C1E enabled
[    0.340044] Switch to broadcast mode on CPU1
[    0.340194] CPU0 attaching sched-domain:
[    0.340197]  domain 0: span 0-1 level MC
[    0.340199]   groups: 0 1
[    0.340204] CPU1 attaching sched-domain:
[    0.340206]  domain 0: span 0-1 level MC
[    0.340207]   groups: 1 0
[    0.340283] Switch to broadcast mode on CPU0
[    0.340283] devtmpfs: initialized
[    0.340283] regulator: core version 0.5
[    0.340283] Time: 13:12:14  Date: 05/06/10
[    0.340283] NET: Registered protocol family 16
[    0.340283] node 0 link 0: io port [1000, ffff]
[    0.340283] TOM: 00000000c8000000 aka 3200M
[    0.340283] Fam 10h mmconf [e0000000, efffffff]
[    0.340283] node 0 link 0: mmio [a0000, bffff]
[    0.340283] node 0 link 0: mmio [c8000000, cfcfffff]
[    0.340283] Trying to unpack rootfs image as initramfs...
[    0.340283] node 0 link 0: mmio [cfd00000, cfefffff]
[    0.340283] node 0 link 0: mmio [cff00000, cfffffff]
[    0.340283] node 0 link 0: mmio [d0000000, efffffff] ==> [d0000000, dfffffff]
[    0.340283] node 0 link 0: mmio [f0000000, ffffffff]
[    0.340283] TOM2: 0000000138000000 aka 4992M
[    0.340283] bus: [00,ff] on node 0 link 0
[    0.340283] bus: 00 index 0 io port: [0, ffff]
[    0.340283] bus: 00 index 1 mmio: [a0000, bffff]
[    0.340283] bus: 00 index 2 mmio: [c8000000, dfffffff]
[    0.340283] bus: 00 index 3 mmio: [f0000000, ffffffff]
[    0.340283] bus: 00 index 4 mmio: [138000000, fcffffffff]
[    0.340283] ACPI FADT declares the system doesn't support PCIe ASPM, so disable it
[    0.340283] ACPI: bus type pci registered
[    0.340355] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 9
[    0.340357] PCI: MCFG area at e0000000 reserved in E820
[    0.340660] PCI: Using MMCONFIG at e0000000 - e09fffff
[    0.340662] PCI: Using configuration type 1 for base access
[    0.350167] bio: create slab <bio-0> at 0
[    0.351066] ACPI: EC: Look up EC in DSDT
[    0.355931] ACPI: BIOS _OSI(Linux) query ignored
[    0.356661] ACPI: OEMN 00000000b7ed8c69 00173 (v01 AMD    NAHP     00000001 MSFT 03000001)
[    0.360110] ACPI: Interpreter enabled
[    0.360110] ACPI: (supports S0 S3 S4 S5)
[    0.360110] ACPI: Using IOAPIC for interrupt routing
[    0.380063] ACPI: EC: GPE = 0x3, I/O: command/status = 0x66, data = 0x62
[    0.380257] ACPI: No dock devices found.
[    0.381867] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.382028] pci 0000:00:04.0: PME# supported from D0 D3hot D3cold
[    0.382032] pci 0000:00:04.0: PME# disabled
[    0.382066] pci 0000:00:06.0: PME# supported from D0 D3hot D3cold
[    0.382069] pci 0000:00:06.0: PME# disabled
[    0.382122] pci 0000:00:11.0: reg 10 io port: [0x8420-0x8427]
[    0.382129] pci 0000:00:11.0: reg 14 io port: [0x8414-0x8417]
[    0.382136] pci 0000:00:11.0: reg 18 io port: [0x8418-0x841f]
[    0.382142] pci 0000:00:11.0: reg 1c io port: [0x8410-0x8413]
[    0.382149] pci 0000:00:11.0: reg 20 io port: [0x8400-0x840f]
[    0.382156] pci 0000:00:11.0: reg 24 32bit mmio: [0xf0208000-0xf02083ff]
[    0.382208] pci 0000:00:12.0: reg 10 32bit mmio: [0xf0004000-0xf0004fff]
[    0.382261] pci 0000:00:12.1: reg 10 32bit mmio: [0xf0005000-0xf0005fff]
[    0.382331] pci 0000:00:12.2: reg 10 32bit mmio: [0xf0208400-0xf02084ff]
[    0.382382] pci 0000:00:12.2: supports D1 D2
[    0.382384] pci 0000:00:12.2: PME# supported from D0 D1 D2 D3hot
[    0.382388] pci 0000:00:12.2: PME# disabled
[    0.382419] pci 0000:00:13.0: reg 10 32bit mmio: [0xf0006000-0xf0006fff]
[    0.382474] pci 0000:00:13.1: reg 10 32bit mmio: [0xf0007000-0xf0007fff]
[    0.382544] pci 0000:00:13.2: reg 10 32bit mmio: [0xf0208800-0xf02088ff]
[    0.382595] pci 0000:00:13.2: supports D1 D2
[    0.382597] pci 0000:00:13.2: PME# supported from D0 D1 D2 D3hot
[    0.382601] pci 0000:00:13.2: PME# disabled
[    0.382721] pci 0000:00:14.2: reg 10 64bit mmio: [0xf0000000-0xf0003fff]
[    0.382763] pci 0000:00:14.2: PME# supported from D0 D3hot D3cold
[    0.382767] pci 0000:00:14.2: PME# disabled
[    0.382989] pci 0000:01:05.0: reg 10 32bit mmio pref: [0xd0000000-0xdfffffff]
[    0.382993] pci 0000:01:05.0: reg 14 io port: [0x9000-0x90ff]
[    0.382997] pci 0000:01:05.0: reg 18 32bit mmio: [0xcfdf0000-0xcfdfffff]
[    0.383004] pci 0000:01:05.0: reg 24 32bit mmio: [0xcfe00000-0xcfefffff]
[    0.383015] pci 0000:01:05.0: supports D1 D2
[    0.383032] pci 0000:01:05.1: reg 10 32bit mmio: [0xcfdec000-0xcfdeffff]
[    0.383051] pci 0000:01:05.1: supports D1 D2
[    0.383124] pci 0000:00:01.0: bridge io port: [0x9000-0x9fff]
[    0.383127] pci 0000:00:01.0: bridge 32bit mmio: [0xcfd00000-0xcfefffff]
[    0.383131] pci 0000:00:01.0: bridge 64bit mmio pref: [0xd0000000-0xdfffffff]
[    0.383181] pci 0000:03:00.0: reg 10 64bit mmio: [0xf0300000-0xf030ffff]
[    0.383239] pci 0000:03:00.0: PME# supported from D3hot D3cold
[    0.383243] pci 0000:03:00.0: PME# disabled
[    0.383333] pci 0000:00:04.0: bridge 32bit mmio: [0xf0300000-0xf03fffff]
[    0.383372] pci 0000:09:00.0: reg 10 64bit mmio: [0xf0400000-0xf040ffff]
[    0.383419] pci 0000:09:00.0: supports D1
[    0.383421] pci 0000:09:00.0: PME# supported from D0 D1 D3hot
[    0.383424] pci 0000:09:00.0: PME# disabled
[    0.383516] pci 0000:00:06.0: bridge 32bit mmio: [0xf0400000-0xf04fffff]
[    0.383574] pci 0000:00:14.4: transparent bridge
[    0.383595] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.383789] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PB4_._PRT]
[    0.383860] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PB6_._PRT]
[    0.383961] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P2P_._PRT]
[    0.384088] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.AGP_._PRT]
[    0.388167] ACPI: PCI Interrupt Link [LNKA] (IRQs 10 11) *0, disabled.
[    0.388318] ACPI: PCI Interrupt Link [LNKB] (IRQs 10 11) *0, disabled.
[    0.388467] ACPI: PCI Interrupt Link [LNKC] (IRQs 10 11) *0, disabled.
[    0.388615] ACPI: PCI Interrupt Link [LNKD] (IRQs 10 11) *0, disabled.
[    0.388763] ACPI: PCI Interrupt Link [LNKE] (IRQs 10 11) *0, disabled.
[    0.388911] ACPI: PCI Interrupt Link [LNKF] (IRQs 10 11) *0, disabled.
[    0.389059] ACPI: PCI Interrupt Link [LNKG] (IRQs 10 11) *0, disabled.
[    0.389206] ACPI: PCI Interrupt Link [LNKH] (IRQs 10 11) *0, disabled.
[    0.389323] vgaarb: device added: PCI:0000:01:05.0,decodes=io+mem,owns=io+mem,locks=none
[    0.389326] vgaarb: loaded
[    0.389422] SCSI subsystem initialized
[    0.389515] libata version 3.00 loaded.
[    0.389570] usbcore: registered new interface driver usbfs
[    0.389580] usbcore: registered new interface driver hub
[    0.389600] usbcore: registered new device driver usb
[    0.389754] ACPI: WMI: Mapper loaded
[    0.389756] PCI: Using ACPI for IRQ routing
[    0.389931] NetLabel: Initializing
[    0.389933] NetLabel:  domain hash size = 128
[    0.389934] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.389946] NetLabel:  unlabeled traffic allowed by default
[    0.390013] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 24, 0
[    0.390018] hpet0: 4 comparators, 32-bit 14.318180 MHz counter
[    0.392028] Switching to clocksource tsc
[    0.392229] AppArmor: AppArmor Filesystem Enabled
[    0.392229] pnp: PnP ACPI init
[    0.392229] ACPI: bus type pnp registered
[    0.396688] pnp: PnP ACPI: found 11 devices
[    0.396691] ACPI: ACPI bus type pnp unregistered
[    0.396705] system 00:01: ioport range 0xf50-0xf51 has been reserved
[    0.396710] system 00:01: iomem range 0xfec00000-0xfec00fff could not be reserved
[    0.396713] system 00:01: iomem range 0xfee00000-0xfee00fff has been reserved
[    0.396720] system 00:06: ioport range 0x220-0x22f has been reserved
[    0.396723] system 00:06: ioport range 0x40b-0x40b has been reserved
[    0.396725] system 00:06: ioport range 0x4d0-0x4d1 has been reserved
[    0.396727] system 00:06: ioport range 0x4d6-0x4d6 has been reserved
[    0.396730] system 00:06: ioport range 0x530-0x537 has been reserved
[    0.396732] system 00:06: ioport range 0xc00-0xc01 has been reserved
[    0.396734] system 00:06: ioport range 0xc14-0xc14 has been reserved
[    0.396737] system 00:06: ioport range 0xc50-0xc52 has been reserved
[    0.396739] system 00:06: ioport range 0xc6c-0xc6c has been reserved
[    0.396741] system 00:06: ioport range 0xc6f-0xc6f has been reserved
[    0.396743] system 00:06: ioport range 0xcd0-0xcd1 has been reserved
[    0.396746] system 00:06: ioport range 0xcd2-0xcd3 has been reserved
[    0.396748] system 00:06: ioport range 0xcd4-0xcd5 has been reserved
[    0.396750] system 00:06: ioport range 0xcd6-0xcd7 has been reserved
[    0.396753] system 00:06: ioport range 0xcd8-0xcdf has been reserved
[    0.396755] system 00:06: ioport range 0x8000-0x805f has been reserved
[    0.396758] system 00:06: ioport range 0xf40-0xf47 has been reserved
[    0.396760] system 00:06: ioport range 0x87f-0x87f has been reserved
[    0.396763] system 00:06: iomem range 0xff800000-0xffefffff has been reserved
[    0.396765] system 00:06: iomem range 0xfec10000-0xfec1001f has been reserved
[    0.396771] system 00:07: iomem range 0xe0000-0xfffff could not be reserved
[    0.396774] system 00:07: iomem range 0xffe00000-0xffffffff could not be reserved
[    0.396776] system 00:07: iomem range 0xfec10000-0xfec1001f has been reserved
[    0.401821] pci 0000:00:01.0: PCI bridge, secondary bus 0000:01
[    0.401824] pci 0000:00:01.0:   IO window: 0x9000-0x9fff
[    0.401827] pci 0000:00:01.0:   MEM window: 0xcfd00000-0xcfefffff
[    0.401830] pci 0000:00:01.0:   PREFETCH window: 0x000000d0000000-0x000000dfffffff
[    0.401834] pci 0000:00:04.0: PCI bridge, secondary bus 0000:03
[    0.401835] pci 0000:00:04.0:   IO window: disabled
[    0.401838] pci 0000:00:04.0:   MEM window: 0xf0300000-0xf03fffff
[    0.401841] pci 0000:00:04.0:   PREFETCH window: disabled
[    0.401844] pci 0000:00:06.0: PCI bridge, secondary bus 0000:09
[    0.401846] pci 0000:00:06.0:   IO window: disabled
[    0.401849] pci 0000:00:06.0:   MEM window: 0xf0400000-0xf04fffff
[    0.401851] pci 0000:00:06.0:   PREFETCH window: disabled
[    0.401854] pci 0000:00:14.4: PCI bridge, secondary bus 0000:0a
[    0.401856] pci 0000:00:14.4:   IO window: disabled
[    0.401901] pci 0000:00:14.4:   MEM window: disabled
[    0.401905] pci 0000:00:14.4:   PREFETCH window: disabled
[    0.401920]   alloc irq_desc for 16 on node 0
[    0.401922]   alloc kstat_irqs on node 0
[    0.401927] pci 0000:00:04.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.401930] pci 0000:00:04.0: setting latency timer to 64
[    0.401934]   alloc irq_desc for 18 on node 0
[    0.401935]   alloc kstat_irqs on node 0
[    0.401938] pci 0000:00:06.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    0.401941] pci 0000:00:06.0: setting latency timer to 64
[    0.401949] pci_bus 0000:00: resource 0 io:  [0x00-0xffff]
[    0.401951] pci_bus 0000:00: resource 1 mem: [0x000000-0xffffffffffffffff]
[    0.401954] pci_bus 0000:01: resource 0 io:  [0x9000-0x9fff]
[    0.401956] pci_bus 0000:01: resource 1 mem: [0xcfd00000-0xcfefffff]
[    0.401958] pci_bus 0000:01: resource 2 pref mem [0xd0000000-0xdfffffff]
[    0.401961] pci_bus 0000:03: resource 1 mem: [0xf0300000-0xf03fffff]
[    0.401963] pci_bus 0000:09: resource 1 mem: [0xf0400000-0xf04fffff]
[    0.401965] pci_bus 0000:0a: resource 3 io:  [0x00-0xffff]
[    0.401968] pci_bus 0000:0a: resource 4 mem: [0x000000-0xffffffffffffffff]
[    0.402005] NET: Registered protocol family 2
[    0.402160] IP route cache hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.403241] TCP established hash table entries: 524288 (order: 11, 8388608 bytes)
[    0.406298] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[    0.406672] TCP: Hash tables configured (established 524288 bind 65536)
[    0.406675] TCP reno registered
[    0.406758] NET: Registered protocol family 1
[    0.406913] pci 0000:01:05.0: Boot video device
[    0.407096] PCI-DMA: Disabling AGP.
[    0.407175] PCI-DMA: aperture base @ 20000000 size 65536 KB
[    0.407177] PCI-DMA: using GART IOMMU.
[    0.407180] PCI-DMA: Reserving 64MB of IOMMU area in the AGP aperture
[    0.408686] Scanning for low memory corruption every 60 seconds
[    0.408804] audit: initializing netlink socket (disabled)
[    0.408816] type=2000 audit(1273151533.407:1): initialized
[    0.428297] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    0.429428] VFS: Disk quotas dquot_6.5.2
[    0.429476] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    0.430003] fuse init (API version 7.13)
[    0.430075] msgmni has been set to 7399
[    0.430263] alg: No test for stdrng (krng)
[    0.430312] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.430315] io scheduler noop registered
[    0.430317] io scheduler anticipatory registered
[    0.430319] io scheduler deadline registered
[    0.430351] io scheduler cfq registered (default)
[    0.430510]   alloc irq_desc for 25 on node 0
[    0.430513]   alloc kstat_irqs on node 0
[    0.430520] pcieport 0000:00:04.0: irq 25 for MSI/MSI-X
[    0.430526] pcieport 0000:00:04.0: setting latency timer to 64
[    0.430613]   alloc irq_desc for 26 on node 0
[    0.430615]   alloc kstat_irqs on node 0
[    0.430619] pcieport 0000:00:06.0: irq 26 for MSI/MSI-X
[    0.430623] pcieport 0000:00:06.0: setting latency timer to 64
[    0.430684] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.430704] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.432087] ACPI: AC Adapter [ADP1] (off-line)
[    0.432157] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0
[    0.432160] ACPI: Power Button [PWRB]
[    0.432193] input: Lid Switch as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0D:00/input/input1
[    0.433196] ACPI: Lid Switch [LID0]
[    0.433267] input: Sleep Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0E:00/input/input2
[    0.433307] ACPI: Sleep Button [SLPB]
[    0.433357] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input3
[    0.433359] ACPI: Power Button [PWRF]
[    0.433585] ACPI: processor limited to max C-state 1
[    0.433608] processor LNXCPU:00: registered as cooling_device0
[    0.433635] processor LNXCPU:01: registered as cooling_device1
[    0.447630] thermal LNXTHERM:01: registered as thermal_zone0
[    0.447639] ACPI: Thermal Zone [TZS0] (32 C)
[    0.453341] thermal LNXTHERM:02: registered as thermal_zone1
[    0.453350] ACPI: Thermal Zone [TZS1] (27 C)
[    0.454685] Linux agpgart interface v0.103
[    0.454717] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    0.455733] brd: module loaded
[    0.456095] loop: module loaded
[    0.456178] input: Macintosh mouse button emulation as /devices/virtual/input/input4
[    0.456532] Fixed MDIO Bus: probed
[    0.456561] PPP generic driver version 2.4.2
[    0.456591] tun: Universal TUN/TAP device driver, 1.6
[    0.456592] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.456657] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.456760]   alloc irq_desc for 17 on node 0
[    0.456762]   alloc kstat_irqs on node 0
[    0.456768] ehci_hcd 0000:00:12.2: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    0.456802] ehci_hcd 0000:00:12.2: EHCI Host Controller
[    0.456830] ehci_hcd 0000:00:12.2: new USB bus registered, assigned bus number 1
[    0.456868] ehci_hcd 0000:00:12.2: debug port 1
[    0.456892] ehci_hcd 0000:00:12.2: irq 17, io mem 0xf0208400
[    0.467866] ehci_hcd 0000:00:12.2: USB 2.0 started, EHCI 1.00
[    0.467976] usb usb1: configuration #1 chosen from 1 choice
[    0.468008] hub 1-0:1.0: USB hub found
[    0.468016] hub 1-0:1.0: 6 ports detected
[    0.468219]   alloc irq_desc for 19 on node 0
[    0.468222]   alloc kstat_irqs on node 0
[    0.468227] ehci_hcd 0000:00:13.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    0.468249] ehci_hcd 0000:00:13.2: EHCI Host Controller
[    0.468283] ehci_hcd 0000:00:13.2: new USB bus registered, assigned bus number 2
[    0.468315] ehci_hcd 0000:00:13.2: debug port 1
[    0.468338] ehci_hcd 0000:00:13.2: irq 19, io mem 0xf0208800
[    0.487876] ehci_hcd 0000:00:13.2: USB 2.0 started, EHCI 1.00
[    0.487985] usb usb2: configuration #1 chosen from 1 choice
[    0.488016] hub 2-0:1.0: USB hub found
[    0.488023] hub 2-0:1.0: 6 ports detected
[    0.488135] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.488229] ohci_hcd 0000:00:12.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.488256] ohci_hcd 0000:00:12.0: OHCI Host Controller
[    0.488300] ohci_hcd 0000:00:12.0: new USB bus registered, assigned bus number 3
[    0.488372] ohci_hcd 0000:00:12.0: irq 16, io mem 0xf0004000
[    0.516856] Freeing initrd memory: 8137k freed
[    0.551958] usb usb3: configuration #1 chosen from 1 choice
[    0.551984] hub 3-0:1.0: USB hub found
[    0.552029] hub 3-0:1.0: 3 ports detected
[    0.552171] ohci_hcd 0000:00:12.1: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.552193] ohci_hcd 0000:00:12.1: OHCI Host Controller
[    0.552229] ohci_hcd 0000:00:12.1: new USB bus registered, assigned bus number 4
[    0.552254] ohci_hcd 0000:00:12.1: irq 16, io mem 0xf0005000
[    0.572304] ACPI: Battery Slot [BAT0] (battery present)
[    0.611950] usb usb4: configuration #1 chosen from 1 choice
[    0.611976] hub 4-0:1.0: USB hub found
[    0.612021] hub 4-0:1.0: 3 ports detected
[    0.612166] ohci_hcd 0000:00:13.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    0.612189] ohci_hcd 0000:00:13.0: OHCI Host Controller
[    0.612222] ohci_hcd 0000:00:13.0: new USB bus registered, assigned bus number 5
[    0.612252] ohci_hcd 0000:00:13.0: irq 18, io mem 0xf0006000
[    0.671954] usb usb5: configuration #1 chosen from 1 choice
[    0.671986] hub 5-0:1.0: USB hub found
[    0.672030] hub 5-0:1.0: 3 ports detected
[    0.672173] ohci_hcd 0000:00:13.1: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    0.672197] ohci_hcd 0000:00:13.1: OHCI Host Controller
[    0.672237] ohci_hcd 0000:00:13.1: new USB bus registered, assigned bus number 6
[    0.672257] ohci_hcd 0000:00:13.1: irq 18, io mem 0xf0007000
[    0.731953] usb usb6: configuration #1 chosen from 1 choice
[    0.731978] hub 6-0:1.0: USB hub found
[    0.732022] hub 6-0:1.0: 3 ports detected
[    0.732092] uhci_hcd: USB Universal Host Controller Interface driver
[    0.732160] PNP: PS/2 Controller [PNP0303:KBD0,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    0.741471] i8042.c: Detected active multiplexing controller, rev 1.1.
[    0.748303] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.748362] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[    0.748385] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[    0.748402] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[    0.748418] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[    0.748510] mice: PS/2 mouse device common for all mice
[    0.748661] rtc_cmos 00:04: RTC can wake from S4
[    0.748695] rtc_cmos 00:04: rtc core: registered rtc_cmos as rtc0
[    0.748719] rtc0: alarms up to one month, 114 bytes nvram, hpet irqs
[    0.748825] device-mapper: uevent: version 1.0.3
[    0.748938] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: dm-devel@redhat.com
[    0.749023] device-mapper: multipath: version 1.1.0 loaded
[    0.749025] device-mapper: multipath round-robin: version 1.0.0 loaded
[    0.749188] cpuidle: using governor ladder
[    0.749190] cpuidle: using governor menu
[    0.749494] TCP cubic registered
[    0.749596] NET: Registered protocol family 10
[    0.749967] lo: Disabled Privacy Extensions
[    0.750208] NET: Registered protocol family 17
[    0.750251] powernow-k8: Found 1 AMD Turion(tm) II Dual-Core Mobile M500 processors (2 cpu cores) (version 2.20.00)
[    0.750291] powernow-k8:    0 : pstate 0 (2200 MHz)
[    0.750293] powernow-k8:    1 : pstate 1 (2000 MHz)
[    0.750295] powernow-k8:    2 : pstate 2 (1500 MHz)
[    0.750297] powernow-k8:    3 : pstate 3 (1100 MHz)
[    0.750298] powernow-k8:    4 : pstate 4 (800 MHz)
[    0.750551] PM: Resume from disk failed.
[    0.750565] registered taskstats version 1
[    0.750882]   Magic number: 10:987:229
[    0.751007] rtc_cmos 00:04: setting system clock to 2010-05-06 13:12:14 UTC (1273151534)
[    0.751010] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.751012] EDD information not available.
[    0.751065] Freeing unused kernel memory: 876k freed
[    0.751315] Write protecting the kernel read-only data: 7680k
[    0.770660] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input5
[    0.788854] udev: starting version 151
[    0.807874] usb 2-5: new high speed USB device using ehci_hcd and address 2
[    0.861895] tg3.c:v3.102 (September 1, 2009)
[    0.861917] tg3 0000:03:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.861927] tg3 0000:03:00.0: setting latency timer to 64
[    0.866241] ahci 0000:00:11.0: version 3.0
[    0.866294]   alloc irq_desc for 22 on node 0
[    0.866297]   alloc kstat_irqs on node 0
[    0.866304] ahci 0000:00:11.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[    0.866401] ahci 0000:00:11.0: AHCI 0001.0100 32 slots 2 ports 3 Gbps 0x3 impl SATA mode
[    0.866404] ahci 0000:00:11.0: flags: 64bit ncq sntf ilck pm led clo pmp pio slum part ccc 
[    0.890225] scsi0 : ahci
[    0.916536] scsi1 : ahci
[    0.916695] ata1: SATA max UDMA/133 abar m1024@0xf0208000 port 0xf0208100 irq 22
[    0.916699] ata2: SATA max UDMA/133 abar m1024@0xf0208000 port 0xf0208180 irq 22
[    0.996019] usb 2-5: configuration #1 chosen from 1 choice
[    1.440115] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    1.440144] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    1.441330] ata1.00: ATA-8: Hitachi HTS545032B9A300, PB3OC60F, max UDMA/133
[    1.441334] ata1.00: 625142448 sectors, multi 16: LBA48 NCQ (depth 31/32), AA
[    1.442812] ata1.00: configured for UDMA/133
[    1.443507] ata2.00: ATAPI: HL-DT-STDVDRAM GT30N, 1.01, max UDMA/100, ATAPI AN
[    1.447564] ata2.00: configured for UDMA/100
[    1.460248] scsi 0:0:0:0: Direct-Access     ATA      Hitachi HTS54503 PB3O PQ: 0 ANSI: 5
[    1.460402] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    1.460496] sd 0:0:0:0: [sda] 625142448 512-byte logical blocks: (320 GB/298 GiB)
[    1.460529] sd 0:0:0:0: [sda] Write Protect is off
[    1.460532] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.460548] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.460650]  sda:
[    1.462911] scsi 1:0:0:0: CD-ROM            HL-DT-ST DVDRAM GT30N     1.01 PQ: 0 ANSI: 5
[    1.471017] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[    1.471022] Uniform CD-ROM driver Revision: 3.20
[    1.471161] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    1.471219] sr 1:0:0:0: Attached scsi generic sg1 type 5
[    1.485675]  sda1 sda2 sda3 < sda5 sda6 >
[    1.528231] sd 0:0:0:0: [sda] Attached SCSI disk
[    1.995112] EXT4-fs (sda5): mounted filesystem with ordered data mode
[    2.231429] eth0: Tigon3 [partno(BCM95784M) rev 5784100] (PCI Express) MAC address 00:26:2d:73:bb:b1
[    2.231433] eth0: attached PHY is 5784 (10/100/1000Base-T Ethernet) (WireSpeed[1])
[    2.231435] eth0: RXcsums[1] LinkChgREG[0] MIirq[0] ASF[0] TSOcap[1]
[    2.231437] eth0: dma_rwctrl[76180000] dma_mask[64-bit]
[    4.257632] Adding 10634988k swap on /dev/sda6.  Priority:-1 extents:1 across:10634988k 
[    5.197795] udev: starting version 151
[    6.963231] acpi device:37: registered as cooling_device2
[    6.963579] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:34/LNXVIDEO:01/input/input6
[    6.963720] ACPI: Video Device [VGA1] (multi-head: yes  rom: no  post: no)
[    6.986309] piix4_smbus 0000:00:14.0: SMBus Host Controller at 0x8040, revision 0
[    7.067509] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[    7.111745] cfg80211: Calling CRDA to update world regulatory domain
[    7.150512] acer-wmi: Acer Laptop ACPI-WMI Extras
[    7.155962] acer-wmi: Brightness must be controlled by generic video driver
[    8.056650] type=1505 audit(1273162341.799:2):  operation="profile_load" pid=682 name="/sbin/dhclient3"
[    8.056903] type=1505 audit(1273162341.799:3):  operation="profile_load" pid=682 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[    8.057045] type=1505 audit(1273162341.799:4):  operation="profile_load" pid=682 name="/usr/lib/connman/scripts/dhclient-script"
[    8.098496] ath9k 0000:09:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    8.098506] ath9k 0000:09:00.0: setting latency timer to 64
[    8.458168] EDAC MC: Ver: 2.1.0 Apr 28 2010
[    8.525282] [drm] Initialized drm 1.1.0 20060810
[    8.527594] ath: EEPROM regdomain: 0x65
[    8.527596] ath: EEPROM indicates we should expect a direct regpair map
[    8.527600] ath: Country alpha2 being used: 00
[    8.527601] ath: Regpair used: 0x65
[    8.554494] EDAC amd64_edac:  Ver: 3.2.0 Apr 28 2010
[    8.554570] EDAC amd64: This node reports that Memory ECC is currently disabled, set F3x44[22] (0000:00:18.3).
[    8.554580] EDAC amd64: ECC disabled in the BIOS or no ECC capability, module will not load.
[    8.554581]  Either enable ECC checking or force module loading by setting 'ecc_enable_override'.
[    8.554583]  (Note that use of the override may cause unknown side effects.)
[    8.554619] amd64_edac: probe of 0000:00:18.2 failed with error -22
[    8.582177] phy0: Selected rate control algorithm 'ath9k_rate_control'
[    8.582779] Registered led device: ath9k-phy0::radio
[    8.582793] Registered led device: ath9k-phy0::assoc
[    8.582809] Registered led device: ath9k-phy0::tx
[    8.582822] Registered led device: ath9k-phy0::rx
[    8.582832] phy0: Atheros AR9280 MAC/BB Rev:2 AR5133 RF Rev:d0: mem=0xffffc900021a0000, irq=18
[    8.593994] lp: driver loaded but no devices found
[    8.729547] cfg80211: World regulatory domain updated:
[    8.729550] 	(start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[    8.729553] 	(2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[    8.729556] 	(2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[    8.729558] 	(2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[    8.729560] 	(5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[    8.729562] 	(5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[    8.839406] Linux video capture interface: v2.00
[    8.858483] uvcvideo: Found UVC 1.00 device CNF7017 (04f2:b044)
[    8.914860] input: CNF7017 as /devices/pci0000:00/0000:00:13.2/usb2/2-5/2-5:1.0/input/input7
[    8.914908] usbcore: registered new interface driver uvcvideo
[    8.914912] USB Video Class driver (v0.1.0)
[    9.063024] input: ImPS/2 Generic Wheel Mouse as /devices/platform/i8042/serio2/input/input8
[    9.843116] [drm] radeon defaulting to kernel modesetting.
[    9.843119] [drm] radeon kernel modesetting enabled.
[    9.843228] radeon 0000:01:05.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    9.843233] radeon 0000:01:05.0: setting latency timer to 64
[    9.847989] [drm] radeon: Initializing kernel modesetting.
[    9.848119] [drm] register mmio base: 0xCFDF0000
[    9.848121] [drm] register mmio size: 65536
[    9.848190] ATOM BIOS: Acer_JV50TR
[    9.848204] [drm] Clocks initialized !
[    9.848365] [drm] Detected VRAM RAM=256M, BAR=256M
[    9.848369] [drm] RAM width 32bits DDR
[    9.848453] [TTM] Zone  kernel: Available graphics memory: 1898760 kiB.
[    9.848473] [drm] radeon: 256M of VRAM memory ready
[    9.848475] [drm] radeon: 512M of GTT memory ready.
[    9.848514] [drm] radeon: irq initialized.
[    9.848517] [drm] GART: num cpu pages 131072, num gpu pages 131072
[    9.849213] [drm] Loading RS780 Microcode
[    9.849217] platform radeon_cp.0: firmware: requesting radeon/RS780_pfp.bin
[   10.259374] platform radeon_cp.0: firmware: requesting radeon/RS780_me.bin
[   10.458057] platform radeon_cp.0: firmware: requesting radeon/R600_rlc.bin
[   10.970049] [drm] ring test succeeded in 1 usecs
[   10.970134] [drm] radeon: ib pool ready.
[   10.970195] [drm] ib test succeeded in 0 usecs
[   10.970197] [drm] Enabling audio support
[   10.970996] [drm] Radeon Display Connectors
[   10.970999] [drm] Connector 0:
[   10.971001] [drm]   VGA
[   10.971003] [drm]   DDC: 0x7e40 0x7e40 0x7e44 0x7e44 0x7e48 0x7e48 0x7e4c 0x7e4c
[   10.971005] [drm]   Encoders:
[   10.971006] [drm]     CRT1: INTERNAL_KLDSCP_DAC1
[   10.971008] [drm] Connector 1:
[   10.971009] [drm]   LVDS
[   10.971010] [drm]   DDC: 0x7e50 0x7e50 0x7e54 0x7e54 0x7e58 0x7e58 0x7e5c 0x7e5c
[   10.971012] [drm]   Encoders:
[   10.971013] [drm]     LCD1: INTERNAL_KLDSCP_LVTMA
[   10.971015] [drm] Connector 2:
[   10.971016] [drm]   HDMI-A
[   10.971017] [drm]   HPD1
[   10.971018] [drm]   DDC: 0x7e20 0x7e20 0x7e24 0x7e24 0x7e28 0x7e28 0x7e2c 0x7e2c
[   10.971020] [drm]   Encoders:
[   10.971021] [drm]     DFP1: INTERNAL_UNIPHY
[   11.080520] HDA Intel 0000:00:14.2: power state changed by ACPI to D0
[   11.080542] HDA Intel 0000:00:14.2: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   11.104862] [drm] fb mappable at 0xD0141000
[   11.104865] [drm] vram apper at 0xD0000000
[   11.104866] [drm] size 4325376
[   11.104868] [drm] fb depth is 24
[   11.104869] [drm]    pitch is 5632
[   11.105045] fb0: radeondrmfb frame buffer device
[   11.105047] registered panic notifier
[   11.105052] [drm] Initialized radeon 2.0.0 20080528 for 0000:01:05.0 on minor 0
[   11.591068] hda_codec: ALC888: BIOS auto-probing.
[   11.592619] input: HDA Digital PCBeep as /devices/pci0000:00/0000:00:14.2/input/input9
[   11.607796] HDA Intel 0000:01:05.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[   11.607849] HDA Intel 0000:01:05.1: setting latency timer to 64
[   11.723001] vga16fb: initializing
[   11.723005] vga16fb: mapped to 0xffff8800000a0000
[   11.723011] vga16fb: not registering due to another framebuffer present
[   13.000228] Console: switching to colour frame buffer device 170x48
[   15.013958]   alloc irq_desc for 27 on node 0
[   15.013962]   alloc kstat_irqs on node 0
[   15.013975] tg3 0000:03:00.0: irq 27 for MSI/MSI-X
[   15.120093] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   15.401379] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   15.598366] type=1505 audit(1273162349.339:5):  operation="profile_load" pid=941 name="/usr/share/gdm/guest-session/Xsession"
[   15.600129] type=1505 audit(1273162349.349:6):  operation="profile_replace" pid=1004 name="/sbin/dhclient3"
[   15.600391] type=1505 audit(1273162349.349:7):  operation="profile_replace" pid=1004 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[   15.600538] type=1505 audit(1273162349.349:8):  operation="profile_replace" pid=1004 name="/usr/lib/connman/scripts/dhclient-script"
[   16.067044] type=1505 audit(1273162349.809:9):  operation="profile_load" pid=1005 name="/usr/bin/evince"
[   16.070365] type=1505 audit(1273162349.819:10):  operation="profile_load" pid=1005 name="/usr/bin/evince-previewer"
[   16.072413] type=1505 audit(1273162349.819:11):  operation="profile_load" pid=1005 name="/usr/bin/evince-thumbnailer"
[   16.466579] type=1505 audit(1273162350.209:12):  operation="profile_load" pid=1009 name="/usr/lib/cups/backend/cups-pdf"
[   16.466901] type=1505 audit(1273162350.209:13):  operation="profile_load" pid=1009 name="/usr/sbin/cupsd"
[   16.715055] type=1505 audit(1273162350.459:14):  operation="profile_load" pid=1014 name="/usr/sbin/tcpdump"
[   33.527582] hda-intel: IRQ timing workaround is activated for card #1. Suggest a bigger bdl_pos_adj.
[   41.916436] vboxdrv: Trying to deactivate the NMI watchdog permanently...
[   41.916444] vboxdrv: Successfully done.
[   41.916450] vboxdrv: Found 2 processor cores.
[   41.916595] VBoxDrv: dbg - g_abExecMemory=ffffffffa03c4a20
[   41.916637] vboxdrv: fAsync=0 offMin=0x44b offMax=0xb8d
[   41.917735] vboxdrv: TSC mode is 'synchronous', kernel timer mode is 'normal'.
[   41.917742] vboxdrv: Successfully loaded version 3.1.6_OSE (interface 0x00100001).
[   47.604744] ppdev: user-space parallel port driver
[   66.703751] wlan0: direct probe to AP 00:02:cf:c5:00:10 (try 1)
[   66.703781] wlan0: deauthenticating from 00:02:cf:c5:00:10 by local choice (reason=3)
[   66.703801] wlan0: direct probe to AP 00:02:cf:c5:00:10 (try 1)
[   66.707700] wlan0: direct probe responded
[   66.707707] wlan0: authenticate with AP 00:02:cf:c5:00:10 (try 1)
[   66.710289] wlan0: authenticated
[   66.710306] wlan0: associate with AP 00:02:cf:c5:00:10 (try 1)
[   66.712167] wlan0: RX AssocResp from 00:02:cf:c5:00:10 (capab=0x431 status=0 aid=3)
[   66.712169] wlan0: associated
[   66.712737] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   76.870101] wlan0: no IPv6 routers present
[  156.290223] usb 5-1: new low speed USB device using ohci_hcd and address 2
[  156.484507] usb 5-1: configuration #1 chosen from 1 choice
[  156.583077] usbcore: registered new interface driver hiddev
[  156.588768] input: A4Tech PS/2+USB Mouse as /devices/pci0000:00/0000:00:13.0/usb5/5-1/5-1:1.0/input/input10
[  156.588986] generic-usb 0003:09DA:000E.0001: input,hidraw0: USB HID v1.10 Mouse [A4Tech PS/2+USB Mouse] on usb-0000:00:13.0-1/input0
[  156.589042] usbcore: registered new interface driver usbhid
[  156.589048] usbhid: v2.6:USB HID core driver

```

---

### Post by josedb on 2010-05-11
Official forum and no help, god save us!

---

