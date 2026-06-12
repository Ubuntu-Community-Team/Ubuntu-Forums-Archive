---
title: "Ubuntu doesnt start after USB installation"
date: 2012-10-01
forum: General Help
---

### Post by richter12 on 2012-10-01
hello,
this is the first time for me to use Linux. I just installed Ubuntu on my netbook, using a bootable USB created on a Windows-PC (according to the manual). Starting and installing Ubuntu from the USB was no problem, but after the installation finished, ubuntu doesnt start from the hard drive. There is just a blinking "_" at the upper left corner, furthermore nothing happens. 
I am pretty sure I choosed the hard drive for the installation of ubuntu, all the other data on the hard disc was deleted. But it seems Ubuntu was installed on the USB only, because i can start Ununtu only, when I choose the USB drive in the Boot-Menu. How Can I fix this problem? 

Thank you very much for your help! My first impression of Ubuntu is very good!

Greetings,
Richter

---

### Post by 2F4U on 2012-10-01
Sounds to me as if Ubuntu installed the boot loader Grub to the USB instead of your local hard disk. Seems to be a commonon problem and I had it myself when installing from USB. 

[http://ubuntuforums.org/showthread.php?t=1745247](http://ubuntuforums.org/showthread.php?t=1745247)

It can be fixed from a liveCD/USB, just follow the instructions in the link.

---

### Post by richter12 on 2012-10-01
after following the instructions, i got the grub-rescue> problem. So I just installed Ubuntu again, this time first booting from USB, after that clicking on "install ubuntu" (not directly in the menu on "Install Ubuntu on a hard disc"). Now it works. 

Thank you for your help!

---

