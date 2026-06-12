---
title: "XSANE Scanner URI"
date: 2009-07-15
forum: General Help
---

### Post by john_navarro on 2009-07-15
I have a HP OfficeJet 9110 printer/scanner/fax device. It's a networked printer. Under Ubuntu 8.10 XSANE works just fine. It can see the scanner and can capture images. But with Ubuntu 9.04 XSANE can't detect the printer/scanner. After a lot of frustration I was able to get it working by copying the printer URI as defined in 8.10 into 9.04. I get to the printer URI via the printer properties.

Printer Name: HP-OfficeJet-9100

Driver: HP Officejet 9100 series PS v3010.107 Postscript (recommended)

Device URI:   
Ubuntu 8.10: hp:/net/Officejet_9100_series?ip=192.168.1.101 (works)
Ubuntu 9.04: socket://192.168.1.101:9100  (doesn't work)

I'm not sure how I can get the printer URI under Jaunty to read as it's defined under 8.10. Any ideas?

Just thought that I'd post this in case it helps someone else. Andperhaps 

John

---

### Post by CatKiller on 2009-07-16
> **john_navarro said:**
>  I'm not sure how I can get the printer URI under Jaunty to read as it's defined under 8.10. Any ideas?

I'm pretty sure that the hp:/ in the URI means that it's going through HPLIP on Intrepid and not on Jaunty. Perhaps that is where you should check your configuration?

---

