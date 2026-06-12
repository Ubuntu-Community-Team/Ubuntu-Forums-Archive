---
title: "Banshee: LG GD330 not detected as device"
date: 2011-08-09
forum: General Help
---

### Post by astrobob.tk on 2011-08-09
Hey there,

I have tried connecting an LG GD330 mobile in both "Mass Storage" & "Data Service" but in either cases it does not appear in bansheee nor even in rhythmbox.

Anyone have any idea why ?

thanks

---

### Post by astrobob.tk on 2011-08-22
bump

---

### Post by wurzzero on 2011-09-08
Can you access it through nautilus?

---

### Post by astrobob.tk on 2011-09-09
> **wurzzero said:**
> Can you access it through nautilus?

No. I can't find any icon or link to it.

Besides; when it is in "Data Service" mode (asks me when usb is connected), I see

```
$ lsusb
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
**Bus 006 Device 003: ID 1004:6016 LG Electronics, Inc. **
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 05ca:18a0 Ricoh Co., Ltd 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```

But when in "Mass Storage" mode,

```
$ lsusb
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 004: ID 0104:6022  
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 05ca:18a0 Ricoh Co., Ltd
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```

what's going on ?

---

### Post by GerryB on 2011-09-09
Is there a memory card in it?

---

### Post by astrobob.tk on 2011-09-09
> **GerryB said:**
> Is there a memory card in it?

Yup; 4GB micro

Just removed it & reconnect in "Mass Storage" & got:

```
$ lsusb
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 004: ID 0104:6022  
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 003: ID 152d:2509 JMicron Technology Corp. / JMicron USA Technology Corp.
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 05ca:18a0 Ricoh Co., Ltd 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

The JMicron should be the external HDD connected.

---

### Post by astrobob.tk on 2011-09-13
Here's what I get with the command "dmesg" (sorry for the long code blocks).

During "Mass Storage":

```
$ dmesg|tail
[25843.095042] [UFW AUDIT] IN=lo OUT= MAC=00:00:00:00:00:00:00:00:00:00:00:00:08:00 SRC=127.0.0.1 DST=127.0.0.1 LEN=66 TOS=0x00 PREC=0x00 TTL=64 ID=28781 DF PROTO=UDP SPT=54579 DPT=53 LEN=46 
[25843.095096] [UFW AUDIT] IN= OUT=lo SRC=127.0.0.1 DST=127.0.0.1 LEN=94 TOS=0x00 PREC=0xC0 TTL=64 ID=1478 PROTO=ICMP TYPE=3 CODE=3 [SRC=127.0.0.1 DST=127.0.0.1 LEN=66 TOS=0x00 PREC=0x00 TTL=64 ID=28781 DF PROTO=UDP SPT=54579 DPT=53 LEN=46 ] 
[25843.095135] [UFW AUDIT] IN=lo OUT= MAC=00:00:00:00:00:00:00:00:00:00:00:00:08:00 SRC=127.0.0.1 DST=127.0.0.1 LEN=94 TOS=0x00 PREC=0xC0 TTL=64 ID=1478 PROTO=ICMP TYPE=3 CODE=3 [SRC=127.0.0.1 DST=127.0.0.1 LEN=66 TOS=0x00 PREC=0x00 TTL=64 ID=28781 DF PROTO=UDP SPT=54579 DPT=53 LEN=46 ] 
[26789.321266] usb 4-1: new full speed USB device using uhci_hcd and address 2
[26794.486388] usb 4-1: configuration #1 chosen from 1 choice
[26794.497106] scsi8 : SCSI emulation for USB Mass Storage devices
[26794.498754] usb-storage: device found at 2
[26794.498756] usb-storage: waiting for device to settle before scanning
[26799.498664] usb-storage: device scan complete
[26799.501463] scsi 8:0:0:0: Direct-Access     TI       Mobile Phone     1000 PQ: 0 ANSI: 5

$ dmesg|tail
[26794.486388] usb 4-1: configuration #1 chosen from 1 choice
[26794.497106] scsi8 : SCSI emulation for USB Mass Storage devices
[26794.498754] usb-storage: device found at 2
[26794.498756] usb-storage: waiting for device to settle before scanning
[26799.498664] usb-storage: device scan complete
[26799.501463] scsi 8:0:0:0: Direct-Access     TI       Mobile Phone     1000 PQ: 0 ANSI: 5
[26821.112083] usb 4-1: reset full speed USB device using uhci_hcd and address 2
[26831.373172] usb 4-1: reset full speed USB device using uhci_hcd and address 2
[26847.636272] usb 4-1: reset full speed USB device using uhci_hcd and address 2
[26847.900514] usb 4-1: reset full speed USB device using uhci_hcd and address 2

$ dmesg|tail
[26794.498756] usb-storage: waiting for device to settle before scanning
[26799.498664] usb-storage: device scan complete
[26799.501463] scsi 8:0:0:0: Direct-Access     TI       Mobile Phone     1000 PQ: 0 ANSI: 5
[26821.112083] usb 4-1: reset full speed USB device using uhci_hcd and address 2
[26831.373172] usb 4-1: reset full speed USB device using uhci_hcd and address 2
[26847.636272] usb 4-1: reset full speed USB device using uhci_hcd and address 2
[26847.900514] usb 4-1: reset full speed USB device using uhci_hcd and address 2
[26858.160030] usb 4-1: reset full speed USB device using uhci_hcd and address 2
[26858.308316] scsi 8:0:0:1: Device offlined - not ready after error recovery
[26858.308797] sd 8:0:0:0: Attached scsi generic sg2 type 0

$ dmesg|tail
[26794.498756] usb-storage: waiting for device to settle before scanning
[26799.498664] usb-storage: device scan complete
[26799.501463] scsi 8:0:0:0: Direct-Access     TI       Mobile Phone     1000 PQ: 0 ANSI: 5
[26821.112083] usb 4-1: reset full speed USB device using uhci_hcd and address 2
[26831.373172] usb 4-1: reset full speed USB device using uhci_hcd and address 2
[26847.636272] usb 4-1: reset full speed USB device using uhci_hcd and address 2
[26847.900514] usb 4-1: reset full speed USB device using uhci_hcd and address 2
[26858.160030] usb 4-1: reset full speed USB device using uhci_hcd and address 2
[26858.308316] scsi 8:0:0:1: Device offlined - not ready after error recovery
[26858.308797] sd 8:0:0:0: Attached scsi generic sg2 type 0


$ dmesg|tail
[26831.373172] usb 4-1: reset full speed USB device using uhci_hcd and address 2
[26847.636272] usb 4-1: reset full speed USB device using uhci_hcd and address 2
[26847.900514] usb 4-1: reset full speed USB device using uhci_hcd and address 2
[26858.160030] usb 4-1: reset full speed USB device using uhci_hcd and address 2
[26858.308316] scsi 8:0:0:1: Device offlined - not ready after error recovery
[26858.308797] sd 8:0:0:0: Attached scsi generic sg2 type 0
[26889.156085] usb 4-1: reset full speed USB device using uhci_hcd and address 2
[26899.413262] usb 4-1: reset full speed USB device using uhci_hcd and address 2
[26915.672287] usb 4-1: reset full speed USB device using uhci_hcd and address 2
[26915.932073] usb 4-1: reset full speed USB device using uhci_hcd and address 2

$ dmesg|tail -n 14
[26915.932073] usb 4-1: reset full speed USB device using uhci_hcd and address 2
[26926.188273] usb 4-1: reset full speed USB device using uhci_hcd and address 2
[26926.339371] sd 8:0:0:0: Device offlined - not ready after error recovery
[26926.339435] sd 8:0:0:0: rejecting I/O to offline device
[26926.339458] sd 8:0:0:0: rejecting I/O to offline device
[26926.339470] sd 8:0:0:0: rejecting I/O to offline device
[26926.339479] sd 8:0:0:0: [sdb] READ CAPACITY failed
[26926.339484] sd 8:0:0:0: [sdb] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK
[26926.339494] sd 8:0:0:0: [sdb] Sense not available.
[26926.339505] sd 8:0:0:0: rejecting I/O to offline device
[26926.339516] sd 8:0:0:0: [sdb] Write Protect is off
[26926.339522] sd 8:0:0:0: [sdb] Mode Sense: 00 00 00 00
[26926.339527] sd 8:0:0:0: [sdb] Assuming drive cache: write through
[26926.339816] sd 8:0:0:0: [sdb] Attached SCSI removable disk
```


In "Data Service" mode:

```
$ dmesg|tail -n 14
[27428.110614] scsi9 : SCSI emulation for USB Mass Storage devices
[27428.111013] usb-storage: device found at 3
[27428.111018] usb-storage: waiting for device to settle before scanning
[27432.689096] usb 4-1: USB disconnect, address 3
[27444.772270] usb 4-1: new full speed USB device using uhci_hcd and address 4
[27444.918556] usb 4-1: configuration #1 chosen from 1 choice
[27445.008506] cdc_acm 4-1:1.0: Zero length descriptor references
[27445.008525] cdc_acm: probe of 4-1:1.0 failed with error -22
[27445.008568] usbcore: registered new interface driver cdc_acm
[27445.009036] cdc_acm: v0.26:USB Abstract Control Model driver for USB modems and ISDN adapters
[27450.830136] [UFW AUDIT] IN= OUT=lo SRC=127.0.0.1 DST=127.0.0.1 LEN=52 TOS=0x00 PREC=0x00 TTL=64 ID=37499 DF PROTO=UDP SPT=45977 DPT=53 LEN=32 
[27450.830153] [UFW AUDIT] IN=lo OUT= MAC=00:00:00:00:00:00:00:00:00:00:00:00:08:00 SRC=127.0.0.1 DST=127.0.0.1 LEN=52 TOS=0x00 PREC=0x00 TTL=64 ID=37499 DF PROTO=UDP SPT=45977 DPT=53 LEN=32 
[27468.849572] [UFW AUDIT] IN= OUT=lo SRC=127.0.0.1 DST=127.0.0.1 LEN=53 TOS=0x00 PREC=0x00 TTL=64 ID=5915 PROTO=UDP SPT=47467 DPT=53 LEN=33 
[27468.849616] [UFW AUDIT] IN=lo OUT= MAC=00:00:00:00:00:00:00:00:00:00:00:00:08:00 SRC=127.0.0.1 DST=127.0.0.1 LEN=53 TOS=0x00 PREC=0x00 TTL=64 ID=5915 PROTO=UDP SPT=47467 DPT=53 LEN=33
```


Also w/ "Mass Storage" but w/ 4GB miniSD removed & waiting for the cell to  say that the battery is full (it is detected in "My Computer" by not under "lsusb" nor "fdisk -l" & I cannot open it in nautilus):

```
16271] usb 4-1: reset full speed USB device using uhci_hcd and address 7
[35517.877348] usb 4-1: reset full speed USB device using uhci_hcd and address 7
[35528.136064] usb 4-1: reset full speed USB device using uhci_hcd and address 7
[35528.283341] scsi 12:0:0:1: Device offlined - not ready after error recovery
[35528.288791] sd 12:0:0:0: Attached scsi generic sg2 type 0
[35559.112273] usb 4-1: reset full speed USB device using uhci_hcd and address 7
[35569.372276] usb 4-1: reset full speed USB device using uhci_hcd and address 7
[35585.632065] usb 4-1: reset full speed USB device using uhci_hcd and address 7
[35585.888123] usb 4-1: reset full speed USB device using uhci_hcd and address 7
[35596.200275] usb 4-1: reset full speed USB device using uhci_hcd and address 7
[35596.349571] sd 12:0:0:0: Device offlined - not ready after error recovery
[35596.349654] sd 12:0:0:0: rejecting I/O to offline device
[35596.349678] sd 12:0:0:0: rejecting I/O to offline device
[35596.349691] sd 12:0:0:0: rejecting I/O to offline device
[35596.349699] sd 12:0:0:0: [sdb] READ CAPACITY failed
[35596.349705] sd 12:0:0:0: [sdb] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK
[35596.349714] sd 12:0:0:0: [sdb] Sense not available.
[35596.349725] sd 12:0:0:0: rejecting I/O to offline device
[35596.349735] sd 12:0:0:0: [sdb] Write Protect is off
[35596.349741] sd 12:0:0:0: [sdb] Mode Sense: 00 00 00 00
[35596.349747] sd 12:0:0:0: [sdb] Assuming drive cache: write through
[35596.350056] sd 12:0:0:0: [sdb] Attached SCSI removable disk
```


Moreover, check the attached images for what appeared on my screen when the cell was recently (& rarely this happens) detected. When I try to open it in nautilus nothing happens.

What's going on?!

---

