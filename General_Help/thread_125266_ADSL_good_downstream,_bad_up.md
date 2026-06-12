---
title: "ADSL good downstream, bad up"
date: 2006-02-03
forum: General Help
---

### Post by martal on 2006-02-03
My ADSL connection is fine in my XP partition, 512/256 less overheads. Similar downstream speed in Ubuntu, upstream is 3/4 KB. :???: 

3Com wireless router, Realtek NIC. Any ideas?

Determined by the Java test at adslguide.co.uk

---

### Post by Horndog on 2006-02-03
That test requires a java applet, Is it loaded in ubuntu? That applet is responsible for sending packets upstream for the test site to calculate speeds.

---

### Post by martal on 2006-02-03
OK, how can I test that Java is working correctly? It's from the Automatix package and gives an expected download speed.

---

### Post by Horndog on 2006-02-03
If you have it loaded them it should work. I don't know how to test it. Are you using a firewall? I just tested my connection just to make sure it works in ubuntu, and it does. Just for curiosity why don't you try a different site.

---

### Post by dcstar on 2006-02-03
[QUOTE=martal]My ADSL connection is fine in my XP partition, 512/256 less overheads. Similar downstream speed in Ubuntu, upstream is 3/4 KB. :???: 

3Com wireless router, Realtek NIC. Any ideas?

Determined by the Java test at adslguide.co.uk[/QUOTE]
In a terminal, do:

ifconfig

and see if there are any reported errors etc. on the TX packets.

If there are, you may want to use "ethtool" to try changing things to try and resolve the problem.

---

### Post by martal on 2006-02-04
ifconfig output after a short web session:

eth0      Link encap:Ethernet  HWaddr 00:0E:2E:56:9F:BB
          inet addr:192.168.1.2  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::20e:2eff:fe56:9fbb/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:6595 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4788 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:8711927 (8.3 MiB)  TX bytes:395569 (386.2 KiB)
          Interrupt:17 Base address:0xa800

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:82583 errors:0 dropped:0 overruns:0 frame:0
          TX packets:82583 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:5147885 (4.9 MiB)  TX bytes:5147885 (4.9 MiB)

I don't know how to interpret this.

---

### Post by dcstar on 2006-02-04
[QUOTE=martal]ifconfig output after a short web session:

eth0      Link encap:Ethernet  HWaddr 00:0E:2E:56:9F:BB
          inet addr:192.168.1.2  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::20e:2eff:fe56:9fbb/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:6595 **errors:0 dropped:0 overruns:0** frame:0
          TX packets:4788 **errors:0 dropped:0 overruns:0** carrier:0
          collisions:0 txqueuelen:1000
......
I don't know how to interpret this.[/QUOTE]
It shows that there were no problems with the physical LAN connection between your PC and your router, so you can cross that off the list as a possible cause of your issue.

I would do a forum search for "disable IPv6" and try those solutions.

---

