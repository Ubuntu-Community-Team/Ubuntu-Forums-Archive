---
title: "Cannot Connect To Internet"
date: 2006-06-15
forum: General Help
---

### Post by jasrog on 2006-06-15
What displays when I type ifconfig is this:
eth0 Link encap: Ethernet HWADDR 00:40:CA:93:76:AC Inet6 addr:fe80:240:caff:fe 93:76ac/64 Scope:Link UP Broadcast Running Multicast MTU:1500 Metric:1 Rx packets:1822 errors 0 dropped 0 overruns 0 frame:0 tx packets 0 errors0 dropped 0 overruns 0 carrier 0 collisions 0 txqueuelen:1000 rx bytes 111598 (108.9Kib) tx bytes:0 (0.06) interrupt:217

lo Link encap:LOCAL LOOPBACK
inet addr:127.0.0.1 Mask 255.0.0.0
inet6 addr: ::1/128 Scope:Host
UP LOOPBACK RUNNING MTU:16436 Metric:1
Rx Packets: 87 errors 0 dropped 0 overruns 0 frame 0
Rx bytes:6338 (6.2kib) Tx bytes:6388 (6.2kib)

Is this the problem?

---

### Post by Brunellus on 2006-06-15
check your ethernet cable--is it plugged-in?

also, check that your router supports DHCP.

---

### Post by jasrog on 2006-06-15
It's plugged in and my cable modem supports DHCP....now what?

---

### Post by Brunellus on 2006-06-15
execute

sudo dhclient eth0

and see what happens.

---

### Post by jasrog on 2006-06-16
What I got now Brunellis is NO DHCPOFFERS received  No working leases in persistent database-sleeping.???

---

### Post by jasrog on 2006-06-17
Can anybody help?

---

### Post by Brunellus on 2006-06-18
Seems a bit strange.  do you know what the IP of your router is?  If you do, then set that to be the default gateway IP in the networking setup GUI (SYSTEM>ADMINISTRATION>NETWORKING).  Then see how it works.

---

### Post by jasrog on 2006-06-19
It's just a cable modem that automatically gets IP address.

---

