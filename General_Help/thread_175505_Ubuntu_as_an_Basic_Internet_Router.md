---
title: "Ubuntu as an Basic Internet Router"
date: 2006-05-13
forum: General Help
---

### Post by sav2880 on 2006-05-13
I've seen guides on how to set up more advanced Internet routing through Ubuntu using 3 NICs, but I want to do something more simple ... just a 2 NIC setup, one NIC as the WAN port, and one as a router port. 

I'm extremely new to the world of Linux in general, so even stuff as simple as knowing how to get root access and how to setup stuff to run on startup automatically. 

Also, the standard things you would have in a hardware router like port forwarding and virtual servers and DMZ are things I would need to know how to do. 

Is there any type of guide or guidance one could offer to get started on this? It would be a great opportunity for me to learn Ubuntu. :)

---

### Post by gibson on 2006-05-13
Have a look into iptables, that can do all the packet switching etc. You could also use squid as a proxy ang get it to cache, restrict webpages.

You may also be interested in the smoothwall project for something like this...

[http://www.smoothwall.org/](http://www.smoothwall.org/)

hope to help

---

### Post by jtibau on 2006-05-13
I think ubuntu is a great distro, however it is more desktop oriented.
There are a bunch of distros whose object is to set up a router-box...
Ubuntu will be up for the task though :D

---

### Post by jussishow on 2006-05-14
Check out the shorewall package  & homepage.
I use Shorewall to setup my Ubuntu box as an ADSL<->"home network" router/firewall/gateway ...

[http://www.shorewall.net/](http://www.shorewall.net/)

/J

---

