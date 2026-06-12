---
title: "Ubuntu won't pick up my wireless card."
date: 2010-06-29
forum: General Help
---

### Post by fbjoey on 2010-06-29
I have been using a usb speadtouch wireless card on Ubuntu 9.04 on my laptop for a while now and it works just fine. I came across an old desktop and have just installed Ubuntu 10.04 onto it, everything went smoothly, but the same card that works on my 9.04 doesn't work on 10.04 :(.

Can anybody help?


The card is a SpeedTouch 121g, wireless 802.11g USB 2.0 Adapter.

---

### Post by okplayer02 on 2010-06-29
when you plugin your usb stick run the following command from the CLI

```
dmesg
```


can you do a few commands from the CLI first to list the usb devices

```
lsusb
```

then when can determine what chipset

did you try network manager in the top right to see if your usb was detected automatically?

---

### Post by fbjoey on 2010-06-29
No it wasn't automaticly detected.

This is what i got when I ran dmesg

> [    0.104001] pnp 00:08: io resource (0x10-0x1f) overlaps 0000:00:11.6 BAR 0 (0x0-0xff), disabling 
[    0.104001] pnp 00:08: io resource (0x22-0x3f) overlaps 0000:00:11.6 BAR 0 (0x0-0xff), disabling 
[    0.104001] pnp 00:08: io resource (0x44-0x5f) overlaps 0000:00:11.6 BAR 0 (0x0-0xff), disabling 
[    0.104001] pnp 00:08: io resource (0x62-0x63) overlaps 0000:00:11.6 BAR 0 (0x0-0xff), disabling 
[    0.104001] pnp 00:08: io resource (0x65-0x6f) overlaps 0000:00:11.6 BAR 0 (0x0-0xff), disabling 
[    0.104001] pnp 00:08: io resource (0x72-0x7f) overlaps 0000:00:11.6 BAR 0 (0x0-0xff), disabling 
[    0.104001] pnp 00:08: io resource (0x80-0x80) overlaps 0000:00:11.6 BAR 0 (0x0-0xff), disabling 
[    0.104001] pnp 00:08: io resource (0x84-0x86) overlaps 0000:00:11.6 BAR 0 (0x0-0xff), disabling 
[    0.104001] pnp 00:08: io resource (0x88-0x88) overlaps 0000:00:11.6 BAR 0 (0x0-0xff), disabling 
[    0.104001] pnp 00:08: io resource (0x8c-0x8e) overlaps 0000:00:11.6 BAR 0 (0x0-0xff), disabling 
[    0.104001] pnp 00:08: io resource (0x90-0x9f) overlaps 0000:00:11.6 BAR 0 (0x0-0xff), disabling 
[    0.104001] pnp 00:08: io resource (0xa2-0xbf) overlaps 0000:00:11.6 BAR 0 (0x0-0xff), disabling 
[    0.104001] pnp 00:08: io resource (0xe0-0xef) overlaps 0000:00:11.6 BAR 0 (0x0-0xff), disabling 
[    0.105342] pnp: PnP ACPI: found 13 devices 
[    0.105345] ACPI: ACPI bus type pnp unregistered 
[    0.105349] PnPBIOS: Disabled by ACPI PNP 
[    0.105364] system 00:08: ioport range 0x295-0x296 has been reserved 
[    0.105367] system 00:08: ioport range 0x3e1-0x3e7 has been reserved 
[    0.105371] system 00:08: ioport range 0x4d0-0x4d1 has been reserved 
[    0.105375] system 00:08: ioport range 0x800-0x87f has been reserved 
[    0.105379] system 00:08: ioport range 0x400-0x41f has been reserved 
[    0.105386] system 00:09: iomem range 0xfec00000-0xfec00fff could not be reserved 
[    0.105390] system 00:09: iomem range 0xfee00000-0xfee00fff has been reserved 
[    0.105394] system 00:09: iomem range 0xfff80000-0xffffffff has been reserved 
[    0.105401] system 00:0c: iomem range 0x0-0x9ffff could not be reserved 
[    0.105405] system 00:0c: iomem range 0xc0000-0xdffff could not be reserved 
[    0.105409] system 00:0c: iomem range 0xe0000-0xfffff could not be reserved 
[    0.105413] system 00:0c: iomem range 0x100000-0x1ffeffff could not be reserved 
[    0.140107] pci 0000:00:01.0: PCI bridge, secondary bus 0000:01 
[    0.140110] pci 0000:00:01.0:   IO window: disabled 
[    0.140115] pci 0000:00:01.0:   MEM window: 0xfaf00000-0xfbffffff 
[    0.140119] pci 0000:00:01.0:   PREFETCH window: 0xe0000000-0xf9ffffff 
[    0.140134] pci 0000:00:01.0: setting latency timer to 64 
[    0.140140] pci_bus 0000:00: resource 0 io:  [0x00-0xffff] 
[    0.140143] pci_bus 0000:00: resource 1 mem: [0x000000-0xffffffff] 
[    0.140147] pci_bus 0000:01: resource 1 mem: [0xfaf00000-0xfbffffff] 
[    0.140150] pci_bus 0000:01: resource 2 pref mem [0xe0000000-0xf9ffffff] 
[    0.140190] NET: Registered protocol family 2 
[    0.140291] IP route cache hash table entries: 4096 (order: 2, 16384 bytes) 
[    0.140573] TCP established hash table entries: 16384 (order: 5, 131072 bytes) 
[    0.140696] TCP bind hash table entries: 16384 (order: 5, 131072 bytes) 
[    0.140806] TCP: Hash tables configured (established 16384 bind 16384) 
[    0.140809] TCP reno registered 
[    0.140868] NET: Registered protocol family 1 
[    0.140888] pci 0000:00:01.0: disabling DAC on VIA PCI bridge 
[    0.140972] pci 0000:01:00.0: Boot video device 
[    0.141145] cpufreq-nforce2: No nForce2 chipset. 
[    0.141171] Scanning for low memory corruption every 60 seconds 
[    0.141270] audit: initializing netlink socket (disabled) 
[    0.141285] type=2000 audit(1277817165.140:1): initialized 
[    0.151410] Trying to unpack rootfs image as initramfs... 
[    0.164372] HugeTLB registered 4 MB page size, pre-allocated 0 pages 
[    0.165825] VFS: Disk quotas dquot_6.5.2 
[    0.165886] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes) 
[    0.172636] fuse init (API version 7.13) 
[    0.172759] msgmni has been set to 976 
[    0.172994] alg: No test for stdrng (krng) 
[    0.173056] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253) 
[    0.173060] io scheduler noop registered 
[    0.173063] io scheduler anticipatory registered 
[    0.173065] io scheduler deadline registered 
[    0.173104] io scheduler cfq registered (default) 
[    0.173230] pci_hotplug: PCI Hot Plug PCI Core version: 0.5 
[    0.173251] pciehp: PCI Express Hot Plug Controller Driver version: 0.4 
[    0.173358] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0 
[    0.173367] ACPI: Power Button [PWRB] 
[    0.173417] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1 
[    0.173420] ACPI: Power Button [PWRF] 
[    0.173622] processor LNXCPU:00: registered as cooling_device0 
[    0.176921] isapnp: Scanning for PnP cards... 
[    0.182583] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled 
[    0.182670] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A 
[    0.182752] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A 
[    0.183034] 00:0a: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A 
[    0.183147] 00:0b: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A 
[    0.184109] brd: module loaded 
[    0.188784] loop: module loaded 
[    0.188900] input: Macintosh mouse button emulation as /devices/virtual/input/input2 
[    0.189078]   alloc irq_desc for 20 on node -1 
[    0.189081]   alloc kstat_irqs on node -1 
[    0.189089] pata_acpi 0000:00:0f.0: PCI INT B -> GSI 20 (level, low) -> IRQ 20 
[    0.189152] pata_acpi 0000:00:0f.0: PCI INT B disabled 
[    0.189168] pata_acpi 0000:00:0f.1: PCI INT A -> GSI 20 (level, low) -> IRQ 20 
[    0.189188] pata_acpi 0000:00:0f.1: PCI INT A disabled 
[    0.189497] Fixed MDIO Bus: probed 
[    0.189533] PPP generic driver version 2.4.2 
[    0.189576] tun: Universal TUN/TAP device driver, 1.6 
[    0.189579] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com> 
[    0.189650] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver 
[    0.189666]   alloc irq_desc for 21 on node -1 
[    0.189668]   alloc kstat_irqs on node -1 
[    0.189672] ehci_hcd 0000:00:10.4: PCI INT C -> GSI 21 (level, low) -> IRQ 21 
[    0.189688] ehci_hcd 0000:00:10.4: EHCI Host Controller 
[    0.189726] ehci_hcd 0000:00:10.4: new USB bus registered, assigned bus number 1 
[    0.189793] ehci_hcd 0000:00:10.4: irq 21, io mem 0xfab00000 
[    0.240053] ehci_hcd 0000:00:10.4: USB 2.0 started, EHCI 1.00 
[    0.240202] usb usb1: configuration #1 chosen from 1 choice 
[    0.240237] hub 1-0:1.0: USB hub found 
[    0.240250] hub 1-0:1.0: 8 ports detected 
[    0.240316] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver 
[    0.240339] uhci_hcd: USB Universal Host Controller Interface driver 
[    0.240397] uhci_hcd 0000:00:10.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21 
[    0.240405] uhci_hcd 0000:00:10.0: UHCI Host Controller 
[    0.240441] uhci_hcd 0000:00:10.0: new USB bus registered, assigned bus number 2 
[    0.240465] uhci_hcd 0000:00:10.0: irq 21, io base 0x0000b000 
[    0.240558] usb usb2: configuration #1 chosen from 1 choice 
[    0.240583] hub 2-0:1.0: USB hub found 
[    0.240597] hub 2-0:1.0: 2 ports detected 
[    0.240641] uhci_hcd 0000:00:10.1: PCI INT A -> GSI 21 (level, low) -> IRQ 21 
[    0.240646] uhci_hcd 0000:00:10.1: UHCI Host Controller 
[    0.240684] uhci_hcd 0000:00:10.1: new USB bus registered, assigned bus number 3 
[    0.240702] uhci_hcd 0000:00:10.1: irq 21, io base 0x0000b400 
[    0.240794] usb usb3: configuration #1 chosen from 1 choice 
[    0.240819] hub 3-0:1.0: USB hub found 
[    0.240827] hub 3-0:1.0: 2 ports detected 
[    0.240871] uhci_hcd 0000:00:10.2: PCI INT B -> GSI 21 (level, low) -> IRQ 21 
[    0.240876] uhci_hcd 0000:00:10.2: UHCI Host Controller 
[    0.240906] uhci_hcd 0000:00:10.2: new USB bus registered, assigned bus number 4 
[    0.240924] uhci_hcd 0000:00:10.2: irq 21, io base 0x0000b800 
[    0.241024] usb usb4: configuration #1 chosen from 1 choice 
[    0.241053] hub 4-0:1.0: USB hub found 
[    0.241062] hub 4-0:1.0: 2 ports detected 
[    0.241104] uhci_hcd 0000:00:10.3: PCI INT B -> GSI 21 (level, low) -> IRQ 21 
[    0.241110] uhci_hcd 0000:00:10.3: UHCI Host Controller 
[    0.241142] uhci_hcd 0000:00:10.3: new USB bus registered, assigned bus number 5 
[    0.241160] uhci_hcd 0000:00:10.3: irq 21, io base 0x0000c000 
[    0.241257] usb usb5: configuration #1 chosen from 1 choice 
[    0.241285] hub 5-0:1.0: USB hub found 
[    0.241293] hub 5-0:1.0: 2 ports detected 
[    0.241372] PNP: PS/2 Controller [PNP0303:PS2K] at 0x60,0x64 irq 1 
[    0.241375] PNP: PS/2 appears to have AUX port disabled, if this is incorrect please boot with i8042.nopnp 
[    0.241554] serio: i8042 KBD port at 0x60,0x64 irq 1 
[    0.241657] mice: PS/2 mouse device common for all mice 
[    0.241771] rtc_cmos 00:02: RTC can wake from S4 
[    0.241810] rtc_cmos 00:02: rtc core: registered rtc_cmos as rtc0 
[    0.241861] rtc0: alarms up to one year, y3k, 114 bytes nvram 
[    0.241967] device-mapper: uevent: version 1.0.3 
[    0.242083] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: [email]dm-devel@redhat.com[/email] 
[    0.244483] device-mapper: multipath: version 1.1.0 loaded 
[    0.244505] device-mapper: multipath round-robin: version 1.0.0 loaded 
[    0.244660] EISA: Probing bus 0 at eisa.0 
[    0.244668] Cannot allocate resource for EISA slot 1 
[    0.244694] EISA: Detected 0 cards. 
[    0.245921] cpuidle: using governor ladder 
[    0.245924] cpuidle: using governor menu 
[    0.246361] TCP cubic registered 
[    0.246519] NET: Registered protocol family 10 
[    0.246952] lo: Disabled Privacy Extensions 
[    0.247273] NET: Registered protocol family 17 
[    0.247304] powernow-k8: Found 1 AMD Athlon(tm) 64 Processor 3000+ processors (1 cpu cores) (version 2.20.00) 
[    0.247348] powernow-k8:    0 : fid 0xc (2000 MHz), vid 0x2 
[    0.247351] powernow-k8:    1 : fid 0xa (1800 MHz), vid 0x6 
[    0.247353] powernow-k8:    2 : fid 0x2 (1000 MHz), vid 0x12 
[    0.247383] powernow-k8: ph2 null fid transition 0xc 
[    0.247401] Using IPI No-Shortcut mode 
[    0.247499] PM: Resume from disk failed. 
[    0.247511] registered taskstats version 1 
[    0.247815]   Magic number: 14:724:231 
[    0.247922] rtc_cmos 00:02: setting system clock to 2010-06-29 13:12:45 UTC (1277817165) 
[    0.247926] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found 
[    0.247928] EDD information not available. 
[    0.260638] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input3 
[    0.615869] Freeing initrd memory: 7783k freed 
[    0.666962] usb 1-2: new high speed USB device using ehci_hcd and address 3 
[    0.753902] isapnp: No Plug & Play device found 
[    0.753915] Freeing unused kernel memory: 656k freed 
[    0.754597] Write protecting the kernel text: 4676k 
[    0.754628] Write protecting the kernel read-only data: 1840k 
[    0.773898] udev: starting version 151 
[    0.841940] usb 1-2: configuration #1 chosen from 2 choices 
[    0.964374] usb 1-3: new high speed USB device using ehci_hcd and address 4 
[    0.976747] pata_via 0000:00:0f.1: version 0.3.4 
[    0.976764] pata_via 0000:00:0f.1: PCI INT A -> GSI 20 (level, low) -> IRQ 20 
[    0.992989] Floppy drive(s): fd0 is 1.44M 
[    0.999052] scsi0 : pata_via 
[    1.003549] scsi1 : pata_via 
[    1.005187] ata1: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xfc00 irq 14 
[    1.005190] ata2: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xfc08 irq 15 
[    1.005279] sata_via 0000:00:0f.0: version 2.4 
[    1.005292] sata_via 0000:00:0f.0: PCI INT B -> GSI 20 (level, low) -> IRQ 20 
[    1.005339] sata_via 0000:00:0f.0: routed to hard irq line 10 
[    1.005662] scsi2 : sata_via 
[    1.005759] scsi3 : sata_via 
[    1.007040] ata3: SATA max UDMA/133 cmd 0xe000 ctl 0xd800 bmdma 0xc800 irq 20 
[    1.007043] ata4: SATA max UDMA/133 cmd 0xd400 ctl 0xd000 bmdma 0xc808 irq 20 
[    1.017674] FDC 0 is a post-1991 82077 
[    1.017728] Initializing USB Mass Storage driver... 
[    1.018006] via-rhine.c:v1.10-LK1.4.3 2007-03-06 Written by Donald Becker 
[    1.018043]   alloc irq_desc for 23 on node -1 
[    1.018045]   alloc kstat_irqs on node -1 
[    1.018053] via-rhine 0000:00:12.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23 
[    1.020194] eth0: VIA Rhine II at 0xfaa00000, 00:11:2f:00:fb:94, IRQ 23. 
[    1.020909] eth0: MII PHY found at address 1, status 0x7849 advertising 01e1 Link 0000. 
[    1.021361] scsi4 : SCSI emulation for USB Mass Storage devices 
[    1.021492] usbcore: registered new interface driver usb-storage 
[    1.021495] USB Mass Storage support registered. 
[    1.021568] usb-storage: device found at 3 
[    1.021569] usb-storage: waiting for device to settle before scanning 
[    1.104810] usb 1-3: configuration #1 chosen from 1 choice 
[    1.212009] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 300) 
[    1.284774] ata1.00: ATAPI: SONY DVD-ROM DDU1613, 9YS1, max UDMA/33 
[    1.284806] ata1.01: ATAPI: SONY    DVD RW DW-U18A, UYS1, max UDMA/33 
[    1.285292] ata1.00: configured for UDMA/33 
[    1.300241] ata1.01: configured for UDMA/33 
[    1.302505] scsi 0:0:0:0: CD-ROM            SONY     DVD-ROM DDU1613  9YS1 PQ: 0 ANSI: 5 
[    1.304149] sr0: scsi3-mmc drive: 40x/40x cd/rw xa/form2 cdda tray 
[    1.304152] Uniform CD-ROM driver Revision: 3.20 
[    1.304358] sr 0:0:0:0: Attached scsi CD-ROM sr0 
[    1.304465] sr 0:0:0:0: Attached scsi generic sg0 type 5 
[    1.305315] scsi 0:0:1:0: CD-ROM            SONY     DVD RW DW-U18A   UYS1 PQ: 0 ANSI: 5 
[    1.309002] sr1: scsi3-mmc drive: 40x/40x writer cd/rw xa/form2 cdda tray 
[    1.309187] sr 0:0:1:0: Attached scsi CD-ROM sr1 
[    1.309283] sr 0:0:1:0: Attached scsi generic sg1 type 5 
[    1.344016] usb 2-1: new low speed USB device using uhci_hcd and address 2 
[    1.376362] ata3.00: ATA-7: Maxtor 6Y200M0, YAR51HW0, max UDMA/133 
[    1.376365] ata3.00: 398297088 sectors, multi 16: LBA48 
[    1.392395] ata3.00: configured for UDMA/133 
[    1.475334] scsi 2:0:0:0: Direct-Access     ATA      Maxtor 6Y200M0   YAR5 PQ: 0 ANSI: 5 
[    1.475462] sd 2:0:0:0: Attached scsi generic sg2 type 0 
[    1.475657] sd 2:0:0:0: [sda] 398297088 512-byte logical blocks: (203 GB/189 GiB) 
[    1.475701] sd 2:0:0:0: [sda] Write Protect is off 
[    1.475704] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00 
[    1.475727] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA 
[    1.475850]  sda: sda1 sda2 < sda5 > 
[    1.514585] sd 2:0:0:0: [sda] Attached SCSI disk 
[    1.527455] usb 2-1: configuration #1 chosen from 1 choice 
[    1.676015] ata4: SATA link down 1.5 Gbps (SStatus 0 SControl 300) 
[    1.694721]   alloc irq_desc for 16 on node -1 
[    1.694725]   alloc kstat_irqs on node -1 
[    1.694733] ohci1394 0000:00:07.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16 
[    1.704635] usbcore: registered new interface driver hiddev 
[    1.717786] input: Logitech Optical USB Mouse as /devices/pci0000:00/0000:00:10.0/usb2/2-1/2-1:1.0/input/input4 
[    1.717880] generic-usb 0003:046D:C016.0001: input,hidraw0: USB HID v1.10 Mouse [Logitech Optical USB Mouse] on usb-0000:00:10.0-1/input0 
[    1.717912] usbcore: registered new interface driver usbhid 
[    1.717916] usbhid: v2.6:USB HID core driver 
[    1.750047] ohci1394: fw-host0: OHCI-1394 1.0 (PCI): IRQ=[16]  MMIO=[fae00000-fae007ff]  Max Packet=[2048]  IR/IT contexts=[4/8] 
[    2.016606] EXT4-fs (sda1): mounted filesystem with ordered data mode 
[    3.024134] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[00e01800004a96ca] 
[    3.435070] Adding 1485816k swap on /dev/sda5.  Priority:-1 extents:1 across:1485816k 
[    3.477512] udev: starting version 151 
[    4.251051] parport_pc 00:07: reported by Plug and Play ACPI 
[    4.251158] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,EPP,ECP,DMA] 
[    4.288675] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4 
[    4.455752] cfg80211: Calling CRDA to update world regulatory domain 
[    4.487826] ppdev: user-space parallel port driver 
[    4.489596] lp0: using parport0 (interrupt-driven). 
[    4.567929] Linux agpgart interface v0.103 
[    4.699943] type=1505 audit(1277813569.948:2):  operation="profile_load" pid=522 name="/sbin/dhclient3" 
[    4.700299] type=1505 audit(1277813569.952:3):  operation="profile_load" pid=522 name="/usr/lib/NetworkManager/nm-dhcp-client.action" 
[    4.700461] type=1505 audit(1277813569.952:4):  operation="profile_load" pid=522 name="/usr/lib/connman/scripts/dhclient-script" 
[    5.021477] agpgart-amd64 0000:00:00.0: AGP bridge [1106/0204] 
[    5.027933] [drm] Initialized drm 1.1.0 20060810 
[    5.032301] agpgart-amd64 0000:00:00.0: AGP aperture is 128M @ 0xd8000000 
[    5.379567] cfg80211: World regulatory domain updated: 
[    5.379572] 	(start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp) 
[    5.379576] 	(2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm) 
[    5.379579] 	(2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm) 
[    5.379582] 	(2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm) 
[    5.379585] 	(5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm) 
[    5.379588] 	(5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm) 
[    5.463697] nouveau 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16 
[    5.471458] [drm] nouveau 0000:01:00.0: Detected an NV30 generation card (0x034200b1) 
[    5.471536] [drm] nouveau 0000:01:00.0: Attempting to load BIOS image from PROM 
[    5.598184] [drm] nouveau 0000:01:00.0: ... appears to be valid 
[    5.598404] [drm] nouveau 0000:01:00.0: BMP BIOS found 
[    5.598407] [drm] nouveau 0000:01:00.0: BMP version 5.40 
[    5.598411] [drm] nouveau 0000:01:00.0: Bios version 04.34.20.42 
[    5.598415] [drm] nouveau 0000:01:00.0: Found Display Configuration Block version 2.2 
[    5.598420] [drm] nouveau 0000:01:00.0: Raw DCB entry 0: 01000300 000088b8 
[    5.598424] [drm] nouveau 0000:01:00.0: Raw DCB entry 1: 02010310 000088b8 
[    5.598428] [drm] nouveau 0000:01:00.0: Raw DCB entry 2: 01010312 00000000 
[    5.598431] [drm] nouveau 0000:01:00.0: Raw DCB entry 3: 02020321 00000003 
[    5.598613] [drm] nouveau 0000:01:00.0: Loading NV17 power sequencing microcode 
[    5.598617] [drm] nouveau 0000:01:00.0: Parsing VBIOS init table 0 at offset 0xEF40 
[    5.612044] [drm] nouveau 0000:01:00.0: Parsing VBIOS init table 1 at offset 0xF1B0 
[    5.612055] [drm] nouveau 0000:01:00.0: Parsing VBIOS init table 2 at offset 0xF2F6 
[    5.612094] [drm] nouveau 0000:01:00.0: Parsing VBIOS init table 3 at offset 0xF488 
[    5.612098] [drm] nouveau 0000:01:00.0: Parsing VBIOS init table 4 at offset 0xF4A5 
[    5.612104] [drm] nouveau 0000:01:00.0: Parsing VBIOS init table 5 at offset 0xF4C2 
[    5.625860] [drm] nouveau 0000:01:00.0: Parsing VBIOS init table 6 at offset 0xF646 
[    5.638927] [TTM] Zone  kernel: Available graphics memory: 254236 kiB. 
[    5.638942] [drm] nouveau 0000:01:00.0: 128 MiB VRAM 
[    5.639003] agpgart-amd64 0000:00:00.0: AGP 3.0 bridge 
[    5.639016] agpgart: modprobe tried to set rate=x12. Setting to AGP3 x8 mode. 
[    5.639024] agpgart-amd64 0000:00:00.0: putting AGP V3 device into 8x mode 
[    5.639099] nouveau 0000:01:00.0: putting AGP V3 device into 8x mode 
[    5.639103] [drm] nouveau 0000:01:00.0: 128 MiB GART (aperture) 
[    5.639350] [drm] nouveau 0000:01:00.0: Allocating FIFO number 0 
[    5.640234] [drm] nouveau 0000:01:00.0: nouveau_channel_alloc: initialised FIFO 0 
[    5.640243] [drm] nouveau 0000:01:00.0: Initial CRTC_OWNER is 0 
[    5.640250] [drm] nouveau 0000:01:00.0: Saving VGA fonts 
[    5.679060] usb 1-3: reset high speed USB device using ehci_hcd and address 4 
[    5.679327] [drm] nouveau 0000:01:00.0: Detected a VGA connector 
[    5.679598] [drm] nouveau 0000:01:00.0: Detected a DVI-I connector 
[    5.679792] [drm] nouveau 0000:01:00.0: Detected a TV connector 
[    5.680990] [drm] nouveau 0000:01:00.0: Setting dpms mode 3 on vga encoder (output 0) 
[    5.680994] [drm] nouveau 0000:01:00.0: Setting dpms mode 3 on vga encoder (output 1) 
[    5.680997] [drm] nouveau 0000:01:00.0: Setting dpms mode 3 on tmds encoder (output 2) 
[    5.681001] [drm] nouveau 0000:01:00.0: Setting dpms mode 3 on TV encoder (output 3) 
[    5.817794] usb 1-3: firmware: requesting isl3887usb 
[    5.889473] usb 1-3: (p54usb) cannot load firmware isl3887usb (-2)! 
[    5.889533] usb 1-3: firmware: requesting isl3887usb_bare 
[    5.892753] p54usb: probe of 1-3:1.0 failed with error -2 
[    5.892779] usbcore: registered new interface driver p54usb 
[    5.916218] [drm] nouveau 0000:01:00.0: allocated 1280x1024 fb: 0x49000, bo d647d000 
[    5.916319] fb0: nouveaufb frame buffer device 
[    5.916321] registered panic notifier 
[    5.916327] [drm] Initialized nouveau 0.0.15 20090420 for 0000:01:00.0 on minor 0 
[    6.024211] usb-storage: device scan complete 
[    6.031193] scsi 4:0:0:0: Direct-Access     Apple    iPod             1.62 PQ: 0 ANSI: 0 
[    6.033364] sd 4:0:0:0: Attached scsi generic sg3 type 0 
[    6.034184] sd 4:0:0:0: [sdb] 19488471 4096-byte logical blocks: (79.8 GB/74.3 GiB) 
[    6.034676] sd 4:0:0:0: [sdb] Write Protect is off 
[    6.034679] sd 4:0:0:0: [sdb] Mode Sense: 68 00 00 08 
[    6.034682] sd 4:0:0:0: [sdb] Assuming drive cache: write through 
[    6.040698] sd 4:0:0:0: [sdb] 19488471 4096-byte logical blocks: (79.8 GB/74.3 GiB) 
[    6.051958] sd 4:0:0:0: [sdb] Assuming drive cache: write through 
[    6.052038]  sdb: sdb1 
[    6.201354] sd 4:0:0:0: [sdb] 19488471 4096-byte logical blocks: (79.8 GB/74.3 GiB) 
[    6.201939] sd 4:0:0:0: [sdb] Assuming drive cache: write through 
[    6.201998] sd 4:0:0:0: [sdb] Attached SCSI removable disk 
[    6.244098] vga16fb: initializing 
[    6.244104] vga16fb: mapped to 0xc00a0000 
[    6.244112] vga16fb: not registering due to another framebuffer present 
[    6.552594] [drm] nouveau 0000:01:00.0: Setting dpms mode 0 on vga encoder (output 1) 
[    6.552600] [drm] nouveau 0000:01:00.0: Output DVI-I-1 is running on CRTC 0 using output B 
[    6.553517] VIA 82xx Modem 0000:00:11.6: enabling device (0000 -> 0001) 
[    6.553526]   alloc irq_desc for 22 on node -1 
[    6.553528]   alloc kstat_irqs on node -1 
[    6.553535] VIA 82xx Modem 0000:00:11.6: PCI INT C -> GSI 22 (level, low) -> IRQ 22 
[    6.560584] Console: switching to colour frame buffer device 160x64 
[    7.304017] VIA 82xx Modem 0000:00:11.6: setting latency timer to 64 
[    7.808228] VIA 82xx Modem 0000:00:11.6: PCI INT C disabled 
[    7.808244] VIA 82xx Modem: probe of 0000:00:11.6 failed with error -13 
[    7.808429] VIA 82xx Audio 0000:00:11.5: PCI INT C -> GSI 22 (level, low) -> IRQ 22 
[    7.808579] VIA 82xx Audio 0000:00:11.5: setting latency timer to 64 
[   10.206296] eth0: link down 
[   10.206347] ADDRCONF(NETDEV_UP): eth0: link is not ready 
[   10.775213] type=1505 audit(1277813576.024:5):  operation="profile_load" pid=1006 name="/usr/share/gdm/guest-session/Xsession" 
[   10.777404] type=1505 audit(1277813576.028:6):  operation="profile_replace" pid=1008 name="/sbin/dhclient3" 
[   10.777713] type=1505 audit(1277813576.028:7):  operation="profile_replace" pid=1008 name="/usr/lib/NetworkManager/nm-dhcp-client.action" 
[   10.777886] type=1505 audit(1277813576.028:8):  operation="profile_replace" pid=1008 name="/usr/lib/connman/scripts/dhclient-script" 
[   10.888452] type=1505 audit(1277813576.140:9):  operation="profile_load" pid=1009 name="/usr/bin/evince" 
[   10.892613] type=1505 audit(1277813576.144:10):  operation="profile_load" pid=1009 name="/usr/bin/evince-previewer" 
[   10.895493] type=1505 audit(1277813576.144:11):  operation="profile_load" pid=1009 name="/usr/bin/evince-thumbnailer" 
[   11.038537] type=1505 audit(1277813576.289:12):  operation="profile_load" pid=1012 name="/usr/lib/cups/backend/cups-pdf" 
[   11.038904] type=1505 audit(1277813576.289:13):  operation="profile_load" pid=1012 name="/usr/sbin/cupsd" 
[   11.071164] type=1505 audit(1277813576.320:14):  operation="profile_load" pid=1013 name="/usr/sbin/tcpdump" 
[   19.520565] [drm] nouveau 0000:01:00.0: Allocating FIFO number 1 
[   19.521332] [drm] nouveau 0000:01:00.0: nouveau_channel_alloc: initialised FIFO 1 
[   37.535896] [drm:edid_is_valid] *ERROR* EDID checksum is invalid, remainder is 175 
[   37.535901] [drm:edid_is_valid] *ERROR* Raw EDID: 
[   37.535905] <3>00 ff ff ff ff ff ff 00 4d 10 d7 20 01 01 01 01  ........M.. .... 
[   37.535908] <3>04 0e 01 03 0e 22 1b 78 eb ff ff ff ff ff ff ff  .....".x........ 
[   37.535911] <3>ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff  ................ 
[   37.535914] <3>ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff  ................ 
[   37.535916] <3>ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff  ................ 
[   37.535919] <3>ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff  ................ 
[   37.535921] <3>ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff  ................ 
[   37.535924] <3>ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff  ................ 
[   37.535926] 
[   41.776029] end_request: I/O error, dev fd0, sector 0 
[   41.808027] end_request: I/O error, dev fd0, sector 0 
[   74.912140] Marking TSC unstable due to cpufreq changes 
[   74.916291] Switching to clocksource acpi_pm 
[  149.744160] usb 1-3: USB disconnect, address 4 
[  172.376391] hub 1-0:1.0: unable to enumerate USB device on port 3 
[  172.776027] usb 1-3: new high speed USB device using ehci_hcd and address 6 
[  172.913849] usb 1-3: configuration #1 chosen from 1 choice 
[  173.028043] usb 1-3: reset high speed USB device using ehci_hcd and address 6 
[  173.161601] usb 1-3: firmware: requesting isl3887usb 
[  173.177052] usb 1-3: (p54usb) cannot load firmware isl3887usb (-2)! 
[  173.177062] usb 1-3: firmware: requesting isl3887usb_bare 
[  173.185799] p54usb: probe of 1-3:1.0 failed with error -2 
[  174.956450] usb 1-3: USB disconnect, address 6 
[  175.228030] usb 1-3: new high speed USB device using ehci_hcd and address 7 
[  175.365887] usb 1-3: configuration #1 chosen from 1 choice 
[  175.480031] usb 1-3: reset high speed USB device using ehci_hcd and address 7 
[  175.613644] usb 1-3: firmware: requesting isl3887usb 
[  175.616591] usb 1-3: (p54usb) cannot load firmware isl3887usb (-2)! 
[  175.616601] usb 1-3: firmware: requesting isl3887usb_bare 
[  175.625240] p54usb: probe of 1-3:1.0 failed with error -2 
[  175.665432] usb 1-3: USB disconnect, address 7 
[  175.936070] usb 1-3: new high speed USB device using ehci_hcd and address 8 
[  176.072872] usb 1-3: configuration #1 chosen from 1 choice 
[  176.188068] usb 1-3: reset high speed USB device using ehci_hcd and address 8 
[  176.323645] usb 1-3: firmware: requesting isl3887usb 
[  176.344277] usb 1-3: (p54usb) cannot load firmware isl3887usb (-2)! 
[  176.344283] usb 1-3: firmware: requesting isl3887usb_bare 
[  176.350443] p54usb: probe of 1-3:1.0 failed with error -2 
[  180.657256] usb 1-2: USB disconnect, address 3 
[  185.536473] usb 1-3: USB disconnect, address 8 
[  187.236027] usb 1-2: new high speed USB device using ehci_hcd and address 9 
[  187.373749] usb 1-2: configuration #1 chosen from 1 choice 
[  187.488032] usb 1-2: reset high speed USB device using ehci_hcd and address 9 
[  187.621618] usb 1-2: firmware: requesting isl3887usb 
[  187.624598] usb 1-2: (p54usb) cannot load firmware isl3887usb (-2)! 
[  187.624608] usb 1-2: firmware: requesting isl3887usb_bare 
[  187.633380] p54usb: probe of 1-2:1.0 failed with error -2 
[  193.635951] usb 1-2: USB disconnect, address 9 
[  198.460025] usb 1-5: new high speed USB device using ehci_hcd and address 10 
[  198.597868] usb 1-5: configuration #1 chosen from 1 choice 
[  198.712033] usb 1-5: reset high speed USB device using ehci_hcd and address 10 
[  198.845610] usb 1-5: firmware: requesting isl3887usb 
[  198.848691] usb 1-5: (p54usb) cannot load firmware isl3887usb (-2)! 
[  198.848700] usb 1-5: firmware: requesting isl3887usb_bare 
[  198.857392] p54usb: probe of 1-5:1.0 failed with error -2 
[  216.106183] usb 1-5: USB disconnect, address 10 
[ 1964.400037] usb 1-2: new high speed USB device using ehci_hcd and address 11 
[ 1964.537961] usb 1-2: configuration #1 chosen from 1 choice 
[ 1964.652029] usb 1-2: reset high speed USB device using ehci_hcd and address 11 
[ 1964.785681] usb 1-2: firmware: requesting isl3887usb 
[ 1964.788641] usb 1-2: (p54usb) cannot load firmware isl3887usb (-2)! 
[ 1964.788651] usb 1-2: firmware: requesting isl3887usb_bare 
[ 1964.809721] p54usb: probe of 1-2:1.0 failed with error -2 

And for lsusb I got

> Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 
Bus 002 Device 002: ID 046d:c016 Logitech, Inc. M-UV69a/HP M-UV96 Optical Wheel Mouse 
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 
Bus 001 Device 012: ID 13fe:1d00 Kingston Technology Company Inc. DataTraveler 2.0 1GB/4GB Flash Drive / Patriot Xporter 4GB Flash Drive 
Bus 001 Device 011: ID 06b9:0121 Alcatel Telecom SpeedTouch 121g Wireless Dongle 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub 

???

---

### Post by okplayer02 on 2010-06-29
well i searched the forum here i came back with this answer reference this thread:

[http://ubuntuforums.org/showthread.php?t=1466023](http://ubuntuforums.org/showthread.php?t=1466023)



the poster instructed to install firmware that is nonfree


```
sudo apt-get install linux-firmware-nonfree
```

---

### Post by fbjoey on 2010-06-29
Yer i looked at that post already and it doesn't work. I think im going to downgrade it to 9.04.

---

### Post by okplayer02 on 2010-06-29
well i found another answer at debian 

[http://wiki.debian.org/prism54#p54usb](http://wiki.debian.org/prism54#p54usb)

take a look there seems its not installed automatically


reference this bug from ubuntu

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/549383](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/549383)


suggest you try the debian fix sees how it go for you

---

### Post by fbjoey on 2010-06-29
I don't really understand what ndiswrapper is.

---

### Post by okplayer02 on 2010-06-29
there are some possible solutions in the bug page some users tried other solutions have a look there also

---

### Post by okplayer02 on 2010-06-29
> **fbjoey said:**
> I don't really understand what ndiswrapper is.


look at my new post i edited it cause i seen another solution

---

### Post by fbjoey on 2010-06-29
Okay, thank you. I will try these later, I have work now, thank you.

---

### Post by fbjoey on 2010-06-29
I got it working. Cheers :D

---

### Post by okplayer02 on 2010-06-29
explain for the others what you did to get it working so they can know.

---

