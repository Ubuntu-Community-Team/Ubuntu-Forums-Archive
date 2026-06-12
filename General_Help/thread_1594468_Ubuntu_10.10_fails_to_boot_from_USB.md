---
title: "Ubuntu 10.10 fails to boot from USB"
date: 2010-10-12
forum: General Help
---

### Post by kumpsath1 on 2010-10-12
I recently created a bootable pen drive using unetbootin of Ubuntu 10-10 release. It was failing with error message similar to 'specify the init' then formatted the pendrive/usb and now it was giving,
SYSLINUX 3.63 Debian 2008-07-15 EBIOS CopyRight ..... 
Could not find kernal image. boot:
when you press enter it again goes to 
Could not find kernal image. boot: linux

I believe this is due to USB creator. Let me try with creating bootable USB from some windows machine.

---

### Post by C.S.Cameron on 2010-10-12
I understand that UNetbootin is not yet working with 10.10.
Startup Disk Creator from the Live CD worked for me with 32 bit.
First check the MD5SUM of the iso.

---

### Post by Schrute Farms on 2010-10-12
I sure it has something to do with your computer.  There are options you can add to help it boot, but I don't know them.  Maybe someone with some knowledge will post them.

I'm sure it has to do with your computer, because when I create a live image on a usb thumb drive, it does the exact same thing on my desktop.  But when I take the same drive to another computer, it will work.

So if you have another computer available, try the drive on it.  I bet it works.

---

