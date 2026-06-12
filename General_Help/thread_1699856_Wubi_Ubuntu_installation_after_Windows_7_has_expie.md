---
title: "Wubi Ubuntu installation after Windows 7 has expiered"
date: 2011-03-04
forum: General Help
---

### Post by JediClone on 2011-03-04
I just got a new pc without os on it... I wanted to install Ubuntu, but for some reason Ubuntu live cd wouldn't boot. So, i installed Windows 7 and then i installed ubuntu with wubi... My question is: Will i be able to use Ubuntu after Windows 7 30 day trial expires? When windows 7 trial expires will it only lock windows 7 or will it destroy boot file (I read that somewhere on the internet)?

---

### Post by Frogs Hair on 2011-03-04
Wubi installs ubuntu inside the windows partition , so if your  Windows trial locks down as you say you may loose Wubi. 

There some are files stored in Windows that make booting Ubuntu possible , also a Wubi installation uses the Windows boot loader.   

It is possible to move a wubi installation to its own partition.
[http://ubuntuforums.org/showthread.php?t=1519354&highlight=wubi+partition](http://ubuntuforums.org/showthread.php?t=1519354&highlight=wubi+partition)

---

### Post by Rubi1200 on 2011-03-04
I think Frogs Hair is probably correct. 

Wubi uses the Windows bootloader for the booting process.

Therefore, if Windows gets locked down, Wubi will be inaccessible.

---

### Post by Zero2Nine on 2011-03-04
I don't think Windows will kill its own bootloader? Maybe they changed that now but I once had a version of XP which also required activation in 30 days. After that period Windows still booted but you could not do anything except activating. In that case any other OS in the bootloader should still work I guess. But don't let it get that far, better take action before it's too late.

Back up all your important files so you can do a clean install of Ubuntu in case Wubi-Ubuntu becomes unusable.

---

### Post by Frogs Hair on 2011-03-04
The files stored in Windows are Ubuntu , MBR  , and Wubildr. I agree that the boot loader may not be locked . I don't know if the other needed components would work. Take jediClones advice and go for a clean installation.

---

### Post by JediClone on 2011-03-04
I installed ubuntu on different partition... Windows 7 is in C, and ubuntu is in F... I already tried to do a clean install but for some reason i couldn't... When i get to chose partition where to install ubuntu i get some message like root could't be found, or something like that... I will backup all the important files, but i hope ubuntu will stay after windows 7 has expired...

---

### Post by Frogs Hair on 2011-03-04
You may have read this already , but just in-case .

[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)
[https://help.ubuntu.com/community/Installation](https://help.ubuntu.com/community/Installation)

---

