---
title: "Slow USB transfer"
date: 2011-10-05
forum: General Help
---

### Post by doas777 on 2011-10-05
I have a 10.04.3 desktop server with a number of USB harddisks attached. When I copy data from one to another, or access the data over samba, the transfer speed is generally between 15 and 30MB/s using large files.

the disks are all WD 1TB 720 disks (WDC WD10 01FALS-00J7B0) and all have stellar SMART health. Each contains one EXT4 partition. they are sdd, sde, and sdf.

I've walked through the [DebuggingUSBStorage ]("https://help.ubuntu.com/community/DebuggingUSBStorage")and [DiskPerformance ]("https://help.ubuntu.com/community/DiskPerformance")
guides, but it seems like most of the standard diagnostics show no issue.

here are some snippets of my kern.log related to USB and SCSI mounting on these disks:
```

Oct  5 22:03:31 localhost kernel: [    0.491855] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver

Oct  5 22:03:31 localhost kernel: [    0.492148] ehci_hcd 0000:00:02.1: PCI INT B -> Link[APCL] -> GSI 20 (level, low) -> IRQ 20
Oct  5 22:03:31 localhost kernel: [    0.492170] ehci_hcd 0000:00:02.1: setting latency timer to 64
Oct  5 22:03:31 localhost kernel: [    0.492172] ehci_hcd 0000:00:02.1: EHCI Host Controller
Oct  5 22:03:31 localhost kernel: [    0.492237] ehci_hcd 0000:00:02.1: new USB bus registered, assigned bus number 1
Oct  5 22:03:31 localhost kernel: [    0.492263] ehci_hcd 0000:00:02.1: debug port 1
Oct  5 22:03:31 localhost kernel: [    0.492268] ehci_hcd 0000:00:02.1: cache line size of 64 is not supported
Oct  5 22:03:31 localhost kernel: [    0.492288] ehci_hcd 0000:00:02.1: irq 20, io mem 0xfe02e000
Oct  5 22:03:31 localhost kernel: [    0.510018] ehci_hcd 0000:00:02.1: USB 2.0 started, EHCI 1.00
Oct  5 22:03:31 localhost kernel: [    0.510090] usb usb1: configuration #1 chosen from 1 choice
Oct  5 22:03:31 localhost kernel: [    0.510115] hub 1-0:1.0: USB hub found
Oct  5 22:03:31 localhost kernel: [    0.510124] hub 1-0:1.0: 10 ports detected
Oct  5 22:03:31 localhost kernel: [    0.510179] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver

Oct  5 22:03:31 localhost kernel: [    0.510484] ohci_hcd 0000:00:02.0: PCI INT A -> Link[APCF] -> GSI 23 (level, low) -> IRQ 23
Oct  5 22:03:31 localhost kernel: [    0.510497] ohci_hcd 0000:00:02.0: setting latency timer to 64
Oct  5 22:03:31 localhost kernel: [    0.510499] ohci_hcd 0000:00:02.0: OHCI Host Controller
Oct  5 22:03:31 localhost kernel: [    0.510528] ohci_hcd 0000:00:02.0: new USB bus registered, assigned bus number 2
Oct  5 22:03:31 localhost kernel: [    0.510550] ohci_hcd 0000:00:02.0: irq 23, io mem 0xfe02f000
Oct  5 22:03:31 localhost kernel: [    0.572074] usb usb2: configuration #1 chosen from 1 choice
Oct  5 22:03:31 localhost kernel: [    0.572096] hub 2-0:1.0: USB hub found
Oct  5 22:03:31 localhost kernel: [    0.572103] hub 2-0:1.0: 10 ports detected
Oct  5 22:03:31 localhost kernel: [    0.572156] uhci_hcd: USB Universal Host Controller Interface driver

Oct  5 22:03:31 localhost kernel: [    0.891263] usb 1-3: new high speed USB device using ehci_hcd and address 3
Oct  5 22:03:31 localhost kernel: [    1.043007] usb 1-3: configuration #1 chosen from 1 choice
Oct  5 22:03:31 localhost kernel: [    1.049047] Initializing USB Mass Storage driver...
Oct  5 22:03:31 localhost kernel: [    1.049183] scsi4 : SCSI emulation for USB Mass Storage devices
Oct  5 22:03:31 localhost kernel: [    1.049267] usbcore: registered new interface driver usb-storage
Oct  5 22:03:31 localhost kernel: [    1.049270] USB Mass Storage support registered.
Oct  5 22:03:31 localhost kernel: [    1.049275] usb-storage: device found at 3
Oct  5 22:03:31 localhost kernel: [    1.049276] usb-storage: waiting for device to settle before scanning
Oct  5 22:03:31 localhost kernel: [    1.220284] usb 1-9: new high speed USB device using ehci_hcd and address 5

Oct  5 22:03:31 localhost kernel: [    1.220737] sata_nv 0000:00:05.1: PCI INT B -> Link[APSJ] -> GSI 22 (level, low) -> IRQ 22
Oct  5 22:03:31 localhost kernel: [    1.220739] sata_nv 0000:00:05.1: Using SWNCQ mode
Oct  5 22:03:31 localhost kernel: [    1.221095] sata_nv 0000:00:05.1: setting latency timer to 64
Oct  5 22:03:31 localhost kernel: [    1.221219] scsi5 : sata_nv
Oct  5 22:03:31 localhost kernel: [    1.221317] scsi6 : sata_nv
Oct  5 22:03:31 localhost kernel: [    1.222044] scsi7 : sata_nv
Oct  5 22:03:31 localhost kernel: [    1.222133] scsi8 : sata_nv

Oct  5 22:03:31 localhost kernel: [    1.373014] usb 1-9: configuration #1 chosen from 1 choice
Oct  5 22:03:31 localhost kernel: [    1.374038] scsi9 : SCSI emulation for USB Mass Storage devices
Oct  5 22:03:31 localhost kernel: [    1.374175] usb-storage: device found at 5
Oct  5 22:03:31 localhost kernel: [    1.374177] usb-storage: waiting for device to settle before scanning

Oct  5 22:03:31 localhost kernel: [    1.642986] usb 1-10: configuration #1 chosen from 1 choice
Oct  5 22:03:31 localhost kernel: [    1.644039] scsi10 : SCSI emulation for USB Mass Storage devices
Oct  5 22:03:31 localhost kernel: [    1.644169] usb-storage: device found at 6
Oct  5 22:03:31 localhost kernel: [    1.644170] usb-storage: waiting for device to settle before scanning

Oct  5 22:03:31 localhost kernel: [    1.990015] usb 2-1: new low speed USB device using ohci_hcd and address 2
Oct  5 22:03:31 localhost kernel: [    2.225119] usb 2-1: configuration #1 chosen from 1 choice

Oct  5 22:03:31 localhost kernel: [    2.560093] usb 2-4: new low speed USB device using ohci_hcd and address 3

Oct  5 22:03:31 localhost kernel: [    2.792131] usb 2-4: configuration #1 chosen from 1 choice
Oct  5 22:03:31 localhost kernel: [    2.799645] usbcore: registered new interface driver hiddev

Oct  5 22:03:31 localhost kernel: [    2.884193] input: Microsoft Wired Keyboard 600 as /devices/pci0000:00/0000:00:02.0/usb2/2-4/2-4:1.1/input/input4
Oct  5 22:03:31 localhost kernel: [    2.884280] generic-usb 0003:045E:0750.0003: input,hidraw2: USB HID v1.11 Device [Microsoft Wired Keyboard 600] on usb-0000:00:02.0-4/input1
Oct  5 22:03:31 localhost kernel: [    2.884304] usbcore: registered new interface driver usbhid
Oct  5 22:03:31 localhost kernel: [    2.884306] usbhid: v2.6:USB HID core driver
Oct  5 22:03:31 localhost kernel: [    6.041481] usb-storage: device scan complete
Oct  5 22:03:31 localhost kernel: [    6.045099] scsi 4:0:0:0: Direct-Access     WDC WD10 01FALS-00J7B0         PQ: 0 ANSI: 2 CCS
Oct  5 22:03:31 localhost kernel: [    6.045475] sd 4:0:0:0: Attached scsi generic sg4 type 0
Oct  5 22:03:31 localhost kernel: [    6.046193] sd 4:0:0:0: [sdd] 1953525168 512-byte logical blocks: (1.00 TB/931 GiB)
Oct  5 22:03:31 localhost kernel: [    6.047438] sd 4:0:0:0: [sdd] Write Protect is off
Oct  5 22:03:31 localhost kernel: [    6.047440] sd 4:0:0:0: [sdd] Mode Sense: 00 38 00 00
Oct  5 22:03:31 localhost kernel: [    6.047442] sd 4:0:0:0: [sdd] Assuming drive cache: write through
Oct  5 22:03:31 localhost kernel: [    6.049460] sd 4:0:0:0: [sdd] Assuming drive cache: write through
Oct  5 22:03:31 localhost kernel: [    6.049466]  sdd: sdd1
Oct  5 22:03:31 localhost kernel: [    6.060439] sd 4:0:0:0: [sdd] Assuming drive cache: write through
Oct  5 22:03:31 localhost kernel: [    6.060442] sd 4:0:0:0: [sdd] Attached SCSI disk
Oct  5 22:03:31 localhost kernel: [    6.254323] Adding 4883752k swap on /dev/sdb3.  Priority:-1 extents:1 across:4883752k 
Oct  5 22:03:31 localhost kernel: [    6.380220] usb-storage: device scan complete
Oct  5 22:03:31 localhost kernel: [    6.382572] scsi 9:0:0:0: Direct-Access     WDC WD10 01FALS-00J7B0         PQ: 0 ANSI: 2 CCS
Oct  5 22:03:31 localhost kernel: [    6.382907] sd 9:0:0:0: Attached scsi generic sg5 type 0
Oct  5 22:03:31 localhost kernel: [    6.383443] sd 9:0:0:0: [sde] 1953525168 512-byte logical blocks: (1.00 TB/931 GiB)
Oct  5 22:03:31 localhost kernel: [    6.384437] sd 9:0:0:0: [sde] Write Protect is off
Oct  5 22:03:31 localhost kernel: [    6.384440] sd 9:0:0:0: [sde] Mode Sense: 00 38 00 00
Oct  5 22:03:31 localhost kernel: [    6.384441] sd 9:0:0:0: [sde] Assuming drive cache: write through
Oct  5 22:03:31 localhost kernel: [    6.386436] sd 9:0:0:0: [sde] Assuming drive cache: write through
Oct  5 22:03:31 localhost kernel: [    6.386479]  sde: sde1
Oct  5 22:03:31 localhost kernel: [    6.400438] sd 9:0:0:0: [sde] Assuming drive cache: write through
Oct  5 22:03:31 localhost kernel: [    6.400484] sd 9:0:0:0: [sde] Attached SCSI disk
Oct  5 22:03:31 localhost kernel: [    6.650239] usb-storage: device scan complete
Oct  5 22:03:31 localhost kernel: [    6.651577] scsi 10:0:0:0: Direct-Access     WDC WD10 01FALS-75J7B0         PQ: 0 ANSI: 2 CCS
Oct  5 22:03:31 localhost kernel: [    6.652008] sd 10:0:0:0: Attached scsi generic sg6 type 0
Oct  5 22:03:31 localhost kernel: [    6.652565] sd 10:0:0:0: [sdf] 1953525168 512-byte logical blocks: (1.00 TB/931 GiB)
Oct  5 22:03:31 localhost kernel: [    6.653438] sd 10:0:0:0: [sdf] Write Protect is off
Oct  5 22:03:31 localhost kernel: [    6.653440] sd 10:0:0:0: [sdf] Mode Sense: 00 38 00 00
Oct  5 22:03:31 localhost kernel: [    6.653442] sd 10:0:0:0: [sdf] Assuming drive cache: write through
Oct  5 22:03:31 localhost kernel: [    6.655439] sd 10:0:0:0: [sdf] Assuming drive cache: write through
Oct  5 22:03:31 localhost kernel: [    6.655481]  sdf: sdf1
Oct  5 22:03:31 localhost kernel: [    6.682438] sd 10:0:0:0: [sdf] Assuming drive cache: write through
Oct  5 22:03:31 localhost kernel: [    6.682480] sd 10:0:0:0: [sdf] Attached SCSI disk

Oct  5 22:03:31 localhost kernel: [   15.623405] EXT4-fs (sde1): mounted filesystem with ordered data mode
Oct  5 22:03:31 localhost kernel: [   17.947811] EXT4-fs (sdf1): mounted filesystem with ordered data mode
Oct  5 22:03:31 localhost kernel: [   20.406294] kjournald starting.  Commit interval 5 seconds


```to me it lookslike everything is being mounted using usbhid and is on the same bus as my 2.0 root hub. I don't have any idea what those devices on the usb 1.0 hub are though.

I checked for buffer errors and got nothing, but my hdparm output looks weird:
```

user@server:~$ sudo sh -c "echo 120 > /sys/block/sdd/queue/max_sectors_kb"
user@server:~$ sudo sh -c "echo 64 > /sys/block/sdd/queue/max_sectors_kb"
user@server:~$ sudo sh -c "echo 32 > /sys/block/sdd/queue/max_sectors_kb"
user@server:~$ lsusb
Bus 002 Device 003: ID 045e:0750 Microsoft Corp. 
Bus 002 Device 002: ID 0764:0501 Cyber Power System, Inc. CP1500 AVR UPS
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 006: ID 152d:2336 JMicron Technology Corp. / JMicron USA Technology Corp. Hard Disk Drive
Bus 001 Device 005: ID 152d:2336 JMicron Technology Corp. / JMicron USA Technology Corp. Hard Disk Drive
Bus 001 Device 003: ID 152d:2336 JMicron Technology Corp. / JMicron USA Technology Corp. Hard Disk Drive
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
user@server:~$ sudo hdparm /dev/sdd
[sudo] password for user: 
/dev/sdd:
 HDIO_DRIVE_CMD(identify) failed: Invalid exchange
 readonly      =  0 (off)
 readahead     = 256 (on)
 geometry      = 121601/255/63, sectors = 1953525168, start = 0

```So, any ideas what to try next? Does swapping out io schedulers make that much of a differance? unusual_device configs? Neither seems quite right to me, but I am likely wrong....

so does anyone see anything in these logs that is escaping me, or have any ideas what to try next?

Thanks!

---

### Post by dcstar on 2011-10-06
> **doas777 said:**
> I have a 10.04.3 desktop server with a number of USB harddisks attached. When I copy data from one to another, or access the data over samba, the transfer speed is generally between 15 and 30MB/s using large files.
............
so does anyone see anything in these logs that is escaping me, or have any ideas what to try next?

Thanks!

USB 2 is a crappy interface for bulk data transfer, so I don't know why you expect it to be fast.

I have an external 1TB drive with USB 2 and eSATA interfaces and the eSATA connection is at least 5 times faster than USB.

---

### Post by Linuxisfast on 2011-10-06
If you use a powered usb hub, things get far better even though you don't get high speed, you get sustained data transfer instead of data drops.

---

### Post by doas777 on 2011-10-06
> **dcstar said:**
> USB 2 is a crappy interface for bulk data transfer, so I don't know why you expect it to be fast.

I have an external 1TB drive with USB 2 and eSATA interfaces and the eSATA connection is at least 5 times faster than USB.

ok, thats a fair question, but I am skeptical regarding your assertion. 

I guess the reason I would expect it, is because the spec says it should transfer at 480MB/s, so the only limiting factor is the speed of the drive, and this drive can support a sustained write speed of 60MB/s plus, with peak above 120MB/s. since I'm getting a meer 1/6th of that, I would assume something is wrong. I agree eSATA would be prefereable, but I wouldn't be able to find many motherboards that support the number of connections I would have.

@Linuxisfast, Interesting. each of these disks is independently powered, so do you think it would still make a differance? That woudl mean that they would all be sharing the same uplink connection to the box, so wouldn't that introduce a bottleneck when performing ops on several of the drives at once?

---

### Post by doas777 on 2011-10-07
<bump />

---

### Post by repilce on 2011-11-03
> **dcstar said:**
> USB 2 is a crappy interface for bulk data transfer, so I don't know why you expect it to be fast.

I have an external 1TB drive with USB 2 and eSATA interfaces and the eSATA connection is at least 5 times faster than USB.

I'm sorry, but that is a very poor response to the OP's question.
If he could use eSATA, he probably would. There's no reason to give "USB 2 is crappy" when, clearly, it's not performing as it should. 

Most people like "fixing" problems, rather than elimination by bypassing the issue.

I for one am having some "crappy" usb 2 performance myself since using 11.10. It seems that this phenomenon is still very much a problem for ubuntu. And since my Android Device doesn't have a eSATA port.. I guess that's out of the question :rolleyes:

---

