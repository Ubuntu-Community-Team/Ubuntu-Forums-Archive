---
title: "Change DNS System-wide"
date: 2010-08-15
forum: General Help
---

### Post by zzzBrett on 2010-08-15
Is it possible to change the DNS servers for all of my connections on the computer? I can change an individual's DNS in network-manager, but it seems to update /etc/resolv.conf.

---

### Post by mike555 on 2010-08-15
you should be able to change dns numbers in your router .that way all computers on your network will use them.

---

### Post by zzzBrett on 2010-08-15
I connect to a few different networks. Wireless / LAN. I would like to change one setting to be the universal DNS for the system.

---

### Post by mike555 on 2010-08-15
I'm not sure what you mean by "all you connections" , but setting ubuntu to use dns numbers is easy ;
   click on your network connections ,then the edit connections , highlight the connection , then edit , in the IPv4 settings tab set it to get dhcp -addresses only , then type in the dns numbers you want to use (putting a comma in between them)save .......
   you might want to do the same for ethernet and wireless .(you will probably need to shut down for a few minutes before this takes effect)

[IMG]http://i37.tinypic.com/28amj2o.jpg[/IMG]

---

