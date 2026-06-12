---
title: "dead usb formats"
date: 2010-02-12
forum: General Help
---

### Post by Vishnu V on 2010-02-12
I have a dead usb and i want to format it. It is not detected in ubuntu .But in disk utility as 0.0KB unrecognized. In gparted it is not shown.

ouput of fdisk -l
```

vishnu@vishnu-laptop:~$ sudo fdisk -l
[sudo] password for vishnu: 

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x68000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        6225    50002281   83  Linux
/dev/sda2            6226        7005     6265350   82  Linux swap / Solaris
/dev/sda3            7006       36310   235392412+   7  HPFS/NTFS
/dev/sda4   *       36311       38914    20909056    7  HPFS/NTFS


```


lsusb
```

vishnu@vishnu-laptop:~$ lsusb
Bus 002 Device 006: ID 0951:1624 Kingston Technology 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 005: ID 413c:8156 Dell Computer Corp. 
Bus 003 Device 004: ID 413c:8158 Dell Computer Corp. 
Bus 003 Device 003: ID 413c:8157 Dell Computer Corp. 
Bus 003 Device 002: ID 0a5c:4500 Broadcom Corp. 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 0c45:63ea Microdia 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```

ls /dev/sdb
```

vishnu@vishnu-laptop:~$ ls /dev/sdb
/dev/sdb

```
when i tried to format using mkfs
```

vishnu@vishnu-laptop:~$ sudo mkfs.ext3 /dev/sdb
mke2fs 1.41.9 (22-Aug-2009)
/dev/sdb is entire device, not just one partition!
Proceed anyway? (y,n) y
mkfs.ext3: Device size reported to be zero.  Invalid partition specified, or
	partition table wasn't reread after running fdisk, due to
	a modified partition being busy and in use.  You may need to reboot
	to re-read your partition table.



```
How can i format it 

Thanks

---

### Post by l-x-l on 2010-02-12
What do you mean by "dead"? Is it empty or not working? Has it ever worked?

---

### Post by Vishnu V on 2010-02-12
It is not working now

---

### Post by lavinog on 2010-02-12
How did you know it was /dev/sdb?

Post the output of dmesg after inserting the usb drive.

---

### Post by Vishnu V on 2010-02-12
> **lavinog said:**
> How did you know it was /dev/sdb?

Post the output of dmesg after inserting the usb drive.

o/p of dmesg
```

[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.31-19-generic (buildd@palmer) (gcc version 4.4.1 (Ubuntu 4.4.1-4ubuntu8) ) #56-Ubuntu SMP Thu Jan 28 01:26:53 UTC 2010 (Ubuntu 2.6.31-19.56-generic)
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
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009c400 (usable)
[    0.000000]  BIOS-e820: 000000000009c400 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000d2000 - 00000000000d4000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 00000000bf8a1000 (usable)
[    0.000000]  BIOS-e820: 00000000bf8a1000 - 00000000bf8a7000 (reserved)
[    0.000000]  BIOS-e820: 00000000bf8a7000 - 00000000bf9ba000 (usable)
[    0.000000]  BIOS-e820: 00000000bf9ba000 - 00000000bfa0f000 (reserved)
[    0.000000]  BIOS-e820: 00000000bfa0f000 - 00000000bfb08000 (usable)
[    0.000000]  BIOS-e820: 00000000bfb08000 - 00000000bfd0f000 (reserved)
[    0.000000]  BIOS-e820: 00000000bfd0f000 - 00000000bfd19000 (usable)
[    0.000000]  BIOS-e820: 00000000bfd19000 - 00000000bfd1f000 (reserved)
[    0.000000]  BIOS-e820: 00000000bfd1f000 - 00000000bfd63000 (usable)
[    0.000000]  BIOS-e820: 00000000bfd63000 - 00000000bfd9f000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000bfd9f000 - 00000000bfde3000 (usable)
[    0.000000]  BIOS-e820: 00000000bfde3000 - 00000000bfdff000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000bfdff000 - 00000000bfe00000 (usable)
[    0.000000]  BIOS-e820: 00000000bfe00000 - 00000000c0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed00000 - 00000000fed00400 (reserved)
[    0.000000]  BIOS-e820: 00000000fed10000 - 00000000fed14000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed18000 - 00000000fed1a000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed1c000 - 00000000fed90000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000ff800000 - 0000000100000000 (reserved)
[    0.000000] DMI present.
[    0.000000] last_pfn = 0xbfe00 max_arch_pfn = 0x100000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000 mask F80000000 write-back
[    0.000000]   1 base 080000000 mask FC0000000 write-back
[    0.000000]   2 base 0FFE00000 mask FFFE00000 write-protect
[    0.000000]   3 disabled
[    0.000000]   4 disabled
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] e820 update range: 0000000000002000 - 0000000000006000 (usable) ==> (reserved)
[    0.000000] Scanning 1 areas for low memory corruption
[    0.000000] modified physical RAM map:
[    0.000000]  modified: 0000000000000000 - 0000000000002000 (usable)
[    0.000000]  modified: 0000000000002000 - 0000000000006000 (reserved)
[    0.000000]  modified: 0000000000006000 - 000000000009c400 (usable)
[    0.000000]  modified: 000000000009c400 - 00000000000a0000 (reserved)
[    0.000000]  modified: 00000000000d2000 - 00000000000d4000 (reserved)
[    0.000000]  modified: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  modified: 0000000000100000 - 00000000bf8a1000 (usable)
[    0.000000]  modified: 00000000bf8a1000 - 00000000bf8a7000 (reserved)
[    0.000000]  modified: 00000000bf8a7000 - 00000000bf9ba000 (usable)
[    0.000000]  modified: 00000000bf9ba000 - 00000000bfa0f000 (reserved)
[    0.000000]  modified: 00000000bfa0f000 - 00000000bfb08000 (usable)
[    0.000000]  modified: 00000000bfb08000 - 00000000bfd0f000 (reserved)
[    0.000000]  modified: 00000000bfd0f000 - 00000000bfd19000 (usable)
[    0.000000]  modified: 00000000bfd19000 - 00000000bfd1f000 (reserved)
[    0.000000]  modified: 00000000bfd1f000 - 00000000bfd63000 (usable)
[    0.000000]  modified: 00000000bfd63000 - 00000000bfd9f000 (ACPI NVS)
[    0.000000]  modified: 00000000bfd9f000 - 00000000bfde3000 (usable)
[    0.000000]  modified: 00000000bfde3000 - 00000000bfdff000 (ACPI data)
[    0.000000]  modified: 00000000bfdff000 - 00000000bfe00000 (usable)
[    0.000000]  modified: 00000000bfe00000 - 00000000c0000000 (reserved)
[    0.000000]  modified: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  modified: 00000000fec00000 - 00000000fec10000 (reserved)
[    0.000000]  modified: 00000000fed00000 - 00000000fed00400 (reserved)
[    0.000000]  modified: 00000000fed10000 - 00000000fed14000 (reserved)
[    0.000000]  modified: 00000000fed18000 - 00000000fed1a000 (reserved)
[    0.000000]  modified: 00000000fed1c000 - 00000000fed90000 (reserved)
[    0.000000]  modified: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  modified: 00000000ff800000 - 0000000100000000 (reserved)
[    0.000000] initial memory mapped : 0 - 00c00000
[    0.000000] init_memory_mapping: 0000000000000000-00000000377fe000
[    0.000000] Using x86 segment limits to approximate NX protection
[    0.000000]  0000000000 - 0000400000 page 4k
[    0.000000]  0000400000 - 0037400000 page 2M
[    0.000000]  0037400000 - 00377fe000 page 4k
[    0.000000] kernel direct mapping tables up to 377fe000 @ 7000-c000
[    0.000000] RAMDISK: 3773a000 - 37fef71f
[    0.000000] Allocated new RAMDISK: 008ad000 - 0116271f
[    0.000000] Move RAMDISK from 000000003773a000 - 0000000037fef71e to 008ad000 - 0116271e
[    0.000000] ACPI: RSDP 000f7860 00024 (v02 PTLTD )
[    0.000000] ACPI: XSDT bfdf7ae2 00074 (v01 DELL    QA09    06040000  LTP 00000000)
[    0.000000] ACPI: FACP bfde7000 000F4 (v03 INTEL  CRESTLNE 06040000 ALAN 00000001)
[    0.000000] ACPI: DSDT bfde8000 07030 (v02 Intel  CANTIGA  06040000 INTL 20061109)
[    0.000000] ACPI: FACS bfd9efc0 00040
[    0.000000] ACPI: HPET bfdfed16 00038 (v01 INTEL  CRESTLNE 06040000 LOHR 0000005A)
[    0.000000] ACPI: MCFG bfdfed4e 0003C (v01 INTEL  CRESTLNE 06040000 LOHR 0000005A)
[    0.000000] ACPI: APIC bfdfed8a 00068 (v01 PTLTD  	 APIC   06040000  LTP 00000000)
[    0.000000] ACPI: BOOT bfdfedf2 00028 (v01 PTLTD  $SBFTBL$ 06040000  LTP 00000001)
[    0.000000] ACPI: SLIC bfdfee1a 00176 (v01 DELL    QA09    06040000  LTP 00000000)
[    0.000000] ACPI: OSFR bfdfef90 00070 (v01 DELL   DELL     06040000 ASL  00000061)
[    0.000000] ACPI: SSDT bfde6000 00655 (v01  PmRef    CpuPm 00003000 INTL 20050624)
[    0.000000] ACPI: SSDT bfde5000 00259 (v01  PmRef  Cpu0Tst 00003000 INTL 20050624)
[    0.000000] ACPI: SSDT bfde4000 0020F (v01  PmRef    ApTst 00003000 INTL 20050624)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] 2182MB HIGHMEM available.
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
[    0.000000]   #4 [000009c400 - 0000100000]    BIOS reserved ==> [000009c400 - 0000100000]
[    0.000000]   #5 [00008a9000 - 00008ac168]              BRK ==> [00008a9000 - 00008ac168]
[    0.000000]   #6 [0000007000 - 0000008000]          PGTABLE ==> [0000007000 - 0000008000]
[    0.000000]   #7 [00008ad000 - 000116271f]      NEW RAMDISK ==> [00008ad000 - 000116271f]
[    0.000000]   #8 [0000008000 - 000000f000]          BOOTMAP ==> [0000008000 - 000000f000]
[    0.000000] found SMP MP-table at [c00f7910] f7910
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000000 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x000377fe
[    0.000000]   HighMem  0x000377fe -> 0x000bfe00
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[9] active PFN ranges
[    0.000000]     0: 0x00000000 -> 0x00000002
[    0.000000]     0: 0x00000006 -> 0x0000009c
[    0.000000]     0: 0x00000100 -> 0x000bf8a1
[    0.000000]     0: 0x000bf8a7 -> 0x000bf9ba
[    0.000000]     0: 0x000bfa0f -> 0x000bfb08
[    0.000000]     0: 0x000bfd0f -> 0x000bfd19
[    0.000000]     0: 0x000bfd1f -> 0x000bfd63
[    0.000000]     0: 0x000bfd9f -> 0x000bfde3
[    0.000000]     0: 0x000bfdff -> 0x000bfe00
[    0.000000] On node 0 totalpages: 785112
[    0.000000] free_area_init_node: node 0, pgdat c0784960, node_mem_map c1163000
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3960 pages, LIFO batch:0
[    0.000000]   Normal zone: 1744 pages used for memmap
[    0.000000]   Normal zone: 221486 pages, LIFO batch:31
[    0.000000]   HighMem zone: 4365 pages used for memmap
[    0.000000]   HighMem zone: 553525 pages, LIFO batch:31
[    0.000000] Using APIC driver default
[    0.000000] ACPI: PM-Timer IO Port: 0x408
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: Skipping IOAPIC probe due to 'noapic' option.
[    0.000000] Using ACPI for processor (LAPIC) configuration information
[    0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000
[    0.000000] Intel MultiProcessor Specification v1.4
[    0.000000]     Virtual Wire compatibility mode.
[    0.000000] MPTABLE: OEM ID: INTEL   
[    0.000000] MPTABLE: Product ID: MontavinaCRB
[    0.000000] MPTABLE: APIC at: 0xFEE00000
[    0.000000] I/O APIC #2 Version 32 at 0xFEC00000.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] Processors: 2
[    0.000000] SMP: Allowing 2 CPUs, 0 hotplug CPUs
[    0.000000] nr_irqs_gsi: 24
[    0.000000] PM: Registered nosave memory: 0000000000002000 - 0000000000006000
[    0.000000] PM: Registered nosave memory: 000000000009c000 - 000000000009d000
[    0.000000] PM: Registered nosave memory: 000000000009d000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000d2000
[    0.000000] PM: Registered nosave memory: 00000000000d2000 - 00000000000d4000
[    0.000000] PM: Registered nosave memory: 00000000000d4000 - 00000000000e0000
[    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at c0000000 (gap: c0000000:20000000)
[    0.000000] NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:2 nr_node_ids:1
[    0.000000] PERCPU: Embedded 14 pages at c2973000, static data 35612 bytes
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 778971
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.31-19-generic root=UUID=5da8b70b-30ff-4a9e-9657-7af5161bde69 ro quiet splash noapic
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] xsave/xrstor: enabled xstate_bv 0x3, cntxt size 0x240
[    0.000000] allocated 15718400 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] Initializing HighMem for node 0 (000377fe:000bfe00)
[    0.000000] Memory: 3081888k/3143680k available (4567k kernel code, 57708k reserved, 2141k data, 540k init, 2231560k highmem)
[    0.000000] virtual kernel memory layout:
[    0.000000]     fixmap  : 0xfff1d000 - 0xfffff000   ( 904 kB)
[    0.000000]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[    0.000000]     vmalloc : 0xf7ffe000 - 0xff7fe000   ( 120 MB)
[    0.000000]     lowmem  : 0xc0000000 - 0xf77fe000   ( 887 MB)
[    0.000000]       .init : 0xc078e000 - 0xc0815000   ( 540 kB)
[    0.000000]       .data : 0xc0575c48 - 0xc078d408   (2141 kB)
[    0.000000]       .text : 0xc0100000 - 0xc0575c48   (4567 kB)
[    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.000000] SLUB: Genslabs=13, HWalign=64, Order=0-3, MinObjects=0, CPUs=2, Nodes=1
[    0.000000] NR_IRQS:2304 nr_irqs:424
[    0.000000] Extended CMOS year: 2000
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 2095.014 MHz processor.
[    0.001278] Console: colour VGA+ 80x25
[    0.001281] console [tty0] enabled
[    0.001441] hpet clockevent registered
[    0.001445] HPET: 4 timers in total, 0 timers will be used for per-cpu timer
[    0.001449] Calibrating delay loop (skipped), value calculated using timer frequency.. 4190.02 BogoMIPS (lpj=8380056)
[    0.001466] Security Framework initialized
[    0.001484] AppArmor: AppArmor initialized
[    0.001490] Mount-cache hash table entries: 512
[    0.001603] Initializing cgroup subsys ns
[    0.001607] Initializing cgroup subsys cpuacct
[    0.001611] Initializing cgroup subsys memory
[    0.001617] Initializing cgroup subsys freezer
[    0.001619] Initializing cgroup subsys net_cls
[    0.001632] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.001634] CPU: L2 cache: 2048K
[    0.001637] CPU: Physical Processor ID: 0
[    0.001638] CPU: Processor Core ID: 0
[    0.001642] mce: CPU supports 6 MCE banks
[    0.001649] CPU0: Thermal monitoring enabled (TM2)
[    0.001652] using mwait in idle threads.
[    0.001658] Performance Counters: Core2 events, Intel PMU driver.
[    0.001665] ... version:                 2
[    0.001667] ... bit width:               40
[    0.001668] ... generic counters:        2
[    0.001670] ... value mask:              000000ffffffffff
[    0.001672] ... max period:              000000007fffffff
[    0.001673] ... fixed-purpose counters:  3
[    0.001675] ... counter mask:            0000000700000003
[    0.001680] Checking 'hlt' instruction... OK.
[    0.018584] ACPI: Core revision 20090521
[    0.028888] ACPI: setting ELCR to 0200 (from 0ca0)
[    0.032054] CPU0: Intel(R) Core(TM)2 Duo CPU     T6500  @ 2.10GHz stepping 0a
[    0.036001] APIC calibration not consistent with PM-Timer: 351ms instead of 100ms
[    0.036001] APIC delta adjusted to PM-Timer: 1247013 (4389435)
[    0.036001] Booting processor 1 APIC 0x1 ip 0x6000
[    0.004000] Initializing CPU#1
[    0.004000] Calibrating delay using timer specific routine.. 4189.96 BogoMIPS (lpj=8379922)
[    0.004000] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.004000] CPU: L2 cache: 2048K
[    0.004000] CPU: Physical Processor ID: 0
[    0.004000] CPU: Processor Core ID: 1
[    0.004000] mce: CPU supports 6 MCE banks
[    0.004000] CPU1: Thermal monitoring enabled (TM2)
[    0.004000] x86 PAT enabled: cpu 1, old 0x7040600070406, new 0x7010600070106
[    0.121489] CPU1: Intel(R) Core(TM)2 Duo CPU     T6500  @ 2.10GHz stepping 0a
[    0.121503] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
[    0.124021] Brought up 2 CPUs
[    0.124024] Total of 2 processors activated (8379.98 BogoMIPS).
[    0.124033] CPU0 attaching sched-domain:
[    0.124036]  domain 0: span 0-1 level MC
[    0.124038]   groups: 0 1
[    0.124043] CPU1 attaching sched-domain:
[    0.124045]  domain 0: span 0-1 level MC
[    0.124047]   groups: 1 0
[    0.124117] Booting paravirtualized kernel on bare hardware
[    0.124194] regulator: core version 0.5
[    0.124194] Time: 16:04:03  Date: 02/12/10
[    0.124194] NET: Registered protocol family 16
[    0.124194] EISA bus registered
[    0.124203] ACPI: bus type pci registered
[    0.124267] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 255
[    0.124269] PCI: MCFG area at e0000000 reserved in E820
[    0.124271] PCI: Using MMCONFIG for extended config space
[    0.124273] PCI: Using configuration type 1 for base access
[    0.125197] bio: create slab <bio-0> at 0
[    0.128360] ACPI: EC: Look up EC in DSDT
[    0.131839] ACPI: BIOS _OSI(Linux) query ignored
[    0.140633] ACPI: Interpreter enabled
[    0.140639] ACPI: (supports S0 S3 S4 S5)
[    0.140660] ACPI: Using PIC for interrupt routing
[    0.144222] ACPI: EC: non-query interrupt received, switching to interrupt mode
[    0.152362] ACPI: EC: GPE = 0x1c, I/O: command/status = 0x66, data = 0x62
[    0.152365] ACPI: EC: driver started in interrupt mode
[    0.152728] ACPI: No dock devices found.
[    0.153173] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.153280] pci 0000:00:01.0: PME# supported from D0 D3hot D3cold
[    0.153284] pci 0000:00:01.0: PME# disabled
[    0.153396] pci 0000:00:1a.0: reg 20 io port: [0x1800-0x181f]
[    0.156095] pci 0000:00:1a.1: reg 20 io port: [0x1820-0x183f]
[    0.156201] pci 0000:00:1a.2: reg 20 io port: [0x1840-0x185f]
[    0.156305] pci 0000:00:1a.7: reg 10 32bit mmio: [0xfc504800-0xfc504bff]
[    0.156376] pci 0000:00:1a.7: PME# supported from D0 D3hot D3cold
[    0.156382] pci 0000:00:1a.7: PME# disabled
[    0.156437] pci 0000:00:1b.0: reg 10 64bit mmio: [0xfc500000-0xfc503fff]
[    0.156496] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    0.156500] pci 0000:00:1b.0: PME# disabled
[    0.156583] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    0.156588] pci 0000:00:1c.0: PME# disabled
[    0.156673] pci 0000:00:1c.1: PME# supported from D0 D3hot D3cold
[    0.156678] pci 0000:00:1c.1: PME# disabled
[    0.156766] pci 0000:00:1c.3: PME# supported from D0 D3hot D3cold
[    0.156771] pci 0000:00:1c.3: PME# disabled
[    0.156857] pci 0000:00:1c.5: PME# supported from D0 D3hot D3cold
[    0.156862] pci 0000:00:1c.5: PME# disabled
[    0.156935] pci 0000:00:1d.0: reg 20 io port: [0x1860-0x187f]
[    0.157043] pci 0000:00:1d.1: reg 20 io port: [0x1880-0x189f]
[    0.157148] pci 0000:00:1d.2: reg 20 io port: [0x18a0-0x18bf]
[    0.157242] pci 0000:00:1d.7: reg 10 32bit mmio: [0xfc504c00-0xfc504fff]
[    0.157308] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
[    0.157313] pci 0000:00:1d.7: PME# disabled
[    0.157558] pci 0000:00:1f.2: reg 10 io port: [0x18f0-0x18f7]
[    0.157566] pci 0000:00:1f.2: reg 14 io port: [0x18e4-0x18e7]
[    0.157573] pci 0000:00:1f.2: reg 18 io port: [0x18e8-0x18ef]
[    0.157581] pci 0000:00:1f.2: reg 1c io port: [0x18e0-0x18e3]
[    0.157588] pci 0000:00:1f.2: reg 20 io port: [0x18c0-0x18df]
[    0.157596] pci 0000:00:1f.2: reg 24 32bit mmio: [0xfc504000-0xfc5047ff]
[    0.157645] pci 0000:00:1f.2: PME# supported from D3hot
[    0.157650] pci 0000:00:1f.2: PME# disabled
[    0.157691] pci 0000:00:1f.3: reg 10 64bit mmio: [0x000000-0x0000ff]
[    0.157710] pci 0000:00:1f.3: reg 20 io port: [0x1c00-0x1c1f]
[    0.157775] pci 0000:01:00.0: reg 10 32bit mmio: [0xd0000000-0xdfffffff]
[    0.157783] pci 0000:01:00.0: reg 14 io port: [0x2000-0x20ff]
[    0.157791] pci 0000:01:00.0: reg 18 32bit mmio: [0xfc000000-0xfc00ffff]
[    0.157817] pci 0000:01:00.0: reg 30 32bit mmio: [0x000000-0x01ffff]
[    0.157848] pci 0000:01:00.0: supports D1 D2
[    0.157898] pci 0000:01:00.1: reg 10 32bit mmio: [0xfc010000-0xfc013fff]
[    0.157963] pci 0000:01:00.1: supports D1 D2
[    0.158031] pci 0000:00:01.0: bridge io port: [0x2000-0x2fff]
[    0.158035] pci 0000:00:01.0: bridge 32bit mmio: [0xfc000000-0xfc0fffff]
[    0.158040] pci 0000:00:01.0: bridge 64bit mmio pref: [0xd0000000-0xdfffffff]
[    0.158094] pci 0000:00:1c.0: bridge io port: [0x3000-0x3fff]
[    0.158099] pci 0000:00:1c.0: bridge 32bit mmio: [0xf6000000-0xf7ffffff]
[    0.158106] pci 0000:00:1c.0: bridge 64bit mmio pref: [0xf0000000-0xf1ffffff]
[    0.158195] pci 0000:04:00.0: reg 10 64bit mmio: [0xf8000000-0xf8001fff]
[    0.158307] pci 0000:04:00.0: PME# supported from D0 D3hot D3cold
[    0.158314] pci 0000:04:00.0: PME# disabled
[    0.158393] pci 0000:00:1c.1: bridge io port: [0x4000-0x4fff]
[    0.158398] pci 0000:00:1c.1: bridge 32bit mmio: [0xf8000000-0xf9ffffff]
[    0.158406] pci 0000:00:1c.1: bridge 64bit mmio pref: [0xf2000000-0xf3ffffff]
[    0.158461] pci 0000:00:1c.3: bridge io port: [0x5000-0x5fff]
[    0.158466] pci 0000:00:1c.3: bridge 32bit mmio: [0xfa000000-0xfbffffff]
[    0.158474] pci 0000:00:1c.3: bridge 64bit mmio pref: [0xf4000000-0xf5ffffff]
[    0.158713] pci 0000:08:00.0: reg 10 64bit mmio: [0xfc100000-0xfc10ffff]
[    0.158818] pci 0000:08:00.0: PME# supported from D3hot D3cold
[    0.158826] pci 0000:08:00.0: PME# disabled
[    0.158902] pci 0000:00:1c.5: bridge 32bit mmio: [0xfc100000-0xfc1fffff]
[    0.158957] pci 0000:09:01.0: reg 10 32bit mmio: [0xfc200000-0xfc2007ff]
[    0.159026] pci 0000:09:01.0: supports D1 D2
[    0.159028] pci 0000:09:01.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.159033] pci 0000:09:01.0: PME# disabled
[    0.159080] pci 0000:09:01.1: reg 10 32bit mmio: [0xfc200800-0xfc2008ff]
[    0.159148] pci 0000:09:01.1: supports D1 D2
[    0.159150] pci 0000:09:01.1: PME# supported from D0 D1 D2 D3hot D3cold
[    0.159155] pci 0000:09:01.1: PME# disabled
[    0.159202] pci 0000:09:01.2: reg 10 32bit mmio: [0xfc200c00-0xfc200cff]
[    0.159271] pci 0000:09:01.2: supports D1 D2
[    0.159273] pci 0000:09:01.2: PME# supported from D0 D1 D2 D3hot D3cold
[    0.159279] pci 0000:09:01.2: PME# disabled
[    0.159326] pci 0000:09:01.3: reg 10 32bit mmio: [0xfc201000-0xfc2010ff]
[    0.159394] pci 0000:09:01.3: supports D1 D2
[    0.159397] pci 0000:09:01.3: PME# supported from D0 D1 D2 D3hot D3cold
[    0.159402] pci 0000:09:01.3: PME# disabled
[    0.159450] pci 0000:09:01.4: reg 10 32bit mmio: [0xfc201400-0xfc2014ff]
[    0.159517] pci 0000:09:01.4: supports D1 D2
[    0.159519] pci 0000:09:01.4: PME# supported from D0 D1 D2 D3hot D3cold
[    0.159525] pci 0000:09:01.4: PME# disabled
[    0.159593] pci 0000:00:1e.0: transparent bridge
[    0.159600] pci 0000:00:1e.0: bridge 32bit mmio: [0xfc200000-0xfc2fffff]
[    0.159641] pci_bus 0000:00: on NUMA node 0
[    0.159646] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.159835] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P2._PRT]
[    0.159913] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P1._PRT]
[    0.160022] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP01._PRT]
[    0.160105] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP02._PRT]
[    0.160185] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP04._PRT]
[    0.160254] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP06._PRT]
[    0.171781] ACPI: PCI Interrupt Link [LNKA] (IRQs 1 3 4 *5 6 7 10 12 14 15)
[    0.171885] ACPI: PCI Interrupt Link [LNKB] (IRQs 1 3 4 5 6 7 11 12 14 15) *10
[    0.171988] ACPI: PCI Interrupt Link [LNKC] (IRQs 1 3 4 5 6 7 *10 12 14 15)
[    0.172101] ACPI: PCI Interrupt Link [LNKD] (IRQs 1 3 4 5 6 7 11 12 14 15) *10
[    0.172203] ACPI: PCI Interrupt Link [LNKE] (IRQs 1 3 4 5 6 7 10 12 14 15) *0, disabled.
[    0.172306] ACPI: PCI Interrupt Link [LNKF] (IRQs 1 3 4 5 6 7 *11 12 14 15)
[    0.172407] ACPI: PCI Interrupt Link [LNKG] (IRQs 1 3 4 5 6 7 10 12 14 15) *11
[    0.172509] ACPI: PCI Interrupt Link [LNKH] (IRQs 1 3 4 5 6 *7 11 12 14 15)
[    0.172679] SCSI subsystem initialized
[    0.172698] libata version 3.00 loaded.
[    0.172698] usbcore: registered new interface driver usbfs
[    0.172698] usbcore: registered new interface driver hub
[    0.172698] usbcore: registered new device driver usb
[    0.172698] ACPI: WMI: Mapper loaded
[    0.172698] PCI: Using ACPI for IRQ routing
[    0.184009] Bluetooth: Core ver 2.15
[    0.184021] NET: Registered protocol family 31
[    0.184021] Bluetooth: HCI device and connection manager initialized
[    0.184021] Bluetooth: HCI socket layer initialized
[    0.184021] NetLabel: Initializing
[    0.184021] NetLabel:  domain hash size = 128
[    0.184021] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.184030] NetLabel:  unlabeled traffic allowed by default
[    0.184060] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0
[    0.184066] hpet0: 4 comparators, 64-bit 14.318180 MHz counter
[    0.200008] pnp: PnP ACPI init
[    0.200018] ACPI: bus type pnp registered
[    0.202362] pnp: PnP ACPI: found 9 devices
[    0.202365] ACPI: ACPI bus type pnp unregistered
[    0.202368] PnPBIOS: Disabled by ACPI PNP
[    0.202379] system 00:02: iomem range 0xfed00000-0xfed003ff has been reserved
[    0.202385] system 00:04: ioport range 0x400-0x47f has been reserved
[    0.202388] system 00:04: ioport range 0x680-0x69f has been reserved
[    0.202391] system 00:04: ioport range 0x480-0x48f has been reserved
[    0.202393] system 00:04: ioport range 0xffff-0xffff has been reserved
[    0.202396] system 00:04: ioport range 0xffff-0xffff has been reserved
[    0.202399] system 00:04: ioport range 0x1000-0x107f has been reserved
[    0.202401] system 00:04: ioport range 0x1180-0x11ff has been reserved
[    0.202404] system 00:04: ioport range 0x164e-0x164f has been reserved
[    0.202407] system 00:04: ioport range 0xfe00-0xfe00 has been reserved
[    0.202409] system 00:04: ioport range 0x900-0x97f has been reserved
[    0.202416] system 00:08: iomem range 0xfed1c000-0xfed1ffff has been reserved
[    0.202419] system 00:08: iomem range 0xfed10000-0xfed13fff has been reserved
[    0.202421] system 00:08: iomem range 0xfed18000-0xfed18fff has been reserved
[    0.202424] system 00:08: iomem range 0xfed19000-0xfed19fff has been reserved
[    0.202427] system 00:08: iomem range 0xe0000000-0xefffffff has been reserved
[    0.202430] system 00:08: iomem range 0xfeb00000-0xfeb03fff has been reserved
[    0.202432] system 00:08: iomem range 0xfed20000-0xfed3ffff has been reserved
[    0.202435] system 00:08: iomem range 0xfed40000-0xfed44fff has been reserved
[    0.202438] system 00:08: iomem range 0xfed45000-0xfed8ffff has been reserved
[    0.237286] AppArmor: AppArmor Filesystem Enabled
[    0.237364] pci 0000:00:01.0: PCI bridge, secondary bus 0000:01
[    0.237367] pci 0000:00:01.0:   IO window: 0x2000-0x2fff
[    0.237372] pci 0000:00:01.0:   MEM window: 0xfc000000-0xfc0fffff
[    0.237375] pci 0000:00:01.0:   PREFETCH window: 0x000000d0000000-0x000000dfffffff
[    0.237380] pci 0000:00:1c.0: PCI bridge, secondary bus 0000:02
[    0.237384] pci 0000:00:1c.0:   IO window: 0x3000-0x3fff
[    0.237390] pci 0000:00:1c.0:   MEM window: 0xf6000000-0xf7ffffff
[    0.237395] pci 0000:00:1c.0:   PREFETCH window: 0x000000f0000000-0x000000f1ffffff
[    0.237402] pci 0000:00:1c.1: PCI bridge, secondary bus 0000:04
[    0.237406] pci 0000:00:1c.1:   IO window: 0x4000-0x4fff
[    0.237412] pci 0000:00:1c.1:   MEM window: 0xf8000000-0xf9ffffff
[    0.237417] pci 0000:00:1c.1:   PREFETCH window: 0x000000f2000000-0x000000f3ffffff
[    0.237424] pci 0000:00:1c.3: PCI bridge, secondary bus 0000:06
[    0.237427] pci 0000:00:1c.3:   IO window: 0x5000-0x5fff
[    0.237433] pci 0000:00:1c.3:   MEM window: 0xfa000000-0xfbffffff
[    0.237438] pci 0000:00:1c.3:   PREFETCH window: 0x000000f4000000-0x000000f5ffffff
[    0.237446] pci 0000:00:1c.5: PCI bridge, secondary bus 0000:08
[    0.237448] pci 0000:00:1c.5:   IO window: disabled
[    0.237454] pci 0000:00:1c.5:   MEM window: 0xfc100000-0xfc1fffff
[    0.237458] pci 0000:00:1c.5:   PREFETCH window: disabled
[    0.237463] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:09
[    0.237465] pci 0000:00:1e.0:   IO window: disabled
[    0.237471] pci 0000:00:1e.0:   MEM window: 0xfc200000-0xfc2fffff
[    0.237476] pci 0000:00:1e.0:   PREFETCH window: disabled
[    0.237631] ACPI: PCI Interrupt Link [LNKA] enabled at IRQ 5
[    0.237634] PCI: setting IRQ 5 as level-triggered
[    0.237640] pci 0000:00:01.0: PCI INT A -> Link[LNKA] -> GSI 5 (level, low) -> IRQ 5
[    0.237644] pci 0000:00:01.0: setting latency timer to 64
[    0.237792] ACPI: PCI Interrupt Link [LNKB] enabled at IRQ 11
[    0.237794] PCI: setting IRQ 11 as level-triggered
[    0.237800] pci 0000:00:1c.0: PCI INT A -> Link[LNKB] -> GSI 11 (level, low) -> IRQ 11
[    0.237805] pci 0000:00:1c.0: setting latency timer to 64
[    0.237814] pci 0000:00:1c.1: PCI INT B -> Link[LNKA] -> GSI 5 (level, low) -> IRQ 5
[    0.237819] pci 0000:00:1c.1: setting latency timer to 64
[    0.237966] ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 11
[    0.237969] pci 0000:00:1c.3: PCI INT D -> Link[LNKD] -> GSI 11 (level, low) -> IRQ 11
[    0.237974] pci 0000:00:1c.3: setting latency timer to 64
[    0.237983] pci 0000:00:1c.5: PCI INT B -> Link[LNKA] -> GSI 5 (level, low) -> IRQ 5
[    0.237988] pci 0000:00:1c.5: setting latency timer to 64
[    0.237996] pci 0000:00:1e.0: setting latency timer to 64
[    0.238001] pci_bus 0000:00: resource 0 io:  [0x00-0xffff]
[    0.238003] pci_bus 0000:00: resource 1 mem: [0x000000-0xffffffff]
[    0.238005] pci_bus 0000:01: resource 0 io:  [0x2000-0x2fff]
[    0.238008] pci_bus 0000:01: resource 1 mem: [0xfc000000-0xfc0fffff]
[    0.238010] pci_bus 0000:01: resource 2 pref mem [0xd0000000-0xdfffffff]
[    0.238013] pci_bus 0000:02: resource 0 io:  [0x3000-0x3fff]
[    0.238015] pci_bus 0000:02: resource 1 mem: [0xf6000000-0xf7ffffff]
[    0.238018] pci_bus 0000:02: resource 2 pref mem [0xf0000000-0xf1ffffff]
[    0.238020] pci_bus 0000:04: resource 0 io:  [0x4000-0x4fff]
[    0.238022] pci_bus 0000:04: resource 1 mem: [0xf8000000-0xf9ffffff]
[    0.238025] pci_bus 0000:04: resource 2 pref mem [0xf2000000-0xf3ffffff]
[    0.238027] pci_bus 0000:06: resource 0 io:  [0x5000-0x5fff]
[    0.238030] pci_bus 0000:06: resource 1 mem: [0xfa000000-0xfbffffff]
[    0.238032] pci_bus 0000:06: resource 2 pref mem [0xf4000000-0xf5ffffff]
[    0.238034] pci_bus 0000:08: resource 1 mem: [0xfc100000-0xfc1fffff]
[    0.238037] pci_bus 0000:09: resource 1 mem: [0xfc200000-0xfc2fffff]
[    0.238039] pci_bus 0000:09: resource 3 io:  [0x00-0xffff]
[    0.238042] pci_bus 0000:09: resource 4 mem: [0x000000-0xffffffff]
[    0.238072] NET: Registered protocol family 2
[    0.238157] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.238446] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.238879] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.239090] TCP: Hash tables configured (established 131072 bind 65536)
[    0.239092] TCP reno registered
[    0.239158] NET: Registered protocol family 1
[    0.239214] Trying to unpack rootfs image as initramfs...
[    0.461083] Freeing initrd memory: 8917k freed
[    0.465586] Simple Boot Flag at 0x36 set to 0x1
[    0.465758] cpufreq-nforce2: No nForce2 chipset.
[    0.465779] Scanning for low memory corruption every 60 seconds
[    0.465879] audit: initializing netlink socket (disabled)
[    0.465895] type=2000 audit(1265990642.463:1): initialized
[    0.474199] highmem bounce pool size: 64 pages
[    0.474205] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    0.475558] VFS: Disk quotas dquot_6.5.2
[    0.475615] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.476123] fuse init (API version 7.12)
[    0.476202] msgmni has been set to 1679
[    0.476392] alg: No test for stdrng (krng)
[    0.476404] io scheduler noop registered
[    0.476406] io scheduler anticipatory registered
[    0.476408] io scheduler deadline registered
[    0.476447] io scheduler cfq registered (default)
[    0.476602] pci 0000:01:00.0: Boot video device
[    0.476732]   alloc irq_desc for 24 on node -1
[    0.476734]   alloc kstat_irqs on node -1
[    0.476742] pcieport-driver 0000:00:01.0: irq 24 for MSI/MSI-X
[    0.476749] pcieport-driver 0000:00:01.0: setting latency timer to 64
[    0.476882]   alloc irq_desc for 25 on node -1
[    0.476883]   alloc kstat_irqs on node -1
[    0.476892] pcieport-driver 0000:00:1c.0: irq 25 for MSI/MSI-X
[    0.476903] pcieport-driver 0000:00:1c.0: setting latency timer to 64
[    0.477055]   alloc irq_desc for 26 on node -1
[    0.477056]   alloc kstat_irqs on node -1
[    0.477065] pcieport-driver 0000:00:1c.1: irq 26 for MSI/MSI-X
[    0.477076] pcieport-driver 0000:00:1c.1: setting latency timer to 64
[    0.477227]   alloc irq_desc for 27 on node -1
[    0.477229]   alloc kstat_irqs on node -1
[    0.477238] pcieport-driver 0000:00:1c.3: irq 27 for MSI/MSI-X
[    0.477249] pcieport-driver 0000:00:1c.3: setting latency timer to 64
[    0.477401]   alloc irq_desc for 28 on node -1
[    0.477403]   alloc kstat_irqs on node -1
[    0.477412] pcieport-driver 0000:00:1c.5: irq 28 for MSI/MSI-X
[    0.477423] pcieport-driver 0000:00:1c.5: setting latency timer to 64
[    0.477526] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.477688] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.501520] Switched to high resolution mode on CPU 1
[    0.503995] Switched to high resolution mode on CPU 0
[    0.576068] ACPI: AC Adapter [ADP1] (off-line)
[    0.576124] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input0
[    0.576127] ACPI: Power Button [PWRF]
[    0.576182] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1
[    0.576185] ACPI: Power Button [PWRB]
[    0.576223] input: Sleep Button as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input2
[    0.576226] ACPI: Sleep Button [SLPB]
[    0.576265] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input3
[    0.577104] ACPI: Lid Switch [LID0]
[    0.577879] ACPI: SSDT bfd1aca0 00223 (v01  PmRef  Cpu0Ist 00003000 INTL 20050624)
[    0.578397] ACPI: SSDT bfd19620 00575 (v01  PmRef  Cpu0Cst 00003001 INTL 20050624)
[    0.584530] Monitor-Mwait will be used to enter C-1 state
[    0.584552] Monitor-Mwait will be used to enter C-2 state
[    0.584571] Monitor-Mwait will be used to enter C-3 state
[    0.584578] Marking TSC unstable due to TSC halts in idle
[    0.584596] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[    0.584618] processor LNXCPU:00: registered as cooling_device0
[    0.584622] ACPI: Processor [CPU0] (supports 8 throttling states)
[    0.585049] ACPI: SSDT bfd1aa20 001CF (v01  PmRef    ApIst 00003000 INTL 20050624)
[    0.585451] ACPI: SSDT bfd1af20 0008D (v01  PmRef    ApCst 00003000 INTL 20050624)
[    0.590600] ACPI: CPU1 (power states: C1[C1] C2[C2] C3[C3])
[    0.590622] processor LNXCPU:01: registered as cooling_device1
[    0.590626] ACPI: Processor [CPU1] (supports 8 throttling states)
[    0.594881] thermal LNXTHERM:01: registered as thermal_zone0
[    0.594889] ACPI: Thermal Zone [TZ00] (46 C)
[    0.596521] thermal LNXTHERM:02: registered as thermal_zone1
[    0.596529] ACPI: Thermal Zone [TZ01] (37 C)
[    0.599101] thermal LNXTHERM:03: registered as thermal_zone2
[    0.599108] ACPI: Thermal Zone [TZ02] (50 C)
[    0.599158] isapnp: Scanning for PnP cards...
[    0.667806] ACPI: Battery Slot [BAT0] (battery present)
[    0.954032] isapnp: No Plug & Play device found
[    0.955107] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    0.956315] brd: module loaded
[    0.956729] loop: module loaded
[    0.956793] input: Macintosh mouse button emulation as /devices/virtual/input/input4
[    0.956859] ahci 0000:00:1f.2: version 3.0
[    0.956872] ahci 0000:00:1f.2: PCI INT B -> Link[LNKD] -> GSI 11 (level, low) -> IRQ 11
[    0.956903]   alloc irq_desc for 29 on node -1
[    0.956905]   alloc kstat_irqs on node -1
[    0.956915] ahci 0000:00:1f.2: irq 29 for MSI/MSI-X
[    0.956999] ahci 0000:00:1f.2: AHCI 0001.0200 32 slots 4 ports 3 Gbps 0x33 impl SATA mode
[    0.957002] ahci 0000:00:1f.2: flags: 64bit ncq sntf led clo pmp pio slum part 
[    0.957008] ahci 0000:00:1f.2: setting latency timer to 64
[    0.957265] scsi0 : ahci
[    0.957347] scsi1 : ahci
[    0.957398] scsi2 : ahci
[    0.957452] scsi3 : ahci
[    0.957503] scsi4 : ahci
[    0.957555] scsi5 : ahci
[    0.957596] ata1: SATA max UDMA/133 abar m2048@0xfc504000 port 0xfc504100 irq 29
[    0.957600] ata2: SATA max UDMA/133 abar m2048@0xfc504000 port 0xfc504180 irq 29
[    0.957601] ata3: DUMMY
[    0.957603] ata4: DUMMY
[    0.957606] ata5: SATA max UDMA/133 abar m2048@0xfc504000 port 0xfc504300 irq 29
[    0.957609] ata6: SATA max UDMA/133 abar m2048@0xfc504000 port 0xfc504380 irq 29
[    0.958488] Fixed MDIO Bus: probed
[    0.958519] PPP generic driver version 2.4.2
[    0.958594] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.958615] ehci_hcd 0000:00:1a.7: PCI INT C -> Link[LNKD] -> GSI 11 (level, low) -> IRQ 11
[    0.958626] ehci_hcd 0000:00:1a.7: setting latency timer to 64
[    0.958629] ehci_hcd 0000:00:1a.7: EHCI Host Controller
[    0.958674] ehci_hcd 0000:00:1a.7: new USB bus registered, assigned bus number 1
[    0.962585] ehci_hcd 0000:00:1a.7: debug port 1
[    0.962592] ehci_hcd 0000:00:1a.7: cache line size of 32 is not supported
[    0.962599] ehci_hcd 0000:00:1a.7: irq 11, io mem 0xfc504800
[    0.976014] ehci_hcd 0000:00:1a.7: USB 2.0 started, EHCI 1.00
[    0.976099] usb usb1: configuration #1 chosen from 1 choice
[    0.976126] hub 1-0:1.0: USB hub found
[    0.976133] hub 1-0:1.0: 6 ports detected
[    0.976367] ACPI: PCI Interrupt Link [LNKH] enabled at IRQ 7
[    0.976370] PCI: setting IRQ 7 as level-triggered
[    0.976376] ehci_hcd 0000:00:1d.7: PCI INT A -> Link[LNKH] -> GSI 7 (level, low) -> IRQ 7
[    0.976386] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    0.976389] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    0.976419] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 2
[    0.980319] ehci_hcd 0000:00:1d.7: debug port 1
[    0.980326] ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported
[    0.980333] ehci_hcd 0000:00:1d.7: irq 7, io mem 0xfc504c00
[    0.996016] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    0.996093] usb usb2: configuration #1 chosen from 1 choice
[    0.996118] hub 2-0:1.0: USB hub found
[    0.996123] hub 2-0:1.0: 6 ports detected
[    0.996182] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.996198] uhci_hcd: USB Universal Host Controller Interface driver
[    0.996219] uhci_hcd 0000:00:1a.0: PCI INT A -> Link[LNKA] -> GSI 5 (level, low) -> IRQ 5
[    0.996226] uhci_hcd 0000:00:1a.0: setting latency timer to 64
[    0.996229] uhci_hcd 0000:00:1a.0: UHCI Host Controller
[    0.996256] uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 3
[    0.996286] uhci_hcd 0000:00:1a.0: irq 5, io base 0x00001800
[    0.996357] usb usb3: configuration #1 chosen from 1 choice
[    0.996380] hub 3-0:1.0: USB hub found
[    0.996386] hub 3-0:1.0: 2 ports detected
[    0.996580] ACPI: PCI Interrupt Link [LNKF] enabled at IRQ 11
[    0.996584] uhci_hcd 0000:00:1a.1: PCI INT B -> Link[LNKF] -> GSI 11 (level, low) -> IRQ 11
[    0.996590] uhci_hcd 0000:00:1a.1: setting latency timer to 64
[    0.996594] uhci_hcd 0000:00:1a.1: UHCI Host Controller
[    0.996624] uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus number 4
[    0.996650] uhci_hcd 0000:00:1a.1: irq 11, io base 0x00001820
[    0.996722] usb usb4: configuration #1 chosen from 1 choice
[    0.996748] hub 4-0:1.0: USB hub found
[    0.996753] hub 4-0:1.0: 2 ports detected
[    0.996799] uhci_hcd 0000:00:1a.2: PCI INT C -> Link[LNKD] -> GSI 11 (level, low) -> IRQ 11
[    0.996806] uhci_hcd 0000:00:1a.2: setting latency timer to 64
[    0.996809] uhci_hcd 0000:00:1a.2: UHCI Host Controller
[    0.996841] uhci_hcd 0000:00:1a.2: new USB bus registered, assigned bus number 5
[    0.996867] uhci_hcd 0000:00:1a.2: irq 11, io base 0x00001840
[    0.996937] usb usb5: configuration #1 chosen from 1 choice
[    0.996963] hub 5-0:1.0: USB hub found
[    0.996968] hub 5-0:1.0: 2 ports detected
[    0.997013] uhci_hcd 0000:00:1d.0: PCI INT A -> Link[LNKH] -> GSI 7 (level, low) -> IRQ 7
[    0.997020] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    0.997023] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    0.997050] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 6
[    0.997076] uhci_hcd 0000:00:1d.0: irq 7, io base 0x00001860
[    0.997150] usb usb6: configuration #1 chosen from 1 choice
[    0.997174] hub 6-0:1.0: USB hub found
[    0.997180] hub 6-0:1.0: 2 ports detected
[    0.997225] uhci_hcd 0000:00:1d.1: PCI INT B -> Link[LNKD] -> GSI 11 (level, low) -> IRQ 11
[    0.997231] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    0.997235] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    0.997261] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 7
[    0.997288] uhci_hcd 0000:00:1d.1: irq 11, io base 0x00001880
[    0.997362] usb usb7: configuration #1 chosen from 1 choice
[    0.997385] hub 7-0:1.0: USB hub found
[    0.997393] hub 7-0:1.0: 2 ports detected
[    0.997582] ACPI: PCI Interrupt Link [LNKC] enabled at IRQ 10
[    0.997584] PCI: setting IRQ 10 as level-triggered
[    0.997590] uhci_hcd 0000:00:1d.2: PCI INT C -> Link[LNKC] -> GSI 10 (level, low) -> IRQ 10
[    0.997596] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    0.997600] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    0.997631] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 8
[    0.997659] uhci_hcd 0000:00:1d.2: irq 10, io base 0x000018a0
[    0.997732] usb usb8: configuration #1 chosen from 1 choice
[    0.997756] hub 8-0:1.0: USB hub found
[    0.997762] hub 8-0:1.0: 2 ports detected
[    0.997851] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    1.006795] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.006800] serio: i8042 AUX port at 0x60,0x64 irq 12
[    1.006853] mice: PS/2 mouse device common for all mice
[    1.006971] rtc_cmos 00:05: RTC can wake from S4
[    1.007000] rtc_cmos 00:05: rtc core: registered rtc_cmos as rtc0
[    1.007029] rtc0: alarms up to one month, y3k, 242 bytes nvram, hpet irqs
[    1.007115] device-mapper: uevent: version 1.0.3
[    1.007202] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: dm-devel@redhat.com
[    1.007287] device-mapper: multipath: version 1.1.0 loaded
[    1.007289] device-mapper: multipath round-robin: version 1.0.0 loaded
[    1.007395] EISA: Probing bus 0 at eisa.0
[    1.007401] Cannot allocate resource for EISA slot 1
[    1.007403] Cannot allocate resource for EISA slot 2
[    1.007405] Cannot allocate resource for EISA slot 3
[    1.007407] Cannot allocate resource for EISA slot 4
[    1.007409] Cannot allocate resource for EISA slot 5
[    1.007424] EISA: Detected 0 cards.
[    1.007604] cpuidle: using governor ladder
[    1.007714] cpuidle: using governor menu
[    1.008189] TCP cubic registered
[    1.008329] NET: Registered protocol family 10
[    1.008761] lo: Disabled Privacy Extensions
[    1.009096] NET: Registered protocol family 17
[    1.009111] Bluetooth: L2CAP ver 2.13
[    1.009113] Bluetooth: L2CAP socket layer initialized
[    1.009115] Bluetooth: SCO (Voice Link) ver 0.6
[    1.009117] Bluetooth: SCO socket layer initialized
[    1.009159] Bluetooth: RFCOMM TTY layer initialized
[    1.009162] Bluetooth: RFCOMM socket layer initialized
[    1.009164] Bluetooth: RFCOMM ver 1.11
[    1.013763] Using IPI No-Shortcut mode
[    1.013820] PM: Resume from disk failed.
[    1.013831] registered taskstats version 1
[    1.013944]   Magic number: 14:86:85
[    1.014052] rtc_cmos 00:05: setting system clock to 2010-02-12 16:04:04 UTC (1265990644)
[    1.014055] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.014057] EDD information not available.
[    1.014721] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input5
[    1.284146] ata5: SATA link down (SStatus 0 SControl 300)
[    1.284181] ata6: SATA link down (SStatus 0 SControl 300)
[    1.400119] usb 1-6: new high speed USB device using ehci_hcd and address 3
[    1.440091] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    1.448069] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    1.462929] ata2.00: ATAPI: TSSTcorp DVD+/-RW TS-T633A, DW10, max UDMA/100, ATAPI AN
[    1.462954] ata2.00: applying bridge limits
[    1.477639] ata2.00: configured for UDMA/100
[    1.489656] ata1.00: ATA-8: WDC WD3200BEVT-75ZCT2, 11.01A11, max UDMA/133
[    1.489661] ata1.00: 625142448 sectors, multi 16: LBA48 NCQ (depth 31/32)
[    1.491867] ata1.00: configured for UDMA/133
[    1.492048] scsi 0:0:0:0: Direct-Access     ATA      WDC WD3200BEVT-7 11.0 PQ: 0 ANSI: 5
[    1.492166] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    1.492202] sd 0:0:0:0: [sda] 625142448 512-byte logical blocks: (320 GB/298 GiB)
[    1.492243] sd 0:0:0:0: [sda] Write Protect is off
[    1.492246] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.492267] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.492380]  sda: sda1 sda2 sda3 sda4
[    1.495419] scsi 1:0:0:0: CD-ROM            TSSTcorp DVD+-RW TS-T633A DW10 PQ: 0 ANSI: 5
[    1.500044] Clocksource tsc unstable (delta = -397695573 ns)
[    1.502367] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[    1.502372] Uniform CD-ROM driver Revision: 3.20
[    1.502485] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    1.502520] sr 1:0:0:0: Attached scsi generic sg1 type 5
[    1.507621] sd 0:0:0:0: [sda] Attached SCSI disk
[    1.507666] Freeing unused kernel memory: 540k freed
[    1.507977] Write protecting the kernel text: 4568k
[    1.508039] Write protecting the kernel read-only data: 1836k
[    1.612750] Linux agpgart interface v0.103
[    1.631799] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:01/device:02/input/input6
[    1.631836] ACPI: Video Device [M86] (multi-head: yes  rom: no  post: no)
[    1.638672] usb 1-6: configuration #1 chosen from 1 choice
[    1.657333] tg3.c:v3.99 (April 20, 2009)
[    1.657506] tg3 0000:08:00.0: PCI INT A -> Link[LNKB] -> GSI 11 (level, low) -> IRQ 11
[    1.657519] tg3 0000:08:00.0: setting latency timer to 64
[    1.664940] tg3 0000:08:00.0: PME# disabled
[    1.683977] ohci1394 0000:09:01.0: PCI INT A -> Link[LNKB] -> GSI 11 (level, low) -> IRQ 11
[    1.743072] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[11]  MMIO=[fc200000-fc2007ff]  Max Packet=[2048]  IR/IT contexts=[4/4]
[    1.752061] usb 2-3: new high speed USB device using ehci_hcd and address 2
[    1.886644] usb 2-3: configuration #1 chosen from 1 choice
[    1.893516] Initializing USB Mass Storage driver...
[    1.893628] scsi6 : SCSI emulation for USB Mass Storage devices
[    1.893709] usbcore: registered new interface driver usb-storage
[    1.893712] USB Mass Storage support registered.
[    1.893890] usb-storage: device found at 2
[    1.893892] usb-storage: waiting for device to settle before scanning
[    2.124057] usb 3-1: new full speed USB device using uhci_hcd and address 2
[    2.209666] eth0: Tigon3 [partno(BCM95784M) rev 5784100] (PCI Express) MAC address 00:22:19:fe:0e:04
[    2.209670] eth0: attached PHY is 5784 (10/100/1000Base-T Ethernet) (WireSpeed[1])
[    2.209672] eth0: RXcsums[1] LinkChgREG[0] MIirq[0] ASF[0] TSOcap[1]
[    2.209675] eth0: dma_rwctrl[76180000] dma_mask[64-bit]
[    2.298411] usb 3-1: configuration #1 chosen from 1 choice
[    2.301446] hub 3-1:1.0: USB hub found
[    2.303344] hub 3-1:1.0: 3 ports detected
[    2.585355] usb 3-1.1: new full speed USB device using uhci_hcd and address 3
[    2.638238] xor: automatically using best checksumming function: pIII_sse
[    2.657021]    pIII_sse  :  7987.000 MB/sec
[    2.657024] xor: using function: pIII_sse (7987.000 MB/sec)
[    2.659339] device-mapper: dm-raid45: initialized v0.2594b
[    2.668817] md: linear personality registered for level -1
[    2.671122] md: multipath personality registered for level -4
[    2.673205] md: raid0 personality registered for level 0
[    2.676321] md: raid1 personality registered for level 1
[    2.678427] async_tx: api initialized (async)
[    2.745075] raid6: int32x1    796 MB/s
[    2.760110] usb 3-1.1: configuration #1 chosen from 1 choice
[    2.776886] usbcore: registered new interface driver hiddev
[    2.791237] input: HID 413c:8157 as /devices/pci0000:00/0000:00:1a.0/usb3/3-1/3-1.1/3-1.1:1.0/input/input7
[    2.791320] generic-usb 0003:413C:8157.0001: input,hidraw0: USB HID v1.11 Keyboard [HID 413c:8157] on usb-0000:00:1a.0-1.1/input0
[    2.791334] usbcore: registered new interface driver usbhid
[    2.791337] usbhid: v2.6:USB HID core driver
[    2.813073] raid6: int32x2    732 MB/s
[    2.857343] usb 3-1.2: new full speed USB device using uhci_hcd and address 4
[    2.881060] raid6: int32x4    617 MB/s
[    2.949077] raid6: int32x8    510 MB/s
[    3.017015] raid6: mmxx1     2584 MB/s
[    3.046422] usb 3-1.2: configuration #1 chosen from 1 choice
[    3.076427] input: HID 413c:8158 as /devices/pci0000:00/0000:00:1a.0/usb3/3-1/3-1.2/3-1.2:1.0/input/input8
[    3.076510] generic-usb 0003:413C:8158.0002: input,hidraw1: USB HID v1.11 Mouse [HID 413c:8158] on usb-0000:00:1a.0-1.2/input0
[    3.085024] raid6: mmxx2     2995 MB/s
[    3.153029] raid6: sse1x1    1706 MB/s
[    3.221025] raid6: sse1x2    2238 MB/s
[    3.289023] raid6: sse2x1    3122 MB/s
[    3.357009] raid6: sse2x2    3508 MB/s
[    3.357011] raid6: using algorithm sse2x2 (3508 MB/s)
[    3.361815] md: raid6 personality registered for level 6
[    3.361817] md: raid5 personality registered for level 5
[    3.361819] md: raid4 personality registered for level 4
[    3.368471] md: raid10 personality registered for level 10
[    3.609998] PM: Starting manual resume from disk
[    3.610002] PM: Resume from partition 8:2
[    3.610004] PM: Checking hibernation image.
[    3.610197] PM: Resume from disk failed.
[    3.614200] EXT4-fs (sda1): INFO: recovery required on readonly filesystem
[    3.614204] EXT4-fs (sda1): write access will be enabled during recovery
[    3.645149] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[354fc000066e0d58]
[    3.646042] EXT4-fs (sda1): barriers enabled
[    5.090062] kjournald2 starting: pid 473, dev sda1:8, commit interval 5 seconds
[    5.090084] EXT4-fs (sda1): delayed allocation enabled
[    5.090087] EXT4-fs: file extents enabled
[    5.091196] EXT4-fs: mballoc enabled
[    5.091209] EXT4-fs (sda1): orphan cleanup on readonly fs
[    5.091216] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 80423
[    5.091291] EXT4-fs (sda1): 1 orphan inode deleted
[    5.091294] EXT4-fs (sda1): recovery complete
[    5.578266] EXT4-fs (sda1): mounted filesystem with ordered data mode
[    6.335175] type=1505 audit(1265990649.817:2): operation="profile_load" pid=493 name=/usr/share/gdm/guest-session/Xsession
[    6.350894] type=1505 audit(1265990649.833:3): operation="profile_load" pid=494 name=/sbin/dhclient3
[    6.351581] type=1505 audit(1265990649.833:4): operation="profile_load" pid=494 name=/usr/lib/NetworkManager/nm-dhcp-client.action
[    6.351957] type=1505 audit(1265990649.833:5): operation="profile_load" pid=494 name=/usr/lib/connman/scripts/dhclient-script
[    6.400223] type=1505 audit(1265990649.885:6): operation="profile_load" pid=495 name=/usr/bin/evince
[    6.411337] type=1505 audit(1265990649.894:7): operation="profile_load" pid=495 name=/usr/bin/evince-previewer
[    6.418262] type=1505 audit(1265990649.902:8): operation="profile_load" pid=495 name=/usr/bin/evince-thumbnailer
[    6.440156] type=1505 audit(1265990649.923:9): operation="profile_load" pid=497 name=/usr/lib/cups/backend/cups-pdf
[    6.440960] type=1505 audit(1265990649.923:10): operation="profile_load" pid=497 name=/usr/sbin/cupsd
[    6.443557] type=1505 audit(1265990649.926:11): operation="profile_load" pid=498 name=/usr/sbin/mysqld
[    6.892347] usb-storage: device scan complete
[    6.892942] scsi 6:0:0:0: Direct-Access     Kingston DataTraveler 2.0 1.00 PQ: 0 ANSI: 2
[    6.893442] sd 6:0:0:0: Attached scsi generic sg2 type 0
[    6.894153] sd 6:0:0:0: [sdb] 7888896 512-byte logical blocks: (4.03 GB/3.76 GiB)
[    6.894653] sd 6:0:0:0: [sdb] Write Protect is off
[    6.894658] sd 6:0:0:0: [sdb] Mode Sense: 23 00 00 00
[    6.894661] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[    6.896914] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[    6.896919]  sdb: sdb1
[    6.898775] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[    6.898777] sd 6:0:0:0: [sdb] Attached SCSI removable disk
[    7.497707] EXT4-fs (sda1): warning: maximal mount count reached, running e2fsck is recommended
[    7.524212] EXT4-fs (sda1): internal journal on sda1:8
[    7.760376] Adding 6265340k swap on /dev/sda2.  Priority:-1 extents:1 across:6265340k 
[   10.292059] udev: starting version 147
[   11.398356] usb 3-1.3: new full speed USB device using uhci_hcd and address 5
[   11.474129] lp: driver loaded but no devices found
[   11.517727] ricoh-mmc: Ricoh MMC Controller disabling driver
[   11.517730] ricoh-mmc: Copyright(c) Philip Langdale
[   11.517758] ricoh-mmc: Ricoh MMC controller found at 0000:09:01.2 [1180:0843] (rev 12)
[   11.517777] ricoh-mmc: Controller is now disabled.
[   11.547081] dcdbas dcdbas: Dell Systems Management Base Driver (version 5.6.0-3.2)
[   11.591488] usb 3-1.3: configuration #1 chosen from 1 choice
[   11.600068] cfg80211: Calling CRDA to update world regulatory domain
[   11.620960] sdhci: Secure Digital Host Controller Interface driver
[   11.620963] sdhci: Copyright(c) Pierre Ossman
[   11.696619] sdhci-pci 0000:09:01.1: SDHCI controller found [1180:0822] (rev 22)
[   11.696641] sdhci-pci 0000:09:01.1: PCI INT B -> Link[LNKC] -> GSI 10 (level, low) -> IRQ 10
[   11.698697] Registered led device: mmc0::
[   11.699725] mmc0: SDHCI controller on PCI [0000:09:01.1] using DMA
[   11.771599] input: Dell WMI hotkeys as /devices/virtual/input/input9
[   12.118257] Bluetooth: Generic Bluetooth USB driver ver 0.5
[   12.118363] usbcore: registered new interface driver btusb
[   12.122525] ip_tables: (C) 2000-2006 Netfilter Core Team
[   12.362876] Linux video capture interface: v2.00
[   12.408033] Synaptics Touchpad, model: 1, fw: 7.2, id: 0x1c0b1, caps: 0xd04731/0xa40000
[   12.445851] cfg80211: World regulatory domain updated:
[   12.445854] 	(start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   12.445857] 	(2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   12.445859] 	(2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   12.445862] 	(2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   12.445864] 	(5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   12.445866] 	(5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   12.458521] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input10
[   12.513884] iwlagn: Intel(R) Wireless WiFi Link AGN driver for Linux, 1.3.27k
[   12.513887] iwlagn: Copyright(c) 2003-2009 Intel Corporation
[   12.513960] iwlagn 0000:04:00.0: PCI INT A -> Link[LNKB] -> GSI 11 (level, low) -> IRQ 11
[   12.513970] iwlagn 0000:04:00.0: setting latency timer to 64
[   12.514000] iwlagn 0000:04:00.0: Detected Intel Wireless WiFi Link 5100AGN REV=0x54
[   12.523022] uvcvideo: Found UVC 1.00 device Laptop_Integrated_Webcam_2M (0c45:63ea)
[   12.527662] input: Laptop_Integrated_Webcam_2M as /devices/pci0000:00/0000:00:1a.7/usb1/1-6/1-6:1.0/input/input11
[   12.527712] usbcore: registered new interface driver uvcvideo
[   12.527715] USB Video Class driver (v0.1.0)
[   12.573469] iwlagn 0000:04:00.0: Tunable channels: 13 802.11bg, 24 802.11a channels
[   12.573535]   alloc irq_desc for 30 on node -1
[   12.573537]   alloc kstat_irqs on node -1
[   12.573557] iwlagn 0000:04:00.0: irq 30 for MSI/MSI-X
[   13.294928] phy0: Selected rate control algorithm 'iwl-agn-rs'
[   13.533865] ACPI: PCI Interrupt Link [LNKG] enabled at IRQ 10
[   13.533870] HDA Intel 0000:00:1b.0: PCI INT A -> Link[LNKG] -> GSI 10 (level, low) -> IRQ 10
[   13.533899] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   13.664198] input: HDA Digital PCBeep as /devices/pci0000:00/0000:00:1b.0/input/input12
[   13.674172] input: HDA Intel Mic at Ext Left Jack as /devices/pci0000:00/0000:00:1b.0/sound/card0/input13
[   13.674248] input: HDA Intel HP Out at Ext Left Jack as /devices/pci0000:00/0000:00:1b.0/sound/card0/input14
[   13.674301] input: HDA Intel HP Out at Ext Left Jack as /devices/pci0000:00/0000:00:1b.0/sound/card0/input15
[   13.674921] HDA Intel 0000:01:00.1: PCI INT B -> Link[LNKB] -> GSI 11 (level, low) -> IRQ 11
[   13.674965] HDA Intel 0000:01:00.1: setting latency timer to 64
[   13.753720] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   13.753723] Bluetooth: BNEP filters: protocol multicast
[   13.919019] Bridge firewalling registered
[   14.372288] iwlagn 0000:04:00.0: firmware: requesting iwlwifi-5000-2.ucode
[   14.732127] iwlagn 0000:04:00.0: loaded firmware version 8.24.2.12
[   14.873480] Registered led device: iwl-phy0::radio
[   14.873511] Registered led device: iwl-phy0::assoc
[   14.873530] Registered led device: iwl-phy0::RX
[   14.873550] Registered led device: iwl-phy0::TX
[   14.897640] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   14.898990] tg3 0000:08:00.0: PME# disabled
[   14.899335]   alloc irq_desc for 31 on node -1
[   14.899337]   alloc kstat_irqs on node -1
[   14.899359] tg3 0000:08:00.0: irq 31 for MSI/MSI-X
[   15.046807] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   15.545132] __ratelimit: 6 callbacks suppressed
[   15.545135] type=1505 audit(1265970859.030:14): operation="profile_replace" pid=1241 name=/usr/share/gdm/guest-session/Xsession
[   15.546974] type=1505 audit(1265970859.030:15): operation="profile_replace" pid=1287 name=/sbin/dhclient3
[   15.547666] type=1505 audit(1265970859.030:16): operation="profile_replace" pid=1287 name=/usr/lib/NetworkManager/nm-dhcp-client.action
[   15.548084] type=1505 audit(1265970859.033:17): operation="profile_replace" pid=1287 name=/usr/lib/connman/scripts/dhclient-script
[   15.551832] type=1505 audit(1265970859.033:18): operation="profile_replace" pid=1288 name=/usr/bin/evince
[   15.563503] type=1505 audit(1265970859.045:19): operation="profile_replace" pid=1288 name=/usr/bin/evince-previewer
[   15.570035] type=1505 audit(1265970859.053:20): operation="profile_replace" pid=1288 name=/usr/bin/evince-thumbnailer
[   15.579072] type=1505 audit(1265970859.061:21): operation="profile_replace" pid=1291 name=/usr/lib/cups/backend/cups-pdf
[   15.579879] type=1505 audit(1265970859.061:22): operation="profile_replace" pid=1291 name=/usr/sbin/cupsd
[   15.582236] type=1505 audit(1265970859.065:23): operation="profile_replace" pid=1292 name=/usr/sbin/mysqld
[   15.824646] cfg80211: Found new beacon on frequency: 2472 MHz (Ch 13) on phy0
[   21.093427] __ratelimit: 18 callbacks suppressed
[   21.093431] type=1503 audit(1265970864.577:30): operation="open" pid=1677 parent=1676 profile="/usr/sbin/mysqld" requested_mask="r::" denied_mask="r::" fsuid=0 ouid=0 name="/sys/devices/system/cpu/"
[   21.141427] type=1503 audit(1265970864.625:31): operation="open" pid=1688 parent=1687 profile="/usr/sbin/mysqld" requested_mask="r::" denied_mask="r::" fsuid=0 ouid=0 name="/sys/devices/system/cpu/"
[   25.061442] input: Mouseemu virtual keyboard as /devices/virtual/input/input16
[   25.061576] input: Mouseemu virtual mouse as /devices/virtual/input/input17
[   27.056728] ppdev: user-space parallel port driver
[   40.283753] Bluetooth: HIDP (Human Interface Emulation) ver 1.2
[   50.600468] wlan0: direct probe to AP 00:0f:b5:d2:86:fa try 1
[   50.796053] wlan0: direct probe to AP 00:0f:b5:d2:86:fa try 2
[   50.800253] wlan0 direct probe responded
[   50.800256] wlan0: authenticate with AP 00:0f:b5:d2:86:fa
[   50.802113] wlan0: authenticated
[   50.802118] wlan0: associate with AP 00:0f:b5:d2:86:fa
[   50.804533] wlan0: RX AssocResp from 00:0f:b5:d2:86:fa (capab=0x421 status=0 aid=1)
[   50.804536] wlan0: associated
[   50.825266] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   50.845366] cfg80211: Calling CRDA for country: KR
[   50.847410] cfg80211: Received country IE:
[   50.847413] cfg80211: Regulatory domain: KR
[   50.847415] 	(start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   50.847417] 	(2402000 KHz - 2494000 KHz @ 40000 KHz), (10000 mBi, 10000 mBm)
[   50.847419] cfg80211: CRDA thinks this should applied:
[   50.847421] cfg80211: Regulatory domain: KR
[   50.847422] 	(start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   50.847424] 	(2402000 KHz - 2482000 KHz @ 20000 KHz), (N/A, 2000 mBm)
[   50.847427] 	(5170000 KHz - 5250000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   50.847429] 	(5250000 KHz - 5330000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   50.847432] 	(5490000 KHz - 5630000 KHz @ 20000 KHz), (300 mBi, 3000 mBm)
[   50.847434] 	(5735000 KHz - 5815000 KHz @ 20000 KHz), (300 mBi, 3000 mBm)
[   50.847436] cfg80211: We intersect both of these and get:
[   50.847437] cfg80211: Regulatory domain: 98
[   50.847439] 	(start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   50.847441] 	(2402000 KHz - 2482000 KHz @ 20000 KHz), (N/A, 2000 mBm)
[   50.847445] cfg80211: Leaving channel 5180 MHz intact on phy0 - no rule found in band on Country IE
[   50.847447] cfg80211: Leaving channel 5200 MHz intact on phy0 - no rule found in band on Country IE
[   50.847449] cfg80211: Leaving channel 5220 MHz intact on phy0 - no rule found in band on Country IE
[   50.847452] cfg80211: Leaving channel 5240 MHz intact on phy0 - no rule found in band on Country IE
[   50.847454] cfg80211: Leaving channel 5260 MHz intact on phy0 - no rule found in band on Country IE
[   50.847456] cfg80211: Leaving channel 5280 MHz intact on phy0 - no rule found in band on Country IE
[   50.847458] cfg80211: Leaving channel 5300 MHz intact on phy0 - no rule found in band on Country IE
[   50.847460] cfg80211: Leaving channel 5320 MHz intact on phy0 - no rule found in band on Country IE
[   50.847463] cfg80211: Leaving channel 5500 MHz intact on phy0 - no rule found in band on Country IE
[   50.847465] cfg80211: Leaving channel 5520 MHz intact on phy0 - no rule found in band on Country IE
[   50.847467] cfg80211: Leaving channel 5540 MHz intact on phy0 - no rule found in band on Country IE
[   50.847469] cfg80211: Leaving channel 5560 MHz intact on phy0 - no rule found in band on Country IE
[   50.847471] cfg80211: Leaving channel 5580 MHz intact on phy0 - no rule found in band on Country IE
[   50.847474] cfg80211: Leaving channel 5600 MHz intact on phy0 - no rule found in band on Country IE
[   50.847476] cfg80211: Leaving channel 5620 MHz intact on phy0 - no rule found in band on Country IE
[   50.847478] cfg80211: Leaving channel 5640 MHz intact on phy0 - no rule found in band on Country IE
[   50.847480] cfg80211: Leaving channel 5660 MHz intact on phy0 - no rule found in band on Country IE
[   50.847482] cfg80211: Leaving channel 5680 MHz intact on phy0 - no rule found in band on Country IE
[   50.847484] cfg80211: Leaving channel 5700 MHz intact on phy0 - no rule found in band on Country IE
[   50.847487] cfg80211: Leaving channel 5745 MHz intact on phy0 - no rule found in band on Country IE
[   50.847489] cfg80211: Leaving channel 5765 MHz intact on phy0 - no rule found in band on Country IE
[   50.847491] cfg80211: Leaving channel 5785 MHz intact on phy0 - no rule found in band on Country IE
[   50.847493] cfg80211: Leaving channel 5805 MHz intact on phy0 - no rule found in band on Country IE
[   50.847495] cfg80211: Leaving channel 5825 MHz intact on phy0 - no rule found in band on Country IE
[   50.847499] cfg80211: Current regulatory domain updated by AP to: KR
[   50.847501] 	(start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   50.847503] 	(2402000 KHz - 2482000 KHz @ 20000 KHz), (N/A, 2000 mBm)
[   60.924100] wlan0: no IPv6 routers present
[  128.059496] NTFS driver 2.1.29 [Flags: R/O MODULE].
[  128.099324] NTFS volume version 3.1.
[  179.164124] usb 2-1: new high speed USB device using ehci_hcd and address 3
[  179.300521] usb 2-1: configuration #1 chosen from 1 choice
[  179.302842] scsi7 : SCSI emulation for USB Mass Storage devices
[  179.303013] usb-storage: device found at 3
[  179.303016] usb-storage: waiting for device to settle before scanning
[  184.304364] usb-storage: device scan complete
[  184.305179] scsi 7:0:0:0: Direct-Access     Kingston DataTraveler 102 1.00 PQ: 0 ANSI: 2
[  184.305773] sd 7:0:0:0: Attached scsi generic sg3 type 0
[  184.308865] sd 7:0:0:0: [sdc] 15636304 512-byte logical blocks: (8.00 GB/7.45 GiB)
[  184.313589] sd 7:0:0:0: [sdc] Write Protect is off
[  184.313596] sd 7:0:0:0: [sdc] Mode Sense: 03 00 00 00
[  184.313600] sd 7:0:0:0: [sdc] Assuming drive cache: write through
[  184.316590] sd 7:0:0:0: [sdc] Assuming drive cache: write through
[  184.316597]  sdc: sdc1
[  184.319551] sd 7:0:0:0: [sdc] Assuming drive cache: write through
[  184.319559] sd 7:0:0:0: [sdc] Attached SCSI removable disk
[  215.269553] nautilus[3012]: segfault at c ip 0155b597 sp bff744ec error 4 in libgdu.so.0.0.0[1550000+1c000]
[  218.105833] usb 2-3: USB disconnect, address 2
[  305.841389] FAT: Filesystem error (dev sdc1)
[  305.841396]     invalid access to FAT (entry 0x189e948d)
[  305.841402]     File system has been set read-only
[  305.841644] FAT: Filesystem error (dev sdc1)
[  305.841648]     invalid access to FAT (entry 0xdcc6bd7c)
[  305.842358] FAT: Filesystem error (dev sdc1)
[  305.842362]     invalid access to FAT (entry 0xc06bc9e1)
[  305.842671] FAT: Filesystem error (dev sdc1)
[  305.842675]     invalid access to FAT (entry 0x1014eaf4)
[  305.842848] FAT: Filesystem error (dev sdc1)
[  305.842852]     invalid access to FAT (entry 0x72751202)
[  327.199577] FAT: Filesystem error (dev sdc1)
[  327.199584]     invalid access to FAT (entry 0xc06bc9e1)
[  327.201417] FAT: Filesystem error (dev sdc1)
[  327.201422]     invalid access to FAT (entry 0x1014eaf4)
[  327.202959] FAT: Filesystem error (dev sdc1)
[  327.202965]     invalid access to FAT (entry 0x189e948d)
[  327.203115] FAT: Filesystem error (dev sdc1)
[  327.203119]     invalid access to FAT (entry 0xdcc6bd7c)
[  388.925825] FAT: Filesystem error (dev sdc1)
[  388.925830]     invalid access to FAT (entry 0xc06bc9e1)
[  388.925939] FAT: Filesystem error (dev sdc1)
[  388.925941]     invalid access to FAT (entry 0x1014eaf4)
[  388.926449] FAT: Filesystem error (dev sdc1)
[  388.926451]     invalid access to FAT (entry 0x189e948d)
[  388.926551] FAT: Filesystem error (dev sdc1)
[  388.926554]     invalid access to FAT (entry 0xdcc6bd7c)
[  391.681301] FAT: Filesystem error (dev sdc1)
[  391.681305]     invalid access to FAT (entry 0x189e948d)
[  391.691238] FAT: Filesystem error (dev sdc1)
[  391.691243]     invalid access to FAT (entry 0xdcc6bd7c)
[  409.792384] FAT: Filesystem error (dev sdc1)
[  409.792390]     invalid access to FAT (entry 0x189e948d)
[  409.792409] FAT: Filesystem error (dev sdc1)
[  409.792412]     invalid access to FAT (entry 0xdcc6bd7c)
[  409.792428] FAT: Filesystem error (dev sdc1)
[  409.792431]     invalid access to FAT (entry 0xf707f15c)
[  409.792513] FAT: Filesystem error (dev sdc1)
[  409.792516]     invalid access to FAT (entry 0xd05854c2)
[  409.792538] FAT: Filesystem error (dev sdc1)
[  409.792541]     invalid access to FAT (entry 0xe89423c5)
[  409.792562] FAT: Filesystem error (dev sdc1)
[  409.792565]     invalid access to FAT (entry 0x401220f9)
[  409.792623] FAT: Filesystem error (dev sdc1)
[  409.792626]     invalid access to FAT (entry 0xe5db25ac)
[  409.792731] FAT: Filesystem error (dev sdc1)
[  409.792734]     invalid access to FAT (entry 0xd1fffa1e)
[  409.792760] FAT: Filesystem error (dev sdc1)
[  409.792762]     invalid access to FAT (entry 0xe40f8f7a)
[  409.792811] FAT: Filesystem error (dev sdc1)
[  409.792814]     invalid access to FAT (entry 0xaaae1680)
[  409.792841] FAT: Filesystem error (dev sdc1)
[  409.792844]     invalid access to FAT (entry 0x5fddd642)
[  409.792873] FAT: Filesystem error (dev sdc1)
[  409.792876]     invalid access to FAT (entry 0xf806a90c)
[  409.792906] FAT: Filesystem error (dev sdc1)
[  409.792909]     invalid access to FAT (entry 0x579eef0d)
[  409.792939] FAT: Filesystem error (dev sdc1)
[  409.792942]     invalid access to FAT (entry 0x5f070aad)
[  409.793119] FAT: Filesystem error (dev sdc1)
[  409.793122]     invalid access to FAT (entry 0x03cf9808)
[  409.793186] FAT: Filesystem error (dev sdc1)
[  409.793190]     invalid access to FAT (entry 0xde5e3fae)
[  409.793257] FAT: Filesystem error (dev sdc1)
[  409.793260]     invalid access to FAT (entry 0xd56a3bc0)
[  409.793330] FAT: Filesystem error (dev sdc1)
[  409.793333]     invalid access to FAT (entry 0x45b9610e)
[  409.793372] FAT: Filesystem error (dev sdc1)
[  409.793374]     invalid access to FAT (entry 0xd60651c8)
[  409.793414] FAT: Filesystem error (dev sdc1)
[  409.793416]     invalid access to FAT (entry 0x7adcfb16)
[  409.793493] FAT: Filesystem error (dev sdc1)
[  409.793496]     invalid access to FAT (entry 0xa604df1f)
[  409.793573] FAT: Filesystem error (dev sdc1)
[  409.793576]     invalid access to FAT (entry 0x617a5fce)
[  409.793736] FAT: Filesystem error (dev sdc1)
[  409.793739]     invalid access to FAT (entry 0xfd844a3b)
[  409.793785] FAT: Filesystem error (dev sdc1)
[  409.793788]     invalid access to FAT (entry 0x64d6dbd4)
[  409.793835] FAT: Filesystem error (dev sdc1)
[  409.793838]     invalid access to FAT (entry 0xdb009124)
[  409.793930] FAT: Filesystem error (dev sdc1)
[  409.793933]     invalid access to FAT (entry 0x369a29d5)
[  409.793982] FAT: Filesystem error (dev sdc1)
[  409.793985]     invalid access to FAT (entry 0xbee2b796)
[  409.794034] FAT: Filesystem error (dev sdc1)
[  409.794037]     invalid access to FAT (entry 0xdd8c549d)
[  409.794279] FAT: Filesystem error (dev sdc1)
[  409.794282]     invalid access to FAT (entry 0x56765c6d)
[  409.794336] FAT: Filesystem error (dev sdc1)
[  409.794339]     invalid access to FAT (entry 0xfb9d4014)
[  409.794395] FAT: Filesystem error (dev sdc1)
[  409.794398]     invalid access to FAT (entry 0x30300000)
[  409.794506] FAT: Filesystem error (dev sdc1)
[  409.794509]     invalid access to FAT (entry 0xbe4be154)
[  409.794566] FAT: Filesystem error (dev sdc1)
[  409.794568]     invalid access to FAT (entry 0xcf68831a)
[  409.794928] FAT: Filesystem error (dev sdc1)
[  409.794931]     invalid access to FAT (entry 0x161fe0bc)
[  409.987972] FAT: Filesystem error (dev sdc1)
[  409.987978]     invalid access to FAT (entry 0x189e948d)
[  409.987997] FAT: Filesystem error (dev sdc1)
[  409.988000]     invalid access to FAT (entry 0xdcc6bd7c)
[  409.988017] FAT: Filesystem error (dev sdc1)
[  409.988020]     invalid access to FAT (entry 0xf707f15c)
[  409.988057] FAT: Filesystem error (dev sdc1)
[  409.988060]     invalid access to FAT (entry 0xd05854c2)
[  409.988081] FAT: Filesystem error (dev sdc1)
[  409.988084]     invalid access to FAT (entry 0xe89423c5)
[  409.988105] FAT: Filesystem error (dev sdc1)
[  409.988108]     invalid access to FAT (entry 0x401220f9)
[  409.988139] FAT: Filesystem error (dev sdc1)
[  409.988142]     invalid access to FAT (entry 0xe5db25ac)
[  409.988171] FAT: Filesystem error (dev sdc1)
[  409.988174]     invalid access to FAT (entry 0xd1fffa1e)
[  409.988199] FAT: Filesystem error (dev sdc1)
[  409.988202]     invalid access to FAT (entry 0xe40f8f7a)
[  409.988232] FAT: Filesystem error (dev sdc1)
[  409.988235]     invalid access to FAT (entry 0xaaae1680)
[  409.988263] FAT: Filesystem error (dev sdc1)
[  409.988265]     invalid access to FAT (entry 0x5fddd642)
[  409.988295] FAT: Filesystem error (dev sdc1)
[  409.988297]     invalid access to FAT (entry 0xf806a90c)
[  409.988327] FAT: Filesystem error (dev sdc1)
[  409.988330]     invalid access to FAT (entry 0x579eef0d)
[  409.988360] FAT: Filesystem error (dev sdc1)
[  409.988363]     invalid access to FAT (entry 0x5f070aad)
[  409.988406] FAT: Filesystem error (dev sdc1)
[  409.988409]     invalid access to FAT (entry 0x03cf9808)
[  409.988449] FAT: Filesystem error (dev sdc1)
[  409.988452]     invalid access to FAT (entry 0xde5e3fae)
[  409.988492] FAT: Filesystem error (dev sdc1)
[  409.988495]     invalid access to FAT (entry 0xd56a3bc0)
[  409.988536] FAT: Filesystem error (dev sdc1)
[  409.988539]     invalid access to FAT (entry 0x45b9610e)
[  409.988577] FAT: Filesystem error (dev sdc1)
[  409.988580]     invalid access to FAT (entry 0xd60651c8)
[  409.988620] FAT: Filesystem error (dev sdc1)
[  409.988623]     invalid access to FAT (entry 0x7adcfb16)
[  409.988667] FAT: Filesystem error (dev sdc1)
[  409.988670]     invalid access to FAT (entry 0xa604df1f)
[  409.988715] FAT: Filesystem error (dev sdc1)
[  409.988718]     invalid access to FAT (entry 0x617a5fce)
[  409.988774] FAT: Filesystem error (dev sdc1)
[  409.988777]     invalid access to FAT (entry 0xfd844a3b)
[  409.988823] FAT: Filesystem error (dev sdc1)
[  409.988826]     invalid access to FAT (entry 0x64d6dbd4)
[  409.988873] FAT: Filesystem error (dev sdc1)
[  409.988875]     invalid access to FAT (entry 0xdb009124)
[  409.988928] FAT: Filesystem error (dev sdc1)
[  409.988930]     invalid access to FAT (entry 0x369a29d5)
[  409.988979] FAT: Filesystem error (dev sdc1)
[  409.988982]     invalid access to FAT (entry 0xbee2b796)
[  409.989061] FAT: Filesystem error (dev sdc1)
[  409.989064]     invalid access to FAT (entry 0xdd8c549d)
[  409.989131] FAT: Filesystem error (dev sdc1)
[  409.989134]     invalid access to FAT (entry 0x56765c6d)
[  409.989189] FAT: Filesystem error (dev sdc1)
[  409.989192]     invalid access to FAT (entry 0xfb9d4014)
[  409.989248] FAT: Filesystem error (dev sdc1)
[  409.989251]     invalid access to FAT (entry 0x30300000)
[  409.989312] FAT: Filesystem error (dev sdc1)
[  409.989314]     invalid access to FAT (entry 0xbe4be154)
[  409.989371] FAT: Filesystem error (dev sdc1)
[  409.989373]     invalid access to FAT (entry 0xcf68831a)
[  409.989451] FAT: Filesystem error (dev sdc1)
[  409.989454]     invalid access to FAT (entry 0x161fe0bc)
[  410.038371] FAT: Filesystem error (dev sdc1)
[  410.038375]     invalid access to FAT (entry 0xbe4be154)
[  410.038540] FAT: Filesystem error (dev sdc1)
[  410.038542]     invalid access to FAT (entry 0xdb009124)
[  410.038562] FAT: Filesystem error (dev sdc1)
[  410.038564]     invalid access to FAT (entry 0xdcc6bd7c)
[  410.038600] FAT: Filesystem error (dev sdc1)
[  410.038602]     invalid access to FAT (entry 0x03cf9808)
[  410.038614] FAT: Filesystem error (dev sdc1)
[  410.038615]     invalid access to FAT (entry 0x189e948d)
[  410.038646] FAT: Filesystem error (dev sdc1)
[  410.038648]     invalid access to FAT (entry 0xbee2b796)
[  410.038678] FAT: Filesystem error (dev sdc1)
[  410.038680]     invalid access to FAT (entry 0xd60651c8)
[  410.038742] FAT: Filesystem error (dev sdc1)
[  410.038744]     invalid access to FAT (entry 0xf707f15c)
[  410.038845] FAT: Filesystem error (dev sdc1)
[  410.038847]     invalid access to FAT (entry 0xd1fffa1e)
[  410.038873] FAT: Filesystem error (dev sdc1)
[  410.038874]     invalid access to FAT (entry 0xf806a90c)
[  410.038910] FAT: Filesystem error (dev sdc1)
[  410.038912]     invalid access to FAT (entry 0x30300000)
[  410.038946] FAT: Filesystem error (dev sdc1)
[  410.038948]     invalid access to FAT (entry 0xfb9d4014)
[  410.038977] FAT: Filesystem error (dev sdc1)
[  410.038979]     invalid access to FAT (entry 0x64d6dbd4)
[  410.039067] FAT: Filesystem error (dev sdc1)
[  410.039069]     invalid access to FAT (entry 0xfd844a3b)
[  410.039110] FAT: Filesystem error (dev sdc1)
[  410.039111]     invalid access to FAT (entry 0x617a5fce)
[  410.039185] FAT: Filesystem error (dev sdc1)
[  410.039187]     invalid access to FAT (entry 0xd05854c2)
[  410.039215] FAT: Filesystem error (dev sdc1)
[  410.039216]     invalid access to FAT (entry 0xaaae1680)
[  410.039297] FAT: Filesystem error (dev sdc1)
[  410.039299]     invalid access to FAT (entry 0x56765c6d)
[  410.039324] FAT: Filesystem error (dev sdc1)
[  410.039325]     invalid access to FAT (entry 0x401220f9)
[  410.039368] FAT: Filesystem error (dev sdc1)
[  410.039370]     invalid access to FAT (entry 0x161fe0bc)
[  410.039445] FAT: Filesystem error (dev sdc1)
[  410.039447]     invalid access to FAT (entry 0xe40f8f7a)
[  410.039471] FAT: Filesystem error (dev sdc1)
[  410.039473]     invalid access to FAT (entry 0xde5e3fae)
[  410.039509] FAT: Filesystem error (dev sdc1)
[  410.039511]     invalid access to FAT (entry 0xdd8c549d)
[  410.039551] FAT: Filesystem error (dev sdc1)
[  410.039553]     invalid access to FAT (entry 0xcf68831a)
[  410.039578] FAT: Filesystem error (dev sdc1)
[  410.039579]     invalid access to FAT (entry 0x45b9610e)
[  410.039653] FAT: Filesystem error (dev sdc1)
[  410.039655]     invalid access to FAT (entry 0x5fddd642)
[  410.039678] FAT: Filesystem error (dev sdc1)
[  410.039680]     invalid access to FAT (entry 0xe89423c5)
[  410.039763] FAT: Filesystem error (dev sdc1)
[  410.039765]     invalid access to FAT (entry 0x5f070aad)
[  410.039819] FAT: Filesystem error (dev sdc1)
[  410.039821]     invalid access to FAT (entry 0x7adcfb16)
[  410.039838] FAT: Filesystem error (dev sdc1)
[  410.039840]     invalid access to FAT (entry 0xe5db25ac)
[  410.039880] FAT: Filesystem error (dev sdc1)
[  410.039881]     invalid access to FAT (entry 0x369a29d5)
[  410.039906] FAT: Filesystem error (dev sdc1)
[  410.039908]     invalid access to FAT (entry 0xd56a3bc0)
[  421.331336] FAT: Filesystem error (dev sdc1)
[  421.331341]     invalid access to FAT (entry 0xdb009124)
[  421.331509] FAT: Filesystem error (dev sdc1)
[  421.331513]     invalid access to FAT (entry 0xd60651c8)
[  421.331603] FAT: Filesystem error (dev sdc1)
[  421.331606]     invalid access to FAT (entry 0xf806a90c)
[  421.331724] FAT: Filesystem error (dev sdc1)
[  421.331727]     invalid access to FAT (entry 0xaaae1680)
[  421.331777] FAT: Filesystem error (dev sdc1)
[  421.331780]     invalid access to FAT (entry 0x401220f9)
[  421.331888] FAT: Filesystem error (dev sdc1)
[  421.331892]     invalid access to FAT (entry 0xdd8c549d)
[  421.331973] FAT: Filesystem error (dev sdc1)
[  421.331976]     invalid access to FAT (entry 0xe89423c5)
[  421.332223] FAT: Filesystem error (dev sdc1)
[  421.332227]     invalid access to FAT (entry 0x03cf9808)
[  421.332285] FAT: Filesystem error (dev sdc1)
[  421.332289]     invalid access to FAT (entry 0x579eef0d)
[  421.332402] FAT: Filesystem error (dev sdc1)
[  421.332407]     invalid access to FAT (entry 0x30300000)
[  421.332535] FAT: Filesystem error (dev sdc1)
[  421.332539]     invalid access to FAT (entry 0xa604df1f)
[  421.332723] FAT: Filesystem error (dev sdc1)
[  421.332727]     invalid access to FAT (entry 0x7adcfb16)
[  421.332804] FAT: Filesystem error (dev sdc1)
[  421.332808]     invalid access to FAT (entry 0x369a29d5)
[  421.332911] FAT: Filesystem error (dev sdc1)
[  421.332915]     invalid access to FAT (entry 0xdcc6bd7c)
[  421.332958] FAT: Filesystem error (dev sdc1)
[  421.332962]     invalid access to FAT (entry 0x189e948d)
[  421.333100] FAT: Filesystem error (dev sdc1)
[  421.333104]     invalid access to FAT (entry 0xfb9d4014)
[  421.333206] FAT: Filesystem error (dev sdc1)
[  421.333210]     invalid access to FAT (entry 0x617a5fce)
[  421.333258] FAT: Filesystem error (dev sdc1)
[  421.333262]     invalid access to FAT (entry 0xd05854c2)
[  421.333342] FAT: Filesystem error (dev sdc1)
[  421.333346]     invalid access to FAT (entry 0x56765c6d)
[  421.333435] FAT: Filesystem error (dev sdc1)
[  421.333439]     invalid access to FAT (entry 0x161fe0bc)
[  421.333491] FAT: Filesystem error (dev sdc1)
[  421.333495]     invalid access to FAT (entry 0xe40f8f7a)
[  421.333579] FAT: Filesystem error (dev sdc1)
[  421.333583]     invalid access to FAT (entry 0xcf68831a)
[  421.333638] FAT: Filesystem error (dev sdc1)
[  421.333642]     invalid access to FAT (entry 0x5fddd642)
[  421.333699] FAT: Filesystem error (dev sdc1)
[  421.333703]     invalid access to FAT (entry 0x5f070aad)
[  421.333755] FAT: Filesystem error (dev sdc1)
[  421.333759]     invalid access to FAT (entry 0xe5db25ac)
[  421.333823] FAT: Filesystem error (dev sdc1)
[  421.333827]     invalid access to FAT (entry 0xd56a3bc0)
[  421.333911] FAT: Filesystem error (dev sdc1)
[  421.333915]     invalid access to FAT (entry 0xbe4be154)
[  421.334052] FAT: Filesystem error (dev sdc1)
[  421.334056]     invalid access to FAT (entry 0xbee2b796)
[  421.334101] FAT: Filesystem error (dev sdc1)
[  421.334105]     invalid access to FAT (entry 0xf707f15c)
[  421.334157] FAT: Filesystem error (dev sdc1)
[  421.334161]     invalid access to FAT (entry 0xd1fffa1e)
[  421.334235] FAT: Filesystem error (dev sdc1)
[  421.334239]     invalid access to FAT (entry 0x64d6dbd4)
[  421.334312] FAT: Filesystem error (dev sdc1)
[  421.334316]     invalid access to FAT (entry 0xfd844a3b)
[  421.334495] FAT: Filesystem error (dev sdc1)
[  421.334498]     invalid access to FAT (entry 0xde5e3fae)
[  421.334566] FAT: Filesystem error (dev sdc1)
[  421.334570]     invalid access to FAT (entry 0x45b9610e)
[  429.449013] hda-intel: azx_get_response timeout, switching to polling mode: last cmd=0x00ef0700
[  433.356780] FAT: Filesystem error (dev sdc1)
[  433.356786]     invalid access to FAT (entry 0xdb009124)
[  433.356954] FAT: Filesystem error (dev sdc1)
[  433.356957]     invalid access to FAT (entry 0xd60651c8)
[  433.357070] FAT: Filesystem error (dev sdc1)
[  433.357074]     invalid access to FAT (entry 0xf806a90c)
[  433.357192] FAT: Filesystem error (dev sdc1)
[  433.357195]     invalid access to FAT (entry 0xaaae1680)
[  433.357245] FAT: Filesystem error (dev sdc1)
[  433.357249]     invalid access to FAT (entry 0x401220f9)
[  433.357357] FAT: Filesystem error (dev sdc1)
[  433.357360]     invalid access to FAT (entry 0xdd8c549d)
[  433.357441] FAT: Filesystem error (dev sdc1)
[  433.357445]     invalid access to FAT (entry 0xe89423c5)
[  433.357649] FAT: Filesystem error (dev sdc1)
[  433.357652]     invalid access to FAT (entry 0x03cf9808)
[  433.357709] FAT: Filesystem error (dev sdc1)
[  433.357712]     invalid access to FAT (entry 0x579eef0d)
[  433.357826] FAT: Filesystem error (dev sdc1)
[  433.357829]     invalid access to FAT (entry 0x30300000)
[  433.357957] FAT: Filesystem error (dev sdc1)
[  433.357960]     invalid access to FAT (entry 0xa604df1f)
[  433.358143] FAT: Filesystem error (dev sdc1)
[  433.358146]     invalid access to FAT (entry 0x7adcfb16)
[  433.358222] FAT: Filesystem error (dev sdc1)
[  433.358225]     invalid access to FAT (entry 0x369a29d5)
[  433.358328] FAT: Filesystem error (dev sdc1)
[  433.358331]     invalid access to FAT (entry 0xdcc6bd7c)
[  433.358373] FAT: Filesystem error (dev sdc1)
[  433.358376]     invalid access to FAT (entry 0x189e948d)
[  433.358491] FAT: Filesystem error (dev sdc1)
[  433.358495]     invalid access to FAT (entry 0xfb9d4014)
[  433.358595] FAT: Filesystem error (dev sdc1)
[  433.358599]     invalid access to FAT (entry 0x617a5fce)
[  433.358646] FAT: Filesystem error (dev sdc1)
[  433.358649]     invalid access to FAT (entry 0xd05854c2)
[  433.358729] FAT: Filesystem error (dev sdc1)
[  433.358732]     invalid access to FAT (entry 0x56765c6d)
[  433.358819] FAT: Filesystem error (dev sdc1)
[  433.358822]     invalid access to FAT (entry 0x161fe0bc)
[  433.358874] FAT: Filesystem error (dev sdc1)
[  433.358877]     invalid access to FAT (entry 0xe40f8f7a)
[  433.358959] FAT: Filesystem error (dev sdc1)
[  433.358962]     invalid access to FAT (entry 0xcf68831a)
[  433.359017] FAT: Filesystem error (dev sdc1)
[  433.359020]     invalid access to FAT (entry 0x5fddd642)
[  433.359077] FAT: Filesystem error (dev sdc1)
[  433.359080]     invalid access to FAT (entry 0x5f070aad)
[  433.359130] FAT: Filesystem error (dev sdc1)
[  433.359134]     invalid access to FAT (entry 0xe5db25ac)
[  433.359197] FAT: Filesystem error (dev sdc1)
[  433.359200]     invalid access to FAT (entry 0xd56a3bc0)
[  433.359284] FAT: Filesystem error (dev sdc1)
[  433.359287]     invalid access to FAT (entry 0xbe4be154)
[  433.359422] FAT: Filesystem error (dev sdc1)
[  433.359425]     invalid access to FAT (entry 0xbee2b796)
[  433.359469] FAT: Filesystem error (dev sdc1)
[  433.359472]     invalid access to FAT (entry 0xf707f15c)
[  433.359524] FAT: Filesystem error (dev sdc1)
[  433.359527]     invalid access to FAT (entry 0xd1fffa1e)
[  433.359599] FAT: Filesystem error (dev sdc1)
[  433.359602]     invalid access to FAT (entry 0x64d6dbd4)
[  433.359675] FAT: Filesystem error (dev sdc1)
[  433.359678]     invalid access to FAT (entry 0xfd844a3b)
[  433.359832] FAT: Filesystem error (dev sdc1)
[  433.359836]     invalid access to FAT (entry 0xde5e3fae)
[  433.359901] FAT: Filesystem error (dev sdc1)
[  433.359904]     invalid access to FAT (entry 0x45b9610e)
[  439.930142] FAT: Filesystem error (dev sdc1)
[  439.930147]     invalid access to FAT (entry 0xc06bc9e1)
[  439.930289] FAT: Filesystem error (dev sdc1)
[  439.930291]     invalid access to FAT (entry 0x1014eaf4)
[  448.228360] FAT: Filesystem error (dev sdc1)
[  448.228363]     invalid access to FAT (entry 0x189e948d)
[  448.228375] FAT: Filesystem error (dev sdc1)
[  448.228376]     invalid access to FAT (entry 0x189e948d)
[  448.228406] FAT: Filesystem error (dev sdc1)
[  448.228407]     invalid access to FAT (entry 0xdcc6bd7c)
[  448.228416] FAT: Filesystem error (dev sdc1)
[  448.228417]     invalid access to FAT (entry 0xdcc6bd7c)
[  448.228445] FAT: Filesystem error (dev sdc1)
[  448.228446]     invalid access to FAT (entry 0xf707f15c)
[  448.228455] FAT: Filesystem error (dev sdc1)
[  448.228457]     invalid access to FAT (entry 0xf707f15c)
[  448.228579] FAT: Filesystem error (dev sdc1)
[  448.228581]     invalid access to FAT (entry 0xd05854c2)
[  448.228593] FAT: Filesystem error (dev sdc1)
[  448.228595]     invalid access to FAT (entry 0xd05854c2)
[  448.228625] FAT: Filesystem error (dev sdc1)
[  448.228627]     invalid access to FAT (entry 0xe89423c5)
[  448.228638] FAT: Filesystem error (dev sdc1)
[  448.228640]     invalid access to FAT (entry 0xe89423c5)
[  448.228669] FAT: Filesystem error (dev sdc1)
[  448.228671]     invalid access to FAT (entry 0x401220f9)
[  448.228683] FAT: Filesystem error (dev sdc1)
[  448.228685]     invalid access to FAT (entry 0x401220f9)
[  448.228760] FAT: Filesystem error (dev sdc1)
[  448.228762]     invalid access to FAT (entry 0xe5db25ac)
[  448.228775] FAT: Filesystem error (dev sdc1)
[  448.228776]     invalid access to FAT (entry 0xe5db25ac)
[  448.228828] FAT: Filesystem error (dev sdc1)
[  448.228830]     invalid access to FAT (entry 0xd1fffa1e)
[  448.228844] FAT: Filesystem error (dev sdc1)
[  448.228846]     invalid access to FAT (entry 0xd1fffa1e)
[  448.228877] FAT: Filesystem error (dev sdc1)
[  448.228879]     invalid access to FAT (entry 0xe40f8f7a)
[  448.228893] FAT: Filesystem error (dev sdc1)
[  448.228895]     invalid access to FAT (entry 0xe40f8f7a)
[  448.228949] FAT: Filesystem error (dev sdc1)
[  448.228951]     invalid access to FAT (entry 0xaaae1680)
[  448.228966] FAT: Filesystem error (dev sdc1)
[  448.228968]     invalid access to FAT (entry 0xaaae1680)
[  448.229018] FAT: Filesystem error (dev sdc1)
[  448.229019]     invalid access to FAT (entry 0x5fddd642)
[  448.229035] FAT: Filesystem error (dev sdc1)
[  448.229037]     invalid access to FAT (entry 0x5fddd642)
[  448.229072] FAT: Filesystem error (dev sdc1)
[  448.229074]     invalid access to FAT (entry 0xf806a90c)
[  448.229090] FAT: Filesystem error (dev sdc1)
[  448.229092]     invalid access to FAT (entry 0xf806a90c)
[  448.229126] FAT: Filesystem error (dev sdc1)
[  448.229128]     invalid access to FAT (entry 0x579eef0d)
[  448.229144] FAT: Filesystem error (dev sdc1)
[  448.229146]     invalid access to FAT (entry 0x579eef0d)
[  448.229180] FAT: Filesystem error (dev sdc1)
[  448.229182]     invalid access to FAT (entry 0x5f070aad)
[  448.229199] FAT: Filesystem error (dev sdc1)
[  448.229201]     invalid access to FAT (entry 0x5f070aad)
[  448.229302] FAT: Filesystem error (dev sdc1)
[  448.229304]     invalid access to FAT (entry 0x03cf9808)
[  448.229323] FAT: Filesystem error (dev sdc1)
[  448.229325]     invalid access to FAT (entry 0x03cf9808)
[  448.229385] FAT: Filesystem error (dev sdc1)
[  448.229387]     invalid access to FAT (entry 0xde5e3fae)
[  448.229407] FAT: Filesystem error (dev sdc1)
[  448.229409]     invalid access to FAT (entry 0xde5e3fae)
[  448.229470] FAT: Filesystem error (dev sdc1)
[  448.229471]     invalid access to FAT (entry 0xd56a3bc0)
[  448.229492] FAT: Filesystem error (dev sdc1)
[  448.229494]     invalid access to FAT (entry 0xd56a3bc0)
[  448.229555] FAT: Filesystem error (dev sdc1)
[  448.229557]     invalid access to FAT (entry 0x45b9610e)
[  448.229578] FAT: Filesystem error (dev sdc1)
[  448.229580]     invalid access to FAT (entry 0x45b9610e)
[  448.229620] FAT: Filesystem error (dev sdc1)
[  448.229622]     invalid access to FAT (entry 0xd60651c8)
[  448.229644] FAT: Filesystem error (dev sdc1)
[  448.229645]     invalid access to FAT (entry 0xd60651c8)
[  448.229685] FAT: Filesystem error (dev sdc1)
[  448.229687]     invalid access to FAT (entry 0x7adcfb16)
[  448.229709] FAT: Filesystem error (dev sdc1)
[  448.229711]     invalid access to FAT (entry 0x7adcfb16)
[  448.229774] FAT: Filesystem error (dev sdc1)
[  448.229776]     invalid access to FAT (entry 0xa604df1f)
[  448.229799] FAT: Filesystem error (dev sdc1)
[  448.229801]     invalid access to FAT (entry 0xa604df1f)
[  448.229865] FAT: Filesystem error (dev sdc1)
[  448.229866]     invalid access to FAT (entry 0x617a5fce)
[  448.229890] FAT: Filesystem error (dev sdc1)
[  448.229892]     invalid access to FAT (entry 0x617a5fce)
[  448.230005] FAT: Filesystem error (dev sdc1)
[  448.230006]     invalid access to FAT (entry 0xfd844a3b)
[  448.230033] FAT: Filesystem error (dev sdc1)
[  448.230034]     invalid access to FAT (entry 0xfd844a3b)
[  448.230079] FAT: Filesystem error (dev sdc1)
[  448.230081]     invalid access to FAT (entry 0x64d6dbd4)
[  448.230107] FAT: Filesystem error (dev sdc1)
[  448.230109]     invalid access to FAT (entry 0x64d6dbd4)
[  448.230153] FAT: Filesystem error (dev sdc1)
[  448.230154]     invalid access to FAT (entry 0xdb009124)
[  448.230181] FAT: Filesystem error (dev sdc1)
[  448.230182]     invalid access to FAT (entry 0xdb009124)
[  448.230249] FAT: Filesystem error (dev sdc1)
[  448.230251]     invalid access to FAT (entry 0x369a29d5)
[  448.230279] FAT: Filesystem error (dev sdc1)
[  448.230280]     invalid access to FAT (entry 0x369a29d5)
[  448.230325] FAT: Filesystem error (dev sdc1)
[  448.230327]     invalid access to FAT (entry 0xbee2b796)
[  448.230355] FAT: Filesystem error (dev sdc1)
[  448.230356]     invalid access to FAT (entry 0xbee2b796)
[  448.230402] FAT: Filesystem error (dev sdc1)
[  448.230404]     invalid access to FAT (entry 0xdd8c549d)
[  448.230432] FAT: Filesystem error (dev sdc1)
[  448.230434]     invalid access to FAT (entry 0xdd8c549d)
[  448.230575] FAT: Filesystem error (dev sdc1)
[  448.230576]     invalid access to FAT (entry 0x56765c6d)
[  448.230607] FAT: Filesystem error (dev sdc1)
[  448.230609]     invalid access to FAT (entry 0x56765c6d)
[  448.230657] FAT: Filesystem error (dev sdc1)
[  448.230659]     invalid access to FAT (entry 0xfb9d4014)
[  448.230690] FAT: Filesystem error (dev sdc1)
[  448.230691]     invalid access to FAT (entry 0xfb9d4014)
[  448.230741] FAT: Filesystem error (dev sdc1)
[  448.230743]     invalid access to FAT (entry 0x30300000)
[  448.230774] FAT: Filesystem error (dev sdc1)
[  448.230776]     invalid access to FAT (entry 0x30300000)
[  448.230848] FAT: Filesystem error (dev sdc1)
[  448.230850]     invalid access to FAT (entry 0xbe4be154)
[  448.230882] FAT: Filesystem error (dev sdc1)
[  448.230884]     invalid access to FAT (entry 0xbe4be154)
[  448.230933] FAT: Filesystem error (dev sdc1)
[  448.230935]     invalid access to FAT (entry 0xcf68831a)
[  448.230967] FAT: Filesystem error (dev sdc1)
[  448.230969]     invalid access to FAT (entry 0xcf68831a)
[  448.231133] FAT: Filesystem error (dev sdc1)
[  448.231135]     invalid access to FAT (entry 0x161fe0bc)
[  448.231170] FAT: Filesystem error (dev sdc1)
[  448.231172]     invalid access to FAT (entry 0x161fe0bc)
[  451.252885] FAT: Filesystem error (dev sdc1)
[  451.252889]     invalid access to FAT (entry 0xdb009124)
[  451.252991] FAT: Filesystem error (dev sdc1)
[  451.252993]     invalid access to FAT (entry 0xd60651c8)
[  451.253063] FAT: Filesystem error (dev sdc1)
[  451.253065]     invalid access to FAT (entry 0xf806a90c)
[  451.253136] FAT: Filesystem error (dev sdc1)
[  451.253138]     invalid access to FAT (entry 0xaaae1680)
[  451.253168] FAT: Filesystem error (dev sdc1)
[  451.253170]     invalid access to FAT (entry 0x401220f9)
[  451.253235] FAT: Filesystem error (dev sdc1)
[  451.253237]     invalid access to FAT (entry 0xdd8c549d)
[  451.253286] FAT: Filesystem error (dev sdc1)
[  451.253288]     invalid access to FAT (entry 0xe89423c5)
[  451.253414] FAT: Filesystem error (dev sdc1)
[  451.253416]     invalid access to FAT (entry 0x03cf9808)
[  451.253450] FAT: Filesystem error (dev sdc1)
[  451.253452]     invalid access to FAT (entry 0x579eef0d)
[  451.253519] FAT: Filesystem error (dev sdc1)
[  451.253521]     invalid access to FAT (entry 0x30300000)
[  451.253598] FAT: Filesystem error (dev sdc1)
[  451.253600]     invalid access to FAT (entry 0xa604df1f)
[  451.253712] FAT: Filesystem error (dev sdc1)
[  451.253714]     invalid access to FAT (entry 0x7adcfb16)
[  451.253759] FAT: Filesystem error (dev sdc1)
[  451.253761]     invalid access to FAT (entry 0x369a29d5)
[  451.253824] FAT: Filesystem error (dev sdc1)
[  451.253826]     invalid access to FAT (entry 0xdcc6bd7c)
[  451.253852] FAT: Filesystem error (dev sdc1)
[  451.253853]     invalid access to FAT (entry 0x189e948d)
[  451.253936] FAT: Filesystem error (dev sdc1)
[  451.253938]     invalid access to FAT (entry 0xfb9d4014)
[  451.253998] FAT: Filesystem error (dev sdc1)
[  451.254000]     invalid access to FAT (entry 0x617a5fce)
[  451.254029] FAT: Filesystem error (dev sdc1)
[  451.254031]     invalid access to FAT (entry 0xd05854c2)
[  451.254078] FAT: Filesystem error (dev sdc1)
[  451.254080]     invalid access to FAT (entry 0x56765c6d)
[  451.254131] FAT: Filesystem error (dev sdc1)
[  451.254133]     invalid access to FAT (entry 0x161fe0bc)
[  451.254164] FAT: Filesystem error (dev sdc1)
[  451.254166]     invalid access to FAT (entry 0xe40f8f7a)
[  451.254214] FAT: Filesystem error (dev sdc1)
[  451.254216]     invalid access to FAT (entry 0xcf68831a)
[  451.254249] FAT: Filesystem error (dev sdc1)
[  451.254251]     invalid access to FAT (entry 0x5fddd642)
[  451.254285] FAT: Filesystem error (dev sdc1)
[  451.254287]     invalid access to FAT (entry 0x5f070aad)
[  451.254317] FAT: Filesystem error (dev sdc1)
[  451.254319]     invalid access to FAT (entry 0xe5db25ac)
[  451.254357] FAT: Filesystem error (dev sdc1)
[  451.254359]     invalid access to FAT (entry 0xd56a3bc0)
[  451.254408] FAT: Filesystem error (dev sdc1)
[  451.254410]     invalid access to FAT (entry 0xbe4be154)
[  451.254491] FAT: Filesystem error (dev sdc1)
[  451.254493]     invalid access to FAT (entry 0xbee2b796)
[  451.254520] FAT: Filesystem error (dev sdc1)
[  451.254522]     invalid access to FAT (entry 0xf707f15c)
[  451.254553] FAT: Filesystem error (dev sdc1)
[  451.254555]     invalid access to FAT (entry 0xd1fffa1e)
[  451.254598] FAT: Filesystem error (dev sdc1)
[  451.254600]     invalid access to FAT (entry 0x64d6dbd4)
[  451.254643] FAT: Filesystem error (dev sdc1)
[  451.254644]     invalid access to FAT (entry 0xfd844a3b)
[  451.254754] FAT: Filesystem error (dev sdc1)
[  451.254756]     invalid access to FAT (entry 0xde5e3fae)
[  451.254795] FAT: Filesystem error (dev sdc1)
[  451.254797]     invalid access to FAT (entry 0x45b9610e)
[  468.557410] FAT: Filesystem error (dev sdc1)
[  468.557414]     invalid access to FAT (entry 0x189e948d)
[  468.557688] FAT: Filesystem error (dev sdc1)
[  468.557690]     invalid access to FAT (entry 0xdcc6bd7c)
[  468.558188] FAT: Filesystem error (dev sdc1)
[  468.558191]     invalid access to FAT (entry 0xc06bc9e1)
[  468.558344] FAT: Filesystem error (dev sdc1)
[  468.558346]     invalid access to FAT (entry 0x1014eaf4)
[  504.446123] usb 2-1: USB disconnect, address 3
[  531.600158] usb 2-2: new high speed USB device using ehci_hcd and address 4
[  531.734170] usb 2-2: configuration #1 chosen from 1 choice
[  531.734576] scsi8 : SCSI emulation for USB Mass Storage devices
[  531.734873] usb-storage: device found at 4
[  531.734877] usb-storage: waiting for device to settle before scanning
[  536.732502] usb-storage: device scan complete
[  536.733368] scsi 8:0:0:0: Direct-Access     WD       3200BEV External 1.75 PQ: 0 ANSI: 4
[  536.734234] sd 8:0:0:0: Attached scsi generic sg2 type 0
[  536.740591] sd 8:0:0:0: [sdb] 625142448 512-byte logical blocks: (320 GB/298 GiB)
[  536.741079] sd 8:0:0:0: [sdb] Write Protect is off
[  536.741085] sd 8:0:0:0: [sdb] Mode Sense: 23 00 00 00
[  536.741089] sd 8:0:0:0: [sdb] Assuming drive cache: write through
[  536.742324] sd 8:0:0:0: [sdb] Assuming drive cache: write through
[  536.742331]  sdb: sdb1
[  536.785083] sd 8:0:0:0: [sdb] Assuming drive cache: write through
[  536.785091] sd 8:0:0:0: [sdb] Attached SCSI disk
[  537.428099] NTFS volume version 3.1.
[  665.400160] usb 2-3: new high speed USB device using ehci_hcd and address 5
[  665.535433] usb 2-3: configuration #1 chosen from 1 choice
[  665.542142] scsi9 : SCSI emulation for USB Mass Storage devices
[  665.542848] usb-storage: device found at 5
[  665.542852] usb-storage: waiting for device to settle before scanning
[  665.721339] usb 2-3: USB disconnect, address 5
[  666.772158] usb 2-3: new high speed USB device using ehci_hcd and address 6
[  666.907564] usb 2-3: configuration #1 chosen from 1 choice
[  666.912124] scsi10 : SCSI emulation for USB Mass Storage devices
[  666.912310] usb-storage: device found at 6
[  666.912313] usb-storage: waiting for device to settle before scanning
[  671.912523] usb-storage: device scan complete
[  671.913368] scsi 10:0:0:0: Direct-Access     JetFlash Transcend 4GB    8.07 PQ: 0 ANSI: 2
[  671.914154] sd 10:0:0:0: Attached scsi generic sg3 type 0
[  671.921475] sd 10:0:0:0: [sdc] 7843840 512-byte logical blocks: (4.01 GB/3.74 GiB)
[  671.921969] sd 10:0:0:0: [sdc] Write Protect is off
[  671.921974] sd 10:0:0:0: [sdc] Mode Sense: 03 00 00 00
[  671.921978] sd 10:0:0:0: [sdc] Assuming drive cache: write through
[  671.925132] sd 10:0:0:0: [sdc] Assuming drive cache: write through
[  671.925139]  sdc: sdc1
[  672.148165] sd 10:0:0:0: [sdc] Assuming drive cache: write through
[  672.148173] sd 10:0:0:0: [sdc] Attached SCSI removable disk
[  797.604149] usb 2-1: new high speed USB device using ehci_hcd and address 7
[  797.737498] usb 2-1: configuration #1 chosen from 1 choice
[  797.737823] scsi11 : SCSI emulation for USB Mass Storage devices
[  797.738060] usb-storage: device found at 7
[  797.738063] usb-storage: waiting for device to settle before scanning
[  802.736425] usb-storage: device scan complete
[  802.737395] scsi 11:0:0:0: Direct-Access     SanDisk  Cruzer           7.01 PQ: 0 ANSI: 0 CCS
[  802.738157] sd 11:0:0:0: Attached scsi generic sg4 type 0
[  802.743464] sd 11:0:0:0: [sdd] 3940479 512-byte logical blocks: (2.01 GB/1.87 GiB)
[  802.744236] sd 11:0:0:0: [sdd] Write Protect is off
[  802.744242] sd 11:0:0:0: [sdd] Mode Sense: 45 00 00 08
[  802.744246] sd 11:0:0:0: [sdd] Assuming drive cache: write through
[  802.746357] sd 11:0:0:0: [sdd] Assuming drive cache: write through
[  802.746364]  sdd: sdd1
[  802.752869] sd 11:0:0:0: [sdd] Assuming drive cache: write through
[  802.752877] sd 11:0:0:0: [sdd] Attached SCSI removable disk
[  905.265739] usb 2-1: USB disconnect, address 7
[ 1048.772145] usb 2-1: new high speed USB device using ehci_hcd and address 8
[ 1048.907988] usb 2-1: configuration #1 chosen from 1 choice
[ 1048.909162] scsi12 : SCSI emulation for USB Mass Storage devices
[ 1048.909400] usb-storage: device found at 8
[ 1048.909403] usb-storage: waiting for device to settle before scanning
[ 1053.912018] usb-storage: device scan complete
[ 1053.960144] scsi 12:0:0:0: Direct-Access     Kingston DataTraveler 2.0 PMAP PQ: 0 ANSI: 0 CCS
[ 1053.961710] sd 12:0:0:0: Attached scsi generic sg4 type 0
[ 1055.036533] sd 12:0:0:0: [sdd] 15687680 512-byte logical blocks: (8.03 GB/7.48 GiB)
[ 1055.037034] sd 12:0:0:0: [sdd] Write Protect is off
[ 1055.037039] sd 12:0:0:0: [sdd] Mode Sense: 23 00 00 00
[ 1055.037043] sd 12:0:0:0: [sdd] Assuming drive cache: write through
[ 1056.897446] sd 12:0:0:0: [sdd] Assuming drive cache: write through
[ 1056.897455]  sdd: sdd1
[ 1056.932279] sd 12:0:0:0: [sdd] Assuming drive cache: write through
[ 1056.932287] sd 12:0:0:0: [sdd] Attached SCSI removable disk
[ 1120.380937] usb 2-1: USB disconnect, address 8
[ 1142.655922] usb 2-3: USB disconnect, address 6
[ 1143.067121] usb 2-2: USB disconnect, address 4
[ 1293.804121] wlan0: no probe response from AP 00:0f:b5:d2:86:fa - disassociating
[ 1442.801490] wlan0: authenticate with AP 00:14:6c:62:c7:ff
[ 1442.803440] wlan0: authenticated
[ 1442.803447] wlan0: associate with AP 00:14:6c:62:c7:ff
[ 1442.805819] wlan0: RX AssocResp from 00:14:6c:62:c7:ff (capab=0x421 status=0 aid=1161)
[ 1442.805824] wlan0: associated
[ 1497.442745] type=1503 audit(1265972340.926:32): operation="open" pid=5934 parent=5933 profile="/usr/sbin/mysqld" requested_mask="r::" denied_mask="r::" fsuid=0 ouid=0 name="/sys/devices/system/cpu/"
[ 1497.957934] type=1503 audit(1265972341.442:33): operation="open" pid=5985 parent=5984 profile="/usr/sbin/mysqld" requested_mask="r::" denied_mask="r::" fsuid=0 ouid=0 name="/sys/devices/system/cpu/"
[ 1498.442222] type=1503 audit(1265972341.925:34): operation="open" pid=6038 parent=6037 profile="/usr/sbin/mysqld" requested_mask="r::" denied_mask="r::" fsuid=0 ouid=0 name="/sys/devices/system/cpu/"
[ 1498.666965] type=1503 audit(1265972342.149:35): operation="open" pid=6076 parent=6075 profile="/usr/sbin/mysqld" requested_mask="r::" denied_mask="r::" fsuid=0 ouid=0 name="/sys/devices/system/cpu/"
[ 1498.713607] type=1503 audit(1265972342.197:36): operation="open" pid=6091 parent=6090 profile="/usr/sbin/mysqld" requested_mask="r::" denied_mask="r::" fsuid=0 ouid=0 name="/sys/devices/system/cpu/"
[ 2029.491731] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
[ 2029.491738] Disabling lock debugging due to kernel taint
[ 2029.518845] [fglrx] Maximum main memory to use for locked dma buffers: 2873 MBytes.
[ 2029.519200] [fglrx]   vendor: 1002 device: 9553 count: 1
[ 2029.519699] [fglrx] ioport: bar 1, base 0x2000, size: 0x100
[ 2029.519716] pci 0000:01:00.0: PCI INT A -> Link[LNKA] -> GSI 5 (level, low) -> IRQ 5
[ 2029.519722] pci 0000:01:00.0: setting latency timer to 64
[ 2029.519902] [fglrx] Kernel PAT support is enabled
[ 2029.519923] [fglrx] module loaded - fglrx 8.66.10 [Sep  3 2009] with 1 minors

```

---

### Post by benmoran on 2010-02-12
There is the possibility that it really is dead. I've had one or two die on me.

---

### Post by lavinog on 2010-02-12
Your dmesg shows the following detected:
kingston 8g
wd external 320g
jetflash transend 4g
sandisk cruzer 2g

What type was not working?

---

### Post by Vishnu V on 2010-02-12
> **lavinog said:**
> Your dmesg shows the following detected:
kingston 8g
wd external 320g
jetflash transend 4g
sandisk cruzer 2g

What type was not working?

Kingston 4g is not working

---

### Post by lavinog on 2010-02-12
I would assume it is dead then.  Maybe the waranty is still good on it.

---

### Post by GeorgeVita on 2010-02-12
Hi **Vishnu V**,
have you tried other OS to format it?

Can you try Gparted booting from an OLDER Ubuntu LiveCD version (8.10 or 9.04)?

Regards,
George

---

