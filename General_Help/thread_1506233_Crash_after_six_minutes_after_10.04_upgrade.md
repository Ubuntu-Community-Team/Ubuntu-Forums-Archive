---
title: "Crash after six minutes after 10.04 upgrade"
date: 2010-06-10
forum: General Help
---

### Post by faustus69 on 2010-06-10
Hi,

I have this problem since upgrade to lucid.

Every time I start my computer, from the power button, it crash after 6 minutes. It only could be recovered from the reset button, not CTRL + ALT + DEL nor REISUB.

I think it only happens if I don't touch anything in that 6 minutes.

syslog show this during crash:

```
Jun 10 07:46:21 antonio-desktop kernel: imklog 4.2.0, log source = /proc/kmsg started.
Jun 10 07:46:21 antonio-desktop rsyslogd: [origin software="rsyslogd" swVersion="4.2.0" x-pid="725" x-info="http://www.rsyslog.com"] (re)start
Jun 10 07:46:21 antonio-desktop rsyslogd: rsyslogd's groupid changed to 102
Jun 10 07:46:21 antonio-desktop rsyslogd: rsyslogd's userid changed to 101
Jun 10 07:46:21 antonio-desktop rsyslogd-2039: Could no open output file '/dev/xconsole' [try http://www.rsyslog.com/e/2039 ]
Jun 10 07:46:21 antonio-desktop kernel: [    0.000000] Initializing cgroup subsys cpuset
Jun 10 07:46:21 antonio-desktop kernel: [    0.000000] Initializing cgroup subsys cpu
Jun 10 07:46:21 antonio-desktop kernel: [    0.000000] Linux version 2.6.32-22-generic (buildd@palmer) (gcc version 4.4.3 (Ubuntu 4.4.3-4ubuntu5) ) #36-Ubuntu SMP Thu Jun 3 22:02:19 UTC 2010 (Ubuntu 2.6.32-22.36-generic 2.6.32.11+drm33.2)
Jun 10 07:46:21 antonio-desktop kernel: [    0.000000] KERNEL supported cpus:
Jun 10 07:46:21 antonio-desktop kernel: [    0.000000]   Intel GenuineIntel
Jun 10 07:46:21 antonio-desktop kernel: [    0.000000]   AMD AuthenticAMD
Jun 10 07:46:21 antonio-desktop kernel: [    0.000000]   NSC Geode by NSC
Jun 10 07:46:21 antonio-desktop kernel: [    0.000000]   Cyrix CyrixInstead
Jun 10 07:46:21 antonio-desktop kernel: [    0.000000]   Centaur CentaurHauls
Jun 10 07:46:21 antonio-desktop kernel: [    0.000000]   Transmeta GenuineTMx86
Jun 10 07:46:21 antonio-desktop kernel: [    0.000000]   Transmeta TransmetaCPU
Jun 10 07:46:21 antonio-desktop kernel: [    0.000000]   UMC UMC UMC UMC
Jun 10 07:46:21 antonio-desktop kernel: [    0.000000] BIOS-provided physical RAM map:
Jun 10 07:46:21 antonio-desktop kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
Jun 10 07:46:21 antonio-desktop kernel: [    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
Jun 10 07:46:21 antonio-desktop kernel: [    0.000000]  BIOS-e820: 00000000000e8000 - 0000000000100000 (reserved)
Jun 10 07:46:21 antonio-desktop kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 000000007ffb0000 (usable)
Jun 10 07:46:21 antonio-desktop kernel: [    0.000000]  BIOS-e820: 000000007ffb0000 - 000000007ffc0000 (ACPI data)
Jun 10 07:46:21 antonio-desktop kernel: [    0.000000]  BIOS-e820: 000000007ffc0000 - 000000007fff0000 (ACPI NVS)
Jun 10 07:46:21 antonio-desktop kernel: [    0.000000]  BIOS-e820: 000000007fff0000 - 0000000080000000 (reserved)
Jun 10 07:46:21 antonio-desktop kernel: [    0.000000]  BIOS-e820: 00000000ff7c0000 - 0000000100000000 (reserved)
Jun 10 07:46:21 antonio-desktop kernel: [    0.000000] DMI 2.3 present.
Jun 10 07:46:21 antonio-desktop kernel: [    0.000000] AMI BIOS detected: BIOS may corrupt low RAM, working around it.
Jun 10 07:46:21 antonio-desktop kernel: [    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
Jun 10 07:46:21 antonio-desktop kernel: [    0.000000] last_pfn = 0x7ffb0 max_arch_pfn = 0x100000
Jun 10 07:46:21 antonio-desktop kernel: [    0.000000] MTRR default type: uncachable
Jun 10 07:46:21 antonio-desktop kernel: [    0.000000] MTRR fixed ranges enabled:
Jun 10 07:46:21 antonio-desktop kernel: [    0.000000]   00000-9FFFF write-back
Jun 10 07:46:21 antonio-desktop kernel: [    0.000000]   A0000-EFFFF uncachable
Jun 10 07:46:21 antonio-desktop kernel: [    0.000000]   F0000-FFFFF write-protect
Jun 10 07:46:21 antonio-desktop kernel: [    0.000000] MTRR variable ranges enabled:
Jun 10 07:46:21 antonio-desktop kernel: [    0.000000]   0 base 0000000000 mask FF80000000 write-back
Jun 10 07:46:21 antonio-desktop kernel: [    0.000000]   1 disabled
Jun 10 07:46:21 antonio-desktop kernel: [    0.000000]   2 disabled
Jun 10 07:46:21 antonio-desktop kernel: [    0.000000]   3 disabled
Jun 10 07:46:21 antonio-desktop kernel: [    0.000000]   4 disabled
Jun 10 07:46:21 antonio-desktop kernel: [    0.000000]   5 disabled
Jun 10 07:46:21 antonio-desktop kernel: [    0.000000]   6 disabled
Jun 10 07:46:21 antonio-desktop kernel: [    0.000000]   7 disabled
Jun 10 07:46:21 antonio-desktop kernel: [    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
Jun 10 07:46:21 antonio-desktop kernel: [    0.000000] Scanning 0 areas for low memory corruption
Jun 10 07:46:21 antonio-desktop kernel: [    0.000000] modified physical RAM map:
Jun 10 07:46:21 antonio-desktop kernel: [    0.000000]  modified: 0000000000000000 - 0000000000010000 (reserved)
Jun 10 07:46:21 antonio-desktop kernel: [    0.000000]  modified: 0000000000010000 - 000000000009fc00 (usable)
Jun 10 07:46:21 antonio-desktop kernel: [    0.000000]  modified: 000000000009fc00 - 00000000000a0000 (reserved)
Jun 10 07:46:21 antonio-desktop kernel: [    0.000000]  modified: 00000000000e8000 - 0000000000100000 (reserved)
Jun 10 07:46:21 antonio-desktop kernel: [    0.000000]  modified: 0000000000100000 - 000000007ffb0000 (usable)
Jun 10 07:46:21 antonio-desktop kernel: [    0.000000]  modified: 000000007ffb0000 - 000000007ffc0000 (ACPI data)
Jun 10 07:46:21 antonio-desktop kernel: [    0.000000]  modified: 000000007ffc0000 - 000000007fff0000 (ACPI NVS)
Jun 10 07:46:21 antonio-desktop kernel: [    0.000000]  modified: 000000007fff0000 - 0000000080000000 (reserved)
Jun 10 07:46:21 antonio-desktop kernel: [    0.000000]  modified: 00000000ff7c0000 - 0000000100000000 (reserved)
Jun 10 07:46:21 antonio-desktop kernel: [    0.000000] initial memory mapped : 0 - 00c00000
Jun 10 07:46:21 antonio-desktop kernel: [    0.000000] init_memory_mapping: 0000000000000000-00000000377fe000
Jun 10 07:46:21 antonio-desktop kernel: [    0.000000] Using x86 segment limits to approximate NX protection
Jun 10 07:46:21 antonio-desktop kernel: [    0.000000]  0000000000 - 0000400000 page 4k
Jun 10 07:46:21 antonio-desktop kernel: [    0.000000]  0000400000 - 0037400000 page 2M
Jun 10 07:46:21 antonio-desktop kernel: [    0.000000]  0037400000 - 00377fe000 page 4k
Jun 10 07:46:21 antonio-desktop kernel: [    0.000000] kernel direct mapping tables up to 377fe000 @ 10000-15000
Jun 10 07:46:21 antonio-desktop kernel: [    0.000000] RAMDISK: 3784f000 - 37fef0de
Jun 10 07:46:21 antonio-desktop kernel: [    0.000000] Allocated new RAMDISK: 008de000 - 0107e0de
Jun 10 07:46:21 antonio-desktop kernel: [    0.000000] Move RAMDISK from 000000003784f000 - 0000000037fef0dd to 008de000 - 0107e0dd
Jun 10 07:46:21 antonio-desktop kernel: [    0.000000] ACPI: RSDP 000f9a50 00014 (v00 ACPIAM)
Jun 10 07:46:21 antonio-desktop kernel: [    0.000000] ACPI: RSDT 7ffb0000 00034 (v01 A M I  OEMRSDT  09000625 MSFT 00000097)
Jun 10 07:46:21 antonio-desktop kernel: [    0.000000] ACPI: FACP 7ffb0200 00084 (v02 A M I  OEMFACP  09000625 MSFT 00000097)
Jun 10 07:46:21 antonio-desktop kernel: [    0.000000] ACPI: DSDT 7ffb0440 0474D (v01  939M2 939M2222 00000222 INTL 02002026)
Jun 10 07:46:21 antonio-desktop kernel: [    0.000000] ACPI: FACS 7ffc0000 00040
Jun 10 07:46:21 antonio-desktop kernel: [    0.000000] ACPI: APIC 7ffb0390 00068 (v01 A M I  OEMAPIC  09000625 MSFT 00000097)
Jun 10 07:46:21 antonio-desktop kernel: [    0.000000] ACPI: MCFG 7ffb0400 0003C (v01 A M I  OEMMCFG  09000625 MSFT 00000097)
Jun 10 07:46:21 antonio-desktop kernel: [    0.000000] ACPI: OEMB 7ffc0040 00057 (v01 A M I  AMI_OEM  09000625 MSFT 00000097)
Jun 10 07:46:21 antonio-desktop kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
Jun 10 07:46:21 antonio-desktop kernel: [    0.000000] 1159MB HIGHMEM available.
Jun 10 07:46:21 antonio-desktop kernel: [    0.000000] 887MB LOWMEM available.
Jun 10 07:46:21 antonio-desktop kernel: [    0.000000]   mapped low ram: 0 - 377fe000
Jun 10 07:46:21 antonio-desktop kernel: [    0.000000]   low ram: 0 - 377fe000
Jun 10 07:46:21 antonio-desktop kernel: [    0.000000]   node 0 low ram: 00000000 - 377fe000
Jun 10 07:46:21 antonio-desktop kernel: [    0.000000]   node 0 bootmap 00011000 - 00017f00
Jun 10 07:46:21 antonio-desktop kernel: [    0.000000] (9 early reservations) ==> bootmem [0000000000 - 00377fe000]
Jun 10 07:46:21 antonio-desktop kernel: [    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
Jun 10 07:46:21 antonio-desktop kernel: [    0.000000]   #1 [0000001000 - 0000002000]    EX TRAMPOLINE ==> [0000001000 - 0000002000]
Jun 10 07:46:21 antonio-desktop kernel: [    0.000000]   #2 [0000006000 - 0000007000]       TRAMPOLINE ==> [0000006000 - 0000007000]
Jun 10 07:46:21 antonio-desktop kernel: [    0.000000]   #3 [0000100000 - 00008d9e98]    TEXT DATA BSS ==> [0000100000 - 00008d9e98]
Jun 10 07:46:21 antonio-desktop kernel: [    0.000000]   #4 [000009fc00 - 0000100000]    BIOS reserved ==> [000009fc00 - 0000100000]
Jun 10 07:46:21 antonio-desktop kernel: [    0.000000]   #5 [00008da000 - 00008dd0a9]              BRK ==> [00008da000 - 00008dd0a9]
Jun 10 07:46:21 antonio-desktop kernel: [    0.000000]   #6 [0000010000 - 0000011000]          PGTABLE ==> [0000010000 - 0000011000]
Jun 10 07:46:21 antonio-desktop kernel: [    0.000000]   #7 [00008de000 - 000107e0de]      NEW RAMDISK ==> [00008de000 - 000107e0de]
Jun 10 07:46:21 antonio-desktop kernel: [    0.000000]   #8 [0000011000 - 0000018000]          BOOTMAP ==> [0000011000 - 0000018000]
Jun 10 07:46:21 antonio-desktop kernel: [    0.000000] found SMP MP-table at [c00ff780] ff780
Jun 10 07:46:21 antonio-desktop kernel: [    0.000000] Zone PFN ranges:
Jun 10 07:46:21 antonio-desktop kernel: [    0.000000]   DMA      0x00000010 -> 0x00001000
Jun 10 07:46:21 antonio-desktop kernel: [    0.000000]   Normal   0x00001000 -> 0x000377fe
Jun 10 07:46:21 antonio-desktop kernel: [    0.000000]   HighMem  0x000377fe -> 0x0007ffb0
Jun 10 07:46:21 antonio-desktop kernel: [    0.000000] Movable zone start PFN for each node
Jun 10 07:46:21 antonio-desktop kernel: [    0.000000] early_node_map[2] active PFN ranges
Jun 10 07:46:21 antonio-desktop kernel: [    0.000000]     0: 0x00000010 -> 0x0000009f
Jun 10 07:46:21 antonio-desktop kernel: [    0.000000]     0: 0x00000100 -> 0x0007ffb0
Jun 10 07:46:21 antonio-desktop kernel: [    0.000000] On node 0 totalpages: 524095
Jun 10 07:46:21 antonio-desktop kernel: [    0.000000] free_area_init_node: node 0, pgdat c0798720, node_mem_map c1080200
Jun 10 07:46:21 antonio-desktop kernel: [    0.000000]   DMA zone: 32 pages used for memmap
Jun 10 07:46:21 antonio-desktop kernel: [    0.000000]   DMA zone: 0 pages reserved
Jun 10 07:46:21 antonio-desktop kernel: [    0.000000]   DMA zone: 3951 pages, LIFO batch:0
Jun 10 07:46:21 antonio-desktop kernel: [    0.000000]   Normal zone: 1744 pages used for memmap
Jun 10 07:46:21 antonio-desktop kernel: [    0.000000]   Normal zone: 221486 pages, LIFO batch:31
Jun 10 07:46:21 antonio-desktop kernel: [    0.000000]   HighMem zone: 2320 pages used for memmap
Jun 10 07:46:21 antonio-desktop kernel: [    0.000000]   HighMem zone: 294562 pages, LIFO batch:31
Jun 10 07:46:21 antonio-desktop kernel: [    0.000000] Using APIC driver default
Jun 10 07:46:21 antonio-desktop kernel: [    0.000000] Detected use of extended apic ids on hypertransport bus
Jun 10 07:46:21 antonio-desktop kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x808
Jun 10 07:46:21 antonio-desktop kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
Jun 10 07:46:21 antonio-desktop kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
Jun 10 07:46:21 antonio-desktop kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x81] disabled)
Jun 10 07:46:21 antonio-desktop kernel: [    0.000000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
Jun 10 07:46:21 antonio-desktop kernel: [    0.000000] IOAPIC[0]: apic_id 1, version 17, address 0xfec00000, GSI 0-23
Jun 10 07:46:21 antonio-desktop kernel: [    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec10000] gsi_base[24])
Jun 10 07:46:21 antonio-desktop kernel: [    0.000000] IOAPIC[1]: apic_id 2, version 17, address 0xfec10000, GSI 24-39
Jun 10 07:46:21 antonio-desktop kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
Jun 10 07:46:21 antonio-desktop kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 low level)
Jun 10 07:46:21 antonio-desktop kernel: [    0.000000] ACPI: IRQ0 used by override.
Jun 10 07:46:21 antonio-desktop kernel: [    0.000000] ACPI: IRQ2 used by override.
Jun 10 07:46:21 antonio-desktop kernel: [    0.000000] ACPI: IRQ9 used by override.
Jun 10 07:46:21 antonio-desktop kernel: [    0.000000] Using ACPI (MADT) for SMP configuration information
Jun 10 07:46:21 antonio-desktop kernel: [    0.000000] SMP: Allowing 2 CPUs, 1 hotplug CPUs
Jun 10 07:46:21 antonio-desktop kernel: [    0.000000] nr_irqs_gsi: 40
Jun 10 07:46:21 antonio-desktop kernel: [    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
Jun 10 07:46:21 antonio-desktop kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e8000
Jun 10 07:46:21 antonio-desktop kernel: [    0.000000] PM: Registered nosave memory: 00000000000e8000 - 0000000000100000
Jun 10 07:46:21 antonio-desktop kernel: [    0.000000] Allocating PCI resources starting at 80000000 (gap: 80000000:7f7c0000)
Jun 10 07:46:21 antonio-desktop kernel: [    0.000000] Booting paravirtualized kernel on bare hardware
Jun 10 07:46:21 antonio-desktop kernel: [    0.000000] NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:2 nr_node_ids:1
Jun 10 07:46:21 antonio-desktop kernel: [    0.000000] PERCPU: Embedded 14 pages/cpu @c2400000 s36024 r0 d21320 u2097152
Jun 10 07:46:21 antonio-desktop kernel: [    0.000000] pcpu-alloc: s36024 r0 d21320 u2097152 alloc=1*4194304
Jun 10 07:46:21 antonio-desktop kernel: [    0.000000] pcpu-alloc: [0] 0 1 
Jun 10 07:46:21 antonio-desktop kernel: [    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 519999
Jun 10 07:46:21 antonio-desktop kernel: [    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.32-22-generic root=UUID=f1ac553c-accc-4ce8-9b2d-f34b29fb8bb3 ro pata_ali.atapi_dma=1 quiet splash
Jun 10 07:46:21 antonio-desktop kernel: [    0.000000] PID hash table entries: 4096 (order: 2, 16384 bytes)
Jun 10 07:46:21 antonio-desktop kernel: [    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
Jun 10 07:46:21 antonio-desktop kernel: [    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
Jun 10 07:46:21 antonio-desktop kernel: [    0.000000] Enabling fast FPU save and restore... done.
Jun 10 07:46:21 antonio-desktop kernel: [    0.000000] Enabling unmasked SIMD FPU exception support... done.
Jun 10 07:46:21 antonio-desktop kernel: [    0.000000] Initializing CPU#0
Jun 10 07:46:21 antonio-desktop kernel: [    0.000000] allocated 10483840 bytes of page_cgroup
Jun 10 07:46:21 antonio-desktop kernel: [    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
Jun 10 07:46:21 antonio-desktop kernel: [    0.000000] Initializing HighMem for node 0 (000377fe:0007ffb0)
Jun 10 07:46:21 antonio-desktop kernel: [    0.000000] Memory: 2051868k/2096832k available (4673k kernel code, 43464k reserved, 2121k data, 656k init, 1187528k highmem)
Jun 10 07:46:21 antonio-desktop kernel: [    0.000000] virtual kernel memory layout:
Jun 10 07:46:21 antonio-desktop kernel: [    0.000000]     fixmap  : 0xfff1d000 - 0xfffff000   ( 904 kB)
Jun 10 07:46:21 antonio-desktop kernel: [    0.000000]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
Jun 10 07:46:21 antonio-desktop kernel: [    0.000000]     vmalloc : 0xf7ffe000 - 0xff7fe000   ( 120 MB)
Jun 10 07:46:21 antonio-desktop kernel: [    0.000000]     lowmem  : 0xc0000000 - 0xf77fe000   ( 887 MB)
Jun 10 07:46:21 antonio-desktop kernel: [    0.000000]       .init : 0xc07a3000 - 0xc0847000   ( 656 kB)
Jun 10 07:46:21 antonio-desktop kernel: [    0.000000]       .data : 0xc0590663 - 0xc07a2e48   (2121 kB)
Jun 10 07:46:21 antonio-desktop kernel: [    0.000000]       .text : 0xc0100000 - 0xc0590663   (4673 kB)
Jun 10 07:46:21 antonio-desktop kernel: [    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
Jun 10 07:46:21 antonio-desktop kernel: [    0.000000] SLUB: Genslabs=13, HWalign=64, Order=0-3, MinObjects=0, CPUs=2, Nodes=1
Jun 10 07:46:21 antonio-desktop kernel: [    0.000000] Hierarchical RCU implementation.
Jun 10 07:46:21 antonio-desktop kernel: [    0.000000] NR_IRQS:2304 nr_irqs:512
Jun 10 07:46:21 antonio-desktop kernel: [    0.000000] spurious 8259A interrupt: IRQ7.
Jun 10 07:46:21 antonio-desktop kernel: [    0.000000] Console: colour VGA+ 80x25
Jun 10 07:46:21 antonio-desktop kernel: [    0.000000] console [tty0] enabled
Jun 10 07:46:21 antonio-desktop kernel: [    0.000000] Fast TSC calibration using PIT
Jun 10 07:46:21 antonio-desktop kernel: [    0.000000] Detected 2200.294 MHz processor.
Jun 10 07:46:21 antonio-desktop kernel: [    0.004004] Calibrating delay loop (skipped), value calculated using timer frequency.. 4400.58 BogoMIPS (lpj=8801176)
Jun 10 07:46:21 antonio-desktop kernel: [    0.004023] Security Framework initialized
Jun 10 07:46:21 antonio-desktop kernel: [    0.004043] AppArmor: AppArmor initialized
Jun 10 07:46:21 antonio-desktop kernel: [    0.004050] Mount-cache hash table entries: 512
Jun 10 07:46:21 antonio-desktop kernel: [    0.004177] Initializing cgroup subsys ns
Jun 10 07:46:21 antonio-desktop kernel: [    0.004180] Initializing cgroup subsys cpuacct
Jun 10 07:46:21 antonio-desktop kernel: [    0.004184] Initializing cgroup subsys memory
Jun 10 07:46:21 antonio-desktop kernel: [    0.004190] Initializing cgroup subsys devices
Jun 10 07:46:21 antonio-desktop kernel: [    0.004193] Initializing cgroup subsys freezer
Jun 10 07:46:21 antonio-desktop kernel: [    0.004195] Initializing cgroup subsys net_cls
Jun 10 07:46:21 antonio-desktop kernel: [    0.004212] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
Jun 10 07:46:21 antonio-desktop kernel: [    0.004215] CPU: L2 Cache: 1024K (64 bytes/line)
Jun 10 07:46:21 antonio-desktop kernel: [    0.004218] mce: CPU supports 5 MCE banks
Jun 10 07:46:21 antonio-desktop kernel: [    0.004234] Performance Events: AMD PMU driver.
Jun 10 07:46:21 antonio-desktop kernel: [    0.004240] ... version:                0
Jun 10 07:46:21 antonio-desktop kernel: [    0.004242] ... bit width:              48
Jun 10 07:46:21 antonio-desktop kernel: [    0.004244] ... generic registers:      4
Jun 10 07:46:21 antonio-desktop kernel: [    0.004246] ... value mask:             0000ffffffffffff
Jun 10 07:46:21 antonio-desktop kernel: [    0.004248] ... max period:             00007fffffffffff
Jun 10 07:46:21 antonio-desktop kernel: [    0.004250] ... fixed-purpose events:   0
Jun 10 07:46:21 antonio-desktop kernel: [    0.004251] ... event mask:             000000000000000f
Jun 10 07:46:21 antonio-desktop kernel: [    0.004255] Checking 'hlt' instruction... OK.
Jun 10 07:46:21 antonio-desktop kernel: [    0.020611] SMP alternatives: switching to UP code
Jun 10 07:46:21 antonio-desktop kernel: [    0.025863] ACPI: Core revision 20090903
Jun 10 07:46:21 antonio-desktop kernel: [    0.031590] ftrace: converting mcount calls to 0f 1f 44 00 00
Jun 10 07:46:21 antonio-desktop kernel: [    0.031596] ftrace: allocating 21771 entries in 43 pages
Jun 10 07:46:21 antonio-desktop kernel: [    0.032093] Enabling APIC mode:  Flat.  Using 2 I/O APICs
Jun 10 07:46:21 antonio-desktop kernel: [    0.032879] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
Jun 10 07:46:21 antonio-desktop kernel: [    0.073239] CPU0: AMD Athlon(tm) 64 Processor 3700+ stepping 01
Jun 10 07:46:21 antonio-desktop kernel: [    0.076001] Brought up 1 CPUs
Jun 10 07:46:21 antonio-desktop kernel: [    0.076001] Total of 1 processors activated (4400.58 BogoMIPS).
Jun 10 07:46:21 antonio-desktop kernel: [    0.076001] CPU0 attaching NULL sched-domain.
Jun 10 07:46:21 antonio-desktop kernel: [    0.076001] devtmpfs: initialized
Jun 10 07:46:21 antonio-desktop kernel: [    0.076001] regulator: core version 0.5
Jun 10 07:46:21 antonio-desktop kernel: [    0.076001] Time:  7:46:12  Date: 06/10/10
Jun 10 07:46:21 antonio-desktop kernel: [    0.076001] NET: Registered protocol family 16
Jun 10 07:46:21 antonio-desktop kernel: [    0.076001] EISA bus registered
Jun 10 07:46:21 antonio-desktop kernel: [    0.076001] ACPI: bus type pci registered
Jun 10 07:46:21 antonio-desktop kernel: [    0.076001] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 255
Jun 10 07:46:21 antonio-desktop kernel: [    0.076001] PCI: Not using MMCONFIG.
Jun 10 07:46:21 antonio-desktop kernel: [    0.076001] PCI: PCI BIOS revision 3.00 entry at 0xf0031, last bus=4
Jun 10 07:46:21 antonio-desktop kernel: [    0.076001] PCI: Using configuration type 1 for base access
Jun 10 07:46:21 antonio-desktop kernel: [    0.076001] bio: create slab <bio-0> at 0
Jun 10 07:46:21 antonio-desktop kernel: [    0.076001] ACPI: EC: Look up EC in DSDT
Jun 10 07:46:22 antonio-desktop kernel: [    0.076902] ACPI: Executed 1 blocks of module-level executable AML code
Jun 10 07:46:22 antonio-desktop kernel: [    0.079837] ACPI: Interpreter enabled
Jun 10 07:46:22 antonio-desktop kernel: [    0.079843] ACPI: (supports S0 S1 S4 S5)
Jun 10 07:46:22 antonio-desktop kernel: [    0.079861] ACPI: Using IOAPIC for interrupt routing
Jun 10 07:46:22 antonio-desktop kernel: [    0.080011] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 255
Jun 10 07:46:22 antonio-desktop kernel: [    0.082536] PCI: MCFG area at e0000000 reserved in ACPI motherboard resources
Jun 10 07:46:22 antonio-desktop kernel: [    0.082539] PCI: Using MMCONFIG for extended config space
Jun 10 07:46:22 antonio-desktop kernel: [    0.087308] ACPI: No dock devices found.
Jun 10 07:46:22 antonio-desktop kernel: [    0.087405] ACPI: PCI Root Bridge [PCI0] (0000:00)
Jun 10 07:46:22 antonio-desktop kernel: [    0.087510] pci 0000:00:01.0: PME# supported from D0 D3hot D3cold
Jun 10 07:46:22 antonio-desktop kernel: [    0.087514] pci 0000:00:01.0: PME# disabled
Jun 10 07:46:22 antonio-desktop kernel: [    0.087555] pci 0000:00:02.0: PME# supported from D0 D3hot D3cold
Jun 10 07:46:22 antonio-desktop kernel: [    0.087558] pci 0000:00:02.0: PME# disabled
Jun 10 07:46:22 antonio-desktop kernel: [    0.087589] pci 0000:00:04.0: reg 10 32bit mmio pref: [0xdc000000-0xdfffffff]
Jun 10 07:46:22 antonio-desktop kernel: [    0.087776] pci 0000:00:07.1: quirk: region 0800-083f claimed by ali7101 ACPI
Jun 10 07:46:22 antonio-desktop kernel: [    0.087817] pci 0000:00:11.0: reg 10 io port: [0xe800-0xe8ff]
Jun 10 07:46:22 antonio-desktop kernel: [    0.087823] pci 0000:00:11.0: reg 14 32bit mmio: [0xfebffc00-0xfebffcff]
Jun 10 07:46:22 antonio-desktop kernel: [    0.087849] pci 0000:00:11.0: PME# supported from D3hot D3cold
Jun 10 07:46:22 antonio-desktop kernel: [    0.087853] pci 0000:00:11.0: PME# disabled
Jun 10 07:46:22 antonio-desktop kernel: [    0.087880] pci 0000:00:12.0: reg 20 io port: [0xff00-0xff0f]
Jun 10 07:46:22 antonio-desktop kernel: [    0.087905] pci 0000:00:12.1: reg 10 io port: [0xec00-0xec07]
Jun 10 07:46:22 antonio-desktop kernel: [    0.087910] pci 0000:00:12.1: reg 14 io port: [0xe480-0xe483]
Jun 10 07:46:22 antonio-desktop kernel: [    0.087916] pci 0000:00:12.1: reg 18 io port: [0xe400-0xe407]
Jun 10 07:46:22 antonio-desktop kernel: [    0.087921] pci 0000:00:12.1: reg 1c io port: [0xe080-0xe083]
Jun 10 07:46:22 antonio-desktop kernel: [    0.087927] pci 0000:00:12.1: reg 20 io port: [0xe000-0xe00f]
Jun 10 07:46:22 antonio-desktop kernel: [    0.087956] pci 0000:00:13.0: reg 10 32bit mmio: [0xfebfe000-0xfebfefff]
Jun 10 07:46:22 antonio-desktop kernel: [    0.087993] pci 0000:00:13.1: reg 10 32bit mmio: [0xfebfd000-0xfebfdfff]
Jun 10 07:46:22 antonio-desktop kernel: [    0.088033] pci 0000:00:13.2: reg 10 32bit mmio: [0xfebfc000-0xfebfcfff]
Jun 10 07:46:22 antonio-desktop kernel: [    0.088078] pci 0000:00:13.3: reg 10 32bit mmio: [0xfebff800-0xfebff8ff]
Jun 10 07:46:22 antonio-desktop kernel: [    0.088110] pci 0000:00:13.3: PME# supported from D0 D3hot D3cold
Jun 10 07:46:22 antonio-desktop kernel: [    0.088114] pci 0000:00:13.3: PME# disabled
Jun 10 07:46:22 antonio-desktop kernel: [    0.088220] pci 0000:00:01.0: bridge 32bit mmio: [0xfa700000-0xfa7fffff]
Jun 10 07:46:22 antonio-desktop kernel: [    0.088244] pci 0000:00:02.0: bridge 32bit mmio: [0xfa800000-0xfa8fffff]
Jun 10 07:46:22 antonio-desktop kernel: [    0.088284] pci 0000:03:00.0: reg 10 32bit mmio: [0xfd000000-0xfdffffff]
Jun 10 07:46:22 antonio-desktop kernel: [    0.088292] pci 0000:03:00.0: reg 14 32bit mmio pref: [0xc0000000-0xcfffffff]
Jun 10 07:46:22 antonio-desktop kernel: [    0.088300] pci 0000:03:00.0: reg 18 32bit mmio: [0xfc000000-0xfcffffff]
Jun 10 07:46:22 antonio-desktop kernel: [    0.088320] pci 0000:03:00.0: reg 30 32bit mmio pref: [0xfe9e0000-0xfe9fffff]
Jun 10 07:46:22 antonio-desktop kernel: [    0.088377] pci 0000:00:05.0: bridge 32bit mmio: [0xfa900000-0xfe9fffff]
Jun 10 07:46:22 antonio-desktop kernel: [    0.088382] pci 0000:00:05.0: bridge 32bit mmio pref: [0xb7f00000-0xd7efffff]
Jun 10 07:46:22 antonio-desktop kernel: [    0.088420] pci 0000:04:07.0: reg 10 io port: [0xd880-0xd89f]
Jun 10 07:46:22 antonio-desktop kernel: [    0.088458] pci 0000:04:07.0: supports D1 D2
Jun 10 07:46:22 antonio-desktop kernel: [    0.088486] pci 0000:04:07.1: reg 10 io port: [0xdc00-0xdc07]
Jun 10 07:46:22 antonio-desktop kernel: [    0.088524] pci 0000:04:07.1: supports D1 D2
Jun 10 07:46:22 antonio-desktop kernel: [    0.088561] pci 0000:00:06.0: transparent bridge
Jun 10 07:46:22 antonio-desktop kernel: [    0.088565] pci 0000:00:06.0: bridge io port: [0xd000-0xdfff]
Jun 10 07:46:22 antonio-desktop kernel: [    0.088570] pci 0000:00:06.0: bridge 32bit mmio: [0xfea00000-0xfeafffff]
Jun 10 07:46:22 antonio-desktop kernel: [    0.088586] pci_bus 0000:00: on NUMA node 0
Jun 10 07:46:22 antonio-desktop kernel: [    0.088590] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
Jun 10 07:46:22 antonio-desktop kernel: [    0.088656] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P4._PRT]
Jun 10 07:46:22 antonio-desktop kernel: [    0.088690] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.HTT_._PRT]
Jun 10 07:46:22 antonio-desktop kernel: [    0.088779] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEB1._PRT]
Jun 10 07:46:22 antonio-desktop kernel: [    0.088822] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEB2._PRT]
Jun 10 07:46:22 antonio-desktop kernel: [    0.096930] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 *5 6 7 10 11 12 14 15)
Jun 10 07:46:22 antonio-desktop kernel: [    0.097068] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 *10 11 12 14 15)
Jun 10 07:46:22 antonio-desktop kernel: [    0.097201] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 *10 11 12 14 15), disabled.
Jun 10 07:46:22 antonio-desktop kernel: [    0.097338] ACPI: PCI Interrupt Link [LNKD] (IRQs *3 4 5 6 7 10 11 12 14 15)
Jun 10 07:46:22 antonio-desktop kernel: [    0.097475] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 10 *11 12 14 15)
Jun 10 07:46:22 antonio-desktop kernel: [    0.097612] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 *7 10 11 12 14 15)
Jun 10 07:46:22 antonio-desktop kernel: [    0.097749] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 10 *11 12 14 15)
Jun 10 07:46:22 antonio-desktop kernel: [    0.097886] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 10 11 12 14 15) *9
Jun 10 07:46:22 antonio-desktop kernel: [    0.098023] ACPI: PCI Interrupt Link [LNKP] (IRQs 3 *4 5 6 7 10 11 12 14 15)
Jun 10 07:46:22 antonio-desktop kernel: [    0.098120] vgaarb: device added: PCI:0000:03:00.0,decodes=io+mem,owns=io+mem,locks=none
Jun 10 07:46:22 antonio-desktop kernel: [    0.098124] vgaarb: loaded
Jun 10 07:46:22 antonio-desktop kernel: [    0.098216] SCSI subsystem initialized
Jun 10 07:46:22 antonio-desktop kernel: [    0.098256] libata version 3.00 loaded.
Jun 10 07:46:22 antonio-desktop kernel: [    0.098311] usbcore: registered new interface driver usbfs
Jun 10 07:46:22 antonio-desktop kernel: [    0.098322] usbcore: registered new interface driver hub
Jun 10 07:46:22 antonio-desktop kernel: [    0.098346] usbcore: registered new device driver usb
Jun 10 07:46:22 antonio-desktop kernel: [    0.098449] ACPI: WMI: Mapper loaded
Jun 10 07:46:22 antonio-desktop kernel: [    0.098450] PCI: Using ACPI for IRQ routing
Jun 10 07:46:22 antonio-desktop kernel: [    0.098569] NetLabel: Initializing
Jun 10 07:46:22 antonio-desktop kernel: [    0.098571] NetLabel:  domain hash size = 128
Jun 10 07:46:22 antonio-desktop kernel: [    0.098573] NetLabel:  protocols = UNLABELED CIPSOv4
Jun 10 07:46:22 antonio-desktop kernel: [    0.098585] NetLabel:  unlabeled traffic allowed by default
Jun 10 07:46:22 antonio-desktop kernel: [    0.100226] AppArmor: AppArmor Filesystem Enabled
Jun 10 07:46:22 antonio-desktop kernel: [    0.100236] pnp: PnP ACPI init
Jun 10 07:46:22 antonio-desktop kernel: [    0.100244] ACPI: bus type pnp registered
Jun 10 07:46:22 antonio-desktop kernel: [    0.102422] pnp: PnP ACPI: found 10 devices
Jun 10 07:46:22 antonio-desktop kernel: [    0.102424] ACPI: ACPI bus type pnp unregistered
Jun 10 07:46:22 antonio-desktop kernel: [    0.102427] PnPBIOS: Disabled by ACPI PNP
Jun 10 07:46:22 antonio-desktop kernel: [    0.102438] system 00:05: ioport range 0x480-0x48f has been reserved
Jun 10 07:46:22 antonio-desktop kernel: [    0.102441] system 00:05: ioport range 0x4d0-0x4d1 has been reserved
Jun 10 07:46:22 antonio-desktop kernel: [    0.102444] system 00:05: ioport range 0x800-0x87f could not be reserved
Jun 10 07:46:22 antonio-desktop kernel: [    0.102446] system 00:05: ioport range 0x400-0x40f has been reserved
Jun 10 07:46:22 antonio-desktop kernel: [    0.102452] system 00:06: iomem range 0xfec00000-0xfec00fff could not be reserved
Jun 10 07:46:22 antonio-desktop kernel: [    0.102455] system 00:06: iomem range 0xfee00000-0xfee00fff has been reserved
Jun 10 07:46:22 antonio-desktop kernel: [    0.102458] system 00:06: iomem range 0xe0000000-0xefffffff has been reserved
Jun 10 07:46:22 antonio-desktop kernel: [    0.102461] system 00:06: iomem range 0xfec10000-0xfec10fff could not be reserved
Jun 10 07:46:22 antonio-desktop kernel: [    0.102464] system 00:06: iomem range 0xffb00000-0xffffffff has been reserved
Jun 10 07:46:22 antonio-desktop kernel: [    0.102469] system 00:08: ioport range 0x290-0x29f has been reserved
Jun 10 07:46:22 antonio-desktop kernel: [    0.102475] system 00:09: iomem range 0x0-0x9ffff could not be reserved
Jun 10 07:46:22 antonio-desktop kernel: [    0.102478] system 00:09: iomem range 0xc0000-0xcffff could not be reserved
Jun 10 07:46:22 antonio-desktop kernel: [    0.102481] system 00:09: iomem range 0xe0000-0xfffff could not be reserved
Jun 10 07:46:22 antonio-desktop kernel: [    0.102484] system 00:09: iomem range 0x100000-0x7fffffff could not be reserved
Jun 10 07:46:22 antonio-desktop kernel: [    0.137119] Switching to clocksource acpi_pm
Jun 10 07:46:22 antonio-desktop kernel: [    0.137208] pci 0000:00:01.0: PCI bridge, secondary bus 0000:01
Jun 10 07:46:22 antonio-desktop kernel: [    0.137210] pci 0000:00:01.0:   IO window: disabled
Jun 10 07:46:22 antonio-desktop kernel: [    0.137215] pci 0000:00:01.0:   MEM window: 0xfa700000-0xfa7fffff
Jun 10 07:46:22 antonio-desktop kernel: [    0.137217] pci 0000:00:01.0:   PREFETCH window: disabled
Jun 10 07:46:22 antonio-desktop kernel: [    0.137221] pci 0000:00:02.0: PCI bridge, secondary bus 0000:02
Jun 10 07:46:22 antonio-desktop kernel: [    0.137223] pci 0000:00:02.0:   IO window: disabled
Jun 10 07:46:22 antonio-desktop kernel: [    0.137227] pci 0000:00:02.0:   MEM window: 0xfa800000-0xfa8fffff
Jun 10 07:46:22 antonio-desktop kernel: [    0.137230] pci 0000:00:02.0:   PREFETCH window: disabled
Jun 10 07:46:22 antonio-desktop kernel: [    0.137234] pci 0000:00:05.0: PCI bridge, secondary bus 0000:03
Jun 10 07:46:22 antonio-desktop kernel: [    0.137236] pci 0000:00:05.0:   IO window: disabled
Jun 10 07:46:22 antonio-desktop kernel: [    0.137240] pci 0000:00:05.0:   MEM window: 0xfa900000-0xfe9fffff
Jun 10 07:46:22 antonio-desktop kernel: [    0.137245] pci 0000:00:05.0:   PREFETCH window: 0xb7f00000-0xd7efffff
Jun 10 07:46:22 antonio-desktop kernel: [    0.137251] pci 0000:00:06.0: PCI bridge, secondary bus 0000:04
Jun 10 07:46:22 antonio-desktop kernel: [    0.137254] pci 0000:00:06.0:   IO window: 0xd000-0xdfff
Jun 10 07:46:22 antonio-desktop kernel: [    0.137259] pci 0000:00:06.0:   MEM window: 0xfea00000-0xfeafffff
Jun 10 07:46:22 antonio-desktop kernel: [    0.137263] pci 0000:00:06.0:   PREFETCH window: disabled
Jun 10 07:46:22 antonio-desktop kernel: [    0.137276]   alloc irq_desc for 29 on node -1
Jun 10 07:46:22 antonio-desktop kernel: [    0.137278]   alloc kstat_irqs on node -1
Jun 10 07:46:22 antonio-desktop kernel: [    0.137283] pci 0000:00:01.0: PCI INT A -> GSI 29 (level, low) -> IRQ 29
Jun 10 07:46:22 antonio-desktop kernel: [    0.137288] pci 0000:00:01.0: setting latency timer to 64
Jun 10 07:46:22 antonio-desktop kernel: [    0.137293]   alloc irq_desc for 34 on node -1
Jun 10 07:46:22 antonio-desktop kernel: [    0.137295]   alloc kstat_irqs on node -1
Jun 10 07:46:22 antonio-desktop kernel: [    0.137298] pci 0000:00:02.0: PCI INT A -> GSI 34 (level, low) -> IRQ 34
Jun 10 07:46:22 antonio-desktop kernel: [    0.137301] pci 0000:00:02.0: setting latency timer to 64
Jun 10 07:46:22 antonio-desktop kernel: [    0.137307] pci 0000:00:05.0: setting latency timer to 64
Jun 10 07:46:22 antonio-desktop kernel: [    0.137313] pci 0000:00:06.0: setting latency timer to 64
Jun 10 07:46:22 antonio-desktop kernel: [    0.137317] pci_bus 0000:00: resource 0 io:  [0x00-0xffff]
Jun 10 07:46:22 antonio-desktop kernel: [    0.137320] pci_bus 0000:00: resource 1 mem: [0x000000-0xffffffff]
Jun 10 07:46:22 antonio-desktop kernel: [    0.137323] pci_bus 0000:01: resource 1 mem: [0xfa700000-0xfa7fffff]
Jun 10 07:46:22 antonio-desktop kernel: [    0.137325] pci_bus 0000:02: resource 1 mem: [0xfa800000-0xfa8fffff]
Jun 10 07:46:22 antonio-desktop kernel: [    0.137328] pci_bus 0000:03: resource 1 mem: [0xfa900000-0xfe9fffff]
Jun 10 07:46:22 antonio-desktop kernel: [    0.137331] pci_bus 0000:03: resource 2 pref mem [0xb7f00000-0xd7efffff]
Jun 10 07:46:22 antonio-desktop kernel: [    0.137333] pci_bus 0000:04: resource 0 io:  [0xd000-0xdfff]
Jun 10 07:46:22 antonio-desktop kernel: [    0.137336] pci_bus 0000:04: resource 1 mem: [0xfea00000-0xfeafffff]
Jun 10 07:46:22 antonio-desktop kernel: [    0.137339] pci_bus 0000:04: resource 3 io:  [0x00-0xffff]
Jun 10 07:46:22 antonio-desktop kernel: [    0.137341] pci_bus 0000:04: resource 4 mem: [0x000000-0xffffffff]
Jun 10 07:46:22 antonio-desktop kernel: [    0.137372] NET: Registered protocol family 2
Jun 10 07:46:22 antonio-desktop kernel: [    0.137460] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
Jun 10 07:46:22 antonio-desktop kernel: [    0.137793] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
Jun 10 07:46:22 antonio-desktop kernel: [    0.138554] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
Jun 10 07:46:22 antonio-desktop kernel: [    0.138969] TCP: Hash tables configured (established 131072 bind 65536)
Jun 10 07:46:22 antonio-desktop kernel: [    0.138971] TCP reno registered
Jun 10 07:46:22 antonio-desktop kernel: [    0.139062] NET: Registered protocol family 1
Jun 10 07:46:22 antonio-desktop kernel: [    0.139090] pci 0000:00:00.0: Enabling HT MSI Mapping
Jun 10 07:46:22 antonio-desktop kernel: [    0.139112] pci 0000:00:01.0: Enabling HT MSI Mapping
Jun 10 07:46:22 antonio-desktop kernel: [    0.139131] pci 0000:00:02.0: Enabling HT MSI Mapping
Jun 10 07:46:22 antonio-desktop kernel: [    0.139210] pci 0000:03:00.0: Boot video device
Jun 10 07:46:22 antonio-desktop kernel: [    0.139406] cpufreq-nforce2: No nForce2 chipset.
Jun 10 07:46:22 antonio-desktop kernel: [    0.139434] Scanning for low memory corruption every 60 seconds
Jun 10 07:46:22 antonio-desktop kernel: [    0.139532] audit: initializing netlink socket (disabled)
Jun 10 07:46:22 antonio-desktop kernel: [    0.139542] type=2000 audit(1276155972.136:1): initialized
Jun 10 07:46:22 antonio-desktop kernel: [    0.147577] Trying to unpack rootfs image as initramfs...
Jun 10 07:46:22 antonio-desktop kernel: [    0.156409] highmem bounce pool size: 64 pages
Jun 10 07:46:22 antonio-desktop kernel: [    0.156416] HugeTLB registered 4 MB page size, pre-allocated 0 pages
Jun 10 07:46:22 antonio-desktop kernel: [    0.161455] VFS: Disk quotas dquot_6.5.2
Jun 10 07:46:22 antonio-desktop kernel: [    0.161510] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
Jun 10 07:46:22 antonio-desktop kernel: [    0.162014] fuse init (API version 7.13)
Jun 10 07:46:22 antonio-desktop kernel: [    0.162086] msgmni has been set to 1690
Jun 10 07:46:22 antonio-desktop kernel: [    0.168345] alg: No test for stdrng (krng)
Jun 10 07:46:22 antonio-desktop kernel: [    0.168430] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
Jun 10 07:46:22 antonio-desktop kernel: [    0.168433] io scheduler noop registered
Jun 10 07:46:22 antonio-desktop kernel: [    0.168435] io scheduler anticipatory registered
Jun 10 07:46:22 antonio-desktop kernel: [    0.168437] io scheduler deadline registered
Jun 10 07:46:22 antonio-desktop kernel: [    0.168473] io scheduler cfq registered (default)
Jun 10 07:46:22 antonio-desktop kernel: [    0.168589]   alloc irq_desc for 40 on node -1
Jun 10 07:46:22 antonio-desktop kernel: [    0.168591]   alloc kstat_irqs on node -1
Jun 10 07:46:22 antonio-desktop kernel: [    0.168600] pcieport 0000:00:01.0: irq 40 for MSI/MSI-X
Jun 10 07:46:22 antonio-desktop kernel: [    0.168606] pcieport 0000:00:01.0: setting latency timer to 64
Jun 10 07:46:22 antonio-desktop kernel: [    0.168692]   alloc irq_desc for 41 on node -1
Jun 10 07:46:22 antonio-desktop kernel: [    0.168694]   alloc kstat_irqs on node -1
Jun 10 07:46:22 antonio-desktop kernel: [    0.168699] pcieport 0000:00:02.0: irq 41 for MSI/MSI-X
Jun 10 07:46:22 antonio-desktop kernel: [    0.168704] pcieport 0000:00:02.0: setting latency timer to 64
Jun 10 07:46:22 antonio-desktop kernel: [    0.168780] aer 0000:00:01.0:pcie02: AER service couldn't init device: no _OSC support
Jun 10 07:46:22 antonio-desktop kernel: [    0.168786] aer 0000:00:02.0:pcie02: AER service couldn't init device: no _OSC support
Jun 10 07:46:22 antonio-desktop kernel: [    0.168793] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Jun 10 07:46:22 antonio-desktop kernel: [    0.168813] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
Jun 10 07:46:22 antonio-desktop kernel: [    0.168909] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0
Jun 10 07:46:22 antonio-desktop kernel: [    0.168913] ACPI: Power Button [PWRB]
Jun 10 07:46:22 antonio-desktop kernel: [    0.168953] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
Jun 10 07:46:22 antonio-desktop kernel: [    0.168955] ACPI: Power Button [PWRF]
Jun 10 07:46:22 antonio-desktop kernel: [    0.169184] processor LNXCPU:00: registered as cooling_device0
Jun 10 07:46:22 antonio-desktop kernel: [    0.172763] isapnp: Scanning for PnP cards...
Jun 10 07:46:22 antonio-desktop kernel: [    0.178413] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
Jun 10 07:46:22 antonio-desktop kernel: [    0.179493] brd: module loaded
Jun 10 07:46:22 antonio-desktop kernel: [    0.179906] loop: module loaded
Jun 10 07:46:22 antonio-desktop kernel: [    0.179981] input: Macintosh mouse button emulation as /devices/virtual/input/input2
Jun 10 07:46:22 antonio-desktop kernel: [    0.180104]   alloc irq_desc for 19 on node -1
Jun 10 07:46:22 antonio-desktop kernel: [    0.180106]   alloc kstat_irqs on node -1
Jun 10 07:46:22 antonio-desktop kernel: [    0.180111] pata_acpi 0000:00:12.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
Jun 10 07:46:22 antonio-desktop kernel: [    0.180154] pata_acpi 0000:00:12.0: PCI INT A disabled
Jun 10 07:46:22 antonio-desktop kernel: [    0.180164] pata_acpi 0000:00:12.1: PCI INT A -> GSI 19 (level, low) -> IRQ 19
Jun 10 07:46:22 antonio-desktop kernel: [    0.180180] pata_acpi 0000:00:12.1: PCI INT A disabled
Jun 10 07:46:22 antonio-desktop kernel: [    0.180442] Fixed MDIO Bus: probed
Jun 10 07:46:22 antonio-desktop kernel: [    0.180472] PPP generic driver version 2.4.2
Jun 10 07:46:22 antonio-desktop kernel: [    0.180503] tun: Universal TUN/TAP device driver, 1.6
Jun 10 07:46:22 antonio-desktop kernel: [    0.180505] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
Jun 10 07:46:22 antonio-desktop kernel: [    0.180567] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
Jun 10 07:46:22 antonio-desktop kernel: [    0.180580]   alloc irq_desc for 23 on node -1
Jun 10 07:46:22 antonio-desktop kernel: [    0.180582]   alloc kstat_irqs on node -1
Jun 10 07:46:22 antonio-desktop kernel: [    0.180585] ehci_hcd 0000:00:13.3: PCI INT D -> GSI 23 (level, low) -> IRQ 23
Jun 10 07:46:22 antonio-desktop kernel: [    0.180599] ehci_hcd 0000:00:13.3: EHCI Host Controller
Jun 10 07:46:22 antonio-desktop kernel: [    0.180626] ehci_hcd 0000:00:13.3: new USB bus registered, assigned bus number 1
Jun 10 07:46:22 antonio-desktop kernel: [    0.180650] ehci_hcd 0000:00:13.3: debug port 1
Jun 10 07:46:22 antonio-desktop kernel: [    0.227620] ehci_hcd 0000:00:13.3: irq 23, io mem 0xfebff800
Jun 10 07:46:22 antonio-desktop kernel: [    0.236081] ehci_hcd 0000:00:13.3: USB 2.0 started, EHCI 1.00
Jun 10 07:46:22 antonio-desktop kernel: [    0.236197] usb usb1: configuration #1 chosen from 1 choice
Jun 10 07:46:22 antonio-desktop kernel: [    0.236225] hub 1-0:1.0: USB hub found
Jun 10 07:46:22 antonio-desktop kernel: [    0.236238] hub 1-0:1.0: 8 ports detected
Jun 10 07:46:22 antonio-desktop kernel: [    0.236310] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
Jun 10 07:46:22 antonio-desktop kernel: [    0.236332]   alloc irq_desc for 20 on node -1
Jun 10 07:46:22 antonio-desktop kernel: [    0.236334]   alloc kstat_irqs on node -1
Jun 10 07:46:22 antonio-desktop kernel: [    0.236341] ohci_hcd 0000:00:13.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
Jun 10 07:46:22 antonio-desktop kernel: [    0.236358] ohci_hcd 0000:00:13.0: OHCI Host Controller
Jun 10 07:46:22 antonio-desktop kernel: [    0.236391] ohci_hcd 0000:00:13.0: new USB bus registered, assigned bus number 2
Jun 10 07:46:22 antonio-desktop kernel: [    0.236429] ohci_hcd 0000:00:13.0: irq 20, io mem 0xfebfe000
Jun 10 07:46:22 antonio-desktop kernel: [    0.318005] usb usb2: configuration #1 chosen from 1 choice
Jun 10 07:46:22 antonio-desktop kernel: [    0.318036] hub 2-0:1.0: USB hub found
Jun 10 07:46:22 antonio-desktop kernel: [    0.318047] hub 2-0:1.0: 3 ports detected
Jun 10 07:46:22 antonio-desktop kernel: [    0.318099]   alloc irq_desc for 21 on node -1
Jun 10 07:46:22 antonio-desktop kernel: [    0.318101]   alloc kstat_irqs on node -1
Jun 10 07:46:22 antonio-desktop kernel: [    0.318108] ohci_hcd 0000:00:13.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
Jun 10 07:46:22 antonio-desktop kernel: [    0.318125] ohci_hcd 0000:00:13.1: OHCI Host Controller
Jun 10 07:46:22 antonio-desktop kernel: [    0.318162] ohci_hcd 0000:00:13.1: new USB bus registered, assigned bus number 3
Jun 10 07:46:22 antonio-desktop kernel: [    0.318197] ohci_hcd 0000:00:13.1: irq 21, io mem 0xfebfd000
Jun 10 07:46:22 antonio-desktop kernel: [    0.409912] usb usb3: configuration #1 chosen from 1 choice
Jun 10 07:46:22 antonio-desktop kernel: [    0.409940] hub 3-0:1.0: USB hub found
Jun 10 07:46:22 antonio-desktop kernel: [    0.409952] hub 3-0:1.0: 3 ports detected
Jun 10 07:46:22 antonio-desktop kernel: [    0.410003]   alloc irq_desc for 22 on node -1
Jun 10 07:46:22 antonio-desktop kernel: [    0.410005]   alloc kstat_irqs on node -1
Jun 10 07:46:22 antonio-desktop kernel: [    0.410012] ohci_hcd 0000:00:13.2: PCI INT C -> GSI 22 (level, low) -> IRQ 22
Jun 10 07:46:22 antonio-desktop kernel: [    0.410030] ohci_hcd 0000:00:13.2: OHCI Host Controller
Jun 10 07:46:22 antonio-desktop kernel: [    0.410068] ohci_hcd 0000:00:13.2: new USB bus registered, assigned bus number 4
Jun 10 07:46:22 antonio-desktop kernel: [    0.410103] ohci_hcd 0000:00:13.2: irq 22, io mem 0xfebfc000
Jun 10 07:46:22 antonio-desktop kernel: [    0.497728] usb usb4: configuration #1 chosen from 1 choice
Jun 10 07:46:22 antonio-desktop kernel: [    0.497762] hub 4-0:1.0: USB hub found
Jun 10 07:46:22 antonio-desktop kernel: [    0.497774] hub 4-0:1.0: 3 ports detected
Jun 10 07:46:22 antonio-desktop kernel: [    0.497830] uhci_hcd: USB Universal Host Controller Interface driver
Jun 10 07:46:22 antonio-desktop kernel: [    0.497908] PNP: PS/2 Controller [PNP0303:PS2K] at 0x60,0x64 irq 1
Jun 10 07:46:22 antonio-desktop kernel: [    0.497910] PNP: PS/2 appears to have AUX port disabled, if this is incorrect please boot with i8042.nopnp
Jun 10 07:46:22 antonio-desktop kernel: [    0.498619] serio: i8042 KBD port at 0x60,0x64 irq 1
Jun 10 07:46:22 antonio-desktop kernel: [    0.498736] mice: PS/2 mouse device common for all mice
Jun 10 07:46:22 antonio-desktop kernel: [    0.502246] rtc_cmos 00:02: RTC can wake from S4
Jun 10 07:46:22 antonio-desktop kernel: [    0.502285] rtc_cmos 00:02: rtc core: registered rtc_cmos as rtc0
Jun 10 07:46:22 antonio-desktop kernel: [    0.502317] rtc0: alarms up to one month, 114 bytes nvram
Jun 10 07:46:22 antonio-desktop kernel: [    0.502412] device-mapper: uevent: version 1.0.3
Jun 10 07:46:22 antonio-desktop kernel: [    0.502514] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: dm-devel@redhat.com
Jun 10 07:46:22 antonio-desktop kernel: [    0.503683] device-mapper: multipath: version 1.1.0 loaded
Jun 10 07:46:22 antonio-desktop kernel: [    0.503685] device-mapper: multipath round-robin: version 1.0.0 loaded
Jun 10 07:46:22 antonio-desktop kernel: [    0.504968] EISA: Probing bus 0 at eisa.0
Jun 10 07:46:22 antonio-desktop kernel: [    0.505004] EISA: Detected 0 cards.
Jun 10 07:46:22 antonio-desktop kernel: [    0.507426] cpuidle: using governor ladder
Jun 10 07:46:22 antonio-desktop kernel: [    0.507428] cpuidle: using governor menu
Jun 10 07:46:22 antonio-desktop kernel: [    0.507815] TCP cubic registered
Jun 10 07:46:22 antonio-desktop kernel: [    0.507960] NET: Registered protocol family 10
Jun 10 07:46:22 antonio-desktop kernel: [    0.508370] lo: Disabled Privacy Extensions
Jun 10 07:46:22 antonio-desktop kernel: [    0.508641] NET: Registered protocol family 17
Jun 10 07:46:22 antonio-desktop kernel: [    0.508669] powernow-k8: Found 1 AMD Athlon(tm) 64 Processor 3700+ processors (1 cpu cores) (version 2.20.00)
Jun 10 07:46:22 antonio-desktop kernel: [    0.508708] powernow-k8:    0 : fid 0xe (2200 MHz), vid 0x6
Jun 10 07:46:22 antonio-desktop kernel: [    0.508711] powernow-k8:    1 : fid 0xc (2000 MHz), vid 0x8
Jun 10 07:46:22 antonio-desktop kernel: [    0.508713] powernow-k8:    2 : fid 0xa (1800 MHz), vid 0xa
Jun 10 07:46:22 antonio-desktop kernel: [    0.508716] powernow-k8:    3 : fid 0x2 (1000 MHz), vid 0x12
Jun 10 07:46:22 antonio-desktop kernel: [    0.508751] Using IPI No-Shortcut mode
Jun 10 07:46:22 antonio-desktop kernel: [    0.508836] PM: Resume from disk failed.
Jun 10 07:46:22 antonio-desktop kernel: [    0.508853] registered taskstats version 1
Jun 10 07:46:22 antonio-desktop kernel: [    0.509077]   Magic number: 14:725:773
Jun 10 07:46:22 antonio-desktop kernel: [    0.509084] hub 2-0:1.0: hash matches
Jun 10 07:46:22 antonio-desktop kernel: [    0.509164] rtc_cmos 00:02: setting system clock to 2010-06-10 07:46:13 UTC (1276155973)
Jun 10 07:46:22 antonio-desktop kernel: [    0.509168] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
Jun 10 07:46:22 antonio-desktop kernel: [    0.509170] EDD information not available.
Jun 10 07:46:22 antonio-desktop kernel: [    0.518250] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input3
Jun 10 07:46:22 antonio-desktop kernel: [    0.589290] Freeing initrd memory: 7808k freed
Jun 10 07:46:22 antonio-desktop kernel: [    0.725730] isapnp: No Plug & Play device found
Jun 10 07:46:22 antonio-desktop kernel: [    0.725745] Freeing unused kernel memory: 656k freed
Jun 10 07:46:22 antonio-desktop kernel: [    0.726338] Write protecting the kernel text: 4676k
Jun 10 07:46:22 antonio-desktop kernel: [    0.726368] Write protecting the kernel read-only data: 1840k
Jun 10 07:46:22 antonio-desktop kernel: [    0.741888] udev: starting version 151
Jun 10 07:46:22 antonio-desktop kernel: [    0.852054] usb 2-2: new low speed USB device using ohci_hcd and address 2
Jun 10 07:46:22 antonio-desktop kernel: [    0.922945] sata_uli 0000:00:12.1: version 1.3
Jun 10 07:46:22 antonio-desktop kernel: [    0.922956] sata_uli 0000:00:12.1: PCI INT A -> GSI 19 (level, low) -> IRQ 19
Jun 10 07:46:22 antonio-desktop kernel: [    0.926561] scsi0 : sata_uli
Jun 10 07:46:22 antonio-desktop kernel: [    0.927295] scsi1 : sata_uli
Jun 10 07:46:22 antonio-desktop kernel: [    0.927493] ata1: SATA max UDMA/133 cmd 0xec00 ctl 0xe480 bmdma 0xe000 irq 19
Jun 10 07:46:22 antonio-desktop kernel: [    0.927497] ata2: SATA max UDMA/133 cmd 0xe400 ctl 0xe080 bmdma 0xe008 irq 19
Jun 10 07:46:22 antonio-desktop kernel: [    0.927626] pata_ali 0000:00:12.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
Jun 10 07:46:22 antonio-desktop kernel: [    0.929702] scsi2 : pata_ali
Jun 10 07:46:22 antonio-desktop kernel: [    0.930139] scsi3 : pata_ali
Jun 10 07:46:22 antonio-desktop kernel: [    0.931347] ata3: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xff00 irq 14
Jun 10 07:46:22 antonio-desktop kernel: [    0.931350] ata4: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xff08 irq 15
Jun 10 07:46:22 antonio-desktop kernel: [    1.065027] usb 2-2: configuration #1 chosen from 1 choice
Jun 10 07:46:22 antonio-desktop kernel: [    1.096310] ata3.00: ATAPI: PIONEER DVD-RW  DVR-108, 1.20, max UDMA/66
Jun 10 07:46:22 antonio-desktop kernel: [    1.104205] ata3.00: configured for UDMA/66
Jun 10 07:46:22 antonio-desktop kernel: [    1.392051] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
Jun 10 07:46:22 antonio-desktop kernel: [    1.400309] ata1.00: ATA-7: ST3200826AS, 3.06, max UDMA/133
Jun 10 07:46:22 antonio-desktop kernel: [    1.400312] ata1.00: 390721968 sectors, multi 16: LBA48 NCQ (depth 0/32)
Jun 10 07:46:22 antonio-desktop kernel: [    1.416338] ata1.00: configured for UDMA/133
Jun 10 07:46:22 antonio-desktop kernel: [    1.416440] scsi 0:0:0:0: Direct-Access     ATA      ST3200826AS      3.06 PQ: 0 ANSI: 5
Jun 10 07:46:22 antonio-desktop kernel: [    1.416571] sd 0:0:0:0: Attached scsi generic sg0 type 0
Jun 10 07:46:22 antonio-desktop kernel: [    1.416749] sd 0:0:0:0: [sda] 390721968 512-byte logical blocks: (200 GB/186 GiB)
Jun 10 07:46:22 antonio-desktop kernel: [    1.416787] sd 0:0:0:0: [sda] Write Protect is off
Jun 10 07:46:22 antonio-desktop kernel: [    1.416789] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
Jun 10 07:46:22 antonio-desktop kernel: [    1.416810] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Jun 10 07:46:22 antonio-desktop kernel: [    1.416919]  sda: sda1 sda2 < sda5 sda6 >
Jun 10 07:46:22 antonio-desktop kernel: [    1.481147] sd 0:0:0:0: [sda] Attached SCSI disk
Jun 10 07:46:22 antonio-desktop kernel: [    1.884046] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
Jun 10 07:46:22 antonio-desktop kernel: [    1.908188] ata2.00: HPA unlocked: 320170943 -> 320173056, native 320173056
Jun 10 07:46:22 antonio-desktop kernel: [    1.908192] ata2.00: ATA-7: Maxtor 6L160M0, BANC1E00, max UDMA/133
Jun 10 07:46:22 antonio-desktop kernel: [    1.908195] ata2.00: 320173056 sectors, multi 16: LBA48 NCQ (not used)
Jun 10 07:46:22 antonio-desktop kernel: [    1.925154] ata2.00: configured for UDMA/133
Jun 10 07:46:22 antonio-desktop kernel: [    1.925209] scsi 1:0:0:0: Direct-Access     ATA      Maxtor 6L160M0   BANC PQ: 0 ANSI: 5
Jun 10 07:46:22 antonio-desktop kernel: [    1.925303] sd 1:0:0:0: Attached scsi generic sg1 type 0
Jun 10 07:46:22 antonio-desktop kernel: [    1.925503] sd 1:0:0:0: [sdb] 320173056 512-byte logical blocks: (163 GB/152 GiB)
Jun 10 07:46:22 antonio-desktop kernel: [    1.925539] sd 1:0:0:0: [sdb] Write Protect is off
Jun 10 07:46:22 antonio-desktop kernel: [    1.925542] sd 1:0:0:0: [sdb] Mode Sense: 00 3a 00 00
Jun 10 07:46:22 antonio-desktop kernel: [    1.925562] sd 1:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Jun 10 07:46:22 antonio-desktop kernel: [    1.925656]  sdb:
Jun 10 07:46:22 antonio-desktop kernel: [    1.931401] scsi 2:0:0:0: CD-ROM            PIONEER  DVD-RW  DVR-108  1.20 PQ: 0 ANSI: 5
Jun 10 07:46:22 antonio-desktop kernel: [    1.945322]  sdb1 sdb2 <sr0: scsi3-mmc drive: 40x/40x writer cd/rw xa/form2 cdda tray
Jun 10 07:46:22 antonio-desktop kernel: [    1.949760] Uniform CD-ROM driver Revision: 3.20
Jun 10 07:46:22 antonio-desktop kernel: [    1.949827] sr 2:0:0:0: Attached scsi CD-ROM sr0
Jun 10 07:46:22 antonio-desktop kernel: [    1.949866] sr 2:0:0:0: Attached scsi generic sg2 type 5
Jun 10 07:46:22 antonio-desktop kernel: [    1.961473]  sdb5 sdb6 >
Jun 10 07:46:22 antonio-desktop kernel: [    1.981320] sd 1:0:0:0: [sdb] Attached SCSI disk
Jun 10 07:46:22 antonio-desktop kernel: [    2.114397] usbcore: registered new interface driver hiddev
Jun 10 07:46:22 antonio-desktop kernel: [    2.121295] input: PS/2+USB Mouse as /devices/pci0000:00/0000:00:13.0/usb2/2-2/2-2:1.0/input/input4
Jun 10 07:46:22 antonio-desktop kernel: [    2.121388] generic-usb 0003:1267:0201.0001: input,hidraw0: USB HID v1.10 Mouse [PS/2+USB Mouse] on usb-0000:00:13.0-2/input0
Jun 10 07:46:22 antonio-desktop kernel: [    2.121414] usbcore: registered new interface driver usbhid
Jun 10 07:46:22 antonio-desktop kernel: [    2.121417] usbhid: v2.6:USB HID core driver
Jun 10 07:46:22 antonio-desktop kernel: [    2.418794] EXT4-fs (sda5): mounted filesystem with ordered data mode
Jun 10 07:46:22 antonio-desktop kernel: [    4.348847] Adding 995988k swap on /dev/sda1.  Priority:-1 extents:1 across:995988k 
Jun 10 07:46:22 antonio-desktop kernel: [    5.349520] udev: starting version 151
Jun 10 07:46:22 antonio-desktop kernel: [    6.073510] type=1505 audit(1276148779.062:2):  operation="profile_load" pid=492 name="/sbin/dhclient3"
Jun 10 07:46:22 antonio-desktop kernel: [    6.073772] type=1505 audit(1276148779.062:3):  operation="profile_load" pid=492 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
Jun 10 07:46:22 antonio-desktop kernel: [    6.073914] type=1505 audit(1276148779.062:4):  operation="profile_load" pid=492 name="/usr/lib/connman/scripts/dhclient-script"
Jun 10 07:46:22 antonio-desktop kernel: [    6.859721] Linux agpgart interface v0.103
Jun 10 07:46:22 antonio-desktop kernel: [    6.880233] agpgart-ali 0000:00:04.0: unsupported ALi chipset [10b9/1689])
Jun 10 07:46:22 antonio-desktop kernel: [    6.884387] agpgart-amd64 0000:00:04.0: AGP bridge [10b9/1689]
Jun 10 07:46:22 antonio-desktop kernel: [    6.884412] agpgart-amd64 0000:00:04.0: aperture size 4096 MB is not right, using settings from NB
Jun 10 07:46:22 antonio-desktop kernel: [    6.884418] agpgart-amd64 0000:00:04.0: setting up ULi AGP
Jun 10 07:46:22 antonio-desktop kernel: [    6.887942] agpgart-amd64 0000:00:04.0: AGP aperture is 64M @ 0xdc000000
Jun 10 07:46:22 antonio-desktop kernel: [    6.917525] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
Jun 10 07:46:22 antonio-desktop kernel: [    6.958000] uli526x: ULi M5261/M5263 net driver, version 0.9.3 (2005-7-29)
Jun 10 07:46:22 antonio-desktop kernel: [    6.958035]   alloc irq_desc for 17 on node -1
Jun 10 07:46:22 antonio-desktop kernel: [    6.958038]   alloc kstat_irqs on node -1
Jun 10 07:46:22 antonio-desktop kernel: [    6.958045] uli526x 0000:00:11.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
Jun 10 07:46:22 antonio-desktop kernel: [    6.980934] eth0: ULi M5263 at pci0000:00:11.0, 00:13:8f:3f:d6:50, irq 17.
Jun 10 07:46:22 antonio-desktop kernel: [    6.985386] udev: renamed network interface eth0 to eth1
Jun 10 07:46:22 antonio-desktop kernel: [    7.047719] ali1535_smbus 0000:00:07.1: ALI1535_smb region uninitialized - upgrade BIOS?
Jun 10 07:46:22 antonio-desktop kernel: [    7.047722] ali1535_smbus 0000:00:07.1: ALI1535 not detected, module not inserted.
Jun 10 07:46:22 antonio-desktop kernel: [    7.048421] ACPI: resource ali1563_smbus [0x400-0x40f] conflicts with ACPI region SMIO [0xb1-0x1000b0]
Jun 10 07:46:22 antonio-desktop kernel: [    7.048424] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
Jun 10 07:46:22 antonio-desktop kernel: [    7.048427] ali1563_smbus 0000:00:07.0: ALi1563 SMBus probe failed (-19)
Jun 10 07:46:22 antonio-desktop kernel: [    7.051530] ali15x3_smbus 0000:00:07.1: ALI15X3_smb region uninitialized - upgrade BIOS or use force_addr=0xaddr
Jun 10 07:46:22 antonio-desktop kernel: [    7.051611] ali15x3_smbus 0000:00:07.1: ALI15X3 not detected, module not inserted.
Jun 10 07:46:22 antonio-desktop kernel: [    7.329998] EXT4-fs (sda6): mounted filesystem with ordered data mode
Jun 10 07:46:22 antonio-desktop kernel: [    8.154828] EMU10K1_Audigy 0000:04:07.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
Jun 10 07:46:23 antonio-desktop kernel: [   10.151243] type=1505 audit(1276148783.138:5):  operation="profile_replace" pid=743 name="/sbin/dhclient3"
Jun 10 07:46:23 antonio-desktop kernel: [   10.151518] type=1505 audit(1276148783.138:6):  operation="profile_replace" pid=743 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
Jun 10 07:46:23 antonio-desktop kernel: [   10.151674] type=1505 audit(1276148783.138:7):  operation="profile_replace" pid=743 name="/usr/lib/connman/scripts/dhclient-script"
Jun 10 07:46:23 antonio-desktop kernel: [   10.182629] type=1505 audit(1276148783.171:8):  operation="profile_load" pid=744 name="/usr/bin/evince"
Jun 10 07:46:23 antonio-desktop kernel: [   10.186710] type=1505 audit(1276148783.174:9):  operation="profile_load" pid=744 name="/usr/bin/evince-previewer"
Jun 10 07:46:23 antonio-desktop kernel: [   10.188968] type=1505 audit(1276148783.178:10):  operation="profile_load" pid=744 name="/usr/bin/evince-thumbnailer"
Jun 10 07:46:23 antonio-desktop kernel: [   10.215301] type=1505 audit(1276148783.202:11):  operation="profile_load" pid=747 name="/usr/lib/cups/backend/cups-pdf"
Jun 10 07:46:24 antonio-desktop NetworkManager: <info>  starting...
Jun 10 07:46:24 antonio-desktop NetworkManager: <info>  Trying to start the modem-manager...
Jun 10 07:46:24 antonio-desktop NetworkManager:    SCPlugin-Ifupdown: init!
Jun 10 07:46:24 antonio-desktop NetworkManager:    SCPlugin-Ifupdown: update_system_hostname
Jun 10 07:46:24 antonio-desktop NetworkManager:    SCPluginIfupdown: management mode: unmanaged
Jun 10 07:46:24 antonio-desktop NetworkManager:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:11.0/net/eth1, iface: eth1)
Jun 10 07:46:24 antonio-desktop NetworkManager:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:11.0/net/eth1, iface: eth1): no ifupdown configuration found.
Jun 10 07:46:24 antonio-desktop NetworkManager:    SCPlugin-Ifupdown: devices added (path: /sys/devices/virtual/net/lo, iface: lo)
Jun 10 07:46:24 antonio-desktop NetworkManager:    SCPlugin-Ifupdown: device added (path: /sys/devices/virtual/net/lo, iface: lo): no ifupdown configuration found.
Jun 10 07:46:24 antonio-desktop NetworkManager:    SCPlugin-Ifupdown: end _init.
Jun 10 07:46:24 antonio-desktop NetworkManager: Loaded plugin ifupdown: (C) 2008 Canonical Ltd.  To report bugs please use the NetworkManager mailing list.
Jun 10 07:46:24 antonio-desktop NetworkManager: Loaded plugin keyfile: (c) 2007 - 2008 Red Hat, Inc.  To report bugs please use the NetworkManager mailing list.
Jun 10 07:46:24 antonio-desktop NetworkManager: <info>  WiFi enabled by radio killswitch; enabled by state file
Jun 10 07:46:24 antonio-desktop NetworkManager: <info>  WWAN enabled by radio killswitch; enabled by state file
Jun 10 07:46:24 antonio-desktop NetworkManager:    SCPlugin-Ifupdown: (138940656) ... get_connections.
Jun 10 07:46:24 antonio-desktop NetworkManager:    SCPlugin-Ifupdown: (138940656) ... get_connections (managed=false): return empty list.
Jun 10 07:46:25 antonio-desktop NetworkManager:    Ifupdown: get unmanaged devices count: 0
Jun 10 07:46:25 antonio-desktop NetworkManager: <info>  (eth1): carrier is OFF
Jun 10 07:46:25 antonio-desktop NetworkManager: <info>  (eth1): new Ethernet device (driver: 'uli526x')
Jun 10 07:46:25 antonio-desktop NetworkManager: <info>  (eth1): exported as /org/freedesktop/NetworkManager/Devices/0
Jun 10 07:46:25 antonio-desktop NetworkManager: <info>  (eth1): now managed
Jun 10 07:46:25 antonio-desktop NetworkManager: <info>  (eth1): device state change: 1 -> 2 (reason 2)
Jun 10 07:46:25 antonio-desktop NetworkManager: <info>  (eth1): bringing up device.
Jun 10 07:46:25 antonio-desktop NetworkManager: <info>  (eth1): preparing device.
Jun 10 07:46:25 antonio-desktop NetworkManager: <info>  (eth1): deactivating device (reason: 2).
Jun 10 07:46:25 antonio-desktop kernel: [   12.469846] ADDRCONF(NETDEV_UP): eth1: link is not ready
Jun 10 07:46:25 antonio-desktop NetworkManager: <WARN>  default_adapter_cb(): bluez error getting default adapter: The name org.bluez was not provided by any .service files
Jun 10 07:46:25 antonio-desktop NetworkManager: <info>  Trying to start the supplicant...
Jun 10 07:46:25 antonio-desktop gdm-binary[772]: WARNING: Unable to find users: no seat-id found
Jun 10 07:46:25 antonio-desktop cron[800]: (CRON) INFO (pidfile fd = 3)
Jun 10 07:46:25 antonio-desktop acpid: starting up with proc fs
Jun 10 07:46:25 antonio-desktop anacron[885]: Anacron 2.3 started on 2010-06-10
Jun 10 07:46:25 antonio-desktop cron[887]: (CRON) STARTUP (fork ok)
Jun 10 07:46:25 antonio-desktop init: apport pre-start process (796) terminated with status 1
Jun 10 07:46:25 antonio-desktop init: apport post-stop process (889) terminated with status 1
Jun 10 07:46:25 antonio-desktop anacron[885]: Will run job `cron.daily' in 5 min.
Jun 10 07:46:25 antonio-desktop anacron[885]: Jobs will be executed sequentially
Jun 10 07:46:25 antonio-desktop acpid: 36 rules loaded
Jun 10 07:46:25 antonio-desktop acpid: waiting for events: event logging is off
Jun 10 07:46:26 antonio-desktop cron[887]: (CRON) INFO (Running @reboot jobs)
Jun 10 07:46:26 antonio-desktop kernel: [   13.635210] vboxdrv: Trying to deactivate the NMI watchdog permanently...
Jun 10 07:46:26 antonio-desktop kernel: [   13.635214] vboxdrv: Warning: 2.6.31+ kernel detected. Most likely the hardware performance
Jun 10 07:46:26 antonio-desktop kernel: [   13.635216] vboxdrv: counter framework which can generate NMIs is active. You have to prevent
Jun 10 07:46:26 antonio-desktop kernel: [   13.635217] vboxdrv: the usage of hardware performance counters by
Jun 10 07:46:26 antonio-desktop kernel: [   13.635218] vboxdrv:   echo 2 > /proc/sys/kernel/perf_counter_paranoid
Jun 10 07:46:26 antonio-desktop kernel: [   13.635221] vboxdrv: Found 1 processor cores.
Jun 10 07:46:26 antonio-desktop kernel: [   13.636701] vboxdrv: TSC mode is 'synchronous', kernel timer mode is 'normal'.
Jun 10 07:46:26 antonio-desktop kernel: [   13.636704] vboxdrv: Successfully loaded version 3.2.4 (interface 0x00140001).
Jun 10 07:46:26 antonio-desktop acpid: client connected from 909[0:0]
Jun 10 07:46:26 antonio-desktop acpid: 1 client rule loaded
Jun 10 07:46:27 antonio-desktop NetworkManager:    SCPlugin-Ifupdown: devices added (path: /sys/devices/virtual/net/vboxnet0, iface: vboxnet0)
Jun 10 07:46:27 antonio-desktop NetworkManager:    SCPlugin-Ifupdown: device added (path: /sys/devices/virtual/net/vboxnet0, iface: vboxnet0): no ifupdown configuration found.
Jun 10 07:46:27 antonio-desktop NetworkManager: <WARN>  device_creator(): /sys/devices/virtual/net/vboxnet0: couldn't determine device driver; ignoring...
Jun 10 07:46:29 antonio-desktop kernel: [   15.107034] nvidia: module license 'NVIDIA' taints kernel.
Jun 10 07:46:29 antonio-desktop NetworkManager: <info>  (eth1): carrier now ON (device state 2)
Jun 10 07:46:29 antonio-desktop NetworkManager: <info>  (eth1): device state change: 2 -> 3 (reason 40)
Jun 10 07:46:29 antonio-desktop NetworkManager: <info>  Activation (eth1) starting connection 'Auto eth0'
Jun 10 07:46:29 antonio-desktop kernel: [   15.107037] Disabling lock debugging due to kernel taint
Jun 10 07:46:29 antonio-desktop NetworkManager: <info>  (eth1): device state change: 3 -> 4 (reason 0)
Jun 10 07:46:29 antonio-desktop kernel: [   15.468328] uli526x: eth1 NIC Link is Up 100 Mbps Full duplex
Jun 10 07:46:29 antonio-desktop NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) scheduled...
Jun 10 07:46:29 antonio-desktop kernel: [   16.119192] ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
Jun 10 07:46:29 antonio-desktop NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) started...
Jun 10 07:46:29 antonio-desktop NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) scheduled...
Jun 10 07:46:29 antonio-desktop NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) complete.
Jun 10 07:46:29 antonio-desktop NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) starting...
Jun 10 07:46:29 antonio-desktop NetworkManager: <info>  (eth1): device state change: 4 -> 5 (reason 0)
Jun 10 07:46:29 antonio-desktop NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) successful.
Jun 10 07:46:29 antonio-desktop NetworkManager: <info>  Activation (eth1) Stage 3 of 5 (IP Configure Start) scheduled.
Jun 10 07:46:29 antonio-desktop NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) complete.
Jun 10 07:46:29 antonio-desktop NetworkManager: <info>  Activation (eth1) Stage 3 of 5 (IP Configure Start) started...
Jun 10 07:46:29 antonio-desktop NetworkManager: <info>  (eth1): device state change: 5 -> 7 (reason 0)
Jun 10 07:46:29 antonio-desktop NetworkManager: <info>  Activation (eth1) Stage 4 of 5 (IP4 Configure Get) scheduled...
Jun 10 07:46:29 antonio-desktop NetworkManager: <info>  Activation (eth1) Stage 4 of 5 (IP6 Configure Get) scheduled...
Jun 10 07:46:29 antonio-desktop NetworkManager: <info>  Activation (eth1) Stage 3 of 5 (IP Configure Start) complete.
Jun 10 07:46:29 antonio-desktop NetworkManager: <info>  Activation (eth1) Stage 4 of 5 (IP4 Configure Get) started...
Jun 10 07:46:29 antonio-desktop NetworkManager: <info>  Activation (eth1) Stage 4 of 5 (IP4 Configure Get) complete.
Jun 10 07:46:29 antonio-desktop NetworkManager: <info>  Activation (eth1) Stage 4 of 5 (IP6 Configure Get) started...
Jun 10 07:46:29 antonio-desktop NetworkManager: <info>  Activation (eth1) Stage 5 of 5 (IP Configure Commit) scheduled...
Jun 10 07:46:29 antonio-desktop NetworkManager: <info>  Activation (eth1) Stage 4 of 5 (IP6 Configure Get) complete.
Jun 10 07:46:29 antonio-desktop NetworkManager: <info>  Activation (eth1) Stage 5 of 5 (IP Configure Commit) started...
Jun 10 07:46:29 antonio-desktop kernel: [   16.372666]   alloc irq_desc for 16 on node -1
Jun 10 07:46:29 antonio-desktop kernel: [   16.372670]   alloc kstat_irqs on node -1
Jun 10 07:46:29 antonio-desktop kernel: [   16.372677] nvidia 0000:03:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Jun 10 07:46:29 antonio-desktop kernel: [   16.372687] vgaarb: device changed decodes: PCI:0000:03:00.0,olddecodes=io+mem,decodes=none:owns=io+mem
Jun 10 07:46:29 antonio-desktop kernel: [   16.373586] NVRM: loading NVIDIA UNIX x86 Kernel Module  195.36.24  Thu Apr 22 09:18:20 PDT 2010
Jun 10 07:46:30 antonio-desktop NetworkManager: <info>  (eth1): device state change: 7 -> 8 (reason 0)
Jun 10 07:46:30 antonio-desktop NetworkManager: <info>  Policy set 'Auto eth0' (eth1) as default for routing and DNS.
Jun 10 07:46:30 antonio-desktop NetworkManager: <info>  Activation (eth1) successful, device activated.
Jun 10 07:46:30 antonio-desktop NetworkManager: <info>  Activation (eth1) Stage 5 of 5 (IP Configure Commit) complete.
Jun 10 07:46:31 antonio-desktop kernel: [   17.168416] agpgart-amd64 0000:00:04.0: AGP 3.0 bridge
Jun 10 07:46:31 antonio-desktop kernel: [   17.168452] agpgart-amd64 0000:00:04.0: putting AGP V3 device into 8x mode
Jun 10 07:46:31 antonio-desktop kernel: [   17.168485] nvidia 0000:03:00.0: putting AGP V3 device into 8x mode
Jun 10 07:46:32 antonio-desktop acpid: client connected from 909[0:0]
Jun 10 07:46:32 antonio-desktop acpid: 1 client rule loaded
Jun 10 07:46:33 antonio-desktop noip2[1053]: v2.1.9 daemon started with NAT enabled
Jun 10 07:46:34 antonio-desktop ntpdate[1022]: step time server 91.189.94.4 offset 0.686047 sec
Jun 10 07:46:34 antonio-desktop gdm-session-worker[1066]: GLib-GObject-CRITICAL: g_value_get_boolean: assertion `G_VALUE_HOLDS_BOOLEAN (value)' failed
Jun 10 07:46:35 antonio-desktop noip2[1053]: aclbros.no-ip.com was already set to 84.18.26.30.
Jun 10 07:46:40 antonio-desktop kernel: [   26.708010] eth1: no IPv6 routers present
Jun 10 07:46:46 antonio-desktop acpid: client connected from 1259[110:117]
Jun 10 07:46:46 antonio-desktop acpid: 1 client rule loaded
Jun 10 07:46:57 antonio-desktop rtkit-daemon[1330]: Sucessfully called chroot.
Jun 10 07:46:57 antonio-desktop rtkit-daemon[1330]: Sucessfully dropped privileges.
Jun 10 07:46:57 antonio-desktop rtkit-daemon[1330]: Sucessfully limited resources.
Jun 10 07:46:57 antonio-desktop rtkit-daemon[1330]: Running.
Jun 10 07:46:57 antonio-desktop rtkit-daemon[1330]: Watchdog thread running.
Jun 10 07:46:57 antonio-desktop rtkit-daemon[1330]: Canary thread running.
Jun 10 07:46:58 antonio-desktop polkitd[1321]: started daemon version 0.96 using authority implementation `local' version `0.96'
Jun 10 07:46:59 antonio-desktop rtkit-daemon[1330]: Sucessfully made thread 1328 of process 1328 (n/a) owned by '1000' high priority at nice level -11.
Jun 10 07:46:59 antonio-desktop rtkit-daemon[1330]: Supervising 1 threads of 1 processes of 1 users.
Jun 10 07:47:00 antonio-desktop rtkit-daemon[1330]: Sucessfully made thread 1343 of process 1328 (n/a) owned by '1000' RT at priority 5.
Jun 10 07:47:00 antonio-desktop rtkit-daemon[1330]: Supervising 2 threads of 1 processes of 1 users.
Jun 10 07:47:00 antonio-desktop rtkit-daemon[1330]: Sucessfully made thread 1344 of process 1328 (n/a) owned by '1000' RT at priority 5.
Jun 10 07:47:00 antonio-desktop rtkit-daemon[1330]: Supervising 3 threads of 1 processes of 1 users.
Jun 10 07:47:00 antonio-desktop rtkit-daemon[1330]: Sucessfully made thread 1346 of process 1346 (n/a) owned by '1000' high priority at nice level -11.
Jun 10 07:47:00 antonio-desktop rtkit-daemon[1330]: Supervising 4 threads of 2 processes of 1 users.
Jun 10 07:47:00 antonio-desktop pulseaudio[1346]: pid.c: Daemon already running.
Jun 10 07:47:00 antonio-desktop rtkit-daemon[1330]: Sucessfully made thread 1348 of process 1348 (n/a) owned by '1000' high priority at nice level -11.
Jun 10 07:47:00 antonio-desktop rtkit-daemon[1330]: Supervising 4 threads of 2 processes of 1 users.
Jun 10 07:47:00 antonio-desktop pulseaudio[1348]: pid.c: Daemon already running.
Jun 10 07:47:21 antonio-desktop AptDaemon: INFO: Initializing daemon
Jun 10 07:47:34 antonio-desktop kernel: [   81.072021] Clocksource tsc unstable (delta = -272747753 ns)
Jun 10 07:51:26 antonio-desktop anacron[885]: Job `cron.daily' started
Jun 10 07:51:26 antonio-desktop anacron[1408]: Updated timestamp for job `cron.daily' to 2010-06-10
Jun 10 07:52:22 antonio-desktop AptDaemon: INFO: Quiting due to inactivity
Jun 10 07:52:22 antonio-desktop AptDaemon: INFO: Shutdown was requested
```My guess is that it's related to the anacron job, but I don't know how to fix it.

Thank you in advance,

faustus69.

---

### Post by Peter09 on 2010-06-10
I have seen this message due to a failing power supply (UPS power).
 
Jun 10 07:47:34 antonio-desktop kernel: [   81.072021] Clocksource tsc unstable (delta = -272747753 ns)

---

### Post by Peter09 on 2010-06-10
Also check your power management setup just incase you have a shutdown request after a small amount of inactivity.

---

### Post by CountMeIn on 2010-06-10
I also get this problem, seems strange that it never affected me until I installed ubuntu 10.04. Ubuntu 9.10 was fine. So I suspect software problem rather than hardware.

my /var/log/daemon.log had this:

Jun 10 11:17:20 mwlinux AptDaemon: INFO: Initializing daemon
Jun 10 11:23:20 mwlinux AptDaemon: INFO: Quiting due to inactivity
Jun 10 11:23:20 mwlinux AptDaemon: INFO: Shutdown was requested

---

### Post by Peter09 on 2010-06-10
Could be this?
 
[http://ubuntuforums.org/showthread.php?t=1491072](http://ubuntuforums.org/showthread.php?t=1491072)

---

### Post by faustus69 on 2010-06-10
Thanks everyone for your answers

> **Peter09 said:**
> I have seen this message due to a failing power supply (UPS power).
 
Jun 10 07:47:34 antonio-desktop kernel: [   81.072021] Clocksource tsc unstable (delta = -272747753 ns)
I've always had this error, but only means that because of CPU scaling (governor plugin) system have different lectures from the CPU speed.

> Also check your power management setup just incase you have a shutdown  request after a small amount of inactivity.     xfce4-power-manager is configured to never shutdown or suspend.

> Could be this?
 
[http://ubuntuforums.org/showthread.php?t=1491072](http://ubuntuforums.org/showthread.php?t=1491072)I checked that too, but my BIOS is updated.

I was thinking about anacron and Aptdaemon because it starts 1 minute before computer starts and lasts 5 minutes until quitting.

```
Jun 10 07:47:21 antonio-desktop AptDaemon: INFO: Initializing daemon
...
Jun 10 07:51:26 antonio-desktop anacron[885]: Job `cron.daily' started
...
Jun 10 07:52:22 antonio-desktop AptDaemon: INFO: Quiting due to inactivity
Jun 10 07:52:22 antonio-desktop AptDaemon: INFO: Shutdown was requested
```I don't know if as a workaround I could disable anacron or Aptdaemon to avoid this behaviour.

Thanks again,

faustus69.

---

