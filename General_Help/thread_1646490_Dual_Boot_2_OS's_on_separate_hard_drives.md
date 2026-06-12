---
title: "Dual Boot 2 OS's on separate hard drives"
date: 2010-12-15
forum: General Help
---

### Post by lamey on 2010-12-15
Hello I'm brand new to the site and ubuntu, and I've run into a problem I need some help with. I am currently running 2 SATA hard drives, 1 with ubuntu 10.10 installed, the other with windows 7. I am wondering how to set it up so that during boot I will be prompted to choose a hard drive / operating system to start. Is there any program in linux that could do this or will I need to try to change the BIOS, or will I have to change the boot order each time i want to change my OS?

---

### Post by Quackers on 2010-12-15
Welcome to UF.
If you change your bios to boot from the Ubuntu hard drive first then boot Ubuntu. When the desktop appears open up a terminal (Applications > Accessories > terminal) and run ```
sudo update-grub
```
then watch the terminal as grub.cfg is configured to see whether a Windows entry is listed.
If it is reboot and you should get a black and white grub menu with the choice of OS to boot.

---

### Post by lamey on 2010-12-15
Thank you! Will try this now and let you know how it goes.

---

### Post by Quackers on 2010-12-15
That would be nice :-)

---

### Post by lamey on 2010-12-15
worked perfectly, thanks a lot for the help.

---

### Post by Quackers on 2010-12-15
You're welcome, glad to help.
Please mark the thread as solved using the Thread Tools near the top of the page. Thanks.

---

