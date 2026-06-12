---
title: "/etc/netowrk/interface settings"
date: 2012-10-13
forum: General Help
---

### Post by ibrahim.k on 2012-10-13
Hello there,

I am using a virtual ubuntu server machine as a VPN gateway.

Could you please let me know if these settings are correct?
This will be the gateway for users 192.168.70.1
This is the address of the router 192.167.61.1
These are my current settings.
[http://paste.ubuntu.com/1276269/](http://paste.ubuntu.com/1276269/)

Thnx in advance :)

---

### Post by Rexilion on 2012-10-13
# The primary network interface
iface eth0 inet static
        address 192.168.70.1 <-- this one is the same eth1 and not inside the network block
        netmask 255.255.255.0
        network 192.167.61.0
        gateway 192.167.61.1
        post-up iptables-restore < /etc/iptables.up.rules

iface eth1 inet static
        address 192.168.70.1
        netmask 255.255.255.0
        broadcast 192.168.70.255
        network 192.168.70.0

---

### Post by ibrahim.k on 2012-10-13
Thank you !!! 
I did nit notice that before.

---

