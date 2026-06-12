---
title: "Need help with wired connection"
date: 2012-02-23
forum: General Help
---

### Post by PyGuy on 2012-02-23
Hello everyone. I just started dual-booting with W7 and Ubuntu 11.10 last night and my internet worked great, but today, it keeps disconnecting when I try to connect. Here's what I saw when I typed "ifconfig" in the terminal:

eth0
Link encap:Ethernet HWaddr bc:5f:f4:1a:b3:8d
inet6 addr: fe80::be5f:f4ff:fe1a:b38d/64 Scope:Link
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
RX packets:12 errors:0 dropped:14 overruns:0 frame:12
TX packets:285 errors:0 dropped:98 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:4482 (4.4 KB) TX bytes:60739 (60.7 KB)
Interrupt:45 Base address:0xa000

lo
Link encap:Local Loopback
inlet addr: ::1/128 Scope:Host
UP LOOPBACK RUNNING MTU:16436 Metric:1
RX packets:144 errors:0 dropped:0 overruns:0 frame:0
TX packets:144 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:0
RX bytes:11488 (11.4 KB) TX bytes:11488 (11.488 KB)

Thanks in advance,
Andrew

---

### Post by Jimoid on 2012-02-23
Hi Andrew,

Welcome to Ubuntu. The [FONT="Courier New"]ifconfig[/FONT] output you gave shows that you have not been assigned an IPv4 IP address for eth0 (your wired connection), so you cannot connect to a network.

The easiest way to set up a network connection is using the Network Connections GUI, which is available from either typing network into the dash search, or typing [FONT="Courier New"]nm-connection-editor[/FONT] into a terminal.

Add a new wired connection and fill in the appropriate details. Most likely you will want a DHCP address (from the "IPv4 Settings" tab) if you are on a home broadband connection, otherwise you will need to add specific details for a static address, but you will probably know these in that case. The best advice would be for you to play around with the settings until you find what works for you.

Hope this helps,

Jimmy

---

