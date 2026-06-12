---
title: "static connection problem"
date: 2009-10-17
forum: General Help
---

### Post by shahan on 2009-10-17
I am trying to connect my broadband connection but failed for many time...
this is a static connection
I use 

In terminal:
sudo gedit /etc/network/interfaces

auto eth0
iface eth0 inet static
       hwaddress ether  00:08:56:00:08:69
address 111.222.333.444
gateway 555.666.777.888
netmask 255.255.255.0

Then /etc/reslov.conf

nameserver 123.44.49.129
nameserver 123.44.49.130
nameserver 123.44.49.131
nameserver 123.44.49.132

Then
sudo /etc/init.d/networking restart

but its not connect. I don't know why.
Now it is 9.04
I tried this procedure in 8.04.2, 8.04.3, 8.10 and finally in 9.04
Waitting for experts opinions

---

