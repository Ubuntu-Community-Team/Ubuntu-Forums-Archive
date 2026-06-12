---
title: "Is my USB stick bad?"
date: 2010-02-19
forum: General Help
---

### Post by DuncanKline on 2010-02-19
I am having trouble with my Kingston Data Traveler 2GB USB drive. It worked a few months ago, but I can't get it mounted anymore. It shows up when I run lsusb:

user@Desktop:~$ lsusb
**Bus 001 Device 005: ID 13fe:1d00 Kingston Technology Company Inc. DataTraveler 2.0 1GB/4GB Flash Drive / Patriot Xporter 4GB Flash Drive**
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 003: ID 058f:9360 Alcor Micro Corp. 8-in-1 Media Card Reader
Bus 002 Device 002: ID 046d:c521 Logitech, Inc. MX620 Laser Cordless Mouse
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


Interestingly, it says it's a 4GB flash drive but it is labeled as 2GB and as far as I know only has 2GB of storage, not really sure why that is. 

In the past I would format my USB with fdisk, but now it doesn't recognize the USB device. It recognizes only my hard drive:

root@Desktop:/home/user# fdisk -l

Disk /dev/sda: 120.1 GB, 120060444672 bytes
255 heads, 63 sectors/track, 14596 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x02cc02cb

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       14151   113667876   83  Linux
/dev/sda2           14152       14596     3574462+   5  Extended
/dev/sda5           14152       14596     3574431   82  Linux swap / Solaris

I ran dmesg|tail and this is what I got:

root@Desktop:/home/user# dmesg|tail
[  632.695603] usb 1-6: USB disconnect, address 4
[  659.268256] usb 1-6: new high speed USB device using ehci_hcd and address 5
[  659.416127] usb 1-6: configuration #1 chosen from 1 choice
[  659.418906] scsi4 : SCSI emulation for USB Mass Storage devices
[  659.419044] usb-storage: device found at 5
[  659.419046] usb-storage: waiting for device to settle before scanning
[  664.416384] usb-storage: device scan complete
[  664.419113] scsi 4:0:0:0: Direct-Access              USB DISK 30X     1.00 PQ: 0 ANSI: 0 CCS
[  664.419665] sd 4:0:0:0: Attached scsi generic sg7 type 0
[  664.443883] sd 4:0:0:0: [sdf] Attached SCSI removable disk


I am confused as to what I need to do to get this USB mounted so I can format it. It wasn't recognized by BIOS either, as I was going to boot it from BIOS and format it with gparted, but that's a no go. 

So any advice or tips to get this USB working again? I feel like I must be doing something wrong, but I don't know what. 

Thanks.


Edit: I am using Ubuntu 9.10 and KDE 4.4

---

### Post by WubiNoob on 2010-02-19
This might seem really obious, but is it formatted to a readable file format? If you want to boot from it, it needs to be formatted with FAT32. Make sure gparted, or whatever you're using is correctly formatting the disk, because your computer can clearly recognize it being there.

---

### Post by wilee-nilee on 2010-02-19
In order for you to reformat it with gparted it would not be mounted, so when you have the usb plugged in and open gparted the thumb doesn't show up in the drop down in the top right corner am I correct.

---

### Post by DuncanKline on 2010-02-19
It doesn't show up in GParted, nor does it show up under the boot device options in BIOS. It showed up under BIOS as a device in the past which is how I would run gparted to format other USBs.

---

### Post by DuncanKline on 2010-02-19
Still looking for an answer.

---

### Post by Grillin on 2010-02-19
I am also looking for answer.

---

### Post by Plumtreed on 2010-02-19
I have 2 USB drives that had ISOs installed as a 'backup' to use when things go wrong. I recently wanted to check to see how something reacted in 9.04 because it seemed not to work in 9.10.

To make a long story short, the 9.04 disk didn't boot even though it has in the past!

I tried Startup Disk Creator in order to 'redo' the emergency disk and it fails with the message 'Boot Error'.

This appears to be a similar sort of problem.

---

### Post by anaconda on 2010-02-19
have you tried testdisk or photorec on it?

---

### Post by kio_http on 2010-02-19
> **WubiNoob said:**
> This might seem really obious, but is it formatted to a readable file format? If you want to boot from it, it needs to be formatted with FAT32. Make sure gparted, or whatever you're using is correctly formatting the disk, because your computer can clearly recognize it being there.

This is incorrect. Filesystem has nothing to do with the ability to boot.

---

### Post by DuncanKline on 2010-02-19
I can use any sort of recovery tool at this point because the flash drive isn't mounted anywhere. I don't know where I would direct the command to. Is there a way to manually get it mounted at /dev/sdX?


EDIT: Tried testdisk anyway, and as I thought, it wouldn't recognize the usb as a storage device. Only my hard drive was listed.

---

### Post by Plumtreed on 2010-02-21
I sorted my problem by using my 'old' 9.04 iso cd, formatting and creating 2 bootable USB drives. Using the same procedure in 9.10 failed.

At least, in my experience, something is wrong in the 9.10 process.

---

### Post by clubsoda on 2010-02-23
Interesting problem and interesting timing. I've just discovered that my USB flash drive (which shares the same lsusb identifier as yours) is being corrupted when files are written in USB2.0 mode using a 3m USB extension cable. I suspect this flash memory is a bit borderline in high-speed mode. I'd suggest plugging it directly into the motherboard on the back panel rather than a hub, cable or a front panel connector which may involve an internal 50cm cable. If your board has a USB1.x jumper switch or BIOS option that might be worth a test too.

Others have reported that a simple [package update](http://ubuntuforums.org/showthread.php?t=1394433) or [installing linux-modules-backports-karmic](http://ubuntuforums.org/showthread.php?t=1211932) might help.

More likely the boot sector or partition table is broken. The missing lines between "Attached scsi generic sg7 type 0" and "[sdf] Attached SCSI removable disk" indicate that the kernel didn't find partitions, however the good news is that the device should be present as /dev/sdf. Try things like this:-```
ls -l /dev/sd*
sudo fdisk /dev/sdf
```and let us know what you see. Then maybe:-```
dd if=/dev/sdf of=flash.mbr bs=512 count=1
xxd flash.mbr
```If you post the output of that xxd, someone here may be able to interpret it.

---

### Post by jhoney142 on 2010-03-04
Hi, 
  I also have the same problem

---

### Post by no_martini_no on 2011-03-31
After ```
sudo fdisk /dev/sdf
```
it outputs nothing but:
```
Unable to open /dev/sdf
```

I think there might be a problem with the usb flash controller. I have done and experienced the same things as listed above.
thanks.

---

