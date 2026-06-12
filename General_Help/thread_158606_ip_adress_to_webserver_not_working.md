---
title: "ip adress to webserver not working"
date: 2006-04-11
forum: General Help
---

### Post by MaZZly on 2006-04-11
Hi
I have put up a webserver on my ubuntu machine.
I can connect to my homesite by using the local ip (192.168.0.1)
but i cant connect to it using the servers "internet ip" (xxx.xxx.xxx.xxx), it just shows me nothing/blank, and in the adressbar it stands [http://xxx.xxx.xxx.xxx/](http://xxx.xxx.xxx.xxx/)
are there any ports that are supposed to be open?

---

### Post by spanishwasabi on 2006-04-12
Hi,

If I understand you well, you can connect inside your network to [http://192.168.0.1](http://192.168.0.1) but you can not connect from outside your network at [http://xxx.xxx.xxx.xxx](http://xxx.xxx.xxx.xxx) ?

Did you set your router to do a reverse NAT to your webserver?
You must tell your router that all incoming connections to port 80 (or 8080 or whatever) should go to the machine 192.168.0.1 at port 80.

I've a similar setup at home :-)

Enjoy,

G

---

### Post by MaZZly on 2006-04-12
havent got a router, i've got: 
adsl modem(w/o router)->ubuntu(webserver and firewall)->my xp machine(gaming/surfing :))

and port 80 is open. does the 8080 need to be opened to?

---

### Post by spanishwasabi on 2006-04-12
Mmm... I do not have much experience in that...

The port 80 should be open in both interfaces indeed. You can check that with nmap or netstat.

You might also want to revise your apache configuration to make it accept connections from both IP address. Have a look at VirtualHost IP address based.

Have a look anyway at this link, it
[http://www.faqs.org/docs/linux_intro/sect_10_04.html](http://www.faqs.org/docs/linux_intro/sect_10_04.html)
and to the apache documentation.

Good luck,

G

---

### Post by MaZZly on 2006-04-12
i dont have a clue what to do! please explain to me what to change

---

### Post by justleen on 2006-04-12
From where are you accessing [http://x.x.x.x?](http://x.x.x.x?) from that XP/Linux machine?
in my experience, that wont work because of the routing... 
did you test it from outside your own network?

---

### Post by MaZZly on 2006-04-12
I can access it from my xp machine by using local ip
I can access it by using [http://localhost](http://localhost) on the server to.
but not by using the internet ip

I havent tried accessing it from any other place than my own computer

---

### Post by justleen on 2006-04-12
sounds like its working OK to me.. 
i think it wont work from the inside on the outside IP 
any chance you can post you ip, so I can check it?
(or PM it?)

---

### Post by souki on 2006-04-12
[QUOTE=MaZZly]havent got a router, i've got: 
adsl modem(w/o router)->ubuntu(webserver and firewall)->my xp machine(gaming/surfing :))

and port 80 is open. does the 8080 need to be opened to?[/QUOTE]
what kind of link between your adsl modem and your webserver ?
is it usb ? ethernet ?

post here the ouput of 'ifconfig'
post here the ouput of 'route -n'
post here the output of 'netstat -nl46'
post here the output of 'sudo iptables -L'

---

### Post by MaZZly on 2006-04-12
Ethernet cable

ifconfig:
```

eth0      Link encap:Ethernet  HWaddr 00:02:B3:8B:0E:20
          inet addr:62.72.252.115  Bcast:62.72.253.255  Mask:255.255.254.0
          inet6 addr: fe80::202:b3ff:fe8b:e20/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:23421 errors:0 dropped:0 overruns:0 frame:0
          TX packets:18341 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:26031539 (24.8 MiB)  TX bytes:2058846 (1.9 MiB)

eth1      Link encap:Ethernet  HWaddr 00:50:FC:FE:73:A3
          inet addr:192.168.0.1  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::250:fcff:fefe:73a3/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:634563 errors:0 dropped:0 overruns:0 frame:0
          TX packets:978774 errors:0 dropped:0 overruns:0 carrier:0
          collisions:669386 txqueuelen:1000
          RX bytes:39919652 (38.0 MiB)  TX bytes:1399591915 (1.3 GiB)
          Interrupt:10 Base address:0xe000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:51774 errors:0 dropped:0 overruns:0 frame:0
          TX packets:51774 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:14987694 (14.2 MiB)  TX bytes:14987694 (14.2 MiB)

```

route -n:
```

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.0.0     0.0.0.0         255.255.255.0   U     0      0        0 eth1
62.72.252.0     0.0.0.0         255.255.254.0   U     0      0        0 eth0
0.0.0.0         62.72.252.1     0.0.0.0         UG    0      0        0 eth0

```

netstat -nl46:
```

Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State
tcp        0      0 127.0.0.1:1026          0.0.0.0:*               LISTEN
tcp        0      0 127.0.0.1:1027          0.0.0.0:*               LISTEN
tcp        0      0 0.0.0.0:139             0.0.0.0:*               LISTEN
tcp        0      0 0.0.0.0:5900            0.0.0.0:*               LISTEN
tcp        0      0 0.0.0.0:53              0.0.0.0:*               LISTEN
tcp        0      0 127.0.0.1:631           0.0.0.0:*               LISTEN
tcp        0      0 0.0.0.0:445             0.0.0.0:*               LISTEN
tcp6       0      0 :::80                   :::*                    LISTEN
tcp6       0      0 :::53                   :::*                    LISTEN
udp        0      0 0.0.0.0:1024            0.0.0.0:*
udp        0      0 127.0.0.1:1027          0.0.0.0:*
udp        0      0 62.72.252.115:137       0.0.0.0:*
udp        0      0 192.168.0.1:137         0.0.0.0:*
udp        0      0 0.0.0.0:137             0.0.0.0:*
udp        0      0 62.72.252.115:138       0.0.0.0:*
udp        0      0 192.168.0.1:138         0.0.0.0:*
udp        0      0 0.0.0.0:138             0.0.0.0:*
udp        0      0 0.0.0.0:53              0.0.0.0:*
udp        0      0 0.0.0.0:68              0.0.0.0:*
udp6       0      0 :::53                   :::*

```

iptables -L:
```

Chain INBOUND (4 references)
target     prot opt source               destination
ACCEPT     tcp  --  anywhere             anywhere            state RELATED,ESTABLISHED
ACCEPT     udp  --  anywhere             anywhere            state RELATED,ESTABLISHED
ACCEPT     all  --  192.168.0.2          anywhere
ACCEPT     all  --  host-66.battle.net   anywhere
ACCEPT     all  --  host-66.battle.net   anywhere
ACCEPT     all  --  192.168.0.1          anywhere
ACCEPT     all  --  192.168.0.3          anywhere
ACCEPT     tcp  --  anywhere             anywhere            tcp dpts:6112:6119
ACCEPT     udp  --  anywhere             anywhere            udp dpts:6112:6119
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:33187
ACCEPT     udp  --  anywhere             anywhere            udp dpt:33187
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:6881
ACCEPT     udp  --  anywhere             anywhere            udp dpt:6881
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:33333
ACCEPT     udp  --  anywhere             anywhere            udp dpt:33333
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:4373
ACCEPT     udp  --  anywhere             anywhere            udp dpt:4373
ACCEPT     tcp  --  anywhere             anywhere            tcp dpts:1025:1026
ACCEPT     udp  --  anywhere             anywhere            udp dpts:1025:1026
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:www
ACCEPT     udp  --  anywhere             anywhere            udp dpt:www
LSI        all  --  anywhere             anywhere

Chain INPUT (policy DROP)
target     prot opt source               destination
ACCEPT     tcp  --  ns2.multi.fi         anywhere            tcp flags:!SYN,RST,ACK/SYN
ACCEPT     udp  --  ns2.multi.fi         anywhere
ACCEPT     tcp  --  agda.multi.fi        anywhere            tcp flags:!SYN,RST,ACK/SYN
ACCEPT     udp  --  agda.multi.fi        anywhere
ACCEPT     all  --  anywhere             anywhere
ACCEPT     icmp --  anywhere             anywhere            limit: avg 10/sec burst 5
DROP       all  --  anywhere             255.255.255.255
DROP       all  --  anywhere             3e48fdff.adsl.multi.fi
DROP       all  --  BASE-ADDRESS.MCAST.NET/8  anywhere
DROP       all  --  anywhere             BASE-ADDRESS.MCAST.NET/8
DROP       all  --  255.255.255.255      anywhere
DROP       all  --  anywhere             0.0.0.0
DROP       all  --  anywhere             anywhere            state INVALID
LSI        all  -f  anywhere             anywhere            limit: avg 10/min burst 5
INBOUND    all  --  anywhere             anywhere
INBOUND    all  --  anywhere             192.168.0.1
INBOUND    all  --  anywhere             3e48fc73.adsl.multi.fi
INBOUND    all  --  anywhere             192.168.0.255
LOG_FILTER  all  --  anywhere             anywhere
LOG        all  --  anywhere             anywhere            LOG level info prefix `Unknown Input'

Chain FORWARD (policy DROP)
target     prot opt source               destination
ACCEPT     icmp --  anywhere             anywhere            limit: avg 10/sec burst 5
TCPMSS     tcp  --  anywhere             anywhere            tcp flags:SYN,RST/SYN TCPMSS clamp to PMTU
ACCEPT     tcp  --  anywhere             192.168.0.2         tcp dpts:6112:6119
ACCEPT     udp  --  anywhere             192.168.0.2         udp dpts:6112:6119
ACCEPT     tcp  --  anywhere             192.168.0.2         tcp dpt:33187
ACCEPT     udp  --  anywhere             192.168.0.2         udp dpt:33187
ACCEPT     tcp  --  anywhere             192.168.0.2         tcp dpt:33187
ACCEPT     udp  --  anywhere             192.168.0.2         udp dpt:33187
ACCEPT     tcp  --  anywhere             192.168.0.2         tcp dpt:33333
ACCEPT     udp  --  anywhere             192.168.0.2         udp dpt:33333
ACCEPT     tcp  --  anywhere             192.168.0.2         tcp dpt:4373
ACCEPT     udp  --  anywhere             192.168.0.2         udp dpt:4373
ACCEPT     tcp  --  anywhere             192.168.0.2         tcp dpts:1025:1026
ACCEPT     udp  --  anywhere             192.168.0.2         udp dpts:1025:1026
OUTBOUND   all  --  anywhere             anywhere
ACCEPT     tcp  --  anywhere             192.168.0.0/24      state RELATED,ESTABLISHED
ACCEPT     udp  --  anywhere             192.168.0.0/24      state RELATED,ESTABLISHED
LOG_FILTER  all  --  anywhere             anywhere
LOG        all  --  anywhere             anywhere            LOG level info prefix `Unknown Forward'

Chain LOG_FILTER (5 references)
target     prot opt source               destination

Chain LSI (2 references)
target     prot opt source               destination
LOG_FILTER  all  --  anywhere             anywhere
LOG        tcp  --  anywhere             anywhere            tcp flags:SYN,RST,ACK/SYN limit: avg 1/sec burst 5 LOG level info prefix `Inbound '
DROP       tcp  --  anywhere             anywhere            tcp flags:SYN,RST,ACK/SYN
LOG        tcp  --  anywhere             anywhere            tcp flags:FIN,SYN,RST,ACK/RST limit: avg 1/sec burst 5 LOG level info prefix `Inbound '
DROP       tcp  --  anywhere             anywhere            tcp flags:FIN,SYN,RST,ACK/RST
LOG        icmp --  anywhere             anywhere            icmp echo-request limit: avg 1/sec burst 5 LOG level info prefix `Inbound '
DROP       icmp --  anywhere             anywhere            icmp echo-request
LOG        all  --  anywhere             anywhere            limit: avg 5/sec burst 5 LOG level info prefix `Inbound '
DROP       all  --  anywhere             anywhere

Chain LSO (0 references)
target     prot opt source               destination
LOG_FILTER  all  --  anywhere             anywhere
LOG        all  --  anywhere             anywhere            limit: avg 5/sec burst 5 LOG level info prefix `Outbound '
REJECT     all  --  anywhere             anywhere            reject-with icmp-port-unreachable

Chain OUTBOUND (3 references)
target     prot opt source               destination
ACCEPT     icmp --  anywhere             anywhere
ACCEPT     tcp  --  anywhere             anywhere            state RELATED,ESTABLISHED
ACCEPT     udp  --  anywhere             anywhere            state RELATED,ESTABLISHED
ACCEPT     all  --  anywhere             anywhere

Chain OUTPUT (policy DROP)
target     prot opt source               destination
ACCEPT     tcp  --  3e48fc73.adsl.multi.fi  ns2.multi.fi        tcp dpt:domain
ACCEPT     udp  --  3e48fc73.adsl.multi.fi  ns2.multi.fi        udp dpt:domain
ACCEPT     tcp  --  3e48fc73.adsl.multi.fi  agda.multi.fi       tcp dpt:domain
ACCEPT     udp  --  3e48fc73.adsl.multi.fi  agda.multi.fi       udp dpt:domain
ACCEPT     all  --  anywhere             anywhere
DROP       all  --  BASE-ADDRESS.MCAST.NET/8  anywhere
DROP       all  --  anywhere             BASE-ADDRESS.MCAST.NET/8
DROP       all  --  255.255.255.255      anywhere
DROP       all  --  anywhere             0.0.0.0
DROP       all  --  anywhere             anywhere            state INVALID
OUTBOUND   all  --  anywhere             anywhere
OUTBOUND   all  --  anywhere             anywhere
LOG_FILTER  all  --  anywhere             anywhere
LOG        all  --  anywhere             anywhere            LOG level info prefix `Unknown Output'

```


[QUOTE=justleen]sounds like its working OK to me.. 
i think it wont work from the inside on the outside IP 
any chance you can post you ip, so I can check it?
(or PM it?)[/QUOTE]

mazzly.no-ip.org
62.72.253.115

---

### Post by souki on 2006-04-12
your configuration is ok
```
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:www
```
I got a response from your ip on port 80, but the server says "HTTP/1.0 404 Not Found"
there's no others informations, so I don't know if this header came from your server or not
look at the apache logs to find more about my connection attempt

---

### Post by MaZZly on 2006-04-17
hi again, been to a skiing-resort on my easter-holiday :)

so on to my prob:
where is the log file located?

before i got myself the server i had the website on my xp machine using IIS and that worked well w/o problems

since my ip changes constantly , i will try to change the redirecting on [http://mazzly.no-ip.org](http://mazzly.no-ip.org)


*EDIT* its working now when i tested it after my holiday, wierd.. maybe the server just needed to rest ;)

thnx for the help

---

### Post by souki on 2006-04-17
yes, it works
it might be your dynamic ip update

---

