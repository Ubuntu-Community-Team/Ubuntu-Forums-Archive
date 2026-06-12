---
title: "sticky mouse with false button presses?"
date: 2009-08-26
forum: General Help
---

### Post by keastes on 2009-08-26
i'm running xubuntu 9.04 "Jaunty Jackalope" on a 800MHz Pentium 3 with 256b MiB ram and i have a problem with my mouse jumping and sticking to the upper-right corner of the screen and clicking on the quit button. does any one know how to fix this? 

i searched the forum and could not find this mentioned other than in passing, but could bbe that i cant search right now. 

 i'm a semi linux-n00b does anyone know how to fix?

---

### Post by danwood76 on 2009-08-26
What type of mouse is it?
If it is a ball mouse take the ball out and clean the rollers.

Does the mouse work ok in another PC?

---

### Post by keastes on 2009-08-26
> **danwood76 said:**
> What type of mouse is it?
If it is a ball mouse take the ball out and clean the rollers.

Does the mouse work ok in another PC?


ps/2 ball mouse best way i've found to fix it is to unplug and replugin the mouse,

---

### Post by danwood76 on 2009-08-26
And that clears it up?

Could you try another mouse?
I am inclined to think this is a hardware issue rather than a software issue.

---

### Post by keastes on 2009-08-26
i've seen it mentioned a couple of times but no fixes so i have no idea what it is

---

### Post by danwood76 on 2009-08-26
It is probably a faulty mouse.

The way to rule it out is to use a different mouse and see if the problem occurs with it.

Hardware does fail from time to time and if its a ball mouse then its probably pretty old.

---

### Post by keastes on 2009-08-27
oh well thanks any way

---

### Post by P4man on 2009-08-27
Im not so sure this is a "hardware mouse" problem. Have a look here:

[http://ubuntuforums.org/showthread.php?t=92611](http://ubuntuforums.org/showthread.php?t=92611)

Yes, its *very* old, but is it the same behaviour?

Can you perhaps attach the output of dmesg?

---

### Post by danwood76 on 2009-08-27
Mice generally use the same driver.

Until another mouse is tested on the machine or the mouse is tested on another system hardware cannot be ruled out and should be tested!!

---

### Post by keastes on 2009-08-29
dmesg would not pipe to a text file so here you go:

```
kisuke@kisuke-desktop:~$ dmesg
[    0.000000] BIOS EBDA/lowmem at: 0009fc00/0009fc00
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.28-15-generic (buildd@palmer) (gcc version 4.3.3 (Ubuntu 4.3.3-5ubuntu4) ) #49-Ubuntu SMP Tue Aug 18 18:40:08 UTC 2009 (Ubuntu 2.6.28-15.49-generic)
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
[    0.000000] Scanning 2 areas for low memory corruption
[    0.000000] modified physical RAM map:
[    0.000000]  modified: 0000000000000000 - 0000000000002000 (usable)
[    0.000000]  modified: 0000000000002000 - 0000000000006000 (reserved)
[    0.000000]  modified: 0000000000006000 - 0000000000007000 (usable)
[    0.000000]  modified: 0000000000007000 - 0000000000010000 (reserved)
[    0.000000]  modified: 0000000000010000 - 0000000000092c00 (usable)
[    0.000000]  modified: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  modified: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  modified: 0000000000100000 - 000000000fec0000 (usable)
[    0.000000]  modified: 000000000fec0000 - 000000000fef8000 (ACPI data)
[    0.000000]  modified: 000000000fef8000 - 000000000ff00000 (ACPI NVS)
[    0.000000]  modified: 00000000ffb80000 - 00000000ffc00000 (reserved)
[    0.000000]  modified: 00000000fff00000 - 0000000100000000 (reserved)
[    0.000000] kernel direct mapping tables up to fec0000 @ 10000-16000
[    0.000000] RAMDISK: 0f726000 - 0feaf837
[    0.000000] ACPI: RSDP 000FF980, 0014 (r0 AMI   )
[    0.000000] ACPI: RSDT 0FEF0000, 0028 (r1 DELL   MUMMY    20001113 MSFT       97)
[    0.000000] ACPI: FACP 0FEF1000, 0074 (r1 DELL   MUMMY    20001113 MSFT       97)
[    0.000000] ACPI: DSDT 0FEE0000, 27F4 (r1 DELL   DIM_L          12 MSFT  100000B)
[    0.000000] ACPI: FACS 0FEF8000, 0040
[    0.000000] 0MB HIGHMEM available.
[    0.000000] 254MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 0fec0000
[    0.000000]   low ram: 00000000 - 0fec0000
[    0.000000]   bootmap 00012000 - 00013fd8
[    0.000000] (9 early reservations) ==> bootmem [0000000000 - 000fec0000]
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
[    0.000000]   #1 [0000001000 - 0000002000]    EX TRAMPOLINE ==> [0000001000 - 0000002000]
[    0.000000]   #2 [0000006000 - 0000007000]       TRAMPOLINE ==> [0000006000 - 0000007000]
[    0.000000]   #3 [0000100000 - 00008780ac]    TEXT DATA BSS ==> [0000100000 - 00008780ac]
[    0.000000]   #4 [000f726000 - 000feaf837]          RAMDISK ==> [000f726000 - 000feaf837]
[    0.000000]   #5 [0000879000 - 000087d000]    INIT_PG_TABLE ==> [0000879000 - 000087d000]
[    0.000000]   #6 [000009fc00 - 0000100000]    BIOS reserved ==> [000009fc00 - 0000100000]
[    0.000000]   #7 [0000010000 - 0000012000]          PGTABLE ==> [0000010000 - 0000012000]
[    0.000000]   #8 [0000012000 - 0000014000]          BOOTMAP ==> [0000012000 - 0000014000]
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000000 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x0000fec0
[    0.000000]   HighMem  0x0000fec0 -> 0x0000fec0
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[4] active PFN ranges
[    0.000000]     0: 0x00000000 -> 0x00000002
[    0.000000]     0: 0x00000006 -> 0x00000007
[    0.000000]     0: 0x00000010 -> 0x00000092
[    0.000000]     0: 0x00000100 -> 0x0000fec0
[    0.000000] On node 0 totalpages: 65093
[    0.000000] free_area_init_node: node 0, pgdat c06cb500, node_mem_map c1000000
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3941 pages, LIFO batch:0
[    0.000000]   Normal zone: 478 pages used for memmap
[    0.000000]   Normal zone: 60642 pages, LIFO batch:15
[    0.000000]   HighMem zone: 0 pages used for memmap
[    0.000000]   Movable zone: 0 pages used for memmap
[    0.000000] ACPI: PM-Timer IO Port: 0x408
[    0.000000] SMP: Allowing 1 CPUs, 0 hotplug CPUs
[    0.000000] Local APIC disabled by BIOS -- you can enable it with "lapic"
[    0.000000] PM: Registered nosave memory: 0000000000002000 - 0000000000006000
[    0.000000] PM: Registered nosave memory: 0000000000007000 - 0000000000010000
[    0.000000] PM: Registered nosave memory: 0000000000092000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
[    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 10000000 (gap: ff00000:efc80000)
[    0.000000] PERCPU: Allocating 45056 bytes of per cpu data
[    0.000000] NR_CPUS: 64, nr_cpu_ids: 1, nr_node_ids 1
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 64583
[    0.000000] Kernel command line: root=UUID=c32c971f-d9af-4765-8e87-d528bc6e82e9 ro quiet splash 
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 1024 (order: 10, 4096 bytes)
[    0.000000] TSC: PIT calibration matches PMTIMER. 1 loops
[    0.000000] Detected 797.359 MHz processor.
[    0.004000] Console: colour VGA+ 80x25
[    0.004000] console [tty0] enabled
[    0.004000] Dentry cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.004000] Inode-cache hash table entries: 16384 (order: 4, 65536 bytes)
[    0.004000] allocated 1304320 bytes of page_cgroup
[    0.004000] please try cgroup_disable=memory option if you don't want
[    0.004000] Scanning for low memory corruption every 60 seconds
[    0.004000] Memory: 241272k/260864k available (4115k kernel code, 19008k reserved, 2199k data, 532k init, 0k highmem)
[    0.004000] virtual kernel memory layout:
[    0.004000]     fixmap  : 0xffc77000 - 0xfffff000   (3616 kB)
[    0.004000]     pkmap   : 0xff400000 - 0xff800000   (4096 kB)
[    0.004000]     vmalloc : 0xd06c0000 - 0xff3fe000   ( 749 MB)
[    0.004000]     lowmem  : 0xc0000000 - 0xcfec0000   ( 254 MB)
[    0.004000]       .init : 0xc0733000 - 0xc07b8000   ( 532 kB)
[    0.004000]       .data : 0xc0504f5f - 0xc072ae60   (2199 kB)
[    0.004000]       .text : 0xc0100000 - 0xc0504f5f   (4115 kB)
[    0.004000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.004000] SLUB: Genslabs=12, HWalign=32, Order=0-3, MinObjects=0, CPUs=1, Nodes=1
[    0.004024] Calibrating delay loop (skipped), value calculated using timer frequency.. 1594.71 BogoMIPS (lpj=3189436)
[    0.004078] Security Framework initialized
[    0.004104] SELinux:  Disabled at boot.
[    0.004162] AppArmor: AppArmor initialized
[    0.004188] Mount-cache hash table entries: 512
[    0.004550] Initializing cgroup subsys ns
[    0.004562] Initializing cgroup subsys cpuacct
[    0.004570] Initializing cgroup subsys memory
[    0.004580] Initializing cgroup subsys freezer
[    0.004623] CPU: L1 I cache: 16K, L1 D cache: 16K
[    0.004631] CPU: L2 cache: 256K
[    0.004640] CPU serial number disabled.
[    0.004681] Checking 'hlt' instruction... OK.
[    0.021260] SMP alternatives: switching to UP code
[    0.317976] Freeing SMP alternatives: 18k freed
[    0.317996] ACPI: Core revision 20080926
[    0.320321] ACPI: Checking initramfs for custom DSDT
[    1.136200] ACPI: setting ELCR to 0200 (from 0e08)
[    1.136660] weird, boot CPU (#0) not listedby the BIOS.
[    1.136666] SMP motherboard not detected.
[    1.136674] Local APIC not detected. Using dummy APIC emulation.
[    1.136680] SMP disabled
[    1.137581] Brought up 1 CPUs
[    1.137595] Total of 1 processors activated (1594.71 BogoMIPS).
[    1.137632] CPU0 attaching NULL sched-domain.
[    1.138594] net_namespace: 776 bytes
[    1.138639] Booting paravirtualized kernel on bare hardware
[    1.139420] Time:  4:11:26  Date: 08/29/09
[    1.139437] regulator: core version 0.5
[    1.139559] NET: Registered protocol family 16
[    1.139965] EISA bus registered
[    1.140038] ACPI: bus type pci registered
[    1.140957] PCI: PCI BIOS revision 2.10 entry at 0xfda95, last bus=1
[    1.140966] PCI: Using configuration type 1 for base access
[    1.145051] ACPI: EC: Look up EC in DSDT
[    1.157739] ACPI: Interpreter enabled
[    1.157761] ACPI: (supports S0 S1 S4 S5)
[    1.157812] ACPI: Using PIC for interrupt routing
[    1.165961] ACPI: No dock devices found.
[    1.165994] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    1.166149] pci 0000:00:01.0: reg 10 32bit mmio: [0xf8000000-0xfbffffff]
[    1.166162] pci 0000:00:01.0: reg 14 32bit mmio: [0xffa80000-0xffafffff]
[    1.166337] pci 0000:00:1f.0: quirk: region 0400-047f claimed by ICH4 ACPI/GPIO/TCO
[    1.166348] pci 0000:00:1f.0: quirk: region 0500-053f claimed by ICH4 GPIO
[    1.166400] pci 0000:00:1f.1: reg 20 io port: [0xffa0-0xffaf]
[    1.166471] pci 0000:00:1f.2: reg 20 io port: [0xef80-0xef9f]
[    1.166545] pci 0000:00:1f.3: reg 20 io port: [0xefa0-0xefaf]
[    1.166631] pci 0000:01:09.0: reg 10 io port: [0xdf00-0xdf3f]
[    1.166679] pci 0000:01:09.0: supports D1 D2
[    1.166723] pci 0000:01:0a.0: reg 10 32bit mmio: [0xff8f0000-0xff8f7fff]
[    1.166809] pci 0000:01:0b.0: reg 10 io port: [0xd800-0xd8ff]
[    1.166822] pci 0000:01:0b.0: reg 14 32bit mmio: [0xff8ffc00-0xff8fffff]
[    1.166855] pci 0000:01:0b.0: reg 30 32bit mmio: [0xff8c0000-0xff8dffff]
[    1.166871] pci 0000:01:0b.0: supports D1 D2
[    1.166878] pci 0000:01:0b.0: PME# supported from D0 D1 D2 D3hot
[    1.166888] pci 0000:01:0b.0: PME# disabled
[    1.166926] pci 0000:00:1e.0: transparent bridge
[    1.166935] pci 0000:00:1e.0: bridge io port: [0xd000-0xdfff]
[    1.166946] pci 0000:00:1e.0: bridge 32bit mmio: [0xff800000-0xff8fffff]
[    1.166957] pci 0000:00:1e.0: bridge 32bit mmio pref: [0xf6a00000-0xf6afffff]
[    1.166972] bus 00 -> node 0
[    1.166988] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    1.167296] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCI1._PRT]
[    1.169865] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)
[    1.170147] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 9 *10 11 12 14 15)
[    1.170427] ACPI: PCI Interrupt Link [LNKC] (IRQs *3 4 5 6 7 9 10 11 12 14 15)
[    1.170705] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 *9 10 11 12 14 15)
[    1.170931] ACPI: Power Resource [URP1] (off)
[    1.171022] ACPI: Power Resource [URP2] (off)
[    1.171112] ACPI: Power Resource [FDDP] (off)
[    1.171202] ACPI: Power Resource [LPTP] (off)
[    1.171365] ACPI: WMI: Mapper loaded
[    1.172075] SCSI subsystem initialized
[    1.172229] libata version 3.00 loaded.
[    1.172401] usbcore: registered new interface driver usbfs
[    1.172458] usbcore: registered new interface driver hub
[    1.172560] usbcore: registered new device driver usb
[    1.172926] PCI: Using ACPI for IRQ routing
[    1.173135] Bluetooth: Core ver 2.13
[    1.173135] NET: Registered protocol family 31
[    1.173135] Bluetooth: HCI device and connection manager initialized
[    1.173135] Bluetooth: HCI socket layer initialized
[    1.173135] NET: Registered protocol family 8
[    1.173135] NET: Registered protocol family 20
[    1.173135] NetLabel: Initializing
[    1.173135] NetLabel:  domain hash size = 128
[    1.173135] NetLabel:  protocols = UNLABELED CIPSOv4
[    1.173135] NetLabel:  unlabeled traffic allowed by default
[    1.173135] AppArmor: AppArmor Filesystem Enabled
[    1.173135] pnp: PnP ACPI init
[    1.173135] ACPI: bus type pnp registered
[    1.180662] pnp: PnP ACPI: found 12 devices
[    1.180670] ACPI: ACPI bus type pnp unregistered
[    1.180682] PnPBIOS: Disabled by ACPI PNP
[    1.180719] system 00:0b: iomem range 0x0-0x9ffff could not be reserved
[    1.180729] system 00:0b: iomem range 0xe0000-0xfffff could not be reserved
[    1.180738] system 00:0b: iomem range 0x100000-0xfefffff could not be reserved
[    1.215820] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:01
[    1.215830] pci 0000:00:1e.0:   IO window: 0xd000-0xdfff
[    1.215843] pci 0000:00:1e.0:   MEM window: 0xff800000-0xff8fffff
[    1.215853] pci 0000:00:1e.0:   PREFETCH window: 0x000000f6a00000-0x000000f6afffff
[    1.215884] pci 0000:00:1e.0: setting latency timer to 64
[    1.215895] bus: 00 index 0 io port: [0x00-0xffff]
[    1.215902] bus: 00 index 1 mmio: [0x000000-0xffffffff]
[    1.215909] bus: 01 index 0 io port: [0xd000-0xdfff]
[    1.215916] bus: 01 index 1 mmio: [0xff800000-0xff8fffff]
[    1.215923] bus: 01 index 2 mmio: [0xf6a00000-0xf6afffff]
[    1.215930] bus: 01 index 3 io port: [0x00-0xffff]
[    1.215936] bus: 01 index 4 mmio: [0x000000-0xffffffff]
[    1.216005] NET: Registered protocol family 2
[    1.216413] IP route cache hash table entries: 2048 (order: 1, 8192 bytes)
[    1.217172] TCP established hash table entries: 8192 (order: 4, 65536 bytes)
[    1.217384] TCP bind hash table entries: 8192 (order: 4, 65536 bytes)
[    1.217597] TCP: Hash tables configured (established 8192 bind 8192)
[    1.217605] TCP reno registered
[    1.217946] NET: Registered protocol family 1
[    1.218347] checking if image is initramfs...<7>Switched to high resolution mode on CPU 0
[    2.026387]  it is
[    3.057298] Freeing initrd memory: 7718k freed
[    3.057496] cpufreq: No nForce2 chipset.
[    3.057906] audit: initializing netlink socket (disabled)
[    3.057968] type=2000 audit(1251519088.056:1): initialized
[    3.079959] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    3.084403] VFS: Disk quotas dquot_6.5.1
[    3.084617] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    3.086769] fuse init (API version 7.10)
[    3.087044] msgmni has been set to 486
[    3.087700] alg: No test for stdrng (krng)
[    3.087744] io scheduler noop registered
[    3.087751] io scheduler anticipatory registered
[    3.087757] io scheduler deadline registered
[    3.087838] io scheduler cfq registered (default)
[    3.087893] pci 0000:00:01.0: Boot video device
[    3.093033] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    3.093060] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    3.093418] input: Power Button (FF) as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input0
[    3.093429] ACPI: Power Button (FF) [PWRF]
[    3.093809] processor ACPI_CPU:00: registered as cooling_device0
[    3.097261] isapnp: Scanning for PnP cards...
[    3.451092] isapnp: No Plug & Play device found
[    3.454711] Serial: 8250/16550 driver4 ports, IRQ sharing enabled
[    3.454859] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    3.455732] 00:08: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    3.458018] brd: module loaded
[    3.459017] loop: module loaded
[    3.459296] Fixed MDIO Bus: probed
[    3.459317] PPP generic driver version 2.4.2
[    3.459519] input: Macintosh mouse button emulation as /devices/virtual/input/input1
[    3.459639] Driver 'sd' needs updating - please use bus_type methods
[    3.459668] Driver 'sr' needs updating - please use bus_type methods
[    3.459889] ata_piix 0000:00:1f.1: version 2.12
[    3.460154] ata_piix 0000:00:1f.1: setting latency timer to 64
[    3.460478] scsi0 : ata_piix
[    3.460861] scsi1 : ata_piix
[    3.463699] ata1: PATA max UDMA/66 cmd 0x1f0 ctl 0x3f6 bmdma 0xffa0 irq 14
[    3.463712] ata2: PATA max UDMA/66 cmd 0x170 ctl 0x376 bmdma 0xffa8 irq 15
[    3.624602] ata1.00: ATA-6: Maxtor 32049H2, YAH814Y0, max UDMA/100
[    3.624611] ata1.00: 39062500 sectors, multi 16: LBA 
[    3.640555] ata1.00: configured for UDMA/66
[    3.796490] ata2.00: ATAPI: Lite-On LTN483S 48x Max, PD02, max UDMA/33, CDB intr
[    3.804468] ata2.00: configured for UDMA/33
[    3.805032] scsi 0:0:0:0: Direct-Access     ATA      Maxtor 32049H2   YAH8 PQ: 0 ANSI: 5
[    3.805352] sd 0:0:0:0: [sda] 39062500 512-byte hardware sectors: (20.0 GB/18.6 GiB)
[    3.805409] sd 0:0:0:0: [sda] Write Protect is off
[    3.805417] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    3.805506] sd 0:0:0:0: [sda] Write cache: disabled, read cache: enabled, doesn't support DPO or FUA
[    3.805715] sd 0:0:0:0: [sda] 39062500 512-byte hardware sectors: (20.0 GB/18.6 GiB)
[    3.805764] sd 0:0:0:0: [sda] Write Protect is off
[    3.805772] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    3.805858] sd 0:0:0:0: [sda] Write cache: disabled, read cache: enabled, doesn't support DPO or FUA
[    3.805874]  sda: sda1 sda2 < sda5 >
[    3.873558] sd 0:0:0:0: [sda] Attached SCSI disk
[    3.873725] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    3.874436] scsi 1:0:0:0: CD-ROM            Lite-On  LTN483S 48x Max  PD02 PQ: 0 ANSI: 5
[    3.877215] sr0: scsi3-mmc drive: 48x/48x cd/rw xa/form2 cdda tray
[    3.877225] Uniform CD-ROM driver Revision: 3.20
[    3.877588] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    3.877732] sr 1:0:0:0: Attached scsi generic sg1 type 5
[    3.879506] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    3.879562] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    3.879607] uhci_hcd: USB Universal Host Controller Interface driver
[    3.880287] ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 9
[    3.880297] PCI: setting IRQ 9 as level-triggered
[    3.880307] uhci_hcd 0000:00:1f.2: PCI INT D -> Link[LNKD] -> GSI 9 (level, low) -> IRQ 9
[    3.880331] uhci_hcd 0000:00:1f.2: setting latency timer to 64
[    3.880339] uhci_hcd 0000:00:1f.2: UHCI Host Controller
[    3.880546] uhci_hcd 0000:00:1f.2: new USB bus registered, assigned bus number 1
[    3.880592] uhci_hcd 0000:00:1f.2: irq 9, io base 0x0000ef80
[    3.880905] usb usb1: configuration #1 chosen from 1 choice
[    3.880993] hub 1-0:1.0: USB hub found
[    3.881023] hub 1-0:1.0: 2 ports detected
[    3.881504] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f03:PS2M] at 0x60,0x64 irq 1,12
[    3.884495] serio: i8042 KBD port at 0x60,0x64 irq 1
[    3.884515] serio: i8042 AUX port at 0x60,0x64 irq 12
[    3.884858] mice: PS/2 mouse device common for all mice
[    3.885159] rtc_cmos 00:02: RTC can wake from S4
[    3.885268] rtc_cmos 00:02: rtc core: registered rtc_cmos as rtc0
[    3.885302] rtc0: alarms up to one month, 114 bytes nvram
[    3.885581] device-mapper: uevent: version 1.0.3
[    3.885969] device-mapper: ioctl: 4.14.0-ioctl (2008-04-23) initialised: dm-devel@redhat.com
[    3.886152] device-mapper: multipath: version 1.0.5 loaded
[    3.886162] device-mapper: multipath round-robin: version 1.0.0 loaded
[    3.886470] EISA: Probing bus 0 at eisa.0
[    3.886529] EISA: Detected 0 cards.
[    3.886620] cpuidle: using governor ladder
[    3.886626] cpuidle: using governor menu
[    3.888402] TCP cubic registered
[    3.888764] NET: Registered protocol family 10
[    3.890111] lo: Disabled Privacy Extensions
[    3.891160] NET: Registered protocol family 17
[    3.891222] Bluetooth: L2CAP ver 2.11
[    3.891228] Bluetooth: L2CAP socket layer initialized
[    3.891236] Bluetooth: SCO (Voice Link) ver 0.6
[    3.891242] Bluetooth: SCO socket layer initialized
[    3.891395] Bluetooth: RFCOMM socket layer initialized
[    3.891424] Bluetooth: RFCOMM TTY layer initialized
[    3.891430] Bluetooth: RFCOMM ver 1.10
[    3.891589] IO APIC resources could be not be allocated.
[    3.891652] Using IPI No-Shortcut mode
[    3.891979] registered taskstats version 1
[    3.892299]   Magic number: 5:230:162
[    3.892475] rtc_cmos 00:02: setting system clock to 2009-08-29 04:11:29 UTC (1251519089)
[    3.892488] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    3.892493] EDD information not available.
[    3.895020] Freeing unused kernel memory: 532k freed
[    3.895425] Write protecting the kernel text: 4116k
[    3.895539] Write protecting the kernel read-only data: 1528k
[    3.936380] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input2
[    4.194883] usb 1-1: new full speed USB device using uhci_hcd and address 2
[    4.396308] usb 1-1: configuration #1 chosen from 1 choice
[    4.874452] Floppy drive(s): fd0 is 1.44M
[    4.891894] FDC 0 is a post-1991 82077
[    4.997177] Linux Tulip driver version 1.1.15 (Feb 27, 2007)
[    4.997303] tulip 0000:01:0b.0: PCI INT A -> Link[LNKD] -> GSI 9 (level, low) -> IRQ 9
[    4.997861] tulip0:  MII transceiver #1 config 3100 status 7849 advertising 05e1.
[    5.018243] eth0: ADMtek Comet rev 17 at Port 0xd800, 00:e0:50:d4:fc:0c, IRQ 9.
[    5.193926] Initializing USB Mass Storage driver...
[    5.196366] scsi2 : SCSI emulation for USB Mass Storage devices
[    5.199898] usbcore: registered new interface driver usb-storage
[    5.199916] USB Mass Storage support registered.
[    5.200780] usb-storage: device found at 2
[    5.200789] usb-storage: waiting for device to settle before scanning
[    6.394002] PM: Starting manual resume from disk
[    6.394020] PM: Resume from partition 8:5
[    6.394025] PM: Checking hibernation image.
[    6.394468] PM: Resume from disk failed.
[    6.402268] EXT3-fs: INFO: recovery required on readonly filesystem.
[    6.402286] EXT3-fs: write access will be enabled during recovery.
[    8.107403] kjournald starting.  Commit interval 5 seconds
[    8.107472] EXT3-fs: sda1: orphan cleanup on readonly fs
[    8.107492] ext3_orphan_cleanup: deleting unreferenced inode 491625
[    8.107591] ext3_orphan_cleanup: deleting unreferenced inode 491624
[    8.107661] ext3_orphan_cleanup: deleting unreferenced inode 491267
[    8.107694] ext3_orphan_cleanup: deleting unreferenced inode 40900
[    8.107805] EXT3-fs: sda1: 4 orphan inodes deleted
[    8.107812] EXT3-fs: recovery complete.
[    8.313355] EXT3-fs: mounted filesystem with ordered data mode.
[   10.202304] usb-storage: device scan complete
[   10.238544] scsi 2:0:0:0: CD-ROM            HP       DVD Writer 940d  3H23 PQ: 0 ANSI: 0
[   10.261159] sr1: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
[   10.261557] sr 2:0:0:0: Attached scsi CD-ROM sr1
[   10.261783] sr 2:0:0:0: Attached scsi generic sg2 type 5
[   16.998810] udev: starting version 141
[   17.321954] Linux agpgart interface v0.103
[   17.495259] agpgart-intel 0000:00:00.0: Intel i810 Chipset
[   17.501954] pci 0000:00:01.0: detected 4MB dedicated video ram
[   17.507754] intel_rng: Firmware space is locked read-only. If you can't or
[   17.507762] intel_rng: don't want to disable this in firmware setup, and if
[   17.507766] intel_rng: you are certain that your system has a functional
[   17.507770] intel_rng: RNG, try using the 'no_fwh_detect' option.
[   17.515942] agpgart-intel 0000:00:00.0: AGP aperture is 64M @ 0xf8000000
[   17.540489] parport_pc 00:09: reported by Plug and Play ACPI
[   17.540556] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
[   17.574529] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   17.816240] iTCO_vendor_support: vendor-support=0
[   17.930866] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.05
[   17.931173] iTCO_wdt: failed to reset NO_REBOOT flag, reboot disabled by hardware
[   17.931197] iTCO_wdt: No card detected
[   18.279124] input: PC Speaker as /devices/platform/pcspkr/input/input3
[   18.384376] cfg80211: Calling CRDA to update world regulatory domain
[   18.595495] synaptics was reset on resume, see synaptics_resume_reset if you have trouble on resume
[   19.112677] psmouse serio1: ID: 10 00 64<6>input: ImPS/2 Generic Wheel Mouse as /devices/platform/i8042/serio1/input/input4
[   23.760199] cfg80211: World regulatory domain updated:
[   23.760218]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   23.760228]     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   23.760235]     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   23.760243]     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   23.760251]     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   23.760258]     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   24.009801] dcdbas dcdbas: Dell Systems Management Base Driver (version 5.6.0-3.2)
[   24.080859] ppdev: user-space parallel port driver
[   24.477896] ACPI: PCI Interrupt Link [LNKC] enabled at IRQ 3
[   24.477910] PCI: setting IRQ 3 as level-triggered
[   24.477921] rt61pci 0000:01:0a.0: PCI INT A -> Link[LNKC] -> GSI 3 (level, low) -> IRQ 3
[   24.491235] phy0: Selected rate control algorithm 'pid'
[   24.743790] Registered led device: rt61pci-phy0:radio
[   24.743911] Registered led device: rt61pci-phy0:assoc
[   24.945428] ACPI: PCI Interrupt Link [LNKB] enabled at IRQ 10
[   24.945442] PCI: setting IRQ 10 as level-triggered
[   24.945453] ENS1371 0000:01:09.0: PCI INT A -> Link[LNKB] -> GSI 10 (level, low) -> IRQ 10
[   26.252663] lp0: using parport0 (interrupt-driven).
[   26.554779] Adding 722884k swap on /dev/sda5.  Priority:-1 extents:1 across:722884k
[   27.201063] EXT3 FS on sda1, internal journal
[   29.416581] type=1505 audit(1251519115.023:2): operation="profile_load" name="/sbin/dhclient-script" name2="default" pid=1872
[   29.417757] type=1505 audit(1251519115.023:3): operation="profile_load" name="/sbin/dhclient3" name2="default" pid=1872
[   29.418148] type=1505 audit(1251519115.023:4): operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" name2="default" pid=1872
[   29.418372] type=1505 audit(1251519115.023:5): operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" name2="default" pid=1872
[   29.956256] type=1505 audit(1251519115.563:6): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=1877
[   29.957563] type=1505 audit(1251519115.563:7): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=1877
[   30.075312] type=1505 audit(1251519115.679:8): operation="profile_load" name="/usr/sbin/tcpdump" name2="default" pid=1881
[   37.033670] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   37.033680] Bluetooth: BNEP filters: protocol multicast
[   37.117227] Bridge firewalling registered
[   40.215082] [drm] Initialized drm 1.1.0 20060810
[   40.225635] ACPI: PCI Interrupt Link [LNKA] enabled at IRQ 11
[   40.225648] PCI: setting IRQ 11 as level-triggered
[   40.225660] pci 0000:00:01.0: PCI INT A -> Link[LNKA] -> GSI 11 (level, low) -> IRQ 11
[   40.225672] pci 0000:00:01.0: setting latency timer to 64
[   40.226270] [drm] Initialized i810 1.4.0 20030605 on minor 0
[   40.393106] mtrr: base(0xf8000000) is not aligned on a size(0x180000) boundary
[   40.633885] [drm] Using v1.4 init.
[   42.397674] rt61pci 0000:01:0a.0: firmware: requesting rt2561s.bin
[   42.621516] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   43.972033] [drm:drm_release] *ERROR* reclaim_buffers_locked() deadlock. Please rework this
[   43.972043]     driver to use reclaim_buffers_idlelocked() instead.
[   43.972047]     I will go on reclaiming the buffers anyway.
[   44.132127] wlan0: authenticate with AP 00:24:37:0c:ab:60
[   44.133490] wlan0: authenticated
[   44.133500] wlan0: associate with AP 00:24:37:0c:ab:60
[   44.135942] wlan0: RX AssocResp from 00:24:37:0c:ab:60 (capab=0x441 status=0 aid=2)
[   44.135951] wlan0: associated
[   44.138781] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   44.300421] wlan0: disassociating by local choice (reason=3)
[   53.068038] eth0: no IPv6 routers present
[   54.712052] wlan0: no IPv6 routers present
[  153.440196] wlan0: authenticate with AP 00:24:37:32:1d:80
[  153.441544] wlan0: authenticated
[  153.441562] wlan0: associate with AP 00:24:37:32:1d:80
[  153.444352] wlan0: RX AssocResp from 00:24:37:32:1d:80 (capab=0x451 status=0 aid=3)
[  153.444366] wlan0: associated
[  159.094149] padlock: VIA PadLock not detected.
[ 1898.208574] psmouse.c: Wheel Mouse at isa0060/serio1/input0 lost synchronization, throwing 2 bytes away.
kisuke@kisuke-desktop:~$ 

``` am going to try (how many PCs have ps/2 ports any more?) to test mouse in another PC tonight will report if it works there.

---

### Post by P4man on 2009-08-29
Its not your mouse. Look at the last line. I google on that and found this:

[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/119194](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/119194)

A suggested workaround is adding "acpi_osi=Linux" to the kernel parameters.

you can do that by editing your grub menu 

```
gksudo gedit /boot/grub/menu.lst
```

find your most recent kernel. it will look like

kernel		/boot/vmlinuz-2.6.28-15-generic root=UUID=0e5317cf-1aa2-4b20-9ffa-f17c41f48f37 ro quiet splash 

Change it to

kernel		/boot/vmlinuz-2.6.28-15-generic root=UUID=0e5317cf-1aa2-4b20-9ffa-f17c41f48f37 ro quiet splash **acpi_osi=Linux**

reboot, let me know :)

---

