---
title: "memory stick failed IO superblock"
date: 2009-11-11
forum: General Help
---

### Post by H4F on 2009-11-11
I have and memory stick /dev/mmcblk0.

I have tried to do everything to format it .

root@h4f:/dev# sudo fdisk /dev/mmcblk0

Unable to read /dev/mmcblk0

root@h4f:/dev# dd if=/dev/zero of=/dev/mmcblk0
dd: writing to `/dev/mmcblk0': Input/output error
1+0 records in
0+0 records out
0 bytes (0 B) copied, 0.0246371 s, 0.0 kB/s

root@h4f:/dev# mkfs -t vfat /dev/mmcblk0
mkfs.vfat 3.0.3 (18 May 2009)
mkfs.vfat: failed whilst writing reserved sector
root@h4f:/dev# 

nothing worked so far. 
dmesg:
[ 1290.392590] mmcblk0: error -110 sending read/write command, response 0x0, card status 0x3400b00
[ 1290.392593] end_request: I/O error, dev mmcblk0, sector 6
[ 1290.394721] mmcblk0: error -110 sending read/write command, response 0x0, card status 0x3400b00
[ 1290.394724] end_request: I/O error, dev mmcblk0, sector 7
[ 1290.396830] mmcblk0: retrying using single block read
[ 1290.398953] mmcblk0: error -110 sending read/write command, response 0x0, card status 0x3400b00
[ 1290.398956] end_request: I/O error, dev mmcblk0, sector 0
[ 1290.401046] mmcblk0: error -110 sending read/write command, response 0x0, card status 0x3400b00
[ 1290.401050] end_request: I/O error, dev mmcblk0, sector 1
[ 1290.403143] mmcblk0: error -110 sending read/write command, response 0x0, card status 0x3400b00
[ 1290.403148] end_request: I/O error, dev mmcblk0, sector 2
[ 1290.405258] mmcblk0: error -110 sending read/write command, response 0x0, card status 0x3400b00
[ 1290.405261] end_request: I/O error, dev mmcblk0, sector 3
[ 1290.407375] mmcblk0: error -110 sending read/write command, response 0x0, card status 0x3400b00
[ 1290.407377] end_request: I/O error, dev mmcblk0, sector 4
[ 1290.409491] mmcblk0: error -110 sending read/write command, response 0x0, card status 0x3400b00
[ 1290.409493] end_request: I/O error, dev mmcblk0, sector 5
[ 1290.411592] mmcblk0: error -110 sending read/write command, response 0x0, card status 0x3400b00
[ 1290.411594] end_request: I/O error, dev mmcblk0, sector 6
[ 1290.413707] mmcblk0: error -110 sending read/write command, response 0x0, card status 0x3400b00
[ 1290.413710] end_request: I/O error, dev mmcblk0, sector 7


Is there something that I could do more. Or mmcblk0 died forever ?

---

### Post by Giblet5 on 2009-11-11
That's a dead stick.

It happens. NAND flash memory devices deteriorate with every write cycle and they fail very quickly.

If it's a new stick (< six months old), you might be able to get the vendor to replace it for free.

Sandisk is very good about that. So are the fine folks at OCZ.

---

