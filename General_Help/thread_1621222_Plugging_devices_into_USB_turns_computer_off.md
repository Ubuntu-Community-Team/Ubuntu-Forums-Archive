---
title: "Plugging devices into USB turns computer off"
date: 2010-11-14
forum: General Help
---

### Post by RustyTrowel on 2010-11-14
I just installed Ubuntu 10.10 32 bit on my desktop and I've encountered a curious and somewhat frustrating issue.  It appears that when I plug a flash drive, external hard drive or MP3 player into a USB port my computer turns off.  Sometimes it happens instantly, other times it occurs a minute or two later when I'm transferring files.

I'm not sure how to approach this issue.  I've searched the forum and haven't found any mention of this.  I am working on said desktop and all other hardware seems in good working order.  

If it helps, This is a 3 year old desktop with an AMD Athlon 64 X2 4600 cpu, a ABIT NF-M2S AM2 NVIDIA GeForce 6100 motherboard, an EVGA GeForce 7600GT video card and a SATA harddrive.  I can post a log if someone wants, not sure which one to post though.

Any help would be much appreciated,

Thanks

---

### Post by gradinaruvasile on 2010-11-14
Seems like a hardware issue. Does this happen on all usb ports or just one of them? 

Open a terminal, plug in the drive and issue a "dmesg > ~/Desktop/dmesg" command (make it ready before you plug in and press enter after plugging in the drive). You will have a "dmesg" text document on your desktop that contains the system messages. Post that here.

---

### Post by RustyTrowel on 2010-11-14
It seems that this does occurs when I plug in to any of the USB ports.  That said, on the last plug in of my Western Digital external hard drive it did not power down.  

I ran that dmesg command as you suggested.  Here is the output:

```

[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.35-22-generic (buildd@rothera) (gcc version 4.4.5 (Ubuntu/Linaro 4.4.4-14ubuntu4) ) #33-Ubuntu SMP Sun Sep 19 20:34:50 UTC 2010 (Ubuntu 2.6.35-22.33-generic 2.6.35.4)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f400 (usable)
[    0.000000]  BIOS-e820: 000000000009f400 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000003fee0000 (usable)
[    0.000000]  BIOS-e820: 000000003fee0000 - 000000003fee3000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000003fee3000 - 000000003fef0000 (ACPI data)
[    0.000000]  BIOS-e820: 000000003fef0000 - 000000003ff00000 (reserved)
[    0.000000]  BIOS-e820: 00000000f0000000 - 00000000f4000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 0000000100000000 (reserved)
[    0.000000] Notice: NX (Execute Disable) protection cannot be enabled: non-PAE kernel!
[    0.000000] DMI 2.4 present.
[    0.000000] Phoenix BIOS detected: BIOS may corrupt low RAM, working around it.
[    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
[    0.000000] e820 update range: 0000000000000000 - 0000000000001000 (usable) ==> (reserved)
[    0.000000] e820 remove range: 00000000000a0000 - 0000000000100000 (usable)
[    0.000000] last_pfn = 0x3fee0 max_arch_pfn = 0x100000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-C7FFF write-protect
[    0.000000]   C8000-FFFFF uncachable
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 0000000000 mask FFC0000000 write-back
[    0.000000]   1 base 003FF00000 mask FFFFF00000 uncachable
[    0.000000]   2 disabled
[    0.000000]   3 disabled
[    0.000000]   4 disabled
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] Scanning 0 areas for low memory corruption
[    0.000000] modified physical RAM map:
[    0.000000]  modified: 0000000000000000 - 0000000000010000 (reserved)
[    0.000000]  modified: 0000000000010000 - 000000000009f400 (usable)
[    0.000000]  modified: 000000000009f400 - 00000000000a0000 (reserved)
[    0.000000]  modified: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  modified: 0000000000100000 - 000000003fee0000 (usable)
[    0.000000]  modified: 000000003fee0000 - 000000003fee3000 (ACPI NVS)
[    0.000000]  modified: 000000003fee3000 - 000000003fef0000 (ACPI data)
[    0.000000]  modified: 000000003fef0000 - 000000003ff00000 (reserved)
[    0.000000]  modified: 00000000f0000000 - 00000000f4000000 (reserved)
[    0.000000]  modified: 00000000fec00000 - 0000000100000000 (reserved)
[    0.000000] initial memory mapped : 0 - 00c00000
[    0.000000] found SMP MP-table at [c00f3a00] f3a00
[    0.000000] init_memory_mapping: 0000000000000000-00000000377fe000
[    0.000000]  0000000000 - 0000400000 page 4k
[    0.000000]  0000400000 - 0037400000 page 2M
[    0.000000]  0037400000 - 00377fe000 page 4k
[    0.000000] kernel direct mapping tables up to 377fe000 @ 15000-1a000
[    0.000000] RAMDISK: 2f03b000 - 2ff68000
[    0.000000] ACPI: RSDP 000f7a10 00014 (v00 Nvidia)
[    0.000000] ACPI: RSDT 3fee3040 00038 (v01 Nvidia NVDAACPI 42302E31 NVDA 00000000)
[    0.000000] ACPI: FACP 3fee30c0 00074 (v01 Nvidia NVDAACPI 42302E31 NVDA 00000000)
[    0.000000] ACPI Warning: Optional field Pm2ControlBlock has zero address or length: 0x0000000000000000/0x1 (20100428/tbfadt-557)
[    0.000000] ACPI: DSDT 3fee3180 06395 (v01 NVIDIA NVDAACPI 00001000 MSFT 0100000E)
[    0.000000] ACPI: FACS 3fee0000 00040
[    0.000000] ACPI: SSDT 3fee9640 00248 (v01 PTLTD  POWERNOW 00000001  LTP 00000001)
[    0.000000] ACPI: _HPT 3fee9900 00038 (v01 Nvidia NVDAACPI 42302E31 NVDA 00000098)
[    0.000000] ACPI: MCFG 3fee9980 0003C (v01 Nvidia NVDAACPI 42302E31 NVDA 00000000)
[    0.000000] ACPI: APIC 3fee9580 0007C (v01 Nvidia NVDAACPI 42302E31 NVDA 00000000)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] 134MB HIGHMEM available.
[    0.000000] 887MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 377fe000
[    0.000000]   low ram: 0 - 377fe000
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000010 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x000377fe
[    0.000000]   HighMem  0x000377fe -> 0x0003fee0
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[2] active PFN ranges
[    0.000000]     0: 0x00000010 -> 0x0000009f
[    0.000000]     0: 0x00000100 -> 0x0003fee0
[    0.000000] On node 0 totalpages: 261743
[    0.000000] free_area_init_node: node 0, pgdat c07ffd40, node_mem_map c1001200
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3951 pages, LIFO batch:0
[    0.000000]   Normal zone: 1744 pages used for memmap
[    0.000000]   Normal zone: 221486 pages, LIFO batch:31
[    0.000000]   HighMem zone: 270 pages used for memmap
[    0.000000]   HighMem zone: 34260 pages, LIFO batch:7
[    0.000000] Using APIC driver default
[    0.000000] Nvidia board detected. Ignoring ACPI timer override.
[    0.000000] If you got timer trouble try acpi_use_timer_override
[    0.000000] Detected use of extended apic ids on hypertransport bus
[    0.000000] ACPI: PM-Timer IO Port: 0x1008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 17, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 0 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 14 global_irq 14 high edge)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 15 global_irq 15 high edge)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] ACPI: IRQ14 used by override.
[    0.000000] ACPI: IRQ15 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] SMP: Allowing 2 CPUs, 0 hotplug CPUs
[    0.000000] nr_irqs_gsi: 40
[    0.000000] early_res array is doubled to 64 at [16000 - 167ff]
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000f0000
[    0.000000] PM: Registered nosave memory: 00000000000f0000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 3ff00000 (gap: 3ff00000:b0100000)
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] setup_percpu: NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:2 nr_node_ids:1
[    0.000000] PERCPU: Embedded 14 pages/cpu @c1c00000 s36416 r0 d20928 u2097152
[    0.000000] pcpu-alloc: s36416 r0 d20928 u2097152 alloc=1*4194304
[    0.000000] pcpu-alloc: [0] 0 1 
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 259697
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.35-22-generic root=UUID=2e77a75c-daa9-40d1-9158-50bcc739aef6 ro quiet splash
[    0.000000] PID hash table entries: 4096 (order: 2, 16384 bytes)
[    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] allocated 5236800 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] Subtract (47 early reservations)
[    0.000000]   #1 [0000001000 - 0000002000]   EX TRAMPOLINE
[    0.000000]   #2 [0000100000 - 00009a0adc]   TEXT DATA BSS
[    0.000000]   #3 [002f03b000 - 002ff68000]         RAMDISK
[    0.000000]   #4 [00009a1000 - 00009a411d]             BRK
[    0.000000]   #5 [00000f3a10 - 0000100000]   BIOS reserved
[    0.000000]   #6 [00000f3a00 - 00000f3a10]    MP-table mpf
[    0.000000]   #7 [000009f000 - 00000f1f34]   BIOS reserved
[    0.000000]   #8 [00000f2070 - 00000f3a00]   BIOS reserved
[    0.000000]   #9 [00000f1f34 - 00000f2070]    MP-table mpc
[    0.000000]   #10 [0000010000 - 0000011000]      TRAMPOLINE
[    0.000000]   #11 [0000011000 - 0000015000]     ACPI WAKEUP
[    0.000000]   #12 [0000015000 - 0000016000]         PGTABLE
[    0.000000]   #13 [0001000000 - 0001001000]         BOOTMEM
[    0.000000]   #14 [0001001000 - 0001801000]         BOOTMEM
[    0.000000]   #15 [0001801000 - 0001801004]         BOOTMEM
[    0.000000]   #16 [0001801040 - 0001801100]         BOOTMEM
[    0.000000]   #17 [0001801100 - 0001801154]         BOOTMEM
[    0.000000]   #18 [0001801180 - 0001804180]         BOOTMEM
[    0.000000]   #19 [0001804180 - 0001804190]         BOOTMEM
[    0.000000]   #20 [00018041c0 - 0001804dc0]         BOOTMEM
[    0.000000]   #21 [0001804dc0 - 0001804de7]         BOOTMEM
[    0.000000]   #22 [0001804e00 - 0001804f18]         BOOTMEM
[    0.000000]   #23 [0001804f40 - 0001804f80]         BOOTMEM
[    0.000000]   #24 [0001804f80 - 0001804fc0]         BOOTMEM
[    0.000000]   #25 [0001804fc0 - 0001805000]         BOOTMEM
[    0.000000]   #26 [0001805000 - 0001805040]         BOOTMEM
[    0.000000]   #27 [0001805040 - 0001805080]         BOOTMEM
[    0.000000]   #28 [0001805080 - 00018050c0]         BOOTMEM
[    0.000000]   #29 [00018050c0 - 0001805100]         BOOTMEM
[    0.000000]   #30 [0001805100 - 0001805140]         BOOTMEM
[    0.000000]   #31 [0001805140 - 0001805180]         BOOTMEM
[    0.000000]   #32 [0001805180 - 0001805190]         BOOTMEM
[    0.000000]   #33 [00018051c0 - 000180522a]         BOOTMEM
[    0.000000]   #34 [0001805240 - 00018052aa]         BOOTMEM
[    0.000000]   #35 [0001c00000 - 0001c0e000]         BOOTMEM
[    0.000000]   #36 [0001e00000 - 0001e0e000]         BOOTMEM
[    0.000000]   #37 [00018072c0 - 00018072c4]         BOOTMEM
[    0.000000]   #38 [0001807300 - 0001807304]         BOOTMEM
[    0.000000]   #39 [0001807340 - 0001807348]         BOOTMEM
[    0.000000]   #40 [0001807380 - 0001807388]         BOOTMEM
[    0.000000]   #41 [00018073c0 - 0001807468]         BOOTMEM
[    0.000000]   #42 [0001807480 - 00018074e8]         BOOTMEM
[    0.000000]   #43 [0001807500 - 000180b500]         BOOTMEM
[    0.000000]   #44 [000180b500 - 000188b500]         BOOTMEM
[    0.000000]   #45 [000188b500 - 00018cb500]         BOOTMEM
[    0.000000]   #46 [0001e0e000 - 000230c840]         BOOTMEM
[    0.000000] Initializing HighMem for node 0 (000377fe:0003fee0)
[    0.000000] Memory: 1008324k/1047424k available (4928k kernel code, 38648k reserved, 2336k data, 684k init, 138120k highmem)
[    0.000000] virtual kernel memory layout:
[    0.000000]     fixmap  : 0xfff16000 - 0xfffff000   ( 932 kB)
[    0.000000]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[    0.000000]     vmalloc : 0xf7ffe000 - 0xff7fe000   ( 120 MB)
[    0.000000]     lowmem  : 0xc0000000 - 0xf77fe000   ( 887 MB)
[    0.000000]       .init : 0xc0819000 - 0xc08c4000   ( 684 kB)
[    0.000000]       .data : 0xc05d029e - 0xc0818668   (2336 kB)
[    0.000000]       .text : 0xc0100000 - 0xc05d029e   (4928 kB)
[    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.000000] SLUB: Genslabs=13, HWalign=64, Order=0-3, MinObjects=0, CPUs=2, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000]     RCU dyntick-idle grace-period acceleration is enabled.
[    0.000000]     RCU-based detection of stalled CPUs is disabled.
[    0.000000]     Verbose stalled-CPUs detection is disabled.
[    0.000000] NR_IRQS:2304 nr_irqs:512
[    0.000000] spurious 8259A interrupt: IRQ7.
[    0.000000] Console: colour VGA+ 80x25
[    0.000000] console [tty0] enabled
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 2411.263 MHz processor.
[    0.008004] Calibrating delay loop (skipped), value calculated using timer frequency.. 4822.52 BogoMIPS (lpj=9645052)
[    0.008010] pid_max: default: 32768 minimum: 301
[    0.008031] Security Framework initialized
[    0.008054] AppArmor: AppArmor initialized
[    0.008057] Yama: becoming mindful.
[    0.008118] Mount-cache hash table entries: 512
[    0.008255] Initializing cgroup subsys ns
[    0.008259] Initializing cgroup subsys cpuacct
[    0.008264] Initializing cgroup subsys memory
[    0.008274] Initializing cgroup subsys devices
[    0.008277] Initializing cgroup subsys freezer
[    0.008280] Initializing cgroup subsys net_cls
[    0.008306] CPU: Physical Processor ID: 0
[    0.008308] CPU: Processor Core ID: 0
[    0.008312] mce: CPU supports 5 MCE banks
[    0.008321] using C1E aware idle routine
[    0.008330] Performance Events: AMD PMU driver.
[    0.008337] ... version:                0
[    0.008340] ... bit width:              48
[    0.008342] ... generic registers:      4
[    0.008345] ... value mask:             0000ffffffffffff
[    0.008347] ... max period:             00007fffffffffff
[    0.008350] ... fixed-purpose events:   0
[    0.008352] ... event mask:             000000000000000f
[    0.012090] ACPI: Core revision 20100428
[    0.021665] ftrace: converting mcount calls to 0f 1f 44 00 00
[    0.021671] ftrace: allocating 21758 entries in 43 pages
[    0.024074] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.024534] ..TIMER: vector=0x30 apic1=0 pin1=0 apic2=-1 pin2=-1
[    0.067726] CPU0: AMD Athlon(tm) 64 X2 Dual Core Processor 4600+ stepping 02
[    0.068000] Booting Node   0, Processors  #1 Ok.
[    0.012000] Initializing CPU#1
[    0.152125] Brought up 2 CPUs
[    0.152128] Total of 2 processors activated (9645.06 BogoMIPS).
[    0.152355] devtmpfs: initialized
[    0.152881] regulator: core version 0.5
[    0.152916] Time:  7:12:21  Date: 11/14/10
[    0.152955] NET: Registered protocol family 16
[    0.153070] EISA bus registered
[    0.153075] node 0 link 0: io port [9000, ffff]
[    0.153078] TOM: 0000000040000000 aka 1024M
[    0.153081] node 0 link 0: mmio [a0000, bffff]
[    0.153084] node 0 link 0: mmio [40000000, efffffff]
[    0.153086] node 0 link 0: mmio [f4000000, fe02ffff]
[    0.153089] node 0 link 0: mmio [f0000000, f04fffff]
[    0.153092] bus: [00, 04] on node 0 link 0
[    0.153095] bus: 00 index 0 [io  0x0000-0xffff]
[    0.153097] bus: 00 index 1 [mem 0x000a0000-0x000bffff]
[    0.153099] bus: 00 index 2 [mem 0x40000000-0xf3ffffff]
[    0.153102] bus: 00 index 3 [mem 0xf4000000-0xffffffff]
[    0.153108] ACPI: bus type pci registered
[    0.153174] PCI: MMCONFIG for domain 0000 [bus 00-3f] at [mem 0xf0000000-0xf3ffffff] (base 0xf0000000)
[    0.153177] PCI: MMCONFIG at [mem 0xf0000000-0xf3ffffff] reserved in E820
[    0.153179] PCI: Using MMCONFIG for extended config space
[    0.153181] PCI: Using configuration type 1 for base access
[    0.154064] Trying to unpack rootfs image as initramfs...
[    0.154064] bio: create slab <bio-0> at 0
[    0.156100] ACPI: EC: Look up EC in DSDT
[    0.160518] ACPI: Interpreter enabled
[    0.160521] ACPI: (supports S0 S3 S4 S5)
[    0.160541] ACPI: Using IOAPIC for interrupt routing
[    0.169191] ACPI: No dock devices found.
[    0.169194] PCI: Ignoring host bridge windows from ACPI; if necessary, use "pci=use_crs" and report a bug
[    0.169996] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-04])
[    0.171586] pci_root PNP0A08:00: host bridge window [io  0x0000-0x03af] (ignored)
[    0.171588] pci_root PNP0A08:00: host bridge window [io  0x03e0-0x0cf7] (ignored)
[    0.171591] pci_root PNP0A08:00: host bridge window [io  0x9000-0xffff] (ignored)
[    0.171593] pci_root PNP0A08:00: host bridge window [io  0x03b0-0x03df] (ignored)
[    0.171596] pci_root PNP0A08:00: host bridge window [mem 0x000a0000-0x000bffff] (ignored)
[    0.171599] pci_root PNP0A08:00: host bridge window [mem 0x40000000-0xefffffff] (ignored)
[    0.171601] pci_root PNP0A08:00: host bridge window [mem 0xf4000000-0xfe02ffff] (ignored)
[    0.171604] pci_root PNP0A08:00: host bridge window [mem 0xfed40000-0xfed44fff] (ignored)
[    0.171606] pci_root PNP0A08:00: host bridge window [io  0x4700-0x470b] (ignored)
[    0.171609] pci_root PNP0A08:00: host bridge window [io  0x1c00-0x1c80] (ignored)
[    0.171611] pci_root PNP0A08:00: host bridge window [mem 0xfec80000-0xfecbffff] (ignored)
[    0.171783] pci 0000:00:01.1: reg 10: [io  0xfc00-0xfc3f]
[    0.171793] pci 0000:00:01.1: reg 20: [io  0x1c00-0x1c3f]
[    0.171797] pci 0000:00:01.1: reg 24: [io  0xf400-0xf43f]
[    0.171815] pci 0000:00:01.1: PME# supported from D3hot D3cold
[    0.171820] pci 0000:00:01.1: PME# disabled
[    0.171864] pci 0000:00:02.0: reg 10: [mem 0xfe02f000-0xfe02ffff]
[    0.171885] pci 0000:00:02.0: supports D1 D2
[    0.171887] pci 0000:00:02.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.171890] pci 0000:00:02.0: PME# disabled
[    0.171908] pci 0000:00:02.1: reg 10: [mem 0xfe02e000-0xfe02e0ff]
[    0.171933] pci 0000:00:02.1: supports D1 D2
[    0.171935] pci 0000:00:02.1: PME# supported from D0 D1 D2 D3hot D3cold
[    0.171938] pci 0000:00:02.1: PME# disabled
[    0.171991] pci 0000:00:05.0: reg 10: [mem 0xfe028000-0xfe02bfff]
[    0.172025] pci 0000:00:05.0: PME# supported from D3hot D3cold
[    0.172028] pci 0000:00:05.0: PME# disabled
[    0.172057] pci 0000:00:06.0: reg 20: [io  0xf000-0xf00f]
[    0.172085] pci 0000:00:08.0: reg 10: [io  0x09f0-0x09f7]
[    0.172089] pci 0000:00:08.0: reg 14: [io  0x0bf0-0x0bf3]
[    0.172092] pci 0000:00:08.0: reg 18: [io  0x0970-0x0977]
[    0.172096] pci 0000:00:08.0: reg 1c: [io  0x0b70-0x0b73]
[    0.172099] pci 0000:00:08.0: reg 20: [io  0xdc00-0xdc0f]
[    0.172103] pci 0000:00:08.0: reg 24: [mem 0xfe02d000-0xfe02dfff]
[    0.172147] pci 0000:00:09.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.172149] pci 0000:00:09.0: PME# disabled
[    0.172178] pci 0000:00:0b.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.172180] pci 0000:00:0b.0: PME# disabled
[    0.172207] pci 0000:00:0c.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.172210] pci 0000:00:0c.0: PME# disabled
[    0.172288] PCI: peer root bus 00 res updated from pci conf
[    0.172327] pci 0000:01:08.0: reg 10: [io  0xcc00-0xccff]
[    0.172332] pci 0000:01:08.0: reg 14: [mem 0xfdfff000-0xfdfff0ff]
[    0.172350] pci 0000:01:08.0: reg 30: [mem 0x00000000-0x0001ffff pref]
[    0.172363] pci 0000:01:08.0: supports D1 D2
[    0.172365] pci 0000:01:08.0: PME# supported from D1 D2 D3hot D3cold
[    0.172368] pci 0000:01:08.0: PME# disabled
[    0.172393] pci 0000:00:04.0: PCI bridge to [bus 01-01] (subtractive decode)
[    0.172397] pci 0000:00:04.0:   bridge window [io  0xc000-0xcfff]
[    0.172400] pci 0000:00:04.0:   bridge window [mem 0xfdf00000-0xfdffffff]
[    0.172403] pci 0000:00:04.0:   bridge window [mem 0xfde00000-0xfdefffff pref]
[    0.172406] pci 0000:00:04.0:   bridge window [io  0x0000-0xffff] (subtractive decode)
[    0.172408] pci 0000:00:04.0:   bridge window [mem 0x000a0000-0x000bffff] (subtractive decode)
[    0.172411] pci 0000:00:04.0:   bridge window [mem 0x40000000-0xf3ffffff] (subtractive decode)
[    0.172414] pci 0000:00:04.0:   bridge window [mem 0xf4000000-0xffffffff] (subtractive decode)
[    0.172446] pci 0000:02:00.0: reg 10: [mem 0xfa000000-0xfaffffff]
[    0.172453] pci 0000:02:00.0: reg 14: [mem 0xe0000000-0xefffffff 64bit pref]
[    0.172459] pci 0000:02:00.0: reg 1c: [mem 0xfb000000-0xfbffffff 64bit]
[    0.172464] pci 0000:02:00.0: reg 24: [io  0xbc00-0xbc7f]
[    0.172468] pci 0000:02:00.0: reg 30: [mem 0x00000000-0x0001ffff pref]
[    0.172489] pci 0000:02:00.0: disabling ASPM on pre-1.1 PCIe device.  You can enable it with 'pcie_aspm=force'
[    0.172497] pci 0000:00:09.0: PCI bridge to [bus 02-02]
[    0.172500] pci 0000:00:09.0:   bridge window [io  0xb000-0xbfff]
[    0.172503] pci 0000:00:09.0:   bridge window [mem 0xfa000000-0xfcffffff]
[    0.172507] pci 0000:00:09.0:   bridge window [mem 0xe0000000-0xefffffff 64bit pref]
[    0.172527] pci 0000:00:0b.0: PCI bridge to [bus 03-03]
[    0.172530] pci 0000:00:0b.0:   bridge window [io  0xa000-0xafff]
[    0.172533] pci 0000:00:0b.0:   bridge window [mem 0xfdd00000-0xfddfffff]
[    0.172536] pci 0000:00:0b.0:   bridge window [mem 0xfdc00000-0xfdcfffff 64bit pref]
[    0.172556] pci 0000:00:0c.0: PCI bridge to [bus 04-04]
[    0.172559] pci 0000:00:0c.0:   bridge window [io  0x9000-0x9fff]
[    0.172562] pci 0000:00:0c.0:   bridge window [mem 0xfdb00000-0xfdbfffff]
[    0.172565] pci 0000:00:0c.0:   bridge window [mem 0xfda00000-0xfdafffff 64bit pref]
[    0.172573] pci_bus 0000:00: on NUMA node 0
[    0.172578] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.172749] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.HUB0._PRT]
[    0.206509] ACPI: PCI Interrupt Link [LNK1] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.206630] ACPI: PCI Interrupt Link [LNK2] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.206752] ACPI: PCI Interrupt Link [LNK3] (IRQs 5 7 9 *10 11 14 15)
[    0.206871] ACPI: PCI Interrupt Link [LNK4] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.206990] ACPI: PCI Interrupt Link [LNK5] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.207109] ACPI: PCI Interrupt Link [LNK6] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.207228] ACPI: PCI Interrupt Link [LNK7] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.207348] ACPI: PCI Interrupt Link [LNK8] (IRQs *5 7 9 10 11 14 15)
[    0.207466] ACPI: PCI Interrupt Link [LIGP] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.207586] ACPI: PCI Interrupt Link [LP2P] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.207708] ACPI: PCI Interrupt Link [LUBA] (IRQs *5 7 9 10 11 14 15)
[    0.207834] ACPI: PCI Interrupt Link [LMAC] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.207956] ACPI: PCI Interrupt Link [LAZA] (IRQs 5 7 9 10 *11 14 15)
[    0.208086] ACPI: PCI Interrupt Link [LPMU] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.208207] ACPI: PCI Interrupt Link [LSMB] (IRQs 5 7 9 10 *11 14 15)
[    0.208327] ACPI: PCI Interrupt Link [LUB2] (IRQs 5 7 9 *10 11 14 15)
[    0.208451] ACPI: PCI Interrupt Link [LIDE] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.208572] ACPI: PCI Interrupt Link [LSID] (IRQs 5 7 9 10 *11 14 15)
[    0.208696] ACPI: PCI Interrupt Link [LFID] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.208857] ACPI: PCI Interrupt Link [APC1] (IRQs 16) *0, disabled.
[    0.209008] ACPI: PCI Interrupt Link [APC2] (IRQs 17) *0, disabled.
[    0.209160] ACPI: PCI Interrupt Link [APC3] (IRQs 18) *0
[    0.209311] ACPI: PCI Interrupt Link [APC4] (IRQs 19) *0, disabled.
[    0.209463] ACPI: PCI Interrupt Link [APC5] (IRQs 16) *0, disabled.
[    0.209614] ACPI: PCI Interrupt Link [APC6] (IRQs 16) *0, disabled.
[    0.209765] ACPI: PCI Interrupt Link [APC7] (IRQs 16) *0, disabled.
[    0.209915] ACPI: PCI Interrupt Link [APC8] (IRQs 16) *0
[    0.210065] ACPI: PCI Interrupt Link [AIGP] (IRQs 20 21 22 23) *0, disabled.
[    0.210218] ACPI: PCI Interrupt Link [APCF] (IRQs 20 21 22 23) *0
[    0.210370] ACPI: PCI Interrupt Link [APCH] (IRQs 20 21 22 23) *0, disabled.
[    0.210523] ACPI: PCI Interrupt Link [APMU] (IRQs 20 21 22 23) *0, disabled.
[    0.210676] ACPI: PCI Interrupt Link [AAZA] (IRQs 20 21 22 23) *0
[    0.210830] ACPI: PCI Interrupt Link [APCS] (IRQs 20 21 22 23) *0
[    0.210982] ACPI: PCI Interrupt Link [APCL] (IRQs 20 21 22 23) *0
[    0.211134] ACPI: PCI Interrupt Link [APCM] (IRQs 20 21 22 23) *0, disabled.
[    0.211286] ACPI: PCI Interrupt Link [APCZ] (IRQs 20 21 22 23) *0, disabled.
[    0.211438] ACPI: PCI Interrupt Link [APSI] (IRQs 20 21 22 23) *0
[    0.211591] ACPI: PCI Interrupt Link [APSJ] (IRQs 20 21 22 23) *0, disabled.
[    0.211633] HEST: Table is not found!
[    0.211720] vgaarb: device added: PCI:0000:02:00.0,decodes=io+mem,owns=io+mem,locks=none
[    0.211723] vgaarb: loaded
[    0.211875] SCSI subsystem initialized
[    0.216254] libata version 3.00 loaded.
[    0.216254] usbcore: registered new interface driver usbfs
[    0.216254] usbcore: registered new interface driver hub
[    0.216254] usbcore: registered new device driver usb
[    0.216254] ACPI: WMI: Mapper loaded
[    0.216256] PCI: Using ACPI for IRQ routing
[    0.216260] PCI: pci_cache_line_size set to 64 bytes
[    0.216308] reserve RAM buffer: 000000000009f400 - 000000000009ffff 
[    0.216311] reserve RAM buffer: 000000003fee0000 - 000000003fffffff 
[    0.216397] NetLabel: Initializing
[    0.216399] NetLabel:  domain hash size = 128
[    0.216400] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.216412] NetLabel:  unlabeled traffic allowed by default
[    0.225769] AppArmor: AppArmor Filesystem Enabled
[    0.225793] pnp: PnP ACPI init
[    0.225816] ACPI: bus type pnp registered
[    0.230855] pnp: PnP ACPI: found 14 devices
[    0.230857] ACPI: ACPI bus type pnp unregistered
[    0.230860] PnPBIOS: Disabled by ACPI PNP
[    0.230872] system 00:01: [io  0x1000-0x107f] has been reserved
[    0.230874] system 00:01: [io  0x1080-0x10ff] has been reserved
[    0.230877] system 00:01: [io  0x1400-0x147f] has been reserved
[    0.230880] system 00:01: [io  0x1480-0x14ff] has been reserved
[    0.230882] system 00:01: [io  0x1800-0x187f] has been reserved
[    0.230885] system 00:01: [io  0x1880-0x18ff] has been reserved
[    0.230887] system 00:01: [io  0x2000-0x207f] has been reserved
[    0.230890] system 00:01: [io  0x2080-0x20ff] has been reserved
[    0.230894] system 00:01: [mem 0xfefe0000-0xfefe01ff] has been reserved
[    0.230897] system 00:01: [mem 0xfefe1000-0xfefe10ff] has been reserved
[    0.230902] system 00:02: [io  0x04d0-0x04d1] has been reserved
[    0.230905] system 00:02: [io  0x0800-0x087f] has been reserved
[    0.230907] system 00:02: [io  0x0290-0x0297] has been reserved
[    0.230914] system 00:0c: [mem 0xf0000000-0xf3ffffff] has been reserved
[    0.230919] system 00:0d: [mem 0x000f0000-0x000fffff] could not be reserved
[    0.230922] system 00:0d: [mem 0xfeff0000-0xfeff00ff] has been reserved
[    0.230925] system 00:0d: [mem 0x3fee0000-0x3fefffff] could not be reserved
[    0.230927] system 00:0d: [mem 0xffff0000-0xffffffff] has been reserved
[    0.230930] system 00:0d: [mem 0x00000000-0x0009ffff] could not be reserved
[    0.230933] system 00:0d: [mem 0x00100000-0x3fedffff] could not be reserved
[    0.230936] system 00:0d: [mem 0xfec00000-0xfec00fff] could not be reserved
[    0.230939] system 00:0d: [mem 0xfee00000-0xfeefffff] has been reserved
[    0.230942] system 00:0d: [mem 0xfefff000-0xfeffffff] has been reserved
[    0.230944] system 00:0d: [mem 0xfff80000-0xfff80fff] has been reserved
[    0.230947] system 00:0d: [mem 0xfff90000-0xfffbffff] has been reserved
[    0.230950] system 00:0d: [mem 0xfffed000-0xfffeffff] has been reserved
[    0.266774] Switching to clocksource acpi_pm
[    0.267037] pci 0000:01:08.0: BAR 6: assigned [mem 0xfde00000-0xfde1ffff pref]
[    0.267041] pci 0000:00:04.0: PCI bridge to [bus 01-01]
[    0.267045] pci 0000:00:04.0:   bridge window [io  0xc000-0xcfff]
[    0.267048] pci 0000:00:04.0:   bridge window [mem 0xfdf00000-0xfdffffff]
[    0.267052] pci 0000:00:04.0:   bridge window [mem 0xfde00000-0xfdefffff pref]
[    0.267057] pci 0000:02:00.0: BAR 6: assigned [mem 0xfc000000-0xfc01ffff pref]
[    0.267059] pci 0000:00:09.0: PCI bridge to [bus 02-02]
[    0.267061] pci 0000:00:09.0:   bridge window [io  0xb000-0xbfff]
[    0.267064] pci 0000:00:09.0:   bridge window [mem 0xfa000000-0xfcffffff]
[    0.267068] pci 0000:00:09.0:   bridge window [mem 0xe0000000-0xefffffff 64bit pref]
[    0.267071] pci 0000:00:0b.0: PCI bridge to [bus 03-03]
[    0.267073] pci 0000:00:0b.0:   bridge window [io  0xa000-0xafff]
[    0.267076] pci 0000:00:0b.0:   bridge window [mem 0xfdd00000-0xfddfffff]
[    0.267079] pci 0000:00:0b.0:   bridge window [mem 0xfdc00000-0xfdcfffff 64bit pref]
[    0.267083] pci 0000:00:0c.0: PCI bridge to [bus 04-04]
[    0.267085] pci 0000:00:0c.0:   bridge window [io  0x9000-0x9fff]
[    0.267088] pci 0000:00:0c.0:   bridge window [mem 0xfdb00000-0xfdbfffff]
[    0.267091] pci 0000:00:0c.0:   bridge window [mem 0xfda00000-0xfdafffff 64bit pref]
[    0.267100] pci 0000:00:04.0: setting latency timer to 64
[    0.267105] pci 0000:00:09.0: setting latency timer to 64
[    0.267110] pci 0000:00:0b.0: setting latency timer to 64
[    0.267114] pci 0000:00:0c.0: setting latency timer to 64
[    0.267117] pci_bus 0000:00: resource 4 [io  0x0000-0xffff]
[    0.267120] pci_bus 0000:00: resource 5 [mem 0x000a0000-0x000bffff]
[    0.267122] pci_bus 0000:00: resource 6 [mem 0x40000000-0xf3ffffff]
[    0.267124] pci_bus 0000:00: resource 7 [mem 0xf4000000-0xffffffff]
[    0.267127] pci_bus 0000:01: resource 0 [io  0xc000-0xcfff]
[    0.267129] pci_bus 0000:01: resource 1 [mem 0xfdf00000-0xfdffffff]
[    0.267132] pci_bus 0000:01: resource 2 [mem 0xfde00000-0xfdefffff pref]
[    0.267134] pci_bus 0000:01: resource 4 [io  0x0000-0xffff]
[    0.267136] pci_bus 0000:01: resource 5 [mem 0x000a0000-0x000bffff]
[    0.267139] pci_bus 0000:01: resource 6 [mem 0x40000000-0xf3ffffff]
[    0.267141] pci_bus 0000:01: resource 7 [mem 0xf4000000-0xffffffff]
[    0.267143] pci_bus 0000:02: resource 0 [io  0xb000-0xbfff]
[    0.267146] pci_bus 0000:02: resource 1 [mem 0xfa000000-0xfcffffff]
[    0.267148] pci_bus 0000:02: resource 2 [mem 0xe0000000-0xefffffff 64bit pref]
[    0.267151] pci_bus 0000:03: resource 0 [io  0xa000-0xafff]
[    0.267153] pci_bus 0000:03: resource 1 [mem 0xfdd00000-0xfddfffff]
[    0.267155] pci_bus 0000:03: resource 2 [mem 0xfdc00000-0xfdcfffff 64bit pref]
[    0.267158] pci_bus 0000:04: resource 0 [io  0x9000-0x9fff]
[    0.267160] pci_bus 0000:04: resource 1 [mem 0xfdb00000-0xfdbfffff]
[    0.267163] pci_bus 0000:04: resource 2 [mem 0xfda00000-0xfdafffff 64bit pref]
[    0.267199] NET: Registered protocol family 2
[    0.267255] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.267522] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.267996] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.267996] TCP: Hash tables configured (established 131072 bind 65536)
[    0.267996] TCP reno registered
[    0.267996] UDP hash table entries: 512 (order: 2, 16384 bytes)
[    0.267996] UDP-Lite hash table entries: 512 (order: 2, 16384 bytes)
[    0.267996] NET: Registered protocol family 1
[    0.285076] pci 0000:00:00.0: Found enabled HT MSI Mapping
[    0.285124] pci 0000:00:00.0: Found enabled HT MSI Mapping
[    0.285178] pci 0000:00:00.0: Found enabled HT MSI Mapping
[    0.285232] pci 0000:00:00.0: Found enabled HT MSI Mapping
[    0.285291] pci 0000:00:00.0: Found enabled HT MSI Mapping
[    0.285353] pci 0000:00:00.0: Found enabled HT MSI Mapping
[    0.285370] pci 0000:02:00.0: Boot video device
[    0.285373] PCI: CLS 64 bytes, default 64
[    0.285583] cpufreq-nforce2: No nForce2 chipset.
[    0.285611] Scanning for low memory corruption every 60 seconds
[    0.285707] audit: initializing netlink socket (disabled)
[    0.285717] type=2000 audit(1289718741.284:1): initialized
[    0.295175] highmem bounce pool size: 64 pages
[    0.295180] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    0.296381] VFS: Disk quotas dquot_6.5.2
[    0.296432] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.296932] fuse init (API version 7.14)
[    0.297026] msgmni has been set to 1699
[    0.297273] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.297276] io scheduler noop registered
[    0.297278] io scheduler deadline registered
[    0.297288] io scheduler cfq registered (default)
[    0.297382] pcieport 0000:00:09.0: setting latency timer to 64
[    0.297399]   alloc irq_desc for 40 on node -1
[    0.297401]   alloc kstat_irqs on node -1
[    0.297409] pcieport 0000:00:09.0: irq 40 for MSI/MSI-X
[    0.297450] pcieport 0000:00:0b.0: setting latency timer to 64
[    0.297463]   alloc irq_desc for 41 on node -1
[    0.297464]   alloc kstat_irqs on node -1
[    0.297469] pcieport 0000:00:0b.0: irq 41 for MSI/MSI-X
[    0.297508] pcieport 0000:00:0c.0: setting latency timer to 64
[    0.297521]   alloc irq_desc for 42 on node -1
[    0.297523]   alloc kstat_irqs on node -1
[    0.297527] pcieport 0000:00:0c.0: irq 42 for MSI/MSI-X
[    0.297587] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.297608] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.297779] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0
[    0.297785] ACPI: Power Button [PWRB]
[    0.297844] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
[    0.297847] ACPI: Power Button [PWRF]
[    0.297898] ACPI: Fan [FAN] (on)
[    0.298205] ACPI: acpi_idle registered with cpuidle
[    0.302419] thermal LNXTHERM:01: registered as thermal_zone0
[    0.302428] ACPI: Thermal Zone [THRM] (40 C)
[    0.302484] ERST: Table is not found!
[    0.302675] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    0.302769] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.303047] 00:08: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.304056] brd: module loaded
[    0.304504] loop: module loaded
[    0.304739] pata_acpi 0000:00:06.0: setting latency timer to 64
[    0.305077] ACPI: PCI Interrupt Link [APSI] enabled at IRQ 23
[    0.305084]   alloc irq_desc for 23 on node -1
[    0.305087]   alloc kstat_irqs on node -1
[    0.305097] pata_acpi 0000:00:08.0: PCI INT A -> Link[APSI] -> GSI 23 (level, low) -> IRQ 23
[    0.305111] pata_acpi 0000:00:08.0: setting latency timer to 64
[    0.305117] pata_acpi 0000:00:08.0: PCI INT A disabled
[    0.305423] Fixed MDIO Bus: probed
[    0.305455] PPP generic driver version 2.4.2
[    0.305490] tun: Universal TUN/TAP device driver, 1.6
[    0.305491] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.305560] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.305809] ACPI: PCI Interrupt Link [APCL] enabled at IRQ 22
[    0.305811]   alloc irq_desc for 22 on node -1
[    0.305813]   alloc kstat_irqs on node -1
[    0.305820] ehci_hcd 0000:00:02.1: PCI INT B -> Link[APCL] -> GSI 22 (level, low) -> IRQ 22
[    0.305836] ehci_hcd 0000:00:02.1: setting latency timer to 64
[    0.305839] ehci_hcd 0000:00:02.1: EHCI Host Controller
[    0.305875] ehci_hcd 0000:00:02.1: new USB bus registered, assigned bus number 1
[    0.305898] ehci_hcd 0000:00:02.1: debug port 1
[    0.305905] ehci_hcd 0000:00:02.1: cache line size of 64 is not supported
[    0.305928] ehci_hcd 0000:00:02.1: irq 22, io mem 0xfe02e000
[    0.305990] isapnp: Scanning for PnP cards...
[    0.354841] ehci_hcd 0000:00:02.1: USB 2.0 started, EHCI 1.00
[    0.354944] hub 1-0:1.0: USB hub found
[    0.354949] hub 1-0:1.0: 8 ports detected
[    0.355011] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.355263] ACPI: PCI Interrupt Link [APCF] enabled at IRQ 21
[    0.355266]   alloc irq_desc for 21 on node -1
[    0.355267]   alloc kstat_irqs on node -1
[    0.355274] ohci_hcd 0000:00:02.0: PCI INT A -> Link[APCF] -> GSI 21 (level, low) -> IRQ 21
[    0.355282] ohci_hcd 0000:00:02.0: setting latency timer to 64
[    0.355285] ohci_hcd 0000:00:02.0: OHCI Host Controller
[    0.355316] ohci_hcd 0000:00:02.0: new USB bus registered, assigned bus number 2
[    0.355339] ohci_hcd 0000:00:02.0: irq 21, io mem 0xfe02f000
[    0.444204] hub 2-0:1.0: USB hub found
[    0.444209] hub 2-0:1.0: 8 ports detected
[    0.444265] uhci_hcd: USB Universal Host Controller Interface driver
[    0.444346] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    0.444753] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.444759] serio: i8042 AUX port at 0x60,0x64 irq 12
[    0.444856] mice: PS/2 mouse device common for all mice
[    0.444977] rtc_cmos 00:04: RTC can wake from S4
[    0.445036] rtc_cmos 00:04: rtc core: registered rtc_cmos as rtc0
[    0.445069] rtc0: alarms up to one year, y3k, 242 bytes nvram
[    0.445160] device-mapper: uevent: version 1.0.3
[    0.488666] device-mapper: ioctl: 4.17.0-ioctl (2010-03-05) initialised: dm-devel@redhat.com
[    0.534258] Freeing initrd memory: 15540k freed
[    0.544309] device-mapper: multipath: version 1.1.1 loaded
[    0.544313] device-mapper: multipath round-robin: version 1.0.0 loaded
[    0.544519] EISA: Probing bus 0 at eisa.0
[    0.544522] EISA: Cannot allocate resource for mainboard
[    0.544524] Cannot allocate resource for EISA slot 1
[    0.544526] Cannot allocate resource for EISA slot 2
[    0.544528] Cannot allocate resource for EISA slot 3
[    0.544530] Cannot allocate resource for EISA slot 4
[    0.544532] Cannot allocate resource for EISA slot 5
[    0.544534] Cannot allocate resource for EISA slot 6
[    0.544536] Cannot allocate resource for EISA slot 7
[    0.544538] Cannot allocate resource for EISA slot 8
[    0.544540] EISA: Detected 0 cards.
[    0.544615] cpuidle: using governor ladder
[    0.544617] cpuidle: using governor menu
[    0.544899] TCP cubic registered
[    0.545009] NET: Registered protocol family 10
[    0.545378] lo: Disabled Privacy Extensions
[    0.545619] NET: Registered protocol family 17
[    0.545654] powernow-k8: Found 1 AMD Athlon(tm) 64 X2 Dual Core Processor 4600+ (2 cpu cores) (version 2.20.00)
[    0.545704] powernow-k8:    0 : fid 0x10 (2400 MHz), vid 0x8
[    0.545706] powernow-k8:    1 : fid 0xe (2200 MHz), vid 0xa
[    0.545708] powernow-k8:    2 : fid 0xc (2000 MHz), vid 0xc
[    0.545710] powernow-k8:    3 : fid 0xa (1800 MHz), vid 0xe
[    0.545713] powernow-k8:    4 : fid 0x2 (1000 MHz), vid 0x12
[    0.545750] Using IPI No-Shortcut mode
[    0.545840] PM: Resume from disk failed.
[    0.545851] registered taskstats version 1
[    0.546024]   Magic number: 2:989:217
[    0.546131] rtc_cmos 00:04: setting system clock to 2010-11-14 07:12:21 UTC (1289718741)
[    0.546134] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.546136] EDD information not available.
[    0.553235] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input2
[    0.662480] isapnp: No Plug & Play device found
[    0.662501] Freeing unused kernel memory: 684k freed
[    0.662943] Write protecting the kernel text: 4932k
[    0.662978] Write protecting the kernel read-only data: 1976k
[    0.681265] udev[77]: starting version 163
[    0.731047] pata_amd 0000:00:06.0: version 0.4.1
[    0.731094] pata_amd 0000:00:06.0: setting latency timer to 64
[    0.762134] scsi0 : pata_amd
[    0.771716] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    0.772039] ACPI: PCI Interrupt Link [APC3] enabled at IRQ 18
[    0.772045]   alloc irq_desc for 18 on node -1
[    0.772047]   alloc kstat_irqs on node -1
[    0.772059] r8169 0000:01:08.0: PCI INT A -> Link[APC3] -> GSI 18 (level, low) -> IRQ 18
[    0.772087] r8169 0000:01:08.0: (unregistered net_device): no PCI Express capability
[    0.772572] r8169 0000:01:08.0: eth0: RTL8169sc/8110sc at 0xf8074000, 00:18:37:03:86:40, XID 18000000 IRQ 18
[    0.781071] scsi1 : pata_amd
[    0.781710] ata1: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xf000 irq 14
[    0.781713] ata2: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xf008 irq 15
[    0.781844] sata_nv 0000:00:08.0: version 3.5
[    0.781862] sata_nv 0000:00:08.0: PCI INT A -> Link[APSI] -> GSI 23 (level, low) -> IRQ 23
[    0.781916] sata_nv 0000:00:08.0: setting latency timer to 64
[    0.794833] Floppy drive(s): fd0 is 1.44M
[    0.806712] scsi2 : sata_nv
[    0.808787] scsi3 : sata_nv
[    0.808995] ata3: SATA max UDMA/133 cmd 0x9f0 ctl 0xbf0 bmdma 0xdc00 irq 23
[    0.808998] ata4: SATA max UDMA/133 cmd 0x970 ctl 0xb70 bmdma 0xdc08 irq 23
[    0.811971] FDC 0 is a post-1991 82077
[    0.944377] ata1.00: ATAPI: PIONEER DVD-RW  DVR-112D, 1.21, max UDMA/66
[    0.944401] ata1: nv_mode_filter: 0x1f39f&0x1f39f->0x1f39f, BIOS=0x1f000 (0xc5000000) ACPI=0x1f01f (30:600:0x13)
[    0.960279] ata1.00: configured for UDMA/66
[    0.973025] scsi 0:0:0:0: CD-ROM            PIONEER  DVD-RW  DVR-112D 1.21 PQ: 0 ANSI: 5
[    0.996615] sr0: scsi3-mmc drive: 40x/40x writer cd/rw xa/form2 cdda tray
[    0.996618] Uniform CD-ROM driver Revision: 3.20
[    0.996719] sr 0:0:0:0: Attached scsi CD-ROM sr0
[    0.996776] sr 0:0:0:0: Attached scsi generic sg0 type 5
[    0.996846] ata2: port disabled. ignoring.
[    1.130245] ata3: SATA link down (SStatus 0 SControl 300)
[    1.596040] ata4: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    1.604134] ata4.00: ATA-8: WDC WD10EADS-65L5B1, 01.01A01, max UDMA/133
[    1.604137] ata4.00: 1953525168 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    1.620145] ata4.00: configured for UDMA/133
[    1.620255] scsi 3:0:0:0: Direct-Access     ATA      WDC WD10EADS-65L 01.0 PQ: 0 ANSI: 5
[    1.620377] sd 3:0:0:0: [sda] 1953525168 512-byte logical blocks: (1.00 TB/931 GiB)
[    1.620380] sd 3:0:0:0: Attached scsi generic sg1 type 0
[    1.620427] sd 3:0:0:0: [sda] Write Protect is off
[    1.620430] sd 3:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.620468] sd 3:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.620676]  sda: sda1 sda2 sda3
[    1.672032] sd 3:0:0:0: [sda] Attached SCSI disk
[    2.196892] EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: (null)
[    8.348090] udev[382]: starting version 163
[    8.384207] i2c i2c-0: nForce2 SMBus adapter at 0x1c00
[    8.384233] i2c i2c-1: nForce2 SMBus adapter at 0xf400
[    8.396342] k8temp 0000:00:18.3: Temperature readouts might be wrong - check erratum #141
[    8.451918] lp: driver loaded but no devices found
[    8.492179] Adding 4105212k swap on /dev/sda3.  Priority:-1 extents:1 across:4105212k 
[    8.507238] Linux agpgart interface v0.103
[    8.614221] parport_pc 00:09: reported by Plug and Play ACPI
[    8.614279] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
[    8.637702] psmouse serio1: ID: 10 00 64
[    8.659591] ppdev: user-space parallel port driver
[    8.680089] nvidia: module license 'NVIDIA' taints kernel.
[    8.680094] Disabling lock debugging due to kernel taint
[    8.683497] type=1400 audit(1289718749.630:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient3" pid=689 comm="apparmor_parser"
[    8.683774] type=1400 audit(1289718749.630:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=689 comm="apparmor_parser"
[    8.683936] type=1400 audit(1289718749.630:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=689 comm="apparmor_parser"
[    8.716252] lp0: using parport0 (interrupt-driven).
[    8.792389] ACPI: PCI Interrupt Link [AAZA] enabled at IRQ 20
[    8.792395]   alloc irq_desc for 20 on node -1
[    8.792398]   alloc kstat_irqs on node -1
[    8.792408] HDA Intel 0000:00:05.0: PCI INT B -> Link[AAZA] -> GSI 20 (level, low) -> IRQ 20
[    8.792411] hda_intel: Disable MSI for Nvidia chipset
[    8.792449] HDA Intel 0000:00:05.0: setting latency timer to 64
[    9.330757] input: ImPS/2 Logitech Wheel Mouse as /devices/platform/i8042/serio1/input/input3
[    9.408019] hda_codec: ALC883: BIOS auto-probing.
[    9.898077] ACPI: PCI Interrupt Link [APC8] enabled at IRQ 16
[    9.898084]   alloc irq_desc for 16 on node -1
[    9.898087]   alloc kstat_irqs on node -1
[    9.898097] nvidia 0000:02:00.0: PCI INT A -> Link[APC8] -> GSI 16 (level, low) -> IRQ 16
[    9.898104] nvidia 0000:02:00.0: setting latency timer to 64
[    9.898109] vgaarb: device changed decodes: PCI:0000:02:00.0,olddecodes=io+mem,decodes=none:owns=io+mem
[    9.899102] NVRM: loading NVIDIA UNIX x86 Kernel Module  260.19.06  Mon Sep 13 06:35:06 PDT 2010
[   10.003097] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
[   10.313892] EXT4-fs (sda2): mounted filesystem with ordered data mode. Opts: (null)
[   10.482979] r8169 0000:01:08.0: eth0: link up
[   10.496775] type=1400 audit(1289718751.446:5): apparmor="STATUS" operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" pid=1014 comm="apparmor_parser"
[   10.498465] type=1400 audit(1289718751.446:6): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient3" pid=1015 comm="apparmor_parser"
[   10.498730] type=1400 audit(1289718751.446:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=1015 comm="apparmor_parser"
[   10.498880] type=1400 audit(1289718751.446:8): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=1015 comm="apparmor_parser"
[   10.502644] type=1400 audit(1289718751.450:9): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince" pid=1016 comm="apparmor_parser"
[   10.510936] type=1400 audit(1289718751.458:10): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince-previewer" pid=1016 comm="apparmor_parser"
[   10.516683] type=1400 audit(1289718751.466:11): apparmor="STATUS" operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" pid=1018 comm="apparmor_parser"
[   12.337396] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,commit=0
[   12.381692] EXT4-fs (sda2): re-mounted. Opts: commit=0
[   13.405434] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,commit=0
[   13.408133] EXT4-fs (sda2): re-mounted. Opts: commit=0
[   20.520016] eth0: no IPv6 routers present
[   26.983186] padlock: VIA PadLock not detected.
[   72.345442] Valid eCryptfs headers not found in file header region or xattr region
[   72.345449] Either the lower file is not in a valid eCryptfs format, or the key could not be retrieved. Plaintext passthrough mode is not enabled; returning -EIO
[   72.347283] Valid eCryptfs headers not found in file header region or xattr region
[   72.347289] Either the lower file is not in a valid eCryptfs format, or the key could not be retrieved. Plaintext passthrough mode is not enabled; returning -EIO
[   72.347518] Valid eCryptfs headers not found in file header region or xattr region
[   72.347521] Either the lower file is not in a valid eCryptfs format, or the key could not be retrieved. Plaintext passthrough mode is not enabled; returning -EIO
[   72.347691] Valid eCryptfs headers not found in file header region or xattr region
[   72.347694] Either the lower file is not in a valid eCryptfs format, or the key could not be retrieved. Plaintext passthrough mode is not enabled; returning -EIO
[   72.485074] Valid eCryptfs headers not found in file header region or xattr region
[   72.485079] Either the lower file is not in a valid eCryptfs format, or the key could not be retrieved. Plaintext passthrough mode is not enabled; returning -EIO
[   73.152030] Clocksource tsc unstable (delta = -186403425 ns)
[   78.162378] Valid eCryptfs headers not found in file header region or xattr region
[   78.162384] Either the lower file is not in a valid eCryptfs format, or the key could not be retrieved. Plaintext passthrough mode is not enabled; returning -EIO
[   78.164279] Valid eCryptfs headers not found in file header region or xattr region
[   78.164286] Either the lower file is not in a valid eCryptfs format, or the key could not be retrieved. Plaintext passthrough mode is not enabled; returning -EIO
[   78.164488] Valid eCryptfs headers not found in file header region or xattr region
[   78.164491] Either the lower file is not in a valid eCryptfs format, or the key could not be retrieved. Plaintext passthrough mode is not enabled; returning -EIO
[   78.164662] Valid eCryptfs headers not found in file header region or xattr region
[   78.164664] Either the lower file is not in a valid eCryptfs format, or the key could not be retrieved. Plaintext passthrough mode is not enabled; returning -EIO
[   78.166644] Valid eCryptfs headers not found in file header region or xattr region
[   78.166648] Either the lower file is not in a valid eCryptfs format, or the key could not be retrieved. Plaintext passthrough mode is not enabled; returning -EIO
[ 4289.652151] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,commit=0
[ 4289.829721] EXT4-fs (sda2): re-mounted. Opts: commit=0
[ 4291.958603] PM: Syncing filesystems ... done.
[ 4291.963250] PM: Preparing system for mem sleep
[ 4291.963257] Freezing user space processes ... (elapsed 0.01 seconds) done.
[ 4291.980039] Freezing remaining freezable tasks ... (elapsed 0.01 seconds) done.
[ 4291.996029] PM: Entering mem sleep
[ 4291.996045] Suspending console(s) (use no_console_suspend to debug)
[ 4291.996446] sd 3:0:0:0: [sda] Synchronizing SCSI cache
[ 4292.008306] ACPI handle has no context!
[ 4292.008583] parport_pc 00:09: disabled
[ 4292.008788] serial 00:08: disabled
[ 4292.009369] ata2: port disabled. ignoring.
[ 4292.009475] ehci_hcd 0000:00:02.1: PCI INT B disabled
[ 4292.009487] ohci_hcd 0000:00:02.0: PCI INT A disabled
[ 4292.149758] sd 3:0:0:0: [sda] Stopping disk
[ 4292.220032] HDA Intel 0000:00:05.0: PCI INT B disabled
[ 4292.236019] PM: suspend of drv:HDA Intel dev:0000:00:05.0 complete after 226.586 msecs
[ 4292.353142] PM: suspend of drv:nvidia dev:0000:02:00.0 complete after 344.273 msecs
[ 4292.353159] PM: suspend of drv:pcieport dev:0000:00:09.0 complete after 343.837 msecs
[ 4293.014759] PM: suspend of drv:sd dev:3:0:0:0 complete after 1018.320 msecs
[ 4293.014773] PM: suspend of drv:scsi dev:target3:0:0 complete after 1018.207 msecs
[ 4293.014784] PM: suspend of drv:scsi dev:host3 complete after 1018.181 msecs
[ 4293.014865] sata_nv 0000:00:08.0: PCI INT A disabled
[ 4293.028017] PM: suspend of drv:sata_nv dev:0000:00:08.0 complete after 1018.693 msecs
[ 4293.028035] PM: suspend of drv: dev:pci0000:00 complete after 1018.514 msecs
[ 4293.028048] PM: suspend of devices complete after 1031.825 msecs
[ 4293.028051] PM: suspend devices took 1.036 seconds
[ 4293.028558] r8169 0000:01:08.0: PME# enabled
[ 4293.028565] pci 0000:00:04.0: wake-up capability enabled by ACPI
[ 4293.076255] PM: late suspend of devices complete after 48.200 msecs
[ 4293.076340] ACPI: Preparing to enter system sleep state S3
[ 4293.076687] PM: Saving platform NVS memory
[ 4293.076945] Disabling non-boot CPUs ...
[ 4293.080156] Broke affinity for irq 16
[ 4293.080188] Broke affinity for irq 23
[ 4293.184022] CPU 1 is now offline
[ 4293.184024] SMP alternatives: switching to UP code
[ 4293.187459] Back to C!
[ 4293.187459] PM: Restoring platform NVS memory
[ 4293.188954] Enabling non-boot CPUs ...
[ 4293.189139] SMP alternatives: switching to SMP code
[ 4293.192148] Booting Node 0 Processor 1 APIC 0x1
[ 4293.187080] Initializing CPU#1
[ 4293.312249] CPU1 is up
[ 4293.312365] ACPI: Waking up from system sleep state S3
[ 4293.312759] pci 0000:00:00.0: restoring config space at offset 0xf (was 0x0, writing 0xff)
[ 4293.312889] ohci_hcd 0000:00:02.0: restoring config space at offset 0x1 (was 0xb00007, writing 0xb00003)
[ 4293.312913] ehci_hcd 0000:00:02.1: restoring config space at offset 0x1 (was 0xb00006, writing 0xb00002)
[ 4293.312931] pci 0000:00:04.0: restoring config space at offset 0xf (was 0x20400ff, writing 0x60400ff)
[ 4293.312981] pci 0000:00:00.0: Found enabled HT MSI Mapping
[ 4293.312999] HDA Intel 0000:00:05.0: restoring config space at offset 0x1 (was 0xb00006, writing 0xb00002)
[ 4293.313057] pci 0000:00:00.0: Found enabled HT MSI Mapping
[ 4293.313088] sata_nv 0000:00:08.0: restoring config space at offset 0x1 (was 0xb00000, writing 0xb00007)
[ 4293.313140] pci 0000:00:00.0: Found enabled HT MSI Mapping
[ 4293.313156] pcieport 0000:00:09.0: restoring config space at offset 0x1 (was 0x100007, writing 0x100407)
[ 4293.313217] pci 0000:00:00.0: Found enabled HT MSI Mapping
[ 4293.313232] pcieport 0000:00:0b.0: restoring config space at offset 0x1 (was 0x100007, writing 0x100407)
[ 4293.313295] pci 0000:00:00.0: Found enabled HT MSI Mapping
[ 4293.313310] pcieport 0000:00:0c.0: restoring config space at offset 0x1 (was 0x100007, writing 0x100407)
[ 4293.313377] pci 0000:00:00.0: Found enabled HT MSI Mapping
[ 4293.313428] r8169 0000:01:08.0: restoring config space at offset 0x3 (was 0x2010, writing 0x4008)
[ 4293.313433] r8169 0000:01:08.0: restoring config space at offset 0x1 (was 0x2b00007, writing 0x2b00017)
[ 4293.313452] nvidia 0000:02:00.0: restoring config space at offset 0xf (was 0x100, writing 0x105)
[ 4293.313458] nvidia 0000:02:00.0: restoring config space at offset 0x9 (was 0x1, writing 0xbc01)
[ 4293.313462] nvidia 0000:02:00.0: restoring config space at offset 0x7 (was 0x4, writing 0xfb000004)
[ 4293.313466] nvidia 0000:02:00.0: restoring config space at offset 0x5 (was 0xc, writing 0xe000000c)
[ 4293.313470] nvidia 0000:02:00.0: restoring config space at offset 0x4 (was 0x0, writing 0xfa000000)
[ 4293.313474] nvidia 0000:02:00.0: restoring config space at offset 0x1 (was 0x100000, writing 0x100007)
[ 4293.313939] PM: early resume of devices complete after 1.364 msecs
[ 4293.314052] ohci_hcd 0000:00:02.0: PCI INT A -> Link[APCF] -> GSI 21 (level, low) -> IRQ 21
[ 4293.314058] ohci_hcd 0000:00:02.0: setting latency timer to 64
[ 4293.314073] ehci_hcd 0000:00:02.1: PCI INT B -> Link[APCL] -> GSI 22 (level, low) -> IRQ 22
[ 4293.314080] pci 0000:00:04.0: setting latency timer to 64
[ 4293.314079] ehci_hcd 0000:00:02.1: setting latency timer to 64
[ 4293.314092] HDA Intel 0000:00:05.0: PCI INT B -> Link[AAZA] -> GSI 20 (level, low) -> IRQ 20
[ 4293.314096] HDA Intel 0000:00:05.0: setting latency timer to 64
[ 4293.314128] pata_amd 0000:00:06.0: setting latency timer to 64
[ 4293.314136] sata_nv 0000:00:08.0: PCI INT A -> Link[APSI] -> GSI 23 (level, low) -> IRQ 23
[ 4293.314139] sata_nv 0000:00:08.0: setting latency timer to 64
[ 4293.314182] pci 0000:00:04.0: wake-up capability disabled by ACPI
[ 4293.314186] r8169 0000:01:08.0: PME# disabled
[ 4293.314721] ata2: port disabled. ignoring.
[ 4293.315405] sd 3:0:0:0: [sda] Starting disk
[ 4293.330417] serial 00:08: activated
[ 4293.331336] parport_pc 00:09: activated
[ 4293.417028] PM: resume of drv:usb dev:usb2 complete after 102.677 msecs
[ 4293.417035] PM: resume of drv:hub dev:2-0:1.0 complete after 102.681 msecs
[ 4293.529047] PM: resume of drv:nvidia dev:0000:02:00.0 complete after 214.869 msecs
[ 4293.589335] ata1.00: ACPI cmd ef/03:44:00:00:00:a0 (SET FEATURES) filtered out
[ 4293.589339] ata1.00: ACPI cmd ef/03:0c:00:00:00:a0 (SET FEATURES) filtered out
[ 4293.589368] ata1: nv_mode_filter: 0x1f39f&0x1f39f->0x1f39f, BIOS=0x1f000 (0xc5000000) ACPI=0x1f01f (30:600:0x13)
[ 4293.605274] ata1.00: configured for UDMA/66
[ 4293.934839] psmouse serio1: ID: 10 00 64
[ 4294.047257] ata3: SATA link down (SStatus 0 SControl 300)
[ 4296.417012] 
[ 4296.417013] floppy driver state
[ 4296.417015] -------------------
[ 4296.417025] now=999104 last interrupt=4294892499 diff=1073901 last called handler=reset_interrupt
[ 4296.417027] timeout_message=lock fdc
[ 4296.417028] last output bytes:
[ 4296.417030]  8 80 4294892494
[ 4296.417031]  8 80 4294892494
[ 4296.417033]  8 80 4294892494
[ 4296.417034]  8 80 4294892498
[ 4296.417036]  8 80 4294892498
[ 4296.417038]  8 80 4294892498
[ 4296.417039]  8 80 4294892498
[ 4296.417041]  e 80 4294892498
[ 4296.417042] 13 80 4294892498
[ 4296.417044]  0 90 4294892498
[ 4296.417045] 1a 90 4294892498
[ 4296.417047]  0 90 4294892498
[ 4296.417048] 12 90 4294892498
[ 4296.417050]  0 90 4294892498
[ 4296.417051] 14 90 4294892498
[ 4296.417053] 18 80 4294892498
[ 4296.417055]  8 80 4294892499
[ 4296.417056]  8 80 4294892499
[ 4296.417058]  8 80 4294892499
[ 4296.417059]  8 80 4294892499
[ 4296.417060] last result at 4294892499
[ 4296.417062] last redo_fd_request at 4294892499
[ 4296.417073] status=0
[ 4296.417075] fdc_busy=1
[ 4296.417078] do_floppy=reset_interrupt
[ 4296.417079] cont=f809b4d4
[ 4296.417080] current_req=(null)
[ 4296.417082] command_status=-1
[ 4296.417083] 
[ 4296.417085] floppy0: floppy timeout called
[ 4296.417095] PM: resume of drv:floppy dev:floppy.0 complete after 2999.912 msecs
[ 4298.821016] ata4: link is slow to respond, please be patient (ready=0)
[ 4301.733035] ata4: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[ 4301.741122] ata4.00: ACPI cmd ef/03:46:00:00:00:a0 (SET FEATURES) filtered out
[ 4301.757136] ata4.00: configured for UDMA/133
[ 4301.790903] PM: resume of drv:sd dev:3:0:0:0 complete after 8475.496 msecs
[ 4301.790915] PM: resume of drv:scsi_disk dev:3:0:0:0 complete after 5373.795 msecs
[ 4301.790921] PM: resume of drv:scsi_device dev:3:0:0:0 complete after 8475.450 msecs
[ 4301.791065] PM: resume of devices complete after 8477.077 msecs
[ 4301.791215] PM: resume devices took 8.476 seconds
[ 4301.791243] PM: Finishing wakeup.
[ 4301.791245] Restarting tasks ... done.
[ 4302.164609] r8169 0000:01:08.0: eth0: link up
[ 4302.799231] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,commit=0
[ 4303.246085] EXT4-fs (sda2): re-mounted. Opts: commit=0
[ 4312.848024] eth0: no IPv6 routers present
[ 4434.760038] usb 1-5: new high speed USB device using ehci_hcd and address 2
[ 4434.828073] hub 1-0:1.0: unable to enumerate USB device on port 5
[ 4437.500037] usb 1-5: new high speed USB device using ehci_hcd and address 3
[ 4437.675033] Initializing USB Mass Storage driver...
[ 4437.675298] scsi4 : usb-storage 1-5:1.0
[ 4437.675945] usbcore: registered new interface driver usb-storage
[ 4437.675951] USB Mass Storage support registered.
[ 4438.677046] scsi 4:0:0:0: Direct-Access     SanDisk  Sansa Fuze 8GB   v02. PQ: 0 ANSI: 0
[ 4438.677623] scsi 4:0:0:1: Direct-Access     SanDisk  Sansa Fuze 8GB   v02. PQ: 0 ANSI: 0
[ 4438.678682] sd 4:0:0:0: Attached scsi generic sg2 type 0
[ 4438.679017] sd 4:0:0:1: Attached scsi generic sg3 type 0
[ 4438.682464] sd 4:0:0:0: [sdb] 15462400 512-byte logical blocks: (7.91 GB/7.37 GiB)
[ 4438.683406] sd 4:0:0:0: [sdb] Write Protect is off
[ 4438.683420] sd 4:0:0:0: [sdb] Mode Sense: 04 00 00 00
[ 4438.683427] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[ 4438.688002] sd 4:0:0:1: [sdc] Attached SCSI removable disk
[ 4438.688612] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[ 4438.688632]  sdb:
[ 4438.696312] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[ 4438.696323] sd 4:0:0:0: [sdb] Attached SCSI removable disk
[ 4497.147739] WARNING! power/level is deprecated; use power/control instead
[ 4497.232147] usb 1-5: USB disconnect, address 3
[ 4497.600043] usb 2-5: new full speed USB device using ohci_hcd and address 2
[ 4497.800074] usb 2-5: not running at top speed; connect to a high speed hub
[ 4497.829325] scsi5 : usb-storage 2-5:1.0
[ 4498.836140] scsi 5:0:0:0: Direct-Access     SanDisk  Sansa Fuze 8GB   v02. PQ: 0 ANSI: 0
[ 4498.843125] scsi 5:0:0:1: Direct-Access     SanDisk  Sansa Fuze 8GB   v02. PQ: 0 ANSI: 0
[ 4498.844179] sd 5:0:0:0: Attached scsi generic sg2 type 0
[ 4498.844488] sd 5:0:0:1: Attached scsi generic sg3 type 0
[ 4498.859130] sd 5:0:0:0: [sdb] 15462400 512-byte logical blocks: (7.91 GB/7.37 GiB)
[ 4498.898153] sd 5:0:0:0: [sdb] Write Protect is off
[ 4498.898162] sd 5:0:0:0: [sdb] Mode Sense: 04 00 00 00
[ 4498.898169] sd 5:0:0:0: [sdb] Assuming drive cache: write through
[ 4498.922123] sd 5:0:0:1: [sdc] Attached SCSI removable disk
[ 4499.017100] sd 5:0:0:0: [sdb] Assuming drive cache: write through
[ 4499.017121]  sdb:
[ 4499.136155] sd 5:0:0:0: [sdb] Assuming drive cache: write through
[ 4499.136169] sd 5:0:0:0: [sdb] Attached SCSI removable disk
[ 4595.854609] usb 2-5: USB disconnect, address 2
[ 4964.372040] usb 1-5: new high speed USB device using ehci_hcd and address 4
[ 4964.507796] scsi6 : usb-storage 1-5:1.0
[ 4965.509232] scsi 6:0:0:0: Direct-Access     WD       My Passport 070A 1032 PQ: 0 ANSI: 4
[ 4965.510078] scsi 6:0:0:1: CD-ROM            WD       Virtual CD 070A  1032 PQ: 0 ANSI: 4
[ 4965.510825] scsi 6:0:0:2: Enclosure         WD       SES Device       1032 PQ: 0 ANSI: 4
[ 4965.511868] sd 6:0:0:0: Attached scsi generic sg2 type 0
[ 4965.516341] sd 6:0:0:0: [sdb] 623769600 512-byte logical blocks: (319 GB/297 GiB)
[ 4965.518094] sr1: scsi3-mmc drive: 51x/51x caddy
[ 4965.518397] sr 6:0:0:1: Attached scsi CD-ROM sr1
[ 4965.518560] sr 6:0:0:1: Attached scsi generic sg3 type 5
[ 4965.518813] scsi 6:0:0:2: Attached scsi generic sg4 type 13
[ 4965.522844] sd 6:0:0:0: [sdb] Write Protect is off
[ 4965.522856] sd 6:0:0:0: [sdb] Mode Sense: 23 00 10 00
[ 4965.522863] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[ 4965.525560] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[ 4965.525586]  sdb: sdb1
[ 4965.535182] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[ 4965.535194] sd 6:0:0:0: [sdb] Attached SCSI disk
[ 4965.652137] ses 6:0:0:2: Attached Enclosure device
[ 5108.693642] scsi 6:0:0:1: rejecting I/O to offline device
[ 5110.428149] usb 1-5: USB disconnect, address 4
[ 5110.801035] usb 2-5: new full speed USB device using ohci_hcd and address 3
[ 5111.000075] usb 2-5: not running at top speed; connect to a high speed hub
[ 5111.025213] scsi7 : usb-storage 2-5:1.0
[ 5112.033166] scsi 7:0:0:0: Direct-Access     WD       My Passport 070A 1032 PQ: 0 ANSI: 4
[ 5112.040143] scsi 7:0:0:1: CD-ROM            WD       Virtual CD 070A  1032 PQ: 0 ANSI: 4
[ 5112.047153] scsi 7:0:0:2: Enclosure         WD       SES Device       1032 PQ: 0 ANSI: 4
[ 5112.048277] sd 7:0:0:0: Attached scsi generic sg2 type 0
[ 5112.062129] sr1: scsi3-mmc drive: 51x/51x caddy
[ 5112.062420] sr 7:0:0:1: Attached scsi CD-ROM sr1
[ 5112.062595] sr 7:0:0:1: Attached scsi generic sg3 type 5
[ 5112.062784] ses 7:0:0:2: Attached Enclosure device
[ 5112.062938] ses 7:0:0:2: Attached scsi generic sg4 type 13
[ 5112.072168] sd 7:0:0:0: [sdb] 623769600 512-byte logical blocks: (319 GB/297 GiB)
[ 5112.078132] sd 7:0:0:0: [sdb] Write Protect is off
[ 5112.078144] sd 7:0:0:0: [sdb] Mode Sense: 23 00 10 00
[ 5112.078151] sd 7:0:0:0: [sdb] Assuming drive cache: write through
[ 5112.114103] sd 7:0:0:0: [sdb] Assuming drive cache: write through
[ 5112.114122]  sdb: sdb1
[ 5112.212138] sd 7:0:0:0: [sdb] Assuming drive cache: write through
[ 5112.212152] sd 7:0:0:0: [sdb] Attached SCSI disk
[ 5118.107520] usb 2-5: USB disconnect, address 3
[ 5118.108443] sd 7:0:0:0: [sdb] Unhandled error code
[ 5118.108454] sd 7:0:0:0: [sdb] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK
[ 5118.108463] sd 7:0:0:0: [sdb] CDB: Read(10): 28 00 12 97 23 60 00 00 80 00
[ 5118.108483] end_request: I/O error, dev sdb, sector 311894880
[ 5118.108490] quiet_error: 9 callbacks suppressed
[ 5118.108497] Buffer I/O error on device sdb1, logical block 311892832
[ 5118.108506] Buffer I/O error on device sdb1, logical block 311892833
[ 5118.108512] Buffer I/O error on device sdb1, logical block 311892834
[ 5118.108518] Buffer I/O error on device sdb1, logical block 311892835
[ 5118.108524] Buffer I/O error on device sdb1, logical block 311892836
[ 5118.108531] Buffer I/O error on device sdb1, logical block 311892837
[ 5118.108537] Buffer I/O error on device sdb1, logical block 311892838
[ 5118.108544] Buffer I/O error on device sdb1, logical block 311892839
[ 5118.108554] Buffer I/O error on device sdb1, logical block 311892840
[ 5118.108560] Buffer I/O error on device sdb1, logical block 311892841
[ 5118.108838] sd 7:0:0:0: [sdb] Unhandled error code
[ 5118.108843] sd 7:0:0:0: [sdb] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK
[ 5118.108850] sd 7:0:0:0: [sdb] CDB: Read(10): 28 00 12 97 23 e0 00 00 80 00
[ 5118.108866] end_request: I/O error, dev sdb, sector 311895008
[ 5145.416041] usb 1-5: new high speed USB device using ehci_hcd and address 5
[ 5145.550635] scsi8 : usb-storage 1-5:1.0
[ 5146.549255] scsi 8:0:0:0: Direct-Access     WD       My Passport 070A 1032 PQ: 0 ANSI: 4
[ 5146.550102] scsi 8:0:0:1: CD-ROM            WD       Virtual CD 070A  1032 PQ: 0 ANSI: 4
[ 5146.550850] scsi 8:0:0:2: Enclosure         WD       SES Device       1032 PQ: 0 ANSI: 4
[ 5146.551917] sd 8:0:0:0: Attached scsi generic sg2 type 0
[ 5146.556731] sd 8:0:0:0: [sdb] 623769600 512-byte logical blocks: (319 GB/297 GiB)
[ 5146.558952] sr1: scsi3-mmc drive: 51x/51x caddy
[ 5146.559272] sr 8:0:0:1: Attached scsi CD-ROM sr1
[ 5146.559428] sr 8:0:0:1: Attached scsi generic sg3 type 5
[ 5146.559607] ses 8:0:0:2: Attached Enclosure device
[ 5146.559723] ses 8:0:0:2: Attached scsi generic sg4 type 13
[ 5146.561758] sd 8:0:0:0: [sdb] Write Protect is off
[ 5146.561770] sd 8:0:0:0: [sdb] Mode Sense: 23 00 10 00
[ 5146.561777] sd 8:0:0:0: [sdb] Assuming drive cache: write through
[ 5146.564999] sd 8:0:0:0: [sdb] Assuming drive cache: write through
[ 5146.565069]  sdb: sdb1
[ 5146.577882] sd 8:0:0:0: [sdb] Assuming drive cache: write through
[ 5146.577895] sd 8:0:0:0: [sdb] Attached SCSI disk

```

---

### Post by dcstar on 2010-11-19
> **RustyTrowel said:**
> I just installed Ubuntu 10.10 32 bit on my desktop and I've encountered a curious and somewhat frustrating issue.  It appears that when I plug a flash drive, external hard drive or MP3 player into a USB port my computer turns off.
...........

I had this on a PC once and the physical action of pushing in the USB into a slot on the front caused a mismounted reset switch to activate rebooting the bloody thing!

Once we figured this out we could also reboot the box by gently kicking it in just the right place.....

A little bending and twisting got the switch in a more reliable situation.

---

### Post by RustyTrowel on 2010-11-25
Thanks for the feedback!  

It is possible that the wiring inside may be leading to this shutdown issue.  I'll take a look inside the tower this weekend when I get back home.

---

### Post by no2498 on 2010-11-25
look for dust in all the plug ends

---

### Post by RustyTrowel on 2010-11-28
Well, I blew dust out of plug-ins and out of the case and made sure nothing was loose inside.  This, however, did not solve the problem.

Unfortunately, I'm at the hit it with a rock and see what happens level of technological understanding so I may be missing some key issue because I simply don't know what I'm looking at.

I'm wondering if booting from a live cd would demonstrate whether this was a hardware or software problem? I may try that next weekend when I'm back in town.

---

### Post by no2498 on 2010-11-29
install htop to see what starts running

type htop in a terminal it tells you how to install in

now type htop 

plug something in see what starts up and what it does


hope it helps you

---

### Post by ezsit on 2010-11-29
I had this happen with my current rig and found that if I grounded the USB device before plugging into the USB port it prevented the system from rebooting or shutting down. Could be a static electricity problem like mine.

---

