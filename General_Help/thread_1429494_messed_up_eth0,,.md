---
title: "messed up eth0,,"
date: 2010-03-14
forum: General Help
---

### Post by rahilm on 2010-03-14
I have a broadband connection that once used to appear as eth0 in network manager. Yesterday I ran sudo pppoeconf just to check it out and then one thing led to another and now i eth0 doesn't appear in the list.

i am posting this via live-cd. Could someone help me to completely reset my connections?

---

### Post by DawieS on 2010-03-14
Right-click on the network icon (Top Right hand side of screen). Check that **Networking** is Enabled.

Click on "**Edit Connections**", then "**Wired**" and select "eth0" or whatever name you gave it. Select "**Edit**" and enable "**Connect Automatically**".

At the "**IPv4 Settings**" tab, at "**Method**" select "**Automatic(DHCP)**". At the "**IPv6 Settings**" tab, at "**Method**" select "**Ignore**".

---

### Post by rahilm on 2010-03-14
> **DawieS said:**
> Right-click on the network icon (Top Right hand side of screen). Check that **Networking** is Enabled.

Click on "**Edit Connections**", then "**Wired**" and select "eth0" or whatever name you gave it. Select "**Edit**" and enable "**Connect Automatically**".

At the "**IPv4 Settings**" tab, at "**Method**" select "**Automatic(DHCP)**". At the "**IPv6 Settings**" tab, at "**Method**" select "**Ignore**".

There is no eth0 in the list anymore..

---

### Post by spiky001 on 2010-03-14
can you make a new a new etho connection by add in network manager

---

### Post by efflandt on 2010-03-14
The name of connections in Network Connections is whatever name you give a connection.  Just because you deleted "Auto eth0" does not mean that you cannot **Add** a new one with that name (or whatever other name you want to give it).

But one question is whether you really need to do pppoe on your computer?  If so then you should have used the DSL tab in network connections.  If not, then you may need to figure out how to undo whatever you did with pppoeconf which may be interfering with Network Manager.

What does **ifconfig -a** show?

---

### Post by rahilm on 2010-03-14
Apparently this is the output of ifconfig -a
```
eth0      Link encap:Ethernet  HWaddr 00:19:d1:83:fe:cb  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:16 errors:0 dropped:0 overruns:0 frame:0
          TX packets:16 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:960 (960.0 B)  TX bytes:960 (960.0 B)

```
When I click networking notification icon, their are no entries just one gray line "device not managed"
when i right-click and edit connections, there is one connection in "Wired" section named ifupdown(eth0) which apparently I can neither edit not delete.
Making a new connection does not help. The only fields i have to put in is the MAC address and a DNS server. When I put them it does not work. When i restart, the connection i made is gone.

---

### Post by rahilm on 2010-03-14
I figured it out...actually found the file which got messed up. it was /etc/network/interfaces
reverted back to the one in the live-cd and done!!

---

