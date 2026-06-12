---
title: "Squid with OPENDNS"
date: 2012-02-28
forum: General Help
---

### Post by iraqsoul on 2012-02-28
Dear all,

I have a small network here in IRAQ. I have squid cache server with Mikrotik router for users and Mikrotik router for schools. 

My problem is i need to use OPENDNS for schools Router and Google DNS for the users Router.

Please any one can help me to solve this problem. i want to set two access list in the squid, one use OPENDNS and the other use Google DNS.

School Router 95.170.210.80
Users Router 95.170.210.81
Google DNS 8.8.8.8
OPENDNS 208.67.222.222 208.67.220.220

Thanks

---

### Post by SeijiSensei on 2012-02-28
Squid will use the DNS servers that its host computer uses. So on the machine with the school's proxy, you'd configure /etc/resolv.conf to use the OpenDNS servers.  Similarly you'd put the Google DNS server addresses in /etc/resolv.conf on the machine hosting the users' proxy.

If you are using DHCP to get the machines' addresses and IP configuration, you'll have to disable the requests for the DNS server information, or simply use static IP addressing entirely.  I'd go with the latter myself so you don't have to worry about the DHCP client overwriting your resolv.conf files.

---

### Post by iraqsoul on 2012-02-28
thank you for your reply

you mean that i must delete any DNS in the squid server 
and depend on the DNS in the routers?

i have this connection for My network

Internet-----Cisco router with WCCP2 ---- Squid server
. . . . . . . . . . . . . . . I
. . . . . . . . . . . . . . . I
. . . . . . . . . . . . . . My Routers
. . . . . . . . . . . . . . . I 
. . . . . . . . . . . . . . . I
. . . . . . . . . . . . . . Networks

There is DNS in the Cisco router too
when enable OpenDNS on the squid cache, all networks will use openDNS and i dont want this
i want only schools router to use openDNS
Thanks

---

### Post by SeijiSensei on 2012-02-29
I read your initial posting as saying there would be two Squid proxies.  There's no way to do what you want with only one proxy.

Are the "users" and "schools" on different IP subnets?  I'd start with that first.  In this model, all the users connect to one router and all the schools connect to the other.  Both of these routers feed into the Cisco.

On each network I would put a Squid proxy between the subnet router and the Cisco.  On the box handling the users' proxy, I'd enter the Google IP addresses in /etc/resolv.conf.  On the schools' proxy, I'd enter the OpenDNS entries in the same file.

Regardless of where else DNS might be advertised, the Linux boxes are going to use the servers listed in /etc/resolv.conf.  

So I'd have a setup like this

[schools network]->[schools router]->[schools' squid proxy server]->Cisco
[users network]->[users router]->[users' squid proxy server]->Cisco

This model has the appeal of letting you run the proxies in "[transparent]("http://www.google.com/search?q=squid+3+transparent")" mode so you can avoid entering the proxy information manually in each client browser.

---

### Post by iraqsoul on 2012-02-29
so i cant filter schools
thank you for your advise
best regards

---

