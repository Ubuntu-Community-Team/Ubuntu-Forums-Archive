---
title: "scanner not detected"
date: 2011-10-01
forum: General Help
---

### Post by arcturus.red on 2011-10-01
Using Ubuntu 11.04 (Natty). Scanner was working fine until about half an hour ago, and suddenly....

"**Failed to scan. **No scanners available. Please connect a scanner."
"**No scanners detected. **Please check that your scanner is connected and powered on."

Running ```
sudo sane-find-scanner
``` yields

```
  # sane-find-scanner will now attempt to detect your scanner. If the
  # result is different from what you expected, first make sure your
  # scanner is powered up and properly connected to your computer.

  # No SCSI scanners found. If you expected something different, make sure that
  # you have loaded a kernel SCSI driver for your SCSI adapter.

found USB scanner (vendor=0x04e8 [Samsung Electronics Co., Ltd.], product=0x3441 [SCX-3200 Series]) at libusb:001:006
  # Your USB scanner was (probably) detected. It may or may not be supported by
  # SANE. Try scanimage -L and read the backend's manpage.

  # Not checking for parallel port scanners.

  # Most Scanners connected to the parallel port or other proprietary ports
  # can't be detected by this program.

```And then running ```
sudo scanimage -L
``` produces
```
No scanners were identified. If you were expecting something different,
check that the scanner is plugged in, turned on and detected by the
sane-find-scanner tool (if appropriate). Please read the documentation
which came with this software (README, FAQ, manpages).

```Can someone PLEASE explain what to do next, in simple terms that a newbie can understand?

Also, it would be nice if a new user could go five minutes in Ubuntu without encountering yet another major bug. Just sayin'.

---

### Post by WasMeHere on 2011-10-01
I can help you get this thread active, but I am no expert on scanners. I have lucid (ubuntu 10.04 LTS) where my usb scanner can be reached via Simple Scan and Xsane Image Scanner out-of-the-box. I remember that my daughter scans from her computer using remote login (ssh) to mine, and then only one of the scanning programs works.

My general advice is to *restart both the scanner and the computer*. If that does not help, you need *help from someone with experience* how to fix scanner problems.

---

### Post by arcturus.red on 2011-10-01
My scanner started working again, as suddenly as it'd stopped. :confused: 
I'd already tried to restart the scanner and the PC, but that didn't work.
I have no idea what actually fixed it, just as I have no idea what actually caused the error in the first place. 

Anyhow, at least it's working now. Thanks for your time. :)

---

