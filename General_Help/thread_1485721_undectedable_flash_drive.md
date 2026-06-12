---
title: "undectedable flash drive"
date: 2010-05-17
forum: General Help
---

### Post by justborn on 2010-05-17
my system isn't able to detect my pen drive after a sudden power-cut while transfering files from computer to pendrive.....


even my Windows Xp box regards the USB pendrive as non-recognizable(in the notification area).there is really important data on the drive,please help me!

---

### Post by dineshs on 2010-05-17
I am not an expert.I suggest you try to install gparted.Then go to system-admin-gparted
In the top menu click Gparted-device and select your pendrive if listed
Is it hidden(under flags)?.Then right click on the device-click manage flags and untick hidden
Pl wait for other suggestions

---

### Post by justborn on 2010-05-23
> **dineshs said:**
> I am not an expert.I suggest you try to install gparted.Then go to system-admin-gparted
In the top menu click Gparted-device and select your pendrive if listed
Is it hidden(under flags)?.Then right click on the device-click manage flags and untick hidden
Pl wait for other suggestions

no,ma device ain't listed....:(

---

### Post by justborn on 2010-05-24
Bump!!

---

### Post by jerome1232 on 2010-05-24
Have you tried various usb ports?


Plug your usb stick in then immediately run this and post the output maybe, just maybe it will give a clue.

```
dmesg | tail -n 20
```

also, while the stick is plugged in.
```
sudo fdisk -l
```

---

### Post by rob-ward on 2010-05-24
what output do you get from
```
lsusb
```

---

### Post by justborn on 2010-05-24
> **rob-ward said:**
> what output do you get from
```
lsusb
```

```
lsusb
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```

---

### Post by justborn on 2010-05-24
> **jerome1232 said:**
> Have you tried various usb ports?


Plug your usb stick in then immediately run this and post the output maybe, just maybe it will give a clue.

```
dmesg | tail -n 20
```

also, while the stick is plugged in.
```
sudo fdisk -l
```

yes,i've tried various ports,even different systems(also on windows)......

```
dmesg | tail -n 20
[   73.504041] end_request: I/O error, dev fd0, sector 0
[   83.568054] end_request: I/O error, dev fd0, sector 0
[12387.770005] EXT4-fs (sdb1): warning: maximal mount count reached, running e2fsck is recommended
[12387.786243] EXT4-fs (sdb1): recovery complete
[12387.786540] EXT4-fs (sdb1): mounted filesystem with ordered data mode
[21283.030632] CPU0: Temperature above threshold, cpu clock throttled (total events = 1)[CODE]
```
[21283.030658] Disabling lock debugging due to kernel taint
[21283.032125] CPU0: Temperature/speed normal
[21300.000033] Machine check events logged
[22284.828026] usb 2-2: new full speed USB device using uhci_hcd and address 10
[22284.952083] usb 2-2: device descriptor read/64, error -71
[22285.180026] usb 2-2: device descriptor read/64, error -71
[22285.396036] usb 2-2: new full speed USB device using uhci_hcd and address 11
[22285.516025] usb 2-2: device descriptor read/64, error -71
[22285.744037] usb 2-2: device descriptor read/64, error -71
[22285.960027] usb 2-2: new full speed USB device using uhci_hcd and address 12
[22286.368034] usb 2-2: device not accepting address 12, error -71
[22286.480027] usb 2-2: new full speed USB device using uhci_hcd and address 13
[22286.888036] usb 2-2: device not accepting address 13, error -71
[22286.888073] hub 2-0:1.0: unable to enumerate USB device on port 2[/CODE]
```

sudo fdisk -l
Disk /dev/sdb: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00047936

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        4865    39078081   83  Linux

Disk /dev/sda: 80.1 GB, 80060424192 bytes
255 heads, 63 sectors/track, 9733 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000e700d

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9548    76694278+  83  Linux
/dev/sda2            9549        9733     1486012+   5  Extended
/dev/sda5            9549        9733     1485981   82  Linux swap / Solar

```

---

### Post by jerome1232 on 2010-05-24
I think your flash drive has been cooked man, it's dropping read errors and etc..

---

