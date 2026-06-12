---
title: "Please help me setup a static IP in Ubuntu Server"
date: 2010-03-21
forum: General Help
---

### Post by OX!DE on 2010-03-21
Well basically the title :popcorn:

---

### Post by cbraxton on 2010-03-21
> **OX!DE said:**
> Well basically the title :popcorn:

Assuming for sake of example that the address you want is 192.168.1.100, gateway is 192.168.1.1, and the interface is eth0, you would use your favorite text editor to add the following to /etc/network/interfaces:

```

iface eth0 inet static
address 192.168.1.100
netmask 255.255.255.0
gateway 192.168.1.1
auto eth0

```

Then "sudo /etc/init.d/networking restart" (or reboot).

Obviously adjust the network settings for your own needs.

---

### Post by asmoore82 on 2010-03-21
The not-so-tricky tricky part about a Server with Static IP
is that it undercuts the use case of NetworkManager.
So I would just turn it off if it isn't already.

The first part of the Howto in my Signature covers that.

---

### Post by OX!DE on 2010-03-21
I will carry this on here [http://ubuntuforums.org/showthread.php?p=9007002&posted=1#post9007002](http://ubuntuforums.org/showthread.php?p=9007002&posted=1#post9007002) no need for 2 threads, thanks.

---

