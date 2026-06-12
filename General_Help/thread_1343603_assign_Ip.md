---
title: "assign Ip"
date: 2009-12-02
forum: General Help
---

### Post by malikge on 2009-12-02
Hello. 
I am new to Ubuntu. In windows I remember to assign Ip addresses:

Ip address: 
Subnet mask:
Default gateway:
Preferred DNS server:
Alternate DNS server:
and save it.

Now I want to know how to do this in Ubuntu. How can I assign all this in it.
Thanks.

---

### Post by Sef on 2009-12-02
How are you connecting to the internet?

---

### Post by lackoblacko on 2009-12-02
To change network settings in the gui, right click on the network manager and choose edit connections.


To change network settings in the terminal, go to edit the file located in /etc/network/interfaces as root and you will see
```

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inte loopback

#The primary network interface
auto eth0
iface eth0 inet dhcp

```

and configure to static ip, edit it to

```

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inte loopback

#The primary network interface
auto eth0
iface eth0 inet static
address 192.168.0.101
netmask 255.255.255.0
network 192.168.0.0
broadcast 192.168.0.255
gateway 192.168.0.1 

```

after that, save the file and restart the network by typing in 
```

/etc/init.d/networking restart

```
as root

---

### Post by byStanderone on 2009-12-02
...system>preference>network connection, and edit your ip adds. this is in karmic

---

### Post by malikge on 2009-12-03
Thanks guys...

---

