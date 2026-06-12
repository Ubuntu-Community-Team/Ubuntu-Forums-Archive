---
title: "Trouble setting static IP 11.10"
date: 2011-10-31
forum: General Help
---

### Post by guyfromfl on 2011-10-31
I am having trouble setting a static IP address.

It was working fine, until I decided to experiment with xubuntu, which in turn corrupted all sorts of config files (thank goodness I have backups).  I since have reinstalled ubuntu from the CD to try to get back to my original working config.

The problem is if I replace the backed up /etc/network/interfaces and resolv.conf, my entire networking goes out.  I can't even ping the router.

Here is whats returned on my ifconfig. There are two ethx's because I had to install a NIC since the Realtek r8169 isn't/wasn't compatible in 11.04.  The second eth0:avail just showed up at this boot.
```

eth0      Link encap:Ethernet  HWaddr 40:61:86:ca:a1:33  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:41 

eth1      Link encap:Ethernet  HWaddr 34:08:04:2d:c4:6b  
          inet addr:192.168.0.224  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::3608:4ff:fe2d:c46b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:6875 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6350 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:5180870 (5.1 MB)  TX bytes:967711 (967.7 KB)
          Interrupt:16 Base address:0x6c00 

eth0:avahi Link encap:Ethernet  HWaddr 40:61:86:ca:a1:33  
          inet addr:169.254.8.79  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Interrupt:41 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:40 errors:0 dropped:0 overruns:0 frame:0
          TX packets:40 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:4124 (4.1 KB)  TX bytes:4124 (4.1 KB)


```

eth1 is the NIC I installed, I double checked it through MAC address look up.

Currently, I am running DHCP, but would like to set my IP to 192.168.0.230 as I have security permissions on other devices that only allow me to log in on that address.  Instead of reconfiguring the whole network, I would like to restore this machine to working order.

Here is the /etc/network/interfaces I have on back up but kill my networking now:
```

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
	address 192.168.0.230
	netmask 255.255.255.0
	network 192.168.0.0
	broadcast 192.168.0.255
	gateway 192.168.0.27


```

I hope I'm missing something obvious.

Thanks in advance for the time

---

### Post by Slim Odds on 2011-10-31
> **guyfromfl said:**
> I am having trouble setting a static IP address.

It was working fine, until I decided to experiment with xubuntu, which in turn corrupted all sorts of config files (thank goodness I have backups).  I since have reinstalled ubuntu from the CD to try to get back to my original working config.

The problem is if I replace the backed up /etc/network/interfaces and resolv.conf, my entire networking goes out.  I can't even ping the router.

Here is whats returned on my ifconfig. There are two ethx's because I had to install a NIC since the Realtek r8169 isn't/wasn't compatible in 11.04.  The second eth0:avail just showed up at this boot.
```

eth0      Link encap:Ethernet  HWaddr 40:61:86:ca:a1:33  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:41 

eth1      Link encap:Ethernet  HWaddr 34:08:04:2d:c4:6b  
          inet addr:192.168.0.224  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::3608:4ff:fe2d:c46b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:6875 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6350 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:5180870 (5.1 MB)  TX bytes:967711 (967.7 KB)
          Interrupt:16 Base address:0x6c00 

eth0:avahi Link encap:Ethernet  HWaddr 40:61:86:ca:a1:33  
          inet addr:169.254.8.79  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Interrupt:41 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:40 errors:0 dropped:0 overruns:0 frame:0
          TX packets:40 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:4124 (4.1 KB)  TX bytes:4124 (4.1 KB)


```eth1 is the NIC I installed, I double checked it through MAC address look up.

Currently, I am running DHCP, but would like to set my IP to 192.168.0.230 as I have security permissions on other devices that only allow me to log in on that address.  Instead of reconfiguring the whole network, I would like to restore this machine to working order.

Here is the /etc/network/interfaces I have on back up but kill my networking now:
```

auto lo
iface lo inet loopback

auto [COLOR=Red]eth0[/COLOR]
iface [COLOR=Red]eth0 [/COLOR]inet static
    address 192.168.0.230
    netmask 255.255.255.0
    network 192.168.0.0
    broadcast 192.168.0.255
    gateway 192.168.0.27


```I hope I'm missing something obvious.

Thanks in advance for the time

Your network config says "eth0" but you say you want "eth1"

---

### Post by guyfromfl on 2011-10-31
yup, I've tried changing that. Sorry I didn't mention that in my post.

Also, is there any way to get rid of the realtek from the kernel's "eye"? (currently eth0)

I am wondering if there is a conflict with the 2 eth cards.

---

