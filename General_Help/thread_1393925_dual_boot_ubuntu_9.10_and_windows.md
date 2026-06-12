---
title: "dual boot ubuntu 9.10 and windows"
date: 2010-01-29
forum: General Help
---

### Post by Ranko95 on 2010-01-29
Hey guys, I currently have ubuntu 9.10 installed on my computer. I want to dual boot windows 7 WITHOUT using a usb or dvd to install.(i do not have a usb large enough for the win7 .iso) I am thinking about installing tinyxp from usb and then using a virtual drive from winxp to install windows 7. I know there is an issue with installing windows after because of the bootloader. Does anyone have instruction on how to do this? I read this article: [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows) and it says not to use ubuntu 9.10 for some reason. I dont understand the warning very well could someone provide clarification? 

Thanks!

---

### Post by howefield on 2010-01-29
> **Ranko95 said:**
> ..and it says not to use ubuntu 9.10 for some reason. I dont understand the warning very well could someone provide clarification?

The version of grub used in Ubuntu installations changed in 9.10, so if you used it to restore 9.04 which you appear to be running, you would have problems, you need to use a 9.04 cd to restore grub.

---

### Post by mr clark25 on 2010-01-29
i just got done doing this with vista, so dont let anyone tell you it can't be done. (besides the DVD part...)

the bootloader will work if you restore it.


[http://ubuntuforums.org/showthread.php?t=1388222](http://ubuntuforums.org/showthread.php?t=1388222)

---

