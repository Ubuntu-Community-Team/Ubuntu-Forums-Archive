---
title: "Network issues"
date: 2006-01-28
forum: General Help
---

### Post by bobbymcsteels on 2006-01-28
Ok... I'm running win xp, Kubuntu breezy 5.10 64 and ubuntu breezy 5.10-i386, netowork/internet conection works fine with win and kubuntu but not working with ubuntu.... is there anyway I cant copy the settings from kubuntu and apply them to ubuntu??

The network connection is wired, but I have a wireless pci card which I am not using.

Any help would be great.

Cheers

---

### Post by alamba on 2006-01-28
Don't know if you can copy "settings" per se. Can be configured pretty quick though. Just boot into your kubuntu and write down you gateway, dns addresses and ip add incase its a static one.

Akshay

---

### Post by bobbymcsteels on 2006-01-28
have tried the same ip, gatway etc and have tried dhcp still no luck.

---

### Post by alamba on 2006-01-28
ok...let's troubleshoot it. 
1. system>>networking - is the interface active?
2. "ifconfig eth0" (change with your interface name). Do you get an IP?
3. "netstat -rn". Paste here.
4. Ping gateway

Akshay

---

### Post by bobbymcsteels on 2006-01-28
if i type in the modem/router ip in firefox it bruings up the modem's menu and I can access it but will try what you said now and see what I get.

---

### Post by bobbymcsteels on 2006-01-28
Ok the cable connected eth port(eth0) is enabled Typed what you said and this is what i got:-```
root@ubuntu:/home/mcsteels# ifconfig eth0
eth0      Link encap:Ethernet  HWaddr 00:11:5B:65:08:F2
          inet addr:192.168.1.48  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::211:5bff:fe65:8f2/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:35 errors:0 dropped:0 overruns:0 frame:0
          TX packets:33 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:3034 (2.9 KiB)  TX bytes:2532 (2.4 KiB)
          Interrupt:17

root@ubuntu:/home/mcsteels# netstat -rn
Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
192.168.1.0     0.0.0.0         255.255.255.0   U         0 0          0 eth0
0.0.0.0         192.168.1.1     0.0.0.0         UG        0 0          0 eth0
``` this is what I am getting from my KUBUNTU:- ```
# ifconfig eth0
eth0      Link encap:Ethernet  HWaddr 00:11:5B:65:08:F2
          inet addr:192.168.1.4  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::211:5bff:fe65:8f2/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:26864 errors:0 dropped:0 overruns:0 frame:0
          TX packets:25535 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:24873144 (23.7 MiB)  TX bytes:3148136 (3.0 MiB)
          Interrupt:17

# netstat -rn
Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
192.168.1.0     0.0.0.0         255.255.255.0   U         0 0          0 eth0
0.0.0.0         192.168.1.1     0.0.0.0         UG        0 0          0 eth0

```

---

### Post by bobbymcsteels on 2006-01-29
can any1 help me with this?

---

### Post by stream303 on 2006-01-29
Are you using a router?  If so, I'd take a look at **/etc/resolv.conf** and see if the nameserver is correctly matched to your isp's nameservers.  Kind of a hunch ...

Or just look in the network gui under the dns tab and see what the nameservers are.

This is just going on a hunch that you can ping sites by ip address, but can't resolve names for browser usage....

---

### Post by alamba on 2006-01-30
are you able to ping oracle.com? how about 4.1.1.1? incase the first fails and the second does'nt then the solution is what stream has outlined.

Akshay

---

