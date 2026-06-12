---
title: "Ruined flash drives(unetbootin issue)"
date: 2010-01-26
forum: General Help
---

### Post by Andrew_Carr on 2010-01-26
So I've been using unetbootin for awhile. I've noticed that if, for whatever reason, the install process doesn't complete, I sometimes have a flash drive that won't boot, be recognized by the OS(Windows & Linux), etc. 

   Well usually I just use gparted to delete the partitions and redo it. But now I have a thumb drive that gparted doesn't see, windows doesn't see, and Ubuntu doesn't see. So I have no idea how to reformat it at this point. I was able to reformat my SDHC cards by using my mp3 player that has a built in auto format, but since I can't stick my thumb drive in my mp3 player(QQ), I'm not sure how to fix it. Any help would be appreciated.

---

### Post by ajgreeny on 2010-01-26
Try the command line fdisk program.  See ```
man fdisk
``` for more details.
If that is a no go, I don't know what else to suggest.

---

### Post by Andrew_Carr on 2010-01-26
I tried 

sudo fdisk -l 

But it only lists the 3 partitions on my hard drive(sda1, 2, 5, ext3, extended, linux-swap), not the thumb drive. 

   I'm thinking maybe I messed up the header or whatever that identifies the drive's filesystem as fat32, ext3, etc., but I'm not sure how to fix that.

---

### Post by lavinog on 2010-01-26
use dmesg to see if the kernel is at least seeing you attach the drive
you should see something like this:
```

[ 1799.320106] usb 1-2.6: new high speed USB device using ehci_hcd and address 10
[ 1799.434388] usb 1-2.6: configuration #1 chosen from 1 choice
[ 1799.482091] Initializing USB Mass Storage driver...
[ 1799.482586] scsi6 : SCSI emulation for USB Mass Storage devices
[ 1799.482795] usbcore: registered new interface driver usb-storage
[ 1799.482802] USB Mass Storage support registered.
[ 1799.488471] usb-storage: device found at 10
[ 1799.488477] usb-storage: waiting for device to settle before scanning
[ 1800.191292] usb 3-1: new full speed USB device using ohci_hcd and address 6
[ 1804.480334] usb-storage: device scan complete
[ 1804.481230] scsi 6:0:0:0: Direct-Access     USB Mass Storage Device   1.00 PQ: 0 ANSI: 2
[ 1804.483135] sd 6:0:0:0: Attached scsi generic sg3 type 0
[ 1804.484706] sd 6:0:0:0: [sdc] 253952 512-byte logical blocks: (130 MB/124 MiB)
[ 1804.485327] sd 6:0:0:0: [sdc] Write Protect is off
[ 1804.485333] sd 6:0:0:0: [sdc] Mode Sense: 03 00 00 00
[ 1804.485338] sd 6:0:0:0: [sdc] Assuming drive cache: write through
[ 1804.487946] sd 6:0:0:0: [sdc] Assuming drive cache: write through
[ 1804.487953]  sdc: sdc1
[ 1804.493321] sd 6:0:0:0: [sdc] Assuming drive cache: write through
[ 1804.493329] sd 6:0:0:0: [sdc] Attached SCSI removable disk
[ 1810.390448] usb 3-1: device descriptor read/all, error -110
[ 1810.560047] usb 3-1: new full speed USB device using ohci_hcd and address 7

```

---

### Post by Andrew_Carr on 2010-01-26
Ok, so I do get stuff from dmesg. 

Initializing USB Mass Storage driver...
scsi6 : SCSI emulation for USB Mass Storage devices
USB Mass Storage support registered.
scsi7 : SCSI emulation for USB Mass Storage devices
scsi8 : SCSI emulation for USB Mass Storage devices
scsi9 : SCSI emulation for USB Mass Storage devices
scsi10 : SCSI emulation for USB Mass Storage devices

usb 1-3: USB disconnect, address 4
usb 1-3: new high speed USB device using ehci_hcd and address 6
usb 1-3: configuration #1 chosen from 1 choice

usb-storage: device found at 7
usb-storage: waiting for device to settle before scanning
usb-storage: device scan complete

This is repeated from values 3-7 for "device found at X"

---

### Post by lavinog on 2010-01-26
What flash drive is this?
Is it a U3 drive?

---

### Post by Andrew_Carr on 2010-01-26
Nope, just a normal thumb drive. I've reformatted it plenty of times and booted several linux distros from it.

---

### Post by HermanAB on 2010-01-26
Uhmmm, the useful information is immediately after this
```
usb-storage: device found at 7
usb-storage: waiting for device to settle before scanning
usb-storage: device scan complete
```

Assuming it was sdb, then all you need to do is wipe the first part of the disk using dd, then partition and format it again:
$ sudo dd if=/dev/zero of=/dev/sdb bs=1M count=10
$ sudo fdisk /dev/sdb
n
1
enter enter
w
$ mkfs.vfat -n FATTIE /dev/sdb1

---

### Post by Andrew_Carr on 2010-01-26
Ah, my bad. Right after that it has:

scsi 10:0:0:0: Direct-Access     Generic   USB Flash Disk   7.76 PQ: 0 ANSI: 2

sd 10:0:0:0: [sdb] Attached SCSI removable disk
sd 10:0:0:0: Attached scsi generic sg1 type 0


the sudo dd command returns:

dd: opening `/dev/sdb`: No medium found though, and fdisk /dev/sdb returns 

Unable to open /dev/sdb.

---

### Post by Andrew_Carr on 2010-01-26
nm, using sdb1 in those commands instead of sdb is working. Thanks!

fdisk is telling me "You must set cylinders" when entering n. Not sure how many that would be for a 16GB drive. Does 7750 cylinders sound correct? (Assuming it's 16*10^9 bytes, not 16*2^30). 

Used this formula: cylinders * 63 sectors * 64 heads * 512 bytes/cylinder.


Source: [http://tldp.org/HOWTO/Partition/fdisk_partitioning.html](http://tldp.org/HOWTO/Partition/fdisk_partitioning.html)

(Note: Not sure what he's talking about when he says "er... divided by 1024)"

---

### Post by Andrew_Carr on 2010-02-08
Ok, I sorta solved the problem. I had to add a partition with fdisk.

sudo fdisk /dev/sdb1
> a  
> 1
> w
Ctrl +C to exit fdisk

Open gparted(sudo gparted), then create the partition table(set to msdos). 


**fdisk must've changed since 2005. Now a toggles a bootable flag and n adds a new partition.
[http://www.linuxquestions.org/questions/linux-hardware-18/not-valid-partition-table-393042/](http://www.linuxquestions.org/questions/linux-hardware-18/not-valid-partition-table-393042/)
**

Regardless, gparted sees the drive now, but I'm having issues adding a partition or formatting the drive. I keep getting 

"You must set cylinders"

in fdisk.

---

### Post by Andrew_Carr on 2010-02-08
Here's the dmesg output btw

[75461.948043] usb 1-8: new high speed USB device using ehci_hcd and address 14
[75462.124729] usb 1-8: configuration #1 chosen from 1 choice
[75462.166937] scsi13 : SCSI emulation for USB Mass Storage devices
[75462.168961] usb-storage: device found at 14
[75462.168968] usb-storage: waiting for device to settle before scanning
[75467.168360] usb-storage: device scan complete
[75467.170573] scsi 13:0:0:0: Direct-Access     Generic- Multi-Card       1.00 PQ: 0 ANSI: 0 CCS
[75468.542328] sd 13:0:0:0: [sdb] 61419520 512-byte hardware sectors: (31.4 GB/29.2 GiB)
[75468.543063] sd 13:0:0:0: [sdb] Write Protect is off
[75468.543069] sd 13:0:0:0: [sdb] Mode Sense: 03 00 00 00
[75468.543074] sd 13:0:0:0: [sdb] Assuming drive cache: write through
[75468.547825] sd 13:0:0:0: [sdb] 61419520 512-byte hardware sectors: (31.4 GB/29.2 GiB)
[75468.548953] sd 13:0:0:0: [sdb] Write Protect is off
[75468.548960] sd 13:0:0:0: [sdb] Mode Sense: 03 00 00 00
[75468.548965] sd 13:0:0:0: [sdb] Assuming drive cache: write through
[75468.548977]  sdb:

---

### Post by Andrew_Carr on 2010-02-08
Weird. So now gparted can try to format the unallocated partition & file system to various file types. But the size is listed as 10mb. I dd'd the drive twice earlier. First time it returned something like 512mb written, second time it returned 10mb written. So now it looks like I have a working, unpartitioned space of 10mb on the drive.

dd commands used:

sudo dd if=/dev/zero of=/dev/sdb bs=1M count=10

Using /dev/sdb or /dev/sdb1 doesn't seem to make a different.
Also, changing the count to 32000 results in 510mb being written.

---

### Post by lavinog on 2010-02-08
How old is this flash drive?

---

### Post by Andrew_Carr on 2010-02-11
The sd card I'm posting the dmesg's for is about 1 month old now. The thumb drive I have that has the same issue is about 2 years old.

---

