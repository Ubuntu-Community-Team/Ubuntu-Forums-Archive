---
title: "Poofing NIC on restart lol..."
date: 2009-08-30
forum: General Help
---

### Post by jon64 on 2009-08-30
Ohkay the title doesn't say much but its kind of funny lol. Anyways so the internet was fine until i decided to restart my computer, thats when i discovered that i no longer have a eth0 anymore. All i have is an eth1 and loopback. One thing i do recall doing to the nic settings was changing my eth0 from dhcp to static so that has to be the reason why it dissappeared.
 
**/etc/network/interfaces**
```
iface eth0 inet static
address 192.168.x.x
netmask 255.255.x.x
network 192.168.x.x
broadcast 192.168.x.x
gateway 192.168.x.x
```
 
I just checked daemon.log and it says eth0 is now unmanaged.

---

### Post by Iowan on 2009-08-30
That'd do it - Network Manager ignores interfaces defined in */etc/network/interfaces*. Is eth1 wireless (like it is on my laptop)? There is a thread (or two) around that mention changing managed=false setting to managed=true... I haven't tried it. It is possible to set up a static address via Network Manager.

---

### Post by jon64 on 2009-08-30
> **Iowan said:**
> That'd do it - Network Manager ignores interfaces defined in */etc/network/interfaces*. Is eth1 wireless (like it is on my laptop)? There is a thread (or two) around that mention changing managed=false setting to managed=true... I haven't tried it. It is possible to set up a static address via Network Manager.
 
No eth1 is a wired NIC.

---

### Post by bear24rw on 2009-08-30
add:

auto eth0

right above iface

---

### Post by jon64 on 2009-08-30
Ok this is what i did to retrieve my eth0 back i ran ```
*sudo dhclient eth0*
``` and now i can see my eth0 again through ifconfig and its still in static so thats good but network manager still is saying eth0 is unmanaged and when i try to add it via network manager gui the entry won't show in the wired tab as network manager is denying the entry i did. I guess it isnt a big deal that network manager can't manage it cause my internet still works and its in static but if there is a fix for this i would like to hear it :)

---

