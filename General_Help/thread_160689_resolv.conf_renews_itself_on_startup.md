---
title: "resolv.conf renews itself on startup?"
date: 2006-04-15
forum: General Help
---

### Post by jswan on 2006-04-15
Greetings,

basically my problem is that my internet works alot better when I change my nameserver to my isp name server instead of my router/modem.  When I change my resolv.conf to reflect this everything is good, but when I restart it defaults back to 192.168.1.1

How do I get it to stop defaulting?

THANKS!

---

### Post by Prospero2006 on 2006-04-15
The ip of your isp's nameserver is static I would imagine.
I believe the problem is that ubuntu is using dhcp to obtain it's ip info from 
the router. At the time, the router provides it with the 192.168.1.1 dns addy. 
You have a couple options:
    1.) Look at your router's dhcp server. You might be able to configure
          it to distribute the dns info you are looking for.

     2.) add this line to the end of /etc/init.d/bootmisc.sh
           
           echo nameserver ip-addy-you-want > /etc/resolv.conf


 That will overwrite the resolv.conf file at startup. See if it works. Worth a try.

Pros

---

### Post by jswan on 2006-04-15
thanks, I did the first one and it worked great

your smart

---

