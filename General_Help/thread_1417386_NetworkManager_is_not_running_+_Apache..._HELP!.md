---
title: "NetworkManager is not running + Apache... HELP!"
date: 2010-02-27
forum: General Help
---

### Post by robembra on 2010-02-27
Hi,

Yesturday all of a sudden my wired connection (Auto eth0) stopped working and apache wont work either as I can no longer connect to [http://localhost/](http://localhost/) it just loads and loads.



I have been searching the net for a solution and came across this:
```
installed file  /etc/network/interfaces –looks like this…. 
  
auto lo 
iface lo inet loopback 
 
edit  /etc/network/interfaces to look like this… 
 
auto eth0 
iface eth0 inet dhcp 
 
save that and connect; you may have to reboot
```I have done the above but now my connection works sometimes but my NetworkManager never shows the wired connection icon and always says "NetworkManager is not running"??

This is really anoying...only thing I can think of is that I have recently installed apache but it was all working fine till the other day.

Please help me!

---

### Post by robembra on 2010-02-28
BUMP...Please help!

---

### Post by amrypma on 2010-02-28
if you have done the above..
as root do:
```

ifdown eth0
ifup eth0

```

then check it with.
```
ifconfig
```

there should be eth0 listed with an adress listed.

oh. and check that your dhcp server is working. no use requesting an address if no one is listening.

--

If you didn't do the above.

try this.

```
sudo /etc/init.d/NetworkManager restart.
```

that restarts networking on just about all ubuntu desktop machiens.

---

