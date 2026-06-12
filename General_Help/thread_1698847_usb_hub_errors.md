---
title: "usb hub errors?"
date: 2011-03-02
forum: General Help
---

### Post by daglamier on 2011-03-02
I have a recent install of ubuntu 10.10 on a brand new rig, and everything appears to be working properly but i get these 2 errors during bootup that seem to make the book process take a bit longer than expected but haven't actually noticed a problem in performance.

[    6.394416] hub 3-1:1.0: config failed, can't read hub descriptor (err -22)
[    6.752860] hub 3-2:1.0: config failed, can't read hub descriptor (err -22)

I have been unable to find a site with information on what err -22 means. any direction would be appreciated! From what little i have found on the issue it seems to be something with the usb 3.0 hubs on the back of my motherboard?

```
 0.864023] PCI: Using ACPI for IRQ routing
[    0.864024] PCI: pci_cache_line_size set to 64 bytes
[    0.864081] reserve RAM buffer: 000000000009dc00 - 000000000009ffff 
[    0.864082] reserve RAM buffer: 00000000df7e0000 - 00000000dfffffff 
[    0.864083] reserve RAM buffer: 000000021f800000 - 000000021fffffff 
[    0.864120] NetLabel: Initializing
[    0.864121] NetLabel:  domain hash size = 128
[    0.864122] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.864127] NetLabel:  unlabeled traffic allowed by default
[    0.864143] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0, 0, 0, 0, 0
[    0.864146] hpet0: 8 comparators, 64-bit 14.318180 MHz counter
[    0.866156] Switching to clocksource tsc
[    0.869407] AppArmor: AppArmor Filesystem Enabled
[    0.869415] pnp: PnP ACPI init
[    0.869422] ACPI: bus type pnp registered
[    0.870419] pnp: PnP ACPI: found 14 devices
[    0.870419] ACPI: ACPI bus type pnp unregistered
[    0.870425] system 00:01: [io  0x04d0-0x04d1] has been reserved
[    0.870426] system 00:01: [io  0x0290-0x029f] has been reserved
[    0.870427] system 00:01: [io  0x0800-0x087f] has been reserved
[    0.870428] system 00:01: [io  0x0290-0x0294] has been reserved
[    0.870429] system 00:01: [io  0x0880-0x088f] has been reserved
[    0.870432] system 00:08: [io  0x0400-0x04cf] has been reserved
[    0.870433] system 00:08: [io  0x04d2-0x04ff] has been reserved
[    0.870435] system 00:09: [io  0x1000-0x107f] has been reserved
[    0.870436] system 00:09: [io  0x1080-0x10ff] has been reserved
[    0.870437] system 00:09: [io  0x1100-0x117f] has been reserved
[    0.870438] system 00:09: [io  0x1180-0x11ff] has been reserved
[    0.870440] system 00:0a: [io  0x0454-0x0457] has been reserved
[    0.870442] system 00:0b: [mem 0xf0000000-0xf3ffffff] has been reserved
[    0.870444] system 00:0c: [mem 0x000d0a00-0x000d3fff] has been reserved
[    0.870445] system 00:0c: [mem 0x000f0000-0x000f7fff] could not be reserved
[    0.870446] system 00:0c: [mem 0x000f8000-0x000fbfff] could not be reserved
[    0.870447] system 00:0c: [mem 0x000fc000-0x000fffff] could not be reserved
[    0.870449] system 00:0c: [mem 0xdf7e0000-0xdf7effff] could not be reserved
[    0.870450] system 00:0c: [mem 0x00000000-0x0009ffff] could not be reserved
[    0.870451] system 00:0c: [mem 0x00100000-0xdf7dffff] could not be reserved
[    0.870452] system 00:0c: [mem 0xdf7f0000-0xdf7fffff] has been reserved
[    0.870453] system 00:0c: [mem 0xfec00000-0xfec00fff] could not be reserved
[    0.870454] system 00:0c: [mem 0xfed10000-0xfed1dfff] has been reserved
[    0.870455] system 00:0c: [mem 0xfed20000-0xfed8ffff] has been reserved
[    0.870456] system 00:0c: [mem 0xfee00000-0xfee00fff] has been reserved
[    0.870457] system 00:0c: [mem 0xffb00000-0xffb7ffff] has been reserved
[    0.870458] system 00:0c: [mem 0xfff00000-0xffffffff] has been reserved
[    0.870459] system 00:0c: [mem 0x000e0000-0x000effff] has been reserved
[    0.870460] system 00:0c: [mem 0x20000000-0x201fffff] could not be reserved
[    0.870461] system 00:0c: [mem 0x40000000-0x400fffff] could not be reserved
[    0.870462] system 00:0c: [mem 0xdf800000-0xdfffffff] could not be reserved
[    0.871979] Freeing initrd memory: 10756k freed
[    0.875530] pci 0000:00:1c.0: BAR 14: assigned [mem 0xf4000000-0xf41fffff]
[    0.875533] pci 0000:00:1c.0: BAR 15: assigned [mem 0xf4200000-0xf43fffff 64bit pref]
[    0.875534] pci 0000:00:1c.7: BAR 15: assigned [mem 0xf4400000-0xf44fffff pref]
[    0.875536] pci 0000:00:1c.0: BAR 13: assigned [io  0x2000-0x2fff]
[    0.875537] pci 0000:01:00.0: BAR 6: assigned [mem 0xe8000000-0xe807ffff pref]
[    0.875539] pci 0000:00:01.0: PCI bridge to [bus 01-01]
[    0.875540] pci 0000:00:01.0:   bridge window [io  0xe000-0xefff]
[    0.875541] pci 0000:00:01.0:   bridge window [mem 0xf6000000-0xf9ffffff]
[    0.875543] pci 0000:00:01.0:   bridge window [mem 0xe0000000-0xefffffff 64bit pref]
[    0.875545] pci 0000:00:01.1: PCI bridge to [bus 02-02]
[    0.875545] pci 0000:00:01.1:   bridge window [io  disabled]
[    0.875547] pci 0000:00:01.1:   bridge window [mem 0xfbd00000-0xfbdfffff]
[    0.875548] pci 0000:00:01.1:   bridge window [mem pref disabled]
[    0.875550] pci 0000:00:1c.0: PCI bridge to [bus 03-03]
[    0.875552] pci 0000:00:1c.0:   bridge window [io  0x2000-0x2fff]
[    0.875555] pci 0000:00:1c.0:   bridge window [mem 0xf4000000-0xf41fffff]
[    0.875558] pci 0000:00:1c.0:   bridge window [mem 0xf4200000-0xf43fffff 64bit pref]
[    0.875562] pci 0000:00:1c.5: PCI bridge to [bus 04-04]
[    0.875564] pci 0000:00:1c.5:   bridge window [io  0xd000-0xdfff]
[    0.875567] pci 0000:00:1c.5:   bridge window [mem disabled]
[    0.875570] pci 0000:00:1c.5:   bridge window [mem 0xfbc00000-0xfbcfffff 64bit pref]
[    0.875575] pci 0000:05:00.0: PCI bridge to [bus 06-06]
[    0.875575] pci 0000:05:00.0:   bridge window [io  disabled]
[    0.875583] pci 0000:05:00.0:   bridge window [mem 0xfbb00000-0xfbbfffff]
[    0.875588] pci 0000:05:00.0:   bridge window [mem pref disabled]
[    0.875598] pci 0000:00:1c.6: PCI bridge to [bus 05-06]
[    0.875599] pci 0000:00:1c.6:   bridge window [io  disabled]
[    0.875602] pci 0000:00:1c.6:   bridge window [mem 0xfbb00000-0xfbbfffff]
[    0.875605] pci 0000:00:1c.6:   bridge window [mem pref disabled]
[    0.875610] pci 0000:07:00.0: BAR 6: assigned [mem 0xf4400000-0xf440ffff pref]
[    0.875610] pci 0000:00:1c.7: PCI bridge to [bus 07-07]
[    0.875612] pci 0000:00:1c.7:   bridge window [io  0xc000-0xcfff]
[    0.875616] pci 0000:00:1c.7:   bridge window [mem 0xfbe00000-0xfbefffff]
[    0.875618] pci 0000:00:1c.7:   bridge window [mem 0xf4400000-0xf44fffff pref]
[    0.875628]   alloc irq_desc for 16 on node -1
[    0.875629]   alloc kstat_irqs on node -1
[    0.875634] pci 0000:00:01.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.875635] pci 0000:00:01.0: setting latency timer to 64
[    0.875638] pci 0000:00:01.1: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.875639] pci 0000:00:01.1: setting latency timer to 64
[    0.875644] pci 0000:00:1c.0: enabling device (0000 -> 0003)
[    0.875646] pci 0000:00:1c.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.875650] pci 0000:00:1c.0: setting latency timer to 64
[    0.875656]   alloc irq_desc for 17 on node -1
[    0.875656]   alloc kstat_irqs on node -1
[    0.875658] pci 0000:00:1c.5: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    0.875660] pci 0000:00:1c.5: setting latency timer to 64
[    0.875666]   alloc irq_desc for 18 on node -1
[    0.875667]   alloc kstat_irqs on node -1
[    0.875668] pci 0000:00:1c.6: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.875671] pci 0000:00:1c.6: setting latency timer to 64
[    0.875683] pci 0000:05:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    0.875689] pci 0000:05:00.0: setting latency timer to 64
[    0.875696]   alloc irq_desc for 19 on node -1
[    0.875696]   alloc kstat_irqs on node -1
[    0.875698] pci 0000:00:1c.7: PCI INT D -> GSI 19 (level, low) -> IRQ 19
[    0.875700] pci 0000:00:1c.7: setting latency timer to 64
[    0.875702] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
[    0.875703] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff]
[    0.875704] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
[    0.875705] pci_bus 0000:00: resource 7 [mem 0x000c0000-0x000dffff]
[    0.875706] pci_bus 0000:00: resource 8 [mem 0xe0000000-0xfebfffff]
[    0.875707] pci_bus 0000:01: resource 0 [io  0xe000-0xefff]
[    0.875708] pci_bus 0000:01: resource 1 [mem 0xf6000000-0xf9ffffff]
[    0.875709] pci_bus 0000:01: resource 2 [mem 0xe0000000-0xefffffff 64bit pref]
[    0.875710] pci_bus 0000:02: resource 1 [mem 0xfbd00000-0xfbdfffff]
[    0.875711] pci_bus 0000:03: resource 0 [io  0x2000-0x2fff]
[    0.875711] pci_bus 0000:03: resource 1 [mem 0xf4000000-0xf41fffff]
[    0.875712] pci_bus 0000:03: resource 2 [mem 0xf4200000-0xf43fffff 64bit pref]
[    0.875713] pci_bus 0000:04: resource 0 [io  0xd000-0xdfff]
[    0.875714] pci_bus 0000:04: resource 2 [mem 0xfbc00000-0xfbcfffff 64bit pref]
[    0.875715] pci_bus 0000:05: resource 1 [mem 0xfbb00000-0xfbbfffff]
[    0.875716] pci_bus 0000:05: resource 4 [io  0x0000-0x0cf7]
[    0.875717] pci_bus 0000:05: resource 5 [io  0x0d00-0xffff]
[    0.875718] pci_bus 0000:05: resource 6 [mem 0x000a0000-0x000bffff]
[    0.875718] pci_bus 0000:05: resource 7 [mem 0x000c0000-0x000dffff]
[    0.875719] pci_bus 0000:05: resource 8 [mem 0xe0000000-0xfebfffff]
[    0.875720] pci_bus 0000:06: resource 1 [mem 0xfbb00000-0xfbbfffff]
[    0.875721] pci_bus 0000:06: resource 5 [mem 0xfbb00000-0xfbbfffff]
[    0.875722] pci_bus 0000:06: resource 8 [io  0x0000-0x0cf7]
[    0.875723] pci_bus 0000:06: resource 9 [io  0x0d00-0xffff]
[    0.875724] pci_bus 0000:06: resource 10 [mem 0x000a0000-0x000bffff]
[    0.875724] pci_bus 0000:06: resource 11 [mem 0x000c0000-0x000dffff]
[    0.875725] pci_bus 0000:06: resource 12 [mem 0xe0000000-0xfebfffff]
[    0.875726] pci_bus 0000:07: resource 0 [io  0xc000-0xcfff]
[    0.875727] pci_bus 0000:07: resource 1 [mem 0xfbe00000-0xfbefffff]
[    0.875728] pci_bus 0000:07: resource 2 [mem 0xf4400000-0xf44fffff pref]
[    0.875747] NET: Registered protocol family 2
[    0.875869] IP route cache hash table entries: 262144 (order: 9, 2097152 bytes)
[    0.876399] TCP established hash table entries: 524288 (order: 11, 8388608 bytes)
[    0.877205] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[    0.877300] TCP: Hash tables configured (established 524288 bind 65536)
[    0.877301] TCP reno registered
[    0.877309] UDP hash table entries: 4096 (order: 5, 131072 bytes)
[    0.877329] UDP-Lite hash table entries: 4096 (order: 5, 131072 bytes)
[    0.877385] NET: Registered protocol family 1
[    0.908165] pci 0000:01:00.0: Boot video device
[    0.908194] PCI: CLS 4 bytes, default 64
[    0.908195] PCI-DMA: Using software bounce buffering for IO (SWIOTLB)
[    0.908196] Placing 64MB software IO TLB between ffff880001fde000 - ffff880005fde000
[    0.908197] software IO TLB at phys 0x1fde000 - 0x5fde000
[    0.908333] Scanning for low memory corruption every 60 seconds
[    0.908388] audit: initializing netlink socket (disabled)
[    0.908391] type=2000 audit(1299115244.760:1): initialized
[    0.914508] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    0.915057] VFS: Disk quotas dquot_6.5.2
[    0.915079] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    0.915300] fuse init (API version 7.14)
[    0.915331] msgmni has been set to 15965
[    0.916256] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.916258] io scheduler noop registered
[    0.916258] io scheduler deadline registered
[    0.916274] io scheduler cfq registered (default)
[    0.916312] pcieport 0000:00:01.0: setting latency timer to 64
[    0.916323]   alloc irq_desc for 40 on node -1
[    0.916323]   alloc kstat_irqs on node -1
[    0.916328] pcieport 0000:00:01.0: irq 40 for MSI/MSI-X
[    0.916351] pcieport 0000:00:01.1: setting latency timer to 64
[    0.916359]   alloc irq_desc for 41 on node -1
[    0.916360]   alloc kstat_irqs on node -1
[    0.916362] pcieport 0000:00:01.1: irq 41 for MSI/MSI-X
[    0.916385] pcieport 0000:00:1c.0: setting latency timer to 64
[    0.916413]   alloc irq_desc for 42 on node -1
[    0.916414]   alloc kstat_irqs on node -1
[    0.916419] pcieport 0000:00:1c.0: irq 42 for MSI/MSI-X
[    0.916468] pcieport 0000:00:1c.5: setting latency timer to 64
[    0.916495]   alloc irq_desc for 43 on node -1
[    0.916496]   alloc kstat_irqs on node -1
[    0.916501] pcieport 0000:00:1c.5: irq 43 for MSI/MSI-X
[    0.916546] pcieport 0000:00:1c.7: setting latency timer to 64
[    0.916574]   alloc irq_desc for 44 on node -1
[    0.916575]   alloc kstat_irqs on node -1
[    0.916580] pcieport 0000:00:1c.7: irq 44 for MSI/MSI-X
[    0.916627] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.916650] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.916679] intel_idle: MWAIT substates: 0x1120
[    0.916680] intel_idle: v0.4 model 0x2A
[    0.916680] intel_idle: lapic_timer_reliable_states 0xffffffff
[    0.916723] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0
[    0.916726] ACPI: Power Button [PWRB]
[    0.916744] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
[    0.916746] ACPI: Power Button [PWRF]
[    0.916849] ACPI: acpi_idle yielding to intel_idle
[    0.917997] ERST: Table is not found!
[    0.918075] Linux agpgart interface v0.103
[    0.918083] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    0.918631] brd: module loaded
[    0.918806] loop: module loaded
[    0.918965] Fixed MDIO Bus: probed
[    0.918976] PPP generic driver version 2.4.2
[    0.918988] tun: Universal TUN/TAP device driver, 1.6
[    0.918989] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.919015] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.919026] ehci_hcd 0000:00:1a.0: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.919034] ehci_hcd 0000:00:1a.0: setting latency timer to 64
[    0.919036] ehci_hcd 0000:00:1a.0: EHCI Host Controller
[    0.919050] ehci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 1
[    0.919067] ehci_hcd 0000:00:1a.0: debug port 2
[    0.922963] ehci_hcd 0000:00:1a.0: cache line size of 4 is not supported
[    0.922972] ehci_hcd 0000:00:1a.0: irq 18, io mem 0xfbffe000
[    0.938196] ehci_hcd 0000:00:1a.0: USB 2.0 started, EHCI 1.00
[    0.938243] hub 1-0:1.0: USB hub found
[    0.938245] hub 1-0:1.0: 2 ports detected
[    0.938275]   alloc irq_desc for 23 on node -1
[    0.938275]   alloc kstat_irqs on node -1
[    0.938278] ehci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    0.938284] ehci_hcd 0000:00:1d.0: setting latency timer to 64
[    0.938285] ehci_hcd 0000:00:1d.0: EHCI Host Controller
[    0.938297] ehci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    0.938312] ehci_hcd 0000:00:1d.0: debug port 2
[    0.942189] ehci_hcd 0000:00:1d.0: cache line size of 4 is not supported
[    0.942196] ehci_hcd 0000:00:1d.0: irq 23, io mem 0xfbffd000
[    0.958195] ehci_hcd 0000:00:1d.0: USB 2.0 started, EHCI 1.00
[    0.958231] hub 2-0:1.0: USB hub found
[    0.958232] hub 2-0:1.0: 2 ports detected
[    0.958254] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.958259] uhci_hcd: USB Universal Host Controller Interface driver
[    0.958300] PNP: No PS/2 controller found. Probing ports directly.
[    0.991029] Failed to disable AUX port, but continuing anyway... Is this a SiS?
[    0.991030] If AUX port is really absent please use the 'i8042.noaux' option.
[    1.246251] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.246274] mice: PS/2 mouse device common for all mice
[    1.246313] rtc_cmos 00:04: RTC can wake from S4
[    1.246325] rtc_cmos 00:04: rtc core: registered rtc_cmos as rtc0
[    1.246347] rtc0: alarms up to one month, 242 bytes nvram, hpet irqs
[    1.246384] device-mapper: uevent: version 1.0.3
[    1.246415] device-mapper: ioctl: 4.17.0-ioctl (2010-03-05) initialised: dm-devel@redhat.com
[    1.246448] device-mapper: multipath: version 1.1.1 loaded
[    1.246449] device-mapper: multipath round-robin: version 1.0.0 loaded
[    1.246560] cpuidle: using governor ladder
[    1.246620] cpuidle: using governor menu
[    1.246717] TCP cubic registered
[    1.246763] NET: Registered protocol family 10
[    1.246888] lo: Disabled Privacy Extensions
[    1.246955] NET: Registered protocol family 17
[    1.247706] PM: Resume from disk failed.
[    1.247710] registered taskstats version 1
[    1.247940]   Magic number: 3:578:305
[    1.247945] tty tty34: hash matches
[    1.248045] rtc_cmos 00:04: setting system clock to 2011-03-03 01:20:45 UTC (1299115245)
[    1.248046] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.248047] EDD information not available.
[    1.248071] Freeing unused kernel memory: 912k freed
[    1.248131] Write protecting the kernel read-only data: 10240k
[    1.248345] Freeing unused kernel memory: 408k freed
[    1.248512] Freeing unused kernel memory: 1644k freed
[    1.255445] udev[98]: starting version 163
[    1.263917] ahci 0000:00:1f.2: version 3.0
[    1.263927] ahci 0000:00:1f.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    1.263954]   alloc irq_desc for 45 on node -1
[    1.263955]   alloc kstat_irqs on node -1
[    1.263961] ahci 0000:00:1f.2: irq 45 for MSI/MSI-X
[    1.263978] ahci: SSS flag set, parallel bus scan disabled
[    1.267320] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    1.267335] r8169 0000:04:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    1.267370] r8169 0000:04:00.0: setting latency timer to 64
[    1.267375] r8169 0000:04:00.0: (unregistered net_device): unknown MAC, using family default
[    1.267418]   alloc irq_desc for 46 on node -1
[    1.267419]   alloc kstat_irqs on node -1
[    1.267430] r8169 0000:04:00.0: irq 46 for MSI/MSI-X
[    1.267613] r8169 0000:04:00.0: eth0: RTL8168b/8111b at 0xffffc900057c4000, 1c:6f:65:96:b0:e5, XID 0c200000 IRQ 46
[    1.272570] firewire_ohci 0000:06:03.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    1.275635] Floppy drive(s): fd0 is unknown type 13 (usb?)
[    1.276202] usb 1-1: new high speed USB device using ehci_hcd and address 2
[    1.286209] ahci 0000:00:1f.2: AHCI 0001.0300 32 slots 6 ports 6 Gbps 0x3f impl SATA mode
[    1.286211] ahci 0000:00:1f.2: flags: 64bit ncq sntf stag pm led clo pmp pio slum part ems apst 
[    1.286214] ahci 0000:00:1f.2: setting latency timer to 64
[    1.301206] FDC 0 is a post-1991 82077
[    1.336890] firewire_ohci: Added fw-ohci device 0000:06:03.0, OHCI v1.10, 4 IR + 8 IT contexts, quirks 0x2
[    1.386397] scsi0 : ahci
[    1.386510] scsi1 : ahci
[    1.386591] scsi2 : ahci
[    1.386681] scsi3 : ahci
[    1.386766] scsi4 : ahci
[    1.386850] scsi5 : ahci
[    1.386926] ata1: SATA max UDMA/133 abar m2048@0xfbffc000 port 0xfbffc100 irq 45
[    1.386928] ata2: SATA max UDMA/133 abar m2048@0xfbffc000 port 0xfbffc180 irq 45
[    1.386930] ata3: SATA max UDMA/133 abar m2048@0xfbffc000 port 0xfbffc200 irq 45
[    1.386931] ata4: SATA max UDMA/133 abar m2048@0xfbffc000 port 0xfbffc280 irq 45
[    1.386933] ata5: SATA max UDMA/133 abar m2048@0xfbffc000 port 0xfbffc300 irq 45
[    1.386934] ata6: SATA max UDMA/133 abar m2048@0xfbffc000 port 0xfbffc380 irq 45
[    1.386953] ahci 0000:07:00.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    1.387017]   alloc irq_desc for 47 on node -1
[    1.387018]   alloc kstat_irqs on node -1
[    1.387027] ahci 0000:07:00.0: irq 47 for MSI/MSI-X
[    1.406278] ahci 0000:07:00.0: AHCI 0001.0200 32 slots 8 ports 6 Gbps 0xff impl SATA mode
[    1.406282] ahci 0000:07:00.0: flags: 64bit ncq pio 
[    1.406289] ahci 0000:07:00.0: setting latency timer to 64
[    1.406543] scsi6 : ahci
[    1.406626] scsi7 : ahci
[    1.406703] scsi8 : ahci
[    1.406781] scsi9 : ahci
[    1.406846] scsi10 : ahci
[    1.406930] scsi11 : ahci
[    1.407004] scsi12 : ahci
[    1.407063] scsi13 : ahci
[    1.407082] ata7: SATA max UDMA/133 abar m2048@0xfbeff000 port 0xfbeff100 irq 47
[    1.407085] ata8: SATA max UDMA/133 abar m2048@0xfbeff000 port 0xfbeff180 irq 47
[    1.407087] ata9: SATA max UDMA/133 abar m2048@0xfbeff000 port 0xfbeff200 irq 47
[    1.407089] ata10: SATA max UDMA/133 abar m2048@0xfbeff000 port 0xfbeff280 irq 47
[    1.407091] ata11: SATA max UDMA/133 abar m2048@0xfbeff000 port 0xfbeff300 irq 47
[    1.407094] ata12: SATA max UDMA/133 abar m2048@0xfbeff000 port 0xfbeff380 irq 47
[    1.407096] ata13: SATA max UDMA/133 abar m2048@0xfbeff000 port 0xfbeff400 irq 47
[    1.407098] ata14: SATA max UDMA/133 abar m2048@0xfbeff000 port 0xfbeff480 irq 47
[    1.416648] hub 1-1:1.0: USB hub found
[    1.416792] hub 1-1:1.0: 6 ports detected
[    1.536204] usb 2-1: new high speed USB device using ehci_hcd and address 2
[    1.686821] hub 2-1:1.0: USB hub found
[    1.686891] hub 2-1:1.0: 8 ports detected
[    1.756224] ata14: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    1.756229] ata9: SATA link down (SStatus 0 SControl 300)
[    1.756433] ata14.00: ATAPI: MARVELL VIRTUALL, 1.09, max UDMA/66
[    1.756724] ata14.00: configured for UDMA/66
[    1.766309] usb 1-1.5: new low speed USB device using ehci_hcd and address 3
[    1.776217] ata8: SATA link down (SStatus 0 SControl 300)
[    1.776222] ata13: SATA link down (SStatus 0 SControl 300)
[    1.776273] ata11: SATA link down (SStatus 0 SControl 300)
[    1.776280] ata7: SATA link down (SStatus 0 SControl 300)
[    1.776311] ata10: SATA link down (SStatus 0 SControl 300)
[    1.776351] ata12: SATA link down (SStatus 0 SControl 300)
[    1.826250] firewire_core: created device fw0: GUID 003b87c5001c6f65, S400
[    1.919897] usbcore: registered new interface driver hiddev
[    1.922736] input: Logitech USB Keyboard as /devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.5/1-1.5:1.0/input/input2
[    1.922768] generic-usb 0003:046D:C31C.0001: input,hidraw0: USB HID v1.10 Keyboard [Logitech USB Keyboard] on usb-0000:00:1a.0-1.5/input0
[    1.929499] input: Logitech USB Keyboard as /devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.5/1-1.5:1.1/input/input3
[    1.929563] generic-usb 0003:046D:C31C.0002: input,hidraw1: USB HID v1.10 Device [Logitech USB Keyboard] on usb-0000:00:1a.0-1.5/input1
[    1.929570] usbcore: registered new interface driver usbhid
[    1.929571] usbhid: USB HID core driver
[    1.936188] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    1.946612] ata1.00: ATA-8: Corsair CSSD-F90GB2, 2.0, max UDMA/133
[    1.946617] ata1.00: 175836528 sectors, multi 1: LBA48 NCQ (depth 31/32), AA
[    1.956625] ata1.00: configured for UDMA/133
[    1.976335] usb 1-1.6: new full speed USB device using ehci_hcd and address 4
[    1.976429] scsi 0:0:0:0: Direct-Access     ATA      Corsair CSSD-F90 2.0  PQ: 0 ANSI: 5
[    1.976512] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    1.976549] sd 0:0:0:0: [sda] 175836528 512-byte logical blocks: (90.0 GB/83.8 GiB)
[    1.976599] sd 0:0:0:0: [sda] Write Protect is off
[    1.976601] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.976710] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.977150]  sda: sda1 sda2 < sda5 >
[    1.978057] sd 0:0:0:0: [sda] Attached SCSI disk
[    2.000673] EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: (null)
[    2.135086] input: Razer Razer Naga as /devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.6/1-1.6:1.0/input/input4
[    2.135119] generic-usb 0003:1532:0015.0003: input,hidraw2: USB HID v1.11 Mouse [Razer Razer Naga] on usb-0000:00:1a.0-1.6/input0
[    2.136404] input: Razer Razer Naga as /devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.6/1-1.6:1.1/input/input5
[    2.136495] generic-usb 0003:1532:0015.0004: input,hidraw3: USB HID v1.11 Keyboard [Razer Razer Naga] on usb-0000:00:1a.0-1.6/input1
[    2.216284] usb 2-1.5: new high speed USB device using ehci_hcd and address 3
[    2.326653] EXT4-fs (sda1): warning: maximal mount count reached, running e2fsck is recommended
[    2.326822] EXT4-fs (sda1): re-mounted. Opts: discard
[    2.327403] hub 2-1.5:1.0: USB hub found
[    2.327635] hub 2-1.5:1.0: 4 ports detected
[    2.406278] usb 2-1.6: new high speed USB device using ehci_hcd and address 4
[    2.517705] hub 2-1.6:1.0: USB hub found
[    2.517895] hub 2-1.6:1.0: 4 ports detected
[    2.926098] ata2: SATA link up 6.0 Gbps (SStatus 133 SControl 300)
[    2.929223] ata2.00: ATA-8: WDC WD1002FAEX-00Z3A0, 05.01D05, max UDMA/133
[    2.929227] ata2.00: 1953525168 sectors, multi 0: LBA48 NCQ (depth 31/32), AA
[    2.931555] ata2.00: configured for UDMA/133
[    2.946311] scsi 1:0:0:0: Direct-Access     ATA      WDC WD1002FAEX-0 05.0 PQ: 0 ANSI: 5
[    2.946371] sd 1:0:0:0: Attached scsi generic sg1 type 0
[    2.946453] sd 1:0:0:0: [sdb] 1953525168 512-byte logical blocks: (1.00 TB/931 GiB)
[    2.946602] sd 1:0:0:0: [sdb] Write Protect is off
[    2.946604] sd 1:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[    2.946664] sd 1:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.947075]  sdb: unknown partition table
[    2.958670] sd 1:0:0:0: [sdb] Attached SCSI disk
[    3.896056] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    3.897112] ata3.00: ATAPI: TSSTcorp DVDWBD SH-B123L, SB02, max UDMA/100
[    3.898651] ata3.00: configured for UDMA/100
[    3.916873] scsi 2:0:0:0: CD-ROM            TSSTcorp DVDWBD SH-B123L  SB02 PQ: 0 ANSI: 5
[    3.922287] sr0: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
[    3.922291] Uniform CD-ROM driver Revision: 3.20
[    3.922387] sr 2:0:0:0: Attached scsi CD-ROM sr0
[    3.922419] sr 2:0:0:0: Attached scsi generic sg2 type 5
[    4.256048] ata4: SATA link down (SStatus 0 SControl 300)
[    4.625994] ata5: SATA link down (SStatus 0 SControl 300)
[    4.997852] ata6: SATA link down (SStatus 0 SControl 300)
[    5.018561] scsi 13:0:0:0: Processor         Marvell  91xx Config      1.01 PQ: 0 ANSI: 5
[    5.018673] scsi 13:0:0:0: Attached scsi generic sg3 type 3
[    5.430482] Adding 3621884k swap on /dev/sda5.  Priority:-1 extents:1 across:3621884k SS
[    5.453641] udev[383]: starting version 163
[    5.489906] xhci_hcd 0000:02:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    5.489925] xhci_hcd 0000:02:00.0: setting latency timer to 64
[    5.489927] xhci_hcd 0000:02:00.0: xHCI Host Controller
[    5.489957] xhci_hcd 0000:02:00.0: new USB bus registered, assigned bus number 3
[    5.511609] lp: driver loaded but no devices found
[    5.522918] coretemp coretemp.0: TjMax is 98 C.
[    5.523028] coretemp coretemp.1: TjMax is 98 C.
[    5.523047] coretemp coretemp.2: TjMax is 98 C.
[    5.523063] coretemp coretemp.3: TjMax is 98 C.
[    5.526106] pkgtemp pkgtemp.0: TjMax is 98 C.
[    5.561694]   alloc irq_desc for 22 on node -1
[    5.561696]   alloc kstat_irqs on node -1
[    5.561700] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[    5.561737]   alloc irq_desc for 48 on node -1
[    5.561738]   alloc kstat_irqs on node -1
[    5.561747] HDA Intel 0000:00:1b.0: irq 48 for MSI/MSI-X
[    5.561764] HDA Intel 0000:00:1b.0: setting latency timer to 64
[    5.569526] type=1400 audit(1299115249.814:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient3" pid=630 comm="apparmor_parser"
[    5.569532] type=1400 audit(1299115249.814:3): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient3" pid=626 comm="apparmor_parser"
[    5.569807] type=1400 audit(1299115249.814:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=630 comm="apparmor_parser"
[    5.569814] type=1400 audit(1299115249.814:5): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=626 comm="apparmor_parser"
[    5.569956] type=1400 audit(1299115249.814:6): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=630 comm="apparmor_parser"
[    5.569964] type=1400 audit(1299115249.814:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=626 comm="apparmor_parser"
[    5.594876] xhci_hcd 0000:02:00.0: irq 17, io mem 0xfbdfe000
[    5.598209] usb usb3: No SuperSpeed endpoint companion for config 1  interface 0 altsetting 0 ep 129: using minimum values
[    5.598261] xHCI xhci_add_endpoint called for root hub
[    5.598262] xHCI xhci_check_bandwidth called for root hub
[    5.598278] hub 3-0:1.0: USB hub found
[    5.598281] hub 3-0:1.0: 4 ports detected
[    5.632376] nvidia: module license 'NVIDIA' taints kernel.
[    5.632378] Disabling lock debugging due to kernel taint
[    5.663819] hda_codec: ALC889: BIOS auto-probing.
[    5.670210] HDA Intel 0000:01:00.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    5.670212] hda_intel: Disable MSI for Nvidia chipset
[    5.670235] HDA Intel 0000:01:00.1: setting latency timer to 64
[    5.670882] EXT4-fs (sdb): warning: maximal mount count reached, running e2fsck is recommended
[    5.705325] EXT4-fs (sdb): mounted filesystem with writeback data mode. Opts: data=writeback
[    5.741567] type=1400 audit(1299115249.984:8): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient3" pid=937 comm="apparmor_parser"
[    5.741850] type=1400 audit(1299115249.984:9): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=937 comm="apparmor_parser"
[    5.742001] type=1400 audit(1299115249.984:10): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=937 comm="apparmor_parser"
[    5.828723] r8169 0000:04:00.0: eth0: link up
[    5.828727] r8169 0000:04:00.0: eth0: link up
[    5.861100] vboxdrv: Found 4 processor cores.
[    5.861131] VBoxDrv: dbg - g_abExecMemory=ffffffffa0cca5e0
[    5.861173] vboxdrv: fAsync=0 offMin=0x18d offMax=0x139ff
[    5.861194] vboxdrv: TSC mode is 'synchronous', kernel timer mode is 'normal'.
[    5.861195] vboxdrv: Successfully loaded version 4.0.4 (interface 0x00160000).
[    6.039175] usb 3-1: new SuperSpeed USB device using xhci_hcd and address 2
[    6.259332] EXT4-fs (sda1): re-mounted. Opts: discard,commit=0
[    6.261940] EXT4-fs (sdb): re-mounted. Opts: data=writeback,commit=0
[    6.308271] xhci_hcd 0000:02:00.0: WARN: short transfer on control ep
[    6.320973] xhci_hcd 0000:02:00.0: WARN: short transfer on control ep
[    6.333605] xhci_hcd 0000:02:00.0: WARN: short transfer on control ep
[    6.333821] usb 3-1: ep 0x81 - rounding interval to 32768 microframes
[    6.333824] xhci_hcd 0000:02:00.0: WARN no SS endpoint bMaxBurst
[    6.336911] hub 3-1:1.0: USB hub found
[    6.388097] xhci_hcd 0000:02:00.0: WARN: Stalled endpoint
[    6.391270] xhci_hcd 0000:02:00.0: WARN: Stalled endpoint
[    6.394393] xhci_hcd 0000:02:00.0: WARN: Stalled endpoint
[    6.394416] hub 3-1:1.0: config failed, can't read hub descriptor (err -22)
[    6.397670] usb 3-2: new SuperSpeed USB device using xhci_hcd and address 3
[    6.666843] xhci_hcd 0000:02:00.0: WARN: short transfer on control ep
[    6.679509] xhci_hcd 0000:02:00.0: WARN: short transfer on control ep
[    6.692134] xhci_hcd 0000:02:00.0: WARN: short transfer on control ep
[    6.692341] usb 3-2: ep 0x81 - rounding interval to 32768 microframes
[    6.692342] xhci_hcd 0000:02:00.0: WARN no SS endpoint bMaxBurst
[    6.695326] hub 3-2:1.0: USB hub found
[    6.746583] xhci_hcd 0000:02:00.0: WARN: Stalled endpoint
[    6.749712] xhci_hcd 0000:02:00.0: WARN: Stalled endpoint
[    6.752837] xhci_hcd 0000:02:00.0: WARN: Stalled endpoint
[    6.752860] hub 3-2:1.0: config failed, can't read hub descriptor (err -22)
[    7.646715] nvidia 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    7.646721] nvidia 0000:01:00.0: setting latency timer to 64
[    7.646724] vgaarb: device changed decodes: PCI:0000:01:00.0,olddecodes=io+mem,decodes=none:owns=io+mem
[    7.646838] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  260.19.36  Tue Jan 18 16:56:11 PST 2011
[    7.776040] audit_printk_skb: 21 callbacks suppressed
[    7.776041] type=1400 audit(1299115252.014:18): apparmor="STATUS" operation="profile_replace" name="/usr/lib/cups/backend/cups-pdf" pid=1280 comm="apparmor_parser"
[    7.776379] type=1400 audit(1299115252.014:19): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/cupsd" pid=1280 comm="apparmor_parser"
[    7.780939] ppdev: user-space parallel port driver
[    8.624660] HDMI hot plug event: Pin=5 Presence_Detect=1 ELD_Valid=0
[    8.673559] HDMI hot plug event: Pin=5 Presence_Detect=0 ELD_Valid=1
[    9.604332] EXT4-fs (sda1): re-mounted. Opts: discard,commit=0,commit=0
[    9.605351] EXT4-fs (sdb): re-mounted. Opts: data=writeback,commit=0
[   10.605443] HDMI: detected monitor ASUS VH236H
[   10.605444]  at connection type HDMI
[   10.605446] HDMI: available speakers: FL/FR
[   10.605448] HDMI: supports coding type LPCM: channels = 2, rates = 44100 48000 88200, bits = 16
[   11.857452] hda-intel: IRQ timing workaround is activated for card #1. Suggest a bigger bdl_pos_adj.
[   16.231086] eth0: no IPv6 routers present
[   30.138244] lo: Disabled Privacy Extensions
[ 1021.022950] usb 2-1.8: new high speed USB device using ehci_hcd and address 5
[ 1021.160001] Initializing USB Mass Storage driver...
[ 1021.160298] scsi14 : usb-storage 2-1.8:1.0
[ 1021.160419] usbcore: registered new interface driver usb-storage
[ 1021.160421] USB Mass Storage support registered.
[ 1022.200703] scsi 14:0:0:0: Direct-Access     Kingston DataTraveler 2.0 PMAP PQ: 0 ANSI: 0 CCS
[ 1022.201454] sd 14:0:0:0: Attached scsi generic sg4 type 0
[ 1023.612278] sd 14:0:0:0: [sdc] 15675392 512-byte logical blocks: (8.02 GB/7.47 GiB)
[ 1023.612889] sd 14:0:0:0: [sdc] Write Protect is off
[ 1023.612894] sd 14:0:0:0: [sdc] Mode Sense: 23 00 00 00
[ 1023.612897] sd 14:0:0:0: [sdc] Assuming drive cache: write through
[ 1023.616607] sd 14:0:0:0: [sdc] Assuming drive cache: write through
[ 1023.616614]  sdc: sdc1
[ 1023.657407] sd 14:0:0:0: [sdc] Assuming drive cache: write through
[ 1023.657412] sd 14:0:0:0: [sdc] Attached SCSI removable disk
[ 1074.344459] usb 2-1.8: USB disconnect, address 5
[ 1080.587658] usb 2-1.6.3: new high speed USB device using ehci_hcd and address 6
[ 1080.705574] scsi15 : usb-storage 2-1.6.3:1.0
[ 1080.806032] usb 2-1.6.3: USB disconnect, address 6
[ 1081.037650] usb 2-1.6.3: new high speed USB device using ehci_hcd and address 7
[ 1081.153620] scsi16 : usb-storage 2-1.6.3:1.0
[ 1082.195882] scsi 16:0:0:0: Direct-Access     Kingston DataTraveler 2.0 PMAP PQ: 0 ANSI: 0 CCS
[ 1082.196836] sd 16:0:0:0: Attached scsi generic sg4 type 0
[ 1083.596204] sd 16:0:0:0: [sdc] 15675392 512-byte logical blocks: (8.02 GB/7.47 GiB)
[ 1083.596804] sd 16:0:0:0: [sdc] Write Protect is off
[ 1083.596809] sd 16:0:0:0: [sdc] Mode Sense: 23 00 00 00
[ 1083.596812] sd 16:0:0:0: [sdc] Assuming drive cache: write through
[ 1083.600513] sd 16:0:0:0: [sdc] Assuming drive cache: write through
[ 1083.600519]  sdc: sdc1
[ 1083.640919] sd 16:0:0:0: [sdc] Assuming drive cache: write through
[ 1083.640925] sd 16:0:0:0: [sdc] Attached SCSI removable disk

```

---

### Post by bugreporter11 on 2011-04-24
I found your post because of this error:
 xhci_hcd 0000:02:00.0: WARN: Stalled endpoint

we both have several similar error messages. In particular, I am also getting this:
WARN: short transfer on control ep

I don't know what those errors mean, but I'm getting them with a LiveCD of Natty beta2 (32bit) on a Gigabyte motherboard with USB 3.0. I think that's the same brand mobo you have and I assume yours has USB 3 too.

I have seen the exact same problem with Maverick 64bit installed on the system (same mobo).

I get an error dialog with this info:

Error: Unable to mount KINGSTON
A job is pending on /dev/sdg1

It happens with any USB flash drive.

Syslog:

```

Apr 24 15:59:04 ubuntu kernel: [ 3852.153784] usb 10-4: new high speed USB device using xhci_hcd and address 22
Apr 24 15:59:04 ubuntu kernel: [ 3852.171606] xhci_hcd 0000:02:00.0: WARN: short transfer on control ep
Apr 24 15:59:04 ubuntu kernel: [ 3852.172055] xhci_hcd 0000:02:00.0: WARN: short transfer on control ep
Apr 24 15:59:04 ubuntu kernel: [ 3852.172443] xhci_hcd 0000:02:00.0: WARN: short transfer on control ep
Apr 24 15:59:04 ubuntu kernel: [ 3852.172927] xhci_hcd 0000:02:00.0: WARN: short transfer on control ep
Apr 24 15:59:04 ubuntu kernel: [ 3852.174111] scsi46 : usb-storage 10-4:1.0
Apr 24 15:59:05 ubuntu kernel: [ 3853.173751] scsi 46:0:0:0: Direct-Access     Single   Flash Reader     1.00 PQ: 0 ANSI: 0
Apr 24 15:59:05 ubuntu kernel: [ 3853.175151] sd 46:0:0:0: Attached scsi generic sg7 type 0
Apr 24 15:59:05 ubuntu kernel: [ 3853.597743] sd 46:0:0:0: [sdg] 62720 512-byte logical blocks: (32.1 MB/30.6 MiB)
Apr 24 15:59:05 ubuntu kernel: [ 3853.597954] xhci_hcd 0000:02:00.0: WARN: Stalled endpoint
Apr 24 15:59:05 ubuntu kernel: [ 3853.598479] sd 46:0:0:0: [sdg] Write Protect is off
Apr 24 15:59:05 ubuntu kernel: [ 3853.598485] sd 46:0:0:0: [sdg] Mode Sense: 03 00 00 00
Apr 24 15:59:05 ubuntu kernel: [ 3853.599028] sd 46:0:0:0: [sdg] No Caching mode page present
Apr 24 15:59:05 ubuntu kernel: [ 3853.599034] sd 46:0:0:0: [sdg] Assuming drive cache: write through
Apr 24 15:59:05 ubuntu kernel: [ 3853.600561] xhci_hcd 0000:02:00.0: WARN: Stalled endpoint
Apr 24 15:59:05 ubuntu kernel: [ 3853.601439] sd 46:0:0:0: [sdg] No Caching mode page present
Apr 24 15:59:05 ubuntu kernel: [ 3853.601444] sd 46:0:0:0: [sdg] Assuming drive cache: write through
Apr 24 15:59:05 ubuntu kernel: [ 3853.604333]  sdg: sdg1
Apr 24 15:59:05 ubuntu kernel: [ 3853.606715] xhci_hcd 0000:02:00.0: WARN: Stalled endpoint
Apr 24 15:59:05 ubuntu kernel: [ 3853.607607] sd 46:0:0:0: [sdg] No Caching mode page present
Apr 24 15:59:05 ubuntu kernel: [ 3853.607613] sd 46:0:0:0: [sdg] Assuming drive cache: write through
Apr 24 15:59:05 ubuntu kernel: [ 3853.607617] sd 46:0:0:0: [sdg] Attached SCSI removable disk
Apr 24 16:00:29 ubuntu kernel: [ 3937.126803] CE: hpet5 increased min_delta_ns to 7500 nsec
Apr 24 16:00:29 ubuntu kernel: [ 3937.126812] CE: hpet5 increased min_delta_ns to 11250 nsec

```

---

