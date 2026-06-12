---
title: "The owner is &quot;184444735 - user #-184444735&quot; and the group is &quot;17414907&quot; which makes n"
date: 2010-04-15
forum: General Help
---

### Post by baybe1111 on 2010-04-15
Hi. I have recovered most of mu USB drive, but a couple of folders are locked and look like files. I'm unable to change permissions on them and "You are not the owner so you cannot change these permissions." appears in the properties tab. The owner is "184444735 - user #-184444735" and the group is "17414907" which makes no sense to me. Most other folders and files are OK. The disaster I recovered from was a partition move that failed. I used fsck to get most things back. Any idea how I get these couple of folders (the most important one is one of them "Documents" of course). to be visible?

---

### Post by new_tolinux on 2010-04-15
Under normal conditions, this should do:
```
sudo chown -R yourusername:yourgroupname *
```Which set yourusername and yourgroupname (by default the same as yourusername)  as the owner for the current folder + files + all subfolders + files.
Maybe you'll have to do a chmod as well:
```
sudo chmod -R 777 *
```Which grants _all_ rights to you, yourgroup and the rest of the world (also recursive). Although you're probably better of with 770 (which grants you+yourgroup all rights, but grants "no access" to the rest of the world).

---

### Post by baybe1111 on 2010-04-16
Hello new_ I tried the above and got a lot of operation not permitted errors for the chown, and no such file or directory, and Operation not permitted errors for the chmod.
The terminal screen hangs about half way through the second operation. Rest of OS works fine though..? Repeating the above gives identical results. Would mounting as uuid in fstab work. I don't know how to do this (or if it would help) but fstab is below and the uuid is visible in gparted. Looking at fstab the USB drive isn't there now but would it help if it was? so many questions- sorry. Also noted when I shutdown hundreds of scrolling messages saying "Directory # (lots of numbers) contains a hole at offset (more numbers). Strange?

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda1 /               ext3    defaults,errors=remount-ro,relatime 0       1
/dev/sda2 none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0

---

### Post by baybe1111 on 2010-04-18
Hello magnanimous people, thank you for your help thus far. I think maybe with a little more help I might have this one fixed. Below is some of the dmesg output (all of it wouldn't fit). Lots of "bogus i mode" and "attempt to access beyond end of device" errors. Any ideas? 

 *0, disabled.
[   31.452014] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 *9 10 11 12 14 15)
[   31.452344] Linux Plug and Play Support v0.97 (c) Adam Belay
[   31.452421] pnp: PnP ACPI init
[   31.452446] ACPI: bus type pnp registered
[   31.458246] pnp: PnP ACPI: found 13 devices
[   31.458256] ACPI: ACPI bus type pnp unregistered
[   31.458264] PnPBIOS: Disabled by ACPI PNP
[   31.458855] PCI: Using ACPI for IRQ routing
[   31.458864] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   31.464891] PCI: BIOS reporting unknown device 00:22
[   31.464895] PCI: Device 0000:00:0b.1 not found by BIOS
[   31.481889] NET: Registered protocol family 8
[   31.481895] NET: Registered protocol family 20
[   31.482103] AppArmor: AppArmor Filesystem Enabled
[   31.485868] Time: tsc clocksource has been installed.
[   31.494000] system 00:00: iomem range 0x0-0x9ffff could not be reserved
[   31.494008] system 00:00: iomem range 0xf0000-0xfffff could not be reserved
[   31.494013] system 00:00: iomem range 0x100000-0x5fffffff could not be reserved
[   31.494020] system 00:00: iomem range 0xfffe0000-0xffffffff could not be reserved
[   31.494036] system 00:02: ioport range 0x3f0-0x3f1 has been reserved
[   31.494042] system 00:02: ioport range 0x4d0-0x4d1 has been reserved
[   31.494057] system 00:03: ioport range 0xe400-0xe47f has been reserved
[   31.494062] system 00:03: ioport range 0xe800-0xe80f has been reserved
[   31.525006] PCI: Bridge: 0000:00:01.0
[   31.525013]   IO window: disabled.
[   31.525020]   MEM window: e2800000-e3dfffff
[   31.525025]   PREFETCH window: e3f00000-e5ffffff
[   31.525047] PCI: Setting latency timer of device 0000:00:01.0 to 64
[   31.525079] NET: Registered protocol family 2
[   31.562007] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[   31.562829] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[   31.565945] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[   31.567471] TCP: Hash tables configured (established 131072 bind 65536)
[   31.567479] TCP reno registered
[   31.578118] checking if image is initramfs...<7>Switched to high resolution mode on CPU 0
[   32.084004]  it is
[   32.707423] Freeing initrd memory: 7312k freed
[   32.707790] Simple Boot Flag at 0x3a set to 0x1
[   32.708735] audit: initializing netlink socket (disabled)
[   32.708768] audit(1270873403.992:1): initialized
[   32.709170] highmem bounce pool size: 64 pages
[   32.713091] VFS: Disk quotas dquot_6.5.1
[   32.713315] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   32.713654] io scheduler noop registered
[   32.713662] io scheduler anticipatory registered
[   32.713666] io scheduler deadline registered
[   32.713693] io scheduler cfq registered (default)
[   32.713724] Applying VIA southbridge workaround.
[   32.713729] PCI: VIA PCI bridge detected. Disabling DAC.
[   32.713735] PCI: Disabling Via external APIC routing
[   32.713781] Boot video device is 0000:01:00.0
[   32.714448] isapnp: Scanning for PnP cards...
[   33.068421] isapnp: No Plug & Play device found
[   33.186733] Real Time Clock Driver v1.12ac
[   33.186926] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   33.187177] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   33.187636] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[   33.189265] 00:0a: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   33.190147] 00:0b: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[   33.191904] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   33.192081] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[   33.192301] PNP: PS/2 Controller [PNP0303:PS2K] at 0x60,0x64 irq 1
[   33.192308] PNP: PS/2 appears to have AUX port disabled, if this is incorrect please boot with i8042.nopnp
[   33.192516] serio: i8042 KBD port at 0x60,0x64 irq 1
[   33.201063] mice: PS/2 mouse device common for all mice
[   33.201373] EISA: Probing bus 0 at eisa.0
[   33.201430] EISA: Detected 0 cards.
[   33.201437] cpuidle: using governor ladder
[   33.201441] cpuidle: using governor menu
[   33.201776] NET: Registered protocol family 1
[   33.201842] Using IPI No-Shortcut mode
[   33.201928] registered taskstats version 1
[   33.202097]   Magic number: 6:980:362
[   33.202408] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[   33.202412] EDD information not available.
[   33.203382] Freeing unused kernel memory: 368k freed
[   33.203443] Write protecting the kernel read-only data: 802k
[   33.226706] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
[   34.777988] fuse init (API version 7.9)
[   34.827264] ACPI: CPU0 (power states: C1[C1] C2[C2])
[   34.827278] ACPI: Processor [CPU0] (supports 16 throttling states)
[   35.911412] SCSI subsystem initialized
[   36.052926] usbcore: registered new interface driver usbfs
[   36.052978] usbcore: registered new interface driver hub
[   36.068634] r8169 Gigabit Ethernet driver 2.2LK loaded
[   36.068665] PCI: Enabling device 0000:00:0a.0 (0014 -> 0017)
[   36.069199] ACPI: PCI Interrupt Link [LNKC] enabled at IRQ 11
[   36.069206] PCI: setting IRQ 11 as level-triggered
[   36.069213] ACPI: PCI Interrupt 0000:00:0a.0[A] -> Link [LNKC] -> GSI 11 (level, low) -> IRQ 11
[   36.069255] r8169 0000:00:0a.0: no PCI Express capability
[   36.069712] eth0: RTL8169sb/8110sb at 0xf883c000, 00:b0:c2:02:29:d6, XID 10000000 IRQ 11
[   36.092755] libata version 3.00 loaded.
[   36.110911] usbcore: registered new device driver usb
[   36.125966] pata_via 0000:00:04.1: version 0.3.3
[   36.134697] scsi0 : pata_via
[   36.154860] USB Universal Host Controller Interface driver v3.0
[   36.165868] scsi1 : pata_via
[   36.166806] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xd800 irq 14
[   36.166814] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xd808 irq 15
[   36.296903] Floppy drive(s): fd0 is 1.44M
[   36.314528] FDC 0 is a post-1991 82077
[   36.486948] ata1.00: ATAPI: HL-DT-STDVD-ROM GDR8164B, 0L06, max UDMA/33
[   36.658794] ata1.00: configured for UDMA/33
[   36.823141] ata2.00: ATA-5: MAXTOR 6L020J1, A93.0500, max UDMA/133
[   36.823151] ata2.00: 40132503 sectors, multi 16: LBA 
[   36.838922] ata2.00: configured for UDMA/100
[   36.842697] scsi 0:0:0:0: CD-ROM            HL-DT-ST DVD-ROM GDR8164B 0L06 PQ: 0 ANSI: 5
[   36.843084] scsi 1:0:0:0: Direct-Access     ATA      MAXTOR 6L020J1   A93. PQ: 0 ANSI: 5
[   36.848368] ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 9
[   36.848381] PCI: setting IRQ 9 as level-triggered
[   36.848386] ACPI: PCI Interrupt 0000:00:04.2[D] -> Link [LNKD] -> GSI 9 (level, low) -> IRQ 9
[   36.848411] uhci_hcd 0000:00:04.2: UHCI Host Controller
[   36.849173] uhci_hcd 0000:00:04.2: new USB bus registered, assigned bus number 1
[   36.849216] uhci_hcd 0000:00:04.2: irq 9, io base 0x0000d400
[   36.849511] usb usb1: configuration #1 chosen from 1 choice
[   36.849558] hub 1-0:1.0: USB hub found
[   36.849572] hub 1-0:1.0: 2 ports detected
[   36.950547] ACPI: PCI Interrupt 0000:00:04.3[D] -> Link [LNKD] -> GSI 9 (level, low) -> IRQ 9
[   36.950576] uhci_hcd 0000:00:04.3: UHCI Host Controller
[   36.950635] uhci_hcd 0000:00:04.3: new USB bus registered, assigned bus number 2
[   36.950670] uhci_hcd 0000:00:04.3: irq 9, io base 0x0000d000
[   36.950894] usb usb2: configuration #1 chosen from 1 choice
[   36.950940] hub 2-0:1.0: USB hub found
[   36.950953] hub 2-0:1.0: 2 ports detected
[   37.054440] PCI: Enabling device 0000:00:0b.0 (0014 -> 0015)
[   37.054983] ACPI: PCI Interrupt Link [LNKB] enabled at IRQ 11
[   37.054990] ACPI: PCI Interrupt 0000:00:0b.0[A] -> Link [LNKB] -> GSI 11 (level, low) -> IRQ 11
[   37.055011] uhci_hcd 0000:00:0b.0: UHCI Host Controller
[   37.055092] uhci_hcd 0000:00:0b.0: new USB bus registered, assigned bus number 3
[   37.055133] uhci_hcd 0000:00:0b.0: irq 11, io base 0x0000a000
[   37.055382] usb usb3: configuration #1 chosen from 1 choice
[   37.055429] hub 3-0:1.0: USB hub found
[   37.055442] hub 3-0:1.0: 2 ports detected
[   37.158370] PCI: Enabling device 0000:00:0b.1 (0014 -> 0015)
[   37.158392] ACPI: PCI Interrupt 0000:00:0b.1[B] -> Link [LNKC] -> GSI 11 (level, low) -> IRQ 11
[   37.158414] uhci_hcd 0000:00:0b.1: UHCI Host Controller
[   37.158465] uhci_hcd 0000:00:0b.1: new USB bus registered, assigned bus number 4
[   37.158498] uhci_hcd 0000:00:0b.1: irq 11, io base 0x00009800
[   37.158749] usb usb4: configuration #1 chosen from 1 choice
[   37.158805] hub 4-0:1.0: USB hub found
[   37.158818] hub 4-0:1.0: 2 ports detected
[   37.190137] usb 1-1: new full speed USB device using uhci_hcd and address 2
[   37.262580] PCI: Enabling device 0000:00:0b.2 (0014 -> 0016)
[   37.262603] ACPI: PCI Interrupt 0000:00:0b.2[C] -> Link [LNKD] -> GSI 9 (level, low) -> IRQ 9
[   37.262631] ehci_hcd 0000:00:0b.2: EHCI Host Controller
[   37.262716] ehci_hcd 0000:00:0b.2: new USB bus registered, assigned bus number 5
[   37.262795] ehci_hcd 0000:00:0b.2: irq 9, io mem 0xe1800000
[   37.318043] ehci_hcd 0000:00:0b.2: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   37.318313] usb usb5: configuration #1 chosen from 1 choice
[   37.318363] hub 5-0:1.0: USB hub found
[   37.318380] hub 5-0:1.0: 4 ports detected
[   37.333003] usb 1-1: not running at top speed; connect to a high speed hub
[   37.347167] usb 1-1: configuration #1 chosen from 1 choice
[   37.349062] hub 1-1:1.0: USB hub found
[   37.350042] hub 1-1:1.0: 4 ports detected
[   37.836233] Driver 'sd' needs updating - please use bus_type methods
[   37.839563] sd 1:0:0:0: [sda] 40132503 512-byte hardware sectors (20548 MB)
[   37.839596] sd 1:0:0:0: [sda] Write Protect is off
[   37.839601] sd 1:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   37.839633] sd 1:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   37.839748] sd 1:0:0:0: [sda] 40132503 512-byte hardware sectors (20548 MB)
[   37.839769] sd 1:0:0:0: [sda] Write Protect is off
[   37.839773] sd 1:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   37.839802] sd 1:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   37.839811]  sda:<4>Driver 'sr' needs updating - please use bus_type methods
[   37.850043]  sda1 sda2
[   37.855579] sr0: scsi3-mmc drive: 52x/52x cd/rw xa/form2 cdda tray
[   37.855594] Uniform CD-ROM driver Revision: 3.20
[   37.855721] sr 0:0:0:0: Attached scsi CD-ROM sr0
[   37.867463] sd 1:0:0:0: [sda] Attached SCSI disk
[   37.888363] sr 0:0:0:0: Attached scsi generic sg0 type 5
[   37.888404] sd 1:0:0:0: Attached scsi generic sg1 type 0
[   38.593084] usb 5-1: new high speed USB device using ehci_hcd and address 2
[   38.726699] usb 5-1: configuration #1 chosen from 1 choice
[   38.930779] usb 1-1.1: new full speed USB device using uhci_hcd and address 3
[   39.031494] usb 1-1.1: not running at top speed; connect to a high speed hub
[   39.044731] usb 1-1.1: configuration #1 chosen from 1 choice
[   39.047214] hub 1-1.1:1.0: USB hub found
[   39.048518] hub 1-1.1:1.0: 4 ports detected
[   39.358248] usb 1-1.2: new full speed USB device using uhci_hcd and address 4
[   39.510343] usb 1-1.2: configuration #1 chosen from 1 choice
[   39.717948] usb 1-1.4: new low speed USB device using uhci_hcd and address 5
[   39.857056] usb 1-1.4: configuration #1 chosen from 1 choice
[   40.061652] usb 1-1.1.1: new full speed USB device using uhci_hcd and address 6
[   40.215753] usb 1-1.1.1: configuration #1 chosen from 1 choice
[   40.223634] usbcore: registered new interface driver libusual
[   40.223898] usbcore: registered new interface driver hiddev
[   40.238072] input: Logitech USB-PS/2 Optical Mouse as /devices/pci0000:00/0000:00:04.2/usb1/1-1/1-1.4/1-1.4:1.0/input/input2
[   40.246320] Initializing USB Mass Storage driver...
[   40.252123] input,hidraw0: USB HID v1.10 Mouse [Logitech USB-PS/2 Optical Mouse] on usb-0000:00:04.2-1.4
[   40.252172] usbcore: registered new interface driver usbhid
[   40.252181] /build/buildd/linux-2.6.24/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
[   40.259424] scsi2 : SCSI emulation for USB Mass Storage devices
[   40.262060] usbcore: registered new interface driver usb-storage
[   40.262076] USB Mass Storage support registered.
[   40.262340] usb-storage: device found at 2
[   40.262345] usb-storage: waiting for device to settle before scanning
[   43.769202] kjournald starting.  Commit interval 5 seconds
[   43.769244] EXT3-fs: mounted filesystem with ordered data mode.
[   45.256844] usb-storage: device scan complete
[   45.257564] scsi 2:0:0:0: Direct-Access     WD       10EAVS External  1.05 PQ: 0 ANSI: 4
[   45.259134] sd 2:0:0:0: [sdb] 1953525168 512-byte hardware sectors (1000205 MB)
[   45.260015] sd 2:0:0:0: [sdb] Write Protect is off
[   45.260021] sd 2:0:0:0: [sdb] Mode Sense: 21 00 00 00
[   45.260025] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[   45.261255] sd 2:0:0:0: [sdb] 1953525168 512-byte hardware sectors (1000205 MB)
[   45.262137] sd 2:0:0:0: [sdb] Write Protect is off
[   45.262142] sd 2:0:0:0: [sdb] Mode Sense: 21 00 00 00
[   45.262146] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[   45.262261]  sdb: sdb2 sdb3
[   52.997325] sd 2:0:0:0: [sdb] Attached SCSI disk
[   52.997405] sd 2:0:0:0: Attached scsi generic sg2 type 0
[   55.759282] udev: starting version 141
[   56.451896] parport_pc: VIA 686A/8231 detected
[   56.451906] parport_pc: probing current configuration
[   56.451933] parport_pc: Current parallel port base: 0x378
[   56.452041] parport0: PC-style at 0x378 (0x778), irq 7, using FIFO [PCSPP,TRISTATE,COMPAT,ECP]
[   56.514851] input: Power Button (FF) as /devices/virtual/input/input3
[   56.525019] ACPI: Power Button (FF) [PWRF]
[   56.525278] input: Power Button (CM) as /devices/virtual/input/input4
[   56.537440] udev: renamed network interface eth0 to eth1
[   56.541009] ACPI: Power Button (CM) [PWRB]
[   56.549100] parport_pc: VIA parallel port: io=0x378, irq=7
[   56.584101] Linux agpgart interface v0.102
[   56.630729] agpgart: Detected VIA Twister-K/KT133x/KM133 chipset
[   56.634028] agpgart: AGP aperture is 32M @ 0xe6000000
[   57.040297] via686a 0000:00:04.4: Sensors disabled, enable with force_addr=0xe200
[   57.123723] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   57.173437] usblp0: USB Bidirectional printer dev 6 if 1 alt 0 proto 2 vid 0x03F0 pid 0x2D11
[   57.173481] usbcore: registered new interface driver usblp
[   57.240964] input: PC Speaker as /devices/platform/pcspkr/input/input5
[   57.397289] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   57.473468] Linux video capture interface: v2.00
[   57.566137] /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/build/build-generic/media/gspcav1/gspca_core.c: USB GSPCA camera found.(ZC3XX) 
[   57.931744] PCI: Enabling device 0000:00:0d.0 (0004 -> 0007)
[   57.931767] ACPI: PCI Interrupt 0000:00:0d.0[A] -> Link [LNKD] -> GSI 9 (level, low) -> IRQ 9
[   57.931834] Vortex: init.... <6>usbcore: registered new interface driver gspca
[   58.241699] /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/build/build-generic/media/gspcav1/gspca_core.c: gspca driver 01.00.20 registered
[   59.308690] done.
[   59.308738] Aureal Advantage 3D Sound Processor: Activating latency workaround...
[   59.308747] Aureal Advantage 3D Sound Processor: vortex latency is 0xff
[   59.308753] Aureal Advantage 3D Sound Processor: bridge config is 0x18
[   59.362474] gameport: AU88x0 Gameport is pci0000:00:0d.0/gameport0, speed 864kHz
[   59.368622] vortex: IRQ reg error
[   59.687609] ppdev: user-space parallel port driver
[   60.123901] vortex: IRQ reg error
[   60.124092] vortex: IRQ reg error
[   60.236720] lp0: using parport0 (interrupt-driven).
[   60.681089] Adding 8289532k swap on /dev/sda2.  Priority:-1 extents:1 across:8289532k
[   61.139291] EXT3 FS on sda1, internal journal
[   62.020058] audit(1270873433.324:2): type=1505 operation="profile_load" info="unsupported interface version" pid=4327
[   62.158704] audit(1270873433.464:3): type=1505 operation="profile_load" info="unsupported interface version" pid=4333
[   62.529574] audit(1270873433.836:4): type=1505 operation="profile_load" info="unsupported interface version" pid=4340
[   62.613131] audit(1270873433.920:5): type=1505 operation="profile_load" info="unsupported interface version" pid=4346
[   63.734559] No dock devices found.
[   67.094645] NET: Registered protocol family 10
[   67.095761] lo: Disabled Privacy Extensions
[   74.353203] Bluetooth: Core ver 2.11
[   74.361072] NET: Registered protocol family 31
[   74.361085] Bluetooth: HCI device and connection manager initialized
[   74.361095] Bluetooth: HCI socket layer initialized
[   74.391609] Bluetooth: L2CAP ver 2.9
[   74.391619] Bluetooth: L2CAP socket layer initialized
[   74.419364] Bluetooth: BNEP (Ethernet Emulation) ver 1.2
[   74.419378] Bluetooth: BNEP filters: protocol multicast
[   74.549044] Bridge firewalling registered
[   74.549749] pan0: Dropping NETIF_F_UFO since no NETIF_F_HW_CSUM feature.
[   74.569411] Bluetooth: SCO (Voice Link) ver 0.6
[   74.569424] Bluetooth: SCO socket layer initialized
[   79.683065] r8169: eth1: link up
[   80.416816] NET: Registered protocol family 17
[   82.114384] [drm] Initialized drm 1.1.0 20060810
[   82.127390] ACPI: PCI Interrupt Link [LNKA] enabled at IRQ 11
[   82.127411] ACPI: PCI Interrupt 0000:01:00.0[A] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
[   82.128814] [drm] Initialized mga 3.2.1 20051102 on minor 0
[   90.126133] eth1: no IPv6 routers present
[  296.770126] kjournald starting.  Commit interval 5 seconds
[  296.770800] EXT3-fs warning: mounting unchecked fs, running e2fsck is recommended
[  296.772642] EXT3 FS on sdb3, internal journal
[  296.772697] EXT3-fs: mounted filesystem with ordered data mode.
[  296.957467] kjournald starting.  Commit interval 5 seconds
[  297.071491] EXT3 FS on sdb2, internal journal
[  297.071549] EXT3-fs: mounted filesystem with ordered data mode.
[  297.110912] init_special_inode: bogus i_mode (4170)
[  297.122077] init_special_inode: bogus i_mode (134042)
[  297.171587] init_special_inode: bogus i_mode (70124)
[  297.901399] init_special_inode: bogus i_mode (117043)
[  297.901707] init_special_inode: bogus i_mode (7374)
[  297.901873] init_special_inode: bogus i_mode (177475)
[  297.908130] init_special_inode: bogus i_mode (75307)
[  297.909559] init_special_inode: bogus i_mode (7454)
[  297.909824] init_special_inode: bogus i_mode (167177)
[  297.913338] init_special_inode: bogus i_mode (31037)
[  297.913603] init_special_inode: bogus i_mode (155205)
[  297.913751] init_special_inode: bogus i_mode (32471)
[  297.915553] init_special_inode: bogus i_mode (176331)
[  297.915713] init_special_inode: bogus i_mode (0)
[  297.918301] init_special_inode: bogus i_mode (7460)
[  297.919597] init_special_inode: bogus i_mode (0)
[  297.920792] init_special_inode: bogus i_mode (112060)
[  297.922156] init_special_inode: bogus i_mode (30344)
[  297.923535] init_special_inode: bogus i_mode (175261)
[  297.925450] init_special_inode: bogus i_mode (135075)
[  297.926720] init_special_inode: bogus i_mode (0)
[  297.926813] init_special_inode: bogus i_mode (31066)
[  297.926884] init_special_inode: bogus i_mode (0)
[  297.928376] init_special_inode: bogus i_mode (7637)
[  297.929743] init_special_inode: bogus i_mode (35001)
[  297.940939] init_special_inode: bogus i_mode (152420)
[  297.941157] init_special_inode: bogus i_mode (110435)
[  297.959138] init_special_inode: bogus i_mode (2271)
[  297.960528] init_special_inode: bogus i_mode (1056)
[  297.960894] init_special_inode: bogus i_mode (175501)
[  297.961040] init_special_inode: bogus i_mode (174330)
[  297.961129] init_special_inode: bogus i_mode (175375)
[  297.961372] init_special_inode: bogus i_mode (175426)
[  297.961503] init_special_inode: bogus i_mode (174273)
[  297.961598] init_special_inode: bogus i_mode (251)
[  297.961682] init_special_inode: bogus i_mode (174405)
[  297.961780] init_special_inode: bogus i_mode (173370)
[  297.961882] init_special_inode: bogus i_mode (167420)
[  298.013164] init_special_inode: bogus i_mode (174020)
[117570.468423] init_special_inode: bogus i_mode (165676)
[117570.586860] init_special_inode: bogus i_mode (1413)
[117570.689968] init_special_inode: bogus i_mode (110701)
[117657.568496] init_special_inode: bogus i_mode (71440)
[117848.412574] EXT3-fs error (device sdb3): htree_dirblock_to_tree: bad entry in directory #15925497: rec_len % 4 != 0 - offset=0, inode=72619401, rec_len=38087, name_len=41
[117848.458077] EXT3-fs error (device sdb3): htree_dirblock_to_tree: bad entry in directory #15925520: rec_len % 4 != 0 - offset=0, inode=1672478543, rec_len=65293, name_len=160
[117848.504800] init_special_inode: bogus i_mode (52140)
[117848.571544] attempt to access beyond end of device
[117848.571569] sdb3: rw=32, want=12698845608, limit=1003516290
[117848.571839] attempt to access beyond end of device
[117848.571851] sdb3: rw=32, want=12698845608, limit=1003516290
[117848.593251] attempt to access beyond end of device
[117848.593272] sdb3: rw=0, want=29507464528, limit=1003516290
[117848.593279] attempt to access beyond end of device
[117848.593283] sdb3: rw=0, want=29507464528, limit=1003516290
[117848.593580] init_special_inode: bogus i_mode (110574)
[117848.608426] EXT3-fs error (device sdb3): htree_dirblock_to_tree: bad entry in directory #15925671: directory entry across blocks - offset=0, inode=2523942178, rec_len=15916, name_len=168
[117848.746659] EXT3-fs error (device sdb3): htree_dirblock_to_tree: bad entry in directory #15925550: rec_len % 4 != 0 - offset=0, inode=3142846409, rec_len=50726, name_len=73
[117848.832001] EXT3-fs error (device sdb3): htree_dirblock_to_tree: bad entry in directory #15925587: rec_len % 4 != 0 - offset=0, inode=4153290461, rec_len=12430, name_len=33
[117848.900943] EXT3-fs error (device sdb3): htree_dirblock_to_tree: bad entry in directory #15925766: rec_len % 4 != 0 - offset=0, inode=1246691446, rec_len=61185, name_len=64
[117849.038613] EXT3-fs error (device sdb3): htree_dirblock_to_tree: bad entry in directory #15925474: rec_len % 4 != 0 - offset=0, inode=107677346, rec_len=1775, name_len=20
[117849.118963] EXT3-fs error (device sdb3): htree_dirblock_to_tree: bad entry in directory #15925555: rec_len % 4 != 0 - offset=0, inode=3487507434, rec_len=11853, name_len=18
[117849.136097] EXT3-fs error (device sdb3): htree_dirblock_to_tree: bad entry in directory #15925781: rec_len % 4 != 0 - offset=0, inode=1709315729, rec_len=30407, name_len=143
[117849.359449] EXT3-fs error (device sdb3): htree_dirblock_to_tree: bad entry in directory #15925796: rec_len % 4 != 0 - offset=0, inode=3475895107, rec_len=30010, name_len=194
[117849.381457] EXT3-fs error (device sdb3): htree_dirblock_to_tree: bad entry in directory #15925461: rec_len % 4 != 0 - offset=0, inode=925953808, rec_len=58118, name_len=11
[117849.434648] init_special_inode: bogus i_mode (70312)
[117849.435528] init_special_inode: bogus i_mode (170347)
[117849.436275] init_special_inode: bogus i_mode (30645)
[117849.458769] EXT3-fs error (device sdb3): htree_dirblock_to_tree: bad entry in directory #15925544: rec_len % 4 != 0 - offset=0, inode=2955168146, rec_len=65366, name_len=234
[117849.536242] EXT3-fs error (device sdb3): htree_dirblock_to_tree: bad entry in directory #15925478: directory entry across blocks - offset=0, inode=3012715527, rec_len=63272, name_len=109
[117849.630828] EXT3-fs error (device sdb3): htree_dirblock_to_tree: bad entry in directory #15925529: directory entry across blocks - offset=0, inode=4294967295, rec_len=65536, name_len=255
[117849.823082] EXT3-fs error (device sdb3): htree_dirblock_to_tree: bad entry in directory #15925572: directory entry across blocks - offset=0, inode=1741755724, rec_len=43208, name_len=244
[117850.011102] EXT3-fs error (device sdb3): htree_dirblock_to_tree: bad entry in directory #15925688: rec_len % 4 != 0 - offset=0, inode=252841746, rec_len=17427, name_len=19
[117850.058719] EXT3-fs error (device sdb3): htree_dirblock_to_tree: bad entry in directory #15925471: rec_len % 4 != 0 - offset=0, inode=20381156, rec_len=65007, name_len=202
[117850.107200] EXT3-fs error (device sdb3): htree_dirblock_to_tree: bad entry in directory #15925494: rec_len % 4 != 0 - offset=0, inode=3424636617, rec_len=22957, name_len=114
[117850.123629] EXT3-fs error (device sdb3): htree_dirblock_to_tree: bad entry in directory #15925428: directory entry across blocks - offset=0, inode=4237523591, rec_len=53332, name_len=193
[117850.215024] EXT3-fs error (device sdb3): htree_dirblock_to_tree: bad entry in directory #15925720: directory entry across blocks - offset=0, inode=1962978560, rec_len=39424, name_len=0
[117850.284846] EXT3-fs error (device sdb3): htree_dirblock_to_tree: bad entry in directory #15925828: rec_len % 4 != 0 - offset=0, inode=3571843327, rec_len=44110, name_len=152
[117850.308645] EXT3-fs error (device sdb3): htree_dirblock_to_tree: bad entry in directory #15925656: rec_len % 4 != 0 - offset=0, inode=967633756, rec_len=1585, name_len=97
[117850.325707] EXT3-fs error (device sdb3): htree_dirblock_to_tree: bad entry in directory #15925444: rec_len % 4 != 0 - offset=0, inode=1219334520, rec_len=61621, name_len=80
[117850.389401] EXT3-fs error (device sdb3): htree_dirblock_to_tree: bad entry in directory #15925505: rec_len % 4 != 0 - offset=0, inode=545867926, rec_len=53415, name_len=59
[117850.466752] EXT3-fs error (device sdb3): htree_dirblock_to_tree: bad entry in directory #15925502: directory entry across blocks - offset=0, inode=715469547, rec_len=4500, name_len=148
[117850.812770] EXT3-fs error (device sdb3): htree_dirblock_to_tree: bad entry in directory #15925751: rec_len % 4 != 0 - offset=0, inode=209891641, rec_len=929, name_len=111
[117850.834042] EXT3-fs error (device sdb3): htree_dirblock_to_tree: bad entry in directory #15925702: rec_len % 4 != 0 - offset=0, inode=1039876091, rec_len=25083, name_len=251
[117850.845244] EXT3-fs error (device sdb3): htree_dirblock_to_tree: bad entry in directory #15925644: directory entry across blocks - offset=0, inode=2220972143, rec_len=51920, name_len=212
[117850.961611] EXT3-fs error (device sdb3): htree_dirblock_to_tree: bad entry in directory #15925567: rec_len % 4 != 0 - offset=0, inode=3997141093, rec_len=56157, name_len=201
[117850.984283] EXT3-fs error (device sdb3): htree_dirblock_to_tree: bad entry in directory #15925629: directory entry across blocks - offset=0, inode=2831680954, rec_len=17876, name_len=70
[117851.046535] EXT3-fs error (device sdb3): htree_dirblock_to_tree: bad entry in directory #15925607: directory entry across blocks - offset=0, inode=3181783610, rec_len=57888, name_len=37
[117851.066193] EXT3-fs error (device sdb3): htree_dirblock_to_tree: bad entry in directory #15925624: rec_len % 4 != 0 - offset=0, inode=2846975548, rec_len=653, name_len=62
[117851.281007] init_special_inode: bogus i_mode (155462)
[117851.281938] init_special_inode: bogus i_mode (115042)
[117851.282829] init_special_inode: bogus i_mode (50721)
[117851.458341] EXT3-fs error (device sdb3): htree_dirblock_to_tree: bad entry in directory #15925447: directory entry across blocks - offset=0, inode=1674135702, rec_len=21648, name_len=253
[117851.476468] EXT3-fs error (device sdb3): htree_dirblock_to_tree: bad entry in directory #15925431: directory entry across blocks - offset=0, inode=4294967295, rec_len=65536, name_len=255
[117851.501838] EXT3-fs error (device sdb3): htree_dirblock_to_tree: bad entry in directory #15925649: rec_len % 4 != 0 - offset=0, inode=2159276369, rec_len=1610, name_len=56
[117851.541795] EXT3-fs error (device sdb3): htree_dirblock_to_tree: bad entry in directory #15925812: directory entry across blocks - offset=0, inode=2327330369, rec_len=36724, name_len=102
[117851.668617] EXT3-fs error (device sdb3): htree_dirblock_to_tree: bad entry in directory #15925592: directory entry across blocks - offset=0, inode=1236707716, rec_len=35320, name_len=15
[117851.735214] EXT3-fs error (device sdb3): htree_dirblock_to_tree: bad entry in directory #15925735: rec_len % 4 != 0 - offset=0, inode=817422450, rec_len=8949, name_len=199
[165837.038601] nm-connection-e[19064]: segfault at 087d8b3c eip b728c613 esp bfcc8f2c error 4
george@george-desktop:~$ 
george@george-desktop:~$

---

