---
title: "Gnome seems to freeze, but mouse cursor updates correctly..."
date: 2010-04-29
forum: General Help
---

### Post by murderslastcrow on 2010-04-29
I'm getting a little sick of this. After I installed the RC, about a day or two ago, my computer suddenly started to lock up for no apparent reason. I thought it might be Flash, so I used flashblock, but nothing changed- even when I'm just running GIMP and Blender, it'll just start freezing out of nowhere.

However, don't know if this is odd or not, but the mouse moves around just like normal, no freezing, and it even changes to accommodate for text or clickable objects immediately, even before I see them (after closing a browser window, if there's gedit behind that window, it will change to the text cursor immediately before I can see the web browser is gone).

So, some more data- I was wondering if it was the X server leak that was apparently fixed (my Lucid is fully updated), but I installed mesa-utils and checked GLX version and it says 1.2, which as far as I know is the correct version (1.4 had the glitches, right?).

Anyway, some more data about my computer.

OS: Ubuntu 10.04 Lucid Lynx 64-bit.
Computer: Dell E1505.
CPU: Core2Duo 1.83 Ghz per core.
RAM: 2 GB.
Video Card : ATI X1400 with open source drivers since Catalyst doesn't support it anymore.
HD: 80 GB.

Installed software beyond default install: Docky, Stalonetray, Gnome-DO, VLC, gtk-RecordmyDesktop, Ubuntu-Restricted-Extras, Wine (Beta), and 7zip.

Also edited gconf to remove gnome-panel as a required component on startup, if that's relevant.

I don't know what else to tell you guys- I'll try to bring up the System Monitor to check CPU and RAM usage by order next time it happens, to see if it's something like that.

It should be noted that my computer isn't overheating and the video card isn't working too hard (fans aren't on) during more than half of these occurrences.

---

### Post by P4man on 2010-04-29
Its not clear to me what the issue is exactly. You can move the mouse and close windows apparently? what is not working then? Is the keyboard still responsive? does control+alt+f1 still give you a full screen tty ? (control alt+f7 to return).

---

### Post by murderslastcrow on 2010-04-29
The issue is that the display seems to refresh once every 10 minutes (that's an exaggeration- it's more like 10-15 seconds before I get one frame of the GUI appearing to me). So basically, I can't see it when I move windows around, click on something, and the FPS basically drops to 0.2 frames per second. It's not just slowed or slurred, but it freezes and only refreshes after a short time, and it doesn't come back to normal speed unless I restart the computer.

I'm just really not used to having this sort of issue with Linux, and it's kinda' freaking me out since I makes no sense to me. XD

I should also mention that I installed Google Chrome from their website and use that as my default browser, as well. Sorry for being unclear about the basic issue.

---

### Post by murderslastcrow on 2010-04-29
I'll have to try to drop to command line next time, as I'm sure that would work if the cursor itself is moving at normal speed, while the GUI itself is only showing every 10-15 seconds.

---

### Post by P4man on 2010-04-29
okay, I see now.
Well, can you find out if any process has gone all crazy? open a terminal and type

```
top
```

and see if something jumps at you (excessive memory and/or cpu usage)

If there is nonstop hdd activity, run 

```
iotop
```

(need to install that probably).

---

### Post by murderslastcrow on 2010-04-29
Well, the processes are almost hilariously low. Without flash running, I top out at 570 MB RAM usage, with Docky and Gnome up, compiz running. Never using swap for obvious reasons.

My CPUs don't get more than about 20 percent each. However, this is when it's not frozen. Still trying to induce it and reproduce it. Gonna' turn off flashblock and see what happens on a few flash-heavy sites...

K, with flash (npviewer) on, it takes up about 63 CPU, and 55 MB of RAM by itself, even with only a game or two up with an ad.... k, somehow it dropped to 13 percent CPU now and 3.5 MB RAM. Probably because the game's animations stopped and I'm at a results screen.

Lol, yep, shot up as soon as I started it over again. But still, no issues with the freezing. Gonna' open GIMP and start drawing.

Okay, gone about a half hour and nothing's going on. So I'll just leave flash on and see what happens, post again the next time it happens. I didn't change anything, no updates, so it shouldn't have stopped, but I guess it's fixed until further notice?

Jeez, I hope HTML5 replaces everything I use flash for soon. Anyone know of a good music-streaming site that uses HTML5? (lol, in a support thread, what's wrong with me)

---

### Post by murderslastcrow on 2010-04-30
Okay, it happened again, with only Wine and Eye of Gnome running.

When I dropped to console and ran top, a process called ksoftirqd/0 or ksoftirqd/1 kept popping up to the top of the process list then dropping again. The only other processes up that high were Xorg and my actual programs (wineserver, eog, chrome, etc.). ksoftirqd is owned by root in both instances, and usually only ranges around 4 CPU, but every now and again jumped up to about 20 or 30.

Again, I've run Karmic on this computer for months without any issues. I hope someone can help solve this issue for me, since it's becoming more and more obscure as it progresses. It's so confusing! D: *googles everything related in the meantime*

---

### Post by murderslastcrow on 2010-04-30
I have some screenshots of my top results in an image file, within an archive. Hopefully these will give some sort of idea to where the problem is originating from.

---

### Post by P4man on 2010-04-30
I dont see anything out of the ordinary in those. 

What about dmesg ? Anything in there?

Also, have a look at disk utility and check the smart status of your drive. The behaviour you see might be consistent with problems with I/O.

---

### Post by murderslastcrow on 2010-04-30
Well, disk utility doesn't show anything unusual, and I haven't had a chance to run dmesg during or recently after the issue. Ironically, it just happened after I typed that, and here's the dmesg output.

[    0.476796] pci 0000:00:1e.0: transparent bridge
[    0.476807] pci 0000:00:1e.0: bridge 32bit mmio: [0xef900000-0xef9fffff]
[    0.476887] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.477669] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.AGP_._PRT]
[    0.477864] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCIE._PRT]
[    0.478111] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP01._PRT]
[    0.478339] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP04._PRT]
[    0.505841] ACPI: PCI Interrupt Link [LNKA] (IRQs 9 10 11) *4
[    0.506191] ACPI: PCI Interrupt Link [LNKB] (IRQs *5 7)
[    0.506521] ACPI: PCI Interrupt Link [LNKC] (IRQs *9 10 11)
[    0.506863] ACPI: PCI Interrupt Link [LNKD] (IRQs 5 7 9 10 11) *3
[    0.507214] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 9 *10 11 12 14 15)
[    0.507564] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)
[    0.507899] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 *9 10 11 12 14 15)
[    0.508250] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 *7 9 10 11 12 14 15)
[    0.508663] vgaarb: device added: PCI:0000:01:00.0,decodes=io+mem,owns=io+mem,locks=none
[    0.508689] vgaarb: loaded
[    0.509017] SCSI subsystem initialized
[    0.509268] libata version 3.00 loaded.
[    0.509486] usbcore: registered new interface driver usbfs
[    0.509521] usbcore: registered new interface driver hub
[    0.509593] usbcore: registered new device driver usb
[    0.510146] ACPI: WMI: Mapper loaded
[    0.510150] PCI: Using ACPI for IRQ routing
[    0.510639] NetLabel: Initializing
[    0.510653] NetLabel:  domain hash size = 128
[    0.510656] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.510700] NetLabel:  unlabeled traffic allowed by default
[    0.510815] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[    0.510825] hpet0: 3 comparators, 64-bit 14.318180 MHz counter
[    0.520239] Switching to clocksource hpet
[    0.525429] AppArmor: AppArmor Filesystem Enabled
[    0.525468] pnp: PnP ACPI init
[    0.525518] ACPI: bus type pnp registered
[    0.605359] pnp 00:02: io resource (0x1000-0x1005) overlaps 0000:00:1f.0 BAR 13 (0x1000-0x107f), disabling
[    0.605369] pnp 00:02: io resource (0x1008-0x100f) overlaps 0000:00:1f.0 BAR 13 (0x1000-0x107f), disabling
[    0.605624] pnp 00:03: io resource (0x1006-0x1007) overlaps 0000:00:1f.0 BAR 13 (0x1000-0x107f), disabling
[    0.605631] pnp 00:03: io resource (0x100a-0x1059) overlaps 0000:00:1f.0 BAR 13 (0x1000-0x107f), disabling
[    0.605648] pnp 00:03: io resource (0x1060-0x107f) overlaps 0000:00:1f.0 BAR 13 (0x1000-0x107f), disabling
[    0.605655] pnp 00:03: io resource (0x1010-0x102f) overlaps 0000:00:1f.0 BAR 13 (0x1000-0x107f), disabling
[    0.608728] pnp: PnP ACPI: found 12 devices
[    0.608733] ACPI: ACPI bus type pnp unregistered
[    0.608780] system 00:00: iomem range 0x0-0x9fbff could not be reserved
[    0.608787] system 00:00: iomem range 0x9fc00-0x9ffff could not be reserved
[    0.608792] system 00:00: iomem range 0xc0000-0xcffff has been reserved
[    0.608808] system 00:00: iomem range 0xe0000-0xfffff has been reserved
[    0.608815] system 00:00: iomem range 0x100000-0x7fed33ff could not be reserved
[    0.608821] system 00:00: iomem range 0x7fed3400-0x7fefffff has been reserved
[    0.608827] system 00:00: iomem range 0x7ff00000-0x7fffffff has been reserved
[    0.608843] system 00:00: iomem range 0xffb00000-0xffffffff has been reserved
[    0.608850] system 00:00: iomem range 0xfec00000-0xfec0ffff could not be reserved
[    0.608856] system 00:00: iomem range 0xfee00000-0xfee0ffff has been reserved
[    0.608872] system 00:00: iomem range 0xfed20000-0xfed9ffff has been reserved
[    0.608879] system 00:00: iomem range 0xffa80000-0xffa83fff could not be reserved
[    0.608885] system 00:00: iomem range 0xf4000000-0xf4003fff has been reserved
[    0.608890] system 00:00: iomem range 0xf4004000-0xf4004fff has been reserved
[    0.608907] system 00:00: iomem range 0xf4005000-0xf4005fff has been reserved
[    0.608913] system 00:00: iomem range 0xf4006000-0xf4006fff has been reserved
[    0.608919] system 00:00: iomem range 0xf4008000-0xf400bfff has been reserved
[    0.608925] system 00:00: iomem range 0xf0000000-0xf3ffffff has been reserved
[    0.608950] system 00:02: ioport range 0x4d0-0x4d1 has been reserved
[    0.608972] system 00:03: ioport range 0xf400-0xf4fe has been reserved
[    0.608978] system 00:03: ioport range 0x1080-0x10bf has been reserved
[    0.608984] system 00:03: ioport range 0x10c0-0x10df has been reserved
[    0.609000] system 00:03: ioport range 0x809-0x809 has been reserved
[    0.609020] system 00:08: ioport range 0xc80-0xcff could not be reserved
[    0.609036] system 00:08: ioport range 0x910-0x91f has been reserved
[    0.609041] system 00:08: ioport range 0x920-0x92f has been reserved
[    0.609047] system 00:08: ioport range 0xcb0-0xcbf has been reserved
[    0.609053] system 00:08: ioport range 0x930-0x97f has been reserved
[    0.609081] system 00:0b: iomem range 0xfed00000-0xfed003ff has been reserved
[    0.614336] pci 0000:00:01.0: PCI bridge, secondary bus 0000:01
[    0.614343] pci 0000:00:01.0:   IO window: 0xe000-0xefff
[    0.614361] pci 0000:00:01.0:   MEM window: 0xefd00000-0xefefffff
[    0.614369] pci 0000:00:01.0:   PREFETCH window: 0x000000d0000000-0x000000dfffffff
[    0.614378] pci 0000:00:1c.0: PCI bridge, secondary bus 0000:0b
[    0.614394] pci 0000:00:1c.0:   IO window: 0x2000-0x2fff
[    0.614404] pci 0000:00:1c.0:   MEM window: 0xefc00000-0xefcfffff
[    0.614422] pci 0000:00:1c.0:   PREFETCH window: 0x000000e0000000-0x000000e00fffff
[    0.614434] pci 0000:00:1c.3: PCI bridge, secondary bus 0000:0c
[    0.614440] pci 0000:00:1c.3:   IO window: 0xd000-0xdfff
[    0.614460] pci 0000:00:1c.3:   MEM window: 0xefa00000-0xefbfffff
[    0.614468] pci 0000:00:1c.3:   PREFETCH window: 0x000000e0100000-0x000000e03fffff
[    0.614492] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:03
[    0.614496] pci 0000:00:1e.0:   IO window: disabled
[    0.614505] pci 0000:00:1e.0:   MEM window: 0xef900000-0xef9fffff
[    0.614523] pci 0000:00:1e.0:   PREFETCH window: disabled
[    0.614559]   alloc irq_desc for 16 on node -1
[    0.614563]   alloc kstat_irqs on node -1
[    0.614583] pci 0000:00:01.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.614591] pci 0000:00:01.0: setting latency timer to 64
[    0.614617] pci 0000:00:1c.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.614625] pci 0000:00:1c.0: setting latency timer to 64
[    0.614650]   alloc irq_desc for 19 on node -1
[    0.614653]   alloc kstat_irqs on node -1
[    0.614660] pci 0000:00:1c.3: PCI INT D -> GSI 19 (level, low) -> IRQ 19
[    0.614678] pci 0000:00:1c.3: setting latency timer to 64
[    0.614691] pci 0000:00:1e.0: setting latency timer to 64
[    0.614699] pci_bus 0000:00: resource 0 io:  [0x00-0xffff]
[    0.614715] pci_bus 0000:00: resource 1 mem: [0x000000-0xffffffffffffffff]
[    0.614720] pci_bus 0000:01: resource 0 io:  [0xe000-0xefff]
[    0.614725] pci_bus 0000:01: resource 1 mem: [0xefd00000-0xefefffff]
[    0.614730] pci_bus 0000:01: resource 2 pref mem [0xd0000000-0xdfffffff]
[    0.614746] pci_bus 0000:0b: resource 0 io:  [0x2000-0x2fff]
[    0.614750] pci_bus 0000:0b: resource 1 mem: [0xefc00000-0xefcfffff]
[    0.614755] pci_bus 0000:0b: resource 2 pref mem [0xe0000000-0xe00fffff]
[    0.614760] pci_bus 0000:0c: resource 0 io:  [0xd000-0xdfff]
[    0.614775] pci_bus 0000:0c: resource 1 mem: [0xefa00000-0xefbfffff]
[    0.614780] pci_bus 0000:0c: resource 2 pref mem [0xe0100000-0xe03fffff]
[    0.614786] pci_bus 0000:03: resource 1 mem: [0xef900000-0xef9fffff]
[    0.614790] pci_bus 0000:03: resource 3 io:  [0x00-0xffff]
[    0.614795] pci_bus 0000:03: resource 4 mem: [0x000000-0xffffffffffffffff]
[    0.614914] NET: Registered protocol family 2
[    0.615322] IP route cache hash table entries: 65536 (order: 7, 524288 bytes)
[    0.617505] TCP established hash table entries: 262144 (order: 10, 4194304 bytes)
[    0.622672] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[    0.623993] TCP: Hash tables configured (established 262144 bind 65536)
[    0.624010] TCP reno registered
[    0.624277] NET: Registered protocol family 1
[    0.624535] pci 0000:01:00.0: Boot video device
[    0.624746] Simple Boot Flag at 0x79 set to 0x1
[    0.625295] Scanning for low memory corruption every 60 seconds
[    0.625716] audit: initializing netlink socket (disabled)
[    0.625745] type=2000 audit(1272679196.620:1): initialized
[    0.654906] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    0.659125] VFS: Disk quotas dquot_6.5.2
[    0.659288] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    0.661126] fuse init (API version 7.13)
[    0.661364] msgmni has been set to 3999
[    0.661997] alg: No test for stdrng (krng)
[    0.662155] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.662161] io scheduler noop registered
[    0.662165] io scheduler anticipatory registered
[    0.662179] io scheduler deadline registered
[    0.662279] io scheduler cfq registered (default)
[    0.662694]   alloc irq_desc for 24 on node -1
[    0.662698]   alloc kstat_irqs on node -1
[    0.662725] pcieport 0000:00:01.0: irq 24 for MSI/MSI-X
[    0.662737] pcieport 0000:00:01.0: setting latency timer to 64
[    0.663022]   alloc irq_desc for 25 on node -1
[    0.663026]   alloc kstat_irqs on node -1
[    0.663050] pcieport 0000:00:1c.0: irq 25 for MSI/MSI-X
[    0.663076] pcieport 0000:00:1c.0: setting latency timer to 64
[    0.663404]   alloc irq_desc for 26 on node -1
[    0.663408]   alloc kstat_irqs on node -1
[    0.663432] pcieport 0000:00:1c.3: irq 26 for MSI/MSI-X
[    0.663447] pcieport 0000:00:1c.3: setting latency timer to 64
[    0.663706] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.663943] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.664816] ACPI: AC Adapter [AC] (off-line)
[    0.665152] input: Lid Switch as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0D:00/input/input0
[    0.665881] ACPI: Lid Switch [LID]
[    0.666014] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input1
[    0.666024] ACPI: Power Button [PBTN]
[    0.666168] input: Sleep Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0E:00/input/input2
[    0.666174] ACPI: Sleep Button [SBTN]
[    0.667996] ACPI: SSDT 000000007fed4176 00202 (v01  PmRef  Cpu0Ist 00003000 INTL 20050624)
[    0.668922] ACPI: SSDT 000000007fed3f2b 001C6 (v01  PmRef  Cpu0Cst 00003001 INTL 20050624)
[    0.670087] processor LNXCPU:00: registered as cooling_device0
[    0.671068] ACPI: SSDT 000000007fed4378 000C4 (v01  PmRef  Cpu1Ist 00003000 INTL 20050624)
[    0.671858] ACPI: SSDT 000000007fed40f1 00085 (v01  PmRef  Cpu1Cst 00003000 INTL 20050624)
[    0.673631] processor LNXCPU:01: registered as cooling_device1
[    0.689086] thermal LNXTHERM:01: registered as thermal_zone0
[    0.689114] ACPI: Thermal Zone [THM] (25 C)
[    0.693470] Linux agpgart interface v0.103
[    0.693570] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    0.697343] brd: module loaded
[    0.698764] loop: module loaded
[    0.699035] input: Macintosh mouse button emulation as /devices/virtual/input/input3
[    0.699299] ata_piix 0000:00:1f.2: version 2.13
[    0.699337]   alloc irq_desc for 17 on node -1
[    0.699341]   alloc kstat_irqs on node -1
[    0.699365] ata_piix 0000:00:1f.2: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    0.699374] ata_piix 0000:00:1f.2: MAP [ P0 P2 IDE IDE ]
[    0.699486] ata_piix 0000:00:1f.2: setting latency timer to 64
[    0.712534] scsi0 : ata_piix
[    0.722549] scsi1 : ata_piix
[    0.751251] ata1: SATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xbfa0 irq 14
[    0.751268] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xbfa8 irq 15
[    0.752331] Fixed MDIO Bus: probed
[    0.752436] PPP generic driver version 2.4.2
[    0.752612] tun: Universal TUN/TAP device driver, 1.6
[    0.752627] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.752891] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.752953]   alloc irq_desc for 20 on node -1
[    0.752957]   alloc kstat_irqs on node -1
[    0.752979] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    0.753022] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    0.753028] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    0.753141] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 1
[    0.753187] ehci_hcd 0000:00:1d.7: using broken periodic workaround
[    0.753216] ehci_hcd 0000:00:1d.7: debug port 1
[    0.757098] ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported
[    0.757148] ehci_hcd 0000:00:1d.7: irq 20, io mem 0xffa80000
[    0.789618] ACPI: Battery Slot [BAT0] (battery present)
[    0.802539] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    0.802844] usb usb1: configuration #1 chosen from 1 choice
[    0.802933] hub 1-0:1.0: USB hub found
[    0.802959] hub 1-0:1.0: 8 ports detected
[    0.803158] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.803212] uhci_hcd: USB Universal Host Controller Interface driver
[    0.803310] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    0.803336] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    0.803343] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    0.803444] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    0.803509] uhci_hcd 0000:00:1d.0: irq 20, io base 0x0000bf80
[    0.803767] usb usb2: configuration #1 chosen from 1 choice
[    0.803850] hub 2-0:1.0: USB hub found
[    0.803862] hub 2-0:1.0: 2 ports detected
[    0.803996]   alloc irq_desc for 21 on node -1
[    0.804010]   alloc kstat_irqs on node -1
[    0.804022] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[    0.804043] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    0.804049] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    0.804156] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 3
[    0.804238] uhci_hcd 0000:00:1d.1: irq 21, io base 0x0000bf60
[    0.804477] usb usb3: configuration #1 chosen from 1 choice
[    0.804559] hub 3-0:1.0: USB hub found
[    0.804571] hub 3-0:1.0: 2 ports detected
[    0.804697]   alloc irq_desc for 22 on node -1
[    0.804701]   alloc kstat_irqs on node -1
[    0.804720] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 22 (level, low) -> IRQ 22
[    0.804735] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    0.804751] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    0.804862] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 4
[    0.804940] uhci_hcd 0000:00:1d.2: irq 22, io base 0x0000bf40
[    0.805178] usb usb4: configuration #1 chosen from 1 choice
[    0.805265] hub 4-0:1.0: USB hub found
[    0.805280] hub 4-0:1.0: 2 ports detected
[    0.805402]   alloc irq_desc for 23 on node -1
[    0.805406]   alloc kstat_irqs on node -1
[    0.805425] uhci_hcd 0000:00:1d.3: PCI INT D -> GSI 23 (level, low) -> IRQ 23
[    0.805436] uhci_hcd 0000:00:1d.3: setting latency timer to 64
[    0.805452] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[    0.805581] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 5
[    0.805646] uhci_hcd 0000:00:1d.3: irq 23, io base 0x0000bf20
[    0.805878] usb usb5: configuration #1 chosen from 1 choice
[    0.805965] hub 5-0:1.0: USB hub found
[    0.805977] hub 5-0:1.0: 2 ports detected
[    0.806262] PNP: PS/2 Controller [PNP0303:KBC,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    0.809025] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.809052] serio: i8042 AUX port at 0x60,0x64 irq 12
[    0.809288] mice: PS/2 mouse device common for all mice
[    0.809631] rtc_cmos 00:06: RTC can wake from S4
[    0.809739] rtc_cmos 00:06: rtc core: registered rtc_cmos as rtc0
[    0.809804] rtc0: alarms up to one month, y3k, 114 bytes nvram, hpet irqs
[    0.810179] device-mapper: uevent: version 1.0.3
[    0.810481] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: [email]dm-devel@redhat.com[/email]
[    0.810660] device-mapper: multipath: version 1.1.0 loaded
[    0.810665] device-mapper: multipath round-robin: version 1.0.0 loaded
[    0.811282] cpuidle: using governor ladder
[    0.811621] cpuidle: using governor menu
[    0.812704] TCP cubic registered
[    0.813072] NET: Registered protocol family 10
[    0.814363] lo: Disabled Privacy Extensions
[    0.814869] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input4
[    0.815217] NET: Registered protocol family 17
[    0.816417] PM: Resume from disk failed.
[    0.816448] registered taskstats version 1
[    0.817147]   Magic number: 10:611:962
[    0.817327] rtc_cmos 00:06: setting system clock to 2010-05-01 01:59:57 UTC (1272679197)
[    0.817331] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.817333] EDD information not available.
[    0.899330] Freeing initrd memory: 8139k freed
[    0.941188] ata1.00: failed to set max address (err_mask=0x1)
[    0.941192] ata1.00: device aborted resize (114270345 -> 117210240), skipping HPA handling
[    0.941198] ata1.00: ATA-7: FUJITSU MHV2060BH, 0085002A, max UDMA/100
[    0.941211] ata1.00: 114270345 sectors, multi 8: LBA48 NCQ (depth 0/32)
[    0.960630] ata2.00: ATAPI: TSSTcorp DVD+/-RW TS-L632D, DE03, max UDMA/33
[    0.980674] ata1.00: configured for UDMA/100
[    0.980921] scsi 0:0:0:0: Direct-Access     ATA      FUJITSU MHV2060B 0085 PQ: 0 ANSI: 5
[    0.981216] sd 0:0:0:0: [sda] 114270345 512-byte logical blocks: (58.5 GB/54.4 GiB)
[    0.981271] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    0.981306] sd 0:0:0:0: [sda] Write Protect is off
[    0.981309] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    0.981349] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    0.981627]  sda: sda1 sda2 < sda5
[    1.020447] ata2.00: configured for UDMA/33
[    1.034613]  sda6 >
[    1.035150] sd 0:0:0:0: [sda] Attached SCSI disk
[    1.100765] scsi 1:0:0:0: CD-ROM            TSSTcorp DVD+-RW TS-L632D DE03 PQ: 0 ANSI: 5
[    1.208602] sr0: scsi3-mmc drive: 24x/24x writer cd/rw xa/form2 cdda tray
[    1.208605] Uniform CD-ROM driver Revision: 3.20
[    1.208731] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    1.208810] sr 1:0:0:0: Attached scsi generic sg1 type 5
[    1.208885] Freeing unused kernel memory: 876k freed
[    1.209527] Write protecting the kernel read-only data: 7680k
[    1.236028] udev: starting version 151
[    1.459765] ohci1394 0000:03:01.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    1.522380] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[19]  MMIO=[ef9fd800-ef9fdfff]  Max Packet=[2048]  IR/IT contexts=[4/4]
[    1.570099] usb 5-2: new full speed USB device using uhci_hcd and address 2
[    1.755912] usb 5-2: configuration #1 chosen from 1 choice
[    1.979134] EXT4-fs (sda5): mounted filesystem with ordered data mode
[    2.842947] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[344fc0000aeb7541]
[   22.302872] udev: starting version 151
[   22.371502] Adding 1917944k swap on /dev/sda6.  Priority:-1 extents:1 across:1917944k 
[   22.536810] intel_rng: FWH not detected
[   22.566011] lib80211: common routines for IEEE802.11 drivers
[   22.566015] lib80211_crypt: registered algorithm 'NULL'
[   22.572859] [drm] Initialized drm 1.1.0 20060810
[   22.612364] acpi device:23: registered as cooling_device2
[   22.613151] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A03:00/device:20/LNXVIDEO:00/input/input5
[   22.613249] ACPI: Video Device [VID] (multi-head: yes  rom: no  post: no)
[   22.619242] ricoh-mmc: Ricoh MMC Controller disabling driver
[   22.619245] ricoh-mmc: Copyright(c) Philip Langdale
[   22.619281] ricoh-mmc: Ricoh MMC controller found at 0000:03:01.2 [1180:0843] (rev 1)
[   22.619300] ricoh-mmc: Controller is now disabled.
[   22.622436] sdhci: Secure Digital Host Controller Interface driver
[   22.622439] sdhci: Copyright(c) Pierre Ossman
[   22.625747] dcdbas dcdbas: Dell Systems Management Base Driver (version 5.6.0-3.2)
[   22.633694] sdhci-pci 0000:03:01.1: SDHCI controller found [1180:0822] (rev 19)
[   22.633716]   alloc irq_desc for 18 on node -1
[   22.633718]   alloc kstat_irqs on node -1
[   22.633727] sdhci-pci 0000:03:01.1: PCI INT B -> GSI 18 (level, low) -> IRQ 18
[   22.635841] Registered led device: mmc0::
[   22.636918] mmc0: SDHCI controller on PCI [0000:03:01.1] using DMA
[   22.652797] Bluetooth: Core ver 2.15
[   22.657551] NET: Registered protocol family 31
[   22.657554] Bluetooth: HCI device and connection manager initialized
[   22.657558] Bluetooth: HCI socket layer initialized
[   22.659199] Bluetooth: Generic Bluetooth USB driver ver 0.6
[   22.659329] usbcore: registered new interface driver btusb
[   22.666909] lp: driver loaded but no devices found
[   22.667310] wl: module license 'MIXED/Proprietary' taints kernel.
[   22.667314] Disabling lock debugging due to kernel taint
[   22.673113] input: Dell WMI hotkeys as /devices/virtual/input/input6
[   22.676119] type=1505 audit(1272679219.352:2):  operation="profile_load" pid=645 name="/sbin/dhclient3"
[   22.676860] type=1505 audit(1272679219.352:3):  operation="profile_load" pid=645 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[   22.677258] type=1505 audit(1272679219.352:4):  operation="profile_load" pid=645 name="/usr/lib/connman/scripts/dhclient-script"
[   22.712955] wl 0000:0b:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   22.712965] wl 0000:0b:00.0: setting latency timer to 64
[   22.739898] [drm] radeon defaulting to kernel modesetting.
[   22.739902] [drm] radeon kernel modesetting enabled.
[   22.739961] radeon 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   22.739969] radeon 0000:01:00.0: setting latency timer to 64
[   22.745071] [drm] radeon: Initializing kernel modesetting.
[   22.750175] lib80211_crypt: registered algorithm 'TKIP'
[   22.750328] eth0: Broadcom BCM4328 802.11 Hybrid Wireless Controller 5.60.48.36 
[   22.754016] [drm] register mmio base: 0xEFDF0000
[   22.754019] [drm] register mmio size: 65536
[   22.754105] ATOM BIOS: M54P
[   22.754332] [drm] GPU reset succeed (RBBM_STATUS=0x10000140)
[   22.754357] [drm] Generation 2 PCI interface, using max accessible memory
[   22.754360] [drm] radeon: VRAM 128M
[   22.754362] [drm] radeon: VRAM from 0x00000000 to 0x07FFFFFF
[   22.754364] [drm] radeon: GTT 512M
[   22.754366] [drm] radeon: GTT from 0x20000000 to 0x3FFFFFFF
[   22.754428]   alloc irq_desc for 27 on node -1
[   22.754431]   alloc kstat_irqs on node -1
[   22.754446] radeon 0000:01:00.0: irq 27 for MSI/MSI-X
[   22.754455] [drm] radeon: using MSI.
[   22.754495] [drm] radeon: irq initialized.
[   22.755098] [drm] Detected VRAM RAM=128M, BAR=256M
[   22.755102] [drm] RAM width 64bits DDR
[   22.760973] [TTM] Zone  kernel: Available graphics memory: 1028458 kiB.
[   22.760993] [drm] radeon: 128M of VRAM memory ready
[   22.760996] [drm] radeon: 512M of GTT memory ready.
[   22.761011] [drm] GART: num cpu pages 131072, num gpu pages 131072
[   22.761960] usbcore: registered new interface driver wacom
[   22.762220] wacom: v1.52-pc-0.1:USB Wacom tablet driver
[   22.764417] [drm] RB2D reset succeed (RBBM_STATUS=0x10000140)
[   22.764441] [drm] radeon: 1 quad pipes, 1 z pipes initialized.
[   22.764793] [drm] PCIE GART of 512M enabled (table at 0x00040000).
[   22.765019] [drm] radeon: cp idle (0x10000C03)
[   22.765098] [drm] Loading R500 Microcode
[   22.765214] platform radeon_cp.0: firmware: requesting radeon/R520_cp.bin
[   22.777183] b44 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   22.784924] [drm] radeon: ring at 0x0000000020000000
[   22.784971] [drm] ring test succeeded in 4 usecs
[   22.785098] [drm] radeon: ib pool ready.
[   22.785195] [drm] ib test succeeded in 0 usecs
[   22.785371] [drm] Default TV standard: NTSC
[   22.785401] [drm] Radeon Display Connectors
[   22.785404] [drm] Connector 0:
[   22.785405] [drm]   VGA
[   22.785408] [drm]   DDC: 0x7e40 0x7e40 0x7e44 0x7e44 0x7e48 0x7e48 0x7e4c 0x7e4c
[   22.785410] [drm]   Encoders:
[   22.785412] [drm]     CRT1: INTERNAL_KLDSCP_DAC1
[   22.785414] [drm] Connector 1:
[   22.785415] [drm]   LVDS
[   22.785418] [drm]   DDC: 0x7e30 0x7e30 0x7e34 0x7e34 0x7e38 0x7e38 0x7e3c 0x7e3c
[   22.785419] [drm]   Encoders:
[   22.785421] [drm]     LCD1: INTERNAL_LVTM1
[   22.785423] [drm] Connector 2:
[   22.785425] [drm]   S-video
[   22.785426] [drm]   Encoders:
[   22.785428] [drm]     TV1: INTERNAL_KLDSCP_DAC2
[   22.856183] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[   22.856216] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   22.892676] ssb: Sonics Silicon Backplane found on PCI device 0000:03:00.0
[   22.892709] b44.c:v2.0
[   22.933599] eth1: Broadcom 44xx/47xx 10/100BaseT Ethernet 00:15:c5:b5:38:5d
[   22.940585] udev: renamed network interface eth0 to eth1
[   22.941144] udev: renamed network interface eth1_rename to eth0
[   23.040763] input: HDA Intel Mic at Ext Right Jack as /devices/pci0000:00/0000:00:1b.0/sound/card0/input7
[   23.040947] input: HDA Intel HP Out at Ext Right Jack as /devices/pci0000:00/0000:00:1b.0/sound/card0/input8
[   23.213896] type=1505 audit(1272679219.892:5):  operation="profile_load" pid=825 name="/usr/share/gdm/guest-session/Xsession"
[   23.215769] type=1505 audit(1272679219.892:6):  operation="profile_replace" pid=826 name="/sbin/dhclient3"
[   23.216519] type=1505 audit(1272679219.892:7):  operation="profile_replace" pid=826 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[   23.216924] type=1505 audit(1272679219.892:8):  operation="profile_replace" pid=826 name="/usr/lib/connman/scripts/dhclient-script"
[   23.220337] type=1505 audit(1272679219.902:9):  operation="profile_load" pid=827 name="/usr/bin/evince"
[   23.230780] type=1505 audit(1272679219.912:10):  operation="profile_load" pid=827 name="/usr/bin/evince-previewer"
[   23.237056] type=1505 audit(1272679219.912:11):  operation="profile_load" pid=827 name="/usr/bin/evince-thumbnailer"
[   23.301990] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   23.368075] Synaptics Touchpad, model: 1, fw: 6.2, id: 0x180b1, caps: 0xa04713/0x200000
[   23.393300] [drm] fb mappable at 0xD00C0000
[   23.393303] [drm] vram apper at 0xD0000000
[   23.393305] [drm] size 4096000
[   23.393307] [drm] fb depth is 24
[   23.393309] [drm]    pitch is 5120
[   23.393621] fb0: radeondrmfb frame buffer device
[   23.393624] registered panic notifier
[   23.393630] [drm] Initialized radeon 2.0.0 20080528 for 0000:01:00.0 on minor 0
[   23.395913] vga16fb: initializing
[   23.395918] vga16fb: mapped to 0xffff8800000a0000
[   23.395923] vga16fb: not registering due to another framebuffer present
[   23.409255] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input9
[   23.683750] Console: switching to colour frame buffer device 160x50
[   24.125196] vboxdrv: Trying to deactivate the NMI watchdog permanently...
[   24.125200] vboxdrv: Successfully done.
[   24.125202] vboxdrv: Found 2 processor cores.
[   24.125282] VBoxDrv: dbg - g_abExecMemory=ffffffffa0526a20
[   24.125294] vboxdrv: fAsync=1 offMin=0xebc18327 offMax=0xebc18327
[   24.125367] vboxdrv: TSC mode is 'asynchronous', kernel timer mode is 'normal'.
[   24.125370] vboxdrv: Successfully loaded version 3.1.6 (interface 0x00100001).
[   24.412481] Bluetooth: L2CAP ver 2.14
[   24.412526] Bluetooth: L2CAP socket layer initialized
[   24.418301] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   24.418306] Bluetooth: BNEP filters: protocol multicast
[   24.425636] Bridge firewalling registered
[   24.432288] Bluetooth: SCO (Voice Link) ver 0.6
[   24.432291] Bluetooth: SCO socket layer initialized
[   24.467609] ppdev: user-space parallel port driver
[   24.544572] Bluetooth: RFCOMM TTY layer initialized
[   24.544579] Bluetooth: RFCOMM socket layer initialized
[   24.544581] Bluetooth: RFCOMM ver 1.11
[   33.732526] eth1: no IPv6 routers present
[   55.361280] CE: hpet increasing min_delta_ns to 15000 nsec
[ 1428.778511] __ratelimit: 9 callbacks suppressed
[ 1428.778520] npviewer.bin[2843]: segfault at 3839392e ip 000000003839392e sp 00000000ff845f8c error 14
[ 1792.940580] CE: hpet increasing min_delta_ns to 22500 nsec

I wonder if that gives any concrete information? Flash seems to have crashed. Let me see what happens when I close that process... No change. Argh. This sucks. Sorry for whining. ^^;

---

### Post by murderslastcrow on 2010-05-01
Okay, this is weird. Pressing Ctrl+Alt+F1 to drop to console, then Ctrl+Alt+F7 to return to GUI immediately solves the problem.

And pkilling Xorg brings up the login screen and everything is fine, as well.

Does that just mean Xorg is suddenly caught in a loop somewhere? It's pretty weird, although I'm kinda' satisfied with this fix right now, it'd be nice not to have to do that every time. Really weird bug.

---

### Post by P4man on 2010-05-01
Try adding

hpet=disabled

to your kernel options in grub.

---

### Post by murderslastcrow on 2010-05-01
Hm. Don't see why I personally need HPET, either way. Let's see what happens. Do you know which file exactly I should edit to do this in the case of Grub2? Perhaps Startup Manager could handle it. Well, I'll go look for myself, but you can comment on it anyway.

Thank you so much for following me on this one, P4man. It's really done a lot of good so far.

---

### Post by P4man on 2010-05-01
dont use startup manager. It tends to break grub2. Or at least used to, and I still dont trust it.

edit /etc/default/grub

add it to GRUB_CMDLINE_LINUX_DEFAULT

then run update-grub.

---

### Post by murderslastcrow on 2010-05-01
I did that a few hours ago, and it hasn't happened yet. Also, another issue I had with Docky crashing at least once each boot up hasn't occurred again- no updates or anything. I wonder if they're somehow related. Why would this have fixed it? Perhaps I'm not too familiar with the descriptions of HPET I've been given.

Anyway, if this problem doesn't come back for another day or two, I'll mark this as solved.

---

### Post by RedNight on 2010-05-01
Did you also have your keyboard's freezing??

I am getting the same mouse issue as you. However, sometimes, I am  getting freezes on my keyboard too.

---

### Post by lunaparadox on 2010-05-02
my whole system keeps freezing up mouse won't move and keyboard won't work have to do hard reset about all i can run is terminal and firefox.

---

### Post by RedNight on 2010-05-02
> **lunaparadox said:**
> my whole system keeps freezing up mouse won't move and keyboard won't work have to do hard reset about all i can run is terminal and firefox.

Is your internet connection working??

---

### Post by lunaparadox on 2010-05-02
yes internet works but whole sytem crashes if I try to use synaptic to install anything. but can install through terminal no problem. the whole thing is pretty frustrating but I guess goes with installing on the day of the release.

---

### Post by RedNight on 2010-05-02
Did you try P4man's solution?

---

### Post by lunaparadox on 2010-05-02
not yet waiting until the morning to try that one. just watching the forums tonight to get some fresh ideas for later been trying diferent things since yesterday. and just need to let it go for the night I guess.

---

### Post by murderslastcrow on 2010-05-02
Ah, just a small update- no further issues with freezing or Docky so far.

I don't know what you mean by keyboard freezing, since if the programs and display freeze, you won't be able to see what you type- but whatever I typed during the freeze, I could see during the small points at which the display would refresh. So it still worked, but it was frozen with the rest of Gnome.

The only thing that would move according to realtime was audio and the mouse cursor.

Yeah, hopefully some updates somewhere along the next few weeks will clear this up for you guys. This is really odd, since I haven't had any issues I needed to do more than Google for in the past, and even then only very rarely, and nothing so serious as a 'freeze'. So I wouldn't expect a bug like this to come up again in the future.

---

### Post by P4man on 2010-05-02
I only roughly understand what hpet does, its pretty low level kernel/cpu stuff, I dont think trying to explain my understanding of it would be wise :) but may I suggest you file a bug report on launchpad, indicate exactly what type of hardware you have and say it requires disabling hpet to avoid freezing.


To the other posters having the same issue, id say try the same solution.


To mark this thread as solved, click mark solved in thread tools.

---

### Post by lunaparadox on 2010-05-02
got my problems fixed by installing RT kernel like this
sudo apt-get install linux-rt linux-headers-rt 
all problems are gone now. and all seems to run fine.

---

### Post by murderslastcrow on 2010-05-02
Huh, not to discourage you P4Man, since you've given a lot of superb assistance thus far, but the problem came back. But only AFTER a Docky crash, so I think it might be Docky freaking out on me or something and covering the composited layer with a frozen frame, perhaps. It would explain why the mouse still moves around just fine.

I'll try using the realtime kernel as suggested, see if that works, and take away the disabled hpet.

Thanks for everyone's help and suggestions. Hopefull this'll be solved soon.

---

### Post by murderslastcrow on 2010-05-02
So, simply by installing a realtime kernel, this was all fixed for you? I'm not really well versed in how the realtime kernel works, but I would guess it works with the most current kernel release you have installed, correct? Installing it anyway, since I can always just do a reinstallation, I'm not really that concerned with messing things up.

I'm keeping track of the changes I've made, of course. re-enabled hpet and installed realtime kernel as suggested, leaving Docky on to see if it's related. If it still crashes, I'll stop using Docky, and if that fixes it, I'll uninstall the realtime kernel and leave Docky off, since that should deduce where the problem is originating from and I can file the right bug report.

---

### Post by P4man on 2010-05-02
something else to help you troubleshoot. If you get that problem again press control+alt+f1

should give you a full screen terminal. You can kill docky from there.

```
sudo killall docky(something?)
```

not sure how the process is called but start typing docky and press tab to complete, in case it uses a different name. Or type docky*

To return to the gui, press control+alt+F7 or F8

---

### Post by murderslastcrow on 2010-05-02
Ah yes- that's what I've been doing. Ctrl+Alt+F1, wait a few seconds, then switch back to sessions 1 GUI with Ctrl+Alt+F7 seems to immediately refresh the display and bring it back to normal.

And yes, docky is named docky, thanks for reminding me of * meaning anything with the beginning phrase, very helpful for another project I'm doing in the terminal.

Just so everyone knows, this hasn't happened again since I started using the realtime kernel, and Docky hasn't crashed just yet. Still no further updates since the release, and I won't be updating for a few days just to make sure the fix is related to something in this post. If not, I'll update and see what happens.

So, we'll see what happens over the next 48 hours.

---

### Post by murderslastcrow on 2010-05-02
Well, happened about twice in the past ten minutes, and no flash, with realtime kernel, without hpet disabled (since that didn't seem to work anyway).

Good bye, Docky! You were nice while it lasted! XD Let's see if you're the cause of all my problems.

---

### Post by lunaparadox on 2010-05-03
I've had no more issues. that said I install the RT kernel because i use the ubuntu studio audio packages for producing music. at the moment I'm compiling a rt kernel with version 2.6.33 of the kernel. sorry it didn't correct your issue just throwing out whats working for me since we are having similar issues but not the same. don't know why the normal kernel is causing me headaches but wasn't what I run normally any way. best of luck to you and i will be checking to see if you find a fix as i install ubuntu on as many puters as my friends will allow:)

---

### Post by murderslastcrow on 2010-05-04
Been 24 hours without an issue. I think it may have been Docky, after all. I'm considering doing a fresh install, either way, since I never had any problems with the Betas, so I might have tweaked something when I installed Docky. :\ I'm still gonna' wait another day.

---

### Post by murderslastcrow on 2010-05-04
K, happened again, but that every 20 startups disk checker informed me that I may have some hard disk issues.

So I checked, and whatever partitioning I did before installing was getting all screwey, and there were some errors on the disk. SO, backed up my files, did a fresh install, installed all the same stuff I had, and not only is this problem not happening, but my performance is skyrocketing!

Soooo... yeah, looks like I just needed to do a fresh install of Lucid instead of updating from RC? Either way, things are much better now, the fan almost never comes on even with heavy programs.

Thanks for all your help guys, turns out my files were just skiwompus. Solved!

---

