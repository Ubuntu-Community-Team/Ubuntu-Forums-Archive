---
title: "Brief interface/mouse stalls when opening or closing files"
date: 2009-08-26
forum: General Help
---

### Post by hvbakel on 2009-08-26
Since installing Jaunty (64bit, fresh install) a few months ago, I am (very) frequently experiencing brief interface freezes when I open various types of files or when I close programs. These freezes are most noticable when opening complicated pdf files in evince, which generally results in a brief ~1-second freeze, during which I can't move the mouse. Longer freezes will also interrupt sound.

I've tried to narrow down the problem by disabling compiz, but this has no effect. I've also installed the latest mainline kernel and several different versions of the Nvidia driver (180.x, 185.x and the 190.x betas). Unfortunately, none of this seems to have made any difference. The freezes seem to be related to disk activity, since they are correlated to disk writes when monitoring with iotop. There are no messages in any of the system logs that indicate errors. I've included the output from lspci with the system specs below. Any input on this problem would be greatly appreciated!

```

00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
00:01.0 PCI bridge: Intel Corporation Mobile 4 Series Chipset PCI Express Graphics Port (rev 07)
00:19.0 Ethernet controller: Intel Corporation 82567LM Gigabit Network Connection (rev 03)      
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)  
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)  
00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 3 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 4 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M-E LPC Interface Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
01:00.0 VGA compatible controller: nVidia Corporation Quadro NVS 160M (rev a1)
03:01.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev ba)
03:01.1 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 04)
03:01.2 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 21)
0c:00.0 Network controller: Intel Corporation Wireless WiFi Link 5100

```

---

### Post by hvbakel on 2009-09-05
bump

---

### Post by Liolikas on 2009-09-05
dmesg output?

---

### Post by hvbakel on 2009-09-05
```
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.30-02063005-generic (root@zinc) (gcc version 4.2.3 (Ubuntu 4.2.3-2ubuntu7)) #02063005 SMP Mon Aug 17 09:46:11 UTC 2009
[    0.000000] Command line: root=UUID=17996fdf-6d69-4a2d-96bd-f75bd3f4e780 ro quiet splash 
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   Centaur CentaurHauls
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f000 (usable)
[    0.000000]  BIOS-e820: 000000000009f000 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 00000000df44d400 (usable)
[    0.000000]  BIOS-e820: 00000000df44f400 - 00000000e0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000f8000000 - 00000000fc000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed18000 - 00000000fed1c000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed20000 - 00000000fed90000 (reserved)
[    0.000000]  BIOS-e820: 00000000feda0000 - 00000000feda6000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee10000 (reserved)
[    0.000000]  BIOS-e820: 00000000ffe60000 - 0000000100000000 (reserved)
[    0.000000]  BIOS-e820: 0000000100002000 - 0000000120000000 (usable)
[    0.000000] DMI 2.4 present.
[    0.000000] last_pfn = 0x120000 max_arch_pfn = 0x100000000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-CFFFF write-protect
[    0.000000]   D0000-EFFFF uncachable
[    0.000000]   F0000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000 mask 800000000 write-back
[    0.000000]   1 base 0E0000000 mask FE0000000 uncachable
[    0.000000]   2 disabled
[    0.000000]   3 disabled
[    0.000000]   4 disabled
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000] e820 update range: 00000000e0000000 - 0000000100000000 (usable) ==> (reserved)
[    0.000000] last_pfn = 0xdf44d max_arch_pfn = 0x100000000
[    0.000000] e820 update range: 0000000000001000 - 0000000000006000 (usable) ==> (reserved)
[    0.000000] Scanning 1 areas for low memory corruption
[    0.000000] modified physical RAM map:
[    0.000000]  modified: 0000000000000000 - 0000000000001000 (usable)
[    0.000000]  modified: 0000000000001000 - 0000000000006000 (reserved)
[    0.000000]  modified: 0000000000006000 - 000000000009f000 (usable)
[    0.000000]  modified: 000000000009f000 - 00000000000a0000 (reserved)
[    0.000000]  modified: 0000000000100000 - 00000000df44d400 (usable)
[    0.000000]  modified: 00000000df44f400 - 00000000e0000000 (reserved)
[    0.000000]  modified: 00000000f8000000 - 00000000fc000000 (reserved)
[    0.000000]  modified: 00000000fec00000 - 00000000fec10000 (reserved)
[    0.000000]  modified: 00000000fed18000 - 00000000fed1c000 (reserved)
[    0.000000]  modified: 00000000fed20000 - 00000000fed90000 (reserved)
[    0.000000]  modified: 00000000feda0000 - 00000000feda6000 (reserved)
[    0.000000]  modified: 00000000fee00000 - 00000000fee10000 (reserved)
[    0.000000]  modified: 00000000ffe60000 - 0000000100000000 (reserved)
[    0.000000]  modified: 0000000100002000 - 0000000120000000 (usable)
[    0.000000] init_memory_mapping: 0000000000000000-00000000df44d000
[    0.000000]  0000000000 - 00df400000 page 2M
[    0.000000]  00df400000 - 00df44d000 page 4k
[    0.000000] kernel direct mapping tables up to df44d000 @ 8000-e000
[    0.000000] init_memory_mapping: 0000000100000000-0000000120000000
[    0.000000]  0100000000 - 0120000000 page 2M
[    0.000000] kernel direct mapping tables up to 120000000 @ c000-12000
[    0.000000] RAMDISK: 37855000 - 37fef2af
[    0.000000] ACPI: RSDP 00000000000fb9c0 00024 (v02 DELL  )
[    0.000000] ACPI: XSDT 00000000df451e00 0006C (v01 DELL    M09     27D90508 ASL  00000061)
[    0.000000] ACPI: FACP 00000000df451c9c 000F4 (v04 DELL    M09     27D90508 ASL  00000061)
[    0.000000] ACPI: DSDT 00000000df452400 069AD (v02 INT430 SYSFexxx 00001001 INTL 20050624)
[    0.000000] ACPI: FACS 00000000df460c00 00040
[    0.000000] ACPI: HPET 00000000df451f00 00038 (v01 DELL    M09     00000001 ASL  00000061)
[    0.000000] ACPI: ____ 00000000df460400 00030 (v01 DELL    M09     27D90508 ASL  00000061)
[    0.000000] ACPI: APIC 00000000df452000 00068 (v01 DELL    M09     27D90508 ASL  00000047)
[    0.000000] ACPI: ASF! 00000000df451c00 0006A (v32 DELL    M09     27D90508 ASL  00000061)
[    0.000000] ACPI: MCFG 00000000df451fc0 0003E (v16 DELL    M09     27D90508 ASL  00000061)
[    0.000000] ACPI: TCPA 00000000df452300 00032 (v01                 00000000 ASL  00000000)
[    0.000000] ACPI: SLIC 00000000df45209c 00176 (v01 DELL    M09     27D90508 ASL  00000061)
[    0.000000] ACPI: SSDT 00000000df45032d 0066C (v01  PmRef    CpuPm 00003000 INTL 20050624)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] (8 early reservations) ==> bootmem [0000000000 - 0120000000]
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
[    0.000000]   #1 [0000006000 - 0000008000]       TRAMPOLINE ==> [0000006000 - 0000008000]
[    0.000000]   #2 [0000200000 - 0000bd7698]    TEXT DATA BSS ==> [0000200000 - 0000bd7698]
[    0.000000]   #3 [0037855000 - 0037fef2af]          RAMDISK ==> [0037855000 - 0037fef2af]
[    0.000000]   #4 [000009f000 - 0000100000]    BIOS reserved ==> [000009f000 - 0000100000]
[    0.000000]   #5 [0000bd8000 - 0000bd81e8]              BRK ==> [0000bd8000 - 0000bd81e8]
[    0.000000]   #6 [0000008000 - 000000c000]          PGTABLE ==> [0000008000 - 000000c000]
[    0.000000]   #7 [000000c000 - 000000d000]          PGTABLE ==> [000000c000 - 000000d000]
[    0.000000]  [ffffe20000000000-ffffe20003ffffff] PMD -> [ffff880028200000-ffff88002c1fffff] on node 0
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000000 -> 0x00001000
[    0.000000]   DMA32    0x00001000 -> 0x00100000
[    0.000000]   Normal   0x00100000 -> 0x00120000
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[4] active PFN ranges
[    0.000000]     0: 0x00000000 -> 0x00000001
[    0.000000]     0: 0x00000006 -> 0x0000009f
[    0.000000]     0: 0x00000100 -> 0x000df44d
[    0.000000]     0: 0x00100002 -> 0x00120000
[    0.000000] On node 0 totalpages: 1045477
[    0.000000]   DMA zone: 56 pages used for memmap
[    0.000000]   DMA zone: 2624 pages reserved
[    0.000000]   DMA zone: 1314 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 14280 pages used for memmap
[    0.000000]   DMA32 zone: 896133 pages, LIFO batch:31
[    0.000000]   Normal zone: 1792 pages used for memmap
[    0.000000]   Normal zone: 129278 pages, LIFO batch:31
[    0.000000] ACPI: PM-Timer IO Port: 0x1008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 0, address 0xfec00000, GSI 0-23
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
[    0.000000] PM: Registered nosave memory: 00000000df44d000 - 00000000df450000
[    0.000000] PM: Registered nosave memory: 00000000df450000 - 00000000e0000000
[    0.000000] PM: Registered nosave memory: 00000000e0000000 - 00000000f8000000
[    0.000000] PM: Registered nosave memory: 00000000f8000000 - 00000000fc000000
[    0.000000] PM: Registered nosave memory: 00000000fc000000 - 00000000fec00000
[    0.000000] PM: Registered nosave memory: 00000000fec00000 - 00000000fec10000
[    0.000000] PM: Registered nosave memory: 00000000fec10000 - 00000000fed18000
[    0.000000] PM: Registered nosave memory: 00000000fed18000 - 00000000fed1c000
[    0.000000] PM: Registered nosave memory: 00000000fed1c000 - 00000000fed20000
[    0.000000] PM: Registered nosave memory: 00000000fed20000 - 00000000fed90000
[    0.000000] PM: Registered nosave memory: 00000000fed90000 - 00000000feda0000
[    0.000000] PM: Registered nosave memory: 00000000feda0000 - 00000000feda6000
[    0.000000] PM: Registered nosave memory: 00000000feda6000 - 00000000fee00000
[    0.000000] PM: Registered nosave memory: 00000000fee00000 - 00000000fee10000
[    0.000000] PM: Registered nosave memory: 00000000fee10000 - 00000000ffe60000
[    0.000000] PM: Registered nosave memory: 00000000ffe60000 - 0000000100000000
[    0.000000] PM: Registered nosave memory: 0000000100000000 - 0000000100002000
[    0.000000] Allocating PCI resources starting at e2000000 (gap: e0000000:18000000)
[    0.000000] NR_CPUS:64 nr_cpumask_bits:64 nr_cpu_ids:2 nr_node_ids:1
[    0.000000] PERCPU: Embedded 27 pages at ffff88002801f000, static data 79968 bytes
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 1026725
[    0.000000] Kernel command line: root=UUID=17996fdf-6d69-4a2d-96bd-f75bd3f4e780 ro quiet splash 
[    0.000000] Initializing CPU#0
[    0.000000] xsave/xrstor: enabled xstate_bv 0x3, cntxt size 0x240
[    0.000000] NR_IRQS:2304
[    0.000000] PID hash table entries: 4096 (order: 12, 32768 bytes)
[    0.000000] Extended CMOS year: 2000
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 2394.262 MHz processor.
[    0.004000] Console: colour VGA+ 80x25
[    0.004000] console [tty0] enabled
[    0.004000] Dentry cache hash table entries: 524288 (order: 10, 4194304 bytes)
[    0.004000] Inode-cache hash table entries: 262144 (order: 9, 2097152 bytes)
[    0.004000] allocated 47185920 bytes of page_cgroup
[    0.004000] please try cgroup_disable=memory option if you don't want
[    0.004000] Checking aperture...
[    0.004000] No AGP bridge found
[    0.004000] Calgary: detecting Calgary via BIOS EBDA area
[    0.004000] Calgary: Unable to locate Rio Grande table in EBDA - bailing!
[    0.004000] PCI-DMA: Using software bounce buffering for IO (SWIOTLB)
[    0.004000] Placing 64MB software IO TLB between ffff880020000000 - ffff880024000000
[    0.004000] software IO TLB at phys 0x20000000 - 0x24000000
[    0.004000] Memory: 3978708k/4718592k available (4771k kernel code, 536684k absent, 202024k reserved, 2631k data, 528k init)
[    0.004000] SLUB: Genslabs=13, HWalign=64, Order=0-3, MinObjects=0, CPUs=2, Nodes=1
[    0.004000] hpet clockevent registered
[    0.004000] HPET: 4 timers in total, 0 timers will be used for per-cpu timer
[    0.004000] Calibrating delay loop (skipped), value calculated using timer frequency.. 4788.52 BogoMIPS (lpj=9577048)
[    0.004000] Security Framework initialized
[    0.004000] SELinux:  Disabled at boot.
[    0.004000] Mount-cache hash table entries: 256
[    0.004000] Initializing cgroup subsys ns
[    0.004000] Initializing cgroup subsys cpuacct
[    0.004000] Initializing cgroup subsys memory
[    0.004000] Initializing cgroup subsys freezer
[    0.004000] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.004000] CPU: L2 cache: 3072K
[    0.004000] CPU: Physical Processor ID: 0
[    0.004000] CPU: Processor Core ID: 0
[    0.004000] using mwait in idle threads.
[    0.004000] ACPI: Core revision 20090320
[    0.012050] Setting APIC routing to flat
[    0.012544] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.054296] CPU0: Intel(R) Core(TM)2 Duo CPU     P8600  @ 2.40GHz stepping 0a
[    0.056001] Booting processor 1 APIC 0x1 ip 0x6000
[    0.004000] Initializing CPU#1
[    0.004000] Calibrating delay using timer specific routine.. 4787.96 BogoMIPS (lpj=9575936)
[    0.004000] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.004000] CPU: L2 cache: 3072K
[    0.004000] CPU: Physical Processor ID: 0
[    0.004000] CPU: Processor Core ID: 1
[    0.140601] CPU1: Intel(R) Core(TM)2 Duo CPU     P8600  @ 2.40GHz stepping 0a
[    0.140621] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
[    0.144088] Brought up 2 CPUs
[    0.144090] Total of 2 processors activated (9576.49 BogoMIPS).
[    0.144139] CPU0 attaching sched-domain:
[    0.144141]  domain 0: span 0-1 level MC
[    0.144143]   groups: 0 1
[    0.144147] CPU1 attaching sched-domain:
[    0.144148]  domain 0: span 0-1 level MC
[    0.144150]   groups: 1 0
[    0.144210] net_namespace: 1888 bytes
[    0.144210] Booting paravirtualized kernel on bare hardware
[    0.144210] regulator: core version 0.5
[    0.144210] Time: 13:41:39  Date: 09/05/09
[    0.144210] NET: Registered protocol family 16
[    0.144210] ACPI: bus type pci registered
[    0.144235] PCI: MCFG configuration 0: base f8000000 segment 0 buses 0 - 63
[    0.144237] PCI: MCFG area at f8000000 reserved in E820
[    0.144764] PCI: Using MMCONFIG at f8000000 - fbffffff
[    0.144766] PCI: Using configuration type 1 for base access
[    0.145333] bio: create slab <bio-0> at 0
[    0.145346] ACPI: EC: Look up EC in DSDT
[    0.145346] ACPI: BIOS _OSI(Linux) query ignored
[    0.204019] ACPI: EC: non-query interrupt received, switching to interrupt mode
[    0.224204] ACPI: Interpreter enabled
[    0.224207] ACPI: (supports S0 S3 S4 S5)
[    0.224224] ACPI: Using IOAPIC for interrupt routing
[    0.327611] ACPI: EC: GPE = 0x11, I/O: command/status = 0x934, data = 0x930
[    0.327613] ACPI: EC: driver started in interrupt mode
[    0.329406] ACPI: No dock devices found.
[    0.329416] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.329500] pci 0000:00:01.0: PME# supported from D0 D3hot D3cold
[    0.329503] pci 0000:00:01.0: PME# disabled
[    0.329588] pci 0000:00:19.0: reg 10 32bit mmio: [0xf6fe0000-0xf6ffffff]
[    0.329596] pci 0000:00:19.0: reg 14 32bit mmio: [0xf6fdb000-0xf6fdbfff]
[    0.329603] pci 0000:00:19.0: reg 18 io port: [0xefe0-0xefff]
[    0.329654] pci 0000:00:19.0: PME# supported from D0 D3hot D3cold
[    0.329659] pci 0000:00:19.0: PME# disabled
[    0.329722] pci 0000:00:1a.0: reg 20 io port: [0x6f60-0x6f7f]
[    0.329809] pci 0000:00:1a.1: reg 20 io port: [0x6f80-0x6f9f]
[    0.329895] pci 0000:00:1a.2: reg 20 io port: [0x6fa0-0x6fbf]
[    0.329982] pci 0000:00:1a.7: reg 10 32bit mmio: [0xfed1c400-0xfed1c7ff]
[    0.330046] pci 0000:00:1a.7: PME# supported from D0 D3hot D3cold
[    0.330051] pci 0000:00:1a.7: PME# disabled
[    0.330103] pci 0000:00:1b.0: reg 10 64bit mmio: [0xf6fdc000-0xf6fdffff]
[    0.330159] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    0.330163] pci 0000:00:1b.0: PME# disabled
[    0.330240] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    0.330244] pci 0000:00:1c.0: PME# disabled
[    0.330324] pci 0000:00:1c.1: PME# supported from D0 D3hot D3cold
[    0.330328] pci 0000:00:1c.1: PME# disabled
[    0.330407] pci 0000:00:1c.2: PME# supported from D0 D3hot D3cold
[    0.330411] pci 0000:00:1c.2: PME# disabled
[    0.330493] pci 0000:00:1c.3: PME# supported from D0 D3hot D3cold
[    0.330497] pci 0000:00:1c.3: PME# disabled
[    0.330567] pci 0000:00:1d.0: reg 20 io port: [0x6f00-0x6f1f]
[    0.330653] pci 0000:00:1d.1: reg 20 io port: [0x6f20-0x6f3f]
[    0.330740] pci 0000:00:1d.2: reg 20 io port: [0x6f40-0x6f5f]
[    0.330828] pci 0000:00:1d.7: reg 10 32bit mmio: [0xfed1c000-0xfed1c3ff]
[    0.330891] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
[    0.330896] pci 0000:00:1d.7: PME# disabled
[    0.332203] pci 0000:00:1f.2: reg 10 io port: [0x6e70-0x6e77]
[    0.332210] pci 0000:00:1f.2: reg 14 io port: [0x6e78-0x6e7b]
[    0.332217] pci 0000:00:1f.2: reg 18 io port: [0x6e80-0x6e87]
[    0.332224] pci 0000:00:1f.2: reg 1c io port: [0x6e88-0x6e8b]
[    0.332231] pci 0000:00:1f.2: reg 20 io port: [0x6ea0-0x6ebf]
[    0.332238] pci 0000:00:1f.2: reg 24 32bit mmio: [0xfed1c800-0xfed1cfff]
[    0.332282] pci 0000:00:1f.2: PME# supported from D3hot
[    0.332286] pci 0000:00:1f.2: PME# disabled
[    0.332325] pci 0000:00:1f.3: reg 10 64bit mmio: [0xf6fdaf00-0xf6fdafff]
[    0.332343] pci 0000:00:1f.3: reg 20 io port: [0x1100-0x111f]
[    0.332424] pci 0000:01:00.0: reg 10 32bit mmio: [0xf5000000-0xf5ffffff]
[    0.332438] pci 0000:01:00.0: reg 14 64bit mmio: [0xe0000000-0xefffffff]
[    0.332453] pci 0000:01:00.0: reg 1c 64bit mmio: [0xf2000000-0xf3ffffff]
[    0.332461] pci 0000:01:00.0: reg 24 io port: [0xdf00-0xdf7f]
[    0.332469] pci 0000:01:00.0: reg 30 32bit mmio: [0x000000-0x01ffff]
[    0.332573] pci 0000:00:01.0: bridge io port: [0xd000-0xdfff]
[    0.332575] pci 0000:00:01.0: bridge 32bit mmio: [0xf2000000-0xf6efffff]
[    0.332579] pci 0000:00:01.0: bridge 64bit mmio pref: [0xe0000000-0xefffffff]
[    0.332750] pci 0000:0c:00.0: reg 10 64bit mmio: [0xf1ffe000-0xf1ffffff]
[    0.332867] pci 0000:0c:00.0: PME# supported from D0 D3hot D3cold
[    0.332878] pci 0000:0c:00.0: PME# disabled
[    0.332960] pci 0000:00:1c.1: bridge 32bit mmio: [0xf1f00000-0xf1ffffff]
[    0.333085] pci 0000:00:1c.3: bridge io port: [0xc000-0xcfff]
[    0.333089] pci 0000:00:1c.3: bridge 32bit mmio: [0xf1c00000-0xf1efffff]
[    0.333096] pci 0000:00:1c.3: bridge 64bit mmio pref: [0xf0000000-0xf01fffff]
[    0.333140] pci 0000:03:01.0: reg 10 32bit mmio: [0x000000-0x000fff]
[    0.333163] pci 0000:03:01.0: supports D1 D2
[    0.333165] pci 0000:03:01.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.333169] pci 0000:03:01.0: PME# disabled
[    0.333209] pci 0000:03:01.1: reg 10 32bit mmio: [0xf1bff800-0xf1bfffff]
[    0.333266] pci 0000:03:01.1: supports D1 D2
[    0.333267] pci 0000:03:01.1: PME# supported from D0 D1 D2 D3hot D3cold
[    0.333272] pci 0000:03:01.1: PME# disabled
[    0.333312] pci 0000:03:01.2: reg 10 32bit mmio: [0xf1bff700-0xf1bff7ff]
[    0.333368] pci 0000:03:01.2: supports D1 D2
[    0.333370] pci 0000:03:01.2: PME# supported from D0 D1 D2 D3hot D3cold
[    0.333374] pci 0000:03:01.2: PME# disabled
[    0.333443] pci 0000:00:1e.0: transparent bridge
[    0.333450] pci 0000:00:1e.0: bridge 32bit mmio: [0xf1b00000-0xf1bfffff]
[    0.333504] pci_bus 0000:00: on NUMA node 0
[    0.333509] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.333783] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCIE._PRT]
[    0.333882] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.AGP_._PRT]
[    0.333940] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP01._PRT]
[    0.334007] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP02._PRT]
[    0.334072] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP03._PRT]
[    0.334137] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP04._PRT]
[    0.346766] ACPI: PCI Interrupt Link [LNKA] (IRQs 10 11) *3
[    0.346890] ACPI: PCI Interrupt Link [LNKB] (IRQs 5 7) *10
[    0.347013] ACPI: PCI Interrupt Link [LNKC] (IRQs 10 *11)
[    0.347137] ACPI: PCI Interrupt Link [LNKD] (IRQs 5 7 *10 11)
[    0.347259] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 *10 11 12 14 15)
[    0.347383] ACPI: PCI Interrupt Link [LNKF] (IRQs *3 4 5 6 7 10 11 12 14 15)
[    0.347507] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 10 *11 12 14 15)
[    0.347619] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[    0.347759] SCSI subsystem initialized
[    0.347777] libata version 3.00 loaded.
[    0.347777] usbcore: registered new interface driver usbfs
[    0.347777] usbcore: registered new interface driver hub
[    0.347777] usbcore: registered new device driver usb
[    0.348023] ACPI: WMI: Mapper loaded
[    0.348024] PCI: Using ACPI for IRQ routing
[    0.360007] Bluetooth: Core ver 2.15
[    0.360018] NET: Registered protocol family 31
[    0.360018] Bluetooth: HCI device and connection manager initialized
[    0.360018] Bluetooth: HCI socket layer initialized
[    0.360018] NET: Registered protocol family 8
[    0.360018] NET: Registered protocol family 20
[    0.360028] NetLabel: Initializing
[    0.360029] NetLabel:  domain hash size = 128
[    0.360030] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.360041] NetLabel:  unlabeled traffic allowed by default
[    0.360067] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0
[    0.360071] hpet0: 4 comparators, 64-bit 14.318180 MHz counter
[    0.376005] pnp: PnP ACPI init
[    0.376011] ACPI: bus type pnp registered
[    0.444776] pnp: PnP ACPI: found 13 devices
[    0.444778] ACPI: ACPI bus type pnp unregistered
[    0.444787] system 00:05: ioport range 0xc80-0xcaf has been reserved
[    0.444789] system 00:05: ioport range 0xcc0-0xcff could not be reserved
[    0.444795] system 00:08: iomem range 0xfed00000-0xfed003ff has been reserved
[    0.444799] system 00:09: ioport range 0xcb0-0xcbb has been reserved
[    0.444802] system 00:09: iomem range 0xfed40000-0xfed44fff has been reserved
[    0.444806] system 00:0a: ioport range 0x900-0x92f has been reserved
[    0.444809] system 00:0a: ioport range 0x931-0x933 has been reserved
[    0.444811] system 00:0a: ioport range 0x935-0x97f has been reserved
[    0.444813] system 00:0a: ioport range 0x4d0-0x4d1 has been reserved
[    0.444816] system 00:0a: ioport range 0x1000-0x1005 has been reserved
[    0.444818] system 00:0a: ioport range 0x1008-0x100f has been reserved
[    0.444822] system 00:0b: ioport range 0xf400-0xf4fe has been reserved
[    0.444825] system 00:0b: ioport range 0x1006-0x1007 has been reserved
[    0.444827] system 00:0b: ioport range 0x100a-0x1059 could not be reserved
[    0.444829] system 00:0b: ioport range 0x1060-0x107f has been reserved
[    0.444832] system 00:0b: ioport range 0x1080-0x10bf has been reserved
[    0.444834] system 00:0b: ioport range 0x1100-0x111f has been reserved
[    0.444836] system 00:0b: ioport range 0x1010-0x102f has been reserved
[    0.444838] system 00:0b: ioport range 0x809-0x809 has been reserved
[    0.444843] system 00:0c: iomem range 0x0-0x9efff could not be reserved
[    0.444845] system 00:0c: iomem range 0x9f000-0x9ffff could not be reserved
[    0.444848] system 00:0c: iomem range 0xc0000-0xcffff has been reserved
[    0.444850] system 00:0c: iomem range 0xe0000-0xfffff has been reserved
[    0.444852] system 00:0c: iomem range 0x100000-0xdf44d3ff could not be reserved
[    0.444855] system 00:0c: iomem range 0xdf44d400-0xdfefffff could not be reserved
[    0.444857] system 00:0c: iomem range 0xdff00000-0xdfffffff has been reserved
[    0.444859] system 00:0c: iomem range 0xffe00000-0xffffffff could not be reserved
[    0.444862] system 00:0c: iomem range 0xffa00000-0xffbfffff has been reserved
[    0.444864] system 00:0c: iomem range 0xfec00000-0xfec0ffff could not be reserved
[    0.444867] system 00:0c: iomem range 0xfee00000-0xfee0ffff has been reserved
[    0.444869] system 00:0c: iomem range 0xfed20000-0xfed3ffff has been reserved
[    0.444871] system 00:0c: iomem range 0xfed45000-0xfed8ffff has been reserved
[    0.444874] system 00:0c: iomem range 0xfeda0000-0xfeda3fff has been reserved
[    0.444876] system 00:0c: iomem range 0xfeda4000-0xfeda4fff has been reserved
[    0.444879] system 00:0c: iomem range 0xfeda5000-0xfeda5fff has been reserved
[    0.444881] system 00:0c: iomem range 0xfeda6000-0xfeda6fff has been reserved
[    0.444883] system 00:0c: iomem range 0xfed1c800-0xfed1cfff has been reserved
[    0.444886] system 00:0c: iomem range 0xfed18000-0xfed1bfff has been reserved
[    0.444888] system 00:0c: iomem range 0xf8000000-0xfbffffff has been reserved
[    0.449522] pci 0000:00:01.0: PCI bridge, secondary bus 0000:01
[    0.449524] pci 0000:00:01.0:   IO window: 0xd000-0xdfff
[    0.449528] pci 0000:00:01.0:   MEM window: 0xf2000000-0xf6efffff
[    0.449531] pci 0000:00:01.0:   PREFETCH window: 0x000000e0000000-0x000000efffffff
[    0.449535] pci 0000:00:1c.0: PCI bridge, secondary bus 0000:0b
[    0.449536] pci 0000:00:1c.0:   IO window: disabled
[    0.449541] pci 0000:00:1c.0:   MEM window: disabled
[    0.449545] pci 0000:00:1c.0:   PREFETCH window: disabled
[    0.449552] pci 0000:00:1c.1: PCI bridge, secondary bus 0000:0c
[    0.449554] pci 0000:00:1c.1:   IO window: disabled
[    0.449559] pci 0000:00:1c.1:   MEM window: 0xf1f00000-0xf1ffffff
[    0.449563] pci 0000:00:1c.1:   PREFETCH window: disabled
[    0.449570] pci 0000:00:1c.2: PCI bridge, secondary bus 0000:0d
[    0.449572] pci 0000:00:1c.2:   IO window: disabled
[    0.449577] pci 0000:00:1c.2:   MEM window: disabled
[    0.449581] pci 0000:00:1c.2:   PREFETCH window: disabled
[    0.449588] pci 0000:00:1c.3: PCI bridge, secondary bus 0000:0e
[    0.449591] pci 0000:00:1c.3:   IO window: 0xc000-0xcfff
[    0.449596] pci 0000:00:1c.3:   MEM window: 0xf1c00000-0xf1efffff
[    0.449601] pci 0000:00:1c.3:   PREFETCH window: 0x000000f0000000-0x000000f01fffff
[    0.449612] pci 0000:03:01.0: CardBus bridge, secondary bus 0000:04
[    0.449614] pci 0000:03:01.0:   IO window: 0x002000-0x0020ff
[    0.449618] pci 0000:03:01.0:   IO window: 0x002400-0x0024ff
[    0.449623] pci 0000:03:01.0:   PREFETCH window: 0x120000000-0x123ffffff
[    0.449627] pci 0000:03:01.0:   MEM window: 0x124000000-0x127ffffff
[    0.449631] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:03
[    0.449635] pci 0000:00:1e.0:   IO window: 0x2000-0x2fff
[    0.449640] pci 0000:00:1e.0:   MEM window: 0xf1b00000-0xf1bfffff
[    0.449645] pci 0000:00:1e.0:   PREFETCH window: 0x00000120000000-0x00000123ffffff
[    0.449657] pci 0000:00:01.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.449660] pci 0000:00:01.0: setting latency timer to 64
[    0.449668] pci 0000:00:1c.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.449672] pci 0000:00:1c.0: setting latency timer to 64
[    0.449680] pci 0000:00:1c.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    0.449685] pci 0000:00:1c.1: setting latency timer to 64
[    0.449693] pci 0000:00:1c.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.449698] pci 0000:00:1c.2: setting latency timer to 64
[    0.449706] pci 0000:00:1c.3: PCI INT D -> GSI 19 (level, low) -> IRQ 19
[    0.449710] pci 0000:00:1c.3: setting latency timer to 64
[    0.449718] pci 0000:00:1e.0: setting latency timer to 64
[    0.449726] pci 0000:03:01.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    0.449731] pci_bus 0000:00: resource 0 io:  [0x00-0xffff]
[    0.449733] pci_bus 0000:00: resource 1 mem: [0x000000-0xffffffffffffffff]
[    0.449735] pci_bus 0000:01: resource 0 io:  [0xd000-0xdfff]
[    0.449737] pci_bus 0000:01: resource 1 mem: [0xf2000000-0xf6efffff]
[    0.449739] pci_bus 0000:01: resource 2 pref mem [0xe0000000-0xefffffff]
[    0.449742] pci_bus 0000:0c: resource 1 mem: [0xf1f00000-0xf1ffffff]
[    0.449744] pci_bus 0000:0e: resource 0 io:  [0xc000-0xcfff]
[    0.449746] pci_bus 0000:0e: resource 1 mem: [0xf1c00000-0xf1efffff]
[    0.449748] pci_bus 0000:0e: resource 2 pref mem [0xf0000000-0xf01fffff]
[    0.449750] pci_bus 0000:03: resource 0 io:  [0x2000-0x2fff]
[    0.449751] pci_bus 0000:03: resource 1 mem: [0xf1b00000-0xf1bfffff]
[    0.449753] pci_bus 0000:03: resource 2 pref mem [0x120000000-0x123ffffff]
[    0.449755] pci_bus 0000:03: resource 3 io:  [0x00-0xffff]
[    0.449757] pci_bus 0000:03: resource 4 mem: [0x000000-0xffffffffffffffff]
[    0.449759] pci_bus 0000:04: resource 0 io:  [0x2000-0x20ff]
[    0.449761] pci_bus 0000:04: resource 1 io:  [0x2400-0x24ff]
[    0.449763] pci_bus 0000:04: resource 2 pref mem [0x120000000-0x123ffffff]
[    0.449765] pci_bus 0000:04: resource 3 mem: [0x124000000-0x127ffffff]
[    0.449788] NET: Registered protocol family 2
[    0.484033] IP route cache hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.484423] TCP established hash table entries: 262144 (order: 10, 4194304 bytes)
[    0.485990] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[    0.486467] TCP: Hash tables configured (established 262144 bind 65536)
[    0.486470] TCP reno registered
[    0.496091] NET: Registered protocol family 1
[    0.496150] Trying to unpack rootfs image as initramfs...
[    0.500696] Switched to high resolution mode on CPU 1
[    0.503987] Switched to high resolution mode on CPU 0
[    0.650190] Freeing initrd memory: 7784k freed
[    0.653305] Scanning for low memory corruption every 60 seconds
[    0.653436] audit: initializing netlink socket (disabled)
[    0.653452] type=2000 audit(1252158098.653:1): initialized
[    0.661662] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    0.662690] VFS: Disk quotas dquot_6.5.2
[    0.662738] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    0.663161] fuse init (API version 7.11)
[    0.663225] msgmni has been set to 7788
[    0.663387] alg: No test for stdrng (krng)
[    0.663398] io scheduler noop registered
[    0.663400] io scheduler anticipatory registered
[    0.663401] io scheduler deadline registered
[    0.663411] io scheduler cfq registered (default)
[    0.663584] pci 0000:01:00.0: Boot video device
[    0.663691] pcieport-driver 0000:00:01.0: irq 24 for MSI/MSI-X
[    0.663700] pcieport-driver 0000:00:01.0: setting latency timer to 64
[    0.663824] pcieport-driver 0000:00:1c.0: irq 25 for MSI/MSI-X
[    0.663840] pcieport-driver 0000:00:1c.0: setting latency timer to 64
[    0.663986] pcieport-driver 0000:00:1c.1: irq 26 for MSI/MSI-X
[    0.664009] pcieport-driver 0000:00:1c.1: setting latency timer to 64
[    0.664156] pcieport-driver 0000:00:1c.2: irq 27 for MSI/MSI-X
[    0.664173] pcieport-driver 0000:00:1c.2: setting latency timer to 64
[    0.664317] pcieport-driver 0000:00:1c.3: irq 28 for MSI/MSI-X
[    0.664334] pcieport-driver 0000:00:1c.3: setting latency timer to 64
[    0.664425] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.664676] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.664831] ACPI: AC Adapter [AC] (on-line)
[    0.664892] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input0
[    0.665822] ACPI: Lid Switch [LID]
[    0.665860] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1
[    0.665866] ACPI: Power Button [PBTN]
[    0.665901] input: Sleep Button as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input2
[    0.665903] ACPI: Sleep Button [SBTN]
[    0.666630] ACPI: SSDT 00000000df450999 00281 (v01  PmRef   BspIst 00003000 INTL 20050624)
[    0.666982] ACPI: SSDT 00000000df450df1 005C6 (v01  PmRef   BspCst 00003001 INTL 20050624)
[    0.667515] Monitor-Mwait will be used to enter C-1 state
[    0.667537] Monitor-Mwait will be used to enter C-2 state
[    0.667555] Monitor-Mwait will be used to enter C-3 state
[    0.667561] Marking TSC unstable due to TSC halts in idle
[    0.667579] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[    0.667598] processor ACPI_CPU:00: registered as cooling_device0
[    0.667601] ACPI: Processor [CPU0] (supports 8 throttling states)
[    0.668016] ACPI: SSDT 00000000df450c1a 001D7 (v01  PmRef    ApIst 00003000 INTL 20050624)
[    0.668332] ACPI: SSDT 00000000df4513b7 0008D (v01  PmRef    ApCst 00003000 INTL 20050624)
[    0.669686] ACPI: CPU1 (power states: C1[C1] C2[C2] C3[C3])
[    0.669702] processor ACPI_CPU:01: registered as cooling_device1
[    0.669705] ACPI: Processor [CPU1] (supports 8 throttling states)
[    0.697991] thermal LNXTHERM:01: registered as thermal_zone0
[    0.697998] ACPI: Thermal Zone [THM] (49 C)
[    0.698044] XENFS: not registering filesystem on non-xen platform
[    0.698914] Linux agpgart interface v0.103
[    0.698921] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    0.699734] brd: module loaded
[    0.699990] loop: module loaded
[    0.700048] input: Macintosh mouse button emulation as /devices/virtual/input/input3
[    0.700070] Driver 'sd' needs updating - please use bus_type methods
[    0.700077] Driver 'sr' needs updating - please use bus_type methods
[    0.700110] ahci 0000:00:1f.2: version 3.0
[    0.700121] ahci 0000:00:1f.2: PCI INT D -> GSI 19 (level, low) -> IRQ 19
[    0.700159] ahci 0000:00:1f.2: irq 29 for MSI/MSI-X
[    0.700203] ahci: SSS flag set, parallel bus scan disabled
[    0.700239] ahci 0000:00:1f.2: AHCI 0001.0200 32 slots 4 ports 3 Gbps 0x33 impl SATA mode
[    0.700241] ahci 0000:00:1f.2: flags: 64bit ncq sntf stag pm led clo pmp pio slum part ems 
[    0.700246] ahci 0000:00:1f.2: setting latency timer to 64
[    0.703498] scsi0 : ahci
[    0.703740] scsi1 : ahci
[    0.703787] scsi2 : ahci
[    0.703831] scsi3 : ahci
[    0.703958] scsi4 : ahci
[    0.704021] scsi5 : ahci
[    0.704753] ata1: SATA max UDMA/133 abar m2048@0xfed1c800 port 0xfed1c900 irq 29
[    0.704756] ata2: SATA max UDMA/133 abar m2048@0xfed1c800 port 0xfed1c980 irq 29
[    0.704758] ata3: DUMMY
[    0.704759] ata4: DUMMY
[    0.704761] ata5: SATA max UDMA/133 abar m2048@0xfed1c800 port 0xfed1cb00 irq 29
[    0.704764] ata6: SATA max UDMA/133 abar m2048@0xfed1c800 port 0xfed1cb80 irq 29
[    0.705367] Fixed MDIO Bus: probed
[    0.705372] PPP generic driver version 2.4.2
[    0.705445] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.705463] ehci_hcd 0000:00:1a.7: PCI INT C -> GSI 22 (level, low) -> IRQ 22
[    0.705473] ehci_hcd 0000:00:1a.7: setting latency timer to 64
[    0.705476] ehci_hcd 0000:00:1a.7: EHCI Host Controller
[    0.705523] ehci_hcd 0000:00:1a.7: new USB bus registered, assigned bus number 1
[    0.709424] ehci_hcd 0000:00:1a.7: debug port 1
[    0.709430] ehci_hcd 0000:00:1a.7: cache line size of 32 is not supported
[    0.709441] ehci_hcd 0000:00:1a.7: irq 22, io mem 0xfed1c400
[    0.725277] ehci_hcd 0000:00:1a.7: USB 2.0 started, EHCI 1.00
[    0.725337] usb usb1: configuration #1 chosen from 1 choice
[    0.725361] hub 1-0:1.0: USB hub found
[    0.725366] hub 1-0:1.0: 6 ports detected
[    0.725450] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    0.725458] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    0.725461] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    0.725495] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 2
[    0.729413] ehci_hcd 0000:00:1d.7: debug port 1
[    0.729418] ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported
[    0.729429] ehci_hcd 0000:00:1d.7: irq 20, io mem 0xfed1c000
[    0.745011] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    0.745054] usb usb2: configuration #1 chosen from 1 choice
[    0.745075] hub 2-0:1.0: USB hub found
[    0.745080] hub 2-0:1.0: 6 ports detected
[    0.745103] ACPI: Battery Slot [BAT0] (battery present)
[    0.745153] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.745155] ACPI: Battery Slot [BAT1] (battery absent)
[    0.745168] uhci_hcd: USB Universal Host Controller Interface driver
[    0.745209] uhci_hcd 0000:00:1a.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    0.745215] uhci_hcd 0000:00:1a.0: setting latency timer to 64
[    0.745218] uhci_hcd 0000:00:1a.0: UHCI Host Controller
[    0.745249] uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 3
[    0.745280] uhci_hcd 0000:00:1a.0: irq 20, io base 0x00006f60
[    0.745343] usb usb3: configuration #1 chosen from 1 choice
[    0.745366] hub 3-0:1.0: USB hub found
[    0.745371] hub 3-0:1.0: 2 ports detected
[    0.745432] uhci_hcd 0000:00:1a.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[    0.745438] uhci_hcd 0000:00:1a.1: setting latency timer to 64
[    0.745441] uhci_hcd 0000:00:1a.1: UHCI Host Controller
[    0.745478] uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus number 4
[    0.745508] uhci_hcd 0000:00:1a.1: irq 21, io base 0x00006f80
[    0.745614] usb usb4: configuration #1 chosen from 1 choice
[    0.745636] hub 4-0:1.0: USB hub found
[    0.745641] hub 4-0:1.0: 2 ports detected
[    0.745703] uhci_hcd 0000:00:1a.2: PCI INT C -> GSI 22 (level, low) -> IRQ 22
[    0.745709] uhci_hcd 0000:00:1a.2: setting latency timer to 64
[    0.745712] uhci_hcd 0000:00:1a.2: UHCI Host Controller
[    0.745784] uhci_hcd 0000:00:1a.2: new USB bus registered, assigned bus number 5
[    0.745817] uhci_hcd 0000:00:1a.2: irq 22, io base 0x00006fa0
[    0.745881] usb usb5: configuration #1 chosen from 1 choice
[    0.745903] hub 5-0:1.0: USB hub found
[    0.745907] hub 5-0:1.0: 2 ports detected
[    0.745996] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    0.746001] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    0.746004] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    0.746037] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 6
[    0.746063] uhci_hcd 0000:00:1d.0: irq 20, io base 0x00006f00
[    0.746125] usb usb6: configuration #1 chosen from 1 choice
[    0.746145] hub 6-0:1.0: USB hub found
[    0.746149] hub 6-0:1.0: 2 ports detected
[    0.746212] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[    0.746217] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    0.746220] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    0.746257] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 7
[    0.746281] uhci_hcd 0000:00:1d.1: irq 21, io base 0x00006f20
[    0.746346] usb usb7: configuration #1 chosen from 1 choice
[    0.746368] hub 7-0:1.0: USB hub found
[    0.746373] hub 7-0:1.0: 2 ports detected
[    0.746433] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 22 (level, low) -> IRQ 22
[    0.746438] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    0.746441] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    0.746476] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 8
[    0.746499] uhci_hcd 0000:00:1d.2: irq 22, io base 0x00006f40
[    0.746598] usb usb8: configuration #1 chosen from 1 choice
[    0.746620] hub 8-0:1.0: USB hub found
[    0.746627] hub 8-0:1.0: 2 ports detected
[    0.746765] PNP: PS/2 Controller [PNP0303:KBC,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    0.747106] i8042.c: Warning: Keylock active.
[    0.771739] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.771744] serio: i8042 AUX port at 0x60,0x64 irq 12
[    0.771791] mice: PS/2 mouse device common for all mice
[    0.771881] rtc_cmos 00:03: RTC can wake from S4
[    0.771910] rtc_cmos 00:03: rtc core: registered rtc_cmos as rtc0
[    0.771937] rtc0: alarms up to one month, y3k, 114 bytes nvram, hpet irqs
[    0.772019] device-mapper: uevent: version 1.0.3
[    0.772078] device-mapper: ioctl: 4.14.0-ioctl (2008-04-23) initialised: dm-devel@redhat.com
[    0.772168] device-mapper: multipath: version 1.0.5 loaded
[    0.772171] device-mapper: multipath round-robin: version 1.0.0 loaded
[    0.772373] cpuidle: using governor ladder
[    0.772461] cpuidle: using governor menu
[    0.772766] TCP cubic registered
[    0.772861] NET: Registered protocol family 10
[    0.773207] lo: Disabled Privacy Extensions
[    0.773436] NET: Registered protocol family 17
[    0.773450] Bluetooth: L2CAP ver 2.13
[    0.773451] Bluetooth: L2CAP socket layer initialized
[    0.773454] Bluetooth: SCO (Voice Link) ver 0.6
[    0.773455] Bluetooth: SCO socket layer initialized
[    0.773488] Bluetooth: RFCOMM socket layer initialized
[    0.773491] Bluetooth: RFCOMM TTY layer initialized
[    0.773493] Bluetooth: RFCOMM ver 1.11
[    0.774568] PM: Resume from disk failed.
[    0.774579] registered taskstats version 1
[    0.774679]   Magic number: 9:902:684
[    0.774749] mem full: hash matches
[    0.774813] rtc_cmos 00:03: setting system clock to 2009-09-05 13:41:39 UTC (1252158099)
[    0.774816] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.774817] EDD information not available.
[    0.774897] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input4
[    1.000095] Clocksource tsc unstable (delta = -207872943 ns)
[    1.196101] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    1.227095] ata1.00: ATA-8: ST9320421AS, SD13, max UDMA/133
[    1.227099] ata1.00: 625142448 sectors, multi 8: LBA48 NCQ (depth 31/32)
[    1.271219] ata1.00: configured for UDMA/133
[    1.284228] scsi 0:0:0:0: Direct-Access     ATA      ST9320421AS      SD13 PQ: 0 ANSI: 5
[    1.284334] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    1.284377] sd 0:0:0:0: [sda] 625142448 512-byte hardware sectors: (320 GB/298 GiB)
[    1.284388] sd 0:0:0:0: [sda] Write Protect is off
[    1.284390] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.284408] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.284482]  sda: sda1 sda2 < sda5 >
[    1.325095] sd 0:0:0:0: [sda] Attached SCSI disk
[    1.384097] usb 5-1: new full speed USB device using uhci_hcd and address 2
[    1.557940] usb 5-1: configuration #0 chosen from 1 choice
[    1.557943] usb 5-1: config 0 descriptor??
[    1.808130] usb 7-1: new low speed USB device using uhci_hcd and address 2
[    1.983399] usb 7-1: configuration #1 chosen from 1 choice
[    2.172241] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    2.186817] ata2.00: ATAPI: TSSTcorp DVD+/-RW TS-U633A, D200, max UDMA/100, ATAPI AN
[    2.186829] ata2.00: applying bridge limits
[    2.200906] ata2.00: configured for UDMA/100
[    2.218698] scsi 1:0:0:0: CD-ROM            TSSTcorp DVD+-RW TS-U633A D200 PQ: 0 ANSI: 5
[    2.224352] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[    2.224356] Uniform CD-ROM driver Revision: 3.20
[    2.224427] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    2.224470] sr 1:0:0:0: Attached scsi generic sg1 type 5
[    2.544230] ata5: SATA link down (SStatus 0 SControl 300)
[    2.880246] ata6: SATA link down (SStatus 0 SControl 300)
[    2.896341] Freeing unused kernel memory: 528k freed
[    2.896506] Write protecting the kernel read-only data: 6860k
[    3.078633] e1000e: Intel(R) PRO/1000 Network Driver - 0.3.3.4-k4
[    3.078636] e1000e: Copyright (c) 1999-2008 Intel Corporation.
[    3.078694] e1000e 0000:00:19.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[    3.078706] e1000e 0000:00:19.0: setting latency timer to 64
[    3.078875] e1000e 0000:00:19.0: irq 30 for MSI/MSI-X
[    3.145541] ohci1394 0000:03:01.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    3.155946] usbcore: registered new interface driver hiddev
[    3.168545] input: Logitech Optical USB Mouse as /devices/pci0000:00/0000:00:1d.1/usb7/7-1/7-1:1.0/input/input5
[    3.168619] generic-usb 0003:046D:C016.0001: input,hidraw0: USB HID v1.10 Mouse [Logitech Optical USB Mouse] on usb-0000:00:1d.1-1/input0
[    3.168637] usbcore: registered new interface driver usbhid
[    3.168639] usbhid: v2.6:USB HID core driver
[    3.174787] 0000:00:19.0: eth0: (PCI Express:2.5GB/s:Width x1) 00:21:70:d7:e1:0b
[    3.174790] 0000:00:19.0: eth0: Intel(R) PRO/1000 Network Connection
[    3.174818] 0000:00:19.0: eth0: MAC: 7, PHY: 8, PBA No: 4003ff-0ff
[    3.206101] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[17]  MMIO=[f1bff800-f1bfffff]  Max Packet=[2048]  IR/IT contexts=[4/4]
[    3.473464] PM: Starting manual resume from disk
[    3.473468] PM: Resume from partition 8:5
[    3.473469] PM: Checking hibernation image.
[    3.473756] PM: Resume from disk failed.
[    3.517305] EXT4-fs: barriers enabled
[    3.540853] kjournald2 starting: pid 823, dev sda1:8, commit interval 5 seconds
[    3.540860] EXT4-fs: delayed allocation enabled
[    3.540861] EXT4-fs: file extents enabled
[    3.557510] EXT4-fs: mballoc enabled
[    3.557521] EXT4-fs: mounted filesystem sda1 with ordered data mode
[    4.484181] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[484fc0002318ce01]
[    6.415444] udev: starting version 141
[    6.729868] input: PC Speaker as /devices/platform/pcspkr/input/input6
[    6.736121] cfg80211: Calling CRDA to update world regulatory domain
[    6.799201] iTCO_vendor_support: vendor-support=0
[    6.801834] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.05
[    6.801909] iTCO_wdt: Found a ICH9M-E TCO device (Version=2, TCOBASE=0x1060)
[    6.801971] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[    6.840515] dcdbas dcdbas: Dell Systems Management Base Driver (version 5.6.0-3.2)
[    6.931314] cfg80211: World regulatory domain updated:
[    6.931317] 	(start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[    6.931319] 	(2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[    6.931321] 	(2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[    6.931323] 	(2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[    6.931325] 	(5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[    6.931327] 	(5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[    6.952988] yenta_cardbus 0000:03:01.0: CardBus bridge found [1028:024f]
[    7.082248] yenta_cardbus 0000:03:01.0: ISA IRQ mask 0x0cb8, PCI irq 19
[    7.082252] yenta_cardbus 0000:03:01.0: Socket status: 30000006
[    7.082256] pci_bus 0000:03: Raising subordinate bus# of parent bus (#03) from #04 to #07
[    7.082263] yenta_cardbus 0000:03:01.0: pcmcia: parent PCI bridge I/O window: 0x2000 - 0x2fff
[    7.082266] yenta_cardbus 0000:03:01.0: pcmcia: parent PCI bridge Memory window: 0xf1b00000 - 0xf1bfffff
[    7.082268] yenta_cardbus 0000:03:01.0: pcmcia: parent PCI bridge Memory window: 0x120000000 - 0x123ffffff
[    7.563923] nvidia: module license 'NVIDIA' taints kernel.
[    7.563927] Disabling lock debugging due to kernel taint
[    7.573765] sdhci: Secure Digital Host Controller Interface driver
[    7.573768] sdhci: Copyright(c) Pierre Ossman
[    7.582313] sdhci-pci 0000:03:01.2: SDHCI controller found [1180:0822] (rev 21)
[    7.582329] sdhci-pci 0000:03:01.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    7.584375] Registered led device: mmc0::
[    7.585411] mmc0: SDHCI controller on PCI [0000:03:01.2] using DMA
[    7.657346] acpi device:37: registered as cooling_device2
[    7.658039] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A03:00/device:34/device:35/input/input7
[    7.658076] ACPI: Video Device [VID] (multi-head: yes  rom: no  post: no)
[    7.676360] input: DualPoint Stick as /devices/platform/i8042/serio1/input/input8
[    7.693131] input: AlpsPS/2 ALPS DualPoint TouchPad as /devices/platform/i8042/serio1/input/input9
[    7.802815] iwlagn: Intel(R) Wireless WiFi Link AGN driver for Linux, 1.3.27k
[    7.802818] iwlagn: Copyright(c) 2003-2009 Intel Corporation
[    7.802915] iwlagn 0000:0c:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    7.802945] iwlagn 0000:0c:00.0: setting latency timer to 64
[    7.802996] iwlagn 0000:0c:00.0: Detected Intel Wireless WiFi Link 5100AGN REV=0x54
[    7.820354] nvidia 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    7.820369] nvidia 0000:01:00.0: setting latency timer to 64
[    7.820495] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  185.18.36  Fri Aug 14 17:35:21 PDT 2009
[    7.825583] iwlagn 0000:0c:00.0: Tunable channels: 13 802.11bg, 24 802.11a channels
[    7.825672] iwlagn 0000:0c:00.0: irq 31 for MSI/MSI-X
[    8.006871] phy0: Selected rate control algorithm 'iwl-agn-rs'
[    8.071317] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[    8.071341] HDA Intel 0000:00:1b.0: setting latency timer to 64
[    8.158173] input: HDA Intel Mic at Sep Left Jack as /devices/pci0000:00/0000:00:1b.0/input/input10
[    8.158235] input: HDA Intel Mic at Ext Right Jack as /devices/pci0000:00/0000:00:1b.0/input/input11
[    8.158279] input: HDA Intel Line Out at Sep Left Jack as /devices/pci0000:00/0000:00:1b.0/input/input12
[    8.158323] input: HDA Intel HP Out at Ext Right Jack as /devices/pci0000:00/0000:00:1b.0/input/input13
[    8.319990] lp: driver loaded but no devices found
[    8.375307] Adding 11679212k swap on /dev/sda5.  Priority:-1 extents:1 across:11679212k 
[    8.905048] EXT4 FS on sda1, internal journal on sda1:8
[   12.525209] ppdev: user-space parallel port driver
[   16.292298] e1000e 0000:00:19.0: irq 30 for MSI/MSI-X
[   16.352139] e1000e 0000:00:19.0: irq 30 for MSI/MSI-X
[   16.352753] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   16.353326] iwlagn 0000:0c:00.0: firmware: requesting iwlwifi-5000-2.ucode
[   16.393945] iwlagn 0000:0c:00.0: iwlwifi-5000-2.ucode firmware file req failed: -2
[   16.393949] iwlagn 0000:0c:00.0: firmware: requesting iwlwifi-5000-1.ucode
[   16.425855] iwlagn 0000:0c:00.0: Loaded firmware iwlwifi-5000-1.ucode, which is deprecated. Please use API v2 instead.
[   16.425860] iwlagn 0000:0c:00.0: Firmware has old API version. Expected v2, got v1. New firmware can be obtained from http://www.intellinuxwireless.org.
[   16.425862] iwlagn 0000:0c:00.0: loaded firmware version 5.4.1.16
[   16.579649] Registered led device: iwl-phy0::radio
[   16.579664] Registered led device: iwl-phy0::assoc
[   16.579676] Registered led device: iwl-phy0::RX
[   16.579688] Registered led device: iwl-phy0::TX
[   16.629644] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   18.104796] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: None
[   18.104800] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[   18.105351] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   20.026690] wlan0: authenticate with AP 06:24:36:a8:58:37
[   20.036594] wlan0: authenticated
[   20.036597] wlan0: associate with AP 06:24:36:a8:58:37
[   20.038878] wlan0: RX AssocResp from 06:24:36:a8:58:37 (capab=0x421 status=0 aid=1)
[   20.038881] wlan0: associated
[   20.041013] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   20.041086] wlan0: disassociating by local choice (reason=3)
[   28.460043] eth0: no IPv6 routers present
[   30.648012] wlan0: no IPv6 routers present
[   50.712294] wlan0: deauthenticated (Reason: 6)
```

---

### Post by hvbakel on 2009-10-23
In case it helps anyone, I solved this major annoyance by changing the nice level of the X server to -10. You can give this a try by running the following at the command line:

```
sudo renice -10 `pidof X`
```

Note that setting the nice level of X too low can cause latency issues for other applications, e.g. when playing sound. If this is the case, try varying the nice level between -10 and 0 to see what works best for you.

---

