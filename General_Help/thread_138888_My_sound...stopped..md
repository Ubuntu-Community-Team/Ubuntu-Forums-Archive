---
title: "My sound...stopped."
date: 2006-03-02
forum: General Help
---

### Post by mztriz on 2006-03-02
I'm not even sure what happened. I've never had any problems with ubuntu and sound on this computer. I just logged out and when I logged back in there was a huge X over my sound and it says it's not configured? :-k

---

### Post by mlind on 2006-03-02
does *dmesg* show any baddness regarding soundsystem initilization?

---

### Post by mztriz on 2006-03-02
Here's what I got ```
[4294670.343000] Checking for popad bug... OK.
[4294670.343000] checking if image is initramfs... it is
[4294670.875000] Freeing initrd memory: 5172k freed
[4294670.876000] ACPI: Looking for DSDT in initrd... not found!
[4294670.943000]  not found!
[4294670.952000] ENABLING IO-APIC IRQs
[4294670.953000] ..TIMER: vector=0x31 pin1=2 pin2=-1
[4294671.064000] NET: Registered protocol family 16
[4294671.064000] EISA bus registered
[4294671.064000] ACPI: bus type pci registered
[4294671.065000] PCI: PCI BIOS revision 2.10 entry at 0xf1990, last bus=1
[4294671.065000] PCI: Using configuration type 1
[4294671.065000] mtrr: v2.0 (20020519)
[4294671.065000] ACPI: Subsystem revision 20050729
[4294671.074000] ACPI: Interpreter enabled
[4294671.074000] ACPI: Using IOAPIC for interrupt routing
[4294671.075000] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 9 10 *11 12)
[4294671.075000] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 9 10 11 12) *0,  disabled.
[4294671.076000] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 9 10 11 12) *0,  disabled.
[4294671.076000] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 9 10 11 12) *0,  disabled.
[4294671.076000] ACPI: PCI Interrupt Link [LNKE] (IRQs *3 4 5 6 7 9 10 11 12)
[4294671.077000] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 *5 6 7 9 10 11 12)
[4294671.077000] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 10 11 12 14 15)  *9
[4294671.077000] ACPI: PCI Root Bridge [PCI0] (0000:00)
[4294671.077000] PCI: Probing PCI hardware (bus 00)
[4294671.077000] ACPI: Assume root bridge [\_SB_.PCI0] segment is 0
[4294671.077000] ACPI: Assume root bridge [\_SB_.PCI0] bus is 0
[4294671.082000] Boot video device is 0000:01:00.0
[4294671.083000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[4294671.084000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCI1._PRT]
[4294671.090000] Linux Plug and Play Support v0.97 (c) Adam Belay
[4294671.090000] pnp: PnP ACPI init
[4294671.095000] pnp: PnP ACPI: found 14 devices
[4294671.095000] PnPBIOS: Disabled by ACPI PNP
[4294671.095000] PCI: Using ACPI for IRQ routing
[4294671.095000] PCI: If a device doesn't work, try "pci=routeirq".  If it helps , post a report
[4294671.100000] pnp: 00:01: ioport range 0xe400-0xe47f could not be reserved
[4294671.100000] pnp: 00:01: ioport range 0xe800-0xe81f has been reserved
[4294671.100000] pnp: 00:0d: ioport range 0x290-0x297 has been reserved
[4294671.100000] pnp: 00:0d: ioport range 0x370-0x375 has been reserved
[4294671.100000] Simple Boot Flag at 0x3a set to 0x1
[4294671.100000] audit: initializing netlink socket (disabled)
[4294671.100000] audit: initialized
[4294671.101000] VFS: Disk quotas dquot_6.5.1
[4294671.101000] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[4294671.101000] devfs: 2004-01-31 Richard Gooch (rgooch@atnf.csiro.au)
[4294671.101000] devfs: boot_options: 0x0
[4294671.101000] Initializing Cryptographic API
[4294671.101000] isapnp: Scanning for PnP cards...
[4294671.454000] isapnp: No Plug & Play device found
[4294671.475000] PNP: No PS/2 controller found. Probing ports directly.
[4294671.480000] serio: i8042 AUX port at 0x60,0x64 irq 12
[4294671.481000] serio: i8042 KBD port at 0x60,0x64 irq 1
[4294671.481000] Serial: 8250/16550 driver $Revision: 1.90 $ 54 ports, IRQ shari ng enabled
[4294671.481000] ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[4294671.483000] ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[4294671.483000] io scheduler noop registered
[4294671.484000] io scheduler anticipatory registered
[4294671.484000] io scheduler deadline registered
[4294671.484000] io scheduler cfq registered
[4294671.484000] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 bl ocksize
[4294671.485000] EISA: Probing bus 0 at eisa.0
[4294671.485000] EISA: Detected 0 cards.
[4294671.485000] NET: Registered protocol family 2
[4294671.495000] IP: routing cache hash table of 2048 buckets, 16Kbytes
[4294671.495000] TCP established hash table entries: 16384 (order: 5, 131072 byt es)
[4294671.495000] TCP bind hash table entries: 16384 (order: 4, 65536 bytes)
[4294671.496000] TCP: Hash tables configured (established 16384 bind 16384)
[4294671.496000] NET: Registered protocol family 8
[4294671.496000] NET: Registered protocol family 20
[4294671.496000] ACPI wakeup devices:
[4294671.496000] PCI0 PCI1 USB0 USB1 USB2 SU20 SLAN
[4294671.496000] ACPI: (supports S0 S1 S4 S5)
[4294671.496000] Freeing unused kernel memory: 224k freed
[4294671.931000] input: AT Translated Set 2 keyboard on isa0060/serio0
[4294671.938000] vga16fb: initializing
[4294671.938000] vga16fb: mapped to 0xc00a0000
[4294672.068000] Console: switching to colour frame buffer device 80x30
[4294672.068000] fb0: VGA16 VGA frame buffer device
[4294673.193000] Capability LSM initialized
[4294673.208000] NET: Registered protocol family 1
[4294673.226000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[4294673.226000] ide: Assuming 33MHz system bus speed for PIO modes; override wi th idebus=xx
[4294673.226000] ACPI: bus type ide registered
[4294673.231000] VP_IDE: IDE controller at PCI slot 0000:00:11.1
[4294673.231000] ACPI: PCI Interrupt 0000:00:11.1[A]: no GSI
[4294673.231000] PCI: Via IRQ fixup for 0000:00:11.1, from 255 to 15
[4294673.231000] VP_IDE: chipset revision 6
[4294673.231000] VP_IDE: not 100% native mode: will probe irqs later
[4294673.231000] VP_IDE: VIA vt8235 (rev 00) IDE UDMA133 controller on pci0000:0 0:11.1
[4294673.231000]     ide0: BM-DMA at 0xb400-0xb407, BIOS settings: hda:DMA, hdb: pio
[4294673.231000]     ide1: BM-DMA at 0xb408-0xb40f, BIOS settings: hdc:DMA, hdd: DMA
[4294673.231000] Probing IDE interface ide0...
[4294673.615000] hda: MAXTOR 6L080J4, ATA DISK drive
[4294674.227000] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[4294674.227000] Probing IDE interface ide1...
[4294675.019000] hdc: IDE128 CDWriter, ATAPI CD/DVD-ROM drive
[4294675.733000] hdd: DM166D DVD-ROM, ATAPI CD/DVD-ROM drive
[4294675.785000] ide1 at 0x170-0x177,0x376 on irq 15
[4294675.785000] Probing IDE interface ide2...
[4294676.298000] Probing IDE interface ide3...
[4294676.810000] Probing IDE interface ide4...
[4294677.322000] Probing IDE interface ide5...
[4294677.838000] hda: max request size: 128KiB
[4294677.854000] hda: 156355584 sectors (80054 MB) w/1819KiB Cache, CHS=65535/16 /63, UDMA(133)
[4294677.855000] hda: cache flushes supported
[4294677.855000]  /dev/ide/host0/bus0/target0/lun0: p1 p2 < p5 >
[4294677.883000] hdc: ATAPI 32X CD-ROM CD-R/RW drive, 2048kB Cache
[4294677.883000] Uniform CD-ROM driver Revision: 3.20
[4294677.887000] hdd: ATAPI 44X DVD-ROM drive, 512kB Cache
[4294678.296000] Attempting manual resume
[4294678.303000] swsusp: Suspend partition has wrong signature?
[4294678.343000] usbcore: registered new driver usbfs
[4294678.343000] usbcore: registered new driver hub
[4294678.344000] USB Universal Host Controller Interface driver v2.2
[4294678.344000] ACPI: PCI Interrupt 0000:00:10.0[A] -> GSI 21 (level, low) -> I RQ 21
[4294678.344000] PCI: Via IRQ fixup for 0000:00:10.0, from 0 to 5
[4294678.344000] uhci_hcd 0000:00:10.0: VIA Technologies, Inc. VT82xxxxx UHCI US B 1.1 Controller
[4294678.406000] uhci_hcd 0000:00:10.0: new USB bus registered, assigned bus num ber 1
[4294678.406000] uhci_hcd 0000:00:10.0: irq 21, io base 0x0000d400
[4294678.406000] hub 1-0:1.0: USB hub found
[4294678.406000] hub 1-0:1.0: 2 ports detected
[4294678.409000] ACPI: PCI Interrupt 0000:00:10.1[B] -> GSI 21 (level, low) -> I RQ 21
[4294678.409000] PCI: Via IRQ fixup for 0000:00:10.1, from 0 to 5
[4294678.409000] uhci_hcd 0000:00:10.1: VIA Technologies, Inc. VT82xxxxx UHCI US B 1.1 Controller (#2)
[4294678.471000] uhci_hcd 0000:00:10.1: new USB bus registered, assigned bus num ber 2
[4294678.471000] uhci_hcd 0000:00:10.1: irq 21, io base 0x0000d000
[4294678.471000] hub 2-0:1.0: USB hub found
[4294678.471000] hub 2-0:1.0: 2 ports detected
[4294678.474000] ACPI: PCI Interrupt 0000:00:10.2[C] -> GSI 21 (level, low) -> I RQ 21
[4294678.474000] PCI: Via IRQ fixup for 0000:00:10.2, from 0 to 5
[4294678.474000] uhci_hcd 0000:00:10.2: VIA Technologies, Inc. VT82xxxxx UHCI US B 1.1 Controller (#3)
[4294678.536000] uhci_hcd 0000:00:10.2: new USB bus registered, assigned bus num ber 3
[4294678.536000] uhci_hcd 0000:00:10.2: irq 21, io base 0x0000b800
[4294678.536000] hub 3-0:1.0: USB hub found
[4294678.536000] hub 3-0:1.0: 2 ports detected
[4294678.569000] ACPI: PCI Interrupt 0000:00:10.3[D] -> GSI 21 (level, low) -> I RQ 21
[4294678.569000] PCI: Via IRQ fixup for 0000:00:10.3, from 0 to 5
[4294678.569000] ehci_hcd 0000:00:10.3: VIA Technologies, Inc. USB 2.0
[4294678.569000] ehci_hcd 0000:00:10.3: new USB bus registered, assigned bus num ber 4
[4294678.569000] ehci_hcd 0000:00:10.3: irq 21, io mem 0xed000000
[4294678.569000] ehci_hcd 0000:00:10.3: USB 2.0 initialized, EHCI 1.00, driver 1 0 Dec 2004
[4294678.569000] hub 4-0:1.0: USB hub found
[4294678.569000] hub 4-0:1.0: 6 ports detected
[4294678.579000] usb 1-1: new low speed USB device using uhci_hcd and address 2
[4294678.631000] via-rhine.c:v1.10-LK1.2.0-2.6 June-10-2004 Written by Donald Be cker
[4294678.631000] ACPI: PCI Interrupt 0000:00:12.0[A] -> GSI 23 (level, low) -> I RQ 23
[4294678.631000] PCI: Via IRQ fixup for 0000:00:12.0, from 0 to 7
[4294678.631000] eth0: VIA Rhine II at 0x1b000, 00:0e:a6:a8:7f:ad, IRQ 23.
[4294678.632000] eth0: MII PHY found at address 1, status 0x786d advertising 01e 1 Link 41e1.
[4294679.637000] usb 1-1: new low speed USB device using uhci_hcd and address 3
[4294680.007000] usb 2-2: new low speed USB device using uhci_hcd and address 2
[4294680.665000] usbcore: registered new driver hiddev
[4294680.719000] input: USB HID v1.10 Keyboard [  USB Keyboard] on usb-0000:00:1 0.0-1
[4294680.799000] input: USB HID v1.10 Device [  USB Keyboard] on usb-0000:00:10. 0-1
[4294680.817000] input: USB HID v1.10 Mouse [Logitech Optical USB Mouse] on usb- 0000:00:10.1-2
[4294680.817000] usbcore: registered new driver usbhid
[4294680.817000] drivers/usb/input/hid-core.c: v2.01:USB HID core driver
[4294681.374000] ACPI: CPU0 (power states: C1[C1])
[4294681.530000] Attempting manual resume
[4294681.531000] swsusp: Suspend partition has wrong signature?
[4294681.541000] EXT3-fs: INFO: recovery required on readonly filesystem.
[4294681.541000] EXT3-fs: write access will be enabled during recovery.
[4294683.518000] kjournald starting.  Commit interval 5 seconds
[4294683.518000] EXT3-fs: recovery complete.
[4294683.522000] EXT3-fs: mounted filesystem with ordered data mode.
[4294684.775000] md: md driver 0.90.1 MAX_MD_DEVS=256, MD_SB_DISKS=27
[4294688.775000] Adding 746980k swap on /dev/hda5.  Priority:-1 extents:1
[4294689.019000] EXT3 FS on hda1, internal journal
[4294695.754000] parport: PnPBIOS parport detected.
[4294695.754000] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE,EPP]
[4294695.844000] lp0: using parport0 (interrupt-driven).
[4294695.895000] mice: PS/2 mouse device common for all mice
[4294696.003000] Linux agpgart interface v0.101 (c) Dave Jones
[4294696.043000] nvidia: module license 'NVIDIA' taints kernel.
[4294696.063000] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 16 (level, low) -> I RQ 16
[4294696.064000] NVRM: loading NVIDIA Linux x86 NVIDIA Kernel Module  1.0-7174 Tue Mar 22 06:44:39 PST 2005
[4294699.443000] device-mapper: 4.4.0-ioctl (2005-01-12) initialised: dm-devel@r edhat.com
[4294700.270000] cdrom: open failed.
[4294700.273000] cdrom: open failed.
[4294702.472000] agpgart: Detected VIA KT400/KT400A/KT600 chipset
[4294702.496000] agpgart: AGP aperture is 64M @ 0xf8000000
[4294702.618000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[4294702.627000] shpchp: acpi_shpchprm:\_SB_.PCI0 evaluate _BBN fail=0x5
[4294702.627000] shpchp: acpi_shpchprm:get_device PCI ROOT HID fail=0x5
[4294703.099000] irda_init()
[4294703.099000] NET: Registered protocol family 23
[4294703.584000] ACPI: PCI Interrupt 0000:00:11.5[C] -> GSI 22 (level, low) -> I RQ 22
[4294703.584000] PCI: Via IRQ fixup for 0000:00:11.5, from 0 to 6
[4294703.586000] PCI: Setting latency timer of device 0000:00:11.5 to 64
[4294704.096000] codec_read: codec 0 is not valid [0x107e5370]
[4294704.102000] codec_read: codec 0 is not valid [0x107e5370]
[4294704.109000] codec_read: codec 0 is not valid [0x107e5370]
[4294704.115000] codec_read: codec 0 is not valid [0x107e5370]
[4294707.110000] Real Time Clock Driver v1.12
[4294707.181000] input: PC Speaker
[4294707.390000] Floppy drive(s): fd0 is 1.44M
[4294707.405000] FDC 0 is a post-1991 82077
[4294708.498000] ts: Compaq touchscreen protocol output
[4294709.170000] eth0: link up, 100Mbps, full-duplex, lpa 0x41E1
[4294709.184000] NET: Registered protocol family 17
[4294714.513000] NET: Registered protocol family 10
[4294714.513000] Disabled Privacy Extensions on device c02eb280(lo)
[4294714.514000] IPv6 over IPv4 tunneling driver
[4294716.086000] ACPI: Power Button (FF) [PWRF]
[4294716.086000] ACPI: Power Button (CM) [PWRB]
[4294716.234000] ibm_acpi: ec object not found
[4294723.427000] agpgart: Found an AGP 3.5 compliant device at 0000:00:00.0.
[4294723.427000] agpgart: Device is in legacy mode, falling back to 2.x
[4294723.427000] agpgart: Putting AGP V2 device at 0000:00:00.0 into 2x mode
[4294723.427000] agpgart: Putting AGP V2 device at 0000:01:00.0 into 2x mode
[4294724.331000] agpgart: Found an AGP 3.5 compliant device at 0000:00:00.0.
[4294724.331000] agpgart: Device is in legacy mode, falling back to 2.x
[4294724.331000] agpgart: Putting AGP V2 device at 0000:00:00.0 into 2x mode
[4294724.331000] agpgart: Putting AGP V2 device at 0000:01:00.0 into 2x mode
[4294724.766000] eth0: no IPv6 routers present
[4294726.980000] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[4294726.980000] apm: overridden by ACPI.
[4294735.545000] Bluetooth: Core ver 2.7
[4294735.545000] NET: Registered protocol family 31
[4294735.545000] Bluetooth: HCI device and connection manager initialized
[4294735.545000] Bluetooth: HCI socket layer initialized
[4294735.566000] Bluetooth: L2CAP ver 2.7
[4294735.566000] Bluetooth: L2CAP socket layer initialized
[4294735.606000] Bluetooth: RFCOMM ver 1.5
[4294735.606000] Bluetooth: RFCOMM socket layer initialized
[4294735.606000] Bluetooth: RFCOMM TTY layer initialized
[4294736.628000] /dev/vmmon[8567]: Module vmmon: registered with major=10 minor= 165
[4294736.628000] /dev/vmmon[8567]: Module vmmon: initialized
[4294737.007000] /dev/vmnet: open called by PID 8601 (vmnet-bridge)
[4294737.007000] /dev/vmnet: hub 0 does not exist, allocating memory.
[4294737.007000] /dev/vmnet: port on hub 0 successfully opened
[4294737.008000] bridge-eth0: enabling the bridge
[4294737.008000] bridge-eth0: up
[4294737.008000] bridge-eth0: already up
[4294737.008000] bridge-eth0: attached
[4294737.048000] /dev/vmnet: open called by PID 8615 (vmnet-natd)
[4294737.048000] /dev/vmnet: hub 8 does not exist, allocating memory.
[4294737.048000] /dev/vmnet: port on hub 8 successfully opened
[4294747.040000] /dev/vmnet: open called by PID 8676 (vmnet-netifup)
[4294747.040000] /dev/vmnet: hub 1 does not exist, allocating memory.
[4294747.040000] /dev/vmnet: port on hub 1 successfully opened
[4294747.044000] /dev/vmnet: open called by PID 8675 (vmnet-netifup)
[4294747.044000] /dev/vmnet: port on hub 8 successfully opened
[4294747.200000] /dev/vmnet: open called by PID 8712 (vmnet-dhcpd)
[4294747.200000] /dev/vmnet: port on hub 1 successfully opened
[4294747.202000] /dev/vmnet: open called by PID 8708 (vmnet-dhcpd)
[4294747.203000] /dev/vmnet: port on hub 8 successfully opened
[4294757.366000] vmnet1: no IPv6 routers present
[4294757.372000] vmnet8: no IPv6 routers present

```

---

### Post by rfruth on 2006-03-02
I just had a similar problem, in users and groups somehow the use audio devices got turned off ...
[ATTACH]6620[/ATTACH]

---

### Post by mztriz on 2006-03-02
[QUOTE=rfruth]I just had a similar problem, in users and groups somehow the use audio devices got turned off ...
[ATTACH]6620[/ATTACH][/QUOTE]
Thanks for the tip. I guess this problem is getting more complicated. I tried to open 'Users and Groups' a few times but it just kept closing it self before it came up; I logged out and back it but it did the same thing. I can't open it.

---

### Post by mlind on 2006-03-02
try running it from terminal
```
gksu users-admin
```

does it give any error (other that "Authentication rejected")?

---

### Post by louis_nichols on 2006-03-03
alternatively, you can just add the user to the audio group, directly from console.

usermod -a audio <user_name>

(I think I remember correctly... I am not under Linux right now.

---

### Post by ingriffiths on 2006-03-03
my sound stopped too...when you get your problem figured out maybe you could help me out...

---

### Post by mztriz on 2006-03-04
[QUOTE=mlind]try running it from terminal
```
gksu users-admin
```

does it give any error (other that "Authentication rejected")?[/QUOTE]

That got it to open, but it doesn't show the User Privileges that I need it to inorder to get my sound back :???:

EDIT: never mind I'm an idiot; I figured it out, but that still doesn't change that my sound doesn't work. I checked everthing in the list and logged out/in. It still says my sound isn't installed and I checked back in users and groups, everything was unchecked again.

---

### Post by mztriz on 2006-03-04
After rechecking and rebooting everything seems to be in order.

Thank you everyone for all of your help :)

---

