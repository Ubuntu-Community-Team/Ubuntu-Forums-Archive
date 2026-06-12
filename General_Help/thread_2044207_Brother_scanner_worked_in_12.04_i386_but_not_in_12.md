---
title: "Brother scanner worked in 12.04 i386 but not in 12.04 amd64"
date: 2012-08-19
forum: General Help
---

### Post by Paulgirardin on 2012-08-19
I decided to try the 64 bit version of 12.04
I have gone through the driver install procedures that have worked for the 32 bit OS but can't seem to find the reason why Xsane and Simple scan don't see my scanner.
The scanner is a Brother MFC3220C.
sane-find-scanner seems to find the device:
```
paul@paul-P5K-SE:~$ sane-find-scanner

  # sane-find-scanner will now attempt to detect your scanner. If the
  # result is different from what you expected, first make sure your
  # scanner is powered up and properly connected to your computer.

  # No SCSI scanners found. If you expected something different, make sure that
  # you have loaded a kernel SCSI driver for your SCSI adapter.

found USB scanner (vendor=0x04f9, product=0x0146) at libusb:003:002
  # Your USB scanner was (probably) detected. It may or may not be supported by
  # SANE. Try scanimage -L and read the backend's manpage.

  # Not checking for parallel port scanners.

  # Most Scanners connected to the parallel port or other proprietary ports
  # can't be detected by this program.

  # You may want to run this program as root to find all devices. Once you
  # found the scanner devices, be sure to adjust access permissions as
  # necessary.

```

Scanimage -L doesn't detect the device:
```
paul@paul-P5K-SE:~$  scanimage -L

No scanners were identified. If you were expecting something different,
check that the scanner is plugged in, turned on and detected by the
sane-find-scanner tool (if appropriate). Please read the documentation
which came with this software (README, FAQ, manpages).

```

I've tried all the suggestions I could find including running the scan apps
as root and nothing works.
Any suggestions would be welcome.

---

### Post by Paulgirardin on 2012-08-19
I have solved this problem using this thread: 

[http://ubuntuforums.org/showthread.php?t=1594558](http://ubuntuforums.org/showthread.php?t=1594558)

---

