---
title: "Ubuntu 10.04 black screen HELP!!!"
date: 2010-04-24
forum: General Help
---

### Post by bwy on 2010-04-24
Hi. Halp me with my problem. I tryed to install ubuntu 10.04 (x86). I am start computer with live flash, but have only ubuntu picture and black screen. After I press F6 (optios) and put "nomodues" and live flash start normaly. But after instalations the problen is exist again. Only a black scren. Please halp me. My videocard is radeon xpress 1300M
 
P.S. Sorry for my english

---

### Post by lollobrigido on 2010-04-30
I'm too in this situation!
but...the choice "nomodues" ...where is?
Lollo

---

### Post by bwy on 2010-04-30
> **lollobrigido said:**
> I'm too in this situation!
but...the choice "nomodues" ...where is?
Lollo

I am sorry. This parameter is nomodeset you can find it in menu, whee it is ask you yo make a choise between try ubuntu, install, boot from hard disk and so on. In this menu just press F6 and you will see this parameter. And us I am understand, we need to ad this parameter to the GRUB. I tried some variants, but it is not works :(

---

### Post by Okami on 2010-05-01
Try modeset=0 or radeon.modeset=0

---

### Post by dracayr on 2010-05-01
so ubuntu is correctly installed? can you boot in recovery mode / Safe graphics mode?

I had the same problem, and there are a bunch of causes and solutions.

Look here:
[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/568779](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/568779)

---

### Post by not1 on 2010-05-01
It's a known bug.

A HUGE bug.

[http://ubuntuforums.org/showthread.php?t=1466337]("http://ubuntuforums.org/showthread.php?t=1466337")

---

### Post by bwy on 2010-05-10
:( nothing helps.... and this bug in release..... :(

---

