---
title: "Ubuntu Installer on USB fails to boot"
date: 2010-12-22
forum: General Help
---

### Post by natbob1 on 2010-12-22
On a Toshiba Satellite m35x-s149 laptop an Ubuntu installer on USB will not boot.  The USB drive is detected as a hard drive in the BIOS.  In addition, a "[USB Boot Tester]("http://www.pendrivelinux.com/testing-your-system-for-usb-boot-compatibility/")" designed to test whether a computer can boot from USB will not boot either; the tester boots successfully on a different computer.  A live CD successfully boots from the CD Drive.

Thanks,
natbob1

---

### Post by C.S.Cameron on 2010-12-23
Try the usb drive on another computer.
If it works you could try a bootloader such as **plop** as a last resort.

---

### Post by efflandt on 2010-12-23
Sometimes even if you put USB before hard drive in the boot order in CMOS setup, you still might need to press a key during the BIOS splash screen to boot from USB (maybe F12, but look at the BIOS splash screen when you boot).

But it might also depend how you installed the iso to USB. Older versions of programs to create USB boot iso's might not know about the different syslinux in 10.10.

---

### Post by sikander3786 on 2010-12-23
In addition to above posts, it would be worth to check the Ubuntu ISO image for defects. If that is corrupted somehow, the boot process might fail eventually.

[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

If ok, try using Unetbootin.

[http://unetbootin.sourceforge.net](http://unetbootin.sourceforge.net)

---

