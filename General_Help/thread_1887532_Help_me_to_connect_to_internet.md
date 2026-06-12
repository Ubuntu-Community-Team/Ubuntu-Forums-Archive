---
title: "Help me to connect to internet"
date: 2011-11-27
forum: General Help
---

### Post by asifnaz on 2011-11-27
I am using ubuntu 11.10 . This PC is connected(wired connection) to internet with windows 7 but I don't know how to connect it with ubuntu . 

I know User name and password but I don't know rest of the settings.

Here is what I have found with windows 7 

```
Connection-specific DNS Suffix: 
Description:                 buttcable
Physical Address: &#8206;
DHCP Enabled:                No
IPv4 Address:                10.0.1.200
IPv4 Subnet Mask:            255.255.255.255
IPv4 Default Gateway: 
IPv4 DNS Servers:             203.99.163.240, 203.99.163.243
IPv4 WINS Server: 
NetBIOS over Tcpip Enabled:    No
------------------------------------------------------------------------
Details 
Device name                         wan Miniport (PPPOE)
Device Type                         PPPoE
Authentication                      MS Chap V2
compression                         (none)
PPP multilink framing               off
client IPV 4 address                10.0.1.200
Server IPV 4 address                10.0.1.1
NAP state                           Not nap capable 
origin address                      unknown
destination address                 unknown 

--------------------------------------------------------------------------------------
General 

IPv4 connectivity      Internet                                             
IPv6 connectivity      No network access                                               
Media state            connected                                                   

```


I am a new user so please give me step by step answer .
and can anybody tell me what kind of connection I am using ..?

---

### Post by pqwoerituytrueiwoq on 2011-11-27
wired should auto connect and just work on config required
your desktop is connected via router right?

post the output of theses terminal commands
```
lspci | grep Ethernet
``````
ifconfig eth0
```

---

### Post by asifnaz on 2011-11-27
> **pqwoerituytrueiwoq said:**
> wired should auto connect and just work on config required
your desktop is connected via router right?

post the output of theses terminal commands
```
lspci | grep Ethernet
``````
ifconfig eth0
```

It is connected through DSL wire . The connection provider takes DSL internet connection and distributes it to other users .

It requires to put user name and password to connect  so does not connect automaticly . They did settings on windows 7 so it is working . but I dont know how to connect with Ubuntu **(I know username and password btw)**

---

### Post by asifnaz on 2011-11-27
```
asif@asif:~$ lspci | grep Ethernet
01:0c.0 Ethernet controller: Intel Corporation 82540EM Gigabit Ethernet Controller (rev 02)
asif@asif:~$ 



ifconfig eth0

asif@asif:~$ ifconfig eth0
eth0      Link encap:Ethernet  HWaddr 00:0d:56:fb:7b:b6  
          inet addr:192.168.3.41  Bcast:192.168.3.255  Mask:255.255.255.0
          inet6 addr: fe80::20d:56ff:fefb:7bb6/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:76 errors:0 dropped:0 overruns:0 frame:0
          TX packets:58 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:7933 (7.9 KB)  TX bytes:9431 (9.4 KB)
```


Sorry for double post . The connection is fine as I am writing these words using that (using windows 7 ) . I dont know how to apply these settings on ubuntu

**(actually I am asking how to create/edit connection using info I have provided )**

thank you

---

### Post by gandaran on 2011-11-27
> **asifnaz said:**
> It is connected through DSL wire . The connection provider takes DSL internet connection and distributes it to other users .

It requires to put user name and password to connect  so does not connect automaticly . They did settings on windows 7 so it is working . but I dont know how to connect with Ubuntu **(I know username and password btw)**
you should give a better description on how you connect using windows then we can help you with the right way to connect with ubuntu
now I will assume you have a computer DSL setup in windows (not a router configuration setup) if that is correct then the best and easy way to do it on ubuntu is open terminal and type
```
sudo pppoeconf
```
follow the prompts, type username and password, this should get your internet connected if your internet provider uses the pppoe DSL dial up protocol.

---

### Post by asifnaz on 2011-11-28
> **gandaran said:**
> you should give a better description on how you connect using windows then we can help you with the right way to connect with ubuntu
now I will assume you have a computer DSL setup in windows (not a router configuration setup) if that is correct then the best and easy way to do it on ubuntu is open terminal and type
```
sudo pppoeconf
```follow the prompts, type username and password, this should get your internet connected if your internet provider uses the pppoe DSL dial up protocol.

Oh My God . I don't have words to say thank you to . I was really worried but Ubuntu community never let me down .  I really appreciate your help .



Can you please double check for me if all is well now ..

                          ```
asif@asif:~$ plog
 Nov 28 23:03:36 asif pppd[1801]: Using interface ppp1
 Nov 28 23:03:36 asif pppd[1801]: Connect: ppp1 <--> eth0
 Nov 28 23:03:36 asif pppd[1801]: CHAP authentication succeeded
 Nov 28 23:03:36 asif pppd[1801]: peer from calling number 00:0D:56:CB:FA:15 authorized
 Nov 28 23:03:36 asif pppd[1801]: not replacing existing default route through ppp0
 Nov 28 23:03:36 asif pppd[1801]: local  IP address 10.0.1.217
 Nov 28 23:03:36 asif pppd[1801]: remote IP address 10.0.1.1
 Nov 28 23:03:36 asif pppd[1801]: primary   DNS address 203.99.163.240
 Nov 28 23:03:36 asif pppd[1801]: secondary DNS address 203.99.163.243
 asif@asif:~$ 

```Thank you again

---

