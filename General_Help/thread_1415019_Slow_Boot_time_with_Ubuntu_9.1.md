---
title: "Slow Boot time with Ubuntu 9.1"
date: 2010-02-24
forum: General Help
---

### Post by GerryEgan on 2010-02-24
Hello,

I currently have Ubuntu 9.1 (32bit) installed on an AMD 64 processor with 1GB of ram. its got a Nvidia geforce 6800gs and two monitors attached (both working as expected). I installed 9.1 on the same system 2 months ago but the hard disk died (what luck!) so now I'm starting again. Unfortunately the boot time on the new install is very very long, it takes on average 5+ minutes to get from the grub screen to the login prompt. It takes Windows 7 just over one minute to do the same! Something must be terribly wrong. I have gone through the startup applications GUI and disabled a lot of the items in there that i was sure I didn't need. 

There are a number of messages being displayed during boot time that were not displayed when I had Ubuntu running before the disk crash. Ubuntu is now running on a separate disk as the other one is kaput.

After Grub I get a flashing underscore for about 100 seconds. then the white Ubuntu logo appears for about 20 seconds. Once this goes away I get a series of messages that describe a few things starting up. I jotted down some of the messages displayed, here is what I have:

Fsck running?
dev/sda5/ clean (some numbers here) blocks
starting apparmour
starting mysqld....
checking for corrupt tables and tables that were not closed cleanly?
running dkms auto install service something something nvidia

after that I get what looks like an error message in the form of 
240.409.071 Info: task modprobe:620 blocked for more than 120 seconds
echo 0 > /proc/sys/kernel/hung_task_cursor_timeout

This error is repeated many times with the number at the start of the error changing.

Does anybody have any ideas? I'm really only getting used to Linux so I'm not sure where to start. I have attached a copy of my bootchart png so you can see in more detail what is going on at startup. I would really appreciate any help or pointers you may have on this!!

I have run all the updates available and installed amarok, ms office(I have no choice!) and VLC but the problem was there post install and didn't change after the updates.

Gerry

---

### Post by GerryEgan on 2010-02-24
The Attached Image is so compressed by the forum that it is impossible to make out. [here is a link]("http://img94.imageshack.us/img94/9953/gerrydesktopkarmic20100.png") to a copy on imageshack.us

Gerry

---

### Post by GerryEgan on 2010-03-09
Hello there,

I am still having this problem and have been looking through the forums trying to find an answer! no luck yet though, attached is the result of the command dmesg:


```
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.31-20-generic (buildd@rothera) (gcc version 4.4.1 (Ubuntu 4.4.1-4ubuntu9) ) #57-Ubuntu SMP Mon Feb 8 09:05:19 UTC 2010 (Ubuntu 2.6.31-20.57-generic)
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
[    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000003fff0000 (usable)
[    0.000000]  BIOS-e820: 000000003fff0000 - 000000003fff3000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000003fff3000 - 0000000040000000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 0000000100000000 (reserved)
[    0.000000] DMI 2.3 present.
[    0.000000] Phoenix BIOS detected: BIOS may corrupt low RAM, working around it.
[    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
[    0.000000] last_pfn = 0x3fff0 max_arch_pfn = 0x100000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-C7FFF write-protect
[    0.000000]   C8000-FFFFF uncachable
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 0000000000 mask FFC0000000 write-back
[    0.000000]   1 disabled
[    0.000000]   2 disabled
[    0.000000]   3 disabled
[    0.000000]   4 disabled
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] Scanning 0 areas for low memory corruption
[    0.000000] modified physical RAM map:
[    0.000000]  modified: 0000000000000000 - 0000000000010000 (reserved)
[    0.000000]  modified: 0000000000010000 - 000000000009f800 (usable)
[    0.000000]  modified: 000000000009f800 - 00000000000a0000 (reserved)
[    0.000000]  modified: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  modified: 0000000000100000 - 000000003fff0000 (usable)
[    0.000000]  modified: 000000003fff0000 - 000000003fff3000 (ACPI NVS)
[    0.000000]  modified: 000000003fff3000 - 0000000040000000 (ACPI data)
[    0.000000]  modified: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  modified: 00000000fec00000 - 0000000100000000 (reserved)
[    0.000000] initial memory mapped : 0 - 00c00000
[    0.000000] init_memory_mapping: 0000000000000000-00000000377fe000
[    0.000000] Using x86 segment limits to approximate NX protection
[    0.000000]  0000000000 - 0000400000 page 4k
[    0.000000]  0000400000 - 0037400000 page 2M
[    0.000000]  0037400000 - 00377fe000 page 4k
[    0.000000] kernel direct mapping tables up to 377fe000 @ 10000-15000
[    0.000000] RAMDISK: 2f8e7000 - 30033194
[    0.000000] ACPI: RSDP 000f7c60 00014 (v00 Nvidia)
[    0.000000] ACPI: RSDT 3fff3040 00030 (v01 Nvidia AWRDACPI 42302E31 AWRD 00000000)
[    0.000000] ACPI: FACP 3fff30c0 00074 (v01 Nvidia AWRDACPI 42302E31 AWRD 00000000)
[    0.000000] ACPI: DSDT 3fff3180 06A16 (v01 NVIDIA AWRDACPI 00001000 MSFT 0100000E)
[    0.000000] ACPI: FACS 3fff0000 00040
[    0.000000] ACPI: MCFG 3fff9cc0 0003C (v01 Nvidia AWRDACPI 42302E31 AWRD 00000000)
[    0.000000] ACPI: APIC 3fff9c00 0007C (v01 Nvidia AWRDACPI 42302E31 AWRD 00000000)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] 135MB HIGHMEM available.
[    0.000000] 887MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 377fe000
[    0.000000]   low ram: 0 - 377fe000
[    0.000000]   node 0 low ram: 00000000 - 377fe000
[    0.000000]   node 0 bootmap 00011000 - 00017f00
[    0.000000] (9 early reservations) ==> bootmem [0000000000 - 00377fe000]
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
[    0.000000]   #1 [0000001000 - 0000002000]    EX TRAMPOLINE ==> [0000001000 - 0000002000]
[    0.000000]   #2 [0000006000 - 0000007000]       TRAMPOLINE ==> [0000006000 - 0000007000]
[    0.000000]   #3 [0000100000 - 00008ad060]    TEXT DATA BSS ==> [0000100000 - 00008ad060]
[    0.000000]   #4 [002f8e7000 - 0030033194]          RAMDISK ==> [002f8e7000 - 0030033194]
[    0.000000]   #5 [000009f800 - 0000100000]    BIOS reserved ==> [000009f800 - 0000100000]
[    0.000000]   #6 [00008ae000 - 00008b115d]              BRK ==> [00008ae000 - 00008b115d]
[    0.000000]   #7 [0000010000 - 0000011000]          PGTABLE ==> [0000010000 - 0000011000]
[    0.000000]   #8 [0000011000 - 0000018000]          BOOTMAP ==> [0000011000 - 0000018000]
[    0.000000] found SMP MP-table at [c00f5880] f5880
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000010 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x000377fe
[    0.000000]   HighMem  0x000377fe -> 0x0003fff0
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[2] active PFN ranges
[    0.000000]     0: 0x00000010 -> 0x0000009f
[    0.000000]     0: 0x00000100 -> 0x0003fff0
[    0.000000] On node 0 totalpages: 262015
[    0.000000] free_area_init_node: node 0, pgdat c0788920, node_mem_map c1000200
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3951 pages, LIFO batch:0
[    0.000000]   Normal zone: 1744 pages used for memmap
[    0.000000]   Normal zone: 221486 pages, LIFO batch:31
[    0.000000]   HighMem zone: 272 pages used for memmap
[    0.000000]   HighMem zone: 34530 pages, LIFO batch:7
[    0.000000] Using APIC driver default
[    0.000000] Nvidia board detected. Ignoring ACPI timer override.
[    0.000000] If you got timer trouble try acpi_use_timer_override
[    0.000000] ACPI: PM-Timer IO Port: 0x4008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] disabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 17, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: BIOS IRQ0 pin2 override ignored.
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 14 global_irq 14 high edge)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 15 global_irq 15 high edge)
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] ACPI: IRQ14 used by override.
[    0.000000] ACPI: IRQ15 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] SMP: Allowing 2 CPUs, 1 hotplug CPUs
[    0.000000] nr_irqs_gsi: 24
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000f0000
[    0.000000] PM: Registered nosave memory: 00000000000f0000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 40000000 (gap: 40000000:a0000000)
[    0.000000] NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:2 nr_node_ids:1
[    0.000000] PERCPU: Embedded 14 pages at c1805000, static data 35612 bytes
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 259967
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.31-20-generic root=UUID=1b92728c-0926-46ec-9717-4fce874faec9 ro quiet splash
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] allocated 5242240 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] Initializing HighMem for node 0 (000377fe:0003fff0)
[    0.000000] Memory: 1017988k/1048512k available (4579k kernel code, 29612k reserved, 2145k data, 540k init, 139208k highmem)
[    0.000000] virtual kernel memory layout:
[    0.000000]     fixmap  : 0xfff1d000 - 0xfffff000   ( 904 kB)
[    0.000000]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[    0.000000]     vmalloc : 0xf7ffe000 - 0xff7fe000   ( 120 MB)
[    0.000000]     lowmem  : 0xc0000000 - 0xf77fe000   ( 887 MB)
[    0.000000]       .init : 0xc0792000 - 0xc0819000   ( 540 kB)
[    0.000000]       .data : 0xc0578c68 - 0xc0791448   (2145 kB)
[    0.000000]       .text : 0xc0100000 - 0xc0578c68   (4579 kB)
[    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.000000] SLUB: Genslabs=13, HWalign=64, Order=0-3, MinObjects=0, CPUs=2, Nodes=1
[    0.000000] NR_IRQS:2304 nr_irqs:424
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 2412.780 MHz processor.
[    0.000011] spurious 8259A interrupt: IRQ7.
[    0.001409] Console: colour VGA+ 80x25
[    0.001412] console [tty0] enabled
[    0.004009] Calibrating delay loop (skipped), value calculated using timer frequency.. 4825.56 BogoMIPS (lpj=9651120)
[    0.004037] Security Framework initialized
[    0.004061] AppArmor: AppArmor initialized
[    0.004068] Mount-cache hash table entries: 512
[    0.004223] Initializing cgroup subsys ns
[    0.004227] Initializing cgroup subsys cpuacct
[    0.004231] Initializing cgroup subsys memory
[    0.004237] Initializing cgroup subsys freezer
[    0.004239] Initializing cgroup subsys net_cls
[    0.004252] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[    0.004255] CPU: L2 Cache: 1024K (64 bytes/line)
[    0.004259] mce: CPU supports 5 MCE banks
[    0.004278] Performance Counters: AMD PMU driver.
[    0.004284] ... version:                 0
[    0.004286] ... bit width:               48
[    0.004287] ... generic counters:        4
[    0.004289] ... value mask:              0000ffffffffffff
[    0.004291] ... max period:              00007fffffffffff
[    0.004292] ... fixed-purpose counters:  0
[    0.004294] ... counter mask:            000000000000000f
[    0.004298] Checking 'hlt' instruction... OK.
[    0.020639] SMP alternatives: switching to UP code
[    0.025647] ACPI: Core revision 20090521
[    0.036357] ..TIMER: vector=0x30 apic1=0 pin1=0 apic2=-1 pin2=-1
[    0.044001] ..MP-BIOS bug: 8254 timer not connected to IO-APIC
[    0.044001] ...trying to set up timer (IRQ0) through the 8259A ...
[    0.044001] ..... (found apic 0 pin 0) ...
[    0.052001] ....... failed.
[    0.052001] ...trying to set up timer as Virtual Wire IRQ...
[    0.052001] ..... failed.
[    0.052001] ...trying to set up timer as ExtINT IRQ...
[    0.094518] ..... works.
[    0.094519] CPU0: AMD Athlon(tm) 64 Processor 4000+ stepping 01
[    0.096001] Brought up 1 CPUs
[    0.096001] Total of 1 processors activated (4825.56 BogoMIPS).
[    0.096001] CPU0 attaching NULL sched-domain.
[    0.096001] Booting paravirtualized kernel on bare hardware
[    0.096001] regulator: core version 0.5
[    0.096001] Time: 17:12:32  Date: 03/09/10
[    0.096001] NET: Registered protocol family 16
[    0.096001] EISA bus registered
[    0.096001] ACPI: bus type pci registered
[    0.096001] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 255
[    0.096001] PCI: MCFG area at e0000000 reserved in E820
[    0.096001] PCI: Using MMCONFIG for extended config space
[    0.096001] PCI: Using configuration type 1 for base access
[    0.096001] bio: create slab <bio-0> at 0
[    0.096001] ACPI: EC: Look up EC in DSDT
[    0.102364] ACPI: Interpreter enabled
[    0.102369] ACPI: (supports S0 S1 S3 S4 S5)
[    0.102391] ACPI: Using IOAPIC for interrupt routing
[    0.109323] ACPI: No dock devices found.
[    0.109412] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.109504] HPET not enabled in BIOS. You might try hpet=force boot option
[    0.109520] pci 0000:00:01.1: reg 10 io port: [0xdc00-0xdc1f]
[    0.109527] pci 0000:00:01.1: reg 20 io port: [0x4c00-0x4c3f]
[    0.109531] pci 0000:00:01.1: reg 24 io port: [0x4c40-0x4c7f]
[    0.109540] pci 0000:00:01.1: PME# supported from D3hot D3cold
[    0.109543] pci 0000:00:01.1: PME# disabled
[    0.109561] pci 0000:00:02.0: reg 10 32bit mmio: [0xc5003000-0xc5003fff]
[    0.109576] pci 0000:00:02.0: supports D1 D2
[    0.109578] pci 0000:00:02.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.109581] pci 0000:00:02.0: PME# disabled
[    0.109598] pci 0000:00:02.1: reg 10 32bit mmio: [0xfeb00000-0xfeb000ff]
[    0.109616] pci 0000:00:02.1: supports D1 D2
[    0.109618] pci 0000:00:02.1: PME# supported from D0 D1 D2 D3hot D3cold
[    0.109621] pci 0000:00:02.1: PME# disabled
[    0.109646] pci 0000:00:06.0: reg 20 io port: [0xf000-0xf00f]
[    0.109668] pci 0000:00:07.0: reg 10 io port: [0x9f0-0x9f7]
[    0.109671] pci 0000:00:07.0: reg 14 io port: [0xbf0-0xbf3]
[    0.109675] pci 0000:00:07.0: reg 18 io port: [0x970-0x977]
[    0.109678] pci 0000:00:07.0: reg 1c io port: [0xb70-0xb73]
[    0.109682] pci 0000:00:07.0: reg 20 io port: [0xd800-0xd80f]
[    0.109685] pci 0000:00:07.0: reg 24 32bit mmio: [0xc5002000-0xc5002fff]
[    0.109705] pci 0000:00:08.0: reg 10 io port: [0x9e0-0x9e7]
[    0.109709] pci 0000:00:08.0: reg 14 io port: [0xbe0-0xbe3]
[    0.109712] pci 0000:00:08.0: reg 18 io port: [0x960-0x967]
[    0.109715] pci 0000:00:08.0: reg 1c io port: [0xb60-0xb63]
[    0.109719] pci 0000:00:08.0: reg 20 io port: [0xc400-0xc40f]
[    0.109723] pci 0000:00:08.0: reg 24 32bit mmio: [0xc5001000-0xc5001fff]
[    0.109753] pci 0000:00:0a.0: reg 10 32bit mmio: [0xc5000000-0xc5000fff]
[    0.109756] pci 0000:00:0a.0: reg 14 io port: [0xb000-0xb007]
[    0.109770] pci 0000:00:0a.0: supports D1 D2
[    0.109772] pci 0000:00:0a.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.109775] pci 0000:00:0a.0: PME# disabled
[    0.109800] pci 0000:00:0b.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.109803] pci 0000:00:0b.0: PME# disabled
[    0.109829] pci 0000:00:0c.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.109831] pci 0000:00:0c.0: PME# disabled
[    0.109857] pci 0000:00:0d.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.109859] pci 0000:00:0d.0: PME# disabled
[    0.109886] pci 0000:00:0e.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.109888] pci 0000:00:0e.0: PME# disabled
[    0.109978] pci 0000:05:06.0: reg 10 io port: [0x9000-0x903f]
[    0.110003] pci 0000:05:06.0: supports D1 D2
[    0.110023] pci 0000:05:06.1: reg 10 io port: [0x9400-0x9407]
[    0.110048] pci 0000:05:06.1: supports D1 D2
[    0.110069] pci 0000:05:06.2: reg 10 32bit mmio: [0xc4008000-0xc40087ff]
[    0.110075] pci 0000:05:06.2: reg 14 32bit mmio: [0xc4000000-0xc4003fff]
[    0.110099] pci 0000:05:06.2: supports D1 D2
[    0.110101] pci 0000:05:06.2: PME# supported from D0 D1 D2 D3hot
[    0.110104] pci 0000:05:06.2: PME# disabled
[    0.110130] pci 0000:05:0a.0: reg 10 io port: [0x9800-0x9807]
[    0.110135] pci 0000:05:0a.0: reg 14 io port: [0x9c00-0x9c03]
[    0.110139] pci 0000:05:0a.0: reg 18 io port: [0xa000-0xa007]
[    0.110144] pci 0000:05:0a.0: reg 1c io port: [0xa400-0xa403]
[    0.110149] pci 0000:05:0a.0: reg 20 io port: [0xa800-0xa80f]
[    0.110153] pci 0000:05:0a.0: reg 24 32bit mmio: [0xc4009000-0xc40093ff]
[    0.110158] pci 0000:05:0a.0: reg 30 32bit mmio: [0xc3000000-0xc307ffff]
[    0.110169] pci 0000:05:0a.0: supports D1 D2
[    0.110194] pci 0000:05:0c.0: reg 10 32bit mmio: [0xc4004000-0xc4007fff]
[    0.110199] pci 0000:05:0c.0: reg 14 io port: [0xac00-0xacff]
[    0.110214] pci 0000:05:0c.0: reg 30 32bit mmio: [0xc3000000-0xc301ffff]
[    0.110227] pci 0000:05:0c.0: supports D1 D2
[    0.110229] pci 0000:05:0c.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.110232] pci 0000:05:0c.0: PME# disabled
[    0.110251] pci 0000:00:09.0: transparent bridge
[    0.110254] pci 0000:00:09.0: bridge io port: [0x9000-0xafff]
[    0.110257] pci 0000:00:09.0: bridge 32bit mmio: [0xc3000000-0xc4ffffff]
[    0.110363] pci 0000:01:00.0: reg 10 32bit mmio: [0xc0000000-0xc0ffffff]
[    0.110370] pci 0000:01:00.0: reg 14 64bit mmio: [0xa0000000-0xbfffffff]
[    0.110376] pci 0000:01:00.0: reg 1c 64bit mmio: [0xc1000000-0xc1ffffff]
[    0.110383] pci 0000:01:00.0: reg 30 32bit mmio: [0xc2000000-0xc201ffff]
[    0.110427] pci 0000:00:0e.0: bridge 32bit mmio: [0xc0000000-0xc2ffffff]
[    0.110430] pci 0000:00:0e.0: bridge 64bit mmio pref: [0xa0000000-0xbfffffff]
[    0.110439] pci_bus 0000:00: on NUMA node 0
[    0.110444] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.110663] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.HUB0._PRT]
[    0.165021] ACPI: PCI Interrupt Link [LNK1] (IRQs 3 4 5 7 9 10 11 *12 14 15)
[    0.165146] ACPI: PCI Interrupt Link [LNK2] (IRQs *3 4 5 7 9 10 11 12 14 15)
[    0.165270] ACPI: PCI Interrupt Link [LNK3] (IRQs 3 4 5 7 9 10 *11 12 14 15)
[    0.165393] ACPI: PCI Interrupt Link [LNK4] (IRQs 3 4 *5 7 9 10 11 12 14 15)
[    0.165515] ACPI: PCI Interrupt Link [LNK5] (IRQs 3 4 5 7 9 10 11 12 14 15) *0, disabled.
[    0.165645] ACPI: PCI Interrupt Link [LUBA] (IRQs *3 4 5 7 9 10 11 12 14 15)
[    0.165767] ACPI: PCI Interrupt Link [LUBB] (IRQs 3 4 5 7 9 10 11 12 14 15) *0, disabled.
[    0.165891] ACPI: PCI Interrupt Link [LMAC] (IRQs *3 4 5 7 9 10 11 12 14 15)
[    0.166017] ACPI: PCI Interrupt Link [LACI] (IRQs 3 4 5 7 9 10 11 12 14 15) *0, disabled.
[    0.166143] ACPI: PCI Interrupt Link [LMCI] (IRQs 3 4 5 7 9 10 11 12 14 15) *0, disabled.
[    0.166267] ACPI: PCI Interrupt Link [LSMB] (IRQs 3 4 5 7 9 10 11 *12 14 15)
[    0.166394] ACPI: PCI Interrupt Link [LUB2] (IRQs 3 4 5 7 9 10 *11 12 14 15)
[    0.166517] ACPI: PCI Interrupt Link [LIDE] (IRQs 3 4 5 7 9 10 11 12 14 15) *0, disabled.
[    0.166654] ACPI: PCI Interrupt Link [LSID] (IRQs 3 4 5 7 9 10 *11 12 14 15)
[    0.166788] ACPI: PCI Interrupt Link [LFID] (IRQs 3 4 *5 7 9 10 11 12 14 15)
[    0.166921] ACPI: PCI Interrupt Link [LPCA] (IRQs 3 4 5 7 9 10 11 12 14 15) *0, disabled.
[    0.167062] ACPI: PCI Interrupt Link [APC1] (IRQs 16) *0
[    0.167199] ACPI: PCI Interrupt Link [APC2] (IRQs 17) *0
[    0.167336] ACPI: PCI Interrupt Link [APC3] (IRQs 18) *0
[    0.167472] ACPI: PCI Interrupt Link [APC4] (IRQs 19) *0
[    0.167558] ACPI: PCI Interrupt Link [APC5] (IRQs *16), disabled.
[    0.167701] ACPI: PCI Interrupt Link [APCF] (IRQs 20 21 22 23) *0
[    0.167845] ACPI: PCI Interrupt Link [APCG] (IRQs 20 21 22 23) *0, disabled.
[    0.167988] ACPI: PCI Interrupt Link [APCH] (IRQs 20 21 22 23) *0
[    0.168139] ACPI: PCI Interrupt Link [APCJ] (IRQs 20 21 22 23) *0, disabled.
[    0.168283] ACPI: PCI Interrupt Link [APCK] (IRQs 20 21 22 23) *0, disabled.
[    0.168426] ACPI: PCI Interrupt Link [APCS] (IRQs 20 21 22 23) *0
[    0.168569] ACPI: PCI Interrupt Link [APCL] (IRQs 20 21 22 23) *0
[    0.168712] ACPI: PCI Interrupt Link [APCZ] (IRQs 20 21 22 23) *0, disabled.
[    0.168864] ACPI: PCI Interrupt Link [APSI] (IRQs 20 21 22 23) *0
[    0.169015] ACPI: PCI Interrupt Link [APSJ] (IRQs 20 21 22 23) *0
[    0.169167] ACPI: PCI Interrupt Link [APCP] (IRQs 20 21 22 23) *0, disabled.
[    0.169314] SCSI subsystem initialized
[    0.169354] libata version 3.00 loaded.
[    0.169417] usbcore: registered new interface driver usbfs
[    0.169437] usbcore: registered new interface driver hub
[    0.169457] usbcore: registered new device driver usb
[    0.169560] ACPI: WMI: Mapper loaded
[    0.169562] PCI: Using ACPI for IRQ routing
[    0.169678] Bluetooth: Core ver 2.15
[    0.169699] NET: Registered protocol family 31
[    0.169700] Bluetooth: HCI device and connection manager initialized
[    0.169703] Bluetooth: HCI socket layer initialized
[    0.169705] NetLabel: Initializing
[    0.169707] NetLabel:  domain hash size = 128
[    0.169708] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.169721] NetLabel:  unlabeled traffic allowed by default
[    0.171331] pnp: PnP ACPI init
[    0.171350] ACPI: bus type pnp registered
[    0.175685] pnp: PnP ACPI: found 14 devices
[    0.175687] ACPI: ACPI bus type pnp unregistered
[    0.175690] PnPBIOS: Disabled by ACPI PNP
[    0.175701] system 00:01: ioport range 0x4000-0x407f has been reserved
[    0.175704] system 00:01: ioport range 0x4080-0x40ff has been reserved
[    0.175706] system 00:01: ioport range 0x4400-0x447f has been reserved
[    0.175709] system 00:01: ioport range 0x4480-0x44ff has been reserved
[    0.175711] system 00:01: ioport range 0x4800-0x487f has been reserved
[    0.175714] system 00:01: ioport range 0x4880-0x48ff has been reserved
[    0.175722] system 00:02: ioport range 0x4d0-0x4d1 has been reserved
[    0.175725] system 00:02: ioport range 0x800-0x87f has been reserved
[    0.175727] system 00:02: ioport range 0x290-0x297 has been reserved
[    0.175734] system 00:0c: iomem range 0xe0000000-0xefffffff has been reserved
[    0.175739] system 00:0d: iomem range 0xf0000-0xf3fff could not be reserved
[    0.175741] system 00:0d: iomem range 0xf4000-0xf7fff could not be reserved
[    0.175744] system 00:0d: iomem range 0xf8000-0xfbfff could not be reserved
[    0.175746] system 00:0d: iomem range 0xfc000-0xfffff could not be reserved
[    0.175749] system 00:0d: iomem range 0x3fff0000-0x3fffffff could not be reserved
[    0.175752] system 00:0d: iomem range 0xffff0000-0xffffffff has been reserved
[    0.175755] system 00:0d: iomem range 0x0-0x9ffff could not be reserved
[    0.175757] system 00:0d: iomem range 0x100000-0x3ffeffff could not be reserved
[    0.175760] system 00:0d: iomem range 0xfec00000-0xfec00fff could not be reserved
[    0.175763] system 00:0d: iomem range 0xfee00000-0xfeefffff has been reserved
[    0.175765] system 00:0d: iomem range 0xfefff000-0xfeffffff has been reserved
[    0.175768] system 00:0d: iomem range 0xfff80000-0xfff80fff has been reserved
[    0.175771] system 00:0d: iomem range 0xfff90000-0xfffbffff has been reserved
[    0.175773] system 00:0d: iomem range 0xfffed000-0xfffeffff has been reserved
[    0.210443] AppArmor: AppArmor Filesystem Enabled
[    0.210455] pci 0000:05:0a.0: BAR 6: address space collision on of device [0xc3000000-0xc307ffff]
[    0.210458] pci 0000:05:0c.0: BAR 6: address space collision on of device [0xc3000000-0xc301ffff]
[    0.210482] pci 0000:00:09.0: PCI bridge, secondary bus 0000:05
[    0.210484] pci 0000:00:09.0:   IO window: 0x9000-0xafff
[    0.210487] pci 0000:00:09.0:   MEM window: 0xc3000000-0xc4ffffff
[    0.210490] pci 0000:00:09.0:   PREFETCH window: 0x40000000-0x400fffff
[    0.210493] pci 0000:00:0b.0: PCI bridge, secondary bus 0000:04
[    0.210495] pci 0000:00:0b.0:   IO window: disabled
[    0.210498] pci 0000:00:0b.0:   MEM window: disabled
[    0.210500] pci 0000:00:0b.0:   PREFETCH window: disabled
[    0.210503] pci 0000:00:0c.0: PCI bridge, secondary bus 0000:03
[    0.210504] pci 0000:00:0c.0:   IO window: disabled
[    0.210507] pci 0000:00:0c.0:   MEM window: disabled
[    0.210509] pci 0000:00:0c.0:   PREFETCH window: disabled
[    0.210512] pci 0000:00:0d.0: PCI bridge, secondary bus 0000:02
[    0.210513] pci 0000:00:0d.0:   IO window: disabled
[    0.210516] pci 0000:00:0d.0:   MEM window: disabled
[    0.210518] pci 0000:00:0d.0:   PREFETCH window: disabled
[    0.210521] pci 0000:00:0e.0: PCI bridge, secondary bus 0000:01
[    0.210522] pci 0000:00:0e.0:   IO window: disabled
[    0.210525] pci 0000:00:0e.0:   MEM window: 0xc0000000-0xc2ffffff
[    0.210528] pci 0000:00:0e.0:   PREFETCH window: 0x000000a0000000-0x000000bfffffff
[    0.210537] pci 0000:00:09.0: setting latency timer to 64
[    0.210541] pci 0000:00:0b.0: setting latency timer to 64
[    0.210545] pci 0000:00:0c.0: setting latency timer to 64
[    0.210549] pci 0000:00:0d.0: setting latency timer to 64
[    0.210553] pci 0000:00:0e.0: setting latency timer to 64
[    0.210556] pci_bus 0000:00: resource 0 io:  [0x00-0xffff]
[    0.210559] pci_bus 0000:00: resource 1 mem: [0x000000-0xffffffff]
[    0.210561] pci_bus 0000:05: resource 0 io:  [0x9000-0xafff]
[    0.210563] pci_bus 0000:05: resource 1 mem: [0xc3000000-0xc4ffffff]
[    0.210566] pci_bus 0000:05: resource 2 pref mem [0x40000000-0x400fffff]
[    0.210568] pci_bus 0000:05: resource 3 io:  [0x00-0xffff]
[    0.210570] pci_bus 0000:05: resource 4 mem: [0x000000-0xffffffff]
[    0.210573] pci_bus 0000:01: resource 1 mem: [0xc0000000-0xc2ffffff]
[    0.210576] pci_bus 0000:01: resource 2 pref mem [0xa0000000-0xbfffffff]
[    0.210611] NET: Registered protocol family 2
[    0.210701] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.211055] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.212033] Switched to high resolution mode on CPU 0
[    0.212064] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.212576] TCP: Hash tables configured (established 131072 bind 65536)
[    0.212579] TCP reno registered
[    0.212689] NET: Registered protocol family 1
[    0.212757] Trying to unpack rootfs image as initramfs...
[    0.389765] Freeing initrd memory: 7472k freed
[    0.396411] cpufreq-nforce2: No nForce2 chipset.
[    0.396441] Scanning for low memory corruption every 60 seconds
[    0.396545] audit: initializing netlink socket (disabled)
[    0.396564] type=2000 audit(1268154752.396:1): initialized
[    0.404185] highmem bounce pool size: 64 pages
[    0.404190] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    0.405326] VFS: Disk quotas dquot_6.5.2
[    0.405375] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.405819] fuse init (API version 7.12)
[    0.405887] msgmni has been set to 1731
[    0.406056] alg: No test for stdrng (krng)
[    0.406067] io scheduler noop registered
[    0.406068] io scheduler anticipatory registered
[    0.406070] io scheduler deadline registered
[    0.406106] io scheduler cfq registered (default)
[    0.420064] pci 0000:00:00.0: Found enabled HT MSI Mapping
[    0.420069] pci 0000:00:0b.0: Found disabled HT MSI Mapping
[    0.420075] pci 0000:00:00.0: Found enabled HT MSI Mapping
[    0.420079] pci 0000:00:0b.0: Linking AER extended capability
[    0.420111] pci 0000:00:00.0: Found enabled HT MSI Mapping
[    0.420116] pci 0000:00:0c.0: Found disabled HT MSI Mapping
[    0.420123] pci 0000:00:00.0: Found enabled HT MSI Mapping
[    0.420125] pci 0000:00:0c.0: Linking AER extended capability
[    0.420160] pci 0000:00:00.0: Found enabled HT MSI Mapping
[    0.420165] pci 0000:00:0d.0: Found disabled HT MSI Mapping
[    0.420171] pci 0000:00:00.0: Found enabled HT MSI Mapping
[    0.420174] pci 0000:00:0d.0: Linking AER extended capability
[    0.420212] pci 0000:00:00.0: Found enabled HT MSI Mapping
[    0.420216] pci 0000:00:0e.0: Found disabled HT MSI Mapping
[    0.420223] pci 0000:00:00.0: Found enabled HT MSI Mapping
[    0.420225] pci 0000:00:0e.0: Linking AER extended capability
[    0.420241] pci 0000:01:00.0: Boot video device
[    0.420316]   alloc irq_desc for 24 on node -1
[    0.420318]   alloc kstat_irqs on node -1
[    0.420326] pcieport-driver 0000:00:0b.0: irq 24 for MSI/MSI-X
[    0.420331] pcieport-driver 0000:00:0b.0: setting latency timer to 64
[    0.420384]   alloc irq_desc for 25 on node -1
[    0.420385]   alloc kstat_irqs on node -1
[    0.420389] pcieport-driver 0000:00:0c.0: irq 25 for MSI/MSI-X
[    0.420393] pcieport-driver 0000:00:0c.0: setting latency timer to 64
[    0.420444]   alloc irq_desc for 26 on node -1
[    0.420445]   alloc kstat_irqs on node -1
[    0.420449] pcieport-driver 0000:00:0d.0: irq 26 for MSI/MSI-X
[    0.420453] pcieport-driver 0000:00:0d.0: setting latency timer to 64
[    0.420503]   alloc irq_desc for 27 on node -1
[    0.420505]   alloc kstat_irqs on node -1
[    0.420508] pcieport-driver 0000:00:0e.0: irq 27 for MSI/MSI-X
[    0.420512] pcieport-driver 0000:00:0e.0: setting latency timer to 64
[    0.420560] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.420580] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.420689] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input0
[    0.420693] ACPI: Power Button [PWRF]
[    0.420735] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1
[    0.420737] ACPI: Power Button [PWRB]
[    0.420786] fan PNP0C0B:00: registered as cooling_device0
[    0.420790] ACPI: Fan [FAN] (on)
[    0.421221] processor LNXCPU:00: registered as cooling_device1
[    0.424908] thermal LNXTHERM:01: registered as thermal_zone0
[    0.424914] ACPI: Thermal Zone [THRM] (40 C)
[    0.424950] isapnp: Scanning for PnP cards...
[    0.777457] isapnp: No Plug & Play device found
[    0.778314] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    0.778402] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.778624] 00:07: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.779453] brd: module loaded
[    0.779808] loop: module loaded
[    0.779884] input: Macintosh mouse button emulation as /devices/virtual/input/input2
[    0.780024] sata_sil 0000:05:0a.0: version 2.4
[    0.780264] ACPI: PCI Interrupt Link [APC4] enabled at IRQ 19
[    0.780268]   alloc irq_desc for 19 on node -1
[    0.780270]   alloc kstat_irqs on node -1
[    0.780277] sata_sil 0000:05:0a.0: PCI INT A -> Link[APC4] -> GSI 19 (level, low) -> IRQ 19
[    0.780298] sata_sil 0000:05:0a.0: Applying R_ERR on DMA activate FIS errata fix
[    0.780369] scsi0 : sata_sil
[    0.780444] scsi1 : sata_sil
[    0.780486] scsi2 : sata_sil
[    0.780530] scsi3 : sata_sil
[    0.780560] ata1: SATA max UDMA/100 mmio m1024@0xc4009000 tf 0xc4009080 irq 19
[    0.780563] ata2: SATA max UDMA/100 mmio m1024@0xc4009000 tf 0xc40090c0 irq 19
[    0.780566] ata3: SATA max UDMA/100 mmio m1024@0xc4009000 tf 0xc4009280 irq 19
[    0.780568] ata4: SATA max UDMA/100 mmio m1024@0xc4009000 tf 0xc40092c0 irq 19
[    0.780624] sata_nv 0000:00:07.0: version 3.5
[    0.780935] ACPI: PCI Interrupt Link [APSI] enabled at IRQ 23
[    0.780938]   alloc irq_desc for 23 on node -1
[    0.780939]   alloc kstat_irqs on node -1
[    0.780944] sata_nv 0000:00:07.0: PCI INT A -> Link[APSI] -> GSI 23 (level, low) -> IRQ 23
[    0.780980] sata_nv 0000:00:07.0: setting latency timer to 64
[    0.781041] scsi4 : sata_nv
[    0.781100] scsi5 : sata_nv
[    0.781231] ata5: SATA max UDMA/133 cmd 0x9f0 ctl 0xbf0 bmdma 0xd800 irq 23
[    0.781234] ata6: SATA max UDMA/133 cmd 0x970 ctl 0xb70 bmdma 0xd808 irq 23
[    0.781546] ACPI: PCI Interrupt Link [APSJ] enabled at IRQ 22
[    0.781548]   alloc irq_desc for 22 on node -1
[    0.781550]   alloc kstat_irqs on node -1
[    0.781555] sata_nv 0000:00:08.0: PCI INT A -> Link[APSJ] -> GSI 22 (level, low) -> IRQ 22
[    0.781588] sata_nv 0000:00:08.0: setting latency timer to 64
[    0.781641] scsi6 : sata_nv
[    0.781702] scsi7 : sata_nv
[    0.781834] ata7: SATA max UDMA/133 cmd 0x9e0 ctl 0xbe0 bmdma 0xc400 irq 22
[    0.781837] ata8: SATA max UDMA/133 cmd 0x960 ctl 0xb60 bmdma 0xc408 irq 22
[    0.781902] pata_amd 0000:00:06.0: version 0.4.1
[    0.781936] pata_amd 0000:00:06.0: setting latency timer to 64
[    0.782007] scsi8 : pata_amd
[    0.782063] scsi9 : pata_amd
[    0.782729] ata9: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xf000 irq 14
[    0.782732] ata10: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xf008 irq 15
[    0.783260] Fixed MDIO Bus: probed
[    0.783287] PPP generic driver version 2.4.2
[    0.783364] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.783608] ACPI: PCI Interrupt Link [APCL] enabled at IRQ 21
[    0.783611]   alloc irq_desc for 21 on node -1
[    0.783612]   alloc kstat_irqs on node -1
[    0.783617] ehci_hcd 0000:00:02.1: PCI INT B -> Link[APCL] -> GSI 21 (level, low) -> IRQ 21
[    0.783625] ehci_hcd 0000:00:02.1: setting latency timer to 64
[    0.783627] ehci_hcd 0000:00:02.1: EHCI Host Controller
[    0.783653] ehci_hcd 0000:00:02.1: new USB bus registered, assigned bus number 1
[    0.783688] ehci_hcd 0000:00:02.1: debug port 1
[    0.783691] ehci_hcd 0000:00:02.1: cache line size of 64 is not supported
[    0.783702] ehci_hcd 0000:00:02.1: irq 21, io mem 0xfeb00000
[    0.792016] ehci_hcd 0000:00:02.1: USB 2.0 started, EHCI 1.00
[    0.792090] usb usb1: configuration #1 chosen from 1 choice
[    0.792115] hub 1-0:1.0: USB hub found
[    0.792125] hub 1-0:1.0: 10 ports detected
[    0.792175] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.792418] ACPI: PCI Interrupt Link [APCF] enabled at IRQ 20
[    0.792420]   alloc irq_desc for 20 on node -1
[    0.792422]   alloc kstat_irqs on node -1
[    0.792427] ohci_hcd 0000:00:02.0: PCI INT A -> Link[APCF] -> GSI 20 (level, low) -> IRQ 20
[    0.792433] ohci_hcd 0000:00:02.0: setting latency timer to 64
[    0.792435] ohci_hcd 0000:00:02.0: OHCI Host Controller
[    0.792459] ohci_hcd 0000:00:02.0: new USB bus registered, assigned bus number 2
[    0.792477] ohci_hcd 0000:00:02.0: irq 20, io mem 0xc5003000
[    0.850052] usb usb2: configuration #1 chosen from 1 choice
[    0.850072] hub 2-0:1.0: USB hub found
[    0.850080] hub 2-0:1.0: 10 ports detected
[    0.850123] uhci_hcd: USB Universal Host Controller Interface driver
[    0.850196] PNP: PS/2 Controller [PNP0303:PS2K] at 0x60,0x64 irq 1
[    0.850198] PNP: PS/2 appears to have AUX port disabled, if this is incorrect please boot with i8042.nopnp
[    0.850674] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.850720] mice: PS/2 mouse device common for all mice
[    0.850803] rtc_cmos 00:04: RTC can wake from S4
[    0.850833] rtc_cmos 00:04: rtc core: registered rtc_cmos as rtc0
[    0.850854] rtc0: alarms up to one year, y3k, 242 bytes nvram
[    0.850938] device-mapper: uevent: version 1.0.3
[    0.851017] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: dm-devel@redhat.com
[    0.851088] device-mapper: multipath: version 1.1.0 loaded
[    0.851091] device-mapper: multipath round-robin: version 1.0.0 loaded
[    0.851195] EISA: Probing bus 0 at eisa.0
[    0.851206] Cannot allocate resource for EISA slot 4
[    0.851215] EISA: Detected 0 cards.
[    0.851260] cpuidle: using governor ladder
[    0.851262] cpuidle: using governor menu
[    0.851657] TCP cubic registered
[    0.851787] NET: Registered protocol family 10
[    0.852167] lo: Disabled Privacy Extensions
[    0.852413] NET: Registered protocol family 17
[    0.852427] Bluetooth: L2CAP ver 2.13
[    0.852429] Bluetooth: L2CAP socket layer initialized
[    0.852431] Bluetooth: SCO (Voice Link) ver 0.6
[    0.852432] Bluetooth: SCO socket layer initialized
[    0.852457] Bluetooth: RFCOMM TTY layer initialized
[    0.852460] Bluetooth: RFCOMM socket layer initialized
[    0.852462] Bluetooth: RFCOMM ver 1.11
[    0.852472] powernow-k8: Found 1 AMD Athlon(tm) 64 Processor 4000+ processors (1 cpu cores) (version 2.20.00)
[    0.856865] [Firmware Bug]: powernow-k8: No PSB or ACPI _PSS objects
[    0.856902] Using IPI No-Shortcut mode
[    0.856948] PM: Resume from disk failed.
[    0.856960] registered taskstats version 1
[    0.857090]   Magic number: 2:627:238
[    0.857195] rtc_cmos 00:04: setting system clock to 2010-03-09 17:12:33 UTC (1268154753)
[    0.857198] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.857200] EDD information not available.
[    0.871805] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input3
[    1.088357] ata9.01: ATA-7: SAMSUNG SP2014N, VC100-41, max UDMA/100
[    1.088360] ata9.01: 390721968 sectors, multi 1: LBA48 
[    1.088381] ata9: nv_mode_filter: 0x3f39f&0x3f39f->0x3f39f, BIOS=0x3f000 (0xc600c0) ACPI=0x3f01f (600:20:0x1c)
[    1.092018] ata5: SATA link down (SStatus 0 SControl 300)
[    1.100022] ata1: SATA link down (SStatus 0 SControl 310)
[    1.120290] ata9.01: configured for UDMA/100
[    1.248025] ata7: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    1.257095] ata7.00: ATA-7: Maxtor 6V300F0, VA111630, max UDMA/133
[    1.257098] ata7.00: 586114704 sectors, multi 1: LBA48 NCQ (depth 0/32)
[    1.273126] ata7.00: configured for UDMA/133
[    1.420022] ata2: SATA link down (SStatus 0 SControl 310)
[    1.576019] usb 2-4: new low speed USB device using ohci_hcd and address 2
[    1.740026] ata3: SATA link down (SStatus 0 SControl 310)
[    1.785077] usb 2-4: configuration #1 chosen from 1 choice
[    2.060026] ata4: SATA link down (SStatus 0 SControl 310)
[    2.092020] usb 2-9: new full speed USB device using ohci_hcd and address 3
[    2.307071] usb 2-9: configuration #1 chosen from 1 choice
[    2.372023] ata6: SATA link down (SStatus 0 SControl 300)
[    2.372139] scsi 6:0:0:0: Direct-Access     ATA      Maxtor 6V300F0   VA11 PQ: 0 ANSI: 5
[    2.372244] sd 6:0:0:0: Attached scsi generic sg0 type 0
[    2.372279] sd 6:0:0:0: [sda] 586114704 512-byte logical blocks: (300 GB/279 GiB)
[    2.372315] sd 6:0:0:0: [sda] Write Protect is off
[    2.372317] sd 6:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    2.372335] sd 6:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.372439]  sda: sda1 sda2 < sda5 sda6 >
[    2.422727] sd 6:0:0:0: [sda] Attached SCSI disk
[    2.612020] usb 2-10: new full speed USB device using ohci_hcd and address 4
[    2.684020] ata8: SATA link down (SStatus 0 SControl 300)
[    2.684085] scsi 8:0:1:0: Direct-Access     ATA      SAMSUNG SP2014N  VC10 PQ: 0 ANSI: 5
[    2.684167] sd 8:0:1:0: Attached scsi generic sg1 type 0
[    2.684193] sd 8:0:1:0: [sdb] 390721968 512-byte logical blocks: (200 GB/186 GiB)
[    2.684225] sd 8:0:1:0: [sdb] Write Protect is off
[    2.684227] sd 8:0:1:0: [sdb] Mode Sense: 00 3a 00 00
[    2.684244] sd 8:0:1:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.684326]  sdb: sdb1 sdb2 sdb3 < sdb5 sdb6 >
[    2.716809] sdb: p6 size 63149562 exceeds device capacity, limited to end of disk
[    2.716952] sd 8:0:1:0: [sdb] Attached SCSI disk
[    2.850946] usb 2-10: configuration #1 chosen from 1 choice
[    2.856240] ata10.01: ATAPI: TSSTcorpCD/DVDW SH-S182M, SB05, max UDMA/33
[    2.856260] ata10: nv_mode_filter: 0x739f&0x739f->0x739f, BIOS=0x7000 (0xc600c0) ACPI=0x701f (600:60:0x1c)
[    2.872193] ata10.01: configured for UDMA/33
[   23.816029] ata10.01: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6 frozen
[   23.816039] ata10.01: cmd a0/01:00:00:60:00/00:00:00:00:00/b0 tag 0 dma 96 in
[   23.816040]          cdb 12 00 00 00 60 00 00 00  00 00 00 00 00 00 00 00
[   23.816041]          res 40/00:02:00:24:00/00:00:00:00:00/b0 Emask 0x4 (timeout)
[   23.816044] ata10.01: status: { DRDY }
[   28.856021] ata10: link is slow to respond, please be patient (ready=0)
[   33.840020] ata10: device not ready (errno=-16), forcing hardreset
[   33.840025] ata10: soft resetting link
[   34.012261] ata10: nv_mode_filter: 0x739f&0x739f->0x739f, BIOS=0x7000 (0xc600c0) ACPI=0x701f (600:60:0x1c)
[   34.028193] ata10.01: configured for UDMA/33
[   34.028576] ata10: EH complete
[   54.816027] ata10.01: limiting speed to UDMA/25:PIO4
[   54.816030] ata10.01: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6 frozen
[   54.816038] ata10.01: cmd a0/01:00:00:60:00/00:00:00:00:00/b0 tag 0 dma 96 in
[   54.816039]          cdb 12 00 00 00 60 00 00 00  00 00 00 00 00 00 00 00
[   54.816040]          res 40/00:02:00:24:00/00:00:00:00:00/b0 Emask 0x4 (timeout)
[   54.816043] ata10.01: status: { DRDY }
[   59.856020] ata10: link is slow to respond, please be patient (ready=0)
[   64.840019] ata10: device not ready (errno=-16), forcing hardreset
[   64.840023] ata10: soft resetting link
[   65.012260] ata10: nv_mode_filter: 0x339f&0x739f->0x339f, BIOS=0x7000 (0xc600c0) ACPI=0x701f (600:60:0x1c)
[   65.028193] ata10.01: configured for UDMA/25
[   65.028568] ata10: EH complete
[   85.816025] ata10.01: limiting speed to PIO4
[   85.816028] ata10.01: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6 frozen
[   85.816036] ata10.01: cmd a0/01:00:00:60:00/00:00:00:00:00/b0 tag 0 dma 96 in
[   85.816037]          cdb 12 00 00 00 60 00 00 00  00 00 00 00 00 00 00 00
[   85.816038]          res 40/00:02:00:24:00/00:00:00:00:00/b0 Emask 0x4 (timeout)
[   85.816041] ata10.01: status: { DRDY }
[   90.856020] ata10: link is slow to respond, please be patient (ready=0)
[   95.840018] ata10: device not ready (errno=-16), forcing hardreset
[   95.840023] ata10: soft resetting link
[   96.012260] ata10: nv_mode_filter: 0x1f&0x739f->0x1f, BIOS=0x7000 (0xc600c0) ACPI=0x701f (600:60:0x1c)
[   96.028193] ata10.01: configured for PIO4
[   96.028576] ata10: EH complete
[   96.028978] scsi 9:0:1:0: CD-ROM            TSSTcorp CD/DVDW SH-S182M SB05 PQ: 0 ANSI: 5
[   96.035938] sr0: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
[   96.035940] Uniform CD-ROM driver Revision: 3.20
[   96.036013] sr 9:0:1:0: Attached scsi CD-ROM sr0
[   96.036044] sr 9:0:1:0: Attached scsi generic sg2 type 5
[   96.036063] Freeing unused kernel memory: 540k freed
[   96.036528] Write protecting the kernel text: 4580k
[   96.036560] Write protecting the kernel read-only data: 1840k
[   96.176853] forcedeth: Reverse Engineered nForce ethernet driver. Version 0.64.
[   96.177161] ACPI: PCI Interrupt Link [APCH] enabled at IRQ 23
[   96.177167] forcedeth 0000:00:0a.0: PCI INT A -> Link[APCH] -> GSI 23 (level, low) -> IRQ 23
[   96.177171] forcedeth 0000:00:0a.0: setting latency timer to 64
[   96.177221] nv_probe: set workaround bit for reversed mac addr
[   96.249274] ACPI: PCI Interrupt Link [APC2] enabled at IRQ 17
[   96.249282]   alloc irq_desc for 17 on node -1
[   96.249284]   alloc kstat_irqs on node -1
[   96.249294] ohci1394 0000:05:06.2: PCI INT B -> Link[APC2] -> GSI 17 (level, low) -> IRQ 17
[   96.304156] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[17]  MMIO=[c4008000-c40087ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[   96.304285] skge 0000:05:0c.0: PCI INT A -> Link[APC2] -> GSI 17 (level, low) -> IRQ 17
[   96.304328] skge 1.13 addr 0xc4004000 irq 17 chip Yukon-Lite rev 9
[   96.304860] skge eth0: addr 00:13:d4:b8:48:cb
[   96.329134] usbcore: registered new interface driver hiddev
[   96.329280] Initializing USB Mass Storage driver...
[   96.329392] scsi10 : SCSI emulation for USB Mass Storage devices
[   96.329467] usbcore: registered new interface driver usb-storage
[   96.329469] USB Mass Storage support registered.
[   96.335932] input: USB Optical Mouse as /devices/pci0000:00/0000:00:02.0/usb2/2-4/2-4:1.0/input/input4
[   96.336043] generic-usb 0003:04B3:310C.0001: input,hidraw0: USB HID v1.11 Mouse [USB Optical Mouse] on usb-0000:00:02.0-4/input0
[   96.336067] usbcore: registered new interface driver usbhid
[   96.336070] usbhid: v2.6:USB HID core driver
[   96.342394] usb-storage: device found at 3
[   96.342398] usb-storage: waiting for device to settle before scanning
[   96.696780] forcedeth 0000:00:0a.0: ifname eth1, PHY OUI 0x5043 @ 1, addr 00:13:d4:b8:3f:bd
[   96.696785] forcedeth 0000:00:0a.0: highdma csum gbit lnktim desc-v3
[   97.563456] PM: Starting manual resume from disk
[   97.563461] PM: Resume from partition 8:6
[   97.563463] PM: Checking hibernation image.
[   97.563571] PM: Resume from disk failed.
[   97.585019] EXT4-fs (sda5): barriers enabled
[   97.592193] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[00023c0151004dde]
[   97.601247] kjournald2 starting: pid 442, dev sda5:8, commit interval 5 seconds
[   97.601289] EXT4-fs (sda5): delayed allocation enabled
[   97.601293] EXT4-fs: file extents enabled
[   97.603515] EXT4-fs: mballoc enabled
[   97.603525] EXT4-fs (sda5): mounted filesystem with ordered data mode
[   98.125677] type=1505 audit(1268154850.767:2): operation="profile_load" pid=466 name=/usr/share/gdm/guest-session/Xsession
[   98.127863] type=1505 audit(1268154850.767:3): operation="profile_load" pid=467 name=/sbin/dhclient3
[   98.128127] type=1505 audit(1268154850.770:4): operation="profile_load" pid=467 name=/usr/lib/NetworkManager/nm-dhcp-client.action
[   98.128267] type=1505 audit(1268154850.770:5): operation="profile_load" pid=467 name=/usr/lib/connman/scripts/dhclient-script
[   98.176571] type=1505 audit(1268154850.818:6): operation="profile_load" pid=468 name=/usr/bin/evince
[   98.180870] type=1505 audit(1268154850.822:7): operation="profile_load" pid=468 name=/usr/bin/evince-previewer
[   98.183363] type=1505 audit(1268154850.822:8): operation="profile_load" pid=468 name=/usr/bin/evince-thumbnailer
[   98.197868] type=1505 audit(1268154850.838:9): operation="profile_load" pid=470 name=/usr/lib/cups/backend/cups-pdf
[   98.198180] type=1505 audit(1268154850.838:10): operation="profile_load" pid=470 name=/usr/sbin/cupsd
[   98.212325] type=1505 audit(1268154850.854:11): operation="profile_load" pid=471 name=/usr/sbin/mysqld
[  101.341125] usb-storage: device scan complete
[  101.348093] scsi 10:0:0:0: Direct-Access     Generic  USB SD Reader    1.00 PQ: 0 ANSI: 0
[  101.355843] scsi 10:0:0:1: Direct-Access     Generic  USB CF Reader    1.01 PQ: 0 ANSI: 0
[  101.362088] scsi 10:0:0:2: Direct-Access     Generic  USB SM Reader    1.02 PQ: 0 ANSI: 0
[  101.369093] scsi 10:0:0:3: Direct-Access     Generic  USB MS Reader    1.03 PQ: 0 ANSI: 0
[  101.369438] sd 10:0:0:0: Attached scsi generic sg3 type 0
[  101.369510] sd 10:0:0:1: Attached scsi generic sg4 type 0
[  101.369572] sd 10:0:0:2: Attached scsi generic sg5 type 0
[  101.369639] sd 10:0:0:3: Attached scsi generic sg6 type 0
[  101.606082] sd 10:0:0:1: [sdd] Attached SCSI removable disk
[  101.617080] sd 10:0:0:2: [sde] Attached SCSI removable disk
[  101.628082] sd 10:0:0:3: [sdf] Attached SCSI removable disk
[  101.635088] sd 10:0:0:0: [sdc] 8192000 512-byte logical blocks: (4.19 GB/3.90 GiB)
[  101.648080] sd 10:0:0:0: [sdc] Write Protect is off
[  101.648083] sd 10:0:0:0: [sdc] Mode Sense: 03 00 00 00
[  101.648085] sd 10:0:0:0: [sdc] Assuming drive cache: write through
[  101.687079] sd 10:0:0:0: [sdc] Assuming drive cache: write through
[  101.687083]  sdc: unknown partition table
[  101.741079] sd 10:0:0:0: [sdc] Assuming drive cache: write through
[  101.741082] sd 10:0:0:0: [sdc] Attached SCSI removable disk
[  112.428430] Adding 1373516k swap on /dev/sda6.  Priority:-1 extents:1 across:1373516k 
[  112.430612] udev: starting version 147
[  112.460974] lp: driver loaded but no devices found
[  112.470852] i2c-adapter i2c-0: nForce2 SMBus adapter at 0x4c00
[  112.470870] i2c-adapter i2c-1: nForce2 SMBus adapter at 0x4c40
[  112.608025] EXT4-fs (sda5): internal journal on sda5:8
[  112.699677] parport_pc 00:08: reported by Plug and Play ACPI
[  112.699727] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
[  112.812403] Linux agpgart interface v0.103
[  112.832990] gameport: EMU10K1 is pci0000:05:06.1/gameport0, io 0x9400, speed 59659kHz
[  112.868192] lp0: using parport0 (interrupt-driven).
[  112.965843] gameport: NS558 PnP Gameport is pnp00:0b/gameport0, io 0x201, speed 59659kHz
[  113.013943] nvidia: module license 'NVIDIA' taints kernel.
[  113.013948] Disabling lock debugging due to kernel taint
[  113.299157] ppdev: user-space parallel port driver
[  113.311460] ip_tables: (C) 2000-2006 Netfilter Core Team
[  113.485392] ACPI: PCI Interrupt Link [APC1] enabled at IRQ 16
[  113.485399]   alloc irq_desc for 16 on node -1
[  113.485402]   alloc kstat_irqs on node -1
[  113.485410] EMU10K1_Audigy 0000:05:06.0: PCI INT A -> Link[APC1] -> GSI 16 (level, low) -> IRQ 16
[  113.487941] Installing spdif_bug patch: SB Audigy 2 ZS [SB0350]
[  113.628320] ACPI: PCI Interrupt Link [APC3] enabled at IRQ 18
[  113.628327]   alloc irq_desc for 18 on node -1
[  113.628329]   alloc kstat_irqs on node -1
[  113.628338] nvidia 0000:01:00.0: PCI INT A -> Link[APC3] -> GSI 18 (level, low) -> IRQ 18
[  113.628345] nvidia 0000:01:00.0: setting latency timer to 64
[  113.628650] NVRM: loading NVIDIA UNIX x86 Kernel Module  185.18.36  Fri Aug 14 17:18:04 PDT 2009
[  114.106259] __ratelimit: 3 callbacks suppressed
[  114.106263] type=1505 audit(1268154866.746:13): operation="profile_replace" pid=1077 name=/usr/share/gdm/guest-session/Xsession
[  114.107444] type=1505 audit(1268154866.746:14): operation="profile_replace" pid=1078 name=/sbin/dhclient3
[  114.107694] type=1505 audit(1268154866.746:15): operation="profile_replace" pid=1078 name=/usr/lib/NetworkManager/nm-dhcp-client.action
[  114.107835] type=1505 audit(1268154866.746:16): operation="profile_replace" pid=1078 name=/usr/lib/connman/scripts/dhclient-script
[  114.123413] type=1505 audit(1268154866.762:17): operation="profile_replace" pid=1080 name=/usr/bin/evince
[  114.137232] skge eth0: enabling interface
[  114.144738] type=1505 audit(1268154866.786:18): operation="profile_replace" pid=1080 name=/usr/bin/evince-previewer
[  114.147275] type=1505 audit(1268154866.786:19): operation="profile_replace" pid=1080 name=/usr/bin/evince-thumbnailer
[  114.149247] ADDRCONF(NETDEV_UP): eth0: link is not ready
[  114.194685] type=1505 audit(1268154866.834:20): operation="profile_replace" pid=1090 name=/usr/lib/cups/backend/cups-pdf
[  114.194999] type=1505 audit(1268154866.834:21): operation="profile_replace" pid=1090 name=/usr/sbin/cupsd
[  114.196727] type=1505 audit(1268154866.838:22): operation="profile_replace" pid=1091 name=/usr/sbin/mysqld
[  124.452118] eth1: no IPv6 routers present
[ 1280.898018] usb 2-10: USB disconnect, address 4
```From what I can tell there may be an issue with one of my disks. Can anyone have a look at that and give me some pointers? Also the bootchart log that I posted in an earlier post is still a valid representation of the machines booting process. Anyone know why [COLOR=Red]kthreadd,events/0,khelper,kblockd/0,pdflush,async/9 and init[/COLOR] all start at the beginning but nothing else happens for 95 seconds.

Any help or insight on this will be appreciated!

---

### Post by patchwork on 2010-03-09
It looks like the problem is coming from your cd/dvd drive.  Not sure why this is, but I thought I'd point that out.

---

### Post by GerryEgan on 2010-03-09
Hi,

I disconnected the DVD drive and rebooted. I now get from grub to login in 30 seconds! I'm going to check the drive and cable when I get a chance! 

Thanks very much for your help!

Gerry

---

