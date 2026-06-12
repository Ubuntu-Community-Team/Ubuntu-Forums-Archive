---
title: "Setting up Proxy"
date: 2011-08-22
forum: General Help
---

### Post by inuyash274 on 2011-08-22
Alright. I was talking with my uncle the other day about my linux setup. my computer is running Ubuntu 11.04 only right now. recently i installed LAMP on my computer because i am a web developer and need a place where i can read and write PHP among other things. The only problem is that i do not have a constant IP address for mysql to use because i usually just leech off of other peoples wifi in thus, i never have the same ip address.

now my question is, is there a way to get up with proxy so that i can constantly have the same ip address being out put? but accept Internet connections from different ones coming in?

---

### Post by stefangr1 on 2011-08-22
> **inuyash274 said:**
> Alright. I was talking with my uncle the other day about my linux setup. my computer is running Ubuntu 11.04 only right now. recently i installed LAMP on my computer because i am a web developer and need a place where i can read and write PHP among other things. The only problem is that i do not have a constant IP address for mysql to use because i usually just leech off of other peoples wifi in thus, i never have the same ip address.

now my question is, is there a way to get up with proxy so that i can constantly have the same ip address being out put? but accept Internet connections from different ones coming in?

You could use a dynamic dns service for this purpose.

This way you still have a dynamic IP (not much you can do about that except for chaning to another ISP), but your current IP is continuously forwarded to the dns server such that your domain name resolves correctly.

---

### Post by inuyash274 on 2011-08-23
ok, i tried setting this up with [www.dyndns.com](www.dyndns.com) but i had to pay money before i could do anything... is there a free way to do this?

---

### Post by thefasterblueone on 2011-08-23
These two are very popular and free.

[DynDNS](http://dyn.com/dns/dyndns-free/)

[No-ip](http://www.no-ip.com/services/managed_dns/free_dynamic_dns.html)

---

### Post by inuyash274 on 2011-08-23
okay... now how would i go about setting this all up with dyndns?

---

### Post by mikaelcrocker on 2011-11-22
As for registering a domain name, or most of the services DynDns provides, I'm quite sure you have to pay.  The company I work for we pay for DynDNS.

Typically using a service for domain names is going to be expensive since you have to register it.

---

