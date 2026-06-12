---
title: "Help with connecting to Samsung Galaxy S2"
date: 2012-04-15
forum: General Help
---

### Post by Arguable on 2012-04-15
Hello everyone.

I'm sorry for creating another thread on this topic, but none of the threads that came up from a search seemed to help.  I am trying to connect my Samsung Galaxy S2 android phone to my Ubuntu laptop as a mass storage device to transfer music to the phone.  However, there is no response from neither the phone or laptop when connected.  I know it is not the usb port because both ports on the laptop do not work, but both start charging the phone when connected.

From what I've seen, there are two common fixes for this issue.  The first is to go to settings-->Wireless and Network-->USB utilities on the phone and press "Connect storage to PC."  At this point I connect the cord, but nothing happens.  I have been told I am supposed to see a green Android robot turn orange at this point, but there is no response from the phone.

The second fix is to enable USB debugging in settings-->Applications-->Development and then plug the cord in.  Once again, no response at all.

I have also tried the workaround in using bluetooth to transfer files, but after turning both bluetooth devices on neither can detect the other.

Finally, I have tried looking for a device in Nautilus but none is present making me think it is not auto-mounted, but I have tried to manually mount the device in Terminal but that is a bit beyond my technical prowess.  If anyone could tell me what I am doing wrong, any help at all would be greatly appreciated.  Thank you in advance.

---

### Post by Arguable on 2012-04-18
Shameless bump :(

---

### Post by squilookle on 2012-04-18
I'm afraid I don't have a direct solution to your problem, however, I transfer files between my Android phone and my Xubuntu box using [DropBox]("https://www.dropbox.com/"). I'm sure [Ubuntu One]("https://one.ubuntu.com/") would work too. 

The downsides to this, other than it not being a direct solution to your problem, are that the size of the files you can transfer are limited by the storage you have on these services, and of course, would would need to have a fast connection with no data caps for both the computer and the phone. 

*I use these services out of laziness, not because I'm experiencing the same issue. If I can, I'll plug my phone in tonight and see what it does. 

Hope this helps while you find a better solution.

---

### Post by cortman on 2012-04-18
Plug the cord in FIRST.

---

### Post by Arguable on 2012-04-18
> **cortman said:**
> Plug the cord in FIRST.

I have tried this to no avail.

---

### Post by cortman on 2012-04-18
> **Arguable said:**
> I have tried this to no avail.

That's very strange. With "USB Debugging" enabled, when I plug my Galaxy S2 into my laptop and select USB storage from the dropdown menu, it works every time.
Not sure that I have any other suggestions. Sorry it didn't work!

---

### Post by Arguable on 2012-04-19
> **cortman said:**
> That's very strange. With "USB Debugging" enabled, when I plug my Galaxy S2 into my laptop and select USB storage from the dropdown menu, it works every time.
Not sure that I have any other suggestions. Sorry it didn't work!
Thanks for trying.  When my laptop ran Windows 7 it would work as you described with USB debugging, but ever since I switched to Ubuntu it has been unable to connect.  It's the strangest thing.

---

### Post by cortman on 2012-04-19
Well, you could try running

```
lsusb
```

before and after plugging the phone in. If there's any difference, you may be able to mount it manually.
To make it easier, disconnect as many other USB devices as you can.

---

### Post by iponeverything on 2012-04-19
Get some debugging output --

run this:

```
sudo tail -vf /var/log/messages /var/log/debug
```

Then pulg in the phone. Post the output from the above command.

---

### Post by for.i.am.root on 2012-04-19
I would use:
Applications - Accessories - Terminal

Unplug phone.
sudo dmesg -c
Plug in phone.
dmesg

Post the output here.

Try using a different USB cable and disabling Developer Mode. Developer / debugging mode *usually* puts the phone in modem mode. I think with CDMA Samsung's you can use ##8778# and set both options to PDA which will force the phone into mass storage.

Also with Samsung's *I believe* mass storage only works with a microsd, not internal storage. Is your microsd mounted and recognized by the phone? Try unmounting it on the phone first. Should be in storage under settings.

dmesg will probably show a modem being connected.

The above command will work better for logging rather than the one I put in. Takes forever to type decently on this tablet.

---

### Post by cortman on 2012-04-19
> **for.i.am.root said:**
> 
Also with Samsung's *I believe* mass storage only works with a microsd, not internal storage. Is your microsd mounted and recognized by the phone? Try unmounting it on the phone first. Should be in storage under settings.

+1 for dmesg.
Samsung mass storage works for both. Mine automatically mounts both the internal SD and the external SD. Though why they would call the internal flash storage an "sdcard" is beyond me.

---

### Post by for.i.am.root on 2012-04-19
Haven't owned a Samsung in a LONG time. Switched to Sony Ericsson and then HTC. Thanks for the correction.

---

### Post by Arguable on 2012-04-20
> **cortman said:**
> Well, you could try running

```
lsusb
```

before and after plugging the phone in. If there's any difference, you may be able to mount it manually.
To make it easier, disconnect as many other USB devices as you can.
There was no difference in the terminal output.

> Get some debugging output --

run this:

Code:
sudo tail -vf /var/log/messages /var/log/debug
Then pulg in the phone. Post the output from the above command.

```
sudo tail -vf /var/log/messages /var/log/debug
tail: cannot open `/var/log/messages' for reading: No such file or directory
tail: cannot open `/var/log/debug' for reading: No such file or directory
```

This was all I got.  Not sure what it was supposed to do, but maybe I typed the command wrong?

---

### Post by Arguable on 2012-04-20
> **for.i.am.root said:**
> I would use:
Applications - Accessories - Terminal

Unplug phone.
sudo dmesg -c
Plug in phone.
dmesg

Post the output here.
I'm not sure this is what you wanted, but this is the output without the cord connected:

```
[    1.679470] system 00:0a: [mem 0xfee00000-0xfeefffff] has been reserved
[    1.679472] system 00:0a: Plug and Play ACPI device, IDs PNP0c02 (active)
[    1.683241] pnp 00:0b: [irq 23]
[    1.683266] pnp 00:0b: Plug and Play ACPI device, IDs SMO8800 (active)
[    1.703446] pnp 00:0c: can't evaluate _CRS: 12311
[    1.703489] system 00:0c: Plug and Play ACPI device, IDs PNP0c01 (active)
[    1.703496] pnp: PnP ACPI: found 13 devices
[    1.703498] ACPI: ACPI bus type pnp unregistered
[    1.708859] PCI: max bus depth: 1 pci_try_num: 2
[    1.708916] pci 0000:00:01.0: PCI bridge to [bus 01-01]
[    1.708918] pci 0000:00:01.0:   bridge window [io  0x4000-0x4fff]
[    1.708921] pci 0000:00:01.0:   bridge window [mem 0xe4000000-0xe50fffff]
[    1.708923] pci 0000:00:01.0:   bridge window [mem 0xd0000000-0xe1ffffff 64bit pref]
[    1.708927] pci 0000:00:1c.0: PCI bridge to [bus 02-02]
[    1.708928] pci 0000:00:1c.0:   bridge window [io  disabled]
[    1.708935] pci 0000:00:1c.0:   bridge window [mem disabled]
[    1.708939] pci 0000:00:1c.0:   bridge window [mem pref disabled]
[    1.708948] pci 0000:00:1c.1: PCI bridge to [bus 03-03]
[    1.708949] pci 0000:00:1c.1:   bridge window [io  disabled]
[    1.708956] pci 0000:00:1c.1:   bridge window [mem 0xe6600000-0xe66fffff]
[    1.708961] pci 0000:00:1c.1:   bridge window [mem pref disabled]
[    1.708969] pci 0000:00:1c.2: PCI bridge to [bus 04-09]
[    1.708972] pci 0000:00:1c.2:   bridge window [io  0x3000-0x3fff]
[    1.708979] pci 0000:00:1c.2:   bridge window [mem 0xe5b00000-0xe64fffff]
[    1.708984] pci 0000:00:1c.2:   bridge window [mem 0xe2b00000-0xe34fffff 64bit pref]
[    1.708992] pci 0000:00:1c.3: PCI bridge to [bus 0a-0a]
[    1.708995] pci 0000:00:1c.3:   bridge window [io  0x2000-0x2fff]
[    1.709002] pci 0000:00:1c.3:   bridge window [mem 0xe5100000-0xe5afffff]
[    1.709007] pci 0000:00:1c.3:   bridge window [mem 0xe2100000-0xe2afffff 64bit pref]
[    1.709016] pci 0000:00:1c.5: PCI bridge to [bus 0b-0b]
[    1.709017] pci 0000:00:1c.5:   bridge window [io  disabled]
[    1.709022] pci 0000:00:1c.5:   bridge window [mem 0xe6500000-0xe65fffff]
[    1.709026] pci 0000:00:1c.5:   bridge window [mem pref disabled]
[    1.709043] pci 0000:00:01.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.709046] pci 0000:00:01.0: setting latency timer to 64
[    1.709052] pci 0000:00:1c.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.709057] pci 0000:00:1c.0: setting latency timer to 64
[    1.709068] pci 0000:00:1c.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    1.709074] pci 0000:00:1c.1: setting latency timer to 64
[    1.709084] pci 0000:00:1c.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    1.709090] pci 0000:00:1c.2: setting latency timer to 64
[    1.709100] pci 0000:00:1c.3: PCI INT D -> GSI 19 (level, low) -> IRQ 19
[    1.709106] pci 0000:00:1c.3: setting latency timer to 64
[    1.709112] pci 0000:00:1c.5: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    1.709116] pci 0000:00:1c.5: setting latency timer to 64
[    1.709120] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
[    1.709122] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff]
[    1.709123] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
[    1.709125] pci_bus 0000:00: resource 7 [mem 0xd0000000-0xfeafffff]
[    1.709126] pci_bus 0000:00: resource 8 [mem 0xfed40000-0xfed44fff]
[    1.709128] pci_bus 0000:01: resource 0 [io  0x4000-0x4fff]
[    1.709129] pci_bus 0000:01: resource 1 [mem 0xe4000000-0xe50fffff]
[    1.709131] pci_bus 0000:01: resource 2 [mem 0xd0000000-0xe1ffffff 64bit pref]
[    1.709133] pci_bus 0000:03: resource 1 [mem 0xe6600000-0xe66fffff]
[    1.709135] pci_bus 0000:04: resource 0 [io  0x3000-0x3fff]
[    1.709136] pci_bus 0000:04: resource 1 [mem 0xe5b00000-0xe64fffff]
[    1.709138] pci_bus 0000:04: resource 2 [mem 0xe2b00000-0xe34fffff 64bit pref]
[    1.709139] pci_bus 0000:0a: resource 0 [io  0x2000-0x2fff]
[    1.709141] pci_bus 0000:0a: resource 1 [mem 0xe5100000-0xe5afffff]
[    1.709142] pci_bus 0000:0a: resource 2 [mem 0xe2100000-0xe2afffff 64bit pref]
[    1.709144] pci_bus 0000:0b: resource 1 [mem 0xe6500000-0xe65fffff]
[    1.709167] NET: Registered protocol family 2
[    1.709293] IP route cache hash table entries: 131072 (order: 8, 1048576 bytes)
[    1.710085] TCP established hash table entries: 524288 (order: 11, 8388608 bytes)
[    1.711229] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[    1.711356] TCP: Hash tables configured (established 524288 bind 65536)
[    1.711358] TCP reno registered
[    1.711369] UDP hash table entries: 2048 (order: 4, 65536 bytes)
[    1.711385] UDP-Lite hash table entries: 2048 (order: 4, 65536 bytes)
[    1.711475] NET: Registered protocol family 1
[    1.711583] pci 0000:01:00.0: Boot video device
[    1.711637] PCI: CLS 64 bytes, default 64
[    1.711641] PCI-DMA: Using software bounce buffering for IO (SWIOTLB)
[    1.711643] Placing 64MB software IO TLB between ffff8800cb271000 - ffff8800cf271000
[    1.711644] software IO TLB at phys 0xcb271000 - 0xcf271000
[    1.711657] Simple Boot Flag at 0xf3 set to 0x1
[    1.711987] audit: initializing netlink socket (disabled)
[    1.711994] type=2000 audit(1334934872.552:1): initialized
[    1.733500] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    1.741945] VFS: Disk quotas dquot_6.5.2
[    1.741987] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    1.742391] fuse init (API version 7.16)
[    1.742447] msgmni has been set to 7827
[    1.742725] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    1.742752] io scheduler noop registered
[    1.742753] io scheduler deadline registered
[    1.742778] io scheduler cfq registered (default)
[    1.742848] pcieport 0000:00:01.0: setting latency timer to 64
[    1.742873] pcieport 0000:00:01.0: irq 41 for MSI/MSI-X
[    1.743228] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    1.743244] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    1.743271] intel_idle: MWAIT substates: 0x21120
[    1.743272] intel_idle: v0.4 model 0x2A
[    1.743273] intel_idle: lapic_timer_reliable_states 0xffffffff
[    1.743696] ACPI: Deprecated procfs I/F for AC is loaded, please retry with CONFIG_ACPI_PROCFS_POWER cleared
[    1.743940] ACPI: AC Adapter [AC] (on-line)
[    1.744052] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input0
[    1.744729] ACPI: Lid Switch [LID]
[    1.744755] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1
[    1.744758] ACPI: Power Button [PBTN]
[    1.744781] input: Sleep Button as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input2
[    1.744783] ACPI: Sleep Button [SBTN]
[    1.744808] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input3
[    1.744811] ACPI: Power Button [PWRF]
[    1.744830] ACPI: acpi_idle yielding to intel_idle
[    1.927274] thermal LNXTHERM:00: registered as thermal_zone0
[    1.927276] ACPI: Thermal Zone [THM] (25 C)
[    1.927293] ACPI: Deprecated procfs I/F for battery is loaded, please retry with CONFIG_ACPI_PROCFS_POWER cleared
[    1.927302] ACPI: Deprecated procfs I/F for battery is loaded, please retry with CONFIG_ACPI_PROCFS_POWER cleared
[    1.927324] ACPI: Deprecated procfs I/F for battery is loaded, please retry with CONFIG_ACPI_PROCFS_POWER cleared
[    1.927337] ERST: Table is not found!
[    1.927380] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    2.251047] ACPI Error: [EABF] Namespace lookup failure, AE_ALREADY_EXISTS (20110413/dswload2-316)
[    2.251052] ACPI Exception: AE_ALREADY_EXISTS, During name lookup/catalog (20110413/psloop-231)
[    2.251055] ACPI Error: Method parse/execution failed [\_SB_.EEAC] (Node ffff880126e43f00), AE_ALREADY_EXISTS (20110413/psparse-536)
[    2.251061] ACPI: Marking method EEAC as Serialized because of AE_ALREADY_EXISTS error
[    2.251064] ACPI Error: Method parse/execution failed [\_SB_.BAT2._STA] (Node ffff880126e44500), AE_ALREADY_EXISTS (20110413/psparse-536)
[    2.251069] ACPI: Marking method _STA as Serialized because of AE_ALREADY_EXISTS error
[    2.251073] ACPI Exception: AE_ERROR, Evaluating _STA (20110413/battery-396)
[    2.251076] ACPI: Battery Slot [BAT2] (battery absent)
[    2.251539] ACPI: Battery Slot [BAT1] (battery absent)
[    2.259160] ACPI: Battery Slot [BAT0] (battery present)
[    2.307077] serial 0000:00:16.3: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    2.327283] 0000:00:16.3: ttyS4 at I/O 0x50a0 (irq = 17) is a 16550A
[    2.327457] Linux agpgart interface v0.103
[    2.328185] brd: module loaded
[    2.328494] loop: module loaded
[    2.328733] Fixed MDIO Bus: probed
[    2.328746] PPP generic driver version 2.4.2
[    2.328771] tun: Universal TUN/TAP device driver, 1.6
[    2.328772] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    2.328817] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    2.328828] ehci_hcd 0000:00:1a.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    2.328846] ehci_hcd 0000:00:1a.0: setting latency timer to 64
[    2.328850] ehci_hcd 0000:00:1a.0: EHCI Host Controller
[    2.328872] ehci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 1
[    2.328896] ehci_hcd 0000:00:1a.0: debug port 2
[    2.332791] ehci_hcd 0000:00:1a.0: cache line size of 64 is not supported
[    2.332803] ehci_hcd 0000:00:1a.0: irq 16, io mem 0xe6770000
[    2.346915] ehci_hcd 0000:00:1a.0: USB 2.0 started, EHCI 1.00
[    2.347033] hub 1-0:1.0: USB hub found
[    2.347036] hub 1-0:1.0: 3 ports detected
[    2.347080] ehci_hcd 0000:00:1d.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    2.347091] ehci_hcd 0000:00:1d.0: setting latency timer to 64
[    2.347094] ehci_hcd 0000:00:1d.0: EHCI Host Controller
[    2.347117] ehci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    2.347136] ehci_hcd 0000:00:1d.0: debug port 2
[    2.351033] ehci_hcd 0000:00:1d.0: cache line size of 64 is not supported
[    2.351043] ehci_hcd 0000:00:1d.0: irq 17, io mem 0xe6750000
[    2.366909] ehci_hcd 0000:00:1d.0: USB 2.0 started, EHCI 1.00
[    2.367017] hub 2-0:1.0: USB hub found
[    2.367019] hub 2-0:1.0: 3 ports detected
[    2.367058] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    2.367066] uhci_hcd: USB Universal Host Controller Interface driver
[    2.367103] i8042: PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    2.367297] i8042: Warning: Keylock active
[    2.368730] serio: i8042 KBD port at 0x60,0x64 irq 1
[    2.368734] serio: i8042 AUX port at 0x60,0x64 irq 12
[    2.368814] mousedev: PS/2 mouse device common for all mice
[    2.368908] rtc_cmos 00:06: RTC can wake from S4
[    2.369004] rtc_cmos 00:06: rtc core: registered rtc_cmos as rtc0
[    2.369029] rtc0: alarms up to one year, y3k, 242 bytes nvram, hpet irqs
[    2.369103] device-mapper: uevent: version 1.0.3
[    2.369160] device-mapper: ioctl: 4.20.0-ioctl (2011-02-02) initialised: dm-devel@redhat.com
[    2.369235] cpuidle: using governor ladder
[    2.369366] cpuidle: using governor menu
[    2.369367] EFI Variables Facility v0.08 2004-May-17
[    2.369518] TCP cubic registered
[    2.369610] NET: Registered protocol family 10
[    2.369669] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input4
[    2.370028] NET: Registered protocol family 17
[    2.370039] Registering the dns_resolver key type
[    2.370093] PM: Hibernation image not present or could not be loaded.
[    2.370100] registered taskstats version 1
[    2.379642]   Magic number: 8:249:235
[    2.379735] rtc_cmos 00:06: setting system clock to 2012-04-20 15:14:34 UTC (1334934874)
[    2.380364] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    2.380365] EDD information not available.
[    2.381371] Freeing unused kernel memory: 988k freed
[    2.381458] Write protecting the kernel read-only data: 12288k
[    2.385370] Freeing unused kernel memory: 2032k freed
[    2.388081] Freeing unused kernel memory: 1388k freed
[    2.398534] udevd[90]: starting version 173
[    2.412667] e1000e: Intel(R) PRO/1000 Network Driver - 1.3.10-k2
[    2.412670] e1000e: Copyright(c) 1999 - 2011 Intel Corporation.
[    2.412710] e1000e 0000:00:19.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    2.412722] e1000e 0000:00:19.0: setting latency timer to 64
[    2.412828] e1000e 0000:00:19.0: irq 42 for MSI/MSI-X
[    2.420930] sdhci: Secure Digital Host Controller Interface driver
[    2.420932] sdhci: Copyright(c) Pierre Ossman
[    2.421273] sdhci-pci 0000:0b:00.1: SDHCI controller found [1217:8321] (rev 5)
[    2.421297] sdhci-pci 0000:0b:00.1: PCI INT B -> GSI 18 (level, low) -> IRQ 18
[    2.421345] sdhci-pci 0000:0b:00.1: Invalid iomem size. You may experience problems.
[    2.421384] sdhci-pci 0000:0b:00.1: setting latency timer to 64
[    2.421408] mmc0: no vmmc regulator found
[    2.421438] Registered led device: mmc0::
[    2.421482] mmc0: SDHCI controller on PCI [0000:0b:00.1] using DMA
[    2.422224] firewire_ohci 0000:0b:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    2.422234] firewire_ohci 0000:0b:00.0: setting latency timer to 64
[    2.474988] firewire_ohci: Added fw-ohci device 0000:0b:00.0, OHCI v1.10, 8 IR + 8 IT contexts, quirks 0x10
[    2.606386] e1000e 0000:00:19.0: eth0: (PCI Express:2.5GT/s:Width x1) 5c:26:0a:57:d6:ba
[    2.606389] e1000e 0000:00:19.0: eth0: Intel(R) PRO/1000 Network Connection
[    2.606439] e1000e 0000:00:19.0: eth0: MAC: 10, PHY: 11, PBA No: 4041FF-0FF
[    2.606463] ahci 0000:00:1f.2: version 3.0
[    2.634973] ahci 0000:00:1f.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    2.635139] ahci 0000:00:1f.2: irq 43 for MSI/MSI-X
[    2.635169] ahci: SSS flag set, parallel bus scan disabled
[    2.650939] ahci 0000:00:1f.2: AHCI 0001.0300 32 slots 6 ports 6 Gbps 0x3b impl RAID mode
[    2.650950] ahci 0000:00:1f.2: flags: 64bit ncq sntf stag pm led clo pio slum part ems sxs apst 
[    2.650955] ahci 0000:00:1f.2: setting latency timer to 64
[    2.658910] usb 1-1: new high speed USB device number 2 using ehci_hcd
[    2.683254] scsi0 : ahci
[    2.683379] scsi1 : ahci
[    2.683430] scsi2 : ahci
[    2.683482] scsi3 : ahci
[    2.683532] scsi4 : ahci
[    2.683581] scsi5 : ahci
[    2.710880] Refined TSC clocksource calibration: 2693.878 MHz.
[    2.710893] Switching to clocksource tsc
[    2.791753] hub 1-1:1.0: USB hub found
[    2.791852] hub 1-1:1.0: 6 ports detected
[    2.902845] usb 2-1: new high speed USB device number 2 using ehci_hcd
[    2.974887] firewire_core: created device fw0: GUID 029e86c1374fc000, S400
[    3.035680] hub 2-1:1.0: USB hub found
[    3.035777] hub 2-1:1.0: 8 ports detected
[    3.106933] usb 1-1.4: new full speed USB device number 3 using ehci_hcd
[    3.274883] usb 1-1.5: new high speed USB device number 4 using ehci_hcd
[    3.374876] acpi device:16: registered as cooling_device4
[    3.475071] ata1: SATA max UDMA/133 abar m2048@0xe6740000 port 0xe6740100 irq 43
[    3.475075] ata2: SATA max UDMA/133 abar m2048@0xe6740000 port 0xe6740180 irq 43
[    3.475077] ata3: DUMMY
[    3.475079] ata4: SATA max UDMA/133 abar m2048@0xe6740000 port 0xe6740280 irq 43
[    3.475082] ata5: SATA max UDMA/133 abar m2048@0xe6740000 port 0xe6740300 irq 43
[    3.475085] ata6: SATA max UDMA/133 abar m2048@0xe6740000 port 0xe6740380 irq 43
[    3.602708] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:13/LNXVIDEO:00/input/input5
[    3.602756] ACPI: Video Device [VID] (multi-head: yes  rom: yes  post: no)
[    3.794538] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    3.818833] usb 2-1.8: new full speed USB device number 3 using ehci_hcd
[    3.839268] ata1.00: ACPI cmd 00/00:00:00:00:00:a0 (NOP) rejected by device (Stat=0x51 Err=0x04)
[    3.839482] ata1.00: ATA-8: SAMSUNG HM500JJ, 2AK10002, max UDMA/133
[    3.839484] ata1.00: 976773168 sectors, multi 16: LBA48 NCQ (depth 31/32), AA
[    3.851342] ata1.00: ACPI cmd 00/00:00:00:00:00:a0 (NOP) rejected by device (Stat=0x51 Err=0x04)
[    3.851559] ata1.00: configured for UDMA/133
[    3.858647] scsi 0:0:0:0: Direct-Access     ATA      SAMSUNG HM500JJ  2AK1 PQ: 0 ANSI: 5
[    3.858783] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    3.858808] sd 0:0:0:0: [sda] 976773168 512-byte logical blocks: (500 GB/465 GiB)
[    3.858841] sd 0:0:0:0: [sda] Write Protect is off
[    3.858843] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    3.858854] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    3.911095]  sda: sda1 sda2 < sda5 >
[    3.911362] sd 0:0:0:0: [sda] Attached SCSI disk
[    3.933702] usb 2-1.8: config 0 descriptor??
[    4.178425] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    4.188408] ata2.00: ATAPI: TSSTcorp DVD+/-RW TS-U633J, D400, max UDMA/100
[    4.203405] ata2.00: configured for UDMA/100
[    4.211400] scsi 1:0:0:0: CD-ROM            TSSTcorp DVD+-RW TS-U633J D400 PQ: 0 ANSI: 5
[    4.221281] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[    4.221285] cdrom: Uniform CD-ROM driver Revision: 3.20
[    4.221404] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    4.221461] sr 1:0:0:0: Attached scsi generic sg1 type 5
[    4.538310] ata4: SATA link down (SStatus 0 SControl 300)
[    4.858212] ata5: SATA link down (SStatus 0 SControl 300)
[    5.178102] ata6: SATA link down (SStatus 0 SControl 300)
[    6.475469] vesafb: mode is 640x480x32, linelength=2560, pages=0
[    6.475471] vesafb: scrolling: redraw
[    6.475473] vesafb: Truecolor: size=8:8:8:8, shift=24:16:8:0
[    6.476846] vesafb: framebuffer at 0xe1000000, mapped to 0xffffc90005100000, using 1216k, total 1216k
[    6.476925] Console: switching to colour frame buffer device 80x30
[    6.476933] fb0: VESA VGA frame buffer device
[    6.735160] EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: (null)
[    8.997714] udevd[359]: starting version 173
[   10.316731] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
[   10.360067] lp: driver loaded but no devices found
[   10.855951] wmi: Mapper loaded
[   10.877656] parport_pc 00:08: [io  0x0378-0x037b]
[   10.877748] parport_pc 00:08: [irq 5]
[   10.913278] parport_pc 00:08: activated
[   10.913281] parport_pc 00:08: reported by Plug and Play ACPI
[   10.913354] parport_pc 00:08: disabled
[   10.961583] dcdbas dcdbas: Dell Systems Management Base Driver (version 5.6.0-3.2)
[   11.205545] mei: module is from the staging directory, the quality is unknown, you have been warned.
[   11.205833] mei 0000:00:16.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   11.205838] mei 0000:00:16.0: setting latency timer to 64
[   11.220999] ppdev: user-space parallel port driver
[   11.334148] alps.c: Enabled hardware quirk, falling back to psmouse-core
[   11.347297] input: ImPS/2 ALPS GlidePoint as /devices/platform/i8042/serio1/input/input6
[   11.417562] Bluetooth: Core ver 2.16
[   11.417579] NET: Registered protocol family 31
[   11.417580] Bluetooth: HCI device and connection manager initialized
[   11.417582] Bluetooth: HCI socket layer initialized
[   11.417583] Bluetooth: L2CAP socket layer initialized
[   11.418037] Bluetooth: SCO socket layer initialized
[   11.434764] input: Dell WMI hotkeys as /devices/virtual/input/input7
[   11.451840] Bluetooth: Generic Bluetooth USB driver ver 0.6
[   11.452111] usbcore: registered new interface driver btusb
[   11.562424] cfg80211: Calling CRDA to update world regulatory domain
[   12.561530] iwlagn: Intel(R) Wireless WiFi Link AGN driver for Linux, in-tree:
[   12.561532] iwlagn: Copyright(c) 2003-2011 Intel Corporation
[   12.561627] iwlagn 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   12.561658] iwlagn 0000:03:00.0: setting latency timer to 64
[   12.561726] iwlagn 0000:03:00.0: Detected Intel(R) Centrino(R) Ultimate-N 6300 AGN, REV=0x74
[   12.570811] iwlagn 0000:03:00.0: device EEPROM VER=0x43a, CALIB=0x6
[   12.570813] iwlagn 0000:03:00.0: Device SKU: 0Xb
[   12.570814] iwlagn 0000:03:00.0: Valid Tx ant: 0X7, Valid Rx ant: 0X7
[   12.570825] iwlagn 0000:03:00.0: Tunable channels: 13 802.11bg, 24 802.11a channels
[   12.570956] iwlagn 0000:03:00.0: irq 44 for MSI/MSI-X
[   12.626369] cfg80211: World regulatory domain updated:
[   12.626372] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   12.626374] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   12.626375] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   12.626376] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   12.626378] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   12.626379] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   12.956542] Linux video capture interface: v2.00
[   13.285823] iwlagn 0000:03:00.0: loaded firmware version 9.221.4.1 build 25532
[   13.285970] Registered led device: phy0-led
[   13.285993] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain 
[   13.354983] uvcvideo: Found UVC 1.00 device Laptop_Integrated_Webcam_FHD (1bcf:2802)
[   13.377597] input: Laptop_Integrated_Webcam_FHD as /devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.5/1-1.5:1.0/input/input8
[   13.377652] usbcore: registered new interface driver uvcvideo
[   13.377654] USB Video Class driver (v1.1.0)
[   13.994058] ieee80211 phy0: Selected rate control algorithm 'iwl-agn-rs'
[   14.698513] nvidia: module license 'NVIDIA' taints kernel.
[   14.698516] Disabling lock debugging due to kernel taint
[   14.894125] type=1400 audit(1334934887.012:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=748 comm="apparmor_parser"
[   14.894133] type=1400 audit(1334934887.012:3): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=816 comm="apparmor_parser"
[   14.894534] type=1400 audit(1334934887.012:4): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=749 comm="apparmor_parser"
[   14.894541] type=1400 audit(1334934887.012:5): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=816 comm="apparmor_parser"
[   14.894547] type=1400 audit(1334934887.012:6): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=748 comm="apparmor_parser"
[   14.894795] type=1400 audit(1334934887.012:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=749 comm="apparmor_parser"
[   14.894801] type=1400 audit(1334934887.012:8): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=816 comm="apparmor_parser"
[   14.894806] type=1400 audit(1334934887.012:9): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=748 comm="apparmor_parser"
[   14.894966] type=1400 audit(1334934887.016:10): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=749 comm="apparmor_parser"
[   15.034566] nvidia 0000:01:00.0: power state changed by ACPI to D0
[   15.034570] nvidia 0000:01:00.0: power state changed by ACPI to D0
[   15.034577] nvidia 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   15.034583] nvidia 0000:01:00.0: setting latency timer to 64
[   15.034586] vgaarb: device changed decodes: PCI:0000:01:00.0,olddecodes=io+mem,decodes=none:owns=io+mem
[   15.034681] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  280.13  Wed Jul 27 16:53:56 PDT 2011
[   15.793673] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[   15.793728] HDA Intel 0000:00:1b.0: irq 45 for MSI/MSI-X
[   15.793748] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   15.947434] input: HDA Intel PCH Mic at Sep Left Jack as /devices/pci0000:00/0000:00:1b.0/sound/card0/input9
[   15.947562] input: HDA Intel PCH Mic at Ext Left Jack as /devices/pci0000:00/0000:00:1b.0/sound/card0/input10
[   15.947661] input: HDA Intel PCH Line Out at Sep Left Jack as /devices/pci0000:00/0000:00:1b.0/sound/card0/input11
[   15.947761] input: HDA Intel PCH HP Out at Ext Left Jack as /devices/pci0000:00/0000:00:1b.0/sound/card0/input12
[   15.948015] HDA Intel 0000:01:00.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[   15.948017] hda_intel: Disabling MSI
[   15.948084] HDA Intel 0000:01:00.1: setting latency timer to 64
[   16.933235] init: failsafe main process (836) killed by TERM signal
[   16.986255] HDMI status: Pin=5 Presence_Detect=0 ELD_Valid=0
[   17.010252] HDMI status: Pin=6 Presence_Detect=0 ELD_Valid=0
[   17.034238] HDMI status: Pin=7 Presence_Detect=0 ELD_Valid=0
[   17.050297] input: HDA NVidia HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:01.0/0000:01:00.1/sound/card1/input13
[   17.050385] input: HDA NVidia HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:01.0/0000:01:00.1/sound/card1/input14
[   17.050441] input: HDA NVidia HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:01.0/0000:01:00.1/sound/card1/input15
[   20.496943] type=1400 audit(1334934892.616:11): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=999 comm="apparmor_parser"
[   20.497203] type=1400 audit(1334934892.620:12): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=999 comm="apparmor_parser"
[   20.497356] type=1400 audit(1334934892.620:13): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=999 comm="apparmor_parser"
[   20.759669] type=1400 audit(1334934892.880:14): apparmor="STATUS" operation="profile_load" name="/usr/lib/telepathy/mission-control-5" pid=1002 comm="apparmor_parser"
[   20.759894] type=1400 audit(1334934892.880:15): apparmor="STATUS" operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" pid=995 comm="apparmor_parser"
[   20.759944] type=1400 audit(1334934892.880:16): apparmor="STATUS" operation="profile_load" name="/usr/lib/telepathy/telepathy-*" pid=1002 comm="apparmor_parser"
[   20.760230] type=1400 audit(1334934892.880:17): apparmor="STATUS" operation="profile_load" name="/usr/sbin/cupsd" pid=995 comm="apparmor_parser"
[   20.760592] type=1400 audit(1334934892.880:18): apparmor="STATUS" operation="profile_replace" name="/usr/lib/cups/backend/cups-pdf" pid=1003 comm="apparmor_parser"
[   20.761194] type=1400 audit(1334934892.884:19): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/cupsd" pid=1003 comm="apparmor_parser"
[   21.028170] type=1400 audit(1334934893.148:20): apparmor="STATUS" operation="profile_load" name="/usr/lib/lightdm/lightdm-guest-session-wrapper" pid=998 comm="apparmor_parser"
[   21.544927] e1000e 0000:00:19.0: irq 42 for MSI/MSI-X
[   21.600887] e1000e 0000:00:19.0: irq 42 for MSI/MSI-X
[   21.601146] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   22.038446] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   22.163603] Adding 4148220k swap on /dev/mapper/cryptswap1.  Priority:-1 extents:1 across:4148220k 
[   23.316833] init: apport pre-start process (1120) terminated with status 1
[   23.318284] init: apport post-stop process (1180) terminated with status 1
[   24.436787] cfg80211: Found new beacon on frequency: 5220 MHz (Ch 44) on phy0
[   27.980937] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   27.980940] Bluetooth: BNEP filters: protocol multicast
[   28.094982] Bluetooth: RFCOMM TTY layer initialized
[   28.094987] Bluetooth: RFCOMM socket layer initialized
[   28.094989] Bluetooth: RFCOMM ver 1.11
[   30.207830] wlan0: authenticate with e0:46:9a:77:2f:81 (try 1)
[   30.209697] wlan0: authenticated
[   30.310315] wlan0: associate with e0:46:9a:77:2f:81 (try 1)
[   30.325132] wlan0: RX AssocResp from e0:46:9a:77:2f:81 (capab=0x411 status=0 aid=6)
[   30.325135] wlan0: associated
[   30.340202] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   32.033237] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,commit=0
[   34.057382] init: plymouth-stop pre-start process (1512) terminated with status 1
[   38.537154] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,commit=0
[   41.038605] wlan0: no IPv6 routers present
[   64.106512] iwlagn 0000:03:00.0: Aggregation not enabled for tid 0 because load = 10
[   98.638776] iwlagn 0000:03:00.0: Aggregation not enabled for tid 0 because load = 6
[  103.088996] iwlagn 0000:03:00.0: iwlagn_tx_agg_start on ra = e0:46:9a:77:2f:81 tid = 0
logan@logan-Latitude-E6520:~$ dmesg
logan@logan-Latitude-E6520:~$ 
```
No output was given with the cord connected.
> Try using a different USB cable and disabling Developer Mode. Developer / debugging mode *usually* puts the phone in modem mode. I think with CDMA Samsung's you can use ##8778# and set both options to PDA which will force the phone into mass storage.

Also with Samsung's *I believe* mass storage only works with a microsd, not internal storage. Is your microsd mounted and recognized by the phone? Try unmounting it on the phone first. Should be in storage under settings.

dmesg will probably show a modem being connected.
I have debugging mode off at the moment.  It was necessary to have it on to connect to my laptop when I ran Windows 7, but now it seems to make no difference.  Also, I don't have a microSD card in the phone.

Thanks for all your help guys, I really appreciate this.  I wish I was more versed in computers.  Is there a comprehensive online resource I can use to better educate myself on Linux/Ubuntu?

> The above command will work better for logging rather than the one I put in. Takes forever to type decently on this tablet.
Unrelated: what tablet are you using?  I'm considering buying one.

---

### Post by cortman on 2012-04-20
I'm not seeing anything there, I don't think, but someone more versed than me may pick up on something. Can you try lsusb?

Re online learning resources, see the link in my sig.

---

### Post by for.i.am.root on 2012-04-20
If dmesg doesn't detect any connection then either the cable is bad or your phone doesn't detect the cable.

Dmesg should output something when the device is connected.

Has to be the phone or the cable. Did you try the ##8778# and put it in PDA mode?

You can also try accessing it via recovery.

Pull battery from phone.
Hold volume down down while putting battery in.
While holding volume down press and hold power.
Should get a weird screen, not the normal boot screen.

---

### Post by flipper T on 2012-04-20
forget usb & try via bluetooth ?

---

### Post by Arguable on 2012-04-21
> **for.i.am.root said:**
> If dmesg doesn't detect any connection then either the cable is bad or your phone doesn't detect the cable.

Dmesg should output something when the device is connected.

Has to be the phone or the cable. Did you try the ##8778# and put it in PDA mode?

You can also try accessing it via recovery.

Pull battery from phone.
Hold volume down down while putting battery in.
While holding volume down press and hold power.
Should get a weird screen, not the normal boot screen.

I've got it! It was the cord; somehow the cord would allow the phone to charge but not transfer files.  I feel like an idiot.  Thanks everyone for all the help! :)

---

### Post by cortman on 2012-04-21
> **Arguable said:**
> I've got it! It was the cord; somehow the cord would allow the phone to charge but not transfer files.  I feel like an idiot.  Thanks everyone for all the help! :)

Great! Mark the thread [SOLVED] if you would, using the thread tools in the upper right. Good luck!

---

### Post by bookcrazy on 2012-08-07
Thanks for the thread. When I run ```
dmesg
``` the output is ```
[ 3644.424994] usb 2-1.5: new full-speed USB device number 4 using ehci_hcd

``` So how do I mount the phone from here?

---

### Post by jammybob56 on 2012-08-07
Yes, mass storage almost never works with internal memory on any device. Only the memory card, micro sd for galaxy s 2. Maybe you could buy a cheapo micro sd and transfer files to internal memory on the phone. Not exactly practical, but it might work.#-o

if not then im stumped

---

### Post by ivotkl on 2012-11-28
Hello. I have a Samsung Android phone and I see the Card on Computer, but I cannot open its folder. Somewhere I read that installing gMTP would fix it, but I' m trying to work out a better solution that would not include installing "unnecessary" software. Here' s the debug list and msgs info:
 
```
[messages and debug](http://pastebin.com/NRSTw863)
```
 
```
[dmsg output](http://pastebin.com/bYfmFP2v)
```
 
Hope you can help. Thank you in advanced.

---

### Post by ivotkl on 2012-12-02
Shameless bump / update: I decided to create a [new thread](http://ubuntuforums.org/showthread.php?t=2089972) as this one was quite old.

---

### Post by MacHaddock on 2013-01-09
> **cortman said:**
> Well, you could try running

```
lsusb
```before and after plugging the phone in. If there's any difference, you may be able to mount it manually.
To make it easier, disconnect as many other USB devices as you can.

Just running lsusb and then plugging in worked for me :D

thanks

---

