---
title: "How to allow protocol 59 in firewall?"
date: 2011-05-25
forum: General Help
---

### Post by iX9 on 2011-05-25
Can anyone help me solve this?

How to get incoming connection by teredo (ipv6) adapter in KTorrent?

My ufw settings:
```


ee@aa:~$ sudo ufw status verbose
Status: active
Logging: on (low)
Default: deny (incoming), allow (outgoing)
New profiles: skip

Do                         Akce        Od
--                         ----        --

6881                       ALLOW IN    Anywhere
6881                       ALLOW IN    Anywhere (v6)

ee@aa:~$

```

KTorrent is listening on 6881 port.
My ufw log is full of this:
> 
May 24 18:19:45 aa kernel: [ 1157.419846] [UFW BLOCK] IN=teredo OUT= MAC= SRC=2001:0000:5ef5:79fd:10b7:103e:a83f:5f09 DST=2001:0000:98aa:064c:14b2:3333:b2cf:77ca LEN=40 TC=0 HOPLIMIT=21 FLOWLBL=0 PROTO=59
May 24 18:19:45 aa kernel: [ 1157.619125] [UFW BLOCK] IN=teredo OUT= MAC= SRC=2001:0000:5ef5:79fd:38e6:3c1a:a54b:3311 DST=2001:0000:98aa:064c:14b2:3333:b2cf:77ca LEN=40 TC=0 HOPLIMIT=21 FLOWLBL=0 PROTO=59
May 24 18:20:05 aa kernel: [ 1177.346269] [UFW BLOCK] IN=teredo OUT= MAC= SRC=2001:0000:5ef5:73b8:3884:1735:2baf:b6fd DST=2001:0000:98aa:064c:14b2:3333:b2cf:77ca LEN=40 TC=0 HOPLIMIT=21 FLOWLBL=0 PROTO=59


How to enable protocol 59 in firewall?
Ufw supports only tcp/udp protocol.
If I have ufw disabled, inc. connection by teredo works - there is a lot of them succesed in KTorent log. But when is ufw enable, no ipv6 incoming connections any more, and ufw's log is full of above....

And this is my ip6tables:
```

ee@aa:~$ sudo ip6tables -L -n
Chain INPUT (policy DROP)
target     prot opt source               destination         
ufw6-before-logging-input  all      ::/0                 ::/0                
ufw6-before-input  all      ::/0                 ::/0                
ufw6-after-input  all      ::/0                 ::/0                
ufw6-after-logging-input  all      ::/0                 ::/0                
ufw6-reject-input  all      ::/0                 ::/0                
ufw6-track-input  all      ::/0                 ::/0                

Chain FORWARD (policy DROP)
target     prot opt source               destination         
ufw6-before-logging-forward  all      ::/0                 ::/0                
ufw6-before-forward  all      ::/0                 ::/0                
ufw6-after-forward  all      ::/0                 ::/0                
ufw6-after-logging-forward  all      ::/0                 ::/0                
ufw6-reject-forward  all      ::/0                 ::/0                

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination         
ufw6-before-logging-output  all      ::/0                 ::/0                
ufw6-before-output  all      ::/0                 ::/0                
ufw6-after-output  all      ::/0                 ::/0                
ufw6-after-logging-output  all      ::/0                 ::/0                
ufw6-reject-output  all      ::/0                 ::/0                
ufw6-track-output  all      ::/0                 ::/0                

Chain ufw6-after-forward (1 references)
target     prot opt source               destination         

Chain ufw6-after-input (1 references)
target     prot opt source               destination         
ufw6-skip-to-policy-input  udp      ::/0                 ::/0                udp dpt:137 
ufw6-skip-to-policy-input  udp      ::/0                 ::/0                udp dpt:138 
ufw6-skip-to-policy-input  tcp      ::/0                 ::/0                tcp dpt:139 
ufw6-skip-to-policy-input  tcp      ::/0                 ::/0                tcp dpt:445 
ufw6-skip-to-policy-input  udp      ::/0                 ::/0                udp dpt:67 
ufw6-skip-to-policy-input  udp      ::/0                 ::/0                udp dpt:68 

Chain ufw6-after-logging-forward (1 references)
target     prot opt source               destination         
LOG        all      ::/0                 ::/0                limit: avg 3/min burst 10 LOG flags 0 level 4 prefix `[UFW BLOCK] ' 

Chain ufw6-after-logging-input (1 references)
target     prot opt source               destination         
LOG        all      ::/0                 ::/0                limit: avg 3/min burst 10 LOG flags 0 level 4 prefix `[UFW BLOCK] ' 

Chain ufw6-after-logging-output (1 references)
target     prot opt source               destination         

Chain ufw6-after-output (1 references)
target     prot opt source               destination         

Chain ufw6-before-forward (1 references)
target     prot opt source               destination         
DROP       all      ::/0                 ::/0                rt type:0 
ufw6-user-forward  all      ::/0                 ::/0                

Chain ufw6-before-input (1 references)
target     prot opt source               destination         
ACCEPT     all      ::/0                 ::/0                
DROP       all      ::/0                 ::/0                rt type:0 
ACCEPT     icmpv6    ::/0                 ::/0                ipv6-icmp type 135 HL match HL == 255 
ACCEPT     icmpv6    ::/0                 ::/0                ipv6-icmp type 136 HL match HL == 255 
ACCEPT     icmpv6    ::/0                 ::/0                ipv6-icmp type 133 HL match HL == 255 
ACCEPT     icmpv6    ::/0                 ::/0                ipv6-icmp type 134 HL match HL == 255 
ACCEPT     all      ::/0                 ::/0                state RELATED,ESTABLISHED 
ACCEPT     icmpv6    fe80::/10            ::/0                ipv6-icmp type 129 
ufw6-logging-deny  all      ::/0                 ::/0                state INVALID 
DROP       all      ::/0                 ::/0                state INVALID 
ACCEPT     icmpv6    ::/0                 ::/0                ipv6-icmp type 1 
ACCEPT     icmpv6    ::/0                 ::/0                ipv6-icmp type 2 
ACCEPT     icmpv6    ::/0                 ::/0                ipv6-icmp type 3 
ACCEPT     icmpv6    ::/0                 ::/0                ipv6-icmp type 4 
ACCEPT     icmpv6    ::/0                 ::/0                ipv6-icmp type 128 
ACCEPT     udp      ::/0                 ::/0                udp spt:67 dpt:68 
ACCEPT     udp      ::/0                 ff02::fb/128        udp dpt:5353 
ufw6-user-input  all      ::/0                 ::/0                

Chain ufw6-before-logging-forward (1 references)
target     prot opt source               destination         

Chain ufw6-before-logging-input (1 references)
target     prot opt source               destination         

Chain ufw6-before-logging-output (1 references)
target     prot opt source               destination         

Chain ufw6-before-output (1 references)
target     prot opt source               destination         
ACCEPT     all      ::/0                 ::/0                
DROP       all      ::/0                 ::/0                rt type:0 
ACCEPT     icmpv6    ::/0                 ::/0                ipv6-icmp type 135 HL match HL == 255 
ACCEPT     icmpv6    ::/0                 ::/0                ipv6-icmp type 136 HL match HL == 255 
ACCEPT     all      ::/0                 ::/0                state RELATED,ESTABLISHED 
ufw6-user-output  all      ::/0                 ::/0                

Chain ufw6-logging-allow (0 references)
target     prot opt source               destination         
LOG        all      ::/0                 ::/0                limit: avg 3/min burst 10 LOG flags 0 level 4 prefix `[UFW ALLOW] ' 

Chain ufw6-logging-deny (1 references)
target     prot opt source               destination         
RETURN     all      ::/0                 ::/0                state INVALID limit: avg 3/min burst 10 
LOG        all      ::/0                 ::/0                limit: avg 3/min burst 10 LOG flags 0 level 4 prefix `[UFW BLOCK] ' 

Chain ufw6-reject-forward (1 references)
target     prot opt source               destination         

Chain ufw6-reject-input (1 references)
target     prot opt source               destination         

Chain ufw6-reject-output (1 references)
target     prot opt source               destination         

Chain ufw6-skip-to-policy-forward (0 references)
target     prot opt source               destination         
DROP       all      ::/0                 ::/0                

Chain ufw6-skip-to-policy-input (6 references)
target     prot opt source               destination         
DROP       all      ::/0                 ::/0                

Chain ufw6-skip-to-policy-output (0 references)
target     prot opt source               destination         
ACCEPT     all      ::/0                 ::/0                

Chain ufw6-track-input (1 references)
target     prot opt source               destination         

Chain ufw6-track-output (1 references)
target     prot opt source               destination         
ACCEPT     tcp      ::/0                 ::/0                state NEW 
ACCEPT     udp      ::/0                 ::/0                state NEW 

Chain ufw6-user-forward (1 references)
target     prot opt source               destination         

Chain ufw6-user-input (1 references)
target     prot opt source               destination         
ACCEPT     tcp      ::/0                 ::/0                tcp dpt:6881 
ACCEPT     udp      ::/0                 ::/0                udp dpt:6881 

Chain ufw6-user-limit (0 references)
target     prot opt source               destination         

Chain ufw6-user-limit-accept (0 references)
target     prot opt source               destination         

Chain ufw6-user-logging-forward (0 references)
target     prot opt source               destination         

Chain ufw6-user-logging-input (0 references)
target     prot opt source               destination         

Chain ufw6-user-logging-output (0 references)
target     prot opt source               destination         

Chain ufw6-user-output (1 references)
target     prot opt source               destination         
ee@aa:~$

```

Any suggestion?

---

### Post by linuxinstalledfromhdd on 2011-05-25
Have you already configured port-forwarding in your router box? Normally UFW will allow outgoing requests.

---

### Post by iX9 on 2011-05-25
No need for forwarding, I have public IP.
IPv4 incomming connection works well.

---

### Post by linuxinstalledfromhdd on 2011-05-25
Wouldn't you still need to set up port forwarding on your router for your private network that you are attached to?

---

### Post by iX9 on 2011-05-25
I dont thing so.
  If I disable ufw, it works, if enable - no. It must be just firewall problem. Everythings fine on M$windous.

---

### Post by linuxinstalledfromhdd on 2011-05-25
You can try

sudo iptables -A INPUT -p tcp --dport 6881 -j ACCEPT


If you are using different port you need to enter that port number instead of 6881.

---

### Post by iX9 on 2011-05-26
SOLVED! :popcorn:
[B]
sudo ip6tables -I INPUT -p 59 -j ACCEPT
sudo ip6tables -I INPUT -p 129 -j ACCEPT
[/B]

1.) This commands must be applyed after ufw setups iptables on boot.
2.) There is need to use "**-I**" intead of common "**-A**", to ensure proccesing those two rules before the packets are droped in else chains of ip6tables...

Now, finally, I have incoming connections in KTorrent, even I am behind NAT and firewall... :):D

---

