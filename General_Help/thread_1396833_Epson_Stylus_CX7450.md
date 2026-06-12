---
title: "Epson Stylus CX7450"
date: 2010-02-02
forum: General Help
---

### Post by DTM84 on 2010-02-02
Haven't been able to get my scanner to work on my Epson Stylus CX7450. XSane doesn't seem to support my scanner. Is there a way around this?

---

### Post by ellgor on 2010-02-03
Hi,

Go to the "Avasys" site, its for Epsons', and get their Imagescan package, get the deb package and load it with gdebi, works after a reboot.  

Regards, Ellgor.

---

### Post by h8uthemost on 2010-04-27
I'm needing help with this also. I have a Stylus CX7450. And I can't get it to print. Ubuntu(9.04) recognizes the computer, but that's about it. When I go to print the printer just sites there.

I went to that Avasys site that ellgor recommended, but there's no cx7450 on the site.

Anyone got any other ideas?

Thank you for any help.

---

### Post by illunatic on 2011-08-22
BUMP - I am also having trouble getting the Stylus CX7450 to print. It hangs on print processing and never prints. Natty Narwhale 11.04

I installed: 
**[SIZE=2]Epson Inkjet Printer Driver (ESC/P-R) for Linux[/SIZE]**

[http://avasys.jp/eng/linux_driver/download/lsb/epson-inkjet/escpr/](http://avasys.jp/eng/linux_driver/download/lsb/epson-inkjet/escpr/)

Errors (most recent error_log attached):
```
E [21/Aug/2011:16:04:45 -0500] [Job 1] File '/System/Library/ColorSync/Profiles/sRGB Profile.icc' not found
E [21/Aug/2011:16:11:45 -0500] [Job 2] File '/System/Library/ColorSync/Profiles/sRGB Profile.icc' not found
E [21/Aug/2011:16:22:44 -0500] [Job 2] Unable to write print data: Input/output error

```I am also getting a pop-up "Printer not connected?"

Edit: usb-device outputs the following:

```
T:  Bus=02 Lev=01 Prnt=01 Port=00 Cnt=01 Dev#= 10 Spd=480 MxCh= 0
D:  Ver= 2.00 Cls=00(>ifc ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=04b8 ProdID=0838 Rev=01.00
S:  Manufacturer=EPSON
S:  Product=USB2.0 MFP(Hi-Speed)
S:  SerialNumber=4C36313031478FF071
C:  #Ifs= 3 Cfg#= 1 Atr=c0 MxPwr=2mA
I:  If#= 0 Alt= 0 #EPs= 2 Cls=ff(vend.) Sub=ff Prot=ff Driver=(none)
I:  If#= 1 Alt= 0 #EPs= 2 Cls=07(print) Sub=01 Prot=02 Driver=usblp
I:  If#= 2 Alt= 0 #EPs= 2 Cls=08(stor.) Sub=06 Prot=50 Driver=usb-storage

```

Edit 2: The printer works fine. It turned out to be a problem with a print cartridge.
I did add a .icm file (icc profile) from the Windows 32 bit driver.

---

