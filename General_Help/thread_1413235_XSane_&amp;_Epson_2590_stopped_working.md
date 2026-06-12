---
title: "XSane &amp; Epson 2590 stopped working"
date: 2010-02-22
forum: General Help
---

### Post by MickG01 on 2010-02-22
2 days ago on Ubuntu 9.10 my scanner was working fine under xsane
Now it gives:
failed to open device 'snapscan:libusb:001:002':Invalid Argument

in a terminal I get this:

sane-find-scanner:
...
found USB scanner (vendor=0x04b8 [EPSON], product=0x0122 [EPSON Scanner]) at libusb:001:002
...

scanimage -L
No scanners were identified. If you were expecting something different,
check that the scanner is plugged in, turned on and detected by the
sane-find-scanner tool (if appropriate). Please read the documentation
which came with this software (README, FAQ, manpages).

the device epson2 is enabled in /etc/sane.d/dll.conf

The scanner is an epson perfection 3590 PHOTO

The only thing installed during this time was Java required for a web site under firefox.

Any suggestions?

---

