---
title: "Can't boot Jaunty &quot;command line system&quot;"
date: 2009-07-08
forum: General Help
---

### Post by Yet Another Dima on 2009-07-08
Hi all and sorry for my bad english.

A few days ago i installed Jaunty from alternate CD. I chose " install command line system". During system's boot i recive error messages:

device-mapper: table: device /dev/sdb too small for target
device-mapper: 252: 0: striped: couldn't parse stripe destination
device-mapper: ioctl: error adding target to table.

These three messages repeats continuously. And system don't want to boot. But when i am installed Ubuntu 9 desktop it works well! But i don't want Jaunty desktop! 
Also, I noticed a strange thing. During installation Jaunty  alternate, installer says me that it finds some RAID drive in my computer and ask me for loading necessary modules (but i don't have any RAID arrays in my computer). If i answered  "yes" in the next installation menu item where i must chose partitioning and mount points i don't see my hdd. So i answered "no" and installation ends well. 
Maybe you now how to solve this problem?

---

### Post by BlindHunter on 2009-12-02
The same **** for me in karmic 9.10.
Can't mount external USB HDD drive!
The problem is that /dev/sdc1 is not generated at all!

dmesg says:
[  145.840719] scsi 7:0:0:0: Direct-Access     StoreJet  Transcend            PQ: 0 ANSI: 2 CCS
[  145.841044] sd 7:0:0:0: Attached scsi generic sg3 type 0
[  145.843331] sd 7:0:0:0: [sdc] 625142448 512-byte logical blocks: (320 GB/298 GiB)
[  145.844421] sd 7:0:0:0: [sdc] Write Protect is off
[  145.844424] sd 7:0:0:0: [sdc] Mode Sense: 34 00 00 00
[  145.844426] sd 7:0:0:0: [sdc] Assuming drive cache: write through
[  145.845955] sd 7:0:0:0: [sdc] Assuming drive cache: write through
[  145.845963]  sdc: sdc1
[  145.870826] sd 7:0:0:0: [sdc] Assuming drive cache: write through
[  145.870830] sd 7:0:0:0: [sdc] Attached SCSI disk
[  146.387521] device-mapper: table: 252:0: striped: Couldn't parse stripe destination
[  146.387524] device-mapper: ioctl: error adding target to table

blkid /dev/sdc
/dev/sdc: TYPE="nvidia_raid_member"

cat /proc/scsi/usb-storage/7 
   Host scsi7: usb-storage
       Vendor: JMicron
      Product: StoreJet Transcend
Serial Number: 33271F131A00
     Protocol: Transparent SCSI
    Transport: Bulk
       Quirks:

---

