---
title: "xsane no devices available"
date: 2009-11-11
forum: General Help
---

### Post by retiredU on 2009-11-11
When I try scanning a document I get a message from xsane "no devices available"

When I run sane-find-scanner:
> 
  # sane-find-scanner will now attempt to detect your scanner. If the
  # result is different from what you expected, first make sure your
  # scanner is powered up and properly connected to your computer.

  # No SCSI scanners found. If you expected something different, make sure that
  # you have loaded a kernel SCSI driver for your SCSI adapter.

found USB scanner (vendor=0x04e8, product=0x3419) at libusb:003:003
  # Your USB scanner was (probably) detected. It may or may not be supported by
  # SANE. Try scanimage -L and read the backend's manpage.

  # Not checking for parallel port scanners.

  # Most Scanners connected to the parallel port or other proprietary ports
  # can't be detected by this program.

  # You may want to run this program as root to find all devices. Once you
  # found the scanner devices, be sure to adjust access permissions as
  # necessary.
When I run scanimage -L:

> 
WARNING: Unhandled message: interface=org.freedesktop.DBus.Introspectable, path=/, member=Introspect

No scanners were identified. If you were expecting something different,
check that the scanner is plugged in, turned on and detected by the
sane-find-scanner tool (if appropriate). Please read the documentation
which came with this software (README, FAQ, manpages).
I am running ubuntu 9.10 on a laptop. I also tried using different USB ports to connect to my printer. I've restarted both the laptop and the printer. Printing test pages from the printer works fine. I dont know if this helps but the last time I tried scanning (Oct 20th, prior to upgrade from ubuntu 9.01 to 9.10), scanning worked to the best of my recollection. I did a cursory search through the forums already. I have little ubuntu experience so please be kind :)

---

### Post by ub12 on 2009-11-12
I am having the same problem. I have a dual boot Ubuntu 8.04 and 9.10. I can scan without a problem using 8.04. When I run Xsane in 9.10 I get an error "no devices available. 
hp-probe provides the following:
Using connection type: net


--------------------
| DEVICE DISCOVERY |
--------------------

Probing network for printers. Please wait, this will take approx. 10 seconds...

  Device URI                                  Model                   Name    
  ------------------------------------------  ----------------------  --------
  hp:/net/Photosmart_3300_series?ip=10.0.0.6  Photosmart_3300_series  HP51A346

Found 1 printer(s) on the 'net' bus.


Done.

hp-info returns an error:
error:  No devices found. 

scanimage -l returned an error:
WARNING: Unhandled message: interface=org.freedesktop.DBus.Introspectable, path=/, member=Introspect
scanimage: no SANE devices found

I have installed the drivers recommended by HP (hplip) but still no good.
Check permissions but I cannot see scanners in the list.

---

### Post by ub12 on 2009-11-16
Hey, retiredU,
found the solution to my problem using this thread. I hope it works for you.

[http://ubuntuforums.org/showthread.php?p=8326899#post8326899](http://ubuntuforums.org/showthread.php?p=8326899#post8326899)

Cheers

---

