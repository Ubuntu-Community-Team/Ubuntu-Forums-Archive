---
title: "pen drive"
date: 2011-01-18
forum: General Help
---

### Post by L Style on 2011-01-18
My 4GB & 8Gb kingston pen drives doesn't work with ubuntu 10.04. how can i fix this

---

### Post by matt_symes on 2011-01-18
Hi

> **L Style said:**
> My 4GB & 8Gb kingston pen drives doesn't work with ubuntu 10.04. how can i fix this

What do you mean "doesn't work" ?

Kind regards

---

### Post by L Style on 2011-01-18
> **matt_symes said:**
> Hi



What do you mean "doesn't work" ?

Kind regards
yes, It doesn't mount. Nothing in computer window

---

### Post by matt_symes on 2011-01-18
Hi

Have you given the pen drive a label ? If you have, it should be auto mounted under that label name.

Kind regards

---

### Post by L Style on 2011-01-18
bump

---

### Post by L Style on 2011-01-18
bump

---

### Post by L Style on 2011-01-18
> **matt_symes said:**
> Hi

Have you given the pen drive a label ? If you have, it should be auto mounted under that label name.

Kind regards

when i plugged my 8gb pen drive. there were nothing happen. this is lsusb displayed


achitha@lachitha-desktop:~$ lsusb
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 004: ID 0951:1613 Kingston Technology DataTraveler 8GB Pen Drive
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

---

### Post by matt_symes on 2011-01-18
Hi

Unplug the device, plug it back in and type

```
dmesg | tail
```

at a terminal. Post the results back here. That might give some clue as to what is going on.

Kind regards

---

### Post by matt_symes on 2011-01-18
Hi

Have you tried to manually mount it?

You could also check to see if nautilus is set up for automount.

Kind regards

---

### Post by L Style on 2011-01-18
> **matt_symes said:**
> Hi

Unplug the device, plug it back in and type

```
dmesg | tail
```

at a terminal. Post the results back here. That might give some clue as to what is going on.

Kind regards
[ 5315.070358] usb 1-6: configuration #1 chosen from 1 choice
[ 5315.076437] scsi15 : SCSI emulation for USB Mass Storage devices
[ 5315.078459] usb-storage: device found at 6
[ 5315.078467] usb-storage: waiting for device to settle before scanning
[ 5331.855471] usb 1-6: USB disconnect, address 6
[ 5334.144050] usb 1-6: new high speed USB device using ehci_hcd and address 7
[ 5334.287966] usb 1-6: configuration #1 chosen from 1 choice
[ 5334.292436] scsi16 : SCSI emulation for USB Mass Storage devices
[ 5334.298765] usb-storage: device found at 7
[ 5334.298774] usb-storage: waiting for device to settle before scanning

these are the results please help to fix this

---

### Post by matt_symes on 2011-01-18
Hi

Lets see if we can manually mount it first. Plug the USB stick and open a terminal and type

```
sudo fdisk -l
```

That is a small L above. Post the results back here.

EDIT: Forgot to ask. What is the filing system on the stick? fat32, ntfs, extX ?

Kind regards

---

### Post by L Style on 2011-01-18
> **matt_symes said:**
> Hi

Have you tried to manually mount it?

You could also check to see if nautilus is set up for automount.

Kind regards

how can i manually mount & how to set up nautilus for auto mount I don't know how to do these

---

### Post by L Style on 2011-01-18
> **matt_symes said:**
> Hi

Lets see if we can manually mount it first. Plug the USB stick and open a terminal and type

```
sudo fdisk -l
```

That is a small L above. Post the results back here.

EDIT: Forgot to ask. What is the filing system on the stick? fat32, ntfs, extX ?

Kind regards
its fat 32

---

### Post by matt_symes on 2011-01-18
Hi

Lets see if we can manually mount it first. Plug the USB stick and open a terminal and type

```
sudo fdisk -l
```

That is a small L above. Post the results back here.

Please follow these instructions.

Kind regards

---

### Post by L Style on 2011-01-18
> **L Style said:**
> its fat 32

Disk /dev/sda: 41.1 GB, 41110142976 bytes
255 heads, 63 sectors/track, 4998 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x44121ea8

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1203     9663066   83  Linux
/dev/sda2            1204        4997    30474915+   f  W95 Ext'd (LBA)
/dev/sda5            1251        2563    10546641    b  W95 FAT32
/dev/sda6            2564        3876    10546641    b  W95 FAT32
/dev/sda7            3877        4997     9004401    b  W95 FAT32
/dev/sda8            1204        1250      376832   82  Linux swap / Solaris


these are the results

---

### Post by matt_symes on 2011-01-18
Hi

```

Disk /dev/sda: 41.1 GB, 41110142976 bytes
255 heads, 63 sectors/track, 4998 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x44121ea8

Device Boot Start End Blocks Id System
/dev/sda1 * 1 1203 9663066 83 Linux
/dev/sda2 1204 4997 30474915+ f W95 Ext'd (LBA)
/dev/sda5 1251 2563 10546641 b W95 FAT32
/dev/sda6 2564 3876 10546641 b W95 FAT32
/dev/sda7 3877 4997 9004401 b W95 FAT32
/dev/sda8 1204 1250 376832 82 Linux swap / Solaris
```

That is not so good. While the kernel is seeing the USB stick (output from dmesg) it is not recognising it, as fdisk should have returned the device if it was plugged in. That means we can't manually mount.

To be honest, i am not sure why that is. I will do some reading and see if i can find out why. Hopefully others might know.

Kind regards

---

### Post by L Style on 2011-01-18
> **matt_symes said:**
> Hi

```

Disk /dev/sda: 41.1 GB, 41110142976 bytes
255 heads, 63 sectors/track, 4998 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x44121ea8

Device Boot Start End Blocks Id System
/dev/sda1 * 1 1203 9663066 83 Linux
/dev/sda2 1204 4997 30474915+ f W95 Ext'd (LBA)
/dev/sda5 1251 2563 10546641 b W95 FAT32
/dev/sda6 2564 3876 10546641 b W95 FAT32
/dev/sda7 3877 4997 9004401 b W95 FAT32
/dev/sda8 1204 1250 376832 82 Linux swap / Solaris
```

That is not so good. While the kernel is seeing the USB stick (output from dmesg) it is not recognising it, as fdisk should have returned the device if it was plugged in. That means we can't manually mount.

To be honest, i am not sure why that is. I will do some reading and see if i can find out why. Hopefully others might know.

Kind regards

Ooppss... Is that a big problem. Can we report this to ubuntu HQ.

---

### Post by L Style on 2011-01-18
> **matt_symes said:**
> Hi

```

Disk /dev/sda: 41.1 GB, 41110142976 bytes
255 heads, 63 sectors/track, 4998 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x44121ea8

Device Boot Start End Blocks Id System
/dev/sda1 * 1 1203 9663066 83 Linux
/dev/sda2 1204 4997 30474915+ f W95 Ext'd (LBA)
/dev/sda5 1251 2563 10546641 b W95 FAT32
/dev/sda6 2564 3876 10546641 b W95 FAT32
/dev/sda7 3877 4997 9004401 b W95 FAT32
/dev/sda8 1204 1250 376832 82 Linux swap / Solaris
```

That is not so good. While the kernel is seeing the USB stick (output from dmesg) it is not recognising it, as fdisk should have returned the device if it was plugged in. That means we can't manually mount.

To be honest, i am not sure why that is. I will do some reading and see if i can find out why. Hopefully others might know.

Kind regards

Ooppss... Is that a big problem. Can we report this to ubuntu HQ.

---

### Post by L Style on 2011-01-18
> **matt_symes said:**
> Hi

```

Disk /dev/sda: 41.1 GB, 41110142976 bytes
255 heads, 63 sectors/track, 4998 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x44121ea8

Device Boot Start End Blocks Id System
/dev/sda1 * 1 1203 9663066 83 Linux
/dev/sda2 1204 4997 30474915+ f W95 Ext'd (LBA)
/dev/sda5 1251 2563 10546641 b W95 FAT32
/dev/sda6 2564 3876 10546641 b W95 FAT32
/dev/sda7 3877 4997 9004401 b W95 FAT32
/dev/sda8 1204 1250 376832 82 Linux swap / Solaris
```

That is not so good. While the kernel is seeing the USB stick (output from dmesg) it is not recognising it, as fdisk should have returned the device if it was plugged in. That means we can't manually mount.

To be honest, i am not sure why that is. I will do some reading and see if i can find out why. Hopefully others might know.

Kind regards

Ooppss... Is that a big problem. Can we report this to ubuntu HQ.

---

### Post by matt_symes on 2011-01-18
Hi

Your not the only one to have this problem. It's not scanning the USB drive.

[http://ubuntuforums.org/showthread.php?t=871678](http://ubuntuforums.org/showthread.php?t=871678)

I am not having much luck finding a solution at the moment.

Kind regards

---

