---
title: "Install stops with reference to usbcore"
date: 2006-06-06
forum: General Help
---

### Post by rockylab on 2006-06-06
All,

I have read other threads to see if there is a solution for my install issues but have not found one yet.  I am hoping someone can assist.  The computer is an Acer Veritron 7700G that Ubuntu 5.10 installs on and updates with no problems.  I have tried installing from the Ubuntu and Kubuntu Dapper CDs with the following result.

After the following lines during mounting root file system the install stops.

usbcore: registered new driver usbhid
drivers/usb/input/hid-core.c: v2.6:USB HID core driver
ata2: BUG: timeout without command

I have tried various BIOS settings and tried switching out hardware (ie mouse, keyboard, harddrive, cdrom drive) with no success.

Thanks for your assistance in advance.

---

### Post by rockylab on 2006-06-08
Is there anyone with any ideas.  I really want to keep using Ubuntu but I cannot get it loaded.  Maybe there is something I can use as a boot option that would work. ](*,)

---

### Post by thingy on 2006-06-08
That error message indicates a sata_nv driver issue. It's a bug most probably.

You can help the kernel devs track down the commit(s) which introduced the problem, by trying various kernel versions to locate the kernel the problem first showed up in.

I know that you prob. can't do this if you can't install dapper, but I believe you will be able to install an older distro with an older kernel fine if this is a recently introduced bug.

jin

---

### Post by rockylab on 2006-06-08
Thank you for your assistance jin,

All 5.10 works fine.  This includes all updates.  Matter of fact I am using the machine I am having problems with right now with 5.10 re-installed from scratch and everything works perfect.  I would love to help figure out where the problem is but so far all my attempts at changing out hardware and various boot options have all failed.

rocky

---

### Post by thingy on 2006-06-08
[QUOTE=rockylab]Thank you for your assistance jin,

All 5.10 works fine.  This includes all updates.  Matter of fact I am using the machine I am having problems with right now with 5.10 re-installed from scratch and everything works perfect.  I would love to help figure out where the problem is but so far all my attempts at changing out hardware and various boot options have all failed.

rocky[/QUOTE]

I don't think your hardware is faulty.

I think that some recent updates to the sata_nv driver in the kernel has resulted in a bug being introduced.

If you want to get the bug fixed, file a kernel bug report.

See this on how to do that:

[http://www.kernel.org/pub/linux/docs/lkml/reporting-bugs.html](http://www.kernel.org/pub/linux/docs/lkml/reporting-bugs.html)

---

### Post by rockylab on 2006-06-08
Thanks for the info.  I will do that now.

---

