---
title: "I can't get my webcam to connect"
date: 2012-02-05
forum: General Help
---

### Post by DeloreanFanatic on 2012-02-05
Can you guys please help me?  I am using Ubuntu 11.10 on a Dell XPS M1710.  I am still pretty new to Ubuntu and this is really confusing me.  I am trying to use a Vimicro USB cam and when I plug it in nothing happens.

I did an ```
lsusb
``` and got this:
```
root@docbrown:/home/ian/spcaview-20071224# lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 413c:a005 Dell Computer Corp. Internal 2.0 Hub
Bus 002 Device 003: ID 0b97:7761 O2 Micro, Inc. Oz776 1.1 Hub
Bus 002 Device 004: ID 0b97:7762 O2 Micro, Inc. Oz776 SmartCard Reader
```

This looks normal as far as I can tell with my limited knowledge, but this is also not giving me a bus location for the web cam.

Also when I try ```
ls /dev/video
```

I get nothing because it says the file doesn't exist.

There are third party drivers I've been trying to work with and I've also run into a wall there, not sure if I'm allowed to post about that though so I wont yet.

Am I completely barking up the wrong tree?

Thanks in advance for any help offered!  I have had to overcome a lot to switch from windows, but Ubuntu is definitely the better way to go!

---

### Post by lechien73 on 2012-02-05
Strange that lsusb isn't showing it.

Could you try posting the output of:

```
dmesg
```

after you've plugged the camera in?

---

### Post by DeloreanFanatic on 2012-02-05
After typing in ```
dmesg
``` I got a long list of gibberish...I'm not even able to put the whole thing in here...

Here is all I am able to copy/past from terminal:

```
[    0.268195] pnp 00:03: [io  0xf400-0xf4fe]
[    0.268198] pnp 00:03: [io  0x0086]
[    0.268200] pnp 00:03: [io  0x00b3]
[    0.268202] pnp 00:03: [io  0x1006-0x1007]
[    0.268204] pnp 00:03: [io  0x100a-0x1059]
[    0.268207] pnp 00:03: [io  0x1060-0x107f]
[    0.268209] pnp 00:03: [io  0x1080-0x10bf]
[    0.268211] pnp 00:03: [io  0x10c0-0x10df]
[    0.268214] pnp 00:03: [io  0x1010-0x102f]
[    0.268216] pnp 00:03: [io  0x0809]
[    0.268234] pnp 00:03: disabling [io  0x1006-0x1007] because it overlaps 0000:00:1f.0 BAR 13 [io  0x1000-0x107f]
[    0.268238] pnp 00:03: disabling [io  0x100a-0x1059] because it overlaps 0000:00:1f.0 BAR 13 [io  0x1000-0x107f]
[    0.268241] pnp 00:03: disabling [io  0x1060-0x107f] because it overlaps 0000:00:1f.0 BAR 13 [io  0x1000-0x107f]
[    0.268245] pnp 00:03: disabling [io  0x1010-0x102f] because it overlaps 0000:00:1f.0 BAR 13 [io  0x1000-0x107f]
[    0.268288] system 00:03: [io  0xf400-0xf4fe] has been reserved
[    0.268292] system 00:03: [io  0x1080-0x10bf] has been reserved
[    0.268295] system 00:03: [io  0x10c0-0x10df] has been reserved
[    0.268298] system 00:03: [io  0x0809] has been reserved
[    0.268302] system 00:03: Plug and Play ACPI device, IDs PNP0c01 (active)
[    0.268334] pnp 00:04: [irq 12]
[    0.268366] pnp 00:04: Plug and Play ACPI device, IDs PNP0f13 (active)
[    0.268384] pnp 00:05: [io  0x0060]
[    0.268387] pnp 00:05: [io  0x0064]
[    0.268389] pnp 00:05: [io  0x0062]
[    0.268391] pnp 00:05: [io  0x0066]
[    0.268398] pnp 00:05: [irq 1]
[    0.268433] pnp 00:05: Plug and Play ACPI device, IDs PNP0303 (active)
[    0.268451] pnp 00:06: [io  0x0070-0x0071]
[    0.268457] pnp 00:06: [irq 8]
[    0.268459] pnp 00:06: [io  0x0072-0x0077]
[    0.268492] pnp 00:06: Plug and Play ACPI device, IDs PNP0b00 (active)
[    0.268512] pnp 00:07: [io  0x0061]
[    0.268515] pnp 00:07: [io  0x0063]
[    0.268520] pnp 00:07: [io  0x0065]
[    0.268522] pnp 00:07: [io  0x0067]
[    0.268555] pnp 00:07: Plug and Play ACPI device, IDs PNP0800 (active)
[    0.268573] pnp 00:08: [io  0x002e-0x002f]
[    0.268575] pnp 00:08: [io  0x0c80-0x0cff]
[    0.268578] pnp 00:08: [io  0x004e-0x004f]
[    0.268580] pnp 00:08: [io  0x0910-0x091f]
[    0.268583] pnp 00:08: [io  0x0920-0x092f]
[    0.268585] pnp 00:08: [io  0x0cb0-0x0cbf]
[    0.268587] pnp 00:08: [io  0x0930-0x097f]
[    0.268646] system 00:08: [io  0x0c80-0x0cff] could not be reserved
[    0.268649] system 00:08: [io  0x0910-0x091f] has been reserved
[    0.268652] system 00:08: [io  0x0920-0x092f] has been reserved
[    0.268656] system 00:08: [io  0x0cb0-0x0cbf] has been reserved
[    0.268659] system 00:08: [io  0x0930-0x097f] has been reserved
[    0.268663] system 00:08: Plug and Play ACPI device, IDs PNP0c01 (active)
[    0.268684] pnp 00:09: [dma 4]
[    0.268687] pnp 00:09: [io  0x0000-0x000f]
[    0.268689] pnp 00:09: [io  0x0080-0x0085]
[    0.268691] pnp 00:09: [io  0x0087-0x008f]
[    0.268694] pnp 00:09: [io  0x00c0-0x00df]
[    0.268696] pnp 00:09: [io  0x0010-0x001f]
[    0.268698] pnp 00:09: [io  0x0090-0x0091]
[    0.268701] pnp 00:09: [io  0x0093-0x009f]
[    0.268738] pnp 00:09: Plug and Play ACPI device, IDs PNP0200 (active)
[    0.268756] pnp 00:0a: [io  0x00f0-0x00ff]
[    0.268762] pnp 00:0a: [irq 13]
[    0.268800] pnp 00:0a: Plug and Play ACPI device, IDs PNP0c04 (active)
[    0.268852] pnp 00:0b: [mem 0xfed00000-0xfed003ff]
[    0.268911] system 00:0b: [mem 0xfed00000-0xfed003ff] has been reserved
[    0.268916] system 00:0b: Plug and Play ACPI device, IDs PNP0103 PNP0c01 (active)
[    0.271950] pnp: PnP ACPI: found 12 devices
[    0.271952] ACPI: ACPI bus type pnp unregistered
[    0.271956] PnPBIOS: Disabled by ACPI PNP
[    0.308385] PCI: max bus depth: 1 pci_try_num: 2
[    0.308462] pci 0000:00:1c.2: BAR 15: assigned [mem 0x80000000-0x801fffff 64bit pref]
[    0.308467] pci 0000:00:1c.2: BAR 13: assigned [io  0x2000-0x2fff]
[    0.308471] pci 0000:00:1c.1: BAR 15: assigned [mem 0x80200000-0x803fffff 64bit pref]
[    0.308475] pci 0000:00:1c.1: BAR 13: assigned [io  0x3000-0x3fff]
[    0.308479] pci 0000:00:1c.0: BAR 14: assigned [mem 0x80400000-0x805fffff]
[    0.308483] pci 0000:00:1c.0: BAR 15: assigned [mem 0x80600000-0x807fffff 64bit pref]
[    0.308487] pci 0000:00:1c.0: BAR 13: assigned [io  0x4000-0x4fff]
[    0.308491] pci 0000:00:01.0: PCI bridge to [bus 01-01]
[    0.308494] pci 0000:00:01.0:   bridge window [io  0xe000-0xefff]
[    0.308499] pci 0000:00:01.0:   bridge window [mem 0xed000000-0xefefffff]
[    0.308503] pci 0000:00:01.0:   bridge window [mem 0xd0000000-0xdfffffff 64bit pref]
[    0.308509] pci 0000:00:1c.0: PCI bridge to [bus 0b-0b]
[    0.308513] pci 0000:00:1c.0:   bridge window [io  0x4000-0x4fff]
[    0.308520] pci 0000:00:1c.0:   bridge window [mem 0x80400000-0x805fffff]
[    0.308526] pci 0000:00:1c.0:   bridge window [mem 0x80600000-0x807fffff 64bit pref]
[    0.308535] pci 0000:00:1c.1: PCI bridge to [bus 0c-0c]
[    0.308539] pci 0000:00:1c.1:   bridge window [io  0x3000-0x3fff]
[    0.308546] pci 0000:00:1c.1:   bridge window [mem 0xecf00000-0xecffffff]
[    0.308552] pci 0000:00:1c.1:   bridge window [mem 0x80200000-0x803fffff 64bit pref]
[    0.308561] pci 0000:00:1c.2: PCI bridge to [bus 09-09]
[    0.308565] pci 0000:00:1c.2:   bridge window [io  0x2000-0x2fff]
[    0.308572] pci 0000:00:1c.2:   bridge window [mem 0xece00000-0xecefffff]
[    0.308578] pci 0000:00:1c.2:   bridge window [mem 0x80000000-0x801fffff 64bit pref]
[    0.308586] pci 0000:00:1c.3: PCI bridge to [bus 0d-0e]
[    0.308590] pci 0000:00:1c.3:   bridge window [io  0xd000-0xdfff]
[    0.308597] pci 0000:00:1c.3:   bridge window [mem 0xecc00000-0xecdfffff]
[    0.308603] pci 0000:00:1c.3:   bridge window [mem 0xe0000000-0xe01fffff 64bit pref]
[    0.308612] pci 0000:00:1e.0: PCI bridge to [bus 03-03]
[    0.308614] pci 0000:00:1e.0:   bridge window [io  disabled]
[    0.308622] pci 0000:00:1e.0:   bridge window [mem 0xecb00000-0xecbfffff]
[    0.308627] pci 0000:00:1e.0:   bridge window [mem pref disabled]
[    0.308658] pci 0000:00:01.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.308663] pci 0000:00:01.0: setting latency timer to 64
[    0.308672] pci 0000:00:1c.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.308678] pci 0000:00:1c.0: setting latency timer to 64
[    0.308690] pci 0000:00:1c.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    0.308696] pci 0000:00:1c.1: setting latency timer to 64
[    0.308708] pci 0000:00:1c.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.308713] pci 0000:00:1c.2: setting latency timer to 64
[    0.308726] pci 0000:00:1c.3: PCI INT D -> GSI 19 (level, low) -> IRQ 19
[    0.308731] pci 0000:00:1c.3: setting latency timer to 64
[    0.308741] pci 0000:00:1e.0: setting latency timer to 64
[    0.308746] pci_bus 0000:00: resource 0 [io  0x0000-0xffff]
[    0.308749] pci_bus 0000:00: resource 1 [mem 0x00000000-0xffffffff]
[    0.308752] pci_bus 0000:01: resource 0 [io  0xe000-0xefff]
[    0.308755] pci_bus 0000:01: resource 1 [mem 0xed000000-0xefefffff]
[    0.308758] pci_bus 0000:01: resource 2 [mem 0xd0000000-0xdfffffff 64bit pref]
[    0.308761] pci_bus 0000:0b: resource 0 [io  0x4000-0x4fff]
[    0.308764] pci_bus 0000:0b: resource 1 [mem 0x80400000-0x805fffff]
[    0.308767] pci_bus 0000:0b: resource 2 [mem 0x80600000-0x807fffff 64bit pref]
[    0.308770] pci_bus 0000:0c: resource 0 [io  0x3000-0x3fff]
[    0.308773] pci_bus 0000:0c: resource 1 [mem 0xecf00000-0xecffffff]
[    0.308776] pci_bus 0000:0c: resource 2 [mem 0x80200000-0x803fffff 64bit pref]
[    0.308779] pci_bus 0000:09: resource 0 [io  0x2000-0x2fff]
[    0.308781] pci_bus 0000:09: resource 1 [mem 0xece00000-0xecefffff]
[    0.308784] pci_bus 0000:09: resource 2 [mem 0x80000000-0x801fffff 64bit pref]
[    0.308787] pci_bus 0000:0d: resource 0 [io  0xd000-0xdfff]
[    0.308790] pci_bus 0000:0d: resource 1 [mem 0xecc00000-0xecdfffff]
[    0.308793] pci_bus 0000:0d: resource 2 [mem 0xe0000000-0xe01fffff 64bit pref]
[    0.308797] pci_bus 0000:03: resource 1 [mem 0xecb00000-0xecbfffff]
[    0.308799] pci_bus 0000:03: resource 4 [io  0x0000-0xffff]
[    0.308802] pci_bus 0000:03: resource 5 [mem 0x00000000-0xffffffff]
[    0.308857] NET: Registered protocol family 2
[    0.308941] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.309224] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.309756] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.310037] TCP: Hash tables configured (established 131072 bind 65536)
[    0.310039] TCP reno registered
[    0.310043] UDP hash table entries: 512 (order: 2, 16384 bytes)
[    0.310053] UDP-Lite hash table entries: 512 (order: 2, 16384 bytes)
[    0.310151] NET: Registered protocol family 1
[    0.310321] pci 0000:01:00.0: Boot video device
[    0.310347] PCI: CLS 64 bytes, default 64
[    0.310355] Simple Boot Flag at 0x79 set to 0x1
[    0.310742] audit: initializing netlink socket (disabled)
[    0.310753] type=2000 audit(1328467856.304:1): initialized
[    0.337819] highmem bounce pool size: 64 pages
[    0.337826] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    0.347936] VFS: Disk quotas dquot_6.5.2
[    0.348041] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.348831] fuse init (API version 7.16)
[    0.348940] msgmni has been set to 1680
[    0.349318] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.349348] io scheduler noop registered
[    0.349351] io scheduler deadline registered
[    0.349366] io scheduler cfq registered (default)
[    0.349510] pcieport 0000:00:01.0: setting latency timer to 64
[    0.349553] pcieport 0000:00:01.0: irq 40 for MSI/MSI-X
[    0.349610] pcieport 0000:00:1c.0: setting latency timer to 64
[    0.349669] pcieport 0000:00:1c.0: irq 41 for MSI/MSI-X
[    0.349753] pcieport 0000:00:1c.1: setting latency timer to 64
[    0.349810] pcieport 0000:00:1c.1: irq 42 for MSI/MSI-X
[    0.349895] pcieport 0000:00:1c.2: setting latency timer to 64
[    0.349954] pcieport 0000:00:1c.2: irq 43 for MSI/MSI-X
[    0.350036] pcieport 0000:00:1c.3: setting latency timer to 64
[    0.350094] pcieport 0000:00:1c.3: irq 44 for MSI/MSI-X
[    0.350204] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.350232] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.350300] intel_idle: MWAIT substates: 0x22220
[    0.350302] intel_idle: does not run on family 6 model 15
[    0.350750] ACPI: Deprecated procfs I/F for AC is loaded, please retry with CONFIG_ACPI_PROCFS_POWER cleared
[    0.351102] ACPI: AC Adapter [AC] (on-line)
[    0.351193] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input0
[    0.351597] ACPI: Lid Switch [LID]
[    0.351644] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1
[    0.351649] ACPI: Power Button [PBTN]
[    0.351694] input: Sleep Button as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input2
[    0.351698] ACPI: Sleep Button [SBTN]
[    0.351744] ACPI: acpi_idle registered with cpuidle
[    0.361491] thermal LNXTHERM:00: registered as thermal_zone0
[    0.361494] ACPI: Thermal Zone [THM] (57 C)
[    0.361516] ACPI: Deprecated procfs I/F for battery is loaded, please retry with CONFIG_ACPI_PROCFS_POWER cleared
[    0.361549] ERST: Table is not found!
[    0.361615] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    0.361959] isapnp: Scanning for PnP cards...
[    0.400342] ACPI: Battery Slot [BAT0] (battery present)
[    0.532473] Freeing initrd memory: 13328k freed
[    0.720532] isapnp: No Plug & Play device found
[    0.729691] Linux agpgart interface v0.103
[    0.731351] brd: module loaded
[    0.732058] loop: module loaded
[    0.732231] ata_piix 0000:00:1f.2: version 2.13
[    0.732250] ata_piix 0000:00:1f.2: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    0.732258] ata_piix 0000:00:1f.2: MAP [ P0 P2 IDE IDE ]
[    0.732307] ata_piix 0000:00:1f.2: setting latency timer to 64
[    0.732680] scsi0 : ata_piix
[    0.732793] scsi1 : ata_piix
[    0.733307] ata1: SATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xbfa0 irq 14
[    0.733310] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xbfa8 irq 15
[    0.733748] Fixed MDIO Bus: probed
[    0.733780] PPP generic driver version 2.4.2
[    0.733824] tun: Universal TUN/TAP device driver, 1.6
[    0.733826] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.733918] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.733946] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    0.733959] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    0.733963] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    0.734005] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 1
[    0.734027] ehci_hcd 0000:00:1d.7: using broken periodic workaround
[    0.734040] ehci_hcd 0000:00:1d.7: debug port 1
[    0.737939] ehci_hcd 0000:00:1d.7: cache line size of 64 is not supported
[    0.737957] ehci_hcd 0000:00:1d.7: irq 20, io mem 0xffa80000
[    0.752020] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    0.752160] hub 1-0:1.0: USB hub found
[    0.752165] hub 1-0:1.0: 8 ports detected
[    0.752263] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.752282] uhci_hcd: USB Universal Host Controller Interface driver
[    0.752305] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    0.752313] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    0.752317] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    0.752360] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    0.752391] uhci_hcd 0000:00:1d.0: irq 20, io base 0x0000bf80
[    0.752529] hub 2-0:1.0: USB hub found
[    0.752533] hub 2-0:1.0: 2 ports detected
[    0.752613] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[    0.752620] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    0.752624] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    0.752662] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 3
[    0.752704] uhci_hcd 0000:00:1d.1: irq 21, io base 0x0000bf60
[    0.752839] hub 3-0:1.0: USB hub found
[    0.752843] hub 3-0:1.0: 2 ports detected
[    0.752927] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 22 (level, low) -> IRQ 22
[    0.752935] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    0.752939] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    0.752976] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 4
[    0.753020] uhci_hcd 0000:00:1d.2: irq 22, io base 0x0000bf40
[    0.753155] hub 4-0:1.0: USB hub found
[    0.753159] hub 4-0:1.0: 2 ports detected
[    0.753241] uhci_hcd 0000:00:1d.3: PCI INT D -> GSI 23 (level, low) -> IRQ 23
[    0.753249] uhci_hcd 0000:00:1d.3: setting latency timer to 64
[    0.753253] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[    0.753290] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 5
[    0.753329] uhci_hcd 0000:00:1d.3: irq 23, io base 0x0000bf20
[    0.753467] hub 5-0:1.0: USB hub found
[    0.753472] hub 5-0:1.0: 2 ports detected
[    0.753611] i8042: PNP: PS/2 Controller [PNP0303:KBC,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    0.756438] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.756446] serio: i8042 AUX port at 0x60,0x64 irq 12
[    0.756583] mousedev: PS/2 mouse device common for all mice
[    0.756753] rtc_cmos 00:06: RTC can wake from S4
[    0.756877] rtc_cmos 00:06: rtc core: registered rtc_cmos as rtc0
[    0.756921] rtc0: alarms up to one month, y3k, 114 bytes nvram, hpet irqs
[    0.757018] device-mapper: uevent: version 1.0.3
[    0.757103] device-mapper: ioctl: 4.20.0-ioctl (2011-02-02) initialised: dm-devel@redhat.com
[    0.757139] EISA: Probing bus 0 at eisa.0
[    0.757202] EISA: Mainboard ^O_FFFF detected.
[    0.757222] Cannot allocate resource for EISA slot 1
[    0.757224] Cannot allocate resource for EISA slot 2
[    0.757227] Cannot allocate resource for EISA slot 3
[    0.757229] Cannot allocate resource for EISA slot 4
[    0.757247] EISA: Detected 0 cards.
[    0.757259] cpufreq-nforce2: No nForce2 chipset.
[    0.757335] cpuidle: using governor ladder
[    0.757450] cpuidle: using governor menu
[    0.757452] EFI Variables Facility v0.08 2004-May-17
[    0.757810] TCP cubic registered
[    0.757970] NET: Registered protocol family 10
[    0.758672] NET: Registered protocol family 17
[    0.758693] Registering the dns_resolver key type
[    0.758714] Using IPI No-Shortcut mode
[    0.758814] PM: Hibernation image not present or could not be loaded.
[    0.758827] registered taskstats version 1
[    0.764553] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input3
[    0.771834]   Magic number: 0:48:847
[    0.771945] rtc_cmos 00:06: setting system clock to 2012-02-05 18:50:57 UTC (1328467857)
[    0.772710] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.772712] EDD information not available.
[    0.896652] ata1.00: ATA-7: ST980825AS, 8.04, max UDMA/133
[    0.896659] ata1.00: 156301488 sectors, multi 8: LBA48 NCQ (depth 0/32)
[    0.912571] ata2.00: ATAPI: TSSTcorpCD-RW/DVD-ROM TSL462D, DE01, max UDMA/33
[    0.912939] ata1.00: configured for UDMA/133
[    0.913210] scsi 0:0:0:0: Direct-Access     ATA      ST980825AS       8.04 PQ: 0 ANSI: 5
[    0.913397] sd 0:0:0:0: [sda] 156301488 512-byte logical blocks: (80.0 GB/74.5 GiB)
[    0.913416] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    0.913457] sd 0:0:0:0: [sda] Write Protect is off
[    0.913461] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    0.913506] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    0.944322] ata2.00: configured for UDMA/33
[    0.945818] scsi 1:0:0:0: CD-ROM            TSSTcorp CDRW/DVD TSL462D DE01 PQ: 0 ANSI: 5
[    0.947383] sr0: scsi3-mmc drive: 24x/24x writer cd/rw xa/form2 cdda tray
[    0.947387] cdrom: Uniform CD-ROM driver Revision: 3.20
[    0.947491] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    0.947552] sr 1:0:0:0: Attached scsi generic sg1 type 5
[    0.949541]  sda: sda1 sda2 < sda5 >
[    0.949958] sd 0:0:0:0: [sda] Attached SCSI disk
[    0.950029] Freeing unused kernel memory: 696k freed
[    0.950290] Write protecting the kernel text: 5340k
[    0.950349] Write protecting the kernel read-only data: 2192k
[    0.968777] udevd[85]: starting version 173
[    1.030707] tg3.c:v3.119 (May 18, 2011)
[    1.030729] tg3 0000:09:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    1.030741] tg3 0000:09:00.0: setting latency timer to 64
[    1.040796] sdhci: Secure Digital Host Controller Interface driver
[    1.040800] sdhci: Copyright(c) Pierre Ossman
[    1.046811] sdhci-pci 0000:03:01.1: SDHCI controller found [1180:0822] (rev 19)
[    1.046833] sdhci-pci 0000:03:01.1: PCI INT B -> GSI 18 (level, low) -> IRQ 18
[    1.047882] mmc0: no vmmc regulator found
[    1.054844] Registered led device: mmc0::
[    1.055886] mmc0: SDHCI controller on PCI [0000:03:01.1] using DMA
[    1.065923] tg3 0000:09:00.0: eth0: Tigon3 [partno(BCM5752KFBG) rev 6002] (PCI Express) MAC address 00:18:8b:b9:76:79
[    1.065928] tg3 0000:09:00.0: eth0: attached PHY is 5752 (10/100/1000Base-T Ethernet) (WireSpeed[1], EEE[0])
[    1.065932] tg3 0000:09:00.0: eth0: RXcsums[1] LinkChgREG[0] MIirq[0] ASF[0] TSOcap[1]
[    1.065936] tg3 0000:09:00.0: eth0: dma_rwctrl[76180000] dma_mask[64-bit]
[    1.069032] firewire_ohci 0000:03:01.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    1.132098] firewire_ohci: Added fw-ohci device 0000:03:01.0, OHCI v1.10, 4 IR + 4 IT contexts, quirks 0x1
[    1.325736] EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: (null)
[    1.384122] usb 2-1: new full speed USB device number 2 using uhci_hcd
[    1.534508] hub 2-1:1.0: USB hub found
[    1.536472] hub 2-1:1.0: 4 ports detected
[    1.632108] firewire_core: created device fw0: GUID 434fc0003825c561, S400
[    1.833486] usb 2-1.2: new full speed USB device number 3 using uhci_hcd
[    1.963524] hub 2-1.2:1.0: USB hub found
[    1.965488] hub 2-1.2:1.0: 3 ports detected
[    2.245502] usb 2-1.2.2: new full speed USB device number 4 using uhci_hcd
[   17.874360] udevd[299]: starting version 173
[   17.925447] lp: driver loaded but no devices found
[   17.947693] cfg80211: Calling CRDA to update world regulatory domain
[   17.981384] Adding 2094076k swap on /dev/sda5.  Priority:-1 extents:1 across:2094076k 
[   17.988952] wmi: Mapper loaded
[   18.009918] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
[   18.033707] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, in-tree:s
[   18.033711] iwl3945: Copyright(c) 2003-2011 Intel Corporation
[   18.033782] iwl3945 0000:0c:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   18.033798] iwl3945 0000:0c:00.0: setting latency timer to 64
[   18.121771] iwl3945 0000:0c:00.0: Tunable channels: 11 802.11bg, 13 802.11a channels
[   18.121776] iwl3945 0000:0c:00.0: Detected Intel Wireless WiFi Link 3945ABG
[   18.121929] iwl3945 0000:0c:00.0: irq 45 for MSI/MSI-X
[   18.160940] Registered led device: phy0-led
[   18.161009] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain 
[   18.161475] intel_rng: FWH not detected
[   18.180579] leds_ss4200: no LED devices found
[   18.208164] ieee80211 phy0: Selected rate control algorithm 'iwl-3945-rs'
[   18.210992] r592 0000:03:01.2: PCI INT B -> GSI 18 (level, low) -> IRQ 18
[   18.211003] r592 0000:03:01.2: setting latency timer to 64
[   18.219188] nvidia: module license 'NVIDIA' taints kernel.
[   18.219193] Disabling lock debugging due to kernel taint
[   18.251058] r592: driver successfully loaded
[   18.251943] r852 0000:03:01.3: PCI INT B -> GSI 18 (level, low) -> IRQ 18
[   18.251953] r852 0000:03:01.3: setting latency timer to 64
[   18.259440] type=1400 audit(1328467874.981:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=529 comm="apparmor_parser"
[   18.259893] type=1400 audit(1328467874.981:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=529 comm="apparmor_parser"
[   18.260205] type=1400 audit(1328467874.985:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=529 comm="apparmor_parser"
[   18.267245] r852: Non dma capable device detected, dma disabled
[   18.267264] r852: driver loaded successfully
[   18.404091] dcdbas dcdbas: Dell Systems Management Base Driver (version 5.6.0-3.2)
[   18.408183] acpi device:2e: registered as cooling_device2
[   18.408598] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A03:00/device:2b/LNXVIDEO:00/input/input4
[   18.408694] ACPI: Video Device [VID] (multi-head: yes  rom: no  post: no)
[   18.560407] input: Dell WMI hotkeys as /devices/virtual/input/input5
[   18.570914] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain 
[   18.570919] cfg80211: World regulatory domain updated:
[   18.570921] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   18.570925] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   18.570928] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   18.570931] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   18.570934] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   18.570937] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   18.586281] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[   18.586349] HDA Intel 0000:00:1b.0: irq 46 for MSI/MSI-X
[   18.586383] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   18.764248] nvidia 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   18.764258] nvidia 0000:01:00.0: setting latency timer to 64
[   18.764265] vgaarb: device changed decodes: PCI:0000:01:00.0,olddecodes=io+mem,decodes=none:owns=io+mem
[   18.764969] NVRM: loading NVIDIA UNIX x86 Kernel Module  173.14.30  Thu Apr 14 08:47:14 PDT 2011
[   18.842565] init: failsafe main process (742) killed by TERM signal
[   18.844814] input: HDA Intel Mic at Ext Right Jack as /devices/pci0000:00/0000:00:1b.0/sound/card0/input6
[   18.844998] input: HDA Intel HP Out at Ext Right Jack as /devices/pci0000:00/0000:00:1b.0/sound/card0/input7
[   18.903135] type=1400 audit(1328467875.625:5): apparmor="STATUS" operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" pid=801 comm="apparmor_parser"
[   18.903148] type=1400 audit(1328467875.625:6): apparmor="STATUS" operation="profile_load" name="/usr/lib/lightdm/lightdm-guest-session-wrapper" pid=802 comm="apparmor_parser"
[   18.910321] type=1400 audit(1328467875.633:7): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=804 comm="apparmor_parser"
[   18.922488] type=1400 audit(1328467875.645:8): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=804 comm="apparmor_parser"
[   18.922788] type=1400 audit(1328467875.645:9): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=804 comm="apparmor_parser"
[   18.927057] type=1400 audit(1328467875.649:10): apparmor="STATUS" operation="profile_load" name="/usr/lib/telepathy/mission-control-5" pid=811 comm="apparmor_parser"
[   18.927736] type=1400 audit(1328467875.649:11): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince" pid=805 comm="apparmor_parser"
[   19.113146] init: apport pre-start process (857) terminated with status 1
[   19.129447] init: apport post-stop process (887) terminated with status 1
[   19.150386] vesafb: mode is 1280x1024x32, linelength=5120, pages=0
[   19.150390] vesafb: scrolling: redraw
[   19.150393] vesafb: Truecolor: size=8:8:8:8, shift=24:16:8:0
[   19.151959] vesafb: framebuffer at 0xd0000000, mapped to 0xf9a80000, using 5120k, total 5120k
[   19.158269] fbcon: VESA VGA (fb0) is primary device
[   19.158395] Console: switching to colour frame buffer device 160x64
[   19.158434] fb0: VESA VGA frame buffer device
[   19.192049] ppdev: user-space parallel port driver
[   19.218650] init: gdm main process (922) killed by TERM signal
[   19.323852] iwl3945 0000:0c:00.0: loaded firmware version 15.32.2.9
[   19.397145] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   19.424559] tg3 0000:09:00.0: irq 47 for MSI/MSI-X
[   19.457253] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   19.472979] Synaptics Touchpad, model: 1, fw: 6.2, id: 0xfa0b1, caps: 0xa04713/0x200000/0x0
[   19.477964] Bluetooth: Core ver 2.16
[   19.477990] NET: Registered protocol family 31
[   19.477992] Bluetooth: HCI device and connection manager initialized
[   19.477995] Bluetooth: HCI socket layer initialized
[   19.477998] Bluetooth: L2CAP socket layer initialized
[   19.478117] Bluetooth: SCO socket layer initialized
[   19.483932] Bluetooth: RFCOMM TTY layer initialized
[   19.483938] Bluetooth: RFCOMM socket layer initialized
[   19.483940] Bluetooth: RFCOMM ver 1.11
[   19.486284] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   19.486287] Bluetooth: BNEP filters: protocol multicast
[   19.507518] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input8
[   20.098158] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,commit=0
[   21.100034] iwl3945 0000:0c:00.0: Error sending REPLY_RXON: time out after 500ms.
[   21.100040] iwl3945 0000:0c:00.0: Error setting new configuration (-110).
[   21.724030] iwl3945 0000:0c:00.0: Error sending REPLY_RXON: time out after 500ms.
[   21.724034] iwl3945 0000:0c:00.0: Error setting new configuration (-110).
[   22.061856] cfg80211: Found new beacon on frequency: 5180 MHz (Ch 36) on phy0
[   23.613455] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,commit=0
[   39.354715] wlan0: authenticate with 00:24:b2:75:53:77 (try 1)
[   39.356499] wlan0: authenticated
[   39.356628] wlan0: associate with 00:24:b2:75:53:77 (try 1)
[   39.359000] wlan0: RX AssocResp from 00:24:b2:75:53:77 (capab=0x411 status=0 aid=9)
[   39.359007] wlan0: associated
[   39.360502] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   50.104027] wlan0: no IPv6 routers present
```

The top is cut off I guess...terminal won't scroll up to where I actually typed the command...idk why not...

Thanks so much for taking the time to help with my problem...it seems not many people want to help a noob.

---

### Post by lechien73 on 2012-02-05
Thanks for the output from dmesg...did you run it directly after plugging in the camera? I'm just trying to find any reference to it in the file, and don't seem to be able to; however this camera does seem to have been problematic with different versions of Ubuntu.

I'm happy to help - as is everyone here. If you don't get a response quickly, then it's usually because people just don't know what to do to help you, but it is a great community & everyone wants to help out new users :)

---

### Post by DeloreanFanatic on 2012-02-06
I did, but for argument's sake I tried it again directly after starting my computer.

This is what I got:
```
[    0.264325] pnp 00:04: Plug and Play ACPI device, IDs PNP0f13 (active)
[    0.264343] pnp 00:05: [io  0x0060]
[    0.264346] pnp 00:05: [io  0x0064]
[    0.264348] pnp 00:05: [io  0x0062]
[    0.264350] pnp 00:05: [io  0x0066]
[    0.264356] pnp 00:05: [irq 1]
[    0.264392] pnp 00:05: Plug and Play ACPI device, IDs PNP0303 (active)
[    0.264410] pnp 00:06: [io  0x0070-0x0071]
[    0.264416] pnp 00:06: [irq 8]
[    0.264418] pnp 00:06: [io  0x0072-0x0077]
[    0.264451] pnp 00:06: Plug and Play ACPI device, IDs PNP0b00 (active)
[    0.264471] pnp 00:07: [io  0x0061]
[    0.264473] pnp 00:07: [io  0x0063]
[    0.264478] pnp 00:07: [io  0x0065]
[    0.264480] pnp 00:07: [io  0x0067]
[    0.264513] pnp 00:07: Plug and Play ACPI device, IDs PNP0800 (active)
[    0.264531] pnp 00:08: [io  0x002e-0x002f]
[    0.264533] pnp 00:08: [io  0x0c80-0x0cff]
[    0.264536] pnp 00:08: [io  0x004e-0x004f]
[    0.264538] pnp 00:08: [io  0x0910-0x091f]
[    0.264541] pnp 00:08: [io  0x0920-0x092f]
[    0.264543] pnp 00:08: [io  0x0cb0-0x0cbf]
[    0.264545] pnp 00:08: [io  0x0930-0x097f]
[    0.264603] system 00:08: [io  0x0c80-0x0cff] could not be reserved
[    0.264607] system 00:08: [io  0x0910-0x091f] has been reserved
[    0.264610] system 00:08: [io  0x0920-0x092f] has been reserved
[    0.264613] system 00:08: [io  0x0cb0-0x0cbf] has been reserved
[    0.264616] system 00:08: [io  0x0930-0x097f] has been reserved
[    0.264620] system 00:08: Plug and Play ACPI device, IDs PNP0c01 (active)
[    0.264642] pnp 00:09: [dma 4]
[    0.264644] pnp 00:09: [io  0x0000-0x000f]
[    0.264647] pnp 00:09: [io  0x0080-0x0085]
[    0.264649] pnp 00:09: [io  0x0087-0x008f]
[    0.264651] pnp 00:09: [io  0x00c0-0x00df]
[    0.264653] pnp 00:09: [io  0x0010-0x001f]
[    0.264656] pnp 00:09: [io  0x0090-0x0091]
[    0.264658] pnp 00:09: [io  0x0093-0x009f]
[    0.264696] pnp 00:09: Plug and Play ACPI device, IDs PNP0200 (active)
[    0.264713] pnp 00:0a: [io  0x00f0-0x00ff]
[    0.264720] pnp 00:0a: [irq 13]
[    0.264758] pnp 00:0a: Plug and Play ACPI device, IDs PNP0c04 (active)
[    0.264810] pnp 00:0b: [mem 0xfed00000-0xfed003ff]
[    0.264870] system 00:0b: [mem 0xfed00000-0xfed003ff] has been reserved
[    0.264874] system 00:0b: Plug and Play ACPI device, IDs PNP0103 PNP0c01 (active)
[    0.267985] pnp: PnP ACPI: found 12 devices
[    0.267988] ACPI: ACPI bus type pnp unregistered
[    0.267992] PnPBIOS: Disabled by ACPI PNP
[    0.304427] PCI: max bus depth: 1 pci_try_num: 2
[    0.304509] pci 0000:00:1c.2: BAR 15: assigned [mem 0x80000000-0x801fffff 64bit pref]
[    0.304514] pci 0000:00:1c.2: BAR 13: assigned [io  0x2000-0x2fff]
[    0.304518] pci 0000:00:1c.1: BAR 15: assigned [mem 0x80200000-0x803fffff 64bit pref]
[    0.304522] pci 0000:00:1c.1: BAR 13: assigned [io  0x3000-0x3fff]
[    0.304526] pci 0000:00:1c.0: BAR 14: assigned [mem 0x80400000-0x805fffff]
[    0.304530] pci 0000:00:1c.0: BAR 15: assigned [mem 0x80600000-0x807fffff 64bit pref]
[    0.304534] pci 0000:00:1c.0: BAR 13: assigned [io  0x4000-0x4fff]
[    0.304538] pci 0000:00:01.0: PCI bridge to [bus 01-01]
[    0.304541] pci 0000:00:01.0:   bridge window [io  0xe000-0xefff]
[    0.304546] pci 0000:00:01.0:   bridge window [mem 0xed000000-0xefefffff]
[    0.304551] pci 0000:00:01.0:   bridge window [mem 0xd0000000-0xdfffffff 64bit pref]
[    0.304556] pci 0000:00:1c.0: PCI bridge to [bus 0b-0b]
[    0.304560] pci 0000:00:1c.0:   bridge window [io  0x4000-0x4fff]
[    0.304567] pci 0000:00:1c.0:   bridge window [mem 0x80400000-0x805fffff]
[    0.304573] pci 0000:00:1c.0:   bridge window [mem 0x80600000-0x807fffff 64bit pref]
[    0.304582] pci 0000:00:1c.1: PCI bridge to [bus 0c-0c]
[    0.304586] pci 0000:00:1c.1:   bridge window [io  0x3000-0x3fff]
[    0.304594] pci 0000:00:1c.1:   bridge window [mem 0xecf00000-0xecffffff]
[    0.304599] pci 0000:00:1c.1:   bridge window [mem 0x80200000-0x803fffff 64bit pref]
[    0.304608] pci 0000:00:1c.2: PCI bridge to [bus 09-09]
[    0.304612] pci 0000:00:1c.2:   bridge window [io  0x2000-0x2fff]
[    0.304619] pci 0000:00:1c.2:   bridge window [mem 0xece00000-0xecefffff]
[    0.304625] pci 0000:00:1c.2:   bridge window [mem 0x80000000-0x801fffff 64bit pref]
[    0.304634] pci 0000:00:1c.3: PCI bridge to [bus 0d-0e]
[    0.304638] pci 0000:00:1c.3:   bridge window [io  0xd000-0xdfff]
[    0.304645] pci 0000:00:1c.3:   bridge window [mem 0xecc00000-0xecdfffff]
[    0.304651] pci 0000:00:1c.3:   bridge window [mem 0xe0000000-0xe01fffff 64bit pref]
[    0.304660] pci 0000:00:1e.0: PCI bridge to [bus 03-03]
[    0.304662] pci 0000:00:1e.0:   bridge window [io  disabled]
[    0.304670] pci 0000:00:1e.0:   bridge window [mem 0xecb00000-0xecbfffff]
[    0.304675] pci 0000:00:1e.0:   bridge window [mem pref disabled]
[    0.304707] pci 0000:00:01.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.304713] pci 0000:00:01.0: setting latency timer to 64
[    0.304721] pci 0000:00:1c.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.304727] pci 0000:00:1c.0: setting latency timer to 64
[    0.304740] pci 0000:00:1c.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    0.304745] pci 0000:00:1c.1: setting latency timer to 64
[    0.304758] pci 0000:00:1c.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.304763] pci 0000:00:1c.2: setting latency timer to 64
[    0.304775] pci 0000:00:1c.3: PCI INT D -> GSI 19 (level, low) -> IRQ 19
[    0.304781] pci 0000:00:1c.3: setting latency timer to 64
[    0.304791] pci 0000:00:1e.0: setting latency timer to 64
[    0.304796] pci_bus 0000:00: resource 0 [io  0x0000-0xffff]
[    0.304799] pci_bus 0000:00: resource 1 [mem 0x00000000-0xffffffff]
[    0.304802] pci_bus 0000:01: resource 0 [io  0xe000-0xefff]
[    0.304804] pci_bus 0000:01: resource 1 [mem 0xed000000-0xefefffff]
[    0.304807] pci_bus 0000:01: resource 2 [mem 0xd0000000-0xdfffffff 64bit pref]
[    0.304810] pci_bus 0000:0b: resource 0 [io  0x4000-0x4fff]
[    0.304813] pci_bus 0000:0b: resource 1 [mem 0x80400000-0x805fffff]
[    0.304816] pci_bus 0000:0b: resource 2 [mem 0x80600000-0x807fffff 64bit pref]
[    0.304819] pci_bus 0000:0c: resource 0 [io  0x3000-0x3fff]
[    0.304822] pci_bus 0000:0c: resource 1 [mem 0xecf00000-0xecffffff]
[    0.304825] pci_bus 0000:0c: resource 2 [mem 0x80200000-0x803fffff 64bit pref]
[    0.304828] pci_bus 0000:09: resource 0 [io  0x2000-0x2fff]
[    0.304831] pci_bus 0000:09: resource 1 [mem 0xece00000-0xecefffff]
[    0.304834] pci_bus 0000:09: resource 2 [mem 0x80000000-0x801fffff 64bit pref]
[    0.304837] pci_bus 0000:0d: resource 0 [io  0xd000-0xdfff]
[    0.304840] pci_bus 0000:0d: resource 1 [mem 0xecc00000-0xecdfffff]
[    0.304843] pci_bus 0000:0d: resource 2 [mem 0xe0000000-0xe01fffff 64bit pref]
[    0.304846] pci_bus 0000:03: resource 1 [mem 0xecb00000-0xecbfffff]
[    0.304849] pci_bus 0000:03: resource 4 [io  0x0000-0xffff]
[    0.304851] pci_bus 0000:03: resource 5 [mem 0x00000000-0xffffffff]
[    0.304904] NET: Registered protocol family 2
[    0.304986] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.305271] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.305799] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.306074] TCP: Hash tables configured (established 131072 bind 65536)
[    0.306076] TCP reno registered
[    0.306080] UDP hash table entries: 512 (order: 2, 16384 bytes)
[    0.306090] UDP-Lite hash table entries: 512 (order: 2, 16384 bytes)
[    0.306186] NET: Registered protocol family 1
[    0.306356] pci 0000:01:00.0: Boot video device
[    0.306382] PCI: CLS 64 bytes, default 64
[    0.306390] Simple Boot Flag at 0x79 set to 0x1
[    0.306780] audit: initializing netlink socket (disabled)
[    0.306791] type=2000 audit(1328511905.300:1): initialized
[    0.333893] highmem bounce pool size: 64 pages
[    0.333899] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    0.344029] VFS: Disk quotas dquot_6.5.2
[    0.344112] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.344902] fuse init (API version 7.16)
[    0.345012] msgmni has been set to 1680
[    0.345391] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.345421] io scheduler noop registered
[    0.345424] io scheduler deadline registered
[    0.345439] io scheduler cfq registered (default)
[    0.345580] pcieport 0000:00:01.0: setting latency timer to 64
[    0.345623] pcieport 0000:00:01.0: irq 40 for MSI/MSI-X
[    0.345680] pcieport 0000:00:1c.0: setting latency timer to 64
[    0.345739] pcieport 0000:00:1c.0: irq 41 for MSI/MSI-X
[    0.345823] pcieport 0000:00:1c.1: setting latency timer to 64
[    0.345881] pcieport 0000:00:1c.1: irq 42 for MSI/MSI-X
[    0.345966] pcieport 0000:00:1c.2: setting latency timer to 64
[    0.346025] pcieport 0000:00:1c.2: irq 43 for MSI/MSI-X
[    0.346108] pcieport 0000:00:1c.3: setting latency timer to 64
[    0.346166] pcieport 0000:00:1c.3: irq 44 for MSI/MSI-X
[    0.346277] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.346305] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.346372] intel_idle: MWAIT substates: 0x22220
[    0.346374] intel_idle: does not run on family 6 model 15
[    0.346804] ACPI: Deprecated procfs I/F for AC is loaded, please retry with CONFIG_ACPI_PROCFS_POWER cleared
[    0.347165] ACPI: AC Adapter [AC] (on-line)
[    0.347256] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input0
[    0.347612] ACPI: Lid Switch [LID]
[    0.347659] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1
[    0.347665] ACPI: Power Button [PBTN]
[    0.347709] input: Sleep Button as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input2
[    0.347713] ACPI: Sleep Button [SBTN]
[    0.347760] ACPI: acpi_idle registered with cpuidle
[    0.357428] thermal LNXTHERM:00: registered as thermal_zone0
[    0.357432] ACPI: Thermal Zone [THM] (25 C)
[    0.357453] ACPI: Deprecated procfs I/F for battery is loaded, please retry with CONFIG_ACPI_PROCFS_POWER cleared
[    0.357485] ERST: Table is not found!
[    0.357552] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    0.357949] isapnp: Scanning for PnP cards...
[    0.396092] ACPI: Battery Slot [BAT0] (battery present)
[    0.530035] Freeing initrd memory: 13328k freed
[    0.715819] isapnp: No Plug & Play device found
[    0.740589] Linux agpgart interface v0.103
[    0.742250] brd: module loaded
[    0.742939] loop: module loaded
[    0.743110] ata_piix 0000:00:1f.2: version 2.13
[    0.743129] ata_piix 0000:00:1f.2: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    0.743137] ata_piix 0000:00:1f.2: MAP [ P0 P2 IDE IDE ]
[    0.743186] ata_piix 0000:00:1f.2: setting latency timer to 64
[    0.743568] scsi0 : ata_piix
[    0.743682] scsi1 : ata_piix
[    0.744225] ata1: SATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xbfa0 irq 14
[    0.744229] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xbfa8 irq 15
[    0.744669] Fixed MDIO Bus: probed
[    0.744701] PPP generic driver version 2.4.2
[    0.744744] tun: Universal TUN/TAP device driver, 1.6
[    0.744746] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.744837] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.744864] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    0.744877] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    0.744882] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    0.744925] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 1
[    0.744947] ehci_hcd 0000:00:1d.7: using broken periodic workaround
[    0.744961] ehci_hcd 0000:00:1d.7: debug port 1
[    0.748846] ehci_hcd 0000:00:1d.7: cache line size of 64 is not supported
[    0.748864] ehci_hcd 0000:00:1d.7: irq 20, io mem 0xffa80000
[    0.764019] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    0.764158] hub 1-0:1.0: USB hub found
[    0.764164] hub 1-0:1.0: 8 ports detected
[    0.764260] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.764277] uhci_hcd: USB Universal Host Controller Interface driver
[    0.764300] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    0.764307] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    0.764311] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    0.764357] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    0.764388] uhci_hcd 0000:00:1d.0: irq 20, io base 0x0000bf80
[    0.764523] hub 2-0:1.0: USB hub found
[    0.764528] hub 2-0:1.0: 2 ports detected
[    0.764611] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[    0.764618] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    0.764622] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    0.764661] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 3
[    0.764701] uhci_hcd 0000:00:1d.1: irq 21, io base 0x0000bf60
[    0.764839] hub 3-0:1.0: USB hub found
[    0.764844] hub 3-0:1.0: 2 ports detected
[    0.764925] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 22 (level, low) -> IRQ 22
[    0.764933] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    0.764937] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    0.764974] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 4
[    0.765017] uhci_hcd 0000:00:1d.2: irq 22, io base 0x0000bf40
[    0.765153] hub 4-0:1.0: USB hub found
[    0.765158] hub 4-0:1.0: 2 ports detected
[    0.765236] uhci_hcd 0000:00:1d.3: PCI INT D -> GSI 23 (level, low) -> IRQ 23
[    0.765244] uhci_hcd 0000:00:1d.3: setting latency timer to 64
[    0.765247] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[    0.765285] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 5
[    0.765325] uhci_hcd 0000:00:1d.3: irq 23, io base 0x0000bf20
[    0.765462] hub 5-0:1.0: USB hub found
[    0.765466] hub 5-0:1.0: 2 ports detected
[    0.765612] i8042: PNP: PS/2 Controller [PNP0303:KBC,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    0.768484] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.768492] serio: i8042 AUX port at 0x60,0x64 irq 12
[    0.768618] mousedev: PS/2 mouse device common for all mice
[    0.768803] rtc_cmos 00:06: RTC can wake from S4
[    0.768925] rtc_cmos 00:06: rtc core: registered rtc_cmos as rtc0
[    0.768964] rtc0: alarms up to one month, y3k, 114 bytes nvram, hpet irqs
[    0.769061] device-mapper: uevent: version 1.0.3
[    0.769152] device-mapper: ioctl: 4.20.0-ioctl (2011-02-02) initialised: dm-devel@redhat.com
[    0.769188] EISA: Probing bus 0 at eisa.0
[    0.769251] EISA: Mainboard ^O_FFFF detected.
[    0.769271] Cannot allocate resource for EISA slot 1
[    0.769273] Cannot allocate resource for EISA slot 2
[    0.769275] Cannot allocate resource for EISA slot 3
[    0.769278] Cannot allocate resource for EISA slot 4
[    0.769296] EISA: Detected 0 cards.
[    0.769308] cpufreq-nforce2: No nForce2 chipset.
[    0.769383] cpuidle: using governor ladder
[    0.769499] cpuidle: using governor menu
[    0.769502] EFI Variables Facility v0.08 2004-May-17
[    0.769852] TCP cubic registered
[    0.770008] NET: Registered protocol family 10
[    0.770747] NET: Registered protocol family 17
[    0.770766] Registering the dns_resolver key type
[    0.770790] Using IPI No-Shortcut mode
[    0.770889] PM: Hibernation image not present or could not be loaded.
[    0.770903] registered taskstats version 1
[    0.775997] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input3
[    0.784063]   Magic number: 0:677:65
[    0.784108] pci 0000:00:1e.0: hash matches
[    0.784177] rtc_cmos 00:06: setting system clock to 2012-02-06 07:05:06 UTC (1328511906)
[    0.784927] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.784929] EDD information not available.
[    0.908638] ata1.00: ATA-7: ST980825AS, 8.04, max UDMA/133
[    0.908646] ata1.00: 156301488 sectors, multi 8: LBA48 NCQ (depth 0/32)
[    0.924573] ata2.00: ATAPI: TSSTcorpCD-RW/DVD-ROM TSL462D, DE01, max UDMA/33
[    0.924938] ata1.00: configured for UDMA/133
[    0.925208] scsi 0:0:0:0: Direct-Access     ATA      ST980825AS       8.04 PQ: 0 ANSI: 5
[    0.925421] sd 0:0:0:0: [sda] 156301488 512-byte logical blocks: (80.0 GB/74.5 GiB)
[    0.925443] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    0.925482] sd 0:0:0:0: [sda] Write Protect is off
[    0.925485] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    0.925530] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    0.956322] ata2.00: configured for UDMA/33
[    0.957814] scsi 1:0:0:0: CD-ROM            TSSTcorp CDRW/DVD TSL462D DE01 PQ: 0 ANSI: 5
[    0.959380] sr0: scsi3-mmc drive: 24x/24x writer cd/rw xa/form2 cdda tray
[    0.959383] cdrom: Uniform CD-ROM driver Revision: 3.20
[    0.959495] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    0.959549] sr 1:0:0:0: Attached scsi generic sg1 type 5
[    0.963723]  sda: sda1 sda2 < sda5 >
[    0.964157] sd 0:0:0:0: [sda] Attached SCSI disk
[    0.964212] Freeing unused kernel memory: 696k freed
[    0.964466] Write protecting the kernel text: 5340k
[    0.964526] Write protecting the kernel read-only data: 2192k
[    0.982902] udevd[85]: starting version 173
[    1.047148] tg3.c:v3.119 (May 18, 2011)
[    1.047169] tg3 0000:09:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    1.047181] tg3 0000:09:00.0: setting latency timer to 64
[    1.082461] tg3 0000:09:00.0: eth0: Tigon3 [partno(BCM5752KFBG) rev 6002] (PCI Express) MAC address 00:18:8b:b9:76:79
[    1.082466] tg3 0000:09:00.0: eth0: attached PHY is 5752 (10/100/1000Base-T Ethernet) (WireSpeed[1], EEE[0])
[    1.082470] tg3 0000:09:00.0: eth0: RXcsums[1] LinkChgREG[0] MIirq[0] ASF[0] TSOcap[1]
[    1.082474] tg3 0000:09:00.0: eth0: dma_rwctrl[76180000] dma_mask[64-bit]
[    1.095050] sdhci: Secure Digital Host Controller Interface driver
[    1.095053] sdhci: Copyright(c) Pierre Ossman
[    1.098059] sdhci-pci 0000:03:01.1: SDHCI controller found [1180:0822] (rev 19)
[    1.098079] sdhci-pci 0000:03:01.1: PCI INT B -> GSI 18 (level, low) -> IRQ 18
[    1.099126] mmc0: no vmmc regulator found
[    1.106701] Registered led device: mmc0::
[    1.110810] mmc0: SDHCI controller on PCI [0000:03:01.1] using DMA
[    1.110913] firewire_ohci 0000:03:01.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    1.172185] firewire_ohci: Added fw-ohci device 0000:03:01.0, OHCI v1.10, 4 IR + 4 IT contexts, quirks 0x1
[    1.192069] usb 1-6: new high speed USB device number 3 using ehci_hcd
[    1.337790] usbcore: registered new interface driver uas
[    1.339687] Initializing USB Mass Storage driver...
[    1.339781] scsi2 : usb-storage 1-6:1.0
[    1.340093] usbcore: registered new interface driver usb-storage
[    1.340096] USB Mass Storage support registered.
[    1.356551] EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: (null)
[    1.568079] usb 2-1: new full speed USB device number 2 using uhci_hcd
[    1.672152] firewire_core: created device fw0: GUID 434fc0003825c561, S400
[    1.718514] hub 2-1:1.0: USB hub found
[    1.720486] hub 2-1:1.0: 4 ports detected
[    2.017498] usb 2-1.2: new full speed USB device number 3 using uhci_hcd
[    2.147537] hub 2-1.2:1.0: USB hub found
[    2.149510] hub 2-1.2:1.0: 3 ports detected
[    2.340762] scsi 2:0:0:0: Direct-Access     SanDisk  Cruzer           1.02 PQ: 0 ANSI: 2
[    2.420234] sd 2:0:0:0: Attached scsi generic sg2 type 0
[    2.420880] sd 2:0:0:0: [sdb] 7813120 512-byte logical blocks: (4.00 GB/3.72 GiB)
[    2.421635] sd 2:0:0:0: [sdb] Write Protect is off
[    2.421642] sd 2:0:0:0: [sdb] Mode Sense: 03 00 00 00
[    2.422518] sd 2:0:0:0: [sdb] No Caching mode page present
[    2.422523] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[    2.425732] sd 2:0:0:0: [sdb] No Caching mode page present
[    2.425735] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[    2.429842]  sdb:
[    2.432381] sd 2:0:0:0: [sdb] No Caching mode page present
[    2.432387] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[    2.432393] sd 2:0:0:0: [sdb] Attached SCSI removable disk
[    2.441502] usb 2-1.2.2: new full speed USB device number 4 using uhci_hcd
[   17.854539] udevd[304]: starting version 173
[   17.902293] lp: driver loaded but no devices found
[   17.966745] nvidia: module license 'NVIDIA' taints kernel.
[   17.966750] Disabling lock debugging due to kernel taint
[   17.970215] Adding 2094076k swap on /dev/sda5.  Priority:-1 extents:1 across:2094076k 
[   17.980130] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
[   17.990863] wmi: Mapper loaded
[   18.016795] type=1400 audit(1328511923.731:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=417 comm="apparmor_parser"
[   18.017263] type=1400 audit(1328511923.731:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=417 comm="apparmor_parser"
[   18.017939] type=1400 audit(1328511923.731:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=417 comm="apparmor_parser"
[   18.115585] acpi device:2e: registered as cooling_device2
[   18.116051] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A03:00/device:2b/LNXVIDEO:00/input/input4
[   18.116153] ACPI: Video Device [VID] (multi-head: yes  rom: no  post: no)
[   18.117969] cfg80211: Calling CRDA to update world regulatory domain
[   18.142794] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, in-tree:s
[   18.142798] iwl3945: Copyright(c) 2003-2011 Intel Corporation
[   18.142873] iwl3945 0000:0c:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   18.142889] iwl3945 0000:0c:00.0: setting latency timer to 64
[   18.196454] intel_rng: FWH not detected
[   18.196566] iwl3945 0000:0c:00.0: Tunable channels: 11 802.11bg, 13 802.11a channels
[   18.196570] iwl3945 0000:0c:00.0: Detected Intel Wireless WiFi Link 3945ABG
[   18.196724] iwl3945 0000:0c:00.0: irq 45 for MSI/MSI-X
[   18.336549] Registered led device: phy0-led
[   18.336627] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain 
[   18.338870] r852 0000:03:01.3: PCI INT B -> GSI 18 (level, low) -> IRQ 18
[   18.338880] r852 0000:03:01.3: setting latency timer to 64
[   18.361502] ieee80211 phy0: Selected rate control algorithm 'iwl-3945-rs'
[   18.370649] dcdbas dcdbas: Dell Systems Management Base Driver (version 5.6.0-3.2)
[   18.444254] r852: Non dma capable device detected, dma disabled
[   18.444278] r852: driver loaded successfully
[   18.444740] r592 0000:03:01.2: PCI INT B -> GSI 18 (level, low) -> IRQ 18
[   18.444750] r592 0000:03:01.2: setting latency timer to 64
[   18.450603] r592: driver successfully loaded
[   18.820989] leds_ss4200: no LED devices found
[   18.855746] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[   18.855813] HDA Intel 0000:00:1b.0: irq 46 for MSI/MSI-X
[   18.855847] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   19.015620] Synaptics Touchpad, model: 1, fw: 6.2, id: 0xfa0b1, caps: 0xa04713/0x200000/0x0
[   19.040198] init: failsafe main process (713) killed by TERM signal
[   19.052329] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input5
[   19.096660] nvidia 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   19.096669] nvidia 0000:01:00.0: setting latency timer to 64
[   19.096675] vgaarb: device changed decodes: PCI:0000:01:00.0,olddecodes=io+mem,decodes=none:owns=io+mem
[   19.099012] NVRM: loading NVIDIA UNIX x86 Kernel Module  173.14.30  Thu Apr 14 08:47:14 PDT 2011
[   19.113194] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain 
[   19.113199] cfg80211: World regulatory domain updated:
[   19.113201] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   19.113205] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   19.113208] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   19.113211] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   19.113214] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   19.113217] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   19.131025] input: HDA Intel Mic at Ext Right Jack as /devices/pci0000:00/0000:00:1b.0/sound/card0/input6
[   19.131866] input: HDA Intel HP Out at Ext Right Jack as /devices/pci0000:00/0000:00:1b.0/sound/card0/input7
[   19.140430] input: Dell WMI hotkeys as /devices/virtual/input/input8
[   19.146947] type=1400 audit(1328511924.859:5): apparmor="STATUS" operation="profile_load" name="/usr/lib/lightdm/lightdm-guest-session-wrapper" pid=794 comm="apparmor_parser"
[   19.151892] type=1400 audit(1328511924.863:6): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=800 comm="apparmor_parser"
[   19.152470] type=1400 audit(1328511924.867:7): apparmor="STATUS" operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" pid=793 comm="apparmor_parser"
[   19.154125] type=1400 audit(1328511924.867:8): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=800 comm="apparmor_parser"
[   19.154425] type=1400 audit(1328511924.867:9): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=800 comm="apparmor_parser"
[   19.161287] type=1400 audit(1328511924.875:10): apparmor="STATUS" operation="profile_load" name="/usr/lib/telepathy/mission-control-5" pid=807 comm="apparmor_parser"
[   19.165927] type=1400 audit(1328511924.879:11): apparmor="STATUS" operation="profile_load" name="/usr/lib/telepathy/telepathy-*" pid=807 comm="apparmor_parser"
[   19.524834] init: apport pre-start process (860) terminated with status 1
[   19.541186] init: apport post-stop process (900) terminated with status 1
[   19.745493] iwl3945 0000:0c:00.0: loaded firmware version 15.32.2.9
[   19.819298] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   19.845860] Bluetooth: Core ver 2.16
[   19.846326] NET: Registered protocol family 31
[   19.846329] Bluetooth: HCI device and connection manager initialized
[   19.846332] Bluetooth: HCI socket layer initialized
[   19.846334] Bluetooth: L2CAP socket layer initialized
[   19.846353] tg3 0000:09:00.0: irq 47 for MSI/MSI-X
[   19.849294] Bluetooth: SCO socket layer initialized
[   19.851873] Bluetooth: RFCOMM TTY layer initialized
[   19.851878] Bluetooth: RFCOMM socket layer initialized
[   19.851880] Bluetooth: RFCOMM ver 1.11
[   19.878463] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   19.878467] Bluetooth: BNEP filters: protocol multicast
[   19.892309] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   20.284470] vesafb: mode is 1280x1024x32, linelength=5120, pages=0
[   20.284473] vesafb: scrolling: redraw
[   20.284476] vesafb: Truecolor: size=8:8:8:8, shift=24:16:8:0
[   20.286023] vesafb: framebuffer at 0xd0000000, mapped to 0xf9b00000, using 5120k, total 5120k
[   20.286376] Console: switching to colour frame buffer device 160x64
[   20.286414] fb0: VESA VGA frame buffer device
[   20.319830] init: gdm main process (1062) killed by TERM signal
[   20.398176] ppdev: user-space parallel port driver
[   21.496527] cfg80211: Found new beacon on frequency: 5180 MHz (Ch 36) on phy0
[   22.648031] iwl3945 0000:0c:00.0: Error sending REPLY_RXON: time out after 500ms.
[   22.648037] iwl3945 0000:0c:00.0: Error setting new configuration (-110).
[   23.272028] iwl3945 0000:0c:00.0: Error sending REPLY_RXON: time out after 500ms.
[   23.272032] iwl3945 0000:0c:00.0: Error setting new configuration (-110).
[   31.456878] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,commit=0
[   31.577544] init: plymouth-stop pre-start process (1320) terminated with status 1
[   54.130345] wlan0: authenticate with 00:24:b2:75:53:77 (try 1)
[   54.132155] wlan0: authenticated
[   54.132450] wlan0: associate with 00:24:b2:75:53:77 (try 1)
[   54.134828] wlan0: RX AssocResp from 00:24:b2:75:53:77 (capab=0x411 status=0 aid=8)
[   54.134832] wlan0: associated
[   54.136470] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   64.400122] wlan0: no IPv6 routers present
[  121.592429] usb 1-6: USB disconnect, device number 3

```

I'm wondering if the last line has anything to do with it?

Also, if it helps, the cam did come with drivers on a disk, but they are executables.  I was able to install the drivers through wine AFTER copying them off of the disk (it wouldn't do it directly from the disk) and they didn't seem to do anything after installation anyway.

I apologize for thinking no one wanted to help, its just a personality trait of mine when I feel like the answer to a problem is right in front of me and I still can't find it (Ubuntu is still doing this to me alot :D)

---

### Post by lechien73 on 2012-02-06
Have you tested this camera with another computer, and in a different USB port? What's odd is that I don't really see any evidence of the kernel trying to locate a driver or encountering an error when the device is plugged in.

The only thing I do see is that the first USB bus is using a patch to fix a kernel bug. This is "usb 1-6", which is the same bus that reports the "disconnect device number 3" message at the end.

---

### Post by Mosome on 2012-02-06
Maybe trying a different USB port may help.  If your computer has a crossover usb bridge, it may not be working correctly with the system.  Try back ports on desktops or the other side of laptops.

---

### Post by DeloreanFanatic on 2012-02-06
I used to use this cam on this same laptop when I was still running windows and it was running fine then...

I keep a crappy tower to run the few windows programs I still need, however I haven't been able to get that computer to associate the installed drivers with the cam...whenever I try to use the cam in the simple capture program that came on the driver disk it says "no capture device found" and I cant seem to get the computer to recognize the cam as a USB device...havent been able to fix that as of yet...

Anyway, I have plugged the cam into all 6 USB ports that this laptop has, and done a dmesg after each time.  As far as I can tell, there is no change but just in case here is everything I could get from terminal after that (I'm pretty sure a large portion of it is missing again, don't know why terminal doesn't keep everything I've done in the current session):

```
[    0.258036] pnp 00:00: [mem 0x00000000-0x0009fbff]
[    0.258040] pnp 00:00: [mem 0x0009fc00-0x0009ffff]
[    0.258042] pnp 00:00: [mem 0x000c0000-0x000cffff]
[    0.258045] pnp 00:00: [mem 0x000e0000-0x000fffff]
[    0.258047] pnp 00:00: [mem 0x00100000-0x7fed9bff]
[    0.258050] pnp 00:00: [mem 0x7fed9c00-0x7fefffff]
[    0.258052] pnp 00:00: [mem 0x7ff00000-0x7fffffff]
[    0.258055] pnp 00:00: [mem 0xffb00000-0xffffffff]
[    0.258057] pnp 00:00: [mem 0xfec00000-0xfec0ffff]
[    0.258060] pnp 00:00: [mem 0xfee00000-0xfee0ffff]
[    0.258062] pnp 00:00: [mem 0xfed20000-0xfed9ffff]
[    0.258065] pnp 00:00: [mem 0xffa80000-0xffa83fff]
[    0.258067] pnp 00:00: [mem 0xf4000000-0xf4003fff]
[    0.258069] pnp 00:00: [mem 0xf4004000-0xf4004fff]
[    0.258072] pnp 00:00: [mem 0xf4005000-0xf4005fff]
[    0.258074] pnp 00:00: [mem 0xf4006000-0xf4006fff]
[    0.258077] pnp 00:00: [mem 0xf4008000-0xf400bfff]
[    0.258079] pnp 00:00: [mem 0xf0000000-0xf3ffffff]
[    0.258169] system 00:00: [mem 0x00000000-0x0009fbff] could not be reserved
[    0.258173] system 00:00: [mem 0x0009fc00-0x0009ffff] could not be reserved
[    0.258176] system 00:00: [mem 0x000c0000-0x000cffff] could not be reserved
[    0.258180] system 00:00: [mem 0x000e0000-0x000fffff] could not be reserved
[    0.258183] system 00:00: [mem 0x00100000-0x7fed9bff] could not be reserved
[    0.258187] system 00:00: [mem 0x7fed9c00-0x7fefffff] has been reserved
[    0.258190] system 00:00: [mem 0x7ff00000-0x7fffffff] has been reserved
[    0.258193] system 00:00: [mem 0xffb00000-0xffffffff] has been reserved
[    0.258197] system 00:00: [mem 0xfec00000-0xfec0ffff] could not be reserved
[    0.258200] system 00:00: [mem 0xfee00000-0xfee0ffff] has been reserved
[    0.258203] system 00:00: [mem 0xfed20000-0xfed9ffff] has been reserved
[    0.258206] system 00:00: [mem 0xffa80000-0xffa83fff] could not be reserved
[    0.258210] system 00:00: [mem 0xf4000000-0xf4003fff] has been reserved
[    0.258213] system 00:00: [mem 0xf4004000-0xf4004fff] has been reserved
[    0.258216] system 00:00: [mem 0xf4005000-0xf4005fff] has been reserved
[    0.258220] system 00:00: [mem 0xf4006000-0xf4006fff] has been reserved
[    0.258223] system 00:00: [mem 0xf4008000-0xf400bfff] has been reserved
[    0.258226] system 00:00: [mem 0xf0000000-0xf3ffffff] has been reserved
[    0.258231] system 00:00: Plug and Play ACPI device, IDs PNP0c01 (active)
[    0.263877] pnp 00:01: [bus 00-ff]
[    0.263881] pnp 00:01: [io  0x0000-0x0cf7 window]
[    0.263883] pnp 00:01: [io  0x0cf8-0x0cff]
[    0.263886] pnp 00:01: [io  0x0d00-0xffff window]
[    0.263889] pnp 00:01: [mem 0x000a0000-0x000bffff window]
[    0.263892] pnp 00:01: [mem 0x000d0000-0x000dffff window]
[    0.263894] pnp 00:01: [mem 0x80000000-0xefffffff window]
[    0.263897] pnp 00:01: [mem 0xf4007000-0xf4007fff window]
[    0.263900] pnp 00:01: [mem 0xf400c000-0xfebfffff window]
[    0.263903] pnp 00:01: [mem 0xfec10000-0xfecfffff window]
[    0.263905] pnp 00:01: [mem 0xfed00400-0xfed1ffff window]
[    0.263908] pnp 00:01: [mem 0xfeda0000-0xfed9ffff window disabled]
[    0.263911] pnp 00:01: [mem 0xfee10000-0xffafffff window]
[    0.264021] pnp 00:01: Plug and Play ACPI device, IDs PNP0a03 (active)
[    0.264043] pnp 00:02: [io  0x0092]
[    0.264045] pnp 00:02: [io  0x00b2]
[    0.264048] pnp 00:02: [io  0x0020-0x0021]
[    0.264050] pnp 00:02: [io  0x00a0-0x00a1]
[    0.264053] pnp 00:02: [irq 0 disabled]
[    0.264055] pnp 00:02: [io  0x04d0-0x04d1]
[    0.264058] pnp 00:02: [io  0x1000-0x1005]
[    0.264060] pnp 00:02: [io  0x1008-0x100f]
[    0.264080] pnp 00:02: disabling [io  0x1000-0x1005] because it overlaps 0000:00:1f.0 BAR 13 [io  0x1000-0x107f]
[    0.264084] pnp 00:02: disabling [io  0x1008-0x100f] because it overlaps 0000:00:1f.0 BAR 13 [io  0x1000-0x107f]
[    0.264128] system 00:02: [io  0x04d0-0x04d1] has been reserved
[    0.264132] system 00:02: Plug and Play ACPI device, IDs PNP0c01 (active)
[    0.264152] pnp 00:03: [io  0xf400-0xf4fe]
[    0.264154] pnp 00:03: [io  0x0086]
[    0.264157] pnp 00:03: [io  0x00b3]
[    0.264159] pnp 00:03: [io  0x1006-0x1007]
[    0.264161] pnp 00:03: [io  0x100a-0x1059]
[    0.264164] pnp 00:03: [io  0x1060-0x107f]
[    0.264166] pnp 00:03: [io  0x1080-0x10bf]
[    0.264168] pnp 00:03: [io  0x10c0-0x10df]
[    0.264170] pnp 00:03: [io  0x1010-0x102f]
[    0.264173] pnp 00:03: [io  0x0809]
[    0.264191] pnp 00:03: disabling [io  0x1006-0x1007] because it overlaps 0000:00:1f.0 BAR 13 [io  0x1000-0x107f]
[    0.264195] pnp 00:03: disabling [io  0x100a-0x1059] because it overlaps 0000:00:1f.0 BAR 13 [io  0x1000-0x107f]
[    0.264199] pnp 00:03: disabling [io  0x1060-0x107f] because it overlaps 0000:00:1f.0 BAR 13 [io  0x1000-0x107f]
[    0.264203] pnp 00:03: disabling [io  0x1010-0x102f] because it overlaps 0000:00:1f.0 BAR 13 [io  0x1000-0x107f]
[    0.264246] system 00:03: [io  0xf400-0xf4fe] has been reserved
[    0.264250] system 00:03: [io  0x1080-0x10bf] has been reserved
[    0.264253] system 00:03: [io  0x10c0-0x10df] has been reserved
[    0.264256] system 00:03: [io  0x0809] has been reserved
[    0.264260] system 00:03: Plug and Play ACPI device, IDs PNP0c01 (active)
[    0.264292] pnp 00:04: [irq 12]
[    0.264325] pnp 00:04: Plug and Play ACPI device, IDs PNP0f13 (active)
[    0.264343] pnp 00:05: [io  0x0060]
[    0.264346] pnp 00:05: [io  0x0064]
[    0.264348] pnp 00:05: [io  0x0062]
[    0.264350] pnp 00:05: [io  0x0066]
[    0.264356] pnp 00:05: [irq 1]
[    0.264392] pnp 00:05: Plug and Play ACPI device, IDs PNP0303 (active)
[    0.264410] pnp 00:06: [io  0x0070-0x0071]
[    0.264416] pnp 00:06: [irq 8]
[    0.264418] pnp 00:06: [io  0x0072-0x0077]
[    0.264451] pnp 00:06: Plug and Play ACPI device, IDs PNP0b00 (active)
[    0.264471] pnp 00:07: [io  0x0061]
[    0.264473] pnp 00:07: [io  0x0063]
[    0.264478] pnp 00:07: [io  0x0065]
[    0.264480] pnp 00:07: [io  0x0067]
[    0.264513] pnp 00:07: Plug and Play ACPI device, IDs PNP0800 (active)
[    0.264531] pnp 00:08: [io  0x002e-0x002f]
[    0.264533] pnp 00:08: [io  0x0c80-0x0cff]
[    0.264536] pnp 00:08: [io  0x004e-0x004f]
[    0.264538] pnp 00:08: [io  0x0910-0x091f]
[    0.264541] pnp 00:08: [io  0x0920-0x092f]
[    0.264543] pnp 00:08: [io  0x0cb0-0x0cbf]
[    0.264545] pnp 00:08: [io  0x0930-0x097f]
[    0.264603] system 00:08: [io  0x0c80-0x0cff] could not be reserved
[    0.264607] system 00:08: [io  0x0910-0x091f] has been reserved
[    0.264610] system 00:08: [io  0x0920-0x092f] has been reserved
[    0.264613] system 00:08: [io  0x0cb0-0x0cbf] has been reserved
[    0.264616] system 00:08: [io  0x0930-0x097f] has been reserved
[    0.264620] system 00:08: Plug and Play ACPI device, IDs PNP0c01 (active)
[    0.264642] pnp 00:09: [dma 4]
[    0.264644] pnp 00:09: [io  0x0000-0x000f]
[    0.264647] pnp 00:09: [io  0x0080-0x0085]
[    0.264649] pnp 00:09: [io  0x0087-0x008f]
[    0.264651] pnp 00:09: [io  0x00c0-0x00df]
[    0.264653] pnp 00:09: [io  0x0010-0x001f]
[    0.264656] pnp 00:09: [io  0x0090-0x0091]
[    0.264658] pnp 00:09: [io  0x0093-0x009f]
[    0.264696] pnp 00:09: Plug and Play ACPI device, IDs PNP0200 (active)
[    0.264713] pnp 00:0a: [io  0x00f0-0x00ff]
[    0.264720] pnp 00:0a: [irq 13]
[    0.264758] pnp 00:0a: Plug and Play ACPI device, IDs PNP0c04 (active)
[    0.264810] pnp 00:0b: [mem 0xfed00000-0xfed003ff]
[    0.264870] system 00:0b: [mem 0xfed00000-0xfed003ff] has been reserved
[    0.264874] system 00:0b: Plug and Play ACPI device, IDs PNP0103 PNP0c01 (active)
[    0.267985] pnp: PnP ACPI: found 12 devices
[    0.267988] ACPI: ACPI bus type pnp unregistered
[    0.267992] PnPBIOS: Disabled by ACPI PNP
[    0.304427] PCI: max bus depth: 1 pci_try_num: 2
[    0.304509] pci 0000:00:1c.2: BAR 15: assigned [mem 0x80000000-0x801fffff 64bit pref]
[    0.304514] pci 0000:00:1c.2: BAR 13: assigned [io  0x2000-0x2fff]
[    0.304518] pci 0000:00:1c.1: BAR 15: assigned [mem 0x80200000-0x803fffff 64bit pref]
[    0.304522] pci 0000:00:1c.1: BAR 13: assigned [io  0x3000-0x3fff]
[    0.304526] pci 0000:00:1c.0: BAR 14: assigned [mem 0x80400000-0x805fffff]
[    0.304530] pci 0000:00:1c.0: BAR 15: assigned [mem 0x80600000-0x807fffff 64bit pref]
[    0.304534] pci 0000:00:1c.0: BAR 13: assigned [io  0x4000-0x4fff]
[    0.304538] pci 0000:00:01.0: PCI bridge to [bus 01-01]
[    0.304541] pci 0000:00:01.0:   bridge window [io  0xe000-0xefff]
[    0.304546] pci 0000:00:01.0:   bridge window [mem 0xed000000-0xefefffff]
[    0.304551] pci 0000:00:01.0:   bridge window [mem 0xd0000000-0xdfffffff 64bit pref]
[    0.304556] pci 0000:00:1c.0: PCI bridge to [bus 0b-0b]
[    0.304560] pci 0000:00:1c.0:   bridge window [io  0x4000-0x4fff]
[    0.304567] pci 0000:00:1c.0:   bridge window [mem 0x80400000-0x805fffff]
[    0.304573] pci 0000:00:1c.0:   bridge window [mem 0x80600000-0x807fffff 64bit pref]
[    0.304582] pci 0000:00:1c.1: PCI bridge to [bus 0c-0c]
[    0.304586] pci 0000:00:1c.1:   bridge window [io  0x3000-0x3fff]
[    0.304594] pci 0000:00:1c.1:   bridge window [mem 0xecf00000-0xecffffff]
[    0.304599] pci 0000:00:1c.1:   bridge window [mem 0x80200000-0x803fffff 64bit pref]
[    0.304608] pci 0000:00:1c.2: PCI bridge to [bus 09-09]
[    0.304612] pci 0000:00:1c.2:   bridge window [io  0x2000-0x2fff]
[    0.304619] pci 0000:00:1c.2:   bridge window [mem 0xece00000-0xecefffff]
[    0.304625] pci 0000:00:1c.2:   bridge window [mem 0x80000000-0x801fffff 64bit pref]
[    0.304634] pci 0000:00:1c.3: PCI bridge to [bus 0d-0e]
[    0.304638] pci 0000:00:1c.3:   bridge window [io  0xd000-0xdfff]
[    0.304645] pci 0000:00:1c.3:   bridge window [mem 0xecc00000-0xecdfffff]
[    0.304651] pci 0000:00:1c.3:   bridge window [mem 0xe0000000-0xe01fffff 64bit pref]
[    0.304660] pci 0000:00:1e.0: PCI bridge to [bus 03-03]
[    0.304662] pci 0000:00:1e.0:   bridge window [io  disabled]
[    0.304670] pci 0000:00:1e.0:   bridge window [mem 0xecb00000-0xecbfffff]
[    0.304675] pci 0000:00:1e.0:   bridge window [mem pref disabled]
[    0.304707] pci 0000:00:01.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.304713] pci 0000:00:01.0: setting latency timer to 64
[    0.304721] pci 0000:00:1c.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.304727] pci 0000:00:1c.0: setting latency timer to 64
[    0.304740] pci 0000:00:1c.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    0.304745] pci 0000:00:1c.1: setting latency timer to 64
[    0.304758] pci 0000:00:1c.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.304763] pci 0000:00:1c.2: setting latency timer to 64
[    0.304775] pci 0000:00:1c.3: PCI INT D -> GSI 19 (level, low) -> IRQ 19
[    0.304781] pci 0000:00:1c.3: setting latency timer to 64
[    0.304791] pci 0000:00:1e.0: setting latency timer to 64
[    0.304796] pci_bus 0000:00: resource 0 [io  0x0000-0xffff]
[    0.304799] pci_bus 0000:00: resource 1 [mem 0x00000000-0xffffffff]
[    0.304802] pci_bus 0000:01: resource 0 [io  0xe000-0xefff]
[    0.304804] pci_bus 0000:01: resource 1 [mem 0xed000000-0xefefffff]
[    0.304807] pci_bus 0000:01: resource 2 [mem 0xd0000000-0xdfffffff 64bit pref]
[    0.304810] pci_bus 0000:0b: resource 0 [io  0x4000-0x4fff]
[    0.304813] pci_bus 0000:0b: resource 1 [mem 0x80400000-0x805fffff]
[    0.304816] pci_bus 0000:0b: resource 2 [mem 0x80600000-0x807fffff 64bit pref]
[    0.304819] pci_bus 0000:0c: resource 0 [io  0x3000-0x3fff]
[    0.304822] pci_bus 0000:0c: resource 1 [mem 0xecf00000-0xecffffff]
[    0.304825] pci_bus 0000:0c: resource 2 [mem 0x80200000-0x803fffff 64bit pref]
[    0.304828] pci_bus 0000:09: resource 0 [io  0x2000-0x2fff]
[    0.304831] pci_bus 0000:09: resource 1 [mem 0xece00000-0xecefffff]
[    0.304834] pci_bus 0000:09: resource 2 [mem 0x80000000-0x801fffff 64bit pref]
[    0.304837] pci_bus 0000:0d: resource 0 [io  0xd000-0xdfff]
[    0.304840] pci_bus 0000:0d: resource 1 [mem 0xecc00000-0xecdfffff]
[    0.304843] pci_bus 0000:0d: resource 2 [mem 0xe0000000-0xe01fffff 64bit pref]
[    0.304846] pci_bus 0000:03: resource 1 [mem 0xecb00000-0xecbfffff]
[    0.304849] pci_bus 0000:03: resource 4 [io  0x0000-0xffff]
[    0.304851] pci_bus 0000:03: resource 5 [mem 0x00000000-0xffffffff]
[    0.304904] NET: Registered protocol family 2
[    0.304986] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.305271] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.305799] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.306074] TCP: Hash tables configured (established 131072 bind 65536)
[    0.306076] TCP reno registered
[    0.306080] UDP hash table entries: 512 (order: 2, 16384 bytes)
[    0.306090] UDP-Lite hash table entries: 512 (order: 2, 16384 bytes)
[    0.306186] NET: Registered protocol family 1
[    0.306356] pci 0000:01:00.0: Boot video device
[    0.306382] PCI: CLS 64 bytes, default 64
[    0.306390] Simple Boot Flag at 0x79 set to 0x1
[    0.306780] audit: initializing netlink socket (disabled)
[    0.306791] type=2000 audit(1328511905.300:1): initialized
[    0.333893] highmem bounce pool size: 64 pages
[    0.333899] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    0.344029] VFS: Disk quotas dquot_6.5.2
[    0.344112] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.344902] fuse init (API version 7.16)
[    0.345012] msgmni has been set to 1680
[    0.345391] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.345421] io scheduler noop registered
[    0.345424] io scheduler deadline registered
[    0.345439] io scheduler cfq registered (default)
[    0.345580] pcieport 0000:00:01.0: setting latency timer to 64
[    0.345623] pcieport 0000:00:01.0: irq 40 for MSI/MSI-X
[    0.345680] pcieport 0000:00:1c.0: setting latency timer to 64
[    0.345739] pcieport 0000:00:1c.0: irq 41 for MSI/MSI-X
[    0.345823] pcieport 0000:00:1c.1: setting latency timer to 64
[    0.345881] pcieport 0000:00:1c.1: irq 42 for MSI/MSI-X
[    0.345966] pcieport 0000:00:1c.2: setting latency timer to 64
[    0.346025] pcieport 0000:00:1c.2: irq 43 for MSI/MSI-X
[    0.346108] pcieport 0000:00:1c.3: setting latency timer to 64
[    0.346166] pcieport 0000:00:1c.3: irq 44 for MSI/MSI-X
[    0.346277] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.346305] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.346372] intel_idle: MWAIT substates: 0x22220
[    0.346374] intel_idle: does not run on family 6 model 15
[    0.346804] ACPI: Deprecated procfs I/F for AC is loaded, please retry with CONFIG_ACPI_PROCFS_POWER cleared
[    0.347165] ACPI: AC Adapter [AC] (on-line)
[    0.347256] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input0
[    0.347612] ACPI: Lid Switch [LID]
[    0.347659] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1
[    0.347665] ACPI: Power Button [PBTN]
[    0.347709] input: Sleep Button as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input2
[    0.347713] ACPI: Sleep Button [SBTN]
[    0.347760] ACPI: acpi_idle registered with cpuidle
[    0.357428] thermal LNXTHERM:00: registered as thermal_zone0
[    0.357432] ACPI: Thermal Zone [THM] (25 C)
[    0.357453] ACPI: Deprecated procfs I/F for battery is loaded, please retry with CONFIG_ACPI_PROCFS_POWER cleared
[    0.357485] ERST: Table is not found!
[    0.357552] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    0.357949] isapnp: Scanning for PnP cards...
[    0.396092] ACPI: Battery Slot [BAT0] (battery present)
[    0.530035] Freeing initrd memory: 13328k freed
[    0.715819] isapnp: No Plug & Play device found
[    0.740589] Linux agpgart interface v0.103
[    0.742250] brd: module loaded
[    0.742939] loop: module loaded
[    0.743110] ata_piix 0000:00:1f.2: version 2.13
[    0.743129] ata_piix 0000:00:1f.2: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    0.743137] ata_piix 0000:00:1f.2: MAP [ P0 P2 IDE IDE ]
[    0.743186] ata_piix 0000:00:1f.2: setting latency timer to 64
[    0.743568] scsi0 : ata_piix
[    0.743682] scsi1 : ata_piix
[    0.744225] ata1: SATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xbfa0 irq 14
[    0.744229] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xbfa8 irq 15
[    0.744669] Fixed MDIO Bus: probed
[    0.744701] PPP generic driver version 2.4.2
[    0.744744] tun: Universal TUN/TAP device driver, 1.6
[    0.744746] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.744837] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.744864] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    0.744877] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    0.744882] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    0.744925] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 1
[    0.744947] ehci_hcd 0000:00:1d.7: using broken periodic workaround
[    0.744961] ehci_hcd 0000:00:1d.7: debug port 1
[    0.748846] ehci_hcd 0000:00:1d.7: cache line size of 64 is not supported
[    0.748864] ehci_hcd 0000:00:1d.7: irq 20, io mem 0xffa80000
[    0.764019] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    0.764158] hub 1-0:1.0: USB hub found
[    0.764164] hub 1-0:1.0: 8 ports detected
[    0.764260] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.764277] uhci_hcd: USB Universal Host Controller Interface driver
[    0.764300] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    0.764307] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    0.764311] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    0.764357] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    0.764388] uhci_hcd 0000:00:1d.0: irq 20, io base 0x0000bf80
[    0.764523] hub 2-0:1.0: USB hub found
[    0.764528] hub 2-0:1.0: 2 ports detected
[    0.764611] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[    0.764618] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    0.764622] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    0.764661] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 3
[    0.764701] uhci_hcd 0000:00:1d.1: irq 21, io base 0x0000bf60
[    0.764839] hub 3-0:1.0: USB hub found
[    0.764844] hub 3-0:1.0: 2 ports detected
[    0.764925] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 22 (level, low) -> IRQ 22
[    0.764933] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    0.764937] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    0.764974] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 4
[    0.765017] uhci_hcd 0000:00:1d.2: irq 22, io base 0x0000bf40
[    0.765153] hub 4-0:1.0: USB hub found
[    0.765158] hub 4-0:1.0: 2 ports detected
[    0.765236] uhci_hcd 0000:00:1d.3: PCI INT D -> GSI 23 (level, low) -> IRQ 23
[    0.765244] uhci_hcd 0000:00:1d.3: setting latency timer to 64
[    0.765247] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[    0.765285] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 5
[    0.765325] uhci_hcd 0000:00:1d.3: irq 23, io base 0x0000bf20
[    0.765462] hub 5-0:1.0: USB hub found
[    0.765466] hub 5-0:1.0: 2 ports detected
[    0.765612] i8042: PNP: PS/2 Controller [PNP0303:KBC,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    0.768484] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.768492] serio: i8042 AUX port at 0x60,0x64 irq 12
[    0.768618] mousedev: PS/2 mouse device common for all mice
[    0.768803] rtc_cmos 00:06: RTC can wake from S4
[    0.768925] rtc_cmos 00:06: rtc core: registered rtc_cmos as rtc0
[    0.768964] rtc0: alarms up to one month, y3k, 114 bytes nvram, hpet irqs
[    0.769061] device-mapper: uevent: version 1.0.3
[    0.769152] device-mapper: ioctl: 4.20.0-ioctl (2011-02-02) initialised: dm-devel@redhat.com
[    0.769188] EISA: Probing bus 0 at eisa.0
[    0.769251] EISA: Mainboard ^O_FFFF detected.
[    0.769271] Cannot allocate resource for EISA slot 1
[    0.769273] Cannot allocate resource for EISA slot 2
[    0.769275] Cannot allocate resource for EISA slot 3
[    0.769278] Cannot allocate resource for EISA slot 4
[    0.769296] EISA: Detected 0 cards.
[    0.769308] cpufreq-nforce2: No nForce2 chipset.
[    0.769383] cpuidle: using governor ladder
[    0.769499] cpuidle: using governor menu
[    0.769502] EFI Variables Facility v0.08 2004-May-17
[    0.769852] TCP cubic registered
[    0.770008] NET: Registered protocol family 10
[    0.770747] NET: Registered protocol family 17
[    0.770766] Registering the dns_resolver key type
[    0.770790] Using IPI No-Shortcut mode
[    0.770889] PM: Hibernation image not present or could not be loaded.
[    0.770903] registered taskstats version 1
[    0.775997] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input3
[    0.784063]   Magic number: 0:677:65
[    0.784108] pci 0000:00:1e.0: hash matches
[    0.784177] rtc_cmos 00:06: setting system clock to 2012-02-06 07:05:06 UTC (1328511906)
[    0.784927] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.784929] EDD information not available.
[    0.908638] ata1.00: ATA-7: ST980825AS, 8.04, max UDMA/133
[    0.908646] ata1.00: 156301488 sectors, multi 8: LBA48 NCQ (depth 0/32)
[    0.924573] ata2.00: ATAPI: TSSTcorpCD-RW/DVD-ROM TSL462D, DE01, max UDMA/33
[    0.924938] ata1.00: configured for UDMA/133
[    0.925208] scsi 0:0:0:0: Direct-Access     ATA      ST980825AS       8.04 PQ: 0 ANSI: 5
[    0.925421] sd 0:0:0:0: [sda] 156301488 512-byte logical blocks: (80.0 GB/74.5 GiB)
[    0.925443] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    0.925482] sd 0:0:0:0: [sda] Write Protect is off
[    0.925485] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    0.925530] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    0.956322] ata2.00: configured for UDMA/33
[    0.957814] scsi 1:0:0:0: CD-ROM            TSSTcorp CDRW/DVD TSL462D DE01 PQ: 0 ANSI: 5
[    0.959380] sr0: scsi3-mmc drive: 24x/24x writer cd/rw xa/form2 cdda tray
[    0.959383] cdrom: Uniform CD-ROM driver Revision: 3.20
[    0.959495] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    0.959549] sr 1:0:0:0: Attached scsi generic sg1 type 5
[    0.963723]  sda: sda1 sda2 < sda5 >
[    0.964157] sd 0:0:0:0: [sda] Attached SCSI disk
[    0.964212] Freeing unused kernel memory: 696k freed
[    0.964466] Write protecting the kernel text: 5340k
[    0.964526] Write protecting the kernel read-only data: 2192k
[    0.982902] udevd[85]: starting version 173
[    1.047148] tg3.c:v3.119 (May 18, 2011)
[    1.047169] tg3 0000:09:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    1.047181] tg3 0000:09:00.0: setting latency timer to 64
[    1.082461] tg3 0000:09:00.0: eth0: Tigon3 [partno(BCM5752KFBG) rev 6002] (PCI Express) MAC address 00:18:8b:b9:76:79
[    1.082466] tg3 0000:09:00.0: eth0: attached PHY is 5752 (10/100/1000Base-T Ethernet) (WireSpeed[1], EEE[0])
[    1.082470] tg3 0000:09:00.0: eth0: RXcsums[1] LinkChgREG[0] MIirq[0] ASF[0] TSOcap[1]
[    1.082474] tg3 0000:09:00.0: eth0: dma_rwctrl[76180000] dma_mask[64-bit]
[    1.095050] sdhci: Secure Digital Host Controller Interface driver
[    1.095053] sdhci: Copyright(c) Pierre Ossman
[    1.098059] sdhci-pci 0000:03:01.1: SDHCI controller found [1180:0822] (rev 19)
[    1.098079] sdhci-pci 0000:03:01.1: PCI INT B -> GSI 18 (level, low) -> IRQ 18
[    1.099126] mmc0: no vmmc regulator found
[    1.106701] Registered led device: mmc0::
[    1.110810] mmc0: SDHCI controller on PCI [0000:03:01.1] using DMA
[    1.110913] firewire_ohci 0000:03:01.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    1.172185] firewire_ohci: Added fw-ohci device 0000:03:01.0, OHCI v1.10, 4 IR + 4 IT contexts, quirks 0x1
[    1.192069] usb 1-6: new high speed USB device number 3 using ehci_hcd
[    1.337790] usbcore: registered new interface driver uas
[    1.339687] Initializing USB Mass Storage driver...
[    1.339781] scsi2 : usb-storage 1-6:1.0
[    1.340093] usbcore: registered new interface driver usb-storage
[    1.340096] USB Mass Storage support registered.
[    1.356551] EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: (null)
[    1.568079] usb 2-1: new full speed USB device number 2 using uhci_hcd
[    1.672152] firewire_core: created device fw0: GUID 434fc0003825c561, S400
[    1.718514] hub 2-1:1.0: USB hub found
[    1.720486] hub 2-1:1.0: 4 ports detected
[    2.017498] usb 2-1.2: new full speed USB device number 3 using uhci_hcd
[    2.147537] hub 2-1.2:1.0: USB hub found
[    2.149510] hub 2-1.2:1.0: 3 ports detected
[    2.340762] scsi 2:0:0:0: Direct-Access     SanDisk  Cruzer           1.02 PQ: 0 ANSI: 2
[    2.420234] sd 2:0:0:0: Attached scsi generic sg2 type 0
[    2.420880] sd 2:0:0:0: [sdb] 7813120 512-byte logical blocks: (4.00 GB/3.72 GiB)
[    2.421635] sd 2:0:0:0: [sdb] Write Protect is off
[    2.421642] sd 2:0:0:0: [sdb] Mode Sense: 03 00 00 00
[    2.422518] sd 2:0:0:0: [sdb] No Caching mode page present
[    2.422523] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[    2.425732] sd 2:0:0:0: [sdb] No Caching mode page present
[    2.425735] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[    2.429842]  sdb:
[    2.432381] sd 2:0:0:0: [sdb] No Caching mode page present
[    2.432387] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[    2.432393] sd 2:0:0:0: [sdb] Attached SCSI removable disk
[    2.441502] usb 2-1.2.2: new full speed USB device number 4 using uhci_hcd
[   17.854539] udevd[304]: starting version 173
[   17.902293] lp: driver loaded but no devices found
[   17.966745] nvidia: module license 'NVIDIA' taints kernel.
[   17.966750] Disabling lock debugging due to kernel taint
[   17.970215] Adding 2094076k swap on /dev/sda5.  Priority:-1 extents:1 across:2094076k 
[   17.980130] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
[   17.990863] wmi: Mapper loaded
[   18.016795] type=1400 audit(1328511923.731:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=417 comm="apparmor_parser"
[   18.017263] type=1400 audit(1328511923.731:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=417 comm="apparmor_parser"
[   18.017939] type=1400 audit(1328511923.731:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=417 comm="apparmor_parser"
[   18.115585] acpi device:2e: registered as cooling_device2
[   18.116051] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A03:00/device:2b/LNXVIDEO:00/input/input4
[   18.116153] ACPI: Video Device [VID] (multi-head: yes  rom: no  post: no)
[   18.117969] cfg80211: Calling CRDA to update world regulatory domain
[   18.142794] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, in-tree:s
[   18.142798] iwl3945: Copyright(c) 2003-2011 Intel Corporation
[   18.142873] iwl3945 0000:0c:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   18.142889] iwl3945 0000:0c:00.0: setting latency timer to 64
[   18.196454] intel_rng: FWH not detected
[   18.196566] iwl3945 0000:0c:00.0: Tunable channels: 11 802.11bg, 13 802.11a channels
[   18.196570] iwl3945 0000:0c:00.0: Detected Intel Wireless WiFi Link 3945ABG
[   18.196724] iwl3945 0000:0c:00.0: irq 45 for MSI/MSI-X
[   18.336549] Registered led device: phy0-led
[   18.336627] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain 
[   18.338870] r852 0000:03:01.3: PCI INT B -> GSI 18 (level, low) -> IRQ 18
[   18.338880] r852 0000:03:01.3: setting latency timer to 64
[   18.361502] ieee80211 phy0: Selected rate control algorithm 'iwl-3945-rs'
[   18.370649] dcdbas dcdbas: Dell Systems Management Base Driver (version 5.6.0-3.2)
[   18.444254] r852: Non dma capable device detected, dma disabled
[   18.444278] r852: driver loaded successfully
[   18.444740] r592 0000:03:01.2: PCI INT B -> GSI 18 (level, low) -> IRQ 18
[   18.444750] r592 0000:03:01.2: setting latency timer to 64
[   18.450603] r592: driver successfully loaded
[   18.820989] leds_ss4200: no LED devices found
[   18.855746] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[   18.855813] HDA Intel 0000:00:1b.0: irq 46 for MSI/MSI-X
[   18.855847] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   19.015620] Synaptics Touchpad, model: 1, fw: 6.2, id: 0xfa0b1, caps: 0xa04713/0x200000/0x0
[   19.040198] init: failsafe main process (713) killed by TERM signal
[   19.052329] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input5
[   19.096660] nvidia 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   19.096669] nvidia 0000:01:00.0: setting latency timer to 64
[   19.096675] vgaarb: device changed decodes: PCI:0000:01:00.0,olddecodes=io+mem,decodes=none:owns=io+mem
[   19.099012] NVRM: loading NVIDIA UNIX x86 Kernel Module  173.14.30  Thu Apr 14 08:47:14 PDT 2011
[   19.113194] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain 
[   19.113199] cfg80211: World regulatory domain updated:
[   19.113201] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   19.113205] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   19.113208] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   19.113211] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   19.113214] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   19.113217] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   19.131025] input: HDA Intel Mic at Ext Right Jack as /devices/pci0000:00/0000:00:1b.0/sound/card0/input6
[   19.131866] input: HDA Intel HP Out at Ext Right Jack as /devices/pci0000:00/0000:00:1b.0/sound/card0/input7
[   19.140430] input: Dell WMI hotkeys as /devices/virtual/input/input8
[   19.146947] type=1400 audit(1328511924.859:5): apparmor="STATUS" operation="profile_load" name="/usr/lib/lightdm/lightdm-guest-session-wrapper" pid=794 comm="apparmor_parser"
[   19.151892] type=1400 audit(1328511924.863:6): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=800 comm="apparmor_parser"
[   19.152470] type=1400 audit(1328511924.867:7): apparmor="STATUS" operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" pid=793 comm="apparmor_parser"
[   19.154125] type=1400 audit(1328511924.867:8): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=800 comm="apparmor_parser"
[   19.154425] type=1400 audit(1328511924.867:9): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=800 comm="apparmor_parser"
[   19.161287] type=1400 audit(1328511924.875:10): apparmor="STATUS" operation="profile_load" name="/usr/lib/telepathy/mission-control-5" pid=807 comm="apparmor_parser"
[   19.165927] type=1400 audit(1328511924.879:11): apparmor="STATUS" operation="profile_load" name="/usr/lib/telepathy/telepathy-*" pid=807 comm="apparmor_parser"
[   19.524834] init: apport pre-start process (860) terminated with status 1
[   19.541186] init: apport post-stop process (900) terminated with status 1
[   19.745493] iwl3945 0000:0c:00.0: loaded firmware version 15.32.2.9
[   19.819298] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   19.845860] Bluetooth: Core ver 2.16
[   19.846326] NET: Registered protocol family 31
[   19.846329] Bluetooth: HCI device and connection manager initialized
[   19.846332] Bluetooth: HCI socket layer initialized
[   19.846334] Bluetooth: L2CAP socket layer initialized
[   19.846353] tg3 0000:09:00.0: irq 47 for MSI/MSI-X
[   19.849294] Bluetooth: SCO socket layer initialized
[   19.851873] Bluetooth: RFCOMM TTY layer initialized
[   19.851878] Bluetooth: RFCOMM socket layer initialized
[   19.851880] Bluetooth: RFCOMM ver 1.11
[   19.878463] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   19.878467] Bluetooth: BNEP filters: protocol multicast
[   19.892309] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   20.284470] vesafb: mode is 1280x1024x32, linelength=5120, pages=0
[   20.284473] vesafb: scrolling: redraw
[   20.284476] vesafb: Truecolor: size=8:8:8:8, shift=24:16:8:0
[   20.286023] vesafb: framebuffer at 0xd0000000, mapped to 0xf9b00000, using 5120k, total 5120k
[   20.286376] Console: switching to colour frame buffer device 160x64
[   20.286414] fb0: VESA VGA frame buffer device
[   20.319830] init: gdm main process (1062) killed by TERM signal
[   20.398176] ppdev: user-space parallel port driver
[   21.496527] cfg80211: Found new beacon on frequency: 5180 MHz (Ch 36) on phy0
[   22.648031] iwl3945 0000:0c:00.0: Error sending REPLY_RXON: time out after 500ms.
[   22.648037] iwl3945 0000:0c:00.0: Error setting new configuration (-110).
[   23.272028] iwl3945 0000:0c:00.0: Error sending REPLY_RXON: time out after 500ms.
[   23.272032] iwl3945 0000:0c:00.0: Error setting new configuration (-110).
[   31.456878] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,commit=0
[   31.577544] init: plymouth-stop pre-start process (1320) terminated with status 1
[   54.130345] wlan0: authenticate with 00:24:b2:75:53:77 (try 1)
[   54.132155] wlan0: authenticated
[   54.132450] wlan0: associate with 00:24:b2:75:53:77 (try 1)
[   54.134828] wlan0: RX AssocResp from 00:24:b2:75:53:77 (capab=0x411 status=0 aid=8)
[   54.134832] wlan0: associated
[   54.136470] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   64.400122] wlan0: no IPv6 routers present
[  121.592429] usb 1-6: USB disconnect, device number 3
[ 1129.312142] CE: hpet increased min_delta_ns to 20113 nsec
[ 1981.707758] do_general_protection: 24 callbacks suppressed
[ 1981.707767] chromium-browse[2732] general protection ip:f8bb50 sp:bffc3258 error:0 in libgtk-x11-2.0.so.0.2400.6[cde000+461000]
[ 2497.707958] chromium-browse[2901]: segfault at 0 ip   (null) sp bfcbb58c error 4 in libX11.so.6.3.0[110000+131000]

```

I think I am probably ready to just say the problem is with the device itself, this isn't going to work and I just need to get another cam.  If you see anything in the code above, or if you could recommend a good replacement cam, please let me know.  Otherwise, thanks so much for your time and effort.  It's been a great help!

---

### Post by Mosome on 2012-02-06
Try this troubleshooter and see if it helps:

[https://help.ubuntu.com/community/Webcam/Troubleshooting](https://help.ubuntu.com/community/Webcam/Troubleshooting)

---

