---
title: "network configure problem"
date: 2009-11-08
forum: General Help
---

### Post by weishigoname on 2009-11-08
I am using ubuntu 9.04 ,when I edit /etc/network/interfaces :
[INDENT]sudo vi /etc/network/interfaces
[/INDENT] [INDENT]auto eth0
iface eth0 inet static
address 192.168.1.90
gateway 192.168.1.1
netmask 255.255.255.0
network 192.168.1.0
broadcast 192.168.1.255


and 
[INDENT]sudo vi /etc/resolv.conf
[/INDENT][INDENT]search 192.168.1.1
nameserver 192.168.1.1


192.168.1.1 is  router

[/INDENT][/INDENT]after that ,my network does not work,the icon of network show that it is disabled.

---

### Post by Psycho.mario on 2009-11-08
That file and network-manager do not play nice. If you disable network manager on startup (System>Preferences>Startup Applications) it should work, but sometimes even that does not work.

---

### Post by blueridgedog on 2009-11-08
> **weishigoname said:**
> 
and 
[INDENT]sudo vi /etc/resolv.conf
[/INDENT][INDENT]search 192.168.1.1
nameserver 192.168.1.1
192.168.1.1 is  router

[/INDENT][/INDENT].

As Psycho.mario stated, you can have one or the other (manual or gnome app).

Also, you are pointing your DNS settings to your router.  That may be the source of your error as well.  Your name server is probably upstream of your router.  You may be able to log in to your router and the IP of the DNS server it recieved along with its DHCP IP address and use that.

---

### Post by Iowan on 2009-11-08
What you've done *should* work (although you could do something similar under Network Manager Manual configuration). Did you restart/reboot (I prefer reboot to restart/resync everything)? Network manager will complain, but networking *should* work.

(Network Manager may still try to overwrite */etc/resolv.conf*)

---

