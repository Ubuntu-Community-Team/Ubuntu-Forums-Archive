---
title: "how to make a network script run at startup"
date: 2009-09-20
forum: General Help
---

### Post by MMoloch on 2009-09-20
Hello guys
 
I was putting together a old PC running ubuntu 9.04 to be an internet gateway and file sharing but whenever I restart the PC I lose all network settings.
I have no experience with linux and I need help making a script to run at startup with the following commands:
 
sudo dhclient eth0 - after this command I have to put my password
MY PASSWORD
sudo ifconfig eth1 192.168.10.100 netmask 255.255.255.0
sudo ifconfig eth2 192.168.0.1 netmask 255.255.255.0
sudo su -
modprobe iptable_nat
echo 1 > /proc/sys/net/ipv4/ip_forward
iptables -t nat -A POSTROUTING -o eth0 -j MASQUERADE
 
Can someone help me? Many thanks...
 
MMoloch

---

### Post by Liolikas on 2009-09-20
[http://embraceubuntu.com/2005/09/07/adding-a-startup-script-to-be-run-at-bootup/](http://embraceubuntu.com/2005/09/07/adding-a-startup-script-to-be-run-at-bootup/)
---
modprobe iptable_nat at startup is not normal you just want edit modprobe.conf and add it.

dhclient eth0 - after this command I have to put my password
MY PASSWORD - just set this in dhclient.conf.

And so clean up things:
```

ifconfig eth1 192.168.10.100 netmask 255.255.255.0
ifconfig eth2 192.168.0.1 netmask 255.255.255.0
echo 1 > /proc/sys/net/ipv4/ip_forward
iptables -t nat -A POSTROUTING -o eth0 -j MASQUERADE

```
And still those 2 first lines maybe not needed at all?

And iptables.conf file exist too so basicall you just want to edit correct .conf files and add your info. Just that echo command remains.

---

