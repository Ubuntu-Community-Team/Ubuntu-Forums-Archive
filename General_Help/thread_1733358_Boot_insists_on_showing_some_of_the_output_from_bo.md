---
title: "Boot insists on showing some of the output from boot processes"
date: 2011-04-19
forum: General Help
---

### Post by desconocido on 2011-04-19
Some time ago, when rearranging disk partitions, I deleted the swap partition without first telling Ubuntu (Karmic Koala). On the next reboot, fsck complained about this with output to the screen during the boot process.

I fixed this, but ever since whenever I reboot I see on the screen a message
```
fsck from util-linux-ng 2.16
```
followed by a message saying that my hard disk is fine.
More output follows from other programs until mysql after which all the output disappears.

Is there a way to stop seeing output when boots go normally?

---

### Post by hwttdz on 2011-04-19
Check your fstab to make sure it's not still looking for that partition.  

Additionally check your boot parameters in grub /etc/default/grub and do sudo update-grub.  You probably want "quiet splash" which says don't output lots of stuff, and display the splash screen.

---

### Post by desconocido on 2011-04-19
fstab seems OK (I restored the swap partition some time ago)```
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
UUID=1a2dbb4a-862c-4083-a7df-d01eb8034711 /               ext4    errors=remount-ro 0       1
UUID=cdf77969-af62-4001-8671-c454facc2631 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
```
I repeated sudo update-grub on a /etc/default/grub which contains
```
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.

GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=0
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entrys
GRUB_DISABLE_LINUX_RECOVERY="true"
```

Problem continues.

---

### Post by hwttdz on 2011-04-19
Can you post dmesg.

---

### Post by desconocido on 2011-04-21
> **hwttdz said:**
> Can you post dmesg.
```

[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.31-22-generic (buildd@vernadsky) (gcc version 4.4.1 (Ubuntu 4.4.1-4ubuntu8) ) #60-Ubuntu SMP Thu May 27 00:22:23 UTC 2010 (Ubuntu 2.6.31-22.60-generic)
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
[    0.000000]  BIOS-e820: 00000000000dc000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000003f690000 (usable)
[    0.000000]  BIOS-e820: 000000003f690000 - 000000003f69a000 (ACPI data)
[    0.000000]  BIOS-e820: 000000003f69a000 - 000000003f700000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000003f700000 - 0000000040000000 (reserved)
[    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed00000 - 00000000fed00400 (reserved)
[    0.000000]  BIOS-e820: 00000000fed14000 - 00000000fed1a000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed1c000 - 00000000fed90000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000ff000000 - 0000000100000000 (reserved)
[    0.000000] DMI 2.4 present.
[    0.000000] Phoenix BIOS detected: BIOS may corrupt low RAM, working around it.
[    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
[    0.000000] last_pfn = 0x3f690 max_arch_pfn = 0x100000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-CFFFF write-protect
[    0.000000]   D0000-DFFFF uncachable
[    0.000000]   E0000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000 mask FC0000000 write-back
[    0.000000]   1 base 03F700000 mask FFFF00000 uncachable
[    0.000000]   2 base 03F800000 mask FFF800000 uncachable
[    0.000000]   3 disabled
[    0.000000]   4 disabled
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] Scanning 0 areas for low memory corruption
[    0.000000] modified physical RAM map:
[    0.000000]  modified: 0000000000000000 - 0000000000010000 (reserved)
[    0.000000]  modified: 0000000000010000 - 000000000009f800 (usable)
[    0.000000]  modified: 000000000009f800 - 00000000000a0000 (reserved)
[    0.000000]  modified: 00000000000dc000 - 0000000000100000 (reserved)
[    0.000000]  modified: 0000000000100000 - 000000003f690000 (usable)
[    0.000000]  modified: 000000003f690000 - 000000003f69a000 (ACPI data)
[    0.000000]  modified: 000000003f69a000 - 000000003f700000 (ACPI NVS)
[    0.000000]  modified: 000000003f700000 - 0000000040000000 (reserved)
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
[    0.000000] kernel direct mapping tables up to 377fe000 @ 10000-15000
[    0.000000] RAMDISK: 2f1e1000 - 2f92b655
[    0.000000] ACPI: RSDP 000f6600 00014 (v00 PTLTD )
[    0.000000] ACPI: RSDT 3f693b94 00048 (v01 GATEWA SYSTEM   20070629  LTP 00000000)
[    0.000000] ACPI: FACP 3f699cb8 00074 (v01 GATEWA SYSTEM   20070629 LOHR 0000005A)
[    0.000000] ACPI: DSDT 3f694292 05A26 (v01 GATEWA SYSTEM   20070629 MSFT 0100000E)
[    0.000000] ACPI: FACS 3f69afc0 00040
[    0.000000] ACPI: APIC 3f699d2c 00068 (v01 GATEWA SYSTEM   20070629 LOHR 0000005A)
[    0.000000] ACPI: HPET 3f699d94 00038 (v01 GATEWA SYSTEM   20070629 LOHR 0000005A)
[    0.000000] ACPI: MCFG 3f699dcc 0003C (v01 GATEWA SYSTEM   20070629 LOHR 0000005A)
[    0.000000] ACPI: APIC 3f699e08 0005A (v01 GATEWA SYSTEM   20070629  LTP 00000000)
[    0.000000] ACPI: BOOT 3f699e62 00028 (v01 GATEWA SYSTEM   20070629  LTP 00000001)
[    0.000000] ACPI: SLIC 3f699e8a 00176 (v01 GATEWA SYSTEM   20070629  LTP 00000000)
[    0.000000] ACPI: SSDT 3f6940c6 001CC (v01  PmRef  Cpu0Cst 00003001 INTL 20050228)
[    0.000000] ACPI: SSDT 3f693bdc 004EA (v01 GATEWA SYSTEM   00003000 INTL 20050228)
[    0.000000] ACPI: BIOS bug: multiple APIC/MADT found, using 0
[    0.000000] ACPI: If "acpi_apic_instance=2" works better, notify linux-acpi@vger.kernel.org
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] 126MB HIGHMEM available.
[    0.000000] 887MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 377fe000
[    0.000000]   low ram: 0 - 377fe000
[    0.000000]   node 0 low ram: 00000000 - 377fe000
[    0.000000]   node 0 bootmap 00011000 - 00017f00
[    0.000000] (9 early reservations) ==> bootmem [0000000000 - 00377fe000]
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
[    0.000000]   #1 [0000001000 - 0000002000]    EX TRAMPOLINE ==> [0000001000 - 0000002000]
[    0.000000]   #2 [0000006000 - 0000007000]       TRAMPOLINE ==> [0000006000 - 0000007000]
[    0.000000]   #3 [0000100000 - 00008b0160]    TEXT DATA BSS ==> [0000100000 - 00008b0160]
[    0.000000]   #4 [002f1e1000 - 002f92b655]          RAMDISK ==> [002f1e1000 - 002f92b655]
[    0.000000]   #5 [000009f800 - 0000100000]    BIOS reserved ==> [000009f800 - 0000100000]
[    0.000000]   #6 [00008b1000 - 00008b4278]              BRK ==> [00008b1000 - 00008b4278]
[    0.000000]   #7 [0000010000 - 0000011000]          PGTABLE ==> [0000010000 - 0000011000]
[    0.000000]   #8 [0000011000 - 0000018000]          BOOTMAP ==> [0000011000 - 0000018000]
[    0.000000] found SMP MP-table at [c00f66b0] f66b0
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000010 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x000377fe
[    0.000000]   HighMem  0x000377fe -> 0x0003f690
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[2] active PFN ranges
[    0.000000]     0: 0x00000010 -> 0x0000009f
[    0.000000]     0: 0x00000100 -> 0x0003f690
[    0.000000] On node 0 totalpages: 259615
[    0.000000] free_area_init_node: node 0, pgdat c078ad40, node_mem_map c1000200
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3951 pages, LIFO batch:0
[    0.000000]   Normal zone: 1744 pages used for memmap
[    0.000000]   Normal zone: 221486 pages, LIFO batch:31
[    0.000000]   HighMem zone: 254 pages used for memmap
[    0.000000]   HighMem zone: 32148 pages, LIFO batch:7
[    0.000000] Using APIC driver default
[    0.000000] ACPI: PM-Timer IO Port: 0x1008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] disabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 1, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000
[    0.000000] SMP: Allowing 2 CPUs, 1 hotplug CPUs
[    0.000000] nr_irqs_gsi: 24
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000dc000
[    0.000000] PM: Registered nosave memory: 00000000000dc000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 40000000 (gap: 40000000:a0000000)
[    0.000000] NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:2 nr_node_ids:1
[    0.000000] PERCPU: Embedded 14 pages at c17f4000, static data 35612 bytes
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 257585
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.31-22-generic root=UUID=314dbdae-737c-49c2-b634-fc39d4564125 ro quiet splash
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] allocated 5194240 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] Initializing HighMem for node 0 (000377fe:0003f690)
[    0.000000] Memory: 1008500k/1038912k available (4583k kernel code, 29504k reserved, 2150k data, 544k init, 129608k highmem)
[    0.000000] virtual kernel memory layout:
[    0.000000]     fixmap  : 0xfff1d000 - 0xfffff000   ( 904 kB)
[    0.000000]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[    0.000000]     vmalloc : 0xf7ffe000 - 0xff7fe000   ( 120 MB)
[    0.000000]     lowmem  : 0xc0000000 - 0xf77fe000   ( 887 MB)
[    0.000000]       .init : 0xc0794000 - 0xc081c000   ( 544 kB)
[    0.000000]       .data : 0xc0579e48 - 0xc0793848   (2150 kB)
[    0.000000]       .text : 0xc0100000 - 0xc0579e48   (4583 kB)
[    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.000000] SLUB: Genslabs=13, HWalign=64, Order=0-3, MinObjects=0, CPUs=2, Nodes=1
[    0.000000] NR_IRQS:2304 nr_irqs:424
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 1596.647 MHz processor.
[    0.001724] Console: colour VGA+ 80x25
[    0.001728] console [tty0] enabled
[    0.001934] hpet clockevent registered
[    0.001938] HPET: 3 timers in total, 0 timers will be used for per-cpu timer
[    0.001946] Calibrating delay loop (skipped), value calculated using timer frequency.. 3193.29 BogoMIPS (lpj=6386588)
[    0.001970] Security Framework initialized
[    0.001996] AppArmor: AppArmor initialized
[    0.002004] Mount-cache hash table entries: 512
[    0.002171] Initializing cgroup subsys ns
[    0.002177] Initializing cgroup subsys cpuacct
[    0.002182] Initializing cgroup subsys memory
[    0.002192] Initializing cgroup subsys devices
[    0.002195] Initializing cgroup subsys freezer
[    0.002198] Initializing cgroup subsys net_cls
[    0.002216] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.002219] CPU: L2 cache: 1024K
[    0.002226] mce: CPU supports 6 MCE banks
[    0.002235] CPU0: Thermal monitoring handled by SMI
[    0.002240] using mwait in idle threads.
[    0.002248] Performance Counters: Core2 events, Intel PMU driver.
[    0.002259] ... version:                 2
[    0.002261] ... bit width:               40
[    0.002264] ... generic counters:        2
[    0.002267] ... value mask:              000000ffffffffff
[    0.002269] ... max period:              000000007fffffff
[    0.002271] ... fixed-purpose counters:  3
[    0.002273] ... counter mask:            0000000700000003
[    0.002278] Checking 'hlt' instruction... OK.
[    0.017007] SMP alternatives: switching to UP code
[    0.024007] ACPI: Core revision 20090521
[    0.036452] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.078522] CPU0: Intel(R) Celeron(R) M CPU        520  @ 1.60GHz stepping 06
[    0.080001] Brought up 1 CPUs
[    0.080001] Total of 1 processors activated (3193.29 BogoMIPS).
[    0.080001] CPU0 attaching NULL sched-domain.
[    0.080001] Booting paravirtualized kernel on bare hardware
[    0.080001] regulator: core version 0.5
[    0.080001] Time: 11:19:41  Date: 04/21/11
[    0.080001] NET: Registered protocol family 16
[    0.080001] EISA bus registered
[    0.080001] ACPI: bus type pci registered
[    0.080001] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 255
[    0.080001] PCI: MCFG area at e0000000 reserved in E820
[    0.080001] PCI: Using MMCONFIG for extended config space
[    0.080001] PCI: Using configuration type 1 for base access
[    0.080001] bio: create slab <bio-0> at 0
[    0.080001] ACPI: EC: Look up EC in DSDT
[    0.081758] ACPI: EC: non-query interrupt received, switching to interrupt mode
[    0.088144] ACPI: Interpreter enabled
[    0.088165] ACPI: (supports S0 S3 S4 S5)
[    0.088189] ACPI: Using IOAPIC for interrupt routing
[    0.092285] [Firmware Bug]: ACPI: ACPI brightness control misses _BQC function
[    0.092416] [Firmware Bug]: ACPI: ACPI brightness control misses _BQC function
[    0.096099] ACPI: EC: GPE = 0x17, I/O: command/status = 0x66, data = 0x62
[    0.096102] ACPI: EC: driver started in interrupt mode
[    0.096523] ACPI: No dock devices found.
[    0.097108] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.097218] pci 0000:00:02.0: reg 10 32bit mmio: [0xd4100000-0xd417ffff]
[    0.097225] pci 0000:00:02.0: reg 14 io port: [0x1800-0x1807]
[    0.097231] pci 0000:00:02.0: reg 18 32bit mmio: [0xc0000000-0xcfffffff]
[    0.097237] pci 0000:00:02.0: reg 1c 32bit mmio: [0xd4200000-0xd423ffff]
[    0.097288] pci 0000:00:02.1: reg 10 32bit mmio: [0xd4180000-0xd41fffff]
[    0.097423] pci 0000:00:1b.0: reg 10 64bit mmio: [0xd4240000-0xd4243fff]
[    0.097492] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    0.097497] pci 0000:00:1b.0: PME# disabled
[    0.097594] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    0.097600] pci 0000:00:1c.0: PME# disabled
[    0.097679] pci 0000:00:1d.0: reg 20 io port: [0x1820-0x183f]
[    0.097751] pci 0000:00:1d.1: reg 20 io port: [0x1840-0x185f]
[    0.097823] pci 0000:00:1d.2: reg 20 io port: [0x1860-0x187f]
[    0.097895] pci 0000:00:1d.3: reg 20 io port: [0x1880-0x189f]
[    0.097971] pci 0000:00:1d.7: reg 10 32bit mmio: [0xd4444000-0xd44443ff]
[    0.098041] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
[    0.098047] pci 0000:00:1d.7: PME# disabled
[    0.098233] pci 0000:00:1f.0: quirk: region 1000-107f claimed by ICH6 ACPI/GPIO/TCO
[    0.098238] pci 0000:00:1f.0: quirk: region 1180-11bf claimed by ICH6 GPIO
[    0.098243] pci 0000:00:1f.0: ICH7 LPC Generic IO decode 1 PIO at 164c (mask 0007)
[    0.098248] pci 0000:00:1f.0: ICH7 LPC Generic IO decode 2 PIO at 0068 (mask 0007)
[    0.098309] pci 0000:00:1f.1: reg 10 io port: [0x00-0x07]
[    0.098318] pci 0000:00:1f.1: reg 14 io port: [0x00-0x03]
[    0.098327] pci 0000:00:1f.1: reg 18 io port: [0x00-0x07]
[    0.098336] pci 0000:00:1f.1: reg 1c io port: [0x00-0x03]
[    0.098345] pci 0000:00:1f.1: reg 20 io port: [0x1810-0x181f]
[    0.098420] pci 0000:00:1f.2: reg 10 io port: [0x18d0-0x18d7]
[    0.098429] pci 0000:00:1f.2: reg 14 io port: [0x18c4-0x18c7]
[    0.098438] pci 0000:00:1f.2: reg 18 io port: [0x18c8-0x18cf]
[    0.098447] pci 0000:00:1f.2: reg 1c io port: [0x18c0-0x18c3]
[    0.098456] pci 0000:00:1f.2: reg 20 io port: [0x18b0-0x18bf]
[    0.098465] pci 0000:00:1f.2: reg 24 32bit mmio: [0xd4444400-0xd44447ff]
[    0.098506] pci 0000:00:1f.2: PME# supported from D3hot
[    0.098512] pci 0000:00:1f.2: PME# disabled
[    0.098583] pci 0000:00:1f.3: reg 20 io port: [0x18e0-0x18ff]
[    0.098707] pci 0000:02:00.0: reg 10 64bit mmio: [0xd2000000-0xd2003fff]
[    0.098719] pci 0000:02:00.0: reg 18 io port: [0x2000-0x20ff]
[    0.098815] pci 0000:02:00.0: supports D1 D2
[    0.098818] pci 0000:02:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.098825] pci 0000:02:00.0: PME# disabled
[    0.098898] pci 0000:00:1c.0: bridge io port: [0x2000-0x2fff]
[    0.098904] pci 0000:00:1c.0: bridge 32bit mmio: [0xd2000000-0xd3ffffff]
[    0.098913] pci 0000:00:1c.0: bridge 64bit mmio pref: [0xd0000000-0xd1ffffff]
[    0.098986] pci 0000:03:09.0: reg 10 32bit mmio: [0x000000-0x000fff]
[    0.099017] pci 0000:03:09.0: supports D1 D2
[    0.099020] pci 0000:03:09.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.099026] pci 0000:03:09.0: PME# disabled
[    0.099080] pci 0000:03:09.1: reg 10 32bit mmio: [0xd4005000-0xd40057ff]
[    0.099091] pci 0000:03:09.1: reg 14 32bit mmio: [0xd4000000-0xd4003fff]
[    0.099161] pci 0000:03:09.1: supports D1 D2
[    0.099163] pci 0000:03:09.1: PME# supported from D0 D1 D2 D3hot
[    0.099169] pci 0000:03:09.1: PME# disabled
[    0.099222] pci 0000:03:09.2: reg 10 32bit mmio: [0xd4004000-0xd4004fff]
[    0.099297] pci 0000:03:09.2: supports D1 D2
[    0.099299] pci 0000:03:09.2: PME# supported from D0 D1 D2 D3hot
[    0.099305] pci 0000:03:09.2: PME# disabled
[    0.099368] pci 0000:00:1e.0: transparent bridge
[    0.099377] pci 0000:00:1e.0: bridge 32bit mmio: [0xd4000000-0xd40fffff]
[    0.099425] pci_bus 0000:00: on NUMA node 0
[    0.099430] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.099714] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP01._PRT]
[    0.099840] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCIB._PRT]
[    0.102554] ACPI: PCI Interrupt Link [LNKA] (IRQs 1 3 4 5 6 7 10 12 14 15) *11
[    0.102676] ACPI: PCI Interrupt Link [LNKB] (IRQs 1 3 4 5 6 7 *11 12 14 15)
[    0.102793] ACPI: PCI Interrupt Link [LNKC] (IRQs 1 3 4 5 6 7 *10 12 14 15)
[    0.102906] ACPI: PCI Interrupt Link [LNKD] (IRQs 1 3 4 5 6 7 11 12 14 15) *10
[    0.103024] ACPI: PCI Interrupt Link [LNKE] (IRQs 1 3 4 5 6 7 10 12 14 15) *0, disabled.
[    0.103144] ACPI: PCI Interrupt Link [LNKF] (IRQs 1 3 4 5 6 7 11 12 14 15) *0, disabled.
[    0.103259] ACPI: PCI Interrupt Link [LNKG] (IRQs 1 3 4 5 6 7 *10 12 14 15)
[    0.103372] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 *11 12 14 15)
[    0.103580] SCSI subsystem initialized
[    0.103640] libata version 3.00 loaded.
[    0.103726] usbcore: registered new interface driver usbfs
[    0.103740] usbcore: registered new interface driver hub
[    0.103767] usbcore: registered new device driver usb
[    0.103909] ACPI: WMI: Mapper loaded
[    0.103911] PCI: Using ACPI for IRQ routing
[    0.104101] Bluetooth: Core ver 2.15
[    0.104133] NET: Registered protocol family 31
[    0.104135] Bluetooth: HCI device and connection manager initialized
[    0.104138] Bluetooth: HCI socket layer initialized
[    0.104141] NetLabel: Initializing
[    0.104143] NetLabel:  domain hash size = 128
[    0.104144] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.104158] NetLabel:  unlabeled traffic allowed by default
[    0.104192] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[    0.104198] hpet0: 3 comparators, 64-bit 14.318180 MHz counter
[    0.109723] pnp: PnP ACPI init
[    0.109748] ACPI: bus type pnp registered
[    0.112801] pnp: PnP ACPI: found 9 devices
[    0.112804] ACPI: ACPI bus type pnp unregistered
[    0.112810] PnPBIOS: Disabled by ACPI PNP
[    0.112823] system 00:01: iomem range 0xe0000000-0xefffffff has been reserved
[    0.112827] system 00:01: iomem range 0xfed14000-0xfed17fff has been reserved
[    0.112831] system 00:01: iomem range 0xfed18000-0xfed18fff has been reserved
[    0.112834] system 00:01: iomem range 0xfed19000-0xfed19fff has been reserved
[    0.112837] system 00:01: iomem range 0xfed1c000-0xfed1ffff has been reserved
[    0.112841] system 00:01: iomem range 0xfed20000-0xfed3ffff has been reserved
[    0.112844] system 00:01: iomem range 0xfed45000-0xfed8ffff has been reserved
[    0.112855] system 00:03: iomem range 0xfed00000-0xfed003ff has been reserved
[    0.112862] system 00:05: ioport range 0x800-0x80f has been reserved
[    0.112866] system 00:05: ioport range 0x1000-0x107f has been reserved
[    0.112869] system 00:05: ioport range 0x1180-0x11bf has been reserved
[    0.112872] system 00:05: ioport range 0x1640-0x164f has been reserved
[    0.112876] system 00:05: ioport range 0xfe00-0xfe00 has been reserved
[    0.112879] system 00:05: iomem range 0xff000000-0xffffffff has been reserved
[    0.147572] AppArmor: AppArmor Filesystem Enabled
[    0.147617] pci 0000:00:1c.0: PCI bridge, secondary bus 0000:02
[    0.147622] pci 0000:00:1c.0:   IO window: 0x2000-0x2fff
[    0.147629] pci 0000:00:1c.0:   MEM window: 0xd2000000-0xd3ffffff
[    0.147636] pci 0000:00:1c.0:   PREFETCH window: 0x000000d0000000-0x000000d1ffffff
[    0.147652] pci 0000:03:09.0: CardBus bridge, secondary bus 0000:04
[    0.147655] pci 0000:03:09.0:   IO window: 0x003000-0x0030ff
[    0.147661] pci 0000:03:09.0:   IO window: 0x003400-0x0034ff
[    0.147668] pci 0000:03:09.0:   PREFETCH window: 0x40000000-0x43ffffff
[    0.147675] pci 0000:03:09.0:   MEM window: 0x44000000-0x47ffffff
[    0.147681] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:03
[    0.147686] pci 0000:00:1e.0:   IO window: 0x3000-0x3fff
[    0.147693] pci 0000:00:1e.0:   MEM window: 0xd4000000-0xd40fffff
[    0.147699] pci 0000:00:1e.0:   PREFETCH window: 0x40000000-0x43ffffff
[    0.147715]   alloc irq_desc for 17 on node -1
[    0.147717]   alloc kstat_irqs on node -1
[    0.147725] pci 0000:00:1c.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    0.147732] pci 0000:00:1c.0: setting latency timer to 64
[    0.147739] pci 0000:00:1e.0: enabling device (0004 -> 0007)
[    0.147746] pci 0000:00:1e.0: setting latency timer to 64
[    0.147757] pci 0000:03:09.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    0.147766] pci_bus 0000:00: resource 0 io:  [0x00-0xffff]
[    0.147769] pci_bus 0000:00: resource 1 mem: [0x000000-0xffffffff]
[    0.147772] pci_bus 0000:02: resource 0 io:  [0x2000-0x2fff]
[    0.147775] pci_bus 0000:02: resource 1 mem: [0xd2000000-0xd3ffffff]
[    0.147778] pci_bus 0000:02: resource 2 pref mem [0xd0000000-0xd1ffffff]
[    0.147781] pci_bus 0000:03: resource 0 io:  [0x3000-0x3fff]
[    0.147784] pci_bus 0000:03: resource 1 mem: [0xd4000000-0xd40fffff]
[    0.147787] pci_bus 0000:03: resource 2 pref mem [0x40000000-0x43ffffff]
[    0.147790] pci_bus 0000:03: resource 3 io:  [0x00-0xffff]
[    0.147793] pci_bus 0000:03: resource 4 mem: [0x000000-0xffffffff]
[    0.147796] pci_bus 0000:04: resource 0 io:  [0x3000-0x30ff]
[    0.147799] pci_bus 0000:04: resource 1 io:  [0x3400-0x34ff]
[    0.147802] pci_bus 0000:04: resource 2 pref mem [0x40000000-0x43ffffff]
[    0.147805] pci_bus 0000:04: resource 3 mem: [0x44000000-0x47ffffff]
[    0.147847] NET: Registered protocol family 2
[    0.147948] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.148289] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.148881] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.149282] TCP: Hash tables configured (established 131072 bind 65536)
[    0.149285] TCP reno registered
[    0.149425] NET: Registered protocol family 1
[    0.149509] Trying to unpack rootfs image as initramfs...
[    0.381577] Freeing initrd memory: 7465k freed
[    0.386286] Simple Boot Flag at 0x36 set to 0x1
[    0.386432] cpufreq-nforce2: No nForce2 chipset.
[    0.386466] Scanning for low memory corruption every 60 seconds
[    0.386598] audit: initializing netlink socket (disabled)
[    0.386622] type=2000 audit(1303384780.383:1): initialized
[    0.397363] highmem bounce pool size: 64 pages
[    0.397370] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    0.398962] VFS: Disk quotas dquot_6.5.2
[    0.399024] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.399645] fuse init (API version 7.12)
[    0.399739] msgmni has been set to 1732
[    0.399946] alg: No test for stdrng (krng)
[    0.399972] io scheduler noop registered
[    0.399975] io scheduler anticipatory registered
[    0.399977] io scheduler deadline registered
[    0.400027] io scheduler cfq registered (default)
[    0.400041] pci 0000:00:02.0: Boot video device
[    0.400284]   alloc irq_desc for 24 on node -1
[    0.400286]   alloc kstat_irqs on node -1
[    0.400300] pcieport-driver 0000:00:1c.0: irq 24 for MSI/MSI-X
[    0.400313] pcieport-driver 0000:00:1c.0: setting latency timer to 64
[    0.400434] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.400500] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.401884] ACPI: AC Adapter [ACAD] (off-line)
[    0.401963] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input0
[    0.401967] ACPI: Power Button [PWRF]
[    0.402020] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1
[    0.402023] ACPI: Power Button [PWRB]
[    0.402071] input: Sleep Button as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input2
[    0.402075] ACPI: Sleep Button [SLPB]
[    0.402131] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input3
[    0.403258] ACPI: Lid Switch [LID]
[    0.403952] Marking TSC unstable due to TSC halts in idle
[    0.403982] Switched to high resolution mode on CPU 0
[    0.404019] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[    0.404048] processor LNXCPU:00: registered as cooling_device0
[    0.415111] thermal LNXTHERM:01: registered as thermal_zone0
[    0.415123] ACPI: Thermal Zone [TZ00] (30 C)
[    0.415181] isapnp: Scanning for PnP cards...
[    0.769712] isapnp: No Plug & Play device found
[    0.771122] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    0.772860] brd: module loaded
[    0.773341] loop: module loaded
[    0.773425] input: Macintosh mouse button emulation as /devices/virtual/input/input4
[    0.773506] ahci 0000:00:1f.2: version 3.0
[    0.773523] ahci 0000:00:1f.2: power state changed by ACPI to D0
[    0.773536]   alloc irq_desc for 19 on node -1
[    0.773538]   alloc kstat_irqs on node -1
[    0.773546] ahci 0000:00:1f.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    0.773586]   alloc irq_desc for 25 on node -1
[    0.773588]   alloc kstat_irqs on node -1
[    0.773598] ahci 0000:00:1f.2: irq 25 for MSI/MSI-X
[    0.773698] ahci 0000:00:1f.2: AHCI 0001.0100 32 slots 4 ports 1.5 Gbps 0x5 impl SATA mode
[    0.773702] ahci 0000:00:1f.2: flags: 64bit ncq pm led clo pio slum part 
[    0.773708] ahci 0000:00:1f.2: setting latency timer to 64
[    0.773927] scsi0 : ahci
[    0.774120] scsi1 : ahci
[    0.774259] scsi2 : ahci
[    0.774502] scsi3 : ahci
[    0.774705] ata1: SATA max UDMA/133 abar m1024@0xd4444400 port 0xd4444500 irq 25
[    0.774708] ata2: DUMMY
[    0.774712] ata3: SATA max UDMA/133 abar m1024@0xd4444400 port 0xd4444600 irq 25
[    0.774714] ata4: DUMMY
[    0.774765] ata_piix 0000:00:1f.1: version 2.13
[    0.774780] ata_piix 0000:00:1f.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    0.774823] ata_piix 0000:00:1f.1: setting latency timer to 64
[    0.775182] scsi4 : ata_piix
[    0.775617] scsi5 : ata_piix
[    0.776268] ata5: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0x1810 irq 14
[    0.776272] ata6: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x1818 irq 15
[    0.777144] Fixed MDIO Bus: probed
[    0.777188] PPP generic driver version 2.4.2
[    0.777390] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.777414]   alloc irq_desc for 23 on node -1
[    0.777416]   alloc kstat_irqs on node -1
[    0.777424] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    0.777443] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    0.777447] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    0.777494] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 1
[    0.777500] ehci_hcd 0000:00:1d.7: using broken periodic workaround
[    0.781411] ehci_hcd 0000:00:1d.7: debug port 1
[    0.781419] ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported
[    0.781597] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xd4444000
[    0.785863] ata6: port disabled. ignoring.
[    0.796062] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    0.796191] usb usb1: configuration #1 chosen from 1 choice
[    0.796224] hub 1-0:1.0: USB hub found
[    0.796233] hub 1-0:1.0: 8 ports detected
[    0.796304] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.796328] uhci_hcd: USB Universal Host Controller Interface driver
[    0.796365] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    0.796374] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    0.796378] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    0.796415] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    0.796445] uhci_hcd 0000:00:1d.0: irq 23, io base 0x00001820
[    0.796531] usb usb2: configuration #1 chosen from 1 choice
[    0.796559] hub 2-0:1.0: USB hub found
[    0.796567] hub 2-0:1.0: 2 ports detected
[    0.796617] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    0.796625] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    0.796629] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    0.796658] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 3
[    0.796700] uhci_hcd 0000:00:1d.1: irq 19, io base 0x00001840
[    0.796791] usb usb3: configuration #1 chosen from 1 choice
[    0.796818] hub 3-0:1.0: USB hub found
[    0.796826] hub 3-0:1.0: 2 ports detected
[    0.796875]   alloc irq_desc for 18 on node -1
[    0.796878]   alloc kstat_irqs on node -1
[    0.796884] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.796891] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    0.796895] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    0.796927] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 4
[    0.796964] uhci_hcd 0000:00:1d.2: irq 18, io base 0x00001860
[    0.797047] usb usb4: configuration #1 chosen from 1 choice
[    0.797078] hub 4-0:1.0: USB hub found
[    0.797086] hub 4-0:1.0: 2 ports detected
[    0.797128]   alloc irq_desc for 16 on node -1
[    0.797131]   alloc kstat_irqs on node -1
[    0.797135] uhci_hcd 0000:00:1d.3: PCI INT D -> GSI 16 (level, low) -> IRQ 16
[    0.797143] uhci_hcd 0000:00:1d.3: setting latency timer to 64
[    0.797147] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[    0.797177] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 5
[    0.797213] uhci_hcd 0000:00:1d.3: irq 16, io base 0x00001880
[    0.797294] usb usb5: configuration #1 chosen from 1 choice
[    0.797324] hub 5-0:1.0: USB hub found
[    0.797332] hub 5-0:1.0: 2 ports detected
[    0.797438] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2P] at 0x60,0x64 irq 1,12
[    0.800579] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.800588] serio: i8042 AUX port at 0x60,0x64 irq 12
[    0.800923] mice: PS/2 mouse device common for all mice
[    0.801085] rtc_cmos 00:06: RTC can wake from S4
[    0.801125] rtc_cmos 00:06: rtc core: registered rtc_cmos as rtc0
[    0.801159] rtc0: alarms up to one month, y3k, 242 bytes nvram, hpet irqs
[    0.801277] device-mapper: uevent: version 1.0.3
[    0.801386] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: dm-devel@redhat.com
[    0.803158] device-mapper: multipath: version 1.1.0 loaded
[    0.803161] device-mapper: multipath round-robin: version 1.0.0 loaded
[    0.803290] EISA: Probing bus 0 at eisa.0
[    0.803297] Cannot allocate resource for EISA slot 1
[    0.803300] Cannot allocate resource for EISA slot 2
[    0.803303] Cannot allocate resource for EISA slot 3
[    0.803325] EISA: Detected 0 cards.
[    0.803413] cpuidle: using governor ladder
[    0.803481] cpuidle: using governor menu
[    0.803970] TCP cubic registered
[    0.804162] NET: Registered protocol family 10
[    0.804600] lo: Disabled Privacy Extensions
[    0.804904] NET: Registered protocol family 17
[    0.804926] Bluetooth: L2CAP ver 2.13
[    0.804928] Bluetooth: L2CAP socket layer initialized
[    0.804931] Bluetooth: SCO (Voice Link) ver 0.6
[    0.804933] Bluetooth: SCO socket layer initialized
[    0.804965] Bluetooth: RFCOMM TTY layer initialized
[    0.804969] Bluetooth: RFCOMM socket layer initialized
[    0.804971] Bluetooth: RFCOMM ver 1.11
[    0.805003] Using IPI No-Shortcut mode
[    0.805076] PM: Resume from disk failed.
[    0.805090] registered taskstats version 1
[    0.805214]   Magic number: 7:3:328
[    0.805320] rtc_cmos 00:06: setting system clock to 2011-04-21 11:19:41 UTC (1303384781)
[    0.805323] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.805325] EDD information not available.
[    0.838015] ACPI: Battery Slot [BAT1] (battery present)
[    0.868430] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input5
[    0.948423] ata5.00: ATAPI: Optiarc DVD RW AD-7530A, EX32, max UDMA/33
[    0.964334] ata5.00: configured for UDMA/33
[    1.000027] Clocksource tsc unstable (delta = -166205208 ns)
[    1.100044] ata3: SATA link down (SStatus 0 SControl 300)
[    1.164035] usb 1-5: new high speed USB device using ehci_hcd and address 3
[    1.302746] usb 1-5: configuration #1 chosen from 1 choice
[    1.428044] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    1.429023] ata1.00: ACPI cmd ef/10:03:00:00:00:a0 filtered out
[    1.429170] ata1.00: ATA-7: Hitachi HTS541680J9SA00, SB2OC70P, max UDMA/100
[    1.429174] ata1.00: 156301488 sectors, multi 16: LBA48 NCQ (depth 31/32)
[    1.430333] ata1.00: ACPI cmd ef/10:03:00:00:00:a0 filtered out
[    1.430511] ata1.00: configured for UDMA/100
[    1.444166] scsi 0:0:0:0: Direct-Access     ATA      Hitachi HTS54168 SB2O PQ: 0 ANSI: 5
[    1.444304] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    1.444348] sd 0:0:0:0: [sda] 156301488 512-byte logical blocks: (80.0 GB/74.5 GiB)
[    1.444398] sd 0:0:0:0: [sda] Write Protect is off
[    1.444401] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.444428] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.444568]  sda:
[    1.445989] scsi 4:0:0:0: CD-ROM            Optiarc  DVD RW AD-7530A  EX32 PQ: 0 ANSI: 5
[    1.455912] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[    1.455916] Uniform CD-ROM driver Revision: 3.20
[    1.456022] sr 4:0:0:0: Attached scsi CD-ROM sr0
[    1.456069] sr 4:0:0:0: Attached scsi generic sg1 type 5
[    1.540033] usb 2-1: new low speed USB device using uhci_hcd and address 2
[    1.694584] usb 2-1: configuration #1 chosen from 1 choice
[    1.839304]  sda1 sda2
[    1.870319] sd 0:0:0:0: [sda] Attached SCSI disk
[    1.870336] Freeing unused kernel memory: 544k freed
[    1.870629] Write protecting the kernel text: 4584k
[    1.870662] Write protecting the kernel read-only data: 1844k
[    2.042854] [Firmware Bug]: ACPI: ACPI brightness control misses _BQC function
[    2.079380] acpi device:0a: registered as cooling_device1
[    2.079583] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:06/input/input6
[    2.079629] ACPI: Video Device [GFX0] (multi-head: yes  rom: no  post: no)
[    2.115424] Linux agpgart interface v0.103
[    2.118809] agpgart-intel 0000:00:00.0: Intel 945GM Chipset
[    2.119058] agpgart-intel 0000:00:00.0: detected 7932K stolen memory
[    2.125798] sky2 driver version 1.23
[    2.125846] sky2 0000:02:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    2.125861] sky2 0000:02:00.0: setting latency timer to 64
[    2.125888] sky2 0000:02:00.0: Yukon-2 FE chip revision 1
[    2.125997]   alloc irq_desc for 26 on node -1
[    2.126000]   alloc kstat_irqs on node -1
[    2.126018] sky2 0000:02:00.0: irq 26 for MSI/MSI-X
[    2.126671] sky2 eth0: addr 00:e0:b8:c5:fa:50
[    2.203298] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0xc0000000
[    2.218812] ohci1394 0000:03:09.1: enabling device (0000 -> 0002)
[    2.218824] ohci1394 0000:03:09.1: PCI INT B -> GSI 18 (level, low) -> IRQ 18
[    2.218834] ohci1394 0000:03:09.1: setting latency timer to 64
[    2.242039] usbcore: registered new interface driver hiddev
[    2.256959] input: HID 062a:0001 as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1:1.0/input/input7
[    2.257049] generic-usb 0003:062A:0001.0001: input,hidraw0: USB HID v1.10 Mouse [HID 062a:0001] on usb-0000:00:1d.0-1/input0
[    2.257069] usbcore: registered new interface driver usbhid
[    2.257072] usbhid: v2.6:USB HID core driver
[    2.291019] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[18]  MMIO=[d4005000-d40057ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[    2.291620] [drm] Initialized drm 1.1.0 20060810
[    2.305421] i915 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    2.305429] i915 0000:00:02.0: setting latency timer to 64
[    2.877580] [drm] TV-14: set mode NTSC 480i 0
[    3.005682] [drm] fb0: inteldrmfb frame buffer device
[    3.005693] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
[    3.078533] [drm] LVDS-8: set mode 1280x800 17
[    3.277481] Console: switching to colour frame buffer device 160x50
[    3.564141] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[00e0b8036609542d]
[    8.690727] EXT4-fs (sda1): barriers enabled
[    8.718213] kjournald2 starting: pid 415, dev sda1:8, commit interval 5 seconds
[    8.718247] EXT4-fs (sda1): delayed allocation enabled
[    8.718251] EXT4-fs: file extents enabled
[    8.723574] EXT4-fs: mballoc enabled
[    8.723592] EXT4-fs (sda1): mounted filesystem with ordered data mode
[    9.552492] type=1505 audit(1303384790.246:2): operation="profile_load" pid=439 name=/usr/share/gdm/guest-session/Xsession
[    9.555406] type=1505 audit(1303384790.246:3): operation="profile_load" pid=440 name=/sbin/dhclient3
[    9.556347] type=1505 audit(1303384790.250:4): operation="profile_load" pid=440 name=/usr/lib/NetworkManager/nm-dhcp-client.action
[    9.556854] type=1505 audit(1303384790.250:5): operation="profile_load" pid=440 name=/usr/lib/connman/scripts/dhclient-script
[    9.586629] type=1505 audit(1303384790.278:6): operation="profile_load" pid=441 name=/usr/bin/evince
[    9.601072] type=1505 audit(1303384790.294:7): operation="profile_load" pid=441 name=/usr/bin/evince-previewer
[    9.610027] type=1505 audit(1303384790.302:8): operation="profile_load" pid=441 name=/usr/bin/evince-thumbnailer
[    9.646618] type=1505 audit(1303384790.338:9): operation="profile_load" pid=443 name=/usr/lib/cups/backend/cups-pdf
[    9.647687] type=1505 audit(1303384790.338:10): operation="profile_load" pid=443 name=/usr/sbin/cupsd
[    9.651111] type=1505 audit(1303384790.342:11): operation="profile_load" pid=444 name=/usr/sbin/mysqld
[   11.928879] Adding 2184832k swap on /dev/sda2.  Priority:-1 extents:1 across:2184832k 
[   13.353068] udev: starting version 147
[   13.469303] EXT4-fs (sda1): internal journal on sda1:8
[   14.795570] intel_rng: FWH not detected
[   14.930487] lp: driver loaded but no devices found
[   15.260591] cfg80211: Calling CRDA to update world regulatory domain
[   15.675616] yenta_cardbus 0000:03:09.0: CardBus bridge found [107b:0366]
[   15.675642] yenta_cardbus 0000:03:09.0: Using CSCINT to route CSC interrupts to PCI
[   15.675645] yenta_cardbus 0000:03:09.0: Routing CardBus interrupts to PCI
[   15.675652] yenta_cardbus 0000:03:09.0: TI: mfunc 0x01ac1b22, devctl 0x64
[   15.725929] Synaptics Touchpad, model: 1, fw: 5.9, id: 0x23aeb3, caps: 0xa04713/0x10008
[   15.758562] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input8
[   15.863161] ip_tables: (C) 2000-2006 Netfilter Core Team
[   15.905883] yenta_cardbus 0000:03:09.0: ISA IRQ mask 0x0cf8, PCI irq 17
[   15.905889] yenta_cardbus 0000:03:09.0: Socket status: 30000006
[   15.905894] pci_bus 0000:03: Raising subordinate bus# of parent bus (#03) from #04 to #07
[   15.905905] yenta_cardbus 0000:03:09.0: pcmcia: parent PCI bridge I/O window: 0x3000 - 0x3fff
[   15.905909] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x3000-0x3fff: clean.
[   15.906145] yenta_cardbus 0000:03:09.0: pcmcia: parent PCI bridge Memory window: 0xd4000000 - 0xd40fffff
[   15.906148] yenta_cardbus 0000:03:09.0: pcmcia: parent PCI bridge Memory window: 0x40000000 - 0x43ffffff
[   15.907736] tifm_7xx1 0000:03:09.2: enabling device (0000 -> 0002)
[   15.907746] tifm_7xx1 0000:03:09.2: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   15.907756] tifm_7xx1 0000:03:09.2: setting latency timer to 64
[   17.025738] cfg80211: World regulatory domain updated:
[   17.025743] 	(start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   17.025747] 	(2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   17.025750] 	(2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   17.025753] 	(2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   17.025756] 	(5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   17.025759] 	(5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   17.088612] phy0: Selected rate control algorithm 'minstrel'
[   17.089283] phy0: hwaddr 00:c0:a8:e1:49:c7, RTL8187vB (default) V1 + rtl8225z2
[   17.100452] rtl8187: Customer ID is 0x00
[   17.100495] Registered led device: rtl8187-phy0::tx
[   17.100514] Registered led device: rtl8187-phy0::rx
[   17.100541] usbcore: registered new interface driver rtl8187
[   17.104299] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x100-0x3af: clean.
[   17.106350] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x3e0-0x4ff: excluding 0x4d0-0x4d7
[   17.107214] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x820-0x8ff: clean.
[   17.107928] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xc00-0xcf7: clean.
[   17.112677] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xa00-0xaff: clean.
[   19.058273]   alloc irq_desc for 22 on node -1
[   19.058277]   alloc kstat_irqs on node -1
[   19.058286] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[   19.058335] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   19.888574] __ratelimit: 3 callbacks suppressed
[   19.888578] type=1505 audit(1303384800.582:13): operation="profile_replace" pid=869 name=/usr/share/gdm/guest-session/Xsession
[   19.890817] type=1505 audit(1303384800.582:14): operation="profile_replace" pid=870 name=/sbin/dhclient3
[   19.891741] type=1505 audit(1303384800.582:15): operation="profile_replace" pid=870 name=/usr/lib/NetworkManager/nm-dhcp-client.action
[   19.892272] type=1505 audit(1303384800.586:16): operation="profile_replace" pid=870 name=/usr/lib/connman/scripts/dhclient-script
[   19.897609] type=1505 audit(1303384800.590:17): operation="profile_replace" pid=871 name=/usr/bin/evince
[   19.925027] type=1505 audit(1303384800.618:18): operation="profile_replace" pid=871 name=/usr/bin/evince-previewer
[   19.942085] type=1505 audit(1303384800.634:19): operation="profile_replace" pid=871 name=/usr/bin/evince-thumbnailer
[   19.965633] type=1505 audit(1303384800.658:20): operation="profile_replace" pid=876 name=/usr/lib/cups/backend/cups-pdf
[   19.966706] type=1505 audit(1303384800.658:21): operation="profile_replace" pid=876 name=/usr/sbin/cupsd
[   19.969904] type=1505 audit(1303384800.662:22): operation="profile_replace" pid=877 name=/usr/sbin/mysqld
[   19.996315] input: HDA Intel Mic at Ext Front Jack as /devices/pci0000:00/0000:00:1b.0/sound/card0/input9
[   25.191815] __ratelimit: 12 callbacks suppressed
[   25.191819] type=1503 audit(1303384805.882:27): operation="open" pid=1147 parent=1146 profile="/usr/sbin/mysqld" requested_mask="r::" denied_mask="r::" fsuid=0 ouid=0 name="/sys/devices/system/cpu/"
[   26.211597] type=1503 audit(1303384806.902:28): operation="open" pid=1161 parent=1160 profile="/usr/sbin/mysqld" requested_mask="r::" denied_mask="r::" fsuid=0 ouid=0 name="/sys/devices/system/cpu/"
[   27.230310] type=1503 audit(1303384807.922:29): operation="open" pid=1232 parent=1231 profile="/usr/sbin/mysqld" requested_mask="r::" denied_mask="r::" fsuid=0 ouid=0 name="/sys/devices/system/cpu/"
[   28.259529] type=1503 audit(1303384808.950:30): operation="open" pid=1243 parent=1242 profile="/usr/sbin/mysqld" requested_mask="r::" denied_mask="r::" fsuid=0 ouid=0 name="/sys/devices/system/cpu/"
[   29.274811] type=1503 audit(1303384809.966:31): operation="open" pid=1285 parent=1284 profile="/usr/sbin/mysqld" requested_mask="r::" denied_mask="r::" fsuid=0 ouid=0 name="/sys/devices/system/cpu/"
[   29.895308] sky2 eth0: enabling interface
[   29.895545] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   30.293422] type=1503 audit(1303384810.986:32): operation="open" pid=1303 parent=1302 profile="/usr/sbin/mysqld" requested_mask="r::" denied_mask="r::" fsuid=0 ouid=0 name="/sys/devices/system/cpu/"
[   31.311945] type=1503 audit(1303384812.002:33): operation="open" pid=1316 parent=1315 profile="/usr/sbin/mysqld" requested_mask="r::" denied_mask="r::" fsuid=0 ouid=0 name="/sys/devices/system/cpu/"
[   32.009558] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   33.062611] type=1503 audit(1303384813.754:34): operation="open" pid=1371 parent=1370 profile="/usr/sbin/mysqld" requested_mask="r::" denied_mask="r::" fsuid=0 ouid=0 name="/sys/devices/system/cpu/"
[   33.121260] type=1503 audit(1303384813.814:35): operation="open" pid=1382 parent=1381 profile="/usr/sbin/mysqld" requested_mask="r::" denied_mask="r::" fsuid=0 ouid=0 name="/sys/devices/system/cpu/"
[   34.974883] ppdev: user-space parallel port driver
[   36.307309] [drm] TV-14: set mode NTSC 480i 0
[   36.449482] [drm] TV-14: set mode NTSC 480i 0
[   36.903020] [drm] TV-14: set mode NTSC 480i 0
[   37.078170] [drm] TV-14: set mode NTSC 480i 0
[   43.816079] [drm] TV-14: set mode NTSC 480i 0
[   43.960610] [drm] TV-14: set mode NTSC 480i 0
[   44.275792] [drm] TV-14: set mode NTSC 480i 0
[   44.421449] [drm] TV-14: set mode NTSC 480i 0
[   44.735987] [drm] TV-14: set mode NTSC 480i 0
[   44.880708] [drm] TV-14: set mode NTSC 480i 0
[   63.894987] [drm] TV-14: set mode NTSC 480i 0
[   64.045611] [drm] TV-14: set mode NTSC 480i 0
[   64.380668] [drm] TV-14: set mode NTSC 480i 0
[   64.543674] [drm] TV-14: set mode NTSC 480i 0
[   64.828949] [drm] TV-14: set mode NTSC 480i 0
[   64.976137] [drm] TV-14: set mode NTSC 480i 0
[   66.558001] [drm] TV-14: set mode NTSC 480i 0
[   66.701450] [drm] TV-14: set mode NTSC 480i 0
[   77.025266] wlan0: authenticate with AP 00:1b:2f:a4:53:0a
[   77.026883] wlan0: authenticated
[   77.026886] wlan0: associate with AP 00:1b:2f:a4:53:0a
[   77.029521] wlan0: RX AssocResp from 00:1b:2f:a4:53:0a (capab=0x471 status=0 aid=2)
[   77.029524] wlan0: associated
[   77.033805] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   87.628034] wlan0: no IPv6 routers present
```

---

### Post by dino99 on 2011-04-21
sudo dpkg --configure -phigh -a

(wait job done )

---

### Post by desconocido on 2011-04-23
> **dino99 said:**
> sudo dpkg --configure -phigh -a

(wait job done )
Thanks. What would that do?

---

