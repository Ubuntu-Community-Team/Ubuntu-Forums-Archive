---
title: "Wired network acting strange..."
date: 2011-07-15
forum: General Help
---

### Post by jeremythuff on 2011-07-15
Hey folks,

I am brand new to Linux and Ubuntu. I have recently installed 11.4 on my pc, and everything has been going pretty good. Initially my wired connection was indicated in the top left hand of the screen by two opposing parallel arrows.

After downloading some updates that changed. Now it shows an empty wireless wedge, and does not seem to register a connection at all. When I select connection information it tells me "Error displaying connection information: No valid active connections found!"


The strange thing is that I AM connected. i am online right now. 

Odd...Any help?

---

### Post by KeyserSoze93 on 2011-07-15
Try opening a terminal  and running:

```

ip addr

```

This should tell you whether the system is seeing your network card - it is possibly that the settings for it could have got corrupted somewhere. 

Next, run:

```

nm-tool

```

This should tell you whether the Ubuntu network management software can see your card.

Post the output of those two commands.

---

### Post by jeremythuff on 2011-07-15
The first returned:

~$ ip addr
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 16436 qdisc noqueue state UNKNOWN 
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
    inet6 ::1/128 scope host 
       valid_lft forever preferred_lft forever
2: eth0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc pfifo_fast state UNKNOWN qlen 1000
    link/ether 00:15:f2:d9:b0:fa brd ff:ff:ff:ff:ff:ff
    inet 192.168.1.7/24 brd 192.168.1.255 scope global eth0
    inet6 fe80::215:f2ff:fed9:b0fa/64 scope link 
       valid_lft forever preferred_lft forever

The second:

~$ nm-tool

NetworkManager Tool

State: connected

- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            skge
  State:             unmanaged
  Default:           no
  HW Address:        00:15:F2:D9:B0:FA

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

---

### Post by Hugh971 on 2011-07-15
looks like it's not connected to the network. Try clicking on the network icon on the panel and clicking on your network adaptor (probably labelled 'Auto eth0').

If that doesn't work post the output of

```
ifconfig
```

---

### Post by jeremythuff on 2011-07-16
I do not see my network in that location.

ifconfig
eth0      Link encap:Ethernet  HWaddr 00:15:f2:d9:b0:fa  
          inet addr:192.168.1.5  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::215:f2ff:fed9:b0fa/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:153 errors:0 dropped:0 overruns:0 frame:0
          TX packets:193 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:65040 (65.0 KB)  TX bytes:32379 (32.3 KB)
          Interrupt:21 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:133 errors:0 dropped:0 overruns:0 frame:0
          TX packets:133 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:6923 (6.9 KB)  TX bytes:6923 (6.9 KB)





I also realized that I ran something awhile back called: application://xfld-xnetcardconfig.desktop

In an attempt to get my wireless card working. 

That probably had something to do with this.

---

