---
title: "Problem: Want to set up wireless laptop with static IP on home network."
date: 2010-02-14
forum: General Help
---

### Post by fisheater on 2010-02-14
Setting up static IP for ubuntu 9.04 laptop.

Hi,

Stuck a bit here…

Problem: Want to set up wireless laptop with static IP on home network.

Background: I have become de facto IT help desk for elderly friend. Was spending too much time patching and sorting her XP, put 8.04 on her laptop. It ran beautifully and without any home visits other than social calls. 

Goal: Set up Nx Nomachine on her computer so I can login and tune it up or add programs from afar. 

To date: 
1.	Installed dnydns on router.
2.	Installed NoMachine on laptop
3.	Installed Fail2Ban
4.	Stuck at getting static wireless IP address

The original setup was 8.04. Found there were complex workaround, so upgraded to 9.04 hoping it would be a simple fix. No such luck. I did it at my home for a wired computer and it was dead easy.
 
This is what I followed without success, likely because this is for a wired connection. I tried the GUI method. (There are some elements of this tutorial that I don’t understand)
[http://linhost.info/2008/11/how-to-set-a-static-ip-on-ubuntu-810/](http://linhost.info/2008/11/how-to-set-a-static-ip-on-ubuntu-810/)

Some questions;
# The primary network interface
auto eth0 			(not in my case, I am using wireless)
iface eth0 inet static


address 192.168.1.110 	(this is my static IP address?)
network 192.168.1.0  	(what is this?)
netmask 255.255.255.0	(this seems standard, no need for explination)
broadcast 192.168.1.255 (is this standard?)
gateway 192.168.1.1	(this is the IP I access my router on)



Suggestions or alternative wireless static setup options for 9.04?

Always ambitious and thankful,

FE

---

### Post by sgosnell on 2010-02-14
Do on the router.  Have the router do the dirty work, it's easier.  The router manual should have the details, and it should be available on the innertubes.

---

### Post by fisheater on 2010-02-14
D'oh. It's so simple and tidy i can hardly stand it. I didn't know it could do that.

Thanks for pointing out the obvious, I will have a look into it and let you know how it went.

(I found this gem: [http://corz.org/comms/hardware/router/static.ip.address.php](http://corz.org/comms/hardware/router/static.ip.address.php) - scrolled down to 'The Router').

Thanks for pointing out the tree.

FE

---

### Post by bruno9779 on 2010-02-14
I would use gitso. (Give Tech Support to Others)

You can compile a .deb from source with you IP address coded in, so the supported person only has to install the .deb and nothing else.

You have to setup your port forwarding. The supported person doesn't.

Fixed IP is needed only for you, since the communication is started from the host machine, that knows it's own IP address.

here goes a link : 

[http://code.google.com/p/gitso/](http://code.google.com/p/gitso/)

PS: By the way, it is cross platform (Win, OSX and linux)

---

