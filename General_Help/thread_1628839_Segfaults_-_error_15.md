---
title: "Segfaults - error 15"
date: 2010-11-23
forum: General Help
---

### Post by winnie on 2010-11-23
Hi all,
 I need urgent help. I use Ubuntu Server 10.04, and it was running well for a while, but yesterday some functions stopped working. Apache and mythbackend runs ok (I've tested it from another computer's browser and mythfrontend), but I cannot login at all. If I type my username and password I can see my init script is running, then I get a Sebmentation fault, and get the login promt again. I've also tried logging in in recovery mode, same result.
 Using a live cd I managed to mount the partition and checked the /var/log/syslog file. I found there a lot of segfaults with "error 15 in grep" and "error 15 in bash" during the booting.
 Just to be sure that nothing is wrong with the hardware I also ran fsck and memtest86+, both of the HDD and memories are ok. 
 Please help me if you have any ideas on how to fix this. I spent a whole day for googling any solution, no results so far  :(
Thanx in advance!
winnie

ps. Here is a part of the /var/log/messages file for a booting (in recovery mode), I marked the segfaults with red.
```
Nov 22 22:23:15 abcserver kernel: imklog 4.2.0, log source = /proc/kmsg started.
Nov 22 22:23:15 abcserver rsyslogd: [origin software="rsyslogd" swVersion="4.2.0" x-pid="820" x-info="http://www.rsyslog.com"] (re)start
Nov 22 22:23:15 abcserver rsyslogd: rsyslogd's groupid changed to 102
Nov 22 22:23:15 abcserver rsyslogd: rsyslogd's userid changed to 101
Nov 22 22:23:15 abcserver kernel: [    0.000000] Initializing cgroup subsys cpuset
Nov 22 22:23:15 abcserver kernel: [    0.000000] Initializing cgroup subsys cpu
Nov 22 22:23:15 abcserver kernel: [    0.000000] Linux version 2.6.32-25-generic-pae (buildd@rothera) (gcc version 4.4.3 (Ubuntu 4.4.3-4ubuntu5) ) #44-Ubuntu SMP Fri Sep 17 21:57:48 UTC 2010 (Ubuntu 2.6.32-25.44-generic-pae 2.6.32.21+drm33.7)
Nov 22 22:23:15 abcserver kernel: [    0.000000] KERNEL supported cpus:
Nov 22 22:23:15 abcserver kernel: [    0.000000]   Intel GenuineIntel
Nov 22 22:23:15 abcserver kernel: [    0.000000]   AMD AuthenticAMD
Nov 22 22:23:15 abcserver kernel: [    0.000000]   NSC Geode by NSC
Nov 22 22:23:15 abcserver kernel: [    0.000000]   Cyrix CyrixInstead
Nov 22 22:23:15 abcserver kernel: [    0.000000]   Centaur CentaurHauls
Nov 22 22:23:15 abcserver kernel: [    0.000000]   Transmeta GenuineTMx86
Nov 22 22:23:15 abcserver kernel: [    0.000000]   Transmeta TransmetaCPU
Nov 22 22:23:15 abcserver kernel: [    0.000000]   UMC UMC UMC UMC
Nov 22 22:23:15 abcserver kernel: [    0.000000] BIOS-provided physical RAM map:
Nov 22 22:23:15 abcserver kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
Nov 22 22:23:15 abcserver kernel: [    0.000000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
Nov 22 22:23:15 abcserver kernel: [    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
Nov 22 22:23:15 abcserver kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 000000007f7f0000 (usable)
Nov 22 22:23:15 abcserver kernel: [    0.000000]  BIOS-e820: 000000007f7f0000 - 000000007f7f3000 (ACPI NVS)
Nov 22 22:23:15 abcserver kernel: [    0.000000]  BIOS-e820: 000000007f7f3000 - 000000007f800000 (ACPI data)
Nov 22 22:23:15 abcserver kernel: [    0.000000]  BIOS-e820: 00000000f0000000 - 00000000f4000000 (reserved)
Nov 22 22:23:15 abcserver kernel: [    0.000000]  BIOS-e820: 00000000fec00000 - 0000000100000000 (reserved)
Nov 22 22:23:15 abcserver kernel: [    0.000000] DMI 2.4 present.
Nov 22 22:23:15 abcserver kernel: [    0.000000] last_pfn = 0x7f7f0 max_arch_pfn = 0x1000000
Nov 22 22:23:15 abcserver kernel: [    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
Nov 22 22:23:15 abcserver kernel: [    0.000000] Scanning 1 areas for low memory corruption
Nov 22 22:23:15 abcserver kernel: [    0.000000] modified physical RAM map:
Nov 22 22:23:15 abcserver kernel: [    0.000000]  modified: 0000000000000000 - 0000000000002000 (usable)
Nov 22 22:23:15 abcserver kernel: [    0.000000]  modified: 0000000000002000 - 0000000000006000 (reserved)
Nov 22 22:23:15 abcserver kernel: [    0.000000]  modified: 0000000000006000 - 000000000009f800 (usable)
Nov 22 22:23:15 abcserver kernel: [    0.000000]  modified: 000000000009f800 - 00000000000a0000 (reserved)
Nov 22 22:23:15 abcserver kernel: [    0.000000]  modified: 00000000000f0000 - 0000000000100000 (reserved)
Nov 22 22:23:15 abcserver kernel: [    0.000000]  modified: 0000000000100000 - 000000007f7f0000 (usable)
Nov 22 22:23:15 abcserver kernel: [    0.000000]  modified: 000000007f7f0000 - 000000007f7f3000 (ACPI NVS)
Nov 22 22:23:15 abcserver kernel: [    0.000000]  modified: 000000007f7f3000 - 000000007f800000 (ACPI data)
Nov 22 22:23:15 abcserver kernel: [    0.000000]  modified: 00000000f0000000 - 00000000f4000000 (reserved)
Nov 22 22:23:15 abcserver kernel: [    0.000000]  modified: 00000000fec00000 - 0000000100000000 (reserved)
Nov 22 22:23:15 abcserver kernel: [    0.000000] init_memory_mapping: 0000000000000000-00000000379fe000
Nov 22 22:23:15 abcserver kernel: [    0.000000] NX (Execute Disable) protection: active
Nov 22 22:23:15 abcserver kernel: [    0.000000] RAMDISK: 37861000 - 37fef115
Nov 22 22:23:15 abcserver kernel: [    0.000000] Allocated new RAMDISK: 0093e000 - 010cc115
Nov 22 22:23:15 abcserver kernel: [    0.000000] Move RAMDISK from 0000000037861000 - 0000000037fef114 to 0093e000 - 010cc114
Nov 22 22:23:15 abcserver kernel: [    0.000000] ACPI: RSDP 000f65a0 00014 (v00 GBT   )
Nov 22 22:23:15 abcserver kernel: [    0.000000] ACPI: RSDT 7f7f3040 0003C (v01 GBT    GBTUACPI 42302E31 GBTU 01010101)
Nov 22 22:23:15 abcserver kernel: [    0.000000] ACPI: FACP 7f7f30c0 00074 (v01 GBT    GBTUACPI 42302E31 GBTU 01010101)
Nov 22 22:23:15 abcserver kernel: [    0.000000] ACPI: DSDT 7f7f3180 03844 (v01 GBT    GBTUACPI 00001000 MSFT 0100000C)
Nov 22 22:23:15 abcserver kernel: [    0.000000] ACPI: FACS 7f7f0000 00040
Nov 22 22:23:15 abcserver kernel: [    0.000000] ACPI: HPET 7f7f6b00 00038 (v01 GBT    GBTUACPI 42302E31 GBTU 00000098)
Nov 22 22:23:15 abcserver kernel: [    0.000000] ACPI: MCFG 7f7f6b80 0003C (v01 GBT    GBTUACPI 42302E31 GBTU 01010101)
Nov 22 22:23:15 abcserver kernel: [    0.000000] ACPI: APIC 7f7f6a40 00068 (v01 GBT    GBTUACPI 42302E31 GBTU 01010101)
Nov 22 22:23:15 abcserver kernel: [    0.000000] ACPI: SSDT 7f7f6c00 0019E (v01  PmRef  Cpu0Ist 00003000 INTL 20040311)
Nov 22 22:23:15 abcserver kernel: [    0.000000] ACPI: SSDT 7f7f7090 00167 (v01  PmRef    CpuPm 00003000 INTL 20040311)
Nov 22 22:23:15 abcserver kernel: [    0.000000] 1149MB HIGHMEM available.
Nov 22 22:23:15 abcserver kernel: [    0.000000] 889MB LOWMEM available.
Nov 22 22:23:15 abcserver kernel: [    0.000000]   mapped low ram: 0 - 379fe000
Nov 22 22:23:15 abcserver kernel: [    0.000000]   low ram: 0 - 379fe000
Nov 22 22:23:15 abcserver kernel: [    0.000000]   node 0 low ram: 00000000 - 379fe000
Nov 22 22:23:15 abcserver kernel: [    0.000000]   node 0 bootmap 00009000 - 0000ff40
Nov 22 22:23:15 abcserver kernel: [    0.000000] (9 early reservations) ==> bootmem [0000000000 - 00379fe000]
Nov 22 22:23:15 abcserver kernel: [    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
Nov 22 22:23:15 abcserver kernel: [    0.000000]   #1 [0000001000 - 0000002000]    EX TRAMPOLINE ==> [0000001000 - 0000002000]
Nov 22 22:23:15 abcserver kernel: [    0.000000]   #2 [0000006000 - 0000007000]       TRAMPOLINE ==> [0000006000 - 0000007000]
Nov 22 22:23:15 abcserver kernel: [    0.000000]   #3 [0000100000 - 0000935818]    TEXT DATA BSS ==> [0000100000 - 0000935818]
Nov 22 22:23:15 abcserver kernel: [    0.000000]   #4 [000009f800 - 0000100000]    BIOS reserved ==> [000009f800 - 0000100000]
Nov 22 22:23:15 abcserver kernel: [    0.000000]   #5 [0000936000 - 000093d0f6]              BRK ==> [0000936000 - 000093d0f6]
Nov 22 22:23:15 abcserver kernel: [    0.000000]   #6 [0000007000 - 0000009000]          PGTABLE ==> [0000007000 - 0000009000]
Nov 22 22:23:15 abcserver kernel: [    0.000000]   #7 [000093e000 - 00010cc115]      NEW RAMDISK ==> [000093e000 - 00010cc115]
Nov 22 22:23:15 abcserver kernel: [    0.000000]   #8 [0000009000 - 0000010000]          BOOTMAP ==> [0000009000 - 0000010000]
Nov 22 22:23:15 abcserver kernel: [    0.000000] found SMP MP-table at [c00f4c60] f4c60
Nov 22 22:23:15 abcserver kernel: [    0.000000] Zone PFN ranges:
Nov 22 22:23:15 abcserver kernel: [    0.000000]   DMA      0x00000000 -> 0x00001000
Nov 22 22:23:15 abcserver kernel: [    0.000000]   Normal   0x00001000 -> 0x000379fe
Nov 22 22:23:15 abcserver kernel: [    0.000000]   HighMem  0x000379fe -> 0x0007f7f0
Nov 22 22:23:15 abcserver kernel: [    0.000000] Movable zone start PFN for each node
Nov 22 22:23:15 abcserver kernel: [    0.000000] early_node_map[3] active PFN ranges
Nov 22 22:23:15 abcserver kernel: [    0.000000]     0: 0x00000000 -> 0x00000002
Nov 22 22:23:15 abcserver kernel: [    0.000000]     0: 0x00000006 -> 0x0000009f
Nov 22 22:23:15 abcserver kernel: [    0.000000]     0: 0x00000100 -> 0x0007f7f0
Nov 22 22:23:15 abcserver kernel: [    0.000000] Using APIC driver default
Nov 22 22:23:15 abcserver kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x408
Nov 22 22:23:15 abcserver kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
Nov 22 22:23:15 abcserver kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
Nov 22 22:23:15 abcserver kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] dfl dfl lint[0x1])
Nov 22 22:23:15 abcserver kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] dfl dfl lint[0x1])
Nov 22 22:23:15 abcserver kernel: [    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
Nov 22 22:23:15 abcserver kernel: [    0.000000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-23
Nov 22 22:23:15 abcserver kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
Nov 22 22:23:15 abcserver kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
Nov 22 22:23:15 abcserver kernel: [    0.000000] Using ACPI (MADT) for SMP configuration information
Nov 22 22:23:15 abcserver kernel: [    0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000
Nov 22 22:23:15 abcserver kernel: [    0.000000] SMP: Allowing 2 CPUs, 0 hotplug CPUs
Nov 22 22:23:15 abcserver kernel: [    0.000000] PM: Registered nosave memory: 0000000000002000 - 0000000000006000
Nov 22 22:23:15 abcserver kernel: [    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
Nov 22 22:23:15 abcserver kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000f0000
Nov 22 22:23:15 abcserver kernel: [    0.000000] PM: Registered nosave memory: 00000000000f0000 - 0000000000100000
Nov 22 22:23:15 abcserver kernel: [    0.000000] Allocating PCI resources starting at 7f800000 (gap: 7f800000:70800000)
Nov 22 22:23:15 abcserver kernel: [    0.000000] Booting paravirtualized kernel on bare hardware
Nov 22 22:23:15 abcserver kernel: [    0.000000] NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:2 nr_node_ids:1
Nov 22 22:23:15 abcserver kernel: [    0.000000] PERCPU: Embedded 15 pages/cpu @c2200000 s39480 r0 d21960 u1048576
Nov 22 22:23:15 abcserver kernel: [    0.000000] pcpu-alloc: s39480 r0 d21960 u1048576 alloc=1*2097152
Nov 22 22:23:15 abcserver kernel: [    0.000000] pcpu-alloc: [0] 0 1 
Nov 22 22:23:15 abcserver kernel: [    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 518043
Nov 22 22:23:15 abcserver kernel: [    0.000000] Kernel command line: root=UUID=3d28fb37-69dd-4fbe-923c-b48790e0cbbd ro quiet splash 
Nov 22 22:23:15 abcserver kernel: [    0.000000] PID hash table entries: 4096 (order: 2, 16384 bytes)
Nov 22 22:23:15 abcserver kernel: [    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
Nov 22 22:23:15 abcserver kernel: [    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
Nov 22 22:23:15 abcserver kernel: [    0.000000] Enabling fast FPU save and restore... done.
Nov 22 22:23:15 abcserver kernel: [    0.000000] Enabling unmasked SIMD FPU exception support... done.
Nov 22 22:23:15 abcserver kernel: [    0.000000] Initializing CPU#0
Nov 22 22:23:15 abcserver kernel: [    0.000000] allocated 10444480 bytes of page_cgroup
Nov 22 22:23:15 abcserver kernel: [    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
Nov 22 22:23:15 abcserver kernel: [    0.000000] Initializing HighMem for node 0 (000379fe:0007f7f0)
Nov 22 22:23:15 abcserver kernel: [    0.000000] Memory: 2043772k/2088896k available (4833k kernel code, 43692k reserved, 2220k data, 672k init, 1177544k highmem)
Nov 22 22:23:15 abcserver kernel: [    0.000000] virtual kernel memory layout:
Nov 22 22:23:15 abcserver kernel: [    0.000000]     fixmap  : 0xfff1d000 - 0xfffff000   ( 904 kB)
Nov 22 22:23:15 abcserver kernel: [    0.000000]     pkmap   : 0xffa00000 - 0xffc00000   (2048 kB)
Nov 22 22:23:15 abcserver kernel: [    0.000000]     vmalloc : 0xf81fe000 - 0xff9fe000   ( 120 MB)
Nov 22 22:23:15 abcserver kernel: [    0.000000]     lowmem  : 0xc0000000 - 0xf79fe000   ( 889 MB)
Nov 22 22:23:15 abcserver kernel: [    0.000000]       .init : 0xc07e4000 - 0xc088c000   ( 672 kB)
Nov 22 22:23:15 abcserver kernel: [    0.000000]       .data : 0xc05b877f - 0xc07e37c8   (2220 kB)
Nov 22 22:23:15 abcserver kernel: [    0.000000]       .text : 0xc0100000 - 0xc05b877f   (4833 kB)
Nov 22 22:23:15 abcserver kernel: [    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
Nov 22 22:23:15 abcserver kernel: [    0.000000] SLUB: Genslabs=13, HWalign=64, Order=0-3, MinObjects=0, CPUs=2, Nodes=1
Nov 22 22:23:15 abcserver kernel: [    0.000000] Hierarchical RCU implementation.
Nov 22 22:23:15 abcserver kernel: [    0.000000] NR_IRQS:2304 nr_irqs:424
Nov 22 22:23:15 abcserver kernel: [    0.000000] Console: colour VGA+ 80x25
Nov 22 22:23:15 abcserver kernel: [    0.000000] console [tty0] enabled
Nov 22 22:23:15 abcserver kernel: [    0.000000] HPET: 3 timers in total, 0 timers will be used for per-cpu timer
Nov 22 22:23:15 abcserver kernel: [    0.000000] Fast TSC calibration using PIT
Nov 22 22:23:15 abcserver kernel: [    0.000000] Detected 2199.924 MHz processor.
Nov 22 22:23:15 abcserver kernel: [    0.004007] Calibrating delay loop (skipped), value calculated using timer frequency.. 4399.84 BogoMIPS (lpj=8799696)
Nov 22 22:23:15 abcserver kernel: [    0.004023] Security Framework initialized
Nov 22 22:23:15 abcserver kernel: [    0.004043] AppArmor: AppArmor initialized
Nov 22 22:23:15 abcserver kernel: [    0.004049] Mount-cache hash table entries: 512
Nov 22 22:23:15 abcserver kernel: [    0.004179] Initializing cgroup subsys ns
Nov 22 22:23:15 abcserver kernel: [    0.004183] Initializing cgroup subsys cpuacct
Nov 22 22:23:15 abcserver kernel: [    0.004187] Initializing cgroup subsys memory
Nov 22 22:23:15 abcserver kernel: [    0.004194] Initializing cgroup subsys devices
Nov 22 22:23:15 abcserver kernel: [    0.004197] Initializing cgroup subsys freezer
Nov 22 22:23:15 abcserver kernel: [    0.004199] Initializing cgroup subsys net_cls
Nov 22 22:23:15 abcserver kernel: [    0.004220] CPU: L1 I cache: 32K, L1 D cache: 32K
Nov 22 22:23:15 abcserver kernel: [    0.004222] CPU: L2 cache: 1024K
Nov 22 22:23:15 abcserver kernel: [    0.004225] CPU: Physical Processor ID: 0
Nov 22 22:23:15 abcserver kernel: [    0.004227] CPU: Processor Core ID: 0
Nov 22 22:23:15 abcserver kernel: [    0.004231] mce: CPU supports 6 MCE banks
Nov 22 22:23:15 abcserver kernel: [    0.004239] CPU0: Thermal monitoring enabled (TM2)
Nov 22 22:23:15 abcserver kernel: [    0.004242] using mwait in idle threads.
Nov 22 22:23:15 abcserver kernel: [    0.004248] Performance Events: Core2 events, Intel PMU driver.
Nov 22 22:23:15 abcserver kernel: [    0.004254] ... version:                2
Nov 22 22:23:15 abcserver kernel: [    0.004256] ... bit width:              40
Nov 22 22:23:15 abcserver kernel: [    0.004257] ... generic registers:      2
Nov 22 22:23:15 abcserver kernel: [    0.004259] ... value mask:             000000ffffffffff
Nov 22 22:23:15 abcserver kernel: [    0.004261] ... max period:             000000007fffffff
Nov 22 22:23:15 abcserver kernel: [    0.004263] ... fixed-purpose events:   3
Nov 22 22:23:15 abcserver kernel: [    0.004264] ... event mask:             0000000700000003
Nov 22 22:23:15 abcserver kernel: [    0.004269] Checking 'hlt' instruction... OK.
Nov 22 22:23:15 abcserver kernel: [    0.022717] ACPI: Core revision 20090903
Nov 22 22:23:15 abcserver kernel: [    0.028008] ftrace: converting mcount calls to 0f 1f 44 00 00
Nov 22 22:23:15 abcserver kernel: [    0.028014] ftrace: allocating 22420 entries in 44 pages
Nov 22 22:23:15 abcserver kernel: [    0.032057] Enabling APIC mode:  Flat.  Using 1 I/O APICs
Nov 22 22:23:15 abcserver kernel: [    0.032369] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
Nov 22 22:23:15 abcserver kernel: [    0.074682] CPU0: Intel(R) Pentium(R) Dual  CPU  E2200  @ 2.20GHz stepping 0d
Nov 22 22:23:15 abcserver kernel: [    0.076001] Booting processor 1 APIC 0x1 ip 0x6000
Nov 22 22:23:15 abcserver kernel: [    0.008000] Initializing CPU#1
Nov 22 22:23:15 abcserver kernel: [    0.008000] CPU: L1 I cache: 32K, L1 D cache: 32K
Nov 22 22:23:15 abcserver kernel: [    0.008000] CPU: L2 cache: 1024K
Nov 22 22:23:15 abcserver kernel: [    0.008000] CPU: Physical Processor ID: 0
Nov 22 22:23:15 abcserver kernel: [    0.008000] CPU: Processor Core ID: 1
Nov 22 22:23:15 abcserver kernel: [    0.008000] CPU1: Thermal monitoring enabled (TM2)
Nov 22 22:23:15 abcserver kernel: [    0.160114] CPU1: Intel(R) Pentium(R) Dual  CPU  E2200  @ 2.20GHz stepping 0d
Nov 22 22:23:15 abcserver kernel: [    0.160123] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
Nov 22 22:23:15 abcserver kernel: [    0.164019] Brought up 2 CPUs
Nov 22 22:23:15 abcserver kernel: [    0.164021] Total of 2 processors activated (8799.81 BogoMIPS).
Nov 22 22:23:15 abcserver kernel: [    0.164477] devtmpfs: initialized
Nov 22 22:23:15 abcserver kernel: [    0.164477] regulator: core version 0.5
Nov 22 22:23:15 abcserver kernel: [    0.164477] Time: 21:22:59  Date: 11/22/10
Nov 22 22:23:15 abcserver kernel: [    0.164477] NET: Registered protocol family 16
Nov 22 22:23:15 abcserver kernel: [    0.164477] Trying to unpack rootfs image as initramfs...
Nov 22 22:23:15 abcserver kernel: [    0.164477] EISA bus registered
Nov 22 22:23:15 abcserver kernel: [    0.164477] ACPI: bus type pci registered
Nov 22 22:23:15 abcserver kernel: [    0.164477] PCI: MCFG configuration 0: base f0000000 segment 0 buses 0 - 63
Nov 22 22:23:15 abcserver kernel: [    0.164477] PCI: MCFG area at f0000000 reserved in E820
Nov 22 22:23:15 abcserver kernel: [    0.164477] PCI: Using MMCONFIG for extended config space
Nov 22 22:23:15 abcserver kernel: [    0.164477] PCI: Using configuration type 1 for base access
Nov 22 22:23:15 abcserver kernel: [    0.168121] bio: create slab <bio-0> at 0
Nov 22 22:23:15 abcserver kernel: [    0.173524] ACPI: Interpreter enabled
Nov 22 22:23:15 abcserver kernel: [    0.173533] ACPI: (supports S0 S3 S4 S5)
Nov 22 22:23:15 abcserver kernel: [    0.173556] ACPI: Using IOAPIC for interrupt routing
Nov 22 22:23:15 abcserver kernel: [    0.177685] ACPI: No dock devices found.
Nov 22 22:23:15 abcserver kernel: [    0.177773] ACPI: PCI Root Bridge [PCI0] (0000:00)
Nov 22 22:23:15 abcserver kernel: [    0.178015] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
Nov 22 22:23:15 abcserver kernel: [    0.178019] pci 0000:00:1b.0: PME# disabled
Nov 22 22:23:15 abcserver kernel: [    0.178085] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
Nov 22 22:23:15 abcserver kernel: [    0.178089] pci 0000:00:1c.0: PME# disabled
Nov 22 22:23:15 abcserver kernel: [    0.178157] pci 0000:00:1c.1: PME# supported from D0 D3hot D3cold
Nov 22 22:23:15 abcserver kernel: [    0.178161] pci 0000:00:1c.1: PME# disabled
Nov 22 22:23:15 abcserver kernel: [    0.178585] pci 0000:00:1f.0: quirk: region 0400-047f claimed by ICH6 ACPI/GPIO/TCO
Nov 22 22:23:15 abcserver kernel: [    0.178589] pci 0000:00:1f.0: quirk: region 0480-04bf claimed by ICH6 GPIO
Nov 22 22:23:15 abcserver kernel: [    0.178593] pci 0000:00:1f.0: ICH7 LPC Generic IO decode 1 PIO at 0800 (mask 000f)
Nov 22 22:23:15 abcserver kernel: [    0.178596] pci 0000:00:1f.0: ICH7 LPC Generic IO decode 2 PIO at 0290 (mask 000f)
Nov 22 22:23:15 abcserver kernel: [    0.178696] pci 0000:00:1f.2: PME# supported from D3hot
Nov 22 22:23:15 abcserver kernel: [    0.178700] pci 0000:00:1f.2: PME# disabled
Nov 22 22:23:15 abcserver kernel: [    0.178957] pci 0000:02:00.0: PME# supported from D0 D1 D2 D3hot D3cold
Nov 22 22:23:15 abcserver kernel: [    0.178962] pci 0000:02:00.0: PME# disabled
Nov 22 22:23:15 abcserver kernel: [    0.179083] pci 0000:00:1e.0: transparent bridge
Nov 22 22:23:15 abcserver kernel: [    0.189204] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 *5 6 7 9 10 11 12 14 15)
Nov 22 22:23:15 abcserver kernel: [    0.189295] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 9 *10 11 12 14 15)
Nov 22 22:23:15 abcserver kernel: [    0.189383] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 *9 10 11 12 14 15)
Nov 22 22:23:15 abcserver kernel: [    0.189468] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)
Nov 22 22:23:15 abcserver kernel: [    0.189554] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
Nov 22 22:23:15 abcserver kernel: [    0.189643] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
Nov 22 22:23:15 abcserver kernel: [    0.189731] ACPI: PCI Interrupt Link [LNK0] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
Nov 22 22:23:15 abcserver kernel: [    0.189817] ACPI: PCI Interrupt Link [LNK1] (IRQs *3 4 5 6 7 9 10 11 12 14 15)
Nov 22 22:23:15 abcserver kernel: [    0.189932] vgaarb: device added: PCI:0000:00:02.0,decodes=io+mem,owns=io+mem,locks=none
Nov 22 22:23:15 abcserver kernel: [    0.189944] vgaarb: loaded
Nov 22 22:23:15 abcserver kernel: [    0.190068] SCSI subsystem initialized
Nov 22 22:23:15 abcserver kernel: [    0.190235] usbcore: registered new interface driver usbfs
Nov 22 22:23:15 abcserver kernel: [    0.190249] usbcore: registered new interface driver hub
Nov 22 22:23:15 abcserver kernel: [    0.190277] usbcore: registered new device driver usb
Nov 22 22:23:15 abcserver kernel: [    0.190410] ACPI: WMI: Mapper loaded
Nov 22 22:23:15 abcserver kernel: [    0.190412] PCI: Using ACPI for IRQ routing
Nov 22 22:23:15 abcserver kernel: [    0.190562] NetLabel: Initializing
Nov 22 22:23:15 abcserver kernel: [    0.190564] NetLabel:  domain hash size = 128
Nov 22 22:23:15 abcserver kernel: [    0.190566] NetLabel:  protocols = UNLABELED CIPSOv4
Nov 22 22:23:15 abcserver kernel: [    0.190578] NetLabel:  unlabeled traffic allowed by default
Nov 22 22:23:15 abcserver kernel: [    0.190617] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
Nov 22 22:23:15 abcserver kernel: [    0.190622] hpet0: 3 comparators, 64-bit 14.318180 MHz counter
Nov 22 22:23:15 abcserver kernel: [    0.196256] Switching to clocksource tsc
Nov 22 22:23:15 abcserver kernel: [    0.198124] AppArmor: AppArmor Filesystem Enabled
Nov 22 22:23:15 abcserver kernel: [    0.198151] pnp: PnP ACPI init
Nov 22 22:23:15 abcserver kernel: [    0.198178] ACPI: bus type pnp registered
Nov 22 22:23:15 abcserver kernel: [    0.200605] pnp: PnP ACPI: found 13 devices
Nov 22 22:23:15 abcserver kernel: [    0.200608] ACPI: ACPI bus type pnp unregistered
Nov 22 22:23:15 abcserver kernel: [    0.200613] PnPBIOS: Disabled by ACPI PNP
Nov 22 22:23:15 abcserver kernel: [    0.200627] system 00:01: ioport range 0x4d0-0x4d1 has been reserved
Nov 22 22:23:15 abcserver kernel: [    0.200630] system 00:01: ioport range 0x290-0x29f has been reserved
Nov 22 22:23:15 abcserver kernel: [    0.200633] system 00:01: ioport range 0x800-0x87f has been reserved
Nov 22 22:23:15 abcserver kernel: [    0.200636] system 00:01: ioport range 0x290-0x294 has been reserved
Nov 22 22:23:15 abcserver kernel: [    0.200639] system 00:01: ioport range 0x880-0x88f has been reserved
Nov 22 22:23:15 abcserver kernel: [    0.200647] system 00:09: ioport range 0x400-0x4bf could not be reserved
Nov 22 22:23:15 abcserver kernel: [    0.200655] system 00:0a: iomem range 0xf0000000-0xf3ffffff has been reserved
Nov 22 22:23:15 abcserver kernel: [    0.200660] system 00:0b: iomem range 0xcc000-0xd3fff has been reserved
Nov 22 22:23:15 abcserver kernel: [    0.200663] system 00:0b: iomem range 0xf0000-0xf7fff could not be reserved
Nov 22 22:23:15 abcserver kernel: [    0.200666] system 00:0b: iomem range 0xf8000-0xfbfff could not be reserved
Nov 22 22:23:15 abcserver kernel: [    0.200669] system 00:0b: iomem range 0xfc000-0xfffff could not be reserved
Nov 22 22:23:15 abcserver kernel: [    0.200672] system 00:0b: iomem range 0x7f7f0000-0x7f7fffff could not be reserved
Nov 22 22:23:15 abcserver kernel: [    0.200675] system 00:0b: iomem range 0x0-0x9ffff could not be reserved
Nov 22 22:23:15 abcserver kernel: [    0.200678] system 00:0b: iomem range 0x100000-0x7f7effff could not be reserved
Nov 22 22:23:15 abcserver kernel: [    0.200681] system 00:0b: iomem range 0xfec00000-0xfec00fff could not be reserved
Nov 22 22:23:15 abcserver kernel: [    0.200684] system 00:0b: iomem range 0xfed13000-0xfed1dfff has been reserved
Nov 22 22:23:15 abcserver kernel: [    0.200686] system 00:0b: iomem range 0xfed20000-0xfed8ffff has been reserved
Nov 22 22:23:15 abcserver kernel: [    0.200689] system 00:0b: iomem range 0xfee00000-0xfee00fff has been reserved
Nov 22 22:23:15 abcserver kernel: [    0.200692] system 00:0b: iomem range 0xffb00000-0xffb7ffff has been reserved
Nov 22 22:23:15 abcserver kernel: [    0.200695] system 00:0b: iomem range 0xfff00000-0xffffffff has been reserved
Nov 22 22:23:15 abcserver kernel: [    0.200698] system 00:0b: iomem range 0xe0000-0xeffff has been reserved
Nov 22 22:23:15 abcserver kernel: [    0.235435] pci 0000:00:1c.0: PCI bridge, secondary bus 0000:01
Nov 22 22:23:15 abcserver kernel: [    0.235440] pci 0000:00:1c.0:   IO window: 0x9000-0x9fff
Nov 22 22:23:15 abcserver kernel: [    0.235445] pci 0000:00:1c.0:   MEM window: 0x80000000-0x801fffff
Nov 22 22:23:15 abcserver kernel: [    0.235450] pci 0000:00:1c.0:   PREFETCH window: 0x00000080200000-0x000000803fffff
Nov 22 22:23:15 abcserver kernel: [    0.235457] pci 0000:00:1c.1: PCI bridge, secondary bus 0000:02
Nov 22 22:23:15 abcserver kernel: [    0.235461] pci 0000:00:1c.1:   IO window: 0xa000-0xafff
Nov 22 22:23:15 abcserver kernel: [    0.235466] pci 0000:00:1c.1:   MEM window: 0xd0000000-0xd0ffffff
Nov 22 22:23:15 abcserver kernel: [    0.235470] pci 0000:00:1c.1:   PREFETCH window: 0x000000d1000000-0x000000d10fffff
Nov 22 22:23:15 abcserver kernel: [    0.235477] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:03
Nov 22 22:23:15 abcserver kernel: [    0.235480] pci 0000:00:1e.0:   IO window: 0x8000-0x8fff
Nov 22 22:23:15 abcserver kernel: [    0.235485] pci 0000:00:1e.0:   MEM window: disabled
Nov 22 22:23:15 abcserver kernel: [    0.235489] pci 0000:00:1e.0:   PREFETCH window: disabled
Nov 22 22:23:15 abcserver kernel: [    0.235522] pci 0000:00:1c.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Nov 22 22:23:15 abcserver kernel: [    0.235541] pci 0000:00:1c.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
Nov 22 22:23:15 abcserver kernel: [    0.235621] NET: Registered protocol family 2
Nov 22 22:23:15 abcserver kernel: [    0.235725] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
Nov 22 22:23:15 abcserver kernel: [    0.236041] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
Nov 22 22:23:15 abcserver kernel: [    0.236649] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
Nov 22 22:23:15 abcserver kernel: [    0.237026] TCP: Hash tables configured (established 131072 bind 65536)
Nov 22 22:23:15 abcserver kernel: [    0.237028] TCP reno registered
Nov 22 22:23:15 abcserver kernel: [    0.237144] NET: Registered protocol family 1
Nov 22 22:23:15 abcserver kernel: [    0.237484] cpufreq-nforce2: No nForce2 chipset.
Nov 22 22:23:15 abcserver kernel: [    0.237511] Scanning for low memory corruption every 60 seconds
Nov 22 22:23:15 abcserver kernel: [    0.237634] audit: initializing netlink socket (disabled)
Nov 22 22:23:15 abcserver kernel: [    0.237655] type=2000 audit(1290460979.235:1): initialized
Nov 22 22:23:15 abcserver kernel: [    0.247156] highmem bounce pool size: 64 pages
Nov 22 22:23:15 abcserver kernel: [    0.247162] HugeTLB registered 2 MB page size, pre-allocated 0 pages
Nov 22 22:23:15 abcserver kernel: [    0.248584] VFS: Disk quotas dquot_6.5.2
Nov 22 22:23:15 abcserver kernel: [    0.248649] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
Nov 22 22:23:15 abcserver kernel: [    0.249197] fuse init (API version 7.13)
Nov 22 22:23:15 abcserver kernel: [    0.249282] msgmni has been set to 1693
Nov 22 22:23:15 abcserver kernel: [    0.249506] alg: No test for stdrng (krng)
Nov 22 22:23:15 abcserver kernel: [    0.249564] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
Nov 22 22:23:15 abcserver kernel: [    0.249566] io scheduler noop registered
Nov 22 22:23:15 abcserver kernel: [    0.249568] io scheduler anticipatory registered
Nov 22 22:23:15 abcserver kernel: [    0.249570] io scheduler deadline registered
Nov 22 22:23:15 abcserver kernel: [    0.249609] io scheduler cfq registered (default)
Nov 22 22:23:15 abcserver kernel: [    0.249986] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Nov 22 22:23:15 abcserver kernel: [    0.250061] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
Nov 22 22:23:15 abcserver kernel: [    0.250149] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0
Nov 22 22:23:15 abcserver kernel: [    0.250153] ACPI: Power Button [PWRB]
Nov 22 22:23:15 abcserver kernel: [    0.250206] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
Nov 22 22:23:15 abcserver kernel: [    0.250209] ACPI: Power Button [PWRF]
Nov 22 22:23:15 abcserver kernel: [    0.250462] processor LNXCPU:00: registered as cooling_device0
Nov 22 22:23:15 abcserver kernel: [    0.250642] ACPI: SSDT 7f7f7000 00087 (v01  PmRef  Cpu1Ist 00003000 INTL 20040311)
Nov 22 22:23:15 abcserver kernel: [    0.250926] processor LNXCPU:01: registered as cooling_device1
Nov 22 22:23:15 abcserver kernel: [    0.252660] isapnp: Scanning for PnP cards...
Nov 22 22:23:15 abcserver kernel: [    0.253887] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
Nov 22 22:23:15 abcserver kernel: [    0.253984] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Nov 22 22:23:15 abcserver kernel: [    0.254316] 00:06: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Nov 22 22:23:15 abcserver kernel: [    0.255381] brd: module loaded
Nov 22 22:23:15 abcserver kernel: [    0.255840] loop: module loaded
Nov 22 22:23:15 abcserver kernel: [    0.255925] input: Macintosh mouse button emulation as /devices/virtual/input/input2
Nov 22 22:23:15 abcserver kernel: [    0.256073] ata_piix 0000:00:1f.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
Nov 22 22:23:15 abcserver kernel: [    0.256078] ata_piix 0000:00:1f.2: MAP [ P0 P2 P1 P3 ]
Nov 22 22:23:15 abcserver kernel: [    0.263600] scsi0 : ata_piix
Nov 22 22:23:15 abcserver kernel: [    0.311519] scsi1 : ata_piix
Nov 22 22:23:15 abcserver kernel: [    0.312219] ata1: SATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xf000 irq 14
Nov 22 22:23:15 abcserver kernel: [    0.312222] ata2: SATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xf008 irq 15
Nov 22 22:23:15 abcserver kernel: [    0.312552] Fixed MDIO Bus: probed
Nov 22 22:23:15 abcserver kernel: [    0.312588] PPP generic driver version 2.4.2
Nov 22 22:23:15 abcserver kernel: [    0.312651] tun: Universal TUN/TAP device driver, 1.6
Nov 22 22:23:15 abcserver kernel: [    0.312653] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
Nov 22 22:23:15 abcserver kernel: [    0.312756] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
Nov 22 22:23:15 abcserver kernel: [    0.312791] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23
Nov 22 22:23:15 abcserver kernel: [    0.312815] ehci_hcd 0000:00:1d.7: EHCI Host Controller
Nov 22 22:23:15 abcserver kernel: [    0.312846] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 1
Nov 22 22:23:15 abcserver kernel: [    0.312864] ehci_hcd 0000:00:1d.7: using broken periodic workaround
Nov 22 22:23:15 abcserver kernel: [    0.316788] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xd11c4000
Nov 22 22:23:15 abcserver kernel: [    0.331555] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
Nov 22 22:23:15 abcserver kernel: [    0.331684] usb usb1: configuration #1 chosen from 1 choice
Nov 22 22:23:15 abcserver kernel: [    0.331713] hub 1-0:1.0: USB hub found
Nov 22 22:23:15 abcserver kernel: [    0.331724] hub 1-0:1.0: 8 ports detected
Nov 22 22:23:15 abcserver kernel: [    0.331797] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
Nov 22 22:23:15 abcserver kernel: [    0.331814] uhci_hcd: USB Universal Host Controller Interface driver
Nov 22 22:23:15 abcserver kernel: [    0.331863] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
Nov 22 22:23:15 abcserver kernel: [    0.331877] uhci_hcd 0000:00:1d.0: UHCI Host Controller
Nov 22 22:23:15 abcserver kernel: [    0.331915] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
Nov 22 22:23:15 abcserver kernel: [    0.331942] uhci_hcd 0000:00:1d.0: irq 23, io base 0x0000b400
Nov 22 22:23:15 abcserver kernel: [    0.332026] usb usb2: configuration #1 chosen from 1 choice
Nov 22 22:23:15 abcserver kernel: [    0.332050] hub 2-0:1.0: USB hub found
Nov 22 22:23:15 abcserver kernel: [    0.332056] hub 2-0:1.0: 2 ports detected
Nov 22 22:23:15 abcserver kernel: [    0.332100] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
Nov 22 22:23:15 abcserver kernel: [    0.332109] uhci_hcd 0000:00:1d.1: UHCI Host Controller
Nov 22 22:23:15 abcserver kernel: [    0.332141] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 3
Nov 22 22:23:15 abcserver kernel: [    0.332173] uhci_hcd 0000:00:1d.1: irq 19, io base 0x0000b800
Nov 22 22:23:15 abcserver kernel: [    0.332255] usb usb3: configuration #1 chosen from 1 choice
Nov 22 22:23:15 abcserver kernel: [    0.332279] hub 3-0:1.0: USB hub found
Nov 22 22:23:15 abcserver kernel: [    0.332285] hub 3-0:1.0: 2 ports detected
Nov 22 22:23:15 abcserver kernel: [    0.332335] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
Nov 22 22:23:15 abcserver kernel: [    0.332344] uhci_hcd 0000:00:1d.2: UHCI Host Controller
Nov 22 22:23:15 abcserver kernel: [    0.332373] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 4
Nov 22 22:23:15 abcserver kernel: [    0.332401] uhci_hcd 0000:00:1d.2: irq 18, io base 0x0000bc00
Nov 22 22:23:15 abcserver kernel: [    0.332487] usb usb4: configuration #1 chosen from 1 choice
Nov 22 22:23:15 abcserver kernel: [    0.332510] hub 4-0:1.0: USB hub found
Nov 22 22:23:15 abcserver kernel: [    0.332516] hub 4-0:1.0: 2 ports detected
Nov 22 22:23:15 abcserver kernel: [    0.332558] uhci_hcd 0000:00:1d.3: PCI INT D -> GSI 16 (level, low) -> IRQ 16
Nov 22 22:23:15 abcserver kernel: [    0.332567] uhci_hcd 0000:00:1d.3: UHCI Host Controller
Nov 22 22:23:15 abcserver kernel: [    0.332596] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 5
Nov 22 22:23:15 abcserver kernel: [    0.332624] uhci_hcd 0000:00:1d.3: irq 16, io base 0x0000c000
Nov 22 22:23:15 abcserver kernel: [    0.332706] usb usb5: configuration #1 chosen from 1 choice
Nov 22 22:23:15 abcserver kernel: [    0.332730] hub 5-0:1.0: USB hub found
Nov 22 22:23:15 abcserver kernel: [    0.332738] hub 5-0:1.0: 2 ports detected
Nov 22 22:23:15 abcserver kernel: [    0.332826] PNP: PS/2 Controller [PNP0f13:PS2M] at 0x60,0x64 irq 12
Nov 22 22:23:15 abcserver kernel: [    0.332828] PNP: PS/2 controller doesn't have KBD irq; using default 1
Nov 22 22:23:15 abcserver kernel: [    0.333224] serio: i8042 KBD port at 0x60,0x64 irq 1
Nov 22 22:23:15 abcserver kernel: [    0.333231] serio: i8042 AUX port at 0x60,0x64 irq 12
Nov 22 22:23:15 abcserver kernel: [    0.333306] mice: PS/2 mouse device common for all mice
Nov 22 22:23:15 abcserver kernel: [    0.333408] rtc_cmos 00:03: RTC can wake from S4
Nov 22 22:23:15 abcserver kernel: [    0.333447] rtc_cmos 00:03: rtc core: registered rtc_cmos as rtc0
Nov 22 22:23:15 abcserver kernel: [    0.333470] rtc0: alarms up to one month, 242 bytes nvram, hpet irqs
Nov 22 22:23:15 abcserver kernel: [    0.333569] device-mapper: uevent: version 1.0.3
Nov 22 22:23:15 abcserver kernel: [    0.339795] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: dm-devel@redhat.com
Nov 22 22:23:15 abcserver kernel: [    0.361863] Freeing initrd memory: 7736k freed
Nov 22 22:23:15 abcserver kernel: [    0.388657] device-mapper: multipath: version 1.1.0 loaded
Nov 22 22:23:15 abcserver kernel: [    0.388667] device-mapper: multipath round-robin: version 1.0.0 loaded
Nov 22 22:23:15 abcserver kernel: [    0.388904] EISA: Probing bus 0 at eisa.0
Nov 22 22:23:15 abcserver kernel: [    0.388931] Cannot allocate resource for EISA slot 8
Nov 22 22:23:15 abcserver kernel: [    0.388933] EISA: Detected 0 cards.
Nov 22 22:23:15 abcserver kernel: [    0.389005] cpuidle: using governor ladder
Nov 22 22:23:15 abcserver kernel: [    0.389008] cpuidle: using governor menu
Nov 22 22:23:15 abcserver kernel: [    0.389461] TCP cubic registered
Nov 22 22:23:15 abcserver kernel: [    0.389604] NET: Registered protocol family 10
Nov 22 22:23:15 abcserver kernel: [    0.390052] lo: Disabled Privacy Extensions
Nov 22 22:23:15 abcserver kernel: [    0.390376] NET: Registered protocol family 17
Nov 22 22:23:15 abcserver kernel: [    0.391552] Using IPI No-Shortcut mode
Nov 22 22:23:15 abcserver kernel: [    0.391659] registered taskstats version 1
Nov 22 22:23:15 abcserver kernel: [    0.391904]   Magic number: 2:735:399
Nov 22 22:23:15 abcserver kernel: [    0.391981] rtc_cmos 00:03: setting system clock to 2010-11-22 21:22:59 UTC (1290460979)
Nov 22 22:23:15 abcserver kernel: [    0.391984] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
Nov 22 22:23:15 abcserver kernel: [    0.391986] EDD information not available.
Nov 22 22:23:15 abcserver kernel: [    0.535607] ata1.00: HPA unlocked: 488395055 -> 488397168, native 488397168
Nov 22 22:23:15 abcserver kernel: [    0.535612] ata1.00: ATA-7: SAMSUNG HD252HJ, 1AC01113, max UDMA7
Nov 22 22:23:15 abcserver kernel: [    0.535615] ata1.00: 488397168 sectors, multi 16: LBA48 NCQ (depth 0/32)
Nov 22 22:23:15 abcserver kernel: [    0.543927] ata1.00: configured for UDMA/133
Nov 22 22:23:15 abcserver kernel: [    0.551603] ata2.00: ATAPI: TSSTcorp CDDVDW SH-S223F, SB00, max UDMA/100
Nov 22 22:23:15 abcserver kernel: [    0.567626] ata2.00: configured for UDMA/100
Nov 22 22:23:15 abcserver kernel: [    0.606410] isapnp: No Plug & Play device found
Nov 22 22:23:15 abcserver kernel: [    0.606520] scsi 0:0:0:0: Direct-Access     ATA      SAMSUNG HD252HJ  1AC0 PQ: 0 ANSI: 5
Nov 22 22:23:15 abcserver kernel: [    0.606637] sd 0:0:0:0: [sda] 488397168 512-byte logical blocks: (250 GB/232 GiB)
Nov 22 22:23:15 abcserver kernel: [    0.606656] sd 0:0:0:0: Attached scsi generic sg0 type 0
Nov 22 22:23:15 abcserver kernel: [    0.606679] sd 0:0:0:0: [sda] Write Protect is off
Nov 22 22:23:15 abcserver kernel: [    0.606705] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Nov 22 22:23:15 abcserver kernel: [    0.606843]  sda:
Nov 22 22:23:15 abcserver kernel: [    0.607340] scsi 1:0:0:0: CD-ROM            TSSTcorp CDDVDW SH-S223F  SB00 PQ: 0 ANSI: 5
Nov 22 22:23:15 abcserver kernel: [    0.611164] sr0: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
Nov 22 22:23:15 abcserver kernel: [    0.611169] Uniform CD-ROM driver Revision: 3.20
Nov 22 22:23:15 abcserver kernel: [    0.611357] sr 1:0:0:0: Attached scsi generic sg1 type 5
Nov 22 22:23:15 abcserver kernel: [    0.623222]  sda1 sda2 < sda5
Nov 22 22:23:15 abcserver kernel: [    0.643613] usb 1-4: new high speed USB device using ehci_hcd and address 2
Nov 22 22:23:15 abcserver kernel: [    0.653545]  sda6 >
Nov 22 22:23:15 abcserver kernel: [    0.653876] sd 0:0:0:0: [sda] Attached SCSI disk
Nov 22 22:23:15 abcserver kernel: [    0.653890] Freeing unused kernel memory: 672k freed
Nov 22 22:23:15 abcserver kernel: [    0.654230] Write protecting the kernel text: 4836k
Nov 22 22:23:15 abcserver kernel: [    0.654306] Write protecting the kernel read-only data: 1880k
Nov 22 22:23:15 abcserver kernel: [    0.671918] udev: starting version 151
Nov 22 22:23:15 abcserver kernel: [    0.760845] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
Nov 22 22:23:15 abcserver kernel: [    0.760868] r8169 0000:02:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
Nov 22 22:23:15 abcserver kernel: [    0.761604] eth0: RTL8168c/8111c at 0xf8250000, 00:1f:d0:02:48:ef, XID 1c4000c0 IRQ 26
Nov 22 22:23:15 abcserver kernel: [    0.823621] usb 1-4: configuration #1 chosen from 1 choice
Nov 22 22:23:15 abcserver kernel: [    0.831150] Initializing USB Mass Storage driver...
Nov 22 22:23:15 abcserver kernel: [    0.831307] scsi2 : SCSI emulation for USB Mass Storage devices
Nov 22 22:23:15 abcserver kernel: [    0.831468] usbcore: registered new interface driver usb-storage
Nov 22 22:23:15 abcserver kernel: [    0.831488] USB Mass Storage support registered.
Nov 22 22:23:15 abcserver kernel: [    0.960526] EXT3-fs: INFO: recovery required on readonly filesystem.
Nov 22 22:23:15 abcserver kernel: [    0.960529] EXT3-fs: write access will be enabled during recovery.
Nov 22 22:23:15 abcserver kernel: [    0.992743] usb 1-8: new high speed USB device using ehci_hcd and address 4
Nov 22 22:23:15 abcserver kernel: [    1.004145] kjournald starting.  Commit interval 5 seconds
Nov 22 22:23:15 abcserver kernel: [    1.004154] EXT3-fs: recovery complete.
Nov 22 22:23:15 abcserver kernel: [    1.004678] EXT3-fs: mounted filesystem with ordered data mode.
Nov 22 22:23:15 abcserver kernel: [    1.128023] usb 1-8: configuration #1 chosen from 1 choice
Nov 22 22:23:15 abcserver kernel: [    1.372041] usb 5-1: new low speed USB device using uhci_hcd and address 2
Nov 22 22:23:15 abcserver kernel: [    1.582829] usb 5-1: configuration #1 chosen from 1 choice
Nov 22 22:23:15 abcserver kernel: [    5.837946] scsi 2:0:0:0: Direct-Access     Generic  Flash HS-CF      3.95 PQ: 0 ANSI: 0
Nov 22 22:23:15 abcserver kernel: [    5.841690] scsi 2:0:0:1: Direct-Access     Generic  Flash HS-MS      3.95 PQ: 0 ANSI: 0
Nov 22 22:23:15 abcserver kernel: [    5.845441] scsi 2:0:0:2: Direct-Access     Generic  Flash HS-SM      3.95 PQ: 0 ANSI: 0
Nov 22 22:23:15 abcserver kernel: [    5.849065] scsi 2:0:0:3: Direct-Access     Generic  Flash HS-SD/MMC  3.95 PQ: 0 ANSI: 0
Nov 22 22:23:15 abcserver kernel: [    5.849530] sd 2:0:0:0: Attached scsi generic sg2 type 0
Nov 22 22:23:15 abcserver kernel: [    5.849655] sd 2:0:0:1: Attached scsi generic sg3 type 0
Nov 22 22:23:15 abcserver kernel: [    5.849772] sd 2:0:0:2: Attached scsi generic sg4 type 0
Nov 22 22:23:15 abcserver kernel: [    5.849895] sd 2:0:0:3: Attached scsi generic sg5 type 0
Nov 22 22:23:15 abcserver kernel: [    5.862171] sd 2:0:0:0: [sdb] Attached SCSI removable disk
Nov 22 22:23:15 abcserver kernel: [    5.920791] sd 2:0:0:1: [sdc] Attached SCSI removable disk
Nov 22 22:23:15 abcserver kernel: [    5.925540] sd 2:0:0:2: [sdd] Attached SCSI removable disk
Nov 22 22:23:15 abcserver kernel: [    5.929541] sd 2:0:0:3: [sde] Attached SCSI removable disk
Nov 22 22:23:15 abcserver kernel: [   15.432453] udev: starting version 151
[COLOR="Red"]Nov 22 22:23:15 abcserver kernel: [   15.495761] grep[312]: segfault at 8060322 ip 08060322 sp bf8b48a8 error 15 in grep[8060000+1000]
[/COLOR]Nov 22 22:23:15 abcserver kernel: [   15.516404] chgrp uses obsolete (PF_INET,SOCK_PACKET)
Nov 22 22:23:15 abcserver kernel: [   15.525799] Linux agpgart interface v0.103
Nov 22 22:23:15 abcserver kernel: [   15.542514] device eth0 entered promiscuous mode
Nov 22 22:23:15 abcserver kernel: [   15.546771] Adding 6048432k swap on /dev/sda6.  Priority:-1 extents:1 across:6048432k 
[COLOR="Red"]Nov 22 22:23:15 abcserver kernel: [   15.551376] grep[426]: segfault at 8060322 ip 08060322 sp bf92b538 error 15 in grep[8060000+1000]
[/COLOR]Nov 22 22:23:15 abcserver kernel: [   15.603577] agpgart-intel 0000:00:00.0: Intel 945G Chipset
Nov 22 22:23:15 abcserver kernel: [   15.603869] agpgart-intel 0000:00:00.0: detected 7932K stolen memory
Nov 22 22:23:15 abcserver kernel: [   15.606232] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0xc0000000
[COLOR="Red"]Nov 22 22:23:15 abcserver kernel: [   15.657467] grep[509]: segfault at 8060322 ip 08060322 sp bfae9ef8 error 15 in grep[8060000+1000]
[/COLOR]Nov 22 22:23:15 abcserver kernel: [   15.687228] intel_rng: FWH not detected
[COLOR="Red"]Nov 22 22:23:15 abcserver kernel: [   15.717608] grep[556]: segfault at 8060322 ip 08060322 sp bf9a7ea8 error 15 in grep[8060000+1000]
[/COLOR]Nov 22 22:23:15 abcserver kernel: [   15.725671] [drm] Initialized drm 1.1.0 20060810
Nov 22 22:23:15 abcserver kernel: [   15.743337] type=1505 audit(1290460994.848:2):  operation="profile_load" pid=534 name="/sbin/dhclient3"
Nov 22 22:23:15 abcserver kernel: [   15.743963] type=1505 audit(1290460994.848:3):  operation="profile_load" pid=534 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
Nov 22 22:23:15 abcserver kernel: [   15.744349] type=1505 audit(1290460994.852:4):  operation="profile_load" pid=534 name="/usr/lib/connman/scripts/dhclient-script"
Nov 22 22:23:15 abcserver kernel: [   15.750569] parport_pc 00:07: reported by Plug and Play ACPI
Nov 22 22:23:15 abcserver kernel: [   15.750617] parport0: PC-style at 0x378, irq 7 [
Nov 22 22:23:15 abcserver kernel: [   15.750658] PCSPP,TRISTATE]
Nov 22 22:23:15 abcserver kernel: [   15.764785] dvb-usb: found a 'Afatech AF9015 DVB-T USB2.0 stick' in cold state, will try to load a firmware
Nov 22 22:23:15 abcserver kernel: [   15.764792] usb 1-8: firmware: requesting dvb-usb-af9015.fw
[COLOR="Red"]Nov 22 22:23:15 abcserver kernel: [   15.789603] grep[593]: segfault at 8060322 ip 08060322 sp bf8b9cc8 error 15 in grep[8060000+1000]
[/COLOR][COLOR="Red"]Nov 22 22:23:15 abcserver kernel: [   15.799187] grep[602]: segfault at 8060322 ip 08060322 sp bfd2eb28 error 15 in grep[8060000+1000][/COLOR]
Nov 22 22:23:15 abcserver kernel: [   15.802595] i915 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[COLOR="Red"]Nov 22 22:23:15 abcserver kernel: [   15.807698] grep[605]: segfault at 8060322 ip 08060322 sp bfc90278 error 15 in grep[8060000+1000]
[/COLOR]Nov 22 22:23:15 abcserver kernel: [   15.813096] [drm] set up 7M of stolen space
Nov 22 22:23:15 abcserver kernel: [   15.813688] [drm] initialized overlay support
Nov 22 22:23:15 abcserver kernel: [   15.840712] dvb-usb: downloading firmware from file 'dvb-usb-af9015.fw'
Nov 22 22:23:15 abcserver kernel: [   15.904145] ppdev: user-space parallel port driver
Nov 22 22:23:15 abcserver kernel: [   15.910334] usbcore: registered new interface driver hiddev
Nov 22 22:23:15 abcserver kernel: [   15.928133] dvb-usb: found a 'Afatech AF9015 DVB-T USB2.0 stick' in warm state.
Nov 22 22:23:15 abcserver kernel: [   15.928183] dvb-usb: will pass the complete MPEG2 transport stream to the software demuxer.
Nov 22 22:23:15 abcserver kernel: [   15.928822] DVB: registering new adapter (Afatech AF9015 DVB-T USB2.0 stick)
Nov 22 22:23:15 abcserver kernel: [   15.988225] fb0: inteldrmfb frame buffer device
Nov 22 22:23:15 abcserver kernel: [   15.988228] registered panic notifier
Nov 22 22:23:15 abcserver kernel: [   15.988239] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
Nov 22 22:23:15 abcserver kernel: [   15.996828] r8169: eth0: link up
Nov 22 22:23:15 abcserver kernel: [   15.996836] r8169: eth0: link up
Nov 22 22:23:15 abcserver kernel: [   16.005336] vga16fb: mapped to 0xc00a0000
Nov 22 22:23:15 abcserver kernel: [   16.005339] vga16fb: not registering due to another framebuffer present
Nov 22 22:23:15 abcserver kernel: [   16.018357] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Nov 22 22:23:15 abcserver kernel: [   16.024970] EXT3 FS on sda5, internal journal
Nov 22 22:23:15 abcserver kernel: [   16.091533] input: HDA Digital PCBeep as /devices/pci0000:00/0000:00:1b.0/input/input3
Nov 22 22:23:15 abcserver kernel: [   16.124952] Console: switching to colour frame buffer device 180x56
Nov 22 22:23:15 abcserver kernel: [   16.370417] input: ImPS/2 Generic Wheel Mouse as /devices/platform/i8042/serio1/input/input4
Nov 22 22:23:15 abcserver kernel: [   16.444395] af9013: firmware version:4.95.0
Nov 22 22:23:15 abcserver kernel: [   16.447896] DVB: registering adapter 0 frontend 0 (Afatech AF9013 DVB-T)...
Nov 22 22:23:15 abcserver kernel: [   16.457396] MT2060: successfully identified (IF1 = 1220)
Nov 22 22:23:16 abcserver kernel: [   16.923293] dvb-usb: Afatech AF9015 DVB-T USB2.0 stick successfully initialized and connected.
Nov 22 22:23:16 abcserver kernel: [   16.932877] Afatech DVB-T 2: Fixing fullspeed to highspeed interval: 16 -> 8
Nov 22 22:23:16 abcserver kernel: [   16.933222] input: Afatech DVB-T 2 as /devices/pci0000:00/0000:00:1d.7/usb1/1-8/1-8:1.1/input/input5
Nov 22 22:23:16 abcserver kernel: [   16.933348] generic-usb 0003:15A4:9016.0001: input,hidraw0: USB HID v1.01 Keyboard [Afatech DVB-T 2] on usb-0000:00:1d.7-8/input1
Nov 22 22:23:16 abcserver kernel: [   16.933397] usbcore: registered new interface driver dvb_usb_af9015
Nov 22 22:23:16 abcserver kernel: [   16.956660] input: BTC USB Multimedia Keyboard as /devices/pci0000:00/0000:00:1d.3/usb5/5-1/5-1:1.0/input/input6
Nov 22 22:23:16 abcserver kernel: [   16.956799] generic-usb 0003:046E:52C0.0002: input,hidraw1: USB HID v1.10 Keyboard [BTC USB Multimedia Keyboard] on usb-0000:00:1d.3-1/input0
Nov 22 22:23:16 abcserver kernel: [   17.033389] input: BTC USB Multimedia Keyboard as /devices/pci0000:00/0000:00:1d.3/usb5/5-1/5-1:1.1/input/input7
Nov 22 22:23:16 abcserver kernel: [   17.033691] generic-usb 0003:046E:52C0.0003: input,hiddev96,hidraw2: USB HID v1.10 Device [BTC USB Multimedia Keyboard] on usb-0000:00:1d.3-1/input1
Nov 22 22:23:16 abcserver kernel: [   17.033726] usbcore: registered new interface driver usbhid
Nov 22 22:23:16 abcserver kernel: [   17.033729] usbhid: v2.6:USB HID core driver
Nov 22 22:23:38 abcserver kernel: [   39.369255] __ratelimit: 16 callbacks suppressed
Nov 22 22:23:38 abcserver kernel: [   39.369258] type=1505 audit(1290461018.477:6):  operation="profile_replace" pid=927 name="/sbin/dhclient3"
Nov 22 22:23:38 abcserver kernel: [   39.369893] type=1505 audit(1290461018.477:7):  operation="profile_replace" pid=927 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
Nov 22 22:23:38 abcserver kernel: [   39.370234] type=1505 audit(1290461018.477:8):  operation="profile_replace" pid=927 name="/usr/lib/connman/scripts/dhclient-script"
Nov 22 22:23:38 abcserver kernel: [   39.372006] type=1505 audit(1290461018.477:9):  operation="profile_load" pid=928 name="/usr/lib/cups/backend/cups-pdf"
Nov 22 22:23:38 abcserver kernel: [   39.372773] type=1505 audit(1290461018.477:10):  operation="profile_load" pid=928 name="/usr/sbin/cupsd"
Nov 22 22:23:38 abcserver kernel: [   39.375283] type=1505 audit(1290461018.481:11):  operation="profile_load" pid=929 name="/usr/sbin/mysqld"
Nov 22 22:23:38 abcserver kernel: [   39.377272] type=1505 audit(1290461018.485:12):  operation="profile_load" pid=930 name="/usr/sbin/named"
Nov 22 22:23:38 abcserver kernel: [   39.456828] type=1505 audit(1290461018.564:13):  operation="profile_replace" pid=931 name="/usr/sbin/ntpd"
Nov 22 22:23:38 abcserver kernel: [   39.459194] type=1505 audit(1290461018.564:14):  operation="profile_load" pid=932 name="/usr/sbin/slapd"
Nov 22 22:23:38 abcserver kernel: [   39.461458] type=1505 audit(1290461018.568:15):  operation="profile_load" pid=933 name="/usr/sbin/tcpdump"
[COLOR="Red"]Nov 22 22:23:59 abcserver kernel: [   60.528901] grep[985]: segfault at 8060322 ip 08060322 sp bfdd9508 error 15 in grep[8060000+1000]
[/COLOR]Nov 22 22:23:59 abcserver kernel: [   60.634128] S17mysql-ndb-mg[1065]: segfault at 810b4a6 ip 0810b4a6 sp bfcad338 error 15 in bash[810b000+1000]
Nov 22 22:23:59 abcserver kernel: [   60.635110] S18mysql-ndb[1066]: segfault at 810b4a6 ip 0810b4a6 sp bfacbaf8 error 15 in bash[810b000+1000]
Nov 22 22:23:59 abcserver kernel: [   60.689768] grep[1081]: segfault at 8060322 ip 08060322 sp bfc9b3c8 error 15 in grep[8060000+1000]
Nov 22 22:23:59 abcserver kernel: [   60.727395] type=1505 audit(1290461039.832:16):  operation="profile_replace" pid=1090 name="/usr/sbin/mysqld"
Nov 22 22:23:59 abcserver kernel: [   60.731495] df[1091]: segfault at 805833a ip 0805833a sp bf825998 error 15 in df[8058000+1000]
Nov 22 22:23:59 abcserver kernel: [   60.870115] RPC: Registered udp transport module.
Nov 22 22:23:59 abcserver kernel: [   60.870119] RPC: Registered tcp transport module.
Nov 22 22:23:59 abcserver kernel: [   60.870121] RPC: Registered tcp NFSv4.1 backchannel transport module.
Nov 22 22:24:00 abcserver kernel: [   60.892558] Installing knfsd (copyright (C) 1996 okir@monad.swb.de).
[COLOR="Red"]Nov 22 22:24:00 abcserver kernel: [   60.894178] grep[1125]: segfault at 8060322 ip 08060322 sp bfa1c218 error 15 in grep[8060000+1000]
[/COLOR][COLOR="Red"]Nov 22 22:24:00 abcserver kernel: [   60.900699] grep[1132]: segfault at 8060322 ip 08060322 sp bfc6b668 error 15 in grep[8060000+1000][/COLOR]
[COLOR="Red"]Nov 22 22:24:01 abcserver kernel: [   62.780110] debian-start[1095]: segfault at 810b4a6 ip 0810b4a6 sp bfb84c18 error 15 in bash[810b000+1000]
[/COLOR][COLOR="Red"]Nov 22 22:24:02 abcserver kernel: [   63.158866] grep[1215]: segfault at 8060322 ip 08060322 sp bfb21818 error 15 in grep[8060000+1000][/COLOR]
Nov 22 22:24:02 abcserver kernel: [   63.293392] lp0: using parport0 (interrupt-driven).
Nov 22 22:24:19 abcserver kernel: [   80.771003] __ratelimit: 9 callbacks suppressed
[COLOR="Red"]Nov 22 22:24:19 abcserver kernel: [   80.771008] grep[1350]: segfault at 8060322 ip 08060322 sp bff23ee8 error 15 in grep[8060000+1000]
[/COLOR][COLOR="Red"]Nov 22 22:24:21 abcserver kernel: [   82.525877] bash[1409]: segfault at 810b4a6 ip 0810b4a6 sp bfacef08 error 15 in bash[810b000+1000][/COLOR]
```

---

