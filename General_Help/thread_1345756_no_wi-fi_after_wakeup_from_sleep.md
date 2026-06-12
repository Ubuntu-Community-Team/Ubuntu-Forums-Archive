---
title: "no wi-fi after wakeup from sleep"
date: 2009-12-04
forum: General Help
---

### Post by maximilianyuen on 2009-12-04
first my network:

```
-network
       description: Ethernet interface
       product: Atheros AR8121/AR8113/AR8114 PCI-E Ethernet Controller
       vendor: Attansic Technology Corp.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: b0
       serial: 90:e6:ba:4a:dd:28
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=ATL1E driverversion=1.0.0.7-NAPI firmware=L1e latency=0 multicast=yes
       resources: irq:29 memory:febc0000-febfffff ioport:ec00(size=128)

```


my wifi works perfect, not until after wake up from sleep, which then become simply dead
can;t detect any network

I read from very old post that this is an old problem....

wonder is this problem solved in 9.10?

or is there any tricks to manually re-enable wifi after sleep?

thanks

---

### Post by cj13579 on 2009-12-04
I have this problem on my jaunty laptop

I normally just run 

```
sudo modprobe acerhk
```

and that kicks it back into life. Don't know if thats what you're meant to do but it works for me!

---

### Post by maximilianyuen on 2009-12-04
modprobe is something to detach and attach modules i learnt

but what is acerhk?

---

### Post by maximilianyuen on 2009-12-04
anyone?

---

### Post by cj13579 on 2009-12-05
acerhk is my wireless drivers. What laptop have you got?

---

### Post by maximilianyuen on 2009-12-05
Asus Pro 8

---

