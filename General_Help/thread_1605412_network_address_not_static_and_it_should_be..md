---
title: "network address not static and it should be."
date: 2010-10-25
forum: General Help
---

### Post by ant2ne on 2010-10-25
using server 10.4, on reboot this devices does not "auto eth0" and requires me to log in and tell it ""ifup eth0". Even then, it doesn't have its static IP address and attempts to get one from dhcp. Which is a fail, seeing as how this device IS the dhcp server. 

```
ant2ne@cygnenos:~$ cat /etc/network/interfaces
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

## The primary network interface
#auto eth0
#iface eth0 inet dhcp

#My Static assigned
auto eth0
allow-hotplug eth0
iface eth0 inet static
address 192.168.1.3
netmask 255.255.255.0
broadcast 192.168.1.255
gateway 192.168.1.1
```
any advice?

---

### Post by Wayne_V on 2010-10-25
If you have network manager installed (dpkg --list | grep -i network-manager) try removing it.  NetworkManager will make your life hell if you are trying to manually configure your network.

---

### Post by ant2ne on 2010-10-25
no network manager installed.

---

### Post by ant2ne on 2010-10-25
dang, I think I fixed it. I didn't have a line "network 192.168.1.0" specified for that iface in /etc/network/interfaces file. You'd think that the broadcast would have been enough. I rebooted and the device came back up automatically with the correct IP.

---

### Post by Wayne_V on 2010-10-25
Right after boot, before trying to ifup anything, what is the output of:

# ifconfig -a

# dmesg | grep -i eth

And does "sudo /etc/init.d/networking restart" yield any different results than just "ifup eth0" ?

---

### Post by Wayne_V on 2010-10-25
Interesting ... I didn't think "network" was a required parameter either.

---

