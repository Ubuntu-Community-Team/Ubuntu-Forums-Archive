---
title: "None of the services start"
date: 2010-02-09
forum: General Help
---

### Post by blwegrzyn on 2010-02-09
Hello, 
I am running ubuntu 9.10 with the latest patches and all the prerelase patches.  At some point and i am not sure when something broke and none off the services start during the boot.
Also the virtual consoles do not start.  The only services that start are the one that are controlled by the gnome session.
In addition i cannot start the rescue mode. It stops loading at same point where the console should show up.  I am guessing that the problem is related to the upstart but i am not sure.  I never ever had problems with boot in linux and this is very frustrating.  I feel like i am running windows and dont know how to troubleshoot. I cannot see anything in the log that would give me a hint?  I dont know where too look.  I tried to activate the bootlogd but it does not work. Probably beacause the services dont start correctly.  Something broke and one of the updates must changed something but i dont know what and where? Anyone can recommend where to look?
How do i see the interactive boot? I tried remove the splash and quiet from grub config but i could not see anything there.  I got too fast to the x login.

please advise?

thx

Bart

---

### Post by mikewhatever on 2010-02-09
You should probably attach your dmesg for people to review.

---

### Post by blwegrzyn on 2010-02-09
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.31-20-generic (buildd@yellow) (gcc version 4.4.1 (Ubuntu 4.4.1-4ubuntu9) ) #57-Ubuntu SMP Mon Feb 8 09:02:26 UTC 2010 (Ubuntu 2.6.31-20.57-generic)
[    0.000000] Command line: BOOT_IMAGE=/vmlinuz-2.6.31-20-generic root=UUID=9a1cf013-ba9d-42c5-a7ee-42a544c9d19d ro quiet splash
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   Centaur CentaurHauls
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f000 (usable)
[    0.000000]  BIOS-e820: 000000000009f000 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000007fe5a800 (usable)
[    0.000000]  BIOS-e820: 000000007fe5a800 - 0000000080000000 (reserved)
[    0.000000]  BIOS-e820: 00000000f8000000 - 00000000fc000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed18000 - 00000000fed1c000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed20000 - 00000000fed90000 (reserved)
[    0.000000]  BIOS-e820: 00000000feda0000 - 00000000feda6000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee10000 (reserved)
[    0.000000]  BIOS-e820: 00000000ffe00000 - 0000000100000000 (reserved)
[    0.000000] DMI 2.4 present.
[    0.000000] last_pfn = 0x7fe5a max_arch_pfn = 0x400000000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-CFFFF write-protect
[    0.000000]   D0000-EFFFF uncachable
[    0.000000]   F0000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000 mask F80000000 write-back
[    0.000000]   1 base 07FF00000 mask FFFF00000 uncachable
[    0.000000]   2 disabled
[    0.000000]   3 disabled
[    0.000000]   4 disabled
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] e820 update range: 0000000000001000 - 0000000000006000 (usable) ==> (reserved)
[    0.000000] Scanning 1 areas for low memory corruption
[    0.000000] modified physical RAM map:
[    0.000000]  modified: 0000000000000000 - 0000000000001000 (usable)
[    0.000000]  modified: 0000000000001000 - 0000000000006000 (reserved)
[    0.000000]  modified: 0000000000006000 - 000000000009f000 (usable)
[    0.000000]  modified: 000000000009f000 - 00000000000a0000 (reserved)
[    0.000000]  modified: 0000000000100000 - 000000007fe5a800 (usable)
[    0.000000]  modified: 000000007fe5a800 - 0000000080000000 (reserved)
[    0.000000]  modified: 00000000f8000000 - 00000000fc000000 (reserved)
[    0.000000]  modified: 00000000fec00000 - 00000000fec10000 (reserved)
[    0.000000]  modified: 00000000fed18000 - 00000000fed1c000 (reserved)
[    0.000000]  modified: 00000000fed20000 - 00000000fed90000 (reserved)
[    0.000000]  modified: 00000000feda0000 - 00000000feda6000 (reserved)
[    0.000000]  modified: 00000000fee00000 - 00000000fee10000 (reserved)
[    0.000000]  modified: 00000000ffe00000 - 0000000100000000 (reserved)
[    0.000000] initial memory mapped : 0 - 20000000
[    0.000000] init_memory_mapping: 0000000000000000-000000007fe5a000
[    0.000000] NX (Execute Disable) protection: active
[    0.000000]  0000000000 - 007fe00000 page 2M
[    0.000000]  007fe00000 - 007fe5a000 page 4k
[    0.000000] kernel direct mapping tables up to 7fe5a000 @ 8000-c000
[    0.000000] RAMDISK: 377ee000 - 37fef8aa
[    0.000000] ACPI: RSDP 00000000000fbb10 00024 (v02 DELL  )
[    0.000000] ACPI: XSDT 000000007fe5d200 00064 (v01 DELL    M08     27D8071C ASL  00000061)
[    0.000000] ACPI: FACP 000000007fe5d09c 000F4 (v04 DELL    M08     27D8071C ASL  00000061)
[    0.000000] ACPI: DSDT 000000007fe5d800 0614C (v02 INT430 SYSFexxx 00001001 INTL 20050624)
[    0.000000] ACPI: FACS 000000007fe6c000 00040
[    0.000000] ACPI: HPET 000000007fe5d300 00038 (v01 DELL    M08     00000001 ASL  00000061)
[    0.000000] ACPI: APIC 000000007fe5d400 00068 (v01 DELL    M08     27D8071C ASL  00000047)
[    0.000000] ACPI: ASF! 000000007fe5d000 0007E (v32 DELL    M08     27D8071C ASL  00000061)
[    0.000000] ACPI: MCFG 000000007fe5d3c0 0003E (v16 DELL    M08     27D8071C ASL  00000061)
[    0.000000] ACPI: TCPA 000000007fe5d700 00032 (v01                 00000000 ASL  00000000)
[    0.000000] ACPI: SLIC 000000007fe5d49c 00176 (v01 DELL    M08     27D8071C ASL  00000061)
[    0.000000] ACPI: SSDT 000000007fe5b9c0 004CC (v01  PmRef    CpuPm 00003000 INTL 20050624)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] No NUMA configuration found
[    0.000000] Faking a node at 0000000000000000-000000007fe5a000
[    0.000000] Bootmem setup node 0 0000000000000000-000000007fe5a000
[    0.000000]   NODE_DATA [000000000000a000 - 000000000000efff]
[    0.000000]   bootmap [000000000000f000 -  000000000001efcf] pages 10
[    0.000000] (7 early reservations) ==> bootmem [0000000000 - 007fe5a000]
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
[    0.000000]   #1 [0000006000 - 0000008000]       TRAMPOLINE ==> [0000006000 - 0000008000]
[    0.000000]   #2 [0001000000 - 00019e8c8c]    TEXT DATA BSS ==> [0001000000 - 00019e8c8c]
[    0.000000]   #3 [00377ee000 - 0037fef8aa]          RAMDISK ==> [00377ee000 - 0037fef8aa]
[    0.000000]   #4 [000009f000 - 0000100000]    BIOS reserved ==> [000009f000 - 0000100000]
[    0.000000]   #5 [00019e9000 - 00019e91ec]              BRK ==> [00019e9000 - 00019e91ec]
[    0.000000]   #6 [0000008000 - 000000a000]          PGTABLE ==> [0000008000 - 000000a000]
[    0.000000]  [ffffea0000000000-ffffea0001bfffff] PMD -> [ffff880001e00000-ffff8800039fffff] on node 0
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000000 -> 0x00001000
[    0.000000]   DMA32    0x00001000 -> 0x00100000
[    0.000000]   Normal   0x00100000 -> 0x00100000
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[3] active PFN ranges
[    0.000000]     0: 0x00000000 -> 0x00000001
[    0.000000]     0: 0x00000006 -> 0x0000009f
[    0.000000]     0: 0x00000100 -> 0x0007fe5a
[    0.000000] On node 0 totalpages: 523764
[    0.000000]   DMA zone: 56 pages used for memmap
[    0.000000]   DMA zone: 102 pages reserved
[    0.000000]   DMA zone: 3836 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 7107 pages used for memmap
[    0.000000]   DMA32 zone: 512663 pages, LIFO batch:31
[    0.000000] ACPI: PM-Timer IO Port: 0x1008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000
[    0.000000] SMP: Allowing 2 CPUs, 0 hotplug CPUs
[    0.000000] nr_irqs_gsi: 24
[    0.000000] PM: Registered nosave memory: 0000000000001000 - 0000000000006000
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 80000000 (gap: 80000000:78000000)
[    0.000000] NR_CPUS:64 nr_cpumask_bits:64 nr_cpu_ids:2 nr_node_ids:1
[    0.000000] PERCPU: Embedded 30 pages at ffff8800019fa000, static data 90720 bytes
[    0.000000] Built 1 zonelists in Node order, mobility grouping on.  Total pages: 516499
[    0.000000] Policy zone: DMA32
[    0.000000] Kernel command line: BOOT_IMAGE=/vmlinuz-2.6.31-20-generic root=UUID=9a1cf013-ba9d-42c5-a7ee-42a544c9d19d ro quiet splash
[    0.000000] PID hash table entries: 4096 (order: 12, 32768 bytes)
[    0.000000] Initializing CPU#0
[    0.000000] Checking aperture...
[    0.000000] No AGP bridge found
[    0.000000] Calgary: detecting Calgary via BIOS EBDA area
[    0.000000] Calgary: Unable to locate Rio Grande table in EBDA - bailing!
[    0.000000] Memory: 2047624k/2095464k available (5328k kernel code, 408k absent, 47432k reserved, 3013k data, 664k init)
[    0.000000] SLUB: Genslabs=14, HWalign=64, Order=0-3, MinObjects=0, CPUs=2, Nodes=1
[    0.000000] NR_IRQS:4352 nr_irqs:424
[    0.000000] Extended CMOS year: 2000
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 1994.205 MHz processor.
[    0.002201] Console: colour VGA+ 80x25
[    0.002205] console [tty0] enabled
[    0.010000] allocated 20971520 bytes of page_cgroup
[    0.010000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.010000] hpet clockevent registered
[    0.010000] HPET: 3 timers in total, 0 timers will be used for per-cpu timer
[    0.010000] Calibrating delay loop (skipped), value calculated using timer frequency.. 3988.41 BogoMIPS (lpj=19942050)
[    0.010000] Security Framework initialized
[    0.010000] AppArmor: AppArmor initialized
[    0.010000] Dentry cache hash table entries: 262144 (order: 9, 2097152 bytes)
[    0.010000] Inode-cache hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.010000] Mount-cache hash table entries: 256
[    0.010000] Initializing cgroup subsys ns
[    0.010000] Initializing cgroup subsys cpuacct
[    0.010000] Initializing cgroup subsys memory
[    0.010000] Initializing cgroup subsys freezer
[    0.010000] Initializing cgroup subsys net_cls
[    0.010000] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.010000] CPU: L2 cache: 4096K
[    0.010000] CPU 0/0x0 -> Node 0
[    0.010000] CPU: Physical Processor ID: 0
[    0.010000] CPU: Processor Core ID: 0
[    0.010000] mce: CPU supports 6 MCE banks
[    0.010000] CPU0: Thermal monitoring enabled (TM2)
[    0.010000] using mwait in idle threads.
[    0.010000] Performance Counters: Core2 events, Intel PMU driver.
[    0.010000] ... version:                 2
[    0.010000] ... bit width:               40
[    0.010000] ... generic counters:        2
[    0.010000] ... value mask:              000000ffffffffff
[    0.010000] ... max period:              000000007fffffff
[    0.010000] ... fixed-purpose counters:  3
[    0.010000] ... counter mask:            0000000700000003
[    0.010000] ACPI: Core revision 20090521
[    0.016276] Setting APIC routing to flat
[    0.016661] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.116678] CPU0: Intel(R) Core(TM)2 Duo CPU     T7300  @ 2.00GHz stepping 0a
[    0.120000] Booting processor 1 APIC 0x1 ip 0x6000
[    0.010000] Initializing CPU#1
[    0.010000] Calibrating delay using timer specific routine.. 3988.88 BogoMIPS (lpj=19944404)
[    0.010000] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.010000] CPU: L2 cache: 4096K
[    0.010000] CPU 1/0x1 -> Node 0
[    0.010000] CPU: Physical Processor ID: 0
[    0.010000] CPU: Processor Core ID: 1
[    0.010000] mce: CPU supports 6 MCE banks
[    0.010000] CPU1: Thermal monitoring enabled (TM2)
[    0.010000] x86 PAT enabled: cpu 1, old 0x7040600070406, new 0x7010600070106
[    0.271503] CPU1: Intel(R) Core(TM)2 Duo CPU     T7300  @ 2.00GHz stepping 0a
[    0.271514] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
[    0.280022] Brought up 2 CPUs
[    0.280025] Total of 2 processors activated (7977.29 BogoMIPS).
[    0.280083] CPU0 attaching sched-domain:
[    0.280087]  domain 0: span 0-1 level MC
[    0.280089]   groups: 0 1
[    0.280095] CPU1 attaching sched-domain:
[    0.280097]  domain 0: span 0-1 level MC
[    0.280099]   groups: 1 0
[    0.280176] Booting paravirtualized kernel on bare hardware
[    0.280176] regulator: core version 0.5
[    0.280176] Time: 10:30:21  Date: 02/09/10
[    0.280176] NET: Registered protocol family 16
[    0.280226] ACPI: bus type pci registered
[    0.280299] PCI: MCFG configuration 0: base f8000000 segment 0 buses 0 - 63
[    0.280302] PCI: MCFG area at f8000000 reserved in E820
[    0.281162] PCI: Using MMCONFIG at f8000000 - fbffffff
[    0.281164] PCI: Using configuration type 1 for base access
[    0.282053] bio: create slab <bio-0> at 0
[    0.282053] ACPI: EC: Look up EC in DSDT
[    0.282053] ACPI: BIOS _OSI(Linux) query ignored
[    0.344225] ACPI: SSDT 000000007fe6c080 00043 (v01  LMPWR  DELLLOM 00001001 INTL 20050624)
[    0.360045] ACPI: Interpreter enabled
[    0.360049] ACPI: (supports S0 S3 S4 S5)
[    0.360068] ACPI: Using IOAPIC for interrupt routing
[    0.523478] ACPI: ACPI Dock Station Driver: 3 docks/bays found
[    0.541474] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.541587] pci 0000:00:01.0: PME# supported from D0 D3hot D3cold
[    0.541591] pci 0000:00:01.0: PME# disabled
[    0.541685] pci 0000:00:1a.0: reg 20 io port: [0x6f20-0x6f3f]
[    0.541754] pci 0000:00:1a.1: reg 20 io port: [0x6f00-0x6f1f]
[    0.541831] pci 0000:00:1a.7: reg 10 32bit mmio: [0xfed1c400-0xfed1c7ff]
[    0.541899] pci 0000:00:1a.7: PME# supported from D0 D3hot D3cold
[    0.541905] pci 0000:00:1a.7: PME# disabled
[    0.541963] pci 0000:00:1b.0: reg 10 64bit mmio: [0xf6ffc000-0xf6ffffff]
[    0.542028] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    0.542033] pci 0000:00:1b.0: PME# disabled
[    0.542125] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    0.542130] pci 0000:00:1c.0: PME# disabled
[    0.542225] pci 0000:00:1c.1: PME# supported from D0 D3hot D3cold
[    0.542231] pci 0000:00:1c.1: PME# disabled
[    0.542330] pci 0000:00:1c.5: PME# supported from D0 D3hot D3cold
[    0.542335] pci 0000:00:1c.5: PME# disabled
[    0.542405] pci 0000:00:1d.0: reg 20 io port: [0x6f80-0x6f9f]
[    0.542474] pci 0000:00:1d.1: reg 20 io port: [0x6f60-0x6f7f]
[    0.542542] pci 0000:00:1d.2: reg 20 io port: [0x6f40-0x6f5f]
[    0.542617] pci 0000:00:1d.7: reg 10 32bit mmio: [0xfed1c000-0xfed1c3ff]
[    0.542684] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
[    0.542690] pci 0000:00:1d.7: PME# disabled
[    0.542868] pci 0000:00:1f.0: quirk: region 1000-107f claimed by ICH6 ACPI/GPIO/TCO
[    0.542872] pci 0000:00:1f.0: quirk: region 1080-10bf claimed by ICH6 GPIO
[    0.542877] pci 0000:00:1f.0: ICH7 LPC Generic IO decode 1 PIO at 0900 (mask 007f)
[    0.542883] pci 0000:00:1f.0: ICH7 LPC Generic IO decode 3 PIO at 0c80 (mask 003f)
[    0.542940] pci 0000:00:1f.1: reg 10 io port: [0x1f0-0x1f7]
[    0.542948] pci 0000:00:1f.1: reg 14 io port: [0x3f4-0x3f7]
[    0.542956] pci 0000:00:1f.1: reg 18 io port: [0x170-0x177]
[    0.542965] pci 0000:00:1f.1: reg 1c io port: [0x374-0x377]
[    0.542973] pci 0000:00:1f.1: reg 20 io port: [0x6fa0-0x6faf]
[    0.543033] pci 0000:00:1f.2: reg 10 io port: [0x6eb0-0x6eb7]
[    0.543041] pci 0000:00:1f.2: reg 14 io port: [0x6eb8-0x6ebb]
[    0.543049] pci 0000:00:1f.2: reg 18 io port: [0x6ec0-0x6ec7]
[    0.543058] pci 0000:00:1f.2: reg 1c io port: [0x6ec8-0x6ecb]
[    0.543066] pci 0000:00:1f.2: reg 20 io port: [0x6ee0-0x6eef]
[    0.543074] pci 0000:00:1f.2: reg 24 io port: [0xeff0-0xefff]
[    0.543106] pci 0000:00:1f.2: PME# supported from D3hot
[    0.543111] pci 0000:00:1f.2: PME# disabled
[    0.543140] pci 0000:00:1f.3: reg 10 32bit mmio: [0xf6ffbf00-0xf6ffbfff]
[    0.543166] pci 0000:00:1f.3: reg 20 io port: [0x10c0-0x10df]
[    0.543249] pci 0000:01:00.0: reg 10 32bit mmio: [0xf5000000-0xf5ffffff]
[    0.543265] pci 0000:01:00.0: reg 14 64bit mmio: [0xe0000000-0xefffffff]
[    0.543282] pci 0000:01:00.0: reg 1c 64bit mmio: [0xf2000000-0xf3ffffff]
[    0.543291] pci 0000:01:00.0: reg 24 io port: [0xdf00-0xdf7f]
[    0.543301] pci 0000:01:00.0: reg 30 32bit mmio: [0x000000-0x01ffff]
[    0.543417] pci 0000:00:01.0: bridge io port: [0xd000-0xdfff]
[    0.543420] pci 0000:00:01.0: bridge 32bit mmio: [0xf2000000-0xf6efffff]
[    0.543425] pci 0000:00:01.0: bridge 64bit mmio pref: [0xe0000000-0xefffffff]
[    0.543564] pci 0000:0c:00.0: reg 10 32bit mmio: [0xf1ffc000-0xf1ffffff]
[    0.543665] pci 0000:0c:00.0: supports D1 D2
[    0.543750] pci 0000:00:1c.1: bridge 32bit mmio: [0xf1f00000-0xf1ffffff]
[    0.543849] pci 0000:09:00.0: reg 10 64bit mmio: [0xf1ef0000-0xf1efffff]
[    0.543960] pci 0000:09:00.0: PME# supported from D3hot D3cold
[    0.543966] pci 0000:09:00.0: PME# disabled
[    0.544052] pci 0000:00:1c.5: bridge 32bit mmio: [0xf1e00000-0xf1efffff]
[    0.544112] pci 0000:03:01.0: reg 10 32bit mmio: [0x000000-0x000fff]
[    0.544142] pci 0000:03:01.0: supports D1 D2
[    0.544144] pci 0000:03:01.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.544150] pci 0000:03:01.0: PME# disabled
[    0.544200] pci 0000:03:01.4: reg 10 32bit mmio: [0xf1dff000-0xf1dfffff]
[    0.544208] pci 0000:03:01.4: reg 14 32bit mmio: [0xf1dfe800-0xf1dfefff]
[    0.544262] pci 0000:03:01.4: supports D1 D2
[    0.544264] pci 0000:03:01.4: PME# supported from D0 D1 D2 D3hot D3cold
[    0.544270] pci 0000:03:01.4: PME# disabled
[    0.544342] pci 0000:00:1e.0: transparent bridge
[    0.544350] pci 0000:00:1e.0: bridge 32bit mmio: [0xf1d00000-0xf1dfffff]
[    0.544414] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.544686] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCIE._PRT]
[    0.544831] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.AGP_._PRT]
[    0.544901] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP01._PRT]
[    0.544978] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP02._PRT]
[    0.545063] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP06._PRT]
[    0.600259] ACPI: PCI Interrupt Link [LNKA] (IRQs 9 10 11) *5
[    0.600388] ACPI: PCI Interrupt Link [LNKB] (IRQs 5 7) *3
[    0.600514] ACPI: PCI Interrupt Link [LNKC] (IRQs 9 *10 11)
[    0.600641] ACPI: PCI Interrupt Link [LNKD] (IRQs 5 7 *9 10 11)
[    0.600768] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)
[    0.600898] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 9 *10 11 12 14 15)
[    0.601027] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 *9 10 11 12 14 15)
[    0.601143] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
[    0.601333] SCSI subsystem initialized
[    0.601355] libata version 3.00 loaded.
[    0.601355] usbcore: registered new interface driver usbfs
[    0.601355] usbcore: registered new interface driver hub
[    0.601355] usbcore: registered new device driver usb
[    0.601355] ACPI: WMI: Mapper loaded
[    0.601355] PCI: Using ACPI for IRQ routing
[    0.630007] Bluetooth: Core ver 2.15
[    0.630022] NET: Registered protocol family 31
[    0.630022] Bluetooth: HCI device and connection manager initialized
[    0.630022] Bluetooth: HCI socket layer initialized
[    0.630022] NetLabel: Initializing
[    0.630022] NetLabel:  domain hash size = 128
[    0.630022] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.630034] NetLabel:  unlabeled traffic allowed by default
[    0.630080] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[    0.630085] hpet0: 3 comparators, 64-bit 14.318180 MHz counter
[    0.650010] Switched to high resolution mode on CPU 0
[    0.651533] Switched to high resolution mode on CPU 1
[    0.670011] pnp: PnP ACPI init
[    0.670020] ACPI: bus type pnp registered
[    0.738549] pnp 00:0c: io resource (0x1000-0x1005) overlaps 0000:00:1f.0 BAR 13 (0x1000-0x107f), disabling
[    0.738554] pnp 00:0c: io resource (0x1008-0x100f) overlaps 0000:00:1f.0 BAR 13 (0x1000-0x107f), disabling
[    0.738647] pnp 00:0d: io resource (0x1006-0x1007) overlaps 0000:00:1f.0 BAR 13 (0x1000-0x107f), disabling
[    0.738650] pnp 00:0d: io resource (0x100a-0x1059) overlaps 0000:00:1f.0 BAR 13 (0x1000-0x107f), disabling
[    0.738654] pnp 00:0d: io resource (0x1060-0x107f) overlaps 0000:00:1f.0 BAR 13 (0x1000-0x107f), disabling
[    0.738657] pnp 00:0d: io resource (0x1010-0x102f) overlaps 0000:00:1f.0 BAR 13 (0x1000-0x107f), disabling
[    0.759874] pnp: PnP ACPI: found 15 devices
[    0.759877] ACPI: ACPI bus type pnp unregistered
[    0.759888] system 00:05: ioport range 0xc80-0xcaf has been reserved
[    0.759891] system 00:05: ioport range 0xcc0-0xcff could not be reserved
[    0.759898] system 00:08: iomem range 0xfed00000-0xfed003ff has been reserved
[    0.759904] system 00:0b: ioport range 0xcb0-0xcbb has been reserved
[    0.759907] system 00:0b: iomem range 0xfed40000-0xfed44fff has been reserved
[    0.759913] system 00:0c: ioport range 0x900-0x97f has been reserved
[    0.759915] system 00:0c: ioport range 0x4d0-0x4d1 has been reserved
[    0.759921] system 00:0d: ioport range 0xf400-0xf4fe has been reserved
[    0.759924] system 00:0d: ioport range 0x1080-0x10bf has been reserved
[    0.759927] system 00:0d: ioport range 0x10c0-0x10df has been reserved
[    0.759930] system 00:0d: ioport range 0x809-0x809 has been reserved
[    0.759935] system 00:0e: iomem range 0x0-0x9efff could not be reserved
[    0.759939] system 00:0e: iomem range 0x9f000-0x9ffff could not be reserved
[    0.759941] system 00:0e: iomem range 0xc0000-0xcffff has been reserved
[    0.759944] system 00:0e: iomem range 0xe0000-0xfffff has been reserved
[    0.759947] system 00:0e: iomem range 0x100000-0x7fe5a7ff could not be reserved
[    0.759950] system 00:0e: iomem range 0x7fe5a800-0x7fefffff has been reserved
[    0.759953] system 00:0e: iomem range 0x7ff00000-0x7fffffff has been reserved
[    0.759956] system 00:0e: iomem range 0x7ff00000-0x806fffff could not be reserved
[    0.759959] system 00:0e: iomem range 0xffe00000-0xffffffff has been reserved
[    0.759962] system 00:0e: iomem range 0xffa00000-0xffbfffff has been reserved
[    0.759965] system 00:0e: iomem range 0xfec00000-0xfec0ffff could not be reserved
[    0.759967] system 00:0e: iomem range 0xfee00000-0xfee0ffff has been reserved
[    0.759970] system 00:0e: iomem range 0xfed20000-0xfed3ffff has been reserved
[    0.759973] system 00:0e: iomem range 0xfed45000-0xfed8ffff has been reserved
[    0.759976] system 00:0e: iomem range 0xfeda0000-0xfeda3fff has been reserved
[    0.759979] system 00:0e: iomem range 0xfeda4000-0xfeda4fff has been reserved
[    0.759982] system 00:0e: iomem range 0xfeda5000-0xfeda5fff has been reserved
[    0.759984] system 00:0e: iomem range 0xfeda6000-0xfeda6fff has been reserved
[    0.759987] system 00:0e: iomem range 0xfed18000-0xfed1bfff has been reserved
[    0.759990] system 00:0e: iomem range 0xf8000000-0xfbffffff has been reserved
[    0.764685] AppArmor: AppArmor Filesystem Enabled
[    0.764760] pci 0000:00:01.0: PCI bridge, secondary bus 0000:01
[    0.764763] pci 0000:00:01.0:   IO window: 0xd000-0xdfff
[    0.764768] pci 0000:00:01.0:   MEM window: 0xf2000000-0xf6efffff
[    0.764771] pci 0000:00:01.0:   PREFETCH window: 0x000000e0000000-0x000000efffffff
[    0.764777] pci 0000:00:1c.0: PCI bridge, secondary bus 0000:0b
[    0.764779] pci 0000:00:1c.0:   IO window: disabled
[    0.764785] pci 0000:00:1c.0:   MEM window: disabled
[    0.764790] pci 0000:00:1c.0:   PREFETCH window: disabled
[    0.764795] pci 0000:00:1c.1: PCI bridge, secondary bus 0000:0c
[    0.764797] pci 0000:00:1c.1:   IO window: disabled
[    0.764803] pci 0000:00:1c.1:   MEM window: 0xf1f00000-0xf1ffffff
[    0.764808] pci 0000:00:1c.1:   PREFETCH window: disabled
[    0.764813] pci 0000:00:1c.5: PCI bridge, secondary bus 0000:09
[    0.764815] pci 0000:00:1c.5:   IO window: disabled
[    0.764822] pci 0000:00:1c.5:   MEM window: 0xf1e00000-0xf1efffff
[    0.764826] pci 0000:00:1c.5:   PREFETCH window: disabled
[    0.764837] pci 0000:03:01.0: CardBus bridge, secondary bus 0000:04
[    0.764840] pci 0000:03:01.0:   IO window: 0x002000-0x0020ff
[    0.764845] pci 0000:03:01.0:   IO window: 0x002400-0x0024ff
[    0.764851] pci 0000:03:01.0:   PREFETCH window: 0x80000000-0x83ffffff
[    0.764856] pci 0000:03:01.0:   MEM window: 0x84000000-0x87ffffff
[    0.764862] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:03
[    0.764866] pci 0000:00:1e.0:   IO window: 0x2000-0x2fff
[    0.764872] pci 0000:00:1e.0:   MEM window: 0xf1d00000-0xf1dfffff
[    0.764877] pci 0000:00:1e.0:   PREFETCH window: 0x80000000-0x83ffffff
[    0.764888]   alloc irq_desc for 16 on node 0
[    0.764890]   alloc kstat_irqs on node 0
[    0.764895] pci 0000:00:01.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.764900] pci 0000:00:01.0: setting latency timer to 64
[    0.764908] pci 0000:00:1c.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.764913] pci 0000:00:1c.0: setting latency timer to 64
[    0.764922]   alloc irq_desc for 17 on node 0
[    0.764924]   alloc kstat_irqs on node 0
[    0.764927] pci 0000:00:1c.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    0.764932] pci 0000:00:1c.1: setting latency timer to 64
[    0.764941] pci 0000:00:1c.5: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    0.764947] pci 0000:00:1c.5: setting latency timer to 64
[    0.764955] pci 0000:00:1e.0: setting latency timer to 64
[    0.764965] pci 0000:03:01.0: enabling device (0000 -> 0003)
[    0.764969]   alloc irq_desc for 19 on node 0
[    0.764971]   alloc kstat_irqs on node 0
[    0.764974] pci 0000:03:01.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    0.764983] pci_bus 0000:00: resource 0 io:  [0x00-0xffff]
[    0.764986] pci_bus 0000:00: resource 1 mem: [0x000000-0xffffffffffffffff]
[    0.764989] pci_bus 0000:01: resource 0 io:  [0xd000-0xdfff]
[    0.764991] pci_bus 0000:01: resource 1 mem: [0xf2000000-0xf6efffff]
[    0.764994] pci_bus 0000:01: resource 2 pref mem [0xe0000000-0xefffffff]
[    0.764996] pci_bus 0000:0c: resource 1 mem: [0xf1f00000-0xf1ffffff]
[    0.764999] pci_bus 0000:09: resource 1 mem: [0xf1e00000-0xf1efffff]
[    0.765001] pci_bus 0000:03: resource 0 io:  [0x2000-0x2fff]
[    0.765004] pci_bus 0000:03: resource 1 mem: [0xf1d00000-0xf1dfffff]
[    0.765006] pci_bus 0000:03: resource 2 pref mem [0x80000000-0x83ffffff]
[    0.765009] pci_bus 0000:03: resource 3 io:  [0x00-0xffff]
[    0.765011] pci_bus 0000:03: resource 4 mem: [0x000000-0xffffffffffffffff]
[    0.765014] pci_bus 0000:04: resource 0 io:  [0x2000-0x20ff]
[    0.765016] pci_bus 0000:04: resource 1 io:  [0x2400-0x24ff]
[    0.765018] pci_bus 0000:04: resource 2 pref mem [0x80000000-0x83ffffff]
[    0.765021] pci_bus 0000:04: resource 3 mem: [0x84000000-0x87ffffff]
[    0.765052] NET: Registered protocol family 2
[    0.765187] IP route cache hash table entries: 65536 (order: 7, 524288 bytes)
[    0.765980] TCP established hash table entries: 262144 (order: 10, 4194304 bytes)
[    0.767655] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[    0.768180] TCP: Hash tables configured (established 262144 bind 65536)
[    0.768183] TCP reno registered
[    0.768300] NET: Registered protocol family 1
[    0.768374] Trying to unpack rootfs image as initramfs...
[    0.965270] Freeing initrd memory: 8198k freed
[    0.969675] Scanning for low memory corruption every 60 seconds
[    0.969827] audit: initializing netlink socket (disabled)
[    0.969846] type=2000 audit(1265711421.960:1): initialized
[    0.979851] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    0.981294] VFS: Disk quotas dquot_6.5.2
[    0.981350] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    0.981942] fuse init (API version 7.12)
[    0.982025] msgmni has been set to 4015
[    0.982227] alg: No test for stdrng (krng)
[    0.982240] io scheduler noop registered
[    0.982243] io scheduler anticipatory registered
[    0.982245] io scheduler deadline registered
[    0.982287] io scheduler cfq registered (default)
[    0.982458] pci 0000:01:00.0: Boot video device
[    0.982602]   alloc irq_desc for 24 on node 0
[    0.982605]   alloc kstat_irqs on node 0
[    0.982614] pcieport-driver 0000:00:01.0: irq 24 for MSI/MSI-X
[    0.982620] pcieport-driver 0000:00:01.0: setting latency timer to 64
[    0.982776]   alloc irq_desc for 25 on node 0
[    0.982778]   alloc kstat_irqs on node 0
[    0.982787] pcieport-driver 0000:00:1c.0: irq 25 for MSI/MSI-X
[    0.982799] pcieport-driver 0000:00:1c.0: setting latency timer to 64
[    0.982986]   alloc irq_desc for 26 on node 0
[    0.982988]   alloc kstat_irqs on node 0
[    0.982997] pcieport-driver 0000:00:1c.1: irq 26 for MSI/MSI-X
[    0.983008] pcieport-driver 0000:00:1c.1: setting latency timer to 64
[    0.983191]   alloc irq_desc for 27 on node 0
[    0.983193]   alloc kstat_irqs on node 0
[    0.983202] pcieport-driver 0000:00:1c.5: irq 27 for MSI/MSI-X
[    0.983213] pcieport-driver 0000:00:1c.5: setting latency timer to 64
[    0.983333] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.983455] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.983621] ACPI: AC Adapter [AC] (on-line)
[    0.983699] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input0
[    0.984261] ACPI: Lid Switch [LID]
[    0.984307] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1
[    0.984314] ACPI: Power Button [PBTN]
[    0.984354] input: Sleep Button as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input2
[    0.984357] ACPI: Sleep Button [SBTN]
[    0.985037] ACPI: SSDT 000000007fe5c4f6 00286 (v01  PmRef  Cpu0Ist 00003000 INTL 20050624)
[    0.985510] ACPI: SSDT 000000007fe5be8c 005E5 (v01  PmRef  Cpu0Cst 00003001 INTL 20050624)
[    0.985876] Monitor-Mwait will be used to enter C-1 state
[    0.985903] Monitor-Mwait will be used to enter C-2 state
[    0.985927] Monitor-Mwait will be used to enter C-3 state
[    0.985934] Marking TSC unstable due to TSC halts in idle
[    0.985954] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[    0.985977] processor LNXCPU:00: registered as cooling_device0
[    0.985981] ACPI: Processor [CPU0] (supports 8 throttling states)
[    0.986328] ACPI: SSDT 000000007fe5c77c 000C4 (v01  PmRef  Cpu1Ist 00003000 INTL 20050624)
[    0.986641] ACPI: SSDT 000000007fe5c471 00085 (v01  PmRef  Cpu1Cst 00003000 INTL 20050624)
[    0.987124] ACPI: CPU1 (power states: C1[C1] C2[C2] C3[C3])
[    0.987144] processor LNXCPU:01: registered as cooling_device1
[    0.987148] ACPI: Processor [CPU1] (supports 8 throttling states)
[    1.041746] thermal LNXTHERM:01: registered as thermal_zone0
[    1.041754] ACPI: Thermal Zone [THM] (70 C)
[    1.042907] Linux agpgart interface v0.103
[    1.042916] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    1.043047] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    1.043409] 00:09: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    1.044412] brd: module loaded
[    1.044862] loop: module loaded
[    1.044930] input: Macintosh mouse button emulation as /devices/virtual/input/input3
[    1.074602] ata_piix 0000:00:1f.1: version 2.13
[    1.074614] ata_piix 0000:00:1f.1: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.074653] ata_piix 0000:00:1f.1: setting latency timer to 64
[    1.074731] ACPI: Battery Slot [BAT0] (battery present)
[    1.074782] ACPI: Battery Slot [BAT1] (battery absent)
[    1.074798] scsi0 : ata_piix
[    1.074886] scsi1 : ata_piix
[    1.077158] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0x6fa0 irq 14
[    1.077161] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x6fa8 irq 15
[    1.077226] ata2: port disabled. ignoring.
[    1.077399]   alloc irq_desc for 18 on node 0
[    1.077401]   alloc kstat_irqs on node 0
[    1.077406] ata_piix 0000:00:1f.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    1.077412] ata_piix 0000:00:1f.2: MAP [ P0 P2 P1 P3 ]
[    1.230062] ata_piix 0000:00:1f.2: setting latency timer to 64
[    1.230269] scsi2 : ata_piix
[    1.230330] scsi3 : ata_piix
[    1.232458] ata3: SATA max UDMA/133 cmd 0x6eb0 ctl 0x6eb8 bmdma 0x6ee0 irq 18
[    1.232466] ata4: SATA max UDMA/133 cmd 0x6ec0 ctl 0x6ec8 bmdma 0x6ee8 irq 18
[    1.233310] Fixed MDIO Bus: probed
[    1.233344] PPP generic driver version 2.4.2
[    1.233426] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    1.233492]   alloc irq_desc for 22 on node 0
[    1.233494]   alloc kstat_irqs on node 0
[    1.233499] ehci_hcd 0000:00:1a.7: PCI INT C -> GSI 22 (level, low) -> IRQ 22
[    1.233511] ehci_hcd 0000:00:1a.7: setting latency timer to 64
[    1.233515] ehci_hcd 0000:00:1a.7: EHCI Host Controller
[    1.233546] ehci_hcd 0000:00:1a.7: new USB bus registered, assigned bus number 1
[    1.237448] ehci_hcd 0000:00:1a.7: debug port 1
[    1.237455] ehci_hcd 0000:00:1a.7: cache line size of 32 is not supported
[    1.237471] ehci_hcd 0000:00:1a.7: irq 22, io mem 0xfed1c400
[    1.252888] ata1.00: ATAPI: HL-DT-ST DVD+/-RW GSA-T11N, A103, max UDMA/33
[    1.260017] ehci_hcd 0000:00:1a.7: USB 2.0 started, EHCI 1.00
[    1.260094] usb usb1: configuration #1 chosen from 1 choice
[    1.260121] hub 1-0:1.0: USB hub found
[    1.260129] hub 1-0:1.0: 4 ports detected
[    1.260222]   alloc irq_desc for 20 on node 0
[    1.260224]   alloc kstat_irqs on node 0
[    1.260228] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    1.260238] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    1.260241] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    1.260275] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 2
[    1.264182] ehci_hcd 0000:00:1d.7: debug port 1
[    1.264188] ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported
[    1.264201] ehci_hcd 0000:00:1d.7: irq 20, io mem 0xfed1c000
[    1.280015] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    1.280079] usb usb2: configuration #1 chosen from 1 choice
[    1.280107] hub 2-0:1.0: USB hub found
[    1.280113] hub 2-0:1.0: 6 ports detected
[    1.280180] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    1.280195] uhci_hcd: USB Universal Host Controller Interface driver
[    1.280272] uhci_hcd 0000:00:1a.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    1.280279] uhci_hcd 0000:00:1a.0: setting latency timer to 64
[    1.280283] uhci_hcd 0000:00:1a.0: UHCI Host Controller
[    1.280314] uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 3
[    1.280344] uhci_hcd 0000:00:1a.0: irq 20, io base 0x00006f20
[    1.280423] usb usb3: configuration #1 chosen from 1 choice
[    1.280450] hub 3-0:1.0: USB hub found
[    1.280458] hub 3-0:1.0: 2 ports detected
[    1.280533]   alloc irq_desc for 21 on node 0
[    1.280535]   alloc kstat_irqs on node 0
[    1.280540] uhci_hcd 0000:00:1a.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[    1.280546] uhci_hcd 0000:00:1a.1: setting latency timer to 64
[    1.280550] uhci_hcd 0000:00:1a.1: UHCI Host Controller
[    1.280577] uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus number 4
[    1.280613] uhci_hcd 0000:00:1a.1: irq 21, io base 0x00006f00
[    1.280694] usb usb4: configuration #1 chosen from 1 choice
[    1.280718] hub 4-0:1.0: USB hub found
[    1.280725] hub 4-0:1.0: 2 ports detected
[    1.280801] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    1.280808] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    1.280811] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    1.280839] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 5
[    1.280868] uhci_hcd 0000:00:1d.0: irq 20, io base 0x00006f80
[    1.280945] usb usb5: configuration #1 chosen from 1 choice
[    1.280969] hub 5-0:1.0: USB hub found
[    1.280977] hub 5-0:1.0: 2 ports detected
[    1.281053] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[    1.281060] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    1.281063] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    1.281090] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 6
[    1.281118] uhci_hcd 0000:00:1d.1: irq 21, io base 0x00006f60
[    1.281200] usb usb6: configuration #1 chosen from 1 choice
[    1.281224] hub 6-0:1.0: USB hub found
[    1.281230] hub 6-0:1.0: 2 ports detected
[    1.281311] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 22 (level, low) -> IRQ 22
[    1.281318] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    1.281322] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    1.281356] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 7
[    1.281384] uhci_hcd 0000:00:1d.2: irq 22, io base 0x00006f40
[    1.281461] usb usb7: configuration #1 chosen from 1 choice
[    1.281488] hub 7-0:1.0: USB hub found
[    1.281494] hub 7-0:1.0: 2 ports detected
[    1.281591] PNP: PS/2 Controller [PNP0303:KBC,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    1.284803] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.284807] serio: i8042 AUX port at 0x60,0x64 irq 12
[    1.284868] mice: PS/2 mouse device common for all mice
[    1.284974] rtc_cmos 00:03: RTC can wake from S4
[    1.285006] rtc_cmos 00:03: rtc core: registered rtc_cmos as rtc0
[    1.285039] rtc0: alarms up to one month, y3k, 114 bytes nvram, hpet irqs
[    1.285159] device-mapper: uevent: version 1.0.3
[    1.285242] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: [email]dm-devel@redhat.com[/email]
[    1.285309] device-mapper: multipath: version 1.1.0 loaded
[    1.285313] device-mapper: multipath round-robin: version 1.0.0 loaded
[    1.285554] cpuidle: using governor ladder
[    1.285671] cpuidle: using governor menu
[    1.286067] TCP cubic registered
[    1.286188] NET: Registered protocol family 10
[    1.286626] lo: Disabled Privacy Extensions
[    1.286915] NET: Registered protocol family 17
[    1.286933] Bluetooth: L2CAP ver 2.13
[    1.286935] Bluetooth: L2CAP socket layer initialized
[    1.286939] Bluetooth: SCO (Voice Link) ver 0.6
[    1.286942] Bluetooth: SCO socket layer initialized
[    1.286987] Bluetooth: RFCOMM TTY layer initialized
[    1.286990] Bluetooth: RFCOMM socket layer initialized
[    1.286992] Bluetooth: RFCOMM ver 1.11
[    1.287641] PM: Resume from disk failed.
[    1.287652] registered taskstats version 1
[    1.287774]   Magic number: 14:187:527
[    1.287827] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input4
[    1.287976] rtc_cmos 00:03: setting system clock to 2010-02-09 10:30:22 UTC (1265711422)
[    1.287979] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.287980] EDD information not available.
[    1.292950] ata1.00: configured for UDMA/33
[    1.306082] scsi 0:0:0:0: CD-ROM            HL-DT-ST DVD+-RW GSA-T11N A103 PQ: 0 ANSI: 5
[    1.310287] sr0: scsi3-mmc drive: 62x/62x writer cd/rw xa/form2 cdda tray
[    1.310290] Uniform CD-ROM driver Revision: 3.20
[    1.310368] sr 0:0:0:0: Attached scsi CD-ROM sr0
[    1.310410] sr 0:0:0:0: Attached scsi generic sg0 type 5
[    1.500144] Clocksource tsc unstable (delta = -192230488 ns)
[    1.700170] usb 1-3: new high speed USB device using ehci_hcd and address 3
[    1.853001] usb 1-3: configuration #1 chosen from 1 choice
[    1.853220] hub 1-3:1.0: USB hub found
[    1.853299] hub 1-3:1.0: 4 ports detected
[    1.940224] ata4.00: SATA link down (SStatus 0 SControl 300)
[    1.940249] ata4.01: SATA link down (SStatus 0 SControl 0)
[    2.090158] ata3.00: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    2.090179] ata3.01: SATA link down (SStatus 0 SControl 300)
[    2.110607] ata3.00: ATA-8: Hitachi HTS722012K9A300, DCCOC54P, max UDMA/133
[    2.110613] ata3.00: 234441648 sectors, multi 8: LBA48 NCQ (depth 0/32)
[    2.150626] ata3.00: configured for UDMA/133
[    2.150740] scsi 2:0:0:0: Direct-Access     ATA      Hitachi HTS72201 DCCO PQ: 0 ANSI: 5
[    2.150910] sd 2:0:0:0: Attached scsi generic sg1 type 0
[    2.150932] sd 2:0:0:0: [sda] 234441648 512-byte logical blocks: (120 GB/111 GiB)
[    2.150987] sd 2:0:0:0: [sda] Write Protect is off
[    2.150990] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    2.151013] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.151130]  sda: sda1 sda2 < sda5 sda6 sda7 > sda3
[    2.201303] sd 2:0:0:0: [sda] Attached SCSI disk
[    2.201343] Freeing unused kernel memory: 664k freed
[    2.201590] Write protecting the kernel read-only data: 7596k
[    2.356475] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A03:00/device:31/device:32/input/input5
[    2.356514] ACPI: Video Device [VID] (multi-head: yes  rom: no  post: no)
[    2.362023] tg3.c:v3.99 (April 20, 2009)
[    2.362044] tg3 0000:09:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    2.362054] tg3 0000:09:00.0: setting latency timer to 64
[    2.372838] usb 3-2: new full speed USB device using uhci_hcd and address 2
[    2.381841] tg3 0000:09:00.0: PME# disabled
[    2.404104] eth0: Tigon3 [partno(BCM95755m) rev a002] (PCI Express) MAC address 00:1c:23:3b:2e:d6
[    2.404108] eth0: attached PHY is 5755 (10/100/1000Base-T Ethernet) (WireSpeed[1])
[    2.404111] eth0: RXcsums[1] LinkChgREG[0] MIirq[0] ASF[0] TSOcap[1]
[    2.404113] eth0: dma_rwctrl[76180000] dma_mask[64-bit]
[    2.419631] ohci1394 0000:03:01.4: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    2.471128] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[19]  MMIO=[f1dff000-f1dff7ff]  Max Packet=[2048]  IR/IT contexts=[8/8]
[    2.574575] usb 3-2: configuration #1 chosen from 1 choice
[    2.850059] usb 4-2: new full speed USB device using uhci_hcd and address 2
[    3.058814] usb 4-2: configuration #1 chosen from 1 choice
[    3.342552] usb 7-1: new full speed USB device using uhci_hcd and address 2
[    3.497630] usb 7-1: configuration #1 chosen from 1 choice
[    3.499576] hub 7-1:1.0: USB hub found
[    3.501523] hub 7-1:1.0: 4 ports detected
[    3.600034] usb 1-3.2: new low speed USB device using ehci_hcd and address 5
[    3.715301] usb 1-3.2: configuration #1 chosen from 1 choice
[    3.734677] usbcore: registered new interface driver hiddev
[    3.736975] input: HID 413c:3010 as /devices/pci0000:00/0000:00:1a.7/usb1/1-3/1-3.2/1-3.2:1.0/input/input6
[    3.737048] generic-usb 0003:413C:3010.0001: input,hidraw0: USB HID v1.00 Mouse [HID 413c:3010] on usb-0000:00:1a.7-3.2/input0
[    3.737060] usbcore: registered new interface driver usbhid
[    3.737063] usbhid: v2.6:USB HID core driver
[    3.798930] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[354fc00024f17981]
[    3.834536] usb 7-1.2: new full speed USB device using uhci_hcd and address 3
[    3.956613] usb 7-1.2: configuration #1 chosen from 1 choice
[    4.033999] PM: Starting manual resume from disk
[    4.034004] PM: Resume from partition 8:7
[    4.034006] PM: Checking hibernation image.
[    4.034188] PM: Resume from disk failed.
[    4.039480] EXT4-fs (sda5): INFO: recovery required on readonly filesystem
[    4.039484] EXT4-fs (sda5): write access will be enabled during recovery
[    4.056109] EXT4-fs (sda5): barriers enabled
[    5.411821] kjournald2 starting: pid 482, dev sda5:8, commit interval 5 seconds
[    5.411965] EXT4-fs (sda5): delayed allocation enabled
[    5.411969] EXT4-fs: file extents enabled
[    5.412026] EXT4-fs: mballoc enabled
[    5.412047] EXT4-fs (sda5): recovery complete
[    5.412787] EXT4-fs (sda5): mounted filesystem with ordered data mode
[    5.947629] type=1505 audit(1265711427.152:2): operation="profile_load" pid=507 name=/usr/share/gdm/guest-session/Xsession
[    5.973666] type=1505 audit(1265711427.182:3): operation="profile_load" pid=508 name=/sbin/dhclient3
[    5.974463] type=1505 audit(1265711427.182:4): operation="profile_load" pid=508 name=/usr/lib/NetworkManager/nm-dhcp-client.action
[    5.974822] type=1505 audit(1265711427.182:5): operation="profile_load" pid=508 name=/usr/lib/connman/scripts/dhclient-script
[    6.010315] type=1505 audit(1265711427.222:6): operation="profile_load" pid=509 name=/usr/bin/evince
[    6.021102] type=1505 audit(1265711427.232:7): operation="profile_load" pid=509 name=/usr/bin/evince-previewer
[    6.030118] type=1505 audit(1265711427.242:8): operation="profile_load" pid=509 name=/usr/bin/evince-thumbnailer
[    6.071759] type=1505 audit(1265711427.282:9): operation="profile_load" pid=511 name=/usr/bin/freshclam
[    6.094902] type=1505 audit(1265711427.302:10): operation="profile_load" pid=512 name=/usr/bin/virt-aa-helper
[    6.106057] type=1505 audit(1265711427.312:11): operation="profile_load" pid=513 name=/usr/lib/cups/backend/cups-pdf
[    6.106865] type=1505 audit(1265711427.312:12): operation="profile_load" pid=513 name=/usr/sbin/cupsd
[    7.104487] Adding 2104472k swap on /dev/sda7.  Priority:-1 extents:1 across:2104472k 
[    7.565125] udev: starting version 147
[    8.066509] sr 0:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[    8.066517] sr 0:0:0:0: [sr0] Sense Key : Illegal Request [current] 
[    8.066524] Info fld=0x0
[    8.066527] sr 0:0:0:0: [sr0] Add. Sense: Logical block address out of range
[    8.066534] end_request: I/O error, dev sr0, sector 0
[    8.069682] sr 0:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[    8.069688] sr 0:0:0:0: [sr0] Sense Key : Illegal Request [current] 
[    8.069694] Info fld=0x0
[    8.069696] sr 0:0:0:0: [sr0] Add. Sense: Logical block address out of range
[    8.069703] end_request: I/O error, dev sr0, sector 0
[    8.753199] lp: driver loaded but no devices found
[    8.769139] parport_pc 00:0a: reported by Plug and Play ACPI
[    8.769220] parport0: PC-style at 0x378 (0x778), irq 7, dma 1 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
[    8.850271] lp0: using parport0 (interrupt-driven).
[    8.907022] dcdbas dcdbas: Dell Systems Management Base Driver (version 5.6.0-3.2)
[    8.910703] ppdev: user-space parallel port driver
[   10.312962] nvidia: module license 'NVIDIA' taints kernel.
[   10.312966] Disabling lock debugging due to kernel taint
[   10.426803] usbcore: registered new interface driver usbserial
[   10.426817] USB Serial support registered for generic
[   10.426873] usbcore: registered new interface driver usbserial_generic
[   10.426876] usbserial: USB Serial Driver core
[   10.569680] Bluetooth: Generic Bluetooth USB driver ver 0.5
[   10.569802] usbcore: registered new interface driver btusb
[   10.581756] lib80211: common routines for IEEE802.11 drivers
[   10.581759] lib80211_crypt: registered algorithm 'NULL'
[   10.581992] nvidia 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   10.582007] nvidia 0000:01:00.0: setting latency timer to 64
[   10.582144] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  185.18.36  Fri Aug 14 17:35:21 PDT 2009
[   10.587112] USB Serial support registered for GSM modem (1-port)
[   10.587170] option 4-2:1.0: GSM modem (1-port) converter detected
[   10.587250] usb 4-2: GSM modem (1-port) converter now attached to ttyUSB0
[   10.587265] option 4-2:1.1: GSM modem (1-port) converter detected
[   10.587310] usb 4-2: GSM modem (1-port) converter now attached to ttyUSB1
[   10.587333] usbcore: registered new interface driver option
[   10.587335] option: v0.7.2:USB Driver for GSM modems
[   10.604386] ip_tables: (C) 2000-2006 Netfilter Core Team
[   10.696265] input: Dell WMI hotkeys as /devices/virtual/input/input7
[   10.752617] yenta_cardbus 0000:03:01.0: CardBus bridge found [1028:01f9]
[   10.752645] yenta_cardbus 0000:03:01.0: O2: res at 0x94/0xD4: 00/ea
[   10.752647] yenta_cardbus 0000:03:01.0: O2: enabling read prefetch/write burst
[   10.901039] yenta_cardbus 0000:03:01.0: ISA IRQ mask 0x0c38, PCI irq 19
[   10.901045] yenta_cardbus 0000:03:01.0: Socket status: 30000006
[   10.901050] pci_bus 0000:03: Raising subordinate bus# of parent bus (#03) from #04 to #07
[   10.901066] yenta_cardbus 0000:03:01.0: pcmcia: parent PCI bridge I/O window: 0x2000 - 0x2fff
[   10.901070] yenta_cardbus 0000:03:01.0: pcmcia: parent PCI bridge Memory window: 0xf1d00000 - 0xf1dfffff
[   10.901073] yenta_cardbus 0000:03:01.0: pcmcia: parent PCI bridge Memory window: 0x80000000 - 0x83ffffff
[   10.912731] wl 0000:0c:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   10.912757] wl 0000:0c:00.0: setting latency timer to 64
[   11.238006] nf_conntrack version 0.5.0 (16384 buckets, 65536 max)
[   11.238246] CONFIG_NF_CT_ACCT is deprecated and will be removed soon. Please use
[   11.238248] nf_conntrack.acct=1 kernel parameter, acct=1 nf_conntrack module option or
[   11.238250] sysctl net.netfilter.nf_conntrack_acct=1 to enable it.
[   11.258905] lib80211_crypt: registered algorithm 'TKIP'
[   11.259046] eth1: Broadcom BCM4311 802.11 Wireless Controller 5.10.91.9
[   11.264141] udev: renamed network interface eth1 to eth2
[   11.344301] input: DualPoint Stick as /devices/platform/i8042/serio1/input/input8
[   11.368323] input: AlpsPS/2 ALPS DualPoint TouchPad as /devices/platform/i8042/serio1/input/input9
[   11.717128] ip6_tables: (C) 2000-2006 Netfilter Core Team
[   11.828575] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[   11.828604] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   12.053700] input: HDA Digital PCBeep as /devices/pci0000:00/0000:00:1b.0/input/input10
[   12.130489] input: HDA Intel Mic at Ext Left Jack as /devices/pci0000:00/0000:00:1b.0/sound/card0/input11
[   12.130562] input: HDA Intel HP Out at Ext Left Jack as /devices/pci0000:00/0000:00:1b.0/sound/card0/input12
[   15.230825] EXT4-fs (sda5): internal journal on sda5:8
[   15.345464] EXT4-fs (sda3): barriers enabled
[   15.363974] kjournald2 starting: pid 1165, dev sda3:8, commit interval 5 seconds
[   15.364427] EXT4-fs (sda3): internal journal on sda3:8
[   15.364434] EXT4-fs (sda3): delayed allocation enabled
[   15.364438] EXT4-fs: file extents enabled
[   15.364612] EXT4-fs: mballoc enabled
[   15.364635] EXT4-fs (sda3): mounted filesystem with ordered data mode
[   15.505071] EXT4-fs (sda6): barriers enabled
[   15.505662] kjournald2 starting: pid 1176, dev sda6:8, commit interval 5 seconds
[   15.515265] EXT4-fs (sda6): internal journal on sda6:8
[   15.515271] EXT4-fs (sda6): delayed allocation enabled
[   15.515276] EXT4-fs: file extents enabled
[   15.515374] EXT4-fs: mballoc enabled
[   15.515401] EXT4-fs (sda6): mounted filesystem with ordered data mode
[   17.341907] tg3 0000:09:00.0: PME# disabled
[   17.342009]   alloc irq_desc for 28 on node 0
[   17.342011]   alloc kstat_irqs on node 0
[   17.342028] tg3 0000:09:00.0: irq 28 for MSI/MSI-X
[   17.405345] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   18.430308] cdrom: This disc doesn't have any tracks I recognize!
[   18.443280] usplash:431 freeing invalid memtype fffffffff3000000-fffffffff3e00000
[   18.959486] tg3: eth0: Link is up at 100 Mbps, full duplex.
[   18.959489] tg3: eth0: Flow control is on for TX and on for RX.
[   18.959713] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   27.442570] eth2: no IPv6 routers present
[   29.890028] eth0: no IPv6 routers present
[   52.734077] Intel AES-NI instructions are not detected.
[   52.789463] padlock: VIA PadLock not detected.
[   86.173508] process `skype.real' is using obsolete setsockopt SO_BSDCOMPAT
[ 1269.822558] CE: hpet increasing min_delta_ns to 15000 nsec
[ 3932.958078] CE: hpet increasing min_delta_ns to 22500 nsec
[12232.332582] usb 2-1: new high speed USB device using ehci_hcd and address 3
[12232.483309] usb 2-1: configuration #1 chosen from 2 choices
[12233.005647] Initializing USB Mass Storage driver...
[12233.005892] scsi4 : SCSI emulation for USB Mass Storage devices
[12233.006016] usbcore: registered new interface driver usb-storage
[12233.006019] USB Mass Storage support registered.
[12233.006281] usb-storage: device found at 3
[12233.006283] usb-storage: waiting for device to settle before scanning
[12238.000463] usb-storage: device scan complete
[12238.001258] scsi 4:0:0:0: Direct-Access     Apple    iPod             1.62 PQ: 0 ANSI: 0
[12238.001710] sd 4:0:0:0: Attached scsi generic sg2 type 0
[12238.005399] sd 4:0:0:0: [sdb] 14658336 2048-byte logical blocks: (30.0 GB/27.9 GiB)
[12238.006501] sd 4:0:0:0: [sdb] Write Protect is off
[12238.006506] sd 4:0:0:0: [sdb] Mode Sense: 68 00 00 08
[12238.006510] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[12238.008379] sd 4:0:0:0: [sdb] 14658336 2048-byte logical blocks: (30.0 GB/27.9 GiB)
[12238.009510] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[12238.009516]  sdb: sdb1 sdb2
[12238.044356] sd 4:0:0:0: [sdb] 14658336 2048-byte logical blocks: (30.0 GB/27.9 GiB)
[12238.045511] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[12238.045517] sd 4:0:0:0: [sdb] Attached SCSI removable disk
[14299.832210] usb 2-1: USB disconnect, address 3
[14299.843848] FAT: bread failed in fat_clusters_flush
[14299.931921] FAT: bread failed in fat_clusters_flush
[14299.931937] FAT: bread failed in fat_clusters_flush
[14299.931947] FAT: bread failed in fat_clusters_flush

---

### Post by blwegrzyn on 2010-02-11
anyone can help?
at least tell me where to look?
I dont want to reinstall the os.

---

### Post by blwegrzyn on 2010-02-15
i am not sure if below is related:

blwegrzyn@blwegrzyn-laptop:~$ sudo insserv
[sudo] password for blwegrzyn:
insserv: warning: script 'K01acpid' missing LSB tags and overrides
insserv: warning: script 'K01acpi-support' missing LSB tags and overrides
insserv: warning: script 'K01network-manager' missing LSB tags and overrides
insserv: warning: script 'S85vpnagentd_init' missing LSB tags and overrides
insserv: warning: script 'ufw' missing LSB tags and overrides
insserv: warning: script 'anacron' missing LSB tags and overrides
insserv: warning: script 'bootchart' missing LSB tags and overrides
insserv: warning: script 'usplash' missing LSB tags and overrides
insserv: warning: script 'apport' missing LSB tags and overrides
insserv: warning: current start runlevel(s) (0 6) of script `umountfs' overwrites defaults (empty).
insserv: warning: script 'vpnagentd_init' missing LSB tags and overrides
insserv: warning: script 'rsyslog' missing LSB tags and overrides
insserv: warning: script 'hal' missing LSB tags and overrides
insserv: warning: current start runlevel(s) (6) of script `reboot' overwrites defaults (empty).
insserv: warning: current start runlevel(s) (0 6) of script `networking' overwrites defaults (empty).
insserv: warning: script 'cron' missing LSB tags and overrides
insserv: warning: script 'gdm' missing LSB tags and overrides
insserv: warning: script 'udev' missing LSB tags and overrides
insserv: warning: script 'network-manager' missing LSB tags and overrides
insserv: warning: script 'acpid' missing LSB tags and overrides
insserv: warning: current start runlevel(s) (0 6) of script `umountnfs.sh' overwrites defaults (empty).
insserv: warning: script 'acpi-support' missing LSB tags and overrides
insserv: warning: current stop runlevel(s) (0 1 2 3 4 5 6) of script `bootlogd' overwrites defaults (empty).
insserv: warning: script 'module-init-tools' missing LSB tags and overrides
insserv: warning: current start runlevel(s) (0 6) of script `wpa-ifupdown' overwrites defaults (empty).
insserv: warning: script 'dbus' missing LSB tags and overrides
insserv: warning: current stop runlevel(s) (2 3 4 5) of script `pppd-dns' overwrites defaults (empty).
insserv: warning: script 'udevtrigger' missing LSB tags and overrides
insserv: warning: script 'atd' missing LSB tags and overrides
insserv: warning: current start runlevel(s) (0 6) of script `umountroot' overwrites defaults (empty).
insserv: warning: current start runlevel(s) (0 6) of script `sendsigs' overwrites defaults (empty).
insserv: warning: script 'hwclock' missing LSB tags and overrides
insserv: warning: script 'dmesg' missing LSB tags and overrides
insserv: warning: script 'failsafe-x' missing LSB tags and overrides
insserv: warning: script 'procps' missing LSB tags and overrides
insserv: warning: current start runlevel(s) (0) of script `halt' overwrites defaults (empty).
insserv: warning: script 'udev-finish' missing LSB tags and overrides
insserv: warning: current stop runlevel(s) (0 1 2 3 4 5 6) of script `dns-clean' overwrites defaults (empty).
insserv: warning: script 'udevmonitor' missing LSB tags and overrides
insserv: warning: script 'rsyslog-kmsg' missing LSB tags and overrides
insserv: warning: script 'avahi-daemon' missing LSB tags and overrides
insserv: warning: script 'hwclock-save' missing LSB tags and overrides
insserv: Starting vpnagentd_init depends on laptop-mode and therefore on system facility `$all' which can not be true!
blwegrzyn@blwegrzyn-laptop:~$

---

### Post by blwegrzyn on 2010-02-15
i found this, but not sure if this relates:
blwegrzyn@blwegrzyn-laptop:~$ sudo insserv
[sudo] password for blwegrzyn:
insserv: warning: script 'K01acpid' missing LSB tags and overrides
insserv: warning: script 'K01acpi-support' missing LSB tags and overrides
insserv: warning: script 'K01network-manager' missing LSB tags and overrides
insserv: warning: script 'S85vpnagentd_init' missing LSB tags and overrides
insserv: warning: script 'ufw' missing LSB tags and overrides
insserv: warning: script 'anacron' missing LSB tags and overrides
insserv: warning: script 'bootchart' missing LSB tags and overrides
insserv: warning: script 'usplash' missing LSB tags and overrides
insserv: warning: script 'apport' missing LSB tags and overrides
insserv: warning: current start runlevel(s) (0 6) of script `umountfs' overwrites defaults (empty).
insserv: warning: script 'vpnagentd_init' missing LSB tags and overrides
insserv: warning: script 'rsyslog' missing LSB tags and overrides
insserv: warning: script 'hal' missing LSB tags and overrides
insserv: warning: current start runlevel(s) (6) of script `reboot' overwrites defaults (empty).
insserv: warning: current start runlevel(s) (0 6) of script `networking' overwrites defaults (empty).
insserv: warning: script 'cron' missing LSB tags and overrides
insserv: warning: script 'gdm' missing LSB tags and overrides
insserv: warning: script 'udev' missing LSB tags and overrides
insserv: warning: script 'network-manager' missing LSB tags and overrides
insserv: warning: script 'acpid' missing LSB tags and overrides
insserv: warning: current start runlevel(s) (0 6) of script `umountnfs.sh' overwrites defaults (empty).
insserv: warning: script 'acpi-support' missing LSB tags and overrides
insserv: warning: current stop runlevel(s) (0 1 2 3 4 5 6) of script `bootlogd' overwrites defaults (empty).
insserv: warning: script 'module-init-tools' missing LSB tags and overrides
insserv: warning: current start runlevel(s) (0 6) of script `wpa-ifupdown' overwrites defaults (empty).
insserv: warning: script 'dbus' missing LSB tags and overrides
insserv: warning: current stop runlevel(s) (2 3 4 5) of script `pppd-dns' overwrites defaults (empty).
insserv: warning: script 'udevtrigger' missing LSB tags and overrides
insserv: warning: script 'atd' missing LSB tags and overrides
insserv: warning: current start runlevel(s) (0 6) of script `umountroot' overwrites defaults (empty).
insserv: warning: current start runlevel(s) (0 6) of script `sendsigs' overwrites defaults (empty).
insserv: warning: script 'hwclock' missing LSB tags and overrides
insserv: warning: script 'dmesg' missing LSB tags and overrides
insserv: warning: script 'failsafe-x' missing LSB tags and overrides
insserv: warning: script 'procps' missing LSB tags and overrides
insserv: warning: current start runlevel(s) (0) of script `halt' overwrites defaults (empty).
insserv: warning: script 'udev-finish' missing LSB tags and overrides
insserv: warning: current stop runlevel(s) (0 1 2 3 4 5 6) of script `dns-clean' overwrites defaults (empty).
insserv: warning: script 'udevmonitor' missing LSB tags and overrides
insserv: warning: script 'rsyslog-kmsg' missing LSB tags and overrides
insserv: warning: script 'avahi-daemon' missing LSB tags and overrides
insserv: warning: script 'hwclock-save' missing LSB tags and overrides
insserv: Starting vpnagentd_init depends on laptop-mode and therefore on system facility `$all' which can not be true!
blwegrzyn@blwegrzyn-laptop:~$

---

### Post by blwegrzyn on 2010-02-16
it looks like there is not too much of support here and i am forced to reinstall the os !!!

---

### Post by blwegrzyn on 2010-02-16
fyi this solved the problem:
[https://bugs.launchpad.net/ureadahead/+bug/515788](https://bugs.launchpad.net/ureadahead/+bug/515788)


anyone knows why?

---

### Post by GreyWizzard on 2010-02-16
> **blwegrzyn said:**
> fyi this solved the problem:
[https://bugs.launchpad.net/ureadahead/+bug/515788](https://bugs.launchpad.net/ureadahead/+bug/515788)


anyone knows why?
Followed your link above but didn't see anything there that shows any fix, only a bug report.

I seem to be having similar issues with my install of 9.10 x86_64 and I would love your input.

---

### Post by blwegrzyn on 2010-02-17
[https://answers.launchpad.net/upstart/+question/98037](https://answers.launchpad.net/upstart/+question/98037)

---

