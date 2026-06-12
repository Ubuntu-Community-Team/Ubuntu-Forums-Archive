---
title: "Cycling IP's"
date: 2009-07-29
forum: General Help
---

### Post by Theory5 on 2009-07-29
Is there some sort of program or something that I can get that will change my IP to a random one or one from a list each time I connect to a network, wireless or wired?

---

### Post by Ocxic on 2009-07-29
your IP is supplied by the network automatically, so no.

---

### Post by jtech55 on 2009-07-29
[https://addons.mozilla.org/en-US/firefox/addon/125](https://addons.mozilla.org/en-US/firefox/addon/125)

---

### Post by DGortze380 on 2009-07-29
> **Theory5 said:**
> Is there some sort of program or something that I can get that will change my IP to a random one or one from a list each time I connect to a network, wireless or wired?

That depends n a lot of things... I think you need to take a closer look at how IPs work across a network.

jtech55's link may be the simplest solution for you.

---

### Post by id10twork on 2009-07-29
> **Theory5 said:**
> Is there some sort of program or something that I can get that will change my IP to a random one or one from a list each time I connect to a network, wireless or wired?

You can mask your IP using certain software that will mask the IP when you go to websites, but your IP changing is up to your network admin/ISP. most ISPs these days do it automatically, and there's no set time frame: you lose your IP when someone else needs one, then you get a new one. If you have a static IP, then there is going to be no way for you to get a random one, unless you pay for more than 1 static IP.

---

### Post by credobyte on 2009-07-29
Theoretically, yes - you can automatically change IP's, but .. you will more likely not be able to use them. IP is not assigned by your PC - it comes from your ISP and in a result of invalid IP ( which is the same as your postal address if I will want to send you a letter ), you might not be able to use the internet. 
As far as I understand, proxy would be the best bet, especially, Tor ( search for it ).

---

### Post by Theory5 on 2009-07-30
sorry, It was late and I was tired, I meant to ask: is there any way to change my MAC address each time I connect to a network, or every so often?

---

### Post by Commander_Keen on 2009-07-30
Yes..
  Get a new Lan card.
Every Mac address is assigned to a lan card from the manufacture.
There are programs out there that will allow you to change it or mask it ( at least for the Macs)  Not sure about Linux.
  Why would you want to change your mac address?

---

### Post by mcduck on 2009-07-30
"ifconfig *interface* hw *class* *newmac*" should work. So you'd do something like this:
```
ifconfig eth0 hw ether 00:80:48:BA:d1:20
```

You could write some simple script to generate random MAC addresses and change the address on startup. Although I don't really see any reason to do that..

---

### Post by Grenage on 2009-07-30
Mcduck has the solution you want.  DHCP addresses have a lease time, and until that time has expired your network adapter will get the same IP address....

...unless you change the MAC address, which is the network identifier.

---

### Post by Commander_Keen on 2009-07-30
oh that's interesting.. Ihad no idea, it was that easy to do.

---

### Post by Theory5 on 2009-07-30
> **Grenage said:**
> Mcduck has the solution you want.  DHCP addresses have a lease time, and until that time has expired your network adapter will get the same IP address....

...unless you change the MAC address, which is the network identifier.

Exactly. Plus changing the mac address makes your laptop harder to track, because well, the mac address pretty much says "this is so and so's card".

---

