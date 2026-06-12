---
title: "b44: eth0: BUG! Timeout waiting for bit 00000002 of register 42c to clear"
date: 2010-02-01
forum: General Help
---

### Post by planetaziemia on 2010-02-01
I've got Ubuntu 9.10. I use dial-up modem to connect to the Internet. I use UBUDSL and liked it very much  till this morning when I got the message that the ubudsl deamon doesn't want to start. I've found out that I need to use following command to solve my problem.
sudo /etc/init.d/ubudsldd start
I got the Internet but still the Ubudsl deamon didn't start automatically when I  restart my computer. I've read that I need to reinstall ubudsl so I removed it but can't install it again. 
I got the bug!
b44: eth0: BUG! Timeout waiting for bit 00000002 of register 42c to clear
HELP PLEASE!

---

### Post by planetaziemia on 2010-02-01
When I do 
sudo  dpkg --configure -a
I got the same error.

---

### Post by planetaziemia on 2010-02-01
I'm sorry because I coulnd't upload a txt file boot.messages so I had to copy the output of dmesg here, it's quite long

[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.31-17-generic (buildd@palmer) (gcc version 4.4.1 (Ubuntu 4.4.1-4ubuntu ) #54-Ubuntu SMP Thu Dec 10 16:20:31 UTC 2009 (Ubuntu 2.6.31-17.54-generic)
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
[    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000001f680000 (usable)
[    0.000000]  BIOS-e820: 000000001f680000 - 000000001f700000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000001f700000 - 0000000020000000 (reserved)
[    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed00000 - 00000000fed00400 (reserved)
[    0.000000]  BIOS-e820: 00000000fed14000 - 00000000fed1a000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed1c000 - 00000000fed90000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000ff000000 - 0000000100000000 (reserved)
[    0.000000] DMI present.
[    0.000000] last_pfn = 0x1f680 max_arch_pfn = 0x100000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-CFFFF write-protect
[    0.000000]   D0000-DFFFF uncachable
[    0.000000]   E0000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000 mask FE0000000 write-back
[    0.000000]   1 base 01F700000 mask FFFF00000 uncachable
[    0.000000]   2 base 01F800000 mask FFF800000 uncachable
[    0.000000]   3 disabled
[    0.000000]   4 disabled
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] PAT not supported by CPU.
[    0.000000] e820 update range: 0000000000002000 - 0000000000006000 (usable) ==> (reserved)
[    0.000000] Scanning 1 areas for low memory corruption
[    0.000000] modified physical RAM map:
[    0.000000]  modified: 0000000000000000 - 0000000000002000 (usable)
[    0.000000]  modified: 0000000000002000 - 0000000000006000 (reserved)
[    0.000000]  modified: 0000000000006000 - 000000000009f800 (usable)
[    0.000000]  modified: 000000000009f800 - 00000000000a0000 (reserved)
[    0.000000]  modified: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  modified: 0000000000100000 - 000000001f680000 (usable)
[    0.000000]  modified: 000000001f680000 - 000000001f700000 (ACPI NVS)
[    0.000000]  modified: 000000001f700000 - 0000000020000000 (reserved)
[    0.000000]  modified: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  modified: 00000000fec00000 - 00000000fec10000 (reserved)
[    0.000000]  modified: 00000000fed00000 - 00000000fed00400 (reserved)
[    0.000000]  modified: 00000000fed14000 - 00000000fed1a000 (reserved)
[    0.000000]  modified: 00000000fed1c000 - 00000000fed90000 (reserved)
[    0.000000]  modified: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  modified: 00000000ff000000 - 0000000100000000 (reserved)
[    0.000000] initial memory mapped : 0 - 00c00000
[    0.000000] init_memory_mapping: 0000000000000000-000000001f680000
[    0.000000] Using x86 segment limits to approximate NX protection
[    0.000000]  0000000000 - 0000400000 page 4k
[    0.000000]  0000400000 - 001f400000 page 2M
[    0.000000]  001f400000 - 001f680000 page 4k
[    0.000000] kernel direct mapping tables up to 1f680000 @ 7000-c000
[    0.000000] RAMDISK: 171d5000 - 1791fbac
[    0.000000] ACPI: RSDP 000f6290 00014 (v00 ACRSYS)
[    0.000000] ACPI: RSDT 1f686745 00054 (v01 ACRSYS ACRPRDCT 06040000  LTP 00000000)
[    0.000000] ACPI: FACP 1f68ddfa 00074 (v01 Acer   Grape    06040000 LOHR 0000005A)
[    0.000000] ACPI: DSDT 1f688067 05D93 (v01 Acer   CALISTGA 06040000 INTL 2005022
[    0.000000] ACPI: FACS 1f68efc0 00040
[    0.000000] ACPI: APIC 1f68de6e 00068 (v01 Acer   Grape    06040000 LOHR 0000005A)
[    0.000000] ACPI: HPET 1f68ded6 00038 (v01 Acer   Grape    06040000 LOHR 0000005A)
[    0.000000] ACPI: MCFG 1f68df0e 0003C (v01 Acer   Grape    06040000 LOHR 0000005A)
[    0.000000] ACPI: DBGP 1f68df4a 00034 (v01 Acer   Grape    06040000 LOHR 00000000)
[    0.000000] ACPI: APIC 1f68df7e 0005A (v01 PTLTD       APIC   06040000  LTP 00000000)
[    0.000000] ACPI: BOOT 1f68dfd8 00028 (v01 PTLTD  $SBFTBL$ 06040000  LTP 00000001)
[    0.000000] ACPI: SSDT 1f687a18 0064F (v01 SataRe  SataPri 00001000 INTL 2005022
[    0.000000] ACPI: SSDT 1f687386 00692 (v01 SataRe  SataSec 00001000 INTL 2005022
[    0.000000] ACPI: SSDT 1f686ec4 004C2 (v01  PmRef  Cpu0Cst 00003001 INTL 2005022
[    0.000000] ACPI: SSDT 1f686c65 0025F (v01  PmRef  Cpu0Tst 00003000 INTL 2005022
[    0.000000] ACPI: SSDT 1f686799 004CC (v01  PmRef    CpuPm 00003000 INTL 20050228)
[    0.000000] ACPI: BIOS bug: multiple APIC/MADT found, using 0
[    0.000000] ACPI: If "acpi_apic_instance=2" works better, notify [EMAIL="linux-acpi@vger.kernel.org"]linux-acpi@vger.kernel.org[/EMAIL]
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] 0MB HIGHMEM available.
[    0.000000] 502MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 1f680000
[    0.000000]   low ram: 0 - 1f680000
[    0.000000]   node 0 low ram: 00000000 - 1f680000
[    0.000000]   node 0 bootmap 00008000 - 0000bed0
[    0.000000] (9 early reservations) ==> bootmem [0000000000 - 001f680000]
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
[    0.000000]   #1 [0000001000 - 0000002000]    EX TRAMPOLINE ==> [0000001000 - 0000002000]
[    0.000000]   #2 [0000006000 - 0000007000]       TRAMPOLINE ==> [0000006000 - 0000007000]
[    0.000000]   #3 [0000100000 - 00008a80a0]    TEXT DATA BSS ==> [0000100000 - 00008a80a0]
[    0.000000]   #4 [00171d5000 - 001791fbac]          RAMDISK ==> [00171d5000 - 001791fbac]
[    0.000000]   #5 [000009f800 - 0000100000]    BIOS reserved ==> [000009f800 - 0000100000]
[    0.000000]   #6 [00008a9000 - 00008ac0d5]              BRK ==> [00008a9000 - 00008ac0d5]
[    0.000000]   #7 [0000007000 - 0000008000]          PGTABLE ==> [0000007000 - 0000008000]
[    0.000000]   #8 [0000008000 - 000000c000]          BOOTMAP ==> [0000008000 - 000000c000]
[    0.000000] found SMP MP-table at [c00f6340] f6340
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000000 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x0001f680
[    0.000000]   HighMem  0x0001f680 -> 0x0001f680
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[3] active PFN ranges
[    0.000000]     0: 0x00000000 -> 0x00000002
[    0.000000]     0: 0x00000006 -> 0x0000009f
[    0.000000]     0: 0x00000100 -> 0x0001f680
[    0.000000] On node 0 totalpages: 128539
[    0.000000] free_area_init_node: node 0, pgdat c0784960, node_mem_map c1000000
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3963 pages, LIFO batch:0
[    0.000000]   Normal zone: 973 pages used for memmap
[    0.000000]   Normal zone: 123571 pages, LIFO batch:31
[    0.000000] Using APIC driver default
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
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000
[    0.000000] SMP: Allowing 2 CPUs, 1 hotplug CPUs
[    0.000000] nr_irqs_gsi: 24
[    0.000000] PM: Registered nosave memory: 0000000000002000 - 0000000000006000
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
[    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 20000000 (gap: 20000000:c0000000)
[    0.000000] NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:2 nr_node_ids:1
[    0.000000] PERCPU: Embedded 14 pages at c13f2000, static data 35612 bytes
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 127534
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.31-17-generic root=UUID=b8782436-d74e-4776-aa31-757d44008cf0 ro quiet splash
[    0.000000] PID hash table entries: 2048 (order: 11, 8192 bytes)
[    0.000000] Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.000000] Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] allocated 2572800 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] Initializing HighMem for node 0 (00000000:00000000)
[    0.000000] Memory: 491412k/514560k available (4566k kernel code, 22424k reserved, 2142k data, 540k init, 0k highmem)
[    0.000000] virtual kernel memory layout:
[    0.000000]     fixmap  : 0xfff1d000 - 0xfffff000   ( 904 kB)
[    0.000000]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[    0.000000]     vmalloc : 0xdfe80000 - 0xff7fe000   ( 505 MB)
[    0.000000]     lowmem  : 0xc0000000 - 0xdf680000   ( 502 MB)
[    0.000000]       .init : 0xc078e000 - 0xc0815000   ( 540 kB)
[    0.000000]       .data : 0xc0575a64 - 0xc078d408   (2142 kB)
[    0.000000]       .text : 0xc0100000 - 0xc0575a64   (4566 kB)
[    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.000000] SLUB: Genslabs=13, HWalign=64, Order=0-3, MinObjects=0, CPUs=2, Nodes=1
[    0.000000] NR_IRQS:2304 nr_irqs:424
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 1728.706 MHz processor.
[    0.001711] Console: colour VGA+ 80x25
[    0.001716] console [tty0] enabled
[    0.001905] hpet clockevent registered
[    0.001910] HPET: 3 timers in total, 0 timers will be used for per-cpu timer
[    0.001916] Calibrating delay loop (skipped), value calculated using timer frequency.. 3457.41 BogoMIPS (lpj=6914824)
[    0.001938] Security Framework initialized
[    0.001960] AppArmor: AppArmor initialized
[    0.001968] Mount-cache hash table entries: 512
[    0.002105] Initializing cgroup subsys ns
[    0.002110] Initializing cgroup subsys cpuacct
[    0.002115] Initializing cgroup subsys memory
[    0.002123] Initializing cgroup subsys freezer
[    0.002125] Initializing cgroup subsys net_cls
[    0.002142] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.002145] CPU: L2 cache: 1024K
[    0.002150] mce: CPU supports 6 MCE banks
[    0.002161] CPU0: Thermal monitoring enabled (TM1)
[    0.002165] using mwait in idle threads.
[    0.002172] Performance Counters: no PMU driver, software counters only.
[    0.002180] Checking 'hlt' instruction... OK.
[    0.016922] SMP alternatives: switching to UP code
[    0.024007] ACPI: Core revision 20090521
[    0.040450] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.083120] CPU0: Intel(R) Celeron(R) M CPU        430  @ 1.73GHz stepping 0c
[    0.084001] Brought up 1 CPUs
[    0.084001] Total of 1 processors activated (3457.41 BogoMIPS).
[    0.084001] CPU0 attaching NULL sched-domain.
[    0.084001] Booting paravirtualized kernel on bare hardware
[    0.084001] regulator: core version 0.5
[    0.084001] Time: 19:14:31  Date: 02/01/10
[    0.084001] NET: Registered protocol family 16
[    0.084001] EISA bus registered
[    0.084001] ACPI: bus type pci registered
[    0.084001] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 255
[    0.084001] PCI: MCFG area at e0000000 reserved in E820
[    0.084001] PCI: Using MMCONFIG for extended config space
[    0.084001] PCI: Using configuration type 1 for base access
[    0.084001] bio: create slab <bio-0> at 0
[    0.084001] ACPI: EC: Look up EC in DSDT
[    0.086965] ACPI: BIOS _OSI(Linux) query ignored
[    0.087894] ACPI: Interpreter enabled
[    0.087902] ACPI: (supports S0 S3 S4 S5)
[    0.087924] ACPI: Using IOAPIC for interrupt routing
[    0.092024] ACPI: EC: non-query interrupt received, switching to interrupt mode
[    0.116093] ACPI: EC: GPE storm detected, transactions will use polling mode
[    0.153505] ACPI: EC: GPE = 0x19, I/O: command/status = 0x66, data = 0x62
[    0.153508] ACPI: EC: driver started in poll mode
[    0.153958] ACPI: No dock devices found.
[    0.154553] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.154657] pci 0000:00:02.0: reg 10 32bit mmio: [0xd0100000-0xd017ffff]
[    0.154663] pci 0000:00:02.0: reg 14 io port: [0x5088-0x508f]
[    0.154669] pci 0000:00:02.0: reg 18 32bit mmio: [0xc0000000-0xcfffffff]
[    0.154675] pci 0000:00:02.0: reg 1c 32bit mmio: [0xd0200000-0xd023ffff]
[    0.154720] pci 0000:00:02.1: reg 10 32bit mmio: [0xd0180000-0xd01fffff]
[    0.154844] pci 0000:00:1b.0: reg 10 64bit mmio: [0xd0240000-0xd0243fff]
[    0.154909] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    0.154915] pci 0000:00:1b.0: PME# disabled
[    0.155007] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    0.155012] pci 0000:00:1c.0: PME# disabled
[    0.155106] pci 0000:00:1c.1: PME# supported from D0 D3hot D3cold
[    0.155112] pci 0000:00:1c.1: PME# disabled
[    0.155205] pci 0000:00:1c.2: PME# supported from D0 D3hot D3cold
[    0.155211] pci 0000:00:1c.2: PME# disabled
[    0.155304] pci 0000:00:1c.3: PME# supported from D0 D3hot D3cold
[    0.155310] pci 0000:00:1c.3: PME# disabled
[    0.155380] pci 0000:00:1d.0: reg 20 io port: [0x50a0-0x50bf]
[    0.155448] pci 0000:00:1d.1: reg 20 io port: [0x50c0-0x50df]
[    0.155516] pci 0000:00:1d.2: reg 20 io port: [0x50e0-0x50ff]
[    0.155585] pci 0000:00:1d.3: reg 20 io port: [0x5400-0x541f]
[    0.155657] pci 0000:00:1d.7: reg 10 32bit mmio: [0xd0444000-0xd04443ff]
[    0.155723] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
[    0.155729] pci 0000:00:1d.7: PME# disabled
[    0.155907] pci 0000:00:1f.0: quirk: region 1000-107f claimed by ICH6 ACPI/GPIO/TCO
[    0.155912] pci 0000:00:1f.0: quirk: region 1180-11bf claimed by ICH6 GPIO
[    0.155918] pci 0000:00:1f.0: ICH7 LPC Generic IO decode 1 PIO at 0230 (mask 000f)
[    0.155923] pci 0000:00:1f.0: ICH7 LPC Generic IO decode 2 PIO at ff20 (mask 000f)
[    0.155997] pci 0000:00:1f.2: reg 10 io port: [0x00-0x07]
[    0.156010] pci 0000:00:1f.2: reg 14 io port: [0x00-0x03]
[    0.156018] pci 0000:00:1f.2: reg 18 io port: [0x00-0x07]
[    0.156027] pci 0000:00:1f.2: reg 1c io port: [0x00-0x03]
[    0.156036] pci 0000:00:1f.2: reg 20 io port: [0x5440-0x544f]
[    0.156074] pci 0000:00:1f.2: PME# supported from D3hot
[    0.156079] pci 0000:00:1f.2: PME# disabled
[    0.156145] pci 0000:00:1f.3: reg 20 io port: [0x5420-0x543f]
[    0.156241] pci 0000:00:1c.0: bridge io port: [0x00-0xfff]
[    0.156247] pci 0000:00:1c.0: bridge 32bit mmio: [0x000000-0x0fffff]
[    0.156505] pci 0000:06:01.0: reg 10 32bit mmio: [0xd0000000-0xd0001fff]
[    0.156565] pci 0000:06:01.0: supports D1 D2
[    0.156568] pci 0000:06:01.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.156573] pci 0000:06:01.0: PME# disabled
[    0.156603] pci 0000:06:02.0: reg 10 32bit mmio: [0xd0002000-0xd0003fff]
[    0.156695] pci 0000:06:04.0: reg 10 32bit mmio: [0x000000-0x000fff]
[    0.156724] pci 0000:06:04.0: supports D1 D2
[    0.156727] pci 0000:06:04.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.156733] pci 0000:06:04.0: PME# disabled
[    0.156785] pci 0000:06:04.1: reg 10 32bit mmio: [0xd0005000-0xd000507f]
[    0.156859] pci 0000:06:04.1: supports D1 D2
[    0.156862] pci 0000:06:04.1: PME# supported from D0 D1 D2 D3hot
[    0.156868] pci 0000:06:04.1: PME# disabled
[    0.156920] pci 0000:06:04.2: reg 10 32bit mmio: [0xd0005400-0xd00054ff]
[    0.156993] pci 0000:06:04.2: supports D1 D2
[    0.156995] pci 0000:06:04.2: PME# supported from D0 D1 D2 D3hot
[    0.157002] pci 0000:06:04.2: PME# disabled
[    0.157054] pci 0000:06:04.3: reg 10 32bit mmio: [0xd0005800-0xd000587f]
[    0.157127] pci 0000:06:04.3: supports D1 D2
[    0.157130] pci 0000:06:04.3: PME# supported from D0 D1 D2 D3hot
[    0.157136] pci 0000:06:04.3: PME# disabled
[    0.157188] pci 0000:06:04.4: reg 10 32bit mmio: [0x000000-0x0000ff]
[    0.157261] pci 0000:06:04.4: supports D1 D2
[    0.157264] pci 0000:06:04.4: PME# supported from D0 D1 D2 D3hot
[    0.157270] pci 0000:06:04.4: PME# disabled
[    0.157337] pci 0000:00:1e.0: transparent bridge
[    0.157345] pci 0000:00:1e.0: bridge 32bit mmio: [0xd0000000-0xd00fffff]
[    0.157409] pci_bus 0000:00: on NUMA node 0
[    0.157414] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.157664] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP01._PRT]
[    0.157755] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP02._PRT]
[    0.157843] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP03._PRT]
[    0.157936] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP04._PRT]
[    0.158050] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCIB._PRT]
[    0.161625] ACPI: PCI Interrupt Link [LNKA] (IRQs 1 5 *6 10 12 14 15)
[    0.161743] ACPI: PCI Interrupt Link [LNKB] (IRQs 1 5 6 *11 12 14 15)
[    0.161859] ACPI: PCI Interrupt Link [LNKC] (IRQs 1 5 6 10 12 14 15) *11
[    0.161976] ACPI: PCI Interrupt Link [LNKD] (IRQs 1 5 6 11 12 14 15) *10
[    0.162092] ACPI: PCI Interrupt Link [LNKE] (IRQs 1 5 6 10 12 14 15) *0, disabled.
[    0.162210] ACPI: PCI Interrupt Link [LNKF] (IRQs 1 5 6 11 12 14 15) *10
[    0.162325] ACPI: PCI Interrupt Link [LNKG] (IRQs 1 5 6 *10 12 14 15)
[    0.162442] ACPI: PCI Interrupt Link [LNKH] (IRQs 1 *5 6 11 12 14 15)
[    0.162657] SCSI subsystem initialized
[    0.162718] libata version 3.00 loaded.
[    0.162809] usbcore: registered new interface driver usbfs
[    0.162829] usbcore: registered new interface driver hub
[    0.162859] usbcore: registered new device driver usb
[    0.163063] ACPI: WMI: Mapper loaded
[    0.163065] PCI: Using ACPI for IRQ routing
[    0.163070] pci 0000:00:1c.0: BAR 13: can't allocate resource
[    0.163073] pci 0000:00:1c.0: BAR 14: can't allocate resource
[    0.163280] Bluetooth: Core ver 2.15
[    0.163310] NET: Registered protocol family 31
[    0.163313] Bluetooth: HCI device and connection manager initialized
[    0.163316] Bluetooth: HCI socket layer initialized
[    0.163319] NetLabel: Initializing
[    0.163321] NetLabel:  domain hash size = 128
[    0.163323] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.163337] NetLabel:  unlabeled traffic allowed by default
[    0.163371] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[    0.163377] hpet0: 3 comparators, 64-bit 14.318180 MHz counter
[    0.169781] pnp: PnP ACPI init
[    0.169805] ACPI: bus type pnp registered
[    0.460877] pnp: PnP ACPI: found 10 devices
[    0.460880] ACPI: ACPI bus type pnp unregistered
[    0.460884] PnPBIOS: Disabled by ACPI PNP
[    0.460899] system 00:01: iomem range 0xe0000000-0xefffffff has been reserved
[    0.460902] system 00:01: iomem range 0xfed14000-0xfed17fff has been reserved
[    0.460906] system 00:01: iomem range 0xfed18000-0xfed18fff has been reserved
[    0.460910] system 00:01: iomem range 0xfed19000-0xfed19fff has been reserved
[    0.460913] system 00:01: iomem range 0xfed1c000-0xfed1ffff has been reserved
[    0.460917] system 00:01: iomem range 0xfed20000-0xfed3ffff has been reserved
[    0.460925] system 00:04: iomem range 0xfed00000-0xfed003ff has been reserved
[    0.460932] system 00:06: ioport range 0x800-0x80f has been reserved
[    0.460936] system 00:06: ioport range 0x1000-0x107f has been reserved
[    0.460940] system 00:06: ioport range 0x1180-0x11bf has been reserved
[    0.460943] system 00:06: ioport range 0x1640-0x164f has been reserved
[    0.460947] system 00:06: ioport range 0xfe00-0xfefe has been reserved
[    0.460950] system 00:06: ioport range 0xff2c-0xff2f has been reserved
[    0.495656] AppArmor: AppArmor Filesystem Enabled
[    0.495736] pci 0000:00:1c.0: PCI bridge, secondary bus 0000:02
[    0.495739] pci 0000:00:1c.0:   IO window: disabled
[    0.495746] pci 0000:00:1c.0:   MEM window: disabled
[    0.495751] pci 0000:00:1c.0:   PREFETCH window: disabled
[    0.495757] pci 0000:00:1c.1: PCI bridge, secondary bus 0000:03
[    0.495759] pci 0000:00:1c.1:   IO window: disabled
[    0.495766] pci 0000:00:1c.1:   MEM window: disabled
[    0.495771] pci 0000:00:1c.1:   PREFETCH window: disabled
[    0.495776] pci 0000:00:1c.2: PCI bridge, secondary bus 0000:04
[    0.495779] pci 0000:00:1c.2:   IO window: disabled
[    0.495785] pci 0000:00:1c.2:   MEM window: disabled
[    0.495790] pci 0000:00:1c.2:   PREFETCH window: disabled
[    0.495796] pci 0000:00:1c.3: PCI bridge, secondary bus 0000:05
[    0.495798] pci 0000:00:1c.3:   IO window: disabled
[    0.495805] pci 0000:00:1c.3:   MEM window: disabled
[    0.495810] pci 0000:00:1c.3:   PREFETCH window: disabled
[    0.495827] pci 0000:06:04.0: CardBus bridge, secondary bus 0000:07
[    0.495830] pci 0000:06:04.0:   IO window: 0x002000-0x0020ff
[    0.495838] pci 0000:06:04.0:   IO window: 0x002400-0x0024ff
[    0.495844] pci 0000:06:04.0:   PREFETCH window: 0x20000000-0x23ffffff
[    0.495851] pci 0000:06:04.0:   MEM window: 0x24000000-0x27ffffff
[    0.495858] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:06
[    0.495863] pci 0000:00:1e.0:   IO window: 0x2000-0x2fff
[    0.495870] pci 0000:00:1e.0:   MEM window: 0xd0000000-0xd00fffff
[    0.495876] pci 0000:00:1e.0:   PREFETCH window: 0x20000000-0x23ffffff
[    0.495892]   alloc irq_desc for 17 on node -1
[    0.495895]   alloc kstat_irqs on node -1
[    0.495902] pci 0000:00:1c.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    0.495910] pci 0000:00:1c.0: setting latency timer to 64
[    0.495920]   alloc irq_desc for 16 on node -1
[    0.495922]   alloc kstat_irqs on node -1
[    0.495926] pci 0000:00:1c.1: PCI INT B -> GSI 16 (level, low) -> IRQ 16
[    0.495932] pci 0000:00:1c.1: setting latency timer to 64
[    0.495941]   alloc irq_desc for 18 on node -1
[    0.495943]   alloc kstat_irqs on node -1
[    0.495947] pci 0000:00:1c.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.495953] pci 0000:00:1c.2: setting latency timer to 64
[    0.495962]   alloc irq_desc for 19 on node -1
[    0.495964]   alloc kstat_irqs on node -1
[    0.495968] pci 0000:00:1c.3: PCI INT D -> GSI 19 (level, low) -> IRQ 19
[    0.495973] pci 0000:00:1c.3: setting latency timer to 64
[    0.495980] pci 0000:00:1e.0: enabling device (0004 -> 0007)
[    0.495987] pci 0000:00:1e.0: setting latency timer to 64
[    0.495998] pci 0000:06:04.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.496007] pci_bus 0000:00: resource 0 io:  [0x00-0xffff]
[    0.496010] pci_bus 0000:00: resource 1 mem: [0x000000-0xffffffff]
[    0.496013] pci_bus 0000:02: resource 0 mem: [0x0-0xfff]
[    0.496016] pci_bus 0000:02: resource 1 mem: [0x0-0xfffff]
[    0.496020] pci_bus 0000:06: resource 0 io:  [0x2000-0x2fff]
[    0.496023] pci_bus 0000:06: resource 1 mem: [0xd0000000-0xd00fffff]
[    0.496027] pci_bus 0000:06: resource 2 pref mem [0x20000000-0x23ffffff]
[    0.496030] pci_bus 0000:06: resource 3 io:  [0x00-0xffff]
[    0.496033] pci_bus 0000:06: resource 4 mem: [0x000000-0xffffffff]
[    0.496037] pci_bus 0000:07: resource 0 io:  [0x2000-0x20ff]
[    0.496047] pci_bus 0000:07: resource 1 io:  [0x2400-0x24ff]
[    0.496050] pci_bus 0000:07: resource 2 pref mem [0x20000000-0x23ffffff]
[    0.496054] pci_bus 0000:07: resource 3 mem: [0x24000000-0x27ffffff]
[    0.496095] NET: Registered protocol family 2
[    0.496198] IP route cache hash table entries: 4096 (order: 2, 16384 bytes)
[    0.496484] TCP established hash table entries: 16384 (order: 5, 131072 bytes)
[    0.496585] TCP bind hash table entries: 16384 (order: 5, 131072 bytes)
[    0.496680] TCP: Hash tables configured (established 16384 bind 16384)
[    0.496683] TCP reno registered
[    0.496761] NET: Registered protocol family 1
[    0.496826] Trying to unpack rootfs image as initramfs...
[    0.720102] Switched to high resolution mode on CPU 0
[    0.730432] Freeing initrd memory: 7466k freed
[    0.735654] Simple Boot Flag at 0x36 set to 0x1
[    0.735810] cpufreq-nforce2: No nForce2 chipset.
[    0.735843] Scanning for low memory corruption every 60 seconds
[    0.735975] audit: initializing netlink socket (disabled)
[    0.735996] type=2000 audit(1265051670.732:1): initialized
[    0.746153] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    0.747777] VFS: Disk quotas dquot_6.5.2
[    0.747842] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.748484] fuse init (API version 7.12)
[    0.748577] msgmni has been set to 974
[    0.748793] alg: No test for stdrng (krng)
[    0.748807] io scheduler noop registered
[    0.748809] io scheduler anticipatory registered
[    0.748812] io scheduler deadline registered
[    0.748860] io scheduler cfq registered (default)
[    0.748875] pci 0000:00:02.0: Boot video device
[    0.749129]   alloc irq_desc for 24 on node -1
[    0.749132]   alloc kstat_irqs on node -1
[    0.749145] pcieport-driver 0000:00:1c.0: irq 24 for MSI/MSI-X
[    0.749158] pcieport-driver 0000:00:1c.0: setting latency timer to 64
[    0.749323]   alloc irq_desc for 25 on node -1
[    0.749326]   alloc kstat_irqs on node -1
[    0.749335] pcieport-driver 0000:00:1c.1: irq 25 for MSI/MSI-X
[    0.749347] pcieport-driver 0000:00:1c.1: setting latency timer to 64
[    0.749505]   alloc irq_desc for 26 on node -1
[    0.749508]   alloc kstat_irqs on node -1
[    0.749517] pcieport-driver 0000:00:1c.2: irq 26 for MSI/MSI-X
[    0.749529] pcieport-driver 0000:00:1c.2: setting latency timer to 64
[    0.749692]   alloc irq_desc for 27 on node -1
[    0.749694]   alloc kstat_irqs on node -1
[    0.749703] pcieport-driver 0000:00:1c.3: irq 27 for MSI/MSI-X
[    0.749715] pcieport-driver 0000:00:1c.3: setting latency timer to 64
[    0.749825] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.749958] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.804083] ACPI: AC Adapter [ACAD] (on-line)
[    0.804155] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input0
[    0.804159] ACPI: Power Button [PWRF]
[    0.804216] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input1
[    0.804262] ACPI: Lid Switch [LID]
[    0.804312] input: Sleep Button as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input2
[    0.804315] ACPI: Sleep Button [SLPB]
[    0.804363] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input3
[    0.804366] ACPI: Power Button [PWRB]
[    0.805424] Marking TSC unstable due to TSC halts in idle
[    0.805446] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[    0.805474] processor LNXCPU:00: registered as cooling_device0
[    0.805478] ACPI: Processor [CPU0] (supports 8 throttling states)
[    0.992071] thermal LNXTHERM:01: registered as thermal_zone0
[    0.992080] ACPI: Thermal Zone [TZ00] (54 C)
[    1.104069] thermal LNXTHERM:02: registered as thermal_zone1
[    1.104078] ACPI: Thermal Zone [TZ01] (54 C)
[    1.104132] isapnp: Scanning for PnP cards...
[    1.458366] isapnp: No Plug & Play device found
[    2.648109] ACPI: Battery Slot [BAT1] (battery present)
[    2.648257] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    2.649702] brd: module loaded
[    2.650198] loop: module loaded
[    2.650285] input: Macintosh mouse button emulation as /devices/virtual/input/input4
[    2.650417] ata_piix 0000:00:1f.2: version 2.13
[    2.650438] ata_piix 0000:00:1f.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    2.650445] ata_piix 0000:00:1f.2: MAP [ P0 P2 IDE IDE ]
[    2.804023] ata_piix 0000:00:1f.2: setting latency timer to 64
[    2.804118] scsi0 : ata_piix
[    2.804220] scsi1 : ata_piix
[    2.805350] ata1: SATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0x5440 irq 14
[    2.805354] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x5448 irq 15
[    2.806278] Fixed MDIO Bus: probed
[    2.806317] PPP generic driver version 2.4.2
[    2.806417] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    2.806440]   alloc irq_desc for 23 on node -1
[    2.806443]   alloc kstat_irqs on node -1
[    2.806450] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    2.806466] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    2.806471] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    2.806533] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 1
[    2.810460] ehci_hcd 0000:00:1d.7: debug port 1
[    2.810467] ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported
[    2.810751] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xd0444000
[    2.824015] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    2.824116] usb usb1: configuration #1 chosen from 1 choice
[    2.824149] hub 1-0:1.0: USB hub found
[    2.824158] hub 1-0:1.0: 8 ports detected
[    2.824237] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    2.824256] uhci_hcd: USB Universal Host Controller Interface driver
[    2.824292] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    2.824300] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    2.824304] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    2.824337] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    2.824367] uhci_hcd 0000:00:1d.0: irq 23, io base 0x000050a0
[    2.824451] usb usb2: configuration #1 chosen from 1 choice
[    2.824483] hub 2-0:1.0: USB hub found
[    2.824491] hub 2-0:1.0: 2 ports detected
[    2.824539] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    2.824546] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    2.824551] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    2.824583] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 3
[    2.824620] uhci_hcd 0000:00:1d.1: irq 19, io base 0x000050c0
[    2.824713] usb usb3: configuration #1 chosen from 1 choice
[    2.824742] hub 3-0:1.0: USB hub found
[    2.824749] hub 3-0:1.0: 2 ports detected
[    2.824797] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    2.824804] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    2.824808] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    2.824839] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 4
[    2.824879] uhci_hcd 0000:00:1d.2: irq 18, io base 0x000050e0
[    2.824964] usb usb4: configuration #1 chosen from 1 choice
[    2.824993] hub 4-0:1.0: USB hub found
[    2.825000] hub 4-0:1.0: 2 ports detected
[    2.825048] uhci_hcd 0000:00:1d.3: PCI INT D -> GSI 16 (level, low) -> IRQ 16
[    2.825055] uhci_hcd 0000:00:1d.3: setting latency timer to 64
[    2.825059] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[    2.825090] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 5
[    2.825126] uhci_hcd 0000:00:1d.3: irq 16, io base 0x00005400
[    2.825216] usb usb5: configuration #1 chosen from 1 choice
[    2.825245] hub 5-0:1.0: USB hub found
[    2.825252] hub 5-0:1.0: 2 ports detected
[    2.825362] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:MSS0] at 0x60,0x64 irq 1,12
[    2.825697] i8042.c: Detected active multiplexing controller, rev 1.1.
[    2.825780] serio: i8042 KBD port at 0x60,0x64 irq 1
[    2.825787] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[    2.825790] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[    2.825794] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[    2.825797] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[    2.825859] mice: PS/2 mouse device common for all mice
[    2.825999] rtc_cmos 00:07: RTC can wake from S4
[    2.826037] rtc_cmos 00:07: rtc core: registered rtc_cmos as rtc0
[    2.826070] rtc0: alarms up to one month, y3k, 242 bytes nvram, hpet irqs
[    2.826189] device-mapper: uevent: version 1.0.3
[    2.826292] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: [EMAIL="dm-devel@redhat.com"]dm-devel@redhat.com[/EMAIL]
[    2.826381] device-mapper: multipath: version 1.1.0 loaded
[    2.826384] device-mapper: multipath round-robin: version 1.0.0 loaded
[    2.826516] EISA: Probing bus 0 at eisa.0
[    2.826524] Cannot allocate resource for EISA slot 1
[    2.826526] Cannot allocate resource for EISA slot 2
[    2.826537] Cannot allocate resource for EISA slot 5
[    2.826550] EISA: Detected 0 cards.
[    2.826643] cpuidle: using governor ladder
[    2.826711] cpuidle: using governor menu
[    2.827262] TCP cubic registered
[    2.827438] NET: Registered protocol family 10
[    2.827900] lo: Disabled Privacy Extensions
[    2.828249] NET: Registered protocol family 17
[    2.828269] Bluetooth: L2CAP ver 2.13
[    2.828271] Bluetooth: L2CAP socket layer initialized
[    2.828274] Bluetooth: SCO (Voice Link) ver 0.6
[    2.828276] Bluetooth: SCO socket layer initialized
[    2.828326] Bluetooth: RFCOMM TTY layer initialized
[    2.828330] Bluetooth: RFCOMM socket layer initialized
[    2.828332] Bluetooth: RFCOMM ver 1.11
[    2.828364] Using IPI No-Shortcut mode
[    2.828443] PM: Resume from disk failed.
[    2.828456] registered taskstats version 1
[    2.828580]   Magic number: 14:232:242
[    2.828694] rtc_cmos 00:07: setting system clock to 2010-02-01 19:14:33 UTC (1265051673)
[    2.828699] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    2.828701] EDD information not available.
[    2.830214] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input5
[    2.972616] ata1.00: ATA-7: TOSHIBA MK8034GSX, AH301J, max UDMA/100
[    2.972621] ata1.00: 156301488 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    2.988573] ata1.00: configured for UDMA/100
[    2.988711] scsi 0:0:0:0: Direct-Access     ATA      TOSHIBA MK8034GS AH30 PQ: 0 ANSI: 5
[    2.988838] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    2.988881] sd 0:0:0:0: [sda] 156301488 512-byte logical blocks: (80.0 GB/74.5 GiB)
[    2.988934] sd 0:0:0:0: [sda] Write Protect is off
[    2.988938] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    2.988966] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.989109]  sda:
[    2.996419] ata2.00: ATAPI: Slimtype DVDRW SSM-8515S, GRS6, max UDMA/33
[    3.000024] Clocksource tsc unstable (delta = -86835739 ns)
[    3.023479]  sda1 sda2 <
[    3.036329] ata2.00: configured for UDMA/33
[    3.039354] scsi 1:0:0:0: CD-ROM            Slimtype DVDRW SSM-8515S  GRS6 PQ: 0 ANSI: 5
[    3.042802]  sda5sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[    3.048842] Uniform CD-ROM driver Revision: 3.20
[    3.048936] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    3.048983] sr 1:0:0:0: Attached scsi generic sg1 type 5
[    3.057274]  sda6 sda7 > sda3
[    3.077202] sd 0:0:0:0: [sda] Attached SCSI disk
[    3.216368] Freeing unused kernel memory: 540k freed
[    3.216700] Write protecting the kernel text: 4568k
[    3.216741] Write protecting the kernel read-only data: 1836k
[    3.391794] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:06/input/input6
[    3.391842] ACPI: Video Device [GFX0] (multi-head: yes  rom: no  post: no)
[    3.392488] Linux agpgart interface v0.103
[    3.434869] agpgart-intel 0000:00:00.0: Intel 945GM Chipset
[    3.435101] agpgart-intel 0000:00:00.0: detected 7932K stolen memory
[    3.437756] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0xc0000000
[    3.484445] usb 1-4: new high speed USB device using ehci_hcd and address 3
[    3.549563] [drm] Initialized drm 1.1.0 20060810
[    3.569021] i915 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    3.569028] i915 0000:00:02.0: setting latency timer to 64
[    3.680302] b43-pci-bridge 0000:06:02.0: enabling device (0000 -> 0002)
[    3.680314]   alloc irq_desc for 22 on node -1
[    3.680317]   alloc kstat_irqs on node -1
[    3.680325] b43-pci-bridge 0000:06:02.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[    3.680336] b43-pci-bridge 0000:06:02.0: setting latency timer to 64
[    4.096880] [drm] TV-14: set mode NTSC 480i 0
[    4.226930] [drm] fb0: inteldrmfb frame buffer device
[    4.226942] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
[    4.236477] ssb: Sonics Silicon Backplane found on PCI device 0000:06:02.0
[    4.310828] [drm] LVDS-8: set mode 1280x800 17
[    4.513728]   alloc irq_desc for 21 on node -1
[    4.513732]   alloc kstat_irqs on node -1
[    4.513741] b44 0000:06:01.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[    4.513752] b44 0000:06:01.0: setting latency timer to 64
[    4.538973] Console: switching to colour frame buffer device 160x50
[    4.539078] usb 1-4: configuration #1 chosen from 1 choice
[    4.592089] ssb: Sonics Silicon Backplane found on PCI device 0000:06:01.0
[    4.592116] b44.c:v2.0
[    4.612793] eth0: Broadcom 44xx/47xx 10/100BaseT Ethernet 00:16:d4:c9:a4:f2
[    4.788038] usb 2-1: new low speed USB device using uhci_hcd and address 2
[    4.965514] usb 2-1: configuration #1 chosen from 1 choice
[    5.000248] usbcore: registered new interface driver hiddev
[    5.000307] usbcore: registered new interface driver usbhid
[    5.000311] usbhid: v2.6:USB HID core driver
[    5.020309] input: A4Tech PS/2+USB Mouse as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1:1.0/input/input7
[    5.020405] a4tech 0003:09DA:000A.0001: input,hidraw0: USB HID v1.10 Mouse [A4Tech PS/2+USB Mouse] on usb-0000:00:1d.0-1/input0
[    5.190595] PM: Starting manual resume from disk
[    5.190600] PM: Resume from partition 8:7
[    5.190603] PM: Checking hibernation image.
[    5.190891] PM: Resume from disk failed.
[    5.193984] EXT4-fs (sda3): INFO: recovery required on readonly filesystem
[    5.193990] EXT4-fs (sda3): write access will be enabled during recovery
[    5.209001] EXT4-fs (sda3): barriers enabled
[    6.005002] kjournald2 starting: pid 359, dev sda3:8, commit interval 5 seconds
[    6.005023] EXT4-fs (sda3): delayed allocation enabled
[    6.005027] EXT4-fs: file extents enabled
[    6.005097] EXT4-fs: mballoc enabled
[    6.005115] EXT4-fs (sda3): orphan cleanup on readonly fs
[    6.005123] EXT4-fs (sda3): ext4_orphan_cleanup: deleting unreferenced inode 1780
[    6.005161] EXT4-fs (sda3): 1 orphan inode deleted
[    6.005165] EXT4-fs (sda3): recovery complete
[    6.389891] EXT4-fs (sda3): mounted filesystem with ordered data mode
[    7.449268] type=1505 audit(1265051678.119:2): operation="profile_load" pid=382 name=/usr/share/gdm/guest-session/Xsession
[    7.468888] type=1505 audit(1265051678.139:3): operation="profile_load" pid=383 name=/sbin/dhclient3
[    7.469644] type=1505 audit(1265051678.139:4): operation="profile_load" pid=383 name=/usr/lib/NetworkManager/nm-dhcp-client.action
[    7.470055] type=1505 audit(1265051678.139:5): operation="profile_load" pid=383 name=/usr/lib/connman/scripts/dhclient-script
[    7.550184] type=1505 audit(1265051678.219:6): operation="profile_load" pid=384 name=/usr/bin/evince
[    7.562581] type=1505 audit(1265051678.231:7): operation="profile_load" pid=384 name=/usr/bin/evince-previewer
[    7.569883] type=1505 audit(1265051678.239:8): operation="profile_load" pid=384 name=/usr/bin/evince-thumbnailer
[    7.597372] type=1505 audit(1265051678.267:9): operation="profile_load" pid=386 name=/usr/lib/cups/backend/cups-pdf
[    7.598264] type=1505 audit(1265051678.267:10): operation="profile_load" pid=386 name=/usr/sbin/cupsd
[    7.637142] type=1505 audit(1265051678.307:11): operation="profile_load" pid=387 name=/usr/sbin/dhcpd3
[   25.185205] Adding 537592k swap on /dev/sda7.  Priority:-1 extents:1 across:537592k 
[   25.596477] udev: starting version 147
[   25.739620] EXT4-fs (sda3): internal journal on sda3:8
[   26.360394] lp: driver loaded but no devices found
[   26.545374] acer-wmi: Acer Laptop ACPI-WMI Extras
[   26.905228] sdhci: Secure Digital Host Controller Interface driver
[   26.905232] sdhci: Copyright(c) Pierre Ossman
[   26.912215] cfg80211: Calling CRDA to update world regulatory domain
[   26.917911] Linux video capture interface: v2.00
[   26.972746] intel_rng: FWH not detected
[   26.996407] yenta_cardbus 0000:06:04.0: CardBus bridge found [1025:0090]
[   26.996434] yenta_cardbus 0000:06:04.0: Using CSCINT to route CSC interrupts to PCI
[   26.996437] yenta_cardbus 0000:06:04.0: Routing CardBus interrupts to PCI
[   26.996443] yenta_cardbus 0000:06:04.0: TI: mfunc 0x90501212, devctl 0x44
[   27.120243] Synaptics Touchpad, model: 1, fw: 6.2, id: 0x1280b1, caps: 0xa04713/0x204000
[   27.170281] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio4/input/input8
[   27.228804] yenta_cardbus 0000:06:04.0: ISA IRQ mask 0x0cf8, PCI irq 16
[   27.228811] yenta_cardbus 0000:06:04.0: Socket status: 30000006
[   27.228816] pci_bus 0000:06: Raising subordinate bus# of parent bus (#06) from #07 to #0a
[   27.228827] yenta_cardbus 0000:06:04.0: pcmcia: parent PCI bridge I/O window: 0x2000 - 0x2fff
[   27.228831] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x2000-0x2fff: clean.
[   27.229037] yenta_cardbus 0000:06:04.0: pcmcia: parent PCI bridge Memory window: 0xd0000000 - 0xd00fffff
[   27.229041] yenta_cardbus 0000:06:04.0: pcmcia: parent PCI bridge Memory window: 0x20000000 - 0x23ffffff
[   27.229322] sdhci-pci 0000:06:04.2: SDHCI controller found [1524:0550] (rev 1)
[   27.229337] sdhci-pci 0000:06:04.2: enabling device (0000 -> 0002)
[   27.229347] sdhci-pci 0000:06:04.2: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[   27.229441] Registered led device: mmc0::
[   27.229481] mmc0: SDHCI controller on PCI [0000:06:04.2] using PIO
[   27.229493] sdhci-pci 0000:06:04.4: SDHCI controller found [1524:0551] (rev 1)
[   27.229506] sdhci-pci 0000:06:04.4: enabling device (0000 -> 0002)
[   27.229512] sdhci-pci 0000:06:04.4: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[   27.229552] Registered led device: mmc1::
[   27.229583] mmc1: SDHCI controller on PCI [0000:06:04.4] using PIO
[   27.334857] uvcvideo: Found UVC 1.00 device USB2.0 Camera (5986:0100)
[   27.403853] input: USB2.0 Camera as /devices/pci0000:00/0000:00:1d.7/usb1/1-4/1-4:1.0/input/input9
[   27.403916] usbcore: registered new interface driver uvcvideo
[   27.403920] USB Video Class driver (v0.1.0)
[   27.557310] cfg80211: World regulatory domain updated:
[   27.557315]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   27.557319]     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   27.557322]     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   27.557325]     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   27.557329]     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   27.557332]     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   27.607640] b43-phy0: Broadcom 4318 WLAN found (core revision 9)
[   28.088640] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x100-0x3af: clean.
[   28.090740] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x3e0-0x4ff: excluding 0x4d0-0x4d7
[   28.091612] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x820-0x8ff: clean.
[   28.092354] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xc00-0xcf7: clean.
[   28.093257] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xa00-0xaff: clean.
[   28.184113] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   28.278020] phy0: Selected rate control algorithm 'minstrel'
[   28.278756] Broadcom 43xx driver loaded [ Features: PL, Firmware-ID: FW13 ]
[   28.352061] b43 ssb0:0: firmware: requesting b43/ucode5.fw
[   28.579233] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[   28.579278] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   28.692963] b43 ssb0:0: firmware: requesting b43/pcm5.fw
[   28.737365] input: HDA Digital PCBeep as /devices/pci0000:00/0000:00:1b.0/input/input10
[   28.795832] b43 ssb0:0: firmware: requesting b43/b0g0initvals5.fw
[   28.825689] b43 ssb0:0: firmware: requesting b43/b0g0bsinitvals5.fw
[   28.992158] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
[   29.028994] Registered led device: b43-phy0::tx
[   29.029017] Registered led device: b43-phy0::rx
[   29.029040] Registered led device: b43-phy0::radio
[   29.029456] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   29.619675] [drm] TV-14: set mode NTSC 480i 0
[   29.765709] [drm] TV-14: set mode NTSC 480i 0
[   30.052648] [drm] TV-14: set mode NTSC 480i 0
[   30.198074] [drm] TV-14: set mode NTSC 480i 0
[   36.784875] [drm] TV-14: set mode NTSC 480i 0
[   36.930738] [drm] TV-14: set mode NTSC 480i 0
[   37.240097] [drm] TV-14: set mode NTSC 480i 0
[   37.385466] [drm] TV-14: set mode NTSC 480i 0
[   37.671473] [drm] TV-14: set mode NTSC 480i 0
[   37.815853] [drm] TV-14: set mode NTSC 480i 0
[   39.475469] [drm] TV-14: set mode NTSC 480i 0
[   39.621484] [drm] TV-14: set mode NTSC 480i 0
[   44.576863] wlan0: direct probe to AP 00:0b:6b:da:69:4c try 1
[   44.776051] wlan0: direct probe to AP 00:0b:6b:da:69:4c try 2
[   44.985562] wlan0: direct probe to AP 00:0b:6b:da:69:4c try 3
[   45.184036] wlan0: direct probe to AP 00:0b:6b:da:69:4c timed out
[   51.016419] wlan0: direct probe to AP 00:0b:6b:da:69:4c try 1
[   51.216053] wlan0: direct probe to AP 00:0b:6b:da:69:4c try 2
[   51.416038] wlan0: direct probe to AP 00:0b:6b:da:69:4c try 3
[   51.616051] wlan0: direct probe to AP 00:0b:6b:da:69:4c timed out
[   62.180435] wlan0: direct probe to AP 00:0b:6b:da:69:4c try 1
[   62.380066] wlan0: direct probe to AP 00:0b:6b:da:69:4c try 2
[   62.580064] wlan0: direct probe to AP 00:0b:6b:da:69:4c try 3
[   62.780060] wlan0: direct probe to AP 00:0b:6b:da:69:4c timed out
[   68.612806] wlan0: direct probe to AP 00:0b:6b:da:69:4c try 1
[   68.812040] wlan0: direct probe to AP 00:0b:6b:da:69:4c try 2
[   69.017587] wlan0: direct probe to AP 00:0b:6b:da:69:4c try 3
[   69.216043] wlan0: direct probe to AP 00:0b:6b:da:69:4c timed out
[   75.048421] wlan0: direct probe to AP 00:0b:6b:da:69:4c try 1
[   75.249023] wlan0: direct probe to AP 00:0b:6b:da:69:4c try 2
[   75.448059] wlan0: direct probe to AP 00:0b:6b:da:69:4c try 3
[   75.648043] wlan0: direct probe to AP 00:0b:6b:da:69:4c timed out
[   81.495202] wlan0: direct probe to AP 00:0b:6b:da:69:4c try 1
[   81.692272] wlan0: direct probe to AP 00:0b:6b:da:69:4c try 2
[   81.892036] wlan0: direct probe to AP 00:0b:6b:da:69:4c try 3
[   82.092043] wlan0: direct probe to AP 00:0b:6b:da:69:4c timed out
[   98.628412] wlan0: direct probe to AP 00:0b:6b:da:69:4c try 1
[   98.828052] wlan0: direct probe to AP 00:0b:6b:da:69:4c try 2
[   99.028060] wlan0: direct probe to AP 00:0b:6b:da:69:4c try 3
[   99.228062] wlan0: direct probe to AP 00:0b:6b:da:69:4c timed out
[  105.124959] wlan0: direct probe to AP 00:0b:6b:da:69:4c try 1
[  105.324277] wlan0: direct probe to AP 00:0b:6b:da:69:4c try 2
[  105.525095] wlan0: direct probe to AP 00:0b:6b:da:69:4c try 3
[  105.724042] wlan0: direct probe to AP 00:0b:6b:da:69:4c timed out
[  111.548426] wlan0: direct probe to AP 00:0b:6b:da:69:4c try 1
[  111.748056] wlan0: direct probe to AP 00:0b:6b:da:69:4c try 2
[  111.948029] wlan0: direct probe to AP 00:0b:6b:da:69:4c try 3
[  112.148054] wlan0: direct probe to AP 00:0b:6b:da:69:4c timed out
[  117.964410] wlan0: direct probe to AP 00:0b:6b:da:69:4c try 1
[  118.164034] wlan0: direct probe to AP 00:0b:6b:da:69:4c try 2
[  118.364034] wlan0: direct probe to AP 00:0b:6b:da:69:4c try 3
[  118.564068] wlan0: direct probe to AP 00:0b:6b:da:69:4c timed out
[  124.420329] wlan0: direct probe to AP 00:0b:6b:da:69:4c try 1
[  124.620064] wlan0: direct probe to AP 00:0b:6b:da:69:4c try 2
[  124.820053] wlan0: direct probe to AP 00:0b:6b:da:69:4c try 3
[  125.020052] wlan0: direct probe to AP 00:0b:6b:da:69:4c timed out
[  130.828409] wlan0: direct probe to AP 00:0b:6b:da:69:4c try 1
[  131.028068] wlan0: direct probe to AP 00:0b:6b:da:69:4c try 2
[  131.228058] wlan0: direct probe to AP 00:0b:6b:da:69:4c try 3
[  131.428063] wlan0: direct probe to AP 00:0b:6b:da:69:4c timed out
[  135.760402] wlan0: direct probe to AP 00:0b:6b:da:69:4c try 1
[  135.960176] wlan0: direct probe to AP 00:0b:6b:da:69:4c try 2
[  136.160059] wlan0: direct probe to AP 00:0b:6b:da:69:4c try 3
[  136.360259] wlan0: direct probe to AP 00:0b:6b:da:69:4c timed out

---

### Post by planetaziemia on 2010-02-01
I've found out that I got the bug only when I try to 

sudo dpkg --configure ubudsl

so there's a problem with ubudsl and ubuntu. It maybe started after the update and it isn't the first time that I have some issue after updating (if I would upgrade than my system is dead).
Be honest I'm fed up of the "mighty Ubuntu". It's shame that one of the best distro makes me ](*,)](*,) 

the worst thing is that my ADSL modem Sagem Fast e400 works only with ubudsl ( I've tried a few distros before and only ubudsl is good for me) so I've got to stick to it. As far as I know ubudsl works also with opensuse so I'll give it a try despite the fact I hate Novell & Microsoft deal. but then I'll learn some rpm stuff instead of deb. 

I reallly like debian, ubuntu phiosphy but the updating stuff makes me think that ubuntu sukcs :( 

All the best,

---

### Post by planetaziemia on 2010-03-01
I'm back with ubuntu because I didn't actually install Suse but I did Fedora. I couldn't make ubudsl so I reinstall ubuntu. Noweverything works fine.
SOLVED!

---

