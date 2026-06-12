---
title: "DNS self-hosting: how to bootstrap?"
date: 2012-02-21
forum: General Help
---

### Post by minsf on 2012-02-21
i host an ubuntu server on VPS, let's call it myHost. 
i registered a shiny domain, say mydomain.com, with a different registrar, say myRegistrar.
i want to host my own (authoritative) DNS on myHost.
i did find some good resources about bind9/nsd3 installation/configuration with ubuntu, but i don't understand how to bootstrap it all.

namely, if i installed nsd3/bind9 on myHost, and then i tell myRegistrar to use ns1.mydomain.com for the name server, how would myRegistrar resolve the ip of mydomain.com? 
isn't it a bit like an infinite loop?

i'd appreciate your help- this must be a trivial question for those of you hosting their own dns, but i couldn't find this in any of the dns tutorials yet.

cheers

---

### Post by minsf on 2012-02-25
> **minsf said:**
> i host an ubuntu server on VPS, let's call it myHost. 
if i installed nsd3/bind9 on myHost, and then i tell myRegistrar to use ns1.mydomain.com for the name server, how would myRegistrar resolve the ip of mydomain.com? 
isn't it a bit like a loop?


bump. 
so is it at all possible for one to self host the nameserver of mydomain.com at ns1.mydomain.com? 

after reading the manpage of nsd.conf, nsd's README (/usr/share/doc/nsd3/README.gz), the ubuntu server guide:
[https://help.ubuntu.com/11.10/serverguide/C/dns-configuration.html](https://help.ubuntu.com/11.10/serverguide/C/dns-configuration.html)
and the example here:
[http://calomel.org/nsd_dns.html](http://calomel.org/nsd_dns.html),
i think that the zone file would probably be:
```

$ORIGIN mydomain.com.
$TTL 86400

@ IN SOA ns1.mydomain.com. admin.mydomain.com. (
           2012022501  ; serial number
           28800       ; Refresh
           7200        ; Retry
           864000      ; Expire
           86400       ; Min TTL
           )

           NS      ns1.mydomain.com.

ns1        IN     A    1.2.3.4
*          IN     A    1.2.3.4

```
but i'm not sure how to point the registrar of mydomain.com to ns1.mydomain.com

---

### Post by Doug S on 2012-02-25
I think you will find that a lot of forum readers that run DNS do so only for their LAN, and not for the internet in general.
Anyway, to answer your question, you will have to communicate with your domain name registrar. In my case, I have an account with my registrar and I can set the IP address of the DNS to use for my domain name there (I have it set to what my ISP wanted me to set it to).

---

