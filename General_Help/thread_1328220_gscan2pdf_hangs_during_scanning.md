---
title: "gscan2pdf hangs during scanning"
date: 2009-11-16
forum: General Help
---

### Post by GiganticDays on 2009-11-16
Using a Samsung CLX-2160 MFP with the Samsung Unified driver on Karmic.

When I try to scan a doc using gscan2pdf, it detects the scanner ok and begins the scan, but the progress bar stops near the end and just sits there. The scanner reader returns to the start but the scanner display says "scanning".

I tried running gscan2pdf from the terminal using the -debug option so, if anyone wants the full output I have it. The last few lines are:-

Exception 425: unable to read image data `/tmp/XXwrCLCV7K/out1.pnm' @ pnm.c/ReadPNMImage/762 at /usr/bin/gscan2pdf line 5807.
Use of uninitialized value $format in string ne at /usr/bin/gscan2pdf line 1553.
Use of uninitialized value $width in division (/) at /usr/bin/gscan2pdf line 1564.
Use of uninitialized value $height in division (/) at /usr/bin/gscan2pdf line 1564.
*** unhandled exception in callback:
***   Illegal division by zero at /usr/bin/gscan2pdf line 1564.
***  ignoring at /usr/bin/gscan2pdf line 10341.

Anyone help with this?

I'd really like to migrate from Windows completely but this is a deal-breaker.

P.S. Brand new to Ubuntu (and Linux) so be gentle.

---

### Post by GiganticDays on 2009-11-20
3 days and no replies. Nobody had this before?

I've reinstalled Ubuntu three times (for other reasons than the scanning issue), and the problem remains.

---

### Post by GiganticDays on 2009-11-22
So I've just realised that xsane can save to pdf as well - even multipage files. Marvellous.

Wouldn't mind knowing what was wrong with gscan2pdf though

---

### Post by haralf on 2009-11-22
Hi,

I had the same problem and also tried other solutions.

Then, during investigation I needed pdftk:
sudo apt-get install pdftk

afterwards gscan2pdf worked, too.

Hope this helps.

  Harald

---

### Post by GiganticDays on 2009-11-22
Thanks for the input, but that hasn't made any difference to my problem. Even tried a reboot!

---

