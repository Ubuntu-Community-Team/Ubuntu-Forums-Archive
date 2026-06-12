---
title: "Kernel thread helper error"
date: 2010-08-31
forum: General Help
---

### Post by Adiwubi on 2010-08-31
Hi. I recently bought a new Toshiba C650-I5011 model. I downloaded Ubuntu 10.04 from the net and when i tried to run it from the CD, it threw an error like : "kernel.thread helper+0x7/0x10".

After reading a few articles in this forum, I figured that it might be an ACPI problem and thus turned the acpi off during boot from the CD. After successfully installing Ubuntu, i am getting the same error when booting from the hard disk.

Please tell me how to solve the problem. There is no 'menu.lst' file in boot/grub for my installation. Do i have to create it ? Please help ..

---

### Post by sph0600069 on 2010-09-21
i have the exact same problem please reply!

---

### Post by bejazzy on 2010-12-20
A same topic is open and seems fix this problem. Please read
[http://ubuntuforums.org/showthread.php?t=1512948](http://ubuntuforums.org/showthread.php?t=1512948)

---

### Post by seif_tun on 2011-02-24
Hello,

Thanks for Reply 

Well I fixed the problem:) I chose F1 in ubuntu installation menu screen to enter help menu ,then F6 and typed 
"live-install acpi=off" and that worked fine!

But :( both usb keyboard and usb mouse are not working at all so I cannot connect to my session ..

Thank you for help:)

---

