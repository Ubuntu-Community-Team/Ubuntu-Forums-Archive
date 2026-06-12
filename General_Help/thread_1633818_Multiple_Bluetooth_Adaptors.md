---
title: "Multiple Bluetooth Adaptors"
date: 2010-11-29
forum: General Help
---

### Post by axelmasok on 2010-11-29
Hi everyone, first time poster here. Linux user for 12 years now...geee time flies
.
Using Kubuntu Lucid here and have found on this Asus M51V laptop that the built in wifi+bluetooth adapter is ... ordinary.
My logitech bluetooth mouse and keyboard seems to only work 100% reliably with one of my USB bluetooth dongles. I have 3 of these. So in effect 1x built in and 2 USB bluetooth adaptors either drop the connection to my k+m or never work after resuming the laptop.

So, the question is, is there a command to disable the built-in HCI0 only? I have read posts here demonstrating how to turn the bluetooth completely off via rfkill. I have seen how to make the adapter go into the "down" state with hciconfig.

There must be a better way to completely disable it at startup so my usb bluetooth dongle is and remains the only adapter (HCI0 not HCI1). Worst case scenario is removing the hardware from the laptop but would really like to keep wifi :)

---

### Post by pricetech on 2010-11-29
Check your BIOS.  See if you can disable BlueTooth and leave wireless enabled.  You may not be able to though.  Seems my latest work laptop combines them for some silly reason.

---

### Post by axelmasok on 2010-11-30
> **pricetech said:**
> Check your BIOS.  See if you can disable BlueTooth and leave wireless enabled.  You may not be able to though.  Seems my latest work laptop combines them for some silly reason.

Spot on. Have checked in there. From memory it's either a no option or they are combined. The switch on the front fascia is probably the replacement for the bios option. Thanks though.

---

### Post by pricetech on 2010-11-30
Are BlueTooth and Wireless both on the same card ??

---

### Post by axelmasok on 2010-11-30
> **pricetech said:**
> Are BlueTooth and Wireless both on the same card ??

Well I would imagine they are not as lspci shows the wifi adapter being Intel and looking at the kbluetooth bluetooth adapters the BT is listed as BCM2046B1. The BT adapter is not shown in lspci or lsusb so not sure how it interfaces. 
If there isn't a software solution to this then I believe cracking the case open I should be able to remove the BCM2046B1. Maybe.

---

