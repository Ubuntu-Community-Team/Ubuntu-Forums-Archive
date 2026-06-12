---
title: "Fan won't start up on Toshiba Tecra 8100."
date: 2006-05-10
forum: General Help
---

### Post by Hydraulix on 2006-05-10
The fan won't work unless I do a toshset -fan high and then the fan works but it won't start during boot. It also won't start at all unless I run that command.


272
[4294667.296000] DMA zone: 4096 pages, LIFO batch:1
[4294667.296000] Normal zone: 94176 pages, LIFO batch:31
[4294667.296000] HighMem zone: 0 pages, LIFO batch:1
[4294667.296000] DMI 2.3 present.
[4294667.296000] ACPI: RSDP (v000 TOSHIB ) @ 0x00
0f4fd0
[4294667.296000] ACPI: RSDT (v001 TOSHIB 750 0x00970814 TASM 0x04010000) @
0x17fe0000
[4294667.296000] ACPI: FADT (v001 TOSHIB 750 0x00970814 TASM 0x04010000) @
0x17fe0054
[4294667.296000] ACPI: BOOT (v001 TOSHIB 750 0x00970814 TASM 0x04010000) @
0x17fe002c
[4294667.296000] ACPI: DSDT (v001 TOSHIB 8100 0x20000614 MSFT 0x0100000a) @
0x00000000
[4294667.296000] ACPI: PM-Timer IO Port: 0xfe08
[4294667.296000] Allocating PCI resources starting at 18000000 (gap: 18000000:e7
f80000)
[4294667.296000] Built 1 zonelists
[4294667.296000] Kernel command line: root=/dev/hda1 ro quiet splash
[4294667.296000] Local APIC disabled by BIOS -- you can enable it with "lapic"
[4294667.296000] mapped APIC to ffffd000 (01302000)
[4294667.296000] Initializing CPU#0
[4294667.296000] PID hash table entries: 2048 (order: 11, 32768 bytes)
[4294667.296000] Detected 498.187 MHz processor.
[4294667.296000] Using pmtmr for high-res timesource
[4294667.296000] Console: colour VGA+ 80x25
[4294667.632000] Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)
[4294667.634000] Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)
[4294667.688000] Memory: 381188k/393088k available (1416k kernel code, 11340k re
served, 762k data, 224k init, 0k highmem)
[4294667.688000] Checking if this processor honours the WP bit even in superviso
r mode... Ok.
[4294667.688000] Calibrating delay loop... 987.13 BogoMIPS (lpj=49356
[4294667.708000] Security Framework v1.0.0 initialized
[4294667.708000] SELinux: Disabled at boot.
[4294667.708000] Mount-cache hash table entries: 512
[4294667.708000] CPU: After generic identify, caps: 0383f9ff 00000000 00000000 0
0000000 00000000 00000000 00000000
[4294667.708000] CPU: After vendor identify, caps: 0383f9ff 00000000 00000000 00
000000 00000000 00000000 00000000
[4294667.708000] CPU: L1 I cache: 16K, L1 D cache: 16K
[4294667.708000] CPU: L2 cache: 256K
[4294667.708000] CPU: After all inits, caps: 0383f9ff 00000000 00000000 00000040
00000000 00000000 00000000
[4294667.708000] CPU: Intel Pentium III (Coppermine) stepping 01
[4294667.708000] Enabling fast FPU save and restore... done.
[4294667.708000] Enabling unmasked SIMD FPU exception support... done.
[4294667.708000] Checking 'hlt' instruction... OK.
[4294667.712000] Checking for popad bug... OK.
[4294667.712000] checking if image is initramfs... it is
[4294669.296000] Freeing initrd memory: 5175k freed
[4294669.299000] ACPI: Looking for DSDT in initrd... not found!
[4294669.538000] not found!
[4294669.576000] ACPI: setting ELCR to 0200 (from 080
[4294669.578000] NET: Registered protocol family 16
[4294669.578000] EISA bus registered
[4294669.578000] ACPI: bus type pci registered
[4294669.580000] PCI: PCI BIOS revision 2.10 entry at 0xfee03, last bus=21
[4294669.580000] PCI: Using configuration type 1
[4294669.580000] mtrr: v2.0 (20020519)
[4294669.581000] ACPI: Subsystem revision 20050729
[4294669.600000] ACPI: Interpreter enabled
[4294669.600000] ACPI: Using PIC for interrupt routing
[4294669.603000] ACPI: PCI Interrupt Link [LNKA] (IRQs 5 6 7 10 *11 12)
[4294669.606000] ACPI: PCI Interrupt Link [LNKB] (IRQs 5 6 7 10 *11 12)
[4294669.609000] ACPI: PCI Interrupt Link [LNKC] (IRQs 5 6 7 10 *11 12)
[4294669.612000] ACPI: PCI Interrupt Link [LNKD] (IRQs 5 6 7 10 *11 12)
[4294669.616000] ACPI: PCI Interrupt Link [LNKE] (IRQs *3 4)
[4294669.617000] ACPI: PCI Root Bridge [PCI0] (0000:00)
[4294669.617000] PCI: Probing PCI hardware (bus 00)
[4294669.620000] ACPI: Assume root bridge [\_SB_.PCI0] segment is 0
[4294669.620000] ACPI: Assume root bridge [\_SB_.PCI0] bus is 0
[4294669.625000] Boot video device is 0000:01:00.0
[4294669.638000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[4294669.646000] ACPI: Power Resource [PIHD] (on)
[4294669.647000] ACPI: Power Resource [PMHD] (on)
[4294669.651000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCI1._PRT]
[4294669.654000] ACPI: Power Resource [PFAN] (off)
[4294669.654000] Linux Plug and Play Support v0.97 (c) Adam Belay
[4294669.654000] pnp: PnP ACPI init
[4294669.659000] PCI: setting IRQ 13 as level-triggered
[4294669.681000] pnp: PnP ACPI: found 12 devices
[4294669.681000] PnPBIOS: Disabled by ACPI PNP
[4294669.681000] PCI: Using ACPI for IRQ routing
[4294669.681000] PCI: If a device doesn't work, try "pci=routeirq". If it helps
, post a report
[4294669.701000] Simple Boot Flag value 0x37 read from CMOS RAM was invalid
[4294669.701000] Simple Boot Flag at 0x0 set to 0x1
[4294669.702000] audit: initializing netlink socket (disabled)
[4294669.702000] audit: initialized
[4294669.703000] VFS: Disk quotas dquot_6.5.1
[4294669.703000] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[4294669.703000] devfs: 2004-01-31 Richard Gooch (rgooch@atnf.csiro.au)
[4294669.703000] devfs: boot_options: 0x0
[4294669.703000] Initializing Cryptographic API
[4294669.703000] Limiting direct PCI/PCI transfers.
[4294669.703000] isapnp: Scanning for PnP cards...
[4294670.057000] isapnp: No Plug & Play device found
[4294670.114000] PNP: PS/2 Controller [PNP0303:KBC,PNP0f13:PS2M] at 0x60,0x64 ir
q 1,12
[4294670.116000] serio: i8042 AUX port at 0x60,0x64 irq 12
[4294670.116000] serio: i8042 KBD port at 0x60,0x64 irq 1
[4294670.116000] Serial: 8250/16550 driver $Revision: 1.90 $ 54 ports, IRQ shari
ng enabled
[4294670.117000] ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[4294670.123000] ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[4294670.124000] io scheduler noop registered
[4294670.124000] io scheduler anticipatory registered
[4294670.124000] io scheduler deadline registered
[4294670.124000] io scheduler cfq registered
[4294670.125000] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 bl
ocksize
[4294670.125000] EISA: Probing bus 0 at eisa.0
[4294670.126000] Cannot allocate resource for EISA slot 1
[4294670.126000] EISA: Detected 0 cards.
[4294670.126000] NET: Registered protocol family 2
[4294670.135000] IP: routing cache hash table of 4096 buckets, 32Kbytes
[4294670.135000] TCP established hash table entries: 16384 (order: 5, 131072 byt
es)
[4294670.136000] TCP bind hash table entries: 16384 (order: 4, 65536 bytes)
[4294670.136000] TCP: Hash tables configured (established 16384 bind 16384)
[4294670.136000] NET: Registered protocol family 8
[4294670.136000] NET: Registered protocol family 20
[4294670.137000] ACPI wakeup devices:
[4294670.137000] COM USB VIY0 VIY1 MODM LAN DLAN NOV0 LID
[4294670.137000] ACPI: (supports S0 S1 S3 S4 S4bios S5)
[4294670.138000] Freeing unused kernel memory: 224k freed
[4294670.165000] input: AT Translated Set 2 keyboard on isa0060/serio0
[4294670.190000] vga16fb: initializing
[4294670.190000] vga16fb: mapped to 0xc00a0000
[4294670.327000] Console: switching to colour frame buffer device 80x30
[4294670.327000] fb0: VGA16 VGA frame buffer device
[4294671.649000] Capability LSM initialized
[4294671.693000] NET: Registered protocol family 1
[4294671.739000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[4294671.739000] ide: Assuming 33MHz system bus speed for PIO modes; override wi
th idebus=xx
[4294671.739000] ACPI: bus type ide registered
[4294671.762000] PIIX4: IDE controller at PCI slot 0000:00:05.1
[4294671.762000] PIIX4: chipset revision 1
[4294671.762000] PIIX4: not 100% native mode: will probe irqs later
[4294671.762000] ide0: BM-DMA at 0xfff0-0xfff7, BIOS settings: hdaMA, hdb:
pio
[4294671.762000] ide1: BM-DMA at 0xfff8-0xffff, BIOS settings: hdcMA, hdd:
pio
[4294671.762000] Probing IDE interface ide0...
[4294672.026000] hda: IBM-DARA-212000, ATA DISK drive
[4294672.638000] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[4294672.638000] Probing IDE interface ide1...
[4294673.310000] hdc: CD-224E-B, ATAPI CD/DVD-ROM drive
[4294673.922000] ide1 at 0x170-0x177,0x376 on irq 15
[4294673.922000] Probing IDE interface ide2...
[4294674.435000] Probing IDE interface ide3...
[4294674.948000] Probing IDE interface ide4...
[4294675.461000] Probing IDE interface ide5...
[4294675.987000] hda: max request size: 128KiB
[4294676.023000] hda: 23579136 sectors (12072 MB) w/418KiB Cache, CHS=23392/16/6
3, UDMA(33)
[4294676.023000] hda: cache flushes not supported
[4294676.024000] /dev/ide/host0/bus0/target0/lun0: p1 p2 < p5 >
[4294676.094000] hdc: ATAPI 24X CD-ROM drive, 128kB Cache
[4294676.094000] Uniform CD-ROM driver Revision: 3.20
[4294676.951000] Attempting manual resume
[4294676.951000] swsusp: Suspend partition has wrong signature?
[4294677.108000] usbcore: registered new driver usbfs
[4294677.108000] usbcore: registered new driver hub
[4294677.113000] USB Universal Host Controller Interface driver v2.2
[4294677.116000] ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 11
[4294677.116000] PCI: setting IRQ 11 as level-triggered
[4294677.116000] ACPI: PCI Interrupt 0000:00:05.2[D] -> Link [LNKD] -> GSI 11 (l
evel, low) -> IRQ 11
[4294677.116000] uhci_hcd 0000:00:05.2: Intel Corporation 82371AB/EB/MB PIIX4 US
B
[4294677.178000] uhci_hcd 0000:00:05.2: new USB bus registered, assigned bus num
ber 1
[4294677.178000] uhci_hcd 0000:00:05.2: irq 11, io base 0x0000ff80
[4294677.178000] hub 1-0:1.0: USB hub found
[4294677.178000] hub 1-0:1.0: 2 ports detected
[4294680.396000] ACPI: Fan [FAN] (off)
[4294680.408000] ACPI: CPU0 (power states: C1[C1] C2[C2])
[4294680.412000] ACPI: Thermal Zone [THRM] (27 C)
[4294680.682000] Attempting manual resume
[4294680.682000] swsusp: Suspend partition has wrong signature?
[4294680.732000] kjournald starting. Commit interval 5 seconds
[4294680.732000] EXT3-fs: mounted filesystem with ordered data mode.
[4294683.433000] md: md driver 0.90.1 MAX_MD_DEVS=256, MD_SB_DISKS=27
[4294691.057000] Adding 514040k swap on /dev/hda5. Priority:-1 extents:1
[4294691.502000] EXT3 FS on hda1, internal journal
[4294709.595000] parport: PnPBIOS parport detected.
[4294709.595000] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
[4294709.692000] lp0: using parport0 (interrupt-driven).
[4294709.779000] mice: PS/2 mouse device common for all mice
[4294710.269000] logips2pp: Detected unknown logitech mouse model 0
[4294710.505000] input: ImPS/2 Logitech Wheel Mouse on isa0060/serio1
[4294710.515000] piix4_smbus 0000:00:05.3: Found 0000:00:05.3 device
[4294711.473000] ts: Compaq touchscreen protocol output
[4294714.964000] device-mapper: 4.4.0-ioctl (2005-01-12) initialised: dm-devel@r
edhat.com
[4294716.733000] cdrom: open failed.
[4294720.986000] Linux agpgart interface v0.101 (c) Dave Jones
[4294721.018000] agpgart: Detected an Intel 440BX Chipset.
[4294721.057000] agpgart: AGP aperture is 256M @ 0xd0000000
[4294721.495000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[4294721.516000] shpchp: acpi_shpchprm:\_SB_.PCI0 evaluate _BBN fail=0x5
[4294721.516000] shpchp: acpi_shpchprm:get_device PCI ROOT HID fail=0x5
[4294722.591000] irda_init()
[4294722.591000] NET: Registered protocol family 23
[4294722.625000] ACPI: PCI Interrupt Link [LNKC] enabled at IRQ 11
[4294722.625000] ACPI: PCI Interrupt 0000:00:09.0[A] -> Link [LNKC] -> GSI 11 (l
evel, low) -> IRQ 11
[4294722.637000] IrDA: Registered device irda0
[4294722.637000] toshoboe: Using multiple tasks, version $Id: donauboe.c V2.18 v
en jan 10 03:14:16 2003$
[4294724.184000] Linux Kernel Card Services
[4294724.184000] options: [pci] [cardbus] [pm]
[4294724.231000] PCI: Enabling device 0000:00:0b.0 (0000 -> 0002)
[4294724.233000] ACPI: PCI Interrupt Link [LNKA] enabled at IRQ 11
[4294724.233000] ACPI: PCI Interrupt 0000:00:0b.0[A] -> Link [LNKA] -> GSI 11 (l
evel, low) -> IRQ 11
[4294724.233000] Yenta: CardBus bridge found at 0000:00:0b.0 [1179:0001]
[4294724.353000] Yenta: ISA IRQ mask 0x0438, PCI irq 11
[4294724.353000] Socket status: 30000007
[4294724.402000] PCI: Enabling device 0000:00:0b.1 (0000 -> 0002)
[4294724.404000] ACPI: PCI Interrupt Link [LNKB] enabled at IRQ 11
[4294724.404000] ACPI: PCI Interrupt 0000:00:0b.1[b] -> Link [LNKB] -> GSI 11 (l
evel, low) -> IRQ 11
[4294724.404000] Yenta: CardBus bridge found at 0000:00:0b.1 [1179:0001]
[4294724.524000] Yenta: ISA IRQ mask 0x0438, PCI irq 11
[4294724.524000] Socket status: 30000020
[4294725.643000] ACPI: PCI Interrupt 0000:00:0c.0[A] -> Link [LNKD] -> GSI 11 (l
evel, low) -> IRQ 11
[4294725.706000] ath_hal: module license 'Proprietary' taints kernel.
[4294725.720000] ath_hal: 0.9.14.9 (AR5210, AR5211, AR5212, RF5111, RF5112, RF24
13)
[4294725.740000] wlan: 0.8.6.0 (EXPERIMENTAL)
[4294725.755000] ath_rate_sample: 1.2
[4294725.790000] ath_pci: 0.9.6.0 (EXPERIMENTAL)
[4294726.336000] PCI: Enabling device 0000:06:00.0 (0000 -> 0002)
[4294726.336000] ACPI: PCI Interrupt 0000:06:00.0[A] -> Link [LNKB] -> GSI 11 (l
evel, low) -> IRQ 11
[4294727.046000] Build date: Nov 22 2005
[4294727.046000] Debugging version (IEEE80211)
[4294727.046000] ath0: 11b rates: 1Mbps 2Mbps 5.5Mbps 11Mbps
[4294727.046000] ath0: 11g rates: 1Mbps 2Mbps 5.5Mbps 11Mbps 6Mbps 9Mbps 12Mbps
18Mbps 24Mbps 36Mbps 48Mbps 54Mbps
[4294727.046000] ath0: H/W encryption support: WEP AES AES_CCM TKIP
[4294727.046000] ath0: mac 7.8 phy 4.5 radio 5.6
[4294727.046000] ath0: Use hw queue 1 for WME_AC_BE traffic
[4294727.046000] ath0: Use hw queue 0 for WME_AC_BK traffic
[4294727.046000] ath0: Use hw queue 2 for WME_AC_VI traffic
[4294727.046000] ath0: Use hw queue 3 for WME_AC_VO traffic
[4294727.046000] ath0: Use hw queue 8 for CAB traffic
[4294727.046000] ath0: Use hw queue 9 for beacons
[4294727.046000] Debugging version (ATH)
[4294727.046000] ath0: Atheros 5212: mem=0x19000000, irq=11
[4294729.444000] input: PC Speaker
[4294730.049000] Real Time Clock Driver v1.12
[4294730.284000] Floppy drive(s): fd0 is 1.44M
[4294730.298000] FDC 0 is an 8272A
[4294734.224000] NET: Registered protocol family 17
[4294743.346000] NET: Registered protocol family 10
[4294743.346000] Disabled Privacy Extensions on device c02eb280(lo)
[4294743.347000] IPv6 over IPv4 tunneling driver
[4294745.690000] ACPI: AC Adapter [ADP1] (on-line)
[4294745.851000] ACPI: Battery Slot [BAT1] (battery present)
[4294745.851000] ACPI: Battery Slot [BAT2] (battery absent)
[4294745.926000] ACPI: Power Button (FF) [PWRF]
[4294745.926000] ACPI: Lid Switch [LID]
[4294746.300000] ibm_acpi: ec object not found
[4294746.631000] toshiba_acpi: Toshiba Laptop ACPI Extras version 0.19a-dev
[4294746.631000] toshiba_acpi: HCI method: \_SB_.VALD.GHCI
[4294746.681000] toshiba_acpi: Toshiba hotkeys are sent as ACPI events
[4294746.681000] toshiba_acpi: ktoshkeyd will check 2 times per second
[4294746.682000] toshiba_acpi: Dropped 0 keys from the queue on startup
[4294746.757000] ACPI: Video Device [VGA] (multi-head: yes rom: yes post: no)
[4294753.524000] ath0: no IPv6 routers present
[4294759.408000] apm: BIOS version 1.2 Flags 0x02 (Driver version 1.16ac)
[4294759.408000] apm: overridden by ACPI.
[4294760.811000] cs: IO port probe 0x100-0x4ff: excluding 0x4d0-0x4d7
[4294760.812000] cs: IO port probe 0x100-0x4ff: excluding 0x4d0-0x4d7
[4294760.814000] cs: IO port probe 0xc00-0xcf7: clean.
[4294760.814000] cs: IO port probe 0xc00-0xcf7: clean.
[4294760.815000] cs: IO port probe 0xa00-0xaff: clean.
[4294760.815000] cs: IO port probe 0xa00-0xaff: clean.
[4294847.140000] Bluetooth: Core ver 2.7
[4294847.140000] NET: Registered protocol family 31
[4294847.140000] Bluetooth: HCI device and connection manager initialized
[4294847.140000] Bluetooth: HCI socket layer initialized

toshset -fan high
fan: high

lsmod
Module Size Used by
bluetooth 43012 0
pcmcia 24584 4
video 16004 0
toshiba_acpi 10940 0
tc1100_wmi 6916 0
sony_acpi 5516 0
pcc_acpi 11392 0
hotkey 9508 0
dev_acpi 11396 0
i2c_acpi_ec 5760 0
button 6672 0
battery 9604 0
container 4608 0
ac 4996 0
ipv6 217408 10
af_packet 20232 2
floppy 52692 0
rtc 11832 0
pcspkr 3652 0
ath_pci 69148 0
ath_rate_sample 14344 1 ath_pci
wlan 120988 3 ath_pci,ath_rate_sample
ath_hal 148432 3 ath_pci,ath_rate_sample
snd_ymfpci 56384 1
gameport 14472 1 snd_ymfpci
snd_ac97_codec 72188 1 snd_ymfpci
snd_pcm_oss 46368 0
snd_mixer_oss 16128 1 snd_pcm_oss
snd_pcm 78344 3 snd_ymfpci,snd_ac97_codec,snd_pcm_oss
snd_opl3_lib 9856 1 snd_ymfpci
snd_timer 21764 3 snd_ymfpci,snd_pcm,snd_opl3_lib
snd_hwdep 8608 1 snd_opl3_lib
snd_page_alloc 10120 2 snd_ymfpci,snd_pcm
snd_mpu401_uart 6784 1 snd_ymfpci
snd_rawmidi 22816 1 snd_mpu401_uart
snd_seq_device 8204 2 snd_opl3_lib,snd_rawmidi
snd 48644 13 snd_ymfpci,snd_ac97_codec,snd_pcm_oss,snd_mixer_os s,snd_pcm,snd_opl3_lib,snd_timer,snd_hwdep,snd_mpu 401_uart,snd_rawmidi,snd_seq_device
soundcore 9184 1 snd
yenta_socket 22540 3
rsrc_nonstatic 12032 1 yenta_socket
pcmcia_core 44932 3 pcmcia,yenta_socket,rsrc_nonstatic
donauboe 14720 0
irda 159804 1 donauboe
crc_ccitt 2176 2 donauboe,irda
pci_hotplug 24628 0
intel_agp 21276 1
agpgart 32328 1 intel_agp
dm_mod 50364 1
i2c_isa 2176 0
i2c_viapro 7696 0
tsdev 7616 0
eeprom 7184 0
adm1021 12720 0
i2c_sensor 3456 2 eeprom,adm1021
evdev 9088 0
i2c_piix4 8336 0
i2c_core 19728 7 i2c_acpi_ec,i2c_isa,i2c_viapro,eeprom,adm1021,i2c_ sensor,i2c_piix4
psmouse 26116 0
mousedev 10912 1
parport_pc 31812 1
lp 11460 0
parport 32072 2 parport_pc,lp
md 40656 0
ext3 115976 1
jbd 48536 1 ext3
thermal 13192 0
processor 23100 1 thermal
fan 4740 0
uhci_hcd 28048 0
usbcore 104316 2 uhci_hcd
ide_cd 36996 0
cdrom 33952 1 ide_cd
ide_disk 16128 3
ide_generic 1664 0
piix 9476 1
ide_core 125268 4 ide_cd,ide_disk,ide_generic,piix
unix 24624 476
vesafb 8088 0
capability 5000 0
commoncap 6784 1 capability
vga16fb 12232 1
vgastate 8320 1 vga16fb
softcursor 2432 2 vesafb,vga16fb
cfbimgblt 2944 2 vesafb,vga16fb
cfbfillrect 3840 2 vesafb,vga16fb
cfbcopyarea 4480 2 vesafb,vga16fb
fbcon 34176 72
tileblit 2560 1 fbcon
font 8448 1 fbcon
bitblit 5248 1 fbcon

Let me know if you need more info.

---

### Post by Hydraulix on 2006-05-10
Also I updated the BIOS and I'm not seeing anything there to control the fan.:(

---

### Post by Tom Tiger on 2006-05-10
On the Tecra 8100 there is a fan control in the BIOS, it is under powermanagement (usersettings) or something like that in the first column, but you can't adjust much there,  usually it is set  maximum performance, performance and battery optimized.  With the first setting it is often on, the last it is the least on.

Hope this helps, I haven't seen an 8100 in at least two years for service, so I'm doing this from memory ;)

---

### Post by Hydraulix on 2006-05-11
I've tried all three settings and still nothing. I did notice that fan -d works. Is there a way I can have fan -d run at start up?

---

