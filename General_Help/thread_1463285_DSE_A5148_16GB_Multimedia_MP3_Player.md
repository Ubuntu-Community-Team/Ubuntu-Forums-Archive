---
title: "DSE A5148 16GB Multimedia MP3 Player"
date: 2010-04-26
forum: General Help
---

### Post by Paranoid Tux on 2010-04-26
I have recently bought a new **** Smith Electronics 16GB Multimedia MP3 Player (A5148) and am unable to get it to run under Kubuntu 9.10 64bit edition. I am able to charge the device from the USB port and I can also use the device on the Vista Ultimate 64bit computer (after the usual M$ stuff around and several reboots).

I have read that the A5146, which is the 8GB version of the one that I have, works very well in Ubuntu 8.10 and shows up as a USB drive. I have spoken to DSE Help and they weren't any, other than to say that the drive only mounts under their nominated OS and is nothing like a USB storage device, which I know is rubbish. I tried searching for it using lsusb, but it hangs the process and I have to kill it.

I was wondering if there is anyone out there who has any idea how to mount this drive, even if I have to run a 32bit distro. Please feel free to let me know if you require any other information.

Cheers,

Paranoid Tux

---

### Post by ScarletPea on 2011-01-22
I too have had this device given to me. Today I took it to the store and tried it on their Vista machines. It mounts _sometimes_ on vista and uses the standard usb storage driver.
 I pulled the hardware ID's off it:

```
VID_IE74&PID_4621&Rev_0000
```

When pluging in I get the following:
```
Initializing USB Mass Storage driver...
scsi2 : usb-storage 5-7:1.0
usbcore: registered new interface driver usb-storage
USB Mass Storage support registered.
scsi 2:0:0:0: Direct-Access     MP3                       1.00 PQ: 0 ANSI: 0
sd 2:0:0:0: Attached scsi generic sg2 type 0
sd 2:0:0:0: [sdb] 32296960 512-byte logical blocks: (16.5 GB/15.4 GiB)
usb 5-7: reset high speed USB device using ehci_hcd and address 9
usb 5-7: reset high speed USB device using ehci_hcd and address 9
usb 5-7: reset high speed USB device using ehci_hcd and address 9
usb 5-7: device descriptor read/64, error -110
```

I have tried with the latest (at time of writing) kernel, 2.6.28-rc2 with no improvement.

Given the nature of the error (i.e. it appears to be a hardware fault) I consider this a kernel bug and will follow it that way.

(Also tried on Fedora, Opensuse, Mint, and Debian.)

Can someone confirm that the 8Gig device works. If so I will go and swap it 8)

Cheers.

---

### Post by ScarletPea on 2011-01-25
It is now fixed upstream, thanks to Alan Stern and the linux-usb team:

Note that for kernels before 2.6.37, the USB_* flag names were called
US_* instead. The patch will have to be adjusted to apply to the
earlier stable kernels.



```
Index: usb-2.6/drivers/usb/storage/unusual_devs.h
===================================================================
--- usb-2.6.orig/drivers/usb/storage/unusual_devs.h
+++ usb-2.6/drivers/usb/storage/unusual_devs.h
@@ -1888,6 +1888,13 @@ UNUSUAL_DEV( 0x1908, 0x3335, 0x0200, 0x0
USB_SC_DEVICE, USB_PR_DEVICE, NULL,
US_FL_NO_READ_DISC_INFO ),

+/* Reported by Jasper Mackenzie <scarletpimpernal@hotmail.com> */
+UNUSUAL_DEV( 0x1e74, 0x4621, 0x0000, 0x0000,
+ "Coby Electronics",
+ "MP3 Player",
+ USB_SC_DEVICE, USB_PR_DEVICE, NULL,
+ US_FL_BULK_IGNORE_TAG | US_FL_MAX_SECTORS_64 ),
+
UNUSUAL_DEV( 0x2116, 0x0320, 0x0001, 0x0001,
"ST",
"2A",

```

Please mark as closed.

---

