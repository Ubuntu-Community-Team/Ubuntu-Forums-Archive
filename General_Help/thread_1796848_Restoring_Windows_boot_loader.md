---
title: "Restoring Windows boot loader"
date: 2011-07-04
forum: General Help
---

### Post by rc_enzo on 2011-07-04
Hi,

My setup is like this:
* Installed Windows 7 on primary (SATA) hard drive
* Installed Ubuntu 11.04 on secondary (IDE) hard drive

I've worked with Wubi before, and I liked it so much, I decided to go full scale with Ubuntu. However, I think I've missed an option in the setup, because Grub has now taken over my bootloader. I tried reverting to the Windows loader with EasyBCD, but booting Ubuntu from there is impossible, since it doesn't show itself. By the way, I don't really understand EasyBCD, so that makes it even harder...

Anyway, what I'm trying to accomplish here, is to get a bootloader which uses Windows as default and Ubuntu as secondary OS. How do I do this?

rc_enzo

---

### Post by JRV on 2011-07-04
Any of the three methods listed in this thread will work.

[http://ubuntuforums.org/showthread.php?t=1795241](http://ubuntuforums.org/showthread.php?t=1795241)

---

### Post by rc_enzo on 2011-07-04
Got it! Thank you!

---

