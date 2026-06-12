---
title: "pptp routing problem."
date: 2006-04-14
forum: General Help
---

### Post by lingot on 2006-04-14
Hi,

I have install pptp according

[http://pptpclient.sourceforge.net/howto-ubuntu.phtml](http://pptpclient.sourceforge.net/howto-ubuntu.phtml)

I decided in step 9 that all my network traffic should go via the tunnel. (Which Windows XP does)

But I'm still not able to ping machine on the other side. Here are the debugging information:

# route -n (before pppd)
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 wlan0
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 wlan0

# route -n (after pppd exit)
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
xxx.xxx.xxx.xxx    0.0.0.0         255.255.255.255 UH    0      0        0 ppp0
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 wlan0
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 wlan0

# route -n (after completion)
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
xxx.xxx.xxx.xxx    192.168.1.1     255.255.255.255 UGH   0      0        0 wlan0
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 wlan0
0.0.0.0         0.0.0.0         0.0.0.0         U     0      0        0 ppp0

xxx.xxx.xxx.xxx. is the ip of my server.

It seems to be a routing problem, but I'm not sure what to look for.

Lingot

---

### Post by lingot on 2006-04-14
[HTML]I started a shell and run ifconfig and route -n, here is the result, I'm a bit confuse how the routing table changes from the one mention in the previous email.

$ ifconfig
lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:19767 errors:0 dropped:0 overruns:0 frame:0
          TX packets:19767 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:1669095 (1.5 MiB)  TX bytes:1669095 (1.5 MiB)

ppp0      Link encap:Point-to-Point Protocol
          inet addr:192.168.223.15  P-t-P:xxx.xxx.xxx.xxx  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:334  Metric:1
          RX packets:13 errors:0 dropped:0 overruns:0 frame:0
          TX packets:106505 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3
          RX bytes:172 (172.0 b)  TX bytes:18786723 (17.9 MiB)

wlan0     Link encap:Ethernet  HWaddr xx:xx:xx:xx:xx:xx
          inet addr:192.168.1.101  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: xxxx::xxx:xxxx:xxxx:xxxx/64 Scope:Link
          UP BROADCAST RUNNING  MTU:1500  Metric:1
          RX packets:3611 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3122 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:3362310 (3.2 MiB)  TX bytes:343438 (335.3 KiB)

$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
xxx.xxx.xxx.xxx 192.168.1.1     255.255.255.255 UGH   0      0        0 wlan0
xxx.xxx.xxx.xxx 0.0.0.0         255.255.255.255 UH    0      0        0 ppp0
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 wlan0

Ping to xxx.xxx.xxx.xxx works. How the routing table should look like?

Regards,

Lingot[/HTML]

---

### Post by johnny2211 on 2006-04-14
Why don't you use pptpconfig? Graphical config and everyhing is easy:-)
Or just use it to set everything up and then look what it did. 

This is the best I can come up with. Good luck.

---

### Post by lingot on 2006-04-14
I did use the pptpconfig and follow the instruction up to step 9 (inclusive).

I found the problem, the remote IP address is the same as the pptp server.

see [http://pptpclient.sourceforge.net/routing.phtml#same-ip](http://pptpclient.sourceforge.net/routing.phtml#same-ip)

So after I press start, I have to execute the following command in a shell.

$  ifconfig ppp0 pointopoint 10.0.0.1

and

$ route add default dev ppp0

I don't think there is an option in pptpconfig that verify if the ip are the same.

Thanks,

Lingot

---

### Post by lingot on 2006-05-02
It stop working again, I'm guessing that

ifconfig ppp0 pointopoint 10.0.0.1

may not work if 10.0.0.1 is already in use.

The VPN server is from Microsoft, is there a way to configure the Linux Client to detect the right remote address?

Regards,

---

