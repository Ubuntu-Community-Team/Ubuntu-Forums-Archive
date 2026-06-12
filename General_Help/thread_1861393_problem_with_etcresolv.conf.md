---
title: "problem with /etc/resolv.conf"
date: 2011-10-15
forum: General Help
---

### Post by crakeador on 2011-10-15
Hi, i have problems with my internet configuration. I installed linux in a VMWare with 2 networks card eth0 and eth1. Mi network is 192.168.109.0 and i want to put a static ip to eth0 and disable eth1. 
 
My first action was disable eth0 and eth1. I wrote in terminal **ifconfig eth0 down** and **ifconfig eth1 down. **My next action was to write in **/etc/network/interfaces** the following:
 
#the loopback network interface
auto lo
iface lo inet loopback
 
#The primary network interface
allow-hotplug eth0
 
#NetworkManager
iface eth0 inet static
address 192.168.109.10
netmask 255.255.255.0
network 192.168.109.0
broadcast 192.168.109.255
gateway 192.168.109.2
 
#auto eth1
#iface eth1 inet dhcp
 
My next action was to execute the command **/etc/init.d/networking restart**
 
I followed in **/etc/resolv.conf **writting **nameserver 192.168.109.2 **and i execute **ifconfig eth0 up**
 
I made **pings** to 192.168.109.10 and 192.168.109.2 , where i havent problems. My problem is when i execute **ping **[**www.google.com**]("http://www.google.com")where terminal tell me **unknow host**.
 
when i reboot my machine eth0 has this configuration but eth1 is enabled ¿what is it posible? following with my problem, the file /etc/resolv.conf is cleaned because i write ifconfig eth1 down ¿where is my configuration? ¿why have i not access to internet? 
 
¿any can help me?

---

### Post by gsmanners on 2011-10-15
You do understand that resolv.conf is for DNS, right?

Try this:

```
nameserver 208.67.222.222
nameserver 208.67.220.220
```

(The above is for if you want to use [opendns]("http://www.opendns.com/"), by the way.)

---

### Post by crakeador on 2011-10-16
> **gsmanners said:**
> You do understand that resolv.conf is for DNS, right?
 
Try this:
 
```
nameserver 208.67.222.222
nameserver 208.67.220.220
```
 
(The above is for if you want to use [opendns]("http://www.opendns.com/"), by the way.)
 
Yes but my system run under VMWare so DNS has this ip 192.168.109.2 (the same ip as my gw). I can resolv if eth1 is up. But i want eth1 disable and i cant disabe it

---

### Post by gsmanners on 2011-10-16
Ah, I see. So the problem is that network manager interferes?

I think what happens is that network manager kicks in and finds eth1 and then does a dhcp to try to configure it, so you either need to remove network-manager or you need to remove the dhcp-probe (I would suggest removing network-manager).

---

