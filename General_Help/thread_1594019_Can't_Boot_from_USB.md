---
title: "Can't Boot from USB"
date: 2010-10-11
forum: General Help
---

### Post by Hman242 on 2010-10-11
I've used UNetbootin to make a bootable USB of the new 10.10 Ubuntu Netbook Edition. Open trying to boot from it and passing the UNetbootin menu I get the error that "init" wasn't found. What is the problem here?

Just in case, I checked the .iso with MD5SUM and it all checks out.

---

### Post by spikoley on 2010-10-13
This is a known issue.  Use Startup Disk Creator instead.  It also has an issue, but it can be fixed with editing a file.

[http://ubuntuforums.org/showthread.php?t=1592204](http://ubuntuforums.org/showthread.php?t=1592204)

> Using GParted to Format a USB Stick »
Fixing USB Install Issues with Ubuntu 10.10 Maverick Meerkat
Published on October 7, 2010 in Ubuntu. 2 Comments Tags: bootlogo, fix, gfxboot, maverick meerkat, ubuntu, ui, unknown keyword in configuration file.

This morning, I attempted to install Ubuntu 10.10 Maverick Meerkat from a USB drive but received an error message to my disdain. After using the USB Startup Disk Creator to create a bootable USB installer, I rebooted only to be confronted with the following fatal error message: “Unknown keyword in configuration file”. Here’s a fix for it (thanks to JackNocturne):

NOTE: This has only been tested and reported as working on the 32-bit version of Ubuntu 10.10. Compatibility issues have been reported with the 64-bit version.

1. Using the USB Startup Disk Creator, make a bootable USB disk with the latest Ubuntu 10.10 .ISO.
2. Once the process is complete, browse to the root directory of the USB disk, click on the /syslinux folder, and open the file entitled syslinux.cfg.
3. Using a text/code editor, find the line:
ui gfxboot bootlogo
4. Change it to:
gfxboot bootlogo
5. Save the file and reboot to test — it should work now.

---

