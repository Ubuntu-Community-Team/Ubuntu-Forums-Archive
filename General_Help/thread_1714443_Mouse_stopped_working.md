---
title: "Mouse stopped working"
date: 2011-03-25
forum: General Help
---

### Post by Kryzm on 2011-03-25
I just installed Ubuntu about a month ago on my HP Pavilion dv5, and starting today, I have had trouble with my trackpad mouse. It began giving me issues involving not selecting text, etc. after I'd had my computer running for a little while. I tried "killall gnome-panel nautilus" since that usually seems to help with little issues like this, but when I CTRL-F7'd back to my GUI, I couldn't move the mouse at all. I restarted my computer, was able to move the mouse for a few seconds, then it locked up on me again. I just plugged in a wired mouse, and it works.

Thoughts? I don't really want to have to carry a mouse with me.

---

### Post by ubudog on 2011-03-25
Hi there!  

Type dmesg into a terminal and post the output here (in a code block, or it will take up the whole page).  That will give us some information, and maybe an error message right before the mouse crashes.  If you need to open the terminal without the mouse, press alt>f2, then type gnome-terminal.  

```
dmesg
```

I hope this helps.  :-)

---

### Post by Kryzm on 2011-03-25
Luckily, I have hotkeys set up for most of the things I need.


```

[    0.431278] pci_bus 0000:0a: resource 4 [io  0x0000-0x0cf7]
[    0.431280] pci_bus 0000:0a: resource 5 [io  0x0d00-0xffff]
[    0.431283] pci_bus 0000:0a: resource 6 [mem 0x000a0000-0x000bffff]
[    0.431285] pci_bus 0000:0a: resource 7 [mem 0xc0000000-0xfebfffff]
[    0.431330] NET: Registered protocol family 2
[    0.431401] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.431668] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.432091] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.432309] TCP: Hash tables configured (established 131072 bind 65536)
[    0.432311] TCP reno registered
[    0.432314] UDP hash table entries: 512 (order: 2, 16384 bytes)
[    0.432322] UDP-Lite hash table entries: 512 (order: 2, 16384 bytes)
[    0.432406] NET: Registered protocol family 1
[    0.432798] pci 0000:01:00.0: Boot video device
[    0.432825] PCI: CLS 64 bytes, default 64
[    0.432848] Simple Boot Flag value 0x5 read from CMOS RAM was invalid
[    0.432850] Simple Boot Flag at 0x44 set to 0x1
[    0.433033] cpufreq-nforce2: No nForce2 chipset.
[    0.433063] Scanning for low memory corruption every 60 seconds
[    0.433197] audit: initializing netlink socket (disabled)
[    0.433206] type=2000 audit(1301054037.428:1): initialized
[    0.439343] Freeing initrd memory: 10488k freed
[    0.444934] highmem bounce pool size: 64 pages
[    0.444941] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    0.446477] VFS: Disk quotas dquot_6.5.2
[    0.446547] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.447177] fuse init (API version 7.14)
[    0.447274] msgmni has been set to 1632
[    0.449926] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.449930] io scheduler noop registered
[    0.449932] io scheduler deadline registered
[    0.449946] io scheduler cfq registered (default)
[    0.450085] pcieport 0000:00:01.0: setting latency timer to 64
[    0.450112]   alloc irq_desc for 40 on node -1
[    0.450114]   alloc kstat_irqs on node -1
[    0.450124] pcieport 0000:00:01.0: irq 40 for MSI/MSI-X
[    0.450200] pcieport 0000:00:1c.0: setting latency timer to 64
[    0.450232]   alloc irq_desc for 41 on node -1
[    0.450234]   alloc kstat_irqs on node -1
[    0.450241] pcieport 0000:00:1c.0: irq 41 for MSI/MSI-X
[    0.450323] pcieport 0000:00:1c.1: setting latency timer to 64
[    0.450355]   alloc irq_desc for 42 on node -1
[    0.450357]   alloc kstat_irqs on node -1
[    0.450364] pcieport 0000:00:1c.1: irq 42 for MSI/MSI-X
[    0.450447] pcieport 0000:00:1c.2: setting latency timer to 64
[    0.450479]   alloc irq_desc for 43 on node -1
[    0.450480]   alloc kstat_irqs on node -1
[    0.450487] pcieport 0000:00:1c.2: irq 43 for MSI/MSI-X
[    0.450574] pcieport 0000:00:1c.3: setting latency timer to 64
[    0.450606]   alloc irq_desc for 44 on node -1
[    0.450608]   alloc kstat_irqs on node -1
[    0.450615] pcieport 0000:00:1c.3: irq 44 for MSI/MSI-X
[    0.450702] pcieport 0000:00:1c.4: setting latency timer to 64
[    0.450733]   alloc irq_desc for 45 on node -1
[    0.450735]   alloc kstat_irqs on node -1
[    0.450742] pcieport 0000:00:1c.4: irq 45 for MSI/MSI-X
[    0.450829] pcieport 0000:00:1c.5: setting latency timer to 64
[    0.450861]   alloc irq_desc for 46 on node -1
[    0.450863]   alloc kstat_irqs on node -1
[    0.450869] pcieport 0000:00:1c.5: irq 46 for MSI/MSI-X
[    0.450982] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.451004] Firmware did not grant requested _OSC control
[    0.451014] Firmware did not grant requested _OSC control
[    0.451023] Firmware did not grant requested _OSC control
[    0.451031] Firmware did not grant requested _OSC control
[    0.451040] Firmware did not grant requested _OSC control
[    0.451048] Firmware did not grant requested _OSC control
[    0.451057] Firmware did not grant requested _OSC control
[    0.451080] Firmware did not grant requested _OSC control
[    0.451089] Firmware did not grant requested _OSC control
[    0.451097] Firmware did not grant requested _OSC control
[    0.451106] Firmware did not grant requested _OSC control
[    0.451114] Firmware did not grant requested _OSC control
[    0.451123] Firmware did not grant requested _OSC control
[    0.451131] Firmware did not grant requested _OSC control
[    0.451140] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.451237] intel_idle: MWAIT substates: 0x3122220
[    0.451240] intel_idle: does not run on family 6 model 23
[    0.451629] ACPI: AC Adapter [ACAD] (on-line)
[    0.451712] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0
[    0.451718] ACPI: Power Button [PWRB]
[    0.451783] input: Lid Switch as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0D:00/input/input1
[    0.452086] ACPI: Lid Switch [LID0]
[    0.452134] input: Sleep Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0E:00/input/input2
[    0.452138] ACPI: Sleep Button [SLPB]
[    0.452206] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input3
[    0.452210] ACPI: Power Button [PWRF]
[    0.452709] ACPI: acpi_idle registered with cpuidle
[    0.452910] Monitor-Mwait will be used to enter C-1 state
[    0.452931] Monitor-Mwait will be used to enter C-2 state
[    0.452949] Monitor-Mwait will be used to enter C-3 state
[    0.452955] Marking TSC unstable due to TSC halts in idle
[    0.452997] Switching to clocksource hpet
[    0.458622] [Firmware Bug]: Invalid critical threshold (0)
[    0.459404] thermal LNXTHERM:01: registered as thermal_zone0
[    0.459413] ACPI: Thermal Zone [TZ01] (41 C)
[    0.459501] ERST: Table is not found!
[    0.459563] isapnp: Scanning for PnP cards...
[    0.459820] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    0.461438] brd: module loaded
[    0.462023] loop: module loaded
[    0.462561] Fixed MDIO Bus: probed
[    0.462595] PPP generic driver version 2.4.2
[    0.462627] tun: Universal TUN/TAP device driver, 1.6
[    0.462629] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.462712] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.462732] ehci_hcd 0000:00:1a.7: PCI INT D -> GSI 19 (level, low) -> IRQ 19
[    0.462744] ehci_hcd 0000:00:1a.7: setting latency timer to 64
[    0.462748] ehci_hcd 0000:00:1a.7: EHCI Host Controller
[    0.462782] ehci_hcd 0000:00:1a.7: new USB bus registered, assigned bus number 1
[    0.462808] ehci_hcd 0000:00:1a.7: debug port 1
[    0.466708] ehci_hcd 0000:00:1a.7: cache line size of 64 is not supported
[    0.466725] ehci_hcd 0000:00:1a.7: irq 19, io mem 0xdf305c00
[    0.480031] ehci_hcd 0000:00:1a.7: USB 2.0 started, EHCI 1.00
[    0.480145] hub 1-0:1.0: USB hub found
[    0.480150] hub 1-0:1.0: 4 ports detected
[    0.480306]   alloc irq_desc for 20 on node -1
[    0.480309]   alloc kstat_irqs on node -1
[    0.480314] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    0.480325] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    0.480328] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    0.480362] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 2
[    0.480401] ehci_hcd 0000:00:1d.7: debug port 1
[    0.484287] ehci_hcd 0000:00:1d.7: cache line size of 64 is not supported
[    0.484310] ehci_hcd 0000:00:1d.7: irq 20, io mem 0xdf305800
[    0.492633] ACPI: Battery Slot [BAT0] (battery present)
[    0.500010] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    0.500121] hub 2-0:1.0: USB hub found
[    0.500125] hub 2-0:1.0: 8 ports detected
[    0.500211] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.500227] uhci_hcd: USB Universal Host Controller Interface driver
[    0.500245] uhci_hcd 0000:00:1a.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.500252] uhci_hcd 0000:00:1a.0: setting latency timer to 64
[    0.500255] uhci_hcd 0000:00:1a.0: UHCI Host Controller
[    0.500289] uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 3
[    0.500320] uhci_hcd 0000:00:1a.0: irq 16, io base 0x0000a0e0
[    0.500439] hub 3-0:1.0: USB hub found
[    0.500444] hub 3-0:1.0: 2 ports detected
[    0.500510]   alloc irq_desc for 21 on node -1
[    0.500513]   alloc kstat_irqs on node -1
[    0.500517] uhci_hcd 0000:00:1a.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[    0.500523] uhci_hcd 0000:00:1a.1: setting latency timer to 64
[    0.500526] uhci_hcd 0000:00:1a.1: UHCI Host Controller
[    0.500563] uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus number 4
[    0.500594] uhci_hcd 0000:00:1a.1: irq 21, io base 0x0000a0c0
[    0.500714] hub 4-0:1.0: USB hub found
[    0.500719] hub 4-0:1.0: 2 ports detected
[    0.500790] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    0.500796] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    0.500799] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    0.500832] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 5
[    0.500854] uhci_hcd 0000:00:1d.0: irq 20, io base 0x0000a0a0
[    0.500970] hub 5-0:1.0: USB hub found
[    0.500974] hub 5-0:1.0: 2 ports detected
[    0.501043] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    0.501049] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    0.501052] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    0.501089] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 6
[    0.501110] uhci_hcd 0000:00:1d.1: irq 19, io base 0x0000a080
[    0.501228] hub 6-0:1.0: USB hub found
[    0.501232] hub 6-0:1.0: 2 ports detected
[    0.501298] uhci_hcd 0000:00:1d.2: PCI INT D -> GSI 16 (level, low) -> IRQ 16
[    0.501304] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    0.501307] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    0.501340] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 7
[    0.501364] uhci_hcd 0000:00:1d.2: irq 16, io base 0x0000a060
[    0.501489] hub 7-0:1.0: USB hub found
[    0.501494] hub 7-0:1.0: 2 ports detected
[    0.501561] uhci_hcd 0000:00:1d.3: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.501566] uhci_hcd 0000:00:1d.3: setting latency timer to 64
[    0.501570] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[    0.501602] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 8
[    0.501635] uhci_hcd 0000:00:1d.3: irq 18, io base 0x0000a040
[    0.501755] hub 8-0:1.0: USB hub found
[    0.501759] hub 8-0:1.0: 2 ports detected
[    0.501899] PNP: PS/2 Controller [PNP0303:KBC,PNP0f13:MOUE] at 0x60,0x64 irq 1,12
[    0.522228] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.522235] serio: i8042 AUX port at 0x60,0x64 irq 12
[    0.522298] mice: PS/2 mouse device common for all mice
[    0.522449] rtc_cmos 00:04: RTC can wake from S4
[    0.522484] rtc_cmos 00:04: rtc core: registered rtc_cmos as rtc0
[    0.522508] rtc0: alarms up to one month, 242 bytes nvram, hpet irqs
[    0.522609] device-mapper: uevent: version 1.0.3
[    0.522706] device-mapper: ioctl: 4.17.0-ioctl (2010-03-05) initialised: [email]dm-devel@redhat.com[/email]
[    0.522768] device-mapper: multipath: version 1.1.1 loaded
[    0.522770] device-mapper: multipath round-robin: version 1.0.0 loaded
[    0.522881] EISA: Probing bus 0 at eisa.0
[    0.522884] EISA: Cannot allocate resource for mainboard
[    0.522886] Cannot allocate resource for EISA slot 1
[    0.522888] Cannot allocate resource for EISA slot 2
[    0.522890] Cannot allocate resource for EISA slot 3
[    0.522892] Cannot allocate resource for EISA slot 4
[    0.522894] Cannot allocate resource for EISA slot 5
[    0.522896] Cannot allocate resource for EISA slot 6
[    0.522898] Cannot allocate resource for EISA slot 7
[    0.522900] Cannot allocate resource for EISA slot 8
[    0.522902] EISA: Detected 0 cards.
[    0.523031] cpuidle: using governor ladder
[    0.523139] cpuidle: using governor menu
[    0.523461] TCP cubic registered
[    0.523603] NET: Registered protocol family 10
[    0.523989] lo: Disabled Privacy Extensions
[    0.524246] NET: Registered protocol family 17
[    0.524793] Using IPI No-Shortcut mode
[    0.524870] PM: Resume from disk failed.
[    0.524880] registered taskstats version 1
[    0.525333]   Magic number: 3:365:884
[    0.525398] rtc_cmos 00:04: setting system clock to 2011-03-25 11:53:58 UTC (1301054038)
[    0.525401] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.525402] EDD information not available.
[    0.543248] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input4
[    0.812525] usb 2-4: new high speed USB device using ehci_hcd and address 2
[    0.814534] isapnp: No Plug & Play device found
[    0.814579] Freeing unused kernel memory: 708k freed
[    0.814933] Write protecting the kernel text: 5096k
[    0.815035] Write protecting the kernel read-only data: 2016k
[    0.832090] udev[82]: starting version 163
[    0.935254] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    0.935281] r8169 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    0.935329] r8169 0000:03:00.0: setting latency timer to 64
[    0.935375]   alloc irq_desc for 47 on node -1
[    0.935377]   alloc kstat_irqs on node -1
[    0.935392] r8169 0000:03:00.0: irq 47 for MSI/MSI-X
[    0.935950] r8169 0000:03:00.0: eth0: RTL8168c/8111c at 0xf84c8000, 00:1e:68:a2:68:76, XID 1c4000c0 IRQ 47
[    0.943988] sdhci: Secure Digital Host Controller Interface driver
[    0.943991] sdhci: Copyright(c) Pierre Ossman
[    0.945585] sdhci-pci 0000:06:00.1: SDHCI controller found [197b:2382] (rev 0)
[    0.945611] sdhci-pci 0000:06:00.1: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.945657] sdhci-pci 0000:06:00.1: setting latency timer to 64
[    0.945695] Registered led device: mmc0::
[    0.980920] mmc0: SDHCI controller on PCI [0000:06:00.1] using DMA
[    0.980941] sdhci-pci 0000:06:00.2: SDHCI controller found [197b:2381] (rev 0)
[    0.980967] sdhci-pci 0000:06:00.2: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.980978] sdhci-pci 0000:06:00.2: Refusing to bind to secondary interface.
[    0.980985] sdhci-pci 0000:06:00.2: PCI INT A disabled
[    0.986579] ahci 0000:00:1f.2: version 3.0
[    0.986594] ahci 0000:00:1f.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    0.986637]   alloc irq_desc for 48 on node -1
[    0.986640]   alloc kstat_irqs on node -1
[    0.986650] ahci 0000:00:1f.2: irq 48 for MSI/MSI-X
[    0.986665] ahci 0000:00:1f.2: BIOS update required for suspend/resume
[    0.986737] ahci 0000:00:1f.2: AHCI 0001.0200 32 slots 4 ports 3 Gbps 0x33 impl SATA mode
[    0.986741] ahci 0000:00:1f.2: flags: 64bit ncq sntf ilck pm led clo pmp pio slum part ccc ems sxs 
[    0.986746] ahci 0000:00:1f.2: setting latency timer to 64
[    0.997257] firewire_ohci 0000:06:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.997266] firewire_ohci 0000:06:00.0: setting latency timer to 64
[    1.016616] scsi0 : ahci
[    1.016742] scsi1 : ahci
[    1.016820] scsi2 : ahci
[    1.016907] scsi3 : ahci
[    1.016988] scsi4 : ahci
[    1.017072] scsi5 : ahci
[    1.017307] ata1: SATA max UDMA/133 abar m2048@0xdf305000 port 0xdf305100 irq 48
[    1.017311] ata2: SATA max UDMA/133 abar m2048@0xdf305000 port 0xdf305180 irq 48
[    1.017313] ata3: DUMMY
[    1.017315] ata4: DUMMY
[    1.017318] ata5: SATA max UDMA/133 abar m2048@0xdf305000 port 0xdf305300 irq 48
[    1.017321] ata6: SATA max UDMA/133 abar m2048@0xdf305000 port 0xdf305380 irq 48
[    1.092028] firewire_ohci: Added fw-ohci device 0000:06:00.0, OHCI v1.10, 4 IR + 0 IT contexts, quirks 0x0
[    1.336114] ata6: SATA link down (SStatus 0 SControl 300)
[    1.336134] ata5: SATA link down (SStatus 0 SControl 300)
[    1.384085] usb 7-2: new full speed USB device using uhci_hcd and address 2
[    1.508132] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    1.508149] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    1.510345] ata1.00: ATA-8: WDC WD3200BEVT-60ZCT0, 11.01A11, max UDMA/100
[    1.510349] ata1.00: 625142448 sectors, multi 0: LBA48 NCQ (depth 31/32), AA
[    1.512686] ata1.00: configured for UDMA/100
[    1.520870] ata2.00: ATAPI: Optiarc DVD RW AD-7561S, AH03, max UDMA/100
[    1.528710] scsi 0:0:0:0: Direct-Access     ATA      WDC WD3200BEVT-6 11.0 PQ: 0 ANSI: 5
[    1.528867] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    1.528945] sd 0:0:0:0: [sda] 625142448 512-byte logical blocks: (320 GB/298 GiB)
[    1.529000] sd 0:0:0:0: [sda] Write Protect is off
[    1.529003] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.529027] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.529202]  sda:
[    1.534439] ata2.00: configured for UDMA/100
[    1.549395] scsi 1:0:0:0: CD-ROM            Optiarc  DVD RW AD-7561S  AH03 PQ: 0 ANSI: 5
[    1.554498] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[    1.554501] Uniform CD-ROM driver Revision: 3.20
[    1.554612] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    1.554675] sr 1:0:0:0: Attached scsi generic sg1 type 5
[    1.574658]  sda1 sda2 <
[    1.584663] firewire_core: created device fw0: GUID 00241b0099af1b01, S400
[    1.599418]  sda5 >
[    1.599785] sd 0:0:0:0: [sda] Attached SCSI disk
[    1.916202] EXT4-fs (sda1): INFO: recovery required on readonly filesystem
[    1.916208] EXT4-fs (sda1): write access will be enabled during recovery
[    3.723083] EXT4-fs (sda1): orphan cleanup on readonly fs
[    3.723092] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 1966353
[    3.723166] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 264532
[    3.723186] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 263881
[    3.723204] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 6029382
[    3.723222] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 264219
[    3.723259] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 1966342
[    3.723274] EXT4-fs (sda1): 6 orphan inodes deleted
[    3.723277] EXT4-fs (sda1): recovery complete
[    4.483060] EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: (null)
[   19.354701] udev[430]: starting version 163
[   19.473019] Adding 12286972k swap on /dev/sda5.  Priority:-1 extents:1 across:12286972k 
[   19.797637] type=1400 audit(1301068457.769:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient3" pid=590 comm="apparmor_parser"
[   19.797648] type=1400 audit(1301068457.769:3): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient3" pid=621 comm="apparmor_parser"
[   19.798359] type=1400 audit(1301068457.769:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=590 comm="apparmor_parser"
[   19.798372] type=1400 audit(1301068457.769:5): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=621 comm="apparmor_parser"
[   19.798752] type=1400 audit(1301068457.769:6): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=590 comm="apparmor_parser"
[   19.798768] type=1400 audit(1301068457.769:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=621 comm="apparmor_parser"
[   19.913218] input: HP WMI hotkeys as /devices/virtual/input/input5
[   19.941055] jmb38x_ms 0000:06:00.3: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   19.941063] jmb38x_ms 0000:06:00.3: setting latency timer to 64
[   20.018395] cfg80211: Calling CRDA to update world regulatory domain
[   20.032392] Linux agpgart interface v0.103
[   20.101180] Bluetooth: Core ver 2.15
[   20.101227] NET: Registered protocol family 31
[   20.101230] Bluetooth: HCI device and connection manager initialized
[   20.101232] Bluetooth: HCI socket layer initialized
[   20.114617] lp: driver loaded but no devices found
[   20.177283] Bluetooth: Generic Bluetooth USB driver ver 0.6
[   20.186325] cfg80211: World regulatory domain updated:
[   20.186329]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   20.186332]     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   20.186335]     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   20.186338]     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   20.186341]     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   20.186343]     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   20.198709] Linux video capture interface: v2.00
[   20.203499] usbcore: registered new interface driver btusb
[   20.249414] lirc_dev: IR Remote Control driver registered, major 250 
[   20.275723] uvcvideo: Found UVC 1.00 device HP Webcam (5986:0137)
[   20.277181] input: HP Webcam as /devices/pci0000:00/0000:00:1d.7/usb2/2-4/2-4:1.0/input/input6
[   20.277241] usbcore: registered new interface driver uvcvideo
[   20.277243] USB Video Class driver (v0.1.0)
[   20.286558] acpi device:07: registered as cooling_device2
[   20.286897] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:05/LNXVIDEO:01/input/input7
[   20.286945] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[   20.292999] lirc_ene0100: module is from the staging directory, the quality is unknown, you have been warned.
[   20.293706] enecir 00:0a: lirc_dev: driver enecir registered at minor = 0
[   20.293762] enecir: KB3926C detected, driver support is not complete!
[   20.293765] enecir: chip is 0x3926 - 0x00, 0xc0
[   20.293771] enecir: hardware features:
[   20.293773] enecir: learning and tx off, gpio40_learn off, fan_in off
[   20.293775] enecir: driver has been succesfully loaded
[   20.341714] lis3lv02d: hardware type HPDV5_I found.
[   20.352172] lis3lv02d: 8 bits sensor found
[   20.516163] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
[   20.520586] input: ST LIS3LV02DL Accelerometer as /devices/platform/lis3lv02d/input/input8
[   20.520701] Registered led device: hp::hddprotect
[   20.520717] lis3lv02d driver loaded.
[   20.621413] type=1400 audit(1301068458.593:8): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient3" pid=913 comm="apparmor_parser"
[   20.622140] type=1400 audit(1301068458.593:9): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=913 comm="apparmor_parser"
[   20.622538] type=1400 audit(1301068458.593:10): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=913 comm="apparmor_parser"
[   20.626587] type=1400 audit(1301068458.597:11): apparmor="STATUS" operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" pid=912 comm="apparmor_parser"
[   20.893719] r8169 0000:03:00.0: eth0: link down
[   20.893919] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   21.151850] Synaptics Touchpad, model: 1, fw: 6.5, id: 0x1c0b1, caps: 0xa04751/0xa00000/0x0
[   21.154564] Bluetooth: L2CAP ver 2.14
[   21.154567] Bluetooth: L2CAP socket layer initialized
[   21.232172] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input9
[   21.311607] iwlagn: Intel(R) Wireless WiFi Link AGN driver for Linux, in-tree:
[   21.311610] iwlagn: Copyright(c) 2003-2010 Intel Corporation
[   21.311669] iwlagn 0000:02:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   21.311677] iwlagn 0000:02:00.0: setting latency timer to 64
[   21.311708] iwlagn 0000:02:00.0: Detected Intel(R) WiFi Link 5100 AGN, REV=0x54
[   21.332268] iwlagn 0000:02:00.0: Tunable channels: 13 802.11bg, 24 802.11a channels
[   21.332341]   alloc irq_desc for 49 on node -1
[   21.332343]   alloc kstat_irqs on node -1
[   21.332381] iwlagn 0000:02:00.0: irq 49 for MSI/MSI-X
[   21.513919]   alloc irq_desc for 22 on node -1
[   21.513922]   alloc kstat_irqs on node -1
[   21.513930] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[   21.513979]   alloc irq_desc for 50 on node -1
[   21.513981]   alloc kstat_irqs on node -1
[   21.513991] HDA Intel 0000:00:1b.0: irq 50 for MSI/MSI-X
[   21.514017] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   21.531803] iwlagn 0000:02:00.0: loaded firmware version 8.24.2.12
[   21.588274] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   21.588277] Bluetooth: BNEP filters: protocol multicast
[   21.697412] Bluetooth: SCO (Voice Link) ver 0.6
[   21.697415] Bluetooth: SCO socket layer initialized
[   21.829530] input: HDA Intel Mic at Ext Front Jack as /devices/pci0000:00/0000:00:1b.0/sound/card0/input10
[   21.829816] input: HDA Intel Mic at Sep UNKNOWN Jack as /devices/pci0000:00/0000:00:1b.0/sound/card0/input11
[   21.830051] input: HDA Intel HP Out at Ext Front Jack as /devices/pci0000:00/0000:00:1b.0/sound/card0/input12
[   21.835526] nvidia: module license 'NVIDIA' taints kernel.
[   21.835530] Disabling lock debugging due to kernel taint
[   22.758056] Bluetooth: RFCOMM TTY layer initialized
[   22.758062] Bluetooth: RFCOMM socket layer initialized
[   22.758064] Bluetooth: RFCOMM ver 1.11
[   22.897930] nvidia 0000:01:00.0: power state changed by ACPI to D0
[   22.897950] nvidia 0000:01:00.0: power state changed by ACPI to D0
[   22.897966] nvidia 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   22.897982] nvidia 0000:01:00.0: setting latency timer to 64
[   22.897988] vgaarb: device changed decodes: PCI:0000:01:00.0,olddecodes=io+mem,decodes=none:owns=io+mem
[   22.898130] NVRM: loading NVIDIA UNIX x86 Kernel Module  260.19.06  Mon Sep 13 06:35:06 PDT 2010
[   22.914953] phy0: Selected rate control algorithm 'iwl-agn-rs'
[   23.084767] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   23.175023] ppdev: user-space parallel port driver
[   24.065098] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,commit=0
[   25.917828] cfg80211: Found new beacon on frequency: 5765 MHz (Ch 153) on phy0
[   28.673466] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,commit=0
[   38.881095] wlan0: authenticate with 00:19:a9:a5:bb:e0 (try 1)
[   38.883204] wlan0: authenticated
[   38.883226] wlan0: associate with 00:19:a9:a5:bb:e0 (try 1)
[   38.891081] wlan0: RX AssocResp from 00:19:a9:a5:bb:e0 (capab=0x411 status=0 aid=55)
[   38.891085] wlan0: associated
[   38.894799] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   38.894847] cfg80211: Calling CRDA for country: US
[   38.898839] cfg80211: Disabling channel 2467 MHz on phy0 due to Country IE
[   38.898842] cfg80211: Disabling channel 2472 MHz on phy0 due to Country IE
[   38.898846] cfg80211: Disabling channel 5600 MHz on phy0 due to Country IE
[   38.898848] cfg80211: Disabling channel 5620 MHz on phy0 due to Country IE
[   38.898850] cfg80211: Disabling channel 5640 MHz on phy0 due to Country IE
[   38.898856] cfg80211: Regulatory domain changed to country: US
[   38.898857]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   38.898860]     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
[   38.898863]     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 1700 mBm)
[   38.898866]     (5250000 KHz - 5330000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   38.898868]     (5490000 KHz - 5600000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   38.898871]     (5650000 KHz - 5710000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   38.898874]     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 3000 mBm)
[   39.287545] padlock: VIA PadLock not detected.
[   49.800009] wlan0: no IPv6 routers present
[   51.367070] lo: Disabled Privacy Extensions
[  321.396254] usb 4-1: new low speed USB device using uhci_hcd and address 2
[  321.745469] usbcore: registered new interface driver hiddev
[  321.778991] input: HID 04d9:1133 as /devices/pci0000:00/0000:00:1a.1/usb4/4-1/4-1:1.0/input/input13
[  321.779293] generic-usb 0003:04D9:1133.0001: input,hidraw0: USB HID v1.10 Mouse [HID 04d9:1133] on usb-0000:00:1a.1-1/input0
[  321.779350] usbcore: registered new interface driver usbhid
[  321.779356] usbhid: USB HID core driver
[  674.484041] CE: hpet increased min_delta_ns to 7500 nsec

```

---

### Post by ubudog on 2011-03-25
Cool, I'll take a look at that.  Also, have you done any updates recently?  That may have caused this issue.

---

### Post by ubudog on 2011-03-25
Also, try pressing FN+F9 to see what happens.

---

### Post by Kryzm on 2011-03-25
Great, thank you. And I have updated when prompted, maybe a day or two ago being the last time. Also, FN F9 pauses my music, haha. I've tried turning the trackpad on and off, but it doesn't help.

---

### Post by ubudog on 2011-03-25
Haha, lol.  Strange.  Starting today?  Do you remember if you had any problems with the mouse before updates?

---

### Post by Kryzm on 2011-03-25
I just had another instance of the problem where I can't select text:
I can highlight the address bar in Chrome, but can't type (I don't get a flashing cursor, just a highlight, like when highlighting an html object), so I reloaded the GUI again, and now the trackpad is working. This makes very little sense to me.

---

### Post by Kryzm on 2011-03-25
And no, I haven't had problems before. It began today, and for a few minutes, my wired mouse couldn't right-click. This is strange to me, since most of these seem like they should be unrelated, given that certain functions are ceasing to work, though the entire program seems intact. I can use a mouse, then can't, switch mice, everything's fine, lose functionality, rinse and repeat.

---

### Post by ubudog on 2011-03-25
This is indeed very weird.  I have an idea.  Try booting up a LiveCD, or LiveUSB, whatever, and see if the problem exists there.  If so, this may be a hardware issue (I sure hope not).

---

