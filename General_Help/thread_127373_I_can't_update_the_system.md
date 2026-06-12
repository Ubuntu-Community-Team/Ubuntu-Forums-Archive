---
title: "I can't update the system"
date: 2006-02-08
forum: General Help
---

### Post by lisux on 2006-02-08
Hi list.
I am trying to update the packages list from some ubuntu servers and it always fails.
I get errors like:
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) breezy-updates Release.gpg
  Could not connect to gb.archive.ubuntu.com:80 (1.0.0.0), connection timed out
Err [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security Release.gpg
  Could not connect to security.ubuntu.com:80 (1.0.0.0), connection timed out
Err [http://ftp.linux.it](http://ftp.linux.it) breezy Release.gpg
  Cannot initiate the connection to ftp.linux.it:80 (2001:1418:13:1::5). - conne
ct (101 Network is unreachable) [IP: 2001:1418:13:1::5 80]

I can see webpages and access to ftp sites, so my router have the 80, 20 and 21 ports opened, why apt-update can reach these servers?

Thanks

---

### Post by el3ktro on 2006-02-09
Perhaps the servers are down? You might try another server (like de.archive.ubuntu.com) - or do you have any weird proxy settings enabled somewhere? Do you use a proxy at all?

Tom

EDIT: Just looing at the output you pasted: It says that gb.archive.ubuntu.com has the IP 1.0.0.0 which definitely is not a valid IP address, and it seems that your machine tries to reach ftp.linux.it via an IPv6 address ... which also is very unlikely that it will work. Do you have any weird network settings? Can you post the content of /etc/network/interfaces & /etc/resolv.conf please?

Tom

---

### Post by lisux on 2006-02-20
Yes of course this is my /etc/network/interfaces :
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback
address 127.0.0.1
netmask 255.0.0.0

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
        script grep
        map eth0

# The primary network interface
iface eth0 inet dhcp

auto eth0

And this is the resolv.conf :
nameserver 192.168.1.1

I have disabled the loading of the ipv6 module.
So why the system is trying to reach to the repositories using ipv6?

Thanks

---

