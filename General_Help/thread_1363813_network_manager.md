---
title: "network manager"
date: 2009-12-24
forum: General Help
---

### Post by jrhartley on 2009-12-24
newbie here...needing help...while trying to set a static ip instead of dhcp i accidentally deleted network manager. dont ask me how but i did...i need to get it back...now the machine doesnt have a connection to the network. can it be loaded from install disk? needing step by step help...thanx in advance.  merry christmas

---

### Post by spiderbatdad on 2009-12-24
Could you be a little more specific about what you did? Did you only loose the applet from the  panel? I don't think you can delete network-manager without wiping out a lot of other packages, could be wrong. You should set static address in /etc/network/interfaces like this:
```
iface eth0 inet static
address 192.168.1.99
netmask 255.255.255.0
network 192.168.1.0
broadcast 192.168.1.255
gateway 192.168.1.1
``` Just an example. Usually use some value for the ip outside the dhcp range.

---

### Post by jrhartley on 2009-12-24
Thanx that worked like a champ...ill explain what i did another time...i gotta run ...thanx again

---

