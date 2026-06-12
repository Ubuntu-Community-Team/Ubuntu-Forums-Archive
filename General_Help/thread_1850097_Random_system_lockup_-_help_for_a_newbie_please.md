---
title: "Random system lockup - help for a newbie please"
date: 2011-09-25
forum: General Help
---

### Post by cmill126 on 2011-09-25
Hello everyone.

This is my first experience with Ubuntu, and it's great except for one problem: my computer will randomly lock up. I thought it might be the graphics card, and got some help on another thread, but I've determined it's something else.

Here's what happens: the display will freeze (but not black out; it shows whatever happens to be displayed at the time), sounds playing will either stop or repeat a short segment, neither the mouse nor the keyboard do anything, requiring a manual restart using the button on the tower. The freeze happens as early as the very beginning of Ubuntu's startup cycle. This, along with the fact that it has happened in a wide variety of situations (several, few, or no programs open, heavy load or light load), leads me to believe that it is not caused by any particular program.

Once in a while, when it restarts, the Unity launcher will revert to its default configuration, wiping out the programs I've removed from and added to it. Also, in the most recent freeze and restart, the weather indicator applet lost my settings and seems to not be picking them up even after reentering them. I reinstalled it, to no avail.

I'm sure there are log files that might be helpful, but I'm not sure where they are. Any help would be greatly appreciated. I'm hoping to learn more about Ubuntu and Linux, particularly the guts of the system, but I'll take getting this lock up problem to stop for now.

---

### Post by johnmay on 2011-09-25
I am having a similar problem. I am using 11.04 AMD 64. I have looked in the log files, System> Administration> log file viewer and in var/log/  but don't really know where to look in Ubuntu for the crash/error messages. Thanks!

---

### Post by cmill126 on 2011-09-25
> **johnmay said:**
> I am having a similar problem. I am using 11.04 AMD 64. I have looked in the log files, System> Administration> log file viewer and in var/log/  but don't really know where to look in Ubuntu for the crash/error messages. Thanks!

Same here: using 11.04 64-bit version.

---

### Post by Hylas de Niall on 2011-12-10
Yeah, ditto on my desktop install of 11.10 (though not on my netbook 11.10 install, which has been top-notch since the beta2).
It's been happening intermittently since install. Predominantly whilst using Firefox, but it's also started happening whilst running Sauerbraten as well.
No response from keyboard or mouse at all.

I'm not at all happy with having to cold-boot to get my system back - is there a solution?

---

### Post by Hylas de Niall on 2011-12-12
Aaaag!

Another one this morning! Using Chromium this time.

Does anyone know what could be causing this? I really don't understand it; 11.10 is running perfectly on my three year old netbook, but my desktop with 3gigs of ram keeps locking up on me.

Once more, just once more and i'll go back to 10.04. Or worse!
I need my system to be *reliable*!

:confused:

---

### Post by Hylas de Niall on 2011-12-13
....aaaaaand another. :(

I switched from using Gnome shell back to Unity to see if the issue was with Shell, but apparently not.

!LOCKOUT!

I'm posting this from my Win7 boot, because i want to be sure it won't lock up on me :(

I'm thinking maybe in terms of 10.04 and the hell with it.

---

### Post by zozie on 2011-12-13
It's too bad you're having this issue. I've never had a single freeze/lockup in Ubuntu. Typically you'll see freezes in Windows first if there is an underlying hardware issue. 

Can you post your hardware specs? The only time I had linux freezing on me was on my previous laptop due to something in the bios which went away after latest bios install...

---

### Post by Hylas de Niall on 2011-12-14
Mine's:

Acer Aspire AX3812 Dual Core Desktop PC
Intel Celeron E5400 Dual Core 2.70GHz
3GB RAM(Installed)
500GB Hard Drive
DVD+/-RW Supermulti Dual Layer
Graphics: INTEL GMA X4500
Audio Output: Realtek High Definition Audio
Networking: 10/100/1000 Gigabit

lspci return:

00:00.0 Host bridge: Intel Corporation 4 Series Chipset DRAM Controller (rev 03)
00:02.0 VGA compatible controller: Intel Corporation 4 Series Chipset Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation 4 Series Chipset Integrated Graphics Controller (rev 03)
00:19.0 Ethernet controller: Intel Corporation 82567V-2 Gigabit Network Connection
00:1a.0 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #4
00:1a.1 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #5
00:1a.2 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #6
00:1a.7 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB2 EHCI Controller #2
00:1b.0 Audio device: Intel Corporation 82801JI (ICH10 Family) HD Audio Controller
00:1c.0 PCI bridge: Intel Corporation 82801JI (ICH10 Family) PCI Express Root Port 1
00:1d.0 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #1
00:1d.1 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #2
00:1d.2 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #3
00:1d.7 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB2 EHCI Controller #1
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 90)
00:1f.0 ISA bridge: Intel Corporation 82801JIB (ICH10) LPC Interface Controller
00:1f.2 SATA controller: Intel Corporation 82801JI (ICH10 Family) SATA AHCI Controller
00:1f.3 SMBus: Intel Corporation 82801JI (ICH10 Family) SMBus Controller
01:00.0 FireWire (IEEE 1394): VIA Technologies, Inc. VT6315 Series Firewire Controller

HTH and thanks :)

---

### Post by Hylas de Niall on 2011-12-24
two more lockups since last post :(
I thiiiink it *may* be hardware related...though my Win7 boot on the same machine is having no issues at all.
The 11.10 install on my other machine has been worry free since beta 2 though.
I dunno?

---

### Post by bobsageek on 2011-12-24
Post the output of ```
dmesg
``` and ```
cat /var/log/syslog
``` please.

---

### Post by Hylas de Niall on 2011-12-25
> **bobsageek said:**
> Post the output of ```
dmesg
``` and ```
cat /var/log/syslog
``` please.

```
**dmesg:**

[    0.206904] pnp 00:00: [mem 0x000d0000-0x000dffff window]
[    0.206906] pnp 00:00: [mem 0xbde00000-0xdfffffff window]
[    0.206908] pnp 00:00: [mem 0xf0000000-0xfed8ffff window]
[    0.206985] pnp 00:00: Plug and Play ACPI device, IDs PNP0a08 PNP0a03 (active)
[    0.206994] pnp 00:01: [mem 0xfed14000-0xfed19fff]
[    0.206996] pnp 00:01: [mem 0xfed90000-0xfed93fff]
[    0.207051] system 00:01: [mem 0xfed14000-0xfed19fff] could not be reserved
[    0.207054] system 00:01: [mem 0xfed90000-0xfed93fff] has been reserved
[    0.207057] system 00:01: Plug and Play ACPI device, IDs PNP0c01 (active)
[    0.207087] pnp 00:02: [dma 4]
[    0.207089] pnp 00:02: [io  0x0000-0x000f]
[    0.207091] pnp 00:02: [io  0x0081-0x0083]
[    0.207093] pnp 00:02: [io  0x0087]
[    0.207094] pnp 00:02: [io  0x0089-0x008b]
[    0.207096] pnp 00:02: [io  0x008f]
[    0.207097] pnp 00:02: [io  0x00c0-0x00df]
[    0.207119] pnp 00:02: Plug and Play ACPI device, IDs PNP0200 (active)
[    0.207128] pnp 00:03: [io  0x0070-0x0071]
[    0.207139] pnp 00:03: [irq 8]
[    0.207161] pnp 00:03: Plug and Play ACPI device, IDs PNP0b00 (active)
[    0.207186] pnp 00:04: [io  0x0060]
[    0.207187] pnp 00:04: [io  0x0064]
[    0.207192] pnp 00:04: [irq 1]
[    0.207214] pnp 00:04: Plug and Play ACPI device, IDs PNP0303 PNP030b (active)
[    0.207255] pnp 00:05: [irq 12]
[    0.207279] pnp 00:05: Plug and Play ACPI device, IDs PNP0f03 PNP0f13 (active)
[    0.207286] pnp 00:06: [io  0x0061]
[    0.207308] pnp 00:06: Plug and Play ACPI device, IDs PNP0800 (active)
[    0.207316] pnp 00:07: [io  0x00f0-0x00ff]
[    0.207320] pnp 00:07: [irq 13]
[    0.207343] pnp 00:07: Plug and Play ACPI device, IDs PNP0c04 (active)
[    0.207691] pnp 00:08: [io  0x0000-0xffffffff disabled]
[    0.207693] pnp 00:08: [io  0x0a00-0x0a0f]
[    0.207695] pnp 00:08: [io  0x0a10-0x0a1f]
[    0.207696] pnp 00:08: [io  0x0a20-0x0a2f]
[    0.207698] pnp 00:08: [io  0x0a30-0x0a3f]
[    0.207737] system 00:08: [io  0x0a00-0x0a0f] has been reserved
[    0.207740] system 00:08: [io  0x0a10-0x0a1f] has been reserved
[    0.207742] system 00:08: [io  0x0a20-0x0a2f] has been reserved
[    0.207744] system 00:08: [io  0x0a30-0x0a3f] has been reserved
[    0.207747] system 00:08: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.207841] pnp 00:09: [io  0x0010-0x001f]
[    0.207843] pnp 00:09: [io  0x0022-0x003f]
[    0.207844] pnp 00:09: [io  0x0044-0x005f]
[    0.207846] pnp 00:09: [io  0x0062-0x0063]
[    0.207847] pnp 00:09: [io  0x0065-0x006f]
[    0.207849] pnp 00:09: [io  0x0072-0x007f]
[    0.207853] pnp 00:09: [io  0x0080]
[    0.207854] pnp 00:09: [io  0x0084-0x0086]
[    0.207856] pnp 00:09: [io  0x0088]
[    0.207857] pnp 00:09: [io  0x008c-0x008e]
[    0.207859] pnp 00:09: [io  0x0090-0x009f]
[    0.207861] pnp 00:09: [io  0x00a2-0x00bf]
[    0.207862] pnp 00:09: [io  0x00e0-0x00ef]
[    0.207864] pnp 00:09: [io  0x04d0-0x04d1]
[    0.207866] pnp 00:09: [io  0x0800-0x087f]
[    0.207868] pnp 00:09: [io  0x0000-0xffffffff disabled]
[    0.207870] pnp 00:09: [io  0x0500-0x057f]
[    0.207871] pnp 00:09: [mem 0xfed1c000-0xfed1ffff]
[    0.207873] pnp 00:09: [mem 0xfed20000-0xfed3ffff]
[    0.207875] pnp 00:09: [mem 0xfed40000-0xfed8ffff]
[    0.207923] system 00:09: [io  0x04d0-0x04d1] has been reserved
[    0.207925] system 00:09: [io  0x0800-0x087f] has been reserved
[    0.207928] system 00:09: [io  0x0500-0x057f] has been reserved
[    0.207930] system 00:09: [mem 0xfed1c000-0xfed1ffff] has been reserved
[    0.207933] system 00:09: [mem 0xfed20000-0xfed3ffff] has been reserved
[    0.207935] system 00:09: [mem 0xfed40000-0xfed8ffff] has been reserved
[    0.207938] system 00:09: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.207985] pnp 00:0a: [mem 0xfed00000-0xfed003ff]
[    0.208041] pnp 00:0a: Plug and Play ACPI device, IDs PNP0103 (active)
[    0.208084] pnp 00:0b: [mem 0xffb00000-0xffbfffff]
[    0.208086] pnp 00:0b: [mem 0xfff00000-0xffffffff]
[    0.208111] pnp 00:0b: Plug and Play ACPI device, IDs INT0800 (active)
[    0.208149] pnp 00:0c: [mem 0xffc00000-0xffefffff]
[    0.208187] system 00:0c: [mem 0xffc00000-0xffefffff] has been reserved
[    0.208190] system 00:0c: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.208261] pnp 00:0d: [mem 0xfec00000-0xfec00fff]
[    0.208263] pnp 00:0d: [mem 0xfee00000-0xfee00fff]
[    0.208301] system 00:0d: [mem 0xfec00000-0xfec00fff] could not be reserved
[    0.208303] system 00:0d: [mem 0xfee00000-0xfee00fff] has been reserved
[    0.208306] system 00:0d: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.208344] pnp 00:0e: [mem 0xe0000000-0xefffffff]
[    0.208382] system 00:0e: [mem 0xe0000000-0xefffffff] has been reserved
[    0.208384] system 00:0e: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.208584] pnp 00:0f: [mem 0x00000000-0x0009ffff]
[    0.208586] pnp 00:0f: [mem 0x000c0000-0x000cffff]
[    0.208587] pnp 00:0f: [mem 0x000e0000-0x000fffff]
[    0.208589] pnp 00:0f: [mem 0x00100000-0xbddfffff]
[    0.208591] pnp 00:0f: [mem 0xfed90000-0xffffffff]
[    0.208649] system 00:0f: [mem 0x00000000-0x0009ffff] could not be reserved
[    0.208651] system 00:0f: [mem 0x000c0000-0x000cffff] could not be reserved
[    0.208654] system 00:0f: [mem 0x000e0000-0x000fffff] could not be reserved
[    0.208656] system 00:0f: [mem 0x00100000-0xbddfffff] could not be reserved
[    0.208658] system 00:0f: [mem 0xfed90000-0xffffffff] could not be reserved
[    0.208661] system 00:0f: Plug and Play ACPI device, IDs PNP0c01 (active)
[    0.208776] pnp: PnP ACPI: found 16 devices
[    0.208778] ACPI: ACPI bus type pnp unregistered
[    0.208781] PnPBIOS: Disabled by ACPI PNP
[    0.244665] PCI: max bus depth: 1 pci_try_num: 2
[    0.244695] pci 0000:00:1c.0: BAR 15: assigned [mem 0xc0000000-0xc01fffff 64bit pref]
[    0.244698] pci 0000:00:1c.0: PCI bridge to [bus 01-01]
[    0.244701] pci 0000:00:1c.0:   bridge window [io  0xe000-0xefff]
[    0.244705] pci 0000:00:1c.0:   bridge window [mem 0xfeb00000-0xfebfffff]
[    0.244709] pci 0000:00:1c.0:   bridge window [mem 0xc0000000-0xc01fffff 64bit pref]
[    0.244714] pci 0000:00:1e.0: PCI bridge to [bus 02-02]
[    0.244716] pci 0000:00:1e.0:   bridge window [io  disabled]
[    0.244720] pci 0000:00:1e.0:   bridge window [mem disabled]
[    0.244723] pci 0000:00:1e.0:   bridge window [mem pref disabled]
[    0.244749] pci 0000:00:1c.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    0.244754] pci 0000:00:1c.0: setting latency timer to 64
[    0.244760] pci 0000:00:1e.0: setting latency timer to 64
[    0.244763] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
[    0.244766] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff]
[    0.244767] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
[    0.244769] pci_bus 0000:00: resource 7 [mem 0x000d0000-0x000dffff]
[    0.244771] pci_bus 0000:00: resource 8 [mem 0xbde00000-0xdfffffff]
[    0.244773] pci_bus 0000:00: resource 9 [mem 0xf0000000-0xfed8ffff]
[    0.244776] pci_bus 0000:01: resource 0 [io  0xe000-0xefff]
[    0.244778] pci_bus 0000:01: resource 1 [mem 0xfeb00000-0xfebfffff]
[    0.244780] pci_bus 0000:01: resource 2 [mem 0xc0000000-0xc01fffff 64bit pref]
[    0.244782] pci_bus 0000:02: resource 4 [io  0x0000-0x0cf7]
[    0.244784] pci_bus 0000:02: resource 5 [io  0x0d00-0xffff]
[    0.244786] pci_bus 0000:02: resource 6 [mem 0x000a0000-0x000bffff]
[    0.244788] pci_bus 0000:02: resource 7 [mem 0x000d0000-0x000dffff]
[    0.244790] pci_bus 0000:02: resource 8 [mem 0xbde00000-0xdfffffff]
[    0.244792] pci_bus 0000:02: resource 9 [mem 0xf0000000-0xfed8ffff]
[    0.244841] NET: Registered protocol family 2
[    0.244907] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.245120] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.245552] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.245777] TCP: Hash tables configured (established 131072 bind 65536)
[    0.245779] TCP reno registered
[    0.245781] UDP hash table entries: 512 (order: 2, 16384 bytes)
[    0.245793] UDP-Lite hash table entries: 512 (order: 2, 16384 bytes)
[    0.245893] NET: Registered protocol family 1
[    0.245910] pci 0000:00:02.0: Boot video device
[    0.246061] PCI: CLS 32 bytes, default 64
[    0.246361] audit: initializing netlink socket (disabled)
[    0.246371] type=2000 audit(1324799590.240:1): initialized
[    0.268858] highmem bounce pool size: 64 pages
[    0.268863] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    0.280807] VFS: Disk quotas dquot_6.5.2
[    0.280870] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.281462] fuse init (API version 7.16)
[    0.281547] msgmni has been set to 1657
[    0.281833] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.281856] io scheduler noop registered
[    0.281857] io scheduler deadline registered
[    0.281869] io scheduler cfq registered (default)
[    0.281967] pcieport 0000:00:1c.0: setting latency timer to 64
[    0.282008] pcieport 0000:00:1c.0: irq 40 for MSI/MSI-X
[    0.282080] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.282099] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.282140] intel_idle: MWAIT substates: 0x22220
[    0.282141] intel_idle: does not run on family 6 model 23
[    0.282220] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0
[    0.282225] ACPI: Power Button [PWRB]
[    0.282266] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
[    0.282268] ACPI: Power Button [PWRF]
[    0.282296] ACPI: acpi_idle registered with cpuidle
[    0.284444] ERST: Table is not found!
[    0.284505] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    0.284612] isapnp: Scanning for PnP cards...
[    0.401426] Freeing initrd memory: 13324k freed
[    0.637551] isapnp: No Plug & Play device found
[    0.672535] Linux agpgart interface v0.103
[    0.672636] agpgart-intel 0000:00:00.0: Intel G45/G43 Chipset
[    0.672693] agpgart-intel 0000:00:00.0: detected gtt size: 2097152K total, 262144K mappable
[    0.673401] agpgart-intel 0000:00:00.0: detected 32768K stolen memory
[    0.673511] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0xd0000000
[    0.674576] brd: module loaded
[    0.675077] loop: module loaded
[    0.675487] Fixed MDIO Bus: probed
[    0.675508] PPP generic driver version 2.4.2
[    0.675537] tun: Universal TUN/TAP device driver, 1.6
[    0.675538] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.675603] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.675631] ehci_hcd 0000:00:1a.7: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.675644] ehci_hcd 0000:00:1a.7: setting latency timer to 64
[    0.675647] ehci_hcd 0000:00:1a.7: EHCI Host Controller
[    0.675677] ehci_hcd 0000:00:1a.7: new USB bus registered, assigned bus number 1
[    0.675701] ehci_hcd 0000:00:1a.7: debug port 1
[    0.679599] ehci_hcd 0000:00:1a.7: cache line size of 32 is not supported
[    0.679614] ehci_hcd 0000:00:1a.7: irq 18, io mem 0xfeaf8000
[    0.692018] ehci_hcd 0000:00:1a.7: USB 2.0 started, EHCI 1.00
[    0.692217] hub 1-0:1.0: USB hub found
[    0.692220] hub 1-0:1.0: 6 ports detected
[    0.692286] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    0.692294] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    0.692297] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    0.692326] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 2
[    0.692346] ehci_hcd 0000:00:1d.7: debug port 1
[    0.696235] ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported
[    0.696246] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xfeaf2000
[    0.712019] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    0.712213] hub 2-0:1.0: USB hub found
[    0.712216] hub 2-0:1.0: 6 ports detected
[    0.712275] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.712286] uhci_hcd: USB Universal Host Controller Interface driver
[    0.712308] uhci_hcd 0000:00:1a.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.712314] uhci_hcd 0000:00:1a.0: setting latency timer to 64
[    0.712317] uhci_hcd 0000:00:1a.0: UHCI Host Controller
[    0.712348] uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 3
[    0.712378] uhci_hcd 0000:00:1a.0: irq 16, io base 0x0000d800
[    0.712477] hub 3-0:1.0: USB hub found
[    0.712480] hub 3-0:1.0: 2 ports detected
[    0.712537] uhci_hcd 0000:00:1a.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[    0.712542] uhci_hcd 0000:00:1a.1: setting latency timer to 64
[    0.712545] uhci_hcd 0000:00:1a.1: UHCI Host Controller
[    0.712573] uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus number 4
[    0.712601] uhci_hcd 0000:00:1a.1: irq 21, io base 0x0000d480
[    0.712698] hub 4-0:1.0: USB hub found
[    0.712701] hub 4-0:1.0: 2 ports detected
[    0.712760] uhci_hcd 0000:00:1a.2: PCI INT D -> GSI 19 (level, low) -> IRQ 19
[    0.712764] uhci_hcd 0000:00:1a.2: setting latency timer to 64
[    0.712767] uhci_hcd 0000:00:1a.2: UHCI Host Controller
[    0.712797] uhci_hcd 0000:00:1a.2: new USB bus registered, assigned bus number 5
[    0.712825] uhci_hcd 0000:00:1a.2: irq 19, io base 0x0000d400
[    0.712919] hub 5-0:1.0: USB hub found
[    0.712922] hub 5-0:1.0: 2 ports detected
[    0.712972] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    0.712977] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    0.712980] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    0.713008] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 6
[    0.713028] uhci_hcd 0000:00:1d.0: irq 23, io base 0x0000d080
[    0.713121] hub 6-0:1.0: USB hub found
[    0.713124] hub 6-0:1.0: 2 ports detected
[    0.713173] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    0.713178] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    0.713181] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    0.713209] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 7
[    0.713231] uhci_hcd 0000:00:1d.1: irq 19, io base 0x0000d000
[    0.713328] hub 7-0:1.0: USB hub found
[    0.713331] hub 7-0:1.0: 2 ports detected
[    0.713383] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.713388] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    0.713390] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    0.713417] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 8
[    0.713437] uhci_hcd 0000:00:1d.2: irq 18, io base 0x0000cc00
[    0.713533] hub 8-0:1.0: USB hub found
[    0.713536] hub 8-0:1.0: 2 ports detected
[    0.713645] i8042: PNP: PS/2 Controller [PNP0303:PS2K,PNP0f03:PS2M] at 0x60,0x64 irq 1,12
[    0.714016] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.714027] serio: i8042 AUX port at 0x60,0x64 irq 12
[    0.714229] mousedev: PS/2 mouse device common for all mice
[    0.714385] rtc_cmos 00:03: RTC can wake from S4
[    0.714467] rtc_cmos 00:03: rtc core: registered rtc_cmos as rtc0
[    0.714489] rtc0: alarms up to one month, y3k, 114 bytes nvram, hpet irqs
[    0.714566] device-mapper: uevent: version 1.0.3
[    0.714630] device-mapper: ioctl: 4.20.0-ioctl (2011-02-02) initialised: [email]dm-devel@redhat.com[/email]
[    0.714656] EISA: Probing bus 0 at eisa.0
[    0.714658] EISA: Cannot allocate resource for mainboard
[    0.714659] Cannot allocate resource for EISA slot 1
[    0.714661] Cannot allocate resource for EISA slot 2
[    0.714662] Cannot allocate resource for EISA slot 3
[    0.714664] Cannot allocate resource for EISA slot 4
[    0.714665] Cannot allocate resource for EISA slot 5
[    0.714667] Cannot allocate resource for EISA slot 6
[    0.714668] Cannot allocate resource for EISA slot 7
[    0.714670] Cannot allocate resource for EISA slot 8
[    0.714671] EISA: Detected 0 cards.
[    0.714679] cpufreq-nforce2: No nForce2 chipset.
[    0.714681] cpuidle: using governor ladder
[    0.714683] cpuidle: using governor menu
[    0.714684] EFI Variables Facility v0.08 2004-May-17
[    0.714937] TCP cubic registered
[    0.715059] NET: Registered protocol family 10
[    0.715560] NET: Registered protocol family 17
[    0.715573] Registering the dns_resolver key type
[    0.715596] Using IPI No-Shortcut mode
[    0.715659] PM: Hibernation image not present or could not be loaded.
[    0.715669] registered taskstats version 1
[    0.726030]   Magic number: 7:994:875
[    0.726122] rtc_cmos 00:03: setting system clock to 2011-12-25 07:53:11 UTC (1324799591)
[    0.726773] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.726774] EDD information not available.
[    0.726866] Freeing unused kernel memory: 696k freed
[    0.727073] Write protecting the kernel text: 5336k
[    0.727111] Write protecting the kernel read-only data: 2192k
[    0.735998] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input2
[    0.740316] udevd[80]: starting version 173
[    0.784045] e1000e: Intel(R) PRO/1000 Network Driver - 1.3.10-k2
[    0.784048] e1000e: Copyright(c) 1999 - 2011 Intel Corporation.
[    0.784095] e1000e 0000:00:19.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    0.784105] e1000e 0000:00:19.0: setting latency timer to 64
[    0.800082] e1000e 0000:00:19.0: irq 41 for MSI/MSI-X
[    0.803822] firewire_ohci 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.803830] firewire_ohci 0000:01:00.0: setting latency timer to 64
[    0.864090] firewire_ohci: Added fw-ohci device 0000:01:00.0, OHCI v1.10, 4 IR + 8 IT contexts, quirks 0x11
[    0.992259] e1000e 0000:00:19.0: eth0: (PCI Express:2.5GT/s:Width x1) 00:26:2d:18:62:83
[    0.992262] e1000e 0000:00:19.0: eth0: Intel(R) PRO/1000 Network Connection
[    0.992284] e1000e 0000:00:19.0: eth0: MAC: 7, PHY: 8, PBA No: FFFFFF-0FF
[    0.992302] ahci 0000:00:1f.2: version 3.0
[    0.992319] ahci 0000:00:1f.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    0.992366] ahci 0000:00:1f.2: irq 42 for MSI/MSI-X
[    0.992416] ahci: SSS flag set, parallel bus scan disabled
[    0.992453] ahci 0000:00:1f.2: AHCI 0001.0200 32 slots 6 ports 3 Gbps 0x3f impl SATA mode
[    0.992456] ahci 0000:00:1f.2: flags: 64bit ncq sntf stag pm led clo pio slum part ccc ems sxs 
[    0.992460] ahci 0000:00:1f.2: setting latency timer to 64
[    1.032601] scsi0 : ahci
[    1.032708] scsi1 : ahci
[    1.032767] scsi2 : ahci
[    1.032827] scsi3 : ahci
[    1.032888] scsi4 : ahci
[    1.032946] scsi5 : ahci
[    1.033094] ata1: SATA max UDMA/133 abar m2048@0xfeaf0000 port 0xfeaf0100 irq 42
[    1.033097] ata2: SATA max UDMA/133 abar m2048@0xfeaf0000 port 0xfeaf0180 irq 42
[    1.033099] ata3: SATA max UDMA/133 abar m2048@0xfeaf0000 port 0xfeaf0200 irq 42
[    1.033102] ata4: SATA max UDMA/133 abar m2048@0xfeaf0000 port 0xfeaf0280 irq 42
[    1.033104] ata5: SATA max UDMA/133 abar m2048@0xfeaf0000 port 0xfeaf0300 irq 42
[    1.033107] ata6: SATA max UDMA/133 abar m2048@0xfeaf0000 port 0xfeaf0380 irq 42
[    1.064027] usb 2-6: new high speed USB device number 2 using ehci_hcd
[    1.201327] usbcore: registered new interface driver uas
[    1.244022] Refined TSC clocksource calibration: 2693.553 MHz.
[    1.244031] Switching to clocksource tsc
[    1.352022] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    1.353670] ata1.00: ATAPI: ATAPI   DVD A  DH16AASH, SA15, max UDMA/100
[    1.354413] ata1.00: configured for UDMA/100
[    1.357222] scsi 0:0:0:0: CD-ROM            ATAPI    DVD A  DH16AASH  SA15 PQ: 0 ANSI: 5
[    1.360403] sr0: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
[    1.360408] cdrom: Uniform CD-ROM driver Revision: 3.20
[    1.360627] sr 0:0:0:0: Attached scsi CD-ROM sr0
[    1.360691] sr 0:0:0:0: Attached scsi generic sg0 type 5
[    1.364119] firewire_core: created device fw0: GUID 001d72ffb6c14bff, S400
[    1.436019] usb 5-1: new low speed USB device number 2 using uhci_hcd
[    1.619767] generic-usb: probe of 0003:058F:6363.0001 failed with error -22
[    1.634381] input: Microsoft Comfort Optical Mouse 1000 as /devices/pci0000:00/0000:00:1a.2/usb5/5-1/5-1:1.0/input/input3
[    1.634480] generic-usb 0003:045E:00F6.0002: input,hidraw0: USB HID v1.11 Mouse [Microsoft Comfort Optical Mouse 1000] on usb-0000:00:1a.2-1/input0
[    1.634491] usbcore: registered new interface driver usbhid
[    1.634493] usbhid: USB HID core driver
[    1.680022] ata2: SATA link down (SStatus 0 SControl 300)
[    2.000018] ata3: SATA link down (SStatus 0 SControl 300)
[    2.320019] ata4: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    2.336432] ata4.00: ATA-8: WDC WD5000AAKS-00V1A0, 05.01D05, max UDMA/133
[    2.336438] ata4.00: 976773168 sectors, multi 0: LBA48 NCQ (depth 31/32), AA
[    2.337534] ata4.00: configured for UDMA/133
[    2.337622] scsi 3:0:0:0: Direct-Access     ATA      WDC WD5000AAKS-0 05.0 PQ: 0 ANSI: 5
[    2.337719] sd 3:0:0:0: [sda] 976773168 512-byte logical blocks: (500 GB/465 GiB)
[    2.337738] sd 3:0:0:0: Attached scsi generic sg1 type 0
[    2.337761] sd 3:0:0:0: [sda] Write Protect is off
[    2.337764] sd 3:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    2.337787] sd 3:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.368212]  sda: sda1 sda2 sda3 sda4 < sda5 sda6 >
[    2.368613] sd 3:0:0:0: [sda] Attached SCSI disk
[    2.656019] ata5: SATA link down (SStatus 0 SControl 300)
[    2.976018] ata6: SATA link down (SStatus 0 SControl 300)
[    2.976795] Initializing USB Mass Storage driver...
[    2.977097] scsi6 : usb-storage 2-6:1.0
[    2.977445] usbcore: registered new interface driver usb-storage
[    2.977447] USB Mass Storage support registered.
[    3.888906] EXT4-fs (sda5): INFO: recovery required on readonly filesystem
[    3.888909] EXT4-fs (sda5): write access will be enabled during recovery
[    3.976961] scsi 6:0:0:0: Direct-Access     Generic- Compact Flash    1.01 PQ: 0 ANSI: 0
[    3.977580] scsi 6:0:0:1: Direct-Access     Multiple Flash Reader     1.05 PQ: 0 ANSI: 0
[    3.977634] scsi: killing requests for dead queue
[    3.988058] scsi: killing requests for dead queue
[    4.004091] scsi: killing requests for dead queue
[    4.004204] scsi: killing requests for dead queue
[    4.004298] scsi: killing requests for dead queue
[    4.004389] scsi: killing requests for dead queue
[    4.004440] scsi: killing requests for dead queue
[    4.004485] scsi: killing requests for dead queue
[    4.004828] sd 6:0:0:0: Attached scsi generic sg2 type 0
[    4.004964] sd 6:0:0:1: Attached scsi generic sg3 type 0
[    4.010107] sd 6:0:0:0: [sdb] Attached SCSI removable disk
[    4.011306] sd 6:0:0:1: [sdc] Attached SCSI removable disk
[    4.343686] EXT4-fs (sda5): orphan cleanup on readonly fs
[    4.343693] EXT4-fs (sda5): ext4_orphan_cleanup: deleting unreferenced inode 10224710
[    4.343743] EXT4-fs (sda5): ext4_orphan_cleanup: deleting unreferenced inode 10224157
[    4.343757] EXT4-fs (sda5): ext4_orphan_cleanup: deleting unreferenced inode 6166109
[    4.343770] EXT4-fs (sda5): ext4_orphan_cleanup: deleting unreferenced inode 6029321
[    4.343783] EXT4-fs (sda5): ext4_orphan_cleanup: deleting unreferenced inode 6161633
[    4.343795] EXT4-fs (sda5): ext4_orphan_cleanup: deleting unreferenced inode 6029345
[    4.343825] EXT4-fs (sda5): 6 orphan inodes deleted
[    4.343827] EXT4-fs (sda5): recovery complete
[    5.250685] EXT4-fs (sda5): mounted filesystem with ordered data mode. Opts: (null)
[   14.219431] udevd[348]: starting version 173
[   14.265339] lp: driver loaded but no devices found
[   14.293627] [drm] Initialized drm 1.1.0 20060810
[   14.301940] Adding 33554428k swap on /dev/sda6.  Priority:-1 extents:1 across:33554428k 
[   14.314441] wmi: Mapper loaded
[   14.330684] i915 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   14.330690] i915 0000:00:02.0: setting latency timer to 64
[   14.396553] type=1400 audit(1324799605.167:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=488 comm="apparmor_parser"
[   14.396905] type=1400 audit(1324799605.167:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=488 comm="apparmor_parser"
[   14.397127] type=1400 audit(1324799605.167:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=488 comm="apparmor_parser"
[   14.425307] i915 0000:00:02.0: irq 43 for MSI/MSI-X
[   14.425313] [drm] Supports vblank timestamp caching Rev 1 (10.10.2010).
[   14.425315] [drm] Driver supports precise vblank timestamp query.
[   14.425347] vgaarb: device changed decodes: PCI:0000:00:02.0,olddecodes=io+mem,decodes=io+mem:owns=io+mem
[   14.600644] EXT4-fs (sda5): re-mounted. Opts: errors=remount-ro
[   14.655162] fbcon: inteldrmfb (fb0) is primary device
[   14.655258] Console: switching to colour frame buffer device 180x56
[   14.655287] fb0: inteldrmfb frame buffer device
[   14.655289] drm: registered panic notifier
[   14.655300] No ACPI video bus found
[   14.655366] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
[   14.655430] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[   14.655475] HDA Intel 0000:00:1b.0: irq 44 for MSI/MSI-X
[   14.655500] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   14.696298] hda_codec: ALC888: BIOS auto-probing.
[   14.712171] HDMI status: Pin=3 Presence_Detect=0 ELD_Valid=0
[   14.712494] input: HDA Intel HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:1b.0/sound/card0/input4
[   14.713038] input: HDA Intel Headphone as /devices/pci0000:00/0000:00:1b.0/sound/card0/input5
[   15.057675] type=1400 audit(1324799605.827:5): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=863 comm="apparmor_parser"
[   15.058769] type=1400 audit(1324799605.827:6): apparmor="STATUS" operation="profile_load" name="/usr/lib/lightdm/lightdm-guest-session-wrapper" pid=862 comm="apparmor_parser"
[   15.059630] type=1400 audit(1324799605.827:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=863 comm="apparmor_parser"
[   15.059881] type=1400 audit(1324799605.827:8): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=863 comm="apparmor_parser"
[   15.064754] type=1400 audit(1324799605.835:9): apparmor="STATUS" operation="profile_load" name="/usr/lib/telepathy/mission-control-5" pid=867 comm="apparmor_parser"
[   15.065119] type=1400 audit(1324799605.835:10): apparmor="STATUS" operation="profile_load" name="/usr/lib/telepathy/telepathy-*" pid=867 comm="apparmor_parser"
[   15.068119] type=1400 audit(1324799605.839:11): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince" pid=865 comm="apparmor_parser"
[   15.092186] e1000e 0000:00:19.0: irq 41 for MSI/MSI-X
[   15.148088] e1000e 0000:00:19.0: irq 41 for MSI/MSI-X
[   15.148326] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   15.187669] init: failsafe main process (748) killed by TERM signal
[   15.189957] init: apport pre-start process (904) terminated with status 1
[   15.211202] init: apport post-stop process (945) terminated with status 1
[   15.465682] Bluetooth: Core ver 2.16
[   15.465725] NET: Registered protocol family 31
[   15.465727] Bluetooth: HCI device and connection manager initialized
[   15.465729] Bluetooth: HCI socket layer initialized
[   15.465731] Bluetooth: L2CAP socket layer initialized
[   15.466168] Bluetooth: SCO socket layer initialized
[   15.468630] Bluetooth: RFCOMM TTY layer initialized
[   15.468636] Bluetooth: RFCOMM socket layer initialized
[   15.468638] Bluetooth: RFCOMM ver 1.11
[   15.499172] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   15.499175] Bluetooth: BNEP filters: protocol multicast
[   15.601102] ppdev: user-space parallel port driver
[   15.660557] init: plymouth-upstart-bridge main process (774) killed by TERM signal
[   16.708917] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: Rx/Tx
[   16.708922] e1000e 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[   16.709093] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   17.402544] EXT4-fs (sda5): re-mounted. Opts: errors=remount-ro,commit=0
[   17.805885] init: plymouth-stop pre-start process (1351) terminated with status 1
[   27.648012] eth0: no IPv6 routers present
hylas@hylas-Aspire-X3812:~$ 
```


===========================================================================

```
**cat /var/log/syslog:**

Dec 25 07:53:25 hylas-Aspire-X3812 kernel: [    1.064027] usb 2-6: new high speed USB device number 2 using ehci_hcd
Dec 25 07:53:25 hylas-Aspire-X3812 kernel: [    1.201327] usbcore: registered new interface driver uas
Dec 25 07:53:25 hylas-Aspire-X3812 kernel: [    1.244022] Refined TSC clocksource calibration: 2693.553 MHz.
Dec 25 07:53:25 hylas-Aspire-X3812 kernel: [    1.244031] Switching to clocksource tsc
Dec 25 07:53:25 hylas-Aspire-X3812 kernel: [    1.352022] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
Dec 25 07:53:25 hylas-Aspire-X3812 kernel: [    1.353670] ata1.00: ATAPI: ATAPI   DVD A  DH16AASH, SA15, max UDMA/100
Dec 25 07:53:25 hylas-Aspire-X3812 kernel: [    1.354413] ata1.00: configured for UDMA/100
Dec 25 07:53:25 hylas-Aspire-X3812 kernel: [    1.357222] scsi 0:0:0:0: CD-ROM            ATAPI    DVD A  DH16AASH  SA15 PQ: 0 ANSI: 5
Dec 25 07:53:25 hylas-Aspire-X3812 kernel: [    1.360403] sr0: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
Dec 25 07:53:25 hylas-Aspire-X3812 kernel: [    1.360408] cdrom: Uniform CD-ROM driver Revision: 3.20
Dec 25 07:53:25 hylas-Aspire-X3812 kernel: [    1.360627] sr 0:0:0:0: Attached scsi CD-ROM sr0
Dec 25 07:53:25 hylas-Aspire-X3812 kernel: [    1.360691] sr 0:0:0:0: Attached scsi generic sg0 type 5
Dec 25 07:53:25 hylas-Aspire-X3812 kernel: [    1.364119] firewire_core: created device fw0: GUID 001d72ffb6c14bff, S400
Dec 25 07:53:25 hylas-Aspire-X3812 kernel: [    1.436019] usb 5-1: new low speed USB device number 2 using uhci_hcd
Dec 25 07:53:25 hylas-Aspire-X3812 kernel: [    1.619767] generic-usb: probe of 0003:058F:6363.0001 failed with error -22
Dec 25 07:53:25 hylas-Aspire-X3812 kernel: [    1.634381] input: Microsoft Comfort Optical Mouse 1000 as /devices/pci0000:00/0000:00:1a.2/usb5/5-1/5-1:1.0/input/input3
Dec 25 07:53:25 hylas-Aspire-X3812 kernel: [    1.634480] generic-usb 0003:045E:00F6.0002: input,hidraw0: USB HID v1.11 Mouse [Microsoft Comfort Optical Mouse 1000] on usb-0000:00:1a.2-1/input0
Dec 25 07:53:25 hylas-Aspire-X3812 kernel: [    1.634491] usbcore: registered new interface driver usbhid
Dec 25 07:53:25 hylas-Aspire-X3812 kernel: [    1.634493] usbhid: USB HID core driver
Dec 25 07:53:25 hylas-Aspire-X3812 kernel: [    1.680022] ata2: SATA link down (SStatus 0 SControl 300)
Dec 25 07:53:25 hylas-Aspire-X3812 kernel: [    2.000018] ata3: SATA link down (SStatus 0 SControl 300)
Dec 25 07:53:25 hylas-Aspire-X3812 kernel: [    2.320019] ata4: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
Dec 25 07:53:25 hylas-Aspire-X3812 kernel: [    2.336432] ata4.00: ATA-8: WDC WD5000AAKS-00V1A0, 05.01D05, max UDMA/133
Dec 25 07:53:25 hylas-Aspire-X3812 kernel: [    2.336438] ata4.00: 976773168 sectors, multi 0: LBA48 NCQ (depth 31/32), AA
Dec 25 07:53:25 hylas-Aspire-X3812 kernel: [    2.337534] ata4.00: configured for UDMA/133
Dec 25 07:53:25 hylas-Aspire-X3812 kernel: [    2.337622] scsi 3:0:0:0: Direct-Access     ATA      WDC WD5000AAKS-0 05.0 PQ: 0 ANSI: 5
Dec 25 07:53:25 hylas-Aspire-X3812 kernel: [    2.337719] sd 3:0:0:0: [sda] 976773168 512-byte logical blocks: (500 GB/465 GiB)
Dec 25 07:53:25 hylas-Aspire-X3812 kernel: [    2.337738] sd 3:0:0:0: Attached scsi generic sg1 type 0
Dec 25 07:53:25 hylas-Aspire-X3812 kernel: [    2.337761] sd 3:0:0:0: [sda] Write Protect is off
Dec 25 07:53:25 hylas-Aspire-X3812 kernel: [    2.337764] sd 3:0:0:0: [sda] Mode Sense: 00 3a 00 00
Dec 25 07:53:25 hylas-Aspire-X3812 kernel: [    2.337787] sd 3:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Dec 25 07:53:25 hylas-Aspire-X3812 kernel: [    2.368212]  sda: sda1 sda2 sda3 sda4 < sda5 sda6 >
Dec 25 07:53:25 hylas-Aspire-X3812 kernel: [    2.368613] sd 3:0:0:0: [sda] Attached SCSI disk
Dec 25 07:53:25 hylas-Aspire-X3812 kernel: [    2.656019] ata5: SATA link down (SStatus 0 SControl 300)
Dec 25 07:53:25 hylas-Aspire-X3812 kernel: [    2.976018] ata6: SATA link down (SStatus 0 SControl 300)
Dec 25 07:53:25 hylas-Aspire-X3812 kernel: [    2.976795] Initializing USB Mass Storage driver...
Dec 25 07:53:25 hylas-Aspire-X3812 kernel: [    2.977097] scsi6 : usb-storage 2-6:1.0
Dec 25 07:53:25 hylas-Aspire-X3812 kernel: [    2.977445] usbcore: registered new interface driver usb-storage
Dec 25 07:53:25 hylas-Aspire-X3812 kernel: [    2.977447] USB Mass Storage support registered.
Dec 25 07:53:25 hylas-Aspire-X3812 kernel: [    3.888906] EXT4-fs (sda5): INFO: recovery required on readonly filesystem
Dec 25 07:53:25 hylas-Aspire-X3812 kernel: [    3.888909] EXT4-fs (sda5): write access will be enabled during recovery
Dec 25 07:53:25 hylas-Aspire-X3812 kernel: [    3.976961] scsi 6:0:0:0: Direct-Access     Generic- Compact Flash    1.01 PQ: 0 ANSI: 0
Dec 25 07:53:25 hylas-Aspire-X3812 kernel: [    3.977580] scsi 6:0:0:1: Direct-Access     Multiple Flash Reader     1.05 PQ: 0 ANSI: 0
Dec 25 07:53:25 hylas-Aspire-X3812 kernel: [    3.977634] scsi: killing requests for dead queue
Dec 25 07:53:25 hylas-Aspire-X3812 kernel: [    3.988058] scsi: killing requests for dead queue
Dec 25 07:53:25 hylas-Aspire-X3812 kernel: [    4.004091] scsi: killing requests for dead queue
Dec 25 07:53:25 hylas-Aspire-X3812 kernel: [    4.004204] scsi: killing requests for dead queue
Dec 25 07:53:25 hylas-Aspire-X3812 kernel: [    4.004298] scsi: killing requests for dead queue
Dec 25 07:53:25 hylas-Aspire-X3812 kernel: [    4.004389] scsi: killing requests for dead queue
Dec 25 07:53:25 hylas-Aspire-X3812 kernel: [    4.004440] scsi: killing requests for dead queue
Dec 25 07:53:25 hylas-Aspire-X3812 kernel: [    4.004485] scsi: killing requests for dead queue
Dec 25 07:53:25 hylas-Aspire-X3812 kernel: [    4.004828] sd 6:0:0:0: Attached scsi generic sg2 type 0
Dec 25 07:53:25 hylas-Aspire-X3812 kernel: [    4.004964] sd 6:0:0:1: Attached scsi generic sg3 type 0
Dec 25 07:53:25 hylas-Aspire-X3812 kernel: [    4.010107] sd 6:0:0:0: [sdb] Attached SCSI removable disk
Dec 25 07:53:25 hylas-Aspire-X3812 kernel: [    4.011306] sd 6:0:0:1: [sdc] Attached SCSI removable disk
Dec 25 07:53:25 hylas-Aspire-X3812 kernel: [    4.343686] EXT4-fs (sda5): orphan cleanup on readonly fs
Dec 25 07:53:25 hylas-Aspire-X3812 kernel: [    4.343693] EXT4-fs (sda5): ext4_orphan_cleanup: deleting unreferenced inode 10224710
Dec 25 07:53:25 hylas-Aspire-X3812 kernel: [    4.343743] EXT4-fs (sda5): ext4_orphan_cleanup: deleting unreferenced inode 10224157
Dec 25 07:53:25 hylas-Aspire-X3812 kernel: [    4.343757] EXT4-fs (sda5): ext4_orphan_cleanup: deleting unreferenced inode 6166109
Dec 25 07:53:25 hylas-Aspire-X3812 kernel: [    4.343770] EXT4-fs (sda5): ext4_orphan_cleanup: deleting unreferenced inode 6029321
Dec 25 07:53:25 hylas-Aspire-X3812 kernel: [    4.343783] EXT4-fs (sda5): ext4_orphan_cleanup: deleting unreferenced inode 6161633
Dec 25 07:53:25 hylas-Aspire-X3812 kernel: [    4.343795] EXT4-fs (sda5): ext4_orphan_cleanup: deleting unreferenced inode 6029345
Dec 25 07:53:25 hylas-Aspire-X3812 kernel: [    4.343825] EXT4-fs (sda5): 6 orphan inodes deleted
Dec 25 07:53:25 hylas-Aspire-X3812 kernel: [    4.343827] EXT4-fs (sda5): recovery complete
Dec 25 07:53:25 hylas-Aspire-X3812 kernel: [    5.250685] EXT4-fs (sda5): mounted filesystem with ordered data mode. Opts: (null)
Dec 25 07:53:25 hylas-Aspire-X3812 kernel: [   14.265339] lp: driver loaded but no devices found
Dec 25 07:53:25 hylas-Aspire-X3812 kernel: [   14.293627] [drm] Initialized drm 1.1.0 20060810
Dec 25 07:53:25 hylas-Aspire-X3812 kernel: [   14.301940] Adding 33554428k swap on /dev/sda6.  Priority:-1 extents:1 across:33554428k 
Dec 25 07:53:25 hylas-Aspire-X3812 kernel: [   14.314441] wmi: Mapper loaded
Dec 25 07:53:25 hylas-Aspire-X3812 kernel: [   14.330684] i915 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Dec 25 07:53:25 hylas-Aspire-X3812 kernel: [   14.330690] i915 0000:00:02.0: setting latency timer to 64
Dec 25 07:53:25 hylas-Aspire-X3812 kernel: [   14.396553] type=1400 audit(1324799605.167:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=488 comm="apparmor_parser"
Dec 25 07:53:25 hylas-Aspire-X3812 kernel: [   14.396905] type=1400 audit(1324799605.167:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=488 comm="apparmor_parser"
Dec 25 07:53:25 hylas-Aspire-X3812 kernel: [   14.397127] type=1400 audit(1324799605.167:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=488 comm="apparmor_parser"
Dec 25 07:53:25 hylas-Aspire-X3812 kernel: [   14.425307] i915 0000:00:02.0: irq 43 for MSI/MSI-X
Dec 25 07:53:25 hylas-Aspire-X3812 kernel: [   14.425313] [drm] Supports vblank timestamp caching Rev 1 (10.10.2010).
Dec 25 07:53:25 hylas-Aspire-X3812 kernel: [   14.425315] [drm] Driver supports precise vblank timestamp query.
Dec 25 07:53:25 hylas-Aspire-X3812 kernel: [   14.425347] vgaarb: device changed decodes: PCI:0000:00:02.0,olddecodes=io+mem,decodes=io+mem:owns=io+mem
Dec 25 07:53:25 hylas-Aspire-X3812 kernel: [   14.600644] EXT4-fs (sda5): re-mounted. Opts: errors=remount-ro
Dec 25 07:53:25 hylas-Aspire-X3812 kernel: [   14.655162] fbcon: inteldrmfb (fb0) is primary device
Dec 25 07:53:25 hylas-Aspire-X3812 kernel: [   14.655258] Console: switching to colour frame buffer device 180x56
Dec 25 07:53:25 hylas-Aspire-X3812 kernel: [   14.655287] fb0: inteldrmfb frame buffer device
Dec 25 07:53:25 hylas-Aspire-X3812 kernel: [   14.655289] drm: registered panic notifier
Dec 25 07:53:25 hylas-Aspire-X3812 kernel: [   14.655300] No ACPI video bus found
Dec 25 07:53:25 hylas-Aspire-X3812 kernel: [   14.655366] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
Dec 25 07:53:25 hylas-Aspire-X3812 kernel: [   14.655430] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
Dec 25 07:53:25 hylas-Aspire-X3812 kernel: [   14.655475] HDA Intel 0000:00:1b.0: irq 44 for MSI/MSI-X
Dec 25 07:53:25 hylas-Aspire-X3812 kernel: [   14.655500] HDA Intel 0000:00:1b.0: setting latency timer to 64
Dec 25 07:53:25 hylas-Aspire-X3812 kernel: [   14.696298] hda_codec: ALC888: BIOS auto-probing.
Dec 25 07:53:25 hylas-Aspire-X3812 kernel: [   14.712171] HDMI status: Pin=3 Presence_Detect=0 ELD_Valid=0
Dec 25 07:53:25 hylas-Aspire-X3812 kernel: [   14.712494] input: HDA Intel HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:1b.0/sound/card0/input4
Dec 25 07:53:25 hylas-Aspire-X3812 kernel: [   14.713038] input: HDA Intel Headphone as /devices/pci0000:00/0000:00:1b.0/sound/card0/input5
Dec 25 07:53:25 hylas-Aspire-X3812 polkitd[789]: started daemon version 0.102 using authority implementation `local' version `0.102'
Dec 25 07:53:25 hylas-Aspire-X3812 dbus[769]: [system] Successfully activated service 'org.freedesktop.PolicyKit1'
Dec 25 07:53:25 hylas-Aspire-X3812 NetworkManager[779]:    SCPlugin-Ifupdown: init!
Dec 25 07:53:25 hylas-Aspire-X3812 NetworkManager[779]:    SCPlugin-Ifupdown: update_system_hostname
Dec 25 07:53:25 hylas-Aspire-X3812 NetworkManager[779]:    SCPluginIfupdown: management mode: unmanaged
Dec 25 07:53:25 hylas-Aspire-X3812 NetworkManager[779]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:19.0/net/eth0, iface: eth0)
Dec 25 07:53:25 hylas-Aspire-X3812 NetworkManager[779]:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:19.0/net/eth0, iface: eth0): no ifupdown configuration found.
Dec 25 07:53:25 hylas-Aspire-X3812 NetworkManager[779]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/virtual/net/lo, iface: lo)
Dec 25 07:53:25 hylas-Aspire-X3812 NetworkManager[779]:    SCPlugin-Ifupdown: device added (path: /sys/devices/virtual/net/lo, iface: lo): no ifupdown configuration found.
Dec 25 07:53:25 hylas-Aspire-X3812 NetworkManager[779]:    SCPlugin-Ifupdown: end _init.
Dec 25 07:53:25 hylas-Aspire-X3812 NetworkManager[779]: <info> Loaded plugin ifupdown: (C) 2008 Canonical Ltd.  To report bugs please use the NetworkManager mailing list.
Dec 25 07:53:25 hylas-Aspire-X3812 NetworkManager[779]: <info> Loaded plugin keyfile: (c) 2007 - 2010 Red Hat, Inc.  To report bugs please use the NetworkManager mailing list.
Dec 25 07:53:25 hylas-Aspire-X3812 NetworkManager[779]:    Ifupdown: get unmanaged devices count: 0
Dec 25 07:53:25 hylas-Aspire-X3812 NetworkManager[779]:    SCPlugin-Ifupdown: (142646152) ... get_connections.
Dec 25 07:53:25 hylas-Aspire-X3812 NetworkManager[779]:    SCPlugin-Ifupdown: (142646152) ... get_connections (managed=false): return empty list.
Dec 25 07:53:25 hylas-Aspire-X3812 NetworkManager[779]:    Ifupdown: get unmanaged devices count: 0
Dec 25 07:53:25 hylas-Aspire-X3812 NetworkManager[779]: <info> modem-manager is now available
Dec 25 07:53:25 hylas-Aspire-X3812 NetworkManager[779]: <info> monitoring kernel firmware directory '/lib/firmware'.
Dec 25 07:53:25 hylas-Aspire-X3812 NetworkManager[779]: <info> WiFi enabled by radio killswitch; enabled by state file
Dec 25 07:53:25 hylas-Aspire-X3812 NetworkManager[779]: <info> WWAN enabled by radio killswitch; enabled by state file
Dec 25 07:53:25 hylas-Aspire-X3812 NetworkManager[779]: <info> WiMAX enabled by radio killswitch; enabled by state file
Dec 25 07:53:25 hylas-Aspire-X3812 NetworkManager[779]: <info> Networking is enabled by state file
Dec 25 07:53:25 hylas-Aspire-X3812 NetworkManager[779]: <info> (eth0): carrier is OFF
Dec 25 07:53:25 hylas-Aspire-X3812 NetworkManager[779]: <info> (eth0): new Ethernet device (driver: 'e1000e' ifindex: 2)
Dec 25 07:53:25 hylas-Aspire-X3812 NetworkManager[779]: <info> (eth0): exported as /org/freedesktop/NetworkManager/Devices/0
Dec 25 07:53:25 hylas-Aspire-X3812 NetworkManager[779]: <info> (eth0): now managed
Dec 25 07:53:25 hylas-Aspire-X3812 NetworkManager[779]: <info> (eth0): device state change: unmanaged -> unavailable (reason 'managed') [10 20 2]
Dec 25 07:53:25 hylas-Aspire-X3812 NetworkManager[779]: <info> (eth0): bringing up device.
Dec 25 07:53:25 hylas-Aspire-X3812 kernel: [   15.057675] type=1400 audit(1324799605.827:5): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=863 comm="apparmor_parser"
Dec 25 07:53:25 hylas-Aspire-X3812 kernel: [   15.058769] type=1400 audit(1324799605.827:6): apparmor="STATUS" operation="profile_load" name="/usr/lib/lightdm/lightdm-guest-session-wrapper" pid=862 comm="apparmor_parser"
Dec 25 07:53:25 hylas-Aspire-X3812 kernel: [   15.059630] type=1400 audit(1324799605.827:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=863 comm="apparmor_parser"
Dec 25 07:53:25 hylas-Aspire-X3812 kernel: [   15.059881] type=1400 audit(1324799605.827:8): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=863 comm="apparmor_parser"
Dec 25 07:53:25 hylas-Aspire-X3812 kernel: [   15.064754] type=1400 audit(1324799605.835:9): apparmor="STATUS" operation="profile_load" name="/usr/lib/telepathy/mission-control-5" pid=867 comm="apparmor_parser"
Dec 25 07:53:25 hylas-Aspire-X3812 kernel: [   15.065119] type=1400 audit(1324799605.835:10): apparmor="STATUS" operation="profile_load" name="/usr/lib/telepathy/telepathy-*" pid=867 comm="apparmor_parser"
Dec 25 07:53:25 hylas-Aspire-X3812 kernel: [   15.068119] type=1400 audit(1324799605.839:11): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince" pid=865 comm="apparmor_parser"
Dec 25 07:53:25 hylas-Aspire-X3812 kernel: [   15.092186] e1000e 0000:00:19.0: irq 41 for MSI/MSI-X
Dec 25 07:53:25 hylas-Aspire-X3812 NetworkManager[779]: <info> (eth0): preparing device.
Dec 25 07:53:25 hylas-Aspire-X3812 NetworkManager[779]: <info> (eth0): deactivating device (reason 'managed') [2]
Dec 25 07:53:25 hylas-Aspire-X3812 NetworkManager[779]: <info> Added default wired connection 'Wired connection 1' for /sys/devices/pci0000:00/0000:00:19.0/net/eth0
Dec 25 07:53:25 hylas-Aspire-X3812 NetworkManager[779]: <warn> bluez error getting default adapter: The name org.bluez was not provided by any .service files
Dec 25 07:53:25 hylas-Aspire-X3812 kernel: [   15.148088] e1000e 0000:00:19.0: irq 41 for MSI/MSI-X
Dec 25 07:53:25 hylas-Aspire-X3812 kernel: [   15.148326] ADDRCONF(NETDEV_UP): eth0: link is not ready
Dec 25 07:53:25 hylas-Aspire-X3812 kernel: [   15.187669] init: failsafe main process (748) killed by TERM signal
Dec 25 07:53:25 hylas-Aspire-X3812 kernel: [   15.189957] init: apport pre-start process (904) terminated with status 1
Dec 25 07:53:25 hylas-Aspire-X3812 acpid: starting up with proc fs
Dec 25 07:53:25 hylas-Aspire-X3812 cron[911]: (CRON) INFO (pidfile fd = 3)
Dec 25 07:53:25 hylas-Aspire-X3812 acpid: 32 rules loaded
Dec 25 07:53:25 hylas-Aspire-X3812 acpid: waiting for events: event logging is off
Dec 25 07:53:25 hylas-Aspire-X3812 kernel: [   15.211202] init: apport post-stop process (945) terminated with status 1
Dec 25 07:53:25 hylas-Aspire-X3812 anacron[951]: Anacron 2.3 started on 2011-12-25
Dec 25 07:53:25 hylas-Aspire-X3812 cron[953]: (CRON) STARTUP (fork ok)
Dec 25 07:53:25 hylas-Aspire-X3812 cron[953]: (CRON) INFO (Running @reboot jobs)
Dec 25 07:53:26 hylas-Aspire-X3812 acpid: client connected from 970[0:0]
Dec 25 07:53:26 hylas-Aspire-X3812 acpid: 1 client rule loaded
Dec 25 07:53:26 hylas-Aspire-X3812 anacron[951]: Normal exit (0 jobs run)
Dec 25 07:53:26 hylas-Aspire-X3812 bluetoothd[1006]: Bluetooth daemon 4.96
Dec 25 07:53:26 hylas-Aspire-X3812 bluetoothd[1006]: Starting SDP server
Dec 25 07:53:26 hylas-Aspire-X3812 kernel: [   15.465682] Bluetooth: Core ver 2.16
Dec 25 07:53:26 hylas-Aspire-X3812 kernel: [   15.465725] NET: Registered protocol family 31
Dec 25 07:53:26 hylas-Aspire-X3812 kernel: [   15.465727] Bluetooth: HCI device and connection manager initialized
Dec 25 07:53:26 hylas-Aspire-X3812 kernel: [   15.465729] Bluetooth: HCI socket layer initialized
Dec 25 07:53:26 hylas-Aspire-X3812 kernel: [   15.465731] Bluetooth: L2CAP socket layer initialized
Dec 25 07:53:26 hylas-Aspire-X3812 kernel: [   15.466168] Bluetooth: SCO socket layer initialized
Dec 25 07:53:26 hylas-Aspire-X3812 kernel: [   15.468630] Bluetooth: RFCOMM TTY layer initialized
Dec 25 07:53:26 hylas-Aspire-X3812 kernel: [   15.468636] Bluetooth: RFCOMM socket layer initialized
Dec 25 07:53:26 hylas-Aspire-X3812 kernel: [   15.468638] Bluetooth: RFCOMM ver 1.11
Dec 25 07:53:26 hylas-Aspire-X3812 NetworkManager[779]: <warn> bluez error getting default adapter: No such adapter
Dec 25 07:53:26 hylas-Aspire-X3812 kernel: [   15.499172] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
Dec 25 07:53:26 hylas-Aspire-X3812 kernel: [   15.499175] Bluetooth: BNEP filters: protocol multicast
Dec 25 07:53:26 hylas-Aspire-X3812 kernel: [   15.601102] ppdev: user-space parallel port driver
Dec 25 07:53:26 hylas-Aspire-X3812 anacron[1112]: Anacron 2.3 started on 2011-12-25
Dec 25 07:53:26 hylas-Aspire-X3812 anacron[1112]: Normal exit (0 jobs run)
Dec 25 07:53:26 hylas-Aspire-X3812 kernel: [   15.660557] init: plymouth-upstart-bridge main process (774) killed by TERM signal
Dec 25 07:53:26 hylas-Aspire-X3812 dbus[769]: [system] Activating service name='org.freedesktop.Accounts' (using servicehelper)
Dec 25 07:53:26 hylas-Aspire-X3812 dbus[769]: [system] Successfully activated service 'org.freedesktop.Accounts'
Dec 25 07:53:26 hylas-Aspire-X3812 accounts-daemon[1121]: started daemon version 0.6.14
Dec 25 07:53:26 hylas-Aspire-X3812 dbus[769]: [system] Activating service name='org.freedesktop.ConsoleKit' (using servicehelper)
Dec 25 07:53:26 hylas-Aspire-X3812 dbus[769]: [system] Successfully activated service 'org.freedesktop.ConsoleKit'
Dec 25 07:53:26 hylas-Aspire-X3812 udev-configure-printer: add /module/lp
Dec 25 07:53:26 hylas-Aspire-X3812 udev-configure-printer: Failed to get parent
Dec 25 07:53:27 hylas-Aspire-X3812 NetworkManager[779]: <info> (eth0): carrier now ON (device state 20)
Dec 25 07:53:27 hylas-Aspire-X3812 NetworkManager[779]: <info> (eth0): device state change: unavailable -> disconnected (reason 'carrier-changed') [20 30 40]
Dec 25 07:53:27 hylas-Aspire-X3812 NetworkManager[779]: <info> Auto-activating connection 'Wired connection 1'.
Dec 25 07:53:27 hylas-Aspire-X3812 NetworkManager[779]: <info> Activation (eth0) starting connection 'Wired connection 1'
Dec 25 07:53:27 hylas-Aspire-X3812 NetworkManager[779]: <info> (eth0): device state change: disconnected -> prepare (reason 'none') [30 40 0]
Dec 25 07:53:27 hylas-Aspire-X3812 NetworkManager[779]: <info> Activation (eth0) Stage 1 of 5 (Device Prepare) scheduled...
Dec 25 07:53:27 hylas-Aspire-X3812 NetworkManager[779]: <info> Activation (eth0) Stage 1 of 5 (Device Prepare) started...
Dec 25 07:53:27 hylas-Aspire-X3812 NetworkManager[779]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) scheduled...
Dec 25 07:53:27 hylas-Aspire-X3812 NetworkManager[779]: <info> Activation (eth0) Stage 1 of 5 (Device Prepare) complete.
Dec 25 07:53:27 hylas-Aspire-X3812 NetworkManager[779]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) starting...
Dec 25 07:53:27 hylas-Aspire-X3812 NetworkManager[779]: <info> (eth0): device state change: prepare -> config (reason 'none') [40 50 0]
Dec 25 07:53:27 hylas-Aspire-X3812 NetworkManager[779]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) successful.
Dec 25 07:53:27 hylas-Aspire-X3812 NetworkManager[779]: <info> Activation (eth0) Stage 3 of 5 (IP Configure Start) scheduled.
Dec 25 07:53:27 hylas-Aspire-X3812 NetworkManager[779]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) complete.
Dec 25 07:53:27 hylas-Aspire-X3812 NetworkManager[779]: <info> Activation (eth0) Stage 3 of 5 (IP Configure Start) started...
Dec 25 07:53:27 hylas-Aspire-X3812 NetworkManager[779]: <info> (eth0): device state change: config -> ip-config (reason 'none') [50 70 0]
Dec 25 07:53:27 hylas-Aspire-X3812 NetworkManager[779]: <info> Activation (eth0) Beginning DHCPv4 transaction (timeout in 45 seconds)
Dec 25 07:53:27 hylas-Aspire-X3812 kernel: [   16.708917] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: Rx/Tx
Dec 25 07:53:27 hylas-Aspire-X3812 kernel: [   16.708922] e1000e 0000:00:19.0: eth0: 10/100 speed: disabling TSO
Dec 25 07:53:27 hylas-Aspire-X3812 kernel: [   16.709093] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
Dec 25 07:53:27 hylas-Aspire-X3812 dhclient: Internet Systems Consortium DHCP Client 4.1.1-P1
Dec 25 07:53:27 hylas-Aspire-X3812 dhclient: Copyright 2004-2010 Internet Systems Consortium.
Dec 25 07:53:27 hylas-Aspire-X3812 dhclient: All rights reserved.
Dec 25 07:53:27 hylas-Aspire-X3812 dhclient: For info, please visit [https://www.isc.org/software/dhcp/](https://www.isc.org/software/dhcp/)
Dec 25 07:53:27 hylas-Aspire-X3812 dhclient: 
Dec 25 07:53:27 hylas-Aspire-X3812 NetworkManager[779]: <info> dhclient started with pid 1235
Dec 25 07:53:27 hylas-Aspire-X3812 NetworkManager[779]: <info> Activation (eth0) Stage 3 of 5 (IP Configure Start) complete.
Dec 25 07:53:27 hylas-Aspire-X3812 dbus[769]: [system] Activating service name='org.freedesktop.UPower' (using servicehelper)
Dec 25 07:53:27 hylas-Aspire-X3812 dbus[769]: [system] Successfully activated service 'org.freedesktop.UPower'
Dec 25 07:53:27 hylas-Aspire-X3812 NetworkManager[779]: <info> (eth0): DHCPv4 state changed nbi -> preinit
Dec 25 07:53:27 hylas-Aspire-X3812 dhclient: Listening on LPF/eth0/00:26:2d:18:62:83
Dec 25 07:53:27 hylas-Aspire-X3812 dhclient: Sending on   LPF/eth0/00:26:2d:18:62:83
Dec 25 07:53:27 hylas-Aspire-X3812 dhclient: Sending on   Socket/fallback
Dec 25 07:53:27 hylas-Aspire-X3812 dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
Dec 25 07:53:27 hylas-Aspire-X3812 dbus[769]: [system] Activating service name='org.freedesktop.ColorManager' (using servicehelper)
Dec 25 07:53:27 hylas-Aspire-X3812 dbus[769]: [system] Successfully activated service 'org.freedesktop.ColorManager'
Dec 25 07:53:28 hylas-Aspire-X3812 kernel: [   17.402544] EXT4-fs (sda5): re-mounted. Opts: errors=remount-ro,commit=0
Dec 25 07:53:28 hylas-Aspire-X3812 dbus[769]: [system] Activating service name='org.freedesktop.RealtimeKit1' (using servicehelper)
Dec 25 07:53:28 hylas-Aspire-X3812 dbus[769]: [system] Successfully activated service 'org.freedesktop.RealtimeKit1'
Dec 25 07:53:28 hylas-Aspire-X3812 rtkit-daemon[1316]: Successfully called chroot.
Dec 25 07:53:28 hylas-Aspire-X3812 rtkit-daemon[1316]: Successfully dropped privileges.
Dec 25 07:53:28 hylas-Aspire-X3812 rtkit-daemon[1316]: Successfully limited resources.
Dec 25 07:53:28 hylas-Aspire-X3812 rtkit-daemon[1316]: Running.
Dec 25 07:53:28 hylas-Aspire-X3812 rtkit-daemon[1316]: Canary thread running.
Dec 25 07:53:28 hylas-Aspire-X3812 rtkit-daemon[1316]: Successfully made thread 1314 of process 1314 (n/a) owned by '104' high priority at nice level -11.
Dec 25 07:53:28 hylas-Aspire-X3812 rtkit-daemon[1316]: Supervising 1 threads of 1 processes of 1 users.
Dec 25 07:53:28 hylas-Aspire-X3812 rtkit-daemon[1316]: Watchdog thread running.
Dec 25 07:53:28 hylas-Aspire-X3812 rtkit-daemon[1316]: Successfully made thread 1338 of process 1314 (n/a) owned by '104' RT at priority 5.
Dec 25 07:53:28 hylas-Aspire-X3812 rtkit-daemon[1316]: Supervising 2 threads of 1 processes of 1 users.
Dec 25 07:53:28 hylas-Aspire-X3812 rtkit-daemon[1316]: Successfully made thread 1339 of process 1314 (n/a) owned by '104' RT at priority 5.
Dec 25 07:53:28 hylas-Aspire-X3812 rtkit-daemon[1316]: Supervising 3 threads of 1 processes of 1 users.
Dec 25 07:53:28 hylas-Aspire-X3812 kernel: [   17.805885] init: plymouth-stop pre-start process (1351) terminated with status 1
Dec 25 07:53:29 hylas-Aspire-X3812 dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5
Dec 25 07:53:33 hylas-Aspire-X3812 rtkit-daemon[1316]: Successfully made thread 1463 of process 1463 (n/a) owned by '1000' high priority at nice level -11.
Dec 25 07:53:33 hylas-Aspire-X3812 rtkit-daemon[1316]: Supervising 4 threads of 2 processes of 2 users.
Dec 25 07:53:33 hylas-Aspire-X3812 rtkit-daemon[1316]: Successfully made thread 1466 of process 1463 (n/a) owned by '1000' RT at priority 5.
Dec 25 07:53:33 hylas-Aspire-X3812 rtkit-daemon[1316]: Supervising 5 threads of 2 processes of 2 users.
Dec 25 07:53:33 hylas-Aspire-X3812 rtkit-daemon[1316]: Successfully made thread 1467 of process 1463 (n/a) owned by '1000' RT at priority 5.
Dec 25 07:53:33 hylas-Aspire-X3812 rtkit-daemon[1316]: Supervising 6 threads of 2 processes of 2 users.
Dec 25 07:53:33 hylas-Aspire-X3812 rtkit-daemon[1316]: Successfully made thread 1471 of process 1471 (n/a) owned by '1000' high priority at nice level -11.
Dec 25 07:53:33 hylas-Aspire-X3812 rtkit-daemon[1316]: Supervising 7 threads of 3 processes of 2 users.
Dec 25 07:53:33 hylas-Aspire-X3812 pulseaudio[1471]: [pulseaudio] pid.c: Daemon already running.
Dec 25 07:53:34 hylas-Aspire-X3812 dbus[769]: [system] Activating service name='org.freedesktop.UDisks' (using servicehelper)
Dec 25 07:53:34 hylas-Aspire-X3812 dbus[769]: [system] Successfully activated service 'org.freedesktop.UDisks'
Dec 25 07:53:34 hylas-Aspire-X3812 dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
Dec 25 07:53:35 hylas-Aspire-X3812 dhclient: DHCPOFFER of 10.0.0.3 from 10.0.0.2
Dec 25 07:53:35 hylas-Aspire-X3812 dhclient: DHCPREQUEST of 10.0.0.3 on eth0 to 255.255.255.255 port 67
Dec 25 07:53:35 hylas-Aspire-X3812 dhclient: DHCPACK of 10.0.0.3 from 10.0.0.2
Dec 25 07:53:35 hylas-Aspire-X3812 dhclient: bound to 10.0.0.3 -- renewal in 32736 seconds.
Dec 25 07:53:35 hylas-Aspire-X3812 NetworkManager[779]: <info> (eth0): DHCPv4 state changed preinit -> bound
Dec 25 07:53:35 hylas-Aspire-X3812 NetworkManager[779]: <info> Activation (eth0) Stage 4 of 5 (IP4 Configure Get) scheduled...
Dec 25 07:53:35 hylas-Aspire-X3812 NetworkManager[779]: <info> Activation (eth0) Stage 4 of 5 (IP4 Configure Get) started...
Dec 25 07:53:35 hylas-Aspire-X3812 NetworkManager[779]: <info>   address 10.0.0.3
Dec 25 07:53:35 hylas-Aspire-X3812 NetworkManager[779]: <info>   prefix 24 (255.255.255.0)
Dec 25 07:53:35 hylas-Aspire-X3812 NetworkManager[779]: <info>   gateway 10.0.0.2
Dec 25 07:53:35 hylas-Aspire-X3812 NetworkManager[779]: <info>   nameserver '10.0.0.2'
Dec 25 07:53:35 hylas-Aspire-X3812 NetworkManager[779]: <info> Activation (eth0) Stage 5 of 5 (IP Configure Commit) started...
Dec 25 07:53:36 hylas-Aspire-X3812 NetworkManager[779]: <info> (eth0): device state change: ip-config -> activated (reason 'none') [70 100 0]
Dec 25 07:53:36 hylas-Aspire-X3812 NetworkManager[779]: <info> Policy set 'Wired connection 1' (eth0) as default for IPv4 routing and DNS.
Dec 25 07:53:36 hylas-Aspire-X3812 NetworkManager[779]: <info> Activation (eth0) successful, device activated.
Dec 25 07:53:36 hylas-Aspire-X3812 NetworkManager[779]: <info> Activation (eth0) Stage 5 of 5 (IP Configure Commit) complete.
Dec 25 07:53:36 hylas-Aspire-X3812 NetworkManager[779]: <info> Activation (eth0) Stage 4 of 5 (IP4 Configure Get) complete.
Dec 25 07:53:36 hylas-Aspire-X3812 dbus[769]: [system] Activating service name='org.freedesktop.nm_dispatcher' (using servicehelper)
Dec 25 07:53:36 hylas-Aspire-X3812 dbus[769]: [system] Successfully activated service 'org.freedesktop.nm_dispatcher'
Dec 25 07:53:38 hylas-Aspire-X3812 kernel: [   27.648012] eth0: no IPv6 routers present
Dec 25 07:53:44 hylas-Aspire-X3812 ntpdate[1567]: adjust time server 91.189.94.4 offset 0.443424 sec
hylas@hylas-Aspire-X3812:~$ 
```


It happened yet again this morning :(
If it's of any use, i was running system monitor when the freeze up happened this time (to see if there was a memory or cpu 'spike' at the point of the crash) but there was no apparent sudden drain.

I hope the above is of use, i'm afraid it makes little sense to me!

Many thanks for any help. I'd very much like to stop these halts, as i'm otherwise very pleased with the system as it is.

---

### Post by bobsageek on 2011-12-26
Outside of it not mounting a USB device (from bluez, so probably BlueTooth related, think I've seen that before) nothing leaps out. Can you post the output from lsusb. Thanks.

---

### Post by Hylas de Niall on 2011-12-27
There is no bluetooth hardware native on this machine, so maybe that's why theres a warn message? i plug in a usb dongle when i need to use that function - which is never these days, and certainly never since installing Oneiric :)

hylas@hylas-Aspire-X3812:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 058f:6363 Alcor Micro Corp. 
Bus 005 Device 002: ID 045e:00f6 Microsoft Corp. Comfort Optical Mouse 1000

I wonder if it's the mouse?
 
Thanks again for any and all help!

---

### Post by Hylas de Niall on 2011-12-27
I've swapped the usb M$ mouse for the original Acer PS2 one to see if that helps.

---

### Post by ZeddCypher on 2011-12-27
I had been having a similar problem on my desktop.  I built a dual boot Windows 7 and Ubuntu 11.10 build.  The Windows 7 worked well with no random restarts or lock ups.  Ubuntu however would whenever I was streaming, watching movies, downloading, anything/anytime etc.. With it being a new build I originally thought hardware but the system temperature was cool and Windows was not having the same problem

I have been watching this forum and decided to take one posters advice and flashed the bios and updated all the MB/Video drivers.  And that ended up fixing my problem.  Have not had a lock up or restart yet so maybe that would work for you?

Idea of my setup if it helps...
MB: MSI 970A
HD: SSD 80GB
RAM: 8GB
Video: ATI 5570
System Temp: 25-30 Celsius 

I went to the Motherboard manufacturer site and found a live update program that linked me to all the updates Perhaps this could work for you too

---

### Post by Hylas de Niall on 2011-12-28
I'll give the mouse theory a week first, i think, before flashing the bios (which i'd much rather not have to do, TBH).

How would i update the MoBo etc drivers though? I mean, i know how in 'doze' but no idea for my Ubu. I should add at this point that i'm not savvy with compiling, or even installing anything outside of the Ubu stable.
I'm only just now tentatively starting to use other ppa's.

****just as an aside, and to show how inept i can be, can someone let me know how to post my terminal results in a scrolling window please?****

---

### Post by ZeddCypher on 2011-12-28
Hah it's fine.  This is my first go at Ubuntu and probably should only stay in my corner at Absolute Beginner Thread.  

I had two options specific to me that may be true for you.  During the boot up I could hit F2 and bring up the BIOS screen and motherboard settings.  Within these settings there was a section for "Live Update."  In this section it gave some details on how to update drivers and how to find the latest versions.

I took a second route.  I went to the Manufacturer site and they provided a step by step how to document on using the Live Update.  They gave the option of "compiling" and doing the technical route.  However since I chose to do a dual boot, I used the Windows 7 boot and downloaded installed the drivers and updates patches through that instead of Ubuntu.  Cheating probably but it worked.

Best Advice (from a newb mind you) is to just go to the manufacturer site and see what they can tell you from their documentation.  At this point it seems like it will not take anymore time then you've already spent stuck on this issue.

---

### Post by howefield on 2011-12-28
> **Hylas de Niall said:**
> can someone let me know how to post my terminal results in a scrolling window please?****

When posting, highlight the text to be placed inside the scrolling window and click on the the code tags icon, third icon from the right, bottom row as per screen shot...

---

### Post by Hylas de Niall on 2011-12-30
> **howefield said:**
> When posting, highlight the text to be placed inside the scrolling window and click on the the code tags icon, third icon from the right, bottom row as per screen shot...

Ah, many thanks for that!

@ZeddCypher: It looks as though i will be investigating the options you refer to, as the machine locked up on me yet again this morning. It wasn't a mouse issue after all, more's the pity.

Additional: I visited the Acer site and downloaded the only BIOS update there was for my machine (dated 2009), I bought the machine April 2010 (though there's no telling how long it sat on a pallet in a warehouse).
There was also an updated chipset driver *for Windows* which surely would have no effect on my Ubu?

---

### Post by Hylas de Niall on 2011-12-30
BIOS was already patched to the version available from Acer :(
P01-A1 Sept '09

Temperature info (from CMOS setup):
CPU: 23deg C
System: 53deg C

Next option is to check that everything is seated firmly inside the box, but no issues in Win7 so i doubt if it's that.

---

### Post by Hylas de Niall on 2012-01-05
Agh! It's still happening.
I guess OO just doesn't like my desktop machine (though it *loves* my netbook).
Does anyone have any other suggestions? Would a fresh install do the trick?
I'm seriously considering giving the whole drive back to Windows (reluctantly), but i really don't want to.

---

### Post by ZeddCypher on 2012-01-06
Sorry I'm out of ideas for it...

---

### Post by Rebelli0us on 2012-01-06
I was getting random lock-ups, removed the proprietary video driver and the problem is gone.

---

### Post by Z06Gal on 2012-01-07
I am having the same issue regardless of what de I am in.  I have had to do 4 hard shutdowns in 2 hours.  This is insane.  I have tried changing browsers, mouse settings, updating drivers, and I even removed pulseaudio but nothing has helped.  I have also tried 4 kernels.  I do not recall ever having this issue prior to Oneiric but I definitely have it now. :o

---

### Post by Hylas de Niall on 2012-01-08
> **Z06Gal said:**
> I am having the same issue regardless of what de I am in.  I have had to do 4 hard shutdowns in 2 hours.  This is insane.  I have tried changing browsers, mouse settings, updating drivers, and I even removed pulseaudio but nothing has helped.  I have also tried 4 kernels.  I do not recall ever having this issue prior to Oneiric but I definitely have it now. :o

I'm now working on the theory that that install itself didn't 'take' properly. Like yourself, this has continued for this machine across kernel updates, in both Gnome Shell *and* Unity, using FF and Chromium, etc, here too.

I'm going to back up my apps and docs, and fresh install the system from a different 'OO' source disk (as well as my downloaded copy i have cover DVD's from various magazines).

If that doesn't work I'll give the drive back to 'Doze, as i'm all out of ideas. But i'll be gutted about that because 11.10 is a lovely release and, as i've mentioned, it's running as good as gold on one of my other machines.

I hope the reinstall cures this issue, and will report back here as soon as i'm sure that it has.

---

### Post by Hylas de Niall on 2012-01-08
Fresh install is running great so far, it's been running six or so hours and no lock-up.

Graphics are currently listed as 'unknown' whereas previously it recognised my chipset (after some updates).

 ...does anyone know how i can keep the graphics at 'unknown' - to test a theory - without trawling through every update offered and unchecking the gfx updates?

---

### Post by Hylas de Niall on 2012-01-08
> **Rebelli0us said:**
> I was getting random lock-ups, **removed the proprietary video driver** and the problem is gone.


Should the GMAX4500 (my chipset) driver slip past me (if there is no way to prevent it installing), could you tell me how it can be removed?
Or was your driver one listed in the 'Additional drivers' section of settings?

Cheers!

---

### Post by Hylas de Niall on 2012-01-09
Well, it's still running like a charm, Graphics still listed as 'unknown', so i think it might have been the gfx driver installed during a previous update, but i thought the kernel handles hardware drivers in linux? It's the same kernel i was running before?
How can i make sure it stays in this state while i continue testing?
Should i temporarily disable updates, or would that be too extreme?
:confused:

additional: I have set it t check for updates 'never' for the time being.

---

### Post by Hylas de Niall on 2012-01-12
I got another lock-up this morning.
I'm at the end of my thether on this now and will try one more shot with 10.10 instead, and if that does the same it's bye-bye Ubuntu on this machine :(

Apologies to Cmill for hijacking your thread BTW

---

### Post by Hylas de Niall on 2012-01-12
......okay.

whilst running the install for 10.10 i see that there were TWO linux swap partitions: one at 3gb and one at a massive 60gb. Could that have caused the issues? could the system have been writing to one, and trying to read back from the other?

Whatever, i erased both the swap partitions and the existing Ubu system partition and set up a new 6gb swap and XXXgb '/' for system.
The install went flawlessly, grub successfully found my Win7 and the new Ubu 10.10, and everything now seems hunky-dory.

...I'm now left wondering if the two swaps were causing the issues i had, and that maybe i should have done the above whilst reinstalling 11.10?

:confused:

Now i'm just waiting for it to lock up on me again! LOL!

Any ideas folks?

---

### Post by Hylas de Niall on 2012-01-17
10.10 seems to be running fine I'm very pleased to say :)
It's booting up in about a third the time 11.10 did, isn't locking/freezing up (so far!), everything is working beautifully.
I'd still be interested in what may have been happening on my machine with 11.10 though, as i'm keen to climb aboard with the 12.04 LTS release when it comes along.

---

### Post by the-oggy on 2012-01-17
I also had issues with lockups on my HP 6910p, nothig i did seemed to help, it was insane, UI would just freeze so that just mouse was moving but without being able to perform a click. I found nothing unusual in the logs. 

However, sometimes I was able to switch to tty1 using ctrl-alt-f1, this led me to conclude that the gnome3 environment itself is causing the lock-ups. I almost wiped hard-drive with arch linux when i decided to give a try to xfce4.

Now I'm happy with it. No more damn lock-ups. Even the system seems to be much more responsive than before, not to speak about drastically reduced amount of used RAM.

Give xfce4 a try, you'll be surprised.

---

### Post by Hylas de Niall on 2012-01-17
No go.
My lock-ups were total: no mouse control or (visible at least) keyboard control. Cold reboot only. :(

I've tried XFCE and i liked it a lot, maybe i'll try some extended live sessions with Xubuntu 11.10 and see what happens with that, but i don't want to sour my install of 10.10 while it seems to be working so nicely.
11.10 seems to be too sluggish on that desktop machine - whatever flavour i'm running. That's the only conclusion i come to, comparing boot times and speed between 11.10 and 10.10.

Ironically (as i've mentioned elsewhere") 11.10 seems to love my little netbook ...I just can't figure it out! LOL!

But i only have a couple of months support left for 10.10, right? So i'll look to the future and try the next LTS when it's here, and see what happens.

I may even risk it from beta. :D

*Re: XFCE "crashes" sometimes but no idea why - help
> **Hylas de Niall said:**
> I *think* this is an issue with 11.10. I have seen lots of reports of intermittent crashes for all flavours of 11.10 - i have had many of these myself on my desktop machine (which runs win7 very happily), and i've reverted to using 10.10 after trying different DE's, and a number of reinstalls of 11.10.
I should add though that 11.10 is 100% fine on my much less powerful netbook, right from installing the beta2 back at the beginning of October.

---

### Post by the-oggy on 2012-01-17
I also can't wait for next LTE to come out, i'm really impatient. Unity needs a little bit more time to mature. Till then, xfce4 remains my default desktop, btw I tried lxde, kde, gnome-shell, even cinnamon, but xfce4 rocks:D

Yeah, enjoy your couple months;) hopefully, with Precise everything will look a lot better:)

---

### Post by Hylas de Niall on 2012-01-17
> **the-oggy said:**
> I also can't wait for next LTE to come out, i'm really impatient. Unity needs a little bit more time to mature. Till then, xfce4 remains my default desktop, btw I tried lxde, kde, gnome-shell, even cinnamon, but xfce4 rocks:D

Yeah, enjoy your couple months;) hopefully, with Precise everything will look a lot better:)

Unity really does seem to be coming along nicely now, especially the ability to switch off 'apps available to install' in the lenses, and the proposed ability to disable the global menu.

Cheers for your input, and here's to 12.04! ;)

---

### Post by oxman on 2012-01-22
OK Please forgive. I don't want to read the entire thread. My Unity desktop keeps locking up. I loose mouse control and a hard reboot is required. Even Ctrl+Alt+Backspace doesn't work. Is there a short sweet solution? 11.10

---

### Post by lucky565 on 2012-01-22
I also have same problem.What can i do please somebody help me.
[Dr.Elena Kendall]("http://www.drelenakendall.net")

---

### Post by Hylas de Niall on 2012-02-07
I can only wonder if this apparently rather common issue might be related to Gnome 3 and/or the newer kernels.

My 10.10 is *still* running like greased lightening (and no crashes at all) on the same machine that was repeatedly crashing under 11.10.

---

### Post by Hylas de Niall on 2012-02-17
Okay - my last post on this (and again sorry to ccmill);

--Everything is STILL rock solid on my 10.10 (which will soon get dumped for 10.04.4 just released).

--I'm now convinced that the instability i've noticed on 11.10 is down to either the young Gnome 3 base or the recent 3.XX kernels.

It's a darn shame though, i'm actually rather fond of Unity and Gnome Shell

---

### Post by mjewell on 2012-05-09
My 64 bit Thinkpad running 12.04 is locking up and requiring a hard reboot. The windows open on the desktop drop their outer margin and can't be manipulated and then, soon after, the cursor freezes. It happens 

I've viewed output from dmesg and /var/log/syslog. I don't know which other log file might be helpful. 

I've tried ctrl-alt-fn+F1 to get a shell to monitor and kill different processes and then dropping back to my desktop with ctrl-alt-fn+F7, but no luck fixing problem yet.

---

