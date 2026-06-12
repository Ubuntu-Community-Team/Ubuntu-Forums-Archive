---
title: "Radeon X1950XTX + Dell 3007WFP-HC = boot hang"
date: 2009-12-07
forum: General Help
---

### Post by CHaoSlayeR on 2009-12-07
Hi all,

I have a serious problem.

I want to finally get rid of the old CRT's I have here and replace them with a single 30" LCD. As I already have a Dell 3007WFP-HC at work working perfectly with a HD2400Pro and the radeon driver I thought this would be straight forward.

But the problem is as soon as I try to boot with the big Dell attached the boot hangs and is waiting for something. No progress bar, no splash, not even a blinking cursor. The display just remains black although the backlight is turned on. If I just unplug the monitor cable (and yes, it IS a Dual-Link) while the boot process stopped it continues immediately. No errors or warning in the logs.

But please have a look, maybe someone is able to see any problems during boot:

```

Dec  5 16:05:54 bitch kernel: [    0.000000] Initializing cgroup subsys cpuset
Dec  5 16:05:54 bitch kernel: [    0.000000] Initializing cgroup subsys cpu
Dec  5 16:05:54 bitch kernel: [    0.000000] Linux version 2.6.32-020632-generic (root@zinc) (gcc version 4.2.3 (Ubuntu 4.2.3-2ubuntu7)) #020632 SMP Thu Dec 3 10:09:58 UTC 2009
Dec  5 16:05:54 bitch kernel: [    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-2.6.32-020632-generic root=UUID=a012c7f4-6a94-4195-8616-3c8be07df5df ro quiet splash
Dec  5 16:05:54 bitch kernel: [    0.000000] KERNEL supported cpus:
Dec  5 16:05:54 bitch kernel: [    0.000000]   Intel GenuineIntel
Dec  5 16:05:54 bitch kernel: [    0.000000]   AMD AuthenticAMD
Dec  5 16:05:54 bitch kernel: [    0.000000]   Centaur CentaurHauls
Dec  5 16:05:54 bitch kernel: [    0.000000] BIOS-provided physical RAM map:
Dec  5 16:05:54 bitch kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
Dec  5 16:05:54 bitch kernel: [    0.000000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
Dec  5 16:05:54 bitch kernel: [    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
Dec  5 16:05:54 bitch kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 00000000cfde0000 (usable)
Dec  5 16:05:54 bitch kernel: [    0.000000]  BIOS-e820: 00000000cfde0000 - 00000000cfde3000 (ACPI NVS)
Dec  5 16:05:54 bitch kernel: [    0.000000]  BIOS-e820: 00000000cfde3000 - 00000000cfdf0000 (ACPI data)
Dec  5 16:05:54 bitch kernel: [    0.000000]  BIOS-e820: 00000000cfdf0000 - 00000000cfe00000 (reserved)
Dec  5 16:05:54 bitch kernel: [    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
Dec  5 16:05:54 bitch kernel: [    0.000000]  BIOS-e820: 00000000fec00000 - 0000000100000000 (reserved)
Dec  5 16:05:54 bitch kernel: [    0.000000]  BIOS-e820: 0000000100000000 - 0000000130000000 (usable)
Dec  5 16:05:54 bitch kernel: [    0.000000] DMI 2.4 present.
Dec  5 16:05:54 bitch kernel: [    0.000000] last_pfn = 0x130000 max_arch_pfn = 0x400000000
Dec  5 16:05:54 bitch kernel: [    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
Dec  5 16:05:54 bitch kernel: [    0.000000] last_pfn = 0xcfde0 max_arch_pfn = 0x400000000
Dec  5 16:05:54 bitch kernel: [    0.000000] Scanning 1 areas for low memory corruption
Dec  5 16:05:54 bitch kernel: [    0.000000] modified physical RAM map:
Dec  5 16:05:54 bitch kernel: [    0.000000]  modified: 0000000000000000 - 0000000000001000 (usable)
Dec  5 16:05:54 bitch kernel: [    0.000000]  modified: 0000000000001000 - 0000000000006000 (reserved)
Dec  5 16:05:54 bitch kernel: [    0.000000]  modified: 0000000000006000 - 000000000009f800 (usable)
Dec  5 16:05:54 bitch kernel: [    0.000000]  modified: 000000000009f800 - 00000000000a0000 (reserved)
Dec  5 16:05:54 bitch kernel: [    0.000000]  modified: 00000000000f0000 - 0000000000100000 (reserved)
Dec  5 16:05:54 bitch kernel: [    0.000000]  modified: 0000000000100000 - 00000000cfde0000 (usable)
Dec  5 16:05:54 bitch kernel: [    0.000000]  modified: 00000000cfde0000 - 00000000cfde3000 (ACPI NVS)
Dec  5 16:05:54 bitch kernel: [    0.000000]  modified: 00000000cfde3000 - 00000000cfdf0000 (ACPI data)
Dec  5 16:05:54 bitch kernel: [    0.000000]  modified: 00000000cfdf0000 - 00000000cfe00000 (reserved)
Dec  5 16:05:54 bitch kernel: [    0.000000]  modified: 00000000e0000000 - 00000000f0000000 (reserved)
Dec  5 16:05:54 bitch kernel: [    0.000000]  modified: 00000000fec00000 - 0000000100000000 (reserved)
Dec  5 16:05:54 bitch kernel: [    0.000000]  modified: 0000000100000000 - 0000000130000000 (usable)
Dec  5 16:05:54 bitch kernel: [    0.000000] Using GB pages for direct mapping
Dec  5 16:05:54 bitch kernel: [    0.000000] init_memory_mapping: 0000000000000000-00000000cfde0000
Dec  5 16:05:54 bitch kernel: [    0.000000] init_memory_mapping: 0000000100000000-0000000130000000
Dec  5 16:05:54 bitch kernel: [    0.000000] RAMDISK: 3777a000 - 37fefd8d
Dec  5 16:05:54 bitch kernel: [    0.000000] ACPI: RSDP 00000000000f7220 00014 (v00 GBT   )
Dec  5 16:05:54 bitch kernel: [    0.000000] ACPI: RSDT 00000000cfde3000 0003C (v01 GBT    GBTUACPI 42302E31 GBTU 01010101)
Dec  5 16:05:54 bitch kernel: [    0.000000] ACPI: FACP 00000000cfde3040 00074 (v01 GBT    GBTUACPI 42302E31 GBTU 01010101)
Dec  5 16:05:54 bitch kernel: [    0.000000] ACPI: DSDT 00000000cfde30c0 07299 (v01 GBT    GBTUACPI 00001000 MSFT 03000000)
Dec  5 16:05:54 bitch kernel: [    0.000000] ACPI: FACS 00000000cfde0000 00040
Dec  5 16:05:54 bitch kernel: [    0.000000] ACPI: SSDT 00000000cfdea440 0088C (v01 PTLTD  POWERNOW 00000001  LTP 00000001)
Dec  5 16:05:54 bitch kernel: [    0.000000] ACPI: HPET 00000000cfdead00 00038 (v01 GBT    GBTUACPI 42302E31 GBTU 00000098)
Dec  5 16:05:54 bitch kernel: [    0.000000] ACPI: MCFG 00000000cfdead40 0003C (v01 GBT    GBTUACPI 42302E31 GBTU 01010101)
Dec  5 16:05:54 bitch kernel: [    0.000000] ACPI: TAMG 00000000cfdead80 0029A (v01 GBT    GBT   B0 5455312E BG?? 53450101)
Dec  5 16:05:54 bitch kernel: [    0.000000] ACPI: APIC 00000000cfdea380 00084 (v01 GBT    GBTUACPI 42302E31 GBTU 01010101)
Dec  5 16:05:54 bitch kernel: [    0.000000] Scanning NUMA topology in Northbridge 24
Dec  5 16:05:54 bitch kernel: [    0.000000] No NUMA configuration found
Dec  5 16:05:54 bitch kernel: [    0.000000] Faking a node at 0000000000000000-0000000130000000
Dec  5 16:05:54 bitch kernel: [    0.000000] Bootmem setup node 0 0000000000000000-0000000130000000
Dec  5 16:05:54 bitch kernel: [    0.000000]   NODE_DATA [000000000000b000 - 000000000000ffff]
Dec  5 16:05:54 bitch kernel: [    0.000000]   bootmap [0000000000010000 -  0000000000035fff] pages 26
Dec  5 16:05:54 bitch kernel: [    0.000000] (8 early reservations) ==> bootmem [0000000000 - 0130000000]
Dec  5 16:05:54 bitch kernel: [    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
Dec  5 16:05:54 bitch kernel: [    0.000000]   #1 [0000006000 - 0000008000]       TRAMPOLINE ==> [0000006000 - 0000008000]
Dec  5 16:05:54 bitch kernel: [    0.000000]   #2 [0001000000 - 0001a2f784]    TEXT DATA BSS ==> [0001000000 - 0001a2f784]
Dec  5 16:05:54 bitch kernel: [    0.000000]   #3 [003777a000 - 0037fefd8d]          RAMDISK ==> [003777a000 - 0037fefd8d]
Dec  5 16:05:54 bitch kernel: [    0.000000]   #4 [000009f800 - 0000100000]    BIOS reserved ==> [000009f800 - 0000100000]
Dec  5 16:05:54 bitch kernel: [    0.000000]   #5 [0001a30000 - 0001a300fe]              BRK ==> [0001a30000 - 0001a300fe]
Dec  5 16:05:54 bitch kernel: [    0.000000]   #6 [0000008000 - 000000a000]          PGTABLE ==> [0000008000 - 000000a000]
Dec  5 16:05:54 bitch kernel: [    0.000000]   #7 [000000a000 - 000000b000]          PGTABLE ==> [000000a000 - 000000b000]
Dec  5 16:05:54 bitch kernel: [    0.000000] found SMP MP-table at [ffff8800000f5880] f5880
Dec  5 16:05:54 bitch kernel: [    0.000000] Zone PFN ranges:
Dec  5 16:05:54 bitch kernel: [    0.000000]   DMA      0x00000000 -> 0x00001000
Dec  5 16:05:54 bitch kernel: [    0.000000]   DMA32    0x00001000 -> 0x00100000
Dec  5 16:05:54 bitch kernel: [    0.000000]   Normal   0x00100000 -> 0x00130000
Dec  5 16:05:54 bitch kernel: [    0.000000] Movable zone start PFN for each node
Dec  5 16:05:54 bitch kernel: [    0.000000] early_node_map[4] active PFN ranges
Dec  5 16:05:54 bitch kernel: [    0.000000]     0: 0x00000000 -> 0x00000001
Dec  5 16:05:54 bitch kernel: [    0.000000]     0: 0x00000006 -> 0x0000009f
Dec  5 16:05:54 bitch kernel: [    0.000000]     0: 0x00000100 -> 0x000cfde0
Dec  5 16:05:54 bitch kernel: [    0.000000]     0: 0x00100000 -> 0x00130000
Dec  5 16:05:54 bitch kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x4008
Dec  5 16:05:54 bitch kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
Dec  5 16:05:54 bitch kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
Dec  5 16:05:54 bitch kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x02] enabled)
Dec  5 16:05:54 bitch kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x03] enabled)
Dec  5 16:05:54 bitch kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] dfl dfl lint[0x1])
Dec  5 16:05:54 bitch kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] dfl dfl lint[0x1])
Dec  5 16:05:54 bitch kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x02] dfl dfl lint[0x1])
Dec  5 16:05:54 bitch kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x03] dfl dfl lint[0x1])
Dec  5 16:05:54 bitch kernel: [    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
Dec  5 16:05:54 bitch kernel: [    0.000000] IOAPIC[0]: apic_id 2, version 33, address 0xfec00000, GSI 0-23
Dec  5 16:05:54 bitch kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
Dec  5 16:05:54 bitch kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 low level)
Dec  5 16:05:54 bitch kernel: [    0.000000] Using ACPI (MADT) for SMP configuration information
Dec  5 16:05:54 bitch kernel: [    0.000000] ACPI: HPET id: 0x10b9a201 base: 0xfed00000
Dec  5 16:05:54 bitch kernel: [    0.000000] SMP: Allowing 4 CPUs, 0 hotplug CPUs
Dec  5 16:05:54 bitch kernel: [    0.000000] PM: Registered nosave memory: 0000000000001000 - 0000000000006000
Dec  5 16:05:54 bitch kernel: [    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
Dec  5 16:05:54 bitch kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000f0000
Dec  5 16:05:54 bitch kernel: [    0.000000] PM: Registered nosave memory: 00000000000f0000 - 0000000000100000
Dec  5 16:05:54 bitch kernel: [    0.000000] PM: Registered nosave memory: 00000000cfde0000 - 00000000cfde3000
Dec  5 16:05:54 bitch kernel: [    0.000000] PM: Registered nosave memory: 00000000cfde3000 - 00000000cfdf0000
Dec  5 16:05:54 bitch kernel: [    0.000000] PM: Registered nosave memory: 00000000cfdf0000 - 00000000cfe00000
Dec  5 16:05:54 bitch kernel: [    0.000000] PM: Registered nosave memory: 00000000cfe00000 - 00000000e0000000
Dec  5 16:05:54 bitch kernel: [    0.000000] PM: Registered nosave memory: 00000000e0000000 - 00000000f0000000
Dec  5 16:05:54 bitch kernel: [    0.000000] PM: Registered nosave memory: 00000000f0000000 - 00000000fec00000
Dec  5 16:05:54 bitch kernel: [    0.000000] PM: Registered nosave memory: 00000000fec00000 - 0000000100000000
Dec  5 16:05:54 bitch kernel: [    0.000000] Allocating PCI resources starting at cfe00000 (gap: cfe00000:10200000)
Dec  5 16:05:54 bitch kernel: [    0.000000] Booting paravirtualized kernel on bare hardware
Dec  5 16:05:54 bitch kernel: [    0.000000] NR_CPUS:64 nr_cpumask_bits:64 nr_cpu_ids:4 nr_node_ids:1
Dec  5 16:05:54 bitch kernel: [    0.000000] PERCPU: Embedded 30 pages/cpu @ffff880028200000 s91288 r8192 d23400 u524288
Dec  5 16:05:54 bitch kernel: [    0.000000] pcpu-alloc: s91288 r8192 d23400 u524288 alloc=1*2097152
Dec  5 16:05:54 bitch kernel: [    0.000000] pcpu-alloc: [0] 0 1 2 3
Dec  5 16:05:54 bitch kernel: [    0.000000] Built 1 zonelists in Node order, mobility grouping on.  Total pages: 1030804
Dec  5 16:05:54 bitch kernel: [    0.000000] Policy zone: Normal
Dec  5 16:05:54 bitch kernel: [    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.32-020632-generic root=UUID=a012c7f4-6a94-4195-8616-3c8be07df5df ro quiet splash
Dec  5 16:05:54 bitch kernel: [    0.000000] PID hash table entries: 4096 (order: 3, 32768 bytes)
Dec  5 16:05:54 bitch kernel: [    0.000000] Initializing CPU#0
Dec  5 16:05:54 bitch kernel: [    0.000000] Checking aperture...
Dec  5 16:05:54 bitch kernel: [    0.000000] No AGP bridge found
Dec  5 16:05:54 bitch kernel: [    0.000000] Node 0: aperture @ 83c2000000 size 32 MB
Dec  5 16:05:54 bitch kernel: [    0.000000] Aperture beyond 4GB. Ignoring.
Dec  5 16:05:54 bitch kernel: [    0.000000] Your BIOS doesn't leave a aperture memory hole
Dec  5 16:05:54 bitch kernel: [    0.000000] Please enable the IOMMU option in the BIOS setup
Dec  5 16:05:54 bitch kernel: [    0.000000] This costs you 64 MB of RAM
Dec  5 16:05:54 bitch kernel: [    0.000000] Mapping aperture over 65536 KB of RAM @ 20000000
Dec  5 16:05:54 bitch kernel: [    0.000000] PM: Registered nosave memory: 0000000020000000 - 0000000024000000
Dec  5 16:05:54 bitch kernel: [    0.000000] Memory: 4046956k/4980736k available (5355k kernel code, 789016k absent, 144764k reserved, 3200k data, 728k init)
Dec  5 16:05:54 bitch kernel: [    0.000000] SLUB: Genslabs=14, HWalign=64, Order=0-3, MinObjects=0, CPUs=4, Nodes=1
Dec  5 16:05:54 bitch kernel: [    0.000000] Hierarchical RCU implementation.
Dec  5 16:05:54 bitch kernel: [    0.000000] NR_IRQS:4352 nr_irqs:440
Dec  5 16:05:54 bitch kernel: [    0.000000] Console: colour VGA+ 80x25
Dec  5 16:05:54 bitch kernel: [    0.000000] console [tty0] enabled
Dec  5 16:05:54 bitch kernel: [    0.000000] allocated 41943040 bytes of page_cgroup
Dec  5 16:05:54 bitch kernel: [    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
Dec  5 16:05:54 bitch kernel: [    0.000000] HPET: 4 timers in total, 1 timers will be used for per-cpu timer
Dec  5 16:05:54 bitch kernel: [    0.000000] Fast TSC calibration using PIT
Dec  5 16:05:54 bitch kernel: [    0.000000] Detected 2611.937 MHz processor.
Dec  5 16:05:54 bitch kernel: [    0.030006] Calibrating delay loop (skipped), value calculated using timer frequency.. 5223.86 BogoMIPS (lpj=26119340)
Dec  5 16:05:54 bitch kernel: [    0.030024] Security Framework initialized
Dec  5 16:05:54 bitch kernel: [    0.030029] SELinux:  Disabled at boot.
Dec  5 16:05:54 bitch kernel: [    0.030268] Dentry cache hash table entries: 524288 (order: 10, 4194304 bytes)
Dec  5 16:05:54 bitch kernel: [    0.040938] Inode-cache hash table entries: 262144 (order: 9, 2097152 bytes)
Dec  5 16:05:54 bitch kernel: [    0.041686] Mount-cache hash table entries: 256
Dec  5 16:05:54 bitch kernel: [    0.041810] Initializing cgroup subsys ns
Dec  5 16:05:54 bitch kernel: [    0.041813] Initializing cgroup subsys cpuacct
Dec  5 16:05:54 bitch kernel: [    0.041816] Initializing cgroup subsys memory
Dec  5 16:05:54 bitch kernel: [    0.041822] Initializing cgroup subsys freezer
Dec  5 16:05:54 bitch kernel: [    0.041824] Initializing cgroup subsys net_cls
Dec  5 16:05:54 bitch kernel: [    0.041840] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
Dec  5 16:05:54 bitch kernel: [    0.041842] CPU: L2 Cache: 512K (64 bytes/line)
Dec  5 16:05:54 bitch kernel: [    0.041844] CPU 0/0x0 -> Node 0
Dec  5 16:05:54 bitch kernel: [    0.041848] CPU: Physical Processor ID: 0
Dec  5 16:05:54 bitch kernel: [    0.041849] CPU: Processor Core ID: 0
Dec  5 16:05:54 bitch kernel: [    0.041852] mce: CPU supports 6 MCE banks
Dec  5 16:05:54 bitch kernel: [    0.041861] using C1E aware idle routine
Dec  5 16:05:54 bitch kernel: [    0.041862] Performance Events: AMD PMU driver.
Dec  5 16:05:54 bitch kernel: [    0.041867] ... version:                0
Dec  5 16:05:54 bitch kernel: [    0.041868] ... bit width:              48
Dec  5 16:05:54 bitch kernel: [    0.041869] ... generic registers:      4
Dec  5 16:05:54 bitch kernel: [    0.041870] ... value mask:             0000ffffffffffff
Dec  5 16:05:54 bitch kernel: [    0.041872] ... max period:             00007fffffffffff
Dec  5 16:05:54 bitch kernel: [    0.041873] ... fixed-purpose events:   0
Dec  5 16:05:54 bitch kernel: [    0.041874] ... event mask:             000000000000000f
Dec  5 16:05:54 bitch kernel: [    0.043236] ACPI: Core revision 20090903
Dec  5 16:05:54 bitch kernel: [    0.060070] Setting APIC routing to flat
Dec  5 16:05:54 bitch kernel: [    0.060546] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
Dec  5 16:05:54 bitch kernel: [    0.161572] CPU0: AMD Athlon(tm) II X4 620 Processor stepping 02
Dec  5 16:05:54 bitch kernel: [    0.170000] Booting processor 1 APIC 0x1 ip 0x6000
Dec  5 16:05:54 bitch kernel: [    0.040000] Initializing CPU#1
Dec  5 16:05:54 bitch kernel: [    0.040000] Calibrating delay using timer specific routine.. 5223.67 BogoMIPS (lpj=26118380)
Dec  5 16:05:54 bitch kernel: [    0.040000] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
Dec  5 16:05:54 bitch kernel: [    0.040000] CPU: L2 Cache: 512K (64 bytes/line)
Dec  5 16:05:54 bitch kernel: [    0.040000] CPU 1/0x1 -> Node 0
Dec  5 16:05:54 bitch kernel: [    0.040000] CPU: Physical Processor ID: 0
Dec  5 16:05:54 bitch kernel: [    0.040000] CPU: Processor Core ID: 1
Dec  5 16:05:54 bitch kernel: [    0.320106] CPU1: AMD Athlon(tm) II X4 620 Processor stepping 02
Dec  5 16:05:54 bitch kernel: [    0.320112] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
Dec  5 16:05:54 bitch kernel: [    0.330023] System has AMD C1E enabled
Dec  5 16:05:54 bitch kernel: [    0.330037] Switch to broadcast mode on CPU1
Dec  5 16:05:54 bitch kernel: [    0.330057] Booting processor 2 APIC 0x2 ip 0x6000
Dec  5 16:05:54 bitch kernel: [    0.040000] Initializing CPU#2
Dec  5 16:05:54 bitch kernel: [    0.040000] Calibrating delay using timer specific routine.. 5223.65 BogoMIPS (lpj=26118287)
Dec  5 16:05:54 bitch kernel: [    0.040000] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
Dec  5 16:05:54 bitch kernel: [    0.040000] CPU: L2 Cache: 512K (64 bytes/line)
Dec  5 16:05:54 bitch kernel: [    0.040000] CPU 2/0x2 -> Node 0
Dec  5 16:05:54 bitch kernel: [    0.040000] CPU: Physical Processor ID: 0
Dec  5 16:05:54 bitch kernel: [    0.040000] CPU: Processor Core ID: 3
Dec  5 16:05:54 bitch kernel: [    0.490027] CPU2: AMD Athlon(tm) II X4 620 Processor stepping 02
Dec  5 16:05:54 bitch kernel: [    0.490033] checking TSC synchronization [CPU#0 -> CPU#2]: passed.
Dec  5 16:05:54 bitch kernel: [    0.500027] Switch to broadcast mode on CPU2
Dec  5 16:05:54 bitch kernel: [    0.500061] Booting processor 3 APIC 0x3 ip 0x6000
Dec  5 16:05:54 bitch kernel: [    0.040000] Initializing CPU#3
Dec  5 16:05:54 bitch kernel: [    0.040000] Calibrating delay using timer specific routine.. 5223.68 BogoMIPS (lpj=26118424)
Dec  5 16:05:54 bitch kernel: [    0.040000] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
Dec  5 16:05:54 bitch kernel: [    0.040000] CPU: L2 Cache: 512K (64 bytes/line)
Dec  5 16:05:54 bitch kernel: [    0.040000] CPU 3/0x3 -> Node 0
Dec  5 16:05:54 bitch kernel: [    0.040000] CPU: Physical Processor ID: 0
Dec  5 16:05:54 bitch kernel: [    0.040000] CPU: Processor Core ID: 2
Dec  5 16:05:54 bitch kernel: [    0.660049] CPU3: AMD Athlon(tm) II X4 620 Processor stepping 02
Dec  5 16:05:54 bitch kernel: [    0.660054] checking TSC synchronization [CPU#0 -> CPU#3]: passed.
Dec  5 16:05:54 bitch kernel: [    0.670019] Brought up 4 CPUs
Dec  5 16:05:54 bitch kernel: [    0.670021] Total of 4 processors activated (20894.88 BogoMIPS).
Dec  5 16:05:54 bitch kernel: [    0.670021] Switch to broadcast mode on CPU3
Dec  5 16:05:54 bitch kernel: [    0.670513] Switch to broadcast mode on CPU0
Dec  5 16:05:54 bitch kernel: [    0.670513] regulator: core version 0.5
Dec  5 16:05:54 bitch kernel: [    0.670513] Time: 15:02:50  Date: 12/05/09
Dec  5 16:05:54 bitch kernel: [    0.670513] NET: Registered protocol family 16
Dec  5 16:05:54 bitch kernel: [    0.670513] TOM: 00000000d0000000 aka 3328M
Dec  5 16:05:54 bitch kernel: [    0.670513] TOM2: 0000000130000000 aka 4864M
Dec  5 16:05:54 bitch kernel: [    0.670513] ACPI: bus type pci registered
Dec  5 16:05:54 bitch kernel: [    0.670513] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 255
Dec  5 16:05:54 bitch kernel: [    0.670513] PCI: MCFG area at e0000000 reserved in E820
Dec  5 16:05:54 bitch kernel: [    0.676505] PCI: Using MMCONFIG at e0000000 - efffffff
Dec  5 16:05:54 bitch kernel: [    0.676508] PCI: Using configuration type 1 for base access
Dec  5 16:05:54 bitch kernel: [    0.677067] bio: create slab <bio-0> at 0
Dec  5 16:05:54 bitch kernel: [    0.677067] ACPI: Interpreter enabled
Dec  5 16:05:54 bitch kernel: [    0.677067] ACPI: (supports S0 S3 S4 S5)
Dec  5 16:05:54 bitch kernel: [    0.677067] ACPI: Using IOAPIC for interrupt routing
Dec  5 16:05:54 bitch kernel: [    0.679041] ACPI: No dock devices found.
Dec  5 16:05:54 bitch kernel: [    0.679140] ACPI: PCI Root Bridge [PCI0] (0000:00)
Dec  5 16:05:54 bitch kernel: [    0.679231] pci 0000:00:02.0: PME# supported from D0 D3hot D3cold
Dec  5 16:05:54 bitch kernel: [    0.679234] pci 0000:00:02.0: PME# disabled
Dec  5 16:05:54 bitch kernel: [    0.679270] pci 0000:00:0a.0: PME# supported from D0 D3hot D3cold
Dec  5 16:05:54 bitch kernel: [    0.679273] pci 0000:00:0a.0: PME# disabled
Dec  5 16:05:54 bitch kernel: [    0.679560] pci 0000:00:12.2: PME# supported from D0 D1 D2 D3hot
Dec  5 16:05:54 bitch kernel: [    0.679564] pci 0000:00:12.2: PME# disabled
Dec  5 16:05:54 bitch kernel: [    0.679757] pci 0000:00:13.2: PME# supported from D0 D1 D2 D3hot
Dec  5 16:05:54 bitch kernel: [    0.679761] pci 0000:00:13.2: PME# disabled
Dec  5 16:05:54 bitch kernel: [    0.679989] pci 0000:00:14.2: PME# supported from D0 D3hot D3cold
Dec  5 16:05:54 bitch kernel: [    0.679992] pci 0000:00:14.2: PME# disabled
Dec  5 16:05:54 bitch kernel: [    0.680461] pci 0000:02:00.0: PME# supported from D0 D1 D2 D3hot D3cold
Dec  5 16:05:54 bitch kernel: [    0.680465] pci 0000:02:00.0: PME# disabled
Dec  5 16:05:54 bitch kernel: [    0.680650] pci 0000:03:0e.0: PME# supported from D0 D1 D2 D3hot
Dec  5 16:05:54 bitch kernel: [    0.680655] pci 0000:03:0e.0: PME# disabled
Dec  5 16:05:54 bitch kernel: [    0.680687] pci 0000:00:14.4: transparent bridge
Dec  5 16:05:54 bitch kernel: [    0.700284] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 10 11) *0, disabled.
Dec  5 16:05:54 bitch kernel: [    0.700362] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 10 11) *0, disabled.
Dec  5 16:05:54 bitch kernel: [    0.700435] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 10 11) *0, disabled.
Dec  5 16:05:54 bitch kernel: [    0.700510] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 10 11) *0, disabled.
Dec  5 16:05:54 bitch kernel: [    0.700585] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 10 11) *0, disabled.
Dec  5 16:05:54 bitch kernel: [    0.700660] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 10 11) *0, disabled.
Dec  5 16:05:54 bitch kernel: [    0.700734] ACPI: PCI Interrupt Link [LNK0] (IRQs 3 4 5 6 7 10 11) *0, disabled.
Dec  5 16:05:54 bitch kernel: [    0.700809] ACPI: PCI Interrupt Link [LNK1] (IRQs 3 4 5 6 7 10 11) *0, disabled.
Dec  5 16:05:54 bitch kernel: [    0.700885] vgaarb: device added: PCI:0000:01:00.0,decodes=io+mem,owns=io+mem,locks=none
Dec  5 16:05:54 bitch kernel: [    0.700888] vgaarb: loaded
Dec  5 16:05:54 bitch kernel: [    0.700982] SCSI subsystem initialized
Dec  5 16:05:54 bitch kernel: [    0.710047] usbcore: registered new interface driver usbfs
Dec  5 16:05:54 bitch kernel: [    0.710047] usbcore: registered new interface driver hub
Dec  5 16:05:54 bitch kernel: [    0.710047] usbcore: registered new device driver usb
Dec  5 16:05:54 bitch kernel: [    0.710047] ACPI: WMI: Mapper loaded
Dec  5 16:05:54 bitch kernel: [    0.710047] PCI: Using ACPI for IRQ routing
Dec  5 16:05:54 bitch kernel: [    0.710079] pci 0000:00:00.0: BAR 3: can't allocate resource
Dec  5 16:05:54 bitch kernel: [    0.710206] Bluetooth: Core ver 2.15
Dec  5 16:05:54 bitch kernel: [    0.710213] NET: Registered protocol family 31
Dec  5 16:05:54 bitch kernel: [    0.710213] Bluetooth: HCI device and connection manager initialized
Dec  5 16:05:54 bitch kernel: [    0.710213] Bluetooth: HCI socket layer initialized
Dec  5 16:05:54 bitch kernel: [    0.710213] NetLabel: Initializing
Dec  5 16:05:54 bitch kernel: [    0.710213] NetLabel:  domain hash size = 128
Dec  5 16:05:54 bitch kernel: [    0.710213] NetLabel:  protocols = UNLABELED CIPSOv4
Dec  5 16:05:54 bitch kernel: [    0.710213] NetLabel:  unlabeled traffic allowed by default
Dec  5 16:05:54 bitch kernel: [    0.710213] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 24, 0
Dec  5 16:05:54 bitch kernel: [    0.710213] hpet0: 4 comparators, 32-bit 14.318180 MHz counter
Dec  5 16:05:54 bitch kernel: [    0.750010] Switching to clocksource tsc
Dec  5 16:05:54 bitch kernel: [    0.761173] pnp: PnP ACPI init
Dec  5 16:05:54 bitch kernel: [    0.761196] ACPI: bus type pnp registered
Dec  5 16:05:54 bitch kernel: [    0.763110] pnp 00:0a: mem resource (0xd1a00-0xd3fff) overlaps 0000:00:00.0 BAR 3 (0x0-0x1fffffff), disabling
Dec  5 16:05:54 bitch kernel: [    0.763113] pnp 00:0a: mem resource (0xf0000-0xf7fff) overlaps 0000:00:00.0 BAR 3 (0x0-0x1fffffff), disabling
Dec  5 16:05:54 bitch kernel: [    0.763116] pnp 00:0a: mem resource (0xf8000-0xfbfff) overlaps 0000:00:00.0 BAR 3 (0x0-0x1fffffff), disabling
Dec  5 16:05:54 bitch kernel: [    0.763118] pnp 00:0a: mem resource (0xfc000-0xfffff) overlaps 0000:00:00.0 BAR 3 (0x0-0x1fffffff), disabling
Dec  5 16:05:54 bitch kernel: [    0.763121] pnp 00:0a: mem resource (0x0-0x9ffff) overlaps 0000:00:00.0 BAR 3 (0x0-0x1fffffff), disabling
Dec  5 16:05:54 bitch kernel: [    0.763124] pnp 00:0a: mem resource (0x100000-0xcfddffff) overlaps 0000:00:00.0 BAR 3 (0x0-0x1fffffff), disabling
Dec  5 16:05:54 bitch kernel: [    0.763198] pnp: PnP ACPI: found 11 devices
Dec  5 16:05:54 bitch kernel: [    0.763199] ACPI: ACPI bus type pnp unregistered
Dec  5 16:05:54 bitch kernel: [    0.763209] system 00:01: ioport range 0x4d0-0x4d1 has been reserved
Dec  5 16:05:54 bitch kernel: [    0.763211] system 00:01: ioport range 0x220-0x225 has been reserved
Dec  5 16:05:54 bitch kernel: [    0.763213] system 00:01: ioport range 0x290-0x294 has been reserved
Dec  5 16:05:54 bitch kernel: [    0.763217] system 00:02: ioport range 0x4100-0x411f has been reserved
Dec  5 16:05:54 bitch kernel: [    0.763219] system 00:02: ioport range 0x228-0x22f has been reserved
Dec  5 16:05:54 bitch kernel: [    0.763221] system 00:02: ioport range 0x40b-0x40b has been reserved
Dec  5 16:05:54 bitch kernel: [    0.763223] system 00:02: ioport range 0x4d6-0x4d6 has been reserved
Dec  5 16:05:54 bitch kernel: [    0.763225] system 00:02: ioport range 0xc00-0xc01 has been reserved
Dec  5 16:05:54 bitch kernel: [    0.763227] system 00:02: ioport range 0xc14-0xc14 has been reserved
Dec  5 16:05:54 bitch kernel: [    0.763229] system 00:02: ioport range 0xc50-0xc52 has been reserved
Dec  5 16:05:54 bitch kernel: [    0.763231] system 00:02: ioport range 0xc6c-0xc6d has been reserved
Dec  5 16:05:54 bitch kernel: [    0.763233] system 00:02: ioport range 0xc6f-0xc6f has been reserved
Dec  5 16:05:54 bitch kernel: [    0.763236] system 00:02: ioport range 0xcd0-0xcd1 has been reserved
Dec  5 16:05:54 bitch kernel: [    0.763238] system 00:02: ioport range 0xcd2-0xcd3 has been reserved
Dec  5 16:05:54 bitch kernel: [    0.763240] system 00:02: ioport range 0xcd4-0xcdf has been reserved
Dec  5 16:05:54 bitch kernel: [    0.763242] system 00:02: ioport range 0x4000-0x40fe has been reserved
Dec  5 16:05:54 bitch kernel: [    0.763244] system 00:02: ioport range 0x4210-0x4217 has been reserved
Dec  5 16:05:54 bitch kernel: [    0.763246] system 00:02: ioport range 0xb00-0xb0f has been reserved
Dec  5 16:05:54 bitch kernel: [    0.763248] system 00:02: ioport range 0xb10-0xb1f has been reserved
Dec  5 16:05:54 bitch kernel: [    0.763250] system 00:02: ioport range 0xb20-0xb3f has been reserved
Dec  5 16:05:54 bitch kernel: [    0.763255] system 00:09: iomem range 0xe0000000-0xefffffff has been reserved
Dec  5 16:05:54 bitch kernel: [    0.763259] system 00:0a: iomem range 0xcfde0000-0xcfdfffff could not be reserved
Dec  5 16:05:54 bitch kernel: [    0.763261] system 00:0a: iomem range 0xffff0000-0xffffffff has been reserved
Dec  5 16:05:54 bitch kernel: [    0.763264] system 00:0a: iomem range 0xfec00000-0xfec00fff could not be reserved
Dec  5 16:05:54 bitch kernel: [    0.763266] system 00:0a: iomem range 0xfee00000-0xfee00fff has been reserved
Dec  5 16:05:54 bitch kernel: [    0.763268] system 00:0a: iomem range 0xfff80000-0xfffeffff has been reserved
Dec  5 16:05:54 bitch kernel: [    0.767917] pci 0000:00:02.0: PCI bridge, secondary bus 0000:01
Dec  5 16:05:54 bitch kernel: [    0.767919] pci 0000:00:02.0:   IO window: 0xe000-0xefff
Dec  5 16:05:54 bitch kernel: [    0.767922] pci 0000:00:02.0:   MEM window: 0xfdf00000-0xfdffffff
Dec  5 16:05:54 bitch kernel: [    0.767924] pci 0000:00:02.0:   PREFETCH window: 0x000000d0000000-0x000000dfffffff
Dec  5 16:05:54 bitch kernel: [    0.767928] pci 0000:00:0a.0: PCI bridge, secondary bus 0000:02
Dec  5 16:05:54 bitch kernel: [    0.767931] pci 0000:00:0a.0:   IO window: 0xd000-0xdfff
Dec  5 16:05:54 bitch kernel: [    0.767933] pci 0000:00:0a.0:   MEM window: 0xfde00000-0xfdefffff
Dec  5 16:05:54 bitch kernel: [    0.767936] pci 0000:00:0a.0:   PREFETCH window: 0x000000fdb00000-0x000000fdbfffff
Dec  5 16:05:54 bitch kernel: [    0.767939] pci 0000:00:14.4: PCI bridge, secondary bus 0000:03
Dec  5 16:05:54 bitch kernel: [    0.767942] pci 0000:00:14.4:   IO window: 0xc000-0xcfff
Dec  5 16:05:54 bitch kernel: [    0.767946] pci 0000:00:14.4:   MEM window: 0xfdd00000-0xfddfffff
Dec  5 16:05:54 bitch kernel: [    0.767950] pci 0000:00:14.4:   PREFETCH window: 0xfdc00000-0xfdcfffff
Dec  5 16:05:54 bitch kernel: [    0.767968] pci 0000:00:02.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
Dec  5 16:05:54 bitch kernel: [    0.767976] pci 0000:00:0a.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
Dec  5 16:05:54 bitch kernel: [    0.768043] NET: Registered protocol family 2
Dec  5 16:05:54 bitch kernel: [    0.768170] IP route cache hash table entries: 131072 (order: 8, 1048576 bytes)
Dec  5 16:05:54 bitch kernel: [    0.769150] TCP established hash table entries: 524288 (order: 11, 8388608 bytes)
Dec  5 16:05:54 bitch kernel: [    0.772495] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
Dec  5 16:05:54 bitch kernel: [    0.772905] TCP: Hash tables configured (established 524288 bind 65536)
Dec  5 16:05:54 bitch kernel: [    0.772908] TCP reno registered
Dec  5 16:05:54 bitch kernel: [    0.773010] NET: Registered protocol family 1
Dec  5 16:05:54 bitch kernel: [    0.949927] Trying to unpack rootfs image as initramfs...
Dec  5 16:05:54 bitch kernel: [    1.110752] Freeing initrd memory: 8663k freed
Dec  5 16:05:54 bitch kernel: [    1.114256] PCI-DMA: Disabling AGP.
Dec  5 16:05:54 bitch kernel: [    1.114370] PCI-DMA: aperture base @ 20000000 size 65536 KB
Dec  5 16:05:54 bitch kernel: [    1.114371] PCI-DMA: using GART IOMMU.
Dec  5 16:05:54 bitch kernel: [    1.114374] PCI-DMA: Reserving 64MB of IOMMU area in the AGP aperture
Dec  5 16:05:54 bitch kernel: [    1.115661] Scanning for low memory corruption every 60 seconds
Dec  5 16:05:54 bitch kernel: [    1.115769] audit: initializing netlink socket (disabled)
Dec  5 16:05:54 bitch kernel: [    1.115779] type=2000 audit(1260025371.110:1): initialized
Dec  5 16:05:54 bitch kernel: [    1.123462] HugeTLB registered 2 MB page size, pre-allocated 0 pages
Dec  5 16:05:54 bitch kernel: [    1.124573] VFS: Disk quotas dquot_6.5.2
Dec  5 16:05:54 bitch kernel: [    1.124614] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
Dec  5 16:05:54 bitch kernel: [    1.125115] fuse init (API version 7.13)
Dec  5 16:05:54 bitch kernel: [    1.125170] msgmni has been set to 7921
Dec  5 16:05:54 bitch kernel: [    1.125435] alg: No test for stdrng (krng)
Dec  5 16:05:54 bitch kernel: [    1.125446] io scheduler noop registered
Dec  5 16:05:54 bitch kernel: [    1.125448] io scheduler anticipatory registered
Dec  5 16:05:54 bitch kernel: [    1.125450] io scheduler deadline registered
Dec  5 16:05:54 bitch kernel: [    1.125478] io scheduler cfq registered (default)
Dec  5 16:05:54 bitch kernel: [    1.125777] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Dec  5 16:05:54 bitch kernel: [    1.125800] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
Dec  5 16:05:54 bitch kernel: [    1.125896] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0
Dec  5 16:05:54 bitch kernel: [    1.125899] ACPI: Power Button [PWRB]
Dec  5 16:05:54 bitch kernel: [    1.125938] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
Dec  5 16:05:54 bitch kernel: [    1.125940] ACPI: Power Button [PWRF]
Dec  5 16:05:54 bitch kernel: [    1.126216] processor LNXCPU:00: registered as cooling_device0
Dec  5 16:05:54 bitch kernel: [    1.126256] processor LNXCPU:01: registered as cooling_device1
Dec  5 16:05:54 bitch kernel: [    1.126293] processor LNXCPU:02: registered as cooling_device2
Dec  5 16:05:54 bitch kernel: [    1.126319] processor LNXCPU:03: registered as cooling_device3
Dec  5 16:05:54 bitch kernel: [    1.128876] Linux agpgart interface v0.103
Dec  5 16:05:54 bitch kernel: [    1.128880] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
Dec  5 16:05:54 bitch kernel: [    1.129689] brd: module loaded
Dec  5 16:05:54 bitch kernel: [    1.129985] loop: module loaded
Dec  5 16:05:54 bitch kernel: [    1.130053] input: Macintosh mouse button emulation as /devices/virtual/input/input2
Dec  5 16:05:54 bitch kernel: [    1.130247] ahci 0000:00:11.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
Dec  5 16:05:54 bitch kernel: [    1.130382] ahci 0000:00:11.0: AHCI 0001.0100 32 slots 6 ports 3 Gbps 0x3f impl SATA mode
Dec  5 16:05:54 bitch kernel: [    1.130386] ahci 0000:00:11.0: flags: 64bit ncq sntf ilck pm led clo pmp pio slum part ccc
Dec  5 16:05:54 bitch kernel: [    1.130852] scsi0 : ahci
Dec  5 16:05:54 bitch kernel: [    1.130961] scsi1 : ahci
Dec  5 16:05:54 bitch kernel: [    1.131006] scsi2 : ahci
Dec  5 16:05:54 bitch kernel: [    1.131047] scsi3 : ahci
Dec  5 16:05:54 bitch kernel: [    1.131090] scsi4 : ahci
Dec  5 16:05:54 bitch kernel: [    1.131131] scsi5 : ahci
Dec  5 16:05:54 bitch kernel: [    1.131259] ata1: SATA max UDMA/133 irq 22
Dec  5 16:05:54 bitch kernel: [    1.131262] ata2: SATA max UDMA/133 abar m1024@0xfe02f000 port 0xfe02f180 irq 22
Dec  5 16:05:54 bitch kernel: [    1.131265] ata3: SATA max UDMA/133 abar m1024@0xfe02f000 port 0xfe02f200 irq 22
Dec  5 16:05:54 bitch kernel: [    1.131268] ata4: SATA max UDMA/133 abar m1024@0xfe02f000 port 0xfe02f280 irq 22
Dec  5 16:05:54 bitch kernel: [    1.131272] ata5: SATA max UDMA/133 abar m1024@0xfe02f000 port 0xfe02f300 irq 22
Dec  5 16:05:54 bitch kernel: [    1.131275] ata6: SATA max UDMA/133 abar m1024@0xfe02f000 port 0xfe02f380 irq 22
Dec  5 16:05:54 bitch kernel: [    1.131574] pata_atiixp 0000:00:14.1: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Dec  5 16:05:54 bitch kernel: [    1.131669] scsi6 : pata_atiixp
Dec  5 16:05:54 bitch kernel: [    1.131712] scsi7 : pata_atiixp
Dec  5 16:05:54 bitch kernel: [    1.132521] ata7: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xfa00 irq 14
Dec  5 16:05:54 bitch kernel: [    1.132523] ata8: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xfa08 irq 15
Dec  5 16:05:54 bitch kernel: [    1.133030] Fixed MDIO Bus: probed
Dec  5 16:05:54 bitch kernel: [    1.133081] PPP generic driver version 2.4.2
Dec  5 16:05:54 bitch kernel: [    1.133161] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
Dec  5 16:05:54 bitch kernel: [    1.133284] ehci_hcd 0000:00:12.2: PCI INT B -> GSI 17 (level, low) -> IRQ 17
Dec  5 16:05:54 bitch kernel: [    1.133304] ehci_hcd 0000:00:12.2: EHCI Host Controller
Dec  5 16:05:54 bitch kernel: [    1.133368] ehci_hcd 0000:00:12.2: new USB bus registered, assigned bus number 1
Dec  5 16:05:54 bitch kernel: [    1.133399] ehci_hcd 0000:00:12.2: debug port 1
Dec  5 16:05:54 bitch kernel: [    1.133427] ehci_hcd 0000:00:12.2: irq 17, io mem 0xfe02c000
Dec  5 16:05:54 bitch kernel: [    1.150124] ehci_hcd 0000:00:12.2: USB 2.0 started, EHCI 1.00
Dec  5 16:05:54 bitch kernel: [    1.150175] usb usb1: configuration #1 chosen from 1 choice
Dec  5 16:05:54 bitch kernel: [    1.150196] hub 1-0:1.0: USB hub found
Dec  5 16:05:54 bitch kernel: [    1.150201] hub 1-0:1.0: 6 ports detected
Dec  5 16:05:54 bitch kernel: [    1.150287] ehci_hcd 0000:00:13.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
Dec  5 16:05:54 bitch kernel: [    1.150297] ehci_hcd 0000:00:13.2: EHCI Host Controller
Dec  5 16:05:54 bitch kernel: [    1.150321] ehci_hcd 0000:00:13.2: new USB bus registered, assigned bus number 2
Dec  5 16:05:54 bitch kernel: [    1.150346] ehci_hcd 0000:00:13.2: debug port 1
Dec  5 16:05:54 bitch kernel: [    1.150369] ehci_hcd 0000:00:13.2: irq 19, io mem 0xfe029000
Dec  5 16:05:54 bitch kernel: [    1.160128] ehci_hcd 0000:00:13.2: USB 2.0 started, EHCI 1.00
Dec  5 16:05:54 bitch kernel: [    1.160166] usb usb2: configuration #1 chosen from 1 choice
Dec  5 16:05:54 bitch kernel: [    1.160183] hub 2-0:1.0: USB hub found
Dec  5 16:05:54 bitch kernel: [    1.160187] hub 2-0:1.0: 6 ports detected
Dec  5 16:05:54 bitch kernel: [    1.160239] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
Dec  5 16:05:54 bitch kernel: [    1.160270] ohci_hcd 0000:00:12.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Dec  5 16:05:54 bitch kernel: [    1.160279] ohci_hcd 0000:00:12.0: OHCI Host Controller
Dec  5 16:05:54 bitch kernel: [    1.160301] ohci_hcd 0000:00:12.0: new USB bus registered, assigned bus number 3
Dec  5 16:05:54 bitch kernel: [    1.160327] ohci_hcd 0000:00:12.0: irq 16, io mem 0xfe02e000
Dec  5 16:05:54 bitch kernel: [    1.224170] usb usb3: configuration #1 chosen from 1 choice
Dec  5 16:05:54 bitch kernel: [    1.224186] hub 3-0:1.0: USB hub found
Dec  5 16:05:54 bitch kernel: [    1.224193] hub 3-0:1.0: 3 ports detected
Dec  5 16:05:54 bitch kernel: [    1.224314] ohci_hcd 0000:00:12.1: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Dec  5 16:05:54 bitch kernel: [    1.224322] ohci_hcd 0000:00:12.1: OHCI Host Controller
Dec  5 16:05:54 bitch kernel: [    1.224351] ohci_hcd 0000:00:12.1: new USB bus registered, assigned bus number 4
Dec  5 16:05:54 bitch kernel: [    1.224365] ohci_hcd 0000:00:12.1: irq 16, io mem 0xfe02d000
Dec  5 16:05:54 bitch kernel: [    1.284164] usb usb4: configuration #1 chosen from 1 choice
Dec  5 16:05:54 bitch kernel: [    1.284182] hub 4-0:1.0: USB hub found
Dec  5 16:05:54 bitch kernel: [    1.284189] hub 4-0:1.0: 3 ports detected
Dec  5 16:05:54 bitch kernel: [    1.284307] ohci_hcd 0000:00:13.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
Dec  5 16:05:54 bitch kernel: [    1.284316] ohci_hcd 0000:00:13.0: OHCI Host Controller
Dec  5 16:05:54 bitch kernel: [    1.284338] ohci_hcd 0000:00:13.0: new USB bus registered, assigned bus number 5
Dec  5 16:05:54 bitch kernel: [    1.284363] ohci_hcd 0000:00:13.0: irq 18, io mem 0xfe02b000
Dec  5 16:05:54 bitch kernel: [    1.320657] ata7.00: ATAPI: HL-DT-STDVD-RAM GSA-H55N, 1.03, max UDMA/66
Dec  5 16:05:54 bitch kernel: [    1.320678] ata7.01: ATAPI: TSSTcorpCD/DVDW SH-S182M, SB02, max UDMA/33
Dec  5 16:05:54 bitch kernel: [    1.344264] usb usb5: configuration #1 chosen from 1 choice
Dec  5 16:05:54 bitch kernel: [    1.344286] hub 5-0:1.0: USB hub found
Dec  5 16:05:54 bitch kernel: [    1.344296] hub 5-0:1.0: 3 ports detected
Dec  5 16:05:54 bitch kernel: [    1.344442] ohci_hcd 0000:00:13.1: PCI INT A -> GSI 18 (level, low) -> IRQ 18
Dec  5 16:05:54 bitch kernel: [    1.344461] ohci_hcd 0000:00:13.1: OHCI Host Controller
Dec  5 16:05:54 bitch kernel: [    1.344489] ohci_hcd 0000:00:13.1: new USB bus registered, assigned bus number 6
Dec  5 16:05:54 bitch kernel: [    1.344508] ohci_hcd 0000:00:13.1: irq 18, io mem 0xfe02a000
Dec  5 16:05:54 bitch kernel: [    1.361860] ata7.00: configured for UDMA/66
Dec  5 16:05:54 bitch kernel: [    1.401698] ata7.01: configured for UDMA/33
Dec  5 16:05:54 bitch kernel: [    1.404235] usb usb6: configuration #1 chosen from 1 choice
Dec  5 16:05:54 bitch kernel: [    1.404257] hub 6-0:1.0: USB hub found
Dec  5 16:05:54 bitch kernel: [    1.404266] hub 6-0:1.0: 3 ports detected
Dec  5 16:05:54 bitch kernel: [    1.404413] ohci_hcd 0000:00:14.5: PCI INT C -> GSI 18 (level, low) -> IRQ 18
Dec  5 16:05:54 bitch kernel: [    1.404435] ohci_hcd 0000:00:14.5: OHCI Host Controller
Dec  5 16:05:54 bitch kernel: [    1.404466] ohci_hcd 0000:00:14.5: new USB bus registered, assigned bus number 7
Dec  5 16:05:54 bitch kernel: [    1.404485] ohci_hcd 0000:00:14.5: irq 18, io mem 0xfe028000
Dec  5 16:05:54 bitch kernel: [    1.464155] usb usb7: configuration #1 chosen from 1 choice
Dec  5 16:05:54 bitch kernel: [    1.464171] hub 7-0:1.0: USB hub found
Dec  5 16:05:54 bitch kernel: [    1.464179] hub 7-0:1.0: 2 ports detected
Dec  5 16:05:54 bitch kernel: [    1.464252] uhci_hcd: USB Universal Host Controller Interface driver
Dec  5 16:05:54 bitch kernel: [    1.464346] PNP: PS/2 Controller [PNP0303:PS2K] at 0x60,0x64 irq 1
Dec  5 16:05:54 bitch kernel: [    1.464348] PNP: PS/2 appears to have AUX port disabled, if this is incorrect please boot with i8042.nopnp
Dec  5 16:05:54 bitch kernel: [    1.464486] serio: i8042 KBD port at 0x60,0x64 irq 1
Dec  5 16:05:54 bitch kernel: [    1.464559] mice: PS/2 mouse device common for all mice
Dec  5 16:05:54 bitch kernel: [    1.464608] Driver 'rtc_cmos' needs updating - please use bus_type methods
Dec  5 16:05:54 bitch kernel: [    1.464630] rtc_cmos 00:05: RTC can wake from S4
Dec  5 16:05:54 bitch kernel: [    1.464670] rtc_cmos 00:05: rtc core: registered rtc_cmos as rtc0
Dec  5 16:05:54 bitch kernel: [    1.464701] rtc0: alarms up to one month, 242 bytes nvram, hpet irqs
Dec  5 16:05:54 bitch kernel: [    1.464789] device-mapper: uevent: version 1.0.3
Dec  5 16:05:54 bitch kernel: [    1.464888] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: dm-devel@redhat.com
Dec  5 16:05:54 bitch kernel: [    1.464994] device-mapper: multipath: version 1.1.0 loaded
Dec  5 16:05:54 bitch kernel: [    1.464996] device-mapper: multipath round-robin: version 1.0.0 loaded
Dec  5 16:05:54 bitch kernel: [    1.465193] cpuidle: using governor ladder
Dec  5 16:05:54 bitch kernel: [    1.465194] cpuidle: using governor menu
Dec  5 16:05:54 bitch kernel: [    1.465496] TCP cubic registered
Dec  5 16:05:54 bitch kernel: [    1.465583] NET: Registered protocol family 10
Dec  5 16:05:54 bitch kernel: [    1.465971] lo: Disabled Privacy Extensions
Dec  5 16:05:54 bitch kernel: [    1.466200] NET: Registered protocol family 17
Dec  5 16:05:54 bitch kernel: [    1.466218] Bluetooth: L2CAP ver 2.14
Dec  5 16:05:54 bitch kernel: [    1.466219] Bluetooth: L2CAP socket layer initialized
Dec  5 16:05:54 bitch kernel: [    1.466221] Bluetooth: SCO (Voice Link) ver 0.6
Dec  5 16:05:54 bitch kernel: [    1.466222] Bluetooth: SCO socket layer initialized
Dec  5 16:05:54 bitch kernel: [    1.466308] Bluetooth: RFCOMM TTY layer initialized
Dec  5 16:05:54 bitch kernel: [    1.466310] Bluetooth: RFCOMM socket layer initialized
Dec  5 16:05:54 bitch kernel: [    1.466312] Bluetooth: RFCOMM ver 1.11
Dec  5 16:05:54 bitch kernel: [    1.466347] powernow-k8: Found 1 AMD Athlon(tm) II X4 620 Processor processors (4 cpu cores) (version 2.20.00)
Dec  5 16:05:54 bitch kernel: [    1.466386] powernow-k8:    0 : pstate 0 (2600 MHz)
Dec  5 16:05:54 bitch kernel: [    1.466388] powernow-k8:    1 : pstate 1 (1900 MHz)
Dec  5 16:05:54 bitch kernel: [    1.466389] powernow-k8:    2 : pstate 2 (1400 MHz)
Dec  5 16:05:54 bitch kernel: [    1.466391] powernow-k8:    3 : pstate 3 (800 MHz)
Dec  5 16:05:54 bitch kernel: [    1.466776] registered taskstats version 1
Dec  5 16:05:54 bitch kernel: [    1.467063]   Magic number: 5:962:31
Dec  5 16:05:54 bitch kernel: [    1.467167] rtc_cmos 00:05: setting system clock to 2009-12-05 15:02:51 UTC (1260025371)
Dec  5 16:05:54 bitch kernel: [    1.467170] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
Dec  5 16:05:54 bitch kernel: [    1.467171] EDD information not available.
Dec  5 16:05:54 bitch kernel: [    1.471442] ata4: SATA link down (SStatus 0 SControl 300)
Dec  5 16:05:54 bitch kernel: [    1.471470] ata2: SATA link down (SStatus 0 SControl 300)
Dec  5 16:05:54 bitch kernel: [    1.471496] ata6: SATA link down (SStatus 0 SControl 300)
Dec  5 16:05:54 bitch kernel: [    1.471521] ata5: SATA link down (SStatus 0 SControl 300)
Dec  5 16:05:54 bitch kernel: [    1.481660] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input3
Dec  5 16:05:54 bitch kernel: [    1.630116] usb 4-3: new low speed USB device using ohci_hcd and address 2
Dec  5 16:05:54 bitch kernel: [    1.650133] ata3: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
Dec  5 16:05:54 bitch kernel: [    1.658148] ata3.00: ATA-7: Hitachi HDT725050VLA380, V56OA73A, max UDMA/133
Dec  5 16:05:54 bitch kernel: [    1.658152] ata3.00: 976773168 sectors, multi 0: LBA48 NCQ (depth 31/32), AA
Dec  5 16:05:54 bitch kernel: [    1.659164] ata3.00: configured for UDMA/133
Dec  5 16:05:54 bitch kernel: [    1.824313] usb 4-3: configuration #1 chosen from 1 choice
Dec  5 16:05:54 bitch kernel: [    2.050150] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
Dec  5 16:05:54 bitch kernel: [    2.067517] ata1.00: ATA-8: Hitachi HDT721010SLA360, ST6OA3AA, max UDMA/133
Dec  5 16:05:54 bitch kernel: [    2.067519] ata1.00: 1953525168 sectors, multi 0: LBA48 NCQ (depth 31/32), AA
Dec  5 16:05:54 bitch kernel: [    2.068992] ata1.00: configured for UDMA/133
Dec  5 16:05:54 bitch kernel: [    2.080212] scsi 0:0:0:0: Direct-Access     ATA      Hitachi HDT72101 ST6O PQ: 0 ANSI: 5
Dec  5 16:05:54 bitch kernel: [    2.080345] sd 0:0:0:0: Attached scsi generic sg0 type 0
Dec  5 16:05:54 bitch kernel: [    2.080398] sd 0:0:0:0: [sda] 1953525168 512-byte logical blocks: (1.00 TB/931 GiB)
Dec  5 16:05:54 bitch kernel: [    2.080427] sd 0:0:0:0: [sda] Write Protect is off
Dec  5 16:05:54 bitch kernel: [    2.080444] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Dec  5 16:05:54 bitch kernel: [    2.080470] scsi 2:0:0:0: Direct-Access     ATA      Hitachi HDT72505 V56O PQ: 0 ANSI: 5
Dec  5 16:05:54 bitch kernel: [    2.080535]  sda:
Dec  5 16:05:54 bitch kernel: [    2.080597] sd 2:0:0:0: Attached scsi generic sg1 type 0
Dec  5 16:05:54 bitch kernel: [    2.080640] sd 2:0:0:0: [sdb] 976773168 512-byte logical blocks: (500 GB/465 GiB)
Dec  5 16:05:54 bitch kernel: [    2.080670] sd 2:0:0:0: [sdb] Write Protect is off
Dec  5 16:05:54 bitch kernel: [    2.080686] sd 2:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Dec  5 16:05:54 bitch kernel: [    2.080780]  sdb:
Dec  5 16:05:54 bitch kernel: [    2.082337] scsi 6:0:0:0: CD-ROM            HL-DT-ST DVD-RAM GSA-H55N 1.03 PQ: 0 ANSI: 5
Dec  5 16:05:54 bitch kernel: [    2.087668] sr0: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
Dec  5 16:05:54 bitch kernel: [    2.087670] Uniform CD-ROM driver Revision: 3.20
Dec  5 16:05:54 bitch kernel: [    2.087767] sr 6:0:0:0: Attached scsi generic sg2 type 5
Dec  5 16:05:54 bitch kernel: [    2.088782] scsi 6:0:1:0: CD-ROM            TSSTcorp CD/DVDW SH-S182M SB02 PQ: 0 ANSI: 5
Dec  5 16:05:54 bitch kernel: [    2.096346] sr1: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
Dec  5 16:05:54 bitch kernel: [    2.096422] sr 6:0:1:0: Attached scsi generic sg3 type 5
Dec  5 16:05:54 bitch kernel: [    2.099072]  sdb1 sdb2 sdb3 < sda1 sda2 < sda5 sda6 >
Dec  5 16:05:54 bitch kernel: [    2.110926] sd 0:0:0:0: [sda] Attached SCSI disk
Dec  5 16:05:54 bitch kernel: [    2.116823]  sdb5 >
Dec  5 16:05:54 bitch kernel: [    2.132981] sd 2:0:0:0: [sdb] Attached SCSI disk
Dec  5 16:05:54 bitch kernel: [    2.250193] Freeing unused kernel memory: 728k freed
Dec  5 16:05:54 bitch kernel: [    2.250388] Write protecting the kernel read-only data: 7792k
Dec  5 16:05:54 bitch kernel: [    2.395052] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
Dec  5 16:05:54 bitch kernel: [    2.395080] r8169 0000:02:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
Dec  5 16:05:54 bitch kernel: [    2.395660] eth0: RTL8168c/8111c at 0xffffc90000672000, 00:24:1d:d1:85:c5, XID 1c4000c0 IRQ 27
Dec  5 16:05:54 bitch kernel: [    2.395890] usbcore: registered new interface driver hiddev
Dec  5 16:05:54 bitch kernel: [    2.400429] input: Microsoft Microsoft 5-Button Mouse with IntelliEye(TM) as /devices/pci0000:00/0000:00:12.1/usb4/4-3/4-3:1.0/input/input4
Dec  5 16:05:54 bitch kernel: [    2.400502] generic-usb 0003:045E:0039.0001: input,hidraw0: USB HID v1.10 Mouse [Microsoft Microsoft 5-Button Mouse with IntelliEye(TM)] on usb-0000:00:12.1-3/input0
Dec  5 16:05:54 bitch kernel: [    2.400536] usbcore: registered new interface driver usbhid
Dec  5 16:05:54 bitch kernel: [    2.400538] usbhid: v2.6:USB HID core driver
Dec  5 16:05:54 bitch kernel: [    2.403855] ohci1394 0000:03:0e.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
Dec  5 16:05:54 bitch kernel: [    2.470131] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[22]  MMIO=[fddff000-fddff7ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
Dec  5 16:05:54 bitch kernel: [  178.848332] PM: Starting manual resume from disk
Dec  5 16:05:54 bitch kernel: [  178.879493] EXT4-fs (sda5): mounted filesystem with ordered data mode
Dec  5 16:05:54 bitch kernel: [  183.587543] Adding 3903752k swap on /dev/sda1.  Priority:-1 extents:1 across:3903752k
Dec  5 16:05:54 bitch kernel: [  183.594043] udev: starting version 147
Dec  5 16:05:54 bitch kernel: [  183.712255] ip_tables: (C) 2000-2006 Netfilter Core Team
Dec  5 16:05:54 bitch kernel: [  183.872782] lp: driver loaded but no devices found
Dec  5 16:05:54 bitch kernel: [  183.915753] EDAC MC: Ver: 2.1.0 Dec  3 2009
Dec  5 16:05:54 bitch kernel: [  183.924598] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
Dec  5 16:05:54 bitch kernel: [  183.938294] EDAC amd64_edac:  Ver: 3.2.0 Dec  3 2009
Dec  5 16:05:54 bitch kernel: [  183.938538] EDAC amd64: This node reports that Memory ECC is currently disabled, set F3x44[22] (0000:00:18.3).
Dec  5 16:05:54 bitch kernel: [  183.938549] EDAC amd64: WARNING: ECC is disabled by BIOS. Module will NOT be loaded.
Dec  5 16:05:54 bitch kernel: [  183.938550]  Either Enable ECC in the BIOS, or set 'ecc_enable_override'.
Dec  5 16:05:54 bitch kernel: [  183.938551]  Also, use of the override can cause unknown side effects.
Dec  5 16:05:54 bitch kernel: [  183.938566] amd64_edac: probe of 0000:00:18.2 failed with error -22
Dec  5 16:05:54 bitch kernel: [  184.582190] EXT4-fs (sda6): mounted filesystem with ordered data mode
Dec  5 16:05:54 bitch kernel: [  184.611880] HDA Intel 0000:00:14.2: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Dec  5 16:05:54 bitch kernel: [  184.733657] r8169: eth0: link up
Dec  5 16:05:54 bitch kernel: [  184.733664] r8169: eth0: link up
Dec  5 16:05:54 bitch kernel: [  184.787771] input: HDA Digital PCBeep as /devices/pci0000:00/0000:00:14.2/input/input5
Dec  5 16:05:55 bitch kernel: [  185.227813] usplash:407 freeing invalid memtype ffffffffd0000000-ffffffffd1000000
Dec  5 16:05:55 bitch kernel: [  185.260698] kvm: Nested Virtualization enabled
Dec  5 16:05:55 bitch kernel: [  185.260704] kvm: Nested Paging enabled
Dec  5 16:05:55 bitch kernel: [  185.308324] pci 0000:01:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
Dec  5 16:05:55 bitch kernel: [  185.354034] Bridge firewalling registered
Dec  5 16:05:55 bitch kernel: [  185.359025] virbr0: starting userspace STP failed, starting kernel STP
Dec  5 16:05:55 bitch kernel: [  185.383256] [drm] Initialized drm 1.1.0 20060810
Dec  5 16:05:55 bitch kernel: [  185.394914] ppdev: user-space parallel port driver
Dec  5 16:05:55 bitch kernel: [  185.489960] [drm] radeon defaulting to userspace modesetting.
Dec  5 16:05:55 bitch kernel: [  185.490675] [drm] Initialized radeon 1.31.0 20080528 for 0000:01:00.0 on minor 0
Dec  5 16:05:55 bitch kernel: [  185.529714] nf_conntrack version 0.5.0 (16384 buckets, 65536 max)
Dec  5 16:05:55 bitch kernel: [  185.530408] CONFIG_NF_CT_ACCT is deprecated and will be removed soon. Please use
Dec  5 16:05:55 bitch kernel: [  185.530411] nf_conntrack.acct=1 kernel parameter, acct=1 nf_conntrack module option or
Dec  5 16:05:55 bitch kernel: [  185.530412] sysctl net.netfilter.nf_conntrack_acct=1 to enable it.
Dec  5 16:05:55 bitch kernel: [  185.666407] [drm] Setting GART location based on new memory map
Dec  5 16:05:55 bitch kernel: [  185.666681] [drm] Loading R500 Microcode
Dec  5 16:05:55 bitch kernel: [  185.666686] platform radeon_cp.0: firmware: requesting radeon/R520_cp.bin
Dec  5 16:05:55 bitch kernel: [  185.745174] lo: Disabled Privacy Extensions
Dec  5 16:05:55 bitch kernel: [  185.801603] [drm] Num pipes: 4
Dec  5 16:05:55 bitch kernel: [  185.801614] [drm] writeback test succeeded in 1 usecs
Dec  5 16:06:02 bitch kernel: [  192.019340] RPC: Registered udp transport module.
Dec  5 16:06:02 bitch kernel: [  192.019345] RPC: Registered tcp transport module.
Dec  5 16:06:02 bitch kernel: [  192.019346] RPC: Registered tcp NFSv4.1 backchannel transport module.
Dec  5 16:06:02 bitch kernel: [  192.106731] svc: failed to register lockdv1 RPC service (errno 97).
Dec  5 16:08:15 bitch kernel: [  325.951227] Intel AES-NI instructions are not detected.
Dec  5 16:08:16 bitch kernel: [  325.990225] padlock: VIA PadLock not detected.
Dec  5 16:11:46 bitch kernel: [  535.973915] CE: hpet increasing min_delta_ns to 15000 nsec
...

```

As you can see the early stage in that the boot process hangs couldn't be produced by a driver bug. So there must be something in the kernel. As I have a very similar setup at work running without any problems even with the 2.6.32 vanilla kernel it looks like some kind of race condition.

Additionally when I boot the system with the monitor detached and reattach it when the boot completed I just restart KDM service and voila, all things are fine, composition works, glxgears, no corruptions at all. So the driver is working fine (as it should).

If anyone here has any hints please help me as every time detaching the monitor when rebooting isn't that convenient.

Thanx,

C]-[aoZ

---

### Post by CHaoSlayeR on 2009-12-09
Update:

Today I replaced the previously working Dell 3007WFP-HC at my machine at work with another display after I updated the system.

And now guess what: boot hang.

But this time it's even worse because I was not able to boot completely even without the monitors being attached. So this is a complete show-stopper for me.

Tomorrow I'll try if disabling the framebuffer helps. I'll also update the bug at launchpad accordingly: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/493834](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/493834)

I'll also attach the list of the updates I made there.

C]-[aoZ

---

### Post by CHaoSlayeR on 2009-12-10
As I said earlier I tried to disable the framebuffer for the boot and indeed this did the trick.

But I see that as a workaround, not a fix. So I updated the bug report and wait for comments of any dev.

I also wrote to the ubuntu-kernel-team mailing list about a week ago but without any response from there. So either it's not interesting to fix bugs anymore (feature-hunting is more exciting, I know), or the devs are just a bit blind these days.

C]-[aoZ

[EDIT]
I just found out that it is NOT the framebuffer. Instead it is the "splash" boot option that causes those hangs. disabling that works like a charm. But this is still a workaround, not a fix.
[/EDIT]

---

