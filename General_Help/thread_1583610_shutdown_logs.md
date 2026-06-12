---
title: "shutdown logs"
date: 2010-09-28
forum: General Help
---

### Post by Gordonisnz on 2010-09-28
Hello.

This is a log of my /var/log/messages

All of this  log appears before my PC shuts down - PC is still on, But no screen. I cant press any keys to re-open the PC..


Does this log file make sense / Tell me why the Ubuntu PC is shutting off the screen ?

(any other logs I can check) ?

> 

Sep 28 17:48:21 gordon-desktop kernel: imklog 4.2.0, log source = /proc/kmsg started.
Sep 28 17:48:21 gordon-desktop rsyslogd: [origin software="rsyslogd" swVersion="4.2.0" x-pid="763" x-info="http://www.rsyslog.com"] (re)start
Sep 28 17:48:21 gordon-desktop rsyslogd: rsyslogd's groupid changed to 103
Sep 28 17:48:21 gordon-desktop rsyslogd: rsyslogd's userid changed to 102
Sep 28 17:48:21 gordon-desktop kernel: [    0.000000] Initializing cgroup subsys cpuset
Sep 28 17:48:21 gordon-desktop kernel: [    0.000000] Initializing cgroup subsys cpu
Sep 28 17:48:21 gordon-desktop kernel: [    0.000000] Linux version 2.6.32-24-generic (buildd@yellow) (gcc version 4.4.3 (Ubuntu 4.4.3-4ubuntu5) ) #43-Ubuntu SMP Thu Sep 16 14:58:24 UTC 2010 (Ubuntu 2.6.32-24.43-generic 2.6.32.15+drm33.5)
Sep 28 17:48:21 gordon-desktop kernel: [    0.000000] Command line: root=UUID=01455646-29d0-4357-8934-5cb634de5761 ro quiet splash 
Sep 28 17:48:21 gordon-desktop kernel: [    0.000000] KERNEL supported cpus:
Sep 28 17:48:21 gordon-desktop kernel: [    0.000000]   Intel GenuineIntel
Sep 28 17:48:21 gordon-desktop kernel: [    0.000000]   AMD AuthenticAMD
Sep 28 17:48:21 gordon-desktop kernel: [    0.000000]   Centaur CentaurHauls
Sep 28 17:48:21 gordon-desktop kernel: [    0.000000] BIOS-provided physical RAM map:
Sep 28 17:48:21 gordon-desktop kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
Sep 28 17:48:21 gordon-desktop kernel: [    0.000000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
Sep 28 17:48:21 gordon-desktop kernel: [    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
Sep 28 17:48:21 gordon-desktop kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 00000000cfee0000 (usable)
Sep 28 17:48:21 gordon-desktop kernel: [    0.000000]  BIOS-e820: 00000000cfee0000 - 00000000cfee3000 (ACPI NVS)
Sep 28 17:48:21 gordon-desktop kernel: [    0.000000]  BIOS-e820: 00000000cfee3000 - 00000000cfef0000 (ACPI data)
Sep 28 17:48:21 gordon-desktop kernel: [    0.000000]  BIOS-e820: 00000000cfef0000 - 00000000cff00000 (reserved)
Sep 28 17:48:21 gordon-desktop kernel: [    0.000000]  BIOS-e820: 00000000e0000000 - 00000000e4000000 (reserved)
Sep 28 17:48:21 gordon-desktop kernel: [    0.000000]  BIOS-e820: 00000000fec00000 - 0000000100000000 (reserved)
Sep 28 17:48:21 gordon-desktop kernel: [    0.000000]  BIOS-e820: 0000000100000000 - 0000000130000000 (usable)
Sep 28 17:48:21 gordon-desktop kernel: [    0.000000] DMI 2.4 present.
Sep 28 17:48:21 gordon-desktop kernel: [    0.000000] last_pfn = 0x130000 max_arch_pfn = 0x400000000
Sep 28 17:48:21 gordon-desktop kernel: [    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
Sep 28 17:48:21 gordon-desktop kernel: [    0.000000] last_pfn = 0xcfee0 max_arch_pfn = 0x400000000
Sep 28 17:48:21 gordon-desktop kernel: [    0.000000] Scanning 1 areas for low memory corruption
Sep 28 17:48:21 gordon-desktop kernel: [    0.000000] modified physical RAM map:
Sep 28 17:48:21 gordon-desktop kernel: [    0.000000]  modified: 0000000000000000 - 0000000000001000 (usable)
Sep 28 17:48:21 gordon-desktop kernel: [    0.000000]  modified: 0000000000001000 - 0000000000006000 (reserved)
Sep 28 17:48:21 gordon-desktop kernel: [    0.000000]  modified: 0000000000006000 - 000000000009f800 (usable)
Sep 28 17:48:21 gordon-desktop kernel: [    0.000000]  modified: 000000000009f800 - 00000000000a0000 (reserved)
Sep 28 17:48:21 gordon-desktop kernel: [    0.000000]  modified: 00000000000f0000 - 0000000000100000 (reserved)
Sep 28 17:48:21 gordon-desktop kernel: [    0.000000]  modified: 0000000000100000 - 00000000cfee0000 (usable)
Sep 28 17:48:21 gordon-desktop kernel: [    0.000000]  modified: 00000000cfee0000 - 00000000cfee3000 (ACPI NVS)
Sep 28 17:48:21 gordon-desktop kernel: [    0.000000]  modified: 00000000cfee3000 - 00000000cfef0000 (ACPI data)
Sep 28 17:48:21 gordon-desktop kernel: [    0.000000]  modified: 00000000cfef0000 - 00000000cff00000 (reserved)
Sep 28 17:48:21 gordon-desktop kernel: [    0.000000]  modified: 00000000e0000000 - 00000000e4000000 (reserved)
Sep 28 17:48:21 gordon-desktop kernel: [    0.000000]  modified: 00000000fec00000 - 0000000100000000 (reserved)
Sep 28 17:48:21 gordon-desktop kernel: [    0.000000]  modified: 0000000100000000 - 0000000130000000 (usable)
Sep 28 17:48:21 gordon-desktop kernel: [    0.000000] init_memory_mapping: 0000000000000000-00000000cfee0000
Sep 28 17:48:21 gordon-desktop kernel: [    0.000000] NX (Execute Disable) protection: active
Sep 28 17:48:21 gordon-desktop kernel: [    0.000000] init_memory_mapping: 0000000100000000-0000000130000000
Sep 28 17:48:21 gordon-desktop kernel: [    0.000000] NX (Execute Disable) protection: active
Sep 28 17:48:21 gordon-desktop kernel: [    0.000000] RAMDISK: 3780e000 - 37fefdc0
Sep 28 17:48:21 gordon-desktop kernel: [    0.000000] ACPI: RSDP 00000000000f6980 00014 (v00 GBT   )
Sep 28 17:48:21 gordon-desktop kernel: [    0.000000] ACPI: RSDT 00000000cfee3040 00038 (v01 GBT    GBTUACPI 42302E31 GBTU 01010101)
Sep 28 17:48:21 gordon-desktop kernel: [    0.000000] ACPI: FACP 00000000cfee30c0 00074 (v01 GBT    GBTUACPI 42302E31 GBTU 01010101)
Sep 28 17:48:21 gordon-desktop kernel: [    0.000000] ACPI: DSDT 00000000cfee3180 039B2 (v01 GBT    GBTUACPI 00001000 MSFT 0100000C)
Sep 28 17:48:21 gordon-desktop kernel: [    0.000000] ACPI: FACS 00000000cfee0000 00040
Sep 28 17:48:21 gordon-desktop kernel: [    0.000000] ACPI: HPET 00000000cfee6c80 00038 (v01 GBT    GBTUACPI 42302E31 GBTU 00000098)
Sep 28 17:48:21 gordon-desktop kernel: [    0.000000] ACPI: MCFG 00000000cfee6d00 0003C (v01 GBT    GBTUACPI 42302E31 GBTU 01010101)
Sep 28 17:48:21 gordon-desktop kernel: [    0.000000] ACPI: APIC 00000000cfee6b80 00084 (v01 GBT    GBTUACPI 42302E31 GBTU 01010101)
Sep 28 17:48:21 gordon-desktop kernel: [    0.000000] ACPI: SSDT 00000000cfee7660 003AB (v01  PmRef    CpuPm 00003000 INTL 20040311)
Sep 28 17:48:21 gordon-desktop kernel: [    0.000000] No NUMA configuration found
Sep 28 17:48:21 gordon-desktop kernel: [    0.000000] Faking a node at 0000000000000000-0000000130000000
Sep 28 17:48:21 gordon-desktop kernel: [    0.000000] Bootmem setup node 0 0000000000000000-0000000130000000
Sep 28 17:48:21 gordon-desktop kernel: [    0.000000]   NODE_DATA [000000000000d000 - 0000000000011fff]
Sep 28 17:48:21 gordon-desktop kernel: [    0.000000]   bootmap [0000000000012000 -  0000000000037fff] pages 26
Sep 28 17:48:21 gordon-desktop kernel: [    0.000000] (8 early reservations) ==> bootmem [0000000000 - 0130000000]
Sep 28 17:48:21 gordon-desktop kernel: [    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
Sep 28 17:48:21 gordon-desktop kernel: [    0.000000]   #1 [0000006000 - 0000008000]       TRAMPOLINE ==> [0000006000 - 0000008000]
Sep 28 17:48:21 gordon-desktop kernel: [    0.000000]   #2 [0001000000 - 0001a2fe64]    TEXT DATA BSS ==> [0001000000 - 0001a2fe64]
Sep 28 17:48:21 gordon-desktop kernel: [    0.000000]   #3 [003780e000 - 0037fefdc0]          RAMDISK ==> [003780e000 - 0037fefdc0]
Sep 28 17:48:21 gordon-desktop kernel: [    0.000000]   #4 [000009f800 - 0000100000]    BIOS reserved ==> [000009f800 - 0000100000]
Sep 28 17:48:21 gordon-desktop kernel: [    0.000000]   #5 [0001a30000 - 0001a300f6]              BRK ==> [0001a30000 - 0001a300f6]
Sep 28 17:48:21 gordon-desktop kernel: [    0.000000]   #6 [0000008000 - 000000c000]          PGTABLE ==> [0000008000 - 000000c000]
Sep 28 17:48:21 gordon-desktop kernel: [    0.000000]   #7 [000000c000 - 000000d000]          PGTABLE ==> [000000c000 - 000000d000]
Sep 28 17:48:21 gordon-desktop kernel: [    0.000000] found SMP MP-table at [ffff8800000f4f90] f4f90
Sep 28 17:48:21 gordon-desktop kernel: [    0.000000] Zone PFN ranges:
Sep 28 17:48:21 gordon-desktop kernel: [    0.000000]   DMA      0x00000000 -> 0x00001000
Sep 28 17:48:21 gordon-desktop kernel: [    0.000000]   DMA32    0x00001000 -> 0x00100000
Sep 28 17:48:21 gordon-desktop kernel: [    0.000000]   Normal   0x00100000 -> 0x00130000
Sep 28 17:48:21 gordon-desktop kernel: [    0.000000] Movable zone start PFN for each node
Sep 28 17:48:21 gordon-desktop kernel: [    0.000000] early_node_map[4] active PFN ranges
Sep 28 17:48:21 gordon-desktop kernel: [    0.000000]     0: 0x00000000 -> 0x00000001
Sep 28 17:48:21 gordon-desktop kernel: [    0.000000]     0: 0x00000006 -> 0x0000009f
Sep 28 17:48:21 gordon-desktop kernel: [    0.000000]     0: 0x00000100 -> 0x000cfee0
Sep 28 17:48:21 gordon-desktop kernel: [    0.000000]     0: 0x00100000 -> 0x00130000
Sep 28 17:48:21 gordon-desktop kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x408
Sep 28 17:48:21 gordon-desktop kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
Sep 28 17:48:21 gordon-desktop kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x02] enabled)
Sep 28 17:48:21 gordon-desktop kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x03] enabled)
Sep 28 17:48:21 gordon-desktop kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x01] enabled)
Sep 28 17:48:21 gordon-desktop kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] dfl dfl lint[0x1])
Sep 28 17:48:21 gordon-desktop kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] dfl dfl lint[0x1])
Sep 28 17:48:21 gordon-desktop kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x02] dfl dfl lint[0x1])
Sep 28 17:48:21 gordon-desktop kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x03] dfl dfl lint[0x1])
Sep 28 17:48:21 gordon-desktop kernel: [    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
Sep 28 17:48:21 gordon-desktop kernel: [    0.000000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-23
Sep 28 17:48:21 gordon-desktop kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
Sep 28 17:48:21 gordon-desktop kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
Sep 28 17:48:21 gordon-desktop kernel: [    0.000000] Using ACPI (MADT) for SMP configuration information
Sep 28 17:48:21 gordon-desktop kernel: [    0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000
Sep 28 17:48:21 gordon-desktop kernel: [    0.000000] SMP: Allowing 4 CPUs, 0 hotplug CPUs
Sep 28 17:48:21 gordon-desktop kernel: [    0.000000] PM: Registered nosave memory: 0000000000001000 - 0000000000006000
Sep 28 17:48:21 gordon-desktop kernel: [    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
Sep 28 17:48:21 gordon-desktop kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000f0000
Sep 28 17:48:21 gordon-desktop kernel: [    0.000000] PM: Registered nosave memory: 00000000000f0000 - 0000000000100000
Sep 28 17:48:21 gordon-desktop kernel: [    0.000000] PM: Registered nosave memory: 00000000cfee0000 - 00000000cfee3000
Sep 28 17:48:21 gordon-desktop kernel: [    0.000000] PM: Registered nosave memory: 00000000cfee3000 - 00000000cfef0000
Sep 28 17:48:21 gordon-desktop kernel: [    0.000000] PM: Registered nosave memory: 00000000cfef0000 - 00000000cff00000
Sep 28 17:48:21 gordon-desktop kernel: [    0.000000] PM: Registered nosave memory: 00000000cff00000 - 00000000e0000000
Sep 28 17:48:21 gordon-desktop kernel: [    0.000000] PM: Registered nosave memory: 00000000e0000000 - 00000000e4000000
Sep 28 17:48:21 gordon-desktop kernel: [    0.000000] PM: Registered nosave memory: 00000000e4000000 - 00000000fec00000
Sep 28 17:48:21 gordon-desktop kernel: [    0.000000] PM: Registered nosave memory: 00000000fec00000 - 0000000100000000
Sep 28 17:48:21 gordon-desktop kernel: [    0.000000] Allocating PCI resources starting at e4000000 (gap: e4000000:1ac00000)
Sep 28 17:48:21 gordon-desktop kernel: [    0.000000] Booting paravirtualized kernel on bare hardware
Sep 28 17:48:21 gordon-desktop kernel: [    0.000000] NR_CPUS:64 nr_cpumask_bits:64 nr_cpu_ids:4 nr_node_ids:1
Sep 28 17:48:21 gordon-desktop kernel: [    0.000000] PERCPU: Embedded 30 pages/cpu @ffff880028200000 s91544 r8192 d23144 u524288
Sep 28 17:48:21 gordon-desktop kernel: [    0.000000] pcpu-alloc: s91544 r8192 d23144 u524288 alloc=1*2097152
Sep 28 17:48:21 gordon-desktop kernel: [    0.000000] pcpu-alloc: [0] 0 1 2 3 
Sep 28 17:48:21 gordon-desktop kernel: [    0.000000] Built 1 zonelists in Node order, mobility grouping on.  Total pages: 1031058
Sep 28 17:48:21 gordon-desktop kernel: [    0.000000] Policy zone: Normal
Sep 28 17:48:21 gordon-desktop kernel: [    0.000000] Kernel command line: root=UUID=01455646-29d0-4357-8934-5cb634de5761 ro quiet splash 
Sep 28 17:48:21 gordon-desktop kernel: [    0.000000] PID hash table entries: 4096 (order: 3, 32768 bytes)
Sep 28 17:48:21 gordon-desktop kernel: [    0.000000] Initializing CPU#0
Sep 28 17:48:21 gordon-desktop kernel: [    0.000000] xsave/xrstor: enabled xstate_bv 0x3, cntxt size 0x240
Sep 28 17:48:21 gordon-desktop kernel: [    0.000000] Checking aperture...
Sep 28 17:48:21 gordon-desktop kernel: [    0.000000] No AGP bridge found
Sep 28 17:48:21 gordon-desktop kernel: [    0.000000] PCI-DMA: Using software bounce buffering for IO (SWIOTLB)
Sep 28 17:48:21 gordon-desktop kernel: [    0.000000] Placing 64MB software IO TLB between ffff880020000000 - ffff880024000000
Sep 28 17:48:21 gordon-desktop kernel: [    0.000000] software IO TLB at phys 0x20000000 - 0x24000000
Sep 28 17:48:21 gordon-desktop kernel: [    0.000000] Memory: 4048148k/4980736k available (5422k kernel code, 787992k absent, 144596k reserved, 2979k data, 880k init)
Sep 28 17:48:21 gordon-desktop kernel: [    0.000000] SLUB: Genslabs=14, HWalign=64, Order=0-3, MinObjects=0, CPUs=4, Nodes=1
Sep 28 17:48:21 gordon-desktop kernel: [    0.000000] Hierarchical RCU implementation.
Sep 28 17:48:21 gordon-desktop kernel: [    0.000000] NR_IRQS:4352 nr_irqs:440
Sep 28 17:48:21 gordon-desktop kernel: [    0.000000] Console: colour VGA+ 80x25
Sep 28 17:48:21 gordon-desktop kernel: [    0.000000] console [tty0] enabled
Sep 28 17:48:21 gordon-desktop kernel: [    0.000000] allocated 41943040 bytes of page_cgroup
Sep 28 17:48:21 gordon-desktop kernel: [    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
Sep 28 17:48:21 gordon-desktop kernel: [    0.000000] HPET: 3 timers in total, 0 timers will be used for per-cpu timer
Sep 28 17:48:21 gordon-desktop kernel: [    0.000000] Fast TSC calibration using PIT
Sep 28 17:48:21 gordon-desktop kernel: [    0.000000] Detected 2333.611 MHz processor.
Sep 28 17:48:21 gordon-desktop kernel: [    0.000006] Calibrating delay loop (skipped), value calculated using timer frequency.. 4667.22 BogoMIPS (lpj=23336110)
Sep 28 17:48:21 gordon-desktop kernel: [    0.000030] Security Framework initialized
Sep 28 17:48:21 gordon-desktop kernel: [    0.000048] AppArmor: AppArmor initialized
Sep 28 17:48:21 gordon-desktop kernel: [    0.010287] Dentry cache hash table entries: 524288 (order: 10, 4194304 bytes)
Sep 28 17:48:21 gordon-desktop kernel: [    0.011993] Inode-cache hash table entries: 262144 (order: 9, 2097152 bytes)
Sep 28 17:48:21 gordon-desktop kernel: [    0.012747] Mount-cache hash table entries: 256
Sep 28 17:48:21 gordon-desktop kernel: [    0.012885] Initializing cgroup subsys ns
Sep 28 17:48:21 gordon-desktop kernel: [    0.012891] Initializing cgroup subsys cpuacct
Sep 28 17:48:21 gordon-desktop kernel: [    0.012894] Initializing cgroup subsys memory
Sep 28 17:48:21 gordon-desktop kernel: [    0.012900] Initializing cgroup subsys devices
Sep 28 17:48:21 gordon-desktop kernel: [    0.012903] Initializing cgroup subsys freezer
Sep 28 17:48:21 gordon-desktop kernel: [    0.012904] Initializing cgroup subsys net_cls
Sep 28 17:48:21 gordon-desktop kernel: [    0.012923] CPU: L1 I cache: 32K, L1 D cache: 32K
Sep 28 17:48:21 gordon-desktop kernel: [    0.012925] CPU: L2 cache: 2048K
Sep 28 17:48:21 gordon-desktop kernel: [    0.012928] CPU 0/0x0 -> Node 0
Sep 28 17:48:21 gordon-desktop kernel: [    0.012930] CPU: Physical Processor ID: 0
Sep 28 17:48:21 gordon-desktop kernel: [    0.012931] CPU: Processor Core ID: 0
Sep 28 17:48:21 gordon-desktop kernel: [    0.012934] mce: CPU supports 6 MCE banks
Sep 28 17:48:21 gordon-desktop kernel: [    0.012942] CPU0: Thermal monitoring enabled (TM2)
Sep 28 17:48:21 gordon-desktop kernel: [    0.012947] using mwait in idle threads.
Sep 28 17:48:21 gordon-desktop kernel: [    0.012948] Performance Events: Core2 events, Intel PMU driver.
Sep 28 17:48:21 gordon-desktop kernel: [    0.012954] ... version:                2
Sep 28 17:48:21 gordon-desktop kernel: [    0.012955] ... bit width:              40
Sep 28 17:48:21 gordon-desktop kernel: [    0.012957] ... generic registers:      2
Sep 28 17:48:21 gordon-desktop kernel: [    0.012958] ... value mask:             000000ffffffffff
Sep 28 17:48:21 gordon-desktop kernel: [    0.012960] ... max period:             000000007fffffff
Sep 28 17:48:21 gordon-desktop kernel: [    0.012961] ... fixed-purpose events:   3
Sep 28 17:48:21 gordon-desktop kernel: [    0.012963] ... event mask:             0000000700000003
Sep 28 17:48:21 gordon-desktop kernel: [    0.015422] ACPI: Core revision 20090903
Sep 28 17:48:21 gordon-desktop kernel: [    0.020022] ftrace: converting mcount calls to 0f 1f 44 00 00
Sep 28 17:48:21 gordon-desktop kernel: [    0.020030] ftrace: allocating 22529 entries in 89 pages
Sep 28 17:48:21 gordon-desktop kernel: [    0.030052] Setting APIC routing to flat
Sep 28 17:48:21 gordon-desktop kernel: [    0.030352] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
Sep 28 17:48:21 gordon-desktop kernel: [    0.130088] CPU0: Intel(R) Core(TM)2 Quad CPU    Q8200  @ 2.33GHz stepping 0a
Sep 28 17:48:21 gordon-desktop kernel: [    0.140000] Booting processor 1 APIC 0x2 ip 0x6000
Sep 28 17:48:21 gordon-desktop kernel: [    0.010000] Initializing CPU#1
Sep 28 17:48:21 gordon-desktop kernel: [    0.010000] CPU: L1 I cache: 32K, L1 D cache: 32K
Sep 28 17:48:21 gordon-desktop kernel: [    0.010000] CPU: L2 cache: 2048K
Sep 28 17:48:21 gordon-desktop kernel: [    0.010000] CPU 1/0x2 -> Node 0
Sep 28 17:48:21 gordon-desktop kernel: [    0.010000] CPU: Physical Processor ID: 0
Sep 28 17:48:21 gordon-desktop kernel: [    0.010000] CPU: Processor Core ID: 2
Sep 28 17:48:21 gordon-desktop kernel: [    0.010000] CPU1: Thermal monitoring enabled (TM2)
Sep 28 17:48:21 gordon-desktop kernel: [    0.290059] CPU1: Intel(R) Core(TM)2 Quad CPU    Q8200  @ 2.33GHz stepping 0a
Sep 28 17:48:21 gordon-desktop kernel: [    0.290066] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
Sep 28 17:48:21 gordon-desktop kernel: [    0.300070] Booting processor 2 APIC 0x3 ip 0x6000
Sep 28 17:48:21 gordon-desktop kernel: [    0.010000] Initializing CPU#2
Sep 28 17:48:21 gordon-desktop kernel: [    0.010000] CPU: L1 I cache: 32K, L1 D cache: 32K
Sep 28 17:48:21 gordon-desktop kernel: [    0.010000] CPU: L2 cache: 2048K
Sep 28 17:48:21 gordon-desktop kernel: [    0.010000] CPU 2/0x3 -> Node 0
Sep 28 17:48:21 gordon-desktop kernel: [    0.010000] CPU: Physical Processor ID: 0
Sep 28 17:48:21 gordon-desktop kernel: [    0.010000] CPU: Processor Core ID: 3
Sep 28 17:48:21 gordon-desktop kernel: [    0.010000] CPU2: Thermal monitoring enabled (TM2)
Sep 28 17:48:21 gordon-desktop kernel: [    0.460076] CPU2: Intel(R) Core(TM)2 Quad CPU    Q8200  @ 2.33GHz stepping 0a
Sep 28 17:48:21 gordon-desktop kernel: [    0.460082] checking TSC synchronization [CPU#0 -> CPU#2]: passed.
Sep 28 17:48:21 gordon-desktop kernel: [    0.470071] Booting processor 3 APIC 0x1 ip 0x6000
Sep 28 17:48:21 gordon-desktop kernel: [    0.010000] Initializing CPU#3
Sep 28 17:48:21 gordon-desktop kernel: [    0.010000] CPU: L1 I cache: 32K, L1 D cache: 32K
Sep 28 17:48:21 gordon-desktop kernel: [    0.010000] CPU: L2 cache: 2048K
Sep 28 17:48:21 gordon-desktop kernel: [    0.010000] CPU 3/0x1 -> Node 0
Sep 28 17:48:21 gordon-desktop kernel: [    0.010000] CPU: Physical Processor ID: 0
Sep 28 17:48:21 gordon-desktop kernel: [    0.010000] CPU: Processor Core ID: 1
Sep 28 17:48:21 gordon-desktop kernel: [    0.010000] CPU3: Thermal monitoring enabled (TM2)
Sep 28 17:48:21 gordon-desktop kernel: [    0.630096] CPU3: Intel(R) Core(TM)2 Quad CPU    Q8200  @ 2.33GHz stepping 0a
Sep 28 17:48:21 gordon-desktop kernel: [    0.630106] checking TSC synchronization [CPU#0 -> CPU#3]: passed.
Sep 28 17:48:21 gordon-desktop kernel: [    0.640020] Brought up 4 CPUs
Sep 28 17:48:21 gordon-desktop kernel: [    0.640022] Total of 4 processors activated (18666.94 BogoMIPS).
Sep 28 17:48:21 gordon-desktop kernel: [    0.641488] devtmpfs: initialized
Sep 28 17:48:21 gordon-desktop kernel: [    0.641488] regulator: core version 0.5
Sep 28 17:48:21 gordon-desktop kernel: [    0.641488] Time:  4:48:03  Date: 09/28/10
Sep 28 17:48:21 gordon-desktop kernel: [    0.641488] NET: Registered protocol family 16
Sep 28 17:48:21 gordon-desktop kernel: [    0.641488] Trying to unpack rootfs image as initramfs...
Sep 28 17:48:21 gordon-desktop kernel: [    0.641488] ACPI: bus type pci registered
Sep 28 17:48:21 gordon-desktop kernel: [    0.641488] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 63
Sep 28 17:48:21 gordon-desktop kernel: [    0.641488] PCI: MCFG area at e0000000 reserved in E820
Sep 28 17:48:21 gordon-desktop kernel: [    0.641938] PCI: Using MMCONFIG at e0000000 - e3ffffff
Sep 28 17:48:21 gordon-desktop kernel: [    0.641940] PCI: Using configuration type 1 for base access
Sep 28 17:48:21 gordon-desktop kernel: [    0.642579] bio: create slab <bio-0> at 0
Sep 28 17:48:21 gordon-desktop kernel: [    0.644806] ACPI: Interpreter enabled
Sep 28 17:48:21 gordon-desktop kernel: [    0.644813] ACPI: (supports S0 S3 S4 S5)
Sep 28 17:48:21 gordon-desktop kernel: [    0.644832] ACPI: Using IOAPIC for interrupt routing
Sep 28 17:48:21 gordon-desktop kernel: [    0.653700] ACPI: No dock devices found.
Sep 28 17:48:21 gordon-desktop kernel: [    0.653784] ACPI: PCI Root Bridge [PCI0] (0000:00)
Sep 28 17:48:21 gordon-desktop kernel: [    0.653877] pci 0000:00:01.0: PME# supported from D0 D3hot D3cold
Sep 28 17:48:21 gordon-desktop kernel: [    0.653880] pci 0000:00:01.0: PME# disabled
Sep 28 17:48:21 gordon-desktop kernel: [    0.653967] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
Sep 28 17:48:21 gordon-desktop kernel: [    0.653970] pci 0000:00:1b.0: PME# disabled
Sep 28 17:48:21 gordon-desktop kernel: [    0.654025] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
Sep 28 17:48:21 gordon-desktop kernel: [    0.654028] pci 0000:00:1c.0: PME# disabled
Sep 28 17:48:21 gordon-desktop kernel: [    0.654083] pci 0000:00:1c.3: PME# supported from D0 D3hot D3cold
Sep 28 17:48:21 gordon-desktop kernel: [    0.654086] pci 0000:00:1c.3: PME# disabled
Sep 28 17:48:21 gordon-desktop kernel: [    0.654432] pci 0000:00:1f.0: quirk: region 0400-047f claimed by ICH6 ACPI/GPIO/TCO
Sep 28 17:48:21 gordon-desktop kernel: [    0.654435] pci 0000:00:1f.0: quirk: region 0480-04bf claimed by ICH6 GPIO
Sep 28 17:48:21 gordon-desktop kernel: [    0.654438] pci 0000:00:1f.0: ICH7 LPC Generic IO decode 1 PIO at 0800 (mask 000f)
Sep 28 17:48:21 gordon-desktop kernel: [    0.654441] pci 0000:00:1f.0: ICH7 LPC Generic IO decode 2 PIO at 0290 (mask 000f)
Sep 28 17:48:21 gordon-desktop kernel: [    0.654522] pci 0000:00:1f.2: PME# supported from D3hot
Sep 28 17:48:21 gordon-desktop kernel: [    0.654525] pci 0000:00:1f.2: PME# disabled
Sep 28 17:48:21 gordon-desktop kernel: [    0.654850] pci 0000:03:00.0: PME# supported from D0 D1 D2 D3hot D3cold
Sep 28 17:48:21 gordon-desktop kernel: [    0.654854] pci 0000:03:00.0: PME# disabled
Sep 28 17:48:21 gordon-desktop kernel: [    0.654956] pci 0000:00:1e.0: transparent bridge
Sep 28 17:48:21 gordon-desktop kernel: [    0.663907] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 9 *10 11 12 14 15)
Sep 28 17:48:21 gordon-desktop kernel: [    0.663986] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
Sep 28 17:48:21 gordon-desktop kernel: [    0.664064] ACPI: PCI Interrupt Link [LNKC] (IRQs *3 4 5 6 7 9 10 11 12 14 15)
Sep 28 17:48:21 gordon-desktop kernel: [    0.664142] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)
Sep 28 17:48:21 gordon-desktop kernel: [    0.664219] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
Sep 28 17:48:21 gordon-desktop kernel: [    0.664297] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
Sep 28 17:48:21 gordon-desktop kernel: [    0.664376] ACPI: PCI Interrupt Link [LNK0] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
Sep 28 17:48:21 gordon-desktop kernel: [    0.664455] ACPI: PCI Interrupt Link [LNK1] (IRQs 3 4 *5 6 7 9 10 11 12 14 15)
Sep 28 17:48:21 gordon-desktop kernel: [    0.664555] vgaarb: device added: PCI:0000:01:00.0,decodes=io+mem,owns=io+mem,locks=none
Sep 28 17:48:21 gordon-desktop kernel: [    0.664558] vgaarb: loaded
Sep 28 17:48:21 gordon-desktop kernel: [    0.664655] SCSI subsystem initialized
Sep 28 17:48:21 gordon-desktop kernel: [    0.664689] usbcore: registered new interface driver usbfs
Sep 28 17:48:21 gordon-desktop kernel: [    0.664689] usbcore: registered new interface driver hub
Sep 28 17:48:21 gordon-desktop kernel: [    0.664689] usbcore: registered new device driver usb
Sep 28 17:48:21 gordon-desktop kernel: [    0.664689] ACPI: WMI: Mapper loaded
Sep 28 17:48:21 gordon-desktop kernel: [    0.664689] PCI: Using ACPI for IRQ routing
Sep 28 17:48:21 gordon-desktop kernel: [    0.664689] NetLabel: Initializing
Sep 28 17:48:21 gordon-desktop kernel: [    0.664689] NetLabel:  domain hash size = 128
Sep 28 17:48:21 gordon-desktop kernel: [    0.664689] NetLabel:  protocols = UNLABELED CIPSOv4
Sep 28 17:48:21 gordon-desktop kernel: [    0.664689] NetLabel:  unlabeled traffic allowed by default
Sep 28 17:48:21 gordon-desktop kernel: [    0.664689] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
Sep 28 17:48:21 gordon-desktop kernel: [    0.664689] hpet0: 3 comparators, 64-bit 14.318180 MHz counter
Sep 28 17:48:21 gordon-desktop kernel: [    0.680012] Switching to clocksource tsc
Sep 28 17:48:21 gordon-desktop kernel: [    0.681717] AppArmor: AppArmor Filesystem Enabled
Sep 28 17:48:21 gordon-desktop kernel: [    0.681728] pnp: PnP ACPI init
Sep 28 17:48:21 gordon-desktop kernel: [    0.681738] ACPI: bus type pnp registered
Sep 28 17:48:21 gordon-desktop kernel: [    0.683937] pnp: PnP ACPI: found 14 devices
Sep 28 17:48:21 gordon-desktop kernel: [    0.683939] ACPI: ACPI bus type pnp unregistered
Sep 28 17:48:21 gordon-desktop kernel: [    0.683948] system 00:01: ioport range 0x4d0-0x4d1 has been reserved
Sep 28 17:48:21 gordon-desktop kernel: [    0.683950] system 00:01: ioport range 0x290-0x29f has been reserved
Sep 28 17:48:21 gordon-desktop kernel: [    0.683953] system 00:01: ioport range 0x800-0x87f has been reserved
Sep 28 17:48:21 gordon-desktop kernel: [    0.683955] system 00:01: ioport range 0x290-0x294 has been reserved
Sep 28 17:48:21 gordon-desktop kernel: [    0.683958] system 00:01: ioport range 0x880-0x88f has been reserved
Sep 28 17:48:21 gordon-desktop kernel: [    0.683967] system 00:0a: ioport range 0x400-0x4bf could not be reserved
Sep 28 17:48:21 gordon-desktop kernel: [    0.683972] system 00:0b: iomem range 0xe0000000-0xe3ffffff has been reserved
Sep 28 17:48:21 gordon-desktop kernel: [    0.683977] system 00:0c: iomem range 0xcd200-0xcffff has been reserved
Sep 28 17:48:21 gordon-desktop kernel: [    0.683979] system 00:0c: iomem range 0xf0000-0xf7fff could not be reserved
Sep 28 17:48:21 gordon-desktop kernel: [    0.683982] system 00:0c: iomem range 0xf8000-0xfbfff could not be reserved
Sep 28 17:48:21 gordon-desktop kernel: [    0.683984] system 00:0c: iomem range 0xfc000-0xfffff could not be reserved
Sep 28 17:48:21 gordon-desktop kernel: [    0.683987] system 00:0c: iomem range 0xcfee0000-0xcfefffff could not be reserved
Sep 28 17:48:21 gordon-desktop kernel: [    0.683990] system 00:0c: iomem range 0x0-0x9ffff could not be reserved
Sep 28 17:48:21 gordon-desktop kernel: [    0.683992] system 00:0c: iomem range 0x100000-0xcfedffff could not be reserved
Sep 28 17:48:21 gordon-desktop kernel: [    0.683995] system 00:0c: iomem range 0xfec00000-0xfec00fff could not be reserved
Sep 28 17:48:21 gordon-desktop kernel: [    0.683998] system 00:0c: iomem range 0xfed13000-0xfed1dfff has been reserved
Sep 28 17:48:21 gordon-desktop kernel: [    0.684000] system 00:0c: iomem range 0xfed20000-0xfed8ffff has been reserved
Sep 28 17:48:21 gordon-desktop kernel: [    0.684003] system 00:0c: iomem range 0xfee00000-0xfee00fff has been reserved
Sep 28 17:48:21 gordon-desktop kernel: [    0.684005] system 00:0c: iomem range 0xffb00000-0xffb7ffff has been reserved
Sep 28 17:48:21 gordon-desktop kernel: [    0.684008] system 00:0c: iomem range 0xfff00000-0xffffffff has been reserved
Sep 28 17:48:21 gordon-desktop kernel: [    0.684010] system 00:0c: iomem range 0xe0000-0xeffff has been reserved
Sep 28 17:48:21 gordon-desktop kernel: [    0.688699] pci 0000:00:01.0: PCI bridge, secondary bus 0000:01
Sep 28 17:48:21 gordon-desktop kernel: [    0.688702] pci 0000:00:01.0:   IO window: 0xc000-0xcfff
Sep 28 17:48:21 gordon-desktop kernel: [    0.688705] pci 0000:00:01.0:   MEM window: 0xe4000000-0xe7ffffff
Sep 28 17:48:21 gordon-desktop kernel: [    0.688708] pci 0000:00:01.0:   PREFETCH window: 0x000000d0000000-0x000000dfffffff
Sep 28 17:48:21 gordon-desktop kernel: [    0.688712] pci 0000:00:1c.0: PCI bridge, secondary bus 0000:02
Sep 28 17:48:21 gordon-desktop kernel: [    0.688715] pci 0000:00:1c.0:   IO window: 0xb000-0xbfff
Sep 28 17:48:21 gordon-desktop kernel: [    0.688719] pci 0000:00:1c.0:   MEM window: 0xe9200000-0xe93fffff
Sep 28 17:48:21 gordon-desktop kernel: [    0.688722] pci 0000:00:1c.0:   PREFETCH window: 0x000000e9400000-0x000000e95fffff
Sep 28 17:48:21 gordon-desktop kernel: [    0.688727] pci 0000:00:1c.3: PCI bridge, secondary bus 0000:03
Sep 28 17:48:21 gordon-desktop kernel: [    0.688730] pci 0000:00:1c.3:   IO window: 0xd000-0xdfff
Sep 28 17:48:21 gordon-desktop kernel: [    0.688734] pci 0000:00:1c.3:   MEM window: 0xe8000000-0xe8ffffff
Sep 28 17:48:21 gordon-desktop kernel: [    0.688737] pci 0000:00:1c.3:   PREFETCH window: 0x000000e9000000-0x000000e90fffff
Sep 28 17:48:21 gordon-desktop kernel: [    0.688742] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:04
Sep 28 17:48:21 gordon-desktop kernel: [    0.688745] pci 0000:00:1e.0:   IO window: 0xa000-0xafff
Sep 28 17:48:21 gordon-desktop kernel: [    0.688749] pci 0000:00:1e.0:   MEM window: disabled
Sep 28 17:48:21 gordon-desktop kernel: [    0.688752] pci 0000:00:1e.0:   PREFETCH window: disabled
Sep 28 17:48:21 gordon-desktop kernel: [    0.688767] pci 0000:00:01.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Sep 28 17:48:21 gordon-desktop kernel: [    0.688777] pci 0000:00:1c.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Sep 28 17:48:21 gordon-desktop kernel: [    0.688791] pci 0000:00:1c.3: PCI INT D -> GSI 19 (level, low) -> IRQ 19
Sep 28 17:48:21 gordon-desktop kernel: [    0.688862] NET: Registered protocol family 2
Sep 28 17:48:21 gordon-desktop kernel: [    0.689008] IP route cache hash table entries: 131072 (order: 8, 1048576 bytes)
Sep 28 17:48:21 gordon-desktop kernel: [    0.690065] TCP established hash table entries: 524288 (order: 11, 8388608 bytes)
Sep 28 17:48:21 gordon-desktop kernel: [    0.693381] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
Sep 28 17:48:21 gordon-desktop kernel: [    0.693806] TCP: Hash tables configured (established 524288 bind 65536)
Sep 28 17:48:21 gordon-desktop kernel: [    0.693809] TCP reno registered
Sep 28 17:48:21 gordon-desktop kernel: [    0.693921] NET: Registered protocol family 1
Sep 28 17:48:21 gordon-desktop kernel: [    0.694330] Scanning for low memory corruption every 60 seconds
Sep 28 17:48:21 gordon-desktop kernel: [    0.694468] audit: initializing netlink socket (disabled)
Sep 28 17:48:21 gordon-desktop kernel: [    0.694478] type=2000 audit(1285649282.689:1): initialized
Sep 28 17:48:21 gordon-desktop kernel: [    0.703209] HugeTLB registered 2 MB page size, pre-allocated 0 pages
Sep 28 17:48:21 gordon-desktop kernel: [    0.704534] VFS: Disk quotas dquot_6.5.2
Sep 28 17:48:21 gordon-desktop kernel: [    0.704583] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
Sep 28 17:48:21 gordon-desktop kernel: [    0.705102] fuse init (API version 7.13)
Sep 28 17:48:21 gordon-desktop kernel: [    0.705172] msgmni has been set to 7906
Sep 28 17:48:21 gordon-desktop kernel: [    0.705434] alg: No test for stdrng (krng)
Sep 28 17:48:21 gordon-desktop kernel: [    0.705495] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
Sep 28 17:48:21 gordon-desktop kernel: [    0.705498] io scheduler noop registered
Sep 28 17:48:21 gordon-desktop kernel: [    0.705499] io scheduler anticipatory registered
Sep 28 17:48:21 gordon-desktop kernel: [    0.705501] io scheduler deadline registered
Sep 28 17:48:21 gordon-desktop kernel: [    0.705532] io scheduler cfq registered (default)
Sep 28 17:48:21 gordon-desktop kernel: [    0.705923] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Sep 28 17:48:21 gordon-desktop kernel: [    0.705986] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
Sep 28 17:48:21 gordon-desktop kernel: [    0.706070] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0
Sep 28 17:48:21 gordon-desktop kernel: [    0.706074] ACPI: Power Button [PWRB]
Sep 28 17:48:21 gordon-desktop kernel: [    0.706119] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
Sep 28 17:48:21 gordon-desktop kernel: [    0.706122] ACPI: Power Button [PWRF]
Sep 28 17:48:21 gordon-desktop kernel: [    0.706515] ACPI: SSDT 00000000cfee6d80 0022A (v01  PmRef  Cpu0Ist 00003000 INTL 20040311)
Sep 28 17:48:21 gordon-desktop kernel: [    0.706656] processor LNXCPU:00: registered as cooling_device0
Sep 28 17:48:21 gordon-desktop kernel: [    0.706839] ACPI: SSDT 00000000cfee7240 00152 (v01  PmRef  Cpu1Ist 00003000 INTL 20040311)
Sep 28 17:48:21 gordon-desktop kernel: [    0.707037] processor LNXCPU:01: registered as cooling_device1
Sep 28 17:48:21 gordon-desktop kernel: [    0.707287] ACPI: SSDT 00000000cfee73a0 00152 (v01  PmRef  Cpu2Ist 00003000 INTL 20040311)
Sep 28 17:48:21 gordon-desktop kernel: [    0.707445] processor LNXCPU:02: registered as cooling_device2
Sep 28 17:48:21 gordon-desktop kernel: [    0.707645] ACPI: SSDT 00000000cfee7500 00152 (v01  PmRef  Cpu3Ist 00003000 INTL 20040311)
Sep 28 17:48:21 gordon-desktop kernel: [    0.707832] processor LNXCPU:03: registered as cooling_device3
Sep 28 17:48:21 gordon-desktop kernel: [    0.710450] Linux agpgart interface v0.103
Sep 28 17:48:21 gordon-desktop kernel: [    0.710477] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
Sep 28 17:48:21 gordon-desktop kernel: [    0.710566] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Sep 28 17:48:21 gordon-desktop kernel: [    0.710833] 00:07: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Sep 28 17:48:21 gordon-desktop kernel: [    0.711755] brd: module loaded
Sep 28 17:48:21 gordon-desktop kernel: [    0.712144] loop: module loaded
Sep 28 17:48:21 gordon-desktop kernel: [    0.712214] input: Macintosh mouse button emulation as /devices/virtual/input/input2
Sep 28 17:48:21 gordon-desktop kernel: [    0.712300] ata_piix 0000:00:1f.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
Sep 28 17:48:21 gordon-desktop kernel: [    0.712304] ata_piix 0000:00:1f.2: MAP [ P0 P2 IDE IDE ]
Sep 28 17:48:21 gordon-desktop kernel: [    0.712402] scsi0 : ata_piix
Sep 28 17:48:21 gordon-desktop kernel: [    0.712459] scsi1 : ata_piix
Sep 28 17:48:21 gordon-desktop kernel: [    0.713016] ata1: SATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xf000 irq 14
Sep 28 17:48:21 gordon-desktop kernel: [    0.713018] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xf008 irq 15
Sep 28 17:48:21 gordon-desktop kernel: [    0.713292] Fixed MDIO Bus: probed
Sep 28 17:48:21 gordon-desktop kernel: [    0.713321] PPP generic driver version 2.4.2
Sep 28 17:48:21 gordon-desktop kernel: [    0.713353] tun: Universal TUN/TAP device driver, 1.6
Sep 28 17:48:21 gordon-desktop kernel: [    0.713354] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
Sep 28 17:48:21 gordon-desktop kernel: [    0.713418] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
Sep 28 17:48:21 gordon-desktop kernel: [    0.713441] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23
Sep 28 17:48:21 gordon-desktop kernel: [    0.713459] ehci_hcd 0000:00:1d.7: EHCI Host Controller
Sep 28 17:48:21 gordon-desktop kernel: [    0.713493] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 1
Sep 28 17:48:21 gordon-desktop kernel: [    0.713511] ehci_hcd 0000:00:1d.7: using broken periodic workaround
Sep 28 17:48:21 gordon-desktop kernel: [    0.717387] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xe9104000
Sep 28 17:48:21 gordon-desktop kernel: [    0.739788] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
Sep 28 17:48:21 gordon-desktop kernel: [    0.739870] usb usb1: configuration #1 chosen from 1 choice
Sep 28 17:48:21 gordon-desktop kernel: [    0.739893] hub 1-0:1.0: USB hub found
Sep 28 17:48:21 gordon-desktop kernel: [    0.739901] hub 1-0:1.0: 8 ports detected
Sep 28 17:48:21 gordon-desktop kernel: [    0.739953] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
Sep 28 17:48:21 gordon-desktop kernel: [    0.739964] uhci_hcd: USB Universal Host Controller Interface driver
Sep 28 17:48:21 gordon-desktop kernel: [    0.739982] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
Sep 28 17:48:21 gordon-desktop kernel: [    0.739990] uhci_hcd 0000:00:1d.0: UHCI Host Controller
Sep 28 17:48:21 gordon-desktop kernel: [    0.740018] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
Sep 28 17:48:21 gordon-desktop kernel: [    0.740040] uhci_hcd 0000:00:1d.0: irq 23, io base 0x0000e000
Sep 28 17:48:21 gordon-desktop kernel: [    0.740111] usb usb2: configuration #1 chosen from 1 choice
Sep 28 17:48:21 gordon-desktop kernel: [    0.740134] hub 2-0:1.0: USB hub found
Sep 28 17:48:21 gordon-desktop kernel: [    0.740139] hub 2-0:1.0: 2 ports detected
Sep 28 17:48:21 gordon-desktop kernel: [    0.740177] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
Sep 28 17:48:21 gordon-desktop kernel: [    0.740184] uhci_hcd 0000:00:1d.1: UHCI Host Controller
Sep 28 17:48:21 gordon-desktop kernel: [    0.740209] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 3
Sep 28 17:48:21 gordon-desktop kernel: [    0.740236] uhci_hcd 0000:00:1d.1: irq 19, io base 0x0000e100
Sep 28 17:48:21 gordon-desktop kernel: [    0.740306] usb usb3: configuration #1 chosen from 1 choice
Sep 28 17:48:21 gordon-desktop kernel: [    0.740327] hub 3-0:1.0: USB hub found
Sep 28 17:48:21 gordon-desktop kernel: [    0.740332] hub 3-0:1.0: 2 ports detected
Sep 28 17:48:21 gordon-desktop kernel: [    0.740372] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
Sep 28 17:48:21 gordon-desktop kernel: [    0.740379] uhci_hcd 0000:00:1d.2: UHCI Host Controller
Sep 28 17:48:21 gordon-desktop kernel: [    0.740407] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 4
Sep 28 17:48:21 gordon-desktop kernel: [    0.740433] uhci_hcd 0000:00:1d.2: irq 18, io base 0x0000e200
Sep 28 17:48:21 gordon-desktop kernel: [    0.740500] usb usb4: configuration #1 chosen from 1 choice
Sep 28 17:48:21 gordon-desktop kernel: [    0.740523] hub 4-0:1.0: USB hub found
Sep 28 17:48:21 gordon-desktop kernel: [    0.740528] hub 4-0:1.0: 2 ports detected
Sep 28 17:48:21 gordon-desktop kernel: [    0.740561] uhci_hcd 0000:00:1d.3: PCI INT D -> GSI 16 (level, low) -> IRQ 16
Sep 28 17:48:21 gordon-desktop kernel: [    0.740569] uhci_hcd 0000:00:1d.3: UHCI Host Controller
Sep 28 17:48:21 gordon-desktop kernel: [    0.740599] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 5
Sep 28 17:48:21 gordon-desktop kernel: [    0.740625] uhci_hcd 0000:00:1d.3: irq 16, io base 0x0000e300
Sep 28 17:48:21 gordon-desktop kernel: [    0.740697] usb usb5: configuration #1 chosen from 1 choice
Sep 28 17:48:21 gordon-desktop kernel: [    0.740720] hub 5-0:1.0: USB hub found
Sep 28 17:48:21 gordon-desktop kernel: [    0.740725] hub 5-0:1.0: 2 ports detected
Sep 28 17:48:21 gordon-desktop kernel: [    0.740798] PNP: PS/2 Controller [PNP0f13:PS2M] at 0x60,0x64 irq 12
Sep 28 17:48:21 gordon-desktop kernel: [    0.740800] PNP: PS/2 controller doesn't have KBD irq; using default 1
Sep 28 17:48:21 gordon-desktop kernel: [    0.741178] serio: i8042 KBD port at 0x60,0x64 irq 1
Sep 28 17:48:21 gordon-desktop kernel: [    0.741187] serio: i8042 AUX port at 0x60,0x64 irq 12
Sep 28 17:48:21 gordon-desktop kernel: [    0.741348] mice: PS/2 mouse device common for all mice
Sep 28 17:48:21 gordon-desktop kernel: [    0.741451] rtc_cmos 00:04: RTC can wake from S4
Sep 28 17:48:21 gordon-desktop kernel: [    0.741490] rtc_cmos 00:04: rtc core: registered rtc_cmos as rtc0
Sep 28 17:48:21 gordon-desktop kernel: [    0.741511] rtc0: alarms up to one month, 242 bytes nvram, hpet irqs
Sep 28 17:48:21 gordon-desktop kernel: [    0.741636] device-mapper: uevent: version 1.0.3
Sep 28 17:48:21 gordon-desktop kernel: [    0.741741] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: [email]dm-devel@redhat.com[/email]
Sep 28 17:48:21 gordon-desktop kernel: [    0.741913] device-mapper: multipath: version 1.1.0 loaded
Sep 28 17:48:21 gordon-desktop kernel: [    0.741916] device-mapper: multipath round-robin: version 1.0.0 loaded
Sep 28 17:48:21 gordon-desktop kernel: [    0.742258] cpuidle: using governor ladder
Sep 28 17:48:21 gordon-desktop kernel: [    0.742259] cpuidle: using governor menu
Sep 28 17:48:21 gordon-desktop kernel: [    0.742575] TCP cubic registered
Sep 28 17:48:21 gordon-desktop kernel: [    0.742687] NET: Registered protocol family 10
Sep 28 17:48:21 gordon-desktop kernel: [    0.743068] lo: Disabled Privacy Extensions
Sep 28 17:48:21 gordon-desktop kernel: [    0.743297] NET: Registered protocol family 17
Sep 28 17:48:21 gordon-desktop kernel: [    0.746807] registered taskstats version 1
Sep 28 17:48:21 gordon-desktop kernel: [    0.747041]   Magic number: 10:332:819
Sep 28 17:48:21 gordon-desktop kernel: [    0.747131] rtc_cmos 00:04: setting system clock to 2010-09-28 04:48:03 UTC (1285649283)
Sep 28 17:48:21 gordon-desktop kernel: [    0.747137] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
Sep 28 17:48:21 gordon-desktop kernel: [    0.747138] EDD information not available.
Sep 28 17:48:21 gordon-desktop kernel: [    0.810065] Freeing initrd memory: 8071k freed
Sep 28 17:48:21 gordon-desktop kernel: [    0.909899] ata1.00: ATAPI: TSSTcorp CDDVDW SH-S223F, SB03, max UDMA/100
Sep 28 17:48:21 gordon-desktop kernel: [    1.040192] ata1.01: HPA unlocked: 976771055 -> 976773168, native 976773168
Sep 28 17:48:21 gordon-desktop kernel: [    1.040197] ata1.01: ATA-8: ST3500418AS, CC34, max UDMA/133
Sep 28 17:48:21 gordon-desktop kernel: [    1.040199] ata1.01: 976773168 sectors, multi 16: LBA48 NCQ (depth 0/32)
Sep 28 17:48:21 gordon-desktop kernel: [    1.080201] ata1.00: configured for UDMA/100
Sep 28 17:48:21 gordon-desktop kernel: [    1.146228] ata1.01: configured for UDMA/133
Sep 28 17:48:21 gordon-desktop kernel: [    1.147225] scsi 0:0:0:0: CD-ROM            TSSTcorp CDDVDW SH-S223F  SB03 PQ: 0 ANSI: 5
Sep 28 17:48:21 gordon-desktop kernel: [    1.150700] sr0: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
Sep 28 17:48:21 gordon-desktop kernel: [    1.150704] Uniform CD-ROM driver Revision: 3.20
Sep 28 17:48:21 gordon-desktop kernel: [    1.150885] sr 0:0:0:0: Attached scsi generic sg0 type 5
Sep 28 17:48:21 gordon-desktop kernel: [    1.150979] scsi 0:0:1:0: Direct-Access     ATA      ST3500418AS      CC34 PQ: 0 ANSI: 5
Sep 28 17:48:21 gordon-desktop kernel: [    1.151089] sd 0:0:1:0: Attached scsi generic sg1 type 0
Sep 28 17:48:21 gordon-desktop kernel: [    1.151092] sd 0:0:1:0: [sda] 976773168 512-byte logical blocks: (500 GB/465 GiB)
Sep 28 17:48:21 gordon-desktop kernel: [    1.151142] sd 0:0:1:0: [sda] Write Protect is off
Sep 28 17:48:21 gordon-desktop kernel: [    1.151165] sd 0:0:1:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Sep 28 17:48:21 gordon-desktop kernel: [    1.151281]  sda: sda1 sda2 < sda5 >
Sep 28 17:48:21 gordon-desktop kernel: [    1.202620] sd 0:0:1:0: [sda] Attached SCSI disk
Sep 28 17:48:21 gordon-desktop kernel: [    1.202637] Freeing unused kernel memory: 880k freed
Sep 28 17:48:21 gordon-desktop kernel: [    1.202874] Write protecting the kernel read-only data: 7696k
Sep 28 17:48:21 gordon-desktop kernel: [    1.216358] udev: starting version 151
Sep 28 17:48:21 gordon-desktop kernel: [    1.249681] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
Sep 28 17:48:21 gordon-desktop kernel: [    1.249702] r8169 0000:03:00.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
Sep 28 17:48:21 gordon-desktop kernel: [    1.250299] eth0: RTL8168c/8111c at 0xffffc90000654000, 00:24:1d:1d:52:c0, XID 1c4000c0 IRQ 27
Sep 28 17:48:21 gordon-desktop kernel: [    1.290043] usb 4-1: new low speed USB device using uhci_hcd and address 2
Sep 28 17:48:21 gordon-desktop kernel: [    1.372317] EXT3-fs: INFO: recovery required on readonly filesystem.
Sep 28 17:48:21 gordon-desktop kernel: [    1.372320] EXT3-fs: write access will be enabled during recovery.
Sep 28 17:48:21 gordon-desktop kernel: [    1.490476] usb 4-1: configuration #1 chosen from 1 choice
Sep 28 17:48:21 gordon-desktop kernel: [    1.501399] usbcore: registered new interface driver hiddev
Sep 28 17:48:21 gordon-desktop kernel: [    1.515654] input: Logitech Logitech USB Keyboard as /devices/pci0000:00/0000:00:1d.2/usb4/4-1/4-1:1.0/input/input3
Sep 28 17:48:21 gordon-desktop kernel: [    1.515737] generic-usb 0003:046D:C315.0001: input,hidraw0: USB HID v1.10 Keyboard [Logitech Logitech USB Keyboard] on usb-0000:00:1d.2-1/input0
Sep 28 17:48:21 gordon-desktop kernel: [    1.515763] usbcore: registered new interface driver usbhid
Sep 28 17:48:21 gordon-desktop kernel: [    1.515766] usbhid: v2.6:USB HID core driver
Sep 28 17:48:21 gordon-desktop kernel: [    3.424003] kjournald starting.  Commit interval 5 seconds
Sep 28 17:48:21 gordon-desktop kernel: [    3.424017] EXT3-fs: sda1: orphan cleanup on readonly fs
Sep 28 17:48:21 gordon-desktop kernel: [    3.424136] EXT3-fs: sda1: 9 orphan inodes deleted
Sep 28 17:48:21 gordon-desktop kernel: [    3.424137] EXT3-fs: recovery complete.
Sep 28 17:48:21 gordon-desktop kernel: [    3.464109] EXT3-fs: mounted filesystem with ordered data mode.
Sep 28 17:48:21 gordon-desktop kernel: [   17.997054] udev: starting version 151
Sep 28 17:48:21 gordon-desktop kernel: [   18.014501] lp: driver loaded but no devices found
Sep 28 17:48:21 gordon-desktop kernel: [   18.046694] vga16fb: mapped to 0xffff8800000a0000
Sep 28 17:48:21 gordon-desktop kernel: [   18.046776] fb0: VGA16 VGA frame buffer device
Sep 28 17:48:21 gordon-desktop kernel: [   18.088388] intel_rng: FWH not detected
Sep 28 17:48:21 gordon-desktop kernel: [   18.098596] Adding 11871992k swap on /dev/sda5.  Priority:-1 extents:1 across:11871992k 
Sep 28 17:48:21 gordon-desktop kernel: [   18.118085] nvidia: module license 'NVIDIA' taints kernel.
Sep 28 17:48:21 gordon-desktop kernel: [   18.118088] Disabling lock debugging due to kernel taint
Sep 28 17:48:21 gordon-desktop kernel: [   18.382446] type=1505 audit(1285649301.125:2):  operation="profile_load" pid=598 name="/sbin/dhclient3"
Sep 28 17:48:21 gordon-desktop kernel: [   18.383016] type=1505 audit(1285649301.135:3):  operation="profile_load" pid=598 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
Sep 28 17:48:21 gordon-desktop kernel: [   18.383321] type=1505 audit(1285649301.135:4):  operation="profile_load" pid=598 name="/usr/lib/connman/scripts/dhclient-script"
Sep 28 17:48:21 gordon-desktop kernel: [   18.479856] parport_pc 00:08: reported by Plug and Play ACPI
Sep 28 17:48:21 gordon-desktop kernel: [   18.479902] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
Sep 28 17:48:21 gordon-desktop kernel: [   18.718469] nvidia 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Sep 28 17:48:21 gordon-desktop kernel: [   18.718506] vgaarb: device changed decodes: PCI:0000:01:00.0,olddecodes=io+mem,decodes=none:owns=io+mem
Sep 28 17:48:21 gordon-desktop kernel: [   18.718748] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  195.36.24  Thu Apr 22 19:10:14 PDT 2010
Sep 28 17:48:21 gordon-desktop kernel: [   18.722533] ppdev: user-space parallel port driver
Sep 28 17:48:21 gordon-desktop kernel: [   18.753918] lp0: using parport0 (interrupt-driven).
Sep 28 17:48:21 gordon-desktop kernel: [   18.780380] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Sep 28 17:48:21 gordon-desktop kernel: [   18.879292] Console: switching to colour frame buffer device 80x30
Sep 28 17:48:21 gordon-desktop kernel: [   18.920105] input: HDA Digital PCBeep as /devices/pci0000:00/0000:00:1b.0/input/input4
Sep 28 17:48:21 gordon-desktop kernel: [   19.097417] EXT3 FS on sda1, internal journal
Sep 28 17:48:21 gordon-desktop kernel: [   19.177707] r8169: eth0: link up
Sep 28 17:48:21 gordon-desktop kernel: [   19.177711] r8169: eth0: link up
Sep 28 17:48:21 gordon-desktop kernel: [   19.196226] type=1505 audit(1285649301.945:5):  operation="profile_load" pid=882 name="/usr/share/gdm/guest-session/Xsession"
Sep 28 17:48:21 gordon-desktop kernel: [   19.197861] type=1505 audit(1285649301.945:6):  operation="profile_replace" pid=885 name="/sbin/dhclient3"
Sep 28 17:48:21 gordon-desktop kernel: [   19.198604] type=1505 audit(1285649301.945:7):  operation="profile_replace" pid=885 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
Sep 28 17:48:21 gordon-desktop kernel: [   19.198912] type=1505 audit(1285649301.945:8):  operation="profile_replace" pid=885 name="/usr/lib/connman/scripts/dhclient-script"
Sep 28 17:48:21 gordon-desktop kernel: [   19.201420] type=1505 audit(1285649301.945:9):  operation="profile_load" pid=886 name="/usr/bin/evince"
Sep 28 17:48:21 gordon-desktop kernel: [   19.208746] type=1505 audit(1285649301.955:10):  operation="profile_load" pid=886 name="/usr/bin/evince-previewer"
Sep 28 17:48:21 gordon-desktop kernel: [   19.213281] type=1505 audit(1285649301.965:11):  operation="profile_load" pid=886 name="/usr/bin/evince-thumbnailer"
Sep 28 17:48:22 gordon-desktop kernel: [   19.364304] RPC: Registered udp transport module.
Sep 28 17:48:22 gordon-desktop kernel: [   19.364307] RPC: Registered tcp transport module.
Sep 28 17:48:22 gordon-desktop kernel: [   19.364308] RPC: Registered tcp NFSv4.1 backchannel transport module.
Sep 28 17:48:22 gordon-desktop kernel: [   19.382800] Installing knfsd (copyright (C) 1996 [email]okir@monad.swb.de[/email]).
Sep 28 17:48:22 gordon-desktop kernel: [   19.431177] svc: failed to register lockdv1 RPC service (errno 97).
Sep 28 17:48:22 gordon-desktop kernel: [   19.431812] NFSD: Using /var/lib/nfs/v4recovery as the NFSv4 state recovery directory
Sep 28 17:48:22 gordon-desktop kernel: [   19.434678] NFSD: starting 90-second grace period
Sep 28 17:48:22 gordon-desktop kernel: [   19.543776] input: ImPS/2 Logitech Wheel Mouse as /devices/platform/i8042/serio1/input/input5



---

### Post by andrewthomas on 2010-09-28
That log shows the first 19 [   19.543776] seconds of your boot.  There should be more.

This :```
Kernel logging (proc) stopped.
```should be the last line before shutdown/restart

---

### Post by Gordonisnz on 2010-09-29
I see a few lines like that - Though its Odd - the times before / after, aren't similar.

> 

Sep 27 21:36:08 gordon-desktop kernel: [   19.957859] RPC: Registered udp transport module.
Sep 27 21:36:08 gordon-desktop kernel: [   19.957861] RPC: Registered tcp transport module.
Sep 27 21:36:08 gordon-desktop kernel: [   19.957863] RPC: Registered tcp NFSv4.1 backchannel transport module.
Sep 27 21:36:08 gordon-desktop kernel: [   19.976953] Installing knfsd (copyright (C) 1996 [email]okir@monad.swb.de[/email]).
Sep 27 21:36:08 gordon-desktop kernel: [   20.026670] svc: failed to register lockdv1 RPC service (errno 97).
Sep 27 21:36:08 gordon-desktop kernel: [   20.027361] NFSD: Using /var/lib/nfs/v4recovery as the NFSv4 state recovery directory
Sep 27 21:36:08 gordon-desktop kernel: [   20.038444] NFSD: starting 90-second grace period
Sep 27 21:40:23 gordon-desktop pulseaudio[1854]: ratelimit.c: 2 events suppressed
Sep 28 01:37:45 gordon-desktop kernel: Kernel logging (proc) stopped.
Sep 28 14:55:17 gordon-desktop kernel: imklog 4.2.0, log source = /proc/kmsg started.
Sep 28 14:55:17 gordon-desktop rsyslogd: [origin software="rsyslogd" swVersion="4.2.0" x-pid="768" x-info="http://www.rsyslog.com"] (re)start
Sep 28 14:55:17 gordon-desktop rsyslogd: rsyslogd's groupid changed to 103
Sep 28 14:55:17 gordon-desktop rsyslogd: rsyslogd's userid changed to 102
Sep 28 14:55:17 gordon-desktop kernel: [    0.000000] Initializing cgroup subsys cpuset
Sep 28 14:55:17 gordon-desktop kernel: [    0.000000] Initializing cgroup subsys cpu


It seems to stop - long before/after my screen freezes 


And another one 


> 

Sep 28 21:33:06 gordon-desktop kernel: [   27.919686] RPC: Registered udp transport module.
Sep 28 21:33:06 gordon-desktop kernel: [   27.919689] RPC: Registered tcp transport module.
Sep 28 21:33:06 gordon-desktop kernel: [   27.919690] RPC: Registered tcp NFSv4.1 backchannel transport module.
Sep 28 21:33:06 gordon-desktop kernel: [   28.142785] Console: switching to colour frame buffer device 80x30
Sep 28 21:33:07 gordon-desktop kernel: [   28.338180] Installing knfsd (copyright (C) 1996 [email]okir@monad.swb.de[/email]).
Sep 28 21:33:07 gordon-desktop kernel: [   28.395424] svc: failed to register lockdv1 RPC service (errno 97).
Sep 28 21:33:07 gordon-desktop kernel: [   28.396382] NFSD: Using /var/lib/nfs/v4recovery as the NFSv4 state recovery directory
Sep 28 21:33:07 gordon-desktop kernel: [   28.422543] NFSD: starting 90-second grace period
Sep 28 21:33:07 gordon-desktop kernel: [   28.515685] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Sep 28 21:33:07 gordon-desktop kernel: [   28.812940] input: HDA Digital PCBeep as /devices/pci0000:00/0000:00:1b.0/input/input5
Sep 28 21:35:48 gordon-desktop pulseaudio[1848]: ratelimit.c: 2 events suppressed
Sep 28 21:36:06 gordon-desktop kernel: Kernel logging (proc) stopped.
Sep 28 21:36:06 gordon-desktop rsyslogd: [origin software="rsyslogd" swVersion="4.2.0" x-pid="700" x-info="http://www.rsyslog.com"] exiting on signal 15.
Sep 28 21:36:58 gordon-desktop kernel: imklog 4.2.0, log source = /proc/kmsg started.
Sep 28 21:36:58 gordon-desktop rsyslogd: [origin software="rsyslogd" swVersion="4.2.0" x-pid="712" x-info="http://www.rsyslog.com"] (re)start
Sep 28 21:36:58 gordon-desktop rsyslogd: rsyslogd's groupid changed to 103
Sep 28 21:36:58 gordon-desktop rsyslogd: rsyslogd's userid changed to 102
Sep 28 21:36:58 gordon-desktop kernel: [    0.000000] Initializing cgroup subsys cpuset
Sep 28 21:36:58 gordon-desktop kernel: [    0.000000] Initializing cgroup subsys cpu




Ive only quoted a dozen or so lines either side of each stop command.

Does this tell you useful info ?

---

### Post by Gordonisnz on 2010-09-29
Hmm I'm viewing my NVIDIA X SERVER Settings now

>> GPU 0 (GeForce 9800 GT)

Thermal settings >> Slowdown threshold = 105C

Its now at 111C now (but still on...)

its got FAN INFO :-

ID = 9
100% speed
control type VARIABLE

Cooling target :-  GPU, Memory & Power Supply 


Temp is now 112C - Getting higher...


How do I tell my Screen / Video to "slow down" & drop in temp ?

---

### Post by chrisbay90 on 2010-10-08
Im not sure how to tell it to ease up. But it shouldn't be getting so  hot under normal conditions. It would be worth making sure the GPU  fan/heatsink hasnt gotten clogged with dust. Can happen very quickly if  its in a carpeted area.

---

