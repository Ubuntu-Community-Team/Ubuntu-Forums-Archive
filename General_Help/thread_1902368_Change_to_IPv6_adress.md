---
title: "Change to IPv6 adress"
date: 2011-12-30
forum: General Help
---

### Post by Skylyz on 2011-12-30
Hello !

I have a server with IPv6 adresses which i am willing to use, the only problem is that i don't know how. (i'm a complete newb !)

My /etc/network/interfaces looks like that : 

```
# This configuration file is auto-generated.
# Auto generated lo interface
auto lo
iface lo inet loopback

# Auto generated venet0 interface
auto venet0
iface venet0 inet manual
	up ifconfig venet0 up
	up ifconfig venet0 127.0.0.2
	up route add default dev venet0
	down route del default dev venet0
	down ifconfig venet0 down


iface venet0 inet6 manual
	up ifconfig venet0 add 2a02:xxxx:2:5:0:201:2153:13/128
	down ifconfig venet0 del 2a02:xxxx:2:5:0:201:2153:13/128
	up ifconfig venet0 add 2a02:xxxx:2:5:0:201:2153:12/128
	down ifconfig venet0 del 2a02:xxxx:2:5:0:201:2153:12/128
	up ifconfig venet0 add 2a02:xxxx:2:5:0:201:2153:11/128
	down ifconfig venet0 del 2a02:xxxx:2:5:0:201:2153:11/128
	up ifconfig venet0 add 2a02:xxxx:2:5:0:201:2153:10/128
	down ifconfig venet0 del 2a02:xxxx:2:5:0:201:2153:10/128

auto venet0:0
iface venet0:0 inet static
	address xx.yy.187.126
	netmask 255.255.255.0

auto venet0:1
iface venet0:1 inet static
	address xx.yy.187.94
	netmask 255.255.255.0

auto venet0:2
iface venet0:2 inet static
	address xx.yy.187.95
	netmask 255.255.255.0
```
(last 3 are my IPv4 adresses)

Do you know a way to use these IPv6 adresses please ? 

Thanks in advance. ^^

---

### Post by duncan12 on 2011-12-30
> Do you know a way to use these IPv6 adresses
I'm not sure if this is the answer you wanted, but if you want to change your local IP address to an IPv6 one, you can press the networking button in the notification bar, press Edit Connections, choose either your wireless or wired connection and press Edit, then set IPv4 to Disabled and IPv6 to whatever you want (DHCP, manual address etc.)

HTH

---

### Post by Skylyz on 2011-12-30
hello, thanks for your reply ! The problem is that i don't wanna change my local adress, these are internet IPs i wanna use to navigate on the internet. 
This is a VPS i work with, would changing the local settings affect my internet connection ? (i quite doubt that it would ^^)

---

### Post by duncan12 on 2011-12-30
OK so you want to set your *external* IP to IPv6 as opposed to your internal address. Sorry I don't really know about that - my guess would be that it's up to your ISP.

---

### Post by lemming465 on 2012-01-07
Could we see the output of **ip address show; ip -4 route show; ip -6 route show**?
Having an IPv6 address on an interface isn't enough; there has to be a path we can forward IPv6 packets over too.

---

