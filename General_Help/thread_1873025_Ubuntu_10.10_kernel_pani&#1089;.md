---
title: "Ubuntu 10.10 kernel pani&#1089;"
date: 2011-10-31
forum: General Help
---

### Post by kiruri on 2011-10-31
I have an Ubuntu 10.10 64 bit setup on Lenovo Thinkpad w510.

After waking up the screen I have &#1057;aps Lo&#1089;k blinking. It is very difficult to write this text, because I use &#1057;aps to swit&#1089;h kbd layout.





```
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.35-22-generic (buildd@allspice) (gcc version 4.4.5 (Ubuntu/Linaro 4.4.4-14ubuntu4) ) #33-Ubuntu SMP Sun Sep 19 20:32:27 UTC 2010 (Ubuntu 2.6.35-22.33-generic 2.6.35.4)
[    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-2.6.35-22-generic root=UUID=0b9f7d33-6b4e-40ed-9125-912b3f75424e ro quiet splash
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009e800 (usable)
[    0.000000]  BIOS-e820: 000000000009e800 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000d2000 - 00000000000d4000 (reserved)
[    0.000000]  BIOS-e820: 00000000000dc000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 00000000bf27c000 (usable)
[    0.000000]  BIOS-e820: 00000000bf27c000 - 00000000bf282000 (reserved)
[    0.000000]  BIOS-e820: 00000000bf282000 - 00000000bf34a000 (usable)
[    0.000000]  BIOS-e820: 00000000bf34a000 - 00000000bf35c000 (reserved)
[    0.000000]  BIOS-e820: 00000000bf35c000 - 00000000bf3dd000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000bf3dd000 - 00000000bf40f000 (reserved)
[    0.000000]  BIOS-e820: 00000000bf40f000 - 00000000bf45d000 (usable)
[    0.000000]  BIOS-e820: 00000000bf45d000 - 00000000bf668000 (reserved)
[    0.000000]  BIOS-e820: 00000000bf668000 - 00000000bf6e8000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000bf6e8000 - 00000000bf70f000 (reserved)
[    0.000000]  BIOS-e820: 00000000bf70f000 - 00000000bf717000 (usable)
[    0.000000]  BIOS-e820: 00000000bf717000 - 00000000bf71f000 (reserved)
[    0.000000]  BIOS-e820: 00000000bf71f000 - 00000000bf76c000 (usable)
[    0.000000]  BIOS-e820: 00000000bf76c000 - 00000000bf778000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000bf778000 - 00000000bf77b000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000bf77b000 - 00000000bf78b000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000bf78b000 - 00000000bf78c000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000bf78c000 - 00000000bf79f000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000bf79f000 - 00000000bf7ff000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000bf7ff000 - 00000000bf800000 (usable)
[    0.000000]  BIOS-e820: 00000000bf800000 - 00000000c0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000feaff000 - 00000000feb00000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed00000 - 00000000fed00400 (reserved)
[    0.000000]  BIOS-e820: 00000000fed1c000 - 00000000fed90000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000ff000000 - 0000000100000000 (reserved)
[    0.000000]  BIOS-e820: 0000000100000000 - 00000001fc000000 (usable)
[    0.000000]  BIOS-e820: 0000000200000000 - 000000023c000000 (usable)
[    0.000000] NX (Execute Disable) protection: active
[    0.000000] DMI present.
[    0.000000] e820 update range: 0000000000000000 - 0000000000001000 (usable) ==> (reserved)
[    0.000000] e820 remove range: 00000000000a0000 - 0000000000100000 (usable)
[    0.000000] No AGP bridge found
[    0.000000] last_pfn = 0x23c000 max_arch_pfn = 0x400000000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-D3FFF write-protect
[    0.000000]   D4000-DBFFF uncachable
[    0.000000]   DC000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 disabled
[    0.000000]   1 base 000000000 mask F80000000 write-back
[    0.000000]   2 base 080000000 mask FC0000000 write-back
[    0.000000]   3 base 100000000 mask F00000000 write-back
[    0.000000]   4 base 200000000 mask FC0000000 write-back
[    0.000000]   5 base 23C000000 mask FFC000000 uncachable
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] e820 update range: 00000000c0000000 - 0000000100000000 (usable) ==> (reserved)
[    0.000000] last_pfn = 0xbf800 max_arch_pfn = 0x400000000
[    0.000000] e820 update range: 0000000000001000 - 0000000000010000 (usable) ==> (reserved)
[    0.000000] Scanning 1 areas for low memory corruption
[    0.000000] modified physical RAM map:
[    0.000000]  modified: 0000000000000000 - 0000000000010000 (reserved)
[    0.000000]  modified: 0000000000010000 - 000000000009e800 (usable)
[    0.000000]  modified: 000000000009e800 - 00000000000a0000 (reserved)
[    0.000000]  modified: 00000000000d2000 - 00000000000d4000 (reserved)
[    0.000000]  modified: 00000000000dc000 - 0000000000100000 (reserved)
[    0.000000]  modified: 0000000000100000 - 00000000bf27c000 (usable)
[    0.000000]  modified: 00000000bf27c000 - 00000000bf282000 (reserved)
[    0.000000]  modified: 00000000bf282000 - 00000000bf34a000 (usable)
[    0.000000]  modified: 00000000bf34a000 - 00000000bf35c000 (reserved)
[    0.000000]  modified: 00000000bf35c000 - 00000000bf3dd000 (ACPI NVS)
[    0.000000]  modified: 00000000bf3dd000 - 00000000bf40f000 (reserved)
[    0.000000]  modified: 00000000bf40f000 - 00000000bf45d000 (usable)
[    0.000000]  modified: 00000000bf45d000 - 00000000bf668000 (reserved)
[    0.000000]  modified: 00000000bf668000 - 00000000bf6e8000 (ACPI NVS)
[    0.000000]  modified: 00000000bf6e8000 - 00000000bf70f000 (reserved)
[    0.000000]  modified: 00000000bf70f000 - 00000000bf717000 (usable)
[    0.000000]  modified: 00000000bf717000 - 00000000bf71f000 (reserved)
[    0.000000]  modified: 00000000bf71f000 - 00000000bf76c000 (usable)
[    0.000000]  modified: 00000000bf76c000 - 00000000bf778000 (ACPI NVS)
[    0.000000]  modified: 00000000bf778000 - 00000000bf77b000 (ACPI data)
[    0.000000]  modified: 00000000bf77b000 - 00000000bf78b000 (ACPI NVS)
[    0.000000]  modified: 00000000bf78b000 - 00000000bf78c000 (ACPI data)
[    0.000000]  modified: 00000000bf78c000 - 00000000bf79f000 (ACPI NVS)
[    0.000000]  modified: 00000000bf79f000 - 00000000bf7ff000 (ACPI data)
[    0.000000]  modified: 00000000bf7ff000 - 00000000bf800000 (usable)
[    0.000000]  modified: 00000000bf800000 - 00000000c0000000 (reserved)
[    0.000000]  modified: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  modified: 00000000feaff000 - 00000000feb00000 (reserved)
[    0.000000]  modified: 00000000fec00000 - 00000000fec10000 (reserved)
[    0.000000]  modified: 00000000fed00000 - 00000000fed00400 (reserved)
[    0.000000]  modified: 00000000fed1c000 - 00000000fed90000 (reserved)
[    0.000000]  modified: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  modified: 00000000ff000000 - 0000000100000000 (reserved)
[    0.000000]  modified: 0000000100000000 - 00000001fc000000 (usable)
[    0.000000]  modified: 0000000200000000 - 000000023c000000 (usable)
[    0.000000] initial memory mapped : 0 - 20000000
[    0.000000] found SMP MP-table at [ffff8800000f68c0] f68c0
[    0.000000] init_memory_mapping: 0000000000000000-00000000bf800000
[    0.000000]  0000000000 - 00bf800000 page 2M
[    0.000000] kernel direct mapping tables up to bf800000 @ 16000-1a000
[    0.000000] init_memory_mapping: 0000000100000000-000000023c000000
[    0.000000]  0100000000 - 023c000000 page 2M
[    0.000000] kernel direct mapping tables up to 23c000000 @ 18000-22000
[    0.000000] RAMDISK: 37572000 - 37ff0000
[    0.000000] ACPI: RSDP 00000000000f6880 00024 (v02 LENOVO)
[    0.000000] ACPI: XSDT 00000000bf7f1b2b 00094 (v01 LENOVO TP-6L    00001310  LTP 00000000)
[    0.000000] ACPI: FACP 00000000bf7f1c00 000F4 (v04 LENOVO TP-6L    00001310 LNVO 00000001)
[    0.000000] ACPI: DSDT 00000000bf7f1e9b 0CC3B (v01 LENOVO TP-6L    00001310 MSFT 03000001)
[    0.000000] ACPI: FACS 00000000bf6e7000 00040
[    0.000000] ACPI: SSDT 00000000bf7f1db4 000E7 (v01 LENOVO TP-6L    00001310 MSFT 03000001)
[    0.000000] ACPI: ECDT 00000000bf7fead6 00052 (v01 LENOVO TP-6L    00001310 LNVO 00000001)
[    0.000000] ACPI: APIC 00000000bf7feb28 00084 (v01 LENOVO TP-6L    00001310 LNVO 00000001)
[    0.000000] ACPI: MCFG 00000000bf7febe4 0003C (v01 LENOVO TP-6L    00001310 LNVO 00000001)
[    0.000000] ACPI: HPET 00000000bf7fec20 00038 (v01 LENOVO TP-6L    00001310 LNVO 00000001)
[    0.000000] ACPI: ASF! 00000000bf7fedbe 000A4 (v16 LENOVO TP-6L    00001310 PTL  00000001)
[    0.000000] ACPI: SLIC 00000000bf7fee62 00176 (v01 LENOVO TP-6L    00001310  LTP 00000000)
[    0.000000] ACPI: BOOT 00000000bf7fefd8 00028 (v01 LENOVO TP-6L    00001310  LTP 00000001)
[    0.000000] ACPI: SSDT 00000000bf6e591a 0084B (v01 LENOVO TP-6L    00001310 INTL 20050513)
[    0.000000] ACPI: TCPA 00000000bf78b000 00032 (v02    PTL  CRESTLN 06040000      00005A52)
[    0.000000] ACPI: SSDT 00000000bf77a000 009F1 (v01  PmRef    CpuPm 00003000 INTL 20060912)
[    0.000000] ACPI: SSDT 00000000bf779000 00259 (v01  PmRef  Cpu0Tst 00003000 INTL 20060912)
[    0.000000] ACPI: SSDT 00000000bf778000 0049F (v01  PmRef    ApTst 00003000 INTL 20060912)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] No NUMA configuration found
[    0.000000] Faking a node at 0000000000000000-000000023c000000
[    0.000000] Initmem setup node 0 0000000000000000-000000023c000000
[    0.000000]   NODE_DATA [0000000100000000 - 0000000100004fff]
[    0.000000]  [ffffea0000000000-ffffea0007dfffff] PMD -> [ffff880100200000-ffff8801071fffff] on node 0
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000010 -> 0x00001000
[    0.000000]   DMA32    0x00001000 -> 0x00100000
[    0.000000]   Normal   0x00100000 -> 0x0023c000
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[9] active PFN ranges
[    0.000000]     0: 0x00000010 -> 0x0000009e
[    0.000000]     0: 0x00000100 -> 0x000bf27c
[    0.000000]     0: 0x000bf282 -> 0x000bf34a
[    0.000000]     0: 0x000bf40f -> 0x000bf45d
[    0.000000]     0: 0x000bf70f -> 0x000bf717
[    0.000000]     0: 0x000bf71f -> 0x000bf76c
[    0.000000]     0: 0x000bf7ff -> 0x000bf800
[    0.000000]     0: 0x00100000 -> 0x001fc000
[    0.000000]     0: 0x00200000 -> 0x0023c000
[    0.000000] On node 0 totalpages: 2061174
[    0.000000]   DMA zone: 56 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3926 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 14280 pages used for memmap
[    0.000000]   DMA32 zone: 764960 pages, LIFO batch:31
[    0.000000]   Normal zone: 17696 pages used for memmap
[    0.000000]   Normal zone: 1260256 pages, LIFO batch:31
[    0.000000] ACPI: PM-Timer IO Port: 0x1008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x04] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x05] enabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x02] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x03] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 1, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x8086a701 base: 0xfed00000
[    0.000000] SMP: Allowing 4 CPUs, 0 hotplug CPUs
[    0.000000] nr_irqs_gsi: 40
[    0.000000] early_res array is doubled to 64 at [1d000 - 1d7ff]
[    0.000000] early_res array is doubled to 128 at [1d800 - 1e7ff]
[    0.000000] PM: Registered nosave memory: 000000000009e000 - 000000000009f000
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000d2000
[    0.000000] PM: Registered nosave memory: 00000000000d2000 - 00000000000d4000
[    0.000000] PM: Registered nosave memory: 00000000000d4000 - 00000000000dc000
[    0.000000] PM: Registered nosave memory: 00000000000dc000 - 0000000000100000
[    0.000000] PM: Registered nosave memory: 00000000bf27c000 - 00000000bf282000
[    0.000000] PM: Registered nosave memory: 00000000bf34a000 - 00000000bf35c000
[    0.000000] PM: Registered nosave memory: 00000000bf35c000 - 00000000bf3dd000
[    0.000000] PM: Registered nosave memory: 00000000bf3dd000 - 00000000bf40f000
[    0.000000] PM: Registered nosave memory: 00000000bf45d000 - 00000000bf668000
[    0.000000] PM: Registered nosave memory: 00000000bf668000 - 00000000bf6e8000
[    0.000000] PM: Registered nosave memory: 00000000bf6e8000 - 00000000bf70f000
[    0.000000] PM: Registered nosave memory: 00000000bf717000 - 00000000bf71f000
[    0.000000] PM: Registered nosave memory: 00000000bf76c000 - 00000000bf778000
[    0.000000] PM: Registered nosave memory: 00000000bf778000 - 00000000bf77b000
[    0.000000] PM: Registered nosave memory: 00000000bf77b000 - 00000000bf78b000
[    0.000000] PM: Registered nosave memory: 00000000bf78b000 - 00000000bf78c000
[    0.000000] PM: Registered nosave memory: 00000000bf78c000 - 00000000bf79f000
[    0.000000] PM: Registered nosave memory: 00000000bf79f000 - 00000000bf7ff000
[    0.000000] PM: Registered nosave memory: 00000000bf800000 - 00000000c0000000
[    0.000000] PM: Registered nosave memory: 00000000c0000000 - 00000000e0000000
[    0.000000] PM: Registered nosave memory: 00000000e0000000 - 00000000f0000000
[    0.000000] PM: Registered nosave memory: 00000000f0000000 - 00000000feaff000
[    0.000000] PM: Registered nosave memory: 00000000feaff000 - 00000000feb00000
[    0.000000] PM: Registered nosave memory: 00000000feb00000 - 00000000fec00000
[    0.000000] PM: Registered nosave memory: 00000000fec00000 - 00000000fec10000
[    0.000000] PM: Registered nosave memory: 00000000fec10000 - 00000000fed00000
[    0.000000] PM: Registered nosave memory: 00000000fed00000 - 00000000fed1c000
[    0.000000] PM: Registered nosave memory: 00000000fed1c000 - 00000000fed90000
[    0.000000] PM: Registered nosave memory: 00000000fed90000 - 00000000fee00000
[    0.000000] PM: Registered nosave memory: 00000000fee00000 - 00000000fee01000
[    0.000000] PM: Registered nosave memory: 00000000fee01000 - 00000000ff000000
[    0.000000] PM: Registered nosave memory: 00000000ff000000 - 0000000100000000
[    0.000000] PM: Registered nosave memory: 00000001fc000000 - 0000000200000000
[    0.000000] Allocating PCI resources starting at c0000000 (gap: c0000000:20000000)
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] setup_percpu: NR_CPUS:64 nr_cpumask_bits:64 nr_cpu_ids:4 nr_node_ids:1
[    0.000000] PERCPU: Embedded 30 pages/cpu @ffff880001e00000 s91520 r8192 d23168 u524288
[    0.000000] pcpu-alloc: s91520 r8192 d23168 u524288 alloc=1*2097152
[    0.000000] pcpu-alloc: [0] 0 1 2 3 
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 2029142
[    0.000000] Policy zone: Normal
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.35-22-generic root=UUID=0b9f7d33-6b4e-40ed-9125-912b3f75424e ro quiet splash
[    0.000000] PID hash table entries: 4096 (order: 3, 32768 bytes)
[    0.000000] Checking aperture...
[    0.000000] No AGP bridge found
[    0.000000] Calgary: detecting Calgary via BIOS EBDA area
[    0.000000] Calgary: Unable to locate Rio Grande table in EBDA - bailing!
[    0.000000] Subtract (86 early reservations)
[    0.000000]   #1 [0001000000 - 0001d17114]   TEXT DATA BSS
[    0.000000]   #2 [0037572000 - 0037ff0000]         RAMDISK
[    0.000000]   #3 [0001d18000 - 0001d18144]             BRK
[    0.000000]   #4 [00000f68d0 - 0000100000]   BIOS reserved
[    0.000000]   #5 [00000f68c0 - 00000f68d0]    MP-table mpf
[    0.000000]   #6 [000009e800 - 000009f071]   BIOS reserved
[    0.000000]   #7 [000009f195 - 00000f68c0]   BIOS reserved
[    0.000000]   #8 [000009f071 - 000009f195]    MP-table mpc
[    0.000000]   #9 [0000010000 - 0000012000]      TRAMPOLINE
[    0.000000]   #10 [0000012000 - 0000016000]     ACPI WAKEUP
[    0.000000]   #11 [0000016000 - 0000018000]         PGTABLE
[    0.000000]   #12 [0000018000 - 000001d000]         PGTABLE
[    0.000000]   #13 [0100000000 - 0100005000]       NODE_DATA
[    0.000000]   #14 [0001d18180 - 0001d19180]         BOOTMEM
[    0.000000]   #15 [0001d17140 - 0001d17740]         BOOTMEM
[    0.000000]   #16 [0100005000 - 0100006000]         BOOTMEM
[    0.000000]   #17 [0100006000 - 0100007000]         BOOTMEM
[    0.000000]   #18 [0100200000 - 0107200000]        MEMMAP 0
[    0.000000]   #19 [0001d17740 - 0001d178c0]         BOOTMEM
[    0.000000]   #20 [0001d19180 - 0001d31180]         BOOTMEM
[    0.000000]   #21 [0001d31180 - 0001d49180]         BOOTMEM
[    0.000000]   #22 [0001d4a000 - 0001d4b000]         BOOTMEM
[    0.000000]   #23 [0001d178c0 - 0001d17901]         BOOTMEM
[    0.000000]   #24 [0001d17940 - 0001d17983]         BOOTMEM
[    0.000000]   #25 [0001d49180 - 0001d49928]         BOOTMEM
[    0.000000]   #26 [0001d179c0 - 0001d17a28]         BOOTMEM
[    0.000000]   #27 [0001d17a40 - 0001d17aa8]         BOOTMEM
[    0.000000]   #28 [0001d17ac0 - 0001d17b28]         BOOTMEM
[    0.000000]   #29 [0001d17b40 - 0001d17ba8]         BOOTMEM
[    0.000000]   #30 [0001d17bc0 - 0001d17c28]         BOOTMEM
[    0.000000]   #31 [0001d17c40 - 0001d17ca8]         BOOTMEM
[    0.000000]   #32 [0001d17cc0 - 0001d17d28]         BOOTMEM
[    0.000000]   #33 [0001d17d40 - 0001d17da8]         BOOTMEM
[    0.000000]   #34 [0001d17dc0 - 0001d17e28]         BOOTMEM
[    0.000000]   #35 [0001d17e40 - 0001d17ea8]         BOOTMEM
[    0.000000]   #36 [0001d17ec0 - 0001d17f28]         BOOTMEM
[    0.000000]   #37 [0001d17f40 - 0001d17fa8]         BOOTMEM
[    0.000000]   #38 [0001d49940 - 0001d499a8]         BOOTMEM
[    0.000000]   #39 [0001d499c0 - 0001d49a28]         BOOTMEM
[    0.000000]   #40 [0001d49a40 - 0001d49aa8]         BOOTMEM
[    0.000000]   #41 [0001d49ac0 - 0001d49b28]         BOOTMEM
[    0.000000]   #42 [0001d49b40 - 0001d49ba8]         BOOTMEM
[    0.000000]   #43 [0001d49bc0 - 0001d49c28]         BOOTMEM
[    0.000000]   #44 [0001d49c40 - 0001d49ca8]         BOOTMEM
[    0.000000]   #45 [0001d49cc0 - 0001d49d28]         BOOTMEM
[    0.000000]   #46 [0001d49d40 - 0001d49da8]         BOOTMEM
[    0.000000]   #47 [0001d49dc0 - 0001d49e28]         BOOTMEM
[    0.000000]   #48 [0001d49e40 - 0001d49ea8]         BOOTMEM
[    0.000000]   #49 [0001d49ec0 - 0001d49f28]         BOOTMEM
[    0.000000]   #50 [0001d49f40 - 0001d49fa8]         BOOTMEM
[    0.000000]   #51 [0001d4b000 - 0001d4b068]         BOOTMEM
[    0.000000]   #52 [0001d4b080 - 0001d4b0e8]         BOOTMEM
[    0.000000]   #53 [0001d4b100 - 0001d4b168]         BOOTMEM
[    0.000000]   #54 [0001d4b180 - 0001d4b1e8]         BOOTMEM
[    0.000000]   #55 [0001d4b200 - 0001d4b268]         BOOTMEM
[    0.000000]   #56 [0001d4b280 - 0001d4b2e8]         BOOTMEM
[    0.000000]   #57 [0001d4b300 - 0001d4b368]         BOOTMEM
[    0.000000]   #58 [0001d4b380 - 0001d4b3e8]         BOOTMEM
[    0.000000]   #59 [0001d4b400 - 0001d4b468]         BOOTMEM
[    0.000000]   #60 [0001d17fc0 - 0001d17fe0]         BOOTMEM
[    0.000000]   #61 [0001d49fc0 - 0001d49fe0]         BOOTMEM
[    0.000000]   #62 [0001d4b480 - 0001d4b4a0]         BOOTMEM
[    0.000000]   #63 [0001d4b4c0 - 0001d4b4e0]         BOOTMEM
[    0.000000]   #64 [0001d4b500 - 0001d4b520]         BOOTMEM
[    0.000000]   #65 [0001d4b540 - 0001d4b560]         BOOTMEM
[    0.000000]   #66 [0001d4b580 - 0001d4b5a0]         BOOTMEM
[    0.000000]   #67 [0001d4b5c0 - 0001d4b5e0]         BOOTMEM
[    0.000000]   #68 [0001d4b600 - 0001d4b66a]         BOOTMEM
[    0.000000]   #69 [0001d4b680 - 0001d4b6ea]         BOOTMEM
[    0.000000]   #70 [0001e00000 - 0001e1e000]         BOOTMEM
[    0.000000]   #71 [0001e80000 - 0001e9e000]         BOOTMEM
[    0.000000]   #72 [0001f00000 - 0001f1e000]         BOOTMEM
[    0.000000]   #73 [0001f80000 - 0001f9e000]         BOOTMEM
[    0.000000]   #74 [0001d4d700 - 0001d4d708]         BOOTMEM
[    0.000000]   #75 [0001d4d740 - 0001d4d748]         BOOTMEM
[    0.000000]   #76 [0001d4d780 - 0001d4d790]         BOOTMEM
[    0.000000]   #77 [0001d4d7c0 - 0001d4d7e0]         BOOTMEM
[    0.000000]   #78 [0001d4d800 - 0001d4d930]         BOOTMEM
[    0.000000]   #79 [0001d4d940 - 0001d4d990]         BOOTMEM
[    0.000000]   #80 [0001d4d9c0 - 0001d4da10]         BOOTMEM
[    0.000000]   #81 [0001d4da40 - 0001d55a40]         BOOTMEM
[    0.000000]   #82 [0001f9e000 - 0005f9e000]         BOOTMEM
[    0.000000]   #83 [0001d55a40 - 0001d75a40]         BOOTMEM
[    0.000000]   #84 [0001d75a40 - 0001db5a40]         BOOTMEM
[    0.000000]   #85 [000001e800 - 0000026800]         BOOTMEM
[    0.000000] Memory: 8039096k/9371648k available (5708k kernel code, 1126952k absent, 205600k reserved, 5382k data, 908k init)
[    0.000000] SLUB: Genslabs=14, HWalign=64, Order=0-3, MinObjects=0, CPUs=4, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000] 	RCU dyntick-idle grace-period acceleration is enabled.
[    0.000000] 	RCU-based detection of stalled CPUs is disabled.
[    0.000000] 	Verbose stalled-CPUs detection is disabled.
[    0.000000] NR_IRQS:4352 nr_irqs:712
[    0.000000] Extended CMOS year: 2000
[    0.000000] Console: colour VGA+ 80x25
[    0.000000] console [tty0] enabled
[    0.000000] allocated 83886080 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] hpet clockevent registered
[    0.000000] Fast TSC calibration using PIT
[    0.010000] Detected 2393.668 MHz processor.
[    0.000007] Calibrating delay loop (skipped), value calculated using timer frequency.. 4787.33 BogoMIPS (lpj=23936680)
[    0.000010] pid_max: default: 32768 minimum: 301
[    0.000029] Security Framework initialized
[    0.000043] AppArmor: AppArmor initialized
[    0.000044] Yama: becoming mindful.
[    0.000706] Dentry cache hash table entries: 1048576 (order: 11, 8388608 bytes)
[    0.002599] Inode-cache hash table entries: 524288 (order: 10, 4194304 bytes)
[    0.003388] Mount-cache hash table entries: 256
[    0.003489] Initializing cgroup subsys ns
[    0.003493] Initializing cgroup subsys cpuacct
[    0.003496] Initializing cgroup subsys memory
[    0.003502] Initializing cgroup subsys devices
[    0.003504] Initializing cgroup subsys freezer
[    0.003505] Initializing cgroup subsys net_cls
[    0.003525] CPU: Physical Processor ID: 0
[    0.003526] CPU: Processor Core ID: 0
[    0.003531] mce: CPU supports 9 MCE banks
[    0.003541] CPU0: Thermal monitoring enabled (TM1)
[    0.003548] using mwait in idle threads.
[    0.003550] Performance Events: PEBS fmt1+, Westmere events, Intel PMU driver.
[    0.003557] ... version:                3
[    0.003558] ... bit width:              48
[    0.003559] ... generic registers:      4
[    0.003560] ... value mask:             0000ffffffffffff
[    0.003561] ... max period:             000000007fffffff
[    0.003563] ... fixed-purpose events:   3
[    0.003564] ... event mask:             000000070000000f
[    0.005419] ACPI: Core revision 20100428
[    0.028918] ftrace: converting mcount calls to 0f 1f 44 00 00
[    0.028923] ftrace: allocating 22680 entries in 89 pages
[    0.035415] Setting APIC routing to flat
[    0.035800] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.135466] CPU0: Intel(R) Core(TM) i5 CPU       M 520  @ 2.40GHz stepping 05
[    0.254829] Booting Node   0, Processors  #1 #2 #3 Ok.
[    0.793891] Brought up 4 CPUs
[    0.793895] Total of 4 processors activated (19151.26 BogoMIPS).
[    0.795490] devtmpfs: initialized
[    0.796352] regulator: core version 0.5
[    0.796376] Time:  9:23:51  Date: 10/29/11
[    0.796402] NET: Registered protocol family 16
[    0.796483] Trying to unpack rootfs image as initramfs...
[    0.796493] ACPI FADT declares the system doesn't support PCIe ASPM, so disable it
[    0.796495] ACPI: bus type pci registered
[    0.796557] PCI: MMCONFIG for domain 0000 [bus 00-ff] at [mem 0xe0000000-0xefffffff] (base 0xe0000000)
[    0.796559] PCI: MMCONFIG at [mem 0xe0000000-0xefffffff] reserved in E820
[    0.857910] PCI: Using configuration type 1 for base access
[    0.858561] bio: create slab <bio-0> at 0
[    0.860252] ACPI: EC: EC description table is found, configuring boot EC
[    0.867933] ACPI: BIOS _OSI(Linux) query ignored
[    0.951179] ACPI: SSDT 00000000bf71aa18 0048D (v01  PmRef  Cpu0Ist 00003000 INTL 20060912)
[    0.951599] ACPI: Dynamic OEM Table Load:
[    0.951601] ACPI: SSDT (null) 0048D (v01  PmRef  Cpu0Ist 00003000 INTL 20060912)
[    0.951921] ACPI: SSDT 00000000bf718718 006B2 (v01  PmRef  Cpu0Cst 00003001 INTL 20060912)
[    0.952351] ACPI: Dynamic OEM Table Load:
[    0.952353] ACPI: SSDT (null) 006B2 (v01  PmRef  Cpu0Cst 00003001 INTL 20060912)
[    0.952881] ACPI: SSDT 00000000bf719a98 00303 (v01  PmRef    ApIst 00003000 INTL 20060912)
[    0.953343] ACPI: Dynamic OEM Table Load:
[    0.953345] ACPI: SSDT (null) 00303 (v01  PmRef    ApIst 00003000 INTL 20060912)
[    0.953519] ACPI: SSDT 00000000bf717d98 00119 (v01  PmRef    ApCst 00003000 INTL 20060912)
[    0.953948] ACPI: Dynamic OEM Table Load:
[    0.953950] ACPI: SSDT (null) 00119 (v01  PmRef    ApCst 00003000 INTL 20060912)
[    0.954954] ACPI: Interpreter enabled
[    0.954956] ACPI: (supports S0 S3 S4 S5)
[    0.954977] ACPI: Using IOAPIC for interrupt routing
[    0.963441] ACPI: EC: GPE = 0x11, I/O: command/status = 0x66, data = 0x62
[    0.963638] ACPI: Power Resource [PUBS] (on)
[    0.965000] ACPI: ACPI Dock Station Driver: 2 docks/bays found
[    0.965003] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
[    0.965017] ACPI: PCI Root Bridge [UNCR] (domain 0000 [bus ff])
[    0.965512] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-fe])
[    0.965555] pci_root PNP0A08:00: host bridge window [io  0x0000-0x0cf7]
[    0.965557] pci_root PNP0A08:00: host bridge window [io  0x0d00-0xffff]
[    0.965560] pci_root PNP0A08:00: host bridge window [mem 0x000a0000-0x000bffff]
[    0.965562] pci_root PNP0A08:00: host bridge window [mem 0x000d4000-0x000d7fff]
[    0.965563] pci_root PNP0A08:00: host bridge window [mem 0x000d8000-0x000dbfff]
[    0.965566] pci_root PNP0A08:00: host bridge window [mem 0xc0000000-0xfebfffff]
[    0.965616] pci 0000:00:01.0: PME# supported from D0 D3hot D3cold
[    0.965619] pci 0000:00:01.0: PME# disabled
[    0.965684] pci 0000:00:16.0: reg 10: [mem 0xf2627800-0xf262780f 64bit]
[    0.965738] pci 0000:00:16.0: PME# supported from D0 D3hot D3cold
[    0.965742] pci 0000:00:16.0: PME# disabled
[    0.965784] pci 0000:00:16.3: reg 10: [io  0x1800-0x1807]
[    0.965791] pci 0000:00:16.3: reg 14: [mem 0xf2624000-0xf2624fff]
[    0.965891] pci 0000:00:19.0: reg 10: [mem 0xf2600000-0xf261ffff]
[    0.965898] pci 0000:00:19.0: reg 14: [mem 0xf2625000-0xf2625fff]
[    0.965904] pci 0000:00:19.0: reg 18: [io  0x1820-0x183f]
[    0.965956] pci 0000:00:19.0: PME# supported from D0 D3hot D3cold
[    0.965960] pci 0000:00:19.0: PME# disabled
[    0.966006] pci 0000:00:1a.0: reg 10: [mem 0xf2628000-0xf26283ff]
[    0.966069] pci 0000:00:1a.0: PME# supported from D0 D3hot D3cold
[    0.966073] pci 0000:00:1a.0: PME# disabled
[    0.966114] pci 0000:00:1b.0: reg 10: [mem 0xf2620000-0xf2623fff 64bit]
[    0.966169] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    0.966173] pci 0000:00:1b.0: PME# disabled
[    0.966259] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    0.966263] pci 0000:00:1c.0: PME# disabled
[    0.966349] pci 0000:00:1c.1: PME# supported from D0 D3hot D3cold
[    0.966353] pci 0000:00:1c.1: PME# disabled
[    0.966442] pci 0000:00:1c.3: PME# supported from D0 D3hot D3cold
[    0.966446] pci 0000:00:1c.3: PME# disabled
[    0.966533] pci 0000:00:1c.4: PME# supported from D0 D3hot D3cold
[    0.966537] pci 0000:00:1c.4: PME# disabled
[    0.966624] pci 0000:00:1c.6: PME# supported from D0 D3hot D3cold
[    0.966628] pci 0000:00:1c.6: PME# disabled
[    0.966715] pci 0000:00:1c.7: PME# supported from D0 D3hot D3cold
[    0.966719] pci 0000:00:1c.7: PME# disabled
[    0.966769] pci 0000:00:1d.0: reg 10: [mem 0xf2628400-0xf26287ff]
[    0.966830] pci 0000:00:1d.0: PME# supported from D0 D3hot D3cold
[    0.966834] pci 0000:00:1d.0: PME# disabled
[    0.967020] pci 0000:00:1f.2: reg 10: [io  0x1818-0x181f]
[    0.967026] pci 0000:00:1f.2: reg 14: [io  0x180c-0x180f]
[    0.967033] pci 0000:00:1f.2: reg 18: [io  0x1810-0x1817]
[    0.967039] pci 0000:00:1f.2: reg 1c: [io  0x1808-0x180b]
[    0.967045] pci 0000:00:1f.2: reg 20: [io  0x1840-0x185f]
[    0.967052] pci 0000:00:1f.2: reg 24: [mem 0xf2627000-0xf26277ff]
[    0.967093] pci 0000:00:1f.2: PME# supported from D3hot
[    0.967097] pci 0000:00:1f.2: PME# disabled
[    0.967132] pci 0000:00:1f.3: reg 10: [mem 0xf2628800-0xf26288ff 64bit]
[    0.967148] pci 0000:00:1f.3: reg 20: [io  0x1860-0x187f]
[    0.967205] pci 0000:00:1f.6: reg 10: [mem 0xf2626000-0xf2626fff 64bit]
[    0.967308] pci 0000:01:00.0: reg 10: [mem 0xcc000000-0xccffffff]
[    0.967318] pci 0000:01:00.0: reg 14: [mem 0xd0000000-0xdfffffff 64bit pref]
[    0.967328] pci 0000:01:00.0: reg 1c: [mem 0xce000000-0xcfffffff 64bit pref]
[    0.967334] pci 0000:01:00.0: reg 24: [io  0x2000-0x207f]
[    0.967339] pci 0000:01:00.0: reg 30: [mem 0x00000000-0x0007ffff pref]
[    0.967400] pci 0000:01:00.1: reg 10: [mem 0xcdefc000-0xcdefffff]
[    0.967465] pci 0000:00:01.0: PCI bridge to [bus 01-01]
[    0.967467] pci 0000:00:01.0:   bridge window [io  0x2000-0x2fff]
[    0.967469] pci 0000:00:01.0:   bridge window [mem 0xcc000000-0xcdefffff]
[    0.967473] pci 0000:00:01.0:   bridge window [mem 0xce000000-0xdfffffff 64bit pref]
[    0.967525] pci 0000:00:1c.0: PCI bridge to [bus 02-02]
[    0.967529] pci 0000:00:1c.0:   bridge window [io  0xf000-0x0000] (disabled)
[    0.967533] pci 0000:00:1c.0:   bridge window [mem 0xfff00000-0x000fffff] (disabled)
[    0.967540] pci 0000:00:1c.0:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    0.967650] pci 0000:03:00.0: reg 10: [mem 0xf2000000-0xf2001fff 64bit]
[    0.967758] pci 0000:03:00.0: PME# supported from D0 D3hot D3cold
[    0.967764] pci 0000:03:00.0: PME# disabled
[    0.967798] pci 0000:00:1c.1: PCI bridge to [bus 03-03]
[    0.967802] pci 0000:00:1c.1:   bridge window [io  0xf000-0x0000] (disabled)
[    0.967806] pci 0000:00:1c.1:   bridge window [mem 0xf2000000-0xf20fffff]
[    0.967813] pci 0000:00:1c.1:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    0.967868] pci 0000:00:1c.3: PCI bridge to [bus 05-0c]
[    0.967872] pci 0000:00:1c.3:   bridge window [io  0x3000-0x3fff]
[    0.967876] pci 0000:00:1c.3:   bridge window [mem 0xf0000000-0xf1ffffff]
[    0.967883] pci 0000:00:1c.3:   bridge window [mem 0xf2700000-0xf27fffff 64bit pref]
[    0.968018] pci 0000:0d:00.0: reg 10: [mem 0xf2100000-0xf21000ff]
[    0.968113] pci 0000:0d:00.0: supports D1 D2
[    0.968114] pci 0000:0d:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.968120] pci 0000:0d:00.0: PME# disabled
[    0.968182] pci 0000:0d:00.1: reg 10: [mem 0xf2100400-0xf21004ff]
[    0.968277] pci 0000:0d:00.1: supports D1 D2
[    0.968279] pci 0000:0d:00.1: PME# supported from D0 D1 D2 D3hot D3cold
[    0.968284] pci 0000:0d:00.1: PME# disabled
[    0.968320] pci 0000:00:1c.4: PCI bridge to [bus 0d-0d]
[    0.968324] pci 0000:00:1c.4:   bridge window [io  0xf000-0x0000] (disabled)
[    0.968328] pci 0000:00:1c.4:   bridge window [mem 0xf2100000-0xf21fffff]
[    0.968334] pci 0000:00:1c.4:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    0.968439] pci 0000:0f:00.0: reg 10: [mem 0xf2200000-0xf2201fff 64bit]
[    0.968537] pci 0000:0f:00.0: PME# supported from D0 D3hot D3cold
[    0.968542] pci 0000:0f:00.0: PME# disabled
[    0.968579] pci 0000:00:1c.6: PCI bridge to [bus 0f-16]
[    0.968583] pci 0000:00:1c.6:   bridge window [io  0xf000-0x0000] (disabled)
[    0.968587] pci 0000:00:1c.6:   bridge window [mem 0xf2200000-0xf22fffff]
[    0.968594] pci 0000:00:1c.6:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    0.968728] pci 0000:17:00.0: reg 10: [mem 0xf2300000-0xf23000ff]
[    0.968824] pci 0000:17:00.0: supports D1 D2
[    0.968825] pci 0000:17:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.968830] pci 0000:17:00.0: PME# disabled
[    0.968896] pci 0000:17:00.3: reg 10: [mem 0xf2300800-0xf2300fff]
[    0.968991] pci 0000:17:00.3: supports D1 D2
[    0.968993] pci 0000:17:00.3: PME# supported from D0 D1 D2 D3hot D3cold
[    0.968998] pci 0000:17:00.3: PME# disabled
[    0.969029] pci 0000:00:1c.7: PCI bridge to [bus 17-1e]
[    0.969033] pci 0000:00:1c.7:   bridge window [io  0xf000-0x0000] (disabled)
[    0.969037] pci 0000:00:1c.7:   bridge window [mem 0xf2300000-0xf23fffff]
[    0.969044] pci 0000:00:1c.7:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    0.969115] pci 0000:00:1e.0: PCI bridge to [bus 1f-1f] (subtractive decode)
[    0.969119] pci 0000:00:1e.0:   bridge window [io  0xf000-0x0000] (disabled)
[    0.969123] pci 0000:00:1e.0:   bridge window [mem 0xfff00000-0x000fffff] (disabled)
[    0.969129] pci 0000:00:1e.0:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    0.969131] pci 0000:00:1e.0:   bridge window [io  0x0000-0x0cf7] (subtractive decode)
[    0.969133] pci 0000:00:1e.0:   bridge window [io  0x0d00-0xffff] (subtractive decode)
[    0.969135] pci 0000:00:1e.0:   bridge window [mem 0x000a0000-0x000bffff] (subtractive decode)
[    0.969137] pci 0000:00:1e.0:   bridge window [mem 0x000d4000-0x000d7fff] (subtractive decode)
[    0.969138] pci 0000:00:1e.0:   bridge window [mem 0x000d8000-0x000dbfff] (subtractive decode)
[    0.969140] pci 0000:00:1e.0:   bridge window [mem 0xc0000000-0xfebfffff] (subtractive decode)
[    0.969184] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.969312] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEG_._PRT]
[    0.969383] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.EXP1._PRT]
[    0.969441] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.EXP2._PRT]
[    0.969503] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.EXP4._PRT]
[    0.969568] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.EXP5._PRT]
[    0.969627] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.EXP7._PRT]
[    0.969686] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.EXP8._PRT]
[    0.974162] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 9 10 *11)
[    0.974326] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 9 10 *11)
[    0.974487] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 9 10 *11)
[    0.974646] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 9 10 *11)
[    0.974806] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 9 10 *11)
[    0.974966] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 9 10 *11)
[    0.975127] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 9 10 *11)
[    0.975286] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 9 10 *11)
[    0.975350] HEST: Table is not found!
[    0.975423] vgaarb: device added: PCI:0000:01:00.0,decodes=io+mem,owns=io+mem,locks=none
[    0.975427] vgaarb: loaded
[    0.975537] SCSI subsystem initialized
[    0.975642] libata version 3.00 loaded.
[    0.975681] usbcore: registered new interface driver usbfs
[    0.975688] usbcore: registered new interface driver hub
[    0.975712] usbcore: registered new device driver usb
[    0.975849] ACPI: WMI: Skipping duplicate GUID 05901221-D566-11D1-B2F0-00A0C9062910
[    0.976114] ACPI: WMI: Mapper loaded
[    0.976116] PCI: Using ACPI for IRQ routing
[    0.976118] PCI: pci_cache_line_size set to 64 bytes
[    0.976427] reserve RAM buffer: 000000000009e800 - 000000000009ffff 
[    0.976429] reserve RAM buffer: 00000000bf27c000 - 00000000bfffffff 
[    0.976433] reserve RAM buffer: 00000000bf34a000 - 00000000bfffffff 
[    0.976437] reserve RAM buffer: 00000000bf45d000 - 00000000bfffffff 
[    0.976440] reserve RAM buffer: 00000000bf717000 - 00000000bfffffff 
[    0.976443] reserve RAM buffer: 00000000bf76c000 - 00000000bfffffff 
[    0.976446] reserve RAM buffer: 00000000bf800000 - 00000000bfffffff 
[    0.976520] NetLabel: Initializing
[    0.976521] NetLabel:  domain hash size = 128
[    0.976522] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.976532] NetLabel:  unlabeled traffic allowed by default
[    0.976564] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0, 0, 0, 0, 0
[    0.976569] hpet0: 8 comparators, 64-bit 14.318180 MHz counter
[    0.978587] Switching to clocksource tsc
[    0.985249] AppArmor: AppArmor Filesystem Enabled
[    0.985266] pnp: PnP ACPI init
[    0.985283] ACPI: bus type pnp registered
[    0.989397] pnp: PnP ACPI: found 12 devices
[    0.989399] ACPI: ACPI bus type pnp unregistered
[    0.989410] system 00:00: [mem 0x00000000-0x0009ffff] could not be reserved
[    0.989412] system 00:00: [mem 0x000c0000-0x000c3fff] has been reserved
[    0.989414] system 00:00: [mem 0x000c4000-0x000c7fff] has been reserved
[    0.989416] system 00:00: [mem 0x000c8000-0x000cbfff] has been reserved
[    0.989418] system 00:00: [mem 0x000cc000-0x000cffff] has been reserved
[    0.989420] system 00:00: [mem 0x000d0000-0x000d3fff] could not be reserved
[    0.989422] system 00:00: [mem 0x000dc000-0x000dffff] could not be reserved
[    0.989424] system 00:00: [mem 0x000e0000-0x000e3fff] could not be reserved
[    0.989426] system 00:00: [mem 0x000e4000-0x000e7fff] could not be reserved
[    0.989428] system 00:00: [mem 0x000e8000-0x000ebfff] could not be reserved
[    0.989430] system 00:00: [mem 0x000ec000-0x000effff] could not be reserved
[    0.989432] system 00:00: [mem 0x000f0000-0x000fffff] could not be reserved
[    0.989434] system 00:00: [mem 0x00100000-0xbfffffff] could not be reserved
[    0.989437] system 00:00: [mem 0xfec00000-0xfed3ffff] could not be reserved
[    0.989439] system 00:00: [mem 0xfed4c000-0xffffffff] could not be reserved
[    0.989444] system 00:03: [io  0x164e-0x164f] has been reserved
[    0.989446] system 00:03: [io  0x1000-0x107f] has been reserved
[    0.989448] system 00:03: [io  0x1180-0x11ff] has been reserved
[    0.989450] system 00:03: [io  0x0800-0x080f] has been reserved
[    0.989452] system 00:03: [io  0x15e0-0x15ef] has been reserved
[    0.989454] system 00:03: [io  0x1600-0x1641] has been reserved
[    0.989456] system 00:03: [io  0x1644-0x167f] could not be reserved
[    0.989459] system 00:03: [mem 0xe0000000-0xefffffff] has been reserved
[    0.989461] system 00:03: [mem 0xfeaff000-0xfeafffff] has been reserved
[    0.989463] system 00:03: [mem 0xfed1c000-0xfed1ffff] has been reserved
[    0.989465] system 00:03: [mem 0xfed10000-0xfed13fff] has been reserved
[    0.989467] system 00:03: [mem 0xfed18000-0xfed18fff] has been reserved
[    0.989469] system 00:03: [mem 0xfed19000-0xfed19fff] has been reserved
[    0.989471] system 00:03: [mem 0xfed45000-0xfed4bfff] has been reserved
[    0.995024] pci 0000:01:00.0: BAR 6: assigned [mem 0xcd000000-0xcd07ffff pref]
[    0.995028] pci 0000:00:01.0: PCI bridge to [bus 01-01]
[    0.995030] pci 0000:00:01.0:   bridge window [io  0x2000-0x2fff]
[    0.995032] pci 0000:00:01.0:   bridge window [mem 0xcc000000-0xcdefffff]
[    0.995035] pci 0000:00:01.0:   bridge window [mem 0xce000000-0xdfffffff 64bit pref]
[    0.995039] pci 0000:00:1c.0: PCI bridge to [bus 02-02]
[    0.995040] pci 0000:00:1c.0:   bridge window [io  disabled]
[    0.995045] pci 0000:00:1c.0:   bridge window [mem disabled]
[    0.995048] pci 0000:00:1c.0:   bridge window [mem pref disabled]
[    0.995055] pci 0000:00:1c.1: PCI bridge to [bus 03-03]
[    0.995057] pci 0000:00:1c.1:   bridge window [io  disabled]
[    0.995062] pci 0000:00:1c.1:   bridge window [mem 0xf2000000-0xf20fffff]
[    0.995066] pci 0000:00:1c.1:   bridge window [mem pref disabled]
[    0.995072] pci 0000:00:1c.3: PCI bridge to [bus 05-0c]
[    0.995075] pci 0000:00:1c.3:   bridge window [io  0x3000-0x3fff]
[    0.995080] pci 0000:00:1c.3:   bridge window [mem 0xf0000000-0xf1ffffff]
[    0.995084] pci 0000:00:1c.3:   bridge window [mem 0xf2700000-0xf27fffff 64bit pref]
[    0.995091] pci 0000:00:1c.4: PCI bridge to [bus 0d-0d]
[    0.995093] pci 0000:00:1c.4:   bridge window [io  disabled]
[    0.995098] pci 0000:00:1c.4:   bridge window [mem 0xf2100000-0xf21fffff]
[    0.995102] pci 0000:00:1c.4:   bridge window [mem pref disabled]
[    0.995108] pci 0000:00:1c.6: PCI bridge to [bus 0f-16]
[    0.995110] pci 0000:00:1c.6:   bridge window [io  disabled]
[    0.995115] pci 0000:00:1c.6:   bridge window [mem 0xf2200000-0xf22fffff]
[    0.995119] pci 0000:00:1c.6:   bridge window [mem pref disabled]
[    0.995125] pci 0000:00:1c.7: PCI bridge to [bus 17-1e]
[    0.995127] pci 0000:00:1c.7:   bridge window [io  disabled]
[    0.995132] pci 0000:00:1c.7:   bridge window [mem 0xf2300000-0xf23fffff]
[    0.995136] pci 0000:00:1c.7:   bridge window [mem pref disabled]
[    0.995142] pci 0000:00:1e.0: PCI bridge to [bus 1f-1f]
[    0.995144] pci 0000:00:1e.0:   bridge window [io  disabled]
[    0.995149] pci 0000:00:1e.0:   bridge window [mem disabled]
[    0.995152] pci 0000:00:1e.0:   bridge window [mem pref disabled]
[    0.995166]   alloc irq_desc for 16 on node -1
[    0.995168]   alloc kstat_irqs on node -1
[    0.995173] pci 0000:00:01.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.995176] pci 0000:00:01.0: setting latency timer to 64
[    0.995185]   alloc irq_desc for 20 on node -1
[    0.995186]   alloc kstat_irqs on node -1
[    0.995189] pci 0000:00:1c.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    0.995193] pci 0000:00:1c.0: setting latency timer to 64
[    0.995203]   alloc irq_desc for 21 on node -1
[    0.995204]   alloc kstat_irqs on node -1
[    0.995207] pci 0000:00:1c.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[    0.995211] pci 0000:00:1c.1: setting latency timer to 64
[    0.995219]   alloc irq_desc for 23 on node -1
[    0.995221]   alloc kstat_irqs on node -1
[    0.995225] pci 0000:00:1c.3: PCI INT D -> GSI 23 (level, low) -> IRQ 23
[    0.995229] pci 0000:00:1c.3: setting latency timer to 64
[    0.995237] pci 0000:00:1c.4: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    0.995241] pci 0000:00:1c.4: setting latency timer to 64
[    0.995250]   alloc irq_desc for 22 on node -1
[    0.995251]   alloc kstat_irqs on node -1
[    0.995254] pci 0000:00:1c.6: PCI INT C -> GSI 22 (level, low) -> IRQ 22
[    0.995258] pci 0000:00:1c.6: setting latency timer to 64
[    0.995266] pci 0000:00:1c.7: PCI INT D -> GSI 23 (level, low) -> IRQ 23
[    0.995270] pci 0000:00:1c.7: setting latency timer to 64
[    0.995277] pci 0000:00:1e.0: setting latency timer to 64
[    0.995282] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
[    0.995283] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff]
[    0.995285] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
[    0.995286] pci_bus 0000:00: resource 7 [mem 0x000d4000-0x000d7fff]
[    0.995288] pci_bus 0000:00: resource 8 [mem 0x000d8000-0x000dbfff]
[    0.995289] pci_bus 0000:00: resource 9 [mem 0xc0000000-0xfebfffff]
[    0.995291] pci_bus 0000:01: resource 0 [io  0x2000-0x2fff]
[    0.995293] pci_bus 0000:01: resource 1 [mem 0xcc000000-0xcdefffff]
[    0.995294] pci_bus 0000:01: resource 2 [mem 0xce000000-0xdfffffff 64bit pref]
[    0.995296] pci_bus 0000:03: resource 1 [mem 0xf2000000-0xf20fffff]
[    0.995298] pci_bus 0000:05: resource 0 [io  0x3000-0x3fff]
[    0.995299] pci_bus 0000:05: resource 1 [mem 0xf0000000-0xf1ffffff]
[    0.995301] pci_bus 0000:05: resource 2 [mem 0xf2700000-0xf27fffff 64bit pref]
[    0.995303] pci_bus 0000:0d: resource 1 [mem 0xf2100000-0xf21fffff]
[    0.995304] pci_bus 0000:0f: resource 1 [mem 0xf2200000-0xf22fffff]
[    0.995306] pci_bus 0000:17: resource 1 [mem 0xf2300000-0xf23fffff]
[    0.995308] pci_bus 0000:1f: resource 4 [io  0x0000-0x0cf7]
[    0.995309] pci_bus 0000:1f: resource 5 [io  0x0d00-0xffff]
[    0.995311] pci_bus 0000:1f: resource 6 [mem 0x000a0000-0x000bffff]
[    0.995312] pci_bus 0000:1f: resource 7 [mem 0x000d4000-0x000d7fff]
[    0.995314] pci_bus 0000:1f: resource 8 [mem 0x000d8000-0x000dbfff]
[    0.995315] pci_bus 0000:1f: resource 9 [mem 0xc0000000-0xfebfffff]
[    0.995345] NET: Registered protocol family 2
[    0.995545] IP route cache hash table entries: 262144 (order: 9, 2097152 bytes)
[    0.996574] TCP established hash table entries: 524288 (order: 11, 8388608 bytes)
[    0.998259] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[    0.998454] TCP: Hash tables configured (established 524288 bind 65536)
[    0.998457] TCP reno registered
[    0.998470] UDP hash table entries: 4096 (order: 5, 131072 bytes)
[    0.998509] UDP-Lite hash table entries: 4096 (order: 5, 131072 bytes)
[    0.998613] NET: Registered protocol family 1
[    0.998748] pci 0000:01:00.0: Boot video device
[    0.998896] PCI: CLS 64 bytes, default 64
[    0.998897] PCI-DMA: Using software bounce buffering for IO (SWIOTLB)
[    0.998900] Placing 64MB software IO TLB between ffff880001f9e000 - ffff880005f9e000
[    0.998901] software IO TLB at phys 0x1f9e000 - 0x5f9e000
[    0.998932] Simple Boot Flag at 0x35 set to 0x1
[    0.999159] Scanning for low memory corruption every 60 seconds
[    0.999283] audit: initializing netlink socket (disabled)
[    0.999294] type=2000 audit(1319880230.790:1): initialized
[    1.011748] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    1.012865] VFS: Disk quotas dquot_6.5.2
[    1.012909] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    1.013371] fuse init (API version 7.14)
[    1.013449] msgmni has been set to 15701
[    1.014044] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    1.014047] io scheduler noop registered
[    1.014048] io scheduler deadline registered
[    1.014077] io scheduler cfq registered (default)
[    1.014181] pcieport 0000:00:01.0: setting latency timer to 64
[    1.014200]   alloc irq_desc for 40 on node -1
[    1.014201]   alloc kstat_irqs on node -1
[    1.014209] pcieport 0000:00:01.0: irq 40 for MSI/MSI-X
[    1.014253] pcieport 0000:00:1c.0: setting latency timer to 64
[    1.014293]   alloc irq_desc for 41 on node -1
[    1.014294]   alloc kstat_irqs on node -1
[    1.014301] pcieport 0000:00:1c.0: irq 41 for MSI/MSI-X
[    1.014368] pcieport 0000:00:1c.1: setting latency timer to 64
[    1.014408]   alloc irq_desc for 42 on node -1
[    1.014409]   alloc kstat_irqs on node -1
[    1.014416] pcieport 0000:00:1c.1: irq 42 for MSI/MSI-X
[    1.014482] pcieport 0000:00:1c.3: setting latency timer to 64
[    1.014522]   alloc irq_desc for 43 on node -1
[    1.014523]   alloc kstat_irqs on node -1
[    1.014530] pcieport 0000:00:1c.3: irq 43 for MSI/MSI-X
[    1.014606] pcieport 0000:00:1c.4: setting latency timer to 64
[    1.014645]   alloc irq_desc for 44 on node -1
[    1.014646]   alloc kstat_irqs on node -1
[    1.014653] pcieport 0000:00:1c.4: irq 44 for MSI/MSI-X
[    1.014721] pcieport 0000:00:1c.6: setting latency timer to 64
[    1.014761]   alloc irq_desc for 45 on node -1
[    1.014762]   alloc kstat_irqs on node -1
[    1.014769] pcieport 0000:00:1c.6: irq 45 for MSI/MSI-X
[    1.014837] pcieport 0000:00:1c.7: setting latency timer to 64
[    1.014876]   alloc irq_desc for 46 on node -1
[    1.014877]   alloc kstat_irqs on node -1
[    1.014884] pcieport 0000:00:1c.7: irq 46 for MSI/MSI-X
[    1.014959] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    1.014976] Firmware did not grant requested _OSC control
[    1.014992] Firmware did not grant requested _OSC control
[    1.014997] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    1.015057] intel_idle: MWAIT substates: 0x1120
[    1.015058] intel_idle: v0.4 model 0x25
[    1.015059] intel_idle: lapic_timer_reliable_states 0xffffffff
[    1.015431] ACPI: AC Adapter [AC] (on-line)
[    1.015487] input: Lid Switch as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0D:00/input/input0
[    1.015657] ACPI: Lid Switch [LID]
[    1.015687] input: Sleep Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0E:00/input/input1
[    1.015691] ACPI: Sleep Button [SLPB]
[    1.015727] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input2
[    1.015730] ACPI: Power Button [PWRF]
[    1.015956] ACPI: acpi_idle yielding to intel_idle
[    1.023769] thermal LNXTHERM:01: registered as thermal_zone0
[    1.023776] ACPI: Thermal Zone [THM0] (32 C)
[    1.023833] ERST: Table is not found!
[    1.024056] Linux agpgart interface v0.103
[    1.024076] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    1.024389]   alloc irq_desc for 17 on node -1
[    1.024391]   alloc kstat_irqs on node -1
[    1.024397] serial 0000:00:16.3: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    1.024518] 0000:00:16.3: ttyS0 at I/O 0x1800 (irq = 17) is a 16550A
[    1.025351] brd: module loaded
[    1.025713] loop: module loaded
[    1.026092] Fixed MDIO Bus: probed
[    1.026115] PPP generic driver version 2.4.2
[    1.026139] tun: Universal TUN/TAP device driver, 1.6
[    1.026140] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    1.026194] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    1.026409] ehci_hcd 0000:00:1a.0: power state changed by ACPI to D0
[    1.027163] ehci_hcd 0000:00:1a.0: power state changed by ACPI to D0
[    1.027171] ehci_hcd 0000:00:1a.0: PCI INT D -> GSI 23 (level, low) -> IRQ 23
[    1.027190] ehci_hcd 0000:00:1a.0: setting latency timer to 64
[    1.027196] ehci_hcd 0000:00:1a.0: EHCI Host Controller
[    1.027226] ehci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 1
[    1.027254] ehci_hcd 0000:00:1a.0: debug port 2
[    1.031127] ehci_hcd 0000:00:1a.0: cache line size of 64 is not supported
[    1.031145] ehci_hcd 0000:00:1a.0: irq 23, io mem 0xf2628000
[    1.048616] ACPI: Battery Slot [BAT0] (battery present)
[    1.053463] ehci_hcd 0000:00:1a.0: USB 2.0 started, EHCI 1.00
[    1.053577] hub 1-0:1.0: USB hub found
[    1.053582] hub 1-0:1.0: 3 ports detected
[    1.053833] ehci_hcd 0000:00:1d.0: power state changed by ACPI to D0
[    1.054024] ehci_hcd 0000:00:1d.0: power state changed by ACPI to D0
[    1.054035]   alloc irq_desc for 19 on node -1
[    1.054037]   alloc kstat_irqs on node -1
[    1.054045] ehci_hcd 0000:00:1d.0: PCI INT D -> GSI 19 (level, low) -> IRQ 19
[    1.054078] ehci_hcd 0000:00:1d.0: setting latency timer to 64
[    1.054082] ehci_hcd 0000:00:1d.0: EHCI Host Controller
[    1.054137] ehci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    1.054172] ehci_hcd 0000:00:1d.0: debug port 2
[    1.058058] ehci_hcd 0000:00:1d.0: cache line size of 64 is not supported
[    1.058079] ehci_hcd 0000:00:1d.0: irq 19, io mem 0xf2628400
[    1.073414] ehci_hcd 0000:00:1d.0: USB 2.0 started, EHCI 1.00
[    1.073573] hub 2-0:1.0: USB hub found
[    1.073579] hub 2-0:1.0: 3 ports detected
[    1.073669] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    1.073687] uhci_hcd: USB Universal Host Controller Interface driver
[    1.073825] PNP: PS/2 Controller [PNP0303:KBD,PNP0f13:MOU] at 0x60,0x64 irq 1,12
[    1.077306] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.077313] serio: i8042 AUX port at 0x60,0x64 irq 12
[    1.077379] mice: PS/2 mouse device common for all mice
[    1.077501] rtc_cmos 00:08: RTC can wake from S4
[    1.077546] rtc_cmos 00:08: rtc core: registered rtc_cmos as rtc0
[    1.077575] rtc0: alarms up to one month, y3k, 114 bytes nvram, hpet irqs
[    1.077675] device-mapper: uevent: version 1.0.3
[    1.077758] device-mapper: ioctl: 4.17.0-ioctl (2010-03-05) initialised: dm-devel@redhat.com
[    1.077869] device-mapper: multipath: version 1.1.1 loaded
[    1.077872] device-mapper: multipath round-robin: version 1.0.0 loaded
[    1.078177] cpuidle: using governor ladder
[    1.078355] cpuidle: using governor menu
[    1.078669] TCP cubic registered
[    1.078809] NET: Registered protocol family 10
[    1.079170] lo: Disabled Privacy Extensions
[    1.079399] NET: Registered protocol family 17
[    1.082004] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input3
[    1.083891] PM: Resume from disk failed.
[    1.083903] registered taskstats version 1
[    1.084491]   Magic number: 15:978:374
[    1.084563] acpi LNXVIDEO:00: hash matches
[    1.084603] rtc_cmos 00:08: setting system clock to 2011-10-29 09:23:51 UTC (1319880231)
[    1.084607] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.084608] EDD information not available.
[    1.099456] Freeing initrd memory: 10744k freed
[    1.101831] Freeing unused kernel memory: 908k freed
[    1.102037] Write protecting the kernel read-only data: 10240k
[    1.102258] Freeing unused kernel memory: 416k freed
[    1.102491] Freeing unused kernel memory: 1644k freed
[    1.115458] udev[99]: starting version 163
[    1.141073] e1000e: Intel(R) PRO/1000 Network Driver - 1.0.2-k4
[    1.141076] e1000e: Copyright (c) 1999 - 2009 Intel Corporation.
[    1.141116] e1000e 0000:00:19.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    1.141130] e1000e 0000:00:19.0: setting latency timer to 64
[    1.141280]   alloc irq_desc for 47 on node -1
[    1.141283]   alloc kstat_irqs on node -1
[    1.141298] e1000e 0000:00:19.0: irq 47 for MSI/MSI-X
[    1.149000] sdhci: Secure Digital Host Controller Interface driver
[    1.149004] sdhci: Copyright(c) Pierre Ossman
[    1.172288] sdhci-pci 0000:0d:00.0: SDHCI controller found [1180:e822] (rev 1)
[    1.172312] sdhci-pci 0000:0d:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.172414] sdhci-pci 0000:0d:00.0: Will use DMA mode even though HW doesn't fully claim to support it.
[    1.172422] sdhci-pci 0000:0d:00.0: setting latency timer to 64
[    1.172529] Registered led device: mmc0::
[    1.172613] mmc0: SDHCI controller on PCI [0000:0d:00.0] using DMA
[    1.172679] sdhci-pci 0000:17:00.0: SDHCI controller found [1180:e822] (rev 1)
[    1.172700] sdhci-pci 0000:17:00.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    1.172767] sdhci-pci 0000:17:00.0: Will use DMA mode even though HW doesn't fully claim to support it.
[    1.172775] sdhci-pci 0000:17:00.0: setting latency timer to 64
[    1.172805] Registered led device: mmc1::
[    1.174426] mmc1: SDHCI controller on PCI [0000:17:00.0] using DMA
[    1.192094]   alloc irq_desc for 18 on node -1
[    1.192098]   alloc kstat_irqs on node -1
[    1.192106] firewire_ohci 0000:17:00.3: PCI INT D -> GSI 18 (level, low) -> IRQ 18
[    1.192160] firewire_ohci 0000:17:00.3: setting latency timer to 64
[    1.339914] e1000e 0000:00:19.0: eth0: (PCI Express:2.5GB/s:Width x1) f0:de:f1:00:37:d4
[    1.339917] e1000e 0000:00:19.0: eth0: Intel(R) PRO/1000 Network Connection
[    1.339984] e1000e 0000:00:19.0: eth0: MAC: 9, PHY: 10, PBA No: a002ff-0ff
[    1.340005] ahci 0000:00:1f.2: version 3.0
[    1.340027] ahci 0000:00:1f.2: PCI INT B -> GSI 16 (level, low) -> IRQ 16
[    1.340092]   alloc irq_desc for 48 on node -1
[    1.340094]   alloc kstat_irqs on node -1
[    1.340107] ahci 0000:00:1f.2: irq 48 for MSI/MSI-X
[    1.340144] ahci: SSS flag set, parallel bus scan disabled
[    1.340186] ahci 0000:00:1f.2: AHCI 0001.0300 32 slots 6 ports 3 Gbps 0x33 impl SATA mode
[    1.340188] ahci 0000:00:1f.2: flags: 64bit ncq sntf ilck stag pm led clo pio slum part ems sxs apst 
[    1.340193] ahci 0000:00:1f.2: setting latency timer to 64
[    1.388086] usb 1-1: new high speed USB device using ehci_hcd and address 2
[    1.410697] scsi0 : ahci
[    1.410868] scsi1 : ahci
[    1.410947] scsi2 : ahci
[    1.411080] scsi3 : ahci
[    1.411187] scsi4 : ahci
[    1.411297] scsi5 : ahci
[    1.412260] ata1: SATA max UDMA/133 abar m2048@0xf2627000 port 0xf2627100 irq 48
[    1.412263] ata2: SATA max UDMA/133 abar m2048@0xf2627000 port 0xf2627180 irq 48
[    1.412265] ata3: DUMMY
[    1.412265] ata4: DUMMY
[    1.412267] ata5: SATA max UDMA/133 abar m2048@0xf2627000 port 0xf2627300 irq 48
[    1.412270] ata6: SATA max UDMA/133 abar m2048@0xf2627000 port 0xf2627380 irq 48
[    1.471612] firewire_ohci: Added fw-ohci device 0000:17:00.3, OHCI v1.10, 4 IR + 4 IT contexts, quirks 0x0
[    1.528748] hub 1-1:1.0: USB hub found
[    1.528844] hub 1-1:1.0: 6 ports detected
[    1.651343] usb 2-1: new high speed USB device using ehci_hcd and address 2
[    1.757406] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    1.758511] ata1.00: ACPI cmd ef/02:00:00:00:00:a0 (SET FEATURES) succeeded
[    1.758519] ata1.00: ACPI cmd f5/00:00:00:00:00:a0 (SECURITY FREEZE LOCK) filtered out
[    1.758771] ata1.00: ACPI cmd ef/5f:00:00:00:00:a0 (SET FEATURES) succeeded
[    1.758779] ata1.00: ACPI cmd ef/10:03:00:00:00:a0 (SET FEATURES) filtered out
[    1.759862] ata1.00: ATA-8: HITACHI HTS725032A9A364, PC3ZC70F, max UDMA/100
[    1.759867] ata1.00: 625142448 sectors, multi 16: LBA48 NCQ (depth 31/32), AA
[    1.761256] ata1.00: ACPI cmd ef/02:00:00:00:00:a0 (SET FEATURES) succeeded
[    1.761262] ata1.00: ACPI cmd f5/00:00:00:00:00:a0 (SECURITY FREEZE LOCK) filtered out
[    1.761535] ata1.00: ACPI cmd ef/5f:00:00:00:00:a0 (SET FEATURES) succeeded
[    1.761541] ata1.00: ACPI cmd ef/10:03:00:00:00:a0 (SET FEATURES) filtered out
[    1.762646] ata1.00: configured for UDMA/100
[    1.782319] ata1.00: configured for UDMA/100
[    1.782325] ata1: EH complete
[    1.782499] scsi 0:0:0:0: Direct-Access     ATA      HITACHI HTS72503 PC3Z PQ: 0 ANSI: 5
[    1.782678] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    1.782691] sd 0:0:0:0: [sda] 625142448 512-byte logical blocks: (320 GB/298 GiB)
[    1.782753] sd 0:0:0:0: [sda] Write Protect is off
[    1.782756] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.782777] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.782876]  sda:
[    1.800838] hub 2-1:1.0: USB hub found
[    1.801099] hub 2-1:1.0: 8 ports detected
[    1.877333] usb 1-1.3: new full speed USB device using ehci_hcd and address 3
[    1.957100] firewire_core: created device fw0: GUID f0def1ff0037d4ff, S400
[    2.079469] usb 1-1.4: new full speed USB device using ehci_hcd and address 4
[    2.091158]  sda1 sda2 sda3 sda4 < sda5 sda6 sda7 >
[    2.123535] sd 0:0:0:0: [sda] Attached SCSI disk
[    2.286641] usb 1-1.6: new high speed USB device using ehci_hcd and address 5
[    2.525977] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    2.529184] ata2.00: ACPI cmd e3/00:1f:00:00:00:a0 (IDLE) succeeded
[    2.529752] ata2.00: ACPI cmd e3/00:02:00:00:00:a0 (IDLE) succeeded
[    2.531511] ata2.00: ATAPI: Optiarc DVD RW AD-7700H, 1.FA, max UDMA/100
[    2.535236] ata2.00: ACPI cmd e3/00:1f:00:00:00:a0 (IDLE) succeeded
[    2.536525] ata2.00: ACPI cmd e3/00:02:00:00:00:a0 (IDLE) succeeded
[    2.538338] ata2.00: configured for UDMA/100
[    2.557568] scsi 1:0:0:0: CD-ROM            Optiarc  DVD RW AD-7700H  1.FA PQ: 0 ANSI: 5
[    2.559714] sr0: scsi3-mmc drive: 62x/62x writer dvd-ram cd/rw xa/form2 cdda tray
[    2.559720] Uniform CD-ROM driver Revision: 3.20
[    2.559888] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    2.559940] sr 1:0:0:0: Attached scsi generic sg1 type 5
[    2.905267] ata5: SATA link down (SStatus 0 SControl 300)
[    3.274577] ata6: SATA link down (SStatus 0 SControl 300)
[    4.724933] EXT4-fs (sda5): INFO: recovery required on readonly filesystem
[    4.724937] EXT4-fs (sda5): write access will be enabled during recovery
[    6.659250] EXT4-fs (sda5): orphan cleanup on readonly fs
[    6.659258] EXT4-fs (sda5): ext4_orphan_cleanup: deleting unreferenced inode 1059084
[    6.659308] EXT4-fs (sda5): ext4_orphan_cleanup: deleting unreferenced inode 1059081
[    6.659325] EXT4-fs (sda5): ext4_orphan_cleanup: deleting unreferenced inode 1059045
[    6.659334] EXT4-fs (sda5): ext4_orphan_cleanup: deleting unreferenced inode 1059044
[    6.659343] EXT4-fs (sda5): ext4_orphan_cleanup: deleting unreferenced inode 262692
[    6.659353] EXT4-fs (sda5): ext4_orphan_cleanup: deleting unreferenced inode 1059043
[    6.659362] EXT4-fs (sda5): ext4_orphan_cleanup: deleting unreferenced inode 1059042
[    6.659370] EXT4-fs (sda5): ext4_orphan_cleanup: deleting unreferenced inode 1059040
[    6.659379] EXT4-fs (sda5): ext4_orphan_cleanup: deleting unreferenced inode 1059034
[    6.659387] EXT4-fs (sda5): ext4_orphan_cleanup: deleting unreferenced inode 1059032
[    6.659396] EXT4-fs (sda5): ext4_orphan_cleanup: deleting unreferenced inode 1059036
[    6.659412] EXT4-fs (sda5): ext4_orphan_cleanup: deleting unreferenced inode 1058998
[    6.659422] EXT4-fs (sda5): ext4_orphan_cleanup: deleting unreferenced inode 1058984
[    6.659430] EXT4-fs (sda5): ext4_orphan_cleanup: deleting unreferenced inode 262690
[    6.659440] EXT4-fs (sda5): ext4_orphan_cleanup: deleting unreferenced inode 262689
[    6.659453] EXT4-fs (sda5): ext4_orphan_cleanup: deleting unreferenced inode 262688
[    6.659463] EXT4-fs (sda5): ext4_orphan_cleanup: deleting unreferenced inode 262687
[    6.659475] EXT4-fs (sda5): ext4_orphan_cleanup: deleting unreferenced inode 262686
[    6.659483] EXT4-fs (sda5): ext4_orphan_cleanup: deleting unreferenced inode 262356
[    6.659492] EXT4-fs (sda5): ext4_orphan_cleanup: deleting unreferenced inode 1058981
[    6.659501] EXT4-fs (sda5): ext4_orphan_cleanup: deleting unreferenced inode 1057421
[    6.659516] EXT4-fs (sda5): ext4_orphan_cleanup: deleting unreferenced inode 1059004
[    6.659532] EXT4-fs (sda5): ext4_orphan_cleanup: deleting unreferenced inode 1058882
[    6.659553] EXT4-fs (sda5): ext4_orphan_cleanup: deleting unreferenced inode 1058881
[    6.659571] EXT4-fs (sda5): ext4_orphan_cleanup: deleting unreferenced inode 131135
[    6.659586] EXT4-fs (sda5): ext4_orphan_cleanup: deleting unreferenced inode 1322297
[    6.659612] EXT4-fs (sda5): ext4_orphan_cleanup: deleting unreferenced inode 1058909
[    6.659622] EXT4-fs (sda5): ext4_orphan_cleanup: deleting unreferenced inode 1058908
[    6.659631] EXT4-fs (sda5): ext4_orphan_cleanup: deleting unreferenced inode 135898
[    6.659641] EXT4-fs (sda5): ext4_orphan_cleanup: deleting unreferenced inode 135897
[    6.659650] EXT4-fs (sda5): ext4_orphan_cleanup: deleting unreferenced inode 135896
[    6.659658] EXT4-fs (sda5): ext4_orphan_cleanup: deleting unreferenced inode 135888
[    6.659668] EXT4-fs (sda5): ext4_orphan_cleanup: deleting unreferenced inode 135690
[    6.659677] EXT4-fs (sda5): ext4_orphan_cleanup: deleting unreferenced inode 135109
[    6.659685] EXT4-fs (sda5): ext4_orphan_cleanup: deleting unreferenced inode 135108
[    6.659693] EXT4-fs (sda5): ext4_orphan_cleanup: deleting unreferenced inode 135106
[    6.659702] EXT4-fs (sda5): ext4_orphan_cleanup: deleting unreferenced inode 131136
[    6.659709] EXT4-fs (sda5): 37 orphan inodes deleted
[    6.659711] EXT4-fs (sda5): recovery complete
[    6.885475] EXT4-fs (sda5): mounted filesystem with ordered data mode. Opts: (null)
[   13.812093] udev[461]: starting version 163
[   13.840692] Adding 9854972k swap on /dev/sda7.  Priority:-1 extents:1 across:9854972k 
[   13.900874] intel ips 0000:00:1f.6: Warning: CPU TDP doesn't match expected value (found 25, expected 35)
[   13.900898] intel ips 0000:00:1f.6: PCI INT D -> GSI 19 (level, low) -> IRQ 19
[   13.901069] intel ips 0000:00:1f.6: failed to get i915 symbols, graphics turbo disabled
[   13.904358] Linux video capture interface: v2.00
[   13.914162] lp: driver loaded but no devices found
[   13.914542] cfg80211: Calling CRDA to update world regulatory domain
[   13.916635] uvcvideo: Found UVC 1.00 device Integrated Camera (17ef:480f)
[   13.920743] input: Integrated Camera as /devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.6/1-1.6:1.0/input/input4
[   13.920852] usbcore: registered new interface driver uvcvideo
[   13.920855] USB Video Class driver (v0.1.0)
[   13.934341] xhci_hcd 0000:0f:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[   13.934395] xhci_hcd 0000:0f:00.0: setting latency timer to 64
[   13.934400] xhci_hcd 0000:0f:00.0: xHCI Host Controller
[   13.934509] xhci_hcd 0000:0f:00.0: new USB bus registered, assigned bus number 3
[   13.934764] xhci_hcd 0000:0f:00.0: irq 18, io mem 0xf2200000
[   13.938019] usb usb3: No SuperSpeed endpoint companion for config 1  interface 0 altsetting 0 ep 129: using minimum values
[   13.938209] xHCI xhci_add_endpoint called for root hub
[   13.938212] xHCI xhci_check_bandwidth called for root hub
[   13.938247] hub 3-0:1.0: USB hub found
[   13.938253] hub 3-0:1.0: 4 ports detected
[   13.955469] intel ips 0000:00:1f.6: IPS driver initialized, MCP temp limit 65535
[   13.960616] type=1400 audit(1319873044.396:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient3" pid=713 comm="apparmor_parser"
[   13.961099] type=1400 audit(1319873044.396:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=713 comm="apparmor_parser"
[   13.961467] type=1400 audit(1319873044.396:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=713 comm="apparmor_parser"
[   14.000645] Non-volatile memory driver v1.3
[   14.007837] cfg80211: World regulatory domain updated:
[   14.007840]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   14.007843]     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   14.007845]     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   14.007847]     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   14.007849]     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   14.007852]     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   14.015075] Bluetooth: Core ver 2.15
[   14.015099] NET: Registered protocol family 31
[   14.015100] Bluetooth: HCI device and connection manager initialized
[   14.015103] Bluetooth: HCI socket layer initialized
[   14.021833] acpi device:03: registered as cooling_device4
[   14.022436] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:02/LNXVIDEO:00/input/input5
[   14.022550] ACPI: Video Device [VID] (multi-head: yes  rom: no  post: no)
[   14.026410] Bluetooth: Generic Bluetooth USB driver ver 0.6
[   14.026586] usbcore: registered new interface driver btusb
[   14.028606] tpm_tis 00:0b: 1.2 TPM (device-id 0x0, rev-id 78)
[   14.088604] iwlagn: Intel(R) Wireless WiFi Link AGN driver for Linux, in-tree:
[   14.088607] iwlagn: Copyright(c) 2003-2010 Intel Corporation
[   14.088669] iwlagn 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   14.088677] iwlagn 0000:03:00.0: setting latency timer to 64
[   14.088733] iwlagn 0000:03:00.0: Detected Intel(R) Centrino(R) Ultimate-N 6300 AGN, REV=0x74
[   14.098038] iwlagn 0000:03:00.0: Tunable channels: 13 802.11bg, 24 802.11a channels
[   14.098147]   alloc irq_desc for 49 on node -1
[   14.098149]   alloc kstat_irqs on node -1
[   14.098201] iwlagn 0000:03:00.0: irq 49 for MSI/MSI-X
[   14.117713] thinkpad_acpi: ThinkPad ACPI Extras v0.24
[   14.117717] thinkpad_acpi: http://ibm-acpi.sf.net/
[   14.117719] thinkpad_acpi: ThinkPad BIOS 6LET66WW (1.31 ), EC 6MHT38WW-1.13
[   14.117722] thinkpad_acpi: Lenovo ThinkPad W510, model 43195RU
[   14.118787] thinkpad_acpi: detected a 8-level brightness capable ThinkPad
[   14.119092] thinkpad_acpi: radio switch found; radios are enabled
[   14.119295] HDA Intel 0000:00:1b.0: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[   14.119418]   alloc irq_desc for 50 on node -1
[   14.119421]   alloc kstat_irqs on node -1
[   14.119437] HDA Intel 0000:00:1b.0: irq 50 for MSI/MSI-X
[   14.119648] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   14.123893] thinkpad_acpi: rfkill switch tpacpi_bluetooth_sw: radio is unblocked
[   14.124506] iwlagn 0000:03:00.0: loaded firmware version 9.221.4.1 build 25532
[   14.124691] Registered led device: tpacpi::thinklight
[   14.124757] Registered led device: tpacpi::power
[   14.124773] Registered led device: tpacpi::standby
[   14.124797] Registered led device: tpacpi::thinkvantage
[   14.129554] thinkpad_acpi: Console audio control enabled, mode: monitor (read only)
[   14.132655] input: ThinkPad Extra Buttons as /devices/platform/thinkpad_acpi/input/input6
[   14.135704] phy0: Selected rate control algorithm 'iwl-agn-rs'
[   14.232488] HDA Intel 0000:01:00.1: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   14.232492] hda_intel: Disable MSI for Nvidia chipset
[   14.232562] HDA Intel 0000:01:00.1: setting latency timer to 64
[   14.298673] nvidia: module license 'NVIDIA' taints kernel.
[   14.298677] Disabling lock debugging due to kernel taint
[   14.369097] EXT4-fs (sda5): re-mounted. Opts: errors=remount-ro
[   14.767385] Synaptics Touchpad, model: 1, fw: 7.2, id: 0x1c0b1, caps: 0xd047b1/0xb40000/0xa0000
[   14.767390] Synaptics: Clickpad mode enabled
[   14.767395] serio: Synaptics pass-through port at isa0060/serio1/input0
[   14.821060] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input7
[   14.836294] type=1400 audit(1319873045.266:5): apparmor="STATUS" operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" pid=1046 comm="apparmor_parser"
[   14.836325] type=1400 audit(1319873045.266:6): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient3" pid=1047 comm="apparmor_parser"
[   14.836818] type=1400 audit(1319873045.276:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=1047 comm="apparmor_parser"
[   14.837100] type=1400 audit(1319873045.276:8): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=1047 comm="apparmor_parser"
[   14.837391] type=1400 audit(1319873045.276:9): apparmor="STATUS" operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" pid=1050 comm="apparmor_parser"
[   14.837595] type=1400 audit(1319873045.276:10): apparmor="STATUS" operation="profile_load" name="/usr/sbin/tcpdump" pid=1051 comm="apparmor_parser"
[   14.838060] type=1400 audit(1319873045.276:11): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince" pid=1048 comm="apparmor_parser"
[   15.341206] Bluetooth: L2CAP ver 2.14
[   15.341209] Bluetooth: L2CAP socket layer initialized
[   15.346444] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   15.346447] Bluetooth: BNEP filters: protocol multicast
[   15.349839] Bluetooth: SCO (Voice Link) ver 0.6
[   15.349841] Bluetooth: SCO socket layer initialized
[   15.392224] e1000e 0000:00:19.0: irq 47 for MSI/MSI-X
[   15.412427] Bluetooth: RFCOMM TTY layer initialized
[   15.412433] Bluetooth: RFCOMM socket layer initialized
[   15.412435] Bluetooth: RFCOMM ver 1.11
[   15.451953] e1000e 0000:00:19.0: irq 47 for MSI/MSI-X
[   15.452602] ADDRCONF(NETDEV_UP): eth0: link is not ready

```

---

### Post by matt_symes on 2011-10-31
Hi

```
[    6.659258] EXT4-fs (sda5): ext4_orphan_cleanup: deleting unreferenced inode 1059084
[    6.659308] EXT4-fs (sda5): ext4_orphan_cleanup: deleting unreferenced inode 1059081
[    6.659325] EXT4-fs (sda5): ext4_orphan_cleanup: deleting unreferenced inode 1059045
[    6.659334] EXT4-fs (sda5): ext4_orphan_cleanup: deleting unreferenced inode 1059044
[    6.659343] EXT4-fs (sda5): ext4_orphan_cleanup: deleting unreferenced inode 262692
[    6.659353] EXT4-fs (sda5): ext4_orphan_cleanup: deleting unreferenced inode 1059043
[    6.659362] EXT4-fs (sda5): ext4_orphan_cleanup: deleting unreferenced inode 1059042
[    6.659370] EXT4-fs (sda5): ext4_orphan_cleanup: deleting unreferenced inode 1059040
[    6.659379] EXT4-fs (sda5): ext4_orphan_cleanup: deleting unreferenced inode 1059034
[    6.659387] EXT4-fs (sda5): ext4_orphan_cleanup: deleting unreferenced inode 1059032
[    6.659396] EXT4-fs (sda5): ext4_orphan_cleanup: deleting unreferenced inode 1059036
```

You have had filesystem damage. I would run fsck from a LiveCD/USB. 

Perform a test run first and see what that returns.

Mount the partition and then...

```
fsck -N /mount/point
```

to check. If it returns damage then run fsck without the -N switch.

Kind regards

---

