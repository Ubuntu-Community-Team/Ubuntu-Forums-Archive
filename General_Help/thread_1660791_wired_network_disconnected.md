---
title: "wired network disconnected"
date: 2011-01-05
forum: General Help
---

### Post by bobke on 2011-01-05
I'm trying to connect to the internet and get a msg: "Wired network disconnected you are now offline". When I change to online mode and click the network icon for "Auto eth0" I get the msg. I don't have any wireless connected and set up.

Lucid LTS is a new install on this computer dual boot w/ winxp. XP connects for both firefox and outlook express. So I know the physical connection is ok. 

 FYI - 
/etc/network/interfaces:
auto lo
iface lo inet loopback

I had trouble booting and have to boot noapic, if this has any bearing on the situation. Also, right after first bootup, this connection worked great and was surfing the internet just fine. Then I got on computer today and can't connect. Hopefully only a simple adjustment , me thinks, but don't know how!

PowerSpec mod B634 160gb/864 ram/Geforce 7300 pci-e/intel celeron D

---

### Post by bobke on 2011-01-12
I'm booting fine now and have internet connection. I don't know what happened here, but simply turned off the computer and unplugged it. Then rebooted this time 'noapic acpi=off' and everything works great so far.

---

