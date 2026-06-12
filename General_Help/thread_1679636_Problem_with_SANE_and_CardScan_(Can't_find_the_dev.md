---
title: "Problem with SANE and CardScan (Can't find the device)"
date: 2011-02-01
forum: General Help
---

### Post by TiuTalk on 2011-02-01
I have a CardScan 60 II device and compiled [SANE]("http://www.sane-project.org/") in my Ubuntu 10.10 laptop.

The problem is I can't make SANE find the CardScan.

> $ sudo sane-find-scanner 

  # sane-find-scanner will now attempt to detect your scanner. If the
  # result is different from what you expected, first make sure your
  # scanner is powered up and properly connected to your computer.

  # No SCSI scanners found. If you expected something different, make sure that
  # you have loaded a kernel SCSI driver for your SCSI adapter.

  # No USB scanners found. If you expected something different, make sure that
  # you have loaded a kernel driver for your USB host controller and have setup
  # the USB system correctly. See man sane-usb for details.
  # SANE has been built without libusb support. This may be a reason
  # for not detecting USB scanners. Read README for more details.

  # Not checking for parallel port scanners.

  # Most Scanners connected to the parallel port or other proprietary ports
  # can't be detected by this program.> $ lsusb

Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 002: ID 08f0:1000 Corex Technologies 
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 0a5c:2150 Broadcom Corp. BCM2046 Bluetooth Device
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 003: ID 064e:a127 Suyin Corp. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hubAs you can see, the device is connected and detected by lsusb: "**Bus 006 Device 002: ID 08f0:1000 Corex Technologie**"

---

### Post by greg-t on 2011-09-10
Did you ever have any success with this?  I am looking to get off my XP box, but I really want to be able to use this scanner on Ubuntu.

Any update would be appreciated.

Thanks,
Greg

---

