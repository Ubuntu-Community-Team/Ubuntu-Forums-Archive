---
title: "Cannot remove old printer"
date: 2009-08-07
forum: General Help
---

### Post by fopetesl on 2009-08-07
5.10 "Breezy Badger"
Cannot reset printer correctly.

Initially I had an HP Deskjet 5550 on USB #1.
Now when I want to install another HP Deskjet I cannot get it to print.
i.e. via localhost:631 I can delete and add the correct printer BUT USB #1 always shows as "USB #1 (hp deskjet 5550)".  Even after deleting.

So, to keep the new printer alive with beh, I have to add the identifer usb://Deskjet5650?Serial=MY82Z6711Q1
This is from the 'old' 5550 so the new printer refuses to play.
Probably because the new printer does not have this serial number?

If I plug in the 5550 it still tries to work.
How do I remove this 5550 ?serial number and get back to usb:/dev/usb/lp0?

---

### Post by tgalati4 on 2009-08-07
Perhaps there is a printer defined in the Gnome--Printer-Setup utility.

There could also be a USB device that is defined in the USB Hotplug that keeps recreating the old printer.

I have one Dapper machine, so I don't know how usb hotplug is handled in Breezy.

---

### Post by fopetesl on 2009-08-07
> **tgalati4 said:**
> Perhaps there is a printer defined in the Gnome--Printer-Setup utility.
Umm. I don't think I have Gnome--Printer-Setup.  I use XFCE in kiosk mode.
> There could also be a USB device that is defined in the USB Hotplug that keeps recreating the old printer.Where would I look?

---

### Post by tgalati4 on 2009-08-07
XFCE has a printer-setup utility.  You will have to search for it.  That is probably where the printer is defined--independently  of CUPS.  

I don't have a Breezy machine, so you are on your own to search for hotplug and hal usb configuration files.

On Dapper:

man udev
Look at files in /etc/udev and /var/log/udev

---

