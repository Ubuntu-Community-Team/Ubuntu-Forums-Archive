---
title: "Setting a Static IP in the Terminal"
date: 2010-12-16
forum: General Help
---

### Post by tyler8886 on 2010-12-16
I've used Ubuntu for a couple of years now, but I was wondering how would you go about making a local static IP in the Terminal? Also, I had one more question, does anyone know how to install compiz? If so can you tell me how. thank you

---

### Post by Torombolo on 2010-12-16
> **tyler8886 said:**
> I've used Ubuntu for a couple of years now, but I was wondering how would you go about making a local static IP in the Terminal? Also, I had one more question, does anyone know how to install compiz? If so can you tell me how. thank you



For ubuntu 10.04

```
sudo apt-get install compiz  compiz-plugins compiz-gnome compiz-core emerald  compiz-fusion-plugins-main compiz-fusion-plugins-extra fusion-icon  compizconfig-settings-manager
```


Credit :

[http://www.hackourlives.com/install-compiz-fusion-and-emerald-in-ubuntu-10-04-lucid-lynx/](http://www.hackourlives.com/install-compiz-fusion-and-emerald-in-ubuntu-10-04-lucid-lynx/)

---

### Post by capscrew on 2010-12-16
> **tyler8886 said:**
> I've used Ubuntu for a couple of years now, but I was wondering how would you go about making a local static IP in the Terminal? 

Note your current IP address with this command
```
ifconfig
```
With that information you can edit the following file
```
/etc/network/interfaces

```
You need to check this file for DNS settings```
/etc/resolv.conf
```

Here is my /etc/network/interfaces file
```

>cat /etc/network/interfaces

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth1
iface eth1 inet static
        address 192.168.1.2
        netmask 255.255.255.0
        network 192.168.1.0
        broadcast 192.168.1.255
        gateway 192.168.1.1


```


Here is the information in the /etc/resolv.conf file
```

>cat /etc/resolv.conf

nameserver 192.168.1.1
nameserver 8.8.8.8
nameserver 8.8.4.4

``` 
> 
Also, I had one more question, does anyone know how to install compiz? If so can you tell me how. thank you

---

### Post by matt_symes on 2010-12-16
Hi 

At the terminal type

> man interfaces

to see the man page for /etc/network/interfaces

Kind regards

---

### Post by tyler8886 on 2010-12-16
thank you, this will do

---

