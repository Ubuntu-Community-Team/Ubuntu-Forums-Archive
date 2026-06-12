---
title: "Cant login to yahoo, gmail, hotmail, emesene, skype, ect."
date: 2010-04-12
forum: General Help
---

### Post by hotashes02 on 2010-04-12
I cant login to emails, emesene or skype. everytime i login to email site, it says :

"The connection was reset

The connection to the server was reset while the page was loading.

    *   The site could be temporarily unavailable or too busy. Try again in a few
          moments.

    *   If you are unable to load any pages, check your computer's network
          connection.

    *   If your computer or network is protected by a firewall or proxy, make sure
          that Firefox is permitted to access the Web." 

and when i try to login in emesene it never connect in skype it connect but no let me send i can get but it not let me send anything What is wrong here? and what should i do to solve it?? Thnx!

---

### Post by 98cwitr on 2010-04-12
can you log in from a different computer?

---

### Post by hotashes02 on 2010-04-12
yes i can login with other computers

---

### Post by _0R10N on 2010-04-12
Well it seems like you're not having connection at all!. You can try 
several things...

1- ifconfig <your-interface> and check if you have a valid ip-address.
2- Try pinging [www.google.com](www.google.com)

Are you behind a firewall??

Do you have a DHCP??

More info required!

Please, post your /etc/network/interfaces file


Kind regards!

_0R10N >>

---

### Post by hotashes02 on 2010-04-12
> **_0R10N said:**
> Well it seems like you're not having connection at all!. You can try 
several things...

1- ifconfig <your-interface> and check if you have a valid ip-address.
2- Try pinging [www.google.com](www.google.com)

Are you behind a firewall??

Do you have a DHCP??

More info required!

Please, post your /etc/network/interfaces file


Kind regards!

_0R10N >>

ifconfig
```
leandro@leandro-desktop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1c:c0:ab:e6:49  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Memory:e0200000-e0220000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:8 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:480 (480.0 B)  TX bytes:480 (480.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:17:3f:1d:85:cc  
          inet addr:192.168.2.2  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::217:3fff:fe1d:85cc/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:12424 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8330 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:9814489 (9.8 MB)  TX bytes:2502758 (2.5 MB)

wlan7     Link encap:Ethernet  HWaddr 00:22:75:91:05:4f  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wmaster0  Link encap:UNSPEC  HWaddr 00-22-75-91-05-4F-00-00-00-00-00-00-00-00-00-00  
          UP RUNNING  MTU:0  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wmaster1  Link encap:UNSPEC  HWaddr 00-17-3F-1D-85-CC-00-00-00-00-00-00-00-00-00-00  
          UP RUNNING  MTU:0  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

leandro@leandro-desktop:~$ 

```

ping google
```
leandro@leandro-desktop:~$ pinging www.google.com
pinging: command not found
leandro@leandro-desktop:~$ ping www.google.com
PING www.google.com (74.125.65.103) 56(84) bytes of data.
64 bytes from www.l.google.com (74.125.65.103): icmp_seq=1 ttl=54 time=24.9 ms
64 bytes from www.l.google.com (74.125.65.103): icmp_seq=2 ttl=54 time=18.7 ms
64 bytes from www.l.google.com (74.125.65.103): icmp_seq=3 ttl=54 time=19.0 ms
64 bytes from www.l.google.com (74.125.65.103): icmp_seq=4 ttl=54 time=20.7 ms
64 bytes from www.l.google.com (74.125.65.103): icmp_seq=5 ttl=54 time=18.9 ms
```

/etc/network/interfaces file
```
auto lo
iface lo inet loopback

```

how i check if i have DHCP

firewall the only thing i have is Firewall configuration but is desabled

---

### Post by 98cwitr on 2010-04-12
What router are you connecting to? Are there other devices on the network?

---

### Post by hotashes02 on 2010-04-13
belkin n150 and i have 2 laptop more connect to that router

---

### Post by _0R10N on 2010-04-16
> **hotashes02 said:**
> ifconfig
```
leandro@leandro-desktop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1c:c0:ab:e6:49  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Memory:e0200000-e0220000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:8 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:480 (480.0 B)  TX bytes:480 (480.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:17:3f:1d:85:cc  
          inet addr:192.168.2.2  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::217:3fff:fe1d:85cc/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:12424 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8330 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:9814489 (9.8 MB)  TX bytes:2502758 (2.5 MB)

wlan7     Link encap:Ethernet  HWaddr 00:22:75:91:05:4f  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wmaster0  Link encap:UNSPEC  HWaddr 00-22-75-91-05-4F-00-00-00-00-00-00-00-00-00-00  
          UP RUNNING  MTU:0  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wmaster1  Link encap:UNSPEC  HWaddr 00-17-3F-1D-85-CC-00-00-00-00-00-00-00-00-00-00  
          UP RUNNING  MTU:0  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

leandro@leandro-desktop:~$ 

```

ping google
```
leandro@leandro-desktop:~$ pinging www.google.com
pinging: command not found
leandro@leandro-desktop:~$ ping www.google.com
PING www.google.com (74.125.65.103) 56(84) bytes of data.
64 bytes from www.l.google.com (74.125.65.103): icmp_seq=1 ttl=54 time=24.9 ms
64 bytes from www.l.google.com (74.125.65.103): icmp_seq=2 ttl=54 time=18.7 ms
64 bytes from www.l.google.com (74.125.65.103): icmp_seq=3 ttl=54 time=19.0 ms
64 bytes from www.l.google.com (74.125.65.103): icmp_seq=4 ttl=54 time=20.7 ms
64 bytes from www.l.google.com (74.125.65.103): icmp_seq=5 ttl=54 time=18.9 ms
```

/etc/network/interfaces file
```
auto lo
iface lo inet loopback

```

how i check if i have DHCP

firewall the only thing i have is Firewall configuration but is desabled

You should try uninstalling the firewall. Perhaps there's some configuration messing your connection.

_0R10N >>

---

### Post by _0R10N on 2010-04-16
You can follow this thread [http://ubuntuforums.org/showthread.php?t=1453255](http://ubuntuforums.org/showthread.php?t=1453255)

_0R10N >>

---

### Post by Jive Turkey on 2010-04-16
You can disable your computers firewall if you run the following commands with sudo, this might help you to test if you got some funky iptables rule by accident.  I would not reccoment this as a permanent fix, or consider your computer safe for general use until you apply the normal rule set after running these commands. ufw can be used to apply normal rules after using this for diagnostic purposes.```

iptables -F
iptables -X
iptables -t nat -F
iptables -t nat -X
iptables -t mangle -F
iptables -t mangle -X
iptables -P INPUT ACCEPT
iptables -P FORWARD ACCEPT
iptables -P OUTPUT ACCEPT
```

In case you didn't catch that the commands will totally disable iptables filtering on your computer.

---

### Post by skaarr on 2010-04-16
Have you tried checking for updates (system>administration)?
I had this very problem when I first installed ubuntu and it seemed to be fixed by an update. Can't tell you which one though, sorry...

---

