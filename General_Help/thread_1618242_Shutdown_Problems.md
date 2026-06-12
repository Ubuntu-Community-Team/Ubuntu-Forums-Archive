---
title: "Shutdown Problems"
date: 2010-11-10
forum: General Help
---

### Post by Sideshow Todd on 2010-11-10
Having serious problems: Ubuntu sticks upon shutdown. When I go to shutdown, the splash screen shows and then nothing. I must conduct a hard reboot and illegally shut down. 

Here is a snapshot of my System info:



 [ATTACH]175217[/ATTACH]


PS. I'm on a laptop. 

-Sideshow Todd-

---

### Post by Sideshow Todd on 2010-11-10
I forgot add that the it's 10.10 and that I've installed inside of MS windows. May these facts are pertinent  or maybe they're not.

---

### Post by Hippytaff on 2010-11-10
That's a wubi install then? Wubi can be a pain :-)

have a read of this...if that doesn't answer any questions post back
[https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)
:-)

---

### Post by endotherm on 2010-11-10
not sure if this holds for wubi, but if you absolutely cannot get the system to gracefully shut down, you can use the "Magic SysReq" sequence to sync and unmount your disks and shutdown.

Press and Hold Alt + Printscrn and slowly type
```
r e i s u b
```
when you hit 's' your HDD access light may come on. wait until it is off before hitting 'u'. s writes all unwritten data to your drives, and 'u' unmounts them.

---

### Post by Sideshow Todd on 2010-11-10
Thanks. Doesn't really solve my problem, however, it did inspire me to try something else - installing Ubuntu for real - in a partition. You think that might solve the problem?

For the hell of it I'm booting Maveric and try the other guys idea. It sounds half ***, not being a permanent  solution, but at least I won't have to illegally shut down and corrupt files.

---

### Post by Hippytaff on 2010-11-10
> **Sideshow Todd said:**
> Thanks. Doesn't really solve my problem, however, it did inspire me to try something else - installing Ubuntu for real - in a partition. You think that might solve the problem?

For the hell of it I'm booting Maveric and try the other guys idea. It sounds half ***, not being a permanent  solution, but at least I won't have to illegally shut down and corrupt files.

If you like ubuntu it's best to do what you've decided to do and do a 'real' partition. Wubi gets broken after a while and is only intended to be for trial purposes...also you get the full ubuntu experience with a real install :-)

---

### Post by Sideshow Todd on 2010-11-10
> **Hippytaff said:**
> If you like ubuntu it's best to do what you've decided to do and do a 'real' partition. Wubi gets broken after a while and is only intended to be for trial purposes...also you get the full ubuntu experience with a real install :-)

Reply: The full Ubuntu experience? I don't understand. What experiences am I missing by using a wubi install?

I may dump the wubi install and give the full install a try. But I have to tell ya that I'm worried. I'm worried that I may not be able to escape from behind the locked *gate* and stay a prisoner, looking out the *window*. I'm distraught. I badly wanted this, but this is turning out to be big hassle. God, I hope this full install goes well.

---

### Post by Hippytaff on 2010-11-10
just back up stuff, just incase and do a dual boot from a liveCD...not suggesting you get rid of windows complelely
[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)
and enjoy the best of both worlds :-D

---

### Post by endotherm on 2010-11-11
> **Sideshow Todd said:**
> Reply: The full Ubuntu experience? I don't understand. What experiences am I missing by using a wubi install?

I may dump the wubi install and give the full install a try. But I have to tell ya that I'm worried. I'm worried that I may not be able to escape from behind the locked *gate* and stay a prisoner, looking out the *window*. I'm distraught. I badly wanted this, but this is turning out to be big hassle. God, I hope this full install goes well.
wubi is kinda Ubuntu's red-headed step child as it were, and can cause some weird issues, especially pertaining to the virtual disks it creates for the system to live in.  virtualization presents fake hardware to the os, and most of the time it works fine, but every once in a while, the fake hardware just isn't prepared for what the OS wants to do with it. virtualizing hardware is far from a trivial task, so you can always expect there to be something missing or not quite right. heck, even real hardware seldom implements the specification it was built against 100% correctly. 

I run Ubuntu in virtualbox on a few of my windows boxes, and it is far from the full experience. the biggest lacking on my end is that the video card vbox presents to Ubuntu won't run compiz effects, even if 3da is enabled, and proprietary drivers are installed. IO is slower because of the virtual disks/network, and sometimes usb detection is lacking. in your case, the virtual disks may be preventing you from killing all processes, synching your hdd, unmounting your disks, and sending an ACPI shutdown signal.

it is also quite possible however, that your hardwares ACPI implementation is the culprit, and it and Ubuntu just don't quite mesh. That is troubleshootable, but is closer to the hardware as it were, so removing unknown variables like wubi's idiosyncrasies helps us to get down to cases on your exact issue. 

HTH

---

### Post by Sideshow Todd on 2010-11-14
I might give the live CD a try, just for the hell of it.

I download the ISO onto a 800mb disk. Must I down a special ISO for a live CD, or can I use this one for a live CD?

---

### Post by Hippytaff on 2010-11-14
You can use that one...all the ISO's can be used for live cd's as far as I am aware :-)

---

