---
title: "Slow Boot after removing Dual boot"
date: 2012-02-06
forum: General Help
---

### Post by che47audio on 2012-02-06
Hi,
Hopefully this is a simple problem to solve.
I _was_ dual booting ubuntu 11.10 with windows 7 on a partitioned sata (160gb, split evenly to two 80gb partitions).

I began to enjoy ubuntu alot more and discovered virtualbox and therefore had no need for the windows partition. Using gparted on a live disc I glued the partitions so now ubuntu has the whole 160gb drive to itself- works well.

My issue is this-

When I got rid of the windows installation I longer expected to see the grub 2 menu, as i have also deleted all unused kernels, I still see it every boot. This lengthens the boot time by at least 5 seconds. On top of that Ubuntu seems to boot very slowly anyhow.
My pc has 4gb ram and an AMD Phenom II X2 560 Processor
Should boot time be less than 1min 30secs? Any ideas appreciated

Thanks for your time

---

### Post by runny6play on 2012-02-06
U need to set gr to default boot ubuntu in the config file

---

### Post by L a r r y on 2012-02-06
> **che47audio said:**
> 
My issue is this-

When I got rid of the windows installation I **[no]** longer expected to see the grub 2 menu, as i have also deleted all unused kernels, **[but]** I still see it every boot. This lengthens the boot time by at least 5 seconds. On top of that Ubuntu seems to boot very slowly anyhow.
My pc has 4gb ram and an AMD Phenom II X2 560 Processor
Should boot time be less than 1min 30secs? Any ideas appreciated

Thanks for your time

SOMEwhere in Administration or Preferences on the System menu I remember there once was a tool on the menu that would let me tailor the behavior of the old GRUB (now GRUB 1).  I am running 10.04 with GRUB 2.  I didn't used to see GRUB menu at all, as I had no dual boot going on here.  But ever since I've hit a keystroke to invoke GRUB's appearance, I see that menu every boot.

One way to shave off the five seconds is to hit ENTER as soon as the menu appears.

Better yet, check out this [SOLVED] thread to cut GRUB 2 from 10 seconds to X seconds:  _**[http://ubuntuforums.org/showthread.php?t=1314292](http://ubuntuforums.org/showthread.php?t=1314292)**_
(I haven't read it yet), or see this Introduction to GRUB 2: **_[http://ubuntuforums.org/showthread.php?t=1285897](http://ubuntuforums.org/showthread.php?t=1285897)_**

I am going to read up on these two postings and see if I can resolve my issue with GRUB.

I hope someone more knowledgeable about boot issues can step forward.  You will likely be asked to run various commands and report back the output, and output of some log files.

Boot time can be reduced by removing some programs from your startup, like say, Bluetooth if you have no use for its existence, as an example.  The fewer programs loading at startup to be ready to fly at any time you may need them, the faster things that need to be there will load.

Hope I have been of some help!

---

### Post by drs305 on 2012-02-06
Grub Customizer will allow you to easily change the timeout to less than the default 10 seconds, but if Ubuntu is your only OS you really shouldn't be seeing the menu regardless unless you have instructed Grub to do so.

If you run the Boot Info Script and post the contents of RESULTS.txt perhaps we can see if there are any 'structural' problems with your Grub files. You can run the script directly (BIS) or via the Boot Repair (Boot Repair) app. Links to both are in my signature line.

---

### Post by che47audio on 2012-02-14
The results of this script are attached.

Thanks for your help.

---

### Post by drs305 on 2012-02-15
Your timeout is still set to 10 seconds. You might take that down to 1 second to speed up the boot. You could set it to 0 so you never see the menu, but if you do that test to make sure holding down the SHIFT key during boot displays the menu. 

The timeout setting is established in /etc/default/grub.

I'm not sure why your menu is displaying. I'm on a trip but when I return home later this week I'll try experimenting with your grub.cfg.

One other thing you could try would be to edit your /etc/fstab file as root and place 'noauto' on your vfat partition listing. This would prevent it from trying to mount during boot, and if your boot suddenly speeds up this might be the reason it is currently slow to boot. Rather than 'noauto', you could also just place a # symbol at the start of the line to eliminate the entry for testing purposes.

---

### Post by che47audio on 2012-02-16
Thanks for your advice. I reduced the timeout to one second which shaves 9 secs off the boot time. This is pleasing however I'm convinced there is something else wrong a little deeper than this.
I have ran the "dmesg" command in the terminal and here are the results of that:

```


[    0.474984] pci 0000:00:02.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    0.474987] pci 0000:00:02.0: setting latency timer to 64
[    0.474993] pci 0000:00:09.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    0.474996] pci 0000:00:09.0: setting latency timer to 64
[    0.475007] pci 0000:00:15.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.475009] pci 0000:00:15.0: setting latency timer to 64
[    0.475012] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
[    0.475013] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff]
[    0.475015] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
[    0.475017] pci_bus 0000:00: resource 7 [mem 0x000d0000-0x000dffff]
[    0.475018] pci_bus 0000:00: resource 8 [mem 0xc7f00000-0xdfffffff]
[    0.475020] pci_bus 0000:00: resource 9 [mem 0xf0000000-0xfebfffff]
[    0.475021] pci_bus 0000:04: resource 0 [io  0xe000-0xefff]
[    0.475023] pci_bus 0000:04: resource 1 [mem 0xfe900000-0xfe9fffff]
[    0.475024] pci_bus 0000:04: resource 2 [mem 0xd0000000-0xdfffffff 64bit pref]
[    0.475026] pci_bus 0000:03: resource 0 [io  0xd000-0xdfff]
[    0.475028] pci_bus 0000:02: resource 4 [io  0x0000-0x0cf7]
[    0.475029] pci_bus 0000:02: resource 5 [io  0x0d00-0xffff]
[    0.475031] pci_bus 0000:02: resource 6 [mem 0x000a0000-0x000bffff]
[    0.475032] pci_bus 0000:02: resource 7 [mem 0x000d0000-0x000dffff]
[    0.475034] pci_bus 0000:02: resource 8 [mem 0xc7f00000-0xdfffffff]
[    0.475035] pci_bus 0000:02: resource 9 [mem 0xf0000000-0xfebfffff]
[    0.475037] pci_bus 0000:01: resource 0 [io  0xc000-0xcfff]
[    0.475038] pci_bus 0000:01: resource 1 [mem 0xfe800000-0xfe8fffff]
[    0.475040] pci_bus 0000:01: resource 2 [mem 0xcff00000-0xcfffffff 64bit pref]
[    0.475064] NET: Registered protocol family 2
[    0.475171] IP route cache hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.475994] TCP established hash table entries: 524288 (order: 11, 8388608 bytes)
[    0.477921] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[    0.478158] TCP: Hash tables configured (established 524288 bind 65536)
[    0.478159] TCP reno registered
[    0.478167] UDP hash table entries: 2048 (order: 4, 65536 bytes)
[    0.478190] UDP-Lite hash table entries: 2048 (order: 4, 65536 bytes)
[    0.478285] NET: Registered protocol family 1
[    1.536081] pci 0000:04:00.0: Boot video device
[    1.536089] PCI: CLS 64 bytes, default 64
[    1.537033] PCI-DMA: Disabling AGP.
[    1.537092] PCI-DMA: aperture base @ bc000000 size 65536 KB
[    1.537093] PCI-DMA: using GART IOMMU.
[    1.537095] PCI-DMA: Reserving 64MB of IOMMU area in the AGP aperture
[    1.542345] audit: initializing netlink socket (disabled)
[    1.542354] type=2000 audit(1329436833.540:1): initialized
[    1.563113] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    1.578545] VFS: Disk quotas dquot_6.5.2
[    1.578585] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    1.579023] fuse init (API version 7.16)
[    1.579100] msgmni has been set to 7912
[    1.579446] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    1.579475] io scheduler noop registered
[    1.579476] io scheduler deadline registered
[    1.579505] io scheduler cfq registered (default)
[    1.579609] pcieport 0000:00:02.0: setting latency timer to 64
[    1.579633] pcieport 0000:00:02.0: irq 40 for MSI/MSI-X
[    1.579707] pcieport 0000:00:09.0: setting latency timer to 64
[    1.579725] pcieport 0000:00:09.0: irq 41 for MSI/MSI-X
[    1.579795] pcieport 0000:00:15.0: setting latency timer to 64
[    1.579827] pcieport 0000:00:15.0: irq 42 for MSI/MSI-X
[    1.579897] pcieport 0000:00:02.0: Signaling PME through PCIe PME interrupt
[    1.579899] pci 0000:04:00.0: Signaling PME through PCIe PME interrupt
[    1.579900] pci 0000:04:00.1: Signaling PME through PCIe PME interrupt
[    1.579903] pcie_pme 0000:00:02.0:pcie01: service driver pcie_pme loaded
[    1.579916] pcieport 0000:00:09.0: Signaling PME through PCIe PME interrupt
[    1.579917] pci 0000:03:00.0: Signaling PME through PCIe PME interrupt
[    1.579919] pcie_pme 0000:00:09.0:pcie01: service driver pcie_pme loaded
[    1.579932] pcieport 0000:00:15.0: Signaling PME through PCIe PME interrupt
[    1.579934] pci 0000:01:00.0: Signaling PME through PCIe PME interrupt
[    1.579936] pcie_pme 0000:00:15.0:pcie01: service driver pcie_pme loaded
[    1.579946] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    1.579961] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    1.580054] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0
[    1.580057] ACPI: Power Button [PWRB]
[    1.580084] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
[    1.580086] ACPI: Power Button [PWRF]
[    1.580103] ACPI: acpi_idle registered with cpuidle
[    1.580128] ACPI: processor limited to max C-state 1
[    1.612690] ERST: Table is not found!
[    1.612733] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    1.633080] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    1.654634] 00:05: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    1.654847] Linux agpgart interface v0.103
[    1.655449] brd: module loaded
[    1.655727] loop: module loaded
[    1.655875] pata_acpi 0000:00:14.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    1.655895] pata_acpi 0000:00:14.1: setting latency timer to 64
[    1.655943] pata_acpi 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    1.655957] pata_acpi 0000:03:00.0: setting latency timer to 64
[    1.655965] pata_acpi 0000:03:00.0: PCI INT A disabled
[    1.656203] Fixed MDIO Bus: probed
[    1.656216] PPP generic driver version 2.4.2
[    1.656241] tun: Universal TUN/TAP device driver, 1.6
[    1.656242] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    1.656287] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    1.656318] ehci_hcd 0000:00:12.2: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    1.656334] ehci_hcd 0000:00:12.2: EHCI Host Controller
[    1.656372] ehci_hcd 0000:00:12.2: new USB bus registered, assigned bus number 1
[    1.656378] ehci_hcd 0000:00:12.2: applying AMD SB700/SB800/Hudson-2/3 EHCI dummy qh workaround
[    1.656396] QUIRK: Enable AMD PLL fix
[    1.656404] ehci_hcd 0000:00:12.2: debug port 1
[    1.656421] ehci_hcd 0000:00:12.2: irq 17, io mem 0xfe7fe400
[    1.668050] ehci_hcd 0000:00:12.2: USB 2.0 started, EHCI 1.00
[    1.668133] hub 1-0:1.0: USB hub found
[    1.668136] hub 1-0:1.0: 5 ports detected
[    1.668222] ehci_hcd 0000:00:13.2: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    1.668233] ehci_hcd 0000:00:13.2: EHCI Host Controller
[    1.668256] ehci_hcd 0000:00:13.2: new USB bus registered, assigned bus number 2
[    1.668261] ehci_hcd 0000:00:13.2: applying AMD SB700/SB800/Hudson-2/3 EHCI dummy qh workaround
[    1.668277] ehci_hcd 0000:00:13.2: debug port 1
[    1.668287] ehci_hcd 0000:00:13.2: irq 17, io mem 0xfe7fe800
[    1.680047] ehci_hcd 0000:00:13.2: USB 2.0 started, EHCI 1.00
[    1.680115] hub 2-0:1.0: USB hub found
[    1.680118] hub 2-0:1.0: 5 ports detected
[    1.680206] ehci_hcd 0000:00:16.2: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    1.680217] ehci_hcd 0000:00:16.2: EHCI Host Controller
[    1.680237] ehci_hcd 0000:00:16.2: new USB bus registered, assigned bus number 3
[    1.680243] ehci_hcd 0000:00:16.2: applying AMD SB700/SB800/Hudson-2/3 EHCI dummy qh workaround
[    1.680258] ehci_hcd 0000:00:16.2: debug port 1
[    1.680267] ehci_hcd 0000:00:16.2: irq 17, io mem 0xfe7fec00
[    1.692047] ehci_hcd 0000:00:16.2: USB 2.0 started, EHCI 1.00
[    1.692116] hub 3-0:1.0: USB hub found
[    1.692119] hub 3-0:1.0: 4 ports detected
[    1.692177] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    1.692218] ohci_hcd 0000:00:12.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    1.692228] ohci_hcd 0000:00:12.0: OHCI Host Controller
[    1.692255] ohci_hcd 0000:00:12.0: new USB bus registered, assigned bus number 4
[    1.692273] ohci_hcd 0000:00:12.0: irq 18, io mem 0xfe7f7000
[    1.752097] hub 4-0:1.0: USB hub found
[    1.752103] hub 4-0:1.0: 5 ports detected
[    1.752191] ohci_hcd 0000:00:13.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    1.752201] ohci_hcd 0000:00:13.0: OHCI Host Controller
[    1.752224] ohci_hcd 0000:00:13.0: new USB bus registered, assigned bus number 5
[    1.752237] ohci_hcd 0000:00:13.0: irq 18, io mem 0xfe7fc000
[    1.812094] hub 5-0:1.0: USB hub found
[    1.812099] hub 5-0:1.0: 5 ports detected
[    1.812193] ohci_hcd 0000:00:14.5: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    1.812205] ohci_hcd 0000:00:14.5: OHCI Host Controller
[    1.812226] ohci_hcd 0000:00:14.5: new USB bus registered, assigned bus number 6
[    1.812238] ohci_hcd 0000:00:14.5: irq 18, io mem 0xfe7fd000
[    1.872102] hub 6-0:1.0: USB hub found
[    1.872107] hub 6-0:1.0: 2 ports detected
[    1.872198] ohci_hcd 0000:00:16.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    1.872210] ohci_hcd 0000:00:16.0: OHCI Host Controller
[    1.872235] ohci_hcd 0000:00:16.0: new USB bus registered, assigned bus number 7
[    1.872247] ohci_hcd 0000:00:16.0: irq 18, io mem 0xfe7ff000
[    1.932099] hub 7-0:1.0: USB hub found
[    1.932104] hub 7-0:1.0: 4 ports detected
[    1.932167] uhci_hcd: USB Universal Host Controller Interface driver
[    1.932206] i8042: PNP: PS/2 Controller [PNP0303:PS2K] at 0x60,0x64 irq 1
[    1.932207] i8042: PNP: PS/2 appears to have AUX port disabled, if this is incorrect please boot with i8042.nopnp
[    1.932314] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.932364] mousedev: PS/2 mouse device common for all mice
[    1.932421] rtc_cmos 00:02: RTC can wake from S4
[    1.932480] rtc_cmos 00:02: rtc core: registered rtc_cmos as rtc0
[    1.932498] rtc0: alarms up to one month, y3k, 114 bytes nvram, hpet irqs
[    1.932553] device-mapper: uevent: version 1.0.3
[    1.932592] device-mapper: ioctl: 4.20.0-ioctl (2011-02-02) initialised: [email]dm-devel@redhat.com[/email]
[    1.932598] cpuidle: using governor ladder
[    1.932599] cpuidle: using governor menu
[    1.932600] EFI Variables Facility v0.08 2004-May-17
[    1.932733] TCP cubic registered
[    1.932804] NET: Registered protocol family 10
[    1.933097] NET: Registered protocol family 17
[    1.933106] Registering the dns_resolver key type
[    1.933158] PM: Hibernation image not present or could not be loaded.
[    1.933164] registered taskstats version 1
[    1.944715]   Magic number: 0:210:1
[    1.944789] rtc_cmos 00:02: setting system clock to 2012-02-17 00:00:34 UTC (1329436834)
[    1.944795] powernow-k8: Found 1 AMD Phenom(tm) II X2 560 Processor (2 cpu cores) (version 2.20.00)
[    1.944818] powernow-k8:    0 : pstate 0 (3300 MHz)
[    1.944819] powernow-k8:    1 : pstate 1 (2600 MHz)
[    1.944820] powernow-k8:    2 : pstate 2 (2200 MHz)
[    1.944821] powernow-k8:    3 : pstate 3 (800 MHz)
[    1.945057] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.945059] EDD information not available.
[    1.946177] Freeing unused kernel memory: 988k freed
[    1.946357] Write protecting the kernel read-only data: 12288k
[    1.951214] Freeing unused kernel memory: 2036k freed
[    1.954878] Freeing unused kernel memory: 1388k freed
[    1.962048] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input2
[    1.966051] udevd[120]: starting version 173
[    2.009061] ahci 0000:00:11.0: version 3.0
[    2.009080] ahci 0000:00:11.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    2.009116] ahci 0000:00:11.0: irq 43 for MSI/MSI-X
[    2.009182] ahci 0000:00:11.0: AHCI 0001.0200 32 slots 4 ports 6 Gbps 0xf impl SATA mode
[    2.009185] ahci 0000:00:11.0: flags: 64bit ncq sntf ilck pm led clo pmp pio slum part 
[    2.011443] scsi0 : ahci
[    2.012665] scsi1 : ahci
[    2.013339] scsi2 : ahci
[    2.013441] pata_jmicron 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    2.013466] pata_jmicron 0000:03:00.0: setting latency timer to 64
[    2.014175] scsi3 : ahci
[    2.014250] ata1: SATA max UDMA/133 abar m1024@0xfe7fe000 port 0xfe7fe100 irq 43
[    2.014253] ata2: SATA max UDMA/133 abar m1024@0xfe7fe000 port 0xfe7fe180 irq 43
[    2.014256] ata3: SATA max UDMA/133 abar m1024@0xfe7fe000 port 0xfe7fe200 irq 43
[    2.014258] ata4: SATA max UDMA/133 abar m1024@0xfe7fe000 port 0xfe7fe280 irq 43
[    2.014296] scsi4 : pata_jmicron
[    2.014695] scsi5 : pata_jmicron
[    2.014947] ata5: PATA max UDMA/100 cmd 0xdc00 ctl 0xd880 bmdma 0xd400 irq 17
[    2.014949] ata6: PATA max UDMA/100 cmd 0xd800 ctl 0xd480 bmdma 0xd408 irq 17
[    2.022537] scsi6 : pata_atiixp
[    2.024474] scsi7 : pata_atiixp
[    2.024871] ata7: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xff00 irq 14
[    2.024874] ata8: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xff08 irq 15
[    2.024891] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    2.024908] r8169 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    2.024943] r8169 0000:01:00.0: setting latency timer to 64
[    2.024992] r8169 0000:01:00.0: irq 44 for MSI/MSI-X
[    2.025266] r8169 0000:01:00.0: eth0: RTL8168e/8111e at 0xffffc9000065a000, 48:5b:39:ee:a5:ce, XID 0c100000 IRQ 44
[    2.332099] usb 5-5: new low speed USB device number 2 using ohci_hcd
[    2.504041] ata4: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    2.504061] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    2.504081] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    2.504096] ata2: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    2.505480] ata3.00: ATAPI: TSSTcorp CDDVDW SH-S223C, SB04, max UDMA/100
[    2.505953] ata4.00: ATA-7: SAMSUNG SP1213C, SV100-27, max UDMA7
[    2.505955] ata4.00: 234493056 sectors, multi 16: LBA48 
[    2.507925] ata4.00: configured for UDMA/133
[    2.509772] ata2.00: ATA-8: SAMSUNG HD103SJ, 1AJ10001, max UDMA/133
[    2.509774] ata2.00: 1953525168 sectors, multi 16: LBA48 NCQ (depth 31/32), AA
[    2.515482] ata2.00: configured for UDMA/133
[    2.540041] Refined TSC clocksource calibration: 3311.102 MHz.
[    2.540049] Switching to clocksource tsc
[    2.549078] ata1.00: ATA-7: ST3160811AS, 3.AAE, max UDMA/133
[    2.549080] ata1.00: 312581808 sectors, multi 16: LBA48 NCQ (depth 31/32)
[    2.607379] ata1.00: configured for UDMA/133
[    2.607492] scsi 0:0:0:0: Direct-Access     ATA      ST3160811AS      3.AA PQ: 0 ANSI: 5
[    2.607587] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    2.607628] sd 0:0:0:0: [sda] 312581808 512-byte logical blocks: (160 GB/149 GiB)
[    2.607658] sd 0:0:0:0: [sda] Write Protect is off
[    2.607660] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    2.607664] scsi 1:0:0:0: Direct-Access     ATA      SAMSUNG HD103SJ  1AJ1 PQ: 0 ANSI: 5
[    2.607672] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.607764] sd 1:0:0:0: Attached scsi generic sg1 type 0
[    2.607807] sd 1:0:0:0: [sdb] 1953525168 512-byte logical blocks: (1.00 TB/931 GiB)
[    2.607836] sd 1:0:0:0: [sdb] Write Protect is off
[    2.607838] sd 1:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[    2.607855] sd 1:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.617171]  sdb: sdb1
[    2.617357] sd 1:0:0:0: [sdb] Attached SCSI disk
[    2.659597]  sda: sda2 < sda5 sda6 >
[    2.659798] sd 0:0:0:0: [sda] Attached SCSI disk
[    2.764035] usb 4-5: new full speed USB device number 2 using ohci_hcd
[    3.306495] ata3.00: configured for UDMA/100
[    4.108476] scsi 2:0:0:0: CD-ROM            TSSTcorp CDDVDW SH-S223C  SB04 PQ: 0 ANSI: 5
[    4.111697] sr0: scsi3-mmc drive: 52x/52x writer dvd-ram cd/rw xa/form2 cdda tray
[    4.111699] cdrom: Uniform CD-ROM driver Revision: 3.20
[    4.111777] sr 2:0:0:0: Attached scsi CD-ROM sr0
[    4.111812] sr 2:0:0:0: Attached scsi generic sg2 type 5
[    4.111903] scsi 3:0:0:0: Direct-Access     ATA      SAMSUNG SP1213C  SV10 PQ: 0 ANSI: 5
[    4.111976] sd 3:0:0:0: Attached scsi generic sg3 type 0
[    4.112023] sd 3:0:0:0: [sdc] 234493056 512-byte logical blocks: (120 GB/111 GiB)
[    4.112049] sd 3:0:0:0: [sdc] Write Protect is off
[    4.112051] sd 3:0:0:0: [sdc] Mode Sense: 00 3a 00 00
[    4.112062] sd 3:0:0:0: [sdc] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    4.115835]  sdc: sdc1
[    4.115994] sd 3:0:0:0: [sdc] Attached SCSI disk
[    4.272208] input: PIXART USB OPTICAL MOUSE as /devices/pci0000:00/0000:00:13.0/usb5/5-5/5-5:1.0/input/input3
[    4.272274] generic-usb 0003:093A:2510.0001: input,hidraw0: USB HID v1.11 Mouse [PIXART USB OPTICAL MOUSE] on usb-0000:00:13.0-5/input0
[    4.272287] usbcore: registered new interface driver usbhid
[    4.272288] usbhid: USB HID core driver
[    9.712133] EXT4-fs (sda6): INFO: recovery required on readonly filesystem
[    9.712136] EXT4-fs (sda6): write access will be enabled during recovery
[   13.005988] EXT4-fs (sda6): orphan cleanup on readonly fs
[   13.005994] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 1054975
[   13.006056] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 1048631
[   13.034528] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 3407958
[   13.034535] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 3407944
[   13.034540] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 3407924
[   13.034545] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 3407914
[   13.034550] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 3407896
[   13.034554] EXT4-fs (sda6): 7 orphan inodes deleted
[   13.034555] EXT4-fs (sda6): recovery complete
[   13.413731] EXT4-fs (sda6): mounted filesystem with ordered data mode. Opts: (null)
[   34.848038] ata3.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6 frozen
[   34.848042] ata3.00: failed command: IDENTIFY PACKET DEVICE
[   34.848046] ata3.00: cmd a1/00:01:00:00:00/00:00:00:00:00/00 tag 0 pio 512 in
[   34.848046]          res 40/00:03:00:00:00/00:00:00:00:00/a0 Emask 0x4 (timeout)
[   34.848048] ata3.00: status: { DRDY }
[   34.848051] ata3: hard resetting link
[   35.340048] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[   36.141870] ata3.00: configured for UDMA/100
[   36.942692] ata3: EH complete
[   39.529902] Adding 2987004k swap on /dev/sda5.  Priority:-1 extents:1 across:2987004k 
[   39.949004] udevd[407]: starting version 173
[   42.208743] lp: driver loaded but no devices found
[   43.139427] wmi: Mapper loaded
[   43.159117] MCE: In-kernel MCE decoding enabled.
[   43.167880] EDAC MC: Ver: 2.1.0
[   43.366695] ATK0110 ATK0110:00: EC enabled
[   43.832469] AMD64 EDAC driver v3.4.0
[   43.832537] EDAC amd64: DRAM ECC disabled.
[   43.832543] EDAC amd64: ECC disabled in the BIOS or no ECC capability, module will not load.
[   43.832544]  Either enable ECC checking or force module loading by setting 'ecc_enable_override'.
[   43.832545]  (Note that use of the override may cause unknown side effects.)
[   43.994381] piix4_smbus 0000:00:14.0: SMBus Host Controller at 0xb00, revision 0
[   44.039355] SP5100 TCO timer: SP5100 TCO WatchDog Timer Driver v0.01
[   44.039404] SP5100 TCO timer: mmio address 0xb8fe00 already in use
[   44.486539] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
[   44.486542] Disabling lock debugging due to kernel taint
[   44.519251] [fglrx] Maximum main memory to use for locked dma buffers: 3798 MBytes.
[   44.519322] [fglrx]   vendor: 1002 device: 68da count: 1
[   44.519612] [fglrx] ioport: bar 4, base 0xe000, size: 0x100
[   44.519622] pci 0000:04:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[   44.519626] pci 0000:04:00.0: setting latency timer to 64
[   44.519870] [fglrx] Kernel PAT support is enabled
[   44.519883] [fglrx] module loaded - fglrx 8.88.7 [Jul 28 2011] with 1 minors
[   44.794828] Bluetooth: Core ver 2.16
[   44.794846] NET: Registered protocol family 31
[   44.794848] Bluetooth: HCI device and connection manager initialized
[   44.794849] Bluetooth: HCI socket layer initialized
[   44.794851] Bluetooth: L2CAP socket layer initialized
[   44.795359] Bluetooth: SCO socket layer initialized
[   44.806838] Bluetooth: Generic Bluetooth USB driver ver 0.6
[   44.807104] usbcore: registered new interface driver btusb
[   45.779888] type=1400 audit(1329436878.333:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=709 comm="apparmor_parser"
[   45.779900] type=1400 audit(1329436878.333:3): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=789 comm="apparmor_parser"
[   45.780212] type=1400 audit(1329436878.333:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=709 comm="apparmor_parser"
[   45.780234] type=1400 audit(1329436878.333:5): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=789 comm="apparmor_parser"
[   45.780399] type=1400 audit(1329436878.333:6): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=709 comm="apparmor_parser"
[   45.780425] type=1400 audit(1329436878.333:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=789 comm="apparmor_parser"
[   46.216247] type=1400 audit(1329436878.769:8): apparmor="STATUS" operation="profile_load" name="/usr/sbin/ntpd" pid=861 comm="apparmor_parser"
[   46.216260] type=1400 audit(1329436878.769:9): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/ntpd" pid=860 comm="apparmor_parser"
[   46.578940] HDA Intel 0000:00:14.2: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   46.689806] HDA Intel 0000:04:00.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[   46.689867] HDA Intel 0000:04:00.1: irq 45 for MSI/MSI-X
[   46.689885] HDA Intel 0000:04:00.1: setting latency timer to 64
[   46.890358] HDMI status: Pin=3 Presence_Detect=0 ELD_Valid=0
[   46.890442] input: HD-Audio Generic HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:02.0/0000:04:00.1/sound/card1/input4
[   64.272133] usb 5-5: USB disconnect, device number 2
[   65.840025] usb 5-5: new low speed USB device number 3 using ohci_hcd
[   66.016236] input: PIXART USB OPTICAL MOUSE as /devices/pci0000:00/0000:00:13.0/usb5/5-5/5-5:1.0/input/input5
[   66.016354] generic-usb 0003:093A:2510.0002: input,hidraw0: USB HID v1.11 Mouse [PIXART USB OPTICAL MOUSE] on usb-0000:00:13.0-5/input0
[   66.787345] EXT4-fs (sda6): re-mounted. Opts: (null)
[   66.993566] RPC: Registered named UNIX socket transport module.
[   66.993568] RPC: Registered udp transport module.
[   66.993570] RPC: Registered tcp transport module.
[   66.993571] RPC: Registered tcp NFSv4.1 backchannel transport module.
[   67.009008] FS-Cache: Loaded
[   67.850284] FS-Cache: Netfs 'nfs' registered for caching
[   68.633454] Installing knfsd (copyright (C) 1996 [email]okir@monad.swb.de[/email]).
[   71.088696] type=1400 audit(1329436903.641:10): apparmor="STATUS" operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" pid=1117 comm="apparmor_parser"
[   71.090270] type=1400 audit(1329436903.641:11): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=1119 comm="apparmor_parser"
[   71.090597] type=1400 audit(1329436903.641:12): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=1119 comm="apparmor_parser"
[   71.090785] type=1400 audit(1329436903.641:13): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=1119 comm="apparmor_parser"
[   71.190134] type=1400 audit(1329436903.741:14): apparmor="STATUS" operation="profile_load" name="/usr/lib/lightdm/lightdm-guest-session-wrapper" pid=1118 comm="apparmor_parser"
[   71.281843] type=1400 audit(1329436903.833:15): apparmor="STATUS" operation="profile_load" name="/usr/lib/telepathy/mission-control-5" pid=1122 comm="apparmor_parser"
[   71.282169] type=1400 audit(1329436903.833:16): apparmor="STATUS" operation="profile_load" name="/usr/lib/telepathy/telepathy-*" pid=1122 comm="apparmor_parser"
[   71.354427] type=1400 audit(1329436903.905:17): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince" pid=1120 comm="apparmor_parser"
[   71.358394] type=1400 audit(1329436903.909:18): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince-previewer" pid=1120 comm="apparmor_parser"
[   71.360745] type=1400 audit(1329436903.913:19): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince-thumbnailer" pid=1120 comm="apparmor_parser"
[   71.847578] r8169 0000:01:00.0: eth0: link down
[   71.847588] r8169 0000:01:00.0: eth0: link down
[   71.847939] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   72.335920] init: failsafe main process (1040) killed by TERM signal
[   72.355727] init: apport pre-start process (1191) terminated with status 1
[   72.357471] init: apport post-stop process (1225) terminated with status 1
[   73.295860] NFSD: Using /var/lib/nfs/v4recovery as the NFSv4 state recovery directory
[   73.295880] NFSD: starting 90-second grace period
[   73.453891] r8169 0000:01:00.0: eth0: link up
[   73.454228] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   74.848049] ata3.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6 frozen
[   74.848053] ata3.00: failed command: IDENTIFY PACKET DEVICE
[   74.848057] ata3.00: cmd a1/00:01:00:00:00/00:00:00:00:00/00 tag 0 pio 512 in
[   74.848058]          res 40/00:03:00:00:00/00:00:00:00:00/a0 Emask 0x4 (timeout)
[   74.848060] ata3.00: status: { DRDY }
[   74.848063] ata3: hard resetting link
[   75.340052] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[   76.142252] ata3.00: configured for UDMA/100
[   76.297530] vboxdrv: Found 2 processor cores.
[   76.298018] vboxdrv: fAsync=0 offMin=0x3ca offMax=0xbe8
[   76.298516] vboxdrv: TSC mode is 'synchronous', kernel timer mode is 'normal'.
[   76.298518] vboxdrv: Successfully loaded version 4.1.2_Ubuntu (interface 0x00190000).
[   76.693143] vboxpci: IOMMU not found (not registered)
[   76.943049] ata3: EH complete
[   77.174617] vesafb: mode is 1400x1050x32, linelength=5632, pages=0
[   77.174619] vesafb: scrolling: redraw
[   77.174621] vesafb: Truecolor: size=0:8:8:8, shift=0:16:8:0
[   77.176227] vesafb: framebuffer at 0xd0000000, mapped to 0xffffc90012b00000, using 5824k, total 5824k
[   77.176402] Console: switching to colour frame buffer device 175x65
[   77.176422] fb0: VESA VGA frame buffer device
[   77.295672] ppdev: user-space parallel port driver
[   77.366692] audit_printk_skb: 18 callbacks suppressed
[   77.366695] type=1400 audit(1329436909.917:26): apparmor="STATUS" operation="profile_replace" name="/usr/lib/cups/backend/cups-pdf" pid=1635 comm="apparmor_parser"
[   77.367199] type=1400 audit(1329436909.917:27): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/cupsd" pid=1635 comm="apparmor_parser"
[   78.290841] init: gdm main process (1626) killed by TERM signal
[   83.359749] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   83.359751] Bluetooth: BNEP filters: protocol multicast
[   83.363524] Bluetooth: RFCOMM TTY layer initialized
[   83.363526] Bluetooth: RFCOMM socket layer initialized
[   83.363528] Bluetooth: RFCOMM ver 1.11
[   83.840025] eth0: no IPv6 routers present
[   85.565868] fglrx_pci 0000:04:00.0: irq 46 for MSI/MSI-X
[   85.566316] [fglrx] Firegl kernel thread PID: 1940
[   85.566385] [fglrx] Firegl kernel thread PID: 1941
[   85.566422] [fglrx] Firegl kernel thread PID: 1942
[   85.566660] [fglrx] IRQ 46 Enabled
[   86.357483] [fglrx] Gart USWC size:1240 M.
[   86.357486] [fglrx] Gart cacheable size:491 M.
[   86.357490] [fglrx] Reserved FB block: Shared offset:0, size:1000000 
[   86.357492] [fglrx] Reserved FB block: Unshared offset:f91f000, size:3e1000 
[   86.357493] [fglrx] Reserved FB block: Unshared offset:3fff4000, size:c000 
[   88.867550] EXT4-fs (sda6): re-mounted. Opts: commit=0
[   92.019486] init: plymouth-stop pre-start process (2067) terminated with status 1
[  101.193224] EXT4-fs (sda6): re-mounted. Opts: commit=0
[  101.983402] Bluetooth: HIDP (Human Interface Emulation) ver 1.2
[  101.995201] input: Apple Wireless Keyboard as /devices/pci0000:00/0000:00:12.0/usb4/4-5/4-5:1.0/bluetooth/hci0/hci0:38/input6
[  101.995303] apple 0005:05AC:023A.0003: input,hidraw1: BLUETOOTH HID v0.50 Keyboard [Apple Wireless Keyboard] on 00:15:83:3D:0A:57

```



I have tried disabling ACPI in the bios and grub , with no improvement. I also read that disabling USB legacy in the BIOS has helped others with similar slow boots, but no luck for me here. Something is clearly wrong here:

[   13.413731] EXT4-fs (sda6): mounted filesystem with ordered data mode. Opts: (null)
[   34.848038] ata3.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6 frozen

Why is it taking 21/22 seconds to mount this? Any help would be greatly appreciated, this is a new computer and should be booting much faster than this.

Thanks again

---

### Post by drs305 on 2012-02-17
I can't tell you why your system is acting the way it is. I compared your file with mine, and most of the output times are similar with a couple of exceptions. 

As you noted, there is a delay in sda6 where you mentioned, but also another 9 second delay near the end of the output:

```
[   92.019486] init: plymouth-stop pre-start process (2067) terminated with status 1
[  101.193224] EXT4-fs (sda6): re-mounted. Opts: commit=0

```

There is another 20 second delay here:
> 
[   46.890358] HDMI status: Pin=3 Presence_Detect=0 ELD_Valid=0
[   46.890442] input: HD-Audio Generic HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:02.0/0000:04:00.1/sound/card1/input4
[   64.272133] usb 5-5: USB disconnect, device number 2


I don't know if it's an HDMI or USB issue. If you have USB devices connected, you might try removing them to see if the boot time improves.

I also see Bluetooth loading. Although it doesn't take much time, if you aren't using Bluetooth you can disable it via Startup Applications.

Finally, I've added 'code' tags to your post to make it easier to read. When creating the post, you add the tags by pressing the # icon and pasting the content between the tags.

---

### Post by che47audio on 2012-02-19
Thanks for your response. I had tried booting with all USB devices disconnected. I do use a Bluetooth keyboard normally. I tried without and it made no difference, maybe half a second!
Thankyou for the tips on how to post correctly.

---

### Post by che47audio on 2012-03-04
I would just like to bump this post in hope that someone knows something that can resolve it. Thanks for all the help so far. From searching about I've found several people with the same issue but remains unsolved. So ......bump

---

### Post by PCFreak2 on 2012-03-04
Remember to run:

```
sudo update-grub
```

---

### Post by westie457 on 2012-03-04
An obvious (stupid) question for you.

Have you tried ```
sudo update-grub
```?

---

### Post by che47audio on 2012-03-04
Thanks for the speedy reply. Yes I have ran this to update grub,
But it made no difference....

The pc is 6 months old with a decent spec, it should boot faster than one and a half minutes to login screen surely?

---

### Post by oldfred on 2012-03-04
Have the filechecks run during booting fixd sda6? It looks like it is having issues mounting sda6 and runs a fsck to fix it. It is in several places in you log file:

> 
101.193224] EXT4-fs (sda6): re-mounted. Opts: commit=0

If not run a full e2fsck on sda6.

#From liveCD so everything is unmounted,swap off if necessary, change sda6 to your partition(s)
#e2fsck is used to check the ext2/ext3/ext4 family of file systems.
sudo e2fsck -C0 -p -f -v /dev/sda6
#if errors:
sudo e2fsck -f -y -v /dev/sda6

---

### Post by che47audio on 2012-03-10
Hi, thanks for your reply. I ran a live disc of ubuntu 10.10. I didnt fully understand what you mean by 
change sda6 to your partition(s)
I ran the command you suggested in the terminal, the results of which are in the screenshot attached.
Thanks

---

### Post by che47audio on 2012-03-26
I have still been unsuccessful in attempting to reduce this boot time. Does anyone have any more/other ideas or am I just stuck with this?
 
Thanks

---

### Post by che47audio on 2012-04-19
I'm bumping this thread as I am still struggling with this ridiculous boot time!!

please ! any suggestions welcome.

thanks

---

### Post by AlThePal on 2012-06-02
I encountered the same problem when installing Linux for a friend.  It appears the delay at these lines:

> [   13.413731] EXT4-fs (sda6): mounted filesystem with ordered data mode. Opts: (null)
[   34.848038] ata3.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6 frozen
[   34.848042] ata3.00: failed command: IDENTIFY PACKET DEVICE
is caused by your CD/DVD drive, the technical reason being that the device doesn't support 16-byte ATA commands.  The workaround suggested is to add libata.atapi_passthru16=0 to the kernel boot parameters in GRUB.

To do this, open a terminal window and edit the */etc/default/grub* file (remember to use sudo).  Find the line that starts *GRUB_CMDLINE_LINUX_DEFAULT* and enter *libata.atapi_passthru16=0* at the end of the string.  For example, if the previous entry was
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet"
```it will now read
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet libata.atapi_passthru16=0"
```
Save the file and then run```
sudo update-grub
```Reboot and hopefully the annoying delay will be gone.

---

### Post by che47audio on 2012-08-25
I bought a new dvd drive and removed the old one and this resolved the issue I was having. 
Thanks for all the help with this.

---

