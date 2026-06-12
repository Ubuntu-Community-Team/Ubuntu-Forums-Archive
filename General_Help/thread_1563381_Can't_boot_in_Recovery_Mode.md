---
title: "Can't boot in Recovery Mode"
date: 2010-08-29
forum: General Help
---

### Post by Cariboo1938 on 2010-08-29
Hello all:

I run Ubuntu 10.04 LTS-amd64 and I cannot boot Ubuntu with Linux 2.6.32-24-generic (recovery mode).

The Grub menu is:

GNU GRUB version 1.98-1ubuntu7
Ubuntu, with Linux 2.6.32-24-generic
Ubuntu, with Linux 2.6.32-24-generic (recovery mode)
Memory test (memtest86+)
Windows 7 (loader)

When I chose "Ubuntu, with Linux 2.6.32-24-generic (recovery mode)"
the screen turns black and stays black. All the other boot options work.
What is wrong?
Attached /bootgrub/grub.cfg

---

### Post by Cariboo1938 on 2010-09-01
Once in a while, specially when the computer was shut down unexpectedly through power failure, I want to use the recovery mode to 
- make free space
- repair broken packages
- run in failsafe graphic mode
- etc...

Because > All the other boot options work....
I wonder how I can keep this thread alive?
What other info would be needed to trace the issue?

---

### Post by Cariboo1938 on 2010-09-26
After the last system update to kernel 2.6.32-24-generic #43-Ubuntu I followed the instructions [HERE ]("https://help.ubuntu.com/community/GrubHowto") to update grub boot loader. Issue solved!

---

