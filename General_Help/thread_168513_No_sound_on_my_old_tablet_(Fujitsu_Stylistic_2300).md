---
title: "No sound on my old tablet (Fujitsu Stylistic 2300)"
date: 2006-04-30
forum: General Help
---

### Post by lo_mein_dreams on 2006-04-30
Note: (I click sound and video help and it sends me to warty live cd... so sorry if this is the wrong place
I can't get my sound to work on my Fujitsu Stylistic 2300 (233mhz tablet, relatively old)
I know that it isn't muted. I am running Xubuntu with Dapper Drake (using fluxbox instead of xfce), and to get an os on this hard drive I had to install onto the drive while it was connected to my desktop, so I am running into some issues.

**_lspci -v_**
0000:00:00.0 Host bridge: Intel Corporation 430TX - 82439TX MTXC (rev 01)
        Flags: bus master, medium devsel, latency 32

0000:00:01.0 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ISA (rev 02)
        Flags: bus master, medium devsel, latency 0

0000:00:01.1 IDE interface: Intel Corporation 82371AB/EB/MB PIIX4 IDE (rev 01) (prog-if 80 [Master])
        Flags: bus master, medium devsel, latency 64
        I/O ports at f4f0 [size=16]

0000:00:01.2 USB Controller: Intel Corporation 82371AB/EB/MB PIIX4 USB (rev 01) (prog-if 00 [UHCI])
        Flags: bus master, medium devsel, latency 64, IRQ 9
        I/O ports at f4c0 [size=32]

0000:00:01.3 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ACPI (rev 02)
        Flags: medium devsel, IRQ 9

0000:00:10.0 Communication controller: Agere Systems 56k WinModem (rev 01)
        Subsystem: Fujitsu Limited. LB LT Modem V.90 56k
        Flags: medium devsel, IRQ 9
        Memory at fedffc00 (32-bit, non-prefetchable) [size=256]
        I/O ports at f4e8 [size=8]
        I/O ports at f000 [size=256]
        Capabilities: <available only to root>

0000:00:13.0 CardBus bridge: Texas Instruments PCI1221
        Subsystem: Fujitsu Limited.: Unknown device 1036
        Flags: bus master, medium devsel, latency 168, IRQ 9
        Memory at 18000000 (32-bit, non-prefetchable) [size=4K]
        Bus: primary=00, secondary=01, subordinate=04, sec-latency=176
        Memory window 0: 10000000-11fff000 (prefetchable)
        Memory window 1: 12000000-13fff000
        I/O window 0: 00001000-000010ff
        I/O window 1: 00001400-000014ff
        16-bit legacy interface ports at 0001

0000:00:13.1 CardBus bridge: Texas Instruments PCI1221
        Subsystem: Fujitsu Limited.: Unknown device 1036
        Flags: bus master, medium devsel, latency 168, IRQ 9
        Memory at 18001000 (32-bit, non-prefetchable) [size=4K]
        Bus: primary=00, secondary=05, subordinate=08, sec-latency=176
        Memory window 0: 14000000-15fff000 (prefetchable)
        Memory window 1: 16000000-17fff000
        I/O window 0: 00001800-000018ff
        I/O window 1: 00001c00-00001cff
        16-bit legacy interface ports at 0001

0000:00:14.0 VGA compatible controller: Neomagic Corporation NM2160 [MagicGraph 128XD] (rev 01) (prog-if 00 [VGA])
        Subsystem: Fujitsu Limited. MagicGraph 128XD
        Flags: bus master, medium devsel, latency 128
        Memory at fd000000 (32-bit, prefetchable) [size=16M]
        Memory at fea00000 (32-bit, non-prefetchable) [size=2M]
        Memory at fec00000 (32-bit, non-prefetchable) [size=1M]
[B]
_dmesg_[/B]
[4294667.296000] Linux version 2.6.15-21-386 (buildd@rothera) (gcc version 4.0.3 (Ubuntu 4.0.3-1ubuntu5)) #1 PREEMPT Fri Apr 21 16:43:33 UTC 2006
[4294667.296000] BIOS-provided physical RAM map:
[4294667.296000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[4294667.296000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[4294667.296000]  BIOS-e820: 00000000000f0400 - 0000000000100000 (reserved)
[4294667.296000]  BIOS-e820: 0000000000100000 - 0000000005febc00 (usable)
[4294667.296000]  BIOS-e820: 0000000005febc00 - 0000000005ff0000 (ACPI data)
[4294667.296000]  BIOS-e820: 0000000005ff0000 - 0000000006000000 (ACPI NVS)
[4294667.296000]  BIOS-e820: 00000000ffff0400 - 0000000100000000 (reserved)
[4294667.296000] 0MB HIGHMEM available.
[4294667.296000] 95MB LOWMEM available.
[4294667.296000] On node 0 totalpages: 24555
[4294667.296000]   DMA zone: 4096 pages, LIFO batch:0
[4294667.296000]   DMA32 zone: 0 pages, LIFO batch:0
[4294667.296000]   Normal zone: 20459 pages, LIFO batch:3
[4294667.296000]   HighMem zone: 0 pages, LIFO batch:0
[4294667.296000] DMI 2.1 present.
[4294667.296000] ACPI: RSDP (v000 PTLTD                                 ) @ 0x000f6f00
[4294667.296000] ACPI: RSDT (v001 FUJ    SPRINT   0x00001000 PTL  0x01000000) @ 0x05febc1a
[4294667.296000] ACPI: FADT (v001 FUJ    SPRINT   0x00001000 PTL  0x000f4240) @ 0x05feff8c
[4294667.296000] ACPI: DSDT (v001    FUJ   SPRINT 0x00001080 MSFT 0x01000004) @ 0x00000000
[4294667.296000] ACPI: BIOS age (1998) fails cutoff (2000), acpi=force is required to enable ACPI
[4294667.296000] ACPI: Disabling ACPI support
[4294667.296000] Allocating PCI resources starting at 10000000 (gap: 06000000:f9ff0400)
[4294667.296000] Built 1 zonelists
[4294667.296000] Kernel command line: root=/dev/hda1 ro quiet splash
[4294667.296000] No local APIC present or hardware disabled
[4294667.296000] mapped APIC to ffffd000 (010c1000)
[4294667.296000] Initializing CPU#0
[4294667.296000] PID hash table entries: 512 (order: 9, 8192 bytes)
[    0.000000] Detected 233.921 MHz processor.
[   24.290486] Using tsc for high-res timesource
[   24.291740] Console: colour VGA+ 80x25
[   24.293782] Dentry cache hash table entries: 16384 (order: 4, 65536 bytes)
[   24.294944] Inode-cache hash table entries: 8192 (order: 3, 32768 bytes)
[   24.317801] Memory: 87212k/98220k available (1974k kernel code, 10556k reserved, 604k data, 288k init, 0k highmem)
[   24.317847] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   24.378269] Calibrating delay using timer specific routine.. 468.21 BogoMIPS (lpj=234108)
[   24.378580] Security Framework v1.0.0 initialized
[   24.378645] SELinux:  Disabled at boot.
[   24.378766] Mount-cache hash table entries: 512
[   24.379798] CPU: After generic identify, caps: 008001bf 00000000 00000000 00000000 00000000 00000000 00000000
[   24.379866] CPU: After vendor identify, caps: 008001bf 00000000 00000000 00000000 00000000 00000000 00000000
[   24.379924] Intel Pentium with F0 0F bug - workaround enabled.
[   24.379954] CPU: After all inits, caps: 008001bf 00000000 00000000 00000000 00000000 00000000 00000000
[   24.380110] mtrr: v2.0 (20020519)
[   24.380127] CPU: Intel Mobile Pentium MMX stepping 01
[   24.380166] Checking 'hlt' instruction... OK.
[   24.384513] checking if image is initramfs... it is
[   31.111723] Freeing initrd memory: 6392k freed
[   31.192688] NET: Registered protocol family 16
[   31.193076] EISA bus registered
[   31.194455] PCI: PCI BIOS revision 2.10 entry at 0xfda20, last bus=2
[   31.194506] PCI: Using configuration type 1
[   31.196432] ACPI: Subsystem revision 20051216
[   31.196458] ACPI: Interpreter disabled.
[   31.196485] Linux Plug and Play Support v0.97 (c) Adam Belay
[   31.196564] pnp: PnP ACPI: disabled
[   31.196593] PnPBIOS: Scanning system for PnP BIOS support...
[   31.196975] PnPBIOS: Found PnP BIOS installation structure at 0xc00f6eb0
[   31.197019] PnPBIOS: PnP BIOS version 1.0, entry 0xf0000:0xb777, dseg 0x400
[   31.296179] PnPBIOS: 19 nodes reported by PnP BIOS; 19 recorded by driver
[   31.296325] PCI: Probing PCI hardware
[   31.296357] PCI: Probing PCI hardware (bus 00)
[   31.297365] PCI quirk: region ff00-ff3f claimed by PIIX4 ACPI
[   31.297401] PCI quirk: region ff80-ff8f claimed by PIIX4 SMB
[   31.297434] PIIX4 devres B PIO at fd60-fd67
[   31.297458] PIIX4 devres C PIO at fce8-fcef
[   31.297483] PIIX4 devres I PIO at 0800-0807
[   31.297506] PIIX4 devres J PIO at 0388-038b
[   31.297901] Boot video device is 0000:00:14.0
[   31.303229] PCI: Using IRQ router PIIX/ICH [8086/7110] at 0000:00:01.0
[   31.306103] pnp: 00:01: ioport range 0x4d0-0x4d1 has been reserved
[   31.306180] pnp: 00:01: ioport range 0xff00-0xff3f has been reserved
[   31.306215] pnp: 00:01: ioport range 0xff80-0xff8f has been reserved
[   31.306266] pnp: 00:02: ioport range 0xf800-0xf87f has been reserved
[   31.306300] pnp: 00:02: ioport range 0xf880-0xf8ff has been reserved
[   31.306334] pnp: 00:02: ioport range 0xfd60-0xfd67 has been reserved
[   31.309061] PCI: Ignore bogus resource 6 [0:0] of 0000:00:14.0
[   31.309153] PCI: Bus 1, cardbus bridge: 0000:00:13.0
[   31.309180]   IO window: 00001000-000010ff
[   31.309206]   IO window: 00001400-000014ff
[   31.309233]   PREFETCH window: 10000000-11ffffff
[   31.309261]   MEM window: 12000000-13ffffff
[   31.309285] PCI: Bus 5, cardbus bridge: 0000:00:13.1
[   31.309310]   IO window: 00001800-000018ff
[   31.309335]   IO window: 00001c00-00001cff
[   31.309361]   PREFETCH window: 14000000-15ffffff
[   31.309388]   MEM window: 16000000-17ffffff
[   31.309441] PCI: Found IRQ 9 for device 0000:00:13.0
[   31.309518] PCI: Found IRQ 9 for device 0000:00:13.1
[   31.315500] audit: initializing netlink socket (disabled)
[   31.315587] audit(1146407205.255:1): initialized
[   31.316613] VFS: Disk quotas dquot_6.5.1
[   31.316855] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   31.317311] Initializing Cryptographic API
[   31.317353] io scheduler noop registered
[   31.317417] io scheduler anticipatory registered
[   31.317472] io scheduler deadline registered
[   31.317548] io scheduler cfq registered
[   31.317577] Limiting direct PCI/PCI transfers.
[   31.319275] isapnp: Scanning for PnP cards...
[   31.675582] isapnp: No Plug & Play device found
[   31.937975] PNP: PS/2 Controller [PNP0303,PNP0f13] at 0x60,0x64 irq 1,12
[   31.942758] serio: i8042 AUX port at 0x60,0x64 irq 12
[   31.943363] serio: i8042 KBD port at 0x60,0x64 irq 1
[   31.943973] Serial: 8250/16550 driver $Revision: 1.90 $ 48 ports, IRQ sharing enabled
[   31.944649] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   31.975242] 00:11: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   31.982006] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   31.982663] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[   31.982700] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[   31.983894] mice: PS/2 mouse device common for all mice
[   31.985564] EISA: Probing bus 0 at eisa.0
[   31.985615] Cannot allocate resource for EISA slot 1
[   31.985713] EISA: Detected 0 cards.
[   31.986010] NET: Registered protocol family 2
[   31.994721] IP route cache hash table entries: 1024 (order: 0, 4096 bytes)
[   31.996136] TCP established hash table entries: 4096 (order: 2, 16384 bytes)
[   31.996396] TCP bind hash table entries: 4096 (order: 2, 16384 bytes)
[   31.996617] TCP: Hash tables configured (established 4096 bind 4096)
[   31.996646] TCP reno registered
[   31.997453] TCP bic registered
[   31.997510] NET: Registered protocol family 1
[   31.997564] NET: Registered protocol family 8
[   31.997586] NET: Registered protocol family 20
[   31.997737] Using IPI Shortcut mode
[   31.998041] Freeing unused kernel memory: 288k freed
[   32.018003] input: AT Translated Set 2 keyboard as /class/input/input0
[   32.792233] vga16fb: initializing
[   32.792276] vga16fb: mapped to 0xc00a0000
[   32.924007] Console: switching to colour frame buffer device 80x25
[   32.924058] fb0: VGA16 VGA frame buffer device
[   34.180978] Capability LSM initialized
[   39.365316] PIIX4: IDE controller at PCI slot 0000:00:01.1
[   39.365397] PIIX4: chipset revision 1
[   39.365418] PIIX4: not 100% native mode: will probe irqs later
[   39.365503]     ide0: BM-DMA at 0xf4f0-0xf4f7, BIOS settings: hda:DMA, hdb:pio
[   39.365595] Probing IDE interface ide0...
[   39.629420] hda: TOSHIBA MK8025GAS, ATA DISK drive
[   40.241325] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[   40.303796] hda: max request size: 128KiB
[   40.539900] hda: 156301488 sectors (80026 MB), CHS=65535/16/63, UDMA(33)
[   40.540025] hda: cache flushes supported
[   40.541238]  hda: hda1 hda2 < hda5 >
[   41.157219] usbcore: registered new driver usbfs
[   41.160376] usbcore: registered new driver hub
[   41.176807] USB Universal Host Controller Interface driver v2.3
[   41.179855] PCI: Enabling device 0000:00:01.2 (0000 -> 0001)
[   41.179900] PCI: Found IRQ 9 for device 0000:00:01.2
[   41.179987] uhci_hcd 0000:00:01.2: UHCI Host Controller
[   41.182661] uhci_hcd 0000:00:01.2: new USB bus registered, assigned bus number 1
[   41.182731] uhci_hcd 0000:00:01.2: irq 9, io base 0x0000f4c0
[   41.185964] hub 1-0:1.0: USB hub found
[   41.186103] hub 1-0:1.0: 2 ports detected
[   41.784205] Probing IDE interface ide1...
[   42.665456] EXT3-fs: INFO: recovery required on readonly filesystem.
[   42.665497] EXT3-fs: write access will be enabled during recovery.
[   43.659301] EXT3-fs: recovery complete.
[   43.659447] kjournald starting.  Commit interval 5 seconds
[   43.661155] EXT3-fs: mounted filesystem with ordered data mode.
[   69.876011] PCI: Found IRQ 9 for device 0000:00:13.0
[   69.876115] Yenta: CardBus bridge found at 0000:00:13.0 [10cf:1036]
[   69.876162] Yenta: Enabling burst memory read transactions
[   69.876189] Yenta: Using CSCINT to route CSC interrupts to PCI
[   69.876214] Yenta: Routing CardBus interrupts to PCI
[   69.876244] Yenta TI: socket 0000:00:13.0, mfunc 0x01cc1d22, devctl 0x46
[   70.015662] ltmodem: module license 'Proprietary' taints kernel.
[   70.024575] Loading Lucent Modem Controller driver version 8.26-alk-8
[   70.030196] PCI: Enabling device 0000:00:10.0 (0000 -> 0003)
[   70.030246] PCI: Found IRQ 9 for device 0000:00:10.0
[   70.030329] Detected Parameters Irq=9 BaseAddress=0xf000 ComAddress=0xf4e8
[   70.030463] ttyLTM0 at I/O 0xf000 (irq = 9) is a Lucent/Agere Modem
[   70.058256] piix4_smbus 0000:00:01.3: Found 0000:00:01.3 device
[   70.109347] Yenta: ISA IRQ mask 0x0c98, PCI irq 9
[   70.109406] Socket status: 30000010
[   70.212022] PCI: Found IRQ 9 for device 0000:00:13.1
[   70.212173] Yenta: CardBus bridge found at 0000:00:13.1 [10cf:1036]
[   70.212224] Yenta: Using CSCINT to route CSC interrupts to PCI
[   70.212249] Yenta: Routing CardBus interrupts to PCI
[   70.212281] Yenta TI: socket 0000:00:13.1, mfunc 0x01cc1d22, devctl 0x46
[   70.436080] Yenta: ISA IRQ mask 0x0c98, PCI irq 9
[   70.436116] Socket status: 30000006
[   70.854047] pccard: PCMCIA card inserted into slot 0
[   72.448059] input: PC Speaker as /class/input/input1
[   76.885562] Real Time Clock Driver v1.12
[   77.103803] input: PS/2 Generic Mouse as /class/input/input2
[   77.472365] Floppy drive(s): fd0 is 1.44M
[   77.494037] parport: PnPBIOS parport detected.
[   77.494138] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE,EPP]
[   77.502809] FDC 0 is a post-1991 82077
[   77.569816] cs: IO port probe 0x100-0x3af: excluding 0x220-0x22f 0x388-0x38f
[   77.571129] cs: IO port probe 0x3e0-0x4ff: clean.
[   77.571945] cs: IO port probe 0x820-0x8ff: clean.
[   77.572711] cs: IO port probe 0xc00-0xcf7: clean.
[   77.574829] cs: IO port probe 0xa00-0xaff: clean.
[   77.575644] cs: memory probe 0xa0000000-0xa0ffffff: clean.
[   77.592134] pcmcia: registering new device pcmcia0.0
[   77.609773] cs: IO port probe 0x100-0x3af: excluding 0x220-0x22f 0x388-0x38f
[   77.611084] cs: IO port probe 0x3e0-0x4ff: clean.
[   77.611898] cs: IO port probe 0x820-0x8ff: clean.
[   77.612671] cs: IO port probe 0xc00-0xcf7: clean.
[   77.614792] cs: IO port probe 0xa00-0xaff: clean.
[   78.154875] ts: Compaq touchscreen protocol output
[   79.076286] eth0: Xircom: port 0x300, irq 3, hwaddr 00:10:A4:C3:DB:6B
[   81.400847] Adding 1510068k swap on /dev/hda5.  Priority:-1 extents:1 across:1510068k
[   81.740199] EXT3 FS on hda1, internal journal
[   82.839108] md: md driver 0.90.3 MAX_MD_DEVS=256, MD_SB_DISKS=27
[   82.839148] md: bitmap version 4.39
[   84.407236] eth1: autonegotiation failed; using 10mbs
[   84.407278] eth1: MII selected
[   84.427933] eth1: media 10BaseT, silicon revision 4
[   84.755541] device-mapper: 4.4.0-ioctl (2005-01-12) initialised: [email]dm-devel@redhat.com[/email]
[   85.756071] NET: Registered protocol family 17
[  141.408687] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[ 4167.080422] usb 1-1: new low speed USB device using uhci_hcd and address 2
[ 4169.603362] usbcore: registered new driver hiddev
[ 4169.637917] input: Logitech USB Trackball as /class/input/input3
[ 4169.641548] input: USB HID v1.10 Mouse [Logitech USB Trackball] on usb-0000:00:01.2-1
[ 4169.641648] usbcore: registered new driver usbhid
[ 4169.641676] drivers/usb/input/hid-core.c: v2.6:USB HID core driver
[ 4179.092235] usb 1-1: USB disconnect, address 2
[ 4182.866183] usb 1-1: new low speed USB device using uhci_hcd and address 3
[ 4183.058296] input: Logitech USB Trackball as /class/input/input4
[ 4183.058753] input: USB HID v1.10 Mouse [Logitech USB Trackball] on usb-0000:00:01.2-1
[ 4555.439580] usb 1-1: USB disconnect, address 3
[ 4689.560400] usb 1-1: new low speed USB device using uhci_hcd and address 4
[ 4689.751951] input: Logitech USB Trackball as /class/input/input5
[ 4689.752463] input: USB HID v1.10 Mouse [Logitech USB Trackball] on usb-0000:00:01.2-1
[ 4695.075591] usb 1-1: USB disconnect, address 4
[ 4764.756107] usb 1-1: new low speed USB device using uhci_hcd and address 5
[ 4764.948270] input: Logitech USB Trackball as /class/input/input6
[ 4764.948756] input: USB HID v1.10 Mouse [Logitech USB Trackball] on usb-0000:00:01.2-1
[ 5326.084367] NET: Registered protocol family 10
[ 5326.085645] lo: Disabled Privacy Extensions
[ 5326.087398] IPv6 over IPv4 tunneling driver
[ 5336.192426] eth1: no IPv6 routers present
[ 5479.402720] usb 1-1: USB disconnect, address 5
[ 5741.055903] usb 1-1: new low speed USB device using uhci_hcd and address 6
[ 5741.247809] input: Logitech USB Trackball as /class/input/input7
[ 5741.248282] input: USB HID v1.10 Mouse [Logitech USB Trackball] on usb-0000:00:01.2-1
[ 5752.068224] usb 1-1: USB disconnect, address 6
[ 5777.732716] usb 1-1: new low speed USB device using uhci_hcd and address 7
[ 5777.924954] input: Logitech USB Trackball as /class/input/input8
[ 5777.925437] input: USB HID v1.10 Mouse [Logitech USB Trackball] on usb-0000:00:01.2-1
[    8.578383] PCI: Found IRQ 9 for device 0000:00:01.2
[    8.584603] PCI: Found IRQ 9 for device 0000:00:10.0
[    8.585214] PCI: Found IRQ 9 for device 0000:00:13.0
[   11.206156] eth1: MII link partner: 41e1
[   11.206605] eth1: MII selected
[   11.227565] eth1: media 100BaseT, silicon revision 4
[   11.228135] PCI: Found IRQ 9 for device 0000:00:13.1
[   11.577456] usb 1-1: USB disconnect, address 7
[   14.954645] usb 1-1: new low speed USB device using uhci_hcd and address 8
[   15.146726] input: Logitech USB Trackball as /class/input/input9
[   15.147186] input: USB HID v1.10 Mouse [Logitech USB Trackball] on usb-0000:00:01.2-1
[  135.909500] usb 1-1: USB disconnect, address 8
[  581.724459] usb 1-1: new low speed USB device using uhci_hcd and address 9
[  581.918679] input: Logitech USB Trackball as /class/input/input10
[  581.919160] input: USB HID v1.10 Mouse [Logitech USB Trackball] on usb-0000:0

**_cat /proc/version_**
Linux version 2.6.15-21-386 (buildd@rothera) (gcc version 4.0.3 (Ubuntu 4.0.3-1ubuntu5)) #1 PREEMPT Fri Apr 21 16:43:33 UTC 2006


I know the sound works in windows... its not broken.

Also, if someone knows how to perminantly disable the system bell, that would be great too (my tablet detects the battery life incorrectly, and thinks that it is dead for 3 hours, beeping every 20 seconds.

---

### Post by lo_mein_dreams on 2006-05-02
please?

---

### Post by lawson23 on 2008-02-27
I can't help you but was wondering if you ever found an answer to this??

I'm also interested in doing this with my 2300.  I would like to get Win98 off of this box.

Also was sound your only issue??  If so this doesn't bother me then.  My main concern would be the display, the pen and keyboard working properly.

---

### Post by im_an_alien on 2008-06-21
Sorry to bump this, but I have a stylistic 2300, and I've been thinking about putting linux on it.  How well does the digitizer work?  If it doesn't work (well) I'm gonna stick with windows.  Also, is there any software for handwriting recognition?  I'd like to keep that.

---

