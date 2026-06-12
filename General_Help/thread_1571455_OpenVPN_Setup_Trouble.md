---
title: "OpenVPN Setup Trouble"
date: 2010-09-09
forum: General Help
---

### Post by pwhipped on 2010-09-09
I'm following this guide [https://help.ubuntu.com/10.04/serverguide/C/openvpn.html](https://help.ubuntu.com/10.04/serverguide/C/openvpn.html)

I am trying to use a bridge to vpn from work to home.

/etc/network/interfaces
# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto br0
iface br0 inet dhcp
        bridge_ports eth0

iface eth0 inet manual
        up ifconfig $IFACE 0.0.0.0 up
        up ip link set $IFACE promisc on
        down ip link set $IFACE promisc off
        down ifconfig $IFACE down

I am forced to use dhcp because of my router. (although it is a static lease) I think this is where I am hung up. Everything else seems to be working properly though. I have a windows client connecting but is limited to the server serving out openvpn. (192.168.1.21) In other words it is not functioning as a bridged vpn service.

ifconfig

br0       Link encap:Ethernet  HWaddr 00:0c:29:de:dc:c4
          inet addr:192.168.1.21  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::20c:29ff:fede:dcc4/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:597 errors:0 dropped:0 overruns:0 frame:0
          TX packets:406 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:85803 (85.8 KB)  TX bytes:66745 (66.7 KB)

eth0      Link encap:Ethernet  HWaddr 00:0c:29:de:dc:c4
          inet6 addr: fe80::20c:29ff:fede:dcc4/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:9912 errors:0 dropped:0 overruns:0 frame:0
          TX packets:7399 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:1327709 (1.3 MB)  TX bytes:1339967 (1.3 MB)
          Interrupt:18 Base address:0x1400

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

tap0      Link encap:Ethernet  HWaddr 96:b0:3f:60:04:85
          inet6 addr: fe80::94b0:3fff:fe60:485/64 Scope:Link
          UP BROADCAST RUNNING PROMISC MULTICAST  MTU:1500  Metric:1
          RX packets:41 errors:0 dropped:0 overruns:0 frame:0
          TX packets:81 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:100
          RX bytes:5389 (5.3 KB)  TX bytes:29831 (29.8 KB)

openvpn server.conf
local 192.168.1.21
port 1199
proto udp
dev tap0
up "/etc/openvpn/up.sh br0"
down "/etc/openvpn/down.sh br0"
ca ca.crt
cert server.crt
key server.key  # This file should be kept secret
dh dh1024.pem
ifconfig-pool-persist ipp.txt
server-bridge 192.168.1.21 255.255.255.0 192.168.1.100 192.168.1.200
keepalive 10 120
tls-auth ta.key 0 # This file is secret
comp-lzo
user nobody
group nogroup
persist-key
persist-tun
status openvpn-status.log
verb 3

Thanks for any help given ahead of time. I have been working on this for days and am just completely stumped.

---

### Post by pwhipped on 2010-09-09
Bump for night crowd.

---

### Post by pwhipped on 2010-09-10
Last bump before giving up.

---

