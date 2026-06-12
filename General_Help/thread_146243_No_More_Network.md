---
title: "No More Network"
date: 2006-03-17
forum: General Help
---

### Post by dystrust on 2006-03-17
I'm running Breezy on an IBM Thinkpad T23, and things have been going quite well for a while now.  However, yesterday the following updates were installed:

base-config to 2.67ubuntu20
dhcp3-client to 3.0.2-1ubuntu7
gnupg to 1.4.1-1ubuntu1.2
linux-image 2.6.12-10-386 to 2.6.12-10-30
login to 1:4.0.3-37ubuntu8
passwd to 1:4.0.3-37ubuntu8

Now my eth0 will no longer activate.  I can go into networking and activated it, and it takes an unusually long time.  After closing the network window, nothing has happend, and if I reopen the network window, it shows not activated.  Any ideas?

---

### Post by arphe_el on 2006-03-17
you need to reconfigure your settings since you update it your old configuration was overwritten. 

goto system>administration>networking

click ethernet > properties > then enter your ip address, subnet mask, gateway address, configuration select whether you're static or dhcp

hope this helps you. GODspeed
enter you ip address,

---

