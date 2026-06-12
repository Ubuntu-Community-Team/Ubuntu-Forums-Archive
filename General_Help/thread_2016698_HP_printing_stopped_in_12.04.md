---
title: "HP printing stopped in 12.04"
date: 2012-07-04
forum: General Help
---

### Post by standell on 2012-07-04
hello, 

printing to an HP OfficeJet G85 worked in 11.10 64-bit and stopped when i updated to 12.04 64-bit. i've muddle around for a while on my own and have gotten  nowhere, in fact, after an update to HPLIP  3.12.6 it got worse. i am running cups 1.5.3

right after update to 12.04 when i tried to print the light on the printer would blink, but nothing ever printed - jobs stayed in the print queue. after an auto-update to HPLIP 3.12.6, the printer, which is connected via USB, is no longer even detected when i run hp-setup. and maybe that's a lie because i commented out 'blacklist usblp' (described below) and now hp-check says this about the printer:OfficeJet_G85
-------------
Type: Printer
Device URI: hp:/usb/OfficeJet_G85?serial=SGG22E15MHVL
PPD: /etc/cups/ppd/OfficeJet_G85.ppd
PPD Description: HP Officejet g85, hpcups 3.12.6
Printer status: printer OfficeJet_G85 is idle.  enabled since Wed 04 Jul 2012 02:03:47 PM EDT
error: Unable to communicate with device (code=12): hp:/usb/OfficeJet_G85?serial=SGG22E15MHVL
error: Device not found
error: Communication status: Failed

it seems like it's detecting it in some way... from some other thread, i commented the following line /etc/modprobe.d/blacklist-cups-usblp.conf
#blacklist usblp

i did this because at one point the printer was not detect at all and the thread said this might be a solution. i've purged... and re-installed... and blah,blah, blah so many times this system is probably all sort of screwed up by now.... 

any help is appreciated. oh, yeah, if it matters this is running on an amd 8-core cpu, 64-bit.

thanks.

---

