---
title: "Unable to install iScan on Kubuntu 9.10"
date: 2009-11-04
forum: General Help
---

### Post by MaquinaX on 2009-11-04
Hello Gang,

     Most of the time, I'll be reading, and finding solutions. But with a new distro, I guess it's not uncommon to post new issue. 

Ok, as alot of us, I was one of the many to upgrade to 9.10 Karmic Koala. I'm a professional IT, and need constant use of my printer and scanner, to upload reports and such. I'm using the Epson Workforce 500. The CUPS driver was able to detect and configure the printer with no problems. My scanner was not the same lucky case. In my last setup, I was using iScan, as it was the only software to support my Workforce 500 scanner. The issue is that there is still no current support for installing iScan to new 9.10 version. I went the extra mile in finding the deb packages for iScan and Lib3tdl3, but there appears to be conflict in installing each individually, as iScan requires lib3tdl3...., and when trying to install Lib3tdl3, it has a conflict with an exiting package. Can someone help me out in getting iScan installed, as it is the ONLY scan software the supports my scanner. Thanx to everyone in advanced...
Here is the exactly with the Error Messages display:

```


### Installing iScan deb ###

- Error: Dependency in not satisfiable: libltdl3 (>=1.5.2-2)

### Installing Lib3tdl3 deb ###

- Error: Breaks existing package 'libltdl-dev' conflicct: libltdl3-dev ()


```

---

### Post by MaquinaX on 2009-11-05
... Wait a minute everyone..., GREAT NEWS! Finally able to get the newer release of iScan (after endless searching). Installed newer .deb package, and then ran sane find scanner utility. Once scanner was detected, (of course, after installing iScan), I then rebooted system, and WAHLA!!! I have Karmic Koala running with working WorkForce 500 printer and scanner.
Good luck to everyone, and working together is how we move foward...

Newer iScan .deb

HTML Code:

[http://linux.avasys.jp/drivers/iscan/2.22.1/iscan_2.22.1-2.ltdl7_i386.deb](http://linux.avasys.jp/drivers/iscan/2.22.1/iscan_2.22.1-2.ltdl7_i386.deb)

Find Scanner Command
Code:

 sane-find-scanner | grep 0x04b8

:lolflag:

---

### Post by coogur on 2009-11-18
Same for me .. I was able to scan using my multi-function epson printer scanner model CX/DX7400(7450) in 9.04.  All I had to do was to run an 'lsusb' in order to extract the device id ie. 0838 and then modify the /etc/sane.d/epson.conf to input the device id, remove the'#' symbol in front of the last two lines to get xsane to work via USB.

With a clean 9.10 install .. nothing worked, I tried to apply the same correction with no success..  This is what I did to correct my scanning issue.

I downloaded the iscan_2.22.1-2 (_amd64) deb package and then encountered the same error message as previously mentionned that the libltdl3 dependency version was no greather than 1.5.2.  I found the 1.5.26 library on the debian repository site ie. libltdl3_1.5.26-4_amd64  - installed the package, re-ran the installation of iscan_2.22.1-2 and got a prompt - accepted and iscan works now.

Didn't get a chance to correct xsane yet.  Will post any corrections if I do get it working.

---

### Post by larsman1 on 2011-01-07
Epson RX580 all-in-one is working now.

Get the epson and iscan deb's from Avasys (mine is i386, they also have 64), get the lenny deb from Ubuntu- do a Google search for it to make it an easier search:
Printer:
1.      epson-inkjet-printer-escpr_1.0.1-1lsb3.2_i386.deb
Scanner:
1.  iscan-data_1.6.0-0_all.deb  (#3 won't install without this one)
2.  libltdl3_1.5.26-4+lenny1_i386.deb  (#3 won't install without this one)
3.  iscan_2.26.1-3_i386.deb

I have Linux Mint, but it's pretty much Ubuntu.

---

### Post by chaxastro on 2011-04-02
**Re: Unable to install iScan on Kubuntu 9.10**             
                                                                **Kubuntu 10.04. LTS YES IT WORKS! Thanks for this!:**

[I]'Finally able to get the newer release of  iScan (after endless searching). Installed newer .deb package, and then  ran sane find scanner utility. 
Newer iScan .deb'

[http://linux.avasys.jp/drivers/iscan...ltdl7_i386.deb]("http://linux.avasys.jp/drivers/iscan/2.22.1/iscan_2.22.1-2.ltdl7_i386.deb")[/I]  

Spent ages 'banging head against brick wall' on this one. Trying to get Kubuntu 10.04 Lucid recognise my Epson Stylus SX100. Printer side worked 'straight out of the box', but the scannner/copier was another matter. :confused:

However, downloaded newer deb package and away it went! 

I can now print/scan/copy! Tomorrow the world!!:KS

Time for a beer! Cheers!

Chaxastro
Toshiba Satellite Pro A120
Kubuntu 10.04LTS

---

### Post by synace on 2011-07-30
I posted full instructions on printer & scanner config for 11.04 Natty at: [http://ubuntuforums.org/showthread.php?p=11102817#post11102817](http://ubuntuforums.org/showthread.php?p=11102817#post11102817)

---

