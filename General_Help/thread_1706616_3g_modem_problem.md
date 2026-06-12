---
title: "3g modem problem"
date: 2011-03-14
forum: General Help
---

### Post by L Style on 2011-03-14
I have safaricom 3g modem but it's not work in ubuntu 10.04.  how can I fix this. It's work in windows xp. please tell me how to fix this

[IMG]http://img222.imageshack.us/img222/884/03142011387.jpg[/IMG]


[IMG]http://img20.imageshack.us/img20/134/img0073ax.jpg[/IMG]

This is my modem.

---

### Post by L Style on 2011-03-15
Please help me guys

---

### Post by vivek.pandey on 2011-03-15
there are some hardwares which do not work in ubuntu 10.04. my bsnl evdo modem was one amomg them..actually ubuntu 10.04 treats them as normal usb storage device....anyways lets see if safari works or not

type in terminal lsusb and see if it detects your modem

---

### Post by dineshs on 2011-03-15
Does this(post #7) help?
[http://ubuntuforums.org/showthread.php?t=1695102&highlight=bsnl](http://ubuntuforums.org/showthread.php?t=1695102&highlight=bsnl)

---

### Post by L Style on 2011-03-21
> **neo_aryan said:**
> there are some hardwares which do not work in ubuntu 10.04. my bsnl evdo modem was one amomg them..actually ubuntu 10.04 treats them as normal usb storage device....anyways lets see if safari works or not

type in terminal lsusb and see if it detects your modem

lachitha@lachitha-desktop:~$ lsusb
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 05c6:0018 Qualcomm, Inc. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


This is dmesg 

[    0.000000]  modified: 0000000000100000 - 0000000015fd0000 (usable)
[    0.000000]  modified: 0000000015fd0000 - 0000000015fdf000 (ACPI data)
[    0.000000]  modified: 0000000015fdf000 - 0000000016000000 (ACPI NVS)
[    0.000000]  modified: 00000000fffc0000 - 0000000100000000 (reserved)
[    0.000000] initial memory mapped : 0 - 00c00000
[    0.000000] init_memory_mapping: 0000000000000000-0000000015fd0000
[    0.000000] Using x86 segment limits to approximate NX protection
[    0.000000]  0000000000 - 0000400000 page 4k
[    0.000000]  0000400000 - 0015c00000 page 2M
[    0.000000]  0015c00000 - 0015fd0000 page 4k
[    0.000000] kernel direct mapping tables up to 15fd0000 @ 10000-15000
[    0.000000] RAMDISK: 10082000 - 1081b73d
[    0.000000] ACPI: RSDP 000f6750 00014 (v00 ACPIAM)
[    0.000000] ACPI: RSDT 15fd0000 00030 (v01 A M I  OEMRSDT  07000415 MSFT 00000097)
[    0.000000] ACPI: FACP 15fd0200 00081 (v02 A M I  OEMFACP  07000415 MSFT 00000097)
[    0.000000] ACPI: DSDT 15fd03f0 0343E (v01   M863    M863G 00000000 INTL 02002026)
[    0.000000] ACPI: FACS 15fdf000 00040
[    0.000000] ACPI: APIC 15fd0390 00054 (v01 A M I  OEMAPIC  07000415 MSFT 00000097)
[    0.000000] ACPI: OEMB 15fdf040 00040 (v01 A M I  AMI_OEM  07000415 MSFT 00000097)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] 0MB HIGHMEM available.
[    0.000000] 351MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 15fd0000
[    0.000000]   low ram: 0 - 15fd0000
[    0.000000]   node 0 low ram: 00000000 - 15fd0000
[    0.000000]   node 0 bootmap 00011000 - 00013bfc
[    0.000000] (9 early reservations) ==> bootmem [0000000000 - 0015fd0000]
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
[    0.000000]   #1 [0000001000 - 0000002000]    EX TRAMPOLINE ==> [0000001000 - 0000002000]
[    0.000000]   #2 [0000006000 - 0000007000]       TRAMPOLINE ==> [0000006000 - 0000007000]
[    0.000000]   #3 [0000100000 - 00008ddeb8]    TEXT DATA BSS ==> [0000100000 - 00008ddeb8]
[    0.000000]   #4 [0010082000 - 001081b73d]          RAMDISK ==> [0010082000 - 001081b73d]
[    0.000000]   #5 [000009fc00 - 0000100000]    BIOS reserved ==> [000009fc00 - 0000100000]
[    0.000000]   #6 [00008de000 - 00008e10e1]              BRK ==> [00008de000 - 00008e10e1]
[    0.000000]   #7 [0000010000 - 0000011000]          PGTABLE ==> [0000010000 - 0000011000]
[    0.000000]   #8 [0000011000 - 0000014000]          BOOTMAP ==> [0000011000 - 0000014000]
[    0.000000] found SMP MP-table at [c00ff780] ff780
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000010 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x00015fd0
[    0.000000]   HighMem  0x00015fd0 -> 0x00015fd0
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[2] active PFN ranges
[    0.000000]     0: 0x00000010 -> 0x0000009f
[    0.000000]     0: 0x00000100 -> 0x00015fd0
[    0.000000] On node 0 totalpages: 89951
[    0.000000] free_area_init_node: node 0, pgdat c079a780, node_mem_map c1001200
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3951 pages, LIFO batch:0
[    0.000000]   Normal zone: 672 pages used for memmap
[    0.000000]   Normal zone: 85296 pages, LIFO batch:15
[    0.000000] Using APIC driver default
[    0.000000] ACPI: PM-Timer IO Port: 0x808
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 1, version 2, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 low level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] SMP: Allowing 1 CPUs, 0 hotplug CPUs
[    0.000000] nr_irqs_gsi: 24
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
[    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 16000000 (gap: 16000000:e9fc0000)
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:1 nr_node_ids:1
[    0.000000] PERCPU: Embedded 14 pages/cpu @c1400000 s36056 r0 d21288 u4194304
[    0.000000] pcpu-alloc: s36056 r0 d21288 u4194304 alloc=1*4194304
[    0.000000] pcpu-alloc: [0] 0 
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 89247
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.32-24-generic root=UUID=787b305a-fe40-424e-add9-be334509305a ro quiet splash
[    0.000000] PID hash table entries: 2048 (order: 1, 8192 bytes)
[    0.000000] Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.000000] Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] allocated 1800960 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] Initializing HighMem for node 0 (00000000:00000000)
[    0.000000] Memory: 338592k/360256k available (4679k kernel code, 20924k reserved, 2124k data, 660k init, 0k highmem)
[    0.000000] virtual kernel memory layout:
[    0.000000]     fixmap  : 0xfff1d000 - 0xfffff000   ( 904 kB)
[    0.000000]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[    0.000000]     vmalloc : 0xd67d0000 - 0xff7fe000   ( 656 MB)
[    0.000000]     lowmem  : 0xc0000000 - 0xd5fd0000   ( 351 MB)
[    0.000000]       .init : 0xc07a5000 - 0xc084a000   ( 660 kB)
[    0.000000]       .data : 0xc0591e33 - 0xc07a4e88   (2124 kB)
[    0.000000]       .text : 0xc0100000 - 0xc0591e33   (4679 kB)
[    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.000000] SLUB: Genslabs=13, HWalign=32, Order=0-3, MinObjects=0, CPUs=1, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000] NR_IRQS:2304 nr_irqs:256
[    0.000000] Console: colour VGA+ 80x25
[    0.000000] console [tty0] enabled
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 1099.956 MHz processor.
[    0.004011] Calibrating delay loop (skipped), value calculated using timer frequency.. 2199.91 BogoMIPS (lpj=4399824)
[    0.004058] Security Framework initialized
[    0.004128] AppArmor: AppArmor initialized
[    0.004146] Mount-cache hash table entries: 512
[    0.004464] Initializing cgroup subsys ns
[    0.004475] Initializing cgroup subsys cpuacct
[    0.004484] Initializing cgroup subsys memory
[    0.004507] Initializing cgroup subsys devices
[    0.004514] Initializing cgroup subsys freezer
[    0.004519] Initializing cgroup subsys net_cls
[    0.004567] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[    0.004573] CPU: L2 Cache: 256K (64 bytes/line)
[    0.004583] mce: CPU supports 4 MCE banks
[    0.004630] Performance Events: AMD PMU driver.
[    0.004660] ... version:                0
[    0.004664] ... bit width:              48
[    0.004669] ... generic registers:      4
[    0.004673] ... value mask:             0000ffffffffffff
[    0.004678] ... max period:             00007fffffffffff
[    0.004682] ... fixed-purpose events:   0
[    0.004686] ... event mask:             000000000000000f
[    0.004697] Checking 'hlt' instruction... OK.
[    0.021146] SMP alternatives: switching to UP code
[    0.033765] Freeing SMP alternatives: 19k freed
[    0.033834] ACPI: Core revision 20090903
[    0.047467] ftrace: converting mcount calls to 0f 1f 44 00 00
[    0.047488] ftrace: allocating 21780 entries in 43 pages
[    0.052268] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.052596] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.093233] CPU0: AMD Athlon(tm) XP  stepping 00
[    0.096001] Brought up 1 CPUs
[    0.096001] Total of 1 processors activated (2199.91 BogoMIPS).
[    0.096001] CPU0 attaching NULL sched-domain.
[    0.096001] devtmpfs: initialized
[    0.096001] regulator: core version 0.5
[    0.096001] Time:  6:28:55  Date: 03/21/11
[    0.096001] NET: Registered protocol family 16
[    0.096001] EISA bus registered
[    0.096001] ACPI: bus type pci registered
[    0.096683] PCI: PCI BIOS revision 2.10 entry at 0xf0031, last bus=1
[    0.098623] bio: create slab <bio-0> at 0
[    0.099637] ACPI: EC: Look up EC in DSDT
[    0.107185] ACPI: Executed 1 blocks of module-level executable AML code
[    0.117268] ACPI: Interpreter enabled
[    0.117284] ACPI: (supports S0 S1 S4 S5)
[    0.117327] ACPI: Using IOAPIC for interrupt routing
[    0.132291] ACPI Warning: Incorrect checksum in table [OEMB] - 0F, should be 06 (20090903/tbutils-314)
[    0.132445] ACPI: No dock devices found.
[    0.132689] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.132797] pci 0000:00:00.0: reg 10 32bit mmio: [0xd0000000-0xd3ffffff]
[    0.132997] pci 0000:00:02.0: Enabling SiS 96x SMBus
[    0.133066] pci 0000:00:02.1: reg 20 io port: [0xc00-0xc1f]
[    0.133150] pci 0000:00:02.5: reg 20 io port: [0xffa0-0xffaf]
[    0.133224] pci 0000:00:02.7: reg 10 io port: [0xe800-0xe8ff]
[    0.133236] pci 0000:00:02.7: reg 14 io port: [0xec00-0xec7f]
[    0.133296] pci 0000:00:02.7: supports D1 D2
[    0.133301] pci 0000:00:02.7: PME# supported from D3hot D3cold
[    0.133310] pci 0000:00:02.7: PME# disabled
[    0.133354] pci 0000:00:03.0: reg 10 32bit mmio: [0xcfffd000-0xcfffdfff]
[    0.133435] pci 0000:00:03.1: reg 10 32bit mmio: [0xcfffe000-0xcfffefff]
[    0.133530] pci 0000:00:03.3: reg 10 32bit mmio: [0xcffff000-0xcfffffff]
[    0.133594] pci 0000:00:03.3: PME# supported from D0 D3hot D3cold
[    0.133601] pci 0000:00:03.3: PME# disabled
[    0.133661] pci 0000:00:04.0: reg 10 io port: [0xe400-0xe4ff]
[    0.133673] pci 0000:00:04.0: reg 14 32bit mmio: [0xcfffc000-0xcfffcfff]
[    0.133710] pci 0000:00:04.0: reg 30 32bit mmio pref: [0xcffc0000-0xcffdffff]
[    0.133739] pci 0000:00:04.0: supports D1 D2
[    0.133743] pci 0000:00:04.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.133751] pci 0000:00:04.0: PME# disabled
[    0.133815] pci 0000:00:0b.0: reg 10 io port: [0xe080-0xe0bf]
[    0.133882] pci 0000:00:0b.0: supports D2
[    0.133886] pci 0000:00:0b.0: PME# supported from D0 D2 D3hot D3cold
[    0.133894] pci 0000:00:0b.0: PME# disabled
[    0.133996] pci 0000:01:00.0: reg 10 32bit mmio pref: [0xc0000000-0xc7ffffff]
[    0.134007] pci 0000:01:00.0: reg 14 32bit mmio: [0xcfee0000-0xcfefffff]
[    0.134018] pci 0000:01:00.0: reg 18 io port: [0xdc00-0xdc7f]
[    0.134066] pci 0000:01:00.0: supports D1 D2
[    0.134126] pci 0000:00:01.0: bridge io port: [0xd000-0xdfff]
[    0.134134] pci 0000:00:01.0: bridge 32bit mmio: [0xcfe00000-0xcfefffff]
[    0.134144] pci 0000:00:01.0: bridge 32bit mmio pref: [0xbfd00000-0xcfcfffff]
[    0.134158] pci_bus 0000:00: on NUMA node 0
[    0.134167] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.137285] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 7 10 *11 12 14 15)
[    0.137502] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 7 10 11 12 14 15) *0, disabled.
[    0.137717] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 7 *10 11 12 14 15)
[    0.137941] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 7 10 *11 12 14 15)
[    0.138158] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 *7 10 11 12 14 15)
[    0.138375] ACPI: PCI Interrupt Link [LNKF] (IRQs *3 4 5 7 10 11 12 14 15)
[    0.138592] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 7 10 11 12 14 15) *0, disabled.
[    0.138804] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 *5 7 10 11 12 14 15)
[    0.139084] vgaarb: device added: PCI:0000:01:00.0,decodes=io+mem,owns=io+mem,locks=none
[    0.139090] vgaarb: loaded
[    0.139413] SCSI subsystem initialized
[    0.139649] libata version 3.00 loaded.
[    0.139863] usbcore: registered new interface driver usbfs
[    0.139904] usbcore: registered new interface driver hub
[    0.139975] usbcore: registered new device driver usb
[    0.140320] ACPI: WMI: Mapper loaded
[    0.140326] PCI: Using ACPI for IRQ routing
[    0.140657] NetLabel: Initializing
[    0.140662] NetLabel:  domain hash size = 128
[    0.140665] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.140701] NetLabel:  unlabeled traffic allowed by default
[    0.140809] Switching to clocksource tsc
[    0.144786] AppArmor: AppArmor Filesystem Enabled
[    0.144849] pnp: PnP ACPI init
[    0.144906] ACPI: bus type pnp registered
[    0.157069] pnp: PnP ACPI: found 12 devices
[    0.157075] ACPI: ACPI bus type pnp unregistered
[    0.157085] PnPBIOS: Disabled by ACPI PNP
[    0.157121] system 00:05: ioport range 0x480-0x48f has been reserved
[    0.157128] system 00:05: ioport range 0x4d0-0x4d1 has been reserved
[    0.157135] system 00:05: ioport range 0x800-0x87f has been reserved
[    0.157141] system 00:05: ioport range 0x880-0x8ff has been reserved
[    0.157147] system 00:05: ioport range 0xc00-0xc1f has been reserved
[    0.157157] system 00:05: iomem range 0xfff80000-0xffffffff could not be reserved
[    0.157164] system 00:05: iomem range 0xffe80000-0xffefffff has been reserved
[    0.157171] system 00:05: iomem range 0xfed00000-0xfed003ff has been reserved
[    0.157184] system 00:06: iomem range 0xfec00000-0xfec00fff could not be reserved
[    0.157191] system 00:06: iomem range 0xfee00000-0xfee00fff has been reserved
[    0.157205] system 00:0b: iomem range 0x0-0x9ffff could not be reserved
[    0.157212] system 00:0b: iomem range 0xc0000-0xdffff could not be reserved
[    0.157218] system 00:0b: iomem range 0xe0000-0xfffff could not be reserved
[    0.157225] system 00:0b: iomem range 0x100000-0x15ffffff could not be reserved
[    0.192184] pci 0000:00:01.0: PCI bridge, secondary bus 0000:01
[    0.192193] pci 0000:00:01.0:   IO window: 0xd000-0xdfff
[    0.192206] pci 0000:00:01.0:   MEM window: 0xcfe00000-0xcfefffff
[    0.192215] pci 0000:00:01.0:   PREFETCH window: 0xbfd00000-0xcfcfffff
[    0.192249] pci_bus 0000:00: resource 0 io:  [0x00-0xffff]
[    0.192255] pci_bus 0000:00: resource 1 mem: [0x000000-0xffffffff]
[    0.192262] pci_bus 0000:01: resource 0 io:  [0xd000-0xdfff]
[    0.192268] pci_bus 0000:01: resource 1 mem: [0xcfe00000-0xcfefffff]
[    0.192274] pci_bus 0000:01: resource 2 pref mem [0xbfd00000-0xcfcfffff]
[    0.192371] NET: Registered protocol family 2
[    0.192583] IP route cache hash table entries: 4096 (order: 2, 16384 bytes)
[    0.193194] TCP established hash table entries: 16384 (order: 5, 131072 bytes)
[    0.193613] TCP bind hash table entries: 16384 (order: 5, 131072 bytes)
[    0.194029] TCP: Hash tables configured (established 16384 bind 16384)
[    0.194035] TCP reno registered
[    0.194244] NET: Registered protocol family 1
[    0.194395] pci 0000:01:00.0: Boot video device
[    0.194955] cpufreq-nforce2: No nForce2 chipset.
[    0.195024] Scanning for low memory corruption every 60 seconds
[    0.195346] audit: initializing netlink socket (disabled)
[    0.195377] type=2000 audit(1300688934.195:1): initialized
[    0.213272] Trying to unpack rootfs image as initramfs...
[    0.235756] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    0.239398] VFS: Disk quotas dquot_6.5.2
[    0.239556] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.247647] fuse init (API version 7.13)
[    0.247980] msgmni has been set to 661
[    0.248663] alg: No test for stdrng (krng)
[    0.248751] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.248759] io scheduler noop registered
[    0.248763] io scheduler anticipatory registered
[    0.248768] io scheduler deadline registered
[    0.248852] io scheduler cfq registered (default)
[    0.249107] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.249157] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.249421] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0
[    0.249442] ACPI: Power Button [PWRB]
[    0.249563] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
[    0.249569] ACPI: Power Button [PWRF]
[    0.250085] processor LNXCPU:00: registered as cooling_device0
[    0.271209] isapnp: Scanning for PnP cards...
[    0.277343] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    0.277526] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.278197] 00:0a: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.285448] brd: module loaded
[    0.286580] loop: module loaded
[    0.286896] input: Macintosh mouse button emulation as /devices/virtual/input/input2
[    0.335731] pata_sis 0000:00:02.5: version 0.5.2
[    0.336216] scsi0 : pata_sis
[    0.336437] scsi1 : pata_sis
[    0.338337] ata1: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xffa0 irq 14
[    0.338346] ata2: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xffa8 irq 15
[    0.339156] Fixed MDIO Bus: probed
[    0.339239] PPP generic driver version 2.4.2
[    0.339438] tun: Universal TUN/TAP device driver, 1.6
[    0.339444] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.339688] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.339748]   alloc irq_desc for 23 on node -1
[    0.339754]   alloc kstat_irqs on node -1
[    0.339773] ehci_hcd 0000:00:03.3: PCI INT D -> GSI 23 (level, low) -> IRQ 23
[    0.339822] ehci_hcd 0000:00:03.3: EHCI Host Controller
[    0.339904] ehci_hcd 0000:00:03.3: new USB bus registered, assigned bus number 1
[    0.339990] ehci_hcd 0000:00:03.3: cache line size of 64 is not supported
[    0.340032] ehci_hcd 0000:00:03.3: irq 23, io mem 0xcffff000
[    0.351487] ehci_hcd 0000:00:03.3: USB 2.0 started, EHCI 1.00
[    0.351885] usb usb1: configuration #1 chosen from 1 choice
[    0.351965] hub 1-0:1.0: USB hub found
[    0.352002] hub 1-0:1.0: 6 ports detected
[    0.352167] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.352238]   alloc irq_desc for 20 on node -1
[    0.352244]   alloc kstat_irqs on node -1
[    0.352262] ohci_hcd 0000:00:03.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    0.352311] ohci_hcd 0000:00:03.0: OHCI Host Controller
[    0.352430] ohci_hcd 0000:00:03.0: new USB bus registered, assigned bus number 2
[    0.352516] ohci_hcd 0000:00:03.0: irq 20, io mem 0xcfffd000
[    0.429557] usb usb2: configuration #1 chosen from 1 choice
[    0.429638] hub 2-0:1.0: USB hub found
[    0.429675] hub 2-0:1.0: 3 ports detected
[    0.429835]   alloc irq_desc for 21 on node -1
[    0.429840]   alloc kstat_irqs on node -1
[    0.429861] ohci_hcd 0000:00:03.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[    0.429928] ohci_hcd 0000:00:03.1: OHCI Host Controller
[    0.430040] ohci_hcd 0000:00:03.1: new USB bus registered, assigned bus number 3
[    0.430111] ohci_hcd 0000:00:03.1: irq 21, io mem 0xcfffe000
[    0.517691] usb usb3: configuration #1 chosen from 1 choice
[    0.517773] hub 3-0:1.0: USB hub found
[    0.517815] hub 3-0:1.0: 3 ports detected
[    0.517971] uhci_hcd: USB Universal Host Controller Interface driver
[    0.518233] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f03:PS2M] at 0x60,0x64 irq 1,12
[    0.524263] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.524289] serio: i8042 AUX port at 0x60,0x64 irq 12
[    0.524787] mice: PS/2 mouse device common for all mice
[    0.525066] rtc_cmos 00:02: RTC can wake from S4
[    0.525190] rtc_cmos 00:02: rtc core: registered rtc_cmos as rtc0
[    0.525230] rtc0: alarms up to one month, 114 bytes nvram
[    0.525478] device-mapper: uevent: version 1.0.3
[    0.525767] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: [email]dm-devel@redhat.com[/email]
[    0.527890] device-mapper: multipath: version 1.1.0 loaded
[    0.527904] device-mapper: multipath round-robin: version 1.0.0 loaded
[    0.528437] EISA: Probing bus 0 at eisa.0
[    0.528487] EISA: Detected 0 cards.
[    0.530337] cpuidle: using governor ladder
[    0.530345] cpuidle: using governor menu
[    0.531419] TCP cubic registered
[    0.531775] NET: Registered protocol family 10
[    0.532731] lo: Disabled Privacy Extensions
[    0.533357] NET: Registered protocol family 17
[    0.533836] powernow-k8: Processor cpuid 680 not supported
[    0.533924] Using IPI No-Shortcut mode
[    0.534257] PM: Resume from disk failed.
[    0.534295] registered taskstats version 1
[    0.534652]   Magic number: 3:120:469
[    0.534883] rtc_cmos 00:02: setting system clock to 2011-03-21 06:28:55 UTC (1300688935)
[    0.534892] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.534896] EDD information not available.
[    0.545542] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input3
[    0.567486] ata1.00: HPA unlocked: 80291135 -> 80293248, native 80293248
[    0.567507] ata1.00: ATA-7: Maxtor 6E040L0, NAR61HA0, max UDMA/133
[    0.567514] ata1.00: 80293248 sectors, multi 16: LBA 
[    0.567583] ata1.01: ATAPI: DVD-ROM DDU1632, VER AS19, max UDMA/33
[    0.567628] ata1.00: limited to UDMA/33 due to 40-wire cable
[    0.623764] ata1.00: configured for UDMA/33
[    0.640120] ata1.01: configured for UDMA/33
[    0.963458] isapnp: No Plug & Play device found
[    0.963895] scsi 0:0:0:0: Direct-Access     ATA      Maxtor 6E040L0   NAR6 PQ: 0 ANSI: 5
[    0.964344] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    0.965701] scsi 0:0:1:0: CD-ROM            SONY     DVD-ROM DDU1632  AS19 PQ: 0 ANSI: 5
[    0.972773] sr0: scsi3-mmc drive: 4x/40x cd/rw xa/form2 cdda tray
[    0.972788] Uniform CD-ROM driver Revision: 3.20
[    0.973144] sr 0:0:1:0: Attached scsi CD-ROM sr0
[    0.973325] sr 0:0:1:0: Attached scsi generic sg1 type 5
[    0.973781] sd 0:0:0:0: [sda] 80293248 512-byte logical blocks: (41.1 GB/38.2 GiB)
[    0.973918] sd 0:0:0:0: [sda] Write Protect is off
[    0.973925] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    0.973995] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    0.974359]  sda: sda1 sda2 < sda5 sda6 sda7 sda8 >
[    1.028831] sd 0:0:0:0: [sda] Attached SCSI disk
[    1.079782] Freeing initrd memory: 7781k freed
[    1.152318] ata2.00: ATAPI: HL-DT-ST RW/DVD GCC-4522B, 1.03, max UDMA/33
[    1.184312] ata2.00: configured for UDMA/33
[    1.185842] scsi 1:0:0:0: CD-ROM            HL-DT-ST RW/DVD GCC-4522B 1.03 PQ: 0 ANSI: 5
[    1.188187] sr1: scsi3-mmc drive: 52x/52x writer cd/rw xa/form2 cdda tray
[    1.188511] sr 1:0:0:0: Attached scsi CD-ROM sr1
[    1.188672] sr 1:0:0:0: Attached scsi generic sg2 type 5
[    1.188802] Freeing unused kernel memory: 660k freed
[    1.190682] Write protecting the kernel text: 4680k
[    1.190748] Write protecting the kernel read-only data: 1844k
[    1.251375] udev: starting version 151
[    1.800491] FDC 0 is a post-1991 82077
[    1.816228] sis900.c: v1.08.10 Apr. 2 2006
[    1.816360]   alloc irq_desc for 19 on node -1
[    1.816366]   alloc kstat_irqs on node -1
[    1.816387] sis900 0000:00:04.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    1.817557] 0000:00:04.0: Realtek RTL8201 PHY transceiver found at address 1.
[    1.829473] 0000:00:04.0: Using transceiver found at address 1 as default
[    1.839623] eth0: SiS 900 PCI Fast Ethernet at 0xe400, IRQ 19, 00:2a:43:00:6e:f5
[    2.363066] EXT4-fs (sda1): mounted filesystem with ordered data mode
[   13.703721] Adding 566264k swap on /dev/sda8.  Priority:-1 extents:1 across:566264k 
[   14.038472] udev: starting version 151
[   14.659640] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   14.809245] sis96x_smbus 0000:00:02.1: SiS96x SMBus base address: 0x0c00
[   14.822178] Linux agpgart interface v0.103
[   15.190472] agpgart-sis 0000:00:00.0: SiS chipset [1039/0741]
[   15.416183] lp: driver loaded but no devices found
[   15.678321] agpgart-sis 0000:00:00.0: AGP aperture is 64M @ 0xd0000000
[   15.774554] psmouse serio1: ID: 10 00 64
[   16.102247] vga16fb: initializing
[   16.102264] vga16fb: mapped to 0xc00a0000
[   16.102556] fb0: VGA16 VGA frame buffer device
[   16.378438] input: ImPS/2 Generic Wheel Mouse as /devices/platform/i8042/serio1/input/input4
[   16.528414] type=1505 audit(1300688951.493:2):  operation="profile_load" pid=711 name="/sbin/dhclient3"
[   16.529057] type=1505 audit(1300688951.493:3):  operation="profile_load" pid=711 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[   16.529421] type=1505 audit(1300688951.493:4):  operation="profile_load" pid=711 name="/usr/lib/connman/scripts/dhclient-script"
[   17.132924] Console: switching to colour frame buffer device 80x30
[   18.475021]   alloc irq_desc for 18 on node -1
[   18.475032]   alloc kstat_irqs on node -1
[   18.475053] Intel ICH 0000:00:02.7: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[   18.621143] eth0: Media Link Off
[   18.623959] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   18.812139] intel8x0_measure_ac97_clock: measured 55859 usecs (2686 samples)
[   18.812152] intel8x0: clocking to 48000
[   18.959269] type=1505 audit(1300688953.921:5):  operation="profile_load" pid=1086 name="/usr/share/gdm/guest-session/Xsession"
[   18.989074] type=1505 audit(1300688953.953:6):  operation="profile_replace" pid=1088 name="/sbin/dhclient3"
[   18.989773] type=1505 audit(1300688953.953:7):  operation="profile_replace" pid=1088 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[   18.990165] type=1505 audit(1300688953.953:8):  operation="profile_replace" pid=1088 name="/usr/lib/connman/scripts/dhclient-script"
[   19.125180] type=1505 audit(1300688954.089:9):  operation="profile_load" pid=1091 name="/usr/bin/evince"
[   19.140928] type=1505 audit(1300688954.105:10):  operation="profile_load" pid=1091 name="/usr/bin/evince-previewer"
[   19.147856] type=1505 audit(1300688954.109:11):  operation="profile_load" pid=1091 name="/usr/bin/evince-thumbnailer"
[   20.566652] ppdev: user-space parallel port driver
[   82.196035] usb 1-6: new high speed USB device using ehci_hcd and address 2
[   82.331890] usb 1-6: configuration #1 chosen from 1 choice
[   82.588568] Initializing USB Mass Storage driver...
[   82.591724] scsi2 : SCSI emulation for USB Mass Storage devices
[   82.593196] usbcore: registered new interface driver usb-storage
[   82.593208] USB Mass Storage support registered.
[   82.607341] usb-storage: device found at 2
[   82.607352] usb-storage: waiting for device to settle before scanning
[   87.604815] usb-storage: device scan complete
[   87.605620] scsi 2:0:0:0: CD-ROM            HSUPA    MMC Storage      2.31 PQ: 0 ANSI: 2
[   87.606199] scsi 2:0:0:1: Direct-Access     HSUPA    MMC Storage      2.31 PQ: 0 ANSI: 2
[   87.614748] sr2: scsi-1 drive
[   87.617114] sr 2:0:0:0: Attached scsi CD-ROM sr2
[   87.617783] sr 2:0:0:0: Attached scsi generic sg3 type 5
[   87.618730] sd 2:0:0:1: Attached scsi generic sg4 type 0
[   87.631133] sd 2:0:0:1: [sdb] Attached SCSI removable disk
[   88.902556] usb 1-6: USB disconnect, address 2
[   89.252032] usb 1-6: new high speed USB device using ehci_hcd and address 3
[   89.386713] usb 1-6: configuration #1 chosen from 1 choice
[   89.545868] scsi3 : SCSI emulation for USB Mass Storage devices
[   89.583200] usb-storage: device found at 3
[   89.583210] usb-storage: waiting for device to settle before scanning
[   94.580705] usb-storage: device scan complete
[   94.581628] scsi 3:0:0:0: CD-ROM            HSUPA    MMC Storage      2.31 PQ: 0 ANSI: 2
[   94.582191] scsi 3:0:0:1: Direct-Access     HSUPA    MMC Storage      2.31 PQ: 0 ANSI: 2
[   94.589975] sr2: scsi-1 drive
[   94.590451] sr 3:0:0:0: Attached scsi CD-ROM sr2
[   94.590711] sr 3:0:0:0: Attached scsi generic sg3 type 5
[   94.594026] sd 3:0:0:1: Attached scsi generic sg4 type 0
[   94.600199] sd 3:0:0:1: [sdb] Attached SCSI removable disk

---

### Post by Script Warlock on 2011-03-21
if it does work, try to plug and click the network applet and something says "A new mobile broadband (GSM) connection...."

---

### Post by tredegar on 2011-03-21
You need to install [**usb_modeswitch**]("http://www.draisberghof.de/usb_modeswitch/") to switch the device from being a CD-Rom to being a modem, then you will be able to use it.

It is in the ubuntu repositories, but you may still need to refer to the link I gave.

---

### Post by L Style on 2011-03-21
It's work. I download saiks3g application, It's best.. thank you

---

### Post by tredegar on 2011-03-21
> I download saiks3g application, It's best..
What is that? Where did you download it from?

---

### Post by L Style on 2011-03-21
> **tredegar said:**
> What is that? Where did you download it from?

from that software you can connect with any 3g modems. [http://www.sakis3g.org/](http://www.sakis3g.org/) use this link

---

### Post by dineshs on 2011-03-21
Happy to hear that your problem is solved.Please mark the thread as solved (via thread tools)

---

