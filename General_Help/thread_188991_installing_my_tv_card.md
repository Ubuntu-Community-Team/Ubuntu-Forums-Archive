---
title: "installing my tv card"
date: 2006-06-04
forum: General Help
---

### Post by chinozinho on 2006-06-04
I've donne a lot of search in the forum about these subject, but i'm stuck....](*,) 
my tv card is a zaapa with a Bt878
I've already installed TvTime, and done:
```
sudo modprobe -v bttv tuner=5 card=78 radio=1
```
witch, i think, are the numbers of my card, but i can't run tvtime

it always give me these message:
```
$ tvtime
running tvtime 1.0.1.
reading configuration /etc/tvtime/tvtime.xml
I/O warning : failed to load external entity "/home/andre/.tvtime/tvtime.xml"
I/O error : Permission denied
Não foi possível alterar o dono de /home/andre/.tvtime/tvtime.xml: Permissão negada.
xvoutput: No XVIDEO port found which supports YUY2 images.

*** tvtime requires hardware YUY2 overlay support from your video card
*** driver.  If you are using an older NVIDIA card (TNT2), then
*** this capability is only available with their binary drivers.
*** For some ATI cards, this feature may be found in the experimental
*** GATOS drivers: http://gatos.souceforge.net/
*** If unsure, please check with your distribution to see if your
*** X driver supports hardware overlay surfaces.
```

sorry about the lazy english :???:

---

### Post by Jose Catre-Vandis on 2006-06-04
Can you do an output of "dmesg" so we can see what is loaded tv wise (also to check your card is right)

While you are at it, take a trip to the tvtime site, there is some good info there about configuration issues, especially for overlay, which depends on what type of grpahics card you have.

---

### Post by gala on 2006-06-08
Read this link:
[http://www.ubuntuforums.org/showthread.php?t=191763&highlight=tvtime](http://www.ubuntuforums.org/showthread.php?t=191763&highlight=tvtime)

---

### Post by chinozinho on 2006-06-11
i think that that's my problem, but i'm with a Nvidia....how do i activate de xv?!?!?

i already managed to get read of these error:
```
I/O warning : failed to load external entity "/home/andre/.tvtime/tvtime.xml"
I/O error : Permission denied
Não foi possível alterar o dono de /home/andre/.tvtime/tvtime.xml: Permissão negada.
```
that was simple

but still have these one:
```
xvoutput: No XVIDEO port found which supports YUY2 images.
```
and these is the same as the one in the link gala said....but they only can fix it with ATI graphic cards....

seems to be a lot of info to fix these in ATI cards, but i can't find anything for nvidia.....

btw: the dmesg output it's huge....can i make it show me only things that can be related to thesse issue!?!?
```
[4294667.296000] WARNING: NR_CPUS limit of 1 reached.  Processor ignored.
[4294667.296000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x02] disabled)
[4294667.296000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x03] disabled)
[4294667.296000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[4294667.296000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[4294667.296000] ACPI: LAPIC_NMI (acpi_id[0x02] high edge lint[0x1])
[4294667.296000] ACPI: LAPIC_NMI (acpi_id[0x03] high edge lint[0x1])
[4294667.296000] ACPI: IOAPIC (id[0x04] address[0xfec00000] gsi_base[0])
[4294667.296000] IOAPIC[0]: apic_id 4, version 17, address 0xfec00000, GSI 0-23
[4294667.296000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[4294667.296000] ACPI: INT_SRC_OVR (bus 0 bus_irq 14 global_irq 14 high edge)
[4294667.296000] ACPI: INT_SRC_OVR (bus 0 bus_irq 15 global_irq 15 high edge)
[4294667.296000] ACPI: IRQ9 used by override.
[4294667.296000] ACPI: IRQ14 used by override.
[4294667.296000] ACPI: IRQ15 used by override.
[4294667.296000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[4294667.296000] Using ACPI (MADT) for SMP configuration information
[4294667.296000] Allocating PCI resources starting at 88000000 (gap: 80000000:60000000)
[4294667.296000] Built 1 zonelists
[4294667.296000] Kernel command line: root=/dev/sda3 ro quiet splash
[4294667.296000] mapped APIC to ffffd000 (fee00000)
[4294667.296000] mapped IOAPIC to ffffc000 (fec00000)
[4294667.296000] Initializing CPU#0
[4294667.296000] PID hash table entries: 4096 (order: 12, 65536 bytes)
[4294667.296000] Detected 3400.796 MHz processor.
[4294667.296000] Using pmtmr for high-res timesource
[4294667.296000] Console: colour VGA+ 80x25
[4294670.558000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[4294670.558000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[4294670.635000] Memory: 2068648k/2097088k available (1976k kernel code, 27136k reserved, 606k data, 288k init, 1179584k highmem)
[4294670.635000] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[4294670.695000] Calibrating delay using timer specific routine.. 6805.83 BogoMIPS (lpj=3402915)
[4294670.695000] Security Framework v1.0.0 initialized
[4294670.695000] SELinux:  Disabled at boot.
[4294670.695000] Mount-cache hash table entries: 512
[4294670.695000] CPU: After generic identify, caps: bfebfbff 20100000 00000000 00000000 0000649d 00000000 00000000
[4294670.695000] CPU: After vendor identify, caps: bfebfbff 20100000 00000000 00000000 0000649d 00000000 00000000
[4294670.695000] monitor/mwait feature present.
[4294670.695000] using mwait in idle threads.
[4294670.695000] CPU: Trace cache: 12K uops, L1 D cache: 16K
[4294670.695000] CPU: L2 cache: 2048K
[4294670.695000] CPU: After all inits, caps: bfebfbff 20100000 00000000 00000080 0000649d 00000000 00000000
[4294670.695000] mtrr: v2.0 (20020519)
[4294670.695000] CPU: Intel(R) Pentium(R) 4 CPU 3.40GHz stepping 03
[4294670.695000] Enabling fast FPU save and restore... done.
[4294670.695000] Enabling unmasked SIMD FPU exception support... done.
[4294670.695000] Checking 'hlt' instruction... OK.
[4294670.699000] checking if image is initramfs... it is
[4294671.149000] Freeing initrd memory: 6608k freed
[4294671.156000] ACPI: Looking for DSDT ... not found!
[4294671.161000] ENABLING IO-APIC IRQs
[4294671.162000] ..TIMER: vector=0x31 apic1=0 pin1=0 apic2=-1 pin2=-1
[4294671.273000] NET: Registered protocol family 16
[4294671.273000] EISA bus registered
[4294671.273000] ACPI: bus type pci registered
[4294671.276000] PCI: PCI BIOS revision 3.00 entry at 0xf25b0, last bus=3
[4294671.276000] PCI: Using MMCONFIG
[4294671.276000] ACPI: Subsystem revision 20051216
[4294671.284000] ACPI: Interpreter enabled
[4294671.284000] ACPI: Using IOAPIC for interrupt routing
[4294671.285000] ACPI: PCI Root Bridge [PCI0] (0000:00)
[4294671.285000] PCI: Probing PCI hardware (bus 00)
[4294671.290000] Boot video device is 0000:01:00.0
[4294671.290000] PCI: Transparent bridge - 0000:00:12.0
[4294671.290000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[4294671.413000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.HUB0._PRT]
[4294671.415000] ACPI: PCI Interrupt Link [LNK1] (IRQs 3 4 *5 7 10 11 12 14 15)
[4294671.416000] ACPI: PCI Interrupt Link [LNK2] (IRQs *3 4 5 7 10 11 12 14 15)
[4294671.416000] ACPI: PCI Interrupt Link [LNK3] (IRQs 3 4 5 7 10 11 12 14 15) *0, disabled.
[4294671.417000] ACPI: PCI Interrupt Link [LNK4] (IRQs 3 4 5 7 10 *11 12 14 15)
[4294671.417000] ACPI: PCI Interrupt Link [LNK5] (IRQs 3 4 *5 7 10 11 12 14 15)
[4294671.417000] ACPI: PCI Interrupt Link [LUBA] (IRQs 3 4 *5 7 10 11 12 14 15)
[4294671.418000] ACPI: PCI Interrupt Link [LUBB] (IRQs 3 4 5 7 10 *11 12 14 15)
[4294671.418000] ACPI: PCI Interrupt Link [LMAC] (IRQs 3 4 5 7 10 *11 12 14 15)
[4294671.418000] ACPI: PCI Interrupt Link [LACI] (IRQs *3 4 5 7 10 11 12 14 15)
[4294671.419000] ACPI: PCI Interrupt Link [LMCI] (IRQs 3 4 5 7 10 11 12 14 15) *0, disabled.
[4294671.419000] ACPI: PCI Interrupt Link [LSMB] (IRQs *3 4 5 7 10 11 12 14 15)
[4294671.419000] ACPI: PCI Interrupt Link [LUB2] (IRQs *3 4 5 7 10 11 12 14 15)
[4294671.420000] ACPI: PCI Interrupt Link [LIDE] (IRQs 3 4 5 7 10 11 12 14 15) *0, disabled.
[4294671.420000] ACPI: PCI Interrupt Link [LSID] (IRQs 3 4 5 7 10 *11 12 14 15)
[4294671.420000] ACPI: PCI Interrupt Link [LFID] (IRQs 3 4 *5 7 10 11 12 14 15)
[4294671.421000] ACPI: PCI Interrupt Link [APC1] (IRQs 16) *0, disabled.
[4294671.421000] ACPI: PCI Interrupt Link [APC2] (IRQs 17) *0, disabled.
[4294671.422000] ACPI: PCI Interrupt Link [APC3] (IRQs 18) *0, disabled.
[4294671.422000] ACPI: PCI Interrupt Link [APC4] (IRQs 19) *0, disabled.
[4294671.422000] ACPI: PCI Interrupt Link [APC5] (IRQs *16), disabled.
[4294671.423000] ACPI: PCI Interrupt Link [APCF] (IRQs 20 21 22 23) *0, disabled.
[4294671.423000] ACPI: PCI Interrupt Link [APCG] (IRQs 20 21 22 23) *0, disabled.
[4294671.424000] ACPI: PCI Interrupt Link [APCH] (IRQs 20 21 22 23) *0, disabled.
[4294671.424000] ACPI: PCI Interrupt Link [APCJ] (IRQs 20 21 22 23) *0, disabled.
[4294671.424000] ACPI: PCI Interrupt Link [APCK] (IRQs 20 21 22 23) *0, disabled.
[4294671.425000] ACPI: PCI Interrupt Link [APCS] (IRQs 20 21 22 23) *0, disabled.
[4294671.425000] ACPI: PCI Interrupt Link [APCL] (IRQs 20 21 22 23) *0, disabled.
[4294671.426000] ACPI: PCI Interrupt Link [APCZ] (IRQs 20 21 22 23) *0, disabled.
[4294671.426000] ACPI: PCI Interrupt Link [APSI] (IRQs 20 21 22 23) *0, disabled.
[4294671.427000] ACPI: PCI Interrupt Link [APSJ] (IRQs 20 21 22 23) *0, disabled.
[4294671.427000] ACPI: PCI Interrupt Link [APCP] (IRQs 20 21 22 23) *0, disabled.
[4294671.431000] Linux Plug and Play Support v0.97 (c) Adam Belay
[4294671.431000] pnp: PnP ACPI init
[4294671.438000] pnp: PnP ACPI: found 16 devices
[4294671.438000] PnPBIOS: Disabled by ACPI PNP
[4294671.438000] PCI: Using ACPI for IRQ routing
[4294671.438000] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[4294671.563000] pnp: 00:00: ioport range 0x4000-0x407f could not be reserved
[4294671.563000] pnp: 00:00: ioport range 0x4080-0x40ff has been reserved
[4294671.563000] pnp: 00:00: ioport range 0x4400-0x447f has been reserved
[4294671.563000] pnp: 00:00: ioport range 0x4480-0x44ff could not be reserved
[4294671.563000] pnp: 00:00: ioport range 0x4800-0x487f has been reserved
[4294671.563000] pnp: 00:00: ioport range 0x4880-0x48ff has been reserved
[4294671.564000] PCI: Bridge: 0000:00:02.0
[4294671.564000]   IO window: disabled.
[4294671.564000]   MEM window: c0000000-c7ffffff
[4294671.564000]   PREFETCH window: b0000000-bfffffff
[4294671.564000] PCI: Bridge: 0000:00:05.0
[4294671.564000]   IO window: 9000-9fff
[4294671.564000]   MEM window: c8000000-c9ffffff
[4294671.564000]   PREFETCH window: 88000000-880fffff
[4294671.564000] PCI: Bridge: 0000:00:12.0
[4294671.564000]   IO window: a000-afff
[4294671.564000]   MEM window: ca000000-caffffff
[4294671.564000]   PREFETCH window: cb000000-cbffffff
[4294671.564000] PCI: Setting latency timer of device 0000:00:02.0 to 64
[4294671.564000] PCI: Setting latency timer of device 0000:00:05.0 to 64
[4294671.564000] PCI: Setting latency timer of device 0000:00:12.0 to 64
[4294671.564000] audit: initializing netlink socket (disabled)
[4294671.564000] audit(1150051428.563:1): initialized
[4294671.564000] highmem bounce pool size: 64 pages
[4294671.564000] VFS: Disk quotas dquot_6.5.1
[4294671.564000] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[4294671.564000] Initializing Cryptographic API
[4294671.564000] io scheduler noop registered
[4294671.564000] io scheduler anticipatory registered
[4294671.564000] io scheduler deadline registered
[4294671.564000] io scheduler cfq registered
[4294671.565000] PCI: Setting latency timer of device 0000:00:02.0 to 64
[4294671.565000] pcie_portdrv_probe->Dev[007e:10de] has invalid IRQ. Check vendor BIOS
[4294671.565000] assign_interrupt_mode Found MSI capability
[4294671.565000] Allocate Port Service[pcie00]
[4294671.565000] Allocate Port Service[pcie03]
[4294671.565000] PCI: Setting latency timer of device 0000:00:05.0 to 64
[4294671.565000] pcie_portdrv_probe->Dev[007e:10de] has invalid IRQ. Check vendor BIOS
[4294671.565000] assign_interrupt_mode Found MSI capability
[4294671.565000] Allocate Port Service[pcie00]
[4294671.565000] Allocate Port Service[pcie03]
[4294671.565000] isapnp: Scanning for PnP cards...
[4294671.920000] isapnp: No Plug & Play device found
[4294671.936000] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[4294671.938000] serio: i8042 AUX port at 0x60,0x64 irq 12
[4294671.938000] serio: i8042 KBD port at 0x60,0x64 irq 1
[4294671.938000] Serial: 8250/16550 driver $Revision: 1.90 $ 48 ports, IRQ sharing enabled
[4294671.938000] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[4294671.940000] 00:08: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[4294671.941000] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[4294671.941000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[4294671.941000] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[4294671.941000] mice: PS/2 mouse device common for all mice
[4294671.941000] EISA: Probing bus 0 at eisa.0
[4294671.941000] Cannot allocate resource for EISA slot 4
[4294671.941000] Cannot allocate resource for EISA slot 5
[4294671.942000] EISA: Detected 0 cards.
[4294671.942000] NET: Registered protocol family 2
[4294671.952000] IP route cache hash table entries: 131072 (order: 7, 524288 bytes)
[4294671.952000] TCP established hash table entries: 524288 (order: 9, 2097152 bytes)
[4294671.953000] TCP bind hash table entries: 65536 (order: 6, 262144 bytes)
[4294671.953000] TCP: Hash tables configured (established 524288 bind 65536)
[4294671.953000] TCP reno registered
[4294671.953000] TCP bic registered
[4294671.953000] NET: Registered protocol family 1
[4294671.953000] NET: Registered protocol family 8
[4294671.953000] NET: Registered protocol family 20
[4294671.953000] Using IPI Shortcut mode
[4294671.953000] ACPI wakeup devices:
[4294671.953000] HUB0 XVR0 XVR1 XVR2 XVR3 XVR4 USB0 USB1 USB2 MMAC MMCI UAR1 PS2M PS2K
[4294671.953000] ACPI: (supports S0 S1 S3 S4 S5)
[4294671.953000] Freeing unused kernel memory: 288k freed
[4294671.966000] input: AT Translated Set 2 keyboard as /class/input/input0
[4294671.989000] vga16fb: initializing
[4294671.989000] vga16fb: mapped to 0xc00a0000
[4294672.200000] Console: switching to colour frame buffer device 80x25
[4294672.200000] fb0: VGA16 VGA frame buffer device
[4294673.404000] Capability LSM initialized
[4294673.428000] ACPI: Fan [FAN] (on)
[4294673.432000] ACPI: Thermal Zone [THRM] (40 C)
[4294673.927000] SCSI subsystem initialized
[4294673.929000] ACPI: bus type scsi registered
[4294673.929000] libata version 1.20 loaded.
[4294673.930000] sata_nv 0000:00:10.0: version 0.8
[4294673.930000] **** SET: Misaligned resource pointer: df8fac02 Type 07 Len 0
[4294673.930000] ACPI: PCI Interrupt Link [APSI] enabled at IRQ 23
[4294673.930000] ACPI: PCI Interrupt 0000:00:10.0[A] -> Link [APSI] -> GSI 23 (level, low) -> IRQ 201
[4294673.930000] PCI: Setting latency timer of device 0000:00:10.0 to 64
[4294673.930000] ata1: SATA max UDMA/133 cmd 0x9F0 ctl 0xBF2 bmdma 0xCC00 irq 201
[4294673.930000] ata2: SATA max UDMA/133 cmd 0x970 ctl 0xB72 bmdma 0xCC08 irq 201
[4294674.285000] ata1: dev 0 cfg 00:427a 49:2f00 82:746b 83:7f01 84:4023 85:7468 86:3c01 87:4023 88:407f 93:0000
[4294674.285000] ata1: dev 0 ATA-7, max UDMA/133, 390721968 sectors: LBA48
[4294674.289000] sata_get_dev_handle: SATA dev addr=0x100000, handle=0xdffe9e20
[4294674.298000] nv_sata: Primary device added
[4294674.298000] nv_sata: Primary device removed
[4294674.298000] nv_sata: Secondary device added
[4294674.298000] nv_sata: Secondary device removed
[4294674.298000] ata1: dev 0 configured for UDMA/133
[4294674.302000] sata_get_dev_handle: SATA dev addr=0x100000, handle=0xdffe9e20
[4294674.310000] scsi0 : sata_nv
[4294674.512000] ata2: no device found (phy stat 00000000)
[4294674.512000] scsi1 : sata_nv
[4294674.512000]   Vendor: ATA       Model: WDC WD2000JS-00M  Rev: 02.0
[4294674.512000]   Type:   Direct-Access                      ANSI SCSI revision: 05
[4294674.512000] **** SET: Misaligned resource pointer: df8faa02 Type 07 Len 0
[4294674.513000] ACPI: PCI Interrupt Link [APSJ] enabled at IRQ 22
[4294674.513000] ACPI: PCI Interrupt 0000:00:11.0[A] -> Link [APSJ] -> GSI 22 (level, low) -> IRQ 209
[4294674.513000] PCI: Setting latency timer of device 0000:00:11.0 to 64
[4294674.513000] ata3: SATA max UDMA/133 cmd 0x9E0 ctl 0xBE2 bmdma 0xE000 irq 209
[4294674.513000] ata4: SATA max UDMA/133 cmd 0x960 ctl 0xB62 bmdma 0xE008 irq 209
[4294674.516000] Driver 'sd' needs updating - please use bus_type methods
[4294674.517000] SCSI device sda: 390721968 512-byte hdwr sectors (200050 MB)
[4294674.517000] SCSI device sda: drive cache: write back
[4294674.518000] SCSI device sda: 390721968 512-byte hdwr sectors (200050 MB)
[4294674.519000] SCSI device sda: drive cache: write back
[4294674.519000]  sda: sda1 sda2 < sda5 sda6 sda7 > sda3
[4294674.559000] sd 0:0:0:0: Attached scsi disk sda
[4294674.714000] ata3: no device found (phy stat 00000000)
[4294674.714000] scsi2 : sata_nv
[4294674.915000] ata4: no device found (phy stat 00000000)
[4294674.915000] scsi3 : sata_nv
[4294674.916000] NFORCE-MCP04: IDE controller at PCI slot 0000:00:0f.0
[4294674.916000] NFORCE-MCP04: chipset revision 242
[4294674.916000] NFORCE-MCP04: not 100% native mode: will probe irqs later
[4294674.916000] NFORCE-MCP04: 0000:00:0f.0 (rev f2) UDMA133 controller
[4294674.916000]     ide0: BM-DMA at 0xf000-0xf007, BIOS settings: hda:DMA, hdb:DMA
[4294674.916000]     ide1: BM-DMA at 0xf008-0xf00f, BIOS settings: hdc:DMA, hdd:DMA
[4294674.916000] Probing IDE interface ide0...
[4294675.588000] hda: TSSTcorpDVD-ROM SH-D162C, ATAPI CD/DVD-ROM drive
[4294676.302000] hdb: TSSTcorpCD/DVDW SH-W162C, ATAPI CD/DVD-ROM drive
[4294676.354000] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[4294676.392000] Probing IDE interface ide1...
[4294676.918000] hda: ATAPI 48X DVD-ROM drive, 256kB Cache, UDMA(33)
[4294676.918000] Uniform CD-ROM driver Revision: 3.20
[4294676.924000] hdb: ATAPI 48X DVD-ROM DVD-R CD-R/RW drive, 2048kB Cache, UDMA(33)
[4294677.036000] ieee1394: Initialized config rom entry `ip1394'
[4294677.037000] ohci1394: $Rev: 1313 $ Ben Collins <bcollins@debian.org>
[4294677.037000] **** SET: Misaligned resource pointer: c225eec2 Type 07 Len 0
[4294677.037000] ACPI: PCI Interrupt Link [APC5] enabled at IRQ 16
[4294677.037000] ACPI: PCI Interrupt 0000:03:0b.0[A] -> Link [APC5] -> GSI 16 (level, low) -> IRQ 217
[4294677.094000] usbcore: registered new driver usbfs
[4294677.094000] usbcore: registered new driver hub
[4294677.095000] ohci_hcd: 2005 April 22 USB 1.1 'Open' Host Controller (OHCI) Driver (PCI)
[4294677.095000] **** SET: Misaligned resource pointer: c225eac2 Type 07 Len 0
[4294677.095000] ACPI: PCI Interrupt Link [APCF] enabled at IRQ 21
[4294677.095000] ACPI: PCI Interrupt 0000:00:0b.0[A] -> Link [APCF] -> GSI 21 (level, low) -> IRQ 225
[4294677.095000] PCI: Setting latency timer of device 0000:00:0b.0 to 64
[4294677.095000] ohci_hcd 0000:00:0b.0: OHCI Host Controller
[4294677.120000] ohci_hcd 0000:00:0b.0: new USB bus registered, assigned bus number 1
[4294677.120000] ohci_hcd 0000:00:0b.0: irq 225, io mem 0xcc004000
[4294677.126000] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[217]  MMIO=[ca024000-ca0247ff]  Max Packet=[2048]
[4294677.140000] forcedeth.c: Reverse Engineered nForce ethernet driver. Version 0.48.
[4294677.173000] hub 1-0:1.0: USB hub found
[4294677.173000] hub 1-0:1.0: 5 ports detected
[4294677.274000] **** SET: Misaligned resource pointer: c225e7c2 Type 07 Len 0
[4294677.274000] ACPI: PCI Interrupt Link [APCG] enabled at IRQ 20
[4294677.274000] ACPI: PCI Interrupt 0000:00:0b.1[B] -> Link [APCG] -> GSI 20 (level, low) -> IRQ 233
[4294677.274000] PCI: Setting latency timer of device 0000:00:0b.1 to 64
[4294677.274000] ohci_hcd 0000:00:0b.1: OHCI Host Controller
[4294677.286000] ohci_hcd 0000:00:0b.1: new USB bus registered, assigned bus number 2
[4294677.286000] ohci_hcd 0000:00:0b.1: irq 233, io mem 0xcc005000
[4294677.339000] hub 2-0:1.0: USB hub found
[4294677.339000] hub 2-0:1.0: 5 ports detected
[4294677.441000] **** SET: Misaligned resource pointer: c225e4c2 Type 07 Len 0
[4294677.441000] ACPI: PCI Interrupt Link [APCH] enabled at IRQ 23
[4294677.441000] ACPI: PCI Interrupt 0000:00:0e.0[A] -> Link [APCH] -> GSI 23 (level, low) -> IRQ 201
[4294677.441000] PCI: Setting latency timer of device 0000:00:0e.0 to 64
[4294677.442000] **** SET: Misaligned resource pointer: c225e4c2 Type 07 Len 0
[4294677.442000] ACPI: PCI Interrupt Link [APCL] enabled at IRQ 22
[4294677.442000] ACPI: PCI Interrupt 0000:00:0b.2[C] -> Link [APCL] -> GSI 22 (level, low) -> IRQ 209
[4294677.442000] PCI: Setting latency timer of device 0000:00:0b.2 to 64
[4294677.442000] ehci_hcd 0000:00:0b.2: EHCI Host Controller
[4294677.442000] ehci_hcd 0000:00:0b.2: debug port 1
[4294677.442000] PCI: cache line size of 128 is not supported by device 0000:00:0b.2
[4294677.442000] ehci_hcd 0000:00:0b.2: new USB bus registered, assigned bus number 3
[4294677.442000] ehci_hcd 0000:00:0b.2: irq 209, io mem 0xcc000000
[4294677.442000] ehci_hcd 0000:00:0b.2: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[4294677.442000] hub 3-0:1.0: USB hub found
[4294677.442000] hub 3-0:1.0: 10 ports detected
[4294677.491000] usb 1-1: new low speed USB device using ohci_hcd and address 2
[4294677.954000] eth0: forcedeth.c: subsystem: 01043:8141 bound to 0000:00:0e.0
[4294677.972000] Probing IDE interface ide1...
[4294678.377000] usb 3-7: new high speed USB device using ehci_hcd and address 4[4294678.382000] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[0011d80000674643][4294678.533000] Initializing USB Mass Storage driver...
[4294678.538000] Attempting manual resume
[4294678.562000] kjournald starting.  Commit interval 5 seconds
[4294678.562000] EXT3-fs: mounted filesystem with ordered data mode.
[4294678.742000] usb 1-1: new low speed USB device using ohci_hcd and address 3
[4294679.112000] usb 1-2: new full speed USB device using ohci_hcd and address 4[4294679.285000] scsi4 : SCSI emulation for USB Mass Storage devices
[4294679.285000] usb-storage: device found at 4
[4294679.285000] usb-storage: waiting for device to settle before scanning
[4294679.285000] usbcore: registered new driver usb-storage
[4294679.285000] USB Mass Storage support registered.
[4294684.300000]   Vendor: OTi       Model: CF CARD Reader    Rev: 2.00
[4294684.300000]   Type:   Direct-Access                      ANSI SCSI revision: 00
[4294684.344000] sd 4:0:0:0: Attached scsi removable disk sdb
[4294684.357000]   Vendor: OTi       Model: SM CARD Reader    Rev: 2.00
[4294684.357000]   Type:   Direct-Access                      ANSI SCSI revision: 00
[4294684.403000] sd 4:0:0:1: Attached scsi removable disk sdc
[4294684.416000]   Vendor: OTi       Model: SD CARD Reader    Rev: 2.00
[4294684.416000]   Type:   Direct-Access                      ANSI SCSI revision: 00
[4294684.461000] sd 4:0:0:2: Attached scsi removable disk sdd
[4294684.474000]   Vendor: OTi       Model: MS CARD Reader    Rev: 2.00
[4294684.474000]   Type:   Direct-Access                      ANSI SCSI revision: 00
[4294684.479000] sd 0:0:0:0: Attached scsi generic sg0 type 0
[4294684.479000] sd 4:0:0:0: Attached scsi generic sg1 type 0
[4294684.479000] sd 4:0:0:1: Attached scsi generic sg2 type 0
[4294684.479000] sd 4:0:0:2: Attached scsi generic sg3 type 0
[4294684.517000] sd 4:0:0:3: Attached scsi removable disk sde
[4294684.517000] sd 4:0:0:3: Attached scsi generic sg4 type 0
[4294684.518000] usb-storage: device scan complete
[4294685.668000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[4294685.670000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[4294685.862000] sata_sil24 0000:02:00.0: version 0.23
[4294685.862000] **** SET: Misaligned resource pointer: f7ea00c2 Type 07 Len 0
[4294685.862000] ACPI: PCI Interrupt Link [APC2] enabled at IRQ 17
[4294685.862000] ACPI: PCI Interrupt 0000:02:00.0[A] -> Link [APC2] -> GSI 17 (level, low) -> IRQ 50
[4294685.862000] PCI: Setting latency timer of device 0000:02:00.0 to 64
[4294685.862000] ata5: SATA max UDMA/100 cmd 0xF8A10000 ctl 0x0 bmdma 0x0 irq 50[4294685.862000] ata6: SATA max UDMA/100 cmd 0xF8A12000 ctl 0x0 bmdma 0x0 irq 50[4294686.063000] ata5: no device found (phy stat 00000000)
[4294686.063000] scsi5 : sata_sil24
[4294686.206000] **** SET: Misaligned resource pointer: f7efbb02 Type 07 Len 0
[4294686.206000] ACPI: PCI Interrupt Link [APCJ] enabled at IRQ 21
[4294686.206000] ACPI: PCI Interrupt 0000:00:13.0[A] -> Link [APCJ] -> GSI 21 (level, low) -> IRQ 225
[4294686.206000] PCI: Setting latency timer of device 0000:00:13.0 to 64
[4294686.232000] Linux agpgart interface v0.101 (c) Dave Jones
[4294686.244000] nvidia: module license 'NVIDIA' taints kernel.
[4294686.264000] ata6: no device found (phy stat 00000000)
[4294686.264000] scsi6 : sata_sil24
[4294686.359000] input: ImPS/2 Generic Wheel Mouse as /class/input/input1
[4294686.534000] intel8x0_measure_ac97_clock: measured 66653 usecs
[4294686.534000] intel8x0: clocking to 47164
[4294686.535000] **** SET: Misaligned resource pointer: f7f609c2 Type 07 Len 0
[4294686.535000] ACPI: PCI Interrupt Link [APC1] enabled at IRQ 16
[4294686.535000] ACPI: PCI Interrupt 0000:01:00.0[A] -> Link [APC1] -> GSI 16 (level, low) -> IRQ 217
[4294686.535000] PCI: Setting latency timer of device 0000:01:00.0 to 64
[4294686.535000] NVRM: loading NVIDIA Linux x86 Kernel Module  1.0-8762  Mon May 15 13:06:38 PDT 2006
[4294686.924000] drivers/usb/class/usblp.c: usblp0: USB Bidirectional printer dev 4 if 0 alt 0 proto 2 vid 0x03F0 pid 0x0704
[4294686.924000] usbcore: registered new driver usblp
[4294686.924000] drivers/usb/class/usblp.c: v0.13: USB Printer Device Class driver
[4294686.925000] usbcore: registered new driver hiddev
[4294686.933000] Real Time Clock Driver v1.12
[4294686.934000] input: PC Speaker as /class/input/input2
[4294686.942000] Linux video capture interface: v1.00
[4294686.945000] input: Mega World USB Game Controllers as /class/input/input3
[4294686.945000] input: USB HID v1.10 Joystick [Mega World USB Game Controllers] on usb-0000:00:0b.0-1
[4294686.945000] usbcore: registered new driver usbhid
[4294686.945000] drivers/usb/input/hid-core.c: v2.6:USB HID core driver
[4294686.972000] bttv: driver version 0.9.16 loaded
[4294686.972000] bttv: using 8 buffers with 2080k (520 pages) each for capture
[4294686.972000] bttv: Bt8xx card found (0).
[4294686.972000] ACPI: PCI Interrupt 0000:03:06.0[A] -> Link [APC1] -> GSI 16 (level, low) -> IRQ 217
[4294686.972000] bttv0: Bt878 (rev 17) at 0000:03:06.0, irq: 217, latency: 32, mmio: 0xcb000000
[4294686.972000] bttv0: using:  *** UNKNOWN/GENERIC ***  [card=0,autodetected]
[4294686.972000] bttv0: gpio: en=00000000, out=00000000 in=00d4dfe0 [init]
[4294686.976000] tveeprom 0-0050: Huh, no eeprom present (err=-121)?
[4294686.976000] bttv0: using tuner=-1
[4294686.976000] bttv0: i2c: checking for MSP34xx @ 0x80... not found
[4294686.978000] bttv0: i2c: checking for TDA9875 @ 0xb0... not found
[4294686.980000] bttv0: i2c: checking for TDA7432 @ 0x8a... not found
[4294686.983000] bttv0: i2c: checking for TDA9887 @ 0x86... not found
[4294686.985000] bttv0: registered device video0
[4294686.985000] bttv0: registered device vbi0
[4294686.995000] Intel(R) PRO/1000 Network Driver - version 7.0.33-k2
[4294686.995000] Copyright (c) 1999-2005 Intel Corporation.
[4294686.995000] **** SET: Misaligned resource pointer: f7e229c2 Type 07 Len 0
[4294686.996000] ACPI: PCI Interrupt Link [APC4] enabled at IRQ 19
[4294686.996000] ACPI: PCI Interrupt 0000:03:0c.0[A] -> Link [APC4] -> GSI 19 (level, low) -> IRQ 58
[4294686.998000] parport: PnPBIOS parport detected.
[4294686.999000] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
[4294687.072000] Floppy drive(s): fd0 is 1.44M
[4294687.153000] FDC 0 is a post-1991 82077
[4294687.153000] bt878: AUDIO driver version 0.0.0 loaded
[4294687.153000] bt878: Bt878 AUDIO function found (0).
[4294687.153000] ACPI: PCI Interrupt 0000:03:06.1[A] -> Link [APC1] -> GSI 16 (level, low) -> IRQ 217
[4294687.153000] bt878(0): Bt878 (rev 17) at 03:06.1, irq: 217, latency: 32, memory: 0xcb001000
[4294687.251000] e1000: 0000:03:0c.0: e1000_probe: (PCI:33MHz:32-bit) 00:13:d4:df:fc:f6
[4294687.276000] e1000: eth1: e1000_probe: Intel(R) PRO/1000 Network Connection
[4294687.378000] ts: Compaq touchscreen protocol output
[4294688.907000] e1000: eth1: e1000_watchdog_task: NIC Link is Up 100 Mbps Full Duplex
[4294688.911000] lp0: using parport0 (interrupt-driven).
[4294688.935000] sbp2: $Rev: 1306 $ Ben Collins <bcollins@debian.org>
[4294688.935000] ieee1394: sbp2: Driver forced to serialize I/O (serialize_io=1)[4294688.935000] ieee1394: sbp2: Try serialize_io=0 for better performance
[4294688.975000] Adding 843340k swap on /dev/sda7.  Priority:-1 extents:1 across:843340k
[4294689.141000] EXT3 FS on sda3, internal journal
[4294689.255000] md: md driver 0.90.3 MAX_MD_DEVS=256, MD_SB_DISKS=27
[4294689.255000] md: bitmap version 4.39
[4294689.733000] NET: Registered protocol family 17
[4294689.744000] device-mapper: 4.4.0-ioctl (2005-01-12) initialised: dm-devel@redhat.com
[4294690.244000] cdrom: open failed.
[4294690.548000] cdrom: open failed.
[4294690.552000] cdrom: open failed.
[4294691.029000] NTFS driver 2.1.25 [Flags: R/O MODULE].
[4294691.073000] NTFS volume version 3.1.
[4294691.931000] ACPI: Power Button (FF) [PWRF]
[4294691.931000] ACPI: Power Button (CM) [PWRB]
[4294692.002000] ibm_acpi: ec object not found
[4294692.022000] pcc_acpi: loading...
[4294692.468000] acpi-cpufreq: CPU0 - ACPI performance management activated.
[4294693.211000] NET: Registered protocol family 10
[4294693.211000] lo: Disabled Privacy Extensions
[4294693.212000] IPv6 over IPv4 tunneling driver
[4294699.534000] ppdev: user-space parallel port driver
[4294699.873000] apm: BIOS version 1.2 Flags 0x07 (Driver version 1.16ac)
[4294699.873000] apm: overridden by ACPI.
[4294703.646000] eth1: no IPv6 routers present
[4294703.741000] Bluetooth: Core ver 2.8
[4294703.741000] NET: Registered protocol family 31
[4294703.741000] Bluetooth: HCI device and connection manager initialized
[4294703.741000] Bluetooth: HCI socket layer initialized
[4294703.818000] Bluetooth: L2CAP ver 2.8
[4294703.818000] Bluetooth: L2CAP socket layer initialized
[4294703.820000] Bluetooth: RFCOMM socket layer initialized
[4294703.820000] Bluetooth: RFCOMM TTY layer initialized
[4294703.820000] Bluetooth: RFCOMM ver 1.7

```

---

