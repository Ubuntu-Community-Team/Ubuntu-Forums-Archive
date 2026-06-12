---
title: "DNS Problem."
date: 2006-02-17
forum: General Help
---

### Post by adam3223 on 2006-02-17
I installed ubuntu 5.1 yesterday, and today i added a Belkin Wireless pci card with the rt2500 chipset.

It works fine, it connects, and i can access websites , but only directly from thier IP.

Extract from terminal:
[FONT="Courier New"]root@server:~# ifconfig
eth0      Link encap:Ethernet  HWaddr 00:0D:87:44:4F:7E
          inet addr:192.168.2.203  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::20d:87ff:fe44:4f7e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:333 errors:0 dropped:0 overruns:0 frame:0
          TX packets:356 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:60149 (58.7 KiB)  TX bytes:40734 (39.7 KiB)
          Interrupt:19 Base address:0xd400

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:12641 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12641 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:1145727 (1.0 MiB)  TX bytes:1145727 (1.0 MiB)

ra0       Link encap:Ethernet  HWaddr 00:11:50:90:76:CD
          inet addr:192.168.1.203  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::211:50ff:fe90:76cd/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:222 errors:0 dropped:0 overruns:0 frame:0
          TX packets:742 errors:0 dropped:0 overruns:0 carrier:0
          collisions:14 txqueuelen:1000
          RX bytes:22942 (22.4 KiB)  TX bytes:45088 (44.0 KiB)
          Interrupt:18



root@server:~# cat /etc/network/interfaces
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
        script grep
        map eth0

# The primary network interface
iface ra0 inet static
address 192.168.1.203
netmask 255.255.255.0
gateway 192.168.1.1
wireless-essid 3223NETWORK

auto ra0


iface eth0 inet static
address 192.168.2.203
netmask 255.255.255.0

auto eth0


root@server:/etc# cat resolv.conf
nameserver 194.168.100.8
nameserver 194.166.100.4


root@server:~# ping 192.168.1.1
PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data.
64 bytes from 192.168.1.1: icmp_seq=1 ttl=150 time=1.38 ms
64 bytes from 192.168.1.1: icmp_seq=2 ttl=150 time=1.38 ms
64 bytes from 192.168.1.1: icmp_seq=3 ttl=150 time=1.40 ms
--- 192.168.1.1 ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2001ms
rtt min/avg/max/mdev = 1.381/1.389/1.400/0.031 ms

root@server:~# ping google.com

root@server:~# ping 194.168.100.8
PING 194.168.100.8 (194.168.100.8) 56(84) bytes of data.
--- 194.168.100.8 ping statistics ---
182 packets transmitted, 0 received, 100% packet loss, time 180972ms[/FONT]

As you can see i cannot ping the DNS at 194.168.100.8.

Does any one know why??

---

### Post by kaamos on 2006-02-17
Have you checked that these
> 
root@server:/etc# cat resolv.conf
nameserver 194.168.100.8
nameserver 194.166.100.4
are correct? You isp should be able to provide you with the info.

---

### Post by adam3223 on 2006-02-17
They are, my windows pc is running with the same ones.

---

