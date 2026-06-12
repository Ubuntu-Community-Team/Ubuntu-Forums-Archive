---
title: "Iomega Prestige 1tb external drive not recognised in usb 3.0 port..."
date: 2011-06-23
forum: General Help
---

### Post by kimangroo on 2011-06-23
I have the above drive and it is recognized in usb 2.0 ports in natty fine, however it is not recognised in the usb 3.0 port.

It shows up in lsusb, but nothing in fdisk -l. The disk utility can find it as well but reports firmware is 0000, and can't get any details from it.

The port isn't faulty as it works fine on windows with some very nice speeds.

I read one thread suggesting that some companies' firmware just isn't compatible with linux but I booted parted magic and it recognised the drive in both the usb 2 and 3 ports... and I could mount it fine.

So the drive should be able to work with linux...

Another thread suggested adding pci=nomsi to grub. I tried this and no change....

Can anyone give me any advice as how to get it to work? Or at least how I should go about debugging...

Thanks!

---

### Post by kimangroo on 2011-06-24
*bump*

anyone able to point me in the direction I should be looking?

---

### Post by kimangroo on 2011-06-26
*bump*

Not even a hint?!!

---

### Post by kimangroo on 2011-06-27
Ok I rebooted partedmagic just to check it really was using the drive as usb 3.0, and compared speeds copying a dvd onto  the external drive using the usb 2.0 port and the usb 3.0 port. I got approx twice the speeds using the usb 3.0 port, so I guess it is working properly.

Here is the output of the var/log/messages file with partedmagic using kernel 2.6.38.4-pmagic:

```
Jun 27 15:49:01 (none) syslog.info syslogd started: BusyBox v1.18.4
Jun 27 15:49:01 (none) user.notice kernel: klogd started: BusyBox v1.18.4 (2011-04-09 18:34:08 CDT)
Jun 27 15:49:01 (none) user.info kernel: or memmap
Jun 27 15:49:01 (none) user.debug kernel: [    0.000000]   Normal zone: 186942 pages, LIFO batch:31
Jun 27 15:49:01 (none) user.debug kernel: [    0.000000]   HighMem zone: 3457 pages used for memmap
Jun 27 15:49:01 (none) user.debug kernel: [    0.000000]   HighMem zone: 438465 pages, LIFO batch:31
Jun 27 15:49:01 (none) user.info kernel: [    0.000000] Using APIC driver default
Jun 27 15:49:01 (none) user.info kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x408
Jun 27 15:49:01 (none) user.debug kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
Jun 27 15:49:01 (none) user.info kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
Jun 27 15:49:01 (none) user.info kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
Jun 27 15:49:01 (none) user.info kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x02] enabled)
Jun 27 15:49:01 (none) user.info kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x03] enabled)
Jun 27 15:49:01 (none) user.info kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x05] lapic_id[0x00] disabled)
Jun 27 15:49:01 (none) user.info kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x06] lapic_id[0x00] disabled)
Jun 27 15:49:01 (none) user.info kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x07] lapic_id[0x00] disabled)
Jun 27 15:49:01 (none) user.info kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x08] lapic_id[0x00] disabled)
Jun 27 15:49:01 (none) user.info kernel: [    0.000000] ACPI: IOAPIC (id[0x00] address[0xfec00000] gsi_base[0])
Jun 27 15:49:01 (none) user.info kernel: [    0.000000] IOAPIC[0]: apic_id 0, version 32, address 0xfec00000, GSI 0-23
Jun 27 15:49:01 (none) user.info kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
Jun 27 15:49:01 (none) user.info kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
Jun 27 15:49:01 (none) user.debug kernel: [    0.000000] ACPI: IRQ0 used by override.
Jun 27 15:49:01 (none) user.debug kernel: [    0.000000] ACPI: IRQ2 used by override.
Jun 27 15:49:01 (none) user.debug kernel: [    0.000000] ACPI: IRQ9 used by override.
Jun 27 15:49:01 (none) user.info kernel: [    0.000000] Using ACPI (MADT) for SMP configuration information
Jun 27 15:49:01 (none) user.info kernel: [    0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000
Jun 27 15:49:01 (none) user.info kernel: [    0.000000] SMP: Allowing 8 CPUs, 4 hotplug CPUs
Jun 27 15:49:01 (none) user.debug kernel: [    0.000000] nr_irqs_gsi: 40
Jun 27 15:49:01 (none) user.info kernel: [    0.000000] PM: Registered nosave memory: 0000000000094000 - 0000000000095000
Jun 27 15:49:01 (none) user.info kernel: [    0.000000] PM: Registered nosave memory: 0000000000095000 - 00000000000a0000
Jun 27 15:49:01 (none) user.info kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
Jun 27 15:49:01 (none) user.info kernel: [    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
Jun 27 15:49:01 (none) user.info kernel: [    0.000000] Allocating PCI resources starting at 9fa00000 (gap: 9fa00000:40600000)
Jun 27 15:49:01 (none) user.info kernel: [    0.000000] Booting paravirtualized kernel on bare hardware
Jun 27 15:49:01 (none) user.info kernel: [    0.000000] setup_percpu: NR_CPUS:32 nr_cpumask_bits:32 nr_cpu_ids:8 nr_node_ids:1
Jun 27 15:49:01 (none) user.info kernel: [    0.000000] PERCPU: Embedded 12 pages/cpu @eb800000 s27648 r0 d21504 u524288
Jun 27 15:49:01 (none) user.debug kernel: [    0.000000] pcpu-alloc: s27648 r0 d21504 u524288 alloc=1*4194304
Jun 27 15:49:01 (none) user.debug kernel: [    0.000000] pcpu-alloc: [0] 0 1 2 3 4 5 6 7 
Jun 27 15:49:01 (none) user.warn kernel: [    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 629347
Jun 27 15:49:01 (none) user.notice kernel: [    0.000000] Kernel command line: edd=off load_ramdisk=1 prompt_ramdisk=0 rw vga=normal loglevel=9 max_loop=256 vmalloc=256MiB initrd=/pmagic/initramfs BOOT_IMAGE=/pmagic/bzImage 
Jun 27 15:49:01 (none) user.info kernel: [    0.000000] PID hash table entries: 4096 (order: 2, 16384 bytes)
Jun 27 15:49:01 (none) user.info kernel: [    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
Jun 27 15:49:01 (none) user.info kernel: [    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
Jun 27 15:49:01 (none) user.info kernel: [    0.000000] Initializing CPU#0
Jun 27 15:49:01 (none) user.info kernel: [    0.000000] xsave/xrstor: enabled xstate_bv 0x7, cntxt size 0x340
Jun 27 15:49:01 (none) user.info kernel: [    0.000000] allocated 12697280 bytes of page_cgroup
Jun 27 15:49:01 (none) user.info kernel: [    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
Jun 27 15:49:01 (none) user.info kernel: [    0.000000] Initializing HighMem for node 0 (0002effe:0009b000)
Jun 27 15:49:01 (none) user.info kernel: [    0.000000] Memory: 2467096k/2539520k available (4069k kernel code, 70136k reserved, 1577k data, 572k init, 1767688k highmem)
Jun 27 15:49:01 (none) user.info kernel: [    0.000000] virtual kernel memory layout:
Jun 27 15:49:01 (none) user.info kernel: [    0.000000]     fixmap  : 0xffd36000 - 0xfffff000   (2852 kB)
Jun 27 15:49:01 (none) user.info kernel: [    0.000000]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
Jun 27 15:49:01 (none) user.info kernel: [    0.000000]     vmalloc : 0xef7fe000 - 0xff7fe000   ( 256 MB)
Jun 27 15:49:01 (none) user.info kernel: [    0.000000]     lowmem  : 0xc0000000 - 0xeeffe000   ( 751 MB)
Jun 27 15:49:01 (none) user.info kernel: [    0.000000]       .init : 0xc1584000 - 0xc1613000   ( 572 kB)
Jun 27 15:49:01 (none) user.info kernel: [    0.000000]       .data : 0xc13f966d - 0xc1583d40   (1577 kB)
Jun 27 15:49:01 (none) user.info kernel: [    0.000000]       .text : 0xc1000000 - 0xc13f966d   (4069 kB)
Jun 27 15:49:01 (none) user.info kernel: [    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
Jun 27 15:49:01 (none) user.info kernel: [    0.000000] SLUB: Genslabs=15, HWalign=64, Order=0-3, MinObjects=0, CPUs=8, Nodes=1
Jun 27 15:49:01 (none) user.info kernel: [    0.000000] Hierarchical RCU implementation.
Jun 27 15:49:01 (none) user.info kernel: [    0.000000] 	RCU-based detection of stalled CPUs is disabled.
Jun 27 15:49:01 (none) user.info kernel: [    0.000000] NR_IRQS:1280
Jun 27 15:49:01 (none) user.debug kernel: [    0.000000] CPU 0 irqstacks, hard=ea40c000 soft=ea40e000
Jun 27 15:49:01 (none) user.info kernel: [    0.000000] Extended CMOS year: 2000
Jun 27 15:49:01 (none) user.warn kernel: [    0.000000] Console: colour VGA+ 80x25
Jun 27 15:49:01 (none) user.info kernel: [    0.000000] console [tty0] enabled
Jun 27 15:49:01 (none) user.debug kernel: [    0.000000] hpet clockevent registered
Jun 27 15:49:01 (none) user.warn kernel: [    0.000000] Fast TSC calibration using PIT
Jun 27 15:49:01 (none) user.warn kernel: [    0.001000] Detected 2494.474 MHz processor.
Jun 27 15:49:01 (none) user.info kernel: [    0.000002] Calibrating delay loop (skipped), value calculated using timer frequency.. 4988.94 BogoMIPS (lpj=2494474)
Jun 27 15:49:01 (none) user.info kernel: [    0.000155] pid_max: default: 32768 minimum: 301
Jun 27 15:49:01 (none) user.info kernel: [    0.000282] Security Framework initialized
Jun 27 15:49:01 (none) user.warn kernel: [    0.000386] Mount-cache hash table entries: 512
Jun 27 15:49:01 (none) user.info kernel: [    0.000646] Initializing cgroup subsys ns
Jun 27 15:49:01 (none) user.warn kernel: [    0.000721] ns_cgroup deprecated: consider using the 'clone_children' flag without the ns_cgroup.
Jun 27 15:49:01 (none) user.info kernel: [    0.000830] Initializing cgroup subsys cpuacct
Jun 27 15:49:01 (none) user.info kernel: [    0.000918] Initializing cgroup subsys memory
Jun 27 15:49:01 (none) user.info kernel: [    0.001001] Initializing cgroup subsys devices
Jun 27 15:49:01 (none) user.info kernel: [    0.001076] Initializing cgroup subsys freezer
Jun 27 15:49:01 (none) user.info kernel: [    0.001151] Initializing cgroup subsys net_cls
Jun 27 15:49:01 (none) user.info kernel: [    0.001226] Initializing cgroup subsys blkio
Jun 27 15:49:01 (none) user.info kernel: [    0.001343] CPU: Physical Processor ID: 0
Jun 27 15:49:01 (none) user.info kernel: [    0.001418] CPU: Processor Core ID: 0
Jun 27 15:49:01 (none) user.info kernel: [    0.001495] mce: CPU supports 7 MCE banks
Jun 27 15:49:01 (none) user.info kernel: [    0.001578] CPU0: Thermal monitoring enabled (TM1)
Jun 27 15:49:01 (none) user.info kernel: [    0.001658] using mwait in idle threads.
Jun 27 15:49:01 (none) user.info kernel: [    0.003606] ACPI: Core revision 20110112
Jun 27 15:49:01 (none) user.info kernel: [    0.021581] ftrace: allocating 18309 entries in 36 pages
Jun 27 15:49:01 (none) user.info kernel: [    0.028306] Enabling APIC mode:  Flat.  Using 1 I/O APICs
Jun 27 15:49:01 (none) user.info kernel: [    0.028737] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
Jun 27 15:49:01 (none) user.info kernel: [    0.038804] CPU0: Intel(R) Core(TM) i5-2520M CPU @ 2.50GHz stepping 07
Jun 27 15:49:01 (none) user.info kernel: [    0.140117] Performance Events: PEBS fmt1+, generic architected perfmon, Intel PMU driver.
Jun 27 15:49:01 (none) user.info kernel: [    0.140351] ... version:                3
Jun 27 15:49:01 (none) user.info kernel: [    0.140425] ... bit width:              48
Jun 27 15:49:01 (none) user.info kernel: [    0.140499] ... generic registers:      4
Jun 27 15:49:01 (none) user.info kernel: [    0.140573] ... value mask:             0000ffffffffffff
Jun 27 15:49:01 (none) user.info kernel: [    0.140650] ... max period:             000000007fffffff
Jun 27 15:49:01 (none) user.info kernel: [    0.140726] ... fixed-purpose events:   3
Jun 27 15:49:01 (none) user.info kernel: [    0.140800] ... event mask:             000000070000000f
Jun 27 15:49:01 (none) user.debug kernel: [    0.140998] CPU 1 irqstacks, hard=ea4d2000 soft=ea4d4000
Jun 27 15:49:01 (none) user.info kernel: [    0.141076] Booting Node   0, Processors  #1
Jun 27 15:49:01 (none) user.info kernel: [    0.151485] Initializing CPU#1
Jun 27 15:49:01 (none) user.debug kernel: [    0.232092] CPU 2 irqstacks, hard=ea4de000 soft=ea4e0000
Jun 27 15:49:01 (none) user.warn kernel: [    0.232310]  #2
Jun 27 15:49:01 (none) user.info kernel: [    0.242661] Initializing CPU#2
Jun 27 15:49:01 (none) user.debug kernel: [    0.323016] CPU 3 irqstacks, hard=ea4ea000 soft=ea4ec000
Jun 27 15:49:01 (none) user.warn kernel: [    0.323234]  #3
Jun 27 15:49:01 (none) user.info kernel: [    0.333583] Initializing CPU#3
Jun 27 15:49:01 (none) user.info kernel: [    0.413794] Brought up 4 CPUs
Jun 27 15:49:01 (none) user.info kernel: [    0.414006] Total of 4 processors activated (19953.03 BogoMIPS).
Jun 27 15:49:01 (none) user.info kernel: [    0.416399] devtmpfs: initialized
Jun 27 15:49:01 (none) user.info kernel: [    0.416749] atomic64 test passed for i586+ platform with CX8 and with SSE
Jun 27 15:49:01 (none) user.info kernel: [    0.416892] NET: Registered protocol family 16
Jun 27 15:49:01 (none) user.info kernel: [    0.417197] EISA bus registered
Jun 27 15:49:01 (none) user.info kernel: [    0.417279] ACPI: bus type pci registered
Jun 27 15:49:01 (none) user.info kernel: [    0.417477] PCI: MMCONFIG for domain 0000 [bus 00-ff] at [mem 0xe0000000-0xefffffff] (base 0xe0000000)
Jun 27 15:49:01 (none) user.info kernel: [    0.417587] PCI: MMCONFIG at [mem 0xe0000000-0xefffffff] reserved in E820
Jun 27 15:49:01 (none) user.info kernel: [    0.417666] PCI: Using MMCONFIG for extended config space
Jun 27 15:49:01 (none) user.info kernel: [    0.417745] PCI: Using configuration type 1 for base access
Jun 27 15:49:01 (none) user.warn kernel: [    0.419667] bio: create slab <bio-0> at 0
Jun 27 15:49:01 (none) user.debug kernel: [    0.421174] ACPI: EC: Look up EC in DSDT
Jun 27 15:49:01 (none) user.warn kernel: [    0.422516] ACPI: Executed 1 blocks of module-level executable AML code
Jun 27 15:49:01 (none) user.notice kernel: [    0.431749] [Firmware Bug]: ACPI: BIOS _OSI(Linux) query ignored
Jun 27 15:49:01 (none) user.warn kernel: [    0.439615] ACPI: SSDT 9ae70718 0067C (v01  PmRef  Cpu0Cst 00003001 INTL 20100121)
Jun 27 15:49:01 (none) user.warn kernel: [    0.440150] ACPI: Dynamic OEM Table Load:
Jun 27 15:49:01 (none) user.warn kernel: [    0.440307] ACPI: SSDT   (null) 0067C (v01  PmRef  Cpu0Cst 00003001 INTL 20100121)
Jun 27 15:49:01 (none) user.warn kernel: [    0.443018] ACPI: SSDT 9ae71a98 00303 (v01  PmRef    ApIst 00003000 INTL 20100121)
Jun 27 15:49:01 (none) user.warn kernel: [    0.443582] ACPI: Dynamic OEM Table Load:
Jun 27 15:49:01 (none) user.warn kernel: [    0.443740] ACPI: SSDT   (null) 00303 (v01  PmRef    ApIst 00003000 INTL 20100121)
Jun 27 15:49:01 (none) user.warn kernel: [    0.446881] ACPI: SSDT 9ae6fd98 00119 (v01  PmRef    ApCst 00003000 INTL 20100121)
Jun 27 15:49:01 (none) user.warn kernel: [    0.447405] ACPI: Dynamic OEM Table Load:
Jun 27 15:49:01 (none) user.warn kernel: [    0.447560] ACPI: SSDT   (null) 00119 (v01  PmRef    ApCst 00003000 INTL 20100121)
Jun 27 15:49:01 (none) user.info kernel: [    0.854281] ACPI: Interpreter enabled
Jun 27 15:49:01 (none) user.info kernel: [    0.854358] ACPI: (supports S0 S3 S4 S5)
Jun 27 15:49:01 (none) user.info kernel: [    0.854613] ACPI: Using IOAPIC for interrupt routing
Jun 27 15:49:01 (none) user.info kernel: [    0.860681] ACPI: EC: GPE = 0x17, I/O: command/status = 0x66, data = 0x62
Jun 27 15:49:01 (none) user.info kernel: [    0.860918] ACPI: No dock devices found.
Jun 27 15:49:01 (none) user.info kernel: [    0.860993] HEST: Table not found.
Jun 27 15:49:01 (none) user.info kernel: [    0.861068] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
Jun 27 15:49:01 (none) user.debug kernel: [    0.861477] \_SB_.PCI0:_OSC invalid UUID
Jun 27 15:49:01 (none) user.debug kernel: [    0.861551] _OSC request data:1 8 1f 
Jun 27 15:49:01 (none) user.info kernel: [    0.861788] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-fe])
Jun 27 15:49:01 (none) user.info kernel: [    0.862396] pci_root PNP0A08:00: host bridge window [io  0x0000-0x0cf7]
Jun 27 15:49:01 (none) user.info kernel: [    0.862476] pci_root PNP0A08:00: host bridge window [io  0x0d00-0xffff]
Jun 27 15:49:01 (none) user.info kernel: [    0.862555] pci_root PNP0A08:00: host bridge window [mem 0x000a0000-0x000bffff]
Jun 27 15:49:01 (none) user.info kernel: [    0.862662] pci_root PNP0A08:00: host bridge window [mem 0x9fa00000-0xfeafffff]
Jun 27 15:49:01 (none) user.debug kernel: [    0.862776] pci 0000:00:00.0: [8086:0104] type 0 class 0x000600
Jun 27 15:49:01 (none) user.debug kernel: [    0.862885] pci 0000:00:01.0: [8086:0101] type 1 class 0x000604
Jun 27 15:49:01 (none) user.debug kernel: [    0.862984] pci 0000:00:01.0: PME# supported from D0 D3hot D3cold
Jun 27 15:49:01 (none) user.debug kernel: [    0.863062] pci 0000:00:01.0: PME# disabled
Jun 27 15:49:01 (none) user.debug kernel: [    0.863160] pci 0000:00:02.0: [8086:0126] type 0 class 0x000300
Jun 27 15:49:01 (none) user.debug kernel: [    0.863246] pci 0000:00:02.0: reg 10: [mem 0xc0000000-0xc03fffff 64bit]
Jun 27 15:49:01 (none) user.debug kernel: [    0.863329] pci 0000:00:02.0: reg 18: [mem 0xb0000000-0xbfffffff 64bit pref]
Jun 27 15:49:01 (none) user.debug kernel: [    0.863410] pci 0000:00:02.0: reg 20: [io  0x8000-0x803f]
Jun 27 15:49:01 (none) user.debug kernel: [    0.863553] pci 0000:00:16.0: [8086:1c3a] type 0 class 0x000780
Jun 27 15:49:01 (none) user.debug kernel: [    0.863664] pci 0000:00:16.0: reg 10: [mem 0xc9404000-0xc940400f 64bit]
Jun 27 15:49:01 (none) user.debug kernel: [    0.863833] pci 0000:00:16.0: PME# supported from D0 D3hot D3cold
Jun 27 15:49:01 (none) user.debug kernel: [    0.863913] pci 0000:00:16.0: PME# disabled
Jun 27 15:49:01 (none) user.debug kernel: [    0.864034] pci 0000:00:1a.0: [8086:1c2d] type 0 class 0x000c03
Jun 27 15:49:01 (none) user.debug kernel: [    0.864558] pci 0000:00:1a.0: reg 10: [mem 0xc940a000-0xc940a3ff]
Jun 27 15:49:01 (none) user.debug kernel: [    0.867190] pci 0000:00:1a.0: PME# supported from D0 D3hot D3cold
Jun 27 15:49:01 (none) user.debug kernel: [    0.867271] pci 0000:00:1a.0: PME# disabled
Jun 27 15:49:01 (none) user.debug kernel: [    0.867379] pci 0000:00:1b.0: [8086:1c20] type 0 class 0x000403
Jun 27 15:49:01 (none) user.debug kernel: [    0.867481] pci 0000:00:1b.0: reg 10: [mem 0xc9400000-0xc9403fff 64bit]
Jun 27 15:49:01 (none) user.debug kernel: [    0.867654] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
Jun 27 15:49:01 (none) user.debug kernel: [    0.867735] pci 0000:00:1b.0: PME# disabled
Jun 27 15:49:01 (none) user.debug kernel: [    0.867838] pci 0000:00:1c.0: [8086:1c10] type 1 class 0x000604
Jun 27 15:49:01 (none) user.debug kernel: [    0.868015] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
Jun 27 15:49:01 (none) user.debug kernel: [    0.868098] pci 0000:00:1c.0: PME# disabled
Jun 27 15:49:01 (none) user.debug kernel: [    0.868204] pci 0000:00:1c.1: [8086:1c12] type 1 class 0x000604
Jun 27 15:49:01 (none) user.debug kernel: [    0.868380] pci 0000:00:1c.1: PME# supported from D0 D3hot D3cold
Jun 27 15:49:01 (none) user.debug kernel: [    0.868461] pci 0000:00:1c.1: PME# disabled
Jun 27 15:49:01 (none) user.debug kernel: [    0.868567] pci 0000:00:1c.2: [8086:1c14] type 1 class 0x000604
Jun 27 15:49:01 (none) user.debug kernel: [    0.868742] pci 0000:00:1c.2: PME# supported from D0 D3hot D3cold
Jun 27 15:49:01 (none) user.debug kernel: [    0.868824] pci 0000:00:1c.2: PME# disabled
Jun 27 15:49:01 (none) user.debug kernel: [    0.868931] pci 0000:00:1c.3: [8086:1c16] type 1 class 0x000604
Jun 27 15:49:01 (none) user.debug kernel: [    0.869108] pci 0000:00:1c.3: PME# supported from D0 D3hot D3cold
Jun 27 15:49:01 (none) user.debug kernel: [    0.869189] pci 0000:00:1c.3: PME# disabled
Jun 27 15:49:01 (none) user.debug kernel: [    0.869309] pci 0000:00:1d.0: [8086:1c26] type 0 class 0x000c03
Jun 27 15:49:01 (none) user.debug kernel: [    0.869829] pci 0000:00:1d.0: reg 10: [mem 0xc9409000-0xc94093ff]
Jun 27 15:49:01 (none) user.debug kernel: [    0.872471] pci 0000:00:1d.0: PME# supported from D0 D3hot D3cold
Jun 27 15:49:01 (none) user.debug kernel: [    0.872552] pci 0000:00:1d.0: PME# disabled
Jun 27 15:49:01 (none) user.debug kernel: [    0.872658] pci 0000:00:1f.0: [8086:1c4b] type 0 class 0x000601
Jun 27 15:49:01 (none) user.debug kernel: [    0.872895] pci 0000:00:1f.2: [8086:282a] type 0 class 0x000104
Jun 27 15:49:01 (none) user.debug kernel: [    0.873004] pci 0000:00:1f.2: reg 10: [io  0x8088-0x808f]
Jun 27 15:49:01 (none) user.debug kernel: [    0.873093] pci 0000:00:1f.2: reg 14: [io  0x809c-0x809f]
Jun 27 15:49:01 (none) user.debug kernel: [    0.873182] pci 0000:00:1f.2: reg 18: [io  0x8080-0x8087]
Jun 27 15:49:01 (none) user.debug kernel: [    0.873271] pci 0000:00:1f.2: reg 1c: [io  0x8098-0x809b]
Jun 27 15:49:01 (none) user.debug kernel: [    0.873359] pci 0000:00:1f.2: reg 20: [io  0x8060-0x807f]
Jun 27 15:49:01 (none) user.debug kernel: [    0.873448] pci 0000:00:1f.2: reg 24: [mem 0xc9408000-0xc94087ff]
Jun 27 15:49:01 (none) user.debug kernel: [    0.873585] pci 0000:00:1f.2: PME# supported from D3hot
Jun 27 15:49:01 (none) user.debug kernel: [    0.873665] pci 0000:00:1f.2: PME# disabled
Jun 27 15:49:01 (none) user.debug kernel: [    0.873763] pci 0000:00:1f.3: [8086:1c22] type 0 class 0x000c05
Jun 27 15:49:01 (none) user.debug kernel: [    0.873865] pci 0000:00:1f.3: reg 10: [mem 0xc9406000-0xc94060ff 64bit]
Jun 27 15:49:01 (none) user.debug kernel: [    0.873979] pci 0000:00:1f.3: reg 20: [io  0x8040-0x805f]
Jun 27 15:49:01 (none) user.debug kernel: [    0.874127] pci 0000:01:00.0: [1002:6741] type 0 class 0x000300
Jun 27 15:49:01 (none) user.debug kernel: [    0.874220] pci 0000:01:00.0: reg 10: [mem 0xa0000000-0xafffffff 64bit pref]
Jun 27 15:49:01 (none) user.debug kernel: [    0.874310] pci 0000:01:00.0: reg 18: [mem 0xc8400000-0xc841ffff 64bit]
Jun 27 15:49:01 (none) user.debug kernel: [    0.874396] pci 0000:01:00.0: reg 20: [io  0x7000-0x70ff]
Jun 27 15:49:01 (none) user.debug kernel: [    0.874487] pci 0000:01:00.0: reg 30: [mem 0xfffe0000-0xffffffff pref]
Jun 27 15:49:01 (none) user.debug kernel: [    0.874585] pci 0000:01:00.0: supports D1 D2
Jun 27 15:49:01 (none) user.info kernel: [    0.876090] pci 0000:00:01.0: PCI bridge to [bus 01-01]
Jun 27 15:49:01 (none) user.debug kernel: [    0.876201] pci 0000:00:01.0:   bridge window [io  0x7000-0x7fff]
Jun 27 15:49:01 (none) user.debug kernel: [    0.876294] pci 0000:00:01.0:   bridge window [mem 0xc8400000-0xc93fffff]
Jun 27 15:49:01 (none) user.debug kernel: [    0.876375] pci 0000:00:01.0:   bridge window [mem 0xa0000000-0xafffffff 64bit pref]
Jun 27 15:49:01 (none) user.debug kernel: [    0.876588] pci 0000:02:00.0: [8086:0083] type 0 class 0x000280
Jun 27 15:49:01 (none) user.debug kernel: [    0.876716] pci 0000:02:00.0: reg 10: [mem 0xc7400000-0xc7401fff 64bit]
Jun 27 15:49:01 (none) user.debug kernel: [    0.876991] pci 0000:02:00.0: PME# supported from D0 D3hot D3cold
Jun 27 15:49:01 (none) user.debug kernel: [    0.877078] pci 0000:02:00.0: PME# disabled
Jun 27 15:49:01 (none) user.info kernel: [    0.879098] pci 0000:00:1c.0: PCI bridge to [bus 02-02]
Jun 27 15:49:01 (none) user.debug kernel: [    0.879209] pci 0000:00:1c.0:   bridge window [io  0x6000-0x6fff]
Jun 27 15:49:01 (none) user.debug kernel: [    0.879302] pci 0000:00:1c.0:   bridge window [mem 0xc7400000-0xc83fffff]
Jun 27 15:49:01 (none) user.debug kernel: [    0.879388] pci 0000:00:1c.0:   bridge window [mem 0xc0400000-0xc13fffff 64bit pref]
Jun 27 15:49:01 (none) user.debug kernel: [    0.879590] pci 0000:03:00.0: [10ec:5209] type 0 class 0x00ff00
Jun 27 15:49:01 (none) user.debug kernel: [    0.879691] pci 0000:03:00.0: reg 10: [mem 0xc6400000-0xc6400fff]
Jun 27 15:49:01 (none) user.debug kernel: [    0.879920] pci 0000:03:00.0: supports D1 D2
Jun 27 15:49:01 (none) user.debug kernel: [    0.879995] pci 0000:03:00.0: PME# supported from D1 D2 D3hot
Jun 27 15:49:01 (none) user.debug kernel: [    0.880079] pci 0000:03:00.0: PME# disabled
Jun 27 15:49:01 (none) user.info kernel: [    0.882088] pci 0000:00:1c.1: PCI bridge to [bus 03-03]
Jun 27 15:49:01 (none) user.debug kernel: [    0.882200] pci 0000:00:1c.1:   bridge window [io  0x5000-0x5fff]
Jun 27 15:49:01 (none) user.debug kernel: [    0.882294] pci 0000:00:1c.1:   bridge window [mem 0xc6400000-0xc73fffff]
Jun 27 15:49:01 (none) user.debug kernel: [    0.882379] pci 0000:00:1c.1:   bridge window [mem 0xc1400000-0xc23fffff 64bit pref]
Jun 27 15:49:01 (none) user.debug kernel: [    0.883121] pci 0000:04:00.0: [1033:0194] type 0 class 0x000c03
Jun 27 15:49:01 (none) user.debug kernel: [    0.883230] pci 0000:04:00.0: reg 10: [mem 0xc5400000-0xc5401fff 64bit]
Jun 27 15:49:01 (none) user.debug kernel: [    0.883445] pci 0000:04:00.0: PME# supported from D0 D3hot D3cold
Jun 27 15:49:01 (none) user.debug kernel: [    0.883527] pci 0000:04:00.0: PME# disabled
Jun 27 15:49:01 (none) user.info kernel: [    0.885083] pci 0000:00:1c.2: PCI bridge to [bus 04-04]
Jun 27 15:49:01 (none) user.debug kernel: [    0.885194] pci 0000:00:1c.2:   bridge window [io  0x4000-0x4fff]
Jun 27 15:49:01 (none) user.debug kernel: [    0.885288] pci 0000:00:1c.2:   bridge window [mem 0xc5400000-0xc63fffff]
Jun 27 15:49:01 (none) user.debug kernel: [    0.885373] pci 0000:00:1c.2:   bridge window [mem 0xc2400000-0xc33fffff 64bit pref]
Jun 27 15:49:01 (none) user.debug kernel: [    0.885626] pci 0000:05:00.0: [10ec:8168] type 0 class 0x000200
Jun 27 15:49:01 (none) user.debug kernel: [    0.885774] pci 0000:05:00.0: reg 10: [io  0x3000-0x30ff]
Jun 27 15:49:01 (none) user.debug kernel: [    0.885978] pci 0000:05:00.0: reg 18: [mem 0xc3404000-0xc3404fff 64bit pref]
Jun 27 15:49:01 (none) user.debug kernel: [    0.886138] pci 0000:05:00.0: reg 20: [mem 0xc3400000-0xc3403fff 64bit pref]
Jun 27 15:49:01 (none) user.debug kernel: [    0.886444] pci 0000:05:00.0: supports D1 D2
Jun 27 15:49:01 (none) user.debug kernel: [    0.886519] pci 0000:05:00.0: PME# supported from D0 D1 D2 D3hot D3cold
Jun 27 15:49:01 (none) user.debug kernel: [    0.886611] pci 0000:05:00.0: PME# disabled
Jun 27 15:49:01 (none) user.info kernel: [    0.888103] pci 0000:00:1c.3: PCI bridge to [bus 05-05]
Jun 27 15:49:01 (none) user.debug kernel: [    0.888220] pci 0000:00:1c.3:   bridge window [io  0x3000-0x3fff]
Jun 27 15:49:01 (none) user.debug kernel: [    0.888301] pci 0000:00:1c.3:   bridge window [mem 0xc4400000-0xc53fffff]
Jun 27 15:49:01 (none) user.debug kernel: [    0.888387] pci 0000:00:1c.3:   bridge window [mem 0xc3400000-0xc43fffff 64bit pref]
Jun 27 15:49:01 (none) user.debug kernel: [    0.888525] pci_bus 0000:00: on NUMA node 0
Jun 27 15:49:01 (none) user.debug kernel: [    0.888600] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
Jun 27 15:49:01 (none) user.debug kernel: [    0.888761] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP01._PRT]
Jun 27 15:49:01 (none) user.debug kernel: [    0.888872] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP02._PRT]
Jun 27 15:49:01 (none) user.debug kernel: [    0.888981] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP03._PRT]
Jun 27 15:49:01 (none) user.debug kernel: [    0.889093] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP04._PRT]
Jun 27 15:49:01 (none) user.debug kernel: [    0.889209] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEG0._PRT]
Jun 27 15:49:01 (none) user.debug kernel: [    0.889355] \_SB_.PCI0:_OSC invalid UUID
Jun 27 15:49:01 (none) user.debug kernel: [    0.889430] _OSC request data:1 1f 1f 
Jun 27 15:49:01 (none) user.info kernel: [    0.889667]  pci0000:00: Requesting ACPI _OSC control (0x1d)
Jun 27 15:49:01 (none) user.debug kernel: [    0.889772] \_SB_.PCI0:_OSC invalid UUID
Jun 27 15:49:01 (none) user.debug kernel: [    0.889846] _OSC request data:1 0 1d 
Jun 27 15:49:01 (none) user.info kernel: [    0.892803] ACPI: PCI Interrupt Link [LNKA] (IRQs 1 3 4 5 6 10 11 12 14 15) *7
Jun 27 15:49:01 (none) user.info kernel: [    0.893483] ACPI: PCI Interrupt Link [LNKB] (IRQs 1 3 4 5 6 10 *11 12 14 15)
Jun 27 15:49:01 (none) user.info kernel: [    0.894091] ACPI: PCI Interrupt Link [LNKC] (IRQs 1 3 4 5 6 10 *11 12 14 15)
Jun 27 15:49:01 (none) user.info kernel: [    0.894696] ACPI: PCI Interrupt Link [LNKD] (IRQs 1 3 4 5 6 *10 11 12 14 15)
Jun 27 15:49:01 (none) user.info kernel: [    0.895304] ACPI: PCI Interrupt Link [LNKE] (IRQs 1 3 4 5 6 10 11 12 14 15) *7
Jun 27 15:49:01 (none) user.info kernel: [    0.895976] ACPI: PCI Interrupt Link [LNKF] (IRQs 1 3 4 5 6 10 11 12 14 15) *0, disabled.
Jun 27 15:49:01 (none) user.info kernel: [    0.896694] ACPI: PCI Interrupt Link [LNKG] (IRQs 1 3 4 5 6 *10 11 12 14 15)
Jun 27 15:49:01 (none) user.info kernel: [    0.897303] ACPI: PCI Interrupt Link [LNKH] (IRQs 1 3 4 5 6 *10 11 12 14 15)
Jun 27 15:49:01 (none) user.info kernel: [    0.897977] vgaarb: device added: PCI:0000:00:02.0,decodes=io+mem,owns=io+mem,locks=none
Jun 27 15:49:01 (none) user.info kernel: [    0.898093] vgaarb: device added: PCI:0000:01:00.0,decodes=io+mem,owns=none,locks=none
Jun 27 15:49:01 (none) user.info kernel: [    0.898203] vgaarb: loaded
Jun 27 15:49:01 (none) user.notice kernel: [    0.898386] SCSI subsystem initialized
Jun 27 15:49:01 (none) user.debug kernel: [    0.898522] libata version 3.00 loaded.
Jun 27 15:49:01 (none) user.info kernel: [    0.898640] usbcore: registered new interface driver usbfs
Jun 27 15:49:01 (none) user.info kernel: [    0.898754] usbcore: registered new interface driver hub
Jun 27 15:49:01 (none) user.info kernel: [    0.898855] usbcore: registered new device driver usb
Jun 27 15:49:01 (none) user.info kernel: [    0.898997] PCI: Using ACPI for IRQ routing
Jun 27 15:49:01 (none) user.debug kernel: [    0.899074] PCI: pci_cache_line_size set to 64 bytes
Jun 27 15:49:01 (none) user.debug kernel: [    0.899243] reserve RAM buffer: 0000000000094400 - 000000000009ffff 
Jun 27 15:49:01 (none) user.debug kernel: [    0.899296] reserve RAM buffer: 000000009ae3f000 - 000000009bffffff 
Jun 27 15:49:01 (none) user.debug kernel: [    0.899416] reserve RAM buffer: 000000009b000000 - 000000009bffffff 
Jun 27 15:49:01 (none) user.info kernel: [    0.899669] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0, 0, 0, 0, 0
Jun 27 15:49:01 (none) user.info kernel: [    0.900185] hpet0: 8 comparators, 64-bit 14.318180 MHz counter
Jun 27 15:49:01 (none) user.info kernel: [    0.903279] Switching to clocksource hpet
Jun 27 15:49:01 (none) user.info kernel: [    0.904035] Switched to NOHz mode on CPU #0
Jun 27 15:49:01 (none) user.info kernel: [    0.904100] Switched to NOHz mode on CPU #1
Jun 27 15:49:01 (none) user.info kernel: [    0.904101] Switched to NOHz mode on CPU #3
Jun 27 15:49:01 (none) user.info kernel: [    0.904145] Switched to NOHz mode on CPU #2
Jun 27 15:49:01 (none) user.info kernel: [    0.904622] pnp: PnP ACPI init
Jun 27 15:49:01 (none) user.info kernel: [    0.904703] ACPI: bus type pnp registered
Jun 27 15:49:01 (none) user.debug kernel: [    0.905041] pnp 00:00: [bus 00-fe]
Jun 27 15:49:01 (none) user.debug kernel: [    0.905115] pnp 00:00: [io  0x0000-0x0cf7 window]
Jun 27 15:49:01 (none) user.debug kernel: [    0.905191] pnp 00:00: [io  0x0cf8-0x0cff]
Jun 27 15:49:01 (none) user.debug kernel: [    0.905266] pnp 00:00: [io  0x0d00-0xffff window]
Jun 27 15:49:01 (none) user.debug kernel: [    0.905342] pnp 00:00: [mem 0x000a0000-0x000bffff window]
Jun 27 15:49:01 (none) user.debug kernel: [    0.905418] pnp 00:00: [mem 0x000c0000-0x000c3fff window]
Jun 27 15:49:01 (none) user.debug kernel: [    0.905515] pnp 00:00: [mem 0x000c4000-0x000c7fff window]
Jun 27 15:49:01 (none) user.debug kernel: [    0.905592] pnp 00:00: [mem 0x000c8000-0x000cbfff window]
Jun 27 15:49:01 (none) user.debug kernel: [    0.905669] pnp 00:00: [mem 0x000cc000-0x000cffff window]
Jun 27 15:49:01 (none) user.debug kernel: [    0.905746] pnp 00:00: [mem 0x000d0000-0x000d3fff window]
Jun 27 15:49:01 (none) user.debug kernel: [    0.905822] pnp 00:00: [mem 0x000d4000-0x000d7fff window]
Jun 27 15:49:01 (none) user.debug kernel: [    0.905900] pnp 00:00: [mem 0x000d8000-0x000dbfff window]
Jun 27 15:49:01 (none) user.debug kernel: [    0.905977] pnp 00:00: [mem 0x000dc000-0x000dffff window]
Jun 27 15:49:01 (none) user.debug kernel: [    0.906053] pnp 00:00: [mem 0x000e0000-0x000e3fff window]
Jun 27 15:49:01 (none) user.debug kernel: [    0.906130] pnp 00:00: [mem 0x000e4000-0x000e7fff window]
Jun 27 15:49:01 (none) user.debug kernel: [    0.906207] pnp 00:00: [mem 0x000e8000-0x000ebfff window]
Jun 27 15:49:01 (none) user.debug kernel: [    0.906284] pnp 00:00: [mem 0x000ec000-0x000effff window]
Jun 27 15:49:01 (none) user.debug kernel: [    0.906362] pnp 00:00: [mem 0x000f0000-0x000fffff window]
Jun 27 15:49:01 (none) user.debug kernel: [    0.906439] pnp 00:00: [mem 0x9fa00000-0xfeafffff window]
Jun 27 15:49:01 (none) user.debug kernel: [    0.906595] pnp 00:00: Plug and Play ACPI device, IDs PNP0a08 PNP0a03 (active)
Jun 27 15:49:01 (none) user.debug kernel: [    0.906760] pnp 00:01: [io  0x0000-0x001f]
Jun 27 15:49:01 (none) user.debug kernel: [    0.906835] pnp 00:01: [io  0x0081-0x0091]
Jun 27 15:49:01 (none) user.debug kernel: [    0.906910] pnp 00:01: [io  0x0093-0x009f]
Jun 27 15:49:01 (none) user.debug kernel: [    0.906985] pnp 00:01: [io  0x00c0-0x00df]
Jun 27 15:49:01 (none) user.debug kernel: [    0.907060] pnp 00:01: [dma 4]
Jun 27 15:49:01 (none) user.debug kernel: [    0.907174] pnp 00:01: Plug and Play ACPI device, IDs PNP0200 (active)
Jun 27 15:49:01 (none) user.debug kernel: [    0.907259] pnp 00:02: [mem 0xff000000-0xffffffff]
Jun 27 15:49:01 (none) user.debug kernel: [    0.907374] pnp 00:02: Plug and Play ACPI device, IDs INT0800 (active)
Jun 27 15:49:01 (none) user.debug kernel: [    0.907525] pnp 00:03: [mem 0xfed00000-0xfed003ff]
Jun 27 15:49:01 (none) user.debug kernel: [    0.907648] pnp 00:03: Plug and Play ACPI device, IDs PNP0103 (active)
Jun 27 15:49:01 (none) user.debug kernel: [    0.907734] pnp 00:04: [io  0x00f0]
Jun 27 15:49:01 (none) user.debug kernel: [    0.907813] pnp 00:04: [irq 13]
Jun 27 15:49:01 (none) user.debug kernel: [    0.907927] pnp 00:04: Plug and Play ACPI device, IDs PNP0c04 (active)
Jun 27 15:49:01 (none) user.debug kernel: [    0.908015] pnp 00:05: [io  0x002e-0x002f]
Jun 27 15:49:01 (none) user.debug kernel: [    0.908090] pnp 00:05: [io  0x004e-0x004f]
Jun 27 15:49:01 (none) user.debug kernel: [    0.908164] pnp 00:05: [io  0x0061]
Jun 27 15:49:01 (none) user.debug kernel: [    0.908238] pnp 00:05: [io  0x0063]
Jun 27 15:49:01 (none) user.debug kernel: [    0.908311] pnp 00:05: [io  0x0065]
Jun 27 15:49:01 (none) user.debug kernel: [    0.908384] pnp 00:05: [io  0x0067]
Jun 27 15:49:01 (none) user.debug kernel: [    0.908468] pnp 00:05: [io  0x0070]
Jun 27 15:49:01 (none) user.debug kernel: [    0.908541] pnp 00:05: [io  0x0080]
Jun 27 15:49:01 (none) user.debug kernel: [    0.908615] pnp 00:05: [io  0x0092]
Jun 27 15:49:01 (none) user.debug kernel: [    0.908689] pnp 00:05: [io  0x00b2-0x00b3]
Jun 27 15:49:01 (none) user.debug kernel: [    0.908764] pnp 00:05: [io  0x0680-0x069f]
Jun 27 15:49:01 (none) user.debug kernel: [    0.908839] pnp 00:05: [io  0x1000-0x100f]
Jun 27 15:49:01 (none) user.debug kernel: [    0.908915] pnp 00:05: [io  0xffff]
Jun 27 15:49:01 (none) user.debug kernel: [    0.908989] pnp 00:05: [io  0xffff]
Jun 27 15:49:01 (none) user.debug kernel: [    0.909062] pnp 00:05: [io  0x0400-0x0453]
Jun 27 15:49:01 (none) user.debug kernel: [    0.909137] pnp 00:05: [io  0x0458-0x047f]
Jun 27 15:49:01 (none) user.debug kernel: [    0.909211] pnp 00:05: [io  0x0500-0x057f]
Jun 27 15:49:01 (none) user.debug kernel: [    0.909285] pnp 00:05: [io  0x164e-0x164f]
Jun 27 15:49:01 (none) user.debug kernel: [    0.909360] pnp 00:05: [io  0x2000]
Jun 27 15:49:01 (none) user.debug kernel: [    0.909434] pnp 00:05: [io  0x2004]
Jun 27 15:49:01 (none) user.info kernel: [    0.909584] system 00:05: [io  0x0680-0x069f] has been reserved
Jun 27 15:49:01 (none) user.info kernel: [    0.909663] system 00:05: [io  0x1000-0x100f] has been reserved
Jun 27 15:49:01 (none) user.info kernel: [    0.909741] system 00:05: [io  0xffff] has been reserved
Jun 27 15:49:01 (none) user.info kernel: [    0.909818] system 00:05: [io  0xffff] has been reserved
Jun 27 15:49:01 (none) user.info kernel: [    0.909895] system 00:05: [io  0x0400-0x0453] has been reserved
Jun 27 15:49:01 (none) user.info kernel: [    0.909973] system 00:05: [io  0x0458-0x047f] has been reserved
Jun 27 15:49:01 (none) user.info kernel: [    0.910052] system 00:05: [io  0x0500-0x057f] has been reserved
Jun 27 15:49:01 (none) user.info kernel: [    0.910130] system 00:05: [io  0x164e-0x164f] has been reserved
Jun 27 15:49:01 (none) user.info kernel: [    0.910207] system 00:05: [io  0x2000] has been reserved
Jun 27 15:49:01 (none) user.info kernel: [    0.910284] system 00:05: [io  0x2004] has been reserved
Jun 27 15:49:01 (none) user.debug kernel: [    0.910362] system 00:05: Plug and Play ACPI device, IDs PNP0c02 (active)
Jun 27 15:49:01 (none) user.debug kernel: [    0.910447] pnp 00:06: [io  0x0070-0x0077]
Jun 27 15:49:01 (none) user.debug kernel: [    0.910538] pnp 00:06: [irq 8]
Jun 27 15:49:01 (none) user.debug kernel: [    0.910654] pnp 00:06: Plug and Play ACPI device, IDs PNP0b00 (active)
Jun 27 15:49:01 (none) user.debug kernel: [    0.910749] pnp 00:07: [io  0x0454-0x0457]
Jun 27 15:49:01 (none) user.info kernel: [    0.910878] system 00:07: [io  0x0454-0x0457] has been reserved
Jun 27 15:49:01 (none) user.debug kernel: [    0.910957] system 00:07: Plug and Play ACPI device, IDs INT3f0d PNP0c02 (active)
Jun 27 15:49:01 (none) user.debug kernel: [    0.911075] pnp 00:08: [io  0x0060]
Jun 27 15:49:01 (none) user.debug kernel: [    0.911148] pnp 00:08: [io  0x0064]
Jun 27 15:49:01 (none) user.debug kernel: [    0.911225] pnp 00:08: [irq 1]
Jun 27 15:49:01 (none) user.debug kernel: [    0.911341] pnp 00:08: Plug and Play ACPI device, IDs PNP0303 (active)
Jun 27 15:49:01 (none) user.debug kernel: [    0.911433] pnp 00:09: [irq 12]
Jun 27 15:49:01 (none) user.debug kernel: [    0.911569] pnp 00:09: Plug and Play ACPI device, IDs SNY9014 PNP0f13 (active)
Jun 27 15:49:01 (none) user.debug kernel: [    0.911695] pnp 00:0a: [mem 0xfed40000-0xfed44fff]
Jun 27 15:49:01 (none) user.debug kernel: [    0.911815] pnp 00:0a: Plug and Play ACPI device, IDs IFX0102 PNP0c31 (active)
Jun 27 15:49:01 (none) user.debug kernel: [    0.912012] pnp 00:0b: [mem 0xfed1c000-0xfed1ffff]
Jun 27 15:49:01 (none) user.debug kernel: [    0.912088] pnp 00:0b: [mem 0xfed10000-0xfed17fff]
Jun 27 15:49:01 (none) user.debug kernel: [    0.912163] pnp 00:0b: [mem 0xfed18000-0xfed18fff]
Jun 27 15:49:01 (none) user.debug kernel: [    0.912239] pnp 00:0b: [mem 0xfed19000-0xfed19fff]
Jun 27 15:49:01 (none) user.debug kernel: [    0.912315] pnp 00:0b: [mem 0xe0000000-0xefffffff]
Jun 27 15:49:01 (none) user.debug kernel: [    0.912390] pnp 00:0b: [mem 0xfed20000-0xfed3ffff]
Jun 27 15:49:01 (none) user.debug kernel: [    0.912477] pnp 00:0b: [mem 0xfed90000-0xfed93fff]
Jun 27 15:49:01 (none) user.debug kernel: [    0.912552] pnp 00:0b: [mem 0xff000000-0xffffffff]
Jun 27 15:49:01 (none) user.debug kernel: [    0.912628] pnp 00:0b: [mem 0xfee00000-0xfeefffff]
Jun 27 15:49:01 (none) user.debug kernel: [    0.912704] pnp 00:0b: [mem 0x9fa00000-0x9fa00fff]
Jun 27 15:49:01 (none) user.info kernel: [    0.912844] system 00:0b: [mem 0xfed1c000-0xfed1ffff] has been reserved
Jun 27 15:49:01 (none) user.info kernel: [    0.912924] system 00:0b: [mem 0xfed10000-0xfed17fff] has been reserved
Jun 27 15:49:01 (none) user.info kernel: [    0.913003] system 00:0b: [mem 0xfed18000-0xfed18fff] has been reserved
Jun 27 15:49:01 (none) user.info kernel: [    0.913083] system 00:0b: [mem 0xfed19000-0xfed19fff] has been reserved
Jun 27 15:49:01 (none) user.info kernel: [    0.913162] system 00:0b: [mem 0xe0000000-0xefffffff] has been reserved
Jun 27 15:49:01 (none) user.info kernel: [    0.913241] system 00:0b: [mem 0xfed20000-0xfed3ffff] has been reserved
Jun 27 15:49:01 (none) user.info kernel: [    0.913320] system 00:0b: [mem 0xfed90000-0xfed93fff] has been reserved
Jun 27 15:49:01 (none) user.info kernel: [    0.913400] system 00:0b: [mem 0xff000000-0xffffffff] could not be reserved
Jun 27 15:49:01 (none) user.info kernel: [    0.913499] system 00:0b: [mem 0xfee00000-0xfeefffff] could not be reserved
Jun 27 15:49:01 (none) user.info kernel: [    0.913578] system 00:0b: [mem 0x9fa00000-0x9fa00fff] has been reserved
Jun 27 15:49:01 (none) user.debug kernel: [    0.913658] system 00:0b: Plug and Play ACPI device, IDs PNP0c02 (active)
Jun 27 15:49:01 (none) user.debug kernel: [    0.913979] pnp 00:0c: [mem 0x20000000-0x201fffff]
Jun 27 15:49:01 (none) user.debug kernel: [    0.914055] pnp 00:0c: [mem 0x40000000-0x401fffff]
Jun 27 15:49:01 (none) user.info kernel: [    0.914206] system 00:0c: [mem 0x20000000-0x201fffff] could not be reserved
Jun 27 15:49:01 (none) user.info kernel: [    0.914285] system 00:0c: [mem 0x40000000-0x401fffff] could not be reserved
Jun 27 15:49:01 (none) user.debug kernel: [    0.914365] system 00:0c: Plug and Play ACPI device, IDs PNP0c01 (active)
Jun 27 15:49:01 (none) user.info kernel: [    0.914470] pnp: PnP ACPI: found 13 devices
Jun 27 15:49:01 (none) user.info kernel: [    0.914545] ACPI: ACPI bus type pnp unregistered
Jun 27 15:49:01 (none) user.info kernel: [    0.952175] pci 0000:01:00.0: no compatible bridge window for [mem 0xfffe0000-0xffffffff pref]
Jun 27 15:49:01 (none) user.info kernel: [    0.952892] pci 0000:01:00.0: BAR 6: assigned [mem 0xc8420000-0xc843ffff pref]
Jun 27 15:49:01 (none) user.info kernel: [    0.952999] pci 0000:00:01.0: PCI bridge to [bus 01-01]
Jun 27 15:49:01 (none) user.info kernel: [    0.953076] pci 0000:00:01.0:   bridge window [io  0x7000-0x7fff]
Jun 27 15:49:01 (none) user.info kernel: [    0.953154] pci 0000:00:01.0:   bridge window [mem 0xc8400000-0xc93fffff]
Jun 27 15:49:01 (none) user.info kernel: [    0.953234] pci 0000:00:01.0:   bridge window [mem 0xa0000000-0xafffffff 64bit pref]
Jun 27 15:49:01 (none) user.info kernel: [    0.953343] pci 0000:00:1c.0: PCI bridge to [bus 02-02]
Jun 27 15:49:01 (none) user.info kernel: [    0.953433] pci 0000:00:1c.0:   bridge window [io  0x6000-0x6fff]
Jun 27 15:49:01 (none) user.info kernel: [    0.953517] pci 0000:00:1c.0:   bridge window [mem 0xc7400000-0xc83fffff]
Jun 27 15:49:01 (none) user.info kernel: [    0.953599] pci 0000:00:1c.0:   bridge window [mem 0xc0400000-0xc13fffff 64bit pref]
Jun 27 15:49:01 (none) user.info kernel: [    0.953713] pci 0000:00:1c.1: PCI bridge to [bus 03-03]
Jun 27 15:49:01 (none) user.info kernel: [    0.953791] pci 0000:00:1c.1:   bridge window [io  0x5000-0x5fff]
Jun 27 15:49:01 (none) user.info kernel: [    0.953874] pci 0000:00:1c.1:   bridge window [mem 0xc6400000-0xc73fffff]
Jun 27 15:49:01 (none) user.info kernel: [    0.953956] pci 0000:00:1c.1:   bridge window [mem 0xc1400000-0xc23fffff 64bit pref]
Jun 27 15:49:01 (none) user.info kernel: [    0.954070] pci 0000:00:1c.2: PCI bridge to [bus 04-04]
Jun 27 15:49:01 (none) user.info kernel: [    0.954148] pci 0000:00:1c.2:   bridge window [io  0x4000-0x4fff]
Jun 27 15:49:01 (none) user.info kernel: [    0.954231] pci 0000:00:1c.2:   bridge window [mem 0xc5400000-0xc63fffff]
Jun 27 15:49:01 (none) user.info kernel: [    0.954313] pci 0000:00:1c.2:   bridge window [mem 0xc2400000-0xc33fffff 64bit pref]
Jun 27 15:49:01 (none) user.info kernel: [    0.954439] pci 0000:00:1c.3: PCI bridge to [bus 05-05]
Jun 27 15:49:01 (none) user.info kernel: [    0.954517] pci 0000:00:1c.3:   bridge window [io  0x3000-0x3fff]
Jun 27 15:49:01 (none) user.info kernel: [    0.954600] pci 0000:00:1c.3:   bridge window [mem 0xc4400000-0xc53fffff]
Jun 27 15:49:01 (none) user.info kernel: [    0.954723] pci 0000:00:1c.3:   bridge window [mem 0xc3400000-0xc43fffff 64bit pref]
Jun 27 15:49:01 (none) user.info kernel: [    0.954842] pci 0000:00:01.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Jun 27 15:49:01 (none) user.debug kernel: [    0.954922] pci 0000:00:01.0: setting latency timer to 64
Jun 27 15:49:01 (none) user.info kernel: [    0.955003] pci 0000:00:1c.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Jun 27 15:49:01 (none) user.debug kernel: [    0.955085] pci 0000:00:1c.0: setting latency timer to 64
Jun 27 15:49:01 (none) user.info kernel: [    0.955169] pci 0000:00:1c.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
Jun 27 15:49:01 (none) user.debug kernel: [    0.955251] pci 0000:00:1c.1: setting latency timer to 64
Jun 27 15:49:01 (none) user.info kernel: [    0.955334] pci 0000:00:1c.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
Jun 27 15:49:01 (none) user.debug kernel: [    0.955424] pci 0000:00:1c.2: setting latency timer to 64
Jun 27 15:49:01 (none) user.info kernel: [    0.955508] pci 0000:00:1c.3: PCI INT D -> GSI 19 (level, low) -> IRQ 19
Jun 27 15:49:01 (none) user.debug kernel: [    0.955590] pci 0000:00:1c.3: setting latency timer to 64
Jun 27 15:49:01 (none) user.debug kernel: [    0.955669] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
Jun 27 15:49:01 (none) user.debug kernel: [    0.955747] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff]
Jun 27 15:49:01 (none) user.debug kernel: [    0.955824] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
Jun 27 15:49:01 (none) user.debug kernel: [    0.955903] pci_bus 0000:00: resource 7 [mem 0x9fa00000-0xfeafffff]
Jun 27 15:49:01 (none) user.debug kernel: [    0.955981] pci_bus 0000:01: resource 0 [io  0x7000-0x7fff]
Jun 27 15:49:01 (none) user.debug kernel: [    0.956058] pci_bus 0000:01: resource 1 [mem 0xc8400000-0xc93fffff]
Jun 27 15:49:01 (none) user.debug kernel: [    0.956136] pci_bus 0000:01: resource 2 [mem 0xa0000000-0xafffffff 64bit pref]
Jun 27 15:49:01 (none) user.debug kernel: [    0.956242] pci_bus 0000:02: resource 0 [io  0x6000-0x6fff]
Jun 27 15:49:01 (none) user.debug kernel: [    0.956319] pci_bus 0000:02: resource 1 [mem 0xc7400000-0xc83fffff]
Jun 27 15:49:01 (none) user.debug kernel: [    0.956404] pci_bus 0000:02: resource 2 [mem 0xc0400000-0xc13fffff 64bit pref]
Jun 27 15:49:01 (none) user.debug kernel: [    0.956511] pci_bus 0000:03: resource 0 [io  0x5000-0x5fff]
Jun 27 15:49:01 (none) user.debug kernel: [    0.956588] pci_bus 0000:03: resource 1 [mem 0xc6400000-0xc73fffff]
Jun 27 15:49:01 (none) user.debug kernel: [    0.956666] pci_bus 0000:03: resource 2 [mem 0xc1400000-0xc23fffff 64bit pref]
Jun 27 15:49:01 (none) user.debug kernel: [    0.956772] pci_bus 0000:04: resource 0 [io  0x4000-0x4fff]
Jun 27 15:49:01 (none) user.debug kernel: [    0.956850] pci_bus 0000:04: resource 1 [mem 0xc5400000-0xc63fffff]
Jun 27 15:49:01 (none) user.debug kernel: [    0.956928] pci_bus 0000:04: resource 2 [mem 0xc2400000-0xc33fffff 64bit pref]
Jun 27 15:49:01 (none) user.debug kernel: [    0.957035] pci_bus 0000:05: resource 0 [io  0x3000-0x3fff]
Jun 27 15:49:01 (none) user.debug kernel: [    0.957112] pci_bus 0000:05: resource 1 [mem 0xc4400000-0xc53fffff]
Jun 27 15:49:01 (none) user.debug kernel: [    0.957191] pci_bus 0000:05: resource 2 [mem 0xc3400000-0xc43fffff 64bit pref]
Jun 27 15:49:01 (none) user.info kernel: [    0.957324] NET: Registered protocol family 2
Jun 27 15:49:01 (none) user.info kernel: [    0.957446] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
Jun 27 15:49:01 (none) user.info kernel: [    0.957582] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
Jun 27 15:49:01 (none) user.info kernel: [    0.957896] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
Jun 27 15:49:01 (none) user.info kernel: [    0.958074] TCP: Hash tables configured (established 131072 bind 65536)
Jun 27 15:49:01 (none) user.info kernel: [    0.958153] TCP reno registered
Jun 27 15:49:01 (none) user.info kernel: [    0.958228] UDP hash table entries: 512 (order: 2, 16384 bytes)
Jun 27 15:49:01 (none) user.info kernel: [    0.958309] UDP-Lite hash table entries: 512 (order: 2, 16384 bytes)
Jun 27 15:49:01 (none) user.info kernel: [    0.958507] NET: Registered protocol family 1
Jun 27 15:49:01 (none) user.info kernel: [    0.958647] RPC: Registered udp transport module.
Jun 27 15:49:01 (none) user.info kernel: [    0.958723] RPC: Registered tcp transport module.
Jun 27 15:49:01 (none) user.info kernel: [    0.958798] RPC: Registered tcp NFSv4.1 backchannel transport module.
Jun 27 15:49:01 (none) user.debug kernel: [    0.958884] pci 0000:00:02.0: Boot video device
Jun 27 15:49:01 (none) user.warn kernel: [    0.982494] pci 0000:04:00.0: xHCI HW did not halt within 2000 usec status = 0x0
Jun 27 15:49:01 (none) user.debug kernel: [    0.982611] PCI: CLS 64 bytes, default 64
Jun 27 15:49:01 (none) user.info kernel: [    0.982714] Trying to unpack rootfs image as initramfs...
Jun 27 15:49:01 (none) user.info kernel: [    1.036755] Freeing initrd memory: 29940k freed
Jun 27 15:49:01 (none) user.info kernel: [    1.040808] Simple Boot Flag at 0x44 set to 0x1
Jun 27 15:49:01 (none) user.info kernel: [    1.042022] audit: initializing netlink socket (disabled)
Jun 27 15:49:01 (none) user.notice kernel: [    1.042105] type=2000 audit(1309189740.866:1): initialized
Jun 27 15:49:01 (none) user.warn kernel: [    1.042492] highmem bounce pool size: 64 pages
Jun 27 15:49:01 (none) user.notice kernel: [    1.045155] VFS: Disk quotas dquot_6.5.2
Jun 27 15:49:01 (none) user.warn kernel: [    1.045326] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
Jun 27 15:49:01 (none) user.info kernel: [    1.045542] squashfs: version 4.0 (2009/01/31) Phillip Lougher
Jun 27 15:49:01 (none) user.info kernel: [    1.045748] ROMFS MTD (C) 2007 Red Hat, Inc.
Jun 27 15:49:01 (none) user.info kernel: [    1.046058] aufs 2.1-standalone.tree-38-rcN-20110307
Jun 27 15:49:01 (none) user.info kernel: [    1.046137] msgmni has been set to 1424
Jun 27 15:49:01 (none) user.info kernel: [    1.047193] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 254)
Jun 27 15:49:01 (none) user.info kernel: [    1.047318] io scheduler noop registered
Jun 27 15:49:01 (none) user.info kernel: [    1.047392] io scheduler deadline registered
Jun 27 15:49:01 (none) user.info kernel: [    1.047474] io scheduler cfq registered (default)
Jun 27 15:49:01 (none) user.debug kernel: [    1.047631] pcieport 0000:00:01.0: setting latency timer to 64
Jun 27 15:49:01 (none) user.debug kernel: [    1.047728] pcieport 0000:00:01.0: irq 40 for MSI/MSI-X
Jun 27 15:49:01 (none) user.info kernel: [    1.048223] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Jun 27 15:49:01 (none) user.info kernel: [    1.048370] ERST: Table is not found!
Jun 27 15:49:01 (none) user.info kernel: [    1.048453] isapnp: Scanning for PnP cards...
Jun 27 15:49:01 (none) user.info kernel: [    1.404839] isapnp: No Plug & Play device found
Jun 27 15:49:01 (none) user.info kernel: [    1.407466] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
Jun 27 15:49:01 (none) user.info kernel: [    1.473110] brd: module loaded
Jun 27 15:49:01 (none) user.info kernel: [    1.502706] loop: module loaded
Jun 27 15:49:01 (none) user.info kernel: [    1.502965] Loading iSCSI transport class v2.0-870.
Jun 27 15:49:01 (none) user.info kernel: [    1.503603] i8042: PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
Jun 27 15:49:01 (none) user.info kernel: [    1.506405] serio: i8042 KBD port at 0x60,0x64 irq 1
Jun 27 15:49:01 (none) user.info kernel: [    1.506484] serio: i8042 AUX port at 0x60,0x64 irq 12
Jun 27 15:49:01 (none) user.info kernel: [    1.506774] mousedev: PS/2 mouse device common for all mice
Jun 27 15:49:01 (none) user.info kernel: [    1.506949] EISA: Probing bus 0 at eisa.0
Jun 27 15:49:01 (none) user.warn kernel: [    1.507023] EISA: Cannot allocate resource for mainboard
Jun 27 15:49:01 (none) user.warn kernel: [    1.507100] Cannot allocate resource for EISA slot 1
Jun 27 15:49:01 (none) user.warn kernel: [    1.507176] Cannot allocate resource for EISA slot 2
Jun 27 15:49:01 (none) user.warn kernel: [    1.507252] Cannot allocate resource for EISA slot 3
Jun 27 15:49:01 (none) user.warn kernel: [    1.507327] Cannot allocate resource for EISA slot 4
Jun 27 15:49:01 (none) user.warn kernel: [    1.507403] Cannot allocate resource for EISA slot 5
Jun 27 15:49:01 (none) user.warn kernel: [    1.507478] Cannot allocate resource for EISA slot 6
Jun 27 15:49:01 (none) user.warn kernel: [    1.507554] Cannot allocate resource for EISA slot 7
Jun 27 15:49:01 (none) user.warn kernel: [    1.507629] Cannot allocate resource for EISA slot 8
Jun 27 15:49:01 (none) user.info kernel: [    1.507723] EISA: Detected 0 cards.
Jun 27 15:49:01 (none) user.info kernel: [    1.507797] cpuidle: using governor ladder
Jun 27 15:49:01 (none) user.info kernel: [    1.507870] cpuidle: using governor menu
Jun 27 15:49:01 (none) user.info kernel: [    1.507988] TCP cubic registered
Jun 27 15:49:01 (none) user.info kernel: [    1.508060] Initializing XFRM netlink socket
Jun 27 15:49:01 (none) user.info kernel: [    1.508137] NET: Registered protocol family 17
Jun 27 15:49:01 (none) user.notice kernel: [    1.508225] Registering the dns_resolver key type
Jun 27 15:49:01 (none) user.info kernel: [    1.508313] Using IPI No-Shortcut mode
Jun 27 15:49:01 (none) user.info kernel: [    1.522296] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input0
Jun 27 15:49:01 (none) user.warn kernel: [    1.526515] registered taskstats version 1
Jun 27 15:49:01 (none) user.info kernel: [    1.527103] Freeing unused kernel memory: 572k freed
Jun 27 15:49:01 (none) user.info kernel: [    1.527302] Write protecting the kernel text: 4072k
Jun 27 15:49:01 (none) user.info kernel: [    1.527397] Write protecting the kernel read-only data: 1196k
Jun 27 15:49:01 (none) daemon.err udevd[1284]: specified group 'netdev' unknown
Jun 27 15:49:01 (none) daemon.err udevd[1284]: specified group 'tty' unknown
Jun 27 15:49:01 (none) daemon.err udevd[1284]: specified group 'dialout' unknown
Jun 27 15:49:01 (none) daemon.err udevd[1284]: specified group 'kmem' unknown
Jun 27 15:49:01 (none) daemon.err udevd[1284]: specified group 'video' unknown
Jun 27 15:49:01 (none) daemon.err udevd[1284]: specified group 'audio' unknown
Jun 27 15:49:01 (none) daemon.err udevd[1284]: specified group 'lp' unknown
Jun 27 15:49:01 (none) daemon.err udevd[1284]: specified group 'disk' unknown
Jun 27 15:49:01 (none) daemon.err udevd[1284]: specified group 'floppy' unknown
Jun 27 15:49:01 (none) daemon.err udevd[1284]: specified group 'cdrom' unknown
Jun 27 15:49:01 (none) daemon.err udevd[1284]: specified group 'tape' unknown
Jun 27 15:49:01 (none) daemon.err udevd[1284]: specified group 'plugdev' unknown
Jun 27 15:49:01 (none) daemon.err udevd[1284]: BUS= will be removed in a future udev version, please use SUBSYSTEM= to match the event device, or SUBSYSTEMS= to match a parent device, in /lib/udev/rules.d/60-bluetooth.rules:2
Jun 27 15:49:01 (none) daemon.err udevd[1284]: SYSFS{}= will be removed in a future udev version, please use ATTR{}= to match the event device, or ATTRS{}= to match a parent device, in /lib/udev/rules.d/60-bluetooth.rules:2
Jun 27 15:49:01 (none) daemon.err udevd[1284]: BUS= will be removed in a future udev version, please use SUBSYSTEM= to match the event device, or SUBSYSTEMS= to match a parent device, in /lib/udev/rules.d/60-bluetooth.rules:5
Jun 27 15:49:01 (none) daemon.err udevd[1284]: SYSFS{}= will be removed in a future udev version, please use ATTR{}= to match the event device, or ATTRS{}= to match a parent device, in /lib/udev/rules.d/60-bluetooth.rules:5
Jun 27 15:49:01 (none) daemon.err udevd[1284]: BUS= will be removed in a future udev version, please use SUBSYSTEM= to match the event device, or SUBSYSTEMS= to match a parent device, in /lib/udev/rules.d/60-bluetooth.rules:8
Jun 27 15:49:01 (none) daemon.err udevd[1284]: SYSFS{}= will be removed in a future udev version, please use ATTR{}= to match the event device, or ATTRS{}= to match a parent device, in /lib/udev/rules.d/60-bluetooth.rules:8
Jun 27 15:49:01 (none) daemon.err udevd[1284]: BUS= will be removed in a future udev version, please use SUBSYSTEM= to match the event device, or SUBSYSTEMS= to match a parent device, in /lib/udev/rules.d/60-bluetooth.rules:11
Jun 27 15:49:01 (none) daemon.err udevd[1284]: SYSFS{}= will be removed in a future udev version, please use ATTR{}= to match the event device, or ATTRS{}= to match a parent device, in /lib/udev/rules.d/60-bluetooth.rules:11
Jun 27 15:49:01 (none) daemon.err udevd[1284]: BUS= will be removed in a future udev version, please use SUBSYSTEM= to match the event device, or SUBSYSTEMS= to match a parent device, in /lib/udev/rules.d/60-bluetooth.rules:14
Jun 27 15:49:01 (none) daemon.err udevd[1284]: SYSFS{}= will be removed in a future udev version, please use ATTR{}= to match the event device, or ATTRS{}= to match a parent device, in /lib/udev/rules.d/60-bluetooth.rules:14
Jun 27 15:49:01 (none) daemon.err udevd[1284]: BUS= will be removed in a future udev version, please use SUBSYSTEM= to match the event device, or SUBSYSTEMS= to match a parent device, in /lib/udev/rules.d/60-bluetooth.rules:17
Jun 27 15:49:01 (none) daemon.err udevd[1284]: SYSFS{}= will be removed in a future udev version, please use ATTR{}= to match the event device, or ATTRS{}= to match a parent device, in /lib/udev/rules.d/60-bluetooth.rules:17
Jun 27 15:49:01 (none) daemon.err udevd[1284]: BUS= will be removed in a future udev version, please use SUBSYSTEM= to match the event device, or SUBSYSTEMS= to match a parent device, in /lib/udev/rules.d/60-bluetooth.rules:20
Jun 27 15:49:01 (none) daemon.err udevd[1284]: SYSFS{}= will be removed in a future udev version, please use ATTR{}= to match the event device, or ATTRS{}= to match a parent device, in /lib/udev/rules.d/60-bluetooth.rules:20
Jun 27 15:49:01 (none) daemon.err udevd[1284]: BUS= will be removed in a future udev version, please use SUBSYSTEM= to match the event device, or SUBSYSTEMS= to match a parent device, in /lib/udev/rules.d/60-bluetooth.rules:23
Jun 27 15:49:01 (none) daemon.err udevd[1284]: SYSFS{}= will be removed in a future udev version, please use ATTR{}= to match the event device, or ATTRS{}= to match a parent device, in /lib/udev/rules.d/60-bluetooth.rules:23
Jun 27 15:49:01 (none) daemon.err udevd[1284]: BUS= will be removed in a future udev version, please use SUBSYSTEM= to match the event device, or SUBSYSTEMS= to match a parent device, in /lib/udev/rules.d/60-bluetooth.rules:26
Jun 27 15:49:01 (none) daemon.err udevd[1284]: SYSFS{}= will be removed in a future udev version, please use ATTR{}= to match the event device, or ATTRS{}= to match a parent device, in /lib/udev/rules.d/60-bluetooth.rules:26
Jun 27 15:49:01 (none) daemon.err udevd[1284]: BUS= will be removed in a future udev version, please use SUBSYSTEM= to match the event device, or SUBSYSTEMS= to match a parent device, in /lib/udev/rules.d/60-bluetooth.rules:29
Jun 27 15:49:01 (none) daemon.err udevd[1284]: SYSFS{}= will be removed in a future udev version, please use ATTR{}= to match the event device, or ATTRS{}= to match a parent device, in /lib/udev/rules.d/60-bluetooth.rules:29
Jun 27 15:49:01 (none) daemon.err udevd[1284]: BUS= will be removed in a future udev version, please use SUBSYSTEM= to match the event device, or SUBSYSTEMS= to match a parent device, in /lib/udev/rules.d/60-bluetooth.rules:32
Jun 27 15:49:01 (none) daemon.err udevd[1284]: SYSFS{}= will be removed in a future udev version, please use ATTR{}= to match the event device, or ATTRS{}= to match a parent device, in /lib/udev/rules.d/60-bluetooth.rules:32
Jun 27 15:49:01 (none) daemon.err udevd[1284]: BUS= will be removed in a future udev version, please use SUBSYSTEM= to match the event device, or SUBSYSTEMS= to match a parent device, in /lib/udev/rules.d/60-bluetooth.rules:35
Jun 27 15:49:01 (none) daemon.err udevd[1284]: SYSFS{}= will be removed in a future udev version, please use ATTR{}= to match the event device, or ATTRS{}= to match a parent device, in /lib/udev/rules.d/60-bluetooth.rules:35
Jun 27 15:49:01 (none) user.warn kernel: [    1.669273] ------------[ cut here ]------------
Jun 27 15:49:01 (none) user.warn kernel: [    1.669283] WARNING: at arch/x86/kernel/apic/ipi.c:109 default_send_IPI_mask_logical+0xb1/0xf0()
Jun 27 15:49:01 (none) user.warn kernel: [    1.669286] Hardware name: VPCSB1C5E
Jun 27 15:49:01 (none) user.warn kernel: [    1.669289] empty IPI mask
Jun 27 15:49:01 (none) user.warn kernel: [    1.669290] Modules linked in:
Jun 27 15:49:01 (none) user.warn kernel: [    1.669294] Pid: 1440, comm: blkid Not tainted 2.6.38.4-pmagic #1
Jun 27 15:49:01 (none) user.warn kernel: [    1.669296] Call Trace:
Jun 27 15:49:01 (none) user.warn kernel: [    1.669301]  [<c1045db2>] ? warn_slowpath_common+0x72/0xa0
Jun 27 15:49:01 (none) user.warn kernel: [    1.669305]  [<c101fd91>] ? default_send_IPI_mask_logical+0xb1/0xf0
Jun 27 15:49:01 (none) user.warn kernel: [    1.669310]  [<c101fd91>] ? default_send_IPI_mask_logical+0xb1/0xf0
Jun 27 15:49:01 (none) user.warn kernel: [    1.669313]  [<c1045e83>] ? warn_slowpath_fmt+0x33/0x40
Jun 27 15:49:01 (none) user.warn kernel: [    1.669316]  [<c101fd91>] ? default_send_IPI_mask_logical+0xb1/0xf0
Jun 27 15:49:01 (none) user.warn kernel: [    1.669320]  [<c101d907>] ? native_send_call_func_ipi+0x37/0x60
Jun 27 15:49:01 (none) user.warn kernel: [    1.669325]  [<c1077a06>] ? smp_call_function_many+0x136/0x230
Jun 27 15:49:01 (none) user.warn kernel: [    1.669331]  [<c1123fb0>] ? invalidate_bh_lru+0x0/0x40
Jun 27 15:49:01 (none) user.warn kernel: [    1.669334]  [<c1123fb0>] ? invalidate_bh_lru+0x0/0x40
Jun 27 15:49:01 (none) user.warn kernel: [    1.669338]  [<c1077b24>] ? smp_call_function+0x24/0x30
Jun 27 15:49:01 (none) user.warn kernel: [    1.669342]  [<c1077b4d>] ? on_each_cpu+0x1d/0x50
Jun 27 15:49:01 (none) user.warn kernel: [    1.669347]  [<c11238e9>] ? invalidate_bh_lrus+0x19/0x20
Jun 27 15:49:01 (none) user.warn kernel: [    1.669351]  [<c11299cf>] ? kill_bdev.clone.12+0x1f/0x40
Jun 27 15:49:01 (none) user.warn kernel: [    1.669354]  [<c112a095>] ? __blkdev_put+0x55/0x160
Jun 27 15:49:01 (none) user.warn kernel: [    1.669357]  [<c112a252>] ? blkdev_put+0xb2/0x130
Jun 27 15:49:01 (none) user.warn kernel: [    1.669361]  [<c112a2ed>] ? blkdev_close+0x1d/0x20
Jun 27 15:49:01 (none) user.warn kernel: [    1.669366]  [<c10fe665>] ? fput+0xb5/0x1e0
Jun 27 15:49:01 (none) user.warn kernel: [    1.669369]  [<c10fb53e>] ? filp_close+0x4e/0x70
Jun 27 15:49:01 (none) user.warn kernel: [    1.669372]  [<c10fbd15>] ? sys_close+0x75/0xd0
Jun 27 15:49:01 (none) user.warn kernel: [    1.669377]  [<c13f82e4>] ? syscall_call+0x7/0xb
Jun 27 15:49:01 (none) user.warn kernel: [    1.669382]  [<c13f0000>] ? init_intel+0xd7/0x32c
Jun 27 15:49:01 (none) user.warn kernel: [    1.669385] ---[ end trace 83d5b7d21480b685 ]---
Jun 27 15:49:01 (none) user.info kernel: [    2.041011] Refined TSC clocksource calibration: 2494.333 MHz.
Jun 27 15:49:01 (none) user.info kernel: [    2.041017] Switching to clocksource tsc
Jun 27 15:49:02 (none) user.info kernel: [    2.261066] i801_smbus 0000:00:1f.3: PCI INT B -> GSI 22 (level, low) -> IRQ 22
Jun 27 15:49:02 (none) user.warn kernel: [    2.261073] ACPI: resource 0000:00:1f.3 [io  0x8040-0x805f] conflicts with ACPI region SMBI [io 0x8040-0x804f]
Jun 27 15:49:02 (none) user.info kernel: [    2.261075] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
Jun 27 15:49:02 (none) user.info kernel: [    2.301504] Linux agpgart interface v0.103
Jun 27 15:49:02 (none) user.warn kernel: [    2.491094] ACPI: Deprecated procfs I/F for AC is loaded, please retry with CONFIG_ACPI_PROCFS_POWER cleared
Jun 27 15:49:02 (none) user.info kernel: [    2.491150] ACPI: AC Adapter [ADP1] (on-line)
Jun 27 15:49:02 (none) user.debug kernel: [    2.491229] ahci 0000:00:1f.2: version 3.0
Jun 27 15:49:02 (none) user.info kernel: [    2.491243] ahci 0000:00:1f.2: PCI INT A -> GSI 22 (level, low) -> IRQ 22
Jun 27 15:49:02 (none) user.debug kernel: [    2.491431] ahci 0000:00:1f.2: irq 41 for MSI/MSI-X
Jun 27 15:49:02 (none) user.info kernel: [    2.491685] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input1
Jun 27 15:49:02 (none) user.info kernel: [    2.491741] ahci: SSS flag set, parallel bus scan disabled
Jun 27 15:49:02 (none) user.info kernel: [    2.491761] ACPI: Lid Switch [LID0]
Jun 27 15:49:02 (none) user.info kernel: [    2.491798] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input2
Jun 27 15:49:02 (none) user.info kernel: [    2.491823] ACPI: Power Button [PWRB]
Jun 27 15:49:02 (none) user.info kernel: [    2.502420] ahci 0000:00:1f.2: AHCI 0001.0300 32 slots 6 ports 6 Gbps 0x11 impl RAID mode
Jun 27 15:49:02 (none) user.info kernel: [    2.502423] ahci 0000:00:1f.2: flags: 64bit ncq sntf stag pm led clo pio slum part apst 
Jun 27 15:49:02 (none) user.debug kernel: [    2.502429] ahci 0000:00:1f.2: setting latency timer to 64
Jun 27 15:49:02 (none) user.info kernel: [    2.502928] scsi0 : ahci
Jun 27 15:49:02 (none) user.info kernel: [    2.503007] scsi1 : ahci
Jun 27 15:49:02 (none) user.info kernel: [    2.503061] scsi2 : ahci
Jun 27 15:49:02 (none) user.info kernel: [    2.503113] scsi3 : ahci
Jun 27 15:49:02 (none) user.info kernel: [    2.503167] scsi4 : ahci
Jun 27 15:49:02 (none) user.info kernel: [    2.503218] scsi5 : ahci
Jun 27 15:49:02 (none) user.info kernel: [    2.503545] ata1: SATA max UDMA/133 abar m2048@0xc9408000 port 0xc9408100 irq 41
Jun 27 15:49:02 (none) user.info kernel: [    2.503547] ata2: DUMMY
Jun 27 15:49:02 (none) user.info kernel: [    2.503548] ata3: DUMMY
Jun 27 15:49:02 (none) user.info kernel: [    2.503549] ata4: DUMMY
Jun 27 15:49:02 (none) user.info kernel: [    2.503552] ata5: SATA max UDMA/133 abar m2048@0xc9408000 port 0xc9408300 irq 41
Jun 27 15:49:02 (none) user.info kernel: [    2.503553] ata6: DUMMY
Jun 27 15:49:02 (none) user.warn kernel: [    2.713178] ACPI: Deprecated procfs I/F for battery is loaded, please retry with CONFIG_ACPI_PROCFS_POWER cleared
Jun 27 15:49:02 (none) user.info kernel: [    2.713186] ACPI: Battery Slot [BAT1] (battery present)
Jun 27 15:49:02 (none) user.warn kernel: [    2.713214] ACPI: Deprecated procfs I/F for battery is loaded, please retry with CONFIG_ACPI_PROCFS_POWER cleared
Jun 27 15:49:02 (none) user.info kernel: [    2.713220] ACPI: Battery Slot [BAT2] (battery absent)
Jun 27 15:49:02 (none) user.info kernel: [    2.762205] cfg80211: Calling CRDA to update world regulatory domain
Jun 27 15:49:02 (none) user.info kernel: [    2.809019] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
Jun 27 15:49:02 (none) user.info kernel: [    2.812087] ata1.00: ATA-8: ST95005620AS, SD25, max UDMA/133
Jun 27 15:49:02 (none) user.info kernel: [    2.812089] ata1.00: 976773168 sectors, multi 0: LBA48 NCQ (depth 31/32)
Jun 27 15:49:02 (none) user.info kernel: [    2.815229] ata1.00: configured for UDMA/133
Jun 27 15:49:02 (none) user.notice kernel: [    2.815336] scsi 0:0:0:0: Direct-Access     ATA      ST95005620AS     SD25 PQ: 0 ANSI: 5
Jun 27 15:49:02 (none) user.notice kernel: [    2.815525] sd 0:0:0:0: [sda] 976773168 512-byte logical blocks: (500 GB/465 GiB)
Jun 27 15:49:02 (none) user.notice kernel: [    2.815617] sd 0:0:0:0: [sda] Write Protect is off
Jun 27 15:49:02 (none) user.debug kernel: [    2.815619] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
Jun 27 15:49:02 (none) user.notice kernel: [    2.815647] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Jun 27 15:49:02 (none) user.info kernel: [    2.816859]  sda: sda1 sda2 sda3 sda4 < sda5 sda6 sda7 >
Jun 27 15:49:02 (none) user.notice kernel: [    2.817301] sd 0:0:0:0: [sda] Attached SCSI disk
Jun 27 15:49:02 (none) user.info kernel: [    2.904151] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
Jun 27 15:49:02 (none) user.info kernel: [    2.904186] ehci_hcd 0000:00:1a.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
Jun 27 15:49:02 (none) user.debug kernel: [    2.904209] ehci_hcd 0000:00:1a.0: setting latency timer to 64
Jun 27 15:49:02 (none) user.info kernel: [    2.904213] ehci_hcd 0000:00:1a.0: EHCI Host Controller
Jun 27 15:49:02 (none) user.info kernel: [    2.904302] ehci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 1
Jun 27 15:49:02 (none) user.info kernel: [    2.909900] ehci_hcd 0000:00:1a.0: debug port 2
Jun 27 15:49:02 (none) user.debug kernel: [    2.913788] ehci_hcd 0000:00:1a.0: cache line size of 64 is not supported
Jun 27 15:49:02 (none) user.info kernel: [    2.913804] ehci_hcd 0000:00:1a.0: irq 23, io mem 0xc940a000
Jun 27 15:49:02 (none) user.info kernel: [    2.922856] ehci_hcd 0000:00:1a.0: USB 2.0 started, EHCI 1.00
Jun 27 15:49:02 (none) user.info kernel: [    2.922873] usb usb1: New USB device found, idVendor=1d6b, idProduct=0002
Jun 27 15:49:02 (none) user.info kernel: [    2.922875] usb usb1: New USB device strings: Mfr=3, Product=2, SerialNumber=1
Jun 27 15:49:02 (none) user.info kernel: [    2.922877] usb usb1: Product: EHCI Host Controller
Jun 27 15:49:02 (none) user.info kernel: [    2.922879] usb usb1: Manufacturer: Linux 2.6.38.4-pmagic ehci_hcd
Jun 27 15:49:02 (none) user.info kernel: [    2.922880] usb usb1: SerialNumber: 0000:00:1a.0
Jun 27 15:49:02 (none) user.info kernel: [    2.922982] hub 1-0:1.0: USB hub found
Jun 27 15:49:02 (none) user.info kernel: [    2.922987] hub 1-0:1.0: 2 ports detected
Jun 27 15:49:02 (none) user.info kernel: [    2.923109] ehci_hcd 0000:00:1d.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
Jun 27 15:49:02 (none) user.debug kernel: [    2.923129] ehci_hcd 0000:00:1d.0: setting latency timer to 64
Jun 27 15:49:02 (none) user.info kernel: [    2.923133] ehci_hcd 0000:00:1d.0: EHCI Host Controller
Jun 27 15:49:02 (none) user.info kernel: [    2.923170] ehci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
Jun 27 15:49:02 (none) user.info kernel: [    2.929878] ehci_hcd 0000:00:1d.0: debug port 2
Jun 27 15:49:02 (none) user.debug kernel: [    2.933752] ehci_hcd 0000:00:1d.0: cache line size of 64 is not supported
Jun 27 15:49:02 (none) user.info kernel: [    2.933800] ehci_hcd 0000:00:1d.0: irq 20, io mem 0xc9409000
Jun 27 15:49:02 (none) user.info kernel: [    2.942830] ehci_hcd 0000:00:1d.0: USB 2.0 started, EHCI 1.00
Jun 27 15:49:02 (none) user.info kernel: [    2.942850] usb usb2: New USB device found, idVendor=1d6b, idProduct=0002
Jun 27 15:49:02 (none) user.info kernel: [    2.942853] usb usb2: New USB device strings: Mfr=3, Product=2, SerialNumber=1
Jun 27 15:49:02 (none) user.info kernel: [    2.942856] usb usb2: Product: EHCI Host Controller
Jun 27 15:49:02 (none) user.info kernel: [    2.942858] usb usb2: Manufacturer: Linux 2.6.38.4-pmagic ehci_hcd
Jun 27 15:49:02 (none) user.info kernel: [    2.942860] usb usb2: SerialNumber: 0000:00:1d.0
Jun 27 15:49:02 (none) user.info kernel: [    2.943087] hub 2-0:1.0: USB hub found
Jun 27 15:49:02 (none) user.info kernel: [    2.943092] hub 2-0:1.0: 2 ports detected
Jun 27 15:49:02 (none) user.info kernel: [    2.978743] xhci_hcd 0000:04:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
Jun 27 15:49:02 (none) user.debug kernel: [    2.978771] xhci_hcd 0000:04:00.0: setting latency timer to 64
Jun 27 15:49:02 (none) user.info kernel: [    2.978781] xhci_hcd 0000:04:00.0: xHCI Host Controller
Jun 27 15:49:02 (none) user.info kernel: [    2.978856] xhci_hcd 0000:04:00.0: new USB bus registered, assigned bus number 3
Jun 27 15:49:02 (none) user.info kernel: [    3.089458] xhci_hcd 0000:04:00.0: irq 18, io mem 0xc5400000
Jun 27 15:49:02 (none) user.debug kernel: [    3.089541] xhci_hcd 0000:04:00.0: irq 42 for MSI/MSI-X
Jun 27 15:49:02 (none) user.debug kernel: [    3.089544] xhci_hcd 0000:04:00.0: irq 43 for MSI/MSI-X
Jun 27 15:49:02 (none) user.debug kernel: [    3.089546] xhci_hcd 0000:04:00.0: irq 44 for MSI/MSI-X
Jun 27 15:49:02 (none) user.debug kernel: [    3.089548] xhci_hcd 0000:04:00.0: irq 45 for MSI/MSI-X
Jun 27 15:49:02 (none) user.debug kernel: [    3.089550] xhci_hcd 0000:04:00.0: irq 46 for MSI/MSI-X
Jun 27 15:49:02 (none) user.warn kernel: [    3.092857] usb usb3: No SuperSpeed endpoint companion for config 1  interface 0 altsetting 0 ep 129: using minimum values
Jun 27 15:49:02 (none) user.info kernel: [    3.092864] usb usb3: New USB device found, idVendor=1d6b, idProduct=0003
Jun 27 15:49:02 (none) user.info kernel: [    3.092866] usb usb3: New USB device strings: Mfr=3, Product=2, SerialNumber=1
Jun 27 15:49:02 (none) user.info kernel: [    3.092867] usb usb3: Product: xHCI Host Controller
Jun 27 15:49:02 (none) user.info kernel: [    3.092869] usb usb3: Manufacturer: Linux 2.6.38.4-pmagic xhci_hcd
Jun 27 15:49:02 (none) user.info kernel: [    3.092870] usb usb3: SerialNumber: 0000:04:00.0
Jun 27 15:49:02 (none) user.debug kernel: [    3.092961] xHCI xhci_add_endpoint called for root hub
Jun 27 15:49:02 (none) user.debug kernel: [    3.092963] xHCI xhci_check_bandwidth called for root hub
Jun 27 15:49:02 (none) user.info kernel: [    3.093001] hub 3-0:1.0: USB hub found
Jun 27 15:49:02 (none) user.info kernel: [    3.093006] hub 3-0:1.0: 4 ports detected
Jun 27 15:49:02 (none) user.info kernel: [    3.122616] ata5: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
Jun 27 15:49:02 (none) user.info kernel: [    3.123841] ata5.00: ATAPI: MATSHITABD-MLT UJ242AS, 1.40, max UDMA/100
Jun 27 15:49:02 (none) user.info kernel: [    3.125324] ata5.00: configured for UDMA/100
Jun 27 15:49:02 (none) user.notice kernel: [    3.126884] scsi 4:0:0:0: CD-ROM            MATSHITA BD-MLT UJ242AS   1.40 PQ: 0 ANSI: 5
Jun 27 15:49:02 (none) user.warn kernel: [    3.128041] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
Jun 27 15:49:02 (none) user.info kernel: [    3.128043] cdrom: Uniform CD-ROM driver Revision: 3.20
Jun 27 15:49:02 (none) user.debug kernel: [    3.128287] sr 4:0:0:0: Attached scsi CD-ROM sr0
Jun 27 15:49:02 (none) user.info kernel: [    3.144884] thermal LNXTHERM:00: registered as thermal_zone0
Jun 27 15:49:02 (none) user.info kernel: [    3.144887] ACPI: Thermal Zone [TZ01] (72 C)
Jun 27 15:49:02 (none) user.debug kernel: [    3.147479] ACPI: acpi_idle registered with cpuidle
Jun 27 15:49:02 (none) user.debug kernel: [    3.164608] Monitor-Mwait will be used to enter C-1 state
Jun 27 15:49:02 (none) user.debug kernel: [    3.164648] Monitor-Mwait will be used to enter C-3 state
Jun 27 15:49:03 (none) user.info kernel: [    3.224481] usb 1-1: new high speed USB device using ehci_hcd and address 2
Jun 27 15:49:03 (none) user.info kernel: [    3.299619] input: ImPS/2 Generic Wheel Mouse as /devices/platform/i8042/serio1/input/input3
Jun 27 15:49:03 (none) user.info kernel: [    3.321058] agpgart-intel 0000:00:00.0: Intel Sandybridge Chipset
Jun 27 15:49:03 (none) user.info kernel: [    3.321140] agpgart-intel 0000:00:00.0: detected gtt size: 2097152K total, 262144K mappable
Jun 27 15:49:03 (none) user.info kernel: [    3.322131] agpgart-intel 0000:00:00.0: detected 65536K stolen memory
Jun 27 15:49:03 (none) user.info kernel: [    3.322384] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0xb0000000
Jun 27 15:49:03 (none) user.info kernel: [    3.327877] tpm_tis 00:0a: 1.2 TPM (device-id 0xB, rev-id 16)
Jun 27 15:49:03 (none) user.info kernel: [    3.340700] usb 1-1: New USB device found, idVendor=8087, idProduct=0024
Jun 27 15:49:03 (none) user.info kernel: [    3.340702] usb 1-1: New USB device strings: Mfr=0, Product=0, SerialNumber=0
Jun 27 15:49:03 (none) user.info kernel: [    3.340967] hub 1-1:1.0: USB hub found
Jun 27 15:49:03 (none) user.info kernel: [    3.341046] hub 1-1:1.0: 6 ports detected
Jun 27 15:49:03 (none) user.info kernel: [    3.371317] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
Jun 27 15:49:03 (none) user.info kernel: [    3.371346] r8169 0000:05:00.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
Jun 27 15:49:03 (none) user.debug kernel: [    3.371456] r8169 0000:05:00.0: setting latency timer to 64
Jun 27 15:49:03 (none) user.notice kernel: [    3.371471] r8169 0000:05:00.0: (unregistered net_device): unknown MAC, using family default
Jun 27 15:49:03 (none) user.debug kernel: [    3.371681] r8169 0000:05:00.0: irq 47 for MSI/MSI-X
Jun 27 15:49:03 (none) user.info kernel: [    3.371824] r8169 0000:05:00.0: eth0: RTL8168b/8111b at 0xef982000, f0:bf:97:59:18:50, XID 0c200000 IRQ 47
Jun 27 15:49:03 (none) user.info kernel: [    3.443189] usb 2-1: new high speed USB device using ehci_hcd and address 2
Jun 27 15:49:03 (none) user.notice kernel: [    3.449301] sd 0:0:0:0: Attached scsi generic sg0 type 0
Jun 27 15:49:03 (none) user.notice kernel: [    3.449382] sr 4:0:0:0: Attached scsi generic sg1 type 5
Jun 27 15:49:03 (none) user.info kernel: [    3.485476] rtc_cmos 00:06: RTC can wake from S4
Jun 27 15:49:03 (none) user.info kernel: [    3.488024] sony-laptop: Sony Notebook Control Driver v0.6.
Jun 27 15:49:03 (none) user.info kernel: [    3.493179] rtc_cmos 00:06: rtc core: registered rtc_cmos as rtc0
Jun 27 15:49:03 (none) user.info kernel: [    3.493222] rtc0: alarms up to one month, y3k, 242 bytes nvram, hpet irqs
Jun 27 15:49:03 (none) user.info kernel: [    3.504152] input: Sony Vaio Keys as /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:01/SNY5001:00/input/input4
Jun 27 15:49:03 (none) user.info kernel: [    3.504239] input: Sony Vaio Jogdial as /devices/virtual/input/input5
Jun 27 15:49:03 (none) user.info kernel: [    3.504537] sony-laptop: brightness ignored, must be controlled by ACPI video driver
Jun 27 15:49:03 (none) user.info kernel: [    3.557391] usb 2-1: New USB device found, idVendor=8087, idProduct=0024
Jun 27 15:49:03 (none) user.info kernel: [    3.557395] usb 2-1: New USB device strings: Mfr=0, Product=0, SerialNumber=0
Jun 27 15:49:03 (none) user.info kernel: [    3.557674] hub 2-1:1.0: USB hub found
Jun 27 15:49:03 (none) user.info kernel: [    3.557764] hub 2-1:1.0: 8 ports detected
Jun 27 15:49:03 (none) user.info kernel: [    3.664136] usb 3-1: new SuperSpeed USB device using xhci_hcd and address 2
Jun 27 15:49:03 (none) user.warn kernel: [    3.701714] xhci_hcd 0000:04:00.0: WARN: short transfer on control ep
Jun 27 15:49:03 (none) user.warn kernel: [    3.707454] xhci_hcd 0000:04:00.0: WARN: short transfer on control ep
Jun 27 15:49:03 (none) user.warn kernel: [    3.713445] xhci_hcd 0000:04:00.0: WARN: short transfer on control ep
Jun 27 15:49:03 (none) user.warn kernel: [    3.719162] xhci_hcd 0000:04:00.0: WARN: short transfer on control ep
Jun 27 15:49:03 (none) user.info kernel: [    3.719304] usb 3-1: New USB device found, idVendor=059b, idProduct=0070
Jun 27 15:49:03 (none) user.info kernel: [    3.719307] usb 3-1: New USB device strings: Mfr=1, Product=2, SerialNumber=3
Jun 27 15:49:03 (none) user.info kernel: [    3.719311] usb 3-1: Product: LPHD-UP3
Jun 27 15:49:03 (none) user.info kernel: [    3.719313] usb 3-1: Manufacturer: iomega
Jun 27 15:49:03 (none) user.info kernel: [    3.719315] usb 3-1: SerialNumber: 0000D20218A3
Jun 27 15:49:03 (none) user.warn kernel: [    3.749250] xhci_hcd 0000:04:00.0: WARN: short transfer on control ep
Jun 27 15:49:03 (none) user.warn kernel: [    3.756363] xhci_hcd 0000:04:00.0: WARN: short transfer on control ep
Jun 27 15:49:03 (none) user.info kernel: [    3.818810] usb 1-1.1: new full speed USB device using ehci_hcd and address 3
Jun 27 15:49:03 (none) user.info kernel: [    3.842058] [drm] Initialized drm 1.1.0 20060810
Jun 27 15:49:03 (none) user.info kernel: [    3.877001] Initializing USB Mass Storage driver...
Jun 27 15:49:03 (none) user.info kernel: [    3.877088] scsi6 : usb-storage 3-1:1.0
Jun 27 15:49:03 (none) user.info kernel: [    3.877201] usbcore: registered new interface driver usb-storage
Jun 27 15:49:03 (none) user.info kernel: [    3.877203] USB Mass Storage support registered.
Jun 27 15:49:03 (none) user.info kernel: [    3.905068] usb 1-1.1: New USB device found, idVendor=08ff, idProduct=168f
Jun 27 15:49:03 (none) user.info kernel: [    3.905072] usb 1-1.1: New USB device strings: Mfr=0, Product=1, SerialNumber=0
Jun 27 15:49:03 (none) user.info kernel: [    3.905075] usb 1-1.1: Product: Fingerprint Sensor
Jun 27 15:49:03 (none) user.info kernel: [    3.923724] iwlagn: Intel(R) Wireless WiFi Link AGN driver for Linux, in-tree:
Jun 27 15:49:03 (none) user.info kernel: [    3.923727] iwlagn: Copyright(c) 2003-2010 Intel Corporation
Jun 27 15:49:03 (none) user.info kernel: [    3.923778] iwlagn 0000:02:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Jun 27 15:49:03 (none) user.debug kernel: [    3.923789] iwlagn 0000:02:00.0: setting latency timer to 64
Jun 27 15:49:03 (none) user.info kernel: [    3.923827] iwlagn 0000:02:00.0: Detected Intel(R) Centrino(R) Wireless-N 1000 BGN, REV=0x6C
Jun 27 15:49:03 (none) user.info kernel: [    3.944980] iwlagn 0000:02:00.0: device EEPROM VER=0x15d, CALIB=0x6
Jun 27 15:49:03 (none) user.info kernel: [    3.944982] iwlagn 0000:02:00.0: Device SKU: 0X9
Jun 27 15:49:03 (none) user.info kernel: [    3.944983] iwlagn 0000:02:00.0: Valid Tx ant: 0X1, Valid Rx ant: 0X3
Jun 27 15:49:03 (none) user.info kernel: [    3.944994] iwlagn 0000:02:00.0: Tunable channels: 13 802.11bg, 0 802.11a channels
Jun 27 15:49:03 (none) user.debug kernel: [    3.945333] iwlagn 0000:02:00.0: irq 48 for MSI/MSI-X
Jun 27 15:49:03 (none) user.info kernel: [    3.953782] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Jun 27 15:49:03 (none) user.debug kernel: [    3.953852] HDA Intel 0000:00:1b.0: irq 49 for MSI/MSI-X
Jun 27 15:49:03 (none) user.debug kernel: [    3.953884] HDA Intel 0000:00:1b.0: setting latency timer to 64
Jun 27 15:49:03 (none) user.info kernel: [    3.980602] usb 1-1.3: new high speed USB device using ehci_hcd and address 4
Jun 27 15:49:03 (none) user.info kernel: [    4.008678] usbcore: registered new interface driver uas
Jun 27 15:49:03 (none) user.info kernel: [    4.085368] usb 1-1.3: New USB device found, idVendor=0c45, idProduct=64b5
Jun 27 15:49:03 (none) user.info kernel: [    4.085373] usb 1-1.3: New USB device strings: Mfr=2, Product=1, SerialNumber=0
Jun 27 15:49:03 (none) user.info kernel: [    4.085376] usb 1-1.3: Product: USB 2.0 Camera
Jun 27 15:49:03 (none) user.info kernel: [    4.085379] usb 1-1.3: Manufacturer: 93010A601289G14GBJG
Jun 27 15:49:03 (none) user.info kernel: [    4.150385] usb 1-1.6: new full speed USB device using ehci_hcd and address 5
Jun 27 15:49:04 (none) user.info kernel: [    4.173978] [drm] radeon defaulting to kernel modesetting.
Jun 27 15:49:04 (none) user.info kernel: [    4.173981] [drm] radeon kernel modesetting enabled.
Jun 27 15:49:04 (none) user.info kernel: [    4.173995] VGA switcheroo: detected switching method \_SB_.PCI0.GFX0.ATPX handle
Jun 27 15:49:04 (none) user.info kernel: [    4.174031] radeon 0000:01:00.0: enabling device (0000 -> 0003)
Jun 27 15:49:04 (none) user.info kernel: [    4.174039] radeon 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Jun 27 15:49:04 (none) user.debug kernel: [    4.174046] radeon 0000:01:00.0: setting latency timer to 64
Jun 27 15:49:04 (none) user.info kernel: [    4.175201] [drm] initializing kernel modesetting (TURKS 0x1002:0x6741).
Jun 27 15:49:04 (none) user.info kernel: [    4.175256] [drm] register mmio base: 0xC8400000
Jun 27 15:49:04 (none) user.info kernel: [    4.175257] [drm] register mmio size: 131072
Jun 27 15:49:04 (none) user.info kernel: [    4.192542] iwlagn 0000:02:00.0: loaded firmware version 128.50.3.1 build 13488
Jun 27 15:49:04 (none) user.debug kernel: [    4.194346] ieee80211 phy0: Selected rate control algorithm 'iwl-agn-rs'
Jun 27 15:49:04 (none) user.info kernel: [    4.237052] Linux video capture interface: v2.00
Jun 27 15:49:04 (none) user.info kernel: [    4.239129] usb 1-1.6: New USB device found, idVendor=0489, idProduct=e00f
Jun 27 15:49:04 (none) user.info kernel: [    4.239132] usb 1-1.6: New USB device strings: Mfr=1, Product=2, SerialNumber=3
Jun 27 15:49:04 (none) user.info kernel: [    4.239134] usb 1-1.6: Product: Broadcom Bluetooth Device
Jun 27 15:49:04 (none) user.info kernel: [    4.239136] usb 1-1.6: Manufacturer: Broadcom Corp
Jun 27 15:49:04 (none) user.info kernel: [    4.239137] usb 1-1.6: SerialNumber: EC55F9CAD44F
Jun 27 15:49:04 (none) user.info kernel: [    4.239291] uvcvideo: Found UVC 1.00 device USB 2.0 Camera (0c45:64b5)
Jun 27 15:49:04 (none) user.info kernel: [    4.249241] input: USB 2.0 Camera as /devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.3/1-1.3:1.0/input/input6
Jun 27 15:49:04 (none) user.info kernel: [    4.249317] usbcore: registered new interface driver uvcvideo
Jun 27 15:49:04 (none) user.info kernel: [    4.249319] USB Video Class driver (v1.0.0)
Jun 27 15:49:04 (none) user.info kernel: [    4.294482] Bluetooth: Core ver 2.15
Jun 27 15:49:04 (none) user.info kernel: [    4.294502] NET: Registered protocol family 31
Jun 27 15:49:04 (none) user.info kernel: [    4.294504] Bluetooth: HCI device and connection manager initialized
Jun 27 15:49:04 (none) user.info kernel: [    4.294506] Bluetooth: HCI socket layer initialized
Jun 27 15:49:04 (none) user.info kernel: [    4.312162] usb 2-1.2: new full speed USB device using ehci_hcd and address 3
Jun 27 15:49:04 (none) user.info kernel: [    4.347744] Bluetooth: Generic Bluetooth USB driver ver 0.6
Jun 27 15:49:04 (none) user.info kernel: [    4.349664] usbcore: registered new interface driver btusb
Jun 27 15:49:04 (none) user.info kernel: [    4.501722] hda_codec: ALC275: SKU not ready 0x411111f0
Jun 27 15:49:04 (none) user.info kernel: [    4.501726] hda_codec: ALC275: BIOS auto-probing.
Jun 27 15:49:04 (none) user.info kernel: [    4.508078] input: HDA Intel PCH Headphone as /devices/pci0000:00/0000:00:1b.0/sound/card0/input7
Jun 27 15:49:04 (none) user.info kernel: [    4.508270] i915 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Jun 27 15:49:04 (none) user.debug kernel: [    4.508275] i915 0000:00:02.0: setting latency timer to 64
Jun 27 15:49:04 (none) user.info kernel: [    4.612678] usb 2-1.2: New USB device found, idVendor=0a12, idProduct=0001
Jun 27 15:49:04 (none) user.info kernel: [    4.612687] usb 2-1.2: New USB device strings: Mfr=0, Product=2, SerialNumber=0
Jun 27 15:49:04 (none) user.info kernel: [    4.612692] usb 2-1.2: Product: BT2.0
Jun 27 15:49:04 (none) user.notice kernel: [    4.886031] scsi 6:0:0:0: Direct-Access     OEM      Ext Hard Disk    0000 PQ: 0 ANSI: 5
Jun 27 15:49:04 (none) user.notice kernel: [    4.886281] sd 6:0:0:0: Attached scsi generic sg2 type 0
Jun 27 15:49:04 (none) user.notice kernel: [    4.987654] sd 6:0:0:0: [sdb] 244190646 4096-byte logical blocks: (1.00 TB/931 GiB)
Jun 27 15:49:04 (none) user.notice kernel: [    5.040805] sd 6:0:0:0: [sdb] Write Protect is off
Jun 27 15:49:04 (none) user.debug kernel: [    5.040819] sd 6:0:0:0: [sdb] Mode Sense: 10 00 00 00
Jun 27 15:49:04 (none) user.notice kernel: [    5.141541] sd 6:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Jun 27 15:49:05 (none) user.notice kernel: [    5.242842] sd 6:0:0:0: [sdb] 244190646 4096-byte logical blocks: (1.00 TB/931 GiB)
Jun 27 15:49:05 (none) user.info kernel: [    5.393071] ATOM BIOS: Sony
Jun 27 15:49:05 (none) user.info kernel: [    5.393113] radeon 0000:01:00.0: VRAM: 1024M 0x0000000000000000 - 0x000000003FFFFFFF (1024M used)
Jun 27 15:49:05 (none) user.info kernel: [    5.393116] radeon 0000:01:00.0: GTT: 512M 0x0000000040000000 - 0x000000005FFFFFFF
Jun 27 15:49:05 (none) user.info kernel: [    5.394298] [drm] Detected VRAM RAM=1024M, BAR=256M
Jun 27 15:49:05 (none) user.info kernel: [    5.394301] [drm] RAM width 128bits DDR
Jun 27 15:49:05 (none) user.info kernel: [    5.394435] [TTM] Zone  kernel: Available graphics memory: 364960 kiB.
Jun 27 15:49:05 (none) user.info kernel: [    5.394437] [TTM] Zone highmem: Available graphics memory: 1248804 kiB.
Jun 27 15:49:05 (none) user.info kernel: [    5.394438] [TTM] Initializing pool allocator.
Jun 27 15:49:05 (none) user.info kernel: [    5.394451] [drm] radeon: 1024M of VRAM memory ready
Jun 27 15:49:05 (none) user.info kernel: [    5.394453] [drm] radeon: 512M of GTT memory ready.
Jun 27 15:49:05 (none) user.info kernel: [    5.394468] [drm] Supports vblank timestamp caching Rev 1 (10.10.2010).
Jun 27 15:49:05 (none) user.info kernel: [    5.394469] [drm] Driver supports precise vblank timestamp query.
Jun 27 15:49:05 (none) user.debug kernel: [    5.394511] radeon 0000:01:00.0: irq 50 for MSI/MSI-X
Jun 27 15:49:05 (none) user.info kernel: [    5.394517] radeon 0000:01:00.0: radeon: using MSI.
Jun 27 15:49:05 (none) user.info kernel: [    5.394583] [drm] radeon: irq initialized.
Jun 27 15:49:05 (none) user.info kernel: [    5.394585] [drm] GART: num cpu pages 131072, num gpu pages 131072
Jun 27 15:49:05 (none) user.info kernel: [    5.394814] [drm] Loading TURKS Microcode
Jun 27 15:49:05 (none) user.err kernel: [    5.397198] ni_cp: Failed to load firmware "radeon/TURKS_pfp.bin"
Jun 27 15:49:05 (none) user.err kernel: [    5.397201] [drm:evergreen_startup] *ERROR* Failed to load firmware!
Jun 27 15:49:05 (none) user.err kernel: [    5.397205] radeon 0000:01:00.0: disabling GPU acceleration
Jun 27 15:49:05 (none) user.warn kernel: [    5.398285] radeon 0000:01:00.0: ee7c1000 unpin not necessary
Jun 27 15:49:05 (none) user.warn kernel: [    5.398287] radeon 0000:01:00.0: ee7c1000 unpin not necessary
Jun 27 15:49:05 (none) user.info kernel: [    5.398456] [drm] Radeon Display Connectors
Jun 27 15:49:05 (none) user.info kernel: [    5.398459] [drm] Internal thermal controller without fan control
Jun 27 15:49:05 (none) user.info kernel: [    5.398489] [drm] radeon: power management initialized
Jun 27 15:49:05 (none) user.info kernel: [    5.398602] No connectors reported connected with modes
Jun 27 15:49:05 (none) user.info kernel: [    5.398605] [drm] Cannot find any crtc or sizes - going 1024x768
Jun 27 15:49:05 (none) user.info kernel: [    5.400910] [drm] fb mappable at 0xA0040000
Jun 27 15:49:05 (none) user.info kernel: [    5.400912] [drm] vram apper at 0xA0000000
Jun 27 15:49:05 (none) user.info kernel: [    5.400913] [drm] size 3145728
Jun 27 15:49:05 (none) user.info kernel: [    5.400914] [drm] fb depth is 24
Jun 27 15:49:05 (none) user.info kernel: [    5.400915] [drm]    pitch is 4096
Jun 27 15:49:05 (none) user.warn kernel: [    5.403491] Console: switching to colour frame buffer device 128x48
Jun 27 15:49:05 (none) user.info kernel: [    5.405537] fb0: radeondrmfb frame buffer device
Jun 27 15:49:05 (none) user.info kernel: [    5.405538] drm: registered panic notifier
Jun 27 15:49:05 (none) user.info kernel: [    5.405541] [drm] Initialized radeon 2.8.0 20080528 for 0000:01:00.0 on minor 0
Jun 27 15:49:05 (none) user.info kernel: [    5.415229] mtrr: no more MTRRs available
Jun 27 15:49:05 (none) user.info kernel: [    5.415231] [drm] MTRR allocation failed.  Graphics performance may suffer.
Jun 27 15:49:05 (none) user.debug kernel: [    5.415606] i915 0000:00:02.0: irq 50 for MSI/MSI-X
Jun 27 15:49:05 (none) user.info kernel: [    5.415610] [drm] Supports vblank timestamp caching Rev 1 (10.10.2010).
Jun 27 15:49:05 (none) user.info kernel: [    5.415612] [drm] Driver supports precise vblank timestamp query.
Jun 27 15:49:05 (none) user.info kernel: [    5.448785] vga_switcheroo: enabled
Jun 27 15:49:05 (none) user.info kernel: [    5.448843] radeon atpx: version is 1
Jun 27 15:49:05 (none) user.info kernel: [    5.456165] vgaarb: device changed decodes: PCI:0000:01:00.0,olddecodes=io+mem,decodes=none:owns=none
Jun 27 15:49:05 (none) user.info kernel: [    5.456170] vgaarb: device changed decodes: PCI:0000:00:02.0,olddecodes=io+mem,decodes=none:owns=io+mem
Jun 27 15:49:05 (none) user.info kernel: [    5.508657] fb1: inteldrmfb frame buffer device
Jun 27 15:49:05 (none) user.warn kernel: [    5.508831] [Firmware Bug]: ACPI(PEGP) defines _DOD but not _DOS
Jun 27 15:49:05 (none) user.info kernel: [    5.509862] acpi LNXVIDEO:02: registered as cooling_device4
Jun 27 15:49:05 (none) user.info kernel: [    5.510417] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:27/LNXVIDEO:00/input/input8
Jun 27 15:49:05 (none) user.info kernel: [    5.510454] ACPI: Video Device [PEGP] (multi-head: yes  rom: no  post: no)
Jun 27 15:49:05 (none) user.warn kernel: [    5.510480] [Firmware Bug]: Duplicate ACPI video bus devices for the same VGA controller, please try module parameter "video.allow_duplicates=1"if the current driver doesn't work.
Jun 27 15:49:05 (none) user.warn kernel: [    5.510488] [Firmware Bug]: Duplicate ACPI video bus devices for the same VGA controller, please try module parameter "video.allow_duplicates=1"if the current driver doesn't work.
Jun 27 15:49:05 (none) user.warn kernel: [    5.510495] [Firmware Bug]: Duplicate ACPI video bus devices for the same VGA controller, please try module parameter "video.allow_duplicates=1"if the current driver doesn't work.
Jun 27 15:49:05 (none) user.warn kernel: [    5.510507] [Firmware Bug]: Duplicate ACPI video bus devices for the same VGA controller, please try module parameter "video.allow_duplicates=1"if the current driver doesn't work.
Jun 27 15:49:05 (none) user.warn kernel: [    5.510515] [Firmware Bug]: Duplicate ACPI video bus devices for the same VGA controller, please try module parameter "video.allow_duplicates=1"if the current driver doesn't work.
Jun 27 15:49:05 (none) user.warn kernel: [    5.510524] [Firmware Bug]: Duplicate ACPI video bus devices for the same VGA controller, please try module parameter "video.allow_duplicates=1"if the current driver doesn't work.
Jun 27 15:49:05 (none) user.warn kernel: [    5.510531] [Firmware Bug]: Duplicate ACPI video bus devices for the same VGA controller, please try module parameter "video.allow_duplicates=1"if the current driver doesn't work.
Jun 27 15:49:05 (none) user.info kernel: [    5.511528] acpi device:2a: registered as cooling_device5
Jun 27 15:49:05 (none) user.info kernel: [    5.511964] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/LNXVIDEO:09/input/input9
Jun 27 15:49:05 (none) user.info kernel: [    5.512051] ACPI: Video Device [GFX0] (multi-head: yes  rom: no  post: no)
Jun 27 15:49:05 (none) user.info kernel: [    5.512219] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 1
Jun 27 15:49:05 (none) user.info kernel: [    5.818497]  sdb: sdb1
Jun 27 15:49:05 (none) user.notice kernel: [    5.876460] sd 6:0:0:0: [sdb] 244190646 4096-byte logical blocks: (1.00 TB/931 GiB)
Jun 27 15:49:05 (none) user.notice kernel: [    5.956554] sd 6:0:0:0: [sdb] Attached SCSI disk
Jun 27 15:49:08 (none) user.debug kernel: [    8.334346] ISO 9660 Extensions: RRIP_1991A
Jun 27 15:50:12 (none) user.warn kernel: [   72.786069] aufs test_add:262:mount[2590]: uid/gid/perm /branches/fmu 0/0/0755, 0/0/01777
Jun 27 15:50:12 (none) user.warn kernel: [   72.786074] aufs test_add:262:mount[2590]: uid/gid/perm /branches/sqfs 0/0/0755, 0/0/01777
Jun 27 15:50:12 (none) user.warn kernel: [   72.794839] aufs may_rename_srcdir:487:mv[2599]: renaming dir who has child(ren) on multiple branches, is not supported
Jun 27 15:50:12 (none) user.notice kernel: klogd: exiting
Jun 27 15:50:12 (none) syslog.info syslogd exiting
Jun 27 15:50:13 (none) syslog.info syslogd started: BusyBox v1.18.4
Jun 27 15:50:13 (none) user.notice kernel: klogd started: BusyBox v1.18.4 (2011-04-09 18:49:28 CDT)
Jun 27 15:50:13 (none) daemon.err udevd[2633]: BUS= will be removed in a future udev version, please use SUBSYSTEM= to match the event device, or SUBSYSTEMS= to match a parent device, in /lib/udev/rules.d/60-bluetooth.rules:2
Jun 27 15:50:13 (none) daemon.err udevd[2633]: SYSFS{}= will be removed in a future udev version, please use ATTR{}= to match the event device, or ATTRS{}= to match a parent device, in /lib/udev/rules.d/60-bluetooth.rules:2
Jun 27 15:50:13 (none) daemon.err udevd[2633]: BUS= will be removed in a future udev version, please use SUBSYSTEM= to match the event device, or SUBSYSTEMS= to match a parent device, in /lib/udev/rules.d/60-bluetooth.rules:5
Jun 27 15:50:13 (none) daemon.err udevd[2633]: SYSFS{}= will be removed in a future udev version, please use ATTR{}= to match the event device, or ATTRS{}= to match a parent device, in /lib/udev/rules.d/60-bluetooth.rules:5
Jun 27 15:50:13 (none) daemon.err udevd[2633]: BUS= will be removed in a future udev version, please use SUBSYSTEM= to match the event device, or SUBSYSTEMS= to match a parent device, in /lib/udev/rules.d/60-bluetooth.rules:8
Jun 27 15:50:13 (none) daemon.err udevd[2633]: SYSFS{}= will be removed in a future udev version, please use ATTR{}= to match the event device, or ATTRS{}= to match a parent device, in /lib/udev/rules.d/60-bluetooth.rules:8
Jun 27 15:50:13 (none) daemon.err udevd[2633]: BUS= will be removed in a future udev version, please use SUBSYSTEM= to match the event device, or SUBSYSTEMS= to match a parent device, in /lib/udev/rules.d/60-bluetooth.rules:11
Jun 27 15:50:13 (none) daemon.err udevd[2633]: SYSFS{}= will be removed in a future udev version, please use ATTR{}= to match the event device, or ATTRS{}= to match a parent device, in /lib/udev/rules.d/60-bluetooth.rules:11
Jun 27 15:50:13 (none) daemon.err udevd[2633]: BUS= will be removed in a future udev version, please use SUBSYSTEM= to match the event device, or SUBSYSTEMS= to match a parent device, in /lib/udev/rules.d/60-bluetooth.rules:14
Jun 27 15:50:13 (none) daemon.err udevd[2633]: SYSFS{}= will be removed in a future udev version, please use ATTR{}= to match the event device, or ATTRS{}= to match a parent device, in /lib/udev/rules.d/60-bluetooth.rules:14
Jun 27 15:50:13 (none) daemon.err udevd[2633]: BUS= will be removed in a future udev version, please use SUBSYSTEM= to match the event device, or SUBSYSTEMS= to match a parent device, in /lib/udev/rules.d/60-bluetooth.rules:17
Jun 27 15:50:13 (none) daemon.err udevd[2633]: SYSFS{}= will be removed in a future udev version, please use ATTR{}= to match the event device, or ATTRS{}= to match a parent device, in /lib/udev/rules.d/60-bluetooth.rules:17
Jun 27 15:50:13 (none) daemon.err udevd[2633]: BUS= will be removed in a future udev version, please use SUBSYSTEM= to match the event device, or SUBSYSTEMS= to match a parent device, in /lib/udev/rules.d/60-bluetooth.rules:20
Jun 27 15:50:13 (none) daemon.err udevd[2633]: SYSFS{}= will be removed in a future udev version, please use ATTR{}= to match the event device, or ATTRS{}= to match a parent device, in /lib/udev/rules.d/60-bluetooth.rules:20
Jun 27 15:50:13 (none) daemon.err udevd[2633]: BUS= will be removed in a future udev version, please use SUBSYSTEM= to match the event device, or SUBSYSTEMS= to match a parent device, in /lib/udev/rules.d/60-bluetooth.rules:23
Jun 27 15:50:13 (none) daemon.err udevd[2633]: SYSFS{}= will be removed in a future udev version, please use ATTR{}= to match the event device, or ATTRS{}= to match a parent device, in /lib/udev/rules.d/60-bluetooth.rules:23
Jun 27 15:50:13 (none) daemon.err udevd[2633]: BUS= will be removed in a future udev version, please use SUBSYSTEM= to match the event device, or SUBSYSTEMS= to match a parent device, in /lib/udev/rules.d/60-bluetooth.rules:26
Jun 27 15:50:13 (none) daemon.err udevd[2633]: SYSFS{}= will be removed in a future udev version, please use ATTR{}= to match the event device, or ATTRS{}= to match a parent device, in /lib/udev/rules.d/60-bluetooth.rules:26
Jun 27 15:50:13 (none) daemon.err udevd[2633]: BUS= will be removed in a future udev version, please use SUBSYSTEM= to match the event device, or SUBSYSTEMS= to match a parent device, in /lib/udev/rules.d/60-bluetooth.rules:29
Jun 27 15:50:13 (none) daemon.err udevd[2633]: SYSFS{}= will be removed in a future udev version, please use ATTR{}= to match the event device, or ATTRS{}= to match a parent device, in /lib/udev/rules.d/60-bluetooth.rules:29
Jun 27 15:50:13 (none) daemon.err udevd[2633]: BUS= will be removed in a future udev version, please use SUBSYSTEM= to match the event device, or SUBSYSTEMS= to match a parent device, in /lib/udev/rules.d/60-bluetooth.rules:32
Jun 27 15:50:13 (none) daemon.err udevd[2633]: SYSFS{}= will be removed in a future udev version, please use ATTR{}= to match the event device, or ATTRS{}= to match a parent device, in /lib/udev/rules.d/60-bluetooth.rules:32
Jun 27 15:50:13 (none) daemon.err udevd[2633]: BUS= will be removed in a future udev version, please use SUBSYSTEM= to match the event device, or SUBSYSTEMS= to match a parent device, in /lib/udev/rules.d/60-bluetooth.rules:35
Jun 27 15:50:13 (none) daemon.err udevd[2633]: SYSFS{}= will be removed in a future udev version, please use ATTR{}= to match the event device, or ATTRS{}= to match a parent device, in /lib/udev/rules.d/60-bluetooth.rules:35
Jun 27 15:50:14 (none) user.info kernel: [   75.019175] fuse init (API version 7.16)
Jun 27 15:50:15 (none) user.info gpm[3500]: *** info [startup.c(95)]: 
Jun 27 15:50:15 (none) user.info gpm[3500]: Started gpm successfully. Entered daemon mode.
Jun 27 15:50:15 (none) user.info kernel: [   75.289011] device-mapper: uevent: version 1.0.3
Jun 27 15:50:15 (none) user.info kernel: [   75.289311] device-mapper: ioctl: 4.19.1-ioctl (2011-01-07) initialised: dm-devel@redhat.com
Jun 27 15:50:15 (none) user.info kernel: [   75.636347] Installing knfsd (copyright (C) 1996 okir@monad.swb.de).
Jun 27 15:50:15 (none) daemon.notice rpc.statd[3510]: Version 1.1.2 Starting
Jun 27 15:50:15 (none) daemon.notice rpc.statd[3510]: statd running as root. chown /var/lib/nfs/sm to choose different user
Jun 27 15:50:15 (none) daemon.err exportfs[3512]: malformed entry in rmtab file
Jun 27 15:50:15 (none) user.info kernel: [   75.861943] NET: Registered protocol family 10
Jun 27 15:50:15 (none) user.warn kernel: [   75.862309] svc: failed to register lockdv1 RPC service (errno 97).
Jun 27 15:50:15 (none) user.warn kernel: [   75.862339] NFSD: Using /var/lib/nfs/v4recovery as the NFSv4 state recovery directory
Jun 27 15:50:15 (none) user.warn kernel: [   75.862347] NFSD: unable to find recovery directory /var/lib/nfs/v4recovery
Jun 27 15:50:15 (none) user.info kernel: [   75.862349] NFSD: starting 90-second grace period
Jun 27 15:50:16 (none) daemon.info smartd[3553]: smartd 5.39.1 2010-01-28 r3054 [i486-slackware-linux-gnu] (local build) Copyright (C) 2002-10 by Bruce Allen, http://smartmontools.sourceforge.net
Jun 27 15:50:16 (none) daemon.info smartd[3553]: Opened configuration file /usr/etc/smartd.conf
Jun 27 15:50:16 (none) daemon.info smartd[3553]: Drive: DEVICESCAN, implied '-a' Directive on line 23 of file /usr/etc/smartd.conf
Jun 27 15:50:16 (none) daemon.info smartd[3553]: Configuration file /usr/etc/smartd.conf was parsed, found DEVICESCAN, scanning devices
Jun 27 15:50:16 (none) daemon.info smartd[3553]: Device: /dev/sda, type changed from 'scsi' to 'sat'
Jun 27 15:50:16 (none) daemon.info smartd[3553]: Device: /dev/sda [SAT], opened
Jun 27 15:50:16 (none) daemon.info smartd[3553]: Device: /dev/sda [SAT], not found in smartd database.
Jun 27 15:50:16 (none) daemon.info smartd[3553]: Device: /dev/sda [SAT], is SMART capable. Adding to "monitor" list.
Jun 27 15:50:16 (none) daemon.info smartd[3553]: Monitoring 1 ATA and 0 SCSI devices
Jun 27 15:50:16 (none) daemon.info smartd[3555]: smartd has fork()ed into background mode. New PID=3555.
Jun 27 15:50:16 (none) daemon.info acpid: starting up with proc fs
Jun 27 15:50:17 (none) daemon.info acpid: skipping conf file /etc/acpi/events/.
Jun 27 15:50:17 (none) daemon.info acpid: skipping conf file /etc/acpi/events/..
Jun 27 15:50:17 (none) daemon.info acpid: 1 rule loaded
Jun 27 15:50:17 (none) daemon.info acpid: waiting for events: event logging is off
Jun 27 15:50:19 (none) daemon.notice acpid: client connected from 3603[82:82]
Jun 27 15:50:19 (none) daemon.info acpid: 1 client rule loaded
Jun 27 15:50:19 (none) user.warn kernel: [   79.811246] dmeventd (3606): /proc/3606/oom_adj is deprecated, please use /proc/3606/oom_score_adj instead.
Jun 27 15:50:19 (none) daemon.notice dmeventd[3606]: dmeventd ready for processing.
Jun 27 15:50:23 (none) daemon.info hcid[3966]: Bluetooth HCI daemon
Jun 27 15:50:23 (none) daemon.err hcid[3966]: Parsing /etc/bluetooth/main.conf failed: No such file or directory
Jun 27 15:50:23 (none) daemon.info hcid[3966]: Starting SDP server
Jun 27 15:50:23 (none) user.info kernel: [   83.987938] Bluetooth: L2CAP ver 2.15
Jun 27 15:50:23 (none) user.info kernel: [   83.987946] Bluetooth: L2CAP socket layer initialized
Jun 27 15:50:23 (none) user.info kernel: [   84.001885] Bluetooth: RFCOMM TTY layer initialized
Jun 27 15:50:23 (none) user.info kernel: [   84.001890] Bluetooth: RFCOMM socket layer initialized
Jun 27 15:50:23 (none) user.info kernel: [   84.001892] Bluetooth: RFCOMM ver 1.11
Jun 27 15:50:24 (none) daemon.info hcid[3966]: Unix socket created: 11
Jun 27 15:50:24 (none) daemon.info hcid[3966]: Registered manager path:/org/bluez/audio
Jun 27 15:50:24 (none) daemon.info hcid[3966]: Registered input manager path:/org/bluez/input
Jun 27 15:50:24 (none) user.info kernel: [   84.445756] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
Jun 27 15:50:24 (none) user.info kernel: [   84.445759] Bluetooth: BNEP filters: protocol multicast
Jun 27 15:50:24 (none) daemon.info hcid[3966]: bridge pan0 created
Jun 27 15:50:24 (none) daemon.info hcid[3966]: Registered manager path:/org/bluez/network
Jun 27 15:50:24 (none) user.notice kernel: [   84.497935] Bridge firewalling registered
Jun 27 15:50:24 (none) daemon.info hcid[3966]: Registered manager path:/org/bluez/serial
Jun 27 15:50:24 (none) daemon.info hcid[3966]: HCI dev 0 registered
Jun 27 15:50:24 (none) daemon.info hcid[3966]: HCI dev 1 registered
Jun 27 15:50:24 (none) daemon.info hcid[3966]: HCI dev 0 up
Jun 27 15:50:24 (none) daemon.info hcid[3966]: Device hci0 has been added
Jun 27 15:50:24 (none) daemon.info hcid[3966]: Starting security manager 0
Jun 27 15:50:24 (none) daemon.info hcid[3966]: Device hci0 has been activated
Jun 27 15:50:24 (none) daemon.info hcid[3966]: HCI dev 1 up
Jun 27 15:50:24 (none) daemon.info hcid[3966]: Device hci1 has been added
Jun 27 15:50:24 (none) daemon.info hcid[3966]: Starting security manager 1
Jun 27 15:50:24 (none) daemon.info hcid[3966]: Device hci1 has been activated
Jun 27 15:50:26 (none) daemon.info dhclient: isc-dhclient-4.2.0
Jun 27 15:50:26 (none) daemon.info dhclient: isc-dhclient-4.2.0
Jun 27 15:50:26 (none) user.info kernel: [   86.766117] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Jun 27 15:50:28 (none) auth.info sshd[4020]: Server listening on 0.0.0.0 port 22.
Jun 27 15:50:28 (none) auth.info sshd[4020]: Server listening on :: port 22.
Jun 27 15:50:29 (none) daemon.notice ntpd[4029]: ntpd 4.2.6p3@1.2290-o Wed Jan 26 04:19:40 UTC 2011 (1)
Jun 27 15:50:29 (none) daemon.notice ntpd[4030]: proto: precision = 0.340 usec
Jun 27 15:50:29 (none) daemon.debug ntpd[4030]: ntp_io: estimated max descriptors: 1024, initial socket boundary: 16
Jun 27 15:50:29 (none) daemon.info ntpd[4030]: Listen and drop on 0 v4wildcard 0.0.0.0 UDP 123
Jun 27 15:50:29 (none) daemon.info ntpd[4030]: Listen and drop on 1 v6wildcard :: UDP 123
Jun 27 15:50:29 (none) daemon.info ntpd[4030]: Listen normally on 2 lo 127.0.0.1 UDP 123
Jun 27 15:50:29 (none) daemon.info ntpd[4030]: Listen normally on 3 lo ::1 UDP 123
Jun 27 15:50:29 (none) daemon.info ntpd[4030]: peers refreshed
Jun 27 15:50:29 (none) daemon.notice ntpd[4031]: ntpd 4.2.6p3@1.2290-o Wed Jan 26 04:19:40 UTC 2011 (1)
Jun 27 15:50:29 (none) daemon.notice ntpd[4032]: proto: precision = 0.451 usec
Jun 27 15:50:29 (none) daemon.debug ntpd[4032]: ntp_io: estimated max descriptors: 1024, initial socket boundary: 16
Jun 27 15:50:29 (none) daemon.err ntpd[4032]: unable to bind to wildcard address 0.0.0.0 - another process may be running - EXITING
Jun 27 15:50:32 (none) user.info kernel: [   92.117483] r8169 0000:05:00.0: eth0: link down
Jun 27 15:50:32 (none) user.info kernel: [   92.117614] ADDRCONF(NETDEV_UP): eth0: link is not ready
Jun 27 15:50:32 (none) daemon.info init: starting pid 4063, tty '/dev/tty1': '/sbin/mingetty --autologin root tty1'
Jun 27 15:50:32 (none) authpriv.notice login[4063]: ROOT LOGIN  on '/dev/tty1'
Jun 27 15:50:33 (none) daemon.notice acpid: client connected from 4108[0:0]
Jun 27 15:50:33 (none) daemon.info acpid: 1 client rule loaded
Jun 27 15:50:53 (none) daemon.notice ntfs-3g[4277]: Version 2011.4.12 integrated FUSE 27
Jun 27 15:50:53 (none) daemon.notice ntfs-3g[4277]: Mounted /dev/sdb1 (Read-Write, label "External", NTFS 3.1)
Jun 27 15:50:53 (none) daemon.notice ntfs-3g[4277]: Cmdline options: rw
Jun 27 15:50:53 (none) daemon.notice ntfs-3g[4277]: Mount options: rw,allow_other,nonempty,atime,fsname=/dev/sdb1,blkdev,blksize=4096
Jun 27 15:50:53 (none) daemon.notice ntfs-3g[4277]: Ownership and permissions disabled, configuration type 1
Jun 27 15:51:09 (none) daemon.notice ntfs-3g[4331]: Version 2011.4.12 integrated FUSE 27
Jun 27 15:51:09 (none) daemon.notice ntfs-3g[4331]: Mounted /dev/sda5 (Read-Write, label "Common", NTFS 3.1)
Jun 27 15:51:09 (none) daemon.notice ntfs-3g[4331]: Cmdline options: rw
Jun 27 15:51:09 (none) daemon.notice ntfs-3g[4331]: Mount options: rw,allow_other,nonempty,atime,fsname=/dev/sda5,blkdev,blksize=4096
Jun 27 15:51:09 (none) daemon.notice ntfs-3g[4331]: Ownership and permissions disabled, configuration type 1

```

I noticed I get the same error here as I do with ubuntu natty to do with no superspeed endpoint, but it doesn't seem to matter:

```
Jun 27 15:49:02 (none) user.info kernel: [    2.978743] xhci_hcd 0000:04:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
Jun 27 15:49:02 (none) user.debug kernel: [    2.978771] xhci_hcd 0000:04:00.0: setting latency timer to 64
Jun 27 15:49:02 (none) user.info kernel: [    2.978781] xhci_hcd 0000:04:00.0: xHCI Host Controller
Jun 27 15:49:02 (none) user.info kernel: [    2.978856] xhci_hcd 0000:04:00.0: new USB bus registered, assigned bus number 3
Jun 27 15:49:02 (none) user.info kernel: [    3.089458] xhci_hcd 0000:04:00.0: irq 18, io mem 0xc5400000
Jun 27 15:49:02 (none) user.debug kernel: [    3.089541] xhci_hcd 0000:04:00.0: irq 42 for MSI/MSI-X
Jun 27 15:49:02 (none) user.debug kernel: [    3.089544] xhci_hcd 0000:04:00.0: irq 43 for MSI/MSI-X
Jun 27 15:49:02 (none) user.debug kernel: [    3.089546] xhci_hcd 0000:04:00.0: irq 44 for MSI/MSI-X
Jun 27 15:49:02 (none) user.debug kernel: [    3.089548] xhci_hcd 0000:04:00.0: irq 45 for MSI/MSI-X
Jun 27 15:49:02 (none) user.debug kernel: [    3.089550] xhci_hcd 0000:04:00.0: irq 46 for MSI/MSI-X
Jun 27 15:49:02 (none) user.warn kernel: [    3.092857] usb usb3: No SuperSpeed endpoint companion for config 1  interface 0 altsetting 0 ep 129: using minimum values
Jun 27 15:49:02 (none) user.info kernel: [    3.092864] usb usb3: New USB device found, idVendor=1d6b, idProduct=0003
Jun 27 15:49:02 (none) user.info kernel: [    3.092866] usb usb3: New USB device strings: Mfr=3, Product=2, SerialNumber=1
Jun 27 15:49:02 (none) user.info kernel: [    3.092867] usb usb3: Product: xHCI Host Controller
Jun 27 15:49:02 (none) user.info kernel: [    3.092869] usb usb3: Manufacturer: Linux 2.6.38.4-pmagic xhci_hcd
Jun 27 15:49:02 (none) user.info kernel: [    3.092870] usb usb3: SerialNumber: 0000:04:00.0
Jun 27 15:49:02 (none) user.debug kernel: [    3.092961] xHCI xhci_add_endpoint called for root hub
Jun 27 15:49:02 (none) user.debug kernel: [    3.092963] xHCI xhci_check_bandwidth called for root hub
```


And this is the dmesg output for ubuntu natty 64bit, 2.6.38-8-generic, when the drive doesn't work:

```
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.38-8-generic (buildd@allspice) (gcc version 4.5.2 (Ubuntu/Linaro 4.5.2-8ubuntu3) ) #42-Ubuntu SMP Mon Apr 11 03:31:24 UTC 2011 (Ubuntu 2.6.38-8.42-generic 2.6.38.2)
[    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-2.6.38-8-generic root=UUID=28f9b476-4084-4a9a-a382-00697089f8ed ro quiet splash vt.handoff=7
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 0000000000094400 (usable)
[    0.000000]  BIOS-e820: 0000000000094400 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000009ae3f000 (usable)
[    0.000000]  BIOS-e820: 000000009ae3f000 - 000000009aebf000 (reserved)
[    0.000000]  BIOS-e820: 000000009aebf000 - 000000009afbf000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000009afbf000 - 000000009afff000 (ACPI data)
[    0.000000]  BIOS-e820: 000000009afff000 - 000000009b000000 (usable)
[    0.000000]  BIOS-e820: 000000009b000000 - 000000009fa00000 (reserved)
[    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000feb00000 - 00000000feb04000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed10000 - 00000000fed1a000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed1c000 - 00000000fed20000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000ffd80000 - 0000000100000000 (reserved)
[    0.000000]  BIOS-e820: 0000000100000000 - 000000015fe00000 (usable)
[    0.000000] NX (Execute Disable) protection: active
[    0.000000] DMI 2.6 present.
[    0.000000] DMI: Sony Corporation VPCSB1C5E/VAIO, BIOS R1031H4 04/25/2011
[    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
[    0.000000] e820 remove range: 00000000000a0000 - 0000000000100000 (usable)
[    0.000000] No AGP bridge found
[    0.000000] last_pfn = 0x15fe00 max_arch_pfn = 0x400000000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000 mask F80000000 write-back
[    0.000000]   1 base 080000000 mask FE0000000 write-back
[    0.000000]   2 base 09B000000 mask FFF000000 uncachable
[    0.000000]   3 base 09C000000 mask FFC000000 uncachable
[    0.000000]   4 base 0FFC00000 mask FFFC00000 write-protect
[    0.000000]   5 base 100000000 mask FC0000000 write-back
[    0.000000]   6 base 140000000 mask FF0000000 write-back
[    0.000000]   7 base 150000000 mask FF0000000 write-back
[    0.000000]   8 base 15FE00000 mask FFFE00000 uncachable
[    0.000000]   9 disabled
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] last_pfn = 0x9b000 max_arch_pfn = 0x400000000
[    0.000000] found SMP MP-table at [ffff8800000fe1b0] fe1b0
[    0.000000] initial memory mapped : 0 - 20000000
[    0.000000] init_memory_mapping: 0000000000000000-000000009b000000
[    0.000000]  0000000000 - 009b000000 page 2M
[    0.000000] kernel direct mapping tables up to 9b000000 @ 1fffc000-20000000
[    0.000000] init_memory_mapping: 0000000100000000-000000015fe00000
[    0.000000]  0100000000 - 015fe00000 page 2M
[    0.000000] kernel direct mapping tables up to 15fe00000 @ 9ae38000-9ae3f000
[    0.000000] RAMDISK: 366e2000 - 37369000
[    0.000000] ACPI: RSDP 00000000000fe020 00024 (v02   Sony)
[    0.000000] ACPI: XSDT 000000009affe120 000A4 (v01   Sony     VAIO 20110425      01000013)
[    0.000000] ACPI: FACP 000000009affb000 000F4 (v04   Sony     VAIO 20110425 ACPI 00040000)
[    0.000000] ACPI: DSDT 000000009afef000 0819C (v01   Sony     VAIO 20110425 ACPI 00040000)
[    0.000000] ACPI: FACS 000000009af6e000 00040
[    0.000000] ACPI: TCPA 000000009affd000 00032 (v02   Sony     VAIO 20110425 ACPI 00040000)
[    0.000000] ACPI: ASF! 000000009affc000 000A5 (v32   Sony     VAIO 20110425 ACPI 00040000)
[    0.000000] ACPI: HPET 000000009affa000 00038 (v01   Sony     VAIO 20110425 ACPI 00040000)
[    0.000000] ACPI: APIC 000000009aff9000 0008C (v02   Sony     VAIO 20110425 ACPI 00040000)
[    0.000000] ACPI: MCFG 000000009aff8000 0003C (v01   Sony     VAIO 20110425 ACPI 00040000)
[    0.000000] ACPI: SLIC 000000009afee000 00176 (v01   Sony     VAIO 20110425 ACPI 00040000)
[    0.000000] ACPI: WDAT 000000009afed000 00224 (v01   Sony     VAIO 20110425 ACPI 00040000)
[    0.000000] ACPI: SSDT 000000009afec000 00CA6 (v01   Sony     VAIO 20110425 ACPI 00040000)
[    0.000000] ACPI: BOOT 000000009afea000 00028 (v01   Sony     VAIO 20110425 ACPI 00040000)
[    0.000000] ACPI: SSDT 000000009afe8000 0022B (v01   Sony     VAIO 20110425 ACPI 00040000)
[    0.000000] ACPI: ASPT 000000009afe5000 00034 (v07   Sony     VAIO 20110425 ACPI 00040000)
[    0.000000] ACPI: SSDT 000000009afe4000 007C2 (v01   Sony     VAIO 20110425 ACPI 00040000)
[    0.000000] ACPI: SSDT 000000009afe3000 00996 (v01   Sony     VAIO 20110425 ACPI 00040000)
[    0.000000] ACPI: SSDT 000000009afe1000 011B9 (v01   Sony     VAIO 20110425 ACPI 00040000)
[    0.000000] ACPI: SSDT 000000009afe0000 002DD (v01   Sony     VAIO 20110425 ACPI 00040000)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] No NUMA configuration found
[    0.000000] Faking a node at 0000000000000000-000000015fe00000
[    0.000000] Initmem setup node 0 0000000000000000-000000015fe00000
[    0.000000]   NODE_DATA [000000015fdfb000 - 000000015fdfffff]
[    0.000000]  [ffffea0000000000-ffffea0004dfffff] PMD -> [ffff88015bc00000-ffff88015f5fffff] on node 0
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000010 -> 0x00001000
[    0.000000]   DMA32    0x00001000 -> 0x00100000
[    0.000000]   Normal   0x00100000 -> 0x0015fe00
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[4] active PFN ranges
[    0.000000]     0: 0x00000010 -> 0x00000094
[    0.000000]     0: 0x00000100 -> 0x0009ae3f
[    0.000000]     0: 0x0009afff -> 0x0009b000
[    0.000000]     0: 0x00100000 -> 0x0015fe00
[    0.000000] On node 0 totalpages: 1027012
[    0.000000]   DMA zone: 56 pages used for memmap
[    0.000000]   DMA zone: 6 pages reserved
[    0.000000]   DMA zone: 3910 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 14280 pages used for memmap
[    0.000000]   DMA32 zone: 616056 pages, LIFO batch:31
[    0.000000]   Normal zone: 5369 pages used for memmap
[    0.000000]   Normal zone: 387335 pages, LIFO batch:31
[    0.000000] ACPI: PM-Timer IO Port: 0x408
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x02] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x03] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x05] lapic_id[0x00] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x06] lapic_id[0x00] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x07] lapic_id[0x00] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x08] lapic_id[0x00] disabled)
[    0.000000] ACPI: IOAPIC (id[0x00] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 0, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000
[    0.000000] SMP: Allowing 8 CPUs, 4 hotplug CPUs
[    0.000000] nr_irqs_gsi: 40
[    0.000000] PM: Registered nosave memory: 0000000000094000 - 0000000000095000
[    0.000000] PM: Registered nosave memory: 0000000000095000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
[    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
[    0.000000] PM: Registered nosave memory: 000000009ae3f000 - 000000009aebf000
[    0.000000] PM: Registered nosave memory: 000000009aebf000 - 000000009afbf000
[    0.000000] PM: Registered nosave memory: 000000009afbf000 - 000000009afff000
[    0.000000] PM: Registered nosave memory: 000000009b000000 - 000000009fa00000
[    0.000000] PM: Registered nosave memory: 000000009fa00000 - 00000000e0000000
[    0.000000] PM: Registered nosave memory: 00000000e0000000 - 00000000f0000000
[    0.000000] PM: Registered nosave memory: 00000000f0000000 - 00000000feb00000
[    0.000000] PM: Registered nosave memory: 00000000feb00000 - 00000000feb04000
[    0.000000] PM: Registered nosave memory: 00000000feb04000 - 00000000fec00000
[    0.000000] PM: Registered nosave memory: 00000000fec00000 - 00000000fec01000
[    0.000000] PM: Registered nosave memory: 00000000fec01000 - 00000000fed10000
[    0.000000] PM: Registered nosave memory: 00000000fed10000 - 00000000fed1a000
[    0.000000] PM: Registered nosave memory: 00000000fed1a000 - 00000000fed1c000
[    0.000000] PM: Registered nosave memory: 00000000fed1c000 - 00000000fed20000
[    0.000000] PM: Registered nosave memory: 00000000fed20000 - 00000000fee00000
[    0.000000] PM: Registered nosave memory: 00000000fee00000 - 00000000fee01000
[    0.000000] PM: Registered nosave memory: 00000000fee01000 - 00000000ffd80000
[    0.000000] PM: Registered nosave memory: 00000000ffd80000 - 0000000100000000
[    0.000000] Allocating PCI resources starting at 9fa00000 (gap: 9fa00000:40600000)
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] setup_percpu: NR_CPUS:256 nr_cpumask_bits:256 nr_cpu_ids:8 nr_node_ids:1
[    0.000000] PERCPU: Embedded 28 pages/cpu @ffff88009ac00000 s84416 r8192 d22080 u262144
[    0.000000] pcpu-alloc: s84416 r8192 d22080 u262144 alloc=1*2097152
[    0.000000] pcpu-alloc: [0] 0 1 2 3 4 5 6 7 
[    0.000000] Built 1 zonelists in Node order, mobility grouping on.  Total pages: 1007301
[    0.000000] Policy zone: Normal
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.38-8-generic root=UUID=28f9b476-4084-4a9a-a382-00697089f8ed ro quiet splash vt.handoff=7
[    0.000000] PID hash table entries: 4096 (order: 3, 32768 bytes)
[    0.000000] xsave/xrstor: enabled xstate_bv 0x7, cntxt size 0x340
[    0.000000] Checking aperture...
[    0.000000] No AGP bridge found
[    0.000000] Calgary: detecting Calgary via BIOS EBDA area
[    0.000000] Calgary: Unable to locate Rio Grande table in EBDA - bailing!
[    0.000000] Memory: 3955404k/5765120k available (5940k kernel code, 1657072k absent, 152644k reserved, 5017k data, 956k init)
[    0.000000] SLUB: Genslabs=15, HWalign=64, Order=0-3, MinObjects=0, CPUs=8, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000] 	RCU dyntick-idle grace-period acceleration is enabled.
[    0.000000] 	RCU-based detection of stalled CPUs is disabled.
[    0.000000] NR_IRQS:16640 nr_irqs:744 16
[    0.000000] Extended CMOS year: 2000
[    0.000000] vt handoff: transparent VT on vt#7
[    0.000000] Console: colour dummy device 80x25
[    0.000000] console [tty0] enabled
[    0.000000] allocated 41943040 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] hpet clockevent registered
[    0.000000] Fast TSC calibration using PIT
[    0.010000] Detected 2494.732 MHz processor.
[    0.000002] Calibrating delay loop (skipped), value calculated using timer frequency.. 4989.46 BogoMIPS (lpj=24947320)
[    0.000006] pid_max: default: 32768 minimum: 301
[    0.000026] Security Framework initialized
[    0.000037] AppArmor: AppArmor initialized
[    0.000038] Yama: becoming mindful.
[    0.000410] Dentry cache hash table entries: 524288 (order: 10, 4194304 bytes)
[    0.001473] Inode-cache hash table entries: 262144 (order: 9, 2097152 bytes)
[    0.001918] Mount-cache hash table entries: 256
[    0.002015] Initializing cgroup subsys ns
[    0.002018] ns_cgroup deprecated: consider using the 'clone_children' flag without the ns_cgroup.
[    0.002020] Initializing cgroup subsys cpuacct
[    0.002023] Initializing cgroup subsys memory
[    0.002028] Initializing cgroup subsys devices
[    0.002030] Initializing cgroup subsys freezer
[    0.002032] Initializing cgroup subsys net_cls
[    0.002033] Initializing cgroup subsys blkio
[    0.002059] CPU: Physical Processor ID: 0
[    0.002060] CPU: Processor Core ID: 0
[    0.002065] mce: CPU supports 7 MCE banks
[    0.002075] CPU0: Thermal monitoring enabled (TM1)
[    0.002082] using mwait in idle threads.
[    0.004355] ACPI: Core revision 20110112
[    0.021782] ftrace: allocating 24314 entries in 96 pages
[    0.030831] Not enabling x2apic, Intr-remapping init failed.
[    0.030834] Setting APIC routing to flat
[    0.031190] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.131084] CPU0: Intel(R) Core(TM) i5-2520M CPU @ 2.50GHz stepping 07
[    0.245485] Performance Events: PEBS fmt1+, generic architected perfmon, Intel PMU driver.
[    0.245491] ... version:                3
[    0.245492] ... bit width:              48
[    0.245493] ... generic registers:      4
[    0.245494] ... value mask:             0000ffffffffffff
[    0.245495] ... max period:             000000007fffffff
[    0.245496] ... fixed-purpose events:   3
[    0.245497] ... event mask:             000000070000000f
[    0.245877] Booting Node   0, Processors  #1 #2 #3
[    0.784839] Brought up 4 CPUs
[    0.784842] Total of 4 processors activated (19955.47 BogoMIPS).
[    0.786735] devtmpfs: initialized
[    0.787526] print_constraints: dummy: 
[    0.787558] Time: 16:03:22  Date: 06/27/11
[    0.787584] NET: Registered protocol family 16
[    0.787661] Trying to unpack rootfs image as initramfs...
[    0.787665] ACPI: bus type pci registered
[    0.787725] PCI: MMCONFIG for domain 0000 [bus 00-ff] at [mem 0xe0000000-0xefffffff] (base 0xe0000000)
[    0.787727] PCI: MMCONFIG at [mem 0xe0000000-0xefffffff] reserved in E820
[    0.825776] PCI: Using configuration type 1 for base access
[    0.826399] bio: create slab <bio-0> at 0
[    0.827937] ACPI: EC: Look up EC in DSDT
[    0.829314] ACPI: Executed 1 blocks of module-level executable AML code
[    0.964750] [Firmware Bug]: ACPI: BIOS _OSI(Linux) query ignored
[    0.971640] ACPI: SSDT 000000009ae70718 0067C (v01  PmRef  Cpu0Cst 00003001 INTL 20100121)
[    0.972007] ACPI: Dynamic OEM Table Load:
[    0.972010] ACPI: SSDT           (null) 0067C (v01  PmRef  Cpu0Cst 00003001 INTL 20100121)
[    0.987007] Freeing initrd memory: 12828k freed
[    0.995015] ACPI: SSDT 000000009ae71a98 00303 (v01  PmRef    ApIst 00003000 INTL 20100121)
[    0.995417] ACPI: Dynamic OEM Table Load:
[    0.995419] ACPI: SSDT           (null) 00303 (v01  PmRef    ApIst 00003000 INTL 20100121)
[    1.034803] ACPI: SSDT 000000009ae6fd98 00119 (v01  PmRef    ApCst 00003000 INTL 20100121)
[    1.035160] ACPI: Dynamic OEM Table Load:
[    1.035162] ACPI: SSDT           (null) 00119 (v01  PmRef    ApCst 00003000 INTL 20100121)
[    1.494049] ACPI: Interpreter enabled
[    1.494052] ACPI: (supports S0 S3 S4 S5)
[    1.494074] ACPI: Using IOAPIC for interrupt routing
[    1.498164] ACPI: EC: GPE = 0x17, I/O: command/status = 0x66, data = 0x62
[    1.498307] ACPI: No dock devices found.
[    1.498309] HEST: Table not found.
[    1.498311] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
[    1.498596] \_SB_.PCI0:_OSC invalid UUID
[    1.498597] _OSC request data:1 8 1f 
[    1.498600] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-fe])
[    1.499086] pci_root PNP0A08:00: host bridge window [io  0x0000-0x0cf7]
[    1.499088] pci_root PNP0A08:00: host bridge window [io  0x0d00-0xffff]
[    1.499090] pci_root PNP0A08:00: host bridge window [mem 0x000a0000-0x000bffff]
[    1.499093] pci_root PNP0A08:00: host bridge window [mem 0x9fa00000-0xfeafffff]
[    1.499102] pci 0000:00:00.0: [8086:0104] type 0 class 0x000600
[    1.499134] pci 0000:00:01.0: [8086:0101] type 1 class 0x000604
[    1.499157] pci 0000:00:01.0: PME# supported from D0 D3hot D3cold
[    1.499159] pci 0000:00:01.0: PME# disabled
[    1.499183] pci 0000:00:02.0: [8086:0126] type 0 class 0x000300
[    1.499192] pci 0000:00:02.0: reg 10: [mem 0xc0000000-0xc03fffff 64bit]
[    1.499198] pci 0000:00:02.0: reg 18: [mem 0xb0000000-0xbfffffff 64bit pref]
[    1.499202] pci 0000:00:02.0: reg 20: [io  0x8000-0x803f]
[    1.499269] pci 0000:00:16.0: [8086:1c3a] type 0 class 0x000780
[    1.499304] pci 0000:00:16.0: reg 10: [mem 0xc9404000-0xc940400f 64bit]
[    1.499395] pci 0000:00:16.0: PME# supported from D0 D3hot D3cold
[    1.499400] pci 0000:00:16.0: PME# disabled
[    1.499449] pci 0000:00:1a.0: [8086:1c2d] type 0 class 0x000c03
[    1.499898] pci 0000:00:1a.0: reg 10: [mem 0xc940a000-0xc940a3ff]
[    1.502449] pci 0000:00:1a.0: PME# supported from D0 D3hot D3cold
[    1.502454] pci 0000:00:1a.0: PME# disabled
[    1.502489] pci 0000:00:1b.0: [8086:1c20] type 0 class 0x000403
[    1.502514] pci 0000:00:1b.0: reg 10: [mem 0xc9400000-0xc9403fff 64bit]
[    1.502609] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    1.502614] pci 0000:00:1b.0: PME# disabled
[    1.502644] pci 0000:00:1c.0: [8086:1c10] type 1 class 0x000604
[    1.502743] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    1.502748] pci 0000:00:1c.0: PME# disabled
[    1.502781] pci 0000:00:1c.1: [8086:1c12] type 1 class 0x000604
[    1.502880] pci 0000:00:1c.1: PME# supported from D0 D3hot D3cold
[    1.502885] pci 0000:00:1c.1: PME# disabled
[    1.502917] pci 0000:00:1c.2: [8086:1c14] type 1 class 0x000604
[    1.503016] pci 0000:00:1c.2: PME# supported from D0 D3hot D3cold
[    1.503021] pci 0000:00:1c.2: PME# disabled
[    1.503053] pci 0000:00:1c.3: [8086:1c16] type 1 class 0x000604
[    1.503152] pci 0000:00:1c.3: PME# supported from D0 D3hot D3cold
[    1.503157] pci 0000:00:1c.3: PME# disabled
[    1.503205] pci 0000:00:1d.0: [8086:1c26] type 0 class 0x000c03
[    1.503642] pci 0000:00:1d.0: reg 10: [mem 0xc9409000-0xc94093ff]
[    1.506199] pci 0000:00:1d.0: PME# supported from D0 D3hot D3cold
[    1.506204] pci 0000:00:1d.0: PME# disabled
[    1.506235] pci 0000:00:1f.0: [8086:1c4b] type 0 class 0x000601
[    1.506396] pci 0000:00:1f.2: [8086:282a] type 0 class 0x000104
[    1.506428] pci 0000:00:1f.2: reg 10: [io  0x8088-0x808f]
[    1.506442] pci 0000:00:1f.2: reg 14: [io  0x809c-0x809f]
[    1.506455] pci 0000:00:1f.2: reg 18: [io  0x8080-0x8087]
[    1.506469] pci 0000:00:1f.2: reg 1c: [io  0x8098-0x809b]
[    1.506482] pci 0000:00:1f.2: reg 20: [io  0x8060-0x807f]
[    1.506495] pci 0000:00:1f.2: reg 24: [mem 0xc9408000-0xc94087ff]
[    1.506554] pci 0000:00:1f.2: PME# supported from D3hot
[    1.506559] pci 0000:00:1f.2: PME# disabled
[    1.506585] pci 0000:00:1f.3: [8086:1c22] type 0 class 0x000c05
[    1.506611] pci 0000:00:1f.3: reg 10: [mem 0xc9406000-0xc94060ff 64bit]
[    1.506647] pci 0000:00:1f.3: reg 20: [io  0x8040-0x805f]
[    1.506718] pci 0000:01:00.0: [1002:6741] type 0 class 0x000300
[    1.506735] pci 0000:01:00.0: reg 10: [mem 0xa0000000-0xafffffff 64bit pref]
[    1.506748] pci 0000:01:00.0: reg 18: [mem 0xc8400000-0xc841ffff 64bit]
[    1.506756] pci 0000:01:00.0: reg 20: [io  0x7000-0x70ff]
[    1.506772] pci 0000:01:00.0: reg 30: [mem 0xfffe0000-0xffffffff pref]
[    1.506794] pci 0000:01:00.0: supports D1 D2
[    1.523849] pci 0000:00:01.0: PCI bridge to [bus 01-01]
[    1.523856] pci 0000:00:01.0:   bridge window [io  0x7000-0x7fff]
[    1.523863] pci 0000:00:01.0:   bridge window [mem 0xc8400000-0xc93fffff]
[    1.523872] pci 0000:00:01.0:   bridge window [mem 0xa0000000-0xafffffff 64bit pref]
[    1.524021] pci 0000:02:00.0: [8086:0083] type 0 class 0x000280
[    1.524073] pci 0000:02:00.0: reg 10: [mem 0xc7400000-0xc7401fff 64bit]
[    1.524273] pci 0000:02:00.0: PME# supported from D0 D3hot D3cold
[    1.524280] pci 0000:02:00.0: PME# disabled
[    1.543836] pci 0000:00:1c.0: PCI bridge to [bus 02-02]
[    1.543845] pci 0000:00:1c.0:   bridge window [io  0x6000-0x6fff]
[    1.543855] pci 0000:00:1c.0:   bridge window [mem 0xc7400000-0xc83fffff]
[    1.543869] pci 0000:00:1c.0:   bridge window [mem 0xc0400000-0xc13fffff 64bit pref]
[    1.544000] pci 0000:03:00.0: [10ec:5209] type 0 class 0x00ff00
[    1.544027] pci 0000:03:00.0: reg 10: [mem 0xc6400000-0xc6400fff]
[    1.544179] pci 0000:03:00.0: supports D1 D2
[    1.544180] pci 0000:03:00.0: PME# supported from D1 D2 D3hot
[    1.544186] pci 0000:03:00.0: PME# disabled
[    1.563803] pci 0000:00:1c.1: PCI bridge to [bus 03-03]
[    1.563812] pci 0000:00:1c.1:   bridge window [io  0x5000-0x5fff]
[    1.563821] pci 0000:00:1c.1:   bridge window [mem 0xc6400000-0xc73fffff]
[    1.563836] pci 0000:00:1c.1:   bridge window [mem 0xc1400000-0xc23fffff 64bit pref]
[    1.563971] pci 0000:04:00.0: [1033:0194] type 0 class 0x000c03
[    1.564005] pci 0000:04:00.0: reg 10: [mem 0xc5400000-0xc5401fff 64bit]
[    1.564142] pci 0000:04:00.0: PME# supported from D0 D3hot D3cold
[    1.564148] pci 0000:04:00.0: PME# disabled
[    1.583776] pci 0000:00:1c.2: PCI bridge to [bus 04-04]
[    1.583785] pci 0000:00:1c.2:   bridge window [io  0x4000-0x4fff]
[    1.583794] pci 0000:00:1c.2:   bridge window [mem 0xc5400000-0xc63fffff]
[    1.583809] pci 0000:00:1c.2:   bridge window [mem 0xc2400000-0xc33fffff 64bit pref]
[    1.583994] pci 0000:05:00.0: [10ec:8168] type 0 class 0x000200
[    1.584066] pci 0000:05:00.0: reg 10: [io  0x3000-0x30ff]
[    1.584195] pci 0000:05:00.0: reg 18: [mem 0xc3404000-0xc3404fff 64bit pref]
[    1.584274] pci 0000:05:00.0: reg 20: [mem 0xc3400000-0xc3403fff 64bit pref]
[    1.584502] pci 0000:05:00.0: supports D1 D2
[    1.584503] pci 0000:05:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    1.584518] pci 0000:05:00.0: PME# disabled
[    1.603775] pci 0000:00:1c.3: PCI bridge to [bus 05-05]
[    1.603784] pci 0000:00:1c.3:   bridge window [io  0x3000-0x3fff]
[    1.603793] pci 0000:00:1c.3:   bridge window [mem 0xc4400000-0xc53fffff]
[    1.603808] pci 0000:00:1c.3:   bridge window [mem 0xc3400000-0xc43fffff 64bit pref]
[    1.603862] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    1.603944] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP01._PRT]
[    1.603972] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP02._PRT]
[    1.604000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP03._PRT]
[    1.604027] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP04._PRT]
[    1.604060] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEG0._PRT]
[    1.604125] \_SB_.PCI0:_OSC invalid UUID
[    1.604126] _OSC request data:1 1f 1f 
[    1.604130]  pci0000:00: Requesting ACPI _OSC control (0x1d)
[    1.604158] \_SB_.PCI0:_OSC invalid UUID
[    1.604159] _OSC request data:1 0 1d 
[    1.606353] ACPI: PCI Interrupt Link [LNKA] (IRQs 1 3 4 5 6 10 11 12 14 15) *7
[    1.606396] ACPI: PCI Interrupt Link [LNKB] (IRQs 1 3 4 5 6 10 *11 12 14 15)
[    1.606437] ACPI: PCI Interrupt Link [LNKC] (IRQs 1 3 4 5 6 10 *11 12 14 15)
[    1.606476] ACPI: PCI Interrupt Link [LNKD] (IRQs 1 3 4 5 6 *10 11 12 14 15)
[    1.606516] ACPI: PCI Interrupt Link [LNKE] (IRQs 1 3 4 5 6 10 11 12 14 15) *7
[    1.606557] ACPI: PCI Interrupt Link [LNKF] (IRQs 1 3 4 5 6 10 11 12 14 15) *0, disabled.
[    1.606597] ACPI: PCI Interrupt Link [LNKG] (IRQs 1 3 4 5 6 *10 11 12 14 15)
[    1.606637] ACPI: PCI Interrupt Link [LNKH] (IRQs 1 3 4 5 6 *10 11 12 14 15)
[    1.606714] vgaarb: device added: PCI:0000:00:02.0,decodes=io+mem,owns=io+mem,locks=none
[    1.606721] vgaarb: device added: PCI:0000:01:00.0,decodes=io+mem,owns=none,locks=none
[    1.606724] vgaarb: loaded
[    1.606850] SCSI subsystem initialized
[    1.606891] libata version 3.00 loaded.
[    1.606921] usbcore: registered new interface driver usbfs
[    1.606929] usbcore: registered new interface driver hub
[    1.606948] usbcore: registered new device driver usb
[    1.607024] wmi: Mapper loaded
[    1.607025] PCI: Using ACPI for IRQ routing
[    1.607027] PCI: pci_cache_line_size set to 64 bytes
[    1.607121] reserve RAM buffer: 0000000000094400 - 000000000009ffff 
[    1.607123] reserve RAM buffer: 000000009ae3f000 - 000000009bffffff 
[    1.607125] reserve RAM buffer: 000000009b000000 - 000000009bffffff 
[    1.607127] reserve RAM buffer: 000000015fe00000 - 000000015fffffff 
[    1.607200] NetLabel: Initializing
[    1.607201] NetLabel:  domain hash size = 128
[    1.607202] NetLabel:  protocols = UNLABELED CIPSOv4
[    1.607211] NetLabel:  unlabeled traffic allowed by default
[    1.607241] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0, 0, 0, 0, 0
[    1.607246] hpet0: 8 comparators, 64-bit 14.318180 MHz counter
[    1.609258] Switching to clocksource hpet
[    1.613723] Switched to NOHz mode on CPU #0
[    1.613766] Switched to NOHz mode on CPU #3
[    1.613854] Switched to NOHz mode on CPU #1
[    1.613857] Switched to NOHz mode on CPU #2
[    1.614077] AppArmor: AppArmor Filesystem Enabled
[    1.614098] pnp: PnP ACPI init
[    1.614110] ACPI: bus type pnp registered
[    1.614383] pnp 00:00: [bus 00-fe]
[    1.614385] pnp 00:00: [io  0x0000-0x0cf7 window]
[    1.614387] pnp 00:00: [io  0x0cf8-0x0cff]
[    1.614388] pnp 00:00: [io  0x0d00-0xffff window]
[    1.614390] pnp 00:00: [mem 0x000a0000-0x000bffff window]
[    1.614391] pnp 00:00: [mem 0x000c0000-0x000c3fff window]
[    1.614393] pnp 00:00: [mem 0x000c4000-0x000c7fff window]
[    1.614394] pnp 00:00: [mem 0x000c8000-0x000cbfff window]
[    1.614396] pnp 00:00: [mem 0x000cc000-0x000cffff window]
[    1.614397] pnp 00:00: [mem 0x000d0000-0x000d3fff window]
[    1.614399] pnp 00:00: [mem 0x000d4000-0x000d7fff window]
[    1.614400] pnp 00:00: [mem 0x000d8000-0x000dbfff window]
[    1.614402] pnp 00:00: [mem 0x000dc000-0x000dffff window]
[    1.614403] pnp 00:00: [mem 0x000e0000-0x000e3fff window]
[    1.614405] pnp 00:00: [mem 0x000e4000-0x000e7fff window]
[    1.614407] pnp 00:00: [mem 0x000e8000-0x000ebfff window]
[    1.614408] pnp 00:00: [mem 0x000ec000-0x000effff window]
[    1.614410] pnp 00:00: [mem 0x000f0000-0x000fffff window]
[    1.614413] pnp 00:00: [mem 0x9fa00000-0xfeafffff window]
[    1.614473] pnp 00:00: Plug and Play ACPI device, IDs PNP0a08 PNP0a03 (active)
[    1.614535] pnp 00:01: [io  0x0000-0x001f]
[    1.614537] pnp 00:01: [io  0x0081-0x0091]
[    1.614538] pnp 00:01: [io  0x0093-0x009f]
[    1.614539] pnp 00:01: [io  0x00c0-0x00df]
[    1.614541] pnp 00:01: [dma 4]
[    1.614559] pnp 00:01: Plug and Play ACPI device, IDs PNP0200 (active)
[    1.614565] pnp 00:02: [mem 0xff000000-0xffffffff]
[    1.614584] pnp 00:02: Plug and Play ACPI device, IDs INT0800 (active)
[    1.614644] pnp 00:03: [mem 0xfed00000-0xfed003ff]
[    1.614662] pnp 00:03: Plug and Play ACPI device, IDs PNP0103 (active)
[    1.614670] pnp 00:04: [io  0x00f0]
[    1.614678] pnp 00:04: [irq 13]
[    1.614695] pnp 00:04: Plug and Play ACPI device, IDs PNP0c04 (active)
[    1.614704] pnp 00:05: [io  0x002e-0x002f]
[    1.614705] pnp 00:05: [io  0x004e-0x004f]
[    1.614707] pnp 00:05: [io  0x0061]
[    1.614708] pnp 00:05: [io  0x0063]
[    1.614709] pnp 00:05: [io  0x0065]
[    1.614710] pnp 00:05: [io  0x0067]
[    1.614711] pnp 00:05: [io  0x0070]
[    1.614713] pnp 00:05: [io  0x0080]
[    1.614714] pnp 00:05: [io  0x0092]
[    1.614715] pnp 00:05: [io  0x00b2-0x00b3]
[    1.614716] pnp 00:05: [io  0x0680-0x069f]
[    1.614718] pnp 00:05: [io  0x1000-0x100f]
[    1.614719] pnp 00:05: [io  0xffff]
[    1.614720] pnp 00:05: [io  0xffff]
[    1.614722] pnp 00:05: [io  0x0400-0x0453]
[    1.614723] pnp 00:05: [io  0x0458-0x047f]
[    1.614724] pnp 00:05: [io  0x0500-0x057f]
[    1.614725] pnp 00:05: [io  0x164e-0x164f]
[    1.614727] pnp 00:05: [io  0x2000]
[    1.614728] pnp 00:05: [io  0x2004]
[    1.614775] system 00:05: [io  0x0680-0x069f] has been reserved
[    1.614777] system 00:05: [io  0x1000-0x100f] has been reserved
[    1.614779] system 00:05: [io  0xffff] has been reserved
[    1.614781] system 00:05: [io  0xffff] has been reserved
[    1.614782] system 00:05: [io  0x0400-0x0453] has been reserved
[    1.614784] system 00:05: [io  0x0458-0x047f] has been reserved
[    1.614786] system 00:05: [io  0x0500-0x057f] has been reserved
[    1.614788] system 00:05: [io  0x164e-0x164f] has been reserved
[    1.614789] system 00:05: [io  0x2000] has been reserved
[    1.614791] system 00:05: [io  0x2004] has been reserved
[    1.614793] system 00:05: Plug and Play ACPI device, IDs PNP0c02 (active)
[    1.614800] pnp 00:06: [io  0x0070-0x0077]
[    1.614804] pnp 00:06: [irq 8]
[    1.614821] pnp 00:06: Plug and Play ACPI device, IDs PNP0b00 (active)
[    1.614840] pnp 00:07: [io  0x0454-0x0457]
[    1.614870] system 00:07: [io  0x0454-0x0457] has been reserved
[    1.614872] system 00:07: Plug and Play ACPI device, IDs INT3f0d PNP0c02 (active)
[    1.614883] pnp 00:08: [io  0x0060]
[    1.614884] pnp 00:08: [io  0x0064]
[    1.614889] pnp 00:08: [irq 1]
[    1.614907] pnp 00:08: Plug and Play ACPI device, IDs PNP0303 (active)
[    1.614921] pnp 00:09: [irq 12]
[    1.614942] pnp 00:09: Plug and Play ACPI device, IDs SNY9014 PNP0f13 (active)
[    1.614962] pnp 00:0a: [mem 0xfed40000-0xfed44fff]
[    1.614982] pnp 00:0a: Plug and Play ACPI device, IDs IFX0102 PNP0c31 (active)
[    1.615072] pnp 00:0b: [mem 0xfed1c000-0xfed1ffff]
[    1.615074] pnp 00:0b: [mem 0xfed10000-0xfed17fff]
[    1.615075] pnp 00:0b: [mem 0xfed18000-0xfed18fff]
[    1.615076] pnp 00:0b: [mem 0xfed19000-0xfed19fff]
[    1.615079] pnp 00:0b: [mem 0xe0000000-0xefffffff]
[    1.615081] pnp 00:0b: [mem 0xfed20000-0xfed3ffff]
[    1.615082] pnp 00:0b: [mem 0xfed90000-0xfed93fff]
[    1.615083] pnp 00:0b: [mem 0xff000000-0xffffffff]
[    1.615085] pnp 00:0b: [mem 0xfee00000-0xfeefffff]
[    1.615086] pnp 00:0b: [mem 0x9fa00000-0x9fa00fff]
[    1.615124] system 00:0b: [mem 0xfed1c000-0xfed1ffff] has been reserved
[    1.615126] system 00:0b: [mem 0xfed10000-0xfed17fff] has been reserved
[    1.615128] system 00:0b: [mem 0xfed18000-0xfed18fff] has been reserved
[    1.615130] system 00:0b: [mem 0xfed19000-0xfed19fff] has been reserved
[    1.615132] system 00:0b: [mem 0xe0000000-0xefffffff] has been reserved
[    1.615133] system 00:0b: [mem 0xfed20000-0xfed3ffff] has been reserved
[    1.615135] system 00:0b: [mem 0xfed90000-0xfed93fff] has been reserved
[    1.615137] system 00:0b: [mem 0xff000000-0xffffffff] could not be reserved
[    1.615139] system 00:0b: [mem 0xfee00000-0xfeefffff] could not be reserved
[    1.615141] system 00:0b: [mem 0x9fa00000-0x9fa00fff] has been reserved
[    1.615143] system 00:0b: Plug and Play ACPI device, IDs PNP0c02 (active)
[    1.615385] pnp 00:0c: [mem 0x20000000-0x201fffff]
[    1.615387] pnp 00:0c: [mem 0x40000000-0x401fffff]
[    1.615433] system 00:0c: [mem 0x20000000-0x201fffff] could not be reserved
[    1.615435] system 00:0c: [mem 0x40000000-0x401fffff] could not be reserved
[    1.615438] system 00:0c: Plug and Play ACPI device, IDs PNP0c01 (active)
[    1.615451] pnp: PnP ACPI: found 13 devices
[    1.615453] ACPI: ACPI bus type pnp unregistered
[    1.621112] pci 0000:01:00.0: no compatible bridge window for [mem 0xfffe0000-0xffffffff pref]
[    1.621166] pci 0000:01:00.0: BAR 6: assigned [mem 0xc8420000-0xc843ffff pref]
[    1.621169] pci 0000:00:01.0: PCI bridge to [bus 01-01]
[    1.621171] pci 0000:00:01.0:   bridge window [io  0x7000-0x7fff]
[    1.621173] pci 0000:00:01.0:   bridge window [mem 0xc8400000-0xc93fffff]
[    1.621176] pci 0000:00:01.0:   bridge window [mem 0xa0000000-0xafffffff 64bit pref]
[    1.621179] pci 0000:00:1c.0: PCI bridge to [bus 02-02]
[    1.621182] pci 0000:00:1c.0:   bridge window [io  0x6000-0x6fff]
[    1.621189] pci 0000:00:1c.0:   bridge window [mem 0xc7400000-0xc83fffff]
[    1.621194] pci 0000:00:1c.0:   bridge window [mem 0xc0400000-0xc13fffff 64bit pref]
[    1.621202] pci 0000:00:1c.1: PCI bridge to [bus 03-03]
[    1.621205] pci 0000:00:1c.1:   bridge window [io  0x5000-0x5fff]
[    1.621212] pci 0000:00:1c.1:   bridge window [mem 0xc6400000-0xc73fffff]
[    1.621217] pci 0000:00:1c.1:   bridge window [mem 0xc1400000-0xc23fffff 64bit pref]
[    1.621225] pci 0000:00:1c.2: PCI bridge to [bus 04-04]
[    1.621228] pci 0000:00:1c.2:   bridge window [io  0x4000-0x4fff]
[    1.621235] pci 0000:00:1c.2:   bridge window [mem 0xc5400000-0xc63fffff]
[    1.621240] pci 0000:00:1c.2:   bridge window [mem 0xc2400000-0xc33fffff 64bit pref]
[    1.621248] pci 0000:00:1c.3: PCI bridge to [bus 05-05]
[    1.621251] pci 0000:00:1c.3:   bridge window [io  0x3000-0x3fff]
[    1.621258] pci 0000:00:1c.3:   bridge window [mem 0xc4400000-0xc53fffff]
[    1.621263] pci 0000:00:1c.3:   bridge window [mem 0xc3400000-0xc43fffff 64bit pref]
[    1.621280] pci 0000:00:01.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.621283] pci 0000:00:01.0: setting latency timer to 64
[    1.621289] pci 0000:00:1c.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.621294] pci 0000:00:1c.0: setting latency timer to 64
[    1.621303] pci 0000:00:1c.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    1.621308] pci 0000:00:1c.1: setting latency timer to 64
[    1.621317] pci 0000:00:1c.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    1.621322] pci 0000:00:1c.2: setting latency timer to 64
[    1.621331] pci 0000:00:1c.3: PCI INT D -> GSI 19 (level, low) -> IRQ 19
[    1.621336] pci 0000:00:1c.3: setting latency timer to 64
[    1.621340] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
[    1.621342] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff]
[    1.621343] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
[    1.621345] pci_bus 0000:00: resource 7 [mem 0x9fa00000-0xfeafffff]
[    1.621347] pci_bus 0000:01: resource 0 [io  0x7000-0x7fff]
[    1.621348] pci_bus 0000:01: resource 1 [mem 0xc8400000-0xc93fffff]
[    1.621350] pci_bus 0000:01: resource 2 [mem 0xa0000000-0xafffffff 64bit pref]
[    1.621352] pci_bus 0000:02: resource 0 [io  0x6000-0x6fff]
[    1.621353] pci_bus 0000:02: resource 1 [mem 0xc7400000-0xc83fffff]
[    1.621355] pci_bus 0000:02: resource 2 [mem 0xc0400000-0xc13fffff 64bit pref]
[    1.621357] pci_bus 0000:03: resource 0 [io  0x5000-0x5fff]
[    1.621358] pci_bus 0000:03: resource 1 [mem 0xc6400000-0xc73fffff]
[    1.621360] pci_bus 0000:03: resource 2 [mem 0xc1400000-0xc23fffff 64bit pref]
[    1.621361] pci_bus 0000:04: resource 0 [io  0x4000-0x4fff]
[    1.621363] pci_bus 0000:04: resource 1 [mem 0xc5400000-0xc63fffff]
[    1.621365] pci_bus 0000:04: resource 2 [mem 0xc2400000-0xc33fffff 64bit pref]
[    1.621366] pci_bus 0000:05: resource 0 [io  0x3000-0x3fff]
[    1.621368] pci_bus 0000:05: resource 1 [mem 0xc4400000-0xc53fffff]
[    1.621369] pci_bus 0000:05: resource 2 [mem 0xc3400000-0xc43fffff 64bit pref]
[    1.621390] NET: Registered protocol family 2
[    1.621514] IP route cache hash table entries: 131072 (order: 8, 1048576 bytes)
[    1.622348] TCP established hash table entries: 524288 (order: 11, 8388608 bytes)
[    1.624089] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[    1.624307] TCP: Hash tables configured (established 524288 bind 65536)
[    1.624309] TCP reno registered
[    1.624318] UDP hash table entries: 2048 (order: 4, 65536 bytes)
[    1.624339] UDP-Lite hash table entries: 2048 (order: 4, 65536 bytes)
[    1.624425] NET: Registered protocol family 1
[    1.624438] pci 0000:00:02.0: Boot video device
[    1.661349] pci 0000:04:00.0: xHCI HW did not halt within 2000 usec status = 0x0
[    1.661362] PCI: CLS 64 bytes, default 64
[    1.661364] PCI-DMA: Using software bounce buffering for IO (SWIOTLB)
[    1.661366] Placing 64MB software IO TLB between ffff880096c00000 - ffff88009ac00000
[    1.661367] software IO TLB at phys 0x96c00000 - 0x9ac00000
[    1.661395] Simple Boot Flag at 0x44 set to 0x1
[    1.661743] audit: initializing netlink socket (disabled)
[    1.661749] type=2000 audit(1309190602.520:1): initialized
[    1.672962] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    1.674237] VFS: Disk quotas dquot_6.5.2
[    1.674279] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    1.674725] fuse init (API version 7.16)
[    1.674786] msgmni has been set to 7750
[    1.674963] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    1.674984] io scheduler noop registered
[    1.674985] io scheduler deadline registered
[    1.675014] io scheduler cfq registered (default)
[    1.675089] pcieport 0000:00:01.0: setting latency timer to 64
[    1.675112] pcieport 0000:00:01.0: irq 40 for MSI/MSI-X
[    1.675417] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    1.675433] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    1.675463] intel_idle: MWAIT substates: 0x21120
[    1.675465] intel_idle: v0.4 model 0x2A
[    1.675466] intel_idle: lapic_timer_reliable_states 0xffffffff
[    1.675543] ACPI: Deprecated procfs I/F for AC is loaded, please retry with CONFIG_ACPI_PROCFS_POWER cleared
[    1.675576] ACPI: AC Adapter [ADP1] (on-line)
[    1.675650] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input0
[    1.675661] ACPI: Lid Switch [LID0]
[    1.675691] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1
[    1.675694] ACPI: Power Button [PWRB]
[    1.675804] ACPI: acpi_idle yielding to intel_idle
[    1.677567] thermal LNXTHERM:00: registered as thermal_zone0
[    1.677569] ACPI: Thermal Zone [TZ01] (73 C)
[    1.677581] ACPI: Deprecated procfs I/F for battery is loaded, please retry with CONFIG_ACPI_PROCFS_POWER cleared
[    1.677592] ACPI: Deprecated procfs I/F for battery is loaded, please retry with CONFIG_ACPI_PROCFS_POWER cleared
[    1.677636] ERST: Table is not found!
[    1.677755] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    1.677768] ACPI: Battery Slot [BAT2] (battery absent)
[    1.683449] ACPI: Battery Slot [BAT1] (battery present)
[    1.930536] Linux agpgart interface v0.103
[    1.930604] agpgart-intel 0000:00:00.0: Intel Sandybridge Chipset
[    1.930695] agpgart-intel 0000:00:00.0: detected gtt size: 2097152K total, 262144K mappable
[    1.931666] agpgart-intel 0000:00:00.0: detected 65536K stolen memory
[    1.931757] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0xb0000000
[    1.932533] brd: module loaded
[    1.932884] loop: module loaded
[    1.932949] i2c-core: driver [adp5520] using legacy suspend method
[    1.932950] i2c-core: driver [adp5520] using legacy resume method
[    1.933219] Fixed MDIO Bus: probed
[    1.933239] PPP generic driver version 2.4.2
[    1.933263] tun: Universal TUN/TAP device driver, 1.6
[    1.933265] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    1.933319] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    1.933340] ehci_hcd 0000:00:1a.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    1.933355] ehci_hcd 0000:00:1a.0: setting latency timer to 64
[    1.933358] ehci_hcd 0000:00:1a.0: EHCI Host Controller
[    1.933387] ehci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 1
[    1.933445] ehci_hcd 0000:00:1a.0: debug port 2
[    1.937324] ehci_hcd 0000:00:1a.0: cache line size of 64 is not supported
[    1.937340] ehci_hcd 0000:00:1a.0: irq 23, io mem 0xc940a000
[    1.958843] ehci_hcd 0000:00:1a.0: USB 2.0 started, EHCI 1.00
[    1.959023] hub 1-0:1.0: USB hub found
[    1.959026] hub 1-0:1.0: 2 ports detected
[    1.959079] ehci_hcd 0000:00:1d.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    1.959091] ehci_hcd 0000:00:1d.0: setting latency timer to 64
[    1.959094] ehci_hcd 0000:00:1d.0: EHCI Host Controller
[    1.959122] ehci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    1.959169] ehci_hcd 0000:00:1d.0: debug port 2
[    1.963049] ehci_hcd 0000:00:1d.0: cache line size of 64 is not supported
[    1.963060] ehci_hcd 0000:00:1d.0: irq 20, io mem 0xc9409000
[    1.978821] ehci_hcd 0000:00:1d.0: USB 2.0 started, EHCI 1.00
[    1.978986] hub 2-0:1.0: USB hub found
[    1.978989] hub 2-0:1.0: 2 ports detected
[    1.979032] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    1.979040] uhci_hcd: USB Universal Host Controller Interface driver
[    1.979117] i8042: PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    1.981721] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.981726] serio: i8042 AUX port at 0x60,0x64 irq 12
[    1.981825] mousedev: PS/2 mouse device common for all mice
[    1.981919] rtc_cmos 00:06: RTC can wake from S4
[    1.981968] rtc_cmos 00:06: rtc core: registered rtc_cmos as rtc0
[    1.982000] rtc0: alarms up to one month, y3k, 242 bytes nvram, hpet irqs
[    1.982070] device-mapper: uevent: version 1.0.3
[    1.982122] device-mapper: ioctl: 4.19.1-ioctl (2011-01-07) initialised: dm-devel@redhat.com
[    1.982168] device-mapper: multipath: version 1.2.0 loaded
[    1.982170] device-mapper: multipath round-robin: version 1.0.0 loaded
[    1.982335] cpuidle: using governor ladder
[    1.982472] cpuidle: using governor menu
[    1.982630] TCP cubic registered
[    1.982715] NET: Registered protocol family 10
[    1.983049] NET: Registered protocol family 17
[    1.983060] Registering the dns_resolver key type
[    1.983739] PM: Hibernation image not present or could not be loaded.
[    1.983746] registered taskstats version 1
[    1.984156]   Magic number: 15:239:86
[    1.984243] rtc_cmos 00:06: setting system clock to 2011-06-27 16:03:23 UTC (1309190603)
[    1.984245] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.984246] EDD information not available.
[    1.985405] Freeing unused kernel memory: 956k freed
[    1.985500] Write protecting the kernel read-only data: 10240k
[    1.986134] Freeing unused kernel memory: 184k freed
[    1.989476] Freeing unused kernel memory: 1444k freed
[    1.997326] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input2
[    2.002585] <30>udev[70]: starting version 167
[    2.036958] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    2.036991] r8169 0000:05:00.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    2.037102] r8169 0000:05:00.0: setting latency timer to 64
[    2.037118] r8169 0000:05:00.0: (unregistered net_device): unknown MAC, using family default
[    2.037331] r8169 0000:05:00.0: irq 41 for MSI/MSI-X
[    2.037791] r8169 0000:05:00.0: eth0: RTL8168b/8111b at 0xffffc900110ac000, f0:bf:97:59:18:50, XID 0c200000 IRQ 41
[    2.042644] ahci 0000:00:1f.2: version 3.0
[    2.042664] ahci 0000:00:1f.2: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[    2.042715] ahci 0000:00:1f.2: irq 42 for MSI/MSI-X
[    2.042741] ahci: SSS flag set, parallel bus scan disabled
[    2.059189] ahci 0000:00:1f.2: AHCI 0001.0300 32 slots 6 ports 6 Gbps 0x11 impl RAID mode
[    2.059194] ahci 0000:00:1f.2: flags: 64bit ncq sntf stag pm led clo pio slum part apst 
[    2.059199] ahci 0000:00:1f.2: setting latency timer to 64
[    2.059644] scsi0 : ahci
[    2.059770] scsi1 : ahci
[    2.059835] scsi2 : ahci
[    2.059895] scsi3 : ahci
[    2.059998] scsi4 : ahci
[    2.060086] scsi5 : ahci
[    2.060303] ata1: SATA max UDMA/133 abar m2048@0xc9408000 port 0xc9408100 irq 42
[    2.060305] ata2: DUMMY
[    2.060306] ata3: DUMMY
[    2.060306] ata4: DUMMY
[    2.060309] ata5: SATA max UDMA/133 abar m2048@0xc9408000 port 0xc9408300 irq 42
[    2.060310] ata6: DUMMY
[    2.278511] usb 1-1: new high speed USB device using ehci_hcd and address 2
[    2.408349] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    2.411769] ata1.00: ATA-8: ST95005620AS, SD25, max UDMA/133
[    2.411779] ata1.00: 976773168 sectors, multi 0: LBA48 NCQ (depth 31/32)
[    2.417345] ata1.00: configured for UDMA/133
[    2.417544] scsi 0:0:0:0: Direct-Access     ATA      ST95005620AS     SD25 PQ: 0 ANSI: 5
[    2.417690] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    2.417792] sd 0:0:0:0: [sda] 976773168 512-byte logical blocks: (500 GB/465 GiB)
[    2.417853] sd 0:0:0:0: [sda] Write Protect is off
[    2.417855] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    2.417879] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.421044]  sda: sda1 sda2 sda3 sda4 < sda5 sda6 sda7 >
[    2.421425] sd 0:0:0:0: [sda] Attached SCSI disk
[    2.428904] hub 1-1:1.0: USB hub found
[    2.428999] hub 1-1:1.0: 6 ports detected
[    2.548165] usb 2-1: new high speed USB device using ehci_hcd and address 2
[    2.658007] Refined TSC clocksource calibration: 2494.333 MHz.
[    2.658019] Switching to clocksource tsc
[    2.698550] hub 2-1:1.0: USB hub found
[    2.698648] hub 2-1:1.0: 8 ports detected
[    2.757890] ata5: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    2.759631] ata5.00: ATAPI: MATSHITABD-MLT UJ242AS, 1.40, max UDMA/100
[    2.761545] ata5.00: configured for UDMA/100
[    2.763111] scsi 4:0:0:0: CD-ROM            MATSHITA BD-MLT UJ242AS   1.40 PQ: 0 ANSI: 5
[    2.769676] sr0: scsi3-mmc drive: 62x/62x writer dvd-ram cd/rw xa/form2 cdda tray
[    2.769687] cdrom: Uniform CD-ROM driver Revision: 3.20
[    2.769904] sr 4:0:0:0: Attached scsi CD-ROM sr0
[    2.770004] sr 4:0:0:0: Attached scsi generic sg1 type 5
[    2.777930] usb 1-1.1: new full speed USB device using ehci_hcd and address 3
[    2.929092] EXT4-fs (sda6): mounted filesystem with ordered data mode. Opts: (null)
[    2.967705] usb 1-1.3: new high speed USB device using ehci_hcd and address 4
[    3.187441] usb 1-1.6: new full speed USB device using ehci_hcd and address 5
[    3.377236] usb 2-1.2: new full speed USB device using ehci_hcd and address 3
[    8.542421] Adding 13218812k swap on /dev/sda7.  Priority:-1 extents:1 across:13218812k 
[    8.549643] <30>udev[319]: starting version 167
[    8.568169] lp: driver loaded but no devices found
[    8.577261] EXT4-fs (sda6): re-mounted. Opts: errors=remount-ro
[    8.610953] tpm_tis 00:0a: 1.2 TPM (device-id 0xB, rev-id 16)
[    8.623266] sony-laptop: Sony Notebook Control Driver v0.6.
[    8.642889] type=1400 audit(1309187010.163:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=478 comm="apparmor_parser"
[    8.643605] type=1400 audit(1309187010.163:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=478 comm="apparmor_parser"
[    8.644064] type=1400 audit(1309187010.163:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=478 comm="apparmor_parser"
[    8.645061] rts_pstor: module is from the staging directory, the quality is unknown, you have been warned.
[    8.672562] xhci_hcd 0000:04:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    8.672588] xhci_hcd 0000:04:00.0: setting latency timer to 64
[    8.672593] xhci_hcd 0000:04:00.0: xHCI Host Controller
[    8.672683] xhci_hcd 0000:04:00.0: new USB bus registered, assigned bus number 3
[    8.672918] Initializing Realtek PCIE storage driver...
[    8.672939] rts_pstor 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    8.674247] Resource length: 0x1000
[    8.674269] Original address: 0xc6400000, remapped address: 0xffffc900110be000
[    8.674275] pci->irq = 17
[    8.674277] rtsx_acquire_irq: chip->msi_en = 0, pci->irq = 17
[    8.674304] rts_pstor 0000:03:00.0: setting latency timer to 64
[    8.674310] scsi6 : SCSI emulation for PCI-Express Mass Storage devices
[    8.713600] input: Sony Vaio Keys as /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:01/SNY5001:00/input/input3
[    8.714381] input: Sony Vaio Jogdial as /devices/virtual/input/input4
[    8.714580] sony-laptop: brightness ignored, must be controlled by ACPI video driver
[    8.720586] Bluetooth: Core ver 2.15
[    8.720625] NET: Registered protocol family 31
[    8.720627] Bluetooth: HCI device and connection manager initialized
[    8.720630] Bluetooth: HCI socket layer initialized
[    8.721240] r8169 0000:05:00.0: eth0: link down
[    8.721614] ADDRCONF(NETDEV_UP): eth0: link is not ready
[    8.725136] cfg80211: Calling CRDA to update world regulatory domain
[    8.771839] Bluetooth: Generic Bluetooth USB driver ver 0.6
[    8.777993] usbcore: registered new interface driver btusb
[    8.831861] type=1400 audit(1309187010.353:5): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=684 comm="apparmor_parser"
[    8.835300] xhci_hcd 0000:04:00.0: irq 18, io mem 0xc5400000
[    8.835442] xhci_hcd 0000:04:00.0: irq 43 for MSI/MSI-X
[    8.835448] xhci_hcd 0000:04:00.0: irq 44 for MSI/MSI-X
[    8.835454] xhci_hcd 0000:04:00.0: irq 45 for MSI/MSI-X
[    8.835459] xhci_hcd 0000:04:00.0: irq 46 for MSI/MSI-X
[    8.835463] xhci_hcd 0000:04:00.0: irq 47 for MSI/MSI-X
[    8.835926] type=1400 audit(1309187010.353:6): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince" pid=685 comm="apparmor_parser"
[    8.837152] type=1400 audit(1309187010.353:7): apparmor="STATUS" operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" pid=683 comm="apparmor_parser"
[    8.838496] type=1400 audit(1309187010.353:8): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=684 comm="apparmor_parser"
[    8.838512] usb usb3: No SuperSpeed endpoint companion for config 1  interface 0 altsetting 0 ep 129: using minimum values
[    8.838640] xHCI xhci_add_endpoint called for root hub
[    8.838642] xHCI xhci_check_bandwidth called for root hub
[    8.838675] hub 3-0:1.0: USB hub found
[    8.838679] hub 3-0:1.0: 4 ports detected
[    8.838958] type=1400 audit(1309187010.353:9): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=684 comm="apparmor_parser"
[    8.840735] type=1400 audit(1309187010.363:10): apparmor="STATUS" operation="profile_load" name="/usr/sbin/tcpdump" pid=694 comm="apparmor_parser"
[    8.842824] type=1400 audit(1309187010.363:11): apparmor="STATUS" operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" pid=688 comm="apparmor_parser"
[    8.853999] Linux video capture interface: v2.00
[    8.855133] [drm] Initialized drm 1.1.0 20060810
[    8.857097] uvcvideo: Found UVC 1.00 device USB 2.0 Camera (0c45:64b5)
[    8.866975] input: USB 2.0 Camera as /devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.3/1-1.3:1.0/input/input5
[    8.867068] usbcore: registered new interface driver uvcvideo
[    8.867070] USB Video Class driver (v1.0.0)
[    8.880741] rts_pstor: waiting for device to settle before scanning
[    8.894447] cfg80211: World regulatory domain updated:
[    8.894450] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[    8.894453] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[    8.894456] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[    8.894458] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[    8.894460] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[    8.894463] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[    8.903766] Bluetooth: L2CAP ver 2.15
[    8.903769] Bluetooth: L2CAP socket layer initialized
[    8.906521] i915 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    8.906526] i915 0000:00:02.0: setting latency timer to 64
[    8.932183] iwlagn: Intel(R) Wireless WiFi Link AGN driver for Linux, in-tree:
[    8.932186] iwlagn: Copyright(c) 2003-2010 Intel Corporation
[    8.932236] iwlagn 0000:02:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    8.932245] iwlagn 0000:02:00.0: setting latency timer to 64
[    8.932279] iwlagn 0000:02:00.0: Detected Intel(R) Centrino(R) Wireless-N 1000 BGN, REV=0x6C
[    8.953872] iwlagn 0000:02:00.0: device EEPROM VER=0x15d, CALIB=0x6
[    8.953875] iwlagn 0000:02:00.0: Device SKU: 0X9
[    8.953876] iwlagn 0000:02:00.0: Valid Tx ant: 0X1, Valid Rx ant: 0X3
[    8.957616] iwlagn 0000:02:00.0: Tunable channels: 13 802.11bg, 0 802.11a channels
[    8.958040] iwlagn 0000:02:00.0: irq 48 for MSI/MSI-X
[    8.965310] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[    8.965313] Bluetooth: BNEP filters: protocol multicast
[    8.973619] iwlagn 0000:02:00.0: loaded firmware version 128.50.3.1 build 13488
[    8.973757] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain 
[    8.976057] i915 0000:00:02.0: irq 49 for MSI/MSI-X
[    8.976063] [drm] Supports vblank timestamp caching Rev 1 (10.10.2010).
[    8.976065] [drm] Driver supports precise vblank timestamp query.
```

The no superspeed endpoint error bit on ubuntu:

```
[    8.835300] xhci_hcd 0000:04:00.0: irq 18, io mem 0xc5400000
[    8.835442] xhci_hcd 0000:04:00.0: irq 43 for MSI/MSI-X
[    8.835448] xhci_hcd 0000:04:00.0: irq 44 for MSI/MSI-X
[    8.835454] xhci_hcd 0000:04:00.0: irq 45 for MSI/MSI-X
[    8.835459] xhci_hcd 0000:04:00.0: irq 46 for MSI/MSI-X
[    8.835463] xhci_hcd 0000:04:00.0: irq 47 for MSI/MSI-X
[    8.835926] type=1400 audit(1309187010.353:6): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince" pid=685 comm="apparmor_parser"
[    8.837152] type=1400 audit(1309187010.353:7): apparmor="STATUS" operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" pid=683 comm="apparmor_parser"
[    8.838496] type=1400 audit(1309187010.353:8): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=684 comm="apparmor_parser"
[    8.838512] usb usb3: No SuperSpeed endpoint companion for config 1  interface 0 altsetting 0 ep 129: using minimum values
[    8.838640] xHCI xhci_add_endpoint called for root hub
[    8.838642] xHCI xhci_check_bandwidth called for root hub
[    8.838675] hub 3-0:1.0: USB hub found
[    8.838679] hub 3-0:1.0: 4 ports detected
```

When booting I had a bluetooth dongle and the external drive plugged into the usb ports, nothing else.

Hope this might give someone an idea...

---

### Post by kimangroo on 2011-06-29
Ok, so does anyone know of any mailing lists or other forums where I might be able to get some help?

---

### Post by gyurma on 2011-07-08
I have a similar problem.

My controller is a Digitus board with NEC uPD720200 on it.

If i have the drive already plugged in at boot time, system does not boot, but stalls at some point during bootup.

If i plug it in later, it gives some xhci warning and error messages in dmesg. (something like "endpoint enumeration failed")

Maybe it does not like that the drive provides a simulated CD and a HDD ? 

When I replug it, it even crashes the xhci module.

I can post logfiles later in the evening.

---

### Post by Bart Robeyns on 2011-07-08
I have the 2TB version of the Iomega Prestige USB 3.0; it also hangs the whole system when plugging it into the usb3-port of a running system. Below is the relevant part of kern.log (starting from the point where I plug it into the port). It clearly indicates some errors, but I haven't got a clue about what they mean.
```
Jul  7 16:29:49 brtop kernel: [ 1156.601827] usb 3-2: new SuperSpeed USB device using xhci_hcd and address 3
Jul  7 16:29:49 brtop kernel: [ 1156.644612] xhci_hcd 0000:45:00.0: WARN: short transfer on control ep
Jul  7 16:29:49 brtop kernel: [ 1156.650723] xhci_hcd 0000:45:00.0: WARN: short transfer on control ep
Jul  7 16:29:49 brtop kernel: [ 1156.656741] xhci_hcd 0000:45:00.0: WARN: short transfer on control ep
Jul  7 16:29:49 brtop kernel: [ 1156.662738] xhci_hcd 0000:45:00.0: WARN: short transfer on control ep
Jul  7 16:29:49 brtop kernel: [ 1156.692477] xhci_hcd 0000:45:00.0: WARN: short transfer on control ep
Jul  7 16:29:49 brtop kernel: [ 1156.699706] xhci_hcd 0000:45:00.0: WARN: short transfer on control ep
Jul  7 16:29:49 brtop kernel: [ 1156.699873] xhci_hcd 0000:45:00.0: WARN no SS endpoint bMaxBurst
Jul  7 16:29:49 brtop kernel: [ 1156.750933] xhci_hcd 0000:45:00.0: WARN: short transfer on control ep
Jul  7 16:29:49 brtop kernel: [ 1156.751199] scsi8 : uas
Jul  7 16:29:49 brtop kernel: [ 1156.759384] scsi 8:0:0:0: Direct-Access     OEM      Ext Hard Disk    0000 PQ: 0 ANSI: 5
Jul  7 16:29:49 brtop kernel: [ 1156.920267] scsi 8:0:0:1: CD-ROM            Virtual  CDROM                 PQ: 0 ANSI: 0
Jul  7 16:29:49 brtop kernel: [ 1156.920716] sd 8:0:0:0: Attached scsi generic sg2 type 0
Jul  7 16:29:49 brtop kernel: [ 1157.064942] sd 8:0:0:0: [sdb] 488199446 4096-byte logical blocks: (1.99 TB/1.81 TiB)
Jul  7 16:29:49 brtop kernel: [ 1157.111628] sr1: scsi-1 drive
Jul  7 16:29:49 brtop kernel: [ 1157.111895] sr 8:0:0:1: Attached scsi CD-ROM sr1
Jul  7 16:29:49 brtop kernel: [ 1157.112423] sr 8:0:0:1: Attached scsi generic sg3 type 5
Jul  7 16:29:49 brtop kernel: [ 1157.350698] sd 8:0:0:0: [sdb] Write Protect is off
Jul  7 16:29:49 brtop kernel: [ 1157.350706] sd 8:0:0:0: [sdb] Mode Sense: 00 00 00 00
Jul  7 16:29:50 brtop kernel: [ 1157.443827] sd 8:0:0:0: [sdb] Cache data unavailable
Jul  7 16:29:50 brtop kernel: [ 1157.443834] sd 8:0:0:0: [sdb] Assuming drive cache: write through
Jul  7 16:29:50 brtop kernel: [ 1157.638907] xhci_hcd 0000:45:00.0: WARN: babble error on endpoint
Jul  7 16:29:50 brtop kernel: [ 1157.639137] xhci_hcd 0000:45:00.0: WARN Set TR Deq Ptr cmd invalid because of stream ID configuration
Jul  7 16:29:50 brtop kernel: [ 1157.639283] xhci_hcd 0000:45:00.0: ERROR Transfer event for disabled endpoint or incorrect stream ring
Jul  7 16:30:01 brtop kernel: [ 1169.062543] BUG: unable to handle kernel paging request at 01012e00
Jul  7 16:30:01 brtop kernel: [ 1169.062552] IP: [<c1126190>] kmem_cache_alloc+0x50/0x100
Jul  7 16:30:01 brtop kernel: [ 1169.062565] *pdpt = 000000002e111001 *pde = 0000000000000000 
Jul  7 16:30:01 brtop kernel: [ 1169.062572] Oops: 0000 [#1] SMP 
Jul  7 16:30:01 brtop kernel: [ 1169.062576] last sysfs file: /sys/devices/system/cpu/cpu3/cache/index2/shared_cpu_map
Jul  7 16:30:01 brtop kernel: [ 1169.062581] Modules linked in: aesni_intel cryptd aes_i586 aes_generic usb_storage uas rfcomm sco bnep l2cap binfmt_misc vboxnetadp vboxnetflt vboxdrv vmnet dm_crypt vesafb vmblock vsock vmci vmmon pata_pcmcia nfsd exportfs nfs lockd fscache nfs_acl auth_rpcgss sunrpc arc4 tpm_infineon iwlagn pcmcia hp_wmi snd_hda_codec_idt nvidia(P) snd_hda_intel snd_hda_codec snd_hwdep snd_pcm snd_seq_midi uvcvideo snd_rawmidi videodev xhci_hcd snd_seq_midi_event snd_seq joydev btusb sparse_keymap ppdev tpm_tis snd_timer tpm yenta_socket pcmcia_rsrc bluetooth snd_seq_device iwlcore mac80211 tpm_bios r852 sm_common snd pcmcia_core hp_accel nand nand_ids intel_ips cfg80211 nand_ecc mtd lis3lv02d parport_pc soundcore snd_page_alloc input_polldev psmouse serio_raw lp parport firewire_ohci ahci sdhci_pci firewire_core sdhci crc_itu_t libahci video e1000e
Jul  7 16:30:01 brtop kernel: [ 1169.062688] 
Jul  7 16:30:01 brtop kernel: [ 1169.062693] Pid: 3930, comm: atsa1 Tainted: P            2.6.38-8-generic-pae #42-Ubuntu Hewlett-Packard HP EliteBook 8740w/1520
Jul  7 16:30:01 brtop kernel: [ 1169.062703] EIP: 0060:[<c1126190>] EFLAGS: 00010006 CPU: 2
Jul  7 16:30:01 brtop kernel: [ 1169.062708] EIP is at kmem_cache_alloc+0x50/0x100
Jul  7 16:30:01 brtop kernel: [ 1169.062711] EAX: f7887e94 EBX: f7402380 ECX: c1073bbd EDX: 00000000
Jul  7 16:30:01 brtop kernel: [ 1169.062715] ESI: 00000246 EDI: 01012e00 EBP: d799dee8 ESP: d799debc
Jul  7 16:30:01 brtop kernel: [ 1169.062719]  DS: 007b ES: 007b FS: 00d8 GS: 00e0 SS: 0068
Jul  7 16:30:01 brtop kernel: [ 1169.062723] Process atsa1 (pid: 3930, ti=d799c000 task=d7da1940 task.ti=d799c000)
Jul  7 16:30:01 brtop kernel: [ 1169.062726] Stack:
Jul  7 16:30:01 brtop kernel: [ 1169.062729]  00000022 ea570600 d7864c20 c1073bbd d7864c0c d7864c00 f752a600 000000d0
Jul  7 16:30:01 brtop kernel: [ 1169.062739]  ea62bf20 c1774400 00000000 d799df04 c1073bbd 01200011 d798bfb4 ea62bf20
Jul  7 16:30:01 brtop kernel: [ 1169.062748]  00000000 00000000 d799df3c c1057ad9 ea62bf20 d799dfb4 00022a94 ee8b9f84
Jul  7 16:30:01 brtop kernel: [ 1169.062757] Call Trace:
Jul  7 16:30:01 brtop kernel: [ 1169.062766]  [<c1073bbd>] ? alloc_pid+0x1d/0x170
Jul  7 16:30:01 brtop kernel: [ 1169.062771]  [<c1073bbd>] alloc_pid+0x1d/0x170
Jul  7 16:30:01 brtop kernel: [ 1169.062779]  [<c1057ad9>] copy_process+0x769/0xbb0
Jul  7 16:30:01 brtop kernel: [ 1169.062785]  [<c1057fc3>] do_fork+0x63/0x2d0
Jul  7 16:30:01 brtop kernel: [ 1169.062793]  [<c1136cbb>] ? sys_stat64+0x2b/0x30
Jul  7 16:30:01 brtop kernel: [ 1169.062798]  [<c10129e4>] sys_clone+0x34/0x40
Jul  7 16:30:01 brtop kernel: [ 1169.062805]  [<c100ac99>] ptregs_clone+0x15/0x3c
Jul  7 16:30:01 brtop kernel: [ 1169.062809]  [<c100ab5f>] ? sysenter_do_call+0x12/0x28
Jul  7 16:30:01 brtop kernel: [ 1169.062813] Code: b7 99 40 00 8b 4d e0 9c 58 8d 74 26 00 89 c6 fa 90 8d 74 26 00 8b 03 64 03 05 58 2e 87 c1 8b 38 85 ff 0f 84 9d 00 00 00 8b 53 10 <8b> 14 17 89 10 89 f0 50 9d 8d 74 26 00 85 ff 75 6f 8b 53 08 8b 
Jul  7 16:30:01 brtop kernel: [ 1169.062867] EIP: [<c1126190>] kmem_cache_alloc+0x50/0x100 SS:ESP 0068:d799debc
Jul  7 16:30:01 brtop kernel: [ 1169.062874] CR2: 0000000001012e00
Jul  7 16:30:01 brtop kernel: [ 1169.062879] ---[ end trace cc8097e307ef6b8d ]---
Jul  7 16:30:01 brtop kernel: [ 1169.081266] BUG: unable to handle kernel paging request at 01012e00
Jul  7 16:30:01 brtop kernel: [ 1169.081274] IP: [<c1125e03>] kmem_cache_alloc_trace+0x53/0x100
Jul  7 16:30:01 brtop kernel: [ 1169.081283] *pdpt = 00000000179a0001 *pde = 0000000000000000 
Jul  7 16:30:01 brtop kernel: [ 1169.081289] Oops: 0000 [#2] SMP 
Jul  7 16:30:01 brtop kernel: [ 1169.081293] last sysfs file: /sys/devices/system/cpu/cpu3/cache/index2/shared_cpu_map
Jul  7 16:30:01 brtop kernel: [ 1169.081297] Modules linked in: aesni_intel cryptd aes_i586 aes_generic usb_storage uas rfcomm sco bnep l2cap binfmt_misc vboxnetadp vboxnetflt vboxdrv vmnet dm_crypt vesafb vmblock vsock vmci vmmon pata_pcmcia nfsd exportfs nfs lockd fscache nfs_acl auth_rpcgss sunrpc arc4 tpm_infineon iwlagn pcmcia hp_wmi snd_hda_codec_idt nvidia(P) snd_hda_intel snd_hda_codec snd_hwdep snd_pcm snd_seq_midi uvcvideo snd_rawmidi videodev xhci_hcd snd_seq_midi_event snd_seq joydev btusb sparse_keymap ppdev tpm_tis snd_timer tpm yenta_socket pcmcia_rsrc bluetooth snd_seq_device iwlcore mac80211 tpm_bios r852 sm_common snd pcmcia_core hp_accel nand nand_ids intel_ips cfg80211 nand_ecc mtd lis3lv02d parport_pc soundcore snd_page_alloc input_polldev psmouse serio_raw lp parport firewire_ohci ahci sdhci_pci firewire_core sdhci crc_itu_t libahci video e1000e
Jul  7 16:30:01 brtop kernel: [ 1169.081392] 
Jul  7 16:30:01 brtop kernel: [ 1169.081396] Pid: 3928, comm: cron Tainted: P      D     2.6.38-8-generic-pae #42-Ubuntu Hewlett-Packard HP EliteBook 8740w/1520
Jul  7 16:30:01 brtop kernel: [ 1169.081406] EIP: 0060:[<c1125e03>] EFLAGS: 00010006 CPU: 2
Jul  7 16:30:01 brtop kernel: [ 1169.081410] EIP is at kmem_cache_alloc_trace+0x53/0x100
Jul  7 16:30:01 brtop kernel: [ 1169.081414] EAX: f7887e94 EBX: f7402380 ECX: c113aadc EDX: 00000000
Jul  7 16:30:01 brtop kernel: [ 1169.081418] ESI: 00000246 EDI: 01012e00 EBP: d7931f30 ESP: d7931f04
Jul  7 16:30:01 brtop kernel: [ 1169.081422]  DS: 007b ES: 007b FS: 00d8 GS: 00e0 SS: 0068
Jul  7 16:30:01 brtop kernel: [ 1169.081426] Process cron (pid: 3928, ti=d7930000 task=d7dcbf20 task.ti=d7930000)
Jul  7 16:30:01 brtop kernel: [ 1169.081429] Stack:
Jul  7 16:30:01 brtop kernel: [ 1169.081431]  c1148237 d7931f10 c1226cbe c113aadc c114813e 00000040 f7709200 000080d0
Jul  7 16:30:01 brtop kernel: [ 1169.081441]  e8c49950 e8c49950 ffffffe9 d7931f40 c113aadc e8c49950 00000000 d7931f68
Jul  7 16:30:01 brtop kernel: [ 1169.081450]  c113ad60 00000000 00000000 c16b8286 00000009 bfee775c ffffffea 00000000
Jul  7 16:30:01 brtop kernel: [ 1169.081460] Call Trace:
Jul  7 16:30:01 brtop kernel: [ 1169.081465]  [<c1148237>] ? alloc_inode+0x57/0x80
Jul  7 16:30:01 brtop kernel: [ 1169.081473]  [<c1226cbe>] ? security_inode_alloc+0x1e/0x20
Jul  7 16:30:01 brtop kernel: [ 1169.081479]  [<c113aadc>] ? alloc_pipe_info+0x2c/0xb0
Jul  7 16:30:01 brtop kernel: [ 1169.081483]  [<c114813e>] ? inode_init_always+0xfe/0x1a0
Jul  7 16:30:01 brtop kernel: [ 1169.081488]  [<c113aadc>] alloc_pipe_info+0x2c/0xb0
Jul  7 16:30:01 brtop kernel: [ 1169.081493]  [<c113ad60>] create_write_pipe+0x50/0x1b0
Jul  7 16:30:01 brtop kernel: [ 1169.081498]  [<c113afaf>] do_pipe_flags+0x3f/0x120
Jul  7 16:30:01 brtop kernel: [ 1169.081503]  [<c113b0a7>] sys_pipe2+0x17/0x60
Jul  7 16:30:01 brtop kernel: [ 1169.081510]  [<c106ea2c>] ? sys_getrlimit+0x3c/0x60
Jul  7 16:30:01 brtop kernel: [ 1169.081515]  [<c113b10e>] sys_pipe+0x1e/0x20
Jul  7 16:30:01 brtop kernel: [ 1169.081520]  [<c100ab5f>] sysenter_do_call+0x12/0x28
Jul  7 16:30:01 brtop kernel: [ 1169.081523] Code: 44 9d 40 00 8b 4d e0 9c 58 8d 74 26 00 89 c6 fa 90 8d 74 26 00 8b 03 64 03 05 58 2e 87 c1 8b 38 85 ff 0f 84 8f 00 00 00 8b 53 10 <8b> 14 17 89 10 89 f0 50 9d 8d 74 26 00 85 ff 75 64 8b 5b 08 8b 
Jul  7 16:30:01 brtop kernel: [ 1169.081577] EIP: [<c1125e03>] kmem_cache_alloc_trace+0x53/0x100 SS:ESP 0068:d7931f04
Jul  7 16:30:01 brtop kernel: [ 1169.081584] CR2: 0000000001012e00
Jul  7 16:30:01 brtop kernel: [ 1169.081588] ---[ end trace cc8097e307ef6b8e ]---
Jul  7 16:30:11 brtop kernel: [ 1178.377261] BUG: unable to handle kernel paging request at 01012e00
Jul  7 16:30:11 brtop kernel: [ 1178.377267] IP: [<c1125e03>] kmem_cache_alloc_trace+0x53/0x100
Jul  7 16:30:11 brtop kernel: [ 1178.377276] *pdpt = 000000002e576001 *pde = 0000000000000000 
Jul  7 16:30:11 brtop kernel: [ 1178.377280] Oops: 0000 [#3] SMP 
Jul  7 16:30:11 brtop kernel: [ 1178.377283] last sysfs file: /sys/devices/system/cpu/cpu0/topology/core_siblings
Jul  7 16:30:11 brtop kernel: [ 1178.377286] Modules linked in: aesni_intel cryptd aes_i586 aes_generic usb_storage uas rfcomm sco bnep l2cap binfmt_misc vboxnetadp vboxnetflt vboxdrv vmnet dm_crypt vesafb vmblock vsock vmci vmmon pata_pcmcia nfsd exportfs nfs lockd fscache nfs_acl auth_rpcgss sunrpc arc4 tpm_infineon iwlagn pcmcia hp_wmi snd_hda_codec_idt nvidia(P) snd_hda_intel snd_hda_codec snd_hwdep snd_pcm snd_seq_midi uvcvideo snd_rawmidi videodev xhci_hcd snd_seq_midi_event snd_seq joydev btusb sparse_keymap ppdev tpm_tis snd_timer tpm yenta_socket pcmcia_rsrc bluetooth snd_seq_device iwlcore mac80211 tpm_bios r852 sm_common snd pcmcia_core hp_accel nand nand_ids intel_ips cfg80211 nand_ecc mtd lis3lv02d parport_pc soundcore snd_page_alloc input_polldev psmouse serio_raw lp parport firewire_ohci ahci sdhci_pci firewire_core sdhci crc_itu_t libahci video e1000e
Jul  7 16:30:11 brtop kernel: [ 1178.377346] 
Jul  7 16:30:11 brtop kernel: [ 1178.377350] Pid: 1128, comm: irqbalance Tainted: P      D     2.6.38-8-generic-pae #42-Ubuntu Hewlett-Packard HP EliteBook 8740w/1520
Jul  7 16:30:11 brtop kernel: [ 1178.377356] EIP: 0060:[<c1125e03>] EFLAGS: 00010006 CPU: 2
Jul  7 16:30:11 brtop kernel: [ 1178.377359] EIP is at kmem_cache_alloc_trace+0x53/0x100
Jul  7 16:30:11 brtop kernel: [ 1178.377361] EAX: f7887e94 EBX: f7402380 ECX: c118eafb EDX: 00000000
Jul  7 16:30:11 brtop kernel: [ 1178.377363] ESI: 00000246 EDI: 01012e00 EBP: ecd8fe0c ESP: ecd8fde0
Jul  7 16:30:11 brtop kernel: [ 1178.377365]  DS: 007b ES: 007b FS: 00d8 GS: 00e0 SS: 0068
Jul  7 16:30:11 brtop kernel: [ 1178.377368] Process irqbalance (pid: 1128, ti=ecd8e000 task=f75dcbc0 task.ti=ecd8e000)
Jul  7 16:30:11 brtop kernel: [ 1178.377370] Stack:
Jul  7 16:30:11 brtop kernel: [ 1178.377371]  c11454f3 ecd8fde8 00000fcc c118eafb f608b880 00000038 f608b880 000080d0
Jul  7 16:30:11 brtop kernel: [ 1178.377377]  d7ef3600 f69bc450 c157248c ecd8fe3c c118eafb ef1b93b0 d7ef3608 ef1b93b0
Jul  7 16:30:11 brtop kernel: [ 1178.377382]  ecd8fe3c c12272b4 ef1b93b0 f78021b0 d7ef3600 00000000 ef1b93b0 ecd8fe60
Jul  7 16:30:11 brtop kernel: [ 1178.377388] Call Trace:
Jul  7 16:30:11 brtop kernel: [ 1178.377394]  [<c11454f3>] ? d_path+0xc3/0xe0
Jul  7 16:30:11 brtop kernel: [ 1178.377399]  [<c118eafb>] ? sysfs_open_file+0xdb/0x1e0
Jul  7 16:30:11 brtop kernel: [ 1178.377403]  [<c118eafb>] sysfs_open_file+0xdb/0x1e0
Jul  7 16:30:11 brtop kernel: [ 1178.377408]  [<c12272b4>] ? security_dentry_open+0x74/0x80
Jul  7 16:30:11 brtop kernel: [ 1178.377412]  [<c11308e1>] __dentry_open+0xc1/0x280
Jul  7 16:30:11 brtop kernel: [ 1178.377415]  [<c1131c4e>] nameidata_to_filp+0x6e/0x80
Jul  7 16:30:11 brtop kernel: [ 1178.377419]  [<c118ea20>] ? sysfs_open_file+0x0/0x1e0
Jul  7 16:30:11 brtop kernel: [ 1178.377422]  [<c113f0df>] finish_open+0xaf/0x1a0
Jul  7 16:30:11 brtop kernel: [ 1178.377425]  [<c113e988>] ? do_path_lookup+0x68/0x120
Jul  7 16:30:11 brtop kernel: [ 1178.377428]  [<c113f727>] do_filp_open+0x207/0x6e0
Jul  7 16:30:11 brtop kernel: [ 1178.377434]  [<c10f57d8>] ? release_pages+0x1b8/0x1e0
Jul  7 16:30:11 brtop kernel: [ 1178.377439]  [<c1287832>] ? copy_to_user+0x42/0x60
Jul  7 16:30:11 brtop kernel: [ 1178.377443]  [<c118f3f4>] ? sysfs_readdir+0x144/0x280
Jul  7 16:30:11 brtop kernel: [ 1178.377446]  [<c1131cb6>] do_sys_open+0x56/0x120
Jul  7 16:30:11 brtop kernel: [ 1178.377449]  [<c11422b0>] ? filldir+0x0/0xe0
Jul  7 16:30:11 brtop kernel: [ 1178.377452]  [<c1131dae>] sys_open+0x2e/0x40
Jul  7 16:30:11 brtop kernel: [ 1178.377456]  [<c100ab5f>] sysenter_do_call+0x12/0x28
Jul  7 16:30:11 brtop kernel: [ 1178.377458] Code: 44 9d 40 00 8b 4d e0 9c 58 8d 74 26 00 89 c6 fa 90 8d 74 26 00 8b 03 64 03 05 58 2e 87 c1 8b 38 85 ff 0f 84 8f 00 00 00 8b 53 10 <8b> 14 17 89 10 89 f0 50 9d 8d 74 26 00 85 ff 75 64 8b 5b 08 8b 
Jul  7 16:30:11 brtop kernel: [ 1178.377489] EIP: [<c1125e03>] kmem_cache_alloc_trace+0x53/0x100 SS:ESP 0068:ecd8fde0
Jul  7 16:30:11 brtop kernel: [ 1178.377493] CR2: 0000000001012e00
Jul  7 16:30:11 brtop kernel: [ 1178.377496] ---[ end trace cc8097e307ef6b8f ]---
Jul  7 16:30:20 brtop kernel: [ 1188.278493] sr 8:0:0:1: uas_eh_abort_handler tag -1
Jul  7 16:30:20 brtop kernel: [ 1188.278501] sd 8:0:0:0: uas_eh_abort_handler tag 0
Jul  7 16:30:20 brtop kernel: [ 1188.278509] sd 8:0:0:0: uas_eh_device_reset_handler tag 0
Jul  7 16:30:20 brtop kernel: [ 1188.278513] sr 8:0:0:1: uas_eh_device_reset_handler tag -1
Jul  7 16:30:20 brtop kernel: [ 1188.278516] sr 8:0:0:1: uas_eh_target_reset_handler tag -1
Jul  7 16:30:20 brtop kernel: [ 1188.278520] sd 8:0:0:0: uas_eh_bus_reset_handler tag 0
Jul  7 16:30:21 brtop kernel: [ 1188.400722] usb 3-2: reset SuperSpeed USB device using xhci_hcd and address 3
Jul  7 16:30:21 brtop kernel: [ 1188.483517] xhci_hcd 0000:45:00.0: WARN: short transfer on control ep
Jul  7 16:30:21 brtop kernel: [ 1188.483643] xhci_hcd 0000:45:00.0: xHCI xhci_drop_endpoint called with disabled ep f65a2c00
Jul  7 16:30:21 brtop kernel: [ 1188.483649] xhci_hcd 0000:45:00.0: xHCI xhci_drop_endpoint called with disabled ep f65a2c2c
Jul  7 16:30:21 brtop kernel: [ 1188.483653] xhci_hcd 0000:45:00.0: xHCI xhci_drop_endpoint called with disabled ep f65a2c58
Jul  7 16:30:21 brtop kernel: [ 1188.483657] xhci_hcd 0000:45:00.0: xHCI xhci_drop_endpoint called with disabled ep f65a2c84
Jul  7 16:30:21 brtop kernel: [ 1188.483687] BUG: unable to handle kernel paging request at 01012e00
Jul  7 16:30:21 brtop kernel: [ 1188.483691] IP: [<c1125e03>] kmem_cache_alloc_trace+0x53/0x100
Jul  7 16:30:21 brtop kernel: [ 1188.483702] *pdpt = 0000000000000000 *pde = f000f84dc0001c00 
Jul  7 16:30:21 brtop kernel: [ 1188.483708] Oops: 0000 [#4] SMP 
Jul  7 16:30:21 brtop kernel: [ 1188.483712] last sysfs file: /sys/devices/system/cpu/cpu0/topology/core_siblings
Jul  7 16:30:21 brtop kernel: [ 1188.483716] Modules linked in: aesni_intel cryptd aes_i586 aes_generic usb_storage uas rfcomm sco bnep l2cap binfmt_misc vboxnetadp vboxnetflt vboxdrv vmnet dm_crypt vesafb vmblock vsock vmci vmmon pata_pcmcia nfsd exportfs nfs lockd fscache nfs_acl auth_rpcgss sunrpc arc4 tpm_infineon iwlagn pcmcia hp_wmi snd_hda_codec_idt nvidia(P) snd_hda_intel snd_hda_codec snd_hwdep snd_pcm snd_seq_midi uvcvideo snd_rawmidi videodev xhci_hcd snd_seq_midi_event snd_seq joydev btusb sparse_keymap ppdev tpm_tis snd_timer tpm yenta_socket pcmcia_rsrc bluetooth snd_seq_device iwlcore mac80211 tpm_bios r852 sm_common snd pcmcia_core hp_accel nand nand_ids intel_ips cfg80211 nand_ecc mtd lis3lv02d parport_pc soundcore snd_page_alloc input_polldev psmouse serio_raw lp parport firewire_ohci ahci sdhci_pci firewire_core sdhci crc_itu_t libahci video e1000e
Jul  7 16:30:21 brtop kernel: [ 1188.483799] 
Jul  7 16:30:21 brtop kernel: [ 1188.483804] Pid: 3918, comm: scsi_eh_8 Tainted: P      D     2.6.38-8-generic-pae #42-Ubuntu Hewlett-Packard HP EliteBook 8740w/1520
Jul  7 16:30:21 brtop kernel: [ 1188.483812] EIP: 0060:[<c1125e03>] EFLAGS: 00010006 CPU: 2
Jul  7 16:30:21 brtop kernel: [ 1188.483816] EIP is at kmem_cache_alloc_trace+0x53/0x100
Jul  7 16:30:21 brtop kernel: [ 1188.483819] EAX: f7887e94 EBX: f7402380 ECX: f9f004f8 EDX: 00000000
Jul  7 16:30:21 brtop kernel: [ 1188.483822] ESI: 00000246 EDI: 01012e00 EBP: d7e3dd4c ESP: d7e3dd20
Jul  7 16:30:21 brtop kernel: [ 1188.483826]  DS: 007b ES: 007b FS: 00d8 GS: 00e0 SS: 0068
Jul  7 16:30:21 brtop kernel: [ 1188.483829] Process scsi_eh_8 (pid: 3918, ti=d7e3c000 task=d7dc8000 task.ti=d7e3c000)
Jul  7 16:30:21 brtop kernel: [ 1188.483832] Stack:
Jul  7 16:30:21 brtop kernel: [ 1188.483834]  c16b31d2 000004a4 00076149 f9f004f8 00000002 0000002c f3b8d6a0 00008010
Jul  7 16:30:21 brtop kernel: [ 1188.483842]  00000001 00000020 00000010 d7e3dd88 f9f004f8 5d373536 00000020 0000001a
Jul  7 16:30:21 brtop kernel: [ 1188.483850]  01e3dd88 c13d0168 80000380 ec51c000 ea483104 06800303 0000001a f74e99c0
Jul  7 16:30:21 brtop kernel: [ 1188.483857] Call Trace:
Jul  7 16:30:21 brtop kernel: [ 1188.483868]  [<f9f004f8>] ? xhci_ring_alloc+0x38/0x180 [xhci_hcd]
Jul  7 16:30:21 brtop kernel: [ 1188.483876]  [<f9f004f8>] xhci_ring_alloc+0x38/0x180 [xhci_hcd]
Jul  7 16:30:21 brtop kernel: [ 1188.483884]  [<c13d0168>] ? usb_control_msg+0xd8/0x100
Jul  7 16:30:21 brtop kernel: [ 1188.483892]  [<f9f00b01>] xhci_endpoint_init+0x81/0x500 [xhci_hcd]
Jul  7 16:30:21 brtop kernel: [ 1188.483899]  [<c1349a5f>] ? __dev_printk+0x3f/0x80
Jul  7 16:30:21 brtop kernel: [ 1188.483908]  [<f9efdf69>] xhci_add_endpoint+0x139/0x180 [xhci_hcd]
Jul  7 16:30:21 brtop kernel: [ 1188.483915]  [<c13ceb89>] usb_hcd_alloc_bandwidth+0x119/0x2b0
Jul  7 16:30:21 brtop kernel: [ 1188.483920]  [<c13c9d55>] usb_reset_and_verify_device+0x145/0x2f0
Jul  7 16:30:21 brtop kernel: [ 1188.483926]  [<c1035908>] ? default_spin_lock_flags+0x8/0x10
Jul  7 16:30:21 brtop kernel: [ 1188.483935]  [<c15319af>] ? _raw_spin_lock_irqsave+0x2f/0x50
Jul  7 16:30:21 brtop kernel: [ 1188.483939]  [<c13c9fa9>] usb_reset_device+0xa9/0x130
Jul  7 16:30:21 brtop kernel: [ 1188.483944]  [<c1349c1b>] ? dev_printk+0x2b/0x30
Jul  7 16:30:21 brtop kernel: [ 1188.483949]  [<f9e252ce>] uas_eh_bus_reset_handler+0x4e/0x60 [uas]
Jul  7 16:30:21 brtop kernel: [ 1188.483956]  [<c136fdae>] scsi_try_bus_reset+0x3e/0xd0
Jul  7 16:30:21 brtop kernel: [ 1188.483962]  [<c1370d4c>] scsi_eh_bus_reset.clone.7+0x8c/0x1d0
Jul  7 16:30:21 brtop kernel: [ 1188.483967]  [<c1370b5f>] ? scsi_eh_bus_device_reset+0x5f/0x1c0
Jul  7 16:30:21 brtop kernel: [ 1188.483972]  [<c1370eeb>] scsi_eh_ready_devs+0x5b/0x100
Jul  7 16:30:21 brtop kernel: [ 1188.483976]  [<c1371780>] scsi_unjam_host+0xa0/0x1d0
Jul  7 16:30:21 brtop kernel: [ 1188.483980]  [<c1035908>] ? default_spin_lock_flags+0x8/0x10
Jul  7 16:30:21 brtop kernel: [ 1188.483985]  [<c15319af>] ? _raw_spin_lock_irqsave+0x2f/0x50
Jul  7 16:30:21 brtop kernel: [ 1188.483989]  [<c13719ef>] scsi_error_handler+0x13f/0x190
Jul  7 16:30:21 brtop kernel: [ 1188.483996]  [<c10420fe>] ? complete+0x4e/0x60
Jul  7 16:30:21 brtop kernel: [ 1188.484000]  [<c13718b0>] ? scsi_error_handler+0x0/0x190
Jul  7 16:30:21 brtop kernel: [ 1188.484006]  [<c1076704>] kthread+0x74/0x80
Jul  7 16:30:21 brtop kernel: [ 1188.484011]  [<c1076690>] ? kthread+0x0/0x80
Jul  7 16:30:21 brtop kernel: [ 1188.484016]  [<c100b0fe>] kernel_thread_helper+0x6/0x10
Jul  7 16:30:21 brtop kernel: [ 1188.484019] Code: 44 9d 40 00 8b 4d e0 9c 58 8d 74 26 00 89 c6 fa 90 8d 74 26 00 8b 03 64 03 05 58 2e 87 c1 8b 38 85 ff 0f 84 8f 00 00 00 8b 53 10 <8b> 14 17 89 10 89 f0 50 9d 8d 74 26 00 85 ff 75 64 8b 5b 08 8b 
Jul  7 16:30:21 brtop kernel: [ 1188.484063] EIP: [<c1125e03>] kmem_cache_alloc_trace+0x53/0x100 SS:ESP 0068:d7e3dd20
Jul  7 16:30:21 brtop kernel: [ 1188.484069] CR2: 0000000001012e00
Jul  7 16:30:21 brtop kernel: [ 1188.484073] ---[ end trace cc8097e307ef6b90 ]---
Jul  7 16:30:45 brtop kernel: [ 1212.408988] BUG: unable to handle kernel paging request at 01012e00
Jul  7 16:30:45 brtop kernel: [ 1212.408998] IP: [<c1125e03>] kmem_cache_alloc_trace+0x53/0x100
Jul  7 16:30:45 brtop kernel: [ 1212.409012] *pdpt = 0000000037698001 *pde = 0000000000000000 
Jul  7 16:30:45 brtop kernel: [ 1212.409019] Oops: 0000 [#5] SMP 
Jul  7 16:30:45 brtop kernel: [ 1212.409023] last sysfs file: /sys/devices/system/cpu/cpu0/topology/core_siblings
Jul  7 16:30:45 brtop kernel: [ 1212.409028] Modules linked in: aesni_intel cryptd aes_i586 aes_generic usb_storage uas rfcomm sco bnep l2cap binfmt_misc vboxnetadp vboxnetflt vboxdrv vmnet dm_crypt vesafb vmblock vsock vmci vmmon pata_pcmcia nfsd exportfs nfs lockd fscache nfs_acl auth_rpcgss sunrpc arc4 tpm_infineon iwlagn pcmcia hp_wmi snd_hda_codec_idt nvidia(P) snd_hda_intel snd_hda_codec snd_hwdep snd_pcm snd_seq_midi uvcvideo snd_rawmidi videodev xhci_hcd snd_seq_midi_event snd_seq joydev btusb sparse_keymap ppdev tpm_tis snd_timer tpm yenta_socket pcmcia_rsrc bluetooth snd_seq_device iwlcore mac80211 tpm_bios r852 sm_common snd pcmcia_core hp_accel nand nand_ids intel_ips cfg80211 nand_ecc mtd lis3lv02d parport_pc soundcore snd_page_alloc input_polldev psmouse serio_raw lp parport firewire_ohci ahci sdhci_pci firewire_core sdhci crc_itu_t libahci video e1000e
Jul  7 16:30:45 brtop kernel: [ 1212.409129] 
Jul  7 16:30:45 brtop kernel: [ 1212.409134] Pid: 2345, comm: python Tainted: P      D     2.6.38-8-generic-pae #42-Ubuntu Hewlett-Packard HP EliteBook 8740w/1520
Jul  7 16:30:45 brtop kernel: [ 1212.409144] EIP: 0060:[<c1125e03>] EFLAGS: 00210006 CPU: 2
Jul  7 16:30:45 brtop kernel: [ 1212.409149] EIP is at kmem_cache_alloc_trace+0x53/0x100
Jul  7 16:30:45 brtop kernel: [ 1212.409153] EAX: f7887e94 EBX: f7402380 ECX: c1444a59 EDX: 00000000
Jul  7 16:30:45 brtop kernel: [ 1212.409157] ESI: 00200246 EDI: 01012e00 EBP: ec7f5ec4 ESP: ec7f5e98
Jul  7 16:30:45 brtop kernel: [ 1212.409161]  DS: 007b ES: 007b FS: 00d8 GS: 00e0 SS: 0068
Jul  7 16:30:45 brtop kernel: [ 1212.409165] Process python (pid: 2345, ti=ec7f4000 task=f6ad8000 task.ti=ec7f4000)
Jul  7 16:30:45 brtop kernel: [ 1212.409168] Stack:
Jul  7 16:30:45 brtop kernel: [ 1212.409170]  00000001 ec7f5e30 ec7f5ea4 c1444a59 c1444a3b 00000040 000001c0 000000d0
Jul  7 16:30:45 brtop kernel: [ 1212.409180]  eaaeb100 00000000 c1955180 ec7f5ed4 c1444a59 00000001 f750e400 ec7f5ee4
Jul  7 16:30:45 brtop kernel: [ 1212.409190]  c1148201 00000001 c1940b40 ec7f5ef4 c1148950 00000001 00000001 ec7f5f00
Jul  7 16:30:45 brtop kernel: [ 1212.409199] Call Trace:
Jul  7 16:30:45 brtop kernel: [ 1212.409210]  [<c1444a59>] ? sock_alloc_inode+0x39/0xa0
Jul  7 16:30:45 brtop kernel: [ 1212.409216]  [<c1444a3b>] ? sock_alloc_inode+0x1b/0xa0
Jul  7 16:30:45 brtop kernel: [ 1212.409222]  [<c1444a59>] sock_alloc_inode+0x39/0xa0
Jul  7 16:30:45 brtop kernel: [ 1212.409227]  [<c1148201>] alloc_inode+0x21/0x80
Jul  7 16:30:45 brtop kernel: [ 1212.409232]  [<c1148950>] new_inode+0x20/0x70
Jul  7 16:30:45 brtop kernel: [ 1212.409237]  [<c1445356>] sock_alloc+0x16/0x60
Jul  7 16:30:45 brtop kernel: [ 1212.409241]  [<c14462d5>] __sock_create+0x75/0x280
Jul  7 16:30:45 brtop kernel: [ 1212.409247]  [<c144655d>] sock_create+0x3d/0x50
Jul  7 16:30:45 brtop kernel: [ 1212.409251]  [<c1446616>] sys_socket+0x46/0x70
Jul  7 16:30:45 brtop kernel: [ 1212.409256]  [<c14478e8>] sys_socketcall+0x88/0x2a0
Jul  7 16:30:45 brtop kernel: [ 1212.409263]  [<c1287832>] ? copy_to_user+0x42/0x60
Jul  7 16:30:45 brtop kernel: [ 1212.409271]  [<c105e1fe>] ? sys_time+0x1e/0x60
Jul  7 16:30:45 brtop kernel: [ 1212.409277]  [<c100ab5f>] sysenter_do_call+0x12/0x28
Jul  7 16:30:45 brtop kernel: [ 1212.409280] Code: 44 9d 40 00 8b 4d e0 9c 58 8d 74 26 00 89 c6 fa 90 8d 74 26 00 8b 03 64 03 05 58 2e 87 c1 8b 38 85 ff 0f 84 8f 00 00 00 8b 53 10 <8b> 14 17 89 10 89 f0 50 9d 8d 74 26 00 85 ff 75 64 8b 5b 08 8b 
Jul  7 16:30:45 brtop kernel: [ 1212.409334] EIP: [<c1125e03>] kmem_cache_alloc_trace+0x53/0x100 SS:ESP 0068:ec7f5e98
Jul  7 16:30:45 brtop kernel: [ 1212.409342] CR2: 0000000001012e00
Jul  7 16:30:45 brtop kernel: [ 1212.409347] ---[ end trace cc8097e307ef6b91 ]---
Jul  7 16:30:50 brtop kernel: [ 1218.207879] BUG: unable to handle kernel paging request at 01012e00
Jul  7 16:30:50 brtop kernel: [ 1218.207886] IP: [<c11262f0>] __kmalloc+0xb0/0x1a0
Jul  7 16:30:50 brtop kernel: [ 1218.207895] *pdpt = 000000002e5a3001 *pde = 0000000000000000 
Jul  7 16:30:50 brtop kernel: [ 1218.207898] Oops: 0000 [#6] SMP 
Jul  7 16:30:50 brtop kernel: [ 1218.207900] last sysfs file: /sys/devices/system/cpu/cpu0/topology/core_siblings
Jul  7 16:30:50 brtop kernel: [ 1218.207903] Modules linked in: aesni_intel cryptd aes_i586 aes_generic usb_storage uas rfcomm sco bnep l2cap binfmt_misc vboxnetadp vboxnetflt vboxdrv vmnet dm_crypt vesafb vmblock vsock vmci vmmon pata_pcmcia nfsd exportfs nfs lockd fscache nfs_acl auth_rpcgss sunrpc arc4 tpm_infineon iwlagn pcmcia hp_wmi snd_hda_codec_idt nvidia(P) snd_hda_intel snd_hda_codec snd_hwdep snd_pcm snd_seq_midi uvcvideo snd_rawmidi videodev xhci_hcd snd_seq_midi_event snd_seq joydev btusb sparse_keymap ppdev tpm_tis snd_timer tpm yenta_socket pcmcia_rsrc bluetooth snd_seq_device iwlcore mac80211 tpm_bios r852 sm_common snd pcmcia_core hp_accel nand nand_ids intel_ips cfg80211 nand_ecc mtd lis3lv02d parport_pc soundcore snd_page_alloc input_polldev psmouse serio_raw lp parport firewire_ohci ahci sdhci_pci firewire_core sdhci crc_itu_t libahci video e1000e
Jul  7 16:30:50 brtop kernel: [ 1218.207950] 
Jul  7 16:30:50 brtop kernel: [ 1218.207953] Pid: 1340, comm: Xorg Tainted: P      D     2.6.38-8-generic-pae #42-Ubuntu Hewlett-Packard HP EliteBook 8740w/1520
Jul  7 16:30:50 brtop kernel: [ 1218.207957] EIP: 0060:[<c11262f0>] EFLAGS: 00213006 CPU: 2
Jul  7 16:30:50 brtop kernel: [ 1218.207960] EIP is at __kmalloc+0xb0/0x1a0
Jul  7 16:30:50 brtop kernel: [ 1218.207961] EAX: f7887e94 EBX: f7402380 ECX: 01012e00 EDX: 00000000
Jul  7 16:30:50 brtop kernel: [ 1218.207963] ESI: 00203246 EDI: 00000034 EBP: ecd17ddc ESP: ecd17db0
Jul  7 16:30:50 brtop kernel: [ 1218.207964]  DS: 007b ES: 007b FS: 00d8 GS: 00e0 SS: 0068
Jul  7 16:30:50 brtop kernel: [ 1218.207966] Process Xorg (pid: 1340, ti=ecd16000 task=ee840000 task.ti=ecd16000)
Jul  7 16:30:50 brtop kernel: [ 1218.207968] Stack:
Jul  7 16:30:50 brtop kernel: [ 1218.207969]  ecd17de4 00203246 ee0d5cc0 f992cfe6 0000000f f94b1ca7 000002d0 01012e00
Jul  7 16:30:50 brtop kernel: [ 1218.207973]  00000034 ee0d5ea8 00000000 ecd17df4 f992cfe6 f992cfe6 f67fea00 00000000
Jul  7 16:30:50 brtop kernel: [ 1218.207977]  caf00145 ee0d5ea8 f9902175 ee0d5ea8 00000034 f943f340 ee0d5ea8 00000034
Jul  7 16:30:50 brtop kernel: [ 1218.207981] Call Trace:
Jul  7 16:30:50 brtop kernel: [ 1218.208174]  [<f992cfe6>] ? os_alloc_mem+0x46/0xd0 [nvidia]
Jul  7 16:30:50 brtop kernel: [ 1218.208297]  [<f94b1ca7>] ? _nv003335rm+0xe3/0x103 [nvidia]
Jul  7 16:30:50 brtop kernel: [ 1218.208455]  [<f992cfe6>] os_alloc_mem+0x46/0xd0 [nvidia]
Jul  7 16:30:50 brtop kernel: [ 1218.208613]  [<f992cfe6>] ? os_alloc_mem+0x46/0xd0 [nvidia]
Jul  7 16:30:50 brtop kernel: [ 1218.208775]  [<f9902175>] _nv022878rm+0x17/0x25 [nvidia]
Jul  7 16:30:50 brtop kernel: [ 1218.208880]  [<f943f340>] ? _nv000603rm+0x33/0xc3 [nvidia]
Jul  7 16:30:50 brtop kernel: [ 1218.208987]  [<f9444b25>] ? _nv000349rm+0x2b7/0x32c [nvidia]
Jul  7 16:30:50 brtop kernel: [ 1218.209104]  [<f949513b>] ? _nv003758rm+0x27a/0x7c3 [nvidia]
Jul  7 16:30:50 brtop kernel: [ 1218.209221]  [<f9495a36>] ? _nv003443rm+0x1bb/0x1d6 [nvidia]
Jul  7 16:30:50 brtop kernel: [ 1218.209338]  [<f9494eb5>] ? _nv002560rm+0x81/0x8d [nvidia]
Jul  7 16:30:50 brtop kernel: [ 1218.209450]  [<f946b8d0>] ? _nv002026rm+0xb7/0x149 [nvidia]
Jul  7 16:30:50 brtop kernel: [ 1218.209611]  [<f990f130>] ? _nv002413rm+0x284/0x611 [nvidia]
Jul  7 16:30:50 brtop kernel: [ 1218.209770]  [<f990bd9d>] ? rm_ioctl+0x3e/0x6d [nvidia]
Jul  7 16:30:50 brtop kernel: [ 1218.209930]  [<f9926bb9>] ? nv_kern_ioctl+0x149/0x4a0 [nvidia]
Jul  7 16:30:50 brtop kernel: [ 1218.210089]  [<f9926f10>] ? nv_kern_unlocked_ioctl+0x0/0x30 [nvidia]
Jul  7 16:30:50 brtop kernel: [ 1218.210248]  [<f9926f30>] ? nv_kern_unlocked_ioctl+0x20/0x30 [nvidia]
Jul  7 16:30:50 brtop kernel: [ 1218.210253]  [<c1141ecb>] ? do_vfs_ioctl+0x7b/0x2e0
Jul  7 16:30:50 brtop kernel: [ 1218.210255]  [<c11421b7>] ? sys_ioctl+0x87/0x90
Jul  7 16:30:50 brtop kernel: [ 1218.210259]  [<c100ab5f>] ? sysenter_do_call+0x12/0x28
Jul  7 16:30:50 brtop kernel: [ 1218.210261] Code: e0 9c 58 8d 74 26 00 89 c6 fa 90 8d 74 26 00 8b 03 64 03 05 58 2e 87 c1 8b 10 85 d2 89 55 f0 0f 84 d8 00 00 00 8b 53 10 8b 4d f0 <8b> 14 11 89 10 89 f0 50 9d 8d 74 26 00 8b 75 f0 85 f6 75 74 8b 
Jul  7 16:30:50 brtop kernel: [ 1218.210285] EIP: [<c11262f0>] __kmalloc+0xb0/0x1a0 SS:ESP 0068:ecd17db0
Jul  7 16:30:50 brtop kernel: [ 1218.210289] CR2: 0000000001012e00
Jul  7 16:30:50 brtop kernel: [ 1218.210292] ---[ end trace cc8097e307ef6b92 ]---
Jul  7 16:31:10 brtop kernel: [ 1238.078881] usb 3-2: USB disconnect, address 3
Jul  7 16:31:10 brtop kernel: [ 1238.079198] usb 3-2: URB BAD STATUS -108
Jul  7 16:31:10 brtop kernel: [ 1238.079203] usb 3-2: URB BAD STATUS -108
```

---

### Post by gyurma on 2011-07-08
Thanks! That's exactly the same, how my logs are also looking like.

---

### Post by kimangroo on 2011-07-09
Ok if you guys still have the virtual cd for encryption, that's what's causing the crash as far as I can tell.

When I had the virtual cd it worked fine in usb 2.0 ports and insta-crashed ubuntu when I plugged it into the usb 3.0

For my iomega prestige drive I solved that problem by removing the hidden partition with the virtual cd using the updated iomega encryption utility, but you need to do it on windows:

[https://iomega-na-en.custhelp.com/app/answers/detail/a_id/24749](https://iomega-na-en.custhelp.com/app/answers/detail/a_id/24749)

download utility (need to register):

[https://iomega-na-en.custhelp.com/app/answers/custom_detail/a_id/26019](https://iomega-na-en.custhelp.com/app/answers/custom_detail/a_id/26019)

I think most manufacturers now provide a utility to remove the virtual cds on their drives.

Now I no longer have the virtual cd and ubuntu doesn't crash anymore but it just doesn't recognise the drive in the usb 3.0 port, so not much improvement (but I didn't want the virtual cd anyway).

I think it's some kernel or driver thing, given the lack of response on the many forums I've posted on, I don't think it's going to get solved anytime soon.

It's annoying because I'm finding my ubuntu experience is yet again suffering a death of a thousand cuts again... the main stuff is great, but all the niggly bugs and stuff that doesn't quite work as it should mean that I find myself using windows more and more...

Right now the list (of problems I haven't been able to solve) includes:

1. Streaming some video in firefox (I have to load it in movie player instead)
2. Very temperamental touchpad. Sometimes works, sometimes skips all over the place. Can't switch it on and off when typing.(basically unusable)
3. No internal microphone.
4. No usb 3.0
5. No hybrid graphics

bleh...

---

### Post by westie457 on 2011-07-09
Hello This is only an idea and might not be the problem at all. I have read somewhere in these forums about these large capacity drives and the partition-tables. Absolutely not sure whether they are normal DOS-type with mbr or they are GPT-type. One of them struggles with the size of the partition and the other sometimes causes problems of a different kind. This might help to shed some light around. [http://ubuntuforums.org/showthread.php?t=1547186](http://ubuntuforums.org/showthread.php?t=1547186)

---

### Post by gyurma on 2011-07-10
Here is how my crash looks like. Interesting, that not the whole system crashes, just parts of it, since I still can type and send you guys this log:
How is that possible?
```
[  980.790330] hub 8-0:1.0: unable to enumerate USB device on port 3
[  981.379127] usb 8-1: new SuperSpeed USB device using xhci_hcd and address 3
[  981.418983] xhci_hcd 0000:02:00.0: WARN: short transfer on control ep
[  981.425113] xhci_hcd 0000:02:00.0: WARN: short transfer on control ep
[  981.430837] xhci_hcd 0000:02:00.0: WARN: short transfer on control ep
[  981.436972] xhci_hcd 0000:02:00.0: WARN: short transfer on control ep
[  981.467729] xhci_hcd 0000:02:00.0: WARN: short transfer on control ep
[  981.474984] xhci_hcd 0000:02:00.0: WARN: short transfer on control ep
[  981.518685] xhci_hcd 0000:02:00.0: WARN no SS endpoint bMaxBurst
[  981.568340] xhci_hcd 0000:02:00.0: WARN: short transfer on control ep
[  981.568729] scsi6 : uas
[  981.569926] usbcore: registered new interface driver uas
[  981.576840] scsi 6:0:0:0: Direct-Access     OEM      Ext Hard Disk    0000 PQ: 0 ANSI: 5
[  981.584069] Initializing USB Mass Storage driver...
[  981.584136] usbcore: registered new interface driver usb-storage
[  981.584137] USB Mass Storage support registered.
[  981.736840] scsi 6:0:0:1: CD-ROM            Virtual  CDROM                 PQ: 0 ANSI: 0
[  981.737372] sd 6:0:0:0: Attached scsi generic sg4 type 0
[  981.883466] sd 6:0:0:0: [sdc] 244011446 4096-byte logical blocks: (999 GB/930 GiB)
[  981.929317] sr2: scsi-1 drive
[  981.929631] sr 6:0:0:1: Attached scsi CD-ROM sr2
[  981.930122] sr 6:0:0:1: Attached scsi generic sg5 type 5
[  982.172292] sd 6:0:0:0: [sdc] Write Protect is off
[  982.172301] sd 6:0:0:0: [sdc] Mode Sense: 00 00 00 00
[  982.265278] sd 6:0:0:0: [sdc] Cache data unavailable
[  982.265285] sd 6:0:0:0: [sdc] Assuming drive cache: write through
[  982.411953] sr2: Hmm, seems the drive doesn't support multisession CD's
[  982.459312] xhci_hcd 0000:02:00.0: WARN: babble error on endpoint
[  982.459657] xhci_hcd 0000:02:00.0: WARN Set TR Deq Ptr cmd invalid because of stream ID configuration
[  982.459943] xhci_hcd 0000:02:00.0: ERROR Transfer event for disabled endpoint or incorrect stream ring
[ 1013.040159] sr 6:0:0:1: uas_eh_abort_handler tag -1
[ 1013.040168] sd 6:0:0:0: uas_eh_abort_handler tag 0
[ 1013.040180] sd 6:0:0:0: uas_eh_device_reset_handler tag 0
[ 1013.040187] sr 6:0:0:1: uas_eh_device_reset_handler tag -1
[ 1013.040194] sr 6:0:0:1: uas_eh_target_reset_handler tag -1
[ 1013.040200] sd 6:0:0:0: uas_eh_bus_reset_handler tag 0
[ 1013.169590] usb 8-1: reset SuperSpeed USB device using xhci_hcd and address 3
[ 1013.246077] xhci_hcd 0000:02:00.0: WARN: short transfer on control ep
[ 1013.246104] xhci_hcd 0000:02:00.0: xHCI xhci_drop_endpoint called with disabled ep ffff880205537a00
[ 1013.246113] xhci_hcd 0000:02:00.0: xHCI xhci_drop_endpoint called with disabled ep ffff880205537a40
[ 1013.246121] xhci_hcd 0000:02:00.0: xHCI xhci_drop_endpoint called with disabled ep ffff880205537a80
[ 1013.246127] xhci_hcd 0000:02:00.0: xHCI xhci_drop_endpoint called with disabled ep ffff880205537ac0
[ 1013.367086] xhci_hcd 0000:02:00.0: WARN no SS endpoint bMaxBurst
[ 1013.487922] usb 8-1: URB BAD STATUS -108
[ 1013.487931] usb 8-1: URB BAD STATUS -108
[ 1013.487949] sd 6:0:0:0: Device offlined - not ready after error recovery
[ 1013.487955] sr 6:0:0:1: Device offlined - not ready after error recovery
[ 1013.488026] sd 6:0:0:0: rejecting I/O to offline device
[ 1013.488041] sr2: CDROM (ioctl) error, command: 
[ 1013.488047] sd 6:0:0:0: rejecting I/O to offline device
[ 1013.488054] Read TOC/PMA/ATIP
[ 1013.488059] sd 6:0:0:0: [sdc] READ CAPACITY(16) failed
[ 1013.488065] sd 6:0:0:0: [sdc]  Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK
[ 1013.488073] sd 6:0:0:0: [sdc] Sense not available.
[ 1013.488078]  43
[ 1013.488082] sd 6:0:0:0: rejecting I/O to offline device
[ 1013.488088]  00
[ 1013.488092] sd 6:0:0:0: rejecting I/O to offline device
[ 1013.488096]  00 00 00 00 00 00 0c 00
[ 1013.488109] sr: Sense Key : No Sense [current] 
[ 1013.488117] sr: Add. Sense: No additional sense information
[ 1013.488127] sd 6:0:0:0: rejecting I/O to offline device
[ 1013.488134] sd 6:0:0:0: [sdc] READ CAPACITY failed
[ 1013.488139] sd 6:0:0:0: [sdc]  Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK
[ 1013.488147] sd 6:0:0:0: [sdc] Sense not available.
[ 1013.488151] sr 6:0:0:1: rejecting I/O to offline device
[ 1013.488162] sd 6:0:0:0: rejecting I/O to offline device
[ 1013.488167] sr 6:0:0:1: rejecting I/O to offline device
[ 1013.488177] sr 6:0:0:1: rejecting I/O to offline device
[ 1013.488182] sd 6:0:0:0: rejecting I/O to offline device
[ 1013.488193] sd 6:0:0:0: rejecting I/O to offline device
[ 1013.488208] sd 6:0:0:0: rejecting I/O to offline device
[ 1013.488215] sd 6:0:0:0: [sdc] Asking for cache data failed
[ 1013.488220] sd 6:0:0:0: [sdc] Assuming drive cache: write through
[ 1013.488226] sr 6:0:0:1: rejecting I/O to offline device
[ 1013.488235] sdc: detected capacity change from 999470882816 to 0
[ 1013.488251] sr 6:0:0:1: rejecting I/O to offline device
[ 1013.488335] sr 6:0:0:1: rejecting I/O to offline device
[ 1013.488379] sd 6:0:0:0: [sdc] Attached SCSI disk
[ 1013.499266] general protection fault: 0000 [#1] SMP 
[ 1013.499277] last sysfs file: /sys/devices/pci0000:00/0000:00:03.0/0000:02:00.0/usb8/8-1/serial
[ 1013.499283] CPU 2 
[ 1013.499287] Modules linked in: usb_storage uas parport_pc ppdev dm_crypt snd_hda_codec_hdmi cx22702 isl6421 cx24116 wm8775 cx88_dvb cx88_vp3054_i2c videobuf_dvb dvb_core rc_hauppauge_new tuner_simple tuner_types tda9887 tda8290 nvidia(P) cx8800 cx8802 ir_lirc_codec lirc_dev tuner ir_sony_decoder ir_jvc_decoder ir_rc6_decoder cx88_alsa ir_rc5_decoder snd_hda_codec_realtek cx88xx ir_nec_decoder rc_core snd_usb_audio snd_usbmidi_lib i2c_algo_bit snd_hda_intel snd_hda_codec snd_hwdep snd_pcm snd_seq_midi snd_rawmidi snd_seq_midi_event tveeprom uvcvideo v4l2_common joydev edac_core snd_seq sp5100_tco videodev videobuf_dma_sg i2c_piix4 snd_timer snd_seq_device psmouse snd hid_logitech videobuf_core v4l2_compat_ioctl32 btcx_risc k10temp edac_mce_amd serio_raw soundcore snd_page_alloc ff_memless lp parport reiserfs usbhid hid ahci r8169 xhci_hcd pata_atiixp libahci
[ 1013.499407] 
[ 1013.499414] Pid: 2127, comm: blkid Tainted: P            2.6.38-8-generic #42-Ubuntu MICRO-STAR INTERNATIONAL CO.,LTD MS-7576/790GX-G65 (MS-7576)        
[ 1013.499429] RIP: 0010:[<ffffffff813bd158>]  [<ffffffff813bd158>] kobj_lookup+0x68/0x1e0
[ 1013.499447] RSP: 0018:ffff880204b33b58  EFLAGS: 00010286
[ 1013.499452] RAX: 000000000000000f RBX: a000140101012e00 RCX: 000000000000000f
[ 1013.499459] RDX: 0000000000000000 RSI: 0000000000800020 RDI: ffffffff81a57660
[ 1013.499464] RBP: ffff880204b33bb8 R08: 0000000000000004 R09: ffff88022f80b3e0
[ 1013.499470] R10: ffff88022f80b3e0 R11: 0000000000000000 R12: 0000000000800020
[ 1013.499476] R13: 0000000000800020 R14: ffffffffffffffff R15: ffff88021f440800
[ 1013.499483] FS:  00007f9a99f47760(0000) GS:ffff8800cfd00000(0000) knlGS:00000000f6028710
[ 1013.499490] CS:  0010 DS: 0000 ES: 0000 CR0: 0000000080050033
[ 1013.499495] CR2: 00007f9a9966cfe0 CR3: 0000000205753000 CR4: 00000000000006e0
[ 1013.499501] DR0: 0000000000000000 DR1: 0000000000000000 DR2: 0000000000000000
[ 1013.499508] DR3: 0000000000000000 DR6: 00000000ffff0ff0 DR7: 0000000000000400
[ 1013.499514] Process blkid (pid: 2127, threadinfo ffff880204b32000, task ffff8801ef1b5b80)
[ 1013.499519] Stack:
[ 1013.499522]  000280da00000000 ffff88022f80d400 0000000000000008 ffff880204b33c14
[ 1013.499532]  ffff880204b33b98 ffff880204b33c64 ffff88021bdab4e0 0000000000800020
[ 1013.499542]  ffff880204b33c14 0000000000000000 ffff88021bdab420 000000000000001d
[ 1013.499551] Call Trace:
[ 1013.499562]  [<ffffffff812ca734>] get_gendisk+0xe4/0x100
[ 1013.499572]  [<ffffffff8119976e>] __blkdev_get+0x10e/0x3b0
[ 1013.499581]  [<ffffffff81199a71>] blkdev_get+0x61/0x2a0
[ 1013.499591]  [<ffffffff815c2cbe>] ? _raw_spin_lock+0xe/0x20
[ 1013.499599]  [<ffffffff81199cb0>] ? blkdev_open+0x0/0x80
[ 1013.499607]  [<ffffffff81199d15>] blkdev_open+0x65/0x80
[ 1013.499616]  [<ffffffff81162cee>] __dentry_open+0xce/0x2f0
[ 1013.499624]  [<ffffffff8116ef33>] ? generic_permission+0x23/0xc0
[ 1013.499632]  [<ffffffff811641e1>] nameidata_to_filp+0x71/0x80
[ 1013.499641]  [<ffffffff811733c8>] finish_open+0xc8/0x1b0
[ 1013.499648]  [<ffffffff811725b7>] ? do_path_lookup+0x87/0x160
[ 1013.499657]  [<ffffffff81173b88>] do_filp_open+0x2c8/0x7c0
[ 1013.499665]  [<ffffffff81131d4d>] ? handle_mm_fault+0x16d/0x250
[ 1013.499675]  [<ffffffff812e6c47>] ? __strncpy_from_user+0x27/0x60
[ 1013.499684]  [<ffffffff81180ea7>] ? alloc_fd+0xf7/0x150
[ 1013.499691]  [<ffffffff8116425a>] do_sys_open+0x6a/0x150
[ 1013.499699]  [<ffffffff81164360>] sys_open+0x20/0x30
[ 1013.499707]  [<ffffffff8100c002>] system_call_fastpath+0x16/0x1b
[ 1013.499712] Code: c1 e0 08 29 d0 29 c1 48 89 4d b0 49 8b bf f8 07 00 00 e8 dc 42 20 00 48 8b 55 b0 49 8b 1c d7 48 85 db 0f 84 f7 00 00 00 0f 1f 00 <8b> 53 08 41 39 d4 0f 82 dc 00 00 00 48 8b 4b 10 89 d0 48 83 e9 
[ 1013.499779] RIP  [<ffffffff813bd158>] kobj_lookup+0x68/0x1e0
[ 1013.499789]  RSP <ffff880204b33b58>
[ 1013.499795] ---[ end trace ac1132336dba76b2 ]---

```

---

### Post by Bart Robeyns on 2011-07-10
The stalls and crashes seem pretty random - I've had the situation where any process I tried to lauch (e.g. bash) simply crashed. 
The GPF that figures in the reports might be caused by something (a driver?) writing erratically beyond it's own memory structures and thus corrupting other memory spaces.
Any idea how to pinpoint this? I've got no experience in Linux development, but am willing to run any tests/setups of interest...
Or should we take this to the usb-linux list? (Their FAQ states that we should first take it up with the forums of the specific distro we're running...)

@[westie457]("http://ubuntuforums.org/member.php?u=970779"): In the thread you refer to there's no mention of the symptoms described in this thread (drive not recognized on USB 3.0, random system crashes after plugging it in). What relation do you see?

@[kimangroo]("http://ubuntuforums.org/member.php?u=479244"): In some defense to Ubuntu (and quite off-topic): I actually tried to remove the virtual cd, but iomega's own tool (both the supplied version and the latest release) failed to recognize the drive on three different Windows computers (one 7, two Vista's): the problems we're experiencing might just as well be due to some crappy firmware.

---

### Post by kimangroo on 2011-07-18
> **Bart Robeyns said:**
> Or should we take this to the usb-linux list? (Their FAQ states that we should first take it up with the forums of the specific distro we're running...)

 In some defense to Ubuntu (and quite off-topic): I actually tried to remove the virtual cd, but iomega's own tool (both the supplied version and the latest release) failed to recognize the drive on three different Windows computers (one 7, two Vista's): the problems we're experiencing might just as well be due to some crappy firmware.

I think it's time to hit the usb-linux list, I've posted about this in lots of forums now with very little feedback.

I'm actually very busy now, and wanted to solve the problem with the hard disk before I put all my data on it, as I don't have time to faff about moving it all around again. I've resigned myself to usb 2.0. But it would be interesting to hear what anyone on that list has to say.

As far as iomega encryption utility is concerned it didn't recognise my first drive I had either (I returned it) but I think that was because I had repartitioned it in an attempt to remove the virtual cd.

Also it's definitely not a linux compatibility problem as I can get it to work fine using the parted magic live cd. I tested the copying speeds to and it does seem to be using usb 3.0. Maybe you could try it out with your drives as well to confirm.

---

### Post by drhex on 2011-09-03
I bought an Iomega prestige and Seagate Goflex, both 2.5" and 1.5TB. 
The iomega has the problems described above (causes hangs and tries to mount a virtual CD) when on USB3.0. It operates at a respectable 36MB/sec on USB2.0, though.  The Seagate works fine in USB3.0 though, whish I had known that before.  (And now there's a fee to the copyright mafiaa when buying external drives in Sweden, argh!)

---

### Post by Filiberke on 2012-01-05
Hey,

had the same problem, searched for a week, but solved it.

You need to do 2 separate things:

1) remove the Virtual CD partition on your HD, using the Iomega Encryption Utility (it's on the disk, or you can download it). This has to be done on a Windows computer.

2) add the line " blacklist uas " to the file  /etc/modprobe.d/blacklist.conf

It will work.

Greetings :)

---

