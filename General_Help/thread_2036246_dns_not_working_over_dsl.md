---
title: "dns not working over dsl"
date: 2012-08-01
forum: General Help
---

### Post by nersi on 2012-08-01
i connect to Internet via a pppoe connection that i configured manually as below:
/etc/ppp/peers/hamyar
#hamyar:
noipdefault
defaultroute
replacedefaultroute
hide-password
noauth
persist
plugin rp-pppoe.so eth0
user "********"
usepeerdns 

when i connect via "pon hamyar" everything works fine(i have ping response from any ip) except pinging to names like google.com and i cannot open it from my browser.
what shall i do?
here's plog information:

: Connected to 00:09:44:6c:e8:1a via interface eth0
: Using interface ppp0
: Connect: ppp0 <--> eth0
: PAP authentication succeeded
: peer from calling number 00:09:44:6C:E8:1A authorized
: replacing old default route to eth0 [192.168.1.20]
: local  IP address 178.173.139.142
: remote IP address 80.191.122.18
: primary   DNS address 80.191.122.5
: secondary DNS address 4.2.2.1

---

