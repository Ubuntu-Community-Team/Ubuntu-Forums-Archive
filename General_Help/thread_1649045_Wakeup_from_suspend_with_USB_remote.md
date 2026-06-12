---
title: "Wakeup from suspend with USB remote"
date: 2010-12-19
forum: General Help
---

### Post by wjoyce on 2010-12-19
Hi,

I'm setting up a HTPC and everything is working great except for waking from suspend using my media centre remote.  It resumes ok with the power button on the unit, but not the remote.

I've checked [FONT="Courier New"]/proc/acpi/wakeup[/FONT] and it shows the following.

```
Device	S-state	  Status   Sysfs node
C096	  S5	*disabled  pci:0000:00:1e.0
[COLOR="Red"]C0F1	  S3	*disabled  pci:0000:00:1d.0
C0F8	  S3	*disabled  pci:0000:00:1d.1
C0F9	  S3	*disabled  pci:0000:00:1d.2
C0FA	  S3	*disabled  pci:0000:00:1d.3
C0FB	  S3	*disabled  pci:0000:00:1d.7[/COLOR]
C102	  S5	*disabled  pci:0000:00:1c.0
C22B	  S5	*disabled  pci:0000:08:00.0
C115	  S5	*disabled  pci:0000:00:1c.2
C22C	  S5	*disabled  
C118	  S5	*disabled  pci:0000:00:1c.3
C22C	  S5	*disabled  

```

lspci shows
```
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 01)
00:1c.2 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 3 (rev 01)
00:1c.3 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 4 (rev 01)
00:1d.0 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01)
00:1f.2 SATA controller: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA AHCI Controller (rev 01)
02:06.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
02:06.1 FireWire (IEEE 1394): Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller
02:06.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)
02:06.3 SD Host controller: Texas Instruments PCIxx12 SDA Standard Compliant SD Host Controller
02:06.4 Communication controller: Texas Instruments PCIxx12 GemCore based SmartCard controller
02:0e.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5788 Gigabit Ethernet (rev 03)
08:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02)
```
which indicates that the items highlighted in red in the first box code box are the USB devices.

I've used [FONT="Courier New"]echo **** > /proc/acpi/wakeup[/FONT] to change the status for each one to Enabled, and amended /etc/rc.local to do that but it still won't wake from the remote.  I've been at this all day and still no joy.  Any help would be greatly appreciated - I'm close to chucking it in and going back to windows just because of this one little (but major to the missus) issue. sob.

Output from lsusb for reference
```
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 0471:0815 Philips (or NXP) eHome Infrared Receiver
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 005: ID 08ff:2580 AuthenTec, Inc. AES2501 Fingerprint Sensor
Bus 001 Device 004: ID 03f0:171d Hewlett-Packard Wireless (Bluetooth + WLAN) Interface [Integrated Module]
Bus 001 Device 002: ID 0424:2503 Standard Microsystems Corp. USB 2.0 Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```

---

