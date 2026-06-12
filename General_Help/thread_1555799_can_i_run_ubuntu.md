---
title: "can i run ubuntu?"
date: 2010-08-18
forum: General Help
---

### Post by jibby_1 on 2010-08-18
hi all, i recently got a laptop which is about six years old its a sony viao vgn-fs215b and it has xp on it which is really slow, so i decided to put ubuntu 10.04 on it seeing that i use ubuntu on my desktop, but i am unsure if i can run it the specs on the laptop are:

Pentium M 1.73 GHz
512 MB (DDR SDRAM)
Intel Graphics Media Accelerator (GMA) 900
Display Max. Resolution                       1280 x 800

---

### Post by Spice Weasel on 2010-08-18
Definitely it will run, but might be a bit slow. You might want to look in to Lubuntu or Crunchbang. Those two will run like a dream on that sort of hardware.

---

### Post by jibby_1 on 2010-08-18
i was thinking of xubuntu or kubuntu but again i cant find specs and the main reasons for moving from windows is that i wanna to be able to watch movies and use the internet without it crashing all the time

---

### Post by stefangr1 on 2010-08-18
No it won't be slow. You're well above the minimum that would be required for a workable system. Make sure to allocate enough swap space.

Also, I wouldn't recommend installing Xubuntu (or Lubuntu or Crunchbang) just because of system resources. Your system will just be proportionally slower than a modern system: if firefox needs 1 second to start on a modern system, it'll take 2 seconds on yours. On my PIII with 256mb RAM its still proportionally, takes about 4 seconds (though I have 9.10 there). You usually don't see the negative experience you sometimes have with windows, where the system can get extremely sluggish sometimes on older hardware.

---

### Post by kbless7 on 2010-08-18
Any of the mentioned linux distributions will be less taxing on your system resources than XP. I believe you won't have a problem surfing the web or watching movies without crashing.

---

### Post by uRock on 2010-08-18
> **jibby_1 said:**
> i was thinking of xubuntu or kubuntu but again i cant find specs and the main reasons for moving from windows is that i wanna to be able to watch movies and use the internet without it crashing all the time
I run Ubuntu 32bit in a vbox with 512MB RAM and it runs great. And yes, I do use it for watching youtube and such, being flash in 64bit is so crappy.

---

### Post by jibby_1 on 2010-08-18
will any of the above OS's that have been mentioned automatically pick up on the onboard  wireless card

---

### Post by Spice Weasel on 2010-08-18
> **jibby_1 said:**
> will any of the above OS's that have been mentioned automatically pick up on the onboard  wireless card
It depends, best to try them out.

---

### Post by Vrroom on 2010-08-18
Of course you can....Xubuntu or Lubuntu will be good choice too as they are lightweight and works nice on old hardware.

---

### Post by uRock on 2010-08-18
> **jibby_1 said:**
> will any of the above OS's that have been mentioned automatically pick up on the onboard  wireless card
I would test the LiveCD and see if that works. If you post the make and model of the wireless NIC, then someone may be able to say yes or no.

---

### Post by uRock on 2010-08-18
> **Vrroom said:**
> Of course you can....Xubuntu or Lubuntu will be good choice too as they are lightweight and works nice on old hardware.
Xubuntu is no lighter than Ubuntu and Lubuntu is still very buggy do to the small amount of devs supporting it.

---

### Post by jibby_1 on 2010-08-18
the wireless card is a: Intel(R) PRO/Wireless 2200BG

---

### Post by desnaike on 2010-08-18
I have a Sony Vaio PCG-V505BX 2 ghz P4 512 ram Ubuntu/Xubuntu 9.04,9.10 Lmint7,8 all run well even able to use limited visual effects. Ubuntu 10.04 ran a little sloww in comparison.

---

### Post by jibby_1 on 2010-08-18
> **desnaike said:**
> I have a Sony Vaio PCG-V505BX 2 ghz P4 512 ram Ubuntu/Xubuntu 9.04,9.10 Lmint7,8 all run well even able to use limited visual effects. Ubuntu 10.04 ran a little sloww in comparison.

yh i was thinking of that i have a old 9.04 cd, no ones really mention kubuntu do you think that will be a more lighter choice.

---

### Post by dado2000 on 2010-08-18
It will run. but will be very slow. I have similar configuration: Pentium 4, 1 GB RAM, GeForce graphic Card 512 MB GDDR2. I installed Ubuntu 10.04, in the beginning it was very slow, I figure out when I change the default desktop theme from Ambience to Clearlooks, Ubuntu become more faster, also I changed swapping from 60 to 10,  which means, instead of swapping the memory content to disk (which is 100 time slower than main memory) all the time, it will keep the memory content in most of the time.

I recommend you to read this post [http://ubuntuforums.org/showpost.php?p=1255511&postcount=43](http://ubuntuforums.org/showpost.php?p=1255511&postcount=43) and follow the instructions):P

---

### Post by jibby_1 on 2010-08-18
yh i am going to go head and try 9.04, also if someone can tell me if my wireless card is supported, thanks

---

### Post by Cilph on 2010-08-18
I would say Kubuntu is more taxing than Ubuntu because of the eyecandy KDE4 seems to be focussing on. I'd suggest for you to use Xubuntu because of how light, easy and stable it is.

All these *ubuntu names coming by are just forks of Ubuntu with a different desktop environment. It is still very much the same OS.

Ubuntu - GNOME
Kubuntu - KDE
Xubuntu - XFCE
Lubuntu - LXDE
Crunchbang - Openbox

As for the wireless card, I can't check it at the moment but Intel wireless should work (If not, there's always ndiswrapper) There is also no point in installing 9.04 instead of 10.04, especially with 10.04 being an LTS.

---

