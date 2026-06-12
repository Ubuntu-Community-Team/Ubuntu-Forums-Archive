---
title: "How to use a network-based scanner? (RJ45 not usb)"
date: 2010-10-28
forum: General Help
---

### Post by zoubidoo on 2010-10-28
Hello,

I have a multi-function printer/scanner that plugs straight into the LAN via RJ45.  Printing works fine, but I'm not sure how to proceed to set up the scanner.  Just to be clear, I am not asking about connecting a usb scanner then sharing it over a LAN, that's different.  This scanner plugs straight into the LAN.

Any general advice or pointers to a tutorial much appreciated!

Zoubidoo

---

### Post by zoubidoo on 2010-10-29
Looking at the HPLIP documentation it says that scanning with the device under Ubuntu is supported.  So should scanning applications like Simple Scan and XSane be able to detect the scanner over the network?

[http://hplipopensource.com/hplip-web/models/color_laserjet/hp_color_laserjet_2840.html](http://hplipopensource.com/hplip-web/models/color_laserjet/hp_color_laserjet_2840.html)

---

### Post by zoubidoo on 2010-10-29
I have tried adding the printer/scanner's IP address to /etc/sane.d/net.conf as per the Scanning HOWTO
[https://help.ubuntu.com/community/ScanningHowTo#Client-side%20Setup](https://help.ubuntu.com/community/ScanningHowTo#Client-side%20Setup)

But Simple Scan and XSane still report that they find no scanning device.

---

### Post by zoubidoo on 2010-10-29
The printer/scanner shows the following ports open.  I read that saned usually runs on port 6566 which doesn't appear to be open, so I guess that's why the scanning applications aren't detecting a scanner.  Does anyone recognise any of these open ports as scanning related?

```
$ nmap 192.168.0.117

Starting Nmap 5.00 ( http://nmap.org ) at 2010-10-29 20:55 CEST
Interesting ports on 192.168.0.117:
Not shown: 992 closed ports
PORT      STATE SERVICE
80/tcp    open  http
139/tcp   open  netbios-ssn
515/tcp   open  printer
8290/tcp  open  unknown
8291/tcp  open  unknown
8292/tcp  open  unknown
9100/tcp  open  jetdirect
10002/tcp open  unknown

Nmap done: 1 IP address (1 host up) scanned in 13.53 seconds
```

---

### Post by zoubidoo on 2010-10-29
Here is the solution:
```
$ sudo hp-setup
```
Answer a few questions and it adds the printer and scanner.

This cost hours of effort because there's no FAQ for setting up network scanners :-(

---

### Post by zoubidoo on 2010-10-29
Updated the ScanningHowTo to make this easier in the future.
[https://help.ubuntu.com/community/ScanningHowTo](https://help.ubuntu.com/community/ScanningHowTo)

---

