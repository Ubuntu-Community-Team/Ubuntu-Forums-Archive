---
title: "HP Laserjet 6P won't print from Lucid Lynx"
date: 2011-11-25
forum: General Help
---

### Post by margie2 on 2011-11-25
I just did a fresh install of Ubuntu 10.04 Lucid Lynx and I'm having trouble getting my old HP Laserjet 6P to work on the parallel port. The printer works fine under Windows XP. Ubuntu seems to see the printer okay. lpstat -p -d shows it's there and ready. But every job I send to it doesn't print. No error messages either. It appears that it thinks every job I sent to it was completed when it really just vanished into the ether.

FWIW, this printer worked fine from every Linux client on my local network via CUPS when it was connected to the parallel port on the Win XP machine. But I can't get it to even print from the command line with this new install of Ubuntu.

Help! Please!

Margie J.

---

### Post by dcstar on 2011-11-26
> **margie2 said:**
> I just did a fresh install of Ubuntu 10.04 Lucid Lynx and I'm having trouble getting my old HP Laserjet 6P to work on the parallel port. The printer works fine under Windows XP. Ubuntu seems to see the printer okay. lpstat -p -d shows it's there and ready. But every job I send to it doesn't print. No error messages either. It appears that it thinks every job I sent to it was completed when it really just vanished into the ether.

FWIW, this printer worked fine from every Linux client on my local network via CUPS when it was connected to the parallel port on the Win XP machine. But I can't get it to even print from the command line with this new install of Ubuntu.

Help! Please!

Margie J.

Check the BIOS Parallel Port settings and experiment with the options to see if things change, or change the Linux printer driver you are using.

---

### Post by margie2 on 2011-11-26
I have tried every printer driver available and I have also tried all the various parallel port settings. CUPS sees the printer settings and status accurately so I don't think the parallel port is the problem.

---

### Post by margie2 on 2011-11-26
Problem solved thanks to resources at:

[http://hplipopensource.com/hplip-web/install/index.html](http://hplipopensource.com/hplip-web/install/index.html)
[http://www.openprinting.org/printer/HP/HP-Laserjet_6P](http://www.openprinting.org/printer/HP/HP-Laserjet_6P)

The basic problem seemed to be that I needed to install the latest HPLIP software

hplip-3.11.10

and then set it all up again with CUPS (hpcups 3.11.10) on LPT1

---

