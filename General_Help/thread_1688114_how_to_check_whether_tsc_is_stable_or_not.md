---
title: "how to check whether tsc is stable or not?"
date: 2011-02-15
forum: General Help
---

### Post by begroup on 2011-02-15
Hello all,
We have set our clocksource to TSC on two laptops: Compaq Presario V3000 and IBM Thinkpad.
After about half an hour, the clocks of both the laptops drift by about 10 min. We observed the BIOS settings where the system time on both the laptops was accurate upto seconds.
So is this hapening due to Changing the clock source to TSC??
Does this indicate that TSC is unstable??? How to verify that???

Here is the dmesg output:




[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.36.2 (root@shekhar) (gcc version 4.4.3 (Ubuntu 4.4.3-4ubuntu5) ) #1 SMP Fri Jan 28 21:06:24 IST 2011
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
[    0.000000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000dc000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000007f680000 (usable)
[    0.000000]  BIOS-e820: 000000007f680000 - 000000007f700000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000007f700000 - 0000000080000000 (reserved)
[    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed00000 - 00000000fed00400 (reserved)
[    0.000000]  BIOS-e820: 00000000fed14000 - 00000000fed1a000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed1c000 - 00000000fed90000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000ff000000 - 0000000100000000 (reserved)
[    0.000000] Notice: NX (Execute Disable) protection cannot be enabled: non-PAE kernel!
[    0.000000] DMI present.
[    0.000000] e820 update range: 0000000000000000 - 0000000000001000 (usable) ==> (reserved)
[    0.000000] e820 remove range: 00000000000a0000 - 0000000000100000 (usable)
[    0.000000] last_pfn = 0x7f680 max_arch_pfn = 0x100000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-CFFFF write-protect
[    0.000000]   D0000-DFFFF uncachable
[    0.000000]   E0000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000 mask F80000000 write-back
[    0.000000]   1 base 07F700000 mask FFFF00000 uncachable
[    0.000000]   2 base 07F800000 mask FFF800000 uncachable
[    0.000000]   3 disabled
[    0.000000]   4 disabled
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] PAT not supported by CPU.
[    0.000000] e820 update range: 0000000000002000 - 0000000000010000 (usable) ==> (reserved)
[    0.000000] Scanning 1 areas for low memory corruption
[    0.000000] modified physical RAM map:
[    0.000000]  modified: 0000000000000000 - 0000000000001000 (reserved)
[    0.000000]  modified: 0000000000001000 - 0000000000002000 (usable)
[    0.000000]  modified: 0000000000002000 - 0000000000010000 (reserved)
[    0.000000]  modified: 0000000000010000 - 000000000009f800 (usable)
[    0.000000]  modified: 000000000009f800 - 00000000000a0000 (reserved)
[    0.000000]  modified: 00000000000dc000 - 0000000000100000 (reserved)
[    0.000000]  modified: 0000000000100000 - 000000007f680000 (usable)
[    0.000000]  modified: 000000007f680000 - 000000007f700000 (ACPI NVS)
[    0.000000]  modified: 000000007f700000 - 0000000080000000 (reserved)
[    0.000000]  modified: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  modified: 00000000fec00000 - 00000000fec10000 (reserved)
[    0.000000]  modified: 00000000fed00000 - 00000000fed00400 (reserved)
[    0.000000]  modified: 00000000fed14000 - 00000000fed1a000 (reserved)
[    0.000000]  modified: 00000000fed1c000 - 00000000fed90000 (reserved)
[    0.000000]  modified: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  modified: 00000000ff000000 - 0000000100000000 (reserved)
[    0.000000] initial memory mapped : 0 - 00c00000
[    0.000000] found SMP MP-table at [c00f67e0] f67e0
[    0.000000] init_memory_mapping: 0000000000000000-00000000377fe000
[    0.000000]  0000000000 - 0000400000 page 4k
[    0.000000]  0000400000 - 0037400000 page 2M
[    0.000000]  0037400000 - 00377fe000 page 4k
[    0.000000] kernel direct mapping tables up to 377fe000 @ 15000-1a000
[    0.000000] RAMDISK: 37858000 - 37ff0000
[    0.000000] Allocated new RAMDISK: 00903000 - 0109a45d
[    0.000000] Move RAMDISK from 0000000037858000 - 0000000037fef45c to 00903000 - 0109a45c
[    0.000000] ACPI: RSDP 000f66f0 00024 (v03 HP    )
[    0.000000] ACPI: XSDT 7f683adc 00084 (v01 HPQOEM SLIC-MPC 06040000  LTP 00000000)
[    0.000000] ACPI: FACP 7f68cc2a 000F4 (v03 INTEL  CALISTGA 06040000 ALAN 00000001)
[    0.000000] ACPI: DSDT 7f6854be 076F8 (v01 HPQOEM SLIC-MPC 06040000 MSFT 03000000)
[    0.000000] ACPI: FACS 7f68dfc0 00040
[    0.000000] ACPI: APIC 7f68cd1e 00068 (v01 HPQOEM SLIC-MPC 06040000 LOHR 00000064)
[    0.000000] ACPI: HPET 7f68cd86 00038 (v01 HPQOEM SLIC-MPC 06040000 LOHR 00000064)
[    0.000000] ACPI: MCFG 7f68cdbe 0003C (v01 HPQOEM SLIC-MPC 06040000 LOHR 00000064)
[    0.000000] ACPI: SLIC 7f68cdfa 00176 (v01 HPQOEM SLIC-MPC 06040000 HPQ  00000001)
[    0.000000] ACPI: APIC 7f68cf70 00068 (v01 HPQOEM SLIC-MPC 06040000  LTP 00000000)
[    0.000000] ACPI: BOOT 7f68cfd8 00028 (v01 HPQOEM SLIC-MPC 06040000  LTP 00000001)
[    0.000000] ACPI: SSDT 7f684e6f 0064F (v01 HPQOEM SLIC-MPC 00001000 INTL 20050624)
[    0.000000] ACPI: SSDT 7f6847d3 0069C (v01 HPQOEM SLIC-MPC 00001000 INTL 20050624)
[    0.000000] ACPI: SSDT 7f6840ec 0025F (v01 HPQOEM SLIC-MPC 00003000 INTL 20050624)
[    0.000000] ACPI: SSDT 7f684046 000A6 (v01 HPQOEM SLIC-MPC 00003000 INTL 20050624)
[    0.000000] ACPI: SSDT 7f683b60 004E6 (v01 HPQOEM SLIC-MPC 00003000 INTL 20050624)
[    0.000000] ACPI: BIOS bug: multiple APIC/MADT found, using 0
[    0.000000] ACPI: If "acpi_apic_instance=2" works better, notify [email]linux-acpi@vger.kernel.org[/email]
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] 1150MB HIGHMEM available.
[    0.000000] 887MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 377fe000
[    0.000000]   low ram: 0 - 377fe000
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000001 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x000377fe
[    0.000000]   HighMem  0x000377fe -> 0x0007f680
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[3] active PFN ranges
[    0.000000]     0: 0x00000001 -> 0x00000002
[    0.000000]     0: 0x00000010 -> 0x0000009f
[    0.000000]     0: 0x00000100 -> 0x0007f680
[    0.000000] On node 0 totalpages: 521744
[    0.000000] free_area_init_node: node 0, pgdat c07aff00, node_mem_map c109c020
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3952 pages, LIFO batch:0
[    0.000000]   Normal zone: 1744 pages used for memmap
[    0.000000]   Normal zone: 221486 pages, LIFO batch:31
[    0.000000]   HighMem zone: 2302 pages used for memmap
[    0.000000]   HighMem zone: 292228 pages, LIFO batch:31
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
[    0.000000] nr_irqs_gsi: 40
[    0.000000] early_res array is doubled to 64 at [16000 - 167ff]
[    0.000000] PM: Registered nosave memory: 0000000000002000 - 0000000000010000
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000dc000
[    0.000000] PM: Registered nosave memory: 00000000000dc000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 80000000 (gap: 80000000:60000000)
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] setup_percpu: NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:2 nr_node_ids:1
[    0.000000] PERCPU: Embedded 14 pages/cpu @c2400000 s33024 r0 d24320 u2097152
[    0.000000] pcpu-alloc: s33024 r0 d24320 u2097152 alloc=1*4194304
[    0.000000] pcpu-alloc: [0] 0 1 
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 517666
[    0.000000] Kernel command line: BOOT_IMAGE=/vmlinuz-2.6.36.2 root=UUID=5a1be960-c3da-4778-8e6c-fbd3b5e03605 ro quiet splash clocksource=tsc
[    0.000000] PID hash table entries: 4096 (order: 2, 16384 bytes)
[    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] allocated 10437100 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] Subtract (53 early reservations)
[    0.000000]   #1 [0000001000 - 0000002000]   EX TRAMPOLINE
[    0.000000]   #2 [0000100000 - 00008fe324]   TEXT DATA BSS
[    0.000000]   #3 [00008ff000 - 000090210c]             BRK
[    0.000000]   #4 [00000f67f0 - 0000100000]   BIOS reserved
[    0.000000]   #5 [00000f67e0 - 00000f67f0]    MP-table mpf
[    0.000000]   #6 [000009f800 - 000009fd71]   BIOS reserved
[    0.000000]   #7 [000009ff05 - 00000f67e0]   BIOS reserved
[    0.000000]   #8 [000009fd71 - 000009ff05]    MP-table mpc
[    0.000000]   #9 [0000010000 - 0000011000]      TRAMPOLINE
[    0.000000]   #10 [0000011000 - 0000015000]     ACPI WAKEUP
[    0.000000]   #11 [0000015000 - 0000016000]         PGTABLE
[    0.000000]   #12 [0000903000 - 000109b000]     NEW RAMDISK
[    0.000000]   #13 [000109b000 - 000109c000]         BOOTMEM
[    0.000000]   #14 [000109c000 - 000208c000]         BOOTMEM
[    0.000000]   #15 [000208c000 - 000208c004]         BOOTMEM
[    0.000000]   #16 [000208c040 - 000208c100]         BOOTMEM
[    0.000000]   #17 [000208c100 - 000208c154]         BOOTMEM
[    0.000000]   #18 [000208c180 - 000208f180]         BOOTMEM
[    0.000000]   #19 [000208f180 - 000208f1ec]         BOOTMEM
[    0.000000]   #20 [000208f200 - 0002095200]         BOOTMEM
[    0.000000]   #21 [0002095200 - 0002095225]         BOOTMEM
[    0.000000]   #22 [0002095240 - 0002095267]         BOOTMEM
[    0.000000]   #23 [0002095280 - 0002095440]         BOOTMEM
[    0.000000]   #24 [0002095440 - 0002095480]         BOOTMEM
[    0.000000]   #25 [0002095480 - 00020954c0]         BOOTMEM
[    0.000000]   #26 [00020954c0 - 0002095500]         BOOTMEM
[    0.000000]   #27 [0002095500 - 0002095540]         BOOTMEM
[    0.000000]   #28 [0002095540 - 0002095580]         BOOTMEM
[    0.000000]   #29 [0002095580 - 00020955c0]         BOOTMEM
[    0.000000]   #30 [00020955c0 - 0002095600]         BOOTMEM
[    0.000000]   #31 [0002095600 - 0002095640]         BOOTMEM
[    0.000000]   #32 [0002095640 - 0002095680]         BOOTMEM
[    0.000000]   #33 [0002095680 - 00020956c0]         BOOTMEM
[    0.000000]   #34 [00020956c0 - 0002095700]         BOOTMEM
[    0.000000]   #35 [0002095700 - 0002095740]         BOOTMEM
[    0.000000]   #36 [0002095740 - 0002095780]         BOOTMEM
[    0.000000]   #37 [0002095780 - 0002095790]         BOOTMEM
[    0.000000]   #38 [00020957c0 - 00020957d0]         BOOTMEM
[    0.000000]   #39 [0002095800 - 000209586c]         BOOTMEM
[    0.000000]   #40 [0002095880 - 00020958ec]         BOOTMEM
[    0.000000]   #41 [0002400000 - 000240e000]         BOOTMEM
[    0.000000]   #42 [0002600000 - 000260e000]         BOOTMEM
[    0.000000]   #43 [0002097900 - 0002097904]         BOOTMEM
[    0.000000]   #44 [0002097940 - 0002097944]         BOOTMEM
[    0.000000]   #45 [0002097980 - 0002097988]         BOOTMEM
[    0.000000]   #46 [00020979c0 - 00020979c8]         BOOTMEM
[    0.000000]   #47 [0002097a00 - 0002097aa8]         BOOTMEM
[    0.000000]   #48 [0002097ac0 - 0002097b28]         BOOTMEM
[    0.000000]   #49 [0002097b40 - 000209bb40]         BOOTMEM
[    0.000000]   #50 [000209bb40 - 000211bb40]         BOOTMEM
[    0.000000]   #51 [000211bb40 - 000215bb40]         BOOTMEM
[    0.000000]   #52 [000260e000 - 00030021ec]         BOOTMEM
[    0.000000] Initializing HighMem for node 0 (000377fe:0007f680)
[    0.000000] Memory: 2043508k/2087424k available (4798k kernel code, 43468k reserved, 2093k data, 680k init, 1178120k highmem)
[    0.000000] virtual kernel memory layout:
[    0.000000]     fixmap  : 0xfff15000 - 0xfffff000   ( 936 kB)
[    0.000000]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[    0.000000]     vmalloc : 0xf7ffe000 - 0xff7fe000   ( 120 MB)
[    0.000000]     lowmem  : 0xc0000000 - 0xf77fe000   ( 887 MB)
[    0.000000]       .init : 0xc07bb000 - 0xc0865000   ( 680 kB)
[    0.000000]       .data : 0xc05af978 - 0xc07baf88   (2093 kB)
[    0.000000]       .text : 0xc0100000 - 0xc05af978   (4798 kB)
[    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.000000] SLUB: Genslabs=13, HWalign=64, Order=0-3, MinObjects=0, CPUs=2, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000]     RCU-based detection of stalled CPUs is disabled.
[    0.000000]     Verbose stalled-CPUs detection is disabled.
[    0.000000] NR_IRQS:2304 nr_irqs:512
[    0.000000] Extended CMOS year: 2000
[    0.000000] Console: colour VGA+ 80x25
[    0.000000] console [tty0] enabled
[    0.000000] hpet clockevent registered
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 1595.986 MHz processor.
[    0.004006] Calibrating delay loop (skipped), value calculated using timer frequency.. 3191.97 BogoMIPS (lpj=6383944)
[    0.004014] pid_max: default: 32768 minimum: 301
[    0.004038] Security Framework initialized
[    0.004062] AppArmor: AppArmor initialized
[    0.004073] Mount-cache hash table entries: 512
[    0.004248] Initializing cgroup subsys ns
[    0.004254] Initializing cgroup subsys cpuacct
[    0.004260] Initializing cgroup subsys memory
[    0.004274] Initializing cgroup subsys devices
[    0.004278] Initializing cgroup subsys freezer
[    0.004281] Initializing cgroup subsys net_cls
[    0.004316] CPU: Physical Processor ID: 0
[    0.004319] CPU: Processor Core ID: 0
[    0.004323] mce: CPU supports 6 MCE banks
[    0.004336] CPU0: Thermal monitoring enabled (TM2)
[    0.004341] using mwait in idle threads.
[    0.004350] Performance Events: Core events, core PMU driver.
[    0.004362] ... version:                1
[    0.004364] ... bit width:              40
[    0.004367] ... generic registers:      2
[    0.004370] ... value mask:             000000ffffffffff
[    0.004373] ... max period:             000000007fffffff
[    0.004375] ... fixed-purpose events:   0
[    0.004378] ... event mask:             0000000000000003
[    0.011952] ACPI: Core revision 20100702
[    0.024012] ftrace: converting mcount calls to 0f 1f 44 00 00
[    0.024019] ftrace: allocating 20181 entries in 40 pages
[    0.028070] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.032381] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.072079] CPU0: Genuine Intel(R) CPU           T2050  @ 1.60GHz stepping 08
[    0.076000] Booting Node   0, Processors  #1 Ok.
[    0.008000] Initializing CPU#1
[    0.164029] Brought up 2 CPUs
[    0.164034] Total of 2 processors activated (6383.97 BogoMIPS).
[    0.164684] devtmpfs: initialized
[    0.164684] regulator: core version 0.5
[    0.164684] Time: 11:00:54  Date: 02/15/11
[    0.164684] NET: Registered protocol family 16
[    0.168038] EISA bus registered
[    0.168049] ACPI: bus type pci registered
[    0.168141] PCI: MMCONFIG for domain 0000 [bus 00-ff] at [mem 0xe0000000-0xefffffff] (base 0xe0000000)
[    0.168146] PCI: MMCONFIG at [mem 0xe0000000-0xefffffff] reserved in E820
[    0.168149] PCI: Using MMCONFIG for extended config space
[    0.168152] PCI: Using configuration type 1 for base access
[    0.169325] bio: create slab <bio-0> at 0
[    0.169325] ACPI: EC: Look up EC in DSDT
[    0.173283] ACPI: BIOS _OSI(Linux) query ignored
[    0.175152] ACPI: SSDT 7f6844d9 0023D (v01  PmRef  Cpu0Ist 00003000 INTL 20050624)
[    0.175630] ACPI: Dynamic OEM Table Load:
[    0.175635] ACPI: SSDT (null) 0023D (v01  PmRef  Cpu0Ist 00003000 INTL 20050624)
[    0.175842] ACPI: SSDT 7f68434b 00109 (v01  PmRef  Cpu0Cst 00003001 INTL 20050624)
[    0.176302] ACPI: Dynamic OEM Table Load:
[    0.176307] ACPI: SSDT (null) 00109 (v01  PmRef  Cpu0Cst 00003001 INTL 20050624)
[    0.176789] ACPI: SSDT 7f684716 000BD (v01  PmRef  Cpu1Ist 00003000 INTL 20050624)
[    0.177255] ACPI: Dynamic OEM Table Load:
[    0.177260] ACPI: SSDT (null) 000BD (v01  PmRef  Cpu1Ist 00003000 INTL 20050624)
[    0.177443] ACPI: SSDT 7f684454 00085 (v01  PmRef  Cpu1Cst 00003000 INTL 20050624)
[    0.177897] ACPI: Dynamic OEM Table Load:
[    0.177902] ACPI: SSDT (null) 00085 (v01  PmRef  Cpu1Cst 00003000 INTL 20050624)
[    0.188207] ACPI: Interpreter enabled
[    0.188214] ACPI: (supports S0 S3 S4 S5)
[    0.188243] ACPI: Using IOAPIC for interrupt routing
[    0.192530] [Firmware Bug]: ACPI: No _BQC method, cannot determine initial brightness
[    0.192744] [Firmware Bug]: ACPI: No _BQC method, cannot determine initial brightness
[    0.205172] ACPI: EC: GPE = 0x17, I/O: command/status = 0x66, data = 0x62
[    0.205415] ACPI: No dock devices found.
[    0.205422] PCI: Ignoring host bridge windows from ACPI; if necessary, use "pci=use_crs" and report a bug
[    0.208890] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-ff])
[    0.210201] pci_root PNP0A08:00: host bridge window [io  0x0000-0x0cf7] (ignored)
[    0.210206] pci_root PNP0A08:00: host bridge window [io  0x0d00-0xffff] (ignored)
[    0.210210] pci_root PNP0A08:00: host bridge window [mem 0x000a0000-0x000bffff] (ignored)
[    0.210215] pci_root PNP0A08:00: host bridge window [mem 0x000d0000-0x000d3fff] (ignored)
[    0.210219] pci_root PNP0A08:00: host bridge window [mem 0x000d4000-0x000d7fff] (ignored)
[    0.210223] pci_root PNP0A08:00: host bridge window [mem 0x000d8000-0x000dbfff] (ignored)
[    0.210228] pci_root PNP0A08:00: host bridge window [mem 0x80000000-0xdfffffff] (ignored)
[    0.210232] pci_root PNP0A08:00: host bridge window [mem 0xf0000000-0xfebfffff] (ignored)
[    0.210315] pci 0000:00:02.0: reg 10: [mem 0xd4200000-0xd427ffff]
[    0.210324] pci 0000:00:02.0: reg 14: [io  0x1800-0x1807]
[    0.210333] pci 0000:00:02.0: reg 18: [mem 0xc0000000-0xcfffffff pref]
[    0.210342] pci 0000:00:02.0: reg 1c: [mem 0xd4300000-0xd433ffff]
[    0.210399] pci 0000:00:02.1: reg 10: [mem 0xd4280000-0xd42fffff]
[    0.210540] pci 0000:00:1b.0: reg 10: [mem 0xd4340000-0xd4343fff 64bit]
[    0.210634] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    0.210642] pci 0000:00:1b.0: PME# disabled
[    0.210767] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    0.210773] pci 0000:00:1c.0: PME# disabled
[    0.210903] pci 0000:00:1c.2: PME# supported from D0 D3hot D3cold
[    0.210909] pci 0000:00:1c.2: PME# disabled
[    0.211038] pci 0000:00:1c.3: PME# supported from D0 D3hot D3cold
[    0.211044] pci 0000:00:1c.3: PME# disabled
[    0.211140] pci 0000:00:1d.0: reg 20: [io  0x1820-0x183f]
[    0.211242] pci 0000:00:1d.1: reg 20: [io  0x1840-0x185f]
[    0.211345] pci 0000:00:1d.2: reg 20: [io  0x1860-0x187f]
[    0.211447] pci 0000:00:1d.3: reg 20: [io  0x1880-0x189f]
[    0.211529] pci 0000:00:1d.7: reg 10: [mem 0xd4544000-0xd45443ff]
[    0.211627] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
[    0.211634] pci 0000:00:1d.7: PME# disabled
[    0.211868] pci 0000:00:1f.0: quirk: [io  0x1000-0x107f] claimed by ICH6 ACPI/GPIO/TCO
[    0.211874] pci 0000:00:1f.0: quirk: [io  0x1180-0x11bf] claimed by ICH6 GPIO
[    0.211880] pci 0000:00:1f.0: ICH7 LPC Generic IO decode 1 PIO at 0680 (mask 007f)
[    0.211887] pci 0000:00:1f.0: ICH7 LPC Generic IO decode 2 PIO at 1200 (mask 0007)
[    0.211955] pci 0000:00:1f.1: reg 10: [io  0x0000-0x0007]
[    0.211969] pci 0000:00:1f.1: reg 14: [io  0x0000-0x0003]
[    0.211984] pci 0000:00:1f.1: reg 18: [io  0x0000-0x0007]
[    0.212005] pci 0000:00:1f.1: reg 1c: [io  0x0000-0x0003]
[    0.212019] pci 0000:00:1f.1: reg 20: [io  0x1810-0x181f]
[    0.212091] pci 0000:00:1f.2: reg 10: [io  0x18d0-0x18d7]
[    0.212106] pci 0000:00:1f.2: reg 14: [io  0x18c4-0x18c7]
[    0.212120] pci 0000:00:1f.2: reg 18: [io  0x18c8-0x18cf]
[    0.212134] pci 0000:00:1f.2: reg 1c: [io  0x18c0-0x18c3]
[    0.212149] pci 0000:00:1f.2: reg 20: [io  0x18b0-0x18bf]
[    0.212163] pci 0000:00:1f.2: reg 24: [mem 0xd4544400-0xd45447ff]
[    0.212202] pci 0000:00:1f.2: PME# supported from D3hot
[    0.212208] pci 0000:00:1f.2: PME# disabled
[    0.212304] pci 0000:00:1f.3: reg 20: [io  0x18e0-0x18ff]
[    0.212421] pci 0000:00:1c.0: PCI bridge to [bus 02-03]
[    0.212428] pci 0000:00:1c.0:   bridge window [io  0x2000-0x2fff]
[    0.212435] pci 0000:00:1c.0:   bridge window [mem 0xd2000000-0xd3ffffff]
[    0.212445] pci 0000:00:1c.0:   bridge window [mem 0xd0000000-0xd1ffffff 64bit pref]
[    0.212514] pci 0000:00:1c.2: PCI bridge to [bus 04-04]
[    0.212521] pci 0000:00:1c.2:   bridge window [io  0xf000-0x0000] (disabled)
[    0.212528] pci 0000:00:1c.2:   bridge window [mem 0xfff00000-0x000fffff] (disabled)
[    0.212539] pci 0000:00:1c.2:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    0.212764] pci 0000:05:00.0: reg 10: [mem 0xd4000000-0xd4000fff]
[    0.213124] pci 0000:05:00.0: PME# supported from D0 D3hot D3cold
[    0.213138] pci 0000:05:00.0: PME# disabled
[    0.213212] pci 0000:05:00.0: disabling ASPM on pre-1.1 PCIe device.  You can enable it with 'pcie_aspm=force'
[    0.213243] pci 0000:00:1c.3: PCI bridge to [bus 05-05]
[    0.213250] pci 0000:00:1c.3:   bridge window [io  0xf000-0x0000] (disabled)
[    0.213257] pci 0000:00:1c.3:   bridge window [mem 0xd4000000-0xd40fffff]
[    0.213267] pci 0000:00:1c.3:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    0.213354] pci 0000:08:08.0: reg 10: [mem 0xd4100000-0xd4100fff]
[    0.213368] pci 0000:08:08.0: reg 14: [io  0x3000-0x303f]
[    0.213449] pci 0000:08:08.0: supports D1 D2
[    0.213452] pci 0000:08:08.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.213459] pci 0000:08:08.0: PME# disabled
[    0.213506] pci 0000:08:09.0: reg 10: [mem 0xd4101000-0xd41017ff]
[    0.213601] pci 0000:08:09.0: supports D1 D2
[    0.213604] pci 0000:08:09.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.213611] pci 0000:08:09.0: PME# disabled
[    0.213657] pci 0000:08:09.1: reg 10: [mem 0xd4101800-0xd41018ff]
[    0.213753] pci 0000:08:09.1: supports D1 D2
[    0.213757] pci 0000:08:09.1: PME# supported from D0 D1 D2 D3hot D3cold
[    0.213764] pci 0000:08:09.1: PME# disabled
[    0.213810] pci 0000:08:09.2: reg 10: [mem 0xd4101c00-0xd4101cff]
[    0.213903] pci 0000:08:09.2: supports D1 D2
[    0.213907] pci 0000:08:09.2: PME# supported from D0 D1 D2 D3hot D3cold
[    0.213914] pci 0000:08:09.2: PME# disabled
[    0.213961] pci 0000:08:09.3: reg 10: [mem 0xd4102000-0xd41020ff]
[    0.214056] pci 0000:08:09.3: supports D1 D2
[    0.214060] pci 0000:08:09.3: PME# supported from D0 D1 D2 D3hot D3cold
[    0.214066] pci 0000:08:09.3: PME# disabled
[    0.214127] pci 0000:00:1e.0: PCI bridge to [bus 08-08] (subtractive decode)
[    0.214134] pci 0000:00:1e.0:   bridge window [io  0x3000-0x3fff]
[    0.214141] pci 0000:00:1e.0:   bridge window [mem 0xd4100000-0xd41fffff]
[    0.214151] pci 0000:00:1e.0:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    0.214155] pci 0000:00:1e.0:   bridge window [io  0x0000-0xffff] (subtractive decode)
[    0.214159] pci 0000:00:1e.0:   bridge window [mem 0x00000000-0xffffffff] (subtractive decode)
[    0.214190] pci_bus 0000:00: on NUMA node 0
[    0.214195] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.214465] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP01._PRT]
[    0.214553] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP03._PRT]
[    0.214638] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP04._PRT]
[    0.214748] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCIB._PRT]
[    0.220469] ACPI: PCI Interrupt Link [LNKA] (IRQs 1 3 4 5 6 7 10 12 14 15) *11
[    0.220563] ACPI: PCI Interrupt Link [LNKB] (IRQs 1 3 4 5 6 7 11 12 14 15) *10
[    0.220651] ACPI: PCI Interrupt Link [LNKC] (IRQs 1 3 4 5 6 7 *10 12 14 15)
[    0.220741] ACPI: PCI Interrupt Link [LNKD] (IRQs 1 3 4 5 6 7 11 12 14 15) *10
[    0.220830] ACPI: PCI Interrupt Link [LNKE] (IRQs 1 3 4 5 6 7 *10 12 14 15)
[    0.220920] ACPI: PCI Interrupt Link [LNKF] (IRQs 1 3 4 5 6 7 11 12 14 15) *10
[    0.221009] ACPI: PCI Interrupt Link [LNKG] (IRQs 1 3 4 5 6 7 10 12 14 15) *11
[    0.221099] ACPI: PCI Interrupt Link [LNKH] (IRQs 1 3 4 5 6 7 *11 12 14 15)
[    0.221215] vgaarb: device added: PCI:0000:00:02.0,decodes=io+mem,owns=io+mem,locks=none
[    0.221236] vgaarb: loaded
[    0.221374] SCSI subsystem initialized
[    0.221387] libata version 3.00 loaded.
[    0.221387] usbcore: registered new interface driver usbfs
[    0.221387] usbcore: registered new interface driver hub
[    0.221387] usbcore: registered new device driver usb
[    0.221387] ACPI: WMI: Mapper loaded
[    0.221387] PCI: Using ACPI for IRQ routing
[    0.221387] PCI: pci_cache_line_size set to 64 bytes
[    0.221387] reserve RAM buffer: 0000000000002000 - 000000000000ffff 
[    0.221387] reserve RAM buffer: 000000000009f800 - 000000000009ffff 
[    0.221387] reserve RAM buffer: 000000007f680000 - 000000007fffffff 
[    0.221387] NetLabel: Initializing
[    0.221387] NetLabel:  domain hash size = 128
[    0.221387] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.221387] NetLabel:  unlabeled traffic allowed by default
[    0.221387] HPET: 3 timers in total, 0 timers will be used for per-cpu timer
[    0.221387] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[    0.221387] hpet0: 3 comparators, 64-bit 14.318180 MHz counter
[    0.228026] Switching to clocksource tsc
[    0.230232] AppArmor: AppArmor Filesystem Enabled
[    0.230244] pnp: PnP ACPI init
[    0.230259] ACPI: bus type pnp registered
[    0.233229] pnp: PnP ACPI: found 11 devices
[    0.233233] ACPI: ACPI bus type pnp unregistered
[    0.233237] PnPBIOS: Disabled by ACPI PNP
[    0.233252] system 00:01: [mem 0xe0000000-0xefffffff] has been reserved
[    0.233257] system 00:01: [mem 0xfed14000-0xfed17fff] has been reserved
[    0.233261] system 00:01: [mem 0xfed18000-0xfed18fff] has been reserved
[    0.233266] system 00:01: [mem 0xfed19000-0xfed19fff] has been reserved
[    0.233270] system 00:01: [mem 0xfed1c000-0xfed1ffff] has been reserved
[    0.233275] system 00:01: [mem 0xfed20000-0xfed3ffff] has been reserved
[    0.233279] system 00:01: [mem 0xfed40000-0xfed44fff] has been reserved
[    0.233283] system 00:01: [mem 0xfed45000-0xfed8ffff] has been reserved
[    0.233293] system 00:06: [io  0x0800-0x080f] has been reserved
[    0.233297] system 00:06: [io  0x1000-0x107f] has been reserved
[    0.233302] system 00:06: [io  0x1180-0x11bf] has been reserved
[    0.233306] system 00:06: [io  0x1200-0x120f] has been reserved
[    0.233313] system 00:07: [io  0x06a0-0x06af] has been reserved
[    0.233317] system 00:07: [io  0x06b0-0x06ff] has been reserved
[    0.270013] pci 0000:00:1c.2: BAR 14: assigned [mem 0x80000000-0x801fffff]
[    0.270019] pci 0000:00:1c.2: BAR 15: assigned [mem 0x80200000-0x803fffff 64bit pref]
[    0.270025] pci 0000:00:1c.3: BAR 15: assigned [mem 0x80400000-0x805fffff 64bit pref]
[    0.270030] pci 0000:00:1c.2: BAR 13: assigned [io  0x4000-0x4fff]
[    0.270035] pci 0000:00:1c.3: BAR 13: assigned [io  0x5000-0x5fff]
[    0.270039] pci 0000:00:1c.0: PCI bridge to [bus 02-03]
[    0.270046] pci 0000:00:1c.0:   bridge window [io  0x2000-0x2fff]
[    0.270055] pci 0000:00:1c.0:   bridge window [mem 0xd2000000-0xd3ffffff]
[    0.270062] pci 0000:00:1c.0:   bridge window [mem 0xd0000000-0xd1ffffff 64bit pref]
[    0.270072] pci 0000:00:1c.2: PCI bridge to [bus 04-04]
[    0.270078] pci 0000:00:1c.2:   bridge window [io  0x4000-0x4fff]
[    0.270086] pci 0000:00:1c.2:   bridge window [mem 0x80000000-0x801fffff]
[    0.270093] pci 0000:00:1c.2:   bridge window [mem 0x80200000-0x803fffff 64bit pref]
[    0.270104] pci 0000:00:1c.3: PCI bridge to [bus 05-05]
[    0.270109] pci 0000:00:1c.3:   bridge window [io  0x5000-0x5fff]
[    0.270117] pci 0000:00:1c.3:   bridge window [mem 0xd4000000-0xd40fffff]
[    0.270125] pci 0000:00:1c.3:   bridge window [mem 0x80400000-0x805fffff 64bit pref]
[    0.270136] pci 0000:00:1e.0: PCI bridge to [bus 08-08]
[    0.270141] pci 0000:00:1e.0:   bridge window [io  0x3000-0x3fff]
[    0.270150] pci 0000:00:1e.0:   bridge window [mem 0xd4100000-0xd41fffff]
[    0.270156] pci 0000:00:1e.0:   bridge window [mem pref disabled]
[    0.270178]   alloc irq_desc for 17 on node -1
[    0.270181]   alloc kstat_irqs on node -1
[    0.270188] pci 0000:00:1c.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    0.270196] pci 0000:00:1c.0: setting latency timer to 64
[    0.270209]   alloc irq_desc for 18 on node -1
[    0.270212]   alloc kstat_irqs on node -1
[    0.270217] pci 0000:00:1c.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.270224] pci 0000:00:1c.2: setting latency timer to 64
[    0.270236]   alloc irq_desc for 19 on node -1
[    0.270239]   alloc kstat_irqs on node -1
[    0.270244] pci 0000:00:1c.3: PCI INT D -> GSI 19 (level, low) -> IRQ 19
[    0.270251] pci 0000:00:1c.3: setting latency timer to 64
[    0.270262] pci 0000:00:1e.0: setting latency timer to 64
[    0.270267] pci_bus 0000:00: resource 0 [io  0x0000-0xffff]
[    0.270271] pci_bus 0000:00: resource 1 [mem 0x00000000-0xffffffff]
[    0.270276] pci_bus 0000:02: resource 0 [io  0x2000-0x2fff]
[    0.270279] pci_bus 0000:02: resource 1 [mem 0xd2000000-0xd3ffffff]
[    0.270283] pci_bus 0000:02: resource 2 [mem 0xd0000000-0xd1ffffff 64bit pref]
[    0.270287] pci_bus 0000:04: resource 0 [io  0x4000-0x4fff]
[    0.270291] pci_bus 0000:04: resource 1 [mem 0x80000000-0x801fffff]
[    0.270295] pci_bus 0000:04: resource 2 [mem 0x80200000-0x803fffff 64bit pref]
[    0.270299] pci_bus 0000:05: resource 0 [io  0x5000-0x5fff]
[    0.270303] pci_bus 0000:05: resource 1 [mem 0xd4000000-0xd40fffff]
[    0.270307] pci_bus 0000:05: resource 2 [mem 0x80400000-0x805fffff 64bit pref]
[    0.270311] pci_bus 0000:08: resource 0 [io  0x3000-0x3fff]
[    0.270315] pci_bus 0000:08: resource 1 [mem 0xd4100000-0xd41fffff]
[    0.270319] pci_bus 0000:08: resource 4 [io  0x0000-0xffff]
[    0.270323] pci_bus 0000:08: resource 5 [mem 0x00000000-0xffffffff]
[    0.270369] NET: Registered protocol family 2
[    0.270454] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.270769] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.271576] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.271985] TCP: Hash tables configured (established 131072 bind 65536)
[    0.271989] TCP reno registered
[    0.271993] UDP hash table entries: 512 (order: 2, 16384 bytes)
[    0.272009] UDP-Lite hash table entries: 512 (order: 2, 16384 bytes)
[    0.272139] NET: Registered protocol family 1
[    0.272169] pci 0000:00:02.0: Boot video device
[    0.272334] pci 0000:08:08.0: Firmware left e100 interrupts enabled; disabling
[    0.272352] PCI: CLS 64 bytes, default 64
[    0.272428] Trying to unpack rootfs image as initramfs...
[    0.554706] Freeing initrd memory: 7776k freed
[    0.560455] Simple Boot Flag at 0x36 set to 0x1
[    0.560757] cpufreq-nforce2: No nForce2 chipset.
[    0.560799] Scanning for low memory corruption every 60 seconds
[    0.561046] audit: initializing netlink socket (disabled)
[    0.561064] type=2000 audit(1297767654.556:1): initialized
[    0.574743] highmem bounce pool size: 64 pages
[    0.574752] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    0.576864] VFS: Disk quotas dquot_6.5.2
[    0.576950] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.577783] fuse init (API version 7.15)
[    0.577909] msgmni has been set to 1705
[    0.578218] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.578222] io scheduler noop registered
[    0.578225] io scheduler deadline registered
[    0.578243] io scheduler cfq registered (default)
[    0.579222] pcieport 0000:00:1c.0: ACPI _OSC control granted for 0x18
[    0.579239] pcieport 0000:00:1c.0: setting latency timer to 64
[    0.579295]   alloc irq_desc for 40 on node -1
[    0.579298]   alloc kstat_irqs on node -1
[    0.579314] pcieport 0000:00:1c.0: irq 40 for MSI/MSI-X
[    0.580168] pcieport 0000:00:1c.2: ACPI _OSC control granted for 0x18
[    0.580181] pcieport 0000:00:1c.2: setting latency timer to 64
[    0.580232]   alloc irq_desc for 41 on node -1
[    0.580235]   alloc kstat_irqs on node -1
[    0.580246] pcieport 0000:00:1c.2: irq 41 for MSI/MSI-X
[    0.581103] pcieport 0000:00:1c.3: ACPI _OSC control granted for 0x18
[    0.581116] pcieport 0000:00:1c.3: setting latency timer to 64
[    0.581169]   alloc irq_desc for 42 on node -1
[    0.581171]   alloc kstat_irqs on node -1
[    0.581182] pcieport 0000:00:1c.3: irq 42 for MSI/MSI-X
[    0.581307] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.581340] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.582242] ACPI: AC Adapter [ADP1] (on-line)
[    0.582349] input: Lid Switch as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0D:00/input/input0
[    0.583941] ACPI: Lid Switch [LID0]
[    0.584002] input: Sleep Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0E:00/input/input1
[    0.584009] ACPI: Sleep Button [SLPB]
[    0.584070] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input2
[    0.584075] ACPI: Power Button [PWRB]
[    0.584152] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input3
[    0.584157] ACPI: Power Button [PWRF]
[    0.584376] ACPI: acpi_idle registered with cpuidle
[    0.587371] Marking TSC unstable due to TSC halts in idle
[    0.601915] thermal LNXTHERM:01: registered as thermal_zone0
[    0.601929] ACPI: Thermal Zone [TZS0] (50 C)
[    0.607013] thermal LNXTHERM:02: registered as thermal_zone1
[    0.607027] ACPI: Thermal Zone [TZS1] (51 C)
[    0.607151] isapnp: Scanning for PnP cards...
[    0.611611] ACPI: EC: GPE storm detected, transactions will use polling mode
[    0.961288] isapnp: No Plug & Play device found
[    0.961559] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    0.963655] brd: module loaded
[    0.964421] loop: module loaded
[    0.964610] ata_piix 0000:00:1f.1: version 2.13
[    0.964628] ata_piix 0000:00:1f.1: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    0.964680] ata_piix 0000:00:1f.1: setting latency timer to 64
[    0.964781] scsi0 : ata_piix
[    0.964899] scsi1 : ata_piix
[    0.965483] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0x1810 irq 14
[    0.965487] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x1818 irq 15
[    0.965519]   alloc irq_desc for 20 on node -1
[    0.965522]   alloc kstat_irqs on node -1
[    0.965531] ata_piix 0000:00:1f.2: PCI INT B -> GSI 20 (level, low) -> IRQ 20
[    0.965539] ata_piix 0000:00:1f.2: MAP [ P0 P2 -- -- ]
[    0.965596] ata2: port disabled. ignoring.
[    1.119518] ata_piix 0000:00:1f.2: setting latency timer to 64
[    1.119597] scsi2 : ata_piix
[    1.119684] scsi3 : ata_piix
[    1.120673] ata3: SATA max UDMA/133 cmd 0x18d0 ctl 0x18c4 bmdma 0x18b0 irq 20
[    1.120678] ata4: SATA max UDMA/133 cmd 0x18c8 ctl 0x18c0 bmdma 0x18b8 irq 20
[    1.121164] Fixed MDIO Bus: probed
[    1.121210] PPP generic driver version 2.4.2
[    1.121263] tun: Universal TUN/TAP device driver, 1.6
[    1.121266] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    1.121378] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    1.121404]   alloc irq_desc for 23 on node -1
[    1.121407]   alloc kstat_irqs on node -1
[    1.121414] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    1.121429] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    1.121434] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    1.121479] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 1
[    1.121509] ehci_hcd 0000:00:1d.7: using broken periodic workaround
[    1.121524] ehci_hcd 0000:00:1d.7: debug port 1
[    1.125419] ehci_hcd 0000:00:1d.7: cache line size of 64 is not supported
[    1.125438] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xd4544000
[    1.129829] ata1.00: ATAPI: MATSHITADVD-RAM UJ-840S, 1.11, max MWDMA2
[    1.139405] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    1.139607] hub 1-0:1.0: USB hub found
[    1.139614] hub 1-0:1.0: 8 ports detected
[    1.139725] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    1.139744] uhci_hcd: USB Universal Host Controller Interface driver
[    1.139777] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    1.139786] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    1.139791] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    1.139843] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    1.139875] uhci_hcd 0000:00:1d.0: irq 23, io base 0x00001820
[    1.140037] hub 2-0:1.0: USB hub found
[    1.140043] hub 2-0:1.0: 2 ports detected
[    1.140134] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    1.140143] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    1.140148] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    1.140190] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 3
[    1.140233] uhci_hcd 0000:00:1d.1: irq 19, io base 0x00001840
[    1.140398] hub 3-0:1.0: USB hub found
[    1.140404] hub 3-0:1.0: 2 ports detected
[    1.140485]   alloc irq_desc for 21 on node -1
[    1.140488]   alloc kstat_irqs on node -1
[    1.140496] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 21 (level, low) -> IRQ 21
[    1.140504] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    1.140509] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    1.140556] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 4
[    1.140603] uhci_hcd 0000:00:1d.2: irq 21, io base 0x00001860
[    1.140763] hub 4-0:1.0: USB hub found
[    1.140769] hub 4-0:1.0: 2 ports detected
[    1.140853]   alloc irq_desc for 16 on node -1
[    1.140856]   alloc kstat_irqs on node -1
[    1.140862] uhci_hcd 0000:00:1d.3: PCI INT D -> GSI 16 (level, low) -> IRQ 16
[    1.140871] uhci_hcd 0000:00:1d.3: setting latency timer to 64
[    1.140876] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[    1.140919] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 5
[    1.140961] uhci_hcd 0000:00:1d.3: irq 16, io base 0x00001880
[    1.141119] hub 5-0:1.0: USB hub found
[    1.141127] hub 5-0:1.0: 2 ports detected
[    1.141295] PNP: PS/2 Controller [PNP0303:KBD0,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    1.141655] i8042.c: Detected active multiplexing controller, rev 1.1.
[    1.141742] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.141753] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[    1.141757] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[    1.141761] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[    1.141766] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[    1.141870] mice: PS/2 mouse device common for all mice
[    1.142075] rtc_cmos 00:08: RTC can wake from S4
[    1.142128] rtc_cmos 00:08: rtc core: registered rtc_cmos as rtc0
[    1.142164] rtc0: alarms up to one month, y3k, 242 bytes nvram, hpet irqs
[    1.142311] device-mapper: uevent: version 1.0.3
[    1.142463] device-mapper: ioctl: 4.18.0-ioctl (2010-06-29) initialised: [email]dm-devel@redhat.com[/email]
[    1.142555] device-mapper: multipath: version 1.1.1 loaded
[    1.142559] device-mapper: multipath round-robin: version 1.0.0 loaded
[    1.142730] EISA: Probing bus 0 at eisa.0
[    1.142738] Cannot allocate resource for EISA slot 1
[    1.142742] Cannot allocate resource for EISA slot 2
[    1.142745] Cannot allocate resource for EISA slot 3
[    1.142748] Cannot allocate resource for EISA slot 4
[    1.142751] Cannot allocate resource for EISA slot 5
[    1.142768] EISA: Detected 0 cards.
[    1.142949] cpuidle: using governor ladder
[    1.143111] cpuidle: using governor menu
[    1.143867] ata1.00: configured for MWDMA2
[    1.143951] TCP cubic registered
[    1.144129] NET: Registered protocol family 10
[    1.144606] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input4
[    1.144693] lo: Disabled Privacy Extensions
[    1.145055] NET: Registered protocol family 17
[    1.145076] Registering the dns_resolver key type
[    1.227505] Using IPI No-Shortcut mode
[    1.227604] PM: Resume from disk failed.
[    1.227618] registered taskstats version 1
[    1.228020]   Magic number: 15:228:24
[    1.228025] misc cpu_dma_latency: hash matches
[    1.228128] rtc_cmos 00:08: setting system clock to 2011-02-15 11:00:55 UTC (1297767655)
[    1.228133] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.228135] EDD information not available.
[    1.271571] ACPI: Battery Slot [BAT0] (battery present)
[    1.273483] scsi 0:0:0:0: CD-ROM            MATSHITA DVD-RAM UJ-840S  1.11 PQ: 0 ANSI: 5
[    1.277991] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[    1.277995] cdrom: Uniform CD-ROM driver Revision: 3.20
[    1.278127] sr 0:0:0:0: Attached scsi CD-ROM sr0
[    1.278205] sr 0:0:0:0: Attached scsi generic sg0 type 5
[    1.339592] ata3.00: ATA-7: WDC WD600BEVS-60LAT0, 01.06M01, max UDMA/100
[    1.339597] ata3.00: 117231408 sectors, multi 16: LBA48 
[    1.355587] ata3.00: configured for UDMA/100
[    1.355722] scsi 2:0:0:0: Direct-Access     ATA      WDC WD600BEVS-60 01.0 PQ: 0 ANSI: 5
[    1.355876] sd 2:0:0:0: [sda] 117231408 512-byte logical blocks: (60.0 GB/55.8 GiB)
[    1.355889] sd 2:0:0:0: Attached scsi generic sg1 type 0
[    1.355977] sd 2:0:0:0: [sda] Write Protect is off
[    1.355981] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.356034] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.453506]  sda: sda1 sda2 < sda5 sda6 sda7 sda8 >
[    1.454068] sd 2:0:0:0: [sda] Attached SCSI disk
[    1.454094] Freeing unused kernel memory: 680k freed
[    1.454609] Write protecting the kernel text: 4800k
[    1.454673] Write protecting the kernel read-only data: 1832k
[    1.474267] udev: starting version 151
[    1.474317] udevd (73): /proc/73/oom_adj is deprecated, please use /proc/73/oom_score_adj instead.
[    1.875410] usb 4-2: new full speed USB device using uhci_hcd and address 2
[    2.426961] EXT4-fs (sda8): mounted filesystem with ordered data mode. Opts: (null)
[   18.472733] udev: starting version 151
[   18.578674] Adding 3905532k swap on /dev/sda7.  Priority:-1 extents:1 across:3905532k 
[   18.969150] apparmor_parser[596]: segfault at 0 ip b7627198 sp bfcb44dc error 4 in libc-2.11.1.so[b75b4000+153000]
[   19.043859] [Firmware Bug]: ACPI: No _BQC method, cannot determine initial brightness
[   19.049756] intel_rng: FWH not detected
[   19.095375] lp: driver loaded but no devices found
[   19.167453] acpi device:07: registered as cooling_device2
[   19.167616] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/LNXVIDEO:01/input/input5
[   19.167703] ACPI: Video Device [GFX0] (multi-head: yes  rom: no  post: no)
[   19.485128] Linux agpgart interface v0.103
[   19.554884] input: HP WMI hotkeys as /devices/virtual/input/input6
[   19.639351] Bluetooth: Core ver 2.15
[   19.639415] NET: Registered protocol family 31
[   19.639418] Bluetooth: HCI device and connection manager initialized
[   19.639422] Bluetooth: HCI socket layer initialized
[   19.743636] e100: Intel(R) PRO/100 Network Driver, 3.5.24-k2-NAPI
[   19.743642] e100: Copyright(c) 1999-2006 Intel Corporation
[   19.743716] e100 0000:08:08.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[   19.770615] e100 0000:08:08.0: PME# disabled
[   19.771371] e100 0000:08:08.0: eth0: addr 0xd4100000, irq 20, MAC addr 00:16:d3:0b:18:9c
[   19.846801] sdhci: Secure Digital Host Controller Interface driver
[   19.846806] sdhci: Copyright(c) Pierre Ossman
[   19.910630] sdhci-pci 0000:08:09.1: SDHCI controller found [1180:0822] (rev 19)
[   19.910655] sdhci-pci 0000:08:09.1: PCI INT B -> GSI 18 (level, low) -> IRQ 18
[   19.911691] sdhci-pci 0000:08:09.1: Will use DMA mode even though HW doesn't fully claim to support it.
[   19.911726] mmc0: no vmmc regulator found
[   19.912835] Registered led device: mmc0::
[   19.913954] mmc0: SDHCI controller on PCI [0000:08:09.1] using DMA
[   20.005156] agpgart-intel 0000:00:00.0: Intel 945GM Chipset
[   20.006158] agpgart-intel 0000:00:00.0: detected 7932K stolen memory
[   20.009780] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0xc0000000
[   20.035567] Bluetooth: Generic Bluetooth USB driver ver 0.6
[   20.035804] usbcore: registered new interface driver btusb
[   20.103084] cfg80211: Calling CRDA to update world regulatory domain
[   20.145738] cfg80211: World regulatory domain updated:
[   20.145743]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   20.145748]     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   20.145752]     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   20.145757]     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   20.145761]     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   20.145765]     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   20.369934] ohci1394 0000:08:09.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   20.425354] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[16]  MMIO=[d4101000-d41017ff]  Max Packet=[2048]  IR/IT contexts=[4/4]
[   21.058251] Synaptics Touchpad, model: 1, fw: 6.2, id: 0x1a0b1, caps: 0xa04713/0x200000/0x0
[   21.088049] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio4/input/input7
[   21.413575] [drm] Initialized drm 1.1.0 20060810
[   21.699564] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[06e40a007e395034]
[   22.901587] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, in-tree:s
[   22.901593] iwl3945: Copyright(c) 2003-2010 Intel Corporation
[   22.901705] iwl3945 0000:05:00.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[   22.901723] iwl3945 0000:05:00.0: setting latency timer to 64
[   22.942303] iwl3945 0000:05:00.0: Tunable channels: 11 802.11bg, 13 802.11a channels
[   22.942310] iwl3945 0000:05:00.0: Detected Intel Wireless WiFi Link 3945ABG
[   22.942430]   alloc irq_desc for 43 on node -1
[   22.942433]   alloc kstat_irqs on node -1
[   22.942471] iwl3945 0000:05:00.0: irq 43 for MSI/MSI-X
[   22.984769] i915 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   22.984777] i915 0000:00:02.0: setting latency timer to 64
[   22.988345] [drm] set up 7M of stolen space
[   23.094941] vgaarb: device changed decodes: PCI:0000:00:02.0,olddecodes=io+mem,decodes=io+mem:owns=io+mem
[   23.095565] [drm] initialized overlay support
[   23.464515] phy0: Selected rate control algorithm 'iwl-3945-rs'
[   23.717421] fb0: inteldrmfb frame buffer device
[   23.717426] drm: registered panic notifier
[   23.717443] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
[   23.717504]   alloc irq_desc for 22 on node -1
[   23.717507]   alloc kstat_irqs on node -1
[   23.717519] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[   23.717581]   alloc irq_desc for 44 on node -1
[   23.717583]   alloc kstat_irqs on node -1
[   23.717598] HDA Intel 0000:00:1b.0: irq 44 for MSI/MSI-X
[   23.717640] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   24.378029] Console: switching to colour frame buffer device 160x50
[   24.407679] EXT4-fs (sda8): re-mounted. Opts: errors=remount-ro
[   24.693985] EXT4-fs (sda6): mounted filesystem with ordered data mode. Opts: (null)
[   24.814187] apparmor_parser[792]: segfault at 0 ip b77a4198 sp bfc6befc error 4 in libc-2.11.1.so[b7731000+153000]
[   24.871231] iwl3945 0000:05:00.0: loaded firmware version 15.32.2.9
[   24.940570] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   25.059842] apparmor_parser[818]: segfault at 0 ip 08050ce1 sp bfc3a7c0 error 4 in apparmor_parser[8048000+bd000]
[   25.172549] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   25.175460] e100 0000:08:08.0: eth0: NIC Link is Up 100 Mbps Full Duplex
[   25.177041] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   25.608931] ppdev: user-space parallel port driver
[   25.705187] Bluetooth: L2CAP ver 2.15
[   25.705192] Bluetooth: L2CAP socket layer initialized
[   25.883416] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   25.883421] Bluetooth: BNEP filters: protocol multicast
[   26.107853] Bridge firewalling registered
[   26.185498] Bluetooth: SCO (Voice Link) ver 0.6
[   26.185502] Bluetooth: SCO socket layer initialized
[   26.333991] Bluetooth: RFCOMM TTY layer initialized
[   26.334000] Bluetooth: RFCOMM socket layer initialized
[   26.334002] Bluetooth: RFCOMM ver 1.11
[   35.035275] atkbd serio0: Unknown key pressed (translated set 2, code 0xd9 on isa0060/serio0).
[   35.035281] atkbd serio0: Use 'setkeycodes e059 <keycode>' to make it known.
[   35.037617] atkbd serio0: Unknown key released (translated set 2, code 0xd9 on isa0060/serio0).
[   35.037622] atkbd serio0: Use 'setkeycodes e059 <keycode>' to make it known.

---

### Post by Brandon Williams on 2011-02-16
tsc is known to be unstable as a clock source and should be avoided, especially on multi-core machines. You can make it a bit more stable by disabling CPU throttling, but I don't recommend it. Even if you disable CPU throttling, tsc will drift ... it just won't drift as fast or show significant differences between CPU cores.

---

