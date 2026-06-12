---
title: "Infected USB pen drive read-only. Can't format."
date: 2010-02-01
forum: General Help
---

### Post by Umang on 2010-02-01
Hello,
I got some documents scanned today and had them put in a USB drive. The shopkeeper informed me that it has a virus, yet he transferred the files onto the USB drive.

When I put it into my computer ten minutes later, the drive was not getting mounted. I read up and tried installing usbmount. After installing that, I managed to mount the drive. However, the drive was read-only on Ubuntu. On Windows, I found a virus and tried unsuccessfully to delete it (read-only). I tried again on Ubuntu, but didn't manage to delete the infected file (ReCyCleR/sEtuP.exe).

I have now backed up all the files on the disk (except, obviously, the ReCyCleR directory).

When I try to format the drive using gParted, I get: ```
GParted 0.4.5

Libparted 1.8.8.1.159-1e0e
Format /dev/sdb1 as fat32  00:00:02    ( ERROR )
     	
calibrate /dev/sdb1  00:00:00    ( SUCCESS )
     	
path: /dev/sdb1
start: 32
end: 4005885
size: 4005854 (1.91 GiB)
set partition type on /dev/sdb1  00:00:01    ( ERROR )
libparted messages    ( INFO )
     	
Unable to open /dev/sdb read-write (Read-only file system). /dev/sdb has been opened read-only.
Unable to open /dev/sdb read-write (Read-only file system). /dev/sdb has been opened read-only.
Unable to open /dev/sdb read-write (Read-only file system). /dev/sdb has been opened read-only.
Unable to open /dev/sdb read-write (Read-only file system). /dev/sdb has been opened read-only.
Unable to open /dev/sdb read-write (Read-only file system). /dev/sdb has been opened read-only.
Unable to open /dev/sdb read-write (Read-only file system). /dev/sdb has been opened read-only.
Unable to open /dev/sdb read-write (Read-only file system). /dev/sdb has been opened read-only.
Unable to open /dev/sdb read-write (Read-only file system). /dev/sdb has been opened read-only.
Can't write to /dev/sdb, because it is opened read-only.
Unable to open /dev/sdb read-write (Read-only file system). /dev/sdb has been opened read-only.

========================================
```I also get a similar message on Windows, using the format option in Windows Explorer. It says the device is read-only.

I have looked for tiny switches, and haven't found any. This is a "Transcend JF V30 2GB" USB key. A similar key (4 GB) still works perfectly on the computer.

Any ideas?

Thank you,

Umang

dmesg | grep usb :
```
[    0.130769] usbcore: registered new interface driver usbfs
[    0.130821] usbcore: registered new interface driver hub
[    0.130903] usbcore: registered new device driver usb
[    1.255874] usb usb1: configuration #1 chosen from 1 choice
[    1.257041] usb usb2: configuration #1 chosen from 1 choice
[    1.564092] usb 1-1: new low speed USB device using uhci_hcd and address 2
[    1.720413] usb 1-1: configuration #1 chosen from 1 choice
[    2.746121] usbcore: registered new interface driver hiddev
[    2.759504] input: HID 062a:0000 as /devices/pci0000:00/0000:00:1f.2/usb1/1-1/1-1:1.0/input/input5
[    2.759777] generic-usb 0003:062A:0000.0001: input,hidraw0: USB HID v1.10 Mouse [HID 062a:0000] on usb-0000:00:1f.2-1/input0
[    2.759840] usbcore: registered new interface driver usbhid
[    2.759850] usbhid: v2.6:USB HID core driver
[ 7524.976071] usb 1-2: new full speed USB device using uhci_hcd and address 3
[ 7525.142777] usb 1-2: configuration #1 chosen from 1 choice
[ 7525.561689] usbcore: registered new interface driver usb-storage
[ 7525.562980] usb-storage: device found at 3
[ 7525.562989] usb-storage: waiting for device to settle before scanning
[ 7530.562332] usb-storage: device scan complete
[ 9545.688149] usb 1-2: USB disconnect, address 3
[ 9567.008110] usb 1-2: new full speed USB device using uhci_hcd and address 4
[ 9567.171824] usb 1-2: configuration #1 chosen from 1 choice
[ 9567.175634] usb-storage: device found at 4
[ 9567.175641] usb-storage: waiting for device to settle before scanning
[ 9572.173464] usb-storage: device scan complete
[ 9623.312164] usb 1-2: USB disconnect, address 4
[ 9659.760089] usb 1-2: new full speed USB device using uhci_hcd and address 5
[ 9659.931531] usb 1-2: configuration #1 chosen from 1 choice
[ 9659.937787] usb-storage: device found at 5
[ 9659.937794] usb-storage: waiting for device to settle before scanning
[ 9664.939303] usb-storage: device scan complete
[ 9695.232147] usb 1-2: USB disconnect, address 5
[ 9729.448098] usb 1-2: new full speed USB device using uhci_hcd and address 6
[ 9729.618532] usb 1-2: configuration #1 chosen from 1 choice
[ 9729.624902] usb-storage: device found at 6
[ 9729.624908] usb-storage: waiting for device to settle before scanning
[ 9734.626159] usb-storage: device scan complete
[11784.136170] usb 1-2: USB disconnect, address 6

```

---

### Post by chaanakya_chiraag on 2010-02-01
Can you post the last 100 lines or so from your dmesg output (without the USB filtering)?  Thanks!  It might be an mtab/fstab issue...

---

### Post by undecim on 2010-02-01
> **chaanakya_chiraag said:**
> Can you post the last 100 lines or so from your dmesg output (without the USB filtering)?  Thanks!  It might be an mtab/fstab issue...
If the problem persists in windows, then it's not a [mf]stab issue. Though, the last 100 dmesg lines may help. You can get that by running "dmesg | tail -n 100"

I suspect the write protection may be a "feature" of the flash drive. The JetFlash utility from Transcend may be able to fix that: [http://www.transcendusa.com/Products/JFelite.asp](http://www.transcendusa.com/Products/JFelite.asp)

---

### Post by Umang on 2010-02-01
Attached. I've rebooted and then attached after booting so that other usb activity doesn't come in the way of all this (e.g Printer, other pen drive, etc).

EDIT: I'll try the JetFlash utility tomorrow.

---

### Post by Umang on 2010-02-10
Bump?

---

### Post by chaanakya_chiraag on 2010-02-10
There's something on the flashdrive that's blocking the writing...in otherwords, what undecim said is correct...that is, it's a "feature" of the flash drive.  Have you tried the link undecim pointed out?  That might work.  Also, try looking on the flash drive for a little switch that (en/dis)ables write protection.  I know some flash drives have that.

---

### Post by Umang on 2010-02-13
No. Write protection wasn't a feature, but a problem. I tried the tool you suggested and it gave me a write protected error. From there, I found a JetFlash Recovery Tool, which didn't work (or so it seemed). It told me to contact customer service because the recovery tool wasn't able to fix the device. Being the adamanant person that I am, I tried to format the disk after the recovery. That didn't work as well. 

But now there seemed to be progress - Windows told me that the drive needs to be formatted instead of showing me the write protected partition. I tried the recovery tool yet again, and this time it froze in between. So I removed the USB drive and plugged it in again. I tried formatting the drive again and it worked perfectly!

Thank you for your help. I'm glad I've been able to fix it.

EDIT: For those with the same issue, try this recovery tool at least twice and then format: [http://www.transcendusa.com/Products/online_recovery.asp](http://www.transcendusa.com/Products/online_recovery.asp)

---

