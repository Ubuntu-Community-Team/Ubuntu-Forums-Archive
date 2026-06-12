---
title: "Open and proprietary graphical driver problems"
date: 2011-09-23
forum: General Help
---

### Post by Xenoty on 2011-09-23
Hello,

I have recently installed ubuntu on my new laptop and i have some problems with graphical drivers,

If i use the property driver, the computer starts well but the interface is quite buggy; Eyecandys like screenlets are not refreshing well (a sort of black/white mix) and the 3D games like urbanterror,flightgear, guildwars (by wine) don't work at all !

If i remove this bad property driver, everything is working fine except the boot and the "restart" after a suspend. My computer boot but on a blank screen and i'm force to hard reboot it. hapily it boot maybe one out of five (or by changing the start command (nomodetest). but these solutions is not good for hardware (hard-reboot) and it's a huge waste of time or the nomodetest resolution is horrible.

What can i do to fix it ?




Config

Ubuntu 11.04 with the gnome
AMD Radeon HD 6770
[SIZE=1](HP Pavilion dv6-6190sf[/SIZE])[SIZE=1]
[/SIZE]                     
Thanks :)
Please apologize for languages mistakes (English is not my mother language)

---

### Post by Xenoty on 2011-10-01
UP please

I'm searching but i don't find anything :(

---

### Post by coffeecat on 2011-10-01
I have no experience of that particular ATI graphics card, but I see it is a quite new one. According to this site:

[http://en.wikipedia.org/wiki/Comparison_of_ATI_Graphics_Processing_Units#IGP_.28HD_6xxx.29](http://en.wikipedia.org/wiki/Comparison_of_ATI_Graphics_Processing_Units#IGP_.28HD_6xxx.29)

It was released on the market at nearly the same time as Ubuntu 11.04 was released. Unfortunately, it takes a few weeks or months for Linux drivers for the very latest graphics cards to be released. I doubt whether you will ever get good graphics performance with a default installation of 11.04 or with the proprietary driver that you can install with Additional Drivers.

I suggest one of two things. You could enable a ppa repository so that you can install the newest ATI driver and a later version of the X-server. Or, you could try the 11.10 version of Ubuntu which is due to be released in less than two weeks. With newer drivers and a newer version of the X-server, you might have better performance.

Do you need any more information about either of those options?

---

