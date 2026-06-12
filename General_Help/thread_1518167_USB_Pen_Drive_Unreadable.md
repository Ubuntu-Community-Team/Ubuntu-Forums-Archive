---
title: "USB Pen Drive Unreadable"
date: 2010-06-26
forum: General Help
---

### Post by pi.theta on 2010-06-26
I used gparted to create 3 Primary Partitins on my 2GB Kingston Pen Drive. After that I used the following command to change the label of one of the partitions

```
mkfs.ext3 -L Grub2 /dec/sdb3
```

After this the pen drive has become unreadable. It gets listed as /dev/sdb but the partitions do not. The errors given by various programs are listed below:

dmesg O/P:
```
sd 6:0:0:0: [sdb] ASC=0x0 ASCQ=0x0
sd 6:0:0:0: [sdb] CDB: cdb[0]=0x28: 28 00 00 00 00 78 00 00 08 00
end_request: I/O error, dev sdb, sector 120
sd 6:0:0:0: [sdb] Unhandled sense code
sd 6:0:0:0: [sdb] Result: hostbyte=0x00 driverbyte=0x08
sd 6:0:0:0: [sdb] Sense Key : 0x3 [current] 
Info fld=0x0
sd 6:0:0:0: [sdb] ASC=0x0 ASCQ=0x0
sd 6:0:0:0: [sdb] CDB: cdb[0]=0x28: 28 00 00 00 00 78 00 00 08 00
end_request: I/O error, dev sdb, sector 120
sd 6:0:0:0: [sdb] Unhandled sense code
sd 6:0:0:0: [sdb] Result: hostbyte=0x00 driverbyte=0x08
sd 6:0:0:0: [sdb] Sense Key : 0x3 [current] 
Info fld=0x0
sd 6:0:0:0: [sdb] ASC=0x0 ASCQ=0x0
sd 6:0:0:0: [sdb] CDB: cdb[0]=0x28: 28 00 00 00 00 00 00 00 08 00
end_request: I/O error, dev sdb, sector 0
quiet_error: 2822 callbacks suppressed
Buffer I/O error on device sdb, logical block 0
Buffer I/O error on device sdb, logical block 1
Buffer I/O error on device sdb, logical block 2
Buffer I/O error on device sdb, logical block 3
Buffer I/O error on device sdb, logical block 4
Buffer I/O error on device sdb, logical block 5
Buffer I/O error on device sdb, logical block 6
Buffer I/O error on device sdb, logical block 7
sd 6:0:0:0: [sdb] Unhandled sense code
sd 6:0:0:0: [sdb] Result: hostbyte=0x00 driverbyte=0x08
sd 6:0:0:0: [sdb] Sense Key : 0x3 [current] 
Info fld=0x0
sd 6:0:0:0: [sdb] ASC=0x0 ASCQ=0x0
sd 6:0:0:0: [sdb] CDB: cdb[0]=0x28: 28 00 00 00 00 00 00 00 08 00
end_request: I/O error, dev sdb, sector 0
Buffer I/O error on device sdb, logical block 0
Buffer I/O error on device sdb, logical block 1
sd 6:0:0:0: [sdb] Unhandled sense code
sd 6:0:0:0: [sdb] Result: hostbyte=0x00 driverbyte=0x08
sd 6:0:0:0: [sdb] Sense Key : 0x3 [current] 
Info fld=0x0
sd 6:0:0:0: [sdb] ASC=0x0 ASCQ=0x0
sd 6:0:0:0: [sdb] CDB: cdb[0]=0x28: 28 00 00 00 00 00 00 00 08 00
end_request: I/O error, dev sdb, sector 0
sd 6:0:0:0: [sdb] Unhandled sense code
sd 6:0:0:0: [sdb] Result: hostbyte=0x00 driverbyte=0x08
sd 6:0:0:0: [sdb] Sense Key : 0x3 [current] 
Info fld=0x0
sd 6:0:0:0: [sdb] ASC=0x0 ASCQ=0x0
sd 6:0:0:0: [sdb] CDB: cdb[0]=0x28: 28 00 00 00 00 00 00 00 08 00
end_request: I/O error, dev sdb, sector 0
sd 6:0:0:0: [sdb] Unhandled sense code
sd 6:0:0:0: [sdb] Result: hostbyte=0x00 driverbyte=0x08
sd 6:0:0:0: [sdb] Sense Key : 0x3 [current] 
Info fld=0x0
sd 6:0:0:0: [sdb] ASC=0x0 ASCQ=0x0
sd 6:0:0:0: [sdb] CDB: cdb[0]=0x28: 28 00 00 00 00 00 00 00 08 00
end_request: I/O error, dev sdb, sector 0
sd 6:0:0:0: [sdb] Unhandled sense code
sd 6:0:0:0: [sdb] Result: hostbyte=0x00 driverbyte=0x08
sd 6:0:0:0: [sdb] Sense Key : 0x3 [current] 
Info fld=0x0
sd 6:0:0:0: [sdb] ASC=0x0 ASCQ=0x0
sd 6:0:0:0: [sdb] CDB: cdb[0]=0x28: 28 00 00 00 00 00 00 00 08 00
end_request: I/O error, dev sdb, sector 0
sd 6:0:0:0: [sdb] Unhandled sense code
sd 6:0:0:0: [sdb] Result: hostbyte=0x00 driverbyte=0x08
sd 6:0:0:0: [sdb] Sense Key : 0x3 [current] 
Info fld=0x0
sd 6:0:0:0: [sdb] ASC=0x0 ASCQ=0x0
sd 6:0:0:0: [sdb] CDB: cdb[0]=0x28: 28 00 00 00 00 10 00 00 08 00
end_request: I/O error, dev sdb, sector 16
sd 6:0:0:0: [sdb] Unhandled sense code
sd 6:0:0:0: [sdb] Result: hostbyte=0x00 driverbyte=0x08
sd 6:0:0:0: [sdb] Sense Key : 0x3 [current] 
Info fld=0x0
sd 6:0:0:0: [sdb] ASC=0x0 ASCQ=0x0
sd 6:0:0:0: [sdb] CDB: cdb[0]=0x28: 28 00 00 00 00 80 00 00 08 00
end_request: I/O error, dev sdb, sector 128
sd 6:0:0:0: [sdb] Unhandled sense code
sd 6:0:0:0: [sdb] Result: hostbyte=0x00 driverbyte=0x08
sd 6:0:0:0: [sdb] Sense Key : 0x3 [current] 
Info fld=0x0
sd 6:0:0:0: [sdb] ASC=0x0 ASCQ=0x0
sd 6:0:0:0: [sdb] CDB: cdb[0]=0x28: 28 00 00 00 00 80 00 00 08 00
end_request: I/O error, dev sdb, sector 128
sd 6:0:0:0: [sdb] Unhandled sense code
sd 6:0:0:0: [sdb] Result: hostbyte=0x00 driverbyte=0x08
sd 6:0:0:0: [sdb] Sense Key : 0x3 [current] 
Info fld=0x0
sd 6:0:0:0: [sdb] ASC=0x0 ASCQ=0x0
sd 6:0:0:0: [sdb] CDB: cdb[0]=0x28: 28 00 00 00 00 80 00 00 08 00
end_request: I/O error, dev sdb, sector 128
sd 6:0:0:0: [sdb] Unhandled sense code
sd 6:0:0:0: [sdb] Result: hostbyte=0x00 driverbyte=0x08
sd 6:0:0:0: [sdb] Sense Key : 0x3 [current] 
Info fld=0x0
sd 6:0:0:0: [sdb] ASC=0x0 ASCQ=0x0
sd 6:0:0:0: [sdb] CDB: cdb[0]=0x28: 28 00 00 00 00 10 00 00 08 00
end_request: I/O error, dev sdb, sector 16
sd 6:0:0:0: [sdb] Unhandled sense code
sd 6:0:0:0: [sdb] Result: hostbyte=0x00 driverbyte=0x08
sd 6:0:0:0: [sdb] Sense Key : 0x3 [current] 
Info fld=0x0
sd 6:0:0:0: [sdb] ASC=0x0 ASCQ=0x0
sd 6:0:0:0: [sdb] CDB: cdb[0]=0x28: 28 00 00 00 00 80 00 00 08 00
end_request: I/O error, dev sdb, sector 128
sd 6:0:0:0: [sdb] Unhandled sense code
sd 6:0:0:0: [sdb] Result: hostbyte=0x00 driverbyte=0x08
sd 6:0:0:0: [sdb] Sense Key : 0x3 [current] 
Info fld=0x0
sd 6:0:0:0: [sdb] ASC=0x0 ASCQ=0x0
sd 6:0:0:0: [sdb] CDB: cdb[0]=0x28: 28 00 00 00 00 40 00 00 08 00
end_request: I/O error, dev sdb, sector 64
sd 6:0:0:0: [sdb] Unhandled sense code
sd 6:0:0:0: [sdb] Result: hostbyte=0x00 driverbyte=0x08
sd 6:0:0:0: [sdb] Sense Key : 0x3 [current] 
Info fld=0x0
sd 6:0:0:0: [sdb] ASC=0x0 ASCQ=0x0
sd 6:0:0:0: [sdb] CDB: cdb[0]=0x28: 28 00 00 00 00 40 00 00 08 00
end_request: I/O error, dev sdb, sector 64
sd 6:0:0:0: [sdb] Unhandled sense code
sd 6:0:0:0: [sdb] Result: hostbyte=0x00 driverbyte=0x08
sd 6:0:0:0: [sdb] Sense Key : 0x3 [current] 
Info fld=0x0
sd 6:0:0:0: [sdb] ASC=0x0 ASCQ=0x0
sd 6:0:0:0: [sdb] CDB: cdb[0]=0x28: 28 00 00 00 00 40 00 00 08 00
end_request: I/O error, dev sdb, sector 64
sd 6:0:0:0: [sdb] Unhandled sense code
sd 6:0:0:0: [sdb] Result: hostbyte=0x00 driverbyte=0x08
sd 6:0:0:0: [sdb] Sense Key : 0x3 [current] 
Info fld=0x0
sd 6:0:0:0: [sdb] ASC=0x0 ASCQ=0x0
sd 6:0:0:0: [sdb] CDB: cdb[0]=0x28: 28 00 00 00 00 40 00 00 08 00
end_request: I/O error, dev sdb, sector 64
sd 6:0:0:0: [sdb] Unhandled sense code
sd 6:0:0:0: [sdb] Result: hostbyte=0x00 driverbyte=0x08
sd 6:0:0:0: [sdb] Sense Key : 0x3 [current] 
Info fld=0x0
sd 6:0:0:0: [sdb] ASC=0x0 ASCQ=0x0
sd 6:0:0:0: [sdb] CDB: cdb[0]=0x28: 28 00 00 00 00 40 00 00 08 00
end_request: I/O error, dev sdb, sector 64
sd 6:0:0:0: [sdb] Unhandled sense code
sd 6:0:0:0: [sdb] Result: hostbyte=0x00 driverbyte=0x08
sd 6:0:0:0: [sdb] Sense Key : 0x3 [current] 
Info fld=0x0
sd 6:0:0:0: [sdb] ASC=0x0 ASCQ=0x0
sd 6:0:0:0: [sdb] CDB: cdb[0]=0x28: 28 00 00 00 00 40 00 00 08 00
end_request: I/O error, dev sdb, sector 64
sd 6:0:0:0: [sdb] Unhandled sense code
sd 6:0:0:0: [sdb] Result: hostbyte=0x00 driverbyte=0x08
sd 6:0:0:0: [sdb] Sense Key : 0x3 [current] 
Info fld=0x0
sd 6:0:0:0: [sdb] ASC=0x0 ASCQ=0x0
sd 6:0:0:0: [sdb] CDB: cdb[0]=0x28: 28 00 00 00 00 40 00 00 08 00
end_request: I/O error, dev sdb, sector 64
sd 6:0:0:0: [sdb] Unhandled sense code
sd 6:0:0:0: [sdb] Result: hostbyte=0x00 driverbyte=0x08
sd 6:0:0:0: [sdb] Sense Key : 0x3 [current] 
Info fld=0x0
sd 6:0:0:0: [sdb] ASC=0x0 ASCQ=0x0
sd 6:0:0:0: [sdb] CDB: cdb[0]=0x28: 28 00 00 00 00 40 00 00 08 00
end_request: I/O error, dev sdb, sector 64
sd 6:0:0:0: [sdb] Unhandled sense code
sd 6:0:0:0: [sdb] Result: hostbyte=0x00 driverbyte=0x08
sd 6:0:0:0: [sdb] Sense Key : 0x3 [current] 
Info fld=0x0
sd 6:0:0:0: [sdb] ASC=0x0 ASCQ=0x0
sd 6:0:0:0: [sdb] CDB: cdb[0]=0x28: 28 00 00 00 00 40 00 00 08 00
end_request: I/O error, dev sdb, sector 64
sd 6:0:0:0: [sdb] Unhandled sense code
sd 6:0:0:0: [sdb] Result: hostbyte=0x00 driverbyte=0x08
sd 6:0:0:0: [sdb] Sense Key : 0x3 [current] 
Info fld=0x0
sd 6:0:0:0: [sdb] ASC=0x0 ASCQ=0x0
sd 6:0:0:0: [sdb] CDB: cdb[0]=0x28: 28 00 00 00 00 40 00 00 08 00
end_request: I/O error, dev sdb, sector 64
sd 6:0:0:0: [sdb] Unhandled sense code
sd 6:0:0:0: [sdb] Result: hostbyte=0x00 driverbyte=0x08
sd 6:0:0:0: [sdb] Sense Key : 0x3 [current] 
Info fld=0x0
sd 6:0:0:0: [sdb] ASC=0x0 ASCQ=0x0
sd 6:0:0:0: [sdb] CDB: cdb[0]=0x28: 28 00 00 00 01 00 00 00 08 00
end_request: I/O error, dev sdb, sector 256
sd 6:0:0:0: [sdb] Unhandled sense code
sd 6:0:0:0: [sdb] Result: hostbyte=0x00 driverbyte=0x08
sd 6:0:0:0: [sdb] Sense Key : 0x3 [current] 
Info fld=0x0
sd 6:0:0:0: [sdb] ASC=0x0 ASCQ=0x0
sd 6:0:0:0: [sdb] CDB: cdb[0]=0x28: 28 00 00 00 01 00 00 00 08 00
end_request: I/O error, dev sdb, sector 256
sd 6:0:0:0: [sdb] Unhandled sense code
sd 6:0:0:0: [sdb] Result: hostbyte=0x00 driverbyte=0x08
sd 6:0:0:0: [sdb] Sense Key : 0x3 [current] 
Info fld=0x0
sd 6:0:0:0: [sdb] ASC=0x0 ASCQ=0x0
sd 6:0:0:0: [sdb] CDB: cdb[0]=0x28: 28 00 00 00 01 08 00 00 08 00
end_request: I/O error, dev sdb, sector 264
sd 6:0:0:0: [sdb] Unhandled sense code
sd 6:0:0:0: [sdb] Result: hostbyte=0x00 driverbyte=0x08
sd 6:0:0:0: [sdb] Sense Key : 0x3 [current] 
Info fld=0x0
sd 6:0:0:0: [sdb] ASC=0x0 ASCQ=0x0
sd 6:0:0:0: [sdb] CDB: cdb[0]=0x28: 28 00 00 00 01 08 00 00 08 00
end_request: I/O error, dev sdb, sector 264
sd 6:0:0:0: [sdb] Unhandled sense code
sd 6:0:0:0: [sdb] Result: hostbyte=0x00 driverbyte=0x08
sd 6:0:0:0: [sdb] Sense Key : 0x3 [current] 
Info fld=0x0
sd 6:0:0:0: [sdb] ASC=0x0 ASCQ=0x0
sd 6:0:0:0: [sdb] CDB: cdb[0]=0x28: 28 00 00 00 01 10 00 00 08 00
end_request: I/O error, dev sdb, sector 272
sd 6:0:0:0: [sdb] Unhandled sense code
sd 6:0:0:0: [sdb] Result: hostbyte=0x00 driverbyte=0x08
sd 6:0:0:0: [sdb] Sense Key : 0x3 [current] 
Info fld=0x0
sd 6:0:0:0: [sdb] ASC=0x0 ASCQ=0x0
sd 6:0:0:0: [sdb] CDB: cdb[0]=0x28: 28 00 00 00 01 10 00 00 08 00
end_request: I/O error, dev sdb, sector 272
sd 6:0:0:0: [sdb] Unhandled sense code
sd 6:0:0:0: [sdb] Result: hostbyte=0x00 driverbyte=0x08
sd 6:0:0:0: [sdb] Sense Key : 0x3 [current] 
Info fld=0x0
sd 6:0:0:0: [sdb] ASC=0x0 ASCQ=0x0
sd 6:0:0:0: [sdb] CDB: cdb[0]=0x28: 28 00 00 00 03 00 00 00 08 00
end_request: I/O error, dev sdb, sector 768
sd 6:0:0:0: [sdb] Unhandled sense code
sd 6:0:0:0: [sdb] Result: hostbyte=0x00 driverbyte=0x08
sd 6:0:0:0: [sdb] Sense Key : 0x3 [current] 
Info fld=0x0
sd 6:0:0:0: [sdb] ASC=0x0 ASCQ=0x0
sd 6:0:0:0: [sdb] CDB: cdb[0]=0x28: 28 00 00 00 03 00 00 00 08 00
end_request: I/O error, dev sdb, sector 768
sd 6:0:0:0: [sdb] Unhandled sense code
sd 6:0:0:0: [sdb] Result: hostbyte=0x00 driverbyte=0x08
sd 6:0:0:0: [sdb] Sense Key : 0x3 [current] 
Info fld=0x0
sd 6:0:0:0: [sdb] ASC=0x0 ASCQ=0x0
sd 6:0:0:0: [sdb] CDB: cdb[0]=0x28: 28 00 00 00 03 08 00 00 08 00
end_request: I/O error, dev sdb, sector 776
sd 6:0:0:0: [sdb] Unhandled sense code
sd 6:0:0:0: [sdb] Result: hostbyte=0x00 driverbyte=0x08
sd 6:0:0:0: [sdb] Sense Key : 0x3 [current] 
Info fld=0x0
sd 6:0:0:0: [sdb] ASC=0x0 ASCQ=0x0
sd 6:0:0:0: [sdb] CDB: cdb[0]=0x28: 28 00 00 00 03 08 00 00 08 00
end_request: I/O error, dev sdb, sector 776
sd 6:0:0:0: [sdb] Unhandled sense code
sd 6:0:0:0: [sdb] Result: hostbyte=0x00 driverbyte=0x08
sd 6:0:0:0: [sdb] Sense Key : 0x3 [current] 
Info fld=0x0
sd 6:0:0:0: [sdb] ASC=0x0 ASCQ=0x0
sd 6:0:0:0: [sdb] CDB: cdb[0]=0x28: 28 00 00 00 03 10 00 00 08 00
end_request: I/O error, dev sdb, sector 784
sd 6:0:0:0: [sdb] Unhandled sense code
sd 6:0:0:0: [sdb] Result: hostbyte=0x00 driverbyte=0x08
sd 6:0:0:0: [sdb] Sense Key : 0x3 [current] 
Info fld=0x0
sd 6:0:0:0: [sdb] ASC=0x0 ASCQ=0x0
sd 6:0:0:0: [sdb] CDB: cdb[0]=0x28: 28 00 00 00 03 10 00 00 08 00
end_request: I/O error, dev sdb, sector 784
sd 6:0:0:0: [sdb] Unhandled sense code
sd 6:0:0:0: [sdb] Result: hostbyte=0x00 driverbyte=0x08
sd 6:0:0:0: [sdb] Sense Key : 0x3 [current] 
Info fld=0x0
sd 6:0:0:0: [sdb] ASC=0x0 ASCQ=0x0
sd 6:0:0:0: [sdb] CDB: cdb[0]=0x28: 28 00 00 00 00 00 00 00 08 00
end_request: I/O error, dev sdb, sector 0
sd 6:0:0:0: [sdb] Unhandled sense code
sd 6:0:0:0: [sdb] Result: hostbyte=0x00 driverbyte=0x08
sd 6:0:0:0: [sdb] Sense Key : 0x3 [current] 
Info fld=0x0
sd 6:0:0:0: [sdb] ASC=0x0 ASCQ=0x0
sd 6:0:0:0: [sdb] CDB: cdb[0]=0x28: 28 00 00 00 00 00 00 00 08 00
end_request: I/O error, dev sdb, sector 0
sd 6:0:0:0: [sdb] Unhandled sense code
sd 6:0:0:0: [sdb] Result: hostbyte=0x00 driverbyte=0x08
sd 6:0:0:0: [sdb] Sense Key : 0x3 [current] 
Info fld=0x0
sd 6:0:0:0: [sdb] ASC=0x0 ASCQ=0x0
sd 6:0:0:0: [sdb] CDB: cdb[0]=0x28: 28 00 00 00 00 00 00 00 08 00
end_request: I/O error, dev sdb, sector 0
sd 6:0:0:0: [sdb] Unhandled sense code
sd 6:0:0:0: [sdb] Result: hostbyte=0x00 driverbyte=0x08
sd 6:0:0:0: [sdb] Sense Key : 0x3 [current] 
Info fld=0x0
sd 6:0:0:0: [sdb] ASC=0x0 ASCQ=0x0
sd 6:0:0:0: [sdb] CDB: cdb[0]=0x28: 28 00 00 00 00 00 00 00 08 00
end_request: I/O error, dev sdb, sector 0
sd 6:0:0:0: [sdb] Unhandled sense code
sd 6:0:0:0: [sdb] Result: hostbyte=0x00 driverbyte=0x08
sd 6:0:0:0: [sdb] Sense Key : 0x3 [current] 
Info fld=0x0
sd 6:0:0:0: [sdb] ASC=0x0 ASCQ=0x0
sd 6:0:0:0: [sdb] CDB: cdb[0]=0x28: 28 00 00 00 00 00 00 00 08 00
end_request: I/O error, dev sdb, sector 0
sd 6:0:0:0: [sdb] Unhandled sense code
sd 6:0:0:0: [sdb] Result: hostbyte=0x00 driverbyte=0x08
sd 6:0:0:0: [sdb] Sense Key : 0x3 [current] 
Info fld=0x0
sd 6:0:0:0: [sdb] ASC=0x0 ASCQ=0x0
sd 6:0:0:0: [sdb] CDB: cdb[0]=0x28: 28 00 00 00 00 10 00 00 08 00
end_request: I/O error, dev sdb, sector 16
sd 6:0:0:0: [sdb] Unhandled sense code
sd 6:0:0:0: [sdb] Result: hostbyte=0x00 driverbyte=0x08
sd 6:0:0:0: [sdb] Sense Key : 0x3 [current] 
Info fld=0x0
sd 6:0:0:0: [sdb] ASC=0x0 ASCQ=0x0
sd 6:0:0:0: [sdb] CDB: cdb[0]=0x28: 28 00 00 00 00 00 00 00 08 00
end_request: I/O error, dev sdb, sector 0
sd 6:0:0:0: [sdb] Unhandled sense code
sd 6:0:0:0: [sdb] Result: hostbyte=0x00 driverbyte=0x08
sd 6:0:0:0: [sdb] Sense Key : 0x3 [current] 
Info fld=0x0
sd 6:0:0:0: [sdb] ASC=0x0 ASCQ=0x0
sd 6:0:0:0: [sdb] CDB: cdb[0]=0x28: 28 00 00 00 00 00 00 00 08 00
end_request: I/O error, dev sdb, sector 0
sd 6:0:0:0: [sdb] Unhandled sense code
sd 6:0:0:0: [sdb] Result: hostbyte=0x00 driverbyte=0x08
sd 6:0:0:0: [sdb] Sense Key : 0x3 [current] 
Info fld=0x0
sd 6:0:0:0: [sdb] ASC=0x0 ASCQ=0x0
sd 6:0:0:0: [sdb] CDB: cdb[0]=0x28: 28 00 00 00 00 00 00 00 08 00
end_request: I/O error, dev sdb, sector 0
sd 6:0:0:0: [sdb] Unhandled sense code
sd 6:0:0:0: [sdb] Result: hostbyte=0x00 driverbyte=0x08
sd 6:0:0:0: [sdb] Sense Key : 0x3 [current] 
Info fld=0x0
sd 6:0:0:0: [sdb] ASC=0x0 ASCQ=0x0
sd 6:0:0:0: [sdb] CDB: cdb[0]=0x28: 28 00 00 00 00 00 00 00 08 00
end_request: I/O error, dev sdb, sector 0
sd 6:0:0:0: [sdb] Unhandled sense code
sd 6:0:0:0: [sdb] Result: hostbyte=0x00 driverbyte=0x08
sd 6:0:0:0: [sdb] Sense Key : 0x3 [current] 
Info fld=0x0
sd 6:0:0:0: [sdb] ASC=0x0 ASCQ=0x0
sd 6:0:0:0: [sdb] CDB: cdb[0]=0x28: 28 00 00 00 00 00 00 00 08 00
end_request: I/O error, dev sdb, sector 0
sd 6:0:0:0: [sdb] Unhandled sense code
sd 6:0:0:0: [sdb] Result: hostbyte=0x00 driverbyte=0x08
sd 6:0:0:0: [sdb] Sense Key : 0x3 [current] 
Info fld=0x0
sd 6:0:0:0: [sdb] ASC=0x0 ASCQ=0x0
sd 6:0:0:0: [sdb] CDB: cdb[0]=0x28: 28 00 00 00 00 00 00 00 08 00
end_request: I/O error, dev sdb, sector 0
sd 6:0:0:0: [sdb] Unhandled sense code
sd 6:0:0:0: [sdb] Result: hostbyte=0x00 driverbyte=0x08
sd 6:0:0:0: [sdb] Sense Key : 0x3 [current] 
Info fld=0x0
sd 6:0:0:0: [sdb] ASC=0x0 ASCQ=0x0
sd 6:0:0:0: [sdb] CDB: cdb[0]=0x28: 28 00 00 00 00 00 00 00 08 00
end_request: I/O error, dev sdb, sector 0
sd 6:0:0:0: [sdb] Unhandled sense code
sd 6:0:0:0: [sdb] Result: hostbyte=0x00 driverbyte=0x08
sd 6:0:0:0: [sdb] Sense Key : 0x3 [current] 
Info fld=0x0
sd 6:0:0:0: [sdb] ASC=0x0 ASCQ=0x0
sd 6:0:0:0: [sdb] CDB: cdb[0]=0x28: 28 00 00 00 00 00 00 00 08 00
end_request: I/O error, dev sdb, sector 0
sd 6:0:0:0: [sdb] Unhandled sense code
sd 6:0:0:0: [sdb] Result: hostbyte=0x00 driverbyte=0x08
sd 6:0:0:0: [sdb] Sense Key : 0x3 [current] 
Info fld=0x0
sd 6:0:0:0: [sdb] ASC=0x0 ASCQ=0x0
sd 6:0:0:0: [sdb] CDB: cdb[0]=0x28: 28 00 00 00 00 00 00 00 08 00
end_request: I/O error, dev sdb, sector 0
sd 6:0:0:0: [sdb] Unhandled sense code
sd 6:0:0:0: [sdb] Result: hostbyte=0x00 driverbyte=0x08
sd 6:0:0:0: [sdb] Sense Key : 0x3 [current] 
Info fld=0x0
sd 6:0:0:0: [sdb] ASC=0x0 ASCQ=0x0
sd 6:0:0:0: [sdb] CDB: cdb[0]=0x28: 28 00 00 00 00 00 00 00 08 00
end_request: I/O error, dev sdb, sector 0
sd 6:0:0:0: [sdb] Unhandled sense code
sd 6:0:0:0: [sdb] Result: hostbyte=0x00 driverbyte=0x08
sd 6:0:0:0: [sdb] Sense Key : 0x3 [current] 
Info fld=0x0
sd 6:0:0:0: [sdb] ASC=0x0 ASCQ=0x0
sd 6:0:0:0: [sdb] CDB: cdb[0]=0x28: 28 00 00 00 00 00 00 00 08 00
end_request: I/O error, dev sdb, sector 0
sd 6:0:0:0: [sdb] Unhandled sense code
sd 6:0:0:0: [sdb] Result: hostbyte=0x00 driverbyte=0x08
sd 6:0:0:0: [sdb] Sense Key : 0x3 [current] 
Info fld=0x0
sd 6:0:0:0: [sdb] ASC=0x0 ASCQ=0x0
sd 6:0:0:0: [sdb] CDB: cdb[0]=0x28: 28 00 00 00 00 00 00 00 08 00
end_request: I/O error, dev sdb, sector 0
sd 6:0:0:0: [sdb] Unhandled sense code
sd 6:0:0:0: [sdb] Result: hostbyte=0x00 driverbyte=0x08
sd 6:0:0:0: [sdb] Sense Key : 0x3 [current] 
Info fld=0x0
sd 6:0:0:0: [sdb] ASC=0x0 ASCQ=0x0
sd 6:0:0:0: [sdb] CDB: cdb[0]=0x28: 28 00 00 00 00 80 00 00 08 00
end_request: I/O error, dev sdb, sector 128
sd 6:0:0:0: [sdb] Unhandled sense code
sd 6:0:0:0: [sdb] Result: hostbyte=0x00 driverbyte=0x08
sd 6:0:0:0: [sdb] Sense Key : 0x3 [current] 
Info fld=0x0
sd 6:0:0:0: [sdb] ASC=0x0 ASCQ=0x0
sd 6:0:0:0: [sdb] CDB: cdb[0]=0x28: 28 00 00 00 00 80 00 00 08 00
end_request: I/O error, dev sdb, sector 128
sd 6:0:0:0: [sdb] Unhandled sense code
sd 6:0:0:0: [sdb] Result: hostbyte=0x00 driverbyte=0x08
sd 6:0:0:0: [sdb] Sense Key : 0x3 [current] 
Info fld=0x0
sd 6:0:0:0: [sdb] ASC=0x0 ASCQ=0x0
sd 6:0:0:0: [sdb] CDB: cdb[0]=0x28: 28 00 00 00 00 10 00 00 08 00
end_request: I/O error, dev sdb, sector 16
sd 6:0:0:0: [sdb] Unhandled sense code
sd 6:0:0:0: [sdb] Result: hostbyte=0x00 driverbyte=0x08
sd 6:0:0:0: [sdb] Sense Key : 0x3 [current] 
Info fld=0x0
sd 6:0:0:0: [sdb] ASC=0x0 ASCQ=0x0
sd 6:0:0:0: [sdb] CDB: cdb[0]=0x28: 28 00 00 00 00 00 00 00 08 00
end_request: I/O error, dev sdb, sector 0
sd 6:0:0:0: [sdb] Unhandled sense code
sd 6:0:0:0: [sdb] Result: hostbyte=0x00 driverbyte=0x08
sd 6:0:0:0: [sdb] Sense Key : 0x3 [current] 
Info fld=0x0
sd 6:0:0:0: [sdb] ASC=0x0 ASCQ=0x0
sd 6:0:0:0: [sdb] CDB: cdb[0]=0x28: 28 00 00 00 00 00 00 00 08 00
end_request: I/O error, dev sdb, sector 0
sd 6:0:0:0: [sdb] Unhandled sense code
sd 6:0:0:0: [sdb] Result: hostbyte=0x00 driverbyte=0x08
sd 6:0:0:0: [sdb] Sense Key : 0x3 [current] 
Info fld=0x0
sd 6:0:0:0: [sdb] ASC=0x0 ASCQ=0x0
sd 6:0:0:0: [sdb] CDB: cdb[0]=0x28: 28 00 00 00 00 08 00 00 08 00
end_request: I/O error, dev sdb, sector 8
sd 6:0:0:0: [sdb] Unhandled sense code
sd 6:0:0:0: [sdb] Result: hostbyte=0x00 driverbyte=0x08
sd 6:0:0:0: [sdb] Sense Key : 0x3 [current] 
Info fld=0x0
sd 6:0:0:0: [sdb] ASC=0x0 ASCQ=0x0
sd 6:0:0:0: [sdb] CDB: cdb[0]=0x28: 28 00 00 00 00 10 00 00 08 00
end_request: I/O error, dev sdb, sector 16
sd 6:0:0:0: [sdb] Unhandled sense code
sd 6:0:0:0: [sdb] Result: hostbyte=0x00 driverbyte=0x08
sd 6:0:0:0: [sdb] Sense Key : 0x3 [current] 
Info fld=0x0
sd 6:0:0:0: [sdb] ASC=0x0 ASCQ=0x0
sd 6:0:0:0: [sdb] CDB: cdb[0]=0x28: 28 00 00 00 00 00 00 00 08 00
end_request: I/O error, dev sdb, sector 0
sd 6:0:0:0: [sdb] Unhandled sense code
sd 6:0:0:0: [sdb] Result: hostbyte=0x00 driverbyte=0x08
sd 6:0:0:0: [sdb] Sense Key : 0x3 [current] 
Info fld=0x0
sd 6:0:0:0: [sdb] ASC=0x0 ASCQ=0x0
sd 6:0:0:0: [sdb] CDB: cdb[0]=0x28: 28 00 00 00 00 00 00 00 08 00
end_request: I/O error, dev sdb, sector 0
sd 6:0:0:0: [sdb] Unhandled sense code
sd 6:0:0:0: [sdb] Result: hostbyte=0x00 driverbyte=0x08
sd 6:0:0:0: [sdb] Sense Key : 0x3 [current] 
Info fld=0x0
sd 6:0:0:0: [sdb] ASC=0x0 ASCQ=0x0
sd 6:0:0:0: [sdb] CDB: cdb[0]=0x28: 28 00 00 00 00 00 00 00 08 00
end_request: I/O error, dev sdb, sector 0
sd 6:0:0:0: [sdb] Unhandled sense code
sd 6:0:0:0: [sdb] Result: hostbyte=0x00 driverbyte=0x08
sd 6:0:0:0: [sdb] Sense Key : 0x3 [current] 
Info fld=0x0
sd 6:0:0:0: [sdb] ASC=0x0 ASCQ=0x0
sd 6:0:0:0: [sdb] CDB: cdb[0]=0x28: 28 00 00 00 00 00 00 00 08 00
end_request: I/O error, dev sdb, sector 0
sd 6:0:0:0: [sdb] Unhandled sense code
sd 6:0:0:0: [sdb] Result: hostbyte=0x00 driverbyte=0x08
sd 6:0:0:0: [sdb] Sense Key : 0x3 [current] 
Info fld=0x0
sd 6:0:0:0: [sdb] ASC=0x0 ASCQ=0x0
sd 6:0:0:0: [sdb] CDB: cdb[0]=0x28: 28 00 00 00 00 00 00 00 08 00
end_request: I/O error, dev sdb, sector 0
sd 6:0:0:0: [sdb] Unhandled sense code
sd 6:0:0:0: [sdb] Result: hostbyte=0x00 driverbyte=0x08
sd 6:0:0:0: [sdb] Sense Key : 0x3 [current] 
Info fld=0x0
sd 6:0:0:0: [sdb] ASC=0x0 ASCQ=0x0
sd 6:0:0:0: [sdb] CDB: cdb[0]=0x28: 28 00 00 00 00 00 00 00 08 00
end_request: I/O error, dev sdb, sector 0
sd 6:0:0:0: [sdb] Unhandled sense code
sd 6:0:0:0: [sdb] Result: hostbyte=0x00 driverbyte=0x08
sd 6:0:0:0: [sdb] Sense Key : 0x3 [current] 
Info fld=0x0
sd 6:0:0:0: [sdb] ASC=0x0 ASCQ=0x0
sd 6:0:0:0: [sdb] CDB: cdb[0]=0x28: 28 00 00 00 00 08 00 00 08 00
end_request: I/O error, dev sdb, sector 8
sd 6:0:0:0: [sdb] Unhandled sense code
sd 6:0:0:0: [sdb] Result: hostbyte=0x00 driverbyte=0x08
sd 6:0:0:0: [sdb] Sense Key : 0x3 [current] 
Info fld=0x0
sd 6:0:0:0: [sdb] ASC=0x0 ASCQ=0x0
sd 6:0:0:0: [sdb] CDB: cdb[0]=0x28: 28 00 00 00 00 80 00 00 08 00
end_request: I/O error, dev sdb, sector 128
sd 6:0:0:0: [sdb] Unhandled sense code
sd 6:0:0:0: [sdb] Result: hostbyte=0x00 driverbyte=0x08
sd 6:0:0:0: [sdb] Sense Key : 0x3 [current] 
Info fld=0x0
sd 6:0:0:0: [sdb] ASC=0x0 ASCQ=0x0
sd 6:0:0:0: [sdb] CDB: cdb[0]=0x28: 28 00 00 00 00 00 00 00 08 00
end_request: I/O error, dev sdb, sector 0
sd 6:0:0:0: [sdb] Unhandled sense code
sd 6:0:0:0: [sdb] Result: hostbyte=0x00 driverbyte=0x08
sd 6:0:0:0: [sdb] Sense Key : 0x3 [current] 
Info fld=0x0
sd 6:0:0:0: [sdb] ASC=0x0 ASCQ=0x0
sd 6:0:0:0: [sdb] CDB: cdb[0]=0x28: 28 00 00 00 00 00 00 00 08 00
end_request: I/O error, dev sdb, sector 0
sd 6:0:0:0: [sdb] Unhandled sense code
sd 6:0:0:0: [sdb] Result: hostbyte=0x00 driverbyte=0x08
sd 6:0:0:0: [sdb] Sense Key : 0x3 [current] 
Info fld=0x0
sd 6:0:0:0: [sdb] ASC=0x0 ASCQ=0x0
sd 6:0:0:0: [sdb] CDB: cdb[0]=0x28: 28 00 00 00 10 00 00 00 08 00
end_request: I/O error, dev sdb, sector 4096
```


fdisk:
```
[theta@boolean-pc ~]$ fdisk /dev/sdb
Unable to read /dev/sdb

```


sfdisk:
```
[theta@boolean-pc ~]$ sudo sfdisk /dev/sdb
Password: 
Checking that no-one is using this disk right now ...
BLKRRPART: Input/output error
OK

Disk /dev/sdb: 1905 cylinders, 64 heads, 32 sectors/track
read: Input/output error

sfdisk: read error on /dev/sdb - cannot read sector 0
 /dev/sdb: unrecognized partition table type
Old situation:
No partitions found
Input in the following format; absent fields get a default value.
<start> <size> <type [E,S,L,X,hex]> <bootable [-,*]> <c,h,s> <c,h,s>
Usually you only need to specify <start> and <size> (and perhaps <type>).

/dev/sdb1 :
/dev/sdb1          0+   1904    1905-   1950719+  83  Linux
/dev/sdb2 :
/dev/sdb2          0       -       0          0    0  Empty
/dev/sdb3 :
/dev/sdb3          0       -       0          0    0  Empty
/dev/sdb4 :
/dev/sdb4          0       -       0          0    0  Empty
New situation:
Units = cylinders of 1048576 bytes, blocks of 1024 bytes, counting from 0

   Device Boot Start     End   #cyls    #blocks   Id  System
/dev/sdb1          0+   1904    1905-   1950719+  83  Linux
/dev/sdb2          0       -       0          0    0  Empty
/dev/sdb3          0       -       0          0    0  Empty
/dev/sdb4          0       -       0          0    0  Empty
Warning: no primary partition is marked bootable (active)
This does not matter for LILO, but the DOS MBR will not boot this disk.
Do you want to write this to disk? [ynq] y
read: Input/output error

sfdisk: read error on /dev/sdb - cannot read sector 0
Re-reading the partition table ...
BLKRRPART: Input/output error

If you created or changed a DOS partition, /dev/foo7, say, then use dd(1)
to zero the first 512 bytes:  dd if=/dev/zero of=/dev/foo7 bs=512 count=1
(See fdisk(8).)

```

I tried rewriting the partition table using testdisk but was of no avail. How can just labeling a partition cause a pen drive to crash?

---

