---
title: "Connecting to the internet?"
date: 2009-08-23
forum: General Help
---

### Post by tushantin on 2009-08-23
I work at a Cafe where the internet is shared by LAN TCP/IP and running under Windows XP. When a customer wishes to connect their laptop to the net, I simply give them a port, copy the IP addresses and DNS while giving them an address, such as, "192.168.100.91" which no other PC uses. 

However, I wanted to try connecting a computer with Ubuntu installed onto the net, but I'm unable to. How do I use that TCP/IP that I use under Windows XP in Ubuntu?

---

### Post by DeMus on 2009-08-23
> **tushantin said:**
> I work at a Cafe where the internet is shared by LAN TCP/IP and running under Windows XP. When a customer wishes to connect their laptop to the net, I simply give them a port, copy the IP addresses and DNS while giving them an address, such as, "192.168.100.91" which no other PC uses. 

However, I wanted to try connecting a computer with Ubuntu installed onto the net, but I'm unable to. How do I use that TCP/IP that I use under Windows XP in Ubuntu?

Isn't it possible to make the whole system use DHCP, which is a kind of standard for accesspoints. That way every computer can connect without the need of setting addresses.

---

### Post by sp0nge on 2009-08-23
I can see the pros of controlling this access in a public place, especially if you're tasked as the network admin- chances are security is an afterthought (as usual).

Connecting ubuntu via static IP can be done by editing /etc/network/interfaces as follows:

```
auto lo eth0
iface lo inet loopback
iface eth0 inet static
address xxx.xxx.xxx.xxx(enter your ip here)
netmask xxx.xxx.xxx.xxx
gateway xxx.xxx.xxx.xxx(enter gateway ip here)
```

then edit /etc/resolv.conf:

```
nameserver xxx.xxx.xxx.xxx(enter your dns server ip)
nameserver xxx.xxx.xxx.xxx(enter your alt dns server ip)
```

finally restart the networking on the machine:

```
sudo /etc/init.d/networking restart
```

Viola! you should haz interwebz!

---

### Post by tushantin on 2009-08-24
XD Thanks! It works now. I should probably note this down in case I forgot.

---

