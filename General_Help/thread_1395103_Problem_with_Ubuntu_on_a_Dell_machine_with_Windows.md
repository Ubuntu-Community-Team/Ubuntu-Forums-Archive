---
title: "Problem with Ubuntu on a Dell machine with Windows 7 on it"
date: 2010-01-31
forum: General Help
---

### Post by TigrisAltaica on 2010-01-31
Hello. I managed to dual install both ubuntu 9.10 and windows 7 on a brand new dell laptop. Ubuntu worked well, as did windows, however once the machine was shut off from windows, it all went to hell. Upon turning the laptop on, I discovered that GRUB was gone, and that neither OS could be accessed. I've installed windows again but I need to know how to fix this before re-installing ubuntu. Thank you very much.

---

### Post by efflandt on 2010-01-31
Did you first use Win7 administration tools to shrink its Win7 partition, then install Ubuntu to its own partition(s), or did you use Wubi to install Ubuntu within Windows?

I had no issues with Win7 or 64-bit Ubuntu 9.10 installed on separate partitions, with standard Win mbr and grub installed on the Linux (primary) partition (with that flagged as boot partition).

Although, I had some issue when I was going to remove Ubuntu (to put it on USB hard drive instead).  I made the mistake of trying to use System > Administration > Disk Utility (instead of Gparted) to switch boot flag back to the Win7 partition instead of the Linux partition.  But after the Disk Utility was doing something unknown endlessly, I canceled that.  Then Win7 failed to boot (bootmgr missing).  So I used the Win7 disk to repair that (took a couple of trys, no need to reinstall), removed the Linux partition using Ubuntu booted from USB (grub2 properly installed on USB mbr), then used Win7 to expand its partition back to the rest of the drive.

---

### Post by TigrisAltaica on 2010-01-31
Yeah, both were on separate partitions.

---

