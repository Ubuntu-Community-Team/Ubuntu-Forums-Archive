---
title: "USB Install"
date: 2012-05-06
forum: General Help
---

### Post by pghud3 on 2012-05-06
Hello,

Is there a way i can install Ubuntu 12.04 to a usb like you would to a hard drive and it not run slow?  I have read online that you manully create your root partition and leave out the swap space (cause the swap space will shorten the life of the USB) .  Is there a way i can install to the usb drive and it not run so slow? or do i just need to put the swap space on there? I want to be able to have a user account and install updates and programs so they are they when i use the drive the again. And it just runs like its installed on a hard drive.

What do you recommend is the best way to do this?

Thanks,
PGH

---

### Post by oldfred on 2012-05-06
Is this a USB flash drive or a spinning hard drive?

USB ports are slower than SATA, and flash drives are slow writing. If using flash drive you want to change settings to reduce writes. I have a full install of 12.04 on a flash drive, it is not speedy but is functional. More RAM memory helps as Ubuntu caches recent use in RAM. If system is limited the Lubuntu may be a better choice as apps are lighter weight.

Installs to 4GB flash, newer versions require 4.4GB as minimum
HOW TO Avoid Wubi & Install Ubuntu 10.04 on USB Drive -amjjawad
[http://ubuntuforums.org/showthread.php?t=1650699](http://ubuntuforums.org/showthread.php?t=1650699)
HOW TO Install Lubuntu on USB Drive - amjjawad
[http://ubuntuforums.org/showthread.php?t=1872303](http://ubuntuforums.org/showthread.php?t=1872303)

---

### Post by pghud3 on 2012-05-06
its one a usb flash drive.  If i used a usb external hard drive would it be faster?  Or am in stuck where im at?

---

### Post by oldfred on 2012-05-06
Flash writes are slow. So a USB hard drive will be faster than a flash drive. But USB ports are not as fast as SATA ports. Often more RAM makes up for some of the slowness as Ubuntu caches as much as it can in RAM, so if you do something again it can be real quick from RAM. Using swap is slow.

---

### Post by pghud3 on 2012-05-07
So if i get a external Hard drive and connect it trough usb it should be faster than a just useing a USB thumb drive correct?

---

### Post by oldfred on 2012-05-07
Yes, my flash drive is functional, but not speedy. I notice large apps take a bit to load with flash drive, where my hard drive is barely noticeable.

But my laptop with only 1.5GB of RAM can be slow from hard drive if I have several larger apps loaded and do something else. It is fine with just Firefox or just LibreOffice.

---

