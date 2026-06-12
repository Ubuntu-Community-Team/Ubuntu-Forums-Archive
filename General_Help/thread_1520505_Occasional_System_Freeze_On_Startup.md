---
title: "Occasional System Freeze On Startup"
date: 2010-06-29
forum: General Help
---

### Post by Joshun on 2010-06-29
Hi, so far i'm really enjoying ubuntu lucid, but this one issue is really annoying. Sometimes, when I turn on my computer to boot ubuntu, it freezes, not straight away, but around the time that it has loaded with five dots. Waiting for a period of time makes no difference, it just sits there. I once caught a glimpse of what was going on - it looked like a kernel panic or something. I've attached the major system logs, if there is any more you need then I can add them on.

Thankyou

Joshua

Hardware: eeepc 1001ha

output of lspci:

00:00.0 Host bridge: Intel Corporation Mobile 945GME Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GME Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 2 (rev 02)
00:1c.3 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 4 (rev 02)
00:1d.0 USB Controller: Intel Corporation N10/ICH7 Family USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.2 SATA controller: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA AHCI Controller (rev 02)
01:00.0 Ethernet controller: Atheros Communications Atheros AR8132 / L1c Gigabit Ethernet Adapter (rev c0)
02:00.0 Network controller: RaLink RT3090 Wireless 802.11n 1T/1R PCIe

NOTE: I enabled bootlogging via /var/log/boot.log, but due to the freeze it hadn't logged it here.

---

### Post by Joshun on 2010-06-29
Bump

---

### Post by Joshun on 2010-07-16
I have attached photos of the error from the freeze, I had to take them with a camera as it doesn't log these for some reason.

I am unsure what is causing this still, looks like a kernel panic or something.

---

