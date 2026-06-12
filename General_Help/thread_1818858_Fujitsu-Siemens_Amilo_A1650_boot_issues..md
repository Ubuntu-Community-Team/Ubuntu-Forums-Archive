---
title: "Fujitsu-Siemens Amilo A1650 boot issues."
date: 2011-08-05
forum: General Help
---

### Post by SoulTechnologist on 2011-08-05
Hi everybody,

I am not totally a rookie when it comes to installing Ubuntu on someone's laptop, but the followings never happened to me.
I am aware that I have to set the boot priorities in order to make it start from USB. I did it, no go. Tried every single USB slot, no go. I also tried to boot from the CD and it gives me the exact same result. I really don't know what else to try, I have been working on it for almost 5 hours now and I begin to feel my rage pumping to my head...
Just to give you every info, for the USB boot I tried both UNebootin as well as well as Universal USB Installer. I am sure things are done good, since I used this methods several times for several users...till now of course.
The live CD as well is ignored during the BOOT process. It's just like it doesn't even bother to check those devices, since the CD/DVD light is not even flashing when it boots.
I have also checked to see if it reads disks, and it does so under MS Win XP...I simply cannot boot from USB or LiveCD...which sadly means I simply cannot install my favourite OS (Ubuntu) and make my friend a gift...

Please help...

P.S. The distro i'm trying to install is Ubuntu 10.10

= = = =
More advice here: 
[http://ubuntuforums.org/showthread.php?t=1543006&page=147&p=12859180&viewfull=1#post12859180](http://ubuntuforums.org/showthread.php?t=1543006&page=147&p=12859180&viewfull=1#post12859180) 
Mörgæs 2013-11-27

---

### Post by galvatron408 on 2011-08-05
I had an old laptop that had a broken cd-rom drive, no usb boot option but had a PXE boot. I spent a little time building a kickstart image. Then, I was able to install over the network.

Kickstart isn't for a rookie but you said you are not. So, here is the link to the how to.

[https://help.ubuntu.com/community/PXEInstallServer](https://help.ubuntu.com/community/PXEInstallServer)

---

### Post by SoulTechnologist on 2011-08-05
That's great galvatron...I'll give it a look. But I will use it as my plan B or emergency parachute...For now my problem is why I am able to change the boot devices priority but the machine acts like it doesn't even pay attention to it. And for the cd-rom drive, it is not broken since it's able to read whatever CD/DVD on windows. I don't know why, but to me it seems it just ignore the boot priority and goes straight to HD and I really want to understand why...
Do you have any guesses?...I really want to fix this, plus I've seen many people using Ubuntu on that machine...

---

### Post by SoulTechnologist on 2011-08-05
I did anything I know until now...tried every BIOS setting that could hepl, visited every forum both related to linux and to the laptop in general and still got nothing...
Please Ubuntu community members...save me...

---

### Post by daniel227 on 2011-10-25
hello, 

i had problems installing ubuntu on my amilo 1645, maybe this thread helps:

[http://ubuntuforums.org/showthread.php?t=1835514](http://ubuntuforums.org/showthread.php?t=1835514)

btw, i couldn't boot from usb although it should b possible according to bios.
i checked amiloforums, there's talk about crappy bios versions. 

good luck!

---

