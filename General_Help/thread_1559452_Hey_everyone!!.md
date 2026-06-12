---
title: "Hey everyone!!"
date: 2010-08-23
forum: General Help
---

### Post by SpazyRantz on 2010-08-23
Hey guys. I'm kinda new to ubuntu. I mean, I've used it before, just not as my main opperating system. I'm not too familliar with installing programs and drivers, so I was wondering if I could get hand fro you guys? Is installing my packages offline as impossible as it seems? :confused:
 
-p.s. I'm running a 64-bit OS if that makes a difference.

---

### Post by mhgsys on 2010-08-23
Hello and welcome to the forums
; 
Installing packages offline is not a really big deal; in fact it's easy when you downloaded a .deb file.. and tar.gz files are not that hard either/.

Anyway; The easiest way for new users would be when online :the GUIway I guess.

You can find lot's of packages going to your panel and click 
[COLOR="Blue"]Applications> Ubuntu Software center[/COLOR]
Or 
[COLOR="Blue"]System>Administration> Synaptic Package Manager[/COLOR]

The easiest way to install drivers would be 
[COLOR="Blue"]System>Administration>Hardware Drivers[/COLOR]

---

### Post by SpazyRantz on 2010-08-23
Thanks! But here's the screwy thing, there's no available wireless networks around where I am, and the only computer that actually has internet access is my dads. Plugging the network cord into my computer just won't seem to work. so I'm stuck with a flash card as a connection between the two computers. Plus any tutorials I seem to follow don't help either T-T

---

### Post by mhgsys on 2010-08-23
Well in that case ; as a newbie at ubuntu your a bit in a pickle.

Go to [COLOR="Blue"]Applications> Accessories > Terminal[/COLOR]

You could try to manually find out what drivers you need by entering

```
lspci
``` in a terminal

```
lsusb
``` for usb devices (and some wireless lan card are recognized as a usb device)

These commands will show you the hardware devices on your system

You can use the output to search on internet for your drivers.

---

### Post by coolman98 on 2010-08-23
hi are you a kid me to I used to use a flash drive for this purpose.

---

