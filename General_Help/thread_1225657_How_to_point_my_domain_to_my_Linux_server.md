---
title: "How to point my domain to my Linux server?"
date: 2009-07-28
forum: General Help
---

### Post by CaptSaltyJack on 2009-07-28
I just got a nice boost on my upstream rate (2Mbps) and I'd like to purchase a domain and have it point to my Linux server at home, so I can run a web server, mail server, etc. Once I buy the domain, how exactly do I set it up so going to (for example) myfunkyserver.com goes to my Linux machine?

PS, I already use DynDNS which is nice, but it would be even nicer to have my own domain if possible.

---

### Post by zzzBrett on 2009-07-28
> **CaptSaltyJack said:**
> I just got a nice boost on my upstream rate (2Mbps) and I'd like to purchase a domain and have it point to my Linux server at home, so I can run a web server, mail server, etc. Once I buy the domain, how exactly do I set it up so going to (for example) myfunkyserver.com goes to my Linux machine?

PS, I already use DynDNS which is nice, but it would be even nicer to have my own domain if possible.

Use Godaddy ([www.godaddy.com](www.godaddy.com)) to purchase a domain name.  Then, you will have to specify some nameservers to have to domain point to.  If DynDNS supports this, i'm sure they will have some kind of name servers like ns1.dyndns.org through ns4.  If they don't support this, try using freedns.afraid.org.

---

### Post by credobyte on 2009-07-28
The best choice would be to use [bind9]("http://news.softpedia.com/news/How-to-Host-Your-Own-Domain-With-Bind9-on-Ubuntu-49585.shtml") ( your own DNS server ) !

---

### Post by philcamlin on 2009-07-28
id go with godaddy.com

---

### Post by hamstersquasher on 2009-07-28
You can register a domain name like xyz.com and then using your registrar, set up a URL redirect to a free dyndns domain name like xyz.dyndns.com.  That way you can work around the fact that you probably have a dynamic IP from your ISP.  You can also perform a blind URL redirect so that the address bar always shows xyz.com even though the user gets redirected to xyz.dyndns.com.  It just looks a litle bit more professional that way.  If you go with dyndns.com or another dynamic DNS provider, make sure you have some sort of client piece that monitors changes in your outside IP address from your ISP and updates your dynamic DNS account.

---

### Post by CaptSaltyJack on 2009-07-28
> **hamstersquasher said:**
> You can register a domain name like xyz.com and then using your registrar, set up a URL redirect to a free dyndns domain name like xyz.dyndns.com.  That way you can work around the fact that you probably have a dynamic IP from your ISP.  You can also perform a blind URL redirect so that the address bar always shows xyz.com even though the user gets redirected to xyz.dyndns.com.  It just looks a litle bit more professional that way.  If you go with dyndns.com or another dynamic DNS provider, make sure you have some sort of client piece that monitors changes in your outside IP address from your ISP and updates your dynamic DNS account.

Thanks, this is exactly what I was looking for. I'm happy with NameCheap for my registrar so I'll use their dynamic DNS service and see how that works out.

---

