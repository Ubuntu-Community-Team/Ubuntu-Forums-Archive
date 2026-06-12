---
title: "epson printer won't work"
date: 2010-10-20
forum: General Help
---

### Post by tszanon on 2010-10-20
I installed my epson stylus tx420w through cups web interface. I used the PPD file provided by the driver recommended in linuxprinting.org.
But when I try to print the test page (or anything else), nothing is printed. According to the diagnostics, the printer status is "*Processing page 1...*", but it won't go beyond that.
I've already tested it, it's fine. But won't work in ubuntu. :(
Don't know what's going on...any ideas? Everything seems to be fine. I'm using an USB cable.

---

### Post by ellgor on 2010-10-21
Hi,

Go to this site, "Avasys" and check out their drivers, if your printer has a scanner as well, whilst on the download page for your printer, scroll down near the bottom and look for for an app called "imagescan.deb" totally seperate package from the printing one, but a must.

Regards, Ellgor.

---

### Post by Mark Phelps on 2010-10-21
Results will vary by specific printer model, but I've found with my Epson R200, the CUPS-Gutenprint drivers, ever since Ubuntu 10.04, have been the best drivers available.

I would remove the printer and try adding it again, this time selecting make and model, and then selecting the CUPS-Gutenprint driver.

Don't know if they have one for you specific printer, but it's worth trying.

---

### Post by philinux on 2010-10-21
The nearest driver from sys>admin><printing is a TX410

---

### Post by tszanon on 2010-10-21
> **philinux said:**
> The nearest driver from sys>admin><printing is a TX410
Exactly. But I haven't tried this one, because the driver I'm using (epson-nx420) is not designed for the tx410.
And, by the way, this epson-nx420 is the very same driver provided by avasys.

I've downloaded the Image Scan software, but it doesn't work either. I don't know why, but the scanner isn't detected.

The device is detected by lsusb:
```
Bus 002 Device 007: ID 04b8:0864 Seiko Epson Corp. 
```
The installation works fine, but only if I do it in the web interface. Installing the printer in System > Admin > Printers give me an error message.

Linuxprinting says it works perfectly, so I think I shouldn't be having any problems...there must be something very wrong in my computer. I'm gonna try some other stuff.

---

### Post by tszanon on 2010-10-21
I'd like to add that the tx410 driver is no good. First, half a billion white pages, then some pages full of trash.

I'll keep trying.

---

