---
title: "Boot time in lucid"
date: 2010-05-02
forum: General Help
---

### Post by ankit.vader on 2010-05-02
yesterday i read a thread in this forum that lucid takes much less time to boot, but my boot time is considerably higher( almost 50 sec) is there any settings that can be changed to improve that???

---

### Post by ankit.vader on 2010-05-02
also i cannot see neither boot screen nor the grub menu, not that it is a  problem but i think something is wrong

---

### Post by ankit.vader on 2010-05-02
also i cannot see neither boot screen nor the grub menu, not that it is a problem but i think something is wrong

---

### Post by lavinog on 2010-05-02
It would be helpful if you gave some info about your system.  Also did you do an upgrade or a clean install?
You should post the output of dmesg, lspci, lsusb and lshw.
use code tags to keep your post clean.

---

### Post by sarin_cv on 2010-05-02
I am also having the same issue but the boot time for me is almost 20-30 seconds... I am having a 2GHz dual core processor with 3GB RAM... I had installed Lucid beta1 and updated daily and with the latest update on 1st of may, it shows LTS version.... for the beta version it was more than 40 seconds for me and after updating it was reduced to 20+... On selecting ubuntu from grub, a blank screen with a blinking cursor appears for more than 10 seconds and then only the ubuntu logo is shown....

---

### Post by lavinog on 2010-05-02
> **sarin_cv said:**
> I am also having the same issue but the boot time for me is almost 20-30 seconds... I am having a 2GHz dual core processor with 3GB RAM... I had installed Lucid beta1 and updated daily and with the latest update on 1st of may, it shows LTS version.... for the beta version it was more than 40 seconds for me and after updating it was reduced to 20+... On selecting ubuntu from grub, a blank screen with a blinking cursor appears for more than 10 seconds and then only the ubuntu logo is shown....

Can you post a bootchart?
Do you have autologin enabled?

---

### Post by ankit.vader on 2010-05-02
i have lenovo y500, 3gb ram, intel 845 GM, core 2 duo processor. 
I did an upgrade
```

**dmesg**
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.32-21-generic (buildd@rothera) (gcc version 4.4.3 (Ubuntu 4.4.3-4ubuntu5) ) #32-Ubuntu SMP Fri Apr 16 08:10:02 UTC 2010 (Ubuntu 2.6.32-21.32-generic 2.6.32.11+drm33.2)
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   NSC Geode by NSC
[    0.000000]   Cyrix CyrixInstead
[    0.000000]   Centaur CentaurHauls
[    0.000000]   Transmeta GenuineTMx86
[    0.000000]   Transmeta TransmetaCPU
[    0.000000]   UMC UMC UMC UMCI did 
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
[    0.000000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000dc000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 00000000bf6e0000 (usable)
[    0.000000]  BIOS-e820: 00000000bf6e0000 - 00000000bf700000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000bf700000 - 00000000c0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed00000 - 00000000fed00400 (reserved)
[    0.000000]  BIOS-e820: 00000000fed14000 - 00000000fed1a000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed1c000 - 00000000fed90000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000ff000000 - 0000000100000000 (reserved)
[    0.000000] DMI present.
[    0.000000] last_pfn = 0xbf6e0 max_arch_pfn = 0x100000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-CFFFF write-protect
[    0.000000]   D0000-DFFFF uncachable
[    0.000000]   E0000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000 mask F80000000 write-back
[    0.000000]   1 base 080000000 mask FC0000000 write-back
[    0.000000]   2 base 0BF700000 mask FFFF00000 uncachable
[    0.000000]   3 base 0BF800000 mask FFF800000 uncachable
[    0.000000]   4 disabled
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] e820 update range: 0000000000002000 - 0000000000006000 (usable) ==> (reserved)
[    0.000000] Scanning 1 areas for low memory corruption
[    0.000000] modified physical RAM map:
[    0.000000]  modified: 0000000000000000 - 0000000000002000 (usable)
[    0.000000]  modified: 0000000000002000 - 0000000000006000 (reserved)
[    0.000000]  modified: 0000000000006000 - 000000000009f800 (usable)
[    0.000000]  modified: 000000000009f800 - 00000000000a0000 (reserved)
[    0.000000]  modified: 00000000000dc000 - 0000000000100000 (reserved)
[    0.000000]  modified: 0000000000100000 - 00000000bf6e0000 (usable)
[    0.000000]  modified: 00000000bf6e0000 - 00000000bf700000 (ACPI NVS)
[    0.000000]  modified: 00000000bf700000 - 00000000c0000000 (reserved)
[    0.000000]  modified: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  modified: 00000000fec00000 - 00000000fec10000 (reserved)
[    0.000000]  modified: 00000000fed00000 - 00000000fed00400 (reserved)
[    0.000000]  modified: 00000000fed14000 - 00000000fed1a000 (reserved)
[    0.000000]  modified: 00000000fed1c000 - 00000000fed90000 (reserved)
[    0.000000]  modified: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  modified: 00000000ff000000 - 0000000100000000 (reserved)
[    0.000000] initial memory mapped : 0 - 00c00000
[    0.000000] init_memory_mapping: 0000000000000000-00000000377fe000
[    0.000000] Using x86 segment limits to approximate NX protection
[    0.000000]  0000000000 - 0000400000 page 4k
[    0.000000]  0000400000 - 0037400000 page 2M
[    0.000000]  0037400000 - 00377fe000 page 4k
[    0.000000] kernel direct mapping tables up to 377fe000 @ 7000-c000
[    0.000000] RAMDISK: 37859000 - 37fefab5
[    0.000000] Allocated new RAMDISK: 008de000 - 01074ab5
[    0.000000] Move RAMDISK from 0000000037859000 - 0000000037fefab4 to 008de000 - 01074ab4
[    0.000000] ACPI: RSDP 000f65c0 00024 (v02 LENOVO)
[    0.000000] ACPI: XSDT bf6e59d8 00094 (v01 LENOVO CB-01    06040000  LTP 00000000)
[    0.000000] ACPI: FACP bf6ecbc4 000F4 (v03 LENOVO CB-01    06040000 ALAN 00000001)
[    0.000000] ACPI: DSDT bf6e77a5 053AB (v01 LENOVO CB-01    06040000 MSFT 0100000E)
[    0.000000] ACPI: FACS bf6edfc0 00040
[    0.000000] ACPI: APIC bf6eccb8 00068 (v01 LENOVO CB-01    06040000 LOHR 0000005A)
[    0.000000] ACPI: HPET bf6ecd20 00038 (v01 LENOVO CB-01    06040000 LOHR 0000005A)
[    0.000000] ACPI: MCFG bf6ecd58 0003C (v01 LENOVO CB-01    06040000 LOHR 0000005A)
[    0.000000] ACPI: TCPA bf6ecd94 00032 (v01 LENOVO CB-01    06040000  TL  00000000)
[    0.000000] ACPI: SLIC bf6ecdc6 00176 (v01 LENOVO CB-01    06040000 TBD  00000001)
[    0.000000] ACPI: DBGP bf6ecf3c 00034 (v01 LENOVO CB-01    06040000 LOHR 00000000)
[    0.000000] ACPI: APIC bf6ecf70 00068 (v01 LENOVO CB-01    06040000  LTP 00000000)
[    0.000000] ACPI: BOOT bf6ecfd8 00028 (v01 LENOVO CB-01    06040000  LTP 00000001)
[    0.000000] ACPI: SSDT bf6e7156 0064F (v01 SataRe  SataPri 00001000 INTL 20050624)
[    0.000000] ACPI: SSDT bf6e6ac4 00692 (v01 SataRe  SataSec 00001000 INTL 20050624)
[    0.000000] ACPI: SSDT bf6e5ff8 0025F (v01  PmRef  Cpu0Tst 00003000 INTL 20050624)
[    0.000000] ACPI: SSDT bf6e5f52 000A6 (v01  PmRef  Cpu1Tst 00003000 INTL 20050624)
[    0.000000] ACPI: SSDT bf6e5a6c 004E6 (v01  PmRef    CpuPm 00003000 INTL 20050624)
[    0.000000] ACPI: BIOS bug: multiple APIC/MADT found, using 0
[    0.000000] ACPI: If "acpi_apic_instance=2" works better, notify linux-acpi@vger.kernel.org
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] 2174MB HIGHMEM available.
[    0.000000] 887MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 377fe000
[    0.000000]   low ram: 0 - 377fe000
[    0.000000]   node 0 low ram: 00000000 - 377fe000
[    0.000000]   node 0 bootmap 00008000 - 0000ef00
[    0.000000] (9 early reservations) ==> bootmem [0000000000 - 00377fe000]
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
[    0.000000]   #1 [0000001000 - 0000002000]    EX TRAMPOLINE ==> [0000001000 - 0000002000]
[    0.000000]   #2 [0000006000 - 0000007000]       TRAMPOLINE ==> [0000006000 - 0000007000]
[    0.000000]   #3 [0000100000 - 00008d9e98]    TEXT DATA BSS ==> [0000100000 - 00008d9e98]
[    0.000000]   #4 [000009f800 - 0000100000]    BIOS reserved ==> [000009f800 - 0000100000]
[    0.000000]   #5 [00008da000 - 00008dd190]              BRK ==> [00008da000 - 00008dd190]
[    0.000000]   #6 [0000007000 - 0000008000]          PGTABLE ==> [0000007000 - 0000008000]
[    0.000000]   #7 [00008de000 - 0001074ab5]      NEW RAMDISK ==> [00008de000 - 0001074ab5]
[    0.000000]   #8 [0000008000 - 000000f000]          BOOTMAP ==> [0000008000 - 000000f000]
[    0.000000] found SMP MP-table at [c00f6640] f6640
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000000 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x000377fe
[    0.000000]   HighMem  0x000377fe -> 0x000bf6e0
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[3] active PFN ranges
[    0.000000]     0: 0x00000000 -> 0x00000002
[    0.000000]     0: 0x00000006 -> 0x0000009f
[    0.000000]     0: 0x00000100 -> 0x000bf6e0
[    0.000000] On node 0 totalpages: 783995
[    0.000000] free_area_init_node: node 0, pgdat c0798720, node_mem_map c1076000
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3963 pages, LIFO batch:0
[    0.000000]   Normal zone: 1744 pages used for memmap
[    0.000000]   Normal zone: 221486 pages, LIFO batch:31
[    0.000000]   HighMem zone: 4350 pages used for memmap
[    0.000000]   HighMem zone: 552420 pages, LIFO batch:31
[    0.000000] Using APIC driver default
[    0.000000] ACPI: PM-Timer IO Port: 0x1008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 1, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000
[    0.000000] SMP: Allowing 2 CPUs, 0 hotplug CPUs
[    0.000000] nr_irqs_gsi: 24
[    0.000000] PM: Registered nosave memory: 0000000000002000 - 0000000000006000
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000dc000
[    0.000000] PM: Registered nosave memory: 00000000000dc000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at c0000000 (gap: c0000000:20000000)
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:2 nr_node_ids:1
[    0.000000] PERCPU: Embedded 14 pages/cpu @c2c00000 s36024 r0 d21320 u2097152
[    0.000000] pcpu-alloc: s36024 r0 d21320 u2097152 alloc=1*4194304
[    0.000000] pcpu-alloc: [0] 0 1 
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 777869
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.32-21-generic root=UUID=ccf42d63-3c13-4806-80c6-4ad4a9f92d67 ro splash vga=773 quiet splash locale=fr_FR i8042.reset
[    0.000000] PID hash table entries: 4096 (order: 2, 16384 bytes)
[    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] allocated 15681920 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] Initializing HighMem for node 0 (000377fe:000bf6e0)
[    0.000000] Memory: 3078336k/3136384k available (4673k kernel code, 56660k reserved, 2122k data, 656k init, 2227080k highmem)
[    0.000000] virtual kernel memory layout:
[    0.000000]     fixmap  : 0xfff1d000 - 0xfffff000   ( 904 kB)
[    0.000000]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[    0.000000]     vmalloc : 0xf7ffe000 - 0xff7fe000   ( 120 MB)
[    0.000000]     lowmem  : 0xc0000000 - 0xf77fe000   ( 887 MB)
[    0.000000]       .init : 0xc07a3000 - 0xc0847000   ( 656 kB)
[    0.000000]       .data : 0xc0590613 - 0xc07a2e48   (2122 kB)
[    0.000000]       .text : 0xc0100000 - 0xc0590613   (4673 kB)
[    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.000000] SLUB: Genslabs=13, HWalign=64, Order=0-3, MinObjects=0, CPUs=2, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000] NR_IRQS:2304 nr_irqs:424
[    0.000000] Extended CMOS year: 2000
[    0.000000] Console: colour dummy device 80x25
[    0.000000] console [tty0] enabled
[    0.000000] hpet clockevent registered
[    0.000000] HPET: 3 timers in total, 0 timers will be used for per-cpu timer
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 1728.903 MHz processor.
[    0.004008] Calibrating delay loop (skipped), value calculated using timer frequency.. 3457.80 BogoMIPS (lpj=6915612)
[    0.004046] Security Framework initialized
[    0.004086] AppArmor: AppArmor initialized
[    0.004101] Mount-cache hash table entries: 512
[    0.004366] Initializing cgroup subsys ns
[    0.004375] Initializing cgroup subsys cpuacct
[    0.004386] Initializing cgroup subsys memory
[    0.004402] Initializing cgroup subsys devices
[    0.004408] Initializing cgroup subsys freezer
[    0.004413] Initializing cgroup subsys net_cls
[    0.004455] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.004462] CPU: L2 cache: 2048K
[    0.004470] CPU: Physical Processor ID: 0
[    0.004474] CPU: Processor Core ID: 0
[    0.004484] mce: CPU supports 6 MCE banks
[    0.004501] CPU0: Thermal monitoring handled by SMI
[    0.004509] using mwait in idle threads.
[    0.004522] Performance Events: Core2 events, Intel PMU driver.
[    0.004543] ... version:                2
[    0.004548] ... bit width:              40
[    0.004552] ... generic registers:      2
[    0.004557] ... value mask:             000000ffffffffff
[    0.004562] ... max period:             000000007fffffff
[    0.004567] ... fixed-purpose events:   3
[    0.004572] ... event mask:             0000000700000003
[    0.004580] Checking 'hlt' instruction... OK.
[    0.026431] ACPI: Core revision 20090903
[    0.044019] ftrace: converting mcount calls to 0f 1f 44 00 00
[    0.044036] ftrace: allocating 21771 entries in 43 pages
[    0.048102] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.048532] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.090886] CPU0: Intel(R) Core(TM)2 CPU         T5300  @ 1.73GHz stepping 02
[    0.092001] Booting processor 1 APIC 0x1 ip 0x6000
[    0.008000] Initializing CPU#1
[    0.008000] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.008000] CPU: L2 cache: 2048K
[    0.008000] CPU: Physical Processor ID: 0
[    0.008000] CPU: Processor Core ID: 1
[    0.008000] CPU1: Thermal monitoring handled by SMI
[    0.176109] CPU1: Intel(R) Core(TM)2 CPU         T5300  @ 1.73GHz stepping 02
[    0.176136] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
[    0.180033] Brought up 2 CPUs
[    0.180040] Total of 2 processors activated (6915.86 BogoMIPS).
[    0.181009] CPU0 attaching sched-domain:
[    0.181016]  domain 0: span 0-1 level MC
[    0.181023]   groups: 0 1
[    0.181037] CPU1 attaching sched-domain:
[    0.181043]  domain 0: span 0-1 level MC
[    0.181049]   groups: 1 0
[    0.181246] devtmpfs: initialized
[    0.181246] regulator: core version 0.5
[    0.181246] Time:  6:06:10  Date: 05/02/10
[    0.181246] NET: Registered protocol family 16
[    0.181246] Trying to unpack rootfs image as initramfs...
[    0.181246] EISA bus registered
[    0.181246] ACPI: bus type pci registered
[    0.181246] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 255
[    0.181246] PCI: MCFG area at e0000000 reserved in E820
[    0.181246] PCI: Using MMCONFIG for extended config space
[    0.181246] PCI: Using configuration type 1 for base access
[    0.196313] bio: create slab <bio-0> at 0
[    0.198504] ACPI: EC: Look up EC in DSDT
[    0.205254] ACPI: BIOS _OSI(Linux) query ignored
[    0.248196] ACPI: Interpreter enabled
[    0.248215] ACPI: (supports S0 S3 S4 S5)
[    0.248272] ACPI: Using IOAPIC for interrupt routing
[    0.301961] ACPI: EC: GPE = 0x19, I/O: command/status = 0x66, data = 0x62
[    0.302863] ACPI: No dock devices found.
[    0.303955] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.304180] pci 0000:00:02.0: reg 10 32bit mmio: [0xd4200000-0xd427ffff]
[    0.304194] pci 0000:00:02.0: reg 14 io port: [0x1800-0x1807]
[    0.304206] pci 0000:00:02.0: reg 18 32bit mmio pref: [0xc0000000-0xcfffffff]
[    0.304219] pci 0000:00:02.0: reg 1c 32bit mmio: [0xd4300000-0xd433ffff]
[    0.304317] pci 0000:00:02.1: reg 10 32bit mmio: [0xd4280000-0xd42fffff]
[    0.304531] pci 0000:00:1b.0: reg 10 64bit mmio: [0xd4340000-0xd4343fff]
[    0.304632] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    0.304643] pci 0000:00:1b.0: PME# disabled
[    0.304797] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    0.304806] pci 0000:00:1c.0: PME# disabled
[    0.304965] pci 0000:00:1c.1: PME# supported from D0 D3hot D3cold
[    0.304974] pci 0000:00:1c.1: PME# disabled
[    0.305131] pci 0000:00:1c.2: PME# supported from D0 D3hot D3cold
[    0.305141] pci 0000:00:1c.2: PME# disabled
[    0.305253] pci 0000:00:1d.0: reg 20 io port: [0x1820-0x183f]
[    0.305360] pci 0000:00:1d.1: reg 20 io port: [0x1840-0x185f]
[    0.305467] pci 0000:00:1d.2: reg 20 io port: [0x1860-0x187f]
[    0.305573] pci 0000:00:1d.3: reg 20 io port: [0x1880-0x189f]
[    0.305688] pci 0000:00:1d.7: reg 10 32bit mmio: [0xd4544000-0xd45443ff]
[    0.305791] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
[    0.305802] pci 0000:00:1d.7: PME# disabled
[    0.306078] pci 0000:00:1f.0: quirk: region 1000-107f claimed by ICH6 ACPI/GPIO/TCO
[    0.306089] pci 0000:00:1f.0: quirk: region 1180-11bf claimed by ICH6 GPIO
[    0.306098] pci 0000:00:1f.0: ICH7 LPC Generic IO decode 1 PIO at 1670 (mask 0003)
[    0.306107] pci 0000:00:1f.0: ICH7 LPC Generic IO decode 2 PIO at ff2c (mask 007f)
[    0.306220] pci 0000:00:1f.2: reg 10 io port: [0x00-0x07]
[    0.306235] pci 0000:00:1f.2: reg 14 io port: [0x00-0x03]
[    0.306250] pci 0000:00:1f.2: reg 18 io port: [0x00-0x07]
[    0.306265] pci 0000:00:1f.2: reg 1c io port: [0x00-0x03]
[    0.306280] pci 0000:00:1f.2: reg 20 io port: [0x18b0-0x18bf]
[    0.306341] pci 0000:00:1f.2: PME# supported from D3hot
[    0.306350] pci 0000:00:1f.2: PME# disabled
[    0.306446] pci 0000:00:1f.3: reg 20 io port: [0x18c0-0x18df]
[    0.306601] pci 0000:00:1c.0: bridge io port: [0x2000-0x2fff]
[    0.306612] pci 0000:00:1c.0: bridge 32bit mmio: [0xd2000000-0xd3ffffff]
[    0.306628] pci 0000:00:1c.0: bridge 64bit mmio pref: [0xd0000000-0xd1ffffff]
[    0.306847] pci 0000:03:00.0: reg 10 32bit mmio: [0xd4000000-0xd4000fff]
[    0.307134] pci 0000:03:00.0: PME# supported from D0 D3hot D3cold
[    0.307152] pci 0000:03:00.0: PME# disabled
[    0.307317] pci 0000:00:1c.1: bridge 32bit mmio: [0xd4000000-0xd40fffff]
[    0.307517] pci 0000:05:01.0: reg 10 io port: [0x3000-0x30ff]
[    0.307534] pci 0000:05:01.0: reg 14 32bit mmio: [0xd4100000-0xd41000ff]
[    0.307628] pci 0000:05:01.0: supports D1 D2
[    0.307634] pci 0000:05:01.0: PME# supported from D1 D2 D3hot D3cold
[    0.307644] pci 0000:05:01.0: PME# disabled
[    0.307726] pci 0000:05:04.0: reg 10 32bit mmio: [0x000000-0x000fff]
[    0.307770] pci 0000:05:04.0: supports D1 D2
[    0.307776] pci 0000:05:04.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.307787] pci 0000:05:04.0: PME# disabled
[    0.307862] pci 0000:05:06.0: reg 10 32bit mmio: [0xd4100800-0xd4100fff]
[    0.307959] pci 0000:05:06.0: supports D1 D2
[    0.307965] pci 0000:05:06.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.307975] pci 0000:05:06.0: PME# disabled
[    0.308056] pci 0000:05:06.1: reg 10 32bit mmio: [0xd4100400-0xd41004ff]
[    0.308152] pci 0000:05:06.1: supports D1 D2
[    0.308157] pci 0000:05:06.1: PME# supported from D0 D1 D2 D3hot D3cold
[    0.308167] pci 0000:05:06.1: PME# disabled
[    0.308237] pci 0000:05:06.2: reg 10 32bit mmio: [0xd4101000-0xd41010ff]
[    0.308333] pci 0000:05:06.2: supports D1 D2
[    0.308339] pci 0000:05:06.2: PME# supported from D0 D1 D2 D3hot D3cold
[    0.308348] pci 0000:05:06.2: PME# disabled
[    0.308419] pci 0000:05:06.3: reg 10 32bit mmio: [0xd4101400-0xd41014ff]
[    0.308514] pci 0000:05:06.3: supports D1 D2
[    0.308520] pci 0000:05:06.3: PME# supported from D0 D1 D2 D3hot D3cold
[    0.308530] pci 0000:05:06.3: PME# disabled
[    0.308603] pci 0000:05:06.4: reg 10 32bit mmio: [0xd4101800-0xd41018ff]
[    0.308699] pci 0000:05:06.4: supports D1 D2
[    0.308705] pci 0000:05:06.4: PME# supported from D0 D1 D2 D3hot D3cold
[    0.308715] pci 0000:05:06.4: PME# disabled
[    0.308809] pci 0000:00:1e.0: transparent bridge
[    0.308819] pci 0000:00:1e.0: bridge io port: [0x3000-0x3fff]
[    0.308830] pci 0000:00:1e.0: bridge 32bit mmio: [0xd4100000-0xd41fffff]
[    0.308921] pci_bus 0000:00: on NUMA node 0
[    0.308933] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.309388] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP01._PRT]
[    0.309567] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP02._PRT]
[    0.309744] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP03._PRT]
[    0.309964] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCIB._PRT]
[    0.325911] ACPI: PCI Interrupt Link [LNKA] (IRQs 1 3 4 5 6 7 *10 12 14 15)
[    0.326149] ACPI: PCI Interrupt Link [LNKB] (IRQs 1 3 4 5 6 7 11 12 14 15) *10
[    0.326383] ACPI: PCI Interrupt Link [LNKC] (IRQs 1 3 4 5 6 7 10 12 14 15) *11
[    0.326615] ACPI: PCI Interrupt Link [LNKD] (IRQs 1 3 4 5 6 7 11 12 14 15) *10
[    0.326846] ACPI: PCI Interrupt Link [LNKE] (IRQs 1 3 4 5 6 7 10 12 14 15) *0, disabled.
[    0.327088] ACPI: PCI Interrupt Link [LNKF] (IRQs 1 3 4 5 6 7 *11 12 14 15)
[    0.327316] ACPI: PCI Interrupt Link [LNKG] (IRQs 1 3 4 5 6 7 10 12 14 15) *11
[    0.327546] ACPI: PCI Interrupt Link [LNKH] (IRQs 1 3 4 *5 6 7 11 12 14 15)
[    0.327814] vgaarb: device added: PCI:0000:00:02.0,decodes=io+mem,owns=io+mem,locks=none
[    0.327858] vgaarb: loaded
[    0.328167] SCSI subsystem initialized
[    0.328355] libata version 3.00 loaded.
[    0.328531] usbcore: registered new interface driver usbfs
[    0.328567] usbcore: registered new interface driver hub
[    0.328633] usbcore: registered new device driver usb
[    0.328998] ACPI: WMI: Mapper loaded
[    0.329003] PCI: Using ACPI for IRQ routing
[    0.329504] NetLabel: Initializing
[    0.329508] NetLabel:  domain hash size = 128
[    0.329513] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.329542] NetLabel:  unlabeled traffic allowed by default
[    0.329618] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[    0.329632] hpet0: 3 comparators, 64-bit 14.318180 MHz counter
[    0.332298] Switching to clocksource tsc
[    0.337256] AppArmor: AppArmor Filesystem Enabled
[    0.337282] pnp: PnP ACPI init
[    0.337308] ACPI: bus type pnp registered
[    0.359082] pnp: PnP ACPI: found 11 devices
[    0.359088] ACPI: ACPI bus type pnp unregistered
[    0.359097] PnPBIOS: Disabled by ACPI PNP
[    0.359124] system 00:01: iomem range 0xe0000000-0xefffffff has been reserved
[    0.359133] system 00:01: iomem range 0xfed14000-0xfed17fff has been reserved
[    0.359141] system 00:01: iomem range 0xfed18000-0xfed18fff has been reserved
[    0.359149] system 00:01: iomem range 0xfed19000-0xfed19fff has been reserved
[    0.359156] system 00:01: iomem range 0xfed1c000-0xfed1ffff has been reserved
[    0.359164] system 00:01: iomem range 0xfed20000-0xfed3ffff has been reserved
[    0.359172] system 00:01: iomem range 0xfed40000-0xfed44fff has been reserved
[    0.359180] system 00:01: iomem range 0xfed45000-0xfed8ffff has been reserved
[    0.359201] system 00:06: ioport range 0x680-0x69f has been reserved
[    0.359208] system 00:06: ioport range 0x800-0x80f has been reserved
[    0.359216] system 00:06: ioport range 0x1000-0x107f has been reserved
[    0.359224] system 00:06: ioport range 0x1180-0x11bf has been reserved
[    0.359231] system 00:06: ioport range 0x1640-0x164f has been reserved
[    0.359239] system 00:06: ioport range 0xff00-0xff7f has been reserved
[    0.359254] system 00:07: ioport range 0x6a0-0x6af has been reserved
[    0.359261] system 00:07: ioport range 0x6b0-0x6ff has been reserved
[    0.394336] pci 0000:00:1c.0: PCI bridge, secondary bus 0000:02
[    0.394346] pci 0000:00:1c.0:   IO window: 0x2000-0x2fff
[    0.394360] pci 0000:00:1c.0:   MEM window: 0xd2000000-0xd3ffffff
[    0.394371] pci 0000:00:1c.0:   PREFETCH window: 0x000000d0000000-0x000000d1ffffff
[    0.394386] pci 0000:00:1c.1: PCI bridge, secondary bus 0000:03
[    0.394395] pci 0000:00:1c.1:   IO window: 0x4000-0x4fff
[    0.394407] pci 0000:00:1c.1:   MEM window: 0xd4000000-0xd40fffff
[    0.394418] pci 0000:00:1c.1:   PREFETCH window: 0x000000d4600000-0x000000d47fffff
[    0.394433] pci 0000:00:1c.2: PCI bridge, secondary bus 0000:04
[    0.394441] pci 0000:00:1c.2:   IO window: 0x5000-0x5fff
[    0.394454] pci 0000:00:1c.2:   MEM window: 0xd4800000-0xd49fffff
[    0.394465] pci 0000:00:1c.2:   PREFETCH window: 0x000000d4a00000-0x000000d4bfffff
[    0.394494] pci 0000:05:04.0: CardBus bridge, secondary bus 0000:06
[    0.394500] pci 0000:05:04.0:   IO window: 0x003400-0x0034ff
[    0.394511] pci 0000:05:04.0:   IO window: 0x003800-0x0038ff
[    0.394522] pci 0000:05:04.0:   PREFETCH window: 0xd8000000-0xdbffffff
[    0.394534] pci 0000:05:04.0:   MEM window: 0xdc000000-0xdfffffff
[    0.394545] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:05
[    0.394553] pci 0000:00:1e.0:   IO window: 0x3000-0x3fff
[    0.394566] pci 0000:00:1e.0:   MEM window: 0xd4100000-0xd41fffff
[    0.394576] pci 0000:00:1e.0:   PREFETCH window: 0xd8000000-0xdbffffff
[    0.394613]   alloc irq_desc for 19 on node -1
[    0.394618]   alloc kstat_irqs on node -1
[    0.394633] pci 0000:00:1c.0: PCI INT D -> GSI 19 (level, low) -> IRQ 19
[    0.394645] pci 0000:00:1c.0: setting latency timer to 64
[    0.394677]   alloc irq_desc for 16 on node -1
[    0.394681]   alloc kstat_irqs on node -1
[    0.394691] pci 0000:00:1c.1: PCI INT B -> GSI 16 (level, low) -> IRQ 16
[    0.394702] pci 0000:00:1c.1: setting latency timer to 64
[    0.394722]   alloc irq_desc for 18 on node -1
[    0.394727]   alloc kstat_irqs on node -1
[    0.394736] pci 0000:00:1c.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.394747] pci 0000:00:1c.2: setting latency timer to 64
[    0.394760] pci 0000:00:1e.0: enabling device (0004 -> 0007)
[    0.394773] pci 0000:00:1e.0: setting latency timer to 64
[    0.394795] pci 0000:05:04.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.394809] pci_bus 0000:00: resource 0 io:  [0x00-0xffff]
[    0.394817] pci_bus 0000:00: resource 1 mem: [0x000000-0xffffffff]
[    0.394824] pci_bus 0000:02: resource 0 io:  [0x2000-0x2fff]
[    0.394831] pci_bus 0000:02: resource 1 mem: [0xd2000000-0xd3ffffff]
[    0.394838] pci_bus 0000:02: resource 2 pref mem [0xd0000000-0xd1ffffff]
[    0.394845] pci_bus 0000:03: resource 0 io:  [0x4000-0x4fff]
[    0.394852] pci_bus 0000:03: resource 1 mem: [0xd4000000-0xd40fffff]
[    0.394858] pci_bus 0000:03: resource 2 pref mem [0xd4600000-0xd47fffff]
[    0.394865] pci_bus 0000:04: resource 0 io:  [0x5000-0x5fff]
[    0.394872] pci_bus 0000:04: resource 1 mem: [0xd4800000-0xd49fffff]
[    0.394878] pci_bus 0000:04: resource 2 pref mem [0xd4a00000-0xd4bfffff]
[    0.394885] pci_bus 0000:05: resource 0 io:  [0x3000-0x3fff]
[    0.394891] pci_bus 0000:05: resource 1 mem: [0xd4100000-0xd41fffff]
[    0.394898] pci_bus 0000:05: resource 2 pref mem [0xd8000000-0xdbffffff]
[    0.394904] pci_bus 0000:05: resource 3 io:  [0x00-0xffff]
[    0.394911] pci_bus 0000:05: resource 4 mem: [0x000000-0xffffffff]
[    0.394918] pci_bus 0000:06: resource 0 io:  [0x3400-0x34ff]
[    0.394924] pci_bus 0000:06: resource 1 io:  [0x3800-0x38ff]
[    0.394931] pci_bus 0000:06: resource 2 pref mem [0xd8000000-0xdbffffff]
[    0.394938] pci_bus 0000:06: resource 3 mem: [0xdc000000-0xdfffffff]
[    0.395024] NET: Registered protocol family 2
[    0.395258] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.396029] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.396933] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.397350] TCP: Hash tables configured (established 131072 bind 65536)
[    0.397356] TCP reno registered
[    0.397533] NET: Registered protocol family 1
[    0.397577] pci 0000:00:02.0: Boot video device
[    0.397814] Simple Boot Flag at 0x36 set to 0x1
[    0.398235] cpufreq-nforce2: No nForce2 chipset.
[    0.398310] Scanning for low memory corruption every 60 seconds
[    0.398571] audit: initializing netlink socket (disabled)
[    0.398597] type=2000 audit(1272780370.394:1): initialized
[    0.423689] highmem bounce pool size: 64 pages
[    0.423701] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    0.427645] VFS: Disk quotas dquot_6.5.2
[    0.427798] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.429246] fuse init (API version 7.13)
[    0.429461] msgmni has been set to 1664
[    0.429958] alg: No test for stdrng (krng)
[    0.430088] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.430095] io scheduler noop registered
[    0.430100] io scheduler anticipatory registered
[    0.430105] io scheduler deadline registered
[    0.430205] io scheduler cfq registered (default)
[    0.430562]   alloc irq_desc for 24 on node -1
[    0.430568]   alloc kstat_irqs on node -1
[    0.430589] pcieport 0000:00:1c.0: irq 24 for MSI/MSI-X
[    0.430610] pcieport 0000:00:1c.0: setting latency timer to 64
[    0.430909]   alloc irq_desc for 25 on node -1
[    0.430914]   alloc kstat_irqs on node -1
[    0.430931] pcieport 0000:00:1c.1: irq 25 for MSI/MSI-X
[    0.430950] pcieport 0000:00:1c.1: setting latency timer to 64
[    0.431226]   alloc irq_desc for 26 on node -1
[    0.431230]   alloc kstat_irqs on node -1
[    0.431247] pcieport 0000:00:1c.2: irq 26 for MSI/MSI-X
[    0.431266] pcieport 0000:00:1c.2: setting latency timer to 64
[    0.431483] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.431738] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.433481] ACPI: AC Adapter [ACAD] (off-line)
[    0.433676] input: Lid Switch as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0D:00/input/input0
[    0.433762] ACPI: Lid Switch [LID0]
[    0.433871] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input1
[    0.433879] ACPI: Power Button [PWRB]
[    0.433990] input: Sleep Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0E:00/input/input2
[    0.433997] ACPI: Sleep Button [SLPB]
[    0.434135] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input3
[    0.434141] ACPI: Power Button [PWRF]
[    0.435617] ACPI: SSDT bf6e67c4 00238 (v01  PmRef  Cpu0Ist 00003000 INTL 20050624)
[    0.436720] ACPI: SSDT bf6e6257 004E8 (v01  PmRef  Cpu0Cst 00003001 INTL 20050624)
[    0.441976] Monitor-Mwait will be used to enter C-1 state
[    0.442049] Monitor-Mwait will be used to enter C-2 state
[    0.442118] Monitor-Mwait will be used to enter C-3 state
[    0.442134] Marking TSC unstable due to TSC halts in idle
[    0.442262] processor LNXCPU:00: registered as cooling_device0
[    0.443091] ACPI: SSDT bf6e69fc 000C8 (v01  PmRef  Cpu1Ist 00003000 INTL 20050624)
[    0.443888] ACPI: SSDT bf6e673f 00085 (v01  PmRef  Cpu1Cst 00003000 INTL 20050624)
[    0.445080] Switching to clocksource hpet
[    0.453778] processor LNXCPU:01: registered as cooling_device1
[    0.487587] thermal LNXTHERM:01: registered as thermal_zone0
[    0.487610] ACPI: Thermal Zone [TZ00] (46 C)
[    0.491465] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    0.494870] brd: module loaded
[    0.496085] loop: module loaded
[    0.496281] input: Macintosh mouse button emulation as /devices/virtual/input/input4
[    0.496496] ata_piix 0000:00:1f.2: version 2.13
[    0.496529] ata_piix 0000:00:1f.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    0.496541] ata_piix 0000:00:1f.2: MAP [ P0 P2 IDE IDE ]
[    0.496862] isapnp: Scanning for PnP cards...
[    0.664585] Freeing initrd memory: 7770k freed
[    0.677449] ata_piix 0000:00:1f.2: setting latency timer to 64
[    0.681091] scsi0 : ata_piix
[    0.681435] scsi1 : ata_piix
[    0.683632] ata1: SATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0x18b0 irq 14
[    0.683641] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x18b8 irq 15
[    0.684685] Fixed MDIO Bus: probed
[    0.684773] PPP generic driver version 2.4.2
[    0.684904] tun: Universal TUN/TAP device driver, 1.6
[    0.684909] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.685154] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.685205]   alloc irq_desc for 23 on node -1
[    0.685211]   alloc kstat_irqs on node -1
[    0.685224] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    0.685262] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    0.685270] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    0.685347] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 1
[    0.685386] ehci_hcd 0000:00:1d.7: using broken periodic workaround
[    0.685408] ehci_hcd 0000:00:1d.7: debug port 1
[    0.689301] ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported
[    0.689338] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xd4544000
[    0.702294] ACPI: Battery Slot [BAT1] (battery present)
[    0.705034] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    0.705246] usb usb1: configuration #1 chosen from 1 choice
[    0.705317] hub 1-0:1.0: USB hub found
[    0.705334] hub 1-0:1.0: 8 ports detected
[    0.705481] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.705521] uhci_hcd: USB Universal Host Controller Interface driver
[    0.705578] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    0.705592] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    0.705600] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    0.705678] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    0.705720] uhci_hcd 0000:00:1d.0: irq 23, io base 0x00001820
[    0.705930] usb usb2: configuration #1 chosen from 1 choice
[    0.705996] hub 2-0:1.0: USB hub found
[    0.706012] hub 2-0:1.0: 2 ports detected
[    0.706120] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    0.706133] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    0.706141] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    0.706222] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 3
[    0.706277] uhci_hcd 0000:00:1d.1: irq 19, io base 0x00001840
[    0.706487] usb usb3: configuration #1 chosen from 1 choice
[    0.706552] hub 3-0:1.0: USB hub found
[    0.706567] hub 3-0:1.0: 2 ports detected
[    0.706674] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.706687] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    0.706694] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    0.706769] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 4
[    0.706824] uhci_hcd 0000:00:1d.2: irq 18, io base 0x00001860
[    0.707036] usb usb4: configuration #1 chosen from 1 choice
[    0.707101] hub 4-0:1.0: USB hub found
[    0.707119] hub 4-0:1.0: 2 ports detected
[    0.707225] uhci_hcd 0000:00:1d.3: PCI INT D -> GSI 16 (level, low) -> IRQ 16
[    0.707239] uhci_hcd 0000:00:1d.3: setting latency timer to 64
[    0.707246] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[    0.707331] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 5
[    0.707385] uhci_hcd 0000:00:1d.3: irq 16, io base 0x00001880
[    0.707589] usb usb5: configuration #1 chosen from 1 choice
[    0.707660] hub 5-0:1.0: USB hub found
[    0.707676] hub 5-0:1.0: 2 ports detected
[    0.707908] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    0.724148] i8042.c: Detected active multiplexing controller, rev 1.1.
[    0.742104] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.742128] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[    0.742136] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[    0.742144] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[    0.742151] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[    0.742343] mice: PS/2 mouse device common for all mice
[    0.742664] rtc_cmos 00:08: RTC can wake from S4
[    0.742756] rtc_cmos 00:08: rtc core: registered rtc_cmos as rtc0
[    0.742802] rtc0: alarms up to one month, y3k, 242 bytes nvram, hpet irqs
[    0.743044] device-mapper: uevent: version 1.0.3
[    0.743265] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: dm-devel@redhat.com
[    0.743412] device-mapper: multipath: version 1.1.0 loaded
[    0.743419] device-mapper: multipath round-robin: version 1.0.0 loaded
[    0.743679] EISA: Probing bus 0 at eisa.0
[    0.743691] Cannot allocate resource for EISA slot 1
[    0.743697] Cannot allocate resource for EISA slot 2
[    0.743703] Cannot allocate resource for EISA slot 3
[    0.743708] Cannot allocate resource for EISA slot 4
[    0.743713] Cannot allocate resource for EISA slot 5
[    0.743737] EISA: Detected 0 cards.
[    0.744081] cpuidle: using governor ladder
[    0.744388] cpuidle: using governor menu
[    0.745531] TCP cubic registered
[    0.745930] NET: Registered protocol family 10
[    0.747106] lo: Disabled Privacy Extensions
[    0.747983] NET: Registered protocol family 17
[    0.749262] Using IPI No-Shortcut mode
[    0.749351] PM: Resume from disk failed.
[    0.749367] registered taskstats version 1
[    0.749979]   Magic number: 10:839:113
[    0.750079] rtc_cmos 00:08: setting system clock to 2010-05-02 06:06:11 UTC (1272780371)
[    0.750082] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.750084] EDD information not available.
[    0.763262] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input5
[    0.848575] ata1.00: ATA-7: Hitachi HTS541616J9SA00, SB4OC70P, max UDMA/100
[    0.848579] ata1.00: 312581808 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    0.852417] isapnp: No Plug & Play device found
[    0.856670] ata2.00: ATAPI: MATSHITADVD-RAM UJ-85JS, FYX4, max UDMA/66
[    0.856705] ata2.00: limited to UDMA/33 due to 40-wire cable
[    0.864901] ata1.00: configured for UDMA/100
[    0.865188] scsi 0:0:0:0: Direct-Access     ATA      Hitachi HTS54161 SB4O PQ: 0 ANSI: 5
[    0.865412] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    0.865498] sd 0:0:0:0: [sda] 312581808 512-byte logical blocks: (160 GB/149 GiB)
[    0.865555] sd 0:0:0:0: [sda] Write Protect is off
[    0.865558] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    0.865588] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    0.865750]  sda:
[    0.873530] ata2.00: configured for UDMA/33
[    0.876261] scsi 1:0:0:0: CD-ROM            MATSHITA DVD-RAM UJ-85JS  FYX4 PQ: 0 ANSI: 5
[    0.880786] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda caddy
[    0.880793] Uniform CD-ROM driver Revision: 3.20
[    0.880983] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    0.881062] sr 1:0:0:0: Attached scsi generic sg1 type 5
[    0.884157]  sda1 sda2 < sda5 > sda4
[    0.916171] sd 0:0:0:0: [sda] Attached SCSI disk
[    0.916187] Freeing unused kernel memory: 656k freed
[    0.916674] Write protecting the kernel text: 4676k
[    0.916734] Write protecting the kernel read-only data: 1840k
[    0.936450] udev: starting version 151
[    1.020072] usb 1-4: new high speed USB device using ehci_hcd and address 2
[    1.085302] 8139cp: 10/100 PCI Ethernet driver v1.3 (Mar 22, 2004)
[    1.085332] 8139cp 0000:05:01.0: This (id 10ec:8139 rev 10) is not an 8139C+ compatible chip, use 8139too
[    1.092283] 8139too Fast Ethernet driver 0.9.28
[    1.092342]   alloc irq_desc for 21 on node -1
[    1.092345]   alloc kstat_irqs on node -1
[    1.092353] 8139too 0000:05:01.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[    1.092367] 8139too 0000:05:01.0: setting latency timer to 64
[    1.093906] eth0: RealTek RTL8139 at 0x3000, 00:1b:38:03:f8:3f, IRQ 21
[    1.103955] ohci1394 0000:05:06.0: enabling device (0000 -> 0002)
[    1.103966]   alloc irq_desc for 22 on node -1
[    1.103968]   alloc kstat_irqs on node -1
[    1.103976] ohci1394 0000:05:06.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[    1.103985] ohci1394 0000:05:06.0: setting latency timer to 64
[    1.162131] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[22]  MMIO=[d4100800-d4100fff]  Max Packet=[2048]  IR/IT contexts=[4/4]
[    1.366323] EXT4-fs (sda1): mounted filesystem with ordered data mode
[    1.538109] usb 1-4: configuration #1 chosen from 1 choice
[    1.664065] usb 1-6: new high speed USB device using ehci_hcd and address 3
[    1.805447] usb 1-6: configuration #1 chosen from 1 choice
[    2.436313] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[00023f78a640180b]
[   16.692895] Adding 6385796k swap on /dev/sda5.  Priority:-1 extents:1 across:6385796k 
[   17.036750] udev: starting version 151
[   17.809955] lp: driver loaded but no devices found
[   17.961514] Linux agpgart interface v0.103
[   17.969778] intel_rng: FWH not detected
[   18.045209] ricoh-mmc: Ricoh MMC Controller disabling driver
[   18.045212] ricoh-mmc: Copyright(c) Philip Langdale
[   18.045243] ricoh-mmc: Ricoh MMC controller found at 0000:05:06.2 [1180:0843] (rev 1)
[   18.045263] ricoh-mmc: Controller is now disabled.
[   18.058692] Linux video capture interface: v2.00
[   18.069051] uvcvideo: Found UVC 1.00 device USB 2.0 Camera (04f2:b008)
[   18.072887] input: USB 2.0 Camera as /devices/pci0000:00/0000:00:1d.7/usb1/1-6/1-6:1.0/input/input6
[   18.072990] usbcore: registered new interface driver uvcvideo
[   18.073052] USB Video Class driver (v0.1.0)
[   18.084090] sdhci: Secure Digital Host Controller Interface driver
[   18.084094] sdhci: Copyright(c) Pierre Ossman
[   18.105753] sdhci-pci 0000:05:06.1: SDHCI controller found [1180:0822] (rev 19)
[   18.105772] sdhci-pci 0000:05:06.1: enabling device (0000 -> 0002)
[   18.105783] sdhci-pci 0000:05:06.1: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[   18.106808] sdhci-pci 0000:05:06.1: Will use DMA mode even though HW doesn't fully claim to support it.
[   18.106818] sdhci-pci 0000:05:06.1: setting latency timer to 64
[   18.107855] Registered led device: mmc0::
[   18.108908] mmc0: SDHCI controller on PCI [0000:05:06.1] using DMA
[   18.112915] agpgart-intel 0000:00:00.0: Intel 945GM Chipset
[   18.113574] agpgart-intel 0000:00:00.0: detected 7932K stolen memory
[   18.118054] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0xc0000000
[   18.138281] yenta_cardbus 0000:05:04.0: CardBus bridge found [17aa:3828]
[   18.138310] yenta_cardbus 0000:05:04.0: Using CSCINT to route CSC interrupts to PCI
[   18.138313] yenta_cardbus 0000:05:04.0: Routing CardBus interrupts to PCI
[   18.138320] yenta_cardbus 0000:05:04.0: TI: mfunc 0x01111c12, devctl 0x44
[   18.198580] acpi device:04: registered as cooling_device2
[   18.198748] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/LNXVIDEO:01/input/input7
[   18.198810] ACPI: Video Device [GFX0] (multi-head: yes  rom: no  post: no)
[   18.272239] cfg80211: Calling CRDA to update world regulatory domain
[   18.340809] cfg80211: World regulatory domain updated:
[   18.340813]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   18.340817]     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   18.340820]     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   18.340823]     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   18.340826]     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   18.340829]     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   18.369817] yenta_cardbus 0000:05:04.0: ISA IRQ mask 0x0cf8, PCI irq 16
[   18.369823] yenta_cardbus 0000:05:04.0: Socket status: 30000006
[   18.369828] pci_bus 0000:05: Raising subordinate bus# of parent bus (#05) from #05 to #09
[   18.369838] yenta_cardbus 0000:05:04.0: pcmcia: parent PCI bridge I/O window: 0x3000 - 0x3fff
[   18.369843] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x3000-0x3fff: clean.
[   18.370106] yenta_cardbus 0000:05:04.0: pcmcia: parent PCI bridge Memory window: 0xd4100000 - 0xd41fffff
[   18.370110] yenta_cardbus 0000:05:04.0: pcmcia: parent PCI bridge Memory window: 0xd8000000 - 0xdbffffff
[   18.387436] [drm] Initialized drm 1.1.0 20060810
[   18.509273] input: PS/2 Mouse as /devices/platform/i8042/serio4/input/input8
[   18.535664] input: AlpsPS/2 ALPS GlidePoint as /devices/platform/i8042/serio4/input/input9
[   18.661463] type=1505 audit(1272780389.409:2):  operation="profile_load" pid=654 name="/sbin/dhclient3"
[   18.662247] type=1505 audit(1272780389.409:3):  operation="profile_load" pid=654 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[   18.662666] type=1505 audit(1272780389.409:4):  operation="profile_load" pid=654 name="/usr/lib/connman/scripts/dhclient-script"
[   18.821723] i915 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   18.821730] i915 0000:00:02.0: setting latency timer to 64
[   18.826390] [drm] set up 7M of stolen space
[   18.884639] type=1505 audit(1272780389.633:5):  operation="profile_load" pid=776 name="/usr/share/gdm/guest-session/Xsession"
[   18.886847] type=1505 audit(1272780389.633:6):  operation="profile_replace" pid=777 name="/sbin/dhclient3"
[   18.887650] type=1505 audit(1272780389.633:7):  operation="profile_replace" pid=777 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[   18.888076] type=1505 audit(1272780389.637:8):  operation="profile_replace" pid=777 name="/usr/lib/connman/scripts/dhclient-script"
[   18.895531] type=1505 audit(1272780389.641:9):  operation="profile_load" pid=778 name="/usr/bin/evince"
[   18.905733] type=1505 audit(1272780389.653:10):  operation="profile_load" pid=778 name="/usr/bin/evince-previewer"
[   18.912198] type=1505 audit(1272780389.661:11):  operation="profile_load" pid=778 name="/usr/bin/evince-thumbnailer"
[   18.929307] [drm] initialized overlay support
[   19.387550] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, 1.2.26ks
[   19.387555] iwl3945: Copyright(c) 2003-2009 Intel Corporation
[   19.387848]   alloc irq_desc for 17 on node -1
[   19.387851]   alloc kstat_irqs on node -1
[   19.387861] iwl3945 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   19.387876] iwl3945 0000:03:00.0: setting latency timer to 64
[   19.444292] iwl3945 0000:03:00.0: Tunable channels: 11 802.11bg, 13 802.11a channels
[   19.444296] iwl3945 0000:03:00.0: Detected Intel Wireless WiFi Link 3945ABG
[   19.444419]   alloc irq_desc for 27 on node -1
[   19.444422]   alloc kstat_irqs on node -1
[   19.444458] iwl3945 0000:03:00.0: irq 27 for MSI/MSI-X
[   19.472276] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x100-0x3af: clean.
[   19.474299] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x3e0-0x4ff: excluding 0x4d0-0x4d7
[   19.475151] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x820-0x8ff: clean.
[   19.475862] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xc00-0xcf7: clean.
[   19.479999] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xa00-0xaff: clean.
[   19.507232] fb0: inteldrmfb frame buffer device
[   19.507236] registered panic notifier
[   19.507246] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
[   19.590255] eth0: link down
[   19.590535] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   19.661406] vga16fb: initializing
[   19.661410] vga16fb: mapped to 0xc00a0000
[   19.661414] vga16fb: not registering due to another framebuffer present
[   19.710404] phy0: Selected rate control algorithm 'iwl-3945-rs'
[   20.022065] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[   20.022253] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   20.039628] Console: switching to colour frame buffer device 160x50
[   20.233250] hda_codec: ALC262: BIOS auto-probing.
[   20.234485] input: HDA Digital PCBeep as /devices/pci0000:00/0000:00:1b.0/input/input10
[   20.390836] iwl3945 0000:03:00.0: firmware: requesting iwlwifi-3945-2.ucode
[   20.557655] iwl3945 0000:03:00.0: loaded firmware version 15.32.2.9
[   20.557818] iwl3945 0000:03:00.0: Radio disabled by HW RF Kill switch
[   20.629296] iwl3945 0000:03:00.0: Radio disabled by HW RF Kill switch
[   21.041338] ppdev: user-space parallel port driver
[   37.060066] usb 2-1: new full speed USB device using uhci_hcd and address 2
[   37.282356] usb 2-1: configuration #1 chosen from 1 choice
[   37.356321] cdc_acm 2-1:1.0: ttyACM0: USB ACM device
[   37.359309] usbcore: registered new interface driver cdc_acm
[   37.359316] cdc_acm: v0.26:USB Abstract Control Model driver for USB modems and ISDN adapters
[   98.208124] PPP BSD Compression module registered
[   98.248212] PPP Deflate Compression module registered
[   98.253079] CE: hpet increasing min_delta_ns to 15000 nsec

```

output of lspci
```

00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 3 (rev 02)
00:1d.0 USB Controller: Intel Corporation N10/ICH7 Family USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 02)
03:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02)
05:01.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
05:04.0 CardBus bridge: ENE Technology Inc CB1410 Cardbus Controller (rev 01)
05:06.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller
05:06.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
05:06.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 0a)
05:06.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 05)
05:06.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev ff)

```

output of lshw
```

optimus
    description: Computer
    width: 32 bits
  *-core
       description: Motherboard
       physical id: 0
     *-memory
          description: System memory
          physical id: 0
          size: 3015MiB
     *-cpu
          product: Intel(R) Core(TM)2 CPU         T5300  @ 1.73GHz
          vendor: Intel Corp.
          physical id: 1
          bus info: cpu@0
          version: 6.15.2
          serial: 0000-06F2-0000-0000-0000-0000
          size: 800MHz
          capacity: 800MHz
          width: 64 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx x86-64 constant_tsc arch_perfmon pebs bts aperfmperf pni dtes64 monitor ds_cpl est tm2 ssse3 cx16 xtpr pdcm lahf_lm cpufreq
          configuration: id=0
        *-logicalcpu:0
             description: Logical CPU
             physical id: 0.1
             width: 64 bits
             capabilities: logical
        *-logicalcpu:1
             description: Logical CPU
             physical id: 0.2
             width: 64 bits
             capabilities: logical
     *-pci
          description: Host bridge
          product: Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 03
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-intel
          resources: irq:0
        *-display:0
             description: VGA compatible controller
             product: Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list rom
             configuration: driver=i915 latency=0
             resources: irq:16 memory:d4200000-d427ffff ioport:1800(size=8) memory:c0000000-cfffffff(prefetchable) memory:d4300000-d433ffff
        *-display:1 UNCLAIMED
             description: Display controller
             product: Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2.1
             bus info: pci@0000:00:02.1
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: latency=0
             resources: memory:d4280000-d42fffff
        *-multimedia
             description: Audio device
             product: N10/ICH 7 Family High Definition Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 02
             width: 64 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=HDA Intel latency=0
             resources: irq:22 memory:d4340000-d4343fff
        *-pci:0
             description: PCI bridge
             product: N10/ICH 7 Family PCI Express Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci bus_master cap_list
             configuration: driver=pcieport
             resources: irq:24 ioport:2000(size=4096) memory:d2000000-d3ffffff ioport:d0000000(size=33554432)
        *-pci:1
             description: PCI bridge
             product: N10/ICH 7 Family PCI Express Port 2
             vendor: Intel Corporation
             physical id: 1c.1
             bus info: pci@0000:00:1c.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci bus_master cap_list
             configuration: driver=pcieport
             resources: irq:25 ioport:4000(size=4096) memory:d4000000-d40fffff memory:d4600000-d47fffff(prefetchable)
           *-network DISABLED
                description: Wireless interface
                product: PRO/Wireless 3945ABG [Golan] Network Connection
                vendor: Intel Corporation
                physical id: 0
                bus info: pci@0000:03:00.0
                logical name: wlan0
                version: 02
                serial: 00:1b:77:2e:fa:7a
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=iwl3945 latency=0 multicast=yes wireless=IEEE 802.11abg
                resources: irq:27 memory:d4000000-d4000fff
        *-pci:2
             description: PCI bridge
             product: N10/ICH 7 Family PCI Express Port 3
             vendor: Intel Corporation
             physical id: 1c.2
             bus info: pci@0000:00:1c.2
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci bus_master cap_list
             configuration: driver=pcieport
             resources: irq:26 ioport:5000(size=4096) memory:d4800000-d49fffff memory:d4a00000-d4bfffff(prefetchable)
        *-usb:0
             description: USB Controller
             product: N10/ICH7 Family USB UHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:23 ioport:1820(size=32)
        *-usb:1
             description: USB Controller
             product: N10/ICH 7 Family USB UHCI Controller #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:19 ioport:1840(size=32)
        *-usb:2
             description: USB Controller
             product: N10/ICH 7 Family USB UHCI Controller #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@0000:00:1d.2
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:18 ioport:1860(size=32)
        *-usb:3
             description: USB Controller
             product: N10/ICH 7 Family USB UHCI Controller #4
             vendor: Intel Corporation
             physical id: 1d.3
             bus info: pci@0000:00:1d.3
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:16 ioport:1880(size=32)
        *-usb:4
             description: USB Controller
             product: N10/ICH 7 Family USB2 EHCI Controller
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: irq:23 memory:d4544000-d45443ff
        *-pci:3
             description: PCI bridge
             product: 82801 Mobile PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: e2
             width: 32 bits
             clock: 33MHz
             capabilities: pci bus_master cap_list
             resources: ioport:3000(size=4096) memory:d4100000-d41fffff memory:d8000000-dbffffff(prefetchable)
           *-network
                description: Ethernet interface
                product: RTL-8139/8139C/8139C+
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 1
                bus info: pci@0000:05:01.0
                logical name: eth0
                version: 10
                serial: 00:1b:38:03:f8:3f
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list ethernet physical
                configuration: broadcast=yes driver=8139too driverversion=0.9.28 latency=64 maxlatency=64 mingnt=32 multicast=yes
                resources: irq:21 ioport:3000(size=256) memory:d4100000-d41000ff
           *-pcmcia
                description: CardBus bridge
                product: CB1410 Cardbus Controller
                vendor: ENE Technology Inc
                physical id: 4
                bus info: pci@0000:05:04.0
                version: 01
                width: 32 bits
                clock: 33MHz
                capabilities: pcmcia bus_master cap_list
                configuration: driver=yenta_cardbus latency=176 maxlatency=5 mingnt=192
                resources: irq:16 memory:d4102000-d4102fff ioport:3400(size=256) ioport:3800(size=256) memory:d8000000-dbffffff(prefetchable) memory:dc000000-dfffffff
           *-firewire
                description: FireWire (IEEE 1394)
                product: R5C832 IEEE 1394 Controller
                vendor: Ricoh Co Ltd
                physical id: 6
                bus info: pci@0000:05:06.0
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list
                configuration: driver=ohci1394 latency=64 maxlatency=4 mingnt=2
                resources: irq:22 memory:d4100800-d4100fff
           *-generic:0
                description: SD Host controller
                product: R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter
                vendor: Ricoh Co Ltd
                physical id: 6.1
                bus info: pci@0000:05:06.1
                version: 19
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list
                configuration: driver=sdhci-pci latency=64
                resources: irq:22 memory:d4100400-d41004ff
           *-generic:1
                description: System peripheral
                product: R5C592 Memory Stick Bus Host Adapter
                vendor: Ricoh Co Ltd
                physical id: 6.2
                bus info: pci@0000:05:06.2
                version: 0a
                width: 32 bits
                clock: 33MHz
                capabilities: cap_list
                configuration: driver=ricoh-mmc latency=0
                resources: irq:5 memory:d4101000-d41010ff
           *-generic:2 UNCLAIMED
                description: System peripheral
                product: xD-Picture Card Controller
                vendor: Ricoh Co Ltd
                physical id: 6.3
                bus info: pci@0000:05:06.3
                version: 05
                width: 32 bits
                clock: 33MHz
                capabilities: cap_list
                configuration: latency=0
                resources: memory:d4101400-d41014ff
           *-generic:3 UNCLAIMED
                product: Illegal Vendor ID
                vendor: Illegal Vendor ID
                physical id: 6.4
                bus info: pci@0000:05:06.4
                version: ff
                width: 32 bits
                clock: 66MHz
                capabilities: bus_master vga_palette cap_list
                configuration: latency=255 maxlatency=255 mingnt=255
                resources: memory:d4101800-d41018ff
        *-isa
             description: ISA bridge
             product: 82801GBM (ICH7-M) LPC Interface Bridge
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
             configuration: latency=0
        *-ide
             description: IDE interface
             product: 82801GBM/GHM (ICH7 Family) SATA IDE Controller
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             version: 02
             width: 32 bits
             clock: 66MHz
             capabilities: ide bus_master cap_list
             configuration: driver=ata_piix latency=0
             resources: irq:19 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:18b0(size=16)
        *-serial UNCLAIMED
             description: SMBus
             product: N10/ICH 7 Family SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 02
             width: 32 bits
             clock: 33MHz
             configuration: latency=0
             resources: ioport:18c0(size=32)

```
~$ lsusb
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 1b7d:070a  
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 04f2:b008 Chicony Electronics Co., Ltd USB 2.0 Camera
Bus 001 Device 002: ID 10fd:2535 Anubis Electronics, Ltd 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
[/CODE]

---

### Post by lavinog on 2010-05-02
It would also help if you could post a bootchart
[apt://bootchart](apt://bootchart)

---

### Post by ankit.vader on 2010-05-02
>  	 		 		It would also help if you could post a bootchart
[apt://bootchart](apt://bootchart)

here it is

---

### Post by ankit.vader on 2010-05-02
> I am also having the same issue but the boot time for me is almost 20-30  seconds... I am having a 2GHz dual core processor with 3GB RAM... I had  installed Lucid beta1 and updated daily and with the latest update on  1st of may, it shows LTS version.... for the beta version it was more  than 40 seconds for me and after updating it was reduced to 20+... On  selecting ubuntu from grub, a blank screen with a blinking cursor  appears for more than 10 seconds and then only the ubuntu logo is  shown....

How do i check which version i have???

---

### Post by lavinog on 2010-05-02
> **ankit.vader said:**
> How do i check which version i have???

If you were using the beta or RC, applying all of the current updates should give you the latest version. Go to the update manager, click on check, if no updates show up, you should be up to date.

The way ureadahead works is that some updates purge the readahead pack file, which should trigger a profile on next boot. Profiling will make the boot process take longer, but the subsequent boot should be much shorter.

Your bootchart image was resized by the forum, so I can't quite read it.  It kind of looks like either it was profiling that time, or it needs to be profiled.
The following command should force a profile on next boot:
```

sudo rm /var/lib/ureadahead/pack

```

---

### Post by ankit.vader on 2010-05-02
> If you were using the beta or RC, applying all of the current  updates should give you the latest version. Go to the update manager,  click on check, if no updates show up, you should be up to date.

The way ureadahead works is that some updates purge the readahead pack  file, which should trigger a profile on next boot. Profiling will make  the boot process take longer, but the subsequent boot should be much  shorter.

Your bootchart image was resized by the forum, so I can't quite read it.   It kind of looks like either it was profiling that time, or it needs  to be profiled.
The following command should force a profile on next boot:

i checked it , my system is uptodate
in ubuntu 9.10 i modified the /etc/init.d/rc file so that i can run the boot script in parallel. I replaced line that read CONCURRENCY=none with CONCURRENCY=shell. but in lucid i cannot find that line do you know where i can place it??

---

### Post by lavinog on 2010-05-02
> **ankit.vader said:**
> i checked it , my system is uptodate
in ubuntu 9.10 i modified the /etc/init.d/rc file so that i can run the boot script in parallel. I replaced line that read CONCURRENCY=none with CONCURRENCY=shell. but in lucid i cannot find that line do you know where i can place it??

It is already like that by design now.
init.d scripts are being phased out in favor of upstart which has a better form of concurrency.
This should be noticeable in the bootchart...concurrency allows for multiple processes to start at the same time.

---

### Post by lavinog on 2010-05-02
you should also note that having bootchart installed will add a couple of seconds to your boot time, and you cannot compare a bootchart in lucid with a bootchart in other releases because it includes events after logging in.

---

### Post by ankit.vader on 2010-05-02
> It is already like that by design now.
init.d scripts are being phased out in favor of upstart which has a  better form of concurrency.
This should be noticeable in the bootchart...concurrency allows for  multiple processes to start at the same time.
```

 sudo rm /var/lib/ureadahead/pack
[sudo] password for ankit: 
rm: cannot remove `/var/lib/ureadahead/pack': No such file or directory

```

but then what could be the reason for long time, a whopping 50 sec. I have a decent processor and ram and ubuntu claims 10 sec boot time

---

### Post by sarin_cv on 2010-05-03
I'm going to do a fresh install ... let me see what is the boot time then...

---

### Post by WarrenSH on 2010-05-03
> **sarin_cv said:**
> I'm going to do a fresh install ... let me see what is the boot time then...

My boot time was about 2 mins to boot when I did a fresh install. I used KillDisk to wipe out my hard drive then I did a fresh install. 9.10 is much faster for booting. 

I am going to install the netbook edition now to see if it is slower or faster.

---

### Post by WarrenSH on 2010-05-03
I installed 10.04 netbook & the boot time is about 30seconds very fast! I wonder why it is faster then the desktop ?

---

### Post by sarin_cv on 2010-05-06
> **lavinog said:**
> Can you post a bootchart?
Do you have autologin enabled?

yes... I have auologin enabled... check this link for bootchart

 [COLOR=black][FONT=&quot][http://picasaweb.google.com/sarincv/Downloads#5467982662533094194](http://picasaweb.google.com/sarincv/Downloads#5467982662533094194)[/FONT][/COLOR]

---

### Post by lavinog on 2010-05-06
> **sarin_cv said:**
> yes... I have auologin enabled... check this link for bootchart

 [COLOR=black][FONT=&quot][http://picasaweb.google.com/sarincv/Downloads#5467982662533094194](http://picasaweb.google.com/sarincv/Downloads#5467982662533094194)[/FONT][/COLOR]

I still cannot see the details of those charts...maybe you can zip them or something.

It almost looks like ureadahead isn't running.
Look at the attached bootchart, you should see a point where ureadahead is reading files.  During this time your disk throughput should be higher than any other time.  Also notice the difference with the cpu load.
I have been tweaking some things, so my boot is longer than normal.

---

### Post by sarin_cv on 2010-05-06
try this link.... if not plz giv ur personal id... i will send by mail...

 [COLOR=black][FONT=&quot][http://picasaweb.google.com/sarincv/Downloads#5467982226442974098](http://picasaweb.google.com/sarincv/Downloads#5467982226442974098)[/FONT][/COLOR]

---

### Post by lavinog on 2010-05-06
> **sarin_cv said:**
> try this link.... if not plz giv ur personal id... i will send by mail...

 [COLOR=black][FONT=&quot][http://picasaweb.google.com/sarincv/Downloads#5467982226442974098](http://picasaweb.google.com/sarincv/Downloads#5467982226442974098)[/FONT][/COLOR]

Sorry, just noticed the download link.
It doesn't look ureadahead is doing anything.  Also I see that there is some ntfs activity.  Is this a wubi install?  Are you auto mounting a ntfs partition?

---

### Post by sarin_cv on 2010-05-06
not a wubi install... i have a separate partition for Linux... yes...auto mounting the ntfs drives on startup

---

### Post by CytotoxicTcell on 2010-05-06
same here i dont see the grub screen ethier but it only takes ubuntu to load my laptop only 42 seconds to desktop from the second i press the power button.

---

### Post by sarin_cv on 2010-05-06
bringing up ...

---

### Post by sarin_cv on 2010-05-06
bringing up again......

---

### Post by ankit.vader on 2010-05-06
> I still cannot see the details of those charts...maybe you can zip them or something.

here is a zip file of my boot chart

---

### Post by lavinog on 2010-05-06
> **ankit.vader said:**
> here is a zip file of my boot chart

I see a vga=773 in your kernel options, did you add this recently? Did you upgrade to lucid or did you do a fresh install?

Ureadahead doesn't seem to be loading anything.
do you have ubuntu-desktop installed?
Are you using the default kernel?
After you boot can you post the output of:
```

cat /sys/kernel/debug/tracing/buffer_size_kb 

```

---

### Post by ankit.vader on 2010-05-07
> I see a vga=773 in your kernel options, did you add this recently? Did you upgrade to lucid or did you do a fresh install?

Ureadahead doesn't seem to be loading anything.
do you have ubuntu-desktop installed?
Are you using the default kernel?

I did a fresh install, here is the new bootchart after i did fresh install.  yes i'm using the default kernel.

---

### Post by lavinog on 2010-05-07
reboot again...it looks like ureadahead did a profile (which will lead to a slower boot)
ureadahead will require a reprofile after certain updates.  So boot times are going to be longer after you update the system, but booting aftwards should be much quicker.

---

### Post by ankit.vader on 2010-05-07
> reboot again...it looks like ureadahead did a profile (which will lead to a slower boot)
ureadahead will require a reprofile after certain updates. So boot times are going to be longer after you update the system, but booting aftwards should be much quicker.

here is bootchart after reboot.

---

### Post by lavinog on 2010-05-07
> **ankit.vader said:**
> here is bootchart after reboot.

Now it is working the way it is supposed to.
22 secs is much better.

---

### Post by sarin_cv on 2010-05-08
so I'll also do a fresh install as ankit did...... let me see...

---

### Post by Peter Bell on 2010-05-20
My hardware appears to be similar to Ankit's, and I was also experiencing long boot times.  I found that ureadahead wasn't doing anything so I reinstalled ureadahead from synaptic ... that seems to have done the trick.  My boot time (with autologin) has gone down from 1m 16s to 39s.

---

