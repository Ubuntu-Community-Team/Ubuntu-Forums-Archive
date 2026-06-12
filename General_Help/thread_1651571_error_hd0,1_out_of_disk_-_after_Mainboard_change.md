---
title: "error: hd0,1 out of disk - after Mainboard change"
date: 2010-12-23
forum: General Help
---

### Post by mcemsi on 2010-12-23
Hi,

2 hours ago i installed another Mainboard on my system.
When I try to boot My Ubuntu 10.10 I keep getting the following errors:

error:hd0,1 out of disk
error: couldn't read file
eroor: you neet to load kernel first

Failed to boot both default and fallback entries.

Can anybody help me please?


TIA 
mcemsi

---

### Post by psusi on 2010-12-23
Boot the livecd and paste the output of sudo fdisk -lu and dmesg.  Please use [code] tags since it will be quite long.

---

### Post by mcemsi on 2010-12-23
```
ubuntu@ubuntu:~$ sudo fdisk -lu

Platte /dev/sda: 1500.3 GByte, 1500301910016 Byte
255 Köpfe, 63 Sektoren/Spur, 182401 Zylinder, zusammen 2930277168 Sektoren
Einheiten = Sektoren von 1 × 512 = 512 Bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0008c1d6

   Gerät  boot.     Anfang        Ende     Blöcke   Id  System
/dev/sda1   *        2048   488282111   244140032   83  Linux
/dev/sda2       488284158   494141439     2928641    5  Erweiterte
/dev/sda3       494143335  2542157729  1024007197+   b  W95 FAT32
/dev/sda5       488284160   494141439     2928640   82  Linux Swap / Solaris
```

```
[    0.004683] Performance Events: AMD PMU driver.
[    0.004714] ... version:                0
[    0.004718] ... bit width:              48
[    0.004722] ... generic registers:      4
[    0.004726] ... value mask:             0000ffffffffffff
[    0.004731] ... max period:             00007fffffffffff
[    0.004736] ... fixed-purpose events:   0
[    0.004740] ... event mask:             000000000000000f
[    0.005906] SMP alternatives: switching to UP code
[    0.018377] Freeing SMP alternatives: 24k freed
[    0.018439] ACPI: Core revision 20100428
[    0.026472] ftrace: converting mcount calls to 0f 1f 44 00 00
[    0.026489] ftrace: allocating 21758 entries in 43 pages
[    0.028212] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.028527] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.069467] CPU0: AMD Geode(tm) NX 1750+ stepping 01
[    0.072000] Brought up 1 CPUs
[    0.072000] Total of 1 processors activated (2820.44 BogoMIPS).
[    0.072000] devtmpfs: initialized
[    0.072000] regulator: core version 0.5
[    0.072000] Time: 22:55:33  Date: 12/23/10
[    0.072000] NET: Registered protocol family 16
[    0.072000] EISA bus registered
[    0.072000] ACPI: bus type pci registered
[    0.073454] PCI: PCI BIOS revision 2.10 entry at 0xfdb31, last bus=2
[    0.073459] PCI: Using configuration type 1 for base access
[    0.075265] bio: create slab <bio-0> at 0
[    0.076349] ACPI: EC: Look up EC in DSDT
[    0.083576] ACPI: Interpreter enabled
[    0.083583] ACPI: (supports S0 S1 S4 S5)
[    0.083617] ACPI: Using IOAPIC for interrupt routing
[    0.089813] ACPI: Power Resource [URP1] (off)
[    0.089865] ACPI: Power Resource [URP2] (off)
[    0.089909] ACPI: Power Resource [FDDP] (off)
[    0.089951] ACPI: Power Resource [LPTP] (off)
[    0.090141] ACPI: No dock devices found.
[    0.090150] PCI: Ignoring host bridge windows from ACPI; if necessary, use "pci=use_crs" and report a bug
[    0.090352] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-ff])
[    0.090719] pci_root PNP0A03:00: host bridge window [io  0x0000-0x0cf7] (ignored)
[    0.090726] pci_root PNP0A03:00: host bridge window [io  0x0d00-0xffff] (ignored)
[    0.090731] pci_root PNP0A03:00: host bridge window [mem 0x000a0000-0x000bffff] (ignored)
[    0.090736] pci_root PNP0A03:00: host bridge window [mem 0x000cb000-0x000dffff] (ignored)
[    0.090741] pci_root PNP0A03:00: host bridge window [mem 0x1c000000-0xffdfffff] (ignored)
[    0.090746] pci_root PNP0A03:00: host bridge window [mem 0xfee01000-0xffdfffff] (ignored)
[    0.090789] pci 0000:00:00.0: reg 10: [mem 0xd0000000-0xd3ffffff]
[    0.090970] pci 0000:00:02.0: Enabling SiS 96x SMBus
[    0.091031] pci 0000:00:02.1: reg 20: [io  0x0c00-0x0c1f]
[    0.091104] pci 0000:00:02.5: reg 20: [io  0xff00-0xff0f]
[    0.091167] pci 0000:00:02.7: reg 10: [io  0xdc00-0xdcff]
[    0.091177] pci 0000:00:02.7: reg 14: [io  0xd800-0xd87f]
[    0.091231] pci 0000:00:02.7: supports D1 D2
[    0.091235] pci 0000:00:02.7: PME# supported from D3hot D3cold
[    0.091243] pci 0000:00:02.7: PME# disabled
[    0.091276] pci 0000:00:03.0: reg 10: [mem 0xcfff9000-0xcfff9fff]
[    0.091345] pci 0000:00:03.1: reg 10: [mem 0xcfffa000-0xcfffafff]
[    0.091422] pci 0000:00:03.2: reg 10: [mem 0xcfffb000-0xcfffbfff]
[    0.091479] pci 0000:00:03.2: PME# supported from D0 D3hot D3cold
[    0.091485] pci 0000:00:03.2: PME# disabled
[    0.091535] pci 0000:00:04.0: reg 10: [io  0xd400-0xd4ff]
[    0.091545] pci 0000:00:04.0: reg 14: [mem 0xcfff8000-0xcfff8fff]
[    0.091578] pci 0000:00:04.0: reg 30: [mem 0xfffe0000-0xffffffff pref]
[    0.091603] pci 0000:00:04.0: supports D1 D2
[    0.091607] pci 0000:00:04.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.091613] pci 0000:00:04.0: PME# disabled
[    0.091712] pci 0000:01:00.0: reg 10: [mem 0xc0000000-0xc7ffffff pref]
[    0.091720] pci 0000:01:00.0: reg 14: [mem 0xcfee0000-0xcfefffff]
[    0.091729] pci 0000:01:00.0: reg 18: [io  0xbc00-0xbc7f]
[    0.091769] pci 0000:01:00.0: supports D1 D2
[    0.091813] pci 0000:00:01.0: PCI bridge to [bus 01-02]
[    0.091822] pci 0000:00:01.0:   bridge window [io  0xb000-0xbfff]
[    0.091829] pci 0000:00:01.0:   bridge window [mem 0xcfd00000-0xcfefffff]
[    0.091837] pci 0000:00:01.0:   bridge window [mem 0xbfa00000-0xcfbfffff pref]
[    0.091850] pci_bus 0000:00: on NUMA node 0
[    0.091856] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.105981] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 10 *11 12 14 15)
[    0.106149] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[    0.106313] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 *10 11 12 14 15)
[    0.106486] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 10 *11 12 14 15)
[    0.106652] ACPI: PCI Interrupt Link [LNKE] (IRQs *3 4 5 6 7 10 11 12 14 15)
[    0.106819] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 *5 6 7 10 11 12 14 15)
[    0.106985] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[    0.107148] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 10 11 *12 14 15)
[    0.107218] HEST: Table is not found!
[    0.107407] vgaarb: device added: PCI:0000:01:00.0,decodes=io+mem,owns=io+mem,locks=none
[    0.107412] vgaarb: loaded
[    0.107763] SCSI subsystem initialized
[    0.107935] libata version 3.00 loaded.
[    0.108058] usbcore: registered new interface driver usbfs
[    0.108091] usbcore: registered new interface driver hub
[    0.108150] usbcore: registered new device driver usb
[    0.108441] ACPI: WMI: Mapper loaded
[    0.108446] PCI: Using ACPI for IRQ routing
[    0.108485] PCI: pci_cache_line_size set to 32 bytes
[    0.108561] reserve RAM buffer: 000000000009fc00 - 000000000009ffff 
[    0.108567] reserve RAM buffer: 000000001bff0000 - 000000001bffffff 
[    0.108775] NetLabel: Initializing
[    0.108779] NetLabel:  domain hash size = 128
[    0.108782] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.108811] NetLabel:  unlabeled traffic allowed by default
[    0.108900] Switching to clocksource tsc
[    0.128154] AppArmor: AppArmor Filesystem Enabled
[    0.128200] pnp: PnP ACPI init
[    0.128247] ACPI: bus type pnp registered
[    0.132273] pnp: PnP ACPI: found 11 devices
[    0.132278] ACPI: ACPI bus type pnp unregistered
[    0.132284] PnPBIOS: Disabled by ACPI PNP
[    0.132314] system 00:01: [io  0x04d0-0x04d1] has been reserved
[    0.132320] system 00:01: [io  0x0295-0x0296] has been reserved
[    0.132325] system 00:01: [io  0x0800-0x087f] has been reserved
[    0.132330] system 00:01: [io  0x0880-0x08ff] has been reserved
[    0.132334] system 00:01: [io  0x0c00-0x0c1f] has been reserved
[    0.132341] system 00:01: [mem 0xfee00000-0xfee00fff] has been reserved
[    0.169681] pci 0000:00:04.0: address space collision: [mem 0xfffe0000-0xffffffff pref] conflicts with reserved [mem 0xfffc0000-0xffffffff]
[    0.169716] pci 0000:00:04.0: BAR 6: assigned [mem 0x1c000000-0x1c01ffff pref]
[    0.169724] pci 0000:00:01.0: PCI bridge to [bus 01-02]
[    0.169731] pci 0000:00:01.0:   bridge window [io  0xb000-0xbfff]
[    0.169742] pci 0000:00:01.0:   bridge window [mem 0xcfd00000-0xcfefffff]
[    0.169749] pci 0000:00:01.0:   bridge window [mem 0xbfa00000-0xcfbfffff pref]
[    0.169773] pci_bus 0000:00: resource 0 [io  0x0000-0xffff]
[    0.169777] pci_bus 0000:00: resource 1 [mem 0x00000000-0xffffffff]
[    0.169783] pci_bus 0000:01: resource 0 [io  0xb000-0xbfff]
[    0.169787] pci_bus 0000:01: resource 1 [mem 0xcfd00000-0xcfefffff]
[    0.169792] pci_bus 0000:01: resource 2 [mem 0xbfa00000-0xcfbfffff pref]
[    0.169889] NET: Registered protocol family 2
[    0.170009] IP route cache hash table entries: 4096 (order: 2, 16384 bytes)
[    0.170394] TCP established hash table entries: 16384 (order: 5, 131072 bytes)
[    0.170726] TCP bind hash table entries: 16384 (order: 5, 131072 bytes)
[    0.171040] TCP: Hash tables configured (established 16384 bind 16384)
[    0.171045] TCP reno registered
[    0.171051] UDP hash table entries: 256 (order: 1, 8192 bytes)
[    0.171071] UDP-Lite hash table entries: 256 (order: 1, 8192 bytes)
[    0.171286] NET: Registered protocol family 1
[    0.171434] pci 0000:01:00.0: Boot video device
[    0.171440] PCI: CLS 32 bytes, default 32
[    0.171895] cpufreq-nforce2: No nForce2 chipset.
[    0.171955] Scanning for low memory corruption every 60 seconds
[    0.172164] audit: initializing netlink socket (disabled)
[    0.172189] type=2000 audit(1293144933.168:1): initialized
[    0.187742] Trying to unpack rootfs image as initramfs...
[    4.015708] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    4.018333] VFS: Disk quotas dquot_6.5.2
[    4.018449] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    4.019565] fuse init (API version 7.14)
[    4.019724] msgmni has been set to 843
[    4.020376] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    4.020383] io scheduler noop registered
[    4.020387] io scheduler deadline registered
[    4.020408] io scheduler cfq registered (default)
[    4.020641] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    4.020685] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    4.021041] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0
[    4.021055] ACPI: Power Button [PWRB]
[    4.021152] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
[    4.021159] ACPI: Power Button [PWRF]
[    4.021368] ACPI: acpi_idle registered with cpuidle
[    4.023855] ERST: Table is not found!
[    4.024332] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    4.024483] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    4.024986] 00:08: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    4.027051] brd: module loaded
[    4.028000] loop: module loaded
[    4.028192] isapnp: Scanning for PnP cards...
[    4.034224] pata_sis 0000:00:02.5: version 0.5.2
[    4.034562] scsi0 : pata_sis
[    4.078264] scsi1 : pata_sis
[    4.079538] ata1: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xff00 irq 14
[    4.079544] ata2: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xff08 irq 15
[    4.080252] Fixed MDIO Bus: probed
[    4.080322] PPP generic driver version 2.4.2
[    4.080489] tun: Universal TUN/TAP device driver, 1.6
[    4.080493] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    4.080665] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    4.080711]   alloc irq_desc for 23 on node -1
[    4.080715]   alloc kstat_irqs on node -1
[    4.080733] ehci_hcd 0000:00:03.2: PCI INT D -> GSI 23 (level, low) -> IRQ 23
[    4.080772] ehci_hcd 0000:00:03.2: EHCI Host Controller
[    4.080836] ehci_hcd 0000:00:03.2: new USB bus registered, assigned bus number 1
[    4.080935] ehci_hcd 0000:00:03.2: irq 23, io mem 0xcfffb000
[    4.124722] ehci_hcd 0000:00:03.2: USB 2.0 started, EHCI 1.00
[    4.124978] hub 1-0:1.0: USB hub found
[    4.124990] hub 1-0:1.0: 6 ports detected
[    4.125105] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    4.125134]   alloc irq_desc for 20 on node -1
[    4.125138]   alloc kstat_irqs on node -1
[    4.125150] ohci_hcd 0000:00:03.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    4.125177] ohci_hcd 0000:00:03.0: OHCI Host Controller
[    4.125253] ohci_hcd 0000:00:03.0: new USB bus registered, assigned bus number 2
[    4.125303] ohci_hcd 0000:00:03.0: irq 20, io mem 0xcfff9000
[    4.214545] hub 2-0:1.0: USB hub found
[    4.214556] hub 2-0:1.0: 3 ports detected
[    4.214644]   alloc irq_desc for 21 on node -1
[    4.214648]   alloc kstat_irqs on node -1
[    4.214657] ohci_hcd 0000:00:03.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[    4.214673] ohci_hcd 0000:00:03.1: OHCI Host Controller
[    4.214744] ohci_hcd 0000:00:03.1: new USB bus registered, assigned bus number 3
[    4.214781] ohci_hcd 0000:00:03.1: irq 21, io mem 0xcfffa000
[    4.282538] hub 3-0:1.0: USB hub found
[    4.282548] hub 3-0:1.0: 3 ports detected
[    4.282633] uhci_hcd: USB Universal Host Controller Interface driver
[    4.282805] PNP: PS/2 Controller [PNP0303:PS2K] at 0x60,0x64 irq 1
[    4.282810] PNP: PS/2 appears to have AUX port disabled, if this is incorrect please boot with i8042.nopnp
[    4.283009] serio: i8042 KBD port at 0x60,0x64 irq 1
[    4.283264] mice: PS/2 mouse device common for all mice
[    4.283498] rtc_cmos 00:03: RTC can wake from S4
[    4.283591] rtc_cmos 00:03: rtc core: registered rtc_cmos as rtc0
[    4.283623] rtc0: alarms up to one year, 114 bytes nvram
[    4.283801] device-mapper: uevent: version 1.0.3
[    4.284063] device-mapper: ioctl: 4.17.0-ioctl (2010-03-05) initialised: dm-devel@redhat.com
[    4.284179] device-mapper: multipath: version 1.1.1 loaded
[    4.284185] device-mapper: multipath round-robin: version 1.0.0 loaded
[    4.284400] EISA: Probing bus 0 at eisa.0
[    4.284450] EISA: Detected 0 cards.
[    4.284557] cpuidle: using governor ladder
[    4.284562] cpuidle: using governor menu
[    4.285041] TCP cubic registered
[    4.285299] NET: Registered protocol family 10
[    4.285887] lo: Disabled Privacy Extensions
[    4.286231] NET: Registered protocol family 17
[    4.286321] powernow-k8: Processor cpuid 681 not supported
[    4.286359] powernow: PowerNOW! Technology present. Can scale: frequency and voltage.
[    4.294325] powernow: No PST tables match this cpuid (0x781)
[    4.294329] powernow: This is indicative of a broken BIOS.
[    4.294332] powernow: Trying ACPI perflib
[    4.294678] powernow: ACPI perflib can not be used on this platform
[    4.294682] powernow: ACPI and legacy methods failed
[    4.294696] Using IPI No-Shortcut mode
[    4.294847] ata1.00: ATA-7: SAMSUNG HD154UI, 1AG01118, max UDMA/133
[    4.294853] ata1.00: 2930277168 sectors, multi 16: LBA48 NCQ (depth 0/1)
[    4.294890] ata1.00: limited to UDMA/33 due to 40-wire cable
[    4.295150] PM: Resume from disk failed.
[    4.295177] registered taskstats version 1
[    4.295384]   Magic number: 6:990:957
[    4.295388]   hash matches /build/buildd/linux-2.6.35/drivers/base/power/main.c:544
[    4.295562] rtc_cmos 00:03: setting system clock to 2010-12-23 22:55:37 UTC (1293144937)
[    4.295568] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    4.295572] EDD information not available.
[    4.426600] isapnp: No Plug & Play device found
[    4.426648] ata1.00: configured for UDMA/33
[    4.426912] scsi 0:0:0:0: Direct-Access     ATA      SAMSUNG HD154UI  1AG0 PQ: 0 ANSI: 5
[    4.427239] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    4.427522] sd 0:0:0:0: [sda] 2930277168 512-byte logical blocks: (1.50 TB/1.36 TiB)
[    4.427625] sd 0:0:0:0: [sda] Write Protect is off
[    4.427631] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    4.427674] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    4.427960]  sda:
[    4.433428] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input2
[    4.439795]  sda1 sda2 < sda5 > sda3
[    4.456530] sd 0:0:0:0: [sda] Attached SCSI disk
[    5.043090] ata2.00: ATAPI: SONY    CD-RW  CRX175A1, 5YS2, max UDMA/33
[    5.048398] ata2.00: configured for UDMA/33
[    5.049038] scsi 1:0:0:0: CD-ROM            SONY     CD-RW  CRX175A1  5YS2 PQ: 0 ANSI: 5
[    5.049902] sr0: scsi3-mmc drive: 40x/40x writer cd/rw xa/form2 cdda tray
[    5.049911] Uniform CD-ROM driver Revision: 3.20
[    5.050160] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    5.050307] sr 1:0:0:0: Attached scsi generic sg1 type 5
[    5.071087] Freeing initrd memory: 11144k freed
[    5.094592] Freeing unused kernel memory: 684k freed
[    5.096395] Write protecting the kernel text: 4932k
[    5.096449] Write protecting the kernel read-only data: 1976k
[    5.147808] ramzswap: disk size not provided. You can use disksize_kb module param to specify size.
[    5.147812] Using default: (25% of RAM).
[    5.147818] ramzswap: disk size set to 110944 kB
[    5.152135] usb 2-1: new low speed USB device using ohci_hcd and address 2
[    5.160878] udev[75]: starting version 163
[    5.595956] FDC 0 is a post-1991 82077
[    5.626168] Linux agpgart interface v0.103
[    5.632805] sis900.c: v1.08.10 Apr. 2 2006
[    5.632879]   alloc irq_desc for 19 on node -1
[    5.632884]   alloc kstat_irqs on node -1
[    5.632900] sis900 0000:00:04.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    5.634043] 0000:00:04.0: Realtek RTL8201 PHY transceiver found at address 1.
[    5.645808] 0000:00:04.0: Using transceiver found at address 1 as default
[    5.697284] eth0: SiS 900 PCI Fast Ethernet at 0xd400, IRQ 19, 00:13:8f:30:e7:e9
[    5.697334] agpgart-sis 0000:00:00.0: SiS chipset [1039/0741]
[    5.705881] usbcore: registered new interface driver hiddev
[    5.707849] agpgart-sis 0000:00:00.0: AGP aperture is 64M @ 0xd0000000
[    5.712714] input: HID 04b3:3108 as /devices/pci0000:00/0000:00:03.0/usb2/2-1/2-1:1.0/input/input3
[    5.713149] generic-usb 0003:04B3:3108.0001: input,hidraw0: USB HID v1.00 Mouse [HID 04b3:3108] on usb-0000:00:03.0-1/input0
[    5.713596] usbcore: registered new interface driver usbhid
[    5.713602] usbhid: USB HID core driver
[    9.885947] Btrfs loaded
[    9.898495] xor: automatically using best checksumming function: pIII_sse
[    9.916009]    pIII_sse  :  1556.000 MB/sec
[    9.916014] xor: using function: pIII_sse (1556.000 MB/sec)
[    9.922360] device-mapper: dm-raid45: initialized v0.2594b
[   10.089758] EXT4-fs (sda1): INFO: recovery required on readonly filesystem
[   10.089771] EXT4-fs (sda1): write access will be enabled during recovery
[   12.740120] EXT4-fs (sda1): recovery complete
[   12.748677] EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: (null)
[   16.519161] sr 1:0:0:0: [sr0] Unhandled sense code
[   16.519170] sr 1:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   16.519177] sr 1:0:0:0: [sr0] Sense Key : Medium Error [current] 
[   16.519185] sr 1:0:0:0: [sr0] Add. Sense: No seek complete
[   16.519194] sr 1:0:0:0: [sr0] CDB: Read(10): 28 00 00 11 8c 20 00 00 02 00
[   16.519208] end_request: I/O error, dev sr0, sector 4599936
[   16.519216] Buffer I/O error on device sr0, logical block 574992
[   20.873422] sr 1:0:0:0: [sr0] Unhandled sense code
[   20.873427] sr 1:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   20.873433] sr 1:0:0:0: [sr0] Sense Key : Medium Error [current] 
[   20.873439] sr 1:0:0:0: [sr0] Add. Sense: No seek complete
[   20.873445] sr 1:0:0:0: [sr0] CDB: Read(10): 28 00 00 11 8c 20 00 00 02 00
[   20.873457] end_request: I/O error, dev sr0, sector 4599936
[   20.873462] Buffer I/O error on device sr0, logical block 574992
[   25.216033] sr 1:0:0:0: [sr0] Unhandled sense code
[   25.216038] sr 1:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   25.216044] sr 1:0:0:0: [sr0] Sense Key : Medium Error [current] 
[   25.216050] sr 1:0:0:0: [sr0] Add. Sense: No seek complete
[   25.216055] sr 1:0:0:0: [sr0] CDB: Read(10): 28 00 00 11 8c 42 00 00 02 00
[   25.216068] end_request: I/O error, dev sr0, sector 4600072
[   25.216073] Buffer I/O error on device sr0, logical block 575009
[   29.555523] sr 1:0:0:0: [sr0] Unhandled sense code
[   29.555528] sr 1:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   29.555533] sr 1:0:0:0: [sr0] Sense Key : Medium Error [current] 
[   29.555539] sr 1:0:0:0: [sr0] Add. Sense: No seek complete
[   29.555544] sr 1:0:0:0: [sr0] CDB: Read(10): 28 00 00 11 8c 42 00 00 02 00
[   29.555556] end_request: I/O error, dev sr0, sector 4600072
[   29.555561] Buffer I/O error on device sr0, logical block 575009
[   34.016892] sr 1:0:0:0: [sr0] Unhandled sense code
[   34.016897] sr 1:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   34.016903] sr 1:0:0:0: [sr0] Sense Key : Medium Error [current] 
[   34.016909] sr 1:0:0:0: [sr0] Add. Sense: No seek complete
[   34.016914] sr 1:0:0:0: [sr0] CDB: Read(10): 28 00 00 11 8c 44 00 00 02 00
[   34.016927] end_request: I/O error, dev sr0, sector 4600080
[   34.016933] Buffer I/O error on device sr0, logical block 575010
[   38.366990] sr 1:0:0:0: [sr0] Unhandled sense code
[   38.366994] sr 1:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   38.367000] sr 1:0:0:0: [sr0] Sense Key : Medium Error [current] 
[   38.367006] sr 1:0:0:0: [sr0] Add. Sense: No seek complete
[   38.367012] sr 1:0:0:0: [sr0] CDB: Read(10): 28 00 00 11 8c 44 00 00 02 00
[   38.367024] end_request: I/O error, dev sr0, sector 4600080
[   38.367029] Buffer I/O error on device sr0, logical block 575010
[   42.728332] sr 1:0:0:0: [sr0] Unhandled sense code
[   42.728337] sr 1:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   42.728343] sr 1:0:0:0: [sr0] Sense Key : Medium Error [current] 
[   42.728349] sr 1:0:0:0: [sr0] Add. Sense: No seek complete
[   42.728355] sr 1:0:0:0: [sr0] CDB: Read(10): 28 00 00 11 8c 44 00 00 02 00
[   42.728367] end_request: I/O error, dev sr0, sector 4600080
[   42.728372] Buffer I/O error on device sr0, logical block 575010
[   47.102635] sr 1:0:0:0: [sr0] Unhandled sense code
[   47.102640] sr 1:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   47.102645] sr 1:0:0:0: [sr0] Sense Key : Medium Error [current] 
[   47.102651] sr 1:0:0:0: [sr0] Add. Sense: No seek complete
[   47.102657] sr 1:0:0:0: [sr0] CDB: Read(10): 28 00 00 11 8c 44 00 00 02 00
[   47.102669] end_request: I/O error, dev sr0, sector 4600080
[   47.102674] Buffer I/O error on device sr0, logical block 575010
[   51.466701] sr 1:0:0:0: [sr0] Unhandled sense code
[   51.466705] sr 1:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   51.466711] sr 1:0:0:0: [sr0] Sense Key : Medium Error [current] 
[   51.466717] sr 1:0:0:0: [sr0] Add. Sense: No seek complete
[   51.466722] sr 1:0:0:0: [sr0] CDB: Read(10): 28 00 00 11 8c 44 00 00 02 00
[   51.466735] end_request: I/O error, dev sr0, sector 4600080
[   51.466740] Buffer I/O error on device sr0, logical block 575010
[   55.817589] sr 1:0:0:0: [sr0] Unhandled sense code
[   55.817594] sr 1:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   55.817600] sr 1:0:0:0: [sr0] Sense Key : Medium Error [current] 
[   55.817606] sr 1:0:0:0: [sr0] Add. Sense: No seek complete
[   55.817611] sr 1:0:0:0: [sr0] CDB: Read(10): 28 00 00 11 8c 44 00 00 02 00
[   55.817623] end_request: I/O error, dev sr0, sector 4600080
[   55.817629] Buffer I/O error on device sr0, logical block 575010
[   60.182207] sr 1:0:0:0: [sr0] Unhandled sense code
[   60.182212] sr 1:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   60.182218] sr 1:0:0:0: [sr0] Sense Key : Medium Error [current] 
[   60.182224] sr 1:0:0:0: [sr0] Add. Sense: No seek complete
[   60.182229] sr 1:0:0:0: [sr0] CDB: Read(10): 28 00 00 11 8c 44 00 00 02 00
[   60.182242] end_request: I/O error, dev sr0, sector 4600080
[   60.182246] Buffer I/O error on device sr0, logical block 575010
[   64.547548] sr 1:0:0:0: [sr0] Unhandled sense code
[   64.547552] sr 1:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   64.547558] sr 1:0:0:0: [sr0] Sense Key : Medium Error [current] 
[   64.547564] sr 1:0:0:0: [sr0] Add. Sense: No seek complete
[   64.547569] sr 1:0:0:0: [sr0] CDB: Read(10): 28 00 00 11 8c 36 00 00 02 00
[   64.547581] end_request: I/O error, dev sr0, sector 4600024
[   64.547586] Buffer I/O error on device sr0, logical block 575003
[   68.917755] sr 1:0:0:0: [sr0] Unhandled sense code
[   68.917760] sr 1:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   68.917765] sr 1:0:0:0: [sr0] Sense Key : Medium Error [current] 
[   68.917771] sr 1:0:0:0: [sr0] Add. Sense: No seek complete
[   68.917777] sr 1:0:0:0: [sr0] CDB: Read(10): 28 00 00 11 8c 42 00 00 02 00
[   68.917789] end_request: I/O error, dev sr0, sector 4600072
[   68.917794] Buffer I/O error on device sr0, logical block 575009
[   73.272057] sr 1:0:0:0: [sr0] Unhandled sense code
[   73.272061] sr 1:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   73.272067] sr 1:0:0:0: [sr0] Sense Key : Medium Error [current] 
[   73.272073] sr 1:0:0:0: [sr0] Add. Sense: No seek complete
[   73.272079] sr 1:0:0:0: [sr0] CDB: Read(10): 28 00 00 11 8c 44 00 00 02 00
[   73.272091] end_request: I/O error, dev sr0, sector 4600080
[   73.272097] Buffer I/O error on device sr0, logical block 575010
[   77.608571] sr 1:0:0:0: [sr0] Unhandled sense code
[   77.608576] sr 1:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   77.608581] sr 1:0:0:0: [sr0] Sense Key : Medium Error [current] 
[   77.608587] sr 1:0:0:0: [sr0] Add. Sense: No seek complete
[   77.608592] sr 1:0:0:0: [sr0] CDB: Read(10): 28 00 00 11 8c 44 00 00 02 00
[   77.608605] end_request: I/O error, dev sr0, sector 4600080
[   77.608609] Buffer I/O error on device sr0, logical block 575010
[   81.965079] sr 1:0:0:0: [sr0] Unhandled sense code
[   81.965084] sr 1:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   81.965089] sr 1:0:0:0: [sr0] Sense Key : Medium Error [current] 
[   81.965095] sr 1:0:0:0: [sr0] Add. Sense: No seek complete
[   81.965101] sr 1:0:0:0: [sr0] CDB: Read(10): 28 00 00 11 8c 44 00 00 02 00
[   81.965113] end_request: I/O error, dev sr0, sector 4600080
[   81.965118] Buffer I/O error on device sr0, logical block 575010
[   82.536137] ISO 9660 Extensions: Microsoft Joliet Level 3
[   82.575751] ISO 9660 Extensions: RRIP_1991A
[   82.756563] aufs 2-standalone.tree-35-rcN-20100705
[   82.867740] squashfs: version 4.0 (2009/01/31) Phillip Lougher
[  145.766771] Adding 2928636k swap on /dev/sda5.  Priority:-1 extents:1 across:2928636k 
[  147.526991] udev[1139]: starting version 163
[  150.526071] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[  150.933707] sis96x_smbus 0000:00:02.1: SiS96x SMBus base address: 0x0c00
[  150.933722] ACPI: resource 0000:00:02.1 [io  0x0c00-0x0c1f] conflicts with ACPI region SMRG [??? 0x00000c00-0x00000c1f flags 0x47]
[  150.933727] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[  151.899463] parport_pc 00:09: reported by Plug and Play ACPI
[  151.899598] parport0: PC-style at 0x378 (0x778), irq 7, dma 0 [PCSPP,TRISTATE,COMPAT,EPP,ECP,DMA]
[  152.217993] ppdev: user-space parallel port driver
[  152.228959] gameport gameport0: NS558 PnP Gameport is pnp00:0a/gameport0, io 0x200, speed 795kHz
[  154.032876]   alloc irq_desc for 18 on node -1
[  154.032885]   alloc kstat_irqs on node -1
[  154.032903] Intel ICH 0000:00:02.7: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[  154.163853] eth0: Media Link Off
[  154.166287] ADDRCONF(NETDEV_UP): eth0: link is not ready
[  154.356099] intel8x0_measure_ac97_clock: measured 55784 usecs (2683 samples)
[  154.356108] intel8x0: clocking to 48000
[  155.252057] lp0: using parport0 (interrupt-driven).
[  505.730557] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[  510.016043] ------------[ cut here ]------------
[  510.016076] WARNING: at /build/buildd/linux-2.6.35/net/sched/sch_generic.c:258 dev_watchdog+0x1fd/0x210()
[  510.016081] Hardware name: K7S41GX
[  510.016085] NETDEV WATCHDOG: eth0 (sis900): transmit queue 0 timed out
[  510.016089] Modules linked in: binfmt_misc dm_crypt lp snd_intel8x0 snd_ac97_codec ac97_bus snd_pcm snd_seq_midi snd_rawmidi snd_seq_midi_event ppdev ns558 snd_seq parport_pc snd_timer gameport parport snd_seq_device snd soundcore i2c_sis96x snd_page_alloc shpchp squashfs aufs isofs nls_iso8859_1 nls_cp437 vfat fat dm_raid45 xor btrfs zlib_deflate crc32c libcrc32c usbhid sis_agp sis900 hid floppy mii agpgart ramzswap xvmalloc lzo_compress
[  510.016156] Pid: 0, comm: swapper Not tainted 2.6.35-22-generic #33-Ubuntu
[  510.016161] Call Trace:
[  510.016182]  [<c014ac52>] warn_slowpath_common+0x72/0xa0
[  510.016189]  [<c050e62d>] ? dev_watchdog+0x1fd/0x210
[  510.016196]  [<c050e62d>] ? dev_watchdog+0x1fd/0x210
[  510.016202]  [<c014ad23>] warn_slowpath_fmt+0x33/0x40
[  510.016208]  [<c050e62d>] dev_watchdog+0x1fd/0x210
[  510.016218]  [<c016c121>] ? sched_clock_cpu+0x131/0x190
[  510.016232]  [<c01692ab>] ? hrtimer_forward+0x16b/0x1b0
[  510.016238]  [<c050e430>] ? dev_watchdog+0x0/0x210
[  510.016246]  [<c0157e1f>] call_timer_fn+0x2f/0xf0
[  510.016253]  [<c01222db>] ? lapic_next_event+0x1b/0x20
[  510.016263]  [<c01743fb>] ? clockevents_program_event+0x8b/0x140
[  510.016270]  [<c0159064>] run_timer_softirq+0x104/0x210
[  510.016277]  [<c0175802>] ? tick_dev_program_event+0x42/0x150
[  510.016284]  [<c050e430>] ? dev_watchdog+0x0/0x210
[  510.016293]  [<c015127c>] __do_softirq+0x9c/0x1b0
[  510.016298]  [<c0158a70>] ? do_timer+0x20/0x30
[  510.016304]  [<c0175d00>] ? tick_do_update_jiffies64+0x120/0x170
[  510.016310]  [<c01513d5>] do_softirq+0x45/0x50
[  510.016315]  [<c0151545>] irq_exit+0x65/0x70
[  510.016323]  [<c05cf72b>] smp_apic_timer_interrupt+0x5b/0x8a
[  510.016332]  [<c05c9535>] apic_timer_interrupt+0x31/0x38
[  510.016341]  [<c012c21a>] ? native_safe_halt+0xa/0x10
[  510.016353]  [<c010a2f9>] default_idle+0x49/0xb0
[  510.016359]  [<c0101fcc>] cpu_idle+0x8c/0xd0
[  510.016368]  [<c05b2431>] rest_init+0x71/0x80
[  510.016379]  [<c081981a>] start_kernel+0x36e/0x374
[  510.016385]  [<c08199dd>] ? pass_all_bootoptions+0x0/0xa
[  510.016391]  [<c08190d7>] i386_start_kernel+0xd7/0xdf
[  510.016396] ---[ end trace 2ebe7e5f6342ccad ]---
[  510.016403] eth0: Transmit timeout, status 00000004 00000000
[  510.737080] eth0: Media Link On 100mbps full-duplex
[  515.936048] eth0: no IPv6 routers present

```

(:

---

### Post by psusi on 2010-12-23
Make sure that your bios is set to run the SATA controller in AHCI mode, not IDE mode, and run the boot info script and paste its output:

[http://sourceforge.net/projects/bootinfoscript/](http://sourceforge.net/projects/bootinfoscript/)

---

### Post by mcemsi on 2010-12-23
Hm,

I don't know whether my BIOS supports such settings.

It is a ASUS Asrock K7S41GX in combination with a IDE - to SATA Adapter.

Maybe this Adapter doesn't support booting?

---

### Post by psusi on 2010-12-23
> **mcemsi said:**
> Hm,

I don't know whether my BIOS supports such settings.

It is a ASUS Asrock K7S41GX in combination with a IDE - to SATA Adapter.

Maybe this Adapter doesn't support booting?

Oh, yea.... IDE to SATA adapter would be the problem.  It probably can't see a disk that large.  Try reinstalling but make a 300mb /boot partition at the start of the disk this time.

---

### Post by mcemsi on 2010-12-24
Hm damn^^

I want to use the System on the disk without having to reinstall it.

Is there any possibility to "clone" the partition of the Sata HDD to a IDE and boot from it?

Or woult buying another Board(with sata support) maybe fix the problem?

Thanks a lot and 

Merry Christmas

---

### Post by psusi on 2010-12-24
A new board with sata support should fix the problem.  If that board does't have sata support it must be quite old and the bios can't recognize more than 128gb.

---

