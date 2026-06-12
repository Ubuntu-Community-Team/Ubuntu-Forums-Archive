---
title: "ifconfig question"
date: 2006-06-30
forum: General Help
---

### Post by evaristegalois on 2006-06-30
my internet service provider just hooked me up with an internet line (cable). they will do technical support if you run windows or apple but not linux. it didn't work, neither on my ubuntu machine nor on my roommate's windows xp machine. we called them and they made us type

netsh winsock reset catalog

on the DOS shell which fixed the problem for the windows machine. But my ubuntu machine still doesn't work. what would be the equivalent for the above command?

This is what I get when I type "ifconfig eth1" on my terminal:

[COLOR="Red"]eth1      Link encap:Ethernet  HWaddr 00:06:1B:D3:1B:D2  
          inet6 addr: fe80::206:1bff:fed3:1bd2/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:88056 errors:0 dropped:0 overruns:0 frame:0
          TX packets:50 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:5585654 (5.3 MiB)  TX bytes:11820 (11.5 KiB)[/COLOR]

with the modem cable plugged into my computer and eth1 (ethernet connection) activated

--evaristegalois

---

### Post by invalid on 2006-06-30
Try resetting the connection:
```
sudo ifdown eth1
sudo ifup eth1
```

---

### Post by woedend on 2006-06-30
i would suggest that also. 
(if you are using a router, disregard the rest, but in case...)
 2 things to note - 
If you are plugging directly from the modem to the computer, it may be one of 2 things -

1 - some companies require you to unplug the power from the modem for about 30 seconds, then plug it back in AFTER connecting the cord to a different device


2 - some companies require you to call and register your machine with them in order for it to work.

---

