---
title: "DHCP Over Riding Interfaces file"
date: 2010-10-11
forum: General Help
---

### Post by 200mg on 2010-10-11
Below is my interfaces file.  Whn I boot I am still getting my addy assigned via dhcp, if I do a /etc/init.d/networking retstart I get the static IP, I am wondering why it doesn't get the static @ boot, I have looked around through the GUI for anything I can toggle, TIA for any replies


```
iface lo inet loopback

auto eth0
iface eth0 inet static
address 10.70.112.254			
netmask  255.255.255.0
gateway 10.70.112.1
```

---

### Post by SlugSlug on 2010-10-11
apt-get remove network-manager fixes it (I do this)

---

