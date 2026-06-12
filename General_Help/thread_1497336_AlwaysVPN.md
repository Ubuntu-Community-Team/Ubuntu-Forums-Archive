---
title: "AlwaysVPN"
date: 2010-05-30
forum: General Help
---

### Post by kybush on 2010-05-30
hi 

Im useing AlwaysVPN and i dont have any problems connecting,but i would like to know how to disconnect from the service

---

### Post by sdennie on 2010-05-30
If you click on the network manager and go down to VPN Connections, the sub-menu has a "Disconnect VPN..." option.  (I missed it the first time too).

---

### Post by kybush on 2010-05-30
nope thats not working ........... maybe because i connect to the service through terminal

---

### Post by sdennie on 2010-05-30
What method do you use to connect to the service?  If you are doing something like "sudo pon service_name", to turn the VPN off would be "sudo poff service_name".  If you are using some other method to connect, you'd have to post what you are using.

---

### Post by kybush on 2010-05-30
i use sudo openvpn --config /etc/openvpn/AlwaysVPN-Compatible.conf

---

