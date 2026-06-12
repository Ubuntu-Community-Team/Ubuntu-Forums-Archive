---
title: "USB Scanner not detected by any programs"
date: 2010-09-13
forum: General Help
---

### Post by searchfgold6789 on 2010-09-13
I have an Epson perfection V100 Photo scanner. When I open any program, it will not detect the scanner. Simply plugging in the scanner and crossing fingers does not work.

[LIST]
[*]sane-find-scanner returns the following: ```
  # sane-find-scanner will now attempt to detect your scanner. If the
  # result is different from what you expected, first make sure your
  # scanner is powered up and properly connected to your computer.

  # No SCSI scanners found. If you expected something different, make sure that
  # you have loaded a kernel SCSI driver for your SCSI adapter.

found USB scanner (vendor=0x04b8 [EPSON], product=0x012d [EPSON Scanner]) at libusb:004:002
  # Your USB scanner was (probably) detected. It may or may not be supported by
  # SANE. Try scanimage -L and read the backend's manpage.

  # Not checking for parallel port scanners.

  # Most Scanners connected to the parallel port or other proprietary ports
  # can't be detected by this program.

```
[*]I entered in the informations as described on the Ubuntu Wiki into my /etc/sane.d/epson.conf file, still no luck.
[*]I tried installing the drivers and program from Avasys. Still no luck.
[*]I tried pressing all the buttons on the scanner wildly at random and cursing. Surprisingly enough that didn't get me anywhere either.
[/LIST]
Is there anyone here who has a fix, or has better googling skills than I do and could point me to a thread?
Thanks :)
 - search

---

### Post by drewsavini on 2010-09-13
maybe this thread will help?  the first section is for printers, below is scanners.
 
[http://ubuntuforums.org/showthread.php?t=590793&highlight=scanner+module](http://ubuntuforums.org/showthread.php?t=590793&highlight=scanner+module)

---

### Post by searchfgold6789 on 2010-09-14
I tried that thread but apparently that is for a different release of ubuntu :(

---

### Post by pbrane on 2010-09-14
It seems that you may need something called iscan.
[https://bbs.archlinux.org/viewtopic.php?id=67262]("https://bbs.archlinux.org/viewtopic.php?id=67262")

[http://push.cx/2007/epson-perfection-v100-in-ubuntu]("http://push.cx/2007/epson-perfection-v100-in-ubuntu")

---

### Post by searchfgold6789 on 2010-09-15
...I tried iscan....

---

### Post by philinux on 2010-09-15
> **searchfgold6789 said:**
> ...I tried iscan....

This got mine going. The steps may need modifying for your scanner.

[http://ubuntufs.wordpress.com/2006/05/26/epson-perfection-2480-scanner/](http://ubuntufs.wordpress.com/2006/05/26/epson-perfection-2480-scanner/)

---

### Post by searchfgold6789 on 2010-09-15
I got it to work...apparently they have just updated the drivers for iscan :)

---

