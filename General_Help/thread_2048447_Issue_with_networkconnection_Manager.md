---
title: "Issue with network/connection Manager"
date: 2012-08-26
forum: General Help
---

### Post by asnd16 on 2012-08-26
I just installed Xubuntu on one of my older machines.  All is well except the only way I can get the network card active or to get internet I have to go into terminal and type 
> sudo dhclient eth0


How can I get the network connection manager working?

---

### Post by asnd16 on 2012-08-30
bump  - - umm  hello ?  Here is a screeshot of the issue.  

[IMG]http://i23.photobucket.com/albums/b363/j1232/Screenshot-08302012-025528AM.png[/IMG]

notice the manager states that it is not managed.  Soooooo how do I get it to say managed?

---

### Post by steeldriver on 2012-08-30
a device would normally be 'not managed' by NetworkManager if it has a connection already defined in /etc/network/interfaces - did you modify that file?

---

### Post by asnd16 on 2012-09-01
I have not modified the file but this is what is in the file 

> 
# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
#NetworkManager

iface eth0 inet dhcp
# This is an autoconfigured IPv6 interface
iface eth0 inet6 auto


---

### Post by steeldriver on 2012-09-01
I would try commenting out (using # at the start of each line) everything except 

```

# The loopback network interface 
auto lo 
iface lo inet loopback

```

and then restart the services

```

sudo service networking restart 
sudo service network-manager restart

```

This should set everything back to the out-of-the-box state for a 'desktop' (non-server) installation, with network-manager controlling everything

---

### Post by asnd16 on 2012-09-01
This is what I get when I try the above 

> sudo service networking restart
stop: Unknown instance: 
networking stop/waiting
moses@xub-waffles:~/Desktop$ sudo network-manager restart
sudo: network-manager: command not found


---

### Post by steeldriver on 2012-09-01
```

sudo service networking restart 
sudo **service** network-manager restart

```

---

### Post by asnd16 on 2012-09-01
> **steeldriver said:**
> ```

sudo service networking restart 
sudo **service** network-manager restart

```


Coool It fixed the issue thank you sir!

---

### Post by steeldriver on 2012-09-01
What does the nm-tool command report?

```
nm-tool
```

Are you trying to connect wired or wirelessly? If wireless you will need to define a connection with your access point credentials (wired should be able to create a default connection by itself - provided it finds a DHCP server).

---

