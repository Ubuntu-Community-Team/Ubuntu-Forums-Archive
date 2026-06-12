---
title: "How to restart network adapter (not service) without restart?"
date: 2010-03-13
forum: General Help
---

### Post by leandromartinez98 on 2010-03-13
I have a suspend problem in my laptop. Sometimes, when resuming from
suspend, the network adapter is down (that is, the network does not work
and the light of the network adapter is off). Restarting the network
service doesn't work, because I think that the system forgot about the
hardware, and probably the driver should be reloaded.

Does anyone knows how to do that?

(ps. /etc/init.d/networking restart does not work, because the
hardware driver is not being recognized anymore).

Edit: My network interface, when functional is this:

```

wlan0     Link encap:Ethernet  HWaddr 00:1b:77:db:30:15  
          inet addr:192.168.1.200  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21b:77ff:fedb:3015/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1492  Metric:1
          RX packets:5585 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5066 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3488467 (3.4 MB)  TX bytes:1522198 (1.5 MB)

```

And lsmod here provides this modules which I think are related to the network
adapter:

```

iwl3945                77372  0 
iwlcore               112796  1 iwl3945
mac80211              181140  2 iwl3945,iwlcore
led_class               4096  2 iwl3945,iwlcore
cfg80211               93052  3 iwl3945,iwlcore,mac80211

```

---

### Post by leandromartinez98 on 2010-03-15
Nobody? It is not possible to fully restart a hardware device without rebooting?

---

### Post by spiky001 on 2010-03-15
try sudo ifconfig wlan0 up

---

### Post by patchwork on 2010-03-15
I'm not a network guru, so you will want to research this further, but I believe ifdown and ifup are what you're looking for?

```
man ifup
man ifdown
```Hope this helps


EDIT: too slow....

---

### Post by leandromartinez98 on 2010-03-15
No, it doesn't work. Actually the wlan0 interface disapears from ifconfig. The kernel log provides a log messages like this:

[29486.924179] iwl3945 0000:06:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
[29486.945891] iwl3945 0000:06:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
[29486.968219] iwl3945 0000:06:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
[29486.985965] iwl3945 0000:06:00.0: BSM uCode verification failed at addr 0x00003800+0 (of 900), is 0xffffffff, s/b 0xf802020
[29488.984079] iwl3945 0000:06:00.0: Wait for START_ALIVE timeout after 2000ms.

---

### Post by leandromartinez98 on 2010-03-16
Just to inform, reloading the module, like:

sudo modprobe -r iwl3945 ; sudo modprobe iwl3945

does not work either.

Also I have reported a bug here, in case anyone has a similar issue:

[https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/461250](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/461250)

---

