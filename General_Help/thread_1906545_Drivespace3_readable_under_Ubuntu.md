---
title: "Drivespace3 readable under Ubuntu?"
date: 2012-01-09
forum: General Help
---

### Post by Gitanes on 2012-01-09
I'm trying to help some friends who have a couple of floppies compressed under Windows 98 using Drivespace3 who no longer have Windows 98.  Can this type of compression be read under Ubuntu and how would I go about doing it?

The only other options that I see are to find someone with a Windows 98 machine or find some Windows 98 installation disks and install them in a virtual machine.

Thanks.

---

### Post by andrewc on 2012-01-09
A Win98 VM might be the easiest way. There was a Linux driver for DriveSpace (dmsdos) but the most recent version I can locate is from around 2000 and doesn't work with modern  Linux kernels. There seems to be a version of it in NetBSD  (see [ftp://ftp.netbsd.org/pub/pkgsrc/current/pkgsrc/sysutils/dmsdos/README.html](ftp://ftp.netbsd.org/pub/pkgsrc/current/pkgsrc/sysutils/dmsdos/README.html) ), but IMHO it would be easier using a Win98 VM than trying to get NetBSD running (in or out of a VM)

---

