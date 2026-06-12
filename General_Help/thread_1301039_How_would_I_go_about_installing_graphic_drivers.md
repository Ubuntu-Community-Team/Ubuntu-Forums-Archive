---
title: "How would I go about installing graphic drivers?"
date: 2009-10-25
forum: General Help
---

### Post by segamaster222 on 2009-10-25
I'm using Ubunbu netbook remix on my MSI wind u100 and the out put of lspci is

> 00:00.0 Host bridge: Intel Corporation Mobile 945GME Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GME Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
01:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)
02:00.0 Network controller: RaLink RT2860


Thanks :)

---

### Post by P4man on 2009-10-25
You already have them. no need to download anything.

---

### Post by segamaster222 on 2009-10-25
> **P4man said:**
> You already have them. no need to download anything.

That's weird, cause every game I run in wine even something like starcraft lags and I can't play chess in 3D cause I don't have open GL.

every game I run period lags.

Or am I thinking of a different problem all together?

---

### Post by P4man on 2009-10-25
You got a .. fairly crappy onboard videocard there

Try disabling desktop effects before starting the game.
Also Karmic supposedly has much improved support for intel onboard gpu's. Are you running karmic or jaunty ? (9.04 or 9.10RC)

---

### Post by segamaster222 on 2009-10-25
> **P4man said:**
> You got a .. fairly crappy onboard videocard there

Try disabling desktop effects before starting the game.
Also Karmic supposedly has much improved support for intel onboard gpu's. Are you running karmic or jaunty ? (9.04 or 9.10RC)

Distributor ID: Ubuntu
Description:    Ubuntu 9.04
Release:        9.04
Codename:       jaunty

Thanks for the suggestion, will defanatley try.

---

### Post by Mark Phelps on 2009-10-26
Realize, though, that 9.10 will still only install the default Intel graphics drivers.  If they don't provide the performance you want, there are no alternative restricted drivers that you can install.

---

