---
title: "Issues connecting to Webmin - other posts not working"
date: 2012-04-11
forum: General Help
---

### Post by marktyler on 2012-04-11
I've having issues connecting to my Webmin installation from anything other than the localhost machine. I have the following iptables rules in place with the port 10000 found on forums

```

sudo iptables -nvL
Chain INPUT (policy ACCEPT 124 packets, 31188 bytes)
 pkts bytes target     prot opt in     out     source               destination         
    1    60 ACCEPT     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           state NEW tcp dpt:10000 

Chain FORWARD (policy ACCEPT 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source               destination         

Chain OUTPUT (policy ACCEPT 125 packets, 31248 bytes)
 pkts bytes target     prot opt in     out     source               destination         
  125 31248 Nanny      all  --  *      *       0.0.0.0/0            0.0.0.0/0           

Chain Nanny (1 references)
 pkts bytes target     prot opt in     out     source               destination         

```

However I get a connection timeout from any other machine on the network.
Next I ran tcpdump...

```

$ sudo tcpdump -i eth1 host 192.168.1.2 -v
tcpdump: listening on eth1, link-type EN10MB (Ethernet), capture size 96 bytes
21:00:01.431772 IP (tos 0x0, ttl 64, id 562, offset 0, flags [none], proto UDP (17), length 177)
    192.168.1.2.ipp > 192.168.1.255.ipp: UDP, length 149
21:00:03.055863 IP (tos 0x0, ttl 64, id 42049, offset 0, flags [DF], proto TCP (6), length 64)
    192.168.1.2.64427 > laptop.local.webmin: Flags [S], cksum 0x79a1 (correct), seq 3441291070, win 65535, options [mss 1460,nop,wscale 3,nop,nop,TS val 1064835948 ecr 0,sackOK,eol], length 0
21:00:03.055973 IP (tos 0x0, ttl 64, id 0, offset 0, flags [DF], proto TCP (6), length 60)
    laptop.local.webmin > 192.168.1.2.64427: Flags [S.], cksum 0x1f35 (correct), seq 3230770793, ack 3441291071, win 5792, options [mss 1460,sackOK,TS val 2223520 ecr 1064835948,nop,wscale 6], length 0
21:00:03.305818 IP (tos 0x0, ttl 64, id 31258, offset 0, flags [DF], proto TCP (6), length 64)
    192.168.1.2.64428 > laptop.local.webmin: Flags [S], cksum 0x22fb (correct), seq 677702298, win 65535, options [mss 1460,nop,wscale 3,nop,nop,TS val 1064835951 ecr 0,sackOK,eol], length 0
21:00:03.305926 IP (tos 0x0, ttl 64, id 0, offset 0, flags [DF], proto TCP (6), length 60)
    laptop.local.webmin > 192.168.1.2.64428: Flags [S.], cksum 0x0dbd (correct), seq 1358942350, ack 677702299, win 5792, options [mss 1460,sackOK,TS val 2223583 ecr 1064835951,nop,wscale 6], length 0
21:00:03.999889 IP (tos 0x0, ttl 64, id 30994, offset 0, flags [DF], proto TCP (6), length 64)
    192.168.1.2.64427 > laptop.local.webmin: Flags [S], cksum 0x7998 (correct), seq 3441291070, win 65535, options [mss 1460,nop,wscale 3,nop,nop,TS val 1064835957 ecr 0,sackOK,eol], length 0
21:00:03.999969 IP (tos 0x0, ttl 64, id 0, offset 0, flags [DF], proto TCP (6), length 60)
    laptop.local.webmin > 192.168.1.2.64427: Flags [S.], cksum 0x1e49 (correct), seq 3230770793, ack 3441291071, win 5792, options [mss 1460,sackOK,TS val 2223756 ecr 1064835948,nop,wscale 6], length 0
21:00:04.300227 IP (tos 0x0, ttl 64, id 61978, offset 0, flags [DF], proto TCP (6), length 64)
    192.168.1.2.64428 > laptop.local.webmin: Flags [S], cksum 0x22f2 (correct), seq 677702298, win 65535, options [mss 1460,nop,wscale 3,nop,nop,TS val 1064835960 ecr 0,sackOK,eol], length 0
21:00:04.300308 IP (tos 0x0, ttl 64, id 0, offset 0, flags [DF], proto TCP (6), length 60)
    laptop.local.webmin > 192.168.1.2.64428: Flags [S.], cksum 0x0cc5 (correct), seq 1358942350, ack 677702299, win 5792, options [mss 1460,sackOK,TS val 2223831 ecr 1064835951,nop,wscale 6], length 0
21:00:05.001042 IP (tos 0x0, ttl 64, id 9321, offset 0, flags [DF], proto TCP (6), length 64)
    192.168.1.2.64427 > laptop.local.webmin: Flags [S], cksum 0x798e (correct), seq 3441291070, win 65535, options [mss 1460,nop,wscale 3,nop,nop,TS val 1064835967 ecr 0,sackOK,eol], length 0
21:00:05.001126 IP (tos 0x0, ttl 64, id 0, offset 0, flags [DF], proto TCP (6), length 60)
    laptop.local.webmin > 192.168.1.2.64427: Flags [S.], cksum 0x1d4e (correct), seq 3230770793, ack 3441291071, win 5792, options [mss 1460,sackOK,TS val 2224007 ecr 1064835948,nop,wscale 6], length 0
21:00:05.301474 IP (tos 0x0, ttl 64, id 51834, offset 0, flags [DF], proto TCP (6), length 64)
    192.168.1.2.64428 > laptop.local.webmin: Flags [S], cksum 0x22e8 (correct), seq 677702298, win 65535, options [mss 1460,nop,wscale 3,nop,nop,TS val 1064835970 ecr 0,sackOK,eol], length 0
21:00:05.301559 IP (tos 0x0, ttl 64, id 0, offset 0, flags [DF], proto TCP (6), length 60)
    laptop.local.webmin > 192.168.1.2.64428: Flags [S.], cksum 0x0bca (correct), seq 1358942350, ack 677702299, win 5792, options [mss 1460,sackOK,TS val 2224082 ecr 1064835951,nop,wscale 6], length 0
21:00:06.002219 IP (tos 0x0, ttl 64, id 60693, offset 0, flags [DF], proto TCP (6), length 64)
    192.168.1.2.64427 > laptop.local.webmin: Flags [S], cksum 0x7984 (correct), seq 3441291070, win 65535, options [mss 1460,nop,wscale 3,nop,nop,TS val 1064835977 ecr 0,sackOK,eol], length 0
21:00:06.002280 IP (tos 0x0, ttl 64, id 0, offset 0, flags [DF], proto TCP (6), length 60)
    laptop.local.webmin > 192.168.1.2.64427: Flags [S.], cksum 0x1c54 (correct), seq 3230770793, ack 3441291071, win 5792, options [mss 1460,sackOK,TS val 2224257 ecr 1064835948,nop,wscale 6], length 0
21:00:06.302606 IP (tos 0x0, ttl 64, id 6515, offset 0, flags [DF], proto TCP (6), length 64)
    192.168.1.2.64428 > laptop.local.webmin: Flags [S], cksum 0x22de (correct), seq 677702298, win 65535, options [mss 1460,nop,wscale 3,nop,nop,TS val 1064835980 ecr 0,sackOK,eol], length 0
21:00:06.302691 IP (tos 0x0, ttl 64, id 0, offset 0, flags [DF], proto TCP (6), length 60)
    laptop.local.webmin > 192.168.1.2.64428: Flags [S.], cksum 0x0ad0 (correct), seq 1358942350, ack 677702299, win 5792, options [mss 1460,sackOK,TS val 2224332 ecr 1064835951,nop,wscale 6], length 0
21:00:07.003562 IP (tos 0x0, ttl 64, id 22574, offset 0, flags [DF], proto TCP (6), length 64)
    192.168.1.2.64427 > laptop.local.webmin: Flags [S], cksum 0x797a (correct), seq 3441291070, win 65535, options [mss 1460,nop,wscale 3,nop,nop,TS val 1064835987 ecr 0,sackOK,eol], length 0
21:00:07.003647 IP (tos 0x0, ttl 64, id 0, offset 0, flags [DF], proto TCP (6), length 60)
    laptop.local.webmin > 192.168.1.2.64427: Flags [S.], cksum 0x1b5a (correct), seq 3230770793, ack 3441291071, win 5792, options [mss 1460,sackOK,TS val 2224507 ecr 1064835948,nop,wscale 6], length 0
21:00:07.303937 IP (tos 0x0, ttl 64, id 40714, offset 0, flags [DF], proto TCP (6), length 64)
    192.168.1.2.64428 > laptop.local.webmin: Flags [S], cksum 0x22d4 (correct), seq 677702298, win 65535, options [mss 1460,nop,wscale 3,nop,nop,TS val 1064835990 ecr 0,sackOK,eol], length 0
21:00:07.304022 IP (tos 0x0, ttl 64, id 0, offset 0, flags [DF], proto TCP (6), length 60)
    laptop.local.webmin > 192.168.1.2.64428: Flags [S.], cksum 0x09d6 (correct), seq 1358942350, ack 677702299, win 5792, options [mss 1460,sackOK,TS val 2224582 ecr 1064835951,nop,wscale 6], length 0
21:00:07.428753 IP (tos 0x0, ttl 64, id 0, offset 0, flags [DF], proto TCP (6), length 60)
    laptop.local.webmin > 192.168.1.2.64427: Flags [S.], cksum 0x1aef (correct), seq 3230770793, ack 3441291071, win 5792, options [mss 1460,sackOK,TS val 2224614 ecr 1064835948,nop,wscale 6], length 0
21:00:07.604309 IP (tos 0x0, ttl 64, id 16971, offset 0, flags [DF], proto TCP (6), length 48)
    192.168.1.2.64415 > laptop.local.webmin: Flags [S], cksum 0xd041 (correct), seq 1966708884, win 65535, options [mss 1460,sackOK,eol], length 0
21:00:07.604364 IP (tos 0x0, ttl 64, id 0, offset 0, flags [DF], proto TCP (6), length 60)
    laptop.local.webmin > 192.168.1.2.64415: Flags [S.], cksum 0x7c78 (correct), seq 1443782403, ack 1966708885, win 5792, options [mss 1460,sackOK,TS val 2224657 ecr 1064835644,nop,wscale 6], length 0
21:00:07.628715 IP (tos 0x0, ttl 64, id 0, offset 0, flags [DF], proto TCP (6), length 60)
    laptop.local.webmin > 192.168.1.2.64428: Flags [S.], cksum 0x0984 (correct), seq 1358942350, ack 677702299, win 5792, options [mss 1460,sackOK,TS val 2224664 ecr 1064835951,nop,wscale 6], length 0
21:00:07.904656 IP (tos 0x0, ttl 64, id 34638, offset 0, flags [DF], proto TCP (6), length 48)
    192.168.1.2.64416 > laptop.local.webmin: Flags [S], cksum 0xdc5d (correct), seq 345435418, win 65535, options [mss 1460,sackOK,eol], length 0
21:00:07.904716 IP (tos 0x0, ttl 64, id 0, offset 0, flags [DF], proto TCP (6), length 60)
    laptop.local.webmin > 192.168.1.2.64416: Flags [S.], cksum 0x6150 (correct), seq 4226146337, ack 345435419, win 5792, options [mss 1460,sackOK,TS val 2224732 ecr 1064835647,nop,wscale 6], length 0
21:00:08.004844 IP (tos 0x0, ttl 64, id 42061, offset 0, flags [DF], proto TCP (6), length 64)
    192.168.1.2.64427 > laptop.local.webmin: Flags [S], cksum 0x7970 (correct), seq 3441291070, win 65535, options [mss 1460,nop,wscale 3,nop,nop,TS val 1064835997 ecr 0,sackOK,eol], length 0
21:00:08.004927 IP (tos 0x0, ttl 64, id 0, offset 0, flags [DF], proto TCP (6), length 60)
    laptop.local.webmin > 192.168.1.2.64427: Flags [S.], cksum 0x1a5f (correct), seq 3230770793, ack 3441291071, win 5792, options [mss 1460,sackOK,TS val 2224758 ecr 1064835948,nop,wscale 6], length 0
21:00:08.305807 IP (tos 0x0, ttl 64, id 47708, offset 0, flags [DF], proto TCP (6), length 64)
    192.168.1.2.64428 > laptop.local.webmin: Flags [S], cksum 0x22ca (correct), seq 677702298, win 65535, options [mss 1460,nop,wscale 3,nop,nop,TS val 1064836000 ecr 0,sackOK,eol], length 0
21:00:08.305889 IP (tos 0x0, ttl 64, id 0, offset 0, flags [DF], proto TCP (6), length 60)
    laptop.local.webmin > 192.168.1.2.64428: Flags [S.], cksum 0x08db (correct), seq 1358942350, ack 677702299, win 5792, options [mss 1460,sackOK,TS val 2224833 ecr 1064835951,nop,wscale 6], length 0
21:00:10.007469 IP (tos 0x0, ttl 64, id 35438, offset 0, flags [DF], proto TCP (6), length 64)
    192.168.1.2.64427 > laptop.local.webmin: Flags [S], cksum 0x795c (correct), seq 3441291070, win 65535, options [mss 1460,nop,wscale 3,nop,nop,TS val 1064836017 ecr 0,sackOK,eol], length 0
21:00:10.007555 IP (tos 0x0, ttl 64, id 0, offset 0, flags [DF], proto TCP (6), length 60)
    laptop.local.webmin > 192.168.1.2.64427: Flags [S.], cksum 0x186b (correct), seq 3230770793, ack 3441291071, win 5792, options [mss 1460,sackOK,TS val 2225258 ecr 1064835948,nop,wscale 6], length 0
21:00:10.300735 ARP, Ethernet (len 6), IPv4 (len 4), Request who-has 192.168.1.2 tell laptop.local, length 28
21:00:10.301509 ARP, Ethernet (len 6), IPv4 (len 4), Reply 192.168.1.2 is-at c8:bc:c8:9f:0d:06 (oui Unknown), length 46
21:00:10.307641 IP (tos 0x0, ttl 64, id 31237, offset 0, flags [DF], proto TCP (6), length 64)
    192.168.1.2.64428 > laptop.local.webmin: Flags [S], cksum 0x22b6 (correct), seq 677702298, win 65535, options [mss 1460,nop,wscale 3,nop,nop,TS val 1064836020 ecr 0,sackOK,eol], length 0
21:00:10.307706 IP (tos 0x0, ttl 64, id 0, offset 0, flags [DF], proto TCP (6), length 60)
    laptop.local.webmin > 192.168.1.2.64428: Flags [S.], cksum 0x06e7 (correct), seq 1358942350, ack 677702299, win 5792, options [mss 1460,sackOK,TS val 2225333 ecr 1064835951,nop,wscale 6], length 0
21:00:13.428756 IP (tos 0x0, ttl 64, id 0, offset 0, flags [DF], proto TCP (6), length 60)
    laptop.local.webmin > 192.168.1.2.64427: Flags [S.], cksum 0x1513 (correct), seq 3230770793, ack 3441291071, win 5792, options [mss 1460,sackOK,TS val 2226114 ecr 1064835948,nop,wscale 6], length 0
21:00:13.628767 IP (tos 0x0, ttl 64, id 0, offset 0, flags [DF], proto TCP (6), length 60)
    laptop.local.webmin > 192.168.1.2.64428: Flags [S.], cksum 0x03a8 (correct), seq 1358942350, ack 677702299, win 5792, options [mss 1460,sackOK,TS val 2226164 ecr 1064835951,nop,wscale 6], length 0
21:00:14.012136 IP (tos 0x0, ttl 64, id 21061, offset 0, flags [DF], proto TCP (6), length 48)
    192.168.1.2.64427 > laptop.local.webmin: Flags [S], cksum 0x21a7 (correct), seq 3441291070, win 65535, options [mss 1460,sackOK,eol], length 0
21:00:14.012222 IP (tos 0x0, ttl 64, id 0, offset 0, flags [DF], proto TCP (6), length 60)
    laptop.local.webmin > 192.168.1.2.64427: Flags [S.], cksum 0x1482 (correct), seq 3230770793, ack 3441291071, win 5792, options [mss 1460,sackOK,TS val 2226259 ecr 1064835948,nop,wscale 6], length 0
21:00:14.312659 IP (tos 0x0, ttl 64, id 25428, offset 0, flags [DF], proto TCP (6), length 48)
    192.168.1.2.64428 > laptop.local.webmin: Flags [S], cksum 0xcb03 (correct), seq 677702298, win 65535, options [mss 1460,sackOK,eol], length 0
21:00:14.312746 IP (tos 0x0, ttl 64, id 0, offset 0, flags [DF], proto TCP (6), length 60)
    laptop.local.webmin > 192.168.1.2.64428: Flags [S.], cksum 0x02fe (correct), seq 1358942350, ack 677702299, win 5792, options [mss 1460,sackOK,TS val 2226334 ecr 1064835951,nop,wscale 6], length 0
21:00:18.228761 IP (tos 0x0, ttl 64, id 0, offset 0, flags [DF], proto TCP (6), length 60)
    laptop.local.webmin > 192.168.1.2.64415: Flags [S.], cksum 0x7217 (correct), seq 1443782403, ack 1966708885, win 5792, options [mss 1460,sackOK,TS val 2227314 ecr 1064835644,nop,wscale 6], length 0
21:00:18.561542 IP (tos 0x0, ttl 64, id 4177, offset 0, flags [none], proto UDP (17), length 78)
    192.168.1.2.netbios-ns > 192.168.1.255.netbios-ns: NBT UDP PACKET(137): QUERY; REQUEST; BROADCAST
21:00:19.428762 IP (tos 0x0, ttl 64, id 0, offset 0, flags [DF], proto TCP (6), length 60)
    laptop.local.webmin > 192.168.1.2.64416: Flags [S.], cksum 0x560e (correct), seq 4226146337, ack 345435419, win 5792, options [mss 1460,sackOK,TS val 2227614 ecr 1064835647,nop,wscale 6], length 0
21:00:22.021769 IP (tos 0x0, ttl 64, id 47621, offset 0, flags [DF], proto TCP (6), length 48)
    192.168.1.2.64427 > laptop.local.webmin: Flags [S], cksum 0x21a7 (correct), seq 3441291070, win 65535, options [mss 1460,sackOK,eol], length 0
21:00:22.021854 IP (tos 0x0, ttl 64, id 0, offset 0, flags [DF], proto TCP (6), length 60)
    laptop.local.webmin > 192.168.1.2.64427: Flags [S.], cksum 0x0caf (correct), seq 3230770793, ack 3441291071, win 5792, options [mss 1460,sackOK,TS val 2228262 ecr 1064835948,nop,wscale 6], length 0
21:00:22.322506 IP (tos 0x0, ttl 64, id 59945, offset 0, flags [DF], proto TCP (6), length 48)
    192.168.1.2.64428 > laptop.local.webmin: Flags [S], cksum 0xcb03 (correct), seq 677702298, win 65535, options [mss 1460,sackOK,eol], length 0
21:00:22.322594 IP (tos 0x0, ttl 64, id 0, offset 0, flags [DF], proto TCP (6), length 60)
    laptop.local.webmin > 192.168.1.2.64428: Flags [S.], cksum 0xfb2a (correct), seq 1358942350, ack 677702299, win 5792, options [mss 1460,sackOK,TS val 2228337 ecr 1064835951,nop,wscale 6], length 0
^C
50 packets captured
50 packets received by filter
0 packets dropped by kernel

```

So nothing seems to be dropped. But I'm not getting through either. As an FYI, I do have Gnome Nanny or whatever it's called running hence the empty but named chain on the iptables.
I've now reached the end of my limited linux knowledge in how to get this working.

---

### Post by LewisTM on 2012-04-11
You should setup [SSH local port forwarding]("https://help.ubuntu.com/community/SSH/OpenSSH/PortForwarding") to your machine.

Read up on SSH, install OpenSSH and set it up the way you like. It can be used to remotely log in and execute any command, so it's invaluable for remote management. Using keys for authentication is the most efficient way to use SSH. 

A command like this should allow you to connect to a remote Webmin from a local browser by forwarding port 10000.

```
ssh -L 10001:localhost:10000 user@remotemachine
```

Then connect to the remote Webmin at [https://localhost:10001](https://localhost:10001)

Cheers!

---

### Post by marktyler on 2012-04-12
It was a dumb dumb mistake. My iptables setup was fine as indicated by the TCPDUMP seeing all traffic passing through. The issue? Kid's laptop was connected on a guest network that's not allowed to bridge to the main network so although on the same network mask it was effectively on a separate VLAN.#-o

---

