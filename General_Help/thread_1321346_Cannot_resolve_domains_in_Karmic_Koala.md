---
title: "Cannot resolve domains in Karmic Koala"
date: 2009-11-10
forum: General Help
---

### Post by Mooseknuckle on 2009-11-10
Hi.   I recently upgrade to 9.1 without a hitch.   Then, which I tried to run apt-update, it told me there were a bajillion packages I could remove if I do a sudo apt-get autoremove.   I did it, and now, I cannot connect to webpages, ubuntu update servers, or ssh to any hostname.

I'm not positive it was the autoremove, it could have been timing.

What I can do is ping a machine from my OTHER computer, get the ip address, and then access any machine by it's ip address.  For instance, I cannot open google.com in my web browser, but if I try to load 74.125.53.100:80, it loads fine.

This is not a router issue, because I'm connected to my wireless network right now with my laptop, and I also have a windows partition on that same computer that can access it as well (the network).   I really dont know where to begin troubleshooting this ... Any help?

Edit:

if have dhcp3-client and dhcp-common installed, and this is my resolv.conf:

domain domain_not_set.invalid
search domain_not_set.invalid
nameserver 192.168.0.1
nameserver 68.94.156.1

---

