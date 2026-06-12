---
title: "issues with external 1TB hard drive partition"
date: 2009-10-06
forum: General Help
---

### Post by 987a654 on 2009-10-06
Hi guys

I am trying to partition a new Seagate 7200.12  1TB hard drive, I am using a hard drive dock connected through USB to my laptop. 

First I used the Vista's built in disk manager, but it failed then I used Gparted in Ubuntu's latest live CD (64bit) to format the drive but it threw up an error as well. It's as follows:

GParted 0.4.3

Libparted 1.8.8
Create Primary Partition #1 (ntfs, 300.00 GiB) on /dev/sdb  00:03:31    ( ERROR )
     	
create empty partition  00:00:11    ( SUCCESS )
     	
path: /dev/sdb1
start: 63
end: 629153594
size: 629153532 (300.00 GiB)
set partition type on /dev/sdb1  00:00:10    ( SUCCESS )
     	
new partition type: ntfs
create new ntfs file system  00:03:10    ( ERROR )
     	
mkntfs -Q -v -L "" /dev/sdb1
     	
Cluster size has been automatically set to 4096 bytes.
Creating NTFS volume structures.
Creating root directory (mft record 5)
Creating $MFT (mft record 0)
Creating $MFTMirr (mft record 1)
Creating $LogFile (mft record 2)
Creating $AttrDef (mft record 4)
Creating $Bitmap (mft record 6)
Creating $Boot (mft record 7)
Creating backup boot sector.
Creating $Volume (mft record 3)
Creating $BadClus (mft record 8)
Creating $Secure (mft record 9)
Creating $UpCase (mft record 0xa)
Creating $Extend (mft record 11)
Creating system file (mft record 0xc)
Creating system file (mft record 0xd)
Creating system file (mft record 0xe)
Creating system file (mft record 0xf)
Creating $Quota (mft record 24)
Creating $ObjId (mft record 25)
Creating $Reparse (mft record 26)
Syncing root directory index record.
Syncing $Bitmap.
Syncing $MFT.
Updating $MFTMirr.
Syncing device.
Syncing device. FAILED



Prior to this I formatted two seagate hard drives (320Gb and 500gb), not a single hiccup using gparted. The only difference between then and now is the interface, back then I used SATA but now I am using USB.

can someone please help!!

Yudi

---

### Post by dcstar on 2009-10-06
> **987a654 said:**
> Hi guys

I am trying to partition a new Seagate 7200.12  1TB hard drive, I am using a hard drive dock connected through USB to my laptop. 

**First I used the Vista's built in disk manager, but it failed then I used Gparted in Ubuntu's latest live CD (64bit) to format the drive but it threw up an error as well.**
.........
can someone please help!!

You have an obvious hardware problem if two different OSs cannot format the same drive on your equipment.

I doubt you will find a solution in a software forum for a specific OS.

---

### Post by 987a654 on 2009-10-07
fixed it.

It was the USB cable, stupid me. It was either too long (1.5m) or inferior. Replaced it with a new short one. Worked like a charm. 

Thanks guys

---

