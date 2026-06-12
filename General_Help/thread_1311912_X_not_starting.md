---
title: "X not starting"
date: 2009-11-02
forum: General Help
---

### Post by ixifx on 2009-11-02
I have recently set up xubuntu 9.10 on an old dell.

the machine has onboard intel graphics

everything was running smoothly until I restarted after lowering the desktop resolution and changing a few display options

now when I try to log on to the main account I get:

[ 1152.428038] [drm:i810_wait_ring] *ERROR* space: 65520 wanted 65528
[ 1152.428107] [drm:i810_wait_ring] *ERROR* lockup
[ 1154.571212] [drm] Using v1.4 init.
[ 1157.756030] [drm:drm_reclaim_locked_buffers] *ERROR* reclaim_buffers_locked() deadlock. Please rework this

for a brief second after the screen flickers.  but then I get sent back to the login screen.  I can log in fully and start X with the second account I created, which I haven't done any visual modifications to.  I can also log in to the xterm session with the main account

I did some searching and found a thread on here suggesting I do

dpkg-reconfigure xserver-xorg

so I did, with no luck.  I'm still kinda new to linux, so if there's any information I could get to help diagnose the problem let me know

thanks in advance,

john

---

### Post by ixifx on 2009-11-02
here is a full dmesg

```

[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.31-14-generic (buildd@rothera) (gcc version 4.4.1 (Ubuntu 4.4.1-4ubuntu8) ) #48-Ubuntu SMP Fri Oct 16 14:04:26 UTC 2009 (Ubuntu 2.6.31-14.48-generic)
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
[    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000000fec0000 (usable)
[    0.000000]  BIOS-e820: 000000000fec0000 - 000000000fef8000 (ACPI data)
[    0.000000]  BIOS-e820: 000000000fef8000 - 000000000ff00000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000ffb80000 - 00000000ffc00000 (reserved)
[    0.000000]  BIOS-e820: 00000000fff00000 - 0000000100000000 (reserved)
[    0.000000] DMI 2.3 present.
[    0.000000] last_pfn = 0xfec0 max_arch_pfn = 0x100000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-CFFFF write-protect
[    0.000000]   D0000-DFFFF uncachable
[    0.000000]   E0000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000 mask FF0000000 write-back
[    0.000000]   1 base 00FF00000 mask FFFF00000 uncachable
[    0.000000]   2 disabled
[    0.000000]   3 disabled
[    0.000000]   4 disabled
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] PAT not supported by CPU.
[    0.000000] e820 update range: 0000000000002000 - 0000000000006000 (usable) ==> (reserved)
[    0.000000] Scanning 1 areas for low memory corruption
[    0.000000] modified physical RAM map:
[    0.000000]  modified: 0000000000000000 - 0000000000002000 (usable)
[    0.000000]  modified: 0000000000002000 - 0000000000006000 (reserved)
[    0.000000]  modified: 0000000000006000 - 000000000009fc00 (usable)
[    0.000000]  modified: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  modified: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  modified: 0000000000100000 - 000000000fec0000 (usable)
[    0.000000]  modified: 000000000fec0000 - 000000000fef8000 (ACPI data)
[    0.000000]  modified: 000000000fef8000 - 000000000ff00000 (ACPI NVS)
[    0.000000]  modified: 00000000ffb80000 - 00000000ffc00000 (reserved)
[    0.000000]  modified: 00000000fff00000 - 0000000100000000 (reserved)
[    0.000000] initial memory mapped : 0 - 00c00000
[    0.000000] init_memory_mapping: 0000000000000000-000000000fec0000
[    0.000000] Using x86 segment limits to approximate NX protection
[    0.000000]  0000000000 - 0000400000 page 4k
[    0.000000]  0000400000 - 000fc00000 page 2M
[    0.000000]  000fc00000 - 000fec0000 page 4k
[    0.000000] kernel direct mapping tables up to fec0000 @ 7000-c000
[    0.000000] RAMDISK: 0f769000 - 0feaf188
[    0.000000] ACPI: RSDP 000ff980 00014 (v00 AMI   )
[    0.000000] ACPI: RSDT 0fef0000 00028 (v01 DELL   MUMMY    20010307 MSFT 00000097)
[    0.000000] ACPI: FACP 0fef1000 00074 (v01 DELL   MUMMY    20010307 MSFT 00000097)
[    0.000000] ACPI: DSDT 0fee0000 027D8 (v01 DELL   DIM_L    00000012 MSFT 0100000B)
[    0.000000] ACPI: FACS 0fef8000 00040
[    0.000000] 0MB HIGHMEM available.
[    0.000000] 254MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 0fec0000
[    0.000000]   low ram: 0 - 0fec0000
[    0.000000]   node 0 low ram: 00000000 - 0fec0000
[    0.000000]   node 0 bootmap 00008000 - 00009fd8
[    0.000000] (9 early reservations) ==> bootmem [0000000000 - 000fec0000]
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
[    0.000000]   #1 [0000001000 - 0000002000]    EX TRAMPOLINE ==> [0000001000 - 0000002000]
[    0.000000]   #2 [0000006000 - 0000007000]       TRAMPOLINE ==> [0000006000 - 0000007000]
[    0.000000]   #3 [0000100000 - 00008a80a0]    TEXT DATA BSS ==> [0000100000 - 00008a80a0]
[    0.000000]   #4 [000f769000 - 000feaf188]          RAMDISK ==> [000f769000 - 000feaf188]
[    0.000000]   #5 [000009fc00 - 0000100000]    BIOS reserved ==> [000009fc00 - 0000100000]
[    0.000000]   #6 [00008a9000 - 00008ac24c]              BRK ==> [00008a9000 - 00008ac24c]
[    0.000000]   #7 [0000007000 - 0000008000]          PGTABLE ==> [0000007000 - 0000008000]
[    0.000000]   #8 [0000008000 - 000000a000]          BOOTMAP ==> [0000008000 - 000000a000]
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000000 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x0000fec0
[    0.000000]   HighMem  0x0000fec0 -> 0x0000fec0
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[3] active PFN ranges
[    0.000000]     0: 0x00000000 -> 0x00000002
[    0.000000]     0: 0x00000006 -> 0x0000009f
[    0.000000]     0: 0x00000100 -> 0x0000fec0
[    0.000000] On node 0 totalpages: 65115
[    0.000000] free_area_init_node: node 0, pgdat c0784900, node_mem_map c1000000
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3963 pages, LIFO batch:0
[    0.000000]   Normal zone: 478 pages used for memmap
[    0.000000]   Normal zone: 60642 pages, LIFO batch:15
[    0.000000] Using APIC driver default
[    0.000000] ACPI: PM-Timer IO Port: 0x408
[    0.000000] SMP: Allowing 1 CPUs, 0 hotplug CPUs
[    0.000000] Local APIC disabled by BIOS -- you can enable it with "lapic"
[    0.000000] APIC: disable apic facility
[    0.000000] nr_irqs_gsi: 16
[    0.000000] PM: Registered nosave memory: 0000000000002000 - 0000000000006000
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
[    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at ff00000 (gap: ff00000:efc80000)
[    0.000000] NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:1 nr_node_ids:1
[    0.000000] PERCPU: Embedded 14 pages at c1202000, static data 35612 bytes
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 64605
[    0.000000] Kernel command line: root=UUID=d5bd637f-a3b9-497c-9250-43742d1c75b6 ro quiet splash 
[    0.000000] PID hash table entries: 1024 (order: 10, 4096 bytes)
[    0.000000] Dentry cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.000000] Inode-cache hash table entries: 16384 (order: 4, 65536 bytes)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] allocated 1304320 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] Initializing HighMem for node 0 (00000000:00000000)
[    0.000000] Memory: 241300k/260864k available (4565k kernel code, 18932k reserved, 2143k data, 540k init, 0k highmem)
[    0.000000] virtual kernel memory layout:
[    0.000000]     fixmap  : 0xfff1d000 - 0xfffff000   ( 904 kB)
[    0.000000]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[    0.000000]     vmalloc : 0xd06c0000 - 0xff7fe000   ( 753 MB)
[    0.000000]     lowmem  : 0xc0000000 - 0xcfec0000   ( 254 MB)
[    0.000000]       .init : 0xc078e000 - 0xc0815000   ( 540 kB)
[    0.000000]       .data : 0xc0575554 - 0xc078d308   (2143 kB)
[    0.000000]       .text : 0xc0100000 - 0xc0575554   (4565 kB)
[    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.000000] SLUB: Genslabs=13, HWalign=32, Order=0-3, MinObjects=0, CPUs=1, Nodes=1
[    0.000000] NR_IRQS:2304 nr_irqs:256
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 996.623 MHz processor.
[    0.001950] Console: colour VGA+ 80x25
[    0.001959] console [tty0] enabled
[    0.002087] Calibrating delay loop (skipped), value calculated using timer frequency.. 1993.24 BogoMIPS (lpj=3986492)
[    0.002142] Security Framework initialized
[    0.002213] AppArmor: AppArmor initialized
[    0.002235] Mount-cache hash table entries: 512
[    0.002579] Initializing cgroup subsys ns
[    0.002590] Initializing cgroup subsys cpuacct
[    0.002602] Initializing cgroup subsys memory
[    0.002624] Initializing cgroup subsys freezer
[    0.002631] Initializing cgroup subsys net_cls
[    0.002674] CPU: L1 I cache: 16K, L1 D cache: 16K
[    0.002681] CPU: L2 cache: 256K
[    0.002696] mce: CPU supports 5 MCE banks
[    0.002736] Performance Counters: 
[    0.002743] no APIC, boot with the "lapic" boot parameter to force-enable it.
[    0.002749] no hardware sampling interrupt available.
[    0.002755] p6 PMU driver.
[    0.002797] ... version:                 0
[    0.002803] ... bit width:               32
[    0.002808] ... generic counters:        2
[    0.002813] ... value mask:              00000000ffffffff
[    0.002819] ... max period:              000000007fffffff
[    0.002825] ... fixed-purpose counters:  0
[    0.002830] ... counter mask:            0000000000000003
[    0.002840] Checking 'hlt' instruction... OK.
[    0.017324] SMP alternatives: switching to UP code
[    0.028070] Freeing SMP alternatives: 19k freed
[    0.028140] ACPI: Core revision 20090521
[    0.036520] ACPI: setting ELCR to 0200 (from 0e08)
[    0.037032] weird, boot CPU (#0) not listed by the BIOS.
[    0.037039] SMP motherboard not detected.
[    0.037046] Local APIC not detected. Using dummy APIC emulation.
[    0.037051] SMP disabled
[    0.037740] Brought up 1 CPUs
[    0.037755] Total of 1 processors activated (1993.24 BogoMIPS).
[    0.037817] CPU0 attaching NULL sched-domain.
[    0.038827] Booting paravirtualized kernel on bare hardware
[    0.039520] regulator: core version 0.5
[    0.039564] Time: 22:55:28  Date: 11/02/09
[    0.039752] NET: Registered protocol family 16
[    0.040192] EISA bus registered
[    0.040255] ACPI: bus type pci registered
[    0.041216] PCI: PCI BIOS revision 2.10 entry at 0xfda95, last bus=1
[    0.041226] PCI: Using configuration type 1 for base access
[    0.044036] bio: create slab <bio-0> at 0
[    0.045222] ACPI: EC: Look up EC in DSDT
[    0.055256] ACPI: Interpreter enabled
[    0.055281] ACPI: (supports S0 S1 S4 S5)
[    0.055338] ACPI: Using PIC for interrupt routing
[    0.061671] ACPI: Power Resource [URP1] (off)
[    0.061741] ACPI: Power Resource [URP2] (off)
[    0.061807] ACPI: Power Resource [FDDP] (off)
[    0.061872] ACPI: Power Resource [LPTP] (off)
[    0.062085] ACPI: No dock devices found.
[    0.062585] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.062750] pci 0000:00:01.0: reg 10 32bit mmio: [0xf8000000-0xfbffffff]
[    0.062762] pci 0000:00:01.0: reg 14 32bit mmio: [0xffa80000-0xffafffff]
[    0.062942] pci 0000:00:1f.0: quirk: region 0400-047f claimed by ICH4 ACPI/GPIO/TCO
[    0.062951] pci 0000:00:1f.0: quirk: region 0500-053f claimed by ICH4 GPIO
[    0.063008] pci 0000:00:1f.1: reg 20 io port: [0xffa0-0xffaf]
[    0.063081] pci 0000:00:1f.2: reg 20 io port: [0xef80-0xef9f]
[    0.063158] pci 0000:00:1f.3: reg 20 io port: [0xefa0-0xefaf]
[    0.063247] pci 0000:01:09.0: reg 10 io port: [0xdf00-0xdf3f]
[    0.063302] pci 0000:01:09.0: supports D1 D2
[    0.063346] pci 0000:01:0a.0: reg 10 io port: [0xd800-0xd8ff]
[    0.063359] pci 0000:01:0a.0: reg 14 32bit mmio: [0xff8efc00-0xff8efcff]
[    0.063389] pci 0000:01:0a.0: reg 30 32bit mmio: [0xff880000-0xff8bffff]
[    0.063415] pci 0000:01:0a.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.063424] pci 0000:01:0a.0: PME# disabled
[    0.063468] pci 0000:01:0b.0: reg 10 32bit mmio: [0xff8f0000-0xff8fffff]
[    0.063480] pci 0000:01:0b.0: reg 14 io port: [0xdff0-0xdff7]
[    0.063527] pci 0000:01:0b.0: PME# supported from D0 D3hot
[    0.063535] pci 0000:01:0b.0: PME# disabled
[    0.063572] pci 0000:00:1e.0: transparent bridge
[    0.063582] pci 0000:00:1e.0: bridge io port: [0xd000-0xdfff]
[    0.063591] pci 0000:00:1e.0: bridge 32bit mmio: [0xff800000-0xff8fffff]
[    0.063603] pci 0000:00:1e.0: bridge 32bit mmio pref: [0xf6a00000-0xf6afffff]
[    0.063618] pci_bus 0000:00: on NUMA node 0
[    0.063629] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.063800] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCI1._PRT]
[    0.065819] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)
[    0.066031] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 9 *10 11 12 14 15)
[    0.066237] ACPI: PCI Interrupt Link [LNKC] (IRQs *3 4 5 6 7 9 10 11 12 14 15)
[    0.066456] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 *9 10 11 12 14 15)
[    0.067016] SCSI subsystem initialized
[    0.067281] libata version 3.00 loaded.
[    0.067513] usbcore: registered new interface driver usbfs
[    0.067561] usbcore: registered new interface driver hub
[    0.067639] usbcore: registered new device driver usb
[    0.068060] ACPI: WMI: Mapper loaded
[    0.068067] PCI: Using ACPI for IRQ routing
[    0.068426] Bluetooth: Core ver 2.15
[    0.068545] NET: Registered protocol family 31
[    0.068550] Bluetooth: HCI device and connection manager initialized
[    0.068560] Bluetooth: HCI socket layer initialized
[    0.068565] NetLabel: Initializing
[    0.068569] NetLabel:  domain hash size = 128
[    0.068574] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.068616] NetLabel:  unlabeled traffic allowed by default
[    0.075444] pnp: PnP ACPI init
[    0.075533] ACPI: bus type pnp registered
[    0.080979] pnp: PnP ACPI: found 11 devices
[    0.080989] ACPI: ACPI bus type pnp unregistered
[    0.081001] PnPBIOS: Disabled by ACPI PNP
[    0.081038] system 00:0a: iomem range 0x0-0x9ffff could not be reserved
[    0.081048] system 00:0a: iomem range 0xe0000-0xfffff could not be reserved
[    0.081056] system 00:0a: iomem range 0x100000-0xfefffff could not be reserved
[    0.116047] AppArmor: AppArmor Filesystem Enabled
[    0.116079] pci 0000:01:0a.0: BAR 6: address space collision on of device [0xff880000-0xff8bffff]
[    0.116119] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:01
[    0.116127] pci 0000:00:1e.0:   IO window: 0xd000-0xdfff
[    0.116140] pci 0000:00:1e.0:   MEM window: 0xff800000-0xff8fffff
[    0.116150] pci 0000:00:1e.0:   PREFETCH window: 0xf6a00000-0xf6afffff
[    0.116178] pci 0000:00:1e.0: setting latency timer to 64
[    0.116190] pci_bus 0000:00: resource 0 io:  [0x00-0xffff]
[    0.116197] pci_bus 0000:00: resource 1 mem: [0x000000-0xffffffff]
[    0.116205] pci_bus 0000:01: resource 0 io:  [0xd000-0xdfff]
[    0.116213] pci_bus 0000:01: resource 1 mem: [0xff800000-0xff8fffff]
[    0.116220] pci_bus 0000:01: resource 2 pref mem [0xf6a00000-0xf6afffff]
[    0.116227] pci_bus 0000:01: resource 3 io:  [0x00-0xffff]
[    0.116234] pci_bus 0000:01: resource 4 mem: [0x000000-0xffffffff]
[    0.116350] NET: Registered protocol family 2
[    0.116640] IP route cache hash table entries: 2048 (order: 1, 8192 bytes)
[    0.117418] TCP established hash table entries: 8192 (order: 4, 65536 bytes)
[    0.117635] TCP bind hash table entries: 8192 (order: 4, 65536 bytes)
[    0.117851] TCP: Hash tables configured (established 8192 bind 8192)
[    0.117858] TCP reno registered
[    0.118139] NET: Registered protocol family 1
[    0.118362] Trying to unpack rootfs image as initramfs...
[    0.616196] Switched to high resolution mode on CPU 0
[    0.681402] Freeing initrd memory: 7448k freed
[    0.722705] cpufreq-nforce2: No nForce2 chipset.
[    0.722790] Scanning for low memory corruption every 60 seconds
[    0.723149] audit: initializing netlink socket (disabled)
[    0.723206] type=2000 audit(1257202528.720:1): initialized
[    0.745623] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    0.750153] VFS: Disk quotas dquot_6.5.2
[    0.750346] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.752168] fuse init (API version 7.12)
[    0.752424] msgmni has been set to 486
[    0.753133] alg: No test for stdrng (krng)
[    0.753173] io scheduler noop registered
[    0.753179] io scheduler anticipatory registered
[    0.753184] io scheduler deadline registered
[    0.753368] io scheduler cfq registered (default)
[    0.753419] pci 0000:00:01.0: Boot video device
[    0.753665] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.753727] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.754044] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input0
[    0.754056] ACPI: Power Button [PWRF]
[    0.754460] processor LNXCPU:00: registered as cooling_device0
[    0.757298] isapnp: Scanning for PnP cards...
[    1.111790] isapnp: No Plug & Play device found
[    1.114950] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    1.115137] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    1.115820] 00:08: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    1.118582] brd: module loaded
[    1.119817] loop: module loaded
[    1.120236] input: Macintosh mouse button emulation as /devices/virtual/input/input1
[    1.120573] ata_piix 0000:00:1f.1: version 2.13
[    1.120770] ata_piix 0000:00:1f.1: setting latency timer to 64
[    1.121079] scsi0 : ata_piix
[    1.121454] scsi1 : ata_piix
[    1.124449] ata1: PATA max UDMA/66 cmd 0x1f0 ctl 0x3f6 bmdma 0xffa0 irq 14
[    1.124458] ata2: PATA max UDMA/66 cmd 0x170 ctl 0x376 bmdma 0xffa8 irq 15
[    1.126927] Fixed MDIO Bus: probed
[    1.127026] PPP generic driver version 2.4.2
[    1.127371] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    1.127427] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    1.127467] uhci_hcd: USB Universal Host Controller Interface driver
[    1.128007] ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 9
[    1.128089] PCI: setting IRQ 9 as level-triggered
[    1.128100] uhci_hcd 0000:00:1f.2: PCI INT D -> Link[LNKD] -> GSI 9 (level, low) -> IRQ 9
[    1.128120] uhci_hcd 0000:00:1f.2: setting latency timer to 64
[    1.128129] uhci_hcd 0000:00:1f.2: UHCI Host Controller
[    1.128329] uhci_hcd 0000:00:1f.2: new USB bus registered, assigned bus number 1
[    1.128376] uhci_hcd 0000:00:1f.2: irq 9, io base 0x0000ef80
[    1.128654] usb usb1: configuration #1 chosen from 1 choice
[    1.128752] hub 1-0:1.0: USB hub found
[    1.128783] hub 1-0:1.0: 2 ports detected
[    1.129042] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f03:PS2M] at 0x60,0x64 irq 1,12
[    1.132233] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.132250] serio: i8042 AUX port at 0x60,0x64 irq 12
[    1.132429] mice: PS/2 mouse device common for all mice
[    1.132623] rtc_cmos 00:02: RTC can wake from S4
[    1.132716] rtc_cmos 00:02: rtc core: registered rtc_cmos as rtc0
[    1.132746] rtc0: alarms up to one month, 114 bytes nvram
[    1.133048] device-mapper: uevent: version 1.0.3
[    1.133349] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: dm-devel@redhat.com
[    1.133602] device-mapper: multipath: version 1.1.0 loaded
[    1.133611] device-mapper: multipath round-robin: version 1.0.0 loaded
[    1.134054] EISA: Probing bus 0 at eisa.0
[    1.134105] EISA: Detected 0 cards.
[    1.134269] cpuidle: using governor ladder
[    1.134275] cpuidle: using governor menu
[    1.135814] TCP cubic registered
[    1.136342] NET: Registered protocol family 10
[    1.137592] lo: Disabled Privacy Extensions
[    1.138531] NET: Registered protocol family 17
[    1.138597] Bluetooth: L2CAP ver 2.13
[    1.138602] Bluetooth: L2CAP socket layer initialized
[    1.138611] Bluetooth: SCO (Voice Link) ver 0.6
[    1.138616] Bluetooth: SCO socket layer initialized
[    1.138762] Bluetooth: RFCOMM TTY layer initialized
[    1.138772] Bluetooth: RFCOMM socket layer initialized
[    1.138777] Bluetooth: RFCOMM ver 1.11
[    1.138896] Using IPI No-Shortcut mode
[    1.139124] PM: Resume from disk failed.
[    1.139164] registered taskstats version 1
[    1.139448]   Magic number: 1:406:956
[    1.139620] rtc_cmos 00:02: setting system clock to 2009-11-02 22:55:29 UTC (1257202529)
[    1.139630] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.139635] EDD information not available.
[    1.158720] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input2
[    1.288573] ata1.00: native sectors (39102335) is smaller than sectors (39102336)
[    1.288588] ata1.00: ATA-4: ST320413A, 3.39, max UDMA/100
[    1.288595] ata1.00: 39102336 sectors, multi 16: LBA 
[    1.304453] ata2.00: ATAPI: SAMSUNG CD-R/RW DRIVE SW-248B, R500, max UDMA/33
[    1.304546] ata2.01: ATAPI: IOMEGA  ZIP 100       ATAPI, 12.A, max PIO3, CDB intr
[    1.305275] ata1.00: configured for UDMA/66
[    1.305689] scsi 0:0:0:0: Direct-Access     ATA      ST320413A        3.39 PQ: 0 ANSI: 5
[    1.306064] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    1.306190] sd 0:0:0:0: [sda] 39102336 512-byte logical blocks: (20.0 GB/18.6 GiB)
[    1.306333] sd 0:0:0:0: [sda] Write Protect is off
[    1.306341] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.306414] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.306810]  sda:
[    1.320279] ata2.00: configured for UDMA/33
[    1.330343]  sda1 sda2 <
[    1.336262] ata2.01: configured for PIO3
[    1.339963] scsi 1:0:0:0: CD-ROM            SAMSUNG  CD-R/RW SW-248B  R500 PQ: 0 ANSI: 5
[    1.343936] sr0: scsi3-mmc drive: 48x/1x writer cd/rw xa/form2 cdda tray
[    1.343945] Uniform CD-ROM driver Revision: 3.20
[    1.344243] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    1.344397] sr 1:0:0:0: Attached scsi generic sg1 type 5
[    1.348873] scsi 1:0:1:0: Direct-Access     IOMEGA   ZIP 100          12.A PQ: 0 ANSI: 5
[    1.349184] sd 1:0:1:0: Attached scsi generic sg2 type 0
[    1.353054] sd 1:0:1:0: [sdb] Attached SCSI removable disk
[    1.356408]  sda5 >
[    1.357233] sd 0:0:0:0: [sda] Attached SCSI disk
[    1.357290] Freeing unused kernel memory: 540k freed
[    1.359968] Write protecting the kernel text: 4568k
[    1.360167] Write protecting the kernel read-only data: 1836k
[    1.444148] usb 1-1: new low speed USB device using uhci_hcd and address 2
[    1.651958] usb 1-1: configuration #1 chosen from 1 choice
[    1.764200] usb 1-2: new full speed USB device using uhci_hcd and address 3
[    1.883682] Linux agpgart interface v0.103
[    1.949210] agpgart-intel 0000:00:00.0: Intel i810 Chipset
[    2.114951] usb 1-2: configuration #1 chosen from 1 choice
[    2.138614] pci 0000:00:01.0: detected 4MB dedicated video ram
[    2.140876] agpgart-intel 0000:00:00.0: AGP aperture is 64M @ 0xf8000000
[    2.141350] Floppy drive(s): fd0 is 1.44M
[    2.161317] FDC 0 is a post-1991 82077
[    2.187583] dmfe: Davicom DM9xxx net driver, version 1.36.4 (2002-01-17)
[    2.188241] ACPI: PCI Interrupt Link [LNKC] enabled at IRQ 3
[    2.188251] PCI: setting IRQ 3 as level-triggered
[    2.188262] dmfe 0000:01:0a.0: PCI INT A -> Link[LNKC] -> GSI 3 (level, low) -> IRQ 3
[    2.324872] usbcore: registered new interface driver hiddev
[    2.346076] eth0: Davicom DM9102 at pci0000:01:0a.0, 00:80:ad:0d:6a:25, irq 3.
[    2.378988] input: Microsoft Microsoft Wireless Optical Mouse® 1.00 as /devices/pci0000:00/0000:00:1f.2/usb1/1-1/1-1:1.0/input/input3
[    2.379241] generic-usb 0003:045E:00E1.0001: input,hidraw0: USB HID v1.11 Mouse [Microsoft Microsoft Wireless Optical Mouse® 1.00] on usb-0000:00:1f.2-1/input0
[    2.379317] usbcore: registered new interface driver usbhid
[    2.379327] usbhid: v2.6:USB HID core driver
[    4.082318] PM: Starting manual resume from disk
[    4.082339] PM: Resume from partition 8:5
[    4.082344] PM: Checking hibernation image.
[    4.083026] PM: Resume from disk failed.
[    4.157097] kjournald starting.  Commit interval 5 seconds
[    4.157148] EXT3-fs: mounted filesystem with writeback data mode.
[    5.918901] type=1505 audit(1257202534.277:2): operation="profile_load" pid=317 name=/sbin/dhclient3
[    5.920155] type=1505 audit(1257202534.280:3): operation="profile_load" pid=317 name=/usr/lib/NetworkManager/nm-dhcp-client.action
[    5.920806] type=1505 audit(1257202534.280:4): operation="profile_load" pid=317 name=/usr/lib/connman/scripts/dhclient-script
[    6.034360] type=1505 audit(1257202534.392:5): operation="profile_load" pid=318 name=/usr/bin/evince
[    6.057735] type=1505 audit(1257202534.416:6): operation="profile_load" pid=318 name=/usr/bin/evince-previewer
[    6.071606] type=1505 audit(1257202534.428:7): operation="profile_load" pid=318 name=/usr/bin/evince-thumbnailer
[    6.202072] type=1505 audit(1257202534.560:8): operation="profile_load" pid=320 name=/usr/lib/cups/backend/cups-pdf
[    6.203572] type=1505 audit(1257202534.560:9): operation="profile_load" pid=320 name=/usr/sbin/cupsd
[    6.253638] type=1505 audit(1257202534.612:10): operation="profile_load" pid=321 name=/usr/sbin/tcpdump
[    8.727989] Adding 730916k swap on /dev/sda5.  Priority:-1 extents:1 across:730916k 
[   10.612855] EXT3 FS on sda1, internal journal
[   13.876654] udev: starting version 147
[   17.419150] lp: driver loaded but no devices found
[   17.506624] dcdbas dcdbas: Dell Systems Management Base Driver (version 5.6.0-3.2)
[   17.557487] dell-wmi: No known WMI GUID found
[   18.239363] ip_tables: (C) 2000-2006 Netfilter Core Team
[   18.846579] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   18.877273] psmouse serio1: ID: 10 00 64
[   18.880129] intel_rng: Firmware space is locked read-only. If you can't or
[   18.880135] intel_rng: don't want to disable this in firmware setup, and if
[   18.880139] intel_rng: you are certain that your system has a functional
[   18.880142] intel_rng: RNG, try using the 'no_fwh_detect' option.
[   18.928136] parport_pc 00:09: reported by Plug and Play ACPI
[   18.928177] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE,EPP]
[   18.992983] ppdev: user-space parallel port driver
[   19.024551] lp0: using parport0 (interrupt-driven).
[   19.422780] input: ImPS/2 Generic Wheel Mouse as /devices/platform/i8042/serio1/input/input4
[   20.078367] cfg80211: Calling CRDA to update world regulatory domain
[   21.625551] cfg80211: World regulatory domain updated:
[   21.625570] 	(start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   21.625579] 	(2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   21.625587] 	(2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   21.625595] 	(2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   21.625602] 	(5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   21.625610] 	(5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   23.135831] type=1505 audit(1257202551.492:11): operation="profile_replace" pid=638 name=/sbin/dhclient3
[   23.138211] type=1505 audit(1257202551.496:12): operation="profile_replace" pid=638 name=/usr/lib/NetworkManager/nm-dhcp-client.action
[   23.138879] type=1505 audit(1257202551.496:13): operation="profile_replace" pid=638 name=/usr/lib/connman/scripts/dhclient-script
[   23.190573] type=1505 audit(1257202551.548:14): operation="profile_replace" pid=639 name=/usr/bin/evince
[   23.261986] type=1505 audit(1257202551.620:15): operation="profile_replace" pid=639 name=/usr/bin/evince-previewer
[   23.281249] type=1505 audit(1257202551.640:16): operation="profile_replace" pid=639 name=/usr/bin/evince-thumbnailer
[   23.311525] type=1505 audit(1257202551.668:17): operation="profile_replace" pid=654 name=/usr/lib/cups/backend/cups-pdf
[   23.313190] type=1505 audit(1257202551.672:18): operation="profile_replace" pid=654 name=/usr/sbin/cupsd
[   23.321914] type=1505 audit(1257202551.680:19): operation="profile_replace" pid=655 name=/usr/sbin/tcpdump
[   24.085093] phy0: Selected rate control algorithm 'minstrel'
[   24.087082] Registered led device: rt2500usb-phy0::radio
[   24.087127] Registered led device: rt2500usb-phy0::quality
[   24.093112] usbcore: registered new interface driver rt2500usb
[   24.289819] ACPI: PCI Interrupt Link [LNKB] enabled at IRQ 10
[   24.289834] PCI: setting IRQ 10 as level-triggered
[   24.289845] ENS1371 0000:01:09.0: PCI INT A -> Link[LNKB] -> GSI 10 (level, low) -> IRQ 10
[   38.974772] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   39.434784] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   46.072531] [drm] Initialized drm 1.1.0 20060810
[   46.124877] ACPI: PCI Interrupt Link [LNKA] enabled at IRQ 11
[   46.124892] PCI: setting IRQ 11 as level-triggered
[   46.124904] pci 0000:00:01.0: PCI INT A -> Link[LNKA] -> GSI 11 (level, low) -> IRQ 11
[   46.124915] pci 0000:00:01.0: setting latency timer to 64
[   46.125567] [drm] Initialized i810 1.4.0 20030605 for 0000:00:01.0 on minor 0
[   46.132705] mtrr: base(0xf8000000) is not aligned on a size(0x1e6000) boundary
[   46.335886] [drm] Using v1.4 init.
[   50.368031] [drm:drm_reclaim_locked_buffers] *ERROR* reclaim_buffers_locked() deadlock. Please rework this
[   50.368041] 	driver to use reclaim_buffers_idlelocked() instead.
[   50.368044] 	I will go on reclaiming the buffers anyway.
[ 1152.428038] [drm:i810_wait_ring] *ERROR* space: 65520 wanted 65528
[ 1152.428107] [drm:i810_wait_ring] *ERROR* lockup
[ 1154.420234] mtrr: base(0xf8000000) is not aligned on a size(0x1e6000) boundary
[ 1154.571212] [drm] Using v1.4 init.
[ 1157.756030] [drm:drm_reclaim_locked_buffers] *ERROR* reclaim_buffers_locked() deadlock. Please rework this
[ 1157.756041] 	driver to use reclaim_buffers_idlelocked() instead.
[ 1157.756044] 	I will go on reclaiming the buffers anyway.
[ 1208.684040] [drm:i810_wait_ring] *ERROR* space: 65520 wanted 65528
[ 1208.684109] [drm:i810_wait_ring] *ERROR* lockup
[ 1211.267477] mtrr: base(0xf8000000) is not aligned on a size(0x1e6000) boundary
[ 1211.414783] [drm] Using v1.4 init.
[ 1214.580031] [drm:drm_reclaim_locked_buffers] *ERROR* reclaim_buffers_locked() deadlock. Please rework this
[ 1214.580041] 	driver to use reclaim_buffers_idlelocked() instead.
[ 1214.580045] 	I will go on reclaiming the buffers anyway.
[ 1242.932039] [drm:i810_wait_ring] *ERROR* space: 65520 wanted 65528
[ 1242.932103] [drm:i810_wait_ring] *ERROR* lockup
[ 1245.508270] mtrr: base(0xf8000000) is not aligned on a size(0x1e6000) boundary
[ 1245.655237] [drm] Using v1.4 init.
[ 1248.820029] [drm:drm_reclaim_locked_buffers] *ERROR* reclaim_buffers_locked() deadlock. Please rework this
[ 1248.820038] 	driver to use reclaim_buffers_idlelocked() instead.
[ 1248.820041] 	I will go on reclaiming the buffers anyway.
[ 1354.604028] [drm:drm_reclaim_locked_buffers] *ERROR* reclaim_buffers_locked() deadlock. Please rework this
[ 1354.604036] 	driver to use reclaim_buffers_idlelocked() instead.
[ 1354.604039] 	I will go on reclaiming the buffers anyway.
[ 1354.687019] [drm] DMA Cleanup
[ 1354.767736] mtrr: no MTRR for f8000000,3000000 found
[ 1355.952526] mtrr: base(0xf8000000) is not aligned on a size(0x1e6000) boundary
[ 1356.101189] [drm] Using v1.4 init.
[ 1359.264032] [drm:drm_reclaim_locked_buffers] *ERROR* reclaim_buffers_locked() deadlock. Please rework this
[ 1359.264043] 	driver to use reclaim_buffers_idlelocked() instead.
[ 1359.264047] 	I will go on reclaiming the buffers anyway.
[ 1468.544076] [drm:drm_reclaim_locked_buffers] *ERROR* reclaim_buffers_locked() deadlock. Please rework this
[ 1468.544084] 	driver to use reclaim_buffers_idlelocked() instead.
[ 1468.544087] 	I will go on reclaiming the buffers anyway.
[ 1468.615886] [drm] DMA Cleanup
[ 1468.696973] mtrr: no MTRR for f8000000,3000000 found
[ 1469.580118] mtrr: base(0xf8000000) is not aligned on a size(0x1e6000) boundary
[ 1469.729226] [drm] Using v1.4 init.
[ 1472.896030] [drm:drm_reclaim_locked_buffers] *ERROR* reclaim_buffers_locked() deadlock. Please rework this
[ 1472.896040] 	driver to use reclaim_buffers_idlelocked() instead.
[ 1472.896043] 	I will go on reclaiming the buffers anyway.
[ 1527.804044] [drm:i810_wait_ring] *ERROR* space: 65520 wanted 65528
[ 1527.804110] [drm:i810_wait_ring] *ERROR* lockup
[ 1530.424123] mtrr: base(0xf8000000) is not aligned on a size(0x1e6000) boundary
[ 1530.571189] [drm] Using v1.4 init.
[ 1533.736031] [drm:drm_reclaim_locked_buffers] *ERROR* reclaim_buffers_locked() deadlock. Please rework this
[ 1533.736040] 	driver to use reclaim_buffers_idlelocked() instead.
[ 1533.736044] 	I will go on reclaiming the buffers anyway.
[ 1651.520042] [drm:i810_wait_ring] *ERROR* space: 65520 wanted 65528
[ 1651.520107] [drm:i810_wait_ring] *ERROR* lockup
[ 1654.102639] mtrr: base(0xf8000000) is not aligned on a size(0x1e6000) boundary
[ 1654.249591] [drm] Using v1.4 init.
[ 1657.416030] [drm:drm_reclaim_locked_buffers] *ERROR* reclaim_buffers_locked() deadlock. Please rework this
[ 1657.416039] 	driver to use reclaim_buffers_idlelocked() instead.
[ 1657.416042] 	I will go on reclaiming the buffers anyway.
[ 1701.948041] [drm:i810_wait_ring] *ERROR* space: 65520 wanted 65528
[ 1701.948106] [drm:i810_wait_ring] *ERROR* lockup
[ 1704.577620] mtrr: base(0xf8000000) is not aligned on a size(0x1e6000) boundary
[ 1704.726773] [drm] Using v1.4 init.
[ 1707.892029] [drm:drm_reclaim_locked_buffers] *ERROR* reclaim_buffers_locked() deadlock. Please rework this
[ 1707.892039] 	driver to use reclaim_buffers_idlelocked() instead.
[ 1707.892043] 	I will go on reclaiming the buffers anyway.
[ 2276.112062] [drm:drm_reclaim_locked_buffers] *ERROR* reclaim_buffers_locked() deadlock. Please rework this
[ 2276.112069] 	driver to use reclaim_buffers_idlelocked() instead.
[ 2276.112073] 	I will go on reclaiming the buffers anyway.
[ 2276.192068] [drm] DMA Cleanup
[ 2276.273138] mtrr: no MTRR for f8000000,3000000 found
[ 2277.159049] mtrr: base(0xf8000000) is not aligned on a size(0x1e6000) boundary
[ 2277.305852] [drm] Using v1.4 init.
[ 2280.472028] [drm:drm_reclaim_locked_buffers] *ERROR* reclaim_buffers_locked() deadlock. Please rework this
[ 2280.472035] 	driver to use reclaim_buffers_idlelocked() instead.
[ 2280.472039] 	I will go on reclaiming the buffers anyway.
[ 2326.284059] [drm:drm_reclaim_locked_buffers] *ERROR* reclaim_buffers_locked() deadlock. Please rework this
[ 2326.284067] 	driver to use reclaim_buffers_idlelocked() instead.
[ 2326.284071] 	I will go on reclaiming the buffers anyway.
[ 2326.363925] [drm] DMA Cleanup
[ 2326.445038] mtrr: no MTRR for f8000000,3000000 found
[ 2327.333390] mtrr: base(0xf8000000) is not aligned on a size(0x1e6000) boundary
[ 2327.480744] [drm] Using v1.4 init.
[ 2330.644033] [drm:drm_reclaim_locked_buffers] *ERROR* reclaim_buffers_locked() deadlock. Please rework this
[ 2330.644044] 	driver to use reclaim_buffers_idlelocked() instead.
[ 2330.644047] 	I will go on reclaiming the buffers anyway.
[ 2360.956038] [drm:i810_wait_ring] *ERROR* space: 65520 wanted 65528
[ 2360.956144] [drm:i810_wait_ring] *ERROR* lockup
[ 2363.560131] mtrr: base(0xf8000000) is not aligned on a size(0x1e6000) boundary
[ 2363.710631] [drm] Using v1.4 init.
[ 2366.876030] [drm:drm_reclaim_locked_buffers] *ERROR* reclaim_buffers_locked() deadlock. Please rework this
[ 2366.876039] 	driver to use reclaim_buffers_idlelocked() instead.
[ 2366.876043] 	I will go on reclaiming the buffers anyway.
[ 2397.568042] [drm:i810_wait_ring] *ERROR* space: 65520 wanted 65528
[ 2397.568127] [drm:i810_wait_ring] *ERROR* lockup
[ 2400.181018] mtrr: base(0xf8000000) is not aligned on a size(0x1e6000) boundary
[ 2400.328427] [drm] Using v1.4 init.
[ 2403.492032] [drm:drm_reclaim_locked_buffers] *ERROR* reclaim_buffers_locked() deadlock. Please rework this
[ 2403.492042] 	driver to use reclaim_buffers_idlelocked() instead.
[ 2403.492046] 	I will go on reclaiming the buffers anyway.
[ 2428.512043] [drm:i810_wait_ring] *ERROR* space: 65520 wanted 65528
[ 2428.512134] [drm:i810_wait_ring] *ERROR* lockup
[ 2431.123582] mtrr: base(0xf8000000) is not aligned on a size(0x1e6000) boundary
[ 2431.270641] [drm] Using v1.4 init.
[ 2434.436029] [drm:drm_reclaim_locked_buffers] *ERROR* reclaim_buffers_locked() deadlock. Please rework this
[ 2434.436038] 	driver to use reclaim_buffers_idlelocked() instead.
[ 2434.436041] 	I will go on reclaiming the buffers anyway.
[ 2692.116201] wlan0: authenticate with AP 00:22:3f:7e:7d:b2
[ 2692.265698] wlan0: authenticated
[ 2692.265720] wlan0: associate with AP 00:22:3f:7e:7d:b2
[ 2692.286758] wlan0: RX AssocResp from 00:22:3f:7e:7d:b2 (capab=0x411 status=0 aid=4)
[ 2692.286773] wlan0: associated
[ 2692.377543] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 2703.116037] wlan0: no IPv6 routers present
[ 3902.401404] wlan0: disassociating by local choice (reason=3)
[ 3906.072036] [drm:drm_reclaim_locked_buffers] *ERROR* reclaim_buffers_locked() deadlock. Please rework this
[ 3906.072045] 	driver to use reclaim_buffers_idlelocked() instead.
[ 3906.072049] 	I will go on reclaiming the buffers anyway.
[ 3906.440132] [drm] DMA Cleanup
[ 3906.596694] mtrr: no MTRR for f8000000,3000000 found
[ 3908.874259] mtrr: base(0xf8000000) is not aligned on a size(0x1e6000) boundary
[ 3909.027709] [drm] Using v1.4 init.
[ 3912.196032] [drm:drm_reclaim_locked_buffers] *ERROR* reclaim_buffers_locked() deadlock. Please rework this
[ 3912.196044] 	driver to use reclaim_buffers_idlelocked() instead.
[ 3912.196047] 	I will go on reclaiming the buffers anyway.
[ 4002.748035] [drm:drm_reclaim_locked_buffers] *ERROR* reclaim_buffers_locked() deadlock. Please rework this
[ 4002.748042] 	driver to use reclaim_buffers_idlelocked() instead.
[ 4002.748046] 	I will go on reclaiming the buffers anyway.
[ 4002.817381] [drm] DMA Cleanup
[ 4002.898536] mtrr: no MTRR for f8000000,3000000 found
[ 4003.795378] mtrr: base(0xf8000000) is not aligned on a size(0x1e6000) boundary
[ 4003.948683] [drm] Using v1.4 init.
[ 4007.116031] [drm:drm_reclaim_locked_buffers] *ERROR* reclaim_buffers_locked() deadlock. Please rework this
[ 4007.116043] 	driver to use reclaim_buffers_idlelocked() instead.
[ 4007.116046] 	I will go on reclaiming the buffers anyway.
[ 4039.020039] [drm:i810_wait_ring] *ERROR* space: 65520 wanted 65528
[ 4039.020123] [drm:i810_wait_ring] *ERROR* lockup
[ 4040.338224] mtrr: base(0xf8000000) is not aligned on a size(0x1e6000) boundary
[ 4040.560481] [drm] Using v1.4 init.
[ 4043.784031] [drm:drm_reclaim_locked_buffers] *ERROR* reclaim_buffers_locked() deadlock. Please rework this
[ 4043.784039] 	driver to use reclaim_buffers_idlelocked() instead.
[ 4043.784043] 	I will go on reclaiming the buffers anyway.
[ 4179.080535] wlan0: authenticate with AP 00:22:3f:7e:7d:b2
[ 4179.084490] wlan0: authenticated
[ 4179.084509] wlan0: associate with AP 00:22:3f:7e:7d:b2
[ 4179.087863] wlan0: RX AssocResp from 00:22:3f:7e:7d:b2 (capab=0x411 status=0 aid=2)
[ 4179.087876] wlan0: associated
[ 5446.543126] wlan0: disassociating by local choice (reason=3)
[ 5449.592030] [drm:drm_reclaim_locked_buffers] *ERROR* reclaim_buffers_locked() deadlock. Please rework this
[ 5449.592037] 	driver to use reclaim_buffers_idlelocked() instead.
[ 5449.592041] 	I will go on reclaiming the buffers anyway.
[ 5449.687657] [drm] DMA Cleanup
[ 5449.789909] mtrr: no MTRR for f8000000,3000000 found
[ 5451.982371] mtrr: base(0xf8000000) is not aligned on a size(0x1e6000) boundary
[ 5452.133913] [drm] Using v1.4 init.
[ 5455.308031] [drm:drm_reclaim_locked_buffers] *ERROR* reclaim_buffers_locked() deadlock. Please rework this
[ 5455.308041] 	driver to use reclaim_buffers_idlelocked() instead.
[ 5455.308045] 	I will go on reclaiming the buffers anyway.
[ 5534.648032] [drm:drm_reclaim_locked_buffers] *ERROR* reclaim_buffers_locked() deadlock. Please rework this
[ 5534.648043] 	driver to use reclaim_buffers_idlelocked() instead.
[ 5534.648046] 	I will go on reclaiming the buffers anyway.
[ 5534.730589] [drm] DMA Cleanup
[ 5534.811523] mtrr: no MTRR for f8000000,3000000 found
[ 5535.806621] mtrr: base(0xf8000000) is not aligned on a size(0x1e6000) boundary
[ 5535.958822] [drm] Using v1.4 init.
[ 5539.128033] [drm:drm_reclaim_locked_buffers] *ERROR* reclaim_buffers_locked() deadlock. Please rework this
[ 5539.128043] 	driver to use reclaim_buffers_idlelocked() instead.
[ 5539.128047] 	I will go on reclaiming the buffers anyway.
[ 5567.168040] [drm:i810_wait_ring] *ERROR* space: 65520 wanted 65528
[ 5567.168130] [drm:i810_wait_ring] *ERROR* lockup
[ 5569.742963] mtrr: base(0xf8000000) is not aligned on a size(0x1e6000) boundary
[ 5569.893980] [drm] Using v1.4 init.
[ 5573.060031] [drm:drm_reclaim_locked_buffers] *ERROR* reclaim_buffers_locked() deadlock. Please rework this
[ 5573.060039] 	driver to use reclaim_buffers_idlelocked() instead.
[ 5573.060043] 	I will go on reclaiming the buffers anyway.
[ 5615.156044] [drm:i810_wait_ring] *ERROR* space: 65520 wanted 65528
[ 5615.156129] [drm:i810_wait_ring] *ERROR* lockup
[ 5617.880384] mtrr: base(0xf8000000) is not aligned on a size(0x1e6000) boundary
[ 5618.035536] [drm] Using v1.4 init.
[ 5621.204030] [drm:drm_reclaim_locked_buffers] *ERROR* reclaim_buffers_locked() deadlock. Please rework this
[ 5621.204039] 	driver to use reclaim_buffers_idlelocked() instead.
[ 5621.204043] 	I will go on reclaiming the buffers anyway.
[ 5693.480296] wlan0: authenticate with AP 00:22:3f:7e:7d:b2
[ 5693.482311] wlan0: authenticated
[ 5693.482318] wlan0: associate with AP 00:22:3f:7e:7d:b2
[ 5693.489247] wlan0: RX AssocResp from 00:22:3f:7e:7d:b2 (capab=0x411 status=0 aid=2)
[ 5693.489263] wlan0: associated
[ 6300.007899] wlan0: disassociating by local choice (reason=3)
[ 6302.912031] [drm:drm_reclaim_locked_buffers] *ERROR* reclaim_buffers_locked() deadlock. Please rework this
[ 6302.912040] 	driver to use reclaim_buffers_idlelocked() instead.
[ 6302.912043] 	I will go on reclaiming the buffers anyway.
[ 6303.016747] [drm] DMA Cleanup
[ 6303.106531] mtrr: no MTRR for f8000000,3000000 found
[ 6305.232834] mtrr: base(0xf8000000) is not aligned on a size(0x1e6000) boundary
[ 6305.389301] [drm] Using v1.4 init.
[ 6308.556029] [drm:drm_reclaim_locked_buffers] *ERROR* reclaim_buffers_locked() deadlock. Please rework this
[ 6308.556037] 	driver to use reclaim_buffers_idlelocked() instead.
[ 6308.556041] 	I will go on reclaiming the buffers anyway.
[ 6463.896079] [drm:drm_reclaim_locked_buffers] *ERROR* reclaim_buffers_locked() deadlock. Please rework this
[ 6463.896087] 	driver to use reclaim_buffers_idlelocked() instead.
[ 6463.896090] 	I will go on reclaiming the buffers anyway.
[ 6463.968179] [drm] DMA Cleanup
[ 6464.049352] mtrr: no MTRR for f8000000,3000000 found
[ 6464.937964] mtrr: base(0xf8000000) is not aligned on a size(0x1e6000) boundary
[ 6465.090353] [drm] Using v1.4 init.
[ 6468.256039] [drm:drm_reclaim_locked_buffers] *ERROR* reclaim_buffers_locked() deadlock. Please rework this
[ 6468.256049] 	driver to use reclaim_buffers_idlelocked() instead.
[ 6468.256053] 	I will go on reclaiming the buffers anyway.
[ 6511.608077] [drm:drm_reclaim_locked_buffers] *ERROR* reclaim_buffers_locked() deadlock. Please rework this
[ 6511.608086] 	driver to use reclaim_buffers_idlelocked() instead.
[ 6511.608089] 	I will go on reclaiming the buffers anyway.
[ 6511.680779] [drm] DMA Cleanup
[ 6511.761851] mtrr: no MTRR for f8000000,3000000 found
[ 6512.651416] mtrr: base(0xf8000000) is not aligned on a size(0x1e6000) boundary
[ 6512.804000] [drm] Using v1.4 init.
[ 6515.973346] [drm:drm_reclaim_locked_buffers] *ERROR* reclaim_buffers_locked() deadlock. Please rework this
[ 6515.973354] 	driver to use reclaim_buffers_idlelocked() instead.
[ 6515.973357] 	I will go on reclaiming the buffers anyway.
[ 6547.356042] [drm:i810_wait_ring] *ERROR* space: 65520 wanted 65528
[ 6547.356126] [drm:i810_wait_ring] *ERROR* lockup
[ 6549.998646] mtrr: base(0xf8000000) is not aligned on a size(0x1e6000) boundary
[ 6550.155129] [drm] Using v1.4 init.
[ 6553.324032] [drm:drm_reclaim_locked_buffers] *ERROR* reclaim_buffers_locked() deadlock. Please rework this
[ 6553.324043] 	driver to use reclaim_buffers_idlelocked() instead.
[ 6553.324047] 	I will go on reclaiming the buffers anyway.
[ 6605.756924] wlan0: authenticate with AP 00:22:3f:7e:7d:b2
[ 6605.758914] wlan0: authenticated
[ 6605.758921] wlan0: associate with AP 00:22:3f:7e:7d:b2
[ 6605.763732] wlan0: RX AssocResp from 00:22:3f:7e:7d:b2 (capab=0x411 status=0 aid=2)
[ 6605.763747] wlan0: associated

```

(bump)

---

### Post by ixifx on 2009-11-02
alrighty

using the xterm session I logged in and went to /etc/X11

noticed I had an xorg.conf and another file named xorg.conf.dist-upgrade-200911021403

so I thought maybe the second file was a backup from before the upgrade so I did

cp /etc/X11/xorg.conf.dist-upgrade-200911021403 /etc/X11/xorg.conf

and tried again, still with no luck.

then did sudo mousepad xorg.conf and saw this

# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

so I did 

sudo dpkg-reconfigure -phigh xserver-xorg

and now it appears as if everything is running smoothly again.

will have to restart and log in again to be certain, but I think I fixed it.

thanks again, ubuntuforums.org =D

---

