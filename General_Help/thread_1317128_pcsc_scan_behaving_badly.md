---
title: "pcsc_scan behaving badly"
date: 2009-11-06
forum: General Help
---

### Post by Lachlanus on 2009-11-06
I am attempting to install the software necessary to get my CAC reader to work.  When I run pcsc_scan, I get the following:

> PC/SC device scanner
V 1.4.15 (c) 2001-2009, Ludovic Rousseau <ludovic.rousseau@free.fr>
Compiled with PC/SC lite version: 1.4.102
Scanning present readers...
0: SCM SCR 331 (21120808222597) 00 00

Fri Nov  6 13:08:34 2009
 Reader 0: SCM SCR 331 (21120808222597) 00 00
  Card state: Card inserted, 
  ATR: 3B 95 95 40 FF AE 01 03 00 00

ATR: 3B 95 95 40 FF AE 01 03 00 00
+ TS = 3B --> Direct Convention
+ T0 = 95, Y(1): 1001, K: 5 (historical bytes)
  TA(1) = 95 --> Fi=512, Di=16, 32 cycles/ETU
    125000 bits/s at 4 MHz, fMax for Fi = 5 MHz => 156250 bits/s
  TD(1) = 40 --> Y(i+1) = 0100, Protocol T = 0 
-----
  TC(2) = FF --> Work waiting time: 960 x 255 x (Fi/F)
+ Historical bytes: AE 01 03 00 00
  Category indicator byte: AE (proprietary format)

Possibly identified card (using /usr/share/pcsc/smartcard_list.txt):
3B 95 95 40 FF AE 01 03 00 00
	Axalto - Cyberflex 64K
	Gemalto TOP IM FIPS CY2 (product code HWP115291A)


After that, nothing happens--I have to ctrl-c to get back to the prompt.  I am running Ubuntu 9.10 and have the SCR331 reader.  Why won't it complete the scan?  I have gotten libusb, pcsc-lite, pcsc-tools, and ccid to config, make, and make install.  I have gotten coolkey to config, but it spits out errors when I try to make it.  I wasn't sure if making coolkey was necessary, since I hear Ubuntu comes with it already installed now.

---

### Post by Lachlanus on 2009-11-10
can anyone help?

---

