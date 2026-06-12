---
title: "How do I open port/port forward?"
date: 2011-01-13
forum: General Help
---

### Post by tuahaa on 2011-01-13
Hi.

I've been getting extremely slow torrent speeds on ubuntu. On windows, it is 10 times faster. 

I opened transmission settings and it says the port that transmission uses is closed. I tried changing the port or opening it, but it still doesn't work. What am I doing wrong?

---

### Post by psusi on 2011-01-13
Have you mucked about with a firewall?  It sounds like you have and blocked access to all ports by default.

---

### Post by weedeater64 on 2011-01-13
Try checking the _***Forward port from router***_ check box.
You may have to open a port in your router, if you have one..

there is a way to open more ports too, but I don't recall how, perhaps google "opening ports",
**do be careful with this though, this is a security issue...**

Some folks set up alternate ports for standard services to help in that regard..

---

### Post by tuahaa on 2011-01-13
> **psusi said:**
> Have you mucked about with a firewall?  It sounds like you have and blocked access to all ports by default.

I don't think so. It was like that when I installed Ubuntu 10.10...

---

### Post by tuahaa on 2011-01-13
> **weedeater64 said:**
> Try checking the _***Forward port from router***_ check box.

Which checkbox? Please explain, I'm sort of a noob

---

### Post by weedeater64 on 2011-01-13
Your's may be different that mine, but here is a screenshot...

[ATTACH]180972[/ATTACH]

---

### Post by marin123 on 2011-01-13
> **tuahaa said:**
> Which checkbox? Please explain, I'm sort of a noob

Transmission -> Edit -> Preferences -> Network -> Use UPNP port forwarding

you can open a port in your firewall if you think you'll get more speed: ```
sudo ufw allow 51413
```

thats the port transmission uses by default...

---

### Post by psusi on 2011-01-13
Then you may need to configure your router.  Consult its manual for more information.  It should automatically have the router forward the ports though with UPnP, and since it works in Windows that makes me think UPnP is working, so you shouldn't have a problem.

---

### Post by ledzpg on 2011-01-13
Usually, when you forward a port from the router, you have a pre-defined IP to forward that port.
Ex: Port 17123 to 192.168.168.1

Did you defined your IP manually on Ubuntu or left it by DHCP?
If it's by DHCP, probably the IP is different from the one defined on the modem port forward.

You can also define on your router a fixed IP for your specific MAC Address.
Ex: When the LAN with MAC 00:1A:2B:3C:4D connects, give it the 192.168.168.1 IP

Then you can always leave it by DHCP, no matter the system you use ;)

---

### Post by ledzpg on 2011-01-13
Usually, when you forward a port from the router, you have a pre-defined IP to forward that port.
Ex: Port 17123 to 192.168.168.1

Did you defined your IP manually on Ubuntu or left it by DHCP?
If it's by DHCP, probably the IP is different from the one defined on the modem port forward.

You can also define on your router a fixed IP for your specific MAC Address.
Ex: When the LAN with MAC 00:1A:2B:3C:4D connects, give it the 192.168.168.1 IP

Then you can always leave it by DHCP, no matter the system you use ;)

---

### Post by psusi on 2011-01-13
> **ledzpg said:**
> 
Did you defined your IP manually on Ubuntu or left it by DHCP?
If it's by DHCP, probably the IP is different from the one defined on the modem port forward.

He hasn't set up a forward rule on the router before, which is why the title of the thread is asking how to do so.

---

### Post by tuahaa on 2011-01-14
Well, I've tried forwarding a port to the I.P address my Linux system uses via the router settings... but it doesn't work.

This is odd.

I think this isn't the problem or else it will not have worked on windows either.

I gotta switch to windows everytime I want to get a torrent going :(

---

### Post by tuahaa on 2011-01-14
It seems that I've definitely opened port 51413 (according to "Network Tools") but transmission still reports that the port is closed.

---

### Post by tuahaa on 2011-01-14
Hmm... looks like I'm getting decent speeds now (I did something). I'm downloading [legal, don't worry] torrents at 300Kib/s. I'll probably get 700 Kib/s on windows (seeing as I thankfully have a good connection), but it doesn't make much difference as either way, my downloads finish at decent times.

---

### Post by ledzpg on 2011-01-14
This site may help you in your router config:

[http://portforward.com/english/routers/port_forwarding/routerindex.htm](http://portforward.com/english/routers/port_forwarding/routerindex.htm)

---

### Post by marin123 on 2011-01-14
in my experience, i can tell you that uTorrent has better speeds than Transmission, but i only have 500 kB/s connection, so i dont care much about speed, because i have to limit transmission so others can go online...

---

