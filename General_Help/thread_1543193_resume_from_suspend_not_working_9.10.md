---
title: "resume from suspend not working 9.10"
date: 2010-07-31
forum: General Help
---

### Post by speed32219 on 2010-07-31
Karmic 2.6.31-22-generic, Asus M3N78-EM, MCE remote with USB/IR dongle, latest Bios, Bios PM enable and set for suspend S3. IT will suspend but I need to depress case power button for it to resume.  I want to use my remote control, I also can not get it to resume from Keyboard/mouse (See Note Below). Only suspend and power button work. 

$ **lsusb**
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
**Bus 004 Device 002**: ID 147a:e03c Formosa Industrial Computing, Inc.
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 046d:c517 Logitech, Inc. LX710 Cordless Desktop Laser
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

$**lspci**
00:02.0 USB Controller: nVidia Corporation MCP78S [GeForce 8200] OHCI USB 1.1 Controller (rev a1)
00:02.1 USB Controller: nVidia Corporation MCP78S [GeForce 8200] EHCI USB 2.0 Controller (rev a1)
00:04.0 USB Controller: nVidia Corporation MCP78S [GeForce 8200] OHCI USB 1.1 Controller (rev a1)
00:04.1 USB Controller: nVidia Corporation MCP78S [GeForce 8200] EHCI USB 2.0 Controller (rev a1)

***NOTE:***
$**cat /proc/acpi/wakeup | grep USB**
USB0      S4     disabled  pci:0000:00:02.0
USB2      S3     **disabled**  pci:0000:00:02.1

If I enable USB2 it suspends but it **immediately resumes**.  
$echo USB2 > /proc/acpi/wakeup
 
 #  cat /proc/acpi/wakeup | grep USB
USB0      S4     disabled  pci:0000:00:02.0
USB2      S3     **enabled **  pci:0000:00:02.1

What am I missing?

---

### Post by speed32219 on 2010-08-01
I wasn't looking at the info provided to me correctly.  I highlighted the areas that were of importance.  The device was on Bus 4, and I was stuck on looking for a USB device that had an S3 entry **cat /proc/acpi/wakeup | grep USB**.  I should have been looking at the Bus entry and cross referencing that in the lsusb command were it listed the Formosa Industrial Computing line below.  Hope this helps someone else having a problem with resume from suspend using a remote.


lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
**Bus 004 **Device 002: ID 147a:e03c Formosa Industrial Computing, Inc.
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 046d:c517 Logitech, Inc. LX710 Cordless Desktop Laser
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

$**cat /proc/acpi/wakeup ** 
Device  S-state   Status   Sysfs node
SMB0      S4     disabled  pci:0000:00:01.1
USB0      S4     disabled  pci:0000:00:02.0
USB2      S3     disabled  pci:0000:00:02.1
**US15      S4     enabled   pci:0000:00:_[COLOR="Blue"]04[/COLOR]_.0**
US12      S3     disabled  pci:0000:00:04.1
NMAC      S5     disabled  pci:0000:00:0a.0
P0P1      S4     disabled  pci:0000:00:08.0
HDAC      S4     disabled  pci:0000:00:07.0
MXR0      S4     disabled  pci:0000:00:10.0
BR11      S4     disabled
BR12      S4     disabled  pci:0000:00:12.0
BR14      S4     disabled
BR15      S4     disabled
BR16      S4     disabled
BR17      S4     disabled
BR13      S4     disabled  pci:0000:00:13.0

---

