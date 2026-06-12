---
title: "Wireless-G USB Adapter Not Working (sortof?)"
date: 2010-08-07
forum: General Help
---

### Post by user1397 on 2010-08-07
So I bought a linksys wireless-g usb adapter for my desktop because I don't want an ethernet cable running halfway around my house to the router (the router can't move from that location).

it comes with a windows setup disc which i obviously can't use in linux so i just plugged it in and hoped for the best.

It seems to turn on, the little light flashes, and I tried connecting to my wireless network in the network manager (using 10.04, gnome), but it just seems to be retrying to connect and every 5 minutes it asks me for the password which I've given it already.

Any one experience something similar?

---

### Post by user1397 on 2010-08-08
bump

---

### Post by ubunterooster on 2010-08-08
I have had similar experiences but the result depends on the exact router; which do you have?

---

### Post by user1397 on 2010-08-08
> **ubunterooster said:**
> I have had similar experiences but the result depends on the exact router; which do you have?

my router is the linksys WRTU54G, but i don't think that's the problem, my ubuntu lucid netbook hooks up to it just fine, but what do i know. :(

---

### Post by ubunterooster on 2010-08-08
Oh, wait, sorry. I need the USB adapter number.

Well actually just post it here and someone else will likely carry on. I'm beat for tonight.

---

### Post by user1397 on 2010-08-08
> **ubunterooster said:**
> Oh, wait, sorry. I need the USB adapter number.

Well actually just post it here and someone else will likely carry on. I'm beat for tonight.
Oh, its WUSB54GC, and thanks for helping out.  it is getting pretty late, i feel ya

---

### Post by cavalier911 on 2010-08-08
Your router has security turned on,the computers wireless adapter see's the router, you enter in the passphrase. The association times out and your prompted to re-enter the passphrase. Have you tried connecting with the router security turned off aka open ? Unplug router from the internet while you test if thats a concern.The test would be to get associated with the router,get assigned an ip address and successfully ping the routers lan side a.k.a. gateway address.There is a lucid bug report with some wireless drivers having a problem with wpa supplicant that causes similar timeout prompt for passphrase issue your having. If you can connect with wireless security off I would try ndiswrapper.
Run lsusb in terminal, post the identity of the wireless adapters chipset.

---

### Post by Theft42 on 2010-08-08
Have you tried ndiswrapper? It may help until you can find a better solution :D

---

### Post by user1397 on 2010-08-08
> **cavalier911 said:**
> Your router has security turned on,the computers wireless adapter see's the router, you enter in the passphrase. The association times out and your prompted to re-enter the passphrase. Have you tried connecting with the router security turned off aka open ? Unplug router from the internet while you test if thats a concern.The test would be to get associated with the router,get assigned an ip address and successfully ping the routers lan side a.k.a. gateway address.There is a lucid bug report with some wireless drivers having a problem with wpa supplicant that causes similar timeout prompt for passphrase issue your having. If you can connect with wireless security off I would try ndiswrapper.
Run lsusb in terminal, post the identity of the wireless adapters chipset.
k i'm gonna try that, in the meantime here's what lsusb says:

Bus 001 Device 003: ID 1737:0077 Linksys

---

### Post by user1397 on 2010-08-08
After doing what it says in the first post of this thread: [http://ubuntuforums.org/showthread.php?t=1464255](http://ubuntuforums.org/showthread.php?t=1464255) , I could actually see my network SSID and others around me for the first time.

So I tried connecting to the router without wireless security and it worked, however wireless security is necessary.  When I enable security (WPA2) it will just keep trying to connect but never fully do it.

Thoughts?

---

### Post by user1397 on 2010-08-09
bump

---

### Post by user1397 on 2010-08-11
should I just use ndiswrapper? I've never used it before, is there a good guide anyone know of? (specifically for this hardware preferably)

---

### Post by user1397 on 2010-08-14
So looking through a bunch of guides and whatnot, I came to the conclusion that all I needed to do was blacklist the rt2800usb module and use WPA1 encryption and it works.  Every time I turn on my copmuter and I log in, it asks for my user password again once I'm logged in fully, which is a slight annoyance but less annoying than having a cable run through the house.  WPA2 DOES NOT WORK (yet) for this specific adapter.

So yea, I didn't have to do ndiswrapper or anything.

---

