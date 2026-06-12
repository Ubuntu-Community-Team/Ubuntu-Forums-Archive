---
title: "DSL connectivity"
date: 2011-04-22
forum: General Help
---

### Post by shashanksingh on 2011-04-22
I have an issue with my DSL connectivity (Ubuntu: 10.10).
It takes around 5 or more attempts on an average to connect using DSL connection, nm-applet.
:mad:
I also have windows7 on my system and it works smooth in it.

Is there a driver problem???
I have attatched a few lshw details that may be of help

---

### Post by sknagesh on 2011-04-22
posting your syslog may help.

---

### Post by shashanksingh on 2011-04-22
Here's my syslog

---

### Post by dineshs on 2011-04-23
If you have a modem or router see if you can ping the modem IP.```
ping -c3 192.168.1.1
```assuming that 192.168.1.1 is the modem/router IP.
If there is no reply try running ```
sudo dhclient eth0
``` and post the result.
If you get reply try configuring modem in PPPoE mode.
Also post the output of the following command [COLOR="Red"](windows)[/COLOR] when the connection is OK
```
ipconfig /all
```

---

### Post by shashanksingh on 2011-04-23
> **dineshs said:**
> If you have a modem or router see if you can ping the modem IP.```
ping -c3 192.168.1.1
```assuming that 192.168.1.1 is the modem/router IP.
If there is no reply try running ```
sudo dhclient eth0
``` and post the result.
If you get reply try configuring modem in PPPoE mode.
Also post the output of the following command [COLOR="Red"](windows)[/COLOR] when the connection is OK
```
ipconfig /all
```

I do not have a modem/router. I think its a direct p-2-p connection, the line goes from my machine to somewhere outside I dont know.

I have attatched ipconfig /all before and after connecting in Windows 7

---

### Post by shashanksingh on 2011-04-23
Here's the relevant part of my syslog before and after the connection


Before

18:40:40 user-PC NetworkManager[823]: <info> Activation (eth0) starting connection 'DSL connection 1'
18:40:40 user-PC NetworkManager[823]: <info> (eth0): device state change: 3 -> 4 (reason 0)
18:40:40 user-PC NetworkManager[823]: <info> Activation (eth0) Stage 1 of 5 (Device Prepare) scheduled...
18:40:40 user-PC NetworkManager[823]: <info> Activation (eth0) Stage 1 of 5 (Device Prepare) started...
18:40:40 user-PC NetworkManager[823]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) scheduled...
18:40:40 user-PC NetworkManager[823]: <info> Activation (eth0) Stage 1 of 5 (Device Prepare) complete.
18:40:40 user-PC NetworkManager[823]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) starting...
18:40:40 user-PC NetworkManager[823]: <info> (eth0): device state change: 4 -> 5 (reason 0)
18:40:40 user-PC NetworkManager[823]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) successful.
18:40:40 user-PC NetworkManager[823]: <info> Activation (eth0) Stage 3 of 5 (IP Configure Start) scheduled.
18:40:40 user-PC NetworkManager[823]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) complete.
18:40:40 user-PC NetworkManager[823]: <info> Activation (eth0) Stage 3 of 5 (IP Configure Start) started...
18:40:40 user-PC NetworkManager[823]: <info> (eth0): device state change: 5 -> 7 (reason 0)
18:40:40 user-PC NetworkManager[823]: <info> starting PPP connection
18:40:40 user-PC NetworkManager[823]: <info> pppd started with pid 1994
18:40:40 user-PC NetworkManager[823]: <info> Activation (eth0) Stage 3 of 5 (IP Configure Start) complete.
18:40:40 user-PC pppd[1994]: Plugin rp-pppoe.so loaded.
18:40:40 user-PC pppd[1994]: RP-PPPoE plugin version 3.8p compiled against pppd 2.4.5
18:40:40 user-PC dnsmasq-dhcp[1190]: DHCP packet received on eth0 which has no address
18:40:40 user-PC pppd[1994]: Plugin /usr/lib/pppd/2.4.5/nm-pppd-plugin.so loaded.
18:40:40 user-PC pppd[1994]: pppd 2.4.5 started by root, uid 0
18:40:40 user-PC dnsmasq-dhcp[1190]: DHCP packet received on eth0 which has no address
18:41:11 user-PC dnsmasq-dhcp[1190]: last message repeated 265 times
18:41:11 user-PC NetworkManager[823]: <warn> pppd timed out or didn't initialize our dbus module
18:41:11 user-PC NetworkManager[823]: <info> (eth0): device state change: 7 -> 9 (reason 14)
18:41:11 user-PC NetworkManager[823]: <info> Marking connection 'DSL connection 1' invalid.
18:41:11 user-PC NetworkManager[823]: <warn> Activation (eth0) failed.
18:41:11 user-PC NetworkManager[823]: <info> (eth0): device state change: 9 -> 3 (reason 0)
18:41:11 user-PC NetworkManager[823]: <info> (eth0): deactivating device (reason: 0).
18:41:11 user-PC dnsmasq-dhcp[1190]: DHCP packet received on eth0 which has no address

After

18:41:28 user-PC NetworkManager[823]: <info> Activation (eth0) starting connection 'DSL connection 1'
18:41:28 user-PC NetworkManager[823]: <info> (eth0): device state change: 3 -> 4 (reason 0)
18:41:28 user-PC NetworkManager[823]: <info> Activation (eth0) Stage 1 of 5 (Device Prepare) scheduled...
18:41:28 user-PC NetworkManager[823]: <info> Activation (eth0) Stage 1 of 5 (Device Prepare) started...
18:41:28 user-PC NetworkManager[823]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) scheduled...
18:41:28 user-PC NetworkManager[823]: <info> Activation (eth0) Stage 1 of 5 (Device Prepare) complete.
18:41:28 user-PC NetworkManager[823]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) starting...
18:41:28 user-PC NetworkManager[823]: <info> (eth0): device state change: 4 -> 5 (reason 0)
18:41:28 user-PC NetworkManager[823]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) successful.
18:41:28 user-PC NetworkManager[823]: <info> Activation (eth0) Stage 3 of 5 (IP Configure Start) scheduled.
18:41:28 user-PC NetworkManager[823]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) complete.
18:41:28 user-PC NetworkManager[823]: <info> Activation (eth0) Stage 3 of 5 (IP Configure Start) started...
18:41:28 user-PC NetworkManager[823]: <info> (eth0): device state change: 5 -> 7 (reason 0)
18:41:28 user-PC NetworkManager[823]: <info> starting PPP connection
18:41:28 user-PC NetworkManager[823]: <info> pppd started with pid 1997
18:41:28 user-PC NetworkManager[823]: <info> Activation (eth0) Stage 3 of 5 (IP Configure Start) complete.
18:41:28 user-PC pppd[1997]: Plugin rp-pppoe.so loaded.
18:41:28 user-PC pppd[1997]: RP-PPPoE plugin version 3.8p compiled against pppd 2.4.5
18:41:28 user-PC dnsmasq-dhcp[1190]: DHCP packet received on eth0 which has no address
18:41:28 user-PC dnsmasq-dhcp[1190]: DHCP packet received on eth0 which has no address
18:41:28 user-PC pppd[1997]: Plugin /usr/lib/pppd/2.4.5/nm-pppd-plugin.so loaded.
18:41:28 user-PC pppd[1997]: pppd 2.4.5 started by root, uid 0
18:41:28 user-PC pppd[1997]: PPP session is 259
18:41:28 user-PC kernel: [  172.579887] NET: Registered protocol family 24
18:41:28 user-PC pppd[1997]: Connected to 00:21:5e:6b:57:e9 via interface eth0
18:41:28 user-PC modem-manager: (net/ppp0): could not get port's parent device
18:41:28 user-PC NetworkManager[823]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/virtual/net/ppp0, iface: ppp0)
18:41:28 user-PC NetworkManager[823]:    SCPlugin-Ifupdown: device added (path: /sys/devices/virtual/net/ppp0, iface: ppp0): no ifupdown configuration found.
18:41:28 user-PC pppd[1997]: Using interface ppp0
18:41:28 user-PC pppd[1997]: Connect: ppp0 <--> eth0
18:41:28 user-PC pppd[1997]: CHAP authentication succeeded
18:41:28 user-PC pppd[1997]: CHAP authentication succeeded
18:41:28 user-PC pppd[1997]: peer from calling number 00:21:5E:6B:57:E9 authorized
18:41:28 user-PC pppd[1997]: Cannot determine ethernet address for proxy ARP
18:41:28 user-PC pppd[1997]: local  IP address 27.124.29.5
18:41:28 user-PC pppd[1997]: remote IP address 27.124.3.2
18:41:28 user-PC pppd[1997]: primary   DNS address 115.69.240.12
18:41:28 user-PC pppd[1997]: secondary DNS address 115.69.240.11
18:41:28 user-PC NetworkManager[823]: <info> PPP manager(IP Config Get) reply received.
18:41:28 user-PC NetworkManager[823]: <info> Activation (eth0) Stage 4 of 5 (IP4 Configure Get) scheduled...
18:41:28 user-PC NetworkManager[823]: <info> Activation (eth0) Stage 4 of 5 (IP4 Configure Get) started...
18:41:28 user-PC NetworkManager[823]: <info> Activation (eth0) Stage 5 of 5 (IP Configure Commit) scheduled...
18:41:28 user-PC NetworkManager[823]: <info> Activation (eth0) Stage 4 of 5 (IP4 Configure Get) complete.
18:41:28 user-PC NetworkManager[823]: <info> Activation (eth0) Stage 5 of 5 (IP Configure Commit) started...
18:41:28 user-PC dnsmasq-dhcp[1190]: DHCP packet received on eth0 which has no address
18:41:29 user-PC dnsmasq-dhcp[1190]: last message repeated 10 times
18:41:29 user-PC NetworkManager[823]: <info> (eth0): device state change: 7 -> 8 (reason 0)
18:41:29 user-PC NetworkManager[823]: <info> Policy set 'DSL connection 1' (ppp0) as default for IPv4 routing and DNS.
18:41:29 user-PC NetworkManager[823]: <info> Updating /etc/hosts with new system hostname
18:41:29 user-PC NetworkManager[823]: <info> Activation (eth0) successful, device activated.
18:41:29 user-PC NetworkManager[823]: <info> Activation (eth0) Stage 5 of 5 (IP Configure Commit) complete.
18:41:29 user-PC nm-dispatcher.action: nm_dispatcher_action: Invalid connection: '(null)' / 'connection setting not found' invalid: 1
18:41:29 user-PC nm-dispatcher.action: Script '/etc/NetworkManager/dispatcher.d/01ifupdown' exited with error status 1.
18:41:29 user-PC dnsmasq-dhcp[1190]: DHCP packet received on eth0 which has no address
18:41:30 user-PC dnsmasq-dhcp[1190]: last message repeated 2 times
18:41:30 user-PC dnsmasq[1190]: reading /etc/resolv.conf
18:41:30 user-PC dnsmasq[1190]: using nameserver 115.69.240.11#53
18:41:30 user-PC dnsmasq[1190]: using nameserver 115.69.240.12#53
18:41:30 user-PC dnsmasq-dhcp[1190]: DHCP packet received on eth0 which has no address
18:41:41 user-PC dnsmasq-dhcp[1190]: last message repeated 19 times
18:41:41 user-PC ntpdate[2071]: step time server 91.189.94.4 offset 9.869884 sec
18:41:41 user-PC dnsmasq-dhcp[1190]: DHCP packet received on eth0 which has no address

---

### Post by dineshs on 2011-04-24
I think you are using [this]("http://ubuntuforums.org/showpost.php?p=9611335&postcount=9") method at present.
Please try method 2[ here]("http://ubuntuforums.org/showpost.php?p=9922561&postcount=2") and see if there is any difference.
.Please also post the result of ```
plog
```when the connection is not working

---

### Post by shashanksingh on 2011-04-24
> **dineshs said:**
> I think you are using [this]("http://ubuntuforums.org/showpost.php?p=9611335&postcount=9") method at present.
Please try method 2[ here]("http://ubuntuforums.org/showpost.php?p=9922561&postcount=2") and see if there is any difference.
.Please also post the result of ```
plog
```when the connection is not working
I tried pppoeconf but it gets stuck at 100% just after detecting PPPOE packets at interface eth0.
Ill still try it again soon and also post the plog next time

---

### Post by shashanksingh on 2011-04-24
Here's op of plog when its not working

Apr 24 17:38:53 shashank-PC pppd[7836]: Exit.

---

### Post by shashanksingh on 2011-04-26
> **dineshs said:**
> I think you are using [this]("http://ubuntuforums.org/showpost.php?p=9611335&postcount=9") method at present.
Please try method 2[ here]("http://ubuntuforums.org/showpost.php?p=9922561&postcount=2") and see if there is any difference.
.Please also post the result of ```
plog
```when the connection is not working

I tried pppoeconf but the connection still has the same issue, doesn't work in the first few tries.

Also, the nm-applet icon has just disappeared after pppoe.
When I run nm-applet from terminal, it says an instance of it is already running.

---

### Post by dineshs on 2011-04-27
> Also, the nm-applet icon has just disappeared after pppoe.Please run ```
sudo gedit /etc/network/interfaces
```Edit the file so that it contain only```
auto lo
iface lo inet loopback
```Now run```
sudo service network-manager restart
```(or restart system).
> I tried pppoeconf but the connection still has the same issue, doesn't work in the first few tries.
After doing the above steps connect using pon dsl-provider ,wait for say 10 seconds then do```
ping 4.2.2.1 -c3
```and see if there is reply (when you have issue)
BTW What does ```
cat /etc/resolv.conf 
```say about DNS ?

---

### Post by shashanksingh on 2011-04-28
/etc/resolv.conf

# Generated by NetworkManager
nameserver 115.69.240.12
nameserver 115.69.240.11

the nm applet is back, but im again back to the same place

both network-manager and pppoeconf do not give me a good success rate at connecting in the first few attempts, it just dsnt happen sometimes

---

### Post by shashanksingh on 2011-04-28
> **dineshs said:**
> Please run ```
sudo gedit /etc/network/interfaces
```Edit the file so that it contain only```
auto lo
iface lo inet loopback
```Now run```
sudo service network-manager restart
```(or restart system).

After doing the above steps connect using pon dsl-provider ,wait for say 10 seconds then do```
ping 4.2.2.1 -c3
```and see if there is reply (when you have issue)
BTW What does ```
cat /etc/resolv.conf 
```say about DNS ?

user@user-PC:~$ ping 4.2.2.1 -c3
PING 4.2.2.1 (4.2.2.1) 56(84) bytes of data.
64 bytes from 4.2.2.1: icmp_req=1 ttl=57 time=327 ms
64 bytes from 4.2.2.1: icmp_req=2 ttl=57 time=345 ms
64 bytes from 4.2.2.1: icmp_req=3 ttl=57 time=334 ms

It seems to work fine

---

### Post by dineshs on 2011-04-29
```
both network-manager and pppoeconf do not give me a good success rate at connecting in the first few attempts, it just dsnt happen sometimes
user@user-PC:~$ ping 4.2.2.1 -c3
PING 4.2.2.1 (4.2.2.1) 56(84) bytes of data.
64 bytes from 4.2.2.1: icmp_req=1 ttl=57 time=327 ms
64 bytes from 4.2.2.1: icmp_req=2 ttl=57 time=345 ms
64 bytes from 4.2.2.1: icmp_req=3 ttl=57 time=334 ms
It seems to work fine 
```
If you are able to ping 4.2.2.1 even when you have difficulty in getting sites it could be a DNS issue.Please do```
sudo gedit /etc/resolv.conf
```
Edit the file as follows```
# Generated by NetworkManager
nameserver 4.2.2.1
nameserver 8.8.8.8
```
Connect using *sudo pon dsl-provider* and see if there is any progress.
[COLOR="Red"]OR[/COLOR]
Rightclick network manager icon -edit connections-DSL-select your connection-edit-ipv4 settings-Method=Automatic(pppoe)addresses only-enter DNS as```
4.2.2.1,8.8.8.8
```then apply.(note that the DNS addresses are seperated by a comma)
Now connect DSL via NM ie click on network manager icon click DSL connection and connect, then pl see.

---

### Post by shashanksingh on 2011-05-05
Guess what...

I upgraded to ubuntu 11.04 and no more problems with the connectivity anymore.
I think it was some driver problem with 10.10.

---

