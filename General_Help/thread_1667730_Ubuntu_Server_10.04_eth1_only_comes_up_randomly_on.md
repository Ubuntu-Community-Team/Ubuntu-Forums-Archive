---
title: "Ubuntu Server 10.04: eth1 only comes up randomly on boot"
date: 2011-01-15
forum: General Help
---

### Post by giburrito on 2011-01-15
Sometimes when I reboot the machine, eth1 comes up and I can just ssh into the machine to work on whatever I have to, and about half the time I have to ifup eth1 on the machine itself. When I use ifup manually, there are no errors.

Any ideas on how to make eth1 more reliable?

interfaces file:
```

auto lo
iface lo inet loopback

auto eth1
iface eth1 inet static
address 172.16.31.180
netmask 255.255.255.0
network 172.16.31.0
broadcast 172.16.31.255
gateway 172.16.31.1

```

---

