---
title: "ubuntu server 11.10 static ip assigning"
date: 2012-02-23
forum: General Help
---

### Post by pr3zident on 2012-02-23
i've searched on google and some stuff on this forum but nothing works. I'm trying to set a home file sever ...

this is how my /etc/networking/interface looks 
```

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
 address 192.168.0.100
 netmask 255.255.255.0
 network 192.168.0.0
 broadcast 192.168.0.255
 gateway 192.168.0.1

```

and i edited my /etc/resolv.conf too look like this 
```

nameserver 192.168.0.100
nameserver 192.168.0.100

```
but when i ping google it still says unknown host and i cant update.. im using a virtual machine network adapter is set to Bridged Adapter what am i doing wrong ?

---

### Post by zeljkojagust on 2012-02-23
Your address (192.168.0.100) of the machine is the same as the nameserver address in resolv.conf, which most probably is not true. Nameserver address is probably the same as the address of your gateway (I presume your physical machine is connected to internet over ADSL router). Try to change that.

---

### Post by pr3zident on 2012-02-23
> **zeljkojagust said:**
> Your address (192.168.0.100) of the machine is the same as the nameserver address in resolv.conf, which most probably is not true. Nameserver address is probably the same as the address of your gateway (I presume your physical machine is connected to internet over ADSL router). Try to change that.

ok im guessing my physical machine HAVE to be connected to the internet over ADSL router ? and im going to try and change my nameserver see what that does..

---

### Post by dcstar on 2012-02-24
> **pr3zident said:**
> i've searched on google and some stuff on this forum but nothing works. I'm trying to set a home file sever ...
.......
and i edited my /etc/resolv.conf too look like this 
```

nameserver 192.168.0.100
nameserver 192.168.0.100

```
but when i ping google it still says unknown host and i cant update.. im using a virtual machine network adapter is set to Bridged Adapter what am i doing wrong ?

You don't have a DNS server running on 192.168.0.100.

If you want to set that up then do a Google search on the subject.

---

