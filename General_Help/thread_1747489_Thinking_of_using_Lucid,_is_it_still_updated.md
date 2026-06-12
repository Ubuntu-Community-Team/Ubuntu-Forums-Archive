---
title: "Thinking of using Lucid, is it still updated?"
date: 2011-05-02
forum: General Help
---

### Post by RJ12 on 2011-05-02
Ok, so it seems like the more I use Unity, the more I seem to be getting slightly annoyed with it and I was thinking that maybe I should drop back down to the last LTS release (ubuntu 10.04), but I was wondering... is most software still made for it? I would hate to install Lucid and end up finding out that most of the repositories don't have software available for Lucid. I know the Ubuntu repos will have software for Lucid, but what about the other Launchpad repos? Ubuntu 10.04 did seem to work better on my computer, but I want to have my software available for it.

---

### Post by lakerssuperman on 2011-05-02
Just curious, is it a performance issue or do you simply not like the new Unity interface?  If you don't like the interface, you can still use 11.04 and simply select Unity Classic from the login screen.

As to 10.04, it is fully supported on the desktop until April 2013.  most current PPA's support 10.04 as it is an LTS release.  I haven't seen a program out there that doesn't have an option for this release.  Obviously the further you go towards the next LTS the less likely it will be that this will get the latest and greatest packages.

---

### Post by RJ12 on 2011-05-02
> **lakerssuperman said:**
> Just curious, is it a performance issue or do you simply not like the new Unity interface?  If you don't like the interface, you can still use 11.04 and simply select Unity Classic from the login screen.

As to 10.04, it is fully supported on the desktop until April 2013.  most current PPA's support 10.04 as it is an LTS release.  I haven't seen a program out there that doesn't have an option for this release.  Obviously the further you go towards the next LTS the less likely it will be that this will get the latest and greatest packages.

Yeah, it's mainly performance issues, thanks for replying so quickly :)

---

### Post by IWantFroyo on 2011-05-02
If we can't fix them, I would suggest falling back to the LTE. What problems are you having?

---

### Post by RJ12 on 2011-05-02
> **IWantFroyo said:**
> If we can't fix them, I would suggest falling back to the LTS (<-- I fixed this, it said "LTE" I assumed "LTS"?). What problems are you having?

Well, mainly, I have had problems where X would crash (doesn't happen often, but is very annoying when it does) out of no where and I would be kicked to the login screen (this also happens in Classic... so I don't think it's Unity), and I have had a lot of heat problems with the graphics card which was solved when I installed the proprietary driver, but then things like video was real choppy. I have an ATI Graphics card and I tried the VBlank fix that has been floating around. Anyways if you want to help me with my problems, that would be great (it's probably better than using an older release), as things like my iPod Touch 4G don't work in Lucid (they need updated drivers which I would guess is not in Lucid). I would be happy to post any output that would be helpful, I'm going to post some starting output though :)

DMESG
```
[    0.189992] pnp 00:08: [io  0x0c00-0x0c01]
[    0.189994] pnp 00:08: [io  0x0c14]
[    0.189996] pnp 00:08: [io  0x0c50-0x0c52]
[    0.189999] pnp 00:08: [io  0x0c6c]
[    0.190001] pnp 00:08: [io  0x0c6f]
[    0.190003] pnp 00:08: [io  0x0cd0-0x0cd1]
[    0.190005] pnp 00:08: [io  0x0cd2-0x0cd3]
[    0.190008] pnp 00:08: [io  0x0cd4-0x0cd5]
[    0.190010] pnp 00:08: [io  0x0cd6-0x0cd7]
[    0.190012] pnp 00:08: [io  0x0cd8-0x0cdf]
[    0.190015] pnp 00:08: [io  0x8000-0x805f]
[    0.190017] pnp 00:08: [io  0xfd60-0xfd63]
[    0.190020] pnp 00:08: [io  0x8100-0x81ff window]
[    0.190022] pnp 00:08: [io  0x8200-0x82ff window]
[    0.190025] pnp 00:08: [io  0x0f40-0x0f47]
[    0.190027] pnp 00:08: [io  0x087f]
[    0.190124] system 00:08: [io  0x0220-0x022f] has been reserved
[    0.190127] system 00:08: [io  0x040b] has been reserved
[    0.190130] system 00:08: [io  0x04d0-0x04d1] has been reserved
[    0.190133] system 00:08: [io  0x04d6] has been reserved
[    0.190137] system 00:08: [io  0x0530-0x0537] has been reserved
[    0.190140] system 00:08: [io  0x0c00-0x0c01] has been reserved
[    0.190143] system 00:08: [io  0x0c14] has been reserved
[    0.190146] system 00:08: [io  0x0c50-0x0c52] has been reserved
[    0.190149] system 00:08: [io  0x0c6c] has been reserved
[    0.190152] system 00:08: [io  0x0c6f] has been reserved
[    0.190155] system 00:08: [io  0x0cd0-0x0cd1] has been reserved
[    0.190158] system 00:08: [io  0x0cd2-0x0cd3] has been reserved
[    0.190161] system 00:08: [io  0x0cd4-0x0cd5] has been reserved
[    0.190165] system 00:08: [io  0x0cd6-0x0cd7] has been reserved
[    0.190168] system 00:08: [io  0x0cd8-0x0cdf] has been reserved
[    0.190171] system 00:08: [io  0x8000-0x805f] has been reserved
[    0.190174] system 00:08: [io  0xfd60-0xfd63] has been reserved
[    0.190180] system 00:08: [io  0x8100-0x81ff window] has been reserved
[    0.190184] system 00:08: [io  0x8200-0x82ff window] has been reserved
[    0.190187] system 00:08: [io  0x0f40-0x0f47] has been reserved
[    0.190190] system 00:08: [io  0x087f] has been reserved
[    0.190194] system 00:08: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.190292] pnp 00:09: [mem 0x000e0000-0x000fffff]
[    0.190295] pnp 00:09: [mem 0xfff00000-0xffffffff]
[    0.190298] pnp 00:09: [mem 0x00000000-0xffffffffffffffff disabled]
[    0.190300] pnp 00:09: [mem 0xfec10000-0xfec1001f]
[    0.190362] system 00:09: [mem 0x000e0000-0x000fffff] could not be reserved
[    0.190365] system 00:09: [mem 0xfff00000-0xffffffff] has been reserved
[    0.190369] system 00:09: [mem 0xfec10000-0xfec1001f] has been reserved
[    0.190372] system 00:09: Plug and Play ACPI device, IDs PNP0c01 (active)
[    0.190482] pnp 00:0a: [mem 0xfed00000-0xfed003ff]
[    0.190529] pnp 00:0a: Plug and Play ACPI device, IDs PNP0103 (active)
[    0.212095] pnp: PnP ACPI: found 11 devices
[    0.212097] ACPI: ACPI bus type pnp unregistered
[    0.212101] PnPBIOS: Disabled by ACPI PNP
[    0.249101] pci 0000:00:07.0: BAR 14: assigned [mem 0xc8000000-0xc80fffff]
[    0.249105] pci 0000:00:01.0: PCI bridge to [bus 01-01]
[    0.249109] pci 0000:00:01.0:   bridge window [io  0x9000-0x9fff]
[    0.249114] pci 0000:00:01.0:   bridge window [mem 0xcfd00000-0xcfefffff]
[    0.249118] pci 0000:00:01.0:   bridge window [mem 0xd0000000-0xdfffffff 64bit pref]
[    0.249124] pci 0000:00:06.0: PCI bridge to [bus 0e-0e]
[    0.249127] pci 0000:00:06.0:   bridge window [io  0xa000-0xafff]
[    0.249132] pci 0000:00:06.0:   bridge window [mem 0xf0200000-0xf02fffff]
[    0.249136] pci 0000:00:06.0:   bridge window [mem pref disabled]
[    0.249143] pci 0000:14:00.0: BAR 6: assigned [mem 0xf0420000-0xf043ffff pref]
[    0.249146] pci 0000:00:07.0: PCI bridge to [bus 14-14]
[    0.249150] pci 0000:00:07.0:   bridge window [io  0xb000-0xbfff]
[    0.249154] pci 0000:00:07.0:   bridge window [mem 0xc8000000-0xc80fffff]
[    0.249159] pci 0000:00:07.0:   bridge window [mem 0xf0400000-0xf04fffff 64bit pref]
[    0.249164] pci 0000:00:14.4: PCI bridge to [bus 28-2a]
[    0.249167] pci 0000:00:14.4:   bridge window [io  disabled]
[    0.249207] pci 0000:00:14.4:   bridge window [mem disabled]
[    0.249212] pci 0000:00:14.4:   bridge window [mem pref disabled]
[    0.249241] pci 0000:00:06.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    0.249246] pci 0000:00:06.0: setting latency timer to 64
[    0.249254] pci 0000:00:07.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    0.249259] pci 0000:00:07.0: setting latency timer to 64
[    0.249268] pci_bus 0000:00: resource 4 [mem 0x000a0000-0x000bffff]
[    0.249271] pci_bus 0000:00: resource 5 [mem 0x000d0000-0x000d1fff]
[    0.249273] pci_bus 0000:00: resource 6 [mem 0x000d2000-0x000d3fff]
[    0.249276] pci_bus 0000:00: resource 7 [mem 0x000d4000-0x000d5fff]
[    0.249279] pci_bus 0000:00: resource 8 [mem 0x000d6000-0x000d7fff]
[    0.249282] pci_bus 0000:00: resource 9 [mem 0x000d8000-0x000d9fff]
[    0.249285] pci_bus 0000:00: resource 10 [mem 0x000da000-0x000dbfff]
[    0.249288] pci_bus 0000:00: resource 11 [mem 0x000dc000-0x000ddfff]
[    0.249291] pci_bus 0000:00: resource 12 [mem 0x000de000-0x000dffff]
[    0.249294] pci_bus 0000:00: resource 13 [mem 0x000e0000-0x000e1fff]
[    0.249297] pci_bus 0000:00: resource 14 [mem 0x000e2000-0x000e3fff]
[    0.249300] pci_bus 0000:00: resource 15 [mem 0xc8000000-0xdfffffff]
[    0.249303] pci_bus 0000:00: resource 16 [mem 0xf0000000-0xffffffff]
[    0.249306] pci_bus 0000:00: resource 17 [io  0x0000-0x0cf7]
[    0.249308] pci_bus 0000:00: resource 18 [io  0x0d00-0xffff]
[    0.249311] pci_bus 0000:01: resource 0 [io  0x9000-0x9fff]
[    0.249314] pci_bus 0000:01: resource 1 [mem 0xcfd00000-0xcfefffff]
[    0.249317] pci_bus 0000:01: resource 2 [mem 0xd0000000-0xdfffffff 64bit pref]
[    0.249321] pci_bus 0000:0e: resource 0 [io  0xa000-0xafff]
[    0.249323] pci_bus 0000:0e: resource 1 [mem 0xf0200000-0xf02fffff]
[    0.249326] pci_bus 0000:14: resource 0 [io  0xb000-0xbfff]
[    0.249329] pci_bus 0000:14: resource 1 [mem 0xc8000000-0xc80fffff]
[    0.249332] pci_bus 0000:14: resource 2 [mem 0xf0400000-0xf04fffff 64bit pref]
[    0.249336] pci_bus 0000:28: resource 4 [mem 0x000a0000-0x000bffff]
[    0.249339] pci_bus 0000:28: resource 5 [mem 0x000d0000-0x000d1fff]
[    0.249342] pci_bus 0000:28: resource 6 [mem 0x000d2000-0x000d3fff]
[    0.249345] pci_bus 0000:28: resource 7 [mem 0x000d4000-0x000d5fff]
[    0.249347] pci_bus 0000:28: resource 8 [mem 0x000d6000-0x000d7fff]
[    0.249350] pci_bus 0000:28: resource 9 [mem 0x000d8000-0x000d9fff]
[    0.249353] pci_bus 0000:28: resource 10 [mem 0x000da000-0x000dbfff]
[    0.249356] pci_bus 0000:28: resource 11 [mem 0x000dc000-0x000ddfff]
[    0.249359] pci_bus 0000:28: resource 12 [mem 0x000de000-0x000dffff]
[    0.249362] pci_bus 0000:28: resource 13 [mem 0x000e0000-0x000e1fff]
[    0.249365] pci_bus 0000:28: resource 14 [mem 0x000e2000-0x000e3fff]
[    0.249368] pci_bus 0000:28: resource 15 [mem 0xc8000000-0xdfffffff]
[    0.249371] pci_bus 0000:28: resource 16 [mem 0xf0000000-0xffffffff]
[    0.249374] pci_bus 0000:28: resource 17 [io  0x0000-0x0cf7]
[    0.249377] pci_bus 0000:28: resource 18 [io  0x0d00-0xffff]
[    0.249417] NET: Registered protocol family 2
[    0.249481] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.249761] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.250465] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.250793] TCP: Hash tables configured (established 131072 bind 65536)
[    0.250796] TCP reno registered
[    0.250800] UDP hash table entries: 512 (order: 2, 16384 bytes)
[    0.250812] UDP-Lite hash table entries: 512 (order: 2, 16384 bytes)
[    0.250903] NET: Registered protocol family 1
[    0.250916] pci 0000:00:01.0: MSI quirk detected; subordinate MSI disabled
[    0.251072] pci 0000:01:05.0: Boot video device
[    0.251080] PCI: CLS 32 bytes, default 64
[    0.251403] cpufreq-nforce2: No nForce2 chipset.
[    0.251553] audit: initializing netlink socket (disabled)
[    0.251567] type=2000 audit(1304360887.244:1): initialized
[    0.262889] Trying to unpack rootfs image as initramfs...
[    0.280901] highmem bounce pool size: 64 pages
[    0.280909] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    0.288364] VFS: Disk quotas dquot_6.5.2
[    0.288444] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.289221] fuse init (API version 7.16)
[    0.289320] msgmni has been set to 1601
[    0.296631] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.296697] io scheduler noop registered
[    0.296699] io scheduler deadline registered
[    0.296720] io scheduler cfq registered (default)
[    0.296861] pcieport 0000:00:06.0: setting latency timer to 64
[    0.296910] pcieport 0000:00:06.0: irq 40 for MSI/MSI-X
[    0.296975] pcieport 0000:00:07.0: setting latency timer to 64
[    0.297010] pcieport 0000:00:07.0: irq 41 for MSI/MSI-X
[    0.297099] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.297134] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.297321] ACPI: Deprecated procfs I/F for AC is loaded, please retry with CONFIG_ACPI_PROCFS_POWER cleared
[    0.297409] ACPI: AC Adapter [ACAD] (on-line)
[    0.297474] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0
[    0.297481] ACPI: Power Button [PWRB]
[    0.297537] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input1
[    0.297604] ACPI: Lid Switch [LID]
[    0.297650] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input2
[    0.297653] ACPI: Power Button [PWRF]
[    0.297843] ACPI: acpi_idle registered with cpuidle
[    0.320535] ACPI: Deprecated procfs I/F for battery is loaded, please retry with CONFIG_ACPI_PROCFS_POWER cleared
[    0.320590] ERST: Table is not found!
[    0.320727] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    0.322253] Linux agpgart interface v0.103
[    0.323627] brd: module loaded
[    0.328402] loop: module loaded
[    0.328547] i2c-core: driver [adp5520] using legacy suspend method
[    0.328550] i2c-core: driver [adp5520] using legacy resume method
[    0.328797] pata_acpi 0000:00:14.1: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.329294] Fixed MDIO Bus: probed
[    0.329335] PPP generic driver version 2.4.2
[    0.329379] tun: Universal TUN/TAP device driver, 1.6
[    0.329381] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.329473] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.329527] ehci_hcd 0000:00:12.2: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    0.329552] ehci_hcd 0000:00:12.2: EHCI Host Controller
[    0.329596] ehci_hcd 0000:00:12.2: new USB bus registered, assigned bus number 1
[    0.329645] ehci_hcd 0000:00:12.2: applying AMD SB700/SB800/Hudson-2/3 EHCI dummy qh workaround
[    0.329664] ehci_hcd 0000:00:12.2: applying AMD SB600/SB700 USB freeze workaround
[    0.329681] ehci_hcd 0000:00:12.2: debug port 1
[    0.329707] ehci_hcd 0000:00:12.2: irq 17, io mem 0xf0308400
[    0.329893] isapnp: Scanning for PnP cards...
[    0.384232] ehci_hcd 0000:00:12.2: USB 2.0 started, EHCI 1.00
[    0.384396] hub 1-0:1.0: USB hub found
[    0.384400] hub 1-0:1.0: 6 ports detected
[    0.384557] ehci_hcd 0000:00:13.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    0.384571] ehci_hcd 0000:00:13.2: EHCI Host Controller
[    0.384609] ehci_hcd 0000:00:13.2: new USB bus registered, assigned bus number 2
[    0.384660] ehci_hcd 0000:00:13.2: applying AMD SB700/SB800/Hudson-2/3 EHCI dummy qh workaround
[    0.384676] ehci_hcd 0000:00:13.2: applying AMD SB600/SB700 USB freeze workaround
[    0.384692] ehci_hcd 0000:00:13.2: debug port 1
[    0.384713] ehci_hcd 0000:00:13.2: irq 19, io mem 0xf0308800
[    0.440886] ehci_hcd 0000:00:13.2: USB 2.0 started, EHCI 1.00
[    0.441079] hub 2-0:1.0: USB hub found
[    0.441085] hub 2-0:1.0: 6 ports detected
[    0.441222] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.441280] ohci_hcd 0000:00:12.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.441306] ohci_hcd 0000:00:12.0: OHCI Host Controller
[    0.441352] ohci_hcd 0000:00:12.0: new USB bus registered, assigned bus number 3
[    0.441425] ohci_hcd 0000:00:12.0: irq 16, io mem 0xf0304000
[    0.640911] hub 3-0:1.0: USB hub found
[    0.640955] hub 3-0:1.0: 3 ports detected
[    0.641091] ohci_hcd 0000:00:12.1: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.641119] ohci_hcd 0000:00:12.1: OHCI Host Controller
[    0.641170] ohci_hcd 0000:00:12.1: new USB bus registered, assigned bus number 4
[    0.641229] ohci_hcd 0000:00:12.1: irq 16, io mem 0xf0305000
[    0.735927] hub 4-0:1.0: USB hub found
[    0.735970] hub 4-0:1.0: 3 ports detected
[    0.740195] ohci_hcd 0000:00:13.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    0.740224] ohci_hcd 0000:00:13.0: OHCI Host Controller
[    0.740296] ohci_hcd 0000:00:13.0: new USB bus registered, assigned bus number 5
[    0.740371] ohci_hcd 0000:00:13.0: irq 18, io mem 0xf0306000
[    0.792817] isapnp: No Plug & Play device found
[    0.804475] hub 5-0:1.0: USB hub found
[    0.804518] hub 5-0:1.0: 3 ports detected
[    0.804608] ohci_hcd 0000:00:13.1: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    0.804636] ohci_hcd 0000:00:13.1: OHCI Host Controller
[    0.804687] ohci_hcd 0000:00:13.1: new USB bus registered, assigned bus number 6
[    0.804749] ohci_hcd 0000:00:13.1: irq 18, io mem 0xf0307000
[    0.816216] usb 1-1: new high speed USB device using ehci_hcd and address 2
[    0.868498] hub 6-0:1.0: USB hub found
[    0.868541] hub 6-0:1.0: 3 ports detected
[    0.868636] uhci_hcd: USB Universal Host Controller Interface driver
[    0.868744] i8042: PNP: PS/2 Controller [PNP0303:KBC0,PNP0f13:MSE0] at 0x60,0x64 irq 1,12
[    0.890735] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.890745] serio: i8042 AUX port at 0x60,0x64 irq 12
[    0.890969] mousedev: PS/2 mouse device common for all mice
[    0.892048] rtc_cmos 00:04: RTC can wake from S4
[    0.892141] rtc_cmos 00:04: rtc core: registered rtc_cmos as rtc0
[    0.892170] rtc0: alarms up to one month, 114 bytes nvram, hpet irqs
[    0.892287] device-mapper: uevent: version 1.0.3
[    0.892387] device-mapper: ioctl: 4.19.1-ioctl (2011-01-07) initialised: dm-devel@redhat.com
[    0.895598] device-mapper: multipath: version 1.2.0 loaded
[    0.895603] device-mapper: multipath round-robin: version 1.0.0 loaded
[    0.895743] EISA: Probing bus 0 at eisa.0
[    0.895748] EISA: Cannot allocate resource for mainboard
[    0.895751] Cannot allocate resource for EISA slot 1
[    0.895753] Cannot allocate resource for EISA slot 2
[    0.895755] Cannot allocate resource for EISA slot 3
[    0.895758] Cannot allocate resource for EISA slot 4
[    0.895760] Cannot allocate resource for EISA slot 5
[    0.895763] Cannot allocate resource for EISA slot 6
[    0.895765] Cannot allocate resource for EISA slot 7
[    0.895767] Cannot allocate resource for EISA slot 8
[    0.895769] EISA: Detected 0 cards.
[    0.898634] cpuidle: using governor ladder
[    0.898638] cpuidle: using governor menu
[    0.898935] TCP cubic registered
[    0.899090] NET: Registered protocol family 10
[    0.899622] NET: Registered protocol family 17
[    0.899646] Registering the dns_resolver key type
[    0.899671] powernow-k8: Found 1 AMD Sempron(tm) SI-42 (1 cpu cores) (version 2.20.00)
[    0.899714] powernow-k8:    0 : pstate 0 (2100 MHz)
[    0.899716] powernow-k8:    1 : pstate 1 (1050 MHz)
[    0.899902] Using IPI No-Shortcut mode
[    0.900106] PM: Hibernation image not present or could not be loaded.
[    0.900120] registered taskstats version 1
[    0.900434]   Magic number: 11:976:492
[    0.900608] rtc_cmos 00:04: setting system clock to 2011-05-02 18:28:10 UTC (1304360890)
[    0.900612] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.900614] EDD information not available.
[    0.907738] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input3
[    0.958641] hub 1-1:1.0: USB hub found
[    0.958979] hub 1-1:1.0: 4 ports detected
[    0.972334] ACPI: Battery Slot [BAT1] (battery present)
[    1.181139] Freeing initrd memory: 17768k freed
[    1.192652] Freeing unused kernel memory: 720k freed
[    1.193166] Write protecting the kernel text: 5352k
[    1.193214] Write protecting the kernel read-only data: 2188k
[    1.193216] NX-protecting the kernel data: 4888k
[    1.225087] <30>udev[63]: starting version 167
[    1.232459] usb 1-1.1: new low speed USB device using ehci_hcd and address 3
[    1.260075] Refined TSC clocksource calibration: 2099.134 MHz.
[    1.260082] Switching to clocksource tsc
[    1.327049] usb 1-1.1: config 1 has an invalid interface number: 1 but max is 0
[    1.327055] usb 1-1.1: config 1 has no interface number 0
[    1.442102] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    1.442134] r8169 0000:14:00.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    1.442177] r8169 0000:14:00.0: setting latency timer to 64
[    1.442231] r8169 0000:14:00.0: irq 42 for MSI/MSI-X
[    1.442731] r8169 0000:14:00.0: eth0: RTL8102e at 0xf8412000, 00:26:22:f5:f0:3a, XID 04c00000 IRQ 42
[    1.468119] scsi0 : pata_atiixp
[    1.470531] scsi1 : pata_atiixp
[    1.471438] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0x8410 irq 14
[    1.471442] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x8418 irq 15
[    1.476432] [Firmware Bug]: ACPI: No _BQC method, cannot determine initial brightness
[    1.480581] acpi device:36: registered as cooling_device1
[    1.480704] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:34/LNXVIDEO:01/input/input4
[    1.480766] ACPI: Video Device [VGA1] (multi-head: yes  rom: no  post: no)
[    1.514912] ahci 0000:00:11.0: version 3.0
[    1.514984] ahci 0000:00:11.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[    1.515166] ahci 0000:00:11.0: AHCI 0001.0100 32 slots 4 ports 3 Gbps 0xf impl SATA mode
[    1.515170] ahci 0000:00:11.0: flags: 64bit ncq sntf ilck pm led clo pmp pio slum part ccc 
[    1.534456] scsi2 : ahci
[    1.552565] scsi3 : ahci
[    1.552741] [drm] Initialized drm 1.1.0 20060810
[    1.553264] scsi4 : ahci
[    1.553387] scsi5 : ahci
[    1.553558] ata3: SATA max UDMA/133 abar m1024@0xf0308000 port 0xf0308100 irq 22
[    1.553562] ata4: SATA max UDMA/133 abar m1024@0xf0308000 port 0xf0308180 irq 22
[    1.553567] ata5: SATA max UDMA/133 abar m1024@0xf0308000 port 0xf0308200 irq 22
[    1.553571] ata6: SATA max UDMA/133 abar m1024@0xf0308000 port 0xf0308280 irq 22
[    1.872029] ata3: SATA link down (SStatus 0 SControl 300)
[    1.872079] ata5: SATA link down (SStatus 0 SControl 300)
[    2.044012] ata4: softreset failed (device not ready)
[    2.044016] ata4: applying SB600 PMP SRST workaround and retrying
[    2.044033] ata6: softreset failed (device not ready)
[    2.044036] ata6: applying SB600 PMP SRST workaround and retrying
[    2.216033] ata4: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    2.216058] ata6: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    2.220148] ata6.00: ATAPI: HL-DT-ST DVDRAM GT20N, CT11, max UDMA/133
[    2.225038] ata6.00: configured for UDMA/133
[    2.262650] ata4.00: ATA-8: TOSHIBA MK2555GSX, FG001M, max UDMA/100
[    2.262654] ata4.00: 488397168 sectors, multi 16: LBA48 NCQ (depth 31/32), AA
[    2.263491] ata4.00: configured for UDMA/100
[    2.263616] scsi 3:0:0:0: Direct-Access     ATA      TOSHIBA MK2555GS FG00 PQ: 0 ANSI: 5
[    2.263829] sd 3:0:0:0: Attached scsi generic sg0 type 0
[    2.264164] sd 3:0:0:0: [sda] 488397168 512-byte logical blocks: (250 GB/232 GiB)
[    2.264217] sd 3:0:0:0: [sda] Write Protect is off
[    2.264221] sd 3:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    2.264244] sd 3:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.266957] scsi 5:0:0:0: CD-ROM            HL-DT-ST DVDRAM GT20N     CT11 PQ: 0 ANSI: 5
[    2.271911] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[    2.271915] cdrom: Uniform CD-ROM driver Revision: 3.20
[    2.272056] sr 5:0:0:0: Attached scsi CD-ROM sr0
[    2.272128] sr 5:0:0:0: Attached scsi generic sg1 type 5
[    2.373315]  sda: sda1 sda2 sda3 < sda5 sda6 sda7 >
[    2.373901] sd 3:0:0:0: [sda] Attached SCSI disk
[    2.413392] input: 2.4GHz 2way RF Receiver as /devices/pci0000:00/0000:00:12.2/usb1/1-1/1-1.1/1-1.1:1.1/input/input5
[    2.413927] generic-usb 0003:1BCF:053A.0001: input,hiddev0,hidraw0: USB HID v1.00 Mouse [2.4GHz 2way RF Receiver] on usb-0000:00:12.2-1.1/input1
[    2.414100] usbcore: registered new interface driver usbhid
[    2.414102] usbhid: USB HID core driver
[    2.467421] [drm] radeon defaulting to kernel modesetting.
[    2.467426] [drm] radeon kernel modesetting enabled.
[    2.467522] radeon 0000:01:05.0: power state changed by ACPI to D0
[    2.467527] radeon 0000:01:05.0: power state changed by ACPI to D0
[    2.467537] radeon 0000:01:05.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    2.467543] radeon 0000:01:05.0: setting latency timer to 64
[    2.469503] [drm] initializing kernel modesetting (RS780 0x1002:0x9613).
[    2.469538] [drm] register mmio base: 0xCFDF0000
[    2.469540] [drm] register mmio size: 65536
[    2.469699] ATOM BIOS: Toshiba_BLS_MC
[    2.469740] radeon 0000:01:05.0: VRAM: 256M 0x00000000C0000000 - 0x00000000CFFFFFFF (256M used)
[    2.469744] radeon 0000:01:05.0: GTT: 512M 0x00000000A0000000 - 0x00000000BFFFFFFF
[    2.469862] [drm] Detected VRAM RAM=256M, BAR=256M
[    2.469867] [drm] RAM width 32bits DDR
[    2.469963] [TTM] Zone  kernel: Available graphics memory: 419110 kiB.
[    2.469966] [TTM] Zone highmem: Available graphics memory: 1927882 kiB.
[    2.469968] [TTM] Initializing pool allocator.
[    2.469992] [drm] radeon: 256M of VRAM memory ready
[    2.469994] [drm] radeon: 512M of GTT memory ready.
[    2.470016] [drm] Supports vblank timestamp caching Rev 1 (10.10.2010).
[    2.470018] [drm] Driver supports precise vblank timestamp query.
[    2.470046] [drm] radeon: irq initialized.
[    2.470050] [drm] GART: num cpu pages 131072, num gpu pages 131072
[    2.472289] [drm] Loading RS780 Microcode
[    2.488120] radeon 0000:01:05.0: WB enabled
[    2.521423] [drm] ring test succeeded in 1 usecs
[    2.521649] [drm] radeon: ib pool ready.
[    2.521718] [drm] ib test succeeded in 0 usecs
[    2.521722] [drm] Enabling audio support
[    2.523111] [drm] Radeon Display Connectors
[    2.523113] [drm] Connector 0:
[    2.523115] [drm]   VGA
[    2.523118] [drm]   DDC: 0x7e40 0x7e40 0x7e44 0x7e44 0x7e48 0x7e48 0x7e4c 0x7e4c
[    2.523120] [drm]   Encoders:
[    2.523122] [drm]     CRT1: INTERNAL_KLDSCP_DAC1
[    2.523124] [drm] Connector 1:
[    2.523126] [drm]   LVDS
[    2.523128] [drm]   DDC: 0x7e50 0x7e50 0x7e54 0x7e54 0x7e58 0x7e58 0x7e5c 0x7e5c
[    2.523130] [drm]   Encoders:
[    2.523132] [drm]     LCD1: INTERNAL_KLDSCP_LVTMA
[    2.579741] [drm] radeon: power management initialized
[    3.596576] [drm] fb mappable at 0xD0141000
[    3.596580] [drm] vram apper at 0xD0000000
[    3.596583] [drm] size 4325376
[    3.596584] [drm] fb depth is 24
[    3.596586] [drm]    pitch is 5632
[    3.597106] Console: switching to colour frame buffer device 170x48
[    3.597143] fb0: radeondrmfb frame buffer device
[    3.597146] drm: registered panic notifier
[    3.597155] [drm] Initialized radeon 2.8.0 20080528 for 0000:01:05.0 on minor 0
[    3.946965] EXT4-fs (sda6): mounted filesystem with ordered data mode. Opts: (null)
[   16.368059] Adding 4607996k swap on /dev/sda5.  Priority:-1 extents:1 across:4607996k 
[   16.440169] <30>udev[331]: starting version 167
[   16.482055] lp: driver loaded but no devices found
[   16.517028] Initializing USB Mass Storage driver...
[   16.517278] usbcore: registered new interface driver usb-storage
[   16.517281] USB Mass Storage support registered.
[   16.711924] EXT4-fs (sda6): re-mounted. Opts: errors=remount-ro
[   17.025785] Disabling lock debugging due to kernel taint
[   17.065806] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   17.096374] type=1400 audit(1304378906.694:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=521 comm="apparmor_parser"
[   17.096795] type=1400 audit(1304378906.694:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=521 comm="apparmor_parser"
[   17.097053] type=1400 audit(1304378906.694:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=521 comm="apparmor_parser"
[   17.384570] piix4_smbus 0000:00:14.0: SMBus Host Controller at 0x8040, revision 0
[   17.385793] SP5100 TCO timer: SP5100 TCO WatchDog Timer Driver v0.01
[   17.385926] SP5100 TCO timer: mmio address 0xfec000f0 already in use
[   17.422763] ndiswrapper version 1.56 loaded (smp=yes, preempt=no)
[   17.914650] ndiswrapper: driver net8187se (Realtek Semiconductor Corp.,10/28/2009,5.9109.1028.2009) loaded
[   17.914955] ndiswrapper 0000:0e:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[   17.915541] ndiswrapper 0000:0e:00.0: setting latency timer to 64
[   18.169715] ndiswrapper: using IRQ 18
[   18.397000] HDA Intel 0000:00:14.2: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   18.558832] hda_codec: ALC272: BIOS auto-probing.
[   18.611993] input: HDA ATI SB Headphone as /devices/pci0000:00/0000:00:14.2/sound/card0/input6
[   18.672540] Synaptics Touchpad, model: 1, fw: 7.0, id: 0x1c0b1, caps: 0xd04711/0xa00000/0x20000
[   18.672549] synaptics: Toshiba Satellite L455D detected, limiting rate to 40pps.
[   18.744232] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input7
[   18.900797] wlan0: ethernet device 70:1a:04:91:5a:b9 using NDIS driver: net8187se, version: 0x500a5, NDIS version: 0x500, vendor: 'Realtek RTL8185 Wireless LAN (Mini-)PCI NIC                                     ', 10EC:8199.5.conf
[   18.900822] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2PSK; AES/CCMP with WPA, WPA2, WPA2PSK
[   18.902695] usbcore: registered new interface driver ndiswrapper
[   22.490982] EXT4-fs (sda7): mounted filesystem with ordered data mode. Opts: (null)
[   23.769647] ppdev: user-space parallel port driver
[   23.827209] type=1400 audit(1304378913.422:5): apparmor="STATUS" operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" pid=846 comm="apparmor_parser"
[   23.855986] type=1400 audit(1304378913.450:6): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=849 comm="apparmor_parser"
[   23.856631] type=1400 audit(1304378913.454:7): apparmor="STATUS" operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" pid=845 comm="apparmor_parser"
[   23.861140] type=1400 audit(1304378913.458:8): apparmor="STATUS" operation="profile_load" name="/usr/sbin/cupsd" pid=845 comm="apparmor_parser"
[   23.882169] type=1400 audit(1304378913.478:9): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=849 comm="apparmor_parser"
[   23.882440] type=1400 audit(1304378913.478:10): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=849 comm="apparmor_parser"
[   23.937267] type=1400 audit(1304378913.534:11): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince" pid=853 comm="apparmor_parser"
[   23.958058] type=1400 audit(1304378913.554:12): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince-previewer" pid=853 comm="apparmor_parser"
[   23.970959] type=1400 audit(1304378913.566:13): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince-thumbnailer" pid=853 comm="apparmor_parser"
[   23.990826] type=1400 audit(1304378913.586:14): apparmor="STATUS" operation="profile_replace" name="/usr/lib/cups/backend/cups-pdf" pid=862 comm="apparmor_parser"
[   24.147193] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   24.176328] r8169 0000:14:00.0: eth0: link down
[   24.190217] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   25.543257] EXT4-fs (sda6): re-mounted. Opts: errors=remount-ro,commit=0
[   25.633471] EXT4-fs (sda7): re-mounted. Opts: commit=0
[   28.045933] EXT4-fs (sda6): re-mounted. Opts: errors=remount-ro,commit=0
[   28.050055] EXT4-fs (sda7): re-mounted. Opts: commit=0
[   44.109849] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   54.952023] wlan0: no IPv6 routers present
[   55.659018] exe (1783): /proc/1783/oom_adj is deprecated, please use /proc/1783/oom_score_adj instead.

```

lspci
```
00:00.0 Host bridge: Advanced Micro Devices [AMD] RS780 Host Bridge
00:01.0 PCI bridge: Toshiba America Info Systems Device 9602
00:06.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 2)
00:07.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 3)
00:11.0 SATA controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 SATA Controller [AHCI mode]
00:12.0 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
00:12.1 USB Controller: ATI Technologies Inc SB7x0 USB OHCI1 Controller
00:12.2 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB EHCI Controller
00:13.0 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
00:13.1 USB Controller: ATI Technologies Inc SB7x0 USB OHCI1 Controller
00:13.2 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB EHCI Controller
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 3a)
00:14.1 IDE interface: ATI Technologies Inc SB7x0/SB8x0/SB9x0 IDE Controller
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
00:14.3 ISA bridge: ATI Technologies Inc SB7x0/SB8x0/SB9x0 LPC host controller
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 11h Processor HyperTransport Configuration (rev 40)
00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 11h Processor Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 11h Processor DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 11h Processor Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 11h Processor Link Control
01:05.0 VGA compatible controller: ATI Technologies Inc RS780MC [Radeon HD 3100 Graphics]
0e:00.0 Network controller: Realtek Semiconductor Co., Ltd. RTL8187SE Wireless LAN Controller (rev 22)
14:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)
```

contents of /var/log/Xorg.0.log
```
	ATI Radeon X600 (RV370) 5B62 (PCIE),
	ATI Radeon X550 (RV370) 5B63 (PCIE),
	ATI FireGL V3100 (RV370) 5B64 (PCIE),
	ATI FireMV 2200 PCIE (RV370) 5B65 (PCIE),
	ATI Radeon Mobility 9200 (M9+) 5C61 (AGP),
	ATI Radeon Mobility 9200 (M9+) 5C63 (AGP),
	ATI Mobility Radeon X800 XT (M28) (PCIE),
	ATI Mobility FireGL V5100 (M28) (PCIE),
	ATI Mobility Radeon X800 (M28) (PCIE), ATI Radeon X850 5D4C (PCIE),
	ATI Radeon X850 XT PE (R480) (PCIE),
	ATI Radeon X850 SE (R480) (PCIE), ATI Radeon X850 PRO (R480) (PCIE),
	ATI unknown Radeon / FireGL (R480) 5D50 (PCIE),
	ATI Radeon X850 XT (R480) (PCIE),
	ATI Radeon X800XT (R423) 5D57 (PCIE),
	ATI FireGL V5000 (RV410) (PCIE), ATI Radeon X700 XT (RV410) (PCIE),
	ATI Radeon X700 PRO (RV410) (PCIE),
	ATI Radeon X700 SE (RV410) (PCIE), ATI Radeon X700 (RV410) (PCIE),
	ATI Radeon X700 SE (RV410) (PCIE), ATI Radeon X1800,
	ATI Mobility Radeon X1800 XT, ATI Mobility Radeon X1800,
	ATI Mobility FireGL V7200, ATI FireGL V7200, ATI FireGL V5300,
	ATI Mobility FireGL V7100, ATI Radeon X1800, ATI Radeon X1800,
	ATI Radeon X1800, ATI Radeon X1800, ATI Radeon X1800,
	ATI FireGL V7300, ATI FireGL V7350, ATI Radeon X1600, ATI RV505,
	ATI Radeon X1300/X1550, ATI Radeon X1550, ATI M54-GL,
	ATI Mobility Radeon X1400, ATI Radeon X1300/X1550,
	ATI Radeon X1550 64-bit, ATI Mobility Radeon X1300,
	ATI Mobility Radeon X1300, ATI Mobility Radeon X1300,
	ATI Mobility Radeon X1300, ATI Radeon X1300, ATI Radeon X1300,
	ATI RV505, ATI RV505, ATI FireGL V3300, ATI FireGL V3350,
	ATI Radeon X1300, ATI Radeon X1550 64-bit, ATI Radeon X1300/X1550,
	ATI Radeon X1600, ATI Radeon X1300/X1550, ATI Mobility Radeon X1450,
	ATI Radeon X1300/X1550, ATI Mobility Radeon X2300,
	ATI Mobility Radeon X2300, ATI Mobility Radeon X1350,
	ATI Mobility Radeon X1350, ATI Mobility Radeon X1450,
	ATI Radeon X1300, ATI Radeon X1550, ATI Mobility Radeon X1350,
	ATI FireMV 2250, ATI Radeon X1550 64-bit, ATI Radeon X1600,
	ATI Radeon X1650, ATI Radeon X1600, ATI Radeon X1600,
	ATI Mobility FireGL V5200, ATI Mobility Radeon X1600,
	ATI Radeon X1650, ATI Radeon X1650, ATI Radeon X1600,
	ATI Radeon X1300 XT/X1600 Pro, ATI FireGL V3400,
	ATI Mobility FireGL V5250, ATI Mobility Radeon X1700,
	ATI Mobility Radeon X1700 XT, ATI FireGL V5200,
	ATI Mobility Radeon X1700, ATI Radeon X2300HD,
	ATI Mobility Radeon HD 2300, ATI Mobility Radeon HD 2300,
	ATI Radeon X1950, ATI Radeon X1900, ATI Radeon X1950,
	ATI Radeon X1900, ATI Radeon X1900, ATI Radeon X1900,
	ATI Radeon X1900, ATI Radeon X1900, ATI Radeon X1900,
	ATI Radeon X1900, ATI Radeon X1900, ATI Radeon X1900,
	ATI AMD Stream Processor, ATI Radeon X1900, ATI Radeon X1950,
	ATI RV560, ATI RV560, ATI Mobility Radeon X1900, ATI RV560,
	ATI Radeon X1950 GT, ATI RV570, ATI RV570, ATI FireGL V7400,
	ATI RV560, ATI Radeon X1650, ATI Radeon X1650, ATI RV560,
	ATI Radeon 9100 PRO IGP 7834, ATI Radeon Mobility 9200 IGP 7835,
	ATI Radeon X1200, ATI Radeon X1200, ATI Radeon X1200,
	ATI Radeon X1200, ATI Radeon X1200, ATI RS740, ATI RS740M, ATI RS740,
	ATI RS740M, ATI Radeon HD 2900 XT, ATI Radeon HD 2900 XT,
	ATI Radeon HD 2900 XT, ATI Radeon HD 2900 Pro, ATI Radeon HD 2900 GT,
	ATI FireGL V8650, ATI FireGL V8600, ATI FireGL V7600,
	ATI Radeon 4800 Series, ATI Radeon HD 4870 x2,
	ATI Radeon 4800 Series, ATI Radeon HD 4850 x2,
	ATI FirePro V8750 (FireGL), ATI FirePro V7760 (FireGL),
	ATI Mobility RADEON HD 4850, ATI Mobility RADEON HD 4850 X2,
	ATI Radeon 4800 Series, ATI FirePro RV770, AMD FireStream 9270,
	AMD FireStream 9250, ATI FirePro V8700 (FireGL),
	ATI Mobility RADEON HD 4870, ATI Mobility RADEON M98,
	ATI Mobility RADEON HD 4870, ATI Radeon 4800 Series,
	ATI Radeon 4800 Series, ATI FirePro M7750, ATI M98, ATI M98, ATI M98,
	ATI Mobility Radeon HD 4650, ATI Radeon RV730 (AGP),
	ATI Mobility Radeon HD 4670, ATI FirePro M5750,
	ATI Mobility Radeon HD 4670, ATI Radeon RV730 (AGP),
	ATI RV730XT [Radeon HD 4670], ATI RADEON E4600,
	ATI Radeon HD 4600 Series, ATI RV730 PRO [Radeon HD 4650],
	ATI FirePro V7750 (FireGL), ATI FirePro V5700 (FireGL),
	ATI FirePro V3750 (FireGL), ATI Mobility Radeon HD 4830,
	ATI Mobility Radeon HD 4850, ATI FirePro M7740, ATI RV740,
	ATI Radeon HD 4770, ATI Radeon HD 4700 Series, ATI Radeon HD 4770,
	ATI FirePro M5750, ATI RV610, ATI Radeon HD 2400 XT,
	ATI Radeon HD 2400 Pro, ATI Radeon HD 2400 PRO AGP, ATI FireGL V4000,
	ATI RV610, ATI Radeon HD 2350, ATI Mobility Radeon HD 2400 XT,
	ATI Mobility Radeon HD 2400, ATI RADEON E2400, ATI RV610,
	ATI FireMV 2260, ATI RV670, ATI Radeon HD3870,
	ATI Mobility Radeon HD 3850, ATI Radeon HD3850,
	ATI Mobility Radeon HD 3850 X2, ATI RV670,
	ATI Mobility Radeon HD 3870, ATI Mobility Radeon HD 3870 X2,
	ATI Radeon HD3870 X2, ATI FireGL V7700, ATI Radeon HD3850,
	ATI Radeon HD3690, AMD Firestream 9170, ATI Radeon HD 4550,
	ATI Radeon RV710, ATI Radeon RV710, ATI Radeon RV710,
	ATI Radeon HD 4350, ATI Mobility Radeon 4300 Series,
	ATI Mobility Radeon 4500 Series, ATI Mobility Radeon 4500 Series,
	ATI FirePro RG220, ATI Mobility Radeon 4330, ATI RV630,
	ATI Mobility Radeon HD 2600, ATI Mobility Radeon HD 2600 XT,
	ATI Radeon HD 2600 XT AGP, ATI Radeon HD 2600 Pro AGP,
	ATI Radeon HD 2600 XT, ATI Radeon HD 2600 Pro, ATI Gemini RV630,
	ATI Gemini Mobility Radeon HD 2600 XT, ATI FireGL V5600,
	ATI FireGL V3600, ATI Radeon HD 2600 LE,
	ATI Mobility FireGL Graphics Processor, ATI Radeon HD 3470,
	ATI Mobility Radeon HD 3430, ATI Mobility Radeon HD 3400 Series,
	ATI Radeon HD 3450, ATI Radeon HD 3450, ATI Radeon HD 3430,
	ATI Radeon HD 3450, ATI FirePro V3700, ATI FireMV 2450,
	ATI FireMV 2260, ATI FireMV 2260, ATI Radeon HD 3600 Series,
	ATI Radeon HD 3650 AGP, ATI Radeon HD 3600 PRO,
	ATI Radeon HD 3600 XT, ATI Radeon HD 3600 PRO,
	ATI Mobility Radeon HD 3650, ATI Mobility Radeon HD 3670,
	ATI Mobility FireGL V5700, ATI Mobility FireGL V5725,
	ATI Radeon HD 3200 Graphics, ATI Radeon 3100 Graphics,
	ATI Radeon HD 3200 Graphics, ATI Radeon 3100 Graphics,
	ATI Radeon HD 3300 Graphics, ATI Radeon HD 3200 Graphics,
	ATI Radeon 3000 Graphics, ATI Radeon HD 4200, ATI Radeon 4100,
	ATI Mobility Radeon HD 4200, ATI Mobility Radeon 4100,
	ATI Radeon HD 4290, ATI Radeon HD 4250, AMD Radeon HD 6310 Graphics,
	AMD Radeon HD 6310 Graphics, AMD Radeon HD 6250 Graphics,
	AMD Radeon HD 6250 Graphics, CYPRESS,
	ATI FirePro (FireGL) Graphics Adapter,
	ATI FirePro (FireGL) Graphics Adapter,
	ATI FirePro (FireGL) Graphics Adapter, AMD Firestream 9370,
	AMD Firestream 9350, ATI Radeon HD 5800 Series,
	ATI Radeon HD 5800 Series, ATI Radeon HD 5800 Series,
	ATI Radeon HD 5900 Series, ATI Radeon HD 5900 Series,
	ATI Mobility Radeon HD 5800 Series,
	ATI Mobility Radeon HD 5800 Series,
	ATI FirePro (FireGL) Graphics Adapter,
	ATI FirePro (FireGL) Graphics Adapter,
	ATI Mobility Radeon HD 5800 Series, ATI Radeon HD 5700 Series,
	ATI Radeon HD 5700 Series, ATI Radeon HD 5700 Series,
	ATI Mobility Radeon HD 5000 Series,
	ATI Mobility Radeon HD 5000 Series, ATI Mobility Radeon HD 5570,
	ATI FirePro (FireGL) Graphics Adapter,
	ATI FirePro (FireGL) Graphics Adapter, ATI Radeon HD 5670,
	ATI Radeon HD 5570, ATI Radeon HD 5500 Series, REDWOOD,
	ATI Mobility Radeon HD 5000 Series,
	ATI Mobility Radeon HD 5000 Series, ATI Mobility Radeon Graphics,
	ATI Mobility Radeon Graphics, CEDAR,
	ATI FirePro (FireGL) Graphics Adapter,
	ATI FirePro (FireGL) Graphics Adapter, ATI FirePro 2270, CEDAR,
	ATI Radeon HD 5450, CEDAR, AMD Radeon HD 6900M Series,
	Mobility Radeon HD 6000 Series, BARTS, BARTS,
	Mobility Radeon HD 6000 Series, Mobility Radeon HD 6000 Series,
	BARTS, BARTS, BARTS, BARTS, AMD Radeon HD 6800 Series,
	AMD Radeon HD 6800 Series, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS,
	TURKS, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS, CAICOS, CAICOS,
	CAICOS, CAICOS, CAICOS, CAICOS, CAICOS, CAICOS, CAICOS, CAICOS,
	CAICOS
[    24.531] (II) VESA: driver for VESA chipsets: vesa
[    24.531] (II) FBDEV: driver for framebuffer: fbdev
[    24.531] (++) using VT number 7

[    24.531] (II) Loading /usr/lib/xorg/modules/drivers/radeon_drv.so
[    24.532] (II) [KMS] Kernel modesetting enabled.
[    24.532] (WW) Falling back to old probe method for vesa
[    24.532] (WW) Falling back to old probe method for fbdev
[    24.532] (II) Loading sub module "fbdevhw"
[    24.532] (II) LoadModule: "fbdevhw"
[    24.532] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[    24.532] (II) Module fbdevhw: vendor="X.Org Foundation"
[    24.532] 	compiled for 1.10.1, module version = 0.0.2
[    24.532] 	ABI class: X.Org Video Driver, version 10.0
[    24.532] (II) RADEON(0): Creating default Display subsection in Screen section
	"Default Screen Section" for depth/fbbpp 24/32
[    24.532] (==) RADEON(0): Depth 24, (--) framebuffer bpp 32
[    24.532] (II) RADEON(0): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
[    24.532] (==) RADEON(0): Default visual is TrueColor
[    24.532] (==) RADEON(0): RGB weight 888
[    24.532] (II) RADEON(0): Using 8 bits per RGB (8 bit DAC)
[    24.532] (--) RADEON(0): Chipset: "ATI Radeon 3100 Graphics" (ChipID = 0x9613)
[    24.532] (II) RADEON(0): PCI card detected
[    24.532] drmOpenDevice: node name is /dev/dri/card0
[    24.532] drmOpenDevice: open result is 9, (OK)
[    24.533] drmOpenByBusid: Searching for BusID pci:0000:01:05.0
[    24.533] drmOpenDevice: node name is /dev/dri/card0
[    24.533] drmOpenDevice: open result is 9, (OK)
[    24.533] drmOpenByBusid: drmOpenMinor returns 9
[    24.533] drmOpenByBusid: drmGetBusid reports pci:0000:01:05.0
[    24.533] (II) RADEON(0): KMS Color Tiling: disabled
[    24.533] (II) RADEON(0): KMS Pageflipping: enabled
[    24.533] (II) RADEON(0): SwapBuffers wait for vsync: enabled
[    24.552] (II) RADEON(0): Output VGA-0 has no monitor section
[    24.552] (II) RADEON(0): Output LVDS has no monitor section
[    24.568] (II) RADEON(0): EDID for output VGA-0
[    24.568] (II) RADEON(0): EDID for output LVDS
[    24.568] (II) RADEON(0): Manufacturer: AUO  Model: 12ec  Serial#: 0
[    24.568] (II) RADEON(0): Year: 2008  Week: 1
[    24.568] (II) RADEON(0): EDID Version: 1.3
[    24.568] (II) RADEON(0): Digital Display Input
[    24.568] (II) RADEON(0): Max Image Size [cm]: horiz.: 34  vert.: 19
[    24.568] (II) RADEON(0): Gamma: 2.20
[    24.568] (II) RADEON(0): No DPMS capabilities specified
[    24.568] (II) RADEON(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
[    24.568] (II) RADEON(0): First detailed timing is preferred mode
[    24.568] (II) RADEON(0): redX: 0.640 redY: 0.342   greenX: 0.310 greenY: 0.580
[    24.568] (II) RADEON(0): blueX: 0.150 blueY: 0.120   whiteX: 0.313 whiteY: 0.329
[    24.568] (II) RADEON(0): Manufacturer's mask: 0
[    24.568] (II) RADEON(0): Supported detailed timing:
[    24.568] (II) RADEON(0): clock: 72.0 MHz   Image Size:  344 x 193 mm
[    24.568] (II) RADEON(0): h_active: 1366  h_sync: 1414  h_sync_end 1446 h_blank_end 1486 h_border: 0
[    24.568] (II) RADEON(0): v_active: 768  v_sync: 771  v_sync_end 775 v_blanking: 806 v_border: 0
[    24.568] (II) RADEON(0): Unknown vendor-specific block f
[    24.568] (II) RADEON(0):  AUO
[    24.568] (II) RADEON(0):  B156XW01 V2
[    24.568] (II) RADEON(0): EDID (in hex):
[    24.568] (II) RADEON(0): 	00ffffffffffff0006afec1200000000
[    24.568] (II) RADEON(0): 	01120103802213780ae6b5a3574f9426
[    24.568] (II) RADEON(0): 	1e505400000001010101010101010101
[    24.568] (II) RADEON(0): 	010101010101201c5678500026303020
[    24.568] (II) RADEON(0): 	340058c1100000180000000f00000000
[    24.568] (II) RADEON(0): 	00000000000000000020000000fe0041
[    24.569] (II) RADEON(0): 	554f0a202020202020202020000000fe
[    24.569] (II) RADEON(0): 	004231353658573031205632200a0026
[    24.569] (II) RADEON(0): Printing probed modes for output LVDS
[    24.569] (II) RADEON(0): Modeline "1366x768"x60.1   72.00  1366 1414 1446 1486  768 771 775 806 -hsync -vsync (48.5 kHz)
[    24.569] (II) RADEON(0): Modeline "1280x720"x59.9   74.50  1280 1344 1472 1664  720 723 728 748 -hsync +vsync (44.8 kHz)
[    24.569] (II) RADEON(0): Modeline "1152x768"x59.8   71.75  1152 1216 1328 1504  768 771 781 798 -hsync +vsync (47.7 kHz)
[    24.569] (II) RADEON(0): Modeline "1024x768"x59.9   63.50  1024 1072 1176 1328  768 771 775 798 -hsync +vsync (47.8 kHz)
[    24.569] (II) RADEON(0): Modeline "800x600"x59.9   38.25  800 832 912 1024  600 603 607 624 -hsync +vsync (37.4 kHz)
[    24.569] (II) RADEON(0): Modeline "848x480"x59.7   31.50  848 872 952 1056  480 483 493 500 -hsync +vsync (29.8 kHz)
[    24.569] (II) RADEON(0): Modeline "720x480"x59.7   26.75  720 744 808 896  480 483 493 500 -hsync +vsync (29.9 kHz)
[    24.569] (II) RADEON(0): Modeline "640x480"x59.4   23.75  640 664 720 800  480 483 487 500 -hsync +vsync (29.7 kHz)
[    24.569] (II) RADEON(0): Output VGA-0 disconnected
[    24.569] (II) RADEON(0): Output LVDS connected
[    24.569] (II) RADEON(0): Using exact sizes for initial modes
[    24.569] (II) RADEON(0): Output LVDS using initial mode 1366x768
[    24.569] (II) RADEON(0): Using default gamma of (1.0, 1.0, 1.0) unless otherwise stated.
[    24.569] (II) RADEON(0): mem size init: gart size :1fdff000 vram size: s:10000000 visible:fba0000
[    24.569] (II) RADEON(0): EXA: Driver will allow EXA pixmaps in VRAM
[    24.569] (==) RADEON(0): DPI set to (96, 96)
[    24.569] (II) Loading sub module "fb"
[    24.569] (II) LoadModule: "fb"
[    24.569] (II) Loading /usr/lib/xorg/modules/libfb.so
[    24.569] (II) Module fb: vendor="X.Org Foundation"
[    24.569] 	compiled for 1.10.1, module version = 1.0.0
[    24.569] 	ABI class: X.Org ANSI C Emulation, version 0.4
[    24.569] (II) Loading sub module "ramdac"
[    24.569] (II) LoadModule: "ramdac"
[    24.569] (II) Module "ramdac" already built-in
[    24.570] (II) Loading sub module "exa"
[    24.570] (II) LoadModule: "exa"
[    24.570] (II) Loading /usr/lib/xorg/modules/libexa.so
[    24.570] (II) Module exa: vendor="X.Org Foundation"
[    24.570] 	compiled for 1.10.1, module version = 2.5.0
[    24.570] 	ABI class: X.Org Video Driver, version 10.0
[    24.570] (II) UnloadModule: "vesa"
[    24.570] (II) Unloading vesa
[    24.570] (II) UnloadModule: "fbdev"
[    24.570] (II) Unloading fbdev
[    24.570] (II) UnloadModule: "fbdevhw"
[    24.570] (II) Unloading fbdevhw
[    24.570] (--) Depth 24 pixmap format is 32 bpp
[    24.570] (II) RADEON(0): [DRI2] Setup complete
[    24.570] (II) RADEON(0): [DRI2]   DRI driver: r600
[    24.570] (II) RADEON(0): Front buffer size: 4224K
[    24.570] (II) RADEON(0): VRAM usage limit set to 228096K
[    24.570] (==) RADEON(0): Backing store disabled
[    24.570] (II) RADEON(0): Direct rendering enabled
[    24.570] (II) RADEON(0): Setting EXA maxPitchBytes
[    24.570] (II) EXA(0): Driver allocated offscreen pixmaps
[    24.570] (II) EXA(0): Driver registered support for the following operations:
[    24.570] (II)         Solid
[    24.570] (II)         Copy
[    24.570] (II)         Composite (RENDER acceleration)
[    24.570] (II)         UploadToScreen
[    24.570] (II)         DownloadFromScreen
[    24.571] (II) RADEON(0): Acceleration enabled
[    24.571] (==) RADEON(0): DPMS enabled
[    24.571] (==) RADEON(0): Silken mouse enabled
[    24.571] (II) RADEON(0): Set up textured video
[    24.571] (II) RADEON(0): RandR 1.2 enabled, ignore the following RandR disabled message.
[    24.571] (--) RandR disabled
[    24.571] (II) Initializing built-in extension Generic Event Extension
[    24.571] (II) Initializing built-in extension SHAPE
[    24.571] (II) Initializing built-in extension MIT-SHM
[    24.571] (II) Initializing built-in extension XInputExtension
[    24.571] (II) Initializing built-in extension XTEST
[    24.571] (II) Initializing built-in extension BIG-REQUESTS
[    24.571] (II) Initializing built-in extension SYNC
[    24.571] (II) Initializing built-in extension XKEYBOARD
[    24.571] (II) Initializing built-in extension XC-MISC
[    24.571] (II) Initializing built-in extension SECURITY
[    24.571] (II) Initializing built-in extension XINERAMA
[    24.571] (II) Initializing built-in extension XFIXES
[    24.571] (II) Initializing built-in extension RENDER
[    24.571] (II) Initializing built-in extension RANDR
[    24.571] (II) Initializing built-in extension COMPOSITE
[    24.571] (II) Initializing built-in extension DAMAGE
[    24.571] (II) Initializing built-in extension GESTURE
[    24.596] (II) AIGLX: Trying DRI driver /usr/lib/dri/r600_dri.so
[    24.606] (II) AIGLX: enabled GLX_MESA_copy_sub_buffer
[    24.606] (II) AIGLX: enabled GLX_INTEL_swap_event
[    24.606] (II) AIGLX: enabled GLX_SGI_swap_control and GLX_MESA_swap_control
[    24.606] (II) AIGLX: enabled GLX_SGI_make_current_read
[    24.606] (II) AIGLX: GLX_EXT_texture_from_pixmap backed by buffer objects
[    24.609] (II) AIGLX: Loaded and initialized r600
[    24.609] (II) GLX: Initialized DRI2 GL provider for screen 0
[    24.610] (II) RADEON(0): Setting screen physical size to 361 x 203
[    24.639] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    24.667] (II) config/udev: Adding input device Power Button (/dev/input/event2)
[    24.667] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    24.667] (II) LoadModule: "evdev"
[    24.668] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    24.668] (II) Module evdev: vendor="X.Org Foundation"
[    24.668] 	compiled for 1.10.0.902, module version = 2.6.0
[    24.668] 	Module class: X.Org XInput Driver
[    24.668] 	ABI class: X.Org XInput driver, version 12.3
[    24.668] (II) Using input driver 'evdev' for 'Power Button'
[    24.668] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    24.668] (**) Power Button: always reports core events
[    24.668] (**) Power Button: Device: "/dev/input/event2"
[    24.668] (--) Power Button: Found keys
[    24.668] (II) Power Button: Configuring as keyboard
[    24.668] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input2/event2"
[    24.669] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[    24.669] (**) Option "xkb_rules" "evdev"
[    24.669] (**) Option "xkb_model" "pc105"
[    24.669] (**) Option "xkb_layout" "us"
[    24.805] (II) config/udev: Adding input device Video Bus (/dev/input/event4)
[    24.805] (**) Video Bus: Applying InputClass "evdev keyboard catchall"
[    24.805] (II) Using input driver 'evdev' for 'Video Bus'
[    24.805] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    24.805] (**) Video Bus: always reports core events
[    24.805] (**) Video Bus: Device: "/dev/input/event4"
[    24.805] (--) Video Bus: Found keys
[    24.805] (II) Video Bus: Configuring as keyboard
[    24.805] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0A08:00/device:34/LNXVIDEO:01/input/input4/event4"
[    24.805] (II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD)
[    24.805] (**) Option "xkb_rules" "evdev"
[    24.805] (**) Option "xkb_model" "pc105"
[    24.805] (**) Option "xkb_layout" "us"
[    24.806] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[    24.806] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    24.806] (II) Using input driver 'evdev' for 'Power Button'
[    24.806] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    24.806] (**) Power Button: always reports core events
[    24.806] (**) Power Button: Device: "/dev/input/event0"
[    24.806] (--) Power Button: Found keys
[    24.806] (II) Power Button: Configuring as keyboard
[    24.806] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0/event0"
[    24.806] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[    24.806] (**) Option "xkb_rules" "evdev"
[    24.806] (**) Option "xkb_model" "pc105"
[    24.806] (**) Option "xkb_layout" "us"
[    24.807] (II) config/udev: Adding input device Lid Switch (/dev/input/event1)
[    24.807] (II) No input driver/identifier specified (ignoring)
[    24.813] (II) config/udev: Adding input device 2.4GHz 2way RF Receiver (/dev/input/event5)
[    24.813] (**) 2.4GHz 2way RF Receiver: Applying InputClass "evdev pointer catchall"
[    24.813] (**) 2.4GHz 2way RF Receiver: Applying InputClass "evdev keyboard catchall"
[    24.813] (II) Using input driver 'evdev' for '2.4GHz 2way RF Receiver'
[    24.813] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    24.814] (**) 2.4GHz 2way RF Receiver: always reports core events
[    24.814] (**) 2.4GHz 2way RF Receiver: Device: "/dev/input/event5"
[    24.814] (--) 2.4GHz 2way RF Receiver: Found 12 mouse buttons
[    24.814] (--) 2.4GHz 2way RF Receiver: Found scroll wheel(s)
[    24.814] (--) 2.4GHz 2way RF Receiver: Found relative axes
[    24.814] (--) 2.4GHz 2way RF Receiver: Found x and y relative axes
[    24.814] (--) 2.4GHz 2way RF Receiver: Found absolute axes
[    24.814] (II) evdev-grail: failed to open grail, no gesture support
[    24.814] (--) 2.4GHz 2way RF Receiver: Found keys
[    24.814] (II) 2.4GHz 2way RF Receiver: Configuring as mouse
[    24.814] (II) 2.4GHz 2way RF Receiver: Configuring as keyboard
[    24.814] (II) 2.4GHz 2way RF Receiver: Adding scrollwheel support
[    24.814] (**) 2.4GHz 2way RF Receiver: YAxisMapping: buttons 4 and 5
[    24.814] (**) 2.4GHz 2way RF Receiver: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    24.814] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:12.2/usb1/1-1/1-1.1/1-1.1:1.1/input/input5/event5"
[    24.814] (II) XINPUT: Adding extended input device "2.4GHz 2way RF Receiver" (type: KEYBOARD)
[    24.814] (**) Option "xkb_rules" "evdev"
[    24.814] (**) Option "xkb_model" "pc105"
[    24.814] (**) Option "xkb_layout" "us"
[    24.815] (II) 2.4GHz 2way RF Receiver: initialized for relative axes.
[    24.876] (WW) 2.4GHz 2way RF Receiver: ignoring absolute axes.
[    24.876] (**) 2.4GHz 2way RF Receiver: (accel) keeping acceleration scheme 1
[    24.876] (**) 2.4GHz 2way RF Receiver: (accel) acceleration profile 0
[    24.877] (**) 2.4GHz 2way RF Receiver: (accel) acceleration factor: 2.000
[    24.877] (**) 2.4GHz 2way RF Receiver: (accel) acceleration threshold: 4
[    24.877] (II) config/udev: Adding input device 2.4GHz 2way RF Receiver (/dev/input/mouse0)
[    24.877] (II) No input driver/identifier specified (ignoring)
[    24.879] (II) config/udev: Adding input device HDA ATI SB Headphone (/dev/input/event6)
[    24.879] (II) No input driver/identifier specified (ignoring)
[    24.881] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event3)
[    24.881] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[    24.881] (II) Using input driver 'evdev' for 'AT Translated Set 2 keyboard'
[    24.881] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    24.881] (**) AT Translated Set 2 keyboard: always reports core events
[    24.881] (**) AT Translated Set 2 keyboard: Device: "/dev/input/event3"
[    24.881] (--) AT Translated Set 2 keyboard: Found keys
[    24.881] (II) AT Translated Set 2 keyboard: Configuring as keyboard
[    24.881] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio0/input/input3/event3"
[    24.881] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD)
[    24.881] (**) Option "xkb_rules" "evdev"
[    24.881] (**) Option "xkb_model" "pc105"
[    24.881] (**) Option "xkb_layout" "us"
[    24.882] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/event7)
[    24.882] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "evdev touchpad catchall"
[    24.882] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "touchpad catchall"
[    24.882] (II) LoadModule: "synaptics"
[    24.882] (II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
[    24.883] (II) Module synaptics: vendor="X.Org Foundation"
[    24.883] 	compiled for 1.10.0.902, module version = 1.3.99
[    24.883] 	Module class: X.Org XInput Driver
[    24.883] 	ABI class: X.Org XInput driver, version 12.3
[    24.883] (II) Using input driver 'synaptics' for 'SynPS/2 Synaptics TouchPad'
[    24.883] (II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
[    24.883] (**) SynPS/2 Synaptics TouchPad: always reports core events
[    24.883] (**) Option "Device" "/dev/input/event7"
[    24.883] (--) SynPS/2 Synaptics TouchPad: x-axis range 1472 - 5772
[    24.883] (--) SynPS/2 Synaptics TouchPad: y-axis range 1408 - 5086
[    24.883] (--) SynPS/2 Synaptics TouchPad: pressure range 0 - 255
[    24.883] (--) SynPS/2 Synaptics TouchPad: finger width range 0 - 15
[    24.883] (--) SynPS/2 Synaptics TouchPad: buttons: left right
[    24.883] (--) SynPS/2 Synaptics TouchPad: touchpad found
[    24.883] (**) SynPS/2 Synaptics TouchPad: always reports core events
[    24.883] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio1/input/input7/event7"
[    24.883] (II) XINPUT: Adding extended input device "SynPS/2 Synaptics TouchPad" (type: TOUCHPAD)
[    24.883] (**) SynPS/2 Synaptics TouchPad: (accel) MinSpeed is now constant deceleration 2.5
[    24.883] (**) SynPS/2 Synaptics TouchPad: MaxSpeed is now 1.75
[    24.883] (**) SynPS/2 Synaptics TouchPad: AccelFactor is now 0.035
[    24.883] (**) SynPS/2 Synaptics TouchPad: (accel) keeping acceleration scheme 1
[    24.883] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration profile 1
[    24.883] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration factor: 2.000
[    24.883] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration threshold: 4
[    24.884] (II) SynPS/2 Synaptics TouchPad: failed to open grail, no gesture support
[    24.884] (--) SynPS/2 Synaptics TouchPad: touchpad found
[    24.884] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/mouse1)
[    24.884] (II) No input driver/identifier specified (ignoring)
[    26.048] (II) RADEON(0): EDID vendor "AUO", prod id 4844
[    26.048] (II) RADEON(0): Printing DDC gathered Modelines:
[    26.048] (II) RADEON(0): Modeline "1366x768"x0.0   72.00  1366 1414 1446 1486  768 771 775 806 -hsync -vsync (48.5 kHz)
[    26.068] (II) RADEON(0): EDID vendor "AUO", prod id 4844
[    26.068] (II) RADEON(0): Printing DDC gathered Modelines:
[    26.068] (II) RADEON(0): Modeline "1366x768"x0.0   72.00  1366 1414 1446 1486  768 771 775 806 -hsync -vsync (48.5 kHz)
[    26.104] (II) RADEON(0): EDID vendor "AUO", prod id 4844
[    26.104] (II) RADEON(0): Printing DDC gathered Modelines:
[    26.104] (II) RADEON(0): Modeline "1366x768"x0.0   72.00  1366 1414 1446 1486  768 771 775 806 -hsync -vsync (48.5 kHz)
[    26.120] (II) RADEON(0): EDID vendor "AUO", prod id 4844
[    26.120] (II) RADEON(0): Printing DDC gathered Modelines:
[    26.120] (II) RADEON(0): Modeline "1366x768"x0.0   72.00  1366 1414 1446 1486  768 771 775 806 -hsync -vsync (48.5 kHz)
[    35.628] (II) RADEON(0): EDID vendor "AUO", prod id 4844
[    35.628] (II) RADEON(0): Printing DDC gathered Modelines:
[    35.628] (II) RADEON(0): Modeline "1366x768"x0.0   72.00  1366 1414 1446 1486  768 771 775 806 -hsync -vsync (48.5 kHz)
[    35.648] (II) RADEON(0): EDID vendor "AUO", prod id 4844
[    35.648] (II) RADEON(0): Printing DDC gathered Modelines:
[    35.648] (II) RADEON(0): Modeline "1366x768"x0.0   72.00  1366 1414 1446 1486  768 771 775 806 -hsync -vsync (48.5 kHz)
[    35.668] (II) RADEON(0): EDID vendor "AUO", prod id 4844
[    35.668] (II) RADEON(0): Printing DDC gathered Modelines:
[    35.668] (II) RADEON(0): Modeline "1366x768"x0.0   72.00  1366 1414 1446 1486  768 771 775 806 -hsync -vsync (48.5 kHz)
[    35.688] (II) RADEON(0): EDID vendor "AUO", prod id 4844
[    35.688] (II) RADEON(0): Printing DDC gathered Modelines:
[    35.688] (II) RADEON(0): Modeline "1366x768"x0.0   72.00  1366 1414 1446 1486  768 771 775 806 -hsync -vsync (48.5 kHz)
[    36.156] (II) RADEON(0): EDID vendor "AUO", prod id 4844
[    36.156] (II) RADEON(0): Printing DDC gathered Modelines:
[    36.156] (II) RADEON(0): Modeline "1366x768"x0.0   72.00  1366 1414 1446 1486  768 771 775 806 -hsync -vsync (48.5 kHz)
[    42.196] (II) RADEON(0): EDID vendor "AUO", prod id 4844
[    42.196] (II) RADEON(0): Printing DDC gathered Modelines:
[    42.196] (II) RADEON(0): Modeline "1366x768"x0.0   72.00  1366 1414 1446 1486  768 771 775 806 -hsync -vsync (48.5 kHz)

```

Some of the output is cut off... it didn't fit :(

---

### Post by snowpine on 2011-05-02
10.04 is very stable and will be supported with bug fixes and security patches through April 2013.

---

