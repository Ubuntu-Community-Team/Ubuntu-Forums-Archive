---
title: "Second drive (NTFS) will unmount at will"
date: 2010-09-14
forum: General Help
---

### Post by Elzigzag on 2010-09-14
First of all, I'm a Desktop user and by Desktop I mean GUI-dependent.
I installed Ubuntu 10.04 LTS on my home desktop and everything seemed to be fine.
Suddenly, may be two to three weeks ago, my second drive (inherited from previous OS so it's NTFS) began unmounting at will. From example I was listening to music stored there and a pop-up would tell that it has no access to the file/resource or something like that.
I'm providing my **fstab** (the rebel drive is sdb) and a** dmesg before** the event and **dmesg after** the event. If you compare the dmesg's at the end something happens.
I don't understand its content but I just want to know if someone can help me diagnosing whether it's a hardware issue or system settings.
In spite of its being unmounted somehow via Terminal I have access to the unfortunate drive. (Rather weird, uh?)
Usually, after restarting, the driver would mount... or not.


**fstab**[INDENT] ```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc    /proc    proc    nodev,noexec,nosuid    0    0
#Entry for /dev/sda1 :
UUID=40a5cde7-cae0-428f-a87d-f7454427b8b2    /    ext4    errors=remount-ro    0    1
#Entry for /dev/sda2 :
UUID=2ceff633-b089-4a7b-914f-22d158dc2cd4    /home    ext4    defaults    0    2
#Entry for /dev/sdb1 :
UUID=74D807B1D8077122    /windows    ntfs-3g    defaults,locale=es_AR.utf8    0    0
#Entry for /dev/sda5 :
UUID=2a297422-abe0-443e-bcac-0d764809d585    none    swap    sw    0    0
/dev/fd0    /media/floppy0    auto    rw,user,noauto,exec,utf8    0    0

```[/INDENT]**dmesg BEFORE unmounting**[INDENT]```
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.32-24-generic (buildd@palmer) (gcc version 4.4.3 (Ubuntu 4.4.3-4ubuntu5) ) #42-Ubuntu SMP Fri Aug 20 14:24:04 UTC 2010 (Ubuntu 2.6.32-24.42-generic 2.6.32.15+drm33.5)
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
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e6000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000005ef30000 (usable)
[    0.000000]  BIOS-e820: 000000005ef30000 - 000000005ef40000 (ACPI data)
[    0.000000]  BIOS-e820: 000000005ef40000 - 000000005eff0000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000005eff0000 - 000000005f000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fecf0000 - 00000000fecf1000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed20000 - 00000000feda0000 (reserved)
[    0.000000] DMI 2.3 present.
[    0.000000] last_pfn = 0x5ef30 max_arch_pfn = 0x100000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-EFFFF uncachable
[    0.000000]   F0000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000 mask FC0000000 write-back
[    0.000000]   1 base 040000000 mask FE0000000 write-back
[    0.000000]   2 disabled
[    0.000000]   3 disabled
[    0.000000]   4 disabled
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] e820 update range: 0000000000002000 - 0000000000006000 (usable) ==> (reserved)
[    0.000000] Scanning 1 areas for low memory corruption
[    0.000000] modified physical RAM map:
[    0.000000]  modified: 0000000000000000 - 0000000000002000 (usable)
[    0.000000]  modified: 0000000000002000 - 0000000000006000 (reserved)
[    0.000000]  modified: 0000000000006000 - 000000000009fc00 (usable)
[    0.000000]  modified: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  modified: 00000000000e6000 - 0000000000100000 (reserved)
[    0.000000]  modified: 0000000000100000 - 000000005ef30000 (usable)
[    0.000000]  modified: 000000005ef30000 - 000000005ef40000 (ACPI data)
[    0.000000]  modified: 000000005ef40000 - 000000005eff0000 (ACPI NVS)
[    0.000000]  modified: 000000005eff0000 - 000000005f000000 (reserved)
[    0.000000]  modified: 00000000fecf0000 - 00000000fecf1000 (reserved)
[    0.000000]  modified: 00000000fed20000 - 00000000feda0000 (reserved)
[    0.000000] initial memory mapped : 0 - 00c00000
[    0.000000] init_memory_mapping: 0000000000000000-00000000377fe000
[    0.000000] Using x86 segment limits to approximate NX protection
[    0.000000]  0000000000 - 0000400000 page 4k
[    0.000000]  0000400000 - 0037400000 page 2M
[    0.000000]  0037400000 - 00377fe000 page 4k
[    0.000000] kernel direct mapping tables up to 377fe000 @ 7000-c000
[    0.000000] RAMDISK: 37857000 - 37fefe09
[    0.000000] Allocated new RAMDISK: 008e2000 - 0107ae09
[    0.000000] Move RAMDISK from 0000000037857000 - 0000000037fefe08 to 008e2000 - 0107ae08
[    0.000000] ACPI: RSDP 000f58f0 00014 (v00 ACPIAM)
[    0.000000] ACPI: RSDT 5ef30000 00030 (v01 INTEL  D865GBF  20030423 MSFT 00000097)
[    0.000000] ACPI: FACP 5ef30200 00081 (v02 INTEL  D865GBF  20030423 MSFT 00000097)
[    0.000000] ACPI: DSDT 5ef30370 04154 (v01 INTEL  D865GBF  00000001 MSFT 0100000D)
[    0.000000] ACPI: FACS 5ef40000 00040
[    0.000000] ACPI: APIC 5ef30300 00068 (v01 INTEL  D865GBF  20030423 MSFT 00000097)
[    0.000000] ACPI: WDDT 5ef35244 00040 (v01 INTEL  OEMWDDT  00000001 MSFT 0100000D)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] 631MB HIGHMEM available.
[    0.000000] 887MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 377fe000
[    0.000000]   low ram: 0 - 377fe000
[    0.000000]   node 0 low ram: 00000000 - 377fe000
[    0.000000]   node 0 bootmap 00008000 - 0000ef00
[    0.000000] (9 early reservations) ==> bootmem [0000000000 - 00377fe000]
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
[    0.000000]   #1 [0000001000 - 0000002000]    EX TRAMPOLINE ==> [0000001000 - 0000002000]
[    0.000000]   #2 [0000006000 - 0000007000]       TRAMPOLINE ==> [0000006000 - 0000007000]
[    0.000000]   #3 [0000100000 - 00008ddeb8]    TEXT DATA BSS ==> [0000100000 - 00008ddeb8]
[    0.000000]   #4 [000009fc00 - 0000100000]    BIOS reserved ==> [000009fc00 - 0000100000]
[    0.000000]   #5 [00008de000 - 00008e111b]              BRK ==> [00008de000 - 00008e111b]
[    0.000000]   #6 [0000007000 - 0000008000]          PGTABLE ==> [0000007000 - 0000008000]
[    0.000000]   #7 [00008e2000 - 000107ae09]      NEW RAMDISK ==> [00008e2000 - 000107ae09]
[    0.000000]   #8 [0000008000 - 000000f000]          BOOTMAP ==> [0000008000 - 000000f000]
[    0.000000] found SMP MP-table at [c00ff780] ff780
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000000 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x000377fe
[    0.000000]   HighMem  0x000377fe -> 0x0005ef30
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[3] active PFN ranges
[    0.000000]     0: 0x00000000 -> 0x00000002
[    0.000000]     0: 0x00000006 -> 0x0000009f
[    0.000000]     0: 0x00000100 -> 0x0005ef30
[    0.000000] On node 0 totalpages: 388811
[    0.000000] free_area_init_node: node 0, pgdat c079a780, node_mem_map c107c000
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3963 pages, LIFO batch:0
[    0.000000]   Normal zone: 1744 pages used for memmap
[    0.000000]   Normal zone: 221486 pages, LIFO batch:31
[    0.000000]   HighMem zone: 1263 pages used for memmap
[    0.000000]   HighMem zone: 160323 pages, LIFO batch:31
[    0.000000] Using APIC driver default
[    0.000000] ACPI: PM-Timer IO Port: 0x408
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] dfl dfl lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x02] dfl dfl lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] SMP: Allowing 2 CPUs, 0 hotplug CPUs
[    0.000000] nr_irqs_gsi: 24
[    0.000000] PM: Registered nosave memory: 0000000000002000 - 0000000000006000
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e6000
[    0.000000] PM: Registered nosave memory: 00000000000e6000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 5f000000 (gap: 5f000000:9fcf0000)
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:2 nr_node_ids:1
[    0.000000] PERCPU: Embedded 14 pages/cpu @c2000000 s36056 r0 d21288 u2097152
[    0.000000] pcpu-alloc: s36056 r0 d21288 u2097152 alloc=1*4194304
[    0.000000] pcpu-alloc: [0] 0 1 
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 385772
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.32-24-generic root=UUID=40a5cde7-cae0-428f-a87d-f7454427b8b2 ro quiet splash
[    0.000000] PID hash table entries: 4096 (order: 2, 16384 bytes)
[    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] allocated 7778240 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] Initializing HighMem for node 0 (000377fe:0005ef30)
[    0.000000] Memory: 1517680k/1555648k available (4679k kernel code, 36576k reserved, 2124k data, 660k init, 646344k highmem)
[    0.000000] virtual kernel memory layout:
[    0.000000]     fixmap  : 0xfff1d000 - 0xfffff000   ( 904 kB)
[    0.000000]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[    0.000000]     vmalloc : 0xf7ffe000 - 0xff7fe000   ( 120 MB)
[    0.000000]     lowmem  : 0xc0000000 - 0xf77fe000   ( 887 MB)
[    0.000000]       .init : 0xc07a5000 - 0xc084a000   ( 660 kB)
[    0.000000]       .data : 0xc0591e33 - 0xc07a4e88   (2124 kB)
[    0.000000]       .text : 0xc0100000 - 0xc0591e33   (4679 kB)
[    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.000000] SLUB: Genslabs=13, HWalign=128, Order=0-3, MinObjects=0, CPUs=2, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000] NR_IRQS:2304 nr_irqs:424
[    0.000000] Console: colour VGA+ 80x25
[    0.000000] console [tty0] enabled
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 2394.137 MHz processor.
[    0.004010] Calibrating delay loop (skipped), value calculated using timer frequency.. 4788.27 BogoMIPS (lpj=9576548)
[    0.004041] Security Framework initialized
[    0.004081] AppArmor: AppArmor initialized
[    0.004092] Mount-cache hash table entries: 512
[    0.004329] Initializing cgroup subsys ns
[    0.004337] Initializing cgroup subsys cpuacct
[    0.004344] Initializing cgroup subsys memory
[    0.004357] Initializing cgroup subsys devices
[    0.004361] Initializing cgroup subsys freezer
[    0.004365] Initializing cgroup subsys net_cls
[    0.004402] CPU: Trace cache: 12K uops, L1 D cache: 8K
[    0.004407] CPU: L2 cache: 512K
[    0.004411] CPU: Physical Processor ID: 0
[    0.004414] CPU: Processor Core ID: 0
[    0.004420] mce: CPU supports 4 MCE banks
[    0.004438] CPU0: Thermal monitoring enabled (TM1)
[    0.004456] Performance Events: no PMU driver, software events only.
[    0.004467] Checking 'hlt' instruction... OK.
[    0.024200] ACPI: Core revision 20090903
[    0.034763] ftrace: converting mcount calls to 0f 1f 44 00 00
[    0.034773] ftrace: allocating 21780 entries in 43 pages
[    0.036145] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.036455] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.079183] CPU0: Intel(R) Pentium(R) 4 CPU 2.40GHz stepping 09
[    0.080001] Booting processor 1 APIC 0x1 ip 0x6000
[    0.008000] Initializing CPU#1
[    0.008000] CPU: Trace cache: 12K uops, L1 D cache: 8K
[    0.008000] CPU: L2 cache: 512K
[    0.008000] CPU: Physical Processor ID: 0
[    0.008000] CPU: Processor Core ID: 0
[    0.008000] CPU1: Thermal monitoring enabled (TM1)
[    0.164144] CPU1: Intel(R) Pentium(R) 4 CPU 2.40GHz stepping 09
[    0.164165] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
[    0.168038] Brought up 2 CPUs
[    0.168046] Total of 2 processors activated (9576.78 BogoMIPS).
[    0.168283] CPU0 attaching sched-domain:
[    0.168291]  domain 0: span 0-1 level SIBLING
[    0.168296]   groups: 0 (cpu_power = 589) 1 (cpu_power = 589)
[    0.168306]   domain 1: span 0-1 level MC
[    0.168311]    groups: 0-1 (cpu_power = 1178)
[    0.168322] CPU1 attaching sched-domain:
[    0.168326]  domain 0: span 0-1 level SIBLING
[    0.168330]   groups: 1 (cpu_power = 589) 0 (cpu_power = 589)
[    0.168340]   domain 1: span 0-1 level MC
[    0.168344]    groups: 0-1 (cpu_power = 1178)
[    0.168544] devtmpfs: initialized
[    0.168544] regulator: core version 0.5
[    0.168544] Time:  0:22:10  Date: 09/15/10
[    0.168544] NET: Registered protocol family 16
[    0.168544] Trying to unpack rootfs image as initramfs...
[    0.168544] EISA bus registered
[    0.168544] ACPI: bus type pci registered
[    0.170253] PCI: PCI BIOS revision 2.10 entry at 0xf0031, last bus=1
[    0.170259] PCI: Using configuration type 1 for base access
[    0.174612] bio: create slab <bio-0> at 0
[    0.176539] ACPI: EC: Look up EC in DSDT
[    0.180793] ACPI: Executed 2 blocks of module-level executable AML code
[    0.188966] ACPI: Interpreter enabled
[    0.188990] ACPI: (supports S0 S1 S4 S5)
[    0.189041] ACPI: Using IOAPIC for interrupt routing
[    0.201994] ACPI: Power Resource [URP1] (off)
[    0.202059] ACPI: Power Resource [FDDP] (off)
[    0.202122] ACPI: Power Resource [LPTP] (off)
[    0.202475] ACPI: No dock devices found.
[    0.202775] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.202870] pci 0000:00:00.0: Enabling MCH 'Overflow' Device
[    0.202888] pci 0000:00:00.0: reg 10 32bit mmio pref: [0xf8000000-0xfbffffff]
[    0.202988] pci 0000:00:02.0: reg 10 32bit mmio pref: [0xf0000000-0xf7ffffff]
[    0.203000] pci 0000:00:02.0: reg 14 32bit mmio: [0xffa80000-0xffafffff]
[    0.203011] pci 0000:00:02.0: reg 18 io port: [0xec00-0xec07]
[    0.203084] pci 0000:00:06.0: reg 10 32bit mmio: [0xfecf0000-0xfecf0fff]
[    0.203230] pci 0000:00:1d.0: reg 20 io port: [0xc800-0xc81f]
[    0.203307] pci 0000:00:1d.1: reg 20 io port: [0xcc00-0xcc1f]
[    0.203382] pci 0000:00:1d.2: reg 20 io port: [0xd000-0xd01f]
[    0.203456] pci 0000:00:1d.3: reg 20 io port: [0xd400-0xd41f]
[    0.203542] pci 0000:00:1d.7: reg 10 32bit mmio: [0xffa7fc00-0xffa7ffff]
[    0.203629] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
[    0.203640] pci 0000:00:1d.7: PME# disabled
[    0.203776] pci 0000:00:1f.0: Force enabled HPET at 0xfed00000
[    0.203790] pci 0000:00:1f.0: quirk: region 0400-047f claimed by ICH4 ACPI/GPIO/TCO
[    0.203798] pci 0000:00:1f.0: quirk: region 0500-053f claimed by ICH4 GPIO
[    0.203835] pci 0000:00:1f.1: reg 10 io port: [0x00-0x07]
[    0.203848] pci 0000:00:1f.1: reg 14 io port: [0x00-0x03]
[    0.203859] pci 0000:00:1f.1: reg 18 io port: [0x00-0x07]
[    0.203871] pci 0000:00:1f.1: reg 1c io port: [0x00-0x03]
[    0.203882] pci 0000:00:1f.1: reg 20 io port: [0xffa0-0xffaf]
[    0.203894] pci 0000:00:1f.1: reg 24 32bit mmio: [0x000000-0x0003ff]
[    0.203940] pci 0000:00:1f.2: reg 10 io port: [0xe800-0xe807]
[    0.203952] pci 0000:00:1f.2: reg 14 io port: [0xe400-0xe403]
[    0.203963] pci 0000:00:1f.2: reg 18 io port: [0xe000-0xe007]
[    0.203975] pci 0000:00:1f.2: reg 1c io port: [0xdc00-0xdc03]
[    0.204023] pci 0000:00:1f.2: reg 20 io port: [0xd800-0xd80f]
[    0.204098] pci 0000:00:1f.3: reg 20 io port: [0xc400-0xc41f]
[    0.204188] pci 0000:01:00.0: reg 10 io port: [0xbc00-0xbc3f]
[    0.204249] pci 0000:01:00.0: supports D2
[    0.204311] pci 0000:01:02.0: reg 10 32bit mmio: [0xff8ff000-0xff8fffff]
[    0.204336] pci 0000:01:02.0: reg 14 io port: [0xb800-0xb8ff]
[    0.204397] pci 0000:01:02.0: PME# supported from D3hot D3cold
[    0.204405] pci 0000:01:02.0: PME# disabled
[    0.204454] pci 0000:01:04.0: reg 10 io port: [0xb400-0xb4ff]
[    0.204466] pci 0000:01:04.0: reg 14 32bit mmio: [0xff8fec00-0xff8fefff]
[    0.204500] pci 0000:01:04.0: reg 30 32bit mmio pref: [0xff8c0000-0xff8dffff]
[    0.204527] pci 0000:01:04.0: supports D1 D2
[    0.204533] pci 0000:01:04.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.204541] pci 0000:01:04.0: PME# disabled
[    0.204595] pci 0000:00:1e.0: transparent bridge
[    0.204604] pci 0000:00:1e.0: bridge io port: [0xb000-0xbfff]
[    0.204612] pci 0000:00:1e.0: bridge 32bit mmio: [0xff800000-0xff8fffff]
[    0.204630] pci_bus 0000:00: on NUMA node 0
[    0.204648] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.204827] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P3._PRT]
[    0.210896] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)
[    0.211156] ACPI: PCI Interrupt Link [LNKB] (IRQs *3 4 5 6 7 9 10 11 12 14 15)
[    0.211443] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 9 *10 11 12 14 15)
[    0.211710] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 *5 6 7 9 10 11 12 14 15)
[    0.211973] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
[    0.212290] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 9 *10 11 12 14 15)
[    0.212548] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
[    0.212840] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 *9 10 11 12 14 15)
[    0.213134] vgaarb: device added: PCI:0000:00:02.0,decodes=io+mem,owns=io+mem,locks=none
[    0.213168] vgaarb: loaded
[    0.213467] SCSI subsystem initialized
[    0.213671] libata version 3.00 loaded.
[    0.213844] usbcore: registered new interface driver usbfs
[    0.213877] usbcore: registered new interface driver hub
[    0.213967] usbcore: registered new device driver usb
[    0.214364] ACPI: WMI: Mapper loaded
[    0.214370] PCI: Using ACPI for IRQ routing
[    0.214741] NetLabel: Initializing
[    0.214746] NetLabel:  domain hash size = 128
[    0.214751] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.214781] NetLabel:  unlabeled traffic allowed by default
[    0.214980] hpet clockevent registered
[    0.214987] HPET: 3 timers in total, 0 timers will be used for per-cpu timer
[    0.214997] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[    0.215010] hpet0: 3 comparators, 64-bit 14.318180 MHz counter
[    0.220074] Switching to clocksource tsc
[    0.225110] AppArmor: AppArmor Filesystem Enabled
[    0.225149] pnp: PnP ACPI init
[    0.225190] ACPI: bus type pnp registered
[    0.232132] pnp: PnP ACPI: found 14 devices
[    0.232140] ACPI: ACPI bus type pnp unregistered
[    0.232150] PnPBIOS: Disabled by ACPI PNP
[    0.232193] system 00:0a: ioport range 0x4d0-0x4d1 has been reserved
[    0.232210] system 00:0c: ioport range 0x400-0x47f has been reserved
[    0.232219] system 00:0c: ioport range 0x680-0x6ff has been reserved
[    0.232226] system 00:0c: ioport range 0x500-0x53f has been reserved
[    0.232236] system 00:0c: iomem range 0xfec00000-0xfec00fff could not be reserved
[    0.232244] system 00:0c: iomem range 0xfee00000-0xfee00fff has been reserved
[    0.232251] system 00:0c: iomem range 0xfed20000-0xfed9ffff has been reserved
[    0.232267] system 00:0d: iomem range 0x0-0x9ffff could not be reserved
[    0.232275] system 00:0d: iomem range 0xc0000-0xdffff could not be reserved
[    0.232283] system 00:0d: iomem range 0xe0000-0xfffff could not be reserved
[    0.232291] system 00:0d: iomem range 0x100000-0x5effffff could not be reserved
[    0.267350] pci 0000:01:04.0: BAR 6: address space collision on of device [0xff8c0000-0xff8dffff]
[    0.267395] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:01
[    0.267404] pci 0000:00:1e.0:   IO window: 0xb000-0xbfff
[    0.267414] pci 0000:00:1e.0:   MEM window: 0xff800000-0xff8fffff
[    0.267424] pci 0000:00:1e.0:   PREFETCH window: 0x60000000-0x600fffff
[    0.267451] pci 0000:00:1e.0: setting latency timer to 64
[    0.267461] pci_bus 0000:00: resource 0 io:  [0x00-0xffff]
[    0.267467] pci_bus 0000:00: resource 1 mem: [0x000000-0xffffffff]
[    0.267474] pci_bus 0000:01: resource 0 io:  [0xb000-0xbfff]
[    0.267480] pci_bus 0000:01: resource 1 mem: [0xff800000-0xff8fffff]
[    0.267486] pci_bus 0000:01: resource 2 pref mem [0x60000000-0x600fffff]
[    0.267493] pci_bus 0000:01: resource 3 io:  [0x00-0xffff]
[    0.267499] pci_bus 0000:01: resource 4 mem: [0x000000-0xffffffff]
[    0.267588] NET: Registered protocol family 2
[    0.267828] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.268746] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.270489] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.271431] TCP: Hash tables configured (established 131072 bind 65536)
[    0.271441] TCP reno registered
[    0.271841] NET: Registered protocol family 1
[    0.271894] pci 0000:00:02.0: Boot video device
[    0.272324] cpufreq-nforce2: No nForce2 chipset.
[    0.272402] Scanning for low memory corruption every 60 seconds
[    0.272683] audit: initializing netlink socket (disabled)
[    0.272707] type=2000 audit(1284510130.271:1): initialized
[    0.286053] highmem bounce pool size: 64 pages
[    0.286066] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    0.290071] VFS: Disk quotas dquot_6.5.2
[    0.290234] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.291886] fuse init (API version 7.13)
[    0.292121] msgmni has been set to 1703
[    0.292765] alg: No test for stdrng (krng)
[    0.292928] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.292940] io scheduler noop registered
[    0.292945] io scheduler anticipatory registered
[    0.292951] io scheduler deadline registered
[    0.293070] io scheduler cfq registered (default)
[    0.293351] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.293411] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.293679] input: Sleep Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0E:00/input/input0
[    0.293700] ACPI: Sleep Button [SLPB]
[    0.293828] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
[    0.293836] ACPI: Power Button [PWRF]
[    0.294314] processor LNXCPU:00: registered as cooling_device0
[    0.294504] processor LNXCPU:01: registered as cooling_device1
[    0.301939] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    0.302102] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.302857] 00:08: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.303140]   alloc irq_desc for 17 on node -1
[    0.303146]   alloc kstat_irqs on node -1
[    0.303161] serial 0000:01:02.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    0.304096] 0000:01:02.0: ttyS1 at I/O 0xb828 (irq = 17) is a 8250
[    0.304531] 0000:01:02.0: ttyS2 at I/O 0xb840 (irq = 17) is a 8250
[    0.304857] 0000:01:02.0: ttyS3 at I/O 0xb850 (irq = 17) is a 8250
[    0.304919] Couldn't register serial port 0000:01:02.0: -28
[    0.307458] isapnp: Scanning for PnP cards...
[    0.357039] brd: module loaded
[    0.358322] loop: module loaded
[    0.358603] input: Macintosh mouse button emulation as /devices/virtual/input/input2
[    0.358856] ata_piix 0000:00:1f.1: version 2.13
[    0.358883] ata_piix 0000:00:1f.1: enabling device (0005 -> 0007)
[    0.358902]   alloc irq_desc for 18 on node -1
[    0.358908]   alloc kstat_irqs on node -1
[    0.358925] ata_piix 0000:00:1f.1: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    0.359038] ata_piix 0000:00:1f.1: setting latency timer to 64
[    0.446480] scsi0 : ata_piix
[    0.487279] scsi1 : ata_piix
[    0.489469] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xffa0 irq 14
[    0.489475] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xffa8 irq 15
[    0.489533] ata_piix 0000:00:1f.2: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    0.489543] ata_piix 0000:00:1f.2: MAP [ P0 -- P1 -- ]
[    0.489630] ata_piix 0000:00:1f.2: setting latency timer to 64
[    0.489973] scsi2 : ata_piix
[    0.490126] scsi3 : ata_piix
[    0.492259] ata3: SATA max UDMA/133 cmd 0xe800 ctl 0xe400 bmdma 0xd800 irq 18
[    0.492268] ata4: SATA max UDMA/133 cmd 0xe000 ctl 0xdc00 bmdma 0xd808 irq 18
[    0.493353] Fixed MDIO Bus: probed
[    0.493460] PPP generic driver version 2.4.2
[    0.493602] tun: Universal TUN/TAP device driver, 1.6
[    0.493607] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.493831] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.493900]   alloc irq_desc for 23 on node -1
[    0.493907]   alloc kstat_irqs on node -1
[    0.493929] ehci_hcd 0000:00:1d.7: PCI INT D -> GSI 23 (level, low) -> IRQ 23
[    0.493970] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    0.493978] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    0.494066] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 1
[    0.494117] ehci_hcd 0000:00:1d.7: debug port 1
[    0.497998] ehci_hcd 0000:00:1d.7: cache line size of 128 is not supported
[    0.498085] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xffa7fc00
[    0.511581] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    0.511838] usb usb1: configuration #1 chosen from 1 choice
[    0.511911] hub 1-0:1.0: USB hub found
[    0.511930] hub 1-0:1.0: 8 ports detected
[    0.512075] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.512113] uhci_hcd: USB Universal Host Controller Interface driver
[    0.512206]   alloc irq_desc for 16 on node -1
[    0.512211]   alloc kstat_irqs on node -1
[    0.512225] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.512241] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    0.512248] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    0.512330] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    0.512376] uhci_hcd 0000:00:1d.0: irq 16, io base 0x0000c800
[    0.512567] usb usb2: configuration #1 chosen from 1 choice
[    0.512625] hub 2-0:1.0: USB hub found
[    0.512641] hub 2-0:1.0: 2 ports detected
[    0.512734]   alloc irq_desc for 19 on node -1
[    0.512738]   alloc kstat_irqs on node -1
[    0.512748] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    0.512759] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    0.512765] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    0.512847] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 3
[    0.512886] uhci_hcd 0000:00:1d.1: irq 19, io base 0x0000cc00
[    0.513080] usb usb3: configuration #1 chosen from 1 choice
[    0.513137] hub 3-0:1.0: USB hub found
[    0.513151] hub 3-0:1.0: 2 ports detected
[    0.513241] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.513252] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    0.513258] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    0.513325] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 4
[    0.513353] uhci_hcd 0000:00:1d.2: irq 18, io base 0x0000d000
[    0.513552] usb usb4: configuration #1 chosen from 1 choice
[    0.513608] hub 4-0:1.0: USB hub found
[    0.513629] hub 4-0:1.0: 2 ports detected
[    0.513718] uhci_hcd 0000:00:1d.3: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.513728] uhci_hcd 0000:00:1d.3: setting latency timer to 64
[    0.513734] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[    0.513805] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 5
[    0.513834] uhci_hcd 0000:00:1d.3: irq 16, io base 0x0000d400
[    0.514024] usb usb5: configuration #1 chosen from 1 choice
[    0.514082] hub 5-0:1.0: USB hub found
[    0.514099] hub 5-0:1.0: 2 ports detected
[    0.514311] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f03:PS2M] at 0x60,0x64 irq 1,12
[    0.524242] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.524269] serio: i8042 AUX port at 0x60,0x64 irq 12
[    0.524635] mice: PS/2 mouse device common for all mice
[    0.524870] rtc_cmos 00:02: RTC can wake from S4
[    0.524955] rtc_cmos 00:02: rtc core: registered rtc_cmos as rtc0
[    0.524987] rtc0: alarms up to one month, 114 bytes nvram, hpet irqs
[    0.525242] device-mapper: uevent: version 1.0.3
[    0.539419] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: dm-devel@redhat.com
[    0.544313] Freeing initrd memory: 7779k freed
[    0.557241] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input3
[    0.557664] device-mapper: multipath: version 1.1.0 loaded
[    0.557672] device-mapper: multipath round-robin: version 1.0.0 loaded
[    0.557983] EISA: Probing bus 0 at eisa.0
[    0.558033] EISA: Detected 0 cards.
[    0.558192] cpuidle: using governor ladder
[    0.558197] cpuidle: using governor menu
[    0.559221] TCP cubic registered
[    0.559494] NET: Registered protocol family 10
[    0.560595] lo: Disabled Privacy Extensions
[    0.561406] NET: Registered protocol family 17
[    0.561536] Using IPI No-Shortcut mode
[    0.561729] PM: Resume from disk failed.
[    0.561755] registered taskstats version 1
[    0.562103]   Magic number: 10:962:354
[    0.562112] input event0: hash matches
[    0.562239] rtc_cmos 00:02: setting system clock to 2010-09-15 00:22:10 UTC (1284510130)
[    0.562245] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.562249] EDD information not available.
[    0.651751] ata2.00: ATAPI: TSSTcorpCD/DVDW SH-S182D, SB03, max UDMA/33
[    0.659981] ata1.00: ATA-6: IC35L060AVV207-0, V22OA63A, max UDMA/100
[    0.659987] ata1.00: 120103200 sectors, multi 16: LBA48 
[    0.667703] ata2.00: configured for UDMA/33
[    0.669675] isapnp: No Plug & Play device found
[    0.680947] ata3.00: ATA-8: WDC WD1600AAJS-00WAA0, 58.01D58, max UDMA/133
[    0.680952] ata3.00: 312581808 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    0.683857] ata1.00: configured for UDMA/100
[    0.684043] scsi 0:0:0:0: Direct-Access     ATA      IC35L060AVV207-0 V22O PQ: 0 ANSI: 5
[    0.684298] sd 0:0:0:0: [sda] 120103200 512-byte logical blocks: (61.4 GB/57.2 GiB)
[    0.684377] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    0.684420] sd 0:0:0:0: [sda] Write Protect is off
[    0.684428] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    0.684491] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    0.684819]  sda:
[    0.692144] scsi 1:0:0:0: CD-ROM            TSSTcorp CD/DVDW SH-S182D SB03 PQ: 0 ANSI: 5
[    0.692339] ata3.00: configured for UDMA/133
[    0.694606]  sda1 sda2 sda3 <sr0: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
[    0.698941] Uniform CD-ROM driver Revision: 3.20
[    0.699126] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    0.699244] sr 1:0:0:0: Attached scsi generic sg1 type 5
[    0.699467] scsi 2:0:0:0: Direct-Access     ATA      WDC WD1600AAJS-0 58.0 PQ: 0 ANSI: 5
[    0.699702] sd 2:0:0:0: [sdb] 312581808 512-byte logical blocks: (160 GB/149 GiB)
[    0.699752] sd 2:0:0:0: Attached scsi generic sg2 type 0
[    0.699844] sd 2:0:0:0: [sdb] Write Protect is off
[    0.699852] sd 2:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[    0.699914] sd 2:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    0.700156]  sdb: sda5 >
[    0.722077]  sdb1
[    0.722612] sd 2:0:0:0: [sdb] Attached SCSI disk
[    0.722846] sd 0:0:0:0: [sda] Attached SCSI disk
[    0.722872] Freeing unused kernel memory: 660k freed
[    0.724003] Write protecting the kernel text: 4680k
[    0.724087] Write protecting the kernel read-only data: 1844k
[    0.761782] udev: starting version 151
[    1.082573] Floppy drive(s): fd0 is 1.44M
[    1.092810] Linux Tulip driver version 1.1.15 (Feb 27, 2007)
[    1.092910] tulip 0000:01:04.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    1.093530] tulip0:  MII transceiver #1 config 1000 status 786d advertising 05e1.
[    1.101545] FDC 0 is a post-1991 82077
[    1.106770] eth0: ADMtek Comet rev 17 at Port 0xb400, 00:e0:4c:03:7c:c0, IRQ 18.
[    1.355577] EXT4-fs (sda1): mounted filesystem with ordered data mode
[    9.275892] Adding 2433016k swap on /dev/sda5.  Priority:-1 extents:1 across:2433016k 
[    9.290114] udev: starting version 151
[    9.585361] Linux agpgart interface v0.103
[    9.591071] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[    9.673612] Intel 82802 RNG detected
[    9.852882] lp: driver loaded but no devices found
[    9.942724] [drm] Initialized drm 1.1.0 20060810
[    9.943530] parport_pc 00:09: reported by Plug and Play ACPI
[    9.943561] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE,EPP]
[    9.948200] psmouse serio1: ID: 10 00 64
[    9.954771] agpgart-intel 0000:00:00.0: Intel 865 Chipset
[    9.955136] agpgart-intel 0000:00:00.0: detected 16252K stolen memory
[    9.976671] agpgart-intel 0000:00:00.0: AGP aperture is 128M @ 0xf0000000
[   10.041605] lp0: using parport0 (interrupt-driven).
[   10.110996] ppdev: user-space parallel port driver
[   10.160813] i915 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   10.160830] i915 0000:00:02.0: setting latency timer to 64
[   10.180948] [drm] set up 15M of stolen space
[   10.242314] [drm] initialized overlay support
[   10.326176] type=1505 audit(1284510140.261:2):  operation="profile_load" pid=566 name="/sbin/dhclient3"
[   10.326914] type=1505 audit(1284510140.261:3):  operation="profile_load" pid=566 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[   10.327317] type=1505 audit(1284510140.261:4):  operation="profile_load" pid=566 name="/usr/lib/connman/scripts/dhclient-script"
[   10.442456] fb0: inteldrmfb frame buffer device
[   10.442464] registered panic notifier
[   10.442486] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
[   10.460187] vga16fb: initializing
[   10.460210] vga16fb: mapped to 0xc00a0000
[   10.460223] vga16fb: not registering due to another framebuffer present
[   10.622827] Console: switching to colour frame buffer device 170x48
[   10.628005] EXT4-fs (sda2): mounted filesystem with ordered data mode
[   10.628773]   alloc irq_desc for 21 on node -1
[   10.628779]   alloc kstat_irqs on node -1
[   10.628798] ENS1371 0000:01:00.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[   11.053261] input: ImPS/2 Generic Wheel Mouse as /devices/platform/i8042/serio1/input/input4
[   11.109388] render error detected, EIR: 0x00000010
[   11.109447] [drm:i915_handle_error] *ERROR* EIR stuck: 0x00000010, masking
[   11.109518] render error detected, EIR: 0x00000010
[   12.187465] type=1505 audit(1284510142.122:5):  operation="profile_load" pid=702 name="/usr/share/gdm/guest-session/Xsession"
[   12.219402] type=1505 audit(1284510142.154:6):  operation="profile_replace" pid=706 name="/sbin/dhclient3"
[   12.220349] type=1505 audit(1284510142.154:7):  operation="profile_replace" pid=706 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[   12.220892] type=1505 audit(1284510142.154:8):  operation="profile_replace" pid=706 name="/usr/lib/connman/scripts/dhclient-script"
[   12.270131] type=1505 audit(1284510142.206:9):  operation="profile_load" pid=716 name="/usr/bin/evince"
[   12.310825] type=1505 audit(1284510142.246:10):  operation="profile_load" pid=716 name="/usr/bin/evince-previewer"
[   12.331817] type=1505 audit(1284510142.266:11):  operation="profile_load" pid=716 name="/usr/bin/evince-thumbnailer"
[   13.580041] CPU0 attaching NULL sched-domain.
[   13.580061] CPU1 attaching NULL sched-domain.
[   13.593287] CPU0 attaching sched-domain:
[   13.593299]  domain 0: span 0-1 level SIBLING
[   13.593307]   groups: 0 (cpu_power = 589) 1 (cpu_power = 589)
[   13.593327]   domain 1: span 0-1 level MC
[   13.593337]    groups: 0-1 (cpu_power = 1178)
[   13.593360] CPU1 attaching sched-domain:
[   13.593367]  domain 0: span 0-1 level SIBLING
[   13.593373]   groups: 1 (cpu_power = 589) 0 (cpu_power = 589)
[   13.593388]   domain 1: span 0-1 level MC
[   13.593394]    groups: 0-1 (cpu_power = 1178)
[   15.397889] 0000:01:04.0: tulip_stop_rxtx() failed (CSR5 0xfc664010 CSR6 0xff972113)
[   15.397907] eth0: Setting full-duplex based on MII#1 link partner capability of 45e1.
[   17.147479] CPU0 attaching NULL sched-domain.
[   17.147496] CPU1 attaching NULL sched-domain.
[   17.180193] CPU0 attaching sched-domain:
[   17.180203]  domain 0: span 0-1 level SIBLING
[   17.180210]   groups: 0 (cpu_power = 589) 1 (cpu_power = 589)
[   17.180227]   domain 1: span 0-1 level MC
[   17.180233]    groups: 0-1 (cpu_power = 1178)
[   17.180249] CPU1 attaching sched-domain:
[   17.180255]  domain 0: span 0-1 level SIBLING
[   17.180262]   groups: 1 (cpu_power = 589) 0 (cpu_power = 589)
[   17.180277]   domain 1: span 0-1 level MC
[   17.180284]    groups: 0-1 (cpu_power = 1178)
[   23.288078] eth0: no IPv6 routers present
```[/INDENT]**dmesg AFTER unmounting**[INDENT]```
 Just pasted the end!
[COLOR=DimGray][   17.180284]    groups: 0-1 (cpu_power = 1178)
[   23.288078] eth0: no IPv6 routers present
[/COLOR][ 3150.025443] ata3.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6
[ 3150.025453] ata3.00: BMDMA stat 0x26
[ 3150.025461] ata3.00: failed command: READ DMA EXT
[ 3150.025471] ata3.00: cmd 25/00:00:77:2a:d5/00:02:02:00:00/e0 tag 0 dma 262144 in
[ 3150.025473]          res 51/84:ef:88:2a:d5/84:01:02:00:00/e0 Emask 0x30 (host bus error)
[ 3150.025478] ata3.00: status: { DRDY ERR }
[ 3150.025482] ata3.00: error: { ICRC ABRT }
[ 3150.025499] ata3: soft resetting link
[ 3150.200056] ata3.00: failed to IDENTIFY (I/O error, err_mask=0x2)
[ 3150.200067] ata3.00: revalidation failed (errno=-5)
[ 3155.181085] ata3: soft resetting link
[ 3155.372107] ata3.00: failed to IDENTIFY (I/O error, err_mask=0x2)
[ 3155.372115] ata3.00: revalidation failed (errno=-5)
[ 3155.372132] ata3.00: limiting speed to UDMA/133:PIO3
[ 3160.336080] ata3: soft resetting link
[ 3160.512085] ata3.00: failed to IDENTIFY (I/O error, err_mask=0x2)
[ 3160.512102] ata3.00: revalidation failed (errno=-5)
[ 3160.512127] ata3.00: disabled
[ 3160.512214] ata3: soft resetting link
[ 3160.664136] ata3: EH complete
[ 3160.664200] sd 2:0:0:0: [sdb] Unhandled error code
[ 3160.664205] sd 2:0:0:0: [sdb] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
[ 3160.664213] sd 2:0:0:0: [sdb] CDB: Read(10): 28 00 02 d5 2a 77 00 02 00 00
[ 3160.664235] end_request: I/O error, dev sdb, sector 47524471
[ 3160.664247] __ratelimit: 9 callbacks suppressed
[ 3160.664253] Buffer I/O error on device sdb1, logical block 5940551
[ 3160.664271] Buffer I/O error on device sdb1, logical block 5940552
[ 3160.664280] Buffer I/O error on device sdb1, logical block 5940553
[ 3160.664290] Buffer I/O error on device sdb1, logical block 5940554
[ 3160.664300] Buffer I/O error on device sdb1, logical block 5940555
[ 3160.664310] Buffer I/O error on device sdb1, logical block 5940556
[ 3160.664320] Buffer I/O error on device sdb1, logical block 5940557
[ 3160.664328] Buffer I/O error on device sdb1, logical block 5940558
[ 3160.664334] Buffer I/O error on device sdb1, logical block 5940559
[ 3160.664340] Buffer I/O error on device sdb1, logical block 5940560
[ 3160.664486] sd 2:0:0:0: [sdb] Unhandled error code
[ 3160.664492] sd 2:0:0:0: [sdb] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
[ 3160.664501] sd 2:0:0:0: [sdb] CDB: Read(10): 28 00 02 d5 2a 77 00 00 08 00
[ 3160.664527] end_request: I/O error, dev sdb, sector 47524471
[ 3160.665758] sd 2:0:0:0: [sdb] READ CAPACITY(16) failed
[ 3160.665772] sd 2:0:0:0: [sdb] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
[ 3160.665785] sd 2:0:0:0: [sdb] Sense not available.
[ 3160.665914] sd 2:0:0:0: [sdb] READ CAPACITY failed
[ 3160.665920] sd 2:0:0:0: [sdb] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
[ 3160.665928] sd 2:0:0:0: [sdb] Sense not available.
[ 3160.666085] sd 2:0:0:0: [sdb] Asking for cache data failed
[ 3160.666095] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[ 3160.666121] sdb: detected capacity change from 160041885696 to 0

```[/INDENT]I have installed and reinstalled Ubuntu to no avail. I have a separate /home partition. sdb driver mounts (when it does) as /windows.

---

