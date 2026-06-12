---
title: "Seg Fault in Nautilus - Jaunty AMD_64"
date: 2009-10-30
forum: General Help
---

### Post by lidex on 2009-10-30
Nautilus quickly dies when clicking on link for network or computer. Terminal output:
```
lidex@q5u5k5:~$ nautilus
** Message: Initializing gksu extension...

(nautilus:7278): GLib-GIO-CRITICAL **: g_file_info_get_name: assertion `G_IS_FILE_INFO (info)' failed

** (nautilus:7278): WARNING **: Got GFileInfo with NULL name in computer:///, ignoring. This shouldn't happen unless the gvfs backend is broken.


(nautilus:7278): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed
Segmentation fault
lidex@q5u5k5:~$ 

```
I re-installed nautilus and all gvfs packages to no avail.

---

### Post by Sin@Sin-Sacrifice on 2009-10-31
I'd say try a different version. Also did you use the purge option when removing nautilus? You might be reinstalling it with the problem. Might want to bring it up to the gnome devs too. I don't know if the Ubuntu devs play with the code or not.

---

### Post by lidex on 2009-11-01
Downgraded to Jaunty from Jaunty-Updates to no effect.

---

### Post by lidex on 2009-11-01
dmesg output:
```

[    0.447967] bus: 02 index 3 mmio: [0x0-0x0]
[    0.447968] bus: 03 index 0 mmio: [0x0-0x0]
[    0.447969] bus: 03 index 1 mmio: [0xfb000000-0xfdffffff]
[    0.447970] bus: 03 index 2 mmio: [0x0-0x0]
[    0.447972] bus: 03 index 3 io port: [0x00-0xffff]
[    0.447973] bus: 03 index 4 mmio: [0x000000-0xffffffffffffffff]
[    0.447982] NET: Registered protocol family 2
[    0.484059] IP route cache hash table entries: 262144 (order: 9, 2097152 bytes)
[    0.484909] TCP established hash table entries: 262144 (order: 10, 4194304 bytes)
[    0.486514] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[    0.486938] TCP: Hash tables configured (established 262144 bind 65536)
[    0.486940] TCP reno registered
[    0.496092] NET: Registered protocol family 1
[    0.496185] checking if image is initramfs... it is
[    0.984487] Freeing initrd memory: 7787k freed
[    0.988074] audit: initializing netlink socket (disabled)
[    0.988090] type=2000 audit(1256943708.988:1): initialized
[    0.995063] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    0.996086] VFS: Disk quotas dquot_6.5.1
[    0.996127] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    0.996588] fuse init (API version 7.10)
[    0.996647] msgmni has been set to 15787
[    0.996773] alg: No test for stdrng (krng)
[    0.996782] io scheduler noop registered
[    0.996783] io scheduler anticipatory registered
[    0.996784] io scheduler deadline registered
[    0.996821] io scheduler cfq registered (default)
[    1.116058] pci 0000:01:00.0: Boot video device
[    1.118971] pcieport-driver 0000:00:02.0: setting latency timer to 64
[    1.118997] pcieport-driver 0000:00:02.0: found MSI capability
[    1.119018] pcieport-driver 0000:00:02.0: irq 2303 for MSI/MSI-X
[    1.119026] pci_express 0000:00:02.0:pcie00: allocate port service
[    1.119037] pci_express 0000:00:02.0:pcie03: allocate port service
[    1.119075] pcieport-driver 0000:00:06.0: setting latency timer to 64
[    1.119099] pcieport-driver 0000:00:06.0: found MSI capability
[    1.119116] pcieport-driver 0000:00:06.0: irq 2302 for MSI/MSI-X
[    1.119124] pci_express 0000:00:06.0:pcie00: allocate port service
[    1.119132] pci_express 0000:00:06.0:pcie03: allocate port service
[    1.119176] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    1.119182] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    1.119282] input: Power Button (FF) as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input0
[    1.119284] ACPI: Power Button (FF) [PWRF]
[    1.119320] input: Power Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1
[    1.119327] ACPI: Power Button (CM) [PWRB]
[    1.119532] ACPI: duty_cycle spans bit 4
[    1.119555] processor ACPI_CPU:00: registered as cooling_device0
[    1.119579] processor ACPI_CPU:01: registered as cooling_device1
[    1.148691] Linux agpgart interface v0.103
[    1.148699] Serial: 8250/16550 driver4 ports, IRQ sharing enabled
[    1.148808] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    1.149070] 00:09: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    1.149658] brd: module loaded
[    1.149905] loop: module loaded
[    1.149962] Fixed MDIO Bus: probed
[    1.149967] PPP generic driver version 2.4.2
[    1.150011] input: Macintosh mouse button emulation as /devices/virtual/input/input2
[    1.150038] Driver 'sd' needs updating - please use bus_type methods
[    1.150045] Driver 'sr' needs updating - please use bus_type methods
[    1.150071] ahci 0000:00:12.0: version 3.0
[    1.150087] ahci 0000:00:12.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[    1.150117] ahci 0000:00:12.0: controller can't do 64bit DMA, forcing 32bit
[    1.150219] ahci 0000:00:12.0: AHCI 0001.0100 32 slots 4 ports 3 Gbps 0xf impl SATA mode
[    1.150222] ahci 0000:00:12.0: flags: ncq sntf ilck led clo pmp pio 
[    1.150625] scsi0 : ahci
[    1.150733] scsi1 : ahci
[    1.150787] scsi2 : ahci
[    1.150842] scsi3 : ahci
[    1.150917] ata1: SATA max UDMA/133 abar m1024@0xf5fff800 port 0xf5fff900 irq 22
[    1.150921] ata2: SATA max UDMA/133 abar m1024@0xf5fff800 port 0xf5fff980 irq 22
[    1.150924] ata3: SATA max UDMA/133 abar m1024@0xf5fff800 port 0xf5fffa00 irq 22
[    1.150927] ata4: SATA max UDMA/133 abar m1024@0xf5fff800 port 0xf5fffa80 irq 22
[    1.632017] ata1: softreset failed (device not ready)
[    1.632023] ata1: failed due to HW bug, retry pmp=0
[    1.796028] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    1.796770] ata1.00: ATA-7: ST3320820AS, 3.AHG, max UDMA/100
[    1.796772] ata1.00: 625142448 sectors, multi 16: LBA48 NCQ (depth 31/32)
[    1.796786] ata1.00: SB600 AHCI: limiting to 255 sectors per cmd
[    1.797715] ata1.00: SB600 AHCI: limiting to 255 sectors per cmd
[    1.797717] ata1.00: configured for UDMA/100
[    2.280017] ata2: softreset failed (device not ready)
[    2.280021] ata2: failed due to HW bug, retry pmp=0
[    2.444026] ata2: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    2.485092] ata2.00: ATA-7: ST3320620AS, 3.AAE, max UDMA/133
[    2.485094] ata2.00: 625142448 sectors, multi 16: LBA48 NCQ (depth 31/32)
[    2.485107] ata2.00: SB600 AHCI: limiting to 255 sectors per cmd
[    2.543407] ata2.00: SB600 AHCI: limiting to 255 sectors per cmd
[    2.543409] ata2.00: configured for UDMA/133
[    3.024019] ata3: softreset failed (device not ready)
[    3.024023] ata3: failed due to HW bug, retry pmp=0
[    3.188026] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    3.190089] ata3.00: ATAPI: HL-DT-STDVDRRW GSA-H30L, S856, max UDMA/33
[    3.190103] ata3.00: SB600 AHCI: limiting to 255 sectors per cmd
[    3.192520] ata3.00: SB600 AHCI: limiting to 255 sectors per cmd
[    3.192522] ata3.00: configured for UDMA/33
[    3.512031] ata4: SATA link down (SStatus 0 SControl 300)
[    3.512122] scsi 0:0:0:0: Direct-Access     ATA      ST3320820AS      3.AH PQ: 0 ANSI: 5
[    3.512198] sd 0:0:0:0: [sda] 625142448 512-byte hardware sectors: (320 GB/298 GiB)
[    3.512210] sd 0:0:0:0: [sda] Write Protect is off
[    3.512212] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    3.512230] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    3.512289] sd 0:0:0:0: [sda] 625142448 512-byte hardware sectors: (320 GB/298 GiB)
[    3.512299] sd 0:0:0:0: [sda] Write Protect is off
[    3.512301] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    3.512318] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    3.512321]  sda: sda1 sda2 < sda5 sda6 sda7 >
[    3.573505] sd 0:0:0:0: [sda] Attached SCSI disk
[    3.573547] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    3.573593] scsi 1:0:0:0: Direct-Access     ATA      ST3320620AS      3.AA PQ: 0 ANSI: 5
[    3.573658] sd 1:0:0:0: [sdb] 625142448 512-byte hardware sectors: (320 GB/298 GiB)
[    3.573668] sd 1:0:0:0: [sdb] Write Protect is off
[    3.573670] sd 1:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[    3.573687] sd 1:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    3.573722] sd 1:0:0:0: [sdb] 625142448 512-byte hardware sectors: (320 GB/298 GiB)
[    3.573732] sd 1:0:0:0: [sdb] Write Protect is off
[    3.573733] sd 1:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[    3.573750] sd 1:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    3.573752]  sdb: sdb1 sdb2 sdb3
[    3.591354] sd 1:0:0:0: [sdb] Attached SCSI disk
[    3.591385] sd 1:0:0:0: Attached scsi generic sg1 type 0
[    3.593733] scsi 2:0:0:0: CD-ROM            HL-DT-ST DVDRRW GSA-H30L  S856 PQ: 0 ANSI: 5
[    3.722129] sr0: scsi3-mmc drive: 40x/40x writer dvd-ram cd/rw xa/form2 cdda tray
[    3.722132] Uniform CD-ROM driver Revision: 3.20
[    3.722203] sr 2:0:0:0: Attached scsi CD-ROM sr0
[    3.722229] sr 2:0:0:0: Attached scsi generic sg2 type 5
[    3.722444] pata_atiixp 0000:00:14.1: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    3.722472] pata_atiixp 0000:00:14.1: setting latency timer to 64
[    3.722567] scsi4 : pata_atiixp
[    3.722625] scsi5 : pata_atiixp
[    3.723719] ata5: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xff00 irq 14
[    3.723721] ata6: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xff08 irq 15
[    4.032384] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    4.032402] ehci_hcd 0000:00:13.5: PCI INT D -> GSI 19 (level, low) -> IRQ 19
[    4.032417] ehci_hcd 0000:00:13.5: EHCI Host Controller
[    4.032461] ehci_hcd 0000:00:13.5: new USB bus registered, assigned bus number 1
[    4.032484] ehci_hcd 0000:00:13.5: applying AMD SB600/SB700 USB freeze workaround
[    4.032518] ehci_hcd 0000:00:13.5: debug port 1
[    4.032533] ehci_hcd 0000:00:13.5: irq 19, io mem 0xf5fff000
[    4.044018] ehci_hcd 0000:00:13.5: USB 2.0 started, EHCI 1.00
[    4.044084] usb usb1: configuration #1 chosen from 1 choice
[    4.044104] hub 1-0:1.0: USB hub found
[    4.044110] hub 1-0:1.0: 10 ports detected
[    4.044208] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    4.044219] ohci_hcd 0000:00:13.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    4.044231] ohci_hcd 0000:00:13.0: OHCI Host Controller
[    4.044264] ohci_hcd 0000:00:13.0: new USB bus registered, assigned bus number 2
[    4.044283] ohci_hcd 0000:00:13.0: irq 16, io mem 0xf5ffe000
[    4.104035] usb usb2: configuration #1 chosen from 1 choice
[    4.104055] hub 2-0:1.0: USB hub found
[    4.104062] hub 2-0:1.0: 2 ports detected
[    4.104128] ohci_hcd 0000:00:13.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    4.104136] ohci_hcd 0000:00:13.1: OHCI Host Controller
[    4.104168] ohci_hcd 0000:00:13.1: new USB bus registered, assigned bus number 3
[    4.104185] ohci_hcd 0000:00:13.1: irq 17, io mem 0xf5ffd000
[    4.160033] usb usb3: configuration #1 chosen from 1 choice
[    4.160054] hub 3-0:1.0: USB hub found
[    4.160061] hub 3-0:1.0: 2 ports detected
[    4.160131] ohci_hcd 0000:00:13.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    4.160139] ohci_hcd 0000:00:13.2: OHCI Host Controller
[    4.160169] ohci_hcd 0000:00:13.2: new USB bus registered, assigned bus number 4
[    4.160186] ohci_hcd 0000:00:13.2: irq 18, io mem 0xf5ffc000
[    4.216043] usb usb4: configuration #1 chosen from 1 choice
[    4.216060] hub 4-0:1.0: USB hub found
[    4.216069] hub 4-0:1.0: 2 ports detected
[    4.216137] ohci_hcd 0000:00:13.3: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    4.216146] ohci_hcd 0000:00:13.3: OHCI Host Controller
[    4.216182] ohci_hcd 0000:00:13.3: new USB bus registered, assigned bus number 5
[    4.216195] ohci_hcd 0000:00:13.3: irq 17, io mem 0xf5ffb000
[    4.272041] usb usb5: configuration #1 chosen from 1 choice
[    4.272058] hub 5-0:1.0: USB hub found
[    4.272066] hub 5-0:1.0: 2 ports detected
[    4.272131] ohci_hcd 0000:00:13.4: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    4.272139] ohci_hcd 0000:00:13.4: OHCI Host Controller
[    4.272173] ohci_hcd 0000:00:13.4: new USB bus registered, assigned bus number 6
[    4.272185] ohci_hcd 0000:00:13.4: irq 18, io mem 0xf5ffa000
[    4.328039] usb usb6: configuration #1 chosen from 1 choice
[    4.328058] hub 6-0:1.0: USB hub found
[    4.328066] hub 6-0:1.0: 2 ports detected
[    4.328133] uhci_hcd: USB Universal Host Controller Interface driver
[    4.328198] PNP: PS/2 Controller [PNP0303:PS2K] at 0x60,0x64 irq 1
[    4.328199] PNP: PS/2 appears to have AUX port disabled, if this is incorrect please boot with i8042.nopnp
[    4.328261] serio: i8042 KBD port at 0x60,0x64 irq 1
[    4.336536] mice: PS/2 mouse device common for all mice
[    4.372556] rtc_cmos 00:02: RTC can wake from S4
[    4.372584] rtc_cmos 00:02: rtc core: registered rtc_cmos as rtc0
[    4.372609] rtc0: alarms up to one month, y3k, 114 bytes nvram, hpet irqs
[    4.372659] device-mapper: uevent: version 1.0.3
[    4.372744] device-mapper: ioctl: 4.14.0-ioctl (2008-04-23) initialised: dm-devel@redhat.com
[    4.372839] device-mapper: multipath: version 1.0.5 loaded
[    4.372842] device-mapper: multipath round-robin: version 1.0.0 loaded
[    4.372941] cpuidle: using governor ladder
[    4.372942] cpuidle: using governor menu
[    4.373277] TCP cubic registered
[    4.373333] NET: Registered protocol family 10
[    4.373638] lo: Disabled Privacy Extensions
[    4.373853] NET: Registered protocol family 17
[    4.373870] Bluetooth: L2CAP ver 2.11
[    4.373871] Bluetooth: L2CAP socket layer initialized
[    4.373873] Bluetooth: SCO (Voice Link) ver 0.6
[    4.373874] Bluetooth: SCO socket layer initialized
[    4.373912] Bluetooth: RFCOMM socket layer initialized
[    4.373918] Bluetooth: RFCOMM TTY layer initialized
[    4.373919] Bluetooth: RFCOMM ver 1.10
[    4.373957] powernow-k8: Found 1 AMD Athlon(tm) 64 X2 Dual Core Processor 4600+ processors (2 cpu cores) (version 2.20.00)
[    4.373974] [Firmware Bug]: powernow-k8: Your BIOS does not provide ACPI _PSS objects in a way that Linux understands. Please report this to the Linux ACPI maintainers and complain to your BIOS vendor.
[    4.373999] [Firmware Bug]: powernow-k8: Your BIOS does not provide ACPI _PSS objects in a way that Linux understands. Please report this to the Linux ACPI maintainers and complain to your BIOS vendor.
[    4.374084] registered taskstats version 1
[    4.374197]   Magic number: 13:681:50
[    4.374273] rtc_cmos 00:02: setting system clock to 2009-10-30 23:01:53 UTC (1256943713)
[    4.374276] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    4.374277] EDD information not available.
[    4.374307] Freeing unused kernel memory: 536k freed
[    4.374502] Write protecting the kernel read-only data: 6688k
[    4.395528] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input3
[    4.436672] vesafb: framebuffer at 0xf7000000, mapped to 0xffffc20010100000, using 3072k, total 14336k
[    4.436675] vesafb: mode is 1024x768x16, linelength=2048, pages=1
[    4.436677] vesafb: scrolling: redraw
[    4.436680] vesafb: Truecolor: size=0:5:6:5, shift=0:11:5:0
[    4.436747] Console: switching to colour frame buffer device 128x48
[    4.444889] fb0: VESA VGA frame buffer device
[    4.565208] atl1 0000:02:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    4.565217] atl1 0000:02:00.0: setting latency timer to 64
[    4.565252] atl1 0000:02:00.0: version 2.1.3
[    4.796522] usb 2-1: new low speed USB device using ohci_hcd and address 2
[    4.966107] usb 2-1: configuration #1 chosen from 1 choice
[    4.972220] usbcore: registered new interface driver hiddev
[    4.977351] input: Logitech USB-PS/2 Optical Mouse as /devices/pci0000:00/0000:00:13.0/usb2/2-1/2-1:1.0/input/input4
[    5.004576] generic-usb 0003:046D:C01D.0001: input,hidraw0: USB HID v1.10 Mouse [Logitech USB-PS/2 Optical Mouse] on usb-0000:00:13.0-1/input0
[    5.004594] usbcore: registered new interface driver usbhid
[    5.004597] usbhid: v2.6:USB HID core driver
[    5.105359] PM: Starting manual resume from disk
[    5.105363] PM: Resume from partition 8:7
[    5.105364] PM: Checking hibernation image.
[    5.105510] PM: Resume from disk failed.
[    5.115670] EXT3-fs: INFO: recovery required on readonly filesystem.
[    5.115672] EXT3-fs: write access will be enabled during recovery.
[    5.232521] usb 2-2: new full speed USB device using ohci_hcd and address 3
[    5.399486] usb 2-2: configuration #1 chosen from 1 choice
[    5.591342] kjournald starting.  Commit interval 5 seconds
[    5.591362] EXT3-fs: sdb2: orphan cleanup on readonly fs
[    5.613642] ext3_orphan_cleanup: deleting unreferenced inode 718558
[    5.622099] ext3_orphan_cleanup: deleting unreferenced inode 718571
[    5.632119] ext3_orphan_cleanup: deleting unreferenced inode 719257
[    5.648744] ext3_orphan_cleanup: deleting unreferenced inode 719244
[    5.655964] ext3_orphan_cleanup: deleting unreferenced inode 719248
[    5.664021] usb 5-2: new full speed USB device using ohci_hcd and address 2
[    5.667188] ext3_orphan_cleanup: deleting unreferenced inode 244602
[    5.675431] ext3_orphan_cleanup: deleting unreferenced inode 749934
[    5.685578] ext3_orphan_cleanup: deleting unreferenced inode 718552
[    5.701945] ext3_orphan_cleanup: deleting unreferenced inode 720107
[    5.711339] ext3_orphan_cleanup: deleting unreferenced inode 720158
[    5.723101] ext3_orphan_cleanup: deleting unreferenced inode 720247
[    5.743860] ext3_orphan_cleanup: deleting unreferenced inode 825696
[    5.761172] ext3_orphan_cleanup: deleting unreferenced inode 825691
[    5.767020] ext3_orphan_cleanup: deleting unreferenced inode 718544
[    5.778141] ext3_orphan_cleanup: deleting unreferenced inode 720110
[    5.809099] ext3_orphan_cleanup: deleting unreferenced inode 718489
[    5.809112] ext3_orphan_cleanup: deleting unreferenced inode 718546
[    5.809122] ext3_orphan_cleanup: deleting unreferenced inode 718549
[    5.811698] ext3_orphan_cleanup: deleting unreferenced inode 718548
[    5.813298] ext3_orphan_cleanup: deleting unreferenced inode 716768
[    5.813449] ext3_orphan_cleanup: deleting unreferenced inode 720096
[    5.826616] ext3_orphan_cleanup: deleting unreferenced inode 669729
[    5.826779] EXT3-fs: sdb2: 22 orphan inodes deleted
[    5.826781] EXT3-fs: recovery complete.
[    5.891116] usb 5-2: configuration #1 chosen from 1 choice
[    6.111814] EXT3-fs: mounted filesystem with ordered data mode.
[   12.218766] udev: starting version 141
[   12.551886] Bluetooth: Generic Bluetooth USB driver ver 0.3
[   12.551979] usbcore: registered new interface driver btusb
[   13.419610] nvidia: module license 'NVIDIA' taints kernel.
[   13.672462] nvidia 0000:01:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[   13.672470] nvidia 0000:01:00.0: setting latency timer to 64
[   13.672993] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  185.18.14  Wed May 27 01:23:47 PDT 2009
[   13.882868] piix4_smbus 0000:00:14.0: SMBus Host Controller at 0xb00, revision 0
[   13.901703] input: PC Speaker as /devices/platform/pcspkr/input/input5
[   14.004288] Linux video capture interface: v2.00
[   14.050399] cx88/0: cx2388x v4l2 driver version 0.0.6 loaded
[   14.050438] cx8800 0000:03:07.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[   14.051169] cx88[0]: subsystem: 1002:a101, board: ATI HDTV Wonder [card=34,autodetected], frontend(s): 1
[   14.051171] cx88[0]: TV tuner type 68, Radio tuner type -1
[   14.053953] cx88/2: cx2388x MPEG-TS Driver Manager version 0.0.6 loaded
[   14.113031] cx2388x alsa driver version 0.0.6 loaded
[   14.153849] HDA Intel 0000:00:14.2: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   14.178425] hda_codec: Unknown model for ALC883, trying auto-probe from BIOS...
[   14.227516] cx88[0]/0: found at 0000:03:07.0, rev: 5, irq: 22, latency: 64, mmio: 0xfd000000
[   14.227625] cx88[0]/0: registered device video0 [v4l2]
[   14.227664] cx88[0]/0: registered device vbi0
[   14.227820] cx88[0]/2: cx2388x 8802 Driver Manager
[   14.227833] cx88-mpeg driver manager 0000:03:07.2: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[   14.227843] cx88[0]/2: found at 0000:03:07.2, rev: 5, irq: 22, latency: 64, mmio: 0xfb000000
[   14.227849] cx8802_probe() allocating 1 frontend(s)
[   14.228409] cx88_audio 0000:03:07.1: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[   14.228435] cx88[0]/1: CX88x/0: ALSA support for cx2388x boards
[   14.239654] cx88/2: cx2388x dvb driver version 0.0.6 loaded
[   14.239657] cx88/2: registering cx8802 driver, type: dvb access: shared
[   14.239660] cx88[0]/2: subsystem: 1002:a101, board: ATI HDTV Wonder [card=34]
[   14.239662] cx88[0]/2: cx2388x based DVB/ATSC card
[   14.320420] nxt200x: NXT2004 Detected
[   14.396295] tuner-simple 1-0061: creating new instance
[   14.396298] tuner-simple 1-0061: type set to 68 (Philips TUV1236D ATSC/NTSC dual in)
[   14.396303] DVB: registering new adapter (cx88[0])
[   14.396305] DVB: registering adapter 0 frontend 0 (Nextwave NXT200X VSB/QAM frontend)...
[   14.550026] lp: driver loaded but no devices found
[   14.664582] Adding 7783452k swap on /dev/sda7.  Priority:-1 extents:1 across:7783452k
[   14.690559] Adding 4000144k swap on /dev/sdb1.  Priority:-2 extents:1 across:4000144k
[   15.239834] EXT3 FS on sdb2, internal journal
[   19.916012] kjournald starting.  Commit interval 5 seconds
[   19.916521] EXT3 FS on sdb3, internal journal
[   19.916526] EXT3-fs: mounted filesystem with ordered data mode.
[   20.350702] type=1505 audit(1256958129.474:2): operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" name2="default" pid=2223
[   20.389302] type=1505 audit(1256958129.514:3): operation="profile_load" name="/sbin/dhclient-script" name2="default" pid=2227
[   20.389414] type=1505 audit(1256958129.514:4): operation="profile_load" name="/sbin/dhclient3" name2="default" pid=2227
[   20.389454] type=1505 audit(1256958129.514:5): operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" name2="default" pid=2227
[   20.389488] type=1505 audit(1256958129.514:6): operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" name2="default" pid=2227
[   20.553492] type=1505 audit(1256958129.677:7): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=2241
[   20.553631] type=1505 audit(1256958129.677:8): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=2241
[   20.578596] type=1505 audit(1256958129.701:9): operation="profile_load" name="/usr/sbin/tcpdump" name2="default" pid=2245
[   25.152820] vboxdrv: Trying to deactivate the NMI watchdog permanently...
[   25.152823] vboxdrv: Successfully done.
[   25.152824] vboxdrv: Found 2 processor cores.
[   25.152869] VBoxDrv: dbg - g_abExecMemory=ffffffffa0cc3f00
[   25.152882] vboxdrv: fAsync=1 offMin=0xccf6c offMax=0xccf6c
[   25.152922] vboxdrv: TSC mode is 'asynchronous', kernel timer mode is 'normal'.
[   25.152924] vboxdrv: Successfully loaded version 3.0.8_OSE (interface 0x000e0000).
[   25.159629] VBoxNetAdp: dbg - g_abExecMemory=ffffffffa0e62fc0
[   25.166016] VBoxNetFlt: dbg - g_abExecMemory=ffffffffa0e81820
[   27.316875] ppdev: user-space parallel port driver
[   30.875348] atl1 0000:02:00.0: irq 2301 for MSI/MSI-X
[   30.875416] atl1 0000:02:00.0: eth0 link is up 100 Mbps full duplex
[   30.875461] atl1 0000:02:00.0: eth0 link is up 1000 Mbps full duplex
[   41.324013] eth0: no IPv6 routers present
[   48.578526] warning: `pulseaudio' uses 32-bit capabilities (legacy support in use)
[   49.025359] Too big adjustment 32
[   49.064516] Too big adjustment 32
[   49.106259] Too big adjustment 32
[   49.112518] Too big adjustment 32
[   49.130865] Too big adjustment 32
[   49.136521] Too big adjustment 32
[   49.146242] Too big adjustment 32
[   49.152519] Too big adjustment 32
[   49.170911] Too big adjustment 32
[   49.200516] Too big adjustment 32
[   49.234262] Too big adjustment 32
[   49.240518] Too big adjustment 32
[   49.259487] Too big adjustment 32
[   49.288519] Too big adjustment 32
[   49.322216] Too big adjustment 32
[   49.328521] Too big adjustment 32
[   49.346744] Too big adjustment 32
[   49.376022] Too big adjustment 32
[   49.409847] Too big adjustment 32
[   49.416519] Too big adjustment 32
[   49.434556] Too big adjustment 32
[   49.464517] Too big adjustment 32
[   49.498197] Too big adjustment 32
[   49.504520] Too big adjustment 32
[   49.522526] Too big adjustment 32
[   49.552021] Too big adjustment 32
[   49.585769] Too big adjustment 32
[   49.592519] Too big adjustment 32
[   49.611726] Too big adjustment 32
[   49.616519] Too big adjustment 32
[ 1072.121282] nautilus[3790]: segfault at f960000001b ip 00007fdc8ba66f6c sp 00007fffa069ca40 error 4 in libglib-2.0.so.0.2200.2[7fdc8ba0e000+c4000]
[ 1085.005381] nautilus[5648]: segfault at 400000033 ip 00007f732b2fcf79 sp 00007f73193f7ea0 error 4 in libglib-2.0.so.0.2200.2[7f732b2a4000+c4000]
[ 1106.829181] nautilus[5916] general protection ip:7f9d76b348bf sp:7fff35378498 error:0 in libglib-2.0.so.0.2200.2[7f9d76afc000+c4000]
[ 1150.070800] kjournald starting.  Commit interval 5 seconds
[ 1150.070810] EXT3-fs warning: checktime reached, running e2fsck is recommended
[ 1150.070964] EXT3 FS on sda6, internal journal
[ 1150.070968] EXT3-fs: mounted filesystem with ordered data mode.
[ 1151.584014] kjournald starting.  Commit interval 5 seconds
[ 1151.584022] EXT3-fs warning: checktime reached, running e2fsck is recommended
[ 1151.584178] EXT3 FS on sda5, internal journal
[ 1151.584182] EXT3-fs: mounted filesystem with ordered data mode.
[ 1172.984161] nautilus[5962]: segfault at 610089 ip 00007f45ff6ec8bf sp 00007fff827f7958 error 6 in libglib-2.0.so.0.2200.2[7f45ff6b4000+c4000]
[ 1261.929496] nautilus[6194]: segfault at 6e6f6349 ip 00007ff61d0bef79 sp 00007fff2a458370 error 4 in libglib-2.0.so.0.2200.2[7ff61d066000+c4000]
[ 1297.377055] nautilus[6266] general protection ip:7fef00984790 sp:7fffdd833b70 error:0 in libgobject-2.0.so.0.2200.2[7fef00974000+43000]
[ 1756.750176] nautilus[7124]: segfault at 7fec341c7960 ip 00007fec341c7960 sp 00007fff418dea68 error 14
[ 1764.812297] nautilus[7152]: segfault at 7f583b386960 ip 00007f583b386960 sp 00007fff9a1c5578 error 14
[ 1770.423967] nautilus[7172]: segfault at 1 ip 00007f54c74c1f79 sp 00007f54bfcfc650 error 4 in libglib-2.0.so.0.2200.2[7f54c7469000+c4000]
[ 1780.018012] nautilus[7188]: segfault at 2 ip 00007f4e561b9f79 sp 00007fffdd41a570 error 4 in libglib-2.0.so.0.2200.2[7f4e56161000+c4000]
[ 1819.858420] nautilus[7215] general protection ip:7f9a0b73af79 sp:7fff40cb5980 error:0 in libglib-2.0.so.0.2200.2[7f9a0b6e2000+c4000]
[ 1852.083772] nautilus[7278]: segfault at 7f0065707964 ip 00007f4e5df3b8bf sp 00007fff2b80f9b8 error 6 in libglib-2.0.so.0.2200.2[7f4e5df03000+c4000]
[62059.500014] Clocksource tsc unstable (delta = 62500186 ns)
[78186.557414] nautilus[11249]: segfault at 7f21fff81960 ip 00007f21fff81960 sp 00007fff817b35d8 error 14
[78220.901791] nautilus[11283]: segfault at 1 ip 00007f4e6cb87f79 sp 00007fffa0b04f40 error 4 in libglib-2.0.so.0.2200.2[7f4e6cb2f000+c4000]
[78295.976662] nautilus[11418]: segfault at 7fdd93492960 ip 00007fdd93492960 sp 00007fffc466ea88 error 14
[78314.428966] Too big adjustment 32

```

Though not an expert, looks like a glib problem. Will try downgrading those libs.

---

### Post by lidex on 2009-11-01
That did it. libglib2.0 installed was at a version 2.22x whereas jaunty-updates at 2.20x. Reverted to jaunty-update version. Must have pulled that version in with an install from ppa.

---

### Post by kavoura on 2010-02-26
> **lidex said:**
> That did it. libglib2.0 installed was at a version 2.22x whereas jaunty-updates at 2.20x. Reverted to jaunty-update version. Must have pulled that version in with an install from ppa.

I have the same problem. And I notice that I have libglib 2.22.3
You wrote that reverting to 2.20 solved the problem. But HOW did you do that? I do not know how to downgrade it. If I try to remove libglib it wants to remove almost all of my installed programs.

---

### Post by kavoura on 2010-02-26
> **lidex said:**
> That did it. libglib2.0 installed was at a version 2.22x whereas jaunty-updates at 2.20x. Reverted to jaunty-update version. Must have pulled that version in with an install from ppa.

> **kavoura said:**
> I have the same problem. And I notice that I have libglib 2.22.3
You wrote that reverting to 2.20 solved the problem. But HOW did you do that? I do not know how to downgrade it. If I try to remove libglib it wants to remove almost all of my installed programs.


I found out how to do it by searching this forum and found the following code helpful:

sudo aptitude install libglib2.0-0=2.20.1-0ubuntu2.1

---

### Post by lidex on 2010-02-26
> **kavoura said:**
> I found out how to do it by searching this forum and found the following code helpful:

sudo aptitude install libglib2.0-0=2.20.1-0ubuntu2.1

Or you can use synaptic to force the earlier version, which is what i did.

---

