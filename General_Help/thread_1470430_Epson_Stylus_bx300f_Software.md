---
title: "Epson Stylus bx300f Software"
date: 2010-05-02
forum: General Help
---

### Post by Hambombj on 2010-05-02
Hi ,
I have the above printer/scanner/fax machine

Does anyone know how I can get the scanner/fax to work with ubuntu 10.04?
and also get the ink levels and dock the print shuttle to change the cartridges.


:confused:

---

### Post by Jan Sloep on 2010-05-06
The strange thing is that this scanner was automatically recognized by the release candidate of Ubuntu 10.04 but after a fresh install of the LTS version it is not recognized anymore, while sane-find-scanner indeed finds the scanner? Has it maybe something to do with rights?

---

### Post by Jan Sloep on 2010-05-06
I made a mistake in my above comment. Apparently I downloaded and installed one of the drivers on this page  [http://www.avasys.jp/lx-bin2/linux_e/spc/DL2.do](http://www.avasys.jp/lx-bin2/linux_e/spc/DL2.do) before. 

This installs "Imagescan for Linux" in the Graphics menu and the driver is also recognized by "Xsane" and "Simple Scan" so you can use any of these scanning programs you like.

---

### Post by Hambombj on 2010-05-07
Hi,
i have downloaded and installed Imagescan etc, and now whilst it does recognise that there is a scanner, it classes it as Epson unknown and still cant communicate with the scanner.
any ideas?

---

### Post by Hambombj on 2010-05-07
Hold my last post! Rewind ........ and start again !

I downloaded some codecs etc, re-started again, and now the scanner works!!!

:p

---

### Post by retrozoneorg on 2010-07-30
Hi There,

I have tried everything in these posts.
I have installed the Avasys Drivers.
I have altered the epkowa.conf, dll.conf & epson2.conf files with  the code from these posts but Xsane can still not find the scanner.

According to the xsane website the printer and scanner are supported.
Has anyone figured out how to enable scanning for the BX300F yet?

Please let me know... This is the 3rd time I've tried to convert to  linux (2nd time for ubuntu) and away from M$. I need this scanner for  work use and if I can't get it working I will have to go back to XP.

---

