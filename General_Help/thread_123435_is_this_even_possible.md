---
title: "is this even possible?"
date: 2006-01-30
forum: General Help
---

### Post by prodi_g on 2006-01-30
i have an airport express that for wireless in my dorm room.  i have usb printer attached to it so that i can do wireless printing via cups.  i also am running ubuntu on my desktop comp and i wanted to know if it would be possible to print to this wireless printer as well from a wired network?  

has anyone tried this before or any similar?  thanks in advance, 

j.

---

### Post by alamba on 2006-01-30
Short answer: Yes you can. 

But it really depends on your network topology. One way is to connect the printer to the wired network. Another is to have a single DHCP give out IP's both to your wireless and wired network (not a good idea generally). Third is to have an interface between your wired and wireless network and NAT the IP's for traffic crossing that interface (cleaner way of doing things).

Akshay

---

