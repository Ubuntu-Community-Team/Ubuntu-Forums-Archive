---
title: "PC does not power down completely"
date: 2006-01-27
forum: General Help
---

### Post by beerorkid on 2006-01-27
I reboot or shutdown and I have to hard power down each time

?

---

### Post by dcstar on 2006-01-27
[QUOTE=beerorkid]I reboot or shutdown and I have to hard power down each time

?[/QUOTE]
What kernel are you using.

---

### Post by beerorkid on 2006-01-27
2.6.12-10-386

---

### Post by az on 2006-01-27
Post your dmesg


from a terminal type

dmesg


to see if you are using APM or ACPI.  The messages will say why either one (or both) are not being used.

---

### Post by beerorkid on 2006-01-27
thanks for the response

I saw your other post dealing with this
[http://www.ubuntuforums.org/showthread.php?t=70520&highlight=apm](http://www.ubuntuforums.org/showthread.php?t=70520&highlight=apm)

I did see a bunch of acpi errors while looking through the dmesg

I am at work now.  but will go home later and mess with it.

I was wondering if there is something I can edit while in ubuntu or is it something that must be done the way you said before.

---

### Post by az on 2006-01-27
[QUOTE=beerorkid]I was wondering if there is something I can edit while in ubuntu or is it something that must be done the way you said before.[/QUOTE]

I am not sure.  You can try to unload all the acpi-related modules and then try to load the apm one.  If it still doesn't work, I would try rebooting and preventing the kernel from loading the ACPI modules in the first place, so you may as well just skip to that step and reboot with the apm=force option.

Also, see what your motherboard is set to.  Go in the BIOS (CMOS) and see what power management options you have.

---

### Post by beerorkid on 2006-01-27
```
sramos@ubuntu:~$ dmesg | more
che hash table of 16384 buckets, 128Kbytes
[4294669.862000] TCP established hash table entries: 262144 (order: 9, 2097152 bytes)
[4294669.864000] TCP bind hash table entries: 65536 (order: 6, 262144 bytes)
[4294669.864000] TCP: Hash tables configured (established 262144 bind 65536)
[4294669.866000] NET: Registered protocol family 8
[4294669.866000] NET: Registered protocol family 20
[4294669.866000] ACPI wakeup devices:
[4294669.866000] PCI0 USB0 USB1 USB2 AUDO MODM  P2P PS2K
[4294669.866000] ACPI: (supports S0 S1 S3 S4 S5)
[4294669.866000] Freeing unused kernel memory: 224k freed
[4294669.890000] vga16fb: initializing
[4294669.890000] vga16fb: mapped to 0xc00a0000
[4294670.228000] Console: switching to colour frame buffer device 80x30
[4294670.228000] fb0: VGA16 VGA frame buffer device
[4294671.524000] Capability LSM initialized
[4294671.540000] NET: Registered protocol family 1
[4294671.558000] SCSI subsystem initialized
[4294671.558000] libata version 1.11 loaded.
[4294671.560000] sata_sil version 0.9
[4294671.560000] ACPI: PCI Interrupt 0000:00:12.0[A] -> GSI 22 (level, low) -> IRQ 22
[4294671.560000] ata1: SATA max UDMA/100 cmd 0xF886C080 ctl 0xF886C08A bmdma 0xF886C000 irq 22
[4294671.560000] ata2: SATA max UDMA/100 cmd 0xF886C0C0 ctl 0xF886C0CA bmdma 0xF886C008 irq 22
[4294671.934000] ata1: dev 0 cfg 49:2f00 82:74eb 83:7f63 84:4003 85:74e9 86:3c43 87:4003 88:207f
[4294671.934000] ata1: dev 0 ATA, max UDMA/133, 145226112 sectors: lba48
[4294671.936000] ata1: dev 0 configured for UDMA/100
[4294671.936000] scsi0 : sata_sil
[4294672.342000] ata2: dev 0 cfg 49:2f00 82:346b 83:7f01 84:4003 85:3469 86:3c01 87:4003 88:203f
[4294672.342000] ata2: dev 0 ATA, max UDMA/100, 586072368 sectors: lba48
[4294672.342000] ata2: dev 0 configured for UDMA/100
[4294672.342000] scsi1 : sata_sil
[4294672.342000]   Vendor: ATA       Model: WDC WD740GD-00FL  Rev: 33.0
[4294672.342000]   Type:   Direct-Access                      ANSI SCSI revision: 05
[4294672.342000]   Vendor: ATA       Model: WDC WD3000JD-00K  Rev: 08.0
[4294672.342000]   Type:   Direct-Access                      ANSI SCSI revision: 05
[4294672.362000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[4294672.362000] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[4294672.362000] ACPI: bus type ide registered
[4294672.372000] ATIIXP: IDE controller at PCI slot 0000:00:14.1
[4294672.372000] ACPI: PCI Interrupt 0000:00:14.1[A] -> GSI 16 (level, low) -> IRQ 16
[4294672.372000] ATIIXP: chipset revision 0
[4294672.372000] ATIIXP: not 100% native mode: will probe irqs later
[4294672.372000]     ide0: BM-DMA at 0xf900-0xf907, BIOS settings: hda:pio, hdb:pio
[4294672.372000]     ide1: BM-DMA at 0xf908-0xf90f, BIOS settings: hdc:pio, hdd:pio
[4294672.372000] Probing IDE interface ide0...
[4294672.910000] Probing IDE interface ide1...
[4294673.602000] hdc: PLEXTOR DVDR PX-740A, ATAPI CD/DVD-ROM drive
[4294674.330000] hdd: HL-DT-STDVD-ROM GDR8162B, ATAPI CD/DVD-ROM drive
[4294674.382000] ide1 at 0x170-0x177,0x376 on irq 15
[4294674.382000] Probing IDE interface ide0...
[4294674.920000] Probing IDE interface ide2...
[4294675.444000] Probing IDE interface ide3...
[4294675.968000] Probing IDE interface ide4...
[4294676.492000] Probing IDE interface ide5...
[4294677.024000] hdc: ATAPI 48X DVD-ROM DVD-R CD-R/RW drive, 2048kB Cache
[4294677.024000] Uniform CD-ROM driver Revision: 3.20
[4294677.048000] hdd: ATAPI 48X DVD-ROM drive, 256kB Cache
[4294677.148000] SCSI device sda: 145226112 512-byte hdwr sectors (74356 MB)
[4294677.148000] SCSI device sda: drive cache: write back
[4294677.148000] SCSI device sda: 145226112 512-byte hdwr sectors (74356 MB)
[4294677.148000] SCSI device sda: drive cache: write back
[4294677.148000]  /dev/scsi/host0/bus0/target0/lun0: p1 p2 p3 < p5 >
[4294677.200000] Attached scsi disk sda at scsi0, channel 0, id 0, lun 0
[4294677.200000] SCSI device sdb: 586072368 512-byte hdwr sectors (300069 MB)
[4294677.200000] SCSI device sdb: drive cache: write back
[4294677.200000] SCSI device sdb: 586072368 512-byte hdwr sectors (300069 MB)
[4294677.200000] SCSI device sdb: drive cache: write back
[4294677.200000]  /dev/scsi/host1/bus0/target0/lun0: p1
[4294677.210000] Attached scsi disk sdb at scsi1, channel 0, id 0, lun 0
[4294677.808000] Attempting manual resume
[4294677.808000] swsusp: Suspend partition has wrong signature?
[4294677.856000] usbcore: registered new driver usbfs
[4294677.856000] usbcore: registered new driver hub
[4294677.856000] ohci_hcd: 2004 Nov 08 USB 1.1 'Open' Host Controller (OHCI) Driver (PCI)
[4294677.856000] ACPI: PCI Interrupt 0000:00:13.0[A] -> GSI 19 (level, low) -> IRQ 19
[4294677.856000] ohci_hcd 0000:00:13.0: PCI device 1002:4374 (ATI Technologies Inc)
[4294677.894000] ohci_hcd 0000:00:13.0: new USB bus registered, assigned bus number 1
[4294677.894000] ohci_hcd 0000:00:13.0: irq 19, io mem 0xfe02e000
[4294677.954000] hub 1-0:1.0: USB hub found
[4294677.954000] hub 1-0:1.0: 4 ports detected
[4294677.960000] ACPI: PCI Interrupt 0000:00:13.1[A] -> GSI 19 (level, low) -> IRQ 19
[4294677.960000] ohci_hcd 0000:00:13.1: PCI device 1002:4375 (ATI Technologies Inc)
[4294677.985000] ohci_hcd 0000:00:13.1: new USB bus registered, assigned bus number 2
[4294677.985000] ohci_hcd 0000:00:13.1: irq 19, io mem 0xfe02d000
[4294678.045000] hub 2-0:1.0: USB hub found
[4294678.045000] hub 2-0:1.0: 4 ports detected
[4294678.073000] ACPI: PCI Interrupt 0000:00:13.2[A] -> GSI 19 (level, low) -> IRQ 19
[4294678.073000] ehci_hcd 0000:00:13.2: PCI device 1002:4373 (ATI Technologies Inc)
[4294678.073000] ehci_hcd 0000:00:13.2: new USB bus registered, assigned bus number 3
[4294678.073000] ehci_hcd 0000:00:13.2: irq 19, io mem 0xfe02c000
[4294678.073000] ehci_hcd 0000:00:13.2: USB 2.0 initialized, EHCI 1.00, driver 10 Dec 2004
[4294678.075000] hub 3-0:1.0: USB hub found
[4294678.075000] hub 3-0:1.0: 8 ports detected
[4294678.217000] 8139cp: 10/100 PCI Ethernet driver v1.2 (Mar 22, 2004)
[4294678.217000] 8139cp: pci dev 0000:02:03.0 (id 10ec:8139 rev 10) is not an 8139C+ compatible chip
[4294678.217000] 8139cp: Try the "8139too" driver instead.
[4294678.219000] 8139too Fast Ethernet driver 0.9.27
[4294678.219000] ACPI: PCI Interrupt 0000:02:03.0[A] -> GSI 21 (level, low) -> IRQ 21
[4294678.221000] eth0: RealTek RTL8139 at 0xde00, 00:15:f2:68:1f:d7, IRQ 21
[4294678.221000] eth0:  Identified 8139 chip type 'RTL-8101'
[4294679.319000] usb 2-1: new full speed USB device using ohci_hcd and address 2[4294679.667000] usb 2-2: new low speed USB device using ohci_hcd and address 3
[4294680.061000] usb 1-1: new low speed USB device using ohci_hcd and address 2
[4294680.411000] usb 1-4: new full speed USB device using ohci_hcd and address 3[4294680.557000] usbcore: registered new driver hiddev
[4294690.601000] drivers/usb/input/hid-core.c: usb_submit_urb(ctrl) failed
[4294690.601000] drivers/usb/input/hid-core.c: timeout initializing reports
[4294690.601000]
[4294690.605000] input: USB HID v1.10 Joystick [Logitech Logitech Extreme 3D] on usb-0000:00:13.1-2
[4294690.619000] input: USB HID v1.10 Mouse [Logitech USB-PS/2 Optical Mouse] on usb-0000:00:13.0-1
[4294690.619000] usbcore: registered new driver usbhid
[4294690.619000] drivers/usb/input/hid-core.c: v2.01:USB HID core driver
[4294691.463000] ACPI: Fan [FAN] (on)
[4294691.469000] ACPI: CPU0 (power states: C1[C1])
[4294691.469000] ACPI: Processor [CPU0] (supports 8 throttling states)
[4294691.475000] ACPI: Thermal Zone [THRM] (40 C)
[4294691.647000] Attempting manual resume
[4294691.647000] swsusp: Suspend partition has wrong signature?
[4294691.671000] kjournald starting.  Commit interval 5 seconds
[4294691.671000] EXT3-fs: mounted filesystem with ordered data mode.
[4294693.041000] md: md driver 0.90.1 MAX_MD_DEVS=256, MD_SB_DISKS=27
[4294697.185000] Adding 907632k swap on /dev/sda5.  Priority:-1 extents:1
[4294697.365000] EXT3 FS on sda2, internal journal
[4294704.803000] lp: driver loaded but no devices found
[4294704.847000] mice: PS/2 mouse device common for all mice
[4294704.927000] Linux agpgart interface v0.101 (c) Dave Jones
[4294704.957000] nvidia: module license 'NVIDIA' taints kernel.
[4294704.997000] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 18 (level, low) -> IRQ 18
[4294704.997000] PCI: Setting latency timer of device 0000:01:00.0 to 64
[4294704.997000] NVRM: loading NVIDIA Linux x86 NVIDIA Kernel Module  1.0-7667
Fri Jun 17 07:01:04 PDT 2005
[4294710.673000] device-mapper: 4.4.0-ioctl (2005-01-12) initialised: dm-devel@redhat.com
[4294711.317000] cdrom: open failed.
[4294713.253000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[4294713.261000] shpchp: acpi_shpchprm:\_SB_.PCI0 evaluate _BBN fail=0x5
[4294713.261000] shpchp: acpi_shpchprm:get_device PCI ROOT HID fail=0x5
[4294714.107000] ACPI: PCI Interrupt 0000:00:14.5[B] -> GSI 17 (level, low) -> IRQ 17
[4294716.833000] Initializing USB Mass Storage driver...
[4294716.841000] scsi2 : SCSI emulation for USB Mass Storage devices
[4294716.847000] usb-storage: device found at 3
[4294716.847000] usb-storage: waiting for device to settle before scanning
[4294716.847000] usbcore: registered new driver usb-storage
[4294716.847000] USB Mass Storage support registered.
[4294717.047000] drivers/usb/class/usblp.c: usblp0: USB Bidirectional printer dev 2 if 0 alt 0 proto 2 vid 0x04A9 pid 0x1093
[4294717.055000] usbcore: registered new driver usblp
[4294717.055000] drivers/usb/class/usblp.c: v0.13: USB Printer Device Class driver
[4294717.459000] Real Time Clock Driver v1.12
[4294717.561000] input: PC Speaker
[4294718.349000] ts: Compaq touchscreen protocol output
[4294719.997000] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[4294720.013000] NET: Registered protocol family 17
[4294721.855000]   Vendor: Generic   Model: USB SD Reader     Rev: 1.00
[4294721.855000]   Type:   Direct-Access                      ANSI SCSI revision: 00
[4294721.917000] Attached scsi removable disk sdc at scsi2, channel 0, id 0, lun 0
[4294721.927000]   Vendor: Generic   Model: USB CF Reader     Rev: 1.01
[4294721.927000]   Type:   Direct-Access                      ANSI SCSI revision: 00
[4294722.011000] Attached scsi removable disk sdd at scsi2, channel 0, id 0, lun 1
[4294722.025000]   Vendor: Generic   Model: USB SM Reader     Rev: 1.02
[4294722.025000]   Type:   Direct-Access                      ANSI SCSI revision: 00
[4294722.091000] Attached scsi removable disk sde at scsi2, channel 0, id 0, lun 2
[4294722.105000]   Vendor: Generic   Model: USB MS Reader     Rev: 1.03
[4294722.105000]   Type:   Direct-Access                      ANSI SCSI revision: 00
[4294722.177000] Attached scsi removable disk sdf at scsi2, channel 0, id 0, lun 3
[4294722.185000] usb-storage: device scan complete
[4294727.071000] NET: Registered protocol family 10
[4294727.073000] Disabled Privacy Extensions on device c02eb280(lo)
[4294727.073000] IPv6 over IPv4 tunneling driver
[4294729.153000] ACPI: Power Button (FF) [PWRF]
[4294729.153000] ACPI: Power Button (CM) [PWRB]
[4294729.323000] ibm_acpi: ec object not found
[4294737.352000] eth0: no IPv6 routers present
[4294740.714000] apm: BIOS not found.
[4294742.670000] powernow-k8: Found 1 AMD Athlon 64 / Opteron processors (version 1.40.4)
[4294742.670000] powernow-k8:    0 : fid 0xe (2200 MHz), vid 0x6 (1400 mV)
[4294742.670000] powernow-k8:    1 : fid 0xc (2000 MHz), vid 0x8 (1350 mV)
[4294742.670000] powernow-k8:    2 : fid 0xa (1800 MHz), vid 0xa (1300 mV)
[4294742.670000] powernow-k8:    3 : fid 0x2 (1000 MHz), vid 0x12 (1100 mV)
[4294742.672000] cpu_init done, current fid 0xe, vid 0x6
[4294743.494000] Bluetooth: Core ver 2.7
[4294743.494000] NET: Registered protocol family 31
[4294743.494000] Bluetooth: HCI device and connection manager initialized
[4294743.494000] Bluetooth: HCI socket layer initialized
[4294743.550000] Bluetooth: L2CAP ver 2.7
[4294743.550000] Bluetooth: L2CAP socket layer initialized
[4294743.592000] Bluetooth: RFCOMM ver 1.5
[4294743.592000] Bluetooth: RFCOMM socket layer initialized
[4294743.592000] Bluetooth: RFCOMM TTY layer initialized
[4294798.328000] UDF-fs: No VRS found
[4294798.471000] UDF-fs: No VRS found
[4294798.610000] ISO 9660 Extensions: Microsoft Joliet Level 3
[4294798.645000] ISOFS: changing to secondary root
[4296436.084000] APIC error on CPU0: 00(40)
[4296514.836000] APIC error on CPU0: 40(40)
[4296632.956000] APIC error on CPU0: 40(40)
[4297144.833000] APIC error on CPU0: 40(40)
[4297394.203000] APIC error on CPU0: 40(40)
[4297853.579000] APIC error on CPU0: 40(40)
[4298431.071000] APIC error on CPU0: 40(40)
[4298759.197000] APIC error on CPU0: 40(40)
[4299389.194000] APIC error on CPU0: 40(40)
[4299979.815000] APIC error on CPU0: 40(40)
[4300805.340000] APIC error on CPU0: 40(40)
[4301476.061000] APIC error on CPU0: 40(40)
[4301633.558000] APIC error on CPU0: 40(40)
[4301633.561000] APIC error on CPU0: 40(40)
[4301725.431000] APIC error on CPU0: 40(40)
[4301896.056000] APIC error on CPU0: 40(40)
[4302434.178000] APIC error on CPU0: 40(40)
[4302801.679000] APIC error on CPU0: 40(40)
[4302893.550000] APIC error on CPU0: 40(40)
[4303064.175000] APIC error on CPU0: 40(40)
[4305518.544000] APIC error on CPU0: 40(40)
[4305689.167000] APIC error on CPU0: 40(40)
[4306017.287000] APIC error on CPU0: 40(40)
[4306726.038000] APIC error on CPU0: 40(40)
[4306726.073000] APIC error on CPU0: 40(40)
[4306936.036000] APIC error on CPU0: 40(40)
[4307552.909000] APIC error on CPU0: 40(40)
[4307605.408000] APIC error on CPU0: 40(40)
[4308642.278000] APIC error on CPU0: 40(40)
[4309928.523000] APIC error on CPU0: 40(40)
[4310689.770000] APIC error on CPU0: 40(40)
[4311218.585000] APIC error on CPU0: 40(40)
[4311227.892000] APIC error on CPU0: 40(40)
[4313012.889000] APIC error on CPU0: 40(40)
[4313144.136000] APIC error on CPU0: 40(40)
[4313603.513000] APIC error on CPU0: 40(40)
[4313791.574000] APIC error on CPU0: 40(40)
[4313971.005000] APIC error on CPU0: 40(40)
[4314233.503000] APIC error on CPU0: 40(40)
[4314429.203000] APIC error on CPU0: 40(40)
[4315231.001000] APIC error on CPU0: 40(40)
[4315441.000000] APIC error on CPU0: 40(40)
[4316097.246000] APIC error on CPU0: 40(40)
[4316805.992000] APIC error on CPU0: 40(40)
[4317855.990000] APIC error on CPU0: 40(40)
[4318354.741000] APIC error on CPU0: 40(40)
[4320848.480000] APIC error on CPU0: 40(40)
[4322397.228000] APIC error on CPU0: 40(40)
[4322528.475000] APIC error on CPU0: 40(40)
[4322607.224000] APIC error on CPU0: 40(40)
[4323459.529000] APIC error on CPU0: 40(40)
[4323735.969000] APIC error on CPU0: 40(40)
[4324274.094000] APIC error on CPU0: 40(40)
[4324523.467000] APIC error on CPU0: 40(40)
[4324733.463000] APIC error on CPU0: 40(40)
[4325691.584000] APIC error on CPU0: 40(40)
[4326030.796000] APIC error on CPU0: 40(40)
[4326899.081000] APIC error on CPU0: 40(40)
[4327529.077000] APIC error on CPU0: 40(40)
[4327817.827000] APIC error on CPU0: 40(40)
[4328285.345000] APIC error on CPU0: 40(40)
[4328526.570000] APIC error on CPU0: 40(40)
[4328565.945000] APIC error on CPU0: 40(40)
[4329326.724000] APIC error on CPU0: 40(40)
[4329904.695000] APIC error on CPU0: 40(40)
[4330784.795000] APIC error on CPU0: 40(40)
[4331138.433000] APIC error on CPU0: 40(40)
[4331138.436000] APIC error on CPU0: 40(40)
[4331196.801000] APIC error on CPU0: 40(40)
[4331570.920000] APIC error on CPU0: 40(40)
[4331690.864000] APIC error on CPU0: 40(40)
[4331800.069000] APIC error on CPU0: 40(40)
[4331806.520000] APIC error on CPU0: 40(40)
[4331976.216000] APIC error on CPU0: 40(40)
[4332109.673000] APIC error on CPU0: 40(40)

```

---

### Post by beerorkid on 2006-01-27
I followed you advice on the other thread 
> If not, give apm a shot. When you boot, go into the grub menu and press "e" to edit the ubuntu selection. Edit the kernel like by pressing "e" again. Go to the end of the line and add "apm=force" and hit enter. Then press "b" to boot.

If that fixes it, add "apm=force" to the line in /boot/grub/menu.list

## nonaltoption boot targets option
## This option controls options to pass to only the
## primary kernel menu item.
## You can have ONLY one nonaltoptions line
# nonaltoptions=quiet splash apm=force

Then run

sudo update-grub.

You can also see what your bios is set to (apm or acpi)

and it worked. Thanks azz

---

### Post by az on 2006-01-27
I could only find this bug report relevant to this issue:
[https://launchpad.net/distros/ubuntu/+bug/26399](https://launchpad.net/distros/ubuntu/+bug/26399)

Can you determine that this problem is not caused by your motherboard settings?  Also, are you able to try a Hoary live cd to see if it too has the same problem?  If it is fine in Hoary, then this is a regression and a bug that should be reported.  

I would ask you to add to that bug report.

---

### Post by hensonkid on 2006-02-01
Sorry for newbie intrusion, but I'm having the same problem - it stalls on "Shutting down, please wait" on reboot and shutdown.

I'm not sure what kernel I'm using...or how to check.  Sorry, total noob.

I did check dmesg, and I get:
> ca000: BAP1 offset error: reg=0x4000 id=0x70 offset=0x0
[4295284.648000] eth0: error -5 reading Rx descriptor. Frame dropped.
[4295290.290000] hermes @ e0aca000: BAP1 offset error: reg=0x4000 id=0x70 offset =0x0

And it's repeated several times with the leading numerals changed.

How should I proceed from here?  Please forgive my noobness, and thanks for the help.

---

### Post by hensonkid on 2006-02-01
Ok, so I learned (he can be taught) how to check my kernel version.  It's 2.6.12-10-386.  Also, here's the full report I got from dmesg:
> r: reg=0x4000 id=0x70 offset=0x0
[4296023.640000] eth0: error -5 reading Rx descriptor. Frame dropped.
[4296027.887000] hermes @ e0aca000: BAP1 offset error: reg=0x4000 id=0x70 offset =0x0
[4296027.887000] eth0: error -5 reading info frame. Frame dropped.
[4296030.186000] hermes @ e0aca000: BAP1 offset error: reg=0x4000 id=0x70 offset =0x0
[4296030.186000] eth0: error -5 reading Rx descriptor. Frame dropped.
[4296034.285000] hermes @ e0aca000: BAP1 offset error: reg=0x4000 id=0x70 offset =0x0
[4296034.285000] eth0: error -5 reading Rx descriptor. Frame dropped.
[4296036.331000] hermes @ e0aca000: BAP1 offset error: reg=0x4000 id=0x70 offset =0x0
[4296036.331000] eth0: error -5 reading Rx descriptor. Frame dropped.
[4296045.405000] hermes @ e0aca000: BAP1 offset error: reg=0x4000 id=0x70 offset =0x0
[4296045.405000] eth0: error -5 reading info frame. Frame dropped.
[4296047.494000] hermes @ e0aca000: BAP1 offset error: reg=0x4000 id=0x70 offset =0x0
[4296047.494000] eth0: error -5 reading Rx descriptor. Frame dropped.
[4296062.385000] hermes @ e0aca000: BAP1 offset error: reg=0x4000 id=0x70 offset =0x0
[4296062.385000] eth0: error -5 reading Rx descriptor. Frame dropped.
[4296070.027000] hermes @ e0aca000: BAP1 offset error: reg=0x4000 id=0x70 offset =0x0
[4296070.027000] eth0: error -5 reading Rx descriptor. Frame dropped.
[4296073.511000] hermes @ e0aca000: BAP1 offset error: reg=0x4000 id=0x70 offset =0x0
[4296073.511000] eth0: error -5 reading Rx descriptor. Frame dropped.
[4296076.280000] hermes @ e0aca000: BAP1 offset error: reg=0x4000 id=0x70 offset =0x0
[4296076.280000] eth0: error -5 reading Rx descriptor. Frame dropped.
[4296077.508000] hermes @ e0aca000: BAP1 offset error: reg=0x4000 id=0x70 offset =0x0
[4296077.508000] eth0: error -5 reading Rx descriptor. Frame dropped.
[4296081.636000] hermes @ e0aca000: BAP1 offset error: reg=0x4000 id=0x70 offset =0x0
[4296081.636000] eth0: error -5 reading Rx descriptor. Frame dropped.
[4296105.157000] hermes @ e0aca000: BAP1 offset error: reg=0x4000 id=0x70 offset =0x0
[4296105.157000] eth0: error -5 reading Rx descriptor. Frame dropped.
[4296107.308000] hermes @ e0aca000: BAP1 offset error: reg=0x4000 id=0x70 offset =0x0
[4296107.308000] eth0: error -5 reading Rx descriptor. Frame dropped.
[4296108.970000] hermes @ e0aca000: BAP1 offset error: reg=0x4000 id=0x70 offset =0x0
[4296108.970000] eth0: error -5 reading info frame. Frame dropped.
[4296111.197000] hermes @ e0aca000: BAP1 offset error: reg=0x4000 id=0x70 offset =0x0
[4296111.197000] eth0: error -5 reading Rx descriptor. Frame dropped.
[4296123.592000] hermes @ e0aca000: BAP1 offset error: reg=0x4000 id=0x70 offset =0x0
[4296123.592000] eth0: error -5 reading Rx descriptor. Frame dropped.
[4296126.866000] hermes @ e0aca000: BAP1 offset error: reg=0x4000 id=0x70 offset =0x0
[4296126.866000] eth0: error -5 reading Rx descriptor. Frame dropped.
[4296130.667000] hermes @ e0aca000: BAP1 offset error: reg=0x4000 id=0x70 offset =0x0
[4296130.667000] eth0: error -5 reading Rx descriptor. Frame dropped.
[4296139.574000] hermes @ e0aca000: BAP1 offset error: reg=0x4000 id=0x70 offset =0x0
[4296139.574000] eth0: error -5 reading Rx descriptor. Frame dropped.
[4296142.125000] hermes @ e0aca000: BAP1 offset error: reg=0x4000 id=0x70 offset =0x0
[4296142.125000] eth0: error -5 reading Rx descriptor. Frame dropped.
[4296151.548000] hermes @ e0aca000: BAP1 offset error: reg=0x4000 id=0x70 offset =0x0
[4296151.548000] eth0: error -5 reading Rx descriptor. Frame dropped.
[4296156.264000] hermes @ e0aca000: BAP1 offset error: reg=0x4000 id=0x70 offset =0x0
[4296156.264000] eth0: error -5 reading Rx descriptor. Frame dropped.
[4296163.123000] hermes @ e0aca000: BAP1 offset error: reg=0x4000 id=0x70 offset =0x0
[4296163.123000] eth0: error -5 reading Rx descriptor. Frame dropped.
[4296168.666000] hermes @ e0aca000: BAP1 offset error: reg=0x4000 id=0x70 offset =0x0
[4296168.666000] eth0: error -5 reading Rx descriptor. Frame dropped.
[4296189.351000] hermes @ e0aca000: BAP1 offset error: reg=0x4000 id=0x70 offset =0x0
[4296189.351000] eth0: error -5 reading Rx descriptor. Frame dropped.
[4296246.769000] hermes @ e0aca000: BAP1 offset error: reg=0x4000 id=0x70 offset =0x0
[4296246.769000] eth0: error -5 reading Rx descriptor. Frame dropped.
[4296260.417000] hermes @ e0aca000: BAP1 offset error: reg=0x4000 id=0x70 offset =0x0
[4296260.417000] eth0: error -5 reading Rx descriptor. Frame dropped.
[4296264.926000] hermes @ e0aca000: BAP1 offset error: reg=0x4000 id=0x70 offset =0x0
[4296264.926000] eth0: error -5 reading Rx descriptor. Frame dropped.
[4296274.242000] hermes @ e0aca000: BAP1 offset error: reg=0x4000 id=0x70 offset =0x0
[4296274.242000] eth0: error -5 reading Rx descriptor. Frame dropped.
[4296286.838000] hermes @ e0aca000: BAP1 offset error: reg=0x4000 id=0x70 offset =0x0
[4296286.838000] eth0: error -5 reading Rx descriptor. Frame dropped.
[4296294.589000] hermes @ e0aca000: BAP1 offset error: reg=0x4000 id=0x70 offset =0x0
[4296294.589000] eth0: error -5 reading Rx descriptor. Frame dropped.
[4296295.421000] hermes @ e0aca000: BAP1 offset error: reg=0x4000 id=0x70 offset =0x0
[4296295.421000] eth0: error -5 reading Rx descriptor. Frame dropped.
[4296529.366000] eth0: New link status: AP Changed (0003)
[4296532.204000] hermes @ e0aca000: BAP1 offset error: reg=0x4000 id=0x70 offset =0x0
[4296532.204000] eth0: error -5 reading Rx descriptor. Frame dropped.
[4296534.163000] hermes @ e0aca000: BAP1 offset error: reg=0x4000 id=0x70 offset =0x0
[4296534.163000] eth0: error -5 reading Rx descriptor. Frame dropped.
[4296539.977000] hermes @ e0aca000: BAP1 offset error: reg=0x4000 id=0x70 offset =0x0
[4296539.977000] eth0: error -5 reading info frame. Frame dropped.
[4296546.748000] hermes @ e0aca000: BAP1 offset error: reg=0x4000 id=0x70 offset =0x0
[4296546.748000] eth0: error -5 reading Rx descriptor. Frame dropped.
[4296548.591000] hermes @ e0aca000: BAP1 offset error: reg=0x4000 id=0x70 offset =0x0
[4296548.591000] eth0: error -5 reading Rx descriptor. Frame dropped.
[4296550.948000] hermes @ e0aca000: BAP1 offset error: reg=0x4000 id=0x70 offset =0x0
[4296550.948000] eth0: error -5 reading Rx descriptor. Frame dropped.
[4296559.499000] hermes @ e0aca000: BAP1 offset error: reg=0x4000 id=0x70 offset =0x0
[4296559.499000] eth0: error -5 reading info frame. Frame dropped.
[4296567.026000] hermes @ e0aca000: BAP1 offset error: reg=0x4000 id=0x70 offset =0x0
[4296567.026000] eth0: error -5 reading Rx descriptor. Frame dropped.
[4296568.265000] hermes @ e0aca000: BAP1 offset error: reg=0x4000 id=0x70 offset =0x0
[4296568.265000] eth0: error -5 reading Rx descriptor. Frame dropped.
[4296570.314000] hermes @ e0aca000: BAP1 offset error: reg=0x4000 id=0x70 offset =0x0
[4296570.314000] eth0: error -5 reading Rx descriptor. Frame dropped.
[4296574.535000] hermes @ e0aca000: BAP1 offset error: reg=0x4000 id=0x70 offset =0x0
[4296574.535000] eth0: error -5 reading Rx descriptor. Frame dropped.
[4296575.237000] hermes @ e0aca000: BAP1 offset error: reg=0x4000 id=0x70 offset =0x0
[4296575.237000] eth0: error -5 reading Rx descriptor. Frame dropped.
[4296576.552000] hermes @ e0aca000: BAP1 offset error: reg=0x4000 id=0x70 offset =0x0
[4296576.552000] eth0: error -5 reading Rx descriptor. Frame dropped.
[4296578.504000] hermes @ e0aca000: BAP1 offset error: reg=0x4000 id=0x70 offset =0x0
[4296578.504000] eth0: error -5 reading Rx descriptor. Frame dropped.
[4296590.408000] hermes @ e0aca000: BAP1 offset error: reg=0x4000 id=0x70 offset =0x0
[4296590.408000] eth0: error -5 reading Rx descriptor. Frame dropped.
[4296592.234000] hermes @ e0aca000: BAP1 offset error: reg=0x4000 id=0x70 offset =0x0
[4296592.234000] eth0: error -5 reading Rx descriptor. Frame dropped.
[4296594.370000] hermes @ e0aca000: BAP1 offset error: reg=0x4000 id=0x70 offset =0x0
[4296594.370000] eth0: error -5 reading Rx descriptor. Frame dropped.
[4296598.065000] hermes @ e0aca000: BAP1 offset error: reg=0x4000 id=0x70 offset =0x0
[4296598.065000] eth0: error -5 reading Rx descriptor. Frame dropped.
[4296600.232000] hermes @ e0aca000: BAP1 offset error: reg=0x4000 id=0x70 offset =0x0
[4296600.232000] eth0: error -5 reading Rx descriptor. Frame dropped.
[4296619.359000] hermes @ e0aca000: BAP1 offset error: reg=0x4000 id=0x70 offset =0x0
[4296619.359000] eth0: error -5 reading Rx descriptor. Frame dropped.
[4296642.506000] hermes @ e0aca000: BAP1 offset error: reg=0x4000 id=0x70 offset =0x0
[4296642.506000] eth0: error -5 reading Rx descriptor. Frame dropped.
[4296644.557000] hermes @ e0aca000: BAP1 offset error: reg=0x4000 id=0x70 offset =0x0
[4296644.557000] eth0: error -5 reading Rx descriptor. Frame dropped.
[4296648.763000] hermes @ e0aca000: BAP1 offset error: reg=0x4000 id=0x70 offset =0x0
[4296648.763000] eth0: error -5 reading Rx descriptor. Frame dropped.
[4296655.922000] hermes @ e0aca000: BAP1 offset error: reg=0x4000 id=0x70 offset =0x0
[4296655.922000] eth0: error -5 reading Rx descriptor. Frame dropped.
[4296657.899000] hermes @ e0aca000: BAP1 offset error: reg=0x4000 id=0x70 offset =0x0
[4296657.899000] eth0: error -5 reading Rx descriptor. Frame dropped.
[4296660.636000] hermes @ e0aca000: BAP1 offset error: reg=0x4000 id=0x70 offset =0x0
[4296660.636000] eth0: error -5 reading Rx descriptor. Frame dropped.
[4296671.590000] hermes @ e0aca000: BAP1 offset error: reg=0x4000 id=0x70 offset =0x0
[4296671.590000] eth0: error -5 reading Rx descriptor. Frame dropped.
[4296673.649000] hermes @ e0aca000: BAP1 offset error: reg=0x4000 id=0x70 offset =0x0
[4296673.649000] eth0: error -5 reading Rx descriptor. Frame dropped.
[4296675.220000] hermes @ e0aca000: BAP1 offset error: reg=0x4000 id=0x70 offset =0x0
[4296675.220000] eth0: error -5 reading Rx descriptor. Frame dropped.
[4296681.774000] hermes @ e0aca000: BAP1 offset error: reg=0x4000 id=0x70 offset =0x0
[4296681.774000] eth0: error -5 reading Rx descriptor. Frame dropped.
[4296684.813000] hermes @ e0aca000: BAP1 offset error: reg=0x4000 id=0x70 offset =0x0
[4296684.813000] eth0: error -5 reading Rx descriptor. Frame dropped.
[4296686.555000] hermes @ e0aca000: BAP1 offset error: reg=0x4000 id=0x70 offset =0x0
[4296686.555000] eth0: error -5 reading Rx descriptor. Frame dropped.
[4296689.827000] hermes @ e0aca000: BAP1 offset error: reg=0x4000 id=0x70 offset =0x0
[4296689.827000] eth0: error -5 reading Rx descriptor. Frame dropped.
[4296691.058000] hermes @ e0aca000: BAP1 offset error: reg=0x4000 id=0x70 offset =0x0
[4296691.058000] eth0: error -5 reading Rx descriptor. Frame dropped.
[4296693.204000] hermes @ e0aca000: BAP1 offset error: reg=0x4000 id=0x70 offset =0x0
[4296693.204000] eth0: error -5 reading Rx descriptor. Frame dropped.
[4296697.925000] atkbd.c: Unknown key released (translated set 2, code 0xaa on i sa0060/serio0).
[4296697.925000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4296698.037000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on is a0060/serio0).
[4296698.037000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4296698.099000] atkbd.c: Unknown key released (translated set 2, code 0xaa on i sa0060/serio0).
[4296698.099000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4296698.191000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on is a0060/serio0).
[4296698.191000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4296698.258000] atkbd.c: Unknown key released (translated set 2, code 0xaa on i sa0060/serio0).
[4296698.258000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4296698.365000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on is a0060/serio0).
[4296698.365000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4296698.795000] atkbd.c: Unknown key released (translated set 2, code 0xaa on i sa0060/serio0).
[4296698.795000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4296698.928000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on is a0060/serio0).
[4296698.928000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4296706.412000] hermes @ e0aca000: BAP1 offset error: reg=0x4000 id=0x70 offset =0x0
[4296706.412000] eth0: error -5 reading Rx descriptor. Frame dropped.
[4296708.770000] hermes @ e0aca000: BAP1 offset error: reg=0x4000 id=0x70 offset =0x0
[4296708.770000] eth0: error -5 reading Rx descriptor. Frame dropped.
[4296712.153000] hermes @ e0aca000: BAP1 offset error: reg=0x4000 id=0x70 offset =0x0
[4296712.153000] eth0: error -5 reading Rx descriptor. Frame dropped.
[4296716.355000] hermes @ e0aca000: BAP1 offset error: reg=0x4000 id=0x70 offset =0x0
[4296716.355000] eth0: error -5 reading Rx descriptor. Frame dropped.
[4296718.396000] hermes @ e0aca000: BAP1 offset error: reg=0x4000 id=0x70 offset =0x0
[4296718.396000] eth0: error -5 reading Rx descriptor. Frame dropped.
[4296725.261000] hermes @ e0aca000: BAP1 offset error: reg=0x4000 id=0x70 offset =0x0
[4296725.261000] eth0: error -5 reading Rx descriptor. Frame dropped.
[4296727.304000] hermes @ e0aca000: BAP1 offset error: reg=0x4000 id=0x70 offset =0x0
[4296727.304000] eth0: error -5 reading Rx descriptor. Frame dropped.
[4296756.290000] hermes @ e0aca000: BAP1 offset error: reg=0x4000 id=0x70 offset =0x0
[4296756.290000] eth0: error -5 reading Rx descriptor. Frame dropped.
[4296757.931000] hermes @ e0aca000: BAP1 offset error: reg=0x4000 id=0x70 offset =0x0
[4296757.931000] eth0: error -5 reading Rx descriptor. Frame dropped.
[4296766.839000] hermes @ e0aca000: BAP1 offset error: reg=0x4000 id=0x70 offset =0x0
[4296766.839000] eth0: error -5 reading Rx descriptor. Frame dropped.
[4296767.964000] hermes @ e0aca000: BAP1 offset error: reg=0x4000 id=0x70 offset =0x0
[4296767.964000] eth0: error -5 reading Rx descriptor. Frame dropped.
[4296775.851000] hermes @ e0aca000: BAP1 offset error: reg=0x4000 id=0x70 offset =0x0
[4296775.851000] eth0: error -5 reading Rx descriptor. Frame dropped.
[4296778.308000] hermes @ e0aca000: BAP1 offset error: reg=0x4000 id=0x70 offset =0x0
[4296778.308000] eth0: error -5 reading Rx descriptor. Frame dropped.
[4296793.288000] hermes @ e0aca000: BAP1 offset error: reg=0x4000 id=0x70 offset =0x0
[4296793.288000] eth0: error -5 reading Rx descriptor. Frame dropped.
[4296795.004000] hermes @ e0aca000: BAP1 offset error: reg=0x4000 id=0x70 offset =0x0
[4296795.004000] eth0: error -5 reading Rx descriptor. Frame dropped.
[4296797.282000] hermes @ e0aca000: BAP1 offset error: reg=0x4000 id=0x70 offset =0x0
[4296797.282000] eth0: error -5 reading info frame. Frame dropped.
[4296806.884000] hermes @ e0aca000: BAP1 offset error: reg=0x4000 id=0x70 offset =0x0
[4296806.884000] eth0: error -5 reading Rx descriptor. Frame dropped.
[4296809.265000] hermes @ e0aca000: BAP1 offset error: reg=0x4000 id=0x70 offset =0x0
[4296809.265000] eth0: error -5 reading Rx descriptor. Frame dropped.
[4296840.765000] eth0: New link status: AP Out of Range (0004)
[4296841.254000] eth0: New link status: AP In Range (0005)
[4296851.204000] hermes @ e0aca000: BAP1 offset error: reg=0x4000 id=0x70 offset =0x0
[4296851.204000] eth0: error -5 reading Rx descriptor. Frame dropped.
[4296859.281000] hermes @ e0aca000: BAP1 offset error: reg=0x4000 id=0x70 offset =0x0
[4296859.281000] eth0: error -5 reading Rx descriptor. Frame dropped.
[4296863.876000] hermes @ e0aca000: BAP1 offset error: reg=0x4000 id=0x70 offset =0x0
[4296863.876000] eth0: error -5 reading Rx descriptor. Frame dropped.
[4296867.268000] hermes @ e0aca000: BAP1 offset error: reg=0x4000 id=0x70 offset =0x0
[4296867.268000] eth0: error -5 reading Rx descriptor. Frame dropped.
[4296868.215000] eth0: New link status: AP Out of Range (0004)
[4296868.639000] eth0: New link status: AP In Range (0005)
[4296868.656000] eth0: New link status: AP Changed (0003)
Thanks.  I hope I'm asking all this in the right way, btw.

---

### Post by beerorkid on 2006-02-01
I am not going to be of much help, but I will explain what happened to me.

I have reinstalled after my above post, and the power down issue was not a problem after fixing the things listed below.

I got the linux-image-2.6.12-9-k7 kernel and headers
I also had the double clock speed problem:
[http://ubuntuforums.org/showthread.php?t=75281](http://ubuntuforums.org/showthread.php?t=75281) 

BTW my time was getting hosed because of the double clock problem, it borked my XP as well. (dual boot)

---

### Post by hensonkid on 2006-02-01
Well, I don't know how much this has to do with it, but since I didn't see anything re: ACPI or APM when I did dmesg, I thought it could be something else.  I tried undoing anything I could have done in the last few days to screw it up.

A couple of days ago, I installed a couple of HP printer drivers, including hpoj, which it turns out I don't need.  I removed it, and I was able to shut down.  Also, I noticed that the one of the first items it shut down after the "please wait" screen where it had been stalled was "HP Printing."

I don't know if it was related, and I hate to rely on this as proof that it automagically corrected itself, but I don't know what else it could be.

Thanks for the help.  If it happens again, I think I'll go to the earlier kernel.

---

