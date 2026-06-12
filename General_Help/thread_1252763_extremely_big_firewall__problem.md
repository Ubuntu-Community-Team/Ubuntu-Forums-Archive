---
title: "extremely big firewall  problem"
date: 2009-08-29
forum: General Help
---

### Post by sefs on 2009-08-29
I have a server setup as a vpn server in bridged mode.

I have ufw on this machines.

eth0 is bridged with tap0 to form br0

The thing is the machine appears to not be obeying rules set in gufw / ufw

For instance ... I have vnc installed on this machine.  I do not have the vnc port opened in the firewall (which means only localhost can connect) yet I can connect to this machine from any other machine on the lan.

I should have noticed this when I could connect to samba shares on the machine when no netbios ports were opened for it.  Somehow it seems to be disobeying the firewall rules.

Is it because of the network is briged between tap0 and eth0 to form br0?

Need some urgent help to plug this gaping gotse.

Thanks.

---

### Post by bodhi.zazen on 2009-08-29
First, with such a complex set up ufw / gufw are probably not the best tools to configure your firewall.

Second, how did you set up your rules in ufw / gufw ?

Personally I suggest you either use something like guraddog or shorewall or write your rules yourself.

What is the output of :

```
sudo iptables -L -v
```

---

### Post by sefs on 2009-08-29
Thanks for your response. I was trying to stay away from a complex firewall as I am not really that technical in firewall setup.  In ufw, i used gufw, and set the ports i wanted open or closed in the gui.

iptables:
```

Chain INPUT (policy DROP 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source               destination         
 2417  270K ufw-before-input  all  --  any    any     anywhere             anywhere            
    0     0 ACCEPT     all  --  tap0   any     anywhere             anywhere            
  498 70459 ACCEPT     all  --  br0    any     anywhere             anywhere            
    0     0 ufw-after-input  all  --  any    any     anywhere             anywhere            

Chain FORWARD (policy DROP 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source               destination         
 3557 1256K ufw-before-forward  all  --  any    any     anywhere             anywhere            
 3557 1256K ACCEPT     all  --  br0    any     anywhere             anywhere            
    0     0 ufw-after-forward  all  --  any    any     anywhere             anywhere            

Chain OUTPUT (policy ACCEPT 12 packets, 774 bytes)
 pkts bytes target     prot opt in     out     source               destination         
 2212  232K ufw-before-output  all  --  any    any     anywhere             anywhere            
   12   774 ufw-after-output  all  --  any    any     anywhere             anywhere            

Chain ufw-after-forward (1 references)
 pkts bytes target     prot opt in     out     source               destination         
    0     0 LOG        all  --  any    any     anywhere             anywhere            limit: avg 3/min burst 10 LOG level warning prefix `[UFW BLOCK FORWARD]: ' 
    0     0 RETURN     all  --  any    any     anywhere             anywhere            

Chain ufw-after-input (1 references)
 pkts bytes target     prot opt in     out     source               destination         
    0     0 RETURN     udp  --  any    any     anywhere             anywhere            udp dpt:netbios-ns 
    0     0 RETURN     udp  --  any    any     anywhere             anywhere            udp dpt:netbios-dgm 
    0     0 RETURN     tcp  --  any    any     anywhere             anywhere            tcp dpt:netbios-ssn 
    0     0 RETURN     tcp  --  any    any     anywhere             anywhere            tcp dpt:microsoft-ds 
    0     0 RETURN     udp  --  any    any     anywhere             anywhere            udp dpt:bootps 
    0     0 RETURN     udp  --  any    any     anywhere             anywhere            udp dpt:bootpc 
    0     0 LOG        all  --  any    any     anywhere             anywhere            limit: avg 3/min burst 10 LOG level warning prefix `[UFW BLOCK INPUT]: ' 
    0     0 RETURN     all  --  any    any     anywhere             anywhere            

Chain ufw-after-output (1 references)
 pkts bytes target     prot opt in     out     source               destination         
   12   774 RETURN     all  --  any    any     anywhere             anywhere            

Chain ufw-before-forward (1 references)
 pkts bytes target     prot opt in     out     source               destination         
 3557 1256K ufw-user-forward  all  --  any    any     anywhere             anywhere            
 3557 1256K RETURN     all  --  any    any     anywhere             anywhere            

Chain ufw-before-input (1 references)
 pkts bytes target     prot opt in     out     source               destination         
  159 15168 ACCEPT     all  --  lo     any     anywhere             anywhere            
 1474  159K ACCEPT     all  --  any    any     anywhere             anywhere            ctstate RELATED,ESTABLISHED 
    0     0 DROP       all  --  any    any     anywhere             anywhere            ctstate INVALID 
    0     0 ACCEPT     icmp --  any    any     anywhere             anywhere            icmp destination-unreachable 
    0     0 ACCEPT     icmp --  any    any     anywhere             anywhere            icmp source-quench 
    0     0 ACCEPT     icmp --  any    any     anywhere             anywhere            icmp time-exceeded 
    0     0 ACCEPT     icmp --  any    any     anywhere             anywhere            icmp parameter-problem 
    9   540 ACCEPT     icmp --  any    any     anywhere             anywhere            icmp echo-request 
    0     0 ACCEPT     udp  --  any    any     anywhere             anywhere            udp spt:bootps dpt:bootpc 
  775 94980 ufw-not-local  all  --  any    any     anywhere             anywhere            
    0     0 ACCEPT     all  --  any    any     BASE-ADDRESS.MCAST.NET/4  anywhere            
   15  2755 ACCEPT     all  --  any    any     anywhere             BASE-ADDRESS.MCAST.NET/4 
  760 92225 ufw-user-input  all  --  any    any     anywhere             anywhere            
  498 70459 RETURN     all  --  any    any     anywhere             anywhere            

Chain ufw-before-output (1 references)
 pkts bytes target     prot opt in     out     source               destination         
    0     0 ACCEPT     all  --  lo     any     anywhere             anywhere            
  971  104K ACCEPT     tcp  --  any    any     anywhere             anywhere            state NEW,RELATED,ESTABLISHED 
 1229  127K ACCEPT     udp  --  any    any     anywhere             anywhere            state NEW,RELATED,ESTABLISHED 
   12   774 ufw-user-output  all  --  any    any     anywhere             anywhere            
   12   774 RETURN     all  --  any    any     anywhere             anywhere            

Chain ufw-not-local (1 references)
 pkts bytes target     prot opt in     out     source               destination         
  470 29030 RETURN     all  --  any    any     anywhere             anywhere            ADDRTYPE match dst-type LOCAL 
   15  2755 RETURN     all  --  any    any     anywhere             anywhere            ADDRTYPE match dst-type MULTICAST 
  290 63195 RETURN     all  --  any    any     anywhere             anywhere            ADDRTYPE match dst-type BROADCAST 
    0     0 LOG        all  --  any    any     anywhere             anywhere            limit: avg 3/min burst 10 LOG level warning prefix `[UFW BLOCK NOT-TO-ME]: ' 
    0     0 DROP       all  --  any    any     anywhere             anywhere            

Chain ufw-user-forward (1 references)
 pkts bytes target     prot opt in     out     source               destination         
 3557 1256K RETURN     all  --  any    any     anywhere             anywhere            

Chain ufw-user-input (1 references)
 pkts bytes target     prot opt in     out     source               destination         
    1    60 ACCEPT     tcp  --  any    any     anywhere             anywhere            tcp dpt:ssh 
    0     0 ACCEPT     udp  --  any    any     anywhere             anywhere            udp dpt:openvpn 
    0     0 ACCEPT     tcp  --  any    any     192.168.254.0/24     anywhere            tcp dpt:domain 
  243 15802 ACCEPT     udp  --  any    any     192.168.254.0/24     anywhere            udp dpt:domain 
   18  5904 ACCEPT     udp  --  any    any     192.168.254.0/24     anywhere            udp dpt:bootps 
    0     0 ACCEPT     udp  --  any    any     192.168.254.0/24     anywhere            udp dpt:bootpc 
  498 70459 RETURN     all  --  any    any     anywhere             anywhere            

Chain ufw-user-output (1 references)
 pkts bytes target     prot opt in     out     source               destination         
   12   774 RETURN     all  --  any    any     anywhere             anywhere            

```

interfaces:
```

br0       Link encap:Ethernet  HWaddr 00:e0:18:99:88:77  
          inet addr:192.168.254.3  Bcast:192.168.254.255  Mask:255.255.255.0
          inet6 addr: fe80::2e0:18ff:fe99:8877/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:6629 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2968 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1511648 (1.4 MB)  TX bytes:312299 (304.9 KB)

eth0      Link encap:Ethernet  HWaddr 00:e0:18:99:88:77  
          inet6 addr: fe80::2e0:18ff:fe99:8877/64 Scope:Link
          UP BROADCAST RUNNING PROMISC MULTICAST  MTU:1500  Metric:1
          RX packets:6638 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2942 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1606202 (1.5 MB)  TX bytes:307243 (300.0 KB)
          Interrupt:16 Base address:0x2000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:175 errors:0 dropped:0 overruns:0 frame:0
          TX packets:175 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:16392 (16.0 KB)  TX bytes:16392 (16.0 KB)

tap0      Link encap:Ethernet  HWaddr 00:ff:51:d4:d3:1c  
          inet6 addr: fe80::2ff:51ff:fed4:d31c/64 Scope:Link
          UP BROADCAST RUNNING PROMISC MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3891 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:100 
          RX bytes:0 (0.0 B)  TX bytes:1352742 (1.2 MB)

```

---

