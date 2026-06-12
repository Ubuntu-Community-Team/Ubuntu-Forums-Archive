---
title: "Boot Issue after Installing Wireless keyboard mouse combo"
date: 2011-12-24
forum: General Help
---

### Post by chazdg24 on 2011-12-24
I received a wireless Logitech MK 550 keyboard mouse combo which is causing a boot problem. I get the following message after selecting Ubuntu in Grub:

disk drive for /media/sdg 1 is not ready yet or not present.
Continue to wait; press S to skip mounting; or M for manual recovery.

I press S and Ubuntu boots up. 

Is there anyway to fix this issue so I don't get this error message? It has something to do with etc/fstab but I don't want to mess with it someone knowledgeable guides me along the process.  Thanks for your help.

---

### Post by bobsageek on 2011-12-24
It might be purely coincidence that you installed the mouse/keyboard combo and got this error, stuff like thumb drives and SD cards get mounted to /media, and /media/sdg1 certainly fits that concept. Can you post the contents of *dmesg* and *cat /etc/fstab* please.

I use a Logitech kb/mouse that employs the Unifying Transceiver and it makes no mention of anything in /media during set up or use, hence my questions.

---

### Post by chazdg24 on 2011-12-24
My first question is what setup did you have with your Logitech keyboard?  I will make this two posts.

fstab:

# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                       /proc        proc  nodev,noexec,nosuid  0  0  
# / was on /dev/sda5 during installation
UUID=67e7a8a3-fc6d-408e-be09-9cfbcdb48219  /            ext4  errors=remount-ro    0  1  
# swap was on /dev/sda6 during installation
UUID=851df827-eb3e-43bf-bd46-3468670f6dd5  none         swap  sw                   0  0  
/dev/sdh1                                  /media/sdh1  ntfs  defaults             0  0  
/dev/sdg1                                  /media/sdg1  ntfs  defaults             0  0  
/dev/sdc1                                  /media/sdc1  ntfs  defaults             0  0

---

### Post by chazdg24 on 2011-12-24
```
dmesg:

[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 3.0.0-12-generic (buildd@crested) (gcc version 4.6.1 (Ubuntu/Linaro 4.6.1-9ubuntu3) ) #20-Ubuntu SMP Fri Oct 7 14:56:25 UTC 2011 (Ubuntu 3.0.0-12.20-generic 3.0.4)
[    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-3.0.0-12-generic root=UUID=67e7a8a3-fc6d-408e-be09-9cfbcdb48219 ro splash vga=786 quiet splash vt.handoff=7
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   Centaur CentaurHauls
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009ec00 (usable)
[    0.000000]  BIOS-e820: 000000000009ec00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e4000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 00000000bf760000 (usable)
[    0.000000]  BIOS-e820: 00000000bf760000 - 00000000bf76e000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000bf76e000 - 00000000bf7a8000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000bf7a8000 - 00000000bf7e0000 (reserved)
[    0.000000]  BIOS-e820: 00000000bf7eb800 - 00000000c0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000ffc00000 - 0000000100000000 (reserved)
[    0.000000]  BIOS-e820: 0000000100000000 - 0000000280000000 (usable)
[    0.000000] NX (Execute Disable) protection: active
[    0.000000] DMI present.
[    0.000000] DMI: DELL Inc. Studio XPS 435T/9000/0X501H, BIOS A16 02/04/2010
[    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
[    0.000000] e820 remove range: 00000000000a0000 - 0000000000100000 (usable)
[    0.000000] No AGP bridge found
[    0.000000] last_pfn = 0x280000 max_arch_pfn = 0x400000000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-DFFFF uncachable
[    0.000000]   E0000-EBFFF write-through
[    0.000000]   EC000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000 mask E00000000 write-back
[    0.000000]   1 base 200000000 mask F80000000 write-back
[    0.000000]   2 base 0C0000000 mask FC0000000 uncachable
[    0.000000]   3 base 0BF800000 mask FFF800000 uncachable
[    0.000000]   4 disabled
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] original variable MTRRs
[    0.000000] reg 0, base: 0GB, range: 8GB, type WB
[    0.000000] reg 1, base: 8GB, range: 2GB, type WB
[    0.000000] reg 2, base: 3GB, range: 1GB, type UC
[    0.000000] reg 3, base: 3064MB, range: 8MB, type UC
[    0.000000] total RAM covered: 9208M
[    0.000000] Found optimal setting for mtrr clean up
[    0.000000]  gran_size: 64K 	chunk_size: 16M 	num_reg: 5  	lose cover RAM: 0G
[    0.000000] New variable MTRRs
[    0.000000] reg 0, base: 0GB, range: 2GB, type WB
[    0.000000] reg 1, base: 2GB, range: 1GB, type WB
[    0.000000] reg 2, base: 3064MB, range: 8MB, type UC
[    0.000000] reg 3, base: 4GB, range: 4GB, type WB
[    0.000000] reg 4, base: 8GB, range: 2GB, type WB
[    0.000000] e820 update range: 00000000bf800000 - 0000000100000000 (usable) ==> (reserved)
[    0.000000] last_pfn = 0xbf760 max_arch_pfn = 0x400000000
[    0.000000] found SMP MP-table at [ffff8800000ff780] ff780
[    0.000000] initial memory mapped : 0 - 20000000
[    0.000000] Base memory trampoline at [ffff880000099000] 99000 size 20480
[    0.000000] init_memory_mapping: 0000000000000000-00000000bf760000
[    0.000000]  0000000000 - 00bf600000 page 2M
[    0.000000]  00bf600000 - 00bf760000 page 4k
[    0.000000] kernel direct mapping tables up to bf760000 @ bf75b000-bf760000
[    0.000000] init_memory_mapping: 0000000100000000-0000000280000000
[    0.000000]  0100000000 - 0280000000 page 2M
[    0.000000] kernel direct mapping tables up to 280000000 @ 27fff5000-280000000
[    0.000000] RAMDISK: 365bc000 - 372d6000
[    0.000000] ACPI: RSDP 00000000000f9d60 00014 (v00 ACPIAM)
[    0.000000] ACPI: RSDT 00000000bf760000 00048 (v01 DELL    MI09    20100512 MSFT 00000097)
[    0.000000] ACPI: FACP 00000000bf760200 00084 (v01 DELL   MI09     20100512 MSFT 00000097)
[    0.000000] ACPI: DSDT 00000000bf760600 05F73 (v01  A7546 A7546011 00000011 INTL 20051117)
[    0.000000] ACPI: FACS 00000000bf76e000 00040
[    0.000000] ACPI: APIC 00000000bf760390 000AC (v01 DELL   MI09     20100512 MSFT 00000097)
[    0.000000] ACPI: MCFG 00000000bf760440 0003C (v01 DELL   MI09     20100512 MSFT 00000097)
[    0.000000] ACPI: SLIC 00000000bf760480 00176 (v01 DELL    MI09    20100512 MSFT 00000097)
[    0.000000] ACPI: OEMB 00000000bf76e040 00071 (v01 DELL   MI09     20100512 MSFT 00000097)
[    0.000000] ACPI: HPET 00000000bf766580 00038 (v01 DELL   MI09     20100512 MSFT 00000097)
[    0.000000] ACPI: ASPT 00000000bf766a60 00034 (v04 DELL   PerfTune 20100512 MSFT 00000097)
[    0.000000] ACPI: WDTT 00000000bf766aa0 00134 (v01 DELL   OEMWDTT  20100512 MSFT 00000097)
[    0.000000] ACPI: SSDT 00000000bf7710f0 0249F (v01 DpgPmm    CpuPm 00000012 INTL 20051117)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] No NUMA configuration found
[    0.000000] Faking a node at 0000000000000000-0000000280000000
[    0.000000] Initmem setup node 0 0000000000000000-0000000280000000
[    0.000000]   NODE_DATA [000000027fffb000 - 000000027fffffff]
[    0.000000]  [ffffea0000000000-ffffea0008bfffff] PMD -> [ffff880276600000-ffff88027e3fffff] on node 0
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000010 -> 0x00001000
[    0.000000]   DMA32    0x00001000 -> 0x00100000
[    0.000000]   Normal   0x00100000 -> 0x00280000
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[3] active PFN ranges
[    0.000000]     0: 0x00000010 -> 0x0000009e
[    0.000000]     0: 0x00000100 -> 0x000bf760
[    0.000000]     0: 0x00100000 -> 0x00280000
[    0.000000] On node 0 totalpages: 2356974
[    0.000000]   DMA zone: 56 pages used for memmap
[    0.000000]   DMA zone: 5 pages reserved
[    0.000000]   DMA zone: 3921 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 14280 pages used for memmap
[    0.000000]   DMA32 zone: 765848 pages, LIFO batch:31
[    0.000000]   Normal zone: 21504 pages used for memmap
[    0.000000]   Normal zone: 1551360 pages, LIFO batch:31
[    0.000000] ACPI: PM-Timer IO Port: 0x808
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x02] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x04] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x06] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x05] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x06] lapic_id[0x03] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x07] lapic_id[0x05] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x08] lapic_id[0x07] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x09] lapic_id[0x88] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x0a] lapic_id[0x89] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x0b] lapic_id[0x8a] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x0c] lapic_id[0x8b] disabled)
[    0.000000] ACPI: IOAPIC (id[0x08] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 8, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0xffffffff base: 0xfed00000
[    0.000000] SMP: Allowing 12 CPUs, 4 hotplug CPUs
[    0.000000] nr_irqs_gsi: 40
[    0.000000] PM: Registered nosave memory: 000000000009e000 - 000000000009f000
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e4000
[    0.000000] PM: Registered nosave memory: 00000000000e4000 - 0000000000100000
[    0.000000] PM: Registered nosave memory: 00000000bf760000 - 00000000bf76e000
[    0.000000] PM: Registered nosave memory: 00000000bf76e000 - 00000000bf7a8000
[    0.000000] PM: Registered nosave memory: 00000000bf7a8000 - 00000000bf7e0000
[    0.000000] PM: Registered nosave memory: 00000000bf7e0000 - 00000000bf7ec000
[    0.000000] PM: Registered nosave memory: 00000000bf7ec000 - 00000000c0000000
[    0.000000] PM: Registered nosave memory: 00000000c0000000 - 00000000fee00000
[    0.000000] PM: Registered nosave memory: 00000000fee00000 - 00000000fee01000
[    0.000000] PM: Registered nosave memory: 00000000fee01000 - 00000000ffc00000
[    0.000000] PM: Registered nosave memory: 00000000ffc00000 - 0000000100000000
[    0.000000] Allocating PCI resources starting at c0000000 (gap: c0000000:3ee00000)
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] setup_percpu: NR_CPUS:256 nr_cpumask_bits:256 nr_cpu_ids:12 nr_node_ids:1
[    0.000000] PERCPU: Embedded 27 pages/cpu @ffff88027fc00000 s79616 r8192 d22784 u131072
[    0.000000] pcpu-alloc: s79616 r8192 d22784 u131072 alloc=1*2097152
[    0.000000] pcpu-alloc: [0] 00 01 02 03 04 05 06 07 08 09 10 11 -- -- -- -- 
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 2321129
[    0.000000] Policy zone: Normal
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.0.0-12-generic root=UUID=67e7a8a3-fc6d-408e-be09-9cfbcdb48219 ro splash vga=786 quiet splash vt.handoff=7
[    0.000000] PID hash table entries: 4096 (order: 3, 32768 bytes)
[    0.000000] Checking aperture...
[    0.000000] No AGP bridge found
[    0.000000] Calgary: detecting Calgary via BIOS EBDA area
[    0.000000] Calgary: Unable to locate Rio Grande table in EBDA - bailing!
[    0.000000] Memory: 9204516k/10485760k available (6104k kernel code, 1057864k absent, 223380k reserved, 4880k data, 984k init)
[    0.000000] SLUB: Genslabs=15, HWalign=64, Order=0-3, MinObjects=0, CPUs=12, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000] 	RCU dyntick-idle grace-period acceleration is enabled.
[    0.000000] NR_IRQS:16640 nr_irqs:776 16
[    0.000000] vt handoff: transparent VT on vt#7
[    0.000000] Console: colour dummy device 80x25
[    0.000000] console [tty0] enabled
[    0.000000] allocated 75497472 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] hpet clockevent registered
[    0.000000] Fast TSC calibration using PIT
[    0.004000] Detected 3192.154 MHz processor.
[    0.000003] Calibrating delay loop (skipped), value calculated using timer frequency.. 6384.30 BogoMIPS (lpj=12768616)
[    0.000006] pid_max: default: 32768 minimum: 301
[    0.000029] Security Framework initialized
[    0.000041] AppArmor: AppArmor initialized
[    0.000043] Yama: becoming mindful.
[    0.001257] Dentry cache hash table entries: 2097152 (order: 12, 16777216 bytes)
[    0.004252] Inode-cache hash table entries: 1048576 (order: 11, 8388608 bytes)
[    0.005538] Mount-cache hash table entries: 256
[    0.005644] Initializing cgroup subsys cpuacct
[    0.005649] Initializing cgroup subsys memory
[    0.005656] Initializing cgroup subsys devices
[    0.005657] Initializing cgroup subsys freezer
[    0.005659] Initializing cgroup subsys net_cls
[    0.005660] Initializing cgroup subsys blkio
[    0.005665] Initializing cgroup subsys perf_event
[    0.005689] CPU: Physical Processor ID: 0
[    0.005690] CPU: Processor Core ID: 0
[    0.005694] mce: CPU supports 9 MCE banks
[    0.005708] CPU0: Thermal monitoring enabled (TM1)
[    0.005715] using mwait in idle threads.
[    0.007417] ACPI: Core revision 20110413
[    0.036338] ftrace: allocating 25651 entries in 101 pages
[    0.042357] Switched APIC routing to physical flat.
[    0.042672] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.082259] CPU0: Intel(R) Core(TM) i7 CPU         960  @ 3.20GHz stepping 05
[    0.248403] APIC calibration not consistent with PM-Timer: 159ms instead of 100ms
[    0.248406] APIC delta adjusted to PM-Timer: 831248 (1329983)
[    0.248412] Performance Events: PEBS fmt1+, erratum AAJ80 worked around, Nehalem events, Intel PMU driver.
[    0.248419] ... version:                3
[    0.248420] ... bit width:              48
[    0.248421] ... generic registers:      4
[    0.248422] ... value mask:             0000ffffffffffff
[    0.248424] ... max period:             000000007fffffff
[    0.248425] ... fixed-purpose events:   3
[    0.248426] ... event mask:             000000070000000f
[    0.248798] Booting Node   0, Processors  #1
[    0.248800] smpboot cpu 1: start_ip = 99000
[    0.356260]  #2
[    0.356262] smpboot cpu 2: start_ip = 99000
[    0.467975]  #3
[    0.467977] smpboot cpu 3: start_ip = 99000
[    0.575726]  #4
[    0.575728] smpboot cpu 4: start_ip = 99000
[    0.683457]  #5
[    0.683459] smpboot cpu 5: start_ip = 99000
[    0.791189]  #6
[    0.791191] smpboot cpu 6: start_ip = 99000
[    0.898922]  #7
[    0.898924] smpboot cpu 7: start_ip = 99000
[    1.006592] Brought up 8 CPUs
[    1.006594] Total of 8 processors activated (51069.92 BogoMIPS).
[    1.010906] devtmpfs: initialized
[    1.010999] PM: Registering ACPI NVS region at bf76e000 (237568 bytes)
[    1.012058] print_constraints: dummy: 
[    1.012080] Time: 10:09:40  Date: 12/24/11
[    1.012104] NET: Registered protocol family 16
[    1.012177] Trying to unpack rootfs image as initramfs...
[    1.012182] ACPI: bus type pci registered
[    1.012225] PCI: MMCONFIG for domain 0000 [bus 00-ff] at [mem 0xe0000000-0xefffffff] (base 0xe0000000)
[    1.012227] PCI: not using MMCONFIG
[    1.012228] PCI: Using configuration type 1 for base access
[    1.012716] bio: create slab <bio-0> at 0
[    1.013559] ACPI: EC: Look up EC in DSDT
[    1.014336] ACPI: Executed 1 blocks of module-level executable AML code
[    1.016173] ACPI: SSDT 00000000bf76e0c0 0050B (v01 DpgPmm  P001Ist 00000011 INTL 20051117)
[    1.016353] ACPI: Dynamic OEM Table Load:
[    1.016355] ACPI: SSDT           (null) 0050B (v01 DpgPmm  P001Ist 00000011 INTL 20051117)
[    1.016483] ACPI: SSDT 00000000bf770940 003B2 (v01  PmRef  P001Cst 00003001 INTL 20051117)
[    1.016655] ACPI: Dynamic OEM Table Load:
[    1.016656] ACPI: SSDT           (null) 003B2 (v01  PmRef  P001Cst 00003001 INTL 20051117)
[    1.038588] ACPI: SSDT 00000000bf76e5d0 0050B (v01 DpgPmm  P002Ist 00000012 INTL 20051117)
[    1.038770] ACPI: Dynamic OEM Table Load:
[    1.038771] ACPI: SSDT           (null) 0050B (v01 DpgPmm  P002Ist 00000012 INTL 20051117)
[    1.038888] ACPI: SSDT 00000000bf770d00 00085 (v01  PmRef  P002Cst 00003000 INTL 20051117)
[    1.039062] ACPI: Dynamic OEM Table Load:
[    1.039063] ACPI: SSDT           (null) 00085 (v01  PmRef  P002Cst 00003000 INTL 20051117)
[    1.074515] ACPI: SSDT 00000000bf76eae0 0050B (v01 DpgPmm  P003Ist 00000012 INTL 20051117)
[    1.074701] ACPI: Dynamic OEM Table Load:
[    1.074703] ACPI: SSDT           (null) 0050B (v01 DpgPmm  P003Ist 00000012 INTL 20051117)
[    1.074823] ACPI: SSDT 00000000bf770d90 00085 (v01  PmRef  P003Cst 00003000 INTL 20051117)
[    1.074998] ACPI: Dynamic OEM Table Load:
[    1.074999] ACPI: SSDT           (null) 00085 (v01  PmRef  P003Cst 00003000 INTL 20051117)
[    1.122216] ACPI: SSDT 00000000bf76eff0 0050B (v01 DpgPmm  P004Ist 00000012 INTL 20051117)
[    1.122415] ACPI: Dynamic OEM Table Load:
[    1.122417] ACPI: SSDT           (null) 0050B (v01 DpgPmm  P004Ist 00000012 INTL 20051117)
[    1.122535] ACPI: SSDT 00000000bf770e20 00085 (v01  PmRef  P004Cst 00003000 INTL 20051117)
[    1.122710] ACPI: Dynamic OEM Table Load:
[    1.122712] ACPI: SSDT           (null) 00085 (v01  PmRef  P004Cst 00003000 INTL 20051117)
[    1.186242] ACPI: SSDT 00000000bf76f500 0050B (v01 DpgPmm  P005Ist 00000012 INTL 20051117)
[    1.186428] ACPI: Dynamic OEM Table Load:
[    1.186430] ACPI: SSDT           (null) 0050B (v01 DpgPmm  P005Ist 00000012 INTL 20051117)
[    1.186541] ACPI: SSDT 00000000bf770eb0 00085 (v01  PmRef  P005Cst 00003000 INTL 20051117)
[    1.186715] ACPI: Dynamic OEM Table Load:
[    1.186716] ACPI: SSDT           (null) 00085 (v01  PmRef  P005Cst 00003000 INTL 20051117)
[    1.194686] Freeing initrd memory: 13416k freed
[    1.222194] ACPI: SSDT 00000000bf76fa10 0050B (v01 DpgPmm  P006Ist 00000012 INTL 20051117)
[    1.222382] ACPI: Dynamic OEM Table Load:
[    1.222384] ACPI: SSDT           (null) 0050B (v01 DpgPmm  P006Ist 00000012 INTL 20051117)
[    1.222495] ACPI: SSDT 00000000bf770f40 00085 (v01  PmRef  P006Cst 00003000 INTL 20051117)
[    1.222672] ACPI: Dynamic OEM Table Load:
[    1.222673] ACPI: SSDT           (null) 00085 (v01  PmRef  P006Cst 00003000 INTL 20051117)
[    1.257895] ACPI: SSDT 00000000bf76ff20 0050B (v01 DpgPmm  P007Ist 00000012 INTL 20051117)
[    1.258097] ACPI: Dynamic OEM Table Load:
[    1.258098] ACPI: SSDT           (null) 0050B (v01 DpgPmm  P007Ist 00000012 INTL 20051117)
[    1.258204] ACPI: SSDT 00000000bf770fd0 00085 (v01  PmRef  P007Cst 00003000 INTL 20051117)
[    1.258379] ACPI: Dynamic OEM Table Load:
[    1.258381] ACPI: SSDT           (null) 00085 (v01  PmRef  P007Cst 00003000 INTL 20051117)
[    1.270063] ACPI: SSDT 00000000bf770430 0050B (v01 DpgPmm  P008Ist 00000012 INTL 20051117)
[    1.270249] ACPI: Dynamic OEM Table Load:
[    1.270251] ACPI: SSDT           (null) 0050B (v01 DpgPmm  P008Ist 00000012 INTL 20051117)
[    1.270355] ACPI: SSDT 00000000bf771060 00085 (v01  PmRef  P008Cst 00003000 INTL 20051117)
[    1.270534] ACPI: Dynamic OEM Table Load:
[    1.270535] ACPI: SSDT           (null) 00085 (v01  PmRef  P008Cst 00003000 INTL 20051117)
[    1.281948] ACPI: Interpreter enabled
[    1.281950] ACPI: (supports S0 S3 S4 S5)
[    1.281963] ACPI: Using IOAPIC for interrupt routing
[    1.281981] PCI: MMCONFIG for domain 0000 [bus 00-ff] at [mem 0xe0000000-0xefffffff] (base 0xe0000000)
[    1.282345] PCI: MMCONFIG at [mem 0xe0000000-0xefffffff] reserved in ACPI motherboard resources
[    1.309970] ACPI: No dock devices found.
[    1.309972] HEST: Table not found.
[    1.309974] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
[    1.310030] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-ff])
[    1.310143] pci_root PNP0A08:00: host bridge window [io  0x0000-0x0cf7]
[    1.310145] pci_root PNP0A08:00: host bridge window [io  0x0d00-0xffff]
[    1.310146] pci_root PNP0A08:00: host bridge window [mem 0x000a0000-0x000bffff]
[    1.310148] pci_root PNP0A08:00: host bridge window [mem 0x000d0000-0x000dffff]
[    1.310149] pci_root PNP0A08:00: host bridge window [mem 0xc0000000-0xdfffffff]
[    1.310150] pci_root PNP0A08:00: host bridge window [mem 0xf0000000-0xfed8ffff]
[    1.310163] pci 0000:00:00.0: [8086:3405] type 0 class 0x000600
[    1.310201] pci 0000:00:00.0: PME# supported from D0 D3hot D3cold
[    1.310204] pci 0000:00:00.0: PME# disabled
[    1.310222] pci 0000:00:01.0: [8086:3408] type 1 class 0x000604
[    1.310261] pci 0000:00:01.0: PME# supported from D0 D3hot D3cold
[    1.310263] pci 0000:00:01.0: PME# disabled
[    1.310282] pci 0000:00:03.0: [8086:340a] type 1 class 0x000604
[    1.310320] pci 0000:00:03.0: PME# supported from D0 D3hot D3cold
[    1.310322] pci 0000:00:03.0: PME# disabled
[    1.310342] pci 0000:00:07.0: [8086:340e] type 1 class 0x000604
[    1.310380] pci 0000:00:07.0: PME# supported from D0 D3hot D3cold
[    1.310383] pci 0000:00:07.0: PME# disabled
[    1.310401] pci 0000:00:09.0: [8086:3410] type 1 class 0x000604
[    1.310439] pci 0000:00:09.0: PME# supported from D0 D3hot D3cold
[    1.310442] pci 0000:00:09.0: PME# disabled
[    1.310461] pci 0000:00:14.0: [8086:342e] type 0 class 0x000800
[    1.310514] pci 0000:00:14.1: [8086:3422] type 0 class 0x000800
[    1.310566] pci 0000:00:14.2: [8086:3423] type 0 class 0x000800
[    1.310616] pci 0000:00:14.3: [8086:3438] type 0 class 0x000800
[    1.310667] pci 0000:00:1a.0: [8086:3a37] type 0 class 0x000c03
[    1.310705] pci 0000:00:1a.0: reg 20: [io  0x9400-0x941f]
[    1.310742] pci 0000:00:1a.1: [8086:3a38] type 0 class 0x000c03
[    1.310779] pci 0000:00:1a.1: reg 20: [io  0x9480-0x949f]
[    1.310816] pci 0000:00:1a.2: [8086:3a39] type 0 class 0x000c03
[    1.310853] pci 0000:00:1a.2: reg 20: [io  0x9800-0x981f]
[    1.310898] pci 0000:00:1a.7: [8086:3a3c] type 0 class 0x000c03
[    1.310917] pci 0000:00:1a.7: reg 10: [mem 0xfa800000-0xfa8003ff]
[    1.310981] pci 0000:00:1a.7: PME# supported from D0 D3hot D3cold
[    1.310984] pci 0000:00:1a.7: PME# disabled
[    1.311004] pci 0000:00:1b.0: [8086:3a3e] type 0 class 0x000403
[    1.311016] pci 0000:00:1b.0: reg 10: [mem 0xfaff8000-0xfaffbfff 64bit]
[    1.311063] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    1.311066] pci 0000:00:1b.0: PME# disabled
[    1.311082] pci 0000:00:1c.0: [8086:3a40] type 1 class 0x000604
[    1.311129] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    1.311132] pci 0000:00:1c.0: PME# disabled
[    1.311151] pci 0000:00:1c.2: [8086:3a44] type 1 class 0x000604
[    1.311198] pci 0000:00:1c.2: PME# supported from D0 D3hot D3cold
[    1.311201] pci 0000:00:1c.2: PME# disabled
[    1.311218] pci 0000:00:1c.3: [8086:3a46] type 1 class 0x000604
[    1.311265] pci 0000:00:1c.3: PME# supported from D0 D3hot D3cold
[    1.311268] pci 0000:00:1c.3: PME# disabled
[    1.311285] pci 0000:00:1c.4: [8086:3a48] type 1 class 0x000604
[    1.311332] pci 0000:00:1c.4: PME# supported from D0 D3hot D3cold
[    1.311335] pci 0000:00:1c.4: PME# disabled
[    1.311355] pci 0000:00:1d.0: [8086:3a34] type 0 class 0x000c03
[    1.311393] pci 0000:00:1d.0: reg 20: [io  0x9880-0x989f]
[    1.311430] pci 0000:00:1d.1: [8086:3a35] type 0 class 0x000c03
[    1.311468] pci 0000:00:1d.1: reg 20: [io  0x9c00-0x9c1f]
[    1.311506] pci 0000:00:1d.2: [8086:3a36] type 0 class 0x000c03
[    1.311543] pci 0000:00:1d.2: reg 20: [io  0xa000-0xa01f]
[    1.311589] pci 0000:00:1d.7: [8086:3a3a] type 0 class 0x000c03
[    1.311607] pci 0000:00:1d.7: reg 10: [mem 0xfaa00000-0xfaa003ff]
[    1.311671] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
[    1.311675] pci 0000:00:1d.7: PME# disabled
[    1.311690] pci 0000:00:1e.0: [8086:244e] type 1 class 0x000604
[    1.311739] pci 0000:00:1f.0: [8086:3a16] type 0 class 0x000601
[    1.311812] pci 0000:00:1f.0: ICH7 LPC Generic IO decode 1 PIO at 0a00 (mask 00ff)
[    1.311848] pci 0000:00:1f.2: [8086:3a22] type 0 class 0x000106
[    1.311864] pci 0000:00:1f.2: reg 10: [io  0xa880-0xa887]
[    1.311871] pci 0000:00:1f.2: reg 14: [io  0xa800-0xa803]
[    1.311877] pci 0000:00:1f.2: reg 18: [io  0xa480-0xa487]
[    1.311884] pci 0000:00:1f.2: reg 1c: [io  0xa400-0xa403]
[    1.311890] pci 0000:00:1f.2: reg 20: [io  0xa080-0xa09f]
[    1.311897] pci 0000:00:1f.2: reg 24: [mem 0xfac00000-0xfac007ff]
[    1.311925] pci 0000:00:1f.2: PME# supported from D3hot
[    1.311928] pci 0000:00:1f.2: PME# disabled
[    1.311941] pci 0000:00:1f.3: [8086:3a30] type 0 class 0x000c05
[    1.311954] pci 0000:00:1f.3: reg 10: [mem 0xfafffc00-0xfafffcff 64bit]
[    1.311972] pci 0000:00:1f.3: reg 20: [io  0x0400-0x041f]
[    1.312022] pci 0000:00:01.0: PCI bridge to [bus 09-09]
[    1.312025] pci 0000:00:01.0:   bridge window [io  0xf000-0x0000] (disabled)
[    1.312028] pci 0000:00:01.0:   bridge window [mem 0xfff00000-0x000fffff] (disabled)
[    1.312032] pci 0000:00:01.0:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    1.312070] pci 0000:08:00.0: [1002:6898] type 0 class 0x000300
[    1.312081] pci 0000:08:00.0: reg 10: [mem 0xd0000000-0xdfffffff 64bit pref]
[    1.312090] pci 0000:08:00.0: reg 18: [mem 0xfbfc0000-0xfbfdffff 64bit]
[    1.312097] pci 0000:08:00.0: reg 20: [io  0xe000-0xe0ff]
[    1.312108] pci 0000:08:00.0: reg 30: [mem 0xfbfa0000-0xfbfbffff pref]
[    1.312123] pci 0000:08:00.0: supports D1 D2
[    1.312140] pci 0000:08:00.1: [1002:aa50] type 0 class 0x000403
[    1.312151] pci 0000:08:00.1: reg 10: [mem 0xfbffc000-0xfbffffff 64bit]
[    1.312190] pci 0000:08:00.1: supports D1 D2
[    1.317713] pci 0000:00:03.0: PCI bridge to [bus 08-08]
[    1.317717] pci 0000:00:03.0:   bridge window [io  0xe000-0xefff]
[    1.317721] pci 0000:00:03.0:   bridge window [mem 0xfbf00000-0xfbffffff]
[    1.317727] pci 0000:00:03.0:   bridge window [mem 0xd0000000-0xdfffffff 64bit pref]
[    1.317770] pci 0000:00:07.0: PCI bridge to [bus 07-07]
[    1.317774] pci 0000:00:07.0:   bridge window [io  0xf000-0x0000] (disabled)
[    1.317779] pci 0000:00:07.0:   bridge window [mem 0xfff00000-0x000fffff] (disabled)
[    1.317785] pci 0000:00:07.0:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    1.317822] pci 0000:00:09.0: PCI bridge to [bus 06-06]
[    1.317824] pci 0000:00:09.0:   bridge window [io  0xf000-0x0000] (disabled)
[    1.317827] pci 0000:00:09.0:   bridge window [mem 0xfff00000-0x000fffff] (disabled)
[    1.317831] pci 0000:00:09.0:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    1.317865] pci 0000:00:1c.0: PCI bridge to [bus 05-05]
[    1.317868] pci 0000:00:1c.0:   bridge window [io  0xf000-0x0000] (disabled)
[    1.317871] pci 0000:00:1c.0:   bridge window [mem 0xfff00000-0x000fffff] (disabled)
[    1.317875] pci 0000:00:1c.0:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    1.317924] pci 0000:04:00.0: [10ec:8168] type 0 class 0x000200
[    1.317939] pci 0000:04:00.0: reg 10: [io  0xd800-0xd8ff]
[    1.317965] pci 0000:04:00.0: reg 18: [mem 0xfbeff000-0xfbefffff 64bit]
[    1.317981] pci 0000:04:00.0: reg 20: [mem 0xcfff0000-0xcfffffff 64bit pref]
[    1.317992] pci 0000:04:00.0: reg 30: [mem 0xfbec0000-0xfbedffff pref]
[    1.318027] pci 0000:04:00.0: supports D1 D2
[    1.318029] pci 0000:04:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    1.318033] pci 0000:04:00.0: PME# disabled
[    1.325698] pci 0000:00:1c.2: PCI bridge to [bus 04-04]
[    1.325702] pci 0000:00:1c.2:   bridge window [io  0xd000-0xdfff]
[    1.325707] pci 0000:00:1c.2:   bridge window [mem 0xfbe00000-0xfbefffff]
[    1.325714] pci 0000:00:1c.2:   bridge window [mem 0xcff00000-0xcfffffff 64bit pref]
[    1.325778] pci 0000:03:00.0: [197b:2363] type 0 class 0x000101
[    1.325860] pci 0000:03:00.0: reg 24: [mem 0xfbc00000-0xfbc01fff]
[    1.325900] pci 0000:03:00.0: PME# supported from D3hot
[    1.325904] pci 0000:03:00.0: PME# disabled
[    1.325930] pci 0000:03:00.1: [197b:2363] type 0 class 0x000101
[    1.325952] pci 0000:03:00.1: reg 10: [io  0xcc00-0xcc07]
[    1.325965] pci 0000:03:00.1: reg 14: [io  0xc880-0xc883]
[    1.325977] pci 0000:03:00.1: reg 18: [io  0xc800-0xc807]
[    1.325989] pci 0000:03:00.1: reg 1c: [io  0xc480-0xc483]
[    1.326001] pci 0000:03:00.1: reg 20: [io  0xc400-0xc40f]
[    1.326066] pci 0000:03:00.0: disabling ASPM on pre-1.1 PCIe device.  You can enable it with 'pcie_aspm=force'
[    1.326077] pci 0000:00:1c.3: PCI bridge to [bus 03-03]
[    1.326080] pci 0000:00:1c.3:   bridge window [io  0xc000-0xcfff]
[    1.326083] pci 0000:00:1c.3:   bridge window [mem 0xfbc00000-0xfbdfffff]
[    1.326088] pci 0000:00:1c.3:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    1.326140] pci 0000:02:00.0: [197b:2380] type 0 class 0x000c00
[    1.326161] pci 0000:02:00.0: reg 10: [mem 0xfb800000-0xfb8007ff]
[    1.326176] pci 0000:02:00.0: reg 14: [mem 0xfb600000-0xfb60007f]
[    1.326219] pci 0000:02:00.0: reg 20: [mem 0xfb400000-0xfb40007f]
[    1.326234] pci 0000:02:00.0: reg 24: [mem 0xfb200000-0xfb20007f]
[    1.333680] pci 0000:00:1c.4: PCI bridge to [bus 02-02]
[    1.333685] pci 0000:00:1c.4:   bridge window [io  0xf000-0x0000] (disabled)
[    1.333690] pci 0000:00:1c.4:   bridge window [mem 0xfb200000-0xfb9fffff]
[    1.333697] pci 0000:00:1c.4:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    1.333732] pci 0000:01:00.0: [14f1:2f20] type 0 class 0x000780
[    1.333750] pci 0000:01:00.0: reg 10: [mem 0xfb000000-0xfb00ffff]
[    1.333763] pci 0000:01:00.0: reg 14: [io  0xbc00-0xbc07]
[    1.333813] pci 0000:01:00.0: PME# supported from D3hot D3cold
[    1.333817] pci 0000:01:00.0: PME# disabled
[    1.333856] pci 0000:00:1e.0: PCI bridge to [bus 01-01] (subtractive decode)
[    1.333859] pci 0000:00:1e.0:   bridge window [io  0xb000-0xbfff]
[    1.333861] pci 0000:00:1e.0:   bridge window [mem 0xfb000000-0xfb1fffff]
[    1.333866] pci 0000:00:1e.0:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    1.333868] pci 0000:00:1e.0:   bridge window [io  0x0000-0x0cf7] (subtractive decode)
[    1.333869] pci 0000:00:1e.0:   bridge window [io  0x0d00-0xffff] (subtractive decode)
[    1.333871] pci 0000:00:1e.0:   bridge window [mem 0x000a0000-0x000bffff] (subtractive decode)
[    1.333872] pci 0000:00:1e.0:   bridge window [mem 0x000d0000-0x000dffff] (subtractive decode)
[    1.333874] pci 0000:00:1e.0:   bridge window [mem 0xc0000000-0xdfffffff] (subtractive decode)
[    1.333875] pci 0000:00:1e.0:   bridge window [mem 0xf0000000-0xfed8ffff] (subtractive decode)
[    1.333905] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    1.334043] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P1._PRT]
[    1.334089] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P4._PRT]
[    1.334108] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P6._PRT]
[    1.334125] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P7._PRT]
[    1.334148] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P8._PRT]
[    1.334185]  pci0000:00: Requesting ACPI _OSC control (0x1d)
[    1.334187]  pci0000:00: ACPI _OSC request failed (AE_NOT_FOUND), returned control mask: 0x1d
[    1.334188] ACPI _OSC control for PCIe not granted, disabling ASPM
[    1.341994] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 6 7 10 11 12 14 *15)
[    1.342026] ACPI: PCI Interrupt Link [LNKB] (IRQs *5)
[    1.342052] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 6 7 10 *11 12 14 15)
[    1.342080] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 6 7 *10 11 12 14 15)
[    1.342107] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 6 7 10 11 12 14 15) *0, disabled.
[    1.342135] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 6 *7 10 11 12 14 15)
[    1.342163] ACPI: PCI Interrupt Link [LNKG] (IRQs *3 4 6 7 10 11 12 14 15)
[    1.342191] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 6 7 10 11 12 *14 15)
[    1.342257] vgaarb: device added: PCI:0000:08:00.0,decodes=io+mem,owns=io+mem,locks=none
[    1.342259] vgaarb: loaded
[    1.342260] vgaarb: bridge control possible 0000:08:00.0
[    1.342374] SCSI subsystem initialized
[    1.342415] libata version 3.00 loaded.
[    1.342445] usbcore: registered new interface driver usbfs
[    1.342451] usbcore: registered new interface driver hub
[    1.342468] usbcore: registered new device driver usb
[    1.342525] PCI: Using ACPI for IRQ routing
[    1.347916] PCI: Discovered peer bus ff
[    1.347934] pci 0000:ff:00.0: [8086:2c41] type 0 class 0x000600
[    1.347948] pci 0000:ff:00.1: [8086:2c01] type 0 class 0x000600
[    1.347962] pci 0000:ff:02.0: [8086:2c10] type 0 class 0x000600
[    1.347975] pci 0000:ff:02.1: [8086:2c11] type 0 class 0x000600
[    1.347990] pci 0000:ff:03.0: [8086:2c18] type 0 class 0x000600
[    1.348002] pci 0000:ff:03.1: [8086:2c19] type 0 class 0x000600
[    1.348015] pci 0000:ff:03.4: [8086:2c1c] type 0 class 0x000600
[    1.348028] pci 0000:ff:04.0: [8086:2c20] type 0 class 0x000600
[    1.348040] pci 0000:ff:04.1: [8086:2c21] type 0 class 0x000600
[    1.348052] pci 0000:ff:04.2: [8086:2c22] type 0 class 0x000600
[    1.348064] pci 0000:ff:04.3: [8086:2c23] type 0 class 0x000600
[    1.348078] pci 0000:ff:05.0: [8086:2c28] type 0 class 0x000600
[    1.348091] pci 0000:ff:05.1: [8086:2c29] type 0 class 0x000600
[    1.348103] pci 0000:ff:05.2: [8086:2c2a] type 0 class 0x000600
[    1.348115] pci 0000:ff:05.3: [8086:2c2b] type 0 class 0x000600
[    1.348129] pci 0000:ff:06.0: [8086:2c30] type 0 class 0x000600
[    1.348141] pci 0000:ff:06.1: [8086:2c31] type 0 class 0x000600
[    1.348153] pci 0000:ff:06.2: [8086:2c32] type 0 class 0x000600
[    1.348165] pci 0000:ff:06.3: [8086:2c33] type 0 class 0x000600
[    1.348437] PCI: pci_cache_line_size set to 64 bytes
[    1.348538] reserve RAM buffer: 000000000009ec00 - 000000000009ffff 
[    1.348539] reserve RAM buffer: 00000000bf760000 - 00000000bfffffff 
[    1.348600] NetLabel: Initializing
[    1.348601] NetLabel:  domain hash size = 128
[    1.348602] NetLabel:  protocols = UNLABELED CIPSOv4
[    1.348611] NetLabel:  unlabeled traffic allowed by default
[    1.348638] HPET: 4 timers in total, 0 timers will be used for per-cpu timer
[    1.348642] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0
[    1.348645] hpet0: 4 comparators, 64-bit 14.318180 MHz counter
[    1.377732] Switching to clocksource hpet
[    1.381359] AppArmor: AppArmor Filesystem Enabled
[    1.381371] pnp: PnP ACPI init
[    1.381378] ACPI: bus type pnp registered
[    1.381442] pnp 00:00: [bus 00-ff]
[    1.381444] pnp 00:00: [io  0x0cf8-0x0cff]
[    1.381445] pnp 00:00: [io  0x0000-0x0cf7 window]
[    1.381446] pnp 00:00: [io  0x0d00-0xffff window]
[    1.381448] pnp 00:00: [mem 0x000a0000-0x000bffff window]
[    1.381449] pnp 00:00: [mem 0x000d0000-0x000dffff window]
[    1.381451] pnp 00:00: [mem 0xc0000000-0xdfffffff window]
[    1.381452] pnp 00:00: [mem 0xf0000000-0xfed8ffff window]
[    1.381482] pnp 00:00: Plug and Play ACPI device, IDs PNP0a08 PNP0a03 (active)
[    1.381488] pnp 00:01: [mem 0xfc000000-0xfcffffff]
[    1.381489] pnp 00:01: [mem 0xfd000000-0xfdffffff]
[    1.381491] pnp 00:01: [mem 0xfe000000-0xfebfffff]
[    1.381492] pnp 00:01: [mem 0xfec8a000-0xfec8afff]
[    1.381493] pnp 00:01: [mem 0xfed10000-0xfed10fff]
[    1.381528] system 00:01: [mem 0xfc000000-0xfcffffff] has been reserved
[    1.381529] system 00:01: [mem 0xfd000000-0xfdffffff] has been reserved
[    1.381531] system 00:01: [mem 0xfe000000-0xfebfffff] has been reserved
[    1.381533] system 00:01: [mem 0xfec8a000-0xfec8afff] has been reserved
[    1.381534] system 00:01: [mem 0xfed10000-0xfed10fff] has been reserved
[    1.381536] system 00:01: Plug and Play ACPI device, IDs PNP0c01 (active)
[    1.381556] pnp 00:02: [dma 4]
[    1.381565] Switched to NOHz mode on CPU #0
[    1.381571] pnp 00:02: [io  0x0000-0x000f]
[    1.381572] pnp 00:02: [io  0x0081-0x0083]
[    1.381573] pnp 00:02: [io  0x0087]
[    1.381576] pnp 00:02: [io  0x0089-0x008b]
[    1.381577] pnp 00:02: [io  0x008f]
[    1.381578] pnp 00:02: [io  0x00c0-0x00df]
[    1.381593] pnp 00:02: Plug and Play ACPI device, IDs PNP0200 (active)
[    1.381600] pnp 00:03: [io  0x0070-0x0071]
[    1.381608] pnp 00:03: [irq 8]
[    1.381612] Switched to NOHz mode on CPU #1
[    1.381617] Switched to NOHz mode on CPU #2
[    1.381622] pnp 00:03: Plug and Play ACPI device, IDs PNP0b00 (active)
[    1.381628] pnp 00:04: [io  0x0061]
[    1.381641] pnp 00:04: Plug and Play ACPI device, IDs PNP0800 (active)
[    1.381643] Switched to NOHz mode on CPU #3
[    1.381646] pnp 00:05: [io  0x00f0-0x00ff]
[    1.381650] pnp 00:05: [irq 13]
[    1.381660] Switched to NOHz mode on CPU #4
[    1.381664] Switched to NOHz mode on CPU #5
[    1.381679] pnp 00:05: Plug and Play ACPI device, IDs PNP0c04 (active)
[    1.381682] Switched to NOHz mode on CPU #6
[    1.381687] Switched to NOHz mode on CPU #7
[    1.381756] pnp 00:06: [io  0x0000-0xffffffffffffffff disabled]
[    1.381758] pnp 00:06: [io  0x0a00-0x0adf]
[    1.381759] pnp 00:06: [io  0x0ae0-0x0aef]
[    1.381792] system 00:06: [io  0x0a00-0x0adf] has been reserved
[    1.381794] system 00:06: [io  0x0ae0-0x0aef] has been reserved
[    1.381796] system 00:06: Plug and Play ACPI device, IDs PNP0c02 (active)
[    1.381865] pnp 00:07: [io  0x0010-0x001f]
[    1.381867] pnp 00:07: [io  0x0022-0x003f]
[    1.381868] pnp 00:07: [io  0x0044-0x005f]
[    1.381869] pnp 00:07: [io  0x0062-0x0063]
[    1.381870] pnp 00:07: [io  0x0065-0x006f]
[    1.381871] pnp 00:07: [io  0x0072-0x007f]
[    1.381872] pnp 00:07: [io  0x0080]
[    1.381873] pnp 00:07: [io  0x0084-0x0086]
[    1.381874] pnp 00:07: [io  0x0088]
[    1.381875] pnp 00:07: [io  0x008c-0x008e]
[    1.381877] pnp 00:07: [io  0x0090-0x009f]
[    1.381878] pnp 00:07: [io  0x00a2-0x00bf]
[    1.381879] pnp 00:07: [io  0x00e0-0x00ef]
[    1.381880] pnp 00:07: [io  0x04d0-0x04d1]
[    1.381881] pnp 00:07: [io  0x0800-0x087f]
[    1.381882] pnp 00:07: [io  0x0000-0xffffffffffffffff disabled]
[    1.381883] pnp 00:07: [io  0x0500-0x057f]
[    1.381885] pnp 00:07: [mem 0xfed1c000-0xfed1ffff]
[    1.381886] pnp 00:07: [mem 0xfed20000-0xfed3ffff]
[    1.381887] pnp 00:07: [mem 0xfed40000-0xfed8ffff]
[    1.381934] system 00:07: [io  0x04d0-0x04d1] has been reserved
[    1.381935] system 00:07: [io  0x0800-0x087f] has been reserved
[    1.381937] system 00:07: [io  0x0500-0x057f] has been reserved
[    1.381939] system 00:07: [mem 0xfed1c000-0xfed1ffff] has been reserved
[    1.381941] system 00:07: [mem 0xfed20000-0xfed3ffff] has been reserved
[    1.381942] system 00:07: [mem 0xfed40000-0xfed8ffff] has been reserved
[    1.381944] system 00:07: Plug and Play ACPI device, IDs PNP0c02 (active)
[    1.381979] pnp 00:08: [mem 0xfed00000-0xfed003ff]
[    1.381997] pnp 00:08: Plug and Play ACPI device, IDs PNP0103 (active)
[    1.382043] pnp 00:09: [io  0x0060]
[    1.382045] pnp 00:09: [io  0x0064]
[    1.382046] pnp 00:09: [mem 0xfec00000-0xfec00fff]
[    1.382047] pnp 00:09: [mem 0xfee00000-0xfee00fff]
[    1.382081] system 00:09: [mem 0xfec00000-0xfec00fff] could not be reserved
[    1.382083] system 00:09: [mem 0xfee00000-0xfee00fff] has been reserved
[    1.382085] system 00:09: Plug and Play ACPI device, IDs PNP0c02 (active)
[    1.382105] pnp 00:0a: [mem 0xe0000000-0xefffffff]
[    1.382138] system 00:0a: [mem 0xe0000000-0xefffffff] has been reserved
[    1.382140] system 00:0a: Plug and Play ACPI device, IDs PNP0c02 (active)
[    1.382264] pnp 00:0b: [mem 0x00000000-0x0009ffff]
[    1.382266] pnp 00:0b: [mem 0x000c0000-0x000cffff]
[    1.382267] pnp 00:0b: [mem 0x000e0000-0x000fffff]
[    1.382268] pnp 00:0b: [mem 0x00100000-0xbfffffff]
[    1.382269] pnp 00:0b: [mem 0xfed90000-0xffffffff]
[    1.382314] system 00:0b: [mem 0x00000000-0x0009ffff] could not be reserved
[    1.382316] system 00:0b: [mem 0x000c0000-0x000cffff] could not be reserved
[    1.382317] system 00:0b: [mem 0x000e0000-0x000fffff] could not be reserved
[    1.382319] system 00:0b: [mem 0x00100000-0xbfffffff] could not be reserved
[    1.382321] system 00:0b: [mem 0xfed90000-0xffffffff] could not be reserved
[    1.382323] system 00:0b: Plug and Play ACPI device, IDs PNP0c01 (active)
[    1.382403] pnp: PnP ACPI: found 12 devices
[    1.382404] ACPI: ACPI bus type pnp unregistered
[    1.390751] PCI: max bus depth: 1 pci_try_num: 2
[    1.390810] pci 0000:00:1c.4: BAR 15: assigned [mem 0xc0000000-0xc01fffff 64bit pref]
[    1.390812] pci 0000:00:1c.4: BAR 13: assigned [io  0x1000-0x1fff]
[    1.390814] pci 0000:00:1c.3: BAR 15: assigned [mem 0xc0200000-0xc03fffff 64bit pref]
[    1.390816] pci 0000:00:1c.0: BAR 14: assigned [mem 0xc0400000-0xc05fffff]
[    1.390818] pci 0000:00:1c.0: BAR 15: assigned [mem 0xc0600000-0xc07fffff 64bit pref]
[    1.390820] pci 0000:00:1c.0: BAR 13: assigned [io  0x2000-0x2fff]
[    1.390822] pci 0000:00:01.0: PCI bridge to [bus 09-09]
[    1.390823] pci 0000:00:01.0:   bridge window [io  disabled]
[    1.390826] pci 0000:00:01.0:   bridge window [mem disabled]
[    1.390829] pci 0000:00:01.0:   bridge window [mem pref disabled]
[    1.390833] pci 0000:00:03.0: PCI bridge to [bus 08-08]
[    1.390835] pci 0000:00:03.0:   bridge window [io  0xe000-0xefff]
[    1.390838] pci 0000:00:03.0:   bridge window [mem 0xfbf00000-0xfbffffff]
[    1.390841] pci 0000:00:03.0:   bridge window [mem 0xd0000000-0xdfffffff 64bit pref]
[    1.390845] pci 0000:00:07.0: PCI bridge to [bus 07-07]
[    1.390846] pci 0000:00:07.0:   bridge window [io  disabled]
[    1.390849] pci 0000:00:07.0:   bridge window [mem disabled]
[    1.390851] pci 0000:00:07.0:   bridge window [mem pref disabled]
[    1.390855] pci 0000:00:09.0: PCI bridge to [bus 06-06]
[    1.390856] pci 0000:00:09.0:   bridge window [io  disabled]
[    1.390859] pci 0000:00:09.0:   bridge window [mem disabled]
[    1.390861] pci 0000:00:09.0:   bridge window [mem pref disabled]
[    1.390865] pci 0000:00:1c.0: PCI bridge to [bus 05-05]
[    1.390867] pci 0000:00:1c.0:   bridge window [io  0x2000-0x2fff]
[    1.390871] pci 0000:00:1c.0:   bridge window [mem 0xc0400000-0xc05fffff]
[    1.390874] pci 0000:00:1c.0:   bridge window [mem 0xc0600000-0xc07fffff 64bit pref]
[    1.390878] pci 0000:00:1c.2: PCI bridge to [bus 04-04]
[    1.390880] pci 0000:00:1c.2:   bridge window [io  0xd000-0xdfff]
[    1.390884] pci 0000:00:1c.2:   bridge window [mem 0xfbe00000-0xfbefffff]
[    1.390887] pci 0000:00:1c.2:   bridge window [mem 0xcff00000-0xcfffffff 64bit pref]
[    1.390891] pci 0000:00:1c.3: PCI bridge to [bus 03-03]
[    1.390893] pci 0000:00:1c.3:   bridge window [io  0xc000-0xcfff]
[    1.390897] pci 0000:00:1c.3:   bridge window [mem 0xfbc00000-0xfbdfffff]
[    1.390900] pci 0000:00:1c.3:   bridge window [mem 0xc0200000-0xc03fffff 64bit pref]
[    1.390904] pci 0000:00:1c.4: PCI bridge to [bus 02-02]
[    1.390906] pci 0000:00:1c.4:   bridge window [io  0x1000-0x1fff]
[    1.390910] pci 0000:00:1c.4:   bridge window [mem 0xfb200000-0xfb9fffff]
[    1.390913] pci 0000:00:1c.4:   bridge window [mem 0xc0000000-0xc01fffff 64bit pref]
[    1.390917] pci 0000:00:1e.0: PCI bridge to [bus 01-01]
[    1.390919] pci 0000:00:1e.0:   bridge window [io  0xb000-0xbfff]
[    1.390923] pci 0000:00:1e.0:   bridge window [mem 0xfb000000-0xfb1fffff]
[    1.390926] pci 0000:00:1e.0:   bridge window [mem pref disabled]
[    1.390936] pci 0000:00:01.0: setting latency timer to 64
[    1.390941] pci 0000:00:03.0: setting latency timer to 64
[    1.390946] pci 0000:00:07.0: setting latency timer to 64
[    1.390951] pci 0000:00:09.0: setting latency timer to 64
[    1.390955] pci 0000:00:1c.0: enabling device (0104 -> 0107)
[    1.390968] pci 0000:00:1c.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    1.390970] pci 0000:00:1c.0: setting latency timer to 64
[    1.390978] pci 0000:00:1c.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    1.390981] pci 0000:00:1c.2: setting latency timer to 64
[    1.390988] pci 0000:00:1c.3: PCI INT D -> GSI 19 (level, low) -> IRQ 19
[    1.390991] pci 0000:00:1c.3: setting latency timer to 64
[    1.390995] pci 0000:00:1c.4: enabling device (0106 -> 0107)
[    1.390998] pci 0000:00:1c.4: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    1.391000] pci 0000:00:1c.4: setting latency timer to 64
[    1.391005] pci 0000:00:1e.0: setting latency timer to 64
[    1.391008] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
[    1.391010] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff]
[    1.391011] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
[    1.391012] pci_bus 0000:00: resource 7 [mem 0x000d0000-0x000dffff]
[    1.391014] pci_bus 0000:00: resource 8 [mem 0xc0000000-0xdfffffff]
[    1.391015] pci_bus 0000:00: resource 9 [mem 0xf0000000-0xfed8ffff]
[    1.391017] pci_bus 0000:08: resource 0 [io  0xe000-0xefff]
[    1.391018] pci_bus 0000:08: resource 1 [mem 0xfbf00000-0xfbffffff]
[    1.391019] pci_bus 0000:08: resource 2 [mem 0xd0000000-0xdfffffff 64bit pref]
[    1.391021] pci_bus 0000:05: resource 0 [io  0x2000-0x2fff]
[    1.391022] pci_bus 0000:05: resource 1 [mem 0xc0400000-0xc05fffff]
[    1.391024] pci_bus 0000:05: resource 2 [mem 0xc0600000-0xc07fffff 64bit pref]
[    1.391025] pci_bus 0000:04: resource 0 [io  0xd000-0xdfff]
[    1.391026] pci_bus 0000:04: resource 1 [mem 0xfbe00000-0xfbefffff]
[    1.391028] pci_bus 0000:04: resource 2 [mem 0xcff00000-0xcfffffff 64bit pref]
[    1.391029] pci_bus 0000:03: resource 0 [io  0xc000-0xcfff]
[    1.391031] pci_bus 0000:03: resource 1 [mem 0xfbc00000-0xfbdfffff]
[    1.391032] pci_bus 0000:03: resource 2 [mem 0xc0200000-0xc03fffff 64bit pref]
[    1.391033] pci_bus 0000:02: resource 0 [io  0x1000-0x1fff]
[    1.391035] pci_bus 0000:02: resource 1 [mem 0xfb200000-0xfb9fffff]
[    1.391036] pci_bus 0000:02: resource 2 [mem 0xc0000000-0xc01fffff 64bit pref]
[    1.391038] pci_bus 0000:01: resource 0 [io  0xb000-0xbfff]
[    1.391039] pci_bus 0000:01: resource 1 [mem 0xfb000000-0xfb1fffff]
[    1.391040] pci_bus 0000:01: resource 4 [io  0x0000-0x0cf7]
[    1.391042] pci_bus 0000:01: resource 5 [io  0x0d00-0xffff]
[    1.391043] pci_bus 0000:01: resource 6 [mem 0x000a0000-0x000bffff]
[    1.391044] pci_bus 0000:01: resource 7 [mem 0x000d0000-0x000dffff]
[    1.391046] pci_bus 0000:01: resource 8 [mem 0xc0000000-0xdfffffff]
[    1.391047] pci_bus 0000:01: resource 9 [mem 0xf0000000-0xfed8ffff]
[    1.391048] pci_bus 0000:ff: resource 0 [io  0x0000-0xffff]
[    1.391050] pci_bus 0000:ff: resource 1 [mem 0x00000000-0xfffffffff]
[    1.391083] NET: Registered protocol family 2
[    1.391356] IP route cache hash table entries: 524288 (order: 10, 4194304 bytes)
[    1.392241] TCP established hash table entries: 524288 (order: 11, 8388608 bytes)
[    1.393377] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[    1.393515] TCP: Hash tables configured (established 524288 bind 65536)
[    1.393516] TCP reno registered
[    1.393533] UDP hash table entries: 8192 (order: 6, 262144 bytes)
[    1.393586] UDP-Lite hash table entries: 8192 (order: 6, 262144 bytes)
[    1.393716] NET: Registered protocol family 1
[    1.393876] pci 0000:08:00.0: Boot video device
[    1.393908] PCI: CLS 256 bytes, default 64
[    1.393909] PCI-DMA: Using software bounce buffering for IO (SWIOTLB)
[    1.393911] Placing 64MB software IO TLB between ffff8800bb75b000 - ffff8800bf75b000
[    1.393912] software IO TLB at phys 0xbb75b000 - 0xbf75b000
[    1.394345] audit: initializing netlink socket (disabled)
[    1.394351] type=2000 audit(1324721380.096:1): initialized
[    1.420337] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    1.443103] VFS: Disk quotas dquot_6.5.2
[    1.443144] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    1.443570] fuse init (API version 7.16)
[    1.443631] msgmni has been set to 18003
[    1.443881] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    1.443903] io scheduler noop registered
[    1.443904] io scheduler deadline registered
[    1.443932] io scheduler cfq registered (default)
[    1.444139] pcieport 0000:00:1c.0: setting latency timer to 64
[    1.444175] pcieport 0000:00:1c.0: irq 40 for MSI/MSI-X
[    1.444221] pcieport 0000:00:1c.2: setting latency timer to 64
[    1.444252] pcieport 0000:00:1c.2: irq 41 for MSI/MSI-X
[    1.444295] pcieport 0000:00:1c.3: setting latency timer to 64
[    1.444326] pcieport 0000:00:1c.3: irq 42 for MSI/MSI-X
[    1.444370] pcieport 0000:00:1c.4: setting latency timer to 64
[    1.444401] pcieport 0000:00:1c.4: irq 43 for MSI/MSI-X
[    1.444457] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    1.444470] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    1.444497] intel_idle: MWAIT substates: 0x1120
[    1.444508] intel_idle: v0.4 model 0x1A
[    1.444508] intel_idle: lapic_timer_reliable_states 0x2
[    1.444601] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0
[    1.444605] ACPI: Power Button [PWRB]
[    1.444629] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
[    1.444631] ACPI: Power Button [PWRF]
[    1.444649] ACPI: acpi_idle yielding to intel_idle
[    1.445591] ERST: Table is not found!
[    1.445626] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    1.465926] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    1.541612] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[    1.641286] Linux agpgart interface v0.103
[    1.641955] brd: module loaded
[    1.642252] loop: module loaded
[    1.642349] pata_acpi 0000:03:00.1: enabling device (0000 -> 0001)
[    1.642359] pata_acpi 0000:03:00.1: PCI INT B -> GSI 16 (level, low) -> IRQ 16
[    1.642380] pata_acpi 0000:03:00.1: setting latency timer to 64
[    1.642390] pata_acpi 0000:03:00.1: PCI INT B disabled
[    1.642555] Fixed MDIO Bus: probed
[    1.642568] PPP generic driver version 2.4.2
[    1.642596] tun: Universal TUN/TAP device driver, 1.6
[    1.642597] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    1.642639] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    1.642649] ehci_hcd 0000:00:1a.7: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    1.642667] ehci_hcd 0000:00:1a.7: setting latency timer to 64
[    1.642670] ehci_hcd 0000:00:1a.7: EHCI Host Controller
[    1.642693] ehci_hcd 0000:00:1a.7: new USB bus registered, assigned bus number 1
[    1.642715] ehci_hcd 0000:00:1a.7: debug port 1
[    1.646588] ehci_hcd 0000:00:1a.7: cache line size of 256 is not supported
[    1.646600] ehci_hcd 0000:00:1a.7: irq 18, io mem 0xfa800000
[    1.660977] ehci_hcd 0000:00:1a.7: USB 2.0 started, EHCI 1.00
[    1.661093] hub 1-0:1.0: USB hub found
[    1.661095] hub 1-0:1.0: 6 ports detected
[    1.661152] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    1.661160] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    1.661163] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    1.661185] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 2
[    1.661204] ehci_hcd 0000:00:1d.7: debug port 1
[    1.665067] ehci_hcd 0000:00:1d.7: cache line size of 256 is not supported
[    1.665076] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xfaa00000
[    1.680928] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    1.681034] hub 2-0:1.0: USB hub found
[    1.681036] hub 2-0:1.0: 6 ports detected
[    1.681087] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    1.681095] uhci_hcd: USB Universal Host Controller Interface driver
[    1.681109] uhci_hcd 0000:00:1a.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.681113] uhci_hcd 0000:00:1a.0: setting latency timer to 64
[    1.681116] uhci_hcd 0000:00:1a.0: UHCI Host Controller
[    1.681138] uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 3
[    1.681166] uhci_hcd 0000:00:1a.0: irq 16, io base 0x00009400
[    1.681234] hub 3-0:1.0: USB hub found
[    1.681236] hub 3-0:1.0: 2 ports detected
[    1.681282] uhci_hcd 0000:00:1a.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[    1.681286] uhci_hcd 0000:00:1a.1: setting latency timer to 64
[    1.681289] uhci_hcd 0000:00:1a.1: UHCI Host Controller
[    1.681310] uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus number 4
[    1.681336] uhci_hcd 0000:00:1a.1: irq 21, io base 0x00009480
[    1.681404] hub 4-0:1.0: USB hub found
[    1.681408] hub 4-0:1.0: 2 ports detected
[    1.681450] uhci_hcd 0000:00:1a.2: PCI INT D -> GSI 19 (level, low) -> IRQ 19
[    1.681454] uhci_hcd 0000:00:1a.2: setting latency timer to 64
[    1.681456] uhci_hcd 0000:00:1a.2: UHCI Host Controller
[    1.681475] uhci_hcd 0000:00:1a.2: new USB bus registered, assigned bus number 5
[    1.681502] uhci_hcd 0000:00:1a.2: irq 19, io base 0x00009800
[    1.681571] hub 5-0:1.0: USB hub found
[    1.681574] hub 5-0:1.0: 2 ports detected
[    1.681616] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    1.681620] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    1.681622] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    1.681642] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 6
[    1.681663] uhci_hcd 0000:00:1d.0: irq 23, io base 0x00009880
[    1.681733] hub 6-0:1.0: USB hub found
[    1.681735] hub 6-0:1.0: 2 ports detected
[    1.681777] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    1.681783] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    1.681785] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    1.681810] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 7
[    1.681830] uhci_hcd 0000:00:1d.1: irq 19, io base 0x00009c00
[    1.681904] hub 7-0:1.0: USB hub found
[    1.681906] hub 7-0:1.0: 2 ports detected
[    1.681947] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    1.681951] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    1.681953] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    1.681973] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 8
[    1.681993] uhci_hcd 0000:00:1d.2: irq 18, io base 0x0000a000
[    1.682060] hub 8-0:1.0: USB hub found
[    1.682062] hub 8-0:1.0: 2 ports detected
[    1.682126] i8042: PNP: No PS/2 controller found. Probing ports directly.
[    1.684378] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.684381] serio: i8042 AUX port at 0x60,0x64 irq 12
[    1.684445] mousedev: PS/2 mouse device common for all mice
[    1.684512] rtc_cmos 00:03: RTC can wake from S4
[    1.684584] rtc_cmos 00:03: rtc core: registered rtc_cmos as rtc0
[    1.684606] rtc0: alarms up to one month, y3k, 114 bytes nvram, hpet irqs
[    1.684666] device-mapper: uevent: version 1.0.3
[    1.684711] device-mapper: ioctl: 4.20.0-ioctl (2011-02-02) initialised: [email]dm-devel@redhat.com[/email]
[    1.684820] cpuidle: using governor ladder
[    1.685044] cpuidle: using governor menu
[    1.685046] EFI Variables Facility v0.08 2004-May-17
[    1.685194] TCP cubic registered
[    1.685272] NET: Registered protocol family 10
[    1.685584] NET: Registered protocol family 17
[    1.685593] Registering the dns_resolver key type
[    1.685649] PM: Hibernation image not present or could not be loaded.
[    1.685654] registered taskstats version 1
[    1.701437]   Magic number: 7:516:174
[    1.701480] acpi device:37: hash matches
[    1.701487] acpi device:0a: hash matches
[    1.701712] rtc_cmos 00:03: setting system clock to 2011-12-24 10:09:40 UTC (1324721380)
[    1.706491] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.706493] EDD information not available.
[    1.708033] Freeing unused kernel memory: 984k freed
[    1.708145] Write protecting the kernel read-only data: 10240k
[    1.708588] Freeing unused kernel memory: 20k freed
[    1.711719] Freeing unused kernel memory: 1400k freed
[    1.727580] udevd[104]: starting version 173
[    1.748001] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    1.748021] r8169 0000:04:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    1.748059] r8169 0000:04:00.0: setting latency timer to 64
[    1.748118] r8169 0000:04:00.0: irq 44 for MSI/MSI-X
[    1.748136] pata_jmicron 0000:03:00.1: PCI INT B -> GSI 16 (level, low) -> IRQ 16
[    1.748163] pata_jmicron 0000:03:00.1: setting latency timer to 64
[    1.748462] scsi0 : pata_jmicron
[    1.748482] r8169 0000:04:00.0: eth0: RTL8168c/8111c at 0xffffc90001874000, a4:ba:db:02:c8:f1, XID 1c4000c0 IRQ 44
[    1.748580] scsi1 : pata_jmicron
[    1.748850] ahci 0000:00:1f.2: version 3.0
[    1.748872] ahci 0000:00:1f.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    1.749003] ata1: PATA max UDMA/100 cmd 0xcc00 ctl 0xc880 bmdma 0xc400 irq 16
[    1.749005] ata2: PATA max UDMA/100 cmd 0xc800 ctl 0xc480 bmdma 0xc408 irq 16
[    1.749064] ahci 0000:00:1f.2: irq 45 for MSI/MSI-X
[    1.749096] ahci: SSS flag set, parallel bus scan disabled
[    1.749138] ahci 0000:00:1f.2: AHCI 0001.0200 32 slots 6 ports 3 Gbps 0x3f impl SATA mode
[    1.749141] ahci 0000:00:1f.2: flags: 64bit ncq sntf stag pm led clo pio slum part ccc ems sxs 
[    1.749146] ahci 0000:00:1f.2: setting latency timer to 64
[    1.789486] scsi2 : ahci
[    1.789611] scsi3 : ahci
[    1.789696] scsi4 : ahci
[    1.789852] scsi5 : ahci
[    1.789932] scsi6 : ahci
[    1.790014] scsi7 : ahci
[    1.790113] ata3: SATA max UDMA/133 abar m2048@0xfac00000 port 0xfac00100 irq 45
[    1.790115] ata4: SATA max UDMA/133 abar m2048@0xfac00000 port 0xfac00180 irq 45
[    1.790117] ata5: SATA max UDMA/133 abar m2048@0xfac00000 port 0xfac00200 irq 45
[    1.790119] ata6: SATA max UDMA/133 abar m2048@0xfac00000 port 0xfac00280 irq 45
[    1.790121] ata7: SATA max UDMA/133 abar m2048@0xfac00000 port 0xfac00300 irq 45
[    1.790123] ata8: SATA max UDMA/133 abar m2048@0xfac00000 port 0xfac00380 irq 45
[    1.790144] ahci 0000:03:00.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    1.804881] ahci 0000:03:00.0: AHCI 0001.0000 32 slots 2 ports 3 Gbps 0x3 impl SATA mode
[    1.804887] ahci 0000:03:00.0: flags: 64bit ncq pm led clo pmp pio slum part 
[    1.804894] ahci 0000:03:00.0: setting latency timer to 64
[    1.805289] scsi8 : ahci
[    1.805467] scsi9 : ahci
[    1.805594] ata9: SATA max UDMA/133 abar m8192@0xfbc00000 port 0xfbc00100 irq 19
[    1.805599] ata10: SATA max UDMA/133 abar m8192@0xfbc00000 port 0xfbc00180 irq 19
[    2.088031] usb 2-3: new high speed USB device number 2 using ehci_hcd
[    2.107986] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    2.111725] ata3.00: ATAPI: HL-DT-ST DVD-ROM DH20N, A102, max UDMA/100
[    2.112638] ata3.00: configured for UDMA/100
[    2.118966] scsi 2:0:0:0: CD-ROM            HL-DT-ST DVD-ROM DH20N    A102 PQ: 0 ANSI: 5
[    2.121843] sr0: scsi3-mmc drive: 12x/48x cd/rw xa/form2 cdda tray
[    2.121847] cdrom: Uniform CD-ROM driver Revision: 3.20
[    2.121965] sr 2:0:0:0: Attached scsi CD-ROM sr0
[    2.122021] sr 2:0:0:0: Attached scsi generic sg0 type 5
[    2.124012] ata9: SATA link down (SStatus 0 SControl 300)
[    2.124050] ata10: SATA link down (SStatus 0 SControl 300)
[    2.391257] Refined TSC clocksource calibration: 3191.999 MHz.
[    2.391263] Switching to clocksource tsc
[    2.439151] ata4: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    2.439695] ata4.00: ATAPI: TSSTcorp DVD+/-RW TS-H653G, DW10, max UDMA/100
[    2.439700] ata4.00: applying bridge limits
[    2.440442] ata4.00: configured for UDMA/100
[    2.441872] scsi 3:0:0:0: CD-ROM            TSSTcorp DVD+-RW TS-H653G DW10 PQ: 0 ANSI: 5
[    2.444109] sr1: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
[    2.444214] sr 3:0:0:0: Attached scsi CD-ROM sr1
[    2.444272] sr 3:0:0:0: Attached scsi generic sg1 type 5
[    2.762334] ata5: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    2.776718] usbcore: registered new interface driver uas
[    2.791091] ata5.00: ATA-8: ST31500341AS, CC4G, max UDMA/133
[    2.791095] ata5.00: 2930277168 sectors, multi 0: LBA48 NCQ (depth 31/32)
[    2.833004] ata5.00: configured for UDMA/133
[    2.833120] scsi 4:0:0:0: Direct-Access     ATA      ST31500341AS     CC4G PQ: 0 ANSI: 5
[    2.833237] sd 4:0:0:0: [sda] 2930277168 512-byte logical blocks: (1.50 TB/1.36 TiB)
[    2.833251] sd 4:0:0:0: Attached scsi generic sg2 type 0
[    2.833280] sd 4:0:0:0: [sda] Write Protect is off
[    2.833282] sd 4:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    2.833298] sd 4:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.886446]  sda: sda1 sda2 < sda5 sda6 > sda3
[    2.886974] sd 4:0:0:0: [sda] Attached SCSI disk
[    2.949982] usb 2-5: new high speed USB device number 4 using ehci_hcd
[    3.084825] Initializing USB Mass Storage driver...
[    3.084909] scsi10 : usb-storage 2-3:1.0
[    3.085094] scsi11 : usb-storage 2-5:1.0
[    3.085238] usbcore: registered new interface driver usb-storage
[    3.085239] USB Mass Storage support registered.
[    3.153306] ata6: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    3.182013] ata6.00: ATA-8: ST31500341AS, CC4G, max UDMA/133
[    3.182017] ata6.00: 2930277168 sectors, multi 0: LBA48 NCQ (depth 31/32)
[    3.193211] usb 2-6: new high speed USB device number 5 using ehci_hcd
[    3.223905] ata6.00: configured for UDMA/133
[    3.224056] scsi 5:0:0:0: Direct-Access     ATA      ST31500341AS     CC4G PQ: 0 ANSI: 5
[    3.224144] sd 5:0:0:0: [sdb] 2930277168 512-byte logical blocks: (1.50 TB/1.36 TiB)
[    3.224163] sd 5:0:0:0: Attached scsi generic sg3 type 0
[    3.224191] sd 5:0:0:0: [sdb] Write Protect is off
[    3.224194] sd 5:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[    3.224294] sd 5:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    3.243584]  sdb: sdb1
[    3.244029] sd 5:0:0:0: [sdb] Attached SCSI disk
[    3.342891] scsi12 : usb-storage 2-6:1.0
[    3.407952] EXT4-fs (sda5): mounted filesystem with ordered data mode. Opts: (null)
[    3.544441] ata7: SATA link down (SStatus 0 SControl 300)
[    3.580453] usb 5-2: new full speed USB device number 2 using uhci_hcd
[    3.863550] ata8: SATA link down (SStatus 0 SControl 300)
[    3.865565] firewire_ohci 0000:02:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    3.865572] firewire_ohci 0000:02:00.0: setting latency timer to 64
[    3.927621] firewire_ohci: Added fw-ohci device 0000:02:00.0, OHCI v1.10, 4 IR + 4 IT contexts, quirks 0x10
[    4.003372] usb 7-2: new low speed USB device number 2 using uhci_hcd
[    4.080071] scsi 11:0:0:0: Direct-Access     WDC      WD800BB-00JHA0   05.0 PQ: 0 ANSI: 2
[    4.085791] scsi 10:0:0:0: Direct-Access     Generic- Compact Flash    1.00 PQ: 0 ANSI: 0 CCS
[    4.092185] scsi 10:0:0:1: Direct-Access     Generic- SM/xD-Picture    1.00 PQ: 0 ANSI: 0 CCS
[    4.098509] scsi 10:0:0:2: Direct-Access     Generic- SD/MMC           1.00 PQ: 0 ANSI: 0 CCS
[    4.104891] scsi 10:0:0:3: Direct-Access     Generic- MS/MS-Pro        1.00 PQ: 0 ANSI: 0 CCS
[    4.373919] scsi 12:0:0:0: Direct-Access     Maxtor   3200             0344 PQ: 0 ANSI: 4
[    4.430236] firewire_core: created device fw0: GUID 0010dc0001a33546, S400
[    4.605872] sd 11:0:0:0: Attached scsi generic sg4 type 0
[    4.606103] sd 10:0:0:0: Attached scsi generic sg5 type 0
[    4.606175] sd 10:0:0:1: Attached scsi generic sg6 type 0
[    4.606254] sd 10:0:0:2: Attached scsi generic sg7 type 0
[    4.606327] sd 10:0:0:3: Attached scsi generic sg8 type 0
[    4.606559] sd 11:0:0:0: [sdc] 156301488 512-byte logical blocks: (80.0 GB/74.5 GiB)
[    4.607300] sd 11:0:0:0: [sdc] Write Protect is off
[    4.607305] sd 11:0:0:0: [sdc] Mode Sense: 53 00 00 08
[    4.608020] sd 11:0:0:0: [sdc] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    4.613528] sd 10:0:0:0: [sdd] Attached SCSI removable disk
[    4.614411] sd 10:0:0:3: [sdg] Attached SCSI removable disk
[    4.614519]  sdc: sdc1
[    4.615306] sd 10:0:0:2: [sdf] Attached SCSI removable disk
[    4.616120] sd 10:0:0:1: [sde] Attached SCSI removable disk
[    4.617243] sd 11:0:0:0: [sdc] Attached SCSI disk
[    4.889131] sd 12:0:0:0: Attached scsi generic sg9 type 0
[    4.889950] sd 12:0:0:0: [sdh] 976773168 512-byte logical blocks: (500 GB/465 GiB)
[    4.890803] sd 12:0:0:0: [sdh] Write Protect is off
[    4.890805] sd 12:0:0:0: [sdh] Mode Sense: 17 00 00 00
[    4.891680] sd 12:0:0:0: [sdh] No Caching mode page present
[    4.891683] sd 12:0:0:0: [sdh] Assuming drive cache: write through
[    4.894298] sd 12:0:0:0: [sdh] No Caching mode page present
[    4.894301] sd 12:0:0:0: [sdh] Assuming drive cache: write through
[    4.895931]  sdh: sdh1
[    4.899160] sd 12:0:0:0: [sdh] No Caching mode page present
[    4.899164] sd 12:0:0:0: [sdh] Assuming drive cache: write through
[    4.899167] sd 12:0:0:0: [sdh] Attached SCSI disk
[   17.706000] udevd[387]: starting version 173
[   17.820686] Adding 9426940k swap on /dev/sda6.  Priority:-1 extents:1 across:9426940k 
[   17.997031] lp: driver loaded but no devices found
[   18.367661] EXT4-fs (sda5): re-mounted. Opts: errors=remount-ro
[   18.370690] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
[   18.370694] Disabling lock debugging due to kernel taint
[   18.406771] [fglrx] Maximum main memory to use for locked dma buffers: 8753 MBytes.
[   18.406900] [fglrx]   vendor: 1002 device: 6898 count: 1
[   18.408060] [fglrx] ioport: bar 4, base 0xe000, size: 0x100
[   18.408073] pci 0000:08:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   18.408078] pci 0000:08:00.0: setting latency timer to 64
[   18.408833] [fglrx] Kernel PAT support is enabled
[   18.408846] [fglrx] module loaded - fglrx 8.92.6 [Nov  9 2011] with 1 minors
[   18.427188] EDAC MC: Ver: 2.1.0
[   18.443428] wmi: Mapper loaded
[   18.528746] EDAC MC0: Giving out device to 'i7core_edac.c' 'i7 core #0': DEV 0000:ff:03.0
[   18.528762] EDAC PCI0: Giving out device to module 'i7core_edac' controller 'EDAC PCI controller': DEV '0000:ff:03.0' (POLLED)
[   18.528764] EDAC i7core: Driver loaded.
[   18.530265] dcdbas dcdbas: Dell Systems Management Base Driver (version 5.6.0-3.2)
[   18.581092] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[   18.581132] HDA Intel 0000:00:1b.0: irq 46 for MSI/MSI-X
[   18.581150] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   18.624946] hda_codec: ALC1200: BIOS auto-probing.
[   18.630794] input: HDA Intel Headphone as /devices/pci0000:00/0000:00:1b.0/sound/card0/input2
[   18.630944] HDA Intel 0000:08:00.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[   18.631151] HDA Intel 0000:08:00.1: irq 47 for MSI/MSI-X
[   18.631169] HDA Intel 0000:08:00.1: setting latency timer to 64
[   18.649071] HDMI status: Pin=3 Presence_Detect=0 ELD_Valid=0
[   18.649147] input: HD-Audio Generic HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:03.0/0000:08:00.1/sound/card1/input3
[   18.782788] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:1a.2/usb5/5-2/5-2:1.0/input/input4
[   18.782856] generic-usb 0003:046D:C52B.0001: input,hidraw0: USB HID v1.11 Keyboard [Logitech USB Receiver] on usb-0000:00:1a.2-2/input0
[   18.785960] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:1a.2/usb5/5-2/5-2:1.1/input/input5
[   18.786198] generic-usb 0003:046D:C52B.0002: input,hiddev0,hidraw1: USB HID v1.11 Mouse [Logitech USB Receiver] on usb-0000:00:1a.2-2/input1
[   18.791800] generic-usb 0003:046D:C52B.0003: hiddev0,hidraw2: USB HID v1.11 Device [Logitech USB Receiver] on usb-0000:00:1a.2-2/input2
[   18.791809] usbcore: registered new interface driver usbhid
[   18.791810] usbhid: USB HID core driver
[   19.716434] vesafb: mode is 640x480x32, linelength=2560, pages=0
[   19.716436] vesafb: scrolling: redraw
[   19.716438] vesafb: Truecolor: size=0:8:8:8, shift=0:16:8:0
[   19.719080] vesafb: framebuffer at 0xd0000000, mapped to 0xffffc90012600000, using 1216k, total 1216k
[   19.719196] Console: switching to colour frame buffer device 80x30
[   19.719210] fb0: VESA VGA frame buffer device
[   26.778467] ppdev: user-space parallel port driver
[   26.780137] parport0: PC-style at 0x378 (0x778) [PCSPP,TRISTATE,EPP]
[   26.780675] parport0: irq 7 detected
[   26.817123] r8169 0000:04:00.0: eth0: link down
[   26.817128] r8169 0000:04:00.0: eth0: link down
[   26.818246] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   26.874055] lp0: using parport0 (polling).
[   28.237019] init: failsafe main process (976) killed by TERM signal
[   28.343500] init: apport pre-start process (1265) terminated with status 1
[   28.345453] init: apport post-stop process (1300) terminated with status 1
```

---

### Post by bobsageek on 2011-12-24
So /dev/sdg1 is an ntfs volume, so are you dual booting? Have an external drive you plug in that is NTFS formatted? Or mapping a drive from another machine (least likely since these are usually CIFS volumes)? But I think we can safely say that the mouse/keyboard has little to do with your issue.

dmesg shows  [sdg] Attached SCSI removable disk, and fstab shows it's ntfs, so the fix is to keep it from automounting during boot, but we need more info.

---

### Post by chazdg24 on 2011-12-24
Dual booting with Windows 7, Two ntfs external hard drives.  You are probably correct, however, I never received that message until I plugged in the new Logitech keyboard/mouse.  Thanks for your help!

---

### Post by chazdg24 on 2011-12-24
OK, I installed gparted and the interesting thing is that there is no sdg1 partition on my computer.  Any ideas?

---

### Post by bobsageek on 2011-12-24
If it's not ready at boot it might not be mounted now, but at some point an NTFS device was mounted on your PC as /dev/sdg1. If you are sure you don't need it for any reason, comment out that line in /etc/fstab (using # symbol) and see if it presents any issues on reboot. Smartest move, first do a ```
sudo cp /etc/fstab /etc/fstab.bkup
``` so you have a safe failback. But before you do any of that, make sure you have a backup of your data just in case things go poorly.

---

### Post by chazdg24 on 2011-12-24
I did as you suggested.  Rebooted and instead of "sdg", I got the same message but with "sdd".  I went back into fstab, made a backup and commented sdd out of fstab.  It worked...

I have no idea what is going on but the problem is gone for now.  Thanks for your help, hopefully this puts an end to it!

Gotta go, family is arriving for the holiday, yuck.

---

### Post by bobsageek on 2011-12-25
Glad it worked, technically we should clean it up and either remove those partitions or set them to *noauto* so they don't try to mount on boot, but for now at the least the main part of your issue is resolved.

---

### Post by chazdg24 on 2011-12-25
If you give me an idea what to do, I would go and take care of that.  Thanks again.

---

