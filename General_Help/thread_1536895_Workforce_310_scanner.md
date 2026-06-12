---
title: "Workforce 310 scanner"
date: 2010-07-22
forum: General Help
---

### Post by eddugo on 2010-07-22
Has anyone had success getting the Epson Workforce 310 Scanner working. The printer works right out of the box. I have added the new drivers from AVASYS and it finds it but I get an error message: Failed to open device `epkowa:001:005': 
          Access to resource has been denied

Thank you in advance for any help

---

### Post by hansdown on 2010-07-22
Hi eddugo.

This scanner is working in linux, I think.

You need this driver.

epson-inkjet-printer-escpr_1.0.0-1 lsb 3.2

[http://avasys.jp/eng/linux_driver/download/lsb/epson-inkjet/escpr/](http://avasys.jp/eng/linux_driver/download/lsb/epson-inkjet/escpr/)

Be sure to install, either the i386.deb, for 32bit, or the amd64.deb, for 64bit.

---

### Post by eddugo on 2010-07-23
Thank you for the reply.  I have that driver installed.  Is there a certain sequence for installing it? Maybe that is why it doesn't work

---

### Post by hansdown on 2010-07-23
> **eddugo said:**
> Thank you for the reply.  I have that driver installed.  Is there a certain sequence for installing it? Maybe that is why it doesn't work

There does appear to be a sequence.

There is some info in the manual. 

[http://avasys.jp/eng/linux_driver/download/lsb/epson-inkjet/escpr/README.html](http://avasys.jp/eng/linux_driver/download/lsb/epson-inkjet/escpr/README.html)

The "installing software, says to install the driver **before** connecting the printer.

Are you connecting with USB?

---

### Post by eddugo on 2010-07-31
Thank you for your reply.  I did all that and the printer works, but the scanner doesn't.  The scanner is recognized, but doesn't work. I had a similar problem with a brother scanner - got the same error message.  That was solved by adding a file to 40libsane.rules.  I got the file from the brother site and it worked.  Can not find a similar file from Epson or Avasys.
Yes I have it connected via usb.

---

### Post by hansdown on 2010-07-31
Have you tried installing

```
simple-scan
```

---

### Post by eddugo on 2010-08-24
Yes I have, and re-installed it also.  Still same error message

---

### Post by Tickon on 2011-07-14
I have the same problem using Epson Workforce 310 on Ubuntu 10.10.
"sane-find-scanner" finds a scanner with strange name:
 found USB scanner (vendor=0x04b8, product=0x0854) at libusb:001:005

but "scanimage -L" finds no scanner.

I just noticed this thread is old... Did you solve your problem?

---

