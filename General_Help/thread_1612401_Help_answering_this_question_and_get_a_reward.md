---
title: "Help answering this question and get a reward"
date: 2010-11-03
forum: General Help
---

### Post by karthick87 on 2010-11-03
I am using ubuntu for more than one year.Its awesome and easy to use.I normally use ubuntu for serfing the net,reading the tutorials etc etc..I have my ftp server enabled in my system to share and upload files.I use squid proxy server in my stand alone system to block porn sites and downloads.My friends who use my system they simply disable the proxy settings in the browser and started to download.I want to restrict bypassing my proxy by forwarding all the outgoing traffic through the squid port [COLOR=Red]3128[/COLOR].

Being a standalone system i couldn't find any solution to do this yet.Searched google for a month but end up with no solution.None works...! If someone helps me to get a solution for this, i am ready to pay [COLOR=Red]15$[/COLOR] from my [COLOR=Red]paypal [/COLOR]account as a reward..
[COLOR=DarkRed]
Squid version:[/COLOR]
[COLOR=Red]  
squid 3.0[/COLOR]

---

### Post by P4man on 2010-11-03
Hi,

If I understand it correctly, what you are trying to achieve is locking down firefox so users cant override your proxy settings? Have a look here:

[http://hartmansblog.blogspot.com/2010/06/new-firefoxjs.html](http://hartmansblog.blogspot.com/2010/06/new-firefoxjs.html)

It doesnt mention proxy settings specifically but Im sure you'll figure that out.

BTW, whilst not wanting to pretend this is the definite answer to your question, Im not interested in any reward or payement, and FWIW, it makes me more reluctant to answer for some reason. But I understand why you'd do that.

---

### Post by HermanAB on 2010-11-03
Howdy, 

The solution is to redirect port 80 to 3128 using iptables:
[http://tldp.org/HOWTO/TransparentProxy-6.html](http://tldp.org/HOWTO/TransparentProxy-6.html)
[http://www.faqs.org/docs/Linux-mini/TransparentProxy.html](http://www.faqs.org/docs/Linux-mini/TransparentProxy.html)

Iptables (netfilter) is part of the network stack and cannot be bypassed.

The essential redirect rule is:
iptables -t nat -A PREROUTING -i eth0 -p tcp --dport 80 -j REDIRECT --to-port 3128

---

### Post by karthick87 on 2010-11-03
> **HermanAB said:**
> Howdy, 

The solution is to redirect port 80 to 3128 using iptables:
[http://tldp.org/HOWTO/TransparentProxy-6.html](http://tldp.org/HOWTO/TransparentProxy-6.html)
[http://www.faqs.org/docs/Linux-mini/TransparentProxy.html](http://www.faqs.org/docs/Linux-mini/TransparentProxy.html)

Iptables (netfilter) is part of the network stack and cannot be bypassed.

The essential redirect rule is:
iptables -t nat -A PREROUTING -i eth0 -p tcp --dport 80 -j REDIRECT --to-port 3128

Its not working Herman..

---

### Post by SlugSlug on 2010-11-03
-A PREROUTING -p tcp -m tcp --dport 80 -j http-exceptions
-A PREROUTING -p tcp -m tcp --dport 80 -j REDIRECT --to-ports 3129
##-A http-exceptions -d ip.you.don't.want.blocking -j ACCEPT

---

### Post by karthick87 on 2010-11-04
How about creating a virtual interface..?So that i will be having one more NIC..

---

### Post by SlugSlug on 2010-11-04
humm.  how many NICs do you have now?
on our server we use one for the internal network and another straight to the internet

---

### Post by karthick87 on 2010-11-04
Its a standalone system having one NIC for directly connecting to internet.

---

### Post by SlugSlug on 2010-11-04
righ tok,  and every one else uses that pc then..

ok so what does

-A PREROUTING -p tcp -m tcp --dport 80 -j REDIRECT --to-ports 3129

do 

that should route all 'no proxy' traffic through squid..?

---

