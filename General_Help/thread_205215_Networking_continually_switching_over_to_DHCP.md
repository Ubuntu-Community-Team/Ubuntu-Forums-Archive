---
title: "Networking continually switching over to DHCP"
date: 2006-06-28
forum: General Help
---

### Post by rupy on 2006-06-28
I have statically configured my local network settings as follows:
> 
auto lo
iface lo inet loopback
address 127.0.0.1
netmask 255.0.0.0

auto eth0
iface eth0 inet static
address 172.16.236.151
netmask 255.255.0.0
gateway 172.16.236.254


And it works, but after a few hours it seems to try and route out of a different gateway. I assume that its our DHCP server giving my machine new settings, but why would it be changing if I have specified the interface to be static.

I basically have to run "sudo ifdown eth0" and then "sudo ifup eth0" to fix it, but its hella annoying.

---

### Post by dcstar on 2006-06-28
[QUOTE=rupy]I have statically configured my local network settings as follows:


And it works, but after a few hours it seems to try and route out of a different gateway. I assume that its our DHCP server giving my machine new settings, but why would it be changing if I have specified the interface to be static.

I basically have to run "sudo ifdown eth0" and then "sudo ifup eth0" to fix it, but its hella annoying.[/QUOTE]
If something on your network is sending out routing packets, that could be the problem.

If your DHCP server is set up to pump out RIP (or other routing protocols), see if you can turn them off.

---

### Post by rupy on 2006-06-28
Its a pretty massive office network and I don't think anyone else is getting this. They must be sending out some packets that are messing with my network settings, but surely me having it set to static should stop it.

Isnt there some setting I can enable to force my interface to "ignore" their packets?

---

### Post by rupy on 2006-07-01
I figured it out - It was the dhclient process(s)

---

