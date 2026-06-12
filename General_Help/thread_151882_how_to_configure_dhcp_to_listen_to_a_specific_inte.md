---
title: "how to configure dhcp to listen to a specific interface"
date: 2006-03-28
forum: General Help
---

### Post by jeisma on 2006-03-28
hello!

on my ubuntu 5.10 box, i got two nics. how do you configure dhcp to 
listen to requests in eth1 (for example)?


thanks!

---

### Post by twigboy on 2006-03-29
I dont think dhcp works like.  I believe the nic sends out a broadcast to the dhcp server and the server gives the nic a free ip.  I think you would have to turn on/off that broadcast option on nic itself.

---

### Post by chocolatetoothpaste on 2006-03-29
[QUOTE=jeisma]hello!

on my ubuntu 5.10 box, i got two nics. how do you configure dhcp to 
listen to requests in eth1 (for example)?


thanks![/QUOTE]
Set your nic to obtain IP address automagically via DHCP. System->Configuration->Networking.

---

### Post by jeisma on 2006-03-29
hello!

i mean the server, if it has two nics, how would you configure it to listens for reques in eth1 for example.

thanks!

---

### Post by elamericano on 2006-03-29
That was it wasn't it?

Open System->Administration->Networking

Select each interface and click Properties.

Set one for DHCP and the other to a static address.

-EA

---

### Post by dcstar on 2006-03-30
[QUOTE=jeisma]hello!

i mean the server, if it has two nics, how would you configure it to listens for reques in eth1 for example.

thanks![/QUOTE]
Have a read of the multiple NIC section on this:

[http://www.siliconvalleyccie.com/linux-hn/dchp.htm](http://www.siliconvalleyccie.com/linux-hn/dchp.htm)

---

### Post by jeisma on 2006-03-30
[QUOTE=dcstar]Have a read of the multiple NIC section on this:

[http://www.siliconvalleyccie.com/linux-hn/dchp.htm](http://www.siliconvalleyccie.com/linux-hn/dchp.htm)[/QUOTE]

great!

thanks!

---

