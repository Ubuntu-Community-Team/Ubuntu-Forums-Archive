---
title: "Losing DNS eventually"
date: 2006-03-27
forum: General Help
---

### Post by pacman^ on 2006-03-27
Hello and thanks for the forum. 

I've got a problem: my ISP gives the DNS servers in the DHCP package. I use an external ethernet ADSL modem and ethernet card so the interface is eth0. As I read from another thread, I wrote some magic commands to the terminal and got following:

```

:~$less /etc/hosts

127.0.0.1       localhost.localdomain   localhost       a81-197-47-177

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

```

```

:~$ less /etc/resolv.conf

search elisa-laajakaista.fi
nameserver 193.229.0.40
nameserver 193.229.0.42

```

```

:~$ less /etc/network/interfaces

# The loopback network interface
auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
        script grep
        map eth0

# The primary network interface
iface eth0 inet dhcp

```

```

:~$ ifconfig eth0

eth0      Link encap:Ethernet  HWaddr 00:0C:6E:6F:A5:AF
          inet addr:81.197.47.177  Bcast:81.197.63.255  Mask:255.255.192.0
          inet6 addr: fe80::20c:6eff:fe6f:a5af/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:22016 errors:0 dropped:0 overruns:0 frame:0
          TX packets:22575 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:13522980 (12.8 MiB)  TX bytes:4901812 (4.6 MiB)
          Interrupt:21 Base address:0xe000

```


OK, at the moment it works. But from time to time, it just stops resolving addresses. My roommate's computer that's connected to the same ADSL box works perfectly with Debian. I also had Debian previously but got fed up with unstable so thought of switching to Ubuntu. Oh, and that ethernet card: it's integrated on the mb and uses forcedeth module. 

Need more info? Please ask it! ;)

EDIT: Sorry if this is a duplicate, didn't find anything just similar with the search DNS or DNS problem...

---

### Post by dcstar on 2006-03-28
[QUOTE=pacman^]
......
EDIT: Sorry if this is a duplicate, didn't find anything just similar with the search DNS or DNS problem...[/QUOTE]
Some people have fixed some of their DNS issues by removing IPv6 support, do a forum search and you should find the instructions to try this out.

---

