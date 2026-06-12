---
title: "Unable to scan"
date: 2010-06-08
forum: General Help
---

### Post by frank456 on 2010-06-08
I had some trouble getting the scanner to work after I upgraded
to ubuntu 10.04 LTS.  But I got it to work.  Then when I went
to scan something weeks later it didn't work.  
Xsane image scanner and simple scan can't find the scanner.
I have a Brother MFC-495CW.  It's not listed as supported
by sane but I have had it working before.  Not sure what 
changed.

sane-find-scanner returns
found USB scanner (vendor=0x04f9 [Brother], product=0x022a [MFC-495CW]) at libusb:001:009

scanimage -d test -T
passes the backend test no problem.  

scanimage -L can't find the scanner.

I tried to set the configuration up according to the
documentation online as follows:

/etc/sane.d/dll.conf has an entry for Brother.

I have the following lines near the bottom of 
/lib/udev/rules.d/40-libsane.rules
# Brother scanners
ATTRS{idVendor}=="04f9", ENV{libsane_matched}="yes"

I have the following lines near the bottom of 
/etc/udev/rules.d/45-libmtp7.rules
# Brother scanner
ATTRS{idVendor}=="04f9",ATTRS{idProduct}=="022a", MODE="664", GROUP="scanner", ENV(libsane_matched)="yes"

Any help will be greatly appreciated.

Frank

---

