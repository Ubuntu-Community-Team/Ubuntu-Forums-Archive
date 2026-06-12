---
title: "wireless troubles!"
date: 2006-03-12
forum: General Help
---

### Post by newbdude on 2006-03-12
Ok, I got a little further this time. I loaded ndiswrapper 1.1, my windows xp drivers from the cd (the wiki said that they'd work), and got all the wap to enabling my card with "sudo modprobe ndiswrapper". It appears to load the driver, but:

The lights on my card dont come on
and in dmesg it shows ndis loading, but no drivers!

Im going to try the drivers from the inet next, along with the "alternate" drivers.

PC specs:
Dell Inspiron 3500 Laptop
400 mhz, 126 ram
Airlink 101 AWLC 3025 Wireless 802.11g PCMCIA card
connecting to an Airlink 101 wireless g router with wep encription.
I dont have a hard wire lan connection on the laptop, so doing a apt-get or something wont work.

Thanks in advance!

---

### Post by Henry Rayker on 2006-03-12
HEY! this sounds exactly like the problem I'm currently having...same card, too...well, the same brand, but the 5025...which archtecture is it built on? the rt2600/rt61/whatever else they might call it?

My card's lights don't come on either, but I actually got a driver loaded one time...but the laptop doesn't recognize that the hardware is plugged in...

Maybe the airlink 101 cards just don't work...

---

### Post by newbdude on 2006-03-12
Yay Im not alone! Your card isn't on the wiki site though. Its at [http://ndiswrapper.sourceforge.net/mediawiki/index.php/List#A](http://ndiswrapper.sourceforge.net/mediawiki/index.php/List#A)

mines there, and the guy said that it worked fine with the cd drivers. Humph!
Im not sure what you mean by the architecture, but if its the chipset, then its the TI something something. I honestly forget! If you get and further with yours, let me know, and I'll do vice versa if I find out.

Thanks!

---

### Post by Henry Rayker on 2006-03-12
Sorry, I did mean chipset...we're on a different chipset, but the same manufacturer.

---

