---
title: "problem in bridge vbox"
date: 2010-12-08
forum: General Help
---

### Post by nodehi on 2010-12-08
hello 
sorry
I know english alittle
may os is 7 and i install virtual box and install ubuntu server into
i want bridg ubuntu srever and win7 
i use this commands
cd /etc/network
add
sudo nano interfaces
there are this cintent into interfaces file :

#...
#...

# the loopback network interfaces
auto lo
iface lo inet loopback

# the primary network interfaces
auto lo
iface eth0 inet static 
address (my ip)
netmask 255.255.255.0

when i go to ifconfig dont where ip
what i do?

---

