---
title: "Network eth0 not up at boot time"
date: 2010-10-27
forum: General Help
---

### Post by satish_j on 2010-10-27
I have to manually enable the Network interface eth0 at boot time by running:
[code
sudo ifconfig eth0 up
[/code]
Any ideas how to enable it at startup.
Here is my /etc/network/interfaces file
```
auto lo
iface lo inet loopback


iface dsl-provider inet ppp
pre-up /sbin/ifconfig eth0 up # line maintained by pppoeconf
provider dsl-provider

auto eth0
iface eth0 inet manual

```

---

### Post by dcstar on 2010-10-27
> **satish_j said:**
> I have to manually enable the Network interface eth0 at boot time by running:
[code
sudo ifconfig eth0 up
[/code]
Any ideas how to enable it at startup.
Here is my /etc/network/interfaces file
```
auto lo
iface lo inet loopback


iface dsl-provider inet ppp
pre-up /sbin/ifconfig eth0 up # line maintained by pppoeconf
provider dsl-provider

auto eth0
iface eth0 inet **manual**

```

It is doing exactly what it is supposed to with that configuration.

Why not just let the Network Manager manage it with the "Connect Automatically" setting?

---

### Post by satish_j on 2010-10-27
> **dcstar said:**
> It is doing exactly what it is supposed to with that configuration.

Why not just let the Network Manager manage it with the "Connect Automatically" setting?
And,how to achieve this "Connect Automatically"?
shall i have to change 'Manual' to 'Automatic' in interfaces file??

---

### Post by satish_j on 2010-10-29
Ok,got it..
changed the entry 'manual' to 'dhcp',rebooted and it is up and running.

---

