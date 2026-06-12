---
title: "device descriptor read/all, error -110 Kernel Panic"
date: 2011-12-24
forum: General Help
---

### Post by mirec on 2011-12-24
Hi, I am very new to Ubuntu. Almost every time I try to start the computer each day I get a kernel panic. 
Usually it help when I start with recovery console stay in it doing nothing (while this I can see some device descriptor errors coming. please see screenshot) and then boot (it boots without icons and with wrong resolution set up). After restart it boots normally...

[ATTACH]209645[/ATTACH]

Here is the log from kern.log (sorry for its length but I dont know which parts might be relevant):

```

Dec 24 10:27:54 laptop kernel: imklog 5.8.1, log source = /proc/kmsg started.
Dec 24 10:27:54 laptop kernel: [    0.000000] Initializing cgroup subsys cpuset
Dec 24 10:27:54 laptop kernel: [    0.000000] Initializing cgroup subsys cpu
Dec 24 10:27:54 laptop kernel: [    0.000000] Linux version 3.0.0-14-generic-pae (buildd@palmer) (gcc version 4.6.1 (Ubuntu/Linaro 4.6.1-9ubuntu3) ) #23-Ubuntu SMP Mon Nov 21 22:07:10 UTC 2011 (Ubuntu 3.0.0-14.23-generic-pae 3.0.9)
Dec 24 10:27:54 laptop kernel: [    0.000000] KERNEL supported cpus:
Dec 24 10:27:54 laptop kernel: [    0.000000]   Intel GenuineIntel
Dec 24 10:27:54 laptop kernel: [    0.000000]   AMD AuthenticAMD
Dec 24 10:27:54 laptop kernel: [    0.000000]   NSC Geode by NSC
Dec 24 10:27:54 laptop kernel: [    0.000000]   Cyrix CyrixInstead
Dec 24 10:27:54 laptop kernel: [    0.000000]   Centaur CentaurHauls
Dec 24 10:27:54 laptop kernel: [    0.000000]   Transmeta GenuineTMx86
Dec 24 10:27:54 laptop kernel: [    0.000000]   Transmeta TransmetaCPU
Dec 24 10:27:54 laptop kernel: [    0.000000]   UMC UMC UMC UMC
Dec 24 10:27:54 laptop kernel: [    0.000000] BIOS-provided physical RAM map:
Dec 24 10:27:54 laptop kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 000000000009d000 (usable)
Dec 24 10:27:54 laptop kernel: [    0.000000]  BIOS-e820: 000000000009d000 - 00000000000a0000 (reserved)
Dec 24 10:27:54 laptop kernel: [    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
Dec 24 10:27:54 laptop kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 00000000bf681000 (usable)
Dec 24 10:27:54 laptop kernel: [    0.000000]  BIOS-e820: 00000000bf681000 - 00000000bf6bf000 (reserved)
Dec 24 10:27:54 laptop kernel: [    0.000000]  BIOS-e820: 00000000bf6bf000 - 00000000bf75d000 (usable)
Dec 24 10:27:54 laptop kernel: [    0.000000]  BIOS-e820: 00000000bf75d000 - 00000000bf7bf000 (ACPI NVS)
Dec 24 10:27:54 laptop kernel: [    0.000000]  BIOS-e820: 00000000bf7bf000 - 00000000bf7e1000 (usable)
Dec 24 10:27:54 laptop kernel: [    0.000000]  BIOS-e820: 00000000bf7e1000 - 00000000bf7ff000 (ACPI data)
Dec 24 10:27:54 laptop kernel: [    0.000000]  BIOS-e820: 00000000bf7ff000 - 00000000bf800000 (usable)
Dec 24 10:27:54 laptop kernel: [    0.000000]  BIOS-e820: 00000000bf800000 - 00000000c0000000 (reserved)
Dec 24 10:27:54 laptop kernel: [    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
Dec 24 10:27:54 laptop kernel: [    0.000000]  BIOS-e820: 00000000feb00000 - 00000000feb04000 (reserved)
Dec 24 10:27:54 laptop kernel: [    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved)
Dec 24 10:27:54 laptop kernel: [    0.000000]  BIOS-e820: 00000000fed10000 - 00000000fed14000 (reserved)
Dec 24 10:27:54 laptop kernel: [    0.000000]  BIOS-e820: 00000000fed18000 - 00000000fed1a000 (reserved)
Dec 24 10:27:54 laptop kernel: [    0.000000]  BIOS-e820: 00000000fed1b000 - 00000000fed20000 (reserved)
Dec 24 10:27:54 laptop kernel: [    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
Dec 24 10:27:54 laptop kernel: [    0.000000]  BIOS-e820: 00000000ffe80000 - 0000000100000000 (reserved)
Dec 24 10:27:54 laptop kernel: [    0.000000]  BIOS-e820: 0000000100000000 - 000000013c000000 (usable)
Dec 24 10:27:54 laptop kernel: [    0.000000] NX (Execute Disable) protection: active
Dec 24 10:27:54 laptop kernel: [    0.000000] DMI 2.6 present.
Dec 24 10:27:54 laptop kernel: [    0.000000] DMI: Hewlett-Packard HP Pavilion dv7 Notebook PC/365C, BIOS F.15 01/05/2010
Dec 24 10:27:54 laptop kernel: [    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
Dec 24 10:27:54 laptop kernel: [    0.000000] e820 remove range: 00000000000a0000 - 0000000000100000 (usable)
Dec 24 10:27:54 laptop kernel: [    0.000000] last_pfn = 0x13c000 max_arch_pfn = 0x1000000
Dec 24 10:27:54 laptop kernel: [    0.000000] MTRR default type: uncachable
Dec 24 10:27:54 laptop kernel: [    0.000000] MTRR fixed ranges enabled:
Dec 24 10:27:54 laptop kernel: [    0.000000]   00000-9FFFF write-back
Dec 24 10:27:54 laptop kernel: [    0.000000]   A0000-BFFFF uncachable
Dec 24 10:27:54 laptop kernel: [    0.000000]   C0000-EFFFF write-through
Dec 24 10:27:54 laptop kernel: [    0.000000]   F0000-FFFFF write-combining
Dec 24 10:27:54 laptop kernel: [    0.000000] MTRR variable ranges enabled:
Dec 24 10:27:54 laptop kernel: [    0.000000]   0 base 000000000 mask F80000000 write-back
Dec 24 10:27:54 laptop kernel: [    0.000000]   1 base 0FFE00000 mask FFFE00000 write-protect
Dec 24 10:27:54 laptop kernel: [    0.000000]   2 base 080000000 mask FC0000000 write-back
Dec 24 10:27:54 laptop kernel: [    0.000000]   3 base 0BF800000 mask FFF800000 uncachable
Dec 24 10:27:54 laptop kernel: [    0.000000]   4 base 100000000 mask FC0000000 write-back
Dec 24 10:27:54 laptop kernel: [    0.000000]   5 disabled
Dec 24 10:27:54 laptop kernel: [    0.000000]   6 disabled
Dec 24 10:27:54 laptop kernel: [    0.000000]   7 disabled
Dec 24 10:27:54 laptop kernel: [    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
Dec 24 10:27:54 laptop kernel: [    0.000000] initial memory mapped : 0 - 02000000
Dec 24 10:27:54 laptop kernel: [    0.000000] Base memory trampoline at [c0099000] 99000 size 16384
Dec 24 10:27:54 laptop kernel: [    0.000000] init_memory_mapping: 0000000000000000-0000000037bfe000
Dec 24 10:27:54 laptop kernel: [    0.000000]  0000000000 - 0000200000 page 4k
Dec 24 10:27:54 laptop kernel: [    0.000000]  0000200000 - 0037a00000 page 2M
Dec 24 10:27:54 laptop kernel: [    0.000000]  0037a00000 - 0037bfe000 page 4k
Dec 24 10:27:54 laptop kernel: [    0.000000] kernel direct mapping tables up to 37bfe000 @ 1ffb000-2000000
Dec 24 10:27:54 laptop kernel: [    0.000000] RAMDISK: 365e8000 - 372ec000
Dec 24 10:27:54 laptop kernel: [    0.000000] ACPI: RSDP 000fe020 00024 (v02 HPQOEM)
Dec 24 10:27:54 laptop kernel: [    0.000000] ACPI: XSDT bf7fe120 00074 (v01 HPQOEM SLIC-MPC 00000001      01000013)
Dec 24 10:27:54 laptop kernel: [    0.000000] ACPI: FACP bf7fc000 000F4 (v04 HPQOEM SLIC-MPC 00000001 MSFT 01000013)
Dec 24 10:27:54 laptop kernel: [    0.000000] ACPI: DSDT bf7eb000 0DC73 (v02 HPQOEM SLIC-MPC 00000001 MSFT 01000013)
Dec 24 10:27:54 laptop kernel: [    0.000000] ACPI: FACS bf76f000 00040
Dec 24 10:27:54 laptop kernel: [    0.000000] ACPI: ASF! bf7fd000 000A5 (v32 HPQOEM SLIC-MPC 00000001 MSFT 01000013)
Dec 24 10:27:54 laptop kernel: [    0.000000] ACPI: HPET bf7fb000 00038 (v01 HPQOEM SLIC-MPC 00000001 MSFT 01000013)
Dec 24 10:27:54 laptop kernel: [    0.000000] ACPI: APIC bf7fa000 0008C (v02 HPQOEM SLIC-MPC 00000001 MSFT 01000013)
Dec 24 10:27:54 laptop kernel: [    0.000000] ACPI: MCFG bf7f9000 0003C (v01 HPQOEM SLIC-MPC 00000001 MSFT 01000013)
Dec 24 10:27:54 laptop kernel: [    0.000000] ACPI: SLIC bf7ea000 00176 (v01 HPQOEM SLIC-MPC 00000001 SLIC 000F4240)
Dec 24 10:27:54 laptop kernel: [    0.000000] ACPI: BOOT bf7e7000 00028 (v01 HPQOEM SLIC-MPC 00000001 MSFT 01000013)
Dec 24 10:27:54 laptop kernel: [    0.000000] ACPI: ASPT bf7e3000 00034 (v04 HPQOEM SLIC-MPC 00000001 MSFT 01000013)
Dec 24 10:27:54 laptop kernel: [    0.000000] ACPI: WDRT bf7e2000 00047 (v01 HPQOEM SLIC-MPC 00000000 MSFT 01000013)
Dec 24 10:27:54 laptop kernel: [    0.000000] ACPI: SSDT bf7e1000 009F1 (v01  PmRef    CpuPm 00003000 INTL 20060317)
Dec 24 10:27:54 laptop kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
Dec 24 10:27:54 laptop kernel: [    0.000000] 4164MB HIGHMEM available.
Dec 24 10:27:54 laptop kernel: [    0.000000] 891MB LOWMEM available.
Dec 24 10:27:54 laptop kernel: [    0.000000]   mapped low ram: 0 - 37bfe000
Dec 24 10:27:54 laptop kernel: [    0.000000]   low ram: 0 - 37bfe000
Dec 24 10:27:54 laptop kernel: [    0.000000] Zone PFN ranges:
Dec 24 10:27:54 laptop kernel: [    0.000000]   DMA      0x00000010 -> 0x00001000
Dec 24 10:27:54 laptop kernel: [    0.000000]   Normal   0x00001000 -> 0x00037bfe
Dec 24 10:27:54 laptop kernel: [    0.000000]   HighMem  0x00037bfe -> 0x0013c000
Dec 24 10:27:54 laptop kernel: [    0.000000] Movable zone start PFN for each node
Dec 24 10:27:54 laptop kernel: [    0.000000] early_node_map[6] active PFN ranges
Dec 24 10:27:54 laptop kernel: [    0.000000]     0: 0x00000010 -> 0x0000009d
Dec 24 10:27:54 laptop kernel: [    0.000000]     0: 0x00000100 -> 0x000bf681
Dec 24 10:27:54 laptop kernel: [    0.000000]     0: 0x000bf6bf -> 0x000bf75d
Dec 24 10:27:54 laptop kernel: [    0.000000]     0: 0x000bf7bf -> 0x000bf7e1
Dec 24 10:27:54 laptop kernel: [    0.000000]     0: 0x000bf7ff -> 0x000bf800
Dec 24 10:27:54 laptop kernel: [    0.000000]     0: 0x00100000 -> 0x0013c000
Dec 24 10:27:54 laptop kernel: [    0.000000] On node 0 totalpages: 1029839
Dec 24 10:27:54 laptop kernel: [    0.000000] free_area_init_node: node 0, pgdat c17ee1c0, node_mem_map f3e68200
Dec 24 10:27:54 laptop kernel: [    0.000000]   DMA zone: 32 pages used for memmap
Dec 24 10:27:54 laptop kernel: [    0.000000]   DMA zone: 0 pages reserved
Dec 24 10:27:54 laptop kernel: [    0.000000]   DMA zone: 3949 pages, LIFO batch:0
Dec 24 10:27:54 laptop kernel: [    0.000000]   Normal zone: 1752 pages used for memmap
Dec 24 10:27:54 laptop kernel: [    0.000000]   Normal zone: 222502 pages, LIFO batch:31
Dec 24 10:27:54 laptop kernel: [    0.000000]   HighMem zone: 8329 pages used for memmap
Dec 24 10:27:54 laptop kernel: [    0.000000]   HighMem zone: 793275 pages, LIFO batch:31
Dec 24 10:27:54 laptop kernel: [    0.000000] Using APIC driver default
Dec 24 10:27:54 laptop kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x408
Dec 24 10:27:54 laptop kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
Dec 24 10:27:54 laptop kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
Dec 24 10:27:54 laptop kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
Dec 24 10:27:54 laptop kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x04] enabled)
Dec 24 10:27:54 laptop kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x05] enabled)
Dec 24 10:27:54 laptop kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x05] lapic_id[0x00] disabled)
Dec 24 10:27:54 laptop kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x06] lapic_id[0x00] disabled)
Dec 24 10:27:54 laptop kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x07] lapic_id[0x00] disabled)
Dec 24 10:27:54 laptop kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x08] lapic_id[0x00] disabled)
Dec 24 10:27:54 laptop kernel: [    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
Dec 24 10:27:54 laptop kernel: [    0.000000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-23
Dec 24 10:27:54 laptop kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
Dec 24 10:27:54 laptop kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
Dec 24 10:27:54 laptop kernel: [    0.000000] ACPI: IRQ0 used by override.
Dec 24 10:27:54 laptop kernel: [    0.000000] ACPI: IRQ2 used by override.
Dec 24 10:27:54 laptop kernel: [    0.000000] ACPI: IRQ9 used by override.
Dec 24 10:27:54 laptop kernel: [    0.000000] Using ACPI (MADT) for SMP configuration information
Dec 24 10:27:54 laptop kernel: [    0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000
Dec 24 10:27:54 laptop kernel: [    0.000000] SMP: Allowing 8 CPUs, 4 hotplug CPUs
Dec 24 10:27:54 laptop kernel: [    0.000000] nr_irqs_gsi: 40
Dec 24 10:27:54 laptop kernel: [    0.000000] PM: Registered nosave memory: 000000000009d000 - 00000000000a0000
Dec 24 10:27:54 laptop kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
Dec 24 10:27:54 laptop kernel: [    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
Dec 24 10:27:54 laptop kernel: [    0.000000] Allocating PCI resources starting at c0000000 (gap: c0000000:20000000)
Dec 24 10:27:54 laptop kernel: [    0.000000] Booting paravirtualized kernel on bare hardware
Dec 24 10:27:54 laptop kernel: [    0.000000] setup_percpu: NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:8 nr_node_ids:1
Dec 24 10:27:54 laptop kernel: [    0.000000] PERCPU: Embedded 13 pages/cpu @f7800000 s29952 r0 d23296 u262144
Dec 24 10:27:54 laptop kernel: [    0.000000] pcpu-alloc: s29952 r0 d23296 u262144 alloc=1*2097152
Dec 24 10:27:54 laptop kernel: [    0.000000] pcpu-alloc: [0] 0 1 2 3 4 5 6 7 
Dec 24 10:27:54 laptop kernel: [    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 1019726
Dec 24 10:27:54 laptop kernel: [    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.0.0-14-generic-pae root=UUID=1293a0e3-f2ed-4d61-bd76-a855970c1fe4 ro recovery nomodeset
Dec 24 10:27:54 laptop kernel: [    0.000000] PID hash table entries: 4096 (order: 2, 16384 bytes)
Dec 24 10:27:54 laptop kernel: [    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
Dec 24 10:27:54 laptop kernel: [    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
Dec 24 10:27:54 laptop kernel: [    0.000000] Initializing CPU#0
Dec 24 10:27:54 laptop kernel: [    0.000000] allocated 20709120 bytes of page_cgroup
Dec 24 10:27:54 laptop kernel: [    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
Dec 24 10:27:54 laptop kernel: [    0.000000] Initializing HighMem for node 0 (00037bfe:0013c000)
Dec 24 10:27:54 laptop kernel: [    0.000000] Memory: 4034212k/5177344k available (5499k kernel code, 85144k reserved, 2665k data, 720k init, 3206416k highmem)
Dec 24 10:27:54 laptop kernel: [    0.000000] virtual kernel memory layout:
Dec 24 10:27:54 laptop kernel: [    0.000000]     fixmap  : 0xfff16000 - 0xfffff000   ( 932 kB)
Dec 24 10:27:54 laptop kernel: [    0.000000]     pkmap   : 0xffc00000 - 0xffe00000   (2048 kB)
Dec 24 10:27:54 laptop kernel: [    0.000000]     vmalloc : 0xf83fe000 - 0xffbfe000   ( 120 MB)
Dec 24 10:27:54 laptop kernel: [    0.000000]     lowmem  : 0xc0000000 - 0xf7bfe000   ( 891 MB)
Dec 24 10:27:54 laptop kernel: [    0.000000]       .init : 0xc17fa000 - 0xc18ae000   ( 720 kB)
Dec 24 10:27:54 laptop kernel: [    0.000000]       .data : 0xc155efb0 - 0xc17f94c0   (2665 kB)
Dec 24 10:27:54 laptop kernel: [    0.000000]       .text : 0xc1000000 - 0xc155efb0   (5499 kB)
Dec 24 10:27:54 laptop kernel: [    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
Dec 24 10:27:54 laptop kernel: [    0.000000] SLUB: Genslabs=15, HWalign=64, Order=0-3, MinObjects=0, CPUs=8, Nodes=1
Dec 24 10:27:54 laptop kernel: [    0.000000] Hierarchical RCU implementation.
Dec 24 10:27:54 laptop kernel: [    0.000000] 	RCU dyntick-idle grace-period acceleration is enabled.
Dec 24 10:27:54 laptop kernel: [    0.000000] NR_IRQS:2304 nr_irqs:744 16
Dec 24 10:27:54 laptop kernel: [    0.000000] CPU 0 irqstacks, hard=f740a000 soft=f740c000
Dec 24 10:27:54 laptop kernel: [    0.000000] Extended CMOS year: 2000
Dec 24 10:27:54 laptop kernel: [    0.000000] Console: colour VGA+ 80x25
Dec 24 10:27:54 laptop kernel: [    0.000000] console [tty0] enabled
Dec 24 10:27:54 laptop kernel: [    0.000000] hpet clockevent registered
Dec 24 10:27:54 laptop kernel: [    0.000000] Fast TSC calibration using PIT
Dec 24 10:27:54 laptop kernel: [    0.004000] Detected 2128.065 MHz processor.
Dec 24 10:27:54 laptop kernel: [    0.000003] Calibrating delay loop (skipped), value calculated using timer frequency.. 4256.13 BogoMIPS (lpj=8512260)
Dec 24 10:27:54 laptop kernel: [    0.000153] pid_max: default: 32768 minimum: 301
Dec 24 10:27:54 laptop kernel: [    0.000246] Security Framework initialized
Dec 24 10:27:54 laptop kernel: [    0.000334] AppArmor: AppArmor initialized
Dec 24 10:27:54 laptop kernel: [    0.000408] Yama: becoming mindful.
Dec 24 10:27:54 laptop kernel: [    0.000530] Mount-cache hash table entries: 512
Dec 24 10:27:54 laptop kernel: [    0.000733] Initializing cgroup subsys cpuacct
Dec 24 10:27:54 laptop kernel: [    0.000815] Initializing cgroup subsys memory
Dec 24 10:27:54 laptop kernel: [    0.000893] Initializing cgroup subsys devices
Dec 24 10:27:54 laptop kernel: [    0.000969] Initializing cgroup subsys freezer
Dec 24 10:27:54 laptop kernel: [    0.001042] Initializing cgroup subsys net_cls
Dec 24 10:27:54 laptop kernel: [    0.001114] Initializing cgroup subsys blkio
Dec 24 10:27:54 laptop kernel: [    0.001190] Initializing cgroup subsys perf_event
Dec 24 10:27:54 laptop kernel: [    0.001288] CPU: Physical Processor ID: 0
Dec 24 10:27:54 laptop kernel: [    0.001363] CPU: Processor Core ID: 0
Dec 24 10:27:54 laptop kernel: [    0.001437] mce: CPU supports 9 MCE banks
Dec 24 10:27:54 laptop kernel: [    0.001516] CPU0: Thermal monitoring enabled (TM1)
Dec 24 10:27:54 laptop kernel: [    0.001598] using mwait in idle threads.
Dec 24 10:27:54 laptop kernel: [    0.003807] ACPI: Core revision 20110413
Dec 24 10:27:54 laptop kernel: [    0.038652] ftrace: allocating 25575 entries in 51 pages
Dec 24 10:27:54 laptop kernel: [    0.047251] Enabling APIC mode:  Flat.  Using 1 I/O APICs
Dec 24 10:27:54 laptop kernel: [    0.047734] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
Dec 24 10:27:54 laptop kernel: [    0.087480] CPU0: Intel(R) Core(TM) i3 CPU       M 330  @ 2.13GHz stepping 02
Dec 24 10:27:54 laptop kernel: [    0.195000] Performance Events: PEBS fmt1+, Westmere events, Intel PMU driver.
Dec 24 10:27:54 laptop kernel: [    0.195243] ... version:                3
Dec 24 10:27:54 laptop kernel: [    0.195313] ... bit width:              48
Dec 24 10:27:54 laptop kernel: [    0.195385] ... generic registers:      4
Dec 24 10:27:54 laptop kernel: [    0.195457] ... value mask:             0000ffffffffffff
Dec 24 10:27:54 laptop kernel: [    0.195531] ... max period:             000000007fffffff
Dec 24 10:27:54 laptop kernel: [    0.195605] ... fixed-purpose events:   3
Dec 24 10:27:54 laptop kernel: [    0.195673] ... event mask:             000000070000000f
Dec 24 10:27:54 laptop kernel: [    0.196123] CPU 1 irqstacks, hard=f74ce000 soft=f74d8000
Dec 24 10:27:54 laptop kernel: [    0.196125] Booting Node   0, Processors  #1
Dec 24 10:27:54 laptop kernel: [    0.196236] smpboot cpu 1: start_ip = 99000
Dec 24 10:27:54 laptop kernel: [    0.206518] Initializing CPU#1
Dec 24 10:27:54 laptop kernel: [    0.307181] CPU 2 irqstacks, hard=f74e2000 soft=f74e4000
Dec 24 10:27:54 laptop kernel: [    0.307254]  #2
Dec 24 10:27:54 laptop kernel: [    0.307307] smpboot cpu 2: start_ip = 99000
Dec 24 10:27:54 laptop kernel: [    0.317517] Initializing CPU#2
Dec 24 10:27:54 laptop kernel: [    0.415072] CPU 3 irqstacks, hard=f750e000 soft=f7510000
Dec 24 10:27:54 laptop kernel: [    0.415150]  #3
Dec 24 10:27:54 laptop kernel: [    0.415202] smpboot cpu 3: start_ip = 99000
Dec 24 10:27:54 laptop kernel: [    0.425412] Initializing CPU#3
Dec 24 10:27:54 laptop kernel: [    0.522971] Brought up 4 CPUs
Dec 24 10:27:54 laptop kernel: [    0.523114] Total of 4 processors activated (17023.86 BogoMIPS).
Dec 24 10:27:54 laptop kernel: [    0.525660] devtmpfs: initialized
Dec 24 10:27:54 laptop kernel: [    0.525888] PM: Registering ACPI NVS region at bf75d000 (401408 bytes)
Dec 24 10:27:54 laptop kernel: [    0.527846] print_constraints: dummy: 
Dec 24 10:27:54 laptop kernel: [    0.527948] Time:  9:26:34  Date: 12/24/11
Dec 24 10:27:54 laptop kernel: [    0.528062] NET: Registered protocol family 16
Dec 24 10:27:54 laptop kernel: [    0.528242] Trying to unpack rootfs image as initramfs...
Dec 24 10:27:54 laptop kernel: [    0.528245] EISA bus registered
Dec 24 10:27:54 laptop kernel: [    0.528396] ACPI FADT declares the system doesn't support PCIe ASPM, so disable it
Dec 24 10:27:54 laptop kernel: [    0.528491] ACPI: bus type pci registered
Dec 24 10:27:54 laptop kernel: [    0.528632] PCI: MMCONFIG for domain 0000 [bus 00-ff] at [mem 0xe0000000-0xefffffff] (base 0xe0000000)
Dec 24 10:27:54 laptop kernel: [    0.528731] PCI: MMCONFIG at [mem 0xe0000000-0xefffffff] reserved in E820
Dec 24 10:27:54 laptop kernel: [    0.528806] PCI: Using MMCONFIG for extended config space
Dec 24 10:27:54 laptop kernel: [    0.528877] PCI: Using configuration type 1 for base access
Dec 24 10:27:54 laptop kernel: [    0.529827] bio: create slab <bio-0> at 0
Dec 24 10:27:54 laptop kernel: [    0.532498] ACPI: EC: Look up EC in DSDT
Dec 24 10:27:54 laptop kernel: [    0.534913] ACPI: Executed 1 blocks of module-level executable AML code
Dec 24 10:27:54 laptop kernel: [    0.566900] [Firmware Bug]: ACPI: BIOS _OSI(Linux) query ignored
Dec 24 10:27:54 laptop kernel: [    0.572440] ACPI: SSDT bf691c18 003A0 (v01  PmRef  Cpu0Ist 00003000 INTL 20060317)
Dec 24 10:27:54 laptop kernel: [    0.574947] ACPI: Dynamic OEM Table Load:
Dec 24 10:27:54 laptop kernel: [    0.575117] ACPI: SSDT   (null) 003A0 (v01  PmRef  Cpu0Ist 00003000 INTL 20060317)
Dec 24 10:27:54 laptop kernel: [    0.575463] ACPI: SSDT bf68f618 005CD (v01  PmRef  Cpu0Cst 00003001 INTL 20060317)
Dec 24 10:27:54 laptop kernel: [    0.576230] ACPI: Dynamic OEM Table Load:
Dec 24 10:27:54 laptop kernel: [    0.576399] ACPI: SSDT   (null) 005CD (v01  PmRef  Cpu0Cst 00003001 INTL 20060317)
Dec 24 10:27:54 laptop kernel: [    0.647143] ACPI: SSDT bf690a98 00303 (v01  PmRef    ApIst 00003000 INTL 20060317)
Dec 24 10:27:54 laptop kernel: [    0.647997] ACPI: Dynamic OEM Table Load:
Dec 24 10:27:54 laptop kernel: [    0.648170] ACPI: SSDT   (null) 00303 (v01  PmRef    ApIst 00003000 INTL 20060317)
Dec 24 10:27:54 laptop kernel: [    0.666955] ACPI: SSDT bf68ed98 00119 (v01  PmRef    ApCst 00003000 INTL 20060317)
Dec 24 10:27:54 laptop kernel: [    0.667764] ACPI: Dynamic OEM Table Load:
Dec 24 10:27:54 laptop kernel: [    0.667935] ACPI: SSDT   (null) 00119 (v01  PmRef    ApCst 00003000 INTL 20060317)
Dec 24 10:27:54 laptop kernel: [    0.698769] ACPI: Interpreter enabled
Dec 24 10:27:54 laptop kernel: [    0.698855] ACPI: (supports S0 S3 S4 S5)
Dec 24 10:27:54 laptop kernel: [    0.699187] ACPI: Using IOAPIC for interrupt routing
Dec 24 10:27:54 laptop kernel: [    0.738994] ACPI: EC: GPE = 0x16, I/O: command/status = 0x66, data = 0x62
Dec 24 10:27:54 laptop kernel: [    0.739364] ACPI: No dock devices found.
Dec 24 10:27:54 laptop kernel: [    0.739440] HEST: Table not found.
Dec 24 10:27:54 laptop kernel: [    0.739515] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
Dec 24 10:27:54 laptop kernel: [    0.740278] \_SB_.PCI0:_OSC invalid UUID
Dec 24 10:27:54 laptop kernel: [    0.740281] _OSC request data:1 8 1f 
Dec 24 10:27:54 laptop kernel: [    0.740287] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-fe])
Dec 24 10:27:54 laptop kernel: [    0.741465] pci_root PNP0A08:00: host bridge window [io  0x0000-0x0cf7]
Dec 24 10:27:54 laptop kernel: [    0.741549] pci_root PNP0A08:00: host bridge window [io  0x0d00-0xffff]
Dec 24 10:27:54 laptop kernel: [    0.741629] pci_root PNP0A08:00: host bridge window [mem 0x000a0000-0x000bffff]
Dec 24 10:27:54 laptop kernel: [    0.741726] pci_root PNP0A08:00: host bridge window [mem 0xc0000000-0xfeafffff]
Dec 24 10:27:54 laptop kernel: [    0.741839] pci 0000:00:00.0: [8086:0044] type 0 class 0x000600
Dec 24 10:27:54 laptop kernel: [    0.741865] DMAR: BIOS has allocated no shadow GTT; disabling IOMMU for graphics
Dec 24 10:27:54 laptop kernel: [    0.741981] pci 0000:00:01.0: [8086:0045] type 1 class 0x000604
Dec 24 10:27:54 laptop kernel: [    0.742017] pci 0000:00:01.0: PME# supported from D0 D3hot D3cold
Dec 24 10:27:54 laptop kernel: [    0.742021] pci 0000:00:01.0: PME# disabled
Dec 24 10:27:54 laptop kernel: [    0.742086] pci 0000:00:1a.0: [8086:3b3c] type 0 class 0x000c03
Dec 24 10:27:54 laptop kernel: [    0.742478] pci 0000:00:1a.0: reg 10: [mem 0xdb105c00-0xdb105fff]
Dec 24 10:27:54 laptop kernel: [    0.744736] pci 0000:00:1a.0: PME# supported from D0 D3hot D3cold
Dec 24 10:27:54 laptop kernel: [    0.744743] pci 0000:00:1a.0: PME# disabled
Dec 24 10:27:54 laptop kernel: [    0.744778] pci 0000:00:1b.0: [8086:3b56] type 0 class 0x000403
Dec 24 10:27:54 laptop kernel: [    0.744804] pci 0000:00:1b.0: reg 10: [mem 0xdb100000-0xdb103fff 64bit]
Dec 24 10:27:54 laptop kernel: [    0.744893] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
Dec 24 10:27:54 laptop kernel: [    0.744900] pci 0000:00:1b.0: PME# disabled
Dec 24 10:27:54 laptop kernel: [    0.744931] pci 0000:00:1c.0: [8086:3b42] type 1 class 0x000604
Dec 24 10:27:54 laptop kernel: [    0.745027] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
Dec 24 10:27:54 laptop kernel: [    0.745034] pci 0000:00:1c.0: PME# disabled
Dec 24 10:27:54 laptop kernel: [    0.745068] pci 0000:00:1c.1: [8086:3b44] type 1 class 0x000604
Dec 24 10:27:54 laptop kernel: [    0.745160] pci 0000:00:1c.1: PME# supported from D0 D3hot D3cold
Dec 24 10:27:54 laptop kernel: [    0.745166] pci 0000:00:1c.1: PME# disabled
Dec 24 10:27:54 laptop kernel: [    0.745203] pci 0000:00:1c.4: [8086:3b4a] type 1 class 0x000604
Dec 24 10:27:54 laptop kernel: [    0.745293] pci 0000:00:1c.4: PME# supported from D0 D3hot D3cold
Dec 24 10:27:54 laptop kernel: [    0.745300] pci 0000:00:1c.4: PME# disabled
Dec 24 10:27:54 laptop kernel: [    0.745337] pci 0000:00:1c.7: [8086:3b50] type 1 class 0x000604
Dec 24 10:27:54 laptop kernel: [    0.745430] pci 0000:00:1c.7: PME# supported from D0 D3hot D3cold
Dec 24 10:27:54 laptop kernel: [    0.745437] pci 0000:00:1c.7: PME# disabled
Dec 24 10:27:54 laptop kernel: [    0.745481] pci 0000:00:1d.0: [8086:3b34] type 0 class 0x000c03
Dec 24 10:27:54 laptop kernel: [    0.745870] pci 0000:00:1d.0: reg 10: [mem 0xdb105800-0xdb105bff]
Dec 24 10:27:54 laptop kernel: [    0.748129] pci 0000:00:1d.0: PME# supported from D0 D3hot D3cold
Dec 24 10:27:54 laptop kernel: [    0.748135] pci 0000:00:1d.0: PME# disabled
Dec 24 10:27:54 laptop kernel: [    0.748165] pci 0000:00:1e.0: [8086:2448] type 1 class 0x000604
Dec 24 10:27:54 laptop kernel: [    0.748254] pci 0000:00:1f.0: [8086:3b03] type 0 class 0x000601
Dec 24 10:27:54 laptop kernel: [    0.748386] pci 0000:00:1f.2: [8086:3b2f] type 0 class 0x000106
Dec 24 10:27:54 laptop kernel: [    0.748415] pci 0000:00:1f.2: reg 10: [io  0x7048-0x704f]
Dec 24 10:27:54 laptop kernel: [    0.748427] pci 0000:00:1f.2: reg 14: [io  0x7054-0x7057]
Dec 24 10:27:54 laptop kernel: [    0.748439] pci 0000:00:1f.2: reg 18: [io  0x7040-0x7047]
Dec 24 10:27:54 laptop kernel: [    0.748451] pci 0000:00:1f.2: reg 1c: [io  0x7050-0x7053]
Dec 24 10:27:54 laptop kernel: [    0.748462] pci 0000:00:1f.2: reg 20: [io  0x7020-0x703f]
Dec 24 10:27:54 laptop kernel: [    0.748474] pci 0000:00:1f.2: reg 24: [mem 0xdb105000-0xdb1057ff]
Dec 24 10:27:54 laptop kernel: [    0.748525] pci 0000:00:1f.2: PME# supported from D3hot
Dec 24 10:27:54 laptop kernel: [    0.748530] pci 0000:00:1f.2: PME# disabled
Dec 24 10:27:54 laptop kernel: [    0.748553] pci 0000:00:1f.3: [8086:3b30] type 0 class 0x000c05
Dec 24 10:27:54 laptop kernel: [    0.748576] pci 0000:00:1f.3: reg 10: [mem 0xdb106000-0xdb1060ff 64bit]
Dec 24 10:27:54 laptop kernel: [    0.748608] pci 0000:00:1f.3: reg 20: [io  0x7000-0x701f]
Dec 24 10:27:54 laptop kernel: [    0.748681] pci 0000:01:00.0: [10de:0a68] type 0 class 0x000300
Dec 24 10:27:54 laptop kernel: [    0.748692] pci 0000:01:00.0: reg 10: [mem 0xd2000000-0xd2ffffff]
Dec 24 10:27:54 laptop kernel: [    0.748702] pci 0000:01:00.0: reg 14: [mem 0xc0000000-0xcfffffff 64bit pref]
Dec 24 10:27:54 laptop kernel: [    0.748713] pci 0000:01:00.0: reg 1c: [mem 0xd0000000-0xd1ffffff 64bit pref]
Dec 24 10:27:54 laptop kernel: [    0.748721] pci 0000:01:00.0: reg 24: [io  0x6000-0x607f]
Dec 24 10:27:54 laptop kernel: [    0.748728] pci 0000:01:00.0: reg 30: [mem 0xfff80000-0xffffffff pref]
Dec 24 10:27:54 laptop kernel: [    0.748770] pci 0000:01:00.1: [10de:0be3] type 0 class 0x000403
Dec 24 10:27:54 laptop kernel: [    0.748780] pci 0000:01:00.1: reg 10: [mem 0xd3000000-0xd3003fff]
Dec 24 10:27:54 laptop kernel: [    0.748851] pci 0000:00:01.0: PCI bridge to [bus 01-01]
Dec 24 10:27:54 laptop kernel: [    0.748926] pci 0000:00:01.0:   bridge window [io  0x6000-0x6fff]
Dec 24 10:27:54 laptop kernel: [    0.748930] pci 0000:00:01.0:   bridge window [mem 0xd2000000-0xd30fffff]
Dec 24 10:27:54 laptop kernel: [    0.748934] pci 0000:00:01.0:   bridge window [mem 0xc0000000-0xd1ffffff 64bit pref]
Dec 24 10:27:54 laptop kernel: [    0.749054] pci 0000:02:00.0: [14e4:4357] type 0 class 0x000280
Dec 24 10:27:54 laptop kernel: [    0.749122] pci 0000:02:00.0: reg 10: [mem 0xda100000-0xda103fff 64bit]
Dec 24 10:27:54 laptop kernel: [    0.749405] pci 0000:02:00.0: supports D1 D2
Dec 24 10:27:54 laptop kernel: [    0.749512] pci 0000:00:1c.0: PCI bridge to [bus 02-02]
Dec 24 10:27:54 laptop kernel: [    0.749589] pci 0000:00:1c.0:   bridge window [io  0x5000-0x5fff]
Dec 24 10:27:54 laptop kernel: [    0.749594] pci 0000:00:1c.0:   bridge window [mem 0xda100000-0xdb0fffff]
Dec 24 10:27:54 laptop kernel: [    0.749602] pci 0000:00:1c.0:   bridge window [mem 0xd3100000-0xd40fffff 64bit pref]
Dec 24 10:27:54 laptop kernel: [    0.749732] pci 0000:03:00.0: [10ec:8168] type 0 class 0x000200
Dec 24 10:27:54 laptop kernel: [    0.749797] pci 0000:03:00.0: reg 10: [io  0x4000-0x40ff]
Dec 24 10:27:54 laptop kernel: [    0.749911] pci 0000:03:00.0: reg 18: [mem 0xd4104000-0xd4104fff 64bit pref]
Dec 24 10:27:54 laptop kernel: [    0.749982] pci 0000:03:00.0: reg 20: [mem 0xd4100000-0xd4103fff 64bit pref]
Dec 24 10:27:54 laptop kernel: [    0.750028] pci 0000:03:00.0: reg 30: [mem 0xffff0000-0xffffffff pref]
Dec 24 10:27:54 laptop kernel: [    0.750187] pci 0000:03:00.0: supports D1 D2
Dec 24 10:27:54 laptop kernel: [    0.750189] pci 0000:03:00.0: PME# supported from D0 D1 D2 D3hot D3cold
Dec 24 10:27:54 laptop kernel: [    0.750204] pci 0000:03:00.0: PME# disabled
Dec 24 10:27:54 laptop kernel: [    0.750273] pci 0000:00:1c.1: PCI bridge to [bus 03-03]
Dec 24 10:27:54 laptop kernel: [    0.750348] pci 0000:00:1c.1:   bridge window [io  0x4000-0x4fff]
Dec 24 10:27:54 laptop kernel: [    0.750353] pci 0000:00:1c.1:   bridge window [mem 0xd9100000-0xda0fffff]
Dec 24 10:27:54 laptop kernel: [    0.750361] pci 0000:00:1c.1:   bridge window [mem 0xd4100000-0xd50fffff 64bit pref]
Dec 24 10:27:54 laptop kernel: [    0.750451] pci 0000:04:00.0: [197b:2380] type 0 class 0x000c00
Dec 24 10:27:54 laptop kernel: [    0.750489] pci 0000:04:00.0: reg 10: [mem 0xd8100000-0xd81007ff]
Dec 24 10:27:54 laptop kernel: [    0.750516] pci 0000:04:00.0: reg 14: [mem 0xd8100d00-0xd8100d7f]
Dec 24 10:27:54 laptop kernel: [    0.750592] pci 0000:04:00.0: reg 20: [mem 0xd8100c80-0xd8100cff]
Dec 24 10:27:54 laptop kernel: [    0.750620] pci 0000:04:00.0: reg 24: [mem 0xd8100c00-0xd8100c7f]
Dec 24 10:27:54 laptop kernel: [    0.750774] pci 0000:04:00.1: [197b:2382] type 0 class 0x000880
Dec 24 10:27:54 laptop kernel: [    0.750807] pci 0000:04:00.1: reg 10: [mem 0xd8100b00-0xd8100bff]
Dec 24 10:27:54 laptop kernel: [    0.751062] pci 0000:04:00.2: [197b:2381] type 0 class 0x000805
Dec 24 10:27:54 laptop kernel: [    0.751096] pci 0000:04:00.2: reg 10: [mem 0xd8100a00-0xd8100aff]
Dec 24 10:27:54 laptop kernel: [    0.751346] pci 0000:04:00.3: [197b:2383] type 0 class 0x000880
Dec 24 10:27:54 laptop kernel: [    0.751380] pci 0000:04:00.3: reg 10: [mem 0xd8100900-0xd81009ff]
Dec 24 10:27:54 laptop kernel: [    0.751631] pci 0000:04:00.4: [197b:2384] type 0 class 0x000880
Dec 24 10:27:54 laptop kernel: [    0.751664] pci 0000:04:00.4: reg 10: [mem 0xd8100800-0xd81008ff]
Dec 24 10:27:54 laptop kernel: [    0.751931] pci 0000:00:1c.4: PCI bridge to [bus 04-04]
Dec 24 10:27:54 laptop kernel: [    0.752007] pci 0000:00:1c.4:   bridge window [io  0x3000-0x3fff]
Dec 24 10:27:54 laptop kernel: [    0.752012] pci 0000:00:1c.4:   bridge window [mem 0xd8100000-0xd90fffff]
Dec 24 10:27:54 laptop kernel: [    0.752020] pci 0000:00:1c.4:   bridge window [mem 0xd5100000-0xd60fffff 64bit pref]
Dec 24 10:27:54 laptop kernel: [    0.752079] pci 0000:00:1c.7: PCI bridge to [bus 05-08]
Dec 24 10:27:54 laptop kernel: [    0.752154] pci 0000:00:1c.7:   bridge window [io  0x2000-0x2fff]
Dec 24 10:27:54 laptop kernel: [    0.752160] pci 0000:00:1c.7:   bridge window [mem 0xd7100000-0xd80fffff]
Dec 24 10:27:54 laptop kernel: [    0.752168] pci 0000:00:1c.7:   bridge window [mem 0xd6100000-0xd70fffff 64bit pref]
Dec 24 10:27:54 laptop kernel: [    0.752247] pci 0000:00:1e.0: PCI bridge to [bus 09-09] (subtractive decode)
Dec 24 10:27:54 laptop kernel: [    0.752324] pci 0000:00:1e.0:   bridge window [io  0xf000-0x0000] (disabled)
Dec 24 10:27:54 laptop kernel: [    0.752330] pci 0000:00:1e.0:   bridge window [mem 0xfff00000-0x000fffff] (disabled)
Dec 24 10:27:54 laptop kernel: [    0.752338] pci 0000:00:1e.0:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
Dec 24 10:27:54 laptop kernel: [    0.752341] pci 0000:00:1e.0:   bridge window [io  0x0000-0x0cf7] (subtractive decode)
Dec 24 10:27:54 laptop kernel: [    0.752343] pci 0000:00:1e.0:   bridge window [io  0x0d00-0xffff] (subtractive decode)
Dec 24 10:27:54 laptop kernel: [    0.752346] pci 0000:00:1e.0:   bridge window [mem 0x000a0000-0x000bffff] (subtractive decode)
Dec 24 10:27:54 laptop kernel: [    0.752348] pci 0000:00:1e.0:   bridge window [mem 0xc0000000-0xfeafffff] (subtractive decode)
Dec 24 10:27:54 laptop kernel: [    0.752382] pci_bus 0000:00: on NUMA node 0
Dec 24 10:27:54 laptop kernel: [    0.752387] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
Dec 24 10:27:54 laptop kernel: [    0.752557] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P3._PRT]
Dec 24 10:27:54 laptop kernel: [    0.752598] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P1._PRT]
Dec 24 10:27:54 laptop kernel: [    0.752615] ACPI Warning: For \_SB_.PCI0.P0P1._PRT: Return Package has no elements (empty) (20110413/nspredef-457)
Dec 24 10:27:54 laptop kernel: [    0.752842] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP01._PRT]
Dec 24 10:27:54 laptop kernel: [    0.752882] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP02._PRT]
Dec 24 10:27:54 laptop kernel: [    0.752930] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP05._PRT]
Dec 24 10:27:54 laptop kernel: [    0.752993] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP08._PRT]
Dec 24 10:27:54 laptop kernel: [    0.753084] \_SB_.PCI0:_OSC invalid UUID
Dec 24 10:27:54 laptop kernel: [    0.753086] _OSC request data:1 1f 1f 
Dec 24 10:27:54 laptop kernel: [    0.753091]  pci0000:00: Requesting ACPI _OSC control (0x1d)
Dec 24 10:27:54 laptop kernel: [    0.753201] \_SB_.PCI0:_OSC invalid UUID
Dec 24 10:27:54 laptop kernel: [    0.753203] _OSC request data:1 0 1d 
Dec 24 10:27:54 laptop kernel: [    0.753207]  pci0000:00: ACPI _OSC request failed (AE_ERROR), returned control mask: 0x1d
Dec 24 10:27:54 laptop kernel: [    0.753300] ACPI _OSC control for PCIe not granted, disabling ASPM
Dec 24 10:27:54 laptop kernel: [    0.758641] ACPI: PCI Root Bridge [CPBG] (domain 0000 [bus ff])
Dec 24 10:27:54 laptop kernel: [    0.758786] pci 0000:ff:00.0: [8086:2c62] type 0 class 0x000600
Dec 24 10:27:54 laptop kernel: [    0.758809] pci 0000:ff:00.1: [8086:2d01] type 0 class 0x000600
Dec 24 10:27:54 laptop kernel: [    0.758834] pci 0000:ff:02.0: [8086:2d10] type 0 class 0x000600
Dec 24 10:27:54 laptop kernel: [    0.758853] pci 0000:ff:02.1: [8086:2d11] type 0 class 0x000600
Dec 24 10:27:54 laptop kernel: [    0.758877] pci 0000:ff:02.2: [8086:2d12] type 0 class 0x000600
Dec 24 10:27:54 laptop kernel: [    0.758897] pci 0000:ff:02.3: [8086:2d13] type 0 class 0x000600
Dec 24 10:27:54 laptop kernel: [    0.758928] pci_bus 0000:ff: on NUMA node 0
Dec 24 10:27:54 laptop kernel: [    0.758936]  pci0000:ff: Requesting ACPI _OSC control (0x1d)
Dec 24 10:27:54 laptop kernel: [    0.759011]  pci0000:ff: ACPI _OSC request failed (AE_NOT_FOUND), returned control mask: 0x1d
Dec 24 10:27:54 laptop kernel: [    0.759104] ACPI _OSC control for PCIe not granted, disabling ASPM
Dec 24 10:27:54 laptop kernel: [    0.759418] ACPI: PCI Interrupt Link [LNKA] (IRQs 1 3 4 *5 6 7 10 12 14 15)
Dec 24 10:27:54 laptop kernel: [    0.760130] ACPI: PCI Interrupt Link [LNKB] (IRQs 1 3 4 *5 6 7 11 12 14 15)
Dec 24 10:27:54 laptop kernel: [    0.760840] ACPI: PCI Interrupt Link [LNKC] (IRQs 1 3 4 5 6 7 10 12 14 15) *11
Dec 24 10:27:54 laptop kernel: [    0.761610] ACPI: PCI Interrupt Link [LNKD] (IRQs 1 3 4 *5 6 7 11 12 14 15)
Dec 24 10:27:54 laptop kernel: [    0.762316] ACPI: PCI Interrupt Link [LNKE] (IRQs 1 3 4 5 6 7 10 12 14 15) *0, disabled.
Dec 24 10:27:54 laptop kernel: [    0.763146] ACPI: PCI Interrupt Link [LNKF] (IRQs 1 3 4 5 6 7 *11 12 14 15)
Dec 24 10:27:54 laptop kernel: [    0.763852] ACPI: PCI Interrupt Link [LNKG] (IRQs 1 3 4 5 6 7 *10 12 14 15)
Dec 24 10:27:54 laptop kernel: [    0.764561] ACPI: PCI Interrupt Link [LNKH] (IRQs 1 3 4 5 6 7 11 12 14 15) *0, disabled.
Dec 24 10:27:54 laptop kernel: [    0.765446] vgaarb: device added: PCI:0000:01:00.0,decodes=io+mem,owns=io+mem,locks=none
Dec 24 10:27:54 laptop kernel: [    0.765544] vgaarb: loaded
Dec 24 10:27:54 laptop kernel: [    0.765613] vgaarb: bridge control possible 0000:01:00.0
Dec 24 10:27:54 laptop kernel: [    0.765885] SCSI subsystem initialized
Dec 24 10:27:54 laptop kernel: [    0.766031] libata version 3.00 loaded.
Dec 24 10:27:54 laptop kernel: [    0.766076] usbcore: registered new interface driver usbfs
Dec 24 10:27:54 laptop kernel: [    0.766157] usbcore: registered new interface driver hub
Dec 24 10:27:54 laptop kernel: [    0.766259] usbcore: registered new device driver usb
Dec 24 10:27:54 laptop kernel: [    0.766416] PCI: Using ACPI for IRQ routing
Dec 24 10:27:54 laptop kernel: [    0.776447] PCI: pci_cache_line_size set to 64 bytes
Dec 24 10:27:54 laptop kernel: [    0.776575] reserve RAM buffer: 000000000009d000 - 000000000009ffff 
Dec 24 10:27:54 laptop kernel: [    0.776578] reserve RAM buffer: 00000000bf681000 - 00000000bfffffff 
Dec 24 10:27:54 laptop kernel: [    0.776581] reserve RAM buffer: 00000000bf75d000 - 00000000bfffffff 
Dec 24 10:27:54 laptop kernel: [    0.776584] reserve RAM buffer: 00000000bf7e1000 - 00000000bfffffff 
Dec 24 10:27:54 laptop kernel: [    0.776587] reserve RAM buffer: 00000000bf800000 - 00000000bfffffff 
Dec 24 10:27:54 laptop kernel: [    0.776696] NetLabel: Initializing
Dec 24 10:27:54 laptop kernel: [    0.776767] NetLabel:  domain hash size = 128
Dec 24 10:27:54 laptop kernel: [    0.776838] NetLabel:  protocols = UNLABELED CIPSOv4
Dec 24 10:27:54 laptop kernel: [    0.776921] NetLabel:  unlabeled traffic allowed by default
Dec 24 10:27:54 laptop kernel: [    0.777053] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0, 0, 0, 0, 0
Dec 24 10:27:54 laptop kernel: [    0.777569] hpet0: 8 comparators, 64-bit 14.318180 MHz counter
Dec 24 10:27:54 laptop kernel: [    0.779668] Switching to clocksource hpet
Dec 24 10:27:54 laptop kernel: [    0.782752] Switched to NOHz mode on CPU #0
Dec 24 10:27:54 laptop kernel: [    0.782822] Switched to NOHz mode on CPU #2
Dec 24 10:27:54 laptop kernel: [    0.782860] Switched to NOHz mode on CPU #3
Dec 24 10:27:54 laptop kernel: [    0.782888] Switched to NOHz mode on CPU #1
Dec 24 10:27:54 laptop kernel: [    0.786214] AppArmor: AppArmor Filesystem Enabled
Dec 24 10:27:54 laptop kernel: [    0.786313] pnp: PnP ACPI init
Dec 24 10:27:54 laptop kernel: [    0.786397] ACPI: bus type pnp registered
Dec 24 10:27:54 laptop kernel: [    0.787170] pnp 00:00: [bus 00-fe]
Dec 24 10:27:54 laptop kernel: [    0.787173] pnp 00:00: [io  0x0000-0x0cf7 window]
Dec 24 10:27:54 laptop kernel: [    0.787175] pnp 00:00: [io  0x0cf8-0x0cff]
Dec 24 10:27:54 laptop kernel: [    0.787178] pnp 00:00: [io  0x0d00-0xffff window]
Dec 24 10:27:54 laptop kernel: [    0.787180] pnp 00:00: [mem 0x000a0000-0x000bffff window]
Dec 24 10:27:54 laptop kernel: [    0.787182] pnp 00:00: [mem 0x000c0000-0x000c3fff window]
Dec 24 10:27:54 laptop kernel: [    0.787184] pnp 00:00: [mem 0x000c4000-0x000c7fff window]
Dec 24 10:27:54 laptop kernel: [    0.787187] pnp 00:00: [mem 0x000c8000-0x000cbfff window]
Dec 24 10:27:54 laptop kernel: [    0.787189] pnp 00:00: [mem 0x000cc000-0x000cffff window]
Dec 24 10:27:54 laptop kernel: [    0.787191] pnp 00:00: [mem 0x000d0000-0x000d3fff window]
Dec 24 10:27:54 laptop kernel: [    0.787193] pnp 00:00: [mem 0x000d4000-0x000d7fff window]
Dec 24 10:27:54 laptop kernel: [    0.787195] pnp 00:00: [mem 0x000d8000-0x000dbfff window]
Dec 24 10:27:54 laptop kernel: [    0.787198] pnp 00:00: [mem 0x000dc000-0x000dffff window]
Dec 24 10:27:54 laptop kernel: [    0.787200] pnp 00:00: [mem 0x000e0000-0x000e3fff window]
Dec 24 10:27:54 laptop kernel: [    0.787202] pnp 00:00: [mem 0x000e4000-0x000e7fff window]
Dec 24 10:27:54 laptop kernel: [    0.787204] pnp 00:00: [mem 0x000e8000-0x000ebfff window]
Dec 24 10:27:54 laptop kernel: [    0.787206] pnp 00:00: [mem 0x000ec000-0x000effff window]
Dec 24 10:27:54 laptop kernel: [    0.787209] pnp 00:00: [mem 0x000f0000-0x000fffff window]
Dec 24 10:27:54 laptop kernel: [    0.787211] pnp 00:00: [mem 0xc0000000-0xfeafffff window]
Dec 24 10:27:54 laptop kernel: [    0.787213] pnp 00:00: [mem 0xfed40000-0xfed44fff window]
Dec 24 10:27:54 laptop kernel: [    0.787291] pnp 00:00: Plug and Play ACPI device, IDs PNP0a08 PNP0a03 (active)
Dec 24 10:27:54 laptop kernel: [    0.787366] pnp 00:01: [io  0x0380-0x038e]
Dec 24 10:27:54 laptop kernel: [    0.787378] pnp 00:01: [irq 4]
Dec 24 10:27:54 laptop kernel: [    0.787413] pnp 00:01: Plug and Play ACPI device, IDs ENE0100 (active)
Dec 24 10:27:54 laptop kernel: [    0.787423] pnp 00:02: [io  0x0000-0x001f]
Dec 24 10:27:54 laptop kernel: [    0.787425] pnp 00:02: [io  0x0081-0x0091]
Dec 24 10:27:54 laptop kernel: [    0.787427] pnp 00:02: [io  0x0093-0x009f]
Dec 24 10:27:54 laptop kernel: [    0.787429] pnp 00:02: [io  0x00c0-0x00df]
Dec 24 10:27:54 laptop kernel: [    0.787431] pnp 00:02: [dma 4]
Dec 24 10:27:54 laptop kernel: [    0.787460] pnp 00:02: Plug and Play ACPI device, IDs PNP0200 (active)
Dec 24 10:27:54 laptop kernel: [    0.787468] pnp 00:03: [mem 0xff000000-0xffffffff]
Dec 24 10:27:54 laptop kernel: [    0.787497] pnp 00:03: Plug and Play ACPI device, IDs INT0800 (active)
Dec 24 10:27:54 laptop kernel: [    0.787590] pnp 00:04: [mem 0xfed00000-0xfed003ff]
Dec 24 10:27:54 laptop kernel: [    0.787620] pnp 00:04: Plug and Play ACPI device, IDs PNP0103 (active)
Dec 24 10:27:54 laptop kernel: [    0.787631] pnp 00:05: [io  0x00f0]
Dec 24 10:27:54 laptop kernel: [    0.787637] pnp 00:05: [irq 13]
Dec 24 10:27:54 laptop kernel: [    0.787667] pnp 00:05: Plug and Play ACPI device, IDs PNP0c04 (active)
Dec 24 10:27:54 laptop kernel: [    0.787679] pnp 00:06: [io  0x002e-0x002f]
Dec 24 10:27:54 laptop kernel: [    0.787681] pnp 00:06: [io  0x004e-0x004f]
Dec 24 10:27:54 laptop kernel: [    0.787683] pnp 00:06: [io  0x0061]
Dec 24 10:27:54 laptop kernel: [    0.787685] pnp 00:06: [io  0x0063]
Dec 24 10:27:54 laptop kernel: [    0.787688] pnp 00:06: [io  0x0065]
Dec 24 10:27:54 laptop kernel: [    0.787690] pnp 00:06: [io  0x0067]
Dec 24 10:27:54 laptop kernel: [    0.787692] pnp 00:06: [io  0x0070]
Dec 24 10:27:54 laptop kernel: [    0.787693] pnp 00:06: [io  0x0080]
Dec 24 10:27:54 laptop kernel: [    0.787695] pnp 00:06: [io  0x0092]
Dec 24 10:27:54 laptop kernel: [    0.787697] pnp 00:06: [io  0x00b2-0x00b3]
Dec 24 10:27:54 laptop kernel: [    0.787699] pnp 00:06: [io  0x0680-0x069f]
Dec 24 10:27:54 laptop kernel: [    0.787701] pnp 00:06: [io  0x0800-0x080f]
Dec 24 10:27:54 laptop kernel: [    0.787702] pnp 00:06: [io  0xffff]
Dec 24 10:27:54 laptop kernel: [    0.787704] pnp 00:06: [io  0xffff]
Dec 24 10:27:54 laptop kernel: [    0.787706] pnp 00:06: [io  0x0400-0x047f]
Dec 24 10:27:54 laptop kernel: [    0.787708] pnp 00:06: [io  0x0500-0x057f]
Dec 24 10:27:54 laptop kernel: [    0.787710] pnp 00:06: [io  0x164e-0x164f]
Dec 24 10:27:54 laptop kernel: [    0.787712] pnp 00:06: [io  0x0380-0x038e]
Dec 24 10:27:54 laptop kernel: [    0.787811] system 00:06: [io  0x0680-0x069f] has been reserved
Dec 24 10:27:54 laptop kernel: [    0.787888] system 00:06: [io  0x0800-0x080f] has been reserved
Dec 24 10:27:54 laptop kernel: [    0.787963] system 00:06: [io  0xffff] has been reserved
Dec 24 10:27:54 laptop kernel: [    0.788036] system 00:06: [io  0xffff] has been reserved
Dec 24 10:27:54 laptop kernel: [    0.788110] system 00:06: [io  0x0400-0x047f] has been reserved
Dec 24 10:27:54 laptop kernel: [    0.788184] system 00:06: [io  0x0500-0x057f] has been reserved
Dec 24 10:27:54 laptop kernel: [    0.788260] system 00:06: [io  0x164e-0x164f] has been reserved
Dec 24 10:27:54 laptop kernel: [    0.788337] system 00:06: [io  0x0380-0x038e] has been reserved
Dec 24 10:27:54 laptop kernel: [    0.788413] system 00:06: Plug and Play ACPI device, IDs PNP0c02 (active)
Dec 24 10:27:54 laptop kernel: [    0.788423] pnp 00:07: [io  0x0070-0x0077]
Dec 24 10:27:54 laptop kernel: [    0.788429] pnp 00:07: [irq 8]
Dec 24 10:27:54 laptop kernel: [    0.788460] pnp 00:07: Plug and Play ACPI device, IDs PNP0b00 (active)
Dec 24 10:27:54 laptop kernel: [    0.788471] pnp 00:08: [io  0x0060]
Dec 24 10:27:54 laptop kernel: [    0.788473] pnp 00:08: [io  0x0064]
Dec 24 10:27:54 laptop kernel: [    0.788478] pnp 00:08: [irq 1]
Dec 24 10:27:54 laptop kernel: [    0.788520] pnp 00:08: Plug and Play ACPI device, IDs PNP0303 (active)
Dec 24 10:27:54 laptop kernel: [    0.788540] pnp 00:09: [irq 12]
Dec 24 10:27:54 laptop kernel: [    0.788579] pnp 00:09: Plug and Play ACPI device, IDs SYN1e10 SYN1e00 SYN0002 PNP0f13 (active)
Dec 24 10:27:54 laptop kernel: [    0.788728] pnp 00:0a: [irq 23]
Dec 24 10:27:54 laptop kernel: [    0.788771] pnp 00:0a: Plug and Play ACPI device, IDs HPQ0004 (active)
Dec 24 10:27:54 laptop kernel: [    0.788984] pnp 00:0b: [mem 0xfed1c000-0xfed1ffff]
Dec 24 10:27:54 laptop kernel: [    0.788987] pnp 00:0b: [mem 0xfed10000-0xfed13fff]
Dec 24 10:27:54 laptop kernel: [    0.788989] pnp 00:0b: [mem 0xfed18000-0xfed18fff]
Dec 24 10:27:54 laptop kernel: [    0.788991] pnp 00:0b: [mem 0xfed19000-0xfed19fff]
Dec 24 10:27:54 laptop kernel: [    0.788993] pnp 00:0b: [mem 0xe0000000-0xefffffff]
Dec 24 10:27:54 laptop kernel: [    0.788995] pnp 00:0b: [mem 0xfed20000-0xfed3ffff]
Dec 24 10:27:54 laptop kernel: [    0.788997] pnp 00:0b: [mem 0xfed90000-0xfed8ffff disabled]
Dec 24 10:27:54 laptop kernel: [    0.788999] pnp 00:0b: [mem 0xfed45000-0xfed8ffff]
Dec 24 10:27:54 laptop kernel: [    0.789001] pnp 00:0b: [mem 0xff000000-0xffffffff]
Dec 24 10:27:54 laptop kernel: [    0.789003] pnp 00:0b: [mem 0xfee00000-0xfeefffff]
Dec 24 10:27:54 laptop kernel: [    0.789005] pnp 00:0b: [mem 0xdb200000-0xdb200fff]
Dec 24 10:27:54 laptop kernel: [    0.789077] system 00:0b: [mem 0xfed1c000-0xfed1ffff] has been reserved
Dec 24 10:27:54 laptop kernel: [    0.789155] system 00:0b: [mem 0xfed10000-0xfed13fff] has been reserved
Dec 24 10:27:54 laptop kernel: [    0.789233] system 00:0b: [mem 0xfed18000-0xfed18fff] has been reserved
Dec 24 10:27:54 laptop kernel: [    0.789306] system 00:0b: [mem 0xfed19000-0xfed19fff] has been reserved
Dec 24 10:27:54 laptop kernel: [    0.789383] system 00:0b: [mem 0xe0000000-0xefffffff] has been reserved
Dec 24 10:27:54 laptop kernel: [    0.789460] system 00:0b: [mem 0xfed20000-0xfed3ffff] has been reserved
Dec 24 10:27:54 laptop kernel: [    0.789537] system 00:0b: [mem 0xfed45000-0xfed8ffff] has been reserved
Dec 24 10:27:54 laptop kernel: [    0.789614] system 00:0b: [mem 0xff000000-0xffffffff] could not be reserved
Dec 24 10:27:54 laptop kernel: [    0.789689] system 00:0b: [mem 0xfee00000-0xfeefffff] could not be reserved
Dec 24 10:27:54 laptop kernel: [    0.789765] system 00:0b: [mem 0xdb200000-0xdb200fff] has been reserved
Dec 24 10:27:54 laptop kernel: [    0.789844] system 00:0b: Plug and Play ACPI device, IDs PNP0c02 (active)
Dec 24 10:27:54 laptop kernel: [    0.789998] pnp 00:0c: [bus ff]
Dec 24 10:27:54 laptop kernel: [    0.790042] pnp 00:0c: Plug and Play ACPI device, IDs PNP0a03 (active)
Dec 24 10:27:54 laptop kernel: [    0.790058] pnp: PnP ACPI: found 13 devices
Dec 24 10:27:54 laptop kernel: [    0.790130] ACPI: ACPI bus type pnp unregistered
Dec 24 10:27:54 laptop kernel: [    0.790205] PnPBIOS: Disabled by ACPI PNP
Dec 24 10:27:54 laptop kernel: [    0.826173] pci 0000:01:00.0: no compatible bridge window for [mem 0xfff80000-0xffffffff pref]
Dec 24 10:27:54 laptop kernel: [    0.826274] pci 0000:03:00.0: no compatible bridge window for [mem 0xffff0000-0xffffffff pref]
Dec 24 10:27:54 laptop kernel: [    0.826377] PCI: max bus depth: 1 pci_try_num: 2
Dec 24 10:27:54 laptop kernel: [    0.826440] pci 0000:01:00.0: BAR 6: assigned [mem 0xd3080000-0xd30fffff pref]
Dec 24 10:27:54 laptop kernel: [    0.826530] pci 0000:00:01.0: PCI bridge to [bus 01-01]
Dec 24 10:27:54 laptop kernel: [    0.826605] pci 0000:00:01.0:   bridge window [io  0x6000-0x6fff]
Dec 24 10:27:54 laptop kernel: [    0.826681] pci 0000:00:01.0:   bridge window [mem 0xd2000000-0xd30fffff]
Dec 24 10:27:54 laptop kernel: [    0.826759] pci 0000:00:01.0:   bridge window [mem 0xc0000000-0xd1ffffff 64bit pref]
Dec 24 10:27:54 laptop kernel: [    0.826854] pci 0000:00:1c.0: PCI bridge to [bus 02-02]
Dec 24 10:27:54 laptop kernel: [    0.826928] pci 0000:00:1c.0:   bridge window [io  0x5000-0x5fff]
Dec 24 10:27:54 laptop kernel: [    0.827007] pci 0000:00:1c.0:   bridge window [mem 0xda100000-0xdb0fffff]
Dec 24 10:27:54 laptop kernel: [    0.827088] pci 0000:00:1c.0:   bridge window [mem 0xd3100000-0xd40fffff 64bit pref]
Dec 24 10:27:54 laptop kernel: [    0.827184] pci 0000:03:00.0: BAR 6: assigned [mem 0xd4110000-0xd411ffff pref]
Dec 24 10:27:54 laptop kernel: [    0.827274] pci 0000:00:1c.1: PCI bridge to [bus 03-03]
Dec 24 10:27:54 laptop kernel: [    0.827350] pci 0000:00:1c.1:   bridge window [io  0x4000-0x4fff]
Dec 24 10:27:54 laptop kernel: [    0.827429] pci 0000:00:1c.1:   bridge window [mem 0xd9100000-0xda0fffff]
Dec 24 10:27:54 laptop kernel: [    0.827509] pci 0000:00:1c.1:   bridge window [mem 0xd4100000-0xd50fffff 64bit pref]
Dec 24 10:27:54 laptop kernel: [    0.827610] pci 0000:00:1c.4: PCI bridge to [bus 04-04]
Dec 24 10:27:54 laptop kernel: [    0.827686] pci 0000:00:1c.4:   bridge window [io  0x3000-0x3fff]
Dec 24 10:27:54 laptop kernel: [    0.827772] pci 0000:00:1c.4:   bridge window [mem 0xd8100000-0xd90fffff]
Dec 24 10:27:54 laptop kernel: [    0.827853] pci 0000:00:1c.4:   bridge window [mem 0xd5100000-0xd60fffff 64bit pref]
Dec 24 10:27:54 laptop kernel: [    0.827951] pci 0000:00:1c.7: PCI bridge to [bus 05-08]
Dec 24 10:27:54 laptop kernel: [    0.828025] pci 0000:00:1c.7:   bridge window [io  0x2000-0x2fff]
Dec 24 10:27:54 laptop kernel: [    0.828105] pci 0000:00:1c.7:   bridge window [mem 0xd7100000-0xd80fffff]
Dec 24 10:27:54 laptop kernel: [    0.828184] pci 0000:00:1c.7:   bridge window [mem 0xd6100000-0xd70fffff 64bit pref]
Dec 24 10:27:54 laptop kernel: [    0.828280] pci 0000:00:1e.0: PCI bridge to [bus 09-09]
Dec 24 10:27:54 laptop kernel: [    0.828352] pci 0000:00:1e.0:   bridge window [io  disabled]
Dec 24 10:27:54 laptop kernel: [    0.828430] pci 0000:00:1e.0:   bridge window [mem disabled]
Dec 24 10:27:54 laptop kernel: [    0.828507] pci 0000:00:1e.0:   bridge window [mem pref disabled]
Dec 24 10:27:54 laptop kernel: [    0.828610] pci 0000:00:01.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Dec 24 10:27:54 laptop kernel: [    0.828688] pci 0000:00:01.0: setting latency timer to 64
Dec 24 10:27:54 laptop kernel: [    0.828701] pci 0000:00:1c.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
Dec 24 10:27:54 laptop kernel: [    0.828780] pci 0000:00:1c.0: setting latency timer to 64
Dec 24 10:27:54 laptop kernel: [    0.828788] pci 0000:00:1c.1: PCI INT B -> GSI 16 (level, low) -> IRQ 16
Dec 24 10:27:54 laptop kernel: [    0.828868] pci 0000:00:1c.1: setting latency timer to 64
Dec 24 10:27:54 laptop kernel: [    0.828876] pci 0000:00:1c.4: PCI INT A -> GSI 17 (level, low) -> IRQ 17
Dec 24 10:27:54 laptop kernel: [    0.828955] pci 0000:00:1c.4: setting latency timer to 64
Dec 24 10:27:54 laptop kernel: [    0.828964] pci 0000:00:1c.7: PCI INT B -> GSI 16 (level, low) -> IRQ 16
Dec 24 10:27:54 laptop kernel: [    0.829040] pci 0000:00:1c.7: setting latency timer to 64
Dec 24 10:27:54 laptop kernel: [    0.829049] pci 0000:00:1e.0: setting latency timer to 64
Dec 24 10:27:54 laptop kernel: [    0.829054] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
Dec 24 10:27:54 laptop kernel: [    0.829056] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff]
Dec 24 10:27:54 laptop kernel: [    0.829059] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
Dec 24 10:27:54 laptop kernel: [    0.829061] pci_bus 0000:00: resource 7 [mem 0xc0000000-0xfeafffff]
Dec 24 10:27:54 laptop kernel: [    0.829063] pci_bus 0000:01: resource 0 [io  0x6000-0x6fff]
Dec 24 10:27:54 laptop kernel: [    0.829066] pci_bus 0000:01: resource 1 [mem 0xd2000000-0xd30fffff]
Dec 24 10:27:54 laptop kernel: [    0.829068] pci_bus 0000:01: resource 2 [mem 0xc0000000-0xd1ffffff 64bit pref]
Dec 24 10:27:54 laptop kernel: [    0.829071] pci_bus 0000:02: resource 0 [io  0x5000-0x5fff]
Dec 24 10:27:54 laptop kernel: [    0.829073] pci_bus 0000:02: resource 1 [mem 0xda100000-0xdb0fffff]
Dec 24 10:27:54 laptop kernel: [    0.829075] pci_bus 0000:02: resource 2 [mem 0xd3100000-0xd40fffff 64bit pref]
Dec 24 10:27:54 laptop kernel: [    0.829078] pci_bus 0000:03: resource 0 [io  0x4000-0x4fff]
Dec 24 10:27:54 laptop kernel: [    0.829080] pci_bus 0000:03: resource 1 [mem 0xd9100000-0xda0fffff]
Dec 24 10:27:54 laptop kernel: [    0.829082] pci_bus 0000:03: resource 2 [mem 0xd4100000-0xd50fffff 64bit pref]
Dec 24 10:27:54 laptop kernel: [    0.829085] pci_bus 0000:04: resource 0 [io  0x3000-0x3fff]
Dec 24 10:27:54 laptop kernel: [    0.829087] pci_bus 0000:04: resource 1 [mem 0xd8100000-0xd90fffff]
Dec 24 10:27:54 laptop kernel: [    0.829090] pci_bus 0000:04: resource 2 [mem 0xd5100000-0xd60fffff 64bit pref]
Dec 24 10:27:54 laptop kernel: [    0.829092] pci_bus 0000:05: resource 0 [io  0x2000-0x2fff]
Dec 24 10:27:54 laptop kernel: [    0.829094] pci_bus 0000:05: resource 1 [mem 0xd7100000-0xd80fffff]
Dec 24 10:27:54 laptop kernel: [    0.829097] pci_bus 0000:05: resource 2 [mem 0xd6100000-0xd70fffff 64bit pref]
Dec 24 10:27:54 laptop kernel: [    0.829099] pci_bus 0000:09: resource 4 [io  0x0000-0x0cf7]
Dec 24 10:27:54 laptop kernel: [    0.829101] pci_bus 0000:09: resource 5 [io  0x0d00-0xffff]
Dec 24 10:27:54 laptop kernel: [    0.829104] pci_bus 0000:09: resource 6 [mem 0x000a0000-0x000bffff]
Dec 24 10:27:54 laptop kernel: [    0.829106] pci_bus 0000:09: resource 7 [mem 0xc0000000-0xfeafffff]
Dec 24 10:27:54 laptop kernel: [    0.829150] NET: Registered protocol family 2
Dec 24 10:27:54 laptop kernel: [    0.829282] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
Dec 24 10:27:54 laptop kernel: [    0.829551] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
Dec 24 10:27:54 laptop kernel: [    0.830330] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
Dec 24 10:27:54 laptop kernel: [    0.830750] TCP: Hash tables configured (established 131072 bind 65536)
Dec 24 10:27:54 laptop kernel: [    0.830826] TCP reno registered
Dec 24 10:27:54 laptop kernel: [    0.830894] UDP hash table entries: 512 (order: 2, 16384 bytes)
Dec 24 10:27:54 laptop kernel: [    0.830977] UDP-Lite hash table entries: 512 (order: 2, 16384 bytes)
Dec 24 10:27:54 laptop kernel: [    0.831147] NET: Registered protocol family 1
Dec 24 10:27:54 laptop kernel: [    0.845751] Freeing initrd memory: 13328k freed
Dec 24 10:27:54 laptop kernel: [    0.859798] pci 0000:01:00.0: Boot video device
Dec 24 10:27:54 laptop kernel: [    0.859852] PCI: CLS 64 bytes, default 64
Dec 24 10:27:54 laptop kernel: [    0.859860] Simple Boot Flag at 0x44 set to 0x1
Dec 24 10:27:54 laptop kernel: [    0.860427] audit: initializing netlink socket (disabled)
Dec 24 10:27:54 laptop kernel: [    0.860513] type=2000 audit(1324718794.676:1): initialized
Dec 24 10:27:54 laptop kernel: [    0.888602] highmem bounce pool size: 64 pages
Dec 24 10:27:54 laptop kernel: [    0.888682] HugeTLB registered 2 MB page size, pre-allocated 0 pages
Dec 24 10:27:54 laptop kernel: [    0.899748] VFS: Disk quotas dquot_6.5.2
Dec 24 10:27:54 laptop kernel: [    0.899893] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
Dec 24 10:27:54 laptop kernel: [    0.900657] fuse init (API version 7.16)
Dec 24 10:27:54 laptop kernel: [    0.900821] msgmni has been set to 1642
Dec 24 10:27:54 laptop kernel: [    0.901323] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
Dec 24 10:27:54 laptop kernel: [    0.901447] io scheduler noop registered
Dec 24 10:27:54 laptop kernel: [    0.901520] io scheduler deadline registered
Dec 24 10:27:54 laptop kernel: [    0.901605] io scheduler cfq registered (default)
Dec 24 10:27:54 laptop kernel: [    0.901805] pcieport 0000:00:01.0: setting latency timer to 64
Dec 24 10:27:54 laptop kernel: [    0.901837] pcieport 0000:00:01.0: irq 40 for MSI/MSI-X
Dec 24 10:27:54 laptop kernel: [    0.902118] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Dec 24 10:27:54 laptop kernel: [    0.902214] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
Dec 24 10:27:54 laptop kernel: [    0.902344] intel_idle: MWAIT substates: 0x1120
Dec 24 10:27:54 laptop kernel: [    0.902345] intel_idle: v0.4 model 0x25
Dec 24 10:27:54 laptop kernel: [    0.902347] intel_idle: lapic_timer_reliable_states 0xffffffff
Dec 24 10:27:54 laptop kernel: [    0.902725] ACPI: Deprecated procfs I/F for AC is loaded, please retry with CONFIG_ACPI_PROCFS_POWER cleared
Dec 24 10:27:54 laptop kernel: [    0.903172] ACPI: AC Adapter [ACAD] (on-line)
Dec 24 10:27:54 laptop kernel: [    0.903341] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0
Dec 24 10:27:54 laptop kernel: [    0.905245] ACPI: Power Button [PWRB]
Dec 24 10:27:54 laptop kernel: [    0.905369] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input1
Dec 24 10:27:54 laptop kernel: [    0.905845] ACPI: Lid Switch [LID0]
Dec 24 10:27:54 laptop kernel: [    0.905957] input: Sleep Button as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input2
Dec 24 10:27:54 laptop kernel: [    0.906053] ACPI: Sleep Button [SLPB]
Dec 24 10:27:54 laptop kernel: [    0.906170] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input3
Dec 24 10:27:54 laptop kernel: [    0.906264] ACPI: Power Button [PWRF]
Dec 24 10:27:54 laptop kernel: [    0.906359] ACPI: acpi_idle yielding to intel_idle
Dec 24 10:27:54 laptop kernel: [    0.909215] [Firmware Bug]: Invalid critical threshold (0)
Dec 24 10:27:54 laptop kernel: [    0.910990] thermal LNXTHERM:00: registered as thermal_zone0
Dec 24 10:27:54 laptop kernel: [    0.911067] ACPI: Thermal Zone [TZ01] (34 C)
Dec 24 10:27:54 laptop kernel: [    0.911154] ACPI: Deprecated procfs I/F for battery is loaded, please retry with CONFIG_ACPI_PROCFS_POWER cleared
Dec 24 10:27:54 laptop kernel: [    0.911278] ERST: Table is not found!
Dec 24 10:27:54 laptop kernel: [    0.911420] isapnp: Scanning for PnP cards...
Dec 24 10:27:54 laptop kernel: [    0.911442] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
Dec 24 10:27:54 laptop kernel: [    0.928081] ACPI: Battery Slot [BAT0] (battery present)
Dec 24 10:27:54 laptop kernel: [    1.265828] isapnp: No Plug & Play device found
Dec 24 10:27:54 laptop kernel: [    1.319921] Linux agpgart interface v0.103
Dec 24 10:27:54 laptop kernel: [    1.321261] brd: module loaded
Dec 24 10:27:54 laptop kernel: [    1.321887] loop: module loaded
Dec 24 10:27:54 laptop kernel: [    1.322391] Fixed MDIO Bus: probed
Dec 24 10:27:54 laptop kernel: [    1.322482] PPP generic driver version 2.4.2
Dec 24 10:27:54 laptop kernel: [    1.322587] tun: Universal TUN/TAP device driver, 1.6
Dec 24 10:27:54 laptop kernel: [    1.322661] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
Dec 24 10:27:54 laptop kernel: [    1.322812] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
Dec 24 10:27:54 laptop kernel: [    1.322907] ehci_hcd 0000:00:1a.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Dec 24 10:27:54 laptop kernel: [    1.322998] ehci_hcd 0000:00:1a.0: setting latency timer to 64
Dec 24 10:27:54 laptop kernel: [    1.323003] ehci_hcd 0000:00:1a.0: EHCI Host Controller
Dec 24 10:27:54 laptop kernel: [    1.323108] ehci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 1
Dec 24 10:27:54 laptop kernel: [    1.323233] ehci_hcd 0000:00:1a.0: debug port 2
Dec 24 10:27:54 laptop kernel: [    1.327209] ehci_hcd 0000:00:1a.0: cache line size of 64 is not supported
Dec 24 10:27:54 laptop kernel: [    1.327228] ehci_hcd 0000:00:1a.0: irq 16, io mem 0xdb105c00
Dec 24 10:27:54 laptop kernel: [    1.339522] ehci_hcd 0000:00:1a.0: USB 2.0 started, EHCI 1.00
Dec 24 10:27:54 laptop kernel: [    1.339735] hub 1-0:1.0: USB hub found
Dec 24 10:27:54 laptop kernel: [    1.339809] hub 1-0:1.0: 3 ports detected
Dec 24 10:27:54 laptop kernel: [    1.339949] ehci_hcd 0000:00:1d.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
Dec 24 10:27:54 laptop kernel: [    1.340039] ehci_hcd 0000:00:1d.0: setting latency timer to 64
Dec 24 10:27:54 laptop kernel: [    1.340043] ehci_hcd 0000:00:1d.0: EHCI Host Controller
Dec 24 10:27:54 laptop kernel: [    1.340155] ehci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
Dec 24 10:27:54 laptop kernel: [    1.340274] ehci_hcd 0000:00:1d.0: debug port 2
Dec 24 10:27:54 laptop kernel: [    1.344255] ehci_hcd 0000:00:1d.0: cache line size of 64 is not supported
Dec 24 10:27:54 laptop kernel: [    1.344271] ehci_hcd 0000:00:1d.0: irq 21, io mem 0xdb105800
Dec 24 10:27:54 laptop kernel: [    1.359515] ehci_hcd 0000:00:1d.0: USB 2.0 started, EHCI 1.00
Dec 24 10:27:54 laptop kernel: [    1.359701] hub 2-0:1.0: USB hub found
Dec 24 10:27:54 laptop kernel: [    1.359775] hub 2-0:1.0: 3 ports detected
Dec 24 10:27:54 laptop kernel: [    1.359907] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
Dec 24 10:27:54 laptop kernel: [    1.359992] uhci_hcd: USB Universal Host Controller Interface driver
Dec 24 10:27:54 laptop kernel: [    1.360137] i8042: PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
Dec 24 10:27:54 laptop kernel: [    1.383218] serio: i8042 KBD port at 0x60,0x64 irq 1
Dec 24 10:27:54 laptop kernel: [    1.383296] serio: i8042 AUX port at 0x60,0x64 irq 12
Dec 24 10:27:54 laptop kernel: [    1.383463] mousedev: PS/2 mouse device common for all mice
Dec 24 10:27:54 laptop kernel: [    1.384696] rtc_cmos 00:07: RTC can wake from S4
Dec 24 10:27:54 laptop kernel: [    1.384867] rtc_cmos 00:07: rtc core: registered rtc_cmos as rtc0
Dec 24 10:27:54 laptop kernel: [    1.384972] rtc0: alarms up to one year, y3k, 242 bytes nvram, hpet irqs
Dec 24 10:27:54 laptop kernel: [    1.385120] device-mapper: uevent: version 1.0.3
Dec 24 10:27:54 laptop kernel: [    1.385263] device-mapper: ioctl: 4.20.0-ioctl (2011-02-02) initialised: dm-devel@redhat.com
Dec 24 10:27:54 laptop kernel: [    1.385383] EISA: Probing bus 0 at eisa.0
Dec 24 10:27:54 laptop kernel: [    1.385456] EISA: Cannot allocate resource for mainboard
Dec 24 10:27:54 laptop kernel: [    1.385530] Cannot allocate resource for EISA slot 1
Dec 24 10:27:54 laptop kernel: [    1.385604] Cannot allocate resource for EISA slot 2
Dec 24 10:27:54 laptop kernel: [    1.385677] Cannot allocate resource for EISA slot 3
Dec 24 10:27:54 laptop kernel: [    1.385750] Cannot allocate resource for EISA slot 4
Dec 24 10:27:54 laptop kernel: [    1.385824] Cannot allocate resource for EISA slot 5
Dec 24 10:27:54 laptop kernel: [    1.385898] Cannot allocate resource for EISA slot 6
Dec 24 10:27:54 laptop kernel: [    1.385972] Cannot allocate resource for EISA slot 7
Dec 24 10:27:54 laptop kernel: [    1.386045] Cannot allocate resource for EISA slot 8
Dec 24 10:27:54 laptop kernel: [    1.386119] EISA: Detected 0 cards.
Dec 24 10:27:54 laptop kernel: [    1.386196] cpufreq-nforce2: No nForce2 chipset.
Dec 24 10:27:54 laptop kernel: [    1.386366] cpuidle: using governor ladder
Dec 24 10:27:54 laptop kernel: [    1.386597] cpuidle: using governor menu
Dec 24 10:27:54 laptop kernel: [    1.386669] EFI Variables Facility v0.08 2004-May-17
Dec 24 10:27:54 laptop kernel: [    1.386978] TCP cubic registered
Dec 24 10:27:54 laptop kernel: [    1.387179] NET: Registered protocol family 10
Dec 24 10:27:54 laptop kernel: [    1.387774] NET: Registered protocol family 17
Dec 24 10:27:54 laptop kernel: [    1.387859] Registering the dns_resolver key type
Dec 24 10:27:54 laptop kernel: [    1.387947] Using IPI No-Shortcut mode
Dec 24 10:27:54 laptop kernel: [    1.388085] PM: Hibernation image not present or could not be loaded.
Dec 24 10:27:54 laptop kernel: [    1.388095] registered taskstats version 1
Dec 24 10:27:54 laptop kernel: [    1.407789]   Magic number: 7:169:425
Dec 24 10:27:54 laptop kernel: [    1.408041] rtc_cmos 00:07: setting system clock to 2011-12-24 09:26:35 UTC (1324718795)
Dec 24 10:27:54 laptop kernel: [    1.408700] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input4
Dec 24 10:27:54 laptop kernel: [    1.409548] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
Dec 24 10:27:54 laptop kernel: [    1.409631] EDD information not available.
Dec 24 10:27:54 laptop kernel: [    1.410326] Freeing unused kernel memory: 720k freed
Dec 24 10:27:54 laptop kernel: [    1.410633] Write protecting the kernel text: 5500k
Dec 24 10:27:54 laptop kernel: [    1.410784] Write protecting the kernel read-only data: 2240k
Dec 24 10:27:54 laptop kernel: [    1.410861] NX-protecting the kernel data: 4740k
Dec 24 10:27:54 laptop kernel: [    1.476257] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
Dec 24 10:27:54 laptop kernel: [    1.476362] r8169 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
Dec 24 10:27:54 laptop kernel: [    1.476488] r8169 0000:03:00.0: setting latency timer to 64
Dec 24 10:27:54 laptop kernel: [    1.476556] r8169 0000:03:00.0: irq 41 for MSI/MSI-X
Dec 24 10:27:54 laptop kernel: [    1.477215] r8169 0000:03:00.0: eth0: RTL8168d/8111d at 0xf843c000, 00:26:9e:e9:6a:94, XID 083000c0 IRQ 41
Dec 24 10:27:54 laptop kernel: [    1.478750] firewire_ohci 0000:04:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Dec 24 10:27:54 laptop kernel: [    1.478853] firewire_ohci 0000:04:00.0: setting latency timer to 64
Dec 24 10:27:54 laptop kernel: [    1.479528] sdhci: Secure Digital Host Controller Interface driver
Dec 24 10:27:54 laptop kernel: [    1.479606] sdhci: Copyright(c) Pierre Ossman
Dec 24 10:27:54 laptop kernel: [    1.485149] ahci 0000:00:1f.2: version 3.0
Dec 24 10:27:54 laptop kernel: [    1.485178] ahci 0000:00:1f.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
Dec 24 10:27:54 laptop kernel: [    1.485324] ahci 0000:00:1f.2: irq 42 for MSI/MSI-X
Dec 24 10:27:54 laptop kernel: [    1.485430] ahci 0000:00:1f.2: AHCI 0001.0300 32 slots 6 ports 3 Gbps 0x33 impl SATA mode
Dec 24 10:27:54 laptop kernel: [    1.485526] ahci 0000:00:1f.2: flags: 64bit ncq sntf ilck pm led clo pio slum part ems sxs apst 
Dec 24 10:27:54 laptop kernel: [    1.485625] ahci 0000:00:1f.2: setting latency timer to 64
Dec 24 10:27:54 laptop kernel: [    1.508403] scsi0 : ahci
Dec 24 10:27:54 laptop kernel: [    1.508700] scsi1 : ahci
Dec 24 10:27:54 laptop kernel: [    1.508941] scsi2 : ahci
Dec 24 10:27:54 laptop kernel: [    1.509195] scsi3 : ahci
Dec 24 10:27:54 laptop kernel: [    1.509359] scsi4 : ahci
Dec 24 10:27:54 laptop kernel: [    1.509525] scsi5 : ahci
Dec 24 10:27:54 laptop kernel: [    1.509659] ata1: SATA max UDMA/133 abar m2048@0xdb105000 port 0xdb105100 irq 42
Dec 24 10:27:54 laptop kernel: [    1.509755] ata2: SATA max UDMA/133 abar m2048@0xdb105000 port 0xdb105180 irq 42
Dec 24 10:27:54 laptop kernel: [    1.509847] ata3: DUMMY
Dec 24 10:27:54 laptop kernel: [    1.509914] ata4: DUMMY
Dec 24 10:27:54 laptop kernel: [    1.509983] ata5: SATA max UDMA/133 abar m2048@0xdb105000 port 0xdb105300 irq 42
Dec 24 10:27:54 laptop kernel: [    1.510078] ata6: SATA max UDMA/133 abar m2048@0xdb105000 port 0xdb105380 irq 42
Dec 24 10:27:54 laptop kernel: [    1.539617] firewire_ohci: Added fw-ohci device 0000:04:00.0, OHCI v1.10, 4 IR + 0 IT contexts, quirks 0x10
Dec 24 10:27:54 laptop kernel: [    1.539793] sdhci-pci 0000:04:00.1: SDHCI controller found [197b:2382] (rev 0)
Dec 24 10:27:54 laptop kernel: [    1.539958] sdhci-pci 0000:04:00.1: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Dec 24 10:27:54 laptop kernel: [    1.540150] sdhci-pci 0000:04:00.1: setting latency timer to 64
Dec 24 10:27:54 laptop kernel: [    1.540163] mmc0: no vmmc regulator found
Dec 24 10:27:54 laptop kernel: [    1.540266] Registered led device: mmc0::
Dec 24 10:27:54 laptop kernel: [    1.540314] mmc0: SDHCI controller on PCI [0000:04:00.1] using DMA
Dec 24 10:27:54 laptop kernel: [    1.540419] sdhci-pci 0000:04:00.2: SDHCI controller found [197b:2381] (rev 0)
Dec 24 10:27:54 laptop kernel: [    1.540524] sdhci-pci 0000:04:00.2: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Dec 24 10:27:54 laptop kernel: [    1.540619] sdhci-pci 0000:04:00.2: Refusing to bind to secondary interface.
Dec 24 10:27:54 laptop kernel: [    1.540702] sdhci-pci 0000:04:00.2: PCI INT A disabled
Dec 24 10:27:54 laptop kernel: [    1.651530] usb 1-1: new high speed USB device number 2 using ehci_hcd
Dec 24 10:27:54 laptop kernel: [    1.784313] hub 1-1:1.0: USB hub found
Dec 24 10:27:54 laptop kernel: [    1.784575] hub 1-1:1.0: 6 ports detected
Dec 24 10:27:54 laptop kernel: [    1.827416] ata6: SATA link down (SStatus 0 SControl 300)
Dec 24 10:27:54 laptop kernel: [    1.827530] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
Dec 24 10:27:54 laptop kernel: [    1.827636] ata5: SATA link down (SStatus 0 SControl 300)
Dec 24 10:27:54 laptop kernel: [    1.827784] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
Dec 24 10:27:54 laptop kernel: [    1.828510] ata1.00: ATA-8: Hitachi HTS725050A9A364, PC4OC70E, max UDMA/100
Dec 24 10:27:54 laptop kernel: [    1.828589] ata1.00: 976773168 sectors, multi 16: LBA48 NCQ (depth 31/32), AA
Dec 24 10:27:54 laptop kernel: [    1.829812] ata1.00: configured for UDMA/100
Dec 24 10:27:54 laptop kernel: [    1.830157] scsi 0:0:0:0: Direct-Access     ATA      Hitachi HTS72505 PC4O PQ: 0 ANSI: 5
Dec 24 10:27:54 laptop kernel: [    1.830384] sd 0:0:0:0: [sda] 976773168 512-byte logical blocks: (500 GB/465 GiB)
Dec 24 10:27:54 laptop kernel: [    1.830415] sd 0:0:0:0: Attached scsi generic sg0 type 0
Dec 24 10:27:54 laptop kernel: [    1.830598] sd 0:0:0:0: [sda] Write Protect is off
Dec 24 10:27:54 laptop kernel: [    1.830667] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
Dec 24 10:27:54 laptop kernel: [    1.830684] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Dec 24 10:27:54 laptop kernel: [    1.842237] ata2.00: ATAPI: hp      DVD RW AD-7561S, AH73, max UDMA/100
Dec 24 10:27:54 laptop kernel: [    1.858940] ata2.00: configured for UDMA/100
Dec 24 10:27:54 laptop kernel: [    1.863382] Refined TSC clocksource calibration: 2127.999 MHz.
Dec 24 10:27:54 laptop kernel: [    1.863476] Switching to clocksource tsc
Dec 24 10:27:54 laptop kernel: [    1.866700] scsi 1:0:0:0: CD-ROM            hp       DVD RW AD-7561S  AH73 PQ: 0 ANSI: 5
Dec 24 10:27:54 laptop kernel: [    1.874068] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
Dec 24 10:27:54 laptop kernel: [    1.874178] cdrom: Uniform CD-ROM driver Revision: 3.20
Dec 24 10:27:54 laptop kernel: [    1.874339] sr 1:0:0:0: Attached scsi CD-ROM sr0
Dec 24 10:27:54 laptop kernel: [    1.874387] sr 1:0:0:0: Attached scsi generic sg1 type 5
Dec 24 10:27:54 laptop kernel: [    1.889263]  sda: sda1 sda2 < sda5 sda6 sda7 >
Dec 24 10:27:54 laptop kernel: [    1.889756] sd 0:0:0:0: [sda] Attached SCSI disk
Dec 24 10:27:54 laptop kernel: [    1.895333] usb 2-1: new high speed USB device number 2 using ehci_hcd
Dec 24 10:27:54 laptop kernel: [    2.028019] hub 2-1:1.0: USB hub found
Dec 24 10:27:54 laptop kernel: [    2.028217] hub 2-1:1.0: 8 ports detected
Dec 24 10:27:54 laptop kernel: [    2.039330] firewire_core: created device fw0: GUID 00241b00ce59bc01, S400
Dec 24 10:27:54 laptop kernel: [    2.103495] usb 1-1.4: new high speed USB device number 3 using ehci_hcd
Dec 24 10:27:54 laptop kernel: [    2.181524] EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: (null)
Dec 24 10:27:54 laptop kernel: [    2.299398] usb 2-1.3: new full speed USB device number 3 using ehci_hcd
Dec 24 10:27:54 laptop kernel: [    2.463182] usb 2-1.5: new high speed USB device number 4 using ehci_hcd
Dec 24 10:27:54 laptop kernel: [    7.565037] usb 2-1.5: device descriptor read/all, error -110
Dec 24 10:27:54 laptop kernel: [    7.637146] usb 2-1.5: new high speed USB device number 5 using ehci_hcd
Dec 24 10:27:54 laptop kernel: [   12.738835] usb 2-1.5: device descriptor read/all, error -110
Dec 24 10:27:54 laptop kernel: [   12.810963] usb 2-1.5: new high speed USB device number 6 using ehci_hcd
Dec 24 10:27:54 laptop kernel: [   75.811056] Adding 10971132k swap on /dev/sda5.  Priority:-1 extents:1 across:10971132k 
Dec 24 10:27:54 laptop kernel: [   75.826305] lp: driver loaded but no devices found
Dec 24 10:27:54 laptop kernel: [   75.873055] hp_accel: hardware type DV7 found
Dec 24 10:27:54 laptop kernel: [   75.873709] lis3lv02d: 8 bits sensor found
Dec 24 10:27:54 laptop kernel: [   75.874147] wmi: Mapper loaded
Dec 24 10:27:54 laptop kernel: [   75.905554] ene_ir: chip is 0x3926 - kbver = 0x00, rev = 0xd2
Dec 24 10:27:54 laptop kernel: [   75.905558] ene_ir: PLL freq = 1406
Dec 24 10:27:54 laptop kernel: [   75.905560] ene_ir: KB3926D or higher detected
Dec 24 10:27:54 laptop kernel: [   75.905577] ene_ir: Firmware regs: c0 04
Dec 24 10:27:54 laptop kernel: [   75.905578] ene_ir: Hardware features:
Dec 24 10:27:54 laptop kernel: [   75.905580] ene_ir: * Uses GPIO 40 for IR demodulated input
Dec 24 10:27:54 laptop kernel: [   75.912945] IR NEC protocol handler initialized
Dec 24 10:27:54 laptop kernel: [   75.920393] jmb38x_ms 0000:04:00.3: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Dec 24 10:27:54 laptop kernel: [   75.920405] jmb38x_ms 0000:04:00.3: setting latency timer to 64
Dec 24 10:27:54 laptop kernel: [   75.921001] IR RC5(x) protocol handler initialized
Dec 24 10:27:54 laptop kernel: [   75.923796] IR RC6 protocol handler initialized
Dec 24 10:27:54 laptop kernel: [   75.925868] IR JVC protocol handler initialized
Dec 24 10:27:54 laptop kernel: [   75.927613] IR Sony protocol handler initialized
Dec 24 10:27:54 laptop kernel: [   75.930205] lirc_dev: IR Remote Control driver registered, major 250 
Dec 24 10:27:54 laptop kernel: [   75.930498] IR LIRC bridge handler initialized
Dec 24 10:27:54 laptop kernel: [   75.932850] input: ST LIS3LV02DL Accelerometer as /devices/platform/lis3lv02d/input/input5
Dec 24 10:27:54 laptop kernel: [   75.933015] Registered led device: hp::hddprotect
Dec 24 10:27:54 laptop kernel: [   75.933041] hp_accel: driver loaded
Dec 24 10:27:54 laptop kernel: [   75.935516] type=1400 audit(1324718870.053:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=697 comm="apparmor_parser"
Dec 24 10:27:54 laptop kernel: [   75.936173] type=1400 audit(1324718870.057:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=697 comm="apparmor_parser"
Dec 24 10:27:54 laptop kernel: [   75.936490] Registered IR keymap rc-rc6-mce
Dec 24 10:27:54 laptop kernel: [   75.936599] type=1400 audit(1324718870.057:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=697 comm="apparmor_parser"
Dec 24 10:27:54 laptop kernel: [   75.936696] input: ENE eHome Infrared Remote Receiver as /devices/virtual/rc/rc0/input6
Dec 24 10:27:54 laptop kernel: [   75.936862] rc0: ENE eHome Infrared Remote Receiver as /devices/virtual/rc/rc0
Dec 24 10:27:54 laptop kernel: [   75.937385] cfg80211: Calling CRDA to update world regulatory domain
Dec 24 10:27:54 laptop kernel: [   75.939131] rc rc0: lirc_dev: driver ir-lirc-codec (ene_ir) registered at minor = 0
Dec 24 10:27:54 laptop kernel: [   75.939136] ene_ir: driver has been successfully loaded
Dec 24 10:27:54 laptop kernel: [   75.943804] acpi device:11: registered as cooling_device4
Dec 24 10:27:54 laptop kernel: [   75.943907] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:0e/LNXVIDEO:02/input/input7
Dec 24 10:27:54 laptop kernel: [   75.943995] ACPI: Video Device [VGA1] (multi-head: yes  rom: no  post: no)
Dec 24 10:27:54 laptop kernel: [   75.956359] brcmutil: module is from the staging directory, the quality is unknown, you have been warned.
Dec 24 10:27:54 laptop kernel: [   75.957446] brcmsmac: module is from the staging directory, the quality is unknown, you have been warned.
Dec 24 10:27:54 laptop kernel: [   75.966967] brcmsmac 0000:02:00.0: bus 2 slot 0 func 0 irq 5
Dec 24 10:27:54 laptop kernel: [   75.966986] brcmsmac 0000:02:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Dec 24 10:27:54 laptop kernel: [   75.966996] brcmsmac 0000:02:00.0: setting latency timer to 64
Dec 24 10:27:54 laptop kernel: [   75.987549] Linux video capture interface: v2.00
Dec 24 10:27:54 laptop kernel: [   75.993925] uvcvideo: Found UVC 1.00 device HP Webcam (5986:0143)
Dec 24 10:27:54 laptop kernel: [   75.998634] input: HP Webcam as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.5/2-1.5:1.0/input/input8
Dec 24 10:27:54 laptop kernel: [   75.998729] usbcore: registered new interface driver uvcvideo
Dec 24 10:27:54 laptop kernel: [   75.998733] USB Video Class driver (v1.1.0)
Dec 24 10:27:54 laptop kernel: [   76.023900] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
Dec 24 10:27:54 laptop kernel: [   76.024399] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
Dec 24 10:27:54 laptop kernel: [   76.024474] HDA Intel 0000:00:1b.0: irq 43 for MSI/MSI-X
Dec 24 10:27:54 laptop kernel: [   76.024509] HDA Intel 0000:00:1b.0: setting latency timer to 64
Dec 24 10:27:54 laptop kernel: [   76.024648] [drm] Initialized drm 1.1.0 20060810
Dec 24 10:27:54 laptop kernel: [   76.112165] input: HDA Intel Mic at Ext Front Jack as /devices/pci0000:00/0000:00:1b.0/sound/card0/input9
Dec 24 10:27:54 laptop kernel: [   76.112278] input: HDA Intel Line Out at Ext Front Jack as /devices/pci0000:00/0000:00:1b.0/sound/card0/input10
Dec 24 10:27:54 laptop kernel: [   76.112565] HDA Intel 0000:01:00.1: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Dec 24 10:27:54 laptop kernel: [   76.112652] HDA Intel 0000:01:00.1: irq 44 for MSI/MSI-X
Dec 24 10:27:54 laptop kernel: [   76.112679] HDA Intel 0000:01:00.1: setting latency timer to 64
Dec 24 10:27:54 laptop kernel: [   76.117607] input: HP WMI hotkeys as /devices/virtual/input/input11
Dec 24 10:27:54 laptop kernel: [   76.132742] cfg80211: World regulatory domain updated:
Dec 24 10:27:54 laptop kernel: [   76.132747] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
Dec 24 10:27:54 laptop kernel: [   76.132751] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Dec 24 10:27:54 laptop kernel: [   76.132754] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Dec 24 10:27:54 laptop kernel: [   76.132758] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Dec 24 10:27:54 laptop kernel: [   76.132765] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Dec 24 10:27:54 laptop kernel: [   76.132768] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Dec 24 10:27:54 laptop kernel: [   76.168195] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
Dec 24 10:27:54 laptop kernel: [   76.168200] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
Dec 24 10:27:54 laptop kernel: [   76.168204] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
Dec 24 10:27:54 laptop kernel: [   76.168207] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
Dec 24 10:27:54 laptop kernel: [   76.168210] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
Dec 24 10:27:54 laptop kernel: [   76.168213] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
Dec 24 10:27:54 laptop kernel: [   76.168216] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
Dec 24 10:27:54 laptop kernel: [   76.168220] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
Dec 24 10:27:54 laptop kernel: [   76.168223] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
Dec 24 10:27:54 laptop kernel: [   76.168226] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
Dec 24 10:27:54 laptop kernel: [   76.168229] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
Dec 24 10:27:54 laptop kernel: [   76.168232] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
Dec 24 10:27:54 laptop kernel: [   76.168235] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
Dec 24 10:27:54 laptop kernel: [   76.168238] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
Dec 24 10:27:54 laptop kernel: [   76.168241] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
Dec 24 10:27:54 laptop kernel: [   76.168244] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
Dec 24 10:27:54 laptop kernel: [   76.168247] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
Dec 24 10:27:54 laptop kernel: [   76.168250] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
Dec 24 10:27:54 laptop kernel: [   76.168253] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
Dec 24 10:27:54 laptop kernel: [   76.168256] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
Dec 24 10:27:54 laptop kernel: [   76.168259] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
Dec 24 10:27:54 laptop kernel: [   76.168263] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
Dec 24 10:27:54 laptop kernel: [   76.168266] cfg80211: Updating information on frequency 2467 MHz for a 20 MHz width channel with regulatory rule:
Dec 24 10:27:54 laptop kernel: [   76.168269] cfg80211: 2457000 KHz - 2482000 KHz @  KHz), (300 mBi, 2000 mBm)
Dec 24 10:27:54 laptop kernel: [   76.168272] cfg80211: Updating information on frequency 2472 MHz for a 20 MHz width channel with regulatory rule:
Dec 24 10:27:54 laptop kernel: [   76.168275] cfg80211: 2457000 KHz - 2482000 KHz @  KHz), (300 mBi, 2000 mBm)
Dec 24 10:27:54 laptop kernel: [   76.168278] cfg80211: Updating information on frequency 2484 MHz for a 20 MHz width channel with regulatory rule:
Dec 24 10:27:54 laptop kernel: [   76.168281] cfg80211: 2474000 KHz - 2494000 KHz @  KHz), (300 mBi, 2000 mBm)
Dec 24 10:27:54 laptop kernel: [   76.170862] ieee80211 phy0: Selected rate control algorithm 'minstrel_ht'
Dec 24 10:27:54 laptop kernel: [   76.172157] lib80211: common routines for IEEE802.11 drivers
Dec 24 10:27:54 laptop kernel: [   76.172160] lib80211_crypt: registered algorithm 'NULL'
Dec 24 10:27:54 laptop kernel: [   76.174362] wl: module license 'MIXED/Proprietary' taints kernel.
Dec 24 10:27:54 laptop kernel: [   76.174367] Disabling lock debugging due to kernel taint
Dec 24 10:27:54 laptop kernel: [   76.176130] cfg80211: Calling CRDA for country: US
Dec 24 10:27:54 laptop kernel: [   76.180130] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
Dec 24 10:27:54 laptop kernel: [   76.180134] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2700 mBm)
Dec 24 10:27:54 laptop kernel: [   76.180137] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
Dec 24 10:27:54 laptop kernel: [   76.180140] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2700 mBm)
Dec 24 10:27:54 laptop kernel: [   76.180142] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
Dec 24 10:27:54 laptop kernel: [   76.180144] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2700 mBm)
Dec 24 10:27:54 laptop kernel: [   76.180146] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
Dec 24 10:27:54 laptop kernel: [   76.180149] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2700 mBm)
Dec 24 10:27:54 laptop kernel: [   76.180151] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
Dec 24 10:27:54 laptop kernel: [   76.180153] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2700 mBm)
Dec 24 10:27:54 laptop kernel: [   76.180155] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
Dec 24 10:27:54 laptop kernel: [   76.180158] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2700 mBm)
Dec 24 10:27:54 laptop kernel: [   76.180160] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
Dec 24 10:27:54 laptop kernel: [   76.180162] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2700 mBm)
Dec 24 10:27:54 laptop kernel: [   76.180164] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
Dec 24 10:27:54 laptop kernel: [   76.180167] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2700 mBm)
Dec 24 10:27:54 laptop kernel: [   76.180169] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
Dec 24 10:27:54 laptop kernel: [   76.180172] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2700 mBm)
Dec 24 10:27:54 laptop kernel: [   76.180174] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
Dec 24 10:27:54 laptop kernel: [   76.180176] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2700 mBm)
Dec 24 10:27:54 laptop kernel: [   76.180178] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
Dec 24 10:27:54 laptop kernel: [   76.180181] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2700 mBm)
Dec 24 10:27:54 laptop kernel: [   76.180183] cfg80211: Disabling freq 2467 MHz
Dec 24 10:27:54 laptop kernel: [   76.180184] cfg80211: Disabling freq 2472 MHz
Dec 24 10:27:54 laptop kernel: [   76.180186] cfg80211: Disabling freq 2484 MHz
Dec 24 10:27:54 laptop kernel: [   76.180188] cfg80211: Regulatory domain changed to country: US
Dec 24 10:27:54 laptop kernel: [   76.180190] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
Dec 24 10:27:54 laptop kernel: [   76.180193] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
Dec 24 10:27:54 laptop kernel: [   76.180195] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 1700 mBm)
Dec 24 10:27:54 laptop kernel: [   76.180197] cfg80211:     (5250000 KHz - 5330000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Dec 24 10:27:54 laptop kernel: [   76.180200] cfg80211:     (5490000 KHz - 5600000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Dec 24 10:27:54 laptop kernel: [   76.180202] cfg80211:     (5650000 KHz - 5710000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Dec 24 10:27:54 laptop kernel: [   76.180204] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 3000 mBm)
Dec 24 10:27:54 laptop kernel: [   76.399249] dvb-usb: found a 'AVerMedia A309' in cold state, will try to load a firmware
Dec 24 10:27:54 laptop kernel: [   76.401233] dvb-usb: did not find the firmware file. (dvb-usb-af9015.fw) Please see linux/Documentation/dvb/ for more details on firmware-problems. (-2)
Dec 24 10:27:54 laptop kernel: [   76.401321] dvb_usb_af9015: probe of 1-1.4:1.0 failed with error -2
Dec 24 10:27:54 laptop kernel: [   76.401376] usbcore: registered new interface driver dvb_usb_af9015
Dec 24 10:27:54 laptop kernel: [   76.952159] Synaptics Touchpad, model: 1, fw: 6.5, id: 0x1c0b1, caps: 0xa04751/0xa00000/0x0
Dec 24 10:27:54 laptop kernel: [   77.036119] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input12
Dec 24 10:27:54 laptop kernel: [   78.966285] EXT4-fs (sda6): mounted filesystem with ordered data mode. Opts: user_xattr
Dec 24 10:27:54 laptop kernel: [   79.170683] hda-intel: azx_get_response timeout, switching to polling mode: last cmd=0x300f0000
Dec 24 10:27:54 laptop kernel: [   79.835562] type=1400 audit(1324718873.957:5): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=1059 comm="apparmor_parser"
Dec 24 10:27:54 laptop kernel: [   79.835843] type=1400 audit(1324718873.957:6): apparmor="STATUS" operation="profile_load" name="/usr/lib/lightdm/lightdm-guest-session-wrapper" pid=1058 comm="apparmor_parser"
Dec 24 10:27:54 laptop kernel: [   79.836209] type=1400 audit(1324718873.957:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=1059 comm="apparmor_parser"
Dec 24 10:27:54 laptop kernel: [   79.836601] type=1400 audit(1324718873.957:8): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=1059 comm="apparmor_parser"
Dec 24 10:27:54 laptop kernel: [   79.837685] type=1400 audit(1324718873.957:9): apparmor="STATUS" operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" pid=1057 comm="apparmor_parser"
Dec 24 10:27:54 laptop kernel: [   79.839890] type=1400 audit(1324718873.961:10): apparmor="STATUS" operation="profile_load" name="/usr/lib/telepathy/mission-control-5" pid=1062 comm="apparmor_parser"
Dec 24 10:27:54 laptop kernel: [   79.840395] type=1400 audit(1324718873.961:11): apparmor="STATUS" operation="profile_load" name="/usr/sbin/mysqld" pid=1064 comm="apparmor_parser"
Dec 24 10:27:54 laptop kernel: [   79.922408] HDMI status: Pin=5 Presence_Detect=0 ELD_Valid=0
Dec 24 10:27:54 laptop kernel: [   79.954394] HDMI status: Pin=5 Presence_Detect=0 ELD_Valid=0
Dec 24 10:27:54 laptop kernel: [   79.978353] HDMI status: Pin=5 Presence_Detect=0 ELD_Valid=0
Dec 24 10:27:54 laptop kernel: [   80.010307] HDMI status: Pin=5 Presence_Detect=0 ELD_Valid=0
Dec 24 10:27:54 laptop kernel: [   80.026378] input: HDA NVidia HDMI/DP,pcm=9 as /devices/pci0000:00/0000:00:01.0/0000:01:00.1/sound/card1/input13
Dec 24 10:27:54 laptop kernel: [   80.026546] input: HDA NVidia HDMI/DP,pcm=8 as /devices/pci0000:00/0000:00:01.0/0000:01:00.1/sound/card1/input14
Dec 24 10:27:54 laptop kernel: [   80.026719] input: HDA NVidia HDMI/DP,pcm=7 as /devices/pci0000:00/0000:00:01.0/0000:01:00.1/sound/card1/input15
Dec 24 10:27:54 laptop kernel: [   80.026878] input: HDA NVidia HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:01.0/0000:01:00.1/sound/card1/input16
Dec 24 10:27:54 laptop kernel: [   80.045403] ieee80211 phy0: wl_ops_config: change monitor mode: false (implement)
Dec 24 10:27:54 laptop kernel: [   80.045476] ieee80211 phy0: wl_ops_config: change power-save mode: false (implement)
Dec 24 10:27:54 laptop kernel: [   80.057266] ieee80211 phy0: wl_ops_bss_info_changed: qos enabled: false (implement)
Dec 24 10:27:54 laptop kernel: [   80.057550] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Dec 24 10:27:54 laptop kernel: [   80.121915] r8169 0000:03:00.0: eth0: link down
Dec 24 10:27:54 laptop kernel: [   80.122235] ADDRCONF(NETDEV_UP): eth0: link is not ready
Dec 24 10:27:54 laptop kernel: [   80.171916] init: failsafe main process (1005) killed by TERM signal
Dec 24 10:27:54 laptop kernel: [   80.175673] init: apport pre-start process (1146) terminated with status 1
Dec 24 10:27:54 laptop kernel: [   80.187111] init: apport post-stop process (1185) terminated with status 1
Dec 24 10:27:54 laptop kernel: [   80.257582] ppdev: user-space parallel port driver
Dec 24 10:27:54 laptop kernel: [   80.282933] init: udev-fallback-graphics main process (1227) terminated with status 1
Dec 24 10:27:54 laptop kernel: [   80.289792] init: friendly-recovery post-stop process (431) terminated with status 1
Dec 24 10:27:54 laptop kernel: [   80.299040] init: gdm main process (1277) killed by TERM signal
Dec 24 10:27:56 laptop kernel: [   82.289189] wlan0: authenticate with 00:0c:42:23:3f:a0 (try 1)
Dec 24 10:27:56 laptop kernel: [   82.290797] wlan0: authenticated
Dec 24 10:27:56 laptop kernel: [   82.294589] wlan0: associate with 00:0c:42:23:3f:a0 (try 1)
Dec 24 10:27:56 laptop kernel: [   82.301928] wlan0: RX AssocResp from 00:0c:42:23:3f:a0 (capab=0x431 status=0 aid=2)
Dec 24 10:27:56 laptop kernel: [   82.301932] wlan0: associated
Dec 24 10:27:56 laptop kernel: [   82.303369] ieee80211 phy0: wl_ops_bss_info_changed: qos enabled: false (implement)
Dec 24 10:27:56 laptop kernel: [   82.303375] ieee80211 phy0: brcmsmac: wl_ops_bss_info_changed: associated
Dec 24 10:27:56 laptop kernel: [   82.303394] ieee80211 phy0: wl_ops_bss_info_changed: arp filtering: enabled true, count 0 (implement)
Dec 24 10:27:56 laptop kernel: [   82.303619] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
Dec 24 10:27:57 laptop kernel: [   82.987357] ieee80211 phy0: wl_ops_bss_info_changed: arp filtering: enabled true, count 1 (implement)
Dec 24 10:28:00 laptop kernel: [   86.057523] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,commit=0
Dec 24 10:28:00 laptop kernel: [   86.319540] EXT4-fs (sda6): re-mounted. Opts: user_xattr,commit=0
Dec 24 10:28:00 laptop kernel: [   86.482138] Bluetooth: Core ver 2.16
Dec 24 10:28:00 laptop kernel: [   86.482166] NET: Registered protocol family 31
Dec 24 10:28:00 laptop kernel: [   86.482168] Bluetooth: HCI device and connection manager initialized
Dec 24 10:28:00 laptop kernel: [   86.482172] Bluetooth: HCI socket layer initialized
Dec 24 10:28:00 laptop kernel: [   86.482174] Bluetooth: L2CAP socket layer initialized
Dec 24 10:28:00 laptop kernel: [   86.482215] Bluetooth: SCO socket layer initialized
Dec 24 10:28:00 laptop kernel: [   86.484789] Bluetooth: RFCOMM TTY layer initialized
Dec 24 10:28:00 laptop kernel: [   86.484794] Bluetooth: RFCOMM socket layer initialized
Dec 24 10:28:00 laptop kernel: [   86.484797] Bluetooth: RFCOMM ver 1.11
Dec 24 10:28:00 laptop kernel: [   86.486584] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
Dec 24 10:28:00 laptop kernel: [   86.486587] Bluetooth: BNEP filters: protocol multicast
Dec 24 10:28:00 laptop kernel: [   86.621404] /dev/vmmon[1755]: Module vmmon: registered with major=10 minor=165
Dec 24 10:28:00 laptop kernel: [   86.621431] /dev/vmmon[1755]: Initial HV check: anyNotCapable=0 anyUnlocked=0 anyEnabled=0 anyDisabled=1
Dec 24 10:28:00 laptop kernel: [   86.621439] /dev/vmmon[1755]: HV check: anyNotCapable=0 anyUnlocked=0 anyEnabled=0 anyDisabled=1
Dec 24 10:28:00 laptop kernel: [   86.621442] /dev/vmmon[1755]: Module vmmon: initialized
Dec 24 10:28:00 laptop kernel: [   86.628651] [1763]: VMCI: shared components initialized.
Dec 24 10:28:00 laptop kernel: [   86.628696] [1763]: VMCI: host components initialized.
Dec 24 10:28:00 laptop kernel: [   86.628785] [1763]: VMCI: Module registered (name=vmci,major=10,minor=56).
Dec 24 10:28:00 laptop kernel: [   86.628789] [1763]: VMCI: Using host personality
Dec 24 10:28:00 laptop kernel: [   86.628792] [1763]: VMCI: Module (name=vmci) is initialized
Dec 24 10:28:00 laptop kernel: [   86.856536] /dev/vmnet: open called by PID 1832 (vmnet-bridge)
Dec 24 10:28:00 laptop kernel: [   86.856549] /dev/vmnet: hub 0 does not exist, allocating memory.
Dec 24 10:28:00 laptop kernel: [   86.856579] /dev/vmnet: port on hub 0 successfully opened
Dec 24 10:28:00 laptop kernel: [   86.856593] bridge-wlan0: device is wireless, enabling SMAC
Dec 24 10:28:00 laptop kernel: [   86.856597] bridge-wlan0: up
Dec 24 10:28:00 laptop kernel: [   86.856601] bridge-wlan0: attached
Dec 24 10:28:02 laptop kernel: [   87.872673] /dev/vmnet: open called by PID 1839 (vmnet-netifup)
Dec 24 10:28:02 laptop kernel: [   87.872683] /dev/vmnet: hub 1 does not exist, allocating memory.
Dec 24 10:28:02 laptop kernel: [   87.872704] /dev/vmnet: port on hub 1 successfully opened
Dec 24 10:28:02 laptop kernel: [   87.947532] /dev/vmnet: open called by PID 1842 (vmnet-dhcpd)
Dec 24 10:28:02 laptop kernel: [   87.947547] /dev/vmnet: port on hub 1 successfully opened
Dec 24 10:28:02 laptop kernel: [   87.951686] /dev/vmnet: open called by PID 1848 (vmnet-natd)
Dec 24 10:28:02 laptop kernel: [   87.951694] /dev/vmnet: hub 8 does not exist, allocating memory.
Dec 24 10:28:02 laptop kernel: [   87.951715] /dev/vmnet: port on hub 8 successfully opened
Dec 24 10:28:02 laptop kernel: [   87.952961] userif-3: sent link down event.
Dec 24 10:28:02 laptop kernel: [   87.952964] userif-3: sent link up event.
Dec 24 10:28:02 laptop kernel: [   87.954411] /dev/vmnet: open called by PID 1849 (vmnet-netifup)
Dec 24 10:28:02 laptop kernel: [   87.954421] /dev/vmnet: port on hub 8 successfully opened
Dec 24 10:28:02 laptop kernel: [   88.006645] /dev/vmnet: open called by PID 1853 (vmnet-dhcpd)
Dec 24 10:28:02 laptop kernel: [   88.006660] /dev/vmnet: port on hub 8 successfully opened
Dec 24 10:28:02 laptop kernel: [   88.152904] init: plymouth-stop pre-start process (1924) terminated with status 1
Dec 24 10:28:07 laptop kernel: Kernel logging (proc) stopped.
Dec 24 10:28:39 laptop kernel: imklog 5.8.1, log source = /proc/kmsg started.
Dec 24 10:28:39 laptop kernel: [    0.000000] Initializing cgroup subsys cpuset
Dec 24 10:28:39 laptop kernel: [    0.000000] Initializing cgroup subsys cpu
Dec 24 10:28:39 laptop kernel: [    0.000000] Linux version 3.0.0-14-generic-pae (buildd@palmer) (gcc version 4.6.1 (Ubuntu/Linaro 4.6.1-9ubuntu3) ) #23-Ubuntu SMP Mon Nov 21 22:07:10 UTC 2011 (Ubuntu 3.0.0-14.23-generic-pae 3.0.9)
Dec 24 10:28:39 laptop kernel: [    0.000000] KERNEL supported cpus:
Dec 24 10:28:39 laptop kernel: [    0.000000]   Intel GenuineIntel
Dec 24 10:28:39 laptop kernel: [    0.000000]   AMD AuthenticAMD
Dec 24 10:28:39 laptop kernel: [    0.000000]   NSC Geode by NSC
Dec 24 10:28:39 laptop kernel: [    0.000000]   Cyrix CyrixInstead
Dec 24 10:28:39 laptop kernel: [    0.000000]   Centaur CentaurHauls
Dec 24 10:28:39 laptop kernel: [    0.000000]   Transmeta GenuineTMx86
Dec 24 10:28:39 laptop kernel: [    0.000000]   Transmeta TransmetaCPU
Dec 24 10:28:39 laptop kernel: [    0.000000]   UMC UMC UMC UMC
Dec 24 10:28:39 laptop kernel: [    0.000000] BIOS-provided physical RAM map:
Dec 24 10:28:39 laptop kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 000000000009d000 (usable)
Dec 24 10:28:39 laptop kernel: [    0.000000]  BIOS-e820: 000000000009d000 - 00000000000a0000 (reserved)
Dec 24 10:28:39 laptop kernel: [    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
Dec 24 10:28:39 laptop kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 00000000bf681000 (usable)
Dec 24 10:28:39 laptop kernel: [    0.000000]  BIOS-e820: 00000000bf681000 - 00000000bf6bf000 (reserved)
Dec 24 10:28:39 laptop kernel: [    0.000000]  BIOS-e820: 00000000bf6bf000 - 00000000bf75d000 (usable)
Dec 24 10:28:39 laptop kernel: [    0.000000]  BIOS-e820: 00000000bf75d000 - 00000000bf7bf000 (ACPI NVS)
Dec 24 10:28:39 laptop kernel: [    0.000000]  BIOS-e820: 00000000bf7bf000 - 00000000bf7e1000 (usable)
Dec 24 10:28:39 laptop kernel: [    0.000000]  BIOS-e820: 00000000bf7e1000 - 00000000bf7ff000 (ACPI data)
Dec 24 10:28:39 laptop kernel: [    0.000000]  BIOS-e820: 00000000bf7ff000 - 00000000bf800000 (usable)
Dec 24 10:28:39 laptop kernel: [    0.000000]  BIOS-e820: 00000000bf800000 - 00000000c0000000 (reserved)
Dec 24 10:28:39 laptop kernel: [    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
Dec 24 10:28:39 laptop kernel: [    0.000000]  BIOS-e820: 00000000feb00000 - 00000000feb04000 (reserved)
Dec 24 10:28:39 laptop kernel: [    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved)
Dec 24 10:28:39 laptop kernel: [    0.000000]  BIOS-e820: 00000000fed10000 - 00000000fed14000 (reserved)
Dec 24 10:28:39 laptop kernel: [    0.000000]  BIOS-e820: 00000000fed18000 - 00000000fed1a000 (reserved)
Dec 24 10:28:39 laptop kernel: [    0.000000]  BIOS-e820: 00000000fed1b000 - 00000000fed20000 (reserved)
Dec 24 10:28:39 laptop kernel: [    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
Dec 24 10:28:39 laptop kernel: [    0.000000]  BIOS-e820: 00000000ffe80000 - 0000000100000000 (reserved)
Dec 24 10:28:39 laptop kernel: [    0.000000]  BIOS-e820: 0000000100000000 - 000000013c000000 (usable)
Dec 24 10:28:39 laptop kernel: [    0.000000] NX (Execute Disable) protection: active
Dec 24 10:28:39 laptop kernel: [    0.000000] DMI 2.6 present.
Dec 24 10:28:39 laptop kernel: [    0.000000] DMI: Hewlett-Packard HP Pavilion dv7 Notebook PC/365C, BIOS F.15 01/05/2010
Dec 24 10:28:39 laptop kernel: [    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
Dec 24 10:28:39 laptop kernel: [    0.000000] e820 remove range: 00000000000a0000 - 0000000000100000 (usable)
Dec 24 10:28:39 laptop kernel: [    0.000000] last_pfn = 0x13c000 max_arch_pfn = 0x1000000
Dec 24 10:28:39 laptop kernel: [    0.000000] MTRR default type: uncachable
Dec 24 10:28:39 laptop kernel: [    0.000000] MTRR fixed ranges enabled:
Dec 24 10:28:39 laptop kernel: [    0.000000]   00000-9FFFF write-back
Dec 24 10:28:39 laptop kernel: [    0.000000]   A0000-BFFFF uncachable
Dec 24 10:28:39 laptop kernel: [    0.000000]   C0000-EFFFF write-through
Dec 24 10:28:39 laptop kernel: [    0.000000]   F0000-FFFFF write-combining
Dec 24 10:28:39 laptop kernel: [    0.000000] MTRR variable ranges enabled:
Dec 24 10:28:39 laptop kernel: [    0.000000]   0 base 000000000 mask F80000000 write-back
Dec 24 10:28:39 laptop kernel: [    0.000000]   1 base 0FFE00000 mask FFFE00000 write-protect
Dec 24 10:28:39 laptop kernel: [    0.000000]   2 base 080000000 mask FC0000000 write-back
Dec 24 10:28:39 laptop kernel: [    0.000000]   3 base 0BF800000 mask FFF800000 uncachable
Dec 24 10:28:39 laptop kernel: [    0.000000]   4 base 100000000 mask FC0000000 write-back
Dec 24 10:28:39 laptop kernel: [    0.000000]   5 disabled
Dec 24 10:28:39 laptop kernel: [    0.000000]   6 disabled
Dec 24 10:28:39 laptop kernel: [    0.000000]   7 disabled
Dec 24 10:28:39 laptop kernel: [    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
Dec 24 10:28:39 laptop kernel: [    0.000000] initial memory mapped : 0 - 02000000
Dec 24 10:28:39 laptop kernel: [    0.000000] Base memory trampoline at [c0099000] 99000 size 16384
Dec 24 10:28:39 laptop kernel: [    0.000000] init_memory_mapping: 0000000000000000-0000000037bfe000
Dec 24 10:28:39 laptop kernel: [    0.000000]  0000000000 - 0000200000 page 4k
Dec 24 10:28:39 laptop kernel: [    0.000000]  0000200000 - 0037a00000 page 2M
Dec 24 10:28:39 laptop kernel: [    0.000000]  0037a00000 - 0037bfe000 page 4k
Dec 24 10:28:39 laptop kernel: [    0.000000] kernel direct mapping tables up to 37bfe000 @ 1ffb000-2000000
Dec 24 10:28:39 laptop kernel: [    0.000000] RAMDISK: 365e8000 - 372ec000
Dec 24 10:28:39 laptop kernel: [    0.000000] ACPI: RSDP 000fe020 00024 (v02 HPQOEM)
Dec 24 10:28:39 laptop kernel: [    0.000000] ACPI: XSDT bf7fe120 00074 (v01 HPQOEM SLIC-MPC 00000001      01000013)
Dec 24 10:28:39 laptop kernel: [    0.000000] ACPI: FACP bf7fc000 000F4 (v04 HPQOEM SLIC-MPC 00000001 MSFT 01000013)
Dec 24 10:28:39 laptop kernel: [    0.000000] ACPI: DSDT bf7eb000 0DC73 (v02 HPQOEM SLIC-MPC 00000001 MSFT 01000013)
Dec 24 10:28:39 laptop kernel: [    0.000000] ACPI: FACS bf76f000 00040
Dec 24 10:28:39 laptop kernel: [    0.000000] ACPI: ASF! bf7fd000 000A5 (v32 HPQOEM SLIC-MPC 00000001 MSFT 01000013)
Dec 24 10:28:39 laptop kernel: [    0.000000] ACPI: HPET bf7fb000 00038 (v01 HPQOEM SLIC-MPC 00000001 MSFT 01000013)
Dec 24 10:28:39 laptop kernel: [    0.000000] ACPI: APIC bf7fa000 0008C (v02 HPQOEM SLIC-MPC 00000001 MSFT 01000013)
Dec 24 10:28:39 laptop kernel: [    0.000000] ACPI: MCFG bf7f9000 0003C (v01 HPQOEM SLIC-MPC 00000001 MSFT 01000013)
Dec 24 10:28:39 laptop kernel: [    0.000000] ACPI: SLIC bf7ea000 00176 (v01 HPQOEM SLIC-MPC 00000001 SLIC 000F4240)
Dec 24 10:28:39 laptop kernel: [    0.000000] ACPI: BOOT bf7e7000 00028 (v01 HPQOEM SLIC-MPC 00000001 MSFT 01000013)
Dec 24 10:28:39 laptop kernel: [    0.000000] ACPI: ASPT bf7e3000 00034 (v04 HPQOEM SLIC-MPC 00000001 MSFT 01000013)
Dec 24 10:28:39 laptop kernel: [    0.000000] ACPI: WDRT bf7e2000 00047 (v01 HPQOEM SLIC-MPC 00000000 MSFT 01000013)
Dec 24 10:28:39 laptop kernel: [    0.000000] ACPI: SSDT bf7e1000 009F1 (v01  PmRef    CpuPm 00003000 INTL 20060317)
Dec 24 10:28:39 laptop kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
Dec 24 10:28:39 laptop kernel: [    0.000000] 4164MB HIGHMEM available.
Dec 24 10:28:39 laptop kernel: [    0.000000] 891MB LOWMEM available.
Dec 24 10:28:39 laptop kernel: [    0.000000]   mapped low ram: 0 - 37bfe000
Dec 24 10:28:39 laptop kernel: [    0.000000]   low ram: 0 - 37bfe000
Dec 24 10:28:39 laptop kernel: [    0.000000] Zone PFN ranges:
Dec 24 10:28:39 laptop kernel: [    0.000000]   DMA      0x00000010 -> 0x00001000
Dec 24 10:28:39 laptop kernel: [    0.000000]   Normal   0x00001000 -> 0x00037bfe
Dec 24 10:28:39 laptop kernel: [    0.000000]   HighMem  0x00037bfe -> 0x0013c000
Dec 24 10:28:39 laptop kernel: [    0.000000] Movable zone start PFN for each node
Dec 24 10:28:39 laptop kernel: [    0.000000] early_node_map[6] active PFN ranges
Dec 24 10:28:39 laptop kernel: [    0.000000]     0: 0x00000010 -> 0x0000009d
Dec 24 10:28:39 laptop kernel: [    0.000000]     0: 0x00000100 -> 0x000bf681
Dec 24 10:28:39 laptop kernel: [    0.000000]     0: 0x000bf6bf -> 0x000bf75d
Dec 24 10:28:39 laptop kernel: [    0.000000]     0: 0x000bf7bf -> 0x000bf7e1
Dec 24 10:28:39 laptop kernel: [    0.000000]     0: 0x000bf7ff -> 0x000bf800
Dec 24 10:28:39 laptop kernel: [    0.000000]     0: 0x00100000 -> 0x0013c000
Dec 24 10:28:39 laptop kernel: [    0.000000] On node 0 totalpages: 1029839
Dec 24 10:28:39 laptop kernel: [    0.000000] free_area_init_node: node 0, pgdat c17ee1c0, node_mem_map f3e68200
Dec 24 10:28:39 laptop kernel: [    0.000000]   DMA zone: 32 pages used for memmap
Dec 24 10:28:39 laptop kernel: [    0.000000]   DMA zone: 0 pages reserved
Dec 24 10:28:39 laptop kernel: [    0.000000]   DMA zone: 3949 pages, LIFO batch:0
Dec 24 10:28:39 laptop kernel: [    0.000000]   Normal zone: 1752 pages used for memmap
Dec 24 10:28:39 laptop kernel: [    0.000000]   Normal zone: 222502 pages, LIFO batch:31
Dec 24 10:28:39 laptop kernel: [    0.000000]   HighMem zone: 8329 pages used for memmap
Dec 24 10:28:39 laptop kernel: [    0.000000]   HighMem zone: 793275 pages, LIFO batch:31
Dec 24 10:28:39 laptop kernel: [    0.000000] Using APIC driver default
Dec 24 10:28:39 laptop kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x408
Dec 24 10:28:39 laptop kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
Dec 24 10:28:39 laptop kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
Dec 24 10:28:39 laptop kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
Dec 24 10:28:39 laptop kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x04] enabled)
Dec 24 10:28:39 laptop kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x05] enabled)
Dec 24 10:28:39 laptop kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x05] lapic_id[0x00] disabled)
Dec 24 10:28:39 laptop kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x06] lapic_id[0x00] disabled)
Dec 24 10:28:39 laptop kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x07] lapic_id[0x00] disabled)
Dec 24 10:28:39 laptop kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x08] lapic_id[0x00] disabled)
Dec 24 10:28:39 laptop kernel: [    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
Dec 24 10:28:39 laptop kernel: [    0.000000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-23
Dec 24 10:28:39 laptop kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
Dec 24 10:28:39 laptop kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
Dec 24 10:28:39 laptop kernel: [    0.000000] ACPI: IRQ0 used by override.
Dec 24 10:28:39 laptop kernel: [    0.000000] ACPI: IRQ2 used by override.
Dec 24 10:28:39 laptop kernel: [    0.000000] ACPI: IRQ9 used by override.
Dec 24 10:28:39 laptop kernel: [    0.000000] Using ACPI (MADT) for SMP configuration information
Dec 24 10:28:39 laptop kernel: [    0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000
Dec 24 10:28:39 laptop kernel: [    0.000000] SMP: Allowing 8 CPUs, 4 hotplug CPUs
Dec 24 10:28:39 laptop kernel: [    0.000000] nr_irqs_gsi: 40
Dec 24 10:28:39 laptop kernel: [    0.000000] PM: Registered nosave memory: 000000000009d000 - 00000000000a0000
Dec 24 10:28:39 laptop kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
Dec 24 10:28:39 laptop kernel: [    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
Dec 24 10:28:39 laptop kernel: [    0.000000] Allocating PCI resources starting at c0000000 (gap: c0000000:20000000)
Dec 24 10:28:39 laptop kernel: [    0.000000] Booting paravirtualized kernel on bare hardware
Dec 24 10:28:39 laptop kernel: [    0.000000] setup_percpu: NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:8 nr_node_ids:1
Dec 24 10:28:39 laptop kernel: [    0.000000] PERCPU: Embedded 13 pages/cpu @f7800000 s29952 r0 d23296 u262144
Dec 24 10:28:39 laptop kernel: [    0.000000] pcpu-alloc: s29952 r0 d23296 u262144 alloc=1*2097152
Dec 24 10:28:39 laptop kernel: [    0.000000] pcpu-alloc: [0] 0 1 2 3 4 5 6 7 
Dec 24 10:28:39 laptop kernel: [    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 1019726
Dec 24 10:28:39 laptop kernel: [    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.0.0-14-generic-pae root=UUID=1293a0e3-f2ed-4d61-bd76-a855970c1fe4 ro quiet splash vt.handoff=7
Dec 24 10:28:39 laptop kernel: [    0.000000] PID hash table entries: 4096 (order: 2, 16384 bytes)
Dec 24 10:28:39 laptop kernel: [    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
Dec 24 10:28:39 laptop kernel: [    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
Dec 24 10:28:39 laptop kernel: [    0.000000] Initializing CPU#0
Dec 24 10:28:39 laptop kernel: [    0.000000] allocated 20709120 bytes of page_cgroup
Dec 24 10:28:39 laptop kernel: [    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
Dec 24 10:28:39 laptop kernel: [    0.000000] Initializing HighMem for node 0 (00037bfe:0013c000)
Dec 24 10:28:39 laptop kernel: [    0.000000] Memory: 4034212k/5177344k available (5499k kernel code, 85144k reserved, 2665k data, 720k init, 3206416k highmem)
Dec 24 10:28:39 laptop kernel: [    0.000000] virtual kernel memory layout:
Dec 24 10:28:39 laptop kernel: [    0.000000]     fixmap  : 0xfff16000 - 0xfffff000   ( 932 kB)
Dec 24 10:28:39 laptop kernel: [    0.000000]     pkmap   : 0xffc00000 - 0xffe00000   (2048 kB)
Dec 24 10:28:39 laptop kernel: [    0.000000]     vmalloc : 0xf83fe000 - 0xffbfe000   ( 120 MB)
Dec 24 10:28:39 laptop kernel: [    0.000000]     lowmem  : 0xc0000000 - 0xf7bfe000   ( 891 MB)
Dec 24 10:28:39 laptop kernel: [    0.000000]       .init : 0xc17fa000 - 0xc18ae000   ( 720 kB)
Dec 24 10:28:39 laptop kernel: [    0.000000]       .data : 0xc155efb0 - 0xc17f94c0   (2665 kB)
Dec 24 10:28:39 laptop kernel: [    0.000000]       .text : 0xc1000000 - 0xc155efb0   (5499 kB)
Dec 24 10:28:39 laptop kernel: [    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
Dec 24 10:28:39 laptop kernel: [    0.000000] SLUB: Genslabs=15, HWalign=64, Order=0-3, MinObjects=0, CPUs=8, Nodes=1
Dec 24 10:28:39 laptop kernel: [    0.000000] Hierarchical RCU implementation.
Dec 24 10:28:39 laptop kernel: [    0.000000] 	RCU dyntick-idle grace-period acceleration is enabled.
Dec 24 10:28:39 laptop kernel: [    0.000000] NR_IRQS:2304 nr_irqs:744 16
Dec 24 10:28:39 laptop kernel: [    0.000000] CPU 0 irqstacks, hard=f740a000 soft=f740c000
Dec 24 10:28:39 laptop kernel: [    0.000000] Extended CMOS year: 2000
Dec 24 10:28:39 laptop kernel: [    0.000000] vt handoff: transparent VT on vt#7
Dec 24 10:28:39 laptop kernel: [    0.000000] Console: colour dummy device 80x25
Dec 24 10:28:39 laptop kernel: [    0.000000] console [tty0] enabled
Dec 24 10:28:39 laptop kernel: [    0.000000] hpet clockevent registered
Dec 24 10:28:39 laptop kernel: [    0.000000] Fast TSC calibration using PIT
Dec 24 10:28:39 laptop kernel: [    0.004000] Detected 2127.727 MHz processor.
Dec 24 10:28:39 laptop kernel: [    0.000003] Calibrating delay loop (skipped), value calculated using timer frequency.. 4255.45 BogoMIPS (lpj=8510908)
Dec 24 10:28:39 laptop kernel: [    0.000007] pid_max: default: 32768 minimum: 301
Dec 24 10:28:39 laptop kernel: [    0.000029] Security Framework initialized
Dec 24 10:28:39 laptop kernel: [    0.000043] AppArmor: AppArmor initialized
Dec 24 10:28:39 laptop kernel: [    0.000045] Yama: becoming mindful.
Dec 24 10:28:39 laptop kernel: [    0.000099] Mount-cache hash table entries: 512
Dec 24 10:28:39 laptop kernel: [    0.000228] Initializing cgroup subsys cpuacct
Dec 24 10:28:39 laptop kernel: [    0.000235] Initializing cgroup subsys memory
Dec 24 10:28:39 laptop kernel: [    0.000243] Initializing cgroup subsys devices
Dec 24 10:28:39 laptop kernel: [    0.000245] Initializing cgroup subsys freezer
Dec 24 10:28:39 laptop kernel: [    0.000247] Initializing cgroup subsys net_cls
Dec 24 10:28:39 laptop kernel: [    0.000250] Initializing cgroup subsys blkio
Dec 24 10:28:39 laptop kernel: [    0.000255] Initializing cgroup subsys perf_event
Dec 24 10:28:39 laptop kernel: [    0.000285] CPU: Physical Processor ID: 0
Dec 24 10:28:39 laptop kernel: [    0.000287] CPU: Processor Core ID: 0
Dec 24 10:28:39 laptop kernel: [    0.000292] mce: CPU supports 9 MCE banks
Dec 24 10:28:39 laptop kernel: [    0.000304] CPU0: Thermal monitoring enabled (TM1)
Dec 24 10:28:39 laptop kernel: [    0.000312] using mwait in idle threads.
Dec 24 10:28:39 laptop kernel: [    0.002429] ACPI: Core revision 20110413
Dec 24 10:28:39 laptop kernel: [    0.037761] ftrace: allocating 25575 entries in 51 pages
Dec 24 10:28:39 laptop kernel: [    0.046284] Enabling APIC mode:  Flat.  Using 1 I/O APICs
Dec 24 10:28:39 laptop kernel: [    0.046688] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
Dec 24 10:28:39 laptop kernel: [    0.086351] CPU0: Intel(R) Core(TM) i3 CPU       M 330  @ 2.13GHz stepping 02
Dec 24 10:28:39 laptop kernel: [    0.191574] Performance Events: PEBS fmt1+, Westmere events, Intel PMU driver.
Dec 24 10:28:39 laptop kernel: [    0.191581] ... version:                3
Dec 24 10:28:39 laptop kernel: [    0.191582] ... bit width:              48
Dec 24 10:28:39 laptop kernel: [    0.191584] ... generic registers:      4
Dec 24 10:28:39 laptop kernel: [    0.191585] ... value mask:             0000ffffffffffff
Dec 24 10:28:39 laptop kernel: [    0.191587] ... max period:             000000007fffffff
Dec 24 10:28:39 laptop kernel: [    0.191588] ... fixed-purpose events:   3
Dec 24 10:28:39 laptop kernel: [    0.191590] ... event mask:             000000070000000f
Dec 24 10:28:39 laptop kernel: [    0.191968] CPU 1 irqstacks, hard=f74ce000 soft=f74d8000
Dec 24 10:28:39 laptop kernel: [    0.191971] Booting Node   0, Processors  #1
Dec 24 10:28:39 laptop kernel: [    0.191973] smpboot cpu 1: start_ip = 99000
Dec 24 10:28:39 laptop kernel: [    0.202194] Initializing CPU#1
Dec 24 10:28:39 laptop kernel: [    0.231555] calibrate_delay_direct() ignoring timer_rate as we had a TSC wrap around start=4278384060 >=post_end=440312
Dec 24 10:28:39 laptop kernel: [    0.299756] CPU 2 irqstacks, hard=f74e2000 soft=f74e4000
Dec 24 10:28:39 laptop kernel: [    0.299759]  #2
Dec 24 10:28:39 laptop kernel: [    0.299760] smpboot cpu 2: start_ip = 99000
Dec 24 10:28:39 laptop kernel: [    0.309908] Initializing CPU#2
Dec 24 10:28:39 laptop kernel: [    0.407638] CPU 3 irqstacks, hard=f750e000 soft=f7514000
Dec 24 10:28:39 laptop kernel: [    0.407641]  #3
Dec 24 10:28:39 laptop kernel: [    0.407642] smpboot cpu 3: start_ip = 99000
Dec 24 10:28:39 laptop kernel: [    0.417790] Initializing CPU#3
Dec 24 10:28:39 laptop kernel: [    0.515526] Brought up 4 CPUs
Dec 24 10:28:39 laptop kernel: [    0.515528] Total of 4 processors activated (17023.16 BogoMIPS).
Dec 24 10:28:39 laptop kernel: [    0.518008] devtmpfs: initialized
Dec 24 10:28:39 laptop kernel: [    0.518160] PM: Registering ACPI NVS region at bf75d000 (401408 bytes)
Dec 24 10:28:39 laptop kernel: [    0.520037] print_constraints: dummy: 
Dec 24 10:28:39 laptop kernel: [    0.520067] Time:  9:28:22  Date: 12/24/11
Dec 24 10:28:39 laptop kernel: [    0.520109] NET: Registered protocol family 16
Dec 24 10:28:39 laptop kernel: [    0.520216] Trying to unpack rootfs image as initramfs...
Dec 24 10:28:39 laptop kernel: [    0.520219] EISA bus registered
Dec 24 10:28:39 laptop kernel: [    0.520238] ACPI FADT declares the system doesn't support PCIe ASPM, so disable it
Dec 24 10:28:39 laptop kernel: [    0.520241] ACPI: bus type pci registered
Dec 24 10:28:39 laptop kernel: [    0.520314] PCI: MMCONFIG for domain 0000 [bus 00-ff] at [mem 0xe0000000-0xefffffff] (base 0xe0000000)
Dec 24 10:28:39 laptop kernel: [    0.520318] PCI: MMCONFIG at [mem 0xe0000000-0xefffffff] reserved in E820
Dec 24 10:28:39 laptop kernel: [    0.520320] PCI: Using MMCONFIG for extended config space
Dec 24 10:28:39 laptop kernel: [    0.520322] PCI: Using configuration type 1 for base access
Dec 24 10:28:39 laptop kernel: [    0.521210] bio: create slab <bio-0> at 0
Dec 24 10:28:39 laptop kernel: [    0.523826] ACPI: EC: Look up EC in DSDT
Dec 24 10:28:39 laptop kernel: [    0.526237] ACPI: Executed 1 blocks of module-level executable AML code
Dec 24 10:28:39 laptop kernel: [    0.559475] [Firmware Bug]: ACPI: BIOS _OSI(Linux) query ignored
Dec 24 10:28:39 laptop kernel: [    0.564860] ACPI: SSDT bf691c18 003A0 (v01  PmRef  Cpu0Ist 00003000 INTL 20060317)
Dec 24 10:28:39 laptop kernel: [    0.565458] ACPI: Dynamic OEM Table Load:
Dec 24 10:28:39 laptop kernel: [    0.565461] ACPI: SSDT   (null) 003A0 (v01  PmRef  Cpu0Ist 00003000 INTL 20060317)
Dec 24 10:28:39 laptop kernel: [    0.565621] ACPI: SSDT bf68f618 005CD (v01  PmRef  Cpu0Cst 00003001 INTL 20060317)
Dec 24 10:28:39 laptop kernel: [    0.566200] ACPI: Dynamic OEM Table Load:
Dec 24 10:28:39 laptop kernel: [    0.566202] ACPI: SSDT   (null) 005CD (v01  PmRef  Cpu0Cst 00003001 INTL 20060317)
Dec 24 10:28:39 laptop kernel: [    0.639720] ACPI: SSDT bf690a98 00303 (v01  PmRef    ApIst 00003000 INTL 20060317)
Dec 24 10:28:39 laptop kernel: [    0.640382] ACPI: Dynamic OEM Table Load:
Dec 24 10:28:39 laptop kernel: [    0.640385] ACPI: SSDT   (null) 00303 (v01  PmRef    ApIst 00003000 INTL 20060317)
Dec 24 10:28:39 laptop kernel: [    0.659533] ACPI: SSDT bf68ed98 00119 (v01  PmRef    ApCst 00003000 INTL 20060317)
Dec 24 10:28:39 laptop kernel: [    0.660151] ACPI: Dynamic OEM Table Load:
Dec 24 10:28:39 laptop kernel: [    0.660154] ACPI: SSDT   (null) 00119 (v01  PmRef    ApCst 00003000 INTL 20060317)
Dec 24 10:28:39 laptop kernel: [    0.691318] ACPI: Interpreter enabled
Dec 24 10:28:39 laptop kernel: [    0.691329] ACPI: (supports S0 S3 S4 S5)
Dec 24 10:28:39 laptop kernel: [    0.691374] ACPI: Using IOAPIC for interrupt routing
Dec 24 10:28:39 laptop kernel: [    0.731615] ACPI: EC: GPE = 0x16, I/O: command/status = 0x66, data = 0x62
Dec 24 10:28:39 laptop kernel: [    0.731909] ACPI: No dock devices found.
Dec 24 10:28:39 laptop kernel: [    0.731913] HEST: Table not found.
Dec 24 10:28:39 laptop kernel: [    0.731920] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
Dec 24 10:28:39 laptop kernel: [    0.732583] \_SB_.PCI0:_OSC invalid UUID
Dec 24 10:28:39 laptop kernel: [    0.732586] _OSC request data:1 8 1f 
Dec 24 10:28:39 laptop kernel: [    0.732593] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-fe])
Dec 24 10:28:39 laptop kernel: [    0.733691] pci_root PNP0A08:00: host bridge window [io  0x0000-0x0cf7]
Dec 24 10:28:39 laptop kernel: [    0.733695] pci_root PNP0A08:00: host bridge window [io  0x0d00-0xffff]
Dec 24 10:28:39 laptop kernel: [    0.733699] pci_root PNP0A08:00: host bridge window [mem 0x000a0000-0x000bffff]
Dec 24 10:28:39 laptop kernel: [    0.733705] pci_root PNP0A08:00: host bridge window [mem 0xc0000000-0xfeafffff]
Dec 24 10:28:39 laptop kernel: [    0.733725] pci 0000:00:00.0: [8086:0044] type 0 class 0x000600
Dec 24 10:28:39 laptop kernel: [    0.733751] DMAR: BIOS has allocated no shadow GTT; disabling IOMMU for graphics
Dec 24 10:28:39 laptop kernel: [    0.733776] pci 0000:00:01.0: [8086:0045] type 1 class 0x000604
Dec 24 10:28:39 laptop kernel: [    0.733812] pci 0000:00:01.0: PME# supported from D0 D3hot D3cold
Dec 24 10:28:39 laptop kernel: [    0.733817] pci 0000:00:01.0: PME# disabled
Dec 24 10:28:39 laptop kernel: [    0.733881] pci 0000:00:1a.0: [8086:3b3c] type 0 class 0x000c03
Dec 24 10:28:39 laptop kernel: [    0.734278] pci 0000:00:1a.0: reg 10: [mem 0xdb105c00-0xdb105fff]
Dec 24 10:28:39 laptop kernel: [    0.736540] pci 0000:00:1a.0: PME# supported from D0 D3hot D3cold
Dec 24 10:28:39 laptop kernel: [    0.736547] pci 0000:00:1a.0: PME# disabled
Dec 24 10:28:39 laptop kernel: [    0.736583] pci 0000:00:1b.0: [8086:3b56] type 0 class 0x000403
Dec 24 10:28:39 laptop kernel: [    0.736609] pci 0000:00:1b.0: reg 10: [mem 0xdb100000-0xdb103fff 64bit]
Dec 24 10:28:39 laptop kernel: [    0.736697] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
Dec 24 10:28:39 laptop kernel: [    0.736703] pci 0000:00:1b.0: PME# disabled
Dec 24 10:28:39 laptop kernel: [    0.736737] pci 0000:00:1c.0: [8086:3b42] type 1 class 0x000604
Dec 24 10:28:39 laptop kernel: [    0.736830] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
Dec 24 10:28:39 laptop kernel: [    0.736837] pci 0000:00:1c.0: PME# disabled
Dec 24 10:28:39 laptop kernel: [    0.736871] pci 0000:00:1c.1: [8086:3b44] type 1 class 0x000604
Dec 24 10:28:39 laptop kernel: [    0.736963] pci 0000:00:1c.1: PME# supported from D0 D3hot D3cold
Dec 24 10:28:39 laptop kernel: [    0.736969] pci 0000:00:1c.1: PME# disabled
Dec 24 10:28:39 laptop kernel: [    0.737006] pci 0000:00:1c.4: [8086:3b4a] type 1 class 0x000604
Dec 24 10:28:39 laptop kernel: [    0.737096] pci 0000:00:1c.4: PME# supported from D0 D3hot D3cold
Dec 24 10:28:39 laptop kernel: [    0.737102] pci 0000:00:1c.4: PME# disabled
Dec 24 10:28:39 laptop kernel: [    0.737139] pci 0000:00:1c.7: [8086:3b50] type 1 class 0x000604
Dec 24 10:28:39 laptop kernel: [    0.737232] pci 0000:00:1c.7: PME# supported from D0 D3hot D3cold
Dec 24 10:28:39 laptop kernel: [    0.737239] pci 0000:00:1c.7: PME# disabled
Dec 24 10:28:39 laptop kernel: [    0.737283] pci 0000:00:1d.0: [8086:3b34] type 0 class 0x000c03
Dec 24 10:28:39 laptop kernel: [    0.737672] pci 0000:00:1d.0: reg 10: [mem 0xdb105800-0xdb105bff]
Dec 24 10:28:39 laptop kernel: [    0.739931] pci 0000:00:1d.0: PME# supported from D0 D3hot D3cold
Dec 24 10:28:39 laptop kernel: [    0.739938] pci 0000:00:1d.0: PME# disabled
Dec 24 10:28:39 laptop kernel: [    0.739969] pci 0000:00:1e.0: [8086:2448] type 1 class 0x000604
Dec 24 10:28:39 laptop kernel: [    0.740059] pci 0000:00:1f.0: [8086:3b03] type 0 class 0x000601
Dec 24 10:28:39 laptop kernel: [    0.740190] pci 0000:00:1f.2: [8086:3b2f] type 0 class 0x000106
Dec 24 10:28:39 laptop kernel: [    0.740220] pci 0000:00:1f.2: reg 10: [io  0x7048-0x704f]
Dec 24 10:28:39 laptop kernel: [    0.740231] pci 0000:00:1f.2: reg 14: [io  0x7054-0x7057]
Dec 24 10:28:39 laptop kernel: [    0.740243] pci 0000:00:1f.2: reg 18: [io  0x7040-0x7047]
Dec 24 10:28:39 laptop kernel: [    0.740255] pci 0000:00:1f.2: reg 1c: [io  0x7050-0x7053]
Dec 24 10:28:39 laptop kernel: [    0.740267] pci 0000:00:1f.2: reg 20: [io  0x7020-0x703f]
Dec 24 10:28:39 laptop kernel: [    0.740279] pci 0000:00:1f.2: reg 24: [mem 0xdb105000-0xdb1057ff]
Dec 24 10:28:39 laptop kernel: [    0.740329] pci 0000:00:1f.2: PME# supported from D3hot
Dec 24 10:28:39 laptop kernel: [    0.740334] pci 0000:00:1f.2: PME# disabled
Dec 24 10:28:39 laptop kernel: [    0.740358] pci 0000:00:1f.3: [8086:3b30] type 0 class 0x000c05
Dec 24 10:28:39 laptop kernel: [    0.740380] pci 0000:00:1f.3: reg 10: [mem 0xdb106000-0xdb1060ff 64bit]
Dec 24 10:28:39 laptop kernel: [    0.740412] pci 0000:00:1f.3: reg 20: [io  0x7000-0x701f]
Dec 24 10:28:39 laptop kernel: [    0.740485] pci 0000:01:00.0: [10de:0a68] type 0 class 0x000300
Dec 24 10:28:39 laptop kernel: [    0.740495] pci 0000:01:00.0: reg 10: [mem 0xd2000000-0xd2ffffff]
Dec 24 10:28:39 laptop kernel: [    0.740506] pci 0000:01:00.0: reg 14: [mem 0xc0000000-0xcfffffff 64bit pref]
Dec 24 10:28:39 laptop kernel: [    0.740517] pci 0000:01:00.0: reg 1c: [mem 0xd0000000-0xd1ffffff 64bit pref]
Dec 24 10:28:39 laptop kernel: [    0.740524] pci 0000:01:00.0: reg 24: [io  0x6000-0x607f]
Dec 24 10:28:39 laptop kernel: [    0.740532] pci 0000:01:00.0: reg 30: [mem 0xfff80000-0xffffffff pref]
Dec 24 10:28:39 laptop kernel: [    0.740573] pci 0000:01:00.1: [10de:0be3] type 0 class 0x000403
Dec 24 10:28:39 laptop kernel: [    0.740583] pci 0000:01:00.1: reg 10: [mem 0xd3000000-0xd3003fff]
Dec 24 10:28:39 laptop kernel: [    0.740655] pci 0000:00:01.0: PCI bridge to [bus 01-01]
Dec 24 10:28:39 laptop kernel: [    0.740658] pci 0000:00:01.0:   bridge window [io  0x6000-0x6fff]
Dec 24 10:28:39 laptop kernel: [    0.740661] pci 0000:00:01.0:   bridge window [mem 0xd2000000-0xd30fffff]
Dec 24 10:28:39 laptop kernel: [    0.740666] pci 0000:00:01.0:   bridge window [mem 0xc0000000-0xd1ffffff 64bit pref]
Dec 24 10:28:39 laptop kernel: [    0.740765] pci 0000:02:00.0: [14e4:4357] type 0 class 0x000280
Dec 24 10:28:39 laptop kernel: [    0.740812] pci 0000:02:00.0: reg 10: [mem 0xda100000-0xda103fff 64bit]
Dec 24 10:28:39 laptop kernel: [    0.740987] pci 0000:02:00.0: supports D1 D2
Dec 24 10:28:39 laptop kernel: [    0.741058] pci 0000:00:1c.0: PCI bridge to [bus 02-02]
Dec 24 10:28:39 laptop kernel: [    0.741063] pci 0000:00:1c.0:   bridge window [io  0x5000-0x5fff]
Dec 24 10:28:39 laptop kernel: [    0.741068] pci 0000:00:1c.0:   bridge window [mem 0xda100000-0xdb0fffff]
Dec 24 10:28:39 laptop kernel: [    0.741076] pci 0000:00:1c.0:   bridge window [mem 0xd3100000-0xd40fffff 64bit pref]
Dec 24 10:28:39 laptop kernel: [    0.741207] pci 0000:03:00.0: [10ec:8168] type 0 class 0x000200
Dec 24 10:28:39 laptop kernel: [    0.741272] pci 0000:03:00.0: reg 10: [io  0x4000-0x40ff]
Dec 24 10:28:39 laptop kernel: [    0.741363] pci 0000:03:00.0: reg 18: [mem 0xd4104000-0xd4104fff 64bit pref]
Dec 24 10:28:39 laptop kernel: [    0.741420] pci 0000:03:00.0: reg 20: [mem 0xd4100000-0xd4103fff 64bit pref]
Dec 24 10:28:39 laptop kernel: [    0.741466] pci 0000:03:00.0: reg 30: [mem 0xffff0000-0xffffffff pref]
Dec 24 10:28:39 laptop kernel: [    0.741625] pci 0000:03:00.0: supports D1 D2
Dec 24 10:28:39 laptop kernel: [    0.741627] pci 0000:03:00.0: PME# supported from D0 D1 D2 D3hot D3cold
Dec 24 10:28:39 laptop kernel: [    0.741642] pci 0000:03:00.0: PME# disabled
Dec 24 10:28:39 laptop kernel: [    0.741778] pci 0000:00:1c.1: PCI bridge to [bus 03-03]
Dec 24 10:28:39 laptop kernel: [    0.741783] pci 0000:00:1c.1:   bridge window [io  0x4000-0x4fff]
Dec 24 10:28:39 laptop kernel: [    0.741788] pci 0000:00:1c.1:   bridge window [mem 0xd9100000-0xda0fffff]
Dec 24 10:28:39 laptop kernel: [    0.741796] pci 0000:00:1c.1:   bridge window [mem 0xd4100000-0xd50fffff 64bit pref]
Dec 24 10:28:39 laptop kernel: [    0.741885] pci 0000:04:00.0: [197b:2380] type 0 class 0x000c00
Dec 24 10:28:39 laptop kernel: [    0.741923] pci 0000:04:00.0: reg 10: [mem 0xd8100000-0xd81007ff]
Dec 24 10:28:39 laptop kernel: [    0.741950] pci 0000:04:00.0: reg 14: [mem 0xd8100d00-0xd8100d7f]
Dec 24 10:28:39 laptop kernel: [    0.742027] pci 0000:04:00.0: reg 20: [mem 0xd8100c80-0xd8100cff]
Dec 24 10:28:39 laptop kernel: [    0.742054] pci 0000:04:00.0: reg 24: [mem 0xd8100c00-0xd8100c7f]
Dec 24 10:28:39 laptop kernel: [    0.742208] pci 0000:04:00.1: [197b:2382] type 0 class 0x000880
Dec 24 10:28:39 laptop kernel: [    0.742242] pci 0000:04:00.1: reg 10: [mem 0xd8100b00-0xd8100bff]
Dec 24 10:28:39 laptop kernel: [    0.742491] pci 0000:04:00.2: [197b:2381] type 0 class 0x000805
Dec 24 10:28:39 laptop kernel: [    0.742526] pci 0000:04:00.2: reg 10: [mem 0xd8100a00-0xd8100aff]
Dec 24 10:28:39 laptop kernel: [    0.742776] pci 0000:04:00.3: [197b:2383] type 0 class 0x000880
Dec 24 10:28:39 laptop kernel: [    0.742809] pci 0000:04:00.3: reg 10: [mem 0xd8100900-0xd81009ff]
Dec 24 10:28:39 laptop kernel: [    0.743057] pci 0000:04:00.4: [197b:2384] type 0 class 0x000880
Dec 24 10:28:39 laptop kernel: [    0.743091] pci 0000:04:00.4: reg 10: [mem 0xd8100800-0xd81008ff]
Dec 24 10:28:39 laptop kernel: [    0.743358] pci 0000:00:1c.4: PCI bridge to [bus 04-04]
Dec 24 10:28:39 laptop kernel: [    0.743363] pci 0000:00:1c.4:   bridge window [io  0x3000-0x3fff]
Dec 24 10:28:39 laptop kernel: [    0.743369] pci 0000:00:1c.4:   bridge window [mem 0xd8100000-0xd90fffff]
Dec 24 10:28:39 laptop kernel: [    0.743377] pci 0000:00:1c.4:   bridge window [mem 0xd5100000-0xd60fffff 64bit pref]
Dec 24 10:28:39 laptop kernel: [    0.743440] pci 0000:00:1c.7: PCI bridge to [bus 05-08]
Dec 24 10:28:39 laptop kernel: [    0.743446] pci 0000:00:1c.7:   bridge window [io  0x2000-0x2fff]
Dec 24 10:28:39 laptop kernel: [    0.743451] pci 0000:00:1c.7:   bridge window [mem 0xd7100000-0xd80fffff]
Dec 24 10:28:39 laptop kernel: [    0.743459] pci 0000:00:1c.7:   bridge window [mem 0xd6100000-0xd70fffff 64bit pref]
Dec 24 10:28:39 laptop kernel: [    0.743537] pci 0000:00:1e.0: PCI bridge to [bus 09-09] (subtractive decode)
Dec 24 10:28:39 laptop kernel: [    0.743543] pci 0000:00:1e.0:   bridge window [io  0xf000-0x0000] (disabled)
Dec 24 10:28:39 laptop kernel: [    0.743548] pci 0000:00:1e.0:   bridge window [mem 0xfff00000-0x000fffff] (disabled)
Dec 24 10:28:39 laptop kernel: [    0.743556] pci 0000:00:1e.0:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
Dec 24 10:28:39 laptop kernel: [    0.743558] pci 0000:00:1e.0:   bridge window [io  0x0000-0x0cf7] (subtractive decode)
Dec 24 10:28:39 laptop kernel: [    0.743561] pci 0000:00:1e.0:   bridge window [io  0x0d00-0xffff] (subtractive decode)
Dec 24 10:28:39 laptop kernel: [    0.743563] pci 0000:00:1e.0:   bridge window [mem 0x000a0000-0x000bffff] (subtractive decode)
Dec 24 10:28:39 laptop kernel: [    0.743566] pci 0000:00:1e.0:   bridge window [mem 0xc0000000-0xfeafffff] (subtractive decode)
Dec 24 10:28:39 laptop kernel: [    0.743600] pci_bus 0000:00: on NUMA node 0
Dec 24 10:28:39 laptop kernel: [    0.743605] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
Dec 24 10:28:39 laptop kernel: [    0.743770] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P3._PRT]
Dec 24 10:28:39 laptop kernel: [    0.743811] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P1._PRT]
Dec 24 10:28:39 laptop kernel: [    0.743828] ACPI Warning: For \_SB_.PCI0.P0P1._PRT: Return Package has no elements (empty) (20110413/nspredef-457)
Dec 24 10:28:39 laptop kernel: [    0.743864] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP01._PRT]
Dec 24 10:28:39 laptop kernel: [    0.743904] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP02._PRT]
Dec 24 10:28:39 laptop kernel: [    0.743952] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP05._PRT]
Dec 24 10:28:39 laptop kernel: [    0.744015] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP08._PRT]
Dec 24 10:28:39 laptop kernel: [    0.744106] \_SB_.PCI0:_OSC invalid UUID
Dec 24 10:28:39 laptop kernel: [    0.744108] _OSC request data:1 1f 1f 
Dec 24 10:28:39 laptop kernel: [    0.744112]  pci0000:00: Requesting ACPI _OSC control (0x1d)
Dec 24 10:28:39 laptop kernel: [    0.744150] \_SB_.PCI0:_OSC invalid UUID
Dec 24 10:28:39 laptop kernel: [    0.744151] _OSC request data:1 0 1d 
Dec 24 10:28:39 laptop kernel: [    0.744155]  pci0000:00: ACPI _OSC request failed (AE_ERROR), returned control mask: 0x1d
Dec 24 10:28:39 laptop kernel: [    0.744157] ACPI _OSC control for PCIe not granted, disabling ASPM
Dec 24 10:28:39 laptop kernel: [    0.749454] ACPI: PCI Root Bridge [CPBG] (domain 0000 [bus ff])
Dec 24 10:28:39 laptop kernel: [    0.749522] pci 0000:ff:00.0: [8086:2c62] type 0 class 0x000600
Dec 24 10:28:39 laptop kernel: [    0.749544] pci 0000:ff:00.1: [8086:2d01] type 0 class 0x000600
Dec 24 10:28:39 laptop kernel: [    0.749567] pci 0000:ff:02.0: [8086:2d10] type 0 class 0x000600
Dec 24 10:28:39 laptop kernel: [    0.749587] pci 0000:ff:02.1: [8086:2d11] type 0 class 0x000600
Dec 24 10:28:39 laptop kernel: [    0.749607] pci 0000:ff:02.2: [8086:2d12] type 0 class 0x000600
Dec 24 10:28:39 laptop kernel: [    0.749627] pci 0000:ff:02.3: [8086:2d13] type 0 class 0x000600
Dec 24 10:28:39 laptop kernel: [    0.749657] pci_bus 0000:ff: on NUMA node 0
Dec 24 10:28:39 laptop kernel: [    0.749666]  pci0000:ff: Requesting ACPI _OSC control (0x1d)
Dec 24 10:28:39 laptop kernel: [    0.749668]  pci0000:ff: ACPI _OSC request failed (AE_NOT_FOUND), returned control mask: 0x1d
Dec 24 10:28:39 laptop kernel: [    0.749670] ACPI _OSC control for PCIe not granted, disabling ASPM
Dec 24 10:28:39 laptop kernel: [    0.749906] ACPI: PCI Interrupt Link [LNKA] (IRQs 1 3 4 *5 6 7 10 12 14 15)
Dec 24 10:28:39 laptop kernel: [    0.749957] ACPI: PCI Interrupt Link [LNKB] (IRQs 1 3 4 *5 6 7 11 12 14 15)
Dec 24 10:28:39 laptop kernel: [    0.750005] ACPI: PCI Interrupt Link [LNKC] (IRQs 1 3 4 5 6 7 10 12 14 15) *11
Dec 24 10:28:39 laptop kernel: [    0.750054] ACPI: PCI Interrupt Link [LNKD] (IRQs 1 3 4 *5 6 7 11 12 14 15)
Dec 24 10:28:39 laptop kernel: [    0.750102] ACPI: PCI Interrupt Link [LNKE] (IRQs 1 3 4 5 6 7 10 12 14 15) *0, disabled.
Dec 24 10:28:39 laptop kernel: [    0.750151] ACPI: PCI Interrupt Link [LNKF] (IRQs 1 3 4 5 6 7 *11 12 14 15)
Dec 24 10:28:39 laptop kernel: [    0.750199] ACPI: PCI Interrupt Link [LNKG] (IRQs 1 3 4 5 6 7 *10 12 14 15)
Dec 24 10:28:39 laptop kernel: [    0.750248] ACPI: PCI Interrupt Link [LNKH] (IRQs 1 3 4 5 6 7 11 12 14 15) *0, disabled.
Dec 24 10:28:39 laptop kernel: [    0.750360] vgaarb: device added: PCI:0000:01:00.0,decodes=io+mem,owns=io+mem,locks=none
Dec 24 10:28:39 laptop kernel: [    0.750368] vgaarb: loaded
Dec 24 10:28:39 laptop kernel: [    0.750369] vgaarb: bridge control possible 0000:01:00.0
Dec 24 10:28:39 laptop kernel: [    0.750570] SCSI subsystem initialized
Dec 24 10:28:39 laptop kernel: [    0.750646] libata version 3.00 loaded.
Dec 24 10:28:39 laptop kernel: [    0.750688] usbcore: registered new interface driver usbfs
Dec 24 10:28:39 laptop kernel: [    0.750698] usbcore: registered new interface driver hub
Dec 24 10:28:39 laptop kernel: [    0.750726] usbcore: registered new device driver usb
Dec 24 10:28:39 laptop kernel: [    0.750812] PCI: Using ACPI for IRQ routing
Dec 24 10:28:39 laptop kernel: [    0.760770] PCI: pci_cache_line_size set to 64 bytes
Dec 24 10:28:39 laptop kernel: [    0.760896] reserve RAM buffer: 000000000009d000 - 000000000009ffff 
Dec 24 10:28:39 laptop kernel: [    0.760899] reserve RAM buffer: 00000000bf681000 - 00000000bfffffff 
Dec 24 10:28:39 laptop kernel: [    0.760903] reserve RAM buffer: 00000000bf75d000 - 00000000bfffffff 
Dec 24 10:28:39 laptop kernel: [    0.760905] reserve RAM buffer: 00000000bf7e1000 - 00000000bfffffff 
Dec 24 10:28:39 laptop kernel: [    0.760908] reserve RAM buffer: 00000000bf800000 - 00000000bfffffff 
Dec 24 10:28:39 laptop kernel: [    0.761017] NetLabel: Initializing
Dec 24 10:28:39 laptop kernel: [    0.761019] NetLabel:  domain hash size = 128
Dec 24 10:28:39 laptop kernel: [    0.761020] NetLabel:  protocols = UNLABELED CIPSOv4
Dec 24 10:28:39 laptop kernel: [    0.761031] NetLabel:  unlabeled traffic allowed by default
Dec 24 10:28:39 laptop kernel: [    0.761089] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0, 0, 0, 0, 0
Dec 24 10:28:39 laptop kernel: [    0.761096] hpet0: 8 comparators, 64-bit 14.318180 MHz counter
Dec 24 10:28:39 laptop kernel: [    0.763119] Switching to clocksource hpet
Dec 24 10:28:39 laptop kernel: [    0.763329] Switched to NOHz mode on CPU #0
Dec 24 10:28:39 laptop kernel: [    0.763388] Switched to NOHz mode on CPU #2
Dec 24 10:28:39 laptop kernel: [    0.763418] Switched to NOHz mode on CPU #3
Dec 24 10:28:39 laptop kernel: [    0.763465] Switched to NOHz mode on CPU #1
Dec 24 10:28:39 laptop kernel: [    0.769563] AppArmor: AppArmor Filesystem Enabled
Dec 24 10:28:39 laptop kernel: [    0.769592] pnp: PnP ACPI init
Dec 24 10:28:39 laptop kernel: [    0.769610] ACPI: bus type pnp registered
Dec 24 10:28:39 laptop kernel: [    0.770296] pnp 00:00: [bus 00-fe]
Dec 24 10:28:39 laptop kernel: [    0.770299] pnp 00:00: [io  0x0000-0x0cf7 window]
Dec 24 10:28:39 laptop kernel: [    0.770302] pnp 00:00: [io  0x0cf8-0x0cff]
Dec 24 10:28:39 laptop kernel: [    0.770304] pnp 00:00: [io  0x0d00-0xffff window]
Dec 24 10:28:39 laptop kernel: [    0.770306] pnp 00:00: [mem 0x000a0000-0x000bffff window]
Dec 24 10:28:39 laptop kernel: [    0.770308] pnp 00:00: [mem 0x000c0000-0x000c3fff window]
Dec 24 10:28:39 laptop kernel: [    0.770311] pnp 00:00: [mem 0x000c4000-0x000c7fff window]
Dec 24 10:28:39 laptop kernel: [    0.770313] pnp 00:00: [mem 0x000c8000-0x000cbfff window]
Dec 24 10:28:39 laptop kernel: [    0.770315] pnp 00:00: [mem 0x000cc000-0x000cffff window]
Dec 24 10:28:39 laptop kernel: [    0.770317] pnp 00:00: [mem 0x000d0000-0x000d3fff window]
Dec 24 10:28:39 laptop kernel: [    0.770319] pnp 00:00: [mem 0x000d4000-0x000d7fff window]
Dec 24 10:28:39 laptop kernel: [    0.770322] pnp 00:00: [mem 0x000d8000-0x000dbfff window]
Dec 24 10:28:39 laptop kernel: [    0.770324] pnp 00:00: [mem 0x000dc000-0x000dffff window]
Dec 24 10:28:39 laptop kernel: [    0.770326] pnp 00:00: [mem 0x000e0000-0x000e3fff window]
Dec 24 10:28:39 laptop kernel: [    0.770328] pnp 00:00: [mem 0x000e4000-0x000e7fff window]
Dec 24 10:28:39 laptop kernel: [    0.770330] pnp 00:00: [mem 0x000e8000-0x000ebfff window]
Dec 24 10:28:39 laptop kernel: [    0.770333] pnp 00:00: [mem 0x000ec000-0x000effff window]
Dec 24 10:28:39 laptop kernel: [    0.770335] pnp 00:00: [mem 0x000f0000-0x000fffff window]
Dec 24 10:28:39 laptop kernel: [    0.770337] pnp 00:00: [mem 0xc0000000-0xfeafffff window]
Dec 24 10:28:39 laptop kernel: [    0.770339] pnp 00:00: [mem 0xfed40000-0xfed44fff window]
Dec 24 10:28:39 laptop kernel: [    0.770419] pnp 00:00: Plug and Play ACPI device, IDs PNP0a08 PNP0a03 (active)
Dec 24 10:28:39 laptop kernel: [    0.770493] pnp 00:01: [io  0x0380-0x038e]
Dec 24 10:28:39 laptop kernel: [    0.770505] pnp 00:01: [irq 4]
Dec 24 10:28:39 laptop kernel: [    0.770540] pnp 00:01: Plug and Play ACPI device, IDs ENE0100 (active)
Dec 24 10:28:39 laptop kernel: [    0.770550] pnp 00:02: [io  0x0000-0x001f]
Dec 24 10:28:39 laptop kernel: [    0.770552] pnp 00:02: [io  0x0081-0x0091]
Dec 24 10:28:39 laptop kernel: [    0.770554] pnp 00:02: [io  0x0093-0x009f]
Dec 24 10:28:39 laptop kernel: [    0.770556] pnp 00:02: [io  0x00c0-0x00df]
Dec 24 10:28:39 laptop kernel: [    0.770558] pnp 00:02: [dma 4]
Dec 24 10:28:39 laptop kernel: [    0.770586] pnp 00:02: Plug and Play ACPI device, IDs PNP0200 (active)
Dec 24 10:28:39 laptop kernel: [    0.770595] pnp 00:03: [mem 0xff000000-0xffffffff]
Dec 24 10:28:39 laptop kernel: [    0.770623] pnp 00:03: Plug and Play ACPI device, IDs INT0800 (active)
Dec 24 10:28:39 laptop kernel: [    0.770716] pnp 00:04: [mem 0xfed00000-0xfed003ff]
Dec 24 10:28:39 laptop kernel: [    0.770747] pnp 00:04: Plug and Play ACPI device, IDs PNP0103 (active)
Dec 24 10:28:39 laptop kernel: [    0.770758] pnp 00:05: [io  0x00f0]
Dec 24 10:28:39 laptop kernel: [    0.770764] pnp 00:05: [irq 13]
Dec 24 10:28:39 laptop kernel: [    0.770794] pnp 00:05: Plug and Play ACPI device, IDs PNP0c04 (active)
Dec 24 10:28:39 laptop kernel: [    0.770805] pnp 00:06: [io  0x002e-0x002f]
Dec 24 10:28:39 laptop kernel: [    0.770808] pnp 00:06: [io  0x004e-0x004f]
Dec 24 10:28:39 laptop kernel: [    0.770810] pnp 00:06: [io  0x0061]
Dec 24 10:28:39 laptop kernel: [    0.770811] pnp 00:06: [io  0x0063]
Dec 24 10:28:39 laptop kernel: [    0.770815] pnp 00:06: [io  0x0065]
Dec 24 10:28:39 laptop kernel: [    0.770817] pnp 00:06: [io  0x0067]
Dec 24 10:28:39 laptop kernel: [    0.770818] pnp 00:06: [io  0x0070]
Dec 24 10:28:39 laptop kernel: [    0.770820] pnp 00:06: [io  0x0080]
Dec 24 10:28:39 laptop kernel: [    0.770822] pnp 00:06: [io  0x0092]
Dec 24 10:28:39 laptop kernel: [    0.770824] pnp 00:06: [io  0x00b2-0x00b3]
Dec 24 10:28:39 laptop kernel: [    0.770826] pnp 00:06: [io  0x0680-0x069f]
Dec 24 10:28:39 laptop kernel: [    0.770827] pnp 00:06: [io  0x0800-0x080f]
Dec 24 10:28:39 laptop kernel: [    0.770829] pnp 00:06: [io  0xffff]
Dec 24 10:28:39 laptop kernel: [    0.770831] pnp 00:06: [io  0xffff]
Dec 24 10:28:39 laptop kernel: [    0.770833] pnp 00:06: [io  0x0400-0x047f]
Dec 24 10:28:39 laptop kernel: [    0.770835] pnp 00:06: [io  0x0500-0x057f]
Dec 24 10:28:39 laptop kernel: [    0.770837] pnp 00:06: [io  0x164e-0x164f]
Dec 24 10:28:39 laptop kernel: [    0.770839] pnp 00:06: [io  0x0380-0x038e]
Dec 24 10:28:39 laptop kernel: [    0.770913] system 00:06: [io  0x0680-0x069f] has been reserved
Dec 24 10:28:39 laptop kernel: [    0.770915] system 00:06: [io  0x0800-0x080f] has been reserved
Dec 24 10:28:39 laptop kernel: [    0.770918] system 00:06: [io  0xffff] has been reserved
Dec 24 10:28:39 laptop kernel: [    0.770921] system 00:06: [io  0xffff] has been reserved
Dec 24 10:28:39 laptop kernel: [    0.770923] system 00:06: [io  0x0400-0x047f] has been reserved
Dec 24 10:28:39 laptop kernel: [    0.770926] system 00:06: [io  0x0500-0x057f] has been reserved
Dec 24 10:28:39 laptop kernel: [    0.770928] system 00:06: [io  0x164e-0x164f] has been reserved
Dec 24 10:28:39 laptop kernel: [    0.770931] system 00:06: [io  0x0380-0x038e] has been reserved
Dec 24 10:28:39 laptop kernel: [    0.770934] system 00:06: Plug and Play ACPI device, IDs PNP0c02 (active)
Dec 24 10:28:39 laptop kernel: [    0.770943] pnp 00:07: [io  0x0070-0x0077]
Dec 24 10:28:39 laptop kernel: [    0.770949] pnp 00:07: [irq 8]
Dec 24 10:28:39 laptop kernel: [    0.770980] pnp 00:07: Plug and Play ACPI device, IDs PNP0b00 (active)
Dec 24 10:28:39 laptop kernel: [    0.770991] pnp 00:08: [io  0x0060]
Dec 24 10:28:39 laptop kernel: [    0.770993] pnp 00:08: [io  0x0064]
Dec 24 10:28:39 laptop kernel: [    0.770998] pnp 00:08: [irq 1]
Dec 24 10:28:39 laptop kernel: [    0.771040] pnp 00:08: Plug and Play ACPI device, IDs PNP0303 (active)
Dec 24 10:28:39 laptop kernel: [    0.771059] pnp 00:09: [irq 12]
Dec 24 10:28:39 laptop kernel: [    0.771119] pnp 00:09: Plug and Play ACPI device, IDs SYN1e10 SYN1e00 SYN0002 PNP0f13 (active)
Dec 24 10:28:39 laptop kernel: [    0.771271] pnp 00:0a: [irq 23]
Dec 24 10:28:39 laptop kernel: [    0.771315] pnp 00:0a: Plug and Play ACPI device, IDs HPQ0004 (active)
Dec 24 10:28:39 laptop kernel: [    0.771528] pnp 00:0b: [mem 0xfed1c000-0xfed1ffff]
Dec 24 10:28:39 laptop kernel: [    0.771531] pnp 00:0b: [mem 0xfed10000-0xfed13fff]
Dec 24 10:28:39 laptop kernel: [    0.771533] pnp 00:0b: [mem 0xfed18000-0xfed18fff]
Dec 24 10:28:39 laptop kernel: [    0.771535] pnp 00:0b: [mem 0xfed19000-0xfed19fff]
Dec 24 10:28:39 laptop kernel: [    0.771537] pnp 00:0b: [mem 0xe0000000-0xefffffff]
Dec 24 10:28:39 laptop kernel: [    0.771539] pnp 00:0b: [mem 0xfed20000-0xfed3ffff]
Dec 24 10:28:39 laptop kernel: [    0.771541] pnp 00:0b: [mem 0xfed90000-0xfed8ffff disabled]
Dec 24 10:28:39 laptop kernel: [    0.771543] pnp 00:0b: [mem 0xfed45000-0xfed8ffff]
Dec 24 10:28:39 laptop kernel: [    0.771545] pnp 00:0b: [mem 0xff000000-0xffffffff]
Dec 24 10:28:39 laptop kernel: [    0.771547] pnp 00:0b: [mem 0xfee00000-0xfeefffff]
Dec 24 10:28:39 laptop kernel: [    0.771549] pnp 00:0b: [mem 0xdb200000-0xdb200fff]
Dec 24 10:28:39 laptop kernel: [    0.771620] system 00:0b: [mem 0xfed1c000-0xfed1ffff] has been reserved
Dec 24 10:28:39 laptop kernel: [    0.771623] system 00:0b: [mem 0xfed10000-0xfed13fff] has been reserved
Dec 24 10:28:39 laptop kernel: [    0.771626] system 00:0b: [mem 0xfed18000-0xfed18fff] has been reserved
Dec 24 10:28:39 laptop kernel: [    0.771629] system 00:0b: [mem 0xfed19000-0xfed19fff] has been reserved
Dec 24 10:28:39 laptop kernel: [    0.771631] system 00:0b: [mem 0xe0000000-0xefffffff] has been reserved
Dec 24 10:28:39 laptop kernel: [    0.771634] system 00:0b: [mem 0xfed20000-0xfed3ffff] has been reserved
Dec 24 10:28:39 laptop kernel: [    0.771637] system 00:0b: [mem 0xfed45000-0xfed8ffff] has been reserved
Dec 24 10:28:39 laptop kernel: [    0.771640] system 00:0b: [mem 0xff000000-0xffffffff] could not be reserved
Dec 24 10:28:39 laptop kernel: [    0.771642] system 00:0b: [mem 0xfee00000-0xfeefffff] could not be reserved
Dec 24 10:28:39 laptop kernel: [    0.771645] system 00:0b: [mem 0xdb200000-0xdb200fff] has been reserved
Dec 24 10:28:39 laptop kernel: [    0.771648] system 00:0b: Plug and Play ACPI device, IDs PNP0c02 (active)
Dec 24 10:28:39 laptop kernel: [    0.771798] pnp 00:0c: [bus ff]
Dec 24 10:28:39 laptop kernel: [    0.771842] pnp 00:0c: Plug and Play ACPI device, IDs PNP0a03 (active)
Dec 24 10:28:39 laptop kernel: [    0.771859] pnp: PnP ACPI: found 13 devices
Dec 24 10:28:39 laptop kernel: [    0.771860] ACPI: ACPI bus type pnp unregistered
Dec 24 10:28:39 laptop kernel: [    0.771864] PnPBIOS: Disabled by ACPI PNP
Dec 24 10:28:39 laptop kernel: [    0.807758] pci 0000:01:00.0: no compatible bridge window for [mem 0xfff80000-0xffffffff pref]
Dec 24 10:28:39 laptop kernel: [    0.807765] pci 0000:03:00.0: no compatible bridge window for [mem 0xffff0000-0xffffffff pref]
Dec 24 10:28:39 laptop kernel: [    0.807776] PCI: max bus depth: 1 pci_try_num: 2
Dec 24 10:28:39 laptop kernel: [    0.807839] pci 0000:01:00.0: BAR 6: assigned [mem 0xd3080000-0xd30fffff pref]
Dec 24 10:28:39 laptop kernel: [    0.807842] pci 0000:00:01.0: PCI bridge to [bus 01-01]
Dec 24 10:28:39 laptop kernel: [    0.807845] pci 0000:00:01.0:   bridge window [io  0x6000-0x6fff]
Dec 24 10:28:39 laptop kernel: [    0.807849] pci 0000:00:01.0:   bridge window [mem 0xd2000000-0xd30fffff]
Dec 24 10:28:39 laptop kernel: [    0.807852] pci 0000:00:01.0:   bridge window [mem 0xc0000000-0xd1ffffff 64bit pref]
Dec 24 10:28:39 laptop kernel: [    0.807857] pci 0000:00:1c.0: PCI bridge to [bus 02-02]
Dec 24 10:28:39 laptop kernel: [    0.807861] pci 0000:00:1c.0:   bridge window [io  0x5000-0x5fff]
Dec 24 10:28:39 laptop kernel: [    0.807868] pci 0000:00:1c.0:   bridge window [mem 0xda100000-0xdb0fffff]
Dec 24 10:28:39 laptop kernel: [    0.807873] pci 0000:00:1c.0:   bridge window [mem 0xd3100000-0xd40fffff 64bit pref]
Dec 24 10:28:39 laptop kernel: [    0.807883] pci 0000:03:00.0: BAR 6: assigned [mem 0xd4110000-0xd411ffff pref]
Dec 24 10:28:39 laptop kernel: [    0.807885] pci 0000:00:1c.1: PCI bridge to [bus 03-03]
Dec 24 10:28:39 laptop kernel: [    0.807889] pci 0000:00:1c.1:   bridge window [io  0x4000-0x4fff]
Dec 24 10:28:39 laptop kernel: [    0.807895] pci 0000:00:1c.1:   bridge window [mem 0xd9100000-0xda0fffff]
Dec 24 10:28:39 laptop kernel: [    0.807901] pci 0000:00:1c.1:   bridge window [mem 0xd4100000-0xd50fffff 64bit pref]
Dec 24 10:28:39 laptop kernel: [    0.807910] pci 0000:00:1c.4: PCI bridge to [bus 04-04]
Dec 24 10:28:39 laptop kernel: [    0.807914] pci 0000:00:1c.4:   bridge window [io  0x3000-0x3fff]
Dec 24 10:28:39 laptop kernel: [    0.807921] pci 0000:00:1c.4:   bridge window [mem 0xd8100000-0xd90fffff]
Dec 24 10:28:39 laptop kernel: [    0.807926] pci 0000:00:1c.4:   bridge window [mem 0xd5100000-0xd60fffff 64bit pref]
Dec 24 10:28:39 laptop kernel: [    0.807934] pci 0000:00:1c.7: PCI bridge to [bus 05-08]
Dec 24 10:28:39 laptop kernel: [    0.807938] pci 0000:00:1c.7:   bridge window [io  0x2000-0x2fff]
Dec 24 10:28:39 laptop kernel: [    0.807945] pci 0000:00:1c.7:   bridge window [mem 0xd7100000-0xd80fffff]
Dec 24 10:28:39 laptop kernel: [    0.807950] pci 0000:00:1c.7:   bridge window [mem 0xd6100000-0xd70fffff 64bit pref]
Dec 24 10:28:39 laptop kernel: [    0.807958] pci 0000:00:1e.0: PCI bridge to [bus 09-09]
Dec 24 10:28:39 laptop kernel: [    0.807960] pci 0000:00:1e.0:   bridge window [io  disabled]
Dec 24 10:28:39 laptop kernel: [    0.807966] pci 0000:00:1e.0:   bridge window [mem disabled]
Dec 24 10:28:39 laptop kernel: [    0.807971] pci 0000:00:1e.0:   bridge window [mem pref disabled]
Dec 24 10:28:39 laptop kernel: [    0.807999] pci 0000:00:01.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Dec 24 10:28:39 laptop kernel: [    0.808004] pci 0000:00:01.0: setting latency timer to 64
Dec 24 10:28:39 laptop kernel: [    0.808016] pci 0000:00:1c.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
Dec 24 10:28:39 laptop kernel: [    0.808021] pci 0000:00:1c.0: setting latency timer to 64
Dec 24 10:28:39 laptop kernel: [    0.808029] pci 0000:00:1c.1: PCI INT B -> GSI 16 (level, low) -> IRQ 16
Dec 24 10:28:39 laptop kernel: [    0.808035] pci 0000:00:1c.1: setting latency timer to 64
Dec 24 10:28:39 laptop kernel: [    0.808043] pci 0000:00:1c.4: PCI INT A -> GSI 17 (level, low) -> IRQ 17
Dec 24 10:28:39 laptop kernel: [    0.808048] pci 0000:00:1c.4: setting latency timer to 64
Dec 24 10:28:39 laptop kernel: [    0.808056] pci 0000:00:1c.7: PCI INT B -> GSI 16 (level, low) -> IRQ 16
Dec 24 10:28:39 laptop kernel: [    0.808061] pci 0000:00:1c.7: setting latency timer to 64
Dec 24 10:28:39 laptop kernel: [    0.808070] pci 0000:00:1e.0: setting latency timer to 64
Dec 24 10:28:39 laptop kernel: [    0.808075] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
Dec 24 10:28:39 laptop kernel: [    0.808078] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff]
Dec 24 10:28:39 laptop kernel: [    0.808080] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
Dec 24 10:28:39 laptop kernel: [    0.808082] pci_bus 0000:00: resource 7 [mem 0xc0000000-0xfeafffff]
Dec 24 10:28:39 laptop kernel: [    0.808085] pci_bus 0000:01: resource 0 [io  0x6000-0x6fff]
Dec 24 10:28:39 laptop kernel: [    0.808087] pci_bus 0000:01: resource 1 [mem 0xd2000000-0xd30fffff]
Dec 24 10:28:39 laptop kernel: [    0.808089] pci_bus 0000:01: resource 2 [mem 0xc0000000-0xd1ffffff 64bit pref]
Dec 24 10:28:39 laptop kernel: [    0.808092] pci_bus 0000:02: resource 0 [io  0x5000-0x5fff]
Dec 24 10:28:39 laptop kernel: [    0.808094] pci_bus 0000:02: resource 1 [mem 0xda100000-0xdb0fffff]
Dec 24 10:28:39 laptop kernel: [    0.808097] pci_bus 0000:02: resource 2 [mem 0xd3100000-0xd40fffff 64bit pref]
Dec 24 10:28:39 laptop kernel: [    0.808099] pci_bus 0000:03: resource 0 [io  0x4000-0x4fff]
Dec 24 10:28:39 laptop kernel: [    0.808101] pci_bus 0000:03: resource 1 [mem 0xd9100000-0xda0fffff]
Dec 24 10:28:39 laptop kernel: [    0.808104] pci_bus 0000:03: resource 2 [mem 0xd4100000-0xd50fffff 64bit pref]
Dec 24 10:28:39 laptop kernel: [    0.808106] pci_bus 0000:04: resource 0 [io  0x3000-0x3fff]
Dec 24 10:28:39 laptop kernel: [    0.808108] pci_bus 0000:04: resource 1 [mem 0xd8100000-0xd90fffff]
Dec 24 10:28:39 laptop kernel: [    0.808111] pci_bus 0000:04: resource 2 [mem 0xd5100000-0xd60fffff 64bit pref]
Dec 24 10:28:39 laptop kernel: [    0.808113] pci_bus 0000:05: resource 0 [io  0x2000-0x2fff]
Dec 24 10:28:39 laptop kernel: [    0.808116] pci_bus 0000:05: resource 1 [mem 0xd7100000-0xd80fffff]
Dec 24 10:28:39 laptop kernel: [    0.808118] pci_bus 0000:05: resource 2 [mem 0xd6100000-0xd70fffff 64bit pref]
Dec 24 10:28:39 laptop kernel: [    0.808120] pci_bus 0000:09: resource 4 [io  0x0000-0x0cf7]
Dec 24 10:28:39 laptop kernel: [    0.808123] pci_bus 0000:09: resource 5 [io  0x0d00-0xffff]
Dec 24 10:28:39 laptop kernel: [    0.808125] pci_bus 0000:09: resource 6 [mem 0x000a0000-0x000bffff]
Dec 24 10:28:39 laptop kernel: [    0.808127] pci_bus 0000:09: resource 7 [mem 0xc0000000-0xfeafffff]
Dec 24 10:28:39 laptop kernel: [    0.808171] NET: Registered protocol family 2
Dec 24 10:28:39 laptop kernel: [    0.808234] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
Dec 24 10:28:39 laptop kernel: [    0.808426] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
Dec 24 10:28:39 laptop kernel: [    0.809117] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
Dec 24 10:28:39 laptop kernel: [    0.809462] TCP: Hash tables configured (established 131072 bind 65536)
Dec 24 10:28:39 laptop kernel: [    0.809464] TCP reno registered
Dec 24 10:28:39 laptop kernel: [    0.809467] UDP hash table entries: 512 (order: 2, 16384 bytes)
Dec 24 10:28:39 laptop kernel: [    0.809477] UDP-Lite hash table entries: 512 (order: 2, 16384 bytes)
Dec 24 10:28:39 laptop kernel: [    0.809571] NET: Registered protocol family 1
Dec 24 10:28:39 laptop kernel: [    0.837378] Freeing initrd memory: 13328k freed
Dec 24 10:28:39 laptop kernel: [    0.839154] pci 0000:01:00.0: Boot video device
Dec 24 10:28:39 laptop kernel: [    0.839201] PCI: CLS 64 bytes, default 64
Dec 24 10:28:39 laptop kernel: [    0.839208] Simple Boot Flag at 0x44 set to 0x1
Dec 24 10:28:39 laptop kernel: [    0.839747] audit: initializing netlink socket (disabled)
Dec 24 10:28:39 laptop kernel: [    0.839761] type=2000 audit(1324718901.656:1): initialized
Dec 24 10:28:39 laptop kernel: [    0.867899] highmem bounce pool size: 64 pages
Dec 24 10:28:39 laptop kernel: [    0.867906] HugeTLB registered 2 MB page size, pre-allocated 0 pages
Dec 24 10:28:39 laptop kernel: [    0.878845] VFS: Disk quotas dquot_6.5.2
Dec 24 10:28:39 laptop kernel: [    0.878919] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
Dec 24 10:28:39 laptop kernel: [    0.879633] fuse init (API version 7.16)
Dec 24 10:28:39 laptop kernel: [    0.879725] msgmni has been set to 1642
Dec 24 10:28:39 laptop kernel: [    0.880145] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
Dec 24 10:28:39 laptop kernel: [    0.880179] io scheduler noop registered
Dec 24 10:28:39 laptop kernel: [    0.880181] io scheduler deadline registered
Dec 24 10:28:39 laptop kernel: [    0.880197] io scheduler cfq registered (default)
Dec 24 10:28:39 laptop kernel: [    0.880323] pcieport 0000:00:01.0: setting latency timer to 64
Dec 24 10:28:39 laptop kernel: [    0.880356] pcieport 0000:00:01.0: irq 40 for MSI/MSI-X
Dec 24 10:28:39 laptop kernel: [    0.880637] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Dec 24 10:28:39 laptop kernel: [    0.880660] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
Dec 24 10:28:39 laptop kernel: [    0.880714] intel_idle: MWAIT substates: 0x1120
Dec 24 10:28:39 laptop kernel: [    0.880716] intel_idle: v0.4 model 0x25
Dec 24 10:28:39 laptop kernel: [    0.880717] intel_idle: lapic_timer_reliable_states 0xffffffff
Dec 24 10:28:39 laptop kernel: [    0.881118] ACPI: Deprecated procfs I/F for AC is loaded, please retry with CONFIG_ACPI_PROCFS_POWER cleared
Dec 24 10:28:39 laptop kernel: [    0.881473] ACPI: AC Adapter [ACAD] (on-line)
Dec 24 10:28:39 laptop kernel: [    0.881566] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0
Dec 24 10:28:39 laptop kernel: [    0.881572] ACPI: Power Button [PWRB]
Dec 24 10:28:39 laptop kernel: [    0.881611] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input1
Dec 24 10:28:39 laptop kernel: [    0.882137] ACPI: Lid Switch [LID0]
Dec 24 10:28:39 laptop kernel: [    0.882195] input: Sleep Button as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input2
Dec 24 10:28:39 laptop kernel: [    0.882199] ACPI: Sleep Button [SLPB]
Dec 24 10:28:39 laptop kernel: [    0.882244] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input3
Dec 24 10:28:39 laptop kernel: [    0.882247] ACPI: Power Button [PWRF]
Dec 24 10:28:39 laptop kernel: [    0.882274] ACPI: acpi_idle yielding to intel_idle
Dec 24 10:28:39 laptop kernel: [    0.885351] [Firmware Bug]: Invalid critical threshold (0)
Dec 24 10:28:39 laptop kernel: [    0.887074] thermal LNXTHERM:00: registered as thermal_zone0
Dec 24 10:28:39 laptop kernel: [    0.887077] ACPI: Thermal Zone [TZ01] (42 C)
Dec 24 10:28:39 laptop kernel: [    0.887095] ACPI: Deprecated procfs I/F for battery is loaded, please retry with CONFIG_ACPI_PROCFS_POWER cleared
Dec 24 10:28:39 laptop kernel: [    0.887121] ERST: Table is not found!
Dec 24 10:28:39 laptop kernel: [    0.887195] isapnp: Scanning for PnP cards...
Dec 24 10:28:39 laptop kernel: [    0.887209] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
Dec 24 10:28:39 laptop kernel: [    0.903131] ACPI: Battery Slot [BAT0] (battery present)
Dec 24 10:28:39 laptop kernel: [    1.241282] isapnp: No Plug & Play device found
Dec 24 10:28:39 laptop kernel: [    1.295341] Linux agpgart interface v0.103
Dec 24 10:28:39 laptop kernel: [    1.296617] brd: module loaded
Dec 24 10:28:39 laptop kernel: [    1.297166] loop: module loaded
Dec 24 10:28:39 laptop kernel: [    1.297602] Fixed MDIO Bus: probed
Dec 24 10:28:39 laptop kernel: [    1.297625] PPP generic driver version 2.4.2
Dec 24 10:28:39 laptop kernel: [    1.297657] tun: Universal TUN/TAP device driver, 1.6
Dec 24 10:28:39 laptop kernel: [    1.297659] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
Dec 24 10:28:39 laptop kernel: [    1.297730] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
Dec 24 10:28:39 laptop kernel: [    1.297748] ehci_hcd 0000:00:1a.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Dec 24 10:28:39 laptop kernel: [    1.297763] ehci_hcd 0000:00:1a.0: setting latency timer to 64
Dec 24 10:28:39 laptop kernel: [    1.297767] ehci_hcd 0000:00:1a.0: EHCI Host Controller
Dec 24 10:28:39 laptop kernel: [    1.297800] ehci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 1
Dec 24 10:28:39 laptop kernel: [    1.297831] ehci_hcd 0000:00:1a.0: debug port 2
Dec 24 10:28:39 laptop kernel: [    1.301733] ehci_hcd 0000:00:1a.0: cache line size of 64 is not supported
Dec 24 10:28:39 laptop kernel: [    1.301753] ehci_hcd 0000:00:1a.0: irq 16, io mem 0xdb105c00
Dec 24 10:28:39 laptop kernel: [    1.314888] ehci_hcd 0000:00:1a.0: USB 2.0 started, EHCI 1.00
Dec 24 10:28:39 laptop kernel: [    1.315044] hub 1-0:1.0: USB hub found
Dec 24 10:28:39 laptop kernel: [    1.315049] hub 1-0:1.0: 3 ports detected
Dec 24 10:28:39 laptop kernel: [    1.315118] ehci_hcd 0000:00:1d.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
Dec 24 10:28:39 laptop kernel: [    1.315131] ehci_hcd 0000:00:1d.0: setting latency timer to 64
Dec 24 10:28:39 laptop kernel: [    1.315135] ehci_hcd 0000:00:1d.0: EHCI Host Controller
Dec 24 10:28:39 laptop kernel: [    1.315166] ehci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
Dec 24 10:28:39 laptop kernel: [    1.315193] ehci_hcd 0000:00:1d.0: debug port 2
Dec 24 10:28:39 laptop kernel: [    1.319087] ehci_hcd 0000:00:1d.0: cache line size of 64 is not supported
Dec 24 10:28:39 laptop kernel: [    1.319102] ehci_hcd 0000:00:1d.0: irq 21, io mem 0xdb105800
Dec 24 10:28:39 laptop kernel: [    1.334883] ehci_hcd 0000:00:1d.0: USB 2.0 started, EHCI 1.00
Dec 24 10:28:39 laptop kernel: [    1.335025] hub 2-0:1.0: USB hub found
Dec 24 10:28:39 laptop kernel: [    1.335029] hub 2-0:1.0: 3 ports detected
Dec 24 10:28:39 laptop kernel: [    1.335091] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
Dec 24 10:28:39 laptop kernel: [    1.335103] uhci_hcd: USB Universal Host Controller Interface driver
Dec 24 10:28:39 laptop kernel: [    1.335170] i8042: PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
Dec 24 10:28:39 laptop kernel: [    1.366863] serio: i8042 KBD port at 0x60,0x64 irq 1
Dec 24 10:28:39 laptop kernel: [    1.366870] serio: i8042 AUX port at 0x60,0x64 irq 12
Dec 24 10:28:39 laptop kernel: [    1.366975] mousedev: PS/2 mouse device common for all mice
Dec 24 10:28:39 laptop kernel: [    1.368807] rtc_cmos 00:07: RTC can wake from S4
Dec 24 10:28:39 laptop kernel: [    1.368908] rtc_cmos 00:07: rtc core: registered rtc_cmos as rtc0
Dec 24 10:28:39 laptop kernel: [    1.368939] rtc0: alarms up to one year, y3k, 242 bytes nvram, hpet irqs
Dec 24 10:28:39 laptop kernel: [    1.369010] device-mapper: uevent: version 1.0.3
Dec 24 10:28:39 laptop kernel: [    1.369082] device-mapper: ioctl: 4.20.0-ioctl (2011-02-02) initialised: dm-devel@redhat.com
Dec 24 10:28:39 laptop kernel: [    1.369109] EISA: Probing bus 0 at eisa.0
Dec 24 10:28:39 laptop kernel: [    1.369112] EISA: Cannot allocate resource for mainboard
Dec 24 10:28:39 laptop kernel: [    1.369114] Cannot allocate resource for EISA slot 1
Dec 24 10:28:39 laptop kernel: [    1.369115] Cannot allocate resource for EISA slot 2
Dec 24 10:28:39 laptop kernel: [    1.369117] Cannot allocate resource for EISA slot 3
Dec 24 10:28:39 laptop kernel: [    1.369119] Cannot allocate resource for EISA slot 4
Dec 24 10:28:39 laptop kernel: [    1.369120] Cannot allocate resource for EISA slot 5
Dec 24 10:28:39 laptop kernel: [    1.369122] Cannot allocate resource for EISA slot 6
Dec 24 10:28:39 laptop kernel: [    1.369124] Cannot allocate resource for EISA slot 7
Dec 24 10:28:39 laptop kernel: [    1.369125] Cannot allocate resource for EISA slot 8
Dec 24 10:28:39 laptop kernel: [    1.369127] EISA: Detected 0 cards.
Dec 24 10:28:39 laptop kernel: [    1.369136] cpufreq-nforce2: No nForce2 chipset.
Dec 24 10:28:39 laptop kernel: [    1.369234] cpuidle: using governor ladder
Dec 24 10:28:39 laptop kernel: [    1.369390] cpuidle: using governor menu
Dec 24 10:28:39 laptop kernel: [    1.369392] EFI Variables Facility v0.08 2004-May-17
Dec 24 10:28:39 laptop kernel: [    1.369633] TCP cubic registered
Dec 24 10:28:39 laptop kernel: [    1.369769] NET: Registered protocol family 10
Dec 24 10:28:39 laptop kernel: [    1.370280] NET: Registered protocol family 17
Dec 24 10:28:39 laptop kernel: [    1.370294] Registering the dns_resolver key type
Dec 24 10:28:39 laptop kernel: [    1.370315] Using IPI No-Shortcut mode
Dec 24 10:28:39 laptop kernel: [    1.370390] PM: Hibernation image not present or could not be loaded.
Dec 24 10:28:39 laptop kernel: [    1.370399] registered taskstats version 1
Dec 24 10:28:39 laptop kernel: [    1.383390]   Magic number: 7:719:475
Dec 24 10:28:39 laptop kernel: [    1.383550] rtc_cmos 00:07: setting system clock to 2011-12-24 09:28:23 UTC (1324718903)
Dec 24 10:28:39 laptop kernel: [    1.384676] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
Dec 24 10:28:39 laptop kernel: [    1.384678] EDD information not available.
Dec 24 10:28:39 laptop kernel: [    1.384909] Freeing unused kernel memory: 720k freed
Dec 24 10:28:39 laptop kernel: [    1.385142] Write protecting the kernel text: 5500k
Dec 24 10:28:39 laptop kernel: [    1.385221] Write protecting the kernel read-only data: 2240k
Dec 24 10:28:39 laptop kernel: [    1.385222] NX-protecting the kernel data: 4740k
Dec 24 10:28:39 laptop kernel: [    1.389100] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input4
Dec 24 10:28:39 laptop kernel: [    1.438498] ahci 0000:00:1f.2: version 3.0
Dec 24 10:28:39 laptop kernel: [    1.438531] ahci 0000:00:1f.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
Dec 24 10:28:39 laptop kernel: [    1.438605] ahci 0000:00:1f.2: irq 41 for MSI/MSI-X
Dec 24 10:28:39 laptop kernel: [    1.438710] ahci 0000:00:1f.2: AHCI 0001.0300 32 slots 6 ports 3 Gbps 0x33 impl SATA mode
Dec 24 10:28:39 laptop kernel: [    1.438715] ahci 0000:00:1f.2: flags: 64bit ncq sntf ilck pm led clo pio slum part ems sxs apst 
Dec 24 10:28:39 laptop kernel: [    1.438723] ahci 0000:00:1f.2: setting latency timer to 64
Dec 24 10:28:39 laptop kernel: [    1.445456] sdhci: Secure Digital Host Controller Interface driver
Dec 24 10:28:39 laptop kernel: [    1.445460] sdhci: Copyright(c) Pierre Ossman
Dec 24 10:28:39 laptop kernel: [    1.445717] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
Dec 24 10:28:39 laptop kernel: [    1.445742] r8169 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
Dec 24 10:28:39 laptop kernel: [    1.445794] r8169 0000:03:00.0: setting latency timer to 64
Dec 24 10:28:39 laptop kernel: [    1.445834] sdhci-pci 0000:04:00.1: SDHCI controller found [197b:2382] (rev 0)
Dec 24 10:28:39 laptop kernel: [    1.445856] sdhci-pci 0000:04:00.1: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Dec 24 10:28:39 laptop kernel: [    1.445878] r8169 0000:03:00.0: irq 42 for MSI/MSI-X
Dec 24 10:28:39 laptop kernel: [    1.445917] sdhci-pci 0000:04:00.1: setting latency timer to 64
Dec 24 10:28:39 laptop kernel: [    1.445931] mmc0: no vmmc regulator found
Dec 24 10:28:39 laptop kernel: [    1.445965] Registered led device: mmc0::
Dec 24 10:28:39 laptop kernel: [    1.449409] mmc0: SDHCI controller on PCI [0000:04:00.1] using DMA
Dec 24 10:28:39 laptop kernel: [    1.449460] firewire_ohci 0000:04:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Dec 24 10:28:39 laptop kernel: [    1.449471] firewire_ohci 0000:04:00.0: setting latency timer to 64
Dec 24 10:28:39 laptop kernel: [    1.455410] r8169 0000:03:00.0: eth0: RTL8168d/8111d at 0xf842e000, 00:26:9e:e9:6a:94, XID 083000c0 IRQ 42
Dec 24 10:28:39 laptop kernel: [    1.464400] scsi0 : ahci
Dec 24 10:28:39 laptop kernel: [    1.465808] scsi1 : ahci
Dec 24 10:28:39 laptop kernel: [    1.466689] scsi2 : ahci
Dec 24 10:28:39 laptop kernel: [    1.466795] scsi3 : ahci
Dec 24 10:28:39 laptop kernel: [    1.466914] scsi4 : ahci
Dec 24 10:28:39 laptop kernel: [    1.467009] scsi5 : ahci
Dec 24 10:28:39 laptop kernel: [    1.467078] ata1: SATA max UDMA/133 abar m2048@0xdb105000 port 0xdb105100 irq 41
Dec 24 10:28:39 laptop kernel: [    1.467084] ata2: SATA max UDMA/133 abar m2048@0xdb105000 port 0xdb105180 irq 41
Dec 24 10:28:39 laptop kernel: [    1.467087] ata3: DUMMY
Dec 24 10:28:39 laptop kernel: [    1.467088] ata4: DUMMY
Dec 24 10:28:39 laptop kernel: [    1.467092] ata5: SATA max UDMA/133 abar m2048@0xdb105000 port 0xdb105300 irq 41
Dec 24 10:28:39 laptop kernel: [    1.467097] ata6: SATA max UDMA/133 abar m2048@0xdb105000 port 0xdb105380 irq 41
Dec 24 10:28:39 laptop kernel: [    1.515041] firewire_ohci: Added fw-ohci device 0000:04:00.0, OHCI v1.10, 4 IR + 0 IT contexts, quirks 0x10
Dec 24 10:28:39 laptop kernel: [    1.515127] sdhci-pci 0000:04:00.2: SDHCI controller found [197b:2381] (rev 0)
Dec 24 10:28:39 laptop kernel: [    1.515213] sdhci-pci 0000:04:00.2: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Dec 24 10:28:39 laptop kernel: [    1.515228] sdhci-pci 0000:04:00.2: Refusing to bind to secondary interface.
Dec 24 10:28:39 laptop kernel: [    1.515242] sdhci-pci 0000:04:00.2: PCI INT A disabled
Dec 24 10:28:39 laptop kernel: [    1.626828] usb 1-1: new high speed USB device number 2 using ehci_hcd
Dec 24 10:28:39 laptop kernel: [    1.759653] hub 1-1:1.0: USB hub found
Dec 24 10:28:39 laptop kernel: [    1.759811] hub 1-1:1.0: 6 ports detected
Dec 24 10:28:39 laptop kernel: [    1.786795] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
Dec 24 10:28:39 laptop kernel: [    1.786833] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
Dec 24 10:28:39 laptop kernel: [    1.787744] ata1.00: ATA-8: Hitachi HTS725050A9A364, PC4OC70E, max UDMA/100
Dec 24 10:28:39 laptop kernel: [    1.787749] ata1.00: 976773168 sectors, multi 16: LBA48 NCQ (depth 31/32), AA
Dec 24 10:28:39 laptop kernel: [    1.788889] ata1.00: configured for UDMA/100
Dec 24 10:28:39 laptop kernel: [    1.789149] scsi 0:0:0:0: Direct-Access     ATA      Hitachi HTS72505 PC4O PQ: 0 ANSI: 5
Dec 24 10:28:39 laptop kernel: [    1.789401] sd 0:0:0:0: [sda] 976773168 512-byte logical blocks: (500 GB/465 GiB)
Dec 24 10:28:39 laptop kernel: [    1.789422] sd 0:0:0:0: Attached scsi generic sg0 type 0
Dec 24 10:28:39 laptop kernel: [    1.789467] sd 0:0:0:0: [sda] Write Protect is off
Dec 24 10:28:39 laptop kernel: [    1.789470] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
Dec 24 10:28:39 laptop kernel: [    1.789501] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Dec 24 10:28:39 laptop kernel: [    1.790770] ata5: SATA link down (SStatus 0 SControl 300)
Dec 24 10:28:39 laptop kernel: [    1.790809] ata6: SATA link down (SStatus 0 SControl 300)
Dec 24 10:28:39 laptop kernel: [    1.801452] ata2.00: ATAPI: hp      DVD RW AD-7561S, AH73, max UDMA/100
Dec 24 10:28:39 laptop kernel: [    1.817918] ata2.00: configured for UDMA/100
Dec 24 10:28:39 laptop kernel: [    1.821314] scsi 1:0:0:0: CD-ROM            hp       DVD RW AD-7561S  AH73 PQ: 0 ANSI: 5
Dec 24 10:28:39 laptop kernel: [    1.828378] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
Dec 24 10:28:39 laptop kernel: [    1.828383] cdrom: Uniform CD-ROM driver Revision: 3.20
Dec 24 10:28:39 laptop kernel: [    1.828549] sr 1:0:0:0: Attached scsi CD-ROM sr0
Dec 24 10:28:39 laptop kernel: [    1.828619] sr 1:0:0:0: Attached scsi generic sg1 type 5
Dec 24 10:28:39 laptop kernel: [    1.838799] Refined TSC clocksource calibration: 2127.999 MHz.
Dec 24 10:28:39 laptop kernel: [    1.838807] Switching to clocksource tsc
Dec 24 10:28:39 laptop kernel: [    1.845987]  sda: sda1 sda2 < sda5 sda6 sda7 >
Dec 24 10:28:39 laptop kernel: [    1.846370] sd 0:0:0:0: [sda] Attached SCSI disk
Dec 24 10:28:39 laptop kernel: [    1.870760] usb 2-1: new high speed USB device number 2 using ehci_hcd
Dec 24 10:28:39 laptop kernel: [    2.003727] hub 2-1:1.0: USB hub found
Dec 24 10:28:39 laptop kernel: [    2.003812] hub 2-1:1.0: 8 ports detected
Dec 24 10:28:39 laptop kernel: [    2.014739] firewire_core: created device fw0: GUID 00241b00ce59bc01, S400
Dec 24 10:28:39 laptop kernel: [    2.074632] usb 1-1.4: new high speed USB device number 3 using ehci_hcd
Dec 24 10:28:39 laptop kernel: [    2.196812] EXT4-fs (sda1): INFO: recovery required on readonly filesystem
Dec 24 10:28:39 laptop kernel: [    2.196816] EXT4-fs (sda1): write access will be enabled during recovery
Dec 24 10:28:39 laptop kernel: [    2.278713] usb 2-1.3: new full speed USB device number 3 using ehci_hcd
Dec 24 10:28:39 laptop kernel: [    2.442516] usb 2-1.5: new high speed USB device number 4 using ehci_hcd
Dec 24 10:28:39 laptop kernel: [    3.040130] EXT4-fs (sda1): orphan cleanup on readonly fs
Dec 24 10:28:39 laptop kernel: [    3.040140] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 1177430
Dec 24 10:28:39 laptop kernel: [    3.040165] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 1177427
Dec 24 10:28:39 laptop kernel: [    3.040171] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 1177426
Dec 24 10:28:39 laptop kernel: [    3.040177] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 1177425
Dec 24 10:28:39 laptop kernel: [    3.040184] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 1177424
Dec 24 10:28:39 laptop kernel: [    3.040190] EXT4-fs (sda1): 5 orphan inodes deleted
Dec 24 10:28:39 laptop kernel: [    3.040192] EXT4-fs (sda1): recovery complete
Dec 24 10:28:39 laptop kernel: [    3.263771] EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: (null)
Dec 24 10:28:39 laptop kernel: [   15.307920] lp: driver loaded but no devices found
Dec 24 10:28:39 laptop kernel: [   15.339792] acpi device:11: registered as cooling_device4
Dec 24 10:28:39 laptop kernel: [   15.339858] cfg80211: Calling CRDA to update world regulatory domain
Dec 24 10:28:39 laptop kernel: [   15.342917] wmi: Mapper loaded
Dec 24 10:28:39 laptop kernel: [   15.346848] Adding 10971132k swap on /dev/sda5.  Priority:-1 extents:1 across:10971132k 
Dec 24 10:28:39 laptop kernel: [   15.349805] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:0e/LNXVIDEO:02/input/input5
Dec 24 10:28:39 laptop kernel: [   15.349892] ACPI: Video Device [VGA1] (multi-head: yes  rom: no  post: no)
Dec 24 10:28:39 laptop kernel: [   15.364989] jmb38x_ms 0000:04:00.3: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Dec 24 10:28:39 laptop kernel: [   15.365001] jmb38x_ms 0000:04:00.3: setting latency timer to 64
Dec 24 10:28:39 laptop kernel: [   15.375361] [drm] Initialized drm 1.1.0 20060810
Dec 24 10:28:39 laptop kernel: [   15.382580] hp_accel: hardware type DV7 found
Dec 24 10:28:39 laptop kernel: [   15.387800] lis3lv02d: 8 bits sensor found
Dec 24 10:28:39 laptop kernel: [   15.393018] type=1400 audit(1324718917.514:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=510 comm="apparmor_parser"
Dec 24 10:28:39 laptop kernel: [   15.393654] type=1400 audit(1324718917.514:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=510 comm="apparmor_parser"
Dec 24 10:28:39 laptop kernel: [   15.394062] type=1400 audit(1324718917.514:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=510 comm="apparmor_parser"
Dec 24 10:28:39 laptop kernel: [   15.394582] nouveau 0000:01:00.0: power state changed by ACPI to D0
Dec 24 10:28:39 laptop kernel: [   15.394588] nouveau 0000:01:00.0: power state changed by ACPI to D0
Dec 24 10:28:39 laptop kernel: [   15.394599] nouveau 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Dec 24 10:28:39 laptop kernel: [   15.394605] nouveau 0000:01:00.0: setting latency timer to 64
Dec 24 10:28:39 laptop kernel: [   15.397696] [drm] nouveau 0000:01:00.0: Detected an NV50 generation card (0x0a8400a2)
Dec 24 10:28:39 laptop kernel: [   15.405882] [drm] nouveau 0000:01:00.0: Attempting to load BIOS image from PRAMIN
Dec 24 10:28:39 laptop kernel: [   15.411230] ene_ir: chip is 0x3926 - kbver = 0x00, rev = 0xd2
Dec 24 10:28:39 laptop kernel: [   15.411233] ene_ir: PLL freq = 1406
Dec 24 10:28:39 laptop kernel: [   15.411235] ene_ir: KB3926D or higher detected
Dec 24 10:28:39 laptop kernel: [   15.411259] ene_ir: Firmware regs: c0 01
Dec 24 10:28:39 laptop kernel: [   15.411260] ene_ir: Hardware features:
Dec 24 10:28:39 laptop kernel: [   15.411262] ene_ir: * Uses GPIO 40 for IR demodulated input
Dec 24 10:28:39 laptop kernel: [   15.416236] IR NEC protocol handler initialized
Dec 24 10:28:39 laptop kernel: [   15.421108] IR RC5(x) protocol handler initialized
Dec 24 10:28:39 laptop kernel: [   15.424297] IR RC6 protocol handler initialized
Dec 24 10:28:39 laptop kernel: [   15.429802] IR JVC protocol handler initialized
Dec 24 10:28:39 laptop kernel: [   15.435956] IR Sony protocol handler initialized
Dec 24 10:28:39 laptop kernel: [   15.436921] Registered IR keymap rc-rc6-mce
Dec 24 10:28:39 laptop kernel: [   15.437028] input: ST LIS3LV02DL Accelerometer as /devices/platform/lis3lv02d/input/input7
Dec 24 10:28:39 laptop kernel: [   15.437036] input: ENE eHome Infrared Remote Receiver as /devices/virtual/rc/rc0/input6
Dec 24 10:28:39 laptop kernel: [   15.437206] rc0: ENE eHome Infrared Remote Receiver as /devices/virtual/rc/rc0
Dec 24 10:28:39 laptop kernel: [   15.437236] Registered led device: hp::hddprotect
Dec 24 10:28:39 laptop kernel: [   15.437257] hp_accel: driver loaded
Dec 24 10:28:39 laptop kernel: [   15.437308] ene_ir: driver has been successfully loaded
Dec 24 10:28:39 laptop kernel: [   15.439505] lirc_dev: IR Remote Control driver registered, major 250 
Dec 24 10:28:39 laptop kernel: [   15.439794] rc rc0: lirc_dev: driver ir-lirc-codec (ene_ir) registered at minor = 0
Dec 24 10:28:39 laptop kernel: [   15.439797] IR LIRC bridge handler initialized
Dec 24 10:28:39 laptop kernel: [   15.466078] Linux video capture interface: v2.00
Dec 24 10:28:39 laptop kernel: [   15.466850] uvcvideo: Found UVC 1.00 device HP Webcam (5986:0143)
Dec 24 10:28:39 laptop kernel: [   15.470252] brcmutil: module is from the staging directory, the quality is unknown, you have been warned.
Dec 24 10:28:39 laptop kernel: [   15.473086] input: HP Webcam as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.5/2-1.5:1.0/input/input8
Dec 24 10:28:39 laptop kernel: [   15.473190] usbcore: registered new interface driver uvcvideo
Dec 24 10:28:39 laptop kernel: [   15.473194] USB Video Class driver (v1.1.0)
Dec 24 10:28:39 laptop kernel: [   15.474241] brcmsmac: module is from the staging directory, the quality is unknown, you have been warned.
Dec 24 10:28:39 laptop kernel: [   15.479305] brcmsmac 0000:02:00.0: bus 2 slot 0 func 0 irq 5
Dec 24 10:28:39 laptop kernel: [   15.479325] brcmsmac 0000:02:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Dec 24 10:28:39 laptop kernel: [   15.479335] brcmsmac 0000:02:00.0: setting latency timer to 64
Dec 24 10:28:39 laptop kernel: [   15.488031] [drm] nouveau 0000:01:00.0: ... appears to be valid
Dec 24 10:28:39 laptop kernel: [   15.488038] [drm] nouveau 0000:01:00.0: BIT BIOS found
Dec 24 10:28:39 laptop kernel: [   15.488042] [drm] nouveau 0000:01:00.0: Bios version 70.18.1f.00
Dec 24 10:28:39 laptop kernel: [   15.488045] [drm] nouveau 0000:01:00.0: Pointer to BIT loadval table invalid
Dec 24 10:28:39 laptop kernel: [   15.488051] [drm] nouveau 0000:01:00.0: TMDS table version 2.0
Dec 24 10:28:39 laptop kernel: [   15.488054] [drm] nouveau 0000:01:00.0: Found Display Configuration Block version 4.0
Dec 24 10:28:39 laptop kernel: [   15.488059] [drm] nouveau 0000:01:00.0: Raw DCB entry 0: 01000323 00010034
Dec 24 10:28:39 laptop kernel: [   15.488063] [drm] nouveau 0000:01:00.0: Raw DCB entry 1: 02014300 00000000
Dec 24 10:28:39 laptop kernel: [   15.488067] [drm] nouveau 0000:01:00.0: Raw DCB entry 2: 02021362 00020010
Dec 24 10:28:39 laptop kernel: [   15.488070] [drm] nouveau 0000:01:00.0: Raw DCB entry 3: 0000000e 00000000
Dec 24 10:28:39 laptop kernel: [   15.488075] [drm] nouveau 0000:01:00.0: DCB connector table: VHER 0x40 5 16 4
Dec 24 10:28:39 laptop kernel: [   15.488079] [drm] nouveau 0000:01:00.0:   0: 0x00000340: type 0x40 idx 0 tag 0xff
Dec 24 10:28:39 laptop kernel: [   15.488082] [drm] nouveau 0000:01:00.0:   1: 0x00001061: type 0x61 idx 1 tag 0x07
Dec 24 10:28:39 laptop kernel: [   15.488086] [drm] nouveau 0000:01:00.0:   2: 0x00000147: type 0x47 idx 2 tag 0xff
Dec 24 10:28:39 laptop kernel: [   15.488089] [drm] nouveau 0000:01:00.0:   3: 0x00002131: type 0x31 idx 3 tag 0x08
Dec 24 10:28:39 laptop kernel: [   15.488093] [drm] nouveau 0000:01:00.0:   4: 0x00000400: type 0x00 idx 4 tag 0xff
Dec 24 10:28:39 laptop kernel: [   15.488097] [drm] nouveau 0000:01:00.0:   5: 0x00000210: type 0x10 idx 5 tag 0xff
Dec 24 10:28:39 laptop kernel: [   15.488100] [drm] nouveau 0000:01:00.0:   6: 0x00000211: type 0x11 idx 6 tag 0xff
Dec 24 10:28:39 laptop kernel: [   15.488103] [drm] nouveau 0000:01:00.0:   7: 0x00000213: type 0x13 idx 7 tag 0xff
Dec 24 10:28:39 laptop kernel: [   15.488109] [drm] nouveau 0000:01:00.0: Parsing VBIOS init table 0 at offset 0xD359
Dec 24 10:28:39 laptop kernel: [   15.522165] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
Dec 24 10:28:39 laptop kernel: [   15.522235] HDA Intel 0000:00:1b.0: irq 43 for MSI/MSI-X
Dec 24 10:28:39 laptop kernel: [   15.522269] HDA Intel 0000:00:1b.0: setting latency timer to 64
Dec 24 10:28:39 laptop kernel: [   15.528240] [drm] nouveau 0000:01:00.0: 0xD6AF: Condition still not met after 20ms, skipping following opcodes
Dec 24 10:28:39 laptop kernel: [   15.548090] [drm] nouveau 0000:01:00.0: 0xD6B3: Condition still not met after 20ms, skipping following opcodes
Dec 24 10:28:39 laptop kernel: [   15.567965] [drm] nouveau 0000:01:00.0: 0xD859: Condition still not met after 20ms, skipping following opcodes
Dec 24 10:28:39 laptop kernel: [   15.567977] [drm] nouveau 0000:01:00.0: Parsing VBIOS init table 1 at offset 0xD8A4
Dec 24 10:28:39 laptop kernel: [   15.575706] [drm] nouveau 0000:01:00.0: Parsing VBIOS init table 2 at offset 0xE3D3
Dec 24 10:28:39 laptop kernel: [   15.575719] [drm] nouveau 0000:01:00.0: Parsing VBIOS init table 3 at offset 0xE408
Dec 24 10:28:39 laptop kernel: [   15.618242] [drm] nouveau 0000:01:00.0: Parsing VBIOS init table 4 at offset 0xE59C
Dec 24 10:28:39 laptop kernel: [   15.618246] [drm] nouveau 0000:01:00.0: Parsing VBIOS init table at offset 0xE601
Dec 24 10:28:39 laptop kernel: [   15.625136] input: HDA Intel Mic at Ext Front Jack as /devices/pci0000:00/0000:00:1b.0/sound/card0/input9
Dec 24 10:28:39 laptop kernel: [   15.625241] input: HDA Intel Line Out at Ext Front Jack as /devices/pci0000:00/0000:00:1b.0/sound/card0/input10
Dec 24 10:28:39 laptop kernel: [   15.638093] [drm] nouveau 0000:01:00.0: 0xE601: Condition still not met after 20ms, skipping following opcodes
Dec 24 10:28:39 laptop kernel: [   15.667205] input: HP WMI hotkeys as /devices/virtual/input/input11
Dec 24 10:28:39 laptop kernel: [   15.667355] [drm] nouveau 0000:01:00.0: 3 available performance level(s)
Dec 24 10:28:39 laptop kernel: [   15.667363] [drm] nouveau 0000:01:00.0: 0: memory 135MHz core 135MHz shader 270MHz voltage 800mV timing 2
Dec 24 10:28:39 laptop kernel: [   15.667369] [drm] nouveau 0000:01:00.0: 1: memory 405MHz core 405MHz shader 810MHz voltage 850mV timing 1
Dec 24 10:28:39 laptop kernel: [   15.667376] [drm] nouveau 0000:01:00.0: 3: memory 790MHz core 535MHz shader 1230MHz voltage 900mV timing 0
Dec 24 10:28:39 laptop kernel: [   15.667400] [drm] nouveau 0000:01:00.0: c: memory 405MHz core 405MHz shader 810MHz voltage 900mV
Dec 24 10:28:39 laptop kernel: [   15.670742] [TTM] Zone  kernel: Available graphics memory: 420922 kiB.
Dec 24 10:28:39 laptop kernel: [   15.670746] [TTM] Zone highmem: Available graphics memory: 2024130 kiB.
Dec 24 10:28:39 laptop kernel: [   15.670749] [TTM] Initializing pool allocator.
Dec 24 10:28:39 laptop kernel: [   15.670769] [drm] nouveau 0000:01:00.0: Detected 512MiB VRAM
Dec 24 10:28:39 laptop kernel: [   15.676747] [drm] nouveau 0000:01:00.0: 512 MiB GART (aperture)
Dec 24 10:28:39 laptop kernel: [   15.708746] cfg80211: World regulatory domain updated:
Dec 24 10:28:39 laptop kernel: [   15.708751] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
Dec 24 10:28:39 laptop kernel: [   15.708755] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Dec 24 10:28:39 laptop kernel: [   15.708759] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Dec 24 10:28:39 laptop kernel: [   15.708763] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Dec 24 10:28:39 laptop kernel: [   15.708767] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Dec 24 10:28:39 laptop kernel: [   15.708770] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Dec 24 10:28:39 laptop kernel: [   15.731380] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
Dec 24 10:28:39 laptop kernel: [   15.731384] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
Dec 24 10:28:39 laptop kernel: [   15.731387] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
Dec 24 10:28:39 laptop kernel: [   15.731390] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
Dec 24 10:28:39 laptop kernel: [   15.731392] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
Dec 24 10:28:39 laptop kernel: [   15.731395] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
Dec 24 10:28:39 laptop kernel: [   15.731397] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
Dec 24 10:28:39 laptop kernel: [   15.731400] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
Dec 24 10:28:39 laptop kernel: [   15.731402] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
Dec 24 10:28:39 laptop kernel: [   15.731405] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
Dec 24 10:28:39 laptop kernel: [   15.731407] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
Dec 24 10:28:39 laptop kernel: [   15.731410] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
Dec 24 10:28:39 laptop kernel: [   15.731412] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
Dec 24 10:28:39 laptop kernel: [   15.731415] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
Dec 24 10:28:39 laptop kernel: [   15.731417] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
Dec 24 10:28:39 laptop kernel: [   15.731420] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
Dec 24 10:28:39 laptop kernel: [   15.731422] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
Dec 24 10:28:39 laptop kernel: [   15.731425] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
Dec 24 10:28:39 laptop kernel: [   15.731427] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
Dec 24 10:28:39 laptop kernel: [   15.731430] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
Dec 24 10:28:39 laptop kernel: [   15.731432] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
Dec 24 10:28:39 laptop kernel: [   15.731435] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
Dec 24 10:28:39 laptop kernel: [   15.731438] cfg80211: Updating information on frequency 2467 MHz for a 20 MHz width channel with regulatory rule:
Dec 24 10:28:39 laptop kernel: [   15.731440] cfg80211: 2457000 KHz - 2482000 KHz @  KHz), (300 mBi, 2000 mBm)
Dec 24 10:28:39 laptop kernel: [   15.731443] cfg80211: Updating information on frequency 2472 MHz for a 20 MHz width channel with regulatory rule:
Dec 24 10:28:39 laptop kernel: [   15.731445] cfg80211: 2457000 KHz - 2482000 KHz @  KHz), (300 mBi, 2000 mBm)
Dec 24 10:28:39 laptop kernel: [   15.731448] cfg80211: Updating information on frequency 2484 MHz for a 20 MHz width channel with regulatory rule:
Dec 24 10:28:39 laptop kernel: [   15.731450] cfg80211: 2474000 KHz - 2494000 KHz @  KHz), (300 mBi, 2000 mBm)
Dec 24 10:28:39 laptop kernel: [   15.733966] ieee80211 phy0: Selected rate control algorithm 'minstrel_ht'
Dec 24 10:28:39 laptop kernel: [   15.735136] lib80211: common routines for IEEE802.11 drivers
Dec 24 10:28:39 laptop kernel: [   15.735139] lib80211_crypt: registered algorithm 'NULL'
Dec 24 10:28:39 laptop kernel: [   15.736799] cfg80211: Calling CRDA for country: US
Dec 24 10:28:39 laptop kernel: [   15.737410] wl: module license 'MIXED/Proprietary' taints kernel.
Dec 24 10:28:39 laptop kernel: [   15.737413] Disabling lock debugging due to kernel taint
Dec 24 10:28:39 laptop kernel: [   15.740635] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
Dec 24 10:28:39 laptop kernel: [   15.740640] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2700 mBm)
Dec 24 10:28:39 laptop kernel: [   15.740642] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
Dec 24 10:28:39 laptop kernel: [   15.740645] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2700 mBm)
Dec 24 10:28:39 laptop kernel: [   15.740647] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
Dec 24 10:28:39 laptop kernel: [   15.740649] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2700 mBm)
Dec 24 10:28:39 laptop kernel: [   15.740651] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
Dec 24 10:28:39 laptop kernel: [   15.740654] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2700 mBm)
Dec 24 10:28:39 laptop kernel: [   15.740656] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
Dec 24 10:28:39 laptop kernel: [   15.740659] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2700 mBm)
Dec 24 10:28:39 laptop kernel: [   15.740661] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
Dec 24 10:28:39 laptop kernel: [   15.740663] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2700 mBm)
Dec 24 10:28:39 laptop kernel: [   15.740665] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
Dec 24 10:28:39 laptop kernel: [   15.740668] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2700 mBm)
Dec 24 10:28:39 laptop kernel: [   15.740670] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
Dec 24 10:28:39 laptop kernel: [   15.740672] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2700 mBm)
Dec 24 10:28:39 laptop kernel: [   15.740674] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
Dec 24 10:28:39 laptop kernel: [   15.740677] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2700 mBm)
Dec 24 10:28:39 laptop kernel: [   15.740679] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
Dec 24 10:28:39 laptop kernel: [   15.740681] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2700 mBm)
Dec 24 10:28:39 laptop kernel: [   15.740683] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
Dec 24 10:28:39 laptop kernel: [   15.740686] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2700 mBm)
Dec 24 10:28:39 laptop kernel: [   15.740688] cfg80211: Disabling freq 2467 MHz
Dec 24 10:28:39 laptop kernel: [   15.740689] cfg80211: Disabling freq 2472 MHz
Dec 24 10:28:39 laptop kernel: [   15.740691] cfg80211: Disabling freq 2484 MHz
Dec 24 10:28:39 laptop kernel: [   15.740694] cfg80211: Regulatory domain changed to country: US
Dec 24 10:28:39 laptop kernel: [   15.740696] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
Dec 24 10:28:39 laptop kernel: [   15.740698] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
Dec 24 10:28:39 laptop kernel: [   15.740701] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 1700 mBm)
Dec 24 10:28:39 laptop kernel: [   15.740703] cfg80211:     (5250000 KHz - 5330000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Dec 24 10:28:39 laptop kernel: [   15.740705] cfg80211:     (5490000 KHz - 5600000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Dec 24 10:28:39 laptop kernel: [   15.740708] cfg80211:     (5650000 KHz - 5710000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Dec 24 10:28:39 laptop kernel: [   15.740710] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 3000 mBm)
Dec 24 10:28:39 laptop kernel: [   15.750282] [drm] nouveau 0000:01:00.0: ACPI backlight interface available, not registering our own
Dec 24 10:28:39 laptop kernel: [   15.752059] [drm] Supports vblank timestamp caching Rev 1 (10.10.2010).
Dec 24 10:28:39 laptop kernel: [   15.752062] [drm] No driver support for vblank timestamp query.
Dec 24 10:28:39 laptop kernel: [   15.816923] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
Dec 24 10:28:39 laptop kernel: [   15.923861] [drm] nouveau 0000:01:00.0: allocated 1600x900 fb: 0x40000000, bo ee78b400
Dec 24 10:28:39 laptop kernel: [   15.923970] fbcon: nouveaufb (fb0) is primary device
Dec 24 10:28:39 laptop kernel: [   15.924143] Console: switching to colour frame buffer device 200x56
Dec 24 10:28:39 laptop kernel: [   15.924202] fb0: nouveaufb frame buffer device
Dec 24 10:28:39 laptop kernel: [   15.924204] drm: registered panic notifier
Dec 24 10:28:39 laptop kernel: [   15.924212] [drm] Initialized nouveau 0.0.16 20090420 for 0000:01:00.0 on minor 0
Dec 24 10:28:39 laptop kernel: [   15.924257] HDA Intel 0000:01:00.1: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Dec 24 10:28:39 laptop kernel: [   15.924356] HDA Intel 0000:01:00.1: irq 44 for MSI/MSI-X
Dec 24 10:28:39 laptop kernel: [   15.924383] HDA Intel 0000:01:00.1: setting latency timer to 64
Dec 24 10:28:39 laptop kernel: [   16.011050] dvb-usb: found a 'AVerMedia A309' in cold state, will try to load a firmware
Dec 24 10:28:39 laptop kernel: [   16.012835] dvb-usb: did not find the firmware file. (dvb-usb-af9015.fw) Please see linux/Documentation/dvb/ for more details on firmware-problems. (-2)
Dec 24 10:28:39 laptop kernel: [   16.012850] dvb_usb_af9015: probe of 1-1.4:1.0 failed with error -2
Dec 24 10:28:39 laptop kernel: [   16.012878] usbcore: registered new interface driver dvb_usb_af9015
Dec 24 10:28:39 laptop kernel: [   16.296457] EXT4-fs (sda6): mounted filesystem with ordered data mode. Opts: user_xattr
Dec 24 10:28:39 laptop kernel: [   16.467492] Synaptics Touchpad, model: 1, fw: 6.5, id: 0x1c0b1, caps: 0xa04751/0xa00000/0x0
Dec 24 10:28:39 laptop kernel: [   16.549957] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input12
Dec 24 10:28:39 laptop kernel: [   17.333861] type=1400 audit(1324718919.454:5): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=924 comm="apparmor_parser"
Dec 24 10:28:39 laptop kernel: [   17.334254] type=1400 audit(1324718919.454:6): apparmor="STATUS" operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" pid=922 comm="apparmor_parser"
Dec 24 10:28:39 laptop kernel: [   17.339539] type=1400 audit(1324718919.458:7): apparmor="STATUS" operation="profile_load" name="/usr/lib/lightdm/lightdm-guest-session-wrapper" pid=923 comm="apparmor_parser"
Dec 24 10:28:39 laptop kernel: [   17.341500] type=1400 audit(1324718919.462:8): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=924 comm="apparmor_parser"
Dec 24 10:28:39 laptop kernel: [   17.341904] type=1400 audit(1324718919.462:9): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=924 comm="apparmor_parser"
Dec 24 10:28:39 laptop kernel: [   17.346308] type=1400 audit(1324718919.466:10): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince" pid=925 comm="apparmor_parser"
Dec 24 10:28:39 laptop kernel: [   17.346388] type=1400 audit(1324718919.466:11): apparmor="STATUS" operation="profile_load" name="/usr/sbin/mysqld" pid=932 comm="apparmor_parser"
Dec 24 10:28:39 laptop kernel: [   17.431437] ieee80211 phy0: wl_ops_config: change monitor mode: false (implement)
Dec 24 10:28:39 laptop kernel: [   17.431444] ieee80211 phy0: wl_ops_config: change power-save mode: false (implement)
Dec 24 10:28:39 laptop kernel: [   17.437451] ieee80211 phy0: wl_ops_bss_info_changed: qos enabled: false (implement)
Dec 24 10:28:39 laptop kernel: [   17.440537] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Dec 24 10:28:39 laptop kernel: [   17.495889] r8169 0000:03:00.0: eth0: link down
Dec 24 10:28:39 laptop kernel: [   17.496293] ADDRCONF(NETDEV_UP): eth0: link is not ready
Dec 24 10:28:39 laptop kernel: [   17.508571] init: failsafe main process (870) killed by TERM signal
Dec 24 10:28:39 laptop kernel: [   17.510810] init: apport pre-start process (975) terminated with status 1
Dec 24 10:28:39 laptop kernel: [   17.545396] init: apport post-stop process (1033) terminated with status 1
Dec 24 10:28:39 laptop kernel: [   17.552882] init: gdm main process (1032) killed by TERM signal
Dec 24 10:28:41 laptop kernel: [   18.971413] hda-intel: azx_get_response timeout, switching to polling mode: last cmd=0x300f0000
Dec 24 10:28:41 laptop kernel: [   19.529914] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,commit=0
Dec 24 10:28:41 laptop kernel: [   19.698025] EXT4-fs (sda6): re-mounted. Opts: user_xattr,commit=0
Dec 24 10:28:41 laptop kernel: [   19.747136] HDMI status: Pin=5 Presence_Detect=0 ELD_Valid=0
Dec 24 10:28:41 laptop kernel: [   19.779098] HDMI status: Pin=5 Presence_Detect=0 ELD_Valid=0
Dec 24 10:28:41 laptop kernel: [   19.790432] Bluetooth: Core ver 2.16
Dec 24 10:28:41 laptop kernel: [   19.790494] NET: Registered protocol family 31
Dec 24 10:28:41 laptop kernel: [   19.790497] Bluetooth: HCI device and connection manager initialized
Dec 24 10:28:41 laptop kernel: [   19.790500] Bluetooth: HCI socket layer initialized
Dec 24 10:28:41 laptop kernel: [   19.790502] Bluetooth: L2CAP socket layer initialized
Dec 24 10:28:41 laptop kernel: [   19.791236] Bluetooth: SCO socket layer initialized
Dec 24 10:28:41 laptop kernel: [   19.793957] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
Dec 24 10:28:41 laptop kernel: [   19.793960] Bluetooth: BNEP filters: protocol multicast
Dec 24 10:28:41 laptop kernel: [   19.795291] Bluetooth: RFCOMM TTY layer initialized
Dec 24 10:28:41 laptop kernel: [   19.795296] Bluetooth: RFCOMM socket layer initialized
Dec 24 10:28:41 laptop kernel: [   19.795299] Bluetooth: RFCOMM ver 1.11
Dec 24 10:28:41 laptop kernel: [   19.811144] HDMI status: Pin=5 Presence_Detect=0 ELD_Valid=0
Dec 24 10:28:41 laptop kernel: [   19.843053] HDMI status: Pin=5 Presence_Detect=0 ELD_Valid=0
Dec 24 10:28:41 laptop kernel: [   19.859204] input: HDA NVidia HDMI/DP,pcm=9 as /devices/pci0000:00/0000:00:01.0/0000:01:00.1/sound/card1/input13
Dec 24 10:28:41 laptop kernel: [   19.859366] input: HDA NVidia HDMI/DP,pcm=8 as /devices/pci0000:00/0000:00:01.0/0000:01:00.1/sound/card1/input14
Dec 24 10:28:41 laptop kernel: [   19.859503] input: HDA NVidia HDMI/DP,pcm=7 as /devices/pci0000:00/0000:00:01.0/0000:01:00.1/sound/card1/input15
Dec 24 10:28:41 laptop kernel: [   19.859630] input: HDA NVidia HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:01.0/0000:01:00.1/sound/card1/input16
Dec 24 10:28:42 laptop kernel: [   19.882578] wlan0: authenticate with 00:0c:42:23:3f:a0 (try 1)
Dec 24 10:28:42 laptop kernel: [   19.884183] wlan0: authenticated
Dec 24 10:28:42 laptop kernel: [   19.887961] wlan0: associate with 00:0c:42:23:3f:a0 (try 1)
Dec 24 10:28:42 laptop kernel: [   19.895238] wlan0: RX AssocResp from 00:0c:42:23:3f:a0 (capab=0x431 status=0 aid=2)
Dec 24 10:28:42 laptop kernel: [   19.895241] wlan0: associated
Dec 24 10:28:42 laptop kernel: [   19.895981] ieee80211 phy0: wl_ops_bss_info_changed: qos enabled: false (implement)
Dec 24 10:28:42 laptop kernel: [   19.895986] ieee80211 phy0: brcmsmac: wl_ops_bss_info_changed: associated
Dec 24 10:28:42 laptop kernel: [   19.896003] ieee80211 phy0: wl_ops_bss_info_changed: arp filtering: enabled true, count 0 (implement)
Dec 24 10:28:42 laptop kernel: [   19.896171] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
Dec 24 10:28:42 laptop kernel: [   20.072086] /dev/vmmon[1370]: Module vmmon: registered with major=10 minor=165
Dec 24 10:28:42 laptop kernel: [   20.072114] /dev/vmmon[1370]: Initial HV check: anyNotCapable=0 anyUnlocked=0 anyEnabled=0 anyDisabled=1
Dec 24 10:28:42 laptop kernel: [   20.072123] /dev/vmmon[1370]: HV check: anyNotCapable=0 anyUnlocked=0 anyEnabled=0 anyDisabled=1
Dec 24 10:28:42 laptop kernel: [   20.072127] /dev/vmmon[1370]: Module vmmon: initialized
Dec 24 10:28:42 laptop kernel: [   20.079428] [1379]: VMCI: shared components initialized.
Dec 24 10:28:42 laptop kernel: [   20.079467] [1379]: VMCI: host components initialized.
Dec 24 10:28:42 laptop kernel: [   20.079534] [1379]: VMCI: Module registered (name=vmci,major=10,minor=56).
Dec 24 10:28:42 laptop kernel: [   20.079537] [1379]: VMCI: Using host personality
Dec 24 10:28:42 laptop kernel: [   20.079539] [1379]: VMCI: Module (name=vmci) is initialized
Dec 24 10:28:42 laptop kernel: [   20.141038] ppdev: user-space parallel port driver
Dec 24 10:28:42 laptop kernel: [   20.321031] ieee80211 phy0: wl_ops_bss_info_changed: arp filtering: enabled true, count 1 (implement)
Dec 24 10:28:42 laptop kernel: [   20.593620] /dev/vmnet: open called by PID 1499 (vmnet-bridge)
Dec 24 10:28:42 laptop kernel: [   20.593632] /dev/vmnet: hub 0 does not exist, allocating memory.
Dec 24 10:28:42 laptop kernel: [   20.593660] /dev/vmnet: port on hub 0 successfully opened
Dec 24 10:28:42 laptop kernel: [   20.593673] bridge-wlan0: device is wireless, enabling SMAC
Dec 24 10:28:42 laptop kernel: [   20.593678] bridge-wlan0: up
Dec 24 10:28:42 laptop kernel: [   20.593682] bridge-wlan0: attached
Dec 24 10:28:43 laptop kernel: [   21.119185] /dev/vmnet: open called by PID 1609 (vmnet-netifup)
Dec 24 10:28:43 laptop kernel: [   21.119198] /dev/vmnet: hub 1 does not exist, allocating memory.
Dec 24 10:28:43 laptop kernel: [   21.119236] /dev/vmnet: port on hub 1 successfully opened
Dec 24 10:28:43 laptop kernel: [   21.535198] /dev/vmnet: open called by PID 1612 (vmnet-dhcpd)
Dec 24 10:28:43 laptop kernel: [   21.535215] /dev/vmnet: port on hub 1 successfully opened
Dec 24 10:28:43 laptop kernel: [   21.539127] /dev/vmnet: open called by PID 1664 (vmnet-natd)
Dec 24 10:28:43 laptop kernel: [   21.539139] /dev/vmnet: hub 8 does not exist, allocating memory.
Dec 24 10:28:43 laptop kernel: [   21.539174] /dev/vmnet: port on hub 8 successfully opened
Dec 24 10:28:43 laptop kernel: [   21.540568] userif-3: sent link down event.
Dec 24 10:28:43 laptop kernel: [   21.540572] userif-3: sent link up event.
Dec 24 10:28:43 laptop kernel: [   21.542269] /dev/vmnet: open called by PID 1668 (vmnet-netifup)
Dec 24 10:28:43 laptop kernel: [   21.542285] /dev/vmnet: port on hub 8 successfully opened
Dec 24 10:28:43 laptop kernel: [   21.693579] /dev/vmnet: open called by PID 1671 (vmnet-dhcpd)
Dec 24 10:28:43 laptop kernel: [   21.693595] /dev/vmnet: port on hub 8 successfully opened
Dec 24 10:28:44 laptop kernel: [   22.047190] init: plymouth-stop pre-start process (1778) terminated with status 1
Dec 24 10:28:45 laptop kernel: [   22.900931] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,commit=0
Dec 24 10:28:45 laptop kernel: [   22.903829] EXT4-fs (sda6): re-mounted. Opts: user_xattr,commit=0
Dec 24 10:28:53 laptop kernel: [   31.422459] vmnet1: no IPv6 routers present
Dec 24 10:28:54 laptop kernel: [   32.358583] vmnet8: no IPv6 routers present
Dec 24 10:29:40 laptop kernel: [   78.292607] psmouse.c: TouchPad at isa0060/serio1/input0 lost synchronization, throwing 4 bytes away.
Dec 24 10:29:40 laptop kernel: [   78.811125] psmouse.c: resync failed, issuing reconnect request
Dec 24 10:29:51 laptop kernel: [   89.551157] usb 2-1.1: new low speed USB device number 5 using ehci_hcd
Dec 24 10:29:51 laptop kernel: [   89.719384] input: Genius Optical Mouse as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.1/2-1.1:1.0/input/input17
Dec 24 10:29:51 laptop kernel: [   89.719777] generic-usb 0003:0458:003A.0001: input,hidraw0: USB HID v1.11 Mouse [Genius Optical Mouse] on usb-0000:00:1d.0-1.1/input0
Dec 24 10:29:51 laptop kernel: [   89.719875] usbcore: registered new interface driver usbhid
Dec 24 10:29:51 laptop kernel: [   89.719882] usbhid: USB HID core driver

```

I appreciate any help. Thanks

---

