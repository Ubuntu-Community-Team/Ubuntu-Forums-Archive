---
title: "Questions about running my own DNS for routing subdomains"
date: 2009-07-01
forum: General Help
---

### Post by ejcdke on 2009-07-01
I have a domain (we’ll call it domain.com) that points to my router with a dynamic WAN IP.  I’m using ZoneEdit for dynamic DNS duties to link the domain to my ever changing IP.  I have a server running Ubuntu Server 8.04 attached to the router with a subdomain of main.domain.com, which runs OpenVZ and three virtual environments.  I gave each virtual environment a subdomain of vz1.domain.com, vz2.domain.com, and vz3.domain.com.  I have traffic properly routing inside my LAN to each subdomain.  So if I’m on my LAN and using my laptop, I can ssh into vz2.domain.com, no problem.  If I FTP to main.domain.com, no problem.  Ports are properly configured and traffic flows as it should.  

However, when I’m outside my LAN, traffic always ends up at the domain.com (the router) regardless of the subdomain I use.  The router doesn’t seem to know to send the traffic to the server or the virtual environments based on the subdomain.  Is there any way in DNSMasq to have the WAN traffic properly route to the right subdomains (I’m using DNSMasq on my ddWRT Linksys WRT54GL router)?  I can ssh into the router and go beyond the web gui if necessary.  If this is not possible in DNSMasq, what if I setup my own nameserver using BIND on my Ubuntu Server box?  I'm actually thinking of just going with BIND on my server, which is why I posted here, but I don't know if this is even possible without getting a block of WAN IP addresses.  I’m starting to get in over my head and am hoping someone can steer me in the right direction.  Thanks.

---

