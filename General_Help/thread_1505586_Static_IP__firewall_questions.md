---
title: "Static IP / firewall questions"
date: 2010-06-09
forum: General Help
---

### Post by Major Payne on 2010-06-09
Currently I'm running ubuntu (desktop) 10.04 on a e6400 which is running a CS server with a static external IP. 

I have my Firewall on my Modem turned off. I can ping the server from outside the network but if I attempt to have someone connect to the server it fails. 

Does ubuntu automatically install a firewall?

how do i open port 27015 if it is on
i've used the 
iptables -A INPUT -p tcp --dport 27015 -j ACCEPT and did a iptables -L and it shows... but when I check to see if it's open i get Port [27015]("http://en.wikipedia.org/wiki/Port_27015")
 is closed on

i also do a netstat grep listen (not exact command used) and it does not show that it's listening

---

### Post by Major Payne on 2010-06-09
added a few steps i have taken

---

### Post by dino99 on 2010-06-09
[https://help.ubuntu.com/community/UFW](https://help.ubuntu.com/community/UFW)

into synaptic , look at gufw and ipblock/moblock

and link below

---

### Post by Major Payne on 2010-06-09
ok I have done all that my modem is in DMZ mode and nothing... is there a way to find out if the port is open from command line?

i'm not sure where the block is coming from... either my modem (but the pc is in SMZ mode) my PC shows that it's working. or the ISP network

---

### Post by Major Payne on 2010-06-09
sorry for the post.. If i turn ufw logging on will it shows if something attempted to access port 27015. This is the only way i can think of that will help me ascertain if it's the pc, modem or the network blocking that port

used nmap and it shows that the port is closed.

PORT      STATE  SERVICE
27015/tcp closed unknown

i checked my iptables and this is what it shows for that 

```
Chain ufw-user-input (1 references)
target     prot opt source               destination
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:27015
ACCEPT     udp  --  anywhere             anywhere            udp dpt:27015
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:27015
ACCEPT     udp  --  anywhere             anywhere            udp dpt:27015

```

---

### Post by dcstar on 2010-06-10
> **Major Payne said:**
> Currently I'm running ubuntu (desktop) 10.04 on a e6400 which is running a CS server with a static external IP. 

I have my Firewall on my Modem turned off. I can ping the server from outside the network but if I attempt to have someone connect to the server it fails. 

Does ubuntu automatically install a firewall?

how do i open port 27015 if it is on
i've used the 
iptables -A INPUT -p tcp --dport 27015 -j ACCEPT and did a iptables -L and it shows... but when I check to see if it's open i get Port [27015]("http://en.wikipedia.org/wiki/Port_27015")
 is closed on

i also do a netstat grep listen (not exact command used) and it does not show that it's listening

Unless an **application** is actually using the port, then nothing will be listening on it.

---

### Post by lz1dsb on 2010-06-10
> **dcstar said:**
> Unless an **application** is actually using the port, then nothing will be listening on it.

That's absolutely correct. Did you try to a telnet to that port? If it's a TCP port just checking with "telnet <ip-address> <port>" will give you an idea whether the initial three way handshake is working.

Cheers, 
Boyan

---

