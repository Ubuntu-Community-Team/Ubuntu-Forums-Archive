---
title: "WD Passport external hd not detected"
date: 2011-11-11
forum: General Help
---

### Post by bradlees on 2011-11-11
I am using ubuntu 11.10. I have a wd external hd that ubuntu does not seem to detect. I cannot go into gparted to reformat the drive because i only see dev/sda. 

How do I get ubuntu to see the xhd?

---

### Post by pqwoerituytrueiwoq on 2011-11-11
make sure the usb device is being detected 
post out put of [FONT=Courier New]lsusb[/FONT]

---

### Post by bradlees on 2011-11-12
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 006: ID 05c8:040d Cheng Uei Precision Industry Co., Ltd (Foxlink) 
Bus 005 Device 002: ID 046d:c51b Logitech, Inc. V220 Cordless Optical Mouse for Notebooks
Bus 005 Device 003: ID 0a5c:21b4 Broadcom Corp. BCM2070 Bluetooth 2.1 + EDR

---

### Post by Chris_Sugden on 2011-11-18
I have a western digital wd1600u017-005 I inherited. No manual. 

I have tried several ports on my Ubuntu 11.10 box

It is also not being recognised:
```
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
```

Works fine plugged into a Windoze XP machine....must be a driver needed.

---

### Post by dcstar on 2011-11-18
Plug device in and then immediately run:

```
dmesg
```

And post results here.

It should look like something like this:
```
[ 7532.114485] usb 3-3: USB disconnect, address 3
[ 7537.290041] usb 3-3: new high speed USB device using ehci_hcd and address 4
[ 7537.441031] usb 3-3: configuration #1 chosen from 1 choice
[ 7537.452385] scsi10 : SCSI emulation for USB Mass Storage devices
[ 7537.455642] usb-storage: device found at 4
[ 7537.455646] usb-storage: waiting for device to settle before scanning
[ 7542.461130] usb-storage: device scan complete
[ 7542.461525] scsi 10:0:0:0: Direct-Access     SEAGATE  ST68022CF        3.01 PQ: 0 ANSI: 2
[ 7542.462440] sd 10:0:0:0: Attached scsi generic sg6 type 0
[ 7542.464235] sd 10:0:0:0: [sdf] 15625008 512-byte logical blocks: (8.00 GB/7.45 GiB)
[ 7542.464968] sd 10:0:0:0: [sdf] Write Protect is off
[ 7542.464976] sd 10:0:0:0: [sdf] Mode Sense: 53 00 00 08
[ 7542.464982] sd 10:0:0:0: [sdf] Assuming drive cache: write through
[ 7542.466472] sd 10:0:0:0: [sdf] Assuming drive cache: write through
[ 7542.466481]  sdf: sdf1
[ 7543.924618] sd 10:0:0:0: [sdf] Assuming drive cache: write through
[ 7543.924632] sd 10:0:0:0: [sdf] Attached SCSI disk
[ 7544.849296] EXT4-fs (sdf1): mounted filesystem with ordered data mode
```

---

### Post by efflandt on 2011-11-18
A WD Passport should show up as an sd device in **dmesg** after its USB is plugged in, and any Linux partitions that are not corrupted (mine showed "warning: maximal mount count reached, running e2fsck is recommended", but the ext3 partition on it still auto mounted).

Although, it may show up as different Bus and Device, this is typical **lsusb** listing for 160 GB Passport in 11.10:

```
Bus 002 Device 004: ID 1058:0702 Western Digital Technologies, Inc. Passport External HDD
```If nothing shows up in **dmesg** or **lsusb**, you may have a cable or hardware problem with the drive.  I have (2) 160 GB and (2) 500 GB Passports and have not had a problem with any of them, other than that "some" computers will not boot from the 500 GB drives when those same drives boot Linux on other computers.  But the computers that cannot boot from the bigger drives can still access and mount any of them no problem from Linux on their internal drives.  Even a corrupted USB drive will usually show something (drive info) in **sudo fdisk -l**, even if bad sectors prevent its partition table from being read (at least that has been my experience for trashed laptop drives in external USB enclosure).

PS: Both of my root hubs are usb 2.0.  I think it should still work in a usb 1.1 root hub, but slower.  Maybe try a different usb port if you have mixed 1.1 and 2.0.

---

### Post by bradlees on 2011-11-19
The other responses were a bit over my head. I plugged the xhd in on windows 7. I uninstalled the auto back up feature or wd unlock, whatever its called. It has a file on it that causes it to be recognized as cd media and starts wd's secure backup program. Just uninstall this and use the built in tool to reformat it to ntsf. Don't register it or put any passwords. Then I rebooted to ubuntu, xhd is there, no problem since.

---

