---
title: "Ubuntu Atheros 9285 Toshiba wifi problem after 9.10"
date: 2010-10-27
forum: General Help
---

### Post by IIC0RRUPT10NII on 2010-10-27
Hello, I am having problem with Ubuntu 10.4, wireless just  says disconnected, anyways I figured out that 9.10 will allow wireless to  work but not wired, but when I update 10.4 does not allow wireless or wired to work until I install Compat yet wireless still does not work.. my atheros card is 9285.  When I go into hardware drivers it states there are no proprietary  drivers. Iv installed compat and the restricted drivers but to no avial.  here is a copy of my info

00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:02.1 Display controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
00:1c.4 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.3 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
02:00.0 Ethernet controller: Attansic Technology Corp. Device 2060 (rev c1)
03:00.0 Network controller: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) (rev 01)

---

### Post by IIC0RRUPT10NII on 2010-10-27
Bump --- Can anyone help with this problem it is a big one for me..

---

### Post by IIC0RRUPT10NII on 2010-10-27
Ok everyone I have solved this problem without knowing exactly what I did but, what I did was after using 9.10 I updated to 10.4 which disallowed both wired and wireless drivers from working, I then installed compat wireless which got my wired driver working and I disabled LTS to allow my update to update to 10.10 after updating my wireless and wired both worked, I do not know is this is from just the distro upgrade or a combination of compat and distro upgrade but thanks to it I have resolved the issue of wireless and can now search and connect to networks! please mark this as solved.

---

