---
title: "External Hard Drive won't show up in GUI"
date: 2012-05-21
forum: General Help
---

### Post by davestrrr on 2012-05-21
Hi, I am running Ubuntu 10.04 on an HP desktop, and I have used a Seagate Expansion Portable drive with it numerous times. I was transferring some files between two computers, and I left the drive plugged in overnight. I then ejected it and tried to plug it into another computer. No response. Now, it is not accessible from the GUI, or at least doesn't seem to mount on its own. If I run lsusb:

```
$ lsusb
Bus 002 Device 003: ID 05d5:0624 Super Gate Technology Co., Ltd 
Bus 002 Device 002: ID 093a:2510 Pixart Imaging, Inc. Hama Optical Mouse
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 006: ID 0bc2:2300 Seagate RSS LLC 
Bus 001 Device 004: ID 058f:6366 Alcor Micro Corp. Multi Flash Reader
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

It shows up as Device 006. Then when I clear dmesg with:

```

sudo dmesg -c

```

and then plug the drive, in and check dmesg again, I get this output: 

```
$ sudo dmesg 
[  218.652807] usb 1-8: USB disconnect, address 5
[  218.660528] sd 5:0:0:0: [sdc] Unhandled error code
[  218.660536] sd 5:0:0:0: [sdc] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK
[  218.660546] sd 5:0:0:0: [sdc] CDB: Read(10): 28 00 00 00 00 18 00 00 08 00
[  218.660565] end_request: I/O error, dev sdc, sector 24
[  218.660575] __ratelimit: 78 callbacks suppressed
[  218.660581] Buffer I/O error on device sdc, logical block 24
[  218.660589] Buffer I/O error on device sdc, logical block 25
[  218.660595] Buffer I/O error on device sdc, logical block 26
[  218.660600] Buffer I/O error on device sdc, logical block 27
[  218.660606] Buffer I/O error on device sdc, logical block 28
[  218.660611] Buffer I/O error on device sdc, logical block 29
[  218.660617] Buffer I/O error on device sdc, logical block 30
[  218.660622] Buffer I/O error on device sdc, logical block 31
[  218.660750]  unable to read partition table
[  218.661060] sd 5:0:0:0: [sdc] READ CAPACITY failed
[  218.661065] sd 5:0:0:0: [sdc] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK
[  218.661073] sd 5:0:0:0: [sdc] Sense not available.
[  218.661099] sd 5:0:0:0: [sdc] Assuming drive cache: write through
[  218.661106] sd 5:0:0:0: [sdc] Attached SCSI disk
```


Indicating that clearly there is something wrong with accessing the drive/getting some sort of I/O error. I don't know enough to know how to interpret all of this. I actually tried the drive on two different computers, bot h ubuntu, and got the same symptom of not being able to see the drive in the GUI/doesn't seem to be mounted in /media as it usually is. Any help in manually mounting this thing or fixing it?

---

### Post by dcstar on 2012-05-22
> **davestrrr said:**
> 
............
and then plug the drive, in and check dmesg again, I get this output: 

```
$ sudo dmesg 
[  218.652807] usb 1-8: USB disconnect, address 5
[  218.660528] sd 5:0:0:0: [sdc] Unhandled error code
[  218.660536] sd 5:0:0:0: [sdc] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK
[  218.660546] sd 5:0:0:0: [sdc] CDB: Read(10): 28 00 00 00 00 18 00 00 08 00
[  218.660565] end_request: I/O error, dev sdc, sector 24
[  218.660575] __ratelimit: 78 callbacks suppressed
[  218.660581] Buffer I/O error on device sdc, logical block 24
[  218.660589] Buffer I/O error on device sdc, logical block 25
[  218.660595] Buffer I/O error on device sdc, logical block 26
[  218.660600] Buffer I/O error on device sdc, logical block 27
[  218.660606] Buffer I/O error on device sdc, logical block 28
[  218.660611] Buffer I/O error on device sdc, logical block 29
[  218.660617] Buffer I/O error on device sdc, logical block 30
[  218.660622] Buffer I/O error on device sdc, logical block 31
[  218.660750]  unable to read partition table
[  218.661060] sd 5:0:0:0: [sdc] READ CAPACITY failed
[  218.661065] sd 5:0:0:0: [sdc] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK
[  218.661073] sd 5:0:0:0: [sdc] Sense not available.
[  218.661099] sd 5:0:0:0: [sdc] Assuming drive cache: write through
[  218.661106] sd 5:0:0:0: [sdc] Attached SCSI disk
```


Indicating that clearly there is something wrong with accessing the drive/getting some sort of I/O error. I don't know enough to know how to interpret all of this. I actually tried the drive on two different computers, bot h ubuntu, and got the same symptom of not being able to see the drive in the GUI/doesn't seem to be mounted in /media as it usually is. Any help in manually mounting this thing or fixing it?

The drive is faulty, possibly unrecoverable.

Use the testdisk package or a data recovery CD to try and recover some of the data on it.

---

