---
title: "Canon MF4270 Scanner no-go"
date: 2009-07-21
forum: General Help
---

### Post by rwigle on 2009-07-21
I purchased a Canon MF4270 multi-function (laser). I followed the steps in this post to install it.

[http://ubuntuforums.org/showthread.php?t=1140724](http://ubuntuforums.org/showthread.php?t=1140724)

Everything works EXCEPT the scanner. I can print, copy, and duplex output also works.

When I start Xsane it says "no devices available"

If I type sane-find-scanner I get:

found USB scanner (vendor=0x04a9, product=0x26b5) at libusb:002:002

Then if I type scanimage -L it says "no scanners were identified"

I have redone these with or without the Scan button pushed.

I have also re-installed the deb package, but I get the same result.

Help.

---

### Post by rwigle on 2009-07-24
Bump....

I have successfully installed the new drivers for Canon MF4270 printer, now on two systems i) Hardy 8.04.3 and ii) Intrepid 8.10, but I still get "no devices available" when I try to use Xsane..

I have looked at various Sane pages, which say that the MF4270 has good capabilities under Sane, but nothing seems to work. The diagnostics from scanimage -L and sane-find-scanner are the same.

---

