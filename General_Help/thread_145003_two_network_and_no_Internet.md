---
title: "two network and no Internet"
date: 2006-03-15
forum: General Help
---

### Post by jgregory on 2006-03-15
I've done some searching on the forum, but haven't quite found what I needed. I'm running Edubuntu Breezy. I've got two network cards and no Internet at boot. When I disable and re-enable  eth2, Internet works. This sets the default gateway interface to eth1. Can I fix this in my interfaces file? /etc/network/interfaces is configured like so:

```
auto lo
iface lo inet loopback

auto eth1
iface eth1 inet dhcp

mapping hotplug
	script grep
	map eth2

iface eth2 inet static
	address 192.168.0.1
	netmask 255.255.255.0
	network 192.168.0.0
	broadcast 192.168.0.255
	gateway 192.168.0.1
	# dns-* options are implemented by the resolvconf package, if installed
	dns-nameservers 192.168.0.1
```

eth1 gets a DHCP IP from a router, eth2 is the gateway for my LTSP subnet. 

route gives me the following at boot:

```
john@edubuntu:~$ route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     *               255.255.255.0   U     0      0        0 eth1
localnet        *               255.255.255.0   U     0      0        0 eth2
default         edubuntu        0.0.0.0         UG    0      0        0 eth2
default         192.168.1.1     0.0.0.0         UG    0      0        0 eth1
```


ifconfig gives me:

```
john@edubuntu:~$ ifconfig
eth1      Link encap:Ethernet  HWaddr 00:E0:29:70:26:73
          inet addr:192.168.1.100  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::2e0:29ff:fe70:2673/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1238 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1141 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:921443 (899.8 KiB)  TX bytes:155332 (151.6 KiB)
          Interrupt:10 Base address:0xd800

eth2      Link encap:Ethernet  HWaddr 00:04:76:39:68:8C
          inet addr:192.168.0.1  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::204:76ff:fe39:688c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:150 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:14782 (14.4 KiB)
          Interrupt:3 Base address:0xdc00

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:11122 errors:0 dropped:0 overruns:0 frame:0
          TX packets:11122 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:1011963 (988.2 KiB)  TX bytes:1011963 (988.2 KiB)
```

I'm sure that I'm missing something simple... any ideas?

TIA - John

---

### Post by Stormbringer on 2006-03-15
There's one thing coming into my mind: Is IP-Forwarding between the interfaces enabled?

# cat /proc/sys/net/ipv4/ip_forward

If you get a "0" it isn't. Issue...

# sudo echo "1" > /proc/sys/net/ipv4/ip_forward

...and give it a try.

If it works you can make it permanent by editing /etc/sysctl.conf:

# sudo gedit /etc/sysctl.conf
Add the following line:

sys.net.ipv4.ip_forward=1

Save the file.
Either restart networking or reboot.

Storm.

---

### Post by jgregory on 2006-03-20
I found the answer to my problem. You can't have two gateways. I thought I could have a gateway for each interface... But I guess not. When I got rid the the gateway for eth2 in interfaces, it worked.

Thanks for your suggestion.

John

---

