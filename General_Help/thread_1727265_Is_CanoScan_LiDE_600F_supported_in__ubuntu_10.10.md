---
title: "Is CanoScan LiDE 600F supported in  ubuntu 10.10?"
date: 2011-04-12
forum: General Help
---

### Post by dragonfly41 on 2011-04-12
Is the Canon scanner .. CanoScan LiDE 600F .. supported in ubuntu 10.10?

This scanner works in Vista.

In ubuntu I ran ..

```
[B]
sudo sane-find-scanner[/B]

  # sane-find-scanner will now attempt to detect your scanner. If the
  # result is different from what you expected, first make sure your
  # scanner is powered up and properly connected to your computer.

  # No SCSI scanners found. If you expected something different, make sure that
  # you have loaded a kernel SCSI driver for your SCSI adapter.

found USB scanner (vendor=0x04a9 [Canon], product=0x2224 [CanoScan]) at libusb:002:003
  # Your USB scanner was (probably) detected. It may or may not be supported by
  # SANE. Try scanimage -L and read the backend's manpage.

  # Not checking for parallel port scanners.

  # Most Scanners connected to the parallel port or other proprietary ports
  # can't be detected by this program.

==================================================================


**sudo scanimage -L**

No scanners were identified. If you were expecting something different,
check that the scanner is plugged in, turned on and detected by the
sane-find-scanner tool (if appropriate). Please read the documentation
which came with this software (README, FAQ, manpages).


```


Then I searched through this ..

Desktop Hardware Incompatibility List

[http://ubuntuforums.org/showthread.php?t=361237&highlight=CanoScan+LiDE+600F](http://ubuntuforums.org/showthread.php?t=361237&highlight=CanoScan+LiDE+600F)


> 

Re: Desktop Hardware Incompatibility List.

Sept 7th 2008

1) Scanner
2) Canon
3) CanoScan LiDE 600F
4) Not detected & not supported in Ubuntu 8.04. Can be driven by a Windows guest OS in VirtualBox 1.6.6 



It doesn't look hopeful.

---

### Post by Matt__ on 2011-04-12
its totally unsupported sorry, look here

[http://www.sane-project.org/sane-mfgs.html#Z-CANON](http://www.sane-project.org/sane-mfgs.html#Z-CANON)

but look here for possibly partial use.

[http://www.juergen-ernst.de/info_sane.html](http://www.juergen-ernst.de/info_sane.html)


#problem is down to canon not releasing driver documentation.

---

### Post by dragonfly41 on 2011-04-12
Thank you for that info Matt__

---

