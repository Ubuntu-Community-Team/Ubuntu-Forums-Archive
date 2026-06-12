---
title: "Ubuntu 8.04 Problems!!"
date: 2010-06-26
forum: General Help
---

### Post by MHarrison72 on 2010-06-26
I have recently built my own computer. While waiting for Win7, I figured I'd give Ubuntu a try. I had the 8.04 disk from a failed attempt eariler so I tried that. I was able to install everything correctly but I cannot get internet access. When I go into network, it only shows point to point, not wired connection. Any suggestions or help?

---

### Post by Leppie on 2010-06-26
if you just plug in the network cable, it doesn't work?
normally network manager should take care of this.
could you post the output of the following command:
```
ifconfig -a
```

---

### Post by MHarrison72 on 2010-06-26
I plugged the cord in and nothing happened. Now keep in mind I am completely new to linux as well.

the output is as follows:
Link encap:Local Loopback
inet addr: 127.0.0.1 Mask:255.0.0.0
inet6 addr: ::1/128 Scope:Host
UP LOOPBACK RUNNING MTU:16436 Metric:1
RX packets:1922 errors:0 dropped:0 overruns:0 frame:0
TX packets:1922 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:0
RX bytes:96100 (93.8 KB) TX bytes:96100 (93.8 KB)

---

### Post by danbuter on 2010-06-26
disable the ubuntu add-on for firefox and restart Firefox. There is something wrong with that add-on.

You may have to sudo dhclient first.

---

