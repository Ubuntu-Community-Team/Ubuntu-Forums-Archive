---
title: "Ubuntu 9.10 crashes for no reason"
date: 2010-02-11
forum: General Help
---

### Post by new_to_ubun2 on 2010-02-11
Title says it all.Ubuntu 9.10 on HP Pavilion dv4 laptop crashes all the time absolutely for no reason.

Everything is working very fine and suddenly bang ubuntu drops to black screen and cursor blinking on top right corner requiring a reboot to get it back to normal and again happens the same at any random time.

Need urgent fix with the problem, Thanks in advance.

---

### Post by aeiah on 2010-02-11
next time it happens drop to tty1 with alt+ctrl+F1. if there's nothing unusual reported, try going back to your gui with alt+ctrl+F7. if that doesnt work, drop back to alt+ctrl+F1 and run dmesg and see if it says anything about the problem

---

### Post by Struki on 2010-02-12
I'm having some similar problems, I've posted a thread with more details [http://ubuntuforums.org/showthread.php?t=1402806](http://ubuntuforums.org/showthread.php?t=1402806)

---

### Post by new_to_ubun2 on 2010-02-13
running dmesg gave me vey long output which out my knowledge.
any other idea..?

---

### Post by Richard1979 on 2010-02-14
> **new_to_ubun2 said:**
> running dmesg gave me vey long output which out my knowledge.
any other idea..?

If you don't know what to look for then post the output here so people who do know can figure out the problem.

---

### Post by new_to_ubun2 on 2010-02-15
> **Richard1979 said:**
> If you don't know what to look for then post the output here so people who do know can figure out the problem.

It is such a long output it dont fit compleately on screen
here is only what I see on my terminal window

```
[    0.937055] pci 0000:00:1c.4:   PREFETCH window: 0x000000d3400000-0x000000d43fffff
[    0.937063] pci 0000:00:1c.5: PCI bridge, secondary bus 0000:05
[    0.937066] pci 0000:00:1c.5:   IO window: 0x1000-0x1fff
[    0.937072] pci 0000:00:1c.5:   MEM window: 0xd5500000-0xd64fffff
[    0.937077] pci 0000:00:1c.5:   PREFETCH window: 0x000000d4400000-0x000000d53fffff
[    0.937084] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:08
[    0.937086] pci 0000:00:1e.0:   IO window: disabled
[    0.937092] pci 0000:00:1e.0:   MEM window: disabled
[    0.937096] pci 0000:00:1e.0:   PREFETCH window: disabled
[    0.937108]   alloc irq_desc for 16 on node -1
[    0.937109]   alloc kstat_irqs on node -1
[    0.937114] pci 0000:00:1c.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.937119] pci 0000:00:1c.0: setting latency timer to 64
[    0.937127]   alloc irq_desc for 18 on node -1
[    0.937128]   alloc kstat_irqs on node -1
[    0.937132] pci 0000:00:1c.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.937137] pci 0000:00:1c.2: setting latency timer to 64
[    0.937144]   alloc irq_desc for 19 on node -1
[    0.937146]   alloc kstat_irqs on node -1
[    0.937149] pci 0000:00:1c.3: PCI INT D -> GSI 19 (level, low) -> IRQ 19
[    0.937154] pci 0000:00:1c.3: setting latency timer to 64
[    0.937163] pci 0000:00:1c.4: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.937167] pci 0000:00:1c.4: setting latency timer to 64
[    0.937175]   alloc irq_desc for 17 on node -1
[    0.937177]   alloc kstat_irqs on node -1
[    0.937180] pci 0000:00:1c.5: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    0.937185] pci 0000:00:1c.5: setting latency timer to 64
[    0.937192] pci 0000:00:1e.0: setting latency timer to 64
[    0.937197] pci_bus 0000:00: resource 0 io:  [0x00-0xffff]
[    0.937199] pci_bus 0000:00: resource 1 mem: [0x000000-0xffffffff]
[    0.937201] pci_bus 0000:01: resource 0 io:  [0x5000-0x5fff]
[    0.937204] pci_bus 0000:01: resource 1 mem: [0xd9500000-0xda4fffff]
[    0.937206] pci_bus 0000:01: resource 2 pref mem [0xd0400000-0xd13fffff]
[    0.937208] pci_bus 0000:02: resource 0 io:  [0x4000-0x4fff]
[    0.937211] pci_bus 0000:02: resource 1 mem: [0xd8500000-0xd94fffff]
[    0.937213] pci_bus 0000:02: resource 2 pref mem [0xd1400000-0xd23fffff]
[    0.937215] pci_bus 0000:03: resource 0 io:  [0x3000-0x3fff]
[    0.937218] pci_bus 0000:03: resource 1 mem: [0xd7500000-0xd84fffff]
[    0.937220] pci_bus 0000:03: resource 2 pref mem [0xd2400000-0xd33fffff]
[    0.937222] pci_bus 0000:04: resource 0 io:  [0x2000-0x2fff]
[    0.937225] pci_bus 0000:04: resource 1 mem: [0xd6500000-0xd74fffff]
[    0.937227] pci_bus 0000:04: resource 2 pref mem [0xd3400000-0xd43fffff]
[    0.937229] pci_bus 0000:05: resource 0 io:  [0x1000-0x1fff]
[    0.937232] pci_bus 0000:05: resource 1 mem: [0xd5500000-0xd64fffff]
[    0.937234] pci_bus 0000:05: resource 2 pref mem [0xd4400000-0xd53fffff]
[    0.937236] pci_bus 0000:08: resource 3 io:  [0x00-0xffff]
[    0.937238] pci_bus 0000:08: resource 4 mem: [0x000000-0xffffffff]
[    0.937269] NET: Registered protocol family 2
[    0.937355] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.937635] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.938083] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.938300] TCP: Hash tables configured (established 131072 bind 65536)
[    0.938302] TCP reno registered
[    0.938368] NET: Registered protocol family 1
[    0.938420] Trying to unpack rootfs image as initramfs...
[    1.119401] Freeing initrd memory: 7725k freed
[    1.123378] Simple Boot Flag value 0x5 read from CMOS RAM was invalid
[    1.123381] Simple Boot Flag at 0x44 set to 0x1
[    1.123543] cpufreq-nforce2: No nForce2 chipset.
[    1.123568] Scanning for low memory corruption every 60 seconds
[    1.123668] audit: initializing netlink socket (disabled)
[    1.123684] type=2000 audit(1266278301.120:1): initialized
[    1.131537] highmem bounce pool size: 64 pages
[    1.131542] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    1.132869] VFS: Disk quotas dquot_6.5.2
[    1.132926] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    1.133411] fuse init (API version 7.12)
[    1.133486] msgmni has been set to 1681
[    1.133665] alg: No test for stdrng (krng)
[    1.133677] io scheduler noop registered
[    1.133679] io scheduler anticipatory registered
[    1.133681] io scheduler deadline registered
[    1.133718] io scheduler cfq registered (default)
[    1.133728] pci 0000:00:02.0: Boot video device
[    1.164158]   alloc irq_desc for 24 on node -1
[    1.164160]   alloc kstat_irqs on node -1
[    1.164172] pcieport-driver 0000:00:1c.0: irq 24 for MSI/MSI-X
[    1.164183] pcieport-driver 0000:00:1c.0: setting latency timer to 64
[    1.164335]   alloc irq_desc for 25 on node -1
[    1.164337]   alloc kstat_irqs on node -1
[    1.164346] pcieport-driver 0000:00:1c.2: irq 25 for MSI/MSI-X
[    1.164357] pcieport-driver 0000:00:1c.2: setting latency timer to 64
[    1.164507]   alloc irq_desc for 26 on node -1
[    1.164509]   alloc kstat_irqs on node -1
[    1.164518] pcieport-driver 0000:00:1c.3: irq 26 for MSI/MSI-X
[    1.164528] pcieport-driver 0000:00:1c.3: setting latency timer to 64
[    1.164679]   alloc irq_desc for 27 on node -1
[    1.164681]   alloc kstat_irqs on node -1
[    1.164690] pcieport-driver 0000:00:1c.4: irq 27 for MSI/MSI-X
[    1.164700] pcieport-driver 0000:00:1c.4: setting latency timer to 64
[    1.164851]   alloc irq_desc for 28 on node -1
[    1.164853]   alloc kstat_irqs on node -1
[    1.164861] pcieport-driver 0000:00:1c.5: irq 28 for MSI/MSI-X
[    1.164872] pcieport-driver 0000:00:1c.5: setting latency timer to 64
[    1.164974] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    1.165193] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    1.300073] ACPI: AC Adapter [AC] (on-line)
[    1.300146] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input0
[    1.300150] ACPI: Power Button [PWRF]
[    1.300194] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1
[    1.300197] ACPI: Power Button [PWRB]
[    1.300242] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input2
[    1.300305] ACPI: Lid Switch [LID0]
[    1.300345] input: Sleep Button as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input3
[    1.300351] ACPI: Sleep Button [SLPB]
[    1.341596] fan PNP0C0B:00: registered as cooling_device0
[    1.341601] ACPI: Fan [FAN] (on)
[    1.342502] ACPI: SSDT bba6ec98 00223 (v01  PmRef  Cpu0Ist 00003000 INTL 20051117)
[    1.343094] ACPI: SSDT bba6c618 005B3 (v01  PmRef  Cpu0Cst 00003001 INTL 20051117)
[    1.343591] Monitor-Mwait will be used to enter C-1 state
[    1.343611] Monitor-Mwait will be used to enter C-2 state
[    1.343628] Monitor-Mwait will be used to enter C-3 state
[    1.343634] Marking TSC unstable due to TSC halts in idle
[    1.343652] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[    1.343669] processor LNXCPU:00: registered as cooling_device1
[    1.343672] ACPI: Processor [CPU0] (supports 8 throttling states)
[    1.344141] ACPI: SSDT bba6de18 001CF (v01  PmRef    ApIst 00003000 INTL 20051117)
[    1.344616] ACPI: SSDT bba6ef18 0008D (v01  PmRef    ApCst 00003000 INTL 20051117)
[    1.345239] ACPI: CPU1 (power states: C1[C1] C2[C2] C3[C3])
[    1.345256] processor LNXCPU:01: registered as cooling_device2
[    1.345260] ACPI: Processor [CPU1] (supports 8 throttling states)
[    1.511012] thermal LNXTHERM:01: registered as thermal_zone0
[    1.511020] ACPI: Thermal Zone [THRM] (50 C)
[    1.511079] isapnp: Scanning for PnP cards...
[    1.865039] isapnp: No Plug & Play device found
[    1.866081] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    1.867257] brd: module loaded
[    1.867664] loop: module loaded
[    1.867721] input: Macintosh mouse button emulation as /devices/virtual/input/input4
[    1.867783] ahci 0000:00:1f.2: version 3.0
[    1.867795]   alloc irq_desc for 21 on node -1
[    1.867797]   alloc kstat_irqs on node -1
[    1.867803] ahci 0000:00:1f.2: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[    1.867833]   alloc irq_desc for 29 on node -1
[    1.867834]   alloc kstat_irqs on node -1
[    1.867843] ahci 0000:00:1f.2: irq 29 for MSI/MSI-X
[    1.867893] ahci: SSS flag set, parallel bus scan disabled
[    1.867930] ahci 0000:00:1f.2: AHCI 0001.0200 32 slots 4 ports 3 Gbps 0x33 impl SATA mode
[    1.867933] ahci 0000:00:1f.2: flags: 64bit ncq sntf stag pm led clo pmp pio slum part ems 
[    1.867938] ahci 0000:00:1f.2: setting latency timer to 64
[    1.888068] scsi0 : ahci
[    1.888149] scsi1 : ahci
[    1.888198] scsi2 : ahci
[    1.888247] scsi3 : ahci
[    1.888300] scsi4 : ahci
[    1.888349] scsi5 : ahci
[    1.888576] ata1: SATA max UDMA/133 abar m2048@0xda504000 port 0xda504100 irq 29
[    1.888579] ata2: SATA max UDMA/133 abar m2048@0xda504000 port 0xda504180 irq 29
[    1.888581] ata3: DUMMY
[    1.888583] ata4: DUMMY
[    1.888586] ata5: SATA max UDMA/133 abar m2048@0xda504000 port 0xda504300 irq 29
[    1.888589] ata6: SATA max UDMA/133 abar m2048@0xda504000 port 0xda504380 irq 29
[    1.889413] Fixed MDIO Bus: probed
[    1.889444] PPP generic driver version 2.4.2
[    1.889516] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    1.889532] ehci_hcd 0000:00:1a.7: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    1.889543] ehci_hcd 0000:00:1a.7: setting latency timer to 64
[    1.889546] ehci_hcd 0000:00:1a.7: EHCI Host Controller
[    1.889588] ehci_hcd 0000:00:1a.7: new USB bus registered, assigned bus number 1
[    1.893503] ehci_hcd 0000:00:1a.7: debug port 1
[    1.893509] ehci_hcd 0000:00:1a.7: cache line size of 32 is not supported
[    1.893523] ehci_hcd 0000:00:1a.7: irq 18, io mem 0xda504c00
[    1.908512] ehci_hcd 0000:00:1a.7: USB 2.0 started, EHCI 1.00
[    1.908580] usb usb1: configuration #1 chosen from 1 choice
[    1.908606] hub 1-0:1.0: USB hub found
[    1.908613] hub 1-0:1.0: 4 ports detected
[    1.908665]   alloc irq_desc for 20 on node -1
[    1.908666]   alloc kstat_irqs on node -1
[    1.908671] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    1.908680] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    1.908683] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    1.908709] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 2
[    1.912608] ehci_hcd 0000:00:1d.7: debug port 1
[    1.912615] ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported
[    1.912627] ehci_hcd 0000:00:1d.7: irq 20, io mem 0xda504800
[    1.928017] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    1.928080] usb usb2: configuration #1 chosen from 1 choice
[    1.928104] hub 2-0:1.0: USB hub found
[    1.928110] hub 2-0:1.0: 6 ports detected
[    1.928166] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    1.928182] uhci_hcd: USB Universal Host Controller Interface driver
[    1.928200] uhci_hcd 0000:00:1a.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.928207] uhci_hcd 0000:00:1a.0: setting latency timer to 64
[    1.928210] uhci_hcd 0000:00:1a.0: UHCI Host Controller
[    1.928239] uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 3
[    1.928283] uhci_hcd 0000:00:1a.0: irq 16, io base 0x000060c0
[    1.928430] usb usb3: configuration #1 chosen from 1 choice
[    1.928452] hub 3-0:1.0: USB hub found
[    1.928458] hub 3-0:1.0: 2 ports detected
[    1.928511] uhci_hcd 0000:00:1a.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    1.928517] uhci_hcd 0000:00:1a.1: setting latency timer to 64
[    1.928521] uhci_hcd 0000:00:1a.1: UHCI Host Controller
[    1.928553] uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus number 4
[    1.928587] uhci_hcd 0000:00:1a.1: irq 17, io base 0x000060a0
[    1.928656] usb usb4: configuration #1 chosen from 1 choice
[    1.928678] hub 4-0:1.0: USB hub found
[    1.928684] hub 4-0:1.0: 2 ports detected
[    1.928729] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    1.928735] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    1.928738] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    1.928763] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 5
[    1.928789] uhci_hcd 0000:00:1d.0: irq 20, io base 0x00006080
[    1.928861] usb usb5: configuration #1 chosen from 1 choice
[    1.928883] hub 5-0:1.0: USB hub found
[    1.928888] hub 5-0:1.0: 2 ports detected
[    1.928931]   alloc irq_desc for 22 on node -1
[    1.928933]   alloc kstat_irqs on node -1
[    1.928937] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 22 (level, low) -> IRQ 22
[    1.928943] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    1.928946] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    1.928973] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 6
[    1.929006] uhci_hcd 0000:00:1d.1: irq 22, io base 0x00006060
[    1.929072] usb usb6: configuration #1 chosen from 1 choice
[    1.929094] hub 6-0:1.0: USB hub found
[    1.929101] hub 6-0:1.0: 2 ports detected
[    1.929147] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    1.929153] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    1.929157] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    1.929182] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 7
[    1.929208] uhci_hcd 0000:00:1d.2: irq 18, io base 0x00006040
[    1.929274] usb usb7: configuration #1 chosen from 1 choice
[    1.929299] hub 7-0:1.0: USB hub found
[    1.929304] hub 7-0:1.0: 2 ports detected
[    1.929390] PNP: PS/2 Controller [PNP0303:KBC,PNP0f13:MOUE] at 0x60,0x64 irq 1,12
[    1.983054] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.983059] serio: i8042 AUX port at 0x60,0x64 irq 12
[    1.983114] mice: PS/2 mouse device common for all mice
[    1.983231] rtc_cmos 00:03: RTC can wake from S4
[    1.983258] rtc_cmos 00:03: rtc core: registered rtc_cmos as rtc0
[    1.983290] rtc0: alarms up to one month, 242 bytes nvram, hpet irqs
[    1.983378] device-mapper: uevent: version 1.0.3
[    1.984336] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: dm-devel@redhat.com
[    1.984401] device-mapper: multipath: version 1.1.0 loaded
[    1.984404] device-mapper: multipath round-robin: version 1.0.0 loaded
[    1.984507] EISA: Probing bus 0 at eisa.0
[    1.984513] Cannot allocate resource for EISA slot 1
[    1.984515] Cannot allocate resource for EISA slot 2
[    1.984517] Cannot allocate resource for EISA slot 3
[    1.984519] Cannot allocate resource for EISA slot 4
[    1.984521] Cannot allocate resource for EISA slot 5
[    1.984522] Cannot allocate resource for EISA slot 6
[    1.984532] EISA: Detected 0 cards.
[    1.984652] cpuidle: using governor ladder
[    1.984760] cpuidle: using governor menu
[    1.985193] TCP cubic registered
[    1.985336] NET: Registered protocol family 10
[    1.985740] lo: Disabled Privacy Extensions
[    1.986032] NET: Registered protocol family 17
[    1.986046] Bluetooth: L2CAP ver 2.13
[    1.986048] Bluetooth: L2CAP socket layer initialized
[    1.986051] Bluetooth: SCO (Voice Link) ver 0.6
[    1.986052] Bluetooth: SCO socket layer initialized
[    1.986073] Bluetooth: RFCOMM TTY layer initialized
[    1.986076] Bluetooth: RFCOMM socket layer initialized
[    1.986078] Bluetooth: RFCOMM ver 1.11
[    1.986488] Using IPI No-Shortcut mode
[    1.986544] PM: Resume from disk failed.
[    1.986555] registered taskstats version 1
[    1.986672]   Magic number: 14:983:1009
[    1.986762] rtc_cmos 00:03: setting system clock to 2010-02-15 23:58:22 UTC (1266278302)
[    1.986765] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.986767] EDD information not available.
[    2.025063] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input5
[    2.130901] ACPI: Battery Slot [BAT0] (battery present)
[    2.380055] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    2.381534] ata1.00: ACPI cmd 00/00:00:00:00:00:a0 rejected by device (Stat=0x51 Err=0x04)
[    2.381812] ata1.00: ACPI cmd ef/10:01:00:00:00:a0 rejected by device (Stat=0x51 Err=0x04)
[    2.382030] ata1.00: ACPI cmd ef/10:02:00:00:00:a0 succeeded
[    2.382036] ata1.00: ACPI cmd ef/10:03:00:00:00:a0 filtered out
[    2.382260] ata1.00: ACPI cmd ef/10:04:00:00:00:a0 rejected by device (Stat=0x51 Err=0x04)
[    2.382503] ata1.00: ACPI cmd ef/10:05:00:00:00:a0 rejected by device (Stat=0x51 Err=0x04)
[    2.383303] ata1.00: ATA-8: Hitachi HTS723232L9A360, FC4OC60D, max UDMA/100
[    2.383308] ata1.00: 625142448 sectors, multi 0: LBA48 NCQ (depth 31/32)
[    2.385029] ata1.00: ACPI cmd 00/00:00:00:00:00:a0 rejected by device (Stat=0x51 Err=0x04)
[    2.385255] ata1.00: ACPI cmd ef/10:01:00:00:00:a0 rejected by device (Stat=0x51 Err=0x04)
[    2.385261] ata1.00: ACPI cmd ef/10:03:00:00:00:a0 filtered out
[    2.385492] ata1.00: ACPI cmd ef/10:04:00:00:00:a0 rejected by device (Stat=0x51 Err=0x04)
[    2.385770] ata1.00: ACPI cmd ef/10:05:00:00:00:a0 rejected by device (Stat=0x51 Err=0x04)
[    2.385815] ata1.00: configured for UDMA/100
[    2.400210] scsi 0:0:0:0: Direct-Access     ATA      Hitachi HTS72323 FC4O PQ: 0 ANSI: 5
[    2.400315] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    2.400332] sd 0:0:0:0: [sda] 625142448 512-byte logical blocks: (320 GB/298 GiB)
[    2.400372] sd 0:0:0:0: [sda] Write Protect is off
[    2.400374] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    2.400395] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.400514]  sda: sda1 sda2
[    2.416903] sd 0:0:0:0: [sda] Attached SCSI disk
[    2.500037] Clocksource tsc unstable (delta = -457391302 ns)
[    2.500057] usb 2-5: new high speed USB device using ehci_hcd and address 4
[    2.635183] usb 2-5: configuration #1 chosen from 1 choice
[    2.872060] usb 3-2: new full speed USB device using uhci_hcd and address 2
[    3.026453] usb 3-2: configuration #1 chosen from 1 choice
[    3.268114] usb 5-1: new full speed USB device using uhci_hcd and address 2
[    3.288109] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    3.293308] ata2.00: ACPI cmd 00/00:00:00:00:00:b0 rejected by device (Stat=0x51 Err=0x04)
[    3.293815] ata2.00: ACPI cmd ef/10:01:00:00:00:b0 rejected by device (Stat=0x51 Err=0x04)
[    3.294318] ata2.00: ACPI cmd ef/10:02:00:00:00:b0 rejected by device (Stat=0x51 Err=0x04)
[    3.294323] ata2.00: ACPI cmd ef/10:03:00:00:00:b0 filtered out
[    3.294824] ata2.00: ACPI cmd ef/10:04:00:00:00:b0 rejected by device (Stat=0x51 Err=0x04)
[    3.295326] ata2.00: ACPI cmd ef/10:05:00:00:00:b0 succeeded
[    3.300298] ata2.00: ATAPI: hp       DVDRAM GT20L, DC05, max UDMA/100, ATAPI AN
[    3.305704] ata2.00: ACPI cmd 00/00:00:00:00:00:b0 rejected by device (Stat=0x51 Err=0x04)
[    3.306218] ata2.00: ACPI cmd ef/10:01:00:00:00:b0 rejected by device (Stat=0x51 Err=0x04)
[    3.306732] ata2.00: ACPI cmd ef/10:02:00:00:00:b0 rejected by device (Stat=0x51 Err=0x04)
[    3.306738] ata2.00: ACPI cmd ef/10:03:00:00:00:b0 filtered out
[    3.307228] ata2.00: ACPI cmd ef/10:04:00:00:00:b0 rejected by device (Stat=0x51 Err=0x04)
[    3.307782] ata2.00: configured for UDMA/100
[    3.327227] scsi 1:0:0:0: CD-ROM            hp       DVDRAM GT20L     DC05 PQ: 0 ANSI: 5
[    3.338375] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[    3.338379] Uniform CD-ROM driver Revision: 3.20
[    3.338491] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    3.338551] sr 1:0:0:0: Attached scsi generic sg1 type 5
[    3.441917] usb 5-1: configuration #2 chosen from 2 choices
[    3.656112] ata5: SATA link down (SStatus 0 SControl 300)
[    3.688101] usb 5-2: new low speed USB device using uhci_hcd and address 3
[    3.861922] usb 5-2: configuration #1 chosen from 1 choice
[    3.992125] ata6: SATA link down (SStatus 0 SControl 300)
[    4.008157] Freeing unused kernel memory: 540k freed
[    4.008484] Write protecting the kernel text: 4568k
[    4.008542] Write protecting the kernel read-only data: 1836k
[    4.302728] Linux agpgart interface v0.103
[    4.310217] agpgart-intel 0000:00:00.0: Intel Mobile Intel® GM45 Express Chipset
[    4.310878] agpgart-intel 0000:00:00.0: detected 65532K stolen memory
[    4.314237] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0xc0000000
[    4.328189] b43-pci-bridge 0000:02:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    4.328207] b43-pci-bridge 0000:02:00.0: setting latency timer to 64
[    4.333259] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    4.333291] r8169 0000:03:00.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    4.333408] r8169 0000:03:00.0: setting latency timer to 64
[    4.333560]   alloc irq_desc for 30 on node -1
[    4.333562]   alloc kstat_irqs on node -1
[    4.333612] r8169 0000:03:00.0: irq 30 for MSI/MSI-X
[    4.334257] eth0: RTL8102e at 0xf80f6000, 00:26:22:9b:6f:93, XID 24c00000 IRQ 30
[    4.372490] usbcore: registered new interface driver hiddev
[    4.385121] input: SIGMACH1P U+P Mouse as /devices/pci0000:00/0000:00:1d.0/usb5/5-2/5-2:1.0/input/input6
[    4.385193] generic-usb 0003:1C4F:0003.0001: input,hidraw0: USB HID v1.10 Mouse [SIGMACH1P U+P Mouse] on usb-0000:00:1d.0-2/input0
[    4.385209] usbcore: registered new interface driver usbhid
[    4.385211] usbhid: v2.6:USB HID core driver
[    4.396149] ssb: Sonics Silicon Backplane found on PCI device 0000:02:00.0
[    4.426436] [drm] Initialized drm 1.1.0 20060810
[    4.436278] i915 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    4.436283] i915 0000:00:02.0: setting latency timer to 64
[    4.438356]   alloc irq_desc for 31 on node -1
[    4.438358]   alloc kstat_irqs on node -1
[    4.438367] i915 0000:00:02.0: irq 31 for MSI/MSI-X
[    4.544536] [drm] i2c_init DPDDC-B
[    4.554170] [drm] i2c_init DPDDC-D
[    4.677472] i2c-adapter i2c-2: unable to read EDID block.
[    4.677475] i915 0000:00:02.0: HDMI Type A-1: no EDID data
[    4.685374] [drm] fb0: inteldrmfb frame buffer device
[    4.686424] [Firmware Bug]: ACPI: ACPI brightness control misses _BQC function
[    4.697320] acpi device:04: registered as cooling_device3
[    4.697556] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:01/input/input7
[    4.697580] ACPI: Video Device [OVGA] (multi-head: yes  rom: no  post: no)
[    4.697624] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
[    5.112353] [drm] LVDS-8: set mode 1280x800 14
[    5.755184] Console: switching to colour frame buffer device 160x50
[    6.339103] EXT4-fs (loop0): INFO: recovery required on readonly filesystem
[    6.339109] EXT4-fs (loop0): write access will be enabled during recovery
[    6.360342] EXT4-fs (loop0): barriers enabled
[    7.191739] kjournald2 starting: pid 437, dev loop0:8, commit interval 5 seconds
[    7.191763] EXT4-fs (loop0): delayed allocation enabled
[    7.191767] EXT4-fs: file extents enabled
[    7.192328] EXT4-fs: mballoc enabled
[    7.192342] EXT4-fs (loop0): orphan cleanup on readonly fs
[    7.192349] EXT4-fs (loop0): ext4_orphan_cleanup: deleting unreferenced inode 136941
[    7.192418] EXT4-fs (loop0): ext4_orphan_cleanup: deleting unreferenced inode 136940
[    7.192435] EXT4-fs (loop0): ext4_orphan_cleanup: deleting unreferenced inode 136900
[    7.192477] EXT4-fs (loop0): ext4_orphan_cleanup: deleting unreferenced inode 130712
[    7.192492] EXT4-fs (loop0): ext4_orphan_cleanup: deleting unreferenced inode 130967
[    7.192511] EXT4-fs (loop0): ext4_orphan_cleanup: deleting unreferenced inode 65200
[    7.192521] EXT4-fs (loop0): ext4_orphan_cleanup: deleting unreferenced inode 4836
[    7.192530] EXT4-fs (loop0): ext4_orphan_cleanup: deleting unreferenced inode 4833
[    7.192538] EXT4-fs (loop0): ext4_orphan_cleanup: deleting unreferenced inode 4820
[    7.192545] EXT4-fs (loop0): ext4_orphan_cleanup: deleting unreferenced inode 4818
[    7.192552] EXT4-fs (loop0): 10 orphan inodes deleted
[    7.192555] EXT4-fs (loop0): recovery complete
[    7.195215] EXT4-fs (loop0): mounted filesystem with ordered data mode
[    7.777586] type=1505 audit(1266278308.290:2): operation="profile_load" pid=461 name=/usr/share/gdm/guest-session/Xsession
[    7.779537] type=1505 audit(1266278308.290:3): operation="profile_load" pid=462 name=/sbin/dhclient3
[    7.780216] type=1505 audit(1266278308.293:4): operation="profile_load" pid=462 name=/usr/lib/NetworkManager/nm-dhcp-client.action
[    7.780575] type=1505 audit(1266278308.293:5): operation="profile_load" pid=462 name=/usr/lib/connman/scripts/dhclient-script
[    7.819340] type=1505 audit(1266278308.329:6): operation="profile_load" pid=463 name=/usr/bin/evince
[    7.829580] type=1505 audit(1266278308.341:7): operation="profile_load" pid=463 name=/usr/bin/evince-previewer
[    7.835594] type=1505 audit(1266278308.345:8): operation="profile_load" pid=463 name=/usr/bin/evince-thumbnailer
[    7.852535] type=1505 audit(1266278308.365:9): operation="profile_load" pid=465 name=/usr/lib/cups/backend/cups-pdf
[    7.853305] type=1505 audit(1266278308.365:10): operation="profile_load" pid=465 name=/usr/sbin/cupsd
[    7.866394] type=1505 audit(1266278308.377:11): operation="profile_load" pid=466 name=/usr/sbin/mysqld
[   11.265669] udev: starting version 147
[   11.678709] lirc_dev: IR Remote Control driver registered, major 61 
[   11.679204] lirc_dev: lirc_register_driver: sample_rate: 0
[   11.679314] enecir: unknown ENE chip detected, assuming KB3926D
[   11.679316] enecir: driver support incomplete
[   11.679318] enecir: chip is 0x3926 - 0x00, 0xd2
[   11.679326] enecir: hardware features:
[   11.679328] enecir: learning and tx off, gpio40_learn off, fan_in off
[   11.679330] enecir: driver has been succesfully loaded
[   11.685501] lis3lv02d: laptop model unknown, using default axes configuration
[   11.686195] lis3lv02d: 1-byte sensor found
[   11.707630] input: ST LIS3LV02DL Accelerometer as /devices/platform/lis3lv02d/input/input8
[   11.707705] Registered led device: hp::hddprotect
[   11.707723] lis3lv02d driver loaded.
[   11.890318] jmb38x_ms 0000:04:00.3: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   11.890327] jmb38x_ms 0000:04:00.3: setting latency timer to 64
[   11.892215] sdhci: Secure Digital Host Controller Interface driver
[   11.892218] sdhci: Copyright(c) Pierre Ossman
[   11.893457] sdhci-pci 0000:04:00.0: SDHCI controller found [197b:2382] (rev 0)
[   11.893481] sdhci-pci 0000:04:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   11.893523] sdhci-pci 0000:04:00.0: setting latency timer to 64
[   11.893558] Registered led device: mmc0::
[   11.893595] mmc0: SDHCI controller on PCI [0000:04:00.0] using ADMA
[   11.893607] sdhci-pci 0000:04:00.2: SDHCI controller found [197b:2381] (rev 0)
[   11.893624] sdhci-pci 0000:04:00.2: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   11.893630] sdhci-pci 0000:04:00.2: Refusing to bind to secondary interface.
[   11.893638] sdhci-pci 0000:04:00.2: PCI INT A disabled
[   11.980152] cfg80211: Calling CRDA to update world regulatory domain
[   11.996225] b43-phy0: Broadcom 4312 WLAN found (core revision 15)
[   12.040142] b43-phy0 ERROR: FOUND UNSUPPORTED PHY (Analog 6, Type 5, Revision 1)
[   12.040192] b43: probe of ssb0:0 failed with error -95
[   12.040231] Broadcom 43xx driver loaded [ Features: PL, Firmware-ID: FW13 ]
[   12.126448] eth1: register 'cdc_ether' at usb-0000:00:1d.0-1, CDC Ethernet Device, 00:1b:57:1d:eb:4d
[   12.126471] usbcore: registered new interface driver cdc_ether
[   12.223006] lp: driver loaded but no devices found
[   12.235297] cfg80211: World regulatory domain updated:
[   12.235300] 	(start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   12.235303] 	(2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   12.235305] 	(2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   12.235308] 	(2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   12.235310] 	(5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   12.235312] 	(5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   12.392774] Linux video capture interface: v2.00
[   12.462353] uvcvideo: Found UVC 1.00 device HP Webcam (090c:137b)
[   12.541795] HDA Intel 0000:00:1b.0: power state changed by ACPI to D0
[   12.541808] HDA Intel 0000:00:1b.0: PCI INT B -> GSI 22 (level, low) -> IRQ 22
[   12.541813] hda_intel: msi for device 103c:30f7 set to 1
[   12.541870]   alloc irq_desc for 32 on node -1
[   12.541872]   alloc kstat_irqs on node -1
[   12.541886] HDA Intel 0000:00:1b.0: irq 32 for MSI/MSI-X
[   12.541924] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   12.548440] ip_tables: (C) 2000-2006 Netfilter Core Team
[   12.617340] input: HDA Digital PCBeep as /devices/pci0000:00/0000:00:1b.0/input/input9
[   12.692018] input: HP Webcam as /devices/pci0000:00/0000:00:1d.7/usb2/2-5/2-5:1.0/input/input10
[   12.692069] usbcore: registered new interface driver uvcvideo
[   12.692072] USB Video Class driver (v0.1.0)
[   12.790167] input: HDA Intel Mic at Ext Front Jack as /devices/pci0000:00/0000:00:1b.0/sound/card0/input11
[   12.790238] input: HDA Intel Mic at Sep UNKNOWN Jack as /devices/pci0000:00/0000:00:1b.0/sound/card0/input12
[   12.790288] input: HDA Intel HP Out at Ext Front Jack as /devices/pci0000:00/0000:00:1b.0/sound/card0/input13
[   13.243816] input: PS/2 Mouse as /devices/platform/i8042/serio1/input/input14
[   13.291137] input: AlpsPS/2 ALPS GlidePoint as /devices/platform/i8042/serio1/input/input15
[   25.805753] Adding 262136k swap on /host/ubuntu/disks/swap.disk.  Priority:-1 extents:1 across:262136k 
[   26.073461] EXT4-fs (loop0): internal journal on loop0:8
[   26.363137] __ratelimit: 3 callbacks suppressed
[   26.363140] type=1505 audit(1266258526.873:13): operation="profile_replace" pid=966 name=/usr/share/gdm/guest-session/Xsession
[   26.364794] type=1505 audit(1266258526.877:14): operation="profile_replace" pid=967 name=/sbin/dhclient3
[   26.365454] type=1505 audit(1266258526.877:15): operation="profile_replace" pid=967 name=/usr/lib/NetworkManager/nm-dhcp-client.action
[   26.365813] type=1505 audit(1266258526.877:16): operation="profile_replace" pid=967 name=/usr/lib/connman/scripts/dhclient-script
[   26.369721] type=1505 audit(1266258526.881:17): operation="profile_replace" pid=970 name=/usr/bin/evince
[   26.379966] type=1505 audit(1266258526.889:18): operation="profile_replace" pid=970 name=/usr/bin/evince-previewer
[   26.386516] type=1505 audit(1266258526.897:19): operation="profile_replace" pid=970 name=/usr/bin/evince-thumbnailer
[   26.394997] type=1505 audit(1266258526.905:20): operation="profile_replace" pid=972 name=/usr/lib/cups/backend/cups-pdf
[   26.395769] type=1505 audit(1266258526.905:21): operation="profile_replace" pid=972 name=/usr/sbin/cupsd
[   26.398004] type=1505 audit(1266258526.909:22): operation="profile_replace" pid=973 name=/usr/sbin/mysqld
[   26.483892] r8169: eth0: link down
[   26.484090] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   27.697271] i2c-adapter i2c-2: unable to read EDID block.
[   27.697276] i915 0000:00:02.0: HDMI Type A-1: no EDID data
[   27.701942] i2c-adapter i2c-2: unable to read EDID block.
[   27.701948] i915 0000:00:02.0: HDMI Type A-1: no EDID data
[   27.834706] i2c-adapter i2c-2: unable to read EDID block.
[   27.834710] i915 0000:00:02.0: HDMI Type A-1: no EDID data
[   27.839112] i2c-adapter i2c-2: unable to read EDID block.
[   27.839114] i915 0000:00:02.0: HDMI Type A-1: no EDID data
[   29.057861] ppdev: user-space parallel port driver
[   29.523029] CPU0 attaching NULL sched-domain.
[   29.523034] CPU1 attaching NULL sched-domain.
[   29.536592] CPU0 attaching sched-domain:
[   29.536596]  domain 0: span 0-1 level MC
[   29.536598]   groups: 0 1
[   29.536603] CPU1 attaching sched-domain:
[   29.536605]  domain 0: span 0-1 level MC
[   29.536607]   groups: 1 0
[   29.726356] i2c-adapter i2c-2: unable to read EDID block.
[   29.726360] i915 0000:00:02.0: HDMI Type A-1: no EDID data
[   29.730761] i2c-adapter i2c-2: unable to read EDID block.
[   29.730763] i915 0000:00:02.0: HDMI Type A-1: no EDID data
[   29.866332] i2c-adapter i2c-2: unable to read EDID block.
[   29.866335] i915 0000:00:02.0: HDMI Type A-1: no EDID data
[   29.871065] i2c-adapter i2c-2: unable to read EDID block.
[   29.871068] i915 0000:00:02.0: HDMI Type A-1: no EDID data
[   30.006575] i2c-adapter i2c-2: unable to read EDID block.
[   30.006579] i915 0000:00:02.0: HDMI Type A-1: no EDID data
[   30.011297] i2c-adapter i2c-2: unable to read EDID block.
[   30.011300] i915 0000:00:02.0: HDMI Type A-1: no EDID data
[   36.896065] eth1: no IPv6 routers present
[   43.990008] i2c-adapter i2c-2: unable to read EDID block.
[   43.990012] i915 0000:00:02.0: HDMI Type A-1: no EDID data
[   43.994791] i2c-adapter i2c-2: unable to read EDID block.
[   43.994797] i915 0000:00:02.0: HDMI Type A-1: no EDID data
[   44.130542] i2c-adapter i2c-2: unable to read EDID block.
[   44.130546] i915 0000:00:02.0: HDMI Type A-1: no EDID data
[   44.134958] i2c-adapter i2c-2: unable to read EDID block.
[   44.134960] i915 0000:00:02.0: HDMI Type A-1: no EDID data
[   44.282971] i2c-adapter i2c-2: unable to read EDID block.
[   44.282975] i915 0000:00:02.0: HDMI Type A-1: no EDID data
[   44.287383] i2c-adapter i2c-2: unable to read EDID block.
[   44.287385] i915 0000:00:02.0: HDMI Type A-1: no EDID data
[   45.086524] i2c-adapter i2c-2: unable to read EDID block.
[   45.086528] i915 0000:00:02.0: HDMI Type A-1: no EDID data
[   45.091286] i2c-adapter i2c-2: unable to read EDID block.
[   45.091289] i915 0000:00:02.0: HDMI Type A-1: no EDID data
[   62.724915] NET: Registered protocol family 24
```

---

