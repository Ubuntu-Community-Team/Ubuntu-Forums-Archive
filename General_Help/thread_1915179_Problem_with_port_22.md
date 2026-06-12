---
title: "Problem with port 22"
date: 2012-01-25
forum: General Help
---

### Post by igorips on 2012-01-25
I have a problem with port 22 will not even be opened. I opened it to the router in the iptables firewall and everywhere I opened al still writes to me that the port is closed. Can someone help me pls?

---

### Post by bodhi.zazen on 2012-01-25
Can't tell you much from what little you posted.

Did you install openssh-server ? Did you start it ?

---

### Post by igorips on 2012-01-25
I installed the openssh-server and running it. But from another buddy I can not connect. When I scan port 22 writes me that the port is closed.

---

### Post by bodhi.zazen on 2012-01-25
Does it work on your local machine ?

```
ssh localhost
```

What settings did you use on your router ?
What settings did you use with iptables ?
What command did your friend use ?

---

### Post by igorips on 2012-01-25
port forwarding for router in admin panel . And for iptables

 sudo iptables -A INPUT -p tcp -d 0/0 -s 0/0 --dport 22 -j ACCEPT

 im use and for firewall 

 sudo ufw insert 1 allow 22

and my friend his use putty.
I really do not know where the problem for 2 days trying to solve the problem of al always the same.

---

### Post by igorips on 2012-01-25
Yes. working on localhost. Someone help me pls?

---

### Post by igorips on 2012-01-25
Someone help me pls ?

---

### Post by bodhi.zazen on 2012-01-25
You need to provide details, details of your port forwarding, details of your iptables rules. Why are you using both iptables and ufw ?

The order of rules is critical in iptables, so if you denied ssh higher in your rule set, adding it later makes no difference.

Post the output of 

```
sudo iptables -L -v -n
ufw status
```

Also, as ssh is working on local host, go the next step. connect from another computer on your LAN.

---

### Post by igorips on 2012-01-25
```
Chain INPUT (policy DROP 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source               destination         
 1101  697K ACCEPT     tcp  --  *      *       192.168.1.1          0.0.0.0/0           tcp flags:!0x17/0x02 
 2890  963K ACCEPT     udp  --  *      *       192.168.1.1          0.0.0.0/0           
  403 18923 ACCEPT     all  --  lo     *       0.0.0.0/0            0.0.0.0/0           
  115  6452 ACCEPT     icmp --  *      *       0.0.0.0/0            0.0.0.0/0           limit: avg 10/sec burst 5 
    0     0 DROP       all  --  wlan0  *       0.0.0.0/0            255.255.255.255     
    6   468 DROP       all  --  *      *       0.0.0.0/0            192.168.1.255       
    0     0 DROP       all  --  *      *       224.0.0.0/8          0.0.0.0/0           
  105  2944 DROP       all  --  *      *       0.0.0.0/0            224.0.0.0/8         
    0     0 DROP       all  --  *      *       255.255.255.255      0.0.0.0/0           
    0     0 DROP       all  --  *      *       0.0.0.0/0            0.0.0.0             
    9   360 DROP       all  --  *      *       0.0.0.0/0            0.0.0.0/0           state INVALID 
    0     0 LSI        all  -f  *      *       0.0.0.0/0            0.0.0.0/0           limit: avg 10/min burst 5 
 107K  116M INBOUND    all  --  wlan0  *       0.0.0.0/0            0.0.0.0/0           
    0     0 INBOUND    all  --  wlan0  *       0.0.0.0/0            192.168.1.5         
    0     0 INBOUND    all  --  wlan0  *       0.0.0.0/0            192.168.1.5         
    0     0 INBOUND    all  --  wlan0  *       0.0.0.0/0            192.168.1.255       
    0     0 LOG_FILTER  all  --  *      *       0.0.0.0/0            0.0.0.0/0           
    0     0 LOG        all  --  *      *       0.0.0.0/0            0.0.0.0/0           LOG flags 0 level 6 prefix `Unknown Input' 
    0     0 ACCEPT     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           tcp dpt:22 

Chain FORWARD (policy DROP 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source               destination         
    0     0 ACCEPT     icmp --  *      *       0.0.0.0/0            0.0.0.0/0           limit: avg 10/sec burst 5 
    0     0 TCPMSS     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           tcp flags:0x06/0x02 TCPMSS clamp to PMTU 
    0     0 OUTBOUND   all  --  wlan0  *       0.0.0.0/0            0.0.0.0/0           
    0     0 ACCEPT     tcp  --  *      *       0.0.0.0/0            192.168.1.0/24      state RELATED,ESTABLISHED 
    0     0 ACCEPT     udp  --  *      *       0.0.0.0/0            192.168.1.0/24      state RELATED,ESTABLISHED 
    0     0 LOG_FILTER  all  --  *      *       0.0.0.0/0            0.0.0.0/0           
    0     0 LOG        all  --  *      *       0.0.0.0/0            0.0.0.0/0           LOG flags 0 level 6 prefix `Unknown Forward' 

Chain OUTPUT (policy DROP 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source               destination         
    0     0 ACCEPT     tcp  --  *      *       192.168.1.5          192.168.1.1         tcp dpt:53 
 2969  193K ACCEPT     udp  --  *      *       192.168.1.5          192.168.1.1         udp dpt:53 
  403 18923 ACCEPT     all  --  *      lo      0.0.0.0/0            0.0.0.0/0           
    0     0 DROP       all  --  *      *       224.0.0.0/8          0.0.0.0/0           
   55  6188 DROP       all  --  *      *       0.0.0.0/0            224.0.0.0/8         
    0     0 DROP       all  --  *      *       255.255.255.255      0.0.0.0/0           
    0     0 DROP       all  --  *      *       0.0.0.0/0            0.0.0.0             
  165  6600 DROP       all  --  *      *       0.0.0.0/0            0.0.0.0/0           state INVALID 
88321   11M OUTBOUND   all  --  *      wlan0   0.0.0.0/0            0.0.0.0/0           
    0     0 OUTBOUND   all  --  *      wlan0   0.0.0.0/0            0.0.0.0/0           
    0     0 LOG_FILTER  all  --  *      *       0.0.0.0/0            0.0.0.0/0           
    0     0 LOG        all  --  *      *       0.0.0.0/0            0.0.0.0/0           LOG flags 0 level 6 prefix `Unknown Output' 

Chain INBOUND (4 references)
 pkts bytes target     prot opt in     out     source               destination         
 105K  116M ACCEPT     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           state RELATED,ESTABLISHED 
 2080  261K ACCEPT     udp  --  *      *       0.0.0.0/0            0.0.0.0/0           state RELATED,ESTABLISHED 
   29  1630 LSI        all  --  *      *       0.0.0.0/0            0.0.0.0/0           

Chain LOG_FILTER (5 references)
 pkts bytes target     prot opt in     out     source               destination         

Chain LSI (2 references)
 pkts bytes target     prot opt in     out     source               destination         
   29  1630 LOG_FILTER  all  --  *      *       0.0.0.0/0            0.0.0.0/0           
   26  1488 LOG        tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           tcp flags:0x17/0x02 limit: avg 1/sec burst 5 LOG flags 0 level 6 prefix `Inbound ' 
   26  1488 DROP       tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           tcp flags:0x17/0x02 
    0     0 LOG        tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           tcp flags:0x17/0x04 limit: avg 1/sec burst 5 LOG flags 0 level 6 prefix `Inbound ' 
    0     0 DROP       tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           tcp flags:0x17/0x04 
    0     0 LOG        icmp --  *      *       0.0.0.0/0            0.0.0.0/0           icmp type 8 limit: avg 1/sec burst 5 LOG flags 0 level 6 prefix `Inbound ' 
    0     0 DROP       icmp --  *      *       0.0.0.0/0            0.0.0.0/0           icmp type 8 
    3   142 LOG        all  --  *      *       0.0.0.0/0            0.0.0.0/0           limit: avg 5/sec burst 5 LOG flags 0 level 6 prefix `Inbound ' 
    3   142 DROP       all  --  *      *       0.0.0.0/0            0.0.0.0/0           

Chain LSO (0 references)
 pkts bytes target     prot opt in     out     source               destination         
    0     0 LOG_FILTER  all  --  *      *       0.0.0.0/0            0.0.0.0/0           
    0     0 LOG        all  --  *      *       0.0.0.0/0            0.0.0.0/0           limit: avg 5/sec burst 5 LOG flags 0 level 6 prefix `Outbound ' 
    0     0 REJECT     all  --  *      *       0.0.0.0/0            0.0.0.0/0           reject-with icmp-port-unreachable 

Chain OUTBOUND (3 references)
 pkts bytes target     prot opt in     out     source               destination         
    0     0 ACCEPT     icmp --  *      *       0.0.0.0/0            0.0.0.0/0           
83191   11M ACCEPT     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           state RELATED,ESTABLISHED 
 2134  240K ACCEPT     udp  --  *      *       0.0.0.0/0            0.0.0.0/0           state RELATED,ESTABLISHED 
 2996  161K ACCEPT     all  --  *      *       0.0.0.0/0            0.0.0.0/0           

```
that is the iptables
and the firewall :

```
Status: active

To                         Action      From
--                         ------      ----
22/tcp                     ALLOW       Anywhere
22/tcp                     ALLOW       22/tcp
22/tcp                     ALLOW       Anywhere (v6)

```

---

### Post by bodhi.zazen on 2012-01-25
You still have not posted all the information I have requested more then once.

Can you connect from another computer on your LAN ?

Your iptables rules are a horrible mess, where did you get them from ? They are not the default rules you get with ufw.

I suggest you do the following

```
sudo ufw disable
sudo iptables -F
sudo iptables -X
sudo iptables -t nat -F
sudo iptables -t nat -X
```

I assume your connection will then work.

You can then:

```
sudo ufw reset
sudo ufw allow OPENSSH
sudo ufw enable
```

It should then be working and from there you need to do a bit of reading on iptables and  ufw.

---

### Post by igorips on 2012-01-25
Yes its work :D thx

---

### Post by bodhi.zazen on 2012-01-25
Fantastic, thank you for marking this thread as solved. I take it you can sort out iptables / ufw from here then :twisted:

---

