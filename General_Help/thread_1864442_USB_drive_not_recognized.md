---
title: "USB drive not recognized"
date: 2011-10-19
forum: General Help
---

### Post by ghormax on 2011-10-19
I am running Ubuntu 10.04 on my netbook and this is the first time a USB stick has not been recognized. It is a 32GB sized stick from Maxflash. It works fine on another Windows notebook.

I cannot find the drive anywhere in the system:

dmesg | tail -n10
[ 3537.332349] sd 6:0:0:0: [sdd] Mode Sense: 03 00 00 00
[ 3537.332357] sd 6:0:0:0: [sdd] Assuming drive cache: write through
[ 3537.337948] sd 6:0:0:0: [sdd] Assuming drive cache: write through
[ 3537.337969]  sdd: sdd1
[ 3537.987424] sd 6:0:0:0: [sdd] Assuming drive cache: write through
[ 3537.987441] sd 6:0:0:0: [sdd] Attached SCSI removable disk
[ 3569.100549] usb 1-2: reset high speed USB device using ehci_hcd and address 7
[ 3600.101124] usb 1-2: reset high speed USB device using ehci_hcd and address 7
[ 3631.101152] usb 1-2: reset high speed USB device using ehci_hcd and address 7
[ 3662.100111] usb 1-2: reset high speed USB device using ehci_hcd and address 7

lsusb
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 0a5c:2150 Broadcom Corp. 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 010: ID 0011:7788  
Bus 001 Device 006: ID 0951:1607 Kingston Technology DataTraveler 100
Bus 001 Device 004: ID 0bda:0158 Realtek Semiconductor Corp. Mass Storage Device
Bus 001 Device 002: ID 090c:4371 Feiya Technology Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

The two USB devices listed are my Kingston 2GB stick and the card-reader.

Is this a problem with my Netbook or Ubuntu?

---

### Post by papibe on 2011-10-19
In my experience, Ubuntu doesn't do well with USB devices of different speeds. I can't use my relative old Maxtor USB disk (probably 1.0), at the same time than my other 2 more modern external disks (WD and Iomega).

What I do is unplug the 2 fastest disks, and just plug the old Maxtor.

Just some ideas,
Regards.

---

### Post by ghormax on 2011-10-19
The device is not even recognized when the other USB drive is disconnected or when the computer boots up.

---

### Post by ghormax on 2011-10-23
Actually this should be the USB drive: 

```
Bus 001 Device 008: ID 0011:7788 
```


Here is the output of lsusb with vs. without stick:

```
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 0a5c:2150 Broadcom Corp. 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 15ca:00c3 Textech International Ltd. Mini Optical Mouse
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 008: ID 0011:7788  
Bus 001 Device 004: ID 0bda:0158 Realtek Semiconductor Corp. Mass Storage Device
Bus 001 Device 002: ID 090c:4371 Feiya Technology Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```

```
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 0a5c:2150 Broadcom Corp. 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 15ca:00c3 Textech International Ltd. Mini Optical Mouse
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 004: ID 0bda:0158 Realtek Semiconductor Corp. Mass Storage Device
Bus 001 Device 002: ID 090c:4371 Feiya Technology Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```

---

### Post by ghormax on 2011-10-23
This is the output for dmesg | tail

```
[32907.100161] usb 1-1: reset high speed USB device using ehci_hcd and address 16
[32938.112115] usb 1-1: reset high speed USB device using ehci_hcd and address 16
[32938.328831] sd 14:0:0:0: [sdc] Unhandled error code
[32938.328847] sd 14:0:0:0: [sdc] Result: hostbyte=DID_ABORT driverbyte=DRIVER_OK
[32938.328864] sd 14:0:0:0: [sdc] CDB: Read(10): 28 00 03 8a 3f f8 00 00 01 00
[32938.328904] end_request: I/O error, dev sdc, sector 59391992
[32938.328923] Buffer I/O error on device sdc, logical block 7423999
[32969.112143] usb 1-1: reset high speed USB device using ehci_hcd and address 16
[33000.100112] usb 1-1: reset high speed USB device using ehci_hcd and address 16
[33031.100111] usb 1-1: reset high speed USB device using ehci_hcd and address 16
```

please, can anyone help?

---

