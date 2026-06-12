---
title: "NetworkManager and Multiple IP Addresses"
date: 2010-10-08
forum: General Help
---

### Post by prahsj on 2010-10-08
When I use NetworkManager to assign multiple IP addresses to an interface, is there a command line tool that will list all IP addresses in use? ifconfig only shows the first IP address.

The 2nd IP address is working - it responds to ping and I can telnet to this address.

Can someone explain what NetworkManager is doing when you configure multiple IP address on one interface? When I have used multiple IP addresses in the past, this is done by creating virtual interfaces such as eth0:1. NetworkManager does not seem to be doing this.

Thanks,
Jon

---

### Post by geekshlby on 2010-10-08
```
ip addr
```

---

