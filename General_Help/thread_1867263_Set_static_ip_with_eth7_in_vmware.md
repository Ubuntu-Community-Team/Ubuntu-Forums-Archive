---
title: "Set static ip with eth7 in vmware"
date: 2011-10-22
forum: General Help
---

### Post by arulnambi on 2011-10-22
Hi 
I have a problem setting up static ip for my ubuntu vm.
Procedure I followed.
Edited /etc/network/interfaces to look like

auto eth7
iface eth0 inet static
address 192.168.128.3
netmask 255.255.255.0
gateway 192.168.0.2

The message I get when I enter ifconfig is
someuser@ubuntu:~$ ifconfig
eth7      Link encap:Ethernet  HWaddr 00:0c:29:8f:32:9f  
          inet6 addr: fe80::20c:29ff:fe8f:329f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:86 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:8312 (8.3 KB)  TX bytes:468 (468.0 B)
          Interrupt:19 Base address:0x2024 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:182 errors:0 dropped:0 overruns:0 frame:0
          TX packets:182 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:31501 (31.5 KB)  TX bytes:31501 (31.5 KB)

When I try to restart my network setting using  
sudo /etc/init.d/networking restart , 
I get an message
* Reconfiguring network interfaces...                                                                                                                                  Ignoring unknown interface eth7=eth7.

I also tried editing  /etc/udev/rules.d/70-persitent-net.rules and switching eth0 with eth7, now I don’t get the error message  but I am unable to connect to the network after doing this change.
Note. I tried the same thing in another vm which has an eth0 and I did not receive any ignore message and the ip address changed without any problems.
Thanks a lot for taking your time to look at it.
Any help is appreciated.
With regards
Arul

---

