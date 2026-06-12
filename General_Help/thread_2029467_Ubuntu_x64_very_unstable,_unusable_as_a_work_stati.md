---
title: "Ubuntu x64 very unstable, unusable as a work station"
date: 2012-07-19
forum: General Help
---

### Post by ivanonano on 2012-07-19
Hi 

I decided to try and move all together to Ubuntu after dual booting on my old computer for some years. I heard of improvements in stability etc but it hasn't been 4 hours since I installed ubuntu into my newly build desktop and I already had five freezes where I had to force power off the machine. 

Other then the latest standard Ubuntu installation I installed java and flash support, and the Chromium browser, nothing else.

I like listening to online radio while I work, web browsing etc, but nothing special. 

I am using a very powerful computer, 32G RAM, Core i7, SSD. 

Please help me find a reason not to go back to Windows 7 because this is far from stable and cannot be used as a workstation, to have it freeze in the middle of something would be disaster. Any tips, am I missing something here or has this OS really gotten that bad?

---

### Post by Paqman on 2012-07-19
I can only assume something went badly wrong with the install. Can you try running from the CD or USB for a bit and see if you get the same lockups? And can you post your hardware specs in a bit more detail? You may have something in there that's not well supported.

PS: 32GB RAM? Wow, what do you use all that for?

---

### Post by ivanonano on 2012-07-19
Hi Paqman

Thanks for the reply. 

I am not 100% but it seems like the problem comes after the system has shut down the monitors (not gone to sleep but just sleeping the monitors); I get the feeling this is something to do with Java or Flash but I may be wrong. The system was set up as a trading desk to connect to 6 monitors and display graphs and quotes in realtime in several windows while having a live TV feed and news feed running together with email, some complex spreadsheets and web browsing hence the 32G RAM, it was sold as a package from corsair not much more then getting the 16 so value for $ went for the 32G as it should last a while. But so far is not running a web browser with online radio connected to one monitor ;) so as of now a raspberry pi would probably perform better!. Hopefully will get there eventually with all your help. Description of the hardware below:
Motherboard: P8Z77-V Deluxe
SSD: OCZ 120GB
RAM: 32G Corsair 
Processor: Core i7 3770 1.6GHz

---

### Post by idoitprone on 2012-07-19
> **ivanonano said:**
> Hi Paqman

Thanks for the reply. 

I am not 100% but it seems like the problem comes after the system has shut down the monitors (not gone to sleep but just sleeping the monitors); I get the feeling this is something to do with Java or Flash but I may be wrong. The system was set up as a trading desk to connect to 6 monitors and display graphs and quotes in realtime in several windows while having a live TV feed and news feed running together with email, some complex spreadsheets and web browsing hence the 32G RAM, it was sold as a package from corsair not much more then getting the 16 so value for $ went for the 32G as it should last a while. But so far is not running a web browser with online radio connected to one monitor ;) so as of now a raspberry pi would probably perform better!. Hopefully will get there eventually with all your help. Description of the hardware below:
Motherboard: P8Z77-V Deluxe
SSD: OCZ 120GB
RAM: 32G Corsair 
Processor: Core i7 3770 1.6GHz

hmmm a very new system

```
uname -a
```

I guessing you are using precise

[http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.4-precise/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.4-precise/)

download the kernel amd 64 and the header.

Install it 

reboot to try

i am guessing the precise kernel does not support your chip too well

---

### Post by jmfal on 2012-07-19
Check your swap 
its probably to big 
if you have it set to 1/2 your ram then everything has to stop while 16gb are loaded to hdd

---

### Post by efflandt on 2012-07-19
If he has 32 GB RAM he would not even need swap unless he wants to hibernate, and then swap would need to be at least as large as RAM.

I don't have any swap on my 8 GB desktop because I do not hibernate it.  It cold boots faster from SSD than it wakes from suspend and I imagine waking from hibernation would take longer than waking from suspend.

What sort of video does it have capable of 6 monitors?  Have you looked through /var/log/syslog for any errors when you have issues?

---

### Post by mastablasta on 2012-07-20
yup it could be the video card/drivers that don't support linux well. well many things to be looked at firts to see where the problem is that is causing the freeze.

---

### Post by idoitprone on 2012-07-20
> **efflandt said:**
> If he has 32 GB RAM he would not even need swap unless he wants to hibernate, and then swap would need to be at least as large as RAM.

I don't have any swap on my 8 GB desktop because I do not hibernate it.  It cold boots faster from SSD than it wakes from suspend and I imagine waking from hibernation would take longer than waking from suspend.

What sort of video does it have capable of 6 monitors?  Have you looked through /var/log/syslog for any errors when you have issues?

well, the linux might be accessing swap although there is plenty of room in ram. 

He should change the swappiness to 0, so linux will not try to swap out sleeping processes unless it needs to

[https://help.ubuntu.com/community/SwapFaq/#What_is_swappiness_and_how_do_I_change_it.3F](https://help.ubuntu.com/community/SwapFaq/#What_is_swappiness_and_how_do_I_change_it.3F)

---

### Post by 3Miro on 2012-07-20
Video is the usual suspect when it comes to Linux crashes, please provide info on which card you are using. If Java or Flash is trying to use 2D acceleration and the driver is bad, this will probably crash the system.

In your case, the other possibility is that the UEFI doesn't like Linux. See if there is newer version of your Motherboard BIOS and update it (note that updating the BIOS is a very tricky thing and can permanently damage your system, don't do it unless you know what you are doing).

---

### Post by idoitprone on 2012-07-20
> **3Miro said:**
> Video is the usual suspect when it comes to Linux crashes, please provide info on which card you are using. If Java or Flash is trying to use 2D acceleration and the driver is bad, this will probably crash the system.

In your case, the other possibility is that the UEFI doesn't like Linux. See if there is newer version of your Motherboard BIOS and update it (note that updating the BIOS is a very tricky thing and can permanently damage your system, don't do it unless you know what you are doing).

he sort of already did.

He has the newest i7 3770 which has intel hd 4000

His chipset is not properly supported by stock ubuntu kernel.
[http://partiallysanedeveloper.blogspot.ca/2012/05/ivy-bridge-hd4000-linux-freeze.html](http://partiallysanedeveloper.blogspot.ca/2012/05/ivy-bridge-hd4000-linux-freeze.html)
People have reported complaints of stability problem that is fixed on the later kernels

The most sane route to find a solution is to upgrade his kernel 
[http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.4-precise/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.4-precise/)
here is the link to precise 3.4 kernel

---

### Post by 3Miro on 2012-07-20
> **idoitprone said:**
> he sort of already did.

He has the newest i7 3770 which has intel hd 4000

The motherboard will have a PCI-E sloth, so he could be running a dedicated graphics card. I wanted to double-check.

> 
His chipset is not properly supported by stock ubuntu kernel.
[http://partiallysanedeveloper.blogspot.ca/2012/05/ivy-bridge-hd4000-linux-freeze.html](http://partiallysanedeveloper.blogspot.ca/2012/05/ivy-bridge-hd4000-linux-freeze.html)
People have reported complaints of stability problem that is fixed on the later kernels

The most sane route to find a solution is to upgrade his kernel 
[http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.4-precise/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.4-precise/)
here is the link to precise 3.4 kernel

Update the kernel or update the BIOS, hopefully one of those will fix the problem. Updating the kernel is indeed easier.

---

### Post by ivanonano on 2012-07-20
Thanks for all the input! Actually I left the videocard out of the system to make sure all was working first in case something like this happened, so just using the graphics built in the MoB.

After hours of testing it seems what is causing the crash is having the tunein online radio open in the browser. I think it's java.

---

### Post by pqwoerituytrueiwoq on 2012-07-20
using icedtea/openjdk or sun java
you could try switching to the other one

---

