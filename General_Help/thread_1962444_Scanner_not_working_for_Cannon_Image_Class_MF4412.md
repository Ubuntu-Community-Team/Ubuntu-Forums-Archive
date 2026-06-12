---
title: "Scanner not working for Cannon Image Class MF4412"
date: 2012-04-21
forum: General Help
---

### Post by Nath A on 2012-04-21
Hello, I recently switched from windows vista to ubuntu 11.10.
I realized that my printer/Scanner/photocopier was not working.I went on [www.**canon](www.**canon)**-**asia**.com and downloaded the driver for the printer.Now the printer is working fine.But the site doesnt have a driver for the scanner for linux and Xsane is not detecting my scanner:confused: . I tried running the windows and mac version of the driver through wine and acetoneiso but to no avail.
Please help me out . I really need my scanner to work 

Thanks

---

### Post by davidvandoren on 2012-04-21
Try vuescan!
You can try it out for free but the full version will cost you.

[http://www.hamrick.com/#download](http://www.hamrick.com/#download)

---

### Post by Nath A on 2012-04-21
> **davidvandoren said:**
> Try vuescan!
You can try it out for free but the full version will cost you.

[http://www.hamrick.com/#download](http://www.hamrick.com/#download)
Hey,
thanks for the quick reply. I downloaded vuescan like you said .When i try to scan ,this is what i get :-
No scanners were found connected to your computer, and no raw scan files were found.

---

### Post by Nath A on 2012-04-21
I typed ```
sudo sane-find-scanner
``` in the terminal ..this is what i got :-

```
# sane-find-scanner will now attempt to detect your scanner. If the
  # result is different from what you expected, first make sure your
  # scanner is powered up and properly connected to your computer.

  # No SCSI scanners found. If you expected something different, make sure that
  # you have loaded a kernel SCSI driver for your SCSI adapter.

found USB scanner (vendor=0x04a9 [Canon Inc], product=0x2737 [MF4410]) at libusb:001:004
  # Your USB scanner was (probably) detected. It may or may not be supported by
  # SANE. Try scanimage -L and read the backend's manpage.

  # Not checking for parallel port scanners.

  # Most Scanners connected to the parallel port or other proprietary ports
  # can't be detected by this program.
```

Well, the scanner is being detected by ubuntu. Its just not working.I dont know what to make of this :confused:

---

### Post by Nath A on 2012-04-21
Finally I got my scanner to work . :) .Just followed on the instructions on [**Canon MF4350d - Printer Scanner setup    **]("http://ubuntuforums.org/showthread.php?t=1427330")thread
 
[]("http://ubuntuforums.org/showthread.php?t=1427330")

---

