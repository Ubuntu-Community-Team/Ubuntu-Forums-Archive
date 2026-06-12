---
title: "Epson Stylus NX110 can print but not scan"
date: 2010-02-20
forum: General Help
---

### Post by 240r on 2010-02-20
Using Kubuntu 9.04. I just installed the Epson Stylus NX110 and got it to print but when I tried scanning, it did nothing. Xsane says no devices are available. 

```
sudo sane-find-scanner
found USB scanner (vendor=0x04b8 [SEIKO EPSON], product=0x084d [USB MFP]) at libusb:002:004
  # Your USB scanner was (probably) detected. It may or may not be supported by
  # SANE. Try scanimage -L and read the backend's manpage.

scanimage -L

No scanners were identified. If you were expecting something different,
check that the scanner is plugged in, turned on and detected by the
sane-find-scanner tool (if appropriate). Please read the documentation
which came with this software (README, FAQ, manpages). 
```

I also tried doing sudo xsane but still no device found.

I found [http://ubuntuforums.org/showthread.php?t=1357523&highlight=epson+stylus+nx110](http://ubuntuforums.org/showthread.php?t=1357523&highlight=epson+stylus+nx110) but wasn't sure if my problem is related enough and was afraid to hijack it.

Please help.

---

### Post by ellgor on 2010-02-21
Hi,

Go to the "Avasys" site and get a package called Imagescan, there are a lot of packages there so look carefully for a "deb" package called Imagescan (its way down the download page), I say deb package because once downloaded you can use gdebi to install it automatically,it works after a reboot.

Regards, Ellgor.

---

### Post by 240r on 2010-02-22
Thank you for the reply. I have never tried installing a deb file. How do I use a gdebi? Do I have to install that first?

---

### Post by spcwingo on 2010-02-22
> **240r said:**
> Thank you for the reply. I have never tried installing a deb file. How do I use a gdebi? Do I have to install that first?

Gdebi is installed by default.  All you have to do is double-click the downloaded deb and it will be opened with gdebi.  After that just follow the on-screen instructions.

---

### Post by 240r on 2010-02-23
Oh ok. Will try that when I get a chance. Thank you.

---

### Post by 240r on 2010-03-11
Got it to work. Thank you both so much for the help!

---

### Post by geovino on 2010-07-03
> **ellgor said:**
> Hi,

Go to the "Avasys" site and get a package called Imagescan, there are a lot of packages there so look carefully for a "deb" package called Imagescan (its way down the download page), I say deb package because once downloaded you can use gdebi to install it automatically,it works after a reboot.

Regards, Ellgor.

where is the file on the scanner page? I can't find it.

---

