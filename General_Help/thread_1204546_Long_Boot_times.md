---
title: "Long Boot times"
date: 2009-07-04
forum: General Help
---

### Post by manikanthm on 2009-07-04
Hi all,

I am pretty new to Ubuntu, being a recent convert. Everything seems to go well, except that I have been facing long times for booting up my computer. I have tried googling around a bit and have already tried options in the grub menu.lst using "irqpoll" and using the verbose mode. 

I have attached my dmesg output here (ref. between 13 and 191 - whats causing that lag?). Possibilities that I could think of (neither i am sure of ) - 1. its the touchpad (but the touchpad works fine), 2. its the loading of the swap partition.

Help appreciated !

cheers,
mani

============= dmesg ===========
[    0.000000] BIOS EBDA/lowmem at: 0009f800/0009f800
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.28-13-generic (buildd@vernadsky) (gcc version 4.3.3 (Ubuntu 4.3.3-5ubuntu4) ) #45-Ubuntu SMP Tue Jun 30 19:49:51 UTC 2009 (Ubuntu 2.6.28-13.45-generic)
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
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
[    0.000000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e0000 - 00000000000e4000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e8000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000007fe80000 (usable)
[    0.000000]  BIOS-e820: 000000007fe80000 - 000000007fe8a000 (ACPI data)
[    0.000000]  BIOS-e820: 000000007fe8a000 - 000000007ff00000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000007ff00000 - 0000000080000000 (reserved)
[    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0006000 (reserved)
[    0.000000]  BIOS-e820: 00000000f0008000 - 00000000f000c000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed00000 - 00000000fed00400 (reserved)
[    0.000000]  BIOS-e820: 00000000fed20000 - 00000000fed90000 (reserved)
[    0.000000]  BIOS-e820: 00000000ff000000 - 0000000100000000 (reserved)
[    0.000000] DMI present.
[    0.000000] last_pfn = 0x7fe80 max_arch_pfn = 0x100000
[    0.000000] Scanning 2 areas for low memory corruption
[    0.000000] modified physical RAM map:
[    0.000000]  modified: 0000000000000000 - 0000000000002000 (usable)
[    0.000000]  modified: 0000000000002000 - 0000000000006000 (reserved)
[    0.000000]  modified: 0000000000006000 - 0000000000007000 (usable)
[    0.000000]  modified: 0000000000007000 - 0000000000010000 (reserved)
[    0.000000]  modified: 0000000000010000 - 0000000000092800 (usable)
[    0.000000]  modified: 000000000009f800 - 00000000000a0000 (reserved)
[    0.000000]  modified: 00000000000e0000 - 00000000000e4000 (reserved)
[    0.000000]  modified: 00000000000e8000 - 0000000000100000 (reserved)
[    0.000000]  modified: 0000000000100000 - 000000007fe80000 (usable)
[    0.000000]  modified: 000000007fe80000 - 000000007fe8a000 (ACPI data)
[    0.000000]  modified: 000000007fe8a000 - 000000007ff00000 (ACPI NVS)
[    0.000000]  modified: 000000007ff00000 - 0000000080000000 (reserved)
[    0.000000]  modified: 00000000e0000000 - 00000000f0006000 (reserved)
[    0.000000]  modified: 00000000f0008000 - 00000000f000c000 (reserved)
[    0.000000]  modified: 00000000fed00000 - 00000000fed00400 (reserved)
[    0.000000]  modified: 00000000fed20000 - 00000000fed90000 (reserved)
[    0.000000]  modified: 00000000ff000000 - 0000000100000000 (reserved)
[    0.000000] kernel direct mapping tables up to 373fe000 @ 10000-16000
[    0.000000] RAMDISK: 378bb000 - 37fef142
[    0.000000] Allocated new RAMDISK: 0087b000 - 00faf142
[    0.000000] Move RAMDISK from 00000000378bb000 - 0000000037fef141 to 0087b000 - 00faf141
[    0.000000] ACPI: RSDP 000F6BB0, 0014 (r0 PTLTD )
[    0.000000] ACPI: RSDT 7FE8224F, 0044 (r1 PTLTD    RSDT    6040000  LTP        0)
[    0.000000] ACPI: FACP 7FE89E88, 0074 (r1 INTEL  ALVISO    6040000 LOHR       5F)
[    0.000000] ACPI: DSDT 7FE82AC9, 73BF (r1 INTEL  ALVISO    6040000 MSFT  2000002)
[    0.000000] ACPI: FACS 7FE9AFC0, 0040
[    0.000000] ACPI: APIC 7FE89EFC, 0068 (r1 INTEL  ALVISO    6040000 LOHR       5F)
[    0.000000] ACPI: HPET 7FE89F64, 0038 (r1 INTEL  ALVISO    6040000 LOHR       5F)
[    0.000000] ACPI: MCFG 7FE89F9C, 003C (r1 INTEL  ALVISO    6040000 LOHR       5F)
[    0.000000] ACPI: BOOT 7FE89FD8, 0028 (r1 PTLTD  $SBFTBL$  6040000  LTP        1)
[    0.000000] ACPI: SSDT 7FE82684, 0235 (r1  PmRef  Cpu0Ist     3000 INTL 20030224)
[    0.000000] ACPI: SSDT 7FE824AC, 01D8 (r1  PmRef  Cpu0Cst     3001 INTL 20030224)
[    0.000000] ACPI: SSDT 7FE82293, 0219 (r1  PmRef    CpuPm     3000 INTL 20030224)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] 1162MB HIGHMEM available.
[    0.000000] 883MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 373fe000
[    0.000000]   low ram: 00000000 - 373fe000
[    0.000000]   bootmap 00012000 - 00018e80
[    0.000000] (9 early reservations) ==> bootmem [0000000000 - 00373fe000]
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
[    0.000000]   #1 [0000001000 - 0000002000]    EX TRAMPOLINE ==> [0000001000 - 0000002000]
[    0.000000]   #2 [0000006000 - 0000007000]       TRAMPOLINE ==> [0000006000 - 0000007000]
[    0.000000]   #3 [0000100000 - 00008760ac]    TEXT DATA BSS ==> [0000100000 - 00008760ac]
[    0.000000]   #4 [0000877000 - 000087b000]    INIT_PG_TABLE ==> [0000877000 - 000087b000]
[    0.000000]   #5 [000009f800 - 0000100000]    BIOS reserved ==> [000009f800 - 0000100000]
[    0.000000]   #6 [0000010000 - 0000012000]          PGTABLE ==> [0000010000 - 0000012000]
[    0.000000]   #7 [000087b000 - 0000faf142]      NEW RAMDISK ==> [000087b000 - 0000faf142]
[    0.000000]   #8 [0000012000 - 0000019000]          BOOTMAP ==> [0000012000 - 0000019000]
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000000 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x000373fe
[    0.000000]   HighMem  0x000373fe -> 0x0007fe80
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[4] active PFN ranges
[    0.000000]     0: 0x00000000 -> 0x00000002
[    0.000000]     0: 0x00000006 -> 0x00000007
[    0.000000]     0: 0x00000010 -> 0x00000092
[    0.000000]     0: 0x00000100 -> 0x0007fe80
[    0.000000] On node 0 totalpages: 523781
[    0.000000] free_area_init_node: node 0, pgdat c06c9500, node_mem_map c1000000
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3941 pages, LIFO batch:0
[    0.000000]   Normal zone: 1736 pages used for memmap
[    0.000000]   Normal zone: 220470 pages, LIFO batch:31
[    0.000000]   HighMem zone: 2326 pages used for memmap
[    0.000000]   HighMem zone: 295276 pages, LIFO batch:31
[    0.000000]   Movable zone: 0 pages used for memmap
[    0.000000] ACPI: PM-Timer IO Port: 0x1008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] disabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 1, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] SMP: Allowing 2 CPUs, 1 hotplug CPUs
[    0.000000] PM: Registered nosave memory: 0000000000002000 - 0000000000006000
[    0.000000] PM: Registered nosave memory: 0000000000007000 - 0000000000010000
[    0.000000] PM: Registered nosave memory: 0000000000092000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
[    0.000000] PM: Registered nosave memory: 00000000000e0000 - 00000000000e4000
[    0.000000] PM: Registered nosave memory: 00000000000e4000 - 00000000000e8000
[    0.000000] PM: Registered nosave memory: 00000000000e8000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 88000000 (gap: 80000000:60000000)
[    0.000000] PERCPU: Allocating 45056 bytes of per cpu data
[    0.000000] NR_CPUS: 64, nr_cpu_ids: 2, nr_node_ids 1
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 519687
[    0.000000] Kernel command line: root=UUID=2071369f-6be3-4a8a-9dc6-a166f10b6888 ro irqpoll i8042.nomux 
[    0.000000] Misrouted IRQ fixup and polling support enabled
[    0.000000] This may significantly impact system performance
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] TSC: PIT calibration matches PMTIMER. 1 loops
[    0.000000] Detected 1728.952 MHz processor.
[    0.004000] Console: colour VGA+ 80x25
[    0.004000] console [tty0] enabled
[    0.004000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.004000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.004000] allocated 10478080 bytes of page_cgroup
[    0.004000] please try cgroup_disable=memory option if you don't want
[    0.004000] Scanning for low memory corruption every 60 seconds
[    0.004000] Memory: 2051648k/2095616k available (4110k kernel code, 42616k reserved, 2196k data, 532k init, 1190408k highmem)
[    0.004000] virtual kernel memory layout:
[    0.004000]     fixmap  : 0xffc77000 - 0xfffff000   (3616 kB)
[    0.004000]     pkmap   : 0xff400000 - 0xff800000   (4096 kB)
[    0.004000]     vmalloc : 0xf7bfe000 - 0xff3fe000   ( 120 MB)
[    0.004000]     lowmem  : 0xc0000000 - 0xf73fe000   ( 883 MB)
[    0.004000]       .init : 0xc0731000 - 0xc07b6000   ( 532 kB)
[    0.004000]       .data : 0xc0503b9f - 0xc0728e60   (2196 kB)
[    0.004000]       .text : 0xc0100000 - 0xc0503b9f   (4110 kB)
[    0.004000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.004000] SLUB: Genslabs=12, HWalign=64, Order=0-3, MinObjects=0, CPUs=2, Nodes=1
[    0.004000] hpet clockevent registered
[    0.004000] HPET: 3 timers in total, 0 timers will be used for per-cpu timer
[    0.004000] Calibrating delay loop (skipped), value calculated using timer frequency.. 3457.90 BogoMIPS (lpj=6915808)
[    0.004000] Security Framework initialized
[    0.004000] SELinux:  Disabled at boot.
[    0.004000] AppArmor: AppArmor initialized
[    0.004000] Mount-cache hash table entries: 512
[    0.004000] Initializing cgroup subsys ns
[    0.004000] Initializing cgroup subsys cpuacct
[    0.004000] Initializing cgroup subsys memory
[    0.004000] Initializing cgroup subsys freezer
[    0.004000] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.004000] CPU: L2 cache: 2048K
[    0.004000] Checking 'hlt' instruction... OK.
[    0.017037] SMP alternatives: switching to UP code
[    0.135512] ACPI: Core revision 20080926
[    0.139191] ACPI: Checking initramfs for custom DSDT
[    0.500570] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.542139] CPU0: Intel(R) Pentium(R) M processor 1.73GHz stepping 08
[    0.544002] APIC calibration not consistent with PM Timer: 247ms instead of 100ms
[    0.544002] APIC delta adjusted to PM-Timer: 831248 (2061474)
[    0.544002] Brought up 1 CPUs
[    0.544002] Total of 1 processors activated (3457.90 BogoMIPS).
[    0.544002] CPU0 attaching NULL sched-domain.
[    0.544002] net_namespace: 776 bytes
[    0.544002] Booting paravirtualized kernel on bare hardware
[    0.544002] Time:  2:04:29  Date: 07/05/09
[    0.544002] regulator: core version 0.5
[    0.544002] NET: Registered protocol family 16
[    0.544002] EISA bus registered
[    0.544002] ACPI: bus type pci registered
[    0.544002] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 255
[    0.544002] PCI: MCFG area at e0000000 reserved in E820
[    0.544002] PCI: Using MMCONFIG for extended config space
[    0.544002] PCI: Using configuration type 1 for base access
[    0.544002] ACPI: EC: Look up EC in DSDT
[    0.549810] ACPI: EC: non-query interrupt received, switching to interrupt mode
[    0.552017] ACPI: EC: GPE storm detected, transactions will use polling mode
[    0.582632] ACPI: Interpreter enabled
[    0.582673] ACPI: (supports S0 S3 S4 S5)
[    0.582832] ACPI: Using IOAPIC for interrupt routing
[    0.587878] ACPI: EC: GPE = 0x1d, I/O: command/status = 0x66, data = 0x62
[    0.587920] ACPI: EC: driver started in interrupt mode
[    0.588110] ACPI: No dock devices found.
[    0.588156] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.588275] pci 0000:00:01.0: PME# supported from D0 D3hot D3cold
[    0.588316] pci 0000:00:01.0: PME# disabled
[    0.588413] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    0.588454] pci 0000:00:1c.0: PME# disabled
[    0.588533] pci 0000:00:1c.1: PME# supported from D0 D3hot D3cold
[    0.588574] pci 0000:00:1c.1: PME# disabled
[    0.588652] pci 0000:00:1c.2: PME# supported from D0 D3hot D3cold
[    0.588694] pci 0000:00:1c.2: PME# disabled
[    0.588773] pci 0000:00:1d.0: reg 20 io port: [0x1800-0x181f]
[    0.588816] pci 0000:00:1d.1: reg 20 io port: [0x1820-0x183f]
[    0.588859] pci 0000:00:1d.2: reg 20 io port: [0x1840-0x185f]
[    0.588902] pci 0000:00:1d.3: reg 20 io port: [0x1860-0x187f]
[    0.588950] pci 0000:00:1d.7: reg 10 32bit mmio: [0xc8000000-0xc80003ff]
[    0.588985] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
[    0.589027] pci 0000:00:1d.7: PME# disabled
[    0.589124] pci 0000:00:1e.2: reg 10 io port: [0x1c00-0x1cff]
[    0.589130] pci 0000:00:1e.2: reg 14 io port: [0x1880-0x18bf]
[    0.589136] pci 0000:00:1e.2: reg 18 32bit mmio: [0xc8000800-0xc80009ff]
[    0.589142] pci 0000:00:1e.2: reg 1c 32bit mmio: [0xc8000400-0xc80004ff]
[    0.589161] pci 0000:00:1e.2: PME# supported from D0 D3hot D3cold
[    0.589202] pci 0000:00:1e.2: PME# disabled
[    0.589262] pci 0000:00:1e.3: reg 10 io port: [0x2400-0x24ff]
[    0.589268] pci 0000:00:1e.3: reg 14 io port: [0x2000-0x207f]
[    0.589294] pci 0000:00:1e.3: PME# supported from D0 D3hot D3cold
[    0.589335] pci 0000:00:1e.3: PME# disabled
[    0.589433] pci 0000:00:1f.0: quirk: region 1000-107f claimed by ICH6 ACPI/GPIO/TCO
[    0.589481] pci 0000:00:1f.0: quirk: region 1180-11bf claimed by ICH6 GPIO
[    0.589537] pci 0000:00:1f.1: reg 10 io port: [0x00-0x07]
[    0.589544] pci 0000:00:1f.1: reg 14 io port: [0x00-0x03]
[    0.589550] pci 0000:00:1f.1: reg 18 io port: [0x00-0x07]
[    0.589557] pci 0000:00:1f.1: reg 1c io port: [0x00-0x03]
[    0.589563] pci 0000:00:1f.1: reg 20 io port: [0x18c0-0x18cf]
[    0.589616] pci 0000:00:1f.3: reg 20 io port: [0x20a0-0x20bf]
[    0.589659] pci 0000:01:00.0: reg 10 32bit mmio: [0xd0000000-0xd7ffffff]
[    0.589665] pci 0000:01:00.0: reg 14 io port: [0x3000-0x30ff]
[    0.589671] pci 0000:01:00.0: reg 18 32bit mmio: [0xc8100000-0xc810ffff]
[    0.589686] pci 0000:01:00.0: reg 30 32bit mmio: [0x000000-0x01ffff]
[    0.589694] pci 0000:01:00.0: supports D1 D2
[    0.589730] pci 0000:00:01.0: bridge io port: [0x3000-0x3fff]
[    0.589733] pci 0000:00:01.0: bridge 32bit mmio: [0xc8100000-0xc81fffff]
[    0.589737] pci 0000:00:01.0: bridge 32bit mmio pref: [0xd0000000-0xd7ffffff]
[    0.589773] pci 0000:00:1c.0: bridge io port: [0x00-0xfff]
[    0.589777] pci 0000:00:1c.0: bridge 32bit mmio: [0x000000-0x0fffff]
[    0.589783] pci 0000:00:1c.0: bridge 64bit mmio pref: [0x000000-0x0fffff]
[    0.589818] pci 0000:00:1c.1: bridge io port: [0x00-0xfff]
[    0.589823] pci 0000:00:1c.1: bridge 32bit mmio: [0x000000-0x0fffff]
[    0.589829] pci 0000:00:1c.1: bridge 64bit mmio pref: [0x000000-0x0fffff]
[    0.589864] pci 0000:00:1c.2: bridge io port: [0x00-0xfff]
[    0.589868] pci 0000:00:1c.2: bridge 32bit mmio: [0x000000-0x0fffff]
[    0.589874] pci 0000:00:1c.2: bridge 64bit mmio pref: [0x000000-0x0fffff]
[    0.589909] pci 0000:06:01.0: reg 10 32bit mmio: [0xc8216000-0xc8216fff]
[    0.589919] pci 0000:06:01.0: supports D1 D2
[    0.589921] pci 0000:06:01.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.589963] pci 0000:06:01.0: PME# disabled
[    0.590033] pci 0000:06:01.2: reg 10 32bit mmio: [0xc8217000-0xc82177ff]
[    0.590041] pci 0000:06:01.2: reg 14 32bit mmio: [0xc8210000-0xc8213fff]
[    0.590076] pci 0000:06:01.2: supports D1 D2
[    0.590078] pci 0000:06:01.2: PME# supported from D0 D1 D2 D3hot
[    0.590120] pci 0000:06:01.2: PME# disabled
[    0.590188] pci 0000:06:01.3: reg 10 32bit mmio: [0xc8214000-0xc8215fff]
[    0.590225] pci 0000:06:01.3: supports D1 D2
[    0.590228] pci 0000:06:01.3: PME# supported from D0 D1 D2 D3hot
[    0.590269] pci 0000:06:01.3: PME# disabled
[    0.590341] pci 0000:06:02.0: reg 10 32bit mmio: [0xc8217800-0xc8217fff]
[    0.590379] pci 0000:06:02.0: supports D1 D2
[    0.590412] pci 0000:06:03.0: reg 10 32bit mmio: [0xc8218000-0xc8218fff]
[    0.590450] pci 0000:06:03.0: PME# supported from D0 D3hot D3cold
[    0.590492] pci 0000:06:03.0: PME# disabled
[    0.590582] pci 0000:06:08.0: reg 10 32bit mmio: [0xc8200000-0xc820ffff]
[    0.590623] pci 0000:06:08.0: PME# supported from D3hot D3cold
[    0.590665] pci 0000:06:08.0: PME# disabled
[    0.590735] pci 0000:00:1e.0: transparent bridge
[    0.590777] pci 0000:00:1e.0: bridge 32bit mmio: [0xc8200000-0xc82fffff]
[    0.590815] bus 00 -> node 0
[    0.590822] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.591225] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEGP._PRT]
[    0.591386] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP01._PRT]
[    0.591541] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP02._PRT]
[    0.591696] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP03._PRT]
[    0.591970] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCIB._PRT]
[    0.599738] ACPI: PCI Interrupt Link [LNKA] (IRQs 1 3 4 5 6 7 *10 12 14 15)
[    0.600208] ACPI: PCI Interrupt Link [LNKB] (IRQs 1 3 4 5 6 7 11 12 14 15) *10
[    0.600718] ACPI: PCI Interrupt Link [LNKC] (IRQs 1 3 4 5 6 7 10 12 14 15) *11
[    0.601231] ACPI: PCI Interrupt Link [LNKD] (IRQs 1 3 4 5 6 7 *11 12 14 15)
[    0.601707] ACPI: PCI Interrupt Link [LNKE] (IRQs 1 3 4 5 6 7 10 12 14 15) *11
[    0.602216] ACPI: PCI Interrupt Link [LNKF] (IRQs 1 3 4 5 6 7 11 12 14 15) *0, disabled.
[    0.602752] ACPI: PCI Interrupt Link [LNKG] (IRQs 1 3 4 5 6 7 10 12 14 15) *0, disabled.
[    0.603288] ACPI: PCI Interrupt Link [LNKH] (IRQs 1 3 4 5 6 7 *11 12 14 15)
[    0.603841] ACPI: WMI: Mapper loaded
[    0.604062] SCSI subsystem initialized
[    0.604135] libata version 3.00 loaded.
[    0.604179] usbcore: registered new interface driver usbfs
[    0.604232] usbcore: registered new interface driver hub
[    0.604295] usbcore: registered new device driver usb
[    0.604444] PCI: Using ACPI for IRQ routing
[    0.604485] pci 0000:00:1c.0: BAR 7: can't allocate resource
[    0.604524] pci 0000:00:1c.0: BAR 8: can't allocate resource
[    0.604563] pci 0000:00:1c.0: BAR 9: can't allocate resource
[    0.604602] pci 0000:00:1c.1: BAR 7: can't allocate resource
[    0.604641] pci 0000:00:1c.1: BAR 8: can't allocate resource
[    0.604680] pci 0000:00:1c.1: BAR 9: can't allocate resource
[    0.604719] pci 0000:00:1c.2: BAR 7: can't allocate resource
[    0.604758] pci 0000:00:1c.2: BAR 8: can't allocate resource
[    0.604797] pci 0000:00:1c.2: BAR 9: can't allocate resource
[    0.604934] Bluetooth: Core ver 2.13
[    0.604934] NET: Registered protocol family 31
[    0.604934] Bluetooth: HCI device and connection manager initialized
[    0.604934] Bluetooth: HCI socket layer initialized
[    0.604934] NET: Registered protocol family 8
[    0.604934] NET: Registered protocol family 20
[    0.604934] NetLabel: Initializing
[    0.604934] NetLabel:  domain hash size = 128
[    0.604934] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.604934] NetLabel:  unlabeled traffic allowed by default
[    0.604934] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[    0.604934] hpet0: 3 comparators, 64-bit 14.318180 MHz counter
[    0.608064] AppArmor: AppArmor Filesystem Enabled
[    0.608106] pnp: PnP ACPI init
[    0.608106] ACPI: bus type pnp registered
[    0.611052] pnp: PnP ACPI: found 10 devices
[    0.611091] ACPI: ACPI bus type pnp unregistered
[    0.611130] PnPBIOS: Disabled by ACPI PNP
[    0.611176] system 00:01: iomem range 0xe0000000-0xefffffff has been reserved
[    0.611217] system 00:01: iomem range 0xf0000000-0xf0003fff has been reserved
[    0.611258] system 00:01: iomem range 0xf0004000-0xf0004fff has been reserved
[    0.611299] system 00:01: iomem range 0xf0005000-0xf0005fff has been reserved
[    0.611340] system 00:01: iomem range 0xf0008000-0xf000bfff has been reserved
[    0.611381] system 00:01: iomem range 0xfed20000-0xfed8ffff has been reserved
[    0.611426] system 00:05: ioport range 0x680-0x6ff has been reserved
[    0.611467] system 00:05: ioport range 0x800-0x80f has been reserved
[    0.611507] system 00:05: ioport range 0x1000-0x107f has been reserved
[    0.611547] system 00:05: ioport range 0x1180-0x11bf has been reserved
[    0.611588] system 00:05: ioport range 0x1600-0x167f has been reserved
[    0.612198] Switched to high resolution mode on CPU 0
[    0.646633] pci 0000:00:01.0: PCI bridge, secondary bus 0000:01
[    0.646673] pci 0000:00:01.0:   IO window: 0x3000-0x3fff
[    0.646714] pci 0000:00:01.0:   MEM window: 0xc8100000-0xc81fffff
[    0.646755] pci 0000:00:01.0:   PREFETCH window: 0x000000d0000000-0x000000d7ffffff
[    0.646804] pci 0000:00:1c.0: PCI bridge, secondary bus 0000:09
[    0.646843] pci 0000:00:1c.0:   IO window: disabled
[    0.646883] pci 0000:00:1c.0:   MEM window: disabled
[    0.646923] pci 0000:00:1c.0:   PREFETCH window: disabled
[    0.646966] pci 0000:00:1c.1: PCI bridge, secondary bus 0000:0a
[    0.647005] pci 0000:00:1c.1:   IO window: disabled
[    0.647045] pci 0000:00:1c.1:   MEM window: disabled
[    0.647085] pci 0000:00:1c.1:   PREFETCH window: disabled
[    0.647127] pci 0000:00:1c.2: PCI bridge, secondary bus 0000:02
[    0.647166] pci 0000:00:1c.2:   IO window: disabled
[    0.647207] pci 0000:00:1c.2:   MEM window: disabled
[    0.647247] pci 0000:00:1c.2:   PREFETCH window: disabled
[    0.647292] pci 0000:06:01.0: CardBus bridge, secondary bus 0000:07
[    0.647331] pci 0000:06:01.0:   IO window: 0x004000-0x0040ff
[    0.647373] pci 0000:06:01.0:   IO window: 0x004400-0x0044ff
[    0.647414] pci 0000:06:01.0:   PREFETCH window: 0x88000000-0x8bffffff
[    0.647457] pci 0000:06:01.0:   MEM window: 0x8c000000-0x8fffffff
[    0.647498] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:06
[    0.647539] pci 0000:00:1e.0:   IO window: 0x4000-0x4fff
[    0.647580] pci 0000:00:1e.0:   MEM window: 0xc8200000-0xc82fffff
[    0.647621] pci 0000:00:1e.0:   PREFETCH window: 0x00000088000000-0x0000008bffffff
[    0.647679] pci 0000:00:01.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.647721] pci 0000:00:01.0: setting latency timer to 64
[    0.647729] pci 0000:00:1c.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    0.647771] pci 0000:00:1c.0: setting latency timer to 64
[    0.647778] pci 0000:00:1c.1: PCI INT B -> GSI 16 (level, low) -> IRQ 16
[    0.647821] pci 0000:00:1c.1: setting latency timer to 64
[    0.647828] pci 0000:00:1c.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.647870] pci 0000:00:1c.2: setting latency timer to 64
[    0.647877] pci 0000:00:1e.0: setting latency timer to 64
[    0.647884] pci 0000:06:01.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    0.647928] bus: 00 index 0 io port: [0x00-0xffff]
[    0.647966] bus: 00 index 1 mmio: [0x000000-0xffffffff]
[    0.648010] bus: 01 index 0 io port: [0x3000-0x3fff]
[    0.648048] bus: 01 index 1 mmio: [0xc8100000-0xc81fffff]
[    0.648087] bus: 01 index 2 mmio: [0xd0000000-0xd7ffffff]
[    0.648126] bus: 01 index 3 mmio: [0x0-0x0]
[    0.648164] bus: 09 index 0 mmio: [0x0-0xfff]
[    0.648201] bus: 09 index 1 mmio: [0x0-0xfffff]
[    0.648239] bus: 09 index 2 mmio: [0x0-0xfffff]
[    0.648277] bus: 09 index 3 mmio: [0x0-0x0]
[    0.648314] bus: 0a index 0 mmio: [0x0-0xfff]
[    0.648352] bus: 0a index 1 mmio: [0x0-0xfffff]
[    0.648390] bus: 0a index 2 mmio: [0x0-0xfffff]
[    0.648428] bus: 0a index 3 mmio: [0x0-0x0]
[    0.648465] bus: 02 index 0 mmio: [0x0-0xfff]
[    0.648503] bus: 02 index 1 mmio: [0x0-0xfffff]
[    0.648541] bus: 02 index 2 mmio: [0x0-0xfffff]
[    0.648579] bus: 02 index 3 mmio: [0x0-0x0]
[    0.648616] bus: 06 index 0 io port: [0x4000-0x4fff]
[    0.648655] bus: 06 index 1 mmio: [0xc8200000-0xc82fffff]
[    0.648694] bus: 06 index 2 mmio: [0x88000000-0x8bffffff]
[    0.648733] bus: 06 index 3 io port: [0x00-0xffff]
[    0.648771] bus: 06 index 4 mmio: [0x000000-0xffffffff]
[    0.648810] bus: 07 index 0 io port: [0x4000-0x40ff]
[    0.648848] bus: 07 index 1 io port: [0x4400-0x44ff]
[    0.648886] bus: 07 index 2 mmio: [0x88000000-0x8bffffff]
[    0.648925] bus: 07 index 3 mmio: [0x8c000000-0x8fffffff]
[    0.648970] NET: Registered protocol family 2
[    0.649123] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.649421] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.650155] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.650642] TCP: Hash tables configured (established 131072 bind 65536)
[    0.650684] TCP reno registered
[    0.650875] NET: Registered protocol family 1
[    0.651058] checking if image is initramfs... it is
[    1.499431] Freeing initrd memory: 7376k freed
[    1.499527] Simple Boot Flag at 0x36 set to 0x1
[    1.499598] cpufreq: No nForce2 chipset.
[    1.499813] audit: initializing netlink socket (disabled)
[    1.499874] type=2000 audit(1246759469.496:1): initialized
[    1.508340] highmem bounce pool size: 64 pages
[    1.508384] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    1.509811] VFS: Disk quotas dquot_6.5.1
[    1.509906] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    1.510592] fuse init (API version 7.10)
[    1.510716] msgmni has been set to 1698
[    1.510933] alg: No test for stdrng (krng)
[    1.510982] io scheduler noop registered
[    1.511019] io scheduler anticipatory registered
[    1.511057] io scheduler deadline registered
[    1.511108] io scheduler cfq registered (default)
[    1.511348] pci 0000:01:00.0: Boot video device
[    1.514649] pcieport-driver 0000:00:01.0: setting latency timer to 64
[    1.514680] pcieport-driver 0000:00:01.0: found MSI capability
[    1.514740] pcieport-driver 0000:00:01.0: irq 2303 for MSI/MSI-X
[    1.514749] pci_express 0000:00:01.0:pcie00: allocate port service
[    1.514765] pci_express 0000:00:01.0:pcie03: allocate port service
[    1.514806] pcieport-driver 0000:00:1c.0: setting latency timer to 64
[    1.514836] pcieport-driver 0000:00:1c.0: found MSI capability
[    1.515553] pcieport-driver 0000:00:1c.0: irq 2302 for MSI/MSI-X
[    1.515563] pci_express 0000:00:1c.0:pcie00: allocate port service
[    1.515577] pci_express 0000:00:1c.0:pcie02: allocate port service
[    1.515591] pci_express 0000:00:1c.0:pcie03: allocate port service
[    1.515645] pcieport-driver 0000:00:1c.1: setting latency timer to 64
[    1.515675] pcieport-driver 0000:00:1c.1: found MSI capability
[    1.515732] pcieport-driver 0000:00:1c.1: irq 2301 for MSI/MSI-X
[    1.515743] pci_express 0000:00:1c.1:pcie00: allocate port service
[    1.515757] pci_express 0000:00:1c.1:pcie02: allocate port service
[    1.515769] pci_express 0000:00:1c.1:pcie03: allocate port service
[    1.515820] pcieport-driver 0000:00:1c.2: setting latency timer to 64
[    1.515849] pcieport-driver 0000:00:1c.2: found MSI capability
[    1.515907] pcieport-driver 0000:00:1c.2: irq 2300 for MSI/MSI-X
[    1.515918] pci_express 0000:00:1c.2:pcie00: allocate port service
[    1.515931] pci_express 0000:00:1c.2:pcie02: allocate port service
[    1.515944] pci_express 0000:00:1c.2:pcie03: allocate port service
[    1.516017] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    1.516321] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    1.519118] ACPI: AC Adapter [ACAD] (on-line)
[    1.519226] ACPI: Battery Slot [BAT1] (battery absent)
[    1.519310] ACPI: Battery Slot [BAT2] (battery absent)
[    1.519415] input: Power Button (FF) as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input0
[    1.519462] ACPI: Power Button (FF) [PWRF]
[    1.519550] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input1
[    1.519661] ACPI: Lid Switch [LID]
[    1.519744] input: Power Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input2
[    1.519792] ACPI: Power Button (CM) [PWRB]
[    1.519871] input: Sleep Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input3
[    1.519919] ACPI: Sleep Button (CM) [SLPB]
[    1.520373] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3] C4[C3])
[    1.520571] processor ACPI_CPU:00: registered as cooling_device0
[    1.520612] ACPI: Processor [CPU0] (supports 8 throttling states)
[    1.525989] thermal LNXTHERM:01: registered as thermal_zone0
[    1.531714] ACPI: Thermal Zone [THRM] (71 C)
[    1.531804] isapnp: Scanning for PnP cards...
[    1.884762] isapnp: No Plug & Play device found
[    1.886187] Serial: 8250/16550 driver4 ports, IRQ sharing enabled
[    1.886595] serial 0000:00:1e.3: PCI INT B -> GSI 20 (level, low) -> IRQ 20
[    1.886638] serial 0000:00:1e.3: PCI INT B disabled
[    1.887351] brd: module loaded
[    1.887704] loop: module loaded
[    1.887807] Fixed MDIO Bus: probed
[    1.887848] PPP generic driver version 2.4.2
[    1.887942] input: Macintosh mouse button emulation as /devices/virtual/input/input4
[    1.888023] Driver 'sd' needs updating - please use bus_type methods
[    1.888071] Driver 'sr' needs updating - please use bus_type methods
[    1.888184] ata_piix 0000:00:1f.1: version 2.12
[    1.888191] ata_piix 0000:00:1f.1: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    1.888266] ata_piix 0000:00:1f.1: setting latency timer to 64
[    1.888351] scsi0 : ata_piix
[    1.888471] scsi1 : ata_piix
[    1.888769] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0x18c0 irq 14
[    1.888810] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x18c8 irq 15
[    2.060430] ata1.00: ATA-6: TOSHIBA MK8025GAS, KA023A, max UDMA/100
[    2.060471] ata1.00: 156301488 sectors, multi 16: LBA 
[    2.060547] ata1.01: ATAPI: MATSHITAUJ-845D, D100, max UDMA/33
[    2.068382] ata1.00: configured for UDMA/100
[    2.084422] ata1.01: configured for UDMA/33
[    2.084820] ata2: port disabled. ignoring.
[    2.084934] scsi 0:0:0:0: Direct-Access     ATA      TOSHIBA MK8025GA KA02 PQ: 0 ANSI: 5
[    2.085079] sd 0:0:0:0: [sda] 156301488 512-byte hardware sectors: (80.0 GB/74.5 GiB)
[    2.085142] sd 0:0:0:0: [sda] Write Protect is off
[    2.085181] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    2.085207] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.085310] sd 0:0:0:0: [sda] 156301488 512-byte hardware sectors: (80.0 GB/74.5 GiB)
[    2.085370] sd 0:0:0:0: [sda] Write Protect is off
[    2.085408] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    2.085433] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.085482]  sda: sda1 sda2 sda3 < sda5 sda6 sda7 sda8 >
[    2.206023] sd 0:0:0:0: [sda] Attached SCSI disk
[    2.206103] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    2.207731] scsi 0:0:1:0: CD-ROM            MATSHITA UJ-845D          D100 PQ: 0 ANSI: 5
[    2.212020] sr0: scsi3-mmc drive: 24x/24x writer cd/rw xa/form2 cdda caddy
[    2.212062] Uniform CD-ROM driver Revision: 3.20
[    2.212181] sr 0:0:1:0: Attached scsi CD-ROM sr0
[    2.212217] sr 0:0:1:0: Attached scsi generic sg1 type 5
[    2.212893] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    2.212951] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    2.213006] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    2.213010] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    2.213112] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 1
[    2.217076] ehci_hcd 0000:00:1d.7: debug port 1
[    2.217118] ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported
[    2.217133] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xc8000000
[    2.232007] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    2.232124] usb usb1: configuration #1 chosen from 1 choice
[    2.232190] hub 1-0:1.0: USB hub found
[    2.232234] hub 1-0:1.0: 8 ports detected
[    2.232377] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    2.232434] uhci_hcd: USB Universal Host Controller Interface driver
[    2.232494] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    2.232538] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    2.232541] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    2.232616] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    2.232681] uhci_hcd 0000:00:1d.0: irq 23, io base 0x00001800
[    2.232790] usb usb2: configuration #1 chosen from 1 choice
[    2.232851] hub 2-0:1.0: USB hub found
[    2.232893] hub 2-0:1.0: 2 ports detected
[    2.233009] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    2.233053] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    2.233056] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    2.233132] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 3
[    2.233206] uhci_hcd 0000:00:1d.1: irq 19, io base 0x00001820
[    2.233316] usb usb3: configuration #1 chosen from 1 choice
[    2.233379] hub 3-0:1.0: USB hub found
[    2.233420] hub 3-0:1.0: 2 ports detected
[    2.233531] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    2.233574] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    2.233578] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    2.233656] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 4
[    2.233727] uhci_hcd 0000:00:1d.2: irq 18, io base 0x00001840
[    2.233836] usb usb4: configuration #1 chosen from 1 choice
[    2.233898] hub 4-0:1.0: USB hub found
[    2.233945] hub 4-0:1.0: 2 ports detected
[    2.234060] uhci_hcd 0000:00:1d.3: PCI INT D -> GSI 16 (level, low) -> IRQ 16
[    2.234103] uhci_hcd 0000:00:1d.3: setting latency timer to 64
[    2.234107] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[    2.234190] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 5
[    2.234264] uhci_hcd 0000:00:1d.3: irq 16, io base 0x00001860
[    2.234371] usb usb5: configuration #1 chosen from 1 choice
[    2.234435] hub 5-0:1.0: USB hub found
[    2.234476] hub 5-0:1.0: 2 ports detected
[    2.234646] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    2.237877] serio: i8042 KBD port at 0x60,0x64 irq 1
[    2.237919] serio: i8042 AUX port at 0x60,0x64 irq 12
[    2.238067] mice: PS/2 mouse device common for all mice
[    2.238319] rtc_cmos 00:06: rtc core: registered rtc_cmos as rtc0
[    2.238380] rtc0: alarms up to one month, y3k, 242 bytes nvram, hpet irqs
[    2.238479] device-mapper: uevent: version 1.0.3
[    2.238618] device-mapper: ioctl: 4.14.0-ioctl (2008-04-23) initialised: dm-devel@redhat.com
[    2.238710] device-mapper: multipath: version 1.0.5 loaded
[    2.238749] device-mapper: multipath round-robin: version 1.0.0 loaded
[    2.238863] EISA: Probing bus 0 at eisa.0
[    2.238904] Cannot allocate resource for EISA slot 1
[    2.238943] Cannot allocate resource for EISA slot 2
[    2.238981] Cannot allocate resource for EISA slot 3
[    2.239019] Cannot allocate resource for EISA slot 4
[    2.239069] EISA: Detected 0 cards.
[    2.239181] cpuidle: using governor ladder
[    2.239296] cpuidle: using governor menu
[    2.239838] TCP cubic registered
[    2.239973] NET: Registered protocol family 10
[    2.240430] lo: Disabled Privacy Extensions
[    2.240782] NET: Registered protocol family 17
[    2.240834] Bluetooth: L2CAP ver 2.11
[    2.240871] Bluetooth: L2CAP socket layer initialized
[    2.240909] Bluetooth: SCO (Voice Link) ver 0.6
[    2.240947] Bluetooth: SCO socket layer initialized
[    2.241007] Bluetooth: RFCOMM socket layer initialized
[    2.241050] Bluetooth: RFCOMM TTY layer initialized
[    2.241088] Bluetooth: RFCOMM ver 1.10
[    2.241394] Using IPI No-Shortcut mode
[    2.241504] registered taskstats version 1
[    2.241664]   Magic number: 1:103:55
[    2.241769] rtc_cmos 00:06: setting system clock to 2009-07-05 02:04:30 UTC (1246759470)
[    2.241817] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    2.241856] EDD information not available.
[    2.242162] Freeing unused kernel memory: 532k freed
[    2.242315] Write protecting the kernel text: 4112k
[    2.242393] Write protecting the kernel read-only data: 1524k
[    2.284867] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input5
[    2.489354] ohci1394 0000:06:01.2: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    2.539174] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[18]  MMIO=[c8217000-c82177ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[    2.553790] tg3.c:v3.94 (August 14, 2008)
[    2.553850] tg3 0000:06:08.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    2.644076] eth0: Tigon3 [partno(BCM95705A50) rev 3003 PHY(5705)] (PCI:33MHz:32-bit) 10/100/1000Base-T Ethernet 00:c0:9f:c7:9d:6f
[    2.644133] eth0: RXcsums[1] LinkChgREG[0] MIirq[0] ASF[0] WireSpeed[0] TSOcap[1]
[    2.644180] eth0: dma_rwctrl[763f0000] dma_mask[32-bit]
[    2.840023] usb 5-1: new low speed USB device using uhci_hcd and address 2
[    2.840090] Marking TSC unstable due to TSC halts in idle
[    3.000204] Clocksource tsc unstable (delta = -192583199 ns)
[    3.015344] usb 5-1: configuration #1 chosen from 1 choice
[    3.042505] usbcore: registered new interface driver hiddev
[    3.067920] generic-usb: probe of 0003:147A:E02C.0001 failed with error -22
[    3.068648] usbcore: registered new interface driver usbhid
[    3.068688] usbhid: v2.6:USB HID core driver
[    3.272369] usb 5-2: new low speed USB device using uhci_hcd and address 3
[    3.352653] PM: Starting manual resume from disk
[    3.352692] PM: Resume from partition 8:5
[    3.352694] PM: Checking hibernation image.
[    3.352900] PM: Resume from disk failed.
[    3.385224] kjournald starting.  Commit interval 5 seconds
[    3.385271] EXT3-fs: mounted filesystem with ordered data mode.
[    3.450688] usb 5-2: configuration #1 chosen from 1 choice
[    3.467023] input: Genius       NetScroll+Mini Traveler as /devices/pci0000:00/0000:00:1d.3/usb5/5-2/5-2:1.0/input/input6
[    3.471319] generic-usb 0003:0458:0036.0002: input,hidraw0: USB HID v1.10 Mouse [Genius       NetScroll+Mini Traveler] on usb-0000:00:1d.3-2/input0
[    3.824470] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[00c09f0000683909]
[   10.640926] udev: starting version 141
[   11.286547] irda_init()
[   11.286561] NET: Registered protocol family 23
[   11.288804] intel_rng: FWH not detected
[   12.069470] acer-wmi: Acer Laptop ACPI-WMI Extras
[   12.069528] acer-wmi: No or unsupported WMI interface, unable to load
[   12.127718] ieee80211_crypt: registered algorithm 'NULL'
[   12.132320] ieee80211: 802.11 data/management/control stack, git-1.1.13
[   12.132364] ieee80211: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
[   12.187141] input: PC Speaker as /devices/platform/pcspkr/input/input7
[   12.254371] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:01/device:02/input/input8
[   12.256806] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[   12.272164] Linux agpgart interface v0.103
[   12.295993] yenta_cardbus 0000:06:01.0: CardBus bridge found [1025:0066]
[   12.296062] yenta_cardbus 0000:06:01.0: Using CSCINT to route CSC interrupts to PCI
[   12.296109] yenta_cardbus 0000:06:01.0: Routing CardBus interrupts to PCI
[   12.296152] yenta_cardbus 0000:06:01.0: TI: mfunc 0x01c21b22, devctl 0x64
[   12.394103] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.2.2kmprq
[   12.394155] ipw2200: Copyright(c) 2003-2006 Intel Corporation
[   12.403783] nsc_ircc_pnp_probe() : From PnP, found firbase 0x3F8 ; irq 3 ; dma 1.
[   12.403810] nsc-ircc, chip->init
[   12.403859] nsc-ircc, Found chip at base=0x164e
[   12.403898] nsc-ircc, Wrong chip version ff
[   12.403964] nsc-ircc, Found chip at base=0x164e
[   12.404024] nsc-ircc, Wrong chip version ff
[   12.404386] nsc-ircc 00:07: disabled
[   12.422555] iTCO_vendor_support: vendor-support=0
[   12.424888] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.05
[   12.425090] iTCO_wdt: Found a ICH6-M TCO device (Version=2, TCOBASE=0x1060)
[   12.425212] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   12.443529] Linux video capture interface: v2.00
[   12.452027] synaptics was reset on resume, see synaptics_resume_reset if you have trouble on resume
[   12.532907] yenta_cardbus 0000:06:01.0: ISA IRQ mask 0x0cf8, PCI irq 18
[   12.532954] yenta_cardbus 0000:06:01.0: Socket status: 30000006
[   12.532995] pci_bus 0000:06: Raising subordinate bus# of parent bus (#06) from #07 to #08
[   12.533048] yenta_cardbus 0000:06:01.0: pcmcia: parent PCI bridge I/O window: 0x4000 - 0x4fff
[   12.533096] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x4000-0x4fff: clean.
[   12.533401] yenta_cardbus 0000:06:01.0: pcmcia: parent PCI bridge Memory window: 0xc8200000 - 0xc82fffff
[   12.533450] yenta_cardbus 0000:06:01.0: pcmcia: parent PCI bridge Memory window: 0x88000000 - 0x8bffffff
[   12.534861] tifm_7xx1 0000:06:01.3: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[   12.535112] ipw2200 0000:06:03.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   12.536220] ipw2200: Detected Intel PRO/Wireless 2200BG Network Connection
[   12.536335] ipw2200 0000:06:03.0: firmware: requesting ipw2200-bss.fw
[   12.548140] saa7130/34: v4l2 driver version 0.2.14 loaded
[   12.798244] ipw2200: Detected geography ZZM (11 802.11bg channels, 0 802.11a channels)
[   12.798336] saa7134 0000:06:02.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   12.798381] saa7133[0]: found at 0000:06:02.0, rev: 209, irq: 17, latency: 32, mmio: 0xc8217800
[   12.798434] saa7133[0]: subsystem: 1461:a836, board: Avermedia M115 [card=138,autodetected]
[   12.798568] saa7133[0]: board init: gpio is a400000
[   12.922736] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x100-0x3af: clean.
[   12.924019] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x3e0-0x4ff: excluding 0x4d0-0x4d7
[   12.924648] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x820-0x8ff: clean.
[   12.925136] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xc00-0xcf7: clean.
[   12.925769] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xa00-0xaff: clean.
[   12.983340] saa7133[0]: i2c eeprom 00: 61 14 36 a8 00 00 00 00 00 00 00 00 00 00 00 00
[   12.983842] saa7133[0]: i2c eeprom 10: ff ff ff ff ff 20 ff ff ff ff ff ff ff ff ff ff
[   12.984350] saa7133[0]: i2c eeprom 20: 01 40 01 02 02 01 01 03 08 ff 00 c0 ff ff ff ff
[   12.984846] saa7133[0]: i2c eeprom 30: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   12.985341] saa7133[0]: i2c eeprom 40: ff 65 00 ff c2 1e ff ff ff ff ff ff ff ff ff ff
[   12.985837] saa7133[0]: i2c eeprom 50: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   12.986333] saa7133[0]: i2c eeprom 60: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   12.986831] saa7133[0]: i2c eeprom 70: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   12.987411] saa7133[0]: i2c eeprom 80: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   12.987917] saa7133[0]: i2c eeprom 90: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   12.988431] saa7133[0]: i2c eeprom a0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   12.988945] saa7133[0]: i2c eeprom b0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   12.989441] saa7133[0]: i2c eeprom c0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   12.989937] saa7133[0]: i2c eeprom d0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   12.990433] saa7133[0]: i2c eeprom e0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   12.990929] saa7133[0]: i2c eeprom f0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   12.996830] Intel ICH 0000:00:1e.2: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   12.996932] Intel ICH 0000:00:1e.2: setting latency timer to 64
[   13.024336] tuner' 0-0061: chip found @ 0xc2 (saa7133[0])
[   13.079098] xc2028 0-0061: creating new instance
[   13.079140] xc2028 0-0061: type set to XCeive xc2028/xc3028 tuner
[   13.079192] BUG: unable to handle kernel paging request at fffffff4
[   13.079284] IP: [<f7eb32c0>] saa7134_board_init2+0x140/0x710 [saa7134]
[   13.079362] *pde = 007b7067 *pte = 00000000 
[   13.079454] Oops: 0000 [#1] SMP 
[   13.079543] last sysfs file: /sys/module/videodev/initstate
[   13.079583] Dumping ftrace buffer:
[   13.079620]    (ftrace buffer empty)
[   13.079657] Modules linked in: tuner_xc2028 tuner snd_intel8x0(+) snd_ac97_codec ac97_bus snd_pcm_oss snd_mixer_oss snd_pcm snd_seq_dummy snd_seq_oss snd_seq_midi snd_rawmidi pcmcia snd_seq_midi_event saa7134(+) snd_seq snd_timer snd_seq_device ir_common videodev v4l1_compat compat_ioctl32 intel_agp iTCO_wdt iTCO_vendor_support ipw2200 psmouse snd soundcore v4l2_common videobuf_dma_sg videobuf_core tifm_7xx1 yenta_socket rsrc_nonstatic agpgart video pcspkr ieee80211 ieee80211_crypt serio_raw snd_page_alloc led_class tveeprom tifm_core pcmcia_core output irda crc_ccitt usbhid tg3 ohci1394 ieee1394 fbcon tileblit font bitblit softcursor
[   13.081359] 
[   13.081395] Pid: 1581, comm: modprobe Not tainted (2.6.28-13-generic #45-Ubuntu) Aspire 5510     
[   13.081443] EIP: 0060:[<f7eb32c0>] EFLAGS: 00010292 CPU: 0
[   13.081488] EIP is at saa7134_board_init2+0x140/0x710 [saa7134]
[   13.081527] EAX: 00000000 EBX: 00000000 ECX: 00000000 EDX: 00000000
[   13.081566] ESI: 00000000 EDI: 00000000 EBP: 00000000 ESP: f670fc54
[   13.081606]  DS: 007b ES: 007b FS: 00d8 GS: 0033 SS: 0068
[   13.081645] Process modprobe (pid: 1581, ti=f670e000 task=f6106480 task.ti=f670e000)
[   13.081691] Stack:
[   13.081726]  00000303 f670fc58 f670fc58 f6263000 f6f97000 f6263000 f670fcd0 c014ade7
[   13.081952]  000000d0 f7eb5889 656e7574 00000072 000000f0 f62634b0 00000000 f6263140
[   13.082224]  f7ebf490 f62634b0 f670fcd0 f7eb594d 65626f72 642d7000 006d6561 0000062d
[   13.082224] Call Trace:
[   13.082224]  [<c014ade7>] ? request_module+0x97/0xf0
[   13.082224]  [<f7eb5889>] ? saa7134_i2c_eeprom+0xe9/0x110 [saa7134]
[   13.082224]  [<f7eb594d>] ? saa7134_i2c_register+0x9d/0x120 [saa7134]
[   13.082224]  [<f7ebe5fc>] ? saa7134_initdev+0x3cc/0x8d5 [saa7134]
[   13.082224]  [<c02dc60e>] ? pci_device_probe+0x5e/0x80
[   13.082224]  [<c034f214>] ? really_probe+0x54/0x180
[   13.082224]  [<c02dbe3e>] ? pci_match_device+0xbe/0xd0
[   13.082224]  [<c04fe314>] ? __down+0x64/0x90
[   13.082224]  [<c034f37e>] ? driver_probe_device+0x3e/0x50
[   13.082224]  [<c034f419>] ? __driver_attach+0x89/0x90
[   13.082224]  [<c034eb53>] ? bus_for_each_dev+0x53/0x80
[   13.082224]  [<c02dc550>] ? pci_device_remove+0x0/0x40
[   13.082224]  [<c034f0d9>] ? driver_attach+0x19/0x20
[   13.082224]  [<c034f390>] ? __driver_attach+0x0/0x90
[   13.082224]  [<c034e527>] ? bus_add_driver+0x1c7/0x240
[   13.082224]  [<c02dc550>] ? pci_device_remove+0x0/0x40
[   13.082224]  [<c034f5b9>] ? driver_register+0x69/0x140
[   13.082224]  [<f7eb5240>] ? saa7134_init+0x0/0x60 [saa7134]
[   13.082224]  [<c02dc86a>] ? __pci_register_driver+0x4a/0x90
[   13.082224]  [<f7eb5240>] ? saa7134_init+0x0/0x60 [saa7134]
[   13.082224]  [<f7eb5292>] ? saa7134_init+0x52/0x60 [saa7134]
[   13.082224]  [<c010111e>] ? _stext+0x2e/0x170
[   13.082224]  [<c020c0b5>] ? sysfs_addrm_finish+0x15/0xf0
[   13.082224]  [<c020b883>] ? sysfs_add_one+0x13/0x50
[   13.082224]  [<c020b8ff>] ? sysfs_addrm_start+0x3f/0xa0
[   13.082224]  [<c01a90ac>] ? __vunmap+0x9c/0xe0
[   13.082224]  [<c0127c8d>] ? update_curr+0x8d/0x1e0
[   13.082224]  [<c02ca43a>] ? rb_insert_color+0xca/0x100
[   13.082224]  [<c012c6fc>] ? enqueue_entity+0x13c/0x360
[   13.082224]  [<c0131bfe>] ? resched_task+0x1e/0x70
[   13.082224]  [<c0133b74>] ? try_to_wake_up+0x104/0x290
[   13.082224]  [<c0163fe8>] ? sys_init_module+0x88/0x1b0
[   13.082224]  [<c0103f6b>] ? sysenter_do_call+0x12/0x2f
[   13.082224]  [<c04f0000>] ? quirk_isa_dma_hangs+0x39/0x46
[   13.082224] Code: 45 99 64 c8 8b 55 90 8b 82 2c 01 00 00 89 5c 24 04 c7 04 24 b8 03 ec f7 89 44 24 08 e8 28 99 64 c8 66 90 8b 45 90 e8 40 fd ff ff <8b> 5d f4 31 c0 8b 75 f8 8b 7d fc 89 ec 5d c3 90 8b 4d 90 8b 71 
[   13.082224] EIP: [<f7eb32c0>] saa7134_board_init2+0x140/0x710 [saa7134] SS:ESP 0068:f670fc54
[   13.082224] ---[ end trace d26172850f2b3a4c ]---
[   13.316200] intel8x0_measure_ac97_clock: measured 53977 usecs
[   13.316242] intel8x0: clocking to 48000
[   13.318130] Synaptics Touchpad, model: 1, fw: 6.2, id: 0x12a0b1, caps: 0xa04713/0x204000
[   13.357287] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input9
[  191.193572] lp: driver loaded but no devices found
[  191.248574] Adding 1052220k swap on /dev/sda5.  Priority:-1 extents:1 across:1052220k
[  191.773563] EXT3 FS on sda6, internal journal
[  192.603476] type=1505 audit(1246756060.858:2): operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" name2="default" pid=2038
[  192.658914] type=1505 audit(1246756060.914:3): operation="profile_load" name="/sbin/dhclient-script" name2="default" pid=2042
[  192.659036] type=1505 audit(1246756060.914:4): operation="profile_load" name="/sbin/dhclient3" name2="default" pid=2042
[  192.659085] type=1505 audit(1246756060.914:5): operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" name2="default" pid=2042
[  192.659132] type=1505 audit(1246756060.914:6): operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" name2="default" pid=2042
[  192.822511] type=1505 audit(1246756061.078:7): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=2047
[  192.822768] type=1505 audit(1246756061.078:8): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=2047
[  192.853938] type=1505 audit(1246756061.110:9): operation="profile_load" name="/usr/sbin/tcpdump" name2="default" pid=2051
[  196.596766] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[  196.596770] Bluetooth: BNEP filters: protocol multicast
[  196.619353] Bridge firewalling registered
[  198.012560] pci 0000:01:00.0: power state changed by ACPI to D0
[  198.012572] pci 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[  198.130415] ppdev: user-space parallel port driver
[  198.342081] [drm] Initialized drm 1.1.0 20060810
[  198.471192] pci 0000:01:00.0: setting latency timer to 64
[  198.471356] [drm] Initialized radeon 1.29.0 20080528 on minor 0
[  199.146086] [drm] Setting GART location based on new memory map
[  199.147763] [drm] Loading R400 Microcode
[  199.147806] [drm] Num pipes: 2
[  199.147812] [drm] writeback test succeeded in 1 usecs
[  202.012355] ADDRCONF(NETDEV_UP): eth0: link is not ready
[  202.499344] ieee80211_crypt: registered algorithm 'TKIP'
[  212.440207] eth1: no IPv6 routers present
[  224.112603] CPU0 attaching NULL sched-domain.
[  224.114357] CPU0 attaching NULL sched-domain.
[  550.371215] synaptics: using relaxed packet validation
=========================================

---

### Post by earthpigg on 2009-07-04
have you tried disabling things you dont need in system->preferences->startup applications?

some of them have obvious names... others, google search to see what it is, and if you need it. uncheck what you dont need it.

---

### Post by manikanthm on 2009-07-05
I doubt its the start up applications, since i dont think its getting to that stage when the lag occurs.

For more information, i have attached the bootchart image...

---

