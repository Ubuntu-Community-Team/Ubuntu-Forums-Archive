---
title: "Wireless PCI card that works for older pc's"
date: 2011-08-05
forum: General Help
---

### Post by william_ia on 2011-08-05
Hi All,

I am looking for a reliable Wireless PCI card that could be installed and supported through the Ubuntu operating system. Has anyone had any success with this? What I am seeing so far online only supports Windows operating systems.

:popcorn:

---

### Post by desnaike on 2011-08-05
I use  Edimax ew 7727in pci card works out of the box but might be hard to find, on my new box having no pci slots I went with this [http://www.simplewifi.com/alfa-1000mw-with-white-cantenna.html](http://www.simplewifi.com/alfa-1000mw-with-white-cantenna.html) it does include the small antenna in the box it's usb and has worked with U/K/Xubuntu,Mepis,pclinuxos,opensuse,mandriva all out of the box. It's very conveniant because you can use it with more than 1 PC.

---

### Post by william_ia on 2011-08-05
Thanks desnaike, but I think I need to clarify myself better. We are looking to buy several of these and they have to be internal PCI cards so someone at a remote location can not walk up to one of these PC's and walk off with the Wireless card!

I know this is old school, but its what we have to work with!

---

### Post by walt.smith1960 on 2011-08-05
I'm not sure how up to date this is but:

[http://linuxwireless.org/en/users/Devices/PCI](http://linuxwireless.org/en/users/Devices/PCI)

Here's another:

[http://linux-wless.passys.nl/](http://linux-wless.passys.nl/)

And google will turn up yet more.  Once you see a card you like, you can google that model and search for the chip set used.  Chip set is really what matters.  Chipsets also change within a model #.  For example, Trendnet TEW424UB v2 used an SiS chipset which was difficult; Trendnet TEW424UB**v3** uses RealTek 8187b which is plug & play.  Some work as soon as they're connected, some work after activating a restricted driver and some are a royal PITA. You might spend some time skimming the networking & wireless forum here to get a feel for which ones are a problematic and which ones are plug & play.  My own experience is that RealTek 8187b is plug & play on everything since about 8.10 but it 802.11g.  Since 11.04 was released, Atheros Ath9k & RealTek 8192SU are plug & play -- they required add-ons prior to 11.04.  I'm using USB devices and don't know if that matters.

---

