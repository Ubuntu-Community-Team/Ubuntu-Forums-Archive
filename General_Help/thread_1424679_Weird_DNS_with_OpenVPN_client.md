---
title: "Weird DNS with OpenVPN client"
date: 2010-03-08
forum: General Help
---

### Post by artheus on 2010-03-08
Hi!

I've got a little problem with my OpenVPN configuration.

When I connect with a client with these settings :

```
client

dev tap

remote domain.org 1194

nobind

resolv-retry infinite

persist-key
persist-tun

ca ca.crt
cert myusername.crt
key myusername.key

tls-auth ta.key 1

cipher BF-CBC

comp-lzo

ns-cert-type server

verb 3
```

the dns starts acting a little weird.

When I try to use ssh, or Putty in Windows, and I write in the hostname www9, which is in my local network, it will try to connect to www9 on the remote vpn network.

Same thing if I use firefox, and I want to go to Googles home-page. I usually just write "google" in the url bar. But when I hit enter, it tries to connect to hostname "google" on the remote vpn network.

I don't know if this should probably be in a Windows forum, as I am connecting from Windows to a Ubuntu vpn server. But the config comes from Ubuntu documents. So I posted here.

Hope someone knows how to solve this problem, It's really irritating.

Thanks,
Artheus

---

### Post by The Cog on 2010-03-08
I wonder if the VPN server is pushing a new DNS server to the client. If you try "ping www9" both with and without the VPN connected, does it try to ping different addresses?

Or do you mean that your default route is changing so that your connection attempts to the same IP address is going up the VPN when is shouldn't. Looking at the output of the command "route print" both with and without the VPN should help understand what's going on.

---

### Post by artheus on 2010-03-08
Windows ping output of www9 ping :

```

Microsoft Windows [Version 6.1.7600]
Copyright (c) 2009 Microsoft Corporation.  All rights reserved.

C:\Users\Artheus>ping www9

Pinging www9 [192.168.0.196] with 32 bytes of data:
Reply from 192.168.0.196: bytes=32 time=69ms TTL=64
Reply from 192.168.0.196: bytes=32 time=32ms TTL=64
Reply from 192.168.0.196: bytes=32 time=40ms TTL=64
Reply from 192.168.0.196: bytes=32 time=40ms TTL=64

Ping statistics for 192.168.0.196:
    Packets: Sent = 4, Received = 4, Lost = 0 (0% loss),
Approximate round trip times in milli-seconds:
    Minimum = 32ms, Maximum = 69ms, Average = 45ms

# TURNING OFF OPENVPN

C:\Users\Artheus>ping www9

Pinging www9 [192.168.0.196] with 32 bytes of data:
Request timed out.
Request timed out.
Request timed out.
Request timed out.

Ping statistics for 192.168.0.196:
    Packets: Sent = 4, Received = 0, Lost = 4 (100% loss),

```

---

### Post by The Cog on 2010-03-08
Sounds like a routing issue then. Can you post the output of "route print" both with and without the VPN running?

Do you have control over the VPN server or is it someone else's?

---

### Post by artheus on 2010-03-08
> **The Cog said:**
> Sounds like a routing issue then. Can you post the output of "route print" both with and without the VPN running?

Do you have control over the VPN server or is it someone else's?


With vpn
```

===========================================================================
Interface List
 24...02 23 54 0e 99 82 ......MAC Bridge Miniport
 17...00 ff bf f6 e2 e1 ......TAP-Win32 Adapter V9
 23...08 00 27 00 3c 16 ......VirtualBox Host-Only Ethernet Adapter
  1...........................Software Loopback Interface 1
 12...00 00 00 00 00 00 00 e0 Microsoft ISATAP Adapter
 14...00 00 00 00 00 00 00 e0 Microsoft ISATAP Adapter #2
 15...00 00 00 00 00 00 00 e0 Microsoft 6to4 Adapter
 16...00 00 00 00 00 00 00 e0 Teredo Tunneling Pseudo-Interface
 20...00 00 00 00 00 00 00 e0 Microsoft ISATAP Adapter #4
===========================================================================

IPv4 Route Table
===========================================================================
Active Routes:
Network Destination        Netmask          Gateway       Interface  Metric
          0.0.0.0          0.0.0.0       198.0.0.60       198.0.0.91     10
        127.0.0.0        255.0.0.0         On-link         127.0.0.1    306
        127.0.0.1  255.255.255.255         On-link         127.0.0.1    306
  127.255.255.255  255.255.255.255         On-link         127.0.0.1    306
      169.254.0.0      255.255.0.0         On-link        198.0.0.91    286
   169.254.245.71  255.255.255.255         On-link    169.254.245.71    276
  169.254.255.255  255.255.255.255         On-link        198.0.0.91    266
      192.168.0.0    255.255.255.0         On-link     192.168.0.103    286
    192.168.0.103  255.255.255.255         On-link     192.168.0.103    286
    192.168.0.255  255.255.255.255         On-link     192.168.0.103    286
        198.0.0.0    255.255.255.0         On-link        198.0.0.91    266
       198.0.0.91  255.255.255.255         On-link        198.0.0.91    266
      198.0.0.255  255.255.255.255         On-link        198.0.0.91    266
        224.0.0.0        240.0.0.0         On-link         127.0.0.1    306
        224.0.0.0        240.0.0.0         On-link        198.0.0.91    266
        224.0.0.0        240.0.0.0         On-link     192.168.0.103    286
        224.0.0.0        240.0.0.0         On-link    169.254.245.71    276
  255.255.255.255  255.255.255.255         On-link         127.0.0.1    306
  255.255.255.255  255.255.255.255         On-link        198.0.0.91    266
  255.255.255.255  255.255.255.255         On-link     192.168.0.103    286
  255.255.255.255  255.255.255.255         On-link    169.254.245.71    276
===========================================================================
Persistent Routes:
  None

IPv6 Route Table
===========================================================================
Active Routes:
 If Metric Network Destination      Gateway
 15   1110 ::/0                     2002:c058:6301::c058:6301
  1    306 ::1/128                  On-link
 15   1010 2002::/16                On-link
 15    266 2002:c600:5b::c600:5b/128
                                    On-link
 24    266 fe80::/64                On-link
 17    286 fe80::/64                On-link
 23    276 fe80::/64                On-link
 12    266 fe80::200:5efe:198.0.0.91/128
                                    On-link
 23    276 fe80::c49e:4965:875f:f547/128
                                    On-link
 17    286 fe80::e1b9:c4ff:464:b3a0/128
                                    On-link
 24    266 fe80::e924:a1cf:e236:469/128
                                    On-link
  1    306 ff00::/8                 On-link
 24    266 ff00::/8                 On-link
 17    286 ff00::/8                 On-link
 23    276 ff00::/8                 On-link
===========================================================================
Persistent Routes:
  None

```

And without VPN

```
===========================================================================
Interface List
 24...02 23 54 0e 99 82 ......MAC Bridge Miniport
 17...00 ff bf f6 e2 e1 ......TAP-Win32 Adapter V9
 23...08 00 27 00 3c 16 ......VirtualBox Host-Only Ethernet Adapter
  1...........................Software Loopback Interface 1
 12...00 00 00 00 00 00 00 e0 Microsoft ISATAP Adapter
 14...00 00 00 00 00 00 00 e0 Microsoft ISATAP Adapter #2
 15...00 00 00 00 00 00 00 e0 Microsoft 6to4 Adapter
 16...00 00 00 00 00 00 00 e0 Teredo Tunneling Pseudo-Interface
 20...00 00 00 00 00 00 00 e0 Microsoft ISATAP Adapter #4
===========================================================================

IPv4 Route Table
===========================================================================
Active Routes:
Network Destination        Netmask          Gateway       Interface  Metric
          0.0.0.0          0.0.0.0       198.0.0.60       198.0.0.91     10
        127.0.0.0        255.0.0.0         On-link         127.0.0.1    306
        127.0.0.1  255.255.255.255         On-link         127.0.0.1    306
  127.255.255.255  255.255.255.255         On-link         127.0.0.1    306
      169.254.0.0      255.255.0.0         On-link        198.0.0.91    286
   169.254.245.71  255.255.255.255         On-link    169.254.245.71    276
  169.254.255.255  255.255.255.255         On-link        198.0.0.91    266
        198.0.0.0    255.255.255.0         On-link        198.0.0.91    266
       198.0.0.91  255.255.255.255         On-link        198.0.0.91    266
      198.0.0.255  255.255.255.255         On-link        198.0.0.91    266
        224.0.0.0        240.0.0.0         On-link         127.0.0.1    306
        224.0.0.0        240.0.0.0         On-link        198.0.0.91    266
        224.0.0.0        240.0.0.0         On-link    169.254.245.71    276
  255.255.255.255  255.255.255.255         On-link         127.0.0.1    306
  255.255.255.255  255.255.255.255         On-link        198.0.0.91    266
  255.255.255.255  255.255.255.255         On-link    169.254.245.71    276
===========================================================================
Persistent Routes:
  None

IPv6 Route Table
===========================================================================
Active Routes:
 If Metric Network Destination      Gateway
 15   1110 ::/0                     2002:c058:6301::c058:6301
  1    306 ::1/128                  On-link
 15   1010 2002::/16                On-link
 15    266 2002:c600:5b::c600:5b/128
                                    On-link
 24    266 fe80::/64                On-link
 23    276 fe80::/64                On-link
 23    276 fe80::c49e:4965:875f:f547/128
                                    On-link
 24    266 fe80::e924:a1cf:e236:469/128
                                    On-link
  1    306 ff00::/8                 On-link
 24    266 ff00::/8                 On-link
 23    276 ff00::/8                 On-link
===========================================================================
Persistent Routes:
  None
```

---

### Post by artheus on 2010-03-08
The VPN Server is under my full control.

---

### Post by The Cog on 2010-03-09
You have a routing conflict. The server www9 is at address 192.168.0.196 (not your local network, but presumably via your default gateway which is 198.0.0.60). However, it seems that the VPN is giving you a locally connected network 192.168.0.x whenever you connect to the VPN, and this is of course taking precedence over your default route. The VPN network includes the address of www9 so that www9 appears to be connected locally, on the VPN network. 

I would suggest that you reconfigure your VPN server so that it gives you a different network number for the VPN connection itself. Something that is not used elsewhere in your network, maybe 192.168.199.x as a guess.

---

### Post by artheus on 2010-03-09
The vpn server config looks like this :

```

mode server
tls-server

local 192.168.0.196
port 1194
proto udp

dev tap0
up "/etc/openvpn/up.sh br0"
down "/etc/openvpn/down.sh br0"

persist-key
persist-tun

ca ca.crt
cert server.crt
key server.key 
dh dh1024.pem
tls-auth ta.key 0

cipher BF-CBC
comp-lzo

ifconfig-pool-persist ipp.txt
server-bridge 192.168.0.196 255.255.255.0 192.168.0.100 192.168.0.199
push "dhcp-option DNS 192.168.0.1"
push "dhcp-option DOMAIN domain.com"
max-clients 10

user nobody
group nogroup
keepalive 10 120
status openvpn-status.log
verb 3

```

I am a newbie on VPN.. So I would really appreciate the help on how to make the changes in my vpn config too.

To set it up I used [https://help.ubuntu.com/community/OpenVPN](https://help.ubuntu.com/community/OpenVPN)

Thanks,
Artheus

---

### Post by The Cog on 2010-03-10
The IP address that the client is trying to connect to isn't 192.168.0.196
is it? If so then things won't work because as soon as the VPN comes up, then the VPN is a better way to talk to the VPN server than the real connection, so it tries to use the VPN to make the VPN work, and disappears in a circle. The ubuntu example you show uses NAT to hide the VPN server's local address, so that the VPN doesn't start eating its own tail. Actually, I can't think how such bridging could work without NAT (or a dual-homed VPN server) to separate the real path from the VPN LAN.

Is 192.168.0.196 the correct IP address for www9, or is this a wrong address that the VPN name resolution is making you see?
Does network 192.168.0.x exist at both sites?

---

