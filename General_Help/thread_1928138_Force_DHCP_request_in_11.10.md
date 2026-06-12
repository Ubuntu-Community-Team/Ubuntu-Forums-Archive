---
title: "Force DHCP request in 11.10"
date: 2012-02-19
forum: General Help
---

### Post by Tralce on 2012-02-19
I have had this issue a while actually. I used to request an IP from my DHCP server by this:
```
sudo dhclient eth0
```
and if I had changed the IP for that machine in the router's static leases list it would change the IP of the machine I ran the command on. For example I set up a new machine and the router always gives it an address from the pool, like 10.0.1.142. I set the card's MAC address in the static leases list to always give it the IP 10.0.1.12 and run the above command on the computer. Voila new IP. 

Not any more. As far as I can tell there's no way to do a force DHCP request in 11.04+ as it always tells me to use the reload utility but I have no %^$& idea what to reload.

Any ideas? Oh, and this HAS to work from the command line.

---

### Post by Iowan on 2012-02-19
I fought with it for awhile. My 11.10 machine *seems* to behave if I release the current address with **sudo dhclient -r**, then run **sudo dhclient eth0**
I didn't see the reload message - I just got **RTNETLINK answers: File exists**

---

### Post by Tralce on 2012-02-19
No luck. :(

```
tralce@www:~$ sudo dhclient -r
[sudo] password for tralce: 
tralce@www:~$ sudo dhclient eth0
Rather than invoking init scripts through /etc/init.d, use the service(8)
utility, e.g. service smbd reload

Since the script you are attempting to invoke has been converted to an
Upstart job, you may also use the reload(8) utility, e.g. reload smbd
RTNETLINK answers: File exists
tralce@www:~$ ifconfig eth0
eth0      Link encap:Ethernet  HWaddr 08:00:27:57:e1:eb  
          inet addr:10.0.1.142  Bcast:10.0.1.255  Mask:255.255.255.0
          inet6 addr: fe80::a00:27ff:fe57:e1eb/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1926 errors:0 dropped:0 overruns:0 frame:0
          TX packets:259 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:153359 (153.3 KB)  TX bytes:32830 (32.8 KB)

```

---

