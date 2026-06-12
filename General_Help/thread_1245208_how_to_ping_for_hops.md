---
title: "how to ping for hops?"
date: 2009-08-20
forum: General Help
---

### Post by abhilashm86 on 2009-08-20
if i want to know how many times my IP packet went through routers or network switches, i read there is a hop count that does and ping supports this......
how i need to do it using ping or other method?

---

### Post by coldReactive on 2009-08-20
> **abhilashm86 said:**
> if i want to know how many times my IP packet went through routers or network switches, i read there is a hop count that does and ping supports this......
how i need to do it using ping or other method?

```
sudo apt-get install traceroute
```

then do this in terminal

```
sudo tracert <ip or domain>
```

---

### Post by philinux on 2009-08-20
tracepath is installed.

---

### Post by kanikilu on 2009-08-20
I think traceroute will do what you want:

(GUI) System -> Administration -> Network Tools -> Traceroute

(CLI) traceroute target (may need to install traceroute first with apt-get or synaptic)

// Edit - too slow ;)

---

### Post by Grenage on 2009-08-20
At the risk of being another 'me too'...

**traceroute** IP or DNS name.

---

### Post by The Cog on 2009-08-20
My favourite is **mtr**.

---

### Post by abhilashm86 on 2009-08-20
thanks for inforamtion, i just now used traceroute, but can anyone please explain following result?
```
abhilash@abhilash:~$ traceroute 208.100.40.200
traceroute to 208.100.40.200 (208.100.40.200), 30 hops max, 40 byte packets
 1  192.168.1.1 (192.168.1.1)  1.050 ms  1.489 ms  1.951 ms
 2  117.192.96.1 (117.192.96.1)  23.457 ms  25.891 ms  28.284 ms
 3  218.248.160.106 (218.248.160.106)  30.505 ms  32.940 ms  35.426 ms
 4  * * *

```
its a website ip address, when i tried 3 or more ip's, it just says 30 hopsmax?

---

