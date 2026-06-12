---
title: "Wireless Static Ip (shell)"
date: 2006-03-31
forum: General Help
---

### Post by playmobiel on 2006-03-31
How to give my wireless connection a static ip , in the shell for my home server? 
I've read something about /etc/network/interfaces but i don't know how to set it up,

Thanks,

---

### Post by Ramses de Norre on 2006-03-31
sudo gedit /etc/network/interfaces 
make it look something like this: ```
mapping hotplug
        script grep

# The primary network interface
iface ath0 inet static
wireless-essid RAFAEL
wireless-key 3D4B####EE
address 192.168.123.###
netmask 255.255.248.0
gateway 192.168.123.###

auto ath0

```
Where ath0 is the name of my wireless adapter. (Don't mind the #'s)

---

### Post by playmobiel on 2006-03-31
Thanks mate 

problem solved :)

---

