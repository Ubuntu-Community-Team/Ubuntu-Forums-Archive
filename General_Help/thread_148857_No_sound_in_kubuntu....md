---
title: "No sound in kubuntu..."
date: 2006-03-22
forum: General Help
---

### Post by jehnx on 2006-03-22
I just installed the newest Kubuntu release, but cannot seem to get my sound to work correctly. I've got a USB 5.1 channel audio adapter by GWC model AA1500 (as found [here](http://www.gwctech.com/ebproductdetail.asp?id=88)), but haven't figured out a way to have ubuntu recognize it as being there. When it was installing, I heard a pop in my speakers, making me think that it was going to actually recognize the device, but after installation never heard another peep.

I also have found this site where folks are saying that "even on linux" my device works: [link](http://72.14.203.104/search?q=cache:cvYP2SZkolsJ:www.newegg.com/Product/CustRatingReview.asp%3FItem%3DN82E16829126101+gwc+5.1+usb+linux&hl=en&gl=us&ct=clnk&cd=1&client=safari)

Worth noting, when I start the computer up, every single time while ubuntu is loading modules it makes a sound in my speakers. I guess that means that it's just checking the USB port to see that something is there, but when I go to lsusb it doesn't show up as being a device that is recognized.

Thanks in advance for any of you guys' help!

---

### Post by Barrakketh on 2006-03-22
Post the output of 

```
cat /var/log/kern.log
```
and
```
dmesg
```

EDIT:

Also, try the following command (Warning: don't have your speaker turned up too loud):
```
cat /dev/urandom > /dev/audio
```
Do you hear any static?  Use Ctrl+C to stop it.

---

### Post by jehnx on 2006-03-22
I'm gonna cut this into three replies, since the output was so huge.

> Post the output of 

cat /var/log/kern.log

```

Mar 22 00:35:47 localhost kernel: [4294688.605000]   Type:   Direct-Access
                ANSI SCSI revision: 00
Mar 22 00:35:47 localhost kernel: [4294688.681000] Attached scsi removable disk
sdc at scsi2, channel 0, id 0, lun 1
Mar 22 00:35:47 localhost kernel: [4294688.722000]   Vendor: Generic   Model: US
B SM Reader     Rev: 1.02
Mar 22 00:35:47 localhost kernel: [4294688.722000]   Type:   Direct-Access
                ANSI SCSI revision: 00
Mar 22 00:35:47 localhost kernel: [4294688.738000] Attached scsi removable disk
sdd at scsi2, channel 0, id 0, lun 2
Mar 22 00:35:47 localhost kernel: [4294688.741000]   Vendor: Generic   Model: US
B MS Reader     Rev: 1.03
Mar 22 00:35:47 localhost kernel: [4294688.741000]   Type:   Direct-Access
                ANSI SCSI revision: 00
Mar 22 00:35:47 localhost kernel: [4294688.756000] Attached scsi removable disk
sde at scsi2, channel 0, id 0, lun 3
Mar 22 00:35:47 localhost kernel: [4294688.762000] usb-storage: device scan comp
lete
Mar 22 00:35:47 localhost kernel: [4294688.816000] Adding 3036244k swap on /dev/
sda5.  Priority:-1 extents:1
Mar 22 00:35:47 localhost kernel: [4294689.100000] EXT3 FS on sda3, internal jou
rnal
Mar 22 00:35:47 localhost kernel: [4294695.173000] parport: PnPBIOS parport dete
cted.
Mar 22 00:35:47 localhost kernel: [4294695.173000] parport0: PC-style at 0x378 (
0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
Mar 22 00:35:47 localhost kernel: [4294695.260000] lp0: using parport0 (interrup
t-driven).
Mar 22 00:35:47 localhost kernel: [4294695.294000] mice: PS/2 mouse device commo
n for all mice
Mar 22 00:35:47 localhost kernel: [4294695.373000] ieee1394: Initialized config
rom entry `ip1394'
Mar 22 00:35:47 localhost kernel: [4294695.377000] sbp2: $Rev: 1219 $ Ben Collin
s <bcollins@debian.org>
Mar 22 00:35:47 localhost kernel: [4294698.321000] device-mapper: 4.4.0-ioctl (2
005-01-12) initialised: [email]dm-devel@redhat.com[/email]
Mar 22 00:35:47 localhost kernel: [4294699.111000] cdrom: open failed.
Mar 22 00:35:47 localhost kernel: [4294699.115000] cdrom: open failed.
Mar 22 00:35:47 localhost kernel: [4294701.429000] Linux agpgart interface v0.10
1 (c) Dave Jones
Mar 22 00:35:47 localhost kernel: [4294701.437000] agpgart: Detected an Intel 94
5G Chipset.
Mar 22 00:35:47 localhost kernel: [4294701.469000] agpgart: AGP aperture is 256M
 @ 0x0
Mar 22 00:35:47 localhost kernel: [4294701.610000] pci_hotplug: PCI Hot Plug PCI
 Core version: 0.5
Mar 22 00:35:47 localhost kernel: [4294701.620000] shpchp: Standard Hot Plug PCI
 Controller Driver version: 0.4
Mar 22 00:35:47 localhost kernel: [4294701.777000] ACPI: PCI Interrupt 0000:00:1
b.0[A] -> GSI 16 (level, low) -> IRQ 16
Mar 22 00:35:47 localhost kernel: [4294701.777000] PCI: Setting latency timer of
 device 0000:00:1b.0 to 64
Mar 22 00:35:47 localhost kernel: [4294702.552000] hw_random hardware driver 1.0
.0 loaded
Mar 22 00:35:47 localhost kernel: [4294702.877000] ohci1394: $Rev: 1250 $ Ben Co
llins <bcollins@debian.org>
Mar 22 00:35:47 localhost kernel: [4294702.877000] ACPI: PCI Interrupt 0000:02:0
1.0[A] -> GSI 20 (level, low) -> IRQ 20
Mar 22 00:35:47 localhost kernel: [4294702.877000] PCI: Via IRQ fixup for 0000:0
2:01.0, from 255 to 4
Mar 22 00:35:47 localhost kernel: [4294702.934000] ohci1394: fw-host0: OHCI-1394
 1.0 (PCI): IRQ=[20]  MMIO=[fdeff000-fdeff7ff]  Max Packet=[2048]
Mar 22 00:35:47 localhost kernel: [4294704.201000] ieee1394: Host added: ID:BUS[
0-00:1023]  GUID[0011d8000063790c]
Mar 22 00:35:47 localhost kernel: [4294704.947000] usbcore: registered new drive
r snd-usb-audio
Mar 22 00:35:47 localhost kernel: [4294705.492000] Real Time Clock Driver v1.12
Mar 22 00:35:47 localhost kernel: [4294705.567000] input: PC Speaker
Mar 22 00:35:47 localhost kernel: [4294705.898000] ts: Compaq touchscreen protoc
ol output
Mar 22 00:35:47 localhost kernel: [4294707.362000] e100: eth0: e100_watchdog: li
nk up, 10Mbps, full-duplex
Mar 22 00:35:47 localhost kernel: [4294707.371000] NET: Registered protocol fami
ly 17
Mar 22 00:35:47 localhost kernel: [4294712.502000] NET: Registered protocol fami
ly 10
Mar 22 00:35:47 localhost kernel: [4294712.502000] Disabled Privacy Extensions o
n device c02eb280(lo)
Mar 22 00:35:47 localhost kernel: [4294712.502000] IPv6 over IPv4 tunneling driv
er
Mar 22 00:35:47 localhost kernel: [4294713.873000] ACPI: Power Button (FF) [PWRF
]
Mar 22 00:35:47 localhost kernel: [4294713.873000] ACPI: Power Button (CM) [PWRB
]
Mar 22 00:35:47 localhost kernel: [4294713.965000] ibm_acpi: ec object not found
Mar 22 00:35:50 localhost kernel: [4294718.528000] apm: BIOS version 1.2 Flags 0
x07 (Driver version 1.16ac)
Mar 22 00:35:50 localhost kernel: [4294718.528000] apm: overridden by ACPI.
Mar 22 00:35:55 localhost kernel: [4294722.949000] eth0: no IPv6 routers present
Mar 22 00:47:10 localhost kernel: [4295398.737000] apm: BIOS version 1.2 Flags 0
x07 (Driver version 1.16ac)
Mar 22 00:47:10 localhost kernel: [4295398.737000] apm: disabled on user request
.
Mar 22 00:47:13 localhost kernel: Kernel logging (proc) stopped.
Mar 22 00:47:13 localhost kernel: Kernel log daemon terminating.
Mar 22 00:48:41 localhost kernel: Inspecting /boot/System.map-2.6.12-10-386
Mar 22 00:48:42 localhost kernel: Loaded 29010 symbols from /boot/System.map-2.6
.12-10-386.
Mar 22 00:48:42 localhost kernel: Symbols match kernel version 2.6.12.
Mar 22 00:48:42 localhost kernel: No module symbols loaded - kernel modules not
enabled.
Mar 22 00:48:42 localhost kernel: terrupt routing
Mar 22 00:48:42 localhost kernel: [4294668.269000] ACPI: PCI Root Bridge [PCI0]
(0000:00)
Mar 22 00:48:42 localhost kernel: [4294668.269000] PCI: Probing PCI hardware (bu
s 00)
Mar 22 00:48:42 localhost kernel: [4294668.269000] ACPI: Assume root bridge [\_S
B_.PCI0] segment is 0
Mar 22 00:48:42 localhost kernel: [4294668.272000] PCI: Ignoring BAR0-3 of IDE c
ontroller 0000:00:1f.1
Mar 22 00:48:42 localhost kernel: [4294668.272000] Boot video device is 0000:01:
00.0
Mar 22 00:48:42 localhost kernel: [4294668.272000] PCI: Transparent bridge - 000
0:00:1e.0
Mar 22 00:48:42 localhost kernel: [4294668.290000] ACPI: PCI Interrupt Routing T
able [\_SB_.PCI0._PRT]
Mar 22 00:48:42 localhost kernel: [4294668.291000] ACPI: PCI Interrupt Routing T
able [\_SB_.PCI0.HUB0._PRT]
Mar 22 00:48:42 localhost kernel: [4294668.295000] ACPI: PCI Interrupt Link [LNK
A] (IRQs 3 4 *5 7 9 10 11 12 14 15)
Mar 22 00:48:42 localhost kernel: [4294668.295000] ACPI: PCI Interrupt Link [LNK
B] (IRQs 3 4 5 7 9 10 11 12 14 15) *0, disabled.
Mar 22 00:48:42 localhost kernel: [4294668.295000] ACPI: PCI Interrupt Link [LNK
C] (IRQs 3 4 5 7 9 10 11 12 14 15) *0, disabled.
Mar 22 00:48:42 localhost kernel: [4294668.296000] ACPI: PCI Interrupt Link [LNK
D] (IRQs 3 4 5 7 9 10 *11 12 14 15)
Mar 22 00:48:42 localhost kernel: [4294668.296000] ACPI: PCI Interrupt Link [LNK
E] (IRQs 3 4 5 7 9 *10 11 12 14 15)
Mar 22 00:48:42 localhost kernel: [4294668.297000] ACPI: PCI Interrupt Link [LNK
F] (IRQs 3 4 5 7 9 10 11 12 14 15) *0, disabled.
Mar 22 00:48:42 localhost kernel: [4294668.297000] ACPI: PCI Interrupt Link [LNK
0] (IRQs 3 4 5 7 9 10 11 12 14 15) *0, disabled.
Mar 22 00:48:42 localhost kernel: [4294668.297000] ACPI: PCI Interrupt Link [LNK
1] (IRQs 3 4 5 7 9 10 11 12 14 15) *0, disabled.
Mar 22 00:48:42 localhost kernel: [4294668.298000] Linux Plug and Play Support v
0.97 (c) Adam Belay
Mar 22 00:48:42 localhost kernel: [4294668.298000] pnp: PnP ACPI init
Mar 22 00:48:42 localhost kernel: [4294668.301000] pnp: PnP ACPI: found 11 devic
es
Mar 22 00:48:42 localhost kernel: [4294668.301000] PnPBIOS: Disabled by ACPI PNP
Mar 22 00:48:42 localhost kernel: [4294668.301000] PCI: Using ACPI for IRQ routi
ng
Mar 22 00:48:42 localhost kernel: [4294668.301000] PCI: If a device doesn't work
, try "pci=routeirq".  If it helps, post a report
Mar 22 00:48:42 localhost kernel: [4294668.322000] pnp: 00:07: ioport range 0x40
0-0x4bf could not be reserved
Mar 22 00:48:42 localhost kernel: [4294668.323000] audit: initializing netlink s
ocket (disabled)
Mar 22 00:48:42 localhost kernel: [4294668.323000] audit: initialized
Mar 22 00:48:42 localhost kernel: [4294668.323000] highmem bounce pool size: 64
pages
Mar 22 00:48:42 localhost kernel: [4294668.323000] VFS: Disk quotas dquot_6.5.1
Mar 22 00:48:42 localhost kernel: [4294668.323000] Dquot-cache hash table entrie
s: 1024 (order 0, 4096 bytes)
Mar 22 00:48:42 localhost kernel: [4294668.323000] devfs: 2004-01-31 Richard Goo
ch (rgooch@atnf.csiro.au)
Mar 22 00:48:42 localhost kernel: [4294668.323000] devfs: boot_options: 0x0
Mar 22 00:48:42 localhost kernel: [4294668.323000] Initializing Cryptographic AP
I
Mar 22 00:48:42 localhost kernel: [4294668.323000] ACPI: PCI Interrupt 0000:00:0
1.0[A] -> GSI 16 (level, low) -> IRQ 16
Mar 22 00:48:42 localhost kernel: [4294668.323000] PCI: Setting latency timer of
 device 0000:00:01.0 to 64
Mar 22 00:48:42 localhost kernel: [4294668.323000] assign_interrupt_mode Found M
SI capability
Mar 22 00:48:42 localhost kernel: [4294668.323000] Allocate Port Service[pcie00]
Mar 22 00:48:42 localhost kernel: [4294668.323000] Allocate Port Service[pcie03]
Mar 22 00:48:42 localhost kernel: [4294668.323000] isapnp: Scanning for PnP card
s...
Mar 22 00:48:42 localhost kernel: [4294668.674000] isapnp: No Plug & Play device
 found
Mar 22 00:48:42 localhost kernel: [4294668.694000] PNP: No PS/2 controller found
. Probing ports directly.
Mar 22 00:48:42 localhost kernel: [4294668.703000] serio: i8042 AUX port at 0x60
,0x64 irq 12
Mar 22 00:48:42 localhost kernel: [4294668.705000] serio: i8042 KBD port at 0x60
,0x64 irq 1
Mar 22 00:48:42 localhost kernel: [4294668.705000] Serial: 8250/16550 driver $Re
vision: 1.90 $ 54 ports, IRQ sharing enabled
Mar 22 00:48:42 localhost kernel: [4294668.707000] io scheduler noop registered
Mar 22 00:48:42 localhost kernel: [4294668.707000] io scheduler anticipatory reg
istered
Mar 22 00:48:42 localhost kernel: [4294668.707000] io scheduler deadline registe
red
Mar 22 00:48:42 localhost kernel: [4294668.707000] io scheduler cfq registered
Mar 22 00:48:42 localhost kernel: [4294668.708000] RAMDISK driver initialized: 1
6 RAM disks of 65536K size 1024 blocksize
Mar 22 00:48:42 localhost kernel: [4294668.710000] EISA: Probing bus 0 at eisa.0
Mar 22 00:48:42 localhost kernel: [4294668.710000] EISA: Detected 0 cards.
Mar 22 00:48:42 localhost kernel: [4294668.710000] NET: Registered protocol fami
ly 2
Mar 22 00:48:42 localhost kernel: [4294668.723000] IP: routing cache hash table
of 8192 buckets, 64Kbytes
Mar 22 00:48:42 localhost kernel: [4294668.723000] TCP established hash table en
tries: 131072 (order: 8, 1048576 bytes)
Mar 22 00:48:42 localhost kernel: [4294668.723000] TCP bind hash table entries:
65536 (order: 6, 262144 bytes)
Mar 22 00:48:42 localhost kernel: [4294668.723000] TCP: Hash tables configured (
established 131072 bind 65536)
Mar 22 00:48:42 localhost kernel: [4294668.723000] NET: Registered protocol fami
ly 8
Mar 22 00:48:42 localhost kernel: [4294668.723000] NET: Registered protocol fami
ly 20
Mar 22 00:48:42 localhost kernel: [4294668.725000] ACPI wakeup devices:
Mar 22 00:48:42 localhost kernel: [4294668.725000] PCI0 PEX0 PEX1 PEX2 PEX3 PEX4
 PEX5 HUB0 USB0 USB1 USB2 USB3 USBE AC97 AZAL
Mar 22 00:48:42 localhost kernel: [4294668.725000] ACPI: (supports S0 S1 S3 S4 S
5)
Mar 22 00:48:42 localhost kernel: [4294668.725000] Freeing unused kernel memory:
 224k freed
Mar 22 00:48:42 localhost kernel: [4294668.793000] input: AT Translated Set 2 ke
yboard on isa0060/serio0
Mar 22 00:48:42 localhost kernel: [4294668.806000] vga16fb: initializing
Mar 22 00:48:42 localhost kernel: [4294668.806000] vga16fb: mapped to 0xc00a0000
Mar 22 00:48:42 localhost kernel: [4294668.930000] Console: switching to colour
frame buffer device 80x30
Mar 22 00:48:42 localhost kernel: [4294668.930000] fb0: VGA16 VGA frame buffer d
evice
Mar 22 00:48:42 localhost kernel: [4294670.075000] Capability LSM initialized
Mar 22 00:48:42 localhost kernel: [4294670.085000] NET: Registered protocol fami
ly 1
Mar 22 00:48:42 localhost kernel: [4294670.100000] Uniform Multi-Platform E-IDE
driver Revision: 7.00alpha2
Mar 22 00:48:42 localhost kernel: [4294670.100000] ide: Assuming 33MHz system bu
s speed for PIO modes; override with idebus=xx
Mar 22 00:48:42 localhost kernel: [4294670.100000] ACPI: bus type ide registered
Mar 22 00:48:42 localhost kernel: [4294670.110000] SCSI subsystem initialized
Mar 22 00:48:42 localhost kernel: [4294670.111000] libata version 1.11 loaded.
Mar 22 00:48:42 localhost kernel: [4294670.112000] ata_piix version 1.03
Mar 22 00:48:42 localhost kernel: [4294670.112000] ACPI: PCI Interrupt 0000:00:1
f.2[B] -> GSI 19 (level, low) -> IRQ 19
Mar 22 00:48:42 localhost kernel: [4294670.112000] PCI: Setting latency timer of
 device 0000:00:1f.2 to 64
Mar 22 00:48:42 localhost kernel: [4294670.112000] ata1: SATA max UDMA/133 cmd 0
xFA00 ctl 0xF902 bmdma 0xF600 irq 19
Mar 22 00:48:42 localhost kernel: [4294670.112000] ata2: SATA max UDMA/133 cmd 0
xF800 ctl 0xF702 bmdma 0xF608 irq 19
Mar 22 00:48:42 localhost kernel: [4294670.266000] ata1: dev 0 cfg 49:2f00 82:70
69 83:7c01 84:4023 85:7069 86:3c01 87:4023 88:203f
Mar 22 00:48:42 localhost kernel: [4294670.266000] ata1: dev 0 ATA, max UDMA/100
, 488397168 sectors: lba48
Mar 22 00:48:42 localhost kernel: [4294670.266000] ata1: dev 0 configured for UD
MA/100
Mar 22 00:48:42 localhost kernel: [4294670.266000] scsi0 : ata_piix
Mar 22 00:48:42 localhost kernel: [4294670.427000] ATA: abnormal status 0x7F on
port 0xF807
Mar 22 00:48:42 localhost kernel: [4294670.427000] ata2: disabling port
Mar 22 00:48:42 localhost kernel: [4294670.427000] scsi1 : ata_piix
Mar 22 00:48:42 localhost kernel: [4294670.427000]   Vendor: ATA       Model: WD
C WD2500JS-60M  Rev: 10.0
Mar 22 00:48:42 localhost kernel: [4294670.427000]   Type:   Direct-Access
                ANSI SCSI revision: 05
Mar 22 00:48:42 localhost kernel: [4294670.433000] ICH7: IDE controller at PCI s
lot 0000:00:1f.1
Mar 22 00:48:42 localhost kernel: [4294670.434000] ACPI: PCI Interrupt 0000:00:1
f.1[A] -> GSI 18 (level, low) -> IRQ 18
Mar 22 00:48:42 localhost kernel: [4294670.434000] ICH7: chipset revision 1
Mar 22 00:48:42 localhost kernel: [4294670.434000] ICH7: not 100%% native mode:
will probe irqs later
Mar 22 00:48:42 localhost kernel: [4294670.434000]     ide0: BM-DMA at 0xfb00-0x
fb07, BIOS settings: hda:DMA, hdb:pio
Mar 22 00:48:42 localhost kernel: [4294670.434000] Probing IDE interface ide0...
Mar 22 00:48:42 localhost kernel: [4294671.105000] hda: HP DVD Writer 840b, ATAP
I CD/DVD-ROM drive
Mar 22 00:48:42 localhost kernel: [4294671.819000] hdb: IDE-DVD DROM6216, ATAPI
CD/DVD-ROM drive
Mar 22 00:48:42 localhost kernel: [4294671.870000] ide0 at 0x1f0-0x1f7,0x3f6 on
irq 14
Mar 22 00:48:42 localhost kernel: [4294671.870000] Probing IDE interface ide1...
Mar 22 00:48:42 localhost kernel: [4294672.383000] Probing IDE interface ide2...
Mar 22 00:48:42 localhost kernel: [4294672.895000] Probing IDE interface ide3...
Mar 22 00:48:42 localhost kernel: [4294673.407000] Probing IDE interface ide4...
Mar 22 00:48:42 localhost kernel: [4294673.919000] Probing IDE interface ide5...
Mar 22 00:48:42 localhost kernel: [4294674.437000] hda: ATAPI 48X DVD-ROM DVD-R-
RAM CD-R/RW drive, 2048kB Cache
Mar 22 00:48:42 localhost kernel: [4294674.437000] Uniform CD-ROM driver Revisio
n: 3.20
Mar 22 00:48:42 localhost kernel: [4294674.441000] hdb: ATAPI 40X DVD-ROM drive,
 512kB Cache
Mar 22 00:48:42 localhost kernel: [4294674.448000] SCSI device sda: 488397168 51
2-byte hdwr sectors (250059 MB)
Mar 22 00:48:42 localhost kernel: [4294674.448000] SCSI device sda: drive cache:
 write back
Mar 22 00:48:42 localhost kernel: [4294674.448000] SCSI device sda: 488397168 51
2-byte hdwr sectors (250059 MB)
Mar 22 00:48:42 localhost kernel: [4294674.448000] SCSI device sda: drive cache:
 write back
Mar 22 00:48:42 localhost kernel: [4294674.448000]  /dev/scsi/host0/bus0/target0
/lun0: p1 p2 p3 p4 < p5 >
Mar 22 00:48:42 localhost kernel: [4294674.498000] Attached scsi disk sda at scs
i0, channel 0, id 0, lun 0
Mar 22 00:48:42 localhost kernel: [4294674.892000] Attempting manual resume
Mar 22 00:48:42 localhost kernel: [4294674.892000] swsusp: Suspend partition has
 wrong signature?
Mar 22 00:48:42 localhost kernel: [4294674.919000] usbcore: registered new drive
r usbfs
Mar 22 00:48:42 localhost kernel: [4294674.919000] usbcore: registered new drive
r hub
Mar 22 00:48:42 localhost kernel: [4294674.920000] USB Universal Host Controller
 Interface driver v2.2
Mar 22 00:48:42 localhost kernel: [4294674.920000] ACPI: PCI Interrupt 0000:00:1
d.0[A] -> GSI 23 (level, low) -> IRQ 23
Mar 22 00:48:42 localhost kernel: [4294674.920000] PCI: Setting latency timer of
 device 0000:00:1d.0 to 64
Mar 22 00:48:42 localhost kernel: [4294674.920000] uhci_hcd 0000:00:1d.0: Intel
Corporation I/O Controller Hub UHCI USB #1
Mar 22 00:48:42 localhost kernel: [4294674.982000] uhci_hcd 0000:00:1d.0: new US
B bus registered, assigned bus number 1
Mar 22 00:48:42 localhost kernel: [4294674.982000] uhci_hcd 0000:00:1d.0: irq 23
, io base 0x0000ff00
Mar 22 00:48:42 localhost kernel: [4294674.982000] hub 1-0:1.0: USB hub found
Mar 22 00:48:42 localhost kernel: [4294674.982000] hub 1-0:1.0: 2 ports detected
Mar 22 00:48:42 localhost kernel: [4294674.985000] ACPI: PCI Interrupt 0000:00:1
d.1[B] -> GSI 19 (level, low) -> IRQ 19
Mar 22 00:48:42 localhost kernel: [4294674.985000] PCI: Setting latency timer of
 device 0000:00:1d.1 to 64
Mar 22 00:48:42 localhost kernel: [4294674.985000] uhci_hcd 0000:00:1d.1: Intel
Corporation I/O Controller Hub UHCI USB #2
Mar 22 00:48:42 localhost kernel: [4294675.047000] uhci_hcd 0000:00:1d.1: new US
B bus registered, assigned bus number 2
Mar 22 00:48:42 localhost kernel: [4294675.047000] uhci_hcd 0000:00:1d.1: irq 19
, io base 0x0000fe00
Mar 22 00:48:42 localhost kernel: [4294675.047000] hub 2-0:1.0: USB hub found
Mar 22 00:48:42 localhost kernel: [4294675.047000] hub 2-0:1.0: 2 ports detected
Mar 22 00:48:42 localhost kernel: [4294675.050000] ACPI: PCI Interrupt 0000:00:1
d.2[C] -> GSI 18 (level, low) -> IRQ 18
Mar 22 00:48:42 localhost kernel: [4294675.050000] PCI: Setting latency timer of
 device 0000:00:1d.2 to 64
Mar 22 00:48:42 localhost kernel: [4294675.050000] uhci_hcd 0000:00:1d.2: Intel
Corporation I/O Controller Hub UHCI USB #3
Mar 22 00:48:42 localhost kernel: [4294675.112000] uhci_hcd 0000:00:1d.2: new US
B bus registered, assigned bus number 3
Mar 22 00:48:42 localhost kernel: [4294675.112000] uhci_hcd 0000:00:1d.2: irq 18
, io base 0x0000fd00
Mar 22 00:48:42 localhost kernel: [4294675.112000] hub 3-0:1.0: USB hub found
Mar 22 00:48:42 localhost kernel: [4294675.112000] hub 3-0:1.0: 2 ports detected
Mar 22 00:48:42 localhost kernel: [4294675.115000] ACPI: PCI Interrupt 0000:00:1
d.3[D] -> GSI 16 (level, low) -> IRQ 16
Mar 22 00:48:42 localhost kernel: [4294675.115000] PCI: Setting latency timer of
 device 0000:00:1d.3 to 64
Mar 22 00:48:42 localhost kernel: [4294675.115000] uhci_hcd 0000:00:1d.3: Intel
Corporation I/O Controller Hub UHCI USB #4
Mar 22 00:48:42 localhost kernel: [4294675.151000] usb 1-1: new low speed USB de
vice using uhci_hcd and address 2
Mar 22 00:48:42 localhost kernel: [4294675.177000] uhci_hcd 0000:00:1d.3: new US
B bus registered, assigned bus number 4
Mar 22 00:48:42 localhost kernel: [4294675.177000] uhci_hcd 0000:00:1d.3: irq 16
, io base 0x0000fc00
Mar 22 00:48:42 localhost kernel: [4294675.177000] hub 4-0:1.0: USB hub found
Mar 22 00:48:42 localhost kernel: [4294675.177000] hub 4-0:1.0: 2 ports detected
Mar 22 00:48:42 localhost kernel: [4294675.207000] ACPI: PCI Interrupt 0000:00:1
d.7[A] -> GSI 23 (level, low) -> IRQ 23
Mar 22 00:48:42 localhost kernel: [4294675.207000] PCI: Setting latency timer of
 device 0000:00:1d.7 to 64
Mar 22 00:48:42 localhost kernel: [4294675.207000] ehci_hcd 0000:00:1d.7: Intel
Corporation I/O Controller Hub EHCI USB
Mar 22 00:48:42 localhost kernel: [4294675.459000] usb 2-1: new low speed USB de
vice using uhci_hcd and address 2
Mar 22 00:48:42 localhost kernel: [4294675.756000] usb 2-2: new full speed USB d
evice using uhci_hcd and address 3
Mar 22 00:48:42 localhost kernel: [4294676.009000] usb 4-1: new full speed USB d
evice using uhci_hcd and address 2
Mar 22 00:48:42 localhost kernel: [4294680.707000] ehci_hcd 0000:00:1d.7: BIOS h
andoff failed (104, 1010001)
Mar 22 00:48:42 localhost kernel: [4294680.707000] ehci_hcd 0000:00:1d.7: contin
uing after BIOS bug...
Mar 22 00:48:42 localhost kernel: [4294680.707000] ehci_hcd 0000:00:1d.7: new US
B bus registered, assigned bus number 5
Mar 22 00:48:42 localhost kernel: [4294680.707000] ehci_hcd 0000:00:1d.7: irq 23
, io mem 0xfdfff000
Mar 22 00:48:42 localhost kernel: [4294680.710000] PCI: cache line size of 128 i
s not supported by device 0000:00:1d.7
Mar 22 00:48:42 localhost kernel: [4294680.710000] ehci_hcd 0000:00:1d.7: USB 2.
0 initialized, EHCI 1.00, driver 10 Dec 2004
Mar 22 00:48:42 localhost kernel: [4294680.711000] hub 5-0:1.0: USB hub found
Mar 22 00:48:42 localhost kernel: [4294680.711000] hub 5-0:1.0: 8 ports detected
Mar 22 00:48:42 localhost kernel: [4294680.803000] e100: Intel(R) PRO/100 Networ
k Driver, 3.4.8-k2-NAPI
Mar 22 00:48:42 localhost kernel: [4294680.803000] e100: Copyright(c) 1999-2005
Intel Corporation
Mar 22 00:48:42 localhost kernel: [4294680.803000] ACPI: PCI Interrupt 0000:02:0
8.0[A] -> GSI 20 (level, low) -> IRQ 20
Mar 22 00:48:42 localhost kernel: [4294680.822000] e100: eth0: e100_probe: addr
0xfdefd000, irq 20, MAC addr 00:13:D4:D0:04:BA
Mar 22 00:48:42 localhost kernel: [4294681.364000] usb 1-1: USB disconnect, addr
ess 2
Mar 22 00:48:42 localhost kernel: [4294681.530000] usb 1-1: new low speed USB de
vice using uhci_hcd and address 3
Mar 22 00:48:42 localhost kernel: [4294681.672000] usb 2-1: USB disconnect, addr
ess 2
Mar 22 00:48:42 localhost kernel: [4294681.838000] usb 2-1: new low speed USB de
vice using uhci_hcd and address 4
Mar 22 00:48:42 localhost kernel: [4294681.969000] usb 2-2: USB disconnect, addr
ess 3
Mar 22 00:48:42 localhost kernel: [4294682.135000] usb 2-2: new full speed USB d
evice using uhci_hcd and address 5
Mar 22 00:48:42 localhost kernel: [4294682.222000] usb 4-1: USB disconnect, addr
ess 2
Mar 22 00:48:42 localhost kernel: [4294682.388000] usb 4-1: new full speed USB d
evice using uhci_hcd and address 3
Mar 22 00:48:42 localhost kernel: [4294682.838000] usbcore: registered new drive
r hiddev
Mar 22 00:48:42 localhost kernel: [4294682.857000] input: USB HID v1.10 Keyboard
 [Key Tronic Keytronic USB Keyboard] on usb-0000:00:1d.0-1
Mar 22 00:48:42 localhost kernel: [4294682.895000] input: USB HID v1.11 Mouse [M
icrosoft Microsoft Wireless Optical Mouse 1.0A] on usb-0000:00:1d.1-1
Mar 22 00:48:42 localhost kernel: [4294682.900000] input: USB HID v1.00 Device [
USB Audio] on usb-0000:00:1d.1-2
Mar 22 00:48:42 localhost kernel: [4294682.900000] usbcore: registered new drive
r usbhid
Mar 22 00:48:42 localhost kernel: [4294682.900000] drivers/usb/input/hid-core.c:
 v2.01:USB HID core driver
Mar 22 00:48:42 localhost kernel: [4294682.959000] Initializing USB Mass Storage
 driver...
Mar 22 00:48:42 localhost kernel: [4294682.961000] scsi2 : SCSI emulation for US
B Mass Storage devices
Mar 22 00:48:42 localhost kernel: [4294682.961000] usb-storage: device found at
3
Mar 22 00:48:42 localhost kernel: [4294682.961000] usb-storage: waiting for devi
ce to settle before scanning
Mar 22 00:48:42 localhost kernel: [4294682.961000] usbcore: registered new drive
r usb-storage
Mar 22 00:48:42 localhost kernel: [4294682.961000] USB Mass Storage support regi
stered.
Mar 22 00:48:42 localhost kernel: [4294683.646000] ACPI: Fan [FAN] (on)
Mar 22 00:48:42 localhost kernel: [4294683.648000] ACPI: CPU0 (power states: C1[
C1])
Mar 22 00:48:42 localhost kernel: [4294683.667000] ACPI: Thermal Zone [THRM] (40
 C)
Mar 22 00:48:42 localhost kernel: [4294683.907000] Attempting manual resume
Mar 22 00:48:42 localhost kernel: [4294683.907000] swsusp: Suspend partition has
 wrong signature?
Mar 22 00:48:42 localhost kernel: [4294683.918000] kjournald starting.  Commit i
nterval 5 seconds
Mar 22 00:48:42 localhost kernel: [4294683.918000] EXT3-fs: mounted filesystem w
ith ordered data mode.
Mar 22 00:48:42 localhost kernel: [4294684.807000] md: md driver 0.90.1 MAX_MD_D
EVS=256, MD_SB_DISKS=27

```

---

### Post by jehnx on 2006-03-22
Here is some more of that command:

```

Mar 22 00:48:42 localhost kernel: [4294687.965000]   Vendor: Generic   Model: US
B SD Reader     Rev: 1.00
Mar 22 00:48:42 localhost kernel: [4294687.965000]   Type:   Direct-Access
                ANSI SCSI revision: 00
Mar 22 00:48:42 localhost kernel: [4294687.980000] Attached scsi removable disk
sdb at scsi2, channel 0, id 0, lun 0
Mar 22 00:48:42 localhost kernel: [4294687.983000]   Vendor: Generic   Model: US
B CF Reader     Rev: 1.01
Mar 22 00:48:42 localhost kernel: [4294687.983000]   Type:   Direct-Access
                ANSI SCSI revision: 00
Mar 22 00:48:42 localhost kernel: [4294688.002000] Attached scsi removable disk
sdc at scsi2, channel 0, id 0, lun 1
Mar 22 00:48:42 localhost kernel: [4294688.006000]   Vendor: Generic   Model: US
B SM Reader     Rev: 1.02
Mar 22 00:48:42 localhost kernel: [4294688.006000]   Type:   Direct-Access
                ANSI SCSI revision: 00
Mar 22 00:48:42 localhost kernel: [4294688.021000] Attached scsi removable disk
sdd at scsi2, channel 0, id 0, lun 2
Mar 22 00:48:42 localhost kernel: [4294688.160000]   Vendor: Generic   Model: US
B MS Reader     Rev: 1.03
Mar 22 00:48:42 localhost kernel: [4294688.160000]   Type:   Direct-Access
                ANSI SCSI revision: 00
Mar 22 00:48:42 localhost kernel: [4294688.176000] Attached scsi removable disk
sde at scsi2, channel 0, id 0, lun 3
Mar 22 00:48:42 localhost kernel: [4294688.183000] usb-storage: device scan comp
lete
Mar 22 00:48:42 localhost kernel: [4294688.237000] Adding 3036244k swap on /dev/
sda5.  Priority:-1 extents:1
Mar 22 00:48:42 localhost kernel: [4294688.513000] EXT3 FS on sda3, internal jou
rnal
Mar 22 00:48:42 localhost kernel: [4294694.652000] parport: PnPBIOS parport dete
cted.
Mar 22 00:48:42 localhost kernel: [4294694.652000] parport0: PC-style at 0x378 (
0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
Mar 22 00:48:42 localhost kernel: [4294694.751000] lp0: using parport0 (interrup
t-driven).
Mar 22 00:48:42 localhost kernel: [4294694.790000] mice: PS/2 mouse device commo
n for all mice
Mar 22 00:48:42 localhost kernel: [4294694.843000] ieee1394: Initialized config
rom entry `ip1394'
Mar 22 00:48:42 localhost kernel: [4294694.848000] sbp2: $Rev: 1219 $ Ben Collin
s <bcollins@debian.org>
Mar 22 00:48:42 localhost kernel: [4294697.676000] device-mapper: 4.4.0-ioctl (2
005-01-12) initialised: [email]dm-devel@redhat.com[/email]
Mar 22 00:48:42 localhost kernel: [4294698.465000] cdrom: open failed.
Mar 22 00:48:42 localhost kernel: [4294698.470000] cdrom: open failed.
Mar 22 00:48:42 localhost kernel: [4294700.675000] Linux agpgart interface v0.10
1 (c) Dave Jones
Mar 22 00:48:42 localhost kernel: [4294700.682000] agpgart: Detected an Intel 94
5G Chipset.
Mar 22 00:48:42 localhost kernel: [4294700.714000] agpgart: AGP aperture is 256M
 @ 0x0
Mar 22 00:48:42 localhost kernel: [4294700.931000] pci_hotplug: PCI Hot Plug PCI
 Core version: 0.5
Mar 22 00:48:42 localhost kernel: [4294700.941000] shpchp: Standard Hot Plug PCI
 Controller Driver version: 0.4
Mar 22 00:48:42 localhost kernel: [4294701.098000] ACPI: PCI Interrupt 0000:00:1
b.0[A] -> GSI 16 (level, low) -> IRQ 16
Mar 22 00:48:42 localhost kernel: [4294701.098000] PCI: Setting latency timer of
 device 0000:00:1b.0 to 64
Mar 22 00:48:42 localhost kernel: [4294701.900000] hw_random hardware driver 1.0
.0 loaded
Mar 22 00:48:42 localhost kernel: [4294702.244000] ohci1394: $Rev: 1250 $ Ben Co
llins <bcollins@debian.org>
Mar 22 00:48:42 localhost kernel: [4294702.244000] ACPI: PCI Interrupt 0000:02:0
1.0[A] -> GSI 20 (level, low) -> IRQ 20
Mar 22 00:48:42 localhost kernel: [4294702.244000] PCI: Via IRQ fixup for 0000:0
2:01.0, from 255 to 4
Mar 22 00:48:42 localhost kernel: [4294702.300000] ohci1394: fw-host0: OHCI-1394
 1.0 (PCI): IRQ=[20]  MMIO=[fdeff000-fdeff7ff]  Max Packet=[2048]
Mar 22 00:48:42 localhost kernel: [4294703.567000] ieee1394: Host added: ID:BUS[
0-00:1023]  GUID[0011d8000063790c]
Mar 22 00:48:42 localhost kernel: [4294704.440000] usbcore: registered new drive
r snd-usb-audio
Mar 22 00:48:42 localhost kernel: [4294704.940000] Real Time Clock Driver v1.12
Mar 22 00:48:42 localhost kernel: [4294705.038000] input: PC Speaker
Mar 22 00:48:42 localhost kernel: [4294705.407000] ts: Compaq touchscreen protoc
ol output
Mar 22 00:48:42 localhost kernel: [4294706.858000] e100: eth0: e100_watchdog: li
nk up, 10Mbps, full-duplex
Mar 22 00:48:42 localhost kernel: [4294706.867000] NET: Registered protocol fami
ly 17
Mar 22 00:48:42 localhost kernel: [4294711.767000] NET: Registered protocol fami
ly 10
Mar 22 00:48:42 localhost kernel: [4294711.767000] Disabled Privacy Extensions o
n device c02eb280(lo)
Mar 22 00:48:42 localhost kernel: [4294711.768000] IPv6 over IPv4 tunneling driv
er
Mar 22 00:48:42 localhost kernel: [4294713.169000] ACPI: Power Button (FF) [PWRF
]
Mar 22 00:48:42 localhost kernel: [4294713.169000] ACPI: Power Button (CM) [PWRB
]
Mar 22 00:48:42 localhost kernel: [4294713.267000] ibm_acpi: ec object not found
Mar 22 00:48:45 localhost kernel: [4294718.022000] apm: BIOS version 1.2 Flags 0
x07 (Driver version 1.16ac)
Mar 22 00:48:45 localhost kernel: [4294718.022000] apm: overridden by ACPI.
Mar 22 00:48:50 localhost kernel: [4294722.579000] eth0: no IPv6 routers present
Mar 22 01:20:31 localhost kernel: [4296623.543000] cdrom: open failed.
Mar 22 01:20:31 localhost kernel: [4296623.583000] cdrom: open failed.
Mar 22 01:21:07 localhost kernel: [4296660.166000] ISO 9660 Extensions: Microsof
t Joliet Level 3
Mar 22 01:21:07 localhost kernel: [4296660.237000] ISO 9660 Extensions: RRIP_199
1A
Mar 22 01:31:26 localhost kernel: [4297279.134000] ISO 9660 Extensions: Microsof
t Joliet Level 3
Mar 22 01:31:26 localhost kernel: [4297279.326000] ISO 9660 Extensions: RRIP_199
1A
Mar 22 01:32:59 localhost kernel: [4297372.379000] ibm_acpi: ec object not found
Mar 22 01:33:03 localhost kernel: [4297375.760000] Bluetooth: Core ver 2.7
Mar 22 01:33:03 localhost kernel: [4297375.760000] NET: Registered protocol fami
ly 31
Mar 22 01:33:03 localhost kernel: [4297375.760000] Bluetooth: HCI device and con
nection manager initialized
Mar 22 01:33:03 localhost kernel: [4297375.760000] Bluetooth: HCI socket layer i
nitialized
Mar 22 01:33:03 localhost kernel: [4297375.780000] Bluetooth: L2CAP ver 2.7
Mar 22 01:33:03 localhost kernel: [4297375.780000] Bluetooth: L2CAP socket layer
 initialized
Mar 22 01:33:03 localhost kernel: [4297375.784000] Bluetooth: RFCOMM ver 1.5
Mar 22 01:33:03 localhost kernel: [4297375.784000] Bluetooth: RFCOMM socket laye
r initialized
Mar 22 01:33:03 localhost kernel: [4297375.784000] Bluetooth: RFCOMM TTY layer i
nitialized
Mar 22 01:50:54 localhost kernel: [4298446.725000] apm: BIOS version 1.2 Flags 0
x07 (Driver version 1.16ac)
Mar 22 01:50:54 localhost kernel: [4298446.725000] apm: disabled on user request
.
Mar 22 01:50:57 localhost kernel: Kernel logging (proc) stopped.
Mar 22 01:50:57 localhost kernel: Kernel log daemon terminating.
Mar 22 21:29:24 localhost kernel: Inspecting /boot/System.map-2.6.12-10-386
Mar 22 21:29:24 localhost kernel: Loaded 29010 symbols from /boot/System.map-2.6
.12-10-386.
Mar 22 21:29:24 localhost kernel: Symbols match kernel version 2.6.12.
Mar 22 21:29:24 localhost kernel: No module symbols loaded - kernel modules not
enabled.
Mar 22 21:29:24 localhost kernel: terrupt routing
Mar 22 21:29:24 localhost kernel: [4294672.074000] ACPI: PCI Root Bridge [PCI0]
(0000:00)
Mar 22 21:29:24 localhost kernel: [4294672.074000] PCI: Probing PCI hardware (bu
s 00)
Mar 22 21:29:24 localhost kernel: [4294672.074000] ACPI: Assume root bridge [\_S
B_.PCI0] segment is 0
Mar 22 21:29:24 localhost kernel: [4294672.077000] PCI: Ignoring BAR0-3 of IDE c
ontroller 0000:00:1f.1
Mar 22 21:29:24 localhost kernel: [4294672.077000] Boot video device is 0000:01:
00.0
Mar 22 21:29:24 localhost kernel: [4294672.077000] PCI: Transparent bridge - 000
0:00:1e.0
Mar 22 21:29:24 localhost kernel: [4294672.095000] ACPI: PCI Interrupt Routing T
able [\_SB_.PCI0._PRT]
Mar 22 21:29:24 localhost kernel: [4294672.096000] ACPI: PCI Interrupt Routing T
able [\_SB_.PCI0.HUB0._PRT]
Mar 22 21:29:24 localhost kernel: [4294672.100000] ACPI: PCI Interrupt Link [LNK
A] (IRQs 3 4 *5 7 9 10 11 12 14 15)
Mar 22 21:29:24 localhost kernel: [4294672.100000] ACPI: PCI Interrupt Link [LNK
B] (IRQs 3 4 5 7 9 10 11 12 14 15) *0, disabled.
Mar 22 21:29:24 localhost kernel: [4294672.100000] ACPI: PCI Interrupt Link [LNK
C] (IRQs 3 4 5 7 9 10 11 12 14 15) *0, disabled.
Mar 22 21:29:24 localhost kernel: [4294672.101000] ACPI: PCI Interrupt Link [LNK
D] (IRQs 3 4 5 7 9 10 *11 12 14 15)
Mar 22 21:29:24 localhost kernel: [4294672.101000] ACPI: PCI Interrupt Link [LNK
E] (IRQs 3 4 5 7 9 *10 11 12 14 15)
Mar 22 21:29:24 localhost kernel: [4294672.102000] ACPI: PCI Interrupt Link [LNK
F] (IRQs 3 4 5 7 9 10 11 12 14 15) *0, disabled.
Mar 22 21:29:24 localhost kernel: [4294672.102000] ACPI: PCI Interrupt Link [LNK
0] (IRQs 3 4 5 7 9 10 11 12 14 15) *0, disabled.
Mar 22 21:29:24 localhost kernel: [4294672.102000] ACPI: PCI Interrupt Link [LNK
1] (IRQs 3 4 5 7 9 10 11 12 14 15) *0, disabled.
Mar 22 21:29:24 localhost kernel: [4294672.103000] Linux Plug and Play Support v
0.97 (c) Adam Belay
Mar 22 21:29:24 localhost kernel: [4294672.103000] pnp: PnP ACPI init
Mar 22 21:29:24 localhost kernel: [4294672.106000] pnp: PnP ACPI: found 11 devic
es
Mar 22 21:29:24 localhost kernel: [4294672.106000] PnPBIOS: Disabled by ACPI PNP
Mar 22 21:29:24 localhost kernel: [4294672.106000] PCI: Using ACPI for IRQ routi
ng
Mar 22 21:29:24 localhost kernel: [4294672.106000] PCI: If a device doesn't work
, try "pci=routeirq".  If it helps, post a report
Mar 22 21:29:24 localhost kernel: [4294672.127000] pnp: 00:07: ioport range 0x40
0-0x4bf could not be reserved
Mar 22 21:29:24 localhost kernel: [4294672.128000] audit: initializing netlink s
ocket (disabled)
Mar 22 21:29:24 localhost kernel: [4294672.128000] audit: initialized
Mar 22 21:29:24 localhost kernel: [4294672.128000] highmem bounce pool size: 64
pages
Mar 22 21:29:24 localhost kernel: [4294672.128000] VFS: Disk quotas dquot_6.5.1
Mar 22 21:29:24 localhost kernel: [4294672.128000] Dquot-cache hash table entrie
s: 1024 (order 0, 4096 bytes)
Mar 22 21:29:24 localhost kernel: [4294672.128000] devfs: 2004-01-31 Richard Goo
ch (rgooch@atnf.csiro.au)
Mar 22 21:29:24 localhost kernel: [4294672.128000] devfs: boot_options: 0x0
Mar 22 21:29:24 localhost kernel: [4294672.128000] Initializing Cryptographic AP
I
Mar 22 21:29:24 localhost kernel: [4294672.128000] ACPI: PCI Interrupt 0000:00:0
1.0[A] -> GSI 16 (level, low) -> IRQ 16
Mar 22 21:29:24 localhost kernel: [4294672.128000] PCI: Setting latency timer of
 device 0000:00:01.0 to 64
Mar 22 21:29:24 localhost kernel: [4294672.128000] assign_interrupt_mode Found M
SI capability
Mar 22 21:29:24 localhost kernel: [4294672.128000] Allocate Port Service[pcie00]
Mar 22 21:29:24 localhost kernel: [4294672.128000] Allocate Port Service[pcie03]
Mar 22 21:29:24 localhost kernel: [4294672.128000] isapnp: Scanning for PnP card
s...
Mar 22 21:29:24 localhost kernel: [4294672.480000] isapnp: No Plug & Play device
 found
Mar 22 21:29:24 localhost kernel: [4294672.500000] PNP: No PS/2 controller found
. Probing ports directly.
Mar 22 21:29:24 localhost kernel: [4294672.509000] serio: i8042 AUX port at 0x60
,0x64 irq 12
Mar 22 21:29:24 localhost kernel: [4294672.510000] serio: i8042 KBD port at 0x60
,0x64 irq 1
Mar 22 21:29:24 localhost kernel: [4294672.510000] Serial: 8250/16550 driver $Re
vision: 1.90 $ 54 ports, IRQ sharing enabled
Mar 22 21:29:24 localhost kernel: [4294672.512000] io scheduler noop registered
Mar 22 21:29:24 localhost kernel: [4294672.512000] io scheduler anticipatory reg
istered
Mar 22 21:29:24 localhost kernel: [4294672.512000] io scheduler deadline registe
red
Mar 22 21:29:24 localhost kernel: [4294672.512000] io scheduler cfq registered
Mar 22 21:29:24 localhost kernel: [4294672.513000] RAMDISK driver initialized: 1
6 RAM disks of 65536K size 1024 blocksize
Mar 22 21:29:24 localhost kernel: [4294672.515000] EISA: Probing bus 0 at eisa.0
Mar 22 21:29:24 localhost kernel: [4294672.515000] EISA: Detected 0 cards.
Mar 22 21:29:24 localhost kernel: [4294672.515000] NET: Registered protocol fami
ly 2
Mar 22 21:29:24 localhost kernel: [4294672.527000] IP: routing cache hash table
of 8192 buckets, 64Kbytes
Mar 22 21:29:24 localhost kernel: [4294672.527000] TCP established hash table en
tries: 131072 (order: 8, 1048576 bytes)
Mar 22 21:29:24 localhost kernel: [4294672.527000] TCP bind hash table entries:
65536 (order: 6, 262144 bytes)
Mar 22 21:29:24 localhost kernel: [4294672.527000] TCP: Hash tables configured (
established 131072 bind 65536)
Mar 22 21:29:24 localhost kernel: [4294672.527000] NET: Registered protocol fami
ly 8
Mar 22 21:29:24 localhost kernel: [4294672.527000] NET: Registered protocol fami
ly 20
Mar 22 21:29:24 localhost kernel: [4294672.527000] ACPI wakeup devices:
Mar 22 21:29:24 localhost kernel: [4294672.527000] PCI0 PEX0 PEX1 PEX2 PEX3 PEX4
 PEX5 HUB0 USB0 USB1 USB2 USB3 USBE AC97 AZAL
Mar 22 21:29:24 localhost kernel: [4294672.528000] ACPI: (supports S0 S1 S3 S4 S
5)
Mar 22 21:29:24 localhost kernel: [4294672.528000] Freeing unused kernel memory:
 224k freed
Mar 22 21:29:24 localhost kernel: [4294672.598000] input: AT Translated Set 2 ke
yboard on isa0060/serio0
Mar 22 21:29:24 localhost kernel: [4294672.610000] vga16fb: initializing
Mar 22 21:29:24 localhost kernel: [4294672.610000] vga16fb: mapped to 0xc00a0000
Mar 22 21:29:24 localhost kernel: [4294672.734000] Console: switching to colour
frame buffer device 80x30
Mar 22 21:29:24 localhost kernel: [4294672.734000] fb0: VGA16 VGA frame buffer d
evice
Mar 22 21:29:24 localhost kernel: [4294673.879000] Capability LSM initialized
Mar 22 21:29:24 localhost kernel: [4294673.889000] NET: Registered protocol fami
ly 1
Mar 22 21:29:24 localhost kernel: [4294673.904000] Uniform Multi-Platform E-IDE
driver Revision: 7.00alpha2
Mar 22 21:29:24 localhost kernel: [4294673.904000] ide: Assuming 33MHz system bu
s speed for PIO modes; override with idebus=xx
Mar 22 21:29:24 localhost kernel: [4294673.904000] ACPI: bus type ide registered
Mar 22 21:29:24 localhost kernel: [4294673.913000] SCSI subsystem initialized
Mar 22 21:29:24 localhost kernel: [4294673.914000] libata version 1.11 loaded.
Mar 22 21:29:24 localhost kernel: [4294673.915000] ata_piix version 1.03
Mar 22 21:29:24 localhost kernel: [4294673.915000] ACPI: PCI Interrupt 0000:00:1
f.2[B] -> GSI 19 (level, low) -> IRQ 19
Mar 22 21:29:24 localhost kernel: [4294673.915000] PCI: Setting latency timer of
 device 0000:00:1f.2 to 64
Mar 22 21:29:24 localhost kernel: [4294673.915000] ata1: SATA max UDMA/133 cmd 0
xFA00 ctl 0xF902 bmdma 0xF600 irq 19
Mar 22 21:29:24 localhost kernel: [4294673.916000] ata2: SATA max UDMA/133 cmd 0
xF800 ctl 0xF702 bmdma 0xF608 irq 19
Mar 22 21:29:24 localhost kernel: [4294674.070000] ata1: dev 0 cfg 49:2f00 82:70
69 83:7c01 84:4023 85:7069 86:3c01 87:4023 88:203f
Mar 22 21:29:24 localhost kernel: [4294674.070000] ata1: dev 0 ATA, max UDMA/100
, 488397168 sectors: lba48
Mar 22 21:29:24 localhost kernel: [4294674.070000] ata1: dev 0 configured for UD
MA/100
Mar 22 21:29:24 localhost kernel: [4294674.070000] scsi0 : ata_piix
Mar 22 21:29:24 localhost kernel: [4294674.231000] ATA: abnormal status 0x7F on
port 0xF807
Mar 22 21:29:24 localhost kernel: [4294674.231000] ata2: disabling port
Mar 22 21:29:24 localhost kernel: [4294674.231000] scsi1 : ata_piix
Mar 22 21:29:24 localhost kernel: [4294674.231000]   Vendor: ATA       Model: WD
C WD2500JS-60M  Rev: 10.0
Mar 22 21:29:24 localhost kernel: [4294674.231000]   Type:   Direct-Access
                ANSI SCSI revision: 05
Mar 22 21:29:24 localhost kernel: [4294674.237000] ICH7: IDE controller at PCI s
lot 0000:00:1f.1
Mar 22 21:29:24 localhost kernel: [4294674.237000] ACPI: PCI Interrupt 0000:00:1
f.1[A] -> GSI 18 (level, low) -> IRQ 18
Mar 22 21:29:24 localhost kernel: [4294674.237000] ICH7: chipset revision 1
Mar 22 21:29:24 localhost kernel: [4294674.237000] ICH7: not 100%% native mode:
will probe irqs later
Mar 22 21:29:24 localhost kernel: [4294674.238000]     ide0: BM-DMA at 0xfb00-0x
fb07, BIOS settings: hda:DMA, hdb:pio
Mar 22 21:29:24 localhost kernel: [4294674.238000] Probing IDE interface ide0...
Mar 22 21:29:24 localhost kernel: [4294674.909000] hda: HP DVD Writer 840b, ATAP
I CD/DVD-ROM drive
Mar 22 21:29:24 localhost kernel: [4294675.623000] hdb: IDE-DVD DROM6216, ATAPI
CD/DVD-ROM drive
Mar 22 21:29:24 localhost kernel: [4294675.674000] ide0 at 0x1f0-0x1f7,0x3f6 on
irq 14
Mar 22 21:29:24 localhost kernel: [4294675.674000] Probing IDE interface ide1...
Mar 22 21:29:24 localhost kernel: [4294676.187000] Probing IDE interface ide2...
Mar 22 21:29:24 localhost kernel: [4294676.699000] Probing IDE interface ide3...
Mar 22 21:29:24 localhost kernel: [4294677.211000] Probing IDE interface ide4...
Mar 22 21:29:24 localhost kernel: [4294677.723000] Probing IDE interface ide5...
Mar 22 21:29:24 localhost kernel: [4294678.241000] hda: ATAPI 48X DVD-ROM DVD-R-
RAM CD-R/RW drive, 2048kB Cache
Mar 22 21:29:24 localhost kernel: [4294678.241000] Uniform CD-ROM driver Revisio
n: 3.20
Mar 22 21:29:24 localhost kernel: [4294678.245000] hdb: ATAPI 40X DVD-ROM drive,
 512kB Cache
Mar 22 21:29:24 localhost kernel: [4294678.252000] SCSI device sda: 488397168 51
2-byte hdwr sectors (250059 MB)
Mar 22 21:29:24 localhost kernel: [4294678.252000] SCSI device sda: drive cache:
 write back
Mar 22 21:29:24 localhost kernel: [4294678.252000] SCSI device sda: 488397168 51
2-byte hdwr sectors (250059 MB)
Mar 22 21:29:24 localhost kernel: [4294678.252000] SCSI device sda: drive cache:
 write back
Mar 22 21:29:24 localhost kernel: [4294678.252000]  /dev/scsi/host0/bus0/target0
/lun0: p1 p2 p3 p4 < p5 >
Mar 22 21:29:24 localhost kernel: [4294678.311000] Attached scsi disk sda at scs
i0, channel 0, id 0, lun 0
Mar 22 21:29:24 localhost kernel: [4294678.705000] Attempting manual resume
Mar 22 21:29:24 localhost kernel: [4294678.705000] swsusp: Suspend partition has
 wrong signature?
Mar 22 21:29:24 localhost kernel: [4294678.733000] usbcore: registered new drive
r usbfs
Mar 22 21:29:24 localhost kernel: [4294678.733000] usbcore: registered new drive
r hub
Mar 22 21:29:24 localhost kernel: [4294678.734000] USB Universal Host Controller
 Interface driver v2.2
Mar 22 21:29:24 localhost kernel: [4294678.734000] ACPI: PCI Interrupt 0000:00:1
d.0[A] -> GSI 23 (level, low) -> IRQ 23
Mar 22 21:29:24 localhost kernel: [4294678.734000] PCI: Setting latency timer of
 device 0000:00:1d.0 to 64
Mar 22 21:29:24 localhost kernel: [4294678.734000] uhci_hcd 0000:00:1d.0: Intel
Corporation I/O Controller Hub UHCI USB #1
Mar 22 21:29:24 localhost kernel: [4294678.796000] uhci_hcd 0000:00:1d.0: new US
B bus registered, assigned bus number 1
Mar 22 21:29:24 localhost kernel: [4294678.796000] uhci_hcd 0000:00:1d.0: irq 23
, io base 0x0000ff00
Mar 22 21:29:24 localhost kernel: [4294678.796000] hub 1-0:1.0: USB hub found
Mar 22 21:29:24 localhost kernel: [4294678.796000] hub 1-0:1.0: 2 ports detected
Mar 22 21:29:24 localhost kernel: [4294678.799000] ACPI: PCI Interrupt 0000:00:1
d.1[B] -> GSI 19 (level, low) -> IRQ 19
Mar 22 21:29:24 localhost kernel: [4294678.799000] PCI: Setting latency timer of
 device 0000:00:1d.1 to 64
Mar 22 21:29:24 localhost kernel: [4294678.799000] uhci_hcd 0000:00:1d.1: Intel
Corporation I/O Controller Hub UHCI USB #2
Mar 22 21:29:24 localhost kernel: [4294678.861000] uhci_hcd 0000:00:1d.1: new US
B bus registered, assigned bus number 2
Mar 22 21:29:24 localhost kernel: [4294678.861000] uhci_hcd 0000:00:1d.1: irq 19
, io base 0x0000fe00
Mar 22 21:29:24 localhost kernel: [4294678.861000] hub 2-0:1.0: USB hub found
Mar 22 21:29:24 localhost kernel: [4294678.861000] hub 2-0:1.0: 2 ports detected
Mar 22 21:29:24 localhost kernel: [4294678.864000] ACPI: PCI Interrupt 0000:00:1
d.2[C] -> GSI 18 (level, low) -> IRQ 18
Mar 22 21:29:24 localhost kernel: [4294678.864000] PCI: Setting latency timer of
 device 0000:00:1d.2 to 64
Mar 22 21:29:24 localhost kernel: [4294678.864000] uhci_hcd 0000:00:1d.2: Intel
Corporation I/O Controller Hub UHCI USB #3
Mar 22 21:29:24 localhost kernel: [4294678.926000] uhci_hcd 0000:00:1d.2: new US
B bus registered, assigned bus number 3
Mar 22 21:29:24 localhost kernel: [4294678.926000] uhci_hcd 0000:00:1d.2: irq 18
, io base 0x0000fd00
Mar 22 21:29:24 localhost kernel: [4294678.926000] hub 3-0:1.0: USB hub found
Mar 22 21:29:24 localhost kernel: [4294678.926000] hub 3-0:1.0: 2 ports detected
Mar 22 21:29:24 localhost kernel: [4294678.929000] ACPI: PCI Interrupt 0000:00:1
d.3[D] -> GSI 16 (level, low) -> IRQ 16
Mar 22 21:29:24 localhost kernel: [4294678.929000] PCI: Setting latency timer of
 device 0000:00:1d.3 to 64
Mar 22 21:29:24 localhost kernel: [4294678.929000] uhci_hcd 0000:00:1d.3: Intel
Corporation I/O Controller Hub UHCI USB #4
Mar 22 21:29:24 localhost kernel: [4294678.965000] usb 1-1: new low speed USB de
vice using uhci_hcd and address 2
Mar 22 21:29:24 localhost kernel: [4294678.991000] uhci_hcd 0000:00:1d.3: new US
B bus registered, assigned bus number 4
Mar 22 21:29:24 localhost kernel: [4294678.991000] uhci_hcd 0000:00:1d.3: irq 16
, io base 0x0000fc00
Mar 22 21:29:24 localhost kernel: [4294678.991000] hub 4-0:1.0: USB hub found
Mar 22 21:29:24 localhost kernel: [4294678.991000] hub 4-0:1.0: 2 ports detected
Mar 22 21:29:24 localhost kernel: [4294679.021000] ACPI: PCI Interrupt 0000:00:1
d.7[A] -> GSI 23 (level, low) -> IRQ 23
Mar 22 21:29:24 localhost kernel: [4294679.021000] PCI: Setting latency timer of
 device 0000:00:1d.7 to 64
Mar 22 21:29:24 localhost kernel: [4294679.021000] ehci_hcd 0000:00:1d.7: Intel
Corporation I/O Controller Hub EHCI USB
Mar 22 21:29:24 localhost kernel: [4294679.273000] usb 2-1: new low speed USB de
vice using uhci_hcd and address 2
Mar 22 21:29:24 localhost kernel: [4294679.570000] usb 2-2: new full speed USB d
evice using uhci_hcd and address 3
Mar 22 21:29:24 localhost kernel: [4294679.823000] usb 4-1: new full speed USB d
evice using uhci_hcd and address 2
Mar 22 21:29:24 localhost kernel: [4294684.521000] ehci_hcd 0000:00:1d.7: BIOS h
andoff failed (104, 1010001)
Mar 22 21:29:24 localhost kernel: [4294684.521000] ehci_hcd 0000:00:1d.7: contin
uing after BIOS bug...
Mar 22 21:29:24 localhost kernel: [4294684.521000] ehci_hcd 0000:00:1d.7: new US
B bus registered, assigned bus number 5
Mar 22 21:29:24 localhost kernel: [4294684.521000] ehci_hcd 0000:00:1d.7: irq 23
, io mem 0xfdfff000
Mar 22 21:29:24 localhost kernel: [4294684.524000] PCI: cache line size of 128 i
s not supported by device 0000:00:1d.7
Mar 22 21:29:24 localhost kernel: [4294684.524000] ehci_hcd 0000:00:1d.7: USB 2.
0 initialized, EHCI 1.00, driver 10 Dec 2004
Mar 22 21:29:24 localhost kernel: [4294684.525000] hub 5-0:1.0: USB hub found
Mar 22 21:29:24 localhost kernel: [4294684.525000] hub 5-0:1.0: 8 ports detected
Mar 22 21:29:24 localhost kernel: [4294684.617000] e100: Intel(R) PRO/100 Networ
k Driver, 3.4.8-k2-NAPI
Mar 22 21:29:24 localhost kernel: [4294684.617000] e100: Copyright(c) 1999-2005
Intel Corporation
Mar 22 21:29:24 localhost kernel: [4294684.617000] ACPI: PCI Interrupt 0000:02:0
8.0[A] -> GSI 20 (level, low) -> IRQ 20
Mar 22 21:29:24 localhost kernel: [4294684.636000] e100: eth0: e100_probe: addr
0xfdefd000, irq 20, MAC addr 00:13:D4:D0:04:BA
Mar 22 21:29:24 localhost kernel: [4294685.178000] usb 1-1: USB disconnect, addr
ess 2
Mar 22 21:29:24 localhost kernel: [4294685.344000] usb 1-1: new low speed USB de
vice using uhci_hcd and address 3
Mar 22 21:29:24 localhost kernel: [4294685.486000] usb 2-1: USB disconnect, addr
ess 2
Mar 22 21:29:24 localhost kernel: [4294685.652000] usb 2-1: new low speed USB de
vice using uhci_hcd and address 4
Mar 22 21:29:24 localhost kernel: [4294685.783000] usb 2-2: USB disconnect, addr
ess 3
Mar 22 21:29:24 localhost kernel: [4294685.949000] usb 2-2: new full speed USB d
evice using uhci_hcd and address 5
Mar 22 21:29:24 localhost kernel: [4294686.036000] usb 4-1: USB disconnect, addr
ess 2
Mar 22 21:29:24 localhost kernel: [4294686.202000] usb 4-1: new full speed USB d
evice using uhci_hcd and address 3
Mar 22 21:29:24 localhost kernel: [4294686.652000] usbcore: registered new drive
r hiddev
Mar 22 21:29:24 localhost kernel: [4294686.671000] input: USB HID v1.10 Keyboard
 [Key Tronic Keytronic USB Keyboard] on usb-0000:00:1d.0-1

```

---

### Post by jehnx on 2006-03-22
And, the last bit:

```
Mar 22 21:29:24 localhost kernel: [4294686.709000] input: USB HID v1.11 Mouse [M
icrosoft Microsoft Wireless Optical Mouse 1.0A] on usb-0000:00:1d.1-1
Mar 22 21:29:24 localhost kernel: [4294686.714000] input: USB HID v1.00 Device [
USB Audio] on usb-0000:00:1d.1-2
Mar 22 21:29:24 localhost kernel: [4294686.714000] usbcore: registered new drive
r usbhid
Mar 22 21:29:24 localhost kernel: [4294686.714000] drivers/usb/input/hid-core.c:
 v2.01:USB HID core driver
Mar 22 21:29:24 localhost kernel: [4294686.773000] Initializing USB Mass Storage
 driver...
Mar 22 21:29:24 localhost kernel: [4294686.775000] scsi2 : SCSI emulation for US
B Mass Storage devices
Mar 22 21:29:24 localhost kernel: [4294686.775000] usb-storage: device found at
3
Mar 22 21:29:24 localhost kernel: [4294686.775000] usb-storage: waiting for devi
ce to settle before scanning
Mar 22 21:29:24 localhost kernel: [4294686.775000] usbcore: registered new drive
r usb-storage
Mar 22 21:29:24 localhost kernel: [4294686.775000] USB Mass Storage support regi
stered.
Mar 22 21:29:24 localhost kernel: [4294687.458000] ACPI: Fan [FAN] (on)
Mar 22 21:29:24 localhost kernel: [4294687.461000] ACPI: CPU0 (power states: C1[
C1])
Mar 22 21:29:24 localhost kernel: [4294687.479000] ACPI: Thermal Zone [THRM] (40
 C)
Mar 22 21:29:24 localhost kernel: [4294687.729000] Attempting manual resume
Mar 22 21:29:24 localhost kernel: [4294687.729000] swsusp: Suspend partition has
 wrong signature?
Mar 22 21:29:24 localhost kernel: [4294687.739000] kjournald starting.  Commit i
nterval 5 seconds
Mar 22 21:29:24 localhost kernel: [4294687.739000] EXT3-fs: mounted filesystem w
ith ordered data mode.
Mar 22 21:29:24 localhost kernel: [4294688.662000] md: md driver 0.90.1 MAX_MD_D
EVS=256, MD_SB_DISKS=27
Mar 22 21:29:24 localhost kernel: [4294691.778000]   Vendor: Generic   Model: US
B SD Reader     Rev: 1.00
Mar 22 21:29:24 localhost kernel: [4294691.778000]   Type:   Direct-Access
                ANSI SCSI revision: 00
Mar 22 21:29:24 localhost kernel: [4294691.814000] Attached scsi removable disk
sdb at scsi2, channel 0, id 0, lun 0
Mar 22 21:29:24 localhost kernel: [4294691.817000]   Vendor: Generic   Model: US
B CF Reader     Rev: 1.01
Mar 22 21:29:24 localhost kernel: [4294691.817000]   Type:   Direct-Access
                ANSI SCSI revision: 00
Mar 22 21:29:24 localhost kernel: [4294691.833000] Attached scsi removable disk
sdc at scsi2, channel 0, id 0, lun 1
Mar 22 21:29:24 localhost kernel: [4294691.836000]   Vendor: Generic   Model: US
B SM Reader     Rev: 1.02
Mar 22 21:29:24 localhost kernel: [4294691.836000]   Type:   Direct-Access
                ANSI SCSI revision: 00
Mar 22 21:29:24 localhost kernel: [4294691.852000] Attached scsi removable disk
sdd at scsi2, channel 0, id 0, lun 2
Mar 22 21:29:24 localhost kernel: [4294691.855000]   Vendor: Generic   Model: US
B MS Reader     Rev: 1.03
Mar 22 21:29:24 localhost kernel: [4294691.855000]   Type:   Direct-Access
                ANSI SCSI revision: 00
Mar 22 21:29:24 localhost kernel: [4294691.873000] Attached scsi removable disk
sde at scsi2, channel 0, id 0, lun 3
Mar 22 21:29:24 localhost kernel: [4294691.874000] usb-storage: device scan comp
lete
Mar 22 21:29:24 localhost kernel: [4294692.117000] Adding 3036244k swap on /dev/
sda5.  Priority:-1 extents:1
Mar 22 21:29:24 localhost kernel: [4294692.393000] EXT3 FS on sda3, internal jou
rnal
Mar 22 21:29:24 localhost kernel: [4294698.996000] parport: PnPBIOS parport dete
cted.
Mar 22 21:29:24 localhost kernel: [4294698.996000] parport0: PC-style at 0x378 (
0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
Mar 22 21:29:24 localhost kernel: [4294699.083000] lp0: using parport0 (interrup
t-driven).
Mar 22 21:29:24 localhost kernel: [4294699.118000] mice: PS/2 mouse device commo
n for all mice
Mar 22 21:29:24 localhost kernel: [4294699.183000] ieee1394: Initialized config
rom entry `ip1394'
Mar 22 21:29:24 localhost kernel: [4294699.189000] sbp2: $Rev: 1219 $ Ben Collin
s <bcollins@debian.org>
Mar 22 21:29:24 localhost kernel: [4294702.487000] device-mapper: 4.4.0-ioctl (2
005-01-12) initialised: [email]dm-devel@redhat.com[/email]
Mar 22 21:29:24 localhost kernel: [4294703.387000] cdrom: open failed.
Mar 22 21:29:24 localhost kernel: [4294703.392000] cdrom: open failed.
Mar 22 21:29:24 localhost kernel: [4294705.554000] Linux agpgart interface v0.10
1 (c) Dave Jones
Mar 22 21:29:24 localhost kernel: [4294705.561000] agpgart: Detected an Intel 94
5G Chipset.
Mar 22 21:29:24 localhost kernel: [4294705.587000] agpgart: AGP aperture is 256M
 @ 0x0
Mar 22 21:29:24 localhost kernel: [4294705.785000] pci_hotplug: PCI Hot Plug PCI
 Core version: 0.5
Mar 22 21:29:24 localhost kernel: [4294705.796000] shpchp: Standard Hot Plug PCI
 Controller Driver version: 0.4
Mar 22 21:29:24 localhost kernel: [4294705.954000] ACPI: PCI Interrupt 0000:00:1
b.0[A] -> GSI 16 (level, low) -> IRQ 16
Mar 22 21:29:24 localhost kernel: [4294705.954000] PCI: Setting latency timer of
 device 0000:00:1b.0 to 64
Mar 22 21:29:24 localhost kernel: [4294706.757000] hw_random hardware driver 1.0
.0 loaded
Mar 22 21:29:24 localhost kernel: [4294707.081000] ohci1394: $Rev: 1250 $ Ben Co
llins <bcollins@debian.org>
Mar 22 21:29:24 localhost kernel: [4294707.081000] ACPI: PCI Interrupt 0000:02:0
1.0[A] -> GSI 20 (level, low) -> IRQ 20
Mar 22 21:29:24 localhost kernel: [4294707.081000] PCI: Via IRQ fixup for 0000:0
2:01.0, from 255 to 4
Mar 22 21:29:24 localhost kernel: [4294707.138000] ohci1394: fw-host0: OHCI-1394
 1.0 (PCI): IRQ=[20]  MMIO=[fdeff000-fdeff7ff]  Max Packet=[2048]
Mar 22 21:29:24 localhost kernel: [4294708.405000] ieee1394: Host added: ID:BUS[
0-00:1023]  GUID[0011d8000063790c]
Mar 22 21:29:24 localhost kernel: [4294709.245000] usbcore: registered new drive
r snd-usb-audio
Mar 22 21:29:24 localhost kernel: [4294709.660000] Real Time Clock Driver v1.12
Mar 22 21:29:24 localhost kernel: [4294709.703000] input: PC Speaker
Mar 22 21:29:24 localhost kernel: [4294710.064000] ts: Compaq touchscreen protoc
ol output
Mar 22 21:29:24 localhost kernel: [4294711.521000] e100: eth0: e100_watchdog: li
nk up, 10Mbps, full-duplex
Mar 22 21:29:24 localhost kernel: [4294711.530000] NET: Registered protocol fami
ly 17
Mar 22 21:29:24 localhost kernel: [4294716.764000] NET: Registered protocol fami
ly 10
Mar 22 21:29:24 localhost kernel: [4294716.764000] Disabled Privacy Extensions o
n device c02eb280(lo)
Mar 22 21:29:24 localhost kernel: [4294716.764000] IPv6 over IPv4 tunneling driv
er
Mar 22 21:29:24 localhost kernel: [4294718.149000] ACPI: Power Button (FF) [PWRF
]
Mar 22 21:29:24 localhost kernel: [4294718.149000] ACPI: Power Button (CM) [PWRB                                                                           ]
Mar 22 21:29:24 localhost kernel: [4294718.247000] ibm_acpi: ec object not found
Mar 22 21:29:28 localhost kernel: [4294722.960000] apm: BIOS version 1.2 Flags 0                                                                           x07 (Driver version 1.16ac)
Mar 22 21:29:28 localhost kernel: [4294722.960000] apm: overridden by ACPI.
Mar 22 21:29:29 localhost kernel: [4294723.865000] Bluetooth: Core ver 2.7
Mar 22 21:29:29 localhost kernel: [4294723.865000] NET: Registered protocol fami                                                                           ly 31
Mar 22 21:29:29 localhost kernel: [4294723.865000] Bluetooth: HCI device and con                                                                           nection manager initialized
Mar 22 21:29:29 localhost kernel: [4294723.865000] Bluetooth: HCI socket layer i                                                                           nitialized
Mar 22 21:29:29 localhost kernel: [4294723.904000] Bluetooth: L2CAP ver 2.7
Mar 22 21:29:29 localhost kernel: [4294723.904000] Bluetooth: L2CAP socket layer                                                                            initialized
Mar 22 21:29:29 localhost kernel: [4294723.951000] Bluetooth: RFCOMM ver 1.5
Mar 22 21:29:29 localhost kernel: [4294723.951000] Bluetooth: RFCOMM socket laye                                                                           r initialized
Mar 22 21:29:29 localhost kernel: [4294723.951000] Bluetooth: RFCOMM TTY layer i                                                                           nitialized
Mar 22 21:29:32 localhost kernel: [4294727.039000] eth0: no IPv6 routers present

```


> dmesg
```

7 9 10 11 12 14 15) *0, disabled.
[4294672.100000] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 7 9 10 11 12 14 15) *0, disabled.
[4294672.101000] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 7 9 10 *11 12 14 15)
[4294672.101000] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 7 9 *10 11 12 14 15)
[4294672.102000] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 7 9 10 11 12 14 15) *0, disabled.
[4294672.102000] ACPI: PCI Interrupt Link [LNK0] (IRQs 3 4 5 7 9 10 11 12 14 15) *0, disabled.
[4294672.102000] ACPI: PCI Interrupt Link [LNK1] (IRQs 3 4 5 7 9 10 11 12 14 15) *0, disabled.
[4294672.103000] Linux Plug and Play Support v0.97 (c) Adam Belay
[4294672.103000] pnp: PnP ACPI init
[4294672.106000] pnp: PnP ACPI: found 11 devices
[4294672.106000] PnPBIOS: Disabled by ACPI PNP
[4294672.106000] PCI: Using ACPI for IRQ routing
[4294672.106000] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[4294672.127000] pnp: 00:07: ioport range 0x400-0x4bf could not be reserved
[4294672.128000] audit: initializing netlink socket (disabled)
[4294672.128000] audit: initialized
[4294672.128000] highmem bounce pool size: 64 pages
[4294672.128000] VFS: Disk quotas dquot_6.5.1
[4294672.128000] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[4294672.128000] devfs: 2004-01-31 Richard Gooch (rgooch@atnf.csiro.au)
[4294672.128000] devfs: boot_options: 0x0
[4294672.128000] Initializing Cryptographic API
[4294672.128000] ACPI: PCI Interrupt 0000:00:01.0[A] -> GSI 16 (level, low) -> IRQ 16
[4294672.128000] PCI: Setting latency timer of device 0000:00:01.0 to 64
[4294672.128000] assign_interrupt_mode Found MSI capability
[4294672.128000] Allocate Port Service[pcie00]
[4294672.128000] Allocate Port Service[pcie03]
[4294672.128000] isapnp: Scanning for PnP cards...
[4294672.480000] isapnp: No Plug & Play device found
[4294672.500000] PNP: No PS/2 controller found. Probing ports directly.
[4294672.509000] serio: i8042 AUX port at 0x60,0x64 irq 12
[4294672.510000] serio: i8042 KBD port at 0x60,0x64 irq 1
[4294672.510000] Serial: 8250/16550 driver $Revision: 1.90 $ 54 ports, IRQ sharing enabled
[4294672.512000] io scheduler noop registered
[4294672.512000] io scheduler anticipatory registered
[4294672.512000] io scheduler deadline registered
[4294672.512000] io scheduler cfq registered
[4294672.513000] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[4294672.515000] EISA: Probing bus 0 at eisa.0
[4294672.515000] EISA: Detected 0 cards.
[4294672.515000] NET: Registered protocol family 2
[4294672.527000] IP: routing cache hash table of 8192 buckets, 64Kbytes
[4294672.527000] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[4294672.527000] TCP bind hash table entries: 65536 (order: 6, 262144 bytes)
[4294672.527000] TCP: Hash tables configured (established 131072 bind 65536)
[4294672.527000] NET: Registered protocol family 8
[4294672.527000] NET: Registered protocol family 20
[4294672.527000] ACPI wakeup devices:
[4294672.527000] PCI0 PEX0 PEX1 PEX2 PEX3 PEX4 PEX5 HUB0 USB0 USB1 USB2 USB3 USBE AC97 AZAL
[4294672.528000] ACPI: (supports S0 S1 S3 S4 S5)
[4294672.528000] Freeing unused kernel memory: 224k freed
[4294672.598000] input: AT Translated Set 2 keyboard on isa0060/serio0
[4294672.610000] vga16fb: initializing
[4294672.610000] vga16fb: mapped to 0xc00a0000
[4294672.734000] Console: switching to colour frame buffer device 80x30
[4294672.734000] fb0: VGA16 VGA frame buffer device
[4294673.879000] Capability LSM initialized
[4294673.889000] NET: Registered protocol family 1
[4294673.904000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[4294673.904000] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[4294673.904000] ACPI: bus type ide registered
[4294673.913000] SCSI subsystem initialized
[4294673.914000] libata version 1.11 loaded.
[4294673.915000] ata_piix version 1.03
[4294673.915000] ACPI: PCI Interrupt 0000:00:1f.2[B] -> GSI 19 (level, low) -> IRQ 19
[4294673.915000] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[4294673.915000] ata1: SATA max UDMA/133 cmd 0xFA00 ctl 0xF902 bmdma 0xF600 irq 19
[4294673.916000] ata2: SATA max UDMA/133 cmd 0xF800 ctl 0xF702 bmdma 0xF608 irq 19
[4294674.070000] ata1: dev 0 cfg 49:2f00 82:7069 83:7c01 84:4023 85:7069 86:3c01 87:4023 88:203f
[4294674.070000] ata1: dev 0 ATA, max UDMA/100, 488397168 sectors: lba48
[4294674.070000] ata1: dev 0 configured for UDMA/100
[4294674.070000] scsi0 : ata_piix
[4294674.231000] ATA: abnormal status 0x7F on port 0xF807
[4294674.231000] ata2: disabling port
[4294674.231000] scsi1 : ata_piix
[4294674.231000]   Vendor: ATA       Model: WDC WD2500JS-60M  Rev: 10.0
[4294674.231000]   Type:   Direct-Access                      ANSI SCSI revision: 05
[4294674.237000] ICH7: IDE controller at PCI slot 0000:00:1f.1
[4294674.237000] ACPI: PCI Interrupt 0000:00:1f.1[A] -> GSI 18 (level, low) -> IRQ 18
[4294674.237000] ICH7: chipset revision 1
[4294674.237000] ICH7: not 100% native mode: will probe irqs later
[4294674.238000]     ide0: BM-DMA at 0xfb00-0xfb07, BIOS settings: hda:DMA, hdb:pio
[4294674.238000] Probing IDE interface ide0...
[4294674.909000] hda: HP DVD Writer 840b, ATAPI CD/DVD-ROM drive
[4294675.623000] hdb: IDE-DVD DROM6216, ATAPI CD/DVD-ROM drive
[4294675.674000] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[4294675.674000] Probing IDE interface ide1...
[4294676.187000] Probing IDE interface ide2...
[4294676.699000] Probing IDE interface ide3...
[4294677.211000] Probing IDE interface ide4...
[4294677.723000] Probing IDE interface ide5...
[4294678.241000] hda: ATAPI 48X DVD-ROM DVD-R-RAM CD-R/RW drive, 2048kB Cache
[4294678.241000] Uniform CD-ROM driver Revision: 3.20
[4294678.245000] hdb: ATAPI 40X DVD-ROM drive, 512kB Cache
[4294678.252000] SCSI device sda: 488397168 512-byte hdwr sectors (250059 MB)
[4294678.252000] SCSI device sda: drive cache: write back
[4294678.252000] SCSI device sda: 488397168 512-byte hdwr sectors (250059 MB)
[4294678.252000] SCSI device sda: drive cache: write back
[4294678.252000]  /dev/scsi/host0/bus0/target0/lun0: p1 p2 p3 p4 < p5 >
[4294678.311000] Attached scsi disk sda at scsi0, channel 0, id 0, lun 0
[4294678.705000] Attempting manual resume
[4294678.705000] swsusp: Suspend partition has wrong signature?
[4294678.733000] usbcore: registered new driver usbfs
[4294678.733000] usbcore: registered new driver hub
[4294678.734000] USB Universal Host Controller Interface driver v2.2
[4294678.734000] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 23 (level, low) -> IRQ 23
[4294678.734000] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[4294678.734000] uhci_hcd 0000:00:1d.0: Intel Corporation I/O Controller Hub UHCI USB #1
[4294678.796000] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[4294678.796000] uhci_hcd 0000:00:1d.0: irq 23, io base 0x0000ff00
[4294678.796000] hub 1-0:1.0: USB hub found
[4294678.796000] hub 1-0:1.0: 2 ports detected
[4294678.799000] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 19 (level, low) -> IRQ 19
[4294678.799000] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[4294678.799000] uhci_hcd 0000:00:1d.1: Intel Corporation I/O Controller Hub UHCI USB #2
[4294678.861000] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
[4294678.861000] uhci_hcd 0000:00:1d.1: irq 19, io base 0x0000fe00
[4294678.861000] hub 2-0:1.0: USB hub found
[4294678.861000] hub 2-0:1.0: 2 ports detected
[4294678.864000] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 18
[4294678.864000] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[4294678.864000] uhci_hcd 0000:00:1d.2: Intel Corporation I/O Controller Hub UHCI USB #3
[4294678.926000] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
[4294678.926000] uhci_hcd 0000:00:1d.2: irq 18, io base 0x0000fd00
[4294678.926000] hub 3-0:1.0: USB hub found
[4294678.926000] hub 3-0:1.0: 2 ports detected
[4294678.929000] ACPI: PCI Interrupt 0000:00:1d.3[D] -> GSI 16 (level, low) -> IRQ 16
[4294678.929000] PCI: Setting latency timer of device 0000:00:1d.3 to 64
[4294678.929000] uhci_hcd 0000:00:1d.3: Intel Corporation I/O Controller Hub UHCI USB #4
[4294678.965000] usb 1-1: new low speed USB device using uhci_hcd and address 2
[4294678.991000] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 4
[4294678.991000] uhci_hcd 0000:00:1d.3: irq 16, io base 0x0000fc00
[4294678.991000] hub 4-0:1.0: USB hub found
[4294678.991000] hub 4-0:1.0: 2 ports detected
[4294679.021000] ACPI: PCI Interrupt 0000:00:1d.7[A] -> GSI 23 (level, low) -> IRQ 23
[4294679.021000] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[4294679.021000] ehci_hcd 0000:00:1d.7: Intel Corporation I/O Controller Hub EHCI USB
[4294679.273000] usb 2-1: new low speed USB device using uhci_hcd and address 2
[4294679.570000] usb 2-2: new full speed USB device using uhci_hcd and address 3
[4294679.823000] usb 4-1: new full speed USB device using uhci_hcd and address 2
[4294684.521000] ehci_hcd 0000:00:1d.7: BIOS handoff failed (104, 1010001)
[4294684.521000] ehci_hcd 0000:00:1d.7: continuing after BIOS bug...
[4294684.521000] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 5
[4294684.521000] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xfdfff000
[4294684.524000] PCI: cache line size of 128 is not supported by device 0000:00:1d.7
[4294684.524000] ehci_hcd 0000:00:1d.7: USB 2.0 initialized, EHCI 1.00, driver 10 Dec 2004
[4294684.525000] hub 5-0:1.0: USB hub found
[4294684.525000] hub 5-0:1.0: 8 ports detected
[4294684.617000] e100: Intel(R) PRO/100 Network Driver, 3.4.8-k2-NAPI
[4294684.617000] e100: Copyright(c) 1999-2005 Intel Corporation
[4294684.617000] ACPI: PCI Interrupt 0000:02:08.0[A] -> GSI 20 (level, low) -> IRQ 20
[4294684.636000] e100: eth0: e100_probe: addr 0xfdefd000, irq 20, MAC addr 00:13:D4:D0:04:BA
[4294685.178000] usb 1-1: USB disconnect, address 2
[4294685.344000] usb 1-1: new low speed USB device using uhci_hcd and address 3
[4294685.486000] usb 2-1: USB disconnect, address 2
[4294685.652000] usb 2-1: new low speed USB device using uhci_hcd and address 4
[4294685.783000] usb 2-2: USB disconnect, address 3
[4294685.949000] usb 2-2: new full speed USB device using uhci_hcd and address 5
[4294686.036000] usb 4-1: USB disconnect, address 2
[4294686.202000] usb 4-1: new full speed USB device using uhci_hcd and address 3
[4294686.652000] usbcore: registered new driver hiddev
[4294686.671000] input: USB HID v1.10 Keyboard [Key Tronic Keytronic USB Keyboard] on usb-0000:00:1d.0-1
[4294686.709000] input: USB HID v1.11 Mouse [Microsoft Microsoft Wireless Optical Mouse 1.0A] on usb-0000:00:1d.1-1
[4294686.714000] input: USB HID v1.00 Device [USB Audio] on usb-0000:00:1d.1-2
[4294686.714000] usbcore: registered new driver usbhid
[4294686.714000] drivers/usb/input/hid-core.c: v2.01:USB HID core driver
[4294686.773000] Initializing USB Mass Storage driver...
[4294686.775000] scsi2 : SCSI emulation for USB Mass Storage devices
[4294686.775000] usb-storage: device found at 3
[4294686.775000] usb-storage: waiting for device to settle before scanning
[4294686.775000] usbcore: registered new driver usb-storage
[4294686.775000] USB Mass Storage support registered.
[4294687.458000] ACPI: Fan [FAN] (on)
[4294687.461000] ACPI: CPU0 (power states: C1[C1])
[4294687.479000] ACPI: Thermal Zone [THRM] (40 C)
[4294687.729000] Attempting manual resume
[4294687.729000] swsusp: Suspend partition has wrong signature?
[4294687.739000] kjournald starting.  Commit interval 5 seconds
[4294687.739000] EXT3-fs: mounted filesystem with ordered data mode.
[4294688.662000] md: md driver 0.90.1 MAX_MD_DEVS=256, MD_SB_DISKS=27
[4294691.778000]   Vendor: Generic   Model: USB SD Reader     Rev: 1.00
[4294691.778000]   Type:   Direct-Access                      ANSI SCSI revision: 00
[4294691.814000] Attached scsi removable disk sdb at scsi2, channel 0, id 0, lun 0
[4294691.817000]   Vendor: Generic   Model: USB CF Reader     Rev: 1.01
[4294691.817000]   Type:   Direct-Access                      ANSI SCSI revision: 00
[4294691.833000] Attached scsi removable disk sdc at scsi2, channel 0, id 0, lun 1
[4294691.836000]   Vendor: Generic   Model: USB SM Reader     Rev: 1.02
[4294691.836000]   Type:   Direct-Access                      ANSI SCSI revision: 00
[4294691.852000] Attached scsi removable disk sdd at scsi2, channel 0, id 0, lun 2
[4294691.855000]   Vendor: Generic   Model: USB MS Reader     Rev: 1.03
[4294691.855000]   Type:   Direct-Access                      ANSI SCSI revision: 00
[4294691.873000] Attached scsi removable disk sde at scsi2, channel 0, id 0, lun 3
[4294691.874000] usb-storage: device scan complete
[4294692.117000] Adding 3036244k swap on /dev/sda5.  Priority:-1 extents:1
[4294692.393000] EXT3 FS on sda3, internal journal
[4294698.996000] parport: PnPBIOS parport detected.
[4294698.996000] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
[4294699.083000] lp0: using parport0 (interrupt-driven).
[4294699.118000] mice: PS/2 mouse device common for all mice
[4294699.183000] ieee1394: Initialized config rom entry `ip1394'
[4294699.189000] sbp2: $Rev: 1219 $ Ben Collins <bcollins@debian.org>
[4294702.487000] device-mapper: 4.4.0-ioctl (2005-01-12) initialised: [email]dm-devel@redhat.com[/email]
[4294703.387000] cdrom: open failed.
[4294703.392000] cdrom: open failed.
[4294705.554000] Linux agpgart interface v0.101 (c) Dave Jones
[4294705.561000] agpgart: Detected an Intel 945G Chipset.
[4294705.587000] agpgart: AGP aperture is 256M @ 0x0
[4294705.785000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[4294705.796000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[4294705.954000] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 16 (level, low) -> IRQ 16
[4294705.954000] PCI: Setting latency timer of device 0000:00:1b.0 to 64
[4294706.757000] hw_random hardware driver 1.0.0 loaded
[4294707.081000] ohci1394: $Rev: 1250 $ Ben Collins <bcollins@debian.org>
[4294707.081000] ACPI: PCI Interrupt 0000:02:01.0[A] -> GSI 20 (level, low) -> IRQ 20
[4294707.081000] PCI: Via IRQ fixup for 0000:02:01.0, from 255 to 4
[4294707.138000] ohci1394: fw-host0: OHCI-1394 1.0 (PCI): IRQ=[20]  MMIO=[fdeff000-fdeff7ff]  Max Packet=[2048]
[4294708.405000] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[0011d8000063790c]
[4294709.245000] usbcore: registered new driver snd-usb-audio
[4294709.660000] Real Time Clock Driver v1.12
[4294709.703000] input: PC Speaker
[4294710.064000] ts: Compaq touchscreen protocol output
[4294711.521000] e100: eth0: e100_watchdog: link up, 10Mbps, full-duplex
[4294711.530000] NET: Registered protocol family 17
[4294716.764000] NET: Registered protocol family 10
[4294716.764000] Disabled Privacy Extensions on device c02eb280(lo)
[4294716.764000] IPv6 over IPv4 tunneling driver
[4294718.149000] ACPI: Power Button (FF) [PWRF]
[4294718.149000] ACPI: Power Button (CM) [PWRB]
[4294718.247000] ibm_acpi: ec object not found
[4294722.960000] apm: BIOS version 1.2 Flags 0x07 (Driver version 1.16ac)
[4294722.960000] apm: overridden by ACPI.
[4294723.865000] Bluetooth: Core ver 2.7
[4294723.865000] NET: Registered protocol family 31
[4294723.865000] Bluetooth: HCI device and connection manager initialized
[4294723.865000] Bluetooth: HCI socket layer initialized
[4294723.904000] Bluetooth: L2CAP ver 2.7
[4294723.904000] Bluetooth: L2CAP socket layer initialized
[4294723.951000] Bluetooth: RFCOMM ver 1.5
[4294723.951000] Bluetooth: RFCOMM socket layer initialized
[4294723.951000] Bluetooth: RFCOMM TTY layer initialized
[4294727.039000] eth0: no IPv6 routers present

```

> cat /dev/urandom > /dev/audio

I didn't hear anything when I did this.

Thanks SO much for your help!!!

---

### Post by Barrakketh on 2006-03-22
Since I overlooked that part, what does lsusb and lsmod output?

And FYI, you can put long pieces of text in between code tags to disable the smilies and make it not take up so much room :)

---

### Post by jehnx on 2006-03-22
lsusb gives this:

```

Bus 005 Device 001: ID 0000:0000
Bus 004 Device 003: ID 058f:9360 Alcor Micro Corp.
Bus 004 Device 001: ID 0000:0000
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 005: ID 0c45:167f Microdia
Bus 002 Device 004: ID 045e:008c Microsoft Corp. Wireless Intellimouse Explorer 2.0
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 003: ID 03f9:0100 KeyTronic Corp.
Bus 001 Device 001: ID 0000:0000
```

lsmod gives this:

```

Module                  Size  Used by
rfcomm                 34972  0
l2cap                  22404  5 rfcomm
bluetooth              43012  4 rfcomm,l2cap
speedstep_lib           4228  0
cpufreq_userspace       4444  0
cpufreq_stats           5124  0
freq_table              4484  1 cpufreq_stats
cpufreq_powersave       1920  0
cpufreq_ondemand        5916  0
cpufreq_conservative     6820  0
video                  16004  0
tc1100_wmi              6916  0
sony_acpi               5516  0
pcc_acpi               11392  0
hotkey                  9508  0
dev_acpi               11396  0
i2c_acpi_ec             5760  0
i2c_core               19728  1 i2c_acpi_ec
button                  6672  0
battery                 9604  0
container               4608  0
ac                      4996  0
ipv6                  217408  6
af_packet              20232  2
tsdev                   7616  0
pcspkr                  3652  0
rtc                    11832  0
snd_usb_audio          68160  1
snd_usb_lib            13824  1 snd_usb_audio
snd_rawmidi            22816  1 snd_usb_lib
snd_seq_device          8204  1 snd_rawmidi
snd_hwdep               8608  1 snd_usb_audio
ohci1394               30644  0
tpm_nsc                 6528  0
tpm                     9504  1 tpm_nsc
hw_random               5268  0
snd_hda_intel          15872  1
snd_hda_codec          72064  1 snd_hda_intel
snd_pcm_oss            46368  0
snd_mixer_oss          16128  3 snd_pcm_oss
snd_pcm                78344  4 snd_usb_audio,snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_timer              21764  1 snd_pcm
snd                    48644  10 snd_usb_audio,snd_rawmidi,snd_seq_device,snd_hwdep,snd_hda_intel,snd_hda_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore               9184  3 snd
snd_page_alloc         10120  2 snd_hda_intel,snd_pcm
shpchp                 80612  0
pci_hotplug            24628  1 shpchp
intel_agp              21276  1
agpgart                32328  1 intel_agp
dm_mod                 50364  1
evdev                   9088  0
sr_mod                 15652  0
sbp2                   21128  0
ieee1394               90936  2 ohci1394,sbp2
psmouse                26116  0
mousedev               10912  1
parport_pc             31812  1
lp                     11460  0
parport                32072  2 parport_pc,lp
md                     40656  0
ext3                  115976  1
jbd                    48536  1 ext3
thermal                13192  0
processor              23100  1 thermal
fan                     4740  0
usb_storage            64704  0
usbhid                 30688  0
e100                   32768  0
mii                     5248  1 e100
ehci_hcd               29448  0
uhci_hcd               28048  0
usbcore               104316  7 snd_usb_audio,snd_usb_lib,usb_storage,usbhid,ehci_hcd,uhci_hcd
sd_mod                 17424  3
ide_cd                 36996  0
cdrom                  33952  2 sr_mod,ide_cd
ide_generic             1664  0
ata_piix                9476  6
libata                 47876  1 ata_piix
scsi_mod              124872  5 sr_mod,sbp2,usb_storage,sd_mod,libata
piix                    9476  1
ide_core              125268  4 usb_storage,ide_cd,ide_generic,piix
unix                   24624  314
vesafb                  8088  0
capability              5000  0
commoncap               6784  1 capability
vga16fb                12232  1
vgastate                8320  1 vga16fb
softcursor              2432  2 vesafb,vga16fb
cfbimgblt               2944  2 vesafb,vga16fb
cfbfillrect             3840  2 vesafb,vga16fb
cfbcopyarea             4480  2 vesafb,vga16fb
fbcon                  34176  72
tileblit                2560  1 fbcon
font                    8448  1 fbcon
bitblit                 5248  1 fbcon
```

Also, I'm heading back up to edit those... sorry for the inconvenience!

---

### Post by Barrakketh on 2006-03-22
Can you open KMix and make sure that all of your speakers are unmuted and the volume is turned up?  It appears that the drivers remain loaded, and do you know if you own any devices by Microdia?  I think that might be your sound card.

---

### Post by jehnx on 2006-03-22
Actually, I think Microdia is one of my slots in the front of my computer that holds my Flash memory and whatnot.  My sound adapter is made by GWC, model AA1500.  I also have on-board sound in the computer, but the reason I'm using this external adapter is because that on-board card has been broken, I believe.

In KMix, it was set to read from "Intel" so I think that is my motherboard.  I changed it over to USB Audio, which it recognized, under "output," and checked that both green lights are on on the Speaker settings.  They're both also turned all the way up.

When I go to the tab called "Switches" and turn on Auto Gain Control, I can hear static.

Any ideas?

---

### Post by jehnx on 2006-03-22
As an addendum, if I go to that Switches area, turn on the Auto Gain Control, and unmute my mic, it makes very loud noise through my speaker (that is controllable via the normal kmix speaker settings).

---

### Post by Barrakketh on 2006-03-22
[QUOTE=jehnx]Actually, I think Microdia is one of my slots in the front of my computer that holds my Flash memory and whatnot.[/quote]
I looked it up, and your flash card reader appears to be made by Alcor Micro.
> My sound adapter is made by GWC, model AA1500.  I also have on-board sound in the computer, but the reason I'm using this external adapter is because that on-board card has been broken, I believe.
Is your onboard sound disabled in the BIOS?  (alternatively, via a jumper on your mother board).

> In KMix, it was set to read from "Intel" so I think that is my motherboard.  I changed it over to USB Audio, which it recognized, under "output," and checked that both green lights are on on the Speaker settings.  They're both also turned all the way up.
Make sure that's set right, make sure the volume for "Master" and "PCM" is turned up (and not muted).  I'm not sure whether you'd need to mute/unmute each speaker individually or not.  Consider toggling the Surround Jack Mode in Switches.

---

### Post by jehnx on 2006-03-22
See, there are four different things on the front: SmartMedia/xD, MMC/SD, CompactFlash I/II, and Memory Stick/PRO.  I was thinking that maybe one of those was made by that company you pointed out, because it looks like that company doesn't make my sound adapter.

Onboard sound is not disabled in the BIOS, so I'm going to reboot right now and attempt to do that.  I'll post back in a few minutes with whether there is a change or not.

"Master" and "PCM" are not present in my Output tab in KMix, actually.   Only two options, "Speaker" and another "Speaker."

Thanks so much for all of your help thus far, Barrakketh.

---

### Post by jehnx on 2006-03-22
I heard a sound through the speakers when I just logged in, so that's great.  :)  How can I test that they are still working?  I loaded up GAIM but am not hearing anything through there, and don't have any music downloaded on here.  Is there a way to test?

EDIT:

Doing cat /dev/urandom > /dev/audio now makes a lot of static happen, yep, so I'd say that means it's working?  Or is there another way I can test to see if real sound will come through (besides the log-in "dum dum dum dum dum" sound?

---

### Post by Barrakketh on 2006-03-22
[QUOTE=jehnx]Doing cat /dev/urandom > /dev/audio now makes a lot of static happen, yep, so I'd say that means it's working?  Or is there another way I can test to see if real sound will come through (besides the log-in "dum dum dum dum dum" sound?[/QUOTE]

Load up a track in amaroK?  Like the login sound:
/usr/share/sounds/KDE_Startup_1.ogg

---

### Post by jehnx on 2006-03-22
Barrakketh, if there is any way for me to thank you, just let me know!  Thank you so much for your help!!!

---

### Post by Barrakketh on 2006-03-22
[QUOTE=jehnx]Barrakketh, if there is any way for me to thank you, just let me know!  Thank you so much for your help!!![/QUOTE]
You're welcome.  Update your first post and add [SOLVED] to the title :)

---

