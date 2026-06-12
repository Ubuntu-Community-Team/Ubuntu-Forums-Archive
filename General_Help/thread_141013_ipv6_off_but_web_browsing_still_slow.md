---
title: "ipv6 off but web browsing still slow"
date: 2006-03-07
forum: General Help
---

### Post by s|k on 2006-03-07
I turned off ipv6 both in Firefox 1.5 in the about:config and on the system by editing /etc/modprobe.d/aliases but DNS look up still seems to be taking forever. It's slow in Konqueror too. I've read through the other threads about it, but none of that seems to help. It's not a Firefox configuration issue, I'm sure, but if you have suggestions please let me know! Thank you.

---

### Post by cyberb0b on 2006-03-07
so... what is your network setup like?  Ethernet card using DHCP plugged into router plugged into cable modem?  Did you manually enter DNS server IP addresses that your ISP told you to enter?  etc.  just need some info :) 

System->Administration->Networking, click on the ethernet card, properties, look for the list of DNS servers (going from memory here...)

Whatcha got?  Does it work if you remove all your DNS entries.  Does DHCP add entries? Does it work if you just enter the IP address of your router?  Am I asking too many questions at once?

---

### Post by s|k on 2006-03-07
[QUOTE=cyberb0b]so... what is your network setup like?  Ethernet card using DHCP plugged into router plugged into cable modem?  Did you manually enter DNS server IP addresses that your ISP told you to enter?  etc.  just need some info :) 

System->Administration->Networking, click on the ethernet card, properties, look for the list of DNS servers (going from memory here...)

Whatcha got?  Does it work if you remove all your DNS entries.  Does DHCP add entries? Does it work if you just enter the IP address of your router?  Am I asking too many questions at once?[/QUOTE]
It says DHCP. I'm not using a router locally (I barely know what a router is) or what the IP to it is. I use a cable ISP and my IP isn't static. Does that help? :0

---

### Post by codejunkie on 2006-03-07
[QUOTE=s|k]I turned off ipv6 both in Firefox 1.5 in the about:config and on the system by editing /etc/modprobe.d/aliases but DNS look up still seems to be taking forever. It's slow in Konqueror too. I've read through the other threads about it, but none of that seems to help. It's not a Firefox configuration issue, I'm sure, but if you have suggestions please let me know! Thank you.[/QUOTE]
i don't know if this will help your firefox speed but this does help Konqueror and other apps in kde.
run
```
sudo kwrite /etc/environment
```
add this line to the file
```
KDE_NO_IPV6=true
```
save and reboot this seemed to give me a big speed inprovement in kde.

---

### Post by s|k on 2006-03-07
[QUOTE=codejunkie]i don't know if this will help your firefox speed but this does help Konqueror and other apps in kde.
run
```
sudo kwrite /etc/environment
```
add this line to the file
```
KDE_NO_IPV6=true
```
save and reboot this seemed to give me a big speed inprovement in kde.[/QUOTE]
I'm using gnome. :/

---

### Post by s|k on 2006-03-07
I fixed it. I edited  /etc/resolv.conf and removed the search line and an IP that didn't seem to be up.

It's blazing fast now!

Thanks. :)

---

