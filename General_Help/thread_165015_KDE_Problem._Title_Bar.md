---
title: "KDE Problem. Title Bar"
date: 2006-04-23
forum: General Help
---

### Post by mjs on 2006-04-23
Hi,

I use the Linux for work, then I decided install the kubuntu in opposite to Debian that I've always use.

After update the Kubunt yesterday the KDE was insane! The Title Bar don't appears more.

Then I've create a new user for check If the problem is with configuration, but don't is.

The snapshot can help us to help me. :)

[http://www.linuxhard.org/snapshot1.png](http://www.linuxhard.org/snapshot1.png)

Any Idea?

Thanks

---

### Post by Kethinov on 2006-04-23
Hmm. Looks like your window manager is missing. Open up a terminal and type kwin.

See if that fixes it.

---

### Post by mjs on 2006-04-23
I'm ty run it.. but I receive this message.

I'm notice that this error ocurr too always that I try run any program.

marcos@zeus:~$ kwin
X Error: BadDevice, invalid or uninitialized input device 166
  Major opcode:  144
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 166
  Major opcode:  144
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
kwin: symbol lookup error: /usr/lib/libkdeinit_kwin.so: undefined symbol: _ZN3NET16timestampCompareEmm

---

### Post by Kethinov on 2006-04-23
Well that's certainly not normal.

Type **dmesg** and show me the output.

---

### Post by mjs on 2006-04-23
[QUOTE=Kethinov]Type **dmesg** and show me the output.[/QUOTE]

O.k.

This is output:

```

[4294667.296000] Linux version 2.6.15-21-386 (buildd@rothera) (gcc version 4.0.3 (Ubuntu 4.0.3-1ubuntu5)) #1 PREEMPT Fri Apr 21 16:43:33 UTC 2006
[4294667.296000] BIOS-provided physical RAM map:
[4294667.296000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[4294667.296000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[4294667.296000]  BIOS-e820: 00000000000e4000 - 0000000000100000 (reserved)
[4294667.296000]  BIOS-e820: 0000000000100000 - 000000003ffb0000 (usable)
[4294667.296000]  BIOS-e820: 000000003ffb0000 - 000000003ffc0000 (ACPI data)
[4294667.296000]  BIOS-e820: 000000003ffc0000 - 000000003fff0000 (ACPI NVS)
[4294667.296000]  BIOS-e820: 000000003fff0000 - 0000000040000000 (reserved)
[4294667.296000]  BIOS-e820: 00000000ff780000 - 0000000100000000 (reserved)
[4294667.296000] 127MB HIGHMEM available.
[4294667.296000] 896MB LOWMEM available.
[4294667.296000] found SMP MP-table at 000ff780
[4294667.296000] On node 0 totalpages: 262064
[4294667.296000]   DMA zone: 4096 pages, LIFO batch:0
[4294667.296000]   DMA32 zone: 0 pages, LIFO batch:0
[4294667.296000]   Normal zone: 225280 pages, LIFO batch:31
[4294667.296000]   HighMem zone: 32688 pages, LIFO batch:7
[4294667.296000] DMI 2.3 present.
[4294667.296000] ACPI: RSDP (v000 ACPIAM                                ) @ 0x000fab00
[4294667.296000] ACPI: RSDT (v001 A M I  OEMRSDT  0x09000506 MSFT 0x00000097) @ 0x3ffb0000
[4294667.296000] ACPI: FADT (v001 A M I  OEMFACP  0x09000506 MSFT 0x00000097) @ 0x3ffb0200
[4294667.296000] ACPI: MADT (v001 A M I  OEMAPIC  0x09000506 MSFT 0x00000097) @ 0x3ffb0390
[4294667.296000] ACPI: OEMB (v001 A M I  OEMBIOS  0x09000506 MSFT 0x00000097) @ 0x3ffc0040
[4294667.296000] ACPI: DSDT (v001  A0232 A0232008 0x00000008 MSFT 0x0100000d) @ 0x00000000
[4294667.296000] ACPI: PM-Timer IO Port: 0x808
[4294667.296000] ACPI: Local APIC address 0xfee00000
[4294667.296000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[4294667.296000] Processor #0 15:12 APIC version 16
[4294667.296000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
[4294667.296000] IOAPIC[0]: apic_id 1, version 3, address 0xfec00000, GSI 0-23
[4294667.296000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[4294667.296000] ACPI: IRQ0 used by override.
[4294667.296000] ACPI: IRQ2 used by override.
[4294667.296000] ACPI: IRQ9 used by override.
[4294667.296000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[4294667.296000] Using ACPI (MADT) for SMP configuration information
[4294667.296000] Allocating PCI resources starting at 50000000 (gap: 40000000:bf780000)
[4294667.296000] Built 1 zonelists
[4294667.296000] Kernel command line: root=/dev/hda1 ro quiet splash
[4294667.296000] mapped APIC to ffffd000 (fee00000)
[4294667.296000] mapped IOAPIC to ffffc000 (fec00000)
[4294667.296000] Initializing CPU#0
[4294667.296000] PID hash table entries: 4096 (order: 12, 65536 bytes)
[4294667.296000] Detected 1602.262 MHz processor.
[4294667.296000] Using pmtmr for high-res timesource
[4294667.296000] Console: colour VGA+ 80x25
[4294669.717000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[4294669.718000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[4294669.743000] Memory: 1028820k/1048256k available (1974k kernel code, 18708k reserved, 604k data, 288k init, 130752k highmem)
[4294669.743000] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[4294669.803000] Calibrating delay using timer specific routine.. 3206.99 BogoMIPS (lpj=1603499)
[4294669.803000] Security Framework v1.0.0 initialized
[4294669.803000] SELinux:  Disabled at boot.
[4294669.803000] Mount-cache hash table entries: 512
[4294669.803000] CPU: After generic identify, caps: 078bfbff e3d3fbff 00000000 00000000 00000001 00000000 00000001
[4294669.803000] CPU: After vendor identify, caps: 078bfbff e3d3fbff 00000000 00000000 00000001 00000000 00000001
[4294669.803000] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[4294669.803000] CPU: L2 Cache: 256K (64 bytes/line)
[4294669.803000] CPU: After all inits, caps: 078bfbff e3d3fbff 00000000 00000010 00000001 00000000 00000001
[4294669.803000] mtrr: v2.0 (20020519)
[4294669.803000] CPU: AMD Sempron(tm) Processor 2800+ stepping 02
[4294669.803000] Enabling fast FPU save and restore... done.
[4294669.803000] Enabling unmasked SIMD FPU exception support... done.
[4294669.803000] Checking 'hlt' instruction... OK.
[4294669.807000] checking if image is initramfs... it is
[4294670.401000] Freeing initrd memory: 6393k freed
[4294670.409000] ACPI: Looking for DSDT ... not found!
[4294670.411000] ENABLING IO-APIC IRQs
[4294670.412000] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[4294670.523000] NET: Registered protocol family 16
[4294670.523000] EISA bus registered
[4294670.523000] ACPI: bus type pci registered
[4294670.523000] PCI: PCI BIOS revision 2.10 entry at 0xf0031, last bus=1
[4294670.523000] PCI: Using configuration type 1
[4294670.524000] ACPI: Subsystem revision 20051216
[4294670.528000] ACPI: Interpreter enabled
[4294670.528000] ACPI: Using IOAPIC for interrupt routing
[4294670.529000] ACPI: PCI Root Bridge [PCI0] (0000:00)
[4294670.529000] PCI: Probing PCI hardware (bus 00)
[4294670.532000] Boot video device is 0000:01:00.0
[4294670.532000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[4294670.547000] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 7 10 *11 14 15)
[4294670.547000] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 7 *10 11 14 15)
[4294670.547000] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 *5 7 10 11 14 15)
[4294670.548000] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 7 10 11 14 15) *0, disabled.
[4294670.548000] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 7 10 11 14 15) *0, disabled.
[4294670.548000] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 7 10 11 14 15) *0, disabled.
[4294670.548000] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 7 10 11 14 15) *0, disabled.
[4294670.548000] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 7 10 11 14 15) *0, disabled.
[4294670.549000] Linux Plug and Play Support v0.97 (c) Adam Belay
[4294670.549000] pnp: PnP ACPI init
[4294670.552000] pnp: PnP ACPI: found 13 devices
[4294670.552000] PnPBIOS: Disabled by ACPI PNP
[4294670.552000] PCI: Using ACPI for IRQ routing
[4294670.552000] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[4294670.557000] pnp: 00:08: ioport range 0x290-0x297 has been reserved
[4294670.557000] PCI: Bridge: 0000:00:01.0
[4294670.557000]   IO window: e000-efff
[4294670.557000]   MEM window: fbe00000-fbffffff
[4294670.557000]   PREFETCH window: f0000000-faffffff
[4294670.557000] PCI: Setting latency timer of device 0000:00:01.0 to 64
[4294670.558000] audit: initializing netlink socket (disabled)
[4294670.558000] audit(1145829706.557:1): initialized
[4294670.558000] highmem bounce pool size: 64 pages
[4294670.558000] VFS: Disk quotas dquot_6.5.1
[4294670.558000] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[4294670.558000] Initializing Cryptographic API
[4294670.558000] io scheduler noop registered
[4294670.558000] io scheduler anticipatory registered
[4294670.558000] io scheduler deadline registered
[4294670.558000] io scheduler cfq registered
[4294670.581000] isapnp: Scanning for PnP cards...
[4294671.121000] isapnp: No Plug & Play device found
[4294671.132000] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f03:PS2M] at 0x60,0x64 irq 1,12
[4294671.133000] serio: i8042 AUX port at 0x60,0x64 irq 12
[4294671.133000] serio: i8042 KBD port at 0x60,0x64 irq 1
[4294671.133000] Serial: 8250/16550 driver $Revision: 1.90 $ 48 ports, IRQ sharing enabled
[4294671.133000] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[4294671.134000] 00:0b: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[4294671.135000] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[4294671.135000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[4294671.135000] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[4294671.135000] mice: PS/2 mouse device common for all mice
[4294671.135000] EISA: Probing bus 0 at eisa.0
[4294671.135000] EISA: Detected 0 cards.
[4294671.135000] NET: Registered protocol family 2
[4294671.144000] IP route cache hash table entries: 65536 (order: 6, 262144 bytes)
[4294671.144000] TCP established hash table entries: 262144 (order: 8, 1048576 bytes)
[4294671.145000] TCP bind hash table entries: 65536 (order: 6, 262144 bytes)
[4294671.145000] TCP: Hash tables configured (established 262144 bind 65536)
[4294671.145000] TCP reno registered
[4294671.146000] TCP bic registered
[4294671.146000] NET: Registered protocol family 1
[4294671.146000] NET: Registered protocol family 8
[4294671.146000] NET: Registered protocol family 20
[4294671.146000] Using IPI Shortcut mode
[4294671.146000] ACPI wakeup devices: 
[4294671.146000] PCI0 PS2K PS2M UAR1 AC97 USB1 USB2 USB3 USB4 EHCI ILAN PWRB SLPB 
[4294671.146000] ACPI: (supports S0 S1 S3 S4 S5)
[4294671.146000] Freeing unused kernel memory: 288k freed
[4294671.163000] input: AT Translated Set 2 keyboard as /class/input/input0
[4294671.220000] vga16fb: initializing
[4294671.220000] vga16fb: mapped to 0xc00a0000
[4294671.347000] Console: switching to colour frame buffer device 80x25
[4294671.347000] fb0: VGA16 VGA frame buffer device
[4294672.496000] Capability LSM initialized
[4294673.140000] SCSI subsystem initialized
[4294673.141000] libata version 1.20 loaded.
[4294673.143000] sata_via 0000:00:0f.0: version 1.1
[4294673.143000] ACPI: PCI Interrupt 0000:00:0f.0[B] -> GSI 20 (level, low) -> IRQ 169
[4294673.143000] PCI: Via IRQ fixup for 0000:00:0f.0, from 10 to 9
[4294673.143000] sata_via 0000:00:0f.0: routed to hard irq line 9
[4294673.143000] ata1: SATA max UDMA/133 cmd 0xD800 ctl 0xD402 bmdma 0xC400 irq 169
[4294673.143000] ata2: SATA max UDMA/133 cmd 0xD000 ctl 0xC802 bmdma 0xC408 irq 169
[4294673.344000] ata1: no device found (phy stat 00000000)
[4294673.344000] scsi0 : sata_via
[4294673.545000] ata2: no device found (phy stat 00000000)
[4294673.545000] scsi1 : sata_via
[4294673.564000] VP_IDE: IDE controller at PCI slot 0000:00:0f.1
[4294673.564000] ACPI: PCI Interrupt 0000:00:0f.1[A] -> GSI 20 (level, low) -> IRQ 169
[4294673.564000] PCI: Via IRQ fixup for 0000:00:0f.1, from 255 to 9
[4294673.564000] VP_IDE: chipset revision 6
[4294673.564000] VP_IDE: not 100% native mode: will probe irqs later
[4294673.564000] VP_IDE: VIA vt8237 (rev 00) IDE UDMA133 controller on pci0000:00:0f.1
[4294673.564000]     ide0: BM-DMA at 0xfc00-0xfc07, BIOS settings: hda:DMA, hdb:DMA
[4294673.564000]     ide1: BM-DMA at 0xfc08-0xfc0f, BIOS settings: hdc:DMA, hdd:DMA
[4294673.564000] Probing IDE interface ide0...
[4294673.950000] hda: ST380011A, ATA DISK drive
[4294674.205000] hdb: Maxtor 2F040L0, ATA DISK drive
[4294674.256000] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[4294674.257000] Probing IDE interface ide1...
[4294675.051000] hdc: LG DVD-ROM DRD-8120B, ATAPI CD/DVD-ROM drive
[4294675.765000] hdd: HL-DT-ST GCE-8527B, ATAPI CD/DVD-ROM drive
[4294675.856000] ide1 at 0x170-0x177,0x376 on irq 15
[4294675.863000] hda: max request size: 1024KiB
[4294675.882000] hda: 156250000 sectors (80000 MB) w/2048KiB Cache, CHS=16383/255/63, UDMA(100)
[4294675.883000] hda: cache flushes supported
[4294675.883000]  hda: hda1 hda2 < hda5 hda6 > hda3 hda4
[4294675.957000] hdb: max request size: 128KiB
[4294675.957000] hdb: 80293248 sectors (41110 MB) w/2048KiB Cache, CHS=65535/16/63, UDMA(133)
[4294675.957000] hdb: cache flushes supported
[4294675.957000]  hdb: hdb1 hdb2 < hdb5 >
[4294675.996000] hdc: ATAPI 40X DVD-ROM drive, 512kB Cache, UDMA(33)
[4294675.996000] Uniform CD-ROM driver Revision: 3.20
[4294676.007000] hdd: ATAPI 52X CD-ROM CD-R/RW drive, 1536kB Cache, UDMA(33)
[4294677.040000] usbcore: registered new driver usbfs
[4294677.041000] usbcore: registered new driver hub
[4294677.043000] USB Universal Host Controller Interface driver v2.3
[4294677.044000] ACPI: PCI Interrupt 0000:00:10.0[A] -> GSI 21 (level, low) -> IRQ 177
[4294677.044000] PCI: Via IRQ fixup for 0000:00:10.0, from 11 to 1
[4294677.044000] uhci_hcd 0000:00:10.0: UHCI Host Controller
[4294677.045000] uhci_hcd 0000:00:10.0: new USB bus registered, assigned bus number 1
[4294677.045000] uhci_hcd 0000:00:10.0: irq 177, io base 0x0000a800
[4294677.046000] hub 1-0:1.0: USB hub found
[4294677.046000] hub 1-0:1.0: 2 ports detected
[4294677.147000] ACPI: PCI Interrupt 0000:00:10.1[A] -> GSI 21 (level, low) -> IRQ 177
[4294677.147000] PCI: Via IRQ fixup for 0000:00:10.1, from 11 to 1
[4294677.147000] uhci_hcd 0000:00:10.1: UHCI Host Controller
[4294677.147000] uhci_hcd 0000:00:10.1: new USB bus registered, assigned bus number 2
[4294677.147000] uhci_hcd 0000:00:10.1: irq 177, io base 0x0000b000
[4294677.147000] hub 2-0:1.0: USB hub found
[4294677.147000] hub 2-0:1.0: 2 ports detected
[4294677.248000] ACPI: PCI Interrupt 0000:00:10.2[B] -> GSI 21 (level, low) -> IRQ 177
[4294677.248000] PCI: Via IRQ fixup for 0000:00:10.2, from 10 to 1
[4294677.248000] uhci_hcd 0000:00:10.2: UHCI Host Controller
[4294677.248000] uhci_hcd 0000:00:10.2: new USB bus registered, assigned bus number 3
[4294677.248000] uhci_hcd 0000:00:10.2: irq 177, io base 0x0000b400
[4294677.248000] hub 3-0:1.0: USB hub found
[4294677.248000] hub 3-0:1.0: 2 ports detected
[4294677.349000] ACPI: PCI Interrupt 0000:00:10.3[B] -> GSI 21 (level, low) -> IRQ 177
[4294677.349000] PCI: Via IRQ fixup for 0000:00:10.3, from 10 to 1
[4294677.349000] uhci_hcd 0000:00:10.3: UHCI Host Controller
[4294677.349000] uhci_hcd 0000:00:10.3: new USB bus registered, assigned bus number 4
[4294677.349000] uhci_hcd 0000:00:10.3: irq 177, io base 0x0000b800
[4294677.349000] hub 4-0:1.0: USB hub found
[4294677.349000] hub 4-0:1.0: 2 ports detected
[4294677.453000] ACPI: PCI Interrupt 0000:00:10.4[C] -> GSI 21 (level, low) -> IRQ 177
[4294677.453000] PCI: Via IRQ fixup for 0000:00:10.4, from 5 to 1
[4294677.453000] ehci_hcd 0000:00:10.4: EHCI Host Controller
[4294677.453000] ehci_hcd 0000:00:10.4: new USB bus registered, assigned bus number 5
[4294677.453000] ehci_hcd 0000:00:10.4: irq 177, io mem 0xfbc00000
[4294677.453000] ehci_hcd 0000:00:10.4: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[4294677.453000] hub 5-0:1.0: USB hub found
[4294677.453000] hub 5-0:1.0: 8 ports detected
[4294677.762000] Attempting manual resume
[4294677.773000] SGI XFS with ACLs, security attributes, realtime, large block numbers, no debug enabled
[4294677.773000] SGI XFS Quota Management subsystem
[4294677.788000] XFS mounting filesystem hda1
[4294677.879000] Ending clean XFS mount for filesystem: hda1
[4294678.599000] usb 5-7: new high speed USB device using ehci_hcd and address 4
[4294678.924000] usb 2-1: new low speed USB device using uhci_hcd and address 2
[4294684.283000] usb 2-2: new full speed USB device using uhci_hcd and address 3
[4294689.558000] Linux agpgart interface v0.101 (c) Dave Jones
[4294689.559000] agpgart: Detected AGP bridge 0
[4294689.561000] agpgart: AGP aperture is 32M @ 0xec000000
[4294689.801000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[4294689.806000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[4294690.125000] via-rhine.c:v1.10-LK1.2.0-2.6 June-10-2004 Written by Donald Becker
[4294690.126000] ACPI: PCI Interrupt 0000:00:12.0[A] -> GSI 23 (level, low) -> IRQ 185
[4294690.126000] PCI: Via IRQ fixup for 0000:00:12.0, from 11 to 9
[4294690.127000] eth0: VIA Rhine II at 0x1a000, 00:15:f2:17:50:8a, IRQ 185.
[4294690.128000] eth0: MII PHY found at address 1, status 0x786d advertising 01e1 Link 0021.
[4294690.687000] Initializing USB Mass Storage driver...
[4294690.687000] scsi2 : SCSI emulation for USB Mass Storage devices
[4294690.687000] usb-storage: device found at 4
[4294690.687000] usb-storage: waiting for device to settle before scanning
[4294690.687000] usbcore: registered new driver usb-storage
[4294690.687000] USB Mass Storage support registered.
[4294690.826000] ACPI: PCI Interrupt 0000:00:11.5[C] -> GSI 22 (level, low) -> IRQ 193
[4294690.826000] PCI: Via IRQ fixup for 0000:00:11.5, from 5 to 1
[4294690.833000] PCI: Setting latency timer of device 0000:00:11.5 to 64
[4294690.890000] Real Time Clock Driver v1.12
[4294690.927000] input: PC Speaker as /class/input/input1
[4294690.973000] Linux video capture interface: v1.00
[4294691.100000] drivers/usb/media/spca5xx/spca5xx-main.c: USB SPCA5XX camera found. Type Intel Create and Share (SPCA501 )
[4294691.113000] input: PS/2 Generic Mouse as /class/input/input2
[4294691.172000] Floppy drive(s): fd0 is 1.44M
[4294691.186000] FDC 0 is a post-1991 82077
[4294691.204000] parport: PnPBIOS parport detected.
[4294691.205000] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,EPP,ECP,DMA]
[4294691.231000] ts: Compaq touchscreen protocol output
[4294691.311000] eth0: link up, 10Mbps, half-duplex, lpa 0x0021
[4294691.345000] codec_read: codec 0 is not valid [0xfe0000]
[4294691.353000] codec_read: codec 0 is not valid [0xfe0000]
[4294691.360000] codec_read: codec 0 is not valid [0xfe0000]
[4294691.367000] codec_read: codec 0 is not valid [0xfe0000]
[4294691.503000] usbcore: registered new driver spca5xx
[4294691.503000] drivers/usb/media/spca5xx/spca5xx-main.c: spca5xx driver 00.57.08 registered
[4294692.050000] NET: Registered protocol family 10
[4294692.050000] lo: Disabled Privacy Extensions
[4294692.051000] IPv6 over IPv4 tunneling driver
[4294692.318000] lp0: using parport0 (interrupt-driven).
[4294693.824000] Adding 489972k swap on /dev/hda4.  Priority:-1 extents:1 across:489972k
[4294694.087000] md: md driver 0.90.3 MAX_MD_DEVS=256, MD_SB_DISKS=27
[4294694.087000] md: bitmap version 4.39
[4294694.692000] device-mapper: 4.4.0-ioctl (2005-01-12) initialised: [email]dm-devel@redhat.com[/email]
[4294694.959000] cdrom: open failed.
[4294695.455000] cdrom: open failed.
[4294695.457000] cdrom: open failed.
[4294695.688000]   Vendor: I-Stick2  Model: IntelligentStick  Rev: 2.00
[4294695.688000]   Type:   Direct-Access                      ANSI SCSI revision: 02
[4294695.690000] usb-storage: device scan complete
[4294695.739000] Driver 'sd' needs updating - please use bus_type methods
[4294695.740000] SCSI device sda: 255488 512-byte hdwr sectors (131 MB)
[4294695.741000] sda: Write Protect is off
[4294695.741000] sda: Mode Sense: 03 00 00 00
[4294695.741000] sda: assuming drive cache: write through
[4294695.747000] SCSI device sda: 255488 512-byte hdwr sectors (131 MB)
[4294695.748000] sda: Write Protect is off
[4294695.748000] sda: Mode Sense: 03 00 00 00
[4294695.748000] sda: assuming drive cache: write through
[4294695.748000]  sda: unknown partition table
[4294695.752000] sd 2:0:0:0: Attached scsi removable disk sda
[4294695.767000] sd 2:0:0:0: Attached scsi generic sg0 type 0
[4294697.210000] kjournald starting.  Commit interval 5 seconds
[4294697.210000] EXT3 FS on hda3, internal journal
[4294697.210000] EXT3-fs: mounted filesystem with ordered data mode.
[4294697.246000] XFS mounting filesystem hda5
[4294697.331000] Ending clean XFS mount for filesystem: hda5
[4294698.699000] ACPI: Power Button (FF) [PWRF]
[4294698.699000] ACPI: Power Button (CM) [PWRB]
[4294698.699000] ACPI: Sleep Button (CM) [SLPB]
[4294698.811000] ibm_acpi: ec object not found
[4294698.836000] pcc_acpi: loading...
[4294699.351000] powernow-k8: Power state transitions not supported
[4294702.485000] eth0: no IPv6 routers present
[4294703.763000] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[4294703.763000] apm: overridden by ACPI.
[4294704.468000] hdc: drive_cmd: status=0x51 { DriveReady SeekComplete Error }
[4294704.468000] hdc: drive_cmd: error=0x04 { AbortedCommand }
[4294704.468000] ide: failed opcode was: 0xec
[4294704.474000] hdd: drive_cmd: status=0x51 { DriveReady SeekComplete Error }
[4294704.474000] hdd: drive_cmd: error=0x04 { AbortedCommand }
[4294704.474000] ide: failed opcode was: 0xec
[4294704.651000] hdc: drive_cmd: status=0x51 { DriveReady SeekComplete Error }
[4294704.651000] hdc: drive_cmd: error=0x04 { AbortedCommand }
[4294704.651000] ide: failed opcode was: 0xec
[4294704.657000] hdd: drive_cmd: status=0x51 { DriveReady SeekComplete Error }
[4294704.657000] hdd: drive_cmd: error=0x04 { AbortedCommand }
[4294704.657000] ide: failed opcode was: 0xec
[4294711.466000] Bluetooth: Core ver 2.8
[4294711.466000] NET: Registered protocol family 31
[4294711.466000] Bluetooth: HCI device and connection manager initialized
[4294711.466000] Bluetooth: HCI socket layer initialized
[4294711.489000] Bluetooth: L2CAP ver 2.8
[4294711.489000] Bluetooth: L2CAP socket layer initialized
[4294711.514000] Bluetooth: RFCOMM socket layer initialized
[4294711.514000] Bluetooth: RFCOMM TTY layer initialized
[4294711.514000] Bluetooth: RFCOMM ver 1.7
[4294901.839000] UDF-fs: No VRS found
[4294901.873000] UDF-fs: No VRS found
[4294901.966000] Unable to identify CD-ROM format.
[4294902.016000] Unable to identify CD-ROM format.
[4294902.023000] FAT: utf8 is not a recommended IO charset for FAT filesystems, filesystem will be case sensitive!

```

---

### Post by Kethinov on 2006-04-23
I don't see any scary, menacing hardware failure messages there, but those errors you get when running kwin would seem to suggest one of your input devices is screwed up.

Since this only started happening to you recently, I doubt it's an issue with your xorg.conf. Maybe it's just a bug in the latest kwin or KDE. Does this occur in other desktop environments like GNOME, XFCE, or other window managers like icewm etc?

---

### Post by mjs on 2006-04-24
> menacing hardware failure messages there

Do you can say me what hardware? HDC and HDD are the DVD and CD-BURN drivers respectively.

> Maybe it's just a bug in the latest kwin or KDE.

Exist a new version of kwin in the sources... now I'm downloading.

> Does this occur in other desktop environments like GNOME, XFCE, or other window managers like icewm etc?

I don't. In the hdb I have the windows XP and the hardware and devices work fine.

> but those errors you get when running kwin would seem to suggest one of your input devices is screwed up.

If the update don't resolve my problem, then I'm disconnect all the devices and test for see.


Thaks for help.

Marcos

---

### Post by mjs on 2006-04-24
Unfortunately the update don't solve my problem :(.

I turn off the drivers of CD and DVD but the problem continues.

any idea?

I'm going now to install the gnome to see if it works fine.

Thanks for you paticience and help.

---

### Post by Kethinov on 2006-04-25
You need to find out if it's a KDE specific problem. Let me know if GNOME or any other desktop environment suffers from the same issue.

---

### Post by mjs on 2006-04-25
Hi Kethinov,

Today I finished the download and instalation of GNOME, it works fine!!! I'm in the GNOME with Title bar working very fine.

I'm thinking that problem is a bug with KDE. What do you think?

Thanks.

Marcos.

---

### Post by Kethinov on 2006-04-25
It's possible that you have some sort of preferences corruption in your KDE configs, some setting gone wrong somewhere. I'm not well versed enough in KDE to guess what exactly might have gone wrong, but if you erase your ~/.kde directory or maybe move it to another location it might cause KDE to "start fresh" so to speak, which might solve your problem. Just a guess though.

---

### Post by mjs on 2006-04-25
I've done this before. And every time that i did the update I delete the content of /home/teste to check if the problem is fix.

---

