---
title: "My computer crashes on startup."
date: 2010-01-27
forum: General Help
---

### Post by theflanman on 2010-01-27
It has been for a few days every other time I start up, I have to go to a previous version of Karmic to get it to work.  It started after I updated my ALSA drivers.

---

### Post by Tux+ on 2010-01-27
Does it boot up in recovery mode?

---

### Post by theflanman on 2010-01-27
no, I chose a recovery mode on startup but it didn't work, only a previous version.

---

### Post by cpeake on 2010-01-27
Are you sure Synaptic Package manager ticked all the packets you need to install the ALSA drivers when you did the update? Did you check for updates for the system that could include some ALSA updates as well?

If installing the ALSA drivers seems to cause the problem, can you go back and do a fresh install of Ubuntu and describe the problems/situations as to why you want to update the ALSA drivers in the first place?

---

### Post by lidex on 2010-01-27
> **theflanman said:**
> It has been for a few days every other time I start up, I have to go to a previous version of Karmic to get it to work.  It started after I updated my ALSA drivers.
So you mean you're choosing an earlier kernel from the grub menu? What exactly is it doing-how far does it get? Post the contents of your dmesg file(use code tags). It's located in /var/log/dmesg. Command is :
```
gedit /var/log/dmesg
```

---

### Post by theflanman on 2010-01-27
```
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.31-16-generic (buildd@rothera) (gcc version 4.4.1 (Ubuntu 4.4.1-4ubuntu8) ) #53-Ubuntu SMP Tue Dec 8 04:01:29 UTC 2009 (Ubuntu 2.6.31-16.53-generic)
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
[    0.000000]  BIOS-e820: 00000000000d2000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 00000000bbf00000 (usable)
[    0.000000]  BIOS-e820: 00000000bbf00000 - 00000000bbf0a000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000bbf0a000 - 00000000bbf80000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000bbf80000 - 00000000c0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fff80000 - 0000000100000000 (reserved)
[    0.000000]  BIOS-e820: 0000000100000000 - 0000000140000000 (usable)
[    0.000000] DMI present.
[    0.000000] last_pfn = 0xbbf00 max_arch_pfn = 0x100000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-D3FFF write-protect
[    0.000000]   D4000-E3FFF uncachable
[    0.000000]   E4000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 0000000000 mask FF80000000 write-back
[    0.000000]   1 base 0080000000 mask FFE0000000 write-back
[    0.000000]   2 base 00A0000000 mask FFF0000000 write-back
[    0.000000]   3 base 00B0000000 mask FFF8000000 write-back
[    0.000000]   4 base 00B8000000 mask FFFC000000 write-back
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] TOM2: 0000000140000000 aka 5120M
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] e820 update range: 00000000bc000000 - 0000000100000000 (usable) ==> (reserved)
[    0.000000] e820 update range: 0000000000002000 - 0000000000006000 (usable) ==> (reserved)
[    0.000000] Scanning 1 areas for low memory corruption
[    0.000000] modified physical RAM map:
[    0.000000]  modified: 0000000000000000 - 0000000000002000 (usable)
[    0.000000]  modified: 0000000000002000 - 0000000000006000 (reserved)
[    0.000000]  modified: 0000000000006000 - 000000000009dc00 (usable)
[    0.000000]  modified: 000000000009dc00 - 00000000000a0000 (reserved)
[    0.000000]  modified: 00000000000d2000 - 0000000000100000 (reserved)
[    0.000000]  modified: 0000000000100000 - 00000000bbf00000 (usable)
[    0.000000]  modified: 00000000bbf00000 - 00000000bbf0a000 (ACPI data)
[    0.000000]  modified: 00000000bbf0a000 - 00000000bbf80000 (ACPI NVS)
[    0.000000]  modified: 00000000bbf80000 - 00000000c0000000 (reserved)
[    0.000000]  modified: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  modified: 00000000fec00000 - 00000000fec10000 (reserved)
[    0.000000]  modified: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  modified: 00000000fff80000 - 0000000100000000 (reserved)
[    0.000000]  modified: 0000000100000000 - 0000000140000000 (usable)
[    0.000000] initial memory mapped : 0 - 00c00000
[    0.000000] init_memory_mapping: 0000000000000000-00000000377fe000
[    0.000000] Using x86 segment limits to approximate NX protection
[    0.000000]  0000000000 - 0000400000 page 4k
[    0.000000]  0000400000 - 0037400000 page 2M
[    0.000000]  0037400000 - 00377fe000 page 4k
[    0.000000] kernel direct mapping tables up to 377fe000 @ 7000-c000
[    0.000000] RAMDISK: 378a7000 - 37fef3e7
[    0.000000] Allocated new RAMDISK: 008ad000 - 00ff53e7
[    0.000000] Move RAMDISK from 00000000378a7000 - 0000000037fef3e6 to 008ad000 - 00ff53e6
[    0.000000] ACPI: RSDP 000f8920 00014 (v00 HP    )
[    0.000000] ACPI: RSDT bbf00926 00040 (v01 HPQOEM SLIC-MPC 06040000  LTP 00000000)
[    0.000000] ACPI: FACP bbf09ad4 00074 (v01 HP     MCP51M   06040000 PTL_ 000F4240)
[    0.000000] ACPI: DSDT bbf00966 0916E (v01 HP       MCP51M 06040000 MSFT 03000000)
[    0.000000] ACPI: FACS bbf0afc0 00040
[    0.000000] ACPI: SSDT bbf09b48 00248 (v01 HP     POWERNOW 06040000  LTP 00000001)
[    0.000000] ACPI: MCFG bbf09d90 0003C (v01 HP       MCFG   06040000  LTP 00000000)
[    0.000000] ACPI: HPET bbf09dcc 00038 (v01 PTLTD  HPETTBL  06040000  LTP 00000001)
[    0.000000] ACPI: APIC bbf09e04 0005E (v01 HP          APIC   06040000  LTP 00000000)
[    0.000000] ACPI: BOOT bbf09e62 00028 (v01     HP $SBFTBL$ 06040000  LTP 00000001)
[    0.000000] ACPI: SLIC bbf09e8a 00176 (v01 HPQOEM SLIC-MPC 06040000  LTP 00000001)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] 2119MB HIGHMEM available.
[    0.000000] 887MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 377fe000
[    0.000000]   low ram: 0 - 377fe000
[    0.000000]   node 0 low ram: 00000000 - 377fe000
[    0.000000]   node 0 bootmap 00008000 - 0000ef00
[    0.000000] (9 early reservations) ==> bootmem [0000000000 - 00377fe000]
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
[    0.000000]   #1 [0000001000 - 0000002000]    EX TRAMPOLINE ==> [0000001000 - 0000002000]
[    0.000000]   #2 [0000006000 - 0000007000]       TRAMPOLINE ==> [0000006000 - 0000007000]
[    0.000000]   #3 [0000100000 - 00008a80a0]    TEXT DATA BSS ==> [0000100000 - 00008a80a0]
[    0.000000]   #4 [000009dc00 - 0000100000]    BIOS reserved ==> [000009dc00 - 0000100000]
[    0.000000]   #5 [00008a9000 - 00008ac154]              BRK ==> [00008a9000 - 00008ac154]
[    0.000000]   #6 [0000007000 - 0000008000]          PGTABLE ==> [0000007000 - 0000008000]
[    0.000000]   #7 [00008ad000 - 0000ff53e7]      NEW RAMDISK ==> [00008ad000 - 0000ff53e7]
[    0.000000]   #8 [0000008000 - 000000f000]          BOOTMAP ==> [0000008000 - 000000f000]
[    0.000000] found SMP MP-table at [c00f89e0] f89e0
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000000 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x000377fe
[    0.000000]   HighMem  0x000377fe -> 0x000bbf00
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[3] active PFN ranges
[    0.000000]     0: 0x00000000 -> 0x00000002
[    0.000000]     0: 0x00000006 -> 0x0000009d
[    0.000000]     0: 0x00000100 -> 0x000bbf00
[    0.000000] On node 0 totalpages: 769689
[    0.000000] free_area_init_node: node 0, pgdat c0784940, node_mem_map c1000000
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3961 pages, LIFO batch:0
[    0.000000]   Normal zone: 1744 pages used for memmap
[    0.000000]   Normal zone: 221486 pages, LIFO batch:31
[    0.000000]   HighMem zone: 4239 pages used for memmap
[    0.000000]   HighMem zone: 538227 pages, LIFO batch:31
[    0.000000] Using APIC driver default
[    0.000000] Detected use of extended apic ids on hypertransport bus
[    0.000000] ACPI: PM-Timer IO Port: 0x1008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 17, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x10de8201 base: 0xfed00000
[    0.000000] SMP: Allowing 2 CPUs, 0 hotplug CPUs
[    0.000000] nr_irqs_gsi: 24
[    0.000000] PM: Registered nosave memory: 0000000000002000 - 0000000000006000
[    0.000000] PM: Registered nosave memory: 000000000009d000 - 000000000009e000
[    0.000000] PM: Registered nosave memory: 000000000009e000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000d2000
[    0.000000] PM: Registered nosave memory: 00000000000d2000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at c0000000 (gap: c0000000:20000000)
[    0.000000] NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:2 nr_node_ids:1
[    0.000000] PERCPU: Embedded 14 pages at c2790000, static data 35612 bytes
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 763674
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.31-16-generic root=UUID=274df390-b9dd-4285-88c0-a0a1185c53ee ro quiet splash
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] allocated 15395840 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] Initializing HighMem for node 0 (000377fe:000bbf00)
[    0.000000] Memory: 3022356k/3079168k available (4566k kernel code, 55416k reserved, 2142k data, 540k init, 2169864k highmem)
[    0.000000] virtual kernel memory layout:
[    0.000000]     fixmap  : 0xfff1d000 - 0xfffff000   ( 904 kB)
[    0.000000]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[    0.000000]     vmalloc : 0xf7ffe000 - 0xff7fe000   ( 120 MB)
[    0.000000]     lowmem  : 0xc0000000 - 0xf77fe000   ( 887 MB)
[    0.000000]       .init : 0xc078e000 - 0xc0815000   ( 540 kB)
[    0.000000]       .data : 0xc0575bb4 - 0xc078d3c8   (2142 kB)
[    0.000000]       .text : 0xc0100000 - 0xc0575bb4   (4566 kB)
[    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.000000] SLUB: Genslabs=13, HWalign=64, Order=0-3, MinObjects=0, CPUs=2, Nodes=1
[    0.000000] NR_IRQS:2304 nr_irqs:424
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 797.865 MHz processor.
[    0.000019] spurious 8259A interrupt: IRQ7.
[    0.003985] Console: colour VGA+ 80x25
[    0.003992] console [tty0] enabled
[    0.004000] hpet clockevent registered
[    0.004000] HPET: 3 timers in total, 0 timers will be used for per-cpu timer
[    0.004000] Calibrating delay loop (skipped), value calculated using timer frequency.. 1595.73 BogoMIPS (lpj=3191460)
[    0.004000] Security Framework initialized
[    0.004000] AppArmor: AppArmor initialized
[    0.004000] Mount-cache hash table entries: 512
[    0.004000] Initializing cgroup subsys ns
[    0.004000] Initializing cgroup subsys cpuacct
[    0.004000] Initializing cgroup subsys memory
[    0.004000] Initializing cgroup subsys freezer
[    0.004000] Initializing cgroup subsys net_cls
[    0.004000] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[    0.004000] CPU: L2 Cache: 512K (64 bytes/line)
[    0.004000] CPU: Physical Processor ID: 0
[    0.004000] CPU: Processor Core ID: 0
[    0.004000] mce: CPU supports 5 MCE banks
[    0.004000] using C1E aware idle routine
[    0.004000] Performance Counters: AMD PMU driver.
[    0.004000] ... version:                 0
[    0.004000] ... bit width:               48
[    0.004000] ... generic counters:        4
[    0.004000] ... value mask:              0000ffffffffffff
[    0.004000] ... max period:              00007fffffffffff
[    0.004000] ... fixed-purpose counters:  0
[    0.004000] ... counter mask:            000000000000000f
[    0.004000] Checking 'hlt' instruction... OK.
[    0.020017] ACPI: Core revision 20090521
[    0.048327] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.088043] CPU0: AMD Turion(tm) 64 X2 Mobile Technology TL-64 stepping 02
[    0.092001] Booting processor 1 APIC 0x1 ip 0x6000
[    0.004000] Initializing CPU#1
[    0.004000] Calibrating delay using timer specific routine.. 1595.72 BogoMIPS (lpj=3191451)
[    0.004000] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[    0.004000] CPU: L2 Cache: 512K (64 bytes/line)
[    0.004000] CPU: Physical Processor ID: 0
[    0.004000] CPU: Processor Core ID: 1
[    0.004000] mce: CPU supports 5 MCE banks
[    0.004000] x86 PAT enabled: cpu 1, old 0x7040600070406, new 0x7010600070106
[    0.177047] CPU1: AMD Turion(tm) 64 X2 Mobile Technology TL-64 stepping 02
[    0.177106] Brought up 2 CPUs
[    0.177113] Total of 2 processors activated (3191.45 BogoMIPS).
[    0.177103] System has AMD C1E enabled
[    0.177103] Switch to broadcast mode on CPU1
[    0.177248] CPU0 attaching sched-domain:
[    0.177256]  domain 0: span 0-1 level MC
[    0.177264]   groups: 0 1
[    0.177277] CPU1 attaching sched-domain:
[    0.177283]  domain 0: span 0-1 level MC
[    0.177290]   groups: 1 0
[    0.177465] Switch to broadcast mode on CPU0
[    0.177465] Booting paravirtualized kernel on bare hardware
[    0.177465] regulator: core version 0.5
[    0.177465] Time:  7:38:47  Date: 01/27/10
[    0.177465] NET: Registered protocol family 16
[    0.177465] EISA bus registered
[    0.177465] ACPI: bus type pci registered
[    0.177465] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 6
[    0.177465] PCI: MCFG area at e0000000 reserved in E820
[    0.177465] PCI: Using MMCONFIG for extended config space
[    0.177465] PCI: Using configuration type 1 for base access
[    0.180261] bio: create slab <bio-0> at 0
[    0.181670] ACPI: EC: Enabling special treatment for EC from MSI.
[    0.181677] ACPI: EC: Look up EC in DSDT
[    0.214845] ACPI: BIOS _OSI(Linux) query ignored
[    0.220032] ACPI: EC: non-query interrupt received, switching to interrupt mode
[    0.224201] ACPI: Interpreter enabled
[    0.224215] ACPI: (supports S0 S3 S4 S5)
[    0.224291] ACPI: Using IOAPIC for interrupt routing
[    0.300985] ACPI: EC: GPE = 0x10, I/O: command/status = 0x66, data = 0x62
[    0.300992] ACPI: EC: driver started in interrupt mode
[    0.302425] ACPI: ACPI Dock Station Driver: 1 docks/bays found
[    0.303012] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.303521] pci 0000:00:02.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.303530] pci 0000:00:02.0: PME# disabled
[    0.303599] pci 0000:00:03.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.303606] pci 0000:00:03.0: PME# disabled
[    0.303649] pci 0000:00:05.0: reg 10 32bit mmio: [0xc2000000-0xc2ffffff]
[    0.303663] pci 0000:00:05.0: reg 14 64bit mmio: [0xd0000000-0xdfffffff]
[    0.303676] pci 0000:00:05.0: reg 1c 64bit mmio: [0xc1000000-0xc1ffffff]
[    0.303688] pci 0000:00:05.0: reg 30 32bit mmio: [0x000000-0x01ffff]
[    0.304021] pci 0000:00:0a.1: reg 20 io port: [0x3040-0x307f]
[    0.304032] pci 0000:00:0a.1: reg 24 io port: [0x3000-0x303f]
[    0.304068] pci 0000:00:0a.1: PME# supported from D3hot D3cold
[    0.304078] pci 0000:00:0a.1: PME# disabled
[    0.304126] pci 0000:00:0a.3: reg 10 32bit mmio: [0xc0040000-0xc007ffff]
[    0.304249] pci 0000:00:0b.0: reg 10 32bit mmio: [0xc0004000-0xc0004fff]
[    0.304302] pci 0000:00:0b.0: supports D1 D2
[    0.304308] pci 0000:00:0b.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.304317] pci 0000:00:0b.0: PME# disabled
[    0.304368] pci 0000:00:0b.1: reg 10 32bit mmio: [0xc0005000-0xc00050ff]
[    0.304422] pci 0000:00:0b.1: supports D1 D2
[    0.304428] pci 0000:00:0b.1: PME# supported from D0 D1 D2 D3hot D3cold
[    0.304436] pci 0000:00:0b.1: PME# disabled
[    0.304500] pci 0000:00:0d.0: reg 20 io port: [0x3080-0x308f]
[    0.304574] pci 0000:00:0e.0: reg 10 io port: [0x30b0-0x30b7]
[    0.304585] pci 0000:00:0e.0: reg 14 io port: [0x30a4-0x30a7]
[    0.304596] pci 0000:00:0e.0: reg 18 io port: [0x30a8-0x30af]
[    0.304607] pci 0000:00:0e.0: reg 1c io port: [0x30a0-0x30a3]
[    0.304617] pci 0000:00:0e.0: reg 20 io port: [0x3090-0x309f]
[    0.304628] pci 0000:00:0e.0: reg 24 32bit mmio: [0xc0006000-0xc0006fff]
[    0.304774] pci 0000:00:10.1: reg 10 32bit mmio: [0x000000-0x003fff]
[    0.304829] pci 0000:00:10.1: PME# supported from D3hot D3cold
[    0.304837] pci 0000:00:10.1: PME# disabled
[    0.304892] pci 0000:00:14.0: reg 10 32bit mmio: [0xc0007000-0xc0007fff]
[    0.304903] pci 0000:00:14.0: reg 14 io port: [0x30b8-0x30bf]
[    0.304943] pci 0000:00:14.0: supports D1 D2
[    0.304948] pci 0000:00:14.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.304956] pci 0000:00:14.0: PME# disabled
[    0.305190] pci 0000:00:02.0: bridge io port: [0x4000-0x4fff]
[    0.305198] pci 0000:00:02.0: bridge 32bit mmio: [0xc4000000-0xc7ffffff]
[    0.305208] pci 0000:00:02.0: bridge 64bit mmio pref: [0xc9000000-0xc91fffff]
[    0.305270] pci 0000:03:00.0: reg 10 64bit mmio: [0xc8000000-0xc8003fff]
[    0.305288] pci 0000:03:00.0: reg 18 64bit mmio: [0xc9200000-0xc92fffff]
[    0.305342] pci 0000:03:00.0: supports D1 D2
[    0.305421] pci 0000:00:03.0: bridge 32bit mmio: [0xc8000000-0xc8ffffff]
[    0.305432] pci 0000:00:03.0: bridge 64bit mmio pref: [0xc9200000-0xc93fffff]
[    0.305493] pci 0000:00:10.0: transparent bridge
[    0.305515] pci_bus 0000:00: on NUMA node 0
[    0.305527] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.305786] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P2P0._PRT]
[    0.305875] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.XVR1._PRT]
[    0.305963] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.XVR2._PRT]
[    0.388786] ACPI: PCI Interrupt Link [LNK1] (IRQs 5 7 10 11 14 15) *0, disabled.
[    0.389237] ACPI: PCI Interrupt Link [LNK2] (IRQs 5 7 *10 11 14 15)
[    0.389677] ACPI: PCI Interrupt Link [LNK3] (IRQs 5 7 10 11 14 15) *0, disabled.
[    0.390118] ACPI: PCI Interrupt Link [LNK4] (IRQs 5 7 10 11 14 15) *0, disabled.
[    0.390559] ACPI: PCI Interrupt Link [LK1E] (IRQs 19) *0, disabled.
[    0.390995] ACPI: PCI Interrupt Link [LK2E] (IRQs 16 17 20 22 23) *0, disabled.
[    0.391436] ACPI: PCI Interrupt Link [LK3E] (IRQs 18) *10
[    0.391871] ACPI: PCI Interrupt Link [LK4E] (IRQs 16 17 20 22 23) *0, disabled.
[    0.392327] ACPI: PCI Interrupt Link [LSMB] (IRQs 16 17 20 22 23) *10
[    0.392775] ACPI: PCI Interrupt Link [LPMU] (IRQs 16 17 20 22 23) *11
[    0.393214] ACPI: PCI Interrupt Link [LUS0] (IRQs 16 17 20 22 23) *11
[    0.393658] ACPI: PCI Interrupt Link [LUS2] (IRQs 16 17 20 22 23) *7
[    0.394100] ACPI: PCI Interrupt Link [LMAC] (IRQs 16 17 20 22 23) *11
[    0.394546] ACPI: PCI Interrupt Link [LAZA] (IRQs 16 17 20 22 23) *0, disabled.
[    0.394986] ACPI: PCI Interrupt Link [LACI] (IRQs 16 17 20 22 23) *0, disabled.
[    0.395427] ACPI: PCI Interrupt Link [LMCI] (IRQs 16 17 20 22 23) *0, disabled.
[    0.395869] ACPI: PCI Interrupt Link [LPID] (IRQs 16 17 20 22 23) *0, disabled.
[    0.396348] ACPI: PCI Interrupt Link [LTID] (IRQs 21) *5
[    0.396791] ACPI: PCI Interrupt Link [LSI1] (IRQs 21) *0
[    0.397243] SCSI subsystem initialized
[    0.400046] libata version 3.00 loaded.
[    0.400128] usbcore: registered new interface driver usbfs
[    0.400128] usbcore: registered new interface driver hub
[    0.400131] usbcore: registered new device driver usb
[    0.400196] ACPI: WMI: Mapper loaded
[    0.400202] PCI: Using ACPI for IRQ routing
[    0.408022] Bluetooth: Core ver 2.15
[    0.412032] NET: Registered protocol family 31
[    0.412038] Bluetooth: HCI device and connection manager initialized
[    0.412046] Bluetooth: HCI socket layer initialized
[    0.412052] NetLabel: Initializing
[    0.412057] NetLabel:  domain hash size = 128
[    0.412061] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.412094] NetLabel:  unlabeled traffic allowed by default
[    0.412170] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 31
[    0.412185] hpet0: 3 comparators, 32-bit 25.000000 MHz counter
[    0.424036] Switched to high resolution mode on CPU 0
[    0.424061] Switched to high resolution mode on CPU 1
[    0.429067] pnp: PnP ACPI init
[    0.429106] ACPI: bus type pnp registered
[    0.464309] pnp: PnP ACPI: found 13 devices
[    0.464315] ACPI: ACPI bus type pnp unregistered
[    0.464324] PnPBIOS: Disabled by ACPI PNP
[    0.464351] system 00:00: iomem range 0xe0000000-0xefffffff has been reserved
[    0.464367] system 00:01: iomem range 0xffc00000-0xffffffff could not be reserved
[    0.464376] system 00:01: iomem range 0xfec00000-0xfec00fff could not be reserved
[    0.464385] system 00:01: iomem range 0xfee00000-0xfeefffff could not be reserved
[    0.464393] system 00:01: iomem range 0xfed00000-0xfed00fff has been reserved
[    0.464408] system 00:03: iomem range 0xe0000000-0xefffffff has been reserved
[    0.464424] system 00:04: ioport range 0x1000-0x107f has been reserved
[    0.464432] system 00:04: ioport range 0x1080-0x10ff has been reserved
[    0.464439] system 00:04: ioport range 0x1400-0x147f has been reserved
[    0.464447] system 00:04: ioport range 0x1480-0x14ff has been reserved
[    0.464455] system 00:04: ioport range 0x1800-0x187f has been reserved
[    0.464463] system 00:04: ioport range 0x1880-0x18ff has been reserved
[    0.464471] system 00:04: ioport range 0x2000-0x203f has been reserved
[    0.464486] system 00:05: ioport range 0x360-0x361 has been reserved
[    0.464494] system 00:05: ioport range 0x380-0x383 has been reserved
[    0.464502] system 00:05: ioport range 0x4d0-0x4d1 has been reserved
[    0.499398] AppArmor: AppArmor Filesystem Enabled
[    0.499480] pci 0000:00:02.0: PCI bridge, secondary bus 0000:01
[    0.499488] pci 0000:00:02.0:   IO window: 0x4000-0x4fff
[    0.499498] pci 0000:00:02.0:   MEM window: 0xc4000000-0xc7ffffff
[    0.499507] pci 0000:00:02.0:   PREFETCH window: 0x000000c9000000-0x000000c91fffff
[    0.499519] pci 0000:00:03.0: PCI bridge, secondary bus 0000:03
[    0.499524] pci 0000:00:03.0:   IO window: disabled
[    0.499533] pci 0000:00:03.0:   MEM window: 0xc8000000-0xc8ffffff
[    0.499541] pci 0000:00:03.0:   PREFETCH window: 0x000000c9200000-0x000000c93fffff
[    0.499551] pci 0000:00:10.0: PCI bridge, secondary bus 0000:07
[    0.499557] pci 0000:00:10.0:   IO window: disabled
[    0.499565] pci 0000:00:10.0:   MEM window: disabled
[    0.499572] pci 0000:00:10.0:   PREFETCH window: disabled
[    0.499592] pci 0000:00:02.0: setting latency timer to 64
[    0.499603] pci 0000:00:03.0: setting latency timer to 64
[    0.499614] pci 0000:00:10.0: setting latency timer to 64
[    0.499625] pci_bus 0000:00: resource 0 io:  [0x00-0xffff]
[    0.499633] pci_bus 0000:00: resource 1 mem: [0x000000-0xffffffff]
[    0.499641] pci_bus 0000:01: resource 0 io:  [0x4000-0x4fff]
[    0.499649] pci_bus 0000:01: resource 1 mem: [0xc4000000-0xc7ffffff]
[    0.499656] pci_bus 0000:01: resource 2 pref mem [0xc9000000-0xc91fffff]
[    0.499664] pci_bus 0000:03: resource 1 mem: [0xc8000000-0xc8ffffff]
[    0.499671] pci_bus 0000:03: resource 2 pref mem [0xc9200000-0xc93fffff]
[    0.499680] pci_bus 0000:07: resource 3 io:  [0x00-0xffff]
[    0.499688] pci_bus 0000:07: resource 4 mem: [0x000000-0xffffffff]
[    0.499782] NET: Registered protocol family 2
[    0.500023] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.500860] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.502439] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.503242] TCP: Hash tables configured (established 131072 bind 65536)
[    0.503249] TCP reno registered
[    0.503470] NET: Registered protocol family 1
[    0.503643] Trying to unpack rootfs image as initramfs...
[    1.023173] Freeing initrd memory: 7456k freed
[    1.034416] Simple Boot Flag at 0x36 set to 0x1
[    1.034855] cpufreq-nforce2: No nForce2 chipset.
[    1.034920] Scanning for low memory corruption every 60 seconds
[    1.035167] audit: initializing netlink socket (disabled)
[    1.035202] type=2000 audit(1264577927.033:1): initialized
[    1.058157] highmem bounce pool size: 64 pages
[    1.058171] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    1.061706] VFS: Disk quotas dquot_6.5.2
[    1.061847] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    1.063155] fuse init (API version 7.12)
[    1.063356] msgmni has been set to 1681
[    1.063924] alg: No test for stdrng (krng)
[    1.063980] io scheduler noop registered
[    1.063986] io scheduler anticipatory registered
[    1.063992] io scheduler deadline registered
[    1.064124] io scheduler cfq registered (default)
[    1.064176] pci 0000:00:00.0: Found disabled HT MSI Mapping
[    1.064187] pci 0000:00:00.0: Enabling HT MSI Mapping
[    1.064269] pci 0000:00:00.0: Found enabled HT MSI Mapping
[    1.064319] pci 0000:00:00.0: Found enabled HT MSI Mapping
[    1.064334] pci 0000:00:05.0: Boot video device
[    1.064520] pci 0000:00:09.0: Found enabled HT MSI Mapping
[    1.064600] pci 0000:00:09.0: Found enabled HT MSI Mapping
[    1.064683] pci 0000:00:09.0: Found enabled HT MSI Mapping
[    1.064947]   alloc irq_desc for 24 on node -1
[    1.064954]   alloc kstat_irqs on node -1
[    1.064974] pcieport-driver 0000:00:02.0: irq 24 for MSI/MSI-X
[    1.064987] pcieport-driver 0000:00:02.0: setting latency timer to 64
[    1.065142]   alloc irq_desc for 25 on node -1
[    1.065147]   alloc kstat_irqs on node -1
[    1.065158] pcieport-driver 0000:00:03.0: irq 25 for MSI/MSI-X
[    1.065169] pcieport-driver 0000:00:03.0: setting latency timer to 64
[    1.065313] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    1.065374] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    1.068426] ACPI: AC Adapter [ACAD] (off-line)
[    1.068632] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input0
[    1.068641] ACPI: Power Button [PWRF]
[    1.068757] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1
[    1.068765] ACPI: Power Button [PWRB]
[    1.068873] input: Sleep Button as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input2
[    1.068880] ACPI: Sleep Button [SLPB]
[    1.068980] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input3
[    1.069144] ACPI: Lid Switch [LID]
[    1.069921] ACPI: processor limited to max C-state 1
[    1.069992] processor LNXCPU:00: registered as cooling_device0
[    1.070082] processor LNXCPU:01: registered as cooling_device1
[    1.110472] thermal LNXTHERM:01: registered as thermal_zone0
[    1.110492] ACPI: Thermal Zone [THRM] (46 C)
[    1.110633] isapnp: Scanning for PnP cards...
[    1.463972] isapnp: No Plug & Play device found
[    1.466902] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    1.469929] brd: module loaded
[    1.471077] loop: module loaded
[    1.471273] input: Macintosh mouse button emulation as /devices/virtual/input/input4
[    1.471827] sata_nv 0000:00:0e.0: version 3.5
[    1.472584] ACPI: PCI Interrupt Link [LTID] enabled at IRQ 21
[    1.472597]   alloc irq_desc for 21 on node -1
[    1.472603]   alloc kstat_irqs on node -1
[    1.472624] sata_nv 0000:00:0e.0: PCI INT A -> Link[LTID] -> GSI 21 (level, high) -> IRQ 21
[    1.472633] sata_nv 0000:00:0e.0: Using SWNCQ mode
[    1.472740] sata_nv 0000:00:0e.0: setting latency timer to 64
[    1.473139] scsi0 : sata_nv
[    1.473394] scsi1 : sata_nv
[    1.473745] ata1: SATA max UDMA/133 cmd 0x30b0 ctl 0x30a4 bmdma 0x3090 irq 21
[    1.473754] ata2: SATA max UDMA/133 cmd 0x30a8 ctl 0x30a0 bmdma 0x3098 irq 21
[    1.474012] pata_amd 0000:00:0d.0: version 0.4.1
[    1.474093] pata_amd 0000:00:0d.0: setting latency timer to 64
[    1.474311] scsi2 : pata_amd
[    1.474457] scsi3 : pata_amd
[    1.476112] ata3: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0x3080 irq 14
[    1.476120] ata4: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0x3088 irq 15
[    1.478034] Fixed MDIO Bus: probed
[    1.478123] PPP generic driver version 2.4.2
[    1.478371] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    1.479149] ACPI: PCI Interrupt Link [LUS2] enabled at IRQ 23
[    1.479158]   alloc irq_desc for 23 on node -1
[    1.479163]   alloc kstat_irqs on node -1
[    1.479180] ehci_hcd 0000:00:0b.1: PCI INT B -> Link[LUS2] -> GSI 23 (level, high) -> IRQ 23
[    1.479210] ehci_hcd 0000:00:0b.1: setting latency timer to 64
[    1.479217] ehci_hcd 0000:00:0b.1: EHCI Host Controller
[    1.479343] ehci_hcd 0000:00:0b.1: new USB bus registered, assigned bus number 1
[    1.479443] ehci_hcd 0000:00:0b.1: debug port 1
[    1.479453] ehci_hcd 0000:00:0b.1: cache line size of 64 is not supported
[    1.479492] ehci_hcd 0000:00:0b.1: irq 23, io mem 0xc0005000
[    1.489056] ehci_hcd 0000:00:0b.1: USB 2.0 started, EHCI 1.00
[    1.489250] usb usb1: configuration #1 chosen from 1 choice
[    1.489329] hub 1-0:1.0: USB hub found
[    1.489350] hub 1-0:1.0: 8 ports detected
[    1.489495] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    1.490196] ACPI: PCI Interrupt Link [LUS0] enabled at IRQ 22
[    1.490204]   alloc irq_desc for 22 on node -1
[    1.490209]   alloc kstat_irqs on node -1
[    1.490225] ohci_hcd 0000:00:0b.0: PCI INT A -> Link[LUS0] -> GSI 22 (level, high) -> IRQ 22
[    1.490244] ohci_hcd 0000:00:0b.0: setting latency timer to 64
[    1.490251] ohci_hcd 0000:00:0b.0: OHCI Host Controller
[    1.490337] ohci_hcd 0000:00:0b.0: new USB bus registered, assigned bus number 2
[    1.490386] ohci_hcd 0000:00:0b.0: irq 22, io mem 0xc0004000
[    1.546193] usb usb2: configuration #1 chosen from 1 choice
[    1.546257] hub 2-0:1.0: USB hub found
[    1.546278] hub 2-0:1.0: 8 ports detected
[    1.546412] uhci_hcd: USB Universal Host Controller Interface driver
[    1.546617] PNP: PS/2 Controller [PNP0303:KBC0,PNP0f13:MSE0] at 0x60,0x64 irq 1,12
[    1.562349] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.562364] serio: i8042 AUX port at 0x60,0x64 irq 12
[    1.562546] mice: PS/2 mouse device common for all mice
[    1.562851] rtc_cmos 00:09: RTC can wake from S4
[    1.562945] rtc_cmos 00:09: rtc core: registered rtc_cmos as rtc0
[    1.562993] rtc0: alarms up to one year, y3k, 114 bytes nvram, hpet irqs
[    1.563232] device-mapper: uevent: version 1.0.3
[    1.563459] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: dm-devel@redhat.com
[    1.563699] device-mapper: multipath: version 1.1.0 loaded
[    1.563708] device-mapper: multipath round-robin: version 1.0.0 loaded
[    1.564032] EISA: Probing bus 0 at eisa.0
[    1.564044] Cannot allocate resource for EISA slot 1
[    1.564050] Cannot allocate resource for EISA slot 2
[    1.564056] Cannot allocate resource for EISA slot 3
[    1.564062] Cannot allocate resource for EISA slot 4
[    1.564086] EISA: Detected 0 cards.
[    1.564375] cpuidle: using governor ladder
[    1.564381] cpuidle: using governor menu
[    1.565635] TCP cubic registered
[    1.566030] NET: Registered protocol family 10
[    1.567132] lo: Disabled Privacy Extensions
[    1.567929] NET: Registered protocol family 17
[    1.567972] Bluetooth: L2CAP ver 2.13
[    1.567977] Bluetooth: L2CAP socket layer initialized
[    1.567985] Bluetooth: SCO (Voice Link) ver 0.6
[    1.567989] Bluetooth: SCO socket layer initialized
[    1.568076] Bluetooth: RFCOMM TTY layer initialized
[    1.568084] Bluetooth: RFCOMM socket layer initialized
[    1.568089] Bluetooth: RFCOMM ver 1.11
[    1.568128] powernow-k8: Found 1 AMD Turion(tm) 64 X2 Mobile Technology TL-64 processors (2 cpu cores) (version 2.20.00)
[    1.568231] powernow-k8:    0 : fid 0xe (2200 MHz), vid 0x12
[    1.568238] powernow-k8:    1 : fid 0xc (2000 MHz), vid 0x13
[    1.568245] powernow-k8:    2 : fid 0xa (1800 MHz), vid 0x14
[    1.568251] powernow-k8:    3 : fid 0x8 (1600 MHz), vid 0x15
[    1.568258] powernow-k8:    4 : fid 0x0 (800 MHz), vid 0x1e
[    1.570270] Using IPI No-Shortcut mode
[    1.570360] PM: Resume from disk failed.
[    1.570372] registered taskstats version 1
[    1.570494]   Magic number: 10:319:623
[    1.570606] rtc_cmos 00:09: setting system clock to 2010-01-27 07:38:48 UTC (1264577928)
[    1.570609] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.570611] EDD information not available.
[    1.574150] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input5
[    1.628083] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
[    1.636293] ata1.00: ATA-8: WDC WD2500BEVS-60UST0, 01.01A01, max UDMA/100
[    1.636297] ata1.00: 488397168 sectors, multi 16: LBA48 
[    1.652252] ata1.00: configured for UDMA/100
[    1.660342] ata3.00: ATAPI: Slimtype DVD A  DS8A1H, WH66, max MWDMA2
[    1.660363] ata3: nv_mode_filter: 0x39f&0x739f->0x39f, BIOS=0x0 (0xc600) ACPI=0x39f (120:600:0x12)
[    1.700291] ata3.00: configured for MWDMA2
[    1.738302] ACPI: Battery Slot [BAT0] (battery present)
[    1.738477] scsi 0:0:0:0: Direct-Access     ATA      WDC WD2500BEVS-6 01.0 PQ: 0 ANSI: 5
[    1.738600] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    1.738625] sd 0:0:0:0: [sda] 488397168 512-byte logical blocks: (250 GB/232 GiB)
[    1.749194] ata2: SATA link down (SStatus 0 SControl 310)
[    1.749219] sd 0:0:0:0: [sda] Write Protect is off
[    1.749222] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.749242] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.749361]  sda:
[    1.751362] scsi 2:0:0:0: CD-ROM            Slimtype DVD A  DS8A1H    WH66 PQ: 0 ANSI: 5
[    1.761946] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[    1.761949] Uniform CD-ROM driver Revision: 3.20
[    1.762029] sr 2:0:0:0: Attached scsi CD-ROM sr0
[    1.762064] sr 2:0:0:0: Attached scsi generic sg1 type 5
[    1.762090] ata4: port disabled. ignoring.
[    1.795619]  sda1 sda2 <
[    1.804053] usb 1-2: new high speed USB device using ehci_hcd and address 2
[    1.818394]  sda5 >
[    1.818631] sd 0:0:0:0: [sda] Attached SCSI disk
[    1.936960] usb 1-2: configuration #1 chosen from 1 choice
[    1.937056] hub 1-2:1.0: USB hub found
[    1.937160] hub 1-2:1.0: 4 ports detected
[    2.000044] Clocksource tsc unstable (delta = 755336748 ns)
[    2.026681] Freeing unused kernel memory: 540k freed
[    2.027071] Write protecting the kernel text: 4568k
[    2.027109] Write protecting the kernel read-only data: 1836k
[    2.292266] forcedeth: Reverse Engineered nForce ethernet driver. Version 0.64.
[    2.293081] ACPI: PCI Interrupt Link [LMAC] enabled at IRQ 20
[    2.293095]   alloc irq_desc for 20 on node -1
[    2.293101]   alloc kstat_irqs on node -1
[    2.293125] forcedeth 0000:00:14.0: PCI INT A -> Link[LMAC] -> GSI 20 (level, high) -> IRQ 20
[    2.293137] forcedeth 0000:00:14.0: setting latency timer to 64
[    2.293233] nv_probe: set workaround bit for reversed mac addr
[    2.357007] usb 2-7: new full speed USB device using ohci_hcd and address 2
[    2.373007] acpi device:2d: registered as cooling_device2
[    2.375144] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:2b/input/input6
[    2.375259] ACPI: Video Device [UVGA] (multi-head: yes  rom: no  post: no)
[    2.596086] usb 2-7: configuration #1 chosen from 1 choice
[    2.676649] usb 1-2.1: new high speed USB device using ehci_hcd and address 4
[    2.778524] usb 1-2.1: configuration #1 chosen from 1 choice
[    2.814186] forcedeth 0000:00:14.0: ifname eth0, PHY OUI 0x732 @ 1, addr 00:1e:68:5a:ed:c3
[    2.814200] forcedeth 0000:00:14.0: highdma pwrctl gbit lnktim desc-v3
[    2.853649] usb 1-2.2: new full speed USB device using ehci_hcd and address 5
[    2.958091] usb 1-2.2: configuration #1 chosen from 1 choice
[    3.037011] usb 1-2.3: new full speed USB device using ehci_hcd and address 6
[    3.142986] usb 1-2.3: configuration #1 chosen from 1 choice
[    3.167098] usbcore: registered new interface driver hiddev
[    3.167221] usbcore: registered new interface driver usbhid
[    3.167228] usbhid: v2.6:USB HID core driver
[    3.974706] PM: Starting manual resume from disk
[    3.974706] PM: Resume from partition 8:5
[    3.974706] PM: Checking hibernation image.
[    3.976648] PM: Resume from disk failed.
[    3.989225] EXT4-fs (sda1): INFO: recovery required on readonly filesystem
[    3.989225] EXT4-fs (sda1): write access will be enabled during recovery
[    4.044398] EXT4-fs (sda1): barriers enabled
[    4.176091] kjournald2 starting: pid 400, dev sda1:8, commit interval 5 seconds
[    4.176091] EXT4-fs (sda1): delayed allocation enabled
[    4.176091] EXT4-fs: file extents enabled
[    4.253008] EXT4-fs: mballoc enabled
[    4.253008] EXT4-fs (sda1): recovery complete
[    4.256615] EXT4-fs (sda1): mounted filesystem with ordered data mode
[    4.954084] type=1505 audit(1264577931.881:2): operation="profile_load" pid=423 name=/usr/share/gdm/guest-session/Xsession
[    4.959961] type=1505 audit(1264577931.886:3): operation="profile_load" pid=424 name=/sbin/dhclient3
[    4.961018] type=1505 audit(1264577931.890:4): operation="profile_load" pid=424 name=/usr/lib/NetworkManager/nm-dhcp-client.action
[    4.961018] type=1505 audit(1264577931.890:5): operation="profile_load" pid=424 name=/usr/lib/connman/scripts/dhclient-script
[    5.029019] type=1505 audit(1264577931.957:6): operation="profile_load" pid=425 name=/usr/bin/evince
[    5.041014] type=1505 audit(1264577931.970:7): operation="profile_load" pid=425 name=/usr/bin/evince-previewer
[    5.049012] type=1505 audit(1264577931.978:8): operation="profile_load" pid=425 name=/usr/bin/evince-thumbnailer
[    5.088168] type=1505 audit(1264577932.014:9): operation="profile_load" pid=427 name=/usr/lib/cups/backend/cups-pdf
[   20.844679] udev: starting version 147
[   20.874958] lp: driver loaded but no devices found
[   20.877028] Adding 8883904k swap on /dev/sda5.  Priority:-1 extents:1 across:8883904k 
[   21.299782] i2c-adapter i2c-0: nForce2 SMBus adapter at 0x3040
[   21.299831] i2c-adapter i2c-1: nForce2 SMBus adapter at 0x3000
[   21.394987] Linux agpgart interface v0.103
[   21.597014] EXT4-fs (sda1): internal journal on sda1:8
[   21.687160] nvidia: module license 'NVIDIA' taints kernel.
[   21.687173] Disabling lock debugging due to kernel taint
[   21.928009] k8temp 0000:00:18.3: Temperature readouts might be wrong - check erratum #141
[   21.933014] lib80211: common routines for IEEE802.11 drivers
[   21.933014] lib80211_crypt: registered algorithm 'NULL'
[   21.962966] ACPI: PCI Interrupt Link [LK1E] enabled at IRQ 19
[   21.962966]   alloc irq_desc for 19 on node -1
[   21.962966]   alloc kstat_irqs on node -1
[   21.962966] wl 0000:03:00.0: PCI INT A -> Link[LK1E] -> GSI 19 (level, high) -> IRQ 19
[   21.962966] wl 0000:03:00.0: setting latency timer to 64
[   22.018584] ip_tables: (C) 2000-2006 Netfilter Core Team
[   22.029013] Bluetooth: Generic Bluetooth USB driver ver 0.5
[   22.029013] usbcore: registered new interface driver btusb
[   22.033454] lib80211_crypt: registered algorithm 'TKIP'
[   22.033783] eth1: Broadcom BCM4328 802.11 Wireless Controller 5.10.91.9
[   22.061011] udev: renamed network interface eth1 to eth2
[   22.067479] Linux video capture interface: v2.00
[   22.082765] input: Wacom ISDv4 93 as /devices/pci0000:00/0000:00:0b.1/usb1/1-2/1-2.3/1-2.3:1.0/input/input7
[   22.085055] input: Wacom ISDv4 93 as /devices/pci0000:00/0000:00:0b.1/usb1/1-2/1-2.3/1-2.3:1.1/input/input8
[   22.085055] usbcore: registered new interface driver wacom
[   22.085055] wacom: v1.51:USB Wacom Graphire and Wacom Intuos tablet driver
[   22.156493] uvcvideo: Found UVC 1.00 device HP Webcam (064e:a110)
[   22.163250] input: HP Webcam as /devices/pci0000:00/0000:00:0b.1/usb1/1-2/1-2.1/1-2.1:1.0/input/input9
[   22.163379] usbcore: registered new interface driver uvcvideo
[   22.163388] USB Video Class driver (v0.1.0)
[   22.281583] HDA Intel 0000:00:10.1: enabling device (0000 -> 0002)
[   22.281583] ACPI: PCI Interrupt Link [LAZA] enabled at IRQ 17
[   22.281583]   alloc irq_desc for 17 on node -1
[   22.281583]   alloc kstat_irqs on node -1
[   22.281583] HDA Intel 0000:00:10.1: PCI INT B -> Link[LAZA] -> GSI 17 (level, high) -> IRQ 17
[   22.281583] HDA Intel 0000:00:10.1: setting latency timer to 64
[   22.559163] eth0: no link during initialization.
[   22.561276] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   22.803152] __ratelimit: 6 callbacks suppressed
[   22.803163] type=1505 audit(1264595949.729:12): operation="profile_replace" pid=967 name=/usr/share/gdm/guest-session/Xsession
[   22.811394] type=1505 audit(1264595949.737:13): operation="profile_replace" pid=968 name=/sbin/dhclient3
[   22.812262] type=1505 audit(1264595949.741:14): operation="profile_replace" pid=968 name=/usr/lib/NetworkManager/nm-dhcp-client.action
[   22.812688] type=1505 audit(1264595949.741:15): operation="profile_replace" pid=968 name=/usr/lib/connman/scripts/dhclient-script
[   22.823464] type=1505 audit(1264595949.749:16): operation="profile_replace" pid=969 name=/usr/bin/evince
[   22.838438] type=1505 audit(1264595949.765:17): operation="profile_replace" pid=969 name=/usr/bin/evince-previewer
[   22.846779] type=1505 audit(1264595949.773:18): operation="profile_replace" pid=969 name=/usr/bin/evince-thumbnailer
[   22.864573] type=1505 audit(1264595949.793:19): operation="profile_replace" pid=971 name=/usr/lib/cups/backend/cups-pdf
[   22.865492] type=1505 audit(1264595949.793:20): operation="profile_replace" pid=971 name=/usr/sbin/cupsd
[   22.869012] type=1505 audit(1264595949.797:21): operation="profile_replace" pid=972 name=/usr/sbin/tcpdump
[   23.024065] hda_codec: Unknown model for ALC861-VD, trying auto-probe from BIOS...
[   23.025017] input: HDA Digital PCBeep as /devices/pci0000:00/0000:00:10.1/input/input10
[   23.081524] Synaptics Touchpad, model: 1, fw: 6.3, id: 0x180b1, caps: 0xa04713/0x200000
[   23.144228] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input11
```

---

### Post by lidex on 2010-01-29
Can you go here:
[http://bootinfoscript.sourceforge.net/]("http://bootinfoscript.sourceforge.net/")
and follow instructions for bootinfo script and post results in your next post? Thanks.

---

