---
title: "just installed 11.10, and have network issues."
date: 2012-01-29
forum: General Help
---

### Post by ulao on 2012-01-29
After my upgrade I get this waiting for network, then another message saying will wait 60 more seconds. I tried advice I found on the net about remarking the auto's but didnt help. Once the system is up i can bring my network up but the systems behind my network are struggling to get though the linux firewall. By passing linux works fine. Is this a known issue with 11.10, or can I some how role back to 10.10?

---

### Post by fhgaminguk on 2012-01-29
> **ulao said:**
> After my upgrade I get this waiting for network, then another message saying will wait 60 more seconds. I tried advice I found on the net about remarking the auto's but didnt help. Once the system is up i can bring my network up but the systems behind my network are struggling to get though the linux firewall. By passing linux works fine. Is this a known issue with 11.10, or can I some how role back to 10.10?

I assume that you are having trouble with wireless? If you are, this is a known problem inside 11.10. It can be fixed. If you are getting the "firmware"  issue when searching for wireless, you will need to search the ubuntu software centre for the correct drivers. You can find out what wireless you have by typing in a certain command into terminal (I have forgotten what it is) then search the software centre for the correct drivers :)

---

### Post by ulao on 2012-01-29
No I read that also, but I dont have or want any wires connection from this box. I'd be happy disabling it all.

Could the fact I'm not getting my eth0 auto up be someting else?

here is my interface file:

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet dhcp
#pre-up iptables-restor < /etc/iptables.up.rules
iface eth0:1 inet static
address 192.168.0.19
netmask 255.255.255.0
network 192.168.0.0
roadcast 192.168.0.255


Should I just remove the sleep lines in failsafe.conf if this is not related?

---

### Post by ulao on 2012-01-29
This first the majority of my problems.

```
sudo mv /var/run/* /run/
sudo mv /var/lock/* /run/lock/
sudo rm -r /var/run
sudo rm -r /var/lock
sudo ln -s /run /var/run
sudo ln -s /run/lock /var/lock
sudo rm /run/dbus/*
```

To fix the fire wall issue I did this
```
ptables -t mangle -A FORWARD -p tcp --tcp-flags SYN,RST SYN -j TCPMSS --clamp-mss-to-pmtu
```

---

### Post by grahammechanical on 2012-01-29
My interfaces files has only this in it:

> auto lo
iface lo inet loopback


It is my understanding that Network Manager needs to only have those lines in this file. On one occasion other information was put in that file on my machine and I could not get access to my router until I removed the extra lines.

So, I think that you have a choice:

1) to let network manager - manage your network connections.

2) un-install network manager and use some other utility to manage networks, a utility that uses the interfaces file.

I am sure that network manager does not use the interfaces file but requires it to only have those two lines.

Do you have another network utility installed that is causing a conflict with network manager?

Regards.

---

### Post by ulao on 2012-01-29
I read that also where. I never could get network manager to load. But this was back to 8.10. I may have to give that a go again.

---

