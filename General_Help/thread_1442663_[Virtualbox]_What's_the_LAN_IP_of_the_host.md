---
title: "[Virtualbox] What's the LAN IP of the host?"
date: 2010-03-30
forum: General Help
---

### Post by blazemore on 2010-03-30
Hi all, I'm running a testing web server on my Ubuntu machine, and running XP with Dreamweaver in a virtual box. What's the address of the web server within virtualbox?
I found some information that suggests its 192.168.0.202 but that doesn't seem to work.
How can I find out?

---

### Post by rcah on 2010-03-30
use windows 7
will not **** yu
your useing a private ip
 your in the range of 192.168.0.0 which is private only.....................................
do you understand this ?

---

### Post by rcah on 2010-03-30
windows 7 kicks *** comp to this crappy os
get a ******* ? this OS is ****!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!1

---

### Post by the yawner on 2010-03-30
> **rcah said:**
> use windows 7
will not **** yu
your useing a private ip
 your in the range of 192.168.0.0 which is private only.....................................
do you understand this ?
I barely understood whatever it is you're trying to say.

@blazemore
Virtualbox supports a couple of network settings for your virtual machine. (Right-click the virtual machine then click Settings>Network)

On the drop down menu *Attached to:* you can set it to NAT which will give the machine a 10.x.x.x IP. However, this IP won't be accessible to the host machine. If you set it to Bridged, you can assign the virtual machine an IP on the same network as your host machine. Much better if you have a DHCP on your network, as the virtual machine will acquire an IP.

---

### Post by blazemore on 2010-03-30
> **the yawner said:**
> I barely understood whatever it is you're trying to say.

@blazemore
Virtualbox supports a couple of network settings for your virtual machine. (Right-click the virtual machine then click Settings>Network)

On the drop down menu *Attached to:* you can set it to NAT which will give the machine a 10.x.x.x IP. However, this IP won't be accessible to the host machine. If you set it to Bridged, you can assign the virtual machine an IP on the same network as your host machine. Much better if you have a DHCP on your network, as the virtual machine will acquire an IP.

I don't need the host to access the guest.
I need the guest OS to be able to access the host.
How can I do this?

---

### Post by blazemore on 2010-03-30
Thanks, I set it to Bridged, and now I can just use [http://james-desktop](http://james-desktop)
You are a legend, thanks a lot!

---

### Post by the yawner on 2010-03-30
Glad it worked out well for you. Cheers. :D

---

