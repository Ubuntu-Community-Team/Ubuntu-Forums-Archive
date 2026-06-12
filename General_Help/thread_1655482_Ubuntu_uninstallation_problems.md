---
title: "Ubuntu uninstallation problems"
date: 2010-12-29
forum: General Help
---

### Post by cezz624 on 2010-12-29
OK, so I decided to try out Ubuntu 10.04, when I finished installing it there was an update to 10.10, I installed it and rebooted but when I booted to Ubuntu, there was just a black screen and my pc just restarted. So i uninstalled it. But now, Ubuntu is still on the OS select screen even when I uninstalled it.. I could only boot into win7. When I try to boot to Ubuntu, Win7 says that Ubuntu is missing or corrupt. Please help me! I tried reinstalling Ubuntu but now to Ubuntu selections are on the OS select screen.(Both can be booted in to.) But when I Uninstalled Ubuntu, the corrupted OS is still there!

---

### Post by cezz624 on 2010-12-29
Oh and just incase you need it, My system is a Compaq CQ5600F Running Win7 Ultimate 64-bit

---

### Post by cipherboy_loc on 2010-12-29
What happened was that when Ubuntu installed itself, it installed a bootloader. You need to reinstall the Windows 7 bootloader to fix your issue. [http://www.ehow.com/how_4836283_repair-mbr-windows.html](http://www.ehow.com/how_4836283_repair-mbr-windows.html) for an example on how to fix that issue.


Cipherboy

---

### Post by cezz624 on 2010-12-29
Thanks, but your method did not work, so i installed Easy BCD and removed Ubuntu. And it worked!

---

### Post by cezz624 on 2010-12-29
And i also fixed the mbr

---

