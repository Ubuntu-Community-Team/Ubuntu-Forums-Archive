---
title: "/etc/network/interfaces bridge"
date: 2009-09-06
forum: General Help
---

### Post by Psycho.mario on 2009-09-06
How can i have a bridge from eth0 to eth1 in the /etc/network/interfaces file?
eth0 is to the lan:

```
auto eth0
iface eth0 inet static
address 192.168.1.100
network 192.168.1.0
netmask 255.255.255.0
broadcast 192.168.1.255
gateway 192.168.1.1
```

Im not sure how to put eth1, i want it to be 192.168.**2**.1 (Is this possible?)
Then i want to bridge eth0 to eth1 and create a subnet from the linux box.
Can someone give me some pointers to creating a bridge, and what should the settings be to put eth1 in the /etc/network/interfaces file?

Thanks

---

### Post by Psycho.mario on 2009-09-06
Bump

---

### Post by Iowan on 2009-09-06
[Here]("https://help.ubuntu.com/community/NetworkConnectionBridge") is a help page on bridging.

---

