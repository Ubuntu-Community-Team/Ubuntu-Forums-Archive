---
title: "Painfully long boot time in Ubuntu 9.04"
date: 2009-09-20
forum: General Help
---

### Post by Rizqureshy on 2009-09-20
Hi,

I don't know if this is the right place to post it as i am new to both this forum and Ubuntu Desktop 9.04. This is the first time i have ever dared to step into the realm of open source community and truly amazed to see the stride it has take in the shape of Ubuntu 9.04.

Although the desktop experience is truly mesmerizing but the painfully long boot time and slow operating (opening/installing programs) is a pain in the neck.

My PC Specs are
Intel Pentium 4 HT 3.0 Ghz
1GB DDR ram
40.GB Seagate HDD

I suppose this is enough to run Ubuntu without lag as Windows 7 never gave me a hard time on the same machine. I have installed the Nvidia accelerated driver version 180. The Graphics and user interface pose no problem and runs liquid smooth. Disabling the eye candy make little impact over the system performance.

I hope if anyone could guide me about how to fix this constant lag. This is my first time with linux and i don't feel like going back to the Windows.

Thanks

---

### Post by mikewhatever on 2009-09-20
I suggest looking at the processes that might be using too much CPU first. System->Admin->System Monitor. You might want to show us too with the output of the 'top' command.

---

### Post by Peacefulpieofdeath on 2009-09-20
Can you restart your computer and tell us how long it takes in seconds (about) and also tell us where it stays the longest.

---

### Post by drs305 on 2009-09-20
Is the delay before or after you make a menu selection from Grub? Or both?

You can check this log file for the initial startup. It may be confusing, but if you look at the time column and see a long pause between events that could help find the problem.

System, Administration, Log File Viewer: dmesg

---

### Post by Rizqureshy on 2009-09-20
This is what i found in the log file u mentioned.

[    0.000000] BIOS EBDA/lowmem at: 0009f400/0009f400
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.28-15-generic (buildd@palmer) (gcc version 4.3.3 (Ubuntu 4.3.3-5ubuntu4) ) #49-Ubuntu SMP Tue Aug 18 18:40:08 UTC 2009 (Ubuntu 2.6.28-15.49-generic)
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
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f400 (usable)
[    0.000000]  BIOS-e820: 000000000009f400 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000003def0000 (usable)
[    0.000000]  BIOS-e820: 000000003def0000 - 000000003def3000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000003def3000 - 000000003df00000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 0000000100000000 (reserved)
[    0.000000] DMI 2.3 present.
[    0.000000] last_pfn = 0x3def0 max_arch_pfn = 0x100000
[    0.000000] Scanning 2 areas for low memory corruption
[    0.000000] modified physical RAM map:
[    0.000000]  modified: 0000000000000000 - 0000000000002000 (usable)
[    0.000000]  modified: 0000000000002000 - 0000000000006000 (reserved)
[    0.000000]  modified: 0000000000006000 - 0000000000007000 (usable)
[    0.000000]  modified: 0000000000007000 - 0000000000010000 (reserved)
[    0.000000]  modified: 0000000000010000 - 0000000000092400 (usable)
[    0.000000]  modified: 000000000009f400 - 00000000000a0000 (reserved)
[    0.000000]  modified: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  modified: 0000000000100000 - 000000003def0000 (usable)
[    0.000000]  modified: 000000003def0000 - 000000003def3000 (ACPI NVS)
[    0.000000]  modified: 000000003def3000 - 000000003df00000 (ACPI data)
[    0.000000]  modified: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  modified: 00000000fec00000 - 0000000100000000 (reserved)
[    0.000000] kernel direct mapping tables up to 373fe000 @ 10000-16000
[    0.000000] RAMDISK: 378b9000 - 37fef259
[    0.000000] Allocated new RAMDISK: 0087d000 - 00fb3259
[    0.000000] Move RAMDISK from 00000000378b9000 - 0000000037fef258 to 0087d000 - 00fb3258
[    0.000000] ACPI: RSDP 000F7D10, 0014 (r0 ATi   )
[    0.000000] ACPI: RSDT 3DEF3040, 0030 (r1 ATi    AWRDACPI 42302E31 AWRD        0)
[    0.000000] ACPI: FACP 3DEF30C0, 0074 (r1 ATi    AWRDACPI 42302E31 AWRD        0)
[    0.000000] ACPI: DSDT 3DEF3180, 3B02 (r1 ATI    AWRDACPI     1000 MSFT  100000E)
[    0.000000] ACPI: FACS 3DEF0000, 0040
[    0.000000] ACPI: MCFG 3DEF6E00, 003C (r1 ATi    AWRDACPI 42302E31 AWRD        0)
[    0.000000] ACPI: APIC 3DEF6D00, 0084 (r1 ATi    AWRDACPI 42302E31 AWRD        0)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] 106MB HIGHMEM available.
[    0.000000] 883MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 373fe000
[    0.000000]   low ram: 00000000 - 373fe000
[    0.000000]   bootmap 00012000 - 00018e80
[    0.000000] (9 early reservations) ==> bootmem [0000000000 - 00373fe000]
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
[    0.000000]   #1 [0000001000 - 0000002000]    EX TRAMPOLINE ==> [0000001000 - 0000002000]
[    0.000000]   #2 [0000006000 - 0000007000]       TRAMPOLINE ==> [0000006000 - 0000007000]
[    0.000000]   #3 [0000100000 - 00008780ac]    TEXT DATA BSS ==> [0000100000 - 00008780ac]
[    0.000000]   #4 [0000879000 - 000087d000]    INIT_PG_TABLE ==> [0000879000 - 000087d000]
[    0.000000]   #5 [000009f400 - 0000100000]    BIOS reserved ==> [000009f400 - 0000100000]
[    0.000000]   #6 [0000010000 - 0000012000]          PGTABLE ==> [0000010000 - 0000012000]
[    0.000000]   #7 [000087d000 - 0000fb3259]      NEW RAMDISK ==> [000087d000 - 0000fb3259]
[    0.000000]   #8 [0000012000 - 0000019000]          BOOTMAP ==> [0000012000 - 0000019000]
[    0.000000] found SMP MP-table at [c00f5e30] 000f5e30
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000000 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x000373fe
[    0.000000]   HighMem  0x000373fe -> 0x0003def0
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[4] active PFN ranges
[    0.000000]     0: 0x00000000 -> 0x00000002
[    0.000000]     0: 0x00000006 -> 0x00000007
[    0.000000]     0: 0x00000010 -> 0x00000092
[    0.000000]     0: 0x00000100 -> 0x0003def0
[    0.000000] On node 0 totalpages: 253557
[    0.000000] free_area_init_node: node 0, pgdat c06cb500, node_mem_map c1000000
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3941 pages, LIFO batch:0
[    0.000000]   Normal zone: 1736 pages used for memmap
[    0.000000]   Normal zone: 220470 pages, LIFO batch:31
[    0.000000]   HighMem zone: 214 pages used for memmap
[    0.000000]   HighMem zone: 27164 pages, LIFO batch:7
[    0.000000]   Movable zone: 0 pages used for memmap
[    0.000000] ACPI: PM-Timer IO Port: 0x4008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x02] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x03] disabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x02] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x03] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x04] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 4, version 33, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 low level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] SMP: Allowing 4 CPUs, 2 hotplug CPUs
[    0.000000] PM: Registered nosave memory: 0000000000002000 - 0000000000006000
[    0.000000] PM: Registered nosave memory: 0000000000007000 - 0000000000010000
[    0.000000] PM: Registered nosave memory: 0000000000092000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000f0000
[    0.000000] PM: Registered nosave memory: 00000000000f0000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 40000000 (gap: 3df00000:a2100000)
[    0.000000] PERCPU: Allocating 45056 bytes of per cpu data
[    0.000000] NR_CPUS: 64, nr_cpu_ids: 4, nr_node_ids 1
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 251575
[    0.000000] Kernel command line: root=UUID=a23f9704-325c-437c-813f-01aa61af366f ro quiet splash 
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 3066.527 MHz processor.
[    0.004000] Console: colour VGA+ 80x25
[    0.004000] console [tty0] enabled
[    0.004000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.004000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.004000] allocated 5073600 bytes of page_cgroup
[    0.004000] please try cgroup_disable=memory option if you don't want
[    0.004000] Scanning for low memory corruption every 60 seconds
[    0.004000] Memory: 984916k/1014720k available (4115k kernel code, 28972k reserved, 2199k data, 532k init, 109512k highmem)
[    0.004000] virtual kernel memory layout:
[    0.004000]     fixmap  : 0xffc77000 - 0xfffff000   (3616 kB)
[    0.004000]     pkmap   : 0xff400000 - 0xff800000   (4096 kB)
[    0.004000]     vmalloc : 0xf7bfe000 - 0xff3fe000   ( 120 MB)
[    0.004000]     lowmem  : 0xc0000000 - 0xf73fe000   ( 883 MB)
[    0.004000]       .init : 0xc0733000 - 0xc07b8000   ( 532 kB)
[    0.004000]       .data : 0xc0504f5f - 0xc072ae60   (2199 kB)
[    0.004000]       .text : 0xc0100000 - 0xc0504f5f   (4115 kB)
[    0.004000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.004000] SLUB: Genslabs=12, HWalign=128, Order=0-3, MinObjects=0, CPUs=4, Nodes=1
[    0.004015] Calibrating delay loop (skipped), value calculated using timer frequency.. 6133.05 BogoMIPS (lpj=12266108)
[    0.004040] Security Framework initialized
[    0.004052] SELinux:  Disabled at boot.
[    0.004077] AppArmor: AppArmor initialized
[    0.004090] Mount-cache hash table entries: 512
[    0.004305] Initializing cgroup subsys ns
[    0.004312] Initializing cgroup subsys cpuacct
[    0.004316] Initializing cgroup subsys memory
[    0.004322] Initializing cgroup subsys freezer
[    0.004347] CPU: Trace cache: 12K uops, L1 D cache: 16K
[    0.004350] CPU: L2 cache: 1024K
[    0.004354] CPU: Physical Processor ID: 0
[    0.004356] CPU: Processor Core ID: 0
[    0.004361] using mwait in idle threads.
[    0.004379] Checking 'hlt' instruction... OK.
[    0.023613] ACPI: Core revision 20080926
[    0.026683] ACPI: Checking initramfs for custom DSDT
[    0.308605] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.350206] CPU0: Intel(R) Pentium(R) 4 CPU 3.06GHz stepping 09
[    0.352001] Booting processor 1 APIC 0x1 ip 0x6000
[    0.004000] Initializing CPU#1
[    0.004000] Calibrating delay using timer specific routine.. 6133.89 BogoMIPS (lpj=12267785)
[    0.004000] CPU: Trace cache: 12K uops, L1 D cache: 16K
[    0.004000] CPU: L2 cache: 1024K
[    0.004000] CPU: Physical Processor ID: 0
[    0.004000] CPU: Processor Core ID: 0
[    0.440403] CPU1: Intel(R) Pentium(R) 4 CPU 3.06GHz stepping 09
[    0.440432] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
[    0.444067] Brought up 2 CPUs
[    0.444072] Total of 2 processors activated (12266.94 BogoMIPS).
[    0.444129] CPU0 attaching sched-domain:
[    0.444133]  domain 0: span 0-1 level SIBLING
[    0.444136]   groups: 0 1
[    0.444145] CPU1 attaching sched-domain:
[    0.444147]  domain 0: span 0-1 level SIBLING
[    0.444150]   groups: 1 0
[    0.444250] net_namespace: 776 bytes
[    0.444250] Booting paravirtualized kernel on bare hardware
[    0.444467] Time: 19:35:40  Date: 09/20/09
[    0.444467] regulator: core version 0.5
[    0.444467] NET: Registered protocol family 16
[    0.444467] EISA bus registered
[    0.444467] ACPI: bus type pci registered
[    0.444467] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 255
[    0.444467] PCI: MCFG area at e0000000 reserved in E820
[    0.444467] PCI: Using MMCONFIG for extended config space
[    0.444467] PCI: Using configuration type 1 for base access
[    0.445516] ACPI: EC: Look up EC in DSDT
[    0.454139] ACPI: Interpreter enabled
[    0.454146] ACPI: (supports S0 S1 S4 S5)
[    0.454174] ACPI: Using IOAPIC for interrupt routing
[    0.458810] ACPI: No dock devices found.
[    0.458827] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.458895] pci 0000:00:00.0: reg 1c 64bit mmio: [0xe0000000-0xffffffff]
[    0.458952] pci 0000:00:02.0: PME# supported from D0 D3hot D3cold
[    0.458956] pci 0000:00:02.0: PME# disabled
[    0.459061] pci 0000:00:11.0: reg 10 io port: [0xff00-0xff07]
[    0.459072] pci 0000:00:11.0: reg 14 io port: [0xfe00-0xfe03]
[    0.459083] pci 0000:00:11.0: reg 18 io port: [0xfd00-0xfd07]
[    0.459094] pci 0000:00:11.0: reg 1c io port: [0xfc00-0xfc03]
[    0.459105] pci 0000:00:11.0: reg 20 io port: [0xfb00-0xfb0f]
[    0.459116] pci 0000:00:11.0: reg 24 32bit mmio: [0xfe02f000-0xfe02f1ff]
[    0.459127] pci 0000:00:11.0: reg 30 32bit mmio: [0xfdf80000-0xfdffffff]
[    0.459146] pci 0000:00:11.0: supports D1 D2
[    0.459220] pci 0000:00:12.0: reg 10 io port: [0xfa00-0xfa07]
[    0.459231] pci 0000:00:12.0: reg 14 io port: [0xf900-0xf903]
[    0.459242] pci 0000:00:12.0: reg 18 io port: [0xf800-0xf807]
[    0.459253] pci 0000:00:12.0: reg 1c io port: [0xf700-0xf703]
[    0.459264] pci 0000:00:12.0: reg 20 io port: [0xf600-0xf60f]
[    0.459275] pci 0000:00:12.0: reg 24 32bit mmio: [0xfe02e000-0xfe02e1ff]
[    0.459286] pci 0000:00:12.0: reg 30 32bit mmio: [0xfdf80000-0xfdffffff]
[    0.459304] pci 0000:00:12.0: supports D1 D2
[    0.459366] pci 0000:00:13.0: reg 10 32bit mmio: [0xfe02d000-0xfe02dfff]
[    0.459490] pci 0000:00:13.1: reg 10 32bit mmio: [0xfe02c000-0xfe02cfff]
[    0.459626] pci 0000:00:13.2: reg 10 32bit mmio: [0xfe02b000-0xfe02bfff]
[    0.459693] pci 0000:00:13.2: supports D1 D2
[    0.459695] pci 0000:00:13.2: PME# supported from D0 D1 D2 D3hot
[    0.459702] pci 0000:00:13.2: PME# disabled
[    0.459753] pci 0000:00:14.0: reg 10 io port: [0xb00-0xb0f]
[    0.459764] pci 0000:00:14.0: reg 14 32bit mmio: [0xfe02a000-0xfe02a3ff]
[    0.459813] HPET not enabled in BIOS. You might try hpet=force boot option
[    0.459867] pci 0000:00:14.1: reg 10 io port: [0x00-0x07]
[    0.459878] pci 0000:00:14.1: reg 14 io port: [0x00-0x03]
[    0.459889] pci 0000:00:14.1: reg 18 io port: [0x00-0x07]
[    0.459900] pci 0000:00:14.1: reg 1c io port: [0x00-0x03]
[    0.459911] pci 0000:00:14.1: reg 20 io port: [0xf400-0xf40f]
[    0.460040] pci 0000:00:14.2: reg 10 64bit mmio: [0xfe024000-0xfe027fff]
[    0.460100] pci 0000:00:14.2: PME# supported from D0 D3hot D3cold
[    0.460106] pci 0000:00:14.2: PME# disabled
[    0.460325] pci 0000:01:00.0: reg 10 32bit mmio: [0xfa000000-0xfaffffff]
[    0.460339] pci 0000:01:00.0: reg 14 64bit mmio: [0xd0000000-0xdfffffff]
[    0.460352] pci 0000:01:00.0: reg 1c 64bit mmio: [0xf8000000-0xf9ffffff]
[    0.460361] pci 0000:01:00.0: reg 24 io port: [0xef00-0xef7f]
[    0.460369] pci 0000:01:00.0: reg 30 32bit mmio: [0xfbf80000-0xfbffffff]
[    0.460468] pci 0000:00:02.0: bridge io port: [0xe000-0xefff]
[    0.460472] pci 0000:00:02.0: bridge 32bit mmio: [0xf8000000-0xfbffffff]
[    0.460480] pci 0000:00:02.0: bridge 64bit mmio pref: [0xd0000000-0xdfffffff]
[    0.460553] pci 0000:02:02.0: reg 10 io port: [0xde00-0xdeff]
[    0.460567] pci 0000:02:02.0: reg 14 32bit mmio: [0xfddff000-0xfddff0ff]
[    0.460635] pci 0000:02:02.0: supports D1 D2
[    0.460638] pci 0000:02:02.0: PME# supported from D1 D2 D3hot D3cold
[    0.460645] pci 0000:02:02.0: PME# disabled
[    0.460719] pci 0000:02:04.0: reg 10 32bit mmio: [0xfddf0000-0xfddf7fff]
[    0.460877] pci 0000:00:14.4: transparent bridge
[    0.460888] pci 0000:00:14.4: bridge io port: [0xd000-0xdfff]
[    0.460895] pci 0000:00:14.4: bridge 32bit mmio: [0xfdd00000-0xfddfffff]
[    0.460903] pci 0000:00:14.4: bridge 32bit mmio pref: [0xfde00000-0xfdefffff]
[    0.460921] bus 00 -> node 0
[    0.460929] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.461285] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P2P_._PRT]
[    0.471704] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 10 11) *0, disabled.
[    0.471855] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 10 11) *0, disabled.
[    0.472020] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 10 11) *0, disabled.
[    0.472168] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 10 11) *0, disabled.
[    0.472315] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 10 11) *0, disabled.
[    0.472461] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 *5 6 7 10 11)
[    0.472611] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 10 *11)
[    0.472757] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 *10 11)
[    0.472940] ACPI: WMI: Mapper loaded
[    0.473015] SCSI subsystem initialized
[    0.473015] libata version 3.00 loaded.
[    0.473015] usbcore: registered new interface driver usbfs
[    0.473015] usbcore: registered new interface driver hub
[    0.473015] usbcore: registered new device driver usb
[    0.473015] PCI: Using ACPI for IRQ routing
[    0.473015] pci 0000:00:00.0: BAR 3: can't allocate resource
[    0.480015] Bluetooth: Core ver 2.13
[    0.480035] NET: Registered protocol family 31
[    0.480035] Bluetooth: HCI device and connection manager initialized
[    0.480035] Bluetooth: HCI socket layer initialized
[    0.480035] NET: Registered protocol family 8
[    0.480035] NET: Registered protocol family 20
[    0.480049] NetLabel: Initializing
[    0.480052] NetLabel:  domain hash size = 128
[    0.480054] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.480072] NetLabel:  unlabeled traffic allowed by default
[    0.480183] AppArmor: AppArmor Filesystem Enabled
[    0.484016] pnp: PnP ACPI init
[    0.484030] ACPI: bus type pnp registered
[    0.487546] pnp 00:0b: mem resource (0xd0000-0xd3fff) overlaps 0000:00:00.0 BAR 3 (0x0-0x1fffffff), disabling
[    0.487552] pnp 00:0b: mem resource (0xf0000-0xf7fff) overlaps 0000:00:00.0 BAR 3 (0x0-0x1fffffff), disabling
[    0.487555] pnp 00:0b: mem resource (0xf8000-0xfbfff) overlaps 0000:00:00.0 BAR 3 (0x0-0x1fffffff), disabling
[    0.487559] pnp 00:0b: mem resource (0xfc000-0xfffff) overlaps 0000:00:00.0 BAR 3 (0x0-0x1fffffff), disabling
[    0.487563] pnp 00:0b: mem resource (0x0-0x9ffff) overlaps 0000:00:00.0 BAR 3 (0x0-0x1fffffff), disabling
[    0.487566] pnp 00:0b: mem resource (0x100000-0x3deeffff) overlaps 0000:00:00.0 BAR 3 (0x0-0x1fffffff), disabling
[    0.487646] pnp: PnP ACPI: found 12 devices
[    0.487648] ACPI: ACPI bus type pnp unregistered
[    0.487654] PnPBIOS: Disabled by ACPI PNP
[    0.487666] system 00:01: ioport range 0x228-0x22f has been reserved
[    0.487669] system 00:01: ioport range 0x40b-0x40b has been reserved
[    0.487672] system 00:01: ioport range 0x4d6-0x4d6 has been reserved
[    0.487675] system 00:01: ioport range 0xc00-0xc01 has been reserved
[    0.487678] system 00:01: ioport range 0xc14-0xc14 has been reserved
[    0.487681] system 00:01: ioport range 0xc50-0xc52 has been reserved
[    0.487684] system 00:01: ioport range 0xc6c-0xc6d has been reserved
[    0.487687] system 00:01: ioport range 0xc6f-0xc6f has been reserved
[    0.487689] system 00:01: ioport range 0xcd4-0xcdf has been reserved
[    0.487692] system 00:01: ioport range 0x4000-0x40fe has been reserved
[    0.487695] system 00:01: ioport range 0x4210-0x4217 has been reserved
[    0.487706] system 00:06: ioport range 0x4d0-0x4d1 has been reserved
[    0.487710] system 00:06: ioport range 0x800-0x87f has been reserved
[    0.487712] system 00:06: ioport range 0x880-0x88f has been reserved
[    0.487722] system 00:0a: iomem range 0xe0000000-0xefffffff has been reserved
[    0.487730] system 00:0b: iomem range 0x3df00000-0x3dffffff has been reserved
[    0.487734] system 00:0b: iomem range 0x3def0000-0x3defffff could not be reserved
[    0.487737] system 00:0b: iomem range 0xffff0000-0xffffffff has been reserved
[    0.487741] system 00:0b: iomem range 0xfec00000-0xfec00fff has been reserved
[    0.487744] system 00:0b: iomem range 0xfee00000-0xfee00fff has been reserved
[    0.487747] system 00:0b: iomem range 0xfff80000-0xfffeffff has been reserved
[    0.522543] pci 0000:00:02.0: PCI bridge, secondary bus 0000:01
[    0.522547] pci 0000:00:02.0:   IO window: 0xe000-0xefff
[    0.522553] pci 0000:00:02.0:   MEM window: 0xf8000000-0xfbffffff
[    0.522558] pci 0000:00:02.0:   PREFETCH window: 0x000000d0000000-0x000000dfffffff
[    0.522565] pci 0000:00:14.4: PCI bridge, secondary bus 0000:02
[    0.522569] pci 0000:00:14.4:   IO window: 0xd000-0xdfff
[    0.522578] pci 0000:00:14.4:   MEM window: 0xfdd00000-0xfddfffff
[    0.522584] pci 0000:00:14.4:   PREFETCH window: 0x000000fde00000-0x000000fdefffff
[    0.522604] pci 0000:00:02.0: setting latency timer to 64
[    0.522617] bus: 00 index 0 io port: [0x00-0xffff]
[    0.522620] bus: 00 index 1 mmio: [0x000000-0xffffffff]
[    0.522622] bus: 01 index 0 io port: [0xe000-0xefff]
[    0.522625] bus: 01 index 1 mmio: [0xf8000000-0xfbffffff]
[    0.522627] bus: 01 index 2 mmio: [0xd0000000-0xdfffffff]
[    0.522630] bus: 01 index 3 mmio: [0x0-0x0]
[    0.522632] bus: 02 index 0 io port: [0xd000-0xdfff]
[    0.522635] bus: 02 index 1 mmio: [0xfdd00000-0xfddfffff]
[    0.522637] bus: 02 index 2 mmio: [0xfde00000-0xfdefffff]
[    0.522640] bus: 02 index 3 io port: [0x00-0xffff]
[    0.522642] bus: 02 index 4 mmio: [0x000000-0xffffffff]
[    0.522651] NET: Registered protocol family 2
[    0.536146] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.536552] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.537351] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.538063] TCP: Hash tables configured (established 131072 bind 65536)
[    0.538066] TCP reno registered
[    0.544270] NET: Registered protocol family 1
[    0.544449] checking if image is initramfs... it is
[    1.020659] Switched to high resolution mode on CPU 1
[    1.024153] Switched to high resolution mode on CPU 0
[    1.130745] Freeing initrd memory: 7384k freed
[    1.131059] cpufreq: No nForce2 chipset.
[    1.131259] audit: initializing netlink socket (disabled)
[    1.131301] type=2000 audit(1253475341.128:1): initialized
[    1.139142] highmem bounce pool size: 64 pages
[    1.139149] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    1.140753] VFS: Disk quotas dquot_6.5.1
[    1.140832] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    1.141616] fuse init (API version 7.10)
[    1.141724] msgmni has been set to 1724
[    1.141963] alg: No test for stdrng (krng)
[    1.141993] io scheduler noop registered
[    1.141998] io scheduler anticipatory registered
[    1.142002] io scheduler deadline registered
[    1.142027] io scheduler cfq registered (default)
[    1.142040] pci 0000:00:00.0: MSI quirk detected; MSI disabled
[    1.220088] pci 0000:01:00.0: Boot video device
[    1.220182] pcieport-driver 0000:00:02.0: setting latency timer to 64
[    1.220230] pcieport-driver 0000:00:02.0: found MSI capability
[    1.220234] pci_express 0000:00:02.0:pcie00: allocate port service
[    1.220255] pci_express 0000:00:02.0:pcie01: allocate port service
[    1.220274] pci_express 0000:00:02.0:pcie03: allocate port service
[    1.221545] aer 0000:00:02.0:pcie01: AER service couldn't init device: no _OSC support
[    1.221562] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    1.221576] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    1.221753] input: Power Button (FF) as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input0
[    1.221756] ACPI: Power Button (FF) [PWRF]
[    1.221814] input: Power Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1
[    1.221817] ACPI: Power Button (CM) [PWRB]
[    1.221888] fan PNP0C0B:00: registered as cooling_device0
[    1.221896] ACPI: Fan [FAN] (on)
[    1.222152] processor ACPI_CPU:00: registered as cooling_device1
[    1.222157] ACPI: Processor [CPU0] (supports 8 throttling states)
[    1.222265] processor ACPI_CPU:01: registered as cooling_device2
[    1.222271] ACPI: Processor [CPU1] (supports 8 throttling states)
[    1.224847] thermal LNXTHERM:01: registered as thermal_zone0
[    1.226146] ACPI: Thermal Zone [THRM] (40 C)
[    1.226208] isapnp: Scanning for PnP cards...
[    1.577917] isapnp: No Plug & Play device found
[    1.584693] Serial: 8250/16550 driver4 ports, IRQ sharing enabled
[    1.584839] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    1.585306] 00:07: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    1.586382] brd: module loaded
[    1.586840] loop: module loaded
[    1.586936] Fixed MDIO Bus: probed
[    1.586943] PPP generic driver version 2.4.2
[    1.587020] input: Macintosh mouse button emulation as /devices/virtual/input/input2
[    1.587061] Driver 'sd' needs updating - please use bus_type methods
[    1.587073] Driver 'sr' needs updating - please use bus_type methods
[    1.587200] sata_sil 0000:00:11.0: version 2.3
[    1.587270] sata_sil 0000:00:11.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    1.587426] scsi0 : sata_sil
[    1.587570] scsi1 : sata_sil
[    1.587769] ata1: SATA max UDMA/100 mmio m512@0xfe02f000 tf 0xfe02f080 irq 23
[    1.587774] ata2: SATA max UDMA/100 mmio m512@0xfe02f000 tf 0xfe02f0c0 irq 23
[    1.904042] ata1: SATA link down (SStatus 0 SControl 310)
[    2.224041] ata2: SATA link down (SStatus 0 SControl 310)
[    2.224111] sata_sil 0000:00:12.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[    2.224206] scsi2 : sata_sil
[    2.224293] scsi3 : sata_sil
[    2.224467] ata3: SATA max UDMA/100 mmio m512@0xfe02e000 tf 0xfe02e080 irq 22
[    2.224472] ata4: SATA max UDMA/100 mmio m512@0xfe02e000 tf 0xfe02e0c0 irq 22
[    2.544042] ata3: SATA link down (SStatus 0 SControl 310)
[    2.864040] ata4: SATA link down (SStatus 0 SControl 310)
[    2.864283] pata_atiixp 0000:00:14.1: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    2.864431] scsi4 : pata_atiixp
[    2.864519] scsi5 : pata_atiixp
[    2.866037] ata5: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xf400 irq 14
[    2.866041] ata6: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xf408 irq 15
[    3.028813] ata5.00: ATA-6: ST340015A, 3.01, max UDMA/100
[    3.028816] ata5.00: 78165360 sectors, multi 1: LBA 
[    3.044751] ata5.00: configured for UDMA/100
[    3.232588] ata6.00: ATAPI: SONY    CD-RW  CRX320EE, RYK4, max UDMA/33
[    3.232860] ata6.01: native sectors (78165359) is smaller than sectors (78165360)
[    3.232865] ata6.01: ATA-5: ST340823A, 3.39, max UDMA/100
[    3.232868] ata6.01: 78165360 sectors, multi 1: LBA 
[    3.264586] ata6.00: configured for UDMA/33
[    3.280751] ata6.01: configured for UDMA/100
[    3.281613] scsi 4:0:0:0: Direct-Access     ATA      ST340015A        3.01 PQ: 0 ANSI: 5
[    3.281751] sd 4:0:0:0: [sda] 78165360 512-byte hardware sectors: (40.0 GB/37.2 GiB)
[    3.281775] sd 4:0:0:0: [sda] Write Protect is off
[    3.281779] sd 4:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    3.281815] sd 4:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    3.281913] sd 4:0:0:0: [sda] 78165360 512-byte hardware sectors: (40.0 GB/37.2 GiB)
[    3.281933] sd 4:0:0:0: [sda] Write Protect is off
[    3.281937] sd 4:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    3.281971] sd 4:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    3.281976]  sda: sda1 sda2 sda3
[    3.311724] sd 4:0:0:0: [sda] Attached SCSI disk
[    3.311803] sd 4:0:0:0: Attached scsi generic sg0 type 0
[    3.313070] scsi 5:0:0:0: CD-ROM            SONY     CD-RW  CRX320EE  RYK4 PQ: 0 ANSI: 5
[    3.315936] sr0: scsi3-mmc drive: 31x/62x writer cd/rw xa/form2 cdda tray
[    3.315940] Uniform CD-ROM driver Revision: 3.20
[    3.316082] sr 5:0:0:0: Attached scsi CD-ROM sr0
[    3.316130] sr 5:0:0:0: Attached scsi generic sg1 type 5
[    3.316221] scsi 5:0:1:0: Direct-Access     ATA      ST340823A        3.39 PQ: 0 ANSI: 5
[    3.316336] sd 5:0:1:0: [sdb] 78165360 512-byte hardware sectors: (40.0 GB/37.2 GiB)
[    3.316357] sd 5:0:1:0: [sdb] Write Protect is off
[    3.316361] sd 5:0:1:0: [sdb] Mode Sense: 00 3a 00 00
[    3.316396] sd 5:0:1:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    3.316464] sd 5:0:1:0: [sdb] 78165360 512-byte hardware sectors: (40.0 GB/37.2 GiB)
[    3.316484] sd 5:0:1:0: [sdb] Write Protect is off
[    3.316488] sd 5:0:1:0: [sdb] Mode Sense: 00 3a 00 00
[    3.316527] sd 5:0:1:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    3.316532]  sdb: sdb1 sdb2 < sdb5 sdb6 sdb7 >
[    3.366641] sd 5:0:1:0: [sdb] Attached SCSI disk
[    3.366694] sd 5:0:1:0: Attached scsi generic sg2 type 0
[    3.367264] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    3.367299] ehci_hcd 0000:00:13.2: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    3.367326] ehci_hcd 0000:00:13.2: EHCI Host Controller
[    3.367420] ehci_hcd 0000:00:13.2: new USB bus registered, assigned bus number 1
[    3.367499] ehci_hcd 0000:00:13.2: irq 19, io mem 0xfe02b000
[    3.376025] ehci_hcd 0000:00:13.2: USB 2.0 started, EHCI 1.00
[    3.376132] usb usb1: configuration #1 chosen from 1 choice
[    3.376169] hub 1-0:1.0: USB hub found
[    3.376180] hub 1-0:1.0: 8 ports detected
[    3.376339] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    3.376358] ohci_hcd 0000:00:13.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    3.376375] ohci_hcd 0000:00:13.0: OHCI Host Controller
[    3.376433] ohci_hcd 0000:00:13.0: new USB bus registered, assigned bus number 2
[    3.376456] ohci_hcd 0000:00:13.0: irq 19, io mem 0xfe02d000
[    3.436083] usb usb2: configuration #1 chosen from 1 choice
[    3.436126] hub 2-0:1.0: USB hub found
[    3.436141] hub 2-0:1.0: 4 ports detected
[    3.436259] ohci_hcd 0000:00:13.1: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    3.436274] ohci_hcd 0000:00:13.1: OHCI Host Controller
[    3.436328] ohci_hcd 0000:00:13.1: new USB bus registered, assigned bus number 3
[    3.436349] ohci_hcd 0000:00:13.1: irq 19, io mem 0xfe02c000
[    3.496074] usb usb3: configuration #1 chosen from 1 choice
[    3.496108] hub 3-0:1.0: USB hub found
[    3.496124] hub 3-0:1.0: 4 ports detected
[    3.496243] uhci_hcd: USB Universal Host Controller Interface driver
[    3.496354] PNP: PS/2 Controller [PNP0f13:PS2M] at 0x60,0x64 irq 12
[    3.496357] PNP: PS/2 controller doesn't have KBD irq; using default 1
[    3.498772] serio: i8042 KBD port at 0x60,0x64 irq 1
[    3.498781] serio: i8042 AUX port at 0x60,0x64 irq 12
[    3.500065] mice: PS/2 mouse device common for all mice
[    3.512117] rtc_cmos 00:03: RTC can wake from S4
[    3.512168] rtc_cmos 00:03: rtc core: registered rtc_cmos as rtc0
[    3.512202] rtc0: alarms up to one month, 242 bytes nvram
[    3.512280] device-mapper: uevent: version 1.0.3
[    3.512422] device-mapper: ioctl: 4.14.0-ioctl (2008-04-23) initialised: [email]dm-devel@redhat.com[/email]
[    3.512562] device-mapper: multipath: version 1.0.5 loaded
[    3.512568] device-mapper: multipath round-robin: version 1.0.0 loaded
[    3.512675] EISA: Probing bus 0 at eisa.0
[    3.512700] Cannot allocate resource for EISA slot 4
[    3.512723] EISA: Detected 0 cards.
[    3.512798] cpuidle: using governor ladder
[    3.512802] cpuidle: using governor menu
[    3.513490] TCP cubic registered
[    3.513585] NET: Registered protocol family 10
[    3.514166] lo: Disabled Privacy Extensions
[    3.514603] NET: Registered protocol family 17
[    3.514630] Bluetooth: L2CAP ver 2.11
[    3.514633] Bluetooth: L2CAP socket layer initialized
[    3.514636] Bluetooth: SCO (Voice Link) ver 0.6
[    3.514638] Bluetooth: SCO socket layer initialized
[    3.514687] Bluetooth: RFCOMM socket layer initialized
[    3.514700] Bluetooth: RFCOMM TTY layer initialized
[    3.514703] Bluetooth: RFCOMM ver 1.10
[    3.514777] Using IPI No-Shortcut mode
[    3.514895] registered taskstats version 1
[    3.515047]   Magic number: 9:566:597
[    3.515165] rtc_cmos 00:03: setting system clock to 2009-09-20 19:35:43 UTC (1253475343)
[    3.515170] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    3.515172] EDD information not available.
[    3.515766] Freeing unused kernel memory: 532k freed
[    3.515923] Write protecting the kernel text: 4116k
[    3.515980] Write protecting the kernel read-only data: 1528k
[    3.889134] 8139cp: 10/100 PCI Ethernet driver v1.3 (Mar 22, 2004)
[    3.889187] 8139cp 0000:02:02.0: This (id 10ec:8139 rev 10) is not an 8139C+ compatible chip, use 8139too
[    3.893897] 8139too Fast Ethernet driver 0.9.28
[    3.894003] 8139too 0000:02:02.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[    3.896334] eth0: RealTek RTL8139 at 0xde00, 00:16:76:8e:40:fc, IRQ 21
[    3.896339] eth0:  Identified 8139 chip type 'RTL-8101'
[    4.052678] usb 2-1: new full speed USB device using ohci_hcd and address 2
[    4.270268] usb 2-1: configuration #1 chosen from 1 choice
[    4.576036] usb 3-1: new low speed USB device using ohci_hcd and address 2
[    4.785687] usb 3-1: configuration #1 chosen from 1 choice
[    4.797334] usbcore: registered new interface driver hiddev
[    4.802605] input: Dell Dell USB Keyboard as /devices/pci0000:00/0000:00:13.1/usb3/3-1/3-1:1.0/input/input3
[    4.802876] generic-usb 0003:413C:2003.0001: input,hidraw0: USB HID v1.10 Keyboard [Dell Dell USB Keyboard] on usb-0000:00:13.1-1/input0
[    4.802912] usbcore: registered new interface driver usbhid
[    4.802917] usbhid: v2.6:USB HID core driver
[   14.398015] PM: Starting manual resume from disk
[   14.398020] PM: Resume from partition 8:21
[   14.398022] PM: Checking hibernation image.
[   14.398289] PM: Resume from disk failed.
[   14.454608] kjournald starting.  Commit interval 5 seconds
[   14.454619] EXT3-fs: mounted filesystem with ordered data mode.
[  100.862518] udev: starting version 141
[  105.834166] Linux agpgart interface v0.103
[  107.114695] parport_pc 00:08: reported by Plug and Play ACPI
[  107.114789] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
[  111.747597] ACPI: I/O resource piix4_smbus [0xb00-0xb07] conflicts with ACPI region SM00 [0xb00-0xb07]
[  111.747605] ACPI: Device needs an ACPI driver
[  111.747618] piix4_smbus 0000:00:14.0: SMBus Host Controller at 0xb00, revision 0
[  111.756044] input: PC Speaker as /devices/platform/pcspkr/input/input4
[  112.425150] ppdev: user-space parallel port driver
[  135.133596] nvidia: module license 'NVIDIA' taints kernel.
[  135.390390] nvidia 0000:01:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[  135.390406] nvidia 0000:01:00.0: setting latency timer to 64
[  135.391448] NVRM: loading NVIDIA UNIX x86 Kernel Module  180.44  Mon Mar 23 14:59:10 PST 2009
[  135.865276] cfg80211: Calling CRDA to update world regulatory domain
[  135.948580] synaptics was reset on resume, see synaptics_resume_reset if you have trouble on resume
[  136.434319] Registered led device: xpad0
[  136.434478] input: Microsoft X-Box 360 pad as /devices/pci0000:00/0000:00:13.0/usb2/2-1/2-1:1.0/input/input5
[  136.438228] usbcore: registered new interface driver xpad
[  136.438279] xpad: X-Box pad driver
[  136.464930] psmouse serio1: ID: 10 00 64<6>input: ImPS/2 Generic Wheel Mouse as /devices/platform/i8042/serio1/input/input6
[  137.581024] rt61pci 0000:02:04.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[  137.592051] phy0: Selected rate control algorithm 'pid'
[  137.698235] Registered led device: rt61pci-phy0:radio
[  137.698272] Registered led device: rt61pci-phy0:assoc
[  137.899532] HDA Intel 0000:00:14.2: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[  138.408643] lp0: using parport0 (interrupt-driven).
[  139.016876] Adding 1646620k swap on /dev/sdb5.  Priority:-1 extents:1 across:1646620k
[  140.154835] EXT3 FS on sdb7, internal journal
[  141.607314] kjournald starting.  Commit interval 5 seconds
[  141.661990] EXT3 FS on sdb6, internal journal
[  141.662005] EXT3-fs: mounted filesystem with ordered data mode.
[  148.183637] type=1505 audit(1253475488.164:2): operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" name2="default" pid=1935
[  148.237079] type=1505 audit(1253475488.220:3): operation="profile_load" name="/sbin/dhclient-script" name2="default" pid=1939
[  148.237300] type=1505 audit(1253475488.220:4): operation="profile_load" name="/sbin/dhclient3" name2="default" pid=1939
[  148.237363] type=1505 audit(1253475488.220:5): operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" name2="default" pid=1939
[  148.237412] type=1505 audit(1253475488.220:6): operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" name2="default" pid=1939
[  148.388439] type=1505 audit(1253475488.372:7): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=1944
[  148.388781] type=1505 audit(1253475488.372:8): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=1944
[  148.422908] type=1505 audit(1253475488.404:9): operation="profile_load" name="/usr/sbin/tcpdump" name2="default" pid=1948
[  202.545192] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[  202.545199] Bluetooth: BNEP filters: protocol multicast
[  202.764462] Bridge firewalling registered

---

### Post by Rizqureshy on 2009-09-20
My MSN id is :  [email]rizqureshy@hotmail.com[/email]

if anyone could please add me and help me out

---

### Post by ajgreeny on 2009-09-20
For the boot time check, next time you boot, choose the ubuntu you want from the grub menu and hit "E" to edit, scroll down to the second line which starts "kernel" and hit "E" again.  Now scroll to the end of the line and delete the words "usplash quiet" from the end.  Hit enter to accept the edit and then "B" to boot.  You will now see all the text that is usually hidden by the splash screen, and it may show you, or give you a clue about where the delay comes.

Next boot, everything will be back to normal with your splash; don't worry about the change being permanent.

---

### Post by Rizqureshy on 2009-09-20
It says something like

Loading files necessary to boot (Stage one)

Loads HAL, Driver something something. takes time

then the says

Loading files necessary to boot (Stage)

then loads a lot of things.

---

### Post by Rizqureshy on 2009-09-20
Actually it takes about 7 minutes from the point i select the version of os to load. 

I have recorded a few things, hope that'll give u a little insight to my case.

it starts with

Boot from (hd0,6) ext3

Reading files needed to boot
setting preliminary keymap
setting restricted driver
setting kernel event manger
loading hardware drivers

reading files needed to boot (second stage)
then an awful amount of details about the things it loads

after a while comes the login in screen.

but its all slow. very slow.

Please Help

---

### Post by NoaHall on 2009-09-20
sudo apt-get install rcconf, sudo rcconf, and disable anything that isn't vital.

---

### Post by Rizqureshy on 2009-09-20
thats the list of startup things i got from the terminal
tell me what to disable. This is the list

NetworkManager
acpi - support
acpid
anacron
apmd
appparmor
apport
atd
avahi - deamon
binfmt - support
bluetooth
botlogs.sh
brltty
console-setup
cron
cups
dbus
dkms_auinstaller
gdm
hal
hddtemp
hotkey-setup
keyboard-setup
klogd
laptop-mode
linux-restricted-modules-common
module-init-tools
nullmailer
ondemand
pcmciautils
policykit
pppd-dns
procps
pulseaudio
readahead
readahed-desktop
rsync
saned
stop-readahed
syslogd
system-tools-backends
udev
udev-finish
ufw
usplash
winbind
x11-common

---

### Post by NoaHall on 2009-09-20
Do you have a laptop?

If not, you can remove 

acpi - support
hotkey-setup
laptop-mode

Also, these two if you don't have -

bluetooth
rsync

---

### Post by Rizqureshy on 2009-09-20
Done it. I appreciate u r inputs. Thanks but seems like nothing is making a difference the wait is still there.

Could this be coz of the hdd? Its not very new. Its 40gb by the way.

I wish if it can only boot faster

---

### Post by scratman on 2009-09-20
I had a similar problem which, after much fiddling, was narrowed down to my Wireless USB dongle.  I just unplug that while it boots, and then reconnect one I get to the login screen.  It may not be the precise nature of your issue, but it could be worth a shot.  I'd unplug any peripherals that are not vital at boot time and see if that helps at all.

---

### Post by mikewhatever on 2009-09-20
How about the output of **df -h**?

---

### Post by Rizqureshy on 2009-09-20
Surprisingly it was booting/running much faster when i first tested it on usb (live version). Honestly that convinced me to install it in full. To my limited understanding is it not suppose to operate faster installed on a hard drive

---

### Post by NoaHall on 2009-09-20
It's meant to be the other way around. Installed is faster, live is much slower.

---

### Post by frt975 on 2009-09-20
Install bootchart.```
sudo aptitude install bootchart
``` It'll record every process and how long it takes.

---

### Post by oldfred on 2009-09-20
It looks like you have some type of between these two lines:
[   14.454619] EXT3-fs: mounted filesystem with ordered data mode.
[  100.862518] udev: starting version 141

I am not sure if the time stamp is start or end time but either EXT3-fs is having trouble mounting a NTFS directory or udev tries to load something that does not exist. 
If ntfs you may need to do a filecheck on that directory. 
If udev do you have something still in BIOS that has been removed. Google showed one user had removed a floppy drive but the BIOS still showed it and resetting BIOS solved it. Others had issues with USB devices.

---

### Post by nikhilbhardwaj on 2009-09-20
with all due respect ubuntu isn't the fastest distro
i'd recommend arch if you want a real difference
you could compile your kernel(but not if you are new to linux)
that really speeds things up

---

### Post by ibuclaw on 2009-09-20
> **Rizqureshy said:**
> My MSN id is :

if anyone could please add me and help me out

If you install xchat, connect to the Ubuntu Servers and you can ask for realtime help in either #ubuntu, or #ubuntu-beginners-help

The command to join is:
```
/join #ubuntu-beginners-help
```
Regards
Iain

---

### Post by Rizqureshy on 2009-09-24
Hurrrrraaaaa!!!!!..

Thank you all for your rapid input and interest in solving my problem. It was my HDD after all. When i gave it a ear, i heard it cranking real bad. Changed it and Ubuntu boots in seconds. Hardly 20-25. This is wonderful

Thanks once again

Rizwan Qureshy

---

