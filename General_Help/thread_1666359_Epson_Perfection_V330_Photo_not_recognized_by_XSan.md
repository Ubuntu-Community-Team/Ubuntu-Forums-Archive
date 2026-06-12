---
title: "Epson Perfection V330 Photo not recognized by XSane and Simple Scan"
date: 2011-01-13
forum: General Help
---

### Post by sanderj on 2011-01-13
I just got an Epson Perfection V330 Photo scanner.
After connecting it to Ubuntu 10.04, it's not recognized by XSane and Simple Scan.

The relevant lsusb output:

Bus 001 Device 008: ID 04b8:0142 Seiko Epson Corp.


Google does not yet know "04b8:0142", so I'm posting this to 'create a record', and to get a solution.

---

### Post by sanderj on 2011-01-13
```
sander@quirinius:~$ sane-find-scanner

  # sane-find-scanner will now attempt to detect your scanner. If the
  # result is different from what you expected, first make sure your
  # scanner is powered up and properly connected to your computer.

  # No SCSI scanners found. If you expected something different, make sure that
  # you have loaded a kernel SCSI driver for your SCSI adapter.

found USB scanner (vendor=0x04b8, product=0x0142) at libusb:001:008
  # Your USB scanner was (probably) detected. It may or may not be supported by
  # SANE. Try scanimage -L and read the backend's manpage.

  # Not checking for parallel port scanners.

  # Most Scanners connected to the parallel port or other proprietary ports
  # can't be detected by this program.

  # You may want to run this program as root to find all devices. Once you
  # found the scanner devices, be sure to adjust access permissions as
  # necessary.


sander@quirinius:~$ scanimage -L

No scanners were identified. If you were expecting something different,
check that the scanner is plugged in, turned on and detected by the
sane-find-scanner tool (if appropriate). Please read the documentation
which came with this software (README, FAQ, manpages).
sander@quirinius:~$
```

---

### Post by davidmohammed on 2011-01-13
drivers for your scanner found [here]("http://www.avasys.jp/lx-bin2/linux_e/scan/DL1.do").  Search for your model - fill in the questionnaire.  Look at the installation manual - you will need to download the "deb" files and install as per the installation manual.

---

### Post by sanderj on 2011-01-13
> **davidmohammed said:**
> drivers for your scanner found [here]("http://www.avasys.jp/lx-bin2/linux_e/scan/DL1.do").  Search for your model - fill in the questionnaire.  Look at the installation manual - you will need to download the "deb" files and install as per the installation manual.

Man ... you're fast! And good! I did what you advised, and downloaded and installed three .deb's:


> Download for Perfection V330 Photo data package
deb package	
iscan-data_1.6.0-0_all.deb


Download for Perfection V330 Photo core package
deb 32bit package [libltdl7] (for Ubuntu 8.10 or later)	
iscan_2.26.1-3.ltdl7_i386.deb	 
esci-interpreter-perfection-v330_0.0.1-1_i386.deb

I now get:

```
sander@quirinius:~$ scanimage -L
device `epkowa:interpreter:001:009' is a Epson Perfection V330 Photo flatbed scanner
sander@quirinius:~$ 
```

And now Simple Scan (1.0.3) just scans from the Epson! It works.

Great. Thank you!


Sander

---

### Post by sanderj on 2011-06-29
I'm trying the same trick on Ubuntu 11.04 64-bit, but so far no success.

I've installed:

-rw-r--r-- 1 sander sander   156780 2011-06-29 17:15 esci-interpreter-perfection-v330_0.1.1-2_amd64.deb
-rw-r--r-- 1 sander sander   369788 2011-06-29 17:15 iscan_2.26.4-2.ltdl7_amd64.deb
-rw-r--r-- 1 sander sander    25166 2011-06-29 17:14 iscan-data_1.9.0-1_all.deb

and Software Centers confirms they are installed, scanimage says:


```
sander@R540:~$ scanimage -L
device `epkowa:interpreter:002:011' is a Epson (unknown model) flatbed scanner
sander@R540:~$ 

```

and/but Simple Scan says "Unable to connect to scanner".

I'll now reboot to see if that helps...

---

### Post by sanderj on 2011-06-29
> **sanderj said:**
> 

<snip>

and/but Simple Scan says "Unable to connect to scanner".

I'll now reboot to see if that helps...

The good news: after the reboot Simple Scan can successfully scan from the scanner.
The bad news: after the reboot Simple Scan can successfully scan from the scanner.

But seriously: it works, but since when does Linux need reboots for a simple driver? :(


@davidmohammed Do you know if the license of these drivers/software allows it to be included in the Ubuntu repository? If so, would Ubuntu then be able to install the drivers automagically?

---

### Post by Peter Ratcliffe on 2012-02-04
Thanks Sanderj.  Followed your advise and got my Epson v330 scanner to work.  Brilliant

Peter Ratcliffe

---

