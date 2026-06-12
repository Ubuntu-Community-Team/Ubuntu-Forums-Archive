---
title: "HP4570C on 32-bit Ubuntu 12.04LTS SANE can't find"
date: 2012-07-14
forum: General Help
---

### Post by mcdugal2 on 2012-07-14
Don't know if this is the correct place for this post or not... I've got an HP Scanjet 4570c that SANE says is supported. it shows up under lsusb and its mentioned when running sane-find-scanner, however scanimage -L shows no scanner detected...
outputs are as follows...

lsusb
```

philip@philip-GA-78LMT-S2P:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 03f0:1305 Hewlett-Packard ScanJet 4570c
Bus 003 Device 002: ID 413c:2003 Dell Computer Corp. Keyboard
Bus 002 Device 002: ID 054c:01bd Sony Corp. MRW62E Multi-Card Reader/Writer
Bus 006 Device 002: ID 046d:c00c Logitech, Inc. Optical Wheel Mouse
```sane-find-scanner
```
philip@philip-GA-78LMT-S2P:~$ sane-find-scanner

  # sane-find-scanner will now attempt to detect your scanner. If the
  # result is different from what you expected, first make sure your
  # scanner is powered up and properly connected to your computer.

  # No SCSI scanners found. If you expected something different, make sure that
  # you have loaded a kernel SCSI driver for your SCSI adapter.

found USB scanner (vendor=0x03f0 [Hewlett-Packard], product=0x1305 [hp scanjet scanner], chip=GL842?) at libusb:001:003
  # Your USB scanner was (probably) detected. It may or may not be supported by
  # SANE. Try scanimage -L and read the backend's manpage.

  # Not checking for parallel port scanners.

  # Most Scanners connected to the parallel port or other proprietary ports
  # can't be detected by this program.

  # You may want to run this program as root to find all devices. Once you
  # found the scanner devices, be sure to adjust access permissions as
  # necessary.
```scanimage -L
```
philip@philip-GA-78LMT-S2P:~$ scanimage -L

No scanners were identified. If you were expecting something different,
check that the scanner is plugged in, turned on and detected by the
sane-find-scanner tool (if appropriate). Please read the documentation
which came with this software (README, FAQ, manpages).
```I found a bug report for another distribution that maybe relevant to my problem (_[COLOR=Blue][here]("https://bugzilla.redhat.com/show_bug.cgi?id=723696")[/COLOR]_).  I do not know if this is the same issue that is happening with my setup or not. I would appreciate any information on how to get this scanner working on this system...

---

