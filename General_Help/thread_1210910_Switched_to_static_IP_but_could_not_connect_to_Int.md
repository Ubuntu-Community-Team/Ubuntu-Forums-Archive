---
title: "Switched to static IP but could not connect to Internet"
date: 2009-07-12
forum: General Help
---

### Post by hasatmax on 2009-07-12
Hello ,
i am facing a situation here, my project on Ubuntu 9.04 running on a VMWare requires me to have a static IP rather than a dynamic one, I tried to change it by going to 
System -->Administration --> Networking and over there I changed the Wired Network to "Static IP" and provided the IP and saved and closed. Since then i am not able to connect to internet, when i switch back to DHCP mode it then works.! but I need to have a static IP, can someone help me out with this..?? I am totally new to Ubuntu and worked previous steps looking up online. I guess we can do it by the terminal too, but

sudo vi/etc/network interfaces gives me a blank Terminal..!! so i had to switch to the GUI way of changing it.

Any suggestions or steps would be really helpful. 

Thanks,
hasatmax.

---

### Post by jonobr on 2009-07-12
Hello


If your not used to using vi, you need to be careful as it takes a bit of getting used to 
gedit may be of more use.

Anyway, when you setup your static address, you should open a terminal and type

ifconfig


post the results here.

Also, if you could post the results of 
cat /etc/resolv.conf

lastly,

if you set the ip address of the 192.168.1.4 (eg)

then try 
ping 127.0.0.1
ping 192.168.1.4

then 192.168.1.1 (assuming this is your default router

then 

ping 74.125.45.100

let us know which fail

---

### Post by Hobgoblin on 2009-07-12
> **hasatmax said:**
>  
System -->Administration --> Networking and over there I changed the Wired Network to "Static IP" and provided the IP and saved and closed. 

Did you provide the netmask and gateway IP as well?

With no gateway IP you will have no internet access.

---

### Post by hasatmax on 2009-07-12
thnx so much for ur response,
 1. on typing ifconfig I get

eth0   Link encap:Ethernet HWaddr:00:0c:29:79:5e:7f
         inet addr:141.215.___.___ Bcast:141.215.255.255 Mask:255.255.0.0
         inet6 addr:fe80::20c:29ff:fe79:5e7f/64 Scope:Link
         UP BROADCAST RUNNING MULTICAST MTU:1500 METRIC:1
         RX packets:251 errors:1 dopped:1 overruns:0 frame:0
         TX packets:77 errors:0 dropped:0 overruns:0 carrier:0
         collisions:0 txqueuelen:1000
         RX bytes:21529(21.5 KB) TX bytes:7581(7.5 KB)
         Interrupt:18 Base address:0x2000

lo      Link encap:Local Loopback
         inet addr:127.0.0.1 Mask:255.0.00
         inet6 addr:  ::1/128 Scope:Host
         UP LOOPBACK RUNNING MTU:16436 Metric:1
         RX packets:22 errors:0 dropped:0 overruns:0 carrier:0
         TX packets:22 errors:0 dropped:0 overruns:0 carrier:0
         collisions:0 txqueuelen:0
         RX bytes:1724(1.7 KB) TX bytes:1724(1.7 KB)


2.     ping 127.0.0.1 gives an infinite terminal something like this.!

        64 Bytes from 127.0.0.1:icmp_seq=1 t+1=64 time=0.029
        .......
         .......


3.      and finally ping 192.168.1.4
                         ping 192.168.1.1
                         ping 74.125.45.100

      gave me "Network Unreachable" !


   Please let me know what I gotta do and where m going wrong, thnx again for ur early response.


hasatmax.

---

### Post by hasatmax on 2009-07-12
> **Hobgoblin said:**
> Did you provide the netmask and gateway IP as well?

With no gateway IP you will have no internet access.

@Hobgoblin: Oh..I didn't do it, but I remember when I typed Static IP it automatically generated gateway IP but I havent done it specifically, or may be it was netmask which was generated automatically, I just dont remember as of now, I apologize as I have very less knowledge about this stuff, I am a student and learning Ubuntu and Linux in general.!

Thanx for ur response.

---

### Post by DeMus on 2009-07-12
> **hasatmax said:**
> Hello ,
i am facing a situation here, my project on Ubuntu 9.04 running on a VMWare requires me to have a static IP rather than a dynamic one, I tried to change it by going to 
System -->Administration --> Networking and over there I changed the Wired Network to "Static IP" and provided the IP and saved and closed. Since then i am not able to connect to internet, when i switch back to DHCP mode it then works.! but I need to have a static IP, can someone help me out with this..?? I am totally new to Ubuntu and worked previous steps looking up online. I guess we can do it by the terminal too, but

sudo vi/etc/network interfaces gives me a blank Terminal..!! so i had to switch to the GUI way of changing it.

Any suggestions or steps would be really helpful. 

Thanks,
hasatmax.

You obviously have a router to which you conenct to, This router gives out IP addresses in DHCP mode. When you switch to static addresses you need to make sure which addresses you can use.
My router says the first 50 addresses are used for DHCP and starting from 51 (as last numbers of the address 192.168.0.xx) are used for static.
So read the manual to know which addresses you can and may use. Maybe that helps.

---

### Post by Hobgoblin on 2009-07-12
> **hasatmax said:**
> 
eth0   Link encap:Ethernet HWaddr:00:0c:29:79:5e:7f
         inet addr:141.215.___.___ Bcast:141.215.255.255 Mask:255.255.0.0

....

3.      and finally ping 192.168.1.4
                         ping 192.168.1.1
                         ping 74.125.45.100


Have you set the IP to 141.215.x.x and 192.168.1.1 is your router?  If so then that will be why it isn't working.

You need an IP address in the same subnet as the router.  Why are you using a 141.215.x.x IP?  That isn't a [private network IP](http://en.wikipedia.org/wiki/Private_network).

---

### Post by jonobr on 2009-07-12
Hello


As the other posters implied, it we would need to know more about your network.

The suggestions I gave give a typical example of a home network where 192.168 address are handed out by your router.

In this case you are mentioning a class B 141 address range.

I think the best this to see is , when you setup dynamic and it works, 
what kind of IP address do you get?
Are you assigned a ip that is in that 141 addressing range?

your getting 192.168 addresse4s unreachable due to the differences in IP between the devices.

If you ping your default gateway and see if it responds, that would test your Ip stack on your router

---

