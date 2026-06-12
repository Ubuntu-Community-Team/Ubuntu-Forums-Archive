---
title: "new nic added, how to configure"
date: 2006-03-22
forum: General Help
---

### Post by jeisma on 2006-03-22
hello!

i just added a new nic (now i have two) in my box. how do i go about configuring it? didnt ubuntu auto detected it?


thanks!

---

### Post by jamesr on 2006-03-22
What type of NIC is it?
Post the outputs of
```
sudo ifconfig -a
dmesg | grep eth0 
```

---

### Post by jeisma on 2006-03-22
hello!

its 3c90b-c, its detected alrite. when i go to system-admin-networking, it display eth1. which is the 2nd nic. i was looking for the cli way of configuring the 2nd nic. where is it?

thanks!

---

### Post by Barrakketh on 2006-03-22
[QUOTE=jeisma]hello!

its 3c90b-c, its detected alrite. when i go to system-admin-networking, it display eth1. which is the 2nd nic. i was looking for the cli way of configuring the 2nd nic. where is it?

thanks![/QUOTE]
Take a look in the file /etc/network/interfaces

---

### Post by jeisma on 2006-03-23
wonderful!

thank you. now i got a new problem.

im on a lan. i can no longer access the internet. eth0 address is allowed internet access, eth1 (new one) address is not.

seems like browsing defaults to eth1?

how do i tell the browser to use eth0?

thanks!

---

### Post by Barrakketh on 2006-03-23
[QUOTE=jeisma]wonderful!

thank you. now i got a new problem.

im on a lan. i can no longer access the internet. eth0 address is allowed internet access, eth1 (new one) address is not.

seems like browsing defaults to eth1?

how do i tell the browser to use eth0?

thanks![/QUOTE]
Are you using DHCP for network configuration?  What is the output of "route"?

---

### Post by jeisma on 2006-03-23
hi!

no im not using dhcp.

route gives this:

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.0.0     *               255.255.254.0   U     0      0        0 eth1
192.168.0.0     *               255.255.254.0   U     0      0        0 eth0

currently i have eth0 deactivated, i lose internet connection if i activate it.

what do you think? how can i tell the browser to use eth0, later i will setup eth1 handle dhcp requests.

thanks!

joey

---

### Post by jamesr on 2006-03-23
Could you please post the output of 
```
sudo ifconfig -a
```

I have seen particularly with 3com NICs a clash or it could be that I mainly used to use 3com NICs

---

