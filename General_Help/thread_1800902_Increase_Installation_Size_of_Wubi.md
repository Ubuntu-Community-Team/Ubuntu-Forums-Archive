---
title: "Increase Installation Size of Wubi"
date: 2011-07-09
forum: General Help
---

### Post by Shady211 on 2011-07-09
I am trying to install Ubuntu via Wubi on a 120GB hard drive but the max installation size is only 30GB. I can NOT use a CD/DVD or USB to boot because I get an error 'BOOTMGR is missing press CTRL + ALT + Delete to restart' I'm currently on Windows 7 and have looked into fixing that error. I have tried using a Windows 7 recovery disc and followed some guides but I can't seem to fix it. So I am left with the only option of installing Ubuntu via Wubi but I want to use the entire hard drive, and not just 30GB. So what I'm asking is if there is a way to increase the size.

---

### Post by Old_Grey_Wolf on 2011-07-09
That is one of the limitations of using a WUBI install. If you want to use more disk space you will have to dual boot, use virtualization; such as, VMware Player or Virtualbox, or install Ubuntu as the only OS on the computer.

It looks like you tried the traditional install but get an error message from Windows 7. Did you change the boot order in the computer's BIOS to boot from a CD/DVD or USB? I don't understand the error if you did. Windows 7 should not be giving you errors if the BIOS is set to boot from the CD/DVD or USB. Also, what release (10.04, 10.10, 11.04) of Ubuntu are you trying to install?

Most computers display a screen briefly when they boot that tells you to press F12, F10, F2, Esc, etc., to go to Setup or Temporarily Change Boot Order.

---

### Post by wildmanne39 on 2011-07-09
Hi, I agree with Old_Gray_Wolf it sounds like you need to change your boot order in bios to boot a cd or usb stick. If you still want to install with wubi here is a guide that you can use to resize your partition after you install ubuntu with wubi, however if you have a problem with windows it may affect your ubuntu install as well since it will be installed in windows.
[http://ubuntuforums.org/showthread.php?t=1625371](http://ubuntuforums.org/showthread.php?t=1625371)

---

### Post by Shady211 on 2011-07-10
The boot order is not the problem. I tried booting from a DVD and a USB, and the boot order was correct for each. I decided to stick with a 30gb ubuntu install and use an external drive for extra storage.

---

### Post by wildmanne39 on 2011-07-10
> **Shady211 said:**
> The boot order is not the problem. I tried booting from a DVD and a USB, and the boot order was correct for each. I decided to stick with a 30gb ubuntu install and use an external drive for extra storage.Hi, I am glad you figured out a way that works for you, would you please go to the top of the page and mark this thread solved be clicking on thread tools. Thank you so much.

---

