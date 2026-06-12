---
title: "VPN issue ? Need help"
date: 2012-02-11
forum: General Help
---

### Post by Hypnopirate on 2012-02-11
Im trying to use a VPN ..Anonine to be exact 

Ive followed these instructions >
**Command-line based start:**             

[LIST]
[*]1. Install openvpn package by using apt-get install openvpn
[*]2. Extract anonine_openvpn.zip ([download here]("https://www.anonine.com/files/anonine_openvpn.zip")) into /home/<USERNAME>/openvpn              directory
[*]3. Start connection with:
               sudo openvpn --client --config $HOME/openvpn/anonine.ovpn --ca $HOME/openvpn/anonine.ca.crt
[*]4. Enter username
[*]5. Enter password
[/LIST]
It lets me log in .. but then I cant connect to any webpages they all seem to time out ..  am I not doing something right ?is there a set up I need to do? ..  Im completely new to this .. so please write it out plainly and clear as if I knew nothing about vpns or ubuntu .. cause I dont ..lol

---

### Post by k999 on 2012-02-12
You'll need to do a bit more debugging and find some more information. Check:

* which interfaces do you have, and what IP-adresses are they on, especially one called tun0 or tap0: ifconfig -a
* check all your network routes: route -an
* check your DNS resolver configuration: cat /etc/resolv.conf
* try watching what data is transferred on different network interfaces when you try to connect: tcpdump -i <device>
* check any firewall rules you have that might block traffic: iptables-save

---

### Post by Hypnopirate on 2012-02-12
Umm yeah I dont have any clue what any of that mean ..  I think Ill just give up while Im ahead

---

### Post by Prospero2006 on 2012-02-12
You know, I run openvpn myself and somehow the direct connection quit working for web pages. (Not sure exactly myself.) You can install either squid or privoxy and use that to facilitate things. I dropped squid on the vpn server and it works just fine for me now.

---

