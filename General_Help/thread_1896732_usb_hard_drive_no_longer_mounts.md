---
title: "usb hard drive no longer mounts"
date: 2011-12-17
forum: General Help
---

### Post by patjennings on 2011-12-17
Hi all, as Stated in the title my western digital usb hdd does not mount anymore. I have been using 10.10 32 bit on a sys 76 lemur for a while now and have never had a problem with it. It would always autodetect with out a hitch. I had not used it in a while and recently needed to back u some files so I plugged it in. The light came on and it seems to spin fine, but it never shows up in nauilus. I figured one of the updates messed something up so i tried running a live cd of ubuntu 11.10, mint 9 , and opensuse. None of them recognised the device. All other usb sticks are recognised though I cannot edit them. I ran dmesg and this is the output

[    1.082059] pci_bus 0000:02: resource 2 [mem 0xc0200000-0xc03fffff 64bit pref]
[    1.082063] pci_bus 0000:03: resource 0 [io  0x4000-0x4fff]
[    1.082066] pci_bus 0000:03: resource 1 [mem 0xf0500000-0xf05fffff]
[    1.082070] pci_bus 0000:03: resource 2 [mem 0xc0400000-0xc05fffff 64bit pref]
[    1.082074] pci_bus 0000:04: resource 0 [io  0x2000-0x2fff]
[    1.082078] pci_bus 0000:04: resource 1 [mem 0xf0400000-0xf04fffff]
[    1.082082] pci_bus 0000:04: resource 2 [mem 0xc0600000-0xc07fffff 64bit pref]
[    1.082086] pci_bus 0000:05: resource 4 [io  0x0000-0x0cf7]
[    1.082090] pci_bus 0000:05: resource 5 [io  0x0d00-0xffff]
[    1.082093] pci_bus 0000:05: resource 6 [mem 0x000a0000-0x000bffff]
[    1.082097] pci_bus 0000:05: resource 7 [mem 0x000d4000-0x000d7fff]
[    1.082101] pci_bus 0000:05: resource 8 [mem 0x000d8000-0x000dbfff]
[    1.082105] pci_bus 0000:05: resource 9 [mem 0xc0000000-0xfeafffff]
[    1.082160] NET: Registered protocol family 2
[    1.082247] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    1.082543] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    1.082953] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    1.083158] TCP: Hash tables configured (established 131072 bind 65536)
[    1.083162] TCP reno registered
[    1.083166] UDP hash table entries: 512 (order: 2, 16384 bytes)
[    1.083179] UDP-Lite hash table entries: 512 (order: 2, 16384 bytes)
[    1.083292] NET: Registered protocol family 1
[    1.083313] pci 0000:00:02.0: Boot video device
[    1.083483] PCI: CLS 64 bytes, default 64
[    1.083517] Simple Boot Flag at 0x36 set to 0x1
[    1.083940] cpufreq-nforce2: No nForce2 chipset.
[    1.083980] Scanning for low memory corruption every 60 seconds
[    1.084130] audit: initializing netlink socket (disabled)
[    1.084143] type=2000 audit(1324154747.908:1): initialized
[    1.105038] highmem bounce pool size: 64 pages
[    1.105047] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    1.107233] VFS: Disk quotas dquot_6.5.2
[    1.107329] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    1.108219] fuse init (API version 7.14)
[    1.108350] msgmni has been set to 1604
[    1.216150] Freeing initrd memory: 16016k freed
[    1.225232] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    1.225238] io scheduler noop registered
[    1.225242] io scheduler deadline registered
[    1.225262] io scheduler cfq registered (default)
[    1.225440] pcieport 0000:00:1c.0: setting latency timer to 64
[    1.225512]   alloc irq_desc for 40 on node -1
[    1.225515]   alloc kstat_irqs on node -1
[    1.225534] pcieport 0000:00:1c.0: irq 40 for MSI/MSI-X
[    1.225677] pcieport 0000:00:1c.2: setting latency timer to 64
[    1.225742]   alloc irq_desc for 41 on node -1
[    1.225745]   alloc kstat_irqs on node -1
[    1.225758] pcieport 0000:00:1c.2: irq 41 for MSI/MSI-X
[    1.225890] pcieport 0000:00:1c.3: setting latency timer to 64
[    1.225956]   alloc irq_desc for 42 on node -1
[    1.225958]   alloc kstat_irqs on node -1
[    1.225971] pcieport 0000:00:1c.3: irq 42 for MSI/MSI-X
[    1.226131] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    1.226368] \_SB_.PCI0:_OSC invalid UUID
[    1.226370] _OSC request data:1 0 1f 
[    1.226559] \_SB_.PCI0:_OSC invalid UUID
[    1.226562] _OSC request data:1 0 1f 
[    1.226744] \_SB_.PCI0:_OSC invalid UUID
[    1.226746] _OSC request data:1 0 1f 
[    1.226951] \_SB_.PCI0:_OSC invalid UUID
[    1.226954] _OSC request data:1 0 1f 
[    1.227134] \_SB_.PCI0:_OSC invalid UUID
[    1.227136] _OSC request data:1 0 1f 
[    1.227316] \_SB_.PCI0:_OSC invalid UUID
[    1.227318] _OSC request data:1 0 1f 
[    1.227354] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    1.227489] intel_idle: MWAIT substates: 0x1120
[    1.227492] intel_idle: v0.4 model 0x25
[    1.227494] intel_idle: lapic_timer_reliable_states 0xffffffff
[    1.228076] ACPI: AC Adapter [ADP0] (on-line)
[    1.228190] input: Lid Switch as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0D:00/input/input0
[    1.228725] ACPI: Lid Switch [LID0]
[    1.228792] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input1
[    1.228799] ACPI: Power Button [PWRB]
[    1.228862] input: Sleep Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0E:00/input/input2
[    1.228868] ACPI: Sleep Button [SLPB]
[    1.228931] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input3
[    1.228937] ACPI: Power Button [PWRF]
[    1.229994] ACPI: acpi_idle yielding to intel_idle
[    1.244582] thermal LNXTHERM:01: registered as thermal_zone0
[    1.244596] ACPI: Thermal Zone [THM0] (55 C)
[    1.244701] ERST: Table is not found!
[    1.244779] isapnp: Scanning for PnP cards...
[    1.245431] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    1.248053] brd: module loaded
[    1.249050] loop: module loaded
[    1.249909] Fixed MDIO Bus: probed
[    1.249964] PPP generic driver version 2.4.2
[    1.250017] tun: Universal TUN/TAP device driver, 1.6
[    1.250020] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    1.250181] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    1.250253] ehci_hcd 0000:00:1a.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.250272] ehci_hcd 0000:00:1a.0: setting latency timer to 64
[    1.250279] ehci_hcd 0000:00:1a.0: EHCI Host Controller
[    1.250344] ehci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 1
[    1.250431] ehci_hcd 0000:00:1a.0: debug port 2
[    1.254423] ehci_hcd 0000:00:1a.0: cache line size of 64 is not supported
[    1.254452] ehci_hcd 0000:00:1a.0: irq 16, io mem 0xf0806000
[    1.263334] ACPI: Battery Slot [BAT0] (battery present)
[    1.269037] ehci_hcd 0000:00:1a.0: USB 2.0 started, EHCI 1.00
[    1.269205] hub 1-0:1.0: USB hub found
[    1.269213] hub 1-0:1.0: 3 ports detected
[    1.269318]   alloc irq_desc for 23 on node -1
[    1.269321]   alloc kstat_irqs on node -1
[    1.269329] ehci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    1.269347] ehci_hcd 0000:00:1d.0: setting latency timer to 64
[    1.269352] ehci_hcd 0000:00:1d.0: EHCI Host Controller
[    1.269402] ehci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    1.269445] ehci_hcd 0000:00:1d.0: debug port 2
[    1.273437] ehci_hcd 0000:00:1d.0: cache line size of 64 is not supported
[    1.273459] ehci_hcd 0000:00:1d.0: irq 23, io mem 0xf0807000
[    1.289026] ehci_hcd 0000:00:1d.0: USB 2.0 started, EHCI 1.00
[    1.289184] hub 2-0:1.0: USB hub found
[    1.289190] hub 2-0:1.0: 3 ports detected
[    1.289281] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    1.289300] uhci_hcd: USB Universal Host Controller Interface driver
[    1.289418] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    1.292961] i8042.c: Detected active multiplexing controller, rev 1.1.
[    1.295656] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.295666] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[    1.295673] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[    1.295680] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[    1.295687] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[    1.295802] mice: PS/2 mouse device common for all mice
[    1.296112] rtc_cmos 00:06: rtc core: registered rtc_cmos as rtc0
[    1.296151] rtc0: alarms up to one month, y3k, 242 bytes nvram, hpet irqs
[    1.296296] device-mapper: uevent: version 1.0.3
[    1.296449] device-mapper: ioctl: 4.17.0-ioctl (2010-03-05) initialised: [email]dm-devel@redhat.com[/email]
[    1.296611] device-mapper: multipath: version 1.1.1 loaded
[    1.296617] device-mapper: multipath round-robin: version 1.0.0 loaded
[    1.296783] EISA: Probing bus 0 at eisa.0
[    1.296787] EISA: Cannot allocate resource for mainboard
[    1.296791] Cannot allocate resource for EISA slot 1
[    1.296793] Cannot allocate resource for EISA slot 2
[    1.296796] Cannot allocate resource for EISA slot 3
[    1.296799] Cannot allocate resource for EISA slot 4
[    1.296802] Cannot allocate resource for EISA slot 5
[    1.296804] Cannot allocate resource for EISA slot 6
[    1.296807] Cannot allocate resource for EISA slot 7
[    1.296810] Cannot allocate resource for EISA slot 8
[    1.296812] EISA: Detected 0 cards.
[    1.297204] cpuidle: using governor ladder
[    1.297481] cpuidle: using governor menu
[    1.297887] TCP cubic registered
[    1.298091] NET: Registered protocol family 10
[    1.298594] lo: Disabled Privacy Extensions
[    1.298905] NET: Registered protocol family 17
[    1.301717] Using IPI No-Shortcut mode
[    1.301833] PM: Resume from disk failed.
[    1.301849] registered taskstats version 1
[    1.302381]   Magic number: 7:672:801
[    1.302476] rtc_cmos 00:06: setting system clock to 2011-12-17 20:45:49 UTC (1324154749)
[    1.302482] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.302484] EDD information not available.
[    1.336394] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input4
[    1.580945] usb 1-1: new high speed USB device using ehci_hcd and address 2
[    1.615333] isapnp: No Plug & Play device found
[    1.615534] Freeing unused kernel memory: 708k freed
[    1.615983] Write protecting the kernel text: 5100k
[    1.616158] Write protecting the kernel read-only data: 2016k
[    1.646712] ramzswap: module is from the staging directory, the quality is unknown, you have been warned.
[    1.648133] ramzswap: num_devices not specified. Using default: 1
[    1.648137] ramzswap: Creating 1 devices ...
[    1.655428] udev[107]: starting version 163
[    1.717684] hub 1-1:1.0: USB hub found
[    1.717739] hub 1-1:1.0: 6 ports detected
[    1.739447] Linux agpgart interface v0.103
[    1.757241] sdhci: Secure Digital Host Controller Interface driver
[    1.757248] sdhci: Copyright(c) Pierre Ossman
[    1.761377] sdhci-pci 0000:04:00.0: SDHCI controller found [197b:2382] (rev 80)
[    1.761420] sdhci-pci 0000:04:00.0: PCI INT B -> GSI 16 (level, low) -> IRQ 16
[    1.761500] sdhci-pci 0000:04:00.0: setting latency timer to 64
[    1.761576] Registered led device: mmc0::
[    1.761645] mmc0: SDHCI controller on PCI [0000:04:00.0] using ADMA
[    1.761667] sdhci-pci 0000:04:00.2: SDHCI controller found [197b:2381] (rev 80)
[    1.761697] sdhci-pci 0000:04:00.2: PCI INT B -> GSI 16 (level, low) -> IRQ 16
[    1.761706] sdhci-pci 0000:04:00.2: Refusing to bind to secondary interface.
[    1.761719] sdhci-pci 0000:04:00.2: PCI INT B disabled
[    1.780646] jme: JMicron JMC2XX ethernet driver version 1.0.6
[    1.780716]   alloc irq_desc for 17 on node -1
[    1.780721]   alloc kstat_irqs on node -1
[    1.780735] jme 0000:04:00.5: PCI INT C -> GSI 17 (level, low) -> IRQ 17
[    1.780760] jme 0000:04:00.5: setting latency timer to 64
[    1.782366] jme 0000:04:00.5: eth0: JMC250 Gigabit Ethernet ver:23 rev:3 macaddr:00:90:f5:b2:9d:97
[    1.805809] agpgart-intel 0000:00:00.0: Intel HD Graphics Chipset
[    1.813438] agpgart-intel 0000:00:00.0: detected 32764K stolen memory
[    1.832752] usb 2-1: new high speed USB device using ehci_hcd and address 2
[    1.912841] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0xd0000000
[    1.912915] ahci 0000:00:1f.2: version 3.0
[    1.912942] ahci 0000:00:1f.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    1.913002]   alloc irq_desc for 43 on node -1
[    1.913006]   alloc kstat_irqs on node -1
[    1.913024] ahci 0000:00:1f.2: irq 43 for MSI/MSI-X
[    1.913080] ahci: SSS flag set, parallel bus scan disabled
[    1.913125] ahci 0000:00:1f.2: AHCI 0001.0300 32 slots 4 ports 3 Gbps 0x1 impl SATA mode
[    1.913134] ahci 0000:00:1f.2: flags: 64bit ncq sntf ilck stag pm led clo pio slum part ems apst 
[    1.913146] ahci 0000:00:1f.2: setting latency timer to 64
[    1.913332] scsi0 : ahci
[    1.913545] scsi1 : ahci
[    1.913657] scsi2 : ahci
[    1.913771] scsi3 : ahci
[    1.913859] ata1: SATA max UDMA/133 abar m2048@0xf0808000 port 0xf0808100 irq 43
[    1.913863] ata2: DUMMY
[    1.913865] ata3: DUMMY
[    1.913867] ata4: DUMMY
[    1.948166] [drm] Initialized drm 1.1.0 20060810
[    1.963288] hub 2-1:1.0: USB hub found
[    1.963352] hub 2-1:1.0: 8 ports detected
[    2.232604] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    2.272629] ata1.00: ATA-8: ST9500420AS, 0002SDM1, max UDMA/133
[    2.272635] ata1.00: 976773168 sectors, multi 16: LBA48 NCQ (depth 31/32)
[    2.274740] ata1.00: configured for UDMA/133
[    2.288809] scsi 0:0:0:0: Direct-Access     ATA      ST9500420AS      0002 PQ: 0 ANSI: 5
[    2.289040] sd 0:0:0:0: [sda] 976773168 512-byte logical blocks: (500 GB/465 GiB)
[    2.289061] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    2.289146] sd 0:0:0:0: [sda] Write Protect is off
[    2.289152] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    2.289228] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.289482]  sda: sda1 sda2 < sda5 sda6 sda7 >
[    2.338403] sd 0:0:0:0: [sda] Attached SCSI disk
[    2.380734] i915 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    2.380742] i915 0000:00:02.0: setting latency timer to 64
[    2.440765]   alloc irq_desc for 44 on node -1
[    2.440772]   alloc kstat_irqs on node -1
[    2.440789] i915 0000:00:02.0: irq 44 for MSI/MSI-X
[    2.440806] [drm] set up 31M of stolen space
[    2.555599] vgaarb: device changed decodes: PCI:0000:00:02.0,olddecodes=io+mem,decodes=io+mem:owns=io+mem
[    2.866158] Skipping EDID probe due to cached edid
[    3.280643] Console: switching to colour frame buffer device 170x48
[    3.287485] fb0: inteldrmfb frame buffer device
[    3.287488] drm: registered panic notifier
[    3.287494] Slow work thread pool: Starting up
[    3.287795] Slow work thread pool: Ready
[    3.295121] acpi device:04: registered as cooling_device4
[    3.295618] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/LNXVIDEO:00/input/input5
[    3.295693] ACPI: Video Device [GFX0] (multi-head: yes  rom: no  post: no)
[    3.295738] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
[    3.566685] Skipping EDID probe due to cached edid
[    3.724446] xor: automatically using best checksumming function: pIII_sse
[    3.743665]    pIII_sse  :  4494.000 MB/sec
[    3.743670] xor: using function: pIII_sse (4494.000 MB/sec)
[    3.748277] device-mapper: dm-raid45: initialized v0.2594b
[    3.991759] EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: (null)
[   12.748569] udev[481]: starting version 163
[   12.790302] lp: driver loaded but no devices found
[   13.004209] Adding 12285948k swap on /dev/sda5.  Priority:-1 extents:1 across:12285948k 
[   13.008003] intel ips 0000:00:1f.6: Warning: CPU TDP doesn't match expected value (found 11, expected 18)
[   13.008044] intel ips 0000:00:1f.6: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[   13.043705] cfg80211: Calling CRDA to update world regulatory domain
[   13.075357] jmb38x_ms 0000:04:00.3: PCI INT C -> GSI 17 (level, low) -> IRQ 17
[   13.075372] jmb38x_ms 0000:04:00.3: setting latency timer to 64
[   13.082915] intel ips 0000:00:1f.6: IPS driver initialized, MCP temp limit 90
[   13.103019] cfg80211: World regulatory domain updated:
[   13.103027]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   13.103035]     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   13.103043]     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   13.103050]     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   13.103057]     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   13.103064]     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   13.229420] iwlagn: Intel(R) Wireless WiFi Link AGN driver for Linux, in-tree:
[   13.229429] iwlagn: Copyright(c) 2003-2010 Intel Corporation
[   13.229586] iwlagn 0000:03:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[   13.229631] iwlagn 0000:03:00.0: setting latency timer to 64
[   13.229747] iwlagn 0000:03:00.0: Detected Intel(R) Centrino(R) Advanced-N 6200 AGN, REV=0x74
[   13.237177] type=1400 audit(1324154761.438:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient3" pid=780 comm="apparmor_parser"
[   13.237613] type=1400 audit(1324154761.438:3): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient3" pid=776 comm="apparmor_parser"
[   13.238314] type=1400 audit(1324154761.438:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=780 comm="apparmor_parser"
[   13.238738] type=1400 audit(1324154761.438:5): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=776 comm="apparmor_parser"
[   13.238954] type=1400 audit(1324154761.438:6): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=780 comm="apparmor_parser"
[   13.239366] type=1400 audit(1324154761.438:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=776 comm="apparmor_parser"
[   13.247692] iwlagn 0000:03:00.0: Tunable channels: 13 802.11bg, 24 802.11a channels
[   13.247935]   alloc irq_desc for 45 on node -1
[   13.247941]   alloc kstat_irqs on node -1
[   13.248024] iwlagn 0000:03:00.0: irq 45 for MSI/MSI-X
[   13.274121] iwlagn 0000:03:00.0: loaded firmware version 9.221.4.1 build 25532
[   13.292050] phy0: Selected rate control algorithm 'iwl-agn-rs'
[   13.316180] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
[   13.328661]   alloc irq_desc for 22 on node -1
[   13.328667]   alloc kstat_irqs on node -1
[   13.328683] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[   13.328777]   alloc irq_desc for 46 on node -1
[   13.328781]   alloc kstat_irqs on node -1
[   13.328801] HDA Intel 0000:00:1b.0: irq 46 for MSI/MSI-X
[   13.328856] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   13.845351] Synaptics Touchpad, model: 1, fw: 7.2, id: 0x1c0b1, caps: 0xd04731/0xa42000/0xa0000
[   13.881376] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio4/input/input6
[   14.019242] type=1400 audit(1324154762.222:8): apparmor="STATUS" operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" pid=1000 comm="apparmor_parser"
[   14.028106] type=1400 audit(1324154762.230:9): apparmor="STATUS" operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" pid=1007 comm="apparmor_parser"
[   14.029510] type=1400 audit(1324154762.230:10): apparmor="STATUS" operation="profile_load" name="/usr/sbin/cupsd" pid=1007 comm="apparmor_parser"
[   14.032527] type=1400 audit(1324154762.234:11): apparmor="STATUS" operation="profile_load" name="/usr/bin/freshclam" pid=1005 comm="apparmor_parser"
[   14.283994] Skipping EDID probe due to cached edid
[   14.312488] Skipping EDID probe due to cached edid
[   14.393876] hda_codec: ALC272: BIOS auto-probing.
[   14.412836] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   14.428082]   alloc irq_desc for 47 on node -1
[   14.428090]   alloc kstat_irqs on node -1
[   14.428119] jme 0000:04:00.5: irq 47 for MSI/MSI-X
[   14.428504] jme 0000:04:00.5: eth0: Link is down.
[   14.428957] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   14.530128] ppdev: user-space parallel port driver
[   16.882678] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,commit=0
[   16.998255] Skipping EDID probe due to cached edid
[   17.028407] Skipping EDID probe due to cached edid
[   17.123695] Skipping EDID probe due to cached edid
[   17.153332] Skipping EDID probe due to cached edid
[   18.221278] intel ips 0000:00:1f.6: CPU power or thermal limit exceeded
[   18.941691] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,commit=0
[   23.217013] intel ips 0000:00:1f.6: CPU power or thermal limit exceeded
[   28.214280] intel ips 0000:00:1f.6: CPU power or thermal limit exceeded
[   33.211457] intel ips 0000:00:1f.6: CPU power or thermal limit exceeded
[   34.209431] padlock: VIA PadLock not detected.
[   35.719668] Skipping EDID probe due to cached edid
[   35.778757] Skipping EDID probe due to cached edid
[   35.808676] Skipping EDID probe due to cached edid
[   35.838404] Skipping EDID probe due to cached edid
[   37.126511] Skipping EDID probe due to cached edid
[   37.987002] wlan0: authenticate with 00:23:97:f9:c1:17 (try 1)
[   37.991866] wlan0: authenticated
[   37.995436] wlan0: associate with 00:23:97:f9:c1:17 (try 1)
[   38.192693] wlan0: associate with 00:23:97:f9:c1:17 (try 2)
[   38.196037] wlan0: RX AssocResp from 00:23:97:f9:c1:17 (capab=0x411 status=0 aid=1)
[   38.196046] wlan0: associated
[   38.199835] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   38.208688] intel ips 0000:00:1f.6: CPU power or thermal limit exceeded
[   39.765654] Skipping EDID probe due to cached edid
[   42.315039] Skipping EDID probe due to cached edid
[   43.206006] intel ips 0000:00:1f.6: CPU power or thermal limit exceeded
[   48.203243] intel ips 0000:00:1f.6: CPU power or thermal limit exceeded
[   48.379062] wlan0: no IPv6 routers present
[   53.200435] intel ips 0000:00:1f.6: CPU power or thermal limit exceeded
[   58.197676] intel ips 0000:00:1f.6: CPU power or thermal limit exceeded
[   63.194932] intel ips 0000:00:1f.6: CPU power or thermal limit exceeded
[   68.192217] intel ips 0000:00:1f.6: CPU power or thermal limit exceeded
[   73.189371] intel ips 0000:00:1f.6: CPU power or thermal limit exceeded
[   78.186612] intel ips 0000:00:1f.6: CPU power or thermal limit exceeded
[   83.183912] intel ips 0000:00:1f.6: CPU power or thermal limit exceeded
[   88.181130] intel ips 0000:00:1f.6: CPU power or thermal limit exceeded
[   93.178398] intel ips 0000:00:1f.6: CPU power or thermal limit exceeded
[   98.175647] intel ips 0000:00:1f.6: CPU power or thermal limit exceeded
[  103.172883] intel ips 0000:00:1f.6: CPU power or thermal limit exceeded
[  108.170182] intel ips 0000:00:1f.6: CPU power or thermal limit exceeded
[  113.167388] intel ips 0000:00:1f.6: CPU power or thermal limit exceeded
[  118.164605] intel ips 0000:00:1f.6: CPU power or thermal limit exceeded
[  123.161853] intel ips 0000:00:1f.6: CPU power or thermal limit exceeded
[  128.159146] intel ips 0000:00:1f.6: CPU power or thermal limit exceeded
[  133.156332] intel ips 0000:00:1f.6: CPU power or thermal limit exceeded
[  138.153586] intel ips 0000:00:1f.6: CPU power or thermal limit exceeded
[  143.150820] intel ips 0000:00:1f.6: CPU power or thermal limit exceeded
[  148.148055] intel ips 0000:00:1f.6: CPU power or thermal limit exceeded
[  153.145284] intel ips 0000:00:1f.6: CPU power or thermal limit exceeded
[  158.142550] intel ips 0000:00:1f.6: CPU power or thermal limit exceeded
[  163.139764] intel ips 0000:00:1f.6: CPU power or thermal limit exceeded
[  168.137054] intel ips 0000:00:1f.6: CPU power or thermal limit exceeded
[  173.134311] intel ips 0000:00:1f.6: CPU power or thermal limit exceeded
[  178.131516] intel ips 0000:00:1f.6: CPU power or thermal limit exceeded
[  183.128751] intel ips 0000:00:1f.6: CPU power or thermal limit exceeded
[  188.126005] intel ips 0000:00:1f.6: CPU power or thermal limit exceeded
[  193.123209] intel ips 0000:00:1f.6: CPU power or thermal limit exceeded
[  198.120454] intel ips 0000:00:1f.6: CPU power or thermal limit exceeded
[  203.117734] intel ips 0000:00:1f.6: CPU power or thermal limit exceeded
[  208.114982] intel ips 0000:00:1f.6: CPU power or thermal limit exceeded
[  213.112149] intel ips 0000:00:1f.6: CPU power or thermal limit exceeded
[  218.109465] intel ips 0000:00:1f.6: CPU power or thermal limit exceeded
[  223.106685] intel ips 0000:00:1f.6: CPU power or thermal limit exceeded
[  228.103949] intel ips 0000:00:1f.6: CPU power or thermal limit exceeded
[  233.101177] intel ips 0000:00:1f.6: CPU power or thermal limit exceeded
[  238.098453] intel ips 0000:00:1f.6: CPU power or thermal limit exceeded
[  243.095658] intel ips 0000:00:1f.6: CPU power or thermal limit exceeded
[  248.092908] intel ips 0000:00:1f.6: CPU power or thermal limit exceeded
[  253.090144] intel ips 0000:00:1f.6: CPU power or thermal limit exceeded
[  258.087390] intel ips 0000:00:1f.6: CPU power or thermal limit exceeded
[  263.088569] intel ips 0000:00:1f.6: CPU power or thermal limit exceeded
[  268.086076] intel ips 0000:00:1f.6: CPU power or thermal limit exceeded
[  273.083116] intel ips 0000:00:1f.6: CPU power or thermal limit exceeded
[  278.080357] intel ips 0000:00:1f.6: CPU power or thermal limit exceeded
[  283.077630] intel ips 0000:00:1f.6: CPU power or thermal limit exceeded
[  288.074844] intel ips 0000:00:1f.6: CPU power or thermal limit exceeded
[  293.073129] intel ips 0000:00:1f.6: CPU power or thermal limit exceeded
[  298.069266] intel ips 0000:00:1f.6: CPU power or thermal limit exceeded
[  303.066574] intel ips 0000:00:1f.6: CPU power or thermal limit exceeded
[  308.063837] intel ips 0000:00:1f.6: CPU power or thermal limit exceeded
[  313.061063] intel ips 0000:00:1f.6: CPU power or thermal limit exceeded
[  318.058300] intel ips 0000:00:1f.6: CPU power or thermal limit exceeded
[  323.055544] intel ips 0000:00:1f.6: CPU power or thermal limit exceeded
[  328.052740] intel ips 0000:00:1f.6: CPU power or thermal limit exceeded
[  333.050030] intel ips 0000:00:1f.6: CPU power or thermal limit exceeded
[  338.047255] intel ips 0000:00:1f.6: CPU power or thermal limit exceeded
[  343.045447] intel ips 0000:00:1f.6: CPU power or thermal limit exceeded
[  348.042741] intel ips 0000:00:1f.6: CPU power or thermal limit exceeded
[  353.039047] intel ips 0000:00:1f.6: CPU power or thermal limit exceeded
[  358.036237] intel ips 0000:00:1f.6: CPU power or thermal limit exceeded
[  363.033484] intel ips 0000:00:1f.6: CPU power or thermal limit exceeded
[  368.031675] intel ips 0000:00:1f.6: CPU power or thermal limit exceeded
[  373.027963] intel ips 0000:00:1f.6: CPU power or thermal limit exceeded
[  378.025226] intel ips 0000:00:1f.6: CPU power or thermal limit exceeded
[  383.022683] intel ips 0000:00:1f.6: CPU power or thermal limit exceeded
[  388.019720] intel ips 0000:00:1f.6: CPU power or thermal limit exceeded
[  393.016985] intel ips 0000:00:1f.6: CPU power or thermal limit exceeded
[  398.014231] intel ips 0000:00:1f.6: CPU power or thermal limit exceeded
[  403.012352] intel ips 0000:00:1f.6: CPU power or thermal limit exceeded
[  408.009637] intel ips 0000:00:1f.6: CPU power or thermal limit exceeded
[  413.005898] intel ips 0000:00:1f.6: CPU power or thermal limit exceeded
[  418.003143] intel ips 0000:00:1f.6: CPU power or thermal limit exceeded
[  423.000374] intel ips 0000:00:1f.6: CPU power or thermal limit exceeded
[  427.998570] intel ips 0000:00:1f.6: CPU power or thermal limit exceeded
[  432.994850] intel ips 0000:00:1f.6: CPU power or thermal limit exceeded
[  437.993115] intel ips 0000:00:1f.6: CPU power or thermal limit exceeded
[  442.990305] intel ips 0000:00:1f.6: CPU power or thermal limit exceeded
[  447.986624] intel ips 0000:00:1f.6: CPU power or thermal limit exceeded
[  452.983833] intel ips 0000:00:1f.6: CPU power or thermal limit exceeded
[  457.982106] intel ips 0000:00:1f.6: CPU power or thermal limit exceeded
[  462.978336] intel ips 0000:00:1f.6: CPU power or thermal limit exceeded
[  467.975777] intel ips 0000:00:1f.6: CPU power or thermal limit exceeded
[  472.972808] intel ips 0000:00:1f.6: CPU power or thermal limit exceeded
[  477.970981] intel ips 0000:00:1f.6: CPU power or thermal limit exceeded
[  482.968268] intel ips 0000:00:1f.6: CPU power or thermal limit exceeded
[  487.964540] intel ips 0000:00:1f.6: CPU power or thermal limit exceeded
[  492.961761] intel ips 0000:00:1f.6: CPU power or thermal limit exceeded
[  497.959019] intel ips 0000:00:1f.6: CPU power or thermal limit exceeded
[  502.956268] intel ips 0000:00:1f.6: CPU power or thermal limit exceeded
[  507.953512] intel ips 0000:00:1f.6: CPU power or thermal limit exceeded
[  512.950728] intel ips 0000:00:1f.6: CPU power or thermal limit exceeded
[  517.948975] intel ips 0000:00:1f.6: CPU power or thermal limit exceeded
[  522.945212] intel ips 0000:00:1f.6: CPU power or thermal limit exceeded
[  527.942479] intel ips 0000:00:1f.6: CPU power or thermal limit exceeded
[  532.939714] intel ips 0000:00:1f.6: CPU power or thermal limit exceeded
[  537.937008] intel ips 0000:00:1f.6: CPU power or thermal limit exceeded
[  542.934197] intel ips 0000:00:1f.6: CPU power or thermal limit exceeded
[  547.931441] intel ips 0000:00:1f.6: CPU power or thermal limit exceeded
[  552.928738] intel ips 0000:00:1f.6: CPU power or thermal limit exceeded
[  557.925931] intel ips 0000:00:1f.6: CPU power or thermal limit exceeded
[  562.924168] intel ips 0000:00:1f.6: CPU power or thermal limit exceeded
[  567.920407] intel ips 0000:00:1f.6: CPU power or thermal limit exceeded
[  572.918650] intel ips 0000:00:1f.6: CPU power or thermal limit exceeded
[  577.915887] intel ips 0000:00:1f.6: CPU power or thermal limit exceeded
[  582.913144] intel ips 0000:00:1f.6: CPU power or thermal limit exceeded
[  587.910370] intel ips 0000:00:1f.6: CPU power or thermal limit exceeded
[  592.907569] intel ips 0000:00:1f.6: CPU power or thermal limit exceeded
[  597.904014] intel ips 0000:00:1f.6: CPU power or thermal limit exceeded
[  602.901129] intel ips 0000:00:1f.6: CPU power or thermal limit exceeded
[  607.899355] intel ips 0000:00:1f.6: CPU power or thermal limit exceeded
[  612.896623] intel ips 0000:00:1f.6: CPU power or thermal limit exceeded
[  617.893885] intel ips 0000:00:1f.6: CPU power or thermal limit exceeded
[  618.220858] usb 2-1.4: new high speed USB device using ehci_hcd and address 3
[  618.237367] hub 2-1:1.0: unable to enumerate USB device on port 4
[  618.620863] hub 2-1:1.0: unable to enumerate USB device on port 4
[  618.877988] hub 2-1:1.0: unable to enumerate USB device on port 4
[  619.188339] usb 2-1.4: new full speed USB device using ehci_hcd and address 6
[  619.260269] usb 2-1.4: device descriptor read/64, error -32
[  619.436167] usb 2-1.4: device descriptor read/64, error -32
[  619.612096] usb 2-1.4: new full speed USB device using ehci_hcd and address 7
[  619.688084] usb 2-1.4: device descriptor read/64, error -32


Device does not show up in disk utility, and I could not get mount manager to work.

Does anyone know what is wrong here? All my music is on the hdd i need to find a way to get it off.

---

### Post by patjennings on 2011-12-18
i finally got it to mount, by accident when i wiggle the usb wire, then it kept unmounting on me. So this one is obviously a defective wire.

---

