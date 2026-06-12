---
title: "Dns with static ip?"
date: 2011-01-24
forum: General Help
---

### Post by abhilashm86 on 2011-01-24
I made a setup of web server using Ubuntu 10.04 yesterday with a static ip and works fine!! I also installed shorewall firewall and allowed ports 80 and 22. 

In the router i opened port 80 and redirected to my ubuntu machine which had an static ip setup. 

I'm doing like this to access my Webserver, [http://122.xxx.xx.xx/appProduct](http://122.xxx.xx.xx/appProduct)  

Where appProduct is in /var/www and some php. 

I've a static ip, but i want to know how to place a domain name instead of  [http://122.xxx.xx.xx](http://122.xxx.xx.xx). Where exactly should i give a domain name?? 

I want like [http://mycompany.com/appProduct](http://mycompany.com/appProduct). To my little knowledge in network, i thought this should be a dns re direct?? 

Please tell all possibilities to use a domain name and it should redirect to my router static ip address. 
Thanks!!

---

### Post by LoneWolfJack on 2011-01-25
you can set up a DNS server with the berkeley internet name daemon (sudo apt-get install bind9), but it's usually not worth the effort. most companies that offer domain registration will offer DNS servers for a few cents a year.

so simply find a company that lets you edit your domain zonefile or at least provide a way to set the IP the domains need to be resolved to.

---

### Post by abhilashm86 on 2011-01-26
> **LoneWolfJack said:**
> you can set up a DNS server with the berkeley internet name daemon (sudo apt-get install bind9), but it's usually not worth the effort. most companies that offer domain registration will offer DNS servers for a few cents a year.


Thanks you jack for the easiest way of suggesting, i searched in my domain provider and found out that dns hosting is free!! and it works, so my webserver is on!! happy:p

---

