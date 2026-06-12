---
title: "Help with ubuntu as router"
date: 2012-01-09
forum: General Help
---

### Post by Warwigan on 2012-01-09
Hi I am new to the forum.

I have a problem with setting up ubuntu as a router. I have followed this guide [https://help.ubuntu.com/community/Router]("https://help.ubuntu.com/community/Router") 

So I have completed all the steps in the guide (including the DHCP setup) So the last thing I did was to restart the network interface. (sudo /etc/init.d/networking restart) When I use this command I get the error message "RTNETLINK answers no such prosess" on one of the network cards. The other works just fine. When try to connect to my machine I get no ip-adress. I think there might be something wrong with the nat.sh script, but I just copied and pasted the code so I don't know for sure.

Appreciate any help

---

### Post by Pilot6 on 2012-01-09
I see no reason to use Ubuntu as a router. You can install special linux for that. Openwrt, for instance.

---

### Post by Doug S on 2012-01-09
Hi warwigan, and welcome to ubuntu forums.
 
My main ubuntu server box runs as a router (as well as many other things, internal DNS, DHCP server, web server, samba file server, email ...)
I don't have an answer for you, but rather a request for more information. What are the sub-nets of each of your NIC cards and do they conflict?
Could you post your /etc/network/interfaces file.

---

