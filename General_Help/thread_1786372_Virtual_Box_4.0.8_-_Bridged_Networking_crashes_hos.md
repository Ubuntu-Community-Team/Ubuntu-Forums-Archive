---
title: "Virtual Box 4.0.8 - Bridged Networking crashes host (kernel 2.6.38-10)"
date: 2011-06-19
forum: General Help
---

### Post by jtmdias on 2011-06-19
Hello everyone!
I have an Ubuntu 10.10 host running in VirtualBox  4.0.8 r71778, and I need to setup a LDAP authentication network between  two VM's: a Maverick-based distro and Ubuntu Server 11.04.

Screenshot of the two running perfectly fine:
[http://img855.imageshack.us/img855/1340 ... aecrap.png]("http://img855.imageshack.us/img855/1340/capturaecrap.png")

Using NAT, I can have the two VM's up and running on VBox, but they get the same IP (10.0.2.15).
So  I googled it and quickly found out that I needed to change the VM's  network interfaces to Bridged Networking. So I tried that. 
Here's two screenshots of the default configurations:

1- Ubuntu Maverick based distro:
[http://img813.imageshack.us/img813/3481 ... figura.png]("http://img813.imageshack.us/img813/3481/capturaecraeosconfigura.png")

2- And here is one of the Ubuntu Server:
[http://img857.imageshack.us/img857/2651 ... server.png]("http://img857.imageshack.us/img857/2651/capturaecraubuntuserver.png")
(I'm Portuguese, that's why there are mixed languages in the UI)

It's  pretty stupid to explain like this, but whenever I try to start one of  those two using Bridged Networking, I get a black screen full of errors  (I can't take a printscreen of that, so I took a bunch of pictures -  yeah, it's lame, I know  [IMG]http://forums.virtualbox.org/images/smilies/icon_lol.gif[/IMG] ). Then, I have to press the power button to shut down my host, and restart the pc.
Here they are:

Part 1- [http://img21.imageshack.us/img21/4476/cimg2279p.jpg](http://img21.imageshack.us/img21/4476/cimg2279p.jpg)
Part 2 - [http://img849.imageshack.us/img849/6481/cimg2280.jpg](http://img849.imageshack.us/img849/6481/cimg2280.jpg)

Where I think the problem is:
[http://img137.imageshack.us/img137/8021/cimg2281g.jpg](http://img137.imageshack.us/img137/8021/cimg2281g.jpg)


My host is currently running Linux kernel 2.6.38-10.
I have dkms, linux-header-generic and build-essentials installed (and the VB extension package too)
And my host is a laptop, connecting to the internet using the router my ISP provided me.

How can I solve this? Is this some kind of bug regarding 2.6.38-10 kernel?
I don't have other pc's to test my LDAP authentication, so I needed the two VM's to have different IP's.

Thanks in advance  [IMG]http://forums.virtualbox.org/images/smilies/icon_mrgreen.gif[/IMG]

---

### Post by pqwoerituytrueiwoq on 2011-06-19
just a thought (lame workaround)
one bridged and one using nat

---

### Post by drdos2006 on 2011-06-19
You have different adapter types for each VM Network Interfaces.
Try making each NIC the same.
It may help.

regards

---

### Post by jtmdias on 2011-06-19
> **pqwoerituytrueiwoq said:**
> just a thought (lame workaround)
one bridged and one using nat

Thanks for the response, but I think that won't work, just because every time I start one of them using a bridged adapter, my pc crashes. 

But thanks anyway :)

---

### Post by drdos2006 on 2011-06-19
I am running same Virtual box version on my Ubuntu 10.4 LTS [edit] Desktop [/edit]
My linux-headers version is 2.6.32.32.38
The NIC in each of my VM is : Adapter 1 : Intel PRO/1000 MT Desktop (Bridged adapter, eth0)
I do not have any problem running Windows XP, Version 7 or Ubuntu Server 10.4 simutaneously on Gigabyte motherboard with 4 Gig RAM.


regards

---

