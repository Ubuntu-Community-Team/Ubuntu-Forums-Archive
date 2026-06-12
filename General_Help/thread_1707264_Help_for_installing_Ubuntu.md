---
title: "Help for installing Ubuntu"
date: 2011-03-15
forum: General Help
---

### Post by f69 on 2011-03-15
[B]Hi 
I had downloaded the Ubuntu 10.10 Desktop 32Bit from it`s web site. 
My system information is : 
[COLOR=Blue]
Cpu : AMD Athlon 2500+ 
Vga : 128 Mb Ati 9550
Ram : 512 Mb x 2 = 1G
Hdd : maxtor[/COLOR]

But I can`t use or install ubuntu on my system.
I test the CD that i download on other Computer with Intel CPU and it worked.
But on my system after boot from CD and select one of item from ubuntu menu , the screen goes black and nothing is happening.

is that possible this problem is for AMD cpu ??
or is there any AMD support release ???
Please help me find out the problem.

Thanks for your attention.
[/B]

---

### Post by mastablasta on 2011-03-15
> **f69 said:**
>  
**is that possible this problem is for AMD cpu ??**
**or is there any AMD support release ???**

 
No AMD64 release is just 64bit version of system.
 
it is probably a graphics card issue.
 
try this Solution 1: [http://www.ubuntugeek.com/how-to-fix-ubuntu-10-04-lts-lucid-blank-screen-at-startup.html](http://www.ubuntugeek.com/how-to-fix-ubuntu-10-04-lts-lucid-blank-screen-at-startup.html)
 
 
if it works then this: [http://ubuntuforums.org/showthread.php?t=1675337](http://ubuntuforums.org/showthread.php?t=1675337)
 
on another radeon issue:
[http://ubuntuforums.org/showthread.php?t=1466952](http://ubuntuforums.org/showthread.php?t=1466952)

---

### Post by f69 on 2011-03-15
> **mastablasta said:**
> No AMD64 release is just 64bit version of system.
 
it is probably a graphics card issue.
 
try this Solution 1: [http://www.ubuntugeek.com/how-to-fix-ubuntu-10-04-lts-lucid-blank-screen-at-startup.html](http://www.ubuntugeek.com/how-to-fix-ubuntu-10-04-lts-lucid-blank-screen-at-startup.html)
 
 
if it works then this: [http://ubuntuforums.org/showthread.php?t=1675337](http://ubuntuforums.org/showthread.php?t=1675337)
 
on another radeon issue:
[http://ubuntuforums.org/showthread.php?t=1466952](http://ubuntuforums.org/showthread.php?t=1466952)


[B]Thank you very much, I will try these.

But I use my graphic card on other Computer with intel CPU and after boot from Cd that black screen appeared for 2 sec and after that ubuntu run correctly .
Is it possible the problem is for Cpu ?
 
[/B]

---

### Post by mastablasta on 2011-03-16
it could be just plymouth (start animation) is not loading. if ubuntu works afterwards then everyhitng is ok and the plymouth issue has some workarround. though usually this happens on install.
 
also if you boot from CD it may take quite some time too boot. CD/DVD reading is very slow compared to hard disk or USB drive. Sytsem will also work quite a bit slower than upon install.

---

### Post by f69 on 2011-03-16
> **mastablasta said:**
> it could be just plymouth (start animation) is not loading. if ubuntu works afterwards then everyhitng is ok and the plymouth issue has some workarround. though usually this happens on install.
 
also if you boot from CD it may take quite some time too boot. CD/DVD reading is very slow compared to hard disk or USB drive. Sytsem will also work quite a bit slower than upon install.

thanks indeed.
but in my computer i wait for 20 min , and still black screen ( like command line) was still there.
I don`t know what to do !

---

### Post by Kirboosy on 2011-03-16
Welcome to the Forums! :D

If the cd drive is still chugging then I would say its still loading, but if it doesn't seem like anything is really going on then I would turn it off. Since the computer you are trying to install it on is older I would expect it to take a good bit of time. (I don't think it should take 20 minutes though)

> try this Solution 1: [http://www.ubuntugeek.com/how-to-fix...t-startup.html]("http://www.ubuntugeek.com/how-to-fix-ubuntu-10-04-lts-lucid-blank-screen-at-startup.html")
 
 
if it works then this: [http://ubuntuforums.org/showthread.php?t=1675337](http://ubuntuforums.org/showthread.php?t=1675337)
 
on another radeon issue:
[http://ubuntuforums.org/showthread.php?t=1466952](http://ubuntuforums.org/showthread.php?t=1466952)+1

If you have the parts and your computer is compatible I would try making a [Pendrive]("http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/")


~Caboose

---

