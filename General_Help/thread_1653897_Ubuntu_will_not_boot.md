---
title: "Ubuntu will not boot"
date: 2010-12-27
forum: General Help
---

### Post by 1492 on 2010-12-27
I have a dual-boot Ubuntu 10.10 & Windows 7 computer. I when choose "Ubuntu" on the boot menu, it just says something about no wubldr, then the screen goes blank, & it goes back to the boot menu. The last time I used Ubuntu I installed some updates, and it told me to restart the computer. I restarted the computer, and Ubuntu wouldn't start. What should I do? Any help is appreciated

---

### Post by 1492 on 2010-12-27
[COLOR=White]bump?[/COLOR]

---

### Post by oldfred on 2010-12-27
I do not know wubi, but there are a few common issues. These regular posters have solutions to most of the issues with wubi.

how to fix those Wubi installation breakages without going crazy Rubi1200 Dec 2010
[http://ubuntuforums.org/showthread.php?t=1639198](http://ubuntuforums.org/showthread.php?t=1639198)
Fix for 10.04 upgrade fail bcbc copy wubildr or edit grub.cfg
[http://ubuntuforums.org/showpost.php?p=9932369&postcount=5](http://ubuntuforums.org/showpost.php?p=9932369&postcount=5)
[http://ubuntuforums.org/showpost.php?p=10180520&postcount=78](http://ubuntuforums.org/showpost.php?p=10180520&postcount=78)

---

### Post by 1492 on 2010-12-27
I am not using Wubi, it just displays a message about it every time I boot into Ubuntu. It is a dual-boot, though.

---

### Post by 1492 on 2010-12-27
bump...

---

### Post by bcbc on 2010-12-27
From what you describe you are using wubi. (the wubildr is the bootloader for wubi installs).

You can confirm - boot windows, go to control panel, add/remove programs, look for an Ubuntu entry.
Look for the c:\ubuntu folder
etc.

If you confirm a wubi install, then the first link from oldfred is what you want. 

Also likely you have 10.04.1, not 10.10. The ubuntu.com website is confusing as it shows 10.10 but if you select the windows-installer option it actually downloads 10.04.1. (and the problem you are describing is happening to 10.04.1 installs)

Hope that helps.

---

### Post by camtom12 on 2010-12-29
New guy here with a very similar problem.  I've got a dual boot with XP, though.
 
I'll check out those links you posted but subscribing here for any updates!

---

### Post by Rubi1200 on 2010-12-29
Hi and welcome to the forums camtom12 :-)

The [Wubi Megathread]("http://ubuntuforums.org/showthread.php?t=1639198") is the place to go for issues and solutions.

---

### Post by Kirboosy on 2010-12-29
If you are using Wubi I don't think its possible to select an alternate kernel to boot (I've never used Wubi so I could be wrong.) I think you need to 'Live CD' Ubuntu mount the directory and manually edit the grub.cfg file. 

It sounds like it was a kernel update or a major system update if it asked you to reboot. Changing the grub back to the older kernel should fix the issue (in theory)

---

### Post by bcbc on 2010-12-29
> **Caboose885 said:**
> If you are using Wubi I don't think its possible to select an alternate kernel to boot (I've never used Wubi so I could be wrong.) I think you need to 'Live CD' Ubuntu mount the directory and manually edit the grub.cfg file. 

It sounds like it was a kernel update or a major system update if it asked you to reboot. Changing the grub back to the older kernel should fix the issue (in theory)

The grub-pc update happened to coincide with a kernel update. The problem is unrelated to the kernel. 

yes you can select alternate kernels with wubi - normally. Not with this problem as grub fails to present it. The wubi megathread explains all (it's not related to the kernel update).

---

### Post by 1492 on 2010-12-29
It's working now, thank you so much!

---

### Post by Rubi1200 on 2010-12-30
> **1492 said:**
> It's working now, thank you so much!

On behalf of bcbc and myself, you are more than welcome :-)

---

