---
title: "slow and sticky USB mouse"
date: 2009-08-10
forum: General Help
---

### Post by darkdesire on 2009-08-10
I have Ubuntu 9.04 (Jaunty Jackalope) and all updates are done. I also have medibuntu installed. 

Since a couple of weeks the mouse has changed behaviour and is annoying. The Logitech USB mouse is slow to respond and is sticky. I changed to a HP USB mouse but there is no change. 

Something must have changed since sine the updates and /or since I installed media software.

I beleive ubuntu uses HAL for mouse confiuration but I done see how to check this

Any ideas? :confused:

---

### Post by callumacrae on 2009-08-10
My USB mouse works fine, and it didn't need anything installing. Have you tried them on another computer?

~Callum

---

### Post by P4man on 2009-08-10
can you elaborate a bit? what do you mean its "sticky"?

Since 2 mice exhibit this problem, is it possible it has nothing to do with your mouse as such, but the system is unresponsive as a whole? if you open system > administration > system monitor, make sure you don't have some app or process hogging 100% of your cpu ?

---

### Post by darkdesire on 2009-08-10
Hi

Thanks for your replies

The CPU monitor shows no real activity and there are no processes taking up the resources. The computer is clean and I see this behaviour soon after reboot.

By Sticky I mean that the mouse responds a little after the mouse is moved. It eventually catches up but the effect is not user friendly

---

### Post by P4man on 2009-08-10
Then im guessing its apic issue. When you boot, go in to the grub menu, select your kernel and press "e". Select the kernel line and add one of these set of switches to the kernel parameters:

```
noapic nolapic

noapic acpi=noirq

noapic acpi=off

noapictimer

noapictimer irqpoll

noapic acpi=noirq nolapic
```

So for instance:

```
kernel	/boot/vmlinuz-2.6.28-14-generic root=UUID=0e5317cf-1aa2-4b20-9ffa-f17c41f48f37 ro quiet splash noapic acpi=noirq

```

To boot the kernel after making the changes, press B in grub

Try them one by one (I mean one line) until hopefully the problem dissapears. Then report back.

edit: also attach the output of dmesg here if possible

---

### Post by P4man on 2009-08-10
A friend of mine had something that reminded me of your issue. When his computer was idle and he didn't move his mouse for a few seconds, then moved it (or scrolled), there would be a small, but noticeable delay before the system reacted. Something like half a second or even less. Just enough to be mildly annoying As if the mouse went in sleep mode (which it didnt, it was a std wired, usb mouse). His system also locked up regularly and has a known buggy ACPI BIOS implementation.

What solved it for him, was going in the bios and in powermanagement disable "C2". Im sure that will cost a bit of electricity/heat, but the issues went away. I have yet to eat my own medicine and try the above boot options with C2 enabled, but I thought I'd share it already.

---

### Post by darkdesire on 2009-08-10
The option **noapictime irqpol**l gave successfull results. Some of the others froze the system.

Many thanks for this. What does it do exactly?

The result of dmesg is

dmesg
[    0.000000] BIOS EBDA/lowmem at: 0009fc00/0009fc00
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.28-14-generic (buildd@palmer) (gcc version 4.3.3 (Ubuntu 4.3.3-5ubuntu4) ) #47-Ubuntu SMP Sat Jul 25 00:28:35 UTC 2009 (Ubuntu 2.6.28-14.47-generic)
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
[    0.000000]  BIOS-e820: 0000000000100000 - 000000000fff0000 (usable)
[    0.000000]  BIOS-e820: 000000000fff0000 - 000000000fff8000 (ACPI data)
[    0.000000]  BIOS-e820: 000000000fff8000 - 0000000010000000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000fff80000 - 0000000100000000 (reserved)
[    0.000000] DMI 2.3 present.
[    0.000000] AMI BIOS detected: BIOS may corrupt low RAM, working it around.
[    0.000000] last_pfn = 0xfff0 max_arch_pfn = 0x100000
[    0.000000] Scanning 0 areas for low memory corruption
[    0.000000] modified physical RAM map:
[    0.000000]  modified: 0000000000000000 - 0000000000010000 (reserved)
[    0.000000]  modified: 0000000000010000 - 000000000009fc00 (usable)
[    0.000000]  modified: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  modified: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  modified: 0000000000100000 - 000000000fff0000 (usable)
[    0.000000]  modified: 000000000fff0000 - 000000000fff8000 (ACPI data)
[    0.000000]  modified: 000000000fff8000 - 0000000010000000 (ACPI NVS)
[    0.000000]  modified: 00000000fff80000 - 0000000100000000 (reserved)
[    0.000000] kernel direct mapping tables up to fff0000 @ 10000-16000
[    0.000000] RAMDISK: 0f8af000 - 0ffdf512
[    0.000000] ACPI: RSDP 000FC990, 0014 (r0 AMI   )
[    0.000000] ACPI: RSDT 0FFF0000, 0028 (r1 AMIINT VIA_K7         11 MSFT       97)
[    0.000000] ACPI: FACP 0FFF0030, 0074 (r1 AMIINT VIA_K7         11 MSFT       97)
[    0.000000] ACPI: DSDT 0FFF00B0, 2954 (r1    VIA   VIA_K7     1000 MSFT  100000D)
[    0.000000] ACPI: FACS 0FFF8000, 0040
[    0.000000] 0MB HIGHMEM available.
[    0.000000] 255MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 0fff0000
[    0.000000]   low ram: 00000000 - 0fff0000
[    0.000000]   bootmap 00012000 - 00014000
[    0.000000] (9 early reservations) ==> bootmem [0000000000 - 000fff0000]
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
[    0.000000]   #1 [0000001000 - 0000002000]    EX TRAMPOLINE ==> [0000001000 - 0000002000]
[    0.000000]   #2 [0000006000 - 0000007000]       TRAMPOLINE ==> [0000006000 - 0000007000]
[    0.000000]   #3 [0000100000 - 00008760ac]    TEXT DATA BSS ==> [0000100000 - 00008760ac]
[    0.000000]   #4 [000f8af000 - 000ffdf512]          RAMDISK ==> [000f8af000 - 000ffdf512]
[    0.000000]   #5 [0000877000 - 000087b000]    INIT_PG_TABLE ==> [0000877000 - 000087b000]
[    0.000000]   #6 [000009fc00 - 0000100000]    BIOS reserved ==> [000009fc00 - 0000100000]
[    0.000000]   #7 [0000010000 - 0000012000]          PGTABLE ==> [0000010000 - 0000012000]
[    0.000000]   #8 [0000012000 - 0000014000]          BOOTMAP ==> [0000012000 - 0000014000]
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000010 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x0000fff0
[    0.000000]   HighMem  0x0000fff0 -> 0x0000fff0
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[2] active PFN ranges
[    0.000000]     0: 0x00000010 -> 0x0000009f
[    0.000000]     0: 0x00000100 -> 0x0000fff0
[    0.000000] On node 0 totalpages: 65407
[    0.000000] free_area_init_node: node 0, pgdat c06ca500, node_mem_map c1000200
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3951 pages, LIFO batch:0
[    0.000000]   Normal zone: 480 pages used for memmap
[    0.000000]   Normal zone: 60944 pages, LIFO batch:15
[    0.000000]   HighMem zone: 0 pages used for memmap
[    0.000000]   Movable zone: 0 pages used for memmap
[    0.000000] ACPI: PM-Timer IO Port: 0x808
[    0.000000] SMP: Allowing 1 CPUs, 0 hotplug CPUs
[    0.000000] Local APIC disabled by BIOS -- you can enable it with "lapic"
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
[    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 20000000 (gap: 10000000:eff80000)
[    0.000000] PERCPU: Allocating 45056 bytes of per cpu data
[    0.000000] NR_CPUS: 64, nr_cpu_ids: 1, nr_node_ids 1
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 64895
[    0.000000] Kernel command line: root=UUID=86348300-123d-4c12-80e4-1e914797ba80 ro quiet splash noapictimer irqpoll 
[    0.000000] Misrouted IRQ fixup and polling support enabled
[    0.000000] This may significantly impact system performance
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 1024 (order: 10, 4096 bytes)
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 1400.061 MHz processor.
[    0.004000] Console: colour VGA+ 80x25
[    0.004000] console [tty0] enabled
[    0.004000] Dentry cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.004000] Inode-cache hash table entries: 16384 (order: 4, 65536 bytes)
[    0.004000] allocated 1310080 bytes of page_cgroup
[    0.004000] please try cgroup_disable=memory option if you don't want
[    0.004000] Scanning for low memory corruption every 60 seconds
[    0.004000] Memory: 242740k/262080k available (4115k kernel code, 18640k reserved, 2196k data, 532k init, 0k highmem)
[    0.004000] virtual kernel memory layout:
[    0.004000]     fixmap  : 0xffc77000 - 0xfffff000   (3616 kB)
[    0.004000]     pkmap   : 0xff400000 - 0xff800000   (4096 kB)
[    0.004000]     vmalloc : 0xd07f0000 - 0xff3fe000   ( 748 MB)
[    0.004000]     lowmem  : 0xc0000000 - 0xcfff0000   ( 255 MB)
[    0.004000]       .init : 0xc0731000 - 0xc07b6000   ( 532 kB)
[    0.004000]       .data : 0xc0504def - 0xc0729e60   (2196 kB)
[    0.004000]       .text : 0xc0100000 - 0xc0504def   (4115 kB)
[    0.004000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.004000] SLUB: Genslabs=12, HWalign=32, Order=0-3, MinObjects=0, CPUs=1, Nodes=1
[    0.004658] Calibrating delay loop (skipped), value calculated using timer frequency.. 2800.12 BogoMIPS (lpj=5600244)
[    0.004707] Security Framework initialized
[    0.004723] SELinux:  Disabled at boot.
[    0.004777] AppArmor: AppArmor initialized
[    0.004794] Mount-cache hash table entries: 512
[    0.005092] Initializing cgroup subsys ns
[    0.005100] Initializing cgroup subsys cpuacct
[    0.005104] Initializing cgroup subsys memory
[    0.005113] Initializing cgroup subsys freezer
[    0.005136] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[    0.005141] CPU: L2 Cache: 256K (64 bytes/line)
[    0.005172] Checking 'hlt' instruction... OK.
[    0.020990] SMP alternatives: switching to UP code
[    0.293634] Freeing SMP alternatives: 18k freed
[    0.293642] ACPI: Core revision 20080926
[    0.295671] ACPI: Checking initramfs for custom DSDT
[    0.799049] ACPI: setting ELCR to 0200 (from 1c00)
[    0.799494] weird, boot CPU (#0) not listedby the BIOS.
[    0.799499] SMP motherboard not detected.
[    0.799504] Local APIC not detected. Using dummy APIC emulation.
[    0.799507] SMP disabled
[    0.800853] Brought up 1 CPUs
[    0.800859] Total of 1 processors activated (2800.12 BogoMIPS).
[    0.800892] CPU0 attaching NULL sched-domain.
[    0.801675] net_namespace: 776 bytes
[    0.801700] Booting paravirtualized kernel on bare hardware
[    0.802094] Time: 17:35:05  Date: 08/10/09
[    0.802105] regulator: core version 0.5
[    0.802188] NET: Registered protocol family 16
[    0.802424] EISA bus registered
[    0.802453] ACPI: bus type pci registered
[    0.835692] PCI: PCI BIOS revision 2.10 entry at 0xfdb31, last bus=1
[    0.835697] PCI: Using configuration type 1 for base access
[    0.838599] ACPI: EC: Look up EC in DSDT
[    0.845614] ACPI: Interpreter enabled
[    0.845630] ACPI: (supports S0 S1 S4 S5)
[    0.845663] ACPI: Using PIC for interrupt routing
[    0.850296] ACPI: No dock devices found.
[    0.850317] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.850395] pci 0000:00:00.0: reg 10 32bit mmio: [0xe0000000-0xe3ffffff]
[    0.850458] pci 0000:00:01.0: supports D1
[    0.850553] pci 0000:00:07.1: reg 20 io port: [0xff00-0xff0f]
[    0.850606] pci 0000:00:07.2: reg 20 io port: [0xd400-0xd41f]
[    0.850657] pci 0000:00:07.3: reg 20 io port: [0xd800-0xd81f]
[    0.850731] pci 0000:00:07.4: quirk: region 0c00-0c7f claimed by vt82c686 HW-mon
[    0.850736] pci 0000:00:07.4: quirk: region 0400-040f claimed by vt82c686 SMB
[    0.850764] pci 0000:00:0a.0: reg 10 32bit mmio: [0xdd9ff000-0xdd9fffff]
[    0.850771] pci 0000:00:0a.0: reg 14 io port: [0xd000-0xd01f]
[    0.850778] pci 0000:00:0a.0: reg 18 32bit mmio: [0xdff00000-0xdfffffff]
[    0.850794] pci 0000:00:0a.0: reg 30 32bit mmio: [0xdfe00000-0xdfefffff]
[    0.850825] pci 0000:00:0e.0: reg 10 io port: [0xcc00-0xcc3f]
[    0.850854] pci 0000:00:0e.0: supports D2
[    0.850879] pci 0000:00:0f.0: reg 10 io port: [0xc800-0xc80f]
[    0.850907] pci 0000:00:0f.0: PME# supported from D0 D3hot D3cold
[    0.850912] pci 0000:00:0f.0: PME# disabled
[    0.850963] pci 0000:01:00.0: reg 10 32bit mmio: [0xde000000-0xdeffffff]
[    0.850970] pci 0000:01:00.0: reg 14 32bit mmio: [0xda000000-0xdbffffff]
[    0.850988] pci 0000:01:00.0: reg 30 32bit mmio: [0xdfaf0000-0xdfafffff]
[    0.851027] pci 0000:00:01.0: bridge io port: [0xa000-0xafff]
[    0.851033] pci 0000:00:01.0: bridge 32bit mmio: [0xdda00000-0xdfafffff]
[    0.851038] pci 0000:00:01.0: bridge 32bit mmio pref: [0xd9800000-0xdd8fffff]
[    0.851046] bus 00 -> node 0
[    0.851058] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.853168] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 10 *11 12 14 15)
[    0.853328] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[    0.853479] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 *10 11 12 14 15)
[    0.853627] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 10 11 *12 14 15)
[    0.853742] ACPI: Power Resource [URP1] (off)
[    0.853790] ACPI: Power Resource [URP2] (off)
[    0.853836] ACPI: Power Resource [FDDP] (off)
[    0.853896] ACPI: Power Resource [LPTP] (off)
[    0.854003] ACPI: WMI: Mapper loaded
[    0.854469] SCSI subsystem initialized
[    0.854561] libata version 3.00 loaded.
[    0.854670] usbcore: registered new interface driver usbfs
[    0.854701] usbcore: registered new interface driver hub
[    0.854756] usbcore: registered new device driver usb
[    0.854965] PCI: Using ACPI for IRQ routing
[    0.855095] Bluetooth: Core ver 2.13
[    0.855095] NET: Registered protocol family 31
[    0.855095] Bluetooth: HCI device and connection manager initialized
[    0.855095] Bluetooth: HCI socket layer initialized
[    0.855095] NET: Registered protocol family 8
[    0.855095] NET: Registered protocol family 20
[    0.855095] NetLabel: Initializing
[    0.855095] NetLabel:  domain hash size = 128
[    0.855095] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.855095] NetLabel:  unlabeled traffic allowed by default
[    0.855095] AppArmor: AppArmor Filesystem Enabled
[    0.855095] pnp: PnP ACPI init
[    0.855095] ACPI: bus type pnp registered
[    0.858948] pnp: PnP ACPI: found 9 devices
[    0.858954] ACPI: ACPI bus type pnp unregistered
[    0.858963] PnPBIOS: Disabled by ACPI PNP
[    0.894208] pci 0000:00:01.0: PCI bridge, secondary bus 0000:01
[    0.894215] pci 0000:00:01.0:   IO window: 0xa000-0xafff
[    0.894222] pci 0000:00:01.0:   MEM window: 0xdda00000-0xdfafffff
[    0.894227] pci 0000:00:01.0:   PREFETCH window: 0x000000d9800000-0x000000dd8fffff
[    0.894248] pci 0000:00:01.0: setting latency timer to 64
[    0.894254] bus: 00 index 0 io port: [0x00-0xffff]
[    0.894257] bus: 00 index 1 mmio: [0x000000-0xffffffff]
[    0.894260] bus: 01 index 0 io port: [0xa000-0xafff]
[    0.894264] bus: 01 index 1 mmio: [0xdda00000-0xdfafffff]
[    0.894267] bus: 01 index 2 mmio: [0xd9800000-0xdd8fffff]
[    0.894270] bus: 01 index 3 mmio: [0x0-0x0]
[    0.894320] NET: Registered protocol family 2
[    0.894585] IP route cache hash table entries: 2048 (order: 1, 8192 bytes)
[    0.895032] TCP established hash table entries: 8192 (order: 4, 65536 bytes)
[    0.895217] TCP bind hash table entries: 8192 (order: 4, 65536 bytes)
[    0.895388] TCP: Hash tables configured (established 8192 bind 8192)
[    0.895392] TCP reno registered
[    0.895517] NET: Registered protocol family 1
[    0.895780] checking if image is initramfs... it is
[    1.396687] Switched to high resolution mode on CPU 0
[    2.036818] Freeing initrd memory: 7361k freed
[    2.037017] cpufreq: No nForce2 chipset.
[    2.037269] audit: initializing netlink socket (disabled)
[    2.037312] type=2000 audit(1249925706.036:1): initialized
[    2.050451] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    2.053225] VFS: Disk quotas dquot_6.5.1
[    2.053331] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    2.054341] fuse init (API version 7.10)
[    2.054473] msgmni has been set to 489
[    2.054841] alg: No test for stdrng (krng)
[    2.054866] io scheduler noop registered
[    2.054869] io scheduler anticipatory registered
[    2.054873] io scheduler deadline registered
[    2.054897] io scheduler cfq registered (default)
[    2.054932] pci 0000:00:00.0: Applying VIA southbridge workaround
[    2.054938] PCI: VIA PCI bridge detected.Disabling DAC.
[    2.054945] pci 0000:00:07.0: Disabling VIA external APIC routing
[    2.055017] pci 0000:00:0a.0: Firmware left e100 interrupts enabled; disabling
[    2.055044] pci 0000:01:00.0: Boot video device
[    2.058411] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    2.058427] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    2.058678] input: Power Button (FF) as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input0
[    2.058683] ACPI: Power Button (FF) [PWRF]
[    2.058753] input: Power Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1
[    2.058757] ACPI: Power Button (CM) [PWRB]
[    2.058855] input: Sleep Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input2
[    2.058859] ACPI: Sleep Button (CM) [SLPB]
[    2.059084] processor ACPI_CPU:00: registered as cooling_device0
[    2.059090] ACPI: Processor [CPU1] (supports 16 throttling states)
[    2.061528] isapnp: Scanning for PnP cards...
[    2.416961] isapnp: No Plug & Play device found
[    2.419282] Serial: 8250/16550 driver4 ports, IRQ sharing enabled
[    2.419425] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    2.419874] 00:07: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    2.420999] ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 12
[    2.421009] PCI: setting IRQ 12 as level-triggered
[    2.421019] serial 0000:00:0f.0: PCI INT A -> Link[LNKD] -> GSI 12 (level, low) -> IRQ 12
[    2.422439] brd: module loaded
[    2.422967] loop: module loaded
[    2.423114] Fixed MDIO Bus: probed
[    2.423125] PPP generic driver version 2.4.2
[    2.423250] input: Macintosh mouse button emulation as /devices/virtual/input/input3
[    2.423313] Driver 'sd' needs updating - please use bus_type methods
[    2.423329] Driver 'sr' needs updating - please use bus_type methods
[    2.424840] pata_via 0000:00:07.1: version 0.3.3
[    2.426091] scsi0 : pata_via
[    2.426353] scsi1 : pata_via
[    2.428951] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xff00 irq 14
[    2.428958] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xff08 irq 15
[    2.592813] ata1.00: ATA-6: Maxtor 4D040H2, DAH017K0, max UDMA/100
[    2.592818] ata1.00: 80043264 sectors, multi 16: LBA 
[    2.600867] ata1.00: configured for UDMA/100
[    2.756586] ata2.01: NODEV after polling detection
[    2.764562] ata2.00: ATAPI: SAMSUNG  CD-R/RW SW-216B  Q001 20010913, Q001, max MWDMA2
[    2.780574] ata2.00: configured for MWDMA2
[    2.781158] scsi 0:0:0:0: Direct-Access     ATA      Maxtor 4D040H2   DAH0 PQ: 0 ANSI: 5
[    2.781382] sd 0:0:0:0: [sda] 80043264 512-byte hardware sectors: (40.9 GB/38.1 GiB)
[    2.781417] sd 0:0:0:0: [sda] Write Protect is off
[    2.781422] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    2.781469] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.781626] sd 0:0:0:0: [sda] 80043264 512-byte hardware sectors: (40.9 GB/38.1 GiB)
[    2.781652] sd 0:0:0:0: [sda] Write Protect is off
[    2.781656] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    2.781698] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.781705]  sda: sda1 sda2 < sda5 >
[    2.845659] sd 0:0:0:0: [sda] Attached SCSI disk
[    2.845789] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    2.847711] scsi 1:0:0:0: CD-ROM            SAMSUNG  CD-R/RW SW-216B  Q001 PQ: 0 ANSI: 5
[    2.851706] sr0: scsi3-mmc drive: 32x/32x writer cd/rw xa/form2 cdda tray
[    2.851716] Uniform CD-ROM driver Revision: 3.20
[    2.851986] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    2.852734] sr 1:0:0:0: Attached scsi generic sg1 type 5
[    2.853037] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    2.853069] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    2.853089] uhci_hcd: USB Universal Host Controller Interface driver
[    2.853193] uhci_hcd 0000:00:07.2: PCI INT D -> Link[LNKD] -> GSI 12 (level, low) -> IRQ 12
[    2.853214] uhci_hcd 0000:00:07.2: UHCI Host Controller
[    2.853343] uhci_hcd 0000:00:07.2: new USB bus registered, assigned bus number 1
[    2.854003] uhci_hcd 0000:00:07.2: irq 12, io base 0x0000d400
[    2.855998] spurious 8259A interrupt: IRQ15.
[    2.977550] usb usb1: configuration #1 chosen from 1 choice
[    2.977600] hub 1-0:1.0: USB hub found
[    2.977626] hub 1-0:1.0: 2 ports detected
[    2.977816] uhci_hcd 0000:00:07.3: PCI INT D -> Link[LNKD] -> GSI 12 (level, low) -> IRQ 12
[    2.977831] uhci_hcd 0000:00:07.3: UHCI Host Controller
[    2.977915] uhci_hcd 0000:00:07.3: new USB bus registered, assigned bus number 2
[    2.977941] uhci_hcd 0000:00:07.3: irq 12, io base 0x0000d800
[    2.978081] usb usb2: configuration #1 chosen from 1 choice
[    2.978117] hub 2-0:1.0: USB hub found
[    2.978137] hub 2-0:1.0: 2 ports detected
[    2.978337] PNP: PS/2 Controller [PNP0303:PS2K] at 0x60,0x64 irq 1
[    2.978342] PNP: PS/2 appears to have AUX port disabled, if this is incorrect please boot with i8042.nopnp
[    2.978458] serio: i8042 KBD port at 0x60,0x64 irq 1
[    2.978668] mice: PS/2 mouse device common for all mice
[    2.978918] rtc_cmos 00:02: RTC can wake from S4
[    2.978989] rtc_cmos 00:02: rtc core: registered rtc_cmos as rtc0
[    2.979020] rtc0: alarms up to one year, y3k, 114 bytes nvram
[    2.979182] device-mapper: uevent: version 1.0.3
[    2.979401] device-mapper: ioctl: 4.14.0-ioctl (2008-04-23) initialised: [EMAIL="dm-devel@redhat.com"]dm-devel@redhat.com[/EMAIL]
[    2.979505] device-mapper: multipath: version 1.0.5 loaded
[    2.979511] device-mapper: multipath round-robin: version 1.0.0 loaded
[    2.979665] EISA: Probing bus 0 at eisa.0
[    2.979716] EISA: Detected 0 cards.
[    2.979775] cpuidle: using governor ladder
[    2.979779] cpuidle: using governor menu
[    2.981285] TCP cubic registered
[    2.981485] NET: Registered protocol family 10
[    2.982187] lo: Disabled Privacy Extensions
[    2.982687] NET: Registered protocol family 17
[    2.982726] Bluetooth: L2CAP ver 2.11
[    2.982729] Bluetooth: L2CAP socket layer initialized
[    2.982734] Bluetooth: SCO (Voice Link) ver 0.6
[    2.982737] Bluetooth: SCO socket layer initialized
[    2.982843] Bluetooth: RFCOMM socket layer initialized
[    2.982862] Bluetooth: RFCOMM TTY layer initialized
[    2.982865] Bluetooth: RFCOMM ver 1.10
[    2.982909] powernow-k8: Processor cpuid 662 not supported
[    2.982956] IO APIC resources could be not be allocated.
[    2.983033] Using IPI No-Shortcut mode
[    2.983245] registered taskstats version 1
[    2.983397]   Magic number: 5:595:592
[    2.983577] rtc_cmos 00:02: setting system clock to 2009-08-10 17:35:07 UTC (1249925707)
[    2.983583] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    2.983586] EDD information not available.
[    2.985819] Freeing unused kernel memory: 532k freed
[    2.986024] Write protecting the kernel text: 4116k
[    2.986084] Write protecting the kernel read-only data: 1524k
[    3.020765] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input4
[    3.289012] usb 1-1: new low speed USB device using uhci_hcd and address 2
[    3.523321] usb 1-1: configuration #1 chosen from 1 choice
[    3.537759] Floppy drive(s): fd0 is 1.44M
[    3.559646] FDC 0 is a post-1991 82077
[    3.640748] usb 1-2: new full speed USB device using uhci_hcd and address 3
[    3.742876] e100: Intel(R) PRO/100 Network Driver, 3.5.23-k6-NAPI
[    3.742884] e100: Copyright(c) 1999-2006 Intel Corporation
[    3.743349] ACPI: PCI Interrupt Link [LNKC] enabled at IRQ 10
[    3.743356] PCI: setting IRQ 10 as level-triggered
[    3.743365] e100 0000:00:0a.0: PCI INT A -> Link[LNKC] -> GSI 10 (level, low) -> IRQ 10
[    3.783055] e100: eth0: e100_probe: addr 0xdd9ff000, irq 10, MAC addr 00:a0:c9:aa:1b:6d
[    3.891296] usb 1-2: configuration #1 chosen from 1 choice
[    4.008760] usb 2-1: new full speed USB device using uhci_hcd and address 2
[    4.193094] usb 2-1: configuration #1 chosen from 1 choice
[    4.196876] hub 2-1:1.0: USB hub found
[    4.200792] hub 2-1:1.0: 4 ports detected
[    4.545000] usbcore: registered new interface driver hiddev
[    4.565521] input: USB Optical Mouse as /devices/pci0000:00/0000:00:07.2/usb1/1-1/1-1:1.0/input/input5
[    4.591811] generic-usb 0003:0461:4D20.0001: input,hidraw0: USB HID v1.11 Mouse [USB Optical Mouse] on usb-0000:00:07.2-1/input0
[    4.591862] usbcore: registered new interface driver usbhid
[    4.591869] usbhid: v2.6:USB HID core driver
[    4.694280] PM: Starting manual resume from disk
[    4.694290] PM: Resume from partition 8:5
[    4.694293] PM: Checking hibernation image.
[    4.694608] PM: Resume from disk failed.
[    4.756713] kjournald starting.  Commit interval 5 seconds
[    4.756758] EXT3-fs: mounted filesystem with ordered data mode.
[   13.003627] udev: starting version 141
[   13.227374] Linux agpgart interface v0.103
[   13.337181] agpgart: Detected VIA Twister-K/KT133x/KM133 chipset
[   13.343745] agpgart-via 0000:00:00.0: AGP aperture is 64M @ 0xe0000000
[   13.402289] parport_pc: VIA 686A/8231 detected
[   13.402297] parport_pc: probing current configuration
[   13.402317] parport_pc: Current parallel port base: 0x378
[   13.402398] parport0: PC-style at 0x378 (0x778), irq 7, using FIFO [PCSPP,TRISTATE,COMPAT,ECP]
[   13.496905] parport_pc: VIA parallel port: io=0x378, irq=7
[   13.574640] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   13.653157] usblp0: USB Bidirectional printer dev 3 if 0 alt 0 proto 2 vid 0x04F9 pid 0x001A
[   13.653210] usbcore: registered new interface driver usblp
[   13.907072] input: PC Speaker as /devices/platform/pcspkr/input/input6
[   14.697154] ENS1371 0000:00:0e.0: PCI INT A -> Link[LNKC] -> GSI 10 (level, low) -> IRQ 10
[   15.022018] ppdev: user-space parallel port driver
[   16.073407] Control name 'Sigmatel Surround Phase Inversion Playback Switch' truncated to 'Sigmatel Surround Phase Inversion Playback '
[   16.395657] lp0: using parport0 (interrupt-driven).
[   16.674955] Adding 730916k swap on /dev/sda5.  Priority:-1 extents:1 across:730916k
[   17.421648] EXT3 FS on sda1, internal journal
[   19.249094] type=1505 audit(1249925723.764:2): operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" name2="default" pid=1829
[   19.381393] type=1505 audit(1249925723.896:3): operation="profile_load" name="/sbin/dhclient-script" name2="default" pid=1833
[   19.381927] type=1505 audit(1249925723.896:4): operation="profile_load" name="/sbin/dhclient3" name2="default" pid=1833
[   19.382065] type=1505 audit(1249925723.896:5): operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" name2="default" pid=1833
[   19.382190] type=1505 audit(1249925723.896:6): operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" name2="default" pid=1833
[   19.486468] type=1505 audit(1249925724.000:7): operation="profile_load" name="/usr/bin/freshclam" name2="default" pid=1838
[   19.843586] type=1505 audit(1249925724.356:8): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=1842
[   19.845003] type=1505 audit(1249925724.360:9): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=1842
[   19.923260] type=1505 audit(1249925724.436:10): operation="profile_load" name="/usr/sbin/tcpdump" name2="default" pid=1846
[   27.265458] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   27.265467] Bluetooth: BNEP filters: protocol multicast
[   27.342640] Bridge firewalling registered
[   33.502439] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   33.504849] e100: eth0: e100_watchdog: link up, 100Mbps, full-duplex
[   33.511349] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   34.393533] ppdev0: registered pardevice
[   34.441224] ppdev0: unregistered pardevice
[   43.560216] eth0: no IPv6 routers present

---

### Post by P4man on 2009-08-10
> **darkdesire said:**
> The option **noapictime irqpol**l gave successfull results. Some of the others froze the system.

Many thanks for this. What does it do exactly? 

Hey, glad it worked!

As to what it does exactly.. well. I could tell you of course, 

...but ahm.. I'd have to .. ahm.. get a PhD first I guess lol. 

I dont know exactly. I roughly know what apic is, I know more or less what irq polling is, but not well enough to explain without making a dire fool out of myself. I do know very well its a very frequent cause of all kinds of weird issues on linux. I also know you don't need apic on single cpu system. And I know I bookmarked those boot options a long time ago, and they have helped me quite a bit :)

If you want to know more, google, or ask linus :p

---

### Post by bbob on 2010-01-25
I know this is an old thread, but I have to say

> noapictimer irqpoll

worked for me!  USB mouse and k/b now work perfectly for me in 9.10 64 bit.

Thanks P4man!

---

### Post by Return-Path on 2010-03-14
'noapictimer irqpoll' works for me too, with an Elitegroup ATI motherboard (RS480+SB400).  Thanks all.

---

### Post by nutsy.ben on 2010-05-03
Also worked for me ... 

Was a longlong problem I had for reading CDs and using an usb mouse ... Now I can throw this old keyboard to the trash and get my more recent wireless one.

Thanks

---

### Post by nutsy.ben on 2010-07-07
> **P4man said:**
> Then im guessing its apic issue. When you boot, go in to the grub menu, select your kernel and press "e". Select the kernel line and add one of these set of switches to the kernel parameters:

```
noapic nolapic

noapic acpi=noirq

noapic acpi=off

noapictimer

noapictimer irqpoll

noapic acpi=noirq nolapic
```

So for instance:

```
kernel	/boot/vmlinuz-2.6.28-14-generic root=UUID=0e5317cf-1aa2-4b20-9ffa-f17c41f48f37 ro quiet splash noapic acpi=noirq

```

To boot the kernel after making the changes, press B in grub

Try them one by one (I mean one line) until hopefully the problem dissapears. Then report back.

edit: also attach the output of dmesg here if possible




noapictimer irqpoll was the line working for me !!! :)
I was using a HP media center desktop, low speed for CD and USB ... everything is back to normal! YEAAAAAH  !! 
Thanks,

Ben

---

### Post by matewka on 2011-06-13
For those who are using Grub2 (like me) useful can be information that:
1. grub menu file is /boot/grub/grub.cfg (not /boot/grub/menu.lst)
2. try looking there for line "linux    /boot/vmlinuz-2.6.32-22-generic root=UUID=e0540c12-9dbf-49a5-aff5-b9a0062a050e ro   quiet splash" instead of "kernel /boot/vmlinuz...",
and of course "noapictimer irqpoll" works just fine at the end of this line.

---

### Post by aperomsik on 2011-07-18
This thread saved us on an emachines T6524, which was working fine until we swapped out the video card for a newer nv-based card than we had before. 

> **matewka said:**
> For those who are using Grub2 (like me) useful can be information that:
1. grub menu file is /boot/grub/grub.cfg (not /boot/grub/menu.lst)
2. try looking there for line "linux    /boot/vmlinuz-2.6.32-22-generic root=UUID=e0540c12-9dbf-49a5-aff5-b9a0062a050e ro   quiet splash" instead of "kernel /boot/vmlinuz...",
and of course "noapictimer irqpoll" works just fine at the end of this line.

Actually grub.cfg says not to modify it... seems better to add the arguments to /etc/default/grub, perhaps on the line that starts GRUB_CMDLINE_LINUX_DEFAULT (but inside the quotes) and then run sudo update-grub.

---

