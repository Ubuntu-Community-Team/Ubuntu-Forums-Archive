---
title: "dnsmasq: failed to create listening socket: Address already in use"
date: 2010-01-06
forum: General Help
---

### Post by markp1989 on 2010-01-06
im trying to set up a local dns cache [http://embraceubuntu.com/2006/08/02/local-dns-cache-for-faster-browsing/](http://embraceubuntu.com/2006/08/02/local-dns-cache-for-faster-browsing/) 


when i try to start the daemon i get error. 

```

mark@torrentslave:~$ sudo /etc/init.d/dnsmasq stop
 * Stopping DNS forwarder and DHCP server dnsmasq                                                                                                                        * (not running)
mark@torrentslave:~$ sudo /etc/init.d/dnsmasq start
 * Starting DNS forwarder and DHCP server dnsmasq                                                                                                                       
dnsmasq: failed to create listening socket: Address already in use
```

how do i sort this out?

i may have another service running that is listening on the socket. how do i foind out whcih one?


Thanks MArkp1989

edit: sorted it out dnsmasq had started it self during apt, before i had configured it . manualy stoped it , now it starts and works fine :D

---

### Post by cariboo on 2010-01-06
You can check if you have dhcp3-server running, by typing in a terminal:

```
ps ax | grep dhcp
```

If it is running, you can remove it, as you don't need it.

---

### Post by rnerwein on 2010-01-06
> **cariboo907 said:**
> You can check if you have dhcp3-server running, by typing in a terminal:

```
ps ax | grep dhcp
```If it is running, you can remove it, as you don't need it.

another reason can be that any body else block the default dhcp ports (67/68). figure it out by using: lsof -i 
ciao

oh now i know how to get the cool smilie. i mean port 68 and what did i get - ups

---

### Post by markp1989 on 2010-01-06
thanks for the replys, i sorted it out , dnsmasq had started it self during apt, before i had configured it . manualy stoped it , now it starts and works fine 


thanks :)

---

