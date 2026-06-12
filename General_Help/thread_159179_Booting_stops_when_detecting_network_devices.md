---
title: "Booting stops when detecting network devices"
date: 2006-04-12
forum: General Help
---

### Post by benvdh on 2006-04-12
Hey everyone,

I'm having some problems booting kubuntu. I don't really know what caused the problem since kubuntu was running fine until a week ago. Then kubuntu suddenly started to freeze every time I try to boot kubuntu. Kubuntu just stops booting when it says "Setting up network devices". The system doesn't give any errors on the screen, it just stops.

I've tried booting the older kernel. But that didn't help either. The strange thing is that suse doesn't have this problem when I try to boot it.

Any thoughts on how to solve this problem ?

Regards,

Ben

---

### Post by Sidk on 2006-04-12
Try pressing ctrl+c when it stops and see what happens

---

### Post by benvdh on 2006-04-13
Hey,

it worked. I also noticed another problem. When I look in the /etc/init.d/ folder there is no dhclient nor some other dhcp script that could be ran to get an ip. So now when I want to have a router IP I need to run dhclient manually all the time. Strange thing is that I am able to access the web with a 169.254 kind of IP.

So is there a way to automaticly get a router IP  every time I boot ?

Regards,

Ben

---

