---
title: "Advanced network Issue"
date: 2006-03-19
forum: General Help
---

### Post by eXidos on 2006-03-19
Recently I have been doing alot of work with networking, mainly installs, optimization, VPN's, and security however I'm still relativly new at this game so bear with me.

This is my network:


[img]http://www.useright.net/images/network.gif[/img]


I need to get the blue (EXBOX) computer on both networks but when I activate both connections I lose my ability to go on the web, the strange part is that I can still reach both the Smoothwall DHCP software by browser and the Linksys firmware also by browser. I have tried setting the wireless connection as the default but every time I close the networking window it defaults back to the wired network.

I'm at a loss this has to be possible. any suggestions? or perhaps a walkthrough?

---

### Post by cilynx on 2006-03-19
Your problem is that your wired network default route is taking over.  If you look at your routing table "route -n" I'm sure you'll see that your route to the outside world is being done through the wired network.  I don't know the pretty graphical way to fix it, but that's the problem.  "man route" is your friend.

---

### Post by eXidos on 2006-03-19
[img]http://www.useright.net/images/network_1.gif[/img]

---

### Post by cilynx on 2006-03-20
Ok, you've got two default routes (destination 0.0.0.0), that's not really a good thing.  Delete them with "route -del default".  You may have to run it twice.  Add a new default route after that with "route add default gw 192.168.x.x" such that the address is the address of the wireless card that goes out to the internet.

---

### Post by eXidos on 2006-03-20
got it great! thanx man.

---

