---
title: "Internet sharing on unbutu !"
date: 2011-12-17
forum: General Help
---

### Post by melc_sokat on 2011-12-17
Hello here.

I got a problem with my ubuntu.

Problem is like this.

I got this ubuntu server running 10.04 and i set up my windows machine to get internet from linux.
Problem is after i reboot that linux each time i need to get eth0 up and run this command : 


 sudo ip addr add 192.168.0.1/24 dev eth0

After that all things are fine.
My problem is: what is need to be done to not run those 2 commands.
Any help is apreciated.

---

### Post by lechien73 on 2011-12-17
Hi, take a look at the guide here: [https://help.ubuntu.com/10.04/serverguide/C/network-configuration.html](https://help.ubuntu.com/10.04/serverguide/C/network-configuration.html)

Look under the section about Static Addressing to see how to make the card come up with an address on boot.

---

