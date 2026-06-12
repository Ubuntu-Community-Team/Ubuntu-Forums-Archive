---
title: "Accessing stranded encrypted /home partition"
date: 2012-03-02
forum: General Help
---

### Post by Waldotherogue on 2012-03-02
Hey everyone,
I'm attempting to rescue my encrypted /home partition via livecd from 
a drive which is growing bad sectors. I can not figure out how to 
mount the partition, which I encrypted just using ubuntu standard
encryption. I think it was just a tickbox I checked to do this.
GParted sees a logical volume with unallocated space as expected.
However, when I try boot from the bad disk, it says "the disk for /home
is not ready yet" or something similar. Since the partition isn't
being recognized, there's no "access your private data" or whatever
within the home folder.
 
I've tried using cryptsetup, ecrypt-rescue-private, and a number of other methods suggested by friends
who have a bit more linux experience than I. I've included a screenshot
of GParted as well as the contents of fstab and mtab while running the livecd. I've also included the full output of dmesg. 
 
Since I live in a rural area, I'm using a public computer to post so most likely 
I'll only be able to respond to suggestions and report with results
the following day.
I'm sure the integrity of the data is intact, I just can't access it.
Please suggest anything you can think of. Thanks in advance :D
 
GParted - [http://i.imgur.com/BuNeL.png](http://i.imgur.com/BuNeL.png)
 
FSTAB============================
ubuntu@ubuntu:~$ sudo cat '/media/df7355b1-761d-43bb-ac72-28780ac0c52a/etc/fstab' 
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point> <type> <options> <dump> <pass>
proc /proc proc nodev,noexec,nosuid 0 0
# / was on /dev/sda1 during installation
UUID=df7355b1-761d-43bb-ac72-28780ac0c52a / ext4 errors=remount-ro 0 1
# /home was on /dev/sda5 during installation
UUID=ab7608b8-ceb4-4b14-a34a-29fb27375597 /home ext4 defaults 0 2
# swap was on /dev/sda6 during installation
UUID=e69e78bb-3396-4388-afe0-2c3c64041e5b none swap sw 0 0
/dev/fd0 /media/floppy0 auto rw,user,noauto,exec,utf8 0 0
MTAB===========================
ubuntu@ubuntu:~$ sudo cat '/media/df7355b1-761d-43bb-ac72-28780ac0c52a/etc/mtab' 
/dev/sdb1 / ext4 rw,errors=remount-ro 0 0
proc /proc proc rw,noexec,nosuid,nodev 0 0
none /sys sysfs rw,noexec,nosuid,nodev 0 0
none /dev devtmpfs rw,mode=0755 0 0
none /dev/pts devpts rw,noexec,nosuid,gid=5,mode=0620 0 0
none /dev/shm tmpfs rw,nosuid,nodev 0 0
none /var/run tmpfs rw,nosuid,mode=0755 0 0
none /var/lock tmpfs rw,noexec,nosuid,nodev 0 0
none /lib/init/rw tmpfs rw,nosuid,mode=0755 0 0
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw,noexec,nosuid,nodev 0 0
DMESG====================
[ 0.000000] Initializing cgroup subsys cpuset
[ 0.000000] Initializing cgroup subsys cpu
[ 0.000000] Linux version 2.6.32-38-generic (buildd@zirconium) (gcc version 4.4.3 (Ubuntu 4.4.3-4ubuntu5) ) #83-Ubuntu SMP Wed Jan 4 11:13:04 UTC 2012 (Ubuntu 2.6.32-38.83-generic 2.6.32.52+drm33.21)
[ 0.000000] KERNEL supported cpus:
[ 0.000000] Intel GenuineIntel
[ 0.000000] AMD AuthenticAMD
[ 0.000000] NSC Geode by NSC
[ 0.000000] Cyrix CyrixInstead
[ 0.000000] Centaur CentaurHauls
[ 0.000000] Transmeta GenuineTMx86
[ 0.000000] Transmeta TransmetaCPU
[ 0.000000] UMC UMC UMC UMC
[ 0.000000] BIOS-provided physical RAM map:
[ 0.000000] BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[ 0.000000] BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[ 0.000000] BIOS-e820: 00000000000e4000 - 0000000000100000 (reserved)
[ 0.000000] BIOS-e820: 0000000000100000 - 000000007f7b0000 (usable)
[ 0.000000] BIOS-e820: 000000007f7b0000 - 000000007f7c0000 (ACPI data)
[ 0.000000] BIOS-e820: 000000007f7c0000 - 000000007f7f0000 (ACPI NVS)
[ 0.000000] BIOS-e820: 000000007f7f0000 - 000000007f800000 (reserved)
[ 0.000000] BIOS-e820: 00000000fed00000 - 00000000fed00400 (reserved)
[ 0.000000] BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[ 0.000000] BIOS-e820: 00000000ff380000 - 0000000100000000 (reserved)
[ 0.000000] DMI present.
[ 0.000000] AMI BIOS detected: BIOS may corrupt low RAM, working around it.
[ 0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
[ 0.000000] last_pfn = 0x7f7b0 max_arch_pfn = 0x100000
[ 0.000000] MTRR default type: uncachable
[ 0.000000] MTRR fixed ranges enabled:
[ 0.000000] 00000-9FFFF write-back
[ 0.000000] A0000-DFFFF uncachable
[ 0.000000] E0000-EFFFF write-through
[ 0.000000] F0000-FFFFF write-protect
[ 0.000000] MTRR variable ranges enabled:
[ 0.000000] 0 base 000000000 mask F80000000 write-back
[ 0.000000] 1 base 07F800000 mask FFF800000 uncachable
[ 0.000000] 2 disabled
[ 0.000000] 3 disabled
[ 0.000000] 4 disabled
[ 0.000000] 5 disabled
[ 0.000000] 6 disabled
[ 0.000000] 7 disabled
[ 0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[ 0.000000] Scanning 0 areas for low memory corruption
[ 0.000000] modified physical RAM map:
[ 0.000000] modified: 0000000000000000 - 0000000000010000 (reserved)
[ 0.000000] modified: 0000000000010000 - 000000000009fc00 (usable)
[ 0.000000] modified: 000000000009fc00 - 00000000000a0000 (reserved)
[ 0.000000] modified: 00000000000e4000 - 0000000000100000 (reserved)
[ 0.000000] modified: 0000000000100000 - 000000007f7b0000 (usable)
[ 0.000000] modified: 000000007f7b0000 - 000000007f7c0000 (ACPI data)
[ 0.000000] modified: 000000007f7c0000 - 000000007f7f0000 (ACPI NVS)
[ 0.000000] modified: 000000007f7f0000 - 000000007f800000 (reserved)
[ 0.000000] modified: 00000000fed00000 - 00000000fed00400 (reserved)
[ 0.000000] modified: 00000000fee00000 - 00000000fee01000 (reserved)
[ 0.000000] modified: 00000000ff380000 - 0000000100000000 (reserved)
[ 0.000000] initial memory mapped : 0 - 00c00000
[ 0.000000] init_memory_mapping: 0000000000000000-00000000377fe000
[ 0.000000] Using x86 segment limits to approximate NX protection
[ 0.000000] 0000000000 - 0000400000 page 4k
[ 0.000000] 0000400000 - 0037400000 page 2M
[ 0.000000] 0037400000 - 00377fe000 page 4k
[ 0.000000] kernel direct mapping tables up to 377fe000 @ 10000-15000
[ 0.000000] RAMDISK: 7ee84000 - 7f77fc7b
[ 0.000000] Allocated new RAMDISK: 008e8000 - 011e3c7b
[ 0.000000] Move RAMDISK from 000000007ee84000 - 000000007f77fc7a to 008e8000 - 011e3c7a
[ 0.000000] ACPI: RSDP 000f91e0 00014 (v00 ACPIAM)
[ 0.000000] ACPI: RSDT 7f7b0000 00034 (v01 A_M_I OEMRSDT 02000705 MSFT 00000097)
[ 0.000000] ACPI: FACP 7f7b0200 00084 (v02 A M I OEMFACP 12000601 MSFT 00000097)
[ 0.000000] ACPI: DSDT 7f7b0440 04ACF (v01 ASR21 ASR21101 00000101 INTL 02002026)
[ 0.000000] ACPI: FACS 7f7c0000 00040
[ 0.000000] ACPI: APIC 7f7b0390 0006C (v01 A_M_I OEMAPIC 02000705 MSFT 00000097)
[ 0.000000] ACPI: MCFG 7f7b0400 0003C (v01 A_M_I OEMMCFG 02000705 MSFT 00000097)
[ 0.000000] ACPI: OEMB 7f7c0040 00046 (v01 A_M_I AMI_OEM 02000705 MSFT 00000097)
[ 0.000000] ACPI: Local APIC address 0xfee00000
[ 0.000000] 1151MB HIGHMEM available.
[ 0.000000] 887MB LOWMEM available.
[ 0.000000] mapped low ram: 0 - 377fe000
[ 0.000000] low ram: 0 - 377fe000
[ 0.000000] node 0 low ram: 00000000 - 377fe000
[ 0.000000] node 0 bootmap 00011000 - 00017f00
[ 0.000000] (9 early reservations) ==> bootmem [0000000000 - 00377fe000]
[ 0.000000] #0 [0000000000 - 0000001000] BIOS data page ==> [0000000000 - 0000001000]
[ 0.000000] #1 [0000001000 - 0000002000] EX TRAMPOLINE ==> [0000001000 - 0000002000]
[ 0.000000] #2 [0000006000 - 0000007000] TRAMPOLINE ==> [0000006000 - 0000007000]
[ 0.000000] #3 [0000100000 - 00008e3f18] TEXT DATA BSS ==> [0000100000 - 00008e3f18]
[ 0.000000] #4 [000009fc00 - 0000100000] BIOS reserved ==> [000009fc00 - 0000100000]
[ 0.000000] #5 [00008e4000 - 00008e712f] BRK ==> [00008e4000 - 00008e712f]
[ 0.000000] #6 [0000010000 - 0000011000] PGTABLE ==> [0000010000 - 0000011000]
[ 0.000000] #7 [00008e8000 - 00011e3c7b] NEW RAMDISK ==> [00008e8000 - 00011e3c7b]
[ 0.000000] #8 [0000011000 - 0000018000] BOOTMAP ==> [0000011000 - 0000018000]
[ 0.000000] found SMP MP-table at [c00ff780] ff780
[ 0.000000] Zone PFN ranges:
[ 0.000000] DMA 0x00000010 -> 0x00001000
[ 0.000000] Normal 0x00001000 -> 0x000377fe
[ 0.000000] HighMem 0x000377fe -> 0x0007f7b0
[ 0.000000] Movable zone start PFN for each node
[ 0.000000] early_node_map[2] active PFN ranges
[ 0.000000] 0: 0x00000010 -> 0x0000009f
[ 0.000000] 0: 0x00000100 -> 0x0007f7b0
[ 0.000000] On node 0 totalpages: 522047
[ 0.000000] free_area_init_node: node 0, pgdat c079e9c0, node_mem_map c11e5200
[ 0.000000] DMA zone: 32 pages used for memmap
[ 0.000000] DMA zone: 0 pages reserved
[ 0.000000] DMA zone: 3951 pages, LIFO batch:0
[ 0.000000] Normal zone: 1744 pages used for memmap
[ 0.000000] Normal zone: 221486 pages, LIFO batch:31
[ 0.000000] HighMem zone: 2304 pages used for memmap
[ 0.000000] HighMem zone: 292530 pages, LIFO batch:31
[ 0.000000] Using APIC driver default
[ 0.000000] ACPI: PM-Timer IO Port: 0x808
[ 0.000000] ACPI: Local APIC address 0xfee00000
[ 0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[ 0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
[ 0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x82] disabled)
[ 0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x83] disabled)
[ 0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[ 0.000000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-23
[ 0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[ 0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[ 0.000000] ACPI: IRQ0 used by override.
[ 0.000000] ACPI: IRQ2 used by override.
[ 0.000000] ACPI: IRQ9 used by override.
[ 0.000000] Using ACPI (MADT) for SMP configuration information
[ 0.000000] SMP: Allowing 4 CPUs, 2 hotplug CPUs
[ 0.000000] nr_irqs_gsi: 24
[ 0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[ 0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e4000
[ 0.000000] PM: Registered nosave memory: 00000000000e4000 - 0000000000100000
[ 0.000000] Allocating PCI resources starting at 7f800000 (gap: 7f800000:7f500000)
[ 0.000000] Booting paravirtualized kernel on bare hardware
[ 0.000000] NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:4 nr_node_ids:1
[ 0.000000] PERCPU: Embedded 14 pages/cpu @c2400000 s36056 r0 d21288 u1048576
[ 0.000000] pcpu-alloc: s36056 r0 d21288 u1048576 alloc=1*4194304
[ 0.000000] pcpu-alloc: [0] 0 1 2 3 
[ 0.000000] Built 1 zonelists in Zone order, mobility grouping on. Total pages: 517967
[ 0.000000] Kernel command line: BOOT_IMAGE=/casper/vmlinuz file=/cdrom/preseed/ubuntu.seed boot=casper initrd=/casper/initrd.lz quiet splash --
[ 0.000000] PID hash table entries: 4096 (order: 2, 16384 bytes)
[ 0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[ 0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[ 0.000000] Enabling fast FPU save and restore... done.
[ 0.000000] Enabling unmasked SIMD FPU exception support... done.
[ 0.000000] Initializing CPU#0
[ 0.000000] allocated 10442880 bytes of page_cgroup
[ 0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[ 0.000000] Initializing HighMem for node 0 (000377fe:0007f7b0)
[ 0.000000] Memory: 2042020k/2088640k available (4696k kernel code, 44900k reserved, 2123k data, 664k init, 1179336k highmem)
[ 0.000000] virtual kernel memory layout:
[ 0.000000] fixmap : 0xfff1d000 - 0xfffff000 ( 904 kB)
[ 0.000000] pkmap : 0xff800000 - 0xffc00000 (4096 kB)
[ 0.000000] vmalloc : 0xf7ffe000 - 0xff7fe000 ( 120 MB)
[ 0.000000] lowmem : 0xc0000000 - 0xf77fe000 ( 887 MB)
[ 0.000000] .init : 0xc07a9000 - 0xc084f000 ( 664 kB)
[ 0.000000] .data : 0xc0596257 - 0xc07a8f88 (2123 kB)
[ 0.000000] .text : 0xc0100000 - 0xc0596257 (4696 kB)
[ 0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[ 0.000000] SLUB: Genslabs=13, HWalign=128, Order=0-3, MinObjects=0, CPUs=4, Nodes=1
[ 0.000000] Hierarchical RCU implementation.
[ 0.000000] NR_IRQS:2304 nr_irqs:440
[ 0.000000] Console: colour VGA+ 80x25
[ 0.000000] console [tty0] enabled
[ 0.000000] Fast TSC calibration using PIT
[ 0.000000] Detected 2991.822 MHz processor.
[ 0.004006] Calibrating delay loop (skipped), value calculated using timer frequency.. 5983.64 BogoMIPS (lpj=11967288)
[ 0.004029] Security Framework initialized
[ 0.004056] AppArmor: AppArmor initialized
[ 0.004067] Mount-cache hash table entries: 512
[ 0.004242] Initializing cgroup subsys ns
[ 0.004248] Initializing cgroup subsys cpuacct
[ 0.004254] Initializing cgroup subsys memory
[ 0.004264] Initializing cgroup subsys devices
[ 0.004267] Initializing cgroup subsys freezer
[ 0.004270] Initializing cgroup subsys net_cls
[ 0.008018] CPU: Trace cache: 12K uops, L1 D cache: 16K
[ 0.008022] CPU: L2 cache: 2048K
[ 0.008026] CPU: Physical Processor ID: 0
[ 0.008028] CPU: Processor Core ID: 0
[ 0.008033] mce: CPU supports 4 MCE banks
[ 0.008048] CPU0: Thermal monitoring enabled (TM1)
[ 0.008054] using mwait in idle threads.
[ 0.008064] Performance Events: no PMU driver, software events only.
[ 0.008073] Checking 'hlt' instruction... OK.
[ 0.028302] ACPI: Core revision 20090903
[ 0.040015] ftrace: converting mcount calls to 0f 1f 44 00 00
[ 0.040022] ftrace: allocating 21817 entries in 43 pages
[ 0.044081] Enabling APIC mode: Flat. Using 1 I/O APICs
[ 0.044408] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[ 0.087456] CPU0: Intel(R) Pentium(R) D CPU 3.00GHz stepping 05
[ 0.088001] Booting processor 1 APIC 0x1 ip 0x6000
[ 0.008000] Initializing CPU#1
[ 0.008000] CPU: Trace cache: 12K uops, L1 D cache: 16K
[ 0.008000] CPU: L2 cache: 2048K
[ 0.008000] CPU: Physical Processor ID: 0
[ 0.008000] CPU: Processor Core ID: 1
[ 0.008000] CPU1: Thermal monitoring enabled (TM1)
[ 0.172087] CPU1: Intel(R) Pentium(R) D CPU 3.00GHz stepping 05
[ 0.172099] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
[ 0.176021] Brought up 2 CPUs
[ 0.176028] Total of 2 processors activated (11967.54 BogoMIPS).
[ 0.177075] CPU0 attaching sched-domain:
[ 0.177081] domain 0: span 0-1 level CPU
[ 0.177085] groups: 0 1
[ 0.177093] CPU1 attaching sched-domain:
[ 0.177096] domain 0: span 0-1 level CPU
[ 0.177099] groups: 1 0
[ 0.177215] devtmpfs: initialized
[ 0.177215] regulator: core version 0.5
[ 0.177215] Time: 16:15:55 Date: 03/02/12
[ 0.177215] NET: Registered protocol family 16
[ 0.177215] Trying to unpack rootfs image as initramfs...
[ 0.177215] EISA bus registered
[ 0.177215] ACPI: bus type pci registered
[ 0.177215] PCI: Found Intel Corporation 945G/GZ/P/PL Express Memory Controller Hub with MMCONFIG support.
[ 0.177215] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 255
[ 0.177215] PCI: Not using MMCONFIG.
[ 0.177215] PCI: PCI BIOS revision 3.00 entry at 0xf0031, last bus=3
[ 0.177215] PCI: Using configuration type 1 for base access
[ 0.184150] bio: create slab <bio-0> at 0
[ 0.185538] ACPI: EC: Look up EC in DSDT
[ 0.189821] ACPI: Executed 1 blocks of module-level executable AML code
[ 0.196493] ACPI: Interpreter enabled
[ 0.196499] ACPI: (supports S0 S1 S4 S5)
[ 0.196529] ACPI: Using IOAPIC for interrupt routing
[ 0.205886] ACPI Warning: Incorrect checksum in table [OEMB] - BF, should be B2 (20090903/tbutils-314)
[ 0.206025] ACPI: No dock devices found.
[ 0.206425] ACPI: PCI Root Bridge [PCI0] (0000:00)
[ 0.206541] pci 0000:00:02.0: reg 10 32bit mmio: [0xfe980000-0xfe9fffff]
[ 0.206549] pci 0000:00:02.0: reg 14 io port: [0xdc00-0xdc07]
[ 0.206556] pci 0000:00:02.0: reg 18 32bit mmio pref: [0xd0000000-0xdfffffff]
[ 0.206562] pci 0000:00:02.0: reg 1c 32bit mmio: [0xfe940000-0xfe97ffff]
[ 0.206664] pci 0000:00:1b.0: reg 10 64bit mmio: [0xfe938000-0xfe93bfff]
[ 0.206717] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[ 0.206722] pci 0000:00:1b.0: PME# disabled
[ 0.206801] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[ 0.206807] pci 0000:00:1c.0: PME# disabled
[ 0.206887] pci 0000:00:1c.1: PME# supported from D0 D3hot D3cold
[ 0.206893] pci 0000:00:1c.1: PME# disabled
[ 0.206955] pci 0000:00:1d.0: reg 20 io port: [0xd400-0xd41f]
[ 0.207017] pci 0000:00:1d.1: reg 20 io port: [0xd480-0xd49f]
[ 0.207079] pci 0000:00:1d.2: reg 20 io port: [0xd800-0xd81f]
[ 0.207139] pci 0000:00:1d.3: reg 20 io port: [0xd880-0xd89f]
[ 0.207207] pci 0000:00:1d.7: reg 10 32bit mmio: [0xfe937c00-0xfe937fff]
[ 0.207268] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
[ 0.207274] pci 0000:00:1d.7: PME# disabled
[ 0.207427] pci 0000:00:1f.0: Force enabled HPET at 0xfed00000
[ 0.207441] pci 0000:00:1f.0: ICH7 LPC Generic IO decode 1 PIO at 0280 (mask 00ff)
[ 0.207496] pci 0000:00:1f.1: reg 10 io port: [0x00-0x07]
[ 0.207505] pci 0000:00:1f.1: reg 14 io port: [0x00-0x03]
[ 0.207514] pci 0000:00:1f.1: reg 18 io port: [0x8f0-0x8f7]
[ 0.207522] pci 0000:00:1f.1: reg 1c io port: [0x8f8-0x8fb]
[ 0.207531] pci 0000:00:1f.1: reg 20 io port: [0xffa0-0xffaf]
[ 0.207588] pci 0000:00:1f.2: reg 10 io port: [0xd080-0xd087]
[ 0.207596] pci 0000:00:1f.2: reg 14 io port: [0xd000-0xd003]
[ 0.207604] pci 0000:00:1f.2: reg 18 io port: [0xcc00-0xcc07]
[ 0.207612] pci 0000:00:1f.2: reg 1c io port: [0xc880-0xc883]
[ 0.207619] pci 0000:00:1f.2: reg 20 io port: [0xc800-0xc80f]
[ 0.207649] pci 0000:00:1f.2: PME# supported from D3hot
[ 0.207654] pci 0000:00:1f.2: PME# disabled
[ 0.207710] pci 0000:00:1f.3: reg 20 io port: [0x400-0x41f]
[ 0.207799] pci 0000:00:1c.0: bridge 64bit mmio pref: [0xfdf00000-0xfdffffff]
[ 0.207868] pci 0000:01:00.0: reg 10 io port: [0xe800-0xe8ff]
[ 0.207894] pci 0000:01:00.0: reg 18 64bit mmio: [0xfeaff000-0xfeafffff]
[ 0.207920] pci 0000:01:00.0: reg 30 32bit mmio pref: [0xfeac0000-0xfeadffff]
[ 0.207975] pci 0000:01:00.0: supports D1 D2
[ 0.207978] pci 0000:01:00.0: PME# supported from D1 D2 D3hot D3cold
[ 0.207985] pci 0000:01:00.0: PME# disabled
[ 0.208048] pci 0000:00:1c.1: bridge io port: [0xe000-0xefff]
[ 0.208054] pci 0000:00:1c.1: bridge 32bit mmio: [0xfea00000-0xfeafffff]
[ 0.208093] pci 0000:03:01.0: reg 10 32bit mmio: [0xfebfe000-0xfebfffff]
[ 0.208183] pci 0000:00:1e.0: transparent bridge
[ 0.208191] pci 0000:00:1e.0: bridge 32bit mmio: [0xfeb00000-0xfebfffff]
[ 0.208215] pci_bus 0000:00: on NUMA node 0
[ 0.208220] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[ 0.208403] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P1._PRT]
[ 0.208538] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P4._PRT]
[ 0.208615] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P5._PRT]
[ 0.213410] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 10 *11 12 14 15)
[ 0.213557] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 *10 11 12 14 15)
[ 0.213698] ACPI: PCI Interrupt Link [LNKC] (IRQs *3 4 5 6 7 10 11 12 14 15)
[ 0.213839] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 *5 6 7 10 11 12 14 15)
[ 0.213981] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[ 0.214124] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[ 0.214267] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 *5 6 7 10 11 12 14 15)
[ 0.214409] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 10 11 12 14 *15)
[ 0.214548] vgaarb: device added: PCI:0000:00:02.0,decodes=io+mem,owns=io+mem,locks=none
[ 0.214565] vgaarb: loaded
[ 0.214722] SCSI subsystem initialized
[ 0.214805] libata version 3.00 loaded.
[ 0.214905] usbcore: registered new interface driver usbfs
[ 0.214924] usbcore: registered new interface driver hub
[ 0.214960] usbcore: registered new device driver usb
[ 0.215137] ACPI: WMI: Mapper loaded
[ 0.215140] PCI: Using ACPI for IRQ routing
[ 0.215339] NetLabel: Initializing
[ 0.215342] NetLabel: domain hash size = 128
[ 0.215345] NetLabel: protocols = UNLABELED CIPSOv4
[ 0.215362] NetLabel: unlabeled traffic allowed by default
[ 0.215480] hpet clockevent registered
[ 0.215485] HPET: 3 timers in total, 0 timers will be used for per-cpu timer
[ 0.215492] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[ 0.215499] hpet0: 3 comparators, 64-bit 14.318180 MHz counter
[ 3.038857] Switching to clocksource tsc
[ 3.039113] AppArmor: AppArmor Filesystem Enabled
[ 3.039152] pnp: PnP ACPI init
[ 3.039188] ACPI: bus type pnp registered
[ 3.045707] pnp: PnP ACPI: found 16 devices
[ 3.045710] ACPI: ACPI bus type pnp unregistered
[ 3.045716] PnPBIOS: Disabled by ACPI PNP
[ 3.045735] system 00:01: iomem range 0xfed13000-0xfed19fff has been reserved
[ 3.045749] system 00:08: ioport range 0x4d0-0x4d1 has been reserved
[ 3.045754] system 00:08: ioport range 0x800-0x87f has been reserved
[ 3.045758] system 00:08: ioport range 0x480-0x4bf has been reserved
[ 3.045761] system 00:08: ioport range 0x900-0x90f has been reserved
[ 3.045766] system 00:08: iomem range 0xfed1c000-0xfed1ffff has been reserved
[ 3.045770] system 00:08: iomem range 0xfed20000-0xfed8ffff has been reserved
[ 3.045779] system 00:0a: iomem range 0xffc00000-0xfff7ffff has been reserved
[ 3.045787] system 00:0b: iomem range 0xfec00000-0xfec00fff could not be reserved
[ 3.045791] system 00:0b: iomem range 0xfee00000-0xfee00fff has been reserved
[ 3.045800] system 00:0d: ioport range 0x290-0x29f has been reserved
[ 3.045808] system 00:0e: iomem range 0xe0000000-0xefffffff has been reserved
[ 3.045817] system 00:0f: iomem range 0x0-0x9ffff could not be reserved
[ 3.045821] system 00:0f: iomem range 0xc0000-0xcffff could not be reserved
[ 3.045825] system 00:0f: iomem range 0xe0000-0xfffff could not be reserved
[ 3.045829] system 00:0f: iomem range 0x100000-0x7f7fffff could not be reserved
[ 3.080670] pci 0000:00:1c.0: PCI bridge, secondary bus 0000:02
[ 3.080676] pci 0000:00:1c.0: IO window: 0x1000-0x1fff
[ 3.080683] pci 0000:00:1c.0: MEM window: 0x80000000-0x803fffff
[ 3.080690] pci 0000:00:1c.0: PREFETCH window: 0x000000fdf00000-0x000000fdffffff
[ 3.080702] pci 0000:00:1c.1: PCI bridge, secondary bus 0000:01
[ 3.080706] pci 0000:00:1c.1: IO window: 0xe000-0xefff
[ 3.080713] pci 0000:00:1c.1: MEM window: 0xfea00000-0xfeafffff
[ 3.080719] pci 0000:00:1c.1: PREFETCH window: 0x00000080400000-0x000000805fffff
[ 3.080730] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:03
[ 3.080733] pci 0000:00:1e.0: IO window: disabled
[ 3.080740] pci 0000:00:1e.0: MEM window: 0xfeb00000-0xfebfffff
[ 3.080745] pci 0000:00:1e.0: PREFETCH window: disabled
[ 3.080761] pci 0000:00:1c.0: enabling device (0106 -> 0107)
[ 3.080772] alloc irq_desc for 16 on node -1
[ 3.080775] alloc kstat_irqs on node -1
[ 3.080782] pci 0000:00:1c.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[ 3.080789] pci 0000:00:1c.0: setting latency timer to 64
[ 3.080802] alloc irq_desc for 17 on node -1
[ 3.080804] alloc kstat_irqs on node -1
[ 3.080809] pci 0000:00:1c.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[ 3.080815] pci 0000:00:1c.1: setting latency timer to 64
[ 3.080825] pci 0000:00:1e.0: setting latency timer to 64
[ 3.080833] pci_bus 0000:00: resource 0 io: [0x00-0xffff]
[ 3.080837] pci_bus 0000:00: resource 1 mem: [0x000000-0xffffffff]
[ 3.080842] pci_bus 0000:02: resource 0 io: [0x1000-0x1fff]
[ 3.080845] pci_bus 0000:02: resource 1 mem: [0x80000000-0x803fffff]
[ 3.080848] pci_bus 0000:02: resource 2 pref mem [0xfdf00000-0xfdffffff]
[ 3.080852] pci_bus 0000:01: resource 0 io: [0xe000-0xefff]
[ 3.080855] pci_bus 0000:01: resource 1 mem: [0xfea00000-0xfeafffff]
[ 3.080858] pci_bus 0000:01: resource 2 pref mem [0x80400000-0x805fffff]
[ 3.080861] pci_bus 0000:03: resource 1 mem: [0xfeb00000-0xfebfffff]
[ 3.080864] pci_bus 0000:03: resource 3 io: [0x00-0xffff]
[ 3.080867] pci_bus 0000:03: resource 4 mem: [0x000000-0xffffffff]
[ 3.080922] NET: Registered protocol family 2
[ 3.081080] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[ 3.081605] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[ 3.082339] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[ 3.082685] TCP: Hash tables configured (established 131072 bind 65536)
[ 3.082689] TCP reno registered
[ 3.082795] NET: Registered protocol family 1
[ 3.082826] pci 0000:00:02.0: Boot video device
[ 3.083169] cpufreq-nforce2: No nForce2 chipset.
[ 3.083209] Scanning for low memory corruption every 60 seconds
[ 3.083365] audit: initializing netlink socket (disabled)
[ 3.083381] type=2000 audit(1330704958.080:1): initialized
[ 3.092757] highmem bounce pool size: 64 pages
[ 3.092766] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[ 3.094974] VFS: Disk quotas dquot_6.5.2
[ 3.095058] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[ 3.095929] fuse init (API version 7.13)
[ 3.096069] msgmni has been set to 1687
[ 3.100525] alg: No test for stdrng (krng)
[ 3.100613] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[ 3.100618] io scheduler noop registered
[ 3.100621] io scheduler anticipatory registered
[ 3.100624] io scheduler deadline registered
[ 3.100683] io scheduler cfq registered (default)
[ 3.100864] alloc irq_desc for 24 on node -1
[ 3.100867] alloc kstat_irqs on node -1
[ 3.100881] pcieport 0000:00:1c.0: irq 24 for MSI/MSI-X
[ 3.100893] pcieport 0000:00:1c.0: setting latency timer to 64
[ 3.101033] alloc irq_desc for 25 on node -1
[ 3.101036] alloc kstat_irqs on node -1
[ 3.101046] pcieport 0000:00:1c.1: irq 25 for MSI/MSI-X
[ 3.101057] pcieport 0000:00:1c.1: setting latency timer to 64
[ 3.101167] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[ 3.101190] Firmware did not grant requested _OSC control
[ 3.101213] Firmware did not grant requested _OSC control
[ 3.101253] Firmware did not grant requested _OSC control
[ 3.101271] Firmware did not grant requested _OSC control
[ 3.101292] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[ 3.101428] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0
[ 3.101433] ACPI: Power Button [PWRB]
[ 3.101497] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
[ 3.101501] ACPI: Power Button [PWRF]
[ 3.102329] ACPI: SSDT 7f7c0090 001D2 (v01 AMI CPU1PM 00000001 INTL 20051117)
[ 3.102673] processor LNXCPU:00: registered as cooling_device0
[ 3.103152] ACPI: SSDT 7f7c0270 00143 (v01 AMI CPU2PM 00000001 INTL 20051117)
[ 3.103333] Freeing initrd memory: 9199k freed
[ 3.103485] processor LNXCPU:01: registered as cooling_device1
[ 3.109349] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[ 3.109483] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[ 3.109543] isapnp: Scanning for PnP cards...
[ 3.110058] 00:0c: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[ 3.111510] brd: module loaded
[ 3.112179] loop: module loaded
[ 3.112284] input: Macintosh mouse button emulation as /devices/virtual/input/input2
[ 3.112400] ata_piix 0000:00:1f.1: version 2.13
[ 3.112416] alloc irq_desc for 18 on node -1
[ 3.112419] alloc kstat_irqs on node -1
[ 3.112426] ata_piix 0000:00:1f.1: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[ 3.112473] ata_piix 0000:00:1f.1: setting latency timer to 64
[ 3.112585] scsi0 : ata_piix
[ 3.112691] scsi1 : ata_piix
[ 3.114590] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xffa0 irq 14
[ 3.114595] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xffa8 irq 15
[ 3.114626] alloc irq_desc for 19 on node -1
[ 3.114630] alloc kstat_irqs on node -1
[ 3.114636] ata_piix 0000:00:1f.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[ 3.114645] ata_piix 0000:00:1f.2: MAP [ P0 P2 P1 P3 ]
[ 3.114690] ata_piix 0000:00:1f.2: setting latency timer to 64
[ 3.114901] scsi2 : ata_piix
[ 3.114981] scsi3 : ata_piix
[ 3.115034] ata3: SATA max UDMA/133 cmd 0xd080 ctl 0xd000 bmdma 0xc800 irq 19
[ 3.115038] ata4: SATA max UDMA/133 cmd 0xcc00 ctl 0xc880 bmdma 0xc808 irq 19
[ 3.115129] ata2: port disabled. ignoring.
[ 3.115535] Fixed MDIO Bus: probed
[ 3.115587] PPP generic driver version 2.4.2
[ 3.115638] tun: Universal TUN/TAP device driver, 1.6
[ 3.115641] tun: (C) 1999-2004 Max Krasnyansky <[EMAIL="maxk@qualcomm.com"]maxk@qualcomm.com[/EMAIL]>
[ 3.115757] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[ 3.115780] alloc irq_desc for 23 on node -1
[ 3.115783] alloc kstat_irqs on node -1
[ 3.115790] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[ 3.115804] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[ 3.115809] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[ 3.115860] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 1
[ 3.115893] ehci_hcd 0000:00:1d.7: using broken periodic workaround
[ 3.115907] ehci_hcd 0000:00:1d.7: debug port 1
[ 3.119798] ehci_hcd 0000:00:1d.7: cache line size of 128 is not supported
[ 3.119813] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xfe937c00
[ 3.132515] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[ 3.132639] usb usb1: configuration #1 chosen from 1 choice
[ 3.132682] hub 1-0:1.0: USB hub found
[ 3.132694] hub 1-0:1.0: 8 ports detected
[ 3.132785] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[ 3.132809] uhci_hcd: USB Universal Host Controller Interface driver
[ 3.132838] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[ 3.132845] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[ 3.132850] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[ 3.132895] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
[ 3.132922] uhci_hcd 0000:00:1d.0: irq 23, io base 0x0000d400
[ 3.133044] usb usb2: configuration #1 chosen from 1 choice
[ 3.133082] hub 2-0:1.0: USB hub found
[ 3.133092] hub 2-0:1.0: 2 ports detected
[ 3.133157] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[ 3.133165] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[ 3.133169] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[ 3.133213] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 3
[ 3.133239] uhci_hcd 0000:00:1d.1: irq 19, io base 0x0000d480
[ 3.133361] usb usb3: configuration #1 chosen from 1 choice
[ 3.133398] hub 3-0:1.0: USB hub found
[ 3.133408] hub 3-0:1.0: 2 ports detected
[ 3.133469] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[ 3.133478] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[ 3.133482] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[ 3.133525] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 4
[ 3.133558] uhci_hcd 0000:00:1d.2: irq 18, io base 0x0000d800
[ 3.133681] usb usb4: configuration #1 chosen from 1 choice
[ 3.133720] hub 4-0:1.0: USB hub found
[ 3.133730] hub 4-0:1.0: 2 ports detected
[ 3.133797] uhci_hcd 0000:00:1d.3: PCI INT D -> GSI 16 (level, low) -> IRQ 16
[ 3.133805] uhci_hcd 0000:00:1d.3: setting latency timer to 64
[ 3.133809] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[ 3.133851] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 5
[ 3.133884] uhci_hcd 0000:00:1d.3: irq 16, io base 0x0000d880
[ 3.134003] usb usb5: configuration #1 chosen from 1 choice
[ 3.134042] hub 5-0:1.0: USB hub found
[ 3.134052] hub 5-0:1.0: 2 ports detected
[ 3.134196] PNP: No PS/2 controller found. Probing ports directly.
[ 3.136704] serio: i8042 KBD port at 0x60,0x64 irq 1
[ 3.136715] serio: i8042 AUX port at 0x60,0x64 irq 12
[ 3.136882] mice: PS/2 mouse device common for all mice
[ 3.137050] rtc_cmos 00:03: RTC can wake from S4
[ 3.137099] rtc_cmos 00:03: rtc core: registered rtc_cmos as rtc0
[ 3.137127] rtc0: alarms up to one month, 114 bytes nvram, hpet irqs
[ 3.137271] device-mapper: uevent: version 1.0.3
[ 3.137393] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: [EMAIL="dm-devel@redhat.com"]dm-devel@redhat.com[/EMAIL]
[ 3.137479] device-mapper: multipath: version 1.1.0 loaded
[ 3.137483] device-mapper: multipath round-robin: version 1.0.0 loaded
[ 3.137626] EISA: Probing bus 0 at eisa.0
[ 3.137633] Cannot allocate resource for EISA slot 1
[ 3.137658] EISA: Detected 0 cards.
[ 3.137763] cpuidle: using governor ladder
[ 3.137766] cpuidle: using governor menu
[ 3.138364] TCP cubic registered
[ 3.138551] NET: Registered protocol family 10
[ 3.139707] NET: Registered protocol family 17
[ 3.140284] Using IPI No-Shortcut mode
[ 3.140386] PM: Resume from disk failed.
[ 3.140402] registered taskstats version 1
[ 3.140744] Magic number: 4:546:286
[ 3.140751] ppp ppp: hash matches
[ 3.140821] rtc_cmos 00:03: setting system clock to 2012-03-02 16:15:58 UTC (1330704958)
[ 3.140826] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[ 3.140828] EDD information not available.
[ 3.280322] ata1.00: ATAPI: TSSTcorp CDDVDW SH-S202G, SB00, max UDMA/66
[ 3.300227] ata1.00: configured for UDMA/66
[ 3.340833] ata3.00: ATA-7: WDC WD800JD-22LSA1, 10.01E01, max UDMA/133
[ 3.340838] ata3.00: 156301488 sectors, multi 16: LBA48 
[ 3.350045] ata3.01: ATA-8: WDC WD3200AAKS-00VYA0, 12.01B02, max UDMA/133
[ 3.350050] ata3.01: 625142448 sectors, multi 16: LBA48 NCQ (depth 0/32)
[ 3.356854] ata3.00: configured for UDMA/133
[ 3.365491] ata3.01: configured for UDMA/133
[ 3.465518] isapnp: No Plug & Play device found
[ 3.466205] scsi 0:0:0:0: CD-ROM TSSTcorp CDDVDW SH-S202G SB00 PQ: 0 ANSI: 5
[ 3.469638] sr0: scsi3-mmc drive: 32x/40x writer dvd-ram cd/rw xa/form2 cdda tray
[ 3.469642] Uniform CD-ROM driver Revision: 3.20
[ 3.469782] sr 0:0:0:0: Attached scsi CD-ROM sr0
[ 3.469878] sr 0:0:0:0: Attached scsi generic sg0 type 5
[ 3.470069] scsi 2:0:0:0: Direct-Access ATA WDC WD800JD-22LS 10.0 PQ: 0 ANSI: 5
[ 3.470238] sd 2:0:0:0: Attached scsi generic sg1 type 0
[ 3.470264] sd 2:0:0:0: [sda] 156301488 512-byte logical blocks: (80.0 GB/74.5 GiB)
[ 3.470373] sd 2:0:0:0: [sda] Write Protect is off
[ 3.470377] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[ 3.470399] scsi 2:0:1:0: Direct-Access ATA WDC WD3200AAKS-0 12.0 PQ: 0 ANSI: 5
[ 3.470419] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[ 3.470584] sd 2:0:1:0: Attached scsi generic sg2 type 0
[ 3.470700] sda:
[ 3.470706] sd 2:0:1:0: [sdb] 625142448 512-byte logical blocks: (320 GB/298 GiB)
[ 3.480995] sd 2:0:1:0: [sdb] Write Protect is off
[ 3.481001] sd 2:0:1:0: [sdb] Mode Sense: 00 3a 00 00
[ 3.481165] sd 2:0:1:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[ 3.481320] unknown partition table
[ 3.481443] sdb: sdb1 sdb2 < >
[ 3.497603] sd 2:0:0:0: [sda] Attached SCSI disk
[ 3.497903] sd 2:0:1:0: [sdb] Attached SCSI disk
[ 3.497924] Freeing unused kernel memory: 664k freed
[ 3.498435] Write protecting the kernel text: 4700k
[ 3.498493] Write protecting the kernel read-only data: 1844k
[ 3.527202] udev: starting version 151
[ 3.624672] usb 1-5: new high speed USB device using ehci_hcd and address 4
[ 3.676826] Floppy drive(s): fd0 is 1.44M
[ 3.679230] Linux agpgart interface v0.103
[ 3.685473] alloc irq_desc for 22 on node -1
[ 3.685478] alloc kstat_irqs on node -1
[ 3.685487] b43-pci-bridge 0000:03:01.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[ 3.688641] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[ 3.688669] r8169 0000:01:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[ 3.688728] r8169 0000:01:00.0: setting latency timer to 64
[ 3.688798] alloc irq_desc for 26 on node -1
[ 3.688801] alloc kstat_irqs on node -1
[ 3.688820] r8169 0000:01:00.0: irq 26 for MSI/MSI-X
[ 3.689722] eth0: RTL8168b/8111b at 0xf80c8000, 00:19:66:1d:14:d6, XID 18000000 IRQ 26
[ 3.716043] FDC 0 is a post-1991 82077
[ 3.721265] agpgart-intel 0000:00:00.0: Intel 945G Chipset
[ 3.722503] agpgart-intel 0000:00:00.0: detected 7932K stolen memory
[ 3.723021] [drm] Initialized drm 1.1.0 20060810
[ 3.726453] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0xd0000000
[ 3.752584] ssb: Sonics Silicon Backplane found on PCI device 0000:03:01.0
[ 3.756577] i915 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[ 3.756585] i915 0000:00:02.0: setting latency timer to 64
[ 3.761642] [drm] set up 7M of stolen space
[ 3.762720] [drm] initialized overlay support
[ 3.767109] usb 1-5: configuration #1 chosen from 1 choice
[ 3.778374] Initializing USB Mass Storage driver...
[ 3.778524] scsi4 : SCSI emulation for USB Mass Storage devices
[ 3.778711] usb-storage: device found at 4
[ 3.778715] usb-storage: waiting for device to settle before scanning
[ 3.778732] usbcore: registered new interface driver usb-storage
[ 3.778845] USB Mass Storage support registered.
[ 3.888520] usb 1-6: new high speed USB device using ehci_hcd and address 5
[ 3.930006] fb0: inteldrmfb frame buffer device
[ 3.930010] registered panic notifier
[ 3.930019] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
[ 3.932368] vga16fb: initializing
[ 3.932372] vga16fb: mapped to 0xc00a0000
[ 3.932377] vga16fb: not registering due to another framebuffer present
[ 3.994699] Console: switching to colour frame buffer device 200x56
[ 4.024979] usb 1-6: configuration #1 chosen from 1 choice
[ 4.026466] scsi5 : SCSI emulation for USB Mass Storage devices
[ 4.026706] usb-storage: device found at 5
[ 4.026710] usb-storage: waiting for device to settle before scanning
[ 4.268017] usb 3-1: new low speed USB device using uhci_hcd and address 2
[ 4.445393] usb 3-1: configuration #1 chosen from 1 choice
[ 4.481588] usbcore: registered new interface driver hiddev
[ 4.496610] input: Logitech USB Keyboard as /devices/pci0000:00/0000:00:1d.1/usb3/3-1/3-1:1.0/input/input3
[ 4.496725] generic-usb 0003:046D:C31C.0001: input,hidraw0: USB HID v1.10 Keyboard [Logitech USB Keyboard] on usb-0000:00:1d.1-1/input0
[ 4.536377] input: Logitech USB Keyboard as /devices/pci0000:00/0000:00:1d.1/usb3/3-1/3-1:1.1/input/input4
[ 4.536463] generic-usb 0003:046D:C31C.0002: input,hidraw1: USB HID v1.10 Device [Logitech USB Keyboard] on usb-0000:00:1d.1-1/input1
[ 4.536497] usbcore: registered new interface driver usbhid
[ 4.536502] usbhid: v2.6:USB HID core driver
[ 4.776015] usb 3-2: new full speed USB device using uhci_hcd and address 3
[ 4.791232] xor: automatically using best checksumming function: pIII_sse
[ 4.808509] pIII_sse : 4511.000 MB/sec
[ 4.808512] xor: using function: pIII_sse (4511.000 MB/sec)
[ 4.815685] device-mapper: dm-raid45: initialized v0.2594b
[ 4.964407] usb 3-2: configuration #1 chosen from 1 choice
[ 4.972587] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:1d.1/usb3/3-2/3-2:1.0/input/input5
[ 4.972690] generic-usb 0003:046D:C52B.0003: input,hidraw2: USB HID v1.11 Keyboard [Logitech USB Receiver] on usb-0000:00:1d.1-2/input0
[ 4.973710] EXT4-fs (sdb1): mounted filesystem with ordered data mode
[ 4.975784] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:1d.1/usb3/3-2/3-2:1.1/input/input6
[ 4.975976] generic-usb 0003:046D:C52B.0004: input,hiddev96,hidraw3: USB HID v1.11 Mouse [Logitech USB Receiver] on usb-0000:00:1d.1-2/input1
[ 4.982380] generic-usb 0003:046D:C52B.0005: hiddev97,hidraw4: USB HID v1.11 Device [Logitech USB Receiver] on usb-0000:00:1d.1-2/input2
[ 6.450130] ISO 9660 Extensions: Microsoft Joliet Level 3
[ 6.491937] ISO 9660 Extensions: RRIP_1991A
[ 6.570502] aufs 2-standalone.tree-20091207
[ 6.649149] squashfs: version 4.0 (2009/01/31) Phillip Lougher
[ 8.780398] usb-storage: device scan complete
[ 8.781113] scsi 4:0:0:0: Direct-Access SanDisk U3 Cruzer Micro 2.17 PQ: 0 ANSI: 2
[ 8.781916] sd 4:0:0:0: Attached scsi generic sg3 type 0
[ 8.787872] sd 4:0:0:0: [sdc] 4013713 512-byte logical blocks: (2.05 GB/1.91 GiB)
[ 8.791862] sd 4:0:0:0: [sdc] Write Protect is off
[ 8.791866] sd 4:0:0:0: [sdc] Mode Sense: 03 00 00 00
[ 8.791869] sd 4:0:0:0: [sdc] Assuming drive cache: write through
[ 8.807362] sd 4:0:0:0: [sdc] Assuming drive cache: write through
[ 8.807368] sdc: sdc1
[ 8.820488] sd 4:0:0:0: [sdc] Assuming drive cache: write through
[ 8.820493] sd 4:0:0:0: [sdc] Attached SCSI removable disk
[ 9.028140] usb-storage: device scan complete
[ 9.028636] scsi 5:0:0:0: Direct-Access SanDisk Cruzer 8.01 PQ: 0 ANSI: 0 CCS
[ 9.029687] sd 5:0:0:0: Attached scsi generic sg4 type 0
[ 9.030368] sd 5:0:0:0: [sdd] 15731711 512-byte logical blocks: (8.05 GB/7.50 GiB)
[ 9.030861] sd 5:0:0:0: [sdd] Write Protect is off
[ 9.030866] sd 5:0:0:0: [sdd] Mode Sense: 45 00 00 08
[ 9.030869] sd 5:0:0:0: [sdd] Assuming drive cache: write through
[ 9.032485] sd 5:0:0:0: [sdd] Assuming drive cache: write through
[ 9.032490] sdd: sdd1
[ 9.034740] sd 5:0:0:0: [sdd] Assuming drive cache: write through
[ 9.034745] sd 5:0:0:0: [sdd] Attached SCSI removable disk
[ 47.163135] udev: starting version 151
[ 50.524909] intel_rng: FWH not detected
[ 51.713872] cfg80211: Calling CRDA to update world regulatory domain
[ 51.720086] parport_pc 00:07: reported by Plug and Play ACPI
[ 51.720144] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
[ 52.166616] ppdev: user-space parallel port driver
[ 52.350213] b43-phy0: Broadcom 4318 WLAN found (core revision 9)
[ 53.590790] cfg80211: World regulatory domain updated:
[ 53.590795] (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[ 53.590799] (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 53.590803] (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 53.590807] (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 53.590810] (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 53.590814] (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 53.608624] phy0: Selected rate control algorithm 'minstrel'
[ 53.609731] Registered led device: b43-phy0::tx
[ 53.609759] Registered led device: b43-phy0::rx
[ 53.609785] Registered led device: b43-phy0::radio
[ 53.609883] Broadcom 43xx driver loaded [ Features: PL, Firmware-ID: FW13 ]
[ 54.026876] r8169: eth0: link down
[ 54.027047] ADDRCONF(NETDEV_UP): eth0: link is not ready
[ 54.092108] b43 ssb0:0: firmware: requesting b43/ucode5.fw
[ 54.232619] b43 ssb0:0: firmware: requesting b43-open/ucode5.fw
[ 54.383546] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found
[ 54.383552] b43-phy0 ERROR: Firmware file "b43-open/ucode5.fw" not found
[ 54.383557] b43-phy0 ERROR: You must go to [http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware](http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware for this driver version. Please carefully read all instructions on this website.
[ 54.619486] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[ 54.619521] HDA Intel 0000:00:1b.0: setting latency timer to 64
[ 54.876864] hda_codec: ALC888: BIOS auto-probing.
[ 54.878237] input: HDA Digital PCBeep as /devices/pci0000:00/0000:00:1b.0/input/input7
[ 54.888532] b43 ssb0:0: firmware: requesting b43/ucode5.fw
[ 54.890944] b43 ssb0:0: firmware: requesting b43-open/ucode5.fw
[ 54.901609] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found
[ 54.901617] b43-phy0 ERROR: Firmware file "b43-open/ucode5.fw" not found
[ 54.901621] b43-phy0 ERROR: You must go to [http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware](http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware for this driver version. Please carefully read all instructions on this website.
[ 59.634621] lp0: using parport0 (interrupt-driven).
[ 66.224019] CPU0 attaching NULL sched-domain.
[ 66.224029] CPU1 attaching NULL sched-domain.
[ 66.240588] CPU0 attaching sched-domain:
[ 66.240594] domain 0: span 0-1 level CPU
[ 66.240598] groups: 0 1
[ 66.240606] CPU1 attaching sched-domain:
[ 66.240609] domain 0: span 0-1 level CPU
[ 66.240612] groups: 1 0
[ 84.418573] CPU0 attaching NULL sched-domain.
[ 84.418581] CPU1 attaching NULL sched-domain.
[ 84.440580] CPU0 attaching sched-domain:
[ 84.440585] domain 0: span 0-1 level CPU
[ 84.440589] groups: 0 1
[ 84.440597] CPU1 attaching sched-domain:
[ 84.440600] domain 0: span 0-1 level CPU
[ 84.440603] groups: 1 0
[ 168.197203] padlock: VIA PadLock not detected.
[ 168.283778] alg: No test for xts(twofish) (xts(twofish-generic))
[ 168.367378] alg: No test for xts(serpent) (xts(serpent-generic))
[ 168.517048] EXT4-fs (dm-2): mounted filesystem with ordered data mode
[ 220.429046] EXT4-fs (dm-2): mounted filesystem with ordered data mode
[ 1543.404777] SGI XFS with ACLs, security attributes, realtime, large block/inode numbers, no debug enabled
[ 1543.407278] SGI XFS Quota Management subsystem
[ 1543.471054] JFS: nTxBlock = 8192, nTxLock = 65536
[ 1543.537979] NTFS driver 2.1.29 [Flags: R/O MODULE].
[ 1543.707885] QNX4 filesystem 0.2.3 registered.
[ 1543.860615] Btrfs loaded
[ 1544.203716] EXT4-fs (sdb1): mounted filesystem with ordered data mode
[ 1553.366575] cdrom: sr0: mrw address space DMA selected
[ 1565.572575] end_request: I/O error, dev fd0, sector 0
[ 1577.741644] end_request: I/O error, dev fd0, sector 0
[ 1646.689924] EXT4-fs (dm-2): mounted filesystem with ordered data mode
[ 1827.251854] EXT4-fs (sdb1): mounted filesystem with ordered data mode

---

### Post by winh8r on 2012-03-02
try having a read through this info:

[http://preview.tinyurl.com/7nwzhcl]("http://preview.tinyurl.com/7nwzhcl")

before you attempt anything else.


Hope this is of some help to you.

---

### Post by Waldotherogue on 2012-03-02
I'll save the article to my thumb drive and give it a go.  Will report back... oh jeez its Friday.
Will report back Monday hopefully.  Thanks for the info.

---

