---
title: "Visioneer Strobe XP 200 problems"
date: 2011-11-04
forum: General Help
---

### Post by talkitivewizard on 2011-11-04
OS Ubuntu 11.10


Just a few days ago, my Visioneer Strobe XP 200 scanner was working just fine without a hitch. Today I tried to use Xsane and it gave me an error saying it couldn't find my scanner. After some time of fiddling with the cords, restarting, and what not, I tried to use the scanner in windows. That worked fine. 

So I come back to Ubuntu and start doing some searching. I find that lsusb shows it up.
```
Bus 006 Device 003: ID 04a7:0426 Visioneer Strobe XP 200
```

Ok, after some more searching I look at sane-find-scanner:
```
  # sane-find-scanner will now attempt to detect your scanner. If the
  # result is different from what you expected, first make sure your
  # scanner is powered up and properly connected to your computer.

  # No SCSI scanners found. If you expected something different, make sure that
  # you have loaded a kernel SCSI driver for your SCSI adapter.

found USB scanner (vendor=0x04a7, product=0x0426, chip=GL646_HP?) at libusb:006:003
  # Your USB scanner was (probably) detected. It may or may not be supported by
  # SANE. Try scanimage -L and read the backend's manpage.

  # Not checking for parallel port scanners.

  # Most Scanners connected to the parallel port or other proprietary ports
  # can't be detected by this program.

  # You may want to run this program as root to find all devices. Once you
  # found the scanner devices, be sure to adjust access permissions as
  # necessary.

```

I check on the compatibility list for sane and it says the following:
Strobe XP 200 USB 0x04a7/0x0426 [COLOR=#90B000]Good[/COLOR] All resolution and mode supported, calibration is available
So I know for a fact that the stupid thing is there... but if I do a scanimage -L I get the following:
```
No scanners were identified. If you were expecting something different,
check that the scanner is plugged in, turned on and detected by the
sane-find-scanner tool (if appropriate). Please read the documentation
which came with this software (README, FAQ, manpages).

```

Does anyone have any ideas on how to help me and/or point me in the right direction?

---

### Post by talkitivewizard on 2011-11-10
Well it seems that it's not just this single scanner. I just got a new Brother MFC-7340. It has the exact same problem even after installing the drivers and doing as the brother website says. 

I've confirmed that if I boot from a live cd of 11.10, the exact same thing happens.

However, I've also confirmed that if I boot from a live cd of 11.04, everything works for both scanners as it should. I hate to see this as a "solution" but it may be as close as I can get.

Any ideas?

---

### Post by n1v0la on 2011-12-04
Hello talkitivewizard.

I'm no expert in this, but maybe the problem is not directly SANE related?
Just thinking that it could be related to USB device names changing?

You could try the lsusb command on the working and on the non-working system.
The comparison might give a hint...

---

