---
title: "Speed Startup on Ubuntu 10.10"
date: 2011-03-14
forum: General Help
---

### Post by Yoqtan on 2011-03-14
Hello all,

I've been on Ubuntu for quite some time now, and it working very well, better and better with each generation, actually. 
However, I am still missing one quite important piece, which is the boot time. My PC is still taking about 45 seconds to boot, and I don't find a way to decrease this. 
I looked in my dmesg, and here is what I see : 

```

[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.35-28-generic (buildd@roseapple) (gcc version 4.4.5 (Ubuntu/Linaro 4.4.4-14ubuntu5) ) #49-Ubuntu SMP Tue Mar 1 14:40:58 UTC 2011 (Ubuntu 2.6.35-28.49-generic 2.6.35.11)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e4000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 00000000cff80000 (usable)
[    0.000000]  BIOS-e820: 00000000cff80000 - 00000000cff8e000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000cff8e000 - 00000000cffd0000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000cffd0000 - 00000000d0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000ff700000 - 0000000100000000 (reserved)
[    0.000000]  BIOS-e820: 0000000100000000 - 0000000130000000 (usable)
[    0.000000] Notice: NX (Execute Disable) protection cannot be enabled: non-PAE kernel!
[    0.000000] DMI present.
[    0.000000] AMI BIOS detected: BIOS may corrupt low RAM, working around it.
[    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
[    0.000000] e820 update range: 0000000000000000 - 0000000000001000 (usable) ==> (reserved)
[    0.000000] e820 remove range: 00000000000a0000 - 0000000000100000 (usable)
[    0.000000] last_pfn = 0xcff80 max_arch_pfn = 0x100000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-EFFFF uncachable
[    0.000000]   F0000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 0000000000 mask FF80000000 write-back
[    0.000000]   1 base 0080000000 mask FFC0000000 write-back
[    0.000000]   2 base 00C0000000 mask FFF0000000 write-back
[    0.000000]   3 disabled
[    0.000000]   4 disabled
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] TOM2: 0000000130000000 aka 4864M
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] e820 update range: 00000000d0000000 - 0000000100000000 (usable) ==> (reserved)
[    0.000000] Scanning 0 areas for low memory corruption
[    0.000000] modified physical RAM map:
[    0.000000]  modified: 0000000000000000 - 0000000000010000 (reserved)
[    0.000000]  modified: 0000000000010000 - 000000000009fc00 (usable)
[    0.000000]  modified: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  modified: 00000000000e4000 - 0000000000100000 (reserved)
[    0.000000]  modified: 0000000000100000 - 00000000cff80000 (usable)
[    0.000000]  modified: 00000000cff80000 - 00000000cff8e000 (ACPI data)
[    0.000000]  modified: 00000000cff8e000 - 00000000cffd0000 (ACPI NVS)
[    0.000000]  modified: 00000000cffd0000 - 00000000d0000000 (reserved)
[    0.000000]  modified: 00000000ff700000 - 0000000100000000 (reserved)
[    0.000000]  modified: 0000000100000000 - 0000000130000000 (usable)
[    0.000000] initial memory mapped : 0 - 00c00000
[    0.000000] found SMP MP-table at [c00ff780] ff780
[    0.000000] init_memory_mapping: 0000000000000000-00000000377fe000
[    0.000000]  0000000000 - 0000400000 page 4k
[    0.000000]  0000400000 - 0037400000 page 2M
[    0.000000]  0037400000 - 00377fe000 page 4k
[    0.000000] kernel direct mapping tables up to 377fe000 @ 15000-1a000
[    0.000000] RAMDISK: 375ab000 - 37ff0000
[    0.000000] Allocated new RAMDISK: 009a9000 - 013ed893
[    0.000000] Move RAMDISK from 00000000375ab000 - 0000000037fef892 to 009a9000 - 013ed892
[    0.000000] ACPI: RSDP 000fbb70 00024 (v02 ACPIAM)
[    0.000000] ACPI: XSDT cff80100 00064 (v01 _ASUS_ Notebook 20090227 MSFT 00000097)
[    0.000000] ACPI: FACP cff80290 000F4 (v03 022709 FACP0924 20090227 MSFT 00000097)
[    0.000000] ACPI: DSDT cff80610 0888B (v01  A1118 A1118000 00000000 INTL 20060113)
[    0.000000] ACPI: FACS cff8e000 00040
[    0.000000] ACPI: APIC cff80390 0005C (v01 022709 APIC0924 20090227 MSFT 00000097)
[    0.000000] ACPI: MCFG cff803f0 0003C (v01 022709 OEMMCFG  20090227 MSFT 00000097)
[    0.000000] ACPI: SLIC cff80430 00176 (v01 _ASUS_ Notebook 20090227 MSFT 00000097)
[    0.000000] ACPI: ECDT cff805b0 00055 (v01 022709 OEMECDT  20090227 MSFT 00000097)
[    0.000000] ACPI: OEMB cff8e040 00072 (v01 022709 OEMB0924 20090227 MSFT 00000097)
[    0.000000] ACPI: HPET cff88ea0 00038 (v01 022709 OEMHPET  20090227 MSFT 00000097)
[    0.000000] ACPI: SSDT cff88ee0 00390 (v01 A M I  POWERNOW 00000001 AMD  00000001)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] 2439MB HIGHMEM available.
[    0.000000] 887MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 377fe000
[    0.000000]   low ram: 0 - 377fe000
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000010 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x000377fe
[    0.000000]   HighMem  0x000377fe -> 0x000cff80
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[2] active PFN ranges
[    0.000000]     0: 0x00000010 -> 0x0000009f
[    0.000000]     0: 0x00000100 -> 0x000cff80
[    0.000000] On node 0 totalpages: 851727
[    0.000000] free_area_init_node: node 0, pgdat c0801fc0, node_mem_map c13ef200
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3951 pages, LIFO batch:0
[    0.000000]   Normal zone: 1744 pages used for memmap
[    0.000000]   Normal zone: 221486 pages, LIFO batch:31
[    0.000000]   HighMem zone: 4880 pages used for memmap
[    0.000000]   HighMem zone: 619634 pages, LIFO batch:31
[    0.000000] Using APIC driver default
[    0.000000] ACPI: PM-Timer IO Port: 0x808
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 33, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 low level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x8300 base: 0xfed00000
[    0.000000] SMP: Allowing 2 CPUs, 0 hotplug CPUs
[    0.000000] nr_irqs_gsi: 40
[    0.000000] early_res array is doubled to 64 at [16000 - 167ff]
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e4000
[    0.000000] PM: Registered nosave memory: 00000000000e4000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at d0000000 (gap: d0000000:2f700000)
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] setup_percpu: NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:2 nr_node_ids:1
[    0.000000] PERCPU: Embedded 14 pages/cpu @c3000000 s36416 r0 d20928 u2097152
[    0.000000] pcpu-alloc: s36416 r0 d20928 u2097152 alloc=1*4194304
[    0.000000] pcpu-alloc: [0] 0 1 
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 845071
[    0.000000] Kernel command line: root=UUID=ab2dd1dc-789d-40e7-ab12-abe6b29ecc2d ro quiet splash 
[    0.000000] PID hash table entries: 4096 (order: 2, 16384 bytes)
[    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] allocated 17036480 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] Subtract (48 early reservations)
[    0.000000]   #1 [0000001000 - 0000002000]   EX TRAMPOLINE
[    0.000000]   #2 [0000100000 - 00009a4adc]   TEXT DATA BSS
[    0.000000]   #3 [00009a5000 - 00009a81f7]             BRK
[    0.000000]   #4 [00000ff790 - 0000100000]   BIOS reserved
[    0.000000]   #5 [00000ff780 - 00000ff790]    MP-table mpf
[    0.000000]   #6 [000009fc00 - 00000e3bf0]   BIOS reserved
[    0.000000]   #7 [00000e3d74 - 00000ff780]   BIOS reserved
[    0.000000]   #8 [00000e3bf0 - 00000e3d74]    MP-table mpc
[    0.000000]   #9 [0000010000 - 0000011000]      TRAMPOLINE
[    0.000000]   #10 [0000011000 - 0000015000]     ACPI WAKEUP
[    0.000000]   #11 [0000015000 - 0000016000]         PGTABLE
[    0.000000]   #12 [00009a9000 - 00013ee000]     NEW RAMDISK
[    0.000000]   #13 [00013ee000 - 00013ef000]         BOOTMEM
[    0.000000]   #14 [00013ef000 - 0002def000]         BOOTMEM
[    0.000000]   #15 [0002def000 - 0002def004]         BOOTMEM
[    0.000000]   #16 [0002def040 - 0002def100]         BOOTMEM
[    0.000000]   #17 [0002def100 - 0002def154]         BOOTMEM
[    0.000000]   #18 [0002def180 - 0002df2180]         BOOTMEM
[    0.000000]   #19 [0002df2180 - 0002df2268]         BOOTMEM
[    0.000000]   #20 [0002df2280 - 0002dfe280]         BOOTMEM
[    0.000000]   #21 [0002dfe280 - 0002dfe2a5]         BOOTMEM
[    0.000000]   #22 [0002dfe2c0 - 0002dfe2e7]         BOOTMEM
[    0.000000]   #23 [0002dfe300 - 0002dfe418]         BOOTMEM
[    0.000000]   #24 [0002dfe440 - 0002dfe480]         BOOTMEM
[    0.000000]   #25 [0002dfe480 - 0002dfe4c0]         BOOTMEM
[    0.000000]   #26 [0002dfe4c0 - 0002dfe500]         BOOTMEM
[    0.000000]   #27 [0002dfe500 - 0002dfe540]         BOOTMEM
[    0.000000]   #28 [0002dfe540 - 0002dfe580]         BOOTMEM
[    0.000000]   #29 [0002dfe580 - 0002dfe5c0]         BOOTMEM
[    0.000000]   #30 [0002dfe5c0 - 0002dfe600]         BOOTMEM
[    0.000000]   #31 [0002dfe600 - 0002dfe640]         BOOTMEM
[    0.000000]   #32 [0002dfe640 - 0002dfe680]         BOOTMEM
[    0.000000]   #33 [0002dfe680 - 0002dfe690]         BOOTMEM
[    0.000000]   #34 [0002dfe6c0 - 0002dfe700]         BOOTMEM
[    0.000000]   #35 [0002dfe700 - 0002dfe740]         BOOTMEM
[    0.000000]   #36 [0003000000 - 000300e000]         BOOTMEM
[    0.000000]   #37 [0003200000 - 000320e000]         BOOTMEM
[    0.000000]   #38 [0002e00740 - 0002e00744]         BOOTMEM
[    0.000000]   #39 [0002e00780 - 0002e00784]         BOOTMEM
[    0.000000]   #40 [0002e007c0 - 0002e007c8]         BOOTMEM
[    0.000000]   #41 [0002e00800 - 0002e00808]         BOOTMEM
[    0.000000]   #42 [0002e00840 - 0002e008e8]         BOOTMEM
[    0.000000]   #43 [0002e00900 - 0002e00968]         BOOTMEM
[    0.000000]   #44 [0002e00980 - 0002e04980]         BOOTMEM
[    0.000000]   #45 [0002e04980 - 0002e84980]         BOOTMEM
[    0.000000]   #46 [0002e84980 - 0002ec4980]         BOOTMEM
[    0.000000]   #47 [000320e000 - 000424d4c0]         BOOTMEM
[    0.000000] Initializing HighMem for node 0 (000377fe:000cff80)
[    0.000000] Memory: 3343268k/3407360k available (4935k kernel code, 63640k reserved, 2337k data, 688k init, 2498056k highmem)
[    0.000000] virtual kernel memory layout:
[    0.000000]     fixmap  : 0xfff16000 - 0xfffff000   ( 932 kB)
[    0.000000]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[    0.000000]     vmalloc : 0xf7ffe000 - 0xff7fe000   ( 120 MB)
[    0.000000]     lowmem  : 0xc0000000 - 0xf77fe000   ( 887 MB)
[    0.000000]       .init : 0xc081b000 - 0xc08c7000   ( 688 kB)
[    0.000000]       .data : 0xc05d1fde - 0xc081a7a8   (2337 kB)
[    0.000000]       .text : 0xc0100000 - 0xc05d1fde   (4935 kB)
[    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.000000] SLUB: Genslabs=13, HWalign=64, Order=0-3, MinObjects=0, CPUs=2, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000]     RCU dyntick-idle grace-period acceleration is enabled.
[    0.000000]     RCU-based detection of stalled CPUs is disabled.
[    0.000000]     Verbose stalled-CPUs detection is disabled.
[    0.000000] NR_IRQS:2304 nr_irqs:512
[    0.000000] Extended CMOS year: 2000
[    0.000000] Console: colour VGA+ 80x25
[    0.000000] console [tty0] enabled
[    0.000000] hpet clockevent registered
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 2099.411 MHz processor.
[    0.004007] Calibrating delay loop (skipped), value calculated using timer frequency.. 4198.82 BogoMIPS (lpj=8397644)
[    0.004015] pid_max: default: 32768 minimum: 301
[    0.004040] Security Framework initialized
[    0.004065] AppArmor: AppArmor initialized
[    0.004068] Yama: becoming mindful.
[    0.008023] Mount-cache hash table entries: 512
[    0.008188] Initializing cgroup subsys ns
[    0.008194] Initializing cgroup subsys cpuacct
[    0.008201] Initializing cgroup subsys memory
[    0.008213] Initializing cgroup subsys devices
[    0.008218] Initializing cgroup subsys freezer
[    0.008222] Initializing cgroup subsys net_cls
[    0.008256] CPU: Physical Processor ID: 0
[    0.008259] CPU: Processor Core ID: 0
[    0.008264] mce: CPU supports 5 MCE banks
[    0.008283] Performance Events: AMD PMU driver.
[    0.008294] ... version:                0
[    0.008297] ... bit width:              48
[    0.008299] ... generic registers:      4
[    0.008302] ... value mask:             0000ffffffffffff
[    0.008306] ... max period:             00007fffffffffff
[    0.008309] ... fixed-purpose events:   0
[    0.008312] ... event mask:             000000000000000f
[    0.012311] ACPI: Core revision 20100428
[    0.028010] ftrace: converting mcount calls to 0f 1f 44 00 00
[    0.028014] ftrace: allocating 21762 entries in 43 pages
[    0.032094] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.032492] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.074416] CPU0: AMD Turion(tm) X2 Dual-Core Mobile RM-72 stepping 01
[    0.076000] Booting Node   0, Processors  #1 Ok.
[    0.004000] Initializing CPU#1
[    0.164000] TSC synchronization [CPU#0 -> CPU#1]:
[    0.164000] Measured 461186987 cycles TSC warp between CPUs, turning off TSC clock.
[    0.164000] Marking TSC unstable due to check_tsc_sync_source failed
[    0.164009] Brought up 2 CPUs
[    0.164012] Total of 2 processors activated (8387.48 BogoMIPS).
[    0.164282] devtmpfs: initialized
[    0.165064] regulator: core version 0.5
[    0.165130] Time: 22:42:19  Date: 03/14/11
[    0.165184] NET: Registered protocol family 16
[    0.165323] EISA bus registered
[    0.165334] TOM: 00000000d0000000 aka 3328M
[    0.165337] Fam 10h mmconf [e0000000, efffffff]
[    0.165345] TOM2: 0000000130000000 aka 4864M
[    0.165355] ACPI: bus type pci registered
[    0.165469] PCI: MMCONFIG for domain 0000 [bus 00-ff] at [mem 0xe0000000-0xefffffff] (base 0xe0000000)
[    0.165474] PCI: not using MMCONFIG
[    0.165918] PCI: PCI BIOS revision 3.00 entry at 0xf0031, last bus=6
[    0.165920] PCI: Using configuration type 1 for base access
[    0.165922] PCI: Using configuration type 1 for extended access
[    0.168082] Trying to unpack rootfs image as initramfs...
[    0.168766] bio: create slab <bio-0> at 0
[    0.169631] ACPI: EC: EC description table is found, configuring boot EC
[    0.172410] ACPI: Executed 4 blocks of module-level executable AML code
[    0.176293] ACPI: BIOS _OSI(Linux) query ignored
[    0.181103] ACPI: Interpreter enabled
[    0.181107] ACPI: (supports S0 S3 S4 S5)
[    0.181132] ACPI: Using IOAPIC for interrupt routing
[    0.181466] PCI: MMCONFIG for domain 0000 [bus 00-ff] at [mem 0xe0000000-0xefffffff] (base 0xe0000000)
[    0.182586] PCI: MMCONFIG at [mem 0xe0000000-0xefffffff] reserved in ACPI motherboard resources
[    0.182589] PCI: Using MMCONFIG for extended config space
[    0.192130] ACPI: EC: GPE = 0xe, I/O: command/status = 0x66, data = 0x62
[    0.192408] ACPI: No dock devices found.
[    0.192412] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
[    0.192590] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-ff])
[    0.192945] pci_root PNP0A03:00: host bridge window [io  0x0000-0x0cf7]
[    0.192948] pci_root PNP0A03:00: host bridge window [io  0x0d00-0xffff]
[    0.192951] pci_root PNP0A03:00: host bridge window [mem 0x000a0000-0x000bffff]
[    0.192954] pci_root PNP0A03:00: host bridge window [mem 0x000d0000-0x000dffff]
[    0.192957] pci_root PNP0A03:00: host bridge window [mem 0xd0000000-0xdfffffff]
[    0.192960] pci_root PNP0A03:00: host bridge window [mem 0xf0000000-0xfed44fff]
[    0.193117] pci 0000:00:02.0: PME# supported from D0 D3hot D3cold
[    0.193121] pci 0000:00:02.0: PME# disabled
[    0.193207] pci 0000:00:05.0: PME# supported from D0 D3hot D3cold
[    0.193210] pci 0000:00:05.0: PME# disabled
[    0.193263] pci 0000:00:06.0: PME# supported from D0 D3hot D3cold
[    0.193267] pci 0000:00:06.0: PME# disabled
[    0.193320] pci 0000:00:07.0: PME# supported from D0 D3hot D3cold
[    0.193323] pci 0000:00:07.0: PME# disabled
[    0.193381] pci 0000:00:11.0: reg 10: [io  0xb000-0xb007]
[    0.193389] pci 0000:00:11.0: reg 14: [io  0xa000-0xa003]
[    0.193397] pci 0000:00:11.0: reg 18: [io  0x9000-0x9007]
[    0.193405] pci 0000:00:11.0: reg 1c: [io  0x8000-0x8003]
[    0.193413] pci 0000:00:11.0: reg 20: [io  0x7000-0x700f]
[    0.193422] pci 0000:00:11.0: reg 24: [mem 0xfacff800-0xfacffbff]
[    0.193483] pci 0000:00:12.0: reg 10: [mem 0xfacfe000-0xfacfefff]
[    0.193547] pci 0000:00:12.1: reg 10: [mem 0xfacfd000-0xfacfdfff]
[    0.193625] pci 0000:00:12.2: reg 10: [mem 0xfacff000-0xfacff0ff]
[    0.193688] pci 0000:00:12.2: supports D1 D2
[    0.193690] pci 0000:00:12.2: PME# supported from D0 D1 D2 D3hot
[    0.193695] pci 0000:00:12.2: PME# disabled
[    0.193732] pci 0000:00:13.0: reg 10: [mem 0xfacfc000-0xfacfcfff]
[    0.193812] pci 0000:00:13.2: reg 10: [mem 0xfacfb800-0xfacfb8ff]
[    0.193875] pci 0000:00:13.2: supports D1 D2
[    0.193877] pci 0000:00:13.2: PME# supported from D0 D1 D2 D3hot
[    0.193882] pci 0000:00:13.2: PME# disabled
[    0.194020] pci 0000:00:14.2: reg 10: [mem 0xfacf4000-0xfacf7fff 64bit]
[    0.194072] pci 0000:00:14.2: PME# supported from D0 D3hot D3cold
[    0.194077] pci 0000:00:14.2: PME# disabled
[    0.194202] pci 0000:00:14.5: reg 10: [mem 0xfacfa000-0xfacfafff]
[    0.194485] pci 0000:01:00.0: reg 10: [mem 0xd0000000-0xdfffffff pref]
[    0.194492] pci 0000:01:00.0: reg 14: [io  0xc000-0xc0ff]
[    0.194498] pci 0000:01:00.0: reg 18: [mem 0xfadf0000-0xfadfffff]
[    0.194514] pci 0000:01:00.0: reg 30: [mem 0xfadc0000-0xfaddffff pref]
[    0.194534] pci 0000:01:00.0: supports D1 D2
[    0.194562] pci 0000:01:00.1: reg 10: [mem 0xfadec000-0xfadeffff]
[    0.194602] pci 0000:01:00.1: supports D1 D2
[    0.200016] pci 0000:00:02.0: PCI bridge to [bus 01-01]
[    0.200022] pci 0000:00:02.0:   bridge window [io  0xc000-0xcfff]
[    0.200026] pci 0000:00:02.0:   bridge window [mem 0xfad00000-0xfadfffff]
[    0.200032] pci 0000:00:02.0:   bridge window [mem 0xd0000000-0xdfffffff 64bit pref]
[    0.200095] pci 0000:02:00.0: reg 10: [io  0xd800-0xd8ff]
[    0.200113] pci 0000:02:00.0: reg 18: [mem 0xfaeff000-0xfaefffff 64bit]
[    0.200126] pci 0000:02:00.0: reg 20: [mem 0xf7ff0000-0xf7ffffff 64bit pref]
[    0.200135] pci 0000:02:00.0: reg 30: [mem 0xfaec0000-0xfaedffff pref]
[    0.200170] pci 0000:02:00.0: supports D1 D2
[    0.200173] pci 0000:02:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.200178] pci 0000:02:00.0: PME# disabled
[    0.208017] pci 0000:00:05.0: PCI bridge to [bus 02-02]
[    0.208022] pci 0000:00:05.0:   bridge window [io  0xd000-0xdfff]
[    0.208026] pci 0000:00:05.0:   bridge window [mem 0xfae00000-0xfaefffff]
[    0.208032] pci 0000:00:05.0:   bridge window [mem 0xf7f00000-0xf7ffffff 64bit pref]
[    0.208102] pci 0000:03:00.0: reg 10: [mem 0xfaff0000-0xfaffffff 64bit]
[    0.208161] pci 0000:03:00.0: supports D1
[    0.208164] pci 0000:03:00.0: PME# supported from D0 D1 D3hot
[    0.208169] pci 0000:03:00.0: PME# disabled
[    0.208192] pci 0000:03:00.0: disabling ASPM on pre-1.1 PCIe device.  You can enable it with 'pcie_aspm=force'
[    0.208201] pci 0000:00:06.0: PCI bridge to [bus 03-03]
[    0.208206] pci 0000:00:06.0:   bridge window [io  0xf000-0x0000] (disabled)
[    0.208210] pci 0000:00:06.0:   bridge window [mem 0xfaf00000-0xfaffffff]
[    0.208216] pci 0000:00:06.0:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    0.208253] pci 0000:00:07.0: PCI bridge to [bus 04-05]
[    0.208258] pci 0000:00:07.0:   bridge window [io  0xe000-0xefff]
[    0.208262] pci 0000:00:07.0:   bridge window [mem 0xfb000000-0xfbefffff]
[    0.208268] pci 0000:00:07.0:   bridge window [mem 0xf8000000-0xf9ffffff 64bit pref]
[    0.208319] pci 0000:06:01.0: reg 10: [mem 0xfbfff800-0xfbffffff]
[    0.208389] pci 0000:06:01.0: PME# supported from D0 D3hot D3cold
[    0.208395] pci 0000:06:01.0: PME# disabled
[    0.208437] pci 0000:06:01.1: reg 10: [mem 0xfbfff400-0xfbfff4ff]
[    0.208507] pci 0000:06:01.1: supports D1 D2
[    0.208509] pci 0000:06:01.1: PME# supported from D0 D1 D2 D3hot D3cold
[    0.208515] pci 0000:06:01.1: PME# disabled
[    0.208557] pci 0000:06:01.2: reg 10: [mem 0xfbfff000-0xfbfff0ff]
[    0.208626] pci 0000:06:01.2: supports D1 D2
[    0.208629] pci 0000:06:01.2: PME# supported from D0 D1 D2 D3hot D3cold
[    0.208634] pci 0000:06:01.2: PME# disabled
[    0.208676] pci 0000:06:01.3: reg 10: [mem 0xfbffec00-0xfbffecff]
[    0.208746] pci 0000:06:01.3: supports D1 D2
[    0.208748] pci 0000:06:01.3: PME# supported from D0 D1 D2 D3hot D3cold
[    0.208754] pci 0000:06:01.3: PME# disabled
[    0.208826] pci 0000:00:14.4: PCI bridge to [bus 06-06] (subtractive decode)
[    0.208831] pci 0000:00:14.4:   bridge window [io  0xf000-0x0000] (disabled)
[    0.208837] pci 0000:00:14.4:   bridge window [mem 0xfbf00000-0xfbffffff]
[    0.208842] pci 0000:00:14.4:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    0.208846] pci 0000:00:14.4:   bridge window [io  0x0000-0x0cf7] (subtractive decode)
[    0.208849] pci 0000:00:14.4:   bridge window [io  0x0d00-0xffff] (subtractive decode)
[    0.208852] pci 0000:00:14.4:   bridge window [mem 0x000a0000-0x000bffff] (subtractive decode)
[    0.208855] pci 0000:00:14.4:   bridge window [mem 0x000d0000-0x000dffff] (subtractive decode)
[    0.208858] pci 0000:00:14.4:   bridge window [mem 0xd0000000-0xdfffffff] (subtractive decode)
[    0.208861] pci 0000:00:14.4:   bridge window [mem 0xf0000000-0xfed44fff] (subtractive decode)
[    0.208882] pci_bus 0000:00: on NUMA node 0
[    0.208888] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.209182] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCE2._PRT]
[    0.209261] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCE5._PRT]
[    0.209333] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCE6._PRT]
[    0.209427] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0PC._PRT]
[    0.209521] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCE7._PRT]
[    0.217987] ACPI: PCI Interrupt Link [LNKA] (IRQs 4 7 10 11 12 14 15) *0, disabled.
[    0.218176] ACPI: PCI Interrupt Link [LNKB] (IRQs 4 7 10 11 12 14 15) *0, disabled.
[    0.218360] ACPI: PCI Interrupt Link [LNKC] (IRQs 4 7 10 11 12 14 15) *0, disabled.
[    0.218519] ACPI: PCI Interrupt Link [LNKD] (IRQs 4 7 10 11 12 14 15) *0, disabled.
[    0.218708] ACPI: PCI Interrupt Link [LNKE] (IRQs 4 7 10 11 12 14 15) *0, disabled.
[    0.218904] ACPI: PCI Interrupt Link [LNKF] (IRQs 4 7 10 11 12 14 15) *0, disabled.
[    0.219064] ACPI: PCI Interrupt Link [LNKG] (IRQs 10 11 12 14 15) *0, disabled.
[    0.219253] ACPI: PCI Interrupt Link [LNKH] (IRQs 4 7 10 11 12 14 15) *0, disabled.
[    0.219300] HEST: Table is not found!
[    0.219408] vgaarb: device added: PCI:0000:01:00.0,decodes=io+mem,owns=io+mem,locks=none
[    0.219414] vgaarb: loaded
[    0.219586] SCSI subsystem initialized
[    0.219685] libata version 3.00 loaded.
[    0.219747] usbcore: registered new interface driver usbfs
[    0.219760] usbcore: registered new interface driver hub
[    0.219786] usbcore: registered new device driver usb
[    0.219929] ACPI: WMI: Mapper loaded
[    0.219931] PCI: Using ACPI for IRQ routing
[    0.219960] PCI: pci_cache_line_size set to 64 bytes
[    0.220105] reserve RAM buffer: 000000000009fc00 - 000000000009ffff 
[    0.220109] reserve RAM buffer: 00000000cff80000 - 00000000cfffffff 
[    0.220209] NetLabel: Initializing
[    0.220212] NetLabel:  domain hash size = 128
[    0.220213] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.220229] NetLabel:  unlabeled traffic allowed by default
[    0.220305] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0
[    0.220311] hpet0: 4 comparators, 32-bit 14.318180 MHz counter
[    0.222338] Switching to clocksource hpet
[    0.229794] AppArmor: AppArmor Filesystem Enabled
[    0.229815] pnp: PnP ACPI init
[    0.229837] ACPI: bus type pnp registered
[    0.232949] pnp: PnP ACPI: found 13 devices
[    0.232951] ACPI: ACPI bus type pnp unregistered
[    0.232955] PnPBIOS: Disabled by ACPI PNP
[    0.232973] system 00:07: [mem 0xfec00000-0xfec00fff] could not be reserved
[    0.232977] system 00:07: [mem 0xfee00000-0xfee00fff] has been reserved
[    0.232983] system 00:08: [io  0x04d0-0x04d1] has been reserved
[    0.233051] system 00:08: [io  0x040b] has been reserved
[    0.233053] system 00:08: [io  0x04d6] has been reserved
[    0.233056] system 00:08: [io  0x0c00-0x0c01] has been reserved
[    0.233059] system 00:08: [io  0x0c14] has been reserved
[    0.233062] system 00:08: [io  0x0c50-0x0c51] has been reserved
[    0.233065] system 00:08: [io  0x0c52] has been reserved
[    0.233068] system 00:08: [io  0x0c6c] has been reserved
[    0.233071] system 00:08: [io  0x0c6f] has been reserved
[    0.233077] system 00:08: [io  0x0cd0-0x0cd1] has been reserved
[    0.233080] system 00:08: [io  0x0cd2-0x0cd3] has been reserved
[    0.233084] system 00:08: [io  0x0cd4-0x0cd5] has been reserved
[    0.233087] system 00:08: [io  0x0cd6-0x0cd7] has been reserved
[    0.233090] system 00:08: [io  0x0cd8-0x0cdf] has been reserved
[    0.233093] system 00:08: [io  0x0800-0x089f] has been reserved
[    0.233096] system 00:08: [io  0x0b00-0x0b0f] has been reserved
[    0.233099] system 00:08: [io  0x0b20-0x0b3f] has been reserved
[    0.233102] system 00:08: [io  0x0900-0x090f] has been reserved
[    0.233105] system 00:08: [io  0x0910-0x091f] has been reserved
[    0.233108] system 00:08: [io  0xfe00-0xfefe] has been reserved
[    0.233112] system 00:08: [mem 0xffb80000-0xffbfffff] has been reserved
[    0.233115] system 00:08: [mem 0xfec10000-0xfec1001f] has been reserved
[    0.233122] system 00:0b: [mem 0xe0000000-0xefffffff] has been reserved
[    0.233128] system 00:0c: [mem 0x00000000-0x0009ffff] could not be reserved
[    0.233131] system 00:0c: [mem 0x000c0000-0x000cffff] could not be reserved
[    0.233135] system 00:0c: [mem 0x000e0000-0x000fffff] could not be reserved
[    0.233138] system 00:0c: [mem 0x00100000-0xcfffffff] could not be reserved
[    0.233141] system 00:0c: [mem 0xfed45000-0xffffffff] could not be reserved
[    0.269615] pci 0000:00:02.0: PCI bridge to [bus 01-01]
[    0.269620] pci 0000:00:02.0:   bridge window [io  0xc000-0xcfff]
[    0.269625] pci 0000:00:02.0:   bridge window [mem 0xfad00000-0xfadfffff]
[    0.269629] pci 0000:00:02.0:   bridge window [mem 0xd0000000-0xdfffffff 64bit pref]
[    0.269635] pci 0000:00:05.0: PCI bridge to [bus 02-02]
[    0.269638] pci 0000:00:05.0:   bridge window [io  0xd000-0xdfff]
[    0.269643] pci 0000:00:05.0:   bridge window [mem 0xfae00000-0xfaefffff]
[    0.269647] pci 0000:00:05.0:   bridge window [mem 0xf7f00000-0xf7ffffff 64bit pref]
[    0.269653] pci 0000:00:06.0: PCI bridge to [bus 03-03]
[    0.269655] pci 0000:00:06.0:   bridge window [io  disabled]
[    0.269659] pci 0000:00:06.0:   bridge window [mem 0xfaf00000-0xfaffffff]
[    0.269663] pci 0000:00:06.0:   bridge window [mem pref disabled]
[    0.269668] pci 0000:00:07.0: PCI bridge to [bus 04-05]
[    0.269671] pci 0000:00:07.0:   bridge window [io  0xe000-0xefff]
[    0.269676] pci 0000:00:07.0:   bridge window [mem 0xfb000000-0xfbefffff]
[    0.269680] pci 0000:00:07.0:   bridge window [mem 0xf8000000-0xf9ffffff 64bit pref]
[    0.269686] pci 0000:00:14.4: PCI bridge to [bus 06-06]
[    0.269688] pci 0000:00:14.4:   bridge window [io  disabled]
[    0.269716] pci 0000:00:14.4:   bridge window [mem 0xfbf00000-0xfbffffff]
[    0.269721] pci 0000:00:14.4:   bridge window [mem pref disabled]
[    0.269737]   alloc irq_desc for 18 on node -1
[    0.269740]   alloc kstat_irqs on node -1
[    0.269746] pci 0000:00:02.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    0.269751] pci 0000:00:02.0: setting latency timer to 64
[    0.269759]   alloc irq_desc for 17 on node -1
[    0.269761]   alloc kstat_irqs on node -1
[    0.269765] pci 0000:00:05.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    0.269769] pci 0000:00:05.0: setting latency timer to 64
[    0.269777] pci 0000:00:06.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    0.269781] pci 0000:00:06.0: setting latency timer to 64
[    0.269789]   alloc irq_desc for 19 on node -1
[    0.269791]   alloc kstat_irqs on node -1
[    0.269794] pci 0000:00:07.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    0.269798] pci 0000:00:07.0: setting latency timer to 64
[    0.269808] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
[    0.269810] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff]
[    0.269813] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
[    0.269816] pci_bus 0000:00: resource 7 [mem 0x000d0000-0x000dffff]
[    0.269819] pci_bus 0000:00: resource 8 [mem 0xd0000000-0xdfffffff]
[    0.269822] pci_bus 0000:00: resource 9 [mem 0xf0000000-0xfed44fff]
[    0.269825] pci_bus 0000:01: resource 0 [io  0xc000-0xcfff]
[    0.269827] pci_bus 0000:01: resource 1 [mem 0xfad00000-0xfadfffff]
[    0.269830] pci_bus 0000:01: resource 2 [mem 0xd0000000-0xdfffffff 64bit pref]
[    0.269833] pci_bus 0000:02: resource 0 [io  0xd000-0xdfff]
[    0.269836] pci_bus 0000:02: resource 1 [mem 0xfae00000-0xfaefffff]
[    0.269839] pci_bus 0000:02: resource 2 [mem 0xf7f00000-0xf7ffffff 64bit pref]
[    0.269842] pci_bus 0000:03: resource 1 [mem 0xfaf00000-0xfaffffff]
[    0.269845] pci_bus 0000:04: resource 0 [io  0xe000-0xefff]
[    0.269848] pci_bus 0000:04: resource 1 [mem 0xfb000000-0xfbefffff]
[    0.269851] pci_bus 0000:04: resource 2 [mem 0xf8000000-0xf9ffffff 64bit pref]
[    0.269854] pci_bus 0000:06: resource 1 [mem 0xfbf00000-0xfbffffff]
[    0.269857] pci_bus 0000:06: resource 4 [io  0x0000-0x0cf7]
[    0.269859] pci_bus 0000:06: resource 5 [io  0x0d00-0xffff]
[    0.269862] pci_bus 0000:06: resource 6 [mem 0x000a0000-0x000bffff]
[    0.269865] pci_bus 0000:06: resource 7 [mem 0x000d0000-0x000dffff]
[    0.269868] pci_bus 0000:06: resource 8 [mem 0xd0000000-0xdfffffff]
[    0.269870] pci_bus 0000:06: resource 9 [mem 0xf0000000-0xfed44fff]
[    0.269912] NET: Registered protocol family 2
[    0.269979] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.270278] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.271033] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.271379] TCP: Hash tables configured (established 131072 bind 65536)
[    0.271381] TCP reno registered
[    0.271385] UDP hash table entries: 512 (order: 2, 16384 bytes)
[    0.271400] UDP-Lite hash table entries: 512 (order: 2, 16384 bytes)
[    0.271502] NET: Registered protocol family 1
[    0.993063] pci 0000:01:00.0: Boot video device
[    0.993087] PCI: CLS 64 bytes, default 64
[    0.993309] cpufreq-nforce2: No nForce2 chipset.
[    0.993341] Scanning for low memory corruption every 60 seconds
[    0.993452] audit: initializing netlink socket (disabled)
[    0.993464] type=2000 audit(1300142539.992:1): initialized
[    1.004563] highmem bounce pool size: 64 pages
[    1.004568] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    1.006092] VFS: Disk quotas dquot_6.5.2
[    1.006156] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    1.006762] fuse init (API version 7.14)
[    1.006852] msgmni has been set to 1650
[    1.159370] Freeing initrd memory: 10516k freed
[    1.170025] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    1.170030] io scheduler noop registered
[    1.170032] io scheduler deadline registered
[    1.170046] io scheduler cfq registered (default)
[    1.170182] pcieport 0000:00:02.0: setting latency timer to 64
[    1.170218]   alloc irq_desc for 40 on node -1
[    1.170221]   alloc kstat_irqs on node -1
[    1.170233] pcieport 0000:00:02.0: irq 40 for MSI/MSI-X
[    1.170309] pcieport 0000:00:05.0: setting latency timer to 64
[    1.170338]   alloc irq_desc for 41 on node -1
[    1.170340]   alloc kstat_irqs on node -1
[    1.170347] pcieport 0000:00:05.0: irq 41 for MSI/MSI-X
[    1.170417] pcieport 0000:00:06.0: setting latency timer to 64
[    1.170446]   alloc irq_desc for 42 on node -1
[    1.170448]   alloc kstat_irqs on node -1
[    1.170454] pcieport 0000:00:06.0: irq 42 for MSI/MSI-X
[    1.170522] pcieport 0000:00:07.0: setting latency timer to 64
[    1.170550]   alloc irq_desc for 43 on node -1
[    1.170552]   alloc kstat_irqs on node -1
[    1.170559] pcieport 0000:00:07.0: irq 43 for MSI/MSI-X
[    1.170667] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    1.170741] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    1.170990] ACPI: AC Adapter [AC0] (on-line)
[    1.171074] input: Lid Switch as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0D:00/input/input0
[    1.175838] ACPI: Lid Switch [LID]
[    1.175884] input: Sleep Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0E:00/input/input1
[    1.175929] ACPI: Sleep Button [SLPB]
[    1.175973] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input2
[    1.175977] ACPI: Power Button [PWRB]
[    1.176024] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input3
[    1.176027] ACPI: Power Button [PWRF]
[    1.176381] ACPI: acpi_idle registered with cpuidle
[    1.185161] thermal LNXTHERM:01: registered as thermal_zone0
[    1.185171] ACPI: Thermal Zone [TZ00] (76 C)
[    1.186421] thermal LNXTHERM:02: registered as thermal_zone1
[    1.186429] ACPI: Thermal Zone [TZ01] (66 C)
[    1.186517] ERST: Table is not found!
[    1.186737] isapnp: Scanning for PnP cards...
[    1.186833] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    1.188309] brd: module loaded
[    1.188827] loop: module loaded
[    1.189454] Fixed MDIO Bus: probed
[    1.189494] PPP generic driver version 2.4.2
[    1.189530] tun: Universal TUN/TAP device driver, 1.6
[    1.189533] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    1.189613] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    1.189675] ehci_hcd 0000:00:12.2: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    1.189697] ehci_hcd 0000:00:12.2: EHCI Host Controller
[    1.189731] ehci_hcd 0000:00:12.2: new USB bus registered, assigned bus number 1
[    1.189808] ehci_hcd 0000:00:12.2: applying AMD SB600/SB700 USB freeze workaround
[    1.189825] ehci_hcd 0000:00:12.2: debug port 1
[    1.189854] ehci_hcd 0000:00:12.2: irq 17, io mem 0xfacff000
[    1.199285] ACPI: Battery Slot [BAT0] (battery present)
[    1.201046] ehci_hcd 0000:00:12.2: USB 2.0 started, EHCI 1.00
[    1.201176] hub 1-0:1.0: USB hub found
[    1.201182] hub 1-0:1.0: 6 ports detected
[    1.201300] ehci_hcd 0000:00:13.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    1.201314] ehci_hcd 0000:00:13.2: EHCI Host Controller
[    1.201348] ehci_hcd 0000:00:13.2: new USB bus registered, assigned bus number 2
[    1.201375] ehci_hcd 0000:00:13.2: applying AMD SB600/SB700 USB freeze workaround
[    1.201391] ehci_hcd 0000:00:13.2: debug port 1
[    1.201414] ehci_hcd 0000:00:13.2: irq 19, io mem 0xfacfb800
[    1.213049] ehci_hcd 0000:00:13.2: USB 2.0 started, EHCI 1.00
[    1.213146] hub 2-0:1.0: USB hub found
[    1.213150] hub 2-0:1.0: 6 ports detected
[    1.213226] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    1.213274]   alloc irq_desc for 16 on node -1
[    1.213277]   alloc kstat_irqs on node -1
[    1.213284] ohci_hcd 0000:00:12.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.213295] ohci_hcd 0000:00:12.0: OHCI Host Controller
[    1.213329] ohci_hcd 0000:00:12.0: new USB bus registered, assigned bus number 3
[    1.213397] ohci_hcd 0000:00:12.0: irq 16, io mem 0xfacfe000
[    1.273149] hub 3-0:1.0: USB hub found
[    1.273190] hub 3-0:1.0: 3 ports detected
[    1.273255] ohci_hcd 0000:00:12.1: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.273268] ohci_hcd 0000:00:12.1: OHCI Host Controller
[    1.273301] ohci_hcd 0000:00:12.1: new USB bus registered, assigned bus number 4
[    1.273318] ohci_hcd 0000:00:12.1: irq 16, io mem 0xfacfd000
[    1.333138] hub 4-0:1.0: USB hub found
[    1.333145] hub 4-0:1.0: 3 ports detected
[    1.333207] ohci_hcd 0000:00:13.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    1.333218] ohci_hcd 0000:00:13.0: OHCI Host Controller
[    1.333250] ohci_hcd 0000:00:13.0: new USB bus registered, assigned bus number 5
[    1.333278] ohci_hcd 0000:00:13.0: irq 18, io mem 0xfacfc000
[    1.393154] hub 5-0:1.0: USB hub found
[    1.393174] hub 5-0:1.0: 3 ports detected
[    1.393238] ohci_hcd 0000:00:14.5: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    1.393249] ohci_hcd 0000:00:14.5: OHCI Host Controller
[    1.393290] ohci_hcd 0000:00:14.5: new USB bus registered, assigned bus number 6
[    1.393343] ohci_hcd 0000:00:14.5: irq 18, io mem 0xfacfa000
[    1.453130] hub 6-0:1.0: USB hub found
[    1.453170] hub 6-0:1.0: 2 ports detected
[    1.453236] uhci_hcd: USB Universal Host Controller Interface driver
[    1.453332] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f03:PS2M] at 0x60,0x64 irq 1,12
[    1.459441] i8042.c: Detected active multiplexing controller, rev 1.1.
[    1.463370] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.463376] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[    1.463403] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[    1.463428] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[    1.463450] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[    1.463553] mice: PS/2 mouse device common for all mice
[    1.463757] rtc_cmos 00:03: RTC can wake from S4
[    1.463796] rtc_cmos 00:03: rtc core: registered rtc_cmos as rtc0
[    1.463864] rtc0: alarms up to one month, y3k, 114 bytes nvram, hpet irqs
[    1.463967] device-mapper: uevent: version 1.0.3
[    1.464122] device-mapper: ioctl: 4.17.0-ioctl (2010-03-05) initialised: dm-devel@redhat.com
[    1.464226] device-mapper: multipath: version 1.1.1 loaded
[    1.464229] device-mapper: multipath round-robin: version 1.0.0 loaded
[    1.464385] EISA: Probing bus 0 at eisa.0
[    1.464388] EISA: Cannot allocate resource for mainboard
[    1.464391] Cannot allocate resource for EISA slot 1
[    1.464394] Cannot allocate resource for EISA slot 2
[    1.464396] Cannot allocate resource for EISA slot 3
[    1.464399] Cannot allocate resource for EISA slot 4
[    1.464401] Cannot allocate resource for EISA slot 5
[    1.464404] Cannot allocate resource for EISA slot 6
[    1.464406] Cannot allocate resource for EISA slot 7
[    1.464408] Cannot allocate resource for EISA slot 8
[    1.464410] EISA: Detected 0 cards.
[    1.464522] cpuidle: using governor ladder
[    1.464525] cpuidle: using governor menu
[    1.464881] TCP cubic registered
[    1.465069] NET: Registered protocol family 10
[    1.465484] lo: Disabled Privacy Extensions
[    1.465771] NET: Registered protocol family 17
[    1.465804] powernow-k8: Found 1 AMD Turion(tm) X2 Dual-Core Mobile RM-72 (2 cpu cores) (version 2.20.00)
[    1.465907] powernow-k8:    0 : pstate 0 (2100 MHz)
[    1.465910] powernow-k8:    1 : pstate 1 (1050 MHz)
[    1.465912] powernow-k8:    2 : pstate 2 (525 MHz)
[    1.479390] Using IPI No-Shortcut mode
[    1.479492] PM: Resume from disk failed.
[    1.479505] registered taskstats version 1
[    1.479928]   Magic number: 3:53:755
[    1.480065] rtc_cmos 00:03: setting system clock to 2011-03-14 22:42:21 UTC (1300142541)
[    1.480068] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.480071] EDD information not available.
[    1.502551] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input4
[    1.570893] isapnp: No Plug & Play device found
[    1.570944] Freeing unused kernel memory: 688k freed
[    1.571563] Write protecting the kernel text: 4936k
[    1.571603] Write protecting the kernel read-only data: 1980k
[    1.596279] udev[75]: starting version 163
[    1.625208] usb 1-5: new high speed USB device using ehci_hcd and address 3
[    1.677973] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    1.678006] r8169 0000:02:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    1.678050] r8169 0000:02:00.0: setting latency timer to 64
[    1.678090]   alloc irq_desc for 44 on node -1
[    1.678092]   alloc kstat_irqs on node -1
[    1.678107] r8169 0000:02:00.0: irq 44 for MSI/MSI-X
[    1.678626] r8169 0000:02:00.0: eth0: RTL8168c/8111c at 0xf8096000, 00:24:8c:81:ca:07, XID 1c4000c0 IRQ 44
[    1.729470] ahci 0000:00:11.0: version 3.0
[    1.729528]   alloc irq_desc for 22 on node -1
[    1.729531]   alloc kstat_irqs on node -1
[    1.729539] ahci 0000:00:11.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[    1.729714] ahci 0000:00:11.0: AHCI 0001.0100 32 slots 4 ports 3 Gbps 0xf impl SATA mode
[    1.729718] ahci 0000:00:11.0: flags: 64bit ncq sntf ilck led clo pmp pio slum part ccc 
[    1.759795] sdhci: Secure Digital Host Controller Interface driver
[    1.759799] sdhci: Copyright(c) Pierre Ossman
[    1.762675] scsi0 : ahci
[    1.773442] sdhci-pci 0000:06:01.1: SDHCI controller found [1180:0822] (rev 22)
[    1.773468]   alloc irq_desc for 21 on node -1
[    1.773471]   alloc kstat_irqs on node -1
[    1.773479] sdhci-pci 0000:06:01.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[    1.774642] sdhci-pci 0000:06:01.1: Will use DMA mode even though HW doesn't fully claim to support it.
[    1.775694] Registered led device: mmc0::
[    1.779144] scsi1 : ahci
[    1.781293] mmc0: SDHCI controller on PCI [0000:06:01.1] using DMA
[    1.781416]   alloc irq_desc for 20 on node -1
[    1.781421]   alloc kstat_irqs on node -1
[    1.781430] firewire_ohci 0000:06:01.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    1.782155] scsi2 : ahci
[    1.782284] scsi3 : ahci
[    1.782342] ata1: SATA max UDMA/133 abar m1024@0xfacff800 port 0xfacff900 irq 22
[    1.782347] ata2: SATA max UDMA/133 irq_stat 0x00000040, connection status changed irq 22
[    1.782352] ata3: SATA max UDMA/133 abar m1024@0xfacff800 port 0xfacffa00 irq 22
[    1.782356] ata4: SATA max UDMA/133 abar m1024@0xfacff800 port 0xfacffa80 irq 22
[    1.869072] firewire_ohci: Added fw-ohci device 0000:06:01.0, OHCI v1.0, 4 IR + 4 IT contexts, quirks 0x0
[    2.069066] usb 3-1: new full speed USB device using ohci_hcd and address 2
[    2.100087] ata3: SATA link down (SStatus 0 SControl 300)
[    2.100149] ata4: SATA link down (SStatus 0 SControl 300)
[    2.253448] Initializing USB Mass Storage driver...
[    2.254616] scsi7 : usb-storage 3-1:1.3
[    2.254960] usbcore: registered new interface driver usb-storage
[    2.254963] USB Mass Storage support registered.
[    2.272073] ata1: softreset failed (device not ready)
[    2.272078] ata1: applying SB600 PMP SRST workaround and retrying
[    2.361163] firewire_core: created device fw0: GUID 001e8c0001da404e, S400
[    2.444078] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    2.445889] ata1.00: ATA-8: ST9500325AS, 0001SDM1, max UDMA/133
[    2.445893] ata1.00: 976773168 sectors, multi 16: LBA48 NCQ (depth 31/32)
[    2.448007] ata1.00: configured for UDMA/133
[    2.448237] scsi 0:0:0:0: Direct-Access     ATA      ST9500325AS      0001 PQ: 0 ANSI: 5
[    2.448419] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    2.448516] sd 0:0:0:0: [sda] 976773168 512-byte logical blocks: (500 GB/465 GiB)
[    2.448645] sd 0:0:0:0: [sda] Write Protect is off
[    2.448649] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    2.448690] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.448898]  sda: sda1 sda2 sda3 < sda5 sda6 sda7 sda8 >
[    2.564782] sd 0:0:0:0: [sda] Attached SCSI disk
[    2.676067] ata2: softreset failed (device not ready)
[    2.676072] ata2: applying SB600 PMP SRST workaround and retrying
[    2.848077] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    2.849910] ata2.00: ATAPI: MATSHITADVD-RAM UJ870BJ, 1.02, max UDMA/33
[    2.852123] ata2.00: configured for UDMA/33
[    2.856287] scsi 1:0:0:0: CD-ROM            MATSHITA DVD-RAM UJ870BJ  1.02 PQ: 0 ANSI: 5
[    2.859953] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[    2.859957] Uniform CD-ROM driver Revision: 3.20
[    2.860083] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    2.860158] sr 1:0:0:0: Attached scsi generic sg1 type 5
[    3.259113] scsi 7:0:0:0: CD-ROM            HUAWEI   Mass Storage     2.31 PQ: 0 ANSI: 2
[    3.265094] scsi 7:0:0:1: Direct-Access     HUAWEI   SD Storage       2.31 PQ: 0 ANSI: 2
[    3.297090] sr1: scsi-1 drive
[    3.297240] sr 7:0:0:0: Attached scsi CD-ROM sr1
[    3.297316] sr 7:0:0:0: Attached scsi generic sg2 type 5
[    3.297514] sd 7:0:0:1: Attached scsi generic sg3 type 0
[    3.328099] sd 7:0:0:1: [sdb] Attached SCSI removable disk
[    3.937891] EXT4-fs (sda6): mounted filesystem with ordered data mode. Opts: (null)
[   28.304824] udev[370]: starting version 163
[   28.434371] Adding 7815584k swap on /dev/sda7.  Priority:-1 extents:1 across:7815584k 
[   28.626398] type=1400 audit(1300106568.642:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient3" pid=560 comm="apparmor_parser"
[   28.626698] type=1400 audit(1300106568.642:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=560 comm="apparmor_parser"
[   28.626869] type=1400 audit(1300106568.642:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=560 comm="apparmor_parser"
[   28.631857] type=1400 audit(1300106568.646:5): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient3" pid=567 comm="apparmor_parser"
[   28.632258] type=1400 audit(1300106568.650:6): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=567 comm="apparmor_parser"
[   28.632432] type=1400 audit(1300106568.650:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=567 comm="apparmor_parser"
[   29.087712] Linux video capture interface: v2.00
[   29.108754] uvcvideo: Found UVC 1.00 device CNF7129 (04f2:b071)
[   29.114427] usbcore: registered new interface driver usbserial
[   29.114453] USB Serial support registered for generic
[   29.123218] acpi device:05: registered as cooling_device2
[   29.123564] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A03:00/device:02/LNXVIDEO:00/input/input5
[   29.123704] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[   29.133398] input: CNF7129 as /devices/pci0000:00/0000:00:12.2/usb1/1-5/1-5:1.0/input/input6
[   29.133473] usbcore: registered new interface driver uvcvideo
[   29.133476] USB Video Class driver (v0.1.0)
[   29.133972] usbcore: registered new interface driver usbserial_generic
[   29.133975] usbserial: USB Serial Driver core
[   29.197729] lp: driver loaded but no devices found
[   29.296549] Linux agpgart interface v0.103
[   29.722457] USB Serial support registered for GSM modem (1-port)
[   29.723484] option 3-1:1.0: GSM modem (1-port) converter detected
[   29.723824] usb 3-1: GSM modem (1-port) converter now attached to ttyUSB0
[   29.723840] option 3-1:1.1: GSM modem (1-port) converter detected
[   29.726386] usb 3-1: GSM modem (1-port) converter now attached to ttyUSB1
[   29.726411] option 3-1:1.2: GSM modem (1-port) converter detected
[   29.726504] usb 3-1: GSM modem (1-port) converter now attached to ttyUSB2
[   29.726530] usbcore: registered new interface driver option
[   29.726533] option: v0.7.2:USB Driver for GSM modems
[   29.809594] ACPI: resource piix4_smbus [io  0x0b00-0x0b07] conflicts with ACPI region SMRG [??? 0x00000b00-0x00000b0f flags 0x47]
[   29.809599] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[   29.810487] cfg80211: Calling CRDA to update world regulatory domain
[   29.814232] asus_laptop: Asus Laptop Support version 0.42
[   29.817561] cfg80211: World regulatory domain updated:
[   29.817565]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   29.817569]     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   29.817572]     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   29.817575]     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   29.817578]     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   29.817581]     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   29.817846] asus_laptop:   N5051Tp model detected
[   29.846321] asus_laptop: Backlight controlled by ACPI video driver
[   29.846388] input: Asus Laptop extra buttons as /devices/platform/asus_laptop/input/input7
[   29.980684] r852 0000:06:01.3: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[   29.980827] r852: driver loaded succesfully
[   30.322121] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
[   30.322129] Disabling lock debugging due to kernel taint
[   30.475695] [fglrx] Maximum main memory to use for locked dma buffers: 3125 MBytes.
[   30.476115] [fglrx]   vendor: 1002 device: 9480 count: 1
[   30.476638] [fglrx] ioport: bar 1, base 0xc000, size: 0x100
[   30.476662] pci 0000:01:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[   30.476669] pci 0000:01:00.0: setting latency timer to 64
[   30.476890] [fglrx] Kernel PAT support is enabled
[   30.476916] [fglrx] module loaded - fglrx 8.78.30 [Sep 20 2010] with 1 minors
[   30.575517] Synaptics Touchpad, model: 1, fw: 7.2, id: 0x1c0b1, caps: 0xd04711/0xa00000/0x20000
[   30.618263] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio4/input/input8
[   30.952969] ath9k 0000:03:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[   30.952982] ath9k 0000:03:00.0: setting latency timer to 64
[   31.381610] ath: EEPROM regdomain: 0x60
[   31.381614] ath: EEPROM indicates we should expect a direct regpair map
[   31.381620] ath: Country alpha2 being used: 00
[   31.381623] ath: Regpair used: 0x60
[   31.672478] phy0: Selected rate control algorithm 'ath9k_rate_control'
[   31.673217] Registered led device: ath9k-phy0::radio
[   31.673240] Registered led device: ath9k-phy0::assoc
[   31.673259] Registered led device: ath9k-phy0::tx
[   31.673277] Registered led device: ath9k-phy0::rx
[   31.673285] phy0: Atheros AR9280 Rev:2 mem=0xf83e0000, irq=18
[   32.166543] HDA Intel 0000:00:14.2: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   32.286497] HDA Intel 0000:01:00.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[   32.286556]   alloc irq_desc for 45 on node -1
[   32.286559]   alloc kstat_irqs on node -1
[   32.286574] HDA Intel 0000:01:00.1: irq 45 for MSI/MSI-X
[   32.286602] HDA Intel 0000:01:00.1: setting latency timer to 64
[   32.430370] EXT4-fs (sda6): re-mounted. Opts: errors=remount-ro
[   32.580369] EXT4-fs (sda8): mounted filesystem with ordered data mode. Opts: (null)
[   36.659199] type=1400 audit(1300106576.674:8): apparmor="STATUS" operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" pid=1021 comm="apparmor_parser"
[   36.659609] type=1400 audit(1300106576.674:9): apparmor="STATUS" operation="profile_load" name="/usr/sbin/cupsd" pid=1021 comm="apparmor_parser"
[   36.713824] r8169 0000:02:00.0: eth0: link down
[   36.714053] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   36.720511] type=1400 audit(1300106576.734:10): apparmor="STATUS" operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" pid=1114 comm="apparmor_parser"
[   36.737775] type=1400 audit(1300106576.754:11): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince" pid=1117 comm="apparmor_parser"
[   36.741806] type=1400 audit(1300106576.758:12): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient3" pid=1115 comm="apparmor_parser"
[   36.742110] type=1400 audit(1300106576.758:13): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=1115 comm="apparmor_parser"
[   36.742283] type=1400 audit(1300106576.758:14): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=1115 comm="apparmor_parser"
[   36.743879] type=1400 audit(1300106576.758:15): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince-previewer" pid=1117 comm="apparmor_parser"
[   36.746593] type=1400 audit(1300106576.762:16): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince-thumbnailer" pid=1117 comm="apparmor_parser"
[   36.749885] type=1400 audit(1300106576.766:17): apparmor="STATUS" operation="profile_replace" name="/usr/lib/cups/backend/cups-pdf" pid=1121 comm="apparmor_parser"
[   36.774898] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   36.794895] ppdev: user-space parallel port driver

```I guess the interesting part is this : 
```

[    3.297514] sd 7:0:0:1: Attached scsi generic sg3 type 0
[    3.328099] sd 7:0:0:1: [sdb] Attached SCSI removable disk
[    3.937891] EXT4-fs (sda6): mounted filesystem with ordered data mode. Opts: (null)
[   28.304824] udev[370]: starting version 163
[   28.434371] Adding 7815584k swap on /dev/sda7.  Priority:-1 extents:1 across:7815584k 
[   28.626398] type=1400 audit(1300106568.642:2): apparmor="STATUS"  operation="profile_load" name="/sbin/dhclient3" pid=560  comm="apparmor_parser"

```At start-up, my pc is taking about 24 seconds to do...something. I am stuck here, any idea where I could investigate to find where that comes from ? how to increase the amount of logs ? Is there any other logs somewhere in this /var/log that could help me ?

Thanks for your help !

---

### Post by lithopsian on 2011-03-14
At startup your PC is taking about 24 seconds to .... boot :)  To see details, install the bootchart package, reboot, and post the picture that it produces in /var/log/bootchart.

You can also remove the "quiet" boot parameter to see more details at boot time.  Can be helpful if you're a very fast reader!

---

