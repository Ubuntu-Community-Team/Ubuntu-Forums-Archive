---
title: "IPv6 Server Test &amp; WebProxy?"
date: 2009-08-06
forum: General Help
---

### Post by harry71194 on 2009-08-06
Hi, I was wondering if there was an IPv6 webproxy anywhere? I have looked and can not find one. I need one so I can see if my server is working with IPv6 correctly. I set my AAAA record to 2001:0:53aa:64c:2cf7:10af:e7c4:ab66, so I need a proxy to see if it will load correctly. You can try to connect to the website though my DNS....please tell me which tunnelbroker you are using too. I am using HElectric. [http://ipv6.harryy.us](http://ipv6.harryy.us)

I am new to IPv6, so tell me if the site loads, and if it doesn't, tell me if my AAAA Record is correct please (my AAAA record is very long compared to ones from real servers, such as ipv6.google.com ........ mine is just a home connection). And see if there is an IPv6 Webproxy anywhere, please :)

---

### Post by broquea on 2009-08-06
> **harry71194 said:**
> Hi, I was wondering if there was an IPv6 webproxy anywhere? I have looked and can not find one. I need one so I can see if my server is working with IPv6 correctly. I set my AAAA record to 2001:0:53aa:64c:2cf7:10af:e7c4:ab66, so I need a proxy to see if it will load correctly. You can try to connect to the website though my DNS....please tell me which tunnelbroker you are using too. I am using HElectric. [http://ipv6.harryy.us](http://ipv6.harryy.us)

I am new to IPv6, so tell me if the site loads, and if it doesn't, tell me if my AAAA Record is correct please (my AAAA record is very long compared to ones from real servers, such as ipv6.google.com ........ mine is just a home connection). And see if there is an IPv6 Webproxy anywhere, please :)


1) better choice of domain this time....:roll:
2) you are using Teredo, not necessarily the HE broker, otherwise you'd be assigned an address range in their /32
3) ```
telnet ipv6.harryy.us 80
Trying 2001:0:53aa:64c:2cf7:10af:e7c4:ab66...
telnet: connect to address 2001:0:53aa:64c:2cf7:10af:e7c4:ab66: Connection refused

```

---

### Post by harry71194 on 2009-08-06
Okay.


Google's IPv6 address is 2001:4860:0:2001::68 ...... mine is so much larger compared to Google's.....
 
 
Lighttpd is running and listening for IPv4 and IPv6 connections. So, what have I done wrong?
 
 
I think it might be a problem with forwarding ports differently under IPv6, OR you can nor forward ports through a broker, or something..... as my Ident (~ on IRC) works if I use IPv4 servers, and does not if I use IPv6 servers.

---

### Post by broquea on 2009-08-06
> **harry71194 said:**
> Okay.


Google's IPv6 address is 2001:4860:0:2001::68 ...... mine is so much larger compared to Google's.....
 
 
Lighttpd is running and listening for IPv4 and IPv6 connections. So, what have I done wrong?
 
 
I think it might be a problem with forwarding ports differently under IPv6, OR you can nor forward ports through a broker, or something..... as my Ident (~ on IRC) works if I use IPv4 servers, and does not if I use IPv6 servers.

Address length has nothing to do with any of this. Make sure that you can connect to that IP locally (enclose in [] if using a browser, otherwise telnet to port 80).

Again, you aren't using a broker, you are using Teredo. So it is using UDP to penetrate your NAT, talk to MS teredo servers to figure out connectivity based on closest teredo relays based on source and destinations. Most likely an issue with trying to serve content over Teredo and not getting back into your machine. Possibly ip6tables rules.

---

