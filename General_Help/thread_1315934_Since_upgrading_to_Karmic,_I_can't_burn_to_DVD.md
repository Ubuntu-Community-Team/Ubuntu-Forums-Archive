---
title: "Since upgrading to Karmic, I can't burn to DVD"
date: 2009-11-05
forum: General Help
---

### Post by pbeesley on 2009-11-05
help since the installation of Karmic I can't burn DVD's at all. I can read fine but can't write :(

I've tried running the app as root and also that i'm in the cdrom group.


PLEASE HELP :(

---

### Post by StoneCrow on 2009-11-05
Did you do a dual boot configuration or a fresh linux install?

---

### Post by pbeesley on 2009-11-05
this was a fresh install but I have a windows partition, before karmic I have Jaunty and DVD / CD buring worked fine so i know the hardware is all good

---

### Post by kestrel1 on 2009-11-05
What application are you trying to use to burn your disk's? I presume it is brasero?
Try installing K3B: ```
sudo apt-get install k3b
```
& see if that works for you.

---

### Post by orasis on 2009-11-05
The first thing that you should do is to make sure everything is being detected properly with a dmesg sent to a text file to take a look at... 

@ sudo dmesg > whatevername.txt 

It may be detected as a RW device and then you simple have to remove the device and have it detected, yet again. 

Second you might want to start your burning app from console and look at the output, are you seeing any daemon errors? If so what? 

In fact for others to help you I believe that this would be the best option start your app from console and save the output and paste it here.

---

### Post by pbeesley on 2009-11-05
tried brasero, gnomebaker and k3b all no dice :(

---

### Post by pbeesley on 2009-11-05
> **orasis said:**
> 
@ sudo dmesg > whatevername.txt 


Hope this makes sense to someone :S

```
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.31-14-generic (buildd@rothera) (gcc version 4.4.1 (Ubuntu 4.4.1-4ubuntu8) ) #48-Ubuntu SMP Fri Oct 16 14:04:26 UTC 2009 (Ubuntu 2.6.31-14.48-generic)
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
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e6000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 00000000bbfb0000 (usable)
[    0.000000]  BIOS-e820: 00000000bbfb0000 - 00000000bbfc0000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000bbfc0000 - 00000000bbff0000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000bbff0000 - 00000000bc000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000ff780000 - 0000000100000000 (reserved)
[    0.000000] DMI 2.3 present.
[    0.000000] AMI BIOS detected: BIOS may corrupt low RAM, working around it.
[    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
[    0.000000] last_pfn = 0xbbfb0 max_arch_pfn = 0x100000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-DFFFF uncachable
[    0.000000]   E0000-EFFFF write-through
[    0.000000]   F0000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000 mask F80000000 write-back
[    0.000000]   1 base 080000000 mask FE0000000 write-back
[    0.000000]   2 base 0A0000000 mask FF0000000 write-back
[    0.000000]   3 base 0B0000000 mask FF8000000 write-back
[    0.000000]   4 base 0B8000000 mask FFC000000 write-back
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] Scanning 0 areas for low memory corruption
[    0.000000] modified physical RAM map:
[    0.000000]  modified: 0000000000000000 - 0000000000010000 (reserved)
[    0.000000]  modified: 0000000000010000 - 000000000009fc00 (usable)
[    0.000000]  modified: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  modified: 00000000000e6000 - 0000000000100000 (reserved)
[    0.000000]  modified: 0000000000100000 - 00000000bbfb0000 (usable)
[    0.000000]  modified: 00000000bbfb0000 - 00000000bbfc0000 (ACPI data)
[    0.000000]  modified: 00000000bbfc0000 - 00000000bbff0000 (ACPI NVS)
[    0.000000]  modified: 00000000bbff0000 - 00000000bc000000 (reserved)
[    0.000000]  modified: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  modified: 00000000ff780000 - 0000000100000000 (reserved)
[    0.000000] initial memory mapped : 0 - 00c00000
[    0.000000] init_memory_mapping: 0000000000000000-00000000377fe000
[    0.000000] Using x86 segment limits to approximate NX protection
[    0.000000]  0000000000 - 0000400000 page 4k
[    0.000000]  0000400000 - 0037400000 page 2M
[    0.000000]  0037400000 - 00377fe000 page 4k
[    0.000000] kernel direct mapping tables up to 377fe000 @ 10000-15000
[    0.000000] RAMDISK: 378a4000 - 37fef247
[    0.000000] Allocated new RAMDISK: 008ad000 - 00ff8247
[    0.000000] Move RAMDISK from 00000000378a4000 - 0000000037fef246 to 008ad000 - 00ff8246
[    0.000000] ACPI: RSDP 000f7ca0 00014 (v00 ACPIAM)
[    0.000000] ACPI: RSDT bbfb0000 00034 (v01 A M I  OEMRSDT  06000616 MSFT 00000097)
[    0.000000] ACPI: FACP bbfb0200 00084 (v02 A M I  OEMFACP  06000616 MSFT 00000097)
[    0.000000] ACPI: DSDT bbfb0450 03CD7 (v01  75D8P 75D8P004 00000004 INTL 02002026)
[    0.000000] ACPI: FACS bbfc0000 00040
[    0.000000] ACPI: APIC bbfb0390 00078 (v01 A M I  OEMAPIC  06000616 MSFT 00000097)
[    0.000000] ACPI: MCFG bbfb0410 0003C (v01 A M I  OEMMCFG  06000616 MSFT 00000097)
[    0.000000] ACPI: OEMB bbfc0040 00046 (v01 A M I  AMI_OEM  06000616 MSFT 00000097)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] 2119MB HIGHMEM available.
[    0.000000] 887MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 377fe000
[    0.000000]   low ram: 0 - 377fe000
[    0.000000]   node 0 low ram: 00000000 - 377fe000
[    0.000000]   node 0 bootmap 00011000 - 00017f00
[    0.000000] (9 early reservations) ==> bootmem [0000000000 - 00377fe000]
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
[    0.000000]   #1 [0000001000 - 0000002000]    EX TRAMPOLINE ==> [0000001000 - 0000002000]
[    0.000000]   #2 [0000006000 - 0000007000]       TRAMPOLINE ==> [0000006000 - 0000007000]
[    0.000000]   #3 [0000100000 - 00008a80a0]    TEXT DATA BSS ==> [0000100000 - 00008a80a0]
[    0.000000]   #4 [000009fc00 - 0000100000]    BIOS reserved ==> [000009fc00 - 0000100000]
[    0.000000]   #5 [00008a9000 - 00008ac0a1]              BRK ==> [00008a9000 - 00008ac0a1]
[    0.000000]   #6 [0000010000 - 0000011000]          PGTABLE ==> [0000010000 - 0000011000]
[    0.000000]   #7 [00008ad000 - 0000ff8247]      NEW RAMDISK ==> [00008ad000 - 0000ff8247]
[    0.000000]   #8 [0000011000 - 0000018000]          BOOTMAP ==> [0000011000 - 0000018000]
[    0.000000] found SMP MP-table at [c00ff780] ff780
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000010 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x000377fe
[    0.000000]   HighMem  0x000377fe -> 0x000bbfb0
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[2] active PFN ranges
[    0.000000]     0: 0x00000010 -> 0x0000009f
[    0.000000]     0: 0x00000100 -> 0x000bbfb0
[    0.000000] On node 0 totalpages: 769855
[    0.000000] free_area_init_node: node 0, pgdat c0784900, node_mem_map c1000200
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3951 pages, LIFO batch:0
[    0.000000]   Normal zone: 1744 pages used for memmap
[    0.000000]   Normal zone: 221486 pages, LIFO batch:31
[    0.000000]   HighMem zone: 4240 pages used for memmap
[    0.000000]   HighMem zone: 538402 pages, LIFO batch:31
[    0.000000] Using APIC driver default
[    0.000000] ACPI: PM-Timer IO Port: 0x808
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x81] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x82] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x83] disabled)
[    0.000000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 1, version 3, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfecc0000] gsi_base[24])
[    0.000000] IOAPIC[1]: apic_id 2, version 3, address 0xfecc0000, GSI 24-47
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 low level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 2 I/O APICs
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] SMP: Allowing 4 CPUs, 3 hotplug CPUs
[    0.000000] nr_irqs_gsi: 48
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e6000
[    0.000000] PM: Registered nosave memory: 00000000000e6000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at bc000000 (gap: bc000000:42e00000)
[    0.000000] NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:4 nr_node_ids:1
[    0.000000] PERCPU: Embedded 14 pages at c2790000, static data 35612 bytes
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 763839
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.31-14-generic root=UUID=5715cebf-c816-45f3-8c8a-a364637ee418 ro quiet splash
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] allocated 15399040 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] Initializing HighMem for node 0 (000377fe:000bbfb0)
[    0.000000] Memory: 3022932k/3079872k available (4565k kernel code, 55536k reserved, 2143k data, 540k init, 2170568k highmem)
[    0.000000] virtual kernel memory layout:
[    0.000000]     fixmap  : 0xfff1d000 - 0xfffff000   ( 904 kB)
[    0.000000]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[    0.000000]     vmalloc : 0xf7ffe000 - 0xff7fe000   ( 120 MB)
[    0.000000]     lowmem  : 0xc0000000 - 0xf77fe000   ( 887 MB)
[    0.000000]       .init : 0xc078e000 - 0xc0815000   ( 540 kB)
[    0.000000]       .data : 0xc0575554 - 0xc078d308   (2143 kB)
[    0.000000]       .text : 0xc0100000 - 0xc0575554   (4565 kB)
[    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.000000] SLUB: Genslabs=13, HWalign=128, Order=0-3, MinObjects=0, CPUs=4, Nodes=1
[    0.000000] NR_IRQS:2304 nr_irqs:848
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 3149.770 MHz processor.
[    0.002858] Console: colour VGA+ 80x25
[    0.002863] console [tty0] enabled
[    0.004012] Calibrating delay loop (skipped), value calculated using timer frequency.. 6299.54 BogoMIPS (lpj=12599080)
[    0.004034] Security Framework initialized
[    0.004059] AppArmor: AppArmor initialized
[    0.004069] Mount-cache hash table entries: 512
[    0.004234] Initializing cgroup subsys ns
[    0.004242] Initializing cgroup subsys cpuacct
[    0.004247] Initializing cgroup subsys memory
[    0.004255] Initializing cgroup subsys freezer
[    0.004258] Initializing cgroup subsys net_cls
[    0.004281] CPU: Trace cache: 12K uops, L1 D cache: 16K
[    0.004285] CPU: L2 cache: 256K
[    0.004288] CPU: Hyper-Threading is disabled
[    0.004293] mce: CPU supports 4 MCE banks
[    0.004307] CPU0: Thermal monitoring enabled (TM2)
[    0.004313] using mwait in idle threads.
[    0.004321] Performance Counters: no PMU driver, software counters only.
[    0.004329] Checking 'hlt' instruction... OK.
[    0.021028] SMP alternatives: switching to UP code
[    0.031423] ACPI: Core revision 20090521
[    0.042308] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.082002] CPU0: Intel(R) Celeron(R) CPU 2.80GHz stepping 01
[    0.084001] Brought up 1 CPUs
[    0.084001] Total of 1 processors activated (6299.54 BogoMIPS).
[    0.084001] CPU0 attaching NULL sched-domain.
[    0.084001] Booting paravirtualized kernel on bare hardware
[    0.084001] regulator: core version 0.5
[    0.084001] Time: 17:47:44  Date: 11/05/09
[    0.084001] NET: Registered protocol family 16
[    0.084001] EISA bus registered
[    0.084001] ACPI: bus type pci registered
[    0.084001] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 255
[    0.084001] PCI: Not using MMCONFIG.
[    0.084001] PCI: PCI BIOS revision 3.00 entry at 0xf0031, last bus=2
[    0.084001] PCI: Using configuration type 1 for base access
[    0.084001] bio: create slab <bio-0> at 0
[    0.084001] ACPI: EC: Look up EC in DSDT
[    0.091267] ACPI: Interpreter enabled
[    0.091277] ACPI: (supports S0 S1 S3 S4 S5)
[    0.091309] ACPI: Using IOAPIC for interrupt routing
[    0.091381] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 255
[    0.096760] PCI: MCFG area at e0000000 reserved in ACPI motherboard resources
[    0.096765] PCI: Using MMCONFIG for extended config space
[    0.104933] ACPI Warning: Incorrect checksum in table [OEMB] - 70, should be 62 20090521 tbutils-246
[    0.105055] ACPI: No dock devices found.
[    0.105236] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.105313] pci 0000:00:00.0: reg 10 32bit mmio: [0xf8000000-0xfbffffff]
[    0.105782] pci 0000:00:02.0: PME# supported from D0 D3hot D3cold
[    0.105787] pci 0000:00:02.0: PME# disabled
[    0.105844] pci 0000:00:0a.0: reg 10 32bit mmio: [0xf7ff0000-0xf7ff7fff]
[    0.105932] pci 0000:00:0b.0: reg 10 32bit mmio: [0xf7fff000-0xf7fff7ff]
[    0.105941] pci 0000:00:0b.0: reg 14 io port: [0xc880-0xc8ff]
[    0.106030] pci 0000:00:0f.0: reg 10 io port: [0xec00-0xec07]
[    0.106038] pci 0000:00:0f.0: reg 14 io port: [0xe880-0xe883]
[    0.106045] pci 0000:00:0f.0: reg 18 io port: [0xe800-0xe807]
[    0.106053] pci 0000:00:0f.0: reg 1c io port: [0xe480-0xe483]
[    0.106061] pci 0000:00:0f.0: reg 20 io port: [0xe400-0xe40f]
[    0.106068] pci 0000:00:0f.0: reg 24 io port: [0xe000-0xe0ff]
[    0.106153] pci 0000:00:0f.1: reg 20 io port: [0xfc00-0xfc0f]
[    0.106251] pci 0000:00:10.0: reg 20 io port: [0xdc00-0xdc1f]
[    0.106282] pci 0000:00:10.0: supports D1 D2
[    0.106285] pci 0000:00:10.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.106290] pci 0000:00:10.0: PME# disabled
[    0.106352] pci 0000:00:10.1: reg 20 io port: [0xd080-0xd09f]
[    0.106383] pci 0000:00:10.1: supports D1 D2
[    0.106386] pci 0000:00:10.1: PME# supported from D0 D1 D2 D3hot D3cold
[    0.106390] pci 0000:00:10.1: PME# disabled
[    0.106449] pci 0000:00:10.2: reg 20 io port: [0xd000-0xd01f]
[    0.106481] pci 0000:00:10.2: supports D1 D2
[    0.106484] pci 0000:00:10.2: PME# supported from D0 D1 D2 D3hot D3cold
[    0.106489] pci 0000:00:10.2: PME# disabled
[    0.106546] pci 0000:00:10.3: reg 20 io port: [0xcc00-0xcc1f]
[    0.106577] pci 0000:00:10.3: supports D1 D2
[    0.106580] pci 0000:00:10.3: PME# supported from D0 D1 D2 D3hot D3cold
[    0.106584] pci 0000:00:10.3: PME# disabled
[    0.106622] pci 0000:00:10.4: reg 10 32bit mmio: [0xf7fff800-0xf7fff8ff]
[    0.106672] pci 0000:00:10.4: supports D1 D2
[    0.106675] pci 0000:00:10.4: PME# supported from D0 D1 D2 D3hot D3cold
[    0.106679] pci 0000:00:10.4: PME# disabled
[    0.106755] HPET not enabled in BIOS. You might try hpet=force boot option
[    0.106821] pci 0000:00:11.5: reg 10 io port: [0xd400-0xd4ff]
[    0.106874] pci 0000:00:11.5: supports D1 D2
[    0.106916] pci 0000:00:12.0: reg 10 io port: [0xd800-0xd8ff]
[    0.106924] pci 0000:00:12.0: reg 14 32bit mmio: [0xf7fffc00-0xf7fffcff]
[    0.106971] pci 0000:00:12.0: supports D1 D2
[    0.106973] pci 0000:00:12.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.106978] pci 0000:00:12.0: PME# disabled
[    0.107103] pci 0000:02:00.0: reg 10 32bit mmio: [0xf6000000-0xf6ffffff]
[    0.107116] pci 0000:02:00.0: reg 14 64bit mmio: [0xc0000000-0xcfffffff]
[    0.107129] pci 0000:02:00.0: reg 1c 64bit mmio: [0xf5000000-0xf5ffffff]
[    0.107137] pci 0000:02:00.0: reg 24 io port: [0xbc00-0xbc7f]
[    0.107145] pci 0000:02:00.0: reg 30 32bit mmio: [0xf7ee0000-0xf7efffff]
[    0.107237] pci 0000:00:02.0: bridge io port: [0xb000-0xbfff]
[    0.107243] pci 0000:00:02.0: bridge 32bit mmio: [0xf3e00000-0xf7efffff]
[    0.107248] pci 0000:00:02.0: bridge 32bit mmio pref: [0xbff00000-0xdfefffff]
[    0.107263] pci_bus 0000:00: on NUMA node 0
[    0.107272] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.107556] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.NBPG._PRT]
[    0.120736] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 *5 6 7 10 11 12 14 15)
[    0.120876] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 10 *11 12 14 15)
[    0.121008] ACPI: PCI Interrupt Link [LNKC] (IRQs *3 4 5 6 7 10 11 12 14 15)
[    0.121141] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 *5 6 7 10 11 12 14 15)
[    0.121271] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[    0.121403] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[    0.121535] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[    0.121666] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 *10 11 12 14 15)
[    0.121924] SCSI subsystem initialized
[    0.122022] libata version 3.00 loaded.
[    0.122156] usbcore: registered new interface driver usbfs
[    0.122184] usbcore: registered new interface driver hub
[    0.122230] usbcore: registered new device driver usb
[    0.122446] ACPI: WMI: Mapper loaded
[    0.122449] PCI: Using ACPI for IRQ routing
[    0.122673] Bluetooth: Core ver 2.15
[    0.122742] NET: Registered protocol family 31
[    0.122745] Bluetooth: HCI device and connection manager initialized
[    0.122749] Bluetooth: HCI socket layer initialized
[    0.122751] NetLabel: Initializing
[    0.122753] NetLabel:  domain hash size = 128
[    0.122755] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.122772] NetLabel:  unlabeled traffic allowed by default
[    0.124621] pnp: PnP ACPI init
[    0.124650] ACPI: bus type pnp registered
[    0.130154] pnp: PnP ACPI: found 14 devices
[    0.130160] ACPI: ACPI bus type pnp unregistered
[    0.130166] PnPBIOS: Disabled by ACPI PNP
[    0.130187] system 00:08: ioport range 0x295-0x296 has been reserved
[    0.130191] system 00:08: ioport range 0x3e0-0x3e7 has been reserved
[    0.130194] system 00:08: ioport range 0x4d0-0x4d1 has been reserved
[    0.130197] system 00:08: ioport range 0x800-0x87f has been reserved
[    0.130200] system 00:08: ioport range 0x400-0x41f has been reserved
[    0.130210] system 00:09: iomem range 0xfec00000-0xfec00fff could not be reserved
[    0.130214] system 00:09: iomem range 0xfee00000-0xfee00fff has been reserved
[    0.130222] system 00:0c: iomem range 0xe0000000-0xefffffff has been reserved
[    0.130229] system 00:0d: iomem range 0x0-0x9ffff could not be reserved
[    0.130233] system 00:0d: iomem range 0xc0000-0xcffff could not be reserved
[    0.130236] system 00:0d: iomem range 0xe0000-0xfffff could not be reserved
[    0.130239] system 00:0d: iomem range 0x100000-0xbbffffff could not be reserved
[    0.130243] system 00:0d: iomem range 0xfff80000-0xffffffff has been reserved
[    0.164957] AppArmor: AppArmor Filesystem Enabled
[    0.164995] pci 0000:00:01.0: PCI bridge, secondary bus 0000:01
[    0.164998] pci 0000:00:01.0:   IO window: disabled
[    0.165004] pci 0000:00:01.0:   MEM window: disabled
[    0.165008] pci 0000:00:01.0:   PREFETCH window: disabled
[    0.165013] pci 0000:00:02.0: PCI bridge, secondary bus 0000:02
[    0.165017] pci 0000:00:02.0:   IO window: 0xb000-0xbfff
[    0.165023] pci 0000:00:02.0:   MEM window: 0xf3e00000-0xf7efffff
[    0.165029] pci 0000:00:02.0:   PREFETCH window: 0xbff00000-0xdfefffff
[    0.165047] pci 0000:00:01.0: setting latency timer to 64
[    0.165060]   alloc irq_desc for 27 on node -1
[    0.165063]   alloc kstat_irqs on node -1
[    0.165071] pci 0000:00:02.0: PCI INT A -> GSI 27 (level, low) -> IRQ 27
[    0.165077] pci 0000:00:02.0: setting latency timer to 64
[    0.165083] pci_bus 0000:00: resource 0 io:  [0x00-0xffff]
[    0.165086] pci_bus 0000:00: resource 1 mem: [0x000000-0xffffffff]
[    0.165089] pci_bus 0000:02: resource 0 io:  [0xb000-0xbfff]
[    0.165092] pci_bus 0000:02: resource 1 mem: [0xf3e00000-0xf7efffff]
[    0.165095] pci_bus 0000:02: resource 2 pref mem [0xbff00000-0xdfefffff]
[    0.165143] NET: Registered protocol family 2
[    0.165266] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.165658] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.166309] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.166649] TCP: Hash tables configured (established 131072 bind 65536)
[    0.166654] TCP reno registered
[    0.166811] NET: Registered protocol family 1
[    0.166898] Trying to unpack rootfs image as initramfs...
[    0.399659] Freeing initrd memory: 7468k freed
[    0.404996] cpufreq-nforce2: No nForce2 chipset.
[    0.405041] Scanning for low memory corruption every 60 seconds
[    0.405171] audit: initializing netlink socket (disabled)
[    0.405192] type=2000 audit(1257443263.404:1): initialized
[    0.413916] highmem bounce pool size: 64 pages
[    0.413925] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    0.415431] VFS: Disk quotas dquot_6.5.2
[    0.415527] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.416262] fuse init (API version 7.12)
[    0.416383] msgmni has been set to 1681
[    0.416700] alg: No test for stdrng (krng)
[    0.416725] io scheduler noop registered
[    0.416728] io scheduler anticipatory registered
[    0.416730] io scheduler deadline registered
[    0.416813] io scheduler cfq registered (default)
[    0.416836] pci 0000:00:01.0: disabling DAC on VIA PCI bridge
[    0.416918] pci 0000:00:11.0: Bypassing VIA 8237 APIC De-Assert Message
[    0.416941] pci 0000:02:00.0: Boot video device
[    0.417117]   alloc irq_desc for 48 on node -1
[    0.417120]   alloc kstat_irqs on node -1
[    0.417136] pcieport-driver 0000:00:02.0: irq 48 for MSI/MSI-X
[    0.417147] pcieport-driver 0000:00:02.0: setting latency timer to 64
[    0.417294] aer 0000:00:02.0:pcie02: AER service couldn't init device: no _OSC support
[    0.417308] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.417378] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.417541] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input0
[    0.417546] ACPI: Power Button [PWRF]
[    0.417611] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1
[    0.417614] ACPI: Power Button [PWRB]
[    0.418131] ACPI Error (psparse-0537): Method parse/execution failed [\_PR_.CPU1._PDC] (Node f700e180), AE_INVALID_TABLE_LENGTH
[    0.418213] processor LNXCPU:00: registered as cooling_device0
[    0.421794] isapnp: Scanning for PnP cards...
[    0.668076] Switched to high resolution mode on CPU 0
[    0.775865] isapnp: No Plug & Play device found
[    0.777245] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    0.777367] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.777854] 00:0b: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.779052] brd: module loaded
[    0.779599] loop: module loaded
[    0.779726] input: Macintosh mouse button emulation as /devices/virtual/input/input2
[    0.780425] pata_via 0000:00:0f.1: version 0.3.4
[    0.780450]   alloc irq_desc for 20 on node -1
[    0.780452]   alloc kstat_irqs on node -1
[    0.780461] pata_via 0000:00:0f.1: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    0.780666] scsi0 : pata_via
[    0.780811] scsi1 : pata_via
[    0.783285] ata1: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xfc00 irq 14
[    0.783289] ata2: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xfc08 irq 15
[    0.783937] Fixed MDIO Bus: probed
[    0.783986] PPP generic driver version 2.4.2
[    0.784162] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.784206]   alloc irq_desc for 21 on node -1
[    0.784210]   alloc kstat_irqs on node -1
[    0.784218] ehci_hcd 0000:00:10.4: PCI INT C -> GSI 21 (level, low) -> IRQ 21
[    0.784240] ehci_hcd 0000:00:10.4: EHCI Host Controller
[    0.784336] ehci_hcd 0000:00:10.4: new USB bus registered, assigned bus number 1
[    0.784407] ehci_hcd 0000:00:10.4: irq 21, io mem 0xf7fff800
[    0.796015] ehci_hcd 0000:00:10.4: USB 2.0 started, EHCI 1.00
[    0.796143] usb usb1: configuration #1 chosen from 1 choice
[    0.796184] hub 1-0:1.0: USB hub found
[    0.796195] hub 1-0:1.0: 8 ports detected
[    0.796284] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.796315] uhci_hcd: USB Universal Host Controller Interface driver
[    0.796375] uhci_hcd 0000:00:10.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[    0.796387] uhci_hcd 0000:00:10.0: UHCI Host Controller
[    0.796452] uhci_hcd 0000:00:10.0: new USB bus registered, assigned bus number 2
[    0.796481] uhci_hcd 0000:00:10.0: irq 21, io base 0x0000dc00
[    0.796596] usb usb2: configuration #1 chosen from 1 choice
[    0.796635] hub 2-0:1.0: USB hub found
[    0.796645] hub 2-0:1.0: 2 ports detected
[    0.796713] uhci_hcd 0000:00:10.1: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[    0.796723] uhci_hcd 0000:00:10.1: UHCI Host Controller
[    0.796789] uhci_hcd 0000:00:10.1: new USB bus registered, assigned bus number 3
[    0.796818] uhci_hcd 0000:00:10.1: irq 21, io base 0x0000d080
[    0.796932] usb usb3: configuration #1 chosen from 1 choice
[    0.796969] hub 3-0:1.0: USB hub found
[    0.796981] hub 3-0:1.0: 2 ports detected
[    0.797055] uhci_hcd 0000:00:10.2: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[    0.797066] uhci_hcd 0000:00:10.2: UHCI Host Controller
[    0.797128] uhci_hcd 0000:00:10.2: new USB bus registered, assigned bus number 4
[    0.797156] uhci_hcd 0000:00:10.2: irq 21, io base 0x0000d000
[    0.797258] usb usb4: configuration #1 chosen from 1 choice
[    0.797299] hub 4-0:1.0: USB hub found
[    0.797310] hub 4-0:1.0: 2 ports detected
[    0.797383] uhci_hcd 0000:00:10.3: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[    0.797393] uhci_hcd 0000:00:10.3: UHCI Host Controller
[    0.797459] uhci_hcd 0000:00:10.3: new USB bus registered, assigned bus number 5
[    0.797488] uhci_hcd 0000:00:10.3: irq 21, io base 0x0000cc00
[    0.797590] usb usb5: configuration #1 chosen from 1 choice
[    0.797624] hub 5-0:1.0: USB hub found
[    0.797635] hub 5-0:1.0: 2 ports detected
[    0.797765] PNP: PS/2 Controller [PNP0303:PS2K] at 0x60,0x64 irq 1
[    0.797769] PNP: PS/2 appears to have AUX port disabled, if this is incorrect please boot with i8042.nopnp
[    0.797907] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.798008] mice: PS/2 mouse device common for all mice
[    0.798119] rtc_cmos 00:02: RTC can wake from S4
[    0.798170] rtc_cmos 00:02: rtc core: registered rtc_cmos as rtc0
[    0.798224] rtc0: alarms up to one year, y3k, 114 bytes nvram
[    0.798371] device-mapper: uevent: version 1.0.3
[    0.798542] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: dm-devel@redhat.com
[    0.798682] device-mapper: multipath: version 1.1.0 loaded
[    0.798687] device-mapper: multipath round-robin: version 1.0.0 loaded
[    0.798899] EISA: Probing bus 0 at eisa.0
[    0.798940] EISA: Detected 0 cards.
[    0.799020] cpuidle: using governor ladder
[    0.799025] cpuidle: using governor menu
[    0.799637] TCP cubic registered
[    0.799818] NET: Registered protocol family 10
[    0.800406] lo: Disabled Privacy Extensions
[    0.800768] NET: Registered protocol family 17
[    0.800806] Bluetooth: L2CAP ver 2.13
[    0.800808] Bluetooth: L2CAP socket layer initialized
[    0.800811] Bluetooth: SCO (Voice Link) ver 0.6
[    0.800813] Bluetooth: SCO socket layer initialized
[    0.800883] Bluetooth: RFCOMM TTY layer initialized
[    0.800888] Bluetooth: RFCOMM socket layer initialized
[    0.800890] Bluetooth: RFCOMM ver 1.11
[    0.800937] Using IPI No-Shortcut mode
[    0.801048] PM: Resume from disk failed.
[    0.801071] registered taskstats version 1
[    0.801209]   Magic number: 1:445:794
[    0.801306] rtc_cmos 00:02: setting system clock to 2009-11-05 17:47:44 UTC (1257443264)
[    0.801311] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.801313] EDD information not available.
[    0.823082] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input3
[    0.952541] ata1.01: ATA-7: Maxtor 6Y080L0, YAR41BW0, max UDMA/133
[    0.952545] ata1.01: 160086528 sectors, multi 16: LBA 
[    0.968431] ata1.01: configured for UDMA/133
[    0.968585] scsi 0:0:1:0: Direct-Access     ATA      Maxtor 6Y080L0   YAR4 PQ: 0 ANSI: 5
[    0.968778] sd 0:0:1:0: Attached scsi generic sg0 type 0
[    0.968859] sd 0:0:1:0: [sda] 160086528 512-byte logical blocks: (81.9 GB/76.3 GiB)
[    0.968930] sd 0:0:1:0: [sda] Write Protect is off
[    0.968935] sd 0:0:1:0: [sda] Mode Sense: 00 3a 00 00
[    0.968969] sd 0:0:1:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    0.969171]  sda: sda1 sda2 < sda5 sda6 sda7 >
[    1.009861] sd 0:0:1:0: [sda] Attached SCSI disk
[    1.132461] ata2.00: ATAPI: HL-DT-STDVDRRW GSA-4166B, 1.02, max UDMA/66
[    1.148442] ata2.00: configured for UDMA/66
[    1.151347] scsi 1:0:0:0: CD-ROM            HL-DT-ST DVDRRW GSA-4166B 1.02 PQ: 0 ANSI: 5
[    1.156419] sr0: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
[    1.156425] Uniform CD-ROM driver Revision: 3.20
[    1.156561] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    1.156644] sr 1:0:0:0: Attached scsi generic sg1 type 5
[    1.156684] Freeing unused kernel memory: 540k freed
[    1.157097] Write protecting the kernel text: 4568k
[    1.157128] Write protecting the kernel read-only data: 1836k
[    1.304217] usb 3-1: new low speed USB device using uhci_hcd and address 2
[    1.456984]   alloc irq_desc for 19 on node -1
[    1.456989]   alloc kstat_irqs on node -1
[    1.456999] ohci1394 0000:00:0b.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    1.497793] usb 3-1: configuration #1 chosen from 1 choice
[    1.514794] ohci1394: fw-host0: OHCI-1394 1.0 (PCI): IRQ=[19]  MMIO=[f7fff000-f7fff7ff]  Max Packet=[2]  IR/IT contexts=[4/8]
[    1.521818] ohci1394: fw-host0: Serial EEPROM has suspicious values, attempting to set max_packet_size to 512 bytes
[    1.548280] Linux agpgart interface v0.103
[    1.553417] Floppy drive(s): fd0 is 1.44M
[    1.558023] via-rhine.c:v1.10-LK1.4.3 2007-03-06 Written by Donald Becker
[    1.576724] FDC 0 is a post-1991 82077
[    1.593748] sata_via 0000:00:0f.0: version 2.4
[    1.593770] sata_via 0000:00:0f.0: PCI INT B -> GSI 20 (level, low) -> IRQ 20
[    1.593815] sata_via 0000:00:0f.0: routed to hard irq line 11
[    1.593927] scsi2 : sata_via
[    1.594045] scsi3 : sata_via
[    1.594107] ata3: SATA max UDMA/133 cmd 0xec00 ctl 0xe880 bmdma 0xe400 irq 20
[    1.594111] ata4: SATA max UDMA/133 cmd 0xe800 ctl 0xe480 bmdma 0xe408 irq 20
[    1.594173] agpgart: Detected VIA PT880 Ultra chipset
[    1.598172] agpgart-via 0000:00:00.0: AGP aperture is 64M @ 0xf8000000
[    1.598218]   alloc irq_desc for 23 on node -1
[    1.598221]   alloc kstat_irqs on node -1
[    1.598230] via-rhine 0000:00:12.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    1.599006] eth0: VIA Rhine II at 0xf7fffc00, 00:13:8f:4a:c9:f5, IRQ 23.
[    1.599640] eth0: MII PHY found at address 1, status 0x7849 advertising 05e1 Link 0000.
[    1.638828] usbcore: registered new interface driver hiddev
[    1.652359] input: Microsoft Microsoft 3-Button Mouse with IntelliEye(TM) as /devices/pci0000:00/0000:00:10.1/usb3/3-1/3-1:1.0/input/input4
[    1.652485] generic-usb 0003:045E:0040.0001: input,hidraw0: USB HID v1.10 Mouse [Microsoft Microsoft 3-Button Mouse with IntelliEye(TM)] on usb-0000:00:10.1-1/input0
[    1.652511] usbcore: registered new interface driver usbhid
[    1.652516] usbhid: v2.6:USB HID core driver
[    1.824016] ata3: SATA link down 1.5 Gbps (SStatus 0 SControl 300)
[    2.036022] ata4: SATA link down 1.5 Gbps (SStatus 0 SControl 300)
[    2.942629] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[4d5a900003000000]
[    4.040987] PM: Starting manual resume from disk
[    4.040994] PM: Resume from partition 8:7
[    4.040995] PM: Checking hibernation image.
[    4.046290] PM: Resume from disk failed.
[    4.080418] EXT4-fs (sda6): barriers enabled
[    4.096039] kjournald2 starting: pid 339, dev sda6:8, commit interval 5 seconds
[    4.096070] EXT4-fs (sda6): delayed allocation enabled
[    4.096075] EXT4-fs: file extents enabled
[    4.096193] EXT4-fs: mballoc enabled
[    4.096214] EXT4-fs (sda6): mounted filesystem with ordered data mode
[    4.805086] type=1505 audit(1257443268.502:2): operation="profile_load" pid=362 name=/usr/share/gdm/guest-session/Xsession
[    4.824471] type=1505 audit(1257443268.522:3): operation="profile_load" pid=363 name=/sbin/dhclient3
[    4.825192] type=1505 audit(1257443268.522:4): operation="profile_load" pid=363 name=/usr/lib/NetworkManager/nm-dhcp-client.action
[    4.825584] type=1505 audit(1257443268.522:5): operation="profile_load" pid=363 name=/usr/lib/connman/scripts/dhclient-script
[    4.858873] type=1505 audit(1257443268.554:6): operation="profile_load" pid=364 name=/usr/bin/evince
[    4.869978] type=1505 audit(1257443268.566:7): operation="profile_load" pid=364 name=/usr/bin/evince-previewer
[    4.876583] type=1505 audit(1257443268.574:8): operation="profile_load" pid=364 name=/usr/bin/evince-thumbnailer
[    4.895196] type=1505 audit(1257443268.590:9): operation="profile_load" pid=366 name=/usr/lib/cups/backend/cups-pdf
[    4.896070] type=1505 audit(1257443268.594:10): operation="profile_load" pid=366 name=/usr/sbin/cupsd
[    6.464813] Adding 1437776k swap on /dev/sda7.  Priority:-1 extents:1 across:1437776k 
[    6.544242] udev: starting version 147
[    6.735653] EXT4-fs (sda6): internal journal on sda6:8
[    9.815630] __ratelimit: 3 callbacks suppressed
[    9.815636] type=1505 audit(1257443273.510:12): operation="profile_replace" pid=650 name=/usr/share/gdm/guest-session/Xsession
[    9.818956] type=1505 audit(1257443273.514:13): operation="profile_replace" pid=651 name=/sbin/dhclient3
[    9.819688] type=1505 audit(1257443273.514:14): operation="profile_replace" pid=651 name=/usr/lib/NetworkManager/nm-dhcp-client.action
[    9.820240] type=1505 audit(1257443273.518:15): operation="profile_replace" pid=651 name=/usr/lib/connman/scripts/dhclient-script
[    9.827275] type=1505 audit(1257443273.522:16): operation="profile_replace" pid=652 name=/usr/bin/evince
[    9.838987] type=1505 audit(1257443273.534:17): operation="profile_replace" pid=652 name=/usr/bin/evince-previewer
[    9.846491] type=1505 audit(1257443273.542:18): operation="profile_replace" pid=652 name=/usr/bin/evince-thumbnailer
[    9.858495] type=1505 audit(1257443273.554:19): operation="profile_replace" pid=654 name=/usr/lib/cups/backend/cups-pdf
[    9.859343] type=1505 audit(1257443273.554:20): operation="profile_replace" pid=654 name=/usr/sbin/cupsd
[    9.863569] type=1505 audit(1257443273.558:21): operation="profile_replace" pid=655 name=/usr/sbin/tcpdump
[   10.600743] eth0: link down
[   10.600904] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   12.606417] parport_pc 00:06: reported by Plug and Play ACPI
[   12.606530] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,EPP,ECP,DMA]
[   12.818951] nvidia: module license 'NVIDIA' taints kernel.
[   12.818958] Disabling lock debugging due to kernel taint
[   13.079656] lp0: using parport0 (interrupt-driven).
[   13.082898] ppdev: user-space parallel port driver
[   13.087458] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   13.149331] gameport: NS558 PnP Gameport is pnp00:07/gameport0, io 0x200, speed 795kHz
[   13.150757] cfg80211: Calling CRDA to update world regulatory domain
[   13.159748]   alloc irq_desc for 24 on node -1
[   13.159753]   alloc kstat_irqs on node -1
[   13.159763] nvidia 0000:02:00.0: PCI INT A -> GSI 24 (level, low) -> IRQ 24
[   13.159772] nvidia 0000:02:00.0: setting latency timer to 64
[   13.160063] NVRM: loading NVIDIA UNIX x86 Kernel Module  173.14.20  Thu Jun 25 19:23:24 PDT 2009
[   13.246097] ip_tables: (C) 2000-2006 Netfilter Core Team
[   13.336409] cfg80211: World regulatory domain updated:
[   13.336415] 	(start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   13.336419] 	(2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   13.336422] 	(2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   13.336425] 	(2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   13.336428] 	(5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   13.336431] 	(5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   16.341121]   alloc irq_desc for 18 on node -1
[   16.341126]   alloc kstat_irqs on node -1
[   16.341136] rt61pci 0000:00:0a.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[   16.402341] phy0: Selected rate control algorithm 'minstrel'
[   16.403439] Registered led device: rt61pci-phy0::radio
[   16.403465] Registered led device: rt61pci-phy0::assoc
[   18.109691] rt61pci 0000:00:0a.0: firmware: requesting rt2561s.bin
[   18.396449] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   19.072365]   alloc irq_desc for 22 on node -1
[   19.072370]   alloc kstat_irqs on node -1
[   19.072380] VIA 82xx Audio 0000:00:11.5: PCI INT C -> GSI 22 (level, low) -> IRQ 22
[   19.072543] VIA 82xx Audio 0000:00:11.5: setting latency timer to 64
[   19.373347] nf_conntrack version 0.5.0 (16384 buckets, 65536 max)
[   19.373633] CONFIG_NF_CT_ACCT is deprecated and will be removed soon. Please use
[   19.373637] nf_conntrack.acct=1 kernel parameter, acct=1 nf_conntrack module option or
[   19.373640] sysctl net.netfilter.nf_conntrack_acct=1 to enable it.
[   40.905314] wlan0: authenticate with AP 00:22:3f:15:41:74
[   40.908281] wlan0: authenticated
[   40.908288] wlan0: associate with AP 00:22:3f:15:41:74
[   40.911693] wlan0: RX AssocResp from 00:22:3f:15:41:74 (capab=0x401 status=0 aid=2)
[   40.911700] wlan0: associated
[   40.912317] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   51.856020] wlan0: no IPv6 routers present
[   60.282368] Netfilter messages via NETLINK v0.30.
[ 1636.013609] irq 23: nobody cared (try booting with the "irqpoll" option)
[ 1636.013619] Pid: 0, comm: swapper Tainted: P           2.6.31-14-generic #48-Ubuntu
[ 1636.013622] Call Trace:
[ 1636.013635]  [<c056e41c>] ? printk+0x18/0x1c
[ 1636.013645]  [<c0190ee7>] __report_bad_irq+0x27/0x90
[ 1636.013651]  [<c018f8fc>] ? handle_IRQ_event+0x4c/0x140
[ 1636.013655]  [<c01910a0>] note_interrupt+0x150/0x190
[ 1636.013659]  [<c01915fc>] handle_fasteoi_irq+0xac/0xd0
[ 1636.013664]  [<c0105a38>] handle_irq+0x18/0x30
[ 1636.013667]  [<c0104f07>] do_IRQ+0x47/0xc0
[ 1636.013851]  [<f8df6c59>] ? _nv003968rm+0x2d/0x51 [nvidia]
[ 1636.013860]  [<c01039b0>] common_interrupt+0x30/0x40
[ 1636.013879]  [<c014b365>] ? __do_softirq+0x45/0x1a0
[ 1636.013884]  [<c018f8fc>] ? handle_IRQ_event+0x4c/0x140
[ 1636.013889]  [<c0121270>] ? ack_apic_level+0x60/0x230
[ 1636.013893]  [<c01915dd>] ? handle_fasteoi_irq+0x8d/0xd0
[ 1636.013897]  [<c014b4fd>] do_softirq+0x3d/0x40
[ 1636.013900]  [<c014b63d>] irq_exit+0x5d/0x70
[ 1636.013904]  [<c0104f10>] do_IRQ+0x50/0xc0
[ 1636.013908]  [<c01039b0>] common_interrupt+0x30/0x40
[ 1636.013912]  [<c010a993>] ? mwait_idle+0x63/0xf0
[ 1636.013916]  [<c010202c>] cpu_idle+0x8c/0xd0
[ 1636.013922]  [<c055e875>] rest_init+0x55/0x60
[ 1636.013928]  [<c078e8cd>] start_kernel+0x2e6/0x2ec
[ 1636.013932]  [<c078e406>] ? unknown_bootoption+0x0/0x1ab
[ 1636.013936]  [<c078e07c>] i386_start_kernel+0x7c/0x83
[ 1636.013939] handlers:
[ 1636.013943] [<f813bca0>] (rhine_interrupt+0x0/0x2b0 [via_rhine])
[ 1636.013955] Disabling IRQ #23
[ 8040.492239] sr 1:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 8040.492247] sr 1:0:0:0: [sr0] Sense Key : Illegal Request [current] 
[ 8040.492253] sr 1:0:0:0: [sr0] Add. Sense: Illegal mode for this track
[ 8040.492260] end_request: I/O error, dev sr0, sector 0
[ 8040.492268] Buffer I/O error on device sr0, logical block 0
[ 8040.506150] sr 1:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 8040.506157] sr 1:0:0:0: [sr0] Sense Key : Illegal Request [current] 
[ 8040.506163] sr 1:0:0:0: [sr0] Add. Sense: Illegal mode for this track
[ 8040.506171] end_request: I/O error, dev sr0, sector 0
[ 8040.506179] Buffer I/O error on device sr0, logical block 0
[ 8040.522269] cdrom: This disc doesn't have any tracks I recognize!
[ 8040.538549] sr 1:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 8040.538556] sr 1:0:0:0: [sr0] Sense Key : Illegal Request [current] 
[ 8040.538562] sr 1:0:0:0: [sr0] Add. Sense: Illegal mode for this track
[ 8040.538570] end_request: I/O error, dev sr0, sector 0
[ 8040.538577] Buffer I/O error on device sr0, logical block 0
[ 8040.542641] sr 1:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 8040.542648] sr 1:0:0:0: [sr0] Sense Key : Illegal Request [current] 
[ 8040.542654] sr 1:0:0:0: [sr0] Add. Sense: Illegal mode for this track
[ 8040.542662] end_request: I/O error, dev sr0, sector 0
[ 8040.542668] Buffer I/O error on device sr0, logical block 0
[ 8166.000070] ata2.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6 frozen
[ 8166.000085] ata2.00: cmd a0/01:00:00:00:80/00:00:00:00:00/a0 tag 0 dma 32768 out
[ 8166.000087]          cdb 2a 00 00 00 00 00 00 00  10 00 00 00 00 00 00 00
[ 8166.000088]          res 40/00:02:00:08:00/00:00:00:00:00/a0 Emask 0x4 (timeout)
[ 8166.000092] ata2.00: status: { DRDY }
[ 8171.012038] ata2: link is slow to respond, please be patient (ready=0)
[ 8176.056027] ata2: device not ready (errno=-16), forcing hardreset
[ 8176.056039] ata2: soft resetting link
[ 8176.236393] ata2.00: configured for UDMA/66
[ 8176.238423] ata2: EH complete
[ 9107.408000] type=1505 audit(1257452371.102:22): operation="profile_replace" pid=4818 name=/usr/share/gdm/guest-session/Xsession
[ 9107.840686] type=1505 audit(1257452371.538:23): operation="profile_replace" pid=4820 name=/sbin/dhclient3
[ 9107.840927] type=1505 audit(1257452371.538:24): operation="profile_replace" pid=4820 name=/usr/lib/NetworkManager/nm-dhcp-client.action
[ 9107.841088] type=1505 audit(1257452371.538:25): operation="profile_replace" pid=4820 name=/usr/lib/connman/scripts/dhclient-script
[ 9124.513702] type=1505 audit(1257452388.210:26): operation="profile_replace" pid=4821 name=/usr/bin/evince
[ 9124.515440] type=1505 audit(1257452388.210:27): operation="profile_replace" pid=4821 name=/usr/bin/evince-previewer
[ 9124.516814] type=1505 audit(1257452388.214:28): operation="profile_replace" pid=4821 name=/usr/bin/evince-thumbnailer
[ 9124.911773] type=1505 audit(1257452388.606:29): operation="profile_replace" pid=4824 name=/usr/lib/cups/backend/cups-pdf
[ 9124.915943] type=1505 audit(1257452388.610:30): operation="profile_replace" pid=4824 name=/usr/sbin/cupsd
[ 9125.016761] type=1505 audit(1257452388.714:31): operation="profile_load" pid=4825 name=/usr/sbin/mysqld-akonadi
[ 9125.118283] type=1505 audit(1257452388.814:32): operation="profile_replace" pid=4826 name=/usr/sbin/tcpdump
[ 9380.920050] ISO 9660 Extensions: Microsoft Joliet Level 3
[ 9380.952813] ISO 9660 Extensions: IEEE_P1282
[ 9474.436068] sr 1:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 9474.436075] sr 1:0:0:0: [sr0] Sense Key : Illegal Request [current] 
[ 9474.436081] sr 1:0:0:0: [sr0] Add. Sense: Illegal mode for this track
[ 9474.436089] end_request: I/O error, dev sr0, sector 0
[ 9474.436096] Buffer I/O error on device sr0, logical block 0
[ 9474.438541] sr 1:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 9474.438548] sr 1:0:0:0: [sr0] Sense Key : Illegal Request [current] 
[ 9474.438553] sr 1:0:0:0: [sr0] Add. Sense: Illegal mode for this track
[ 9474.438560] end_request: I/O error, dev sr0, sector 0
[ 9474.438566] Buffer I/O error on device sr0, logical block 0
[ 9474.451584] cdrom: This disc doesn't have any tracks I recognize!
[ 9474.473007] sr 1:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 9474.473014] sr 1:0:0:0: [sr0] Sense Key : Illegal Request [current] 
[ 9474.473020] sr 1:0:0:0: [sr0] Add. Sense: Illegal mode for this track
[ 9474.473028] end_request: I/O error, dev sr0, sector 0
[ 9474.473035] Buffer I/O error on device sr0, logical block 0
[ 9474.477845] sr 1:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 9474.477853] sr 1:0:0:0: [sr0] Sense Key : Illegal Request [current] 
[ 9474.477859] sr 1:0:0:0: [sr0] Add. Sense: Illegal mode for this track
[ 9474.477867] end_request: I/O error, dev sr0, sector 0
[ 9474.477874] Buffer I/O error on device sr0, logical block 0
[ 9601.689731] cdrom: This disc doesn't have any tracks I recognize!
[ 9601.809235] sr 1:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 9601.809243] sr 1:0:0:0: [sr0] Sense Key : Illegal Request [current] 
[ 9601.809249] sr 1:0:0:0: [sr0] Add. Sense: Illegal mode for this track
[ 9601.809257] end_request: I/O error, dev sr0, sector 0
[ 9601.809265] Buffer I/O error on device sr0, logical block 0
[ 9601.812476] sr 1:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 9601.812483] sr 1:0:0:0: [sr0] Sense Key : Illegal Request [current] 
[ 9601.812489] sr 1:0:0:0: [sr0] Add. Sense: Illegal mode for this track
[ 9601.812497] end_request: I/O error, dev sr0, sector 0
[ 9601.812504] Buffer I/O error on device sr0, logical block 0
```

---

### Post by pbeesley on 2009-11-05
ok so that just got about 50% of the way through then died :(

```
Executing 'builtin_dd if=/media/Saturn/00 Downloads/test.iso of=/dev/sr0 obs=32k seek=0'
:-? more than 50% of space will be *wasted*!
/dev/sr0: splitting layers at 814480 blocks
/dev/sr0: "Current Write Speed" is 4.1x1352KBps.
:-[ WRITE@LBA=c6d80h failed with SK=3h/ASC=0Ch/ACQ=80h]: Input/output error
:-( write failed: Input/output error
```

---

### Post by fenian on 2009-11-05
Perhaps the file you are trying to burn is corrupt.Have you tried to burn different files?

---

### Post by pbeesley on 2009-11-05
yeah tried iso then just a few random files a few times

---

### Post by pbeesley on 2009-11-05
```
kp3@sol:~$ sudo k3b
Error: "/var/tmp/kdecache-kp3" is owned by uid 1000 instead of uid 0.
Error: "/tmp/kde-kp3" is owned by uid 1000 instead of uid 0.
kp3@sol:~$ Error: "/tmp/ksocket-kp3" is owned by uid 1000 instead of uid 0.
QLayout: Attempting to add QLayout "" to QFrame "", which already has a layout
K3bQProcess::QProcess(0x0)
lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/kp3/.gvfs
      Output information may be incomplete.

```

---

### Post by kestrel1 on 2009-11-05
> **pbeesley said:**
> ```
kp3@sol:~$ sudo k3b
Error: "/var/tmp/kdecache-kp3" is owned by uid 1000 instead of uid 0.
Error: "/tmp/kde-kp3" is owned by uid 1000 instead of uid 0.
kp3@sol:~$ Error: "/tmp/ksocket-kp3" is owned by uid 1000 instead of uid 0.
QLayout: Attempting to add QLayout "" to QFrame "", which already has a layout
K3bQProcess::QProcess(0x0)
lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/kp3/.gvfs
      Output information may be incomplete.

```
Do you get any errors if you just run k3b without root privileges?
I think this error is telling you that the root user does not own those folders.
Just noticed your location. No more than 25miles from myself :-)

---

### Post by pbeesley on 2009-11-05
Where are you based :)

also yeah same errors  :(

---

### Post by kestrel1 on 2009-11-05
> **pbeesley said:**
> Where are you based :)

also yeah same errors  :(
Not far from Salisbury :-)
It looks like it must be something to do with permissions, but if you are the owner of those folders I cannot understand why you are getting the same errors.
Have you tried to chmod the folders? If you give all users read/write access it should work.
```
sudo chmod 777 /var/tmp/kdecache-kp3
```
```
sudo chmod 777 /tmp/kde-kp3
```
```
sudo chmod 777 /tmp/ksocket-kp3
```

---

### Post by pbeesley on 2009-11-05
right did all that and got this far

```
k3b
kp3@sol:~$ kdeinit4: preparing to launch /usr/lib/kde4/kio_file.so
QLayout: Attempting to add QLayout "" to QFrame "", which already has a layout
K3bQProcess::QProcess(0x0)
QIODevice::putChar: Closed device
QIODevice::putChar: Closed device
QIODevice::putChar: Closed device
QIODevice::putChar: Closed device
QIODevice::putChar: Closed device
QIODevice::putChar: Closed device
QIODevice::putChar: Closed device
QIODevice::putChar: Closed device
QIODevice::putChar: Closed device
QIODevice::putChar: Closed device
QIODevice::putChar: Closed device
QIODevice::putChar: Closed device
QIODevice::putChar: Closed device
QIODevice::putChar: Closed device
QIODevice::putChar: Closed device
QIODevice::putChar: Closed device
QIODevice::putChar: Closed device
QIODevice::putChar: Closed device
QIODevice::putChar: Closed device
QIODevice::putChar: Closed device
QIODevice::putChar: Closed device
QIODevice::putChar: Closed device
QIODevice::putChar: Closed device
QIODevice::putChar: Closed device
QIODevice::putChar: Closed device
QIODevice::putChar: Closed device
QIODevice::putChar: Closed device
QIODevice::putChar: Closed device
QIODevice::putChar: Closed device
QIODevice::putChar: Closed device
QIODevice::putChar: Closed device
QIODevice::putChar: Closed device
QIODevice::putChar: Closed device
QIODevice::putChar: Closed device
QIODevice::putChar: Closed device
QIODevice::putChar: Closed device
QIODevice::putChar: Closed device
QIODevice::putChar: Closed device
QIODevice::putChar: Closed device
QIODevice::putChar: Closed device
QIODevice::putChar: Closed device
QIODevice::putChar: Closed device
QIODevice::putChar: Closed device
QIODevice::putChar: Closed device
QIODevice::putChar: Closed device
QIODevice::putChar: Closed device
QIODevice::putChar: Closed device
QIODevice::putChar: Closed device
QIODevice::putChar: Closed device
QIODevice::putChar: Closed device
QIODevice::putChar: Closed device
QIODevice::putChar: Closed device
QIODevice::putChar: Closed device
QIODevice::putChar: Closed device
QIODevice::putChar: Closed device
QIODevice::putChar: Closed device
QIODevice::putChar: Closed device
QIODevice::putChar: Closed device
QIODevice::putChar: Closed device
QIODevice::putChar: Closed device
QIODevice::putChar: Closed device
QIODevice::putChar: Closed device
QIODevice::putChar: Closed device
QIODevice::putChar: Closed device
QIODevice::putChar: Closed device
QIODevice::putChar: Closed device
QIODevice::putChar: Closed device
QIODevice::putChar: Closed device
QIODevice::putChar: Closed device
QIODevice::putChar: Closed device
QIODevice::putChar: Closed device
QIODevice::putChar: Closed device
QIODevice::putChar: Closed device
QIODevice::putChar: Closed device
QIODevice::putChar: Closed device
QIODevice::putChar: Closed device
QIODevice::putChar: Closed device
QIODevice::putChar: Closed device
QIODevice::putChar: Closed device
QIODevice::putChar: Closed device
QIODevice::putChar: Closed device
QIODevice::putChar: Closed device
QIODevice::putChar: Closed device
QIODevice::putChar: Closed device
QIODevice::putChar: Closed device
QIODevice::putChar: Closed device
QIODevice::putChar: Closed device
QIODevice::putChar: Closed device
QFile::seek: IODevice is not open
QFile::seek: IODevice is not open
QFile::remove: Empty or null file name
QFile::seek: IODevice is not open
QFile::seek: IODevice is not open
QFile::seek: IODevice is not open
QFile::seek: IODevice is not open
QFile::seek: IODevice is not open
QFile::seek: IODevice is not open

```

---

### Post by pbeesley on 2009-11-05
k3b GUI reports this

```
Devices
-----------------------
HL-DT-ST DVDRRW GSA-4166B 1.02 (/dev/sr0, CD-R, CD-RW, CD-ROM, DVD-ROM, DVD-R, DVD-RW, DVD+R, DVD+RW, DVD+R DL) [DVD-ROM, DVD-R Sequential, DVD-R Dual Layer Sequential, DVD-RAM, DVD-RW Restricted Overwrite, DVD-RW Sequential, DVD+RW, DVD+R, DVD+R Dual Layer, CD-ROM, CD-R, CD-RW] [SAO, TAO, RAW, SAO/R96P, SAO/R96R, RAW/R16, RAW/R96P, RAW/R96R, Restricted Overwrite] [%7]

System
-----------------------
K3b Version: 1.68.0
KDE Version: 4.3.2 (KDE 4.3.2)
QT Version:  4.5.2
Kernel:      2.6.31-14-generic

Used versions
-----------------------
cdrecord: 1.1.9

cdrecord
-----------------------
/usr/bin/wodim: Operation not permitted. Warning: Cannot raise RLIMIT_MEMLOCK limits.scsidev: '/dev/sr0'
devname: '/dev/sr0'
scsibus: -2 target: -2 lun: -2
Linux sg driver version: 3.5.27
Wodim version: 1.1.9
SCSI buffer size: 64512
Beginning DMA speed test. Set CDR_NODMATEST environment variable if device
communication breaks or freezes immediately after that.
TOC Type: 1 = CD-ROM
Driveropts: 'burnfree'
Device type    : Removable CD-ROM
Version        : 5
Response Format: 2
Capabilities   : 
Vendor_info    : 'HL-DT-ST'
Identification : 'DVDRRW GSA-4166B'
Revision       : '1.02'
Device seems to be: Generic mmc2 DVD-R/DVD-RW.
Current: 0x002B (DVD+R/DL)
Profile: 0x0012 (DVD-RAM) 
Profile: 0x002B (DVD+R/DL) (current)
Profile: 0x001B (DVD+R) 
Profile: 0x001A (DVD+RW) 
Profile: 0x0015 (DVD-R/DL sequential recording) 
Profile: 0x0014 (DVD-RW sequential recording) 
Profile: 0x0013 (DVD-RW restricted overwrite) 
Profile: 0x0011 (DVD-R sequential recording) 
Profile: 0x0010 (DVD-ROM) 
Profile: 0x000A (CD-RW) 
Profile: 0x0009 (CD-R) 
Profile: 0x0008 (CD-ROM) 
Profile: 0x0002 (Removable disk) 
Using generic SCSI-3/mmc DVD-R(W) driver (mmc_mdvd).
Driver flags   : SWABAUDIO BURNFREE 
Supported modes: PACKET SAO
Drive buf size : 1409024 = 1376 KB
Drive DMA Speed: 13246 kB/s 75x CD 9x DVD
FIFO size      : 12582912 = 12288 KB
Speed set to 5540 KB/s
Track 01: data  3181 MB        
Total size:     3653 MB (361:59.46) = 1628960 sectors
Lout start:     3654 MB (362:01/35) = 1628960 sectors
Current Secsize: 2048
HINT: use dvd+rw-mediainfo from dvd+rw-tools for information extraction.
Blocks total: 4173824 Blocks current: 4173824 Blocks remaining: 2544864
Starting to write CD/DVD at speed   4.0 in real SAO mode for single session.
Last chance to quit, starting real write in    2 seconds.
   1 seconds.
   0 seconds. Operation starts.dvd_dual_layer_split: read_dvd_structure returns invalid data
Preparing middle zone location for this DVD+R dual layer disc
Waiting for reader process to fill input buffer ... Errno: 5 (Input/output error), reserve track scsi sendcmd: no error
CDB:  53 00 00 00 00 00 18 DB 20 00
status: 0x2 (CHECK CONDITION)
Sense Bytes: 70 00 03 00 00 00 00 0E 00 00 00 00 0C 80 00 00
Sense Key: 0x3 Medium Error, Segment 0
Sense Code: 0x0C Qual 0x80 (write error) [No matching qualifier] Fru 0x0
Sense flags: Blk 0 (not valid) 
cmd finished after 83.273s timeout 200s
/usr/bin/wodim: Cannot open new session.
input buffer ready.
Writing  time:   83.430s
/usr/bin/wodim: fifo had 192 puts and 0 gets.
/usr/bin/wodim: fifo was 0 times empty and 0 times full, min fill was 100%.

cdrecord command:
-----------------------
/usr/bin/wodim -v gracetime=2 dev=/dev/sr0 speed=4 -sao driveropts=burnfree -data -tsize=1628960s -
```

---

### Post by pbeesley on 2009-11-06
anyone know what this means?

---

### Post by kumoshk on 2009-11-06
Does it work from the live CD?

If not, does it work from Jaunty's live CD?

I wouldn't do anything too hasty with going back to Windows, now. If it works in Jaunty, why not go back to Jaunty instead? It's a good distribution, I think, even if it's not the latest&#8212;although the log-in screen of Karmic is nice and all.

---

### Post by pbeesley on 2009-11-06
can i do that...boot from the live CD and then take the cd out to put in a blank DVD?

---

### Post by P4man on 2009-11-06
> **pbeesley said:**
> can i do that...boot from the live CD and then take the cd out to put in a blank DVD?

You could try but it may well (and probably will) fail. Ubuntu can not load to ram from a liveCD. 
 Knoppix can do that
alternatively you could try booting from a usb stick

But I guess the question here is: are you sure the dvd writer is ok? If you have another OS installed or you can plug the writer in a different machine  that would also answer that question at least.

---

### Post by pbeesley on 2009-11-06
Yeah I have a windows partion set up. Thing is the Drive reads and was used to burn the karmic CD so I really doubt it is the drive. Someone at work suggested uninstalling then reinstalling the device so I'll try....

- burn an iso in windows
-if the works uninstalling the dvd drive (if I can figure out how)
- cry
- reinstalling jaunty

---

### Post by rudy.elgato on 2009-11-08
I'm having a similar problem.  Since installing 9.10 I'm not able to burn any DVDs.  I've tried using K3b and Brasero, I've tried using DVD-R and DVD+R disk, but nothing works.  I was running 8.04/10 on this system before the clean install of 9.10 and that worked fine.  

In this thread orasis mentions to run a 'dmesg' and capture the output, which pbeesley did.  Has anyone had a chance to look at pbeesley's dmesg output?  I'm asking because I ran dmesg on my system and I see the same "end_request: I/O error, dev sr0, sector 0" in my output that pbeesley reports.  I'm not that familiar with dmesg output, but believe "/dev/sr0" is the dvd writer and don't think an "I/O error" is a good thing.

Thanks...

---

### Post by P4man on 2009-11-08
> **rudy.elgato said:**
> I  I'm not that familiar with dmesg output, but believe "/dev/sr0" is the dvd writer and don't think an "I/O error" is a good thing.


That gives me an idea.. can you go in to the bios and check if you have a settings for you sata devices called AHCI or "IDE Compatibility" ? Disable AHCI if possible (or enable IDE compatibility I believe thats the same thing) and try again?

At least thats assuming you have a sata DVD burner.

---

### Post by rudy.elgato on 2009-11-08
I do have a SATA DVD burner...

Just checked my BIOS and did not see anything mentioning AHCI.

With regards to "IDE compatibility" not sure if it's what you're asking about, but I do see something that says "IDE BusMaster    Enabled".

Wish I were more technically inclined.  Will be more then happy to try and check things if you all can just let me know what to check.

Thanks...

---

### Post by pbeesley on 2009-11-08
Ok i have some progression. I burnt a CD but DVD's won't read....come it people so close....do i need to do something like sudo apt-get install makedvdwork :D

---

### Post by rudy.elgato on 2009-11-08
should have mentioned it, I'm also able to burn usable CDs, just not DVDs.  this is with the same CD/DVD burner.  burn CDs OK,  DVDs not able to...

---

### Post by rudy.elgato on 2009-11-09
Found a fix, at least for my situation...

I ran item #2 in [http://art.ubuntuforums.org/showpost.php?p=7185976&postcount=34](http://art.ubuntuforums.org/showpost.php?p=7185976&postcount=34), and I've been able burn dvds again.  Apparently there are quite a few reported issues related to "wodim".  Anyhow, like I said, running 'sudo chmod u+s /usr/bin/wodim' seems to correct the problem I was having.  Just hoping it permanent.

A few things I did notice afterwards when running 'k3b':

- the little spinning icon that usually just shows up for a second or so while a gui opens, remains constantly spinning.  it's a little odd, makes you think something is stuck, but even though it's spinning, all button selections are live.  
- there's no indication that the checksum is running.  typically as soon as you select the iso to burn in k3b the md5 checksum is run, and you see the indicator bar increasing in size until it reaches the end and you end up with your checksum total.  for me, the bar does not show up at all.  eventually after a minute or so, the time it typically takes for the checksum to run, the checksum total appears.  could be related to the spinning busy icon.  who knows...
- I didn't try burning anything faster then 4x.  

Anyhow, maybe the 'chmod' will help some of you as well...

---

### Post by jeb800e on 2009-11-09
Try updating your system. There may be some fixes released apart from the October 29 release of Karmic

---

### Post by Amzer zo on 2009-11-14
Can't burn audio CDs with Karmic (kubuntu).  The little spinning icon also shows for me but items and menus are selectable.
When burning the CD, it gets stuck on "preparing data" while the CPU goes to 100%.  I waited more than 10 minutes and nothing happens.
The action on wodim does not do anything for me.

---

### Post by funnyname on 2009-11-15
Has there been any update on this. I also use K3B in Ubuntu 9.10, and am also having issues.

It seems to burn the disk, yet on verify it give an error that it can not read sector #,###,###. When I check the disk on my laptop (Ubuntu 9.04), it will not read the disc. Yet when I place the disc in my DVD player, it works.  It also does the same think, where the 'in use' mouse icon stays spinning throughout.

I decided to try Brasero, and it works and verifies the disc with no issue. I suspect this may be because of the method of verification.

Interestingly, I am able to burn the dual layer disks on my laptop, using K3B with 9.04. Is there an issue with this newer version of K3B? Also it worked fine with this drive prior to upgrading to 9.10.

---

### Post by sigurnjak on 2009-11-15
Problem seem to be stil lhere . This is message i get 
DBus error org.gtk.Private.RemoteVolumeMonitor.NotFound: The given volume was not found

It seems to have something to do gvfs , but that is way beyond my skill to fix .

---

### Post by funnyname on 2010-01-08
Is there any movement by the K3B team to fix this?

I am still having the issue with Dual Layer Disks.

---

