---
title: "Sound and hardware probs"
date: 2006-05-19
forum: General Help
---

### Post by Symo on 2006-05-19
I've got some sound problems: can't get any sound with audio CD, mp3 files or anything. Tried doing tests in multimedia systems selector and all I get back is "Failed to construct test pipeline for...". When trying to play an audio CD in Totem it tells me that "there is no audio output available", and in juicer that, "dev/dsp does not exist". When I check in the device manager my CD player is listed as dev/hdc though. 

I've de-enabled the sound server startup box in sound preferences. Tried killall esd (with and without sudo) and this is the line I get back:
> esd: no process killed

I also used easy ubuntu to get the right codecs and whatnot but as yet no joy.

From checking out replies to other posts with sound issues I see that it's often to do with hardware not detected or configured properly and I've got a feeling that it's also the case here.

Anyway, here's what i get with aplay -l:
> **** List of PLAYBACK Hardware Devices ****
aplay: device_list:238: snd_ctl_pcm_next_device

And with cat /proc/version:
 > Linux version 2.6.12-10-amd64-generic (buildd@king) (gcc version 3.4.5 20050809 (prerelease) (Ubuntu 3.4.4-6ubuntu8.1)) #1 Fri Apr 28 13:18:42 UTC 2006


With lspci:
> 0000:00:00.0 RAM memory: nVidia Corporation: Unknown device 02f1 (rev a2)
0000:00:00.2 RAM memory: nVidia Corporation: Unknown device 02fe (rev a2)
0000:00:00.3 RAM memory: nVidia Corporation: Unknown device 02f8 (rev a2)
0000:00:00.4 RAM memory: nVidia Corporation: Unknown device 02f9 (rev a2)
0000:00:00.5 RAM memory: nVidia Corporation: Unknown device 02ff (rev a2)
0000:00:00.6 RAM memory: nVidia Corporation: Unknown device 027f (rev a2)
0000:00:00.7 RAM memory: nVidia Corporation: Unknown device 027e (rev a2)
0000:00:02.0 PCI bridge: nVidia Corporation: Unknown device 02fc (rev a1)
0000:00:03.0 PCI bridge: nVidia Corporation: Unknown device 02fd (rev a1)
0000:00:04.0 PCI bridge: nVidia Corporation: Unknown device 02fb (rev a1)
0000:00:05.0 VGA compatible controller: nVidia Corporation: Unknown device 0242 (rev a2)
0000:00:09.0 RAM memory: nVidia Corporation: Unknown device 0270 (rev a2)
0000:00:0a.0 ISA bridge: nVidia Corporation: Unknown device 0261 (rev a2)
0000:00:0a.1 SMBus: nVidia Corporation: Unknown device 0264 (rev a2)
0000:00:0b.0 USB Controller: nVidia Corporation: Unknown device 026d (rev a2)
0000:00:0b.1 USB Controller: nVidia Corporation: Unknown device 026e (rev a2)
0000:00:0d.0 IDE interface: nVidia Corporation: Unknown device 0265 (rev a1)
0000:00:0e.0 IDE interface: nVidia Corporation: Unknown device 0266 (rev a1)
0000:00:10.0 PCI bridge: nVidia Corporation: Unknown device 026f (rev a2)
0000:00:10.2 Multimedia audio controller: nVidia Corporation: Unknown device 026b (rev a2)
0000:00:14.0 Bridge: nVidia Corporation: Unknown device 0269 (rev a1)
0000:00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 NorthBridge
0000:00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 NorthBridge
0000:00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 NorthBridge
0000:00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 NorthBridge

Lot of unknown devices there...

And with dmesg:
> 0.000000] Checking aperture...
[    0.000000] CPU 0: aperture @ 80a0000000 size 32 MB
[    0.000000] Aperture from northbridge cpu 0 too small (32 MB)
[    0.000000] No AGP bridge found
[    0.000000] Built 1 zonelists
[    0.000000] Kernel command line: root=/dev/mapper/Ubuntu-root ro quiet splash[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 131072 bytes)
[    0.000000] time.c: Using 3.579545 MHz PM timer.
[    0.000000] time.c: Detected 2009.189 MHz processor.
[   10.216842] time.c: Using PIT/TSC based timekeeping.
[   10.221714] Console: colour VGA+ 80x25
[   10.222675] Dentry cache hash table entries: 131072 (order: 8, 1048576 bytes)[   10.224021] Inode-cache hash table entries: 65536 (order: 7, 524288 bytes)
[   10.242168] Memory: 958256k/982720k available (1620k kernel code, 23692k reserved, 997k data, 136k init)
[   10.242209] Calibrating delay loop... 3964.92 BogoMIPS (lpj=1982464)
[   10.263779] Security Framework v1.0.0 initialized
[   10.263783] SELinux:  Disabled at boot.
[   10.263792] Mount-cache hash table entries: 256
[   10.263860] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)[   10.263863] CPU: L2 Cache: 256K (64 bytes/line)
[   10.263867] CPU: AMD Sempron(tm) Processor 3400+ stepping 02
[   10.263954] checking if image is initramfs... it is
[   10.619659] ACPI: Looking for DSDT in initrd... not found!
[   10.701727]  not found!
[   10.723270] Using local APIC timer interrupts.
[   10.772980] Detected 12.557 MHz APIC timer.
[   10.772991] testing NMI watchdog ... OK.
[   10.783049] NET: Registered protocol family 16
[   10.783071] ACPI: bus type pci registered
[   10.783136] PCI: Using configuration type 1
[   10.783139] mtrr: v2.0 (20020519)
[   10.783402] ACPI: Subsystem revision 20050729
[   10.791416] ACPI: Interpreter enabled
[   10.791420] ACPI: Using IOAPIC for interrupt routing
[   10.791852] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   10.791855] PCI: Probing PCI hardware (bus 00)
[   10.791875] ACPI: Assume root bridge [\_SB_.PCI0] segment is 0
[   10.796002] Boot video device is 0000:00:05.0
[   10.796628] PCI: Transparent bridge - 0000:00:10.0
[   10.812660] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   10.813090] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P8._PRT]
[   10.813453] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P9._PRT]
[   10.813816] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0PA._PRT]
[   10.820219] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P1._PRT]
[   10.821166] ACPI: PCI Interrupt Link [LNKA] (IRQs 16 17 18 19) *0, disabled.
[   10.821606] ACPI: PCI Interrupt Link [LNKB] (IRQs 16 17 18 19) *0, disabled.
[   10.822053] ACPI: PCI Interrupt Link [LNKC] (IRQs 16 17 18 19) *0, disabled.
[   10.822494] ACPI: PCI Interrupt Link [LNKD] (IRQs 16 17 18 19) *0, disabled.
[   10.822940] ACPI: PCI Interrupt Link [LNEA] (IRQs 16 17 18 19) *0, disabled.
[   10.823378] ACPI: PCI Interrupt Link [LNEB] (IRQs 16 17 18 19) *0, disabled.
[   10.823816] ACPI: PCI Interrupt Link [LNEC] (IRQs 16 17 18 19) *11
[   10.824261] ACPI: PCI Interrupt Link [LNED] (IRQs 16 17 18 19) *0, disabled.
[   10.824699] ACPI: PCI Interrupt Link [LUB0] (IRQs 20 21 22 23) *11
[   10.825143] ACPI: PCI Interrupt Link [LUB2] (IRQs 20 21 22 23) *11
[   10.825586] ACPI: PCI Interrupt Link [LMAC] (IRQs 20 21 22 23) *11
[   10.826035] ACPI: PCI Interrupt Link [LAZA] (IRQs 20 21 22 23) *0, disabled.
[   10.826477] ACPI: PCI Interrupt Link [LACI] (IRQs 20 21 22 23) *11
[   10.826919] ACPI: PCI Interrupt Link [LMC9] (IRQs 20 21 22 23) *0, disabled.
[   10.827367] ACPI: PCI Interrupt Link [LSMB] (IRQs 20 21 22 23) *11
[   10.827805] ACPI: PCI Interrupt Link [LPMU] (IRQs 20 21 22 23) *11
[   10.828251] ACPI: PCI Interrupt Link [LSA0] (IRQs 20 21 22 23) *10
[   10.828692] ACPI: PCI Interrupt Link [LSA1] (IRQs 20 21 22 23) *0, disabled.
[   10.829206] ACPI: PCI Interrupt Link [LATA] (IRQs 20 21 22 23) *0, disabled.
[   10.829295] Linux Plug and Play Support v0.97 (c) Adam Belay
[   10.829302] pnp: PnP ACPI init
[   10.836451] pnp: PnP ACPI: found 16 devices
[   10.836531] usbcore: registered new driver usbfs
[   10.836550] usbcore: registered new driver hub
[   10.836580] PCI: Using ACPI for IRQ routing
[   10.836584] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   10.836665] PCI-DMA: Disabling IOMMU.
[   10.837919] pnp: 00:0d: ioport range 0x290-0x29f has been reserved
[   10.838178] IA32 emulation $Id: sys_ia32.c,v 1.32 2002/03/24 13:02:28 ak Exp $
[   10.838356] audit: initializing netlink socket (disabled)
[   10.838363] audit: initialized
[   10.838450] VFS: Disk quotas dquot_6.5.1
[   10.838465] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[   10.838489] devfs: 2004-01-31 Richard Gooch (rgooch@atnf.csiro.au)
[   10.838492] devfs: boot_options: 0x0
[   10.838515] Initializing Cryptographic API
[   10.838628] PCI: Setting latency timer of device 0000:00:02.0 to 64
[   10.838631] pcie_portdrv_probe->Dev[02fc:10de] has invalid IRQ. Check vendor BIOS
[   10.838653] assign_interrupt_mode Found MSI capability
[   10.838655] Allocate Port Service[pcie00]
[   10.838692] PCI: Setting latency timer of device 0000:00:03.0 to 64
[   10.838695] pcie_portdrv_probe->Dev[02fd:10de] has invalid IRQ. Check vendor BIOS
[   10.838714] assign_interrupt_mode Found MSI capability
[   10.838716] Allocate Port Service[pcie00]
[   10.838743] PCI: Setting latency timer of device 0000:00:04.0 to 64
[   10.838746] pcie_portdrv_probe->Dev[02fb:10de] has invalid IRQ. Check vendor BIOS
[   10.838765] assign_interrupt_mode Found MSI capability
[   10.838767] Allocate Port Service[pcie00]
[   10.853374] Linux agpgart interface v0.101 (c) Dave Jones
[   10.853447] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f03:PS2M] at 0x60,0x64 irq 1,12
[   10.855261] serio: i8042 AUX port at 0x60,0x64 irq 12
[   10.855425] serio: i8042 KBD port at 0x60,0x64 irq 1
[   10.855429] Serial: 8250/16550 driver $Revision: 1.90 $ 48 ports, IRQ sharing enabled
[   10.855554] ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   10.855692] ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[   10.857207] ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   10.857272] io scheduler noop registered
[   10.857285] io scheduler anticipatory registered
[   10.857289] io scheduler deadline registered
[   10.857296] io scheduler cfq registered
[   10.857572] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   10.857632] NET: Registered protocol family 2
[   10.866923] IP: routing cache hash table of 8192 buckets, 64Kbytes
[   10.867084] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[   10.867950] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[   10.868379] TCP: Hash tables configured (established 131072 bind 65536)
[   10.868450] NET: Registered protocol family 8
[   10.868453] NET: Registered protocol family 20
[   10.868588] ACPI wakeup devices:
[   10.868590] P0P8 P0P9 P0PA PS2K PS2M UAR1 NSMB USB0 USB2 NMAC P0P1 HDAC MC97
[   10.868596] ACPI: (supports S0 S1 S3 S4 S5)
[   10.868759] Freeing unused kernel memory: 136k freed
[   10.882585] input: AT Translated Set 2 keyboard on isa0060/serio0
[   10.883791] vga16fb: initializing
[   10.883795] vga16fb: mapped to 0xffff8100000a0000
[   11.073093] Console: switching to colour frame buffer device 80x30
[   11.073097] fb0: VGA16 VGA frame buffer device
[   12.190749] Capability LSM initialized
[   12.199421] NET: Registered protocol family 1
[   12.214007] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[   12.214017] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[   12.214020] ACPI: bus type ide registered
[   12.217295] SCSI subsystem initialized
[   12.218330] libata version 1.11 loaded.
[   12.220092] sata_nv version 0.6
[   12.220569] ACPI: PCI Interrupt Link [LSA0] enabled at IRQ 23
[   12.220578] ACPI: PCI Interrupt 0000:00:0e.0[A] -> Link [LSA0] -> GSI 23 (level, low) -> IRQ 23
[   12.220593] PCI: Setting latency timer of device 0000:00:0e.0 to 64
[   12.220636] ata1: SATA max UDMA/133 cmd 0xF80 ctl 0xF02 bmdma 0xE000 irq 23
[   12.220653] ata2: SATA max UDMA/133 cmd 0xE80 ctl 0xE02 bmdma 0xE008 irq 23
[   12.420588] ata1: no device found (phy stat 00000000)
[   12.420590] scsi0 : sata_nv
[   12.621292] ata2: no device found (phy stat 00000000)
[   12.621294] scsi1 : sata_nv
[   12.631695] NFORCE-MCP51: IDE controller at PCI slot 0000:00:0d.0
[   12.631715] NFORCE-MCP51: chipset revision 161
[   12.631717] NFORCE-MCP51: not 100% native mode: will probe irqs later
[   12.631724] NFORCE-MCP51: 0000:00:0d.0 (rev a1) UDMA133 controller
[   12.631733]     ide0: BM-DMA at 0xffa0-0xffa7, BIOS settings: hda:DMA, hdb:pio
[   12.631742]     ide1: BM-DMA at 0xffa8-0xffaf, BIOS settings: hdc:DMA, hdd:pio
[   12.631750] Probing IDE interface ide0...
[   12.894993] hda: SAMSUNG SP2014N, ATA DISK drive
[   13.543259] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[   13.543310] Probing IDE interface ide1...
[   14.214052] hdc: _NEC DVD_RW ND-3550A, ATAPI CD/DVD-ROM drive
[   14.825207] ide1 at 0x170-0x177,0x376 on irq 15
[   14.825291] Probing IDE interface ide2...
[   15.337294] Probing IDE interface ide3...
[   15.848542] Probing IDE interface ide4...
[   16.359789] Probing IDE interface ide5...
[   16.874435] hda: max request size: 1024KiB
[   16.876587] hda: 390721968 sectors (200049 MB) w/8192KiB Cache, CHS=24321/255/63, UDMA(100)
[   16.876768] hda: cache flushes supported
[   16.876822]  /dev/ide/host0/bus0/target0/lun0: p1 p2 < p5 >
[   16.889319] hdc: ATAPI 48X DVD-ROM DVD-R CD-R/RW drive, 2048kB Cache
[   16.889325] Uniform CD-ROM driver Revision: 3.20
[   17.250399] ohci_hcd: 2004 Nov 08 USB 1.1 'Open' Host Controller (OHCI) Driver (PCI)
[   17.250912] ACPI: PCI Interrupt Link [LUB0] enabled at IRQ 22
[   17.250921] ACPI: PCI Interrupt 0000:00:0b.0[A] -> Link [LUB0] -> GSI 22 (level, low) -> IRQ 22
[   17.250938] PCI: Setting latency timer of device 0000:00:0b.0 to 64
[   17.250942] ohci_hcd 0000:00:0b.0: nVidia Corporation MCP51 USB Controller
[   17.261608] ohci_hcd 0000:00:0b.0: new USB bus registered, assigned bus number 1
[   17.261620] ohci_hcd 0000:00:0b.0: irq 22, io mem 0xfebde000
[   17.314459] hub 1-0:1.0: USB hub found
[   17.314469] hub 1-0:1.0: 8 ports detected
[   17.322747] ACPI: PCI Interrupt Link [LUB2] enabled at IRQ 21
[   17.322757] ACPI: PCI Interrupt 0000:00:0b.1[B] -> Link [LUB2] -> GSI 21 (level, low) -> IRQ 21
[   17.322771] PCI: Setting latency timer of device 0000:00:0b.1 to 64
[   17.322774] ehci_hcd 0000:00:0b.1: nVidia Corporation MCP51 USB Controller
[   17.322782] ehci_hcd 0000:00:0b.1: debug port 1
[   17.322823] ehci_hcd 0000:00:0b.1: new USB bus registered, assigned bus number 2
[   17.322834] ehci_hcd 0000:00:0b.1: irq 21, io mem 0xfebdfc00
[   17.322861] PCI: cache line size of 64 is not supported by device 0000:00:0b.1
[   17.322864] ehci_hcd 0000:00:0b.1: park 0
[   17.322869] ehci_hcd 0000:00:0b.1: USB 2.0 initialized, EHCI 1.00, driver 10 Dec 2004
[   17.322941] hub 2-0:1.0: USB hub found
[   17.322947] hub 2-0:1.0: 8 ports detected
[   17.365103] forcedeth.c: Reverse Engineered nForce ethernet driver. Version 0.41.
[   17.365618] ACPI: PCI Interrupt Link [LMAC] enabled at IRQ 20
[   17.365627] ACPI: PCI Interrupt 0000:00:14.0[A] -> Link [LMAC] -> GSI 20 (level, low) -> IRQ 20
[   17.365634] PCI: Setting latency timer of device 0000:00:14.0 to 64
[   17.876762] eth0: forcedeth.c: subsystem: 01849:0269 bound to 0000:00:14.0
[   20.302841] ACPI: CPU0 (power states: C1[C1])
[   20.448516] device-mapper: 4.4.0-ioctl (2005-01-12) initialised: [email]dm-devel@redhat.com[/email]
[   20.480181] cdrom: open failed.
[   20.523520] Attempting manual resume
[   20.546317] swsusp: Suspend partition has wrong signature?
[   20.575534] kjournald starting.  Commit interval 5 seconds
[   20.575544] EXT3-fs: mounted filesystem with ordered data mode.
[   21.408377] md: md driver 0.90.1 MAX_MD_DEVS=256, MD_SB_DISKS=27
[   24.362449] Adding 2879480k swap on /dev/mapper/Ubuntu-swap_1.  Priority:-1 extents:1
[   24.633994] EXT3 FS on dm-0, internal journal
[   29.137108] parport: PnPBIOS parport detected.
[   29.137169] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
[   29.223564] lp0: using parport0 (interrupt-driven).
[   29.241546] mice: PS/2 mouse device common for all mice
[   29.275752] Real Time Clock Driver v1.12
[   29.301430] nvidia: module license 'NVIDIA' taints kernel.
[   29.344053] ACPI: PCI Interrupt Link [LNEC] enabled at IRQ 19
[   29.344063] ACPI: PCI Interrupt 0000:00:05.0[A] -> Link [LNEC] -> GSI 19 (level, low) -> IRQ 19
[   29.344072] PCI: Setting latency timer of device 0000:00:05.0 to 64
[   29.344227] NVRM: loading NVIDIA Linux x86_64 NVIDIA Kernel Module  1.0-7174  Tue Mar 22 06:45:40 PST 2005
[   29.551182] input: ImPS/2 Generic Wheel Mouse on isa0060/serio1
[   29.756953] ts: Compaq touchscreen protocol output
[   32.510128] cdrom: open failed.
[   33.037187] kjournald starting.  Commit interval 5 seconds
[   33.037287] EXT3 FS on hda1, internal journal
[   33.037292] EXT3-fs: mounted filesystem with ordered data mode.
[   34.895604] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   34.907664] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   36.846905] input: PC Speaker
[   36.901601] irda_init()
[   36.901618] NET: Registered protocol family 23
[   36.935686] Floppy drive(s): fd0 is 1.44M
[   36.954277] FDC 0 is a post-1991 82077
[   38.221721] NET: Registered protocol family 17
[   42.092619] NET: Registered protocol family 10
[   42.092722] Disabled Privacy Extensions on device ffffffff8035a840(lo)
[   42.093093] IPv6 over IPv4 tunneling driver
[   43.226274] ACPI: Power Button (FF) [PWRF]
[   43.226302] ACPI: Power Button (CM) [PWRB]
[   43.314641] ibm_acpi: ec object not found
[   48.408388] NVRM: RM/client version mismatch!!
[   48.408393] NVRM:    aborting to avoid catastrophe!
[   50.214202] powernow-k8: Found 1 AMD Athlon 64 / Opteron processors (version 1.40.4)
[   50.214525] powernow-k8:    0 : fid 0xc (2000 MHz), vid 0x6 (1400 mV)
[   50.214530] powernow-k8:    1 : fid 0xa (1800 MHz), vid 0x8 (1350 mV)
[   50.214534] powernow-k8:    2 : fid 0x2 (1000 MHz), vid 0xa (1300 mV)
[   50.214831] cpu_init done, current fid 0xc, vid 0x6
[   50.379253] Bluetooth: Core ver 2.7
[   50.379261] NET: Registered protocol family 31
[   50.379263] Bluetooth: HCI device and connection manager initialized
[   50.379274] Bluetooth: HCI socket layer initialized
[   50.397359] Bluetooth: L2CAP ver 2.7
[   50.397364] Bluetooth: L2CAP socket layer initialized
[   50.448094] Bluetooth: RFCOMM ver 1.5
[   50.448103] Bluetooth: RFCOMM socket layer initialized
[   50.448116] Bluetooth: RFCOMM TTY layer initialized
[   52.423401] NVRM: RM/client version mismatch!!
[   52.423406] NVRM:    aborting to avoid catastrophe!
[   52.556377] eth0: no IPv6 routers present
[   54.560836] NVRM: RM/client version mismatch!!
[   54.560841] NVRM:    aborting to avoid catastrophe!
[  131.043030] NVRM: RM/client version mismatch!!
[  131.043034] NVRM:    aborting to avoid catastrophe!
[  449.836411] NVRM: RM/client version mismatch!!
[  449.836415] NVRM:    aborting to avoid catastrophe!
[  452.268862] NVRM: RM/client version mismatch!!
[  452.268866] NVRM:    aborting to avoid catastrophe!
[  454.552630] NVRM: RM/client version mismatch!!
[  454.552634] NVRM:    aborting to avoid catastrophe!
[  659.817773] Warning: /proc/ide/hd?/settings interface is obsolete, and will be removed soon!

Those lines of, "aborting to avoid catastrophe!" don't fill me with confidence!

According to my motherboard installation guide my chipset is:
Northbridge: nVidia GeForce 6100
Southbridge: nVidia nForce 410 MCP
And my soundcard is: Realtek ALC850 7.1 channel AC'97 audio codec

So doctor, how does it look? Am I gonna make it?

---

### Post by Symo on 2006-05-19
Well, I think I may have come across the solution or, at least a part of the solution. My sound card is Realtek ALC850 7.1 channel AC'97 audio codec and apparently it needs alsa-driver-1.0.9b_26 to get it going. Since this driver isn't in the repositories I downloaded it but don't know how to install it. (I'm using Breezy so no inbuilt Debian package installer. I installed GDeb (twice) but it doesn't open so I think there might be something wrong with the package.) I considered installing the alsa driver via the terminal and following the instructions from the readme file but they weren't so clear and I don't want to make things worse.  It also said that I would need to compile the kernel with sound support - and I don't have a clue how to do anything like that.

Can anyone give me any pointers?

---

### Post by Sef on 2006-05-20
Have you downloaded the codecs?

[https://wiki.ubuntu.com/RestrictedFormats]("https://wiki.ubuntu.com/RestrictedFormats")

---

### Post by Symo on 2006-05-20
Yeah, I think so - but I did it through Easy Ubuntu.

---

