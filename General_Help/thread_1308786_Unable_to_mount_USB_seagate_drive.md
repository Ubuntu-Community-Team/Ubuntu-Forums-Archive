---
title: "Unable to mount USB seagate drive"
date: 2009-10-31
forum: General Help
---

### Post by Xelfox on 2009-10-31
Hi there I just did a freash install of 9.10 and am trying to mount my external drive to get my files I backed up back and Got an error (Is in the screen shot I took of it below.)

Thanks for your help

---

### Post by gdi2k on 2009-10-31
Have you tried mounting it manually from the command line? That might give you more of a hint as to what's going wrong. 

```
sudo mkdir /mnt/test
sudo mount /dev/sdb1 /mnt/test
```

Do you know what filesystem is on the drive? (NTFS, FAT32, ext3)

---

### Post by lavinog on 2009-11-01
You may need to mount it in windows and then use the safely remove hardware icon prior to disconnecting it.

---

### Post by Adler on 2010-07-23
Hi All,

I've just run into the same issue with Lucid Lynx (Ubuntu 10.04).

I am not able to mount my TB external HDD.

Can I do this from terminal?

Thanks in advance for productive responses.

Best Regards,

JJMacey
Tempe, Arizona

---

### Post by gdi2k on 2010-07-23
The system log may provide some useful feedback. Plug in the drive, then wait 10 seconds before running 
dmesg
from a terminal. If you paste the last few lines starting with "new high speed USB device..." that should be helpful in seeing what's going on. When I plug my external disk in, dmesg shows the following for example: 

```
[164069.770660] usb 1-5.3: new high speed USB device using ehci_hcd and address 14
[164069.881904] usb 1-5.3: configuration #1 chosen from 1 choice
[164069.882333] scsi9 : SCSI emulation for USB Mass Storage devices
[164069.882588] usb-storage: device found at 14
[164069.882594] usb-storage: waiting for device to settle before scanning
[164074.881219] usb-storage: device scan complete
[164074.882245] scsi 9:0:0:0: Direct-Access     WD       My Passport 070B 2003 PQ: 0 ANSI: 4
[164074.883087] scsi 9:0:0:1: Enclosure         WD       SES Device       2003 PQ: 0 ANSI: 4
[164074.884257] sd 9:0:0:0: Attached scsi generic sg2 type 0
[164074.884433] ses 9:0:0:1: Attached Enclosure device
[164074.884553] ses 9:0:0:1: Attached scsi generic sg3 type 13
[164074.892823] sd 9:0:0:0: [sdb] 975400960 512-byte logical blocks: (499 GB/465 GiB)
[164074.894666] sd 9:0:0:0: [sdb] Write Protect is off
[164074.894675] sd 9:0:0:0: [sdb] Mode Sense: 23 00 10 00
[164074.894681] sd 9:0:0:0: [sdb] Assuming drive cache: write through
[164074.899341] sd 9:0:0:0: [sdb] Assuming drive cache: write through
[164074.899355]  sdb: sdb1 sdb2
[164074.947274] sd 9:0:0:0: [sdb] Assuming drive cache: write through
[164074.947285] sd 9:0:0:0: [sdb] Attached SCSI disk
[164075.907411] EXT4-fs (sdb2): warning: maximal mount count reached, running e2fsck is recommended
[164075.909524] EXT4-fs (sdb2): mounted filesystem with ordered data mode
```

---

