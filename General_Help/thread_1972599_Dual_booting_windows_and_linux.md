---
title: "Dual booting windows and linux"
date: 2012-05-03
forum: General Help
---

### Post by booing on 2012-05-03
A few days ago, I had windows. I got some virus that put stuff in the start menu, disabled my internet, took away 9/10 of my FPS, somehow bypassed AVG, Ad-aware and avast!, put itself somewhere in the root of my computer and created random process names that requested admin permission. I had a linux disc handy, so I just installed linux and told it to destroy the windows partition. My computer came with windows, but I would like to try to get 7(idk how to do this legally for free) or 8 consumer preview, as all of the things I do have no support on linux(except developing, yay linux). I have ubuntu 10.04; I'm sorry if this is not for this forum, but I have a 8GB USB that I would like to boot windows 8 from... what is the most easy method? I want to install windows 8 on my hard drive.

---

### Post by kc1di on 2012-05-03
if you must install it go here to download it :

[http://windows.microsoft.com/en-US/windows-8/iso]("http://windows.microsoft.com/en-US/windows-8/iso")

and here is a step by step guide:

[http://www.theverge.com/2012/2/29/2833006/how-to-install-windows-8-consumer-preview]("http://www.theverge.com/2012/2/29/2833006/how-to-install-windows-8-consumer-preview")

if you decide to dual boot with Ubuntu go here tells you how to do that. 

[https://help.ubuntu.com/community/WindowsDualBoot]("https://help.ubuntu.com/community/WindowsDualBoot")

---

### Post by booing on 2012-05-03
I already have the ISO and I want to do it from linux, but my parents just found a w7 recovery disk... Thanks anyway. I'm sorry to waste your time.

---

### Post by Cheesemill on 2012-05-03
Bear in mind that nearly all recovery disks will only reinstall Windows onto the computer that they came with, so if this is a disk for a different machine then it probably won't work. Even if it did it would be an illegal copy.

To create Windows 8 USB installation media using Ubuntu see here:
[http://www.webupd8.org/2012/01/tool-to-create-windows-usb-install.html](http://www.webupd8.org/2012/01/tool-to-create-windows-usb-install.html)

---

### Post by MikeFranklet on 2012-05-03
If you don't want lose your current ubuntu install, you might be able to use gparted live to resize your ubuntu partition and create another partition alongside it for windows.

Once you install windows to that partition, it will overwrite grub, so you'll have to reinstall that or you'll only be able to boot into windows. If I had to break it down into steps, and if you only have the one USB key, I'd do it like this.

1. Use UNetBootIn to put gparted live on the USB.
2. Boot from USB and use gparted to shrink the ubuntu partition and create the windows partition.
3. Boot back into ubuntu and use it to put a windows 8 iso on the USB.
4. Install windows from the USB.
5. Boot into windows and use UNetBootIn to put the Ubuntu live image back on the USB
6. Boot into Ubuntu live and do "sudo update-grub" in the terminal

That should have it recognize the windows install and put itself back on the MBR.

---

