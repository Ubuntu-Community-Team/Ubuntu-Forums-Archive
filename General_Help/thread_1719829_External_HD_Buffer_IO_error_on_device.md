---
title: "External HD Buffer I/O error on device"
date: 2011-04-02
forum: General Help
---

### Post by trinacriax on 2011-04-02
Hi guys,

today I've plug my external HD, WD Elements 3.5". The hard drive has 2 partitions: 34 GB @ FAT-32 and 460 GB @ NTFS. 
I accessed to the second partition, it was very slow, I recovered some documents and after deleting some data I was able to browse such partition faster.
While I cannot access at all to the first partition. I cannot mount it and the fsck.vfat is useless :(

```

$ dmesg
[  831.382812] usb 2-2: new high speed USB device using ehci_hcd and address 4
[  831.531923] usb 2-2: configuration #1 chosen from 1 choice
[  831.533025] scsi7 : SCSI emulation for USB Mass Storage devices
[  831.533356] usb-storage: device found at 4
[  831.533361] usb-storage: waiting for device to settle before scanning
[  836.530673] usb-storage: device scan complete
[  836.531441] scsi 7:0:0:0: Direct-Access     WD       5000AAK External 1.06 PQ: 0 ANSI: 0
[  836.536987] sd 7:0:0:0: Attached scsi generic sg2 type 0
[  836.540832] sd 7:0:0:0: [sdb] 976773168 512-byte logical blocks: (500 GB/465 GiB)
[  836.541585] sd 7:0:0:0: [sdb] Write Protect is off
[  836.541592] sd 7:0:0:0: [sdb] Mode Sense: 00 00 00 00
[  836.541598] sd 7:0:0:0: [sdb] Assuming drive cache: write through
[  836.543089] sd 7:0:0:0: [sdb] Assuming drive cache: write through
[  836.543097]  sdb: sdb1 sdb2 < sdb5 >
[  836.562600] sd 7:0:0:0: [sdb] Assuming drive cache: write through
[  836.562609] sd 7:0:0:0: [sdb] Attached SCSI disk
[  853.024730] sd 7:0:0:0: [sdb] Unhandled sense code
[  853.024739] sd 7:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_SENSE
[  853.024749] sd 7:0:0:0: [sdb] Sense Key : Hardware Error [current] 
[  853.024760] Info fld=0x0
[  853.024764] sd 7:0:0:0: [sdb] Add. Sense: No additional sense information
[  853.024773] sd 7:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 38 00 00 08 00
[  853.024794] end_request: I/O error, dev sdb, sector 56
[  853.024805] Buffer I/O error on device sdb, logical block 7
[  869.852978] sd 7:0:0:0: [sdb] Unhandled sense code
[  869.852987] sd 7:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_SENSE
[  869.852997] sd 7:0:0:0: [sdb] Sense Key : Hardware Error [current] 
[  869.853008] Info fld=0x0
[  869.853012] sd 7:0:0:0: [sdb] Add. Sense: No additional sense information
[  869.853021] sd 7:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 38 00 00 08 00
[  869.853043] end_request: I/O error, dev sdb, sector 56
[  869.853052] Buffer I/O error on device sdb, logical block 7
[  886.532189] sd 7:0:0:0: [sdb] Unhandled sense code
[  886.532192] sd 7:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_SENSE
[  886.532195] sd 7:0:0:0: [sdb] Sense Key : Hardware Error [current] 
[  886.532198] Info fld=0x0
[  886.532200] sd 7:0:0:0: [sdb] Add. Sense: No additional sense information
[  886.532203] sd 7:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 38 00 00 08 00
[  886.532209] end_request: I/O error, dev sdb, sector 56
[  886.532213] Buffer I/O error on device sdb, logical block 7
[  903.177360] sd 7:0:0:0: [sdb] Unhandled sense code
[  903.177369] sd 7:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_SENSE
[  903.177378] sd 7:0:0:0: [sdb] Sense Key : Hardware Error [current] 
[  903.177389] Info fld=0x0
[  903.177393] sd 7:0:0:0: [sdb] Add. Sense: No additional sense information
[  903.177403] sd 7:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 3f 00 00 01 00
[  903.177424] end_request: I/O error, dev sdb, sector 63
[  903.177435] Buffer I/O error on device sdb1, logical block 0
[  920.159867] sd 7:0:0:0: [sdb] Unhandled sense code
[  920.159876] sd 7:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_SENSE
[  920.159885] sd 7:0:0:0: [sdb] Sense Key : Hardware Error [current] 
[  920.159896] Info fld=0x0
[  920.159900] sd 7:0:0:0: [sdb] Add. Sense: No additional sense information
[  920.159910] sd 7:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 38 00 00 08 00
[  920.159932] end_request: I/O error, dev sdb, sector 56
[  920.159942] Buffer I/O error on device sdb, logical block 7
[  936.400615] sd 7:0:0:0: [sdb] Unhandled sense code
[  936.400624] sd 7:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_SENSE
[  936.400633] sd 7:0:0:0: [sdb] Sense Key : Hardware Error [current] 
[  936.400644] Info fld=0x0
[  936.400648] sd 7:0:0:0: [sdb] Add. Sense: No additional sense information
[  936.400658] sd 7:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 38 00 00 08 00
[  936.400679] end_request: I/O error, dev sdb, sector 56
[  936.400689] Buffer I/O error on device sdb, logical block 7
[  953.184000] sd 7:0:0:0: [sdb] Unhandled sense code
[  953.184009] sd 7:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_SENSE
[  953.184018] sd 7:0:0:0: [sdb] Sense Key : Hardware Error [current] 
[  953.184029] Info fld=0x0
[  953.184034] sd 7:0:0:0: [sdb] Add. Sense: No additional sense information
[  953.184044] sd 7:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 3f 00 00 01 00
[  953.184065] end_request: I/O error, dev sdb, sector 63
[  953.184076] Buffer I/O error on device sdb1, logical block 0
[  970.049223] sd 7:0:0:0: [sdb] Unhandled sense code
[  970.049232] sd 7:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_SENSE
[  970.049241] sd 7:0:0:0: [sdb] Sense Key : Hardware Error [current] 
[  970.049252] Info fld=0x0
[  970.049256] sd 7:0:0:0: [sdb] Add. Sense: No additional sense information
[  970.049266] sd 7:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 38 00 00 08 00
[  970.049287] end_request: I/O error, dev sdb, sector 56
[  970.049296] Buffer I/O error on device sdb, logical block 7
[  986.548365] sd 7:0:0:0: [sdb] Unhandled sense code
[  986.548375] sd 7:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_SENSE
[  986.548384] sd 7:0:0:0: [sdb] Sense Key : Hardware Error [current] 
[  986.548395] Info fld=0x0
[  986.548400] sd 7:0:0:0: [sdb] Add. Sense: No additional sense information
[  986.548409] sd 7:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 3f 00 00 01 00
[  986.548431] end_request: I/O error, dev sdb, sector 63
[  986.548441] Buffer I/O error on device sdb1, logical block 0
[ 1003.213478] sd 7:0:0:0: [sdb] Unhandled sense code
[ 1003.213487] sd 7:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_SENSE
[ 1003.213496] sd 7:0:0:0: [sdb] Sense Key : Hardware Error [current] 
[ 1003.213507] Info fld=0x0
[ 1003.213511] sd 7:0:0:0: [sdb] Add. Sense: No additional sense information
[ 1003.213521] sd 7:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 38 00 00 08 00
[ 1003.213542] end_request: I/O error, dev sdb, sector 56
[ 1003.213552] Buffer I/O error on device sdb, logical block 7
[ 1018.979686] sd 7:0:0:0: [sdb] Unhandled sense code
[ 1018.979690] sd 7:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_SENSE
[ 1018.979693] sd 7:0:0:0: [sdb] Sense Key : Hardware Error [current] 
[ 1018.979696] Info fld=0x0
[ 1018.979697] sd 7:0:0:0: [sdb] Add. Sense: No additional sense information
[ 1018.979701] sd 7:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 3f 00 00 01 00
[ 1018.979707] end_request: I/O error, dev sdb, sector 63
[ 1018.979711] Buffer I/O error on device sdb1, logical block 0
[ 1035.611984] sd 7:0:0:0: [sdb] Unhandled sense code
[ 1035.611993] sd 7:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_SENSE
[ 1035.612002] sd 7:0:0:0: [sdb] Sense Key : Hardware Error [current] 
[ 1035.612013] Info fld=0x0
[ 1035.612017] sd 7:0:0:0: [sdb] Add. Sense: No additional sense information
[ 1035.612027] sd 7:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 3f 00 00 01 00
[ 1035.612048] end_request: I/O error, dev sdb, sector 63
[ 1035.612059] Buffer I/O error on device sdb1, logical block 0
[ 1052.239108] sd 7:0:0:0: [sdb] Unhandled sense code
[ 1052.239118] sd 7:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_SENSE
[ 1052.239127] sd 7:0:0:0: [sdb] Sense Key : Hardware Error [current] 
[ 1052.239138] Info fld=0x0
[ 1052.239142] sd 7:0:0:0: [sdb] Add. Sense: No additional sense information
[ 1052.239152] sd 7:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 3f 00 00 01 00
[ 1052.239173] end_request: I/O error, dev sdb, sector 63
[ 1052.239184] Buffer I/O error on device sdb1, logical block 0
[ 1069.155487] sd 7:0:0:0: [sdb] Unhandled sense code
[ 1069.155496] sd 7:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_SENSE
[ 1069.155505] sd 7:0:0:0: [sdb] Sense Key : Hardware Error [current] 
[ 1069.155516] Info fld=0x0
[ 1069.155520] sd 7:0:0:0: [sdb] Add. Sense: No additional sense information
[ 1069.155530] sd 7:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 3f 00 00 01 00
[ 1069.155551] end_request: I/O error, dev sdb, sector 63
[ 1069.155561] Buffer I/O error on device sdb1, logical block 0
[ 1085.842739] sd 7:0:0:0: [sdb] Unhandled sense code
[ 1085.842747] sd 7:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_SENSE
[ 1085.842756] sd 7:0:0:0: [sdb] Sense Key : Hardware Error [current] 
[ 1085.842767] Info fld=0x0
[ 1085.842771] sd 7:0:0:0: [sdb] Add. Sense: No additional sense information
[ 1085.842781] sd 7:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 3f 00 00 01 00
[ 1085.842802] end_request: I/O error, dev sdb, sector 63
[ 1085.842813] Buffer I/O error on device sdb1, logical block 0
[ 1102.178608] sd 7:0:0:0: [sdb] Unhandled sense code
[ 1102.178611] sd 7:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_SENSE
[ 1102.178614] sd 7:0:0:0: [sdb] Sense Key : Hardware Error [current] 
[ 1102.178618] Info fld=0x0
[ 1102.178619] sd 7:0:0:0: [sdb] Add. Sense: No additional sense information
[ 1102.178622] sd 7:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 3f 00 00 01 00
[ 1102.178629] end_request: I/O error, dev sdb, sector 63
[ 1102.178633] Buffer I/O error on device sdb1, logical block 0
[ 1118.535499] sd 7:0:0:0: [sdb] Unhandled sense code
[ 1118.535508] sd 7:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_SENSE
[ 1118.535517] sd 7:0:0:0: [sdb] Sense Key : Hardware Error [current] 
[ 1118.535528] Info fld=0x0
[ 1118.535532] sd 7:0:0:0: [sdb] Add. Sense: No additional sense information
[ 1118.535542] sd 7:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 3f 00 00 01 00
[ 1118.535563] end_request: I/O error, dev sdb, sector 63
[ 1118.535573] Buffer I/O error on device sdb1, logical block 0
[ 1135.748095] sd 7:0:0:0: [sdb] Unhandled sense code
[ 1135.748099] sd 7:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_SENSE
[ 1135.748102] sd 7:0:0:0: [sdb] Sense Key : Hardware Error [current] 
[ 1135.748106] Info fld=0x0
[ 1135.748107] sd 7:0:0:0: [sdb] Add. Sense: No additional sense information
[ 1135.748110] sd 7:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 3f 00 00 01 00
[ 1135.748117] end_request: I/O error, dev sdb, sector 63
[ 1135.748121] Buffer I/O error on device sdb1, logical block 0
[ 1152.672603] sd 7:0:0:0: [sdb] Unhandled sense code
[ 1152.672607] sd 7:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_SENSE
[ 1152.672612] sd 7:0:0:0: [sdb] Sense Key : Hardware Error [current] 
[ 1152.672617] Info fld=0x0
[ 1152.672619] sd 7:0:0:0: [sdb] Add. Sense: No additional sense information
[ 1152.672624] sd 7:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 3f 00 00 01 00
[ 1152.672635] end_request: I/O error, dev sdb, sector 63
[ 1152.672641] Buffer I/O error on device sdb1, logical block 0
[ 1169.446849] sd 7:0:0:0: [sdb] Unhandled sense code
[ 1169.446852] sd 7:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_SENSE
[ 1169.446855] sd 7:0:0:0: [sdb] Sense Key : Hardware Error [current] 
[ 1169.446859] Info fld=0x0
[ 1169.446860] sd 7:0:0:0: [sdb] Add. Sense: No additional sense information
[ 1169.446863] sd 7:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 3f 00 00 01 00
[ 1169.446869] end_request: I/O error, dev sdb, sector 63
[ 1169.446873] Buffer I/O error on device sdb1, logical block 0
[ 1186.370233] sd 7:0:0:0: [sdb] Unhandled sense code
[ 1186.370238] sd 7:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_SENSE
[ 1186.370242] sd 7:0:0:0: [sdb] Sense Key : Hardware Error [current] 
[ 1186.370248] Info fld=0x0
[ 1186.370250] sd 7:0:0:0: [sdb] Add. Sense: No additional sense information
[ 1186.370255] sd 7:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 3f 00 00 01 00
[ 1186.370266] end_request: I/O error, dev sdb, sector 63
[ 1186.370272] Buffer I/O error on device sdb1, logical block 0

```

fdisk:

```

$ sudo fdisk -l /dev/sdb

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x96222946

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        3824    30716248+   c  W95 FAT32 (LBA)
/dev/sdb2            3825       60801   457667752+   f  W95 Ext'd (LBA)
/dev/sdb5            3825       60801   457667721    7  HPFS/NTFS

```

testdisk: analyzing the HD is very slow: 1 cylinder every 30sec for the first 60 cylinders, then it goes faster, 10 cylenders per second, and at 3200 it goes very slow again.

```

TestDisk 6.11, Data Recovery Utility, April 2009
Christophe GRENIER <grenier@cgsecurity.org>
http://www.cgsecurity.org

Disk /dev/sdb - 500 GB / 465 GiB - CHS 60802 255 63
Analyse cylinder     8/60801: 00%


```

```

Analyse cylinder  3268/60801: 05%
Read error at 3267/223/29 (lba=52498432)


```

testdisk boot on the first fartition:
```

Disk /dev/sdc - 500 GB / 465 GiB - CHS 60801 255 63
     Partition                  Start        End    Size in sectors
 1 P FAT32 LBA                0   1  1  3823 254 63   61432497

Boot sector
fat32_boot_sector: Can't read boot sector.
Bad

Backup boot sector
OK

First sectors (Boot code and partition information) are not identical.
Second sectors (cluster information) are not identical.
Third sectors (Second part of boot code) are not identical.

A valid FAT Boot sector must be present in order to access
any data; even if the partition is not bootable.

```

Yesterday I tried to check the file system but it stuck at 2% for several minutes. 

Any ideas? I surfed a little bit on the web but I didn't find anything useful for me.
I have about 30 GB of pictures on this HD, my last 10 years of pictures :(
Help please 

Thanks!!

---

