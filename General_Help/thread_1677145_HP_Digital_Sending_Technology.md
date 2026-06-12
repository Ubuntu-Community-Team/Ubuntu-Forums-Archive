---
title: "HP Digital Sending Technology"
date: 2011-01-28
forum: General Help
---

### Post by lviggiani on 2011-01-28
Hi,
I've an HP LaserJet Professional m1212nf Multifunction Printer as a network printer/scanner.
I also have HPLIP software version 10.3.6 on Maverick 64bit.
The printer is correctly installed, the scanner is detected.
However when I try scanning with xsane or hp-scan, I get an error while connecting to the scanner.
```
$ hp-scan

HP Linux Imaging and Printing System (ver. 3.10.6)
Scan Utility ver. 2.2

Copyright (c) 2001-9 Hewlett-Packard Development Company, LP
This software comes with ABSOLUTELY NO WARRANTY.
This is free software, and you are welcome to distribute it
under certain conditions. See COPYING file for more details.

Using device: hpaio:/net/HP_LaserJet_Professional_M1212nf_MFP?zc=NPIACDA40

warning: No destinations specified. Adding 'file' destination by default.
warning: File destination enabled with no output file specified.
Setting output format to PNG for greyscale mode.
warning: Defaulting to '/home/lviggiani/hpscan001.png'.
Using device hpaio:/net/HP_LaserJet_Professional_M1212nf_MFP?zc=NPIACDA40
Opening connection to device...
error: SANE: Error during device I/O (code=9)

```

According to [this]("http://hplipopensource.com/hplip-web/models/laserjet/hp_laserjet_professional_m1212nf_mfp.html") page scanning should be supported ([http://hplipopensource.com/hplip-web/models/laserjet/hp_laserjet_professional_m1212nf_mfp.html](http://hplipopensource.com/hplip-web/models/laserjet/hp_laserjet_professional_m1212nf_mfp.html)).
However, I have the doubt that sane API is actually not supported, so I'm looking in how to use the HP Digital Sending Technology.
[This page]("http://hplipopensource.com/node/302") should be supposed to explain how to do that, but actually it says nothing ([http://hplipopensource.com/node/302](http://hplipopensource.com/node/302))... can someone help me please?
Thanks, Luca

---

