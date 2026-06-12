---
title: "Ubuntu with ClearOS in virtualbox as gateway?"
date: 2012-06-29
forum: General Help
---

### Post by ericus on 2012-06-29
Hi all! 
I would like to run ClearOS in a VirtualBox on top of Ubuntu, and have ClearOS act as a firewall/gateway. This would be the setup:
Internet > Ubuntu with ClearOS > switch > other machines. 

On the host I have two NIC's, internet on eth1 and eth2 will be LAN. 
Is it possible to route all traffic trough ClearOS, including to the host? 

I installed ClearOS on a VirtualBox yesterday, and it runs fine. Havent figured out how to configure the NICs in vbox though, or how to connect to ClearOS instead of directly to the internet. 

How would I set this up?

---

### Post by ericus on 2012-06-29
Okay, I've got it working now, but there's another issue right now.

This is some prints of the setup:
Virtualbox - configuration for the WAN network card:
[https://dl.dropbox.com/u/4375930/vm1.png](https://dl.dropbox.com/u/4375930/vm1.png)

Virtualbox - configuration for the LAN network card:
[https://dl.dropbox.com/u/4375930/vm2.png](https://dl.dropbox.com/u/4375930/vm2.png)

Network Manager - LAN
[https://dl.dropbox.com/u/4375930/nw1.png](https://dl.dropbox.com/u/4375930/nw1.png)

Network Manager - Internet
[https://dl.dropbox.com/u/4375930/nw2.png](https://dl.dropbox.com/u/4375930/nw2.png)

The thing is, if I go to [www.whatismyip.com](www.whatismyip.com) from the host or from the virtual machine or from any other machine in the network, I see another IP then what's displayed in Network Manager (three last digits is different).
So basically I have two external IP's (out of three, which is how many I can get from my ISP). Why is that, and how can I fix that?

Otherwise the LAN is working great and assigning all computers an 192.168.111.x-IP adress.

---

### Post by ericus on 2012-06-29
Update: The host OS is NOT going via the ClearOS firewall. I've tried to SSH to the other IP and that works, and it should not. Help me?

ifconfig -a:
```
eth1      Link encap:Ethernet  HWaddr xx:xx:xx:xx:xx:xx  
          inet addr:85.226.xx.xxx  Bcast:85.226.55.255  Mask:255.255.252.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2188611 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1114566 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2761924230 (2.7 GB)  TX bytes:289632614 (289.6 MB)
          Interrupt:50 Base address:0x4000 

eth2      Link encap:Ethernet  HWaddr xx:xx:xx:xx:xx:xx  
          inet addr:192.168.111.2  Bcast:192.168.111.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:160582 errors:0 dropped:0 overruns:0 frame:0
          TX packets:153753 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:151924136 (151.9 MB)  TX bytes:168092365 (168.0 MB)
          Interrupt:21 Base address:0x4c00 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1776 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1776 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:168536 (168.5 KB)  TX bytes:168536 (168.5 KB)
```
eth1 should be 85.226.xx.yyy instead, but it's not!

---

### Post by ericus on 2012-06-30
Sorry for bumping, but what am I missing here?

---

