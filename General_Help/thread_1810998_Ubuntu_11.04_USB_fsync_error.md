---
title: "Ubuntu 11.04 USB fsync error"
date: 2011-07-24
forum: General Help
---

### Post by rtoepfer on 2011-07-24
I just bought a new USB storage disk.  At first the USB key was recognized by my system - Dell Inspiron 5150 Laptop running 11.04 Natty.  I tried to copy two directories to USB storage.  The OS gave an error that the device is read only.  After searching online I used chown to change the device permissions.  After this trying to copy to the device gives a fysnc error. I tried reformatting the device using the right click -> format and trying each different file system type but still get errors.  Now the system does not auto mount the device (I don't see the icon on desktop when USB is plugged into system).  I try to reformat via GParted but get a fsync error.  Does this mean my USB device is faulty?

GParted error:

GParted 0.7.0 --enable-libparted-dmraid

Libparted 2.3
Format /dev/sdb1 as ext2  00:00:00    ( ERROR )
     	
calibrate /dev/sdb1  00:00:00    ( SUCCESS )
     	
path: /dev/sdb1
start: 496
end: 4016127
size: 4015632 (1.91 GiB)
set partition type on /dev/sdb1  00:00:00    ( ERROR )
libparted messages    ( INFO )
     	
Error fsyncing/closing /dev/sdb: Input/output error
Input/output error during write on /dev/sdb
Error fsyncing/closing /dev/sdb: Input/output error

========================================



dmesg error:

```
randall@randall-Inspiron-N5010:/dev$ dmesg | grep -i "sdb"
[    3.833961] sd 6:0:0:0: [sdb] 4016128 512-byte logical blocks: (2.05 GB/1.91 GiB)
[    3.834569] sd 6:0:0:0: [sdb] Write Protect is off
[    3.834577] sd 6:0:0:0: [sdb] Mode Sense: 03 00 00 00
[    3.834582] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[    3.836959] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[    4.008820]  sdb: sdb1
[    4.010779] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[    4.010788] sd 6:0:0:0: [sdb] Attached SCSI removable disk
[  323.523123] sd 7:0:0:0: [sdb] 4016128 512-byte logical blocks: (2.05 GB/1.91 GiB)
[  323.523748] sd 7:0:0:0: [sdb] Write Protect is off
[  323.523754] sd 7:0:0:0: [sdb] Mode Sense: 03 00 00 00
[  323.523759] sd 7:0:0:0: [sdb] Assuming drive cache: write through
[  323.530126] sd 7:0:0:0: [sdb] Assuming drive cache: write through
[  323.702851]  sdb: sdb1
[  323.704864] sd 7:0:0:0: [sdb] Assuming drive cache: write through
[  323.704889] sd 7:0:0:0: [sdb] Attached SCSI removable disk
[  844.981700] sd 7:0:0:0: [sdb] Device not ready
[  844.981721] sd 7:0:0:0: [sdb]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  844.981731] sd 7:0:0:0: [sdb]  Sense Key : Not Ready [current] 
[  844.981758] sd 7:0:0:0: [sdb]  <<vendor>> ASC=0xff ASCQ=0xffASC=0xff <<vendor>> ASCQ=0xff
[  844.981787] sd 7:0:0:0: [sdb] CDB: Write(10): 2a 00 00 00 00 00 00 00 08 00
[  844.981819] end_request: I/O error, dev sdb, sector 0
[  844.981828] Buffer I/O error on device sdb, logical block 0
[  844.981845] lost page write due to I/O error on sdb
[  894.632632] sd 7:0:0:0: [sdb] Unhandled sense code
[  894.632642] sd 7:0:0:0: [sdb]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  894.632666] sd 7:0:0:0: [sdb]  Sense Key : Data Protect [current] 
[  894.632696] sd 7:0:0:0: [sdb]  Add. Sense: Write protected
[  894.632707] sd 7:0:0:0: [sdb] CDB: Write(10): 2a 00 00 00 02 70 00 00 08 00
[  894.632757] end_request: I/O error, dev sdb, sector 624
[  894.632767] Buffer I/O error on device sdb, logical block 78
[  894.632773] lost page write due to I/O error on sdb
[  894.648894] sd 7:0:0:0: [sdb] Unhandled sense code
[  894.648916] sd 7:0:0:0: [sdb]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  894.648924] sd 7:0:0:0: [sdb]  Sense Key : Data Protect [current] 
[  894.648951] sd 7:0:0:0: [sdb]  Add. Sense: Write protected
[  894.648975] sd 7:0:0:0: [sdb] CDB: Write(10): 2a 00 00 00 00 00 00 00 08 00
[  894.648993] end_request: I/O error, dev sdb, sector 0
[  894.649014] Buffer I/O error on device sdb, logical block 0
[  894.649019] lost page write due to I/O error on sdb
randall@randall-Inspiron-N5010:/dev$ clear

randall@randall-Inspiron-N5010:/dev$ dmesg | grep -i "sdb"
[    3.833961] sd 6:0:0:0: [sdb] 4016128 512-byte logical blocks: (2.05 GB/1.91 GiB)
[    3.834569] sd 6:0:0:0: [sdb] Write Protect is off
[    3.834577] sd 6:0:0:0: [sdb] Mode Sense: 03 00 00 00
[    3.834582] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[    3.836959] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[    4.008820]  sdb: sdb1
[    4.010779] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[    4.010788] sd 6:0:0:0: [sdb] Attached SCSI removable disk
[  323.523123] sd 7:0:0:0: [sdb] 4016128 512-byte logical blocks: (2.05 GB/1.91 GiB)
[  323.523748] sd 7:0:0:0: [sdb] Write Protect is off
[  323.523754] sd 7:0:0:0: [sdb] Mode Sense: 03 00 00 00
[  323.523759] sd 7:0:0:0: [sdb] Assuming drive cache: write through
[  323.530126] sd 7:0:0:0: [sdb] Assuming drive cache: write through
[  323.702851]  sdb: sdb1
[  323.704864] sd 7:0:0:0: [sdb] Assuming drive cache: write through
[  323.704889] sd 7:0:0:0: [sdb] Attached SCSI removable disk
[  844.981700] sd 7:0:0:0: [sdb] Device not ready
[  844.981721] sd 7:0:0:0: [sdb]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  844.981731] sd 7:0:0:0: [sdb]  Sense Key : Not Ready [current] 
[  844.981758] sd 7:0:0:0: [sdb]  <<vendor>> ASC=0xff ASCQ=0xffASC=0xff <<vendor>> ASCQ=0xff
[  844.981787] sd 7:0:0:0: [sdb] CDB: Write(10): 2a 00 00 00 00 00 00 00 08 00
[  844.981819] end_request: I/O error, dev sdb, sector 0
[  844.981828] Buffer I/O error on device sdb, logical block 0
[  844.981845] lost page write due to I/O error on sdb
[  894.632632] sd 7:0:0:0: [sdb] Unhandled sense code
[  894.632642] sd 7:0:0:0: [sdb]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  894.632666] sd 7:0:0:0: [sdb]  Sense Key : Data Protect [current] 
[  894.632696] sd 7:0:0:0: [sdb]  Add. Sense: Write protected
[  894.632707] sd 7:0:0:0: [sdb] CDB: Write(10): 2a 00 00 00 02 70 00 00 08 00
[  894.632757] end_request: I/O error, dev sdb, sector 624
[  894.632767] Buffer I/O error on device sdb, logical block 78
[  894.632773] lost page write due to I/O error on sdb
[  894.648894] sd 7:0:0:0: [sdb] Unhandled sense code
[  894.648916] sd 7:0:0:0: [sdb]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  894.648924] sd 7:0:0:0: [sdb]  Sense Key : Data Protect [current] 
[  894.648951] sd 7:0:0:0: [sdb]  Add. Sense: Write protected
[  894.648975] sd 7:0:0:0: [sdb] CDB: Write(10): 2a 00 00 00 00 00 00 00 08 00
[  894.648993] end_request: I/O error, dev sdb, sector 0
[  894.649014] Buffer I/O error on device sdb, logical block 0
[  894.649019] lost page write due to I/O error on sdb
randall@randall-Inspiron-N5010:/dev$ 
```

---

### Post by wolverine2k on 2012-08-13
Hi,

Did you find a solution to this error?

BR; Naresh

---

