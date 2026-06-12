---
title: "battery icon not working after suspend"
date: 2010-01-10
forum: General Help
---

### Post by francois203 on 2010-01-10
Hi,
After suspending my computer, the battery icon doesn't work anymore (nothing happens when I put my mouse over it and it doesn't detect wether the computer is plugged in or not). Also, the brightness of the computer doesn't change when I plug/unplug the computer. All of that works fine before i suspend the computer.
Please help me!

---

### Post by ibuclaw on 2010-01-10
Hi francois.

Due to the nature of your issue, will need some debug output to see what is going on.

First, **reboot** - so that you start with a fresh system.

When you login, open a terminal via "Applications -> Accessories -> Terminal", then copy in the following text:
```
dmesg > ~/Desktop/predmesg.txt
```
This will create a file on your Desktop with an event log of everything that has been recorded since Linux has been running.

Next, suspend your system - wait about 5-10 seconds - then wake your system back up again.
When you reach your Desktop page again, go back to the terminal you opened, and copy in the next text:
```
dmesg > ~/Desktop/postdmesg.txt
```
And this will create a second file on your Desktop.

Next, sign onto these forums, and upload those files in your next post. If you can't upload them for whatever reason, just open the files and copy and paste the output of them into [CODE] tags.

Regards
Iain

---

### Post by francois203 on 2010-01-10
The txt files are to big to be uploaded so here is the code

predmesg.txt

```
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.31-17-generic (buildd@palmer) (gcc version 4.4.1 (Ubuntu 4.4.1-4ubuntu8) ) #54-Ubuntu SMP Thu Dec 10 16:20:31 UTC 2009 (Ubuntu 2.6.31-17.54-generic)
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
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009e000 (usable)
[    0.000000]  BIOS-e820: 000000000009e000 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 00000000b9e6b000 (usable)
[    0.000000]  BIOS-e820: 00000000b9e6b000 - 00000000b9ebf000 (reserved)
[    0.000000]  BIOS-e820: 00000000b9ebf000 - 00000000b9f83000 (usable)
[    0.000000]  BIOS-e820: 00000000b9f83000 - 00000000b9fbf000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000b9fbf000 - 00000000b9fdf000 (usable)
[    0.000000]  BIOS-e820: 00000000b9fdf000 - 00000000b9ff6000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000b9ff6000 - 00000000b9ffe000 (usable)
[    0.000000]  BIOS-e820: 00000000b9ffe000 - 00000000b9fff000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000b9fff000 - 00000000ba000000 (usable)
[    0.000000]  BIOS-e820: 00000000ba000000 - 00000000c0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000f8000000 - 00000000fc000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed10000 - 00000000fed14000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed18000 - 00000000fed1a000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed1c000 - 00000000fed20000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fff00000 - 0000000100000000 (reserved)
[    0.000000]  BIOS-e820: 0000000100000000 - 0000000140000000 (usable)
[    0.000000] DMI 2.4 present.
[    0.000000] last_pfn = 0xba000 max_arch_pfn = 0x100000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-EFFFF write-through
[    0.000000]   F0000-FFFFF write-combining
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000 mask F80000000 write-back
[    0.000000]   1 base 0FFF00000 mask FFFF00000 write-protect
[    0.000000]   2 base 080000000 mask FC0000000 write-back
[    0.000000]   3 base 0BC000000 mask FFC000000 uncachable
[    0.000000]   4 base 0BA000000 mask FFE000000 uncachable
[    0.000000]   5 base 100000000 mask FC0000000 write-back
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] e820 update range: 0000000000002000 - 0000000000006000 (usable) ==> (reserved)
[    0.000000] Scanning 1 areas for low memory corruption
[    0.000000] modified physical RAM map:
[    0.000000]  modified: 0000000000000000 - 0000000000002000 (usable)
[    0.000000]  modified: 0000000000002000 - 0000000000006000 (reserved)
[    0.000000]  modified: 0000000000006000 - 000000000009e000 (usable)
[    0.000000]  modified: 000000000009e000 - 00000000000a0000 (reserved)
[    0.000000]  modified: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  modified: 0000000000100000 - 00000000b9e6b000 (usable)
[    0.000000]  modified: 00000000b9e6b000 - 00000000b9ebf000 (reserved)
[    0.000000]  modified: 00000000b9ebf000 - 00000000b9f83000 (usable)
[    0.000000]  modified: 00000000b9f83000 - 00000000b9fbf000 (ACPI NVS)
[    0.000000]  modified: 00000000b9fbf000 - 00000000b9fdf000 (usable)
[    0.000000]  modified: 00000000b9fdf000 - 00000000b9ff6000 (ACPI data)
[    0.000000]  modified: 00000000b9ff6000 - 00000000b9ffe000 (usable)
[    0.000000]  modified: 00000000b9ffe000 - 00000000b9fff000 (ACPI data)
[    0.000000]  modified: 00000000b9fff000 - 00000000ba000000 (usable)
[    0.000000]  modified: 00000000ba000000 - 00000000c0000000 (reserved)
[    0.000000]  modified: 00000000f8000000 - 00000000fc000000 (reserved)
[    0.000000]  modified: 00000000fec00000 - 00000000fec01000 (reserved)
[    0.000000]  modified: 00000000fed10000 - 00000000fed14000 (reserved)
[    0.000000]  modified: 00000000fed18000 - 00000000fed1a000 (reserved)
[    0.000000]  modified: 00000000fed1c000 - 00000000fed20000 (reserved)
[    0.000000]  modified: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  modified: 00000000fff00000 - 0000000100000000 (reserved)
[    0.000000]  modified: 0000000100000000 - 0000000140000000 (usable)
[    0.000000] initial memory mapped : 0 - 00c00000
[    0.000000] init_memory_mapping: 0000000000000000-00000000377fe000
[    0.000000] Using x86 segment limits to approximate NX protection
[    0.000000]  0000000000 - 0000400000 page 4k
[    0.000000]  0000400000 - 0037400000 page 2M
[    0.000000]  0037400000 - 00377fe000 page 4k
[    0.000000] kernel direct mapping tables up to 377fe000 @ 7000-c000
[    0.000000] RAMDISK: 378a3000 - 37fef6df
[    0.000000] Allocated new RAMDISK: 008ad000 - 00ff96df
[    0.000000] Move RAMDISK from 00000000378a3000 - 0000000037fef6de to 008ad000 - 00ff96de
[    0.000000] ACPI: RSDP 000fe020 00024 (v02 HP    )
[    0.000000] ACPI: XSDT b9ffe120 00074 (v01 HPQOEM SLIC-MPC 00000001      01000013)
[    0.000000] ACPI: FACP b9ff3000 000F4 (v04 HP     BLADE    00000001 MSFT 01000013)
[    0.000000] ACPI: DSDT b9fe4000 0A96B (v01 HP     BLADE    00000001 MSFT 01000013)
[    0.000000] ACPI: FACS b9f8c000 00040
[    0.000000] ACPI: DMAR b9ff5000 00068 (v01                00000001      00000000)
[    0.000000] ACPI: SSDT b9ff4000 00655 (v01  PmRef    CpuPm 00003000 INTL 20051117)
[    0.000000] ACPI: HPET b9ff2000 00038 (v01 HPQOEM SLIC-MPC 00000001 MSFT 01000013)
[    0.000000] ACPI: APIC b9ff1000 0006C (v02 HPQOEM SLIC-MPC 00000001 MSFT 01000013)
[    0.000000] ACPI: MCFG b9ff0000 0003C (v01 HPQOEM SLIC-MPC 00000001 MSFT 01000013)
[    0.000000] ACPI: ASF! b9fef000 000A5 (v32 HPQOEM SLIC-MPC 00000001 MSFT 01000013)
[    0.000000] ACPI: SLIC b9fe3000 00176 (v01 HPQOEM SLIC-MPC 00000001 LOHR 000F4240)
[    0.000000] ACPI: BOOT b9fe2000 00028 (v01 HPQOEM SLIC-MPC 00000001 MSFT 01000013)
[    0.000000] ACPI: SSDT b9fe1000 00296 (v01 INTEL  SataAhci 00001000 INTL 20051117)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] 2088MB HIGHMEM available.
[    0.000000] 887MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 377fe000
[    0.000000]   low ram: 0 - 377fe000
[    0.000000]   node 0 low ram: 00000000 - 377fe000
[    0.000000]   node 0 bootmap 00008000 - 0000ef00
[    0.000000] (9 early reservations) ==> bootmem [0000000000 - 00377fe000]
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
[    0.000000]   #1 [0000001000 - 0000002000]    EX TRAMPOLINE ==> [0000001000 - 0000002000]
[    0.000000]   #2 [0000006000 - 0000007000]       TRAMPOLINE ==> [0000006000 - 0000007000]
[    0.000000]   #3 [0000100000 - 00008a80a0]    TEXT DATA BSS ==> [0000100000 - 00008a80a0]
[    0.000000]   #4 [000009e000 - 0000100000]    BIOS reserved ==> [000009e000 - 0000100000]
[    0.000000]   #5 [00008a9000 - 00008ac1a4]              BRK ==> [00008a9000 - 00008ac1a4]
[    0.000000]   #6 [0000007000 - 0000008000]          PGTABLE ==> [0000007000 - 0000008000]
[    0.000000]   #7 [00008ad000 - 0000ff96df]      NEW RAMDISK ==> [00008ad000 - 0000ff96df]
[    0.000000]   #8 [0000008000 - 000000f000]          BOOTMAP ==> [0000008000 - 000000f000]
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000000 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x000377fe
[    0.000000]   HighMem  0x000377fe -> 0x000ba000
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[7] active PFN ranges
[    0.000000]     0: 0x00000000 -> 0x00000002
[    0.000000]     0: 0x00000006 -> 0x0000009e
[    0.000000]     0: 0x00000100 -> 0x000b9e6b
[    0.000000]     0: 0x000b9ebf -> 0x000b9f83
[    0.000000]     0: 0x000b9fbf -> 0x000b9fdf
[    0.000000]     0: 0x000b9ff6 -> 0x000b9ffe
[    0.000000]     0: 0x000b9fff -> 0x000ba000
[    0.000000] On node 0 totalpages: 761586
[    0.000000] free_area_init_node: node 0, pgdat c0784960, node_mem_map c1000000
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3962 pages, LIFO batch:0
[    0.000000]   Normal zone: 1744 pages used for memmap
[    0.000000]   Normal zone: 221486 pages, LIFO batch:31
[    0.000000]   HighMem zone: 4177 pages used for memmap
[    0.000000]   HighMem zone: 530185 pages, LIFO batch:31
[    0.000000] Using APIC driver default
[    0.000000] ACPI: PM-Timer IO Port: 0x408
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x00] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x00] disabled)
[    0.000000] ACPI: IOAPIC (id[0x04] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 4, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000
[    0.000000] SMP: Allowing 4 CPUs, 2 hotplug CPUs
[    0.000000] nr_irqs_gsi: 24
[    0.000000] PM: Registered nosave memory: 0000000000002000 - 0000000000006000
[    0.000000] PM: Registered nosave memory: 000000000009e000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
[    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at c0000000 (gap: c0000000:38000000)
[    0.000000] NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:4 nr_node_ids:1
[    0.000000] PERCPU: Embedded 14 pages at c2750000, static data 35612 bytes
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 755633
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.31-17-generic root=UUID=9e82b147-8c2d-4bd2-b1b2-d5695d16aeac ro quiet splash
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] allocated 15237120 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] Initializing HighMem for node 0 (000377fe:000ba000)
[    0.000000] Memory: 2990364k/3047424k available (4566k kernel code, 55132k reserved, 2142k data, 540k init, 2137448k highmem)
[    0.000000] virtual kernel memory layout:
[    0.000000]     fixmap  : 0xfff1d000 - 0xfffff000   ( 904 kB)
[    0.000000]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[    0.000000]     vmalloc : 0xf7ffe000 - 0xff7fe000   ( 120 MB)
[    0.000000]     lowmem  : 0xc0000000 - 0xf77fe000   ( 887 MB)
[    0.000000]       .init : 0xc078e000 - 0xc0815000   ( 540 kB)
[    0.000000]       .data : 0xc0575a64 - 0xc078d408   (2142 kB)
[    0.000000]       .text : 0xc0100000 - 0xc0575a64   (4566 kB)
[    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.000000] SLUB: Genslabs=13, HWalign=64, Order=0-3, MinObjects=0, CPUs=4, Nodes=1
[    0.000000] NR_IRQS:2304 nr_irqs:440
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 1995.088 MHz processor.
[    0.001327] Console: colour VGA+ 80x25
[    0.001330] console [tty0] enabled
[    0.001496] hpet clockevent registered
[    0.001500] HPET: 4 timers in total, 0 timers will be used for per-cpu timer
[    0.001506] Calibrating delay loop (skipped), value calculated using timer frequency.. 3990.17 BogoMIPS (lpj=7980352)
[    0.001523] Security Framework initialized
[    0.001542] AppArmor: AppArmor initialized
[    0.001549] Mount-cache hash table entries: 512
[    0.001674] Initializing cgroup subsys ns
[    0.001679] Initializing cgroup subsys cpuacct
[    0.001683] Initializing cgroup subsys memory
[    0.001690] Initializing cgroup subsys freezer
[    0.001692] Initializing cgroup subsys net_cls
[    0.001706] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.001709] CPU: L2 cache: 2048K
[    0.001711] CPU: Physical Processor ID: 0
[    0.001713] CPU: Processor Core ID: 0
[    0.001716] mce: CPU supports 6 MCE banks
[    0.001724] CPU0: Thermal monitoring enabled (TM1)
[    0.001728] using mwait in idle threads.
[    0.001734] Performance Counters: Core2 events, Intel PMU driver.
[    0.001743] ... version:                 2
[    0.001744] ... bit width:               40
[    0.001746] ... generic counters:        2
[    0.001748] ... value mask:              000000ffffffffff
[    0.001750] ... max period:              000000007fffffff
[    0.001752] ... fixed-purpose counters:  3
[    0.001753] ... counter mask:            0000000700000003
[    0.001757] Checking 'hlt' instruction... OK.
[    0.018523] ACPI: Core revision 20090521
[    0.036397] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.076958] CPU0: Intel(R) Core(TM)2 Duo CPU     T5800  @ 2.00GHz stepping 0d
[    0.080001] Booting processor 1 APIC 0x1 ip 0x6000
[    0.004000] Initializing CPU#1
[    0.004000] Calibrating delay using timer specific routine.. 3990.46 BogoMIPS (lpj=7980920)
[    0.004000] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.004000] CPU: L2 cache: 2048K
[    0.004000] CPU: Physical Processor ID: 0
[    0.004000] CPU: Processor Core ID: 1
[    0.004000] mce: CPU supports 6 MCE banks
[    0.004000] CPU1: Thermal monitoring enabled (TM1)
[    0.004000] x86 PAT enabled: cpu 1, old 0x7040600070406, new 0x7010600070106
[    0.165434] CPU1: Intel(R) Core(TM)2 Duo CPU     T5800  @ 2.00GHz stepping 0d
[    0.165447] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
[    0.168022] Brought up 2 CPUs
[    0.168025] Total of 2 processors activated (7980.63 BogoMIPS).
[    0.168074] CPU0 attaching sched-domain:
[    0.168077]  domain 0: span 0-1 level MC
[    0.168080]   groups: 0 1
[    0.168085] CPU1 attaching sched-domain:
[    0.168087]  domain 0: span 0-1 level MC
[    0.168090]   groups: 1 0
[    0.168164] Booting paravirtualized kernel on bare hardware
[    0.168208] regulator: core version 0.5
[    0.168208] Time: 10:09:31  Date: 01/10/10
[    0.168208] NET: Registered protocol family 16
[    0.168208] EISA bus registered
[    0.168217] ACPI: bus type pci registered
[    0.168284] PCI: MCFG configuration 0: base f8000000 segment 0 buses 0 - 63
[    0.168287] PCI: MCFG area at f8000000 reserved in E820
[    0.168289] PCI: Using MMCONFIG for extended config space
[    0.168291] PCI: Using configuration type 1 for base access
[    0.169324] bio: create slab <bio-0> at 0
[    0.173027] ACPI: EC: Enabling special treatment for EC from MSI.
[    0.173029] ACPI: EC: Look up EC in DSDT
[    0.224398] ACPI: BIOS _OSI(Linux) query ignored
[    0.232017] ACPI: EC: non-query interrupt received, switching to interrupt mode
[    0.444193] ACPI: Interpreter enabled
[    0.444200] ACPI: (supports S0 S3 S4 S5)
[    0.444230] ACPI: Using IOAPIC for interrupt routing
[    0.680182] [Firmware Bug]: ACPI: ACPI brightness control misses _BQC function
[    0.680858] [Firmware Bug]: ACPI: ACPI brightness control misses _BQC function
[    0.705476] ACPI: EC: GPE = 0x17, I/O: command/status = 0x66, data = 0x62
[    0.705478] ACPI: EC: driver started in interrupt mode
[    0.712538] ACPI: Power Resource [FN00] (on)
[    0.712538] ACPI: No dock devices found.
[    0.713079] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.713180] pci 0000:00:02.0: reg 10 64bit mmio: [0xd0000000-0xd03fffff]
[    0.713189] pci 0000:00:02.0: reg 18 64bit mmio: [0xc0000000-0xcfffffff]
[    0.713194] pci 0000:00:02.0: reg 20 io port: [0x60f0-0x60f7]
[    0.713240] pci 0000:00:02.1: reg 10 64bit mmio: [0xd5400000-0xd54fffff]
[    0.713366] pci 0000:00:1a.0: reg 20 io port: [0x60c0-0x60df]
[    0.713479] pci 0000:00:1a.1: reg 20 io port: [0x60a0-0x60bf]
[    0.713599] pci 0000:00:1a.7: reg 10 32bit mmio: [0xda504c00-0xda504fff]
[    0.713675] pci 0000:00:1a.7: PME# supported from D0 D3hot D3cold
[    0.713680] pci 0000:00:1a.7: PME# disabled
[    0.713740] pci 0000:00:1b.0: reg 10 64bit mmio: [0xda500000-0xda503fff]
[    0.713803] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    0.713808] pci 0000:00:1b.0: PME# disabled
[    0.716013] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    0.716018] pci 0000:00:1c.0: PME# disabled
[    0.716110] pci 0000:00:1c.2: PME# supported from D0 D3hot D3cold
[    0.716115] pci 0000:00:1c.2: PME# disabled
[    0.716206] pci 0000:00:1c.3: PME# supported from D0 D3hot D3cold
[    0.716211] pci 0000:00:1c.3: PME# disabled
[    0.716299] pci 0000:00:1c.4: PME# supported from D0 D3hot D3cold
[    0.716304] pci 0000:00:1c.4: PME# disabled
[    0.716391] pci 0000:00:1c.5: PME# supported from D0 D3hot D3cold
[    0.716396] pci 0000:00:1c.5: PME# disabled
[    0.716487] pci 0000:00:1d.0: reg 20 io port: [0x6080-0x609f]
[    0.716610] pci 0000:00:1d.1: reg 20 io port: [0x6060-0x607f]
[    0.716740] pci 0000:00:1d.2: reg 20 io port: [0x6040-0x605f]
[    0.716856] pci 0000:00:1d.7: reg 10 32bit mmio: [0xda504800-0xda504bff]
[    0.716932] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
[    0.716937] pci 0000:00:1d.7: PME# disabled
[    0.717185] pci 0000:00:1f.2: reg 10 io port: [0x60e8-0x60ef]
[    0.717193] pci 0000:00:1f.2: reg 14 io port: [0x60fc-0x60ff]
[    0.717201] pci 0000:00:1f.2: reg 18 io port: [0x60e0-0x60e7]
[    0.717209] pci 0000:00:1f.2: reg 1c io port: [0x60f8-0x60fb]
[    0.717217] pci 0000:00:1f.2: reg 20 io port: [0x6020-0x603f]
[    0.717225] pci 0000:00:1f.2: reg 24 32bit mmio: [0xda504000-0xda5047ff]
[    0.717274] pci 0000:00:1f.2: PME# supported from D3hot
[    0.717279] pci 0000:00:1f.2: PME# disabled
[    0.717321] pci 0000:00:1f.3: reg 10 64bit mmio: [0xda505000-0xda5050ff]
[    0.717341] pci 0000:00:1f.3: reg 20 io port: [0x6000-0x601f]
[    0.717424] pci 0000:00:1c.0: bridge io port: [0x5000-0x5fff]
[    0.717430] pci 0000:00:1c.0: bridge 32bit mmio: [0xd9500000-0xda4fffff]
[    0.717438] pci 0000:00:1c.0: bridge 64bit mmio pref: [0xd0400000-0xd13fffff]
[    0.717639] pci 0000:02:00.0: reg 10 64bit mmio: [0xd8500000-0xd8503fff]
[    0.717856] pci 0000:02:00.0: supports D1 D2
[    0.717990] pci 0000:00:1c.2: bridge io port: [0x4000-0x4fff]
[    0.717995] pci 0000:00:1c.2: bridge 32bit mmio: [0xd8500000-0xd94fffff]
[    0.718003] pci 0000:00:1c.2: bridge 64bit mmio pref: [0xd1400000-0xd23fffff]
[    0.718065] pci 0000:03:00.0: reg 10 io port: [0x3000-0x30ff]
[    0.718092] pci 0000:03:00.0: reg 18 64bit mmio: [0xd2410000-0xd2410fff]
[    0.718110] pci 0000:03:00.0: reg 20 64bit mmio: [0xd2400000-0xd240ffff]
[    0.718121] pci 0000:03:00.0: reg 30 32bit mmio: [0xfffe0000-0xffffffff]
[    0.718174] pci 0000:03:00.0: supports D1 D2
[    0.718176] pci 0000:03:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.718182] pci 0000:03:00.0: PME# disabled
[    0.718263] pci 0000:00:1c.3: bridge io port: [0x3000-0x3fff]
[    0.718268] pci 0000:00:1c.3: bridge 32bit mmio: [0xd7500000-0xd84fffff]
[    0.718276] pci 0000:00:1c.3: bridge 64bit mmio pref: [0xd2400000-0xd33fffff]
[    0.718334] pci 0000:04:00.0: reg 10 32bit mmio: [0xd6500300-0xd65003ff]
[    0.718507] pci 0000:04:00.2: reg 10 32bit mmio: [0xd6500200-0xd65002ff]
[    0.718671] pci 0000:04:00.3: reg 10 32bit mmio: [0xd6500100-0xd65001ff]
[    0.718832] pci 0000:04:00.4: reg 10 32bit mmio: [0xd6500000-0xd65000ff]
[    0.719002] pci 0000:00:1c.4: bridge io port: [0x2000-0x2fff]
[    0.719007] pci 0000:00:1c.4: bridge 32bit mmio: [0xd6500000-0xd74fffff]
[    0.719015] pci 0000:00:1c.4: bridge 64bit mmio pref: [0xd3400000-0xd43fffff]
[    0.719075] pci 0000:00:1c.5: bridge io port: [0x1000-0x1fff]
[    0.719080] pci 0000:00:1c.5: bridge 32bit mmio: [0xd5500000-0xd64fffff]
[    0.719087] pci 0000:00:1c.5: bridge 64bit mmio pref: [0xd4400000-0xd53fffff]
[    0.719149] pci 0000:00:1e.0: transparent bridge
[    0.719200] pci_bus 0000:00: on NUMA node 0
[    0.719207] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.719531] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P32_._PRT]
[    0.719684] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.EXP1._PRT]
[    0.719794] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.EXP3._PRT]
[    0.719914] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.EXP4._PRT]
[    0.720039] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.EXP5._PRT]
[    0.720201] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.EXP6._PRT]
[    0.729634] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 7 9 10 *11 12)
[    0.729779] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 7 9 *10 11 12)
[    0.729921] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 7 9 10 *11 12)
[    0.730062] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 7 9 10 *11 12)
[    0.730203] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 7 9 10 *11 12)
[    0.730344] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 7 9 10 *11 12)
[    0.730484] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 7 9 10 *11 12)
[    0.730625] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 7 9 10 11 12) *0, disabled.
[    0.730835] SCSI subsystem initialized
[    0.732017] libata version 3.00 loaded.
[    0.732044] usbcore: registered new interface driver usbfs
[    0.732044] usbcore: registered new interface driver hub
[    0.732046] usbcore: registered new device driver usb
[    0.732090] ACPI: WMI: Mapper loaded
[    0.732092] PCI: Using ACPI for IRQ routing
[    0.740008] Bluetooth: Core ver 2.15
[    0.740014] NET: Registered protocol family 31
[    0.740015] Bluetooth: HCI device and connection manager initialized
[    0.740018] Bluetooth: HCI socket layer initialized
[    0.740020] NetLabel: Initializing
[    0.740021] NetLabel:  domain hash size = 128
[    0.740023] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.740037] NetLabel:  unlabeled traffic allowed by default
[    0.740069] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0
[    0.740075] hpet0: 4 comparators, 64-bit 14.318180 MHz counter
[    0.748013] Switched to high resolution mode on CPU 0
[    0.749469] Switched to high resolution mode on CPU 1
[    0.756510] pnp: PnP ACPI init
[    0.756520] ACPI: bus type pnp registered
[    0.877196] pnp 00:01: io resource (0x164e-0x164f) overlaps 0000:00:1c.5 BAR 13 (0x1000-0x1fff), disabling
[    0.877988]   alloc irq_desc for 23 on node -1
[    0.877991]   alloc kstat_irqs on node -1
[    0.878500] pnp: PnP ACPI: found 11 devices
[    0.878502] ACPI: ACPI bus type pnp unregistered
[    0.878506] PnPBIOS: Disabled by ACPI PNP
[    0.878517] system 00:01: ioport range 0x600-0x60f has been reserved
[    0.878520] system 00:01: ioport range 0x610-0x610 has been reserved
[    0.878523] system 00:01: ioport range 0x800-0x80f has been reserved
[    0.878526] system 00:01: ioport range 0x810-0x817 has been reserved
[    0.878528] system 00:01: ioport range 0x820-0x823 has been reserved
[    0.878531] system 00:01: ioport range 0x400-0x47f has been reserved
[    0.878534] system 00:01: ioport range 0x500-0x53f has been reserved
[    0.878538] system 00:01: iomem range 0xf8000000-0xfbffffff has been reserved
[    0.878541] system 00:01: iomem range 0xfed1c000-0xfed1ffff has been reserved
[    0.878545] system 00:01: iomem range 0xfed10000-0xfed13fff has been reserved
[    0.878548] system 00:01: iomem range 0xfed18000-0xfed18fff has been reserved
[    0.878551] system 00:01: iomem range 0xfed19000-0xfed19fff has been reserved
[    0.878554] system 00:01: iomem range 0xfec00000-0xfec00fff could not be reserved
[    0.878557] system 00:01: iomem range 0xfed20000-0xfed8ffff has been reserved
[    0.878560] system 00:01: iomem range 0xfee00000-0xfee00fff has been reserved
[    0.913217] AppArmor: AppArmor Filesystem Enabled
[    0.913237] pci 0000:03:00.0: BAR 6: no parent found for of device [0xfffe0000-0xffffffff]
[    0.913300] pci 0000:00:1c.0: PCI bridge, secondary bus 0000:01
[    0.913304] pci 0000:00:1c.0:   IO window: 0x5000-0x5fff
[    0.913310] pci 0000:00:1c.0:   MEM window: 0xd9500000-0xda4fffff
[    0.913315] pci 0000:00:1c.0:   PREFETCH window: 0x000000d0400000-0x000000d13fffff
[    0.913323] pci 0000:00:1c.2: PCI bridge, secondary bus 0000:02
[    0.913327] pci 0000:00:1c.2:   IO window: 0x4000-0x4fff
[    0.913333] pci 0000:00:1c.2:   MEM window: 0xd8500000-0xd94fffff
[    0.913338] pci 0000:00:1c.2:   PREFETCH window: 0x000000d1400000-0x000000d23fffff
[    0.913347] pci 0000:00:1c.3: PCI bridge, secondary bus 0000:03
[    0.913351] pci 0000:00:1c.3:   IO window: 0x3000-0x3fff
[    0.913357] pci 0000:00:1c.3:   MEM window: 0xd7500000-0xd84fffff
[    0.913363] pci 0000:00:1c.3:   PREFETCH window: 0x000000d2400000-0x000000d33fffff
[    0.913371] pci 0000:00:1c.4: PCI bridge, secondary bus 0000:04
[    0.913375] pci 0000:00:1c.4:   IO window: 0x2000-0x2fff
[    0.913381] pci 0000:00:1c.4:   MEM window: 0xd6500000-0xd74fffff
[    0.913386] pci 0000:00:1c.4:   PREFETCH window: 0x000000d3400000-0x000000d43fffff
[    0.913395] pci 0000:00:1c.5: PCI bridge, secondary bus 0000:05
[    0.913398] pci 0000:00:1c.5:   IO window: 0x1000-0x1fff
[    0.913405] pci 0000:00:1c.5:   MEM window: 0xd5500000-0xd64fffff
[    0.913410] pci 0000:00:1c.5:   PREFETCH window: 0x000000d4400000-0x000000d53fffff
[    0.913418] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:08
[    0.913420] pci 0000:00:1e.0:   IO window: disabled
[    0.913426] pci 0000:00:1e.0:   MEM window: disabled
[    0.913431] pci 0000:00:1e.0:   PREFETCH window: disabled
[    0.913444]   alloc irq_desc for 16 on node -1
[    0.913446]   alloc kstat_irqs on node -1
[    0.913450] pci 0000:00:1c.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.913455] pci 0000:00:1c.0: setting latency timer to 64
[    0.913464]   alloc irq_desc for 18 on node -1
[    0.913466]   alloc kstat_irqs on node -1
[    0.913470] pci 0000:00:1c.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.913475] pci 0000:00:1c.2: setting latency timer to 64
[    0.913483]   alloc irq_desc for 19 on node -1
[    0.913485]   alloc kstat_irqs on node -1
[    0.913489] pci 0000:00:1c.3: PCI INT D -> GSI 19 (level, low) -> IRQ 19
[    0.913494] pci 0000:00:1c.3: setting latency timer to 64
[    0.913503] pci 0000:00:1c.4: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.913508] pci 0000:00:1c.4: setting latency timer to 64
[    0.913517]   alloc irq_desc for 17 on node -1
[    0.913519]   alloc kstat_irqs on node -1
[    0.913522] pci 0000:00:1c.5: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    0.913528] pci 0000:00:1c.5: setting latency timer to 64
[    0.913536] pci 0000:00:1e.0: setting latency timer to 64
[    0.913541] pci_bus 0000:00: resource 0 io:  [0x00-0xffff]
[    0.913543] pci_bus 0000:00: resource 1 mem: [0x000000-0xffffffff]
[    0.913546] pci_bus 0000:01: resource 0 io:  [0x5000-0x5fff]
[    0.913549] pci_bus 0000:01: resource 1 mem: [0xd9500000-0xda4fffff]
[    0.913551] pci_bus 0000:01: resource 2 pref mem [0xd0400000-0xd13fffff]
[    0.913554] pci_bus 0000:02: resource 0 io:  [0x4000-0x4fff]
[    0.913557] pci_bus 0000:02: resource 1 mem: [0xd8500000-0xd94fffff]
[    0.913559] pci_bus 0000:02: resource 2 pref mem [0xd1400000-0xd23fffff]
[    0.913562] pci_bus 0000:03: resource 0 io:  [0x3000-0x3fff]
[    0.913564] pci_bus 0000:03: resource 1 mem: [0xd7500000-0xd84fffff]
[    0.913567] pci_bus 0000:03: resource 2 pref mem [0xd2400000-0xd33fffff]
[    0.913570] pci_bus 0000:04: resource 0 io:  [0x2000-0x2fff]
[    0.913572] pci_bus 0000:04: resource 1 mem: [0xd6500000-0xd74fffff]
[    0.913575] pci_bus 0000:04: resource 2 pref mem [0xd3400000-0xd43fffff]
[    0.913577] pci_bus 0000:05: resource 0 io:  [0x1000-0x1fff]
[    0.913580] pci_bus 0000:05: resource 1 mem: [0xd5500000-0xd64fffff]
[    0.913582] pci_bus 0000:05: resource 2 pref mem [0xd4400000-0xd53fffff]
[    0.913585] pci_bus 0000:08: resource 3 io:  [0x00-0xffff]
[    0.913587] pci_bus 0000:08: resource 4 mem: [0x000000-0xffffffff]
[    0.913621] NET: Registered protocol family 2
[    0.913717] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.914029] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.914482] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.914697] TCP: Hash tables configured (established 131072 bind 65536)
[    0.914700] TCP reno registered
[    0.914771] NET: Registered protocol family 1
[    0.914829] Trying to unpack rootfs image as initramfs...
[    1.103999] Freeing initrd memory: 7473k freed
[    1.107919] Simple Boot Flag value 0x5 read from CMOS RAM was invalid
[    1.107923] Simple Boot Flag at 0x44 set to 0x1
[    1.108124] cpufreq-nforce2: No nForce2 chipset.
[    1.108152] Scanning for low memory corruption every 60 seconds
[    1.108257] audit: initializing netlink socket (disabled)
[    1.108273] type=2000 audit(1263118171.108:1): initialized
[    1.116866] highmem bounce pool size: 64 pages
[    1.116871] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    1.118342] VFS: Disk quotas dquot_6.5.2
[    1.118407] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    1.118946] fuse init (API version 7.12)
[    1.119028] msgmni has been set to 1682
[    1.119229] alg: No test for stdrng (krng)
[    1.119243] io scheduler noop registered
[    1.119245] io scheduler anticipatory registered
[    1.119247] io scheduler deadline registered
[    1.119288] io scheduler cfq registered (default)
[    1.119300] pci 0000:00:02.0: Boot video device
[    1.152174]   alloc irq_desc for 24 on node -1
[    1.152176]   alloc kstat_irqs on node -1
[    1.152189] pcieport-driver 0000:00:1c.0: irq 24 for MSI/MSI-X
[    1.152201] pcieport-driver 0000:00:1c.0: setting latency timer to 64
[    1.152363]   alloc irq_desc for 25 on node -1
[    1.152365]   alloc kstat_irqs on node -1
[    1.152375] pcieport-driver 0000:00:1c.2: irq 25 for MSI/MSI-X
[    1.152386] pcieport-driver 0000:00:1c.2: setting latency timer to 64
[    1.152546]   alloc irq_desc for 26 on node -1
[    1.152548]   alloc kstat_irqs on node -1
[    1.152557] pcieport-driver 0000:00:1c.3: irq 26 for MSI/MSI-X
[    1.152568] pcieport-driver 0000:00:1c.3: setting latency timer to 64
[    1.152728]   alloc irq_desc for 27 on node -1
[    1.152730]   alloc kstat_irqs on node -1
[    1.152739] pcieport-driver 0000:00:1c.4: irq 27 for MSI/MSI-X
[    1.152750] pcieport-driver 0000:00:1c.4: setting latency timer to 64
[    1.152911]   alloc irq_desc for 28 on node -1
[    1.152913]   alloc kstat_irqs on node -1
[    1.152922] pcieport-driver 0000:00:1c.5: irq 28 for MSI/MSI-X
[    1.152933] pcieport-driver 0000:00:1c.5: setting latency timer to 64
[    1.153044] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    1.153293] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    1.288082] ACPI: AC Adapter [AC] (on-line)
[    1.288166] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input0
[    1.288170] ACPI: Power Button [PWRF]
[    1.288221] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1
[    1.288223] ACPI: Power Button [PWRB]
[    1.288274] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input2
[    1.288344] ACPI: Lid Switch [LID0]
[    1.288389] input: Sleep Button as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input3
[    1.288396] ACPI: Sleep Button [SLPB]
[    1.326051] fan PNP0C0B:00: registered as cooling_device0
[    1.326057] ACPI: Fan [FAN] (on)
[    1.327072] ACPI: SSDT b9e6ec18 00265 (v01  PmRef  Cpu0Ist 00003000 INTL 20051117)
[    1.327756] ACPI: SSDT b9e6c618 005B3 (v01  PmRef  Cpu0Cst 00003001 INTL 20051117)
[    1.328351] Monitor-Mwait will be used to enter C-1 state
[    1.328374] Monitor-Mwait will be used to enter C-2 state
[    1.328394] Monitor-Mwait will be used to enter C-3 state
[    1.328402] Marking TSC unstable due to TSC halts in idle
[    1.328420] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[    1.328439] processor LNXCPU:00: registered as cooling_device1
[    1.328443] ACPI: Processor [CPU0] (supports 8 throttling states)
[    1.328949] ACPI: SSDT b9e6de18 001CF (v01  PmRef    ApIst 00003000 INTL 20051117)
[    1.329518] ACPI: SSDT b9e6ef18 0008D (v01  PmRef    ApCst 00003000 INTL 20051117)
[    1.330237] ACPI: CPU1 (power states: C1[C1] C2[C2] C3[C3])
[    1.330256] processor LNXCPU:01: registered as cooling_device2
[    1.330260] ACPI: Processor [CPU1] (supports 8 throttling states)
[    1.483870] thermal LNXTHERM:01: registered as thermal_zone0
[    1.483878] ACPI: Thermal Zone [THRM] (48 C)
[    1.483949] isapnp: Scanning for PnP cards...
[    1.838241] isapnp: No Plug & Play device found
[    1.839416] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    1.840750] brd: module loaded
[    1.841208] loop: module loaded
[    1.841274] input: Macintosh mouse button emulation as /devices/virtual/input/input4
[    1.841348] ahci 0000:00:1f.2: version 3.0
[    1.841361]   alloc irq_desc for 21 on node -1
[    1.841363]   alloc kstat_irqs on node -1
[    1.841369] ahci 0000:00:1f.2: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[    1.841401]   alloc irq_desc for 29 on node -1
[    1.841403]   alloc kstat_irqs on node -1
[    1.841413] ahci 0000:00:1f.2: irq 29 for MSI/MSI-X
[    1.841465] ahci: SSS flag set, parallel bus scan disabled
[    1.841503] ahci 0000:00:1f.2: AHCI 0001.0200 32 slots 4 ports 3 Gbps 0x33 impl SATA mode
[    1.841507] ahci 0000:00:1f.2: flags: 64bit ncq sntf stag pm led clo pmp pio slum part ems 
[    1.841513] ahci 0000:00:1f.2: setting latency timer to 64
[    1.864075] scsi0 : ahci
[    1.864164] scsi1 : ahci
[    1.864220] scsi2 : ahci
[    1.864275] scsi3 : ahci
[    1.864331] scsi4 : ahci
[    1.864389] scsi5 : ahci
[    1.864652] ata1: SATA max UDMA/133 abar m2048@0xda504000 port 0xda504100 irq 29
[    1.864656] ata2: SATA max UDMA/133 abar m2048@0xda504000 port 0xda504180 irq 29
[    1.864659] ata3: DUMMY
[    1.864660] ata4: DUMMY
[    1.864663] ata5: SATA max UDMA/133 abar m2048@0xda504000 port 0xda504300 irq 29
[    1.864667] ata6: SATA max UDMA/133 abar m2048@0xda504000 port 0xda504380 irq 29
[    1.865620] Fixed MDIO Bus: probed
[    1.865653] PPP generic driver version 2.4.2
[    1.865739] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    1.865758] ehci_hcd 0000:00:1a.7: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    1.865769] ehci_hcd 0000:00:1a.7: setting latency timer to 64
[    1.865773] ehci_hcd 0000:00:1a.7: EHCI Host Controller
[    1.865818] ehci_hcd 0000:00:1a.7: new USB bus registered, assigned bus number 1
[    1.869717] ehci_hcd 0000:00:1a.7: debug port 1
[    1.869724] ehci_hcd 0000:00:1a.7: cache line size of 32 is not supported
[    1.869738] ehci_hcd 0000:00:1a.7: irq 18, io mem 0xda504c00
[    1.884513] ehci_hcd 0000:00:1a.7: USB 2.0 started, EHCI 1.00
[    1.884587] usb usb1: configuration #1 chosen from 1 choice
[    1.884616] hub 1-0:1.0: USB hub found
[    1.884623] hub 1-0:1.0: 4 ports detected
[    1.884682]   alloc irq_desc for 20 on node -1
[    1.884684]   alloc kstat_irqs on node -1
[    1.884689] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    1.884699] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    1.884703] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    1.884733] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 2
[    1.888638] ehci_hcd 0000:00:1d.7: debug port 1
[    1.888645] ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported
[    1.888658] ehci_hcd 0000:00:1d.7: irq 20, io mem 0xda504800
[    1.904019] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    1.904079] usb usb2: configuration #1 chosen from 1 choice
[    1.904106] hub 2-0:1.0: USB hub found
[    1.904112] hub 2-0:1.0: 6 ports detected
[    1.904175] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    1.904193] uhci_hcd: USB Universal Host Controller Interface driver
[    1.904214] uhci_hcd 0000:00:1a.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.904221] uhci_hcd 0000:00:1a.0: setting latency timer to 64
[    1.904224] uhci_hcd 0000:00:1a.0: UHCI Host Controller
[    1.904259] uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 3
[    1.904295] uhci_hcd 0000:00:1a.0: irq 16, io base 0x000060c0
[    1.904378] usb usb3: configuration #1 chosen from 1 choice
[    1.904404] hub 3-0:1.0: USB hub found
[    1.904410] hub 3-0:1.0: 2 ports detected
[    1.904458] uhci_hcd 0000:00:1a.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    1.904465] uhci_hcd 0000:00:1a.1: setting latency timer to 64
[    1.904469] uhci_hcd 0000:00:1a.1: UHCI Host Controller
[    1.904499] uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus number 4
[    1.904545] uhci_hcd 0000:00:1a.1: irq 17, io base 0x000060a0
[    1.904623] usb usb4: configuration #1 chosen from 1 choice
[    1.904649] hub 4-0:1.0: USB hub found
[    1.904655] hub 4-0:1.0: 2 ports detected
[    1.904706] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    1.904713] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    1.904716] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    1.904745] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 5
[    1.904771] uhci_hcd 0000:00:1d.0: irq 20, io base 0x00006080
[    1.904845] usb usb5: configuration #1 chosen from 1 choice
[    1.904871] hub 5-0:1.0: USB hub found
[    1.904877] hub 5-0:1.0: 2 ports detected
[    1.904924]   alloc irq_desc for 22 on node -1
[    1.904926]   alloc kstat_irqs on node -1
[    1.904931] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 22 (level, low) -> IRQ 22
[    1.904937] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    1.904941] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    1.904971] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 6
[    1.905006] uhci_hcd 0000:00:1d.1: irq 22, io base 0x00006060
[    1.905083] usb usb6: configuration #1 chosen from 1 choice
[    1.905109] hub 6-0:1.0: USB hub found
[    1.905115] hub 6-0:1.0: 2 ports detected
[    1.905165] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    1.905171] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    1.905175] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    1.905208] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 7
[    1.905235] uhci_hcd 0000:00:1d.2: irq 18, io base 0x00006040
[    1.905309] usb usb7: configuration #1 chosen from 1 choice
[    1.905337] hub 7-0:1.0: USB hub found
[    1.905343] hub 7-0:1.0: 2 ports detected
[    1.905440] PNP: PS/2 Controller [PNP0303:KBC,PNP0f13:MOUE] at 0x60,0x64 irq 1,12
[    1.955986] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.955992] serio: i8042 AUX port at 0x60,0x64 irq 12
[    1.956058] mice: PS/2 mouse device common for all mice
[    1.956188] rtc_cmos 00:03: RTC can wake from S4
[    1.956219] rtc_cmos 00:03: rtc core: registered rtc_cmos as rtc0
[    1.956252] rtc0: alarms up to one month, 242 bytes nvram, hpet irqs
[    1.956350] device-mapper: uevent: version 1.0.3
[    1.956434] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: dm-devel@redhat.com
[    1.956492] device-mapper: multipath: version 1.1.0 loaded
[    1.956495] device-mapper: multipath round-robin: version 1.0.0 loaded
[    1.956609] EISA: Probing bus 0 at eisa.0
[    1.956615] Cannot allocate resource for EISA slot 1
[    1.956617] Cannot allocate resource for EISA slot 2
[    1.956619] Cannot allocate resource for EISA slot 3
[    1.956621] Cannot allocate resource for EISA slot 4
[    1.956623] Cannot allocate resource for EISA slot 5
[    1.956625] Cannot allocate resource for EISA slot 6
[    1.956636] EISA: Detected 0 cards.
[    1.956774] cpuidle: using governor ladder
[    1.958948] cpuidle: using governor menu
[    1.959434] TCP cubic registered
[    1.959597] NET: Registered protocol family 10
[    1.960055] lo: Disabled Privacy Extensions
[    1.960392] NET: Registered protocol family 17
[    1.960408] Bluetooth: L2CAP ver 2.13
[    1.960410] Bluetooth: L2CAP socket layer initialized
[    1.960412] Bluetooth: SCO (Voice Link) ver 0.6
[    1.960414] Bluetooth: SCO socket layer initialized
[    1.960450] Bluetooth: RFCOMM TTY layer initialized
[    1.960454] Bluetooth: RFCOMM socket layer initialized
[    1.960455] Bluetooth: RFCOMM ver 1.11
[    1.960959] Using IPI No-Shortcut mode
[    1.961019] PM: Resume from disk failed.
[    1.961031] registered taskstats version 1
[    1.961160]   Magic number: 10:394:173
[    1.961186] pci_express 0000:00:1c.0:pcie01: hash matches
[    1.961198] acpi device:36: hash matches
[    1.961258] rtc_cmos 00:03: setting system clock to 2010-01-10 10:09:33 UTC (1263118173)
[    1.961262] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.961264] EDD information not available.
[    1.993400] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input5
[    2.017265] ACPI: Battery Slot [BAT0] (battery present)
[    2.272051] usb 2-5: new high speed USB device using ehci_hcd and address 3
[    2.356055] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    2.358215] ata1.00: ACPI cmd 00/00:00:00:00:00:a0 rejected by device (Stat=0x51 Err=0x04)
[    2.358360] ata1.00: ACPI cmd ef/10:01:00:00:00:a0 rejected by device (Stat=0x51 Err=0x04)
[    2.358459] ata1.00: ACPI cmd ef/10:02:00:00:00:a0 succeeded
[    2.358465] ata1.00: ACPI cmd ef/10:03:00:00:00:a0 filtered out
[    2.358595] ata1.00: ACPI cmd ef/10:04:00:00:00:a0 rejected by device (Stat=0x51 Err=0x04)
[    2.358722] ata1.00: ACPI cmd ef/10:05:00:00:00:a0 rejected by device (Stat=0x51 Err=0x04)
[    2.360269] ata1.00: ATA-8: WDC WD2500BEVT-60ZCT1, 13.01A13, max UDMA/100
[    2.360275] ata1.00: 488397168 sectors, multi 0: LBA48 NCQ (depth 31/32)
[    2.362569] ata1.00: ACPI cmd 00/00:00:00:00:00:a0 rejected by device (Stat=0x51 Err=0x04)
[    2.362768] ata1.00: ACPI cmd ef/10:01:00:00:00:a0 rejected by device (Stat=0x51 Err=0x04)
[    2.362774] ata1.00: ACPI cmd ef/10:03:00:00:00:a0 filtered out
[    2.362911] ata1.00: ACPI cmd ef/10:04:00:00:00:a0 rejected by device (Stat=0x51 Err=0x04)
[    2.363063] ata1.00: ACPI cmd ef/10:05:00:00:00:a0 rejected by device (Stat=0x51 Err=0x04)
[    2.363108] ata1.00: configured for UDMA/100
[    2.376221] scsi 0:0:0:0: Direct-Access     ATA      WDC WD2500BEVT-6 13.0 PQ: 0 ANSI: 5
[    2.376339] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    2.376355] sd 0:0:0:0: [sda] 488397168 512-byte logical blocks: (250 GB/232 GiB)
[    2.376402] sd 0:0:0:0: [sda] Write Protect is off
[    2.376404] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    2.376428] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.376563]  sda:
[    2.410552] usb 2-5: configuration #1 chosen from 1 choice
[    2.418688]  sda1 sda2 sda3 < sda5 sda6 >
[    2.453209] sd 0:0:0:0: [sda] Attached SCSI disk
[    2.500050] Clocksource tsc unstable (delta = -323787461 ns)
[    2.648047] usb 5-1: new low speed USB device using uhci_hcd and address 2
[    2.816905] usb 5-1: configuration #1 chosen from 1 choice
[    3.264136] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    3.266970] ata2.00: ACPI cmd 00/00:00:00:00:00:b0 rejected by device (Stat=0x51 Err=0x04)
[    3.267417] ata2.00: ACPI cmd ef/10:01:00:00:00:b0 rejected by device (Stat=0x51 Err=0x04)
[    3.267885] ata2.00: ACPI cmd ef/10:02:00:00:00:b0 rejected by device (Stat=0x51 Err=0x04)
[    3.267890] ata2.00: ACPI cmd ef/10:03:00:00:00:b0 filtered out
[    3.268333] ata2.00: ACPI cmd ef/10:04:00:00:00:b0 rejected by device (Stat=0x51 Err=0x04)
[    3.268805] ata2.00: ACPI cmd ef/10:05:00:00:00:b0 rejected by device (Stat=0x51 Err=0x04)
[    3.268812] ata2.00: ATAPI: PIONEER DVDRW  DR-TD08HB, 1T10, max UDMA/100
[    3.272092] ata2.00: ACPI cmd 00/00:00:00:00:00:b0 rejected by device (Stat=0x51 Err=0x04)
[    3.272627] ata2.00: ACPI cmd ef/10:01:00:00:00:b0 rejected by device (Stat=0x51 Err=0x04)
[    3.273071] ata2.00: ACPI cmd ef/10:02:00:00:00:b0 rejected by device (Stat=0x51 Err=0x04)
[    3.273077] ata2.00: ACPI cmd ef/10:03:00:00:00:b0 filtered out
[    3.273607] ata2.00: ACPI cmd ef/10:04:00:00:00:b0 rejected by device (Stat=0x51 Err=0x04)
[    3.274053] ata2.00: ACPI cmd ef/10:05:00:00:00:b0 rejected by device (Stat=0x51 Err=0x04)
[    3.274097] ata2.00: configured for UDMA/100
[    3.368069] scsi 1:0:0:0: CD-ROM            PIONEER  DVDRW  DR-TD08HB 1T10 PQ: 0 ANSI: 5
[    3.725411] sr0: scsi3-mmc drive: 8x/8x writer dvd-ram cd/rw xa/form2 cdda tray
[    3.725415] Uniform CD-ROM driver Revision: 3.20
[    3.725543] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    3.725598] sr 1:0:0:0: Attached scsi generic sg1 type 5
[    4.044110] ata5: SATA link down (SStatus 0 SControl 300)
[    4.380112] ata6: SATA link down (SStatus 0 SControl 300)
[    4.396171] Freeing unused kernel memory: 540k freed
[    4.396526] Write protecting the kernel text: 4568k
[    4.396582] Write protecting the kernel read-only data: 1836k
[    4.702535] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    4.702558] r8169 0000:03:00.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    4.702607] r8169 0000:03:00.0: setting latency timer to 64
[    4.702668]   alloc irq_desc for 30 on node -1
[    4.702670]   alloc kstat_irqs on node -1
[    4.702687] r8169 0000:03:00.0: irq 30 for MSI/MSI-X
[    4.703333] eth0: RTL8102e at 0xf80cc000, 00:1e:ec:f8:7c:a0, XID 24a00000 IRQ 30
[    4.711666] Linux agpgart interface v0.103
[    4.714544] agpgart-intel 0000:00:00.0: Intel Mobile Intel® GM45 Express Chipset
[    4.715302] agpgart-intel 0000:00:00.0: detected 65532K stolen memory
[    4.741651] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0xc0000000
[    4.785043] [drm] Initialized drm 1.1.0 20060810
[    4.796171] i915 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    4.796177] i915 0000:00:02.0: setting latency timer to 64
[    4.798395]   alloc irq_desc for 31 on node -1
[    4.798398]   alloc kstat_irqs on node -1
[    4.798408] i915 0000:00:02.0: irq 31 for MSI/MSI-X
[    4.900467] usbcore: registered new interface driver hiddev
[    4.905429] [drm] i2c_init DPDDC-B
[    4.915095] [drm] i2c_init DPDDC-D
[    4.917087] input: USB Optical Mouse as /devices/pci0000:00/0000:00:1d.0/usb5/5-1/5-1:1.0/input/input6
[    4.917194] generic-usb 0003:1BCF:0007.0001: input,hiddev96,hidraw0: USB HID v1.10 Mouse [USB Optical Mouse] on usb-0000:00:1d.0-1/input0
[    4.917209] usbcore: registered new interface driver usbhid
[    4.917212] usbhid: v2.6:USB HID core driver
[    5.035316] i2c-adapter i2c-2: unable to read EDID block.
[    5.035320] i915 0000:00:02.0: HDMI Type A-1: no EDID data
[    5.043600] [drm] fb0: inteldrmfb frame buffer device
[    5.044799] [Firmware Bug]: ACPI: ACPI brightness control misses _BQC function
[    5.055349] acpi device:04: registered as cooling_device3
[    5.055617] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:01/input/input7
[    5.055649] ACPI: Video Device [OVGA] (multi-head: yes  rom: no  post: no)
[    5.055703] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
[    5.471321] [drm] LVDS-8: set mode 1280x800 14
[    6.080082] Console: switching to colour frame buffer device 160x50
[    6.368775] PM: Starting manual resume from disk
[    6.368778] PM: Resume from partition 8:6
[    6.368781] PM: Checking hibernation image.
[    6.368998] PM: Resume from disk failed.
[    6.394613] EXT4-fs (sda5): barriers enabled
[    6.416942] kjournald2 starting: pid 462, dev sda5:8, commit interval 5 seconds
[    6.416983] EXT4-fs (sda5): delayed allocation enabled
[    6.416993] EXT4-fs: file extents enabled
[    6.423389] EXT4-fs: mballoc enabled
[    6.423402] EXT4-fs (sda5): mounted filesystem with ordered data mode
[    7.093452] type=1505 audit(1263118178.631:2): operation="profile_load" pid=485 name=/usr/share/gdm/guest-session/Xsession
[    7.096402] type=1505 audit(1263118178.634:3): operation="profile_load" pid=486 name=/sbin/dhclient3
[    7.097217] type=1505 audit(1263118178.634:4): operation="profile_load" pid=486 name=/usr/lib/NetworkManager/nm-dhcp-client.action
[    7.097617] type=1505 audit(1263118178.634:5): operation="profile_load" pid=486 name=/usr/lib/connman/scripts/dhclient-script
[    7.156106] type=1505 audit(1263118178.694:6): operation="profile_load" pid=487 name=/usr/bin/evince
[    7.167928] type=1505 audit(1263118178.702:7): operation="profile_load" pid=487 name=/usr/bin/evince-previewer
[    7.174874] type=1505 audit(1263118178.710:8): operation="profile_load" pid=487 name=/usr/bin/evince-thumbnailer
[    7.196471] type=1505 audit(1263118178.734:9): operation="profile_load" pid=489 name=/usr/lib/cups/backend/cups-pdf
[    7.197339] type=1505 audit(1263118178.734:10): operation="profile_load" pid=489 name=/usr/sbin/cupsd
[    7.200142] type=1505 audit(1263118178.738:11): operation="profile_load" pid=490 name=/usr/sbin/tcpdump
[   17.372999] udev: starting version 147
[   17.401877] Adding 3461968k swap on /dev/sda6.  Priority:-1 extents:1 across:3461968k 
[   17.595276] lirc_dev: IR Remote Control driver registered, major 61 
[   17.597834] lirc_dev: lirc_register_driver: sample_rate: 0
[   17.597945] enecir: KB3926C detected, driver support is not complete!
[   17.597948] enecir: chip is 0x3926 - 0x00, 0xc0
[   17.597956] enecir: hardware features:
[   17.597958] enecir: learning and tx off, gpio40_learn off, fan_in off
[   17.597960] enecir: driver has been succesfully loaded
[   17.699682] EXT4-fs (sda5): internal journal on sda5:8
[   17.704340] sdhci: Secure Digital Host Controller Interface driver
[   17.704342] sdhci: Copyright(c) Pierre Ossman
[   17.706025] sdhci-pci 0000:04:00.0: SDHCI controller found [197b:2382] (rev 0)
[   17.706049] sdhci-pci 0000:04:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   17.706090] sdhci-pci 0000:04:00.0: setting latency timer to 64
[   17.706127] Registered led device: mmc0::
[   17.706163] mmc0: SDHCI controller on PCI [0000:04:00.0] using ADMA
[   17.706175] sdhci-pci 0000:04:00.2: SDHCI controller found [197b:2381] (rev 0)
[   17.706192] sdhci-pci 0000:04:00.2: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   17.706199] sdhci-pci 0000:04:00.2: Refusing to bind to secondary interface.
[   17.706207] sdhci-pci 0000:04:00.2: PCI INT A disabled
[   17.723678] jmb38x_ms 0000:04:00.3: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   17.723688] jmb38x_ms 0000:04:00.3: setting latency timer to 64
[   17.753258] lis3lv02d: laptop model unknown, using default axes configuration
[   17.753984] lis3lv02d: 1-byte sensor found
[   17.763339] input: ST LIS3LV02DL Accelerometer as /devices/platform/lis3lv02d/input/input8
[   17.763447] Registered led device: hp::hddprotect
[   17.763464] lis3lv02d driver loaded.
[   17.765678] lp: driver loaded but no devices found
[   17.766796] lib80211: common routines for IEEE802.11 drivers
[   17.766799] lib80211_crypt: registered algorithm 'NULL'
[   17.815470] Linux video capture interface: v2.00
[   17.822395] ip_tables: (C) 2000-2006 Netfilter Core Team
[   17.843514] uvcvideo: Found UVC 1.00 device HP Webcam (090c:c371)
[   17.845935] input: HP Webcam as /devices/pci0000:00/0000:00:1d.7/usb2/2-5/2-5:1.0/input/input9
[   17.845980] usbcore: registered new interface driver uvcvideo
[   17.845983] USB Video Class driver (v0.1.0)
[   17.911782] wl: module license 'MIXED/Proprietary' taints kernel.
[   17.911786] Disabling lock debugging due to kernel taint
[   17.913871] wl 0000:02:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[   17.913885] wl 0000:02:00.0: setting latency timer to 64
[   17.937803] lib80211_crypt: registered algorithm 'TKIP'
[   17.937956] eth1: Broadcom BCM4315 802.11 Wireless Controller 5.10.91.9
[   17.945565] udev: renamed network interface eth1 to eth2
[   18.211583] HDA Intel 0000:00:1b.0: power state changed by ACPI to D0
[   18.211595] HDA Intel 0000:00:1b.0: PCI INT B -> GSI 22 (level, low) -> IRQ 22
[   18.211601] hda_intel: msi for device 103c:30f7 set to 1
[   18.211670]   alloc irq_desc for 32 on node -1
[   18.211673]   alloc kstat_irqs on node -1
[   18.211687] HDA Intel 0000:00:1b.0: irq 32 for MSI/MSI-X
[   18.211725] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   18.267838] type=1505 audit(1263136189.802:12): operation="profile_replace" pid=992 name=/usr/share/gdm/guest-session/Xsession
[   18.269907] type=1505 audit(1263136189.806:13): operation="profile_replace" pid=993 name=/sbin/dhclient3
[   18.270646] type=1505 audit(1263136189.806:14): operation="profile_replace" pid=993 name=/usr/lib/NetworkManager/nm-dhcp-client.action
[   18.271049] type=1505 audit(1263136189.806:15): operation="profile_replace" pid=993 name=/usr/lib/connman/scripts/dhclient-script
[   18.274805] type=1505 audit(1263136189.810:16): operation="profile_replace" pid=994 name=/usr/bin/evince
[   18.287549] type=1505 audit(1263136189.822:17): operation="profile_replace" pid=994 name=/usr/bin/evince-previewer
[   18.296999] type=1505 audit(1263136189.834:18): operation="profile_replace" pid=994 name=/usr/bin/evince-thumbnailer
[   18.308037] type=1505 audit(1263136189.842:19): operation="profile_replace" pid=1000 name=/usr/lib/cups/backend/cups-pdf
[   18.308912] type=1505 audit(1263136189.842:20): operation="profile_replace" pid=1000 name=/usr/sbin/cupsd
[   18.311359] type=1505 audit(1263136189.849:21): operation="profile_replace" pid=1001 name=/usr/sbin/tcpdump
[   18.365444] input: HDA Digital PCBeep as /devices/pci0000:00/0000:00:1b.0/input/input10
[   18.616076] r8169: eth0: link down
[   18.616270] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   18.702062] input: HDA Intel Mic at Ext Front Jack as /devices/pci0000:00/0000:00:1b.0/sound/card0/input11
[   18.702140] input: HDA Intel Mic at Sep UNKNOWN Jack as /devices/pci0000:00/0000:00:1b.0/sound/card0/input12
[   18.702202] input: HDA Intel HP Out at Ext Front Jack as /devices/pci0000:00/0000:00:1b.0/sound/card0/input13
[   18.780278] input: PS/2 Mouse as /devices/platform/i8042/serio1/input/input14
[   18.826555] input: AlpsPS/2 ALPS GlidePoint as /devices/platform/i8042/serio1/input/input15
[   19.101689] i2c-adapter i2c-2: unable to read EDID block.
[   19.101694] i915 0000:00:02.0: HDMI Type A-1: no EDID data
[   19.107064] i2c-adapter i2c-2: unable to read EDID block.
[   19.107068] i915 0000:00:02.0: HDMI Type A-1: no EDID data
[   19.253631] i2c-adapter i2c-2: unable to read EDID block.
[   19.253636] i915 0000:00:02.0: HDMI Type A-1: no EDID data
[   19.258051] i2c-adapter i2c-2: unable to read EDID block.
[   19.258054] i915 0000:00:02.0: HDMI Type A-1: no EDID data
[   19.372399] ppdev: user-space parallel port driver
[   20.778180] CPU0 attaching NULL sched-domain.
[   20.778185] CPU1 attaching NULL sched-domain.
[   20.788623] CPU0 attaching sched-domain:
[   20.788629]  domain 0: span 0-1 level MC
[   20.788634]   groups: 0 1
[   20.788642] CPU1 attaching sched-domain:
[   20.788646]  domain 0: span 0-1 level MC
[   20.788650]   groups: 1 0
[   22.646516] CPU0 attaching NULL sched-domain.
[   22.646521] CPU1 attaching NULL sched-domain.
[   22.660126] CPU0 attaching sched-domain:
[   22.660133]  domain 0: span 0-1 level MC
[   22.660137]   groups: 0 1
[   22.660147] CPU1 attaching sched-domain:
[   22.660150]  domain 0: span 0-1 level MC
[   22.660154]   groups: 1 0
[   23.014722] i2c-adapter i2c-2: unable to read EDID block.
[   23.014726] i915 0000:00:02.0: HDMI Type A-1: no EDID data
[   23.019415] i2c-adapter i2c-2: unable to read EDID block.
[   23.019418] i915 0000:00:02.0: HDMI Type A-1: no EDID data
[   23.159151] i2c-adapter i2c-2: unable to read EDID block.
[   23.159155] i915 0000:00:02.0: HDMI Type A-1: no EDID data
[   23.163811] i2c-adapter i2c-2: unable to read EDID block.
[   23.163815] i915 0000:00:02.0: HDMI Type A-1: no EDID data
[   23.301213] i2c-adapter i2c-2: unable to read EDID block.
[   23.301218] i915 0000:00:02.0: HDMI Type A-1: no EDID data
[   23.306037] i2c-adapter i2c-2: unable to read EDID block.
[   23.306041] i915 0000:00:02.0: HDMI Type A-1: no EDID data
[   24.099236] i2c-adapter i2c-2: unable to read EDID block.
[   24.099241] i915 0000:00:02.0: HDMI Type A-1: no EDID data
[   24.103768] i2c-adapter i2c-2: unable to read EDID block.
[   24.103771] i915 0000:00:02.0: HDMI Type A-1: no EDID data
[   28.648039] eth2: no IPv6 routers present
```

postdmesg.txt

```
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.31-17-generic (buildd@palmer) (gcc version 4.4.1 (Ubuntu 4.4.1-4ubuntu8) ) #54-Ubuntu SMP Thu Dec 10 16:20:31 UTC 2009 (Ubuntu 2.6.31-17.54-generic)
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
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009e000 (usable)
[    0.000000]  BIOS-e820: 000000000009e000 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 00000000b9e6b000 (usable)
[    0.000000]  BIOS-e820: 00000000b9e6b000 - 00000000b9ebf000 (reserved)
[    0.000000]  BIOS-e820: 00000000b9ebf000 - 00000000b9f83000 (usable)
[    0.000000]  BIOS-e820: 00000000b9f83000 - 00000000b9fbf000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000b9fbf000 - 00000000b9fdf000 (usable)
[    0.000000]  BIOS-e820: 00000000b9fdf000 - 00000000b9ff6000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000b9ff6000 - 00000000b9ffe000 (usable)
[    0.000000]  BIOS-e820: 00000000b9ffe000 - 00000000b9fff000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000b9fff000 - 00000000ba000000 (usable)
[    0.000000]  BIOS-e820: 00000000ba000000 - 00000000c0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000f8000000 - 00000000fc000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed10000 - 00000000fed14000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed18000 - 00000000fed1a000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed1c000 - 00000000fed20000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fff00000 - 0000000100000000 (reserved)
[    0.000000]  BIOS-e820: 0000000100000000 - 0000000140000000 (usable)
[    0.000000] DMI 2.4 present.
[    0.000000] last_pfn = 0xba000 max_arch_pfn = 0x100000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-EFFFF write-through
[    0.000000]   F0000-FFFFF write-combining
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000 mask F80000000 write-back
[    0.000000]   1 base 0FFF00000 mask FFFF00000 write-protect
[    0.000000]   2 base 080000000 mask FC0000000 write-back
[    0.000000]   3 base 0BC000000 mask FFC000000 uncachable
[    0.000000]   4 base 0BA000000 mask FFE000000 uncachable
[    0.000000]   5 base 100000000 mask FC0000000 write-back
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] e820 update range: 0000000000002000 - 0000000000006000 (usable) ==> (reserved)
[    0.000000] Scanning 1 areas for low memory corruption
[    0.000000] modified physical RAM map:
[    0.000000]  modified: 0000000000000000 - 0000000000002000 (usable)
[    0.000000]  modified: 0000000000002000 - 0000000000006000 (reserved)
[    0.000000]  modified: 0000000000006000 - 000000000009e000 (usable)
[    0.000000]  modified: 000000000009e000 - 00000000000a0000 (reserved)
[    0.000000]  modified: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  modified: 0000000000100000 - 00000000b9e6b000 (usable)
[    0.000000]  modified: 00000000b9e6b000 - 00000000b9ebf000 (reserved)
[    0.000000]  modified: 00000000b9ebf000 - 00000000b9f83000 (usable)
[    0.000000]  modified: 00000000b9f83000 - 00000000b9fbf000 (ACPI NVS)
[    0.000000]  modified: 00000000b9fbf000 - 00000000b9fdf000 (usable)
[    0.000000]  modified: 00000000b9fdf000 - 00000000b9ff6000 (ACPI data)
[    0.000000]  modified: 00000000b9ff6000 - 00000000b9ffe000 (usable)
[    0.000000]  modified: 00000000b9ffe000 - 00000000b9fff000 (ACPI data)
[    0.000000]  modified: 00000000b9fff000 - 00000000ba000000 (usable)
[    0.000000]  modified: 00000000ba000000 - 00000000c0000000 (reserved)
[    0.000000]  modified: 00000000f8000000 - 00000000fc000000 (reserved)
[    0.000000]  modified: 00000000fec00000 - 00000000fec01000 (reserved)
[    0.000000]  modified: 00000000fed10000 - 00000000fed14000 (reserved)
[    0.000000]  modified: 00000000fed18000 - 00000000fed1a000 (reserved)
[    0.000000]  modified: 00000000fed1c000 - 00000000fed20000 (reserved)
[    0.000000]  modified: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  modified: 00000000fff00000 - 0000000100000000 (reserved)
[    0.000000]  modified: 0000000100000000 - 0000000140000000 (usable)
[    0.000000] initial memory mapped : 0 - 00c00000
[    0.000000] init_memory_mapping: 0000000000000000-00000000377fe000
[    0.000000] Using x86 segment limits to approximate NX protection
[    0.000000]  0000000000 - 0000400000 page 4k
[    0.000000]  0000400000 - 0037400000 page 2M
[    0.000000]  0037400000 - 00377fe000 page 4k
[    0.000000] kernel direct mapping tables up to 377fe000 @ 7000-c000
[    0.000000] RAMDISK: 378a3000 - 37fef6df
[    0.000000] Allocated new RAMDISK: 008ad000 - 00ff96df
[    0.000000] Move RAMDISK from 00000000378a3000 - 0000000037fef6de to 008ad000 - 00ff96de
[    0.000000] ACPI: RSDP 000fe020 00024 (v02 HP    )
[    0.000000] ACPI: XSDT b9ffe120 00074 (v01 HPQOEM SLIC-MPC 00000001      01000013)
[    0.000000] ACPI: FACP b9ff3000 000F4 (v04 HP     BLADE    00000001 MSFT 01000013)
[    0.000000] ACPI: DSDT b9fe4000 0A96B (v01 HP     BLADE    00000001 MSFT 01000013)
[    0.000000] ACPI: FACS b9f8c000 00040
[    0.000000] ACPI: DMAR b9ff5000 00068 (v01                00000001      00000000)
[    0.000000] ACPI: SSDT b9ff4000 00655 (v01  PmRef    CpuPm 00003000 INTL 20051117)
[    0.000000] ACPI: HPET b9ff2000 00038 (v01 HPQOEM SLIC-MPC 00000001 MSFT 01000013)
[    0.000000] ACPI: APIC b9ff1000 0006C (v02 HPQOEM SLIC-MPC 00000001 MSFT 01000013)
[    0.000000] ACPI: MCFG b9ff0000 0003C (v01 HPQOEM SLIC-MPC 00000001 MSFT 01000013)
[    0.000000] ACPI: ASF! b9fef000 000A5 (v32 HPQOEM SLIC-MPC 00000001 MSFT 01000013)
[    0.000000] ACPI: SLIC b9fe3000 00176 (v01 HPQOEM SLIC-MPC 00000001 LOHR 000F4240)
[    0.000000] ACPI: BOOT b9fe2000 00028 (v01 HPQOEM SLIC-MPC 00000001 MSFT 01000013)
[    0.000000] ACPI: SSDT b9fe1000 00296 (v01 INTEL  SataAhci 00001000 INTL 20051117)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] 2088MB HIGHMEM available.
[    0.000000] 887MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 377fe000
[    0.000000]   low ram: 0 - 377fe000
[    0.000000]   node 0 low ram: 00000000 - 377fe000
[    0.000000]   node 0 bootmap 00008000 - 0000ef00
[    0.000000] (9 early reservations) ==> bootmem [0000000000 - 00377fe000]
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
[    0.000000]   #1 [0000001000 - 0000002000]    EX TRAMPOLINE ==> [0000001000 - 0000002000]
[    0.000000]   #2 [0000006000 - 0000007000]       TRAMPOLINE ==> [0000006000 - 0000007000]
[    0.000000]   #3 [0000100000 - 00008a80a0]    TEXT DATA BSS ==> [0000100000 - 00008a80a0]
[    0.000000]   #4 [000009e000 - 0000100000]    BIOS reserved ==> [000009e000 - 0000100000]
[    0.000000]   #5 [00008a9000 - 00008ac1a4]              BRK ==> [00008a9000 - 00008ac1a4]
[    0.000000]   #6 [0000007000 - 0000008000]          PGTABLE ==> [0000007000 - 0000008000]
[    0.000000]   #7 [00008ad000 - 0000ff96df]      NEW RAMDISK ==> [00008ad000 - 0000ff96df]
[    0.000000]   #8 [0000008000 - 000000f000]          BOOTMAP ==> [0000008000 - 000000f000]
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000000 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x000377fe
[    0.000000]   HighMem  0x000377fe -> 0x000ba000
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[7] active PFN ranges
[    0.000000]     0: 0x00000000 -> 0x00000002
[    0.000000]     0: 0x00000006 -> 0x0000009e
[    0.000000]     0: 0x00000100 -> 0x000b9e6b
[    0.000000]     0: 0x000b9ebf -> 0x000b9f83
[    0.000000]     0: 0x000b9fbf -> 0x000b9fdf
[    0.000000]     0: 0x000b9ff6 -> 0x000b9ffe
[    0.000000]     0: 0x000b9fff -> 0x000ba000
[    0.000000] On node 0 totalpages: 761586
[    0.000000] free_area_init_node: node 0, pgdat c0784960, node_mem_map c1000000
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3962 pages, LIFO batch:0
[    0.000000]   Normal zone: 1744 pages used for memmap
[    0.000000]   Normal zone: 221486 pages, LIFO batch:31
[    0.000000]   HighMem zone: 4177 pages used for memmap
[    0.000000]   HighMem zone: 530185 pages, LIFO batch:31
[    0.000000] Using APIC driver default
[    0.000000] ACPI: PM-Timer IO Port: 0x408
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x00] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x00] disabled)
[    0.000000] ACPI: IOAPIC (id[0x04] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 4, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000
[    0.000000] SMP: Allowing 4 CPUs, 2 hotplug CPUs
[    0.000000] nr_irqs_gsi: 24
[    0.000000] PM: Registered nosave memory: 0000000000002000 - 0000000000006000
[    0.000000] PM: Registered nosave memory: 000000000009e000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
[    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at c0000000 (gap: c0000000:38000000)
[    0.000000] NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:4 nr_node_ids:1
[    0.000000] PERCPU: Embedded 14 pages at c2750000, static data 35612 bytes
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 755633
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.31-17-generic root=UUID=9e82b147-8c2d-4bd2-b1b2-d5695d16aeac ro quiet splash
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] allocated 15237120 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] Initializing HighMem for node 0 (000377fe:000ba000)
[    0.000000] Memory: 2990364k/3047424k available (4566k kernel code, 55132k reserved, 2142k data, 540k init, 2137448k highmem)
[    0.000000] virtual kernel memory layout:
[    0.000000]     fixmap  : 0xfff1d000 - 0xfffff000   ( 904 kB)
[    0.000000]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[    0.000000]     vmalloc : 0xf7ffe000 - 0xff7fe000   ( 120 MB)
[    0.000000]     lowmem  : 0xc0000000 - 0xf77fe000   ( 887 MB)
[    0.000000]       .init : 0xc078e000 - 0xc0815000   ( 540 kB)
[    0.000000]       .data : 0xc0575a64 - 0xc078d408   (2142 kB)
[    0.000000]       .text : 0xc0100000 - 0xc0575a64   (4566 kB)
[    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.000000] SLUB: Genslabs=13, HWalign=64, Order=0-3, MinObjects=0, CPUs=4, Nodes=1
[    0.000000] NR_IRQS:2304 nr_irqs:440
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 1995.088 MHz processor.
[    0.001327] Console: colour VGA+ 80x25
[    0.001330] console [tty0] enabled
[    0.001496] hpet clockevent registered
[    0.001500] HPET: 4 timers in total, 0 timers will be used for per-cpu timer
[    0.001506] Calibrating delay loop (skipped), value calculated using timer frequency.. 3990.17 BogoMIPS (lpj=7980352)
[    0.001523] Security Framework initialized
[    0.001542] AppArmor: AppArmor initialized
[    0.001549] Mount-cache hash table entries: 512
[    0.001674] Initializing cgroup subsys ns
[    0.001679] Initializing cgroup subsys cpuacct
[    0.001683] Initializing cgroup subsys memory
[    0.001690] Initializing cgroup subsys freezer
[    0.001692] Initializing cgroup subsys net_cls
[    0.001706] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.001709] CPU: L2 cache: 2048K
[    0.001711] CPU: Physical Processor ID: 0
[    0.001713] CPU: Processor Core ID: 0
[    0.001716] mce: CPU supports 6 MCE banks
[    0.001724] CPU0: Thermal monitoring enabled (TM1)
[    0.001728] using mwait in idle threads.
[    0.001734] Performance Counters: Core2 events, Intel PMU driver.
[    0.001743] ... version:                 2
[    0.001744] ... bit width:               40
[    0.001746] ... generic counters:        2
[    0.001748] ... value mask:              000000ffffffffff
[    0.001750] ... max period:              000000007fffffff
[    0.001752] ... fixed-purpose counters:  3
[    0.001753] ... counter mask:            0000000700000003
[    0.001757] Checking 'hlt' instruction... OK.
[    0.018523] ACPI: Core revision 20090521
[    0.036397] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.076958] CPU0: Intel(R) Core(TM)2 Duo CPU     T5800  @ 2.00GHz stepping 0d
[    0.080001] Booting processor 1 APIC 0x1 ip 0x6000
[    0.004000] Initializing CPU#1
[    0.004000] Calibrating delay using timer specific routine.. 3990.46 BogoMIPS (lpj=7980920)
[    0.004000] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.004000] CPU: L2 cache: 2048K
[    0.004000] CPU: Physical Processor ID: 0
[    0.004000] CPU: Processor Core ID: 1
[    0.004000] mce: CPU supports 6 MCE banks
[    0.004000] CPU1: Thermal monitoring enabled (TM1)
[    0.004000] x86 PAT enabled: cpu 1, old 0x7040600070406, new 0x7010600070106
[    0.165434] CPU1: Intel(R) Core(TM)2 Duo CPU     T5800  @ 2.00GHz stepping 0d
[    0.165447] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
[    0.168022] Brought up 2 CPUs
[    0.168025] Total of 2 processors activated (7980.63 BogoMIPS).
[    0.168074] CPU0 attaching sched-domain:
[    0.168077]  domain 0: span 0-1 level MC
[    0.168080]   groups: 0 1
[    0.168085] CPU1 attaching sched-domain:
[    0.168087]  domain 0: span 0-1 level MC
[    0.168090]   groups: 1 0
[    0.168164] Booting paravirtualized kernel on bare hardware
[    0.168208] regulator: core version 0.5
[    0.168208] Time: 10:09:31  Date: 01/10/10
[    0.168208] NET: Registered protocol family 16
[    0.168208] EISA bus registered
[    0.168217] ACPI: bus type pci registered
[    0.168284] PCI: MCFG configuration 0: base f8000000 segment 0 buses 0 - 63
[    0.168287] PCI: MCFG area at f8000000 reserved in E820
[    0.168289] PCI: Using MMCONFIG for extended config space
[    0.168291] PCI: Using configuration type 1 for base access
[    0.169324] bio: create slab <bio-0> at 0
[    0.173027] ACPI: EC: Enabling special treatment for EC from MSI.
[    0.173029] ACPI: EC: Look up EC in DSDT
[    0.224398] ACPI: BIOS _OSI(Linux) query ignored
[    0.232017] ACPI: EC: non-query interrupt received, switching to interrupt mode
[    0.444193] ACPI: Interpreter enabled
[    0.444200] ACPI: (supports S0 S3 S4 S5)
[    0.444230] ACPI: Using IOAPIC for interrupt routing
[    0.680182] [Firmware Bug]: ACPI: ACPI brightness control misses _BQC function
[    0.680858] [Firmware Bug]: ACPI: ACPI brightness control misses _BQC function
[    0.705476] ACPI: EC: GPE = 0x17, I/O: command/status = 0x66, data = 0x62
[    0.705478] ACPI: EC: driver started in interrupt mode
[    0.712538] ACPI: Power Resource [FN00] (on)
[    0.712538] ACPI: No dock devices found.
[    0.713079] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.713180] pci 0000:00:02.0: reg 10 64bit mmio: [0xd0000000-0xd03fffff]
[    0.713189] pci 0000:00:02.0: reg 18 64bit mmio: [0xc0000000-0xcfffffff]
[    0.713194] pci 0000:00:02.0: reg 20 io port: [0x60f0-0x60f7]
[    0.713240] pci 0000:00:02.1: reg 10 64bit mmio: [0xd5400000-0xd54fffff]
[    0.713366] pci 0000:00:1a.0: reg 20 io port: [0x60c0-0x60df]
[    0.713479] pci 0000:00:1a.1: reg 20 io port: [0x60a0-0x60bf]
[    0.713599] pci 0000:00:1a.7: reg 10 32bit mmio: [0xda504c00-0xda504fff]
[    0.713675] pci 0000:00:1a.7: PME# supported from D0 D3hot D3cold
[    0.713680] pci 0000:00:1a.7: PME# disabled
[    0.713740] pci 0000:00:1b.0: reg 10 64bit mmio: [0xda500000-0xda503fff]
[    0.713803] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    0.713808] pci 0000:00:1b.0: PME# disabled
[    0.716013] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    0.716018] pci 0000:00:1c.0: PME# disabled
[    0.716110] pci 0000:00:1c.2: PME# supported from D0 D3hot D3cold
[    0.716115] pci 0000:00:1c.2: PME# disabled
[    0.716206] pci 0000:00:1c.3: PME# supported from D0 D3hot D3cold
[    0.716211] pci 0000:00:1c.3: PME# disabled
[    0.716299] pci 0000:00:1c.4: PME# supported from D0 D3hot D3cold
[    0.716304] pci 0000:00:1c.4: PME# disabled
[    0.716391] pci 0000:00:1c.5: PME# supported from D0 D3hot D3cold
[    0.716396] pci 0000:00:1c.5: PME# disabled
[    0.716487] pci 0000:00:1d.0: reg 20 io port: [0x6080-0x609f]
[    0.716610] pci 0000:00:1d.1: reg 20 io port: [0x6060-0x607f]
[    0.716740] pci 0000:00:1d.2: reg 20 io port: [0x6040-0x605f]
[    0.716856] pci 0000:00:1d.7: reg 10 32bit mmio: [0xda504800-0xda504bff]
[    0.716932] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
[    0.716937] pci 0000:00:1d.7: PME# disabled
[    0.717185] pci 0000:00:1f.2: reg 10 io port: [0x60e8-0x60ef]
[    0.717193] pci 0000:00:1f.2: reg 14 io port: [0x60fc-0x60ff]
[    0.717201] pci 0000:00:1f.2: reg 18 io port: [0x60e0-0x60e7]
[    0.717209] pci 0000:00:1f.2: reg 1c io port: [0x60f8-0x60fb]
[    0.717217] pci 0000:00:1f.2: reg 20 io port: [0x6020-0x603f]
[    0.717225] pci 0000:00:1f.2: reg 24 32bit mmio: [0xda504000-0xda5047ff]
[    0.717274] pci 0000:00:1f.2: PME# supported from D3hot
[    0.717279] pci 0000:00:1f.2: PME# disabled
[    0.717321] pci 0000:00:1f.3: reg 10 64bit mmio: [0xda505000-0xda5050ff]
[    0.717341] pci 0000:00:1f.3: reg 20 io port: [0x6000-0x601f]
[    0.717424] pci 0000:00:1c.0: bridge io port: [0x5000-0x5fff]
[    0.717430] pci 0000:00:1c.0: bridge 32bit mmio: [0xd9500000-0xda4fffff]
[    0.717438] pci 0000:00:1c.0: bridge 64bit mmio pref: [0xd0400000-0xd13fffff]
[    0.717639] pci 0000:02:00.0: reg 10 64bit mmio: [0xd8500000-0xd8503fff]
[    0.717856] pci 0000:02:00.0: supports D1 D2
[    0.717990] pci 0000:00:1c.2: bridge io port: [0x4000-0x4fff]
[    0.717995] pci 0000:00:1c.2: bridge 32bit mmio: [0xd8500000-0xd94fffff]
[    0.718003] pci 0000:00:1c.2: bridge 64bit mmio pref: [0xd1400000-0xd23fffff]
[    0.718065] pci 0000:03:00.0: reg 10 io port: [0x3000-0x30ff]
[    0.718092] pci 0000:03:00.0: reg 18 64bit mmio: [0xd2410000-0xd2410fff]
[    0.718110] pci 0000:03:00.0: reg 20 64bit mmio: [0xd2400000-0xd240ffff]
[    0.718121] pci 0000:03:00.0: reg 30 32bit mmio: [0xfffe0000-0xffffffff]
[    0.718174] pci 0000:03:00.0: supports D1 D2
[    0.718176] pci 0000:03:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.718182] pci 0000:03:00.0: PME# disabled
[    0.718263] pci 0000:00:1c.3: bridge io port: [0x3000-0x3fff]
[    0.718268] pci 0000:00:1c.3: bridge 32bit mmio: [0xd7500000-0xd84fffff]
[    0.718276] pci 0000:00:1c.3: bridge 64bit mmio pref: [0xd2400000-0xd33fffff]
[    0.718334] pci 0000:04:00.0: reg 10 32bit mmio: [0xd6500300-0xd65003ff]
[    0.718507] pci 0000:04:00.2: reg 10 32bit mmio: [0xd6500200-0xd65002ff]
[    0.718671] pci 0000:04:00.3: reg 10 32bit mmio: [0xd6500100-0xd65001ff]
[    0.718832] pci 0000:04:00.4: reg 10 32bit mmio: [0xd6500000-0xd65000ff]
[    0.719002] pci 0000:00:1c.4: bridge io port: [0x2000-0x2fff]
[    0.719007] pci 0000:00:1c.4: bridge 32bit mmio: [0xd6500000-0xd74fffff]
[    0.719015] pci 0000:00:1c.4: bridge 64bit mmio pref: [0xd3400000-0xd43fffff]
[    0.719075] pci 0000:00:1c.5: bridge io port: [0x1000-0x1fff]
[    0.719080] pci 0000:00:1c.5: bridge 32bit mmio: [0xd5500000-0xd64fffff]
[    0.719087] pci 0000:00:1c.5: bridge 64bit mmio pref: [0xd4400000-0xd53fffff]
[    0.719149] pci 0000:00:1e.0: transparent bridge
[    0.719200] pci_bus 0000:00: on NUMA node 0
[    0.719207] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.719531] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P32_._PRT]
[    0.719684] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.EXP1._PRT]
[    0.719794] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.EXP3._PRT]
[    0.719914] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.EXP4._PRT]
[    0.720039] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.EXP5._PRT]
[    0.720201] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.EXP6._PRT]
[    0.729634] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 7 9 10 *11 12)
[    0.729779] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 7 9 *10 11 12)
[    0.729921] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 7 9 10 *11 12)
[    0.730062] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 7 9 10 *11 12)
[    0.730203] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 7 9 10 *11 12)
[    0.730344] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 7 9 10 *11 12)
[    0.730484] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 7 9 10 *11 12)
[    0.730625] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 7 9 10 11 12) *0, disabled.
[    0.730835] SCSI subsystem initialized
[    0.732017] libata version 3.00 loaded.
[    0.732044] usbcore: registered new interface driver usbfs
[    0.732044] usbcore: registered new interface driver hub
[    0.732046] usbcore: registered new device driver usb
[    0.732090] ACPI: WMI: Mapper loaded
[    0.732092] PCI: Using ACPI for IRQ routing
[    0.740008] Bluetooth: Core ver 2.15
[    0.740014] NET: Registered protocol family 31
[    0.740015] Bluetooth: HCI device and connection manager initialized
[    0.740018] Bluetooth: HCI socket layer initialized
[    0.740020] NetLabel: Initializing
[    0.740021] NetLabel:  domain hash size = 128
[    0.740023] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.740037] NetLabel:  unlabeled traffic allowed by default
[    0.740069] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0
[    0.740075] hpet0: 4 comparators, 64-bit 14.318180 MHz counter
[    0.748013] Switched to high resolution mode on CPU 0
[    0.749469] Switched to high resolution mode on CPU 1
[    0.756510] pnp: PnP ACPI init
[    0.756520] ACPI: bus type pnp registered
[    0.877196] pnp 00:01: io resource (0x164e-0x164f) overlaps 0000:00:1c.5 BAR 13 (0x1000-0x1fff), disabling
[    0.877988]   alloc irq_desc for 23 on node -1
[    0.877991]   alloc kstat_irqs on node -1
[    0.878500] pnp: PnP ACPI: found 11 devices
[    0.878502] ACPI: ACPI bus type pnp unregistered
[    0.878506] PnPBIOS: Disabled by ACPI PNP
[    0.878517] system 00:01: ioport range 0x600-0x60f has been reserved
[    0.878520] system 00:01: ioport range 0x610-0x610 has been reserved
[    0.878523] system 00:01: ioport range 0x800-0x80f has been reserved
[    0.878526] system 00:01: ioport range 0x810-0x817 has been reserved
[    0.878528] system 00:01: ioport range 0x820-0x823 has been reserved
[    0.878531] system 00:01: ioport range 0x400-0x47f has been reserved
[    0.878534] system 00:01: ioport range 0x500-0x53f has been reserved
[    0.878538] system 00:01: iomem range 0xf8000000-0xfbffffff has been reserved
[    0.878541] system 00:01: iomem range 0xfed1c000-0xfed1ffff has been reserved
[    0.878545] system 00:01: iomem range 0xfed10000-0xfed13fff has been reserved
[    0.878548] system 00:01: iomem range 0xfed18000-0xfed18fff has been reserved
[    0.878551] system 00:01: iomem range 0xfed19000-0xfed19fff has been reserved
[    0.878554] system 00:01: iomem range 0xfec00000-0xfec00fff could not be reserved
[    0.878557] system 00:01: iomem range 0xfed20000-0xfed8ffff has been reserved
[    0.878560] system 00:01: iomem range 0xfee00000-0xfee00fff has been reserved
[    0.913217] AppArmor: AppArmor Filesystem Enabled
[    0.913237] pci 0000:03:00.0: BAR 6: no parent found for of device [0xfffe0000-0xffffffff]
[    0.913300] pci 0000:00:1c.0: PCI bridge, secondary bus 0000:01
[    0.913304] pci 0000:00:1c.0:   IO window: 0x5000-0x5fff
[    0.913310] pci 0000:00:1c.0:   MEM window: 0xd9500000-0xda4fffff
[    0.913315] pci 0000:00:1c.0:   PREFETCH window: 0x000000d0400000-0x000000d13fffff
[    0.913323] pci 0000:00:1c.2: PCI bridge, secondary bus 0000:02
[    0.913327] pci 0000:00:1c.2:   IO window: 0x4000-0x4fff
[    0.913333] pci 0000:00:1c.2:   MEM window: 0xd8500000-0xd94fffff
[    0.913338] pci 0000:00:1c.2:   PREFETCH window: 0x000000d1400000-0x000000d23fffff
[    0.913347] pci 0000:00:1c.3: PCI bridge, secondary bus 0000:03
[    0.913351] pci 0000:00:1c.3:   IO window: 0x3000-0x3fff
[    0.913357] pci 0000:00:1c.3:   MEM window: 0xd7500000-0xd84fffff
[    0.913363] pci 0000:00:1c.3:   PREFETCH window: 0x000000d2400000-0x000000d33fffff
[    0.913371] pci 0000:00:1c.4: PCI bridge, secondary bus 0000:04
[    0.913375] pci 0000:00:1c.4:   IO window: 0x2000-0x2fff
[    0.913381] pci 0000:00:1c.4:   MEM window: 0xd6500000-0xd74fffff
[    0.913386] pci 0000:00:1c.4:   PREFETCH window: 0x000000d3400000-0x000000d43fffff
[    0.913395] pci 0000:00:1c.5: PCI bridge, secondary bus 0000:05
[    0.913398] pci 0000:00:1c.5:   IO window: 0x1000-0x1fff
[    0.913405] pci 0000:00:1c.5:   MEM window: 0xd5500000-0xd64fffff
[    0.913410] pci 0000:00:1c.5:   PREFETCH window: 0x000000d4400000-0x000000d53fffff
[    0.913418] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:08
[    0.913420] pci 0000:00:1e.0:   IO window: disabled
[    0.913426] pci 0000:00:1e.0:   MEM window: disabled
[    0.913431] pci 0000:00:1e.0:   PREFETCH window: disabled
[    0.913444]   alloc irq_desc for 16 on node -1
[    0.913446]   alloc kstat_irqs on node -1
[    0.913450] pci 0000:00:1c.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.913455] pci 0000:00:1c.0: setting latency timer to 64
[    0.913464]   alloc irq_desc for 18 on node -1
[    0.913466]   alloc kstat_irqs on node -1
[    0.913470] pci 0000:00:1c.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.913475] pci 0000:00:1c.2: setting latency timer to 64
[    0.913483]   alloc irq_desc for 19 on node -1
[    0.913485]   alloc kstat_irqs on node -1
[    0.913489] pci 0000:00:1c.3: PCI INT D -> GSI 19 (level, low) -> IRQ 19
[    0.913494] pci 0000:00:1c.3: setting latency timer to 64
[    0.913503] pci 0000:00:1c.4: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.913508] pci 0000:00:1c.4: setting latency timer to 64
[    0.913517]   alloc irq_desc for 17 on node -1
[    0.913519]   alloc kstat_irqs on node -1
[    0.913522] pci 0000:00:1c.5: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    0.913528] pci 0000:00:1c.5: setting latency timer to 64
[    0.913536] pci 0000:00:1e.0: setting latency timer to 64
[    0.913541] pci_bus 0000:00: resource 0 io:  [0x00-0xffff]
[    0.913543] pci_bus 0000:00: resource 1 mem: [0x000000-0xffffffff]
[    0.913546] pci_bus 0000:01: resource 0 io:  [0x5000-0x5fff]
[    0.913549] pci_bus 0000:01: resource 1 mem: [0xd9500000-0xda4fffff]
[    0.913551] pci_bus 0000:01: resource 2 pref mem [0xd0400000-0xd13fffff]
[    0.913554] pci_bus 0000:02: resource 0 io:  [0x4000-0x4fff]
[    0.913557] pci_bus 0000:02: resource 1 mem: [0xd8500000-0xd94fffff]
[    0.913559] pci_bus 0000:02: resource 2 pref mem [0xd1400000-0xd23fffff]
[    0.913562] pci_bus 0000:03: resource 0 io:  [0x3000-0x3fff]
[    0.913564] pci_bus 0000:03: resource 1 mem: [0xd7500000-0xd84fffff]
[    0.913567] pci_bus 0000:03: resource 2 pref mem [0xd2400000-0xd33fffff]
[    0.913570] pci_bus 0000:04: resource 0 io:  [0x2000-0x2fff]
[    0.913572] pci_bus 0000:04: resource 1 mem: [0xd6500000-0xd74fffff]
[    0.913575] pci_bus 0000:04: resource 2 pref mem [0xd3400000-0xd43fffff]
[    0.913577] pci_bus 0000:05: resource 0 io:  [0x1000-0x1fff]
[    0.913580] pci_bus 0000:05: resource 1 mem: [0xd5500000-0xd64fffff]
[    0.913582] pci_bus 0000:05: resource 2 pref mem [0xd4400000-0xd53fffff]
[    0.913585] pci_bus 0000:08: resource 3 io:  [0x00-0xffff]
[    0.913587] pci_bus 0000:08: resource 4 mem: [0x000000-0xffffffff]
[    0.913621] NET: Registered protocol family 2
[    0.913717] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.914029] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.914482] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.914697] TCP: Hash tables configured (established 131072 bind 65536)
[    0.914700] TCP reno registered
[    0.914771] NET: Registered protocol family 1
[    0.914829] Trying to unpack rootfs image as initramfs...
[    1.103999] Freeing initrd memory: 7473k freed
[    1.107919] Simple Boot Flag value 0x5 read from CMOS RAM was invalid
[    1.107923] Simple Boot Flag at 0x44 set to 0x1
[    1.108124] cpufreq-nforce2: No nForce2 chipset.
[    1.108152] Scanning for low memory corruption every 60 seconds
[    1.108257] audit: initializing netlink socket (disabled)
[    1.108273] type=2000 audit(1263118171.108:1): initialized
[    1.116866] highmem bounce pool size: 64 pages
[    1.116871] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    1.118342] VFS: Disk quotas dquot_6.5.2
[    1.118407] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    1.118946] fuse init (API version 7.12)
[    1.119028] msgmni has been set to 1682
[    1.119229] alg: No test for stdrng (krng)
[    1.119243] io scheduler noop registered
[    1.119245] io scheduler anticipatory registered
[    1.119247] io scheduler deadline registered
[    1.119288] io scheduler cfq registered (default)
[    1.119300] pci 0000:00:02.0: Boot video device
[    1.152174]   alloc irq_desc for 24 on node -1
[    1.152176]   alloc kstat_irqs on node -1
[    1.152189] pcieport-driver 0000:00:1c.0: irq 24 for MSI/MSI-X
[    1.152201] pcieport-driver 0000:00:1c.0: setting latency timer to 64
[    1.152363]   alloc irq_desc for 25 on node -1
[    1.152365]   alloc kstat_irqs on node -1
[    1.152375] pcieport-driver 0000:00:1c.2: irq 25 for MSI/MSI-X
[    1.152386] pcieport-driver 0000:00:1c.2: setting latency timer to 64
[    1.152546]   alloc irq_desc for 26 on node -1
[    1.152548]   alloc kstat_irqs on node -1
[    1.152557] pcieport-driver 0000:00:1c.3: irq 26 for MSI/MSI-X
[    1.152568] pcieport-driver 0000:00:1c.3: setting latency timer to 64
[    1.152728]   alloc irq_desc for 27 on node -1
[    1.152730]   alloc kstat_irqs on node -1
[    1.152739] pcieport-driver 0000:00:1c.4: irq 27 for MSI/MSI-X
[    1.152750] pcieport-driver 0000:00:1c.4: setting latency timer to 64
[    1.152911]   alloc irq_desc for 28 on node -1
[    1.152913]   alloc kstat_irqs on node -1
[    1.152922] pcieport-driver 0000:00:1c.5: irq 28 for MSI/MSI-X
[    1.152933] pcieport-driver 0000:00:1c.5: setting latency timer to 64
[    1.153044] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    1.153293] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    1.288082] ACPI: AC Adapter [AC] (on-line)
[    1.288166] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input0
[    1.288170] ACPI: Power Button [PWRF]
[    1.288221] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1
[    1.288223] ACPI: Power Button [PWRB]
[    1.288274] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input2
[    1.288344] ACPI: Lid Switch [LID0]
[    1.288389] input: Sleep Button as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input3
[    1.288396] ACPI: Sleep Button [SLPB]
[    1.326051] fan PNP0C0B:00: registered as cooling_device0
[    1.326057] ACPI: Fan [FAN] (on)
[    1.327072] ACPI: SSDT b9e6ec18 00265 (v01  PmRef  Cpu0Ist 00003000 INTL 20051117)
[    1.327756] ACPI: SSDT b9e6c618 005B3 (v01  PmRef  Cpu0Cst 00003001 INTL 20051117)
[    1.328351] Monitor-Mwait will be used to enter C-1 state
[    1.328374] Monitor-Mwait will be used to enter C-2 state
[    1.328394] Monitor-Mwait will be used to enter C-3 state
[    1.328402] Marking TSC unstable due to TSC halts in idle
[    1.328420] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[    1.328439] processor LNXCPU:00: registered as cooling_device1
[    1.328443] ACPI: Processor [CPU0] (supports 8 throttling states)
[    1.328949] ACPI: SSDT b9e6de18 001CF (v01  PmRef    ApIst 00003000 INTL 20051117)
[    1.329518] ACPI: SSDT b9e6ef18 0008D (v01  PmRef    ApCst 00003000 INTL 20051117)
[    1.330237] ACPI: CPU1 (power states: C1[C1] C2[C2] C3[C3])
[    1.330256] processor LNXCPU:01: registered as cooling_device2
[    1.330260] ACPI: Processor [CPU1] (supports 8 throttling states)
[    1.483870] thermal LNXTHERM:01: registered as thermal_zone0
[    1.483878] ACPI: Thermal Zone [THRM] (48 C)
[    1.483949] isapnp: Scanning for PnP cards...
[    1.838241] isapnp: No Plug & Play device found
[    1.839416] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    1.840750] brd: module loaded
[    1.841208] loop: module loaded
[    1.841274] input: Macintosh mouse button emulation as /devices/virtual/input/input4
[    1.841348] ahci 0000:00:1f.2: version 3.0
[    1.841361]   alloc irq_desc for 21 on node -1
[    1.841363]   alloc kstat_irqs on node -1
[    1.841369] ahci 0000:00:1f.2: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[    1.841401]   alloc irq_desc for 29 on node -1
[    1.841403]   alloc kstat_irqs on node -1
[    1.841413] ahci 0000:00:1f.2: irq 29 for MSI/MSI-X
[    1.841465] ahci: SSS flag set, parallel bus scan disabled
[    1.841503] ahci 0000:00:1f.2: AHCI 0001.0200 32 slots 4 ports 3 Gbps 0x33 impl SATA mode
[    1.841507] ahci 0000:00:1f.2: flags: 64bit ncq sntf stag pm led clo pmp pio slum part ems 
[    1.841513] ahci 0000:00:1f.2: setting latency timer to 64
[    1.864075] scsi0 : ahci
[    1.864164] scsi1 : ahci
[    1.864220] scsi2 : ahci
[    1.864275] scsi3 : ahci
[    1.864331] scsi4 : ahci
[    1.864389] scsi5 : ahci
[    1.864652] ata1: SATA max UDMA/133 abar m2048@0xda504000 port 0xda504100 irq 29
[    1.864656] ata2: SATA max UDMA/133 abar m2048@0xda504000 port 0xda504180 irq 29
[    1.864659] ata3: DUMMY
[    1.864660] ata4: DUMMY
[    1.864663] ata5: SATA max UDMA/133 abar m2048@0xda504000 port 0xda504300 irq 29
[    1.864667] ata6: SATA max UDMA/133 abar m2048@0xda504000 port 0xda504380 irq 29
[    1.865620] Fixed MDIO Bus: probed
[    1.865653] PPP generic driver version 2.4.2
[    1.865739] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    1.865758] ehci_hcd 0000:00:1a.7: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    1.865769] ehci_hcd 0000:00:1a.7: setting latency timer to 64
[    1.865773] ehci_hcd 0000:00:1a.7: EHCI Host Controller
[    1.865818] ehci_hcd 0000:00:1a.7: new USB bus registered, assigned bus number 1
[    1.869717] ehci_hcd 0000:00:1a.7: debug port 1
[    1.869724] ehci_hcd 0000:00:1a.7: cache line size of 32 is not supported
[    1.869738] ehci_hcd 0000:00:1a.7: irq 18, io mem 0xda504c00
[    1.884513] ehci_hcd 0000:00:1a.7: USB 2.0 started, EHCI 1.00
[    1.884587] usb usb1: configuration #1 chosen from 1 choice
[    1.884616] hub 1-0:1.0: USB hub found
[    1.884623] hub 1-0:1.0: 4 ports detected
[    1.884682]   alloc irq_desc for 20 on node -1
[    1.884684]   alloc kstat_irqs on node -1
[    1.884689] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    1.884699] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    1.884703] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    1.884733] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 2
[    1.888638] ehci_hcd 0000:00:1d.7: debug port 1
[    1.888645] ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported
[    1.888658] ehci_hcd 0000:00:1d.7: irq 20, io mem 0xda504800
[    1.904019] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    1.904079] usb usb2: configuration #1 chosen from 1 choice
[    1.904106] hub 2-0:1.0: USB hub found
[    1.904112] hub 2-0:1.0: 6 ports detected
[    1.904175] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    1.904193] uhci_hcd: USB Universal Host Controller Interface driver
[    1.904214] uhci_hcd 0000:00:1a.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.904221] uhci_hcd 0000:00:1a.0: setting latency timer to 64
[    1.904224] uhci_hcd 0000:00:1a.0: UHCI Host Controller
[    1.904259] uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 3
[    1.904295] uhci_hcd 0000:00:1a.0: irq 16, io base 0x000060c0
[    1.904378] usb usb3: configuration #1 chosen from 1 choice
[    1.904404] hub 3-0:1.0: USB hub found
[    1.904410] hub 3-0:1.0: 2 ports detected
[    1.904458] uhci_hcd 0000:00:1a.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    1.904465] uhci_hcd 0000:00:1a.1: setting latency timer to 64
[    1.904469] uhci_hcd 0000:00:1a.1: UHCI Host Controller
[    1.904499] uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus number 4
[    1.904545] uhci_hcd 0000:00:1a.1: irq 17, io base 0x000060a0
[    1.904623] usb usb4: configuration #1 chosen from 1 choice
[    1.904649] hub 4-0:1.0: USB hub found
[    1.904655] hub 4-0:1.0: 2 ports detected
[    1.904706] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    1.904713] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    1.904716] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    1.904745] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 5
[    1.904771] uhci_hcd 0000:00:1d.0: irq 20, io base 0x00006080
[    1.904845] usb usb5: configuration #1 chosen from 1 choice
[    1.904871] hub 5-0:1.0: USB hub found
[    1.904877] hub 5-0:1.0: 2 ports detected
[    1.904924]   alloc irq_desc for 22 on node -1
[    1.904926]   alloc kstat_irqs on node -1
[    1.904931] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 22 (level, low) -> IRQ 22
[    1.904937] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    1.904941] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    1.904971] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 6
[    1.905006] uhci_hcd 0000:00:1d.1: irq 22, io base 0x00006060
[    1.905083] usb usb6: configuration #1 chosen from 1 choice
[    1.905109] hub 6-0:1.0: USB hub found
[    1.905115] hub 6-0:1.0: 2 ports detected
[    1.905165] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    1.905171] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    1.905175] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    1.905208] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 7
[    1.905235] uhci_hcd 0000:00:1d.2: irq 18, io base 0x00006040
[    1.905309] usb usb7: configuration #1 chosen from 1 choice
[    1.905337] hub 7-0:1.0: USB hub found
[    1.905343] hub 7-0:1.0: 2 ports detected
[    1.905440] PNP: PS/2 Controller [PNP0303:KBC,PNP0f13:MOUE] at 0x60,0x64 irq 1,12
[    1.955986] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.955992] serio: i8042 AUX port at 0x60,0x64 irq 12
[    1.956058] mice: PS/2 mouse device common for all mice
[    1.956188] rtc_cmos 00:03: RTC can wake from S4
[    1.956219] rtc_cmos 00:03: rtc core: registered rtc_cmos as rtc0
[    1.956252] rtc0: alarms up to one month, 242 bytes nvram, hpet irqs
[    1.956350] device-mapper: uevent: version 1.0.3
[    1.956434] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: dm-devel@redhat.com
[    1.956492] device-mapper: multipath: version 1.1.0 loaded
[    1.956495] device-mapper: multipath round-robin: version 1.0.0 loaded
[    1.956609] EISA: Probing bus 0 at eisa.0
[    1.956615] Cannot allocate resource for EISA slot 1
[    1.956617] Cannot allocate resource for EISA slot 2
[    1.956619] Cannot allocate resource for EISA slot 3
[    1.956621] Cannot allocate resource for EISA slot 4
[    1.956623] Cannot allocate resource for EISA slot 5
[    1.956625] Cannot allocate resource for EISA slot 6
[    1.956636] EISA: Detected 0 cards.
[    1.956774] cpuidle: using governor ladder
[    1.958948] cpuidle: using governor menu
[    1.959434] TCP cubic registered
[    1.959597] NET: Registered protocol family 10
[    1.960055] lo: Disabled Privacy Extensions
[    1.960392] NET: Registered protocol family 17
[    1.960408] Bluetooth: L2CAP ver 2.13
[    1.960410] Bluetooth: L2CAP socket layer initialized
[    1.960412] Bluetooth: SCO (Voice Link) ver 0.6
[    1.960414] Bluetooth: SCO socket layer initialized
[    1.960450] Bluetooth: RFCOMM TTY layer initialized
[    1.960454] Bluetooth: RFCOMM socket layer initialized
[    1.960455] Bluetooth: RFCOMM ver 1.11
[    1.960959] Using IPI No-Shortcut mode
[    1.961019] PM: Resume from disk failed.
[    1.961031] registered taskstats version 1
[    1.961160]   Magic number: 10:394:173
[    1.961186] pci_express 0000:00:1c.0:pcie01: hash matches
[    1.961198] acpi device:36: hash matches
[    1.961258] rtc_cmos 00:03: setting system clock to 2010-01-10 10:09:33 UTC (1263118173)
[    1.961262] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.961264] EDD information not available.
[    1.993400] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input5
[    2.017265] ACPI: Battery Slot [BAT0] (battery present)
[    2.272051] usb 2-5: new high speed USB device using ehci_hcd and address 3
[    2.356055] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    2.358215] ata1.00: ACPI cmd 00/00:00:00:00:00:a0 rejected by device (Stat=0x51 Err=0x04)
[    2.358360] ata1.00: ACPI cmd ef/10:01:00:00:00:a0 rejected by device (Stat=0x51 Err=0x04)
[    2.358459] ata1.00: ACPI cmd ef/10:02:00:00:00:a0 succeeded
[    2.358465] ata1.00: ACPI cmd ef/10:03:00:00:00:a0 filtered out
[    2.358595] ata1.00: ACPI cmd ef/10:04:00:00:00:a0 rejected by device (Stat=0x51 Err=0x04)
[    2.358722] ata1.00: ACPI cmd ef/10:05:00:00:00:a0 rejected by device (Stat=0x51 Err=0x04)
[    2.360269] ata1.00: ATA-8: WDC WD2500BEVT-60ZCT1, 13.01A13, max UDMA/100
[    2.360275] ata1.00: 488397168 sectors, multi 0: LBA48 NCQ (depth 31/32)
[    2.362569] ata1.00: ACPI cmd 00/00:00:00:00:00:a0 rejected by device (Stat=0x51 Err=0x04)
[    2.362768] ata1.00: ACPI cmd ef/10:01:00:00:00:a0 rejected by device (Stat=0x51 Err=0x04)
[    2.362774] ata1.00: ACPI cmd ef/10:03:00:00:00:a0 filtered out
[    2.362911] ata1.00: ACPI cmd ef/10:04:00:00:00:a0 rejected by device (Stat=0x51 Err=0x04)
[    2.363063] ata1.00: ACPI cmd ef/10:05:00:00:00:a0 rejected by device (Stat=0x51 Err=0x04)
[    2.363108] ata1.00: configured for UDMA/100
[    2.376221] scsi 0:0:0:0: Direct-Access     ATA      WDC WD2500BEVT-6 13.0 PQ: 0 ANSI: 5
[    2.376339] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    2.376355] sd 0:0:0:0: [sda] 488397168 512-byte logical blocks: (250 GB/232 GiB)
[    2.376402] sd 0:0:0:0: [sda] Write Protect is off
[    2.376404] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    2.376428] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.376563]  sda:
[    2.410552] usb 2-5: configuration #1 chosen from 1 choice
[    2.418688]  sda1 sda2 sda3 < sda5 sda6 >
[    2.453209] sd 0:0:0:0: [sda] Attached SCSI disk
[    2.500050] Clocksource tsc unstable (delta = -323787461 ns)
[    2.648047] usb 5-1: new low speed USB device using uhci_hcd and address 2
[    2.816905] usb 5-1: configuration #1 chosen from 1 choice
[    3.264136] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    3.266970] ata2.00: ACPI cmd 00/00:00:00:00:00:b0 rejected by device (Stat=0x51 Err=0x04)
[    3.267417] ata2.00: ACPI cmd ef/10:01:00:00:00:b0 rejected by device (Stat=0x51 Err=0x04)
[    3.267885] ata2.00: ACPI cmd ef/10:02:00:00:00:b0 rejected by device (Stat=0x51 Err=0x04)
[    3.267890] ata2.00: ACPI cmd ef/10:03:00:00:00:b0 filtered out
[    3.268333] ata2.00: ACPI cmd ef/10:04:00:00:00:b0 rejected by device (Stat=0x51 Err=0x04)
[    3.268805] ata2.00: ACPI cmd ef/10:05:00:00:00:b0 rejected by device (Stat=0x51 Err=0x04)
[    3.268812] ata2.00: ATAPI: PIONEER DVDRW  DR-TD08HB, 1T10, max UDMA/100
[    3.272092] ata2.00: ACPI cmd 00/00:00:00:00:00:b0 rejected by device (Stat=0x51 Err=0x04)
[    3.272627] ata2.00: ACPI cmd ef/10:01:00:00:00:b0 rejected by device (Stat=0x51 Err=0x04)
[    3.273071] ata2.00: ACPI cmd ef/10:02:00:00:00:b0 rejected by device (Stat=0x51 Err=0x04)
[    3.273077] ata2.00: ACPI cmd ef/10:03:00:00:00:b0 filtered out
[    3.273607] ata2.00: ACPI cmd ef/10:04:00:00:00:b0 rejected by device (Stat=0x51 Err=0x04)
[    3.274053] ata2.00: ACPI cmd ef/10:05:00:00:00:b0 rejected by device (Stat=0x51 Err=0x04)
[    3.274097] ata2.00: configured for UDMA/100
[    3.368069] scsi 1:0:0:0: CD-ROM            PIONEER  DVDRW  DR-TD08HB 1T10 PQ: 0 ANSI: 5
[    3.725411] sr0: scsi3-mmc drive: 8x/8x writer dvd-ram cd/rw xa/form2 cdda tray
[    3.725415] Uniform CD-ROM driver Revision: 3.20
[    3.725543] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    3.725598] sr 1:0:0:0: Attached scsi generic sg1 type 5
[    4.044110] ata5: SATA link down (SStatus 0 SControl 300)
[    4.380112] ata6: SATA link down (SStatus 0 SControl 300)
[    4.396171] Freeing unused kernel memory: 540k freed
[    4.396526] Write protecting the kernel text: 4568k
[    4.396582] Write protecting the kernel read-only data: 1836k
[    4.702535] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    4.702558] r8169 0000:03:00.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    4.702607] r8169 0000:03:00.0: setting latency timer to 64
[    4.702668]   alloc irq_desc for 30 on node -1
[    4.702670]   alloc kstat_irqs on node -1
[    4.702687] r8169 0000:03:00.0: irq 30 for MSI/MSI-X
[    4.703333] eth0: RTL8102e at 0xf80cc000, 00:1e:ec:f8:7c:a0, XID 24a00000 IRQ 30
[    4.711666] Linux agpgart interface v0.103
[    4.714544] agpgart-intel 0000:00:00.0: Intel Mobile Intel® GM45 Express Chipset
[    4.715302] agpgart-intel 0000:00:00.0: detected 65532K stolen memory
[    4.741651] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0xc0000000
[    4.785043] [drm] Initialized drm 1.1.0 20060810
[    4.796171] i915 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    4.796177] i915 0000:00:02.0: setting latency timer to 64
[    4.798395]   alloc irq_desc for 31 on node -1
[    4.798398]   alloc kstat_irqs on node -1
[    4.798408] i915 0000:00:02.0: irq 31 for MSI/MSI-X
[    4.900467] usbcore: registered new interface driver hiddev
[    4.905429] [drm] i2c_init DPDDC-B
[    4.915095] [drm] i2c_init DPDDC-D
[    4.917087] input: USB Optical Mouse as /devices/pci0000:00/0000:00:1d.0/usb5/5-1/5-1:1.0/input/input6
[    4.917194] generic-usb 0003:1BCF:0007.0001: input,hiddev96,hidraw0: USB HID v1.10 Mouse [USB Optical Mouse] on usb-0000:00:1d.0-1/input0
[    4.917209] usbcore: registered new interface driver usbhid
[    4.917212] usbhid: v2.6:USB HID core driver
[    5.035316] i2c-adapter i2c-2: unable to read EDID block.
[    5.035320] i915 0000:00:02.0: HDMI Type A-1: no EDID data
[    5.043600] [drm] fb0: inteldrmfb frame buffer device
[    5.044799] [Firmware Bug]: ACPI: ACPI brightness control misses _BQC function
[    5.055349] acpi device:04: registered as cooling_device3
[    5.055617] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:01/input/input7
[    5.055649] ACPI: Video Device [OVGA] (multi-head: yes  rom: no  post: no)
[    5.055703] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
[    5.471321] [drm] LVDS-8: set mode 1280x800 14
[    6.080082] Console: switching to colour frame buffer device 160x50
[    6.368775] PM: Starting manual resume from disk
[    6.368778] PM: Resume from partition 8:6
[    6.368781] PM: Checking hibernation image.
[    6.368998] PM: Resume from disk failed.
[    6.394613] EXT4-fs (sda5): barriers enabled
[    6.416942] kjournald2 starting: pid 462, dev sda5:8, commit interval 5 seconds
[    6.416983] EXT4-fs (sda5): delayed allocation enabled
[    6.416993] EXT4-fs: file extents enabled
[    6.423389] EXT4-fs: mballoc enabled
[    6.423402] EXT4-fs (sda5): mounted filesystem with ordered data mode
[    7.093452] type=1505 audit(1263118178.631:2): operation="profile_load" pid=485 name=/usr/share/gdm/guest-session/Xsession
[    7.096402] type=1505 audit(1263118178.634:3): operation="profile_load" pid=486 name=/sbin/dhclient3
[    7.097217] type=1505 audit(1263118178.634:4): operation="profile_load" pid=486 name=/usr/lib/NetworkManager/nm-dhcp-client.action
[    7.097617] type=1505 audit(1263118178.634:5): operation="profile_load" pid=486 name=/usr/lib/connman/scripts/dhclient-script
[    7.156106] type=1505 audit(1263118178.694:6): operation="profile_load" pid=487 name=/usr/bin/evince
[    7.167928] type=1505 audit(1263118178.702:7): operation="profile_load" pid=487 name=/usr/bin/evince-previewer
[    7.174874] type=1505 audit(1263118178.710:8): operation="profile_load" pid=487 name=/usr/bin/evince-thumbnailer
[    7.196471] type=1505 audit(1263118178.734:9): operation="profile_load" pid=489 name=/usr/lib/cups/backend/cups-pdf
[    7.197339] type=1505 audit(1263118178.734:10): operation="profile_load" pid=489 name=/usr/sbin/cupsd
[    7.200142] type=1505 audit(1263118178.738:11): operation="profile_load" pid=490 name=/usr/sbin/tcpdump
[   17.372999] udev: starting version 147
[   17.401877] Adding 3461968k swap on /dev/sda6.  Priority:-1 extents:1 across:3461968k 
[   17.595276] lirc_dev: IR Remote Control driver registered, major 61 
[   17.597834] lirc_dev: lirc_register_driver: sample_rate: 0
[   17.597945] enecir: KB3926C detected, driver support is not complete!
[   17.597948] enecir: chip is 0x3926 - 0x00, 0xc0
[   17.597956] enecir: hardware features:
[   17.597958] enecir: learning and tx off, gpio40_learn off, fan_in off
[   17.597960] enecir: driver has been succesfully loaded
[   17.699682] EXT4-fs (sda5): internal journal on sda5:8
[   17.704340] sdhci: Secure Digital Host Controller Interface driver
[   17.704342] sdhci: Copyright(c) Pierre Ossman
[   17.706025] sdhci-pci 0000:04:00.0: SDHCI controller found [197b:2382] (rev 0)
[   17.706049] sdhci-pci 0000:04:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   17.706090] sdhci-pci 0000:04:00.0: setting latency timer to 64
[   17.706127] Registered led device: mmc0::
[   17.706163] mmc0: SDHCI controller on PCI [0000:04:00.0] using ADMA
[   17.706175] sdhci-pci 0000:04:00.2: SDHCI controller found [197b:2381] (rev 0)
[   17.706192] sdhci-pci 0000:04:00.2: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   17.706199] sdhci-pci 0000:04:00.2: Refusing to bind to secondary interface.
[   17.706207] sdhci-pci 0000:04:00.2: PCI INT A disabled
[   17.723678] jmb38x_ms 0000:04:00.3: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   17.723688] jmb38x_ms 0000:04:00.3: setting latency timer to 64
[   17.753258] lis3lv02d: laptop model unknown, using default axes configuration
[   17.753984] lis3lv02d: 1-byte sensor found
[   17.763339] input: ST LIS3LV02DL Accelerometer as /devices/platform/lis3lv02d/input/input8
[   17.763447] Registered led device: hp::hddprotect
[   17.763464] lis3lv02d driver loaded.
[   17.765678] lp: driver loaded but no devices found
[   17.766796] lib80211: common routines for IEEE802.11 drivers
[   17.766799] lib80211_crypt: registered algorithm 'NULL'
[   17.815470] Linux video capture interface: v2.00
[   17.822395] ip_tables: (C) 2000-2006 Netfilter Core Team
[   17.843514] uvcvideo: Found UVC 1.00 device HP Webcam (090c:c371)
[   17.845935] input: HP Webcam as /devices/pci0000:00/0000:00:1d.7/usb2/2-5/2-5:1.0/input/input9
[   17.845980] usbcore: registered new interface driver uvcvideo
[   17.845983] USB Video Class driver (v0.1.0)
[   17.911782] wl: module license 'MIXED/Proprietary' taints kernel.
[   17.911786] Disabling lock debugging due to kernel taint
[   17.913871] wl 0000:02:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[   17.913885] wl 0000:02:00.0: setting latency timer to 64
[   17.937803] lib80211_crypt: registered algorithm 'TKIP'
[   17.937956] eth1: Broadcom BCM4315 802.11 Wireless Controller 5.10.91.9
[   17.945565] udev: renamed network interface eth1 to eth2
[   18.211583] HDA Intel 0000:00:1b.0: power state changed by ACPI to D0
[   18.211595] HDA Intel 0000:00:1b.0: PCI INT B -> GSI 22 (level, low) -> IRQ 22
[   18.211601] hda_intel: msi for device 103c:30f7 set to 1
[   18.211670]   alloc irq_desc for 32 on node -1
[   18.211673]   alloc kstat_irqs on node -1
[   18.211687] HDA Intel 0000:00:1b.0: irq 32 for MSI/MSI-X
[   18.211725] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   18.267838] type=1505 audit(1263136189.802:12): operation="profile_replace" pid=992 name=/usr/share/gdm/guest-session/Xsession
[   18.269907] type=1505 audit(1263136189.806:13): operation="profile_replace" pid=993 name=/sbin/dhclient3
[   18.270646] type=1505 audit(1263136189.806:14): operation="profile_replace" pid=993 name=/usr/lib/NetworkManager/nm-dhcp-client.action
[   18.271049] type=1505 audit(1263136189.806:15): operation="profile_replace" pid=993 name=/usr/lib/connman/scripts/dhclient-script
[   18.274805] type=1505 audit(1263136189.810:16): operation="profile_replace" pid=994 name=/usr/bin/evince
[   18.287549] type=1505 audit(1263136189.822:17): operation="profile_replace" pid=994 name=/usr/bin/evince-previewer
[   18.296999] type=1505 audit(1263136189.834:18): operation="profile_replace" pid=994 name=/usr/bin/evince-thumbnailer
[   18.308037] type=1505 audit(1263136189.842:19): operation="profile_replace" pid=1000 name=/usr/lib/cups/backend/cups-pdf
[   18.308912] type=1505 audit(1263136189.842:20): operation="profile_replace" pid=1000 name=/usr/sbin/cupsd
[   18.311359] type=1505 audit(1263136189.849:21): operation="profile_replace" pid=1001 name=/usr/sbin/tcpdump
[   18.365444] input: HDA Digital PCBeep as /devices/pci0000:00/0000:00:1b.0/input/input10
[   18.616076] r8169: eth0: link down
[   18.616270] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   18.702062] input: HDA Intel Mic at Ext Front Jack as /devices/pci0000:00/0000:00:1b.0/sound/card0/input11
[   18.702140] input: HDA Intel Mic at Sep UNKNOWN Jack as /devices/pci0000:00/0000:00:1b.0/sound/card0/input12
[   18.702202] input: HDA Intel HP Out at Ext Front Jack as /devices/pci0000:00/0000:00:1b.0/sound/card0/input13
[   18.780278] input: PS/2 Mouse as /devices/platform/i8042/serio1/input/input14
[   18.826555] input: AlpsPS/2 ALPS GlidePoint as /devices/platform/i8042/serio1/input/input15
[   19.101689] i2c-adapter i2c-2: unable to read EDID block.
[   19.101694] i915 0000:00:02.0: HDMI Type A-1: no EDID data
[   19.107064] i2c-adapter i2c-2: unable to read EDID block.
[   19.107068] i915 0000:00:02.0: HDMI Type A-1: no EDID data
[   19.253631] i2c-adapter i2c-2: unable to read EDID block.
[   19.253636] i915 0000:00:02.0: HDMI Type A-1: no EDID data
[   19.258051] i2c-adapter i2c-2: unable to read EDID block.
[   19.258054] i915 0000:00:02.0: HDMI Type A-1: no EDID data
[   19.372399] ppdev: user-space parallel port driver
[   20.778180] CPU0 attaching NULL sched-domain.
[   20.778185] CPU1 attaching NULL sched-domain.
[   20.788623] CPU0 attaching sched-domain:
[   20.788629]  domain 0: span 0-1 level MC
[   20.788634]   groups: 0 1
[   20.788642] CPU1 attaching sched-domain:
[   20.788646]  domain 0: span 0-1 level MC
[   20.788650]   groups: 1 0
[   22.646516] CPU0 attaching NULL sched-domain.
[   22.646521] CPU1 attaching NULL sched-domain.
[   22.660126] CPU0 attaching sched-domain:
[   22.660133]  domain 0: span 0-1 level MC
[   22.660137]   groups: 0 1
[   22.660147] CPU1 attaching sched-domain:
[   22.660150]  domain 0: span 0-1 level MC
[   22.660154]   groups: 1 0
[   23.014722] i2c-adapter i2c-2: unable to read EDID block.
[   23.014726] i915 0000:00:02.0: HDMI Type A-1: no EDID data
[   23.019415] i2c-adapter i2c-2: unable to read EDID block.
[   23.019418] i915 0000:00:02.0: HDMI Type A-1: no EDID data
[   23.159151] i2c-adapter i2c-2: unable to read EDID block.
[   23.159155] i915 0000:00:02.0: HDMI Type A-1: no EDID data
[   23.163811] i2c-adapter i2c-2: unable to read EDID block.
[   23.163815] i915 0000:00:02.0: HDMI Type A-1: no EDID data
[   23.301213] i2c-adapter i2c-2: unable to read EDID block.
[   23.301218] i915 0000:00:02.0: HDMI Type A-1: no EDID data
[   23.306037] i2c-adapter i2c-2: unable to read EDID block.
[   23.306041] i915 0000:00:02.0: HDMI Type A-1: no EDID data
[   24.099236] i2c-adapter i2c-2: unable to read EDID block.
[   24.099241] i915 0000:00:02.0: HDMI Type A-1: no EDID data
[   24.103768] i2c-adapter i2c-2: unable to read EDID block.
[   24.103771] i915 0000:00:02.0: HDMI Type A-1: no EDID data
[   28.648039] eth2: no IPv6 routers present
[  282.539446] CPU0 attaching NULL sched-domain.
[  282.539458] CPU1 attaching NULL sched-domain.
[  282.552186] CPU0 attaching sched-domain:
[  282.552195]  domain 0: span 0-1 level MC
[  282.552202]   groups: 0 1
[  282.552216] CPU1 attaching sched-domain:
[  282.552222]  domain 0: span 0-1 level MC
[  282.552228]   groups: 1 0
[  283.732505] PM: Syncing filesystems ... done.
[  283.735273] PM: Preparing system for mem sleep
[  283.735277] Freezing user space processes ... (elapsed 0.00 seconds) done.
[  283.736059] Freezing remaining freezable tasks ... (elapsed 0.00 seconds) done.
[  283.736098] PM: Entering mem sleep
[  283.736112] Suspending console(s) (use no_console_suspend to debug)
[  283.776103] sd 0:0:0:0: [sda] Synchronizing SCSI cache
[  283.907041] sd 0:0:0:0: [sda] Stopping disk
[  284.772710] ACPI handle has no context!
[  284.772827] jmb38x_ms 0000:04:00.3: PME# disabled
[  284.772835] jmb38x_ms 0000:04:00.3: PCI INT A disabled
[  284.788227] sdhci-pci 0000:04:00.0: PME# disabled
[  284.788236] sdhci-pci 0000:04:00.0: PCI INT A disabled
[  284.804383] wl 0000:02:00.0: PCI INT A disabled
[  284.900110] ehci_hcd 0000:00:1d.7: PCI INT A disabled
[  284.900121] uhci_hcd 0000:00:1d.2: PCI INT C disabled
[  284.900132] uhci_hcd 0000:00:1d.1: PCI INT B disabled
[  284.900141] uhci_hcd 0000:00:1d.0: PCI INT A disabled
[  285.005006] HDA Intel 0000:00:1b.0: PCI INT B disabled
[  285.040244] HDA Intel 0000:00:1b.0: power state changed by ACPI to D3
[  285.040258] ehci_hcd 0000:00:1a.7: PCI INT C disabled
[  285.040269] uhci_hcd 0000:00:1a.1: PCI INT B disabled
[  285.040279] uhci_hcd 0000:00:1a.0: PCI INT A disabled
[  285.082985] render error detected, EIR: 0x00000010
[  285.082988]   IPEIR: 0x00000000
[  285.082989]   IPEHR: 0x01000000
[  285.082991]   INSTDONE: 0xfffffffe
[  285.082993]   INSTPS: 0x0001e000
[  285.082994]   INSTDONE1: 0xffffffff
[  285.082996]   ACTHD: 0x0521e0f8
[  285.082998] page table error
[  285.082999]   PGTBL_ER: 0x00100000
[  285.083002] [drm:i915_handle_error] *ERROR* EIR stuck: 0x00000010, masking
[  285.104839] PM: suspend devices took 1.372 seconds
[  285.105134] r8169 0000:03:00.0: PME# enabled
[  285.123716] r8169 0000:03:00.0: wake-up capability enabled by ACPI
[  285.136187] ehci_hcd 0000:00:1d.7: PME# disabled
[  285.152449] ehci_hcd 0000:00:1a.7: PME# disabled
[  285.168400] ACPI: Preparing to enter system sleep state S3
[  285.168691] Disabling non-boot CPUs ...
[  285.272021] CPU 1 is now offline
[  285.272024] SMP alternatives: switching to UP code
[  285.277787] CPU0 attaching NULL sched-domain.
[  285.277790] CPU1 attaching NULL sched-domain.
[  285.277795] CPU0 attaching NULL sched-domain.
[  285.277961] CPU1 is down
[  285.277968] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[  285.277968] Back to C!
[  285.277968] CPU0: Thermal LVT vector (0xfa) already installed
[  285.277968] Enabling non-boot CPUs ...
[  285.277968] SMP alternatives: switching to SMP code
[  285.283620] Booting processor 1 APIC 0x1 ip 0x6000
[  285.277660] Initializing CPU#1
[  285.277660] Calibrating delay using timer specific routine.. 3993.84 BogoMIPS (lpj=7987691)
[  285.277660] CPU: L1 I cache: 32K, L1 D cache: 32K
[  285.277660] CPU: L2 cache: 2048K
[  285.277660] CPU: Physical Processor ID: 0
[  285.277660] CPU: Processor Core ID: 1
[  285.277660] mce: CPU supports 6 MCE banks
[  285.277660] CPU1: Thermal monitoring enabled (TM1)
[  285.277660] x86 PAT enabled: cpu 1, old 0x7040600070406, new 0x7010600070106
[  285.379041] CPU1: Intel(R) Core(TM)2 Duo CPU     T5800  @ 2.00GHz stepping 0d
[  285.379111] CPU0 attaching NULL sched-domain.
[  285.380022] Switched to high resolution mode on CPU 1
[  285.392018] CPU0 attaching sched-domain:
[  285.392021]  domain 0: span 0-1 level MC
[  285.392023]   groups: 0 1
[  285.392027] CPU1 attaching sched-domain:
[  285.392029]  domain 0: span 0-1 level MC
[  285.392031]   groups: 1 0
[  285.392518] CPU1 is up
[  285.392520] ACPI: Waking up from system sleep state S3
[  285.441433] i915 0000:00:02.0: restoring config space at offset 0x6 (was 0xc, writing 0xc000000c)
[  285.441440] i915 0000:00:02.0: restoring config space at offset 0x1 (was 0x900007, writing 0x900407)
[  285.441503] uhci_hcd 0000:00:1a.0: restoring config space at offset 0x1 (was 0x2900005, writing 0x2900001)
[  285.441546] uhci_hcd 0000:00:1a.1: restoring config space at offset 0x1 (was 0x2900005, writing 0x2900001)
[  285.441597] ehci_hcd 0000:00:1a.7: restoring config space at offset 0x1 (was 0x2900006, writing 0x2900002)
[  285.441619] ehci_hcd 0000:00:1a.7: PME# disabled
[  285.441658] HDA Intel 0000:00:1b.0: restoring config space at offset 0x3 (was 0x0, writing 0x10)
[  285.441665] HDA Intel 0000:00:1b.0: restoring config space at offset 0x1 (was 0x100006, writing 0x100002)
[  285.441711] pcieport-driver 0000:00:1c.0: restoring config space at offset 0x7 (was 0x20005050, writing 0x5050)
[  285.441725] pcieport-driver 0000:00:1c.0: restoring config space at offset 0x1 (was 0x100007, writing 0x100407)
[  285.441797] pcieport-driver 0000:00:1c.2: restoring config space at offset 0x1 (was 0x100007, writing 0x100407)
[  285.441869] pcieport-driver 0000:00:1c.3: restoring config space at offset 0x1 (was 0x100007, writing 0x100407)
[  285.441941] pcieport-driver 0000:00:1c.4: restoring config space at offset 0x1 (was 0x100007, writing 0x100407)
[  285.442004] pcieport-driver 0000:00:1c.5: restoring config space at offset 0x7 (was 0x20001010, writing 0x1010)
[  285.442017] pcieport-driver 0000:00:1c.5: restoring config space at offset 0x1 (was 0x100007, writing 0x100407)
[  285.442082] uhci_hcd 0000:00:1d.0: restoring config space at offset 0x1 (was 0x2900005, writing 0x2900001)
[  285.442124] uhci_hcd 0000:00:1d.1: restoring config space at offset 0x1 (was 0x2900005, writing 0x2900001)
[  285.442166] uhci_hcd 0000:00:1d.2: restoring config space at offset 0x1 (was 0x2900005, writing 0x2900001)
[  285.442217] ehci_hcd 0000:00:1d.7: restoring config space at offset 0x1 (was 0x2900006, writing 0x2900002)
[  285.442238] ehci_hcd 0000:00:1d.7: PME# disabled
[  285.442257] pci 0000:00:1e.0: restoring config space at offset 0xa (was 0x0, writing 0xffffffff)
[  285.442262] pci 0000:00:1e.0: restoring config space at offset 0x9 (was 0x10001, writing 0x1fff1)
[  285.442268] pci 0000:00:1e.0: restoring config space at offset 0x8 (was 0x0, writing 0xfff0)
[  285.442273] pci 0000:00:1e.0: restoring config space at offset 0x7 (was 0x22800000, writing 0x228000f0)
[  285.442286] pci 0000:00:1e.0: restoring config space at offset 0x1 (was 0x100000, writing 0x100007)
[  285.442387] ahci 0000:00:1f.2: restoring config space at offset 0x1 (was 0x2b00007, writing 0x2b00407)
[  285.442744] r8169 0000:03:00.0: restoring config space at offset 0x3 (was 0x0, writing 0x8)
[  285.442753] r8169 0000:03:00.0: restoring config space at offset 0x1 (was 0x100007, writing 0x100407)
[  285.442833] sdhci-pci 0000:04:00.0: restoring config space at offset 0xf (was 0x1ff, writing 0x10b)
[  285.442872] sdhci-pci 0000:04:00.0: restoring config space at offset 0x1 (was 0x100000, writing 0x100007)
[  285.442924] pci 0000:04:00.2: restoring config space at offset 0xf (was 0x1ff, writing 0x10b)
[  285.442962] pci 0000:04:00.2: restoring config space at offset 0x1 (was 0x100000, writing 0x100003)
[  285.443014] jmb38x_ms 0000:04:00.3: restoring config space at offset 0xf (was 0x1ff, writing 0x10b)
[  285.443052] jmb38x_ms 0000:04:00.3: restoring config space at offset 0x1 (was 0x100000, writing 0x100007)
[  285.443103] pci 0000:04:00.4: restoring config space at offset 0xf (was 0x1ff, writing 0x10b)
[  285.443142] pci 0000:04:00.4: restoring config space at offset 0x1 (was 0x100000, writing 0x100007)
[  285.498398] i915 0000:00:02.0: setting latency timer to 64
[  285.559112] [drm] LVDS-8: set mode 1280x800 14
[  285.579256] pci 0000:00:02.1: PME# disabled
[  285.579267] uhci_hcd 0000:00:1a.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[  285.579274] uhci_hcd 0000:00:1a.0: setting latency timer to 64
[  285.579300] usb usb3: root hub lost power or was reset
[  285.579321] uhci_hcd 0000:00:1a.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[  285.579328] uhci_hcd 0000:00:1a.1: setting latency timer to 64
[  285.579355] usb usb4: root hub lost power or was reset
[  285.579375] ehci_hcd 0000:00:1a.7: PME# disabled
[  285.579380] ehci_hcd 0000:00:1a.7: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[  285.579386] ehci_hcd 0000:00:1a.7: setting latency timer to 64
[  285.579397] HDA Intel 0000:00:1b.0: PCI INT B -> GSI 22 (level, low) -> IRQ 22
[  285.579404] HDA Intel 0000:00:1b.0: setting latency timer to 64
[  285.579449] HDA Intel 0000:00:1b.0: irq 32 for MSI/MSI-X
[  285.579494] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[  285.579501] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[  285.579527] usb usb5: root hub lost power or was reset
[  285.579560] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 22 (level, low) -> IRQ 22
[  285.579566] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[  285.579593] usb usb6: root hub lost power or was reset
[  285.579613] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[  285.579619] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[  285.579646] usb usb7: root hub lost power or was reset
[  285.579667] ehci_hcd 0000:00:1d.7: PME# disabled
[  285.579671] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[  285.579678] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[  285.579702] pci 0000:00:1e.0: setting latency timer to 64
[  285.579714] ahci 0000:00:1f.2: setting latency timer to 64
[  285.579834] wl 0000:02:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[  285.579845] wl 0000:02:00.0: setting latency timer to 64
[  285.597413] r8169 0000:03:00.0: wake-up capability disabled by ACPI
[  285.597420] r8169 0000:03:00.0: PME# disabled
[  285.597428] sdhci-pci 0000:04:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[  285.597443] sdhci-pci 0000:04:00.0: setting latency timer to 64
[  285.597464] pci 0000:04:00.2: PME# disabled
[  285.597470] jmb38x_ms 0000:04:00.3: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[  285.597477] jmb38x_ms 0000:04:00.3: setting latency timer to 64
[  285.597493] pci 0000:04:00.4: PME# disabled
[  285.908111] ata6: SATA link down (SStatus 0 SControl 300)
[  285.932113] ata5: SATA link down (SStatus 0 SControl 300)
[  286.134749] sd 0:0:0:0: [sda] Starting disk
[  286.492103] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[  286.494962] ata2.00: ACPI cmd 00/00:00:00:00:00:b0 rejected by device (Stat=0x51 Err=0x04)
[  286.495490] ata2.00: ACPI cmd ef/10:01:00:00:00:b0 rejected by device (Stat=0x51 Err=0x04)
[  286.495948] ata2.00: ACPI cmd ef/10:02:00:00:00:b0 rejected by device (Stat=0x51 Err=0x04)
[  286.495954] ata2.00: ACPI cmd ef/10:03:00:00:00:b0 filtered out
[  286.496476] ata2.00: ACPI cmd ef/10:04:00:00:00:b0 rejected by device (Stat=0x51 Err=0x04)
[  286.496918] ata2.00: ACPI cmd ef/10:05:00:00:00:b0 rejected by device (Stat=0x51 Err=0x04)
[  286.500419] ata2.00: ACPI cmd 00/00:00:00:00:00:b0 rejected by device (Stat=0x51 Err=0x04)
[  286.500860] ata2.00: ACPI cmd ef/10:01:00:00:00:b0 rejected by device (Stat=0x51 Err=0x04)
[  286.501383] ata2.00: ACPI cmd ef/10:02:00:00:00:b0 rejected by device (Stat=0x51 Err=0x04)
[  286.501389] ata2.00: ACPI cmd ef/10:03:00:00:00:b0 filtered out
[  286.501830] ata2.00: ACPI cmd ef/10:04:00:00:00:b0 rejected by device (Stat=0x51 Err=0x04)
[  286.502353] ata2.00: ACPI cmd ef/10:05:00:00:00:b0 rejected by device (Stat=0x51 Err=0x04)
[  286.502397] ata2.00: configured for UDMA/100
[  288.656101] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[  288.659315] ata1.00: ACPI cmd 00/00:00:00:00:00:a0 rejected by device (Stat=0x51 Err=0x04)
[  288.659563] ata1.00: ACPI cmd ef/10:01:00:00:00:a0 rejected by device (Stat=0x51 Err=0x04)
[  288.659670] ata1.00: ACPI cmd ef/10:02:00:00:00:a0 succeeded
[  288.659675] ata1.00: ACPI cmd ef/10:03:00:00:00:a0 filtered out
[  288.659952] ata1.00: ACPI cmd ef/10:04:00:00:00:a0 rejected by device (Stat=0x51 Err=0x04)
[  288.660972] ata1.00: ACPI cmd ef/10:05:00:00:00:a0 rejected by device (Stat=0x51 Err=0x04)
[  288.666994] ata1.00: ACPI cmd 00/00:00:00:00:00:a0 rejected by device (Stat=0x51 Err=0x04)
[  288.667186] ata1.00: ACPI cmd ef/10:01:00:00:00:a0 rejected by device (Stat=0x51 Err=0x04)
[  288.667192] ata1.00: ACPI cmd ef/10:03:00:00:00:a0 filtered out
[  288.667383] ata1.00: ACPI cmd ef/10:04:00:00:00:a0 rejected by device (Stat=0x51 Err=0x04)
[  288.667546] ata1.00: ACPI cmd ef/10:05:00:00:00:a0 rejected by device (Stat=0x51 Err=0x04)
[  288.667590] ata1.00: configured for UDMA/100
[  288.680102] ata1: exception Emask 0x10 SAct 0x0 SErr 0x0 action 0x9 t4
[  288.680106] ata1: irq_stat 0x40000001
[  288.685553] ata1.00: configured for UDMA/100
[  288.685558] ata1: EH complete
[  288.804106] usb 2-5: reset high speed USB device using ehci_hcd and address 3
[  289.244104] usb 5-1: reset low speed USB device using uhci_hcd and address 2
[  289.551442] PM: resume devices took 4.108 seconds
[  289.551476] PM: Finishing wakeup.
[  289.551478] Restarting tasks ... done.
[  289.618225] r8169: eth0: link down
[  289.618413] ADDRCONF(NETDEV_UP): eth0: link is not ready
[  289.988146] CPU0 attaching NULL sched-domain.
[  289.988158] CPU1 attaching NULL sched-domain.
[  290.000309] CPU0 attaching sched-domain:
[  290.000319]  domain 0: span 0-1 level MC
[  290.000326]   groups: 0 1
[  290.000340] CPU1 attaching sched-domain:
[  290.000346]  domain 0: span 0-1 level MC
[  290.000352]   groups: 1 0
[  291.009503] input: PS/2 Mouse as /devices/platform/i8042/serio1/input/input16
[  291.057370] input: AlpsPS/2 ALPS GlidePoint as /devices/platform/i8042/serio1/input/input17
[  300.112134] eth2: no IPv6 routers present
```

---

### Post by ibuclaw on 2010-01-10
After having a review - I believe this is linked to this open bug that has been fixed in Lucid. [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/453963](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/453963)

Can you run the following two:
```
sudo dmidecode -s system-manufacturer
```
```
sudo dmidecode -s system-product-name
```
to confirm.

Regards
Iain

---

### Post by francois203 on 2010-01-10
manufacturer: Hewlett-Packard
product-name: HP Pavillion dv4 Notebook PC

---

### Post by ibuclaw on 2010-01-10
> **francois203 said:**
> manufacturer: Hewlett-Packard
product-name: HP Pavillion dv4 Notebook PC

Yep - you are one of the affected consumers. :)

As I said before this has been fixed upstream, so all should be working when you upgrade to Lucid.

If you don't want to wait around until the April/May time, you have two options.
[LIST=1]
[*]Compile your own kernel with the upstream patch to fix your issue.
[*]Download and install the kernel package from the Lucid repository.
[/LIST]

Regards
Iain

---

### Post by francois203 on 2010-01-10
I'll wait for lucid.
Thank you very much for your help!

---

### Post by ibuclaw on 2010-01-10
No probs.
Since you seem content with the current resolution, have marked this thread as "solved".

Have a good day!

---

