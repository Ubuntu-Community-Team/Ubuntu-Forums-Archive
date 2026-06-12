---
title: "Network manager, multi eth0 network routing issues"
date: 2009-12-29
forum: General Help
---

### Post by nuclear216 on 2009-12-29
Something strange happened.

I have tow ethernet on my PC; eth1 is connected to my adsl router, configured as DHCP, eth0 is connected to my local LAN and ha static IP-

I never had a problem with this setup, than I installed firestarter to have little control over open ports and all continued to be fine for months, I also have virtual netowrk devices

Now, all of a sudden, I can't get the packets to be routed correctly! at first I just lost connection andn noticed I couldn't ping my router or anything else, than I noticed it was a routing problem because both connections  worked if they weren't connected at the same time, so I played with the option "use this device only for traffic on this network" in NetworkManager and it seemed to made everything work fine (still don't know why it worked wihout this option before, it makes sense it routes LAN IP 192.168 to the interface with a 192.168 IP and the same for the internet connected eth).

than is stopped working again and I have to enable "use this device only for traffic on this network" on the network I don't want to connect to (ie if I want to surf I have to enable it on Local Lan eth and viceversa).

so I am buffled, what's this????


anyway here's some info (my ISP put me behind NAT)

```
~$ route -n
Tabella di routing IP del kernel
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
172.16.112.0    0.0.0.0         255.255.255.0   U     0      0        0 vmnet8
172.16.0.0      0.0.0.0         255.255.255.0   U     0      0        0 vmnet1
192.168.0.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0
"My Internet IP"     0.0.0.0         255.255.XXX.0   U     1      0        0 eth1
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
0.0.0.0         "My Router IP"     0.0.0.0         UG    0      0        0 eth1
```

---

### Post by nuclear216 on 2010-01-02
bump

---

