---
title: "hide OS fingerprint on network"
date: 2012-08-13
forum: General Help
---

### Post by Padamsambhav on 2012-08-13
i am using ubuntu 12.04. i want my OS to be undetected from outside network and Internet. Is it possible??? I tried things with ufw and iptables but nothing is working out for me

---

### Post by asmoore82 on 2012-08-13
Are you just talking about your web browser's user agent string?

---

### Post by Cheesemill on 2012-08-13
You can always switch off networking altogether on that machine.

---

### Post by Habitual on 2012-08-13
> **Padamsambhav said:**
> ... i want my OS to be undetected from outside network and Internet. Is it possible??? ...

Yes, disconnect the ethernet cable.

---

### Post by Padamsambhav on 2012-08-13
Wat exactly i was tryin to do is keep my OS untraceable by network tool like nmap and other network exploitation tools... May be it is possible if i drop all incoming packets excepts the packets that are 'replies' to my outgoing packets..but i dnt know exactly how to configure it... im a beginner so plz include detailed steps

---

### Post by Frogs Hair on 2012-08-13
I have a dual boot on a Windows non sharing network and though my computer is visible what OS I have booted is not. Upload and download activity can viewed from our designated administrators computer regardless of operating system because he controls the router. This site might offer some insight but probably not give you an answer. I have never had to hide my activities.   

[http://www.cyberciti.biz/tips/top-linux-monitoring-tools.html](http://www.cyberciti.biz/tips/top-linux-monitoring-tools.html)

---

### Post by CharlesA on 2012-08-13
> **Habitual said:**
> Yes, disconnect the ethernet cable.

This is the only way to be undetectable.

> **Padamsambhav said:**
> Wat exactly i was tryin to do is keep my OS untraceable by network tool like nmap and other network exploitation tools... May be it is possible if i drop all incoming packets excepts the packets that are 'replies' to my outgoing packets..but i dnt know exactly how to configure it... im a beginner so plz include detailed steps

Anyone with access to the network will be able to see your machine on it, regardless on how you try to 'hide' it.

---

### Post by raja.genupula on 2012-08-13
How about changing to fake proxy's and MAC Address ?

---

### Post by Hungry Man on 2012-08-13
Not without disconnecting from the internet or routing all traffic through a local proxy.

---

### Post by Zukaro on 2012-08-14
The only way I know of you can be hidden on the Internet is just to get on a proxy server and change your MAC Address.  You could also try using TOR to remain anonymous online (although your machine will still appear on your network).  I'm not familiar with TOR however, so I don't know much about it.

[https://www.torproject.org/](https://www.torproject.org/)

Another thing you can do is get behind a NAT router as that blocks all incoming requests unless they're responses to an outgoing request (but again, you still appear on your network).

---

### Post by raja.genupula on 2012-08-15
```
sudo aptitude install macchanger
```

it has very good man page to help you how to change the MAC . it can help you a bit to hide .

---

### Post by CharlesA on 2012-08-15
Spoofing MAC addresses does nothing to help you remain hidden on the network. Even if you spoof the MAC, it will still be associated with an IP and that IP can be traced to a machine.

---

