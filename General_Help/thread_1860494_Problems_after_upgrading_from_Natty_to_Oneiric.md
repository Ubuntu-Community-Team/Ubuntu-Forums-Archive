---
title: "Problems after upgrading from Natty to Oneiric"
date: 2011-10-14
forum: General Help
---

### Post by szafran on 2011-10-14
Hi,

I'm having some problems of getting stuff that worked perfectly on Natty to work on Oneiric. It upgraded without any errors. Some problems (eg not booting if SAS controler is connected, NIC problems, and some other small problems) I have been able to correct on my own. But I had installed (and working) GDM on Natty. Now it doesn't start. Also NUT is not recognizing my UPS (using the same driver that was used on Natty).

As for UPS. Doing lsusb gives:
...
Bus 004 Device 002: ID 0665:5161 Cypress Semiconductor USB to Serial
...

So the UPS is connected properly, and discovered by the system.

As for GDM I have no idea what to do. I've tried reinstalling it. After booting I can see the screen going black and resolution changeing, but after a second or two it comes back to console. I've also tried installing net ati drivers, but that didn't help, and fglrxinfo gives:

Error: unable to open display (null)

xorg logs attached.

I'm using a headless config with Ubuntu Server 11.10, and it has an integrated Radeon:

01:05.0 VGA compatible controller: ATI Technologies Inc RS880 [Radeon HD 4290]

____________
Regards
Szafran

---

