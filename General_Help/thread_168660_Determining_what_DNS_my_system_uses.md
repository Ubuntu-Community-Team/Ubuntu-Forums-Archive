---
title: "Determining what DNS my system uses?"
date: 2006-04-30
forum: General Help
---

### Post by Elif Tymes on 2006-04-30
I want to switch the DNS I use for my ETH0 interface, but I can't figure out how. Any suggestions?(This is for a CLI Server, btw. So GuI won't help :))

I've checked /etc/networking/interfaces, but can't figure out how to change it from there(THe IP is static)

Any help would be appreciated.

---

### Post by cskeide on 2006-04-30
The nameservers are listed in resolv.conf
```
cat /etc/resolv.conf
```

Edit that file with whatever nameservers you want to use.
```
sudo echo "nameserver xxx.xxx.xxx.xxx" >> /etc/resolv.conf
```

EDIT: Sorry, the sudo echo thing didn't work, but you get the picture...
```
sudo vim /etc/resolv.conf
```

---

### Post by Elif Tymes on 2006-05-01
Thanks for the help, but that file is "overwritten" by a different file, I'm getting to the bottom of it as we speak thouh

---

