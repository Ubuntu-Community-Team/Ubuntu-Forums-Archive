---
title: "Devkit-disks and Hal keep polling a non-existing hdd."
date: 2010-04-15
forum: General Help
---

### Post by mikewhatever on 2010-04-15
**Are you a netbook owner? If so, please post the output of the following command here.**
```
ps aux | grep poll
```

**Thanks.**

-------------------------------------------------------------------------------------------------------------------------------------------------------------------


```
ps aux | grep poll
root      1155  0.0  0.1   3420  1132 ?        S    13:23   0:00 hald-addon-storage: no polling on /dev/sdb because it is explicitly disabled
root      1989  0.1  0.0   4828   748 ?        S    13:24   0:00 devkit-disks-daemon: polling /dev/sdb    
```

This is a netbook, and /dev/sdb seems to be the flash stick I installed Karmic from. Now, anything plugged into the system starts from /dev/sdc, and /dev/sdb is just a phantom.

```
sudo fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000080

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        8511    68364576   83  Linux
/dev/sda3            8512       19457    87923745    5  Extended
/dev/sda5            8512       19331    86911618+  83  Linux
/dev/sda6           19332       19457     1012063+  82  Linux swap / Solaris

```

I can manually disable polling of both Hal and devkit-disks:

hal-disable-polling --device /dev/sdb
devkit-disks --inhibit-polling /dev/sdb

but these need to be run at every boot.

I can also open Palimpsest Disk Utility and detach /dev/sdb (see attachment), which needs to be done every time after loading the DE.

I'd like the system to 'forget' about /dev/sdb. The rational should be quite obvious - saving cpu cycles and conversing battery power, it is a netbook, after all.

---

### Post by mikewhatever on 2010-04-15
I was wondering if other netbook users are affected?

I'll post some more info I found meanwhile:

devkit-disks --enumerate
```

/org/freedesktop/DeviceKit/Disks/devices/sda5
/org/freedesktop/DeviceKit/Disks/devices/sda
/org/freedesktop/DeviceKit/Disks/devices/sda6
**/org/freedesktop/DeviceKit/Disks/devices/sdb**
/org/freedesktop/DeviceKit/Disks/devices/sda1
/org/freedesktop/DeviceKit/Disks/devices/sda3

```

devkit-disks --enumerate-device-files
```
/dev/sdb
/dev/disk/by-id/usb-Generic-_Multi-Card_20071114173400000-0:0
/dev/disk/by-path/pci-0000:00:1d.7-usb-0:7:1.0-scsi-0:0:0:0

```

devkit-disks --dump
```
========================================================================
Showing information for /org/freedesktop/DeviceKit/Disks/devices/sdb
  native-path:                 /sys/devices/pci0000:00/0000:00:1d.7/usb1/1-7/1-7:1.0/host2/target2:0:0/2:0:0:0/block/sdb
  device:                      8:16
  device-file:                 /dev/sdb
    by-id:                     /dev/disk/by-id/usb-Generic-_Multi-Card_20071114173400000-0:0
    by-path:                   /dev/disk/by-path/pci-0000:00:1d.7-usb-0:7:1.0-scsi-0:0:0:0
  detected at:                 Thu 15 Apr 2010 03:14:37 PM IDT
  system internal:             0
  removable:                   1
  has media:                   0
    detects change:            1
    detection by polling:      1
    detection inhibitable:     1
    detection inhibited:       0
  is read only:                0
  is mounted:                  0
  mount paths:             
  mounted by uid:              0
  presentation hide:           0
  presentation nopolicy:       0
  presentation name:           
  presentation icon:           
  size:                        0
  block size:                  0
  job underway:                no
  usage:                       
  type:                        
  version:                     
  uuid:                        
  label:                       
  drive:
    vendor:                    Generic-
    model:                     Multi-Card
    revision:                  1.00
    serial:                    20071114173400000
    detachable:                1
    can spindown:              0
    rotational media:          1
    ejectable:                 0
    media:                     
      compat:                 
    interface:                 usb
    if speed:                  480000000 bits/s
    ATA SMART:                 not available

```

---

### Post by mikewhatever on 2010-04-17
bump

---

### Post by mikewhatever on 2010-04-18
bump

---

### Post by mikewhatever on 2010-04-19
bump

---

### Post by mikewhatever on 2010-04-20
bump

---

### Post by mikewhatever on 2010-04-21
bump

---

### Post by mikewhatever on 2010-04-22
bump

---

### Post by mikewhatever on 2010-04-23
bump

---

### Post by mikewhatever on 2010-04-25
bump

---

### Post by mikewhatever on 2010-04-26
bump

---

### Post by mikewhatever on 2010-04-27
bump

---

### Post by mikewhatever on 2010-04-28
bump

---

### Post by mikewhatever on 2010-04-29
bump

---

### Post by mikewhatever on 2010-04-30
bump

---

### Post by happyhamster on 2010-04-30
Hello, 

Perhaps /dev/sdb is the usb hub/reader itself, which gets polled to see if anything is attached to it. In that case a crude way of getting rid of /dev/sdb is disabling it in the BIOS (if possible).

Another way would be to add the lines:

hal-disable-polling --device /dev/sdb
devkit-disks --inhibit-polling /dev/sdb

to /etc/rc.local

> 
#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

# May 2010, added by user:
hal-disable-polling --device /dev/sdb
devkit-disks --inhibit-polling /dev/sdb

exit 0


When using Ubuntu Lucid, you might have to manually create an init.d script instead though.

---

### Post by mikewhatever on 2010-04-30
Interesting suggestion, thanks for replying. Does your Ubuntu installation poll anything?

---

### Post by happyhamster on 2010-04-30
Yes, but I don't have a netbook to compare.

udisks-daemon is polling the dvd-drive on my laptop (Lucid), and hald-addon-storage is doing the same on my desktop (Jaunty), so nothing strange there. (Both installations were done from usb-sticks BTW.)

---

### Post by mikewhatever on 2010-05-02
Well, netbook is just a notebook without cdrom. I've used the following to stop the polling:
```
devkit-disks --detach /dev/sdb
```,

but what I'd really like to find is the config file that holds the sdb related info.

---

