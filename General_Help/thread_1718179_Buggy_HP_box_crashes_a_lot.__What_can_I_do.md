---
title: "Buggy HP box crashes a lot.  What can I do?"
date: 2011-03-30
forum: General Help
---

### Post by DunZH on 2011-03-30
Hi again, I have a cheap HP box with 9.10 on it and it really performs  poorly.  The cpu is often being taxed to the max and it just shouldn't be happening.  

But the most important is the freezing crashes.  It just locks up and there is nothing to do but do a hard re-start.  I have re-installed a few times and this always happens.

Can anyone point me to some resources to de-bug this?

---

### Post by alazou on 2011-03-30
Please include more information. Have you tried to update the system ? what is the HP model ?

---

### Post by DunZH on 2011-03-31
Sorry my bad.

Its a HP Compaq dx2040 Microtower PC. VIA C7-D Model D Processor (1.8 Ghz).

Its fully updated.

---

### Post by tgalati4 on 2011-03-31
C7 is a slooow processor.

Open a terminal.

dmesg  | more   (spacebar  to move foward, q to quit.)

---

### Post by DunZH on 2011-03-31
Ok thanks that makes me feel a bit better somehow heh.

Here is the data i got, dunno really how to use it.  Or what kind of fix I could try.

Any pointers?  :)

```
zhuang-desktop:~$ dmesg | more
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.31-23-generic (buildd@palmer) (gcc version 4.4.
1 (Ubuntu 4.4.1-4ubuntu9) ) #74-Ubuntu SMP Mon Feb 28 21:32:57 UTC 2011 (Ubuntu 
2.6.31-23.74-generic)
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
[    0.000000]  BIOS-e820: 0000000000100000 - 0000000037ee0000 (usable)
[    0.000000]  BIOS-e820: 0000000037ee0000 - 0000000037ee3000 (ACPI NVS)
[    0.000000]  BIOS-e820: 0000000037ee3000 - 0000000037ef0000 (ACPI data)
[    0.000000]  BIOS-e820: 0000000037ef0000 - 0000000037f00000 (reserved)
[    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000ffff0000 - 0000000100000000 (reserved)
[    0.000000] DMI 2.5 present.
[    0.000000] Phoenix BIOS detected: BIOS may corrupt low RAM, working around i
t.
[    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) =
=> (reserved)
[    0.000000] last_pfn = 0x37ee0 max_arch_pfn = 0x100000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-C7FFF write-protect
[    0.000000]   C8000-EFFFF uncachable
[    0.000000]   F0000-F7FFF write-through
[    0.000000]   F8000-F8FFF uncachable
[    0.000000]   F9000-FFFFF write-through
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000 mask FE0000000 write-back
[    0.000000]   1 base 020000000 mask FF0000000 write-back
[    0.000000]   2 base 030000000 mask FF8000000 write-back
[    0.000000]   3 base 0C8000000 mask FF8000000 write-combining
[    0.000000]   4 base 037F00000 mask FFFF00000 uncachable
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
[    0.000000]  modified: 0000000000100000 - 0000000037ee0000 (usable)
[    0.000000]  modified: 0000000037ee0000 - 0000000037ee3000 (ACPI NVS)
[    0.000000]  modified: 0000000037ee3000 - 0000000037ef0000 (ACPI data)
[    0.000000]  modified: 0000000037ef0000 - 0000000037f00000 (reserved)
[    0.000000]  modified: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  modified: 00000000fec00000 - 00000000fec01000 (reserved)
[    0.000000]  modified: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  modified: 00000000ffff0000 - 0000000100000000 (reserved)
[    0.000000] initial memory mapped : 0 - 00c00000
[    0.000000] init_memory_mapping: 0000000000000000-00000000377fe000
[    0.000000] Using x86 segment limits to approximate NX protection
[    0.000000]  0000000000 - 0000400000 page 4k
[    0.000000]  0000400000 - 0037400000 page 2M
[    0.000000]  0037400000 - 00377fe000 page 4k
[    0.000000] kernel direct mapping tables up to 377fe000 @ 10000-15000
[    0.000000] RAMDISK: 297e0000 - 29f6790c
[    0.000000] ACPI: RSDP 000f88b0 00014 (v00 HPQOEM)
[    0.000000] ACPI: RSDT 37ee3000 00038 (v01 HPQOEM SLIC-BPC 42302E31 AWRD 0000
0000)
[    0.000000] ACPI: FACP 37ee3080 00074 (v01 HPQOEM SLIC-BPC 42302E31 AWRD 0000
0000)
[    0.000000] ACPI: DSDT 37ee3100 066CE (v01 HPQOEM AWRDACPI 00001000 MSFT 0300
0000)
[    0.000000] ACPI: FACS 37ee0000 00040
[    0.000000] ACPI: HPET 37ee9880 00038 (v01 HPQOEM SLIC-BPC 42302E31 AWRD 0000
0098)
[    0.000000] ACPI: WDRT 37ee98c0 00047 (v01 HPQOEM SLIC-BPC 42302E31 AWRD 0000
0000)
[    0.000000] ACPI: MCFG 37ee9940 0003C (v01 HPQOEM SLIC-BPC 42302E31 AWRD 0000
0000)
[    0.000000] ACPI: APIC 37ee9800 00066 (v01 HPQOEM SLIC-BPC 42302E31 AWRD 0000
0000)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] 6MB HIGHMEM available.
[    0.000000] 887MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 377fe000
[    0.000000]   low ram: 0 - 377fe000
[    0.000000]   node 0 low ram: 00000000 - 377fe000
[    0.000000]   node 0 bootmap 00011000 - 00017f00
[    0.000000] (9 early reservations) ==> bootmem [0000000000 - 00377fe000]
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 -
 0000001000]
[    0.000000]   #1 [0000001000 - 0000002000]    EX TRAMPOLINE ==> [0000001000 -
 0000002000]
[    0.000000]   #2 [0000006000 - 0000007000]       TRAMPOLINE ==> [0000006000 -
 0000007000]
[    0.000000]   #3 [0000100000 - 00008b0160]    TEXT DATA BSS ==> [0000100000 -
 00008b0160]
[    0.000000]   #4 [00297e0000 - 0029f6790c]          RAMDISK ==> [00297e0000 -
 0029f6790c]
[    0.000000]   #5 [000009f800 - 0000100000]    BIOS reserved ==> [000009f800 -
 0000100000]
[    0.000000]   #6 [00008b1000 - 00008b40f0]              BRK ==> [00008b1000 -
 00008b40f0]
[    0.000000]   #7 [0000010000 - 0000011000]          PGTABLE ==> [0000010000 -
 0000011000]
[    0.000000]   #8 [0000011000 - 0000018000]          BOOTMAP ==> [0000011000 -
 0000018000]
[    0.000000] found SMP MP-table at [c00f4830] f4830
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000010 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x000377fe
[    0.000000]   HighMem  0x000377fe -> 0x00037ee0
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[2] active PFN ranges
[    0.000000]     0: 0x00000010 -> 0x0000009f
[    0.000000]     0: 0x00000100 -> 0x00037ee0
[    0.000000] On node 0 totalpages: 228975
[    0.000000] free_area_init_node: node 0, pgdat c078ad40, node_mem_map c100020
0
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3951 pages, LIFO batch:0
[    0.000000]   Normal zone: 1744 pages used for memmap
[    0.000000]   Normal zone: 221486 pages, LIFO batch:31
[    0.000000]   HighMem zone: 14 pages used for memmap
[    0.000000]   HighMem zone: 1748 pages, LIFO batch:0
[    0.000000] Using APIC driver default
[    0.000000] ACPI: PM-Timer IO Port: 0x408
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 3, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: IOAPIC (id[0x03] address[0xfecc0000] gsi_base[24])
[    0.000000] IOAPIC[1]: apic_id 3, version 3, address 0xfecc0000, GSI 24-47
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 low level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 2 I/O APICs
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x11068201 base: 0xfe800000
[    0.000000] SMP: Allowing 1 CPUs, 0 hotplug CPUs
[    0.000000] nr_irqs_gsi: 48
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000f0000
[    0.000000] PM: Registered nosave memory: 00000000000f0000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 37f00000 (gap: 37f00000:a810
0000)
[    0.000000] NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:1 nr_node_ids:1
[    0.000000] PERCPU: Embedded 14 pages at c1704000, static data 35612 bytes
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pag
es: 227185
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.31-23-generic r
oot=UUID=dacb0dba-f89e-4acf-988f-f6023dd130ca ro quiet splash
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] allocated 4581440 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memor
y cgroups
[    0.000000] Initializing HighMem for node 0 (000377fe:00037ee0)
[    0.000000] Memory: 887512k/916352k available (4584k kernel code, 28132k rese
rved, 2149k data, 544k init, 7048k highmem)
[    0.000000] virtual kernel memory layout:
[    0.000000]     fixmap  : 0xfff1d000 - 0xfffff000   ( 904 kB)
[    0.000000]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[    0.000000]     vmalloc : 0xf7ffe000 - 0xff7fe000   ( 120 MB)
[    0.000000]     lowmem  : 0xc0000000 - 0xf77fe000   ( 887 MB)
[    0.000000]       .init : 0xc0794000 - 0xc081c000   ( 544 kB)
[    0.000000]       .data : 0xc057a248 - 0xc0793848   (2149 kB)
[    0.000000]       .text : 0xc0100000 - 0xc057a248   (4584 kB)
[    0.000000] Checking if this processor honours the WP bit even in supervisor 
mode...Ok.
[    0.000000] SLUB: Genslabs=13, HWalign=64, Order=0-3, MinObjects=0, CPUs=1, N
odes=1
[    0.000000] NR_IRQS:2304 nr_irqs:256
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 1799.907 MHz processor.
[    0.001213] Console: colour VGA+ 80x25
[    0.001219] console [tty0] enabled
[    0.001428] hpet clockevent registered
[    0.001433] HPET: 3 timers in total, 0 timers will be used for per-cpu timer
[    0.001441] Calibrating delay loop (skipped), value calculated using timer fr
equency.. 3599.81 BogoMIPS (lpj=7199628)
[    0.001471] Security Framework initialized
[    0.001505] AppArmor: AppArmor initialized
[    0.001516] Mount-cache hash table entries: 512
[    0.001680] Initializing cgroup subsys ns
[    0.001686] Initializing cgroup subsys cpuacct
[    0.001694] Initializing cgroup subsys memory
[    0.001705] Initializing cgroup subsys devices
[    0.001710] Initializing cgroup subsys freezer
[    0.001714] Initializing cgroup subsys net_cls
[    0.001733] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[    0.001738] CPU: L2 Cache: 128K (64 bytes/line)
[    0.001752] Performance Counters: 
[    0.001760] Checking 'hlt' instruction... OK.
[    0.016938] SMP alternatives: switching to UP code
[    0.028024] Freeing SMP alternatives: 20k freed
[    0.028058] ACPI: Core revision 20090521
[    0.042697] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.082388] CPU0: Centaur VIA C7-D Processor 1800MHz stepping 00
[    0.084001] Brought up 1 CPUs
[    0.084001] Total of 1 processors activated (3599.81 BogoMIPS).
[    0.084001] CPU0 attaching NULL sched-domain.
[    0.084001] HP Compaq Laptop series board detected. Selecting BIOS-method for
 reboots.
[    0.084001] Booting paravirtualized kernel on bare hardware
[    0.084001] regulator: core version 0.5
[    0.084001] Time: 13:43:03  Date: 03/31/11
[    0.084001] NET: Registered protocol family 16
[    0.084001] EISA bus registered
[    0.084001] ACPI: bus type pci registered
[    0.084001] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 255
[    0.084001] PCI: MCFG area at e0000000 reserved in E820
[    0.084001] PCI: Using MMCONFIG for extended config space
[    0.084001] PCI: Using configuration type 1 for base access
[    0.084001] bio: create slab <bio-0> at 0
[    0.084580] ACPI: EC: Look up EC in DSDT
[    0.092113] ACPI Warning: Package List length (8) larger than NumElements cou
nt (5), truncated
[    0.092123]  20090521 dsobject-502
[    0.092283] ACPI Warning: Package List length (8) larger than NumElements cou
nt (5), truncated
[    0.092292]  20090521 dsobject-502
[    0.092444] ACPI Warning: Package List length (8) larger than NumElements cou
nt (5), truncated
[    0.092453]  20090521 dsobject-502
[    0.101477] ACPI: Interpreter enabled
[    0.101492] ACPI: (supports S0 S3 S4 S5)
[    0.101533] ACPI: Using IOAPIC for interrupt routing
[    0.114133] ACPI: No dock devices found.
[    0.114684] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.114764] pci 0000:00:00.0: reg 10 32bit mmio: [0xc8000000-0xcfffffff]
[    0.115315] pci 0000:00:02.0: PME# supported from D0 D3hot D3cold
[    0.115323] pci 0000:00:02.0: PME# disabled
[    0.115403] pci 0000:00:03.0: PME# supported from D0 D3hot D3cold
[    0.115411] pci 0000:00:03.0: PME# disabled
[    0.115486] pci 0000:00:0f.0: reg 10 io port: [0xfc00-0xfc07]
[    0.115496] pci 0000:00:0f.0: reg 14 io port: [0xf800-0xf803]
[    0.115507] pci 0000:00:0f.0: reg 18 io port: [0xf400-0xf407]
[    0.115517] pci 0000:00:0f.0: reg 1c io port: [0xf000-0xf003]
[    0.115527] pci 0000:00:0f.0: reg 20 io port: [0xec00-0xec0f]
[    0.115538] pci 0000:00:0f.0: reg 24 io port: [0xe800-0xe8ff]
[    0.115618] pci 0000:00:0f.1: reg 20 io port: [0xe400-0xe40f]
[    0.115712] pci 0000:00:10.0: reg 20 io port: [0xe000-0xe01f]
[    0.115742] pci 0000:00:10.0: supports D1 D2
[    0.115747] pci 0000:00:10.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.115754] pci 0000:00:10.0: PME# disabled
[    0.115809] pci 0000:00:10.1: reg 20 io port: [0xdc00-0xdc1f]
[    0.115839] pci 0000:00:10.1: supports D1 D2
[    0.115844] pci 0000:00:10.1: PME# supported from D0 D1 D2 D3hot D3cold
[    0.115851] pci 0000:00:10.1: PME# disabled
[    0.115906] pci 0000:00:10.2: reg 20 io port: [0xd800-0xd81f]
[    0.115936] pci 0000:00:10.2: supports D1 D2
[    0.115940] pci 0000:00:10.2: PME# supported from D0 D1 D2 D3hot D3cold
[    0.115947] pci 0000:00:10.2: PME# disabled
[    0.116019] pci 0000:00:10.3: reg 20 io port: [0xd400-0xd41f]
[    0.116050] pci 0000:00:10.3: supports D1 D2
[    0.116054] pci 0000:00:10.3: PME# supported from D0 D1 D2 D3hot D3cold
[    0.116061] pci 0000:00:10.3: PME# disabled
[    0.116106] pci 0000:00:10.4: reg 10 32bit mmio: [0xdffff000-0xdffff0ff]
[    0.116158] pci 0000:00:10.4: supports D1 D2
[    0.116163] pci 0000:00:10.4: PME# supported from D0 D1 D2 D3hot D3cold
[    0.116170] pci 0000:00:10.4: PME# disabled
[    0.116518] pci 0000:01:00.0: reg 10 32bit mmio: [0xd0000000-0xd7ffffff]
[    0.116529] pci 0000:01:00.0: reg 14 32bit mmio: [0xdd000000-0xddffffff]
[    0.116554] pci 0000:01:00.0: reg 30 32bit mmio: [0x000000-0x00ffff]
[    0.116577] pci 0000:01:00.0: supports D1 D2
[    0.116622] pci 0000:00:01.0: bridge io port: [0xb000-0xbfff]
[    0.116629] pci 0000:00:01.0: bridge 32bit mmio: [0xdd000000-0xdeffffff]
[    0.116638] pci 0000:00:01.0: bridge 32bit mmio pref: [0xd0000000-0xd7ffffff]
[    0.116691] pci 0000:00:02.0: bridge io port: [0xa000-0xafff]
[    0.116699] pci 0000:00:02.0: bridge 32bit mmio: [0xdfb00000-0xdfbfffff]
[    0.116709] pci 0000:00:02.0: bridge 64bit mmio pref: [0xdfe00000-0xdfefffff]
[    0.116764] pci 0000:00:03.0: bridge io port: [0xc000-0xcfff]
[    0.116772] pci 0000:00:03.0: bridge 32bit mmio: [0xdfd00000-0xdfdfffff]
[    0.116783] pci 0000:00:03.0: bridge 64bit mmio pref: [0xdfc00000-0xdfcfffff]
[    0.116829] pci 0000:04:05.0: reg 10 io port: [0x9c00-0x9cff]
[    0.116840] pci 0000:04:05.0: reg 14 32bit mmio: [0xdfaff000-0xdfaff0ff]
[    0.116868] pci 0000:04:05.0: reg 30 32bit mmio: [0xdfac0000-0xdfadffff]
[    0.116889] pci 0000:04:05.0: supports D1 D2
[    0.116894] pci 0000:04:05.0: PME# supported from D1 D2 D3hot D3cold
[    0.116901] pci 0000:04:05.0: PME# disabled
[    0.116942] pci 0000:00:13.1: transparent bridge
[    0.116948] pci 0000:00:13.1: bridge io port: [0x9000-0x9fff]
[    0.116956] pci 0000:00:13.1: bridge 32bit mmio: [0xdfa00000-0xdfafffff]
[    0.116965] pci 0000:00:13.1: bridge 64bit mmio pref: [0xdf900000-0xdf9fffff]
[    0.116990] pci_bus 0000:00: on NUMA node 0
[    0.117000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.117489] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEXG._PRT]
[    0.117703] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEX0._PRT]
[    0.117916] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P2PB._PRT]
[    0.220712] ACPI: PCI Root Bridge [PCI1] (0000:80)
[    0.220800] pci 0000:80:01.0: reg 10 64bit mmio: [0xc7ffc000-0xc7ffffff]
[    0.220849] pci 0000:80:01.0: PME# supported from D0 D3hot D3cold
[    0.220856] pci 0000:80:01.0: PME# disabled
[    0.220908] pci_bus 0000:80: on NUMA node 0
[    0.220916] ACPI: PCI Interrupt Routing Table [\_SB_.PCI1._PRT]
[    0.221689] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 6 7 10 11 12) *5
[    0.222001] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 6 7 10 *11 12)
[    0.222316] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 6 7 *10 11 12)
[    0.222630] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 6 7 *10 11 12)
[    0.222902] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 6 7 10 11 12) *0, disab
led.
[    0.223163] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 6 7 10 11 12) *0, disab
led.
[    0.223423] ACPI: PCI Interrupt Link [LNK0] (IRQs 3 4 6 7 10 11 12) *0, disab
led.
[    0.223708] ACPI: PCI Interrupt Link [LNK1] (IRQs 3 4 6 7 10 *11 12)
[    0.224077] SCSI subsystem initialized
[    0.224174] libata version 3.00 loaded.
[    0.224302] usbcore: registered new interface driver usbfs
[    0.224328] usbcore: registered new interface driver hub
[    0.224366] usbcore: registered new device driver usb
[    0.224589] ACPI: WMI: Mapper loaded
[    0.224593] PCI: Using ACPI for IRQ routing
[    0.224866] Bluetooth: Core ver 2.15
[    0.224919] NET: Registered protocol family 31
[    0.224923] Bluetooth: HCI device and connection manager initialized
[    0.224928] Bluetooth: HCI socket layer initialized
[    0.224932] NetLabel: Initializing
[    0.224936] NetLabel:  domain hash size = 128
[    0.224939] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.224961] NetLabel:  unlabeled traffic allowed by default
[    0.225015] hpet0: at MMIO 0xfe800000, IRQs 2, 8, 0
[    0.225025] hpet0: 3 comparators, 32-bit 14.318180 MHz counter
[    0.230514] pnp: PnP ACPI init
[    0.230546] ACPI: bus type pnp registered
[    0.238834] pnp: PnP ACPI: found 19 devices
[    0.238840] ACPI: ACPI bus type pnp unregistered
[    0.238848] PnPBIOS: Disabled by ACPI PNP
[    0.238866] system 00:01: ioport range 0x400-0x47f has been reserved
[    0.238873] system 00:01: ioport range 0x500-0x50f has been reserved
[    0.238886] system 00:02: iomem range 0xfea00000-0xfea000ff has been reserved
[    0.238897] system 00:03: iomem range 0xf0001000-0xf0001fff has been reserved
[    0.238909] system 00:04: iomem range 0xf0002000-0xf0002fff has been reserved
[    0.238921] system 00:05: ioport range 0x4d0-0x4d1 has been reserved
[    0.238928] system 00:05: ioport range 0x290-0x297 has been reserved
[    0.238943] system 00:0f: iomem range 0xf0000000-0xf0000fff has been reserved
[    0.238953] system 00:10: iomem range 0xe0000000-0xefffffff has been reserved
[    0.238965] system 00:12: iomem range 0xf0000-0xfffff could not be reserved
[    0.238972] system 00:12: iomem range 0xfe800000-0xfe8000ff has been reserved
[    0.238979] system 00:12: iomem range 0xfea00000-0xfea000ff has been reserved
[    0.238986] system 00:12: iomem range 0x37ee0000-0x37efffff could not be rese
rved
[    0.238993] system 00:12: iomem range 0xffff0000-0xffffffff has been reserved
[    0.239000] system 00:12: iomem range 0x0-0x9ffff could not be reserved
[    0.239007] system 00:12: iomem range 0x100000-0x37edffff could not be reserv
ed
[    0.239014] system 00:12: iomem range 0xfec00000-0xfec00fff could not be rese
rved
[    0.239021] system 00:12: iomem range 0xfee00000-0xfee00fff has been reserved
[    0.239028] system 00:12: iomem range 0xfff80000-0xfffeffff has been reserved
[    0.273791] AppArmor: AppArmor Filesystem Enabled
[    0.273825] pci 0000:04:05.0: BAR 6: address space collision on of device [0x
dfac0000-0xdfadffff]
[    0.273870] pci 0000:00:01.0: PCI bridge, secondary bus 0000:01
[    0.273877] pci 0000:00:01.0:   IO window: 0xb000-0xbfff
[    0.273885] pci 0000:00:01.0:   MEM window: 0xdd000000-0xdeffffff
[    0.273894] pci 0000:00:01.0:   PREFETCH window: 0xd0000000-0xd7ffffff
[    0.273901] pci 0000:00:02.0: PCI bridge, secondary bus 0000:02
[    0.273907] pci 0000:00:02.0:   IO window: 0xa000-0xafff
[    0.273916] pci 0000:00:02.0:   MEM window: 0xdfb00000-0xdfbfffff
[    0.273923] pci 0000:00:02.0:   PREFETCH window: 0x000000dfe00000-0x000000dfe
fffff
[    0.273933] pci 0000:00:03.0: PCI bridge, secondary bus 0000:03
[    0.273940] pci 0000:00:03.0:   IO window: 0xc000-0xcfff
[    0.273949] pci 0000:00:03.0:   MEM window: 0xdfd00000-0xdfdfffff
[    0.273957] pci 0000:00:03.0:   PREFETCH window: 0x000000dfc00000-0x000000dfc
fffff
[    0.273969] pci 0000:00:13.1: PCI bridge, secondary bus 0000:04
[    0.273975] pci 0000:00:13.1:   IO window: 0x9000-0x9fff
[    0.273983] pci 0000:00:13.1:   MEM window: 0xdfa00000-0xdfafffff
[    0.273991] pci 0000:00:13.1:   PREFETCH window: 0x000000df900000-0x000000df9
fffff
[    0.274010] pci 0000:00:01.0: setting latency timer to 64
[    0.274025]   alloc irq_desc for 27 on node -1
[    0.274029]   alloc kstat_irqs on node -1
[    0.274040] pci 0000:00:02.0: PCI INT A -> GSI 27 (level, low) -> IRQ 27
[    0.274047] pci 0000:00:02.0: setting latency timer to 64
[    0.274058]   alloc irq_desc for 31 on node -1
[    0.274062]   alloc kstat_irqs on node -1
[    0.274069] pci 0000:00:03.0: PCI INT A -> GSI 31 (level, low) -> IRQ 31
[    0.274076] pci 0000:00:03.0: setting latency timer to 64
[    0.274087] pci 0000:00:13.1: setting latency timer to 64
[    0.274095] pci_bus 0000:00: resource 0 io:  [0x00-0xffff]
[    0.274101] pci_bus 0000:00: resource 1 mem: [0x000000-0xffffffff]
[    0.274108] pci_bus 0000:01: resource 0 io:  [0xb000-0xbfff]
[    0.274114] pci_bus 0000:01: resource 1 mem: [0xdd000000-0xdeffffff]
[    0.274120] pci_bus 0000:01: resource 2 pref mem [0xd0000000-0xd7ffffff]
[    0.274126] pci_bus 0000:02: resource 0 io:  [0xa000-0xafff]
[    0.274132] pci_bus 0000:02: resource 1 mem: [0xdfb00000-0xdfbfffff]
[    0.274138] pci_bus 0000:02: resource 2 pref mem [0xdfe00000-0xdfefffff]
[    0.274145] pci_bus 0000:03: resource 0 io:  [0xc000-0xcfff]
[    0.274151] pci_bus 0000:03: resource 1 mem: [0xdfd00000-0xdfdfffff]
[    0.274157] pci_bus 0000:03: resource 2 pref mem [0xdfc00000-0xdfcfffff]
[    0.274163] pci_bus 0000:04: resource 0 io:  [0x9000-0x9fff]
[    0.274169] pci_bus 0000:04: resource 1 mem: [0xdfa00000-0xdfafffff]
[    0.274175] pci_bus 0000:04: resource 2 pref mem [0xdf900000-0xdf9fffff]
[    0.274181] pci_bus 0000:04: resource 3 io:  [0x00-0xffff]
[    0.274187] pci_bus 0000:04: resource 4 mem: [0x000000-0xffffffff]
[    0.274193] pci_bus 0000:80: resource 0 io:  [0x00-0xffff]
[    0.274199] pci_bus 0000:80: resource 1 mem: [0x000000-0xffffffff]
[    0.274264] NET: Registered protocol family 2
[    0.274441] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.275053] TCP established hash table entries: 131072 (order: 8, 1048576 byt
es)
[    0.276438] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.277138] TCP: Hash tables configured (established 131072 bind 65536)
[    0.277145] TCP reno registered
[    0.277299] NET: Registered protocol family 1
[    0.277403] Trying to unpack rootfs image as initramfs...
[    0.504044] Switched to high resolution mode on CPU 0
[    0.699592] Freeing initrd memory: 7710k freed
[    0.707248] cpufreq-nforce2: No nForce2 chipset.
[    0.707342] Scanning for low memory corruption every 60 seconds
[    0.707527] audit: initializing netlink socket (disabled)
[    0.707564] type=2000 audit(1301578983.704:1): initialized
[    0.725316] highmem bounce pool size: 64 pages
[    0.725326] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    0.728138] VFS: Disk quotas dquot_6.5.2
[    0.728263] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.729302] fuse init (API version 7.12)
[    0.729452] msgmni has been set to 1735
[    0.729792] alg: No test for stdrng (krng)
[    0.729812] io scheduler noop registered
[    0.729816] io scheduler anticipatory registered
[    0.729821] io scheduler deadline registered
[    0.729922] io scheduler cfq registered (default)
[    0.729937] pci 0000:00:00.0: MSI quirk detected; MSI disabled
[    0.729962] pci 0000:00:01.0: disabling DAC on VIA PCI bridge
[    0.730072] pci 0000:01:00.0: Boot video device
[    0.730253] pcieport-driver 0000:00:02.0: setting latency timer to 64
[    0.730420] pcieport-driver 0000:00:03.0: setting latency timer to 64
[    0.730578] aer 0000:00:02.0:pcie02: AER service couldn't init device: no _OS
C support
[    0.730591] aer 0000:00:03.0:pcie02: AER service couldn't init device: no _OS
C support
[    0.730607] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.730757] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.730971] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/inp
ut0
[    0.730978] ACPI: Power Button [PWRF]
[    0.731066] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/
input/input1
[    0.731072] ACPI: Power Button [PWRB]
[    0.731162] fan PNP0C0B:00: registered as cooling_device0
[    0.731172] ACPI: Fan [FAN] (on)
[    0.732719] processor LNXCPU:00: registered as cooling_device1
[    0.740590] thermal LNXTHERM:01: registered as thermal_zone0
[    0.740604] ACPI: Thermal Zone [THRM] (27 C)
[    0.740699] isapnp: Scanning for PnP cards...
[    1.094584] isapnp: No Plug & Play device found
[    1.096734] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    1.096880] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    1.097347] 00:0b: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    1.099203] brd: module loaded
[    1.100040] loop: module loaded
[    1.100234] input: Macintosh mouse button emulation as /devices/virtual/input
/input2
[    1.101309] pata_via 0000:00:0f.1: version 0.3.4
[    1.101522] scsi0 : pata_via
[    1.101686] scsi1 : pata_via
[    1.103808] ata1: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xe400 irq 14
[    1.103815] ata2: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xe408 irq 15
[    1.104224]   alloc irq_desc for 21 on node -1
[    1.104229]   alloc kstat_irqs on node -1
[    1.104240] pata_acpi 0000:00:0f.0: PCI INT B -> GSI 21 (level, low) -> IRQ 2
1
[    1.104307] pata_acpi 0000:00:0f.0: PCI INT B disabled
[    1.104840] Fixed MDIO Bus: probed
[    1.104905] PPP generic driver version 2.4.2
[    1.105090] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    1.105131] ehci_hcd 0000:00:10.4: PCI INT C -> GSI 21 (level, low) -> IRQ 21
[    1.105158] ehci_hcd 0000:00:10.4: EHCI Host Controller
[    1.105214] ehci_hcd 0000:00:10.4: new USB bus registered, assigned bus numbe
r 1
[    1.105259] ehci_hcd 0000:00:10.4: debug port 1
[    1.105290] ehci_hcd 0000:00:10.4: irq 21, io mem 0xdffff000
[    1.116015] ehci_hcd 0000:00:10.4: USB 2.0 started, EHCI 1.00
[    1.116135] usb usb1: configuration #1 chosen from 1 choice
[    1.116184] hub 1-0:1.0: USB hub found
[    1.116198] hub 1-0:1.0: 8 ports detected
[    1.116295] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    1.116337] uhci_hcd: USB Universal Host Controller Interface driver
[    1.116418]   alloc irq_desc for 20 on node -1
[    1.116423]   alloc kstat_irqs on node -1
[    1.116455] uhci_hcd 0000:00:10.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    1.116468] uhci_hcd 0000:00:10.0: UHCI Host Controller
[    1.116531] uhci_hcd 0000:00:10.0: new USB bus registered, assigned bus numbe
r 2
[    1.116571] uhci_hcd 0000:00:10.0: irq 20, io base 0x0000e000
[    1.116710] usb usb2: configuration #1 chosen from 1 choice
[    1.116760] hub 2-0:1.0: USB hub found
[    1.116773] hub 2-0:1.0: 2 ports detected
[    1.116840]   alloc irq_desc for 22 on node -1
[    1.116844]   alloc kstat_irqs on node -1
[    1.116852] uhci_hcd 0000:00:10.1: PCI INT B -> GSI 22 (level, low) -> IRQ 22
[    1.116863] uhci_hcd 0000:00:10.1: UHCI Host Controller
[    1.116914] uhci_hcd 0000:00:10.1: new USB bus registered, assigned bus numbe
r 3
[    1.116950] uhci_hcd 0000:00:10.1: irq 22, io base 0x0000dc00
[    1.117079] usb usb3: configuration #1 chosen from 1 choice
[    1.117127] hub 3-0:1.0: USB hub found
[    1.117139] hub 3-0:1.0: 2 ports detected
[    1.117202] uhci_hcd 0000:00:10.2: PCI INT C -> GSI 21 (level, low) -> IRQ 21
[    1.117211] uhci_hcd 0000:00:10.2: UHCI Host Controller
[    1.117258] uhci_hcd 0000:00:10.2: new USB bus registered, assigned bus numbe
r 4
[    1.117283] uhci_hcd 0000:00:10.2: irq 21, io base 0x0000d800
[    1.117417] usb usb4: configuration #1 chosen from 1 choice
[    1.117461] hub 4-0:1.0: USB hub found
[    1.117474] hub 4-0:1.0: 2 ports detected
[    1.117536]   alloc irq_desc for 23 on node -1
[    1.117541]   alloc kstat_irqs on node -1
[    1.117549] uhci_hcd 0000:00:10.3: PCI INT D -> GSI 23 (level, low) -> IRQ 23
[    1.117558] uhci_hcd 0000:00:10.3: UHCI Host Controller
[    1.117611] uhci_hcd 0000:00:10.3: new USB bus registered, assigned bus numbe
r 5
[    1.117646] uhci_hcd 0000:00:10.3: irq 23, io base 0x0000d400
[    1.117787] usb usb5: configuration #1 chosen from 1 choice
[    1.117832] hub 5-0:1.0: USB hub found
[    1.117845] hub 5-0:1.0: 2 ports detected
[    1.118005] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq
 1,12
[    1.118345] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.118358] serio: i8042 AUX port at 0x60,0x64 irq 12
[    1.118459] mice: PS/2 mouse device common for all mice
[    1.118609] rtc_cmos 00:08: RTC can wake from S4
[    1.118666] rtc_cmos 00:08: rtc core: registered rtc_cmos as rtc0
[    1.118702] rtc0: alarms up to one year, y3k, 242 bytes nvram, hpet irqs
[    1.118917] device-mapper: uevent: version 1.0.3
[    1.119102] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: dm-d
evel@redhat.com
[    1.119227] device-mapper: multipath: version 1.1.0 loaded
[    1.119233] device-mapper: multipath round-robin: version 1.0.0 loaded
[    1.119458] EISA: Probing bus 0 at eisa.0
[    1.119505] EISA: Detected 0 cards.
[    1.119594] cpuidle: using governor ladder
[    1.119598] cpuidle: using governor menu
[    1.120642] TCP cubic registered
[    1.120946] NET: Registered protocol family 10
[    1.121792] lo: Disabled Privacy Extensions
[    1.122395] NET: Registered protocol family 17
[    1.122439] Bluetooth: L2CAP ver 2.13
[    1.122443] Bluetooth: L2CAP socket layer initialized
[    1.122448] Bluetooth: SCO (Voice Link) ver 0.6
[    1.122451] Bluetooth: SCO socket layer initialized
[    1.122514] Bluetooth: RFCOMM TTY layer initialized
[    1.122519] Bluetooth: RFCOMM socket layer initialized
[    1.122523] Bluetooth: RFCOMM ver 1.11
[    1.122936] longhaul: APIC detected. Longhaul is currently broken in this con
figuration.
[    1.122948] Using IPI No-Shortcut mode
[    1.123091] PM: Resume from disk failed.
[    1.123110] registered taskstats version 1
[    1.123372]   Magic number: 3:374:737
[    1.123526] rtc_cmos 00:08: setting system clock to 2011-03-31 13:43:04 UTC (
1301578984)
[    1.123532] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.123536] EDD information not available.
[    1.138163] input: AT Translated Set 2 keyboard as /devices/platform/i8042/se
rio0/input/input3
[    1.256129] ata2: port disabled. ignoring.
[    1.256160] Freeing unused kernel memory: 544k freed
[    1.256869] Write protecting the kernel text: 4588k
[    1.256948] Write protecting the kernel read-only data: 1840k
[    1.614886] Linux agpgart interface v0.103
[    1.655383] agpgart: Detected VIA P4M900 chipset
[    1.661263] agpgart-via 0000:00:00.0: AGP aperture is 128M @ 0xc8000000
[    1.666862] sata_via 0000:00:0f.0: version 2.4
[    1.666884] sata_via 0000:00:0f.0: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[    1.666936] sata_via 0000:00:0f.0: routed to hard irq line 11
[    1.676682] scsi2 : sata_via
[    1.676851] scsi3 : sata_via
[    1.679514] ata3: SATA max UDMA/133 cmd 0xfc00 ctl 0xf800 bmdma 0xec00 irq 21
[    1.679521] ata4: SATA max UDMA/133 cmd 0xf400 ctl 0xf000 bmdma 0xec08 irq 21
[    1.968020] ata3: SATA link up 1.5 Gbps (SStatus 123 SControl 300)
[    2.132207] ata3.00: ATA-8: Hitachi HDS721016CLA382, JPEOA3BF, max UDMA/133
[    2.132214] ata3.00: 312581808 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    2.148227] ata3.00: configured for UDMA/133
[    2.148390] scsi 2:0:0:0: Direct-Access     ATA      Hitachi HDS72101 JPEO PQ
: 0 ANSI: 5
[    2.148636] sd 2:0:0:0: Attached scsi generic sg0 type 0
[    2.148704] sd 2:0:0:0: [sda] 312581808 512-byte logical blocks: (160 GB/149 
GiB)
[    2.148765] sd 2:0:0:0: [sda] Write Protect is off
[    2.148771] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    2.148803] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, does
n't support DPO or FUA
[    2.148989]  sda: sda1 sda2 < sda5 sda6 >
[    2.182595] sd 2:0:0:0: [sda] Attached SCSI disk
[    2.352020] ata4: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    2.516206] ata4.00: ATAPI: hp      DVD-ROM TS-H353C, H410, max UDMA/100
[    2.532225] ata4.00: configured for UDMA/100
[    2.535305] scsi 3:0:0:0: CD-ROM            hp       DVD-ROM TS-H353C H410 PQ
: 0 ANSI: 5
[    2.540562] sr0: scsi3-mmc drive: 1x/8x cd/rw xa/form2 cdda tray
[    2.540570] Uniform CD-ROM driver Revision: 3.20
[    2.540776] sr 3:0:0:0: Attached scsi CD-ROM sr0
[    2.540881] sr 3:0:0:0: Attached scsi generic sg1 type 5
[    2.547183] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    2.547208]   alloc irq_desc for 18 on node -1
[    2.547213]   alloc kstat_irqs on node -1
[    2.547224] r8169 0000:04:05.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    2.547257] r8169 0000:04:05.0: no PCI Express capability
[    2.559704] eth0: RTL8169sc/8110sc at 0xf807e000, 6c:62:6d:0a:e8:ef, XID 1800
0000 IRQ 18
[    3.325247] xor: automatically using best checksumming function: pIII_sse
[    3.344006]    pIII_sse  :  3946.000 MB/sec
[    3.344011] xor: using function: pIII_sse (3946.000 MB/sec)
[    3.351155] device-mapper: dm-raid45: initialized v0.2594b
[    3.650045] PM: Starting manual resume from disk
[    3.650054] PM: Resume from partition 8:5
[    3.650057] PM: Checking hibernation image.
[    3.650306] PM: Resume from disk failed.
[    3.674396] EXT3-fs: INFO: recovery required on readonly filesystem.
[    3.674404] EXT3-fs: write access will be enabled during recovery.
[    5.134424] kjournald starting.  Commit interval 5 seconds
[    5.134452] EXT3-fs: sda1: orphan cleanup on readonly fs
[    5.134463] ext3_orphan_cleanup: deleting unreferenced inode 1510838
[    5.134525] ext3_orphan_cleanup: deleting unreferenced inode 1509729
[    5.134545] EXT3-fs: sda1: 2 orphan inodes deleted
[    5.134549] EXT3-fs: recovery complete.
[    5.158237] EXT3-fs: mounted filesystem with ordered data mode.
[    6.233546] type=1505 audit(1301578989.608:2): operation="profile_load" pid=3
80 name=/usr/share/gdm/guest-session/Xsession
[    6.245895] type=1505 audit(1301578989.620:3): operation="profile_load" pid=3
81 name=/sbin/dhclient3
[    6.246394] type=1505 audit(1301578989.620:4): operation="profile_load" pid=3

```

---

### Post by crispy_420 on 2011-03-31
My first guess would be failing hardware possibly. Hard drive or memory maybe but this is just an idea.

---

### Post by DunZH on 2011-03-31
Sorry I should have specified, its a basically new machine, well almost a year old now.  And it has pretty much been like this since I got it.  So probably not failing hardware, but one can always hope.  I think I have some basic warranty on it.

Do you think putting more memory in there would help?  Its the processor that labors from time to time, not memory usage...

---

### Post by DunZH on 2011-03-31
One thing I did that helped was change on demand resource management to performance.  That helped a lot.  And its manageable, so long as I keep firefox under control, which is a real hog.

But what I was really looking for is some help to know how to troubleshoot the freezes...that's my real concern.

---

### Post by alazou on 2011-03-31
Hi
Your cpu is indeed slow but I don't think that causing the freezes.

When your PC freezes, at next reboot try looking at the end of /var/log/Xorg.0.log.old and /var/log/Xorg.0.log.
```
tail -n 40 /var/log/Xorg.0.log.old
tail -n 40 /var/log/Xorg.0.log

```

Also try looking for any errors in those files :
```

grep "EE" /var/log/Xorg.0.log

```

Also why don't you try the 10.10 release of ubuntu ? A lot of work went down the last couple of year in the graphic stack, maybe your problems are caused by an ancient bug

---

### Post by Corsain on 2011-03-31
I currently use both OS's. I have far less issues with ubuntu 10.10 than 9.10. The only reason both computer don't have 10.10 is because i have old imac 2 g4. It cant handle the OS. It installs but never boots. I reach a red screen and it never boots.:(

---

### Post by alazou on 2011-03-31
I'm not sure but I think the ppc architecture have been dropped by the newer ubuntus or have (very) limited support, that could be why the imac won't work. 

But I'm not sure I understand : 10.10 is installed on your hp machine then ? If it is, What I would recommend is using a lighter based distro like xubuntu.
(Never mind just noticed you are not the original poster, Corsain)

---

### Post by DunZH on 2011-03-31
Ha ha I have been threadjacked~!  While I was asleep!

Hey Corsain, pls start a new thread with your question. Try to provide as much information as possible about the problem and your setup.  At least try to do better than I did.  :D

You'll get better results that way  :P

alazou thanks for the info its really helpful, lets me take a step forward.  I will check those when the newest freeze happens, and I may try 10.10 after all, if you think it helps.

Oh, and do you think more memory would make a difference in my performance?

---

### Post by DunZH on 2011-03-31
By the way in case its useful to anyone else, what I did to really improve performance (even though the cps still goes crazy sometimes) is here [http://ubuntuforums.org/showthread.php?t=1152095](http://ubuntuforums.org/showthread.php?t=1152095)

```
**[COLOR=#cc0000]CPUFREQ tweak:[/COLOR]** this helps to get more juice from your processor ([original thread]("http://ubuntuforums.org/showpost.php?p=7394265&postcount=7")).

Run this command:
gksudo gedit /etc/init/d/ondemand

Then find **echo -n ondemand > $CPUFREQ** and replace it with **echo -n performance > $CPUFREQ**
```

---

### Post by alazou on 2011-03-31
> **DunZH said:**
> 
Oh, and do you think more memory would make a difference in my performance?

It depends on what the bottleneck is, really. But majority of the time it will improve performance drastically. How much do you have ATM ?

> 
By the way in case its useful to anyone else, what I did to really improve performance (even though the cps still goes crazy sometimes) is here [http://ubuntuforums.org/showthread.php?t=1152095](http://ubuntuforums.org/showthread.php?t=1152095)

Did it really improve your performance by much ? That would indicate either that the CPU is badly designed or the driver in the kernel is not optimized. C7 is an obscure processor indeed :).

Now that I think about it, the freezes could be CPU related, in that case this file could be investigated :
```

gksudo gedit /var/log/messages

```
The messages are ordered by date, you can find where the freeze occur by scrolling I guess. But beware, CPU related freezes are not easy to resole.

---

### Post by alazou on 2011-03-31
look at what I just found :
[http://fixunix.com/kernel/496855-strange-freeze-via-c7-dedicated-server-libc-2-6-1-a.html](http://fixunix.com/kernel/496855-strange-freeze-via-c7-dedicated-server-libc-2-6-1-a.html)

---

### Post by DunZH on 2011-04-01
Hey alazou:

Ok cool that is an interesting link, I just looked quickly at it, doesn't look like it provides a fix but its nice to know I am not alone :D

For the memory, I have one gig now but the specs say that the system downgrades the memory so that it registers as 800 mb.  I could put another 2 gig stick in there for 3 gigs of memory that would show up as 2.2 or so...

What I don't know is will it help, meaning with performance not the freezes, which I may have to live with heh.  The memory isn't stressed at all according to the system monitor, its stable and low.

Right now in the system monitor things are a bit better, I downgraded my cpu speed in my CPU Frequency monitor to 1.2 gigs , and that has worked well.  Just upped it back to 1.40 to, let's see.

But, using chrome now instead of ff.  ff is some serious bloat I guess.  Real hog.  Seems to be a big improvement.

---

### Post by DunZH on 2011-04-01
This gksudo gedit /var/log/messages

Gives me a lot of stuff, but really a lot of this:

```
Mar 28 02:48:46 zhuang283-desktop pulseaudio[1687]: ratelimit.c: 175 events suppressed
Mar 28 02:57:57 zhuang283-desktop pulseaudio[1687]: ratelimit.c: 175 events suppressed
Mar 28 02:58:55 zhuang283-desktop pulseaudio[1687]: ratelimit.c: 174 events suppressed
Mar 28 02:59:19 zhuang283-desktop pulseaudio[1687]: ratelimit.c: 177 events suppressed
Mar 28 03:02:36 zhuang283-desktop pulseaudio[1687]: ratelimit.c: 176 events suppressed
Mar 28 03:03:05 zhuang283-desktop pulseaudio[1687]: ratelimit.c: 176 events suppressed
Mar 28 03:03:27 zhuang283-desktop pulseaudio[1687]: ratelimit.c: 111 events suppressed
Mar 28 03:03:47 zhuang283-desktop pulseaudio[1687]: ratelimit.c: 116 events suppressed
Mar 28 03:04:12 zhuang283-desktop pulseaudio[1687]: ratelimit.c: 116 events suppressed
Mar 28 03:04:57 zhuang283-desktop pulseaudio[1687]: ratelimit.c: 120 events suppressed
Mar 28 03:09:12 zhuang283-desktop pulseaudio[1687]: ratelimit.c: 121 events suppressed
Mar 28 03:22:11 zhuang283-desktop pulseaudio[1687]: ratelimit.c: 160 events suppressed
Mar 28 16:20:44 zhuang283-desktop pulseaudio[1687]: ratelimit.c: 159 events suppressed
```Performance, yeah the on demand helped for sure, not a lot but it was noticeable.  Cranking down the processer worked too it seems so far, just did it today so not enough testing to be sure.

If that pulseaudio error is the culprit then I will be seeing the crash soon.  This has the azalia sound card which is, heh, buggy. I had to upgrade the alsa drivers. Hmm...

> the driver in the kernel is not optimizedIs this very hard?  Or is it just compiling the driver and installing?

---

### Post by shaoxiao on 2011-04-01
"Phoenix BIOS detected: BIOS may corrupt low RAM, working around i
t."
"Scanning 0 areas for low memory corruption"
It may be caused by the memory.

---

### Post by alazou on 2011-04-01
> **DunZH said:**
> This gksudo gedit /var/log/messages

Gives me a lot of stuff, but really a lot of this:

```
Mar 28 02:48:46 zhuang283-desktop pulseaudio[1687]: ratelimit.c: 175 events suppressed
Mar 28 02:57:57 zhuang283-desktop pulseaudio[1687]: ratelimit.c: 175 events suppressed
Mar 28 02:58:55 zhuang283-desktop pulseaudio[1687]: ratelimit.c: 174 events suppressed
Mar 28 02:59:19 zhuang283-desktop pulseaudio[1687]: ratelimit.c: 177 events suppressed
Mar 28 03:02:36 zhuang283-desktop pulseaudio[1687]: ratelimit.c: 176 events suppressed
Mar 28 03:03:05 zhuang283-desktop pulseaudio[1687]: ratelimit.c: 176 events suppressed
Mar 28 03:03:27 zhuang283-desktop pulseaudio[1687]: ratelimit.c: 111 events suppressed
Mar 28 03:03:47 zhuang283-desktop pulseaudio[1687]: ratelimit.c: 116 events suppressed
Mar 28 03:04:12 zhuang283-desktop pulseaudio[1687]: ratelimit.c: 116 events suppressed
Mar 28 03:04:57 zhuang283-desktop pulseaudio[1687]: ratelimit.c: 120 events suppressed
Mar 28 03:09:12 zhuang283-desktop pulseaudio[1687]: ratelimit.c: 121 events suppressed
Mar 28 03:22:11 zhuang283-desktop pulseaudio[1687]: ratelimit.c: 160 events suppressed
Mar 28 16:20:44 zhuang283-desktop pulseaudio[1687]: ratelimit.c: 159 events suppressed
```Performance, yeah the on demand helped for sure, not a lot but it was noticeable.  Cranking down the processer worked too it seems so far, just did it today so not enough testing to be sure.

If that pulseaudio error is the culprit then I will be seeing the crash soon.  This has the azalia sound card which is, heh, buggy. I had to upgrade the alsa drivers. Hmm...

Is this very hard?  Or is it just compiling the driver and installing?

If the driver in the kernel is at fault, the best option is to upgrade the kernel and pray the issue has been addressed. ie try 10.10.
If it's caused by glibc like it seems to be the case for the ones in the link I would suggest the same thing. If it doesn't work downgrading glibc seems to fix the issue for them.

Also the system will always allocate as much memory as possible to increase performance. even if you use at the moment, say 400Mib of memory, it's way too much (in my mind) compared to 800Mib (50%).
I have 4Gib of ram and at startup I used to have 600->800Mib with gnome, that's less than 20% and leave some latitude for the system to work without stress. If you can increase the ram, go for it. It seems the freeze where more frequent when the system was taxed.

also gksudo gedit etc... didn't open up a pop up window asking for a password ? the things that are poping up in the terminal have no value for the problem at hand

---

### Post by DunZH on 2011-04-01
Ok thanks alazou, I will wait for a crash and then look in the logs.

The output i gave is from gksudo gedit /var/log/messages, yes I have to put in the password, I guess I just took some irrelevant parts to paste in.

Ok, I will probably get some more memory just to improve performance as i need to use this box for some time.

Shaoxiao, thanks, yeah maybe more memory will help.

And then I may upgrade later, to see if it gets better. Don't want to take the time now.

---

### Post by DunZH on 2011-04-05
Well, huh weird.  No crash yet, since I limited the processor speed.

Been leaving firefox running as well, the processor ramps up but only for limited periods of time.

Probably will put in some memory but can't really complain if this is the performance I am going to get.  Much better than before.  So may not choose to re-install, although you never know I might get on it later.

---

### Post by alazou on 2011-04-05
Good to know
no need to reinstall if you ever want to. If you didn't tweek your repositoriesto much  and have a fast connection you could do an online update

---

### Post by DunZH on 2011-04-07
Ok the freeze happened.  Anything to look for in the logs?  I want to make sure that this is a freeze where nothing moves, no mouse, no nothing. I had lots of time to look at the system monitor icon.

I had restarted, and the processor had gone back to default of full 1,80 ghz.  It had only been on for a short time, and there was no heavy load on the processor at all.

I put the processor back to 1.4.  That fixed the problem before.

---

