---
title: "Ubuntu 9.04 crash after automatic update"
date: 2009-08-04
forum: General Help
---

### Post by schwaede on 2009-08-04
Hi!

Today I did an automatic update of my 9.04 OS. I can't remember all the items that there updated, but it were 80 files.
After rebooting the computer the progress bar went from left to right and beck for some time ending in a command screen telling me the following::confused:

"udevadm trigger is not permitted while udev is unconfigured" and further on

"Gave up waiting for root device"

So GRUB couldn't find my boot device.
I could not even start the recovery mode -> same problem.

Now my question: Can anybody tell me what to do to repair the OS?

Or, can anybody tell me how to uninstall the GRUB boot loader? Because I'm working on a dual-boot system with WIndows XPand I have no problem working without Ubuntu any more.

Thanks in advance

Jan

---

### Post by FIONEX on 2009-08-04
To bypass grub completely, get a windows startup disk or a boot cd with fdisk on it. If you dont know where to start, look for "ultimate boot cd".

Get to the DOS shell using the boot cd or startup disk.
then type this

fdisk /mbr

AND BAM, you're all good to go with just windows.  Grub will be erased from the MBR.

---

### Post by schwaede on 2009-08-04
Thank you for the help with GRUB! But this will be my last option.

But you have no idea how to solve the original problem itself?

---

