---
title: "sound dapper don't work well"
date: 2006-04-26
forum: General Help
---

### Post by alerce on 2006-04-26
hi, i got a big problem because the sound sometimes ( only in the beginning of system ) works. But in a little time (like 30seconds) the sound turn off... i don't know why because i don't have any message in anywhere... :-(

thanks for any clue .. please.. i attach some info if you could need more just ask me

my distro : ubuntu dapper lst 6
kernel      : 2.6.15-21-386
alsamixer told i have a : **HDA Intel card**.

my dmesg

alerce@cucao:~#** dmesg**
[4294667.296000] Linux version 2.6.15-21-386 (buildd@rothera) (gcc version 4.0.3 (Ubuntu 4.0.3-1ubuntu5)) #1 PREEMPT Fri Apr 21 16:43:33 UTC 2006
[4294667.296000] BIOS-provided physical RAM map:
[4294667.296000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[4294667.296000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[4294667.296000]  BIOS-e820: 00000000000e4000 - 0000000000100000 (reserved)
[4294667.296000]  BIOS-e820: 0000000000100000 - 000000001ffb0000 (usable)
[4294667.296000]  BIOS-e820: 000000001ffb0000 - 000000001ffbe000 (ACPI data)
[4294667.296000]  BIOS-e820: 000000001ffbe000 - 000000001fff0000 (ACPI NVS)
[4294667.296000]  BIOS-e820: 000000001fff0000 - 0000000020000000 (reserved)
[4294667.296000]  BIOS-e820: 00000000ffb80000 - 0000000100000000 (reserved)
[4294667.296000] 0MB HIGHMEM available.
[4294667.296000] 511MB LOWMEM available.
[4294667.296000] found SMP MP-table at 000ff780
[4294667.296000] On node 0 totalpages: 130992
[4294667.296000]   DMA zone: 4096 pages, LIFO batch:0
[4294667.296000]   DMA32 zone: 0 pages, LIFO batch:0
[4294667.296000]   Normal zone: 126896 pages, LIFO batch:31
[4294667.296000]   HighMem zone: 0 pages, LIFO batch:0
[4294667.296000] DMI 2.3 present.
[4294667.296000] ACPI: RSDP (v000 ACPIAM                                ) @ 0x000fb120
[4294667.296000] ACPI: RSDT (v001 A M I  OEMRSDT  0x01000603 MSFT 0x00000097) @ 0x1ffb0000
[4294667.296000] ACPI: FADT (v001 A M I  OEMFACP  0x01000603 MSFT 0x00000097) @ 0x1ffb0200
[4294667.296000] ACPI: MADT (v001 A M I  OEMAPIC  0x01000603 MSFT 0x00000097) @ 0x1ffb0390
[4294667.296000] ACPI: OEMB (v001 A M I  AMI_OEM  0x01000603 MSFT 0x00000097) @ 0x1ffbe040
[4294667.296000] ACPI: MCFG (v001 A M I  OEMMCFG  0x01000603 MSFT 0x00000097) @ 0x1ffb6c90
[4294667.296000] ACPI: DSDT (v001  A0318 A0318001 0x00000001 INTL 0x02002026) @ 0x00000000
[4294667.296000] ACPI: PM-Timer IO Port: 0x808
[4294667.296000] ACPI: Local APIC address 0xfee00000
[4294667.296000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[4294667.296000] Processor #0 15:4 APIC version 20
[4294667.296000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x81] disabled)
[4294667.296000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
[4294667.296000] IOAPIC[0]: apic_id 1, version 32, address 0xfec00000, GSI 0-23
[4294667.296000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[4294667.296000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[4294667.296000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[4294667.296000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[4294667.296000] ACPI: IRQ0 used by override.
[4294667.296000] ACPI: IRQ2 used by override.
[4294667.296000] ACPI: IRQ9 used by override.
[4294667.296000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[4294667.296000] Using ACPI (MADT) for SMP configuration information
[4294667.296000] Allocating PCI resources starting at 30000000 (gap: 20000000:dfb80000)
[4294667.296000] Built 1 zonelists
[4294667.296000] Kernel command line: root=/dev/sda2 ro quiet splash
[4294667.296000] mapped APIC to ffffd000 (fee00000)
[4294667.296000] mapped IOAPIC to ffffc000 (fec00000)
[4294667.296000] Initializing CPU#0
[4294667.296000] PID hash table entries: 2048 (order: 11, 32768 bytes)
[4294667.296000] Detected 2810.700 MHz processor.
[4294667.296000] Using pmtmr for high-res timesource
[4294667.296000] Console: colour VGA+ 80x25
[4294670.397000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[4294670.398000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[4294670.407000] Memory: 508852k/523968k available (1974k kernel code, 14576k reserved, 604k data, 288k init, 0k highmem)
[4294670.407000] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[4294670.467000] Calibrating delay using timer specific routine.. 5624.40 BogoMIPS (lpj=2812204)
[4294670.467000] Security Framework v1.0.0 initialized
[4294670.467000] SELinux:  Disabled at boot.
[4294670.467000] Mount-cache hash table entries: 512
[4294670.467000] CPU: After generic identify, caps: bfebfbff 20000000 00000000 00000000 0000651d 00000000 00000001
[4294670.467000] CPU: After vendor identify, caps: bfebfbff 20000000 00000000 00000000 0000651d 00000000 00000001
[4294670.467000] monitor/mwait feature present.
[4294670.467000] using mwait in idle threads.
[4294670.467000] CPU: Trace cache: 12K uops, L1 D cache: 16K
[4294670.467000] CPU: L2 cache: 1024K
[4294670.467000] CPU: After all inits, caps: bfebfbff 20000000 00000000 00000080 0000651d 00000000 00000001
[4294670.467000] mtrr: v2.0 (20020519)
[4294670.467000] CPU: Intel(R) Pentium(R) 4 CPU 2.80GHz stepping 09
[4294670.467000] Enabling fast FPU save and restore... done.
[4294670.467000] Enabling unmasked SIMD FPU exception support... done.
[4294670.467000] Checking 'hlt' instruction... OK.
[4294670.471000] checking if image is initramfs... it is
[4294670.997000] Freeing initrd memory: 6395k freed
[4294671.003000] ACPI: Looking for DSDT ... not found!
[4294671.006000] ENABLING IO-APIC IRQs
[4294671.007000] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[4294671.118000] NET: Registered protocol family 16
[4294671.118000] EISA bus registered
[4294671.118000] ACPI: bus type pci registered
[4294671.118000] PCI: PCI BIOS revision 2.10 entry at 0xf0031, last bus=3
[4294671.118000] PCI: Using MMCONFIG
[4294671.118000] ACPI: Subsystem revision 20051216
[4294671.127000] ACPI: Interpreter enabled
[4294671.127000] ACPI: Using IOAPIC for interrupt routing
[4294671.127000] ACPI: PCI Root Bridge [PCI0] (0000:00)
[4294671.127000] PCI: Probing PCI hardware (bus 00)
[4294671.130000] PCI: Ignoring BAR0-3 of IDE controller 0000:00:1f.1
[4294671.130000] Boot video device is 0000:03:00.0
[4294671.131000] PCI: Transparent bridge - 0000:00:1e.0
[4294671.131000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[4294671.133000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P1._PRT]
[4294671.133000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P3._PRT]
[4294671.134000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P4._PRT]
[4294671.141000] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 *10 11 12 14 15)
[4294671.141000] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[4294671.142000] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 10 *11 12 14 15)
[4294671.142000] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 *5 6 7 10 11 12 14 15)
[4294671.142000] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[4294671.142000] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 *10 11 12 14 15)
[4294671.143000] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[4294671.143000] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 *4 5 6 7 10 11 12 14 15)
[4294671.143000] Linux Plug and Play Support v0.97 (c) Adam Belay
[4294671.143000] pnp: PnP ACPI init
[4294671.150000] pnp: PnP ACPI: found 17 devices
[4294671.150000] PnPBIOS: Disabled by ACPI PNP
[4294671.150000] PCI: Using ACPI for IRQ routing
[4294671.150000] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[4294671.163000] pnp: 00:07: ioport range 0x290-0x297 has been reserved
[4294671.163000] PCI: Bridge: 0000:00:01.0
[4294671.163000]   IO window: e000-efff
[4294671.163000]   MEM window: cdf00000-cfffffff
[4294671.163000]   PREFETCH window: d0000000-dfffffff
[4294671.163000] PCI: Bridge: 0000:00:1c.0
[4294671.164000]   IO window: d000-dfff
[4294671.164000]   MEM window: disabled.
[4294671.164000]   PREFETCH window: disabled.
[4294671.164000] PCI: Bridge: 0000:00:1e.0
[4294671.164000]   IO window: c000-cfff
[4294671.164000]   MEM window: cde00000-cdefffff
[4294671.164000]   PREFETCH window: 30000000-300fffff
[4294671.164000] ACPI: PCI Interrupt 0000:00:01.0[A] -> GSI 16 (level, low) -> IRQ 169
[4294671.164000] PCI: Setting latency timer of device 0000:00:01.0 to 64
[4294671.164000] ACPI: PCI Interrupt 0000:00:1c.0[A] -> GSI 16 (level, low) -> IRQ 169
[4294671.164000] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[4294671.164000] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[4294671.164000] audit: initializing netlink socket (disabled)
[4294671.164000] audit(1146038523.163:1): initialized
[4294671.164000] VFS: Disk quotas dquot_6.5.1
[4294671.164000] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[4294671.164000] Initializing Cryptographic API
[4294671.164000] io scheduler noop registered
[4294671.164000] io scheduler anticipatory registered
[4294671.164000] io scheduler deadline registered
[4294671.164000] io scheduler cfq registered
[4294671.164000] ACPI: PCI Interrupt 0000:00:01.0[A] -> GSI 16 (level, low) -> IRQ 169
[4294671.164000] PCI: Setting latency timer of device 0000:00:01.0 to 64
[4294671.164000] assign_interrupt_mode Found MSI capability
[4294671.164000] Allocate Port Service[pcie00]
[4294671.165000] Allocate Port Service[pcie03]
[4294671.165000] ACPI: PCI Interrupt 0000:00:1c.0[A] -> GSI 16 (level, low) -> IRQ 169
[4294671.165000] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[4294671.165000] assign_interrupt_mode Found MSI capability
[4294671.165000] Allocate Port Service[pcie00]
[4294671.165000] Allocate Port Service[pcie02]
[4294671.165000] Allocate Port Service[pcie03]
[4294671.165000] isapnp: Scanning for PnP cards...
[4294671.520000] isapnp: No Plug & Play device found
[4294671.538000] PNP: PS/2 Controller [PNP0303:PS2K] at 0x60,0x64 irq 1
[4294671.538000] PNP: PS/2 controller doesn't have AUX irq; using default 12
[4294671.540000] serio: i8042 AUX port at 0x60,0x64 irq 12
[4294671.540000] serio: i8042 KBD port at 0x60,0x64 irq 1
[4294671.540000] Serial: 8250/16550 driver $Revision: 1.90 $ 48 ports, IRQ sharing enabled
[4294671.540000] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[4294671.543000] 00:0d: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[4294671.543000] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[4294671.543000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[4294671.543000] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[4294671.543000] mice: PS/2 mouse device common for all mice
[4294671.544000] EISA: Probing bus 0 at eisa.0
[4294671.544000] EISA: Detected 0 cards.
[4294671.544000] NET: Registered protocol family 2
[4294671.554000] IP route cache hash table entries: 8192 (order: 3, 32768 bytes)
[4294671.554000] TCP established hash table entries: 32768 (order: 5, 131072 bytes)
[4294671.554000] TCP bind hash table entries: 32768 (order: 5, 131072 bytes)
[4294671.554000] TCP: Hash tables configured (established 32768 bind 32768)
[4294671.554000] TCP reno registered
[4294671.554000] TCP bic registered
[4294671.554000] NET: Registered protocol family 1
[4294671.554000] NET: Registered protocol family 8
[4294671.554000] NET: Registered protocol family 20
[4294671.554000] Using IPI Shortcut mode
[4294671.554000] ACPI wakeup devices:
[4294671.554000] P0P1 P0P3 P0P4 P0P5 P0P6 P0P7 PS2K UAR1 USB1 USB2 USB3 USB4 EUSB MC97
[4294671.554000] ACPI: (supports S0 S1 S3 S4 S5)
[4294671.554000] Freeing unused kernel memory: 288k freed
[4294671.584000] input: AT Translated Set 2 keyboard as /class/input/input0
[4294671.611000] vga16fb: initializing
[4294671.611000] vga16fb: mapped to 0xc00a0000
[4294671.822000] Console: switching to colour frame buffer device 80x25
[4294671.822000] fb0: VGA16 VGA frame buffer device
[4294673.033000] Capability LSM initialized
[4294673.063000] ACPI: Processor [CPU1] (supports 8 throttling states)
[4294673.540000] ICH6: IDE controller at PCI slot 0000:00:1f.1
[4294673.540000] ACPI: PCI Interrupt 0000:00:1f.1[A] -> GSI 18 (level, low) -> IRQ 201
[4294673.540000] ICH6: chipset revision 5
[4294673.540000] ICH6: not 100% native mode: will probe irqs later
[4294673.540000]     ide0: BM-DMA at 0xffa0-0xffa7, BIOS settings: hda:DMA, hdb:pio
[4294673.540000]     ide1: BM-DMA at 0xffa8-0xffaf, BIOS settings: hdc:pio, hdd:pio
[4294673.540000] Probing IDE interface ide0...
[4294674.212000] hda: _NEC DVD_RW ND-3550A, ATAPI CD/DVD-ROM drive
[4294674.824000] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[4294674.825000] Probing IDE interface ide1...
[4294675.351000] hda: ATAPI 48X DVD-ROM DVD-R CD-R/RW drive, 2048kB Cache, UDMA(33)
[4294675.351000] Uniform CD-ROM driver Revision: 3.20
[4294675.396000] SCSI subsystem initialized
[4294675.397000] libata version 1.20 loaded.
[4294675.398000] ata_piix 0000:00:1f.2: version 1.05
[4294675.398000] ata_pci_init_one: pci_dev class+intf: 0x1018f
[4294675.398000] ata_pci_init_one: NO_LEGACY == 0
[4294675.398000] ACPI: PCI Interrupt 0000:00:1f.2[B] -> GSI 19 (level, low) -> IRQ 209
[4294675.398000] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[4294675.399000] ata1: PATA max UDMA/133 cmd 0xB800 ctl 0xB402 bmdma 0xA400 irq 209
[4294675.399000] ata2: PATA max UDMA/133 cmd 0xB000 ctl 0xA802 bmdma 0xA408 irq 209
[4294675.553000] ata1: dev 0 cfg 00:0c5a 49:2f00 82:346b 83:7d01 84:4023 85:3469 86:3c01 87:4023 88:207f 93:0000
[4294675.553000] ata1: dev 0 ATA-7, max UDMA/133, 156301488 sectors: LBA48
[4294675.553000] sata_get_dev_handle: SATA dev addr=0x1f0002, handle=0xdff96e40
[4294675.558000] ata1: dev 0 configured for UDMA/133
[4294675.558000] sata_get_dev_handle: SATA dev addr=0x1f0002, handle=0xdff96e40
[4294675.562000] scsi0 : ata_piix
[4294676.736000] ata2: disabling port
[4294676.736000] scsi1 : ata_piix
[4294676.736000]   Vendor: ATA       Model: ST3808110AS       Rev: 3.AA
[4294676.736000]   Type:   Direct-Access                      ANSI SCSI revision: 05
[4294676.742000] Driver 'sd' needs updating - please use bus_type methods
[4294676.743000] SCSI device sda: 156301488 512-byte hdwr sectors (80026 MB)
[4294676.743000] SCSI device sda: drive cache: write back
[4294676.746000] SCSI device sda: 156301488 512-byte hdwr sectors (80026 MB)
[4294676.746000] SCSI device sda: drive cache: write back
[4294676.746000]  sda: sda1 sda2 sda3 sda4
[4294676.780000] sd 0:0:0:0: Attached scsi disk sda
[4294677.019000] usbcore: registered new driver usbfs
[4294677.019000] usbcore: registered new driver hub
[4294677.020000] USB Universal Host Controller Interface driver v2.3
[4294677.020000] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 23 (level, low) -> IRQ 217
[4294677.020000] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[4294677.020000] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[4294677.021000] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[4294677.022000] uhci_hcd 0000:00:1d.0: irq 217, io base 0x00009000
[4294677.023000] hub 1-0:1.0: USB hub found
[4294677.023000] hub 1-0:1.0: 2 ports detected
[4294677.124000] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 19 (level, low) -> IRQ 209
[4294677.124000] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[4294677.124000] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[4294677.124000] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
[4294677.124000] uhci_hcd 0000:00:1d.1: irq 209, io base 0x00009400
[4294677.124000] hub 2-0:1.0: USB hub found
[4294677.124000] hub 2-0:1.0: 2 ports detected
[4294677.225000] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 201
[4294677.225000] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[4294677.225000] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[4294677.225000] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
[4294677.225000] uhci_hcd 0000:00:1d.2: irq 201, io base 0x00009800
[4294677.225000] hub 3-0:1.0: USB hub found
[4294677.225000] hub 3-0:1.0: 2 ports detected
[4294677.326000] ACPI: PCI Interrupt 0000:00:1d.3[D] -> GSI 16 (level, low) -> IRQ 169
[4294677.326000] PCI: Setting latency timer of device 0000:00:1d.3 to 64
[4294677.326000] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[4294677.326000] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 4
[4294677.326000] uhci_hcd 0000:00:1d.3: irq 169, io base 0x0000a000
[4294677.326000] hub 4-0:1.0: USB hub found
[4294677.326000] hub 4-0:1.0: 2 ports detected
[4294677.431000] usb 2-2: new low speed USB device using uhci_hcd and address 2
[4294677.481000] Probing IDE interface ide1...
[4294677.632000] usbcore: registered new driver hiddev
[4294677.684000] input: HID 1241:1177 as /class/input/input1
[4294677.684000] input: USB HID v1.10 Mouse [HID 1241:1177] on usb-0000:00:1d.1-2
[4294677.684000] usbcore: registered new driver usbhid
[4294677.684000] drivers/usb/input/hid-core.c: v2.6:USB HID core driver
[4294678.031000] Attempting manual resume
[4294678.047000] kjournald starting.  Commit interval 5 seconds
[4294678.047000] EXT3-fs: mounted filesystem with ordered data mode.
[4294684.780000] ts: Compaq touchscreen protocol output
[4294685.309000] sd 0:0:0:0: Attached scsi generic sg0 type 0
[4294686.329000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[4294686.331000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[4294686.337000] Linux agpgart interface v0.101 (c) Dave Jones
[4294686.339000] agpgart: Detected an Intel 915G Chipset.
[4294686.358000] agpgart: AGP aperture is 256M @ 0x0
[4294686.530000] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 16 (level, low) -> IRQ 169
[4294686.530000] PCI: Setting latency timer of device 0000:00:1b.0 to 64
[4294686.564000] Floppy drive(s): fd0 is 1.44M
[4294686.579000] FDC 0 is a post-1991 82077
[4294686.641000] Real Time Clock Driver v1.12
[4294686.759000] input: PC Speaker as /class/input/input2
[4294686.765000] parport: PnPBIOS parport detected.
[4294686.765000] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,EPP,ECP,DMA]
[4294687.090000] hw_random: RNG not detected
[4294687.113000] nvidia: module license 'NVIDIA' taints kernel.
[4294687.118000] ACPI: PCI Interrupt 0000:03:00.0[A] -> GSI 16 (level, low) -> IRQ 169
[4294687.118000] PCI: Setting latency timer of device 0000:03:00.0 to 64
[4294687.118000] NVRM: loading NVIDIA Linux x86 Kernel Module  1.0-8756  Wed Mar 29 14:26:26 PST 2006
[4294687.359000] via-rhine.c:v1.10-LK1.2.0-2.6 June-10-2004 Written by Donald Becker
[4294687.359000] ACPI: PCI Interrupt 0000:01:0a.0[A] -> GSI 21 (level, low) -> IRQ 225
[4294687.359000] PCI: Via IRQ fixup for 0000:01:0a.0, from 10 to 1
[4294687.365000] eth0: VIA Rhine III at 0x1c800, 00:11:95:d7:ff:6b, IRQ 225.
[4294687.366000] eth0: MII PHY found at address 1, status 0x7849 advertising 05e1 Link 0000.
[4294687.379000] Intel(R) PRO/1000 Network Driver - version 7.0.33-k2
[4294687.379000] Copyright (c) 1999-2005 Intel Corporation.
[4294687.379000] ACPI: PCI Interrupt 0000:01:03.0[A] -> GSI 19 (level, low) -> IRQ 209
[4294688.282000] e1000: 0000:01:03.0: e1000_probe: (PCI:33MHz:32-bit) 00:13:d4:f6:42:62
[4294688.307000] e1000: eth0: e1000_probe: Intel(R) PRO/1000 Network Connection
[4294688.794000] lp0: using parport0 (interrupt-driven).
[4294688.882000] Adding 979956k swap on /dev/sda3.  Priority:-1 extents:1 across:979956k
[4294689.077000] EXT3 FS on sda2, internal journal
[4294689.447000] md: md driver 0.90.3 MAX_MD_DEVS=256, MD_SB_DISKS=27
[4294689.447000] md: bitmap version 4.39
[4294689.906000] e1000: eth0: e1000_watchdog_task: NIC Link is Up 100 Mbps Full Duplex
[4294690.212000] device-mapper: 4.4.0-ioctl (2005-01-12) initialised: [email]dm-devel@redhat.com[/email]
[4294690.288000] NET: Registered protocol family 17
[4294691.516000] kjournald starting.  Commit interval 5 seconds
[4294691.516000] EXT3 FS on sda4, internal journal
[4294691.516000] EXT3-fs: mounted filesystem with ordered data mode.
[4294691.556000] NTFS driver 2.1.25 [Flags: R/O MODULE].
[4294691.615000] NTFS volume version 3.1.
[4294692.637000] NET: Registered protocol family 10
[4294692.637000] lo: Disabled Privacy Extensions
[4294692.638000] IPv6 over IPv4 tunneling driver
[4294692.756000] ACPI: Power Button (FF) [PWRF]
[4294692.756000] ACPI: Power Button (CM) [PWRB]
[4294692.837000] ibm_acpi: ec object not found
[4294692.855000] pcc_acpi: loading...
[4294697.844000] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[4294697.844000] apm: overridden by ACPI.
[4294703.142000] eth0: no IPv6 routers present
[4294703.891000] hda: drive_cmd: status=0x51 { DriveReady SeekComplete Error }
[4294703.891000] hda: drive_cmd: error=0x04 { AbortedCommand }
[4294703.891000] ide: failed opcode was: 0xec
[4294703.939000] hda: drive_cmd: status=0x51 { DriveReady SeekComplete Error }
[4294703.939000] hda: drive_cmd: error=0x04 { AbortedCommand }
[4294703.939000] ide: failed opcode was: 0xec
[4294704.490000] Bluetooth: Core ver 2.8
[4294704.490000] NET: Registered protocol family 31
[4294704.490000] Bluetooth: HCI device and connection manager initialized
[4294704.490000] Bluetooth: HCI socket layer initialized
[4294704.560000] Bluetooth: L2CAP ver 2.8
[4294704.560000] Bluetooth: L2CAP socket layer initialized
[4294704.576000] Bluetooth: RFCOMM socket layer initialized
[4294704.576000] Bluetooth: RFCOMM TTY layer initialized
[4294704.576000] Bluetooth: RFCOMM ver 1.7
[4294710.983000] ISO 9660 Extensions: Microsoft Joliet Level 3
[4294711.093000] ISOFS: changing to secondary root

(sorry my language.. english is not my native language)

---

### Post by Sef on 2006-04-26
> (sorry my language.. english is not my native language)

First your English is fine.

Second, the problem may lie in the kernal 2.6.15-21-386.  I have a different sound card, and had sound until I updated the kernel.  Now, I have no sound.

---

### Post by alerce on 2006-04-26
thanks for the feedback, 

and what you do then, you install the old kernel again?..

---

