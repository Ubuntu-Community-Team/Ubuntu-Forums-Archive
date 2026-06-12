---
title: "xubuntu 12.04 won't let me log in"
date: 2012-07-09
forum: General Help
---

### Post by Toriam on 2012-07-09
I recently installed 12.04 andlove it! Unfortunately, once I added a desktop account for my son, I was unable to login under my main account. I've tried to delete his account, but I'm unable to. I was under his account of course. I really don't want to reinstall! I've noticed on both accounts a crash report comes up every time (on my account when I could access it).

---

### Post by rukiaEnix on 2012-07-09
Have you tried logging in with the console?

---

### Post by Toriam on 2012-07-09
Thanks for replying so quickly! I'm working on that right now. Having trouble getting the HUI. Do you know how to fix my initial problem after I get logged in?

---

### Post by rukiaEnix on 2012-07-09
Please first verify you can log in with console.

What is the error message?

---

### Post by Toriam on 2012-07-09
I don't get one. It simply goes black, then goes back to the login screen. It  shows a message for a split second on the black screen. I can't catch it of course

---

### Post by rukiaEnix on 2012-07-09
Could you please post the lines of today from /var/log/messages?

Could you login with the console?

---

### Post by Toriam on 2012-07-10
I logged in console:

Welcome to Ubuntu 12.04! (other standard stuff)....


Then I tried to startx

Fatal server error
Server is already active for display 0
If this server is already running...
please consult...
ddxSigGiveUp: Closing log
Invalid MIT-Magic-Ccookie-1 keyInvalid...
xinit: unable to connect to x server: Resource temporarily unavailible
xinit: server error

I couldn't find messages in /var/log. Instead heres dmesg
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 3.2.0-26-generic (buildd@lamiak) (gcc version 4.6.3 (Ubuntu/Linaro 4.6.3-1ubuntu5) ) #41-Ubuntu SMP Thu Jun 14 16:26:01 UTC 2012 (Ubuntu 3.2.0-26.41-generic 3.2.19)
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   NSC Geode by NSC
[    0.000000]   Cyrix CyrixInstead
[    0.000000]   Centaur CentaurHauls
[    0.000000]   Transmeta GenuineTMx86
[    0.000000]   Transmeta TransmetaCPU
[    0.000000]   UMC UMC UMC UMC
[    0.000000] Atom PSE erratum detected, BIOS microcode update recommended
[    0.000000] Disabled fast string operations
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000003f376000 (usable)
[    0.000000]  BIOS-e820: 000000003f376000 - 000000003f3bf000 (reserved)
[    0.000000]  BIOS-e820: 000000003f3bf000 - 000000003f46d000 (usable)
[    0.000000]  BIOS-e820: 000000003f46d000 - 000000003f4bf000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000003f4bf000 - 000000003f4f0000 (usable)
[    0.000000]  BIOS-e820: 000000003f4f0000 - 000000003f4ff000 (ACPI data)
[    0.000000]  BIOS-e820: 000000003f4ff000 - 000000003f500000 (usable)
[    0.000000]  BIOS-e820: 000000003f500000 - 0000000040000000 (reserved)
[    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed14000 - 00000000fed1a000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed1c000 - 00000000fed20000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fff00000 - 0000000100000000 (reserved)
[    0.000000] Notice: NX (Execute Disable) protection missing in CPU!
[    0.000000] NX (Execute Disable) protection: approximated by x86 segment limits
[    0.000000] DMI 2.4 present.
[    0.000000] DMI: Acer AOA110/        , BIOS v0.3309 10/06/2008
[    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
[    0.000000] e820 remove range: 00000000000a0000 - 0000000000100000 (usable)
[    0.000000] last_pfn = 0x3f500 max_arch_pfn = 0x100000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-C7FFF write-protect
[    0.000000]   C8000-EFFFF uncachable
[    0.000000]   F0000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 0FFFE0000 mask 0FFFE0000 write-protect
[    0.000000]   1 base 0FFFC0000 mask 0FFFE0000 uncachable
[    0.000000]   2 base 000000000 mask 0E0000000 write-back
[    0.000000]   3 base 020000000 mask 0E0000000 write-back
[    0.000000]   4 base 03F800000 mask 0FF800000 uncachable
[    0.000000]   5 base 03F600000 mask 0FFE00000 uncachable
[    0.000000]   6 base 03F500000 mask 0FFF00000 uncachable
[    0.000000]   7 base 000000000 mask 0FFFE0000 uncachable
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] initial memory mapped : 0 - 01c00000
[    0.000000] Base memory trampoline at [c009b000] 9b000 size 16384
[    0.000000] init_memory_mapping: 0000000000000000-00000000377fe000
[    0.000000]  0000000000 - 00377fe000 page 4k
[    0.000000] kernel direct mapping tables up to 377fe000 @ 1b1f000-1c00000
[    0.000000] RAMDISK: 3586a000 - 36c2d000
[    0.000000] ACPI: RSDP 000fe020 00024 (v02 ACRSYS)
[    0.000000] ACPI: XSDT 3f4fe120 00064 (v01 ACRSYS ACRPRDCT 00000001      01000013)
[    0.000000] ACPI: FACP 3f4fc000 000F4 (v04 ACRSYS ACRPRDCT 00000001 1025 01000013)
[    0.000000] ACPI: DSDT 3f4f2000 05DE6 (v01 ACRSYS ACRPRDCT 00000001 1025 01000013)
[    0.000000] ACPI: FACS 3f488000 00040
[    0.000000] ACPI: SSDT 3f4fd000 004C4 (v02  PmRef    CpuPm 00003000 INTL 20051117)
[    0.000000] ACPI: HPET 3f4fb000 00038 (v01 ACRSYS ACRPRDCT 00000001 1025 01000013)
[    0.000000] ACPI: APIC 3f4fa000 00068 (v02 ACRSYS ACRPRDCT 00000001 1025 01000013)
[    0.000000] ACPI: MCFG 3f4f9000 0003C (v01 ACRSYS ACRPRDCT 00000001 1025 01000013)
[    0.000000] ACPI: ASF! 3f4f8000 000A5 (v32 ACRSYS ACRPRDCT 00000001 1025 01000013)
[    0.000000] ACPI: SLIC 3f4f1000 00176 (v01 ACRSYS ACRPRDCT 00000001 1025 01000013)
[    0.000000] ACPI: BOOT 3f4f0000 00028 (v01 ACRSYS ACRPRDCT 00000001 1025 01000013)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] 125MB HIGHMEM available.
[    0.000000] 887MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 377fe000
[    0.000000]   low ram: 0 - 377fe000
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000010 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x000377fe
[    0.000000]   HighMem  0x000377fe -> 0x0003f500
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[5] active PFN ranges
[    0.000000]     0: 0x00000010 -> 0x0000009f
[    0.000000]     0: 0x00000100 -> 0x0003f376
[    0.000000]     0: 0x0003f3bf -> 0x0003f46d
[    0.000000]     0: 0x0003f4bf -> 0x0003f4f0
[    0.000000]     0: 0x0003f4ff -> 0x0003f500
[    0.000000] On node 0 totalpages: 259045
[    0.000000] free_area_init_node: node 0, pgdat c1822dc0, node_mem_map f700d200
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3951 pages, LIFO batch:0
[    0.000000]   Normal zone: 1744 pages used for memmap
[    0.000000]   Normal zone: 221486 pages, LIFO batch:31
[    0.000000]   HighMem zone: 251 pages used for memmap
[    0.000000]   HighMem zone: 31581 pages, LIFO batch:7
[    0.000000] Using APIC driver default
[    0.000000] ACPI: PM-Timer IO Port: 0x408
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x02] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x04] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 4, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000
[    0.000000] SMP: Allowing 2 CPUs, 0 hotplug CPUs
[    0.000000] nr_irqs_gsi: 40
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
[    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 40000000 (gap: 40000000:a0000000)
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] setup_percpu: NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:2 nr_node_ids:1
[    0.000000] PERCPU: Embedded 13 pages/cpu @f6fed000 s31616 r0 d21632 u53248
[    0.000000] pcpu-alloc: s31616 r0 d21632 u53248 alloc=13*4096
[    0.000000] pcpu-alloc: [0] 0 [0] 1 
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 257018
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.2.0-26-generic root=UUID=d1899902-0e2f-4452-9a11-1bdb2b9ec377 ro quiet splash vt.handoff=7
[    0.000000] PID hash table entries: 4096 (order: 2, 16384 bytes)
[    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.000000] Initializing CPU#0
[    0.000000] allocated 4148992 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] Initializing HighMem for node 0 (000377fe:0003f500)
[    0.000000] Memory: 991956k/1037312k available (5615k kernel code, 44224k reserved, 2765k data, 712k init, 127328k highmem)
[    0.000000] virtual kernel memory layout:
[    0.000000]     fixmap  : 0xfff16000 - 0xfffff000   ( 932 kB)
[    0.000000]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[    0.000000]     vmalloc : 0xf7ffe000 - 0xff7fe000   ( 120 MB)
[    0.000000]     lowmem  : 0xc0000000 - 0xf77fe000   ( 887 MB)
[    0.000000]       .init : 0xc1830000 - 0xc18e2000   ( 712 kB)
[    0.000000]       .data : 0xc157be04 - 0xc182f4c0   (2765 kB)
[    0.000000]       .text : 0xc1000000 - 0xc157be04   (5615 kB)
[    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.000000] SLUB: Genslabs=15, HWalign=64, Order=0-3, MinObjects=0, CPUs=2, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000] 	RCU dyntick-idle grace-period acceleration is enabled.
[    0.000000] NR_IRQS:2304 nr_irqs:512 16
[    0.000000] CPU 0 irqstacks, hard=f5008000 soft=f500a000
[    0.000000] vt handoff: transparent VT on vt#7
[    0.000000] Console: colour dummy device 80x25
[    0.000000] console [tty0] enabled
[    0.000000] hpet clockevent registered
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 1596.061 MHz processor.
[    0.004004] Calibrating delay loop (skipped), value calculated using timer frequency.. 3192.12 BogoMIPS (lpj=6384244)
[    0.004017] pid_max: default: 32768 minimum: 301
[    0.004073] Security Framework initialized
[    0.004115] AppArmor: AppArmor initialized
[    0.004120] Yama: becoming mindful.
[    0.004249] Mount-cache hash table entries: 512
[    0.004537] Initializing cgroup subsys cpuacct
[    0.004553] Initializing cgroup subsys memory
[    0.004572] Initializing cgroup subsys devices
[    0.004578] Initializing cgroup subsys freezer
[    0.004584] Initializing cgroup subsys blkio
[    0.004600] Initializing cgroup subsys perf_event
[    0.004647] Atom PSE erratum detected, BIOS microcode update recommended
[    0.004653] Disabled fast string operations
[    0.004662] CPU: Physical Processor ID: 0
[    0.004667] CPU: Processor Core ID: 0
[    0.004674] mce: CPU supports 5 MCE banks
[    0.008021] CPU0: Thermal monitoring enabled (TM1)
[    0.008031] using mwait in idle threads.
[    0.011797] ACPI: Core revision 20110623
[    0.024035] ftrace: allocating 25884 entries in 51 pages
[    0.028112] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.028608] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.069401] CPU0: Intel(R) Atom(TM) CPU N270   @ 1.60GHz stepping 02
[    0.072003] Performance Events: PEBS fmt0+, Atom events, Intel PMU driver.
[    0.072003] ... version:                3
[    0.072003] ... bit width:              40
[    0.072003] ... generic registers:      2
[    0.072003] ... value mask:             000000ffffffffff
[    0.072003] ... max period:             000000007fffffff
[    0.072003] ... fixed-purpose events:   3
[    0.072003] ... event mask:             0000000700000003
[    0.072003] NMI watchdog enabled, takes one hw-pmu counter.
[    0.072003] CPU 1 irqstacks, hard=f50ea000 soft=f50ec000
[    0.072003] Booting Node   0, Processors  #1 Ok.
[    0.072003] smpboot cpu 1: start_ip = 9b000
[    0.008000] Initializing CPU#1
[    0.008000] Atom PSE erratum detected, BIOS microcode update recommended
[    0.008000] Disabled fast string operations
[    0.160077] NMI watchdog enabled, takes one hw-pmu counter.
[    0.160167] Brought up 2 CPUs
[    0.160176] Total of 2 processors activated (6384.06 BogoMIPS).
[    0.160783] devtmpfs: initialized
[    0.160783] EVM: security.selinux
[    0.160783] EVM: security.SMACK64
[    0.160783] EVM: security.capability
[    0.160783] PM: Registering ACPI NVS region at 3f46d000 (335872 bytes)
[    0.160783] Acer Aspire One A110 series board detected. Selecting KBD-method for reboot.
[    0.164780] print_constraints: dummy: 
[    0.164842] RTC time: 16:02:37, date: 07/10/12
[    0.164940] NET: Registered protocol family 16
[    0.165094] Trying to unpack rootfs image as initramfs...
[    0.165456] EISA bus registered
[    0.165571] ACPI: bus type pci registered
[    0.165821] PCI: MMCONFIG for domain 0000 [bus 00-ff] at [mem 0xe0000000-0xefffffff] (base 0xe0000000)
[    0.165833] PCI: MMCONFIG at [mem 0xe0000000-0xefffffff] reserved in E820
[    0.165840] PCI: Using MMCONFIG for extended config space
[    0.165847] PCI: Using configuration type 1 for base access
[    0.180176] bio: create slab <bio-0> at 0
[    0.180572] ACPI: Added _OSI(Module Device)
[    0.180581] ACPI: Added _OSI(Processor Device)
[    0.180590] ACPI: Added _OSI(3.0 _SCP Extensions)
[    0.180598] ACPI: Added _OSI(Processor Aggregator Device)
[    0.184625] ACPI: EC: Look up EC in DSDT
[    0.188811] ACPI: Executed 1 blocks of module-level executable AML code
[    0.193816] [Firmware Bug]: ACPI: BIOS _OSI(Linux) query ignored
[    0.195078] ACPI: SSDT 3f380c90 00239 (v02  PmRef  Cpu0Ist 00003000 INTL 20051117)
[    0.196139] ACPI: Dynamic OEM Table Load:
[    0.196152] ACPI: SSDT   (null) 00239 (v02  PmRef  Cpu0Ist 00003000 INTL 20051117)
[    0.196566] ACPI: SSDT 3f37fe10 001C7 (v02  PmRef  Cpu0Cst 00003001 INTL 20051117)
[    0.197550] ACPI: Dynamic OEM Table Load:
[    0.197563] ACPI: SSDT   (null) 001C7 (v02  PmRef  Cpu0Cst 00003001 INTL 20051117)
[    0.264973] ACPI: SSDT 3f380f10 000D0 (v02  PmRef  Cpu1Ist 00003000 INTL 20051117)
[    0.265993] ACPI: Dynamic OEM Table Load:
[    0.266005] ACPI: SSDT   (null) 000D0 (v02  PmRef  Cpu1Ist 00003000 INTL 20051117)
[    0.266412] ACPI: SSDT 3f37ef10 00083 (v02  PmRef  Cpu1Cst 00003000 INTL 20051117)
[    0.267400] ACPI: Dynamic OEM Table Load:
[    0.267413] ACPI: SSDT   (null) 00083 (v02  PmRef  Cpu1Cst 00003000 INTL 20051117)
[    0.337673] ACPI: Interpreter enabled
[    0.337694] ACPI: (supports S0 S3 S4 S5)
[    0.337764] ACPI: Using IOAPIC for interrupt routing
[    0.370092] ACPI: EC: GPE = 0x17, I/O: command/status = 0x66, data = 0x62
[    0.370613] ACPI: No dock devices found.
[    0.370622] HEST: Table not found.
[    0.370635] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
[    0.372112] ACPI Error: [CAPB] Namespace lookup failure, AE_ALREADY_EXISTS (20110623/dsfield-143)
[    0.372137] ACPI Error: Method parse/execution failed [\_SB_.PCI0._OSC] (Node f5025ca8), AE_ALREADY_EXISTS (20110623/psparse-536)
[    0.372166] ACPI: Marking method _OSC as Serialized because of AE_ALREADY_EXISTS error
[    0.372191] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-ff])
[    0.374685] pci_root PNP0A08:00: host bridge window [io  0x0000-0x0cf7]
[    0.374697] pci_root PNP0A08:00: host bridge window [io  0x0d00-0xffff]
[    0.374707] pci_root PNP0A08:00: host bridge window [mem 0x000a0000-0x000bffff]
[    0.374720] pci_root PNP0A08:00: host bridge window [mem 0x40000000-0xfebfffff]
[    0.374761] pci 0000:00:00.0: [8086:27ac] type 0 class 0x000600
[    0.374856] pci 0000:00:02.0: [8086:27ae] type 0 class 0x000300
[    0.374881] pci 0000:00:02.0: reg 10: [mem 0x58480000-0x584fffff]
[    0.374897] pci 0000:00:02.0: reg 14: [io  0x60c0-0x60c7]
[    0.374913] pci 0000:00:02.0: reg 18: [mem 0x40000000-0x4fffffff pref]
[    0.374929] pci 0000:00:02.0: reg 1c: [mem 0x58500000-0x5853ffff]
[    0.375010] pci 0000:00:02.1: [8086:27a6] type 0 class 0x000380
[    0.375031] pci 0000:00:02.1: reg 10: [mem 0x58400000-0x5847ffff]
[    0.375193] pci 0000:00:1b.0: [8086:27d8] type 0 class 0x000403
[    0.375229] pci 0000:00:1b.0: reg 10: [mem 0x58540000-0x58543fff 64bit]
[    0.375375] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    0.375388] pci 0000:00:1b.0: PME# disabled
[    0.375440] pci 0000:00:1c.0: [8086:27d0] type 1 class 0x000604
[    0.375588] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    0.375600] pci 0000:00:1c.0: PME# disabled
[    0.375655] pci 0000:00:1c.1: [8086:27d2] type 1 class 0x000604
[    0.375807] pci 0000:00:1c.1: PME# supported from D0 D3hot D3cold
[    0.375820] pci 0000:00:1c.1: PME# disabled
[    0.375876] pci 0000:00:1c.2: [8086:27d4] type 1 class 0x000604
[    0.376046] pci 0000:00:1c.2: PME# supported from D0 D3hot D3cold
[    0.376059] pci 0000:00:1c.2: PME# disabled
[    0.376116] pci 0000:00:1c.3: [8086:27d6] type 1 class 0x000604
[    0.376271] pci 0000:00:1c.3: PME# supported from D0 D3hot D3cold
[    0.376283] pci 0000:00:1c.3: PME# disabled
[    0.376340] pci 0000:00:1d.0: [8086:27c8] type 0 class 0x000c03
[    0.376417] pci 0000:00:1d.0: reg 20: [io  0x6080-0x609f]
[    0.376487] pci 0000:00:1d.1: [8086:27c9] type 0 class 0x000c03
[    0.376563] pci 0000:00:1d.1: reg 20: [io  0x6060-0x607f]
[    0.376633] pci 0000:00:1d.2: [8086:27ca] type 0 class 0x000c03
[    0.376709] pci 0000:00:1d.2: reg 20: [io  0x6040-0x605f]
[    0.376778] pci 0000:00:1d.3: [8086:27cb] type 0 class 0x000c03
[    0.376854] pci 0000:00:1d.3: reg 20: [io  0x6020-0x603f]
[    0.376945] pci 0000:00:1d.7: [8086:27cc] type 0 class 0x000c03
[    0.376987] pci 0000:00:1d.7: reg 10: [mem 0x58544400-0x585447ff]
[    0.377134] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
[    0.377148] pci 0000:00:1d.7: PME# disabled
[    0.377191] pci 0000:00:1e.0: [8086:2448] type 1 class 0x000604
[    0.377338] pci 0000:00:1f.0: [8086:27b9] type 0 class 0x000601
[    0.377493] pci 0000:00:1f.0: ICH7 LPC Generic IO decode 4 PIO at 0068 (mask 0007)
[    0.377584] pci 0000:00:1f.2: [8086:27c4] type 0 class 0x000101
[    0.377617] pci 0000:00:1f.2: reg 10: [io  0x0000-0x0007]
[    0.377639] pci 0000:00:1f.2: reg 14: [io  0x0000-0x0003]
[    0.377660] pci 0000:00:1f.2: reg 18: [io  0x0000-0x0007]
[    0.377680] pci 0000:00:1f.2: reg 1c: [io  0x0000-0x0003]
[    0.377701] pci 0000:00:1f.2: reg 20: [io  0x60a0-0x60af]
[    0.377779] pci 0000:00:1f.2: PME# supported from D3hot
[    0.377791] pci 0000:00:1f.2: PME# disabled
[    0.377829] pci 0000:00:1f.3: [8086:27da] type 0 class 0x000c05
[    0.377929] pci 0000:00:1f.3: reg 20: [io  0x6000-0x601f]
[    0.378084] pci 0000:00:1c.0: PCI bridge to [bus 01-01]
[    0.378098] pci 0000:00:1c.0:   bridge window [io  0x5000-0x5fff]
[    0.378111] pci 0000:00:1c.0:   bridge window [mem 0x57300000-0x583fffff]
[    0.378129] pci 0000:00:1c.0:   bridge window [mem 0x50000000-0x50ffffff 64bit pref]
[    0.378252] pci 0000:02:00.0: [10ec:8136] type 0 class 0x000200
[    0.378289] pci 0000:02:00.0: reg 10: [io  0x3000-0x30ff]
[    0.378342] pci 0000:02:00.0: reg 18: [mem 0x51010000-0x51010fff 64bit pref]
[    0.378379] pci 0000:02:00.0: reg 20: [mem 0x51000000-0x5100ffff 64bit pref]
[    0.378406] pci 0000:02:00.0: reg 30: [mem 0xfffe0000-0xffffffff pref]
[    0.378522] pci 0000:02:00.0: supports D1 D2
[    0.378530] pci 0000:02:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.378544] pci 0000:02:00.0: PME# disabled
[    0.384092] pci 0000:00:1c.1: PCI bridge to [bus 02-02]
[    0.384109] pci 0000:00:1c.1:   bridge window [io  0x3000-0x4fff]
[    0.384122] pci 0000:00:1c.1:   bridge window [mem 0x56300000-0x572fffff]
[    0.384139] pci 0000:00:1c.1:   bridge window [mem 0x51000000-0x520fffff 64bit pref]
[    0.384296] pci 0000:03:00.0: [168c:001c] type 0 class 0x000200
[    0.384379] pci 0000:03:00.0: reg 10: [mem 0x55200000-0x5520ffff 64bit]
[    0.384762] pci 0000:03:00.0: disabling ASPM on pre-1.1 PCIe device.  You can enable it with 'pcie_aspm=force'
[    0.384794] pci 0000:00:1c.2: PCI bridge to [bus 03-03]
[    0.384807] pci 0000:00:1c.2:   bridge window [io  0x2000-0x2fff]
[    0.384820] pci 0000:00:1c.2:   bridge window [mem 0x55200000-0x562fffff]
[    0.384837] pci 0000:00:1c.2:   bridge window [mem 0x52100000-0x530fffff 64bit pref]
[    0.384969] pci 0000:04:00.0: [197b:2382] type 0 class 0x000880
[    0.385017] pci 0000:04:00.0: reg 10: [mem 0x54100300-0x541003ff]
[    0.385178] pci 0000:04:00.0: reg 30: [mem 0xffff8000-0xffffffff pref]
[    0.385404] pci 0000:04:00.2: [197b:2381] type 0 class 0x000805
[    0.385451] pci 0000:04:00.2: reg 10: [mem 0x54100200-0x541002ff]
[    0.385812] pci 0000:04:00.3: [197b:2383] type 0 class 0x000880
[    0.385861] pci 0000:04:00.3: reg 10: [mem 0x54100100-0x541001ff]
[    0.386226] pci 0000:04:00.4: [197b:2384] type 0 class 0x000880
[    0.386273] pci 0000:04:00.4: reg 10: [mem 0x54100000-0x541000ff]
[    0.392138] pci 0000:00:1c.3: PCI bridge to [bus 04-04]
[    0.392155] pci 0000:00:1c.3:   bridge window [io  0x1000-0x1fff]
[    0.392169] pci 0000:00:1c.3:   bridge window [mem 0x54100000-0x551fffff]
[    0.392186] pci 0000:00:1c.3:   bridge window [mem 0x53100000-0x540fffff 64bit pref]
[    0.392325] pci 0000:00:1e.0: PCI bridge to [bus 05-05] (subtractive decode)
[    0.392355] pci 0000:00:1e.0:   bridge window [io  0x0000-0x0cf7] (subtractive decode)
[    0.392366] pci 0000:00:1e.0:   bridge window [io  0x0d00-0xffff] (subtractive decode)
[    0.392376] pci 0000:00:1e.0:   bridge window [mem 0x000a0000-0x000bffff] (subtractive decode)
[    0.392387] pci 0000:00:1e.0:   bridge window [mem 0x40000000-0xfebfffff] (subtractive decode)
[    0.392439] pci_bus 0000:00: on NUMA node 0
[    0.392457] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.392936] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P32_._PRT]
[    0.393304] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.EXP1._PRT]
[    0.393535] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.EXP2._PRT]
[    0.393723] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.EXP3._PRT]
[    0.393908] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.EXP4._PRT]
[    0.394428] ACPI Error: [CAPB] Namespace lookup failure, AE_ALREADY_EXISTS (20110623/dsfield-143)
[    0.394453] ACPI Error: Method parse/execution failed [\_SB_.PCI0._OSC] (Node f5025ca8), AE_ALREADY_EXISTS (20110623/psparse-536)
[    0.394495]  pci0000:00: Requesting ACPI _OSC control (0x1d)
[    0.394701] ACPI Error: [CAPB] Namespace lookup failure, AE_ALREADY_EXISTS (20110623/dsfield-143)
[    0.394722] ACPI Error: Method parse/execution failed [\_SB_.PCI0._OSC] (Node f5025ca8), AE_ALREADY_EXISTS (20110623/psparse-536)
[    0.394759]  pci0000:00: ACPI _OSC request failed (AE_ALREADY_EXISTS), returned control mask: 0x1d
[    0.394767] ACPI _OSC control for PCIe not granted, disabling ASPM
[    0.408735] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 7 9 10 *11 12)
[    0.408960] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 7 9 10 *11 12)
[    0.409186] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 7 9 10 *11 12)
[    0.409416] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 7 9 10 *11 12)
[    0.409631] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 7 9 10 11 12) *0, disabled.
[    0.409849] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 7 9 10 11 12) *0, disabled.
[    0.410071] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 7 9 10 11 12) *0, disabled.
[    0.410296] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 7 9 10 11 12) *0, disabled.
[    0.410779] vgaarb: device added: PCI:0000:00:02.0,decodes=io+mem,owns=io+mem,locks=none
[    0.410817] vgaarb: loaded
[    0.410823] vgaarb: bridge control possible 0000:00:02.0
[    0.411412] i2c-core: driver [aat2870] using legacy suspend method
[    0.411421] i2c-core: driver [aat2870] using legacy resume method
[    0.411719] SCSI subsystem initialized
[    0.411939] libata version 3.00 loaded.
[    0.412179] usbcore: registered new interface driver usbfs
[    0.412229] usbcore: registered new interface driver hub
[    0.412346] usbcore: registered new device driver usb
[    0.412790] PCI: Using ACPI for IRQ routing
[    0.425349] PCI: pci_cache_line_size set to 64 bytes
[    0.425556] reserve RAM buffer: 000000000009fc00 - 000000000009ffff 
[    0.425566] reserve RAM buffer: 000000003f376000 - 000000003fffffff 
[    0.425577] reserve RAM buffer: 000000003f46d000 - 000000003fffffff 
[    0.425587] reserve RAM buffer: 000000003f4f0000 - 000000003fffffff 
[    0.425596] reserve RAM buffer: 000000003f500000 - 000000003fffffff 
[    0.426008] NetLabel: Initializing
[    0.426016] NetLabel:  domain hash size = 128
[    0.426021] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.426057] NetLabel:  unlabeled traffic allowed by default
[    0.426304] HPET: 3 timers in total, 0 timers will be used for per-cpu timer
[    0.426319] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[    0.426336] hpet0: 3 comparators, 64-bit 14.318180 MHz counter
[    0.436223] Switching to clocksource hpet
[    0.462367] AppArmor: AppArmor Filesystem Enabled
[    0.462455] pnp: PnP ACPI init
[    0.462512] ACPI: bus type pnp registered
[    0.463931] pnp 00:00: [bus 00-ff]
[    0.463943] pnp 00:00: [io  0x0000-0x0cf7 window]
[    0.463953] pnp 00:00: [io  0x0cf8-0x0cff]
[    0.463961] pnp 00:00: [io  0x0d00-0xffff window]
[    0.463970] pnp 00:00: [mem 0x000a0000-0x000bffff window]
[    0.463979] pnp 00:00: [mem 0x000c0000-0x000c3fff window]
[    0.463988] pnp 00:00: [mem 0x000c4000-0x000c7fff window]
[    0.463997] pnp 00:00: [mem 0x000c8000-0x000cbfff window]
[    0.464051] pnp 00:00: [mem 0x000cc000-0x000cffff window]
[    0.464061] pnp 00:00: [mem 0x000d0000-0x000d3fff window]
[    0.464070] pnp 00:00: [mem 0x000d4000-0x000d7fff window]
[    0.464079] pnp 00:00: [mem 0x000d8000-0x000dbfff window]
[    0.464087] pnp 00:00: [mem 0x000dc000-0x000dffff window]
[    0.464096] pnp 00:00: [mem 0x000e0000-0x000e3fff window]
[    0.464105] pnp 00:00: [mem 0x000e4000-0x000e7fff window]
[    0.464114] pnp 00:00: [mem 0x000e8000-0x000ebfff window]
[    0.464123] pnp 00:00: [mem 0x000ec000-0x000effff window]
[    0.464132] pnp 00:00: [mem 0x000f0000-0x000fffff window]
[    0.464141] pnp 00:00: [mem 0x40000000-0xfebfffff window]
[    0.464345] pnp 00:00: Plug and Play ACPI device, IDs PNP0a08 PNP0a03 (active)
[    0.464848] pnp 00:01: [io  0x002e-0x002f]
[    0.464859] pnp 00:01: [io  0x0068-0x006f]
[    0.464868] pnp 00:01: [io  0x0200-0x020f]
[    0.464877] pnp 00:01: [io  0x164e-0x164f]
[    0.464885] pnp 00:01: [io  0x0061]
[    0.464892] pnp 00:01: [io  0x0070]
[    0.464900] pnp 00:01: [io  0x0080]
[    0.464908] pnp 00:01: [io  0x0092]
[    0.464916] pnp 00:01: [io  0x00b2-0x00b3]
[    0.464925] pnp 00:01: [io  0x0063]
[    0.464933] pnp 00:01: [io  0x0065]
[    0.464941] pnp 00:01: [io  0x0067]
[    0.464949] pnp 00:01: [io  0x0600-0x060f]
[    0.464957] pnp 00:01: [io  0x0610]
[    0.464964] pnp 00:01: [io  0x0800-0x080f]
[    0.464973] pnp 00:01: [io  0x0400-0x047f]
[    0.464981] pnp 00:01: [io  0x0500-0x053f]
[    0.464990] pnp 00:01: [mem 0xe0000000-0xefffffff]
[    0.465000] pnp 00:01: [mem 0xfed1c000-0xfed1ffff]
[    0.465009] pnp 00:01: [mem 0xfed14000-0xfed17fff]
[    0.465019] pnp 00:01: [mem 0xfed18000-0xfed18fff]
[    0.465028] pnp 00:01: [mem 0xfed19000-0xfed19fff]
[    0.465036] pnp 00:01: [mem 0xfec00000-0xfec00fff]
[    0.465045] pnp 00:01: [mem 0xfee00000-0xfee00fff]
[    0.465111] pnp 00:01: disabling [io  0x164e-0x164f] because it overlaps 0000:00:1c.3 BAR 13 [io  0x1000-0x1fff]
[    0.465327] system 00:01: [io  0x0200-0x020f] has been reserved
[    0.465340] system 00:01: [io  0x0600-0x060f] has been reserved
[    0.465350] system 00:01: [io  0x0610] has been reserved
[    0.465359] system 00:01: [io  0x0800-0x080f] has been reserved
[    0.465369] system 00:01: [io  0x0400-0x047f] has been reserved
[    0.465379] system 00:01: [io  0x0500-0x053f] has been reserved
[    0.465391] system 00:01: [mem 0xe0000000-0xefffffff] has been reserved
[    0.465402] system 00:01: [mem 0xfed1c000-0xfed1ffff] has been reserved
[    0.465412] system 00:01: [mem 0xfed14000-0xfed17fff] has been reserved
[    0.465423] system 00:01: [mem 0xfed18000-0xfed18fff] has been reserved
[    0.465433] system 00:01: [mem 0xfed19000-0xfed19fff] has been reserved
[    0.465444] system 00:01: [mem 0xfec00000-0xfec00fff] could not be reserved
[    0.465455] system 00:01: [mem 0xfee00000-0xfee00fff] has been reserved
[    0.465469] system 00:01: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.465515] pnp 00:02: [io  0x0000-0x001f]
[    0.465524] pnp 00:02: [io  0x0081-0x0091]
[    0.465532] pnp 00:02: [io  0x0093-0x009f]
[    0.465540] pnp 00:02: [io  0x00c0-0x00df]
[    0.465548] pnp 00:02: [dma 4]
[    0.465663] pnp 00:02: Plug and Play ACPI device, IDs PNP0200 (active)
[    0.465762] pnp 00:03: [io  0x0070-0x0077]
[    0.465872] pnp 00:03: Plug and Play ACPI device, IDs PNP0b00 (active)
[    0.466103] pnp 00:04: [irq 0 disabled]
[    0.466132] pnp 00:04: [irq 8]
[    0.466141] pnp 00:04: [mem 0xfed00000-0xfed003ff]
[    0.466281] pnp 00:04: Plug and Play ACPI device, IDs PNP0103 (active)
[    0.466332] pnp 00:05: [io  0x00f0]
[    0.466350] pnp 00:05: [irq 13]
[    0.466464] pnp 00:05: Plug and Play ACPI device, IDs PNP0c04 (active)
[    0.466507] pnp 00:06: [mem 0xff800000-0xffffffff]
[    0.466616] pnp 00:06: Plug and Play ACPI device, IDs INT0800 (active)
[    0.466690] pnp 00:07: [io  0x0060]
[    0.466698] pnp 00:07: [io  0x0064]
[    0.466715] pnp 00:07: [irq 1]
[    0.466833] pnp 00:07: Plug and Play ACPI device, IDs PNP0303 (active)
[    0.466900] pnp 00:08: [irq 12]
[    0.467028] pnp 00:08: Plug and Play ACPI device, IDs PNP0f13 (active)
[    0.467327] pnp: PnP ACPI: found 9 devices
[    0.467336] ACPI: ACPI bus type pnp unregistered
[    0.467346] PnPBIOS: Disabled by ACPI PNP
[    0.510226] pci 0000:02:00.0: no compatible bridge window for [mem 0xfffe0000-0xffffffff pref]
[    0.510244] pci 0000:04:00.0: no compatible bridge window for [mem 0xffff8000-0xffffffff pref]
[    0.510260] PCI: max bus depth: 1 pci_try_num: 2
[    0.510339] pci 0000:00:1c.0: PCI bridge to [bus 01-01]
[    0.510349] pci 0000:00:1c.0:   bridge window [io  0x5000-0x5fff]
[    0.510364] pci 0000:00:1c.0:   bridge window [mem 0x57300000-0x583fffff]
[    0.510377] pci 0000:00:1c.0:   bridge window [mem 0x50000000-0x50ffffff 64bit pref]
[    0.510401] pci 0000:02:00.0: BAR 6: assigned [mem 0x51020000-0x5103ffff pref]
[    0.510412] pci 0000:00:1c.1: PCI bridge to [bus 02-02]
[    0.510422] pci 0000:00:1c.1:   bridge window [io  0x3000-0x4fff]
[    0.510436] pci 0000:00:1c.1:   bridge window [mem 0x56300000-0x572fffff]
[    0.510449] pci 0000:00:1c.1:   bridge window [mem 0x51000000-0x520fffff 64bit pref]
[    0.510466] pci 0000:00:1c.2: PCI bridge to [bus 03-03]
[    0.510476] pci 0000:00:1c.2:   bridge window [io  0x2000-0x2fff]
[    0.510491] pci 0000:00:1c.2:   bridge window [mem 0x55200000-0x562fffff]
[    0.510505] pci 0000:00:1c.2:   bridge window [mem 0x52100000-0x530fffff 64bit pref]
[    0.510527] pci 0000:04:00.0: BAR 6: assigned [mem 0x53100000-0x53107fff pref]
[    0.510539] pci 0000:00:1c.3: PCI bridge to [bus 04-04]
[    0.510551] pci 0000:00:1c.3:   bridge window [io  0x1000-0x1fff]
[    0.510568] pci 0000:00:1c.3:   bridge window [mem 0x54100000-0x551fffff]
[    0.510582] pci 0000:00:1c.3:   bridge window [mem 0x53100000-0x540fffff 64bit pref]
[    0.510601] pci 0000:00:1e.0: PCI bridge to [bus 05-05]
[    0.510668] pci 0000:00:1c.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.510682] pci 0000:00:1c.0: setting latency timer to 64
[    0.510714] pci 0000:00:1c.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    0.510727] pci 0000:00:1c.1: setting latency timer to 64
[    0.510757] pci 0000:00:1c.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.510770] pci 0000:00:1c.2: setting latency timer to 64
[    0.510800] pci 0000:00:1c.3: PCI INT D -> GSI 19 (level, low) -> IRQ 19
[    0.510813] pci 0000:00:1c.3: setting latency timer to 64
[    0.510831] pci 0000:00:1e.0: setting latency timer to 64
[    0.510844] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
[    0.510853] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff]
[    0.510862] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
[    0.510872] pci_bus 0000:00: resource 7 [mem 0x40000000-0xfebfffff]
[    0.510881] pci_bus 0000:01: resource 0 [io  0x5000-0x5fff]
[    0.510890] pci_bus 0000:01: resource 1 [mem 0x57300000-0x583fffff]
[    0.510900] pci_bus 0000:01: resource 2 [mem 0x50000000-0x50ffffff 64bit pref]
[    0.510910] pci_bus 0000:02: resource 0 [io  0x3000-0x4fff]
[    0.510919] pci_bus 0000:02: resource 1 [mem 0x56300000-0x572fffff]
[    0.510929] pci_bus 0000:02: resource 2 [mem 0x51000000-0x520fffff 64bit pref]
[    0.510938] pci_bus 0000:03: resource 0 [io  0x2000-0x2fff]
[    0.510947] pci_bus 0000:03: resource 1 [mem 0x55200000-0x562fffff]
[    0.510957] pci_bus 0000:03: resource 2 [mem 0x52100000-0x530fffff 64bit pref]
[    0.510967] pci_bus 0000:04: resource 0 [io  0x1000-0x1fff]
[    0.510976] pci_bus 0000:04: resource 1 [mem 0x54100000-0x551fffff]
[    0.510986] pci_bus 0000:04: resource 2 [mem 0x53100000-0x540fffff 64bit pref]
[    0.510996] pci_bus 0000:05: resource 4 [io  0x0000-0x0cf7]
[    0.511005] pci_bus 0000:05: resource 5 [io  0x0d00-0xffff]
[    0.511014] pci_bus 0000:05: resource 6 [mem 0x000a0000-0x000bffff]
[    0.511023] pci_bus 0000:05: resource 7 [mem 0x40000000-0xfebfffff]
[    0.511156] NET: Registered protocol family 2
[    0.511366] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.512336] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.513473] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.514058] TCP: Hash tables configured (established 131072 bind 65536)
[    0.514070] TCP reno registered
[    0.514085] UDP hash table entries: 512 (order: 2, 16384 bytes)
[    0.514113] UDP-Lite hash table entries: 512 (order: 2, 16384 bytes)
[    0.514387] NET: Registered protocol family 1
[    0.514438] pci 0000:00:02.0: Boot video device
[    0.514502] pci 0000:00:1d.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.514533] pci 0000:00:1d.0: PCI INT A disabled
[    0.514555] pci 0000:00:1d.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    0.514586] pci 0000:00:1d.1: PCI INT B disabled
[    0.514607] pci 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.514637] pci 0000:00:1d.2: PCI INT C disabled
[    0.514658] pci 0000:00:1d.3: PCI INT D -> GSI 19 (level, low) -> IRQ 19
[    0.514688] pci 0000:00:1d.3: PCI INT D disabled
[    0.514712] pci 0000:00:1d.7: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.514880] pci 0000:00:1d.7: PCI INT A disabled
[    0.514955] PCI: CLS 0 bytes, default 64
[    0.514970] Simple Boot Flag value 0x5 read from CMOS RAM was invalid
[    0.514978] Simple Boot Flag at 0x44 set to 0x1
[    0.516341] audit: initializing netlink socket (disabled)
[    0.516379] type=2000 audit(1341936156.512:1): initialized
[    0.579885] highmem bounce pool size: 64 pages
[    0.579903] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    0.587185] VFS: Disk quotas dquot_6.5.2
[    0.587414] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.589667] fuse init (API version 7.17)
[    0.590055] msgmni has been set to 1688
[    0.591363] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.591489] io scheduler noop registered
[    0.591497] io scheduler deadline registered
[    0.591527] io scheduler cfq registered (default)
[    0.591974] pcieport 0000:00:1c.0: setting latency timer to 64
[    0.592125] pcieport 0000:00:1c.0: irq 40 for MSI/MSI-X
[    0.592325] pcieport 0000:00:1c.1: setting latency timer to 64
[    0.592412] pcieport 0000:00:1c.1: irq 41 for MSI/MSI-X
[    0.592574] pcieport 0000:00:1c.2: setting latency timer to 64
[    0.592659] pcieport 0000:00:1c.2: irq 42 for MSI/MSI-X
[    0.592818] pcieport 0000:00:1c.3: setting latency timer to 64
[    0.592907] pcieport 0000:00:1c.3: irq 43 for MSI/MSI-X
[    0.593215] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.593328] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.593565] intel_idle: MWAIT substates: 0x20220
[    0.593584] intel_idle: v0.4 model 0x1C
[    0.593590] intel_idle: lapic_timer_reliable_states 0x2
[    0.593598] Marking TSC unstable due to TSC halts in idle states deeper than C2
[    0.594126] ACPI: Deprecated procfs I/F for AC is loaded, please retry with CONFIG_ACPI_PROCFS_POWER cleared
[    0.594879] ACPI: AC Adapter [ACAD] (on-line)
[    0.595404] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0
[    0.595421] ACPI: Power Button [PWRB]
[    0.595601] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input1
[    0.596084] ACPI: Lid Switch [LID0]
[    0.596274] input: Sleep Button as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input2
[    0.596289] ACPI: Sleep Button [SLPB]
[    0.596490] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input3
[    0.596503] ACPI: Power Button [PWRF]
[    0.600318] ACPI: Deprecated procfs I/F for battery is loaded, please retry with CONFIG_ACPI_PROCFS_POWER cleared
[    0.600361] ACPI: Battery Slot [BAT1] (battery absent)
[    0.600470] ERST: Table is not found!
[    0.600476] GHES: HEST is not enabled!
[    0.600758] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    0.601710] ACPI: Battery Slot [BAT1] (battery absent)
[    0.601743] isapnp: Scanning for PnP cards...
[    0.956688] isapnp: No Plug & Play device found
[    1.231559] Freeing initrd memory: 20236k freed
[    1.293103] Linux agpgart interface v0.103
[    1.293278] agpgart-intel 0000:00:00.0: Intel 945GME Chipset
[    1.293570] agpgart-intel 0000:00:00.0: detected gtt size: 262144K total, 262144K mappable
[    1.293815] agpgart-intel 0000:00:00.0: detected 8192K stolen memory
[    1.294078] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0x40000000
[    1.298548] brd: module loaded
[    1.300921] loop: module loaded
[    1.301344] ata_piix 0000:00:1f.2: version 2.13
[    1.301377] ata_piix 0000:00:1f.2: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    1.301389] ata_piix 0000:00:1f.2: MAP [ P0 P2 IDE IDE ]
[    1.301462] ata_piix 0000:00:1f.2: setting latency timer to 64
[    1.302279] scsi0 : ata_piix
[    1.302516] scsi1 : ata_piix
[    1.304207] ata1: SATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0x60a0 irq 14
[    1.304215] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x60a8 irq 15
[    1.305485] Fixed MDIO Bus: probed
[    1.305556] tun: Universal TUN/TAP device driver, 1.6
[    1.305561] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    1.305752] PPP generic driver version 2.4.2
[    1.306061] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    1.306111] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.306153] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    1.306161] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    1.306305] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 1
[    1.306346] ehci_hcd 0000:00:1d.7: using broken periodic workaround
[    1.306365] ehci_hcd 0000:00:1d.7: debug port 1
[    1.310267] ehci_hcd 0000:00:1d.7: cache line size of 64 is not supported
[    1.310308] ehci_hcd 0000:00:1d.7: irq 16, io mem 0x58544400
[    1.324039] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    1.324399] hub 1-0:1.0: USB hub found
[    1.324412] hub 1-0:1.0: 8 ports detected
[    1.324611] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    1.324650] uhci_hcd: USB Universal Host Controller Interface driver
[    1.324704] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.324722] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    1.324730] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    1.324876] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    1.324921] uhci_hcd 0000:00:1d.0: irq 16, io base 0x00006080
[    1.325271] hub 2-0:1.0: USB hub found
[    1.325283] hub 2-0:1.0: 2 ports detected
[    1.325445] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    1.325462] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    1.325470] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    1.325610] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 3
[    1.325674] uhci_hcd 0000:00:1d.1: irq 17, io base 0x00006060
[    1.326031] hub 3-0:1.0: USB hub found
[    1.326043] hub 3-0:1.0: 2 ports detected
[    1.326197] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    1.326214] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    1.326222] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    1.326353] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 4
[    1.326414] uhci_hcd 0000:00:1d.2: irq 18, io base 0x00006040
[    1.326764] hub 4-0:1.0: USB hub found
[    1.326776] hub 4-0:1.0: 2 ports detected
[    1.326927] uhci_hcd 0000:00:1d.3: PCI INT D -> GSI 19 (level, low) -> IRQ 19
[    1.326944] uhci_hcd 0000:00:1d.3: setting latency timer to 64
[    1.326952] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[    1.327091] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 5
[    1.327161] uhci_hcd 0000:00:1d.3: irq 19, io base 0x00006020
[    1.327513] hub 5-0:1.0: USB hub found
[    1.327525] hub 5-0:1.0: 2 ports detected
[    1.327836] usbcore: registered new interface driver libusual
[    1.327944] i8042: PNP: PS/2 Controller [PNP0303:KBC,PNP0f13:MOUE] at 0x60,0x64 irq 1,12
[    1.329301] i8042: Warning: Keylock active
[    1.338754] i8042: Detected active multiplexing controller, rev 1.1
[    1.344583] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.344602] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[    1.344694] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[    1.344772] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[    1.344849] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[    1.345237] mousedev: PS/2 mouse device common for all mice
[    1.345841] rtc_cmos 00:03: RTC can wake from S4
[    1.346074] rtc_cmos 00:03: rtc core: registered rtc_cmos as rtc0
[    1.346124] rtc0: alarms up to one month, 242 bytes nvram, hpet irqs
[    1.346332] device-mapper: uevent: version 1.0.3
[    1.346542] device-mapper: ioctl: 4.22.0-ioctl (2011-10-19) initialised: [email]dm-devel@redhat.com[/email]
[    1.346644] EISA: Probing bus 0 at eisa.0
[    1.346651] EISA: Cannot allocate resource for mainboard
[    1.346658] Cannot allocate resource for EISA slot 1
[    1.346663] Cannot allocate resource for EISA slot 2
[    1.346669] Cannot allocate resource for EISA slot 3
[    1.346675] Cannot allocate resource for EISA slot 4
[    1.346680] Cannot allocate resource for EISA slot 5
[    1.346686] Cannot allocate resource for EISA slot 6
[    1.346691] Cannot allocate resource for EISA slot 7
[    1.346697] Cannot allocate resource for EISA slot 8
[    1.346702] EISA: Detected 0 cards.
[    1.346720] cpufreq-nforce2: No nForce2 chipset.
[    1.346900] cpuidle: using governor ladder
[    1.347198] cpuidle: using governor menu
[    1.347204] EFI Variables Facility v0.08 2004-May-17
[    1.347827] TCP cubic registered
[    1.348179] NET: Registered protocol family 10
[    1.349641] NET: Registered protocol family 17
[    1.349654] Registering the dns_resolver key type
[    1.349712] Using IPI No-Shortcut mode
[    1.350082] PM: Hibernation image not present or could not be loaded.
[    1.350111] registered taskstats version 1
[    1.367988]   Magic number: 4:415:34
[    1.368249] rtc_cmos 00:03: setting system clock to 2012-07-10 16:02:38 UTC (1341936158)
[    1.369020] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.369026] EDD information not available.
[    1.369382] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input4
[    1.476564] ata2.00: CFA: P-SSD1800, Ver2.Y0C, max UDMA/66
[    1.476573] ata2.00: 15761088 sectors, multi 0: LBA 
[    1.484446] ata2.00: configured for UDMA/66
[    1.484817] scsi 1:0:0:0: Direct-Access     ATA      P-SSD1800        Ver2 PQ: 0 ANSI: 5
[    1.485192] sd 1:0:0:0: [sda] 15761088 512-byte logical blocks: (8.06 GB/7.51 GiB)
[    1.485310] sd 1:0:0:0: Attached scsi generic sg0 type 0
[    1.485438] sd 1:0:0:0: [sda] Write Protect is off
[    1.485450] sd 1:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.485564] sd 1:0:0:0: [sda] Write cache: disabled, read cache: enabled, doesn't support DPO or FUA
[    1.488674]  sda: sda1 sda2 < sda5 >
[    1.489885] sd 1:0:0:0: [sda] Attached SCSI disk
[    1.489968] Freeing unused kernel memory: 712k freed
[    1.490634] Write protecting the kernel text: 5616k
[    1.490728] Write protecting the kernel read-only data: 2324k
[    1.539207] udevd[90]: starting version 175
[    1.636185] usb 1-5: new high-speed USB device number 2 using ehci_hcd
[    1.648811] [Firmware Bug]: battery: (dis)charge rate invalid.
[    1.707320] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/LNXVIDEO:00/input/input5
[    1.711736] ACPI: Video Device [OVGA] (multi-head: yes  rom: yes  post: no)
[    1.714228] wmi: Mapper loaded
[    1.855280] sdhci: Secure Digital Host Controller Interface driver
[    1.855290] sdhci: Copyright(c) Pierre Ossman
[    1.863779] sdhci-pci 0000:04:00.0: SDHCI controller found [197b:2382] (rev 0)
[    1.863822] sdhci-pci 0000:04:00.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    1.863916] sdhci-pci 0000:04:00.0: setting latency timer to 64
[    1.863945] mmc0: no vmmc regulator found
[    1.865320] [drm] Initialized drm 1.1.0 20060810
[    1.873608] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    1.873770] r8169 0000:02:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    1.875466] r8169 0000:02:00.0: setting latency timer to 64
[    1.875589] r8169 0000:02:00.0: irq 44 for MSI/MSI-X
[    1.880427] r8169 0000:02:00.0: eth0: RTL8102e at 0xf800e000, 00:23:8b:54:b5:f2, XID 04a00000 IRQ 44
[    1.887665] Registered led device: mmc0::
[    1.888825] mmc0: SDHCI controller on PCI [0000:04:00.0] using ADMA
[    1.888878] sdhci-pci 0000:04:00.2: SDHCI controller found [197b:2381] (rev 0)
[    1.888921] sdhci-pci 0000:04:00.2: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    1.888944] sdhci-pci 0000:04:00.2: Refusing to bind to secondary interface.
[    1.888963] sdhci-pci 0000:04:00.2: PCI INT A disabled
[    1.937340] i915 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.937356] i915 0000:00:02.0: setting latency timer to 64
[    2.032729] mtrr: no more MTRRs available
[    2.032739] [drm] MTRR allocation failed.  Graphics performance may suffer.
[    2.035245] [drm] Supports vblank timestamp caching Rev 1 (10.10.2010).
[    2.035254] [drm] Driver supports precise vblank timestamp query.
[    2.060997] vgaarb: device changed decodes: PCI:0000:00:02.0,olddecodes=io+mem,decodes=io+mem:owns=io+mem
[    2.305388] mmc0: new SDHC card at address b368
[    2.310587] mmcblk0: mmc0:b368 SDC   7.46 GiB 
[    2.314161]  mmcblk0: p1
[    2.400097] [drm] initialized overlay support
[    2.423296] fbcon: inteldrmfb (fb0) is primary device
[    2.423433] Console: switching to colour frame buffer device 128x37
[    2.423509] fb0: inteldrmfb frame buffer device
[    2.423516] drm: registered panic notifier
[    2.423562] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
[    9.468151] EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: (null)
[   13.625935] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   13.634425] udevd[373]: starting version 175
[   13.746013] lp: driver loaded but no devices found
[   13.783322] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
[   14.484548] ppdev: user-space parallel port driver
[   14.528046] Bluetooth: Core ver 2.16
[   14.528259] NET: Registered protocol family 31
[   14.528267] Bluetooth: HCI device and connection manager initialized
[   14.528276] Bluetooth: HCI socket layer initialized
[   14.528284] Bluetooth: L2CAP socket layer initialized
[   14.528308] Bluetooth: SCO socket layer initialized
[   14.581093] Bluetooth: RFCOMM TTY layer initialized
[   14.581113] Bluetooth: RFCOMM socket layer initialized
[   14.581120] Bluetooth: RFCOMM ver 1.11
[   14.593255] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   14.593265] Bluetooth: BNEP filters: protocol multicast
[   14.674536] type=1400 audit(1341936171.801:2): apparmor="STATUS" operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" pid=623 comm="apparmor_parser"
[   14.694475] type=1400 audit(1341936171.821:3): apparmor="STATUS" operation="profile_load" name="/usr/sbin/cupsd" pid=623 comm="apparmor_parser"
[   15.076308] jmb38x_ms 0000:04:00.3: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[   15.076329] jmb38x_ms 0000:04:00.3: setting latency timer to 64
[   15.086865] cfg80211: Calling CRDA to update world regulatory domain
[   15.165199] intel_rng: FWH not detected
[   15.231668] type=1400 audit(1341936172.357:4): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=662 comm="apparmor_parser"
[   15.248633] type=1400 audit(1341936172.377:5): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=662 comm="apparmor_parser"
[   15.249431] type=1400 audit(1341936172.377:6): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=662 comm="apparmor_parser"
[   15.253918] leds_ss4200: no LED devices found
[   15.417446] Linux video capture interface: v2.00
[   15.420243] uvcvideo: Found UVC 1.00 device USB 2.0 Camera (0c45:62c0)
[   15.440120] input: USB 2.0 Camera as /devices/pci0000:00/0000:00:1d.7/usb1/1-5/1-5:1.0/input/input6
[   15.440696] usbcore: registered new interface driver uvcvideo
[   15.440705] USB Video Class driver (1.1.1)
[   15.514904] ath5k 0000:03:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[   15.514930] ath5k 0000:03:00.0: setting latency timer to 64
[   15.515067] ath5k 0000:03:00.0: registered as 'phy0'
[   15.602584] snd_hda_intel 0000:00:1b.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   15.602972] snd_hda_intel 0000:00:1b.0: irq 45 for MSI/MSI-X
[   15.603036] snd_hda_intel 0000:00:1b.0: setting latency timer to 64
[   15.665975] input: HDA Intel Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input7
[   15.666480] input: HDA Intel Headphone as /devices/pci0000:00/0000:00:1b.0/sound/card0/input8
[   16.026781] ath: EEPROM regdomain: 0x65
[   16.026792] ath: EEPROM indicates we should expect a direct regpair map
[   16.026804] ath: Country alpha2 being used: 00
[   16.026810] ath: Regpair used: 0x65
[   16.026822] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
[   16.026832] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   16.026841] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
[   16.026852] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   16.026860] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
[   16.026871] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   16.026879] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
[   16.026889] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   16.026897] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
[   16.026906] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   16.026915] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
[   16.026926] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   16.026934] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
[   16.026943] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   16.026951] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
[   16.026962] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   16.026971] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
[   16.026981] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   16.026989] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
[   16.026999] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   16.027008] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
[   16.027017] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   16.027024] cfg80211: Updating information on frequency 2467 MHz for a 20 MHz width channel with regulatory rule:
[   16.027034] cfg80211: 2457000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   16.027042] cfg80211: Updating information on frequency 2472 MHz for a 20 MHz width channel with regulatory rule:
[   16.027052] cfg80211: 2457000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   16.027060] cfg80211: Disabling freq 2484 MHz as custom regd has no rule that fits a 20 MHz wide channel
[   16.027441] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain
[   16.041186] ieee80211 phy0: Selected rate control algorithm 'minstrel_ht'
[   16.044975] Registered led device: ath5k-phy0::rx
[   16.045148] Registered led device: ath5k-phy0::tx
[   16.045183] ath5k phy0: Atheros AR2425 chip found (MAC: 0xe2, PHY: 0x70)
[   16.059745] acerhdf: Acer Aspire One Fan driver, v.0.5.24
[   16.059762] acerhdf: Fan control off, to enable do:
[   16.059768] acerhdf: echo -n "enabled" > /sys/class/thermal/thermal_zone0/mode
[   16.541495] init: failsafe main process (757) killed by TERM signal
[   16.926240] acer_wmi: Acer Laptop ACPI-WMI Extras
[   16.926254] acer_wmi: Blacklisted hardware detected - not loading
[   16.927175] psmouse serio2: synaptics: Touchpad model: 1, fw: 7.2, id: 0x1c0b1, caps: 0xd04773/0xa40000/0xa0000
[   16.983453] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio2/input/input9
[   17.049479] type=1400 audit(1341936174.177:7): apparmor="STATUS" operation="profile_load" name="/usr/lib/lightdm/lightdm/lightdm-guest-session-wrapper" pid=882 comm="apparmor_parser"
[   17.057274] type=1400 audit(1341936174.185:8): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=883 comm="apparmor_parser"
[   17.064372] type=1400 audit(1341936174.193:9): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=883 comm="apparmor_parser"
[   17.065213] type=1400 audit(1341936174.193:10): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=883 comm="apparmor_parser"
[   17.103533] r8169 0000:02:00.0: eth0: link down
[   17.112626] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   17.114280] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   17.125466] type=1400 audit(1341936174.253:11): apparmor="STATUS" operation="profile_replace" name="/usr/lib/cups/backend/cups-pdf" pid=892 comm="apparmor_parser"
[   17.151663] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   17.153520] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   17.377328] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain
[   17.377341] cfg80211: World regulatory domain updated:
[   17.377348] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   17.377359] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   17.377369] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   17.377379] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   17.377388] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   17.377398] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)

---

### Post by rukiaEnix on 2012-07-10
Did you login to the console with your account or your son's account?

Also, can you login as root with console? If yes tell me to try other thing.

---

### Post by Toriam on 2012-07-10
My account. Thank you for helping me with this! I've run linux for many years but for some reason this is stumping me so bad.

---

### Post by rukiaEnix on 2012-07-10
OK, no problem!

Well, let's try this, maybe it looks like a stupid solution, but some time ago, I also had a problem login in with my account in graphic mode, and what I did was just erase my user (logged in as root obviously) and then I created it again.

You don't have to lose your info at your home directory, but to avoid risks just backup first your home directory and then proceed erasing the user.

---

### Post by Toriam on 2012-07-10
I tried erasing my son's account since it started after adding him, but for some reason it would make no changes. How should I go about this?

---

### Post by rukiaEnix on 2012-07-10
Did you try erasing it with root?

---

### Post by steeldriver on 2012-07-10
Before going that far I would first check the ownership / permissions on some things in your home dir - if these are not writable (by you) then your xsession cannot start:

```
ls -dl ~
``````
ls -l ~/.*authority
```

(run from the virtual terminal or console logged in as yourself)

---

### Post by Toriam on 2012-07-10
I

---

### Post by Toriam on 2012-07-10
Oops.

I think the biggest problem is I don't now how to log in as root. I see from searching that things have changed in that arena recently. So, I you're willing, I think I'll need some instruction in that area!

---

### Post by rukiaEnix on 2012-07-10
Log in with console.

When it prompts for login, type root.

Then it will ask for a password, type the root password.

But maybe you haven't set a password for root, so first try setting the password.

Log in with the user you can with console and set the root password like this:

```

sudo passwd root

```

---

### Post by Toriam on 2012-07-10
Here's my problem:

ittybittyblox@TheRainbowBus:~$ root
No command 'root' found, did you mean:
 Command 'rootv' from package 'xawtv' (universe)
 Command 'rott' from package 'rott' (multiverse)
 Command 'rbot' from package 'rbot' (universe)
root: command not found
ittybittyblox@TheRainbowBus:~$ sudo passwd root
[sudo] password for ittybittyblox: 
Sorry, try again.
[sudo] password for ittybittyblox: 
ittybittyblox is not in the sudoers file.  This incident will be reported.
ittybittyblox@TheRainbowBus:~$

---

### Post by Toriam on 2012-07-10
I solved it by playing around! 

I was in his account, set as desktop user and don't ask password. Mine was Admin also don't ask. I set both to admin and ask the password. So I guess the computer was insisting on a little more security?  Thanks for all your help and teaching me some things!:D

---

### Post by rukiaEnix on 2012-07-11
Then just change the thread to solved please! :p

---

