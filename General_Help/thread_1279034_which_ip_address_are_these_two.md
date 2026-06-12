---
title: "which ip address are these two?"
date: 2009-09-30
forum: General Help
---

### Post by abhilashm86 on 2009-09-30
hi freinds!! (ip values being changed )
when i check ip address from terminal using ```

/sbin/ifconfig eth0| grep 'inet addr:'
          inet addr:192.168.1.2  Bcast:192.168.1.255  Mask:255.255.255.0

```
everyone's computer on internet has specific ip when its on WWW internet, 
my question is [there is this site]("http://www.whatismyip.com/"), 
which tells our ip......
i was confused by many people and friends, what is ifconfig shows and what that site shows?
ifconfig shows 192.168.1.2 and each person has local domain host name right?
please explain what are ifconfig and that website, i need to convince my friends:)

---

### Post by P4man on 2009-09-30
What you see in ifconfig is your local IP address, given by your router, and not visible to the internet. Your router has another IP address (2 in fact, one local, one for the internet), and that is the one that website is showing you.

More info here:
[http://www.howstuffworks.com/nat.htm](http://www.howstuffworks.com/nat.htm)

---

### Post by scragar on 2009-09-30
Your IP will appear differently locally if using a router because the computer only knows the IP assigned locally by the router, while that site only knows the IP of the router.

---

### Post by abhilashm86 on 2009-09-30
> **scragar said:**
> Your IP will appear differently locally if using a router because the computer only knows the IP assigned locally by the router, while that site only knows the IP of the router.

oh yes, so while using ssh/terminal client, i usually use ifconfig ip address and then hostname to connect...........
so i have broadband internet, i that website, when i traced that ip address, i was amazed now to see its location, its 6 kilometers from my home:)
Is that ISP or router? how to determine hops connected from my system to destination?
i'm just curious how many routers will be in city!! can anyone just tell approximation:)

---

### Post by P4man on 2009-09-30
not every router does NAT addressing (assigning different, local IP address) .Usually it will just be your home router that does that, other routers will just.. route traffic. You can see how many there are using "tracert" and then type in IP address of the destination.

---

### Post by abhilashm86 on 2009-09-30
> **P4man said:**
> What you see in ifconfig is your local IP address, given by your router, and not visible to the internet. Your router has another IP address (2 in fact, one local, one for the internet), and that is the one that website is showing you.

More info here:
[http://www.howstuffworks.com/nat.htm](http://www.howstuffworks.com/nat.htm)

according to you router has 2 ip address, is local ip address of router is same as my local ip address-- 192.168.1.2 ??
and one more ip is for internet, when 2 computers are connected via protocol, say ftp/http, which ip address are used for verification/handshake? is it local system address-192.168.1.2 or ip address of router?
thanks in advance:)

---

### Post by slakkie on 2009-09-30
Have a look here [http://www.warriorsofthe.net/](http://www.warriorsofthe.net/)

---

### Post by P4man on 2009-09-30
> **abhilashm86 said:**
> according to you router has 2 ip address, is local ip address of router is same as my local ip address-- 192.168.1.2 ??
and one more ip is for internet, when 2 computers are connected via protocol, say ftp/http, which ip address are used for verification/handshake? is it local system address-192.168.1.2 or ip address of router?
thanks in advance:)

Your router indeed has 2 addresses, one is usually similar to your PC's local address. Similar, but not the same. eg, on my network, my router has 192.168.1.1 as IP, while my PC's have 192.168.1.100 and upwards. The other address your router has is on the WAN port (internet), its the address whatismyip.com shows you.

As for the other questions:
[http://en.wikipedia.org/wiki/Network_address_translation](http://en.wikipedia.org/wiki/Network_address_translation)

---

### Post by abhilashm86 on 2009-09-30
> **P4man said:**
> Your router indeed has 2 addresses, one is usually similar to your PC's local address. Similar, but not the same. eg, on my network, my router has 192.168.1.1 as IP, while my PC's have 192.168.1.100 and upwards. The other address your router has is on the WAN port (internet), its the address whatismyip.com shows you.

As for the other questions:
[http://en.wikipedia.org/wiki/Network_address_translation](http://en.wikipedia.org/wiki/Network_address_translation)

yes all my doubts are clearer, thanks for the good links!! so to get rid of NAT, i expect IPV6 faster to rule the world of internet!! cheers:)

---

