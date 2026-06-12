---
title: "System Crashing Frequently"
date: 2010-12-02
forum: General Help
---

### Post by Bugs318 on 2010-12-02
I am getting regular crashes, and apparently the entire system and not just X.  Sometimes the system will run for days, sometimes it will lock up a few times per day.  It crashes sometimes when asleep, when waking up from sleep, when in use, and when not in use.  The entire system becomes unresponsive to mouse or keystrokes and the screen either stays black (if I was away) or stuck on the current viewscreen (if in use).

Any ideas where to go to help/debug would be GREATLY appreciated and I thank you immensely in advance!!!

Some info:
1) Running Ubuntu 10.04 Lucid Lynx
2) Cannot ssh in - get error that there is "no route to host"
3) Cannot switch to a shell (Ctrl-Alt-F1)
4) Alt-SysRq-1 followed by Alt-SysRq-t has no effect
5) Ctrl-Alt-Del nor Ctrl-Alt-Bkspace, nor Alt-SysRq-R-E-I-S-U-B (in that order) has any effect.
6) The only way to restart is a forced power off power on.
7) I have tried with and without powernowd enabled
8) I have tried with and without screensavers enabled
9) I have run a memtest overnight (multiple times) with no errors (though I wonder if it is running properly since it won't let me Escape out of it... requiring a hard restart as it doesn't respond to any keystrokes, though the cursors at the top do keep ticking).

Relevant kern.log and entire dmesg follow (as I don't know what from dmesg is pertinent):

```
kern.log

Dec  2 09:03:31 derek-laptop kernel: [ 3406.009316] ata2.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6 frozen
Dec  2 09:03:31 derek-laptop kernel: [ 3406.009328] sr 1:0:0:0: CDB: Test Unit Ready: 00 00 00 00 00 00
Dec  2 09:03:31 derek-laptop kernel: [ 3406.009360] ata2.00: cmd a0/00:00:00:00:00/00:00:00:00:00/a0 tag 0
Dec  2 09:03:31 derek-laptop kernel: [ 3406.009363]          res 40/00:03:00:00:00/00:00:00:00:00/a0 Emask 0x4 (timeout)
Dec  2 09:03:31 derek-laptop kernel: [ 3406.009372] ata2.00: status: { DRDY }
Dec  2 09:03:36 derek-laptop kernel: [ 3411.056078] ata2: link is slow to respond, please be patient (ready=0)
Dec  2 09:03:41 derek-laptop kernel: [ 3416.040094] ata2: device not ready (errno=-16), forcing hardreset
Dec  2 09:03:41 derek-laptop kernel: [ 3416.040113] ata2: soft resetting link
Dec  2 09:03:42 derek-laptop kernel: [ 3416.300348] ata2.00: configured for UDMA/33
Dec  2 09:03:42 derek-laptop kernel: [ 3416.305894] ata2: EH complete
Dec  2 09:20:34 derek-laptop kernel: [ 4428.989191] ata2.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6 frozen
Dec  2 09:20:34 derek-laptop kernel: [ 4428.989204] sr 1:0:0:0: CDB: Test Unit Ready: 00 00 00 00 00 00
Dec  2 09:20:34 derek-laptop kernel: [ 4428.989236] ata2.00: cmd a0/00:00:00:00:00/00:00:00:00:00/a0 tag 0
Dec  2 09:20:34 derek-laptop kernel: [ 4428.989240]          res 40/00:03:00:00:00/00:00:00:00:00/a0 Emask 0x4 (timeout)
Dec  2 09:20:34 derek-laptop kernel: [ 4428.989249] ata2.00: status: { DRDY }
Dec  2 09:20:39 derek-laptop kernel: [ 4434.032848] ata2: link is slow to respond, please be patient (ready=0)
Dec  2 09:20:44 derek-laptop kernel: [ 4439.000295] ata2: device not ready (errno=-16), forcing hardreset
Dec  2 09:20:44 derek-laptop kernel: [ 4439.000314] ata2: soft resetting link
Dec  2 09:20:44 derek-laptop kernel: [ 4439.228490] ata2.00: configured for UDMA/33
Dec  2 09:20:44 derek-laptop kernel: [ 4439.237565] ata2: EH complete
Dec  2 09:59:17 derek-laptop kernel: [ 6751.988400] ata2.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6 frozen
Dec  2 09:59:17 derek-laptop kernel: [ 6751.988412] sr 1:0:0:0: CDB: Test Unit Ready: 00 00 00 00 00 00
Dec  2 09:59:17 derek-laptop kernel: [ 6751.988443] ata2.00: cmd a0/00:00:00:00:00/00:00:00:00:00/a0 tag 0
Dec  2 09:59:17 derek-laptop kernel: [ 6751.988447]          res 40/00:03:00:00:00/00:00:00:00:00/a0 Emask 0x4 (timeout)
Dec  2 09:59:17 derek-laptop kernel: [ 6751.988456] ata2.00: status: { DRDY }
Dec  2 09:59:22 derek-laptop kernel: [ 6757.033579] ata2: link is slow to respond, please be patient (ready=0)
Dec  2 09:59:27 derek-laptop kernel: [ 6762.017093] ata2: device not ready (errno=-16), forcing hardreset
Dec  2 09:59:27 derek-laptop kernel: [ 6762.017112] ata2: soft resetting link
Dec  2 09:59:27 derek-laptop kernel: [ 6762.244495] ata2.00: configured for UDMA/33
Dec  2 09:59:27 derek-laptop kernel: [ 6762.252508] ata2: EH complete
Dec  2 20:35:10 derek-laptop kernel: imklog 4.2.0, log source = /proc/kmsg started.

dmesg

[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.32-26-generic (buildd@rothera) (gcc version 4.4.3 (Ubuntu 4.4.3-4ubuntu5) ) #48-Ubuntu SMP Wed Nov 24 09:00:03 UTC 2010 (Ubuntu 2.6.32-26.48-generic 2.6.32.24+drm33.11)
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
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
[    0.000000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000005f680000 (usable)
[    0.000000]  BIOS-e820: 000000005f680000 - 000000005f700000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000005f700000 - 0000000060000000 (reserved)
[    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed00000 - 00000000fed00400 (reserved)
[    0.000000]  BIOS-e820: 00000000fed14000 - 00000000fed1a000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed1c000 - 00000000fed90000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000ff000000 - 0000000100000000 (reserved)
[    0.000000] DMI present.
[    0.000000] last_pfn = 0x5f680 max_arch_pfn = 0x100000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-CFFFF write-protect
[    0.000000]   D0000-DFFFF uncachable
[    0.000000]   E0000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000 mask FC0000000 write-back
[    0.000000]   1 base 040000000 mask FE0000000 write-back
[    0.000000]   2 base 05F700000 mask FFFF00000 uncachable
[    0.000000]   3 base 05F800000 mask FFF800000 uncachable
[    0.000000]   4 disabled
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] PAT not supported by CPU.
[    0.000000] e820 update range: 0000000000002000 - 0000000000006000 (usable) ==> (reserved)
[    0.000000] Scanning 1 areas for low memory corruption
[    0.000000] modified physical RAM map:
[    0.000000]  modified: 0000000000000000 - 0000000000002000 (usable)
[    0.000000]  modified: 0000000000002000 - 0000000000006000 (reserved)
[    0.000000]  modified: 0000000000006000 - 000000000009f800 (usable)
[    0.000000]  modified: 000000000009f800 - 00000000000a0000 (reserved)
[    0.000000]  modified: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  modified: 0000000000100000 - 000000005f680000 (usable)
[    0.000000]  modified: 000000005f680000 - 000000005f700000 (ACPI NVS)
[    0.000000]  modified: 000000005f700000 - 0000000060000000 (reserved)
[    0.000000]  modified: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  modified: 00000000fec00000 - 00000000fec10000 (reserved)
[    0.000000]  modified: 00000000fed00000 - 00000000fed00400 (reserved)
[    0.000000]  modified: 00000000fed14000 - 00000000fed1a000 (reserved)
[    0.000000]  modified: 00000000fed1c000 - 00000000fed90000 (reserved)
[    0.000000]  modified: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  modified: 00000000ff000000 - 0000000100000000 (reserved)
[    0.000000] initial memory mapped : 0 - 00c00000
[    0.000000] init_memory_mapping: 0000000000000000-00000000377fe000
[    0.000000] Using x86 segment limits to approximate NX protection
[    0.000000]  0000000000 - 0000400000 page 4k
[    0.000000]  0000400000 - 0037400000 page 2M
[    0.000000]  0037400000 - 00377fe000 page 4k
[    0.000000] kernel direct mapping tables up to 377fe000 @ 7000-c000
[    0.000000] RAMDISK: 372ec000 - 37fefeb4
[    0.000000] Allocated new RAMDISK: 008e1000 - 015e4eb4
[    0.000000] Move RAMDISK from 00000000372ec000 - 0000000037fefeb3 to 008e1000 - 015e4eb3
[    0.000000] ACPI: RSDP 000f63a0 00014 (v00 ACRSYS)
[    0.000000] ACPI: RSDT 5f685150 00058 (v01 ACRSYS ACRPRDCT 06040000  LTP 00000000)
[    0.000000] ACPI: FACP 5f68cc76 00074 (v01 Acer   Grape    06040000 LOHR 0000005A)
[    0.000000] ACPI: DSDT 5f686ebb 05DBB (v01 Acer   CALISTGA 06040000 INTL 20050228)
[    0.000000] ACPI: FACS 5f68dfc0 00040
[    0.000000] ACPI: APIC 5f68ccea 00068 (v01 Acer   Grape    06040000 LOHR 0000005A)
[    0.000000] ACPI: HPET 5f68cd52 00038 (v01 Acer   Grape    06040000 LOHR 0000005A)
[    0.000000] ACPI: MCFG 5f68cd8a 0003C (v01 Acer   Grape    06040000 LOHR 0000005A)
[    0.000000] ACPI: SLIC 5f68cdc6 00176 (v01 ACRSYS ACRPRDCT 06040000 LOHR 00000000)
[    0.000000] ACPI: DBGP 5f68cf3c 00034 (v01 Acer   Grape    06040000 LOHR 00000000)
[    0.000000] ACPI: APIC 5f68cf70 00068 (v01 PTLTD  ? APIC   06040000  LTP 00000000)
[    0.000000] ACPI: BOOT 5f68cfd8 00028 (v01 PTLTD  $SBFTBL$ 06040000  LTP 00000001)
[    0.000000] ACPI: SSDT 5f68686c 0064F (v01 SataRe  SataPri 00001000 INTL 20050228)
[    0.000000] ACPI: SSDT 5f6861da 00692 (v01 SataRe  SataSec 00001000 INTL 20050228)
[    0.000000] ACPI: SSDT 5f685734 0025F (v01  PmRef  Cpu0Tst 00003000 INTL 20050228)
[    0.000000] ACPI: SSDT 5f68568e 000A6 (v01  PmRef  Cpu1Tst 00003000 INTL 20050228)
[    0.000000] ACPI: SSDT 5f6851a8 004E6 (v01  PmRef    CpuPm 00003000 INTL 20050228)
[    0.000000] ACPI: BIOS bug: multiple APIC/MADT found, using 0
[    0.000000] ACPI: If "acpi_apic_instance=2" works better, notify [email]linux-acpi@vger.kernel.org[/email]
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] 638MB HIGHMEM available.
[    0.000000] 887MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 377fe000
[    0.000000]   low ram: 0 - 377fe000
[    0.000000]   node 0 low ram: 00000000 - 377fe000
[    0.000000]   node 0 bootmap 00008000 - 0000ef00
[    0.000000] (9 early reservations) ==> bootmem [0000000000 - 00377fe000]
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
[    0.000000]   #1 [0000001000 - 0000002000]    EX TRAMPOLINE ==> [0000001000 - 0000002000]
[    0.000000]   #2 [0000006000 - 0000007000]       TRAMPOLINE ==> [0000006000 - 0000007000]
[    0.000000]   #3 [0000100000 - 00008dced8]    TEXT DATA BSS ==> [0000100000 - 00008dced8]
[    0.000000]   #4 [000009f800 - 0000100000]    BIOS reserved ==> [000009f800 - 0000100000]
[    0.000000]   #5 [00008dd000 - 00008e00d5]              BRK ==> [00008dd000 - 00008e00d5]
[    0.000000]   #6 [0000007000 - 0000008000]          PGTABLE ==> [0000007000 - 0000008000]
[    0.000000]   #7 [00008e1000 - 00015e4eb4]      NEW RAMDISK ==> [00008e1000 - 00015e4eb4]
[    0.000000]   #8 [0000008000 - 000000f000]          BOOTMAP ==> [0000008000 - 000000f000]
[    0.000000] found SMP MP-table at [c00f6450] f6450
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000000 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x000377fe
[    0.000000]   HighMem  0x000377fe -> 0x0005f680
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[3] active PFN ranges
[    0.000000]     0: 0x00000000 -> 0x00000002
[    0.000000]     0: 0x00000006 -> 0x0000009f
[    0.000000]     0: 0x00000100 -> 0x0005f680
[    0.000000] On node 0 totalpages: 390683
[    0.000000] free_area_init_node: node 0, pgdat c079a760, node_mem_map c15e6000
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3963 pages, LIFO batch:0
[    0.000000]   Normal zone: 1744 pages used for memmap
[    0.000000]   Normal zone: 221486 pages, LIFO batch:31
[    0.000000]   HighMem zone: 1278 pages used for memmap
[    0.000000]   HighMem zone: 162180 pages, LIFO batch:31
[    0.000000] Using APIC driver default
[    0.000000] ACPI: PM-Timer IO Port: 0x1008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 1, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000
[    0.000000] SMP: Allowing 2 CPUs, 0 hotplug CPUs
[    0.000000] nr_irqs_gsi: 24
[    0.000000] PM: Registered nosave memory: 0000000000002000 - 0000000000006000
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
[    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 60000000 (gap: 60000000:80000000)
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:2 nr_node_ids:1
[    0.000000] PERCPU: Embedded 14 pages/cpu @c2400000 s36056 r0 d21288 u2097152
[    0.000000] pcpu-alloc: s36056 r0 d21288 u2097152 alloc=1*4194304
[    0.000000] pcpu-alloc: [0] 0 1 
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 387629
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.32-26-generic root=UUID=997d9b48-ea27-4049-8bd1-6d06b27fc88b ro
[    0.000000] PID hash table entries: 4096 (order: 2, 16384 bytes)
[    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] allocated 7815680 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] Initializing HighMem for node 0 (000377fe:0005f680)
[    0.000000] Memory: 1519360k/1563136k available (4682k kernel code, 42224k reserved, 2121k data, 656k init, 653832k highmem)
[    0.000000] virtual kernel memory layout:
[    0.000000]     fixmap  : 0xfff1d000 - 0xfffff000   ( 904 kB)
[    0.000000]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[    0.000000]     vmalloc : 0xf7ffe000 - 0xff7fe000   ( 120 MB)
[    0.000000]     lowmem  : 0xc0000000 - 0xf77fe000   ( 887 MB)
[    0.000000]       .init : 0xc07a5000 - 0xc0849000   ( 656 kB)
[    0.000000]       .data : 0xc0592847 - 0xc07a4e68   (2121 kB)
[    0.000000]       .text : 0xc0100000 - 0xc0592847   (4682 kB)
[    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.000000] SLUB: Genslabs=13, HWalign=64, Order=0-3, MinObjects=0, CPUs=2, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000] NR_IRQS:2304 nr_irqs:424
[    0.000000] Console: colour VGA+ 80x25
[    0.000000] console [tty0] enabled
[    0.000000] hpet clockevent registered
[    0.000000] HPET: 3 timers in total, 0 timers will be used for per-cpu timer
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 1595.813 MHz processor.
[    0.004008] Calibrating delay loop (skipped), value calculated using timer frequency.. 3191.62 BogoMIPS (lpj=6383252)
[    0.004169] Security Framework initialized
[    0.004275] AppArmor: AppArmor initialized
[    0.004349] Mount-cache hash table entries: 512
[    0.004667] Initializing cgroup subsys ns
[    0.004737] Initializing cgroup subsys cpuacct
[    0.004809] Initializing cgroup subsys memory
[    0.004886] Initializing cgroup subsys devices
[    0.004951] Initializing cgroup subsys freezer
[    0.005017] Initializing cgroup subsys net_cls
[    0.005117] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.005220] CPU: L2 cache: 1024K
[    0.005284] CPU: Physical Processor ID: 0
[    0.005348] CPU: Processor Core ID: 0
[    0.005416] mce: CPU supports 6 MCE banks
[    0.005498] CPU0: Thermal monitoring enabled (TM1)
[    0.005565] using mwait in idle threads.
[    0.005636] Performance Events: no PMU driver, software events only.
[    0.005748] Checking 'hlt' instruction... OK.
[    0.027540] ACPI: Core revision 20090903
[    0.052020] ftrace: converting mcount calls to 0f 1f 44 00 00
[    0.052097] ftrace: allocating 21794 entries in 43 pages
[    0.056112] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.056613] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.097376] CPU0: Genuine Intel(R) CPU           T2060  @ 1.60GHz stepping 0c
[    0.100001] Booting processor 1 APIC 0x1 ip 0x6000
[    0.008000] Initializing CPU#1
[    0.008000] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.008000] CPU: L2 cache: 1024K
[    0.008000] CPU: Physical Processor ID: 0
[    0.008000] CPU: Processor Core ID: 1
[    0.008000] CPU1: Thermal monitoring enabled (TM1)
[    0.184115] CPU1: Genuine Intel(R) CPU           T2060  @ 1.60GHz stepping 0c
[    0.184637] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
[    0.188041] Brought up 2 CPUs
[    0.188109] Total of 2 processors activated (6383.71 BogoMIPS).
[    0.188868] CPU0 attaching sched-domain:
[    0.188876]  domain 0: span 0-1 level MC
[    0.188883]   groups: 0 1
[    0.188898] CPU1 attaching sched-domain:
[    0.188904]  domain 0: span 0-1 level MC
[    0.188910]   groups: 1 0
[    0.189052] devtmpfs: initialized
[    0.189052] regulator: core version 0.5
[    0.189052] Time:  1:33:52  Date: 12/03/10
[    0.189052] NET: Registered protocol family 16
[    0.189052] Trying to unpack rootfs image as initramfs...
[    0.189052] EISA bus registered
[    0.189052] ACPI: bus type pci registered
[    0.189052] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 255
[    0.189099] PCI: MCFG area at e0000000 reserved in E820
[    0.189169] PCI: Using MMCONFIG for extended config space
[    0.189240] PCI: Using configuration type 1 for base access
[    0.196866] bio: create slab <bio-0> at 0
[    0.198906] ACPI: EC: Look up EC in DSDT
[    0.207883] ACPI: BIOS _OSI(Linux) query ignored
[    0.209672] ACPI: Interpreter enabled
[    0.209744] ACPI: (supports S0 S3 S4 S5)
[    0.210002] ACPI: Using IOAPIC for interrupt routing
[    0.263854] ACPI: EC: GPE = 0x19, I/O: command/status = 0x66, data = 0x62
[    0.264846] ACPI: No dock devices found.
[    0.266038] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.266300] pci 0000:00:02.0: reg 10 32bit mmio: [0xd0100000-0xd017ffff]
[    0.266314] pci 0000:00:02.0: reg 14 io port: [0x5088-0x508f]
[    0.266326] pci 0000:00:02.0: reg 18 32bit mmio pref: [0xc0000000-0xcfffffff]
[    0.266338] pci 0000:00:02.0: reg 1c 32bit mmio: [0xd0200000-0xd023ffff]
[    0.266422] pci 0000:00:02.1: reg 10 32bit mmio: [0xd0180000-0xd01fffff]
[    0.266616] pci 0000:00:1b.0: reg 10 64bit mmio: [0xd0240000-0xd0243fff]
[    0.266709] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    0.266784] pci 0000:00:1b.0: PME# disabled
[    0.266986] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    0.267061] pci 0000:00:1c.0: PME# disabled
[    0.267270] pci 0000:00:1c.1: PME# supported from D0 D3hot D3cold
[    0.267344] pci 0000:00:1c.1: PME# disabled
[    0.267553] pci 0000:00:1c.2: PME# supported from D0 D3hot D3cold
[    0.267629] pci 0000:00:1c.2: PME# disabled
[    0.267837] pci 0000:00:1c.3: PME# supported from D0 D3hot D3cold
[    0.267911] pci 0000:00:1c.3: PME# disabled
[    0.268089] pci 0000:00:1d.0: reg 20 io port: [0x50a0-0x50bf]
[    0.268189] pci 0000:00:1d.1: reg 20 io port: [0x50c0-0x50df]
[    0.268288] pci 0000:00:1d.2: reg 20 io port: [0x50e0-0x50ff]
[    0.268387] pci 0000:00:1d.3: reg 20 io port: [0x5400-0x541f]
[    0.268496] pci 0000:00:1d.7: reg 10 32bit mmio: [0xd0444000-0xd04443ff]
[    0.268591] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
[    0.268667] pci 0000:00:1d.7: PME# disabled
[    0.268982] pci 0000:00:1f.0: quirk: region 1000-107f claimed by ICH6 ACPI/GPIO/TCO
[    0.269076] pci 0000:00:1f.0: quirk: region 1180-11bf claimed by ICH6 GPIO
[    0.269153] pci 0000:00:1f.0: ICH7 LPC Generic IO decode 1 PIO at 0230 (mask 000f)
[    0.269246] pci 0000:00:1f.0: ICH7 LPC Generic IO decode 2 PIO at ff20 (mask 000f)
[    0.269442] pci 0000:00:1f.2: reg 10 io port: [0x00-0x07]
[    0.269457] pci 0000:00:1f.2: reg 14 io port: [0x00-0x03]
[    0.269472] pci 0000:00:1f.2: reg 18 io port: [0x00-0x07]
[    0.269487] pci 0000:00:1f.2: reg 1c io port: [0x00-0x03]
[    0.269502] pci 0000:00:1f.2: reg 20 io port: [0x5440-0x544f]
[    0.269559] pci 0000:00:1f.2: PME# supported from D3hot
[    0.269631] pci 0000:00:1f.2: PME# disabled
[    0.269781] pci 0000:00:1f.3: reg 20 io port: [0x5420-0x543f]
[    0.269924] pci 0000:00:1c.0: bridge io port: [0x00-0xfff]
[    0.269934] pci 0000:00:1c.0: bridge 32bit mmio: [0x000000-0x0fffff]
[    0.270314] pci 0000:06:01.0: reg 10 32bit mmio: [0xd0010000-0xd0011fff]
[    0.270403] pci 0000:06:01.0: supports D1 D2
[    0.270410] pci 0000:06:01.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.270487] pci 0000:06:01.0: PME# disabled
[    0.270619] pci 0000:06:02.0: reg 10 32bit mmio: [0xd0000000-0xd000ffff]
[    0.270776] pci 0000:06:04.0: reg 10 32bit mmio: [0x000000-0x000fff]
[    0.270815] pci 0000:06:04.0: supports D1 D2
[    0.270822] pci 0000:06:04.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.270899] pci 0000:06:04.0: PME# disabled
[    0.271027] pci 0000:06:04.1: reg 10 32bit mmio: [0xd0013000-0xd001307f]
[    0.271123] pci 0000:06:04.1: supports D1 D2
[    0.271129] pci 0000:06:04.1: PME# supported from D0 D1 D2 D3hot
[    0.271204] pci 0000:06:04.1: PME# disabled
[    0.271334] pci 0000:06:04.2: reg 10 32bit mmio: [0xd0013400-0xd00134ff]
[    0.271429] pci 0000:06:04.2: supports D1 D2
[    0.271435] pci 0000:06:04.2: PME# supported from D0 D1 D2 D3hot
[    0.271512] pci 0000:06:04.2: PME# disabled
[    0.271643] pci 0000:06:04.3: reg 10 32bit mmio: [0xd0013800-0xd001387f]
[    0.271739] pci 0000:06:04.3: supports D1 D2
[    0.271745] pci 0000:06:04.3: PME# supported from D0 D1 D2 D3hot
[    0.271820] pci 0000:06:04.3: PME# disabled
[    0.271951] pci 0000:06:04.4: reg 10 32bit mmio: [0x000000-0x0000ff]
[    0.272060] pci 0000:06:04.4: supports D1 D2
[    0.272066] pci 0000:06:04.4: PME# supported from D0 D1 D2 D3hot
[    0.272143] pci 0000:06:04.4: PME# disabled
[    0.272288] pci 0000:00:1e.0: transparent bridge
[    0.272365] pci 0000:00:1e.0: bridge 32bit mmio: [0xd0000000-0xd00fffff]
[    0.272459] pci_bus 0000:00: on NUMA node 0
[    0.272477] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.273022] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP01._PRT]
[    0.273214] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP02._PRT]
[    0.273404] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP03._PRT]
[    0.273608] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP04._PRT]
[    0.273867] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCIB._PRT]
[    0.284860] ACPI: PCI Interrupt Link [LNKA] (IRQs 1 5 *6 10 12 14 15)
[    0.285506] ACPI: PCI Interrupt Link [LNKB] (IRQs 1 5 6 *11 12 14 15)
[    0.286154] ACPI: PCI Interrupt Link [LNKC] (IRQs 1 5 6 10 12 14 15) *11
[    0.286836] ACPI: PCI Interrupt Link [LNKD] (IRQs 1 5 6 11 12 14 15) *10
[    0.287515] ACPI: PCI Interrupt Link [LNKE] (IRQs 1 5 6 10 12 14 15) *0, disabled.
[    0.288237] ACPI: PCI Interrupt Link [LNKF] (IRQs 1 5 6 11 12 14 15) *10
[    0.288921] ACPI: PCI Interrupt Link [LNKG] (IRQs 1 5 6 *10 12 14 15)
[    0.289564] ACPI: PCI Interrupt Link [LNKH] (IRQs 1 *5 6 11 12 14 15)
[    0.290239] vgaarb: device added: PCI:0000:00:02.0,decodes=io+mem,owns=io+mem,locks=none
[    0.290370] vgaarb: loaded
[    0.290720] SCSI subsystem initialized
[    0.290967] libata version 3.00 loaded.
[    0.291159] usbcore: registered new interface driver usbfs
[    0.291270] usbcore: registered new interface driver hub
[    0.292014] usbcore: registered new device driver usb
[    0.292058] ACPI: WMI: Mapper loaded
[    0.292125] PCI: Using ACPI for IRQ routing
[    0.292194] pci 0000:00:1c.0: BAR 13: can't allocate resource
[    0.292265] pci 0000:00:1c.0: BAR 14: can't allocate resource
[    0.292733] NetLabel: Initializing
[    0.292797] NetLabel:  domain hash size = 128
[    0.292863] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.292957] NetLabel:  unlabeled traffic allowed by default
[    0.293109] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[    0.293332] hpet0: 3 comparators, 64-bit 14.318180 MHz counter
[    0.300523] Switching to clocksource tsc
[    0.305146] AppArmor: AppArmor Filesystem Enabled
[    0.305246] pnp: PnP ACPI init
[    0.305343] ACPI: bus type pnp registered
[    0.329508] pnp: PnP ACPI: found 10 devices
[    0.329582] ACPI: ACPI bus type pnp unregistered
[    0.329652] PnPBIOS: Disabled by ACPI PNP
[    0.329740] system 00:01: iomem range 0xe0000000-0xefffffff has been reserved
[    0.329816] system 00:01: iomem range 0xfed14000-0xfed17fff has been reserved
[    0.329889] system 00:01: iomem range 0xfed18000-0xfed18fff has been reserved
[    0.329968] system 00:01: iomem range 0xfed19000-0xfed19fff has been reserved
[    0.330043] system 00:01: iomem range 0xfed1c000-0xfed1ffff has been reserved
[    0.330119] system 00:01: iomem range 0xfed20000-0xfed3ffff has been reserved
[    0.330206] system 00:04: iomem range 0xfed00000-0xfed003ff has been reserved
[    0.330291] system 00:06: ioport range 0x800-0x80f has been reserved
[    0.330363] system 00:06: ioport range 0x1000-0x107f has been reserved
[    0.330436] system 00:06: ioport range 0x1180-0x11bf has been reserved
[    0.330510] system 00:06: ioport range 0x1640-0x164f has been reserved
[    0.330583] system 00:06: ioport range 0xfe00-0xfefe has been reserved
[    0.330656] system 00:06: ioport range 0xff2c-0xff2f has been reserved
[    0.365852] pci 0000:00:1c.0: PCI bridge, secondary bus 0000:02
[    0.365932] pci 0000:00:1c.0:   IO window: 0x2000-0x2fff
[    0.366011] pci 0000:00:1c.0:   MEM window: 0x64000000-0x641fffff
[    0.366085] pci 0000:00:1c.0:   PREFETCH window: 0x00000064200000-0x000000643fffff
[    0.366183] pci 0000:00:1c.1: PCI bridge, secondary bus 0000:03
[    0.366256] pci 0000:00:1c.1:   IO window: 0x3000-0x3fff
[    0.366332] pci 0000:00:1c.1:   MEM window: 0x64400000-0x645fffff
[    0.366407] pci 0000:00:1c.1:   PREFETCH window: 0x00000064600000-0x000000647fffff
[    0.366505] pci 0000:00:1c.2: PCI bridge, secondary bus 0000:04
[    0.366578] pci 0000:00:1c.2:   IO window: 0x4000-0x4fff
[    0.366652] pci 0000:00:1c.2:   MEM window: 0x64800000-0x649fffff
[    0.366729] pci 0000:00:1c.2:   PREFETCH window: 0x00000064a00000-0x00000064bfffff
[    0.366829] pci 0000:00:1c.3: PCI bridge, secondary bus 0000:05
[    0.366902] pci 0000:00:1c.3:   IO window: 0x6000-0x6fff
[    0.366976] pci 0000:00:1c.3:   MEM window: 0x64c00000-0x64dfffff
[    0.367055] pci 0000:00:1c.3:   PREFETCH window: 0x00000064e00000-0x00000064ffffff
[    0.367173] pci 0000:06:04.0: CardBus bridge, secondary bus 0000:07
[    0.367245] pci 0000:06:04.0:   IO window: 0x007000-0x0070ff
[    0.367319] pci 0000:06:04.0:   IO window: 0x007400-0x0074ff
[    0.367403] pci 0000:06:04.0:   PREFETCH window: 0x60000000-0x63ffffff
[    0.367479] pci 0000:06:04.0:   MEM window: 0x68000000-0x6bffffff
[    0.367557] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:06
[    0.367629] pci 0000:00:1e.0:   IO window: 0x7000-0x7fff
[    0.367706] pci 0000:00:1e.0:   MEM window: 0xd0000000-0xd00fffff
[    0.367783] pci 0000:00:1e.0:   PREFETCH window: 0x60000000-0x63ffffff
[    0.367883] pci 0000:00:1c.0: enabling device (0100 -> 0103)
[    0.367965]   alloc irq_desc for 17 on node -1
[    0.367971]   alloc kstat_irqs on node -1
[    0.367988] pci 0000:00:1c.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    0.368069] pci 0000:00:1c.0: setting latency timer to 64
[    0.368089]   alloc irq_desc for 16 on node -1
[    0.368094]   alloc kstat_irqs on node -1
[    0.368103] pci 0000:00:1c.1: PCI INT B -> GSI 16 (level, low) -> IRQ 16
[    0.368179] pci 0000:00:1c.1: setting latency timer to 64
[    0.368199]   alloc irq_desc for 18 on node -1
[    0.368204]   alloc kstat_irqs on node -1
[    0.368213] pci 0000:00:1c.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.368292] pci 0000:00:1c.2: setting latency timer to 64
[    0.368310]   alloc irq_desc for 19 on node -1
[    0.368315]   alloc kstat_irqs on node -1
[    0.368324] pci 0000:00:1c.3: PCI INT D -> GSI 19 (level, low) -> IRQ 19
[    0.368399] pci 0000:00:1c.3: setting latency timer to 64
[    0.368412] pci 0000:00:1e.0: enabling device (0004 -> 0007)
[    0.368487] pci 0000:00:1e.0: setting latency timer to 64
[    0.368510] pci 0000:06:04.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.368591] pci_bus 0000:00: resource 0 io:  [0x00-0xffff]
[    0.368598] pci_bus 0000:00: resource 1 mem: [0x000000-0xffffffff]
[    0.368606] pci_bus 0000:02: resource 0 io:  [0x2000-0x2fff]
[    0.368613] pci_bus 0000:02: resource 1 mem: [0x64000000-0x641fffff]
[    0.368621] pci_bus 0000:02: resource 2 pref mem [0x64200000-0x643fffff]
[    0.368628] pci_bus 0000:03: resource 0 io:  [0x3000-0x3fff]
[    0.368635] pci_bus 0000:03: resource 1 mem: [0x64400000-0x645fffff]
[    0.368643] pci_bus 0000:03: resource 2 pref mem [0x64600000-0x647fffff]
[    0.368650] pci_bus 0000:04: resource 0 io:  [0x4000-0x4fff]
[    0.368658] pci_bus 0000:04: resource 1 mem: [0x64800000-0x649fffff]
[    0.368665] pci_bus 0000:04: resource 2 pref mem [0x64a00000-0x64bfffff]
[    0.368672] pci_bus 0000:05: resource 0 io:  [0x6000-0x6fff]
[    0.368680] pci_bus 0000:05: resource 1 mem: [0x64c00000-0x64dfffff]
[    0.368687] pci_bus 0000:05: resource 2 pref mem [0x64e00000-0x64ffffff]
[    0.368695] pci_bus 0000:06: resource 0 io:  [0x7000-0x7fff]
[    0.368702] pci_bus 0000:06: resource 1 mem: [0xd0000000-0xd00fffff]
[    0.368709] pci_bus 0000:06: resource 2 pref mem [0x60000000-0x63ffffff]
[    0.368716] pci_bus 0000:06: resource 3 io:  [0x00-0xffff]
[    0.368723] pci_bus 0000:06: resource 4 mem: [0x000000-0xffffffff]
[    0.368731] pci_bus 0000:07: resource 0 io:  [0x7000-0x70ff]
[    0.368738] pci_bus 0000:07: resource 1 io:  [0x7400-0x74ff]
[    0.368745] pci_bus 0000:07: resource 2 pref mem [0x60000000-0x63ffffff]
[    0.368753] pci_bus 0000:07: resource 3 mem: [0x68000000-0x6bffffff]
[    0.368840] NET: Registered protocol family 2
[    0.369138] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.369963] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.371651] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.372503] TCP: Hash tables configured (established 131072 bind 65536)
[    0.372578] TCP reno registered
[    0.372866] NET: Registered protocol family 1
[    0.372978] pci 0000:00:02.0: Boot video device
[    0.373203] Simple Boot Flag at 0x36 set to 0x1
[    0.373710] cpufreq-nforce2: No nForce2 chipset.
[    0.373839] Scanning for low memory corruption every 60 seconds
[    0.374191] audit: initializing netlink socket (disabled)
[    0.374277] type=2000 audit(1291340032.370:1): initialized
[    0.400490] highmem bounce pool size: 64 pages
[    0.400569] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    0.404962] VFS: Disk quotas dquot_6.5.2
[    0.405186] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.406844] fuse init (API version 7.13)
[    0.407143] msgmni has been set to 1692
[    0.407765] alg: No test for stdrng (krng)
[    0.407981] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.408073] io scheduler noop registered
[    0.408137] io scheduler anticipatory registered
[    0.408204] io scheduler deadline registered
[    0.408379] io scheduler cfq registered (default)
[    0.408790]   alloc irq_desc for 24 on node -1
[    0.408796]   alloc kstat_irqs on node -1
[    0.408819] pcieport 0000:00:1c.0: irq 24 for MSI/MSI-X
[    0.408839] pcieport 0000:00:1c.0: setting latency timer to 64
[    0.409122]   alloc irq_desc for 25 on node -1
[    0.409127]   alloc kstat_irqs on node -1
[    0.409144] pcieport 0000:00:1c.1: irq 25 for MSI/MSI-X
[    0.409164] pcieport 0000:00:1c.1: setting latency timer to 64
[    0.409428]   alloc irq_desc for 26 on node -1
[    0.409433]   alloc kstat_irqs on node -1
[    0.409449] pcieport 0000:00:1c.2: irq 26 for MSI/MSI-X
[    0.409468] pcieport 0000:00:1c.2: setting latency timer to 64
[    0.409736]   alloc irq_desc for 27 on node -1
[    0.409741]   alloc kstat_irqs on node -1
[    0.409757] pcieport 0000:00:1c.3: irq 27 for MSI/MSI-X
[    0.409776] pcieport 0000:00:1c.3: setting latency timer to 64
[    0.409995] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.410368] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.414437] ACPI: AC Adapter [ACAD] (on-line)
[    0.415717] input: Lid Switch as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0D:00/input/input0
[    0.415909] ACPI: Lid Switch [LID]
[    0.416096] input: Sleep Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0E:00/input/input1
[    0.416188] ACPI: Sleep Button [SLPB]
[    0.416360] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input2
[    0.416452] ACPI: Power Button [PWRB]
[    0.416676] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input3
[    0.416766] ACPI: Power Button [PWRF]
[    0.418386] ACPI: SSDT 5f685eda 00238 (v01  PmRef  Cpu0Ist 00003000 INTL 20050228)
[    0.419764] ACPI: SSDT 5f685993 004C2 (v01  PmRef  Cpu0Cst 00003001 INTL 20050228)
[    0.426103] Marking TSC unstable due to TSC halts in idle
[    0.426373] processor LNXCPU:00: registered as cooling_device0
[    0.427345] ACPI: SSDT 5f686112 000C8 (v01  PmRef  Cpu1Ist 00003000 INTL 20050228)
[    0.428419] ACPI: SSDT 5f685e55 00085 (v01  PmRef  Cpu1Cst 00003000 INTL 20050228)
[    0.430574] Switching to clocksource hpet
[    0.431276] processor LNXCPU:01: registered as cooling_device1
[    0.461690] thermal LNXTHERM:01: registered as thermal_zone0
[    0.461784] ACPI: Thermal Zone [TZ00] (45 C)
[    0.469222] thermal LNXTHERM:02: registered as thermal_zone1
[    0.469314] ACPI: Thermal Zone [TZ01] (45 C)
[    0.473615] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    0.477228] brd: module loaded
[    0.478580] loop: module loaded
[    0.478869] input: Macintosh mouse button emulation as /devices/virtual/input/input4
[    0.479196] ata_piix 0000:00:1f.2: version 2.13
[    0.479234] ata_piix 0000:00:1f.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    0.479313] ata_piix 0000:00:1f.2: MAP [ P0 P2 IDE IDE ]
[    0.479816] isapnp: Scanning for PnP cards...
[    0.660443] ata_piix 0000:00:1f.2: setting latency timer to 64
[    0.704323] scsi0 : ata_piix
[    0.704681] scsi1 : ata_piix
[    0.707499] ata1: SATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0x5440 irq 14
[    0.707578] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x5448 irq 15
[    0.708993] Fixed MDIO Bus: probed
[    0.709159] PPP generic driver version 2.4.2
[    0.709332] tun: Universal TUN/TAP device driver, 1.6
[    0.709401] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.709689] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.709807]   alloc irq_desc for 23 on node -1
[    0.709813]   alloc kstat_irqs on node -1
[    0.709828] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    0.709987] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    0.709996] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    0.710155] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 1
[    0.710278] ehci_hcd 0000:00:1d.7: using broken periodic workaround
[    0.710364] ehci_hcd 0000:00:1d.7: debug port 1
[    0.714311] ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported
[    0.714345] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xd0444000
[    0.762170] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    0.762525] usb usb1: configuration #1 chosen from 1 choice
[    0.762667] hub 1-0:1.0: USB hub found
[    0.762747] hub 1-0:1.0: 8 ports detected
[    0.762970] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.763254] uhci_hcd: USB Universal Host Controller Interface driver
[    0.763397] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    0.763480] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    0.763489] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    0.763651] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    0.763780] uhci_hcd 0000:00:1d.0: irq 23, io base 0x000050a0
[    0.764116] usb usb2: configuration #1 chosen from 1 choice
[    0.764254] hub 2-0:1.0: USB hub found
[    0.764332] hub 2-0:1.0: 2 ports detected
[    0.764510] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    0.764589] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    0.764597] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    0.764752] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 3
[    0.764895] uhci_hcd 0000:00:1d.1: irq 19, io base 0x000050c0
[    0.765175] usb usb3: configuration #1 chosen from 1 choice
[    0.765310] hub 3-0:1.0: USB hub found
[    0.765387] hub 3-0:1.0: 2 ports detected
[    0.765556] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.765638] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    0.765646] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    0.765816] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 4
[    0.765956] uhci_hcd 0000:00:1d.2: irq 18, io base 0x000050e0
[    0.766238] usb usb4: configuration #1 chosen from 1 choice
[    0.766377] hub 4-0:1.0: USB hub found
[    0.766463] hub 4-0:1.0: 2 ports detected
[    0.766635] uhci_hcd 0000:00:1d.3: PCI INT D -> GSI 16 (level, low) -> IRQ 16
[    0.766716] uhci_hcd 0000:00:1d.3: setting latency timer to 64
[    0.766725] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[    0.766868] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 5
[    0.767004] uhci_hcd 0000:00:1d.3: irq 16, io base 0x00005400
[    0.767297] usb usb5: configuration #1 chosen from 1 choice
[    0.767431] hub 5-0:1.0: USB hub found
[    0.767505] hub 5-0:1.0: 2 ports detected
[    0.767802] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:MSS0] at 0x60,0x64 irq 1,12
[    0.770259] i8042.c: Detected active multiplexing controller, rev 1.1.
[    0.770442] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.770530] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[    0.770600] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[    0.770672] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[    0.770742] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[    0.814742] mice: PS/2 mouse device common for all mice
[    0.815211] rtc_cmos 00:07: RTC can wake from S4
[    0.815373] rtc_cmos 00:07: rtc core: registered rtc_cmos as rtc0
[    0.815490] rtc0: alarms up to one month, y3k, 242 bytes nvram, hpet irqs
[    0.815902] device-mapper: uevent: version 1.0.3
[    0.818116] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: [email]dm-devel@redhat.com[/email]
[    0.859725] isapnp: No Plug & Play device found
[    0.860263] device-mapper: multipath: version 1.1.0 loaded
[    0.860337] device-mapper: multipath round-robin: version 1.0.0 loaded
[    0.860765] EISA: Probing bus 0 at eisa.0
[    0.860838] Cannot allocate resource for EISA slot 1
[    0.860906] Cannot allocate resource for EISA slot 2
[    0.860974] Cannot allocate resource for EISA slot 3
[    0.861048] Cannot allocate resource for EISA slot 4
[    0.861116] Cannot allocate resource for EISA slot 5
[    0.861185] Cannot allocate resource for EISA slot 6
[    0.861255] Cannot allocate resource for EISA slot 7
[    0.861331] EISA: Detected 0 cards.
[    0.861773] cpuidle: using governor ladder
[    0.862157] cpuidle: using governor menu
[    0.863385] TCP cubic registered
[    0.863870] NET: Registered protocol family 10
[    0.865121] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input5
[    0.865977] lo: Disabled Privacy Extensions
[    0.866929] NET: Registered protocol family 17
[    0.867910] Using IPI No-Shortcut mode
[    0.868130] PM: Resume from disk failed.
[    0.868148] registered taskstats version 1
[    0.868743]   Magic number: 6:393:558
[    0.868852] misc vga_arbiter: hash matches
[    0.868988] rtc_cmos 00:07: setting system clock to 2010-12-03 01:33:53 UTC (1291340033)
[    0.869077] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.869154] EDD information not available.
[    0.897518] ata2.00: ATAPI: TSSTcorpCD/DVDW TS-L632D, AC01, max UDMA/33
[    0.914322] ata1.00: ATA-8: ST9500420AS, 0002SDM1, max UDMA/133
[    0.914390] ata1.00: 976773168 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    0.929781] ata2.00: configured for UDMA/33
[    0.930290] ata1.00: configured for UDMA/133
[    0.930568] scsi 0:0:0:0: Direct-Access     ATA      ST9500420AS      0002 PQ: 0 ANSI: 5
[    0.930883] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    0.931058] sd 0:0:0:0: [sda] 976773168 512-byte logical blocks: (500 GB/465 GiB)
[    0.931225] sd 0:0:0:0: [sda] Write Protect is off
[    0.931287] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    0.931323] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    0.931663]  sda: sda1 sda2 <
[    0.938286] scsi 1:0:0:0: CD-ROM            TSSTcorp CD/DVDW TS-L632D AC01 PQ: 0 ANSI: 5
[    0.945079]  sda5 sda6 sda7 sda8
[    0.976230] Freeing initrd memory: 13327k freed
[    0.979693]  sda9sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[    1.000693] Uniform CD-ROM driver Revision: 3.20
[    1.000932] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    1.001037] sr 1:0:0:0: Attached scsi generic sg1 type 5
[    1.006015]  sda10 > sda3 sda4
[    1.021353] sd 0:0:0:0: [sda] Attached SCSI disk
[    1.021452] Freeing unused kernel memory: 656k freed
[    1.022070] Write protecting the kernel text: 4684k
[    1.022205] Write protecting the kernel read-only data: 1840k
[    1.034977] ACPI: EC: GPE storm detected, transactions will use polling mode
[    1.052151] ramzswap: disk size set to 767244 kB
[    1.059576] udev: starting version 151
[    1.081197] ACPI: Battery Slot [BAT1] (battery present)
[    1.104790] Adding 767240k swap on /dev/ramzswap0.  Priority:100 extents:1 across:767240k SS
[    1.173386] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/LNXVIDEO:01/input/input6
[    1.173555] ACPI: Video Device [GFX0] (multi-head: yes  rom: no  post: no)
[    1.204985] Linux agpgart interface v0.103
[    1.262123] agpgart-intel 0000:00:00.0: Intel 945GM Chipset
[    1.262680] agpgart-intel 0000:00:00.0: detected 7932K stolen memory
[    1.278912] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0xc0000000
[    1.295425] [drm] Initialized drm 1.1.0 20060810
[    1.308335]   alloc irq_desc for 21 on node -1
[    1.308339]   alloc kstat_irqs on node -1
[    1.308348] b44 0000:06:01.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[    1.308433] b44 0000:06:01.0: setting latency timer to 64
[    1.339045] i915 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.339120] i915 0000:00:02.0: setting latency timer to 64
[    1.342127] [drm] set up 7M of stolen space
[    1.369190] ssb: Sonics Silicon Backplane found on PCI device 0000:06:01.0
[    1.369624] b44.c:v2.0
[    1.390034] eth0: Broadcom 44xx/47xx 10/100BaseT Ethernet 00:16:d4:6a:92:ac
[    1.450620] [drm] initialized overlay support
[    1.812040] usb 3-1: new low speed USB device using uhci_hcd and address 2
[    1.991223] fb0: inteldrmfb frame buffer device
[    1.991292] registered panic notifier
[    1.991360] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
[    1.994064] vga16fb: initializing
[    1.994068] vga16fb: mapped to 0xc00a0000
[    1.994132] vga16fb: not registering due to another framebuffer present
[    2.036240] usb 3-1: configuration #1 chosen from 1 choice
[    2.059301] usbcore: registered new interface driver hiddev
[    2.087504] input: Microsoft Corporation Microsoft ® Laser Mouse 6000 as /devices/pci0000:00/0000:00:1d.1/usb3/3-1/3-1:1.0/input/input7
[    2.087772] generic-usb 0003:045E:00F0.0001: input,hidraw0: USB HID v1.11 Mouse [Microsoft Corporation Microsoft ® Laser Mouse 6000] on usb-0000:00:1d.1-1/input0
[    2.087810] usbcore: registered new interface driver usbhid
[    2.087943] usbhid: v2.6:USB HID core driver
[    2.159092] Console: switching to colour frame buffer device 160x50
[    2.781673] xor: automatically using best checksumming function: pIII_sse
[    2.800021]    pIII_sse  :  4057.000 MB/sec
[    2.800059] xor: using function: pIII_sse (4057.000 MB/sec)
[    2.804150] device-mapper: dm-raid45: initialized v0.2594b
[    3.000238] EXT4-fs (sda1): INFO: recovery required on readonly filesystem
[    3.000306] EXT4-fs (sda1): write access will be enabled during recovery
[    3.140925] EXT4-fs (sda1): recovery complete
[    3.149477] EXT4-fs (sda1): mounted filesystem with ordered data mode
[    4.324546] Adding 1943824k swap on /dev/sda10.  Priority:-1 extents:1 across:1943824k 
[    4.441287] Adding 1951888k swap on /dev/sda3.  Priority:-2 extents:1 across:1951888k 
[    4.600111] Adding 1951888k swap on /dev/sda4.  Priority:-3 extents:1 across:1951888k 
[    4.815556] udev: starting version 151
[    5.825036] intel_rng: FWH not detected
[    6.013864] yenta_cardbus 0000:06:04.0: CardBus bridge found [1025:0090]
[    6.013893] yenta_cardbus 0000:06:04.0: Using CSCINT to route CSC interrupts to PCI
[    6.013897] yenta_cardbus 0000:06:04.0: Routing CardBus interrupts to PCI
[    6.013905] yenta_cardbus 0000:06:04.0: TI: mfunc 0x90501212, devctl 0x44
[    6.017200] acer-wmi: Acer Laptop ACPI-WMI Extras
[    6.027661] sdhci: Secure Digital Host Controller Interface driver
[    6.027665] sdhci: Copyright(c) Pierre Ossman
[    6.049308] Registered led device: acer-wmi::mail
[    6.079973] type=1505 audit(1291340038.707:2):  operation="profile_load" pid=744 name="/sbin/dhclient3"
[    6.080773] type=1505 audit(1291340038.711:3):  operation="profile_load" pid=744 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[    6.081196] type=1505 audit(1291340038.711:4):  operation="profile_load" pid=744 name="/usr/lib/connman/scripts/dhclient-script"
[    6.081906] lp: driver loaded but no devices found
[    6.115018] cfg80211: Calling CRDA to update world regulatory domain
[    6.244854] yenta_cardbus 0000:06:04.0: ISA IRQ mask 0x0cf8, PCI irq 16
[    6.244861] yenta_cardbus 0000:06:04.0: Socket status: 30000006
[    6.244867] pci_bus 0000:06: Raising subordinate bus# of parent bus (#06) from #07 to #0a
[    6.244879] yenta_cardbus 0000:06:04.0: pcmcia: parent PCI bridge I/O window: 0x7000 - 0x7fff
[    6.244884] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x7000-0x7fff: clean.
[    6.245186] yenta_cardbus 0000:06:04.0: pcmcia: parent PCI bridge Memory window: 0xd0000000 - 0xd00fffff
[    6.245191] yenta_cardbus 0000:06:04.0: pcmcia: parent PCI bridge Memory window: 0x60000000 - 0x63ffffff
[    6.245968] sdhci-pci 0000:06:04.2: SDHCI controller found [1524:0550] (rev 1)
[    6.245988] sdhci-pci 0000:06:04.2: enabling device (0000 -> 0002)
[    6.245998] sdhci-pci 0000:06:04.2: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    6.246115] Registered led device: mmc0::
[    6.246165] mmc0: SDHCI controller on PCI [0000:06:04.2] using PIO
[    6.246182] sdhci-pci 0000:06:04.4: SDHCI controller found [1524:0551] (rev 1)
[    6.246200] sdhci-pci 0000:06:04.4: enabling device (0000 -> 0002)
[    6.246208] sdhci-pci 0000:06:04.4: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    6.246265] Registered led device: mmc1::
[    6.246302] mmc1: SDHCI controller on PCI [0000:06:04.4] using PIO
[    6.380824] ath5k 0000:06:02.0: enabling device (0000 -> 0002)
[    6.380837]   alloc irq_desc for 22 on node -1
[    6.380841]   alloc kstat_irqs on node -1
[    6.380850] ath5k 0000:06:02.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[    6.380911] ath5k 0000:06:02.0: registered as 'phy0'
[    6.710556] Synaptics Touchpad, model: 1, fw: 6.2, id: 0x1280b1, caps: 0xa04713/0x204000
[    6.742866] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio4/input/input8
[    6.836741] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x100-0x3af: clean.
[    6.839118] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x3e0-0x4ff: excluding 0x4d0-0x4d7
[    6.840188] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x820-0x8ff: clean.
[    6.840994] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xc00-0xcf7: clean.
[    6.842027] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xa00-0xaff: clean.
[    7.084900] ath: EEPROM regdomain: 0x63
[    7.084905] ath: EEPROM indicates we should expect a direct regpair map
[    7.084910] ath: Country alpha2 being used: 00
[    7.084913] ath: Regpair used: 0x63
[    7.667658] phy0: Selected rate control algorithm 'minstrel'
[    7.668634] ath5k phy0: Atheros AR2413 chip found (MAC: 0x78, PHY: 0x45)
[    7.675244] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[    7.675285] HDA Intel 0000:00:1b.0: setting latency timer to 64
[    7.793059] input: HDA Digital PCBeep as /devices/pci0000:00/0000:00:1b.0/input/input9
[    8.820116] EXT4-fs (sda7): mounted filesystem with ordered data mode
[   73.101301] kjournald starting.  Commit interval 5 seconds
[   73.102152] EXT3 FS on sda9, internal journal
[   73.102159] EXT3-fs: mounted filesystem with ordered data mode.
[   74.060897] EXT4-fs (sda5): mounted filesystem with ordered data mode
[   74.900448] EXT4-fs (sda6): mounted filesystem with ordered data mode
[   76.448407] EXT4-fs (sda8): mounted filesystem with ordered data mode
[   79.253308] type=1505 audit(1291340111.883:5):  operation="profile_load" pid=1413 name="/usr/share/gdm/guest-session/Xsession"
[   79.255721] type=1505 audit(1291340111.883:6):  operation="profile_replace" pid=1414 name="/sbin/dhclient3"
[   79.256509] type=1505 audit(1291340111.887:7):  operation="profile_replace" pid=1414 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[   79.256938] type=1505 audit(1291340111.887:8):  operation="profile_replace" pid=1414 name="/usr/lib/connman/scripts/dhclient-script"
[   79.307653] type=1505 audit(1291340111.935:9):  operation="profile_load" pid=1415 name="/usr/bin/evince"
[   79.318098] type=1505 audit(1291340111.947:10):  operation="profile_load" pid=1415 name="/usr/bin/evince-previewer"
[   79.324518] type=1505 audit(1291340111.955:11):  operation="profile_load" pid=1415 name="/usr/bin/evince-thumbnailer"
[   79.350100] type=1505 audit(1291340111.979:12):  operation="profile_load" pid=1417 name="/usr/bin/freshclam"
[   79.380983] type=1505 audit(1291340112.011:13):  operation="profile_load" pid=1418 name="/usr/lib/cups/backend/cups-pdf"
[   79.381933] type=1505 audit(1291340112.011:14):  operation="profile_load" pid=1418 name="/usr/sbin/cupsd"
[   80.009765] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   80.078764] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   81.480157] RPC: Registered udp transport module.
[   81.480162] RPC: Registered tcp transport module.
[   81.480165] RPC: Registered tcp NFSv4.1 backchannel transport module.
[   81.559888] Installing knfsd (copyright (C) 1996 [email]okir@monad.swb.de[/email]).
[   82.346831] svc: failed to register lockdv1 RPC service (errno 97).
[   82.348457] NFSD: Using /var/lib/nfs/v4recovery as the NFSv4 state recovery directory
[   82.349050] NFSD: starting 90-second grace period
```

---

### Post by Bugs318 on 2010-12-05
Does anyone have even any suggestions of things I could try to troubleshoot this?  I am at a real loss here and don't want to have to change OSes, but I am getting close (don't worry, it'd be to another Linux version, not MS or Apple products) but I'd rather resolve this?

Did anything work for you with ubuntu crashes?

Do you have troubleshooting suggestions?

Thanks for your thoughts!

---

### Post by LinuxCharms on 2010-12-05
You can try and upgrade your system as 10.10 is now out.

If that doesn't work, run your updates and restart the computer.

Tell me how all that goes.

---

### Post by Bugs318 on 2010-12-06
I'd like to stick with an LTS version (and not have to reinstall software), though if I do not find a 10.04 specific fix, I guess I could try that before switching distros.

Does anyone else have any ideas that may help me avoid that?

---

