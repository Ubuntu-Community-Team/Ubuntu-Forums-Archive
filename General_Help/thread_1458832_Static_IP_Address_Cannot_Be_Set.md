---
title: "Static IP Address Cannot Be Set?"
date: 2010-04-20
forum: General Help
---

### Post by ajwei810192 on 2010-04-20
Hi, 

  I have been fiddling around with my ip address  configuration using several sources, and this is what I have in the  /etc/network/interfaces file:

auto lo
iface lo inet loopback
auto  eth0
iface eth0 inet static
address 192.168.1.122 
broadcast  255.255.255.255  
netmask 255.255.255.0
network 192.168.1.0
gateway  192.168.1.254

Yet, this is what I have in the ifconfig after I  restarted the computer:

alice@alice-laptop:~$ ifconfig
eth0       Link encap:Ethernet  HWaddr 08:00:27:77:07:0b  
          inet  addr:192.168.1.66  Bcast:192.168.1.255  Mask:255.255.255.0
           inet6 addr: fe80::a00:27ff:fe77:70b/64 Scope:Link
          UP  BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX  packets:710 errors:0 dropped:0 overruns:0 frame:0
          TX  packets:741 errors:0 dropped:0 overruns:0 carrier:0
           collisions:0 txqueuelen:1000 
          RX bytes:333701 (333.7 KB)   TX bytes:192871 (192.8 KB)
          Interrupt:10 Base address:0xd020  

lo        Link encap:Local Loopback  
          inet  addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128  Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
           RX packets:8 errors:0 dropped:0 overruns:0 frame:0
          TX  packets:8 errors:0 dropped:0 overruns:0 carrier:0
           collisions:0 txqueuelen:0 
          RX bytes:480 (480.0 B)  TX  bytes:480 (480.0 B)

Could there be any mistakes I have made in  the file? Why is it that I seem to have set a static ip address here and  is not working?
Thanks for your help.

Alice

---

### Post by oldfred on 2010-04-20
I am no expert on settings since I used the gui version. I also do not recommend posting HWaddr.

eth0      Link encap:Ethernet  HWaddr xxxxxx
          inet addr:192.168.1.20  Bcast:192.168.1.255  Mask:255.255.255.0

My router uses 100-150 as DHCP and you cannot use the DHCP range already used by the router.

---

### Post by lisati on 2010-04-20
My preference is to use the options available in my router, to issue a static IP based on MAC address. That way, if I take my laptop somewhere else, I am less likely to run into conflicts with static IPs set up by other people using whatever network I connect to.

---

### Post by ajwei810192 on 2010-04-20
Hi, 

Thanks to the response from lisati and oldfred. 
 oldfred, thanks for pointing that out. I should not have done that. 

  lisati, I kind of like this version. Is this possible? And, is there a simple 123 step that you could lead me through on that so I could follow? 

Thanks.

---

### Post by Iowan on 2010-04-20
> **ajwei810192 said:**
> 
auto lo
iface lo inet loopback
auto  eth0
iface eth0 inet static
address 192.168.1.122 
broadcast  [COLOR="Red"]255.255.255.255 [/COLOR] 
netmask 255.255.255.0
network 192.168.1.0
gateway  192.168.1.254
Broadcast address doesn't look kosher - but it and the network address are optional.  Depending on what version you're running, Network Manager may be overriding the */etc/network/interfaces* file. In previous versions, NM wouldn't touch interfaces defined there - now???

---

### Post by ajwei810192 on 2010-04-21
> **Iowan said:**
> Broadcast address doesn't look kosher - but it and the network address are optional. Depending on what version you're running, Network Manager may be overriding the */etc/network/interfaces* file. In previous versions, NM wouldn't touch interfaces defined there - now???
 
Where is the NM you are talking about? I am not sure how to check that. And, the broadcast address? I copied that straight from ifconfig, and I use Ubuntu 9.10. 
 
BTW, I run my Ubuntu as a virtual box on my Windows machine, if that has anything to do with it, I also found that the ip address is not the same on my windows under the Virtualbox listing compared with what I get from running ifconfig on my ubuntu virtual box.

---

### Post by ajwei810192 on 2010-04-21
> **oldfred said:**
> I am no expert on settings since I used the gui version. I also do not recommend posting HWaddr.
 
eth0 Link encap:Ethernet HWaddr xxxxxx
inet addr:192.168.1.20 Bcast:192.168.1.255 Mask:255.255.255.0
 
My router uses 100-150 as DHCP and you cannot use the DHCP range already used by the router.
 
Seriously? Then, what can I use? I cannot possibly invent a new ip address out of nowhere, if you know what I mean.

---

### Post by oldfred on 2010-04-21
You can use any number not already used including the DHCP range that in effect is already used. That is why if you look at my setttings I posted I used 20. 

Some like to reserve the first numbers for servers and the high numbers for other devices like printers, so all the users are in the middle. When we started using DHCP it made it a lot easier to not have to keep track of each user just fixed devices.

---

### Post by ajwei810192 on 2010-04-21
> **oldfred said:**
> You can use any number not already used including the DHCP range that in effect is already used. That is why if you look at my setttings I posted I used 20. 
 
Some like to reserve the first numbers for servers and the high numbers for other devices like printers, so all the users are in the middle. When we started using DHCP it made it a lot easier to not have to keep track of each user just fixed devices.
 
You mean to follow a tutorial as [http://www.ubuntugeek.com/how-to-set-a-static-ip-address-in-ubuntu-810-intrepid-ibex.html](http://www.ubuntugeek.com/how-to-set-a-static-ip-address-in-ubuntu-810-intrepid-ibex.html)? 
 
As I am writing this, I have un-installed the Networking Manager, followed some of the steps mentioned in the link above, and made the necessary changes as most of you have mentioned in my interface file. I have now got a working static IP address! Thanks for your help!

---

