---
title: "network bridge"
date: 2010-03-27
forum: General Help
---

### Post by krishna1650 on 2010-03-27
Hello all, i am using vnuml to test a network project. I have one Ethernet card on my ubuntu 9.10( eth0) with network 10.1.0.0/16, and creating a tap0 with subnet 10.4.0.0/16. Now the problem is how to work them together, such that packets from one interface goes to other one? 
Can anyone show some way?
Thanks a lot.

---

### Post by dcstar on 2010-03-27
> **krishna1650 said:**
> Hello all, i am using vnuml to test a network project. I have one Ethernet card on my ubuntu 9.10( eth0) with network 10.1.0.0/16, and creating a tap0 with subnet 10.4.0.0/16. Now the problem is how to work them together, such that packets from one interface goes to other one? 
Can anyone show some way?
Thanks a lot.

[http://www.troubleshooters.com/linux/ip_fwd.htm](http://www.troubleshooters.com/linux/ip_fwd.htm)

---

### Post by krishna1650 on 2010-03-28
> **dcstar said:**
> [http://www.troubleshooters.com/linux/ip_fwd.htm](http://www.troubleshooters.com/linux/ip_fwd.htm)

Thanks for the reply. But in this tutorial linux machine has two interfaces eth0 and eth1, whereas in case of mine i have one physical interface eth0 connected to lan (10.1.*.*) and one virtual interface tap0 (10.4.*.*). My problem is how to send packets from one interface to other?

Thanks for the reply.

---

