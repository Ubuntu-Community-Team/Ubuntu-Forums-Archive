---
title: "xubuntu freezing"
date: 2006-06-23
forum: General Help
---

### Post by Corey4666 on 2006-06-23
hello everyone i had to switch to xubuntu cuz i had very many problems with ubuntu! with it booting up and just in general lots of errors i dunno why but i switched to xubuntu and never had problems till now for some reason my start menu freezes i mean application's menu (sorry used to windows) i got a p4 3.00ghz with 512mb ram btw looking forward to everyones replys :mrgreen:

---

### Post by zxee on 2006-06-24
You can look in /var/log/messages and /var/log/syslog and or do dmesg from a shell.
Also after a freeze, since if it's just affecting your menu, you can open a shell and type dmesg -hopefully one of those methods will reveal something.

---

### Post by Corey4666 on 2006-06-24
where is /var/log/messages and /var/log/syslog? and what is shell? :confused:

---

### Post by Arisna on 2006-06-24
[QUOTE=Corey4666]where is /var/log/messages and /var/log/syslog? and what is shell? :confused:[/QUOTE]

/var/log/messages and /var/log/syslog are full file paths.  You can display them through a shell or open them in a text editor.

To open a shell in XFCE, you would normally find a terminal program in your applications menu.  Since that is freezing on you, try pressing Alt+F2, typing in " xterm " and hitting enter.  This will launch a shell window.

In the shell, you can type " dmesg " to display your kernel ring buffer.  This contains various hardware information.  Do " dmesg > ~/dmesg.txt " to save the log to your home folder.  This will make it easier to copy and paste for us.  You can also do " cat /var/log/messages > ~/messages.txt ", and so on for /var/log/syslog.  Then just fire up your favorite text editor, open the files, and you'll be able to post log messages here.

Note:  Leave off the quotes when entering any of these commands.

---

### Post by Corey4666 on 2006-06-24
i dunno where the folder "Home" is at and also i couldent save the log cuz it wudent let me and i cant copy and paste so im gunna write down the last things it said
in the window

corey4666@corey4666-desktop:~$ dmesg> ~dmesg.txt
corey4666@corey4666-desktop cat/var/log/messages > ~/messages.txt
bash: cat/var/log/messages: no such file or directory

](*,)  i dunno what im doing

EDIT:

ok i got the file using the alt-f2

> [4294667.296000] Linux version 2.6.15-23-386 (buildd@rothera) (gcc version 4.0.3 (Ubuntu 4.0.3-1ubuntu5)) #1 PREEMPT Tue May 23 13:49:40 UTC 2006
[4294667.296000] BIOS-provided physical RAM map:
[4294667.296000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[4294667.296000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[4294667.296000]  BIOS-e820: 00000000000e8000 - 0000000000100000 (reserved)
[4294667.296000]  BIOS-e820: 0000000000100000 - 000000001ffc0000 (usable)
[4294667.296000]  BIOS-e820: 000000001ffc0000 - 000000001ffcf000 (ACPI data)
[4294667.296000]  BIOS-e820: 000000001ffcf000 - 000000001fff0000 (ACPI NVS)
[4294667.296000]  BIOS-e820: 000000001fff0000 - 0000000020000000 (reserved)
[4294667.296000]  BIOS-e820: 00000000ffb80000 - 0000000100000000 (reserved)
[4294667.296000] 0MB HIGHMEM available.
[4294667.296000] 511MB LOWMEM available.
[4294667.296000] found SMP MP-table at 000ff780
[4294667.296000] On node 0 totalpages: 131008
[4294667.296000]   DMA zone: 4096 pages, LIFO batch:0
[4294667.296000]   DMA32 zone: 0 pages, LIFO batch:0
[4294667.296000]   Normal zone: 126912 pages, LIFO batch:31
[4294667.296000]   HighMem zone: 0 pages, LIFO batch:0
[4294667.296000] DMI 2.3 present.
[4294667.296000] ACPI: RSDP (v000 ACPIAM                                ) @ 0x000facb0
[4294667.296000] ACPI: RSDT (v001 A M I  OEMRSDT  0x12000312 MSFT 0x00000097) @ 0x1ffc0000
[4294667.296000] ACPI: FADT (v002 A M I  OEMFACP  0x12000312 MSFT 0x00000097) @ 0x1ffc0200
[4294667.296000] ACPI: MADT (v001 A M I  OEMAPIC  0x12000312 MSFT 0x00000097) @ 0x1ffc0390
[4294667.296000] ACPI: OEMB (v001 A M I  OEMBIOS  0x12000312 MSFT 0x00000097) @ 0x1ffcf040
[4294667.296000] ACPI: DSDT (v001  PSLA1 PSLA1110 0x00000110 INTL 0x02002026) @ 0x00000000
[4294667.296000] ACPI: PM-Timer IO Port: 0x808
[4294667.296000] ACPI: Local APIC address 0xfee00000
[4294667.296000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[4294667.296000] Processor #0 15:2 APIC version 20
[4294667.296000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
[4294667.296000] Processor #1 15:2 APIC version 20
[4294667.296000] WARNING: NR_CPUS limit of 1 reached.  Processor ignored.
[4294667.296000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[4294667.296000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-23
[4294667.296000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[4294667.296000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[4294667.296000] ACPI: IRQ0 used by override.
[4294667.296000] ACPI: IRQ2 used by override.
[4294667.296000] ACPI: IRQ9 used by override.
[4294667.296000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[4294667.296000] Using ACPI (MADT) for SMP configuration information
[4294667.296000] Allocating PCI resources starting at 30000000 (gap: 20000000:dfb80000)
[4294667.296000] Built 1 zonelists
[4294667.296000] Kernel command line: root=/dev/hdd1 ro quiet splash
[4294667.296000] mapped APIC to ffffd000 (fee00000)
[4294667.296000] mapped IOAPIC to ffffc000 (fec00000)
[4294667.296000] Initializing CPU#0
[4294667.296000] PID hash table entries: 2048 (order: 11, 32768 bytes)
[4294667.296000] Detected 3000.121 MHz processor.
[4294667.296000] Using pmtmr for high-res timesource
[4294667.296000] Console: colour VGA+ 80x25
[4294667.708000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[4294667.708000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[4294667.717000] Memory: 508468k/524032k available (1976k kernel code, 15020k reserved, 606k data, 288k init, 0k highmem)
[4294667.717000] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[4294667.777000] Calibrating delay using timer specific routine.. 6003.39 BogoMIPS (lpj=3001697)
[4294667.777000] Security Framework v1.0.0 initialized
[4294667.777000] SELinux:  Disabled at boot.
[4294667.777000] Mount-cache hash table entries: 512
[4294667.777000] CPU: After generic identify, caps: bfebfbff 00000000 00000000 00000000 00004400 00000000 00000000
[4294667.777000] CPU: After vendor identify, caps: bfebfbff 00000000 00000000 00000000 00004400 00000000 00000000
[4294667.777000] CPU: Trace cache: 12K uops, L1 D cache: 8K
[4294667.777000] CPU: L2 cache: 512K
[4294667.777000] CPU: After all inits, caps: bfebfbff 00000000 00000000 00000080 00004400 00000000 00000000
[4294667.777000] mtrr: v2.0 (20020519)
[4294667.777000] CPU: Intel(R) Pentium(R) 4 CPU 3.00GHz stepping 09
[4294667.777000] Enabling fast FPU save and restore... done.
[4294667.777000] Enabling unmasked SIMD FPU exception support... done.
[4294667.777000] Checking 'hlt' instruction... OK.
[4294667.781000] checking if image is initramfs... it is
[4294668.250000] Freeing initrd memory: 6837k freed
[4294668.258000] ACPI: Looking for DSDT ... not found!
[4294668.260000] ENABLING IO-APIC IRQs
[4294668.260000] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[4294668.371000] NET: Registered protocol family 16
[4294668.371000] EISA bus registered
[4294668.371000] ACPI: bus type pci registered
[4294668.371000] PCI: PCI BIOS revision 2.10 entry at 0xf0031, last bus=2
[4294668.371000] PCI: Using configuration type 1
[4294668.371000] ACPI: Subsystem revision 20051216
[4294668.376000] ACPI: Interpreter enabled
[4294668.376000] ACPI: Using IOAPIC for interrupt routing
[4294668.377000] ACPI: PCI Root Bridge [PCI0] (0000:00)
[4294668.377000] PCI: Probing PCI hardware (bus 00)
[4294668.379000] PCI quirk: region 0800-087f claimed by ICH4 ACPI/GPIO/TCO
[4294668.379000] PCI quirk: region 0480-04bf claimed by ICH4 GPIO
[4294668.379000] PCI: Ignoring BAR0-3 of IDE controller 0000:00:1f.1
[4294668.379000] Boot video device is 0000:01:00.0
[4294668.380000] PCI: Transparent bridge - 0000:00:1e.0
[4294668.380000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[4294668.387000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P4._PRT]
[4294668.392000] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 *10 11 12 14 15)
[4294668.393000] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 *10 11 12 14 15)
[4294668.393000] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 *5 6 7 10 11 12 14 15)
[4294668.393000] ACPI: PCI Interrupt Link [LNKD] (IRQs *3 4 5 6 7 10 11 12 14 15)
[4294668.393000] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[4294668.393000] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 *5 6 7 10 11 12 14 15)
[4294668.394000] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[4294668.394000] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 10 *11 12 14 15)
[4294668.394000] Linux Plug and Play Support v0.97 (c) Adam Belay
[4294668.394000] pnp: PnP ACPI init
[4294668.398000] pnp: PnP ACPI: found 11 devices
[4294668.398000] PnPBIOS: Disabled by ACPI PNP
[4294668.398000] PCI: Using ACPI for IRQ routing
[4294668.398000] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[4294668.403000] pnp: 00:07: ioport range 0x680-0x6ff has been reserved
[4294668.403000] PCI: Bridge: 0000:00:01.0
[4294668.403000]   IO window: disabled.
[4294668.403000]   MEM window: fc900000-fe9fffff
[4294668.403000]   PREFETCH window: e7f00000-f7efffff
[4294668.403000] PCI: Bridge: 0000:00:1e.0
[4294668.403000]   IO window: b000-bfff
[4294668.403000]   MEM window: fea00000-feafffff
[4294668.403000]   PREFETCH window: disabled.
[4294668.403000] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[4294668.403000] audit: initializing netlink socket (disabled)
[4294668.403000] audit(1151134268.402:1): initialized
[4294668.403000] VFS: Disk quotas dquot_6.5.1
[4294668.403000] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[4294668.403000] Initializing Cryptographic API
[4294668.403000] io scheduler noop registered
[4294668.403000] io scheduler anticipatory registered
[4294668.403000] io scheduler deadline registered
[4294668.403000] io scheduler cfq registered
[4294673.903000] 0000:00:1d.7 EHCI: BIOS handoff failed (BIOS bug ?) 01010001
[4294673.903000] isapnp: Scanning for PnP cards...
[4294674.260000] isapnp: No Plug & Play device found
[4294674.272000] PNP: No PS/2 controller found. Probing ports directly.
[4294674.275000] serio: i8042 AUX port at 0x60,0x64 irq 12
[4294674.275000] serio: i8042 KBD port at 0x60,0x64 irq 1
[4294674.275000] Serial: 8250/16550 driver $Revision: 1.90 $ 48 ports, IRQ sharing enabled
[4294674.275000] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[4294674.277000] 00:04: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[4294674.277000] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[4294674.277000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[4294674.277000] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[4294674.277000] mice: PS/2 mouse device common for all mice
[4294674.278000] EISA: Probing bus 0 at eisa.0
[4294674.278000] EISA: Detected 0 cards.
[4294674.278000] NET: Registered protocol family 2
[4294674.287000] IP route cache hash table entries: 8192 (order: 3, 32768 bytes)
[4294674.287000] TCP established hash table entries: 32768 (order: 5, 131072 bytes)
[4294674.287000] TCP bind hash table entries: 32768 (order: 5, 131072 bytes)
[4294674.287000] TCP: Hash tables configured (established 32768 bind 32768)
[4294674.287000] TCP reno registered
[4294674.287000] TCP bic registered
[4294674.287000] NET: Registered protocol family 1
[4294674.287000] NET: Registered protocol family 8
[4294674.287000] NET: Registered protocol family 20
[4294674.287000] Using IPI Shortcut mode
[4294674.287000] ACPI wakeup devices: 
[4294674.287000] P0P4 BNIC MC97 USB1 USB2 USB3 USB4 EUSB 
[4294674.287000] ACPI: (supports S0 S1 S3 S4 S5)
[4294674.287000] Freeing unused kernel memory: 288k freed
[4294674.327000] vga16fb: initializing
[4294674.327000] vga16fb: mapped to 0xc00a0000
[4294674.468000] Console: switching to colour frame buffer device 80x25
[4294674.468000] fb0: VGA16 VGA frame buffer device
[4294675.577000] Capability LSM initialized
[4294676.070000] ICH5: IDE controller at PCI slot 0000:00:1f.1
[4294676.070000] PCI: Enabling device 0000:00:1f.1 (0005 -> 0007)
[4294676.070000] ACPI: PCI Interrupt 0000:00:1f.1[A] -> GSI 18 (level, low) -> IRQ 169
[4294676.070000] ICH5: chipset revision 2
[4294676.070000] ICH5: not 100% native mode: will probe irqs later
[4294676.070000]     ide0: BM-DMA at 0xfc00-0xfc07, BIOS settings: hda:DMA, hdb:pio
[4294676.070000]     ide1: BM-DMA at 0xfc08-0xfc0f, BIOS settings: hdc:DMA, hdd:DMA
[4294676.070000] Probing IDE interface ide0...
[4294676.334000] hda: ST3120022A, ATA DISK drive
[4294676.946000] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[4294676.950000] Probing IDE interface ide1...
[4294677.316000] hdc: HP DVD Writer 300c, ATAPI CD/DVD-ROM drive
[4294677.571000] hdd: QUANTUM Bigfoot TX12.0AT, ATA DISK drive
[4294677.622000] ide1 at 0x170-0x177,0x376 on irq 15
[4294677.639000] hda: max request size: 1024KiB
[4294677.649000] hda: 234441648 sectors (120034 MB) w/2048KiB Cache, CHS=16383/255/63, UDMA(100)
[4294677.650000] hda: cache flushes supported
[4294677.650000]  hda: hda1 hda2 < hda5 >
[4294677.670000] hdc: ATAPI 40X DVD-ROM CD-R/RW drive, 2048kB Cache, UDMA(33)
[4294677.670000] Uniform CD-ROM driver Revision: 3.20
[4294677.677000] hdd: max request size: 128KiB
[4294677.677000] hdd: 23547888 sectors (12056 MB) w/69KiB Cache, CHS=23361/16/63, UDMA(33)
[4294677.677000] hdd: cache flushes not supported
[4294677.677000]  hdd: hdd1 hdd2 < hdd5 >
[4294678.141000] SCSI subsystem initialized
[4294678.143000] ACPI: bus type scsi registered
[4294678.143000] libata version 1.20 loaded.
[4294678.144000] ata_piix 0000:00:1f.2: version 1.05
[4294678.144000] ata_pci_init_one: pci_dev class+intf: 0x1018f
[4294678.144000] ata_pci_init_one: NO_LEGACY == 0
[4294678.144000] ACPI: PCI Interrupt 0000:00:1f.2[A] -> GSI 18 (level, low) -> IRQ 169
[4294678.144000] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[4294678.144000] ata1: PATA max UDMA/133 cmd 0xDC00 ctl 0xD802 bmdma 0xCC00 irq 169
[4294678.144000] ata2: PATA max UDMA/133 cmd 0xD400 ctl 0xD002 bmdma 0xCC08 irq 169
[4294679.371000] scsi0 : ata_piix
[4294680.598000] scsi1 : ata_piix
[4294680.634000] usbcore: registered new driver usbfs
[4294680.634000] usbcore: registered new driver hub
[4294680.635000] USB Universal Host Controller Interface driver v2.3
[4294680.636000] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 16 (level, low) -> IRQ 177
[4294680.636000] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[4294680.636000] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[4294680.637000] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[4294680.637000] uhci_hcd 0000:00:1d.0: irq 177, io base 0x0000e000
[4294680.638000] hub 1-0:1.0: USB hub found
[4294680.638000] hub 1-0:1.0: 2 ports detected
[4294680.705000] ieee1394: Initialized config rom entry `ip1394'
[4294680.739000] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 19 (level, low) -> IRQ 185
[4294680.739000] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[4294680.739000] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[4294680.739000] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
[4294680.739000] uhci_hcd 0000:00:1d.1: irq 185, io base 0x0000e400
[4294680.739000] hub 2-0:1.0: USB hub found
[4294680.739000] hub 2-0:1.0: 2 ports detected
[4294680.840000] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 169
[4294680.840000] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[4294680.840000] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[4294680.840000] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
[4294680.840000] uhci_hcd 0000:00:1d.2: irq 169, io base 0x0000e800
[4294680.840000] hub 3-0:1.0: USB hub found
[4294680.840000] hub 3-0:1.0: 2 ports detected
[4294680.941000] ACPI: PCI Interrupt 0000:00:1d.3[A] -> GSI 16 (level, low) -> IRQ 177
[4294680.941000] PCI: Setting latency timer of device 0000:00:1d.3 to 64
[4294680.941000] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[4294680.941000] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 4
[4294680.941000] uhci_hcd 0000:00:1d.3: irq 177, io base 0x0000ec00
[4294680.941000] hub 4-0:1.0: USB hub found
[4294680.941000] hub 4-0:1.0: 2 ports detected
[4294681.044000] ACPI: PCI Interrupt 0000:00:1d.7[D] -> GSI 23 (level, low) -> IRQ 193
[4294681.044000] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[4294681.044000] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[4294681.044000] ehci_hcd 0000:00:1d.7: debug port 1
[4294681.044000] PCI: cache line size of 128 is not supported by device 0000:00:1d.7
[4294681.044000] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 5
[4294681.044000] ehci_hcd 0000:00:1d.7: irq 193, io mem 0xfebffc00
[4294681.046000] usb 2-1: new low speed USB device using uhci_hcd and address 2
[4294681.048000] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[4294681.048000] hub 5-0:1.0: USB hub found
[4294681.048000] hub 5-0:1.0: 8 ports detected
[4294681.149000] ohci1394: $Rev: 1313 $ Ben Collins <bcollins@debian.org>
[4294681.149000] ACPI: PCI Interrupt 0000:02:0e.0[A] -> GSI 21 (level, low) -> IRQ 201
[4294681.200000] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[201]  MMIO=[feaff000-feaff7ff]  Max Packet=[2048]
[4294681.323000] Attempting manual resume
[4294681.398000] EXT3-fs: mounted filesystem with ordered data mode.
[4294681.411000] kjournald starting.  Commit interval 5 seconds
[4294681.982000] usb 2-1: new low speed USB device using uhci_hcd and address 3
[4294682.368000] usb 3-1: new full speed USB device using uhci_hcd and address 2
[4294682.456000] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[00e018000044cd4d]
[4294682.705000] usb 4-2: new low speed USB device using uhci_hcd and address 2
[4294703.121000] Linux agpgart interface v0.101 (c) Dave Jones
[4294703.131000] agpgart: Detected an Intel 865 Chipset.
[4294703.134000] agpgart: AGP aperture is 64M @ 0xf8000000
[4294703.155000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[4294703.276000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[4294703.308000] input: PC Speaker as /class/input/input0
[4294703.414000] hw_random: RNG not detected
[4294703.453000] parport: PnPBIOS parport detected.
[4294703.453000] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
[4294703.477000] Real Time Clock Driver v1.12
[4294703.605000] nvidia: module license 'NVIDIA' taints kernel.
[4294703.608000] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 16 (level, low) -> IRQ 177
[4294703.608000] NVRM: loading NVIDIA Linux x86 Kernel Module  1.0-8762  Mon May 15 13:06:38 PDT 2006
[4294704.189000] usbcore: registered new driver hiddev
[4294704.210000] input: BTC USB Multimedia Cordless Kit   as /class/input/input1
[4294704.210000] input: USB HID v1.00 Keyboard [BTC USB Multimedia Cordless Kit  ] on usb-0000:00:1d.1-1
[4294704.287000] input: BTC USB Multimedia Cordless Kit   as /class/input/input2
[4294704.288000] input,hiddev96: USB HID v1.00 Mouse [BTC USB Multimedia Cordless Kit  ] on usb-0000:00:1d.1-1
[4294704.320000] input: Logitech Logitech Dual Action as /class/input/input3
[4294704.321000] input: USB HID v1.10 Joystick [Logitech Logitech Dual Action] on usb-0000:00:1d.3-2
[4294704.321000] usbcore: registered new driver usbhid
[4294704.321000] drivers/usb/input/hid-core.c: v2.6:USB HID core driver
[4294705.134000] Floppy drive(s): fd0 is 1.44M
[4294705.148000] FDC 0 is a post-1991 82077
[4294705.205000] gameport: EMU10K1 is pci0000:02:0b.1/gameport0, io 0xbc00, speed 1125kHz
[4294705.229000] Initializing USB Mass Storage driver...
[4294705.230000] scsi2 : SCSI emulation for USB Mass Storage devices
[4294705.230000] usb-storage: device found at 2
[4294705.230000] usb-storage: waiting for device to settle before scanning
[4294705.230000] usbcore: registered new driver usb-storage
[4294705.230000] USB Mass Storage support registered.
[4294705.292000] 8139too Fast Ethernet driver 0.9.27
[4294705.292000] ACPI: PCI Interrupt 0000:02:0f.0[A] -> GSI 19 (level, low) -> IRQ 185
[4294705.292000] eth0: RealTek RTL8139 at 0xe0a1c800, 00:0e:a6:00:68:52, IRQ 185
[4294705.292000] eth0:  Identified 8139 chip type 'RTL-8101'
[4294705.314000] 8139cp: 10/100 PCI Ethernet driver v1.2 (Mar 22, 2004)
[4294705.322000] ts: Compaq touchscreen protocol output
[4294705.627000] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[4294705.839000] ACPI: PCI Interrupt 0000:02:0b.0[A] -> GSI 23 (level, low) -> IRQ 193
[4294706.422000] lp0: using parport0 (interrupt-driven).
[4294706.462000] sbp2: $Rev: 1306 $ Ben Collins <bcollins@debian.org>
[4294706.462000] ieee1394: sbp2: Driver forced to serialize I/O (serialize_io=1)
[4294706.462000] ieee1394: sbp2: Try serialize_io=0 for better performance
[4294706.528000] Adding 514040k swap on /dev/hdd5.  Priority:-1 extents:1 across:514040k
[4294706.776000] NET: Registered protocol family 17
[4294706.790000] EXT3 FS on hdd1, internal journal
[4294706.972000] md: md driver 0.90.3 MAX_MD_DEVS=256, MD_SB_DISKS=27
[4294706.972000] md: bitmap version 4.39
[4294707.916000] device-mapper: 4.4.0-ioctl (2005-01-12) initialised: [email]dm-devel@redhat.com[/email]
[4294708.876000] cdrom: open failed.
[4294710.234000]   Vendor: Generic   Model: USB SD Reader     Rev: 1.00
[4294710.234000]   Type:   Direct-Access                      ANSI SCSI revision: 00
[4294710.237000]   Vendor: Generic   Model: USB CF Reader     Rev: 1.01
[4294710.237000]   Type:   Direct-Access                      ANSI SCSI revision: 00
[4294710.240000]   Vendor: Generic   Model: USB SM Reader     Rev: 1.02
[4294710.240000]   Type:   Direct-Access                      ANSI SCSI revision: 00
[4294710.243000]   Vendor: Generic   Model: USB MS Reader     Rev: 1.03
[4294710.243000]   Type:   Direct-Access                      ANSI SCSI revision: 00
[4294710.244000] usb-storage: device scan complete
[4294710.475000] Driver 'sd' needs updating - please use bus_type methods
[4294710.529000] sd 2:0:0:0: Attached scsi removable disk sda
[4294710.583000] sd 2:0:0:1: Attached scsi removable disk sdb
[4294710.648000] sd 2:0:0:2: Attached scsi removable disk sdc
[4294710.701000] sd 2:0:0:3: Attached scsi removable disk sdd
[4294710.723000] NET: Registered protocol family 10
[4294710.724000] lo: Disabled Privacy Extensions
[4294710.724000] IPv6 over IPv4 tunneling driver
[4294710.828000] sd 2:0:0:0: Attached scsi generic sg0 type 0
[4294710.828000] sd 2:0:0:1: Attached scsi generic sg1 type 0
[4294710.829000] sd 2:0:0:2: Attached scsi generic sg2 type 0
[4294710.829000] sd 2:0:0:3: Attached scsi generic sg3 type 0
[4294716.366000] ACPI: Power Button (FF) [PWRF]
[4294716.366000] ACPI: Power Button (CM) [PWRB]
[4294716.472000] ibm_acpi: ec object not found
[4294716.492000] pcc_acpi: loading...
[4294721.266000] eth0: no IPv6 routers present
[4294726.535000] ppdev: user-space parallel port driver
[4294727.510000] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[4294727.511000] apm: overridden by ACPI.
[4294749.292000] input: ImPS/2 Generic Wheel Mouse as /class/input/input4


---

### Post by WADemosthenes on 2006-06-24
[QUOTE=Corey4666]hello everyone i had to switch to xubuntu cuz i had very many problems with ubuntu! with it booting up and just in general lots of errors i dunno why but i switched to xubuntu and never had problems till now for some reason my start menu freezes i mean application's menu (sorry used to windows) i got a p4 3.00ghz with 512mb ram btw looking forward to everyones replys :mrgreen:[/QUOTE]

Errors on 3 ghz and half gig of ram PC that can be fixed by moving to something smaller?  Being a noob myslef, I'd use ubuntu (instead of xubuntu) if my system was large enough, so it would be easier to get generic help from the ubuntu forum, not to mention more user friendly. :D

---

### Post by Corey4666 on 2006-06-24
"PC that can be fixed by moving to something smaller"

u mean my pc isnt fast enough for xubuntu? well i tryed DSL (damn small linux) and it wouldent reconize my mouse and the os is useless if i cant use a mouse
and i tryed gentoo i didnt like it

---

