---
title: "Executable bit problem"
date: 2011-08-16
forum: General Help
---

### Post by fearpplen on 2011-08-16
Hi. This is my first time using Ubuntu and i have a little problem here.
My system don't allow me to allow me to enable the executable bit in my program located in my Windows drive.
I have tried [http://www.chrislees.info/ubuntu/easy-run-files.shtml](http://www.chrislees.info/ubuntu/easy-run-files.shtml) but it wont help.
Please help me to solve this

---

### Post by mikewhatever on 2011-08-16
The executable bit is a feature of the Linux file systems. Since the program is somewhere in the Windows driver, it most certainly isn't in a Linux file system, and therefore, no executable bit.
In short, Linux permissions only work on Linux file systems.

---

### Post by 3rdalbum on 2011-08-16
The instructions on my website don't help you set the execute bit - they allow you to run Wine without having to have the execute bit set.

What part doesn't work, and exactly what goes wrong when you try it?

Also, be aware that usually programs don't run directly from your Windows drive - you have to install those programs in Wine like you would in Windows.

---

