---
title: "boot problem"
date: 2006-01-20
forum: General Help
---

### Post by eyebrowman92 on 2006-01-20
i resently set up initng to speed up my boot time. now when i boot normally, it stops at "checking for network interface" could it be initng messed with the init scripts?  it eventually fails, and brings me to tty1 and im unabnle to switch to tty7, the graphical one.  while in tty i did a ```
touch ~/error; dmesg > ~/error
``` and found this in my home dir when i reboted (keep in mind i can still boot up using initng)```
[4294667.296000] Detected 2405.221 MHz processor.
[4294667.296000] Using pmtmr for high-res timesource
[4294667.296000] Console: colour VGA+ 80x25
[4294667.814000] Dentry cache hash table entries: 32768 (order: 5, 131072 bytes)
[4294667.815000] Inode-cache hash table entries: 16384 (order: 4, 65536 bytes)
[4294667.825000] Memory: 233996k/244928k available (1622k kernel code, 10408k reserved, 730k data, 168k init, 0k highmem)
[4294667.825000] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[4294667.825000] Calibrating delay loop... 4734.97 BogoMIPS (lpj=2367488)
[4294667.851000] Security Framework v1.0.0 initialized
[4294667.851000] SELinux:  Disabled at boot.
[4294667.851000] Mount-cache hash table entries: 512
[4294667.851000] CPU: After generic identify, caps: bfebfbff 00000000 00000000 00000000 00004400 00000000 00000000
[4294667.851000] CPU: After vendor identify, caps: bfebfbff 00000000 00000000 00000000 00004400 00000000 00000000
[4294667.851000] CPU: Trace cache: 12K uops, L1 D cache: 8K
[4294667.851000] CPU: L2 cache: 128K
[4294667.851000] CPU: After all inits, caps: bfebfbff 00000000 00000000 00000080 00004400 00000000 00000000
[4294667.851000] Intel machine check architecture supported.
[4294667.851000] Intel machine check reporting enabled on CPU#0.
[4294667.851000] CPU0: Intel P4/Xeon Extended MCE MSRs (12) available
[4294667.851000] CPU0: Thermal monitoring enabled
[4294667.851000] CPU: Intel(R) Celeron(R) CPU 2.40GHz stepping 09
[4294667.851000] Enabling fast FPU save and restore... done.
[4294667.851000] Enabling unmasked SIMD FPU exception support... done.
[4294667.851000] Checking 'hlt' instruction... OK.
[4294667.855000] checking if image is initramfs... it is
[4294668.485000] Freeing initrd memory: 5497k freed
[4294668.486000] ACPI: Looking for DSDT in initrd... not found!
[4294668.533000]  not found!
[4294668.540000] ENABLING IO-APIC IRQs
[4294668.540000] ..TIMER: vector=0x31 pin1=2 pin2=-1
[4294668.651000] NET: Registered protocol family 16
[4294668.651000] ACPI: bus type pci registered
[4294668.651000] PCI: PCI BIOS revision 2.10 entry at 0xf0031, last bus=1
[4294668.651000] PCI: Using configuration type 1
[4294668.651000] mtrr: v2.0 (20020519)
[4294668.652000] ACPI: Subsystem revision 20050729
[4294668.659000] ACPI: Interpreter enabled
[4294668.659000] ACPI: Using IOAPIC for interrupt routing
[4294668.661000] ACPI: PCI Root Bridge [PCI0] (0000:00)
[4294668.661000] PCI: Probing PCI hardware (bus 00)
[4294668.661000] ACPI: Assume root bridge [\_SB_.PCI0] segment is 0
[4294668.664000] Boot video device is 0000:01:00.0
[4294668.671000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[4294668.683000] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 7 10 *11 14 15)
[4294668.683000] ACPI: PCI Interrupt Link [LNKB] (IRQs *3 4 5 7 10 11 14 15)
[4294668.683000] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 7 *10 11 14 15)
[4294668.684000] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 *5 7 10 11 14 15)
[4294668.684000] Linux Plug and Play Support v0.97 (c) Adam Belay
[4294668.684000] pnp: PnP ACPI init
[4294668.691000] pnp: PnP ACPI: found 12 devices
[4294668.692000] PnPBIOS: Disabled by ACPI PNP
[4294668.692000] PCI: Using ACPI for IRQ routing
[4294668.692000] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[4294668.697000] audit: initializing netlink socket (disabled)
[4294668.697000] audit: initialized
[4294668.698000] VFS: Disk quotas dquot_6.5.1
[4294668.698000] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[4294668.698000] devfs: 2004-01-31 Richard Gooch (rgooch@atnf.csiro.au)
[4294668.698000] devfs: boot_options: 0x0
[4294668.698000] Initializing Cryptographic API
[4294668.698000] isapnp: Scanning for PnP cards...
[4294669.052000] isapnp: No Plug & Play device found
[4294669.150000] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f03:PS2M] at 0x60,0x64 irq 1,12
[4294669.151000] serio: i8042 AUX port at 0x60,0x64 irq 12
[4294669.151000] serio: i8042 KBD port at 0x60,0x64 irq 1
[4294669.151000] Serial: 8250/16550 driver $Revision: 1.90 $ 48 ports, IRQ sharing enabled
[4294669.151000] ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[4294669.161000] ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[4294669.161000] ACPI: PCI Interrupt 0000:00:0a.0[A] -> GSI 18 (level, low) -> IRQ 18
[4294669.162000] ttyS15 at I/O 0xee08 (irq = 18) is a 16450
[4294669.162000] ttyS44 at I/O 0xee10 (irq = 18) is a 8250
[4294669.163000] ttyS45 at I/O 0xee18 (irq = 18) is a 16450
[4294669.163000] ttyS46 at I/O 0xee20 (irq = 18) is a 8250
[4294669.163000] ttyS47 at I/O 0xee28 (irq = 18) is a 8250
[4294669.173000] io scheduler noop registered
[4294669.173000] io scheduler anticipatory registered
[4294669.173000] io scheduler deadline registered
[4294669.173000] io scheduler cfq registered
[4294669.175000] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[4294669.175000] NET: Registered protocol family 2
[4294669.184000] IP: routing cache hash table of 2048 buckets, 16Kbytes
[4294669.184000] TCP established hash table entries: 8192 (order: 4, 65536 bytes)
[4294669.184000] TCP bind hash table entries: 8192 (order: 3, 32768 bytes)
[4294669.184000] TCP: Hash tables configured (established 8192 bind 8192)
[4294669.184000] NET: Registered protocol family 8
[4294669.184000] NET: Registered protocol family 20
[4294669.185000] ACPI wakeup devices: 
[4294669.185000] PCI0 PS2K PS2M AC97 MC97 ILAN USB1 USB2 USB3 EHCI PWRB SLPB 
[4294669.185000] ACPI: (supports S0 S1 S3 S4 S5)
[4294669.185000] Freeing unused kernel memory: 168k freed
[4294669.205000] input: AT Translated Set 2 keyboard on isa0060/serio0
[4294669.239000] vga16fb: initializing
[4294669.239000] vga16fb: mapped to 0xc00a0000
[4294669.371000] Console: switching to colour frame buffer device 80x30
[4294669.371000] fb0: VGA16 VGA frame buffer device
[4294670.521000] Capability LSM initialized
[4294670.545000] NET: Registered protocol family 1
[4294670.577000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[4294670.577000] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[4294670.577000] ACPI: bus type ide registered
[4294670.588000] VP_IDE: IDE controller at PCI slot 0000:00:11.1
[4294670.588000] ACPI: PCI Interrupt 0000:00:11.1[A]: no GSI
[4294670.588000] PCI: Via IRQ fixup for 0000:00:11.1, from 255 to 15
[4294670.588000] VP_IDE: chipset revision 6
[4294670.588000] VP_IDE: not 100% native mode: will probe irqs later
[4294670.588000] VP_IDE: VIA vt8235 (rev 00) IDE UDMA133 controller on pci0000:00:11.1
[4294670.588000]     ide0: BM-DMA at 0xfc00-0xfc07, BIOS settings: hda:DMA, hdb:pio
[4294670.588000]     ide1: BM-DMA at 0xfc08-0xfc0f, BIOS settings: hdc:DMA, hdd:DMA
[4294670.588000] Probing IDE interface ide0...
[4294670.972000] hda: WDC WD400BB-22FJA0, ATA DISK drive
[4294671.584000] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[4294671.584000] Probing IDE interface ide1...
[4294672.376000] hdc: SONY CD-RW CRX230EE, ATAPI CD/DVD-ROM drive
[4294673.090000] hdd: JLMS XJ-HD166S, ATAPI CD/DVD-ROM drive
[4294673.141000] ide1 at 0x170-0x177,0x376 on irq 15
[4294673.141000] Probing IDE interface ide2...
[4294673.654000] Probing IDE interface ide3...
[4294674.166000] Probing IDE interface ide4...
[4294674.678000] Probing IDE interface ide5...
[4294675.198000] hda: max request size: 128KiB
[4294675.212000] hda: 78165360 sectors (40020 MB) w/2048KiB Cache, CHS=65535/16/63, UDMA(100)
[4294675.212000] hda: cache flushes supported
[4294675.212000]  /dev/ide/host0/bus0/target0/lun0: p1 p2 p3 p4
[4294675.245000] hdc: ATAPI 40X CD-ROM CD-R/RW drive, 1536kB Cache
[4294675.245000] Uniform CD-ROM driver Revision: 3.20
[4294675.256000] hdd: ATAPI 48X DVD-ROM drive, 512kB Cache
[4294676.567000] Attempting manual resume
[4294676.572000] swsusp: Suspend partition has wrong signature?
[4294676.616000] usbcore: registered new driver usbfs
[4294676.616000] usbcore: registered new driver hub
[4294676.618000] USB Universal Host Controller Interface driver v2.2
[4294676.618000] ACPI: PCI Interrupt 0000:00:10.0[A] -> GSI 21 (level, low) -> IRQ 21
[4294676.618000] PCI: Via IRQ fixup for 0000:00:10.0, from 11 to 5
[4294676.618000] uhci_hcd 0000:00:10.0: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller
[4294676.680000] uhci_hcd 0000:00:10.0: new USB bus registered, assigned bus number 1
[4294676.680000] uhci_hcd 0000:00:10.0: irq 21, io base 0x0000e000
[4294676.680000] hub 1-0:1.0: USB hub found
[4294676.680000] hub 1-0:1.0: 2 ports detected
[4294676.683000] ACPI: PCI Interrupt 0000:00:10.1[B] -> GSI 21 (level, low) -> IRQ 21
[4294676.683000] PCI: Via IRQ fixup for 0000:00:10.1, from 3 to 5
[4294676.683000] uhci_hcd 0000:00:10.1: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (#2)
[4294676.745000] uhci_hcd 0000:00:10.1: new USB bus registered, assigned bus number 2
[4294676.745000] uhci_hcd 0000:00:10.1: irq 21, io base 0x0000e080
[4294676.745000] hub 2-0:1.0: USB hub found
[4294676.745000] hub 2-0:1.0: 2 ports detected
[4294676.748000] ACPI: PCI Interrupt 0000:00:10.2[C] -> GSI 21 (level, low) -> IRQ 21
[4294676.748000] PCI: Via IRQ fixup for 0000:00:10.2, from 10 to 5
[4294676.748000] uhci_hcd 0000:00:10.2: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (#3)
[4294676.810000] uhci_hcd 0000:00:10.2: new USB bus registered, assigned bus number 3
[4294676.810000] uhci_hcd 0000:00:10.2: irq 21, io base 0x0000ec00
[4294676.810000] hub 3-0:1.0: USB hub found
[4294676.810000] hub 3-0:1.0: 2 ports detected
[4294676.845000] ACPI: PCI Interrupt 0000:00:10.3[D] -> GSI 21 (level, low) -> IRQ 21
[4294676.846000] ehci_hcd 0000:00:10.3: VIA Technologies, Inc. USB 2.0
[4294676.846000] ehci_hcd 0000:00:10.3: new USB bus registered, assigned bus number 4
[4294676.846000] ehci_hcd 0000:00:10.3: irq 21, io mem 0xffaff800
[4294676.846000] ehci_hcd 0000:00:10.3: USB 2.0 initialized, EHCI 1.00, driver 10 Dec 2004
[4294676.846000] hub 4-0:1.0: USB hub found
[4294676.846000] hub 4-0:1.0: 6 ports detected
[4294676.910000] via-rhine.c:v1.10-LK1.2.0-2.6 June-10-2004 Written by Donald Becker
[4294676.911000] ACPI: PCI Interrupt 0000:00:12.0[A] -> GSI 23 (level, low) -> IRQ 23
[4294676.911000] PCI: Via IRQ fixup for 0000:00:12.0, from 11 to 7
[4294676.915000] eth0: VIA Rhine II at 0x1e800, 00:0e:a6:9b:b8:75, IRQ 23.
[4294676.915000] eth0: MII PHY found at address 1, status 0x786d advertising 01e1 Link 45e1.
[4294677.712000] usb 4-4: new high speed USB device using ehci_hcd and address 3
[4294677.954000] usb 1-2: new low speed USB device using uhci_hcd and address 2
[4294678.951000] usbcore: registered new driver hiddev
[4294678.971000] input: USB HID v1.10 Mouse [Microsoft Microsoft 5-Button Mouse with IntelliEye(TM)] on usb-0000:00:10.0-2
[4294678.971000] usbcore: registered new driver usbhid
[4294678.971000] drivers/usb/input/hid-core.c: v2.01:USB HID core driver
[4294679.018000] SCSI subsystem initialized
[4294679.021000] Initializing USB Mass Storage driver...
[4294679.021000] scsi0 : SCSI emulation for USB Mass Storage devices
[4294679.021000] usb-storage: device found at 3
[4294679.021000] usb-storage: waiting for device to settle before scanning
[4294679.021000] usbcore: registered new driver usb-storage
[4294679.021000] USB Mass Storage support registered.
[4294680.489000] ACPI: CPU0 (power states: C1[C1])
[4294680.489000] ACPI: Processor [CPU1] (supports 16 throttling states)
[4294680.781000] Attempting manual resume
[4294680.781000] swsusp: Suspend partition has wrong signature?
[4294680.796000] EXT3-fs: INFO: recovery required on readonly filesystem.
[4294680.796000] EXT3-fs: write access will be enabled during recovery.
[4294681.643000] kjournald starting.  Commit interval 5 seconds
[4294681.643000] EXT3-fs: recovery complete.
[4294681.646000] EXT3-fs: mounted filesystem with ordered data mode.
[4294682.544000] md: md driver 0.90.1 MAX_MD_DEVS=256, MD_SB_DISKS=27
[4294684.022000]   Vendor: LEXAR     Model: JUMPDRIVE         Rev: 1000
[4294684.022000]   Type:   Direct-Access                      ANSI SCSI revision: 00
[4294684.040000] usb-storage: device scan complete
[4294686.218000] SCSI device sda: 2030592 512-byte hdwr sectors (1040 MB)
[4294686.219000] sda: Write Protect is off
[4294686.219000] sda: Mode Sense: 43 00 00 00
[4294686.219000] sda: assuming drive cache: write through
[4294686.227000] SCSI device sda: 2030592 512-byte hdwr sectors (1040 MB)
[4294686.228000] sda: Write Protect is off
[4294686.228000] sda: Mode Sense: 43 00 00 00
[4294686.228000] sda: assuming drive cache: write through
[4294686.228000]  /dev/scsi/host0/bus0/target0/lun0: p1
[4294686.232000] Attached scsi removable disk sda at scsi0, channel 0, id 0, lun 0
[4294688.798000] Adding 3911816k swap on /dev/hda4.  Priority:-1 extents:1
[4294689.078000] EXT3 FS on hda2, internal journal
[4294695.958000] parport: PnPBIOS parport detected.
[4294695.958000] parport0: PC-style at 0x378, irq 7 [PCSPP]
[4294696.053000] lp0: using parport0 (interrupt-driven).
[4294696.126000] mice: PS/2 mouse device common for all mice
[4294696.404000] logips2pp: Detected unknown logitech mouse model 1
[4294696.492000] input: PS/2 Logitech Mouse on isa0060/serio1
[4294697.885000] ts: Compaq touchscreen protocol output
[4294700.964000] device-mapper: 4.4.0-ioctl (2005-01-12) initialised: dm-devel@redhat.com
[4294701.864000] cdrom: hdc: mrw address space DMA selected
[4294701.868000] cdrom: open failed.
[4294703.037000] kjournald starting.  Commit interval 5 seconds
[4294703.037000] EXT3 FS on hda3, internal journal
[4294703.037000] EXT3-fs: mounted filesystem with ordered data mode.
[4294703.052000] NTFS driver 2.1.22 [Flags: R/O MODULE].
[4294703.129000] NTFS volume version 3.1.
[4294705.142000] Linux agpgart interface v0.101 (c) Dave Jones
[4294705.164000] agpgart: Detected VIA P4M266x/P4N266 chipset
[4294705.206000] agpgart: AGP aperture is 64M @ 0xe0000000
[4294705.530000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[4294705.555000] shpchp: shpc_init : shpc_cap_offset == 0
[4294705.555000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[4294706.227000] irda_init()
[4294706.227000] NET: Registered protocol family 23
[4294706.804000] via82xx: Assuming DXS channels with 48k fixed sample rate.
[4294706.804000]          Please try dxs_support=5 option
[4294706.804000]          and report if it works on your machine.
[4294706.804000]          For more details, read ALSA-Configuration.txt.
[4294706.804000] ACPI: PCI Interrupt 0000:00:11.5[C] -> GSI 22 (level, low) -> IRQ 22
[4294706.804000] PCI: Via IRQ fixup for 0000:00:11.5, from 10 to 6
[4294706.804000] PCI: Setting latency timer of device 0000:00:11.5 to 64
[4294709.929000] Real Time Clock Driver v1.12
[4294710.068000] input: PC Speaker
[4294710.346000] Floppy drive(s): fd0 is 1.44M
[4294710.361000] FDC 0 is a post-1991 82077
[4294810.040000] ACPI: Power Button (FF) [PWRF]
[4294810.040000] ACPI: Power Button (CM) [PWRB]
[4294810.040000] ACPI: Sleep Button (CM) [SLPB]
[4294810.240000] ibm_acpi: ec object not found
[4294811.973000] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[4294811.973000] apm: overridden by ACPI.
[4294813.348000] Bluetooth: Core ver 2.7
[4294813.348000] NET: Registered protocol family 31
[4294813.348000] Bluetooth: HCI device and connection manager initialized
[4294813.348000] Bluetooth: HCI socket layer initialized
[4294813.368000] Bluetooth: L2CAP ver 2.7
[4294813.368000] Bluetooth: L2CAP socket layer initialized
[4294813.374000] Bluetooth: RFCOMM ver 1.5
[4294813.374000] Bluetooth: RFCOMM socket layer initialized
[4294813.374000] Bluetooth: RFCOMM TTY layer initialized

``` does anyone know how i can fix this?

---

### Post by eyebrowman92 on 2006-01-20
please someone help

---

