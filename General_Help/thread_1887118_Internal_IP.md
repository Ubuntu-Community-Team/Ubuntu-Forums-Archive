---
title: "Internal IP"
date: 2011-11-26
forum: General Help
---

### Post by TheDegree0 on 2011-11-26
Hello,
Is there some way to get the internal ips? For example get the internal ips of the ip <snip>

Thanks and sorry for my bad grammar. :D

---

### Post by haqking on 2011-11-26
> **TheDegree0 said:**
> Hello,
Is there some way to get the internal ips? For example get the internal ips of the ip <snip>

Thanks and sorry for my bad grammar. :D

Are you asking is there a way to determine the LAN IP range from the network whose Public facing IP is the one you mentioned ?

The likelihood is that the LAN will be using NAT and so something along the lines of 192.168.x.x.

However this or may not be seen as a potential illegal activity, if you dont know how to find this information then you probably shouldnt be, if it is a network you own or someone you know owns then you can ask or already know, if you dont then you probably shouldnt ;-)

Peace

---

### Post by TheDegree0 on 2011-11-26
> **haqking said:**
> Are you asking is there a way to determine the LAN IP range from the network whose Public facing IP is the one you mentioned ?

The likelihood is that the LAN will be using NAT and so something along the lines of 192.168.x.x.

However this or may not be seen as a potential illegal activity, if you dont know how to find this information then you probably shouldnt be, if it is a network you own or someone you know owns then you can ask or already know, if you dont then you probably shouldnt ;-)

Peace

Oh okay, I was trying to connect to my other computer with ssh and then when Im in I wanted to connect to my other computer but I dont know the interal ip because isnt static.

Thanks for your help.

---

### Post by haqking on 2011-11-26
> **TheDegree0 said:**
> Oh okay, I was trying to connect to my other computer with ssh and then when Im in I wanted to connect to my other computer but I dont know the interal ip because isnt static.

Thanks for your help.

well if the IP you mentioned is your public IP (which by the way is not a good idea to post) ;-) A malicious person could now be armed with your Pubic IP and knowing you run SSH (half the work is done )

Then you need to make sure that device hosting that IP (likely to be a router) forwards your SSH traffic to your machine running the SSH server.

If it is dynamic, then i would suggest making sure that IP is static or use Dynamic DNS.

Either way port forwarding needs to handle the incoming SSH requests to be forwarded to the SSH hosting machine

---

### Post by TheDegree0 on 2011-11-26
> **haqking said:**
> well if the IP you mentioned is your public IP (which by the way is not a good idea to post) ;-) A malicious person could now be armed with your Pubic IP and knowing you run SSH (half the work is done )

Then you need to make sure that device hosting that IP (likely to be a router) forwards your SSH traffic to your machine running the SSH server.

If it is dynamic, then i would suggest making sure that IP is static or use Dynamic DNS.

Either way port forwarding needs to handle the incoming SSH requests to be forwarded to the SSH hosting machine

Ohh, Thank you. Is not my IP I just put a random one. :D

Thanks for your help.

---

### Post by sffvba[e0rt on 2011-11-26
IP address in OP removed or security purposes (just in case)...


404

---

### Post by Iowan on 2011-11-26
> **TheDegree0 said:**
> Oh okay, I was trying to connect to my other computer with ssh and then when Im in I wanted to connect to my other computer but I dont know the interal ip because isnt static.

Thanks for your help.As mentioned, a static IP or reserved/static lease (DHCP server always assigns the same IP - based on MAC address) will make port forwarding easier.

---

