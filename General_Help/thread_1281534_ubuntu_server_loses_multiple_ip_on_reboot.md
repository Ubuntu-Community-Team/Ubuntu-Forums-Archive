---
title: "ubuntu server loses multiple ip on reboot"
date: 2009-10-03
forum: General Help
---

### Post by zaphod777 on 2009-10-03
I am running ubuntu server using apache. I am learning apache and since I want to run multiple sites on this server then I need multiple ip's. I have configured the interfaces file but when I reboot and do an ifconfig I don't see the other ip's. 

the interesting thing is is i do a 

service networking restart

it works just fine.

Also I need to somehow setup so I can have multiple sites using the same public ip.

The only way I know how to do that is with a Microsoft ISA server if you know of another way let me know.

so I will forward port 80 to the ISA server and depending on what site is requested it will forward it to the respective internal website IP.

---

### Post by Brandon Williams on 2009-10-03
I suggest that you post your /etc/network/interfaces file so that we can offer suggestions about what the problem could be.

Also, this post would be better in the networking category.

---

### Post by zaphod777 on 2009-10-03
Here is my interfaces file below



root@web:~# ifconfig
eth0      Link encap:Ethernet  HWaddr 00:0c:29:a5:48:d1
          inet addr:192.168.11.6  Bcast:192.168.11.255  Mask:255.255.255.0
          inet6 addr: fe80::20c:29ff:fea5:48d1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:118 errors:0 dropped:0 overruns:0 frame:0
          TX packets:87 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:13154 (13.1 KB)  TX bytes:10510 (10.5 KB)

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

root@web:~# cd /etc/network
root@web:/etc/network# vi interfaces
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
name local ip
address 192.168.11.6
netmask 255.255.255.0
broadcast 192.168.11.255
network 192.168.1.1

auto eth0:1
iface eth0:1 inet static
name ilovemestylis.com
address 192.168.11.7
netmask 255.255.255.0
broadcast 192.168.11.255
network 192.168.1.1

auto eth0:2
iface eth0:2 inet static
name nicholas.com
address 192.168.11.8
netmask 255.255.255.0
broadcast 192.168.11.255
network 192.168.1.1


After service network restart

I get 

root@web:~# ifconfig
eth0      Link encap:Ethernet  HWaddr 00:0c:29:a5:48:d1
          inet addr:192.168.11.6  Bcast:192.168.11.255  Mask:255.255.255.0
          inet6 addr: fe80::20c:29ff:fea5:48d1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:422 errors:0 dropped:0 overruns:0 frame:0
          TX packets:349 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:39659 (39.6 KB)  TX bytes:43315 (43.3 KB)

eth0:1    Link encap:Ethernet  HWaddr 00:0c:29:a5:48:d1
          inet addr:192.168.11.7  Bcast:192.168.11.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1

eth0:2    Link encap:Ethernet  HWaddr 00:0c:29:a5:48:d1
          inet addr:192.168.11.8  Bcast:192.168.11.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:6 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:804 (804.0 B)  TX bytes:804 (804.0 B)

root@web:~#

---

### Post by Brandon Williams on 2009-10-03
I doubt this has anything to do with the problem you describe, but the network value for each of your interfaces is incorrect. It should be 192.168.11.0.

All the rest looks reasonable. This makes me think that there may be an ordering issue, since eth0 must be up before eth0:1 and eth0:2 can be defined. All the examples I've seen list all three interfaces on the same auto line, as in:
```
auto eth0 eth0:1 eth0:2
```

Maybe listing all three on the auto line like that will get around the ordering problem, if that's what it is.

---

### Post by zaphod777 on 2009-10-03
your awesome! I would have never thought of that. 


Fixing the network thing didn't help but putting the eth0 line all together worked perfect. Who would have thought.

Now I just need to learn ISA or find a good free load balancer that will recognize the domain name requested and forward it to the correct IP I will be set.

---

### Post by dcstar on 2009-10-03
> **zaphod777 said:**
> 
.......
Also I need to somehow setup so I can have multiple sites using the same public ip.

The only way I know how to do that is with a Microsoft ISA server if you know of another way let me know.

so I will forward port 80 to the ISA server and depending on what site is requested it will forward it to the respective internal website IP.

AFAIK Apache has that built in using the function to forward requests to other web servers.

You will have to research the details yourself.

---

### Post by zaphod777 on 2009-10-03
cool that will make life easier I will check it out.

---

