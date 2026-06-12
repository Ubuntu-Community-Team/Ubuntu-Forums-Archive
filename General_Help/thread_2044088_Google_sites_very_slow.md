---
title: "Google sites very slow"
date: 2012-08-18
forum: General Help
---

### Post by Ptallqvist on 2012-08-18
I asked about this before, and thought I had it solved ([http://ubuntuforums.org/showthread.php?t=2025472](http://ubuntuforums.org/showthread.php?t=2025472)), but no.

So, the problem is that pretty randomly, google (gmail, drive, search, pretty much anything googly) and/or facebook stop working on the browser (firefox, chrome). Sometimes they are just slow, sometimes they keep loading forever without ever getting anywhere.
I have tried this over wifi and wired, with a fresh install of ubuntu, xubuntu and opensuse, and the problem stays the same. Sometimes it's just slow, sometimes 

On the same desktop machine but running windows7, everything works just fine. And on my laptop, which runs on xubuntu.

I'm pretty much running out of ideas. Flash? DNS? ISP?

---

### Post by jacktar on 2012-08-18
Try OpenDNS an see if it helps.

---

### Post by Ptallqvist on 2012-08-19
Thanks for the reply, but I've already tried both opendns and google's dns. According to namebench, google dns should work like a charm.

---

### Post by Ptallqvist on 2012-08-20
Could the ADSL modem/router cause this? I have a crappy one from my ADSL provider. But the router is older than the problem.

---

### Post by Frogs Hair on 2012-08-20
It could be the router, but all search providers would likely be affected. Does your ISP promote a particular search engine I know some do.  

My father went through two ISP supplied routers in 5 years before changing his service. There were intermittent conductivity problems prior to each router dieing, but they were not isolated to any particular search provider.

---

### Post by Ptallqvist on 2012-08-28
I am getting nowhere with this. Right now, for example, I get the "ERR_EMPTY_RESPONSE" from facebook.com when I try it with Chrome. Yet I can ping facebook.com just fine.

I am currently using Google DNS. This is my /etc/network/interfaces:

> auto eth0
    iface eth0 inet static
        address 192.168.100.10
        netmask 255.255.255.0
        gateway 192.168.100.1

This is resolv.conf:
> nameserver 8.8.8.8
nameserver 8.8.4.4

Again, the same computer with Windows7 works just fine, and my laptop with Xubuntu as well, so I really don't think it can be the router. Could it be the network card? How can I check that?

---

### Post by d4m1r on 2012-08-28
Try:

```
auto eth0
    iface eth0 inet static
        address 192.168.1.102
        netmask 255.255.255.0
        gateway 192.168.1.1                      
```

---

### Post by Ptallqvist on 2012-08-31
I tried that, but nothing changed. However, ifconfig still gives this:
> eth0      Link encap:Ethernet  HWaddr 00:21:85:1c:1b:56  
          inet addr:192.168.100.16  Bcast:192.168.100.255  Mask:255.255.255.0
          inet6 addr: fe80::221:85ff:fe1c:1b56/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1572919 errors:0 dropped:0 overruns:0 frame:0
          TX packets:681480 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2243603262 (2.2 GB)  TX bytes:52954182 (52.9 MB)
          Interrupt:45 Base address:0x8000 

Is there a feature in Ubuntu that somehow overrides the /etc/network/interfaces?
This is really weird.

---

### Post by Ptallqvist on 2012-09-01
OK, my bad :) I forgot to reboot the network after editing the file. 

But editing the addresses as suggested by d4m1r stopped the network from working at all. I restored the old addresses and now it works, but as badly as before. I can't reach gmail at all, for example.

---

### Post by Ptallqvist on 2012-09-02
I'm sorry to keep bouncing this thread, but I would really appreciate some help. I really dislike using windows because of this issue.

Could this be a non-network-related problem? Could some other driver cause this kind of behavior?

---

### Post by Ptallqvist on 2012-09-10
It was an MTU issue. I solved it by lowering MTU as described here:
[http://www.ubuntugeek.com/how-to-change-mtu-maximum-transmission-unit-of-network-interface-in-ubuntu-linux.html](http://www.ubuntugeek.com/how-to-change-mtu-maximum-transmission-unit-of-network-interface-in-ubuntu-linux.html)

---

