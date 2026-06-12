---
title: "Internet help question!!!"
date: 2010-05-03
forum: General Help
---

### Post by chrissy.millichamp on 2010-05-03
Hi,
I have Ubuntu Lucid Lynx and suddenly my wired internet network doesnt work anymore after a forced restart.

---

### Post by Rasa1111 on 2010-05-03
have you tried resetting your router>? 
[shutting it down for a couple minutes] usually helps, if that's the case. 

 if not, Im sorry, I cant think of where the problem would be...

---

### Post by Erik765 on 2010-05-03
try

sudo ifconfig eth0 down && eth0 up

assuming eth0 is your connection

if not, you can find it from ifconfig

---

### Post by chrissy.millichamp on 2010-05-03
On the top left where the network icon is, it says only network disable. Its actually weird because in my windows 7 dual boot everything seems to be fine, because everything is properly connected.

---

### Post by Erik765 on 2010-05-03
again...

post the output of ifconfig here please.

---

### Post by chrissy.millichamp on 2010-05-03
chrissy@chrissy-desktop:~$ sudo ifconfig eth0 down && eth0 up
eth0: command not found
chrissy@chrissy-desktop:~$ ifconfig
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:132 errors:0 dropped:0 overruns:0 frame:0
          TX packets:132 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:10988 (10.9 KB)  TX bytes:10988 (10.9 KB)

chrissy@chrissy-desktop:~$ 

This is what what I had as a response, after following precisely your instructions.

---

### Post by sir_nasty on 2010-05-03
try sudo ifconfig eth0 , if that returns something about eth0 not found then I'd click system, administration, hardware drivers and see if it finds anything... if nothing there then run dmesg and scan through there for some error pertaining to your NIC card.

---

### Post by chrissy.millichamp on 2010-05-03
I dont understand, whats (dmesg)?

---

### Post by sir_nasty on 2010-05-04
Sorry for the lack of clarification.  Open a terminal and type in 'dmesg' without the '' of course.  That will return a bunch of data from where it's initializing the interfaces etc.  This should give us the clue of where to look for why eth0 isn't coming up....

---

### Post by chrissy.millichamp on 2010-05-06
Thats what appear, after Ive typed in the terminal (dmesg).

[    0.195885] pci 0000:00:03.1: reg 10 io port: [0x4900-0x493f]
[    0.195900] pci 0000:00:03.1: reg 20 io port: [0x4d00-0x4d3f]
[    0.195905] pci 0000:00:03.1: reg 24 io port: [0x4e00-0x4e3f]
[    0.195931] pci 0000:00:03.1: PME# supported from D3hot D3cold
[    0.195936] pci 0000:00:03.1: PME# disabled
[    0.196122] pci 0000:00:04.0: reg 10 32bit mmio: [0xfeaff000-0xfeafffff]
[    0.196154] pci 0000:00:04.0: supports D1 D2
[    0.196157] pci 0000:00:04.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.196160] pci 0000:00:04.0: PME# disabled
[    0.196191] pci 0000:00:04.1: reg 10 32bit mmio: [0xfeafec00-0xfeafecff]
[    0.196229] pci 0000:00:04.1: supports D1 D2
[    0.196231] pci 0000:00:04.1: PME# supported from D0 D1 D2 D3hot D3cold
[    0.196235] pci 0000:00:04.1: PME# disabled
[    0.196288] pci 0000:00:08.0: reg 20 io port: [0xffa0-0xffaf]
[    0.196336] pci 0000:00:09.0: reg 10 32bit mmio: [0xfeaf8000-0xfeafbfff]
[    0.196371] pci 0000:00:09.0: PME# supported from D3hot D3cold
[    0.196375] pci 0000:00:09.0: PME# disabled
[    0.196463] pci 0000:00:0b.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.196466] pci 0000:00:0b.0: PME# disabled
[    0.196519] pci 0000:00:0c.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.196522] pci 0000:00:0c.0: PME# disabled
[    0.196575] pci 0000:00:0d.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.196578] pci 0000:00:0d.0: PME# disabled
[    0.196612] pci 0000:00:0e.0: reg 10 io port: [0xd480-0xd487]
[    0.196617] pci 0000:00:0e.0: reg 14 io port: [0xd400-0xd403]
[    0.196622] pci 0000:00:0e.0: reg 18 io port: [0xd080-0xd087]
[    0.196626] pci 0000:00:0e.0: reg 1c io port: [0xd000-0xd003]
[    0.196631] pci 0000:00:0e.0: reg 20 io port: [0xcc00-0xcc0f]
[    0.196636] pci 0000:00:0e.0: reg 24 32bit mmio: [0xfeafc000-0xfeafdfff]
[    0.196684] pci 0000:00:0f.0: reg 10 32bit mmio: [0xfeaf7000-0xfeaf7fff]
[    0.196689] pci 0000:00:0f.0: reg 14 io port: [0xc880-0xc887]
[    0.196694] pci 0000:00:0f.0: reg 18 32bit mmio: [0xfeafe800-0xfeafe8ff]
[    0.196699] pci 0000:00:0f.0: reg 1c 32bit mmio: [0xfeafe400-0xfeafe40f]
[    0.196726] pci 0000:00:0f.0: supports D1 D2
[    0.196728] pci 0000:00:0f.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.196733] pci 0000:00:0f.0: PME# disabled
[    0.196759] pci 0000:00:10.0: reg 10 32bit mmio: [0xfd000000-0xfdffffff]
[    0.196766] pci 0000:00:10.0: reg 14 64bit mmio pref: [0xd0000000-0xdfffffff]
[    0.196773] pci 0000:00:10.0: reg 1c 64bit mmio: [0xfc000000-0xfcffffff]
[    0.196780] pci 0000:00:10.0: reg 30 32bit mmio pref: [0xfeac0000-0xfeadffff]
[    0.196864] pci 0000:00:0a.0: transparent bridge
[    0.197006] pci 0000:04:00.0: reg 10 64bit mmio: [0xfebff800-0xfebfffff]
[    0.197013] pci 0000:04:00.0: reg 18 io port: [0xe800-0xe8ff]
[    0.197059] pci 0000:04:00.0: supports D2
[    0.197061] pci 0000:04:00.0: PME# supported from D2 D3hot D3cold
[    0.197066] pci 0000:04:00.0: PME# disabled
[    0.197123] pci 0000:00:0d.0: bridge io port: [0xe000-0xefff]
[    0.197126] pci 0000:00:0d.0: bridge 32bit mmio: [0xfeb00000-0xfebfffff]
[    0.197142] pci_bus 0000:00: on NUMA node 0
[    0.197149] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.197342] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P1._PRT]
[    0.197434] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.BR10._PRT]
[    0.197493] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.BR11._PRT]
[    0.197552] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.BR12._PRT]
[    0.208595] ACPI: PCI Interrupt Link [LNKA] (IRQs 16 17 18 19) *0, disabled.
[    0.208805] ACPI: PCI Interrupt Link [LNKB] (IRQs 16 17 18 19) *0, disabled.
[    0.209015] ACPI: PCI Interrupt Link [LNKC] (IRQs 16 17 18 19) *0, disabled.
[    0.209220] ACPI: PCI Interrupt Link [LNKD] (IRQs 16 17 18 19) *0, disabled.
[    0.209425] ACPI: PCI Interrupt Link [LNEA] (IRQs 16 17 18 19) *0, disabled.
[    0.209633] ACPI: PCI Interrupt Link [LNEB] (IRQs 16 17 18 19) *0, disabled.
[    0.209837] ACPI: PCI Interrupt Link [LNEC] (IRQs 16 17 18 19) *0, disabled.
[    0.210048] ACPI: PCI Interrupt Link [LNED] (IRQs 16 17 18 19) *7
[    0.210259] ACPI: PCI Interrupt Link [LUB0] (IRQs 20 21 22 23) *7
[    0.210467] ACPI: PCI Interrupt Link [LUB2] (IRQs 20 21 22 23) *10
[    0.210675] ACPI: PCI Interrupt Link [LMAC] (IRQs 20 21 22 23) *7
[    0.210899] ACPI: PCI Interrupt Link [LAZA] (IRQs 20 21 22 23) *11
[    0.211113] ACPI: PCI Interrupt Link [SGRU] (IRQs 20 21 22 23) *10
[    0.211326] ACPI: PCI Interrupt Link [LSMB] (IRQs 20 21 22 23) *11
[    0.211535] ACPI: PCI Interrupt Link [LPMU] (IRQs 20 21 22 23) *0, disabled.
[    0.211748] ACPI: PCI Interrupt Link [LSA0] (IRQs 20 21 22 23) *5
[    0.212010] ACPI: PCI Interrupt Link [LATA] (IRQs 20 21 22 23) *0, disabled.
[    0.212144] vgaarb: device added: PCI:0000:00:10.0,decodes=io+mem,owns=io+mem,locks=none
[    0.212147] vgaarb: loaded
[    0.212264] SCSI subsystem initialized
[    0.212384] libata version 3.00 loaded.
[    0.212454] usbcore: registered new interface driver usbfs
[    0.212465] usbcore: registered new interface driver hub
[    0.212488] usbcore: registered new device driver usb
[    0.212649] ACPI: WMI: Mapper loaded
[    0.212651] PCI: Using ACPI for IRQ routing
[    0.212857] NetLabel: Initializing
[    0.212859] NetLabel:  domain hash size = 128
[    0.212861] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.212872] NetLabel:  unlabeled traffic allowed by default
[    0.212908] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 31
[    0.212913] hpet0: 3 comparators, 32-bit 25.000000 MHz counter
[    0.216017] Switching to clocksource tsc
[    0.217957] AppArmor: AppArmor Filesystem Enabled
[    0.217984] pnp: PnP ACPI init
[    0.218006] ACPI: bus type pnp registered
[    0.223404] pnp: PnP ACPI: found 14 devices
[    0.223407] ACPI: ACPI bus type pnp unregistered
[    0.223411] PnPBIOS: Disabled by ACPI PNP
[    0.223426] system 00:05: ioport range 0x4d0-0x4d1 has been reserved
[    0.223428] system 00:05: ioport range 0x800-0x80f has been reserved
[    0.223431] system 00:05: ioport range 0x4000-0x407f has been reserved
[    0.223434] system 00:05: ioport range 0x4080-0x40ff has been reserved
[    0.223436] system 00:05: ioport range 0x4400-0x447f has been reserved
[    0.223439] system 00:05: ioport range 0x4480-0x44ff has been reserved
[    0.223441] system 00:05: ioport range 0x4800-0x487f has been reserved
[    0.223444] system 00:05: ioport range 0x4880-0x48ff has been reserved
[    0.223447] system 00:05: iomem range 0xfec80000-0xfd93ffff could not be reserved
[    0.223450] system 00:05: iomem range 0xfed02000-0xfed03fff has been reserved
[    0.223453] system 00:05: iomem range 0xfed04000-0xfed04fff has been reserved
[    0.223455] system 00:05: iomem range 0xfee01000-0xfeefffff has been reserved
[    0.223462] system 00:08: iomem range 0xfec00000-0xfec00fff could not be reserved
[    0.223464] system 00:08: iomem range 0xfee00000-0xfee00fff has been reserved
[    0.223470] system 00:0b: ioport range 0xa00-0xa0f has been reserved
[    0.223473] system 00:0b: ioport range 0xa10-0xa1f has been reserved
[    0.223475] system 00:0b: ioport range 0xa20-0xa2f has been reserved
[    0.223478] system 00:0b: ioport range 0xa30-0xa3f has been reserved
[    0.223483] system 00:0c: iomem range 0xe0000000-0xefffffff has been reserved
[    0.223488] system 00:0d: iomem range 0x0-0x9ffff could not be reserved
[    0.223491] system 00:0d: iomem range 0xc0000-0xcffff could not be reserved
[    0.223494] system 00:0d: iomem range 0xe0000-0xfffff could not be reserved
[    0.223496] system 00:0d: iomem range 0x100000-0x7fffffff could not be reserved
[    0.223499] system 00:0d: iomem range 0xfec00000-0xffffffff could not be reserved
[    0.258267] pci 0000:00:0a.0: PCI bridge, secondary bus 0000:01
[    0.258270] pci 0000:00:0a.0:   IO window: disabled
[    0.258274] pci 0000:00:0a.0:   MEM window: disabled
[    0.258278] pci 0000:00:0a.0:   PREFETCH window: disabled
[    0.258283] pci 0000:00:0b.0: PCI bridge, secondary bus 0000:02
[    0.258284] pci 0000:00:0b.0:   IO window: disabled
[    0.258288] pci 0000:00:0b.0:   MEM window: disabled
[    0.258291] pci 0000:00:0b.0:   PREFETCH window: disabled
[    0.258295] pci 0000:00:0c.0: PCI bridge, secondary bus 0000:03
[    0.258297] pci 0000:00:0c.0:   IO window: disabled
[    0.258301] pci 0000:00:0c.0:   MEM window: disabled
[    0.258304] pci 0000:00:0c.0:   PREFETCH window: disabled
[    0.258308] pci 0000:00:0d.0: PCI bridge, secondary bus 0000:04
[    0.258311] pci 0000:00:0d.0:   IO window: 0xe000-0xefff
[    0.258315] pci 0000:00:0d.0:   MEM window: 0xfeb00000-0xfebfffff
[    0.258318] pci 0000:00:0d.0:   PREFETCH window: disabled
[    0.258331] pci 0000:00:0a.0: setting latency timer to 64
[    0.258338] pci 0000:00:0b.0: setting latency timer to 64
[    0.258344] pci 0000:00:0c.0: setting latency timer to 64
[    0.258351] pci 0000:00:0d.0: setting latency timer to 64
[    0.258355] pci_bus 0000:00: resource 0 io:  [0x00-0xffff]
[    0.258357] pci_bus 0000:00: resource 1 mem: [0x000000-0xffffffff]
[    0.258360] pci_bus 0000:01: resource 3 io:  [0x00-0xffff]
[    0.258362] pci_bus 0000:01: resource 4 mem: [0x000000-0xffffffff]
[    0.258365] pci_bus 0000:04: resource 0 io:  [0xe000-0xefff]
[    0.258367] pci_bus 0000:04: resource 1 mem: [0xfeb00000-0xfebfffff]
[    0.258406] NET: Registered protocol family 2
[    0.258519] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.258890] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.259465] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.259910] TCP: Hash tables configured (established 131072 bind 65536)
[    0.259913] TCP reno registered
[    0.260024] NET: Registered protocol family 1
[    0.291709] pci 0000:00:10.0: Boot video device
[    0.291906] cpufreq-nforce2: No nForce2 chipset.
[    0.291932] Scanning for low memory corruption every 60 seconds
[    0.292044] audit: initializing netlink socket (disabled)
[    0.292057] type=2000 audit(1273073295.291:1): initialized
[    0.301200] highmem bounce pool size: 64 pages
[    0.301205] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    0.302627] VFS: Disk quotas dquot_6.5.2
[    0.302695] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.303232] fuse init (API version 7.13)
[    0.303312] msgmni has been set to 1696
[    0.303525] alg: No test for stdrng (krng)
[    0.303581] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.303584] io scheduler noop registered
[    0.303586] io scheduler anticipatory registered
[    0.303587] io scheduler deadline registered
[    0.303641] io scheduler cfq registered (default)
[    0.303790]   alloc irq_desc for 24 on node -1
[    0.303792]   alloc kstat_irqs on node -1
[    0.303801] pcieport 0000:00:0b.0: irq 24 for MSI/MSI-X
[    0.303807] pcieport 0000:00:0b.0: setting latency timer to 64
[    0.303900]   alloc irq_desc for 25 on node -1
[    0.303901]   alloc kstat_irqs on node -1
[    0.303907] pcieport 0000:00:0c.0: irq 25 for MSI/MSI-X
[    0.303913] pcieport 0000:00:0c.0: setting latency timer to 64
[    0.304004]   alloc irq_desc for 26 on node -1
[    0.304006]   alloc kstat_irqs on node -1
[    0.304012] pcieport 0000:00:0d.0: irq 26 for MSI/MSI-X
[    0.304017] pcieport 0000:00:0d.0: setting latency timer to 64
[    0.304078] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.304101] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.304196] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0
[    0.304204] ACPI: Power Button [PWRB]
[    0.304250] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
[    0.304253] ACPI: Power Button [PWRF]
[    0.304848] ACPI: SSDT 6ffae670 00235 (v01 DpgPmm  P001Ist 00000011 INTL 20051117)
[    0.305148] processor LNXCPU:00: registered as cooling_device0
[    0.305480] ACPI: SSDT 6ffae8b0 00235 (v01 DpgPmm  P002Ist 00000012 INTL 20051117)
[    0.305757] processor LNXCPU:01: registered as cooling_device1
[    0.310974] thermal LNXTHERM:01: registered as thermal_zone0
[    0.310982] ACPI: Thermal Zone [THRM] (23 C)
[    0.312512] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    0.312614] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.312919] 00:04: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.314012] brd: module loaded
[    0.314444] loop: module loaded
[    0.314539] input: Macintosh mouse button emulation as /devices/virtual/input/input2
[    0.314723] pata_acpi 0000:00:08.0: setting latency timer to 64
[    0.315009] Fixed MDIO Bus: probed
[    0.315047] PPP generic driver version 2.4.2
[    0.315084] tun: Universal TUN/TAP device driver, 1.6
[    0.315086] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.315162] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.315511] ACPI: PCI Interrupt Link [LUB2] enabled at IRQ 23
[    0.315517]   alloc irq_desc for 23 on node -1
[    0.315519]   alloc kstat_irqs on node -1
[    0.315526] ehci_hcd 0000:00:04.1: PCI INT B -> Link[LUB2] -> GSI 23 (level, low) -> IRQ 23
[    0.315548] ehci_hcd 0000:00:04.1: setting latency timer to 64
[    0.315551] ehci_hcd 0000:00:04.1: EHCI Host Controller
[    0.315590] ehci_hcd 0000:00:04.1: new USB bus registered, assigned bus number 1
[    0.315631] ehci_hcd 0000:00:04.1: debug port 1
[    0.315639] ehci_hcd 0000:00:04.1: cache line size of 32 is not supported
[    0.315655] ehci_hcd 0000:00:04.1: irq 23, io mem 0xfeafec00
[    0.315703] isapnp: Scanning for PnP cards...
[    0.364600] ehci_hcd 0000:00:04.1: USB 2.0 started, EHCI 1.00
[    0.364741] usb usb1: configuration #1 chosen from 1 choice
[    0.364772] hub 1-0:1.0: USB hub found
[    0.364783] hub 1-0:1.0: 10 ports detected
[    0.364848] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.365204] ACPI: PCI Interrupt Link [LUB0] enabled at IRQ 22
[    0.365209]   alloc irq_desc for 22 on node -1
[    0.365211]   alloc kstat_irqs on node -1
[    0.365218] ohci_hcd 0000:00:04.0: PCI INT A -> Link[LUB0] -> GSI 22 (level, low) -> IRQ 22
[    0.365237] ohci_hcd 0000:00:04.0: setting latency timer to 64
[    0.365240] ohci_hcd 0000:00:04.0: OHCI Host Controller
[    0.365281] ohci_hcd 0000:00:04.0: new USB bus registered, assigned bus number 2
[    0.365309] ohci_hcd 0000:00:04.0: irq 22, io mem 0xfeaff000
[    0.368883] Freeing initrd memory: 7782k freed
[    0.454316] usb usb2: configuration #1 chosen from 1 choice
[    0.454344] hub 2-0:1.0: USB hub found
[    0.454357] hub 2-0:1.0: 10 ports detected
[    0.454421] uhci_hcd: USB Universal Host Controller Interface driver
[    0.454522] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f03:PS2M] at 0x60,0x64 irq 1,12
[    0.454937] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.454942] serio: i8042 AUX port at 0x60,0x64 irq 12
[    0.455015] mice: PS/2 mouse device common for all mice
[    0.455113] rtc_cmos 00:07: RTC can wake from S4
[    0.455153] rtc_cmos 00:07: rtc core: registered rtc_cmos as rtc0
[    0.455187] rtc0: alarms up to one year, y3k, 114 bytes nvram, hpet irqs
[    0.455277] device-mapper: uevent: version 1.0.3
[    0.459760] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: [email]dm-devel@redhat.com[/email]
[    0.459833] device-mapper: multipath: version 1.1.0 loaded
[    0.459835] device-mapper: multipath round-robin: version 1.0.0 loaded
[    0.459939] EISA: Probing bus 0 at eisa.0
[    0.459952] Cannot allocate resource for EISA slot 4
[    0.459965] EISA: Detected 0 cards.
[    0.460030] cpuidle: using governor ladder
[    0.460032] cpuidle: using governor menu
[    0.460452] TCP cubic registered
[    0.460588] NET: Registered protocol family 10
[    0.461021] lo: Disabled Privacy Extensions
[    0.461327] NET: Registered protocol family 17
[    0.461849] Using IPI No-Shortcut mode
[    0.461919] PM: Resume from disk failed.
[    0.461931] registered taskstats version 1
[    0.462272]   Magic number: 10:883:486
[    0.462347] rtc_cmos 00:07: setting system clock to 2010-05-05 15:28:15 UTC (1273073295)
[    0.462350] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.462352] EDD information not available.
[    0.473234] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input3
[    0.672505] isapnp: No Plug & Play device found
[    0.672518] Freeing unused kernel memory: 656k freed
[    0.672873] Write protecting the kernel text: 4676k
[    0.672910] Write protecting the kernel read-only data: 1840k
[    0.688974] udev: starting version 151
[    0.707714] usb 1-6: new high speed USB device using ehci_hcd and address 2
[    0.793443] ahci 0000:00:0e.0: version 3.0
[    0.793808] ACPI: PCI Interrupt Link [LSA0] enabled at IRQ 21
[    0.793816]   alloc irq_desc for 21 on node -1
[    0.793818]   alloc kstat_irqs on node -1
[    0.793829] ahci 0000:00:0e.0: PCI INT A -> Link[LSA0] -> GSI 21 (level, low) -> IRQ 21
[    0.793880]   alloc irq_desc for 27 on node -1
[    0.793882]   alloc kstat_irqs on node -1
[    0.793890] ahci 0000:00:0e.0: irq 27 for MSI/MSI-X
[    0.793896] ahci 0000:00:0e.0: controller can do NCQ, turning on CAP_NCQ
[    0.793966] ahci 0000:00:0e.0: AHCI 0001.0100 32 slots 4 ports 3 Gbps 0xf impl SATA mode
[    0.793970] ahci 0000:00:0e.0: flags: 64bit ncq sntf led clo pmp pio 
[    0.793973] ahci 0000:00:0e.0: setting latency timer to 64
[    0.802693] scsi0 : ahci
[    0.802890] scsi1 : ahci
[    0.803006] scsi2 : ahci
[    0.803109] scsi3 : ahci
[    0.803234] ata1: SATA max UDMA/133 abar m8192@0xfeafc000 port 0xfeafc100 irq 27
[    0.803237] ata2: SATA max UDMA/133 abar m8192@0xfeafc000 port 0xfeafc180 irq 27
[    0.803239] ata3: SATA max UDMA/133 abar m8192@0xfeafc000 port 0xfeafc200 irq 27
[    0.803242] ata4: SATA max UDMA/133 abar m8192@0xfeafc000 port 0xfeafc280 irq 27
[    0.805422] forcedeth: Reverse Engineered nForce ethernet driver. Version 0.64.
[    0.805769] ACPI: PCI Interrupt Link [LMAC] enabled at IRQ 20
[    0.805775]   alloc irq_desc for 20 on node -1
[    0.805777]   alloc kstat_irqs on node -1
[    0.805785] forcedeth 0000:00:0f.0: PCI INT A -> Link[LMAC] -> GSI 20 (level, low) -> IRQ 20
[    0.805790] forcedeth 0000:00:0f.0: setting latency timer to 64
[    0.842228] usb 1-6: configuration #1 chosen from 1 choice
[    0.853672] Initializing USB Mass Storage driver...
[    0.853773] scsi4 : SCSI emulation for USB Mass Storage devices
[    0.853870] usbcore: registered new interface driver usb-storage
[    0.853873] USB Mass Storage support registered.
[    0.853877] usb-storage: device found at 2
[    0.853879] usb-storage: waiting for device to settle before scanning
[    0.869023] forcedeth 0000:00:0f.0: ifname eth0, PHY OUI 0x732 @ 3, addr 00:25:11:33:44:17
[    0.869026] forcedeth 0000:00:0f.0: highdma pwrctl mgmt gbit lnktim msi desc-v3
[    0.869043] pata_amd 0000:00:08.0: version 0.4.1
[    0.869089] pata_amd 0000:00:08.0: setting latency timer to 64
[    0.869162] scsi5 : pata_amd
[    0.869229] scsi6 : pata_amd
[    0.870182] ata5: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xffa0 irq 14
[    0.870185] ata6: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xffa8 irq 15
[    1.104026] ata4: SATA link down (SStatus 0 SControl 300)
[    1.104047] ata3: SATA link down (SStatus 0 SControl 300)
[    1.240017] usb 2-8: new full speed USB device using ohci_hcd and address 2
[    1.268016] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    1.268031] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    1.271258] ata2.00: ATAPI: HL-DT-ST DVDRAM GH40F, MG01, max UDMA/100
[    1.274998] ata2.00: configured for UDMA/100
[    1.282081] ata1.00: ATA-8: Hitachi HDT721032SLA380, ST2OA31B, max UDMA/133
[    1.282084] ata1.00: 625142448 sectors, multi 0: LBA48 NCQ (depth 31/32)
[    1.282991] ata1.00: configured for UDMA/133
[    1.283097] scsi 0:0:0:0: Direct-Access     ATA      Hitachi HDT72103 ST2O PQ: 0 ANSI: 5
[    1.283272] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    1.283285] sd 0:0:0:0: [sda] 625142448 512-byte logical blocks: (320 GB/298 GiB)
[    1.283337] sd 0:0:0:0: [sda] Write Protect is off
[    1.283340] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.283362] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.283525]  sda:
[    1.285298] scsi 1:0:0:0: CD-ROM            HL-DT-ST DVDRAM GH40F     MG01 PQ: 0 ANSI: 5
[    1.289002] sr0: scsi3-mmc drive: 31x/31x writer dvd-ram cd/rw xa/form2 cdda tray
[    1.289007] Uniform CD-ROM driver Revision: 3.20
[    1.289150] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    1.289205] sr 1:0:0:0: Attached scsi generic sg1 type 5
[    1.289360] ata6: port disabled. ignoring.
[    1.306273]  sda1 sda2 sda3 < sda5 sda6 sda7 >
[    1.347866] sd 0:0:0:0: [sda] Attached SCSI disk
[    1.351141] ACPI: PCI Interrupt Link [LNED] enabled at IRQ 19
[    1.351148]   alloc irq_desc for 19 on node -1
[    1.351150]   alloc kstat_irqs on node -1
[    1.351157] ohci1394 0000:04:00.0: PCI INT A -> Link[LNED] -> GSI 19 (level, low) -> IRQ 19
[    1.351163] ohci1394 0000:04:00.0: setting latency timer to 64
[    1.354546] usbcore: registered new interface driver hiddev
[    1.356146] generic-usb: probe of 0003:058F:6363.0001 failed with error -22
[    1.356192] usbcore: registered new interface driver usbhid
[    1.356195] usbhid: v2.6:USB HID core driver
[    1.410040] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[19]  MMIO=[febff800-febfffff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[    1.449400] usb 2-8: configuration #1 chosen from 1 choice
[    1.930258] EXT4-fs (sda6): mounted filesystem with ordered data mode
[    2.688163] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[00001921ff3bfc29]
[    5.836240] usb-storage: device scan complete
[    5.838471] scsi 4:0:0:0: Direct-Access     Generic- Compact Flash    1.01 PQ: 0 ANSI: 0
[    5.839089] scsi 4:0:0:1: Direct-Access     Multiple Flash Reader     1.05 PQ: 0 ANSI: 0
[    5.839484] sd 4:0:0:0: Attached scsi generic sg2 type 0
[    5.839602] sd 4:0:0:1: Attached scsi generic sg3 type 0
[    5.841577] sd 4:0:0:0: [sdb] Attached SCSI removable disk
[    5.842329] sd 4:0:0:1: [sdc] Attached SCSI removable disk
[   12.597765] udev: starting version 151
[   12.699946] Adding 5277312k swap on /dev/sda7.  Priority:-1 extents:1 across:5277312k 
[   12.772524] i2c i2c-0: nForce2 SMBus adapter at 0x4d00
[   12.772544] i2c i2c-1: nForce2 SMBus adapter at 0x4e00
[   12.837192] vga16fb: initializing
[   12.837198] vga16fb: mapped to 0xc00a0000
[   12.837273] fb0: VGA16 VGA frame buffer device
[   12.842620] acer-wmi: Acer Laptop ACPI-WMI Extras
[   12.842634] acer-wmi: No or unsupported WMI interface, unable to load
[   12.861957] Linux video capture interface: v2.00
[   12.863428] lp: driver loaded but no devices found
[   12.864042] gspca: main v2.7.0 registered
[   12.869354] gspca: probing 045e:00f5
[   12.874549] Linux agpgart interface v0.103
[   12.881355] sonixj: Sonix chip id: 11
[   12.887422] gspca: probe ok
[   12.887434] gspca: probing 045e:00f5
[   12.887442] gspca: probing 045e:00f5
[   12.887457] usbcore: registered new interface driver sonixj
[   12.887460] sonixj: registered
[   12.914132] type=1505 audit(1273087707.950:2):  operation="profile_load" pid=607 name="/sbin/dhclient3"
[   12.914749] type=1505 audit(1273087707.950:3):  operation="profile_load" pid=607 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[   12.915079] type=1505 audit(1273087707.950:4):  operation="profile_load" pid=607 name="/usr/lib/connman/scripts/dhclient-script"
[   13.068410] Console: switching to colour frame buffer device 80x30
[   13.078874] HDA Intel 0000:00:09.0: power state changed by ACPI to D0
[   13.079913] ACPI: PCI Interrupt Link [LAZA] enabled at IRQ 23
[   13.079920] HDA Intel 0000:00:09.0: PCI INT A -> Link[LAZA] -> GSI 23 (level, low) -> IRQ 23
[   13.079925] hda_intel: Disable MSI for Nvidia chipset
[   13.079968] HDA Intel 0000:00:09.0: setting latency timer to 64
[   13.149769] usbcore: registered new interface driver snd-usb-audio
[   13.182907] psmouse serio1: ID: 10 00 64
[   13.344750] nvidia: module license 'NVIDIA' taints kernel.
[   13.344754] Disabling lock debugging due to kernel taint
[   13.772158] input: ImPS/2 Generic Wheel Mouse as /devices/platform/i8042/serio1/input/input4
[   14.356117] input: HDA Digital PCBeep as /devices/pci0000:00/0000:00:09.0/input/input5
[   14.624611] ACPI: PCI Interrupt Link [SGRU] enabled at IRQ 22
[   14.624618] nvidia 0000:00:10.0: PCI INT A -> Link[SGRU] -> GSI 22 (level, low) -> IRQ 22
[   14.624626] nvidia 0000:00:10.0: setting latency timer to 64
[   14.624630] vgaarb: device changed decodes: PCI:0000:00:10.0,olddecodes=io+mem,decodes=none:owns=io+mem
[   14.624823] NVRM: loading NVIDIA UNIX x86 Kernel Module  195.36.15  Thu Mar 11 21:41:46 PST 2010
[   14.755854] type=1505 audit(1273087709.789:5):  operation="profile_load" pid=834 name="/usr/share/gdm/guest-session/Xsession"
[   14.757632] type=1505 audit(1273087709.793:6):  operation="profile_replace" pid=835 name="/sbin/dhclient3"
[   14.758271] type=1505 audit(1273087709.793:7):  operation="profile_replace" pid=835 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[   14.758607] type=1505 audit(1273087709.793:8):  operation="profile_replace" pid=835 name="/usr/lib/connman/scripts/dhclient-script"
[   15.155252] type=1505 audit(1273087710.189:9):  operation="profile_load" pid=919 name="/usr/bin/evince"
[   15.163774] type=1505 audit(1273087710.197:10):  operation="profile_load" pid=919 name="/usr/bin/evince-previewer"
[   15.168854] type=1505 audit(1273087710.205:11):  operation="profile_load" pid=919 name="/usr/bin/evince-thumbnailer"
[   15.376482] RPC: Registered udp transport module.
[   15.376485] RPC: Registered tcp transport module.
[   15.376487] RPC: Registered tcp NFSv4.1 backchannel transport module.
[   15.401141] Installing knfsd (copyright (C) 1996 [email]okir@monad.swb.de[/email]).
[   15.510443] svc: failed to register lockdv1 RPC service (errno 97).
[   15.511210] NFSD: Using /var/lib/nfs/v4recovery as the NFSv4 state recovery directory
[   15.533839] NFSD: starting 90-second grace period
[   16.508566] ppdev: user-space parallel port driver
[   16.917228] CPU0 attaching NULL sched-domain.
[   16.917233] CPU1 attaching NULL sched-domain.
[   16.940093] CPU0 attaching sched-domain:
[   16.940098]  domain 0: span 0-1 level MC
[   16.940103]   groups: 0 1
[   16.940111] CPU1 attaching sched-domain:
[   16.940115]  domain 0: span 0-1 level MC
[   16.940119]   groups: 1 0
[   18.892632] CPU0 attaching NULL sched-domain.
[   18.892639] CPU1 attaching NULL sched-domain.
[   18.916575] CPU0 attaching sched-domain:
[   18.916580]  domain 0: span 0-1 level MC
[   18.916582]   groups: 0 1
[   18.916588] CPU1 attaching sched-domain:
[   18.916590]  domain 0: span 0-1 level MC
[   18.916592]   groups: 1 0
[  465.384531] usb 1-7: new high speed USB device using ehci_hcd and address 4
[  465.518929] usb 1-7: configuration #1 chosen from 2 choices
[  465.519571] scsi7 : SCSI emulation for USB Mass Storage devices
[  465.519774] usb-storage: device found at 4
[  465.519777] usb-storage: waiting for device to settle before scanning
[  467.906802] UDF-fs: Partition marked readonly; forcing readonly mount
[  467.980050] UDF-fs INFO UDF: Mounting volume 'MADONNA', timestamp 2006/12/20 17:41 (1f10)
[  470.516302] usb-storage: device scan complete
[  470.518794] scsi 7:0:0:0: Direct-Access     Apple    iPod             1.62 PQ: 0 ANSI: 0
[  470.519475] sd 7:0:0:0: Attached scsi generic sg4 type 0
[  470.525042] sd 7:0:0:0: [sdd] 39075372 2048-byte logical blocks: (80.0 GB/74.5 GiB)
[  470.528732] sd 7:0:0:0: [sdd] Write Protect is off
[  470.528738] sd 7:0:0:0: [sdd] Mode Sense: 68 00 00 08
[  470.528743] sd 7:0:0:0: [sdd] Assuming drive cache: write through
[  470.531022] sd 7:0:0:0: [sdd] 39075372 2048-byte logical blocks: (80.0 GB/74.5 GiB)
[  470.533516] sd 7:0:0:0: [sdd] Assuming drive cache: write through
[  470.533524]  sdd: sdd1 sdd2
[  470.567535] sd 7:0:0:0: [sdd] 39075372 2048-byte logical blocks: (80.0 GB/74.5 GiB)
[  470.570550] sd 7:0:0:0: [sdd] Assuming drive cache: write through
[  470.570559] sd 7:0:0:0: [sdd] Attached SCSI removable disk
[  471.781393] FAT: invalid media value (0x2f)
[  471.781400] VFS: Can't find a valid FAT filesystem on dev sdd1.
[  472.765623] FAT: invalid media value (0x2f)
[  472.765630] VFS: Can't find a valid FAT filesystem on dev sdd1.
[  473.435786] FAT: invalid media value (0x2f)
[  473.435793] VFS: Can't find a valid FAT filesystem on dev sdd1.

---

### Post by sir_nasty on 2010-05-07
weird... I don't even see it trying to load the drivers..... grab a cd and burn a copy of Ubuntu live CD, boot off that and see if it loads the drivers.  If not, then for me to be of much help I'd need to know the specs on what brand your nic card is...

---

