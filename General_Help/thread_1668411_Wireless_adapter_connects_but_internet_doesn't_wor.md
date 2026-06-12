---
title: "Wireless adapter connects but internet doesn't work"
date: 2011-01-16
forum: General Help
---

### Post by DOSIX on 2011-01-16
My wireless adapter connects to my WPA2 network perfectly, but when I run firefox it says it can't load the webpage, no matter what page I go to. Also, downloading new software doesn't work either. Any ideas please?

---

### Post by DOSIX on 2011-01-17
anybody???

---

### Post by lithopsian on 2011-01-17
Login to your router and see what it thinks.  Maybe your firewall is just blocking everything.  Ping some sites and see if the most basic IP gets through to the outside world.  Try IPs instead of domain names in case it is DNS that isn't working.

---

### Post by Krazie_kid on 2011-01-17
I would log into your router and make sure that it is not blocking any computer to access anything. That is most likely what the problem is.

---

### Post by DOSIX on 2011-01-17
i don't think it's the router because the internet on my windows partition is working fine and my dad's laptop which i'm using now is working fine too (this is a windows partition but i'm using ubuntu on vmware).

---

### Post by ctult on 2011-01-17
Did you try going into System>Administration>Additional Drivers?

---

### Post by ctult on 2011-01-17
Did you try going into System>Administration>Additional Drivers?

---

### Post by DOSIX on 2011-01-17
there is no entry for additional drivers under administration. i checked the entry for hardware drivers and it said there were no proprietary drivers in use. it shoudln't be a driver problem since i already have the right drivers installed and i'm connected to the network.

---

### Post by yeklef on 2011-01-17
How do you know it connects to your network perfectly?  When I first got Ubuntu, my computer would see the network, but wouldn't actually connect until I went through a bunch of set up steps.  Some more information might be useful as well, like what kind of wireless card you have?  (and any other info you think might be useful.  You are kind of sparse right now.)

And if in your last post you meant that the windows side of a dual boot has the drivers, that doesn't mean the Ubuntu side will have them as well.  You might have to install it in both (i did).  If that isn't what you meant, ignore this sentence :P

---

### Post by DOSIX on 2011-01-18
it connects to the network perfectly because network manager shows that it's connected and when i traceroute it shows that it connects to the router. i have a linksys wireless usb adapter (chipset rt2870) and the rt2870sta driver installed. with windows, i can connect to the network, open firefox, and use facebook or whatever. in ubuntu, i connect to the network, but i open firefox and it says there's no internet.

---

### Post by DOSIX on 2011-01-18
thanks to everyone that has tried to help me with this problem. i fixed it by upgrading to ubuntu 10.10. internet is all fine now. thanks again.

---

