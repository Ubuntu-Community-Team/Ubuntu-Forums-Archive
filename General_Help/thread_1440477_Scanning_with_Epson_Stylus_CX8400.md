---
title: "Scanning with Epson Stylus CX8400"
date: 2010-03-27
forum: General Help
---

### Post by Muscovy on 2010-03-27
I have an Epson Stylus CX8400 printer/scanner that can print, but not scan.

XSane cannot find a sanner, and running a check in terminal shows
```

home@karmic-ubuntu:~$ sudo sane-find-scanner
[sudo] password for home: 

  # sane-find-scanner will now attempt to detect your scanner. If the
  # result is different from what you expected, first make sure your
  # scanner is powered up and properly connected to your computer.

  # No SCSI scanners found. If you expected something different, make sure that
  # you have loaded a kernel SCSI driver for your SCSI adapter.

found USB scanner (vendor=0x04b8, product=0x0839) at libusb:001:003
  # Your USB scanner was (probably) detected. It may or may not be supported by
  # SANE. Try scanimage -L and read the backend's manpage.

  # Not checking for parallel port scanners.

  # Most Scanners connected to the parallel port or other proprietary ports
  # can't be detected by this program.

```
Which although returns a device, seems to dead-end there.

I found a page multiple blogs/forums pointed to, filled out distro, version, etc, and was directed to the downloads at [http://www.avasys.jp/lx-bin2/linux_e/spc/DL2.do](http://www.avasys.jp/lx-bin2/linux_e/spc/DL2.do) wich contains a deb, and rpm, and sources. The deb throws the error of
```
Error: Dependency is not satisfiable: libltdl3 (>= 1.5.2-2)

```
which I am unable to solve.

I tried downloading the source, but ./configure is throwing the error of
```

checking for GDK_IMLIB... configure: error: Package requirements (imlibgdk) were not met:

No package 'imlibgdk' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables GDK_IMLIB_CFLAGS
and GDK_IMLIB_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.

```
which, again, is not a package I can find.

---

### Post by ellgor on 2010-03-28
Hi,

To get the libltdl3 for the deb package go to the Debian Packages (google will get you there) and look in Lenny packages, when the list shows up look for "Old-Libs" if its not in there try the next distro Sid or Squeeze, I think, until you find it.

Regards, Ellgor

---

### Post by H3LTerSK3LTer on 2010-09-15
Muscovy were you ever able to get that figured out? I'm having the same issue. I ran "sudo sane-find-scanner" in the terminal and it returned the exact same error message. XSane Image Scanner and  Simple Scan will find my printer. I'm trying to follow your conclusions but I have to say, I'm not an expert with Ubuntu yet.  If you could be a little more specific as to what to type in the terminal. 

cheers

---

### Post by mick222 on 2010-09-15
try here image scan works well for me [http://avasys.jp/eng/linux_driver/](http://avasys.jp/eng/linux_driver/)

---

### Post by Muscovy on 2010-11-13
It seems as of 10.10 it has drivers. Yay!

---

