---
title: "ubuntu stops"
date: 2012-03-26
forum: General Help
---

### Post by sattie on 2012-03-26
Its running very well but suddenly its stops ik have ubuntu 10.04 lts version running as a server 
Is rgere anything what can cause this prob ?
 
s

---

### Post by raja.genupula on 2012-03-26
we need some more info . could you provide us the ```
dmesg
``` log report .
type it in your terminal and place it here and between code tags by pressing # in this window . 

at the time when system get freezes are you doing any specific operation every time before your PC get freezes ?

---

### Post by sattie on 2012-03-26
this is from the file dmseg  and no the ubuntu is running as a server 
 
0.000000] Initializing cgroup subsys cpuset
[ 0.000000] Initializing cgroup subsys cpu
[ 0.000000] Linux version 2.6.32-39-generic (buildd@palmer) (gcc version 4.4.3 (Ubuntu 4.4.3-4ubuntu5) ) #86-Ubuntu SMP Mon Feb 13 21:47:32 UTC 2012 (Ubuntu 2.6.32-39.86-generic 2.6.32.56+drm33.22)
[ 0.000000] KERNEL supported cpus:
[ 0.000000] Intel GenuineIntel
[ 0.000000] AMD AuthenticAMD
[ 0.000000] NSC Geode by NSC
[ 0.000000] Cyrix CyrixInstead
[ 0.000000] Centaur CentaurHauls
[ 0.000000] Transmeta GenuineTMx86
[ 0.000000] Transmeta TransmetaCPU
[ 0.000000] UMC UMC UMC UMC
[ 0.000000] BIOS-provided physical RAM map:
[ 0.000000] BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[ 0.000000] BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[ 0.000000] BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[ 0.000000] BIOS-e820: 0000000000100000 - 000000001dff0000 (usable)
[ 0.000000] BIOS-e820: 000000001dff0000 - 000000001dff3000 (ACPI NVS)
[ 0.000000] BIOS-e820: 000000001dff3000 - 000000001e000000 (ACPI data)
[ 0.000000] BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved)
[ 0.000000] BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[ 0.000000] BIOS-e820: 00000000ffff0000 - 0000000100000000 (reserved)
[ 0.000000] DMI 2.3 present.
[ 0.000000] Phoenix BIOS detected: BIOS may corrupt low RAM, working around it.
[ 0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
[ 0.000000] last_pfn = 0x1dff0 max_arch_pfn = 0x100000
[ 0.000000] MTRR default type: uncachable
[ 0.000000] MTRR fixed ranges enabled:
[ 0.000000] 00000-9FFFF write-back
[ 0.000000] A0000-BFFFF uncachable
[ 0.000000] C0000-C7FFF write-protect
[ 0.000000] C8000-FFFFF uncachable
[ 0.000000] MTRR variable ranges enabled:
[ 0.000000] 0 base 000000000 mask FE0000000 write-back
[ 0.000000] 1 base 01E000000 mask FFE000000 uncachable
[ 0.000000] 2 base 0E0000000 mask FFC000000 write-combining
[ 0.000000] 3 disabled
[ 0.000000] 4 disabled
[ 0.000000] 5 disabled
[ 0.000000] 6 disabled
[ 0.000000] 7 disabled
[ 0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[ 0.000000] Scanning 0 areas for low memory corruption
[ 0.000000] modified physical RAM map:
[ 0.000000] modified: 0000000000000000 - 0000000000010000 (reserved)
[ 0.000000] modified: 0000000000010000 - 000000000009fc00 (usable)
[ 0.000000] modified: 000000000009fc00 - 00000000000a0000 (reserved)
[ 0.000000] modified: 00000000000f0000 - 0000000000100000 (reserved)
[ 0.000000] modified: 0000000000100000 - 000000001dff0000 (usable)
[ 0.000000] modified: 000000001dff0000 - 000000001dff3000 (ACPI NVS)
[ 0.000000] modified: 000000001dff3000 - 000000001e000000 (ACPI data)
[ 0.000000] modified: 00000000fec00000 - 00000000fec01000 (reserved)
[ 0.000000] modified: 00000000fee00000 - 00000000fee01000 (reserved)
[ 0.000000] modified: 00000000ffff0000 - 0000000100000000 (reserved)
[ 0.000000] initial memory mapped : 0 - 00c00000
[ 0.000000] init_memory_mapping: 0000000000000000-000000001dff0000
[ 0.000000] Using x86 segment limits to approximate NX protection
[ 0.000000] 0000000000 - 0000400000 page 4k
[ 0.000000] 0000400000 - 001dc00000 page 2M
[ 0.000000] 001dc00000 - 001dff0000 page 4k
[ 0.000000] kernel direct mapping tables up to 1dff0000 @ 10000-15000
[ 0.000000] RAMDISK: 16095000 - 168335dd
[ 0.000000] ACPI: RSDP 000f7010 00014 (v00 KM400A)
[ 0.000000] ACPI: RSDT 1dff3040 0002C (v01 KM400A AWRDACPI 42302E31 AWRD 00000000)
[ 0.000000] ACPI: FACP 1dff30c0 00074 (v01 KM400A AWRDACPI 42302E31 AWRD 00000000)
[ 0.000000] ACPI: DSDT 1dff3180 044FF (v01 KM400A AWRDACPI 00001000 MSFT 0100000E)
[ 0.000000] ACPI: FACS 1dff0000 00040
[ 0.000000] ACPI: APIC 1dff76c0 0005A (v01 KM400A AWRDACPI 42302E31 AWRD 00000000)
[ 0.000000] ACPI: Local APIC address 0xfee00000
[ 0.000000] 0MB HIGHMEM available.
[ 0.000000] 479MB LOWMEM available.
[ 0.000000] mapped low ram: 0 - 1dff0000
[ 0.000000] low ram: 0 - 1dff0000
[ 0.000000] node 0 low ram: 00000000 - 1dff0000
[ 0.000000] node 0 bootmap 00011000 - 00014c00
[ 0.000000] (9 early reservations) ==> bootmem [0000000000 - 001dff0000]
[ 0.000000] #0 [0000000000 - 0000001000] BIOS data page ==> [0000000000 - 0000001000]
[ 0.000000] #1 [0000001000 - 0000002000] EX TRAMPOLINE ==> [0000001000 - 0000002000]
[ 0.000000] #2 [0000006000 - 0000007000] TRAMPOLINE ==> [0000006000 - 0000007000]
[ 0.000000] #3 [0000100000 - 00008e3f18] TEXT DATA BSS ==> [0000100000 - 00008e3f18]
[ 0.000000] #4 [0016095000 - 00168335dd] RAMDISK ==> [0016095000 - 00168335dd]
[ 0.000000] #5 [000009fc00 - 0000100000] BIOS reserved ==> [000009fc00 - 0000100000]
[ 0.000000] #6 [00008e4000 - 00008e7115] BRK ==> [00008e4000 - 00008e7115]
[ 0.000000] #7 [0000010000 - 0000011000] PGTABLE ==> [0000010000 - 0000011000]
[ 0.000000] #8 [0000011000 - 0000015000] BOOTMAP ==> [0000011000 - 0000015000]
[ 0.000000] found SMP MP-table at [c00f5550] f5550
[ 0.000000] Zone PFN ranges:
[ 0.000000] DMA 0x00000010 -> 0x00001000
[ 0.000000] Normal 0x00001000 -> 0x0001dff0
[ 0.000000] HighMem 0x0001dff0 -> 0x0001dff0
[ 0.000000] Movable zone start PFN for each node
[ 0.000000] early_node_map[2] active PFN ranges
[ 0.000000] 0: 0x00000010 -> 0x0000009f
[ 0.000000] 0: 0x00000100 -> 0x0001dff0
[ 0.000000] On node 0 totalpages: 122751
[ 0.000000] free_area_init_node: node 0, pgdat c079ea00, node_mem_map c1001200
[ 0.000000] DMA zone: 32 pages used for memmap
[ 0.000000] DMA zone: 0 pages reserved
[ 0.000000] DMA zone: 3951 pages, LIFO batch:0
[ 0.000000] Normal zone: 928 pages used for memmap
[ 0.000000] Normal zone: 117840 pages, LIFO batch:31
[ 0.000000] Using APIC driver default
[ 0.000000] ACPI: PM-Timer IO Port: 0x408
[ 0.000000] ACPI: Local APIC address 0xfee00000
[ 0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[ 0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[ 0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[ 0.000000] IOAPIC[0]: apic_id 2, version 3, address 0xfec00000, GSI 0-23
[ 0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[ 0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 low level)
[ 0.000000] ACPI: IRQ0 used by override.
[ 0.000000] ACPI: IRQ2 used by override.
[ 0.000000] ACPI: IRQ9 used by override.
[ 0.000000] Using ACPI (MADT) for SMP configuration information
[ 0.000000] SMP: Allowing 1 CPUs, 0 hotplug CPUs
[ 0.000000] nr_irqs_gsi: 24
[ 0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[ 0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000f0000
[ 0.000000] PM: Registered nosave memory: 00000000000f0000 - 0000000000100000
[ 0.000000] Allocating PCI resources starting at 1e000000 (gap: 1e000000:e0c00000)
[ 0.000000] Booting paravirtualized kernel on bare hardware
[ 0.000000] NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:1 nr_node_ids:1
[ 0.000000] PERCPU: Embedded 14 pages/cpu @c1400000 s36056 r0 d21288 u4194304
[ 0.000000] pcpu-alloc: s36056 r0 d21288 u4194304 alloc=1*4194304
[ 0.000000] pcpu-alloc: [0] 0 
[ 0.000000] Built 1 zonelists in Zone order, mobility grouping on. Total pages: 121791
[ 0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.32-39-generic root=UUID=8b0fe947-82e9-4f43-b3c1-3c23495da5b3 ro quiet splash
[ 0.000000] PID hash table entries: 2048 (order: 1, 8192 bytes)
[ 0.000000] Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)
[ 0.000000] Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)
[ 0.000000] Enabling fast FPU save and restore... done.
[ 0.000000] Enabling unmasked SIMD FPU exception support... done.
[ 0.000000] Initializing CPU#0
[ 0.000000] allocated 2456960 bytes of page_cgroup
[ 0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[ 0.000000] Initializing HighMem for node 0 (00000000:00000000)
[ 0.000000] Memory: 467976k/491456k available (4697k kernel code, 22632k reserved, 2122k data, 664k init, 0k highmem)
[ 0.000000] virtual kernel memory layout:
[ 0.000000] fixmap : 0xfff1d000 - 0xfffff000 ( 904 kB)
[ 0.000000] pkmap : 0xff800000 - 0xffc00000 (4096 kB)
[ 0.000000] vmalloc : 0xde7f0000 - 0xff7fe000 ( 528 MB)
[ 0.000000] lowmem : 0xc0000000 - 0xddff0000 ( 479 MB)
[ 0.000000] .init : 0xc07a9000 - 0xc084f000 ( 664 kB)
[ 0.000000] .data : 0xc0596757 - 0xc07a8fc8 (2122 kB)
[ 0.000000] .text : 0xc0100000 - 0xc0596757 (4697 kB)
[ 0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[ 0.000000] SLUB: Genslabs=13, HWalign=32, Order=0-3, MinObjects=0, CPUs=1, Nodes=1
[ 0.000000] Hierarchical RCU implementation.
[ 0.000000] NR_IRQS:2304 nr_irqs:256
[ 0.000000] Console: colour VGA+ 80x25
[ 0.000000] console [tty0] enabled
[ 0.000000] Fast TSC calibration using PIT
[ 0.000000] Detected 1743.241 MHz processor.
[ 0.008007] Calibrating delay loop (skipped), value calculated using timer frequency.. 3486.48 BogoMIPS (lpj=6972964)
[ 0.008035] Security Framework initialized
[ 0.008076] AppArmor: AppArmor initialized
[ 0.008087] Mount-cache hash table entries: 512
[ 0.008283] Initializing cgroup subsys ns
[ 0.008289] Initializing cgroup subsys cpuacct
[ 0.008295] Initializing cgroup subsys memory
[ 0.008309] Initializing cgroup subsys devices
[ 0.008313] Initializing cgroup subsys freezer
[ 0.008317] Initializing cgroup subsys net_cls
[ 0.008346] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[ 0.008350] CPU: L2 Cache: 256K (64 bytes/line)
[ 0.008357] mce: CPU supports 4 MCE banks
[ 0.008383] Performance Events: AMD PMU driver.
[ 0.008401] ... version: 0
[ 0.008403] ... bit width: 48
[ 0.008406] ... generic registers: 4
[ 0.008408] ... value mask: 0000ffffffffffff
[ 0.008411] ... max period: 00007fffffffffff
[ 0.008414] ... fixed-purpose events: 0
[ 0.008417] ... event mask: 000000000000000f
[ 0.008423] Checking 'hlt' instruction... OK.
[ 0.024684] SMP alternatives: switching to UP code
[ 0.032352] Freeing SMP alternatives: 19k freed
[ 0.032400] ACPI: Core revision 20090903
[ 0.044049] ftrace: converting mcount calls to 0f 1f 44 00 00
[ 0.044069] ftrace: allocating 21824 entries in 43 pages
[ 0.048192] Enabling APIC mode: Flat. Using 1 I/O APICs
[ 0.049263] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[ 0.090583] CPU0: AMD Sempron(tm) 2500+ stepping 01
[ 0.092001] Brought up 1 CPUs
[ 0.092001] Total of 1 processors activated (3486.48 BogoMIPS).
[ 0.092001] CPU0 attaching NULL sched-domain.
[ 0.092001] devtmpfs: initialized
[ 0.092001] regulator: core version 0.5
[ 0.092001] Time: 7:21:51 Date: 03/26/12
[ 0.092001] NET: Registered protocol family 16
[ 0.092001] EISA bus registered
[ 0.092001] ACPI: bus type pci registered
[ 0.097855] PCI: PCI BIOS revision 2.10 entry at 0xfb9f0, last bus=1
[ 0.097858] PCI: Using configuration type 1 for base access
[ 0.099163] bio: create slab <bio-0> at 0
[ 0.099912] ACPI: EC: Look up EC in DSDT
[ 0.107082] ACPI: Interpreter enabled
[ 0.107094] ACPI: (supports S0 S1 S3 S4 S5)
[ 0.107136] ACPI: Using IOAPIC for interrupt routing
[ 0.114136] ACPI: No dock devices found.
[ 0.114273] ACPI: PCI Root Bridge [PCI0] (0000:00)
[ 0.114339] pci 0000:00:00.0: reg 10 32bit mmio pref: [0xe0000000-0xe3ffffff]
[ 0.114440] pci 0000:00:01.0: supports D1
[ 0.114478] pci 0000:00:0a.0: reg 10 io port: [0xd000-0xd0ff]
[ 0.114486] pci 0000:00:0a.0: reg 14 32bit mmio: [0xea000000-0xea0000ff]
[ 0.114528] pci 0000:00:0a.0: supports D1 D2
[ 0.114531] pci 0000:00:0a.0: PME# supported from D1 D2 D3hot D3cold
[ 0.114536] pci 0000:00:0a.0: PME# disabled
[ 0.114586] pci 0000:00:10.0: reg 20 io port: [0xd400-0xd41f]
[ 0.114616] pci 0000:00:10.0: supports D1 D2
[ 0.114619] pci 0000:00:10.0: PME# supported from D0 D1 D2 D3hot D3cold
[ 0.114623] pci 0000:00:10.0: PME# disabled
[ 0.114667] pci 0000:00:10.1: reg 20 io port: [0xd800-0xd81f]
[ 0.114697] pci 0000:00:10.1: supports D1 D2
[ 0.114700] pci 0000:00:10.1: PME# supported from D0 D1 D2 D3hot D3cold
[ 0.114704] pci 0000:00:10.1: PME# disabled
[ 0.114757] pci 0000:00:10.2: reg 20 io port: [0xdc00-0xdc1f]
[ 0.114786] pci 0000:00:10.2: supports D1 D2
[ 0.114789] pci 0000:00:10.2: PME# supported from D0 D1 D2 D3hot D3cold
[ 0.114794] pci 0000:00:10.2: PME# disabled
[ 0.114827] pci 0000:00:10.3: reg 10 32bit mmio: [0xea001000-0xea0010ff]
[ 0.114871] pci 0000:00:10.3: supports D1 D2
[ 0.114873] pci 0000:00:10.3: PME# supported from D0 D1 D2 D3hot D3cold
[ 0.114878] pci 0000:00:10.3: PME# disabled
[ 0.114936] HPET not enabled in BIOS. You might try hpet=force boot option
[ 0.114945] pci 0000:00:11.0: quirk: region 0400-047f claimed by vt8235 PM
[ 0.114950] pci 0000:00:11.0: quirk: region 5000-500f claimed by vt8235 SMB
[ 0.115017] pci 0000:00:11.1: reg 20 io port: [0xe000-0xe00f]
[ 0.115082] pci 0000:00:11.5: reg 10 io port: [0xe400-0xe4ff]
[ 0.115129] pci 0000:00:11.5: supports D1 D2
[ 0.115161] pci 0000:00:12.0: reg 10 io port: [0xec00-0xecff]
[ 0.115169] pci 0000:00:12.0: reg 14 32bit mmio: [0xea002000-0xea0020ff]
[ 0.115210] pci 0000:00:12.0: supports D1 D2
[ 0.115213] pci 0000:00:12.0: PME# supported from D0 D1 D2 D3hot D3cold
[ 0.115218] pci 0000:00:12.0: PME# disabled
[ 0.115269] pci 0000:01:00.0: reg 10 32bit mmio pref: [0xe4000000-0xe7ffffff]
[ 0.115276] pci 0000:01:00.0: reg 14 32bit mmio: [0xe8000000-0xe8ffffff]
[ 0.115294] pci 0000:01:00.0: reg 30 32bit mmio pref: [0x000000-0x00ffff]
[ 0.115319] pci 0000:01:00.0: supports D1 D2
[ 0.115354] pci 0000:00:01.0: bridge 32bit mmio: [0xe8000000-0xe9ffffff]
[ 0.115360] pci 0000:00:01.0: bridge 32bit mmio pref: [0xe4000000-0xe7ffffff]
[ 0.115368] pci_bus 0000:00: on NUMA node 0
[ 0.115374] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[ 0.145576] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 6 7 10 *11 12)
[ 0.145801] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 6 7 10 *11 12)
[ 0.146027] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 6 7 *10 11 12)
[ 0.146255] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 6 7 10 11 12) *5
[ 0.146446] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 6 7 10 11 12) *0, disabled.
[ 0.146628] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 6 7 10 11 12) *0, disabled.
[ 0.146809] ACPI: PCI Interrupt Link [LNK0] (IRQs 3 4 6 7 10 11 12) *0, disabled.
[ 0.146989] ACPI: PCI Interrupt Link [LNK1] (IRQs 3 4 6 7 10 11 12) *0, disabled.
[ 0.147224] ACPI: PCI Interrupt Link [ALKA] (IRQs *20), disabled.
[ 0.147443] ACPI: PCI Interrupt Link [ALKB] (IRQs *21)
[ 0.147660] ACPI: PCI Interrupt Link [ALKC] (IRQs *22)
[ 0.147914] ACPI: PCI Interrupt Link [ALKD] (IRQs *23)
[ 0.148081] vgaarb: device added: PCI:0000:01:00.0,decodes=io+mem,owns=io+mem,locks=none
[ 0.148085] vgaarb: loaded
[ 0.148282] SCSI subsystem initialized
[ 0.148433] libata version 3.00 loaded.
[ 0.148562] usbcore: registered new interface driver usbfs
[ 0.148581] usbcore: registered new interface driver hub
[ 0.148624] usbcore: registered new device driver usb
[ 0.148826] ACPI: WMI: Mapper loaded
[ 0.148830] PCI: Using ACPI for IRQ routing
[ 0.149024] NetLabel: Initializing
[ 0.149027] NetLabel: domain hash size = 128
[ 0.149029] NetLabel: protocols = UNLABELED CIPSOv4
[ 0.149051] NetLabel: unlabeled traffic allowed by default
[ 0.149115] Switching to clocksource tsc
[ 0.152001] AppArmor: AppArmor Filesystem Enabled
[ 0.152001] pnp: PnP ACPI init
[ 0.152001] ACPI: bus type pnp registered
[ 0.156247] pnp: PnP ACPI: found 15 devices
[ 0.156250] ACPI: ACPI bus type pnp unregistered
[ 0.156256] PnPBIOS: Disabled by ACPI PNP
[ 0.156276] system 00:00: iomem range 0xc8000-0xcbfff has been reserved
[ 0.156281] system 00:00: iomem range 0xf0000-0xf7fff could not be reserved
[ 0.156285] system 00:00: iomem range 0xf8000-0xfbfff could not be reserved
[ 0.156289] system 00:00: iomem range 0xfc000-0xfffff could not be reserved
[ 0.156293] system 00:00: iomem range 0x1dff0000-0x1dffffff could not be reserved
[ 0.156298] system 00:00: iomem range 0xffff0000-0xffffffff has been reserved
[ 0.156302] system 00:00: iomem range 0x0-0x9ffff could not be reserved
[ 0.156306] system 00:00: iomem range 0x100000-0x1dfeffff could not be reserved
[ 0.156310] system 00:00: iomem range 0xfec00000-0xfec00fff could not be reserved
[ 0.156314] system 00:00: iomem range 0xfee00000-0xfee00fff has been reserved
[ 0.156318] system 00:00: iomem range 0xfff80000-0xfffeffff has been reserved
[ 0.156328] system 00:02: ioport range 0x400-0x47f has been reserved
[ 0.156332] system 00:02: ioport range 0x5000-0x500f has been reserved
[ 0.156339] system 00:03: ioport range 0x4d0-0x4d1 has been reserved
[ 0.156343] system 00:03: ioport range 0x294-0x297 has been reserved
[ 0.191129] pci 0000:00:01.0: PCI bridge, secondary bus 0000:01
[ 0.191132] pci 0000:00:01.0: IO window: disabled
[ 0.191139] pci 0000:00:01.0: MEM window: 0xe8000000-0xe9ffffff
[ 0.191144] pci 0000:00:01.0: PREFETCH window: 0xe4000000-0xe7ffffff
[ 0.191162] pci 0000:00:01.0: setting latency timer to 64
[ 0.191170] pci_bus 0000:00: resource 0 io: [0x00-0xffff]
[ 0.191173] pci_bus 0000:00: resource 1 mem: [0x000000-0xffffffff]
[ 0.191177] pci_bus 0000:01: resource 1 mem: [0xe8000000-0xe9ffffff]
[ 0.191181] pci_bus 0000:01: resource 2 pref mem [0xe4000000-0xe7ffffff]
[ 0.191241] NET: Registered protocol family 2
[ 0.191375] IP route cache hash table entries: 4096 (order: 2, 16384 bytes)
[ 0.191755] TCP established hash table entries: 16384 (order: 5, 131072 bytes)
[ 0.192000] TCP bind hash table entries: 16384 (order: 5, 131072 bytes)
[ 0.192243] TCP: Hash tables configured (established 16384 bind 16384)
[ 0.192246] TCP reno registered
[ 0.192379] NET: Registered protocol family 1
[ 0.192407] pci 0000:00:01.0: disabling DAC on VIA PCI bridge
[ 0.192496] pci 0000:01:00.0: Boot video device
[ 0.192843] cpufreq-nforce2: No nForce2 chipset.
[ 0.192894] Scanning for low memory corruption every 60 seconds
[ 0.193064] audit: initializing netlink socket (disabled)
[ 0.193083] type=2000 audit(1332746511.190:1): initialized
[ 0.204371] Trying to unpack rootfs image as initramfs...
[ 0.219031] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[ 0.221293] VFS: Disk quotas dquot_6.5.2
[ 0.221396] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[ 0.222220] fuse init (API version 7.13)
[ 0.222335] msgmni has been set to 914
[ 0.227220] alg: No test for stdrng (krng)
[ 0.227332] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[ 0.227337] io scheduler noop registered
[ 0.227340] io scheduler anticipatory registered
[ 0.227343] io scheduler deadline registered
[ 0.227406] io scheduler cfq registered (default)
[ 0.227565] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[ 0.227598] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[ 0.227755] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0
[ 0.227761] ACPI: Power Button [PWRB]
[ 0.227827] input: Sleep Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0E:00/input/input1
[ 0.227837] ACPI: Sleep Button [SLPB]
[ 0.227915] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input2
[ 0.227919] ACPI: Power Button [PWRF]
[ 0.227982] fan PNP0C0B:00: registered as cooling_device0
[ 0.227989] ACPI: Fan [FAN] (on)
[ 0.228357] Marking TSC unstable due to TSC halts in idle
[ 0.228478] processor LNXCPU:00: registered as cooling_device1
[ 0.236669] Switching to clocksource acpi_pm
[ 0.237041] thermal LNXTHERM:01: registered as thermal_zone0
[ 0.237058] ACPI: Thermal Zone [THRM] (57 C)
[ 0.238984] isapnp: Scanning for PnP cards...
[ 0.244886] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[ 0.245006] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[ 0.245106] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[ 0.245471] 00:09: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[ 0.245610] 00:0a: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[ 0.247098] brd: module loaded
[ 0.247780] loop: module loaded
[ 0.247953] input: Macintosh mouse button emulation as /devices/virtual/input/input3
[ 0.252865] ACPI: PCI Interrupt Link [ALKA] disabled and referenced, BIOS bug
[ 0.253000] ACPI: PCI Interrupt Link [ALKA] enabled at IRQ 20
[ 0.253010] alloc irq_desc for 20 on node -1
[ 0.253013] alloc kstat_irqs on node -1
[ 0.253025] pata_acpi 0000:00:11.1: PCI INT A -> Link[ALKA] -> GSI 20 (level, low) -> IRQ 20
[ 0.253128] pata_acpi 0000:00:11.1: PCI INT A disabled
[ 0.253569] Fixed MDIO Bus: probed
[ 0.253619] PPP generic driver version 2.4.2
[ 0.253735] tun: Universal TUN/TAP device driver, 1.6
[ 0.253738] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[ 0.253878] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[ 0.254160] ACPI: PCI Interrupt Link [ALKB] enabled at IRQ 21
[ 0.254166] alloc irq_desc for 21 on node -1
[ 0.254169] alloc kstat_irqs on node -1
[ 0.254177] ehci_hcd 0000:00:10.3: PCI INT D -> Link[ALKB] -> GSI 21 (level, low) -> IRQ 21
[ 0.254206] ehci_hcd 0000:00:10.3: EHCI Host Controller
[ 0.254270] ehci_hcd 0000:00:10.3: new USB bus registered, assigned bus number 1
[ 0.254360] ehci_hcd 0000:00:10.3: irq 21, io mem 0xea001000
[ 0.303832] ehci_hcd 0000:00:10.3: USB 2.0 started, EHCI 1.00
[ 0.304107] usb usb1: configuration #1 chosen from 1 choice
[ 0.304155] hub 1-0:1.0: USB hub found
[ 0.304178] hub 1-0:1.0: 6 ports detected
[ 0.304285] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[ 0.304313] uhci_hcd: USB Universal Host Controller Interface driver
[ 0.304413] uhci_hcd 0000:00:10.0: PCI INT A -> Link[ALKB] -> GSI 21 (level, low) -> IRQ 21
[ 0.304426] uhci_hcd 0000:00:10.0: UHCI Host Controller
[ 0.304486] uhci_hcd 0000:00:10.0: new USB bus registered, assigned bus number 2
[ 0.304519] uhci_hcd 0000:00:10.0: irq 21, io base 0x0000d400
[ 0.304657] usb usb2: configuration #1 chosen from 1 choice
[ 0.304693] hub 2-0:1.0: USB hub found
[ 0.304708] hub 2-0:1.0: 2 ports detected
[ 0.304774] uhci_hcd 0000:00:10.1: PCI INT B -> Link[ALKB] -> GSI 21 (level, low) -> IRQ 21
[ 0.304781] uhci_hcd 0000:00:10.1: UHCI Host Controller
[ 0.304829] uhci_hcd 0000:00:10.1: new USB bus registered, assigned bus number 3
[ 0.304851] uhci_hcd 0000:00:10.1: irq 21, io base 0x0000d800
[ 0.304983] usb usb3: configuration #1 chosen from 1 choice
[ 0.305025] hub 3-0:1.0: USB hub found
[ 0.305039] hub 3-0:1.0: 2 ports detected
[ 0.305093] uhci_hcd 0000:00:10.2: PCI INT C -> Link[ALKB] -> GSI 21 (level, low) -> IRQ 21
[ 0.305101] uhci_hcd 0000:00:10.2: UHCI Host Controller
[ 0.305151] uhci_hcd 0000:00:10.2: new USB bus registered, assigned bus number 4
[ 0.305173] uhci_hcd 0000:00:10.2: irq 21, io base 0x0000dc00
[ 0.305325] usb usb4: configuration #1 chosen from 1 choice
[ 0.305368] hub 4-0:1.0: USB hub found
[ 0.305382] hub 4-0:1.0: 2 ports detected
[ 0.305506] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[ 0.306026] serio: i8042 KBD port at 0x60,0x64 irq 1
[ 0.306035] serio: i8042 AUX port at 0x60,0x64 irq 12
[ 0.306173] mice: PS/2 mouse device common for all mice
[ 0.306341] rtc_cmos 00:05: RTC can wake from S4
[ 0.306419] rtc_cmos 00:05: rtc core: registered rtc_cmos as rtc0
[ 0.306469] rtc0: alarms up to one year, y3k, 242 bytes nvram
[ 0.306616] device-mapper: uevent: version 1.0.3
[ 0.309494] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: [email]dm-devel@redhat.com[/email]
[ 0.310528] device-mapper: multipath: version 1.1.0 loaded
[ 0.310534] device-mapper: multipath round-robin: version 1.0.0 loaded
[ 0.314452] EISA: Probing bus 0 at eisa.0
[ 0.314481] Cannot allocate resource for EISA slot 5
[ 0.314495] EISA: Detected 0 cards.
[ 0.314675] cpuidle: using governor ladder
[ 0.314737] cpuidle: using governor menu
[ 0.315267] TCP cubic registered
[ 0.315472] NET: Registered protocol family 10
[ 0.316493] NET: Registered protocol family 17
[ 0.316555] powernow-k8: Processor cpuid 681 not supported
[ 0.316594] Using IPI No-Shortcut mode
[ 0.316812] PM: Resume from disk failed.
[ 0.316834] registered taskstats version 1
[ 0.317095] Magic number: 4:498:370
[ 0.317253] rtc_cmos 00:05: setting system clock to 2012-03-26 07:21:52 UTC (1332746512)
[ 0.317258] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[ 0.317261] EDD information not available.
[ 0.324940] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input4
[ 0.782629] Freeing initrd memory: 7801k freed
[ 0.883639] isapnp: No Plug & Play device found
[ 0.883665] Freeing unused kernel memory: 664k freed
[ 0.884948] Write protecting the kernel text: 4700k
[ 0.884990] Write protecting the kernel read-only data: 1844k
[ 0.920558] udev: starting version 151
[ 0.952108] usb 2-1: new full speed USB device using uhci_hcd and address 2
[ 1.120819] usb 2-1: configuration #1 chosen from 1 choice
[ 1.200228] Floppy drive(s): fd0 is 1.44M
[ 1.220882] FDC 0 is a post-1991 82077
[ 1.227743] pata_via 0000:00:11.1: version 0.3.4
[ 1.227774] pata_via 0000:00:11.1: PCI INT A -> Link[ALKA] -> GSI 20 (level, low) -> IRQ 20
[ 1.237788] via-rhine.c:v1.10-LK1.4.3 2007-03-06 Written by Donald Becker
[ 1.237862] scsi0 : pata_via
[ 1.247345] scsi1 : pata_via
[ 1.251078] ata1: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xe000 irq 14
[ 1.251083] ata2: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xe008 irq 15
[ 1.251289] 8139cp: 10/100 PCI Ethernet driver v1.3 (Mar 22, 2004)
[ 1.252657] ACPI: PCI Interrupt Link [ALKD] enabled at IRQ 23
[ 1.252669] alloc irq_desc for 23 on node -1
[ 1.252673] alloc kstat_irqs on node -1
[ 1.252685] via-rhine 0000:00:12.0: PCI INT A -> Link[ALKD] -> GSI 23 (level, low) -> IRQ 23
[ 1.253574] eth0: VIA Rhine II at 0xea002000, 00:11:d8:be:88:83, IRQ 23.
[ 1.254288] eth0: MII PHY found at address 1, status 0x7849 advertising 05e1 Link 0000.
[ 1.254481] 8139cp 0000:00:0a.0: This (id 10ec:8139 rev 10) is not an 8139C+ compatible chip, use 8139too
[ 1.412510] ata1.00: native sectors (39102335) is smaller than sectors (39102336)
[ 1.412520] ata1.00: ATA-5: ST320413A, 3.57, max UDMA/100
[ 1.412524] ata1.00: 39102336 sectors, multi 16: LBA 
[ 1.420390] ata1.00: configured for UDMA/100
[ 1.420596] scsi 0:0:0:0: Direct-Access ATA ST320413A 3.57 PQ: 0 ANSI: 5
[ 1.420896] sd 0:0:0:0: Attached scsi generic sg0 type 0
[ 1.421043] sd 0:0:0:0: [sda] 39102336 512-byte logical blocks: (20.0 GB/18.6 GiB)
[ 1.421120] sd 0:0:0:0: [sda] Write Protect is off
[ 1.421125] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[ 1.421165] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[ 1.421389] sda: sda1 sda2 < sda5 >
[ 1.465772] sd 0:0:0:0: [sda] Attached SCSI disk
[ 1.592403] ata2.00: ATAPI: PIONEER DVD-ROM DVD-115, 1.12, max UDMA/33
[ 1.592444] ata2.01: ATAPI: SONY CD-RW CRX160E, 1.0e, max UDMA/33
[ 1.608281] ata2.00: configured for UDMA/33
[ 1.624246] ata2.01: configured for UDMA/33
[ 1.627153] scsi 1:0:0:0: CD-ROM PIONEER DVD-ROM DVD-115 1.12 PQ: 0 ANSI: 5
[ 1.630237] sr0: scsi3-mmc drive: 0x/0x cd/rw xa/form2 cdda tray
[ 1.630246] Uniform CD-ROM driver Revision: 3.20
[ 1.630460] sr 1:0:0:0: Attached scsi CD-ROM sr0
[ 1.630570] sr 1:0:0:0: Attached scsi generic sg1 type 5
[ 1.634282] scsi 1:0:1:0: CD-ROM SONY CD-RW CRX160E 1.0e PQ: 0 ANSI: 5
[ 1.640418] sr1: scsi3-mmc drive: 32x/32x writer cd/rw xa/form2 cdda tray
[ 1.640608] sr 1:0:1:0: Attached scsi CD-ROM sr1
[ 1.640718] sr 1:0:1:0: Attached scsi generic sg2 type 5
[ 1.652139] 8139too Fast Ethernet driver 0.9.28
[ 1.652225] alloc irq_desc for 18 on node -1
[ 1.652229] alloc kstat_irqs on node -1
[ 1.652241] 8139too 0000:00:0a.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[ 1.653459] eth1: RealTek RTL8139 at 0xd000, 00:0e:2e:b8:25:37, IRQ 18
[ 2.047333] EXT4-fs (sda1): INFO: recovery required on readonly filesystem
[ 2.047343] EXT4-fs (sda1): write access will be enabled during recovery
[ 7.737203] EXT4-fs (sda1): recovery complete
[ 7.737664] EXT4-fs (sda1): mounted filesystem with ordered data mode
[ 22.568655] Adding 859128k swap on /dev/sda5. Priority:-1 extents:1 across:859128k 
[ 22.630247] udev: starting version 151
[ 22.742153] lp: driver loaded but no devices found
[ 22.889921] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[ 23.040673] Linux agpgart interface v0.103
[ 23.081281] parport_pc 00:0b: reported by Plug and Play ACPI
[ 23.081395] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,EPP,ECP,DMA]
[ 23.195974] lp0: using parport0 (interrupt-driven).
[ 23.442601] type=1505 audit(1332746535.622:2): operation="profile_load" pid=469 name="/sbin/dhclient3"
[ 23.442989] type=1505 audit(1332746535.622:3): operation="profile_load" pid=469 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[ 23.443234] type=1505 audit(1332746535.622:4): operation="profile_load" pid=469 name="/usr/lib/connman/scripts/dhclient-script"
[ 23.460339] irda_init()
[ 23.460379] NET: Registered protocol family 23
[ 23.463711] vga16fb: initializing
[ 23.463721] vga16fb: mapped to 0xc00a0000
[ 23.463849] fb0: VGA16 VGA frame buffer device
[ 23.482762] agpgart: Detected VIA KM400/KM400A chipset
[ 23.522944] ppdev: user-space parallel port driver
[ 23.531098] usbcore: registered new interface driver usbserial
[ 23.531474] agpgart-via 0000:00:00.0: AGP aperture is 64M @ 0xe0000000
[ 23.532358] USB Serial support registered for generic
[ 23.532745] usbcore: registered new interface driver usbserial_generic
[ 23.532750] usbserial: USB Serial Driver core
[ 23.602468] USB Serial support registered for FTDI USB Serial Device
[ 23.603083] ftdi_sio 2-1:1.0: FTDI USB Serial Device converter detected
[ 23.603257] usb 2-1: Detected FT232BM
[ 23.603262] usb 2-1: Number of endpoints 2
[ 23.603265] usb 2-1: Endpoint 1 MaxPacketSize 64
[ 23.603268] usb 2-1: Endpoint 2 MaxPacketSize 64
[ 23.603270] usb 2-1: Setting MaxPacketSize 64
[ 23.605331] ftdi_sio ttyUSB0: Unable to read latency timer: -32
[ 23.605815] usb 2-1: FTDI USB Serial Device converter now attached to ttyUSB0
[ 23.605898] usbcore: registered new interface driver ftdi_sio
[ 23.605903] ftdi_sio: v1.5.0:USB FTDI Serial Converters Driver
[ 23.765977] gameport: NS558 PnP Gameport is pnp00:0e/gameport0, io 0x201, speed 946kHz
[ 23.827534] psmouse serio1: ID: 00 00 3c
[ 24.216370] Console: switching to colour frame buffer device 80x30
[ 24.226250] ACPI: PCI Interrupt Link [ALKC] enabled at IRQ 22
[ 24.226262] alloc irq_desc for 22 on node -1
[ 24.226266] alloc kstat_irqs on node -1
[ 24.226278] VIA 82xx Audio 0000:00:11.5: PCI INT C -> Link[ALKC] -> GSI 22 (level, low) -> IRQ 22
[ 24.226446] VIA 82xx Audio 0000:00:11.5: setting latency timer to 64
[ 24.489524] type=1505 audit(1332746536.670:5): operation="profile_load" pid=662 name="/usr/share/gdm/guest-session/Xsession"
[ 24.522066] type=1505 audit(1332746536.702:6): operation="profile_replace" pid=663 name="/sbin/dhclient3"
[ 24.522536] type=1505 audit(1332746536.702:7): operation="profile_replace" pid=663 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[ 24.522794] type=1505 audit(1332746536.702:8): operation="profile_replace" pid=663 name="/usr/lib/connman/scripts/dhclient-script"
[ 24.539406] input: PS/2 Logitech Mouse as /devices/platform/i8042/serio1/input/input5
[ 24.589624] eth1: link up, 100Mbps, full-duplex, lpa 0x45E1
[ 24.618187] eth0: link down
[ 24.618783] ADDRCONF(NETDEV_UP): eth0: link is not ready
[ 24.632419] type=1505 audit(1332746536.814:9): operation="profile_load" pid=664 name="/usr/bin/evince"
[ 24.674142] type=1505 audit(1332746536.854:10): operation="profile_load" pid=664 name="/usr/bin/evince-previewer"
[ 24.690941] type=1505 audit(1332746536.870:11): operation="profile_load" pid=664 name="/usr/bin/evince-thumbnailer"
[ 24.739485] codec_read: codec 0 is not valid [0xfe0000]
[ 24.762337] codec_read: codec 0 is not valid [0xfe0000]
[ 24.776405] codec_read: codec 0 is not valid [0xfe0000]
[ 24.792987] codec_read: codec 0 is not valid [0xfe0000]
0.000000] Initializing cgroup subsys cpuset
[ 0.000000] Initializing cgroup subsys cpu
[ 0.000000] Linux version 2.6.32-39-generic (buildd@palmer) (gcc version 4.4.3 (Ubuntu 4.4.3-4ubuntu5) ) #86-Ubuntu SMP Mon Feb 13 21:47:32 UTC 2012 (Ubuntu 2.6.32-39.86-generic 2.6.32.56+drm33.22)
[ 0.000000] KERNEL supported cpus:
[ 0.000000] Intel GenuineIntel
[ 0.000000] AMD AuthenticAMD
[ 0.000000] NSC Geode by NSC
[ 0.000000] Cyrix CyrixInstead
[ 0.000000] Centaur CentaurHauls
[ 0.000000] Transmeta GenuineTMx86
[ 0.000000] Transmeta TransmetaCPU
[ 0.000000] UMC UMC UMC UMC
[ 0.000000] BIOS-provided physical RAM map:
[ 0.000000] BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[ 0.000000] BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[ 0.000000] BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[ 0.000000] BIOS-e820: 0000000000100000 - 000000001dff0000 (usable)
[ 0.000000] BIOS-e820: 000000001dff0000 - 000000001dff3000 (ACPI NVS)
[ 0.000000] BIOS-e820: 000000001dff3000 - 000000001e000000 (ACPI data)
[ 0.000000] BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved)
[ 0.000000] BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[ 0.000000] BIOS-e820: 00000000ffff0000 - 0000000100000000 (reserved)
[ 0.000000] DMI 2.3 present.
[ 0.000000] Phoenix BIOS detected: BIOS may corrupt low RAM, working around it.
[ 0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
[ 0.000000] last_pfn = 0x1dff0 max_arch_pfn = 0x100000
[ 0.000000] MTRR default type: uncachable
[ 0.000000] MTRR fixed ranges enabled:
[ 0.000000] 00000-9FFFF write-back
[ 0.000000] A0000-BFFFF uncachable
[ 0.000000] C0000-C7FFF write-protect
[ 0.000000] C8000-FFFFF uncachable
[ 0.000000] MTRR variable ranges enabled:
[ 0.000000] 0 base 000000000 mask FE0000000 write-back
[ 0.000000] 1 base 01E000000 mask FFE000000 uncachable
[ 0.000000] 2 base 0E0000000 mask FFC000000 write-combining
[ 0.000000] 3 disabled
[ 0.000000] 4 disabled
[ 0.000000] 5 disabled
[ 0.000000] 6 disabled
[ 0.000000] 7 disabled
[ 0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[ 0.000000] Scanning 0 areas for low memory corruption
[ 0.000000] modified physical RAM map:
[ 0.000000] modified: 0000000000000000 - 0000000000010000 (reserved)
[ 0.000000] modified: 0000000000010000 - 000000000009fc00 (usable)
[ 0.000000] modified: 000000000009fc00 - 00000000000a0000 (reserved)
[ 0.000000] modified: 00000000000f0000 - 0000000000100000 (reserved)
[ 0.000000] modified: 0000000000100000 - 000000001dff0000 (usable)
[ 0.000000] modified: 000000001dff0000 - 000000001dff3000 (ACPI NVS)
[ 0.000000] modified: 000000001dff3000 - 000000001e000000 (ACPI data)
[ 0.000000] modified: 00000000fec00000 - 00000000fec01000 (reserved)
[ 0.000000] modified: 00000000fee00000 - 00000000fee01000 (reserved)
[ 0.000000] modified: 00000000ffff0000 - 0000000100000000 (reserved)
[ 0.000000] initial memory mapped : 0 - 00c00000
[ 0.000000] init_memory_mapping: 0000000000000000-000000001dff0000
[ 0.000000] Using x86 segment limits to approximate NX protection
[ 0.000000] 0000000000 - 0000400000 page 4k
[ 0.000000] 0000400000 - 001dc00000 page 2M
[ 0.000000] 001dc00000 - 001dff0000 page 4k
[ 0.000000] kernel direct mapping tables up to 1dff0000 @ 10000-15000
[ 0.000000] RAMDISK: 16095000 - 168335dd
[ 0.000000] ACPI: RSDP 000f7010 00014 (v00 KM400A)
[ 0.000000] ACPI: RSDT 1dff3040 0002C (v01 KM400A AWRDACPI 42302E31 AWRD 00000000)
[ 0.000000] ACPI: FACP 1dff30c0 00074 (v01 KM400A AWRDACPI 42302E31 AWRD 00000000)
[ 0.000000] ACPI: DSDT 1dff3180 044FF (v01 KM400A AWRDACPI 00001000 MSFT 0100000E)
[ 0.000000] ACPI: FACS 1dff0000 00040
[ 0.000000] ACPI: APIC 1dff76c0 0005A (v01 KM400A AWRDACPI 42302E31 AWRD 00000000)
[ 0.000000] ACPI: Local APIC address 0xfee00000
[ 0.000000] 0MB HIGHMEM available.
[ 0.000000] 479MB LOWMEM available.
[ 0.000000] mapped low ram: 0 - 1dff0000
[ 0.000000] low ram: 0 - 1dff0000
[ 0.000000] node 0 low ram: 00000000 - 1dff0000
[ 0.000000] node 0 bootmap 00011000 - 00014c00
[ 0.000000] (9 early reservations) ==> bootmem [0000000000 - 001dff0000]
[ 0.000000] #0 [0000000000 - 0000001000] BIOS data page ==> [0000000000 - 0000001000]
[ 0.000000] #1 [0000001000 - 0000002000] EX TRAMPOLINE ==> [0000001000 - 0000002000]
[ 0.000000] #2 [0000006000 - 0000007000] TRAMPOLINE ==> [0000006000 - 0000007000]
[ 0.000000] #3 [0000100000 - 00008e3f18] TEXT DATA BSS ==> [0000100000 - 00008e3f18]
[ 0.000000] #4 [0016095000 - 00168335dd] RAMDISK ==> [0016095000 - 00168335dd]
[ 0.000000] #5 [000009fc00 - 0000100000] BIOS reserved ==> [000009fc00 - 0000100000]
[ 0.000000] #6 [00008e4000 - 00008e7115] BRK ==> [00008e4000 - 00008e7115]
[ 0.000000] #7 [0000010000 - 0000011000] PGTABLE ==> [0000010000 - 0000011000]
[ 0.000000] #8 [0000011000 - 0000015000] BOOTMAP ==> [0000011000 - 0000015000]
[ 0.000000] found SMP MP-table at [c00f5550] f5550
[ 0.000000] Zone PFN ranges:
[ 0.000000] DMA 0x00000010 -> 0x00001000
[ 0.000000] Normal 0x00001000 -> 0x0001dff0
[ 0.000000] HighMem 0x0001dff0 -> 0x0001dff0
[ 0.000000] Movable zone start PFN for each node
[ 0.000000] early_node_map[2] active PFN ranges
[ 0.000000] 0: 0x00000010 -> 0x0000009f
[ 0.000000] 0: 0x00000100 -> 0x0001dff0
[ 0.000000] On node 0 totalpages: 122751
[ 0.000000] free_area_init_node: node 0, pgdat c079ea00, node_mem_map c1001200
[ 0.000000] DMA zone: 32 pages used for memmap
[ 0.000000] DMA zone: 0 pages reserved
[ 0.000000] DMA zone: 3951 pages, LIFO batch:0
[ 0.000000] Normal zone: 928 pages used for memmap
[ 0.000000] Normal zone: 117840 pages, LIFO batch:31
[ 0.000000] Using APIC driver default
[ 0.000000] ACPI: PM-Timer IO Port: 0x408
[ 0.000000] ACPI: Local APIC address 0xfee00000
[ 0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[ 0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[ 0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[ 0.000000] IOAPIC[0]: apic_id 2, version 3, address 0xfec00000, GSI 0-23
[ 0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[ 0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 low level)
[ 0.000000] ACPI: IRQ0 used by override.
[ 0.000000] ACPI: IRQ2 used by override.
[ 0.000000] ACPI: IRQ9 used by override.
[ 0.000000] Using ACPI (MADT) for SMP configuration information
[ 0.000000] SMP: Allowing 1 CPUs, 0 hotplug CPUs
[ 0.000000] nr_irqs_gsi: 24
[ 0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[ 0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000f0000
[ 0.000000] PM: Registered nosave memory: 00000000000f0000 - 0000000000100000
[ 0.000000] Allocating PCI resources starting at 1e000000 (gap: 1e000000:e0c00000)
[ 0.000000] Booting paravirtualized kernel on bare hardware
[ 0.000000] NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:1 nr_node_ids:1
[ 0.000000] PERCPU: Embedded 14 pages/cpu @c1400000 s36056 r0 d21288 u4194304
[ 0.000000] pcpu-alloc: s36056 r0 d21288 u4194304 alloc=1*4194304
[ 0.000000] pcpu-alloc: [0] 0 
[ 0.000000] Built 1 zonelists in Zone order, mobility grouping on. Total pages: 121791
[ 0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.32-39-generic root=UUID=8b0fe947-82e9-4f43-b3c1-3c23495da5b3 ro quiet splash
[ 0.000000] PID hash table entries: 2048 (order: 1, 8192 bytes)
[ 0.000000] Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)
[ 0.000000] Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)
[ 0.000000] Enabling fast FPU save and restore... done.
[ 0.000000] Enabling unmasked SIMD FPU exception support... done.
[ 0.000000] Initializing CPU#0
[ 0.000000] allocated 2456960 bytes of page_cgroup
[ 0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[ 0.000000] Initializing HighMem for node 0 (00000000:00000000)
[ 0.000000] Memory: 467976k/491456k available (4697k kernel code, 22632k reserved, 2122k data, 664k init, 0k highmem)
[ 0.000000] virtual kernel memory layout:
[ 0.000000] fixmap : 0xfff1d000 - 0xfffff000 ( 904 kB)
[ 0.000000] pkmap : 0xff800000 - 0xffc00000 (4096 kB)
[ 0.000000] vmalloc : 0xde7f0000 - 0xff7fe000 ( 528 MB)
[ 0.000000] lowmem : 0xc0000000 - 0xddff0000 ( 479 MB)
[ 0.000000] .init : 0xc07a9000 - 0xc084f000 ( 664 kB)
[ 0.000000] .data : 0xc0596757 - 0xc07a8fc8 (2122 kB)
[ 0.000000] .text : 0xc0100000 - 0xc0596757 (4697 kB)
[ 0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[ 0.000000] SLUB: Genslabs=13, HWalign=32, Order=0-3, MinObjects=0, CPUs=1, Nodes=1
[ 0.000000] Hierarchical RCU implementation.
[ 0.000000] NR_IRQS:2304 nr_irqs:256
[ 0.000000] Console: colour VGA+ 80x25
[ 0.000000] console [tty0] enabled
[ 0.000000] Fast TSC calibration using PIT
[ 0.000000] Detected 1743.241 MHz processor.
[ 0.008007] Calibrating delay loop (skipped), value calculated using timer frequency.. 3486.48 BogoMIPS (lpj=6972964)
[ 0.008035] Security Framework initialized
[ 0.008076] AppArmor: AppArmor initialized
[ 0.008087] Mount-cache hash table entries: 512
[ 0.008283] Initializing cgroup subsys ns
[ 0.008289] Initializing cgroup subsys cpuacct
[ 0.008295] Initializing cgroup subsys memory
[ 0.008309] Initializing cgroup subsys devices
[ 0.008313] Initializing cgroup subsys freezer
[ 0.008317] Initializing cgroup subsys net_cls
[ 0.008346] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[ 0.008350] CPU: L2 Cache: 256K (64 bytes/line)
[ 0.008357] mce: CPU supports 4 MCE banks
[ 0.008383] Performance Events: AMD PMU driver.
[ 0.008401] ... version: 0
[ 0.008403] ... bit width: 48
[ 0.008406] ... generic registers: 4
[ 0.008408] ... value mask: 0000ffffffffffff
[ 0.008411] ... max period: 00007fffffffffff
[ 0.008414] ... fixed-purpose events: 0
[ 0.008417] ... event mask: 000000000000000f
[ 0.008423] Checking 'hlt' instruction... OK.
[ 0.024684] SMP alternatives: switching to UP code
[ 0.032352] Freeing SMP alternatives: 19k freed
[ 0.032400] ACPI: Core revision 20090903
[ 0.044049] ftrace: converting mcount calls to 0f 1f 44 00 00
[ 0.044069] ftrace: allocating 21824 entries in 43 pages
[ 0.048192] Enabling APIC mode: Flat. Using 1 I/O APICs
[ 0.049263] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[ 0.090583] CPU0: AMD Sempron(tm) 2500+ stepping 01
[ 0.092001] Brought up 1 CPUs
[ 0.092001] Total of 1 processors activated (3486.48 BogoMIPS).
[ 0.092001] CPU0 attaching NULL sched-domain.
[ 0.092001] devtmpfs: initialized
[ 0.092001] regulator: core version 0.5
[ 0.092001] Time: 7:21:51 Date: 03/26/12
[ 0.092001] NET: Registered protocol family 16
[ 0.092001] EISA bus registered
[ 0.092001] ACPI: bus type pci registered
[ 0.097855] PCI: PCI BIOS revision 2.10 entry at 0xfb9f0, last bus=1
[ 0.097858] PCI: Using configuration type 1 for base access
[ 0.099163] bio: create slab <bio-0> at 0
[ 0.099912] ACPI: EC: Look up EC in DSDT
[ 0.107082] ACPI: Interpreter enabled
[ 0.107094] ACPI: (supports S0 S1 S3 S4 S5)
[ 0.107136] ACPI: Using IOAPIC for interrupt routing
[ 0.114136] ACPI: No dock devices found.
[ 0.114273] ACPI: PCI Root Bridge [PCI0] (0000:00)
[ 0.114339] pci 0000:00:00.0: reg 10 32bit mmio pref: [0xe0000000-0xe3ffffff]
[ 0.114440] pci 0000:00:01.0: supports D1
[ 0.114478] pci 0000:00:0a.0: reg 10 io port: [0xd000-0xd0ff]
[ 0.114486] pci 0000:00:0a.0: reg 14 32bit mmio: [0xea000000-0xea0000ff]
[ 0.114528] pci 0000:00:0a.0: supports D1 D2
[ 0.114531] pci 0000:00:0a.0: PME# supported from D1 D2 D3hot D3cold
[ 0.114536] pci 0000:00:0a.0: PME# disabled
[ 0.114586] pci 0000:00:10.0: reg 20 io port: [0xd400-0xd41f]
[ 0.114616] pci 0000:00:10.0: supports D1 D2
[ 0.114619] pci 0000:00:10.0: PME# supported from D0 D1 D2 D3hot D3cold
[ 0.114623] pci 0000:00:10.0: PME# disabled
[ 0.114667] pci 0000:00:10.1: reg 20 io port: [0xd800-0xd81f]
[ 0.114697] pci 0000:00:10.1: supports D1 D2
[ 0.114700] pci 0000:00:10.1: PME# supported from D0 D1 D2 D3hot D3cold
[ 0.114704] pci 0000:00:10.1: PME# disabled
[ 0.114757] pci 0000:00:10.2: reg 20 io port: [0xdc00-0xdc1f]
[ 0.114786] pci 0000:00:10.2: supports D1 D2
[ 0.114789] pci 0000:00:10.2: PME# supported from D0 D1 D2 D3hot D3cold
[ 0.114794] pci 0000:00:10.2: PME# disabled
[ 0.114827] pci 0000:00:10.3: reg 10 32bit mmio: [0xea001000-0xea0010ff]
[ 0.114871] pci 0000:00:10.3: supports D1 D2
[ 0.114873] pci 0000:00:10.3: PME# supported from D0 D1 D2 D3hot D3cold
[ 0.114878] pci 0000:00:10.3: PME# disabled
[ 0.114936] HPET not enabled in BIOS. You might try hpet=force boot option
[ 0.114945] pci 0000:00:11.0: quirk: region 0400-047f claimed by vt8235 PM
[ 0.114950] pci 0000:00:11.0: quirk: region 5000-500f claimed by vt8235 SMB
[ 0.115017] pci 0000:00:11.1: reg 20 io port: [0xe000-0xe00f]
[ 0.115082] pci 0000:00:11.5: reg 10 io port: [0xe400-0xe4ff]
[ 0.115129] pci 0000:00:11.5: supports D1 D2
[ 0.115161] pci 0000:00:12.0: reg 10 io port: [0xec00-0xecff]
[ 0.115169] pci 0000:00:12.0: reg 14 32bit mmio: [0xea002000-0xea0020ff]
[ 0.115210] pci 0000:00:12.0: supports D1 D2
[ 0.115213] pci 0000:00:12.0: PME# supported from D0 D1 D2 D3hot D3cold
[ 0.115218] pci 0000:00:12.0: PME# disabled
[ 0.115269] pci 0000:01:00.0: reg 10 32bit mmio pref: [0xe4000000-0xe7ffffff]
[ 0.115276] pci 0000:01:00.0: reg 14 32bit mmio: [0xe8000000-0xe8ffffff]
[ 0.115294] pci 0000:01:00.0: reg 30 32bit mmio pref: [0x000000-0x00ffff]
[ 0.115319] pci 0000:01:00.0: supports D1 D2
[ 0.115354] pci 0000:00:01.0: bridge 32bit mmio: [0xe8000000-0xe9ffffff]
[ 0.115360] pci 0000:00:01.0: bridge 32bit mmio pref: [0xe4000000-0xe7ffffff]
[ 0.115368] pci_bus 0000:00: on NUMA node 0
[ 0.115374] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[ 0.145576] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 6 7 10 *11 12)
[ 0.145801] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 6 7 10 *11 12)
[ 0.146027] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 6 7 *10 11 12)
[ 0.146255] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 6 7 10 11 12) *5
[ 0.146446] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 6 7 10 11 12) *0, disabled.
[ 0.146628] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 6 7 10 11 12) *0, disabled.
[ 0.146809] ACPI: PCI Interrupt Link [LNK0] (IRQs 3 4 6 7 10 11 12) *0, disabled.
[ 0.146989] ACPI: PCI Interrupt Link [LNK1] (IRQs 3 4 6 7 10 11 12) *0, disabled.
[ 0.147224] ACPI: PCI Interrupt Link [ALKA] (IRQs *20), disabled.
[ 0.147443] ACPI: PCI Interrupt Link [ALKB] (IRQs *21)
[ 0.147660] ACPI: PCI Interrupt Link [ALKC] (IRQs *22)
[ 0.147914] ACPI: PCI Interrupt Link [ALKD] (IRQs *23)
[ 0.148081] vgaarb: device added: PCI:0000:01:00.0,decodes=io+mem,owns=io+mem,locks=none
[ 0.148085] vgaarb: loaded
[ 0.148282] SCSI subsystem initialized
[ 0.148433] libata version 3.00 loaded.
[ 0.148562] usbcore: registered new interface driver usbfs
[ 0.148581] usbcore: registered new interface driver hub
[ 0.148624] usbcore: registered new device driver usb
[ 0.148826] ACPI: WMI: Mapper loaded
[ 0.148830] PCI: Using ACPI for IRQ routing
[ 0.149024] NetLabel: Initializing
[ 0.149027] NetLabel: domain hash size = 128
[ 0.149029] NetLabel: protocols = UNLABELED CIPSOv4
[ 0.149051] NetLabel: unlabeled traffic allowed by default
[ 0.149115] Switching to clocksource tsc
[ 0.152001] AppArmor: AppArmor Filesystem Enabled
[ 0.152001] pnp: PnP ACPI init
[ 0.152001] ACPI: bus type pnp registered
[ 0.156247] pnp: PnP ACPI: found 15 devices
[ 0.156250] ACPI: ACPI bus type pnp unregistered
[ 0.156256] PnPBIOS: Disabled by ACPI PNP
[ 0.156276] system 00:00: iomem range 0xc8000-0xcbfff has been reserved
[ 0.156281] system 00:00: iomem range 0xf0000-0xf7fff could not be reserved
[ 0.156285] system 00:00: iomem range 0xf8000-0xfbfff could not be reserved
[ 0.156289] system 00:00: iomem range 0xfc000-0xfffff could not be reserved
[ 0.156293] system 00:00: iomem range 0x1dff0000-0x1dffffff could not be reserved
[ 0.156298] system 00:00: iomem range 0xffff0000-0xffffffff has been reserved
[ 0.156302] system 00:00: iomem range 0x0-0x9ffff could not be reserved
[ 0.156306] system 00:00: iomem range 0x100000-0x1dfeffff could not be reserved
[ 0.156310] system 00:00: iomem range 0xfec00000-0xfec00fff could not be reserved
[ 0.156314] system 00:00: iomem range 0xfee00000-0xfee00fff has been reserved
[ 0.156318] system 00:00: iomem range 0xfff80000-0xfffeffff has been reserved
[ 0.156328] system 00:02: ioport range 0x400-0x47f has been reserved
[ 0.156332] system 00:02: ioport range 0x5000-0x500f has been reserved
[ 0.156339] system 00:03: ioport range 0x4d0-0x4d1 has been reserved
[ 0.156343] system 00:03: ioport range 0x294-0x297 has been reserved
[ 0.191129] pci 0000:00:01.0: PCI bridge, secondary bus 0000:01
[ 0.191132] pci 0000:00:01.0: IO window: disabled
[ 0.191139] pci 0000:00:01.0: MEM window: 0xe8000000-0xe9ffffff
[ 0.191144] pci 0000:00:01.0: PREFETCH window: 0xe4000000-0xe7ffffff
[ 0.191162] pci 0000:00:01.0: setting latency timer to 64
[ 0.191170] pci_bus 0000:00: resource 0 io: [0x00-0xffff]
[ 0.191173] pci_bus 0000:00: resource 1 mem: [0x000000-0xffffffff]
[ 0.191177] pci_bus 0000:01: resource 1 mem: [0xe8000000-0xe9ffffff]
[ 0.191181] pci_bus 0000:01: resource 2 pref mem [0xe4000000-0xe7ffffff]
[ 0.191241] NET: Registered protocol family 2
[ 0.191375] IP route cache hash table entries: 4096 (order: 2, 16384 bytes)
[ 0.191755] TCP established hash table entries: 16384 (order: 5, 131072 bytes)
[ 0.192000] TCP bind hash table entries: 16384 (order: 5, 131072 bytes)
[ 0.192243] TCP: Hash tables configured (established 16384 bind 16384)
[ 0.192246] TCP reno registered
[ 0.192379] NET: Registered protocol family 1
[ 0.192407] pci 0000:00:01.0: disabling DAC on VIA PCI bridge
[ 0.192496] pci 0000:01:00.0: Boot video device
[ 0.192843] cpufreq-nforce2: No nForce2 chipset.
[ 0.192894] Scanning for low memory corruption every 60 seconds
[ 0.193064] audit: initializing netlink socket (disabled)
[ 0.193083] type=2000 audit(1332746511.190:1): initialized
[ 0.204371] Trying to unpack rootfs image as initramfs...
[ 0.219031] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[ 0.221293] VFS: Disk quotas dquot_6.5.2
[ 0.221396] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[ 0.222220] fuse init (API version 7.13)
[ 0.222335] msgmni has been set to 914
[ 0.227220] alg: No test for stdrng (krng)
[ 0.227332] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[ 0.227337] io scheduler noop registered
[ 0.227340] io scheduler anticipatory registered
[ 0.227343] io scheduler deadline registered
[ 0.227406] io scheduler cfq registered (default)
[ 0.227565] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[ 0.227598] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[ 0.227755] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0
[ 0.227761] ACPI: Power Button [PWRB]
[ 0.227827] input: Sleep Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0E:00/input/input1
[ 0.227837] ACPI: Sleep Button [SLPB]
[ 0.227915] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input2
[ 0.227919] ACPI: Power Button [PWRF]
[ 0.227982] fan PNP0C0B:00: registered as cooling_device0
[ 0.227989] ACPI: Fan [FAN] (on)
[ 0.228357] Marking TSC unstable due to TSC halts in idle
[ 0.228478] processor LNXCPU:00: registered as cooling_device1
[ 0.236669] Switching to clocksource acpi_pm
[ 0.237041] thermal LNXTHERM:01: registered as thermal_zone0
[ 0.237058] ACPI: Thermal Zone [THRM] (57 C)
[ 0.238984] isapnp: Scanning for PnP cards...
[ 0.244886] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[ 0.245006] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[ 0.245106] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[ 0.245471] 00:09: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[ 0.245610] 00:0a: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[ 0.247098] brd: module loaded
[ 0.247780] loop: module loaded
[ 0.247953] input: Macintosh mouse button emulation as /devices/virtual/input/input3
[ 0.252865] ACPI: PCI Interrupt Link [ALKA] disabled and referenced, BIOS bug
[ 0.253000] ACPI: PCI Interrupt Link [ALKA] enabled at IRQ 20
[ 0.253010] alloc irq_desc for 20 on node -1
[ 0.253013] alloc kstat_irqs on node -1
[ 0.253025] pata_acpi 0000:00:11.1: PCI INT A -> Link[ALKA] -> GSI 20 (level, low) -> IRQ 20
[ 0.253128] pata_acpi 0000:00:11.1: PCI INT A disabled
[ 0.253569] Fixed MDIO Bus: probed
[ 0.253619] PPP generic driver version 2.4.2
[ 0.253735] tun: Universal TUN/TAP device driver, 1.6
[ 0.253738] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[ 0.253878] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[ 0.254160] ACPI: PCI Interrupt Link [ALKB] enabled at IRQ 21
[ 0.254166] alloc irq_desc for 21 on node -1
[ 0.254169] alloc kstat_irqs on node -1
[ 0.254177] ehci_hcd 0000:00:10.3: PCI INT D -> Link[ALKB] -> GSI 21 (level, low) -> IRQ 21
[ 0.254206] ehci_hcd 0000:00:10.3: EHCI Host Controller
[ 0.254270] ehci_hcd 0000:00:10.3: new USB bus registered, assigned bus number 1
[ 0.254360] ehci_hcd 0000:00:10.3: irq 21, io mem 0xea001000
[ 0.303832] ehci_hcd 0000:00:10.3: USB 2.0 started, EHCI 1.00
[ 0.304107] usb usb1: configuration #1 chosen from 1 choice
[ 0.304155] hub 1-0:1.0: USB hub found
[ 0.304178] hub 1-0:1.0: 6 ports detected
[ 0.304285] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[ 0.304313] uhci_hcd: USB Universal Host Controller Interface driver
[ 0.304413] uhci_hcd 0000:00:10.0: PCI INT A -> Link[ALKB] -> GSI 21 (level, low) -> IRQ 21
[ 0.304426] uhci_hcd 0000:00:10.0: UHCI Host Controller
[ 0.304486] uhci_hcd 0000:00:10.0: new USB bus registered, assigned bus number 2
[ 0.304519] uhci_hcd 0000:00:10.0: irq 21, io base 0x0000d400
[ 0.304657] usb usb2: configuration #1 chosen from 1 choice
[ 0.304693] hub 2-0:1.0: USB hub found
[ 0.304708] hub 2-0:1.0: 2 ports detected
[ 0.304774] uhci_hcd 0000:00:10.1: PCI INT B -> Link[ALKB] -> GSI 21 (level, low) -> IRQ 21
[ 0.304781] uhci_hcd 0000:00:10.1: UHCI Host Controller
[ 0.304829] uhci_hcd 0000:00:10.1: new USB bus registered, assigned bus number 3
[ 0.304851] uhci_hcd 0000:00:10.1: irq 21, io base 0x0000d800
[ 0.304983] usb usb3: configuration #1 chosen from 1 choice
[ 0.305025] hub 3-0:1.0: USB hub found
[ 0.305039] hub 3-0:1.0: 2 ports detected
[ 0.305093] uhci_hcd 0000:00:10.2: PCI INT C -> Link[ALKB] -> GSI 21 (level, low) -> IRQ 21
[ 0.305101] uhci_hcd 0000:00:10.2: UHCI Host Controller
[ 0.305151] uhci_hcd 0000:00:10.2: new USB bus registered, assigned bus number 4
[ 0.305173] uhci_hcd 0000:00:10.2: irq 21, io base 0x0000dc00
[ 0.305325] usb usb4: configuration #1 chosen from 1 choice
[ 0.305368] hub 4-0:1.0: USB hub found
[ 0.305382] hub 4-0:1.0: 2 ports detected
[ 0.305506] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[ 0.306026] serio: i8042 KBD port at 0x60,0x64 irq 1
[ 0.306035] serio: i8042 AUX port at 0x60,0x64 irq 12
[ 0.306173] mice: PS/2 mouse device common for all mice
[ 0.306341] rtc_cmos 00:05: RTC can wake from S4
[ 0.306419] rtc_cmos 00:05: rtc core: registered rtc_cmos as rtc0
[ 0.306469] rtc0: alarms up to one year, y3k, 242 bytes nvram
[ 0.306616] device-mapper: uevent: version 1.0.3
[ 0.309494] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: [email]dm-devel@redhat.com[/email]
[ 0.310528] device-mapper: multipath: version 1.1.0 loaded
[ 0.310534] device-mapper: multipath round-robin: version 1.0.0 loaded
[ 0.314452] EISA: Probing bus 0 at eisa.0
[ 0.314481] Cannot allocate resource for EISA slot 5
[ 0.314495] EISA: Detected 0 cards.
[ 0.314675] cpuidle: using governor ladder
[ 0.314737] cpuidle: using governor menu
[ 0.315267] TCP cubic registered
[ 0.315472] NET: Registered protocol family 10
[ 0.316493] NET: Registered protocol family 17
[ 0.316555] powernow-k8: Processor cpuid 681 not supported
[ 0.316594] Using IPI No-Shortcut mode
[ 0.316812] PM: Resume from disk failed.
[ 0.316834] registered taskstats version 1
[ 0.317095] Magic number: 4:498:370
[ 0.317253] rtc_cmos 00:05: setting system clock to 2012-03-26 07:21:52 UTC (1332746512)
[ 0.317258] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[ 0.317261] EDD information not available.
[ 0.324940] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input4
[ 0.782629] Freeing initrd memory: 7801k freed
[ 0.883639] isapnp: No Plug & Play device found
[ 0.883665] Freeing unused kernel memory: 664k freed
[ 0.884948] Write protecting the kernel text: 4700k
[ 0.884990] Write protecting the kernel read-only data: 1844k
[ 0.920558] udev: starting version 151
[ 0.952108] usb 2-1: new full speed USB device using uhci_hcd and address 2
[ 1.120819] usb 2-1: configuration #1 chosen from 1 choice
[ 1.200228] Floppy drive(s): fd0 is 1.44M
[ 1.220882] FDC 0 is a post-1991 82077
[ 1.227743] pata_via 0000:00:11.1: version 0.3.4
[ 1.227774] pata_via 0000:00:11.1: PCI INT A -> Link[ALKA] -> GSI 20 (level, low) -> IRQ 20
[ 1.237788] via-rhine.c:v1.10-LK1.4.3 2007-03-06 Written by Donald Becker
[ 1.237862] scsi0 : pata_via
[ 1.247345] scsi1 : pata_via
[ 1.251078] ata1: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xe000 irq 14
[ 1.251083] ata2: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xe008 irq 15
[ 1.251289] 8139cp: 10/100 PCI Ethernet driver v1.3 (Mar 22, 2004)
[ 1.252657] ACPI: PCI Interrupt Link [ALKD] enabled at IRQ 23
[ 1.252669] alloc irq_desc for 23 on node -1
[ 1.252673] alloc kstat_irqs on node -1
[ 1.252685] via-rhine 0000:00:12.0: PCI INT A -> Link[ALKD] -> GSI 23 (level, low) -> IRQ 23
[ 1.253574] eth0: VIA Rhine II at 0xea002000, 00:11:d8:be:88:83, IRQ 23.
[ 1.254288] eth0: MII PHY found at address 1, status 0x7849 advertising 05e1 Link 0000.
[ 1.254481] 8139cp 0000:00:0a.0: This (id 10ec:8139 rev 10) is not an 8139C+ compatible chip, use 8139too
[ 1.412510] ata1.00: native sectors (39102335) is smaller than sectors (39102336)
[ 1.412520] ata1.00: ATA-5: ST320413A, 3.57, max UDMA/100
[ 1.412524] ata1.00: 39102336 sectors, multi 16: LBA 
[ 1.420390] ata1.00: configured for UDMA/100
[ 1.420596] scsi 0:0:0:0: Direct-Access ATA ST320413A 3.57 PQ: 0 ANSI: 5
[ 1.420896] sd 0:0:0:0: Attached scsi generic sg0 type 0
[ 1.421043] sd 0:0:0:0: [sda] 39102336 512-byte logical blocks: (20.0 GB/18.6 GiB)
[ 1.421120] sd 0:0:0:0: [sda] Write Protect is off
[ 1.421125] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[ 1.421165] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[ 1.421389] sda: sda1 sda2 < sda5 >
[ 1.465772] sd 0:0:0:0: [sda] Attached SCSI disk
[ 1.592403] ata2.00: ATAPI: PIONEER DVD-ROM DVD-115, 1.12, max UDMA/33
[ 1.592444] ata2.01: ATAPI: SONY CD-RW CRX160E, 1.0e, max UDMA/33
[ 1.608281] ata2.00: configured for UDMA/33
[ 1.624246] ata2.01: configured for UDMA/33
[ 1.627153] scsi 1:0:0:0: CD-ROM PIONEER DVD-ROM DVD-115 1.12 PQ: 0 ANSI: 5
[ 1.630237] sr0: scsi3-mmc drive: 0x/0x cd/rw xa/form2 cdda tray
[ 1.630246] Uniform CD-ROM driver Revision: 3.20
[ 1.630460] sr 1:0:0:0: Attached scsi CD-ROM sr0
[ 1.630570] sr 1:0:0:0: Attached scsi generic sg1 type 5
[ 1.634282] scsi 1:0:1:0: CD-ROM SONY CD-RW CRX160E 1.0e PQ: 0 ANSI: 5
[ 1.640418] sr1: scsi3-mmc drive: 32x/32x writer cd/rw xa/form2 cdda tray
[ 1.640608] sr 1:0:1:0: Attached scsi CD-ROM sr1
[ 1.640718] sr 1:0:1:0: Attached scsi generic sg2 type 5
[ 1.652139] 8139too Fast Ethernet driver 0.9.28
[ 1.652225] alloc irq_desc for 18 on node -1
[ 1.652229] alloc kstat_irqs on node -1
[ 1.652241] 8139too 0000:00:0a.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[ 1.653459] eth1: RealTek RTL8139 at 0xd000, 00:0e:2e:b8:25:37, IRQ 18
[ 2.047333] EXT4-fs (sda1): INFO: recovery required on readonly filesystem
[ 2.047343] EXT4-fs (sda1): write access will be enabled during recovery
[ 7.737203] EXT4-fs (sda1): recovery complete
[ 7.737664] EXT4-fs (sda1): mounted filesystem with ordered data mode
[ 22.568655] Adding 859128k swap on /dev/sda5. Priority:-1 extents:1 across:859128k 
[ 22.630247] udev: starting version 151
[ 22.742153] lp: driver loaded but no devices found
[ 22.889921] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[ 23.040673] Linux agpgart interface v0.103
[ 23.081281] parport_pc 00:0b: reported by Plug and Play ACPI
[ 23.081395] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,EPP,ECP,DMA]
[ 23.195974] lp0: using parport0 (interrupt-driven).
[ 23.442601] type=1505 audit(1332746535.622:2): operation="profile_load" pid=469 name="/sbin/dhclient3"
[ 23.442989] type=1505 audit(1332746535.622:3): operation="profile_load" pid=469 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[ 23.443234] type=1505 audit(1332746535.622:4): operation="profile_load" pid=469 name="/usr/lib/connman/scripts/dhclient-script"
[ 23.460339] irda_init()
[ 23.460379] NET: Registered protocol family 23
[ 23.463711] vga16fb: initializing
[ 23.463721] vga16fb: mapped to 0xc00a0000
[ 23.463849] fb0: VGA16 VGA frame buffer device
[ 23.482762] agpgart: Detected VIA KM400/KM400A chipset
[ 23.522944] ppdev: user-space parallel port driver
[ 23.531098] usbcore: registered new interface driver usbserial
[ 23.531474] agpgart-via 0000:00:00.0: AGP aperture is 64M @ 0xe0000000
[ 23.532358] USB Serial support registered for generic
[ 23.532745] usbcore: registered new interface driver usbserial_generic
[ 23.532750] usbserial: USB Serial Driver core
[ 23.602468] USB Serial support registered for FTDI USB Serial Device
[ 23.603083] ftdi_sio 2-1:1.0: FTDI USB Serial Device converter detected
[ 23.603257] usb 2-1: Detected FT232BM
[ 23.603262] usb 2-1: Number of endpoints 2
[ 23.603265] usb 2-1: Endpoint 1 MaxPacketSize 64
[ 23.603268] usb 2-1: Endpoint 2 MaxPacketSize 64
[ 23.603270] usb 2-1: Setting MaxPacketSize 64
[ 23.605331] ftdi_sio ttyUSB0: Unable to read latency timer: -32
[ 23.605815] usb 2-1: FTDI USB Serial Device converter now attached to ttyUSB0
[ 23.605898] usbcore: registered new interface driver ftdi_sio
[ 23.605903] ftdi_sio: v1.5.0:USB FTDI Serial Converters Driver
[ 23.765977] gameport: NS558 PnP Gameport is pnp00:0e/gameport0, io 0x201, speed 946kHz
[ 23.827534] psmouse serio1: ID: 00 00 3c
[ 24.216370] Console: switching to colour frame buffer device 80x30
[ 24.226250] ACPI: PCI Interrupt Link [ALKC] enabled at IRQ 22
[ 24.226262] alloc irq_desc for 22 on node -1
[ 24.226266] alloc kstat_irqs on node -1
[ 24.226278] VIA 82xx Audio 0000:00:11.5: PCI INT C -> Link[ALKC] -> GSI 22 (level, low) -> IRQ 22
[ 24.226446] VIA 82xx Audio 0000:00:11.5: setting latency timer to 64
[ 24.489524] type=1505 audit(1332746536.670:5): operation="profile_load" pid=662 name="/usr/share/gdm/guest-session/Xsession"
[ 24.522066] type=1505 audit(1332746536.702:6): operation="profile_replace" pid=663 name="/sbin/dhclient3"
[ 24.522536] type=1505 audit(1332746536.702:7): operation="profile_replace" pid=663 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[ 24.522794] type=1505 audit(1332746536.702:8): operation="profile_replace" pid=663 name="/usr/lib/connman/scripts/dhclient-script"
[ 24.539406] input: PS/2 Logitech Mouse as /devices/platform/i8042/serio1/input/input5
[ 24.589624] eth1: link up, 100Mbps, full-duplex, lpa 0x45E1
[ 24.618187] eth0: link down
[ 24.618783] ADDRCONF(NETDEV_UP): eth0: link is not ready
[ 24.632419] type=1505 audit(1332746536.814:9): operation="profile_load" pid=664 name="/usr/bin/evince"
[ 24.674142] type=1505 audit(1332746536.854:10): operation="profile_load" pid=664 name="/usr/bin/evince-previewer"
[ 24.690941] type=1505 audit(1332746536.870:11): operation="profile_load" pid=664 name="/usr/bin/evince-thumbnailer"
[ 24.739485] codec_read: codec 0 is not valid [0xfe0000]
[ 24.762337] codec_read: codec 0 is not valid [0xfe0000]
[ 24.776405] codec_read: codec 0 is not valid [0xfe0000]
[ 24.792987] codec_read: codec 0 is not valid [0xfe0000]

---

