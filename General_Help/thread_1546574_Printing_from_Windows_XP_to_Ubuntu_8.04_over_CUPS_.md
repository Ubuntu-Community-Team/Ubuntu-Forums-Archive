---
title: "Printing from Windows XP to Ubuntu 8.04 over CUPS or Samba"
date: 2010-08-05
forum: General Help
---

### Post by ChrisTek on 2010-08-05
Hi, I have my Dell 1320c installed via USB on my Ubuntu 8.04 machine. It uses a FX DocuPrint C525 A-AP v1.0 driver. I added it to my MacBook Pro via CUPS just fine, using the [http://192.168.1.110:631/printers/1320c](http://192.168.1.110:631/printers/1320c) path.

However, on my Windows XP machine, I tried adding it via IPP with that path and via Samba with this in the config:

```
   browsable = yes
   guest ok = yes
   use client drivers = yes
```

However, no matter which way I print from Windows I get a garbage file that looks like this:

```
-12345X@PJL COMMENT DATE=08/05/2010
@PJL COMMENT TIME=12:07:33
@PJL COMMENT DNAME=[comment]
JOB MODE=PRINTER
```

And on for about 3/4 of a page... Any idea what's going on? Like I said, OS X prints to it fine via CUPS, but Windows won't print correctly with CUPS or Samba.

---

### Post by davidmohammed on 2010-08-05
suggest install the XP equivalent printer driver.  Then configure the printer to find your Ubuntu printer via its IP address.

---

### Post by ChrisTek on 2010-08-05
> **davidmohammed said:**
> suggest install the XP equivalent printer driver.  Then configure the printer to find your Ubuntu printer via its IP address.

I tried using the Windows versions of both the 1320c driver and the FX DocuPrint driver, neither helped.

---

### Post by davidmohammed on 2010-08-05
presume you've followed the instructions [here]("https://help.ubuntu.com/community/NetworkPrintingFromWinXP")?

---

### Post by ChrisTek on 2010-08-05
> **davidmohammed said:**
> presume you've followed the instructions [here]("https://help.ubuntu.com/community/NetworkPrintingFromWinXP")?

Yes, that's exactly how I set up CUPS.

---

