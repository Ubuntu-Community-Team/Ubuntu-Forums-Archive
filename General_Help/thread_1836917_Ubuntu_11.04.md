---
title: "Ubuntu 11.04"
date: 2011-08-31
forum: General Help
---

### Post by theozzlives on 2011-08-31
I upgraded to 11.04 and my wireless don't work. It says the sta driver is in use and I tried ```
sudo apt get install brodcom-sta-common
``` to no avail. I clack on the network manager and get no wireless networks. I have wired, but no wireless. Please help!

---

### Post by theozzlives on 2011-09-08
Bump

---

### Post by theozzlives on 2011-11-06
bump

---

### Post by lafskelton on 2011-11-06
you can goto the broadcom wirless site and download the source code for sta cards

---

### Post by lafskelton on 2011-11-06
also Try restarting the computer

---

### Post by theozzlives on 2011-12-19
I NEED to get this to work! my lspci is:
```
ozzie@ozzie-netbook:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 01)
00:1c.1 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 2 (rev 01)
00:1c.2 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 3 (rev 01)
00:1d.0 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 01)
02:01.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev b4)
02:01.1 FireWire (IEEE 1394): Ricoh Co Ltd R5C552 IEEE 1394 Controller (rev 09)
02:01.2 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 18)
09:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5752 Gigabit Ethernet PCI Express (rev 02)
0c:00.0 Network controller: Broadcom Corporation BCM4311 802.11b/g WLAN (rev 01)

```

Please help!

---

### Post by theozzlives on 2011-12-20
Bump

---

### Post by theozzlives on 2011-12-21
BUMP damnit!

---

### Post by theozzlives on 2011-12-29
bump

---

### Post by pretty_whistle on 2011-12-29
I have 11.04.  My SSID is hidden so I had to hit the wireless icon on the panel and then on the menu that appears I had to select Connect to hidden wireless network.  Then just put in the SSID (network name), choose the security type, then put in the password.

That was it.

If your network isn't hidden it should show up on the available networks it finds.

---

### Post by theozzlives on 2012-01-03
> **pretty_whistle said:**
> I have 11.04.  My SSID is hidden so I had to hit the wireless icon on the panel and then on the menu that appears I had to select Connect to hidden wireless network.  Then just put in the SSID (network name), choose the security type, then put in the password.

That was it.

If your network isn't hidden it should show up on the available networks it finds.

It's the driver, my network is not hidden.

---

### Post by theozzlives on 2012-01-07
Bump Already! I know someone knows the answer to this!

---

