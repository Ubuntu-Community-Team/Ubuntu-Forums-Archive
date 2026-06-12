---
title: "Flaky boot Ubuntu 11.10 single boot laptop"
date: 2012-02-16
forum: General Help
---

### Post by Jolimont on 2012-02-16
Hello,

I'm brand new to Ubuntu and wanting to learn a lot more for a new job that requires Linux. Ubuntu seemed like a great place to start, so I took an old Compaq laptop and with my husband's help got it formated and got 11.10 installed, then wireless working, then wireless printer working. It wasn't super easy and I could not have gotten this far without his help. He's the kind of guy who thinks in command line and has decades of Unix experience (although none with Ubuntu in particular), so I was lucky. But I NEED to figure it out without his help, so I read and read and read, and nothing seems to address my issue. 

From the get-go the boot process has been flaky. Occasionally it'll boot right up, but mostly I have to boot in safe mode and even then it'll only boot correctly one every 10 tries. Other times I get the black screen for however long I'll let it sit there and have to hold the power button for 10 seconds to try again. I tried the memory test a couple of times it runs OK then tells me to press enter to continue on to safe mode. Hubby said it's getting stuck on some hardware bit but he doesn't know what. Help! What info do I need to give you?

Thanks!

---

### Post by arm-c on 2012-02-16
recommend that you improve your learning experience by starting with good hardware.  If you have a hardware issue, it is not a linux issue.

my recommendation is to take your computer and set up a dual boot system... Or if uncomfortable about that, instal, inside of windows with Wubi Installer.

---

### Post by aasdfasdfg on 2012-02-16
> **Jolimont said:**
> Hello,

I'm brand new to Ubuntu and wanting to learn a lot more for a new job that requires Linux. Ubuntu seemed like a great place to start, so I took an old Compaq laptop and with my husband's help got it formated and got 11.10 installed, then wireless working, then wireless printer working. It wasn't super easy and I could not have gotten this far without his help. He's the kind of guy who thinks in command line and has decades of Unix experience (although none with Ubuntu in particular), so I was lucky. But I NEED to figure it out without his help, so I read and read and read, and nothing seems to address my issue. 

From the get-go the boot process has been flaky. Occasionally it'll boot right up, but mostly I have to boot in safe mode and even then it'll only boot correctly one every 10 tries. Other times I get the black screen for however long I'll let it sit there and have to hold the power button for 10 seconds to try again. I tried the memory test a couple of times it runs OK then tells me to press enter to continue on to safe mode. Hubby said it's getting stuck on some hardware bit but he doesn't know what. Help! What info do I need to give you?

Thanks!

To pinpoint the issue, we can start by looking at some system logs. Once you are logged in (even if it is a "safe mode") you should have access to a terminal. From there, type ```
dmesg
```to access the kernel log during bootup. Copy and past the output here, and someone will be able to tell you if something looks "suspicious" during boot up.

Other useful information may be found in ```
/var/log/syslog
```I would suggest using the ```
tail
```command to only view the most recent entries. For instance, running ```
tail -n 200 /var/log/syslog
``` will only display the most recent 200 lines.


Hopefully this gets you started! Getting Linux setup on old hardware can be a challenge, but it is a rewarding one if your goal is to learn a lot about Linux.

---

### Post by Jolimont on 2012-02-17
. Thank you for your help! I agree that using old hardware is hornet's nest, so I created a VM on my regular Windows laptop and installed Ubuntu that way. Works like a charm and I will use that to go through tutorials, etc. 

BUT I still want to get the old laptop booting properly, so here's the output of dmesg command. Man do you have to be Vulcan for this stuff to make sense or is there hope for a mere mortal?!!! Thanks for giving me any tips you have!

```
[    0.279993] pci 0000:02:04.1:   bridge window [mem 0x24000000-0x27ffffff pref]
[    0.279993] pci 0000:00:0a.0: PCI bridge to [bus 02-02]
[    0.279993] pci 0000:00:0a.0:   bridge window [io  0x3000-0x7fff]
[    0.279993] pci 0000:00:0a.0:   bridge window [mem 0xe8100000-0xe97fffff]
[    0.279993] pci 0000:00:0a.0:   bridge window [mem 0x20000000-0x27ffffff pref]
[    0.279993] pci 0000:01:00.0: BAR 6: assigned [mem 0xfc080000-0xfc09ffff pref]
[    0.279993] pci 0000:00:0b.0: PCI bridge to [bus 01-01]
[    0.279993] pci 0000:00:0b.0:   bridge window [io  disabled]
[    0.279993] pci 0000:00:0b.0:   bridge window [mem 0xea000000-0xeaffffff]
[    0.279993] pci 0000:00:0b.0:   bridge window [mem 0xf8000000-0xfc0fffff pref]
[    0.279993] pci 0000:00:0a.0: setting latency timer to 64
[    0.279993] ACPI: PCI Interrupt Link [LNK1] enabled at IRQ 19
[    0.279993] pci 0000:02:04.0: PCI INT A -> Link[LNK1] -> GSI 19 (level, low) -> IRQ 19
[    0.279993] ACPI: PCI Interrupt Link [LNK2] enabled at IRQ 18
[    0.279993] pci 0000:02:04.1: PCI INT B -> Link[LNK2] -> GSI 18 (level, low) -> IRQ 18
[    0.279993] pci_bus 0000:00: resource 4 [io  0x0000-0xffff]
[    0.279993] pci_bus 0000:00: resource 5 [mem 0x000a0000-0x000bffff]
[    0.279993] pci_bus 0000:00: resource 6 [mem 0x20000000-0xffffffff]
[    0.279993] pci_bus 0000:02: resource 0 [io  0x3000-0x7fff]
[    0.279993] pci_bus 0000:02: resource 1 [mem 0xe8100000-0xe97fffff]
[    0.279993] pci_bus 0000:02: resource 2 [mem 0x20000000-0x27ffffff pref]
[    0.279993] pci_bus 0000:03: resource 0 [io  0x3000-0x30ff]
[    0.279993] pci_bus 0000:03: resource 1 [io  0x3400-0x34ff]
[    0.279993] pci_bus 0000:03: resource 2 [mem 0x20000000-0x23ffffff pref]
[    0.279993] pci_bus 0000:07: resource 0 [io  0x3800-0x38ff]
[    0.279993] pci_bus 0000:07: resource 1 [io  0x3c00-0x3cff]
[    0.279993] pci_bus 0000:07: resource 2 [mem 0x24000000-0x27ffffff pref]
[    0.279993] pci_bus 0000:01: resource 1 [mem 0xea000000-0xeaffffff]
[    0.279993] pci_bus 0000:01: resource 2 [mem 0xf8000000-0xfc0fffff pref]
[    0.279993] NET: Registered protocol family 2
[    0.279993] IP route cache hash table entries: 4096 (order: 2, 16384 bytes)
[    0.280369] TCP established hash table entries: 16384 (order: 5, 131072 bytes)
[    0.280629] TCP bind hash table entries: 16384 (order: 5, 131072 bytes)
[    0.280871] TCP: Hash tables configured (established 16384 bind 16384)
[    0.280946] TCP reno registered
[    0.281017] UDP hash table entries: 256 (order: 1, 8192 bytes)
[    0.281101] UDP-Lite hash table entries: 256 (order: 1, 8192 bytes)
[    0.281354] NET: Registered protocol family 1
[    0.808110] PCI: CLS mismatch (32 != 64), using 64 bytes
[    0.808131] pci 0000:01:00.0: Boot video device
[    0.808222] Simple Boot Flag at 0x37 set to 0x1
[    0.808963] audit: initializing netlink socket (disabled)
[    0.809053] type=2000 audit(1329492143.804:1): initialized
[    0.869068] Trying to unpack rootfs image as initramfs...
[    0.940170] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    0.948591] VFS: Disk quotas dquot_6.5.2
[    0.948852] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.950837] fuse init (API version 7.16)
[    0.951162] msgmni has been set to 964
[    0.964507] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.968992] io scheduler noop registered
[    0.969070] io scheduler deadline registered
[    0.969212] io scheduler cfq registered (default)
[    0.969691] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.969841] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.971826] ACPI: Deprecated procfs I/F for AC is loaded, please retry with CONFIG_ACPI_PROCFS_POWER cleared
[    0.973084] ACPI: AC Adapter [ACAD] (on-line)
[    0.973345] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0
[    0.973446] ACPI: Power Button [PWRB]
[    0.973641] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input1
[    0.998207] ACPI: Lid Switch [LID]
[    0.998474] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input2
[    0.998572] ACPI: Power Button [PWRF]
[    0.998709] ACPI: acpi_idle registered with cpuidle
[    0.998778] Marking TSC unstable due to TSC halts in idle
[    1.039274] ACPI: Invalid active0 threshold
[    1.042288] thermal LNXTHERM:00: registered as thermal_zone0
[    1.042368] ACPI: Thermal Zone [THRM] (54 C)
[    1.042522] ACPI: Deprecated procfs I/F for battery is loaded, please retry with CONFIG_ACPI_PROCFS_POWER cleared
[    1.042673] ERST: Table is not found!
[    1.042938] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    1.046501] ACPI: PCI Interrupt Link [LMCI] enabled at IRQ 22
[    1.046608] serial 0000:00:06.1: PCI INT B -> Link[LMCI] -> GSI 22 (level, low) -> IRQ 22
[    1.046710] serial 0000:00:06.1: PCI INT B disabled
[    1.047158] Linux agpgart interface v0.103
[    1.047285] agpgart-amd64 0000:00:00.0: AGP bridge [10de/00d1]
[    1.047366] agpgart-amd64 0000:00:00.0: aperture size 4096 MB is not right, using settings from NB
[    1.047466] agpgart-amd64 0000:00:00.0: setting up Nforce3 AGP
[    1.060673] isapnp: Scanning for PnP cards...
[    1.113117] agpgart-amd64 0000:00:00.0: AGP aperture is 128M @ 0xf0000000
[    1.121097] brd: module loaded
[    1.122796] loop: module loaded
[    1.123412] pata_acpi 0000:00:08.0: setting latency timer to 64
[    1.129413] Fixed MDIO Bus: probed
[    1.129572] PPP generic driver version 2.4.2
[    1.129786] tun: Universal TUN/TAP device driver, 1.6
[    1.129858] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    1.130163] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    1.130672] ACPI: PCI Interrupt Link [LUS2] enabled at IRQ 21
[    1.130780] ehci_hcd 0000:00:02.2: PCI INT C -> Link[LUS2] -> GSI 21 (level, low) -> IRQ 21
[    1.130903] ehci_hcd 0000:00:02.2: setting latency timer to 64
[    1.130911] ehci_hcd 0000:00:02.2: EHCI Host Controller
[    1.131078] ehci_hcd 0000:00:02.2: new USB bus registered, assigned bus number 1
[    1.131227] ehci_hcd 0000:00:02.2: cache line size of 64 is not supported
[    1.131269] ehci_hcd 0000:00:02.2: irq 21, io mem 0xe8004000
[    1.179927] ehci_hcd 0000:00:02.2: USB 2.0 started, EHCI 1.00
[    1.268461] hub 1-0:1.0: USB hub found
[    1.268547] hub 1-0:1.0: 6 ports detected
[    1.268812] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    1.269292] ACPI: PCI Interrupt Link [LUS0] enabled at IRQ 20
[    1.269398] ohci_hcd 0000:00:02.0: PCI INT A -> Link[LUS0] -> GSI 20 (level, low) -> IRQ 20
[    1.269522] ohci_hcd 0000:00:02.0: setting latency timer to 64
[    1.269530] ohci_hcd 0000:00:02.0: OHCI Host Controller
[    1.269710] ohci_hcd 0000:00:02.0: new USB bus registered, assigned bus number 2
[    1.269857] ohci_hcd 0000:00:02.0: irq 20, io mem 0xe8000000
[    1.452486] hub 2-0:1.0: USB hub found
[    1.452573] hub 2-0:1.0: 3 ports detected
[    1.454524] ACPI: PCI Interrupt Link [LUS1] enabled at IRQ 22
[    1.454612] ohci_hcd 0000:00:02.1: PCI INT B -> Link[LUS1] -> GSI 22 (level, low) -> IRQ 22
[    1.454735] ohci_hcd 0000:00:02.1: setting latency timer to 64
[    1.454744] ohci_hcd 0000:00:02.1: OHCI Host Controller
[    1.454971] ohci_hcd 0000:00:02.1: new USB bus registered, assigned bus number 3
[    1.455126] ohci_hcd 0000:00:02.1: irq 22, io mem 0xe8001000
[    1.510561] hub 3-0:1.0: USB hub found
[    1.510649] hub 3-0:1.0: 3 ports detected
[    1.510919] uhci_hcd: USB Universal Host Controller Interface driver
[    1.511220] i8042: PNP: PS/2 Controller [PNP0303S2K,PNP0f13S2M] at 0x60,0x64 irq 1,12
[    1.520597] i8042: Detected active multiplexing controller, rev 1.1
[    1.566129] isapnp: No Plug & Play device found
[    1.584880] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.584972] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[    1.585048] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[    1.585124] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[    1.585202] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[    1.585520] mousedev: PS/2 mouse device common for all mice
[    1.585971] rtc_cmos 00:06: RTC can wake from S4
[    1.586231] rtc_cmos 00:06: rtc core: registered rtc_cmos as rtc0
[    1.586334] rtc0: alarms up to one year, y3k, 114 bytes nvram
[    1.586700] device-mapper: uevent: version 1.0.3
[    1.587002] device-mapper: ioctl: 4.20.0-ioctl (2011-02-02) initialised: [EMAIL="dm-devel@redhat.com"]dm-devel@redhat.com[/EMAIL]
[    1.587189] EISA: Probing bus 0 at eisa.0
[    1.587261] EISA: Cannot allocate resource for mainboard
[    1.587335] Cannot allocate resource for EISA slot 1
[    1.587408] Cannot allocate resource for EISA slot 2
[    1.587480] Cannot allocate resource for EISA slot 3
[    1.587553] Cannot allocate resource for EISA slot 4
[    1.587625] Cannot allocate resource for EISA slot 5
[    1.587698] Cannot allocate resource for EISA slot 6
[    1.587770] Cannot allocate resource for EISA slot 7
[    1.587843] Cannot allocate resource for EISA slot 8
[    1.589155] EISA: Detected 0 cards.
[    1.597012] cpufreq-nforce2: No nForce2 chipset.
[    1.597198] cpuidle: using governor ladder
[    1.597395] cpuidle: using governor menu
[    1.597465] EFI Variables Facility v0.08 2004-May-17
[    1.598237] TCP cubic registered
[    1.598740] NET: Registered protocol family 10
[    1.600346] NET: Registered protocol family 17
[    1.600464] Registering the dns_resolver key type
[    1.600574] Using IPI No-Shortcut mode
[    1.600909] PM: Hibernation image not present or could not be loaded.
[    1.600936] registered taskstats version 1
[    1.636408] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input3
[    1.660922] ACPI: Battery Slot [BAT1] (battery present)
[    1.884599] usb 2-1: new low speed USB device number 2 using ohci_hcd
[    2.174017] Freeing initrd memory: 13324k freed
[    2.208270]   Magic number: 0:665:386
[    2.208484] rtc_cmos 00:06: setting system clock to 2012-02-17 15:22:25 UTC (1329492145)
[    2.208582] powernow-k8: Found 1 AMD Athlon(tm) XP Processor 3000+ (1 cpu cores) (version 2.20.00)
[    2.231502] powernow-k8: fid 0x8 (1600 MHz), vid 0x6
[    2.231576] powernow-k8: fid 0x0 (800 MHz), vid 0x18
[    2.235829] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    2.235897] EDD information not available.
[    2.236125] Freeing unused kernel memory: 696k freed
[    2.236884] Write protecting the kernel text: 5340k
[    2.236997] Write protecting the kernel read-only data: 2192k
[    2.266950] udevd[77]: starting version 173
[    2.284103] usb 3-1: new low speed USB device number 2 using ohci_hcd
[    2.470082] pata_amd 0000:00:08.0: version 0.4.1
[    2.470145] pata_amd 0000:00:08.0: setting latency timer to 64
[    2.508569] scsi0 : pata_amd
[    2.512092] scsi1 : pata_amd
[    2.512832] ata1: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0x2080 irq 14
[    2.512904] ata2: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0x2088 irq 15
[    2.515987] ACPI: PCI Interrupt Link [LNK3] enabled at IRQ 17
[    2.539256] 8139cp: 8139cp: 10/100 PCI Ethernet driver v1.3 (Mar 22, 2004)
[    2.547533] b43-pci-bridge 0000:02:02.0: PCI INT A -> Link[LNK3] -> GSI 17 (level, low) -> IRQ 17
[    2.547669] ssb: Core 0 found: ChipCommon (cc 0x800, rev 0x04, vendor 0x4243)
[    2.547675] ssb: Core 1 found: IEEE 802.11 (cc 0x812, rev 0x05, vendor 0x4243)
[    2.547682] ssb: Core 2 found: PCMCIA (cc 0x80D, rev 0x02, vendor 0x4243)
[    2.547688] ssb: Core 3 found: V90 (cc 0x807, rev 0x02, vendor 0x4243)
[    2.547693] ssb: Core 4 found: PCI (cc 0x804, rev 0x09, vendor 0x4243)
[    2.551760] input: CHESEN PS2 to USB Converter as /devices/pci0000:00/0000:00:02.0/usb2/2-1/2-1:1.0/input/input4
[    2.551988] generic-usb 0003:0518:0001.0001: input,hidraw0: USB HID v1.10 Keyboard [CHESEN PS2 to USB Converter] on usb-0000:00:02.0-1/input0
[    2.553274] ssb: Sonics Silicon Backplane found on PCI device 0000:02:02.0
[    2.553396] 8139cp 0000:02:01.0: This (id 10ec:8139 rev 10) is not an 8139C+ compatible chip, use 8139too
[    2.561576] input: CHESEN PS2 to USB Converter as /devices/pci0000:00/0000:00:02.0/usb2/2-1/2-1:1.1/input/input5
[    2.561851] generic-usb 0003:0518:0001.0002: input,hidraw1: USB HID v1.10 Mouse [CHESEN PS2 to USB Converter] on usb-0000:00:02.0-1/input1
[    2.567979] input: Microsoft Microsoft 3-Button Mouse with IntelliEye(TM) as /devices/pci0000:00/0000:00:02.1/usb3/3-1/3-1:1.0/input/input6
[    2.568283] generic-usb 0003:045E:0040.0003: input,hidraw2: USB HID v1.10 Mouse [Microsoft Microsoft 3-Button Mouse with IntelliEye(TM)] on usb-0000:00:02.1-1/input0
[    2.568422] usbcore: registered new interface driver usbhid
[    2.568492] usbhid: USB HID core driver
[    2.732543] ata1.00: ATA-6: FUJITSU MHT2060AT PL, 0022, max UDMA/100
[    2.732620] ata1.00: 117210240 sectors, multi 16: LBA 
[    2.732696] ata1: nv_mode_filter: 0x3f39f&0x3f39f->0x3f39f, BIOS=0x3f000 (0xc6000000) ACPI=0x3f01f (20:600:0x13)
[    2.748465] ata1.00: configured for UDMA/100
[    2.748687] scsi 0:0:0:0: Direct-Access     ATA      FUJITSU MHT2060A 0022 PQ: 0 ANSI: 5
[    2.749016] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    2.749303] sd 0:0:0:0: [sda] 117210240 512-byte logical blocks: (60.0 GB/55.8 GiB)
[    2.749452] sd 0:0:0:0: [sda] Write Protect is off
[    2.749520] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    2.749549] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.880849]  sda: sda1 sda2 < sda5 >
[    2.881351] sd 0:0:0:0: [sda] Attached SCSI disk
[    2.912293] ata2.00: ATAPI: HL-DT-STCD-RW/DVD DRIVE GCC-4241N, 0C29, max MWDMA2
[    2.912390] ata2: nv_mode_filter: 0x39f&0x739f->0x39f, BIOS=0x0 (0xc6000000) ACPI=0x39f (120:600:0x12)
[    2.928220] ata2.00: configured for MWDMA2
[    2.934620] scsi 1:0:0:0: CD-ROM            HL-DT-ST RW/DVD GCC-4241N 0C29 PQ: 0 ANSI: 5
[    2.940641] sr0: scsi3-mmc drive: 24x/24x writer cd/rw xa/form2 cdda tray
[    2.940714] cdrom: Uniform CD-ROM driver Revision: 3.20
[    2.940950] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    2.941047] sr 1:0:0:0: Attached scsi generic sg1 type 5
[    2.942336] 8139too: 8139too Fast Ethernet driver 0.9.28
[    2.942465] 8139too 0000:02:01.0: PCI INT A -> Link[LNK2] -> GSI 18 (level, low) -> IRQ 18
[    2.948578] 8139too 0000:02:01.0: eth0: RealTek RTL8139 at 0x7000, 00:0f:b0:0f:3c:da, IRQ 18
[    3.426350] EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: (null)
[    5.512063] floppy0: no floppy controllers found
[   69.713204] udevd[504]: starting version 173
[   69.752310] Adding 521212k swap on /dev/sda5.  Priority:-1 extents:1 across:521212k 
[   70.162620] wmi: Mapper loaded
[   70.186504] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   70.381482] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A03:00/device:18/LNXVIDEO:00/input/input7
[   70.381615] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[   70.568845] parport_pc 00:0b: reported by Plug and Play ACPI
[   70.568899] parport0: PC-style at 0x378 (0x77, irq 7, dma 1 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
[   70.639436] lp: driver loaded but no devices found
[   70.664426] lp0: using parport0 (interrupt-driven).
[   70.705214] input: PS/2 Mouse as /devices/platform/i8042/serio4/input/input8
[   70.725131] input: AlpsPS/2 ALPS GlidePoint as /devices/platform/i8042/serio4/input/input9
[   70.746852] i2c i2c-0: nForce2 SMBus adapter at 0x2040
[   70.746921] i2c i2c-1: nForce2 SMBus adapter at 0x2000
[   70.755636] type=1400 audit(1329492214.039:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=716 comm="apparmor_parser"
[   70.756369] type=1400 audit(1329492214.043:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=716 comm="apparmor_parser"
[   70.756764] type=1400 audit(1329492214.043:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=716 comm="apparmor_parser"
[   70.759381] yenta_cardbus 0000:02:04.0: CardBus bridge found [103c:006d]
[   70.759403] yenta_cardbus 0000:02:04.0: CardBus bridge to [bus 03-06]
[   70.759408] yenta_cardbus 0000:02:04.0:   bridge window [io  0x3000-0x30ff]
[   70.759414] yenta_cardbus 0000:02:04.0:   bridge window [io  0x3400-0x34ff]
[   70.759420] yenta_cardbus 0000:02:04.0:   bridge window [mem 0x20000000-0x23ffffff pref]
[   70.759425] yenta_cardbus 0000:02:04.0:   bridge window [mem 0xe8400000-0xe87fffff]
[   70.759432] yenta_cardbus 0000:02:04.0: Enabling burst memory read transactions
[   70.759437] yenta_cardbus 0000:02:04.0: Using CSCINT to route CSC interrupts to PCI
[   70.759441] yenta_cardbus 0000:02:04.0: Routing CardBus interrupts to PCI
[   70.759447] yenta_cardbus 0000:02:04.0: TI: mfunc 0x01111d22, devctl 0x64
[   70.988645] yenta_cardbus 0000:02:04.0: ISA IRQ mask 0x0c38, PCI irq 19
[   70.988651] yenta_cardbus 0000:02:04.0: Socket status: 30000086
[   70.988657] pci_bus 0000:02: Raising subordinate bus# of parent bus (#02) from #02 to #06
[   70.988670] yenta_cardbus 0000:02:04.0: pcmcia: parent PCI bridge window: [io  0x3000-0x7fff]
[   70.988676] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x3000-0x7fff: excluding 0x3000-0x30ff 0x3400-0x34ff 0x3800-0x38ff 0x3c00-0x3cff 0x7000-0x70ff 0x7400-0x743f
[   71.099923] cfg80211: Calling CRDA to update world regulatory domain
[   71.123094] 
[   71.123107] yenta_cardbus 0000:02:04.0: pcmcia: parent PCI bridge window: [mem 0xe8100000-0xe97fffff]
[   71.123114] pcmcia_socket pcmcia_socket0: cs: memory probe 0xe8100000-0xe97fffff: excluding 0xe8100000-0xe826ffff 0xe83e0000-0xe882ffff
[   71.123132] yenta_cardbus 0000:02:04.0: pcmcia: parent PCI bridge window: [mem 0x20000000-0x27ffffff pref]
[   71.123136] pcmcia_socket pcmcia_socket0: cs: memory probe 0x20000000-0x27ffffff: excluding 0x20000000-0x27ffffff
[   71.135980] yenta_cardbus 0000:02:04.1: CardBus bridge found [103c:006d]
[   71.136047] yenta_cardbus 0000:02:04.1: Using CSCINT to route CSC interrupts to PCI
[   71.136051] yenta_cardbus 0000:02:04.1: Routing CardBus interrupts to PCI
[   71.136057] yenta_cardbus 0000:02:04.1: TI: mfunc 0x01111d22, devctl 0x64
[   71.285047] cfg80211: World regulatory domain updated:
[   71.285054] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   71.285060] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   71.285064] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   71.285068] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   71.285072] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   71.285076] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   71.368582] yenta_cardbus 0000:02:04.1: ISA IRQ mask 0x0c38, PCI irq 18
[   71.368589] yenta_cardbus 0000:02:04.1: Socket status: 30000006
[   71.368595] pci_bus 0000:02: Raising subordinate bus# of parent bus (#02) from #06 to #0a
[   71.368607] yenta_cardbus 0000:02:04.1: pcmcia: parent PCI bridge window: [io  0x3000-0x7fff]
[   71.368613] pcmcia_socket pcmcia_socket1: cs: IO port probe 0x3000-0x7fff: excluding 0x3000-0x30ff 0x3400-0x34ff 0x3800-0x38ff 0x3c00-0x3cff 0x7000-0x70ff 0x7400-0x743f
[   71.382115] yenta_cardbus 0000:02:04.1: pcmcia: parent PCI bridge window: [mem 0xe8100000-0xe97fffff]
[   71.382120] pcmcia_socket pcmcia_socket1: cs: memory probe 0xe8100000-0xe97fffff: excluding 0xe8100000-0xe826ffff 0xe83e0000-0xe882ffff 0xe8b10000-0xe90cffff
[   71.382138] yenta_cardbus 0000:02:04.1: pcmcia: parent PCI bridge window: [mem 0x20000000-0x27ffffff pref]
[   71.382143] pcmcia_socket pcmcia_socket1: cs: memory probe 0x20000000-0x27ffffff: excluding 0x20000000-0x27ffffff
[   71.496947] ppdev: user-space parallel port driver
[   71.635262] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x100-0x3af: excluding nothing: probe failed.
[   71.635353] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x3e0-0x4ff: excluding nothing: probe failed.
[   71.635417] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x820-0x8ff: excluding nothing: probe failed.
[   71.635477] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xc00-0xcf7: excluding nothing: probe failed.
[   71.635540] pcmcia_socket pcmcia_socket0: cs: memory probe 0x0c0000-0x0fffff: excluding 0xc0000-0xfffff
[   71.635596] pcmcia_socket pcmcia_socket0: cs: memory probe 0xa0000000-0xa0ffffff: excluding 0xa0000000-0xa0ffffff
[   71.635650] pcmcia_socket pcmcia_socket0: cs: memory probe 0x60000000-0x60ffffff: excluding 0x60000000-0x60ffffff
[   71.635708] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xa00-0xaff: excluding nothing: probe failed.
[   71.635944] pcmcia_socket pcmcia_socket1: cs: IO port probe 0x100-0x3af: excluding nothing: probe failed.
[   71.636075] pcmcia_socket pcmcia_socket1: cs: IO port probe 0x3e0-0x4ff: excluding nothing: probe failed.
[   71.636138] pcmcia_socket pcmcia_socket1: cs: IO port probe 0x820-0x8ff: excluding nothing: probe failed.
[   71.636197] pcmcia_socket pcmcia_socket1: cs: IO port probe 0xc00-0xcf7: excluding nothing: probe failed.
[   71.636259] pcmcia_socket pcmcia_socket1: cs: memory probe 0x0c0000-0x0fffff: excluding 0xc0000-0xfffff
[   71.636314] pcmcia_socket pcmcia_socket1: cs: memory probe 0xa0000000-0xa0ffffff: excluding 0xa0000000-0xa0ffffff
[   71.636369] pcmcia_socket pcmcia_socket1: cs: memory probe 0x60000000-0x60ffffff: excluding 0x60000000-0x60ffffff
[   71.636424] pcmcia_socket pcmcia_socket1: cs: IO port probe 0xa00-0xaff: excluding nothing: probe failed.
[   71.847906] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
[   71.903223] b43-phy0: Broadcom 4306 WLAN found (core revision 5)
[   71.948274] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
[   71.948282] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[   71.948286] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
[   71.948291] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[   71.948294] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
[   71.948298] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[   71.948301] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
[   71.948305] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[   71.948309] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
[   71.948313] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[   71.948316] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
[   71.948320] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[   71.948323] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
[   71.948327] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[   71.948331] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
[   71.948335] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[   71.948338] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
[   71.948342] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[   71.948345] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
[   71.948349] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[   71.948353] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
[   71.948357] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[   71.948360] cfg80211: Updating information on frequency 2467 MHz for a 20 MHz width channel with regulatory rule:
[   71.948364] cfg80211: 2457000 KHz - 2482000 KHz @  KHz), (300 mBi, 2000 mBm)
[   71.948367] cfg80211: Updating information on frequency 2472 MHz for a 20 MHz width channel with regulatory rule:
[   71.948371] cfg80211: 2457000 KHz - 2482000 KHz @  KHz), (300 mBi, 2000 mBm)
[   71.948375] cfg80211: Updating information on frequency 2484 MHz for a 20 MHz width channel with regulatory rule:
[   71.948379] cfg80211: 2474000 KHz - 2494000 KHz @  KHz), (300 mBi, 2000 mBm)
[   72.140802] nvidia: module license 'NVIDIA' taints kernel.
[   72.140809] Disabling lock debugging due to kernel taint
[   72.692420] nvidia 0000:01:00.0: power state changed by ACPI to D0
[   72.692430] nvidia 0000:01:00.0: power state changed by ACPI to D0
[   72.692617] ACPI: PCI Interrupt Link [LNK5] enabled at IRQ 16
[   72.692640] nvidia 0000:01:00.0: PCI INT A -> Link[LNK5] -> GSI 16 (level, low) -> IRQ 16
[   72.692653] vgaarb: device changed decodes: PCI:0000:01:00.0,olddecodes=io+mem,decodes=nonewns=io+mem
[   72.695211] NVRM: loading NVIDIA Linux x86 Kernel Module  96.43.20  Sun Jul 17 23:28:58 PDT 2011
[   72.701097] ieee80211 phy0: Selected rate control algorithm 'minstrel_ht'
[   72.701979] Registered led device: b43-phy0::tx
[   72.702012] Registered led device: b43-phy0::rx
[   72.702041] Registered led device: b43-phy0::radio
[   72.702067] Broadcom 43xx driver loaded [ Features: PNL, Firmware-ID: FW13 ]
[   72.910990] ACPI: PCI Interrupt Link [LACI] enabled at IRQ 21
[   72.911001] Intel ICH 0000:00:06.0: PCI INT A -> Link[LACI] -> GSI 21 (level, low) -> IRQ 21
[   72.911037] Intel ICH 0000:00:06.0: setting latency timer to 64
[   73.142451] type=1400 audit(1329492216.427:5): apparmor="STATUS" operation="profile_load" name="/usr/lib/lightdm/lightdm-guest-session-wrapper" pid=976 comm="apparmor_parser"
[   73.146534] type=1400 audit(1329492216.431:6): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=980 comm="apparmor_parser"
[   73.152829] type=1400 audit(1329492216.439:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=980 comm="apparmor_parser"
[   73.160963] type=1400 audit(1329492216.447:: apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=980 comm="apparmor_parser"
[   73.207138] type=1400 audit(1329492216.491:9): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince" pid=983 comm="apparmor_parser"
[   73.230870] type=1400 audit(1329492216.515:10): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince-previewer" pid=983 comm="apparmor_parser"
[   73.236712] type=1400 audit(1329492216.523:11): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince-thumbnailer" pid=983 comm="apparmor_parser"
[   73.358365] 8139too 0000:02:01.0: eth0: link down
[   73.358930] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   73.529144] init: failsafe main process (929) killed by TERM signal
[   73.600113] init: apport pre-start process (1023) terminated with status 1
[   73.606396] init: alsa-restore main process (1029) terminated with status 19
[   73.649965] init: apport post-stop process (1052) terminated with status 1
[   73.652262] b43-phy0: Loading firmware version 508.1084 (2009-01-14 01:32:01)
[   73.691225] floppy0: no floppy controllers found
[   73.732282] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   73.836053] intel8x0_measure_ac97_clock: measured 55355 usecs (2688 samples)
[   73.836059] intel8x0: clocking to 47447
[   74.262647] init: udev-fallback-graphics main process (1090) terminated with status 1
[   74.296955] init: friendly-recovery post-stop process (404) terminated with status 1
[   74.345139] Bluetooth: Core ver 2.16
[   74.345203] NET: Registered protocol family 31
[   74.345206] Bluetooth: HCI device and connection manager initialized
[   74.345211] Bluetooth: HCI socket layer initialized
[   74.345213] Bluetooth: L2CAP socket layer initialized
[   74.349654] Bluetooth: SCO socket layer initialized
[   74.394434] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   74.394439] Bluetooth: BNEP filters: protocol multicast
[   75.716297] agpgart-amd64 0000:00:00.0: AGP 2.0 bridge
[   75.716319] agpgart-amd64 0000:00:00.0: putting AGP V2 device into 4x mode
[   75.716371] nvidia 0000:01:00.0: putting AGP V2 device into 4x mode
[   75.979601] cfg80211: Found new beacon on frequency: 2472 MHz (Ch 13) on phy0
[   76.467553] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,commit=0
[   76.674380] init: plymouth-stop pre-start process (1254[    0.279993] pci 0000:02:04.1:   bridge window [mem 0x24000000-0x27ffffff pref]
[    0.279993] pci 0000:00:0a.0: PCI bridge to [bus 02-02]
[    0.279993] pci 0000:00:0a.0:   bridge window [io  0x3000-0x7fff]
[    0.279993] pci 0000:00:0a.0:   bridge window [mem 0xe8100000-0xe97fffff]
[    0.279993] pci 0000:00:0a.0:   bridge window [mem 0x20000000-0x27ffffff pref]
[    0.279993] pci 0000:01:00.0: BAR 6: assigned [mem 0xfc080000-0xfc09ffff pref]
[    0.279993] pci 0000:00:0b.0: PCI bridge to [bus 01-01]
[    0.279993] pci 0000:00:0b.0:   bridge window [io  disabled]
[    0.279993] pci 0000:00:0b.0:   bridge window [mem 0xea000000-0xeaffffff]
[    0.279993] pci 0000:00:0b.0:   bridge window [mem 0xf8000000-0xfc0fffff pref]
[    0.279993] pci 0000:00:0a.0: setting latency timer to 64
[    0.279993] ACPI: PCI Interrupt Link [LNK1] enabled at IRQ 19
[    0.279993] pci 0000:02:04.0: PCI INT A -> Link[LNK1] -> GSI 19 (level, low) -> IRQ 19
[    0.279993] ACPI: PCI Interrupt Link [LNK2] enabled at IRQ 18
[    0.279993] pci 0000:02:04.1: PCI INT B -> Link[LNK2] -> GSI 18 (level, low) -> IRQ 18
[    0.279993] pci_bus 0000:00: resource 4 [io  0x0000-0xffff]
[    0.279993] pci_bus 0000:00: resource 5 [mem 0x000a0000-0x000bffff]
[    0.279993] pci_bus 0000:00: resource 6 [mem 0x20000000-0xffffffff]
[    0.279993] pci_bus 0000:02: resource 0 [io  0x3000-0x7fff]
[    0.279993] pci_bus 0000:02: resource 1 [mem 0xe8100000-0xe97fffff]
[    0.279993] pci_bus 0000:02: resource 2 [mem 0x20000000-0x27ffffff pref]
[    0.279993] pci_bus 0000:03: resource 0 [io  0x3000-0x30ff]
[    0.279993] pci_bus 0000:03: resource 1 [io  0x3400-0x34ff]
[    0.279993] pci_bus 0000:03: resource 2 [mem 0x20000000-0x23ffffff pref]
[    0.279993] pci_bus 0000:07: resource 0 [io  0x3800-0x38ff]
[    0.279993] pci_bus 0000:07: resource 1 [io  0x3c00-0x3cff]
[    0.279993] pci_bus 0000:07: resource 2 [mem 0x24000000-0x27ffffff pref]
[    0.279993] pci_bus 0000:01: resource 1 [mem 0xea000000-0xeaffffff]
[    0.279993] pci_bus 0000:01: resource 2 [mem 0xf8000000-0xfc0fffff pref]
[    0.279993] NET: Registered protocol family 2
[    0.279993] IP route cache hash table entries: 4096 (order: 2, 16384 bytes)
[    0.280369] TCP established hash table entries: 16384 (order: 5, 131072 bytes)
[    0.280629] TCP bind hash table entries: 16384 (order: 5, 131072 bytes)
[    0.280871] TCP: Hash tables configured (established 16384 bind 16384)
[    0.280946] TCP reno registered
[    0.281017] UDP hash table entries: 256 (order: 1, 8192 bytes)
[    0.281101] UDP-Lite hash table entries: 256 (order: 1, 8192 bytes)
[    0.281354] NET: Registered protocol family 1
[    0.808110] PCI: CLS mismatch (32 != 64), using 64 bytes
[    0.808131] pci 0000:01:00.0: Boot video device
[    0.808222] Simple Boot Flag at 0x37 set to 0x1
[    0.808963] audit: initializing netlink socket (disabled)
[    0.809053] type=2000 audit(1329492143.804:1): initialized
[    0.869068] Trying to unpack rootfs image as initramfs...
[    0.940170] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    0.948591] VFS: Disk quotas dquot_6.5.2
[    0.948852] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.950837] fuse init (API version 7.16)
[    0.951162] msgmni has been set to 964
[    0.964507] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.968992] io scheduler noop registered
[    0.969070] io scheduler deadline registered
[    0.969212] io scheduler cfq registered (default)
[    0.969691] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.969841] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.971826] ACPI: Deprecated procfs I/F for AC is loaded, please retry with CONFIG_ACPI_PROCFS_POWER cleared
[    0.973084] ACPI: AC Adapter [ACAD] (on-line)
[    0.973345] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0
[    0.973446] ACPI: Power Button [PWRB]
[    0.973641] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input1
[    0.998207] ACPI: Lid Switch [LID]
[    0.998474] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input2
[    0.998572] ACPI: Power Button [PWRF]
[    0.998709] ACPI: acpi_idle registered with cpuidle
[    0.998778] Marking TSC unstable due to TSC halts in idle
[    1.039274] ACPI: Invalid active0 threshold
[    1.042288] thermal LNXTHERM:00: registered as thermal_zone0
[    1.042368] ACPI: Thermal Zone [THRM] (54 C)
[    1.042522] ACPI: Deprecated procfs I/F for battery is loaded, please retry with CONFIG_ACPI_PROCFS_POWER cleared
[    1.042673] ERST: Table is not found!
[    1.042938] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    1.046501] ACPI: PCI Interrupt Link [LMCI] enabled at IRQ 22
[    1.046608] serial 0000:00:06.1: PCI INT B -> Link[LMCI] -> GSI 22 (level, low) -> IRQ 22
[    1.046710] serial 0000:00:06.1: PCI INT B disabled
[    1.047158] Linux agpgart interface v0.103
[    1.047285] agpgart-amd64 0000:00:00.0: AGP bridge [10de/00d1]
[    1.047366] agpgart-amd64 0000:00:00.0: aperture size 4096 MB is not right, using settings from NB
[    1.047466] agpgart-amd64 0000:00:00.0: setting up Nforce3 AGP
[    1.060673] isapnp: Scanning for PnP cards...
[    1.113117] agpgart-amd64 0000:00:00.0: AGP aperture is 128M @ 0xf0000000
[    1.121097] brd: module loaded
[    1.122796] loop: module loaded
[    1.123412] pata_acpi 0000:00:08.0: setting latency timer to 64
[    1.129413] Fixed MDIO Bus: probed
[    1.129572] PPP generic driver version 2.4.2
[    1.129786] tun: Universal TUN/TAP device driver, 1.6
[    1.129858] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    1.130163] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    1.130672] ACPI: PCI Interrupt Link [LUS2] enabled at IRQ 21
[    1.130780] ehci_hcd 0000:00:02.2: PCI INT C -> Link[LUS2] -> GSI 21 (level, low) -> IRQ 21
[    1.130903] ehci_hcd 0000:00:02.2: setting latency timer to 64
[    1.130911] ehci_hcd 0000:00:02.2: EHCI Host Controller
[    1.131078] ehci_hcd 0000:00:02.2: new USB bus registered, assigned bus number 1
[    1.131227] ehci_hcd 0000:00:02.2: cache line size of 64 is not supported
[    1.131269] ehci_hcd 0000:00:02.2: irq 21, io mem 0xe8004000
[    1.179927] ehci_hcd 0000:00:02.2: USB 2.0 started, EHCI 1.00
[    1.268461] hub 1-0:1.0: USB hub found
[    1.268547] hub 1-0:1.0: 6 ports detected
[    1.268812] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    1.269292] ACPI: PCI Interrupt Link [LUS0] enabled at IRQ 20
[    1.269398] ohci_hcd 0000:00:02.0: PCI INT A -> Link[LUS0] -> GSI 20 (level, low) -> IRQ 20
[    1.269522] ohci_hcd 0000:00:02.0: setting latency timer to 64
[    1.269530] ohci_hcd 0000:00:02.0: OHCI Host Controller
[    1.269710] ohci_hcd 0000:00:02.0: new USB bus registered, assigned bus number 2
[    1.269857] ohci_hcd 0000:00:02.0: irq 20, io mem 0xe8000000
[    1.452486] hub 2-0:1.0: USB hub found
[    1.452573] hub 2-0:1.0: 3 ports detected
[    1.454524] ACPI: PCI Interrupt Link [LUS1] enabled at IRQ 22
[    1.454612] ohci_hcd 0000:00:02.1: PCI INT B -> Link[LUS1] -> GSI 22 (level, low) -> IRQ 22
[    1.454735] ohci_hcd 0000:00:02.1: setting latency timer to 64
[    1.454744] ohci_hcd 0000:00:02.1: OHCI Host Controller
[    1.454971] ohci_hcd 0000:00:02.1: new USB bus registered, assigned bus number 3
[    1.455126] ohci_hcd 0000:00:02.1: irq 22, io mem 0xe8001000
[    1.510561] hub 3-0:1.0: USB hub found
[    1.510649] hub 3-0:1.0: 3 ports detected
[    1.510919] uhci_hcd: USB Universal Host Controller Interface driver
[    1.511220] i8042: PNP: PS/2 Controller [PNP0303S2K,PNP0f13S2M] at 0x60,0x64 irq 1,12
[    1.520597] i8042: Detected active multiplexing controller, rev 1.1
[    1.566129] isapnp: No Plug & Play device found
[    1.584880] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.584972] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[    1.585048] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[    1.585124] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[    1.585202] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[    1.585520] mousedev: PS/2 mouse device common for all mice
[    1.585971] rtc_cmos 00:06: RTC can wake from S4
[    1.586231] rtc_cmos 00:06: rtc core: registered rtc_cmos as rtc0
[    1.586334] rtc0: alarms up to one year, y3k, 114 bytes nvram
[    1.586700] device-mapper: uevent: version 1.0.3
[    1.587002] device-mapper: ioctl: 4.20.0-ioctl (2011-02-02) initialised: [EMAIL="dm-devel@redhat.com"]dm-devel@redhat.com[/EMAIL]
[    1.587189] EISA: Probing bus 0 at eisa.0
[    1.587261] EISA: Cannot allocate resource for mainboard
[    1.587335] Cannot allocate resource for EISA slot 1
[    1.587408] Cannot allocate resource for EISA slot 2
[    1.587480] Cannot allocate resource for EISA slot 3
[    1.587553] Cannot allocate resource for EISA slot 4
[    1.587625] Cannot allocate resource for EISA slot 5
[    1.587698] Cannot allocate resource for EISA slot 6
[    1.587770] Cannot allocate resource for EISA slot 7
[    1.587843] Cannot allocate resource for EISA slot 8
[    1.589155] EISA: Detected 0 cards.
[    1.597012] cpufreq-nforce2: No nForce2 chipset.
[    1.597198] cpuidle: using governor ladder
[    1.597395] cpuidle: using governor menu
[    1.597465] EFI Variables Facility v0.08 2004-May-17
[    1.598237] TCP cubic registered
[    1.598740] NET: Registered protocol family 10
[    1.600346] NET: Registered protocol family 17
[    1.600464] Registering the dns_resolver key type
[    1.600574] Using IPI No-Shortcut mode
[    1.600909] PM: Hibernation image not present or could not be loaded.
[    1.600936] registered taskstats version 1
[    1.636408] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input3
[    1.660922] ACPI: Battery Slot [BAT1] (battery present)
[    1.884599] usb 2-1: new low speed USB device number 2 using ohci_hcd
[    2.174017] Freeing initrd memory: 13324k freed
[    2.208270]   Magic number: 0:665:386
[    2.208484] rtc_cmos 00:06: setting system clock to 2012-02-17 15:22:25 UTC (1329492145)
[    2.208582] powernow-k8: Found 1 AMD Athlon(tm) XP Processor 3000+ (1 cpu cores) (version 2.20.00)
[    2.231502] powernow-k8: fid 0x8 (1600 MHz), vid 0x6
[    2.231576] powernow-k8: fid 0x0 (800 MHz), vid 0x18
[    2.235829] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    2.235897] EDD information not available.
[    2.236125] Freeing unused kernel memory: 696k freed
[    2.236884] Write protecting the kernel text: 5340k
[    2.236997] Write protecting the kernel read-only data: 2192k
[    2.266950] udevd[77]: starting version 173
[    2.284103] usb 3-1: new low speed USB device number 2 using ohci_hcd
[    2.470082] pata_amd 0000:00:08.0: version 0.4.1
[    2.470145] pata_amd 0000:00:08.0: setting latency timer to 64
[    2.508569] scsi0 : pata_amd
[    2.512092] scsi1 : pata_amd
[    2.512832] ata1: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0x2080 irq 14
[    2.512904] ata2: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0x2088 irq 15
[    2.515987] ACPI: PCI Interrupt Link [LNK3] enabled at IRQ 17
[    2.539256] 8139cp: 8139cp: 10/100 PCI Ethernet driver v1.3 (Mar 22, 2004)
[    2.547533] b43-pci-bridge 0000:02:02.0: PCI INT A -> Link[LNK3] -> GSI 17 (level, low) -> IRQ 17
[    2.547669] ssb: Core 0 found: ChipCommon (cc 0x800, rev 0x04, vendor 0x4243)
[    2.547675] ssb: Core 1 found: IEEE 802.11 (cc 0x812, rev 0x05, vendor 0x4243)
[    2.547682] ssb: Core 2 found: PCMCIA (cc 0x80D, rev 0x02, vendor 0x4243)
[    2.547688] ssb: Core 3 found: V90 (cc 0x807, rev 0x02, vendor 0x4243)
[    2.547693] ssb: Core 4 found: PCI (cc 0x804, rev 0x09, vendor 0x4243)
[    2.551760] input: CHESEN PS2 to USB Converter as /devices/pci0000:00/0000:00:02.0/usb2/2-1/2-1:1.0/input/input4
[    2.551988] generic-usb 0003:0518:0001.0001: input,hidraw0: USB HID v1.10 Keyboard [CHESEN PS2 to USB Converter] on usb-0000:00:02.0-1/input0
[    2.553274] ssb: Sonics Silicon Backplane found on PCI device 0000:02:02.0
[    2.553396] 8139cp 0000:02:01.0: This (id 10ec:8139 rev 10) is not an 8139C+ compatible chip, use 8139too
[    2.561576] input: CHESEN PS2 to USB Converter as /devices/pci0000:00/0000:00:02.0/usb2/2-1/2-1:1.1/input/input5
[    2.561851] generic-usb 0003:0518:0001.0002: input,hidraw1: USB HID v1.10 Mouse [CHESEN PS2 to USB Converter] on usb-0000:00:02.0-1/input1
[    2.567979] input: Microsoft Microsoft 3-Button Mouse with IntelliEye(TM) as /devices/pci0000:00/0000:00:02.1/usb3/3-1/3-1:1.0/input/input6
[    2.568283] generic-usb 0003:045E:0040.0003: input,hidraw2: USB HID v1.10 Mouse [Microsoft Microsoft 3-Button Mouse with IntelliEye(TM)] on usb-0000:00:02.1-1/input0
[    2.568422] usbcore: registered new interface driver usbhid
[    2.568492] usbhid: USB HID core driver
[    2.732543] ata1.00: ATA-6: FUJITSU MHT2060AT PL, 0022, max UDMA/100
[    2.732620] ata1.00: 117210240 sectors, multi 16: LBA 
[    2.732696] ata1: nv_mode_filter: 0x3f39f&0x3f39f->0x3f39f, BIOS=0x3f000 (0xc6000000) ACPI=0x3f01f (20:600:0x13)
[    2.748465] ata1.00: configured for UDMA/100
[    2.748687] scsi 0:0:0:0: Direct-Access     ATA      FUJITSU MHT2060A 0022 PQ: 0 ANSI: 5
[    2.749016] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    2.749303] sd 0:0:0:0: [sda] 117210240 512-byte logical blocks: (60.0 GB/55.8 GiB)
[    2.749452] sd 0:0:0:0: [sda] Write Protect is off
[    2.749520] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    2.749549] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.880849]  sda: sda1 sda2 < sda5 >
[    2.881351] sd 0:0:0:0: [sda] Attached SCSI disk
[    2.912293] ata2.00: ATAPI: HL-DT-STCD-RW/DVD DRIVE GCC-4241N, 0C29, max MWDMA2
[    2.912390] ata2: nv_mode_filter: 0x39f&0x739f->0x39f, BIOS=0x0 (0xc6000000) ACPI=0x39f (120:600:0x12)
[    2.928220] ata2.00: configured for MWDMA2
[    2.934620] scsi 1:0:0:0: CD-ROM            HL-DT-ST RW/DVD GCC-4241N 0C29 PQ: 0 ANSI: 5
[    2.940641] sr0: scsi3-mmc drive: 24x/24x writer cd/rw xa/form2 cdda tray
[    2.940714] cdrom: Uniform CD-ROM driver Revision: 3.20
[    2.940950] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    2.941047] sr 1:0:0:0: Attached scsi generic sg1 type 5
[    2.942336] 8139too: 8139too Fast Ethernet driver 0.9.28
[    2.942465] 8139too 0000:02:01.0: PCI INT A -> Link[LNK2] -> GSI 18 (level, low) -> IRQ 18
[    2.948578] 8139too 0000:02:01.0: eth0: RealTek RTL8139 at 0x7000, 00:0f:b0:0f:3c:da, IRQ 18
[    3.426350] EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: (null)
[    5.512063] floppy0: no floppy controllers found
[   69.713204] udevd[504]: starting version 173
[   69.752310] Adding 521212k swap on /dev/sda5.  Priority:-1 extents:1 across:521212k 
[   70.162620] wmi: Mapper loaded
[   70.186504] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   70.381482] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A03:00/device:18/LNXVIDEO:00/input/input7
[   70.381615] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[   70.568845] parport_pc 00:0b: reported by Plug and Play ACPI
[   70.568899] parport0: PC-style at 0x378 (0x77, irq 7, dma 1 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
[   70.639436] lp: driver loaded but no devices found
[   70.664426] lp0: using parport0 (interrupt-driven).
[   70.705214] input: PS/2 Mouse as /devices/platform/i8042/serio4/input/input8
[   70.725131] input: AlpsPS/2 ALPS GlidePoint as /devices/platform/i8042/serio4/input/input9
[   70.746852] i2c i2c-0: nForce2 SMBus adapter at 0x2040
[   70.746921] i2c i2c-1: nForce2 SMBus adapter at 0x2000
[   70.755636] type=1400 audit(1329492214.039:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=716 comm="apparmor_parser"
[   70.756369] type=1400 audit(1329492214.043:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=716 comm="apparmor_parser"
[   70.756764] type=1400 audit(1329492214.043:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=716 comm="apparmor_parser"
[   70.759381] yenta_cardbus 0000:02:04.0: CardBus bridge found [103c:006d]
[   70.759403] yenta_cardbus 0000:02:04.0: CardBus bridge to [bus 03-06]
[   70.759408] yenta_cardbus 0000:02:04.0:   bridge window [io  0x3000-0x30ff]
[   70.759414] yenta_cardbus 0000:02:04.0:   bridge window [io  0x3400-0x34ff]
[   70.759420] yenta_cardbus 0000:02:04.0:   bridge window [mem 0x20000000-0x23ffffff pref]
[   70.759425] yenta_cardbus 0000:02:04.0:   bridge window [mem 0xe8400000-0xe87fffff]
[   70.759432] yenta_cardbus 0000:02:04.0: Enabling burst memory read transactions
[   70.759437] yenta_cardbus 0000:02:04.0: Using CSCINT to route CSC interrupts to PCI
[   70.759441] yenta_cardbus 0000:02:04.0: Routing CardBus interrupts to PCI
[   70.759447] yenta_cardbus 0000:02:04.0: TI: mfunc 0x01111d22, devctl 0x64
[   70.988645] yenta_cardbus 0000:02:04.0: ISA IRQ mask 0x0c38, PCI irq 19
[   70.988651] yenta_cardbus 0000:02:04.0: Socket status: 30000086
[   70.988657] pci_bus 0000:02: Raising subordinate bus# of parent bus (#02) from #02 to #06
[   70.988670] yenta_cardbus 0000:02:04.0: pcmcia: parent PCI bridge window: [io  0x3000-0x7fff]
[   70.988676] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x3000-0x7fff: excluding 0x3000-0x30ff 0x3400-0x34ff 0x3800-0x38ff 0x3c00-0x3cff 0x7000-0x70ff 0x7400-0x743f
[   71.099923] cfg80211: Calling CRDA to update world regulatory domain
[   71.123094] 
[   71.123107] yenta_cardbus 0000:02:04.0: pcmcia: parent PCI bridge window: [mem 0xe8100000-0xe97fffff]
[   71.123114] pcmcia_socket pcmcia_socket0: cs: memory probe 0xe8100000-0xe97fffff: excluding 0xe8100000-0xe826ffff 0xe83e0000-0xe882ffff
[   71.123132] yenta_cardbus 0000:02:04.0: pcmcia: parent PCI bridge window: [mem 0x20000000-0x27ffffff pref]
[   71.123136] pcmcia_socket pcmcia_socket0: cs: memory probe 0x20000000-0x27ffffff: excluding 0x20000000-0x27ffffff
[   71.135980] yenta_cardbus 0000:02:04.1: CardBus bridge found [103c:006d]
[   71.136047] yenta_cardbus 0000:02:04.1: Using CSCINT to route CSC interrupts to PCI
[   71.136051] yenta_cardbus 0000:02:04.1: Routing CardBus interrupts to PCI
[   71.136057] yenta_cardbus 0000:02:04.1: TI: mfunc 0x01111d22, devctl 0x64
[   71.285047] cfg80211: World regulatory domain updated:
[   71.285054] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   71.285060] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   71.285064] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   71.285068] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   71.285072] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   71.285076] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   71.368582] yenta_cardbus 0000:02:04.1: ISA IRQ mask 0x0c38, PCI irq 18
[   71.368589] yenta_cardbus 0000:02:04.1: Socket status: 30000006
[   71.368595] pci_bus 0000:02: Raising subordinate bus# of parent bus (#02) from #06 to #0a
[   71.368607] yenta_cardbus 0000:02:04.1: pcmcia: parent PCI bridge window: [io  0x3000-0x7fff]
[   71.368613] pcmcia_socket pcmcia_socket1: cs: IO port probe 0x3000-0x7fff: excluding 0x3000-0x30ff 0x3400-0x34ff 0x3800-0x38ff 0x3c00-0x3cff 0x7000-0x70ff 0x7400-0x743f
[   71.382115] yenta_cardbus 0000:02:04.1: pcmcia: parent PCI bridge window: [mem 0xe8100000-0xe97fffff]
[   71.382120] pcmcia_socket pcmcia_socket1: cs: memory probe 0xe8100000-0xe97fffff: excluding 0xe8100000-0xe826ffff 0xe83e0000-0xe882ffff 0xe8b10000-0xe90cffff
[   71.382138] yenta_cardbus 0000:02:04.1: pcmcia: parent PCI bridge window: [mem 0x20000000-0x27ffffff pref]
[   71.382143] pcmcia_socket pcmcia_socket1: cs: memory probe 0x20000000-0x27ffffff: excluding 0x20000000-0x27ffffff
[   71.496947] ppdev: user-space parallel port driver
[   71.635262] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x100-0x3af: excluding nothing: probe failed.
[   71.635353] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x3e0-0x4ff: excluding nothing: probe failed.
[   71.635417] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x820-0x8ff: excluding nothing: probe failed.
[   71.635477] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xc00-0xcf7: excluding nothing: probe failed.
[   71.635540] pcmcia_socket pcmcia_socket0: cs: memory probe 0x0c0000-0x0fffff: excluding 0xc0000-0xfffff
[   71.635596] pcmcia_socket pcmcia_socket0: cs: memory probe 0xa0000000-0xa0ffffff: excluding 0xa0000000-0xa0ffffff
[   71.635650] pcmcia_socket pcmcia_socket0: cs: memory probe 0x60000000-0x60ffffff: excluding 0x60000000-0x60ffffff
[   71.635708] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xa00-0xaff: excluding nothing: probe failed.
[   71.635944] pcmcia_socket pcmcia_socket1: cs: IO port probe 0x100-0x3af: excluding nothing: probe failed.
[   71.636075] pcmcia_socket pcmcia_socket1: cs: IO port probe 0x3e0-0x4ff: excluding nothing: probe failed.
[   71.636138] pcmcia_socket pcmcia_socket1: cs: IO port probe 0x820-0x8ff: excluding nothing: probe failed.
[   71.636197] pcmcia_socket pcmcia_socket1: cs: IO port probe 0xc00-0xcf7: excluding nothing: probe failed.
[   71.636259] pcmcia_socket pcmcia_socket1: cs: memory probe 0x0c0000-0x0fffff: excluding 0xc0000-0xfffff
[   71.636314] pcmcia_socket pcmcia_socket1: cs: memory probe 0xa0000000-0xa0ffffff: excluding 0xa0000000-0xa0ffffff
[   71.636369] pcmcia_socket pcmcia_socket1: cs: memory probe 0x60000000-0x60ffffff: excluding 0x60000000-0x60ffffff
[   71.636424] pcmcia_socket pcmcia_socket1: cs: IO port probe 0xa00-0xaff: excluding nothing: probe failed.
[   71.847906] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
[   71.903223] b43-phy0: Broadcom 4306 WLAN found (core revision 5)
[   71.948274] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
[   71.948282] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[   71.948286] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
[   71.948291] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[   71.948294] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
[   71.948298] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[   71.948301] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
[   71.948305] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[   71.948309] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
[   71.948313] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[   71.948316] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
[   71.948320] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[   71.948323] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
[   71.948327] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[   71.948331] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
[   71.948335] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[   71.948338] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
[   71.948342] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[   71.948345] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
[   71.948349] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[   71.948353] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
[   71.948357] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[   71.948360] cfg80211: Updating information on frequency 2467 MHz for a 20 MHz width channel with regulatory rule:
[   71.948364] cfg80211: 2457000 KHz - 2482000 KHz @  KHz), (300 mBi, 2000 mBm)
[   71.948367] cfg80211: Updating information on frequency 2472 MHz for a 20 MHz width channel with regulatory rule:
[   71.948371] cfg80211: 2457000 KHz - 2482000 KHz @  KHz), (300 mBi, 2000 mBm)
[   71.948375] cfg80211: Updating information on frequency 2484 MHz for a 20 MHz width channel with regulatory rule:
[   71.948379] cfg80211: 2474000 KHz - 2494000 KHz @  KHz), (300 mBi, 2000 mBm)
[   72.140802] nvidia: module license 'NVIDIA' taints kernel.
[   72.140809] Disabling lock debugging due to kernel taint
[   72.692420] nvidia 0000:01:00.0: power state changed by ACPI to D0
[   72.692430] nvidia 0000:01:00.0: power state changed by ACPI to D0
[   72.692617] ACPI: PCI Interrupt Link [LNK5] enabled at IRQ 16
[   72.692640] nvidia 0000:01:00.0: PCI INT A -> Link[LNK5] -> GSI 16 (level, low) -> IRQ 16
[   72.692653] vgaarb: device changed decodes: PCI:0000:01:00.0,olddecodes=io+mem,decodes=none:owns=io+mem
[   72.695211] NVRM: loading NVIDIA Linux x86 Kernel Module  96.43.20  Sun Jul 17 23:28:58 PDT 2011
[   72.701097] ieee80211 phy0: Selected rate control algorithm 'minstrel_ht'
[   72.701979] Registered led device: b43-phy0::tx
[   72.702012] Registered led device: b43-phy0::rx
[   72.702041] Registered led device: b43-phy0::radio
[   72.702067] Broadcom 43xx driver loaded [ Features: PNL, Firmware-ID: FW13 ]
[   72.910990] ACPI: PCI Interrupt Link [LACI] enabled at IRQ 21
[   72.911001] Intel ICH 0000:00:06.0: PCI INT A -> Link[LACI] -> GSI 21 (level, low) -> IRQ 21
[   72.911037] Intel ICH 0000:00:06.0: setting latency timer to 64
[   73.142451] type=1400 audit(1329492216.427:5): apparmor="STATUS" operation="profile_load" name="/usr/lib/lightdm/lightdm-guest-session-wrapper" pid=976 comm="apparmor_parser"
[   73.146534] type=1400 audit(1329492216.431:6): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=980 comm="apparmor_parser"
[   73.152829] type=1400 audit(1329492216.439:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=980 comm="apparmor_parser"
[   73.160963] type=1400 audit(1329492216.447:: apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=980 comm="apparmor_parser"
[   73.207138] type=1400 audit(1329492216.491:9): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince" pid=983 comm="apparmor_parser"
[   73.230870] type=1400 audit(1329492216.515:10): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince-previewer" pid=983 comm="apparmor_parser"
[   73.236712] type=1400 audit(1329492216.523:11): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince-thumbnailer" pid=983 comm="apparmor_parser"
[   73.358365] 8139too 0000:02:01.0: eth0: link down
[   73.358930] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   73.529144] init: failsafe main process (929) killed by TERM signal
[   73.600113] init: apport pre-start process (1023) terminated with status 1
[   73.606396] init: alsa-restore main process (1029) terminated with status 19
[   73.649965] init: apport post-stop process (1052) terminated with status 1
[   73.652262] b43-phy0: Loading firmware version 508.1084 (2009-01-14 01:32:01)
[   73.691225] floppy0: no floppy controllers found
[   73.732282] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   73.836053] intel8x0_measure_ac97_clock: measured 55355 usecs (2688 samples)
[   73.836059] intel8x0: clocking to 47447
[   74.262647] init: udev-fallback-graphics main process (1090) terminated with status 1
[   74.296955] init: friendly-recovery post-stop process (404) terminated with status 1
[   74.345139] Bluetooth: Core ver 2.16
[   74.345203] NET: Registered protocol family 31
[   74.345206] Bluetooth: HCI device and connection manager initialized
[   74.345211] Bluetooth: HCI socket layer initialized
[   74.345213] Bluetooth: L2CAP socket layer initialized
[   74.349654] Bluetooth: SCO socket layer initialized
[   74.394434] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   74.394439] Bluetooth: BNEP filters: protocol multicast
[   75.716297] agpgart-amd64 0000:00:00.0: AGP 2.0 bridge
[   75.716319] agpgart-amd64 0000:00:00.0: putting AGP V2 device into 4x mode
[   75.716371] nvidia 0000:01:00.0: putting AGP V2 device into 4x mode
[   75.979601] cfg80211: Found new beacon on frequency: 2472 MHz (Ch 13) on phy0
[   76.467553] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,commit=0
[   76.674380] init: plymouth-stop pre-start process (1254) terminated with status 1
[   78.152098] wlan0: authenticate with 00:1f:33:36:7c:15 (try 1)
[   78.153575] wlan0: authenticated
[   78.176098] wlan0: associate with 00:1f:33:36:7c:15 (try 1)
[   78.178419] wlan0: RX AssocResp from 00:1f:33:36:7c:15 (capab=0x411 status=0 aid=7)
[   78.178426] wlan0: associated
[   78.179790] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   79.301638] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,commit=0
[   88.352032] wlan0: no IPv6 routers present
) terminated with status 1
[   78.152098] wlan0: authenticate with 00:1f:33:36:7c:15 (try 1)
[   78.153575] wlan0: authenticated
[   78.176098] wlan0: associate with 00:1f:33:36:7c:15 (try 1)
[   78.178419] wlan0: RX AssocResp from 00:1f:33:36:7c:15 (capab=0x411 status=0 aid=7)
[   78.178426] wlan0: associated
[   78.179790] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   79.301638] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,commit=0
[   88.352032] wlan0: no IPv6 routers present
```

---

### Post by Jolimont on 2012-02-17
Here's the syslog output:


```
[    0.279993] pci 0000:00:0b.0:   bridge window [io  disabled]
[    0.279993] pci 0000:00:0b.0:   bridge window [mem 0xea000000-0xeaffffff]
[    0.279993] pci 0000:00:0b.0:   bridge window [mem 0xf8000000-0xfc0fffff pref]
[    0.279993] pci 0000:00:0a.0: setting latency timer to 64
[    0.279993] ACPI: PCI Interrupt Link [LNK1] enabled at IRQ 19
[    0.279993] pci 0000:02:04.0: PCI INT A -> Link[LNK1] -> GSI 19 (level, low) -> IRQ 19
[    0.279993] ACPI: PCI Interrupt Link [LNK2] enabled at IRQ 18
[    0.279993] pci 0000:02:04.1: PCI INT B -> Link[LNK2] -> GSI 18 (level, low) -> IRQ 18
[    0.279993] pci_bus 0000:00: resource 4 [io  0x0000-0xffff]
[    0.279993] pci_bus 0000:00: resource 5 [mem 0x000a0000-0x000bffff]
[    0.279993] pci_bus 0000:00: resource 6 [mem 0x20000000-0xffffffff]
[    0.279993] pci_bus 0000:02: resource 0 [io  0x3000-0x7fff]
[    0.279993] pci_bus 0000:02: resource 1 [mem 0xe8100000-0xe97fffff]
[    0.279993] pci_bus 0000:02: resource 2 [mem 0x20000000-0x27ffffff pref]
[    0.279993] pci_bus 0000:03: resource 0 [io  0x3000-0x30ff]
[    0.279993] pci_bus 0000:03: resource 1 [io  0x3400-0x34ff]
[    0.279993] pci_bus 0000:03: resource 2 [mem 0x20000000-0x23ffffff pref]
[    0.279993] pci_bus 0000:07: resource 0 [io  0x3800-0x38ff]
[    0.279993] pci_bus 0000:07: resource 1 [io  0x3c00-0x3cff]
[    0.279993] pci_bus 0000:07: resource 2 [mem 0x24000000-0x27ffffff pref]
[    0.279993] pci_bus 0000:01: resource 1 [mem 0xea000000-0xeaffffff]
[    0.279993] pci_bus 0000:01: resource 2 [mem 0xf8000000-0xfc0fffff pref]
[    0.279993] NET: Registered protocol family 2
[    0.279993] IP route cache hash table entries: 4096 (order: 2, 16384 bytes)
[    0.280369] TCP established hash table entries: 16384 (order: 5, 131072 bytes)
[    0.280629] TCP bind hash table entries: 16384 (order: 5, 131072 bytes)
[    0.280871] TCP: Hash tables configured (established 16384 bind 16384)
[    0.280946] TCP reno registered
[    0.281017] UDP hash table entries: 256 (order: 1, 8192 bytes)
[    0.281101] UDP-Lite hash table entries: 256 (order: 1, 8192 bytes)
[    0.281354] NET: Registered protocol family 1
[    0.808110] PCI: CLS mismatch (32 != 64), using 64 bytes
[    0.808131] pci 0000:01:00.0: Boot video device
[    0.808222] Simple Boot Flag at 0x37 set to 0x1
[    0.808963] audit: initializing netlink socket (disabled)
[    0.809053] type=2000 audit(1329492143.804:1): initialized
[    0.869068] Trying to unpack rootfs image as initramfs...
[    0.940170] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    0.948591] VFS: Disk quotas dquot_6.5.2
[    0.948852] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.950837] fuse init (API version 7.16)
[    0.951162] msgmni has been set to 964
[    0.964507] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.968992] io scheduler noop registered
[    0.969070] io scheduler deadline registered
[    0.969212] io scheduler cfq registered (default)
[    0.969691] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.969841] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.971826] ACPI: Deprecated procfs I/F for AC is loaded, please retry with CONFIG_ACPI_PROCFS_POWER cleared
[    0.973084] ACPI: AC Adapter [ACAD] (on-line)
[    0.973345] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0
[    0.973446] ACPI: Power Button [PWRB]
[    0.973641] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input1
[    0.998207] ACPI: Lid Switch [LID]
[    0.998474] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input2
[    0.998572] ACPI: Power Button [PWRF]
[    0.998709] ACPI: acpi_idle registered with cpuidle
[    0.998778] Marking TSC unstable due to TSC halts in idle
[    1.039274] ACPI: Invalid active0 threshold
[    1.042288] thermal LNXTHERM:00: registered as thermal_zone0
[    1.042368] ACPI: Thermal Zone [THRM] (54 C)
[    1.042522] ACPI: Deprecated procfs I/F for battery is loaded, please retry with CONFIG_ACPI_PROCFS_POWER cleared
[    1.042673] ERST: Table is not found!
[    1.042938] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    1.046501] ACPI: PCI Interrupt Link [LMCI] enabled at IRQ 22
[    1.046608] serial 0000:00:06.1: PCI INT B -> Link[LMCI] -> GSI 22 (level, low) -> IRQ 22
[    1.046710] serial 0000:00:06.1: PCI INT B disabled
[    1.047158] Linux agpgart interface v0.103
[    1.047285] agpgart-amd64 0000:00:00.0: AGP bridge [10de/00d1]
[    1.047366] agpgart-amd64 0000:00:00.0: aperture size 4096 MB is not right, using settings from NB
[    1.047466] agpgart-amd64 0000:00:00.0: setting up Nforce3 AGP
[    1.060673] isapnp: Scanning for PnP cards...
[    1.113117] agpgart-amd64 0000:00:00.0: AGP aperture is 128M @ 0xf0000000
[    1.121097] brd: module loaded
[    1.122796] loop: module loaded
[    1.123412] pata_acpi 0000:00:08.0: setting latency timer to 64
[    1.129413] Fixed MDIO Bus: probed
[    1.129572] PPP generic driver version 2.4.2
[    1.129786] tun: Universal TUN/TAP device driver, 1.6
[    1.129858] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    1.130163] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    1.130672] ACPI: PCI Interrupt Link [LUS2] enabled at IRQ 21
[    1.130780] ehci_hcd 0000:00:02.2: PCI INT C -> Link[LUS2] -> GSI 21 (level, low) -> IRQ 21
[    1.130903] ehci_hcd 0000:00:02.2: setting latency timer to 64
[    1.130911] ehci_hcd 0000:00:02.2: EHCI Host Controller
[    1.131078] ehci_hcd 0000:00:02.2: new USB bus registered, assigned bus number 1
[    1.131227] ehci_hcd 0000:00:02.2: cache line size of 64 is not supported
[    1.131269] ehci_hcd 0000:00:02.2: irq 21, io mem 0xe8004000
[    1.179927] ehci_hcd 0000:00:02.2: USB 2.0 started, EHCI 1.00
[    1.268461] hub 1-0:1.0: USB hub found
[    1.268547] hub 1-0:1.0: 6 ports detected
[    1.268812] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    1.269292] ACPI: PCI Interrupt Link [LUS0] enabled at IRQ 20
[    1.269398] ohci_hcd 0000:00:02.0: PCI INT A -> Link[LUS0] -> GSI 20 (level, low) -> IRQ 20
[    1.269522] ohci_hcd 0000:00:02.0: setting latency timer to 64
[    1.269530] ohci_hcd 0000:00:02.0: OHCI Host Controller
[    1.269710] ohci_hcd 0000:00:02.0: new USB bus registered, assigned bus number 2
[    1.269857] ohci_hcd 0000:00:02.0: irq 20, io mem 0xe8000000
[    1.452486] hub 2-0:1.0: USB hub found
[    1.452573] hub 2-0:1.0: 3 ports detected
[    1.454524] ACPI: PCI Interrupt Link [LUS1] enabled at IRQ 22
[    1.454612] ohci_hcd 0000:00:02.1: PCI INT B -> Link[LUS1] -> GSI 22 (level, low) -> IRQ 22
[    1.454735] ohci_hcd 0000:00:02.1: setting latency timer to 64
[    1.454744] ohci_hcd 0000:00:02.1: OHCI Host Controller
[    1.454971] ohci_hcd 0000:00:02.1: new USB bus registered, assigned bus number 3
[    1.455126] ohci_hcd 0000:00:02.1: irq 22, io mem 0xe8001000
[    1.510561] hub 3-0:1.0: USB hub found
[    1.510649] hub 3-0:1.0: 3 ports detected
[    1.510919] uhci_hcd: USB Universal Host Controller Interface driver
[    1.511220] i8042: PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    1.520597] i8042: Detected active multiplexing controller, rev 1.1
[    1.566129] isapnp: No Plug & Play device found
[    1.584880] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.584972] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[    1.585048] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[    1.585124] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[    1.585202] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[    1.585520] mousedev: PS/2 mouse device common for all mice
[    1.585971] rtc_cmos 00:06: RTC can wake from S4
[    1.586231] rtc_cmos 00:06: rtc core: registered rtc_cmos as rtc0
[    1.586334] rtc0: alarms up to one year, y3k, 114 bytes nvram
[    1.586700] device-mapper: uevent: version 1.0.3
[    1.587002] device-mapper: ioctl: 4.20.0-ioctl (2011-02-02) initialised: [email]dm-devel@redhat.com[/email]
[    1.587189] EISA: Probing bus 0 at eisa.0
[    1.587261] EISA: Cannot allocate resource for mainboard
[    1.587335] Cannot allocate resource for EISA slot 1
[    1.587408] Cannot allocate resource for EISA slot 2
[    1.587480] Cannot allocate resource for EISA slot 3
[    1.587553] Cannot allocate resource for EISA slot 4
[    1.587625] Cannot allocate resource for EISA slot 5
[    1.587698] Cannot allocate resource for EISA slot 6
[    1.587770] Cannot allocate resource for EISA slot 7
[    1.587843] Cannot allocate resource for EISA slot 8
[    1.589155] EISA: Detected 0 cards.
[    1.597012] cpufreq-nforce2: No nForce2 chipset.
[    1.597198] cpuidle: using governor ladder
[    1.597395] cpuidle: using governor menu
[    1.597465] EFI Variables Facility v0.08 2004-May-17
[    1.598237] TCP cubic registered
[    1.598740] NET: Registered protocol family 10
[    1.600346] NET: Registered protocol family 17
[    1.600464] Registering the dns_resolver key type
[    1.600574] Using IPI No-Shortcut mode
[    1.600909] PM: Hibernation image not present or could not be loaded.
[    1.600936] registered taskstats version 1
[    1.636408] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input3
[    1.660922] ACPI: Battery Slot [BAT1] (battery present)
[    1.884599] usb 2-1: new low speed USB device number 2 using ohci_hcd
[    2.174017] Freeing initrd memory: 13324k freed
[    2.208270]   Magic number: 0:665:386
[    2.208484] rtc_cmos 00:06: setting system clock to 2012-02-17 15:22:25 UTC (1329492145)
[    2.208582] powernow-k8: Found 1 AMD Athlon(tm) XP Processor 3000+ (1 cpu cores) (version 2.20.00)
[    2.231502] powernow-k8: fid 0x8 (1600 MHz), vid 0x6
[    2.231576] powernow-k8: fid 0x0 (800 MHz), vid 0x18
[    2.235829] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    2.235897] EDD information not available.
[    2.236125] Freeing unused kernel memory: 696k freed
[    2.236884] Write protecting the kernel text: 5340k
[    2.236997] Write protecting the kernel read-only data: 2192k
[    2.266950] udevd[77]: starting version 173
[    2.284103] usb 3-1: new low speed USB device number 2 using ohci_hcd
[    2.470082] pata_amd 0000:00:08.0: version 0.4.1
[    2.470145] pata_amd 0000:00:08.0: setting latency timer to 64
[    2.508569] scsi0 : pata_amd
[    2.512092] scsi1 : pata_amd
[    2.512832] ata1: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0x2080 irq 14
[    2.512904] ata2: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0x2088 irq 15
[    2.515987] ACPI: PCI Interrupt Link [LNK3] enabled at IRQ 17
[    2.539256] 8139cp: 8139cp: 10/100 PCI Ethernet driver v1.3 (Mar 22, 2004)
[    2.547533] b43-pci-bridge 0000:02:02.0: PCI INT A -> Link[LNK3] -> GSI 17 (level, low) -> IRQ 17
[    2.547669] ssb: Core 0 found: ChipCommon (cc 0x800, rev 0x04, vendor 0x4243)
[    2.547675] ssb: Core 1 found: IEEE 802.11 (cc 0x812, rev 0x05, vendor 0x4243)
[    2.547682] ssb: Core 2 found: PCMCIA (cc 0x80D, rev 0x02, vendor 0x4243)
[    2.547688] ssb: Core 3 found: V90 (cc 0x807, rev 0x02, vendor 0x4243)
[    2.547693] ssb: Core 4 found: PCI (cc 0x804, rev 0x09, vendor 0x4243)
[    2.551760] input: CHESEN PS2 to USB Converter as /devices/pci0000:00/0000:00:02.0/usb2/2-1/2-1:1.0/input/input4
[    2.551988] generic-usb 0003:0518:0001.0001: input,hidraw0: USB HID v1.10 Keyboard [CHESEN PS2 to USB Converter] on usb-0000:00:02.0-1/input0
[    2.553274] ssb: Sonics Silicon Backplane found on PCI device 0000:02:02.0
[    2.553396] 8139cp 0000:02:01.0: This (id 10ec:8139 rev 10) is not an 8139C+ compatible chip, use 8139too
[    2.561576] input: CHESEN PS2 to USB Converter as /devices/pci0000:00/0000:00:02.0/usb2/2-1/2-1:1.1/input/input5
[    2.561851] generic-usb 0003:0518:0001.0002: input,hidraw1: USB HID v1.10 Mouse [CHESEN PS2 to USB Converter] on usb-0000:00:02.0-1/input1
[    2.567979] input: Microsoft Microsoft 3-Button Mouse with IntelliEye(TM) as /devices/pci0000:00/0000:00:02.1/usb3/3-1/3-1:1.0/input/input6
[    2.568283] generic-usb 0003:045E:0040.0003: input,hidraw2: USB HID v1.10 Mouse [Microsoft Microsoft 3-Button Mouse with IntelliEye(TM)] on usb-0000:00:02.1-1/input0
[    2.568422] usbcore: registered new interface driver usbhid
[    2.568492] usbhid: USB HID core driver
[    2.732543] ata1.00: ATA-6: FUJITSU MHT2060AT PL, 0022, max UDMA/100
[    2.732620] ata1.00: 117210240 sectors, multi 16: LBA 
[    2.732696] ata1: nv_mode_filter: 0x3f39f&0x3f39f->0x3f39f, BIOS=0x3f000 (0xc6000000) ACPI=0x3f01f (20:600:0x13)
[    2.748465] ata1.00: configured for UDMA/100
[    2.748687] scsi 0:0:0:0: Direct-Access     ATA      FUJITSU MHT2060A 0022 PQ: 0 ANSI: 5
[    2.749016] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    2.749303] sd 0:0:0:0: [sda] 117210240 512-byte logical blocks: (60.0 GB/55.8 GiB)
[    2.749452] sd 0:0:0:0: [sda] Write Protect is off
[    2.749520] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    2.749549] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.880849]  sda: sda1 sda2 < sda5 >
[    2.881351] sd 0:0:0:0: [sda] Attached SCSI disk
[    2.912293] ata2.00: ATAPI: HL-DT-STCD-RW/DVD DRIVE GCC-4241N, 0C29, max MWDMA2
[    2.912390] ata2: nv_mode_filter: 0x39f&0x739f->0x39f, BIOS=0x0 (0xc6000000) ACPI=0x39f (120:600:0x12)
[    2.928220] ata2.00: configured for MWDMA2
[    2.934620] scsi 1:0:0:0: CD-ROM            HL-DT-ST RW/DVD GCC-4241N 0C29 PQ: 0 ANSI: 5
[    2.940641] sr0: scsi3-mmc drive: 24x/24x writer cd/rw xa/form2 cdda tray
[    2.940714] cdrom: Uniform CD-ROM driver Revision: 3.20
[    2.940950] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    2.941047] sr 1:0:0:0: Attached scsi generic sg1 type 5
[    2.942336] 8139too: 8139too Fast Ethernet driver 0.9.28
[    2.942465] 8139too 0000:02:01.0: PCI INT A -> Link[LNK2] -> GSI 18 (level, low) -> IRQ 18
[    2.948578] 8139too 0000:02:01.0: eth0: RealTek RTL8139 at 0x7000, 00:0f:b0:0f:3c:da, IRQ 18
[    3.426350] EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: (null)
[    5.512063] floppy0: no floppy controllers found
[   69.713204] udevd[504]: starting version 173
[   69.752310] Adding 521212k swap on /dev/sda5.  Priority:-1 extents:1 across:521212k 
[   70.162620] wmi: Mapper loaded
[   70.186504] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   70.381482] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A03:00/device:18/LNXVIDEO:00/input/input7
[   70.381615] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[   70.568845] parport_pc 00:0b: reported by Plug and Play ACPI
[   70.568899] parport0: PC-style at 0x378 (0x778), irq 7, dma 1 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
[   70.639436] lp: driver loaded but no devices found
[   70.664426] lp0: using parport0 (interrupt-driven).
[   70.705214] input: PS/2 Mouse as /devices/platform/i8042/serio4/input/input8
[   70.725131] input: AlpsPS/2 ALPS GlidePoint as /devices/platform/i8042/serio4/input/input9
[   70.746852] i2c i2c-0: nForce2 SMBus adapter at 0x2040
[   70.746921] i2c i2c-1: nForce2 SMBus adapter at 0x2000
[   70.755636] type=1400 audit(1329492214.039:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=716 comm="apparmor_parser"
[   70.756369] type=1400 audit(1329492214.043:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=716 comm="apparmor_parser"
[   70.756764] type=1400 audit(1329492214.043:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=716 comm="apparmor_parser"
[   70.759381] yenta_cardbus 0000:02:04.0: CardBus bridge found [103c:006d]
[   70.759403] yenta_cardbus 0000:02:04.0: CardBus bridge to [bus 03-06]
[   70.759408] yenta_cardbus 0000:02:04.0:   bridge window [io  0x3000-0x30ff]
[   70.759414] yenta_cardbus 0000:02:04.0:   bridge window [io  0x3400-0x34ff]
[   70.759420] yenta_cardbus 0000:02:04.0:   bridge window [mem 0x20000000-0x23ffffff pref]
[   70.759425] yenta_cardbus 0000:02:04.0:   bridge window [mem 0xe8400000-0xe87fffff]
[   70.759432] yenta_cardbus 0000:02:04.0: Enabling burst memory read transactions
[   70.759437] yenta_cardbus 0000:02:04.0: Using CSCINT to route CSC interrupts to PCI
[   70.759441] yenta_cardbus 0000:02:04.0: Routing CardBus interrupts to PCI
[   70.759447] yenta_cardbus 0000:02:04.0: TI: mfunc 0x01111d22, devctl 0x64
[   70.988645] yenta_cardbus 0000:02:04.0: ISA IRQ mask 0x0c38, PCI irq 19
[   70.988651] yenta_cardbus 0000:02:04.0: Socket status: 30000086
[   70.988657] pci_bus 0000:02: Raising subordinate bus# of parent bus (#02) from #02 to #06
[   70.988670] yenta_cardbus 0000:02:04.0: pcmcia: parent PCI bridge window: [io  0x3000-0x7fff]
[   70.988676] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x3000-0x7fff: excluding 0x3000-0x30ff 0x3400-0x34ff 0x3800-0x38ff 0x3c00-0x3cff 0x7000-0x70ff 0x7400-0x743f
[   71.099923] cfg80211: Calling CRDA to update world regulatory domain
[   71.123094] 
[   71.123107] yenta_cardbus 0000:02:04.0: pcmcia: parent PCI bridge window: [mem 0xe8100000-0xe97fffff]
[   71.123114] pcmcia_socket pcmcia_socket0: cs: memory probe 0xe8100000-0xe97fffff: excluding 0xe8100000-0xe826ffff 0xe83e0000-0xe882ffff
[   71.123132] yenta_cardbus 0000:02:04.0: pcmcia: parent PCI bridge window: [mem 0x20000000-0x27ffffff pref]
[   71.123136] pcmcia_socket pcmcia_socket0: cs: memory probe 0x20000000-0x27ffffff: excluding 0x20000000-0x27ffffff
[   71.135980] yenta_cardbus 0000:02:04.1: CardBus bridge found [103c:006d]
[   71.136047] yenta_cardbus 0000:02:04.1: Using CSCINT to route CSC interrupts to PCI
[   71.136051] yenta_cardbus 0000:02:04.1: Routing CardBus interrupts to PCI
[   71.136057] yenta_cardbus 0000:02:04.1: TI: mfunc 0x01111d22, devctl 0x64
[   71.285047] cfg80211: World regulatory domain updated:
[   71.285054] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   71.285060] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   71.285064] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   71.285068] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   71.285072] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   71.285076] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   71.368582] yenta_cardbus 0000:02:04.1: ISA IRQ mask 0x0c38, PCI irq 18
[   71.368589] yenta_cardbus 0000:02:04.1: Socket status: 30000006
[   71.368595] pci_bus 0000:02: Raising subordinate bus# of parent bus (#02) from #06 to #0a
[   71.368607] yenta_cardbus 0000:02:04.1: pcmcia: parent PCI bridge window: [io  0x3000-0x7fff]
[   71.368613] pcmcia_socket pcmcia_socket1: cs: IO port probe 0x3000-0x7fff: excluding 0x3000-0x30ff 0x3400-0x34ff 0x3800-0x38ff 0x3c00-0x3cff 0x7000-0x70ff 0x7400-0x743f
[   71.382115] yenta_cardbus 0000:02:04.1: pcmcia: parent PCI bridge window: [mem 0xe8100000-0xe97fffff]
[   71.382120] pcmcia_socket pcmcia_socket1: cs: memory probe 0xe8100000-0xe97fffff: excluding 0xe8100000-0xe826ffff 0xe83e0000-0xe882ffff 0xe8b10000-0xe90cffff
[   71.382138] yenta_cardbus 0000:02:04.1: pcmcia: parent PCI bridge window: [mem 0x20000000-0x27ffffff pref]
[   71.382143] pcmcia_socket pcmcia_socket1: cs: memory probe 0x20000000-0x27ffffff: excluding 0x20000000-0x27ffffff
[   71.496947] ppdev: user-space parallel port driver
[   71.635262] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x100-0x3af: excluding nothing: probe failed.
[   71.635353] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x3e0-0x4ff: excluding nothing: probe failed.
[   71.635417] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x820-0x8ff: excluding nothing: probe failed.
[   71.635477] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xc00-0xcf7: excluding nothing: probe failed.
[   71.635540] pcmcia_socket pcmcia_socket0: cs: memory probe 0x0c0000-0x0fffff: excluding 0xc0000-0xfffff
[   71.635596] pcmcia_socket pcmcia_socket0: cs: memory probe 0xa0000000-0xa0ffffff: excluding 0xa0000000-0xa0ffffff
[   71.635650] pcmcia_socket pcmcia_socket0: cs: memory probe 0x60000000-0x60ffffff: excluding 0x60000000-0x60ffffff
[   71.635708] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xa00-0xaff: excluding nothing: probe failed.
[   71.635944] pcmcia_socket pcmcia_socket1: cs: IO port probe 0x100-0x3af: excluding nothing: probe failed.
[   71.636075] pcmcia_socket pcmcia_socket1: cs: IO port probe 0x3e0-0x4ff: excluding nothing: probe failed.
[   71.636138] pcmcia_socket pcmcia_socket1: cs: IO port probe 0x820-0x8ff: excluding nothing: probe failed.
[   71.636197] pcmcia_socket pcmcia_socket1: cs: IO port probe 0xc00-0xcf7: excluding nothing: probe failed.
[   71.636259] pcmcia_socket pcmcia_socket1: cs: memory probe 0x0c0000-0x0fffff: excluding 0xc0000-0xfffff
[   71.636314] pcmcia_socket pcmcia_socket1: cs: memory probe 0xa0000000-0xa0ffffff: excluding 0xa0000000-0xa0ffffff
[   71.636369] pcmcia_socket pcmcia_socket1: cs: memory probe 0x60000000-0x60ffffff: excluding 0x60000000-0x60ffffff
[   71.636424] pcmcia_socket pcmcia_socket1: cs: IO port probe 0xa00-0xaff: excluding nothing: probe failed.
[   71.847906] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
[   71.903223] b43-phy0: Broadcom 4306 WLAN found (core revision 5)
[   71.948274] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
[   71.948282] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[   71.948286] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
[   71.948291] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[   71.948294] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
[   71.948298] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[   71.948301] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
[   71.948305] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[   71.948309] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
[   71.948313] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[   71.948316] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
[   71.948320] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[   71.948323] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
[   71.948327] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[   71.948331] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
[   71.948335] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[   71.948338] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
[   71.948342] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[   71.948345] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
[   71.948349] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[   71.948353] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
[   71.948357] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[   71.948360] cfg80211: Updating information on frequency 2467 MHz for a 20 MHz width channel with regulatory rule:
[   71.948364] cfg80211: 2457000 KHz - 2482000 KHz @  KHz), (300 mBi, 2000 mBm)
[   71.948367] cfg80211: Updating information on frequency 2472 MHz for a 20 MHz width channel with regulatory rule:
[   71.948371] cfg80211: 2457000 KHz - 2482000 KHz @  KHz), (300 mBi, 2000 mBm)
[   71.948375] cfg80211: Updating information on frequency 2484 MHz for a 20 MHz width channel with regulatory rule:
[   71.948379] cfg80211: 2474000 KHz - 2494000 KHz @  KHz), (300 mBi, 2000 mBm)
[   72.140802] nvidia: module license 'NVIDIA' taints kernel.
[   72.140809] Disabling lock debugging due to kernel taint
[   72.692420] nvidia 0000:01:00.0: power state changed by ACPI to D0
[   72.692430] nvidia 0000:01:00.0: power state changed by ACPI to D0
[   72.692617] ACPI: PCI Interrupt Link [LNK5] enabled at IRQ 16
[   72.692640] nvidia 0000:01:00.0: PCI INT A -> Link[LNK5] -> GSI 16 (level, low) -> IRQ 16
[   72.692653] vgaarb: device changed decodes: PCI:0000:01:00.0,olddecodes=io+mem,decodes=none:owns=io+mem
[   72.695211] NVRM: loading NVIDIA Linux x86 Kernel Module  96.43.20  Sun Jul 17 23:28:58 PDT 2011
[   72.701097] ieee80211 phy0: Selected rate control algorithm 'minstrel_ht'
[   72.701979] Registered led device: b43-phy0::tx
[   72.702012] Registered led device: b43-phy0::rx
[   72.702041] Registered led device: b43-phy0::radio
[   72.702067] Broadcom 43xx driver loaded [ Features: PNL, Firmware-ID: FW13 ]
[   72.910990] ACPI: PCI Interrupt Link [LACI] enabled at IRQ 21
[   72.911001] Intel ICH 0000:00:06.0: PCI INT A -> Link[LACI] -> GSI 21 (level, low) -> IRQ 21
[   72.911037] Intel ICH 0000:00:06.0: setting latency timer to 64
[   73.142451] type=1400 audit(1329492216.427:5): apparmor="STATUS" operation="profile_load" name="/usr/lib/lightdm/lightdm-guest-session-wrapper" pid=976 comm="apparmor_parser"
[   73.146534] type=1400 audit(1329492216.431:6): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=980 comm="apparmor_parser"
[   73.152829] type=1400 audit(1329492216.439:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=980 comm="apparmor_parser"
[   73.160963] type=1400 audit(1329492216.447:8): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=980 comm="apparmor_parser"
[   73.207138] type=1400 audit(1329492216.491:9): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince" pid=983 comm="apparmor_parser"
[   73.230870] type=1400 audit(1329492216.515:10): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince-previewer" pid=983 comm="apparmor_parser"
[   73.236712] type=1400 audit(1329492216.523:11): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince-thumbnailer" pid=983 comm="apparmor_parser"
[   73.358365] 8139too 0000:02:01.0: eth0: link down
[   73.358930] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   73.529144] init: failsafe main process (929) killed by TERM signal
[   73.600113] init: apport pre-start process (1023) terminated with status 1
[   73.606396] init: alsa-restore main process (1029) terminated with status 19
[   73.649965] init: apport post-stop process (1052) terminated with status 1
[   73.652262] b43-phy0: Loading firmware version 508.1084 (2009-01-14 01:32:01)
[   73.691225] floppy0: no floppy controllers found
[   73.732282] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   73.836053] intel8x0_measure_ac97_clock: measured 55355 usecs (2688 samples)
[   73.836059] intel8x0: clocking to 47447
[   74.262647] init: udev-fallback-graphics main process (1090) terminated with status 1
[   74.296955] init: friendly-recovery post-stop process (404) terminated with status 1
[   74.345139] Bluetooth: Core ver 2.16
[   74.345203] NET: Registered protocol family 31
[   74.345206] Bluetooth: HCI device and connection manager initialized
[   74.345211] Bluetooth: HCI socket layer initialized
[   74.345213] Bluetooth: L2CAP socket layer initialized
[   74.349654] Bluetooth: SCO socket layer initialized
[   74.394434] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   74.394439] Bluetooth: BNEP filters: protocol multicast
[   75.716297] agpgart-amd64 0000:00:00.0: AGP 2.0 bridge
[   75.716319] agpgart-amd64 0000:00:00.0: putting AGP V2 device into 4x mode
[   75.716371] nvidia 0000:01:00.0: putting AGP V2 device into 4x mode
[   75.979601] cfg80211: Found new beacon on frequency: 2472 MHz (Ch 13) on phy0
[   76.467553] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,commit=0
[   76.674380] init: plymouth-stop pre-start process (1254) terminated with status 1
[   78.152098] wlan0: authenticate with 00:1f:33:36:7c:15 (try 1)
[   78.153575] wlan0: authenticated
[   78.176098] wlan0: associate with 00:1f:33:36:7c:15 (try 1)
[   78.178419] wlan0: RX AssocResp from 00:1f:33:36:7c:15 (capab=0x411 status=0 aid=7)
[   78.178426] wlan0: associated
[   78.179790] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   79.301638] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,commit=0
[   88.352032] wlan0: no IPv6 routers present
```

---

### Post by Jolimont on 2012-02-18
Bump, any suggestions as to what might get me stuck please?

---

### Post by stinkeye on 2012-02-18
I was having a similar problemm on a previous release and
thought my drive was failing but was told it was probably a boot "race condition".
What worked for me was to force an fsck every boot,
Which had the effect of slowing down the boot process.
Adds about 10 secs to boot but better than going in to safe mode.

Run this to check every boot
```
sudo tune2fs -c 1 /dev/[COLOR="DarkOrange"]sdxx[/COLOR]
```

Change to your [COLOR="darkorange"]Ubuntu partition[/COLOR].

To find your partition use...
```
sudo blkid
```


To revert back use 
```
sudo tune2fs -c 50 /dev/[COLOR="DarkOrange"]sdxx[/COLOR]
```

---

### Post by Jolimont on 2012-02-18
Thanks, I tried that and it didn't seem to do very much:

annie@annie-Presario-R3200-PM008UA-ABA:~$ sudo tune2fs -c 1 /dev/sdxx
[sudo] password for annie: 
tune2fs 1.41.14 (22-Dec-2010)
tune2fs: No such file or directory while trying to open /dev/sdxx
Couldn't find valid filesystem superblock.
annie@annie-Presario-R3200-PM008UA-ABA:~$ sudo blkid
/dev/sda1: UUID="6b6905f6-e7ca-439c-b3e1-11c8543c2210" TYPE="ext4" 
/dev/sda5: UUID="45c1be51-deae-4dbe-b92f-32d5a228560b" TYPE="swap" 
annie@annie-Presario-R3200-PM008UA-ABA:~$ sudo tune2fs -c 50 /dev/sdxx
tune2fs 1.41.14 (22-Dec-2010)
tune2fs: No such file or directory while trying to open /dev/sdxx
Couldn't find valid filesystem superblock.
annie@annie-Presario-R3200-PM008UA-ABA:~$ 

I'm thinking maybe find a linux distribution that plays nicer with old hardware? xubuntu or tinyme?

---

### Post by stinkeye on 2012-02-18
This was to show your ubuntu partition to use...
```
annie@annie-Presario-R3200-PM008UA-ABA:~$ sudo blkid
 [COLOR="DarkOrange"]/dev/sda1[/COLOR]: UUID="6b6905f6-e7ca-439c-b3e1-11c8543c2210" TYPE="ext4" 
 /dev/sda5: UUID="45c1be51-deae-4dbe-b92f-32d5a228560b" TYPE="swap"
```


So from your blkid output you need to run...
```
sudo tune2fs -c 1 [COLOR="DarkOrange"]/dev/sda1[/COLOR]
```

---

### Post by Jolimont on 2012-02-19
Doh! Now I see what you mean Stinkeye! Sorry, new to this, slowwwwwww ;-)

But, first time I rebooted after running the command line it went into a check of some sort, then booted right up. Will now boot and reboot several times to make sure it wasn't a fluke. Thanks, that's great progress already!

---

### Post by Jolimont on 2012-02-19
Dang it, maybe it was just a fluke. I can't get it to do it again, it hangs!!! Will not give up. Any other suggestions?

---

### Post by stinkeye on 2012-02-19
> **Jolimont said:**
> Dang it, maybe it was just a fluke. I can't get it to do it again, it hangs!!! Will not give up. Any other suggestions?

I have seen a few threads where some users have had luck 
with disabling the splash screen.
This will show a text readout while booting.

Open grub in gedit in the terminal...
```
gksudo gedit /etc/default/grub
```


Locate the line...
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
```


and change to...
```
GRUB_CMDLINE_LINUX_DEFAULT=""
```

Save and close gedit.


Then you need to update grub.
In the terminal..
```
sudo update-grub
```

Reboot and see what happens. [-o<

---

### Post by Jolimont on 2012-02-19
Nope, pray harder Stinkeye!

Tried to reboot at least 10 times, will not do it. I repeat: I will not give up!!!! Thanks for the suggestions, much appreciated!

---

### Post by Jolimont on 2012-02-20
Booted right up (in safe mode) this morning. Maybe it just needed some sleep. Hope it enjoyed the sleep, I WON'T TURN IT OFF AGAIN!!! :twisted::twisted:

---

### Post by goinglinux on 2012-02-21
Hardware, huh?

I read through your post here, then Google searched for  "Linux Presario R3200-PM008UA-ABA" I found just one other post, also  from the Ubuntu forums where someone (with an R3000) was having a  hardware problem. The wireless card. 

Is there a hardware switch that lets you turn off the wireless? If so,  try leaving wireless turned off so that the driver doesn't try to load.  If that gives you consistent and reliable booting, then you might find  some help here: [http://ubuntuforums.org/showthread.php?t=1356628](http://ubuntuforums.org/showthread.php?t=1356628). 

If not, then you could try removing all of the RAM and let the computer  boot with just the base level RAM. I've seen RAM memory cards go bad and  interfere with booting. One last thing to try. It's possible that the  little watch battery that powers the CMOS (it runs the computer's clock  and a few other critical things) has died and it needs a new one.

---

