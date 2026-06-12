---
title: "32 Ubuntu on 64 bit Windows"
date: 2011-07-17
forum: General Help
---

### Post by salmontres on 2011-07-17
Hi guys,

I'd like to install 32 bit Ubuntu using Wubi on a 64 bit Windows OS. When I install the OS, it automatically installs the 64 bit Ubuntu, which is problematic for some of the programs I'm running. How do I specify to Wubi that I want the 32 bit OS? Is it better to simply work around Wubi entirely?

---

### Post by wildmanne39 on 2011-07-17
> **salmontres said:**
> Hi guys,

I'd like to install 32 bit Ubuntu using Wubi on a 64 bit Windows OS. When I install the OS, it automatically installs the 64 bit Ubuntu, which is problematic for some of the programs I'm running. How do I specify to Wubi that I want the 32 bit OS? Is it better to simply work around Wubi entirely?Hi, I do not know much about wubi I am going to give you some links to look at that might answer your question.
[http://ubuntuforums.org/showthread.php?t=1639198](http://ubuntuforums.org/showthread.php?t=1639198)
[http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-](http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-)
[https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)

As for installing without wubi that is the best way in my opinion but it can be a little harder to install but not much.

---

### Post by salmontres on 2011-07-17
Thanks for the quick response Wildmanne!

I have installed without Wubi before, and I didn't think it was too hard. However, installing with Wubi is much more convenient, but I think it also introduces glitches into Ubuntu. I never had problems with USB mice before, and this one on my laptop glitches on occasion. Also, the battery life reader isn't accurate at all, and the brightness on my screen can't be changed.

Has anyone else experienced strange glitches when installing with Wubi?

---

### Post by srisharan on 2011-07-17
Yes,you might experience performance problems and glitches with wubi so it is recommended that you dual boot.And If you want to install the 32 bit ubuntu,download the 32bit iso from ubuntu website instead of relying on wubi to download

---

### Post by grahammechanical on 2011-07-17
Could you not try virtualbox? There is a Windows version. Wubi is a Windows program like other Windows programs. It is running on a 64bit OS. A 32bit Ubuntu might not work with Wubi on a 64bit Windows OS because it does not have direct access to the hardware.

I have used virtualbox to run 32bit Ubuntu on a 64bit Ubuntu.

Regards.

---

### Post by wildmanne39 on 2011-07-17
+1 virtualbox is good, I have used it for years to run windows.

---

### Post by salmontres on 2011-07-18
Thanks everyone,

I ended up doing a clean install in my laptop with a live CD without using Wubi. The reason why I want to avoid VirtualBox is that I need this running on my laptop. I didn't want to allocate some of the already very limited resources on an additional OS.

I did want to mention that I don't see any of the same glitches when I don't use Wubi, for anyone else interested.

---

### Post by wildmanne39 on 2011-07-18
> **salmontres said:**
> Thanks everyone,

I ended up doing a clean install in my laptop with a live CD without using Wubi. The reason why I want to avoid VirtualBox is that I need this running on my laptop. I didn't want to allocate some of the already very limited resources on an additional OS.

I did want to mention that I don't see any of the same glitches when I don't use Wubi, for anyone else interested.
Hi, thats great I am glad ubuntu is working good now.

---

