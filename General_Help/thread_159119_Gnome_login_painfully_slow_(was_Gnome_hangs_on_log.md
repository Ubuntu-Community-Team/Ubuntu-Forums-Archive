---
title: "Gnome login painfully slow (was: Gnome hangs on login)"
date: 2006-04-12
forum: General Help
---

### Post by AaronWyatt on 2006-04-12
Hi all,

I discovered last night that Gnome isn't really locking up...  It's just taking over 10 minutes to show the splash screen, and another 6 to fully log in!  Now, the machine I'm running it on is old and slow (233MHz & 128MB ram with a 512MB swap partition), but it's not *that* slow!  

When I first installed ubuntu, my login time was about 2-3 minutes, with a nearly instantaneous splash screen.  Since then I have: added 2 users to /etc/sudoers, added my machine's IP to /etc/hosts, and updated the system with apt-get update and apt-get upgrade.

Where, specifically, can I look in the logfiles to determine what's going on? The only place I know to look is /var/log/messages, but that file is huge and I don't see anything that stands out as a likely cause.

Please help, and thank you!

Aaron Wyatt

---

### Post by king20878 on 2006-04-12
What is the output of dmesg?
Are you mounting any network filesystems? NFS, SMB, etc

---

### Post by AaronWyatt on 2006-04-12
I'm not mounting any network filesystems.

Where do I find dmesg, and where else should I look?  I'm at work right now so I'm fishing for hints on where to look, and when I get home tonight I'll follow up.

---

### Post by king20878 on 2006-04-12
I would check /var/log/syslog
dmesg should just run from the command line and give you several screens of scrolling text.  Try "dmesg | less" to make it more readable.
Also, I would switch to the terminal during bootup (ALT+CTRL+F7) and watch the messages scroll by.  I'm betting its choking on something and then taking forever to timeout.  See where the bootup gets stalled.

I'm running dapper on a PII and it's quite snappy, so this is definitely not normal.

Good luck tonight.  ;)

---

### Post by AaronWyatt on 2006-04-13
OK, so here are the relevant logfiles.  Hopefully someone here can gleam some kind of idea what's going on from these:

**dmesg**:
```
[4294667.296000] Linux version 2.6.12-9-386 (buildd@rothera) (gcc version 3.4.5 20050809 (prerelease) (Ubuntu 3.4.4-6ubuntu8)) #1 Mon Oct 10 13:14:36 BST 2005
[4294667.296000] BIOS-provided physical RAM map:
[4294667.296000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[4294667.296000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[4294667.296000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[4294667.296000]  BIOS-e820: 0000000000100000 - 0000000007efc000 (usable)
[4294667.296000]  BIOS-e820: 0000000007efc000 - 0000000007eff000 (ACPI data)
[4294667.296000]  BIOS-e820: 0000000007eff000 - 0000000007f00000 (ACPI NVS)
[4294667.296000]  BIOS-e820: 00000000ffff0000 - 0000000100000000 (reserved)
[4294667.296000] 0MB HIGHMEM available.
[4294667.296000] 126MB LOWMEM available.
[4294667.296000] On node 0 totalpages: 32508
[4294667.296000]   DMA zone: 4096 pages, LIFO batch:1
[4294667.296000]   Normal zone: 28412 pages, LIFO batch:15
[4294667.296000]   HighMem zone: 0 pages, LIFO batch:1
[4294667.296000] DMI 2.3 present.
[4294667.296000] ACPI: RSDP (v000 ASUS                                  ) @ 0x000f57a0
[4294667.296000] ACPI: RSDT (v001 ASUS   MEW-AV   0x30303031 MSFT 0x31313031) @ 0x07efc000
[4294667.296000] ACPI: FADT (v001 ASUS   MEW-AV   0x30303031 MSFT 0x31313031) @ 0x07efc080
[4294667.296000] ACPI: BOOT (v001 ASUS   MEW-AV   0x30303031 MSFT 0x31313031) @ 0x07efc040
[4294667.296000] ACPI: DSDT (v001   ASUS MEW-AV   0x00001000 MSFT 0x0100000b) @ 0x00000000
[4294667.296000] ACPI: PM-Timer IO Port: 0xe408
[4294667.296000] Allocating PCI resources starting at 07f00000 (gap: 07f00000:f80f0000)
[4294667.296000] Built 1 zonelists
[4294667.296000] Kernel command line: BOOT_IMAGE=Linux ro root=302
[4294667.296000] Local APIC disabled by BIOS -- you can enable it with "lapic"
[4294667.296000] mapped APIC to ffffd000 (010ff000)
[4294667.296000] Initializing CPU#0
[4294667.296000] PID hash table entries: 512 (order: 9, 8192 bytes)
[4294667.296000] Detected 601.506 MHz processor.
[4294667.296000] Using pmtmr for high-res timesource
[4294667.296000] Console: colour VGA+ 80x25
[4294668.856000] Dentry cache hash table entries: 16384 (order: 4, 65536 bytes)
[4294668.856000] Inode-cache hash table entries: 8192 (order: 3, 32768 bytes)
[4294668.874000] Memory: 120876k/130032k available (1415k kernel code, 8616k reserved, 763k data, 224k init, 0k highmem)
[4294668.874000] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[4294668.874000] Calibrating delay loop... 1191.93 BogoMIPS (lpj=595968)
[4294668.897000] Security Framework v1.0.0 initialized
[4294668.897000] SELinux:  Disabled at boot.
[4294668.897000] Mount-cache hash table entries: 512
[4294668.897000] CPU: After generic identify, caps: 0383f9ff 00000000 00000000 00000000 00000000 00000000 00000000
[4294668.897000] CPU: After vendor identify, caps: 0383f9ff 00000000 00000000 00000000 00000000 00000000 00000000
[4294668.897000] CPU: L1 I cache: 16K, L1 D cache: 16K
[4294668.897000] CPU: L2 cache: 128K
[4294668.897000] CPU: After all inits, caps: 0383f9ff 00000000 00000000 00000040 00000000 00000000 00000000
[4294668.897000] CPU: Intel Celeron (Coppermine) stepping 03
[4294668.897000] Enabling fast FPU save and restore... done.
[4294668.897000] Enabling unmasked SIMD FPU exception support... done.
[4294668.897000] Checking 'hlt' instruction... OK.
[4294668.901000] Checking for popad bug... OK.
[4294668.901000] checking if image is initramfs... it is
[4294670.198000] Freeing initrd memory: 4821k freed
[4294670.201000] ACPI: Looking for DSDT in initrd... not found!
[4294670.410000]  not found!
[4294670.422000] ACPI: setting ELCR to 0200 (from 0a08)
[4294670.424000] NET: Registered protocol family 16
[4294670.424000] EISA bus registered
[4294670.424000] ACPI: bus type pci registered
[4294670.425000] PCI: PCI BIOS revision 2.10 entry at 0xf06a0, last bus=1
[4294670.425000] PCI: Using configuration type 1
[4294670.425000] mtrr: v2.0 (20020519)
[4294670.426000] ACPI: Subsystem revision 20050729
[4294670.440000] ACPI: Interpreter enabled
[4294670.440000] ACPI: Using PIC for interrupt routing
[4294670.442000] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)
[4294670.443000] ACPI: PCI Interrupt Link [LNKB] (IRQs *3 4 5 6 7 9 10 11 12 14 15)
[4294670.444000] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 *9 10 11 12 14 15)
[4294670.445000] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 *9 10 11 12 14 15)
[4294670.446000] ACPI: PCI Root Bridge [PCI0] (0000:00)
[4294670.446000] PCI: Probing PCI hardware (bus 00)
[4294670.446000] ACPI: Assume root bridge [\_SB_.PCI0] segment is 0
[4294670.446000] ACPI: Assume root bridge [\_SB_.PCI0] bus is 0
[4294670.452000] Boot video device is 0000:00:01.0
[4294670.453000] PCI: Transparent bridge - 0000:00:1e.0
[4294670.457000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[4294670.471000] Linux Plug and Play Support v0.97 (c) Adam Belay
[4294670.471000] pnp: PnP ACPI init
[4294670.484000] pnp: PnP ACPI: found 15 devices
[4294670.484000] PnPBIOS: Disabled by ACPI PNP
[4294670.484000] PCI: Using ACPI for IRQ routing
[4294670.484000] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[4294670.491000] pnp: 00:03: ioport range 0xe400-0xe47f could not be reserved
[4294670.491000] pnp: 00:03: ioport range 0xec00-0xec3f has been reserved
[4294670.491000] pnp: 00:03: ioport range 0x290-0x297 has been reserved
[4294670.492000] Simple Boot Flag at 0x3a set to 0x1
[4294670.493000] audit: initializing netlink socket (disabled)
[4294670.493000] audit: initialized
[4294670.494000] VFS: Disk quotas dquot_6.5.1
[4294670.494000] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[4294670.494000] devfs: 2004-01-31 Richard Gooch (rgooch@atnf.csiro.au)
[4294670.494000] devfs: boot_options: 0x0
[4294670.494000] Initializing Cryptographic API
[4294670.495000] isapnp: Scanning for PnP cards...
[4294670.849000] isapnp: No Plug & Play device found
[4294670.955000] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[4294670.957000] serio: i8042 AUX port at 0x60,0x64 irq 12
[4294670.957000] serio: i8042 KBD port at 0x60,0x64 irq 1
[4294670.957000] Serial: 8250/16550 driver $Revision: 1.90 $ 54 ports, IRQ sharing enabled
[4294670.957000] ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[4294670.970000] ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[4294670.971000] io scheduler noop registered
[4294670.971000] io scheduler anticipatory registered
[4294670.971000] io scheduler deadline registered
[4294670.971000] io scheduler cfq registered
[4294670.973000] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[4294670.973000] EISA: Probing bus 0 at eisa.0
[4294670.974000] EISA: Detected 0 cards.
[4294670.974000] NET: Registered protocol family 2
[4294670.983000] IP: routing cache hash table of 512 buckets, 4Kbytes
[4294670.983000] TCP established hash table entries: 4096 (order: 3, 32768 bytes)
[4294670.983000] TCP bind hash table entries: 4096 (order: 2, 16384 bytes)
[4294670.983000] TCP: Hash tables configured (established 4096 bind 4096)
[4294670.984000] NET: Registered protocol family 8
[4294670.984000] NET: Registered protocol family 20
[4294670.984000] ACPI wakeup devices: 
[4294670.984000] UAR1 PS2M USB0 SLOT 
[4294670.984000] ACPI: (supports S0 S1 S3 S4 S5)
[4294670.986000] Freeing unused kernel memory: 224k freed
[4294671.073000] input: AT Translated Set 2 keyboard on isa0060/serio0
[4294671.144000] Capability LSM initialized
[4294671.200000] NET: Registered protocol family 1
[4294671.251000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[4294671.251000] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[4294671.251000] ACPI: bus type ide registered
[4294671.282000] ICH: IDE controller at PCI slot 0000:00:1f.1
[4294671.282000] ICH: chipset revision 2
[4294671.282000] ICH: not 100% native mode: will probe irqs later
[4294671.282000]     ide0: BM-DMA at 0xa800-0xa807, BIOS settings: hda:DMA, hdb:DMA
[4294671.282000]     ide1: BM-DMA at 0xa808-0xa80f, BIOS settings: hdc:DMA, hdd:pio
[4294671.282000] Probing IDE interface ide0...
[4294671.546000] hda: ST315323A, ATA DISK drive
[4294671.801000] hdb: QUANTUM FIREBALLlct20 20, ATA DISK drive
[4294671.852000] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[4294671.853000] Probing IDE interface ide1...
[4294672.525000] hdc: SONY CD-RW CRX140E, ATAPI CD/DVD-ROM drive
[4294673.137000] ide1 at 0x170-0x177,0x376 on irq 15
[4294673.137000] Probing IDE interface ide2...
[4294673.650000] Probing IDE interface ide3...
[4294674.163000] Probing IDE interface ide4...
[4294674.676000] Probing IDE interface ide5...
[4294675.205000] hda: max request size: 128KiB
[4294675.206000] hda: 30008475 sectors (15364 MB) w/512KiB Cache, CHS=29770/16/63, UDMA(66)
[4294675.206000] hda: cache flushes not supported
[4294675.206000]  /dev/ide/host0/bus0/target0/lun0: p1 p2 p3 < p5 p6 >
[4294675.264000] hdb: max request size: 128KiB
[4294675.264000] hdb: 4124736 sectors (2111 MB) w/418KiB Cache, CHS=4092/16/63, UDMA(66)
[4294675.264000] hdb: cache flushes not supported
[4294675.265000]  /dev/ide/host0/bus0/target1/lun0: p1 p2 p3 p4 < >
[4294675.292000] hdc: ATAPI 32X CD-ROM CD-R/RW drive, 4096kB Cache
[4294675.292000] Uniform CD-ROM driver Revision: 3.20
[4294676.824000] Attempting manual resume
[4294676.842000] swsusp: Suspend partition has wrong signature?
[4294677.008000] usbcore: registered new driver usbfs
[4294677.008000] usbcore: registered new driver hub
[4294677.012000] USB Universal Host Controller Interface driver v2.2
[4294677.014000] ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 9
[4294677.014000] PCI: setting IRQ 9 as level-triggered
[4294677.014000] ACPI: PCI Interrupt 0000:00:1f.2[D] -> Link [LNKD] -> GSI 9 (level, low) -> IRQ 9
[4294677.014000] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[4294677.014000] uhci_hcd 0000:00:1f.2: Intel Corporation 82801AA USB
[4294677.076000] uhci_hcd 0000:00:1f.2: new USB bus registered, assigned bus number 1
[4294677.076000] uhci_hcd 0000:00:1f.2: irq 9, io base 0x0000a400
[4294677.077000] hub 1-0:1.0: USB hub found
[4294677.077000] hub 1-0:1.0: 2 ports detected
[4294677.190000] 8139too Fast Ethernet driver 0.9.27
[4294677.192000] ACPI: PCI Interrupt Link [LNKB] enabled at IRQ 3
[4294677.192000] PCI: setting IRQ 3 as level-triggered
[4294677.192000] ACPI: PCI Interrupt 0000:01:09.0[A] -> Link [LNKB] -> GSI 3 (level, low) -> IRQ 3
[4294677.192000] eth0: RealTek RTL8139 at 0xd000, 00:50:ba:af:6a:26, IRQ 3
[4294677.193000] eth0:  Identified 8139 chip type 'RTL-8139C'
[4294677.251000] Linux Tulip driver version 1.1.13 (May 11, 2002)
[4294677.251000] ACPI: PCI Interrupt 0000:01:0b.0[A] -> Link [LNKD] -> GSI 9 (level, low) -> IRQ 9
[4294677.252000] tulip0:  MII transceiver #1 config 3100 status 7849 advertising 05e1.
[4294677.259000] eth1: ADMtek Comet rev 17 at 0001b800, 00:04:E2:92:14:14, IRQ 9.
[4294680.878000] ACPI: CPU0 (power states: C1[C1])
[4294681.195000] device-mapper: 4.4.0-ioctl (2005-01-12) initialised: dm-devel@redhat.com
[4294681.247000] cdrom: open failed.
[4294681.573000] Attempting manual resume
[4294681.592000] swsusp: Suspend partition has wrong signature?
[4294681.649000] kjournald starting.  Commit interval 5 seconds
[4294681.649000] EXT3-fs: mounted filesystem with ordered data mode.
[4294684.402000] md: md driver 0.90.1 MAX_MD_DEVS=256, MD_SB_DISKS=27
[4294692.364000] Adding 497972k swap on /dev/hda5.  Priority:-1 extents:1
[4294692.651000] EXT3 FS on hda2, internal journal
[4294695.962000] parport: PnPBIOS parport detected.
[4294695.962000] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
[4294696.068000] lp0: using parport0 (interrupt-driven).
[4294696.298000] mice: PS/2 mouse device common for all mice
[4294696.453000] ieee1394: Initialized config rom entry `ip1394'
[4294696.540000] SCSI subsystem initialized
[4294696.566000] logips2pp: Detected unknown logitech mouse model 86
[4294696.594000] sbp2: $Rev: 1219 $ Ben Collins <bcollins@debian.org>
[4294696.647000] input: ImExPS/2 Logitech Explorer Mouse on isa0060/serio1
[4294697.686000] ts: Compaq touchscreen protocol output
[4294702.394000] cdrom: open failed.
[4294703.935000] kjournald starting.  Commit interval 5 seconds
[4294703.936000] EXT3 FS on hda6, internal journal
[4294703.936000] EXT3-fs: mounted filesystem with ordered data mode.
[4294706.498000] Linux agpgart interface v0.101 (c) Dave Jones
[4294706.756000] agpgart: Detected an Intel i810 Chipset.
[4294706.777000] agpgart: AGP aperture is 64M @ 0xe4000000
[4294707.222000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[4294707.379000] shpchp: acpi_shpchprm:\_SB_.PCI0 evaluate _BBN fail=0x5
[4294707.379000] shpchp: acpi_shpchprm:get_device PCI ROOT HID fail=0x5
[4294707.675000] hw_random hardware driver 1.0.0 loaded
[4294710.326000] ACPI: PCI Interrupt 0000:00:1f.5[B] -> Link [LNKB] -> GSI 3 (level, low) -> IRQ 3
[4294710.326000] PCI: Setting latency timer of device 0000:00:1f.5 to 64
[4294710.646000] intel8x0_measure_ac97_clock: measured 49522 usecs
[4294710.646000] intel8x0: clocking to 48000
[4294712.696000] ohci1394: $Rev: 1250 $ Ben Collins <bcollins@debian.org>
[4294712.697000] ACPI: PCI Interrupt Link [LNKC] enabled at IRQ 9
[4294712.697000] ACPI: PCI Interrupt 0000:01:0a.0[A] -> Link [LNKC] -> GSI 9 (level, low) -> IRQ 9
[4294712.770000] ohci1394: fw-host0: OHCI-1394 1.0 (PCI): IRQ=[9]  MMIO=[e1800000-e18007ff]  Max Packet=[2048]
[4294714.040000] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[08004603004c8f3f]
[4294715.142000] Real Time Clock Driver v1.12
[4294715.521000] input: PC Speaker
[4294715.853000] Floppy drive(s): fd0 is 1.44M
[4294715.907000] FDC 0 is a post-1991 82077
[4294719.396000] eth0: link up, 100Mbps, full-duplex, lpa 0x41E1
[4294723.106000] NET: Registered protocol family 10
[4294723.106000] Disabled Privacy Extensions on device c02eb280(lo)
[4294723.107000] IPv6 over IPv4 tunneling driver
[4294725.494000] ACPI: Power Button (FF) [PWRF]
[4294725.494000] ACPI: Power Button (CM) [PWRB]
[4294725.952000] ibm_acpi: ec object not found
[4294733.162000] eth0: no IPv6 routers present
[4294738.424000] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[4294738.424000] apm: overridden by ACPI.
[4294742.101000] Bluetooth: Core ver 2.7
[4294742.101000] NET: Registered protocol family 31
[4294742.101000] Bluetooth: HCI device and connection manager initialized
[4294742.101000] Bluetooth: HCI socket layer initialized
[4294742.214000] Bluetooth: L2CAP ver 2.7
[4294742.214000] Bluetooth: L2CAP socket layer initialized
[4294742.284000] Bluetooth: RFCOMM ver 1.5
[4294742.284000] Bluetooth: RFCOMM socket layer initialized
[4294742.284000] Bluetooth: RFCOMM TTY layer initialized

```

**syslog**
```
Apr 13 06:56:24 localhost syslogd 1.4.1#17ubuntu3: restart.
Apr 13 06:56:24 localhost anacron[7257]: Job `cron.daily' terminated (mailing output)
Apr 13 06:56:24 localhost anacron[7257]: Can't find sendmail at /usr/sbin/sendmail, not mailing output
Apr 13 06:56:24 localhost anacron[7257]: Normal exit (1 job run)
Apr 13 06:59:14 localhost gconfd (wyatt-7428): Resolved address "xml:readwrite:/home/wyatt/.gconf" to a writable configuration source at position 0
Apr 13 07:08:45 localhost gconfd (root-7737): starting (version 2.12.0), pid 7737 user 'root'
Apr 13 07:08:45 localhost gconfd (root-7737): Resolved address "xml:readonly:/etc/gconf/gconf.xml.mandatory" to a read-only configuration source at position 0
Apr 13 07:08:45 localhost gconfd (root-7737): Resolved address "xml:readonly:/usr/share/gconf/local.mandatory" to a read-only configuration source at position 1
Apr 13 07:08:45 localhost gconfd (root-7737): Resolved address "xml:readwrite:/root/.gconf" to a writable configuration source at position 2
Apr 13 07:08:45 localhost gconfd (root-7737): Resolved address "xml:readonly:/etc/gconf/gconf.xml.defaults" to a read-only configuration source at position 3
Apr 13 07:08:45 localhost gconfd (root-7737): Resolved address "xml:readonly:/usr/share/gconf/local.defaults" to a read-only configuration source at position 4
Apr 13 07:08:45 localhost gconfd (root-7737): Resolved address "xml:readonly:/usr/share/gconf/cdd.defaults" to a read-only configuration source at position 5
Apr 13 07:08:45 localhost gconfd (root-7737): Resolved address "xml:readonly:/usr/share/gconf/debian.defaults" to a read-only configuration source at position 6
Apr 13 07:08:45 localhost gconfd (root-7737): Resolved address "xml:readonly:/var/lib/gconf/defaults" to a read-only configuration source at position 7

```

**user.log**:

```
Apr 13 06:50:05 localhost hp: unable to open /var/run/hplip/hpiod.port: No such file or directory: prnt/hpijs/hplip_api.c 75 
Apr 13 06:50:05 localhost hpiod: unable to bind socket 0: Cannot assign requested address 
Apr 13 06:50:09 localhost python: hpssd [ERROR] Server exited with error: Unable to bind to socket
Apr 13 06:52:40 localhost gconfd (wyatt-7428): starting (version 2.12.0), pid 7428 user 'wyatt'
Apr 13 06:52:40 localhost gconfd (wyatt-7428): Resolved address "xml:readonly:/etc/gconf/gconf.xml.mandatory" to a read-only configuration source at position 0
Apr 13 06:52:40 localhost gconfd (wyatt-7428): Resolved address "xml:readonly:/usr/share/gconf/local.mandatory" to a read-only configuration source at position 1
Apr 13 06:52:40 localhost gconfd (wyatt-7428): Resolved address "xml:readwrite:/home/wyatt/.gconf" to a writable configuration source at position 2
Apr 13 06:52:40 localhost gconfd (wyatt-7428): Resolved address "xml:readonly:/etc/gconf/gconf.xml.defaults" to a read-only configuration source at position 3
Apr 13 06:52:40 localhost gconfd (wyatt-7428): Resolved address "xml:readonly:/usr/share/gconf/local.defaults" to a read-only configuration source at position 4
Apr 13 06:52:40 localhost gconfd (wyatt-7428): Resolved address "xml:readonly:/usr/share/gconf/cdd.defaults" to a read-only configuration source at position 5
Apr 13 06:52:40 localhost gconfd (wyatt-7428): Resolved address "xml:readonly:/usr/share/gconf/debian.defaults" to a read-only configuration source at position 6
Apr 13 06:52:40 localhost gconfd (wyatt-7428): Resolved address "xml:readonly:/var/lib/gconf/defaults" to a read-only configuration source at position 7
Apr 13 06:55:25 localhost hp: unable to open /var/run/hplip/hpiod.port: No such file or directory: prnt/hpijs/hplip_api.c 75 
Apr 13 06:59:14 localhost gconfd (wyatt-7428): Resolved address "xml:readwrite:/home/wyatt/.gconf" to a writable configuration source at position 0
Apr 13 07:08:45 localhost gconfd (root-7737): starting (version 2.12.0), pid 7737 user 'root'
Apr 13 07:08:45 localhost gconfd (root-7737): Resolved address "xml:readonly:/etc/gconf/gconf.xml.mandatory" to a read-only configuration source at position 0
Apr 13 07:08:45 localhost gconfd (root-7737): Resolved address "xml:readonly:/usr/share/gconf/local.mandatory" to a read-only configuration source at position 1
Apr 13 07:08:45 localhost gconfd (root-7737): Resolved address "xml:readwrite:/root/.gconf" to a writable configuration source at position 2
Apr 13 07:08:45 localhost gconfd (root-7737): Resolved address "xml:readonly:/etc/gconf/gconf.xml.defaults" to a read-only configuration source at position 3
Apr 13 07:08:45 localhost gconfd (root-7737): Resolved address "xml:readonly:/usr/share/gconf/local.defaults" to a read-only configuration source at position 4
Apr 13 07:08:45 localhost gconfd (root-7737): Resolved address "xml:readonly:/usr/share/gconf/cdd.defaults" to a read-only configuration source at position 5
Apr 13 07:08:45 localhost gconfd (root-7737): Resolved address "xml:readonly:/usr/share/gconf/debian.defaults" to a read-only configuration source at position 6
Apr 13 07:08:45 localhost gconfd (root-7737): Resolved address "xml:readonly:/var/lib/gconf/defaults" to a read-only configuration source at position 7

```

---

### Post by AaronWyatt on 2006-04-13
Could this have something to do with it?

from **user.log**:
```
Apr 13 06:50:05 localhost hp: unable to open /var/run/hplip/hpiod.port: No such file or directory: prnt/hpijs/hplip_api.c 75 
Apr 13 06:50:05 localhost hpiod: unable to bind socket 0: Cannot assign requested address 
Apr 13 06:50:09 localhost python: hpssd [ERROR] Server exited with error: Unable to bind to socket
```

---

### Post by AaronWyatt on 2006-04-13
A google search suggests that /var/run/hplip/hpiod.port is related to an hp printing device, and also that it happens as part of init.d.  Please correct me if I'm wrong, but doesn't that mean it happens before logging in, and therefore is unrelated?  (I don't have any printers set up at all on my machine.  Should I bother disabling this script?)

I don't see anything else that suggests (to my novice eyes) a cause for the delay on gnome login.  Any insight into these logfiles or the problem in general, or at least some more ideas where to look to identify a possible cause, would be greatly appreciated.

Thanks in advance for your helpful replies.

---

### Post by AaronWyatt on 2006-04-13
Update: Google found a very similar issue at [http://lists.debian.org/debian-powerpc/2003/05/msg00196.html](http://lists.debian.org/debian-powerpc/2003/05/msg00196.html).

> On Mon, 2003-05-12 at 18:43, Joss Winn wrote: 
> Thanks.  As it happens, the problem was with the package 'dhcp3-client'
> and not with either KDE or Gnome.  On the day I got ADSL, I started
> using dhcp with a router, I downloaded a lot of packages including
> dhclient and then the unbearably slow logins began.  
> 
> After uninstalling a lot of KDE and Gnome I found that
> login was hanging for several minutes with other window managers and
> also found that typing into search fields like google or
> user/password fields for web mail, also caused the browser to hang.   
> 
> I don't understand why it was doing this, but uninstalling dhcp3-client
> and switching to 'pump' has fixed it.
> 
> anyone got an explanation for this?

Likely something like a bogus nameserver entry causing DNS timeouts.


I realize this is from 3 years ago, but so far it's all I have to go on.  Would someone please explain to me how to find out if this is what's happening to my system, and if so how I might fix it?

Thanks.

---

### Post by RafRaf on 2006-04-29
I have the exact same problem on my HP nc6000.

---

### Post by kleiba on 2006-08-24
I had the same problem and found out it was because my loopback device was not setup correctly (although everything used to work fine before, and I can't remember having disabled it intentionally...)

Anyway, in the end, all I had to do was:

```
sudo ifconfig lo 127.0.0.1
```
and everything would go smoothly next time I booted.

Hope that helps.

---

