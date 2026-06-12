---
title: "error messages upon boot.  Please Help"
date: 2009-08-09
forum: General Help
---

### Post by jim_ryan on 2009-08-09
I'm getting some messages when I boot and it doesn't seem like its a good thing, my screen then displays some red blocks and turquoise vertical bars (which is weird) then it goes to my regular login window and eveything seems fine, hopefully it is.

also please let me know if there is some private info in the syslog.0 that i should edit out... thanks..

---

### Post by Monicker on 2009-08-09
Hard to say.  You have a lot of non-essential information in that syslog snippet.  You might have better luck looking at the output of dmesg.

---

### Post by jim_ryan on 2009-08-10
Well whatever problem occurred yesterday cannot be replicated today.  A little background...

I have a dual boot machine, xp 64bit and ubuntu 64bit each on their own hard drive.  Yesterday, My xp system kept crashing with a blue screen of death machine_check_exception.  So i thought, huh, whats causing that?  lets check it out...  I rebooted into my ubuntu system and I got the weird errors on startup and red loading page with vertical blue bars.  Seemed like both systems were running in error.  Today both seem back to normal.

If it happens again, I'll post the dmesg log.

---

### Post by jim_ryan on 2009-08-15
and its back... i think.  

This shows up in dmesg, does this have something to do with my motherboard?
Phoenix BIOS detected: BIOS may corrupt low RAM, working it around.


```
[    0.000000] BIOS EBDA/lowmem at: 0009f000/0009f000
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.28-13-generic (buildd@yellow) (gcc version 4.3.3 (Ubuntu 4.3.3-5ubuntu4) ) #45-Ubuntu SMP Tue Jun 30 22:12:12 UTC 2009 (Ubuntu 2.6.28-13.45-generic)
[    0.000000] Command line: root=UUID=3b7a5306-39ed-4430-9fbc-44679fada010 ro quiet splash 
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   Centaur CentaurHauls
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f000 (usable)
[    0.000000]  BIOS-e820: 000000000009f000 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000009f790000 (usable)
[    0.000000]  BIOS-e820: 000000009f790000 - 000000009f7e3000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000009f7e3000 - 000000009f7f0000 (ACPI data)
[    0.000000]  BIOS-e820: 000000009f7f0000 - 00000000a0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 0000000100000000 (reserved)
[    0.000000]  BIOS-e820: 0000000100000000 - 00000001e0000000 (usable)
[    0.000000] DMI 2.5 present.
[    0.000000] Phoenix BIOS detected: BIOS may corrupt low RAM, working it around.
[    0.000000] last_pfn = 0x1e0000 max_arch_pfn = 0x3ffffffff
[    0.000000] last_pfn = 0x9f790 max_arch_pfn = 0x3ffffffff
[    0.000000] Scanning 0 areas for low memory corruption
[    0.000000] modified physical RAM map:
[    0.000000]  modified: 0000000000000000 - 0000000000010000 (reserved)
[    0.000000]  modified: 0000000000010000 - 000000000009f000 (usable)
[    0.000000]  modified: 000000000009f000 - 00000000000a0000 (reserved)
[    0.000000]  modified: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  modified: 0000000000100000 - 000000009f790000 (usable)
[    0.000000]  modified: 000000009f790000 - 000000009f7e3000 (ACPI NVS)
[    0.000000]  modified: 000000009f7e3000 - 000000009f7f0000 (ACPI data)
[    0.000000]  modified: 000000009f7f0000 - 00000000a0000000 (reserved)
[    0.000000]  modified: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  modified: 00000000fec00000 - 0000000100000000 (reserved)
[    0.000000]  modified: 0000000100000000 - 00000001e0000000 (usable)
[    0.000000] init_memory_mapping: 0000000000000000-000000009f790000
[    0.000000]  0000000000 - 009f600000 page 2M
[    0.000000]  009f600000 - 009f790000 page 4k
[    0.000000] kernel direct mapping tables up to 9f790000 @ 10000-15000
[    0.000000] last_map_addr: 9f790000 end: 9f790000
[    0.000000] init_memory_mapping: 0000000100000000-00000001e0000000
[    0.000000]  0100000000 - 01e0000000 page 2M
[    0.000000] kernel direct mapping tables up to 1e0000000 @ 13000-1c000
[    0.000000] last_map_addr: 1e0000000 end: 1e0000000
[    0.000000] RAMDISK: 37859000 - 37fef42a
[    0.000000] ACPI: RSDP 000F9980, 0024 (r2 IntelR)
[    0.000000] ACPI: XSDT 9F7E3080, 004C (r1 IntelR AWRDACPI 42302E31 AWRD        0)
[    0.000000] ACPI: FACP 9F7EAE80, 00F4 (r3 IntelR AWRDACPI 42302E31 AWRD        0)
[    0.000000] FADT: X_PM1a_EVT_BLK.bit_width (8) does not match PM1_EVT_LEN (4)
[    0.000000] ACPI Warning (tbfadt-0460): Optional field "Pm2ControlBlock" has zero address or length: 0000000000000450/0 [20080926]
[    0.000000] ACPI: DSDT 9F7E3200, 783E (r1 INTELR AWRDACPI     1000 MSFT  3000000)
[    0.000000] ACPI: FACS 9F790000, 0040
[    0.000000] ACPI: SLIC 9F7EAA40, 0424 (r1 IntelR AWRDACPI 42302E31 AWRD        0)
[    0.000000] ACPI: MCFG 9F7EB080, 003C (r1 IntelR AWRDACPI 42302E31 AWRD        0)
[    0.000000] ACPI: APIC 9F7EAF80, 00BC (r1 IntelR AWRDACPI 42302E31 AWRD        0)
[    0.000000] ACPI: SSDT 9F7EB0C0, 1C74 (r1  INTEL PPM RCM  80000001 INTL 20061109)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] (7 early reservations) ==> bootmem [0000000000 - 01e0000000]
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
[    0.000000]   #1 [0000006000 - 0000008000]       TRAMPOLINE ==> [0000006000 - 0000008000]
[    0.000000]   #2 [0000200000 - 0000b7bbb0]    TEXT DATA BSS ==> [0000200000 - 0000b7bbb0]
[    0.000000]   #3 [0037859000 - 0037fef42a]          RAMDISK ==> [0037859000 - 0037fef42a]
[    0.000000]   #4 [000009f000 - 0000100000]    BIOS reserved ==> [000009f000 - 0000100000]
[    0.000000]   #5 [0000010000 - 0000013000]          PGTABLE ==> [0000010000 - 0000013000]
[    0.000000]   #6 [0000013000 - 0000017000]          PGTABLE ==> [0000013000 - 0000017000]
[    0.000000] found SMP MP-table at [ffff8800000f5740] 000f5740
[    0.000000]  [ffffe20000000000-ffffe200069fffff] PMD -> [ffff880028200000-ffff88002ebfffff] on node 0
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000010 -> 0x00001000
[    0.000000]   DMA32    0x00001000 -> 0x00100000
[    0.000000]   Normal   0x00100000 -> 0x001e0000
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[3] active PFN ranges
[    0.000000]     0: 0x00000010 -> 0x0000009f
[    0.000000]     0: 0x00000100 -> 0x0009f790
[    0.000000]     0: 0x00100000 -> 0x001e0000
[    0.000000] On node 0 totalpages: 1570591
[    0.000000]   DMA zone: 56 pages used for memmap
[    0.000000]   DMA zone: 2536 pages reserved
[    0.000000]   DMA zone: 1391 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 14280 pages used for memmap
[    0.000000]   DMA32 zone: 634824 pages, LIFO batch:31
[    0.000000]   Normal zone: 12544 pages used for memmap
[    0.000000]   Normal zone: 904960 pages, LIFO batch:31
[    0.000000]   Movable zone: 0 pages used for memmap
[    0.000000] ACPI: PM-Timer IO Port: 0x408
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x06] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x02] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x04] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x07] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x05] lapic_id[0x05] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x06] lapic_id[0x03] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x07] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x02] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x03] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x04] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x05] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x06] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x07] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x08] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 8, version 0, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] SMP: Allowing 8 CPUs, 0 hotplug CPUs
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000f0000
[    0.000000] PM: Registered nosave memory: 00000000000f0000 - 0000000000100000
[    0.000000] PM: Registered nosave memory: 000000009f790000 - 000000009f7e3000
[    0.000000] PM: Registered nosave memory: 000000009f7e3000 - 000000009f7f0000
[    0.000000] PM: Registered nosave memory: 000000009f7f0000 - 00000000a0000000
[    0.000000] PM: Registered nosave memory: 00000000a0000000 - 00000000e0000000
[    0.000000] PM: Registered nosave memory: 00000000e0000000 - 00000000f0000000
[    0.000000] PM: Registered nosave memory: 00000000f0000000 - 00000000fec00000
[    0.000000] PM: Registered nosave memory: 00000000fec00000 - 0000000100000000
[    0.000000] Allocating PCI resources starting at a4000000 (gap: a0000000:40000000)
[    0.000000] PERCPU: Allocating 69632 bytes of per cpu data
[    0.000000] NR_CPUS: 64, nr_cpu_ids: 8, nr_node_ids 1
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 1541175
[    0.000000] Kernel command line: root=UUID=3b7a5306-39ed-4430-9fbc-44679fada010 ro quiet splash 
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 32768 bytes)
[    0.000000] TSC: PIT calibration matches PMTIMER. 1 loops
[    0.000000] Detected 2653.341 MHz processor.
[    0.004000] Console: colour VGA+ 80x25
[    0.004000] console [tty0] enabled
[    0.004000] Dentry cache hash table entries: 1048576 (order: 11, 8388608 bytes)
[    0.004000] Inode-cache hash table entries: 524288 (order: 10, 4194304 bytes)
[    0.004000] allocated 78643200 bytes of page_cgroup
[    0.004000] please try cgroup_disable=memory option if you don't want
[    0.004000] Scanning for low memory corruption every 60 seconds
[    0.004000] Checking aperture...
[    0.004000] No AGP bridge found
[    0.004000] Calgary: detecting Calgary via BIOS EBDA area
[    0.004000] Calgary: Unable to locate Rio Grande table in EBDA - bailing!
[    0.004000] PCI-DMA: Using software bounce buffering for IO (SWIOTLB)
[    0.004000] Placing software IO TLB between 0x20000000 - 0x24000000
[    0.004000] Memory: 5999516k/7864320k available (4743k kernel code, 1581956k absent, 281920k reserved, 2525k data, 532k init)
[    0.004000] SLUB: Genslabs=12, HWalign=64, Order=0-3, MinObjects=0, CPUs=8, Nodes=1
[    0.004009] Calibrating delay loop (skipped), value calculated using timer frequency.. 5306.68 BogoMIPS (lpj=10613364)
[    0.004019] Security Framework initialized
[    0.004022] SELinux:  Disabled at boot.
[    0.004032] AppArmor: AppArmor initialized
[    0.004037] Mount-cache hash table entries: 256
[    0.004104] Initializing cgroup subsys ns
[    0.004106] Initializing cgroup subsys cpuacct
[    0.004108] Initializing cgroup subsys memory
[    0.004109] Initializing cgroup subsys freezer
[    0.004117] CPU: Physical Processor ID: 0
[    0.004118] CPU: Processor Core ID: 0
[    0.004120] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.004121] CPU: L2 cache: 256K
[    0.004122] CPU: L3 cache: 8192K
[    0.004124] using mwait in idle threads.
[    0.005542] ACPI: Core revision 20080926
[    0.007514] ACPI: Checking initramfs for custom DSDT
[    0.252038] Setting APIC routing to flat
[    0.252424] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.293449] CPU0: Intel(R) Core(TM) i7 CPU         920  @ 2.67GHz stepping 05
[    0.296001] Booting processor 1 APIC 0x6 ip 0x6000
[    0.004000] Initializing CPU#1
[    0.004000] Calibrating delay using timer specific routine.. 5306.76 BogoMIPS (lpj=10613524)
[    0.004000] CPU: Physical Processor ID: 0
[    0.004000] CPU: Processor Core ID: 3
[    0.004000] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.004000] CPU: L2 cache: 256K
[    0.004000] CPU: L3 cache: 8192K
[    0.380474] CPU1: Intel(R) Core(TM) i7 CPU         920  @ 2.67GHz stepping 05
[    0.380496] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
[    0.384066] Booting processor 2 APIC 0x2 ip 0x6000
[    0.004000] Initializing CPU#2
[    0.004000] Calibrating delay using timer specific routine.. 5306.76 BogoMIPS (lpj=10613536)
[    0.004000] CPU: Physical Processor ID: 0
[    0.004000] CPU: Processor Core ID: 1
[    0.004000] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.004000] CPU: L2 cache: 256K
[    0.004000] CPU: L3 cache: 8192K
[    0.472498] CPU2: Intel(R) Core(TM) i7 CPU         920  @ 2.67GHz stepping 05
[    0.472516] checking TSC synchronization [CPU#0 -> CPU#2]: passed.
[    0.476071] Booting processor 3 APIC 0x4 ip 0x6000
[    0.004000] Initializing CPU#3
[    0.004000] Calibrating delay using timer specific routine.. 5306.76 BogoMIPS (lpj=10613538)
[    0.004000] CPU: Physical Processor ID: 0
[    0.004000] CPU: Processor Core ID: 2
[    0.004000] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.004000] CPU: L2 cache: 256K
[    0.004000] CPU: L3 cache: 8192K
[    0.564420] CPU3: Intel(R) Core(TM) i7 CPU         920  @ 2.67GHz stepping 05
[    0.564442] checking TSC synchronization [CPU#0 -> CPU#3]: passed.
[    0.568069] Booting processor 4 APIC 0x7 ip 0x6000
[    0.004000] Initializing CPU#4
[    0.004000] Calibrating delay using timer specific routine.. 5306.76 BogoMIPS (lpj=10613537)
[    0.004000] CPU: Physical Processor ID: 0
[    0.004000] CPU: Processor Core ID: 3
[    0.004000] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.004000] CPU: L2 cache: 256K
[    0.004000] CPU: L3 cache: 8192K
[    0.656541] CPU4: Intel(R) Core(TM) i7 CPU         920  @ 2.67GHz stepping 05
[    0.656563] checking TSC synchronization [CPU#0 -> CPU#4]: passed.
[    0.660066] Booting processor 5 APIC 0x5 ip 0x6000
[    0.004000] Initializing CPU#5
[    0.004000] Calibrating delay using timer specific routine.. 5306.76 BogoMIPS (lpj=10613535)
[    0.004000] CPU: Physical Processor ID: 0
[    0.004000] CPU: Processor Core ID: 2
[    0.004000] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.004000] CPU: L2 cache: 256K
[    0.004000] CPU: L3 cache: 8192K
[    0.748560] CPU5: Intel(R) Core(TM) i7 CPU         920  @ 2.67GHz stepping 05
[    0.748582] checking TSC synchronization [CPU#0 -> CPU#5]: passed.
[    0.752069] Booting processor 6 APIC 0x3 ip 0x6000
[    0.004000] Initializing CPU#6
[    0.004000] Calibrating delay using timer specific routine.. 5306.77 BogoMIPS (lpj=10613546)
[    0.004000] CPU: Physical Processor ID: 0
[    0.004000] CPU: Processor Core ID: 1
[    0.004000] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.004000] CPU: L2 cache: 256K
[    0.004000] CPU: L3 cache: 8192K
[    0.840483] CPU6: Intel(R) Core(TM) i7 CPU         920  @ 2.67GHz stepping 05
[    0.840505] checking TSC synchronization [CPU#0 -> CPU#6]: passed.
[    0.844070] Booting processor 7 APIC 0x1 ip 0x6000
[    0.004000] Initializing CPU#7
[    0.004000] Calibrating delay using timer specific routine.. 5306.76 BogoMIPS (lpj=10613521)
[    0.004000] CPU: Physical Processor ID: 0
[    0.004000] CPU: Processor Core ID: 0
[    0.004000] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.004000] CPU: L2 cache: 256K
[    0.004000] CPU: L3 cache: 8192K
[    0.932494] CPU7: Intel(R) Core(TM) i7 CPU         920  @ 2.67GHz stepping 05
[    0.932515] checking TSC synchronization [CPU#0 -> CPU#7]: passed.
[    0.936030] Brought up 8 CPUs
[    0.936032] Total of 8 processors activated (42454.05 BogoMIPS).
[    0.936081] CPU0 attaching sched-domain:
[    0.936083]  domain 0: span 0,7 level SIBLING
[    0.936084]   groups: 0 7
[    0.936087]   domain 1: span 0-7 level MC
[    0.936088]    groups: 0,7 1,4 2,6 3,5
[    0.936092] CPU1 attaching sched-domain:
[    0.936093]  domain 0: span 1,4 level SIBLING
[    0.936094]   groups: 1 4
[    0.936095]   domain 1: span 0-7 level MC
[    0.936096]    groups: 1,4 2,6 3,5 0,7
[    0.936099] CPU2 attaching sched-domain:
[    0.936100]  domain 0: span 2,6 level SIBLING
[    0.936101]   groups: 2 6
[    0.936103]   domain 1: span 0-7 level MC
[    0.936104]    groups: 2,6 3,5 0,7 1,4
[    0.936107] CPU3 attaching sched-domain:
[    0.936108]  domain 0: span 3,5 level SIBLING
[    0.936109]   groups: 3 5
[    0.936110]   domain 1: span 0-7 level MC
[    0.936111]    groups: 3,5 0,7 1,4 2,6
[    0.936114] CPU4 attaching sched-domain:
[    0.936115]  domain 0: span 1,4 level SIBLING
[    0.936116]   groups: 4 1
[    0.936118]   domain 1: span 0-7 level MC
[    0.936119]    groups: 1,4 2,6 3,5 0,7
[    0.936122] CPU5 attaching sched-domain:
[    0.936123]  domain 0: span 3,5 level SIBLING
[    0.936124]   groups: 5 3
[    0.936125]   domain 1: span 0-7 level MC
[    0.936126]    groups: 3,5 0,7 1,4 2,6
[    0.936129] CPU6 attaching sched-domain:
[    0.936130]  domain 0: span 2,6 level SIBLING
[    0.936131]   groups: 6 2
[    0.936133]   domain 1: span 0-7 level MC
[    0.936134]    groups: 2,6 3,5 0,7 1,4
[    0.936137] CPU7 attaching sched-domain:
[    0.936138]  domain 0: span 0,7 level SIBLING
[    0.936139]   groups: 7 0
[    0.936140]   domain 1: span 0-7 level MC
[    0.936141]    groups: 0,7 1,4 2,6 3,5
[    0.936255] net_namespace: 1400 bytes
[    0.936255] Booting paravirtualized kernel on bare hardware
[    0.936255] Time:  4:49:54  Date: 08/15/09
[    0.936255] regulator: core version 0.5
[    0.936255] NET: Registered protocol family 16
[    0.936255] ACPI FADT declares the system doesn't support PCIe ASPM, so disable it
[    0.936255] ACPI: bus type pci registered
[    0.936255] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 255
[    0.936255] PCI: MCFG area at e0000000 reserved in E820
[    0.944154] PCI: Using MMCONFIG at e0000000 - efffffff
[    0.944155] PCI: Using configuration type 1 for base access
[    0.944590] ACPI: EC: Look up EC in DSDT
[    0.952692] ACPI: Interpreter enabled
[    0.952693] ACPI: (supports S0 S1 S4 S5)
[    0.952707] ACPI: Using IOAPIC for interrupt routing
[    0.957790] ACPI: No dock devices found.
[    0.957797] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.957852] pci 0000:00:00.0: PME# supported from D0 D3hot D3cold
[    0.957854] pci 0000:00:00.0: PME# disabled
[    0.957892] pci 0000:00:01.0: PME# supported from D0 D3hot D3cold
[    0.957895] pci 0000:00:01.0: PME# disabled
[    0.957937] pci 0000:00:03.0: PME# supported from D0 D3hot D3cold
[    0.957940] pci 0000:00:03.0: PME# disabled
[    0.957984] pci 0000:00:07.0: PME# supported from D0 D3hot D3cold
[    0.957986] pci 0000:00:07.0: PME# disabled
[    0.958028] pci 0000:00:09.0: PME# supported from D0 D3hot D3cold
[    0.958030] pci 0000:00:09.0: PME# disabled
[    0.958223] pci 0000:00:1a.0: reg 20 io port: [0xff00-0xff1f]
[    0.958283] pci 0000:00:1a.1: reg 20 io port: [0xfe00-0xfe1f]
[    0.958339] pci 0000:00:1a.2: reg 20 io port: [0xfd00-0xfd1f]
[    0.958404] pci 0000:00:1a.7: reg 10 32bit mmio: [0xf3ffe000-0xf3ffe3ff]
[    0.958443] pci 0000:00:1a.7: PME# supported from D0 D3hot D3cold
[    0.958450] pci 0000:00:1a.7: PME# disabled
[    0.958488] pci 0000:00:1b.0: reg 10 64bit mmio: [0xf3ff4000-0xf3ff7fff]
[    0.958515] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    0.958522] pci 0000:00:1b.0: PME# disabled
[    0.958563] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    0.958570] pci 0000:00:1c.0: PME# disabled
[    0.958613] pci 0000:00:1c.1: PME# supported from D0 D3hot D3cold
[    0.958619] pci 0000:00:1c.1: PME# disabled
[    0.958662] pci 0000:00:1c.2: PME# supported from D0 D3hot D3cold
[    0.958668] pci 0000:00:1c.2: PME# disabled
[    0.958712] pci 0000:00:1c.4: PME# supported from D0 D3hot D3cold
[    0.958714] pci 0000:00:1c.4: PME# disabled
[    0.958760] pci 0000:00:1d.0: reg 20 io port: [0xfc00-0xfc1f]
[    0.958816] pci 0000:00:1d.1: reg 20 io port: [0xfb00-0xfb1f]
[    0.958876] pci 0000:00:1d.2: reg 20 io port: [0xfa00-0xfa1f]
[    0.958935] pci 0000:00:1d.7: reg 10 32bit mmio: [0xf3ffd000-0xf3ffd3ff]
[    0.958971] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
[    0.958978] pci 0000:00:1d.7: PME# disabled
[    0.959110] pci 0000:00:1f.2: reg 10 io port: [0xf900-0xf907]
[    0.959118] pci 0000:00:1f.2: reg 14 io port: [0xf800-0xf803]
[    0.959126] pci 0000:00:1f.2: reg 18 io port: [0xf700-0xf707]
[    0.959134] pci 0000:00:1f.2: reg 1c io port: [0xf600-0xf603]
[    0.959139] pci 0000:00:1f.2: reg 20 io port: [0xf500-0xf50f]
[    0.959147] pci 0000:00:1f.2: reg 24 io port: [0xf400-0xf40f]
[    0.959180] pci 0000:00:1f.3: reg 10 64bit mmio: [0xf3ffc000-0xf3ffc0ff]
[    0.959195] pci 0000:00:1f.3: reg 20 io port: [0x500-0x51f]
[    0.959238] pci 0000:00:1f.5: reg 10 io port: [0xf200-0xf207]
[    0.959246] pci 0000:00:1f.5: reg 14 io port: [0xf100-0xf103]
[    0.959254] pci 0000:00:1f.5: reg 18 io port: [0xf000-0xf007]
[    0.959259] pci 0000:00:1f.5: reg 1c io port: [0xef00-0xef03]
[    0.959267] pci 0000:00:1f.5: reg 20 io port: [0xee00-0xee0f]
[    0.959275] pci 0000:00:1f.5: reg 24 io port: [0xed00-0xed0f]
[    0.959313] pci 0000:00:01.0: bridge io port: [0xb000-0xbfff]
[    0.959316] pci 0000:00:01.0: bridge 32bit mmio: [0xf3200000-0xf32fffff]
[    0.959319] pci 0000:00:01.0: bridge 64bit mmio pref: [0xf3100000-0xf31fffff]
[    0.959343] pci 0000:02:00.0: reg 10 32bit mmio: [0xde000000-0xdeffffff]
[    0.959350] pci 0000:02:00.0: reg 14 64bit mmio: [0xc0000000-0xcfffffff]
[    0.959357] pci 0000:02:00.0: reg 1c 64bit mmio: [0xdc000000-0xddffffff]
[    0.959361] pci 0000:02:00.0: reg 24 io port: [0xaf00-0xaf7f]
[    0.959365] pci 0000:02:00.0: reg 30 32bit mmio: [0xdff80000-0xdfffffff]
[    0.959392] pci 0000:00:03.0: bridge io port: [0xa000-0xafff]
[    0.959394] pci 0000:00:03.0: bridge 32bit mmio: [0xdc000000-0xdfffffff]
[    0.959398] pci 0000:00:03.0: bridge 64bit mmio pref: [0xc0000000-0xcfffffff]
[    0.959422] pci 0000:03:00.0: reg 10 32bit mmio: [0xda000000-0xdaffffff]
[    0.959429] pci 0000:03:00.0: reg 14 64bit mmio: [0xb0000000-0xbfffffff]
[    0.959436] pci 0000:03:00.0: reg 1c 64bit mmio: [0xd8000000-0xd9ffffff]
[    0.959440] pci 0000:03:00.0: reg 24 io port: [0x8f00-0x8f7f]
[    0.959444] pci 0000:03:00.0: reg 30 32bit mmio: [0x000000-0x07ffff]
[    0.959471] pci 0000:00:07.0: bridge io port: [0x8000-0x8fff]
[    0.959473] pci 0000:00:07.0: bridge 32bit mmio: [0xd8000000-0xdbffffff]
[    0.959477] pci 0000:00:07.0: bridge 64bit mmio pref: [0xb0000000-0xbfffffff]
[    0.959496] pci 0000:00:09.0: bridge io port: [0xc000-0xcfff]
[    0.959498] pci 0000:00:09.0: bridge 32bit mmio: [0xf3e00000-0xf3efffff]
[    0.959502] pci 0000:00:09.0: bridge 64bit mmio pref: [0xf3500000-0xf35fffff]
[    0.959591] pci 0000:05:00.0: reg 24 32bit mmio: [0xf3dfe000-0xf3dfffff]
[    0.959612] pci 0000:05:00.0: PME# supported from D3hot
[    0.959619] pci 0000:05:00.0: PME# disabled
[    0.959669] pci 0000:05:00.1: reg 10 io port: [0x7f00-0x7f07]
[    0.959680] pci 0000:05:00.1: reg 14 io port: [0x7e00-0x7e03]
[    0.959691] pci 0000:05:00.1: reg 18 io port: [0x7d00-0x7d07]
[    0.959701] pci 0000:05:00.1: reg 1c io port: [0x7c00-0x7c03]
[    0.959712] pci 0000:05:00.1: reg 20 io port: [0x7b00-0x7b0f]
[    0.959782] pci 0000:00:1c.0: bridge io port: [0x7000-0x7fff]
[    0.959789] pci 0000:00:1c.0: bridge 32bit mmio: [0xf3d00000-0xf3dfffff]
[    0.959798] pci 0000:00:1c.0: bridge 64bit mmio pref: [0xf3c00000-0xf3cfffff]
[    0.959886] pci 0000:06:00.0: reg 24 32bit mmio: [0xf3bfe000-0xf3bfffff]
[    0.959907] pci 0000:06:00.0: PME# supported from D3hot
[    0.959914] pci 0000:06:00.0: PME# disabled
[    0.959961] pci 0000:06:00.1: reg 10 io port: [0x6f00-0x6f07]
[    0.959972] pci 0000:06:00.1: reg 14 io port: [0x6e00-0x6e03]
[    0.959982] pci 0000:06:00.1: reg 18 io port: [0x6d00-0x6d07]
[    0.960009] pci 0000:06:00.1: reg 1c io port: [0x6c00-0x6c03]
[    0.960020] pci 0000:06:00.1: reg 20 io port: [0x6b00-0x6b0f]
[    0.960090] pci 0000:00:1c.1: bridge io port: [0x6000-0x6fff]
[    0.960096] pci 0000:00:1c.1: bridge 32bit mmio: [0xf3b00000-0xf3bfffff]
[    0.960105] pci 0000:00:1c.1: bridge 64bit mmio pref: [0xf3a00000-0xf3afffff]
[    0.960149] pci 0000:07:00.0: reg 10 io port: [0x5e00-0x5eff]
[    0.960171] pci 0000:07:00.0: reg 18 64bit mmio: [0xf39ff000-0xf39fffff]
[    0.960186] pci 0000:07:00.0: reg 20 64bit mmio: [0xf38f0000-0xf38fffff]
[    0.960196] pci 0000:07:00.0: reg 30 32bit mmio: [0xf39c0000-0xf39dffff]
[    0.960210] pci 0000:07:00.0: supports D1 D2
[    0.960211] pci 0000:07:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.960218] pci 0000:07:00.0: PME# disabled
[    0.960267] pci 0000:00:1c.2: bridge io port: [0x5000-0x5fff]
[    0.960274] pci 0000:00:1c.2: bridge 32bit mmio: [0xf3900000-0xf39fffff]
[    0.960282] pci 0000:00:1c.2: bridge 64bit mmio pref: [0xf3800000-0xf38fffff]
[    0.960330] pci 0000:08:00.0: reg 10 io port: [0xde00-0xdeff]
[    0.960351] pci 0000:08:00.0: reg 18 64bit mmio: [0xf37ff000-0xf37fffff]
[    0.960367] pci 0000:08:00.0: reg 20 64bit mmio: [0xf36f0000-0xf36fffff]
[    0.960377] pci 0000:08:00.0: reg 30 32bit mmio: [0xf37c0000-0xf37dffff]
[    0.960390] pci 0000:08:00.0: supports D1 D2
[    0.960391] pci 0000:08:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.960398] pci 0000:08:00.0: PME# disabled
[    0.960447] pci 0000:00:1c.4: bridge io port: [0xd000-0xdfff]
[    0.960454] pci 0000:00:1c.4: bridge 32bit mmio: [0xf3700000-0xf37fffff]
[    0.960462] pci 0000:00:1c.4: bridge 64bit mmio pref: [0xf3600000-0xf36fffff]
[    0.960502] pci 0000:09:03.0: reg 10 32bit mmio: [0xf34ff000-0xf34ff7ff]
[    0.960512] pci 0000:09:03.0: reg 14 32bit mmio: [0xf34f8000-0xf34fbfff]
[    0.960546] pci 0000:09:03.0: supports D1 D2
[    0.960547] pci 0000:09:03.0: PME# supported from D0 D1 D2 D3hot
[    0.960554] pci 0000:09:03.0: PME# disabled
[    0.960594] pci 0000:00:1e.0: transparent bridge
[    0.960601] pci 0000:00:1e.0: bridge io port: [0x9000-0x9fff]
[    0.960608] pci 0000:00:1e.0: bridge 32bit mmio: [0xf3400000-0xf34fffff]
[    0.960616] pci 0000:00:1e.0: bridge 64bit mmio pref: [0xf3300000-0xf33fffff]
[    0.960654] bus 00 -> node 0
[    0.960659] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.961013] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.MRP1._PRT]
[    0.961116] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.MRP3._PRT]
[    0.961222] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.MRP7._PRT]
[    0.961323] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.MRP9._PRT]
[    0.961430] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEX0._PRT]
[    0.961523] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEX1._PRT]
[    0.961616] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEX2._PRT]
[    0.961706] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEX4._PRT]
[    0.961795] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.HUB0._PRT]
[    0.986076] ACPI: PCI Interrupt Link [LNKA] (IRQs *5 9 10 11 12 14 15)
[    0.986196] ACPI: PCI Interrupt Link [LNKB] (IRQs 5 9 *10 11 12 14 15)
[    0.986320] ACPI: PCI Interrupt Link [LNKC] (IRQs 5 *9 10 11 12 14 15)
[    0.986439] ACPI: PCI Interrupt Link [LNKD] (IRQs 5 9 10 *11 12 14 15)
[    0.986559] ACPI: PCI Interrupt Link [LNKE] (IRQs 5 9 10 11 12 14 15) *0, disabled.
[    0.986678] ACPI: PCI Interrupt Link [LNKF] (IRQs *5 9 10 11 12 14 15)
[    0.986799] ACPI: PCI Interrupt Link [LNK0] (IRQs 5 9 10 *11 12 14 15)
[    0.986919] ACPI: PCI Interrupt Link [LNK1] (IRQs 5 9 *10 11 12 14 15)
[    0.987103] ACPI: WMI: Mapper loaded
[    0.987130] SCSI subsystem initialized
[    0.987130] libata version 3.00 loaded.
[    0.987130] usbcore: registered new interface driver usbfs
[    0.987130] usbcore: registered new interface driver hub
[    0.987130] usbcore: registered new device driver usb
[    0.987130] PCI: Using ACPI for IRQ routing
[    1.000009] Bluetooth: Core ver 2.13
[    1.000017] NET: Registered protocol family 31
[    1.000017] Bluetooth: HCI device and connection manager initialized
[    1.000017] Bluetooth: HCI socket layer initialized
[    1.000017] NET: Registered protocol family 8
[    1.000017] NET: Registered protocol family 20
[    1.000021] NetLabel: Initializing
[    1.000021] NetLabel:  domain hash size = 128
[    1.000022] NetLabel:  protocols = UNLABELED CIPSOv4
[    1.000029] NetLabel:  unlabeled traffic allowed by default
[    1.000080] AppArmor: AppArmor Filesystem Enabled
[    1.012008] pnp: PnP ACPI init
[    1.012013] ACPI: bus type pnp registered
[    1.014402] pnp: PnP ACPI: found 12 devices
[    1.014403] ACPI: ACPI bus type pnp unregistered
[    1.014408] system 00:01: ioport range 0x4d0-0x4d1 has been reserved
[    1.014410] system 00:01: ioport range 0x800-0x805 has been reserved
[    1.014411] system 00:01: ioport range 0x880-0x88f has been reserved
[    1.014415] system 00:08: ioport range 0x400-0x4bf has been reserved
[    1.014418] system 00:0a: iomem range 0xe0000000-0xefffffff has been reserved
[    1.014421] system 00:0b: iomem range 0xf0000-0xfffff could not be reserved
[    1.014422] system 00:0b: iomem range 0x9f800000-0x9fffffff has been reserved
[    1.014423] system 00:0b: iomem range 0x9f790000-0x9f7fffff could not be reserved
[    1.014425] system 00:0b: iomem range 0x0-0x9ffff could not be reserved
[    1.014426] system 00:0b: iomem range 0x100000-0x9f78ffff could not be reserved
[    1.014427] system 00:0b: iomem range 0xfec00000-0xfec00fff has been reserved
[    1.014429] system 00:0b: iomem range 0xfed13000-0xfed1ffff has been reserved
[    1.014430] system 00:0b: iomem range 0xfed20000-0xfed9ffff has been reserved
[    1.014432] system 00:0b: iomem range 0xfee00000-0xfee00fff has been reserved
[    1.014433] system 00:0b: iomem range 0xffb00000-0xffb7ffff has been reserved
[    1.014434] system 00:0b: iomem range 0xfff00000-0xffffffff has been reserved
[    1.014435] system 00:0b: iomem range 0xe0000-0xeffff has been reserved
[    1.019069] pci 0000:00:01.0: PCI bridge, secondary bus 0000:01
[    1.019071] pci 0000:00:01.0:   IO window: 0xb000-0xbfff
[    1.019074] pci 0000:00:01.0:   MEM window: 0xf3200000-0xf32fffff
[    1.019077] pci 0000:00:01.0:   PREFETCH window: 0x000000f3100000-0x000000f31fffff
[    1.019081] pci 0000:00:03.0: PCI bridge, secondary bus 0000:02
[    1.019083] pci 0000:00:03.0:   IO window: 0xa000-0xafff
[    1.019086] pci 0000:00:03.0:   MEM window: 0xdc000000-0xdfffffff
[    1.019088] pci 0000:00:03.0:   PREFETCH window: 0x000000c0000000-0x000000cfffffff
[    1.019093] pci 0000:00:07.0: PCI bridge, secondary bus 0000:03
[    1.019094] pci 0000:00:07.0:   IO window: 0x8000-0x8fff
[    1.019097] pci 0000:00:07.0:   MEM window: 0xd8000000-0xdbffffff
[    1.019100] pci 0000:00:07.0:   PREFETCH window: 0x000000b0000000-0x000000bfffffff
[    1.019103] pci 0000:00:09.0: PCI bridge, secondary bus 0000:04
[    1.019105] pci 0000:00:09.0:   IO window: 0xc000-0xcfff
[    1.019108] pci 0000:00:09.0:   MEM window: 0xf3e00000-0xf3efffff
[    1.019110] pci 0000:00:09.0:   PREFETCH window: 0x000000f3500000-0x000000f35fffff
[    1.019114] pci 0000:00:1c.0: PCI bridge, secondary bus 0000:05
[    1.019120] pci 0000:00:1c.0:   IO window: 0x7000-0x7fff
[    1.019128] pci 0000:00:1c.0:   MEM window: 0xf3d00000-0xf3dfffff
[    1.019134] pci 0000:00:1c.0:   PREFETCH window: 0x000000f3c00000-0x000000f3cfffff
[    1.019142] pci 0000:00:1c.1: PCI bridge, secondary bus 0000:06
[    1.019148] pci 0000:00:1c.1:   IO window: 0x6000-0x6fff
[    1.019156] pci 0000:00:1c.1:   MEM window: 0xf3b00000-0xf3bfffff
[    1.019158] pci 0000:00:1c.1:   PREFETCH window: 0x000000f3a00000-0x000000f3afffff
[    1.019167] pci 0000:00:1c.2: PCI bridge, secondary bus 0000:07
[    1.019173] pci 0000:00:1c.2:   IO window: 0x5000-0x5fff
[    1.019180] pci 0000:00:1c.2:   MEM window: 0xf3900000-0xf39fffff
[    1.019187] pci 0000:00:1c.2:   PREFETCH window: 0x000000f3800000-0x000000f38fffff
[    1.019195] pci 0000:00:1c.4: PCI bridge, secondary bus 0000:08
[    1.019201] pci 0000:00:1c.4:   IO window: 0xd000-0xdfff
[    1.019208] pci 0000:00:1c.4:   MEM window: 0xf3700000-0xf37fffff
[    1.019215] pci 0000:00:1c.4:   PREFETCH window: 0x000000f3600000-0x000000f36fffff
[    1.019220] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:09
[    1.019225] pci 0000:00:1e.0:   IO window: 0x9000-0x9fff
[    1.019233] pci 0000:00:1e.0:   MEM window: 0xf3400000-0xf34fffff
[    1.019240] pci 0000:00:1e.0:   PREFETCH window: 0x000000f3300000-0x000000f33fffff
[    1.019254] pci 0000:00:01.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.019257] pci 0000:00:01.0: setting latency timer to 64
[    1.019261] pci 0000:00:03.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.019263] pci 0000:00:03.0: setting latency timer to 64
[    1.019267] pci 0000:00:07.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.019270] pci 0000:00:07.0: setting latency timer to 64
[    1.019274] pci 0000:00:09.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.019276] pci 0000:00:09.0: setting latency timer to 64
[    1.019285] pci 0000:00:1c.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.019292] pci 0000:00:1c.0: setting latency timer to 64
[    1.019302] pci 0000:00:1c.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    1.019307] pci 0000:00:1c.1: setting latency timer to 64
[    1.019317] pci 0000:00:1c.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    1.019319] pci 0000:00:1c.2: setting latency timer to 64
[    1.019328] pci 0000:00:1c.4: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.019335] pci 0000:00:1c.4: setting latency timer to 64
[    1.019344] pci 0000:00:1e.0: setting latency timer to 64
[    1.019350] bus: 00 index 0 io port: [0x00-0xffff]
[    1.019351] bus: 00 index 1 mmio: [0x000000-0xffffffffffffffff]
[    1.019352] bus: 01 index 0 io port: [0xb000-0xbfff]
[    1.019353] bus: 01 index 1 mmio: [0xf3200000-0xf32fffff]
[    1.019354] bus: 01 index 2 mmio: [0xf3100000-0xf31fffff]
[    1.019355] bus: 01 index 3 mmio: [0x0-0x0]
[    1.019356] bus: 02 index 0 io port: [0xa000-0xafff]
[    1.019357] bus: 02 index 1 mmio: [0xdc000000-0xdfffffff]
[    1.019358] bus: 02 index 2 mmio: [0xc0000000-0xcfffffff]
[    1.019359] bus: 02 index 3 mmio: [0x0-0x0]
[    1.019360] bus: 03 index 0 io port: [0x8000-0x8fff]
[    1.019361] bus: 03 index 1 mmio: [0xd8000000-0xdbffffff]
[    1.019362] bus: 03 index 2 mmio: [0xb0000000-0xbfffffff]
[    1.019363] bus: 03 index 3 mmio: [0x0-0x0]
[    1.019364] bus: 04 index 0 io port: [0xc000-0xcfff]
[    1.019365] bus: 04 index 1 mmio: [0xf3e00000-0xf3efffff]
[    1.019366] bus: 04 index 2 mmio: [0xf3500000-0xf35fffff]
[    1.019367] bus: 04 index 3 mmio: [0x0-0x0]
[    1.019368] bus: 05 index 0 io port: [0x7000-0x7fff]
[    1.019369] bus: 05 index 1 mmio: [0xf3d00000-0xf3dfffff]
[    1.019370] bus: 05 index 2 mmio: [0xf3c00000-0xf3cfffff]
[    1.019371] bus: 05 index 3 mmio: [0x0-0x0]
[    1.019372] bus: 06 index 0 io port: [0x6000-0x6fff]
[    1.019373] bus: 06 index 1 mmio: [0xf3b00000-0xf3bfffff]
[    1.019374] bus: 06 index 2 mmio: [0xf3a00000-0xf3afffff]
[    1.019375] bus: 06 index 3 mmio: [0x0-0x0]
[    1.019376] bus: 07 index 0 io port: [0x5000-0x5fff]
[    1.019377] bus: 07 index 1 mmio: [0xf3900000-0xf39fffff]
[    1.019378] bus: 07 index 2 mmio: [0xf3800000-0xf38fffff]
[    1.019378] bus: 07 index 3 mmio: [0x0-0x0]
[    1.019379] bus: 08 index 0 io port: [0xd000-0xdfff]
[    1.019380] bus: 08 index 1 mmio: [0xf3700000-0xf37fffff]
[    1.019381] bus: 08 index 2 mmio: [0xf3600000-0xf36fffff]
[    1.019382] bus: 08 index 3 mmio: [0x0-0x0]
[    1.019383] bus: 09 index 0 io port: [0x9000-0x9fff]
[    1.019384] bus: 09 index 1 mmio: [0xf3400000-0xf34fffff]
[    1.019385] bus: 09 index 2 mmio: [0xf3300000-0xf33fffff]
[    1.019386] bus: 09 index 3 io port: [0x00-0xffff]
[    1.019387] bus: 09 index 4 mmio: [0x000000-0xffffffffffffffff]
[    1.019393] NET: Registered protocol family 2
[    1.056037] IP route cache hash table entries: 262144 (order: 9, 2097152 bytes)
[    1.056316] TCP established hash table entries: 262144 (order: 10, 4194304 bytes)
[    1.056838] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[    1.057005] TCP: Hash tables configured (established 262144 bind 65536)
[    1.057007] TCP reno registered
[    1.068065] NET: Registered protocol family 1
[    1.068131] checking if image is initramfs... it is
[    1.516476] Switched to high resolution mode on CPU 3
[    1.516524] Switched to high resolution mode on CPU 1
[    1.516532] Switched to high resolution mode on CPU 6
[    1.516543] Switched to high resolution mode on CPU 2
[    1.516546] Switched to high resolution mode on CPU 7
[    1.516589] Switched to high resolution mode on CPU 4
[    1.516608] Switched to high resolution mode on CPU 5
[    1.520008] Switched to high resolution mode on CPU 0
[    1.553008] Freeing initrd memory: 7769k freed
[    1.554461] audit: initializing netlink socket (disabled)
[    1.554472] type=2000 audit(1250311794.552:1): initialized
[    1.560928] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    1.561723] VFS: Disk quotas dquot_6.5.1
[    1.561761] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    1.562105] fuse init (API version 7.10)
[    1.562151] msgmni has been set to 11734
[    1.562251] alg: No test for stdrng (krng)
[    1.562259] io scheduler noop registered
[    1.562260] io scheduler anticipatory registered
[    1.562261] io scheduler deadline registered
[    1.562285] io scheduler cfq registered (default)
[    1.562477] pci 0000:02:00.0: Boot video device
[    1.565527] pcieport-driver 0000:00:01.0: setting latency timer to 64
[    1.565558] pcieport-driver 0000:00:01.0: found MSI capability
[    1.565578] pcieport-driver 0000:00:01.0: irq 2303 for MSI/MSI-X
[    1.565585] pci_express 0000:00:01.0:pcie00: allocate port service
[    1.565593] pci_express 0000:00:01.0:pcie01: allocate port service
[    1.565636] pcieport-driver 0000:00:03.0: setting latency timer to 64
[    1.565667] pcieport-driver 0000:00:03.0: found MSI capability
[    1.565683] pcieport-driver 0000:00:03.0: irq 2302 for MSI/MSI-X
[    1.565691] pci_express 0000:00:03.0:pcie00: allocate port service
[    1.565697] pci_express 0000:00:03.0:pcie01: allocate port service
[    1.565737] pcieport-driver 0000:00:07.0: setting latency timer to 64
[    1.565779] pcieport-driver 0000:00:07.0: found MSI capability
[    1.565796] pcieport-driver 0000:00:07.0: irq 2301 for MSI/MSI-X
[    1.565803] pci_express 0000:00:07.0:pcie00: allocate port service
[    1.565810] pci_express 0000:00:07.0:pcie01: allocate port service
[    1.565850] pcieport-driver 0000:00:09.0: setting latency timer to 64
[    1.565879] pcieport-driver 0000:00:09.0: found MSI capability
[    1.565896] pcieport-driver 0000:00:09.0: irq 2300 for MSI/MSI-X
[    1.565903] pci_express 0000:00:09.0:pcie00: allocate port service
[    1.565909] pci_express 0000:00:09.0:pcie01: allocate port service
[    1.565950] pcieport-driver 0000:00:1c.0: setting latency timer to 64
[    1.565981] pcieport-driver 0000:00:1c.0: found MSI capability
[    1.566004] pcieport-driver 0000:00:1c.0: irq 2299 for MSI/MSI-X
[    1.566016] pci_express 0000:00:1c.0:pcie00: allocate port service
[    1.566024] pci_express 0000:00:1c.0:pcie02: allocate port service
[    1.566030] pci_express 0000:00:1c.0:pcie03: allocate port service
[    1.566075] pcieport-driver 0000:00:1c.1: setting latency timer to 64
[    1.566106] pcieport-driver 0000:00:1c.1: found MSI capability
[    1.566128] pcieport-driver 0000:00:1c.1: irq 2298 for MSI/MSI-X
[    1.566141] pci_express 0000:00:1c.1:pcie00: allocate port service
[    1.566147] pci_express 0000:00:1c.1:pcie02: allocate port service
[    1.566153] pci_express 0000:00:1c.1:pcie03: allocate port service
[    1.566201] pcieport-driver 0000:00:1c.2: setting latency timer to 64
[    1.566232] pcieport-driver 0000:00:1c.2: found MSI capability
[    1.566259] pcieport-driver 0000:00:1c.2: irq 2297 for MSI/MSI-X
[    1.566271] pci_express 0000:00:1c.2:pcie00: allocate port service
[    1.566279] pci_express 0000:00:1c.2:pcie02: allocate port service
[    1.566285] pci_express 0000:00:1c.2:pcie03: allocate port service
[    1.566335] pcieport-driver 0000:00:1c.4: setting latency timer to 64
[    1.566366] pcieport-driver 0000:00:1c.4: found MSI capability
[    1.566388] pcieport-driver 0000:00:1c.4: irq 2296 for MSI/MSI-X
[    1.566401] pci_express 0000:00:1c.4:pcie00: allocate port service
[    1.566407] pci_express 0000:00:1c.4:pcie02: allocate port service
[    1.566413] pci_express 0000:00:1c.4:pcie03: allocate port service
[    1.567927] aer 0000:00:01.0:pcie01: AER service couldn't init device: no _OSC support
[    1.569427] aer 0000:00:03.0:pcie01: AER service couldn't init device: no _OSC support
[    1.570907] aer 0000:00:07.0:pcie01: AER service couldn't init device: no _OSC support
[    1.572377] aer 0000:00:09.0:pcie01: AER service couldn't init device: no _OSC support
[    1.572384] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    1.572660] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    1.572740] input: Power Button (FF) as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input0
[    1.572742] ACPI: Power Button (FF) [PWRF]
[    1.572766] input: Power Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1
[    1.572767] ACPI: Power Button (CM) [PWRB]
[    1.572794] fan PNP0C0B:00: registered as cooling_device0
[    1.572797] ACPI: Fan [FAN] (on)
[    1.573221] processor ACPI_CPU:00: registered as cooling_device1
[    1.573431] processor ACPI_CPU:01: registered as cooling_device2
[    1.573637] processor ACPI_CPU:02: registered as cooling_device3
[    1.573859] processor ACPI_CPU:03: registered as cooling_device4
[    1.574069] processor ACPI_CPU:04: registered as cooling_device5
[    1.574276] processor ACPI_CPU:05: registered as cooling_device6
[    1.574483] processor ACPI_CPU:06: registered as cooling_device7
[    1.574691] processor ACPI_CPU:07: registered as cooling_device8
[    1.576816] thermal LNXTHERM:01: registered as thermal_zone0
[    1.577057] ACPI: Thermal Zone [THRM] (35 C)
[    1.601821] Linux agpgart interface v0.103
[    1.601826] Serial: 8250/16550 driver4 ports, IRQ sharing enabled
[    1.601911] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    1.602132] 00:06: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    1.602557] brd: module loaded
[    1.602727] loop: module loaded
[    1.602765] Fixed MDIO Bus: probed
[    1.602768] PPP generic driver version 2.4.2
[    1.602796] input: Macintosh mouse button emulation as /devices/virtual/input/input2
[    1.602811] Driver 'sd' needs updating - please use bus_type methods
[    1.602816] Driver 'sr' needs updating - please use bus_type methods
[    1.602841] ahci 0000:05:00.0: version 3.0
[    1.602853] ahci 0000:05:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.617784] ahci 0000:05:00.0: AHCI 0001.0000 32 slots 2 ports 3 Gbps 0x3 impl SATA mode
[    1.617786] ahci 0000:05:00.0: flags: 64bit ncq pm led clo pmp pio slum part 
[    1.617794] ahci 0000:05:00.0: setting latency timer to 64
[    1.617894] scsi0 : ahci
[    1.617940] scsi1 : ahci
[    1.617979] ata1: SATA max UDMA/133 abar m8192@0xf3dfe000 port 0xf3dfe100 irq 16
[    1.617985] ata2: SATA max UDMA/133 abar m8192@0xf3dfe000 port 0xf3dfe180 irq 16
[    1.936025] ata1: SATA link down (SStatus 0 SControl 300)
[    2.272025] ata2: SATA link down (SStatus 0 SControl 300)
[    2.288021] ahci 0000:06:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    2.304036] ahci 0000:06:00.0: AHCI 0001.0000 32 slots 2 ports 3 Gbps 0x3 impl SATA mode
[    2.304038] ahci 0000:06:00.0: flags: 64bit ncq pm led clo pmp pio slum part 
[    2.304046] ahci 0000:06:00.0: setting latency timer to 64
[    2.304140] scsi2 : ahci
[    2.304174] scsi3 : ahci
[    2.304215] ata3: SATA max UDMA/133 abar m8192@0xf3bfe000 port 0xf3bfe100 irq 17
[    2.304221] ata4: SATA max UDMA/133 abar m8192@0xf3bfe000 port 0xf3bfe180 irq 17
[    2.788020] ata3: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    2.789154] ata3.00: HPA unlocked: 488395055 -> 488397168, native 488397168
[    2.789156] ata3.00: ATA-7: WDC WD2500KS-00MJB0, 02.01C03, max UDMA/133
[    2.789157] ata3.00: 488397168 sectors, multi 0: LBA48 
[    2.789800] ata3.00: configured for UDMA/133
[    3.288019] ata4: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    3.289122] ata4.00: HPA unlocked: 488395055 -> 488397168, native 488397168
[    3.289124] ata4.00: ATA-7: WDC WD2500KS-00MJB0, 02.01C03, max UDMA/133
[    3.289125] ata4.00: 488397168 sectors, multi 0: LBA48 
[    3.289767] ata4.00: configured for UDMA/133
[    3.304068] scsi 2:0:0:0: Direct-Access     ATA      WDC WD2500KS-00M 02.0 PQ: 0 ANSI: 5
[    3.304120] sd 2:0:0:0: [sda] 488397168 512-byte hardware sectors: (250 GB/232 GiB)
[    3.304129] sd 2:0:0:0: [sda] Write Protect is off
[    3.304130] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    3.304143] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    3.304176] sd 2:0:0:0: [sda] 488397168 512-byte hardware sectors: (250 GB/232 GiB)
[    3.304184] sd 2:0:0:0: [sda] Write Protect is off
[    3.304185] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    3.304198] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    3.304199]  sda: sda1 sda2 < sda5 >
[    3.332602] sd 2:0:0:0: [sda] Attached SCSI disk
[    3.332628] sd 2:0:0:0: Attached scsi generic sg0 type 0
[    3.332673] scsi 3:0:0:0: Direct-Access     ATA      WDC WD2500KS-00M 02.0 PQ: 0 ANSI: 5
[    3.332719] sd 3:0:0:0: [sdb] 488397168 512-byte hardware sectors: (250 GB/232 GiB)
[    3.332727] sd 3:0:0:0: [sdb] Write Protect is off
[    3.332728] sd 3:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[    3.332741] sd 3:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    3.332772] sd 3:0:0:0: [sdb] 488397168 512-byte hardware sectors: (250 GB/232 GiB)
[    3.332779] sd 3:0:0:0: [sdb] Write Protect is off
[    3.332780] sd 3:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[    3.332793] sd 3:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    3.332794]  sdb: sdb1
[    3.338354] sd 3:0:0:0: [sdb] Attached SCSI disk
[    3.338376] sd 3:0:0:0: Attached scsi generic sg1 type 0
[    3.338403] ata_piix 0000:00:1f.2: version 2.12
[    3.338415] ata_piix 0000:00:1f.2: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    3.338419] ata_piix 0000:00:1f.2: MAP [ P0 P2 P1 P3 ]
[    3.338458] ata_piix 0000:00:1f.2: setting latency timer to 64
[    3.338507] scsi4 : ata_piix
[    3.338540] scsi5 : ata_piix
[    3.339132] ata5: SATA max UDMA/133 cmd 0xf900 ctl 0xf800 bmdma 0xf500 irq 19
[    3.339141] ata6: SATA max UDMA/133 cmd 0xf700 ctl 0xf600 bmdma 0xf508 irq 19
[    4.132060] ata5.00: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    4.132076] ata5.01: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    4.148228] ata5.00: ATAPI: TSSTcorp CDDVDW SH-S223Q, SB03, max UDMA/100
[    4.148244] ata5.01: ATAPI: TSSTcorp CDDVDW SH-S223Q, SB03, max UDMA/100
[    4.164237] ata5.00: configured for UDMA/100
[    4.180237] ata5.01: configured for UDMA/100
[    4.976060] ata6.00: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    4.976076] ata6.01: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    4.992228] ata6.00: ATAPI: TSSTcorp CDDVDW SH-S223Q, SB03, max UDMA/100
[    4.992243] ata6.01: ATAPI: TSSTcorp CDDVDW SH-S223Q, SB03, max UDMA/100
[    5.009234] ata6.00: configured for UDMA/100
[    5.024237] ata6.01: configured for UDMA/100
[    5.025510] scsi 4:0:0:0: CD-ROM            TSSTcorp CDDVDW SH-S223Q  SB03 PQ: 0 ANSI: 5
[    5.028495] sr0: scsi3-mmc drive: 125x/125x writer dvd-ram cd/rw xa/form2 cdda tray
[    5.028497] Uniform CD-ROM driver Revision: 3.20
[    5.028551] sr 4:0:0:0: Attached scsi CD-ROM sr0
[    5.028572] sr 4:0:0:0: Attached scsi generic sg2 type 5
[    5.029156] scsi 4:0:1:0: CD-ROM            TSSTcorp CDDVDW SH-S223Q  SB03 PQ: 0 ANSI: 5
[    5.032164] sr1: scsi3-mmc drive: 94x/94x writer dvd-ram cd/rw xa/form2 cdda tray
[    5.032198] sr 4:0:1:0: Attached scsi CD-ROM sr1
[    5.032219] sr 4:0:1:0: Attached scsi generic sg3 type 5
[    5.032839] scsi 5:0:0:0: CD-ROM            TSSTcorp CDDVDW SH-S223Q  SB03 PQ: 0 ANSI: 5
[    5.034046] ata6.00: exception Emask 0x10 SAct 0x0 SErr 0x400100 action 0x6
[    5.034149] ata6.00: SError: { UnrecovData Handshk }
[    5.034257] ata6.00: cmd a0/00:00:00:00:00/00:00:00:00:00/a0 tag 0
[    5.034258]          cdb 00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00
[    5.034258]          res 51/40:03:00:00:00/00:00:00:00:00/a0 Emask 0x10 (ATA bus error)
[    5.034579] ata6.00: status: { DRDY ERR }
[    5.034690] ata6.00: hard resetting link
[    5.352008] ata6.01: hard resetting link
[    5.828058] ata6.00: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    5.828074] ata6.01: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    5.860236] ata6.00: configured for UDMA/100
[    5.876237] ata6.01: configured for UDMA/100
[    5.876823] ata6: EH complete
[    5.877498] ata6.00: exception Emask 0x10 SAct 0x0 SErr 0x400100 action 0x6
[    5.877607] ata6.00: SError: { UnrecovData Handshk }
[    5.877711] ata6.00: cmd a0/00:00:00:00:00/00:00:00:00:00/a0 tag 0
[    5.877711]          cdb 00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00
[    5.877712]          res 51/20:03:00:00:00/00:00:00:00:00/a0 Emask 0x10 (ATA bus error)
[    5.878034] ata6.00: status: { DRDY ERR }
[    5.878138] ata6.00: hard resetting link
[    6.196011] ata6.01: hard resetting link
[    6.672061] ata6.00: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    6.672076] ata6.01: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    6.704233] ata6.00: configured for UDMA/100
[    6.720233] ata6.01: configured for UDMA/100
[    6.720721] ata6: EH complete
[    6.721400] ata6.00: exception Emask 0x10 SAct 0x0 SErr 0x400101 action 0x6
[    6.721510] ata6.00: SError: { RecovData UnrecovData Handshk }
[    6.721614] ata6.00: cmd a0/00:00:00:00:00/00:00:00:00:00/a0 tag 0
[    6.721615]          cdb 00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00
[    6.721615]          res 51/20:03:00:00:00/00:00:00:00:00/a0 Emask 0x10 (ATA bus error)
[    6.721939] ata6.00: status: { DRDY ERR }
[    6.722050] ata6.00: hard resetting link
[    7.040012] ata6.01: hard resetting link
[    7.516061] ata6.00: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    7.516076] ata6.01: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[   12.524161] ata6.00: qc timeout (cmd 0xa1)
[   12.524168] ata6.00: failed to IDENTIFY (I/O error, err_mask=0x4)
[   12.524170] ata6.00: revalidation failed (errno=-5)
[   12.524276] ata6.00: hard resetting link
[   12.844011] ata6.01: hard resetting link
[   13.320061] ata6.00: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[   13.320076] ata6.01: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[   13.352236] ata6.00: configured for UDMA/100
[   13.368237] ata6.01: configured for UDMA/100
[   13.368934] ata6: EH complete
[   13.369443] ata6.00: limiting SATA link speed to 1.5 Gbps
[   13.369450] ata6.00: exception Emask 0x10 SAct 0x0 SErr 0x400100 action 0x6
[   13.369573] ata6.00: SError: { UnrecovData Handshk }
[   13.369694] ata6.00: cmd a0/00:00:00:00:00/00:00:00:00:00/a0 tag 0
[   13.369694]          cdb 00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00
[   13.369695]          res 51/20:03:00:00:00/00:00:00:00:00/a0 Emask 0x10 (ATA bus error)
[   13.370069] ata6.00: status: { DRDY ERR }
[   13.370193] ata6.00: hard resetting link
[   13.688011] ata6.01: hard resetting link
[   14.164060] ata6.00: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
[   14.164075] ata6.01: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[   19.172164] ata6.00: qc timeout (cmd 0xa1)
[   19.172171] ata6.00: failed to IDENTIFY (I/O error, err_mask=0x4)
[   19.172172] ata6.00: revalidation failed (errno=-5)
[   19.172298] ata6.00: hard resetting link
[   19.492011] ata6.01: hard resetting link
[   19.968058] ata6.00: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
[   19.968074] ata6.01: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[   20.000237] ata6.00: configured for UDMA/100
[   20.016238] ata6.01: configured for UDMA/100
[   20.016905] ata6: EH complete
[   20.017357] ata6.00: exception Emask 0x10 SAct 0x0 SErr 0x400100 action 0x6
[   20.017480] ata6.00: SError: { UnrecovData Handshk }
[   20.017594] ata6.00: cmd a0/00:00:00:00:00/00:00:00:00:00/a0 tag 0
[   20.017595]          cdb 00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00
[   20.017595]          res 51/20:03:00:00:00/00:00:00:00:00/a0 Emask 0x10 (ATA bus error)
[   20.017970] ata6.00: status: { DRDY ERR }
[   20.018094] ata6.00: hard resetting link
[   20.336011] ata6.01: hard resetting link
[   20.812060] ata6.00: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
[   20.812076] ata6.01: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[   20.844233] ata6.00: configured for UDMA/100
[   20.860233] ata6.01: configured for UDMA/100
[   25.860017] ata6.00: qc timeout (cmd 0xa0)
[   25.860025] ata6.00: TEST_UNIT_READY failed (err_mask=0x4)
[   25.860033] ata6.00: hard resetting link
[   26.180011] ata6.01: hard resetting link
[   26.656060] ata6.00: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
[   26.656080] ata6.01: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[   26.688233] ata6.00: configured for UDMA/100
[   26.704233] ata6.01: configured for UDMA/100
[   31.704019] ata6.00: qc timeout (cmd 0xa0)
[   31.704026] ata6.00: TEST_UNIT_READY failed (err_mask=0x4)
[   31.704033] ata6.00: limiting speed to UDMA/100:PIO3
[   31.704041] ata6.00: hard resetting link
[   32.024012] ata6.01: hard resetting link
[   32.500060] ata6.00: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
[   32.500076] ata6.01: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[   37.524162] ata6.00: qc timeout (cmd 0xa1)
[   37.524170] ata6.00: failed to IDENTIFY (I/O error, err_mask=0x4)
[   37.524171] ata6.00: revalidation failed (errno=-5)
[   37.524290] ata6.00: disabled
[   37.524297] ata6.01: failed to set xfermode (err_mask=0x40)
[   37.524420] ata6.00: hard resetting link
[   37.844011] ata6.01: hard resetting link
[   38.320057] ata6.00: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
[   38.320073] ata6.01: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[   38.344237] ata6.01: configured for UDMA/100
[   38.344580] ata6: EH complete
[   38.344591] sr2: scsi3-mmc drive: 0x/0x caddy
[   38.344627] sr 5:0:0:0: Attached scsi CD-ROM sr2
[   38.344648] sr 5:0:0:0: Attached scsi generic sg4 type 5
[   38.345262] scsi 5:0:1:0: CD-ROM            TSSTcorp CDDVDW SH-S223Q  SB03 PQ: 0 ANSI: 5
[   38.350270] sr3: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
[   38.350305] sr 5:0:1:0: Attached scsi CD-ROM sr3
[   38.350326] sr 5:0:1:0: Attached scsi generic sg5 type 5
[   38.350338] ata_piix 0000:00:1f.5: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[   38.350345] ata_piix 0000:00:1f.5: MAP [ P0 -- P1 -- ]
[   38.350374] ata_piix 0000:00:1f.5: setting latency timer to 64
[   38.350416] scsi6 : ata_piix
[   38.350448] scsi7 : ata_piix
[   38.350891] ata7: SATA max UDMA/133 cmd 0xf200 ctl 0xf100 bmdma 0xee00 irq 19
[   38.350898] ata8: SATA max UDMA/133 cmd 0xf000 ctl 0xef00 bmdma 0xee08 irq 19
[   38.682613] ata7: SATA link down (SStatus 0 SControl 300)
[   39.014614] ata8: SATA link down (SStatus 0 SControl 300)
[   39.014821] pata_jmicron 0000:05:00.1: enabling device (0000 -> 0001)
[   39.014829] pata_jmicron 0000:05:00.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[   39.014849] pata_jmicron 0000:05:00.1: setting latency timer to 64
[   39.014902] scsi8 : pata_jmicron
[   39.014937] scsi9 : pata_jmicron
[   39.015315] ata9: PATA max UDMA/100 cmd 0x7f00 ctl 0x7e00 bmdma 0x7b00 irq 17
[   39.015317] ata10: PATA max UDMA/100 cmd 0x7d00 ctl 0x7c00 bmdma 0x7b08 irq 17
[   39.338645] pata_jmicron 0000:06:00.1: enabling device (0000 -> 0001)
[   39.338652] pata_jmicron 0000:06:00.1: PCI INT B -> GSI 18 (level, low) -> IRQ 18
[   39.338672] pata_jmicron 0000:06:00.1: setting latency timer to 64
[   39.338731] scsi10 : pata_jmicron
[   39.338763] scsi11 : pata_jmicron
[   39.339129] ata11: PATA max UDMA/100 cmd 0x6f00 ctl 0x6e00 bmdma 0x6b00 irq 18
[   39.339130] ata12: PATA max UDMA/100 cmd 0x6d00 ctl 0x6c00 bmdma 0x6b08 irq 18
[   39.662789] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[   39.662804] ehci_hcd 0000:00:1a.7: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[   39.662816] ehci_hcd 0000:00:1a.7: setting latency timer to 64
[   39.662822] ehci_hcd 0000:00:1a.7: EHCI Host Controller
[   39.662848] ehci_hcd 0000:00:1a.7: new USB bus registered, assigned bus number 1
[   39.666750] ehci_hcd 0000:00:1a.7: debug port 1
[   39.666757] ehci_hcd 0000:00:1a.7: cache line size of 32 is not supported
[   39.666761] ehci_hcd 0000:00:1a.7: irq 18, io mem 0xf3ffe000
[   39.680008] ehci_hcd 0000:00:1a.7: USB 2.0 started, EHCI 1.00
[   39.680043] usb usb1: configuration #1 chosen from 1 choice
[   39.680057] hub 1-0:1.0: USB hub found
[   39.680061] hub 1-0:1.0: 6 ports detected
[   39.680131] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[   39.680143] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[   39.680149] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[   39.680171] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 2
[   39.684051] ehci_hcd 0000:00:1d.7: debug port 1
[   39.684059] ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported
[   39.684070] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xf3ffd000
[   39.696008] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[   39.696050] usb usb2: configuration #1 chosen from 1 choice
[   39.696064] hub 2-0:1.0: USB hub found
[   39.696067] hub 2-0:1.0: 6 ports detected
[   39.696123] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[   39.696132] uhci_hcd: USB Universal Host Controller Interface driver
[   39.696146] uhci_hcd 0000:00:1a.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   39.696154] uhci_hcd 0000:00:1a.0: setting latency timer to 64
[   39.696160] uhci_hcd 0000:00:1a.0: UHCI Host Controller
[   39.696181] uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 3
[   39.696208] uhci_hcd 0000:00:1a.0: irq 16, io base 0x0000ff00
[   39.696254] usb usb3: configuration #1 chosen from 1 choice
[   39.696266] hub 3-0:1.0: USB hub found
[   39.696269] hub 3-0:1.0: 2 ports detected
[   39.696324] uhci_hcd 0000:00:1a.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[   39.696329] uhci_hcd 0000:00:1a.1: setting latency timer to 64
[   39.696335] uhci_hcd 0000:00:1a.1: UHCI Host Controller
[   39.696359] uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus number 4
[   39.696391] uhci_hcd 0000:00:1a.1: irq 21, io base 0x0000fe00
[   39.696435] usb usb4: configuration #1 chosen from 1 choice
[   39.696447] hub 4-0:1.0: USB hub found
[   39.696450] hub 4-0:1.0: 2 ports detected
[   39.696507] uhci_hcd 0000:00:1a.2: PCI INT D -> GSI 19 (level, low) -> IRQ 19
[   39.696515] uhci_hcd 0000:00:1a.2: setting latency timer to 64
[   39.696521] uhci_hcd 0000:00:1a.2: UHCI Host Controller
[   39.696543] uhci_hcd 0000:00:1a.2: new USB bus registered, assigned bus number 5
[   39.696569] uhci_hcd 0000:00:1a.2: irq 19, io base 0x0000fd00
[   39.696612] usb usb5: configuration #1 chosen from 1 choice
[   39.696625] hub 5-0:1.0: USB hub found
[   39.696628] hub 5-0:1.0: 2 ports detected
[   39.696682] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[   39.696690] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[   39.696696] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[   39.696716] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 6
[   39.696742] uhci_hcd 0000:00:1d.0: irq 23, io base 0x0000fc00
[   39.696786] usb usb6: configuration #1 chosen from 1 choice
[   39.696798] hub 6-0:1.0: USB hub found
[   39.696800] hub 6-0:1.0: 2 ports detected
[   39.696857] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[   39.696865] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[   39.696870] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[   39.696892] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 7
[   39.696915] uhci_hcd 0000:00:1d.1: irq 19, io base 0x0000fb00
[   39.696956] usb usb7: configuration #1 chosen from 1 choice
[   39.696968] hub 7-0:1.0: USB hub found
[   39.696971] hub 7-0:1.0: 2 ports detected
[   39.697024] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[   39.697031] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[   39.697037] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[   39.697058] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 8
[   39.697086] uhci_hcd 0000:00:1d.2: irq 18, io base 0x0000fa00
[   39.697131] usb usb8: configuration #1 chosen from 1 choice
[   39.697143] hub 8-0:1.0: USB hub found
[   39.697146] hub 8-0:1.0: 2 ports detected
[   39.697221] PNP: PS/2 Controller [PNP0303:PS2K] at 0x60,0x64 irq 1
[   39.697222] PNP: PS/2 appears to have AUX port disabled, if this is incorrect please boot with i8042.nopnp
[   39.697647] serio: i8042 KBD port at 0x60,0x64 irq 1
[   39.708518] mice: PS/2 mouse device common for all mice
[   39.744540] rtc_cmos 00:03: RTC can wake from S4
[   39.744557] rtc_cmos 00:03: rtc core: registered rtc_cmos as rtc0
[   39.744580] rtc0: alarms up to one month, 242 bytes nvram
[   39.744614] device-mapper: uevent: version 1.0.3
[   39.744660] device-mapper: ioctl: 4.14.0-ioctl (2008-04-23) initialised: dm-devel@redhat.com
[   39.744765] device-mapper: multipath: version 1.0.5 loaded
[   39.744767] device-mapper: multipath round-robin: version 1.0.0 loaded
[   39.744887] cpuidle: using governor ladder
[   39.744888] cpuidle: using governor menu
[   39.745144] TCP cubic registered
[   39.745186] NET: Registered protocol family 10
[   39.745428] lo: Disabled Privacy Extensions
[   39.745601] NET: Registered protocol family 17
[   39.745613] Bluetooth: L2CAP ver 2.11
[   39.745613] Bluetooth: L2CAP socket layer initialized
[   39.745615] Bluetooth: SCO (Voice Link) ver 0.6
[   39.745616] Bluetooth: SCO socket layer initialized
[   39.745631] Bluetooth: RFCOMM socket layer initialized
[   39.745634] Bluetooth: RFCOMM TTY layer initialized
[   39.745635] Bluetooth: RFCOMM ver 1.10
[   39.747435] registered taskstats version 1
[   39.747541]   Magic number: 5:348:818
[   39.747571] button PNP0C0C:00: hash matches
[   39.747599] rtc_cmos 00:03: setting system clock to 2009-08-15 04:50:33 UTC (1250311833)
[   39.747601] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[   39.747602] EDD information not available.
[   39.747624] Freeing unused kernel memory: 532k freed
[   39.747705] Write protecting the kernel read-only data: 6684k
[   39.868762] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[   39.868777] r8169 0000:07:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[   39.868796] r8169 0000:07:00.0: setting latency timer to 64
[   39.868875] r8169 0000:07:00.0: irq 2295 for MSI/MSI-X
[   39.869213] eth0: RTL8168c/8111c at 0xffffc20000068000, 00:1f:bc:01:10:08, XID 3c4000c0 IRQ 2295
[   39.871875] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[   39.871887] r8169 0000:08:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   39.871904] r8169 0000:08:00.0: setting latency timer to 64
[   39.871972] r8169 0000:08:00.0: irq 2294 for MSI/MSI-X
[   39.872420] eth1: RTL8168c/8111c at 0xffffc20000048000, 00:1f:bc:01:10:09, XID 3c4000c0 IRQ 2294
[   39.879608] ohci1394 0000:09:03.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[   39.879616] ohci1394 0000:09:03.0: setting latency timer to 64
[   39.929338] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[19]  MMIO=[f34ff000-f34ff7ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[   40.169747] PM: Starting manual resume from disk
[   40.169749] PM: Resume from partition 8:5
[   40.169750] PM: Checking hibernation image.
[   40.169854] PM: Resume from disk failed.
[   40.192008] usb 7-2: new low speed USB device using uhci_hcd and address 2
[   40.209086] kjournald starting.  Commit interval 5 seconds
[   40.209092] EXT3-fs: mounted filesystem with ordered data mode.
[   40.370022] usb 7-2: configuration #1 chosen from 1 choice
[   41.200081] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[696100006e566964]
[   44.905060] udev: starting version 141
[   45.732807] nvidia: module license 'NVIDIA' taints kernel.
[   45.983579] nvidia 0000:02:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   45.983584] nvidia 0000:02:00.0: setting latency timer to 64
[   45.983726] nvidia 0000:03:00.0: enabling device (0000 -> 0003)
[   45.983729] nvidia 0000:03:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   45.983733] nvidia 0000:03:00.0: setting latency timer to 64
[   45.983817] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  185.18.14  Wed May 27 01:23:47 PDT 2009
[   45.989781] iTCO_vendor_support: vendor-support=0
[   45.998846] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.05
[   45.998962] iTCO_wdt: failed to reset NO_REBOOT flag, reboot disabled by hardware
[   45.998974] iTCO_wdt: No card detected
[   46.026466] usbcore: registered new interface driver hiddev
[   46.026694] usbcore: registered new interface driver usbhid
[   46.026713] usbhid: v2.6:USB HID core driver
[   46.027553] input: PC Speaker as /devices/platform/pcspkr/input/input3
[   46.069326] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:1d.1/usb7/7-2/7-2:1.0/input/input4
[   46.096544] logitech 0003:046D:C517.0001: input,hidraw0: USB HID v1.10 Keyboard [Logitech USB Receiver] on usb-0000:00:1d.1-2/input0
[   46.125176] logitech 0003:046D:C517.0002: fixing up Logitech keyboard report descriptor
[   46.125537] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:1d.1/usb7/7-2/7-2:1.1/input/input5
[   46.172547] logitech 0003:046D:C517.0002: input,hiddev96,hidraw1: USB HID v1.10 Mouse [Logitech USB Receiver] on usb-0000:00:1d.1-2/input1
[   46.187682] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[   46.187737] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   46.218599] hda_codec: Unknown model for ALC883, trying auto-probe from BIOS...
[   57.934961] lp: driver loaded but no devices found
[   57.982025] Adding 9936160k swap on /dev/sda5.  Priority:-1 extents:1 across:9936160k
[   58.504960] EXT3 FS on sda1, internal journal
[   59.392515] type=1505 audit(1250311853.141:2): operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" name2="default" pid=2451
[   59.416806] type=1505 audit(1250311853.165:3): operation="profile_load" name="/sbin/dhclient-script" name2="default" pid=2455
[   59.416854] type=1505 audit(1250311853.165:4): operation="profile_load" name="/sbin/dhclient3" name2="default" pid=2455
[   59.416876] type=1505 audit(1250311853.165:5): operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" name2="default" pid=2455
[   59.416896] type=1505 audit(1250311853.165:6): operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" name2="default" pid=2455
[   59.481557] type=1505 audit(1250311853.233:7): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=2460
[   59.481630] type=1505 audit(1250311853.233:8): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=2460
[   59.495521] type=1505 audit(1250311853.245:9): operation="profile_load" name="/usr/sbin/tcpdump" name2="default" pid=2464
[   61.603266] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   61.603268] Bluetooth: BNEP filters: protocol multicast
[   61.609795] Bridge firewalling registered
[   63.203943] ppdev: user-space parallel port driver

```

---

