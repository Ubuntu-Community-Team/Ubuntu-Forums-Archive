---
title: "ping: Destination Host Unreachable"
date: 2012-04-30
forum: General Help
---

### Post by MrRockchip on 2012-04-30
I have two PCs: 1st has Ubuntu 12.04 clean fresh install, and 2nd is running Ubuntu 12.04 LiveCD.
They are connected by an Ethernet wire.

I want to access 2nd computer's share from a 1st one, but cannot see it.
Initially, I had a problem "Network disconnected".
I have solved it by switching IP addresses of their Ethernets from DHCP mode to manual mode:
192.168.0.2 and 192.168.0.3 . Net mask set to 255.255.255.0

But when I try to ping one computer from another, I get "Destination Host Unreachable" error.
Please, tell me, how to solve it?

---

### Post by MrRockchip on 2012-04-30
If I connect 2nd computer (with LiveCD) to a Windows PC, everything works fine.
But with two ubuntu computers, the issue still occurs.

---

### Post by MrRockchip on 2012-05-01
Do you know how to solve this problem?

---

### Post by MrRockchip on 2012-05-01
Any advice, even remote, will be helpful! :KS

---

### Post by zero2xiii on 2012-05-01
Hay,

Please don't do the multiple posts on your own post thing, you can bump a thread after 24-48 hours of no response if you truely feel the need. But this is un necesary.

Anyway, the easy answer to a very dull and no info post. You probably need samba to be installed. Accessing windows shares is fine, but creating them using ubuntu needs a network file client if you will. Try installing samba.

aswell, try changing the IPs to 192.168.1.2 and 192.168.1.3... the range 192.168.**0**.0-255 is not a normal, internal, network range. It is usualy asociated with routers.

Age old issue, make sure you are using the correct cable? If it is not a gigabyte network you might still need a crossover cable to go from PC to PC.

for further help, please post the output of:

```
sudo ifconfig
```
```
sudo route
```

Cherz

---

