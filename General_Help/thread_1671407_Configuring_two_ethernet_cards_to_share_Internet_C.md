---
title: "Configuring two ethernet cards to share Internet Connection"
date: 2011-01-20
forum: General Help
---

### Post by tuxmanic on 2011-01-20
Hai all

for some development purpose i need to share my Internet connection between PC (Ubuntu 10.04.1 LTS)  & a Development board (Angstrom Linux 2010.7 ) to install packages on development board, but my ADSL modem has only one Ethernet port so i  added one more Ethernet card into the PC for the purpose

With the help of friends & ' [https://help.ubuntu.com/10.04/serverguide/C/network-configuration.html](https://help.ubuntu.com/10.04/serverguide/C/network-configuration.html) ' i did the following setup  (as shown in fig) also enabled ipv4 forwarding & masquerading.

```
sudo iptables --table nat --append POSTROUTING --out-interface eth0 -j MASQUERADE
sudo iptables --append FORWARD --in-interface eth1 -j ACCEPT
```Now i can ping Modem along with both eth0 & eth1 from development board also external ips (like 8.8.8.8 , but fails with host name, in short it fails to resolve the domain name. I tried eth1(192.168.2.2), Modem(192.168.1.1) and 8.8.8.8 etc as nameserver for the development board but problem still remains.so some help please.

All the configurations are manually done and removed network manager from main PC

[CENTER][IMG]http://img15.imageshack.us/img15/3430/blockdia.png[/IMG]
[LEFT]
Hope that my post is in the correct section. Thanks in advance... :)
[/LEFT]
 [/CENTER]

---

### Post by tuxmanic on 2011-01-21
Finally solved the problem with the help one of my linux friend.

The issue was with the 'resolv.conf' in the development board , i put only the ip of DNS but no the word nameserver. Just added the the word 'nameserver' in front of ip and now its working

```
nameserver 8.8.8.8
```

Credit goes to Basil ([ http://wiki.basil-kurian.co.cc/index.php/Main_Page]("http://wiki.basil-kurian.co.cc/index.php/Main_Page") )

---

