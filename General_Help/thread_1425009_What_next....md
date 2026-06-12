---
title: "What next... ?"
date: 2010-03-08
forum: General Help
---

### Post by ArpSoft on 2010-03-08
Ok, here is the thing. I've bought 10 used servers from one data center, each has quad core processor, 10Gb of ram and 2 TB hdd...

Anyway, i intalled and configured ubuntu sever on each...

I have 150 MB Up/Down connection, with no bandwidth limit...

Now, i want to go online... I have 10 static ip's for each server...

Now, all i have to do is to somehow register them, their ip's...

Where do I do that? I mean, where can i register my servers so that their ip's are listed in public nameserver list???
Thanks...

---

### Post by myth1914 on 2010-03-08
10 static IPs per server?  WOW!  Anyway, Are you referring to getting DNS services?  Most hosting sites cover this, dyndns.com for example.

Or do you mean how to configure your own DNS server?

---

### Post by ArpSoft on 2010-03-08
> **myth1914 said:**
> 10 static IPs per server?  WOW!  Anyway, Are you referring to getting DNS services?  Most hosting sites cover this, dyndns.com for example.

Or do you mean how to configure your own DNS server?

 My step father is the owner of ISP company, that's why I have all those ip's :)

Anyway, i need to register my severs somewhere somehow, so that i can transfer my existing social networking web site to them...

So instead of linking my domain to my current web hosting provider, from now on i want to link my domain to my servers, since from now on those servers will host my web site :)

---

### Post by LoneWolfJack on 2010-03-08
you probably have your domains registered with some hosting company, so you have two options now: 

the first is to use your hosting companies DNS interface to set the IP address for each domain to one of your IPs

the second option is to set up your own DNS system and provide this information in your domain settings interface

---

### Post by myth1914 on 2010-03-08
The simple option is to buy the domain name and have the provider route traffic to your IP.

---

### Post by ArpSoft on 2010-03-08
So you're saying that instead of ns1.mycurrenthostingprovider.com i could just use my server's ip address?

---

### Post by LoneWolfJack on 2010-03-08
yes, but only if a DNS service is running at that IP address

---

### Post by ArpSoft on 2010-03-08
Oh, I am little confused right now...

Could you please tell me, steb by step what should i do :)

1. Servers are set up and online
2. I have registered domain
3...
4....
5..... 
etc... :)

Thanks

---

### Post by LoneWolfJack on 2010-03-08
when you register a domain, a nameserver (DNS) is specified (in fact, usually two or more). when a user types your domain, his or her ISP will query the DNS for the IP this domain is hosted on.

as you appear to be a total newbie at this, the best solution for you will be to go to the control panel of the company you registered your domains with. they should have a DNS settings page somewhere where you can specify the IP for each domain - that's where you enter one of your IPs. don't confuse this with the nameserver address on your domain settings page.

if you registered with some random junk hosting company, it's quite possible that you can't specify different IP addresses for different domains. in this case, either go find a better hosting company or set up your own DNS.

---

