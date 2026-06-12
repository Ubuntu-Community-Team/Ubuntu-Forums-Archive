---
title: "Cannot burn second disk until reboot"
date: 2010-06-03
forum: General Help
---

### Post by jm321 on 2010-06-03
Hi all,

First Ubuntu install, everything is great except one small problem burning.  Using Brasero 

I burn CD fine
Eject disc
Drive is not accessible for reading or writing CD's until I reboot the computer
Right click on the drive to mount volume and get "Unable to mount volume, no media in drive"

After reboot all is fine.  I have tried multiple burners, same issue.   USB burners can be unplugged, replugged in and used without a reboot.

Drive is a ASUS DRW 1612DL IDE

Happens in both Brasero and K3B

Ubuntu 9.04 Jackalope

Thanks in advance, Jeremy

---

### Post by Jeroensum on 2010-06-03
This might be a weird question, but how exactly do you eject the disc? Trough the burn tool, by pressing the button or by using the eject command or otherwise?

Next, it seems that something is keeping your drive locked, by issuing lsof (in a terminal) you could check what that something is.
lsof needs a location as an argument and this location could be the mountpoint of the drive, probably somewhere under /media , you can check this by issuing: mount in a terminal when you put a(ny) non-blank disc in the drive and waiting for it to be accessible.

So when you know the mountpoint and your drive bugs you again, run something like: lsof /media/cdrom and check if there are processes claiming that location. If there are, kill them like so:
kill <PID> (second column in the lsof output) or by using killall followed by the name of the program. And then try to use the drive again, btw, if there are several programs using the location, kill them all! (possibly the most used quote in many zombie-movies as well) ;o) Also don't expect a process to be dead instantaniously, sometimes they won't just die (again reminding me of zombies somehow...) and you could try kill(all) -9 , this will dissalow a clean exit and just drop the sucker dead in it's tracks. (kind of like a shotgun in zombie movies)

If nothing shows up in lsof you could run dmesg (in a terminal) and check if there are (error)messages about the device.

Lastly I would like to appologize to all non-zombie-movie lovers for the references in this post, or for any zombies out there that I may have offended :P

---

### Post by jm321 on 2010-06-03
Hi there, thanks for the ideas!

I was so excited and ready to kickass, but there were no zombies at all.  Oh well, hopefully I'll have better luck next time.  

The CD burning program is able to eject the burnt disc fine, it is only when the drive door is then closed that the drive turns zombie.  Oooh wait, there is a zombie after all!!

When I do the dmesg I do come up with some interesting stuff.  I'll post the dmesg on a fresh reboot, followed by a dmesg post burn when the drive is inaccessible.. thanks again for the help!  J




dmesg when drive is fine


[    0.617179] system 00:01: iomem range 0xfefe1000-0xfefe10ff has been reserved
[    0.617183] system 00:02: ioport range 0x4d0-0x4d1 has been reserved
[    0.617185] system 00:02: ioport range 0x800-0x87f has been reserved
[    0.617187] system 00:02: ioport range 0x290-0x297 has been reserved
[    0.617193] system 00:0b: iomem range 0xf0000000-0xf3ffffff has been reserved
[    0.617198] system 00:0c: iomem range 0xcf000-0xcffff has been reserved
[    0.617200] system 00:0c: iomem range 0xf0000-0xf7fff could not be reserved
[    0.617202] system 00:0c: iomem range 0xf8000-0xfbfff could not be reserved
[    0.617204] system 00:0c: iomem range 0xfc000-0xfffff could not be reserved
[    0.617207] system 00:0c: iomem range 0xfeff0000-0xfeff00ff has been reserved
[    0.617209] system 00:0c: iomem range 0xdfee0000-0xdfefffff could not be reserved
[    0.617212] system 00:0c: iomem range 0xffff0000-0xffffffff has been reserved
[    0.617214] system 00:0c: iomem range 0x0-0x9ffff could not be reserved
[    0.617216] system 00:0c: iomem range 0x100000-0xdfedffff could not be reserved
[    0.617219] system 00:0c: iomem range 0xfec00000-0xfec00fff has been reserved
[    0.617221] system 00:0c: iomem range 0xfee00000-0xfeefffff has been reserved
[    0.617224] system 00:0c: iomem range 0xfefff000-0xfeffffff has been reserved
[    0.617226] system 00:0c: iomem range 0xfff80000-0xfff80fff has been reserved
[    0.617228] system 00:0c: iomem range 0xfff90000-0xfffbffff has been reserved
[    0.617231] system 00:0c: iomem range 0xfffed000-0xfffeffff has been reserved
[    0.651913] pci 0000:00:08.0: PCI bridge, secondary bus 0000:01
[    0.651916] pci 0000:00:08.0:   IO window: 0xc000-0xcfff
[    0.651919] pci 0000:00:08.0:   MEM window: 0xfde00000-0xfdefffff
[    0.651922] pci 0000:00:08.0:   PREFETCH window: 0x000000f4000000-0x000000f7ffffff
[    0.651926] pci 0000:00:10.0: PCI bridge, secondary bus 0000:02
[    0.651931] pci 0000:00:10.0:   IO window: 0xb000-0xbfff
[    0.651940] pci 0000:00:10.0:   MEM window: 0xfa000000-0xfcffffff
[    0.651947] pci 0000:00:10.0:   PREFETCH window: 0x000000e0000000-0x000000efffffff
[    0.651959] pci 0000:00:12.0: PCI bridge, secondary bus 0000:03
[    0.651963] pci 0000:00:12.0:   IO window: 0xa000-0xafff
[    0.651973] pci 0000:00:12.0:   MEM window: 0xfdd00000-0xfddfffff
[    0.651980] pci 0000:00:12.0:   PREFETCH window: 0x000000fdc00000-0x000000fdcfffff
[    0.652007] pci 0000:00:13.0: PCI bridge, secondary bus 0000:04
[    0.652011] pci 0000:00:13.0:   IO window: 0x9000-0x9fff
[    0.652021] pci 0000:00:13.0:   MEM window: 0xfdb00000-0xfdbfffff
[    0.652027] pci 0000:00:13.0:   PREFETCH window: 0x000000fda00000-0x000000fdafffff
[    0.652039] pci 0000:00:14.0: PCI bridge, secondary bus 0000:05
[    0.652044] pci 0000:00:14.0:   IO window: 0x8000-0x8fff
[    0.652053] pci 0000:00:14.0:   MEM window: 0xfd900000-0xfd9fffff
[    0.652060] pci 0000:00:14.0:   PREFETCH window: 0x000000fd800000-0x000000fd8fffff
[    0.652076] pci 0000:00:08.0: setting latency timer to 64
[    0.652462] ACPI: PCI Interrupt Link [AE0A] enabled at IRQ 16
[    0.652470] pci 0000:00:10.0: PCI INT A -> Link[AE0A] -> GSI 16 (level, low) -> IRQ 16
[    0.652478] pci 0000:00:10.0: setting latency timer to 64
[    0.652857] ACPI: PCI Interrupt Link [AE2A] enabled at IRQ 16
[    0.652859] pci 0000:00:12.0: PCI INT A -> Link[AE2A] -> GSI 16 (level, low) -> IRQ 16
[    0.652867] pci 0000:00:12.0: setting latency timer to 64
[    0.653244] ACPI: PCI Interrupt Link [AE3A] enabled at IRQ 16
[    0.653246] pci 0000:00:13.0: PCI INT A -> Link[AE3A] -> GSI 16 (level, low) -> IRQ 16
[    0.653254] pci 0000:00:13.0: setting latency timer to 64
[    0.653631] ACPI: PCI Interrupt Link [AE4A] enabled at IRQ 16
[    0.653633] pci 0000:00:14.0: PCI INT A -> Link[AE4A] -> GSI 16 (level, low) -> IRQ 16
[    0.653641] pci 0000:00:14.0: setting latency timer to 64
[    0.653646] bus: 00 index 0 io port: [0x00-0xffff]
[    0.653648] bus: 00 index 1 mmio: [0x000000-0xffffffff]
[    0.653650] bus: 01 index 0 io port: [0xc000-0xcfff]
[    0.653651] bus: 01 index 1 mmio: [0xfde00000-0xfdefffff]
[    0.653653] bus: 01 index 2 mmio: [0xf4000000-0xf7ffffff]
[    0.653654] bus: 01 index 3 io port: [0x00-0xffff]
[    0.653656] bus: 01 index 4 mmio: [0x000000-0xffffffff]
[    0.653658] bus: 02 index 0 io port: [0xb000-0xbfff]
[    0.653659] bus: 02 index 1 mmio: [0xfa000000-0xfcffffff]
[    0.653661] bus: 02 index 2 mmio: [0xe0000000-0xefffffff]
[    0.653662] bus: 02 index 3 mmio: [0x0-0x0]
[    0.653664] bus: 03 index 0 io port: [0xa000-0xafff]
[    0.653665] bus: 03 index 1 mmio: [0xfdd00000-0xfddfffff]
[    0.653667] bus: 03 index 2 mmio: [0xfdc00000-0xfdcfffff]
[    0.653669] bus: 03 index 3 mmio: [0x0-0x0]
[    0.653670] bus: 04 index 0 io port: [0x9000-0x9fff]
[    0.653672] bus: 04 index 1 mmio: [0xfdb00000-0xfdbfffff]
[    0.653673] bus: 04 index 2 mmio: [0xfda00000-0xfdafffff]
[    0.653675] bus: 04 index 3 mmio: [0x0-0x0]
[    0.653677] bus: 05 index 0 io port: [0x8000-0x8fff]
[    0.653678] bus: 05 index 1 mmio: [0xfd900000-0xfd9fffff]
[    0.653680] bus: 05 index 2 mmio: [0xfd800000-0xfd8fffff]
[    0.653681] bus: 05 index 3 mmio: [0x0-0x0]
[    0.653690] NET: Registered protocol family 2
[    0.668053] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.668272] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.668766] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.669025] TCP: Hash tables configured (established 131072 bind 65536)
[    0.669027] TCP reno registered
[    0.676082] NET: Registered protocol family 1
[    0.676180] checking if image is initramfs... it is
[    1.121837] Freeing initrd memory: 7369k freed
[    1.121990] cpufreq: No nForce2 chipset.
[    1.122090] audit: initializing netlink socket (disabled)
[    1.122104] type=2000 audit(1275581705.120:1): initialized
[    1.128290] highmem bounce pool size: 64 pages
[    1.128294] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    1.129280] VFS: Disk quotas dquot_6.5.1
[    1.129321] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    1.129788] fuse init (API version 7.10)
[    1.129852] msgmni has been set to 1659
[    1.130010] alg: No test for stdrng (krng)
[    1.130019] io scheduler noop registered
[    1.130021] io scheduler anticipatory registered
[    1.130022] io scheduler deadline registered
[    1.130034] io scheduler cfq registered (default)
[    1.168606] pci 0000:00:07.0: Enabling HT MSI Mapping
[    1.168634] pci 0000:00:08.0: Enabling HT MSI Mapping
[    1.168663] pci 0000:00:09.0: Enabling HT MSI Mapping
[    1.168692] pci 0000:00:0a.0: Enabling HT MSI Mapping
[    1.168748] pci 0000:00:10.0: Enabling HT MSI Mapping
[    1.168813] pci 0000:00:12.0: Enabling HT MSI Mapping
[    1.168879] pci 0000:00:13.0: Enabling HT MSI Mapping
[    1.168945] pci 0000:00:14.0: Enabling HT MSI Mapping
[    1.168995] pci 0000:02:00.0: Boot video device
[    1.184575] pcieport-driver 0000:00:10.0: setting latency timer to 64
[    1.184745] pcieport-driver 0000:00:10.0: found MSI capability
[    1.184827] pcieport-driver 0000:00:10.0: irq 2303 for MSI/MSI-X
[    1.184860] pci_express 0000:00:10.0:pcie00: allocate port service
[    1.185036] pcieport-driver 0000:00:12.0: setting latency timer to 64
[    1.185202] pcieport-driver 0000:00:12.0: found MSI capability
[    1.185280] pcieport-driver 0000:00:12.0: irq 2302 for MSI/MSI-X
[    1.185312] pci_express 0000:00:12.0:pcie00: allocate port service
[    1.185487] pcieport-driver 0000:00:13.0: setting latency timer to 64
[    1.185654] pcieport-driver 0000:00:13.0: found MSI capability
[    1.185731] pcieport-driver 0000:00:13.0: irq 2301 for MSI/MSI-X
[    1.185764] pci_express 0000:00:13.0:pcie00: allocate port service
[    1.185937] pcieport-driver 0000:00:14.0: setting latency timer to 64
[    1.186103] pcieport-driver 0000:00:14.0: found MSI capability
[    1.186181] pcieport-driver 0000:00:14.0: irq 2300 for MSI/MSI-X
[    1.186213] pci_express 0000:00:14.0:pcie00: allocate port service
[    1.186358] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    1.186365] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    1.186505] input: Power Button (FF) as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input0
[    1.186507] ACPI: Power Button (FF) [PWRF]
[    1.186540] input: Power Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1
[    1.186542] ACPI: Power Button (CM) [PWRB]
[    1.186609] fan PNP0C0B:00: registered as cooling_device0
[    1.186613] ACPI: Fan [FAN] (on)
[    1.187086] processor ACPI_CPU:00: registered as cooling_device1
[    1.187112] processor ACPI_CPU:01: registered as cooling_device2
[    1.196468] ACPI Warning (nspredef-0858): \_TZ_.THRM._PSL: Return Package type mismatch at index 0 - found [NULL Object Descriptor], expected Reference [20080926]
[    1.196474] ACPI: Expecting a [Reference] package element, found type 0
[    1.196770] thermal LNXTHERM:01: registered as thermal_zone0
[    1.197287] ACPI: Thermal Zone [THRM] (40 C)
[    1.197344] isapnp: Scanning for PnP cards...
[    1.550057] isapnp: No Plug & Play device found
[    1.556731] Serial: 8250/16550 driver4 ports, IRQ sharing enabled
[    1.556819] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    1.557077] 00:09: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    1.557675] brd: module loaded
[    1.557927] loop: module loaded
[    1.557982] Fixed MDIO Bus: probed
[    1.557987] PPP generic driver version 2.4.2
[    1.558032] input: Macintosh mouse button emulation as /devices/virtual/input/input2
[    1.558058] Driver 'sd' needs updating - please use bus_type methods
[    1.558065] Driver 'sr' needs updating - please use bus_type methods
[    1.558098] ahci 0000:00:09.0: version 3.0
[    1.558518] ACPI: PCI Interrupt Link [APSI] enabled at IRQ 23
[    1.558528] ahci 0000:00:09.0: PCI INT A -> Link[APSI] -> GSI 23 (level, low) -> IRQ 23
[    1.558565] ahci 0000:00:09.0: irq 2299 for MSI/MSI-X
[    1.558638] ahci 0000:00:09.0: AHCI 0001.0200 32 slots 6 ports 3 Gbps 0x3f impl IDE mode
[    1.558641] ahci 0000:00:09.0: flags: 64bit ncq sntf led clo pmp pio 
[    1.558643] ahci 0000:00:09.0: setting latency timer to 64
[    1.559170] scsi0 : ahci
[    1.559275] scsi1 : ahci
[    1.559337] scsi2 : ahci
[    1.559404] scsi3 : ahci
[    1.559470] scsi4 : ahci
[    1.559531] scsi5 : ahci
[    1.559635] ata1: SATA max UDMA/133 abar m8192@0xfe026000 port 0xfe026100 irq 2299
[    1.559637] ata2: SATA max UDMA/133 abar m8192@0xfe026000 port 0xfe026180 irq 2299
[    1.559639] ata3: SATA max UDMA/133 abar m8192@0xfe026000 port 0xfe026200 irq 2299
[    1.559642] ata4: SATA max UDMA/133 abar m8192@0xfe026000 port 0xfe026280 irq 2299
[    1.559644] ata5: SATA max UDMA/133 abar m8192@0xfe026000 port 0xfe026300 irq 2299
[    1.559646] ata6: SATA max UDMA/133 abar m8192@0xfe026000 port 0xfe026380 irq 2299
[    2.040015] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    2.051621] ata1.00: ATA-7: WDC WD3200KS-00PFB0, 21.00M21, max UDMA/133
[    2.051623] ata1.00: 625142448 sectors, multi 16: LBA48 NCQ (depth 1)
[    2.052361] ata1.00: configured for UDMA/133
[    2.940018] ata2: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    2.941760] ata2.00: ATA-8: WDC WD10EADS-00M2B0, 01.00A01, max UDMA/133
[    2.941762] ata2.00: 1953525168 sectors, multi 16: LBA48 NCQ (depth 31/32)
[    2.942808] ata2.00: configured for UDMA/133
[    3.260016] ata3: SATA link down (SStatus 0 SControl 300)
[    3.580015] ata4: SATA link down (SStatus 0 SControl 300)
[    3.900015] ata5: SATA link down (SStatus 0 SControl 300)
[    4.220015] ata6: SATA link down (SStatus 0 SControl 300)
[    4.220105] scsi 0:0:0:0: Direct-Access     ATA      WDC WD3200KS-00P 21.0 PQ: 0 ANSI: 5
[    4.220180] sd 0:0:0:0: [sda] 625142448 512-byte hardware sectors: (320 GB/298 GiB)
[    4.220193] sd 0:0:0:0: [sda] Write Protect is off
[    4.220195] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    4.220214] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    4.220271] sd 0:0:0:0: [sda] 625142448 512-byte hardware sectors: (320 GB/298 GiB)
[    4.220282] sd 0:0:0:0: [sda] Write Protect is off
[    4.220284] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    4.220301] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    4.220305]  sda: sda1 sda2 < sda5 >
[    4.233879] sd 0:0:0:0: [sda] Attached SCSI disk
[    4.233918] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    4.233967] scsi 1:0:0:0: Direct-Access     ATA      WDC WD10EADS-00M 01.0 PQ: 0 ANSI: 5
[    4.234031] sd 1:0:0:0: [sdb] 1953525168 512-byte hardware sectors: (1.00 TB/931 GiB)
[    4.234042] sd 1:0:0:0: [sdb] Write Protect is off
[    4.234044] sd 1:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[    4.234061] sd 1:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    4.234098] sd 1:0:0:0: [sdb] 1953525168 512-byte hardware sectors: (1.00 TB/931 GiB)
[    4.234108] sd 1:0:0:0: [sdb] Write Protect is off
[    4.234110] sd 1:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[    4.234127] sd 1:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    4.234130]  sdb: sdb1 < sdb5 >
[    4.731040] sd 1:0:0:0: [sdb] Attached SCSI disk
[    4.731068] sd 1:0:0:0: Attached scsi generic sg1 type 0
[    4.731258] pata_amd 0000:00:06.0: version 0.3.10
[    4.731290] pata_amd 0000:00:06.0: setting latency timer to 64
[    4.731367] scsi6 : pata_amd
[    4.731437] scsi7 : pata_amd
[    4.732110] ata7: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xf000 irq 14
[    4.732112] ata8: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xf008 irq 15
[    4.896300] ata7.00: ATAPI: ASUS    DRW-1612BL, 1.06, max UDMA/66
[    4.896318] ata7: nv_mode_filter: 0x1f39f&0x1f01f->0x1f01f, BIOS=0x1f000 (0xc5000000) ACPI=0x1f01f (30:600:0x13)
[    4.912242] ata7.00: configured for UDMA/66
[    4.912468] ata8: port disabled. ignoring.
[    4.912948] scsi 6:0:0:0: CD-ROM            ASUS     DRW-1612BL       1.06 PQ: 0 ANSI: 5
[    4.916028] sr0: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
[    4.916031] Uniform CD-ROM driver Revision: 3.20
[    4.916107] sr 6:0:0:0: Attached scsi CD-ROM sr0
[    4.916139] sr 6:0:0:0: Attached scsi generic sg2 type 5
[    4.916525] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    4.916953] ACPI: PCI Interrupt Link [AUB2] enabled at IRQ 22
[    4.916962] ehci_hcd 0000:00:02.1: PCI INT B -> Link[AUB2] -> GSI 22 (level, low) -> IRQ 22
[    4.916978] ehci_hcd 0000:00:02.1: setting latency timer to 64
[    4.916980] ehci_hcd 0000:00:02.1: EHCI Host Controller
[    4.917027] ehci_hcd 0000:00:02.1: new USB bus registered, assigned bus number 1
[    4.917050] ehci_hcd 0000:00:02.1: debug port 1
[    4.917054] ehci_hcd 0000:00:02.1: cache line size of 64 is not supported
[    4.917071] ehci_hcd 0000:00:02.1: irq 22, io mem 0xfe02e000
[    4.928017] ehci_hcd 0000:00:02.1: USB 2.0 started, EHCI 1.00
[    4.928074] usb usb1: configuration #1 chosen from 1 choice
[    4.928095] hub 1-0:1.0: USB hub found
[    4.928101] hub 1-0:1.0: 6 ports detected
[    4.928417] ACPI: PCI Interrupt Link [AU2B] disabled and referenced, BIOS bug
[    4.928586] ACPI: PCI Interrupt Link [AU2B] enabled at IRQ 21
[    4.928593] ehci_hcd 0000:00:04.1: PCI INT B -> Link[AU2B] -> GSI 21 (level, low) -> IRQ 21
[    4.928602] ehci_hcd 0000:00:04.1: setting latency timer to 64
[    4.928604] ehci_hcd 0000:00:04.1: EHCI Host Controller
[    4.928642] ehci_hcd 0000:00:04.1: new USB bus registered, assigned bus number 2
[    4.928661] ehci_hcd 0000:00:04.1: debug port 1
[    4.928664] ehci_hcd 0000:00:04.1: cache line size of 64 is not supported
[    4.928678] ehci_hcd 0000:00:04.1: irq 21, io mem 0xfe02c000
[    4.940015] ehci_hcd 0000:00:04.1: USB 2.0 started, EHCI 1.00
[    4.940057] usb usb2: configuration #1 chosen from 1 choice
[    4.940075] hub 2-0:1.0: USB hub found
[    4.940080] hub 2-0:1.0: 6 ports detected
[    4.940152] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    4.940555] ACPI: PCI Interrupt Link [AUBA] enabled at IRQ 20
[    4.940561] ohci_hcd 0000:00:02.0: PCI INT A -> Link[AUBA] -> GSI 20 (level, low) -> IRQ 20
[    4.940570] ohci_hcd 0000:00:02.0: setting latency timer to 64
[    4.940572] ohci_hcd 0000:00:02.0: OHCI Host Controller
[    4.940607] ohci_hcd 0000:00:02.0: new USB bus registered, assigned bus number 3
[    4.940627] ohci_hcd 0000:00:02.0: irq 20, io mem 0xfe02f000
[    4.998038] usb usb3: configuration #1 chosen from 1 choice
[    4.998056] hub 3-0:1.0: USB hub found
[    4.998064] hub 3-0:1.0: 6 ports detected
[    4.998510] ACPI: PCI Interrupt Link [AU1B] enabled at IRQ 23
[    4.998512] ohci_hcd 0000:00:04.0: PCI INT A -> Link[AU1B] -> GSI 23 (level, low) -> IRQ 23
[    4.998520] ohci_hcd 0000:00:04.0: setting latency timer to 64
[    4.998522] ohci_hcd 0000:00:04.0: OHCI Host Controller
[    4.998562] ohci_hcd 0000:00:04.0: new USB bus registered, assigned bus number 4
[    4.998580] ohci_hcd 0000:00:04.0: irq 23, io mem 0xfe02d000
[    5.054031] usb usb4: configuration #1 chosen from 1 choice
[    5.054049] hub 4-0:1.0: USB hub found
[    5.054055] hub 4-0:1.0: 6 ports detected
[    5.054124] uhci_hcd: USB Universal Host Controller Interface driver
[    5.054175] usbcore: registered new interface driver libusual
[    5.054199] usbcore: registered new interface driver usbserial
[    5.054207] USB Serial support registered for generic
[    5.054218] usbcore: registered new interface driver usbserial_generic
[    5.054220] usbserial: USB Serial Driver core
[    5.054250] PNP: PS/2 Controller [PNP0303:PS2K] at 0x60,0x64 irq 1
[    5.054252] PNP: PS/2 appears to have AUX port disabled, if this is incorrect please boot with i8042.nopnp
[    5.054331] serio: i8042 KBD port at 0x60,0x64 irq 1
[    5.056535] mice: PS/2 mouse device common for all mice
[    5.068564] rtc_cmos 00:05: RTC can wake from S4
[    5.068592] rtc_cmos 00:05: rtc core: registered rtc_cmos as rtc0
[    5.068644] rtc0: alarms up to one year, y3k, 242 bytes nvram, hpet irqs
[    5.068689] device-mapper: uevent: version 1.0.3
[    5.068759] device-mapper: ioctl: 4.14.0-ioctl (2008-04-23) initialised: [EMAIL="dm-devel@redhat.com"]dm-devel@redhat.com[/EMAIL]
[    5.068891] device-mapper: multipath: version 1.0.5 loaded
[    5.068893] device-mapper: multipath round-robin: version 1.0.0 loaded
[    5.068978] EISA: Probing bus 0 at eisa.0
[    5.068983] Cannot allocate resource for EISA slot 1
[    5.068999] Cannot allocate resource for EISA slot 8
[    5.069000] EISA: Detected 0 cards.
[    5.069089] cpuidle: using governor ladder
[    5.069091] cpuidle: using governor menu
[    5.069471] TCP cubic registered
[    5.069544] NET: Registered protocol family 10
[    5.069858] lo: Disabled Privacy Extensions
[    5.070088] NET: Registered protocol family 17
[    5.070102] Bluetooth: L2CAP ver 2.11
[    5.070103] Bluetooth: L2CAP socket layer initialized
[    5.070106] Bluetooth: SCO (Voice Link) ver 0.6
[    5.070107] Bluetooth: SCO socket layer initialized
[    5.070146] Bluetooth: RFCOMM socket layer initialized
[    5.070152] Bluetooth: RFCOMM TTY layer initialized
[    5.070153] Bluetooth: RFCOMM ver 1.10
[    5.070194] powernow-k8: Found 1 AMD Athlon(tm) 64 X2 Dual Core Processor 5400+ processors (2 cpu cores) (version 2.20.00)
[    5.070212] [Firmware Bug]: powernow-k8: Your BIOS does not provide ACPI _PSS objects in a way that Linux understands. Please report this to the Linux ACPI maintainers and complain to your BIOS vendor.
[    5.070290] [Firmware Bug]: powernow-k8: Your BIOS does not provide ACPI _PSS objects in a way that Linux understands. Please report this to the Linux ACPI maintainers and complain to your BIOS vendor.
[    5.070367] Using IPI No-Shortcut mode
[    5.070425] registered taskstats version 1
[    5.070542]   Magic number: 14:639:286
[    5.070554] ppp ppp: hash matches
[    5.070670] rtc_cmos 00:05: setting system clock to 2010-06-03 16:15:10 UTC (1275581710)
[    5.070673] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    5.070674] EDD information not available.
[    5.070951] Freeing unused kernel memory: 532k freed
[    5.071083] Write protecting the kernel text: 4128k
[    5.071123] Write protecting the kernel read-only data: 1532k
[    5.087018] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input3
[    5.240631] usb 1-5: new high speed USB device using ehci_hcd and address 2
[    5.267721] ACPI: PCI Interrupt Link [APC4] enabled at IRQ 19
[    5.267733] ohci1394 0000:01:0a.0: PCI INT A -> Link[APC4] -> GSI 19 (level, low) -> IRQ 19
[    5.278627] forcedeth: Reverse Engineered nForce ethernet driver. Version 0.61.
[    5.279069] ACPI: PCI Interrupt Link [APCH] enabled at IRQ 22
[    5.279073] forcedeth 0000:00:0a.0: PCI INT A -> Link[APCH] -> GSI 22 (level, low) -> IRQ 22
[    5.279077] forcedeth 0000:00:0a.0: setting latency timer to 64
[    5.319469] ohci1394: fw-host0: OHCI-1394 1.0 (PCI): IRQ=[19]  MMIO=[fdeff000-fdeff7ff]  Max Packet=[2048]  IR/IT contexts=[8/8]
[    5.341823] forcedeth 0000:00:0a.0: ifname eth0, PHY OUI 0x732 @ 3, addr 00:22:15:f3:17:d3
[    5.341827] forcedeth 0000:00:0a.0: highdma csum pwrctl mgmt timirq gbit lnktim msi desc-v3
[    5.375439] usb 1-5: configuration #1 chosen from 1 choice
[    5.413067] Floppy drive(s): fd0 is 1.44M
[    5.432604] FDC 0 is a post-1991 82077
[    5.434884] Initializing USB Mass Storage driver...
[    5.459082] scsi8 : SCSI emulation for USB Mass Storage devices
[    5.461152] usbcore: registered new interface driver usb-storage
[    5.461156] USB Mass Storage support registered.
[    5.461236] usb-storage: device found at 2
[    5.461238] usb-storage: waiting for device to settle before scanning
[    5.614249] PM: Starting manual resume from disk
[    5.614252] PM: Resume from partition 8:5
[    5.614253] PM: Checking hibernation image.
[    5.614357] PM: Resume from disk failed.
[    5.636393] kjournald starting.  Commit interval 5 seconds
[    5.636409] EXT3-fs: mounted filesystem with ordered data mode.
[    5.744517] usb 4-1: new low speed USB device using ohci_hcd and address 2
[    5.958087] usb 4-1: configuration #1 chosen from 1 choice
[    6.648600] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[001e8c00017a4b04]
[    9.430647] udev: starting version 141
[    9.530297] usbcore: registered new interface driver hiddev
[    9.538630] input: Microsoft Microsoft Optical Mouse with Tilt Wheel as /devices/pci0000:00/0000:00:04.0/usb4/4-1/4-1:1.0/input/input4
[    9.560663] generic-usb 0003:045E:00D1.0001: input,hidraw0: USB HID v1.11 Mouse [Microsoft Microsoft Optical Mouse with Tilt Wheel] on usb-0000:00:04.0-1/input0
[    9.560683] usbcore: registered new interface driver usbhid
[    9.560700] usbhid: v2.6:USB HID core driver
[    9.751438] Linux agpgart interface v0.103
[    9.772386] Linux video capture interface: v2.00
[    9.788078] input: PC Speaker as /devices/platform/pcspkr/input/input5
[    9.972179] nvidia: module license 'NVIDIA' taints kernel.
[   10.224745] nvidia 0000:02:00.0: PCI INT A -> Link[AE0A] -> GSI 16 (level, low) -> IRQ 16
[   10.224752] nvidia 0000:02:00.0: setting latency timer to 64
[   10.228530] NVRM: loading NVIDIA UNIX x86 Kernel Module  180.44  Mon Mar 23 14:59:10 PST 2009
[   10.310236] ivtv:  Start initialization, version 1.4.0
[   10.310325] ivtv0: Initializing card #0
[   10.310330] ivtv0: Autodetected Hauppauge card (cx23416 based)
[   10.311793] ACPI: PCI Interrupt Link [APC2] enabled at IRQ 17
[   10.311806] ivtv 0000:01:09.0: PCI INT A -> Link[APC2] -> GSI 17 (level, low) -> IRQ 17
[   10.311813] ivtv0: Unreasonably low latency timer, setting to 64 (was 32)
[   10.361042] tveeprom 0-0050: Hauppauge model 26032, rev C599, serial# 8382976
[   10.361045] tveeprom 0-0050: tuner model is TCL 2002N 5H (idx 99, type 50)
[   10.361047] tveeprom 0-0050: TV standards NTSC(M) (eeprom 0x08)
[   10.361049] tveeprom 0-0050: audio processor is CX25841 (idx 35)
[   10.361051] tveeprom 0-0050: decoder processor is CX25841 (idx 28)
[   10.361053] tveeprom 0-0050: has no radio, has IR receiver, has IR transmitter
[   10.361055] ivtv0: Autodetected Hauppauge WinTV PVR-150
[   10.361056] ivtv0: Reopen i2c bus for IR-blaster support
[   10.418975] cx25840 0-0044: cx25841-23 found @ 0x88 (ivtv i2c driver #0)
[   10.431046] tuner 0-0061: chip found @ 0xc2 (ivtv i2c driver #0)
[   10.431067] wm8775 0-001b: chip found @ 0x36 (ivtv i2c driver #0)
[   10.464160] usb-storage: device scan complete
[   10.466359] scsi 8:0:0:0: Direct-Access     Generic  USB SD Reader    1.00 PQ: 0 ANSI: 0
[   10.466860] scsi 8:0:0:1: Direct-Access     Generic  USB CF Reader    1.01 PQ: 0 ANSI: 0
[   10.467483] scsi 8:0:0:2: Direct-Access     Generic  USB SM Reader    1.02 PQ: 0 ANSI: 0
[   10.468109] scsi 8:0:0:3: Direct-Access     Generic  USB MS Reader    1.03 PQ: 0 ANSI: 0
[   10.469525] sd 8:0:0:0: [sdc] Attached SCSI removable disk
[   10.469580] sd 8:0:0:0: Attached scsi generic sg3 type 0
[   10.470635] sd 8:0:0:1: [sdd] Attached SCSI removable disk
[   10.470691] sd 8:0:0:1: Attached scsi generic sg4 type 0
[   10.471831] sd 8:0:0:2: [sde] Attached SCSI removable disk
[   10.471887] sd 8:0:0:2: Attached scsi generic sg5 type 0
[   10.473822] sd 8:0:0:3: [sdf] Attached SCSI removable disk
[   10.473884] sd 8:0:0:3: Attached scsi generic sg6 type 0
[   10.480729] tuner-simple 0-0061: creating new instance
[   10.480733] tuner-simple 0-0061: type set to 50 (TCL 2002N)
[   10.482027] ivtv0: Registered device video0 for encoder MPG (4096 kB)
[   10.482064] ivtv0: Registered device video32 for encoder YUV (2048 kB)
[   10.482103] ivtv0: Registered device vbi0 for encoder VBI (1024 kB)
[   10.482138] ivtv0: Registered device video24 for encoder PCM (320 kB)
[   10.482140] ivtv0: Initialized card #0: Hauppauge WinTV PVR-150
[   10.482171] ivtv:  End initialization
[   10.522551] ACPI: PCI Interrupt Link [AAZA] enabled at IRQ 21
[   10.522557] HDA Intel 0000:00:07.0: PCI INT A -> Link[AAZA] -> GSI 21 (level, low) -> IRQ 21
[   10.522625] HDA Intel 0000:00:07.0: setting latency timer to 64
[   11.450754] lp: driver loaded but no devices found
[   11.538097] Adding 3229024k swap on /dev/sda5.  Priority:-1 extents:1 across:3229024k
[   12.078159] EXT3 FS on sda1, internal journal
[   12.856678] kjournald starting.  Commit interval 5 seconds
[   12.856686] EXT3-fs warning: maximal mount count reached, running e2fsck is recommended
[   12.857112] EXT3 FS on sdb5, internal journal
[   12.857116] EXT3-fs: mounted filesystem with ordered data mode.
[   13.203151] type=1505 audit(1275606918.629:2): operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" name2="default" pid=2369
[   13.243920] type=1505 audit(1275606918.669:3): operation="profile_load" name="/sbin/dhclient-script" name2="default" pid=2373
[   13.244053] type=1505 audit(1275606918.669:4): operation="profile_load" name="/sbin/dhclient3" name2="default" pid=2373
[   13.244093] type=1505 audit(1275606918.669:5): operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" name2="default" pid=2373
[   13.244129] type=1505 audit(1275606918.669:6): operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" name2="default" pid=2373
[   13.362242] type=1505 audit(1275606918.789:7): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=2378
[   13.362398] type=1505 audit(1275606918.789:8): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=2378
[   13.388414] type=1505 audit(1275606918.813:9): operation="profile_load" name="/usr/sbin/mysqld" name2="default" pid=2382
[   13.411215] type=1505 audit(1275606918.837:10): operation="profile_load" name="/usr/sbin/tcpdump" name2="default" pid=2386
[   19.854302] vboxdrv: Trying to deactivate the NMI watchdog permanently...
[   19.854305] vboxdrv: Successfully done.
[   19.854307] vboxdrv: Found 2 processor cores.
[   19.854365] vboxdrv: fAsync=1 offMin=0x6c4ce offMax=0x6c4ce
[   19.854407] vboxdrv: TSC mode is 'asynchronous', kernel timer mode is 'normal'.
[   19.854409] vboxdrv: Successfully loaded version 3.1.0 (interface 0x00100001).
[   21.704016] ivtv 0000:01:09.0: firmware: requesting v4l-cx2341x-enc.fw
[   21.767618] ivtv0: Loaded v4l-cx2341x-enc.fw firmware (376836 bytes)
[   21.964137] ivtv0: Encoder revision: 0x02060039
[   21.980869] cx25840 0-0044: firmware: requesting v4l-cx25840.fw
[   25.433793] cx25840 0-0044: loaded v4l-cx25840.fw firmware (16382 bytes)
[   28.620331] ppdev: user-space parallel port driver
[   32.571604] forcedeth 0000:00:0a.0: irq 2298 for MSI/MSI-X
[   42.752013] eth0: no IPv6 routers present













dmesg post burn




[    2.058026] ata1.00: 625142448 sectors, multi 16: LBA48 NCQ (depth 1)
[    2.058760] ata1.00: configured for UDMA/133
[    2.944018] ata2: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    2.952853] ata2.00: ATA-8: WDC WD10EADS-00M2B0, 01.00A01, max UDMA/133
[    2.952856] ata2.00: 1953525168 sectors, multi 16: LBA48 NCQ (depth 31/32)
[    2.954610] ata2.00: configured for UDMA/133
[    3.272016] ata3: SATA link down (SStatus 0 SControl 300)
[    3.592015] ata4: SATA link down (SStatus 0 SControl 300)
[    3.912015] ata5: SATA link down (SStatus 0 SControl 300)
[    4.232015] ata6: SATA link down (SStatus 0 SControl 300)
[    4.232104] scsi 0:0:0:0: Direct-Access     ATA      WDC WD3200KS-00P 21.0 PQ: 0 ANSI: 5
[    4.232180] sd 0:0:0:0: [sda] 625142448 512-byte hardware sectors: (320 GB/298 GiB)
[    4.232193] sd 0:0:0:0: [sda] Write Protect is off
[    4.232195] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    4.232214] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    4.232271] sd 0:0:0:0: [sda] 625142448 512-byte hardware sectors: (320 GB/298 GiB)
[    4.232282] sd 0:0:0:0: [sda] Write Protect is off
[    4.232284] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    4.232302] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    4.232305]  sda: sda1 sda2 < sda5 >
[    4.248786] sd 0:0:0:0: [sda] Attached SCSI disk
[    4.248825] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    4.248875] scsi 1:0:0:0: Direct-Access     ATA      WDC WD10EADS-00M 01.0 PQ: 0 ANSI: 5
[    4.248939] sd 1:0:0:0: [sdb] 1953525168 512-byte hardware sectors: (1.00 TB/931 GiB)
[    4.248950] sd 1:0:0:0: [sdb] Write Protect is off
[    4.248952] sd 1:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[    4.248969] sd 1:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    4.249006] sd 1:0:0:0: [sdb] 1953525168 512-byte hardware sectors: (1.00 TB/931 GiB)
[    4.249016] sd 1:0:0:0: [sdb] Write Protect is off
[    4.249018] sd 1:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[    4.249035] sd 1:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    4.249038]  sdb: sdb1 < sdb5 >
[    4.262231] sd 1:0:0:0: [sdb] Attached SCSI disk
[    4.262259] sd 1:0:0:0: Attached scsi generic sg1 type 0
[    4.262448] pata_amd 0000:00:06.0: version 0.3.10
[    4.262481] pata_amd 0000:00:06.0: setting latency timer to 64
[    4.262554] scsi6 : pata_amd
[    4.262608] scsi7 : pata_amd
[    4.263281] ata7: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xf000 irq 14
[    4.263283] ata8: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xf008 irq 15
[    4.424300] ata7.00: ATAPI: ASUS    DRW-1612BL, 1.06, max UDMA/66
[    4.424318] ata7: nv_mode_filter: 0x1f39f&0x1f01f->0x1f01f, BIOS=0x1f000 (0xc5000000) ACPI=0x1f01f (30:600:0x13)
[    4.440242] ata7.00: configured for UDMA/66
[    4.440471] ata8: port disabled. ignoring.
[    4.440957] scsi 6:0:0:0: CD-ROM            ASUS     DRW-1612BL       1.06 PQ: 0 ANSI: 5
[    4.444037] sr0: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
[    4.444039] Uniform CD-ROM driver Revision: 3.20
[    4.444115] sr 6:0:0:0: Attached scsi CD-ROM sr0
[    4.444146] sr 6:0:0:0: Attached scsi generic sg2 type 5
[    4.444533] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    4.444947] ACPI: PCI Interrupt Link [AUB2] enabled at IRQ 22
[    4.444956] ehci_hcd 0000:00:02.1: PCI INT B -> Link[AUB2] -> GSI 22 (level, low) -> IRQ 22
[    4.444972] ehci_hcd 0000:00:02.1: setting latency timer to 64
[    4.444975] ehci_hcd 0000:00:02.1: EHCI Host Controller
[    4.445021] ehci_hcd 0000:00:02.1: new USB bus registered, assigned bus number 1
[    4.445045] ehci_hcd 0000:00:02.1: debug port 1
[    4.445048] ehci_hcd 0000:00:02.1: cache line size of 64 is not supported
[    4.445065] ehci_hcd 0000:00:02.1: irq 22, io mem 0xfe02e000
[    4.456017] ehci_hcd 0000:00:02.1: USB 2.0 started, EHCI 1.00
[    4.456074] usb usb1: configuration #1 chosen from 1 choice
[    4.456095] hub 1-0:1.0: USB hub found
[    4.456102] hub 1-0:1.0: 6 ports detected
[    4.456416] ACPI: PCI Interrupt Link [AU2B] disabled and referenced, BIOS bug
[    4.456584] ACPI: PCI Interrupt Link [AU2B] enabled at IRQ 21
[    4.456591] ehci_hcd 0000:00:04.1: PCI INT B -> Link[AU2B] -> GSI 21 (level, low) -> IRQ 21
[    4.456599] ehci_hcd 0000:00:04.1: setting latency timer to 64
[    4.456602] ehci_hcd 0000:00:04.1: EHCI Host Controller
[    4.456639] ehci_hcd 0000:00:04.1: new USB bus registered, assigned bus number 2
[    4.456658] ehci_hcd 0000:00:04.1: debug port 1
[    4.456662] ehci_hcd 0000:00:04.1: cache line size of 64 is not supported
[    4.456676] ehci_hcd 0000:00:04.1: irq 21, io mem 0xfe02c000
[    4.468015] ehci_hcd 0000:00:04.1: USB 2.0 started, EHCI 1.00
[    4.468058] usb usb2: configuration #1 chosen from 1 choice
[    4.468076] hub 2-0:1.0: USB hub found
[    4.468082] hub 2-0:1.0: 6 ports detected
[    4.468153] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    4.468555] ACPI: PCI Interrupt Link [AUBA] enabled at IRQ 20
[    4.468562] ohci_hcd 0000:00:02.0: PCI INT A -> Link[AUBA] -> GSI 20 (level, low) -> IRQ 20
[    4.468571] ohci_hcd 0000:00:02.0: setting latency timer to 64
[    4.468573] ohci_hcd 0000:00:02.0: OHCI Host Controller
[    4.468608] ohci_hcd 0000:00:02.0: new USB bus registered, assigned bus number 3
[    4.468627] ohci_hcd 0000:00:02.0: irq 20, io mem 0xfe02f000
[    4.526037] usb usb3: configuration #1 chosen from 1 choice
[    4.526056] hub 3-0:1.0: USB hub found
[    4.526063] hub 3-0:1.0: 6 ports detected
[    4.526508] ACPI: PCI Interrupt Link [AU1B] enabled at IRQ 23
[    4.526511] ohci_hcd 0000:00:04.0: PCI INT A -> Link[AU1B] -> GSI 23 (level, low) -> IRQ 23
[    4.526519] ohci_hcd 0000:00:04.0: setting latency timer to 64
[    4.526521] ohci_hcd 0000:00:04.0: OHCI Host Controller
[    4.526560] ohci_hcd 0000:00:04.0: new USB bus registered, assigned bus number 4
[    4.526579] ohci_hcd 0000:00:04.0: irq 23, io mem 0xfe02d000
[    4.582031] usb usb4: configuration #1 chosen from 1 choice
[    4.582048] hub 4-0:1.0: USB hub found
[    4.582055] hub 4-0:1.0: 6 ports detected
[    4.582123] uhci_hcd: USB Universal Host Controller Interface driver
[    4.582174] usbcore: registered new interface driver libusual
[    4.582198] usbcore: registered new interface driver usbserial
[    4.582206] USB Serial support registered for generic
[    4.582216] usbcore: registered new interface driver usbserial_generic
[    4.582218] usbserial: USB Serial Driver core
[    4.582248] PNP: PS/2 Controller [PNP0303:PS2K] at 0x60,0x64 irq 1
[    4.582250] PNP: PS/2 appears to have AUX port disabled, if this is incorrect please boot with i8042.nopnp
[    4.582328] serio: i8042 KBD port at 0x60,0x64 irq 1
[    4.584536] mice: PS/2 mouse device common for all mice
[    4.596564] rtc_cmos 00:05: RTC can wake from S4
[    4.596592] rtc_cmos 00:05: rtc core: registered rtc_cmos as rtc0
[    4.596644] rtc0: alarms up to one year, y3k, 242 bytes nvram, hpet irqs
[    4.596690] device-mapper: uevent: version 1.0.3
[    4.596759] device-mapper: ioctl: 4.14.0-ioctl (2008-04-23) initialised: [EMAIL="dm-devel@redhat.com"]dm-devel@redhat.com[/EMAIL]
[    4.596890] device-mapper: multipath: version 1.0.5 loaded
[    4.596892] device-mapper: multipath round-robin: version 1.0.0 loaded
[    4.596976] EISA: Probing bus 0 at eisa.0
[    4.596982] Cannot allocate resource for EISA slot 1
[    4.596998] Cannot allocate resource for EISA slot 8
[    4.596999] EISA: Detected 0 cards.
[    4.597088] cpuidle: using governor ladder
[    4.597089] cpuidle: using governor menu
[    4.597470] TCP cubic registered
[    4.597544] NET: Registered protocol family 10
[    4.597857] lo: Disabled Privacy Extensions
[    4.598087] NET: Registered protocol family 17
[    4.598101] Bluetooth: L2CAP ver 2.11
[    4.598103] Bluetooth: L2CAP socket layer initialized
[    4.598105] Bluetooth: SCO (Voice Link) ver 0.6
[    4.598106] Bluetooth: SCO socket layer initialized
[    4.598145] Bluetooth: RFCOMM socket layer initialized
[    4.598152] Bluetooth: RFCOMM TTY layer initialized
[    4.598153] Bluetooth: RFCOMM ver 1.10
[    4.598194] powernow-k8: Found 1 AMD Athlon(tm) 64 X2 Dual Core Processor 5400+ processors (2 cpu cores) (version 2.20.00)
[    4.598212] [Firmware Bug]: powernow-k8: Your BIOS does not provide ACPI _PSS objects in a way that Linux understands. Please report this to the Linux ACPI maintainers and complain to your BIOS vendor.
[    4.598289] [Firmware Bug]: powernow-k8: Your BIOS does not provide ACPI _PSS objects in a way that Linux understands. Please report this to the Linux ACPI maintainers and complain to your BIOS vendor.
[    4.598366] Using IPI No-Shortcut mode
[    4.598425] registered taskstats version 1
[    4.598542]   Magic number: 10:240:655
[    4.598584] pci_link PNP0C0F:4b: hash matches
[    4.598671] rtc_cmos 00:05: setting system clock to 2010-05-31 22:37:48 UTC (1275345468)
[    4.598673] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    4.598674] EDD information not available.
[    4.598950] Freeing unused kernel memory: 532k freed
[    4.599066] Write protecting the kernel text: 4128k
[    4.599106] Write protecting the kernel read-only data: 1532k
[    4.615749] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input3
[    4.769305] usb 1-5: new high speed USB device using ehci_hcd and address 2
[    4.806562] ACPI: PCI Interrupt Link [APC4] enabled at IRQ 19
[    4.806574] ohci1394 0000:01:0a.0: PCI INT A -> Link[APC4] -> GSI 19 (level, low) -> IRQ 19
[    4.858328] ohci1394: fw-host0: OHCI-1394 1.0 (PCI): IRQ=[19]  MMIO=[fdeff000-fdeff7ff]  Max Packet=[2048]  IR/IT contexts=[8/8]
[    4.915774] Floppy drive(s): fd0 is 1.44M
[    4.933307] forcedeth: Reverse Engineered nForce ethernet driver. Version 0.61.
[    4.933749] ACPI: PCI Interrupt Link [APCH] enabled at IRQ 22
[    4.933753] forcedeth 0000:00:0a.0: PCI INT A -> Link[APCH] -> GSI 22 (level, low) -> IRQ 22
[    4.933757] forcedeth 0000:00:0a.0: setting latency timer to 64
[    4.936042] FDC 0 is a post-1991 82077
[    4.941907] usb 1-5: configuration #1 chosen from 1 choice
[    4.959790] Initializing USB Mass Storage driver...
[    4.959890] scsi8 : SCSI emulation for USB Mass Storage devices
[    4.959958] usbcore: registered new interface driver usb-storage
[    4.959961] USB Mass Storage support registered.
[    4.960072] usb-storage: device found at 2
[    4.960073] usb-storage: waiting for device to settle before scanning
[    4.997805] forcedeth 0000:00:0a.0: ifname eth0, PHY OUI 0x732 @ 3, addr 00:22:15:f3:17:d3
[    4.997809] forcedeth 0000:00:0a.0: highdma csum pwrctl mgmt timirq gbit lnktim msi desc-v3
[    5.146126] PM: Starting manual resume from disk
[    5.146129] PM: Resume from partition 8:5
[    5.146131] PM: Checking hibernation image.
[    5.146253] PM: Resume from disk failed.
[    5.193221] kjournald starting.  Commit interval 5 seconds
[    5.193230] EXT3-fs: mounted filesystem with ordered data mode.
[    5.316519] usb 4-1: new low speed USB device using ohci_hcd and address 2
[    5.530089] usb 4-1: configuration #1 chosen from 1 choice
[    6.136182] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[001e8c00017a4b04]
[    8.987476] udev: starting version 141
[    9.247531] usbcore: registered new interface driver hiddev
[    9.255609] input: Microsoft Microsoft Optical Mouse with Tilt Wheel as /devices/pci0000:00/0000:00:04.0/usb4/4-1/4-1:1.0/input/input4
[    9.284613] generic-usb 0003:045E:00D1.0001: input,hidraw0: USB HID v1.11 Mouse [Microsoft Microsoft Optical Mouse with Tilt Wheel] on usb-0000:00:04.0-1/input0
[    9.284632] usbcore: registered new interface driver usbhid
[    9.284635] usbhid: v2.6:USB HID core driver
[    9.336639] input: PC Speaker as /devices/platform/pcspkr/input/input5
[    9.349839] Linux agpgart interface v0.103
[    9.370786] Linux video capture interface: v2.00
[    9.653604] nvidia: module license 'NVIDIA' taints kernel.
[    9.906171] nvidia 0000:02:00.0: PCI INT A -> Link[AE0A] -> GSI 16 (level, low) -> IRQ 16
[    9.906178] nvidia 0000:02:00.0: setting latency timer to 64
[    9.907434] NVRM: loading NVIDIA UNIX x86 Kernel Module  180.44  Mon Mar 23 14:59:10 PST 2009
[    9.956120] usb-storage: device scan complete
[    9.959888] scsi 8:0:0:0: Direct-Access     Generic  USB SD Reader    1.00 PQ: 0 ANSI: 0
[    9.960483] scsi 8:0:0:1: Direct-Access     Generic  USB CF Reader    1.01 PQ: 0 ANSI: 0
[    9.961245] scsi 8:0:0:2: Direct-Access     Generic  USB SM Reader    1.02 PQ: 0 ANSI: 0
[    9.961973] scsi 8:0:0:3: Direct-Access     Generic  USB MS Reader    1.03 PQ: 0 ANSI: 0
[    9.963104] sd 8:0:0:0: [sdc] Attached SCSI removable disk
[    9.963157] sd 8:0:0:0: Attached scsi generic sg3 type 0
[    9.963964] sd 8:0:0:1: [sdd] Attached SCSI removable disk
[    9.964039] sd 8:0:0:1: Attached scsi generic sg4 type 0
[    9.965018] sd 8:0:0:2: [sde] Attached SCSI removable disk
[    9.965074] sd 8:0:0:2: Attached scsi generic sg5 type 0
[    9.971689] sd 8:0:0:3: [sdf] Attached SCSI removable disk
[    9.971743] sd 8:0:0:3: Attached scsi generic sg6 type 0
[    9.991979] ivtv:  Start initialization, version 1.4.0
[    9.992056] ivtv0: Initializing card #0
[    9.992059] ivtv0: Autodetected Hauppauge card (cx23416 based)
[    9.995368] ACPI: PCI Interrupt Link [APC2] enabled at IRQ 17
[    9.995380] ivtv 0000:01:09.0: PCI INT A -> Link[APC2] -> GSI 17 (level, low) -> IRQ 17
[    9.995387] ivtv0: Unreasonably low latency timer, setting to 64 (was 32)
[   10.044770] tveeprom 0-0050: Hauppauge model 26032, rev C599, serial# 8382976
[   10.044773] tveeprom 0-0050: tuner model is TCL 2002N 5H (idx 99, type 50)
[   10.044776] tveeprom 0-0050: TV standards NTSC(M) (eeprom 0x08)
[   10.044777] tveeprom 0-0050: audio processor is CX25841 (idx 35)
[   10.044779] tveeprom 0-0050: decoder processor is CX25841 (idx 28)
[   10.044781] tveeprom 0-0050: has no radio, has IR receiver, has IR transmitter
[   10.044783] ivtv0: Autodetected Hauppauge WinTV PVR-150
[   10.044785] ivtv0: Reopen i2c bus for IR-blaster support
[   10.084224] cx25840 0-0044: cx25841-23 found @ 0x88 (ivtv i2c driver #0)
[   10.096326] tuner 0-0061: chip found @ 0xc2 (ivtv i2c driver #0)
[   10.096348] wm8775 0-001b: chip found @ 0x36 (ivtv i2c driver #0)
[   10.121151] tuner-simple 0-0061: creating new instance
[   10.121155] tuner-simple 0-0061: type set to 50 (TCL 2002N)
[   10.122442] ivtv0: Registered device video0 for encoder MPG (4096 kB)
[   10.122481] ivtv0: Registered device video32 for encoder YUV (2048 kB)
[   10.122521] ivtv0: Registered device vbi0 for encoder VBI (1024 kB)
[   10.122559] ivtv0: Registered device video24 for encoder PCM (320 kB)
[   10.122561] ivtv0: Initialized card #0: Hauppauge WinTV PVR-150
[   10.122596] ivtv:  End initialization
[   10.162618] ACPI: PCI Interrupt Link [AAZA] enabled at IRQ 21
[   10.162624] HDA Intel 0000:00:07.0: PCI INT A -> Link[AAZA] -> GSI 21 (level, low) -> IRQ 21
[   10.162686] HDA Intel 0000:00:07.0: setting latency timer to 64
[   11.065888] lp: driver loaded but no devices found
[   11.153274] Adding 3229024k swap on /dev/sda5.  Priority:-1 extents:1 across:3229024k
[   11.683816] EXT3 FS on sda1, internal journal
[   12.468902] kjournald starting.  Commit interval 5 seconds
[   12.468911] EXT3-fs warning: maximal mount count reached, running e2fsck is recommended
[   12.469318] EXT3 FS on sdb5, internal journal
[   12.469320] EXT3-fs: recovery complete.
[   12.469437] EXT3-fs: mounted filesystem with ordered data mode.
[   12.717613] type=1505 audit(1275370676.617:2): operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" name2="default" pid=2358
[   12.758268] type=1505 audit(1275370676.657:3): operation="profile_load" name="/sbin/dhclient-script" name2="default" pid=2362
[   12.758375] type=1505 audit(1275370676.657:4): operation="profile_load" name="/sbin/dhclient3" name2="default" pid=2362
[   12.758414] type=1505 audit(1275370676.657:5): operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" name2="default" pid=2362
[   12.758453] type=1505 audit(1275370676.657:6): operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" name2="default" pid=2362
[   12.884826] type=1505 audit(1275370676.785:7): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=2367
[   12.884986] type=1505 audit(1275370676.785:8): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=2367
[   12.920500] type=1505 audit(1275370676.821:9): operation="profile_load" name="/usr/sbin/mysqld" name2="default" pid=2371
[   12.943230] type=1505 audit(1275370676.841:10): operation="profile_load" name="/usr/sbin/tcpdump" name2="default" pid=2375
[   19.586289] vboxdrv: Trying to deactivate the NMI watchdog permanently...
[   19.586292] vboxdrv: Successfully done.
[   19.586294] vboxdrv: Found 2 processor cores.
[   19.587343] vboxdrv: fAsync=1 offMin=0x56af7 offMax=0x56af7
[   19.587397] vboxdrv: TSC mode is 'asynchronous', kernel timer mode is 'normal'.
[   19.587399] vboxdrv: Successfully loaded version 3.1.0 (interface 0x00100001).
[   20.228525] usb 2-2: new high speed USB device using ehci_hcd and address 3
[   20.361895] usb 2-2: configuration #1 chosen from 1 choice
[   20.364035] scsi9 : SCSI emulation for USB Mass Storage devices
[   20.364339] usb-storage: device found at 3
[   20.364342] usb-storage: waiting for device to settle before scanning
[   21.404017] ivtv 0000:01:09.0: firmware: requesting v4l-cx2341x-enc.fw
[   21.458069] ivtv0: Loaded v4l-cx2341x-enc.fw firmware (376836 bytes)
[   21.656134] ivtv0: Encoder revision: 0x02060039
[   21.672894] cx25840 0-0044: firmware: requesting v4l-cx25840.fw
[   25.124597] cx25840 0-0044: loaded v4l-cx25840.fw firmware (16382 bytes)
[   25.368226] usb-storage: device scan complete
[   25.370348] scsi 9:0:0:0: Direct-Access     WDC WD50 00BEVT-22A0RT0   1A01 PQ: 0 ANSI: 2 CCS
[   25.372458] sd 9:0:0:0: [sdg] 976773168 512-byte hardware sectors: (500 GB/465 GiB)
[   25.375212] sd 9:0:0:0: [sdg] Write Protect is off
[   25.375216] sd 9:0:0:0: [sdg] Mode Sense: 00 38 00 00
[   25.375218] sd 9:0:0:0: [sdg] Assuming drive cache: write through
[   25.376958] sd 9:0:0:0: [sdg] 976773168 512-byte hardware sectors: (500 GB/465 GiB)
[   25.378196] sd 9:0:0:0: [sdg] Write Protect is off
[   25.378198] sd 9:0:0:0: [sdg] Mode Sense: 00 38 00 00
[   25.378200] sd 9:0:0:0: [sdg] Assuming drive cache: write through
[   25.378204]  sdg: sdg1
[   27.095953] sd 9:0:0:0: [sdg] Attached SCSI disk
[   27.096009] sd 9:0:0:0: Attached scsi generic sg7 type 0
[   28.592760] ppdev: user-space parallel port driver
[   32.100263] forcedeth 0000:00:0a.0: irq 2298 for MSI/MSI-X
[   42.536518] eth0: no IPv6 routers present
[   89.369336] warning: `VirtualBox' uses 32-bit capabilities (legacy support in use)
[   94.181780] device eth0 entered promiscuous mode
[  102.621993] usb 2-2: USB disconnect, address 3
[  119.775996] hda-intel: IRQ timing workaround is activated for card #0. Suggest a bigger bdl_pos_adj.
[  120.028524] usb 2-2: new high speed USB device using ehci_hcd and address 4
[  120.168305] usb 2-2: configuration #1 chosen from 1 choice
[  120.172579] scsi10 : SCSI emulation for USB Mass Storage devices
[  120.173845] usb-storage: device found at 4
[  120.173848] usb-storage: waiting for device to settle before scanning
[  125.172779] usb-storage: device scan complete
[  125.174168] scsi 10:0:0:0: Direct-Access                                    PQ: 0 ANSI: 2 CCS
[  125.229690] sd 10:0:0:0: [sdg] Attached SCSI disk
[  125.229747] sd 10:0:0:0: Attached scsi generic sg7 type 0
[30530.017593] usb 2-2: USB disconnect, address 4
[30783.039447] end_request: I/O error, dev sr0, sector 0
[30783.039453] Buffer I/O error on device sr0, logical block 0
[30783.039456] Buffer I/O error on device sr0, logical block 1
[30783.039459] Buffer I/O error on device sr0, logical block 2
[30783.039461] Buffer I/O error on device sr0, logical block 3
[30783.039463] Buffer I/O error on device sr0, logical block 4
[30783.039465] Buffer I/O error on device sr0, logical block 5
[30783.039468] Buffer I/O error on device sr0, logical block 6
[30783.039470] Buffer I/O error on device sr0, logical block 7
[30783.039474] Buffer I/O error on device sr0, logical block 8
[30783.039477] Buffer I/O error on device sr0, logical block 9
[30783.047662] sr 6:0:0:0: [sr0] unaligned transfer
[30783.047677] sr 6:0:0:0: [sr0] unaligned transfer
[30783.047688] sr 6:0:0:0: [sr0] unaligned transfer
[30783.154148] cdrom: This disc doesn't have any tracks I recognize!
[30783.169795] end_request: I/O error, dev sr0, sector 0
[30783.190054] sr 6:0:0:0: [sr0] unaligned transfer
[30783.190065] sr 6:0:0:0: [sr0] unaligned transfer
[30783.190075] sr 6:0:0:0: [sr0] unaligned transfer
[30783.190093] sr 6:0:0:0: [sr0] unaligned transfer
[30783.190097] sr 6:0:0:0: [sr0] unaligned transfer
[30783.190102] sr 6:0:0:0: [sr0] unaligned transfer
[30783.190106] sr 6:0:0:0: [sr0] unaligned transfer
[30783.190111] sr 6:0:0:0: [sr0] unaligned transfer
[30783.190115] sr 6:0:0:0: [sr0] unaligned transfer
[30783.190120] sr 6:0:0:0: [sr0] unaligned transfer
[30783.190124] sr 6:0:0:0: [sr0] unaligned transfer
[30783.288538] end_request: I/O error, dev sr0, sector 0
[30783.314244] sr 6:0:0:0: [sr0] unaligned transfer
[30783.314255] sr 6:0:0:0: [sr0] unaligned transfer
[30783.314266] sr 6:0:0:0: [sr0] unaligned transfer
[30783.316643] sr 6:0:0:0: [sr0] unaligned transfer
[30783.316659] sr 6:0:0:0: [sr0] unaligned transfer
[30783.316665] sr 6:0:0:0: [sr0] unaligned transfer
[30783.316672] sr 6:0:0:0: [sr0] unaligned transfer
[30783.316678] sr 6:0:0:0: [sr0] unaligned transfer
[30783.316685] sr 6:0:0:0: [sr0] unaligned transfer
[30783.316691] sr 6:0:0:0: [sr0] unaligned transfer
[30783.316697] sr 6:0:0:0: [sr0] unaligned transfer
[30783.316705] sr 6:0:0:0: [sr0] unaligned transfer
[30783.316711] sr 6:0:0:0: [sr0] unaligned transfer
[30783.316717] sr 6:0:0:0: [sr0] unaligned transfer
[30783.316724] sr 6:0:0:0: [sr0] unaligned transfer
[30783.316730] sr 6:0:0:0: [sr0] unaligned transfer
[30783.316736] sr 6:0:0:0: [sr0] unaligned transfer
[30783.316742] sr 6:0:0:0: [sr0] unaligned transfer
[30783.316748] sr 6:0:0:0: [sr0] unaligned transfer
[30783.908371] sr 6:0:0:0: [sr0] unaligned transfer
[30783.908385] sr 6:0:0:0: [sr0] unaligned transfer
[30783.908391] sr 6:0:0:0: [sr0] unaligned transfer
[30783.908395] sr 6:0:0:0: [sr0] unaligned transfer
[30783.908400] sr 6:0:0:0: [sr0] unaligned transfer
[30783.908405] sr 6:0:0:0: [sr0] unaligned transfer
[30783.908410] sr 6:0:0:0: [sr0] unaligned transfer
[30783.908415] sr 6:0:0:0: [sr0] unaligned transfer
[126058.500013] Clocksource tsc unstable (delta = 62501278 ns)
[209207.764928] sr 6:0:0:0: [sr0] unaligned transfer
[209207.764933] __ratelimit: 94 callbacks suppressed
[209207.764936] Buffer I/O error on device sr0, logical block 0
[209207.764945] sr 6:0:0:0: [sr0] unaligned transfer
[209207.764947] Buffer I/O error on device sr0, logical block 1
[209207.764952] sr 6:0:0:0: [sr0] unaligned transfer
[209207.764954] Buffer I/O error on device sr0, logical block 2
[209207.764959] sr 6:0:0:0: [sr0] unaligned transfer
[209207.764961] Buffer I/O error on device sr0, logical block 3
[209207.764965] sr 6:0:0:0: [sr0] unaligned transfer
[209207.764967] Buffer I/O error on device sr0, logical block 4
[209207.764971] sr 6:0:0:0: [sr0] unaligned transfer
[209207.764973] Buffer I/O error on device sr0, logical block 5
[209207.764978] sr 6:0:0:0: [sr0] unaligned transfer
[209207.764979] Buffer I/O error on device sr0, logical block 6
[209207.764984] sr 6:0:0:0: [sr0] unaligned transfer
[209207.764986] Buffer I/O error on device sr0, logical block 7
[209207.764992] sr 6:0:0:0: [sr0] unaligned transfer
[209207.764994] Buffer I/O error on device sr0, logical block 8
[209207.764998] sr 6:0:0:0: [sr0] unaligned transfer
[209207.765000] Buffer I/O error on device sr0, logical block 9
[209207.765005] sr 6:0:0:0: [sr0] unaligned transfer
[209207.765009] sr 6:0:0:0: [sr0] unaligned transfer
[209207.765014] sr 6:0:0:0: [sr0] unaligned transfer
[209207.765019] sr 6:0:0:0: [sr0] unaligned transfer
[209207.765024] sr 6:0:0:0: [sr0] unaligned transfer
[209207.765028] sr 6:0:0:0: [sr0] unaligned transfer
[209207.765035] sr 6:0:0:0: [sr0] unaligned transfer
[209207.765040] sr 6:0:0:0: [sr0] unaligned transfer
[209207.765045] sr 6:0:0:0: [sr0] unaligned transfer
[209207.765049] sr 6:0:0:0: [sr0] unaligned transfer
[209207.765054] sr 6:0:0:0: [sr0] unaligned transfer
[209207.765059] sr 6:0:0:0: [sr0] unaligned transfer
[209207.765064] sr 6:0:0:0: [sr0] unaligned transfer
[209207.765068] sr 6:0:0:0: [sr0] unaligned transfer
[209207.765075] sr 6:0:0:0: [sr0] unaligned transfer
[209207.765080] sr 6:0:0:0: [sr0] unaligned transfer
[209207.765085] sr 6:0:0:0: [sr0] unaligned transfer
[209207.765089] sr 6:0:0:0: [sr0] unaligned transfer
[209207.765094] sr 6:0:0:0: [sr0] unaligned transfer
[209207.765099] sr 6:0:0:0: [sr0] unaligned transfer
[209207.765103] sr 6:0:0:0: [sr0] unaligned transfer
[209207.765108] sr 6:0:0:0: [sr0] unaligned transfer
[209207.765113] sr 6:0:0:0: [sr0] unaligned transfer
[209207.765118] sr 6:0:0:0: [sr0] unaligned transfer
[209207.765122] sr 6:0:0:0: [sr0] unaligned transfer
[209207.765127] sr 6:0:0:0: [sr0] unaligned transfer
[209207.765131] sr 6:0:0:0: [sr0] unaligned transfer
[209207.765136] sr 6:0:0:0: [sr0] unaligned transfer
[209207.765140] sr 6:0:0:0: [sr0] unaligned transfer
[209207.765145] sr 6:0:0:0: [sr0] unaligned transfer
[209207.887482] end_request: I/O error, dev sr0, sector 0
[209207.891541] sr 6:0:0:0: [sr0] unaligned transfer
[209207.891555] sr 6:0:0:0: [sr0] unaligned transfer
[209207.891560] sr 6:0:0:0: [sr0] unaligned transfer
[209207.891565] sr 6:0:0:0: [sr0] unaligned transfer
[209207.891570] sr 6:0:0:0: [sr0] unaligned transfer
[209207.891575] sr 6:0:0:0: [sr0] unaligned transfer
[209207.891579] sr 6:0:0:0: [sr0] unaligned transfer
[209207.891584] sr 6:0:0:0: [sr0] unaligned transfer
[209207.891590] sr 6:0:0:0: [sr0] unaligned transfer
[209207.891594] sr 6:0:0:0: [sr0] unaligned transfer
[209207.891599] sr 6:0:0:0: [sr0] unaligned transfer
[209207.891604] sr 6:0:0:0: [sr0] unaligned transfer
[209207.891608] sr 6:0:0:0: [sr0] unaligned transfer
[209207.891613] sr 6:0:0:0: [sr0] unaligned transfer
[209207.891617] sr 6:0:0:0: [sr0] unaligned transfer
[209207.891622] sr 6:0:0:0: [sr0] unaligned transfer
[209207.893138] sr 6:0:0:0: [sr0] unaligned transfer
[209207.893146] sr 6:0:0:0: [sr0] unaligned transfer
[209207.893151] sr 6:0:0:0: [sr0] unaligned transfer
[209207.893156] sr 6:0:0:0: [sr0] unaligned transfer
[209207.893160] sr 6:0:0:0: [sr0] unaligned transfer
[209207.893165] sr 6:0:0:0: [sr0] unaligned transfer
[209207.893169] sr 6:0:0:0: [sr0] unaligned transfer
[209207.893174] sr 6:0:0:0: [sr0] unaligned transfer
[209208.369675] cdrom: This disc doesn't have any tracks I recognize!
[209208.390521] sr 6:0:0:0: [sr0] unaligned transfer
[209208.390532] sr 6:0:0:0: [sr0] unaligned transfer
[209208.390537] sr 6:0:0:0: [sr0] unaligned transfer
[209208.390541] sr 6:0:0:0: [sr0] unaligned transfer
[209208.390546] sr 6:0:0:0: [sr0] unaligned transfer
[209208.390550] sr 6:0:0:0: [sr0] unaligned transfer
[209208.390555] sr 6:0:0:0: [sr0] unaligned transfer
[209208.390559] sr 6:0:0:0: [sr0] unaligned transfer
[209208.410464] sr 6:0:0:0: [sr0] unaligned transfer
[209208.410474] sr 6:0:0:0: [sr0] unaligned transfer
[209208.410479] sr 6:0:0:0: [sr0] unaligned transfer
[209208.410483] sr 6:0:0:0: [sr0] unaligned transfer
[209208.410488] sr 6:0:0:0: [sr0] unaligned transfer
[209208.410493] sr 6:0:0:0: [sr0] unaligned transfer
[209208.410497] sr 6:0:0:0: [sr0] unaligned transfer
[209208.410502] sr 6:0:0:0: [sr0] unaligned transfer
[209208.410517] sr 6:0:0:0: [sr0] unaligned transfer
[209208.410522] sr 6:0:0:0: [sr0] unaligned transfer
[209208.410526] sr 6:0:0:0: [sr0] unaligned transfer
[209208.410530] sr 6:0:0:0: [sr0] unaligned transfer
[209208.410535] sr 6:0:0:0: [sr0] unaligned transfer
[209208.410540] sr 6:0:0:0: [sr0] unaligned transfer
[209208.410544] sr 6:0:0:0: [sr0] unaligned transfer
[209208.410549] sr 6:0:0:0: [sr0] unaligned transfer

---

### Post by jm321 on 2010-06-03
Ummm so I just tried to burn a CD (after a reboot) and the CDRW blew up into a million peices while it was being burnt!  That was loud!  

Are Kodak CDRW's bad not good quality?

I have a new DVD burner on order from NCIX, it was reviewed on newegg as being 100% compatible with Ubuntu by numerous posts.  I'll install and report back if the issues continue!

---

### Post by Jeroensum on 2010-06-04
AH-HAH!
Your drive just **knew** it was gonna get busted and crapped out on you... pretty much a luser attitude for a dvd-drive but no way to do anything about it now...

As far as I know kodak discs, they never gave me or any of my clients problems. But there's a time for every new experience ;) 

Hope your new drive brings you new joy and less broken disks)  :o)

I'll  check this thread in about a week (and a bit) to see if the problem still exists with the new drive or not.

---

