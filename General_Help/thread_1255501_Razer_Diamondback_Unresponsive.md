---
title: "Razer Diamondback Unresponsive"
date: 2009-09-01
forum: General Help
---

### Post by Omnicron on 2009-09-01
Hello all. I am brand new with Ubuntu, and I absolutely love it, except for the issue that my razer diamondback mouse is completely unresponsive when I log in. The odd thing is it works in the login screen, and for about 5 seconds once I have logged in, but then it completely freezes and is 100% unresponsive. I tried disconnecting it and switching it to a different usb port, but it is not detected after I unplug it. 

Any suggestions? I would really love the help, so that I can start using Ubuntu for real, and not with keyboard shortcuts! Thanks alot! (I'm not sure if I posted this question in the write place, but please forgive me if I didn't.)

---

### Post by P4man on 2009-09-01
Are you sure its the mouse, and not the entire system freezing up?
Ubuntu still reacts to keyboard commands ?

---

### Post by Omnicron on 2009-09-01
Yes, the keyboard still works, so does everything else (internet, portable HD, etc.)

---

### Post by P4man on 2009-09-01
thats weird ..
Its just a regular USB mouse right? Not a bluetooth mouse?

Anyway, run "dmesg" in a terminal and see if you find an error message that could help us out.

---

### Post by Omnicron on 2009-09-01
Yea, it's not bluetooth, and it's been working for flawlessly on vista since I purchased it a few years ago. I'll run dmesg, and let you know if I find anything.

---

### Post by sloggerkhan on 2009-09-01
I have a razer copperhead mouse and have never had any trouble with it.
Sorry can't be of help.

---

### Post by Omnicron on 2009-09-01
I can't seem to get the output from dmesg into a text file so that I can post it here on vista, but when I ran it, it didn't specifically give any error messages. Any other ideas while I try to get the output posted?

---

### Post by P4man on 2009-09-01
another mouse would be useful, assuming that one would work (which I kind of doubt). But if it didn't show an error, then don't try too hard. instead, try running 

```
lsusb
```

it lists all your usb devices. See if the mouse is in there, and if you unplug it, its removed, and if you plug it in again, its there again.

---

### Post by Omnicron on 2009-09-01
[    0.667448] ACPI: PCI Interrupt Link [LN7A] (IRQs 16 17 18 19) *0, disabled.
[    0.667793] ACPI: PCI Interrupt Link [LN7B] (IRQs 16 17 18 19) *0, disabled.
[    0.668148] ACPI: PCI Interrupt Link [LN7C] (IRQs 16 17 18 19) *0, disabled.
[    0.668494] ACPI: PCI Interrupt Link [LN7D] (IRQs 16 17 18 19) *0, disabled.
[    0.668845] ACPI: PCI Interrupt Link [LUB0] (IRQs 20 21 22 23) *11
[    0.669195] ACPI: PCI Interrupt Link [LUB2] (IRQs 20 21 22 23) *15
[    0.669544] ACPI: PCI Interrupt Link [LMAC] (IRQs 20 21 22 23) *15
[    0.669892] ACPI: PCI Interrupt Link [LAZA] (IRQs 20 21 22 23) *11
[    0.670241] ACPI: PCI Interrupt Link [SGRU] (IRQs 20 21 22 23) *10
[    0.670588] ACPI: PCI Interrupt Link [LSMB] (IRQs 20 21 22 23) *7
[    0.670937] ACPI: PCI Interrupt Link [LPMU] (IRQs 20 21 22 23) *10
[    0.671287] ACPI: PCI Interrupt Link [LSA0] (IRQs 20 21 22 23) *5
[    0.671691] ACPI: PCI Interrupt Link [LATA] (IRQs 20 21 22 23) *0, disabled.
[    0.672039] ACPI: PCI Interrupt Link [UB11] (IRQs 20 21 22 23) *14
[    0.672395] ACPI: PCI Interrupt Link [UB12] (IRQs 20 21 22 23) *10
[    0.672757] ACPI: WMI: Mapper loaded
[    0.672803] SCSI subsystem initialized
[    0.672803] libata version 3.00 loaded.
[    0.672803] usbcore: registered new interface driver usbfs
[    0.672803] usbcore: registered new interface driver hub
[    0.672803] usbcore: registered new device driver usb
[    0.672803] PCI: Using ACPI for IRQ routing
[    0.688010] Bluetooth: Core ver 2.13
[    0.688022] NET: Registered protocol family 31
[    0.688022] Bluetooth: HCI device and connection manager initialized
[    0.688022] Bluetooth: HCI socket layer initialized
[    0.688022] NET: Registered protocol family 8
[    0.688022] NET: Registered protocol family 20
[    0.688029] NetLabel: Initializing
[    0.688031] NetLabel:  domain hash size = 128
[    0.688032] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.688043] NetLabel:  unlabeled traffic allowed by default
[    0.688329] PCI-DMA: Disabling AGP.
[    0.688402] PCI-DMA: aperture base @ 20000000 size 65536 KB
[    0.688403] PCI-DMA: using GART IOMMU.
[    0.688407] PCI-DMA: Reserving 64MB of IOMMU area in the AGP aperture
[    0.689945] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 31
[    0.689951] hpet0: 3 comparators, 32-bit 25.000000 MHz counter
[    0.704077] AppArmor: AppArmor Filesystem Enabled
[    0.708018] Switched to high resolution mode on CPU 2
[    0.708020] Switched to high resolution mode on CPU 0
[    0.708022] Switched to high resolution mode on CPU 1
[    0.708030] Switched to high resolution mode on CPU 3
[    0.716495] pnp: PnP ACPI init
[    0.716512] ACPI: bus type pnp registered
[    0.724131] pnp: PnP ACPI: found 11 devices
[    0.724133] ACPI: ACPI bus type pnp unregistered
[    0.724144] system 00:04: ioport range 0x4d0-0x4d1 has been reserved
[    0.724147] system 00:04: ioport range 0x800-0x80f has been reserved
[    0.724149] system 00:04: ioport range 0x2000-0x207f has been reserved
[    0.724151] system 00:04: ioport range 0x2080-0x20ff has been reserved
[    0.724154] system 00:04: ioport range 0x2400-0x247f has been reserved
[    0.724156] system 00:04: ioport range 0x2480-0x24ff has been reserved
[    0.724158] system 00:04: ioport range 0x2800-0x287f has been reserved
[    0.724159] system 00:04: ioport range 0x2880-0x28ff has been reserved
[    0.724162] system 00:04: iomem range 0xfed04000-0xfed04fff has been reserved
[    0.724165] system 00:04: iomem range 0xfee01000-0xfeefffff has been reserved
[    0.724169] system 00:07: iomem range 0xfec00000-0xfec00fff has been reserved
[    0.724171] system 00:07: iomem range 0xfee00000-0xfee00fff has been reserved
[    0.724175] system 00:08: ioport range 0xa00-0xadf has been reserved
[    0.724179] system 00:09: iomem range 0xf0000000-0xf3ffffff has been reserved
[    0.724183] system 00:0a: iomem range 0x0-0x9ffff could not be reserved
[    0.724185] system 00:0a: iomem range 0xc0000-0xcffff has been reserved
[    0.724188] system 00:0a: iomem range 0xe0000-0xfffff could not be reserved
[    0.724190] system 00:0a: iomem range 0x100000-0xcfffffff could not be reserved
[    0.724192] system 00:0a: iomem range 0xfec00000-0xffffffff could not be reserved
[    0.728876] pci 0000:00:08.0: PCI bridge, secondary bus 0000:01
[    0.728877] pci 0000:00:08.0:   IO window: disabled
[    0.728881] pci 0000:00:08.0:   MEM window: 0xf8e00000-0xf8efffff
[    0.728884] pci 0000:00:08.0:   PREFETCH window: disabled
[    0.728888] pci 0000:00:0b.0: PCI bridge, secondary bus 0000:02
[    0.728890] pci 0000:00:0b.0:   IO window: 0xd000-0xdfff
[    0.728893] pci 0000:00:0b.0:   MEM window: 0xf8f00000-0xf9ffffff
[    0.728895] pci 0000:00:0b.0:   PREFETCH window: 0x000000d6000000-0x000000dfffffff
[    0.728899] pci 0000:00:10.0: PCI bridge, secondary bus 0000:03
[    0.728903] pci 0000:00:10.0:   IO window: 0xe000-0xefff
[    0.728913] pci 0000:00:10.0:   MEM window: 0xfa000000-0xfeafffff
[    0.728920] pci 0000:00:10.0:   PREFETCH window: 0x000000e0000000-0x000000efffffff
[    0.728932] pci 0000:00:12.0: PCI bridge, secondary bus 0000:04
[    0.728933] pci 0000:00:12.0:   IO window: disabled
[    0.728942] pci 0000:00:12.0:   MEM window: disabled
[    0.728949] pci 0000:00:12.0:   PREFETCH window: disabled
[    0.728960] pci 0000:00:13.0: PCI bridge, secondary bus 0000:05
[    0.728962] pci 0000:00:13.0:   IO window: disabled
[    0.728971] pci 0000:00:13.0:   MEM window: 0xfeb00000-0xfebfffff
[    0.728978] pci 0000:00:13.0:   PREFETCH window: disabled
[    0.728989] pci 0000:00:14.0: PCI bridge, secondary bus 0000:06
[    0.728991] pci 0000:00:14.0:   IO window: disabled
[    0.729000] pci 0000:00:14.0:   MEM window: disabled
[    0.729007] pci 0000:00:14.0:   PREFETCH window: disabled
[    0.729026] pci 0000:00:08.0: setting latency timer to 64
[    0.729030] pci 0000:00:0b.0: setting latency timer to 64
[    0.729525] ACPI: PCI Interrupt Link [LN0A] enabled at IRQ 19
[    0.729533] pci 0000:00:10.0: PCI INT A -> Link[LN0A] -> GSI 19 (level, low) -> IRQ 19
[    0.729541] pci 0000:00:10.0: setting latency timer to 64
[    0.730023] ACPI: PCI Interrupt Link [LN2A] enabled at IRQ 18
[    0.730034] pci 0000:00:12.0: PCI INT A -> Link[LN2A] -> GSI 18 (level, low) -> IRQ 18
[    0.730042] pci 0000:00:12.0: setting latency timer to 64
[    0.730519] ACPI: PCI Interrupt Link [LN3A] enabled at IRQ 17
[    0.730530] pci 0000:00:13.0: PCI INT A -> Link[LN3A] -> GSI 17 (level, low) -> IRQ 17
[    0.730537] pci 0000:00:13.0: setting latency timer to 64
[    0.731003] ACPI: PCI Interrupt Link [LN4A] enabled at IRQ 16
[    0.731014] pci 0000:00:14.0: PCI INT A -> Link[LN4A] -> GSI 16 (level, low) -> IRQ 16
[    0.731022] pci 0000:00:14.0: setting latency timer to 64
[    0.731027] bus: 00 index 0 io port: [0x00-0xffff]
[    0.731029] bus: 00 index 1 mmio: [0x000000-0xffffffffffffffff]
[    0.731031] bus: 01 index 0 mmio: [0x0-0x0]
[    0.731032] bus: 01 index 1 mmio: [0xf8e00000-0xf8efffff]
[    0.731034] bus: 01 index 2 mmio: [0x0-0x0]
[    0.731035] bus: 01 index 3 io port: [0x00-0xffff]
[    0.731037] bus: 01 index 4 mmio: [0x000000-0xffffffffffffffff]
[    0.731043] bus: 02 index 0 io port: [0xd000-0xdfff]
[    0.731044] bus: 02 index 1 mmio: [0xf8f00000-0xf9ffffff]
[    0.731046] bus: 02 index 2 mmio: [0xd6000000-0xdfffffff]
[    0.731047] bus: 02 index 3 mmio: [0x0-0x0]
[    0.731052] bus: 03 index 0 io port: [0xe000-0xefff]
[    0.731053] bus: 03 index 1 mmio: [0xfa000000-0xfeafffff]
[    0.731055] bus: 03 index 2 mmio: [0xe0000000-0xefffffff]
[    0.731056] bus: 03 index 3 mmio: [0x0-0x0]
[    0.731058] bus: 04 index 0 mmio: [0x0-0x0]
[    0.731059] bus: 04 index 1 mmio: [0x0-0x0]
[    0.731060] bus: 04 index 2 mmio: [0x0-0x0]
[    0.731062] bus: 04 index 3 mmio: [0x0-0x0]
[    0.731063] bus: 05 index 0 mmio: [0x0-0x0]
[    0.731064] bus: 05 index 1 mmio: [0xfeb00000-0xfebfffff]
[    0.731066] bus: 05 index 2 mmio: [0x0-0x0]
[    0.731067] bus: 05 index 3 mmio: [0x0-0x0]
[    0.731069] bus: 06 index 0 mmio: [0x0-0x0]
[    0.731070] bus: 06 index 1 mmio: [0x0-0x0]
[    0.731071] bus: 06 index 2 mmio: [0x0-0x0]
[    0.731072] bus: 06 index 3 mmio: [0x0-0x0]
[    0.731082] NET: Registered protocol family 2
[    0.764267] IP route cache hash table entries: 262144 (order: 9, 2097152 bytes)
[    0.764912] TCP established hash table entries: 262144 (order: 10, 4194304 bytes)
[    0.766825] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[    0.767306] TCP: Hash tables configured (established 262144 bind 65536)
[    0.767308] TCP reno registered
[    0.776399] NET: Registered protocol family 1
[    0.776508] checking if image is initramfs... it is
[    1.289497] Freeing initrd memory: 7772k freed
[    1.292724] audit: initializing netlink socket (disabled)
[    1.292742] type=2000 audit(1251819406.292:1): initialized
[    1.299604] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    1.300851] VFS: Disk quotas dquot_6.5.1
[    1.300898] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    1.301443] fuse init (API version 7.10)
[    1.301519] msgmni has been set to 9275
[    1.301692] alg: No test for stdrng (krng)
[    1.301704] io scheduler noop registered
[    1.301706] io scheduler anticipatory registered
[    1.301708] io scheduler deadline registered
[    1.301742] io scheduler cfq registered (default)
[    1.389612] pci 0000:00:07.0: Enabling HT MSI Mapping
[    1.389640] pci 0000:00:08.0: Enabling HT MSI Mapping
[    1.389670] pci 0000:00:09.0: Enabling HT MSI Mapping
[    1.389699] pci 0000:00:0a.0: Enabling HT MSI Mapping
[    1.389727] pci 0000:00:0b.0: Enabling HT MSI Mapping
[    1.389782] pci 0000:00:10.0: Enabling HT MSI Mapping
[    1.389848] pci 0000:00:12.0: Enabling HT MSI Mapping
[    1.389914] pci 0000:00:13.0: Enabling HT MSI Mapping
[    1.389980] pci 0000:00:14.0: Enabling HT MSI Mapping
[    1.390056] pci 0000:03:00.0: Boot video device
[    1.400786] pcieport-driver 0000:00:10.0: setting latency timer to 64
[    1.400956] pcieport-driver 0000:00:10.0: found MSI capability
[    1.401044] pcieport-driver 0000:00:10.0: irq 2303 for MSI/MSI-X
[    1.401077] pci_express 0000:00:10.0:pcie00: allocate port service
[    1.401254] pcieport-driver 0000:00:12.0: setting latency timer to 64
[    1.401421] pcieport-driver 0000:00:12.0: found MSI capability
[    1.401514] pcieport-driver 0000:00:12.0: irq 2302 for MSI/MSI-X
[    1.401547] pci_express 0000:00:12.0:pcie00: allocate port service
[    1.401720] pcieport-driver 0000:00:13.0: setting latency timer to 64
[    1.401887] pcieport-driver 0000:00:13.0: found MSI capability
[    1.401971] pcieport-driver 0000:00:13.0: irq 2301 for MSI/MSI-X
[    1.402004] pci_express 0000:00:13.0:pcie00: allocate port service
[    1.402176] pcieport-driver 0000:00:14.0: setting latency timer to 64
[    1.402343] pcieport-driver 0000:00:14.0: found MSI capability
[    1.402427] pcieport-driver 0000:00:14.0: irq 2300 for MSI/MSI-X
[    1.402460] pci_express 0000:00:14.0:pcie00: allocate port service
[    1.402603] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    1.402611] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    1.402736] input: Power Button (FF) as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input0
[    1.402739] ACPI: Power Button (FF) [PWRF]
[    1.402784] input: Power Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1
[    1.402794] ACPI: Power Button (CM) [PWRB]
[    1.403105] processor ACPI_CPU:00: registered as cooling_device0
[    1.403130] processor ACPI_CPU:01: registered as cooling_device1
[    1.403159] processor ACPI_CPU:02: registered as cooling_device2
[    1.403185] processor ACPI_CPU:03: registered as cooling_device3
[    1.437887] Linux agpgart interface v0.103
[    1.437895] Serial: 8250/16550 driver4 ports, IRQ sharing enabled
[    1.438597] brd: module loaded
[    1.438828] loop: module loaded
[    1.438880] Fixed MDIO Bus: probed
[    1.438884] PPP generic driver version 2.4.2
[    1.438926] input: Macintosh mouse button emulation as /devices/virtual/input/input2
[    1.438951] Driver 'sd' needs updating - please use bus_type methods
[    1.438958] Driver 'sr' needs updating - please use bus_type methods
[    1.438993] ahci 0000:00:09.0: version 3.0
[    1.439458] ACPI: PCI Interrupt Link [LSA0] enabled at IRQ 23
[    1.439467] ahci 0000:00:09.0: PCI INT A -> Link[LSA0] -> GSI 23 (level, low) -> IRQ 23
[    1.439500] ahci 0000:00:09.0: irq 2299 for MSI/MSI-X
[    1.439557] ahci 0000:00:09.0: AHCI 0001.0200 32 slots 6 ports 3 Gbps 0x3f impl RAID mode
[    1.439560] ahci 0000:00:09.0: flags: 64bit ncq sntf led clo pmp pio 
[    1.439563] ahci 0000:00:09.0: setting latency timer to 64
[    1.439975] scsi0 : ahci
[    1.440067] scsi1 : ahci
[    1.440119] scsi2 : ahci
[    1.440169] scsi3 : ahci
[    1.440221] scsi4 : ahci
[    1.440276] scsi5 : ahci
[    1.440360] ata1: SATA max UDMA/133 abar m8192@0xf8d76000 port 0xf8d76100 irq 2299
[    1.440363] ata2: SATA max UDMA/133 abar m8192@0xf8d76000 port 0xf8d76180 irq 2299
[    1.440365] ata3: SATA max UDMA/133 abar m8192@0xf8d76000 port 0xf8d76200 irq 2299
[    1.440367] ata4: SATA max UDMA/133 abar m8192@0xf8d76000 port 0xf8d76280 irq 2299
[    1.440369] ata5: SATA max UDMA/133 abar m8192@0xf8d76000 port 0xf8d76300 irq 2299
[    1.440372] ata6: SATA max UDMA/133 abar m8192@0xf8d76000 port 0xf8d76380 irq 2299
[    1.920191] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    1.921117] ata1.00: ATA-7: Hitachi HDS721075KLA330, GK8OA87A, max UDMA/133
[    1.921119] ata1.00: 1465149168 sectors, multi 16: LBA48 NCQ (depth 31/32)
[    1.922377] ata1.00: configured for UDMA/133
[    2.808291] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    2.813659] ata2.00: ATAPI: HL-DT-ST DVD-RAM GH10L, FC09, max UDMA/100
[    2.819933] ata2.00: configured for UDMA/100
[    3.144240] ata3: SATA link down (SStatus 0 SControl 300)
[    3.464050] ata4: SATA link down (SStatus 0 SControl 300)
[    3.784215] ata5: SATA link down (SStatus 0 SControl 300)
[    4.104070] ata6: SATA link down (SStatus 0 SControl 300)
[    4.104162] scsi 0:0:0:0: Direct-Access     ATA      Hitachi HDS72107 GK8O PQ: 0 ANSI: 5
[    4.104229] sd 0:0:0:0: [sda] 1465149168 512-byte hardware sectors: (750 GB/698 GiB)
[    4.104240] sd 0:0:0:0: [sda] Write Protect is off
[    4.104242] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    4.104260] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    4.104312] sd 0:0:0:0: [sda] 1465149168 512-byte hardware sectors: (750 GB/698 GiB)
[    4.104327] sd 0:0:0:0: [sda] Write Protect is off
[    4.104328] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    4.104343] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    4.104351]  sda: sda1 sda2 sda3 < sda5 sda6 sda7 sda8 sda9 sda10 >
[    4.197146] sd 0:0:0:0: [sda] Attached SCSI disk
[    4.197179] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    4.200837] scsi 1:0:0:0: CD-ROM            HL-DT-ST DVD-RAM GH10L    FC09 PQ: 0 ANSI: 5
[    4.205400] sr0: scsi3-mmc drive: 40x/40x writer dvd-ram cd/rw xa/form2 cdda tray
[    4.205402] Uniform CD-ROM driver Revision: 3.20
[    4.205474] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    4.205512] sr 1:0:0:0: Attached scsi generic sg1 type 5
[    4.205979] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    4.206444] ACPI: PCI Interrupt Link [LUB2] enabled at IRQ 22
[    4.206452] ehci_hcd 0000:00:02.1: PCI INT B -> Link[LUB2] -> GSI 22 (level, low) -> IRQ 22
[    4.206464] ehci_hcd 0000:00:02.1: setting latency timer to 64
[    4.206466] ehci_hcd 0000:00:02.1: EHCI Host Controller
[    4.206510] ehci_hcd 0000:00:02.1: new USB bus registered, assigned bus number 1
[    4.206540] ehci_hcd 0000:00:02.1: debug port 1
[    4.206544] ehci_hcd 0000:00:02.1: cache line size of 64 is not supported
[    4.206560] ehci_hcd 0000:00:02.1: irq 22, io mem 0xf8d7ec00
[    4.217589] ehci_hcd 0000:00:02.1: USB 2.0 started, EHCI 1.00
[    4.217645] usb usb1: configuration #1 chosen from 1 choice
[    4.217666] hub 1-0:1.0: USB hub found
[    4.217672] hub 1-0:1.0: 6 ports detected
[    4.218198] ACPI: PCI Interrupt Link [UB12] enabled at IRQ 21
[    4.218205] ehci_hcd 0000:00:04.1: PCI INT B -> Link[UB12] -> GSI 21 (level, low) -> IRQ 21
[    4.218212] ehci_hcd 0000:00:04.1: setting latency timer to 64
[    4.218214] ehci_hcd 0000:00:04.1: EHCI Host Controller
[    4.218244] ehci_hcd 0000:00:04.1: new USB bus registered, assigned bus number 2
[    4.218266] ehci_hcd 0000:00:04.1: debug port 1
[    4.218269] ehci_hcd 0000:00:04.1: cache line size of 64 is not supported
[    4.218283] ehci_hcd 0000:00:04.1: irq 21, io mem 0xf8d7e800
[    4.228114] ehci_hcd 0000:00:04.1: USB 2.0 started, EHCI 1.00
[    4.228160] usb usb2: configuration #1 chosen from 1 choice
[    4.228182] hub 2-0:1.0: USB hub found
[    4.228187] hub 2-0:1.0: 6 ports detected
[    4.228263] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    4.228714] ACPI: PCI Interrupt Link [LUB0] enabled at IRQ 20
[    4.228721] ohci_hcd 0000:00:02.0: PCI INT A -> Link[LUB0] -> GSI 20 (level, low) -> IRQ 20
[    4.228729] ohci_hcd 0000:00:02.0: setting latency timer to 64
[    4.228731] ohci_hcd 0000:00:02.0: OHCI Host Controller
[    4.228761] ohci_hcd 0000:00:02.0: new USB bus registered, assigned bus number 3
[    4.228781] ohci_hcd 0000:00:02.0: irq 20, io mem 0xf8d7f000
[    4.286266] usb usb3: configuration #1 chosen from 1 choice
[    4.286285] hub 3-0:1.0: USB hub found
[    4.286291] hub 3-0:1.0: 6 ports detected
[    4.286795] ACPI: PCI Interrupt Link [UB11] enabled at IRQ 23
[    4.286797] ohci_hcd 0000:00:04.0: PCI INT A -> Link[UB11] -> GSI 23 (level, low) -> IRQ 23
[    4.286805] ohci_hcd 0000:00:04.0: setting latency timer to 64
[    4.286807] ohci_hcd 0000:00:04.0: OHCI Host Controller
[    4.286836] ohci_hcd 0000:00:04.0: new USB bus registered, assigned bus number 4
[    4.286856] ohci_hcd 0000:00:04.0: irq 23, io mem 0xf8d7d000
[    4.342323] usb usb4: configuration #1 chosen from 1 choice
[    4.342342] hub 4-0:1.0: USB hub found
[    4.342347] hub 4-0:1.0: 6 ports detected
[    4.342424] uhci_hcd: USB Universal Host Controller Interface driver
[    4.342480] PNP: No PS/2 controller found. Probing ports directly.
[    4.344737] serio: i8042 KBD port at 0x60,0x64 irq 1
[    4.344743] serio: i8042 AUX port at 0x60,0x64 irq 12
[    4.353749] mice: PS/2 mouse device common for all mice
[    4.389648] rtc_cmos 00:06: RTC can wake from S4
[    4.389676] rtc_cmos 00:06: rtc core: registered rtc_cmos as rtc0
[    4.389730] rtc0: alarms up to one year, y3k, 114 bytes nvram, hpet irqs
[    4.389777] device-mapper: uevent: version 1.0.3
[    4.389860] device-mapper: ioctl: 4.14.0-ioctl (2008-04-23) initialised: [email]dm-devel@redhat.com[/email]
[    4.389999] device-mapper: multipath: version 1.0.5 loaded
[    4.390001] device-mapper: multipath round-robin: version 1.0.0 loaded
[    4.390159] cpuidle: using governor ladder
[    4.390160] cpuidle: using governor menu
[    4.390530] TCP cubic registered
[    4.390585] NET: Registered protocol family 10
[    4.390957] lo: Disabled Privacy Extensions
[    4.391218] NET: Registered protocol family 17
[    4.391233] Bluetooth: L2CAP ver 2.11
[    4.391234] Bluetooth: L2CAP socket layer initialized
[    4.391236] Bluetooth: SCO (Voice Link) ver 0.6
[    4.391238] Bluetooth: SCO socket layer initialized
[    4.391270] Bluetooth: RFCOMM socket layer initialized
[    4.391276] Bluetooth: RFCOMM TTY layer initialized
[    4.391277] Bluetooth: RFCOMM ver 1.10
[    4.391329] powernow-k8: Found 1 AMD Phenom(tm) 9550 Quad-Core Processor processors (4 cpu cores) (version 2.20.00)
[    4.391366] powernow-k8:    0 : pstate 0 (2200 MHz)
[    4.391369] powernow-k8:    1 : pstate 1 (1100 MHz)
[    4.391630] registered taskstats version 1
[    4.391768]   Magic number: 9:264:638
[    4.391886] rtc_cmos 00:06: setting system clock to 2009-09-01 15:36:50 UTC (1251819410)
[    4.391888] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    4.391890] EDD information not available.
[    4.391921] Freeing unused kernel memory: 532k freed
[    4.392103] Write protecting the kernel read-only data: 6688k
[    4.563713] forcedeth: Reverse Engineered nForce ethernet driver. Version 0.61.
[    4.564217] ACPI: PCI Interrupt Link [LMAC] enabled at IRQ 22
[    4.564221] forcedeth 0000:00:0a.0: PCI INT A -> Link[LMAC] -> GSI 22 (level, low) -> IRQ 22
[    4.564226] forcedeth 0000:00:0a.0: setting latency timer to 64
[    4.586565] ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 19
[    4.586571] ohci1394 0000:01:05.0: PCI INT A -> Link[LNKD] -> GSI 19 (level, low) -> IRQ 19
[    4.638329] ohci1394: fw-host0: OHCI-1394 1.0 (PCI): IRQ=[19]  MMIO=[f8eff000-f8eff7ff]  Max Packet=[1024]  IR/IT contexts=[8/8]
[    4.864515] usb 2-3: new high speed USB device using ehci_hcd and address 4
[    4.998601] usb 2-3: configuration #1 chosen from 1 choice
[    5.002632] Initializing USB Mass Storage driver...
[    5.002748] scsi6 : SCSI emulation for USB Mass Storage devices
[    5.003047] usb-storage: device found at 4
[    5.003049] usb-storage: waiting for device to settle before scanning
[    5.003054] usbcore: registered new interface driver usb-storage
[    5.003058] USB Mass Storage support registered.
[    5.085087] forcedeth 0000:00:0a.0: ifname eth0, PHY OUI 0x732 @ 1, addr 00:1f:c6:8a:11:70
[    5.085090] forcedeth 0000:00:0a.0: highdma csum pwrctl mgmt timirq gbit lnktim msi desc-v3
[    5.108037] usb 2-4: new high speed USB device using ehci_hcd and address 5
[    5.150240] PM: Starting manual resume from disk
[    5.150243] PM: Resume from partition 8:10
[    5.150244] PM: Checking hibernation image.
[    5.150354] PM: Resume from disk failed.
[    5.152121] EXT3-fs: INFO: recovery required on readonly filesystem.
[    5.152123] EXT3-fs: write access will be enabled during recovery.
[    5.241832] usb 2-4: configuration #1 chosen from 1 choice
[    5.242214] scsi7 : SCSI emulation for USB Mass Storage devices
[    5.242358] usb-storage: device found at 5
[    5.242360] usb-storage: waiting for device to settle before scanning
[    5.513505] kjournald starting.  Commit interval 5 seconds
[    5.513517] EXT3-fs: recovery complete.
[    5.519203] EXT3-fs: mounted filesystem with ordered data mode.
[    5.545561] usb 4-1: new full speed USB device using ohci_hcd and address 2
[    5.772033] usb 4-1: configuration #1 chosen from 1 choice
[    5.921779] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[001e8c00013aa675]
[    6.077737] usb 4-2: new low speed USB device using ohci_hcd and address 3
[    6.288329] usb 4-2: configuration #1 chosen from 1 choice
[    6.593794] usb 3-1: new full speed USB device using ohci_hcd and address 2
[    6.806705] usb 3-1: configuration #1 chosen from 1 choice
[    7.113580] usb 3-2: new low speed USB device using ohci_hcd and address 3
[    7.446779] usb 3-2: configuration #1 chosen from 1 choice
[    9.856494] udev: starting version 141
[   10.000432] usb-storage: device scan complete
[   10.002196] scsi 6:0:0:0: Direct-Access     Generic  USB SD Reader    1.00 PQ: 0 ANSI: 0
[   10.002812] scsi 6:0:0:1: Direct-Access     Generic  USB CF Reader    1.01 PQ: 0 ANSI: 0
[   10.003438] scsi 6:0:0:2: Direct-Access     Generic  USB SM Reader    1.02 PQ: 0 ANSI: 0
[   10.004062] scsi 6:0:0:3: Direct-Access     Generic  USB MS Reader    1.03 PQ: 0 ANSI: 0
[   10.005184] sd 6:0:0:0: [sdb] Attached SCSI removable disk
[   10.005243] sd 6:0:0:0: Attached scsi generic sg2 type 0
[   10.005982] sd 6:0:0:1: [sdc] Attached SCSI removable disk
[   10.006018] sd 6:0:0:1: Attached scsi generic sg3 type 0
[   10.006728] sd 6:0:0:2: [sdd] Attached SCSI removable disk
[   10.006766] sd 6:0:0:2: Attached scsi generic sg4 type 0
[   10.007537] sd 6:0:0:3: [sde] Attached SCSI removable disk
[   10.007584] sd 6:0:0:3: Attached scsi generic sg5 type 0
[   10.240640] usb-storage: device scan complete
[   10.242554] scsi 7:0:0:0: Direct-Access     WD       2500BMV External 1.75 PQ: 0 ANSI: 4
[   10.243794] sd 7:0:0:0: [sdf] 488397168 512-byte hardware sectors: (250 GB/232 GiB)
[   10.245367] sd 7:0:0:0: [sdf] Write Protect is off
[   10.245370] sd 7:0:0:0: [sdf] Mode Sense: 23 00 00 00
[   10.245372] sd 7:0:0:0: [sdf] Assuming drive cache: write through
[   10.247021] sd 7:0:0:0: [sdf] 488397168 512-byte hardware sectors: (250 GB/232 GiB)
[   10.248274] sd 7:0:0:0: [sdf] Write Protect is off
[   10.248276] sd 7:0:0:0: [sdf] Mode Sense: 23 00 00 00
[   10.248277] sd 7:0:0:0: [sdf] Assuming drive cache: write through
[   10.248281]  sdf: sdf1
[   10.614818] sd 7:0:0:0: [sdf] Attached SCSI disk
[   10.614917] sd 7:0:0:0: Attached scsi generic sg6 type 0
[   10.955940] nvidia: module license 'NVIDIA' taints kernel.
[   10.981399] usblp0: USB Bidirectional printer dev 2 if 1 alt 0 proto 2 vid 0x03F0 pid 0x4C11
[   10.981422] usbcore: registered new interface driver usblp
[   10.991038] usbcore: registered new interface driver hiddev
[   10.997550] input: USB-compliant keyboard as /devices/pci0000:00/0000:00:04.0/usb4/4-2/4-2:1.0/input/input3
[   11.028849] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   11.209801] nvidia 0000:02:00.0: enabling device (0000 -> 0003)
[   11.210298] ACPI: PCI Interrupt Link [SGRU] enabled at IRQ 21
[   11.210302] nvidia 0000:02:00.0: PCI INT A -> Link[SGRU] -> GSI 21 (level, low) -> IRQ 21
[   11.210310] nvidia 0000:02:00.0: setting latency timer to 64
[   11.210541] nvidia 0000:03:00.0: PCI INT A -> Link[LN0A] -> GSI 19 (level, low) -> IRQ 19
[   11.210546] nvidia 0000:03:00.0: setting latency timer to 64
[   11.210970] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  180.44  Tue Mar 24 05:46:32 PST 2009
[   11.225243] input: PC Speaker as /devices/platform/pcspkr/input/input4
[   11.241205] generic-usb 0003:062A:0201.0001: input,hidraw0: USB HID v1.10 Keyboard [USB-compliant keyboard] on usb-0000:00:04.0-2/input0
[   11.250157] input: USB-compliant keyboard as /devices/pci0000:00/0000:00:04.0/usb4/4-2/4-2:1.1/input/input5
[   11.322143] generic-usb 0003:062A:0201.0002: input,hiddev96,hidraw1: USB HID v1.10 Mouse [USB-compliant keyboard] on usb-0000:00:04.0-2/input1
[   11.328964] input: Razer Razer 1600dpi Mouse as /devices/pci0000:00/0000:00:02.0/usb3/3-2/3-2:1.0/input/input6
[   11.365688] generic-usb 0003:1532:0001.0003: input,hidraw2: USB HID v1.10 Mouse [Razer Razer 1600dpi Mouse] on usb-0000:00:02.0-2/input0
[   11.365712] usbcore: registered new interface driver usbhid
[   11.365715] usbhid: v2.6:USB HID core driver
[   11.413790] HDA Intel 0000:00:07.0: power state changed by ACPI to D0
[   11.414264] ACPI: PCI Interrupt Link [LAZA] enabled at IRQ 20
[   11.414269] HDA Intel 0000:00:07.0: PCI INT A -> Link[LAZA] -> GSI 20 (level, low) -> IRQ 20
[   11.414338] HDA Intel 0000:00:07.0: setting latency timer to 64
[   11.438831] usbcore: registered new interface driver snd-usb-audio
[   11.804095] hda_codec: Unknown model for ALC883, trying auto-probe from BIOS...
[   12.401934] lp: driver loaded but no devices found
[   12.471180] Adding 289128k swap on /dev/sda10.  Priority:-1 extents:1 across:289128k
[   13.015077] EXT3 FS on sda9, internal journal
[   13.861512] type=1505 audit(1251833819.969:2): operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" name2="default" pid=2404
[   13.899796] type=1505 audit(1251833820.005:3): operation="profile_load" name="/sbin/dhclient-script" name2="default" pid=2408
[   13.899901] type=1505 audit(1251833820.005:4): operation="profile_load" name="/sbin/dhclient3" name2="default" pid=2408
[   13.899932] type=1505 audit(1251833820.005:5): operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" name2="default" pid=2408
[   13.899961] type=1505 audit(1251833820.005:6): operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" name2="default" pid=2408
[   14.010984] type=1505 audit(1251833820.116:7): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=2413
[   14.011128] type=1505 audit(1251833820.116:8): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=2413
[   14.035870] type=1505 audit(1251833820.140:9): operation="profile_load" name="/usr/sbin/tcpdump" name2="default" pid=2417
[   16.829678] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   16.829681] Bluetooth: BNEP filters: protocol multicast
[   16.836722] Bridge firewalling registered
[   18.116236] ppdev: user-space parallel port driver
[   21.893358] forcedeth 0000:00:0a.0: irq 2298 for MSI/MSI-X
[   32.832284] eth0: no IPv6 routers present
[   55.133309] UDF-fs: No VRS found
[   55.149109] ISO 9660 Extensions: Microsoft Joliet Level 3
[   55.150518] ISOFS: changing to secondary root
[   56.317567] timeout: still 8 active urbs..
kevin@omnicron:~$ 

Thats what dmesg put out. I'm a noob so it's kinda hard for me to judge what the problem might be.

---

### Post by P4man on 2009-09-01
please put long lists such as that between [CODE] tags, so they get put in a scrolling box on the forum, makes it easier to read ;) You can edit your post to add them.

your dmegs doesn't reveal any problems afaict, let me know what lsusb gives (that is LSUSB in lowercase). see my previous post

---

### Post by Omnicron on 2009-09-01
I ran lsusb,  and it detected my mouse on port 003, but when I unplugged it and I tried to run lsusb again it wouldn't output anything. Any ideas what might be the problem? I'm really confused why my mouse isn't working when all my other usb devices are.

---

### Post by P4man on 2009-09-01
it detected it, even when it wasn't working? Or was it still working when it showed in lsusb?

Either way, I tried googling on the issue, but I cant find much definitive. Most things I find seem to indicate a faulty USB port or broken cable. Others say running lsusb a few times can make it detect again.

Im not sure I can give any good advice at this point :s

---

### Post by Omnicron on 2009-09-01
Well, that's the weirdest part, the physical mouse is still on, because it still glows blue from the internal LED inside it, but the mouse is unresponsive and does not move.

 It detects it with lsusb, but when I tried unplugging it and the plugging it back in again it simply doesn't glow whatsoever and is not detected at all.

---

### Post by sloggerkhan on 2009-09-01
[http://bbs.archlinux.org/viewtopic.php?id=58050](http://bbs.archlinux.org/viewtopic.php?id=58050)
Seems like it might be hitting on similar issues.

---

### Post by Omnicron on 2009-09-01
Thanks for that thread, but I don't think I have the same problem they are hitting on. Any other ideas.

---

### Post by sloggerkhan on 2009-09-01
> **Omnicron said:**
> Thanks for that thread, but I don't think I have the same problem they are hitting on. Any other ideas.

Mostly what's relevant is that 
sudo rmmod xyz
sudo modprobe xyz
may be useful if you can figure out what particular part of the mouse is bugging out on you.

My razer shows up as 2 devices, a hid mouse and a keyboard, I think (not at a home), so it's possible that if whatever driver was working previously if you force reload it, it may begin working again.

---

