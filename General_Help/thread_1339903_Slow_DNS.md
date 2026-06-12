---
title: "Slow DNS"
date: 2009-11-28
forum: General Help
---

### Post by spoon_ on 2009-11-28
This is really strange...both the Ubuntu computers in my house suddenly developed the same problem. One is running 9.10, the other 8.10. The 8.10 one isn't ever even updated. DNS resolution on both of them has become painfully slow (like 20-30 seconds). The one Windows machine seems unaffected.

The problem is not just in Firefox, it happens when I use wget too. But the even stranger part is that when I try to resolve hosts manually with nslookup, I get an answer within a second or so. So I don't understand what's going on. I've tried playing around with the order of the DNS servers in Network Manager (putting my router first, putting it last, etc.), and that hasn't helped. I've also tried disabling IPv6 in Firefox, as people have suggested for 9.10, but that doesn't help, and like I said my problem is not restricted to Firefox.

Any ideas? Thanks.

---

### Post by jamesisin on 2009-11-28
It doesn't seem like a dns issue if your nslookups are going fast.

Have you tried testing another browser?

You say this is not limited to Firefox; can you give some other examples where the slow-down is present?

How do trace routes compare between the fast and slow machines?

---

### Post by spoon_ on 2009-11-28
Yep, it's present when I try to wget anything. Konqueror has it too.

---

### Post by spoon_ on 2009-11-28
The traceroutes differ in that on the Linux machines, pretty much every line (except the last) is * * *. I don't know if this is because Linux sends out different packets than Windows, ones which intermediate machines are less likely to respond to, for some reason. I tried tracerouting with TCP and with ICMP packets and get the same results.

On the Windows machine, traceroute gets a response from every intermediate host. The host I tracerouted is google.com.

---

### Post by sanderj on 2009-11-28
Can you post the output of 

traceroute (or mtr -r -c2 ping.xs4all.nl)
ifconfig
ip route show

See mine below



```
ubuntu@ubuntu:~$ mtr -r -c2 ping.xs4all.nl
HOST: ubuntu                      Loss%   Snt   Last   Avg  Best  Wrst StDev
  1. 192.168.1.254                 0.0%     2    0.8   0.8   0.8   0.8   0.0
  2. 82-169-27-254.ip.telfort.nl   0.0%     2   19.0  18.4  17.8  19.0   0.8
  3. ams-ix.sara.xs4all.net        0.0%     2   20.4  21.1  20.4  21.7   0.9
  4. 0.so-1-0-0.xr4.1d12.xs4all.n  0.0%     2   20.6  20.9  20.6  21.3   0.5
  5. uucp1.xs4all.nl               0.0%     2   20.5  21.3  20.5  22.2   1.1


ubuntu@ubuntu:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:17:42:13:41:73  
          inet addr:192.168.1.33  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::217:42ff:fe13:4173/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:17364 errors:0 dropped:0 overruns:0 frame:0
          TX packets:15324 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:13832985 (13.8 MB)  TX bytes:2907537 (2.9 MB)
          Interrupt:16 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:240 (240.0 B)  TX bytes:240 (240.0 B)

pan0      Link encap:Ethernet  HWaddr 5e:6a:b6:0e:35:80  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:18:de:10:c5:06  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wmaster0  Link encap:UNSPEC  HWaddr 00-18-DE-10-C5-06-00-00-00-00-00-00-00-00-00-00  
          UP RUNNING  MTU:0  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)



ubuntu@ubuntu:~$ ip route show
192.168.1.0/24 dev eth0  proto kernel  scope link  src 192.168.1.33  metric 1 
169.254.0.0/16 dev eth0  scope link  metric 1000 
default via 192.168.1.254 dev eth0  proto static 
ubuntu@ubuntu:~$
```

---

### Post by spoon_ on 2009-11-28
Here you go.

```

spoon@table:~/Desktop$ mtr -r -c2 ping.xs4all.nl
HOST: table                       Loss%   Snt   Last   Avg  Best  Wrst StDev
  1. 192.168.1.1                   0.0%     2    0.6   0.6   0.6   0.7   0.1
  2. bas4-toronto46-1279333525.ds  0.0%     2    1.7   1.7   1.7   1.7   0.0
  3. bas4-toronto46_lo0_SYMP.net. 50.0%     2   11.7  11.7  11.7  11.7   0.0
  4. core1-toronto12_3-0-4_149.ne  0.0%     2    9.3  10.8   9.3  12.3   2.1
  5. core3-toronto21_POS0-4-1-0.n  0.0%     2   11.0  11.9  11.0  12.7   1.2
  6. NEWCORE1-CHICAGOCP_so2-1-0-0  0.0%     2   22.7  22.8  22.7  22.8   0.1
  7. bx4-chicagodt_POS2-0-0.net.b  0.0%     2   24.5  24.8  24.5  25.1   0.5
  8. Verio-Peering.net.bell.ca     0.0%     2   24.4  25.0  24.4  25.6   0.9
  9. as-1.r21.nycmny01.us.bb.gin.  0.0%     2   36.1  37.1  36.1  38.1   1.4
 10. as-0.r20.asbnva02.us.bb.gin.  0.0%     2   39.8  41.1  39.8  42.3   1.8
 11. ae-3.r21.asbnva01.us.bb.gin.  0.0%     2   43.6  57.0  43.6  70.4  19.0
 12. as-0.r23.amstnl02.nl.bb.gin.  0.0%     2  130.1 131.0 130.1 131.9   1.3
 13. ae-1.r22.amstnl02.nl.bb.gin.  0.0%     2  126.0 152.9 126.0 179.7  38.0
 14. xe-3-1.r00.amstnl02.nl.bb.gi  0.0%     2  135.6 137.1 135.6 138.7   2.2
 15. 81.20.64.26                   0.0%     2  133.6 136.4 133.6 139.1   3.9
 16. ???                          100.0     2    0.0   0.0   0.0   0.0   0.0
 17. ???                          100.0     2    0.0   0.0   0.0   0.0   0.0
 18. ???                          100.0     2    0.0   0.0   0.0   0.0   0.0
 19. static.kpn.net               50.0%     2  152.6 152.6 152.6 152.6   0.0
 20. uucp1.xs4all.nl              50.0%     2  139.3 139.3 139.3 139.3   0.0

```

```

spoon@table:~/Desktop$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:17:31:89:11:a1  
          inet addr:192.168.1.7  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::217:31ff:fe89:11a1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:67492 errors:0 dropped:0 overruns:0 frame:0
          TX packets:64112 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:55005733 (55.0 MB)  TX bytes:10930303 (10.9 MB)
          Interrupt:29 Base address:0x8000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2858 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2858 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:476249 (476.2 KB)  TX bytes:476249 (476.2 KB)

vboxnet0  Link encap:Ethernet  HWaddr 0a:00:27:00:00:00  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


```

```

spoon@table:~/Desktop$ ip route show
192.168.1.0/24 dev eth0  proto kernel  scope link  src 192.168.1.7  metric 1 
169.254.0.0/16 dev eth0  scope link  metric 1000 
default via 192.168.1.1 dev eth0  proto static 

```

Thanks.

---

### Post by sanderj on 2009-11-28
Furthermore: if you request [http://194.109.6.92/](http://194.109.6.92/) , is it fast, or slow too?

---

### Post by spoon_ on 2009-11-28
> **sanderj said:**
> Furthermore: if you request [http://194.109.6.92/](http://194.109.6.92/) , is it fast, or slow too?

Fast. Any queries that don't require resolving a hostname are fast.

---

### Post by sanderj on 2009-11-28
OK, your networks looks OK. IP-gettings is fast. Let's do some DNS-checking: 

Can you post the output of


cat /etc/resolv.conf
time host [www.xs4all.nl](www.xs4all.nl)

Mine:
```

ubuntu@ubuntu:~$ cat /etc/resolv.conf 
# Generated by NetworkManager
domain lokaal
search lokaal
nameserver 192.168.1.254
nameserver 195.241.77.55
nameserver 195.241.77.58

ubuntu@ubuntu:~$ time host www.xs4all.nl
www.xs4all.nl has address 194.109.6.92

real	0m0.074s
user	0m0.000s
sys	0m0.008s
ubuntu@ubuntu:~$ 

```

---

### Post by spoon_ on 2009-11-28
```

spoon@table:~/Desktop$ cat /etc/resolv.conf
# Generated by NetworkManager
nameserver 192.168.1.1
nameserver 207.164.234.129
spoon@table:~/Desktop$ time host www.xs4all.nl
www.xs4all.nl has address 194.109.6.92

real	0m3.166s
user	0m0.000s
sys	0m0.000s


```

---

### Post by ubername on 2009-11-28
> **spoon_ said:**
> ```

spoon@table:~/Desktop$ cat /etc/resolv.conf
# Generated by NetworkManager
nameserver 192.168.1.1
nameserver 207.164.234.129
spoon@table:~/Desktop$ time host www.xs4all.nl
www.xs4all.nl has address 194.109.6.92

real	0m3.166s
user	0m0.000s
sys	0m0.000s


```

Have you tried removing your router from DNS altogether ?

i.e. just have
nameserver 207.164.234.129)

---

### Post by sanderj on 2009-11-28
3 seconds lookup; not fast, but no 20 seconds delay.

Let's check your namesevers. Post the output of:



time dig @192.168.1.1 [www.xs4all.nl](www.xs4all.nl) +short
time dig @207.164.234.129 [www.xs4all.nl](www.xs4all.nl) +short
time dig @4.4.4.4 [www.xs4all.nl](www.xs4all.nl) +short



```
ubuntu@ubuntu:~$ time dig @192.168.1.254 www.xs4all.nl +short
194.109.6.92

real	0m0.034s
user	0m0.000s
sys	0m0.008s
ubuntu@ubuntu:~$ time dig @4.4.4.4 www.xs4all.nl +short

; <<>> DiG 9.6.1-P1 <<>> @4.4.4.4 www.xs4all.nl +short
; (1 server found)
;; global options: +cmd
;; connection timed out; no servers could be reached

real	0m15.013s
user	0m0.008s
sys	0m0.008s
ubuntu@ubuntu:~$


```

---

### Post by sanderj on 2009-11-28
General one-liner to check your nameservers in your /etc/resolv.conf: 

cat /etc/resolv.conf  | grep nameserver | awk '{ print "time dig +short [www.xs4all.nl](www.xs4all.nl) @" $2 }' | /bin/sh


Example output:

```

ubuntu@ubuntu:~$ cat /etc/resolv.conf  | grep nameserver | awk '{ print "time dig +short www.xs4all.nl @" $2 }' | /bin/sh
194.109.6.92
0.00user 0.00system 0:00.02elapsed 13%CPU (0avgtext+0avgdata 0maxresident)k
0inputs+0outputs (0major+798minor)pagefaults 0swaps
194.109.6.92
0.01user 0.00system 0:00.03elapsed 34%CPU (0avgtext+0avgdata 0maxresident)k
0inputs+0outputs (0major+798minor)pagefaults 0swaps
194.109.6.92
0.00user 0.00system 0:00.03elapsed 35%CPU (0avgtext+0avgdata 0maxresident)k
0inputs+0outputs (0major+797minor)pagefaults 0swaps
ubuntu@ubuntu:~$


```

---

### Post by spoon_ on 2009-11-28
Just tried that, and reconnected. It actually seems to have helped. Though it did just take about 10 seconds to resolve live.com. But at the moment I can't find any more hosts that take an inordinate amount of time to resolve (I've been trying new hosts of course). The live.com thing seems to have been a strange fluke.

The Windows machine was configured as you suggested, by the way (no router in DNS server list). So thanks for your help!

---

### Post by sanderj on 2009-11-28
If you changed /etc/resolv.conf by hand, be careful: after a reboot, it can be the old /etc/resolv.conf as it is probably set by DHCP.

---

### Post by spoon_ on 2009-11-28
> **sanderj said:**
> If you changed /etc/resolv.conf by hand, be careful: after a reboot, it can be the old /etc/resolv.conf as it is probably set by DHCP.

I changed the order of the nameservers in the network manager applet. Hopefully that's permanent? Edit: sorry, I meant I removed the router from the list of nameservers.

---

### Post by sanderj on 2009-11-28
> **spoon_ said:**
> I changed the order of the nameservers in the network manager applet. Hopefully that's permanent? Edit: sorry, I meant I removed the router from the list of nameservers.

Reboot, and let us know the result ... ;-)

---

### Post by spoon_ on 2009-11-28
> **sanderj said:**
> Reboot, and let us know the result ... ;-)

The change has stuck after reboot! And I can't recreate the DNS problems anymore. So it looks like that was it! Thanks!

---

### Post by spoon_ on 2009-11-28
So does the order of the DNS servers matter at all? I assumed it would only query the second one if it got no response from the first.

---

### Post by jamesisin on 2009-11-28
That concurs with my assumption about the server order.

---

### Post by ubername on 2009-11-28
> **spoon_ said:**
> The change has stuck after reboot! And I can't recreate the DNS problems anymore. So it looks like that was it! Thanks!

Was the 'it' removing the router from the DNS list?

---

### Post by spoon_ on 2009-11-28
> **ubername said:**
> Was the 'it' removing the router from the DNS list?

Yes it was.

---

### Post by VastOne on 2009-11-28
Just want to extend a kudos to you two on resolving this. Not only was it great read and lessons on linux networking issues it was also like watching a video how-to

Thanks!

---

### Post by jamesisin on 2009-11-28
On most of my machines I usually order my DNS list as follows:

1. my domain/dns server
2. my outside router/firewall
3. my ISP's DNS server(s)

You might try that order to see if it impacts things to your liking.

There is redundancy built in (the router inquires of my dns server and my dns server inquires of my ISP's server(s)), but each entry can serve a purpose.  For instance, local resources: domain machines will be returned by my server; non-domain machines will be returned by my router.

Maybe this isn't the best arrangement, so I'm always open to suggestions.

---

### Post by Scott O'Nanski on 2009-12-10
This looks like a conversation between people who know what they're talking about. I'm currently experiencing the same problem. How do I fix it?

---

### Post by sanderj on 2009-12-11
> **Scott O'Nanski said:**
> This looks like a conversation between people who know what they're talking about. I'm currently experiencing the same problem. How do I fix it?

Well, use post #13 in this thread: [http://ubuntuforums.org/showpost.php?p=8400666&postcount=13](http://ubuntuforums.org/showpost.php?p=8400666&postcount=13)

---

### Post by Scott O'Nanski on 2009-12-29
> **sanderj said:**
> Well, use post #13 in this thread: [http://ubuntuforums.org/showpost.php?p=8400666&postcount=13](http://ubuntuforums.org/showpost.php?p=8400666&postcount=13)

And then? :)

---

### Post by bad_lopix on 2010-01-16
> **spoon_ said:**
> The change has stuck after reboot! And I can't recreate the DNS problems anymore. So it looks like that was it! Thanks!

What applet are you using to delete the router IP?  In Network Manager (installed by default) I'm not finding anything related to DNS.  I tried installing "Network" tool (gnome-network-admin) : this has a tab for DNS and when I delete the first entry all is well.  BUT it is not sticking after a reboot...  

Thanks!

---

### Post by dale.novak on 2010-10-10
Here is how my thoughts on the issue and my resolution.

Newer versions of Ubuntu have ip6 enabled by default. Normaly this is a good thing, however, if you have a home router that is not ip6 compatible, that would be about 99% of them, dns resolution can be extremely slow.

To fix this use the command "sudo gedit /etc/dhcp3/dhclient.conf" and append the following lines at the end.

#Use OpenDNS for DNS resolution
prepend domain-name-servers 208.67.222.222, 208.67.220.220;

This will insure that ubuntu uses the ip6 compatible OpenDNS dns servers first. Of course, you can substitute any ip6 compatible dns server ip address's you wish.

Some other free ip6 compatible DNS services:

Service provider: Google
8.8.8.8
8.8.4.4

Service provider: dnsadvantage
156.154.70.1
156.154.71.1

Service provider: Level 3 Communications
4.2.2.2
4.2.2.3

Service provider: Time Warner Telecomm
64.129.67.102
64.129.67.103 
:popcorn:

---

