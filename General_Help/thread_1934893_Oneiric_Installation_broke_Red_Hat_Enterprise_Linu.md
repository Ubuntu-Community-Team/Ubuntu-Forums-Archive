---
title: "Oneiric Installation broke Red Hat Enterprise Linux"
date: 2012-03-03
forum: General Help
---

### Post by ceclauson on 2012-03-03
I started with a dual boot machine that had Windows Vista and Red Hat Enterprise Linux 4.6 (RHEL).  I used the installer to shrink the size of the Vista partition, and then installed Ubuntu, using the "install alongside existing operating systems" option in the installer.  The overall result is that Ubuntu and Vista work, but RHEL won't boot.

Specifically, when I try to load RHEL, I get the message “decompressing Linux OK... Loading Kernel”, and then the computer abruptly restarts.

I can, however, mount the RHEL filesystem and navigate it with no problems when I boot from Ubuntu.

To try to fix the problem, I created a bootable CD-ROM with GRUB Legacy, and ran the original grub.conf using the GRUB "configfile" command.  This brought up the original boot menu, and I could launch Vista from it, but when I tried to launch Red Hat, I got the error "Error 17 : Cannot mount selected partition".  To take it a step further, I even installed GRUB Legacy directly on the Red Hat partition, and had it chain loaded from the Ubuntu installation's GRUB, but I got the same message.

Red Hat worked with no problems before the installation, so I'm pretty stumped.  Thanks in advance for any help.

---

### Post by dcstar on 2012-03-03
> **ceclauson said:**
> I started with a dual boot machine that had Windows Vista and Red Hat Enterprise Linux 4.6 (RHEL).  I used the installer to shrink the size of the Vista partition, and then installed Ubuntu, using the "install alongside existing operating systems" option in the installer.  The overall result is that Ubuntu and Vista work, but RHEL won't boot.
.........
Red Hat worked with no problems before the installation, so I'm pretty stumped.  Thanks in advance for any help.

You have a RHEL problem, you **changed** the partition layout so that RHEL now obviously has a problem with it and cannot boot.

Best to go to a RHEL forum and try and get an answer there.

---

### Post by ceclauson on 2012-03-03
Thanks for the advice.  I've posted on a Red Hat forum as well.

However, is there any way you can provide more detail?  Basically, the way I was originally looking at it, the Red Hat partition was never modified during the process at all so it should boot, however it is true that the Ubuntu partitions were inserted *before* the Red Hat partition, so the order of the Red Hat partition on the disk as viewed from the start did change (even though the device as identified both by GRUB and in /dev/ is still the same).

So I guess what I'm wondering is, do you or anyone else know of any mechanism by which a linux kernel would care about what partition (in terms of absolute order on disk) it came from?  I realize I might be reaching here, but I can still access the Red Hat partition's file system, so maybe there's a file I could edit or something.

Thanks again for the previous post, and in advance for future help.

---

