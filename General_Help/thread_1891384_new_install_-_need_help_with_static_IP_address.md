---
title: "new install - need help with static IP address"
date: 2011-12-05
forum: General Help
---

### Post by spindler on 2011-12-05
Hello,

I just did a fresh install of Ubuntu 11.10.   I need to set up the computer with a static IP address so I can use it as a webserver. 

Just after I finished the install process. I checked to see that I have internet connection.

I am using the following documentation to help me. [https://help.ubuntu.com/11.10/serverguide/C/network-configuration.html](https://help.ubuntu.com/11.10/serverguide/C/network-configuration.html)

Then I edited the file interfaces  located at  /etc/network/interfaces.  This is what the file has now.


----------------------------------------------------------------------
#This file describes the network interfaces available on your system
#and how to activate them.  For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet lookback

# The primary network interface
auto eth0
iface etho inet static
address 168.168.1.100
netmask 255.255.255.0
network 168.168.1.0
broadcast 168.168.1.100
gateway 168.168.1.1

--------------------------------------------------------------------

NOW.... After I finish updating and saving the interface file, I restarted the computer to let the changes take affect.   I DID NOT TYPE ANY OTHER COMMANDS IN THE TERMINAL WINDOW TO RESET THE NETWORK.   The documentation did not state I needed to do this.

So... after I reboot  I type the command  ifconfig to confirm the IP address has changed for eth0, which it has.

Here is what ifconfig produces

eth0     Link encap:Ethernet  HWaddr 00:11:c5:4e:ee:d8
           inet addr:168.168.1.100  Bcast: 168.168.1.100  Mask: 255.255.255.0
           inet6 addr: fe80::215:c4ff:fe34:eed8/64 Scope: link
           UP BROADCAST RUNNING MULTICAST MTU:1500  Metric:1
           RX packets:228 errors:0 dropped:0 overruns:0 frame:0
           TX packets:60 errors:0 dropped:0 overruns:0 carrier:0
           collisions:0 txqueuelen:1000
           RX bytes:31107 (31,1. KB) TX Bytes:8890 (8.8 KB)
           Interrupts:16



**HOWEVER, I do not have internet connection now.  Why is this?   What do I need to do to fix this issue?**

Thanks

Spindler

---

### Post by roger_1960 on 2011-12-05
Hi

I think what you have done is set up a fixed IP address within the network controlled by your router.  You need your router to have a fixed external (ie visible to the www) IP address.  Your ISP has to offer/provide this to you.

---

### Post by lisati on 2011-12-05
IMO it is useful (but not always necessary) to have a fixed IP address for BOTH the public connection and on the internal network. There are also multiple methods of arranging for fixed addresses on the internal network, each with its pros and cons. 

Be that as it may, you might find it useful to set up a domain name with a service such as [no-ip.com]("http://no-ip.com") that redirects to your server's connection. If you have a public IP address that changes, you will need to arrange for your DNS records at no-ip to be updated: many routers come with the ability to do this automatically. You will also need to arrange port forwarding within your router so that incoming requests get directed to the correct machine.

---

### Post by spindler on 2011-12-05
I should mention this is my second server.    I have another UBUNTU 11.10 server on the local network which has the ip address 168.168.1.101.

This machine seams to be having issues and I do not know why. 

As I mentioned once I am finished with the clean install the machine has access to the internet.   It is only when I change the address to a static configuration does the network connection shut down. 

I am not using an ISP or website server.  This is within my own network.

---

### Post by lisati on 2011-12-05
Is using your router to set a static IP address an option for you?

---

### Post by spindler on 2011-12-05
Note really,

I can do port forwarding but that would not be what I would want to do with my router.  It would make things more complicated. 

I would rather be able to fix the issue with the server.  Since the problem is with the server.  I am not looking for a work around at this point.

Is there a way of configuring the network access?

How would I set the internet connection on the server?

What tool cal I use to find the issue I have?

Why would this interface file work on one Ubuntu 11.10 machine and not on a second machine?   Could there be a hardware configuration I need to look at?

---

