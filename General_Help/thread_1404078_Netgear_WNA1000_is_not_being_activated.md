---
title: "Netgear WNA1000 is not being activated"
date: 2010-02-11
forum: General Help
---

### Post by Arenlor on 2010-02-11
lsusb gives:
Bus 001 Device 002: ID 0846:9040 NetGear, Inc.
So I think it's correctly recognizing it, but for some reason it won't identify it as a wireless USB NIC. I'm trying to install without a wired connection (several rooms away from a wire, and this is an old tower), so any help there would be nice, if not, then any advice on what to do when I get it hardwired would be nice. I have the Live CD to try this with. I also have a second CD/DVD, and have it installed/working on XP on the box (which after I get wireless working I'll be replacing), so I have the .inf file if anyone can direct me to using ndiswrapper for it. Let me know what else you need to know.

---

### Post by FixIt PeteC on 2010-02-15
Here's the fix that worked for me! 1. Download and install compat-wireless-2010-02-01, 2. go to the compat-wireless-2010-02-01/drivers/net/wireless/ath/ar9170 folder, 3. open the file "usb.c" at line 62 there will be a list of devices with their device IDs, 4. Edit one of the existing devices to "Netgear WNA1000" and device ID "0x0846, 0x9040" you have to edit one of the existing devices since a usb driver can only control 18 devices, which are already listed. 

The ar9170usb driver is the closest match for the WNA1000, but it must recognize your device ID. If for some reason your WNA1000 device ID is different, use you IDs. I had to plug mine into a windows pc and look at its properties first.

Mine looks like: 

static struct usb_device_id ar9170_usb_ids[] = {
/* Atheros 9170 */
{ USB_DEVICE(0x0cf3, 0x9170) },
/* Netgear WNA1000 */
{ USB_DEVICE(0x0846, 0x9040) },
/* TP-Link TL-WN821N v2 */
{ USB_DEVICE(0x0cf3, 0x1002) },

If everything else in the system is correct, just reboot and there it is!

Good luck!

Don't use ndiswrapper

---

### Post by jpace7 on 2010-02-23
Do you have any other advice This did not work for me. I downloaded and installed compact wireless. I also edited the usb.c file.


This is the output from lsusb

Bus 002 Device 005: ID 0846:9040 NetGear, Inc.

---

