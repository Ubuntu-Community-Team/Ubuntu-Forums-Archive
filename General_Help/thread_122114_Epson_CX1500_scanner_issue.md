---
title: "Epson CX1500 scanner issue"
date: 2006-01-26
forum: General Help
---

### Post by evuraan on 2006-01-26
I've an Epson CX [1500]("http://evuraan.blogspot.com/2006/01/epson-stylus-cx1500-on-ubuntu-linux.html") (all in one), and it is in the list of supported(?) scanners per [this]("http://www.sane-project.org/lists/sane-backends-cvs.html") page. (Search for CX-1500 in that page, and you'll see..!!)

The documents says to run ```
sane-find-scanner
``` to begin with, and here's what I get when I do that:

```
# sane-find-scanner

<snip>

  # No SCSI scanners found. If you expected something different, make sure that
  # you have loaded a kernel SCSI driver for your SCSI adapter.
  # Also you need support for SCSI Generic (sg) in your operating system.
  # If using Linux, try "modprobe sg".

found USB scanner (vendor=0x04b8 [EPSON], product=0x080c [USB MFP]) at libusb:001:007
  # Your USB scanner was (probably) detected. It may or may not be supported by
  # SANE. Try scanimage -L and read the backend's manpage.

  # Not checking for parallel port scanners.

  # Most Scanners connected to the parallel port or other proprietary ports
  # can't be detected by this program.
```

It says: "found USB scanner (vendor=0x04b8 [EPSON], product=0x080c [USB MFP]) at libusb:001:007"

Now, per this, when I run " scanimage -L" this is what I get:

```
#  scanimage -L
device `v4l:/dev/video0' is a Noname WinTV PVR 150 virtual device
```

I've MythTV PVR, and that's the PVR 150 card coming in that list. 

I RTFM'd and STFW'd, and found that this slightly similar to [this]("http://www.linuxquestions.org/questions/showthread.php?t=401088") person's issue.

Any help  to have the usb scanner tamed and configured :confused:  will be much appreciated.

---

