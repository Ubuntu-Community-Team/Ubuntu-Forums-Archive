---
title: "help for internet"
date: 2010-05-27
forum: General Help
---

### Post by vaibhav123 on 2010-05-27
I am using ubuntu 8.10 ....

i am unable to configure my internet on it ..i have tried a lot of  things, which i have are as follows...

1. i used these commands but unfortunately no result...
     sudo ifconfig eth0 192.168.1.21
  $ sudo route add default gw 192.168.1.1$ sudo vi /etc/resolv.conf
 this file is edited to enter ipadd etc....

2.Setting the ipaddress in system>admininstrator>network config

there i edited the properties of "Auto eth0" for my ip address, mask, and default gateway....

P.S:
My internet connection is perfectly working fine in windows xp.
Details shown in windows are :

ip address : 192.168.1.21
mask :255.255.255.0
gateway :192.168.1.1
dns :59.179.243.70

---

### Post by viralmeme on 2010-05-27
This might help ..

[http://www.cyberciti.biz/tips/howto-ubuntu-linux-convert-dhcp-network-configuration-to-static-ip-configuration.html](http://www.cyberciti.biz/tips/howto-ubuntu-linux-convert-dhcp-network-configuration-to-static-ip-configuration.html)

---

### Post by inso_741 on 2010-05-27
when you run ```
ifconfig
```does it reflect the ip addr that you entered manually?

---

### Post by vaibhav123 on 2010-05-28
[@ymitchell:]("http://ubuntuforums.org/member.php?u=880593")

I tried the link given by you but in vain...


Upon ifconfig i get :
[FONT=Arial][SIZE=2]Tayal@ubuntu:~$ ifconfig[/SIZE][/FONT][FONT=Arial][SIZE=2]eth0      Link encap:Ethernet  HWaddr 00:1c:c0:21:99:89  [/SIZE][/FONT]
[FONT=Arial][SIZE=2]          inet addr:192.168.1.21  Bcast:192.168.1.255  Mask:255.255.255.0[/SIZE][/FONT]
[FONT=Arial][SIZE=2]          inet6 addr: fe80::21c:c0ff:fe21:9989/64 Scope:Link[/SIZE][/FONT]
[FONT=Arial][SIZE=2]          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1[/SIZE][/FONT]
[FONT=Arial][SIZE=2]          RX packets:13 errors:0 dropped:0 overruns:0 frame:0[/SIZE][/FONT]
[FONT=Arial][SIZE=2]          TX packets:30 errors:0 dropped:0 overruns:0 carrier:0[/SIZE][/FONT]
[FONT=Arial][SIZE=2]          collisions:0 txqueuelen:1000 [/SIZE][/FONT]
[FONT=Arial][SIZE=2]          RX bytes:1496 (1.4 KB)  TX bytes:5430 (5.4 KB)[/SIZE][/FONT]
[FONT=Arial][SIZE=2]          Interrupt:222 Base address:0xc000 [/SIZE][/FONT]
[FONT=Arial][SIZE=2] 
[/SIZE][/FONT]
[FONT=Arial][SIZE=2]lo        Link encap:Local Loopback  [/SIZE][/FONT]
[FONT=Arial][SIZE=2]          inet addr:127.0.0.1  Mask:255.0.0.0[/SIZE][/FONT]
[FONT=Arial][SIZE=2]          inet6 addr: ::1/128 Scope:Host[/SIZE][/FONT]
[FONT=Arial][SIZE=2]          UP LOOPBACK RUNNING  MTU:16436  Metric:1[/SIZE][/FONT]
[FONT=Arial][SIZE=2]          RX packets:286 errors:0 dropped:0 overruns:0 frame:0[/SIZE][/FONT]




[FONT=Arial][SIZE=2]And my details in windows are......[/SIZE][/FONT]
[FONT=Arial][SIZE=2]ip address : 192.168.1.21
mask :255.255.255.0
gateway :192.168.1.1
dns :59.179.243.70[/SIZE][/FONT]


[FONT=Arial][SIZE=2]
[/SIZE][/FONT]

---

### Post by vaibhav123 on 2010-05-28
even the ping 192.168.1.21 is working fine in the terminal with a reply....

---

### Post by inso_741 on 2010-05-28
eht0 seems to be configured properly
can you tell us how exactly do you connect to internet?

---

### Post by vaibhav123 on 2010-05-28
its working now but still having a problem ...

i manually entered te ip address through system>prefrences>network config> auto eth0 >ipv4 settings....

i have to enter them every time i restart or reboot.....

---

### Post by dino99 on 2010-05-28
> **vaibhav123 said:**
> its working now but still having a problem ...

i manually entered te ip address through system>prefrences>network config> auto eth0 >ipv4 settings.... [COLOR="Red"]set on automatic(dhcp)[/COLOR]

i have to enter them every time i restart or reboot.....

how is your /etc/resolv.conf ?

---

