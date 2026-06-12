---
title: "Ubuntu Setup"
date: 2010-04-18
forum: General Help
---

### Post by cayennurff on 2010-04-18
Hi everyone:), i would like to ask some questions before i start using Ubuntu. Its an OS right, so do i need to install drivers of my hardware? My computer is (DIY) done myself, and the drivers that are supplied by the manufacturer is for Windows platform. How do i find/get/install the drivers?

Secondly which is better, wubi or dual booting?

Thirdly is there any difference between using AMD/Intel?

Lastly can i play Steam games on Ubuntu?

---

### Post by Bucky Ball on 2010-04-18
You might like to check out the Never Tried Linux thread in my signature.

In short, download the appropriate ISO file for your machine (64 or 32 bit, forget the AMD, i386 part), burn a cd and run the OS from the CD.

---

### Post by 3rdalbum on 2010-04-18
> **cayennurff said:**
> Hi everyone:), i would like to ask some questions before i start using Ubuntu. Its an OS right, so do i need to install drivers of my hardware?

Maybe your graphics card, but probably not anything else.

> Secondly which is better, wubi or dual booting?

Make a proper dual-boot by booting up from the Ubuntu CD and telling it to resize your Windows partition. Give it a fair amount of space - I'd say 10 gigs would be an absolute minimum.

> Thirdly is there any difference between using AMD/Intel?

Recent Intel CPUs are better than recent AMD CPUs, but a CPU is a CPU - it'll work as well with Ubuntu as it does with Windows.

> Lastly can i play Steam games on Ubuntu?

You can't really run Windows programs on Ubuntu, nor vice-versa. There is, however, a program on Linux called Wine that is best described as a "last resort for running Windows programs". It can run some programs, but don't expect great things of it.

You might get some Steam games to work with Wine. But you're on a different operating system, it really needs its own programs.

---

### Post by cayennurff on 2010-04-19
Hi:),
> **3rdalbum said:**
> Maybe your graphics card, but probably not anything else.
Hmmm, so for graphics card, do i download Linux x86/ Linux x86_64. It works for all versions of linux?

> **3rdalbum said:**
> 
Make a proper dual-boot by booting up from the Ubuntu CD and telling it to resize your Windows partition. Give it a fair amount of space - I'd say 10 gigs would be an absolute minimum.

So lets say i got a 500GB Harddisk, i split 250,250? what you mean by resize my windows partition? So i install Windows first or Linux first?


Another thing i realised from the Beginner's Guide, its for Windows XP/Vista, has anyone tried for Windows 7? 

Thanks for all the answers in advance!

---

### Post by 3rdalbum on 2010-04-19
> **cayennurff said:**
> Hi:),

Hmmm, so for graphics card, do i download Linux x86/ Linux x86_64. It works for all versions of linux?

Ubuntu has a program that will download and install graphics card drivers for you. It's MUCH better to do it this way than to manually download and install them.

If you have Intel graphics then you don't even need to do that.

Use 64-bit Ubuntu if your CPU can handle it and you've got a reasonable amount of RAM (2 gigs or so).

> So lets say i got a 500GB Harddisk, i split 250,250? what you mean by resize my windows partition? So i install Windows first or Linux first?

Windows first, always. Yeah, split it 50/50 if you want, it just depends on how much space you want to use for personal files. You probably won't go over 20 gigabytes for programs.

I thought you already had Windows installed and taking up the whole disk (as in, one partition on the disk), which is what I meant by letting the Ubuntu installer resize the Windows partition to make space.

> Another thing i realised from the Beginner's Guide, its for Windows XP/Vista, has anyone tried for Windows 7?

The procedure is the same regardless. When Ubuntu is running, it really doesn't matter what version of Windows is sitting on the disk. And when Windows is running it doesn't matter what version of Ubuntu.

---

### Post by mifi on 2010-04-19
If the windows is not yet installed and you have enough memory installed, you might consider installing Ubuntu first and virtualbox next (virtualbox.org).
Then create a virtual machine in virtualbox and install windows in the virtual machine.

Given enough memory, you will have a machine that is running ubuntu and windows at the same time. Much more convenient than a multiboot setup where you have to reboot to switch OS.

But beware, the amount of memory in the machine must be sufficient to support both at the same time...

m

---

### Post by seenthelite on 2010-04-19
[http://ubuntuguide.org/wiki/Ubuntu:Karmic](http://ubuntuguide.org/wiki/Ubuntu:Karmic)
[http://www.howtoforge.com/the-perfect-desktop-ubuntu-9.10-karmic-koala](http://www.howtoforge.com/the-perfect-desktop-ubuntu-9.10-karmic-koala)

---

### Post by cayennurff on 2010-04-19
> **3rdalbum said:**
> Ubuntu has a program that will download and  install graphics card drivers for you. It's MUCH better to do it this  way than to manually download and install them.

If you have Intel graphics then you don't even need to do that.

Use 64-bit Ubuntu if your CPU can handle it and you've got a reasonable  amount of RAM (2 gigs or so).

I am either going to use HD4850/ On-board graphics of the HD4200 by ATI. So is that program within linux or have to download separately? btw motherboard drivers needed? those for USB, or are they within Linux? I'm still not sure with the 64-bit in linux, only know that for Windows, to support above 4GB.


> **3rdalbum said:**
>  I thought you already had Windows installed and taking up the whole disk  (as in, one partition on the disk), which is what I meant by letting  the Ubuntu installer resize the Windows partition to make space.

Oh i'm actually thinking of setting up another system, which fits the Windows 7 with Ubuntu. To use Ubuntu for the Office(Excel of Windows), and for surfing/browsing. And Windows 7 for Gaming. Until Linux has Steam platform, i will Dual-Boot.


> **mifi said:**
> If the windows is not yet installed and you have enough memory installed, you might consider installing Ubuntu first and virtualbox next (virtualbox.org).
Then create a virtual machine in virtualbox and install windows in the virtual machine.

Given enough memory, you will have a machine that is running ubuntu and windows at the same time. Much more convenient than a multiboot setup where you have to reboot to switch OS.

But beware, the amount of memory in the machine must be sufficient to support both at the same time...

m
 
Hmmm i guess i will start off with Dual-Booting for now first, i wanna game on the Windows platform, if i were to virtual Machine it, it gonna lag like mad.(If i'm not wrong).

---

### Post by mifi on 2010-04-19
> **cayennurff said:**
> 
Hmmm i guess i will start off with Dual-Booting for now first, i wanna game on the Windows platform, if i were to virtual Machine it, it gonna lag like mad.(If i'm not wrong).
If you have good HW support for virtualisation, it will run at near native speed. If you do not have good HW support for it, do not use it.

Once windows is installed and activated, you can no longer install the same licence in a virtual machine. If you want a windows system virtualised, you would have to buy a new licence.

m

---

### Post by Swagman on 2010-04-19
ati card & linux usually means **Headaches**

Good luck though & welcome to Ubuntu Forums.

---

### Post by cayennurff on 2010-04-19
> **mifi said:**
> If you have good HW support for virtualisation, it  will run at near native speed. If you do not have good HW support for  it, do not use it.

Once windows is installed and activated, you can no longer install the  same licence in a virtual machine. If you want a windows system  virtualised, you would have to buy a new licence.

m

HW support, meaning ? The drivers?
Hmmm once you say this I'm quite tempted but my biggest worry is to run  both simultaneously. Means to run my game, i have to run Ubuntu, Virtual  Machine, Windows7 then Steam, then eg. TeamFortress2 to play. Btw the  Windows licence only can activate once?

> **Swagman said:**
> ati card & linux usually means **Headaches**

Good luck though & welcome to Ubuntu Forums.

I think its both sides, i've seen forums asking for nvidia drivers help. Guess i shall hope that it wouldn't give me headaches.

---

### Post by mifi on 2010-04-20
> **cayennurff said:**
> HW support, meaning ? The drivers?
Hmmm once you say this I'm quite tempted but my biggest worry is to run  both simultaneously. Means to run my game, i have to run Ubuntu, Virtual  Machine, Windows7 then Steam, then eg. TeamFortress2 to play. Btw the  Windows licence only can activate once?

No I do not mean drivers but Vt-x on Intel processors and the equivalent on AMD processors. This is the chip supporting virtualisation. Drivers are software.

And yes, a licence of windows allows you to install once. After activation it will be bound to the hardware you installed it on.

Looking at the questions you have, I doubt if virtualisation is the best option for you at this point in time. Perhaps after you gained some experience with Linux, you might be in a better position to judge if it is a feasible solution for your situation. You might be right in sticking to the multiboot setup.
I selected my PC hardware specifically on the possibility of running virtual machines.

m

---

### Post by Bucky Ball on 2010-04-20
Nvidia much better supported on Linux because Nvidia could be bothered. ATI slowly catching up. OS irrelevant to both as we all use graphics cards and that means money; ATI were perhaps woken up to the fact they could make a bit more by the many support, feedback and complaint emails from the open source community ... :-k

---

### Post by 3rdalbum on 2010-04-20
> **cayennurff said:**
> I am either going to use HD4850/ On-board graphics of the HD4200 by ATI. So is that program within linux or have to download separately?

Use the Hardware Drivers program to install the appropriate driver.

> btw motherboard drivers needed? those for USB, or are they within Linux?

You shouldn't need to worry about "motherboard drivers" (which are really just drivers for components on your motherboard). Why don't you just try booting up the Ubuntu CD and you'll see exactly what is working?

> Oh i'm actually thinking of setting up another system, which fits the Windows 7 with Ubuntu. To use Ubuntu for the Office(Excel of Windows), and for surfing/browsing. And Windows 7 for Gaming. Until Linux has Steam platform, i will Dual-Boot.
 
Hmmm i guess i will start off with Dual-Booting for now first, i wanna game on the Windows platform, if i were to virtual Machine it, it gonna lag like mad.(If i'm not wrong).

I don't know if you get worthwhile 3D acceleration in a virtual machine anyway. You should dual boot.

---

### Post by cayennurff on 2010-04-20
> **mifi said:**
> No I do not mean drivers but Vt-x on Intel processors and the equivalent on AMD processors. This is the chip supporting virtualisation. Drivers are software.

Looking at the questions you have, I doubt if virtualisation is the best option for you at this point in time. Perhaps after you gained some experience with Linux, you might be in a better position to judge if it is a feasible solution for your situation. You might be right in sticking to the multiboot setup.
I selected my PC hardware specifically on the possibility of running virtual machines.

m


> **Bucky Ball said:**
> Nvidia much better supported on Linux because  Nvidia could be bothered. ATI slowly catching up. OS irrelevant to both  as we all use graphics cards and that means money; ATI were perhaps  woken up to the fact they could make a bit more by the many support,  feedback and complaint emails from the open source community ... :-k

> **3rdalbum said:**
> Use the Hardware Drivers program to install the  appropriate driver.
 

:popcorn:Thanks everyone for the help on my questions on Ubuntu before my setup. I am going to wait for 10.04LTS, and give it a shot8-). If i ever come across any problems, i will come back to the forums to seek for help! 
**A BIG THANK YOU TO ALL.**:-D

---

