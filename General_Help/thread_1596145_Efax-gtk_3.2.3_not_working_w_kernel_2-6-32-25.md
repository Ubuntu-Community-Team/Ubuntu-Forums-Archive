---
title: "Efax-gtk 3.2.3 not working w/ kernel 2-6-32-25"
date: 2010-10-13
forum: General Help
---

### Post by A4Skyhawk on 2010-10-13
I have Ubuntu 10.04.1 LTS, and efax-gtk 3.2.3.  The fax program works fine w/ kernel 2.6.32-24, but not -25. 

With the latter, the response to "sudo modprobe agrserial" is
"FATAL: Module agrmodem not found.
FATAL: Module agrserial not found.
ln: creating symbolic link `/dev/ttySAGR': File exists
FATAL: Error running install command for agrserial"

Attempting to run Efax-gtk results in the following message:
"efax-0.9a: 21:57:37 Error: can't open serial port /dev/ttySAGR: No such file or directory
efax-0.9a: 21:57:37 failed page /(file name)
efax-0.9a: 21:57:37 finished - unrecoverable error"

Does anyone have a suggestion to debug/fix this?

TIA,
A4Skyhawk

---

### Post by A4Skyhawk on 2010-10-17
Resolved/fixed.  Did a complete removal of agrsm06pci-2.1.80_20100106_i386.deb and associated files, reinstalled the latest version, and efax-gtk 3.2.3 works fine.
A4Skyhawk

---

