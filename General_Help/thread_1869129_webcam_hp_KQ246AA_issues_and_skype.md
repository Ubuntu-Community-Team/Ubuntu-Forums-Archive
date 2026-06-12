---
title: "webcam hp KQ246AA issues and skype"
date: 2011-10-25
forum: General Help
---

### Post by linuxcss on 2011-10-25
KQ246AA ... used to work with ubuntu 9.x stuff and so did cheese, sound recorder, and skype.

Right now with  xubuntu 11.10 they don't here.

Does anybody have at least skype working with Hp KQ246AA?

Or what mixer can be added so I can get some feedback that the mic
is really not just under the covers muted?

I have installed sound recorder but when recording nothing gets recorded.

---

### Post by no2498 on 2011-10-25
for the cam
open a terminal type dmesg click enter
after it stops type lsusb click enter

---

### Post by linuxcss on 2011-10-26
dmesg produces:

[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 3.0.0-12-generic-pae (buildd@vernadsky) (gcc version 4.6.1 (Ubuntu/Linaro 4.6.1-9ubuntu3) ) #20-Ubuntu SMP Fri Oct 7 16:37:17 UTC 2011 (Ubuntu 3.0.0-12.20-generic-pae 3.0.4)
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
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009ec00 (usable)
[    0.000000]  BIOS-e820: 000000000009ec00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e4000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 00000000bff80000 (usable)
[    0.000000]  BIOS-e820: 00000000bff80000 - 00000000bff8e000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000bff8e000 - 00000000bffd0000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000bffd0000 - 00000000c0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000ff700000 - 0000000100000000 (reserved)
[    0.000000]  BIOS-e820: 0000000100000000 - 0000000230000000 (usable)
[    0.000000] NX (Execute Disable) protection: active
[    0.000000] DMI present.
[    0.000000] DMI: System manufacturer System Product Name/M3A78-EM, BIOS 2003    10/12/2009
[    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
[    0.000000] e820 remove range: 00000000000a0000 - 0000000000100000 (usable)
[    0.000000] last_pfn = 0x230000 max_arch_pfn = 0x1000000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-EFFFF uncachable
[    0.000000]   F0000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000000 mask FFFF80000000 write-back
[    0.000000]   1 base 000080000000 mask FFFFC0000000 write-back
[    0.000000]   2 disabled
[    0.000000]   3 disabled
[    0.000000]   4 disabled
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] TOM2: 0000000230000000 aka 8960M
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] e820 update range: 00000000c0000000 - 0000000100000000 (usable) ==> (reserved)
[    0.000000] found SMP MP-table at [c00ff780] ff780
[    0.000000] initial memory mapped : 0 - 02000000
[    0.000000] Base memory trampoline at [c009a000] 9a000 size 16384
[    0.000000] init_memory_mapping: 0000000000000000-0000000037bfe000
[    0.000000]  0000000000 - 0000200000 page 4k
[    0.000000]  0000200000 - 0037a00000 page 2M
[    0.000000]  0037a00000 - 0037bfe000 page 4k
[    0.000000] kernel direct mapping tables up to 37bfe000 @ 1ffb000-2000000
[    0.000000] RAMDISK: 365f4000 - 372f2000
[    0.000000] ACPI: RSDP 000fb530 00024 (v02 ACPIAM)
[    0.000000] ACPI: XSDT bff80100 00054 (v01 101209 XSDT1907 20091012 MSFT 00000097)
[    0.000000] ACPI: FACP bff80290 000F4 (v03 101209 FACP1907 20091012 MSFT 00000097)
[    0.000000] ACPI: DSDT bff805d0 0BDB1 (v01  A1044 A1044001 00000001 INTL 20060113)
[    0.000000] ACPI: FACS bff8e000 00040
[    0.000000] ACPI: APIC bff80390 0007C (v01 101209 APIC1907 20091012 MSFT 00000097)
[    0.000000] ACPI: MCFG bff80410 0003C (v01 101209 OEMMCFG  20091012 MSFT 00000097)
[    0.000000] ACPI: OEMB bff8e040 00071 (v01 101209 OEMB1907 20091012 MSFT 00000097)
[    0.000000] ACPI: HPET bff8c390 00038 (v01 101209 OEMHPET  20091012 MSFT 00000097)
[    0.000000] ACPI: SSDT bff8c3d0 0088C (v01 A M I  POWERNOW 00000001 AMD  00000001)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] 8068MB HIGHMEM available.
[    0.000000] 891MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 37bfe000
[    0.000000]   low ram: 0 - 37bfe000
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000010 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x00037bfe
[    0.000000]   HighMem  0x00037bfe -> 0x00230000
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[3] active PFN ranges
[    0.000000]     0: 0x00000010 -> 0x0000009e
[    0.000000]     0: 0x00000100 -> 0x000bff80
[    0.000000]     0: 0x00100000 -> 0x00230000
[    0.000000] On node 0 totalpages: 2031374
[    0.000000] free_area_init_node: node 0, pgdat c17e9f40, node_mem_map f1ff4200
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3950 pages, LIFO batch:0
[    0.000000]   Normal zone: 1752 pages used for memmap
[    0.000000]   Normal zone: 222502 pages, LIFO batch:31
[    0.000000]   HighMem zone: 16137 pages used for memmap
[    0.000000]   HighMem zone: 1787001 pages, LIFO batch:31
[    0.000000] Using APIC driver default
[    0.000000] ACPI: PM-Timer IO Port: 0x808
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x02] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x03] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x05] lapic_id[0x84] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x06] lapic_id[0x85] disabled)
[    0.000000] ACPI: IOAPIC (id[0x04] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 4, version 33, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 low level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x8300 base: 0xfed00000
[    0.000000] SMP: Allowing 6 CPUs, 2 hotplug CPUs
[    0.000000] nr_irqs_gsi: 40
[    0.000000] PM: Registered nosave memory: 000000000009e000 - 000000000009f000
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e4000
[    0.000000] PM: Registered nosave memory: 00000000000e4000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at c0000000 (gap: c0000000:3f700000)
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] setup_percpu: NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:6 nr_node_ids:1
[    0.000000] PERCPU: Embedded 13 pages/cpu @f7800000 s29952 r0 d23296 u262144
[    0.000000] pcpu-alloc: s29952 r0 d23296 u262144 alloc=1*2097152
[    0.000000] pcpu-alloc: [0] 0 1 2 3 4 5 - - 
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 2013453
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.0.0-12-generic-pae root=UUID=668ea148-dae1-4609-bec7-6764c26d275e ro quiet splash vt.handoff=7
[    0.000000] PID hash table entries: 4096 (order: 2, 16384 bytes)
[    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.000000] Initializing CPU#0
[    0.000000] allocated 36699904 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] Initializing HighMem for node 0 (00037bfe:00230000)
[    0.000000] Memory: 7993652k/9175040k available (5494k kernel code, 131844k reserved, 2653k data, 720k init, 7212552k highmem)
[    0.000000] virtual kernel memory layout:
[    0.000000]     fixmap  : 0xfff16000 - 0xfffff000   ( 932 kB)
[    0.000000]     pkmap   : 0xffc00000 - 0xffe00000   (2048 kB)
[    0.000000]     vmalloc : 0xf83fe000 - 0xffbfe000   ( 120 MB)
[    0.000000]     lowmem  : 0xc0000000 - 0xf7bfe000   ( 891 MB)
[    0.000000]       .init : 0xc17f6000 - 0xc18aa000   ( 720 kB)
[    0.000000]       .data : 0xc155d9b0 - 0xc17f5180   (2653 kB)
[    0.000000]       .text : 0xc1000000 - 0xc155d9b0   (5494 kB)
[    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.000000] SLUB: Genslabs=15, HWalign=64, Order=0-3, MinObjects=0, CPUs=6, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000]     RCU dyntick-idle grace-period acceleration is enabled.
[    0.000000] NR_IRQS:2304 nr_irqs:728 16
[    0.000000] CPU 0 irqstacks, hard=f740a000 soft=f740c000
[    0.000000] Extended CMOS year: 2000
[    0.000000] spurious 8259A interrupt: IRQ7.
[    0.000000] vt handoff: transparent VT on vt#7
[    0.000000] Console: colour dummy device 80x25
[    0.000000] console [tty0] enabled
[    0.000000] hpet clockevent registered
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 3015.608 MHz processor.
[    0.004003] Calibrating delay loop (skipped), value calculated using timer frequency.. 6031.21 BogoMIPS (lpj=12062432)
[    0.004008] pid_max: default: 32768 minimum: 301
[    0.004027] Security Framework initialized
[    0.004042] AppArmor: AppArmor initialized
[    0.004043] Yama: becoming mindful.
[    0.004091] Mount-cache hash table entries: 512
[    0.004200] Initializing cgroup subsys cpuacct
[    0.004205] Initializing cgroup subsys memory
[    0.004212] Initializing cgroup subsys devices
[    0.004214] Initializing cgroup subsys freezer
[    0.004216] Initializing cgroup subsys net_cls
[    0.004219] Initializing cgroup subsys blkio
[    0.004225] Initializing cgroup subsys perf_event
[    0.004246] CPU: Physical Processor ID: 0
[    0.004248] CPU: Processor Core ID: 0
[    0.004251] mce: CPU supports 6 MCE banks
[    0.008998] ACPI: Core revision 20110413
[    0.016010] ftrace: allocating 25582 entries in 51 pages
[    0.020063] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.020366] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.062744] CPU0: AMD Phenom(tm) II X4 940 Processor stepping 02
[    0.064003] Performance Events: AMD PMU driver.
[    0.064003] ... version:                0
[    0.064003] ... bit width:              48
[    0.064003] ... generic registers:      4
[    0.064003] ... value mask:             0000ffffffffffff
[    0.064003] ... max period:             00007fffffffffff
[    0.064003] ... fixed-purpose events:   0
[    0.064003] ... event mask:             000000000000000f
[    0.064003] CPU 1 irqstacks, hard=f74d2000 soft=f74d4000
[    0.064003] Booting Node   0, Processors  #1
[    0.064003] smpboot cpu 1: start_ip = 9a000
[    0.008000] Initializing CPU#1
[    0.152060] CPU 2 irqstacks, hard=f74de000 soft=f74e0000
[    0.152062]  #2
[    0.152063] smpboot cpu 2: start_ip = 9a000
[    0.008000] Initializing CPU#2
[    0.244060] CPU 3 irqstacks, hard=f74ea000 soft=f74ec000
[    0.244061]  #3
[    0.244062] smpboot cpu 3: start_ip = 9a000
[    0.008000] Initializing CPU#3
[    0.008000] calibrate_delay_direct() ignoring timer_rate as we had a TSC wrap around start=4276247166 >=post_end=5348910
[    0.336025] Brought up 4 CPUs
[    0.336027] Total of 4 processors activated (24083.07 BogoMIPS).
[    0.338698] devtmpfs: initialized
[    0.338698] PM: Registering ACPI NVS region at bff8e000 (270336 bytes)
[    0.340402] print_constraints: dummy: 
[    0.340433] Time: 18:11:47  Date: 10/24/11
[    0.340461] NET: Registered protocol family 16
[    0.340538] EISA bus registered
[    0.340543] node 0 link 0: io port [1000, ffffff]
[    0.340546] TOM: 00000000d0000000 aka 3328M
[    0.340547] Fam 10h mmconf [e0000000, efffffff]
[    0.340550] node 0 link 0: mmio [a0000, bffff]
[    0.340552] node 0 link 0: mmio [d0000000, efffffff] ==> [d0000000, dfffffff]
[    0.340555] node 0 link 0: mmio [f0000000, fbbfffff]
[    0.340557] node 0 link 0: mmio [fbc00000, fbcfffff]
[    0.340559] node 0 link 0: mmio [fbd00000, ffefffff]
[    0.340561] TOM2: 0000000230000000 aka 8960M
[    0.340563] bus: [00, 07] on node 0 link 0
[    0.340565] bus: 00 index 0 [io  0x0000-0xffff]
[    0.340567] bus: 00 index 1 [mem 0x000a0000-0x000bffff]
[    0.340568] bus: 00 index 2 [mem 0xd0000000-0xdfffffff]
[    0.340570] bus: 00 index 3 [mem 0xf0000000-0xffffffff]
[    0.340571] bus: 00 index 4 [mem 0x230000000-0xfcffffffff]
[    0.340581] Extended Config Space enabled on 1 nodes
[    0.340600] ACPI: bus type pci registered
[    0.340470] Trying to unpack rootfs image as initramfs...
[    0.340643] PCI: MMCONFIG for domain 0000 [bus 00-ff] at [mem 0xe0000000-0xefffffff] (base 0xe0000000)
[    0.340645] PCI: not using MMCONFIG
[    0.341359] PCI : PCI BIOS aera is rw and x. Use pci=nobios if you want it NX.
[    0.341426] PCI: PCI BIOS revision 3.00 entry at 0xf0031, last bus=4
[    0.341428] PCI: Using configuration type 1 for base access
[    0.341429] PCI: Using configuration type 1 for extended access
[    0.341449] mtrr: your CPUs had inconsistent fixed MTRR settings
[    0.341451] mtrr: probably your BIOS does not setup all CPUs.
[    0.341452] mtrr: corrected configuration.
[    0.341987] bio: create slab <bio-0> at 0
[    0.341987] ACPI: EC: Look up EC in DSDT
[    0.344586] ACPI: Executed 4 blocks of module-level executable AML code
[    0.347651] ACPI: Interpreter enabled
[    0.347655] ACPI: (supports S0 S1 S3 S4 S5)
[    0.347672] ACPI: Using IOAPIC for interrupt routing
[    0.347688] PCI: MMCONFIG for domain 0000 [bus 00-ff] at [mem 0xe0000000-0xefffffff] (base 0xe0000000)
[    0.348793] PCI: MMCONFIG at [mem 0xe0000000-0xefffffff] reserved in ACPI motherboard resources
[    0.348795] PCI: Using MMCONFIG for extended config space
[    0.353169] ACPI: No dock devices found.
[    0.353170] HEST: Table not found.
[    0.353173] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
[    0.353235] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-ff])
[    0.353355] pci_root PNP0A03:00: host bridge window [io  0x0000-0x0cf7]
[    0.353357] pci_root PNP0A03:00: host bridge window [io  0x0d00-0xffff]
[    0.353359] pci_root PNP0A03:00: host bridge window [mem 0x000a0000-0x000bffff]
[    0.353361] pci_root PNP0A03:00: host bridge window [mem 0x000d0000-0x000dffff]
[    0.353363] pci_root PNP0A03:00: host bridge window [mem 0xc0000000-0xdfffffff]
[    0.353365] pci_root PNP0A03:00: host bridge window [mem 0xf0000000-0xfed44fff]
[    0.353378] pci 0000:00:00.0: [1022:9600] type 0 class 0x000600
[    0.353417] pci 0000:00:01.0: [1043:9602] type 1 class 0x000604
[    0.353452] pci 0000:00:05.0: [1022:9605] type 1 class 0x000604
[    0.353476] pci 0000:00:05.0: PME# supported from D0 D3hot D3cold
[    0.353479] pci 0000:00:05.0: PME# disabled
[    0.353491] pci 0000:00:06.0: [1022:9606] type 1 class 0x000604
[    0.353515] pci 0000:00:06.0: PME# supported from D0 D3hot D3cold
[    0.353517] pci 0000:00:06.0: PME# disabled
[    0.353550] pci 0000:00:11.0: [1002:4391] type 0 class 0x000106
[    0.353569] pci 0000:00:11.0: reg 10: [io  0xc000-0xc007]
[    0.353579] pci 0000:00:11.0: reg 14: [io  0xb000-0xb003]
[    0.353588] pci 0000:00:11.0: reg 18: [io  0xa000-0xa007]
[    0.353597] pci 0000:00:11.0: reg 1c: [io  0x9000-0x9003]
[    0.353606] pci 0000:00:11.0: reg 20: [io  0x8000-0x800f]
[    0.353616] pci 0000:00:11.0: reg 24: [mem 0xfbbff800-0xfbbffbff]
[    0.353659] pci 0000:00:12.0: [1002:4397] type 0 class 0x000c03
[    0.353672] pci 0000:00:12.0: reg 10: [mem 0xfbbfe000-0xfbbfefff]
[    0.353734] pci 0000:00:12.1: [1002:4398] type 0 class 0x000c03
[    0.353747] pci 0000:00:12.1: reg 10: [mem 0xfbbfd000-0xfbbfdfff]
[    0.353814] pci 0000:00:12.2: [1002:4396] type 0 class 0x000c03
[    0.353833] pci 0000:00:12.2: reg 10: [mem 0xfbbff000-0xfbbff0ff]
[    0.353902] pci 0000:00:12.2: supports D1 D2
[    0.353904] pci 0000:00:12.2: PME# supported from D0 D1 D2 D3hot
[    0.353908] pci 0000:00:12.2: PME# disabled
[    0.353928] pci 0000:00:13.0: [1002:4397] type 0 class 0x000c03
[    0.353941] pci 0000:00:13.0: reg 10: [mem 0xfbbfc000-0xfbbfcfff]
[    0.354002] pci 0000:00:13.1: [1002:4398] type 0 class 0x000c03
[    0.354015] pci 0000:00:13.1: reg 10: [mem 0xfbbfb000-0xfbbfbfff]
[    0.354083] pci 0000:00:13.2: [1002:4396] type 0 class 0x000c03
[    0.354101] pci 0000:00:13.2: reg 10: [mem 0xfbbfa800-0xfbbfa8ff]
[    0.354170] pci 0000:00:13.2: supports D1 D2
[    0.354172] pci 0000:00:13.2: PME# supported from D0 D1 D2 D3hot
[    0.354176] pci 0000:00:13.2: PME# disabled
[    0.354198] pci 0000:00:14.0: [1002:4385] type 0 class 0x000c05
[    0.354291] pci 0000:00:14.1: [1002:439c] type 0 class 0x000101
[    0.354307] pci 0000:00:14.1: reg 10: [io  0x0000-0x0007]
[    0.354316] pci 0000:00:14.1: reg 14: [io  0x0000-0x0003]
[    0.354325] pci 0000:00:14.1: reg 18: [io  0x0000-0x0007]
[    0.354334] pci 0000:00:14.1: reg 1c: [io  0x0000-0x0003]
[    0.354344] pci 0000:00:14.1: reg 20: [io  0xff00-0xff0f]
[    0.354391] pci 0000:00:14.2: [1002:4383] type 0 class 0x000403
[    0.354412] pci 0000:00:14.2: reg 10: [mem 0xfbbf4000-0xfbbf7fff 64bit]
[    0.354469] pci 0000:00:14.2: PME# supported from D0 D3hot D3cold
[    0.354473] pci 0000:00:14.2: PME# disabled
[    0.354485] pci 0000:00:14.3: [1002:439d] type 0 class 0x000601
[    0.354558] pci 0000:00:14.4: [1002:4384] type 1 class 0x000604
[    0.354596] pci 0000:00:14.5: [1002:4399] type 0 class 0x000c03
[    0.354609] pci 0000:00:14.5: reg 10: [mem 0xfbbf9000-0xfbbf9fff]
[    0.354674] pci 0000:00:18.0: [1022:1200] type 0 class 0x000600
[    0.354687] pci 0000:00:18.1: [1022:1201] type 0 class 0x000600
[    0.354698] pci 0000:00:18.2: [1022:1202] type 0 class 0x000600
[    0.354709] pci 0000:00:18.3: [1022:1203] type 0 class 0x000600
[    0.354722] pci 0000:00:18.4: [1022:1204] type 0 class 0x000600
[    0.354762] pci 0000:01:05.0: [1002:9610] type 0 class 0x000300
[    0.354769] pci 0000:01:05.0: reg 10: [mem 0xd0000000-0xdfffffff pref]
[    0.354773] pci 0000:01:05.0: reg 14: [io  0xd000-0xd0ff]
[    0.354778] pci 0000:01:05.0: reg 18: [mem 0xfbdf0000-0xfbdfffff]
[    0.354787] pci 0000:01:05.0: reg 24: [mem 0xfbc00000-0xfbcfffff]
[    0.354798] pci 0000:01:05.0: supports D1 D2
[    0.354807] pci 0000:01:05.1: [1002:960f] type 0 class 0x000403
[    0.354815] pci 0000:01:05.1: reg 10: [mem 0xfbde8000-0xfbdebfff]
[    0.354838] pci 0000:01:05.1: supports D1 D2
[    0.354874] pci 0000:00:01.0: PCI bridge to [bus 01-01]
[    0.354877] pci 0000:00:01.0:   bridge window [io  0xd000-0xdfff]
[    0.354880] pci 0000:00:01.0:   bridge window [mem 0xfbc00000-0xfbdfffff]
[    0.354883] pci 0000:00:01.0:   bridge window [mem 0xd0000000-0xdfffffff 64bit pref]
[    0.354920] pci 0000:02:00.0: [197b:2380] type 0 class 0x000c00
[    0.354938] pci 0000:02:00.0: reg 10: [mem 0xfbeff800-0xfbefffff]
[    0.354951] pci 0000:02:00.0: reg 14: [mem 0xfbeff400-0xfbeff47f]
[    0.354988] pci 0000:02:00.0: reg 20: [mem 0xfbeff000-0xfbeff07f]
[    0.355002] pci 0000:02:00.0: reg 24: [mem 0xfbefec00-0xfbefec7f]
[    0.360040] pci 0000:00:05.0: PCI bridge to [bus 02-02]
[    0.360045] pci 0000:00:05.0:   bridge window [io  0xf000-0x0000] (disabled)
[    0.360048] pci 0000:00:05.0:   bridge window [mem 0xfbe00000-0xfbefffff]
[    0.360052] pci 0000:00:05.0:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    0.360090] pci 0000:03:00.0: [10ec:8168] type 0 class 0x000200
[    0.360103] pci 0000:03:00.0: reg 10: [io  0xe800-0xe8ff]
[    0.360123] pci 0000:03:00.0: reg 18: [mem 0xfbfff000-0xfbffffff 64bit]
[    0.360136] pci 0000:03:00.0: reg 20: [mem 0xfaff0000-0xfaffffff 64bit pref]
[    0.360145] pci 0000:03:00.0: reg 30: [mem 0xfbfc0000-0xfbfdffff pref]
[    0.360175] pci 0000:03:00.0: supports D1 D2
[    0.360177] pci 0000:03:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.360180] pci 0000:03:00.0: PME# disabled
[    0.368040] pci 0000:00:06.0: PCI bridge to [bus 03-03]
[    0.368044] pci 0000:00:06.0:   bridge window [io  0xe000-0xefff]
[    0.368047] pci 0000:00:06.0:   bridge window [mem 0xfbf00000-0xfbffffff]
[    0.368050] pci 0000:00:06.0:   bridge window [mem 0xfaf00000-0xfaffffff 64bit pref]
[    0.368117] pci 0000:00:14.4: PCI bridge to [bus 04-04] (subtractive decode)
[    0.368121] pci 0000:00:14.4:   bridge window [io  0xf000-0x0000] (disabled)
[    0.368125] pci 0000:00:14.4:   bridge window [mem 0xfff00000-0x000fffff] (disabled)
[    0.368134] pci 0000:00:14.4:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    0.368136] pci 0000:00:14.4:   bridge window [io  0x0000-0x0cf7] (subtractive decode)
[    0.368138] pci 0000:00:14.4:   bridge window [io  0x0d00-0xffff] (subtractive decode)
[    0.368140] pci 0000:00:14.4:   bridge window [mem 0x000a0000-0x000bffff] (subtractive decode)
[    0.368142] pci 0000:00:14.4:   bridge window [mem 0x000d0000-0x000dffff] (subtractive decode)
[    0.368144] pci 0000:00:14.4:   bridge window [mem 0xc0000000-0xdfffffff] (subtractive decode)
[    0.368145] pci 0000:00:14.4:   bridge window [mem 0xf0000000-0xfed44fff] (subtractive decode)
[    0.368157] pci_bus 0000:00: on NUMA node 0
[    0.368162] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.368331] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P1._PRT]
[    0.368356] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCE5._PRT]
[    0.368376] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCE6._PRT]
[    0.368411] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0PC._PRT]
[    0.368457]  pci0000:00: Requesting ACPI _OSC control (0x1d)
[    0.368459]  pci0000:00: ACPI _OSC request failed (AE_NOT_FOUND), returned control mask: 0x1d
[    0.368461] ACPI _OSC control for PCIe not granted, disabling ASPM
[    0.371957] ACPI: PCI Interrupt Link [LNKA] (IRQs 4 7 10 *11 12 14 15)
[    0.371988] ACPI: PCI Interrupt Link [LNKB] (IRQs 4 7 *10 11 12 14 15)
[    0.372042] ACPI: PCI Interrupt Link [LNKC] (IRQs 4 7 10 *11 12 14 15)
[    0.372068] ACPI: PCI Interrupt Link [LNKD] (IRQs 4 7 *10 11 12 14 15)
[    0.372093] ACPI: PCI Interrupt Link [LNKE] (IRQs 4 7 10 11 12 14 15) *0, disabled.
[    0.372120] ACPI: PCI Interrupt Link [LNKF] (IRQs 4 7 10 11 12 14 15) *0, disabled.
[    0.372148] ACPI: PCI Interrupt Link [LNKG] (IRQs 4 *10 11 12 14 15)
[    0.372174] ACPI: PCI Interrupt Link [LNKH] (IRQs 4 7 10 11 12 14 15) *0, disabled.
[    0.372249] vgaarb: device added: PCI:0000:01:05.0,decodes=io+mem,owns=io+mem,locks=none
[    0.372252] vgaarb: loaded
[    0.372253] vgaarb: bridge control possible 0000:01:05.0
[    0.372389] SCSI subsystem initialized
[    0.372399] libata version 3.00 loaded.
[    0.372399] usbcore: registered new interface driver usbfs
[    0.372399] usbcore: registered new interface driver hub
[    0.372399] usbcore: registered new device driver usb
[    0.372399] PCI: Using ACPI for IRQ routing
[    0.372399] PCI: pci_cache_line_size set to 64 bytes
[    0.372399] reserve RAM buffer: 000000000009ec00 - 000000000009ffff 
[    0.372399] reserve RAM buffer: 00000000bff80000 - 00000000bfffffff 
[    0.372399] NetLabel: Initializing
[    0.372399] NetLabel:  domain hash size = 128
[    0.372399] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.372399] NetLabel:  unlabeled traffic allowed by default
[    0.372399] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0
[    0.372399] hpet0: 4 comparators, 32-bit 14.318180 MHz counter
[    0.374257] Switching to clocksource hpet
[    0.374290] Switched to NOHz mode on CPU #0
[    0.374266] Switched to NOHz mode on CPU #3
[    0.374646] Switched to NOHz mode on CPU #1
[    0.374287] Switched to NOHz mode on CPU #2
[    0.376606] AppArmor: AppArmor Filesystem Enabled
[    0.376621] pnp: PnP ACPI init
[    0.376630] ACPI: bus type pnp registered
[    0.376709] pnp 00:00: [bus 00-ff]
[    0.376711] pnp 00:00: [io  0x0cf8-0x0cff]
[    0.376713] pnp 00:00: [io  0x0000-0x0cf7 window]
[    0.376715] pnp 00:00: [io  0x0d00-0xffff window]
[    0.376717] pnp 00:00: [mem 0x000a0000-0x000bffff window]
[    0.376718] pnp 00:00: [mem 0x000d0000-0x000dffff window]
[    0.376720] pnp 00:00: [mem 0xc0000000-0xdfffffff window]
[    0.376722] pnp 00:00: [mem 0xf0000000-0xfed44fff window]
[    0.376753] pnp 00:00: Plug and Play ACPI device, IDs PNP0a03 (active)
[    0.376820] pnp 00:01: [mem 0x00000000-0xffffffffffffffff disabled]
[    0.376822] pnp 00:01: [mem 0xc0000000-0xcfffffff]
[    0.376855] system 00:01: [mem 0xc0000000-0xcfffffff] has been reserved
[    0.376858] system 00:01: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.376885] pnp 00:02: [dma 4]
[    0.376887] pnp 00:02: [io  0x0000-0x000f]
[    0.376889] pnp 00:02: [io  0x0081-0x0083]
[    0.376890] pnp 00:02: [io  0x0087]
[    0.376891] pnp 00:02: [io  0x0089-0x008b]
[    0.376893] pnp 00:02: [io  0x008f]
[    0.376894] pnp 00:02: [io  0x00c0-0x00df]
[    0.376912] pnp 00:02: Plug and Play ACPI device, IDs PNP0200 (active)
[    0.376918] pnp 00:03: [io  0x0070-0x0071]
[    0.376927] pnp 00:03: [irq 8]
[    0.376944] pnp 00:03: Plug and Play ACPI device, IDs PNP0b00 (active)
[    0.376949] pnp 00:04: [io  0x0061]
[    0.376967] pnp 00:04: Plug and Play ACPI device, IDs PNP0800 (active)
[    0.376972] pnp 00:05: [io  0x00f0-0x00ff]
[    0.376976] pnp 00:05: [irq 13]
[    0.376996] pnp 00:05: Plug and Play ACPI device, IDs PNP0c04 (active)
[    0.377381] pnp 00:06: [io  0x03f0-0x03f5]
[    0.377383] pnp 00:06: [io  0x03f7]
[    0.377386] pnp 00:06: [irq 6]
[    0.377388] pnp 00:06: [dma 2]
[    0.377426] pnp 00:06: Plug and Play ACPI device, IDs PNP0700 (active)
[    0.377921] pnp 00:07: [io  0x0378-0x037f]
[    0.377924] pnp 00:07: [irq 7]
[    0.377926] pnp 00:07: [dma 0 disabled]
[    0.378100] pnp 00:07: Plug and Play ACPI device, IDs PNP0400 (active)
[    0.378123] pnp 00:08: [mem 0xfed00000-0xfed003ff]
[    0.378144] pnp 00:08: Plug and Play ACPI device, IDs PNP0103 (active)
[    0.378172] pnp 00:09: [io  0x0060]
[    0.378174] pnp 00:09: [io  0x0064]
[    0.378177] pnp 00:09: [irq 1]
[    0.378202] pnp 00:09: Plug and Play ACPI device, IDs PNP0303 PNP030b (active)
[    0.378548] pnp 00:0a: [io  0x03f8-0x03ff]
[    0.378552] pnp 00:0a: [irq 4]
[    0.378553] pnp 00:0a: [dma 0 disabled]
[    0.378615] pnp 00:0a: Plug and Play ACPI device, IDs PNP0501 (active)
[    0.378666] pnp 00:0b: [mem 0xfec00000-0xfec00fff]
[    0.378668] pnp 00:0b: [mem 0xfee00000-0xfee00fff]
[    0.378702] system 00:0b: [mem 0xfec00000-0xfec00fff] could not be reserved
[    0.378704] system 00:0b: [mem 0xfee00000-0xfee00fff] has been reserved
[    0.378706] system 00:0b: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.378760] pnp 00:0c: [io  0x0010-0x001f]
[    0.378762] pnp 00:0c: [io  0x0022-0x003f]
[    0.378763] pnp 00:0c: [io  0x0062-0x0063]
[    0.378765] pnp 00:0c: [io  0x0065-0x006f]
[    0.378766] pnp 00:0c: [io  0x0072-0x007f]
[    0.378767] pnp 00:0c: [io  0x0080]
[    0.378769] pnp 00:0c: [io  0x0084-0x0086]
[    0.378770] pnp 00:0c: [io  0x0088]
[    0.378772] pnp 00:0c: [io  0x008c-0x008e]
[    0.378773] pnp 00:0c: [io  0x0090-0x009f]
[    0.378774] pnp 00:0c: [io  0x00a2-0x00bf]
[    0.378776] pnp 00:0c: [io  0x00b1]
[    0.378777] pnp 00:0c: [io  0x00e0-0x00ef]
[    0.378778] pnp 00:0c: [io  0x04d0-0x04d1]
[    0.378780] pnp 00:0c: [io  0x040b]
[    0.378781] pnp 00:0c: [io  0x04d6]
[    0.378782] pnp 00:0c: [io  0x0c00-0x0c01]
[    0.378784] pnp 00:0c: [io  0x0c14]
[    0.378785] pnp 00:0c: [io  0x0c50-0x0c51]
[    0.378786] pnp 00:0c: [io  0x0c52]
[    0.378788] pnp 00:0c: [io  0x0c6c]
[    0.378789] pnp 00:0c: [io  0x0c6f]
[    0.378790] pnp 00:0c: [io  0x0cd0-0x0cd1]
[    0.378792] pnp 00:0c: [io  0x0cd2-0x0cd3]
[    0.378793] pnp 00:0c: [io  0x0cd4-0x0cd5]
[    0.378794] pnp 00:0c: [io  0x0cd6-0x0cd7]
[    0.378796] pnp 00:0c: [io  0x0cd8-0x0cdf]
[    0.378797] pnp 00:0c: [io  0x0b00-0x0b3f]
[    0.378798] pnp 00:0c: [io  0x0800-0x089f]
[    0.378800] pnp 00:0c: [io  0x0b20-0x0b2f]
[    0.378801] pnp 00:0c: [io  0x0000-0xffffffffffffffff disabled]
[    0.378803] pnp 00:0c: [io  0x0900-0x090f]
[    0.378804] pnp 00:0c: [io  0x0910-0x091f]
[    0.378806] pnp 00:0c: [io  0xfe00-0xfefe]
[    0.378807] pnp 00:0c: [mem 0xffb80000-0xffbfffff]
[    0.378809] pnp 00:0c: [mem 0xfec10000-0xfec1001f]
[    0.378810] pnp 00:0c: [mem 0xfed40000-0xfed44fff]
[    0.378868] system 00:0c: [io  0x04d0-0x04d1] has been reserved
[    0.378870] system 00:0c: [io  0x040b] has been reserved
[    0.378872] system 00:0c: [io  0x04d6] has been reserved
[    0.378874] system 00:0c: [io  0x0c00-0x0c01] has been reserved
[    0.378876] system 00:0c: [io  0x0c14] has been reserved
[    0.378877] system 00:0c: [io  0x0c50-0x0c51] has been reserved
[    0.378879] system 00:0c: [io  0x0c52] has been reserved
[    0.378881] system 00:0c: [io  0x0c6c] has been reserved
[    0.378883] system 00:0c: [io  0x0c6f] has been reserved
[    0.378885] system 00:0c: [io  0x0cd0-0x0cd1] has been reserved
[    0.378888] system 00:0c: [io  0x0cd2-0x0cd3] has been reserved
[    0.378890] system 00:0c: [io  0x0cd4-0x0cd5] has been reserved
[    0.378892] system 00:0c: [io  0x0cd6-0x0cd7] has been reserved
[    0.378894] system 00:0c: [io  0x0cd8-0x0cdf] has been reserved
[    0.378896] system 00:0c: [io  0x0b00-0x0b3f] has been reserved
[    0.378898] system 00:0c: [io  0x0800-0x089f] has been reserved
[    0.378900] system 00:0c: [io  0x0b20-0x0b2f] has been reserved
[    0.378902] system 00:0c: [io  0x0900-0x090f] has been reserved
[    0.378904] system 00:0c: [io  0x0910-0x091f] has been reserved
[    0.378906] system 00:0c: [io  0xfe00-0xfefe] has been reserved
[    0.378908] system 00:0c: [mem 0xffb80000-0xffbfffff] has been reserved
[    0.378910] system 00:0c: [mem 0xfec10000-0xfec1001f] has been reserved
[    0.378912] system 00:0c: [mem 0xfed40000-0xfed44fff] has been reserved
[    0.378914] system 00:0c: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.379017] pnp 00:0d: [io  0x0000-0xffffffffffffffff disabled]
[    0.379019] pnp 00:0d: [io  0x0230-0x023f]
[    0.379020] pnp 00:0d: [io  0x0290-0x029f]
[    0.379021] pnp 00:0d: [io  0x0300-0x030f]
[    0.379023] pnp 00:0d: [io  0x0a30-0x0a3f]
[    0.379057] system 00:0d: [io  0x0230-0x023f] has been reserved
[    0.379059] system 00:0d: [io  0x0290-0x029f] has been reserved
[    0.379061] system 00:0d: [io  0x0300-0x030f] has been reserved
[    0.379062] system 00:0d: [io  0x0a30-0x0a3f] has been reserved
[    0.379065] system 00:0d: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.379094] pnp 00:0e: [mem 0xe0000000-0xefffffff]
[    0.379127] system 00:0e: [mem 0xe0000000-0xefffffff] has been reserved
[    0.379129] system 00:0e: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.379211] pnp 00:0f: [mem 0x00000000-0x0009ffff]
[    0.379212] pnp 00:0f: [mem 0x000c0000-0x000cffff]
[    0.379214] pnp 00:0f: [mem 0x000e0000-0x000fffff]
[    0.379216] pnp 00:0f: [mem 0x00100000-0xbfffffff]
[    0.379217] pnp 00:0f: [mem 0xfed45000-0xffffffff]
[    0.379254] system 00:0f: [mem 0x00000000-0x0009ffff] could not be reserved
[    0.379256] system 00:0f: [mem 0x000c0000-0x000cffff] could not be reserved
[    0.379259] system 00:0f: [mem 0x000e0000-0x000fffff] could not be reserved
[    0.379261] system 00:0f: [mem 0x00100000-0xbfffffff] could not be reserved
[    0.379263] system 00:0f: [mem 0xfed45000-0xffffffff] could not be reserved
[    0.379265] system 00:0f: Plug and Play ACPI device, IDs PNP0c01 (active)
[    0.379342] pnp: PnP ACPI: found 16 devices
[    0.379343] ACPI: ACPI bus type pnp unregistered
[    0.379345] PnPBIOS: Disabled by ACPI PNP
[    0.415007] PCI: max bus depth: 1 pci_try_num: 2
[    0.415026] pci 0000:00:01.0: PCI bridge to [bus 01-01]
[    0.415028] pci 0000:00:01.0:   bridge window [io  0xd000-0xdfff]
[    0.415031] pci 0000:00:01.0:   bridge window [mem 0xfbc00000-0xfbdfffff]
[    0.415033] pci 0000:00:01.0:   bridge window [mem 0xd0000000-0xdfffffff 64bit pref]
[    0.415037] pci 0000:00:05.0: PCI bridge to [bus 02-02]
[    0.415038] pci 0000:00:05.0:   bridge window [io  disabled]
[    0.415041] pci 0000:00:05.0:   bridge window [mem 0xfbe00000-0xfbefffff]
[    0.415043] pci 0000:00:05.0:   bridge window [mem pref disabled]
[    0.415046] pci 0000:00:06.0: PCI bridge to [bus 03-03]
[    0.415048] pci 0000:00:06.0:   bridge window [io  0xe000-0xefff]
[    0.415051] pci 0000:00:06.0:   bridge window [mem 0xfbf00000-0xfbffffff]
[    0.415053] pci 0000:00:06.0:   bridge window [mem 0xfaf00000-0xfaffffff 64bit pref]
[    0.415056] pci 0000:00:14.4: PCI bridge to [bus 04-04]
[    0.415058] pci 0000:00:14.4:   bridge window [io  disabled]
[    0.415062] pci 0000:00:14.4:   bridge window [mem disabled]
[    0.415066] pci 0000:00:14.4:   bridge window [mem pref disabled]
[    0.415085] pci 0000:00:05.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    0.415087] pci 0000:00:05.0: setting latency timer to 64
[    0.415094] pci 0000:00:06.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    0.415096] pci 0000:00:06.0: setting latency timer to 64
[    0.415103] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
[    0.415105] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff]
[    0.415107] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
[    0.415108] pci_bus 0000:00: resource 7 [mem 0x000d0000-0x000dffff]
[    0.415110] pci_bus 0000:00: resource 8 [mem 0xc0000000-0xdfffffff]
[    0.415112] pci_bus 0000:00: resource 9 [mem 0xf0000000-0xfed44fff]
[    0.415114] pci_bus 0000:01: resource 0 [io  0xd000-0xdfff]
[    0.415116] pci_bus 0000:01: resource 1 [mem 0xfbc00000-0xfbdfffff]
[    0.415117] pci_bus 0000:01: resource 2 [mem 0xd0000000-0xdfffffff 64bit pref]
[    0.415120] pci_bus 0000:02: resource 1 [mem 0xfbe00000-0xfbefffff]
[    0.415121] pci_bus 0000:03: resource 0 [io  0xe000-0xefff]
[    0.415123] pci_bus 0000:03: resource 1 [mem 0xfbf00000-0xfbffffff]
[    0.415125] pci_bus 0000:03: resource 2 [mem 0xfaf00000-0xfaffffff 64bit pref]
[    0.415127] pci_bus 0000:04: resource 4 [io  0x0000-0x0cf7]
[    0.415129] pci_bus 0000:04: resource 5 [io  0x0d00-0xffff]
[    0.415130] pci_bus 0000:04: resource 6 [mem 0x000a0000-0x000bffff]
[    0.415132] pci_bus 0000:04: resource 7 [mem 0x000d0000-0x000dffff]
[    0.415134] pci_bus 0000:04: resource 8 [mem 0xc0000000-0xdfffffff]
[    0.415135] pci_bus 0000:04: resource 9 [mem 0xf0000000-0xfed44fff]
[    0.415169] NET: Registered protocol family 2
[    0.415222] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.415388] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.415800] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.416040] TCP: Hash tables configured (established 131072 bind 65536)
[    0.416042] TCP reno registered
[    0.416044] UDP hash table entries: 512 (order: 2, 16384 bytes)
[    0.416052] UDP-Lite hash table entries: 512 (order: 2, 16384 bytes)
[    0.416122] NET: Registered protocol family 1
[    0.416129] pci 0000:00:01.0: MSI quirk detected; subordinate MSI disabled
[    0.580050] pci 0000:01:05.0: Boot video device
[    0.580060] PCI: CLS 64 bytes, default 64
[    0.580423] audit: initializing netlink socket (disabled)
[    0.580431] type=2000 audit(1319479906.576:1): initialized
[    0.609345] highmem bounce pool size: 64 pages
[    0.609350] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    0.635957] VFS: Disk quotas dquot_6.5.2
[    0.636030] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.636565] fuse init (API version 7.16)
[    0.636626] msgmni has been set to 1525
[    0.637112] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.637150] io scheduler noop registered
[    0.637152] io scheduler deadline registered
[    0.637162] io scheduler cfq registered (default)
[    0.637256] pcieport 0000:00:05.0: setting latency timer to 64
[    0.637283] pcieport 0000:00:05.0: irq 40 for MSI/MSI-X
[    0.637320] pcieport 0000:00:06.0: setting latency timer to 64
[    0.637340] pcieport 0000:00:06.0: irq 41 for MSI/MSI-X
[    0.637392] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.637409] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.637503] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0
[    0.637507] ACPI: Power Button [PWRB]
[    0.637536] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
[    0.637538] ACPI: Power Button [PWRF]
[    0.637561] ACPI: acpi_idle registered with cpuidle
[    0.640316] ERST: Table is not found!
[    0.640377] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    0.640405] isapnp: Scanning for PnP cards...
[    0.660891] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.682425] Freeing initrd memory: 13304k freed
[    0.997379] isapnp: No Plug & Play device found
[    1.072666] 00:0a: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    1.072958] Linux agpgart interface v0.103
[    1.073930] brd: module loaded
[    1.074319] loop: module loaded
[    1.074486] pata_acpi 0000:00:14.1: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.074514] pata_acpi 0000:00:14.1: setting latency timer to 64
[    1.074727] Fixed MDIO Bus: probed
[    1.074743] PPP generic driver version 2.4.2
[    1.074768] tun: Universal TUN/TAP device driver, 1.6
[    1.074770] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    1.074823] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    1.074836] ehci_hcd 0000:00:12.2: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    1.074847] ehci_hcd 0000:00:12.2: EHCI Host Controller
[    1.074869] ehci_hcd 0000:00:12.2: new USB bus registered, assigned bus number 1
[    1.074878] ehci_hcd 0000:00:12.2: applying AMD SB700/SB800/Hudson-2/3 EHCI dummy qh workaround
[    1.074892] QUIRK: Enable AMD PLL fix
[    1.074894] ehci_hcd 0000:00:12.2: applying AMD SB600/SB700 USB freeze workaround
[    1.074907] ehci_hcd 0000:00:12.2: debug port 1
[    1.074927] ehci_hcd 0000:00:12.2: irq 17, io mem 0xfbbff000
[    1.084035] ehci_hcd 0000:00:12.2: USB 2.0 started, EHCI 1.00
[    1.084135] hub 1-0:1.0: USB hub found
[    1.084138] hub 1-0:1.0: 6 ports detected
[    1.084203] ehci_hcd 0000:00:13.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    1.084214] ehci_hcd 0000:00:13.2: EHCI Host Controller
[    1.084237] ehci_hcd 0000:00:13.2: new USB bus registered, assigned bus number 2
[    1.084243] ehci_hcd 0000:00:13.2: applying AMD SB700/SB800/Hudson-2/3 EHCI dummy qh workaround
[    1.084255] ehci_hcd 0000:00:13.2: applying AMD SB600/SB700 USB freeze workaround
[    1.084267] ehci_hcd 0000:00:13.2: debug port 1
[    1.084287] ehci_hcd 0000:00:13.2: irq 19, io mem 0xfbbfa800
[    1.096034] ehci_hcd 0000:00:13.2: USB 2.0 started, EHCI 1.00
[    1.096122] hub 2-0:1.0: USB hub found
[    1.096125] hub 2-0:1.0: 6 ports detected
[    1.096182] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    1.096203] ohci_hcd 0000:00:12.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.096214] ohci_hcd 0000:00:12.0: OHCI Host Controller
[    1.096241] ohci_hcd 0000:00:12.0: new USB bus registered, assigned bus number 3
[    1.096263] ohci_hcd 0000:00:12.0: irq 16, io mem 0xfbbfe000
[    1.156104] hub 3-0:1.0: USB hub found
[    1.156114] hub 3-0:1.0: 3 ports detected
[    1.156162] ohci_hcd 0000:00:12.1: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.156173] ohci_hcd 0000:00:12.1: OHCI Host Controller
[    1.156200] ohci_hcd 0000:00:12.1: new USB bus registered, assigned bus number 4
[    1.156215] ohci_hcd 0000:00:12.1: irq 16, io mem 0xfbbfd000
[    1.216101] hub 4-0:1.0: USB hub found
[    1.216110] hub 4-0:1.0: 3 ports detected
[    1.216160] ohci_hcd 0000:00:13.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    1.216172] ohci_hcd 0000:00:13.0: OHCI Host Controller
[    1.216195] ohci_hcd 0000:00:13.0: new USB bus registered, assigned bus number 5
[    1.216219] ohci_hcd 0000:00:13.0: irq 18, io mem 0xfbbfc000
[    1.276102] hub 5-0:1.0: USB hub found
[    1.276112] hub 5-0:1.0: 3 ports detected
[    1.276158] ohci_hcd 0000:00:13.1: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    1.276168] ohci_hcd 0000:00:13.1: OHCI Host Controller
[    1.276191] ohci_hcd 0000:00:13.1: new USB bus registered, assigned bus number 6
[    1.276206] ohci_hcd 0000:00:13.1: irq 18, io mem 0xfbbfb000
[    1.336096] hub 6-0:1.0: USB hub found
[    1.336105] hub 6-0:1.0: 3 ports detected
[    1.336156] ohci_hcd 0000:00:14.5: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    1.336167] ohci_hcd 0000:00:14.5: OHCI Host Controller
[    1.336188] ohci_hcd 0000:00:14.5: new USB bus registered, assigned bus number 7
[    1.336203] ohci_hcd 0000:00:14.5: irq 18, io mem 0xfbbf9000
[    1.396135] hub 7-0:1.0: USB hub found
[    1.396144] hub 7-0:1.0: 2 ports detected
[    1.396190] uhci_hcd: USB Universal Host Controller Interface driver
[    1.396240] i8042: PNP: PS/2 Controller [PNP0303:PS2K] at 0x60,0x64 irq 1
[    1.396241] i8042: PNP: PS/2 appears to have AUX port disabled, if this is incorrect please boot with i8042.nopnp
[    1.396373] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.396437] mousedev: PS/2 mouse device common for all mice
[    1.396520] rtc_cmos 00:03: RTC can wake from S4
[    1.396596] rtc_cmos 00:03: rtc core: registered rtc_cmos as rtc0
[    1.396619] rtc0: alarms up to one month, y3k, 114 bytes nvram, hpet irqs
[    1.396671] device-mapper: uevent: version 1.0.3
[    1.396723] device-mapper: ioctl: 4.20.0-ioctl (2011-02-02) initialised: [email]dm-devel@redhat.com[/email]
[    1.396742] EISA: Probing bus 0 at eisa.0
[    1.396744] EISA: Cannot allocate resource for mainboard
[    1.396746] Cannot allocate resource for EISA slot 1
[    1.396747] Cannot allocate resource for EISA slot 2
[    1.396748] Cannot allocate resource for EISA slot 3
[    1.396749] Cannot allocate resource for EISA slot 4
[    1.396751] Cannot allocate resource for EISA slot 5
[    1.396752] Cannot allocate resource for EISA slot 6
[    1.396753] Cannot allocate resource for EISA slot 7
[    1.396754] Cannot allocate resource for EISA slot 8
[    1.396756] EISA: Detected 0 cards.
[    1.396766] cpufreq-nforce2: No nForce2 chipset.
[    1.396769] cpuidle: using governor ladder
[    1.396770] cpuidle: using governor menu
[    1.396772] EFI Variables Facility v0.08 2004-May-17
[    1.396954] TCP cubic registered
[    1.397048] NET: Registered protocol family 10
[    1.397435] NET: Registered protocol family 17
[    1.397444] Registering the dns_resolver key type
[    1.397457] Using IPI No-Shortcut mode
[    1.397505] PM: Hibernation image not present or could not be loaded.
[    1.397513] registered taskstats version 1
[    1.415390]   Magic number: 15:354:191
[    1.415441] acpi device:1d: hash matches
[    1.415494] rtc_cmos 00:03: setting system clock to 2011-10-24 18:11:48 UTC (1319479908)
[    1.415510] powernow-k8: Found 1 AMD Phenom(tm) II X4 940 Processor (4 cpu cores) (version 2.20.00)
[    1.415541] powernow-k8:    0 : pstate 0 (3000 MHz)
[    1.415543] powernow-k8:    1 : pstate 1 (2300 MHz)
[    1.415544] powernow-k8:    2 : pstate 2 (1800 MHz)
[    1.415546] powernow-k8:    3 : pstate 3 (800 MHz)
[    1.416127] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.416129] EDD information not available.
[    1.416281] Freeing unused kernel memory: 720k freed
[    1.416491] Write protecting the kernel text: 5496k
[    1.416538] Write protecting the kernel read-only data: 2232k
[    1.416539] NX-protecting the kernel data: 4744k
[    1.424600] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input2
[    1.428543] udevd[87]: starting version 173
[    1.440897] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    1.440920] r8169 0000:03:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    1.440953] r8169 0000:03:00.0: setting latency timer to 64
[    1.440997] r8169 0000:03:00.0: irq 42 for MSI/MSI-X
[    1.441347] r8169 0000:03:00.0: eth0: RTL8168c/8111c at 0xf8422000, 00:24:8c:fd:04:f3, XID 1c4000c0 IRQ 42
[    1.448285] scsi0 : pata_atiixp
[    1.450742] firewire_ohci 0000:02:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    1.450750] firewire_ohci 0000:02:00.0: setting latency timer to 64
[    1.450918] scsi1 : pata_atiixp
[    1.451395] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xff00 irq 14
[    1.451397] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xff08 irq 15
[    1.452037] usb 1-2: new high speed USB device number 3 using ehci_hcd
[    1.457891] ahci 0000:00:11.0: version 3.0
[    1.457922] ahci 0000:00:11.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[    1.458072] ahci 0000:00:11.0: AHCI 0001.0100 32 slots 6 ports 3 Gbps 0x3f impl SATA mode
[    1.458075] ahci 0000:00:11.0: flags: 64bit ncq sntf ilck pm led clo pmp pio slum part ccc 
[    1.461371] scsi2 : ahci
[    1.461577] scsi3 : ahci
[    1.461722] scsi4 : ahci
[    1.461791] scsi5 : ahci
[    1.462613] scsi6 : ahci
[    1.463612] scsi7 : ahci
[    1.463666] ata3: SATA max UDMA/133 abar m1024@0xfbbff800 port 0xfbbff900 irq 22
[    1.463670] ata4: SATA max UDMA/133 abar m1024@0xfbbff800 port 0xfbbff980 irq 22
[    1.463673] ata5: SATA max UDMA/133 abar m1024@0xfbbff800 port 0xfbbffa00 irq 22
[    1.463676] ata6: SATA max UDMA/133 abar m1024@0xfbbff800 port 0xfbbffa80 irq 22
[    1.463679] ata7: SATA max UDMA/133 abar m1024@0xfbbff800 port 0xfbbffb00 irq 22
[    1.463681] ata8: SATA max UDMA/133 abar m1024@0xfbbff800 port 0xfbbffb80 irq 22
[    1.466779] Floppy drive(s): fd0 is 1.44M
[    1.483858] FDC 0 is a post-1991 82077
[    1.512112] firewire_ohci: Added fw-ohci device 0000:02:00.0, OHCI v1.10, 4 IR + 0 IT contexts, quirks 0x10
[    1.580033] Refined TSC clocksource calibration: 3016.216 MHz.
[    1.580038] Switching to clocksource tsc
[    1.632468] ata1.00: ATAPI: ATAPI   DVD A  DH20A3P, XP5T, max UDMA/66
[    1.664402] ata1.00: configured for UDMA/66
[    1.666585] scsi 0:0:0:0: CD-ROM            ATAPI    DVD A  DH20A3P   XP5T PQ: 0 ANSI: 5
[    1.669683] sr0: scsi3-mmc drive: 48x/12x writer dvd-ram cd/rw xa/form2 cdda tray
[    1.669686] cdrom: Uniform CD-ROM driver Revision: 3.20
[    1.669775] sr 0:0:0:0: Attached scsi CD-ROM sr0
[    1.669818] sr 0:0:0:0: Attached scsi generic sg0 type 5
[    1.780030] ata4: SATA link down (SStatus 0 SControl 300)
[    1.780086] ata6: SATA link down (SStatus 0 SControl 300)
[    1.788031] ata8: SATA link down (SStatus 0 SControl 300)
[    1.848020] usb 3-1: new low speed USB device number 2 using ohci_hcd
[    1.952017] ata3: softreset failed (device not ready)
[    1.952021] ata3: applying SB600 PMP SRST workaround and retrying
[    1.956013] ata7: softreset failed (device not ready)
[    1.956017] ata7: applying SB600 PMP SRST workaround and retrying
[    1.956033] ata5: softreset failed (device not ready)
[    1.956037] ata5: applying SB600 PMP SRST workaround and retrying
[    2.012061] firewire_core: created device fw0: GUID 001e8c0001e5bcc5, S400
[    2.124029] ata3: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    2.125547] ata3.00: ATA-8: WDC WD5000AAKS-00UU3A0, 01.03B01, max UDMA/133
[    2.125550] ata3.00: 976773168 sectors, multi 16: LBA48 NCQ (depth 31/32), AA
[    2.126639] ata3.00: configured for UDMA/133
[    2.126744] scsi 2:0:0:0: Direct-Access     ATA      WDC WD5000AAKS-0 01.0 PQ: 0 ANSI: 5
[    2.126856] sd 2:0:0:0: Attached scsi generic sg1 type 0
[    2.126865] sd 2:0:0:0: [sda] 976773168 512-byte logical blocks: (500 GB/465 GiB)
[    2.126967] sd 2:0:0:0: [sda] Write Protect is off
[    2.126969] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    2.126994] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.128032] ata5: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    2.128054] ata7: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    2.128072] usb 2-4: new high speed USB device number 2 using ehci_hcd
[    2.128516] ata7.00: ATAPI: TSSTcorp CDDVDW SH-S243N, SB00, max UDMA/100
[    2.129171] ata7.00: configured for UDMA/100
[    2.162136] ata5.00: ATA-7: ST3120811AS, 3.AAE, max UDMA/133
[    2.162139] ata5.00: 234441648 sectors, multi 16: LBA48 NCQ (depth 31/32)
[    2.175584]  sda: sda1 sda2 < sda5 sda6 sda7 >
[    2.175893] sd 2:0:0:0: [sda] Attached SCSI disk
[    2.220294] ata5.00: configured for UDMA/133
[    2.220394] scsi 4:0:0:0: Direct-Access     ATA      ST3120811AS      3.AA PQ: 0 ANSI: 5
[    2.220495] sd 4:0:0:0: [sdb] 234441648 512-byte logical blocks: (120 GB/111 GiB)
[    2.220502] sd 4:0:0:0: Attached scsi generic sg2 type 0
[    2.220560] sd 4:0:0:0: [sdb] Write Protect is off
[    2.220563] sd 4:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[    2.220587] sd 4:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.221009] scsi 6:0:0:0: CD-ROM            TSSTcorp CDDVDW SH-S243N  SB00 PQ: 0 ANSI: 5
[    2.223938] sr1: scsi3-mmc drive: 40x/40x writer dvd-ram cd/rw xa/form2 cdda tray
[    2.224039] sr 6:0:0:0: Attached scsi CD-ROM sr1
[    2.224086] sr 6:0:0:0: Attached scsi generic sg3 type 5
[    2.268321] usbcore: registered new interface driver uas
[    2.268558]  sdb: sdb1 < sdb5 > sdb2
[    2.268789] sd 4:0:0:0: [sdb] Attached SCSI disk
[    2.270363] Initializing USB Mass Storage driver...
[    2.270456] scsi8 : usb-storage 2-4:1.0
[    2.270573] usbcore: registered new interface driver usb-storage
[    2.270575] USB Mass Storage support registered.
[    2.274446] input: Logitech USB Trackball as /devices/pci0000:00/0000:00:12.0/usb3/3-1/3-1:1.0/input/input3
[    2.274524] generic-usb 0003:046D:C408.0001: input,hidraw0: USB HID v1.10 Mouse [Logitech USB Trackball] on usb-0000:00:12.0-1/input0
[    2.274537] usbcore: registered new interface driver usbhid
[    2.274539] usbhid: USB HID core driver
[    2.550565] EXT4-fs (sda6): mounted filesystem with ordered data mode. Opts: (null)
[    3.268622] scsi 8:0:0:0: Direct-Access     Generic  USB CF Reader    1.01 PQ: 0 ANSI: 0
[    3.269111] scsi 8:0:0:1: Direct-Access     Multiple Flash Reader     1.05 PQ: 0 ANSI: 0
[    3.624168] sd 8:0:0:0: Attached scsi generic sg4 type 0
[    3.624257] sd 8:0:0:1: Attached scsi generic sg5 type 0
[    3.627525] sd 8:0:0:0: [sdc] Attached SCSI removable disk
[    3.628140] sd 8:0:0:1: [sdd] Attached SCSI removable disk
[    8.762739] udevd[381]: starting version 173
[    8.807910] lp: driver loaded but no devices found
[    8.809325] Adding 4401772k swap on /dev/sda5.  Priority:-1 extents:1 across:4401772k 
[    8.810738] piix4_smbus 0000:00:14.0: SMBus Host Controller at 0xb00, revision 0
[    8.811229] SP5100 TCO timer: SP5100 TCO WatchDog Timer Driver v0.01
[    8.811318] SP5100 TCO timer: mmio address 0xfec000f0 already in use
[    8.815519] k10temp 0000:00:18.3: unreliable CPU thermal sensor; monitoring disabled
[    8.822750] wmi: Mapper loaded
[    8.832086] parport_pc 00:07: reported by Plug and Play ACPI
[    8.832144] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
[    8.867684] HDA Intel 0000:00:14.2: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    8.868428] udevd[395]: renamed network interface eth0 to eth1
[    8.893991] ppdev: user-space parallel port driver
[    8.920134] lp0: using parport0 (interrupt-driven).
[    8.945450] type=1400 audit(1319479916.027:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=673 comm="apparmor_parser"
[    8.945463] type=1400 audit(1319479916.027:3): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=680 comm="apparmor_parser"
[    8.945751] type=1400 audit(1319479916.027:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=673 comm="apparmor_parser"
[    8.945766] type=1400 audit(1319479916.027:5): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=680 comm="apparmor_parser"
[    8.945923] type=1400 audit(1319479916.027:6): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=673 comm="apparmor_parser"
[    8.945960] type=1400 audit(1319479916.027:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=680 comm="apparmor_parser"
[    9.141960] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[    9.142108] HDA Intel 0000:01:05.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    9.142138] HDA Intel 0000:01:05.1: setting latency timer to 64
[    9.181448] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
[    9.181452] Disabling lock debugging due to kernel taint
[    9.235514] [fglrx] Maximum main memory to use for locked dma buffers: 7589 MBytes.
[    9.235564] [fglrx]   vendor: 1002 device: 9610 count: 1
[    9.235926] [fglrx] ioport: bar 1, base 0xd000, size: 0x100
[    9.235937] pci 0000:01:05.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    9.235941] pci 0000:01:05.0: setting latency timer to 64
[    9.236293] [fglrx] Kernel PAT support is enabled
[    9.236309] [fglrx] module loaded - fglrx 8.88.7 [Jul 28 2011] with 1 minors
[    9.577622] vesafb: mode is 1400x1050x32, linelength=5632, pages=0
[    9.577624] vesafb: scrolling: redraw
[    9.577627] vesafb: Truecolor: size=0:8:8:8, shift=0:16:8:0
[    9.580510] vesafb: framebuffer at 0xd0000000, mapped to 0xfa600000, using 5824k, total 5824k
[    9.580714] Console: switching to colour frame buffer device 175x65
[    9.580747] fb0: VESA VGA frame buffer device
[    9.851200] EXT4-fs (sda6): re-mounted. Opts: errors=remount-ro
[    9.927792] EXT4-fs (sda7): mounted filesystem with ordered data mode. Opts: (null)
[   10.190000] type=1400 audit(1319479917.271:8): apparmor="STATUS" operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" pid=948 comm="apparmor_parser"
[   10.190374] type=1400 audit(1319479917.271:9): apparmor="STATUS" operation="profile_load" name="/usr/sbin/cupsd" pid=948 comm="apparmor_parser"
[   10.251404] r8169 0000:03:00.0: eth1: link down
[   10.251409] r8169 0000:03:00.0: eth1: link down
[   10.251583] ADDRCONF(NETDEV_UP): eth1: link is not ready
[   10.663823] type=1400 audit(1319479917.743:10): apparmor="STATUS" operation="profile_load" name="/usr/lib/lightdm/lightdm-guest-session-wrapper" pid=969 comm="apparmor_parser"
[   10.665300] type=1400 audit(1319479917.747:11): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=970 comm="apparmor_parser"
[   10.726288] init: failsafe main process (897) killed by TERM signal
[   10.728208] init: apport pre-start process (1006) terminated with status 1
[   10.736778] init: apport post-stop process (1036) terminated with status 1
[   10.899909] Bluetooth: Core ver 2.16
[   10.899930] NET: Registered protocol family 31
[   10.899932] Bluetooth: HCI device and connection manager initialized
[   10.899934] Bluetooth: HCI socket layer initialized
[   10.899935] Bluetooth: L2CAP socket layer initialized
[   10.899969] Bluetooth: SCO socket layer initialized
[   10.901312] Bluetooth: RFCOMM TTY layer initialized
[   10.901315] Bluetooth: RFCOMM socket layer initialized
[   10.901317] Bluetooth: RFCOMM ver 1.11
[   10.917278] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   10.917280] Bluetooth: BNEP filters: protocol multicast
[   11.652216] EXT4-fs (sda6): re-mounted. Opts: errors=remount-ro,commit=0
[   11.759495] EXT4-fs (sda7): re-mounted. Opts: commit=0
[   11.885416] [fglrx] Could not enable MSI; System prevented initialization
[   11.885854] [fglrx] Firegl kernel thread PID: 1167
[   11.885891] [fglrx] Firegl kernel thread PID: 1168
[   11.885927] [fglrx] Firegl kernel thread PID: 1169
[   11.886171] [fglrx] IRQ 18 Enabled
[   11.944934] r8169 0000:03:00.0: eth1: link up
[   11.945101] ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
[   12.714595] [fglrx] Gart USWC size:1279 M.
[   12.714599] [fglrx] Gart cacheable size:508 M.
[   12.714603] [fglrx] Reserved FB block: Shared offset:0, size:1000000 
[   12.714605] [fglrx] Reserved FB block: Unshared offset:fbfa000, size:401000 
[   12.714607] [fglrx] Reserved FB block: Unshared offset:fffb000, size:5000 
[   14.531618] EXT4-fs (sda6): re-mounted. Opts: errors=remount-ro,commit=0
[   14.533557] EXT4-fs (sda7): re-mounted. Opts: commit=0
[   22.024009] eth1: no IPv6 routers present
[   55.348780] [fglrx] IRQ 18 Disabled
[   56.058371] [fglrx] Could not enable MSI; System prevented initialization
[   56.058816] [fglrx] Firegl kernel thread PID: 1865
[   56.058852] [fglrx] Firegl kernel thread PID: 1866
[   56.058887] [fglrx] Firegl kernel thread PID: 1867
[   56.059134] [fglrx] IRQ 18 Enabled
[   56.320136] [fglrx] Gart USWC size:1279 M.
[   56.320139] [fglrx] Gart cacheable size:508 M.
[   56.320143] [fglrx] Reserved FB block: Shared offset:0, size:1000000 
[   56.320145] [fglrx] Reserved FB block: Unshared offset:fbfa000, size:401000 
[   56.320147] [fglrx] Reserved FB block: Unshared offset:fffb000, size:5000 
[ 1116.192474] EXT4-fs (sdb2): warning: maximal mount count reached, running e2fsck is recommended
[ 1116.193062] EXT4-fs (sdb2): mounted filesystem with ordered data mode. Opts: (null)
[ 3319.881610] EXT3-fs: barriers not enabled
[ 3319.891651] kjournald starting.  Commit interval 5 seconds
[ 3319.891693] EXT3-fs (sdb5): warning: checktime reached, running e2fsck is recommended
[ 3319.891902] EXT3-fs (sdb5): using internal journal
[ 3319.891912] EXT3-fs (sdb5): mounted filesystem with ordered data mode
[ 3499.248808] sr 6:0:0:0: [sr1]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 3499.248821] sr 6:0:0:0: [sr1]  Sense Key : Illegal Request [current] 
[ 3499.248832] sr 6:0:0:0: [sr1]  Add. Sense: Illegal mode for this track
[ 3499.248845] sr 6:0:0:0: [sr1] CDB: Read(10): 28 00 00 00 00 10 00 00 02 00
[ 3499.248864] end_request: I/O error, dev sr1, sector 64
[ 3499.248873] quiet_error: 24 callbacks suppressed
[ 3499.248880] Buffer I/O error on device sr1, logical block 8
[ 3499.249722] sr 6:0:0:0: [sr1]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 3499.249730] sr 6:0:0:0: [sr1]  Sense Key : Illegal Request [current] 
[ 3499.249739] sr 6:0:0:0: [sr1]  Add. Sense: Illegal mode for this track
[ 3499.249750] sr 6:0:0:0: [sr1] CDB: Read(10): 28 00 00 00 00 10 00 00 02 00
[ 3499.249769] end_request: I/O error, dev sr1, sector 64
[ 3499.249775] Buffer I/O error on device sr1, logical block 8
[ 3499.898620] sr 6:0:0:0: [sr1]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 3499.898632] sr 6:0:0:0: [sr1]  Sense Key : Illegal Request [current] 
[ 3499.898644] sr 6:0:0:0: [sr1]  Add. Sense: Illegal mode for this track
[ 3499.898656] sr 6:0:0:0: [sr1] CDB: Read(10): 28 00 00 00 00 10 00 00 02 00
[ 3499.898676] end_request: I/O error, dev sr1, sector 64
[ 3499.898685] Buffer I/O error on device sr1, logical block 8
[ 3499.972301] sr 6:0:0:0: [sr1]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 3499.972312] sr 6:0:0:0: [sr1]  Sense Key : Illegal Request [current] 
[ 3499.972322] sr 6:0:0:0: [sr1]  Add. Sense: Illegal mode for this track
[ 3499.972333] sr 6:0:0:0: [sr1] CDB: Read(10): 28 00 00 00 00 10 00 00 02 00
[ 3499.972352] end_request: I/O error, dev sr1, sector 64
[ 3499.972360] Buffer I/O error on device sr1, logical block 8
[ 3500.089585] sr 6:0:0:0: [sr1]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 3500.089597] sr 6:0:0:0: [sr1]  Sense Key : Illegal Request [current] 
[ 3500.089607] sr 6:0:0:0: [sr1]  Add. Sense: Illegal mode for this track
[ 3500.089619] sr 6:0:0:0: [sr1] CDB: Read(10): 28 00 00 00 00 10 00 00 02 00
[ 3500.089639] end_request: I/O error, dev sr1, sector 64
[ 3500.089648] Buffer I/O error on device sr1, logical block 8
[ 3500.161597] sr 6:0:0:0: [sr1]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 3500.161609] sr 6:0:0:0: [sr1]  Sense Key : Illegal Request [current] 
[ 3500.161619] sr 6:0:0:0: [sr1]  Add. Sense: Illegal mode for this track
[ 3500.161630] sr 6:0:0:0: [sr1] CDB: Read(10): 28 00 00 00 00 10 00 00 02 00
[ 3500.161649] end_request: I/O error, dev sr1, sector 64
[ 3500.161657] Buffer I/O error on device sr1, logical block 8
[ 3500.313220] sr 6:0:0:0: [sr1]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 3500.313231] sr 6:0:0:0: [sr1]  Sense Key : Illegal Request [current] 
[ 3500.313241] sr 6:0:0:0: [sr1]  Add. Sense: Illegal mode for this track
[ 3500.313252] sr 6:0:0:0: [sr1] CDB: Read(10): 28 00 00 00 00 10 00 00 02 00
[ 3500.313270] end_request: I/O error, dev sr1, sector 64
[ 3500.313278] Buffer I/O error on device sr1, logical block 8
[ 3500.385672] sr 6:0:0:0: [sr1]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 3500.385683] sr 6:0:0:0: [sr1]  Sense Key : Illegal Request [current] 
[ 3500.385693] sr 6:0:0:0: [sr1]  Add. Sense: Illegal mode for this track
[ 3500.385704] sr 6:0:0:0: [sr1] CDB: Read(10): 28 00 00 00 00 10 00 00 02 00
[ 3500.385722] end_request: I/O error, dev sr1, sector 64
[ 3500.385730] Buffer I/O error on device sr1, logical block 8
[ 3501.799361] sr 6:0:0:0: [sr1]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 3501.799374] sr 6:0:0:0: [sr1]  Sense Key : Illegal Request [current] 
[ 3501.799385] sr 6:0:0:0: [sr1]  Add. Sense: Illegal mode for this track
[ 3501.799398] sr 6:0:0:0: [sr1] CDB: Read(10): 28 00 00 00 00 10 00 00 02 00
[ 3501.799418] end_request: I/O error, dev sr1, sector 64
[ 3501.799428] Buffer I/O error on device sr1, logical block 8
[ 3501.869551] sr 6:0:0:0: [sr1]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 3501.869562] sr 6:0:0:0: [sr1]  Sense Key : Illegal Request [current] 
[ 3501.869572] sr 6:0:0:0: [sr1]  Add. Sense: Illegal mode for this track
[ 3501.869583] sr 6:0:0:0: [sr1] CDB: Read(10): 28 00 00 00 00 10 00 00 02 00
[ 3501.869602] end_request: I/O error, dev sr1, sector 64
[ 3501.869610] Buffer I/O error on device sr1, logical block 8
[ 3570.939312] sr 6:0:0:0: [sr1]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 3570.939325] sr 6:0:0:0: [sr1]  Sense Key : Illegal Request [current] 
[ 3570.939336] sr 6:0:0:0: [sr1]  Add. Sense: Illegal mode for this track
[ 3570.939349] sr 6:0:0:0: [sr1] CDB: Read(10): 28 00 00 00 00 10 00 00 02 00
[ 3570.939369] end_request: I/O error, dev sr1, sector 64
[ 3570.939378] Buffer I/O error on device sr1, logical block 8
[ 3571.012344] sr 6:0:0:0: [sr1]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 3571.012355] sr 6:0:0:0: [sr1]  Sense Key : Illegal Request [current] 
[ 3571.012364] sr 6:0:0:0: [sr1]  Add. Sense: Illegal mode for this track
[ 3571.012375] sr 6:0:0:0: [sr1] CDB: Read(10): 28 00 00 00 00 10 00 00 02 00
[ 3571.012393] end_request: I/O error, dev sr1, sector 64
[ 3571.012402] Buffer I/O error on device sr1, logical block 8
[ 3571.086420] sr 6:0:0:0: [sr1]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 3571.086430] sr 6:0:0:0: [sr1]  Sense Key : Illegal Request [current] 
[ 3571.086440] sr 6:0:0:0: [sr1]  Add. Sense: Illegal mode for this track
[ 3571.086450] sr 6:0:0:0: [sr1] CDB: Read(10): 28 00 00 00 00 10 00 00 02 00
[ 3571.086468] end_request: I/O error, dev sr1, sector 64
[ 3571.086476] Buffer I/O error on device sr1, logical block 8
[ 3571.160491] sr 6:0:0:0: [sr1]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 3571.160501] sr 6:0:0:0: [sr1]  Sense Key : Illegal Request [current] 
[ 3571.160511] sr 6:0:0:0: [sr1]  Add. Sense: Illegal mode for this track
[ 3571.160523] sr 6:0:0:0: [sr1] CDB: Read(10): 28 00 00 00 00 10 00 00 02 00
[ 3571.160541] end_request: I/O error, dev sr1, sector 64
[ 3571.160549] Buffer I/O error on device sr1, logical block 8
[ 3571.236277] sr 6:0:0:0: [sr1]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 3571.236287] sr 6:0:0:0: [sr1]  Sense Key : Illegal Request [current] 
[ 3571.236296] sr 6:0:0:0: [sr1]  Add. Sense: Illegal mode for this track
[ 3571.236307] sr 6:0:0:0: [sr1] CDB: Read(10): 28 00 00 00 00 10 00 00 02 00
[ 3571.236325] end_request: I/O error, dev sr1, sector 64
[ 3571.236333] Buffer I/O error on device sr1, logical block 8
[ 3571.308658] sr 6:0:0:0: [sr1]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 3571.308668] sr 6:0:0:0: [sr1]  Sense Key : Illegal Request [current] 
[ 3571.308677] sr 6:0:0:0: [sr1]  Add. Sense: Illegal mode for this track
[ 3571.308688] sr 6:0:0:0: [sr1] CDB: Read(10): 28 00 00 00 00 10 00 00 02 00
[ 3571.308706] end_request: I/O error, dev sr1, sector 64
[ 3571.308714] Buffer I/O error on device sr1, logical block 8
[ 3571.586659] sr 6:0:0:0: [sr1]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 3571.586672] sr 6:0:0:0: [sr1]  Sense Key : Illegal Request [current] 
[ 3571.586684] sr 6:0:0:0: [sr1]  Add. Sense: Illegal mode for this track
[ 3571.586697] sr 6:0:0:0: [sr1] CDB: Read(10): 28 00 00 00 00 10 00 00 02 00
[ 3571.586717] end_request: I/O error, dev sr1, sector 64
[ 3571.586727] Buffer I/O error on device sr1, logical block 8
[ 3571.662463] sr 6:0:0:0: [sr1]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 3571.662474] sr 6:0:0:0: [sr1]  Sense Key : Illegal Request [current] 
[ 3571.662484] sr 6:0:0:0: [sr1]  Add. Sense: Illegal mode for this track
[ 3571.662496] sr 6:0:0:0: [sr1] CDB: Read(10): 28 00 00 00 00 10 00 00 02 00
[ 3571.662515] end_request: I/O error, dev sr1, sector 64
[ 3571.662523] Buffer I/O error on device sr1, logical block 8
[ 3571.933711] sr 6:0:0:0: [sr1]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 3571.933724] sr 6:0:0:0: [sr1]  Sense Key : Illegal Request [current] 
[ 3571.933735] sr 6:0:0:0: [sr1]  Add. Sense: Illegal mode for this track
[ 3571.933747] sr 6:0:0:0: [sr1] CDB: Read(10): 28 00 00 00 00 10 00 00 02 00
[ 3571.933767] end_request: I/O error, dev sr1, sector 64
[ 3571.933776] Buffer I/O error on device sr1, logical block 8
[ 3572.005431] sr 6:0:0:0: [sr1]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 3572.005434] sr 6:0:0:0: [sr1]  Sense Key : Illegal Request [current] 
[ 3572.005437] sr 6:0:0:0: [sr1]  Add. Sense: Illegal mode for this track
[ 3572.005441] sr 6:0:0:0: [sr1] CDB: Read(10): 28 00 00 00 00 10 00 00 02 00
[ 3572.005446] end_request: I/O error, dev sr1, sector 64
[ 3572.005449] Buffer I/O error on device sr1, logical block 8
[ 3572.193210] sr 6:0:0:0: [sr1]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 3572.193222] sr 6:0:0:0: [sr1]  Sense Key : Illegal Request [current] 
[ 3572.193233] sr 6:0:0:0: [sr1]  Add. Sense: Illegal mode for this track
[ 3572.193246] sr 6:0:0:0: [sr1] CDB: Read(10): 28 00 00 00 00 10 00 00 02 00
[ 3572.193266] end_request: I/O error, dev sr1, sector 64
[ 3572.265076] sr 6:0:0:0: [sr1]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 3572.265087] sr 6:0:0:0: [sr1]  Sense Key : Illegal Request [current] 
[ 3572.265097] sr 6:0:0:0: [sr1]  Add. Sense: Illegal mode for this track
[ 3572.265108] sr 6:0:0:0: [sr1] CDB: Read(10): 28 00 00 00 00 10 00 00 02 00
[ 3572.265127] end_request: I/O error, dev sr1, sector 64
[ 3572.469695] sr 6:0:0:0: [sr1]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 3572.469707] sr 6:0:0:0: [sr1]  Sense Key : Illegal Request [current] 
[ 3572.469719] sr 6:0:0:0: [sr1]  Add. Sense: Illegal mode for this track
[ 3572.469731] sr 6:0:0:0: [sr1] CDB: Read(10): 28 00 00 00 00 10 00 00 02 00
[ 3572.469751] end_request: I/O error, dev sr1, sector 64
[ 3572.541576] sr 6:0:0:0: [sr1]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 3572.541587] sr 6:0:0:0: [sr1]  Sense Key : Illegal Request [current] 
[ 3572.541597] sr 6:0:0:0: [sr1]  Add. Sense: Illegal mode for this track
[ 3572.541608] sr 6:0:0:0: [sr1] CDB: Read(10): 28 00 00 00 00 10 00 00 02 00
[ 3572.541626] end_request: I/O error, dev sr1, sector 64
[ 3591.963435] sr 6:0:0:0: [sr1]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 3591.963448] sr 6:0:0:0: [sr1]  Sense Key : Illegal Request [current] 
[ 3591.963460] sr 6:0:0:0: [sr1]  Add. Sense: Illegal mode for this track
[ 3591.963472] sr 6:0:0:0: [sr1] CDB: Read(10): 28 00 00 00 00 10 00 00 02 00
[ 3591.963493] end_request: I/O error, dev sr1, sector 64
[ 3591.963502] quiet_error: 4 callbacks suppressed
[ 3591.963508] Buffer I/O error on device sr1, logical block 8
[ 3592.036897] sr 6:0:0:0: [sr1]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 3592.036908] sr 6:0:0:0: [sr1]  Sense Key : Illegal Request [current] 
[ 3592.036918] sr 6:0:0:0: [sr1]  Add. Sense: Illegal mode for this track
[ 3592.036929] sr 6:0:0:0: [sr1] CDB: Read(10): 28 00 00 00 00 10 00 00 02 00
[ 3592.036947] end_request: I/O error, dev sr1, sector 64
[ 3592.036955] Buffer I/O error on device sr1, logical block 8
[ 3592.222387] sr 6:0:0:0: [sr1]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 3592.222400] sr 6:0:0:0: [sr1]  Sense Key : Illegal Request [current] 
[ 3592.222411] sr 6:0:0:0: [sr1]  Add. Sense: Illegal mode for this track
[ 3592.222424] sr 6:0:0:0: [sr1] CDB: Read(10): 28 00 00 00 00 10 00 00 02 00
[ 3592.222443] end_request: I/O error, dev sr1, sector 64
[ 3592.222453] Buffer I/O error on device sr1, logical block 8
[ 3592.294823] sr 6:0:0:0: [sr1]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 3592.294834] sr 6:0:0:0: [sr1]  Sense Key : Illegal Request [current] 
[ 3592.294844] sr 6:0:0:0: [sr1]  Add. Sense: Illegal mode for this track
[ 3592.294855] sr 6:0:0:0: [sr1] CDB: Read(10): 28 00 00 00 00 10 00 00 02 00
[ 3592.294874] end_request: I/O error, dev sr1, sector 64
[ 3592.294882] Buffer I/O error on device sr1, logical block 8
[ 3602.055213] sr 6:0:0:0: [sr1]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 3602.055226] sr 6:0:0:0: [sr1]  Sense Key : Illegal Request [current] 
[ 3602.055238] sr 6:0:0:0: [sr1]  Add. Sense: Illegal mode for this track
[ 3602.055250] sr 6:0:0:0: [sr1] CDB: Read(10): 28 00 00 00 00 10 00 00 02 00
[ 3602.055270] end_request: I/O error, dev sr1, sector 64
[ 3602.055280] Buffer I/O error on device sr1, logical block 8
[ 3602.127639] sr 6:0:0:0: [sr1]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 3602.127651] sr 6:0:0:0: [sr1]  Sense Key : Illegal Request [current] 
[ 3602.127661] sr 6:0:0:0: [sr1]  Add. Sense: Illegal mode for this track
[ 3602.127672] sr 6:0:0:0: [sr1] CDB: Read(10): 28 00 00 00 00 10 00 00 02 00
[ 3602.127690] end_request: I/O error, dev sr1, sector 64
[ 3602.127699] Buffer I/O error on device sr1, logical block 8
[ 3602.289327] sr 6:0:0:0: [sr1]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 3602.289338] sr 6:0:0:0: [sr1]  Sense Key : Illegal Request [current] 
[ 3602.289349] sr 6:0:0:0: [sr1]  Add. Sense: Illegal mode for this track
[ 3602.289361] sr 6:0:0:0: [sr1] CDB: Read(10): 28 00 00 00 00 10 00 00 02 00
[ 3602.289381] end_request: I/O error, dev sr1, sector 64
[ 3602.289390] Buffer I/O error on device sr1, logical block 8
[ 3602.361804] sr 6:0:0:0: [sr1]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 3602.361814] sr 6:0:0:0: [sr1]  Sense Key : Illegal Request [current] 
[ 3602.361824] sr 6:0:0:0: [sr1]  Add. Sense: Illegal mode for this track
[ 3602.361834] sr 6:0:0:0: [sr1] CDB: Read(10): 28 00 00 00 00 10 00 00 02 00
[ 3602.361852] end_request: I/O error, dev sr1, sector 64
[ 3602.361860] Buffer I/O error on device sr1, logical block 8
[ 3967.001921] sr 6:0:0:0: [sr1]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 3967.001933] sr 6:0:0:0: [sr1]  Sense Key : Illegal Request [current] 
[ 3967.001945] sr 6:0:0:0: [sr1]  Add. Sense: Illegal mode for this track
[ 3967.001957] sr 6:0:0:0: [sr1] CDB: Read(10): 28 00 00 00 00 10 00 00 02 00
[ 3967.001977] end_request: I/O error, dev sr1, sector 64
[ 3967.001986] Buffer I/O error on device sr1, logical block 8
[ 3967.079564] sr 6:0:0:0: [sr1]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 3967.079575] sr 6:0:0:0: [sr1]  Sense Key : Illegal Request [current] 
[ 3967.079585] sr 6:0:0:0: [sr1]  Add. Sense: Illegal mode for this track
[ 3967.079596] sr 6:0:0:0: [sr1] CDB: Read(10): 28 00 00 00 00 10 00 00 02 00
[ 3967.079615] end_request: I/O error, dev sr1, sector 64
[ 3967.079623] Buffer I/O error on device sr1, logical block 8
[ 3967.154084] sr 6:0:0:0: [sr1]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 3967.154095] sr 6:0:0:0: [sr1]  Sense Key : Illegal Request [current] 
[ 3967.154104] sr 6:0:0:0: [sr1]  Add. Sense: Illegal mode for this track
[ 3967.154115] sr 6:0:0:0: [sr1] CDB: Read(10): 28 00 00 00 00 10 00 00 02 00
[ 3967.154134] end_request: I/O error, dev sr1, sector 64
[ 3967.154142] Buffer I/O error on device sr1, logical block 8
[ 3967.229880] sr 6:0:0:0: [sr1]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 3967.229890] sr 6:0:0:0: [sr1]  Sense Key : Illegal Request [current] 
[ 3967.229899] sr 6:0:0:0: [sr1]  Add. Sense: Illegal mode for this track
[ 3967.229910] sr 6:0:0:0: [sr1] CDB: Read(10): 28 00 00 00 00 10 00 00 02 00
[ 3967.229928] end_request: I/O error, dev sr1, sector 64
[ 3967.229935] Buffer I/O error on device sr1, logical block 8
[ 3967.299658] sr 6:0:0:0: [sr1]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 3967.299663] sr 6:0:0:0: [sr1]  Sense Key : Illegal Request [current] 
[ 3967.299667] sr 6:0:0:0: [sr1]  Add. Sense: Illegal mode for this track
[ 3967.299671] sr 6:0:0:0: [sr1] CDB: Read(10): 28 00 00 00 00 10 00 00 02 00
[ 3967.299677] end_request: I/O error, dev sr1, sector 64
[ 3967.299680] Buffer I/O error on device sr1, logical block 8
[ 3967.378158] sr 6:0:0:0: [sr1]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 3967.378169] sr 6:0:0:0: [sr1]  Sense Key : Illegal Request [current] 
[ 3967.378179] sr 6:0:0:0: [sr1]  Add. Sense: Illegal mode for this track
[ 3967.378190] sr 6:0:0:0: [sr1] CDB: Read(10): 28 00 00 00 00 10 00 00 02 00
[ 3967.378208] end_request: I/O error, dev sr1, sector 64
[ 3967.378217] Buffer I/O error on device sr1, logical block 8
[ 3967.449977] sr 6:0:0:0: [sr1]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 3967.449987] sr 6:0:0:0: [sr1]  Sense Key : Illegal Request [current] 
[ 3967.449997] sr 6:0:0:0: [sr1]  Add. Sense: Illegal mode for this track
[ 3967.450008] sr 6:0:0:0: [sr1] CDB: Read(10): 28 00 00 00 00 10 00 00 02 00
[ 3967.450026] end_request: I/O error, dev sr1, sector 64
[ 3967.450033] Buffer I/O error on device sr1, logical block 8
[ 3967.633718] sr 6:0:0:0: [sr1]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 3967.633731] sr 6:0:0:0: [sr1]  Sense Key : Illegal Request [current] 
[ 3967.633743] sr 6:0:0:0: [sr1]  Add. Sense: Illegal mode for this track
[ 3967.633756] sr 6:0:0:0: [sr1] CDB: Read(10): 28 00 00 00 00 10 00 00 02 00
[ 3967.633776] end_request: I/O error, dev sr1, sector 64
[ 3967.633785] Buffer I/O error on device sr1, logical block 8
[ 3967.703895] sr 6:0:0:0: [sr1]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 3967.703905] sr 6:0:0:0: [sr1]  Sense Key : Illegal Request [current] 
[ 3967.703915] sr 6:0:0:0: [sr1]  Add. Sense: Illegal mode for this track
[ 3967.703926] sr 6:0:0:0: [sr1] CDB: Read(10): 28 00 00 00 00 10 00 00 02 00
[ 3967.703944] end_request: I/O error, dev sr1, sector 64
[ 3967.703952] Buffer I/O error on device sr1, logical block 8
[ 3967.963603] sr 6:0:0:0: [sr1]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 3967.963616] sr 6:0:0:0: [sr1]  Sense Key : Illegal Request [current] 
[ 3967.963628] sr 6:0:0:0: [sr1]  Add. Sense: Illegal mode for this track
[ 3967.963640] sr 6:0:0:0: [sr1] CDB: Read(10): 28 00 00 00 00 10 00 00 02 00
[ 3967.963660] end_request: I/O error, dev sr1, sector 64
[ 3967.963669] Buffer I/O error on device sr1, logical block 8
[ 3968.036620] sr 6:0:0:0: [sr1]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 3968.036631] sr 6:0:0:0: [sr1]  Sense Key : Illegal Request [current] 
[ 3968.036641] sr 6:0:0:0: [sr1]  Add. Sense: Illegal mode for this track
[ 3968.036652] sr 6:0:0:0: [sr1] CDB: Read(10): 28 00 00 00 00 10 00 00 02 00
[ 3968.036671] end_request: I/O error, dev sr1, sector 64
[ 3968.216064] sr 6:0:0:0: [sr1]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 3968.216077] sr 6:0:0:0: [sr1]  Sense Key : Illegal Request [current] 
[ 3968.216088] sr 6:0:0:0: [sr1]  Add. Sense: Illegal mode for this track
[ 3968.216101] sr 6:0:0:0: [sr1] CDB: Read(10): 28 00 00 00 00 10 00 00 02 00
[ 3968.216120] end_request: I/O error, dev sr1, sector 64
[ 3968.292880] sr 6:0:0:0: [sr1]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 3968.292891] sr 6:0:0:0: [sr1]  Sense Key : Illegal Request [current] 
[ 3968.292900] sr 6:0:0:0: [sr1]  Add. Sense: Illegal mode for this track
[ 3968.292912] sr 6:0:0:0: [sr1] CDB: Read(10): 28 00 00 00 00 10 00 00 02 00
[ 3968.292930] end_request: I/O error, dev sr1, sector 64
[ 3970.536928] sr 6:0:0:0: [sr1]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 3970.536940] sr 6:0:0:0: [sr1]  Sense Key : Illegal Request [current] 
[ 3970.536952] sr 6:0:0:0: [sr1]  Add. Sense: Illegal mode for this track
[ 3970.536965] sr 6:0:0:0: [sr1] CDB: Read(10): 28 00 00 00 00 10 00 00 02 00
[ 3970.536985] end_request: I/O error, dev sr1, sector 64
[ 3970.609055] sr 6:0:0:0: [sr1]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 3970.609067] sr 6:0:0:0: [sr1]  Sense Key : Illegal Request [current] 
[ 3970.609076] sr 6:0:0:0: [sr1]  Add. Sense: Illegal mode for this track
[ 3970.609087] sr 6:0:0:0: [sr1] CDB: Read(10): 28 00 00 00 00 10 00 00 02 00
[ 3970.609106] end_request: I/O error, dev sr1, sector 64
[ 3970.731770] sr 6:0:0:0: [sr1]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 3970.731783] sr 6:0:0:0: [sr1]  Sense Key : Illegal Request [current] 
[ 3970.731794] sr 6:0:0:0: [sr1]  Add. Sense: Illegal mode for this track
[ 3970.731806] sr 6:0:0:0: [sr1] CDB: Read(10): 28 00 00 00 00 10 00 00 02 00
[ 3970.731825] end_request: I/O error, dev sr1, sector 64
[ 3970.868711] sr 6:0:0:0: [sr1]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 3970.868724] sr 6:0:0:0: [sr1]  Sense Key : Illegal Request [current] 
[ 3970.868734] sr 6:0:0:0: [sr1]  Add. Sense: Illegal mode for this track
[ 3970.868746] sr 6:0:0:0: [sr1] CDB: Read(10): 28 00 00 00 00 10 00 00 02 00
[ 3970.868766] end_request: I/O error, dev sr1, sector 64
[ 3970.941115] sr 6:0:0:0: [sr1]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 3970.941126] sr 6:0:0:0: [sr1]  Sense Key : Illegal Request [current] 
[ 3970.941135] sr 6:0:0:0: [sr1]  Add. Sense: Illegal mode for this track
[ 3970.941146] sr 6:0:0:0: [sr1] CDB: Read(10): 28 00 00 00 00 10 00 00 02 00
[ 3970.941165] end_request: I/O error, dev sr1, sector 64
[ 3971.052504] sr 6:0:0:0: [sr1]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 3971.052516] sr 6:0:0:0: [sr1]  Sense Key : Illegal Request [current] 
[ 3971.052527] sr 6:0:0:0: [sr1]  Add. Sense: Illegal mode for this track
[ 3971.052539] sr 6:0:0:0: [sr1] CDB: Read(10): 28 00 00 00 00 10 00 00 02 00
[ 3971.052558] end_request: I/O error, dev sr1, sector 64
[ 3971.180163] sr 6:0:0:0: [sr1]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 3971.180175] sr 6:0:0:0: [sr1]  Sense Key : Illegal Request [current] 
[ 3971.180185] sr 6:0:0:0: [sr1]  Add. Sense: Illegal mode for this track
[ 3971.180197] sr 6:0:0:0: [sr1] CDB: Read(10): 28 00 00 00 00 10 00 00 02 00
[ 3971.180216] end_request: I/O error, dev sr1, sector 64
[ 3971.254301] sr 6:0:0:0: [sr1]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 3971.254314] sr 6:0:0:0: [sr1]  Sense Key : Illegal Request [current] 
[ 3971.254324] sr 6:0:0:0: [sr1]  Add. Sense: Illegal mode for this track
[ 3971.254337] sr 6:0:0:0: [sr1] CDB: Read(10): 28 00 00 00 00 10 00 00 02 00
[ 3971.254356] end_request: I/O error, dev sr1, sector 64
[ 3972.642563] sr 6:0:0:0: [sr1]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 3972.642576] sr 6:0:0:0: [sr1]  Sense Key : Illegal Request [current] 
[ 3972.642587] sr 6:0:0:0: [sr1]  Add. Sense: Illegal mode for this track
[ 3972.642600] sr 6:0:0:0: [sr1] CDB: Read(10): 28 00 00 00 00 10 00 00 02 00
[ 3972.642620] end_request: I/O error, dev sr1, sector 64
[ 3972.642629] quiet_error: 11 callbacks suppressed
[ 3972.642635] Buffer I/O error on device sr1, logical block 8
[ 3972.716121] sr 6:0:0:0: [sr1]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 3972.716131] sr 6:0:0:0: [sr1]  Sense Key : Illegal Request [current] 
[ 3972.716141] sr 6:0:0:0: [sr1]  Add. Sense: Illegal mode for this track
[ 3972.716152] sr 6:0:0:0: [sr1] CDB: Read(10): 28 00 00 00 00 10 00 00 02 00
[ 3972.716171] end_request: I/O error, dev sr1, sector 64
[ 3972.716178] Buffer I/O error on device sr1, logical block 8
[ 4357.361955] sr 6:0:0:0: [sr1]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 4357.361968] sr 6:0:0:0: [sr1]  Sense Key : Illegal Request [current] 
[ 4357.361980] sr 6:0:0:0: [sr1]  Add. Sense: Illegal mode for this track
[ 4357.361992] sr 6:0:0:0: [sr1] CDB: Read(10): 28 00 00 00 00 10 00 00 02 00
[ 4357.362012] end_request: I/O error, dev sr1, sector 64
[ 4357.362022] Buffer I/O error on device sr1, logical block 8
[ 4357.433399] sr 6:0:0:0: [sr1]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 4357.433409] sr 6:0:0:0: [sr1]  Sense Key : Illegal Request [current] 
[ 4357.433419] sr 6:0:0:0: [sr1]  Add. Sense: Illegal mode for this track
[ 4357.433431] sr 6:0:0:0: [sr1] CDB: Read(10): 28 00 00 00 00 10 00 00 02 00
[ 4357.433449] end_request: I/O error, dev sr1, sector 64
[ 4357.433457] Buffer I/O error on device sr1, logical block 8
[ 4357.511620] sr 6:0:0:0: [sr1]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 4357.511631] sr 6:0:0:0: [sr1]  Sense Key : Illegal Request [current] 
[ 4357.511641] sr 6:0:0:0: [sr1]  Add. Sense: Illegal mode for this track
[ 4357.511652] sr 6:0:0:0: [sr1] CDB: Read(10): 28 00 00 00 00 10 00 00 02 00
[ 4357.511670] end_request: I/O error, dev sr1, sector 64
[ 4357.511678] Buffer I/O error on device sr1, logical block 8
[ 4357.582746] sr 6:0:0:0: [sr1]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 4357.582757] sr 6:0:0:0: [sr1]  Sense Key : Illegal Request [current] 
[ 4357.582766] sr 6:0:0:0: [sr1]  Add. Sense: Illegal mode for this track
[ 4357.582777] sr 6:0:0:0: [sr1] CDB: Read(10): 28 00 00 00 00 10 00 00 02 00
[ 4357.582795] end_request: I/O error, dev sr1, sector 64
[ 4357.582803] Buffer I/O error on device sr1, logical block 8
[ 4357.656334] sr 6:0:0:0: [sr1]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 4357.656344] sr 6:0:0:0: [sr1]  Sense Key : Illegal Request [current] 
[ 4357.656353] sr 6:0:0:0: [sr1]  Add. Sense: Illegal mode for this track
[ 4357.656364] sr 6:0:0:0: [sr1] CDB: Read(10): 28 00 00 00 00 10 00 00 02 00
[ 4357.656382] end_request: I/O error, dev sr1, sector 64
[ 4357.656389] Buffer I/O error on device sr1, logical block 8
[ 4357.728189] sr 6:0:0:0: [sr1]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 4357.728199] sr 6:0:0:0: [sr1]  Sense Key : Illegal Request [current] 
[ 4357.728208] sr 6:0:0:0: [sr1]  Add. Sense: Illegal mode for this track
[ 4357.728219] sr 6:0:0:0: [sr1] CDB: Read(10): 28 00 00 00 00 10 00 00 02 00
[ 4357.728237] end_request: I/O error, dev sr1, sector 64
[ 4357.728244] Buffer I/O error on device sr1, logical block 8
[ 4357.804513] sr 6:0:0:0: [sr1]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 4357.804523] sr 6:0:0:0: [sr1]  Sense Key : Illegal Request [current] 
[ 4357.804533] sr 6:0:0:0: [sr1]  Add. Sense: Illegal mode for this track
[ 4357.804544] sr 6:0:0:0: [sr1] CDB: Read(10): 28 00 00 00 00 10 00 00 02 00
[ 4357.804562] end_request: I/O error, dev sr1, sector 64
[ 4357.804569] Buffer I/O error on device sr1, logical block 8
[ 4357.976565] sr 6:0:0:0: [sr1]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 4357.976578] sr 6:0:0:0: [sr1]  Sense Key : Illegal Request [current] 
[ 4357.976589] sr 6:0:0:0: [sr1]  Add. Sense: Illegal mode for this track
[ 4357.976601] sr 6:0:0:0: [sr1] CDB: Read(10): 28 00 00 00 00 10 00 00 02 00
[ 4357.976622] end_request: I/O error, dev sr1, sector 64
[ 4357.976631] Buffer I/O error on device sr1, logical block 8
[ 4358.047245] sr 6:0:0:0: [sr1]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 4358.047256] sr 6:0:0:0: [sr1]  Sense Key : Illegal Request [current] 
[ 4358.047266] sr 6:0:0:0: [sr1]  Add. Sense: Illegal mode for this track
[ 4358.047277] sr 6:0:0:0: [sr1] CDB: Read(10): 28 00 00 00 00 10 00 00 02 00
[ 4358.047295] end_request: I/O error, dev sr1, sector 64
[ 4358.047304] Buffer I/O error on device sr1, logical block 8
[ 4358.309795] sr 6:0:0:0: [sr1]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 4358.309808] sr 6:0:0:0: [sr1]  Sense Key : Illegal Request [current] 
[ 4358.309819] sr 6:0:0:0: [sr1]  Add. Sense: Illegal mode for this track
[ 4358.309831] sr 6:0:0:0: [sr1] CDB: Read(10): 28 00 00 00 00 10 00 00 02 00
[ 4358.309851] end_request: I/O error, dev sr1, sector 64
[ 4358.309861] Buffer I/O error on device sr1, logical block 8
[ 4358.382269] sr 6:0:0:0: [sr1]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 4358.382280] sr 6:0:0:0: [sr1]  Sense Key : Illegal Request [current] 
[ 4358.382289] sr 6:0:0:0: [sr1]  Add. Sense: Illegal mode for this track
[ 4358.382300] sr 6:0:0:0: [sr1] CDB: Read(10): 28 00 00 00 00 10 00 00 02 00
[ 4358.382319] end_request: I/O error, dev sr1, sector 64
[ 4358.561083] sr 6:0:0:0: [sr1]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 4358.561096] sr 6:0:0:0: [sr1]  Sense Key : Illegal Request [current] 
[ 4358.561107] sr 6:0:0:0: [sr1]  Add. Sense: Illegal mode for this track
[ 4358.561119] sr 6:0:0:0: [sr1] CDB: Read(10): 28 00 00 00 00 10 00 00 02 00
[ 4358.561139] end_request: I/O error, dev sr1, sector 64
[ 4358.633554] sr 6:0:0:0: [sr1]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 4358.633565] sr 6:0:0:0: [sr1]  Sense Key : Illegal Request [current] 
[ 4358.633574] sr 6:0:0:0: [sr1]  Add. Sense: Illegal mode for this track
[ 4358.633585] sr 6:0:0:0: [sr1] CDB: Read(10): 28 00 00 00 00 10 00 00 02 00
[ 4358.633603] end_request: I/O error, dev sr1, sector 64
[ 4756.943923] sr 6:0:0:0: [sr1]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 4756.943936] sr 6:0:0:0: [sr1]  Sense Key : Illegal Request [current] 
[ 4756.943948] sr 6:0:0:0: [sr1]  Add. Sense: Illegal mode for this track
[ 4756.943961] sr 6:0:0:0: [sr1] CDB: Read(10): 28 00 00 00 00 10 00 00 02 00
[ 4756.943981] end_request: I/O error, dev sr1, sector 64
[ 4756.943990] quiet_error: 3 callbacks suppressed
[ 4756.943996] Buffer I/O error on device sr1, logical block 8
[ 4757.615633] sr 6:0:0:0: [sr1]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 4757.615646] sr 6:0:0:0: [sr1]  Sense Key : Illegal Request [current] 
[ 4757.615657] sr 6:0:0:0: [sr1]  Add. Sense: Illegal mode for this track
[ 4757.615670] sr 6:0:0:0: [sr1] CDB: Read(10): 28 00 00 00 00 10 00 00 02 00
[ 4757.615691] end_request: I/O error, dev sr1, sector 64
[ 4757.615700] Buffer I/O error on device sr1, logical block 8
[ 4757.696765] sr 6:0:0:0: [sr1]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 4757.696775] sr 6:0:0:0: [sr1]  Sense Key : Illegal Request [current] 
[ 4757.696785] sr 6:0:0:0: [sr1]  Add. Sense: Illegal mode for this track
[ 4757.696796] sr 6:0:0:0: [sr1] CDB: Read(10): 28 00 00 00 00 10 00 00 02 00
[ 4757.696815] end_request: I/O error, dev sr1, sector 64
[ 4757.696823] Buffer I/O error on device sr1, logical block 8
[ 4757.817757] sr 6:0:0:0: [sr1]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 4757.817768] sr 6:0:0:0: [sr1]  Sense Key : Illegal Request [current] 
[ 4757.817778] sr 6:0:0:0: [sr1]  Add. Sense: Illegal mode for this track
[ 4757.817790] sr 6:0:0:0: [sr1] CDB: Read(10): 28 00 00 00 00 10 00 00 02 00
[ 4757.817808] end_request: I/O error, dev sr1, sector 64
[ 4757.817817] Buffer I/O error on device sr1, logical block 8
[ 4757.890229] sr 6:0:0:0: [sr1]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 4757.890239] sr 6:0:0:0: [sr1]  Sense Key : Illegal Request [current] 
[ 4757.890249] sr 6:0:0:0: [sr1]  Add. Sense: Illegal mode for this track
[ 4757.890260] sr 6:0:0:0: [sr1] CDB: Read(10): 28 00 00 00 00 10 00 00 02 00
[ 4757.890278] end_request: I/O error, dev sr1, sector 64
[ 4757.890285] Buffer I/O error on device sr1, logical block 8
[ 4758.044724] sr 6:0:0:0: [sr1]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 4758.044736] sr 6:0:0:0: [sr1]  Sense Key : Illegal Request [current] 
[ 4758.044748] sr 6:0:0:0: [sr1]  Add. Sense: Illegal mode for this track
[ 4758.044760] sr 6:0:0:0: [sr1] CDB: Read(10): 28 00 00 00 00 10 00 00 02 00
[ 4758.044780] end_request: I/O error, dev sr1, sector 64
[ 4758.044789] Buffer I/O error on device sr1, logical block 8
[ 4758.115898] sr 6:0:0:0: [sr1]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 4758.115909] sr 6:0:0:0: [sr1]  Sense Key : Illegal Request [current] 
[ 4758.115918] sr 6:0:0:0: [sr1]  Add. Sense: Illegal mode for this track
[ 4758.115929] sr 6:0:0:0: [sr1] CDB: Read(10): 28 00 00 00 00 10 00 00 02 00
[ 4758.115948] end_request: I/O error, dev sr1, sector 64
[ 4758.115956] Buffer I/O error on device sr1, logical block 8
[ 4759.128096] sr 6:0:0:0: [sr1]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 4759.128109] sr 6:0:0:0: [sr1]  Sense Key : Illegal Request [current] 
[ 4759.128120] sr 6:0:0:0: [sr1]  Add. Sense: Illegal mode for this track
[ 4759.128134] sr 6:0:0:0: [sr1] CDB: Read(10): 28 00 00 00 00 10 00 00 02 00
[ 4759.128154] end_request: I/O error, dev sr1, sector 64
[ 4759.128163] Buffer I/O error on device sr1, logical block 8
[ 4759.199975] sr 6:0:0:0: [sr1]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 4759.199986] sr 6:0:0:0: [sr1]  Sense Key : Illegal Request [current] 
[ 4759.199997] sr 6:0:0:0: [sr1]  Add. Sense: Illegal mode for this track
[ 4759.200037] sr 6:0:0:0: [sr1] CDB: Read(10): 28 00 00 00 00 10 00 00 02 00
[ 4759.200091] end_request: I/O error, dev sr1, sector 64
[ 4759.200104] Buffer I/O error on device sr1, logical block 8
[ 8120.229226] sr 6:0:0:0: [sr1]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 8120.229239] sr 6:0:0:0: [sr1]  Sense Key : Illegal Request [current] 
[ 8120.229251] sr 6:0:0:0: [sr1]  Add. Sense: Illegal mode for this track
[ 8120.229264] sr 6:0:0:0: [sr1] CDB: Read(10): 28 00 00 00 00 10 00 00 02 00
[ 8120.229284] end_request: I/O error, dev sr1, sector 64
[ 8120.229293] Buffer I/O error on device sr1, logical block 8
[ 8120.230195] sr 6:0:0:0: [sr1]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 8120.230206] sr 6:0:0:0: [sr1]  Sense Key : Illegal Request [current] 
[ 8120.230217] sr 6:0:0:0: [sr1]  Add. Sense: Illegal mode for this track
[ 8120.230229] sr 6:0:0:0: [sr1] CDB: Read(10): 28 00 00 00 00 10 00 00 02 00
[ 8120.230249] end_request: I/O error, dev sr1, sector 64
[ 8120.230258] Buffer I/O error on device sr1, logical block 8
[ 8120.848364] sr 6:0:0:0: [sr1]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 8120.848377] sr 6:0:0:0: [sr1]  Sense Key : Illegal Request [current] 
[ 8120.848388] sr 6:0:0:0: [sr1]  Add. Sense: Illegal mode for this track
[ 8120.848401] sr 6:0:0:0: [sr1] CDB: Read(10): 28 00 00 00 00 10 00 00 02 00
[ 8120.848421] end_request: I/O error, dev sr1, sector 64
[ 8120.848431] Buffer I/O error on device sr1, logical block 8
[ 8120.924079] sr 6:0:0:0: [sr1]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 8120.924090] sr 6:0:0:0: [sr1]  Sense Key : Illegal Request [current] 
[ 8120.924100] sr 6:0:0:0: [sr1]  Add. Sense: Illegal mode for this track
[ 8120.924111] sr 6:0:0:0: [sr1] CDB: Read(10): 28 00 00 00 00 10 00 00 02 00
[ 8120.924130] end_request: I/O error, dev sr1, sector 64
[ 8120.924138] Buffer I/O error on device sr1, logical block 8
[ 8121.045679] sr 6:0:0:0: [sr1]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 8121.045691] sr 6:0:0:0: [sr1]  Sense Key : Illegal Request [current] 
[ 8121.045701] sr 6:0:0:0: [sr1]  Add. Sense: Illegal mode for this track
[ 8121.045713] sr 6:0:0:0: [sr1] CDB: Read(10): 28 00 00 00 00 10 00 00 02 00
[ 8121.045732] end_request: I/O error, dev sr1, sector 64
[ 8121.045741] Buffer I/O error on device sr1, logical block 8
[ 8121.121139] sr 6:0:0:0: [sr1]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 8121.121150] sr 6:0:0:0: [sr1]  Sense Key : Illegal Request [current] 
[ 8121.121160] sr 6:0:0:0: [sr1]  Add. Sense: Illegal mode for this track
[ 8121.121171] sr 6:0:0:0: [sr1] CDB: Read(10): 28 00 00 00 00 10 00 00 02 00
[ 8121.121190] end_request: I/O error, dev sr1, sector 64
[ 8121.121198] Buffer I/O error on device sr1, logical block 8
[ 8121.275917] sr 6:0:0:0: [sr1]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 8121.275929] sr 6:0:0:0: [sr1]  Sense Key : Illegal Request [current] 
[ 8121.275940] sr 6:0:0:0: [sr1]  Add. Sense: Illegal mode for this track
[ 8121.275953] sr 6:0:0:0: [sr1] CDB: Read(10): 28 00 00 00 00 10 00 00 02 00
[ 8121.275972] end_request: I/O error, dev sr1, sector 64
[ 8121.275982] Buffer I/O error on device sr1, logical block 8
[ 8121.348272] sr 6:0:0:0: [sr1]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 8121.348282] sr 6:0:0:0: [sr1]  Sense Key : Illegal Request [current] 
[ 8121.348292] sr 6:0:0:0: [sr1]  Add. Sense: Illegal mode for this track
[ 8121.348303] sr 6:0:0:0: [sr1] CDB: Read(10): 28 00 00 00 00 10 00 00 02 00
[ 8121.348321] end_request: I/O error, dev sr1, sector 64
[ 8121.348329] Buffer I/O error on device sr1, logical block 8
[ 8122.188117] sr 6:0:0:0: [sr1]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 8122.188130] sr 6:0:0:0: [sr1]  Sense Key : Illegal Request [current] 
[ 8122.188142] sr 6:0:0:0: [sr1]  Add. Sense: Illegal mode for this track
[ 8122.188154] sr 6:0:0:0: [sr1] CDB: Read(10): 28 00 00 00 00 10 00 00 02 00
[ 8122.188174] end_request: I/O error, dev sr1, sector 64
[ 8122.188184] Buffer I/O error on device sr1, logical block 8
[ 8122.258201] sr 6:0:0:0: [sr1]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 8122.258212] sr 6:0:0:0: [sr1]  Sense Key : Illegal Request [current] 
[ 8122.258222] sr 6:0:0:0: [sr1]  Add. Sense: Illegal mode for this track
[ 8122.258234] sr 6:0:0:0: [sr1] CDB: Read(10): 28 00 00 00 00 10 00 00 02 00
[ 8122.258252] end_request: I/O error, dev sr1, sector 64
[ 8122.258260] Buffer I/O error on device sr1, logical block 8
[ 8129.022481] sr 6:0:0:0: [sr1]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 8129.022494] sr 6:0:0:0: [sr1]  Sense Key : Illegal Request [current] 
[ 8129.022505] sr 6:0:0:0: [sr1]  Add. Sense: Illegal mode for this track
[ 8129.022517] sr 6:0:0:0: [sr1] CDB: Read(10): 28 00 00 00 00 10 00 00 02 00
[ 8129.022537] end_request: I/O error, dev sr1, sector 64
[ 8129.022547] Buffer I/O error on device sr1, logical block 8
[ 8129.094854] sr 6:0:0:0: [sr1]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 8129.094864] sr 6:0:0:0: [sr1]  Sense Key : Illegal Request [current] 
[ 8129.094874] sr 6:0:0:0: [sr1]  Add. Sense: Illegal mode for this track
[ 8129.094884] sr 6:0:0:0: [sr1] CDB: Read(10): 28 00 00 00 00 10 00 00 02 00
[ 8129.094903] end_request: I/O error, dev sr1, sector 64
[ 8129.094911] Buffer I/O error on device sr1, logical block 8
[ 8129.170570] sr 6:0:0:0: [sr1]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 8129.170580] sr 6:0:0:0: [sr1]  Sense Key : Illegal Request [current] 
[ 8129.170590] sr 6:0:0:0: [sr1]  Add. Sense: Illegal mode for this track
[ 8129.170601] sr 6:0:0:0: [sr1] CDB: Read(10): 28 00 00 00 00 10 00 00 02 00
[ 8129.170619] end_request: I/O error, dev sr1, sector 64
[ 8129.170627] Buffer I/O error on device sr1, logical block 8
[ 8129.242941] sr 6:0:0:0: [sr1]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 8129.242952] sr 6:0:0:0: [sr1]  Sense Key : Illegal Request [current] 
[ 8129.242961] sr 6:0:0:0: [sr1]  Add. Sense: Illegal mode for this track
[ 8129.242972] sr 6:0:0:0: [sr1] CDB: Read(10): 28 00 00 00 00 10 00 00 02 00
[ 8129.242989] end_request: I/O error, dev sr1, sector 64
[ 8129.242997] Buffer I/O error on device sr1, logical block 8
[ 8129.315116] sr 6:0:0:0: [sr1]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 8129.315127] sr 6:0:0:0: [sr1]  Sense Key : Illegal Request [current] 
[ 8129.315136] sr 6:0:0:0: [sr1]  Add. Sense: Illegal mode for this track
[ 8129.315147] sr 6:0:0:0: [sr1] CDB: Read(10): 28 00 00 00 00 10 00 00 02 00
[ 8129.315165] end_request: I/O error, dev sr1, sector 64
[ 8129.315173] Buffer I/O error on device sr1, logical block 8
[ 8129.391440] sr 6:0:0:0: [sr1]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 8129.391450] sr 6:0:0:0: [sr1]  Sense Key : Illegal Request [current] 
[ 8129.391460] sr 6:0:0:0: [sr1]  Add. Sense: Illegal mode for this track
[ 8129.391471] sr 6:0:0:0: [sr1] CDB: Read(10): 28 00 00 00 00 10 00 00 02 00
[ 8129.391488] end_request: I/O error, dev sr1, sector 64
[ 8129.391496] Buffer I/O error on device sr1, logical block 8
[ 8129.473934] sr 6:0:0:0: [sr1]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 8129.473945] sr 6:0:0:0: [sr1]  Sense Key : Illegal Request [current] 
[ 8129.473954] sr 6:0:0:0: [sr1]  Add. Sense: Illegal mode for this track
[ 8129.473966] sr 6:0:0:0: [sr1] CDB: Read(10): 28 00 00 00 00 10 00 00 02 00
[ 8129.473984] end_request: I/O error, dev sr1, sector 64
[ 8129.473992] Buffer I/O error on device sr1, logical block 8
[ 8129.692845] sr 6:0:0:0: [sr1]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 8129.692858] sr 6:0:0:0: [sr1]  Sense Key : Illegal Request [current] 
[ 8129.692870] sr 6:0:0:0: [sr1]  Add. Sense: Illegal mode for this track
[ 8129.692882] sr 6:0:0:0: [sr1] CDB: Read(10): 28 00 00 00 00 10 00 00 02 00
[ 8129.692903] end_request: I/O error, dev sr1, sector 64
[ 8129.692912] Buffer I/O error on device sr1, logical block 8
[ 8129.764735] sr 6:0:0:0: [sr1]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 8129.764748] sr 6:0:0:0: [sr1]  Sense Key : Illegal Request [current] 
[ 8129.764759] sr 6:0:0:0: [sr1]  Add. Sense: Illegal mode for this track
[ 8129.764771] sr 6:0:0:0: [sr1] CDB: Read(10): 28 00 00 00 00 10 00 00 02 00
[ 8129.764790] end_request: I/O error, dev sr1, sector 64
[ 8129.764800] Buffer I/O error on device sr1, logical block 8
[ 8130.029612] sr 6:0:0:0: [sr1]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 8130.029625] sr 6:0:0:0: [sr1]  Sense Key : Illegal Request [current] 
[ 8130.029636] sr 6:0:0:0: [sr1]  Add. Sense: Illegal mode for this track
[ 8130.029649] sr 6:0:0:0: [sr1] CDB: Read(10): 28 00 00 00 00 10 00 00 02 00
[ 8130.029668] end_request: I/O error, dev sr1, sector 64
[ 8130.029678] Buffer I/O error on device sr1, logical block 8
[ 8130.102009] sr 6:0:0:0: [sr1]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 8130.102020] sr 6:0:0:0: [sr1]  Sense Key : Illegal Request [current] 
[ 8130.102030] sr 6:0:0:0: [sr1]  Add. Sense: Illegal mode for this track
[ 8130.102042] sr 6:0:0:0: [sr1] CDB: Read(10): 28 00 00 00 00 10 00 00 02 00
[ 8130.102061] end_request: I/O error, dev sr1, sector 64
[ 8130.287086] sr 6:0:0:0: [sr1]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 8130.287099] sr 6:0:0:0: [sr1]  Sense Key : Illegal Request [current] 
[ 8130.287110] sr 6:0:0:0: [sr1]  Add. Sense: Illegal mode for this track
[ 8130.287123] sr 6:0:0:0: [sr1] CDB: Read(10): 28 00 00 00 00 10 00 00 02 00
[ 8130.287143] end_request: I/O error, dev sr1, sector 64
[ 8130.364533] sr 6:0:0:0: [sr1]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 8130.364544] sr 6:0:0:0: [sr1]  Sense Key : Illegal Request [current] 
[ 8130.364554] sr 6:0:0:0: [sr1]  Add. Sense: Illegal mode for this track
[ 8130.364565] sr 6:0:0:0: [sr1] CDB: Read(10): 28 00 00 00 00 10 00 00 02 00
[ 8130.364583] end_request: I/O error, dev sr1, sector 64
[16536.976053] usb 2-6: new high speed USB device number 3 using ehci_hcd
[16537.152002] input: HP Deluxe Webcam KQ246AA HP Deluxe Webcam KQ246AA as /devices/pci0000:00/0000:00:13.2/usb2/2-6/2-6:1.4/input/input4
[16537.152321] generic-usb 0003:04F2:A13C.0002: input,hidraw1: USB HID v1.11 Joystick [HP Deluxe Webcam KQ246AA HP Deluxe Webcam KQ246AA] on usb-0000:00:13.2-6/input4
[16537.477993] Linux video capture interface: v2.00
[16537.479201] uvcvideo: Found UVC 1.00 device HP Deluxe Webcam KQ246AA (04f2:a13c)
[16537.488596] input: HP Deluxe Webcam KQ246AA as /devices/pci0000:00/0000:00:13.2/usb2/2-6/2-6:1.0/input/input5
[16537.488648] usbcore: registered new interface driver uvcvideo
[16537.488650] USB Video Class driver (v1.1.0)
[16537.551711] 3:3:1: cannot get freq at ep 0x84
[16537.552901] usbcore: registered new interface driver snd-usb-audio
[16537.659654] 3:3:1: cannot get freq at ep 0x84
[17570.818176] process `skype' is using obsolete setsockopt SO_BSDCOMPAT
[18452.824084] show_signal_msg: 3 callbacks suppressed
[18452.824089] gnome-alsamixer[9264]: segfault at 18 ip b7406770 sp bfe7d300 error 4 in libgtk-x11-2.0.so.0.2400.6[b73aa000+461000]
[18466.550173] gnome-alsamixer[9267]: segfault at 18 ip b7212770 sp bf9355e0 error 4 in libgtk-x11-2.0.so.0.2400.6[b71b6000+461000]
[18487.845594] gnome-alsamixer[9327]: segfault at 18 ip b734c770 sp bf8be3d0 error 4 in libgtk-x11-2.0.so.0.2400.6[b72f0000+461000]
[18495.964207] gnome-alsamixer[9328]: segfault at 18 ip b7288770 sp bfab7d50 error 4 in libgtk-x11-2.0.so.0.2400.6[b722c000+461000]
[18517.565631] gnome-alsamixer[9335]: segfault at 18 ip b7328770 sp bfbc3540 error 4 in libgtk-x11-2.0.so.0.2400.6[b72cc000+461000]
[22841.427998] guvcview[11816]: segfault at e0ffd90b ip b6379656 sp b10a893c error 5 in libc-2.13.so[b630a000+176000]
[67265.688109] gnome-alsamixer[15835]: segfault at 18 ip b7304770 sp bfa37330 error 4 in libgtk-x11-2.0.so.0.2400.6[b72a8000+461000]
[67269.494710] gnome-alsamixer[15838]: segfault at 18 ip b72bb770 sp bfe11e30 error 4 in libgtk-x11-2.0.so.0.2400.6[b725f000+461000]
[67274.243732] gnome-alsamixer[15841]: segfault at 18 ip b72d0770 sp bfa6dfc0 error 4 in libgtk-x11-2.0.so.0.2400.6[b7274000+461000]
[67278.384737] gnome-alsamixer[15842]: segfault at 18 ip b72a4770 sp bf90d440 error 4 in libgtk-x11-2.0.so.0.2400.6[b7248000+461000]

lsusb produces:

Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 04a9:221c Canon, Inc. CanoScan LiDE 60
Bus 003 Device 002: ID 046d:c408 Logitech, Inc. Marble Mouse (4-button)
Bus 002 Device 002: ID 058f:6361 Alcor Micro Corp. Multimedia Card Reader
Bus 002 Device 003: ID 04f2:a13c Chicony Electronics Co., Ltd 



now what?

---

### Post by no2498 on 2011-10-26
? did it come on in skype or guvcview
you may need to turn them off in your system/preferences auto startup programs
then restart the computer

---

### Post by Bobhuber on 2011-10-26
> **linuxcss said:**
> KQ246AA ... used to work with ubuntu 9.x stuff and so did cheese, sound recorder, and skype.

Right now with  xubuntu 11.10 they don't here.

Does anybody have at least skype working with Hp KQ246AA?

Or what mixer can be added so I can get some feedback that the mic
is really not just under the covers muted?

I have installed sound recorder but when recording nothing gets recorded.
I just put a post out. Try downgrading the kernal to 2.3.38

---

