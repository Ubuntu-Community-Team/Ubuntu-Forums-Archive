---
title: "Netgare problem"
date: 2006-05-29
forum: General Help
---

### Post by SwaroopKunduru on 2006-05-29
Friends,

I have a dell laptop. I have installed UBUNTU5.10 on it with dual boot XP. My laptop connects to internet with Netgare wireless external card. I installed Netgare driver for windows and it works fine on windows. But I don't have a linux driver. So I cannot able to install a driver and hence I could not able to connect to net. Please help me in this regards,

Thanks in advance.

Regards,

Swaroop Kunduru.
](*,)

---

### Post by H.E. Pennypacker on 2006-05-30
As you said yourself, you need the driver, but before we can find the driver, we'll need to know what your wireless card chipset is.  If you are using Ubuntu, start it.  Go to the terminal, and type in:

lspci

That will tell you what you're using, but you'll see a whole bunch of lines.  You need to find the name of your card's chipset (not the name that is one the card, but the name of the card itself - some manufacturer's don't use the actual name of the card).  For me, when I type in the above command, this shows:

> 02:03:0 14e4:4318 Broadcom AirForce One 54G

That tells me which card I am using ( Broadcom Airforce One 54G 4318 ).

Now we know the driver chipset, we're going to find the drivers.  Go to:

[http://ndiswrapper.sourceforge.net/mediawiki/index.php/List](http://ndiswrapper.sourceforge.net/mediawiki/index.php/List)

There, type CTRL-F to use the find window, and type in your card's name.  Once you locate the card's name, find the driver that others added.  For me, I find this:
> 
Card Name: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)

    * Ndiswrapper version: 1.1-4
    * Chipset name: Broadcom BCM4318
    * PCIID: 02:03.0 (rev 02)
    * Windows driver location: [http://biginoz.free.fr/linux/bcmwl5a.inf](http://biginoz.free.fr/linux/bcmwl5a.inf). Also need .sys file [http://biginoz.free.fr/linux/bcmwl5.sys](http://biginoz.free.fr/linux/bcmwl5.sys)
    * Using Ubuntu 5.10 on Dell Inspiron 1300 


I now see my card's name, and where I can find the driver ([http://biginoz.free.fr/linux/bcmwl5a.inf)](http://biginoz.free.fr/linux/bcmwl5a.inf)).  Sometimes, if you are lucky, Ubuntu already comes with the driver you need.  If that is the case, it's only a matter of setting things up.  

There you have it...complete these steps by following [the Ubuntu Wiki]("http://wiki.ubuntu.com/").

---

