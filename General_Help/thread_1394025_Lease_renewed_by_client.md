---
title: "Lease renewed by client"
date: 2010-01-30
forum: General Help
---

### Post by jmore9 on 2010-01-30
Anyone know what Lease 192.168.0.119 renewed by client 0007950BB066 means.  I have had comcast internet for years and have never seen this before.

I am mostly wanting to know what the Lease renewed by client 0007950BB066 means ?  How to find out who client 0007950BB066 is ?

Thanks in advance for your time

---

### Post by 3rdalbum on 2010-01-30
I imagine it's a "DHCP lease". When your computer connects to a network it needs an IP address that's not currently in use, so it contacts your router/modem (which has a DHCP server in it) and asks for an IP address and some other important information.

If your computer crashes, it can't exactly tell the router to release the previous IP address, so instead they use a "lease" system. The computer has to contact the router every so often to "renew the lease". If the period of time goes by without the computer renewing the lease, the router will release the IP address for allocation to another device.

That's all it is. You don't even need to know this, but I thought I'd explain it to you to ease your mind. It's perfectly normal.

---

### Post by gmargo on 2010-02-01
> I am mostly wanting to know what the Lease renewed by client  0007950BB066 means ?  How to find out who client 0007950BB066 is ?0007950BB066 most likely refers to your MAC address, and would normally be written as "00:07:95:0B:B0:66".

You can see your own machine's MAC address with the "ifconfig" command.  You can see other MAC addresses that your machine currently knows about with the "arp" command.

Generally the first 12-bits of the MAC address are assigned to a particular vendor.  The assignments can be found in [http://standards.ieee.org/regauth/oui/oui.txt](http://standards.ieee.org/regauth/oui/oui.txt)

00:07:95 is assigned to 

> 00-07-95   (hex)        Elitegroup Computer System Co. (ECS)
000795     (base 16)        Elitegroup Computer System Co. (ECS)
                No. 22, Alley 38, Lane 91,
                Sec. 1, Nei Hu Road
                Taipei  114
                TAIWAN, REPUBLIC OF CHINA

---

