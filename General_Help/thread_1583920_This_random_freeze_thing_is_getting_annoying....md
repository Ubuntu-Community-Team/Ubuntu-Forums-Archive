---
title: "This random freeze thing is getting annoying..."
date: 2010-09-28
forum: General Help
---

### Post by edward1978 on 2010-09-28
Ok I have no idea why this is happening, I can go days without a freeze & one day might have 3. No clues in any log file, I have had SuSE/OpenSuSE for years without a whole system freeze. 8.04 froze & so does this version. I had Ubuntu for a almost 2 months.

---

### Post by TeoBigusGeekus on 2010-09-28
The 
```
dmesg
```
output might be helpful...

---

### Post by 7h3d4rk0n3 on 2010-09-28
Try turning off Compiz/Desktop effects. 
To do so navigate to:
System >> Preferences >> Appearance

Let me know if this helps at all.

---

### Post by edward1978 on 2010-09-28
> **TeoBigusGeekus said:**
> The 
```
dmesg
```output might be helpful...

[    0.000000] Memory: 4104624k/5505024k available (4832k kernel code, 87072k reserved, 2221k data, 676k init, 3281864k highmem)
[    0.000000] virtual kernel memory layout:
[    0.000000]     fixmap  : 0xfff1d000 - 0xfffff000   ( 904 kB)
[    0.000000]     pkmap   : 0xffa00000 - 0xffc00000   (2048 kB)
[    0.000000]     vmalloc : 0xf81fe000 - 0xff9fe000   ( 120 MB)
[    0.000000]     lowmem  : 0xc0000000 - 0xf79fe000   ( 889 MB)
[    0.000000]       .init : 0xc07e4000 - 0xc088d000   ( 676 kB)
[    0.000000]       .data : 0xc05b82fb - 0xc07e3828   (2221 kB)
[    0.000000]       .text : 0xc0100000 - 0xc05b82fb   (4832 kB)
[    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.000000] SLUB: Genslabs=13, HWalign=64, Order=0-3, MinObjects=0, CPUs=2, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000] NR_IRQS:2304 nr_irqs:424
[    0.000000] spurious 8259A interrupt: IRQ7.
[    0.000000] Console: colour VGA+ 80x25
[    0.000000] console [tty0] enabled
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 2666.833 MHz processor.
[    0.008005] Calibrating delay loop (skipped), value calculated using timer frequency.. 5333.66 BogoMIPS (lpj=10667332)
[    0.008138] Security Framework initialized
[    0.008216] AppArmor: AppArmor initialized
[    0.008278] Mount-cache hash table entries: 512
[    0.008448] Initializing cgroup subsys ns
[    0.008509] Initializing cgroup subsys cpuacct
[    0.008570] Initializing cgroup subsys memory
[    0.008634] Initializing cgroup subsys devices
[    0.012003] Initializing cgroup subsys freezer
[    0.012063] Initializing cgroup subsys net_cls
[    0.012138] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.012239] CPU: L2 cache: 6144K
[    0.012297] CPU: Physical Processor ID: 0
[    0.012356] CPU: Processor Core ID: 0
[    0.012415] mce: CPU supports 6 MCE banks
[    0.012480] using mwait in idle threads.
[    0.012543] Performance Events: Core2 events, Intel PMU driver.
[    0.012689] ... version:                2
[    0.012748] ... bit width:              40
[    0.012806] ... generic registers:      2
[    0.012865] ... value mask:             000000ffffffffff
[    0.012925] ... max period:             000000007fffffff
[    0.012986] ... fixed-purpose events:   3
[    0.013044] ... event mask:             0000000700000003
[    0.013106] Checking 'hlt' instruction... OK.
[    0.030237] ftrace: converting mcount calls to 0f 1f 44 00 00
[    0.030301] ftrace: allocating 22411 entries in 44 pages
[    0.032038] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.032099] SMP disabled
[    0.032279] Brought up 1 CPUs
[    0.032337] Total of 1 processors activated (5333.66 BogoMIPS).
[    0.036028] CPU0 attaching NULL sched-domain.
[    0.036122] devtmpfs: initialized
[    0.036443] regulator: core version 0.5
[    0.036527] Time: 13:19:42  Date: 09/28/10
[    0.036618] NET: Registered protocol family 16
[    0.036758] EISA bus registered
[    0.042980] PCI: PCI BIOS revision 3.00 entry at 0xfa7a0, last bus=4
[    0.043042] PCI: Using configuration type 1 for base access
[    0.043836] bio: create slab <bio-0> at 0
[    0.043927] ACPI: Interpreter disabled.
[    0.044036] vgaarb: loaded
[    0.044168] SCSI subsystem initialized
[    0.044249] libata version 3.00 loaded.
[    0.044296] usbcore: registered new interface driver usbfs
[    0.044364] usbcore: registered new interface driver hub
[    0.044442] usbcore: registered new device driver usb
[    0.044573] PCI: Probing PCI hardware
[    0.044632] PCI: Probing PCI hardware (bus 00)
[    0.045406] pci 0000:00:03.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.045469] pci 0000:00:03.0: PME# disabled
[    0.045574] pci 0000:00:06.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.045637] pci 0000:00:06.0: PME# disabled
[    0.045740] pci 0000:00:07.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.045803] pci 0000:00:07.0: PME# disabled
[    0.046057] HPET not enabled in BIOS. You might try hpet=force boot option
[    0.046164] pci 0000:00:0a.1: reg 20 io port: [0xfc00-0xfc3f]
[    0.046169] pci 0000:00:0a.1: reg 24 io port: [0xf800-0xf83f]
[    0.046193] pci 0000:00:0a.1: PME# supported from D3hot D3cold
[    0.046258] pci 0000:00:0a.1: PME# disabled
[    0.046383] pci 0000:00:0b.0: reg 10 32bit mmio: [0xcffff000-0xcfffffff]
[    0.046414] pci 0000:00:0b.0: supports D1 D2
[    0.046416] pci 0000:00:0b.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.046480] pci 0000:00:0b.0: PME# disabled
[    0.046563] pci 0000:00:0b.1: reg 10 32bit mmio: [0xcfffe000-0xcfffe0ff]
[    0.046596] pci 0000:00:0b.1: supports D1 D2
[    0.046598] pci 0000:00:0b.1: PME# supported from D0 D1 D2 D3hot D3cold
[    0.046662] pci 0000:00:0b.1: PME# disabled
[    0.046760] pci 0000:00:0d.0: reg 20 io port: [0xf400-0xf40f]
[    0.046804] pci 0000:00:0e.0: reg 10 io port: [0x9f0-0x9f7]
[    0.046809] pci 0000:00:0e.0: reg 14 io port: [0xbf0-0xbf3]
[    0.046813] pci 0000:00:0e.0: reg 18 io port: [0x970-0x977]
[    0.046817] pci 0000:00:0e.0: reg 1c io port: [0xb70-0xb73]
[    0.046822] pci 0000:00:0e.0: reg 20 io port: [0xe000-0xe00f]
[    0.046826] pci 0000:00:0e.0: reg 24 32bit mmio: [0xcfffd000-0xcfffdfff]
[    0.046877] pci 0000:00:0f.0: reg 10 io port: [0x9e0-0x9e7]
[    0.046881] pci 0000:00:0f.0: reg 14 io port: [0xbe0-0xbe3]
[    0.046886] pci 0000:00:0f.0: reg 18 io port: [0x960-0x967]
[    0.046890] pci 0000:00:0f.0: reg 1c io port: [0xb60-0xb63]
[    0.046895] pci 0000:00:0f.0: reg 20 io port: [0xcc00-0xcc0f]
[    0.046899] pci 0000:00:0f.0: reg 24 32bit mmio: [0xcfffc000-0xcfffcfff]
[    0.046993] pci 0000:00:10.1: reg 10 32bit mmio: [0xcfff4000-0xcfff7fff]
[    0.047030] pci 0000:00:10.1: PME# supported from D3hot D3cold
[    0.047092] pci 0000:00:10.1: PME# disabled
[    0.047186] pci 0000:00:14.0: reg 10 32bit mmio: [0xcfffb000-0xcfffbfff]
[    0.047190] pci 0000:00:14.0: reg 14 io port: [0xc800-0xc807]
[    0.047215] pci 0000:00:14.0: supports D1 D2
[    0.047217] pci 0000:00:14.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.047281] pci 0000:00:14.0: PME# disabled
[    0.048046] pci 0000:01:00.0: reg 10 32bit mmio: [0xcc000000-0xccffffff]
[    0.048054] pci 0000:01:00.0: reg 14 64bit mmio pref: [0xb0000000-0xbfffffff]
[    0.048062] pci 0000:01:00.0: reg 1c 64bit mmio: [0xca000000-0xcbffffff]
[    0.048067] pci 0000:01:00.0: reg 24 io port: [0xbc00-0xbc7f]
[    0.048071] pci 0000:01:00.0: reg 30 32bit mmio pref: [0x000000-0x01ffff]
[    0.048131] pci 0000:00:03.0: bridge io port: [0xb000-0xbfff]
[    0.048133] pci 0000:00:03.0: bridge 32bit mmio: [0xca000000-0xcdffffff]
[    0.048137] pci 0000:00:03.0: bridge 64bit mmio pref: [0xb0000000-0xbfffffff]
[    0.048260] pci 0000:00:10.0: transparent bridge
[    0.048322] pci 0000:00:10.0: bridge 32bit mmio: [0x000000-0x0fffff]
[    0.048856] vgaarb: device added: PCI:0000:01:00.0,decodes=io+mem,owns=io+mem,locks=none
[    0.049209] pci 0000:00:10.0: BAR 14: can't allocate resource
[    0.049417] NetLabel: Initializing
[    0.049474] NetLabel:  domain hash size = 128
[    0.049533] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.049600] NetLabel:  unlabeled traffic allowed by default
[    0.049697] Switching to clocksource tsc
[    0.051313] AppArmor: AppArmor Filesystem Enabled
[    0.051373] pnp: PnP ACPI: disabled
[    0.051432] PnPBIOS: Scanning system for PnP BIOS support...
[    0.051562] PnPBIOS: Found PnP BIOS installation structure at 0xc00fb390
[    0.051562] PnPBIOS: PnP BIOS version 1.0, entry 0xf0000:0xb3c0, dseg 0xf0000
[    0.051562] PnPBIOS: 13 nodes reported by PnP BIOS; 13 recorded by driver
[    0.051562] system 00:07: iomem range 0x0-0x9ffff could not be reserved
[    0.051562] system 00:07: iomem range 0xfffffffffffe0000-0xffffffffffffffff has been reserved
[    0.051562] system 00:07: iomem range 0xfffffffffec00000-0xfffffffffec0ffff has been reserved
[    0.051562] system 00:07: iomem range 0xfffffffffee00000-0xfffffffffee0ffff has been reserved
[    0.051562] system 00:07: iomem range 0x100000-0xffffff could not be reserved
[    0.051562] system 00:08: iomem range 0xf0000-0xf3fff could not be reserved
[    0.051562] system 00:08: iomem range 0xf4000-0xfffff could not be reserved
[    0.051562] system 00:08: iomem range 0xd5800-0xd7fff has been reserved
[    0.051562] system 00:08: iomem range 0xd0000-0xd3fff has been reserved
[    0.051562] pci 0000:00:03.0: PCI bridge, secondary bus 0000:01
[    0.051562] pci 0000:00:03.0:   IO window: 0xb000-0xbfff
[    0.051572] pci 0000:00:03.0:   MEM window: 0xca000000-0xcdffffff
[    0.051635] pci 0000:00:03.0:   PREFETCH window: 0x000000b0000000-0x000000bfffffff
[    0.051711] pci 0000:00:06.0: PCI bridge, secondary bus 0000:02
[    0.051773] pci 0000:00:06.0:   IO window: disabled
[    0.051834] pci 0000:00:06.0:   MEM window: disabled
[    0.051894] pci 0000:00:06.0:   PREFETCH window: disabled
[    0.051957] pci 0000:00:07.0: PCI bridge, secondary bus 0000:03
[    0.052018] pci 0000:00:07.0:   IO window: disabled
[    0.052079] pci 0000:00:07.0:   MEM window: disabled
[    0.052139] pci 0000:00:07.0:   PREFETCH window: disabled
[    0.052202] pci 0000:00:10.0: PCI bridge, secondary bus 0000:04
[    0.052263] pci 0000:00:10.0:   IO window: disabled
[    0.052325] pci 0000:00:10.0:   MEM window: disabled
[    0.052386] pci 0000:00:10.0:   PREFETCH window: disabled
[    0.052454] pci 0000:00:03.0: setting latency timer to 64
[    0.052459] pci 0000:00:06.0: setting latency timer to 64
[    0.052465] pci 0000:00:07.0: setting latency timer to 64
[    0.052470] pci 0000:00:10.0: setting latency timer to 64
[    0.052473] pci_bus 0000:00: resource 0 io:  [0x00-0xffff]
[    0.052475] pci_bus 0000:00: resource 1 mem: [0x000000-0xffffffffffffffff]
[    0.052477] pci_bus 0000:01: resource 0 io:  [0xb000-0xbfff]
[    0.052479] pci_bus 0000:01: resource 1 mem: [0xca000000-0xcdffffff]
[    0.052481] pci_bus 0000:01: resource 2 pref mem [0xb0000000-0xbfffffff]
[    0.052483] pci_bus 0000:04: resource 1 mem: [0x0-0xfffff]
[    0.052485] pci_bus 0000:04: resource 3 io:  [0x00-0xffff]
[    0.052487] pci_bus 0000:04: resource 4 mem: [0x000000-0xffffffffffffffff]
[    0.052509] NET: Registered protocol family 2
[    0.052632] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.052918] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.053226] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.053408] TCP: Hash tables configured (established 131072 bind 65536)
[    0.053470] TCP reno registered
[    0.053571] NET: Registered protocol family 1
[    0.077888] pci 0000:01:00.0: Boot video device
[    0.077992] cpufreq-nforce2: No nForce2 chipset.
[    0.078064] Scanning for low memory corruption every 60 seconds
[    0.078189] audit: initializing netlink socket (disabled)
[    0.078253] type=2000 audit(1285679982.077:1): initialized
[    0.085908] Trying to unpack rootfs image as initramfs...
[    0.094156] highmem bounce pool size: 64 pages
[    0.094218] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    0.099028] VFS: Disk quotas dquot_6.5.2
[    0.099130] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.099611] fuse init (API version 7.13)
[    0.099734] msgmni has been set to 1609
[    0.105955] alg: No test for stdrng (krng)
[    0.106052] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.106128] io scheduler noop registered
[    0.106186] io scheduler anticipatory registered
[    0.106246] io scheduler deadline registered
[    0.106334] io scheduler cfq registered (default)
[    0.106523]   alloc irq_desc for 24 on node -1
[    0.106525]   alloc kstat_irqs on node -1
[    0.106619] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.106696] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.107770] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    0.107925] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.108327] 00:0b: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.109168] brd: module loaded
[    0.109577] loop: module loaded
[    0.109697] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[    0.109946] pata_acpi 0000:00:0d.0: setting latency timer to 64
[    0.109975] pata_acpi 0000:00:0e.0: setting latency timer to 64
[    0.110000] pata_acpi 0000:00:0f.0: setting latency timer to 64
[    0.110237] Fixed MDIO Bus: probed
[    0.110318] PPP generic driver version 2.4.2
[    0.110400] tun: Universal TUN/TAP device driver, 1.6
[    0.110461] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.110596] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.110678] ehci_hcd 0000:00:0b.1: setting latency timer to 64
[    0.110681] ehci_hcd 0000:00:0b.1: EHCI Host Controller
[    0.110762] ehci_hcd 0000:00:0b.1: new USB bus registered, assigned bus number 1
[    0.110853] ehci_hcd 0000:00:0b.1: debug port 1
[    0.110918] ehci_hcd 0000:00:0b.1: cache line size of 32 is not supported
[    0.110924] ehci_hcd 0000:00:0b.1: irq 11, io mem 0xcfffe000
[    0.111000] isapnp: Scanning for PnP cards...
[    0.121798] ehci_hcd 0000:00:0b.1: USB 2.0 started, EHCI 1.00
[    0.121937] usb usb1: configuration #1 chosen from 1 choice
[    0.122023] hub 1-0:1.0: USB hub found
[    0.122086] hub 1-0:1.0: 8 ports detected
[    0.122188] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.122268] ohci_hcd 0000:00:0b.0: setting latency timer to 64
[    0.122270] ohci_hcd 0000:00:0b.0: OHCI Host Controller
[    0.122351] ohci_hcd 0000:00:0b.0: new USB bus registered, assigned bus number 2
[    0.122435] ohci_hcd 0000:00:0b.0: irq 10, io mem 0xcffff000
[    0.179960] usb usb2: configuration #1 chosen from 1 choice
[    0.180040] hub 2-0:1.0: USB hub found
[    0.180105] hub 2-0:1.0: 8 ports detected
[    0.180206] uhci_hcd: USB Universal Host Controller Interface driver
[    0.180328] PNP: PS/2 Controller [PNP0303,PNP0f13] at 0x60,0x64 irq 1,12
[    0.186974] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.187037] serio: i8042 AUX port at 0x60,0x64 irq 12
[    0.187181] mice: PS/2 mouse device common for all mice
[    0.187311] rtc_cmos 00:03: rtc core: registered rtc_cmos as rtc0
[    0.187390] rtc0: alarms up to one day, 114 bytes nvram
[    0.187520] device-mapper: uevent: version 1.0.3
[    0.187656] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: [email]dm-devel@redhat.com[/email]
[    0.189919] device-mapper: multipath: version 1.1.0 loaded
[    0.189981] device-mapper: multipath round-robin: version 1.0.0 loaded
[    0.192017] EISA: Probing bus 0 at eisa.0
[    0.192099] EISA: Detected 0 cards.
[    0.193299] cpuidle: using governor ladder
[    0.193358] cpuidle: using governor menu
[    0.193768] TCP cubic registered
[    0.193962] NET: Registered protocol family 10
[    0.194368] lo: Disabled Privacy Extensions
[    0.194691] NET: Registered protocol family 17
[    0.194774] Using IPI No-Shortcut mode
[    0.194880] PM: Resume from disk failed.
[    0.194890] registered taskstats version 1
[    0.195257]   Magic number: 10:771:332
[    0.195327] tty tty53: hash matches
[    0.195420] rtc_cmos 00:03: setting system clock to 2010-09-28 13:19:42 UTC (1285679982)
[    0.195496] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.195558] EDD information not available.
[    0.211334] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
[    0.387060] Freeing initrd memory: 7728k freed
[    0.522259] usb 1-7: new high speed USB device using ehci_hcd and address 2
[    0.609265] isapnp: No Plug & Play device found
[    0.609337] Freeing unused kernel memory: 676k freed
[    0.609976] Write protecting the kernel text: 4836k
[    0.610091] Write protecting the kernel read-only data: 1880k
[    0.624504] udev: starting version 151
[    0.694913] usb 1-7: configuration #1 chosen from 1 choice
[    0.712789] pata_amd 0000:00:0d.0: version 0.4.1
[    0.712828] pata_amd 0000:00:0d.0: setting latency timer to 64
[    0.734037] scsi0 : pata_amd
[    0.735105] scsi1 : pata_amd
[    0.735231] ata1: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xf400 irq 14
[    0.735295] ata2: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xf408 irq 15
[    0.735540] sata_nv 0000:00:0e.0: version 3.5
[    0.735546] sata_nv 0000:00:0e.0: Using SWNCQ mode
[    0.735643] sata_nv 0000:00:0e.0: setting latency timer to 64
[    0.735746] scsi2 : sata_nv
[    0.735881] scsi3 : sata_nv
[    0.735965] ata3: SATA max UDMA/133 cmd 0x9f0 ctl 0xbf0 bmdma 0xe000 irq 10
[    0.736028] ata4: SATA max UDMA/133 cmd 0x970 ctl 0xb70 bmdma 0xe008 irq 10
[    0.736133] forcedeth: Reverse Engineered nForce ethernet driver. Version 0.64.
[    0.736216] forcedeth 0000:00:14.0: setting latency timer to 64
[    0.736243] nv_probe: set workaround bit for reversed mac addr
[    0.898070] ata1.00: ATAPI: SONY DVD-ROM DDU1615, FYS2, max UDMA/33
[    0.898151] ata1: nv_mode_filter: 0x739f&0x73ff->0x739f, BIOS=0x7000 (0xc0000000) ACPI=0x0
[    0.914019] ata1.00: configured for UDMA/33
[    0.914831] scsi 0:0:0:0: CD-ROM            SONY     DVD-ROM DDU1615  FYS2 PQ: 0 ANSI: 5
[    0.916777] sr0: scsi3-mmc drive: 4x/40x cd/rw xa/form2 cdda tray
[    0.916841] Uniform CD-ROM driver Revision: 3.20
[    0.917061] sr 0:0:0:0: Attached scsi CD-ROM sr0
[    0.917143] sr 0:0:0:0: Attached scsi generic sg0 type 5
[    0.917272] ata2: port disabled. ignoring.
[    1.053792] usb 2-8: new low speed USB device using ohci_hcd and address 2
[    1.201815] ata3: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    1.210723] ata3.00: ATA-7: WL400GSA1672, 12.06H12, max UDMA/133
[    1.210788] ata3.00: 781422768 sectors, multi 16: LBA48 NCQ (depth 31/32)
[    1.226740] ata3.00: configured for UDMA/133
[    1.226868] scsi 2:0:0:0: Direct-Access     ATA      WL400GSA1672     12.0 PQ: 0 ANSI: 5
[    1.227080] sd 2:0:0:0: [sda] 781422768 512-byte logical blocks: (400 GB/372 GiB)
[    1.227188] sd 2:0:0:0: [sda] Write Protect is off
[    1.227248] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.227267] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.227434]  sda:
[    1.227613] sd 2:0:0:0: Attached scsi generic sg1 type 0
[    1.245980]  sda1 sda2 <
[    1.254493] forcedeth 0000:00:14.0: ifname eth0, PHY OUI 0x5043 @ 1, addr 00:04:4b:06:e2:5e
[    1.254622] forcedeth 0000:00:14.0: highdma pwrctl gbit lnktim desc-v3
[    1.254695] sata_nv 0000:00:0f.0: Using SWNCQ mode
[    1.254795] sata_nv 0000:00:0f.0: setting latency timer to 64
[    1.254991] scsi4 : sata_nv
[    1.255118] scsi5 : sata_nv
[    1.255204] ata5: SATA max UDMA/133 cmd 0x9e0 ctl 0xbe0 bmdma 0xcc00 irq 11
[    1.255268] ata6: SATA max UDMA/133 cmd 0x960 ctl 0xb60 bmdma 0xcc08 irq 11
[    1.267087]  sda5
[    1.273924] usb 2-8: configuration #1 chosen from 1 choice
[    1.281460]  sda6 >
[    1.281983] sd 2:0:0:0: [sda] Attached SCSI disk
[    1.548204] ata4: SATA link down (SStatus 0 SControl 300)
[    1.580197] ata5: SATA link down (SStatus 0 SControl 300)
[    2.045807] ata6: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    2.053936] ata6.00: ATAPI: HL-DT-ST DVDRAM GH22NS50, TN02, max UDMA/100
[    2.069942] ata6.00: configured for UDMA/100
[    2.078562] scsi 5:0:0:0: CD-ROM            HL-DT-ST DVDRAM GH22NS50  TN02 PQ: 0 ANSI: 5
[    2.100440] sr1: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
[    2.100888] sr 5:0:0:0: Attached scsi CD-ROM sr1
[    2.101199] sr 5:0:0:0: Attached scsi generic sg2 type 5
[    2.106781] usbcore: registered new interface driver hiddev
[    2.126873] input: Logitech Logitech Dual Action as /devices/pci0000:00/0000:00:0b.0/usb2/2-8/2-8:1.0/input/input2
[    2.127018] generic-usb 0003:046D:C216.0001: input,hidraw0: USB HID v1.10 Joystick [Logitech Logitech Dual Action] on usb-0000:00:0b.0-8/input0
[    2.127114] usbcore: registered new interface driver usbhid
[    2.127175] usbhid: v2.6:USB HID core driver
[    2.605284] EXT4-fs (sda5): INFO: recovery required on readonly filesystem
[    2.605438] EXT4-fs (sda5): write access will be enabled during recovery
[    4.064451] EXT4-fs (sda5): orphan cleanup on readonly fs
[    4.064601] EXT4-fs (sda5): ext4_orphan_cleanup: deleting unreferenced inode 275821
[    4.064713] EXT4-fs (sda5): ext4_orphan_cleanup: deleting unreferenced inode 527495
[    4.064742] EXT4-fs (sda5): ext4_orphan_cleanup: deleting unreferenced inode 527494
[    4.064753] EXT4-fs (sda5): 3 orphan inodes deleted
[    4.064895] EXT4-fs (sda5): recovery complete
[    4.521406] EXT4-fs (sda5): mounted filesystem with ordered data mode
[   17.140948] Adding 871416k swap on /dev/sda6.  Priority:-1 extents:1 across:871416k 
[   17.155316] udev: starting version 151
[   17.314565] i2c i2c-0: nForce2 SMBus adapter at 0xfc00
[   17.314581] i2c i2c-1: nForce2 SMBus adapter at 0xf800
[   17.317611] Disabling lock debugging due to kernel taint
[   17.366566] lp: driver loaded but no devices found
[   17.416087] ndiswrapper version 1.55 loaded (smp=yes, preempt=no)
[   17.425683] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   17.456233] Linux agpgart interface v0.103
[   17.506250] [drm] Initialized drm 1.1.0 20060810
[   17.509964] type=1505 audit(1285694399.814:2):  operation="profile_load" pid=535 name="/sbin/dhclient3"
[   17.510479] type=1505 audit(1285694399.814:3):  operation="profile_load" pid=535 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[   17.510756] type=1505 audit(1285694399.814:4):  operation="profile_load" pid=535 name="/usr/lib/connman/scripts/dhclient-script"
[   17.554159] nouveau 0000:01:00.0: setting latency timer to 64
[   17.559926] [drm] nouveau 0000:01:00.0: Detected an NV50 generation card (0x092000a2)
[   17.560427] [drm] nouveau 0000:01:00.0: Attempting to load BIOS image from PRAMIN
[   17.614453] [drm] nouveau 0000:01:00.0: ... appears to be valid
[   17.614456] [drm] nouveau 0000:01:00.0: BIT BIOS found
[   17.614458] [drm] nouveau 0000:01:00.0: Bios version 62.92.25.00
[   17.614460] [drm] nouveau 0000:01:00.0: TMDS table revision 2.0 not currently supported
[   17.614463] [drm] nouveau 0000:01:00.0: Found Display Configuration Block version 4.0
[   17.614465] [drm] nouveau 0000:01:00.0: DCB connector table: VHER 0x40 5 16 4
[   17.614468] [drm] nouveau 0000:01:00.0:   0: 0x00001030: type 0x30 idx 0 tag 0x07
[   17.614470] [drm] nouveau 0000:01:00.0:   1: 0x00002130: type 0x30 idx 1 tag 0x08
[   17.614472] [drm] nouveau 0000:01:00.0:   2: 0x00000210: type 0x10 idx 2 tag 0xff
[   17.614474] [drm] nouveau 0000:01:00.0:   3: 0x00000211: type 0x11 idx 2 tag 0xff
[   17.614476] [drm] nouveau 0000:01:00.0:   4: 0x00000213: type 0x13 idx 2 tag 0xff
[   17.614479] [drm] nouveau 0000:01:00.0: Raw DCB entry 0: 02000300 00000028
[   17.614481] [drm] nouveau 0000:01:00.0: Raw DCB entry 1: 01000302 00000030
[   17.614483] [drm] nouveau 0000:01:00.0: Raw DCB entry 2: 04011310 00000028
[   17.614485] [drm] nouveau 0000:01:00.0: Raw DCB entry 3: 02011312 00000030
[   17.614487] [drm] nouveau 0000:01:00.0: Raw DCB entry 4: 010223f1 00c0c080
[   17.614492] [drm] nouveau 0000:01:00.0: Parsing VBIOS init table 0 at offset 0xC17F
[   17.697848] [drm] nouveau 0000:01:00.0: Parsing VBIOS init table 1 at offset 0xC530
[   17.713664] [drm] nouveau 0000:01:00.0: Parsing VBIOS init table 2 at offset 0xD2AB
[   17.713672] [drm] nouveau 0000:01:00.0: Parsing VBIOS init table 3 at offset 0xD3CD
[   17.721732] [drm] nouveau 0000:01:00.0: Parsing VBIOS init table 4 at offset 0xD5FD
[   17.721735] [drm] nouveau 0000:01:00.0: Parsing VBIOS init table at offset 0xD662
[   17.745664] [drm] nouveau 0000:01:00.0: 0xD662: Condition still not met after 20ms, skipping following opcodes
[   17.745671] [drm] nouveau 0000:01:00.0: 0xB3B0: parsing output script 0
[   17.745675] [drm] nouveau 0000:01:00.0: 0xB3B0: parsing output script 0
[   17.745677] [drm] nouveau 0000:01:00.0: 0x9FAE: parsing output script 0
[   17.827865] [TTM] Zone  kernel: Available graphics memory: 416118 kiB.
[   17.827867] [TTM] Zone highmem: Available graphics memory: 2057050 kiB.
[   17.827874] [drm] nouveau 0000:01:00.0: 512 MiB VRAM
[   17.842260] [drm] nouveau 0000:01:00.0: 512 MiB GART (aperture)
[   17.843764] [drm] nouveau 0000:01:00.0: Allocating FIFO number 1
[   17.847270] [drm] nouveau 0000:01:00.0: nouveau_channel_alloc: initialised FIFO 1
[   17.847666] [drm] nouveau 0000:01:00.0: Detected a DAC output
[   17.847669] [drm] nouveau 0000:01:00.0: Detected a TMDS output
[   17.847671] [drm] nouveau 0000:01:00.0: Detected a DAC output
[   17.847673] [drm] nouveau 0000:01:00.0: Detected a TMDS output
[   17.847675] [drm] nouveau 0000:01:00.0: DCB encoder 1 unknown
[   17.847677] [drm] nouveau 0000:01:00.0: Detected a DVI-I connector
[   17.847870] [drm] nouveau 0000:01:00.0: Detected a DVI-I connector
[   17.925176] psmouse serio1: ID: 10 00 64
[   18.131012] [drm] nouveau 0000:01:00.0: allocated 1920x1200 fb: 0x40250000, bo f3c03800
[   18.131146] fb0: nouveaufb frame buffer device
[   18.131147] registered panic notifier
[   18.131152] [drm] Initialized nouveau 0.0.15 20090420 for 0000:01:00.0 on minor 0
[   18.134131] vga16fb: initializing
[   18.134134] vga16fb: mapped to 0xc00a0000
[   18.134136] vga16fb: not registering due to another framebuffer present
[   18.141342] hda_intel: Disable MSI for Nvidia chipset
[   18.141364] HDA Intel 0000:00:10.1: setting latency timer to 64
[   18.426809] eth0: no link during initialization.
[   18.427239] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   18.429092] type=1505 audit(1285694400.730:5):  operation="profile_load" pid=704 name="/usr/share/gdm/guest-session/Xsession"
[   18.431283] type=1505 audit(1285694400.734:6):  operation="profile_replace" pid=705 name="/sbin/dhclient3"
[   18.431802] type=1505 audit(1285694400.734:7):  operation="profile_replace" pid=705 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[   18.432083] type=1505 audit(1285694400.734:8):  operation="profile_replace" pid=705 name="/usr/lib/connman/scripts/dhclient-script"
[   18.436265] type=1505 audit(1285694400.738:9):  operation="profile_load" pid=706 name="/usr/bin/evince"
[   18.451786] type=1505 audit(1285694400.754:10):  operation="profile_load" pid=706 name="/usr/bin/evince-previewer"
[   18.455923] type=1505 audit(1285694400.758:11):  operation="profile_load" pid=706 name="/usr/bin/evince-thumbnailer"
[   18.761437] NVRM: The NVIDIA probe routine was not called for 1 device(s).
[   18.761439] NVRM: This can occur when a driver such as rivafb, nvidiafb or
[   18.761440] NVRM: rivatv was loaded and obtained ownership of the NVIDIA
[   18.761441] NVRM: device(s).
[   18.761443] NVRM: Try unloading the rivafb, nvidiafb or rivatv kernel module
[   18.761444] NVRM: (and/or reconfigure your kernel without rivafb/nvidiafb
[   18.761445] NVRM: support), then try loading the NVIDIA kernel module again.
[   18.761447] NVRM: No NVIDIA graphics adapter probed!
[   18.778840] [drm] nouveau 0000:01:00.0: 0xB3B4: parsing output script 1
[   18.779072] [drm] nouveau 0000:01:00.0: 0xB3B5: parsing output script 2
[   18.779179] [drm] nouveau 0000:01:00.0: 0xB1FB: parsing clock script 0
[   18.786633] Console: switching to colour frame buffer device 240x75
[   18.799571] input: ImPS/2 Logitech Wheel Mouse as /devices/platform/i8042/serio1/input/input3
[   18.995929] ppdev: user-space parallel port driver
[   19.193789] hda_codec: ALC889A: BIOS auto-probing.
[   19.469879] CPU0 attaching NULL sched-domain.
[   19.469910] CPU0 attaching NULL sched-domain.
[   19.505764] input: HDA Digital PCBeep as /devices/pci0000:00/0000:00:10.1/input/input4
[   19.722015] [drm] nouveau 0000:01:00.0: Allocating FIFO number 2
[   19.725451] [drm] nouveau 0000:01:00.0: nouveau_channel_alloc: initialised FIFO 2
[   20.045668] usb 1-7: reset high speed USB device using ehci_hcd and address 2
[   20.260081] ndiswrapper: driver zd1211bu (Atheros,04/09/2008, 1.7.3.21) loaded
[   20.670416] wlan0: ethernet device 00:13:f7:e5:83:e0 using NDIS driver: zd1211bu, version: 0x1070315, NDIS version: 0x501, vendor: 'Atheros AR5007UG Wireless Network Adapter', 083A:4505.F.conf
[   20.677615] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2PSK; AES/CCMP with WPA, WPA2, WPA2PSK
[   20.677737] usbcore: registered new interface driver ndiswrapper
[   20.693523] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   22.878146] CPU0 attaching NULL sched-domain.
[   22.878180] CPU0 attaching NULL sched-domain.
[   49.458031] ndiswrapper (iw_set_auth:1602): invalid cmd 12
[   49.516869] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   49.839572] wlan0: IPv6 duplicate address fe80::213:f7ff:fee5:83e0 detected!
edward78@edward78-desktop:~$ 


> **7h3d4rk0n3 said:**
> Try turning off Compiz/Desktop effects. 
To do so navigate to:
System >> Preferences >> Appearance

Let me know if this helps at all.

No effects are on.

---

### Post by 7h3d4rk0n3 on 2010-09-28
Does it seem to lock up when you do any particular tasks?

---

### Post by edward1978 on 2010-09-28
> **7h3d4rk0n3 said:**
> Does it seem to lock up when you do any particular tasks?

No, I am always in firefox when it happens. I use Linux to mostly surf, so, I am in firefox 99.999% of the time. I switched mice with my dad to see if that is it. He has Ubuntu also so if that is the cause, I think he should start freezing.

---

### Post by TeoBigusGeekus on 2010-09-28
> **edward1978 said:**
> No, I am always in firefox when it happens. I use Linux to mostly surf, so, I am in firefox 99.999% of the time. I switched mice with my dad to see if that is it. He has Ubuntu also so if that is the cause, I think he should start freezing.
When you're using firefox, do you visit sites with a lot of flash?
Next time you're browsing, open a terminal and run top (or even better htop) to see cpu and ram usage.

---

### Post by Dustin2128 on 2010-09-28
lubuntu is still a little buggy, does it freeze with gnome or kde? Other than that, I'd suspect flash might be the culprit.

---

### Post by edward1978 on 2010-09-28
> **TeoBigusGeekus said:**
> When you're using firefox, do you visit sites with a lot of flash?
Next time you're browsing, open a terminal and run top (or even better htop) to see cpu and ram usage.

No, just youtube & that isn't that much. It will freeze on me with out any flash on the page also.

---

### Post by dirty_harry on 2010-09-28
> [    0.192017] EISA: Probing bus 0 at eisa.0
[    0.192099] EISA: Detected 0 cards.Hm, interesting... EISA loaded but no cards available.
 


> [   17.456233] Linux agpgart interface v0.103
[   17.506250] [drm] Initialized drm 1.1.0 20060810

[   17.559926] [drm] nouveau 0000:01:00.0: Detected an NV50 generation card (0x092000a2)
[   17.560427] [drm] nouveau 0000:01:00.0: Attempting to load BIOS image from PRAMIN
[   17.614453] [drm] nouveau 0000:01:00.0: ... appears to be valid
[   17.614456] [drm] nouveau 0000:01:00.0: BIT BIOS found
[   17.614458] [drm] nouveau 0000:01:00.0: Bios version 62.92.25.00
[   17.614460] [drm] nouveau 0000:01:00.0: TMDS table revision 2.0 not currently supported
[   17.614463] [drm] nouveau 0000:01:00.0: Found Display Configuration Block version 4.0
[   17.614465] [drm] nouveau 0000:01:00.0: DCB connector table: VHER 0x40 5 16 4
[   17.614468] [drm] nouveau 0000:01:00.0:   0: 0x00001030: type 0x30 idx 0 tag 0x07
[   17.614470] [drm] nouveau 0000:01:00.0:   1: 0x00002130: type 0x30 idx 1 tag 0x08
[   17.614472] [drm] nouveau 0000:01:00.0:   2: 0x00000210: type 0x10 idx 2 tag 0xff
[   17.614474] [drm] nouveau 0000:01:00.0:   3: 0x00000211: type 0x11 idx 2 tag 0xff
[   17.614476] [drm] nouveau 0000:01:00.0:   4: 0x00000213: type 0x13 idx 2 tag 0xff
[   17.614479] [drm] nouveau 0000:01:00.0: Raw DCB entry 0: 02000300 00000028
[   17.614481] [drm] nouveau 0000:01:00.0: Raw DCB entry 1: 01000302 00000030
[   17.614483] [drm] nouveau 0000:01:00.0: Raw DCB entry 2: 04011310 00000028
[   17.614485] [drm] nouveau 0000:01:00.0: Raw DCB entry 3: 02011312 00000030
[   17.614487] [drm] nouveau 0000:01:00.0: Raw DCB entry 4: 010223f1 00c0c080
[   17.614492] [drm] nouveau 0000:01:00.0: Parsing VBIOS init table 0 at offset 0xC17F
[   17.697848] [drm] nouveau 0000:01:00.0: Parsing VBIOS init table 1 at offset 0xC530
[   17.713664] [drm] nouveau 0000:01:00.0: Parsing VBIOS init table 2 at offset 0xD2AB
[   17.713672] [drm] nouveau 0000:01:00.0: Parsing VBIOS init table 3 at offset 0xD3CD
[   17.721732] [drm] nouveau 0000:01:00.0: Parsing VBIOS init table 4 at offset 0xD5FD
[   17.721735] [drm] nouveau 0000:01:00.0: Parsing VBIOS init table at offset 0xD662
[   17.745664] [drm] nouveau 0000:01:00.0: 0xD662: Condition still not met after 20ms, skipping following opcodes
[   17.745671] [drm] nouveau 0000:01:00.0: 0xB3B0: parsing output script 0
[   17.745675] [drm] nouveau 0000:01:00.0: 0xB3B0: parsing output script 0
[   17.745677] [drm] nouveau 0000:01:00.0: 0x9FAE: parsing output script 0
[   17.827874] [drm] nouveau 0000:01:00.0: 512 MiB VRAM
[   17.842260] [drm] nouveau 0000:01:00.0: 512 MiB GART (aperture)
[   17.843764] [drm] nouveau 0000:01:00.0: Allocating FIFO number 1
[   17.847270] [drm] nouveau 0000:01:00.0: nouveau_channel_alloc: initialised FIFO 1
[   17.847666] [drm] nouveau 0000:01:00.0: Detected a DAC output
[   17.847669] [drm] nouveau 0000:01:00.0: Detected a TMDS output
[   17.847671] [drm] nouveau 0000:01:00.0: Detected a DAC output
[   17.847673] [drm] nouveau 0000:01:00.0: Detected a TMDS output
[   17.847675] [drm] nouveau 0000:01:00.0: DCB encoder 1 unknown
[   17.847677] [drm] nouveau 0000:01:00.0: Detected a DVI-I connector
[   17.847870] [drm] nouveau 0000:01:00.0: Detected a DVI-I connector
[   18.131012] [drm] nouveau 0000:01:00.0: allocated 1920x1200 fb: 0x40250000, bo f3c03800

[   18.141342] hda_intel: Disable MSI for Nvidia chipset
[   18.141364] HDA Intel 0000:00:10.1: setting latency timer to 64

[   18.761437] NVRM: The NVIDIA probe routine was not called for 1 device(s).
[   18.761439] NVRM: This can occur when a driver such as rivafb, nvidiafb or
[   18.761440] NVRM: rivatv was loaded and obtained ownership of the NVIDIA
[   18.761441] NVRM: device(s).
[   18.761443] NVRM: Try unloading the rivafb, nvidiafb or rivatv kernel module
[   18.761444] NVRM: (and/or reconfigure your kernel without rivafb/nvidiafb
[   18.761445] NVRM: support), then try loading the NVIDIA kernel module again.
[   18.761447] NVRM: No NVIDIA graphics adapter probed!

[   18.778840] [drm] nouveau 0000:01:00.0: 0xB3B4: parsing output script 1
[   18.779072] [drm] nouveau 0000:01:00.0: 0xB3B5: parsing output script 2
[   18.779179] [drm] nouveau 0000:01:00.0: 0xB1FB: parsing clock script 0
[   19.722015] [drm] nouveau 0000:01:00.0: Allocating FIFO number 2
[   19.725451] [drm] nouveau 0000:01:00.0: nouveau_channel_alloc: initialised FIFO 2Do you have a nvidia chipset?
wow, nouveau supports nvidia too. I didn't know that. 
But wouldn't it be better to uninstall one of them? NVRM or nouveau...

-> [http://nouveau.freedesktop.org/wiki/UbuntuPackages](http://nouveau.freedesktop.org/wiki/UbuntuPackages)
-> [https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)

your xorg.0.log would be interesting...

If I guessed anything wrong please correct me!

---

### Post by edward1978 on 2010-09-28
Yep, I have a Nvidia chip set


X.Org X Server 1.7.6
Release Date: 2010-03-17
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-27-server i686 Ubuntu
Current Operating System: Linux edward78-desktop 2.6.32-24-generic-pae #43-Ubuntu SMP Thu Sep 16 15:30:27 UTC 2010 i686
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.32-24-generic-pae root=UUID=802764df-10f3-4aea-acee-ccc4884ca197 ro noapic nolapic acpi=off
Build Date: 21 July 2010  12:47:34PM
xorg-server 2:1.7.6-2ubuntu7.3 (For technical support please see [http://www.ubuntu.com/support](http://www.ubuntu.com/support)) 
Current version of pixman: 0.16.4
    Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
    to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Tue Sep 28 13:20:01 2010
(==) Using config directory: "/usr/lib/X11/xorg.conf.d"
(==) No Layout section.  Using the first Screen section.
(==) No screen section available. Using defaults.
(**) |-->Screen "Default Screen Section" (0)
(**) |   |-->Monitor "<default monitor>"
(==) No monitor specified for screen "Default Screen Section".
    Using a default monitor configuration.
(==) Automatically adding devices
(==) Automatically enabling devices
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
    Entry deleted from font path.
(==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/100dpi/:unscaled,
    /usr/share/fonts/X11/75dpi/:unscaled,
    /usr/share/fonts/X11/Type1,
    /usr/share/fonts/X11/100dpi,
    /usr/share/fonts/X11/75dpi,
    /var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
    built-ins
(==) ModulePath set to "/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
(II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
(II) Loader magic: 0x81f0e80
(II) Module ABI versions:
    X.Org ANSI C Emulation: 0.4
    X.Org Video Driver: 6.0
    X.Org XInput driver : 7.0
    X.Org Server Extension : 2.0
(++) using VT number 7

(--) PCI:*(0:1:0:0) 10de:0600:1043:8268 nVidia Corporation G92 [GeForce 8800 GTS 512] rev 162, Mem @ 0xcc000000/16777216, 0xb0000000/268435456, 0xca000000/33554432, I/O @ 0x0000bc00/128, BIOS @ 0x????????/131072
(II) Open ACPI successful (/var/run/acpid.socket)
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.0.0
    Module class: X.Org Server Extension
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension MIT-SCREEN-SAVER
(II) Loading extension XFree86-VidModeExtension
(II) Loading extension XFree86-DGA
(II) Loading extension DPMS
(II) Loading extension XVideo
(II) Loading extension XVideo-MotionCompensation
(II) Loading extension X-Resource
(II) LoadModule: "dbe"
(II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.0.0
    Module class: X.Org Server Extension
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions/libglx.so
(II) Module glx: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.0.0
    ABI class: X.Org Server Extension, version 2.0
(==) AIGLX enabled
(II) Loading extension GLX
(II) LoadModule: "record"
(II) Loading /usr/lib/xorg/modules/extensions/librecord.so
(II) Module record: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.13.0
    Module class: X.Org Server Extension
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension RECORD
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions/libdri.so
(II) Module dri: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.0.0
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension XFree86-DRI
(II) LoadModule: "dri2"
(II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
(II) Module dri2: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.1.0
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DRI2
(==) Matched nouveau as autoconfigured driver 0
(==) Matched nv as autoconfigured driver 1
(==) Matched vesa as autoconfigured driver 2
(==) Matched fbdev as autoconfigured driver 3
(==) Assigned the driver to the xf86ConfigLayout
(II) LoadModule: "nouveau"
(II) Loading /usr/lib/xorg/modules/drivers/nouveau_drv.so
(II) Module nouveau: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 0.0.15
    Module class: X.Org Video Driver
    ABI class: X.Org Video Driver, version 6.0
(II) LoadModule: "nv"
(II) Loading /usr/lib/xorg/modules/drivers/nv_drv.so
(II) Module nv: vendor="X.Org Foundation"
    compiled for 1.7.3.901, module version = 2.1.15
    Module class: X.Org Video Driver
    ABI class: X.Org Video Driver, version 6.0
(II) LoadModule: "vesa"
(II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
(II) Module vesa: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 2.3.0
    Module class: X.Org Video Driver
    ABI class: X.Org Video Driver, version 6.0
(II) LoadModule: "fbdev"
(II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
(II) Module fbdev: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 0.4.1
    ABI class: X.Org Video Driver, version 6.0
(II) NOUVEAU driver Date:   Wed Feb 10 18:43:39 2010 +0100
(II) NOUVEAU driver for NVIDIA chipset families :
    RIVA TNT    (NV04)
    RIVA TNT2   (NV05)
    GeForce 256 (NV10)
    GeForce 2   (NV11, NV15)
    GeForce 4MX (NV17, NV18)
    GeForce 3   (NV20)
    GeForce 4Ti (NV25, NV28)
    GeForce FX  (NV3x)
    GeForce 6   (NV4x)
    GeForce 7   (G7x)
    GeForce 8   (G8x)
(II) NOUVEAU driver Date:   Wed Feb 10 18:43:39 2010 +0100
(II) NOUVEAU driver for NVIDIA chipset families :
    RIVA TNT    (NV04)
    RIVA TNT2   (NV05)
    GeForce 256 (NV10)
    GeForce 2   (NV11, NV15)
    GeForce 4MX (NV17, NV18)
    GeForce 3   (NV20)
    GeForce 4Ti (NV25, NV28)
    GeForce FX  (NV3x)
    GeForce 6   (NV4x)
    GeForce 7   (G7x)
    GeForce 8   (G8x)
(II) VESA: driver for VESA chipsets: vesa
(II) FBDEV: driver for framebuffer: fbdev
(II) Primary Device is: PCI 01@00:00:0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 8, (OK)
drmOpenByBusid: Searching for BusID pci:0000:01:00.0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 8, (OK)
drmOpenByBusid: drmOpenMinor returns 8
drmOpenByBusid: drmGetBusid reports pci:0000:01:00.0
(II) [drm] nouveau interface version: 0.0.15
(WW) Falling back to old probe method for vesa
(WW) Falling back to old probe method for fbdev
(II) Loading sub module "fbdevhw"
(II) LoadModule: "fbdevhw"
(II) Loading /usr/lib/xorg/modules/linux/libfbdevhw.so
(II) Module fbdevhw: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 0.0.2
    ABI class: X.Org Video Driver, version 6.0
(II) Loading sub module "dri"
(II) LoadModule: "dri"
(II) Reloading /usr/lib/xorg/modules/extensions/libdri.so
(II) NOUVEAU(0): Loaded DRI module
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 9, (OK)
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 9, (OK)
drmOpenByBusid: Searching for BusID pci:0000:01:00.0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 9, (OK)
drmOpenByBusid: drmOpenMinor returns 9
drmOpenByBusid: drmGetBusid reports pci:0000:01:00.0
(II) [drm] DRM interface version 1.3
(II) [drm] DRM open master succeeded.
(--) NOUVEAU(0): Chipset: "NVIDIA NV92"
(II) NOUVEAU(0): Creating default Display subsection in Screen section
    "Default Screen Section" for depth/fbbpp 24/32
(==) NOUVEAU(0): Depth 24, (--) framebuffer bpp 32
(==) NOUVEAU(0): RGB weight 888
(==) NOUVEAU(0): Default visual is TrueColor
(==) NOUVEAU(0): Using HW cursor
(II) NOUVEAU(0): Output DVI-I-1 has no monitor section
(II) NOUVEAU(0): Output DVI-I-2 has no monitor section
(II) NOUVEAU(0): EDID for output DVI-I-1
(II) NOUVEAU(0): Manufacturer: SAM  Model: 467  Serial#: 1129132596
(II) NOUVEAU(0): Year: 2008  Week: 35
(II) NOUVEAU(0): EDID Version: 1.3
(II) NOUVEAU(0): Digital Display Input
(II) NOUVEAU(0): Max Image Size [cm]: horiz.: 52  vert.: 32
(II) NOUVEAU(0): Gamma: 2.20
(II) NOUVEAU(0): DPMS capabilities: Off
(II) NOUVEAU(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) NOUVEAU(0): First detailed timing is preferred mode
(II) NOUVEAU(0): redX: 0.650 redY: 0.337   greenX: 0.296 greenY: 0.604
(II) NOUVEAU(0): blueX: 0.147 blueY: 0.074   whiteX: 0.312 whiteY: 0.329
(II) NOUVEAU(0): Supported established timings:
(II) NOUVEAU(0): 720x400@70Hz
(II) NOUVEAU(0): 640x480@60Hz
(II) NOUVEAU(0): 640x480@67Hz
(II) NOUVEAU(0): 640x480@72Hz
(II) NOUVEAU(0): 640x480@75Hz
(II) NOUVEAU(0): 800x600@56Hz
(II) NOUVEAU(0): 800x600@60Hz
(II) NOUVEAU(0): 800x600@72Hz
(II) NOUVEAU(0): 800x600@75Hz
(II) NOUVEAU(0): 832x624@75Hz
(II) NOUVEAU(0): 1024x768@60Hz
(II) NOUVEAU(0): 1024x768@70Hz
(II) NOUVEAU(0): 1024x768@75Hz
(II) NOUVEAU(0): 1280x1024@75Hz
(II) NOUVEAU(0): 1152x864@75Hz
(II) NOUVEAU(0): Manufacturer's mask: 0
(II) NOUVEAU(0): Supported standard timings:
(II) NOUVEAU(0): #0: hsize: 1600  vsize 1200  refresh: 60  vid: 16553
(II) NOUVEAU(0): #1: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) NOUVEAU(0): #2: hsize: 1280  vsize 960  refresh: 60  vid: 16513
(II) NOUVEAU(0): #3: hsize: 1152  vsize 864  refresh: 75  vid: 20337
(II) NOUVEAU(0): Supported detailed timing:
(II) NOUVEAU(0): clock: 154.0 MHz   Image Size:  518 x 324 mm
(II) NOUVEAU(0): h_active: 1920  h_sync: 1968  h_sync_end 2000 h_blank_end 2080 h_border: 0
(II) NOUVEAU(0): v_active: 1200  v_sync: 1203  v_sync_end 1209 v_blanking: 1235 v_border: 0
(II) NOUVEAU(0): Ranges: V min: 56 V max: 75 Hz, H min: 30 H max: 81 kHz, PixClock max 170 MHz
(II) NOUVEAU(0): Monitor name: SyncMaster
(II) NOUVEAU(0): Serial No: H9NQ806893
(II) NOUVEAU(0): EDID (in hex):
(II) NOUVEAU(0):     00ffffffffffff004c2d670434324d43
(II) NOUVEAU(0):     23120103803420782a9fc1a6564b9a25
(II) NOUVEAU(0):     135054bfef80a94081808140714f0101
(II) NOUVEAU(0):     010101010101283c80a070b023403020
(II) NOUVEAU(0):     360006442100001a000000fd00384b1e
(II) NOUVEAU(0):     5111000a202020202020000000fc0053
(II) NOUVEAU(0):     796e634d61737465720a2020000000ff
(II) NOUVEAU(0):     0048394e513830363839330a202000e9
(II) NOUVEAU(0): EDID vendor "SAM", prod id 1127
(II) NOUVEAU(0): Using EDID range info for horizontal sync
(II) NOUVEAU(0): Using EDID range info for vertical refresh
(II) NOUVEAU(0): Printing DDC gathered Modelines:
(II) NOUVEAU(0): Modeline "1920x1200"x0.0  154.00  1920 1968 2000 2080  1200 1203 1209 1235 +hsync -vsync (74.0 kHz)
(II) NOUVEAU(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) NOUVEAU(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) NOUVEAU(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) NOUVEAU(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
(II) NOUVEAU(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
(II) NOUVEAU(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) NOUVEAU(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) NOUVEAU(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(II) NOUVEAU(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(II) NOUVEAU(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) NOUVEAU(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) NOUVEAU(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(II) NOUVEAU(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) NOUVEAU(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(II) NOUVEAU(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
(II) NOUVEAU(0): Modeline "1600x1200"x0.0  162.00  1600 1664 1856 2160  1200 1201 1204 1250 +hsync +vsync (75.0 kHz)
(II) NOUVEAU(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
(II) NOUVEAU(0): Modeline "1280x960"x0.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz)
(II) NOUVEAU(0): Printing probed modes for output DVI-I-1
(II) NOUVEAU(0): Modeline "1920x1200"x60.0  154.00  1920 1968 2000 2080  1200 1203 1209 1235 +hsync -vsync (74.0 kHz)
(II) NOUVEAU(0): Modeline "1600x1200"x60.0  162.00  1600 1664 1856 2160  1200 1201 1204 1250 +hsync +vsync (75.0 kHz)
(II) NOUVEAU(0): Modeline "1280x1024"x75.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(II) NOUVEAU(0): Modeline "1280x1024"x60.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
(II) NOUVEAU(0): Modeline "1280x960"x60.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz)
(II) NOUVEAU(0): Modeline "1152x864"x75.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
(II) NOUVEAU(0): Modeline "1024x768"x75.1   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.1 kHz)
(II) NOUVEAU(0): Modeline "1024x768"x70.1   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) NOUVEAU(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) NOUVEAU(0): Modeline "832x624"x74.6   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(II) NOUVEAU(0): Modeline "800x600"x72.2   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(II) NOUVEAU(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) NOUVEAU(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) NOUVEAU(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) NOUVEAU(0): Modeline "640x480"x72.8   31.50  640 664 704 832  480 489 491 520 -hsync -vsync (37.9 kHz)
(II) NOUVEAU(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) NOUVEAU(0): Modeline "640x480"x66.7   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
(II) NOUVEAU(0): Modeline "640x480"x60.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) NOUVEAU(0): Modeline "720x400"x70.1   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) NOUVEAU(0): EDID for output DVI-I-2
(II) NOUVEAU(0): Output DVI-I-1 connected
(II) NOUVEAU(0): Output DVI-I-2 disconnected
(II) NOUVEAU(0): Using exact sizes for initial modes
(II) NOUVEAU(0): Output DVI-I-1 using initial mode 1920x1200
(II) NOUVEAU(0): Using default gamma of (1.0, 1.0, 1.0) unless otherwise stated.
(--) NOUVEAU(0): Virtual size is 1920x1200 (pitch 1920)
(**) NOUVEAU(0):  Driver mode "1920x1200": 154.0 MHz (scaled from 0.0 MHz), 74.0 kHz, 60.0 Hz
(II) NOUVEAU(0): Modeline "1920x1200"x60.0  154.00  1920 1968 2000 2080  1200 1203 1209 1235 +hsync -vsync (74.0 kHz)
(**) NOUVEAU(0):  Driver mode "1600x1200": 162.0 MHz (scaled from 0.0 MHz), 75.0 kHz, 60.0 Hz
(II) NOUVEAU(0): Modeline "1600x1200"x60.0  162.00  1600 1664 1856 2160  1200 1201 1204 1250 +hsync +vsync (75.0 kHz)
(**) NOUVEAU(0):  Driver mode "1280x1024": 135.0 MHz (scaled from 0.0 MHz), 80.0 kHz, 75.0 Hz
(II) NOUVEAU(0): Modeline "1280x1024"x75.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(**) NOUVEAU(0):  Driver mode "1280x1024": 108.0 MHz (scaled from 0.0 MHz), 64.0 kHz, 60.0 Hz
(II) NOUVEAU(0): Modeline "1280x1024"x60.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
(**) NOUVEAU(0):  Driver mode "1280x960": 108.0 MHz (scaled from 0.0 MHz), 60.0 kHz, 60.0 Hz
(II) NOUVEAU(0): Modeline "1280x960"x60.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz)
(**) NOUVEAU(0):  Driver mode "1152x864": 108.0 MHz (scaled from 0.0 MHz), 67.5 kHz, 75.0 Hz
(II) NOUVEAU(0): Modeline "1152x864"x75.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
(**) NOUVEAU(0):  Driver mode "1024x768": 78.8 MHz (scaled from 0.0 MHz), 60.1 kHz, 75.1 Hz
(II) NOUVEAU(0): Modeline "1024x768"x75.1   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.1 kHz)
(**) NOUVEAU(0):  Driver mode "1024x768": 75.0 MHz (scaled from 0.0 MHz), 56.5 kHz, 70.1 Hz
(II) NOUVEAU(0): Modeline "1024x768"x70.1   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(**) NOUVEAU(0):  Driver mode "1024x768": 65.0 MHz (scaled from 0.0 MHz), 48.4 kHz, 60.0 Hz
(II) NOUVEAU(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(**) NOUVEAU(0):  Driver mode "832x624": 57.3 MHz (scaled from 0.0 MHz), 49.7 kHz, 74.6 Hz
(II) NOUVEAU(0): Modeline "832x624"x74.6   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(**) NOUVEAU(0):  Driver mode "800x600": 50.0 MHz (scaled from 0.0 MHz), 48.1 kHz, 72.2 Hz
(II) NOUVEAU(0): Modeline "800x600"x72.2   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(**) NOUVEAU(0):  Driver mode "800x600": 49.5 MHz (scaled from 0.0 MHz), 46.9 kHz, 75.0 Hz
(II) NOUVEAU(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(**) NOUVEAU(0):  Driver mode "800x600": 40.0 MHz (scaled from 0.0 MHz), 37.9 kHz, 60.3 Hz
(II) NOUVEAU(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(**) NOUVEAU(0):  Driver mode "800x600": 36.0 MHz (scaled from 0.0 MHz), 35.2 kHz, 56.2 Hz
(II) NOUVEAU(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(**) NOUVEAU(0):  Driver mode "640x480": 31.5 MHz (scaled from 0.0 MHz), 37.9 kHz, 72.8 Hz
(II) NOUVEAU(0): Modeline "640x480"x72.8   31.50  640 664 704 832  480 489 491 520 -hsync -vsync (37.9 kHz)
(**) NOUVEAU(0):  Driver mode "640x480": 31.5 MHz (scaled from 0.0 MHz), 37.5 kHz, 75.0 Hz
(II) NOUVEAU(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(**) NOUVEAU(0):  Driver mode "640x480": 30.2 MHz (scaled from 0.0 MHz), 35.0 kHz, 66.7 Hz
(II) NOUVEAU(0): Modeline "640x480"x66.7   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
(**) NOUVEAU(0):  Driver mode "640x480": 25.2 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz
(II) NOUVEAU(0): Modeline "640x480"x60.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(**) NOUVEAU(0):  Driver mode "720x400": 28.3 MHz (scaled from 0.0 MHz), 31.5 kHz, 70.1 Hz
(II) NOUVEAU(0): Modeline "720x400"x70.1   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(**) NOUVEAU(0): Display dimensions: (520, 320) mm
(**) NOUVEAU(0): DPI set to (93, 95)
(II) Loading sub module "wfb"
(II) LoadModule: "wfb"
(II) Loading /usr/lib/xorg/modules/libwfb.so
(II) Module wfb: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.0.0
    ABI class: X.Org ANSI C Emulation, version 0.4
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules/libfb.so
(II) Module fb: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.0.0
    ABI class: X.Org ANSI C Emulation, version 0.4
(II) Loading sub module "exa"
(II) LoadModule: "exa"
(II) Loading /usr/lib/xorg/modules/libexa.so
(II) Module exa: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 2.5.0
    ABI class: X.Org Video Driver, version 6.0
(II) Loading sub module "shadowfb"
(II) LoadModule: "shadowfb"
(II) Loading /usr/lib/xorg/modules/libshadowfb.so
(II) Module shadowfb: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.0.0
    ABI class: X.Org ANSI C Emulation, version 0.4
(II) UnloadModule: "nv"
(II) Unloading /usr/lib/xorg/modules/drivers/nv_drv.so
(II) UnloadModule: "vesa"
(II) Unloading /usr/lib/xorg/modules/drivers/vesa_drv.so
(II) UnloadModule: "fbdev"
(II) Unloading /usr/lib/xorg/modules/drivers/fbdev_drv.so
(II) UnloadModule: "fbdevhw"
(II) Unloading /usr/lib/xorg/modules/linux/libfbdevhw.so
(--) Depth 24 pixmap format is 32 bpp
(II) NOUVEAU(0): Opened GPU channel 2
(II) NOUVEAU(0): [DRI2] Setup complete
(II) NOUVEAU(0): GART: 512MiB available
(II) NOUVEAU(0): GART: Allocated 16MiB as a scratch buffer
(II) EXA(0): Driver allocated offscreen pixmaps
(II) EXA(0): Driver registered support for the following operations:
(II)         Solid
(II)         Copy
(II)         Composite (RENDER acceleration)
(II)         UploadToScreen
(II)         DownloadFromScreen
(==) NOUVEAU(0): Backing store disabled
(==) NOUVEAU(0): Silken mouse enabled
(II) NOUVEAU(0): [XvMC] Associated with Nouveau GeForce 8/9 Textured Video.
(II) NOUVEAU(0): [XvMC] Extension initialized.
(II) NOUVEAU(0): NVEnterVT is called.
(==) NOUVEAU(0): DPMS enabled
(II) NOUVEAU(0): RandR 1.2 enabled, ignore the following RandR disabled message.
(--) RandR disabled
(II) Initializing built-in extension Generic Event Extension
(II) Initializing built-in extension SHAPE
(II) Initializing built-in extension MIT-SHM
(II) Initializing built-in extension XInputExtension
(II) Initializing built-in extension XTEST
(II) Initializing built-in extension BIG-REQUESTS
(II) Initializing built-in extension SYNC
(II) Initializing built-in extension XKEYBOARD
(II) Initializing built-in extension XC-MISC
(II) Initializing built-in extension SECURITY
(II) Initializing built-in extension XINERAMA
(II) Initializing built-in extension XFIXES
(II) Initializing built-in extension RENDER
(II) Initializing built-in extension RANDR
(II) Initializing built-in extension COMPOSITE
(II) Initializing built-in extension DAMAGE
(II) AIGLX error: dlopen of /usr/lib/dri/nouveau_dri.so failed (/usr/lib/dri/nouveau_dri.so: cannot open shared object file: No such file or directory)
(II) AIGLX: reverting to software rendering
(II) AIGLX: Screen 0 is not DRI capable
(II) AIGLX: Loaded and initialized /usr/lib/dri/swrast_dri.so
(II) GLX: Initialized DRISWRAST GL provider for screen 0
(II) NOUVEAU(0): Setting screen physical size to 507 x 317
resize called 1920 1200
(II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
(II) config/udev: Adding input device Logitech Logitech Dual Action (/dev/input/event2)
(II) No input driver/identifier specified (ignoring)
(II) config/udev: Adding input device Logitech Logitech Dual Action (/dev/input/js0)
(II) No input driver/identifier specified (ignoring)
(II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event1)
(**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
(II) LoadModule: "evdev"
(II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
(II) Module evdev: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 2.3.2
    Module class: X.Org XInput Driver
    ABI class: X.Org XInput driver, version 7.0
(**) AT Translated Set 2 keyboard: always reports core events
(**) AT Translated Set 2 keyboard: Device: "/dev/input/event1"
(II) AT Translated Set 2 keyboard: Found keys
(II) AT Translated Set 2 keyboard: Configuring as keyboard
(II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(II) config/udev: Adding input device ImPS/2 Logitech Wheel Mouse (/dev/input/event3)
(**) ImPS/2 Logitech Wheel Mouse: Applying InputClass "evdev pointer catchall"
(**) ImPS/2 Logitech Wheel Mouse: always reports core events
(**) ImPS/2 Logitech Wheel Mouse: Device: "/dev/input/event3"
(II) ImPS/2 Logitech Wheel Mouse: Found 3 mouse buttons
(II) ImPS/2 Logitech Wheel Mouse: Found scroll wheel(s)
(II) ImPS/2 Logitech Wheel Mouse: Found relative axes
(II) ImPS/2 Logitech Wheel Mouse: Found x and y relative axes
(II) ImPS/2 Logitech Wheel Mouse: Configuring as mouse
(**) ImPS/2 Logitech Wheel Mouse: YAxisMapping: buttons 4 and 5
(**) ImPS/2 Logitech Wheel Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "ImPS/2 Logitech Wheel Mouse" (type: MOUSE)
(II) ImPS/2 Logitech Wheel Mouse: initialized for relative axes.
(II) config/udev: Adding input device ImPS/2 Logitech Wheel Mouse (/dev/input/mouse1)
(II) No input driver/identifier specified (ignoring)
(II) config/udev: Adding input device Macintosh mouse button emulation (/dev/input/event0)
(**) Macintosh mouse button emulation: Applying InputClass "evdev pointer catchall"
(**) Macintosh mouse button emulation: always reports core events
(**) Macintosh mouse button emulation: Device: "/dev/input/event0"
(II) Macintosh mouse button emulation: Found 3 mouse buttons
(II) Macintosh mouse button emulation: Found relative axes
(II) Macintosh mouse button emulation: Found x and y relative axes
(II) Macintosh mouse button emulation: Configuring as mouse
(**) Macintosh mouse button emulation: YAxisMapping: buttons 4 and 5
(**) Macintosh mouse button emulation: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "Macintosh mouse button emulation" (type: MOUSE)
(II) Macintosh mouse button emulation: initialized for relative axes.
(II) config/udev: Adding input device Macintosh mouse button emulation (/dev/input/mouse0)
(II) No input driver/identifier specified (ignoring)
(II) config/udev: Adding input device HDA Digital PCBeep (/dev/input/event4)
(II) No input driver/identifier specified (ignoring)
(II) NOUVEAU(0): EDID vendor "SAM", prod id 1127
(II) NOUVEAU(0): Using hsync ranges from config file
(II) NOUVEAU(0): Using vrefresh ranges from config file
(II) NOUVEAU(0): Printing DDC gathered Modelines:
(II) NOUVEAU(0): Modeline "1920x1200"x0.0  154.00  1920 1968 2000 2080  1200 1203 1209 1235 +hsync -vsync (74.0 kHz)
(II) NOUVEAU(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) NOUVEAU(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) NOUVEAU(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) NOUVEAU(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
(II) NOUVEAU(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
(II) NOUVEAU(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) NOUVEAU(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) NOUVEAU(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(II) NOUVEAU(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(II) NOUVEAU(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) NOUVEAU(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) NOUVEAU(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(II) NOUVEAU(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) NOUVEAU(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(II) NOUVEAU(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
(II) NOUVEAU(0): Modeline "1600x1200"x0.0  162.00  1600 1664 1856 2160  1200 1201 1204 1250 +hsync +vsync (75.0 kHz)
(II) NOUVEAU(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
(II) NOUVEAU(0): Modeline "1280x960"x0.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz)
(II) NOUVEAU(0): EDID vendor "SAM", prod id 1127
(II) NOUVEAU(0): Using hsync ranges from config file
(II) NOUVEAU(0): Using vrefresh ranges from config file
(II) NOUVEAU(0): Printing DDC gathered Modelines:
(II) NOUVEAU(0): Modeline "1920x1200"x0.0  154.00  1920 1968 2000 2080  1200 1203 1209 1235 +hsync -vsync (74.0 kHz)
(II) NOUVEAU(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) NOUVEAU(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) NOUVEAU(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) NOUVEAU(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
(II) NOUVEAU(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
(II) NOUVEAU(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) NOUVEAU(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) NOUVEAU(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(II) NOUVEAU(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(II) NOUVEAU(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) NOUVEAU(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) NOUVEAU(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(II) NOUVEAU(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) NOUVEAU(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(II) NOUVEAU(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
(II) NOUVEAU(0): Modeline "1600x1200"x0.0  162.00  1600 1664 1856 2160  1200 1201 1204 1250 +hsync +vsync (75.0 kHz)
(II) NOUVEAU(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
(II) NOUVEAU(0): Modeline "1280x960"x0.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz)
(II) NOUVEAU(0): EDID vendor "SAM", prod id 1127
(II) NOUVEAU(0): Using hsync ranges from config file
(II) NOUVEAU(0): Using vrefresh ranges from config file
(II) NOUVEAU(0): Printing DDC gathered Modelines:
(II) NOUVEAU(0): Modeline "1920x1200"x0.0  154.00  1920 1968 2000 2080  1200 1203 1209 1235 +hsync -vsync (74.0 kHz)
(II) NOUVEAU(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) NOUVEAU(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) NOUVEAU(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) NOUVEAU(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
(II) NOUVEAU(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
(II) NOUVEAU(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) NOUVEAU(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) NOUVEAU(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(II) NOUVEAU(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(II) NOUVEAU(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) NOUVEAU(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) NOUVEAU(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(II) NOUVEAU(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) NOUVEAU(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(II) NOUVEAU(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
(II) NOUVEAU(0): Modeline "1600x1200"x0.0  162.00  1600 1664 1856 2160  1200 1201 1204 1250 +hsync +vsync (75.0 kHz)
(II) NOUVEAU(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
(II) NOUVEAU(0): Modeline "1280x960"x0.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz)
resize called 1280 960
(II) NOUVEAU(0): EDID vendor "SAM", prod id 1127
(II) NOUVEAU(0): Using hsync ranges from config file
(II) NOUVEAU(0): Using vrefresh ranges from config file
(II) NOUVEAU(0): Printing DDC gathered Modelines:
(II) NOUVEAU(0): Modeline "1920x1200"x0.0  154.00  1920 1968 2000 2080  1200 1203 1209 1235 +hsync -vsync (74.0 kHz)
(II) NOUVEAU(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) NOUVEAU(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) NOUVEAU(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) NOUVEAU(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
(II) NOUVEAU(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
(II) NOUVEAU(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) NOUVEAU(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) NOUVEAU(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(II) NOUVEAU(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(II) NOUVEAU(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) NOUVEAU(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) NOUVEAU(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(II) NOUVEAU(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) NOUVEAU(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(II) NOUVEAU(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
(II) NOUVEAU(0): Modeline "1600x1200"x0.0  162.00  1600 1664 1856 2160  1200 1201 1204 1250 +hsync +vsync (75.0 kHz)
(II) NOUVEAU(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
(II) NOUVEAU(0): Modeline "1280x960"x0.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz)
(II) NOUVEAU(0): EDID vendor "SAM", prod id 1127
(II) NOUVEAU(0): Using hsync ranges from config file
(II) NOUVEAU(0): Using vrefresh ranges from config file
(II) NOUVEAU(0): Printing DDC gathered Modelines:
(II) NOUVEAU(0): Modeline "1920x1200"x0.0  154.00  1920 1968 2000 2080  1200 1203 1209 1235 +hsync -vsync (74.0 kHz)
(II) NOUVEAU(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) NOUVEAU(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) NOUVEAU(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) NOUVEAU(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
(II) NOUVEAU(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
(II) NOUVEAU(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) NOUVEAU(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) NOUVEAU(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(II) NOUVEAU(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(II) NOUVEAU(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) NOUVEAU(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) NOUVEAU(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(II) NOUVEAU(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) NOUVEAU(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(II) NOUVEAU(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
(II) NOUVEAU(0): Modeline "1600x1200"x0.0  162.00  1600 1664 1856 2160  1200 1201 1204 1250 +hsync +vsync (75.0 kHz)
(II) NOUVEAU(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
(II) NOUVEAU(0): Modeline "1280x960"x0.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz)

I switched mice on last freeze with my dad I had a USB MS Intellimouse hooked up.

---

### Post by dirty_harry on 2010-09-28
> I switched mice on last freeze with my dad I had a USB MS Intellimouse hooked up.     If this solves your problem and you experience no more freezes it's fine, but then you should mark the thread as "SOLVED"?! Maybe it's best to do this tomorrow when you're sure that the hangups are gone.

The two MS products I'm using are a MS Intellimouse and a MS Natural Keyboard. I really like them :)
Maybe I will never be completely MS free... :(

---

### Post by edward1978 on 2010-09-28
> **dirty_harry said:**
> If this solves your problem and you experience no more freezes it's fine, but then you should mark the thread as "SOLVED"?! Maybe it's best to do this tomorrow when you're sure that the hangups are gone.

The two MS products I'm using are a MS Intellimouse and a MS Natural Keyboard. I really like them :)
Maybe I will never be completely MS free... :(


I will give it a week sometimes it can go for a few days & not freeze. Ya the Logitech mouse is limited. :) Someone said it might be flash, but only flash sites would freeze it then right, plus only the browser would freeze I would think?

---

### Post by 7h3d4rk0n3 on 2010-09-28
I have a Logitech mouse, and I have no freezing issues.

---

### Post by edward1978 on 2010-09-29
> **7h3d4rk0n3 said:**
> I have a Logitech mouse, and I have no freezing issues.

I am hoping it was the USB MS Intelimouse, my dad had the one I have now for around a year & no freezing issues in Ubuntu for him, but he did have 8.04 also.

---

### Post by 7h3d4rk0n3 on 2010-09-29
Wouldn't make sense that it would work in an older version, but not a newer version that has more hardware support, but I suppose it could happen. It could have been bad drivers even.

---

### Post by edward1978 on 2010-10-01
> **7h3d4rk0n3 said:**
> Wouldn't make sense that it would work in an older version, but not a newer version that has more hardware support, but I suppose it could happen. It could have been bad drivers even.

Well it froze for me in 8.04 to, just not for my dad, our systems are 99.999% the same well maybe a little lower. How can I get a list of every driver on the system?? It just froze again a few ago, so it is not the mouse, so might as well switch back to my USB MS Intelimouse. God this is annoying, at least it only happens rarely. It is not flash, it freezes on flash free sites also. Maybe it is a kernel bug...

---

### Post by davidvandoren on 2010-10-01
Are you running your Ubuntu on a sata drive?

I had pretty much the same warnings in the system log as you did.

Anyway I went to the pc dealer and got the same motherboard replaced. The I connected an old 30G hard-drive to the ide slot and installed Ubuntu on it. My DVD drive is a newer one though and Fedora 13 and 12 had a terrible error pretty much to the end of reading the files and Ubuntu 10.04 succeeded after four tries. 

The Ubuntu installation on this 30G hard-drive looks pretty stable.
Only one hick up when using the update-manager (crash while downloading)

I run the update manager again and the install went trough with two packages that could not be installed (dependency failure error blablabla)
sudo apt-get update
sudo apt-get upgrade 
error you might want to  
  [B] apt-get install -f
[/B]no open the update manager and the packages were there and could be installed with no problem 

Finally the NVDIA graphic card.

If you do have an old hard-drive disconnect the one you use now and install Ubuntu on there then reconnect this one and you can use the bios to choose the drive you want to boot.

---

### Post by edward1978 on 2010-10-01
> **davidvandoren said:**
> Are you running your Ubuntu on a sata drive?

I had pretty much the same warnings in the system log as you did.

Anyway I went to the pc dealer and got the same motherboard replaced. The I connected an old 30G hard-drive to the ide slot and installed Ubuntu on it. My DVD drive is a newer one though and Fedora 13 and 12 had a terrible error pretty much to the end of reading the files and Ubuntu 10.04 succeeded after four tries. 

The Ubuntu installation on this 30G hard-drive looks pretty stable.
Only one hick up when using the update-manager (crash while downloading)

I run the update manager again and the install went trough with two packages that could not be installed (dependency failure error blablabla)
sudo apt-get update
sudo apt-get upgrade 
error you might want to  
  [B] apt-get install -f
[/B]no open the update manager and the packages were there and could be installed with no problem 

Finally the NVDIA graphic card.

If you do have an old hard-drive disconnect the one you use now and install Ubuntu on there then reconnect this one and you can use the bios to choose the drive you want to boot.

A prob. with SATA drives, hmmm. Nope I don't have a IDE drive, my dad had 8.04 on a SATA drive for a year no freezes. I uninstalled nouveau, maybe that was it.  SATA drives are a few years old, they are not a new thing. How could they be a prob.?

---

### Post by smilingfrog on 2010-10-01
> **edward1978 said:**
> Well it froze for me in 8.04 to, just not for my dad, our systems are 99.999% the same well maybe a little lower. How can I get a list of every driver on the system?? It just froze again a few ago, so it is not the mouse, so might as well switch back to my USB MS Intelimouse. God this is annoying, at least it only happens rarely. It is not flash, it freezes on flash free sites also. Maybe it is a kernel bug...

I have a few questions:
1. Are you running 64 bit Ubuntu?
2. Are you running VirtualBox?
3. Do you have Flash installed?

I have been plagued with the same problem with crashing. Youtube *is* flash, as the player relies on it, and I cannot surf Youtube without crashing. Things got better when I uninstalled Flash completely, but it does hobble the fun of the machine. Adobe recently re-started 64 bit support, but I haven't noticed a difference to stability yet.

I have freezes in VirtualBox if I try to resize windows within the virtual machine.

I had no problems before upgrading to 64 bit, but I have 8GB now, and I want to use it.

Maybe try switching to 32 bit linux, and see if your problems are solved.

---

### Post by davidvandoren on 2010-10-01
I don't know but something goes wrong with the read write. Don't ask me what exactly and how. SATA drives are around for years. But your new cpu most likely isn't. In forums I always noticed my SATA here and my SATA there so when seeing the IDE connector on my mother board I thought why not and try out. 
I use Linux for more than five years now. As a user not programmer and never had problems like this on my first SATA drive.

Maybe they allow faster reading which can cause the trouble or maybe the slower reading of the old drive prevents trouble. What do I know/care. 
Works for me at least for now it seems like it.

---

### Post by davidvandoren on 2010-10-01
> **smilingfrog said:**
> I have a few questions:
1. Are you running 64 bit Ubuntu?
2. Are you running VirtualBox?
3. Do you have Flash installed?

I have been plagued with the same problem with crashing. Youtube *is* flash, as the player relies on it, and I cannot surf Youtube without crashing. Things got better when I uninstalled Flash completely, but it does hobble the fun of the machine. Adobe recently re-started 64 bit support, but I haven't noticed a difference to stability yet.

I have freezes in VirtualBox if I try to resize windows within the virtual machine.

I had no problems before upgrading to 64 bit, but I have 8GB now, and I want to use it.

Maybe try switching to 32 bit linux, and see if your problems are solved.

Oh forget what I just posted I have not installed Flash yet and am afraid of doing it now.

But how can flash be a problem if you are not running your browser yet?

---

### Post by smilingfrog on 2010-10-01
My understanding is that flash runs as an extension from your browser, using the library files of your computer. The extension allows you to watch flash in the browser, rather than having to download it and watch it in a separate viewer. Likewise, you can run a browser with no flash libraries at all, you just won't see any flash content.

The problems are with 64 bit flash, for the most part.

---

### Post by davidvandoren on 2010-10-02
I actually got a lockout today dropping me onto the command line but no freeze.

I checked my system log and my apt log and found that this ```
/etc/gdm/custom.conf': No such file or directory
``` appeared the first time after installing the additional video codex using [https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats) and then clicking ubuntu-restricted-extra-packages

```
**Playing Restricted Formats**

  
Follow  these steps to play and record most common multimedia formats,  including MP3, DVD, Flash, Quicktime, WMA and WMV, including both  standalone files and content embedded in web pages. 
 
**Ubuntu 10.04 LTS (Lucid Lynx) and 9.10 (Karmic Koala)**

 
```


To create this file I just opened system / Administration / Login Screen  click on unlock and play with the settings. Put everything back to original and close. You can open the folder etc/gdm and watch.

---

### Post by edward1978 on 2010-10-02
> **smilingfrog said:**
> I have a few questions:
1. Are you running 64 bit Ubuntu?
2. Are you running VirtualBox?
3. Do you have Flash installed?

I have been plagued with the same problem with crashing. Youtube *is* flash, as the player relies on it, and I cannot surf Youtube without crashing. Things got better when I uninstalled Flash completely, but it does hobble the fun of the machine. Adobe recently re-started 64 bit support, but I haven't noticed a difference to stability yet.

I have freezes in VirtualBox if I try to resize windows within the virtual machine.

I had no problems before upgrading to 64 bit, but I have 8GB now, and I want to use it.

Maybe try switching to 32 bit linux, and see if your problems are solved.

1. I do have the PAE kernel & am using it, but I booted with the 32 bit kernel, it also froze.
2. Nope
3. Yes, but youtube doesn't freeze all the time & it also freezes on none flash site. Also it rarely freezes.

32 bit froze with 8.04 also. I can not find any error anywhere, log files don't have a clue.

> 
The problems are with 64 bit flash, for the most part.I have 32bit flash

> I don't know but something goes wrong with the read write. Don't ask me  what exactly and how. SATA drives are around for years. But your new cpu  most likely isn't. In forums I always noticed my SATA here and my SATA  there so when seeing the IDE connector on my mother board I thought why  not and try out. 
I use Linux for more than five years now. As a user not programmer and never had problems like this on my first SATA drive.

Maybe they allow faster reading which can cause the trouble or maybe the  slower reading of the old drive prevents trouble. What do I know/care. 
Works for me at least for now it seems like it.

My dad had 8.04 on a SATA for a year, no freezes, 10.04 should be ok with SATA drives.

---

### Post by garner_nc on 2010-10-02
About now I'd be running an extended memtest to make sure my ram was okay. This sounds like a memory or hardware problem especially if you're not getting anything in your logs.

   Boot starting memtest and let it run for a day or so. I know it's a long time but your problem seems very intermittent and may require a long test time to show up.

All the Best,
D. White

---

### Post by edward1978 on 2010-10-02
> **garner_nc said:**
> About now I'd be running an extended memtest to make sure my ram was okay. This sounds like a memory or hardware problem especially if you're not getting anything in your logs.

   Boot starting memtest and let it run for a day or so. I know it's a long time but your problem seems very intermittent and may require a long test time to show up.

All the Best,
D. White

The memory is around a month old, well ok. I have 2 sticks, is it ok to test with both in? Odd, it can go days with out freezing though.

---

### Post by mc4man on 2010-10-02
> The memory is around a month old,
I would definetly ck. the ram, why did you replace it?

While I think these 'random' freezes or x crashing can have numerous causes, a hardware issue is quite likely

Over the summer this laptop developed the same - sometimes a couple of times a day, then fine for 4-5 days.

Memtest initially didn't show anything, as it was there was a built-in pre-boot memory test suite (dell).
Running that did show 2 bad addresses on 2 of the later tests, with the ram replaced have had no issues for almost a month now.

(in my case was able to find some info in syslog after restarting from a freeze at the timeframe just preceding the crash or freeze, though they didn't indicate a ram issue directly
(the relevant keywords for searching the syslog here were
Dazed
Uhhuh
os_pci_init_handle: invalid context!

---

### Post by edward1978 on 2010-10-02
> **mc4man said:**
> I would definetly ck. the ram, why did you replace it?

While I think these 'random' freezes or x crashing can have numerous causes, a hardware issue is quite likely

Over the summer this laptop developed the same - sometimes a couple of times a day, then fine for 4-5 days.

Memtest initially didn't show anything, as it was there was a built-in pre-boot memory test suite (dell).
Running that did show 2 bad addresses on 2 of the later tests, with the ram replaced have had no issues for almost a month now.

(in my case was able to find some info in syslog after restarting from a freeze at the timeframe just preceding the crash or freeze, though they didn't indicate a ram issue directly
(the relevant keywords for searching the syslog here were
Dazed
Uhhuh
os_pci_init_handle: invalid context!

Ironic, I replaced a bad stick, figured I get 2 cuase it was a little more $$ than 1. Is there a way to see what stick is bad if there is one? Man, a month & a few weeks old, I might have a bad stick!!! It is Kingston Platinum Series to...

I found this in messages it is dated a few days back, but looks like a clue iomem range 0x0-0x9ffff could not be reserved that looks like a memory prob. right?

---

