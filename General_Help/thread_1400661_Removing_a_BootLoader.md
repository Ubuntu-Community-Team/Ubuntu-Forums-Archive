---
title: "Removing a BootLoader"
date: 2010-02-07
forum: General Help
---

### Post by Amrobadr on 2010-02-07
Well, I installed XP Recovery Console as startup, and then I removed it
with only XP, I can boot directly, but after installing ubuntu 9.10 I face 2 boot loaders, the 1st one asks me to choose from XP & ubuntu, when I choose ubuntu I get the Grub, which contains windows XP too .

So, is it possible to remove the 1st bootloader "which let me choose from XP & ubuntu" !!

Thanks

---

### Post by Ordes on 2010-02-07
which bootloader is your first bootloader?

You should make grub your main bootloader. When you reinstall grub it should override your old boot loader...You probably using grub2

[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

---

### Post by Amrobadr on 2010-02-07
The 1st one is the XP bootloader "I think" the default XP one

Grub did not overwrite the old bootloader !!
EDIT: I installed ubuntu in windows .

So, now I have to re-install the grub !!

---

### Post by Ordes on 2010-02-07
normally,your windows bootloader will be overwritten with grub, if you install ubuntu after windows.

what u mean by u installed in windows? did you use wubi?

---

### Post by Amrobadr on 2010-02-07
I mean that I installed ubuntu as : INSIDE WINDOWS, and the grub didnt overwrite the old bootloader

---

### Post by Ordes on 2010-02-07
> **Amrobadr said:**
> INSIDE WINDOWS

?!?!?!?
I get what u saying, and also that your bootloader didnt get overwritten.
But by any means, what does it mean INSIDE WINDOWS??

>> Inside windows would normally point to a virtual machine, that is running inside, or on top of windows. And there wouldnt be a grub loader anyways

>> Wubi, since these days a lot of people seem to use wubi, as it allows you to install ubuntu from inside windows, instead of the tradiditonal way over the liveCD. 
In this way, ubuntu is still a kind of a dual-boot setup but manageble over windows ada/ remove programs.  So a good entry for beginners. Even when i see more bad than good with wubi. In this case, you cannot just use grub, as ubu seems to reside in a folder, instead of a partition. And the whole boot setup through wubi has a different build up.
so, again, did you use wubi or not. cuz thats what i suspect you did for your installation

>> being precise/ detailed in answers will help to fix your problem faster and more precise....

---

### Post by Amrobadr on 2010-02-07
this is my boot.ini info from windows :

```
[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=option /fastdetect
C:\wubildr.mbr = "Ubuntu"
```

---

### Post by Ordes on 2010-02-07
and there it is: wubi...

what happens is your xp booloader loads up, and is than through wubi getting refered to your ubu distro which will load up grub. You will need grub as this is the main bootloader, also for different kinds of boot ups (recovery, kernels, etc..)

in case of wubi, i dont think you can get rid of it, unless you would make drastic changes. 

advice:
leave it like that, 
or get rid of the wubi install, and install ubuntu properly over the liveCD on its own partition...

---

### Post by Amrobadr on 2010-02-07
Sorry,
So, May I have to change the default OS to Ubuntu !!
Like :

[IMG]http://images.ask-leo.com/bootoptions.png[/IMG]

---

