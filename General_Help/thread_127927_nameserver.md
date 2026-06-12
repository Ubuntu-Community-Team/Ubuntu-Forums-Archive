---
title: "nameserver"
date: 2006-02-10
forum: General Help
---

### Post by sod on 2006-02-10
In desperate need for help I post this tread here cause problems getting the right answer at the beginnersarea. 
Im having a DHCP modem/router and my problem is that sessions such as Synaptic loading, or downloading media files thru browser stops with [1.0.0.0]:...
Found one tread who suggested to edit /etc/resolv.conf file. In my file it only stands: nameserver 192.168.1.1 the suggestion was to edit whith 
nameserver 61.1.96.69
nameserver 61.1.96.71
nameserver 192.168.1.1
in that order.
Did and it works!   for 1 or 2 minutes in Synaptic then I have to edit again because the list returns to: 
nameserver 192.168.1.1 only.
Another note is when my comp starts it cannot sync external clock.
Maybe same problem?

Could anyone help me please?:cry:

---

### Post by hw-tph on 2006-02-10
The clock syncronization problem and the Synaptics problem is most likely the same; i.e. a name resolution problem.
If what you type in /etc/resolv.conf gets overwritten automatically it's probably your DHCP setup that doesn't work correctly for some reason. I assume you have a little home router that is supposed to forward DNS queries, hence the 192.168.1.1 in your resolv.conf, so the first thing I think you should do is restart that little box and see if it takes care of DNS properly. I have had similar problems and poked around forever with the attached computer only to discover that a simple reboot of the router solved it.

A quick and ugly solution could be first editing your resolv.conf and then change the permissions so it is readonly: **sudo chmod 444 /etc/resolv.conf**


Håkan

---

