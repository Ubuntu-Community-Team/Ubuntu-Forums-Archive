---
title: "Can't use Wifi"
date: 2010-10-24
forum: General Help
---

### Post by rogat on 2010-10-24
Halow dude...
Actually my computer OS is LM, i got depression, i don't know what should i do. Please help me. i has installed the compat wireless, but wifi seems no working at all. FYI, Wifi chipset is atheros ar9285, kernel 2.6.32

---

### Post by rhoparkour on 2010-10-24
Hey man, I assume that by LM you mean Linux Mint. I don't know much about it, but on Lucid the problem is fixed with:

1. Connect with a wired (ethernet) connection.
2. System > Administration > Hardware Drivers
3. Choose the propietary driver to download and activate.

Lucid takes care of it for you.... Don't know about LM, but on Fedora, I just researched my wireless card maker and got the right drivers, then installes them by hand.... 

Let me know if this was useless or if it helped you.

---

### Post by rogat on 2010-10-27
thx 4 reply, but when i do that, i just get the driver 4 my graphics card, no anything else. I had installed the backport modules wireless too, but it just the same, what do i do?

---

### Post by Megaptera on 2010-10-27
What version of Linux Mint, please?

---

### Post by IIC0RRUPT10NII on 2010-10-27
Was Advised to create own thread, Edited out.

---

### Post by Megaptera on 2010-10-27
> **IIC0RRUPT10NII said:**
> Hello, I am also having the same problem with Ubuntu 10.4, wireless just says disconnected, anyways I figured out that 9.10 will allow wired to work but not wireless, my atheros card is the same as the above poster. When I go into hardware drivers it states there are no proprietary drivers. Iv installed compat and the restricted drivers but to no avial. here is a copy of my info

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

Please start your OWN thread otherwise no one can tell who is answering which question.

---

