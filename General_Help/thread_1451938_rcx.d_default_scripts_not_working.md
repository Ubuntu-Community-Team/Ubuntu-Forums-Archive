---
title: "rcx.d default scripts not working"
date: 2010-04-11
forum: General Help
---

### Post by Bob Bertrands on 2010-04-11
Hey

First of all I am using ubuntu for 1 year now but I'm still at the beginning stage of learing to work with linux. 

This said I've been experimenting somewhat with Ubuntu and apparently I've messed up big time.

The first thing I noticed was that my ftp-server stopped running (vsftpd). Something I ignored cause I wasn't using my ftp-server at the time. And I was still able to start the ftp manually (sudo /etc/init.d/vsftp start)

Because I had wired internet  I didn't notice my wireless stopped working at well.
Now yesterday I moved my computer. I suddenly noticed my wireless wasn't working an on top of all when I tried to ssh in to my pc, it failed. (Hadn't ssh'd into my pc for weeks)
However, like with the ftp server, I can still start ssh manually (sudo /etc/init.d/ssh start)

So I started looking and found out that the scripts supposed to start the ftp and ssh server at boot are located in the /etc/rcx.d directory's.

I'm using Keramic Koala and was hoping you guys could help me out

Thanks

B

---

### Post by Bob Bertrands on 2010-04-11
btw 
here's my dmesg output:

```
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.31-16-generic (buildd@crested) (gcc version 4.4.1 (Ubuntu 4.4.1-4ubuntu8) ) #53-Ubuntu SMP Tue Dec 8 04:02:15 UTC 2009 (Ubuntu 2.6.31-16.53-generic)
[    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-2.6.31-16-generic root=UUID=064b97d9-6343-48f5-874a-d519ceff575e ro quiet splash
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   Centaur CentaurHauls
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009e000 (usable)
[    0.000000]  BIOS-e820: 000000000009e000 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 00000000bfc6b000 (usable)
[    0.000000]  BIOS-e820: 00000000bfc6b000 - 00000000bfcbf000 (reserved)
[    0.000000]  BIOS-e820: 00000000bfcbf000 - 00000000bfd83000 (usable)
[    0.000000]  BIOS-e820: 00000000bfd83000 - 00000000bfdbf000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000bfdbf000 - 00000000bfddf000 (usable)
[    0.000000]  BIOS-e820: 00000000bfddf000 - 00000000bfdf7000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000bfdf7000 - 00000000bfe00000 (usable)
[    0.000000]  BIOS-e820: 00000000bfe00000 - 00000000c0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000f8000000 - 00000000fc000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed10000 - 00000000fed14000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed18000 - 00000000fed1a000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed1c000 - 00000000fed20000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fff00000 - 0000000100000000 (reserved)
[    0.000000] DMI 2.4 present.
[    0.000000] last_pfn = 0xbfe00 max_arch_pfn = 0x400000000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000 mask F80000000 write-back
[    0.000000]   1 base 080000000 mask FC0000000 write-back
[    0.000000]   2 base 0FFF00000 mask FFFF00000 write-protect
[    0.000000]   3 base 0BFE00000 mask FFFE00000 uncachable
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
[    0.000000]  modified: 0000000000006000 - 000000000009e000 (usable)
[    0.000000]  modified: 000000000009e000 - 00000000000a0000 (reserved)
[    0.000000]  modified: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  modified: 0000000000100000 - 00000000bfc6b000 (usable)
[    0.000000]  modified: 00000000bfc6b000 - 00000000bfcbf000 (reserved)
[    0.000000]  modified: 00000000bfcbf000 - 00000000bfd83000 (usable)
[    0.000000]  modified: 00000000bfd83000 - 00000000bfdbf000 (ACPI NVS)
[    0.000000]  modified: 00000000bfdbf000 - 00000000bfddf000 (usable)
[    0.000000]  modified: 00000000bfddf000 - 00000000bfdf7000 (ACPI data)
[    0.000000]  modified: 00000000bfdf7000 - 00000000bfe00000 (usable)
[    0.000000]  modified: 00000000bfe00000 - 00000000c0000000 (reserved)
[    0.000000]  modified: 00000000f8000000 - 00000000fc000000 (reserved)
[    0.000000]  modified: 00000000fec00000 - 00000000fec01000 (reserved)
[    0.000000]  modified: 00000000fed10000 - 00000000fed14000 (reserved)
[    0.000000]  modified: 00000000fed18000 - 00000000fed1a000 (reserved)
[    0.000000]  modified: 00000000fed1c000 - 00000000fed20000 (reserved)
[    0.000000]  modified: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  modified: 00000000fff00000 - 0000000100000000 (reserved)
[    0.000000] initial memory mapped : 0 - 20000000
[    0.000000] init_memory_mapping: 0000000000000000-00000000bfe00000
[    0.000000] NX (Execute Disable) protection: active
[    0.000000]  0000000000 - 00bfe00000 page 2M
[    0.000000] kernel direct mapping tables up to bfe00000 @ 8000-c000
[    0.000000] RAMDISK: 37833000 - 37fef27b
[    0.000000] ACPI: RSDP 00000000000fe020 00024 (v02 HP    )
[    0.000000] ACPI: XSDT 00000000bfdf6120 00074 (v01 HPQOEM SLIC-MPC 00000001      01000013)
[    0.000000] ACPI: FACP 00000000bfdf3000 000F4 (v04 HP     VADER    00000001 MSFT 01000013)
[    0.000000] ACPI: DSDT 00000000bfde4000 0A5B2 (v01 HP     VADER    00000001 MSFT 01000013)
[    0.000000] ACPI: FACS 00000000bfd8c000 00040
[    0.000000] ACPI: DMAR 00000000bfdf5000 00040 (v01                00000001      00000000)
[    0.000000] ACPI: SSDT 00000000bfdf4000 00655 (v01  PmRef    CpuPm 00003000 INTL 20051117)
[    0.000000] ACPI: HPET 00000000bfdf2000 00038 (v01 HPQOEM SLIC-MPC 00000001 MSFT 01000013)
[    0.000000] ACPI: APIC 00000000bfdf1000 0006C (v02 HPQOEM SLIC-MPC 00000001 MSFT 01000013)
[    0.000000] ACPI: MCFG 00000000bfdf0000 0003C (v01 HPQOEM SLIC-MPC 00000001 MSFT 01000013)
[    0.000000] ACPI: ASF! 00000000bfdef000 000A5 (v32 HPQOEM SLIC-MPC 00000001 MSFT 01000013)
[    0.000000] ACPI: SLIC 00000000bfde3000 00176 (v01 HPQOEM SLIC-MPC 00000001 LOHR 000F4240)
[    0.000000] ACPI: BOOT 00000000bfde2000 00028 (v01 HPQOEM SLIC-MPC 00000001 MSFT 01000013)
[    0.000000] ACPI: SSDT 00000000bfde1000 00296 (v01 INTEL  SataAhci 00001000 INTL 20051117)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] No NUMA configuration found
[    0.000000] Faking a node at 0000000000000000-00000000bfe00000
[    0.000000] Bootmem setup node 0 0000000000000000-00000000bfe00000
[    0.000000]   NODE_DATA [000000000000a000 - 000000000000efff]
[    0.000000]   bootmap [000000000000f000 -  0000000000026fbf] pages 18
[    0.000000] (7 early reservations) ==> bootmem [0000000000 - 00bfe00000]
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
[    0.000000]   #1 [0000006000 - 0000008000]       TRAMPOLINE ==> [0000006000 - 0000008000]
[    0.000000]   #2 [0001000000 - 00019e4ccc]    TEXT DATA BSS ==> [0001000000 - 00019e4ccc]
[    0.000000]   #3 [0037833000 - 0037fef27b]          RAMDISK ==> [0037833000 - 0037fef27b]
[    0.000000]   #4 [000009e000 - 0000100000]    BIOS reserved ==> [000009e000 - 0000100000]
[    0.000000]   #5 [00019e5000 - 00019e5208]              BRK ==> [00019e5000 - 00019e5208]
[    0.000000]   #6 [0000008000 - 000000a000]          PGTABLE ==> [0000008000 - 000000a000]
[    0.000000]  [ffffea0000000000-ffffea00029fffff] PMD -> [ffff880001e00000-ffff8800047fffff] on node 0
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000000 -> 0x00001000
[    0.000000]   DMA32    0x00001000 -> 0x00100000
[    0.000000]   Normal   0x00100000 -> 0x00100000
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[6] active PFN ranges
[    0.000000]     0: 0x00000000 -> 0x00000001
[    0.000000]     0: 0x00000006 -> 0x0000009e
[    0.000000]     0: 0x00000100 -> 0x000bfc6b
[    0.000000]     0: 0x000bfcbf -> 0x000bfd83
[    0.000000]     0: 0x000bfdbf -> 0x000bfddf
[    0.000000]     0: 0x000bfdf7 -> 0x000bfe00
[    0.000000] On node 0 totalpages: 785649
[    0.000000]   DMA zone: 56 pages used for memmap
[    0.000000]   DMA zone: 103 pages reserved
[    0.000000]   DMA zone: 3834 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 10689 pages used for memmap
[    0.000000]   DMA32 zone: 770967 pages, LIFO batch:31
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
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000
[    0.000000] SMP: Allowing 4 CPUs, 2 hotplug CPUs
[    0.000000] nr_irqs_gsi: 24
[    0.000000] PM: Registered nosave memory: 0000000000001000 - 0000000000006000
[    0.000000] PM: Registered nosave memory: 000000000009e000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
[    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
[    0.000000] PM: Registered nosave memory: 00000000bfc6b000 - 00000000bfcbf000
[    0.000000] PM: Registered nosave memory: 00000000bfd83000 - 00000000bfdbf000
[    0.000000] PM: Registered nosave memory: 00000000bfddf000 - 00000000bfdf7000
[    0.000000] Allocating PCI resources starting at c0000000 (gap: c0000000:38000000)
[    0.000000] NR_CPUS:64 nr_cpumask_bits:64 nr_cpu_ids:4 nr_node_ids:1
[    0.000000] PERCPU: Embedded 30 pages at ffff880001a03000, static data 90720 bytes
[    0.000000] Built 1 zonelists in Node order, mobility grouping on.  Total pages: 774801
[    0.000000] Policy zone: DMA32
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.31-16-generic root=UUID=064b97d9-6343-48f5-874a-d519ceff575e ro quiet splash
[    0.000000] PID hash table entries: 4096 (order: 12, 32768 bytes)
[    0.000000] Initializing CPU#0
[    0.000000] Checking aperture...
[    0.000000] No AGP bridge found
[    0.000000] Calgary: detecting Calgary via BIOS EBDA area
[    0.000000] Calgary: Unable to locate Rio Grande table in EBDA - bailing!
[    0.000000] Memory: 3080828k/3143680k available (5315k kernel code, 1084k absent, 61768k reserved, 3018k data, 660k init)
[    0.000000] SLUB: Genslabs=14, HWalign=64, Order=0-3, MinObjects=0, CPUs=4, Nodes=1
[    0.000000] NR_IRQS:4352 nr_irqs:440
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 1995.632 MHz processor.
[    0.002261] Console: colour VGA+ 80x25
[    0.002264] console [tty0] enabled
[    0.010000] allocated 31457280 bytes of page_cgroup
[    0.010000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.010000] hpet clockevent registered
[    0.010000] HPET: 4 timers in total, 0 timers will be used for per-cpu timer
[    0.010000] Calibrating delay loop (skipped), value calculated using timer frequency.. 3991.26 BogoMIPS (lpj=19956320)
[    0.010000] Security Framework initialized
[    0.010000] AppArmor: AppArmor initialized
[    0.010000] Dentry cache hash table entries: 524288 (order: 10, 4194304 bytes)
[    0.010000] Inode-cache hash table entries: 262144 (order: 9, 2097152 bytes)
[    0.010000] Mount-cache hash table entries: 256
[    0.010000] Initializing cgroup subsys ns
[    0.010000] Initializing cgroup subsys cpuacct
[    0.010000] Initializing cgroup subsys memory
[    0.010000] Initializing cgroup subsys freezer
[    0.010000] Initializing cgroup subsys net_cls
[    0.010000] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.010000] CPU: L2 cache: 2048K
[    0.010000] CPU 0/0x0 -> Node 0
[    0.010000] CPU: Physical Processor ID: 0
[    0.010000] CPU: Processor Core ID: 0
[    0.010000] mce: CPU supports 6 MCE banks
[    0.010000] CPU0: Thermal monitoring enabled (TM1)
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
[    0.030062] Setting APIC routing to flat
[    0.030414] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.138437] CPU0: Intel(R) Core(TM)2 Duo CPU     T5800  @ 2.00GHz stepping 0d
[    0.140000] Booting processor 1 APIC 0x1 ip 0x6000
[    0.010000] Initializing CPU#1
[    0.010000] Calibrating delay using timer specific routine.. 3990.44 BogoMIPS (lpj=19952244)
[    0.010000] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.010000] CPU: L2 cache: 2048K
[    0.010000] CPU 1/0x1 -> Node 0
[    0.010000] CPU: Physical Processor ID: 0
[    0.010000] CPU: Processor Core ID: 1
[    0.010000] mce: CPU supports 6 MCE banks
[    0.010000] CPU1: Thermal monitoring enabled (TM1)
[    0.010000] x86 PAT enabled: cpu 1, old 0x7040600070406, new 0x7010600070106
[    0.291376] CPU1: Intel(R) Core(TM)2 Duo CPU     T5800  @ 2.00GHz stepping 0d
[    0.291385] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
[    0.300025] Brought up 2 CPUs
[    0.300028] Total of 2 processors activated (7981.71 BogoMIPS).
[    0.300083] CPU0 attaching sched-domain:
[    0.300086]  domain 0: span 0-1 level MC
[    0.300089]   groups: 0 1
[    0.300094] CPU1 attaching sched-domain:
[    0.300096]  domain 0: span 0-1 level MC
[    0.300098]   groups: 1 0
[    0.300171] Booting paravirtualized kernel on bare hardware
[    0.300180] regulator: core version 0.5
[    0.300180] Time: 11:01:55  Date: 04/18/10
[    0.300180] NET: Registered protocol family 16
[    0.300219] ACPI: bus type pci registered
[    0.300298] PCI: MCFG configuration 0: base f8000000 segment 0 buses 0 - 63
[    0.300301] PCI: MCFG area at f8000000 reserved in E820
[    0.301495] PCI: Using MMCONFIG at f8000000 - fbffffff
[    0.301497] PCI: Using configuration type 1 for base access
[    0.302376] bio: create slab <bio-0> at 0
[    0.302376] ACPI: EC: Enabling special treatment for EC from MSI.
[    0.302376] ACPI: EC: Look up EC in DSDT
[    0.354662] ACPI: BIOS _OSI(Linux) query ignored
[    0.360015] ACPI: EC: non-query interrupt received, switching to interrupt mode
[    0.550405] ACPI: Interpreter enabled
[    0.550405] ACPI: (supports S0 S3 S4 S5)
[    0.550405] ACPI: Using IOAPIC for interrupt routing
[    0.790186] [Firmware Bug]: ACPI: ACPI brightness control misses _BQC function
[    0.790875] [Firmware Bug]: ACPI: ACPI brightness control misses _BQC function
[    0.820477] ACPI: EC: GPE = 0x17, I/O: command/status = 0x66, data = 0x62
[    0.820479] ACPI: EC: driver started in interrupt mode
[    0.830103] ACPI: Power Resource [FN00] (on)
[    0.830526] ACPI: No dock devices found.
[    0.831060] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.831183] pci 0000:00:01.0: PME# supported from D0 D3hot D3cold
[    0.831187] pci 0000:00:01.0: PME# disabled
[    0.831311] pci 0000:00:1a.0: reg 20 io port: [0x80e0-0x80ff]
[    0.831447] pci 0000:00:1a.1: reg 20 io port: [0x80c0-0x80df]
[    0.831566] pci 0000:00:1a.7: reg 10 32bit mmio: [0xdf004c00-0xdf004fff]
[    0.831643] pci 0000:00:1a.7: PME# supported from D0 D3hot D3cold
[    0.831648] pci 0000:00:1a.7: PME# disabled
[    0.831705] pci 0000:00:1b.0: reg 10 64bit mmio: [0xdf000000-0xdf003fff]
[    0.831767] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    0.831772] pci 0000:00:1b.0: PME# disabled
[    0.831855] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    0.831860] pci 0000:00:1c.0: PME# disabled
[    0.831945] pci 0000:00:1c.1: PME# supported from D0 D3hot D3cold
[    0.831950] pci 0000:00:1c.1: PME# disabled
[    0.832039] pci 0000:00:1c.2: PME# supported from D0 D3hot D3cold
[    0.832043] pci 0000:00:1c.2: PME# disabled
[    0.832120] pci 0000:00:1c.3: PME# supported from D0 D3hot D3cold
[    0.832125] pci 0000:00:1c.3: PME# disabled
[    0.832212] pci 0000:00:1c.4: PME# supported from D0 D3hot D3cold
[    0.832217] pci 0000:00:1c.4: PME# disabled
[    0.832303] pci 0000:00:1c.5: PME# supported from D0 D3hot D3cold
[    0.832308] pci 0000:00:1c.5: PME# disabled
[    0.832407] pci 0000:00:1d.0: reg 20 io port: [0x80a0-0x80bf]
[    0.832541] pci 0000:00:1d.1: reg 20 io port: [0x8080-0x809f]
[    0.832673] pci 0000:00:1d.2: reg 20 io port: [0x8060-0x807f]
[    0.832797] pci 0000:00:1d.3: reg 20 io port: [0x8040-0x805f]
[    0.832914] pci 0000:00:1d.7: reg 10 32bit mmio: [0xdf004800-0xdf004bff]
[    0.832989] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
[    0.832994] pci 0000:00:1d.7: PME# disabled
[    0.833228] pci 0000:00:1f.2: reg 10 io port: [0x8108-0x810f]
[    0.833236] pci 0000:00:1f.2: reg 14 io port: [0x8114-0x8117]
[    0.833244] pci 0000:00:1f.2: reg 18 io port: [0x8100-0x8107]
[    0.833252] pci 0000:00:1f.2: reg 1c io port: [0x8110-0x8113]
[    0.833259] pci 0000:00:1f.2: reg 20 io port: [0x8020-0x803f]
[    0.833267] pci 0000:00:1f.2: reg 24 32bit mmio: [0xdf004000-0xdf0047ff]
[    0.833314] pci 0000:00:1f.2: PME# supported from D3hot
[    0.833319] pci 0000:00:1f.2: PME# disabled
[    0.833360] pci 0000:00:1f.3: reg 10 64bit mmio: [0xdf005000-0xdf0050ff]
[    0.833379] pci 0000:00:1f.3: reg 20 io port: [0x8000-0x801f]
[    0.833468] pci 0000:01:00.0: reg 10 32bit mmio: [0xd2000000-0xd2ffffff]
[    0.833484] pci 0000:01:00.0: reg 14 64bit mmio: [0xc0000000-0xcfffffff]
[    0.833501] pci 0000:01:00.0: reg 1c 64bit mmio: [0xd0000000-0xd1ffffff]
[    0.833510] pci 0000:01:00.0: reg 24 io port: [0x7000-0x707f]
[    0.833520] pci 0000:01:00.0: reg 30 32bit mmio: [0xfffe0000-0xffffffff]
[    0.833639] pci 0000:00:01.0: bridge io port: [0x7000-0x7fff]
[    0.833642] pci 0000:00:01.0: bridge 32bit mmio: [0xd0000000-0xd2ffffff]
[    0.833647] pci 0000:00:01.0: bridge 64bit mmio pref: [0xc0000000-0xcfffffff]
[    0.833847] pci 0000:02:00.0: reg 10 64bit mmio: [0xde000000-0xde003fff]
[    0.834060] pci 0000:02:00.0: supports D1 D2
[    0.834184] pci 0000:00:1c.0: bridge io port: [0x6000-0x6fff]
[    0.834189] pci 0000:00:1c.0: bridge 32bit mmio: [0xde000000-0xdeffffff]
[    0.834197] pci 0000:00:1c.0: bridge 64bit mmio pref: [0xd3000000-0xd3ffffff]
[    0.834260] pci 0000:00:1c.1: bridge io port: [0x5000-0x5fff]
[    0.834265] pci 0000:00:1c.1: bridge 32bit mmio: [0xdd000000-0xddffffff]
[    0.834273] pci 0000:00:1c.1: bridge 64bit mmio pref: [0xd4000000-0xd4ffffff]
[    0.834332] pci 0000:00:1c.2: bridge io port: [0x4000-0x4fff]
[    0.834337] pci 0000:00:1c.2: bridge 32bit mmio: [0xdc000000-0xdcffffff]
[    0.834346] pci 0000:00:1c.2: bridge 64bit mmio pref: [0xd5000000-0xd5ffffff]
[    0.834405] pci 0000:05:00.0: reg 10 io port: [0x3000-0x30ff]
[    0.834431] pci 0000:05:00.0: reg 18 64bit mmio: [0xd6010000-0xd6010fff]
[    0.834450] pci 0000:05:00.0: reg 20 64bit mmio: [0xd6000000-0xd600ffff]
[    0.834461] pci 0000:05:00.0: reg 30 32bit mmio: [0xffff0000-0xffffffff]
[    0.834514] pci 0000:05:00.0: supports D1 D2
[    0.834516] pci 0000:05:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.834522] pci 0000:05:00.0: PME# disabled
[    0.834606] pci 0000:00:1c.3: bridge io port: [0x3000-0x3fff]
[    0.834611] pci 0000:00:1c.3: bridge 32bit mmio: [0xdb000000-0xdbffffff]
[    0.834618] pci 0000:00:1c.3: bridge 64bit mmio pref: [0xd6000000-0xd6ffffff]
[    0.834680] pci 0000:06:00.0: reg 10 32bit mmio: [0xda000000-0xda0007ff]
[    0.834693] pci 0000:06:00.0: reg 14 32bit mmio: [0xda000d00-0xda000d7f]
[    0.834726] pci 0000:06:00.0: reg 20 32bit mmio: [0xda000c80-0xda000cff]
[    0.834738] pci 0000:06:00.0: reg 24 32bit mmio: [0xda000c00-0xda000c7f]
[    0.834865] pci 0000:06:00.1: reg 10 32bit mmio: [0xda000b00-0xda000bff]
[    0.835027] pci 0000:06:00.2: reg 10 32bit mmio: [0xda000a00-0xda000aff]
[    0.835182] pci 0000:06:00.3: reg 10 32bit mmio: [0xda000900-0xda0009ff]
[    0.835339] pci 0000:06:00.4: reg 10 32bit mmio: [0xda000800-0xda0008ff]
[    0.835510] pci 0000:00:1c.4: bridge io port: [0x2000-0x2fff]
[    0.835516] pci 0000:00:1c.4: bridge 32bit mmio: [0xda000000-0xdaffffff]
[    0.835523] pci 0000:00:1c.4: bridge 64bit mmio pref: [0xd7000000-0xd7ffffff]
[    0.835585] pci 0000:00:1c.5: bridge io port: [0x1000-0x1fff]
[    0.835590] pci 0000:00:1c.5: bridge 32bit mmio: [0xd9000000-0xd9ffffff]
[    0.835598] pci 0000:00:1c.5: bridge 64bit mmio pref: [0xd8000000-0xd8ffffff]
[    0.835659] pci 0000:00:1e.0: transparent bridge
[    0.835722] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.836030] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P32_._PRT]
[    0.836184] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.EXP1._PRT]
[    0.836305] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.EXP2._PRT]
[    0.836414] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.EXP3._PRT]
[    0.836523] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.EXP4._PRT]
[    0.836644] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.EXP5._PRT]
[    0.836807] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.EXP6._PRT]
[    0.846931] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 7 9 10 *11 12)
[    0.847081] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 7 9 *10 11 12)
[    0.847230] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 7 9 10 *11 12)
[    0.847378] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 7 9 10 *11 12)
[    0.847524] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 7 9 10 *11 12)
[    0.847671] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 7 9 10 *11 12)
[    0.847818] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 7 9 10 *11 12)
[    0.847969] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 7 9 10 11 12) *0, disabled.
[    0.848175] SCSI subsystem initialized
[    0.848186] libata version 3.00 loaded.
[    0.848186] usbcore: registered new interface driver usbfs
[    0.848186] usbcore: registered new interface driver hub
[    0.848186] usbcore: registered new device driver usb
[    0.848186] ACPI: WMI: Mapper loaded
[    0.848186] PCI: Using ACPI for IRQ routing
[    0.870007] Bluetooth: Core ver 2.15
[    0.870012] NET: Registered protocol family 31
[    0.870013] Bluetooth: HCI device and connection manager initialized
[    0.870017] Bluetooth: HCI socket layer initialized
[    0.870018] NetLabel: Initializing
[    0.870020] NetLabel:  domain hash size = 128
[    0.870022] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.870035] NetLabel:  unlabeled traffic allowed by default
[    0.870088] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0
[    0.870093] hpet0: 4 comparators, 64-bit 14.318180 MHz counter
[    0.890011] Switched to high resolution mode on CPU 0
[    0.891410] Switched to high resolution mode on CPU 1
[    0.911259] pnp: PnP ACPI init
[    0.911272] ACPI: bus type pnp registered
[    1.031160] pnp 00:01: io resource (0x164e-0x164f) overlaps 0000:00:1c.5 BAR 13 (0x1000-0x1fff), disabling
[    1.031932]   alloc irq_desc for 23 on node 0
[    1.031935]   alloc kstat_irqs on node 0
[    1.032421] pnp: PnP ACPI: found 11 devices
[    1.032423] ACPI: ACPI bus type pnp unregistered
[    1.032436] system 00:01: ioport range 0x600-0x60f has been reserved
[    1.032439] system 00:01: ioport range 0x610-0x610 has been reserved
[    1.032442] system 00:01: ioport range 0x800-0x80f has been reserved
[    1.032445] system 00:01: ioport range 0x810-0x817 has been reserved
[    1.032447] system 00:01: ioport range 0x820-0x823 has been reserved
[    1.032450] system 00:01: ioport range 0x400-0x47f has been reserved
[    1.032453] system 00:01: ioport range 0x500-0x53f has been reserved
[    1.032457] system 00:01: iomem range 0xf8000000-0xfbffffff has been reserved
[    1.032460] system 00:01: iomem range 0xfed1c000-0xfed1ffff has been reserved
[    1.032463] system 00:01: iomem range 0xfed10000-0xfed13fff has been reserved
[    1.032466] system 00:01: iomem range 0xfed18000-0xfed18fff has been reserved
[    1.032468] system 00:01: iomem range 0xfed19000-0xfed19fff has been reserved
[    1.032472] system 00:01: iomem range 0xfec00000-0xfec00fff could not be reserved
[    1.032475] system 00:01: iomem range 0xfed20000-0xfed8ffff has been reserved
[    1.032478] system 00:01: iomem range 0xfee00000-0xfee00fff has been reserved
[    1.037168] AppArmor: AppArmor Filesystem Enabled
[    1.037187] pci 0000:01:00.0: BAR 6: no parent found for of device [0xfffe0000-0xffffffff]
[    1.037192] pci 0000:05:00.0: BAR 6: no parent found for of device [0xffff0000-0xffffffff]
[    1.037270] pci 0000:01:00.0: BAR 6: can't allocate mem resource [0xd0000000-0xcfffffff]
[    1.037274] pci 0000:00:01.0: PCI bridge, secondary bus 0000:01
[    1.037277] pci 0000:00:01.0:   IO window: 0x7000-0x7fff
[    1.037281] pci 0000:00:01.0:   MEM window: 0xd0000000-0xd2ffffff
[    1.037285] pci 0000:00:01.0:   PREFETCH window: 0x000000c0000000-0x000000cfffffff
[    1.037290] pci 0000:00:1c.0: PCI bridge, secondary bus 0000:02
[    1.037294] pci 0000:00:1c.0:   IO window: 0x6000-0x6fff
[    1.037301] pci 0000:00:1c.0:   MEM window: 0xde000000-0xdeffffff
[    1.037305] pci 0000:00:1c.0:   PREFETCH window: 0x000000d3000000-0x000000d3ffffff
[    1.037314] pci 0000:00:1c.1: PCI bridge, secondary bus 0000:03
[    1.037317] pci 0000:00:1c.1:   IO window: 0x5000-0x5fff
[    1.037324] pci 0000:00:1c.1:   MEM window: 0xdd000000-0xddffffff
[    1.037329] pci 0000:00:1c.1:   PREFETCH window: 0x000000d4000000-0x000000d4ffffff
[    1.037337] pci 0000:00:1c.2: PCI bridge, secondary bus 0000:04
[    1.037341] pci 0000:00:1c.2:   IO window: 0x4000-0x4fff
[    1.037347] pci 0000:00:1c.2:   MEM window: 0xdc000000-0xdcffffff
[    1.037353] pci 0000:00:1c.2:   PREFETCH window: 0x000000d5000000-0x000000d5ffffff
[    1.037361] pci 0000:00:1c.3: PCI bridge, secondary bus 0000:05
[    1.037364] pci 0000:00:1c.3:   IO window: 0x3000-0x3fff
[    1.037370] pci 0000:00:1c.3:   MEM window: 0xdb000000-0xdbffffff
[    1.037375] pci 0000:00:1c.3:   PREFETCH window: 0x000000d6000000-0x000000d6ffffff
[    1.037384] pci 0000:00:1c.4: PCI bridge, secondary bus 0000:06
[    1.037387] pci 0000:00:1c.4:   IO window: 0x2000-0x2fff
[    1.037393] pci 0000:00:1c.4:   MEM window: 0xda000000-0xdaffffff
[    1.037398] pci 0000:00:1c.4:   PREFETCH window: 0x000000d7000000-0x000000d7ffffff
[    1.037406] pci 0000:00:1c.5: PCI bridge, secondary bus 0000:07
[    1.037409] pci 0000:00:1c.5:   IO window: 0x1000-0x1fff
[    1.037416] pci 0000:00:1c.5:   MEM window: 0xd9000000-0xd9ffffff
[    1.037420] pci 0000:00:1c.5:   PREFETCH window: 0x000000d8000000-0x000000d8ffffff
[    1.037428] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:0a
[    1.037430] pci 0000:00:1e.0:   IO window: disabled
[    1.037436] pci 0000:00:1e.0:   MEM window: disabled
[    1.037441] pci 0000:00:1e.0:   PREFETCH window: disabled
[    1.037450]   alloc irq_desc for 16 on node 0
[    1.037452]   alloc kstat_irqs on node 0
[    1.037456] pci 0000:00:01.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.037461] pci 0000:00:01.0: setting latency timer to 64
[    1.037469] pci 0000:00:1c.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.037474] pci 0000:00:1c.0: setting latency timer to 64
[    1.037482]   alloc irq_desc for 17 on node 0
[    1.037484]   alloc kstat_irqs on node 0
[    1.037487] pci 0000:00:1c.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    1.037492] pci 0000:00:1c.1: setting latency timer to 64
[    1.037500]   alloc irq_desc for 18 on node 0
[    1.037505]   alloc kstat_irqs on node 0
[    1.037508] pci 0000:00:1c.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    1.037513] pci 0000:00:1c.2: setting latency timer to 64
[    1.037521]   alloc irq_desc for 19 on node 0
[    1.037522]   alloc kstat_irqs on node 0
[    1.037526] pci 0000:00:1c.3: PCI INT D -> GSI 19 (level, low) -> IRQ 19
[    1.037531] pci 0000:00:1c.3: setting latency timer to 64
[    1.037540] pci 0000:00:1c.4: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.037544] pci 0000:00:1c.4: setting latency timer to 64
[    1.037552] pci 0000:00:1c.5: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    1.037557] pci 0000:00:1c.5: setting latency timer to 64
[    1.037565] pci 0000:00:1e.0: setting latency timer to 64
[    1.037569] pci_bus 0000:00: resource 0 io:  [0x00-0xffff]
[    1.037572] pci_bus 0000:00: resource 1 mem: [0x000000-0xffffffffffffffff]
[    1.037574] pci_bus 0000:01: resource 0 io:  [0x7000-0x7fff]
[    1.037577] pci_bus 0000:01: resource 1 mem: [0xd0000000-0xd2ffffff]
[    1.037579] pci_bus 0000:01: resource 2 pref mem [0xc0000000-0xcfffffff]
[    1.037581] pci_bus 0000:02: resource 0 io:  [0x6000-0x6fff]
[    1.037584] pci_bus 0000:02: resource 1 mem: [0xde000000-0xdeffffff]
[    1.037586] pci_bus 0000:02: resource 2 pref mem [0xd3000000-0xd3ffffff]
[    1.037589] pci_bus 0000:03: resource 0 io:  [0x5000-0x5fff]
[    1.037591] pci_bus 0000:03: resource 1 mem: [0xdd000000-0xddffffff]
[    1.037593] pci_bus 0000:03: resource 2 pref mem [0xd4000000-0xd4ffffff]
[    1.037596] pci_bus 0000:04: resource 0 io:  [0x4000-0x4fff]
[    1.037598] pci_bus 0000:04: resource 1 mem: [0xdc000000-0xdcffffff]
[    1.037600] pci_bus 0000:04: resource 2 pref mem [0xd5000000-0xd5ffffff]
[    1.037602] pci_bus 0000:05: resource 0 io:  [0x3000-0x3fff]
[    1.037605] pci_bus 0000:05: resource 1 mem: [0xdb000000-0xdbffffff]
[    1.037607] pci_bus 0000:05: resource 2 pref mem [0xd6000000-0xd6ffffff]
[    1.037609] pci_bus 0000:06: resource 0 io:  [0x2000-0x2fff]
[    1.037612] pci_bus 0000:06: resource 1 mem: [0xda000000-0xdaffffff]
[    1.037614] pci_bus 0000:06: resource 2 pref mem [0xd7000000-0xd7ffffff]
[    1.037616] pci_bus 0000:07: resource 0 io:  [0x1000-0x1fff]
[    1.037619] pci_bus 0000:07: resource 1 mem: [0xd9000000-0xd9ffffff]
[    1.037621] pci_bus 0000:07: resource 2 pref mem [0xd8000000-0xd8ffffff]
[    1.037624] pci_bus 0000:0a: resource 3 io:  [0x00-0xffff]
[    1.037626] pci_bus 0000:0a: resource 4 mem: [0x000000-0xffffffffffffffff]
[    1.037663] NET: Registered protocol family 2
[    1.037853] IP route cache hash table entries: 131072 (order: 8, 1048576 bytes)
[    1.039279] TCP established hash table entries: 524288 (order: 11, 8388608 bytes)
[    1.045025] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[    1.045739] TCP: Hash tables configured (established 524288 bind 65536)
[    1.045742] TCP reno registered
[    1.045878] NET: Registered protocol family 1
[    1.045950] Trying to unpack rootfs image as initramfs...
[    1.237363] Freeing initrd memory: 7920k freed
[    1.241397] Simple Boot Flag value 0x5 read from CMOS RAM was invalid
[    1.241400] Simple Boot Flag at 0x44 set to 0x1
[    1.241606] Scanning for low memory corruption every 60 seconds
[    1.241757] audit: initializing netlink socket (disabled)
[    1.241775] type=2000 audit(1271588516.240:1): initialized
[    1.251858] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    1.253304] VFS: Disk quotas dquot_6.5.2
[    1.253360] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    1.253965] fuse init (API version 7.12)
[    1.254046] msgmni has been set to 6032
[    1.254250] alg: No test for stdrng (krng)
[    1.254263] io scheduler noop registered
[    1.254265] io scheduler anticipatory registered
[    1.254268] io scheduler deadline registered
[    1.254310] io scheduler cfq registered (default)
[    3.250007] pci 0000:00:1a.7: EHCI: BIOS handoff failed (BIOS bug?) 01010001
[    5.250006] pci 0000:00:1d.7: EHCI: BIOS handoff failed (BIOS bug?) 01010001
[    5.250150] pci 0000:01:00.0: Boot video device
[    5.250300]   alloc irq_desc for 24 on node 0
[    5.250303]   alloc kstat_irqs on node 0
[    5.250312] pcieport-driver 0000:00:01.0: irq 24 for MSI/MSI-X
[    5.250319] pcieport-driver 0000:00:01.0: setting latency timer to 64
[    5.250478]   alloc irq_desc for 25 on node 0
[    5.250480]   alloc kstat_irqs on node 0
[    5.250489] pcieport-driver 0000:00:1c.0: irq 25 for MSI/MSI-X
[    5.250500] pcieport-driver 0000:00:1c.0: setting latency timer to 64
[    5.250679]   alloc irq_desc for 26 on node 0
[    5.250681]   alloc kstat_irqs on node 0
[    5.250690] pcieport-driver 0000:00:1c.1: irq 26 for MSI/MSI-X
[    5.250701] pcieport-driver 0000:00:1c.1: setting latency timer to 64
[    5.250882]   alloc irq_desc for 27 on node 0
[    5.250884]   alloc kstat_irqs on node 0
[    5.250893] pcieport-driver 0000:00:1c.2: irq 27 for MSI/MSI-X
[    5.250905] pcieport-driver 0000:00:1c.2: setting latency timer to 64
[    5.251080]   alloc irq_desc for 28 on node 0
[    5.251082]   alloc kstat_irqs on node 0
[    5.251091] pcieport-driver 0000:00:1c.3: irq 28 for MSI/MSI-X
[    5.251103] pcieport-driver 0000:00:1c.3: setting latency timer to 64
[    5.251281]   alloc irq_desc for 29 on node 0
[    5.251283]   alloc kstat_irqs on node 0
[    5.251292] pcieport-driver 0000:00:1c.4: irq 29 for MSI/MSI-X
[    5.251303] pcieport-driver 0000:00:1c.4: setting latency timer to 64
[    5.251485]   alloc irq_desc for 30 on node 0
[    5.251487]   alloc kstat_irqs on node 0
[    5.251496] pcieport-driver 0000:00:1c.5: irq 30 for MSI/MSI-X
[    5.251507] pcieport-driver 0000:00:1c.5: setting latency timer to 64
[    5.251619] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    5.251963] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    5.390079] ACPI: AC Adapter [AC] (on-line)
[    5.390158] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input0
[    5.390162] ACPI: Power Button [PWRF]
[    5.390213] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1
[    5.390216] ACPI: Power Button [PWRB]
[    5.390257] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input2
[    5.390328] ACPI: Lid Switch [LID0]
[    5.390379] input: Sleep Button as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input3
[    5.390386] ACPI: Sleep Button [SLPB]
[    5.429499] fan PNP0C0B:00: registered as cooling_device0
[    5.429505] ACPI: Fan [FAN] (on)
[    5.430586] ACPI: SSDT 00000000bfc6ec18 00265 (v01  PmRef  Cpu0Ist 00003000 INTL 20051117)
[    5.431210] ACPI: SSDT 00000000bfc6c618 005B3 (v01  PmRef  Cpu0Cst 00003001 INTL 20051117)
[    5.431750] Monitor-Mwait will be used to enter C-1 state
[    5.431771] Monitor-Mwait will be used to enter C-2 state
[    5.431790] Monitor-Mwait will be used to enter C-3 state
[    5.431797] Marking TSC unstable due to TSC halts in idle
[    5.431816] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[    5.431836] processor LNXCPU:00: registered as cooling_device1
[    5.431840] ACPI: Processor [CPU0] (supports 8 throttling states)
[    5.432378] ACPI: SSDT 00000000bfc6de18 001CF (v01  PmRef    ApIst 00003000 INTL 20051117)
[    5.432894] ACPI: SSDT 00000000bfc6ef18 0008D (v01  PmRef    ApCst 00003000 INTL 20051117)
[    5.433560] ACPI: CPU1 (power states: C1[C1] C2[C2] C3[C3])
[    5.433579] processor LNXCPU:01: registered as cooling_device2
[    5.433583] ACPI: Processor [CPU1] (supports 8 throttling states)
[    5.586017] thermal LNXTHERM:01: registered as thermal_zone0
[    5.586028] ACPI: Thermal Zone [THRM] (29 C)
[    5.587230] Linux agpgart interface v0.103
[    5.587238] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    5.588452] brd: module loaded
[    5.588898] loop: module loaded
[    5.588967] input: Macintosh mouse button emulation as /devices/virtual/input/input4
[    5.589082] ahci 0000:00:1f.2: version 3.0
[    5.589095]   alloc irq_desc for 21 on node 0
[    5.589098]   alloc kstat_irqs on node 0
[    5.589104] ahci 0000:00:1f.2: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[    5.589137]   alloc irq_desc for 31 on node 0
[    5.589138]   alloc kstat_irqs on node 0
[    5.589148] ahci 0000:00:1f.2: irq 31 for MSI/MSI-X
[    5.589196] ahci: SSS flag set, parallel bus scan disabled
[    5.589234] ahci 0000:00:1f.2: AHCI 0001.0200 32 slots 4 ports 3 Gbps 0x33 impl SATA mode
[    5.589238] ahci 0000:00:1f.2: flags: 64bit ncq sntf stag pm led clo pmp pio slum part ems 
[    5.589244] ahci 0000:00:1f.2: setting latency timer to 64
[    5.640066] scsi0 : ahci
[    5.640166] scsi1 : ahci
[    5.640224] scsi2 : ahci
[    5.640283] scsi3 : ahci
[    5.640341] scsi4 : ahci
[    5.640405] scsi5 : ahci
[    5.640659] ata1: SATA max UDMA/133 abar m2048@0xdf004000 port 0xdf004100 irq 31
[    5.640663] ata2: SATA max UDMA/133 abar m2048@0xdf004000 port 0xdf004180 irq 31
[    5.640665] ata3: DUMMY
[    5.640667] ata4: DUMMY
[    5.640670] ata5: SATA max UDMA/133 abar m2048@0xdf004000 port 0xdf004300 irq 31
[    5.640673] ata6: SATA max UDMA/133 abar m2048@0xdf004000 port 0xdf004380 irq 31
[    5.641582] Fixed MDIO Bus: probed
[    5.641616] PPP generic driver version 2.4.2
[    5.641706] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    5.641763] ehci_hcd 0000:00:1a.7: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    5.641776] ehci_hcd 0000:00:1a.7: setting latency timer to 64
[    5.641780] ehci_hcd 0000:00:1a.7: EHCI Host Controller
[    5.641832] ehci_hcd 0000:00:1a.7: new USB bus registered, assigned bus number 1
[    5.645754] ehci_hcd 0000:00:1a.7: debug port 1
[    5.645761] ehci_hcd 0000:00:1a.7: cache line size of 32 is not supported
[    5.645774] ehci_hcd 0000:00:1a.7: irq 18, io mem 0xdf004c00
[    5.660015] ehci_hcd 0000:00:1a.7: USB 2.0 started, EHCI 1.00
[    5.660083] usb usb1: configuration #1 chosen from 1 choice
[    5.660111] hub 1-0:1.0: USB hub found
[    5.660119] hub 1-0:1.0: 4 ports detected
[    5.660211]   alloc irq_desc for 20 on node 0
[    5.660213]   alloc kstat_irqs on node 0
[    5.660218] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    5.660228] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    5.660231] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    5.660261] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 2
[    5.664154] ehci_hcd 0000:00:1d.7: debug port 1
[    5.664161] ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported
[    5.664173] ehci_hcd 0000:00:1d.7: irq 20, io mem 0xdf004800
[    5.680013] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    5.680069] usb usb2: configuration #1 chosen from 1 choice
[    5.680095] hub 2-0:1.0: USB hub found
[    5.680101] hub 2-0:1.0: 8 ports detected
[    5.680172] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    5.680189] uhci_hcd: USB Universal Host Controller Interface driver
[    5.680265] uhci_hcd 0000:00:1a.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    5.680273] uhci_hcd 0000:00:1a.0: setting latency timer to 64
[    5.680276] uhci_hcd 0000:00:1a.0: UHCI Host Controller
[    5.680309] uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 3
[    5.680345] uhci_hcd 0000:00:1a.0: irq 16, io base 0x000080e0
[    5.680421] usb usb3: configuration #1 chosen from 1 choice
[    5.680449] hub 3-0:1.0: USB hub found
[    5.680456] hub 3-0:1.0: 2 ports detected
[    5.680536] uhci_hcd 0000:00:1a.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    5.680544] uhci_hcd 0000:00:1a.1: setting latency timer to 64
[    5.680547] uhci_hcd 0000:00:1a.1: UHCI Host Controller
[    5.680586] uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus number 4
[    5.680622] uhci_hcd 0000:00:1a.1: irq 17, io base 0x000080c0
[    5.680701] usb usb4: configuration #1 chosen from 1 choice
[    5.680726] hub 4-0:1.0: USB hub found
[    5.680732] hub 4-0:1.0: 2 ports detected
[    5.680816] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    5.680823] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    5.680826] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    5.680855] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 5
[    5.680884] uhci_hcd 0000:00:1d.0: irq 20, io base 0x000080a0
[    5.680968] usb usb5: configuration #1 chosen from 1 choice
[    5.680993] hub 5-0:1.0: USB hub found
[    5.680999] hub 5-0:1.0: 2 ports detected
[    5.681076]   alloc irq_desc for 22 on node 0
[    5.681078]   alloc kstat_irqs on node 0
[    5.681082] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 22 (level, low) -> IRQ 22
[    5.681088] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    5.681092] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    5.681121] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 6
[    5.681156] uhci_hcd 0000:00:1d.1: irq 22, io base 0x00008080
[    5.681235] usb usb6: configuration #1 chosen from 1 choice
[    5.681260] hub 6-0:1.0: USB hub found
[    5.681266] hub 6-0:1.0: 2 ports detected
[    5.681342] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    5.681349] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    5.681353] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    5.681386] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 7
[    5.681416] uhci_hcd 0000:00:1d.2: irq 18, io base 0x00008060
[    5.681491] usb usb7: configuration #1 chosen from 1 choice
[    5.681518] hub 7-0:1.0: USB hub found
[    5.681525] hub 7-0:1.0: 2 ports detected
[    5.681598] uhci_hcd 0000:00:1d.3: PCI INT D -> GSI 19 (level, low) -> IRQ 19
[    5.681605] uhci_hcd 0000:00:1d.3: setting latency timer to 64
[    5.681608] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[    5.681639] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 8
[    5.681676] uhci_hcd 0000:00:1d.3: irq 19, io base 0x00008040
[    5.681755] usb usb8: configuration #1 chosen from 1 choice
[    5.681782] hub 8-0:1.0: USB hub found
[    5.681788] hub 8-0:1.0: 2 ports detected
[    5.681887] PNP: PS/2 Controller [PNP0303:KBC,PNP0f13:MOUE] at 0x60,0x64 irq 1,12
[    5.733372] serio: i8042 KBD port at 0x60,0x64 irq 1
[    5.733377] serio: i8042 AUX port at 0x60,0x64 irq 12
[    5.733440] mice: PS/2 mouse device common for all mice
[    5.733559] rtc_cmos 00:03: RTC can wake from S4
[    5.733594] rtc_cmos 00:03: rtc core: registered rtc_cmos as rtc0
[    5.733626] rtc0: alarms up to one month, 242 bytes nvram, hpet irqs
[    5.733721] device-mapper: uevent: version 1.0.3
[    5.736236] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: dm-devel@redhat.com
[    5.736310] device-mapper: multipath: version 1.1.0 loaded
[    5.736314] device-mapper: multipath round-robin: version 1.0.0 loaded
[    5.736554] cpuidle: using governor ladder
[    5.736666] cpuidle: using governor menu
[    5.737065] TCP cubic registered
[    5.737188] NET: Registered protocol family 10
[    5.737631] lo: Disabled Privacy Extensions
[    5.737912] NET: Registered protocol family 17
[    5.737930] Bluetooth: L2CAP ver 2.13
[    5.737932] Bluetooth: L2CAP socket layer initialized
[    5.737936] Bluetooth: SCO (Voice Link) ver 0.6
[    5.737938] Bluetooth: SCO socket layer initialized
[    5.737974] Bluetooth: RFCOMM TTY layer initialized
[    5.737977] Bluetooth: RFCOMM socket layer initialized
[    5.737979] Bluetooth: RFCOMM ver 1.11
[    5.738546] PM: Resume from disk failed.
[    5.738558] registered taskstats version 1
[    5.738707]   Magic number: 6:466:24
[    5.738711] misc cpu_dma_latency: hash matches
[    5.738819] rtc_cmos 00:03: setting system clock to 2010-04-18 11:02:01 UTC (1271588521)
[    5.738823] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    5.738824] EDD information not available.
[    5.771268] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input5
[    6.000132] Clocksource tsc unstable (delta = -219955228 ns)
[    6.060104] usb 2-5: new high speed USB device using ehci_hcd and address 3
[    6.078335] ACPI: Battery Slot [BAT0] (battery present)
[    6.170135] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    6.171603] ata1.00: ACPI cmd 00/00:00:00:00:00:a0 rejected by device (Stat=0x51 Err=0x04)
[    6.171822] ata1.00: ACPI cmd ef/10:01:00:00:00:a0 rejected by device (Stat=0x51 Err=0x04)
[    6.172095] ata1.00: ACPI cmd ef/10:02:00:00:00:a0 succeeded
[    6.172101] ata1.00: ACPI cmd ef/10:03:00:00:00:a0 filtered out
[    6.172365] ata1.00: ACPI cmd ef/10:04:00:00:00:a0 rejected by device (Stat=0x51 Err=0x04)
[    6.172608] ata1.00: ACPI cmd ef/10:05:00:00:00:a0 rejected by device (Stat=0x51 Err=0x04)
[    6.173293] ata1.00: ATA-8: Hitachi HTS543225L9A300, FBEOC44C, max UDMA/100
[    6.173298] ata1.00: 488397168 sectors, multi 0: LBA48 NCQ (depth 31/32)
[    6.174906] ata1.00: ACPI cmd 00/00:00:00:00:00:a0 rejected by device (Stat=0x51 Err=0x04)
[    6.175126] ata1.00: ACPI cmd ef/10:01:00:00:00:a0 rejected by device (Stat=0x51 Err=0x04)
[    6.175130] ata1.00: ACPI cmd ef/10:03:00:00:00:a0 filtered out
[    6.175367] ata1.00: ACPI cmd ef/10:04:00:00:00:a0 rejected by device (Stat=0x51 Err=0x04)
[    6.175645] ata1.00: ACPI cmd ef/10:05:00:00:00:a0 rejected by device (Stat=0x51 Err=0x04)
[    6.175675] ata1.00: configured for UDMA/100
[    6.190209] scsi 0:0:0:0: Direct-Access     ATA      Hitachi HTS54322 FBEO PQ: 0 ANSI: 5
[    6.190328] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    6.190369] sd 0:0:0:0: [sda] 488397168 512-byte logical blocks: (250 GB/232 GiB)
[    6.190412] sd 0:0:0:0: [sda] Write Protect is off
[    6.190415] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    6.190437] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    6.190554]  sda: sda1 sda2 <
[    6.217697] usb 2-5: configuration #1 chosen from 1 choice
[    6.232555]  sda5 > sda3
[    6.232882] sd 0:0:0:0: [sda] Attached SCSI disk
[    6.490101] usb 6-1: new low speed USB device using uhci_hcd and address 2
[    6.670291] usb 6-1: configuration #1 chosen from 1 choice
[    7.120111] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    7.121162] ata2.00: ACPI cmd 00/00:00:00:00:00:b0 rejected by device (Stat=0x51 Err=0x04)
[    7.121351] ata2.00: ACPI cmd ef/10:01:00:00:00:b0 rejected by device (Stat=0x51 Err=0x04)
[    7.121440] ata2.00: ACPI cmd ef/10:02:00:00:00:b0 succeeded
[    7.121446] ata2.00: ACPI cmd ef/10:03:00:00:00:b0 filtered out
[    7.121592] ata2.00: ACPI cmd ef/10:04:00:00:00:b0 rejected by device (Stat=0x51 Err=0x04)
[    7.121721] ata2.00: ACPI cmd ef/10:05:00:00:00:b0 rejected by device (Stat=0x51 Err=0x04)
[    7.410179] ata2.00: ATA-8: WDC WD2500BEVS-00UST0, 01.01A01, max UDMA/133
[    7.410184] ata2.00: 488397168 sectors, multi 0: LBA48 NCQ (depth 31/32)
[    7.411597] ata2.00: ACPI cmd 00/00:00:00:00:00:b0 rejected by device (Stat=0x51 Err=0x04)
[    7.411862] ata2.00: ACPI cmd ef/10:01:00:00:00:b0 rejected by device (Stat=0x51 Err=0x04)
[    7.411868] ata2.00: ACPI cmd ef/10:03:00:00:00:b0 filtered out
[    7.412067] ata2.00: ACPI cmd ef/10:04:00:00:00:b0 rejected by device (Stat=0x51 Err=0x04)
[    7.412250] ata2.00: ACPI cmd ef/10:05:00:00:00:b0 rejected by device (Stat=0x51 Err=0x04)
[    7.412409] ata2.00: configured for UDMA/133
[    7.430208] scsi 1:0:0:0: Direct-Access     ATA      WDC WD2500BEVS-0 01.0 PQ: 0 ANSI: 5
[    7.430334] sd 1:0:0:0: Attached scsi generic sg1 type 0
[    7.430366] sd 1:0:0:0: [sdb] 488397168 512-byte logical blocks: (250 GB/232 GiB)
[    7.430408] sd 1:0:0:0: [sdb] Write Protect is off
[    7.430410] sd 1:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[    7.430433] sd 1:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    7.430540]  sdb: sdb1
[    7.443178] sd 1:0:0:0: [sdb] Attached SCSI disk
[    8.360134] ata5: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    8.365051] ata5.00: ACPI cmd 00/00:00:00:00:00:a0 rejected by device (Stat=0x51 Err=0x04)
[    8.365571] ata5.00: ACPI cmd ef/10:01:00:00:00:a0 rejected by device (Stat=0x51 Err=0x04)
[    8.366035] ata5.00: ACPI cmd ef/10:02:00:00:00:a0 rejected by device (Stat=0x51 Err=0x04)
[    8.366041] ata5.00: ACPI cmd ef/10:03:00:00:00:a0 filtered out
[    8.366550] ata5.00: ACPI cmd ef/10:04:00:00:00:a0 rejected by device (Stat=0x51 Err=0x04)
[    8.367016] ata5.00: ACPI cmd ef/10:05:00:00:00:a0 rejected by device (Stat=0x51 Err=0x04)
[    8.367022] ata5.00: ATAPI: HL-DT-ST DVDRAM GSA-T50L, SC04, max UDMA/100
[    8.372655] ata5.00: ACPI cmd 00/00:00:00:00:00:a0 rejected by device (Stat=0x51 Err=0x04)
[    8.373126] ata5.00: ACPI cmd ef/10:01:00:00:00:a0 rejected by device (Stat=0x51 Err=0x04)
[    8.373652] ata5.00: ACPI cmd ef/10:02:00:00:00:a0 rejected by device (Stat=0x51 Err=0x04)
[    8.373657] ata5.00: ACPI cmd ef/10:03:00:00:00:a0 filtered out
[    8.374118] ata5.00: ACPI cmd ef/10:04:00:00:00:a0 rejected by device (Stat=0x51 Err=0x04)
[    8.374645] ata5.00: ACPI cmd ef/10:05:00:00:00:a0 rejected by device (Stat=0x51 Err=0x04)
[    8.374673] ata5.00: configured for UDMA/100
[    8.503295] scsi 4:0:0:0: CD-ROM            HL-DT-ST DVDRAM GSA-T50L  SC04 PQ: 0 ANSI: 5
[    8.837260] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[    8.837265] Uniform CD-ROM driver Revision: 3.20
[    8.837387] sr 4:0:0:0: Attached scsi CD-ROM sr0
[    8.837446] sr 4:0:0:0: Attached scsi generic sg2 type 5
[    9.180110] ata6: SATA link down (SStatus 0 SControl 300)
[    9.200188] Freeing unused kernel memory: 660k freed
[    9.200420] Write protecting the kernel read-only data: 7584k
[    9.301883] [Firmware Bug]: ACPI: ACPI brightness control misses _BQC function
[    9.314645] acpi device:09: registered as cooling_device3
[    9.314865] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:07/device:08/input/input6
[    9.314903] ACPI: Video Device [EVGA] (multi-head: yes  rom: no  post: no)
[    9.531875] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    9.531902] r8169 0000:05:00.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    9.531959] r8169 0000:05:00.0: setting latency timer to 64
[    9.532021]   alloc irq_desc for 32 on node 0
[    9.532023]   alloc kstat_irqs on node 0
[    9.532041] r8169 0000:05:00.0: irq 32 for MSI/MSI-X
[    9.532632] eth0: RTL8168c/8111c at 0xffffc90000678000, 00:1e:ec:ea:e7:1c, XID 3c2000c0 IRQ 32
[    9.572432] ohci1394 0000:06:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    9.572443] ohci1394 0000:06:00.0: setting latency timer to 64
[    9.578180] usbcore: registered new interface driver hiddev
[    9.591608] input: Logitech USB-PS/2 Optical Mouse as /devices/pci0000:00/0000:00:1d.1/usb6/6-1/6-1:1.0/input/input7
[    9.591690] generic-usb 0003:046D:C00E.0001: input,hidraw0: USB HID v1.10 Mouse [Logitech USB-PS/2 Optical Mouse] on usb-0000:00:1d.1-1/input0
[    9.591709] usbcore: registered new interface driver usbhid
[    9.591712] usbhid: v2.6:USB HID core driver
[    9.631166] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[16]  MMIO=[da000000-da0007ff]  Max Packet=[2048]  IR/IT contexts=[4/4]
[   10.951392] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[8a3f0200962e41d9]
[   11.122291] xor: automatically using best checksumming function: generic_sse
[   11.170008]    generic_sse:  7313.200 MB/sec
[   11.170011] xor: using function: generic_sse (7313.200 MB/sec)
[   11.172129] device-mapper: dm-raid45: initialized v0.2594b
[   11.477007] PM: Starting manual resume from disk
[   11.477012] PM: Resume from partition 8:5
[   11.477013] PM: Checking hibernation image.
[   11.477218] PM: Resume from disk failed.
[   11.495627] EXT4-fs (sda3): barriers enabled
[   11.514650] kjournald2 starting: pid 459, dev sda3:8, commit interval 5 seconds
[   11.514683] EXT4-fs (sda3): delayed allocation enabled
[   11.514690] EXT4-fs: file extents enabled
[   11.514816] EXT4-fs: mballoc enabled
[   11.514830] EXT4-fs (sda3): mounted filesystem with ordered data mode
[   12.270493] type=1505 audit(1271588528.031:2): operation="profile_load" pid=482 name=/usr/share/gdm/guest-session/Xsession
[   12.272888] type=1505 audit(1271588528.031:3): operation="profile_load" pid=483 name=/sbin/dhclient3
[   12.273650] type=1505 audit(1271588528.031:4): operation="profile_load" pid=483 name=/usr/lib/NetworkManager/nm-dhcp-client.action
[   12.274043] type=1505 audit(1271588528.031:5): operation="profile_load" pid=483 name=/usr/lib/connman/scripts/dhclient-script
[   12.332806] type=1505 audit(1271588528.091:6): operation="profile_load" pid=484 name=/usr/bin/evince
[   12.344497] type=1505 audit(1271588528.101:7): operation="profile_load" pid=484 name=/usr/bin/evince-previewer
[   12.351573] type=1505 audit(1271588528.111:8): operation="profile_load" pid=484 name=/usr/bin/evince-thumbnailer
[   12.372426] type=1505 audit(1271588528.131:9): operation="profile_load" pid=486 name=/usr/lib/cups/backend/cups-pdf
[   12.373271] type=1505 audit(1271588528.131:10): operation="profile_load" pid=486 name=/usr/sbin/cupsd
[   12.375981] type=1505 audit(1271588528.131:11): operation="profile_load" pid=487 name=/usr/sbin/tcpdump
[   47.264025] Adding 9759416k swap on /dev/sda5.  Priority:-1 extents:1 across:9759416k 
[   47.582726] udev: starting version 147
[   47.856853] lirc_dev: IR Remote Control driver registered, major 61 
[   47.886292] lis3lv02d: hardware type DV7 found.
[   47.887033] lis3lv02d: 1-byte sensor found
[   47.896392] input: ST LIS3LV02DL Accelerometer as /devices/platform/lis3lv02d/input/input8
[   47.896533] Registered led device: hp::hddprotect
[   47.896560] lis3lv02d driver loaded.
[   47.901902] sdhci: Secure Digital Host Controller Interface driver
[   47.901905] sdhci: Copyright(c) Pierre Ossman
[   47.944773] Disabling lock debugging due to kernel taint
[   47.948733] ndiswrapper version 1.55 loaded (smp=yes, preempt=no)
[   47.954430] sdhci-pci 0000:06:00.1: SDHCI controller found [197b:2382] (rev 0)
[   47.954456] sdhci-pci 0000:06:00.1: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   47.954516] sdhci-pci 0000:06:00.1: setting latency timer to 64
[   47.954567] Registered led device: mmc0::
[   47.954605] mmc0: SDHCI controller on PCI [0000:06:00.1] using DMA
[   47.954664] sdhci-pci 0000:06:00.2: SDHCI controller found [197b:2381] (rev 0)
[   47.954683] sdhci-pci 0000:06:00.2: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   47.954695] sdhci-pci 0000:06:00.2: Refusing to bind to secondary interface.
[   47.954702] sdhci-pci 0000:06:00.2: PCI INT A disabled
[   47.965634] lp: driver loaded but no devices found
[   48.003849] lirc_dev: lirc_register_driver: sample_rate: 0
[   48.003960] enecir: KB3926C detected, driver support is not complete!
[   48.003962] enecir: chip is 0x3926 - 0x00, 0xc0
[   48.003971] enecir: hardware features:
[   48.003973] enecir: learning and tx off, gpio40_learn off, fan_in off
[   48.003975] enecir: driver has been succesfully loaded
[   48.252505] EXT4-fs (sda3): internal journal on sda3:8
[   48.266826] usbcore: registered new interface driver ndiswrapper
[   48.298464] mmc0: new SD card at address 0002
[   50.068070] jmb38x_ms 0000:06:00.3: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   50.068079] jmb38x_ms 0000:06:00.3: setting latency timer to 64
[   50.076426] mmcblk0: mmc0:0002 00000 974 MiB 
[   50.076474]  mmcblk0: p1
[   50.301165] nvidia 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   50.301181] nvidia 0000:01:00.0: setting latency timer to 64
[   50.301341] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  185.18.36  Fri Aug 14 17:35:21 PDT 2009
[   50.364325] Linux video capture interface: v2.00
[   50.397599] ip_tables: (C) 2000-2006 Netfilter Core Team
[   50.475157] uvcvideo: Found UVC 1.00 device HP Webcam (090c:c371)
[   50.476350] input: HP Webcam as /devices/pci0000:00/0000:00:1d.7/usb2/2-5/2-5:1.0/input/input9
[   50.476402] usbcore: registered new interface driver uvcvideo
[   50.476405] USB Video Class driver (v0.1.0)
[   50.951755] HDA Intel 0000:00:1b.0: power state changed by ACPI to D0
[   50.951768] HDA Intel 0000:00:1b.0: PCI INT B -> GSI 22 (level, low) -> IRQ 22
[   50.951824]   alloc irq_desc for 33 on node 0
[   50.951826]   alloc kstat_irqs on node 0
[   50.951839] HDA Intel 0000:00:1b.0: irq 33 for MSI/MSI-X
[   50.951876] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   51.174152] input: HDA Digital PCBeep as /devices/pci0000:00/0000:00:1b.0/input/input10
[   51.281621] input: HDA Intel Mic at Ext Front Jack as /devices/pci0000:00/0000:00:1b.0/sound/card0/input11
[   51.281700] input: HDA Intel HP Out at Ext Front Jack as /devices/pci0000:00/0000:00:1b.0/sound/card0/input12
[   51.419969] Synaptics Touchpad, model: 1, fw: 7.2, id: 0x1a0b1, caps: 0xd04751/0xa00000
[   51.548493] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input13
[   52.589511] r8169: eth0: link up
[   52.589528] r8169: eth0: link up
[   53.909195] usplash:411 freeing invalid memtype ffffffffd1000000-ffffffffd1e00000
[   59.145289] CPU0 attaching NULL sched-domain.
[   59.145296] CPU1 attaching NULL sched-domain.
[   59.181366] CPU0 attaching sched-domain:
[   59.181371]  domain 0: span 0-1 level MC
[   59.181374]   groups: 0 1
[   59.181380] CPU1 attaching sched-domain:
[   59.181382]  domain 0: span 0-1 level MC
[   59.181384]   groups: 1 0
[   63.110036] eth0: no IPv6 routers present

```

---

### Post by Bob Bertrands on 2010-04-11
bump

---

### Post by Bob Bertrands on 2010-04-18
Still same situation

---

### Post by dcstar on 2010-04-18
You need to look at the syslog file and see when the networking started and when the other init scripts were run.

If some things were attempted to be started before networking was up then you can have big problems.

You have not said if you are running Desktop or Server.

---

### Post by Bob Bertrands on 2010-04-18
First of all, thanks for the response !!

Currently running Desktop edition.

Found the syslog file:

```
Apr 18 11:07:54 ben-laptop rsyslogd: [origin software="rsyslogd" swVersion="4.2.0" x-pid="881" x-info="http://www.rsyslog.com"] rsyslogd was HUPed, type 'lightweight'.
Apr 18 11:07:54 ben-laptop rsyslogd: [origin software="rsyslogd" swVersion="4.2.0" x-pid="881" x-info="http://www.rsyslog.com"] rsyslogd was HUPed, type 'lightweight'.
Apr 18 11:08:14 ben-laptop anacron[1303]: Job `cron.daily' terminated
Apr 18 11:08:14 ben-laptop anacron[1303]: Normal exit (1 job run)
Apr 18 11:21:00 ben-laptop dbus-daemon: Reloaded configuration
Apr 18 11:21:01 ben-laptop dbus-daemon: Reloaded configuration
Apr 18 11:23:09 ben-laptop dbus-daemon: Reloaded configuration
Apr 18 11:23:15 ben-laptop dbus-daemon: Reloaded configuration
Apr 18 11:23:58 ben-laptop kernel: [ 1323.933775] SGI XFS with ACLs, security attributes, realtime, large block/inode numbers, no debug enabled
Apr 18 11:23:58 ben-laptop kernel: [ 1323.937538] SGI XFS Quota Management subsystem
Apr 18 11:23:58 ben-laptop kernel: [ 1323.975623] JFS: nTxBlock = 8192, nTxLock = 65536
Apr 18 11:23:58 ben-laptop kernel: [ 1324.011356] NTFS driver 2.1.29 [Flags: R/O MODULE].
Apr 18 11:23:58 ben-laptop kernel: [ 1324.075375] QNX4 filesystem 0.2.3 registered.
Apr 18 11:23:59 ben-laptop os-prober: debug: running /usr/lib/os-probes/mounted/10freedos on mounted /dev/mmcblk0p1
Apr 18 11:23:59 ben-laptop 10freedos: debug: /dev/mmcblk0p1 is a FAT32 partition
Apr 18 11:23:59 ben-laptop os-prober: debug: running /usr/lib/os-probes/mounted/10qnx on mounted /dev/mmcblk0p1
Apr 18 11:23:59 ben-laptop 10qnx: debug: /dev/mmcblk0p1 is not a QNX4 partition: exiting
Apr 18 11:23:59 ben-laptop os-prober: debug: running /usr/lib/os-probes/mounted/20macosx on mounted /dev/mmcblk0p1
Apr 18 11:23:59 ben-laptop macosx-prober: debug: /dev/mmcblk0p1 is not an HFS+ partition: exiting
Apr 18 11:23:59 ben-laptop os-prober: debug: running /usr/lib/os-probes/mounted/20microsoft on mounted /dev/mmcblk0p1
Apr 18 11:23:59 ben-laptop 20microsoft: debug: /dev/mmcblk0p1 is a FAT32 partition
Apr 18 11:23:59 ben-laptop os-prober: debug: running /usr/lib/os-probes/mounted/30utility on mounted /dev/mmcblk0p1
Apr 18 11:23:59 ben-laptop 30utility: debug: /dev/mmcblk0p1 is a FAT32 partition
Apr 18 11:23:59 ben-laptop os-prober: debug: running /usr/lib/os-probes/mounted/40lsb on mounted /dev/mmcblk0p1
Apr 18 11:23:59 ben-laptop os-prober: debug: running /usr/lib/os-probes/mounted/70hurd on mounted /dev/mmcblk0p1
Apr 18 11:23:59 ben-laptop os-prober: debug: running /usr/lib/os-probes/mounted/80minix on mounted /dev/mmcblk0p1
Apr 18 11:23:59 ben-laptop os-prober: debug: running /usr/lib/os-probes/mounted/90linux-distro on mounted /dev/mmcblk0p1
Apr 18 11:23:59 ben-laptop os-prober: debug: running /usr/lib/os-probes/mounted/90solaris on mounted /dev/mmcblk0p1
Apr 18 11:23:59 ben-laptop os-prober: debug: running /usr/lib/os-probes/mounted/10freedos on mounted /dev/sda1
Apr 18 11:23:59 ben-laptop 10freedos: debug: /dev/sda1 is not a FAT partition: exiting
Apr 18 11:23:59 ben-laptop os-prober: debug: running /usr/lib/os-probes/mounted/10qnx on mounted /dev/sda1
Apr 18 11:23:59 ben-laptop 10qnx: debug: /dev/sda1 is not a QNX4 partition: exiting
Apr 18 11:23:59 ben-laptop os-prober: debug: running /usr/lib/os-probes/mounted/20macosx on mounted /dev/sda1
Apr 18 11:23:59 ben-laptop macosx-prober: debug: /dev/sda1 is not an HFS+ partition: exiting
Apr 18 11:23:59 ben-laptop os-prober: debug: running /usr/lib/os-probes/mounted/20microsoft on mounted /dev/sda1
Apr 18 11:23:59 ben-laptop 20microsoft: debug: /dev/sda1 is a FUSE partition
Apr 18 11:23:59 ben-laptop 20microsoft: result: /dev/sda1:Windows 7 (loader):Windows:chain
Apr 18 11:23:59 ben-laptop os-prober: debug: os detected by /usr/lib/os-probes/mounted/20microsoft
Apr 18 11:23:59 ben-laptop os-prober: debug: running /usr/lib/os-probes/50mounted-tests on /dev/sda2
Apr 18 11:23:59 ben-laptop 50mounted-tests: debug: /dev/sda2 type not recognised; skipping
Apr 18 11:23:59 ben-laptop os-prober: debug: os detected by /usr/lib/os-probes/50mounted-tests
Apr 18 11:23:59 ben-laptop os-prober: debug: running /usr/lib/os-probes/50mounted-tests on /dev/sda5
Apr 18 11:23:59 ben-laptop 50mounted-tests: debug: /dev/sda5 is a swap partition; skipping
Apr 18 11:23:59 ben-laptop os-prober: debug: os detected by /usr/lib/os-probes/50mounted-tests
Apr 18 11:23:59 ben-laptop os-prober: debug: running /usr/lib/os-probes/mounted/10freedos on mounted /dev/sdb1
Apr 18 11:23:59 ben-laptop 10freedos: debug: /dev/sdb1 is not a FAT partition: exiting
Apr 18 11:23:59 ben-laptop os-prober: debug: running /usr/lib/os-probes/mounted/10qnx on mounted /dev/sdb1
Apr 18 11:23:59 ben-laptop 10qnx: debug: /dev/sdb1 is not a QNX4 partition: exiting
Apr 18 11:23:59 ben-laptop os-prober: debug: running /usr/lib/os-probes/mounted/20macosx on mounted /dev/sdb1
Apr 18 11:23:59 ben-laptop macosx-prober: debug: /dev/sdb1 is not an HFS+ partition: exiting
Apr 18 11:23:59 ben-laptop os-prober: debug: running /usr/lib/os-probes/mounted/20microsoft on mounted /dev/sdb1
Apr 18 11:23:59 ben-laptop 20microsoft: debug: /dev/sdb1 is a FUSE partition
Apr 18 11:23:59 ben-laptop os-prober: debug: running /usr/lib/os-probes/mounted/30utility on mounted /dev/sdb1
Apr 18 11:23:59 ben-laptop 30utility: debug: /dev/sdb1 is not a FAT partition: exiting
Apr 18 11:23:59 ben-laptop os-prober: debug: running /usr/lib/os-probes/mounted/40lsb on mounted /dev/sdb1
Apr 18 11:23:59 ben-laptop os-prober: debug: running /usr/lib/os-probes/mounted/70hurd on mounted /dev/sdb1
Apr 18 11:23:59 ben-laptop os-prober: debug: running /usr/lib/os-probes/mounted/80minix on mounted /dev/sdb1
Apr 18 11:23:59 ben-laptop os-prober: debug: running /usr/lib/os-probes/mounted/90linux-distro on mounted /dev/sdb1
Apr 18 11:23:59 ben-laptop os-prober: debug: running /usr/lib/os-probes/mounted/90solaris on mounted /dev/sdb1
Apr 18 11:24:04 ben-laptop console-kit-daemon[967]: WARNING: Couldn't read /proc/966/environ: Failed to open file '/proc/966/environ': No such file or directory
Apr 18 11:24:52 ben-laptop kernel: [ 1377.468099] type=1505 audit(1271582692.186:12): operation="profile_replace" pid=14794 name=/sbin/dhclient3
Apr 18 11:24:52 ben-laptop kernel: [ 1377.468834] type=1505 audit(1271582692.186:13): operation="profile_replace" pid=14794 name=/usr/lib/NetworkManager/nm-dhcp-client.action
Apr 18 11:24:52 ben-laptop kernel: [ 1377.469230] type=1505 audit(1271582692.186:14): operation="profile_replace" pid=14794 name=/usr/lib/connman/scripts/dhclient-script
Apr 18 11:24:59 ben-laptop dbus-daemon: Reloaded configuration
Apr 18 11:26:04 ben-laptop dbus-daemon: last message repeated 3 times
Apr 18 11:30:48 ben-laptop pulseaudio[1417]: alsa-sink.c: ALSA woke us up to write new data to the device, but there was actually nothing to write!
Apr 18 11:30:48 ben-laptop pulseaudio[1417]: alsa-sink.c: Most likely this is a bug in the ALSA driver 'snd_hda_intel'. Please report this issue to the ALSA developers.
Apr 18 11:30:48 ben-laptop pulseaudio[1417]: alsa-sink.c: We were woken up with POLLOUT set -- however a subsequent snd_pcm_avail() returned 0 or another value < min_avail.
Apr 18 12:07:30 ben-laptop kernel: [ 3935.999686] compiz.real[1517]: segfault at 10 ip 00007fb3587a2f07 sp 00007fffce3872a8 error 4 in libGLcore.so.185.18.36[7fb357cac000+dda000]
Apr 18 12:40:41 ben-laptop pulseaudio[1417]: ratelimit.c: 137 events suppressed
Apr 18 12:45:02 ben-laptop pulseaudio[1417]: ratelimit.c: 159 events suppressed
Apr 18 13:01:51 ben-laptop kernel: [ 7196.290055] CE: hpet increasing min_delta_ns to 15000 nsec
Apr 18 13:42:01 ben-laptop kernel: [ 9606.330108] CE: hpet increasing min_delta_ns to 22500 nsec
```

A lot of things inside this file I didn't like. I couldn't find anything to do with the ssh or ftp and, apart from network manager being mentioned in a kernel warning, nothing from network either.

Thanks

B

---

### Post by john newbuntu on 2010-04-18
You can set these scripts to run automatically by using the update-rc.d command or by creating manual links to /etc/rc*.d or by adding the command line to /etc/rc.local.
Example:
```
sudo update-rc.d vsftpd defaults 80
sudo update-rc.d ssh defaults 16
```You might want to tweak the numbers 80 etc just to give it the order in which the script starts.

---

### Post by Bob Bertrands on 2010-04-18
I've allready tried. 
It returns  "System start/stop links for /etc/init.d/vsftpd already exist."
Same for ssh.

Thanks though

B

---

### Post by john newbuntu on 2010-04-18
Did you try doing "init 3" from the console and see if it starts the daemons.  Or perhaps as a hack, can you put a sleep command before launching the commands.

Edit: does adding the commands to /etc/rc.local with sleep help?

---

### Post by Bob Bertrands on 2010-04-19
If I execute sudo telinit 3 & enter my password nothing happens. This is very odd cause I remember using it before. (using just init 3 has no effect either)

I have no idee what you mean by > put a sleep command before launching the commandsor 

> adding the commands to /etc/rc.local with sleep

---

### Post by Bob Bertrands on 2010-04-19
update:

Appended the lines

/etc/init.d/vsftpd start
/etc/init.d/ssh start

to /etc/rc.local, sadly ssh & vsftpd are still down.
Don't think I have to put sudo in front of them since I have no way of actually giving my root password.

---

### Post by john newbuntu on 2010-04-20
By sleep command I meant to wait for a short while before running /etc/init.d/vsftpd start.
So, prepend say
sleep 120
just before the first command and see if that help although I am not sure if it will.  Also check the logs to see if these daemons are getting killed for some reason or unable to start.

---

### Post by darolu on 2010-04-20
> **john newbuntu said:**
> Did you try doing "init 3" from the console and see if it starts the daemons.
Ubuntu's default run level is runlevel 2; runlevel 2 to 5 have the exact same services so it wouldn't change anything.

The sleep idea from john newbuntu may work. Have you tried adding launchers to your start-up apps (using the GUI)?

> to **/etc/rc.local**, sadly ssh & vsftpd are still down.
Have you tried adding the lines to **/etc/init.d/local** instead?

---

### Post by Bob Bertrands on 2010-04-20
> Quote:
                                                 to **/etc/rc.local**, sadly ssh & vsftpd are still down.                                 
Have you tried adding the lines to **/etc/init.d/local** instead?I can't find the **/etc/init.d/local **file. Gues I don't have it. :confused:

The sleep-idea did not work either 

my /etc/rc.local file now looks like this:

```
#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.
sleep 120
/etc/init.d/vsfpd start
sleep 120
/etc/init.d/ssh start
exit 0
```

---

### Post by dcstar on 2010-04-20
> **Bob Bertrands said:**
> I can't find the **/etc/init.d/local **file. Gues I don't have it. :confused:

The sleep-idea did not work either 

my /etc/rc.local file now looks like this:

```
#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.
sleep 120
/etc/init.d/vsfpd start
sleep 120
/etc/init.d/ssh start
exit 0
```

Use the logger command to write to the syslog file so you can see when these are actually run.

---

### Post by Bob Bertrands on 2010-04-20
Like this : logger -f /var/log/syslog ??

---

### Post by darolu on 2010-04-20
> **Bob Bertrands said:**
> I can't find the **/etc/init.d/local **file. Gues I don't have it. :confused:

The sleep-idea did not work either 

my /etc/rc.local file now looks like this:

```
#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.
sleep 120
/etc/init.d/vsfpd start
sleep 120
/etc/init.d/ssh start
exit 0
```

No, the /etc/init.d/local file doesn't exist by default, the lines you added to your rc.local file *probably* are doing nothing as (as said in the file) by default it does nothing (deleting the "-e" may make it work); the documentation about rc.local for Ubuntu say we should be using a /etc/init.d/local file: [https://help.ubuntu.com/community/RcLocalHowto](https://help.ubuntu.com/community/RcLocalHowto)

---

### Post by john newbuntu on 2010-04-21
@bob: Correct me if I am wrong.  Should it be vsfpd or vsftpd in /etc/rc.local?

@darolu: The /etc/rc.local in a normal installation works.  This is called by /etc/rc*.d/S99rc.local and if the first file exists, it is run under the old systemV init protocol.  This works in Karmic since I personally run a script from there.

@bob: Are any of your scripts from say, /etc/rc2.d/ directory being run? Also, do you have /etc/init/rc.conf?  You mentioned in your first post that you have messed up big time with the OS. Is backing up your important files and reinstalling Ubuntu an option?  Remember, Lucid stable will be out in a little over a week.

Now, if you are sure that /etc/rc.local is being run, were you able to debug the output from vsftpd using the command: 
/etc/init.d/vsftpd start > /tmp/vsftpd.out 2>&1

---

### Post by Bob Bertrands on 2010-04-21
Changed vsfpd to vsftpd (thanx did'nt spot that)

> Are any of your scripts from say, /etc/rc2.d/ directory being run? 

This is the content of my /etc/rc2.d/ folder
```

K20rsync      S16ssh                 S20winbind         S99grub-common
K20saned      S20dkms_autoinstaller  S50cups            S99laptop-mode
K30dns-clean  S20kerneloops          S50pulseaudio      S99ondemand
K30pppd-dns   S20network-manager     S90binfmt-support  S99rc.local
K74bluetooth  S20speech-dispatcher   S91aolserver4
README        S20vsftpd              S99acpi-support
```

I'm pretty sure pulseaudio runs (I can play music and stuff), same for network-manager

> Also, do you have /etc/init/rc.conf?

yep, I do

> Is backing up your important files and reinstalling Ubuntu an option? Remember, Lucid stable will be out in a little over a week.

If I can't get this fixed I probably will. But I'd just hate to give up on ubuntu & am slightly obsessed with this.


> Now, if you are sure that /etc/rc.local is being run, were you able to debug the output from vsftpd using the command: 
/etc/init.d/vsftpd start > /tmp/vsftpd.out 2>&1 	

After running this the /tmp/vsftpd.out contains:

```
  * Starting FTP server: vsftpd
   ...done.
```

Like I allready said vsftpd works perfectly it's only not started from boot.

---

### Post by Bob Bertrands on 2010-04-21
my rc.conf file:

```
# rc - System V runlevel compatibility
#
# This task runs the old System V-style rc script when changing between
# runlevels.

description    "System V runlevel compatibility"
author        "Scott James Remnant <scott@netsplit.com>"

start on runlevel [0123456]
stop on runlevel [!$RUNLEVEL]

export RUNLEVEL
export PREVLEVEL

task

exec /etc/init.d/rc $RUNLEVEL
```my /etc/rc2.d/S99rc.local file contains this:

```
do_start() {
    if [ -x /etc/rc.local ]; then
            [ "$VERBOSE" != no ] && log_begin_msg "Running local boot scripts (/etc/rc.local)"
        /etc/rc.local
        ES=$?
        [ "$VERBOSE" != no ] && log_end_msg $ES
        return $ES
    fi
}

```Can someone explain to me what this "-x" after if && before /etc/rc.local??

B

---

### Post by john newbuntu on 2010-04-21
Did you get a chance to reboot and then check /tmp/vsftpd.out ?
"-x" checks if the file following it is executable.  '&&' is a logical operator that first checks the left side expression and if that is true, evaluates the right side expression.

---

### Post by Bob Bertrands on 2010-04-21
No change output is still: 
 > * Starting FTP server: vsftpd
   ...done.
When I execute
> /etc/init.d/vsftpd start > /tmp/vsftpd.out 2>&1     what does the last part - 2>&1 do?

---

### Post by john newbuntu on 2010-04-21
It redirects the standard error(if any) to the same output file.

---

### Post by Bob Bertrands on 2010-04-22
Update: still nothing works

Does anyone now how to test if a script was executed?

---

### Post by john newbuntu on 2010-04-23
Bob, Check the timestamp on the file /tmp/vsftpd.out.  If it matches the boot time of your machine, it means the script has run.
I am guessing your problem to be a timing issue but I do not have a solution.  Sorry about that. New install is an option but that could be major work.

However, there are workarounds for this.  Stick the 2 commands into a script one after the other.  Go to system->preferences->startup applications and select "add".  Give it any name.  For the command, click browse and choose the script.  Now, prefix the script name with gksu. Click add. The next time you log in, enter the password and check if your daemons are up.

---

### Post by Bob Bertrands on 2010-04-23
Appended 
```

/etc/init.d/vsftpd start > /var/log/vsftpd.out 2>&1 			 		
/etc/init.d/ssh start > /var/log/vsftpd.out 2>&1 			 		

```
to /etc/rc.local

Sadly those 2 files aren't generated.

Also tried your script-idea strangly the vsftpd & ssh processes aren't started after creating the script and adding to system-preferences-startupapps

---

### Post by john newbuntu on 2010-04-24
Is your script executable and did you add 'sudo' or 'gksudo' before those commands?  Check by just typing the name of the script and see if it brings up the daemons.  Also, did you give the full path of the script in the command line?
If your get 'permission denied' error while running the script, run "chmod 755 <scriptname>" and try again.

Now if all of the above are true and if it still does not work, the one other thing you can try is to add an icon to the panel on the top just to simplify running your script each time.  So right click the bar on the top and choose "add to panel".  Choose "custom application launcher" and click add.  Give anything for the name and click on the 'browse' button and point it to the location of your script.  Finally click 'ok'.  Now after you log the next time, you need to click on this icon once to fire up your daemons.

---

### Post by Bob Bertrands on 2010-04-24
Update: had to restart another time for it to work.

Now after I'm logged in I'm indeed prompted for my password and after giving it ssh & vsftpd works fine. 

My wireless is still down and I still don't know why my rc.local script isn't run.

B

---

### Post by Bob Bertrands on 2010-05-05
update: gave up and installed ubuntu 10.04 lts

---

