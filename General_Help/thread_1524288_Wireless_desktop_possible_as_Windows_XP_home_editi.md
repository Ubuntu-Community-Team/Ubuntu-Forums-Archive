---
title: "Wireless desktop possible as Windows XP home edition?"
date: 2010-07-05
forum: General Help
---

### Post by eugenically on 2010-07-05
[COLOR=magenta]I am not a gaming craze but there is not the least ability to access the Internet wirelessly through my newly installed Ubuntu, kernel 2.6.20-15-generic operating system that co-exists with my former Windows XP Home Edition; anyone can help me to solve the problem proudly.[/COLOR]
[COLOR=#ff00ff]I add here my home computor's networking track for you to help me with ease.[/COLOR]
[EMAIL="robin@eugenically:~$"]robin@eugenically:~$[/EMAIL] lsusb
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 001: ID 0000:0000
[EMAIL="robin@eugenically:~$"]robin@eugenically:~$[/EMAIL] lspci
00:00.0 Host bridge: Intel Corporation 82845 845 (Brookdale) Chipset Host Bridge (rev 04)
00:01.0 PCI bridge: Intel Corporation 82845 845 (Brookdale) Chipset AGP Bridge (rev 04)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 05)
00:1f.0 ISA bridge: Intel Corporation 82801BA ISA Bridge (LPC) (rev 05)
00:1f.1 IDE interface: Intel Corporation 82801BA IDE U100 (rev 05)
00:1f.2 USB Controller: Intel Corporation 82801BA/BAM USB (Hub #1) (rev 05)
00:1f.3 SMBus: Intel Corporation 82801BA/BAM SMBus (rev 05)
00:1f.4 USB Controller: Intel Corporation 82801BA/BAM USB (Hub #2) (rev 05)
00:1f.5 Multimedia audio controller: Intel Corporation 82801BA/BAM AC'97 Audio (rev 05)
01:00.0 VGA compatible controller: ATI Technologies Inc Rage 128 Pro Ultra TF
02:09.0 Communication controller: Conexant HSF 56k Data/Fax Modem (rev 01)
02:0a.0 Ethernet controller: Davicom Semiconductor, Inc. 21x4x DEC-Tulip compatible
10/100 Ethernet (rev 31)
02:0b.0 Network controller: Texas Instruments ACX 111 54Mbps Wireless Interface
[EMAIL="robin@eugenically:~$"]robin@eugenically:~$[/EMAIL]

---

### Post by efflandt on 2010-07-05
What Ubuntu version?  That looks like an old kernel.

What kind of wireless device is it.  Post the line that shows it from **lspci** typed in a terminal if it is internal, or **lsusb** if USB.

---

### Post by eugenically on 2010-07-08
> **efflandt said:**
> What Ubuntu version? That looks like an old kernel.
 
What kind of wireless device is it. Post the line that shows it from **lspci** typed in a terminal if it is internal, or **lsusb** if USB.
Dear Sir,
[EMAIL="robin@eugenically:~$"]robin@eugenically:~$[/EMAIL] lsusb
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 001: ID 0000:0000
[EMAIL="robin@eugenically:~$"]robin@eugenically:~$[/EMAIL] lspci
00:00.0 Host bridge: Intel Corporation 82845 845 (Brookdale) Chipset Host Bridge (rev 04)
00:01.0 PCI bridge: Intel Corporation 82845 845 (Brookdale) Chipset AGP Bridge (rev 04)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 05)
00:1f.0 ISA bridge: Intel Corporation 82801BA ISA Bridge (LPC) (rev 05)
00:1f.1 IDE interface: Intel Corporation 82801BA IDE U100 (rev 05)
00:1f.2 USB Controller: Intel Corporation 82801BA/BAM USB (Hub #1) (rev 05)
00:1f.3 SMBus: Intel Corporation 82801BA/BAM SMBus (rev 05)
00:1f.4 USB Controller: Intel Corporation 82801BA/BAM USB (Hub #2) (rev 05)
00:1f.5 Multimedia audio controller: Intel Corporation 82801BA/BAM AC'97 Audio (rev 05)
01:00.0 VGA compatible controller: ATI Technologies Inc Rage 128 Pro Ultra TF
02:09.0 Communication controller: Conexant HSF 56k Data/Fax Modem (rev 01)
02:0a.0 Ethernet controller: Davicom Semiconductor, Inc. 21x4x DEC-Tulip compatible
10/100 Ethernet (rev 31)
02:0b.0 Network controller: Texas Instruments ACX 111 54Mbps Wireless Interface
[EMAIL="robin@eugenically:~$"]robin@eugenically:~$[/EMAIL] 
Above is my home computer that could not get through the Internet with Ubuntu, please help me further if it is possible.
Thank you very much anyway.

---

### Post by aeiah on 2010-07-08
ACX 111 is the important bit. try searching for solutions based on that. from the looks of things a lot of documentation refers to older versions of ubuntu. this is either because it should work out of the box now, or because this card is very old and now quite rare.

try looking here, perhaps:
[http://ubuntuforums.org/showthread.php?t=892691&highlight=acx+111](http://ubuntuforums.org/showthread.php?t=892691&highlight=acx+111)
but bare in mind that this thread will refer to an older version of ubuntu to what you're probably using

---

