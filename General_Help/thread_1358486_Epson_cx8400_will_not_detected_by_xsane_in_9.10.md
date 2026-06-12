---
title: "Epson cx8400 will not detected by xsane in 9.10"
date: 2009-12-18
forum: General Help
---

### Post by chosenbeans on 2009-12-18
I recently updated to Ubuntu 9.10 from 9.04. In 9.10 my epson cx8400 is not detected by xsane. Everything was working fine in 9.04. I think I have gotten printing to work by changing the drivers to cx7800 but I have no ink to test it. At least now it appears when attempting to print in firefox. However xsane still says there are no devices detected. I have installed the extra package for xsane with no luck. If anyone has successfully been able to get this device to scan in 9.10 please let me know. 


Thank you!

---

### Post by ghostcoil on 2009-12-31
I'm having the same problem - the printer prints fine, but xsane does not detect the scanner...
sane-find-scanner yields:
```

sol@sol-desktop:~$ sudo sane-find-scanner

  # sane-find-scanner will now attempt to detect your scanner. If the
  # result is different from what you expected, first make sure your
  # scanner is powered up and properly connected to your computer.

  # No SCSI scanners found. If you expected something different, make sure that
  # you have loaded a kernel SCSI driver for your SCSI adapter.

found USB scanner (vendor=0x04b8, product=0x0839) at libusb:001:002
  # Your USB scanner was (probably) detected. It may or may not be supported by
  # SANE. Try scanimage -L and read the backend's manpage.

  # Not checking for parallel port scanners.

  # Most Scanners connected to the parallel port or other proprietary ports
  # can't be detected by this program.

```and scanimage
```

sol@sol-desktop:~$ sudo scanimage -L
WARNING: Unhandled message: interface=org.freedesktop.DBus.Introspectable, path=/, member=Introspect

No scanners were identified. If you were expecting something different,
check that the scanner is plugged in, turned on and detected by the
sane-find-scanner tool (if appropriate). Please read the documentation
which came with this software (README, FAQ, manpages).

```

cheers!

---

### Post by ellgor on 2009-12-31
Hi,

I've got an Epson SX115 all-in-one, xsane doesn't recognise mine either, there is an app called Imagescan from the Avasys site, these are especially for Epsons' get the deb package and install it with gdebi, worked first time, after a reboot mind.

Regards, Ellgor.

---

### Post by brimurray on 2010-10-23
> **ellgor said:**
> Hi,

I've got an Epson SX115 all-in-one, xsane doesn't recognise mine either, there is an app called Imagescan from the Avasys site, these are especially for Epsons' get the deb package and install it with gdebi, worked first time, after a reboot mind.

Regards, Ellgor.

I just replaced an Epson Stylus CX3200 (from which I never had any problems with printing and scanner) with an Epson Stylus SX415.

Printing worked out of the box, however xsane or simple scan would not recognise the scanner.

The above Imagescan packages worked superbly!

Thank you for this tip, fantastic!

---

