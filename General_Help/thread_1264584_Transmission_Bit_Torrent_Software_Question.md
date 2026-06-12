---
title: "Transmission Bit Torrent Software Question"
date: 2009-09-12
forum: General Help
---

### Post by wbee on 2009-09-12
((Yes,I did post this on the Transmission forum and received no answers.))

Hello,

I have a dual boot with Windows XP and Ubuntu JJ,32,up to date.

I use utorrent with XP and have a port manually set through my router and a firewall exception with my anitvirus software. Yes,I use a static IP. I checked a few minutes ago and my port is open.

With Ubuntu and Transmission, I could not get either the aforementioned port or a new port to open. Yes,I have an exception set through the firewall.

I did some reading and went into my router,resetting the defaults,taking out the manual routing and the static ip address. Then,I enabled the uPtoP designations,but it is was still closed.

In my network settings,it shows a loopback interface with a different number than the ethernet interface number. The ethernet interface number(including the sub mask) is the one my router recognizes. I went into transmission>preferences>web and the number is shows is the loopback number. I tried to add the ethernet number and it would not accept it;it kept defaulting back to zeros and points.

Now what should I try?

Thank you.

---

### Post by hibliss on 2009-09-12
While in Ubuntu, does the port show as open on a site like [http://canyouseeme.org]("http://canyouseeme.org")?

Post the result of:

```
/sbin/ifconfig
```

---

### Post by wbee on 2009-09-12
hibliss:

I checked that very sight and it shows it closed in Ubuntu and open in XP.

```
wbee@wbee-desktop:~$ /sbin/ifconfig
eth0      Link encap:Ethernet  HWaddr 00:16:17:11:53:d0  
          inet addr:192.168.2.2  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::216:17ff:fe11:53d0/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:7820 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8813 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:6586649 (6.5 MB)  TX bytes:1333469 (1.3 MB)
          Interrupt:20 Base address:0x6000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:20 errors:0 dropped:0 overruns:0 frame:0
          TX packets:20 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1424 (1.4 KB)  TX bytes:1424 (1.4 KB)
```

---

### Post by hibliss on 2009-09-12
Have you tried assigning a different IP in Ubuntu and forwarding a different port in the router?

Try 192.168.2.5, or if that is in the DHCP range, go outside of it. Pick some other high up port, like 44898, and forward that to the new IP.

---

### Post by wbee on 2009-09-12
Thank you. That worked. :-)

---

