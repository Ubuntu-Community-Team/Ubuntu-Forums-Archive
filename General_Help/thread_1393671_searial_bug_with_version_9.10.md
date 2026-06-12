---
title: "searial bug with version 9.10?"
date: 2010-01-29
forum: General Help
---

### Post by loki_dre on 2010-01-29
I get the following error when BOOTING up with Ubuntu 9.10 & in dmesg:
phy0: noise floor calibration timeout
what does this mean & any ideas how to fix it?

I think it is also causing one of my USB Serial devices to work improperly.
I tried changing all the hardware (laptop(motherboard etc.), USB Serial device, & USB hub) but that did not resolve the issue.
My code was previously working on an older version of ubuntu (9.04).

Problem noticed:
As I boot up (before any of my software is run), bytes are written to my USB Serial (FTDI SIO) device.
I also tried this on a fresh install & it appears that some bytes are being written to the serial divice(20 x 2 character LCD) while it is booting up
Is there a bug with Ubuntu 9.10?

---

### Post by Jefferythewind on 2010-01-29
Can you actually boot up into the OS, or are you hanging up before hand?  

If you can't even get into the system I would say to change the boot order in your BIOS so that USB is behind HDD.

---

### Post by loki_dre on 2010-01-29
I can boot up & log in and everything else seems fine except for my 'FTDI SIO' usb serial port
It seems to write to the serial port after Ubuntu bootup graphics are shown.

---

### Post by Jefferythewind on 2010-01-30
Sorry, I don't know about that.

---

