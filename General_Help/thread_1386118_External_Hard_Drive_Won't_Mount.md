---
title: "External Hard Drive Won't Mount"
date: 2010-01-20
forum: General Help
---

### Post by akamigs on 2010-01-20
I'm trying to recover files I have stored on a 3.5" IDE hard drive that had Windows ME installed on it. I am using a SATA / IDE to USB kit to connect the HD to my Ubuntu machine via USB. The HD does show up under "Computer" as a "USB Drive". When I double click on it says it can't mount. A while back I used the "cp -r directory" command in the terminal on a similar case, however I could use a refresher. What's the best way you guys suggest to get the files off of the HD? 

THANK YOU FOR ANY RESPONSES.

---

### Post by Leppie on 2010-01-20
you could try testdisk: [http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

---

### Post by synapsys on 2010-01-20
What is the exact error message you're getting when it says it can't mount?

---

### Post by akamigs on 2010-01-20
> **Leppie said:**
> you could try testdisk: [http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

that program only detects my internal drive

---

### Post by akamigs on 2010-01-20
> **synapsys said:**
> What is the exact error message you're getting when it says it can't mount?

"Unable to mount location Can't mount file"

---

### Post by akamigs on 2010-01-20
A FEW COMMANDS I RAN:

sudo fdisk -l
```
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xdca7dca7

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9728    78140128+   7  HPFS/NTFS
```

sudo lsusb
```
ubuntu@ubuntu:~$ sudo lsusb
Bus 005 Device 002: ID 152d:2338 JMicron Technology Corp. / JMicron USA Technology Corp. JM20337 Hi-Speed USB to SATA & PATA Combo Bridge
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
```

sudo dmesg | tail
```
ubuntu@ubuntu:~$ sudo dmesg | tail
[  143.626823] [drm] Initialized drm 1.1.0 20060810
[  143.676818] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 16 (level, low) -> IRQ 21
[  143.677112] [drm] Initialized via 2.11.1 20070202 on minor 0
[  143.685470] agpgart: Found an AGP 3.5 compliant device at 0000:00:00.0.
[  143.685513] agpgart: Device is in legacy mode, falling back to 2.x
[  143.685523] agpgart: Putting AGP V2 device at 0000:00:00.0 into 0x mode
[  143.685619] agpgart: Putting AGP V2 device at 0000:01:00.0 into 0x mode
[  145.487398] NET: Registered protocol family 10
[  145.488470] lo: Disabled Privacy Extensions
[  155.801176] eth0: no IPv6 routers present
```

---

### Post by efflandt on 2010-01-20
The term "recover" makes me wonder if there was (is) anything wrong with the drive.

I was trying to recover info from a laptop drive that WinXP Pro refused to boot (even in Safe mode) saying that the drive was bad and it was just trying to preserve remaining data.  From Ubuntu CD I was able to only copy some of the user's home dir to a USB drive, when it choked to a halt before it even got to My Documents.  Gparted live CD refused to touch the partition until Windows fixed it.

When I first put the drive in external USB enclosure, the USB enclosure was recognized, but the drive just made clicking noises like reading trouble, and I could not do anything with it from WinXP or Linux.  I just plugged it into my desktop (64-bit Ubuntu 9.10) and surprisingly it auto mounted.  So I copied whatever data I could (not sure if any is corrupted).  It could not read a dir called DNA, but appears to have now copied My Documents.  This is what shows for it in tail end of dmesg:

```
[148799.941763] usb 1-1: new high speed USB device using ehci_hcd and address 5
[148800.091510] usb 1-1: configuration #1 chosen from 1 choice
[148800.094881] scsi5 : SCSI emulation for USB Mass Storage devices
[148800.095116] usb-storage: device found at 5
[148800.095121] usb-storage: waiting for device to settle before scanning
[148805.090287] usb-storage: device scan complete
[148805.090874] scsi 5:0:0:0: Direct-Access     Initio   IC25N040ATCS05-0 1.06 PQ: 0 ANSI: 0
[148805.091722] sd 5:0:0:0: Attached scsi generic sg7 type 0
[148805.114780] sd 5:0:0:0: [sdf] 78140160 512-byte logical blocks: (40.0 GB/37.2 GiB)
[148805.115922] sd 5:0:0:0: [sdf] Write Protect is off
[148805.115931] sd 5:0:0:0: [sdf] Mode Sense: 23 00 00 00
[148805.115938] sd 5:0:0:0: [sdf] Assuming drive cache: write through
[148805.121436] sd 5:0:0:0: [sdf] Assuming drive cache: write through
[148805.121445]  sdf: sdf1 sdf2
[148805.160132] sd 5:0:0:0: [sdf] Assuming drive cache: write through
[148805.160146] sd 5:0:0:0: [sdf] Attached SCSI disk
[148883.682394] sd 5:0:0:0: [sdf] Unhandled sense code
[148883.682403] sd 5:0:0:0: [sdf] Result: hostbyte=DID_ERROR driverbyte=DRIVER_SENSE
[148883.682412] sd 5:0:0:0: [sdf] Sense Key : Hardware Error [current] 
[148883.682423] Info fld=0x0
[148883.682427] sd 5:0:0:0: [sdf] Add. Sense: No additional sense information
[148883.682437] end_request: I/O error, dev sdf, sector 69343516
[148883.682448] Buffer I/O error on device sdf2, logical block 8659907
[148883.682458] Buffer I/O error on device sdf2, logical block 8659908
[148883.682466] Buffer I/O error on device sdf2, logical block 8659909
[148883.682474] Buffer I/O error on device sdf2, logical block 8659910
[148883.682482] Buffer I/O error on device sdf2, logical block 8659911
[148883.682490] Buffer I/O error on device sdf2, logical block 8659912
[148883.682498] Buffer I/O error on device sdf2, logical block 8659913
[148883.682505] Buffer I/O error on device sdf2, logical block 8659914
[148883.682513] Buffer I/O error on device sdf2, logical block 8659915
[148883.682521] Buffer I/O error on device sdf2, logical block 8659916
```USB enclosure was a cheap Kingwin from Frys: Bus 001 Device 005: ID 13fd:1040 Initio Corporation

---

### Post by Leppie on 2010-01-20
sounds a bit like the issue in this bug report: [http://www.mail-archive.com/ubuntu-bugs@lists.ubuntu.com/msg1782556.html](http://www.mail-archive.com/ubuntu-bugs@lists.ubuntu.com/msg1782556.html)

---

