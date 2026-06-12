---
title: "Dyndns"
date: 2009-08-07
forum: General Help
---

### Post by any.linux12 on 2009-08-07
Hi!

I need to install dyndns in my company and I already did the hostname part and it works fine. (the ip address has now a name)

But when I connect to that name I think that is pointing to the router. How can I point to a web site or other stuff like torrents?? how can I give dyndns my network range or my computers hostnames??

Thanks in advance

---

### Post by alarme on 2009-08-07
You must configure NAT in your router to redirect incoming call to the LAN server for this service (eg. redirect calls on port 80 to 192.168.1.15 for web server).  Also, maybe you need to open the port in the firewall of the router and in the firewall of the server.

---

### Post by any.linux12 on 2009-08-10
> **alarme said:**
> You must configure NAT in your router to redirect incoming call to the LAN server for this service (eg. redirect calls on port 80 to 192.168.1.15 for web server).  Also, maybe you need to open the port in the firewall of the router and in the firewall of the server.

Hey. I just saw your reply today and it works. Thanks :D

---

