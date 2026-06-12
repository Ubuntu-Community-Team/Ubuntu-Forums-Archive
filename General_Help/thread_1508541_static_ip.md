---
title: "static ip"
date: 2010-06-13
forum: General Help
---

### Post by spiky001 on 2010-06-13
I want to assign a static ip address, my network/interfaces files shows
```
auto lo
iface lo inet loopback
```
am I correct to add 
```
[I]iface eth0 inet static
address 10.42.43.10
netmask 255.255.252.0
gateway 10.42.43.1[/I]
``` 
or is there more I need?

---

### Post by apjone on 2010-06-13
You will also need to edit /etc/resolv.conf and add dns servers.

/etc/network/interfaces should look like this
```

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
address 10.42.43.10
netmask 255.255.252.0
gateway 10.42.43.1

```

/etc/resolv.conf should look like this
```

domain home
search home
nameserver dns-server1 (from you ISP
nameserver dns-server2   settings)

```

---

### Post by spiky001 on 2010-06-13
ok thks, the pc I want to have static ip is on a lan so do I need dns settings?

---

### Post by apjone on 2010-06-13
because you are not getting it from DHCP if you set it to static and do not set dns settings, everything you want to do LAN or Web will require you to use the IP Address. You could just put 

```

nameserver 10.42.43.1 (or IP address of your router)

```

---

### Post by spiky001 on 2010-06-13
ok confused now sorry, pc1 is server with internet,
I need pc2 to have static for ssh reason/vnc

---

