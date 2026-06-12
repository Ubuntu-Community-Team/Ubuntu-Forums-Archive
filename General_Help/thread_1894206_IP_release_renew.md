---
title: "IP release renew"
date: 2011-12-12
forum: General Help
---

### Post by cozmosis33 on 2011-12-12
How do i do an IP release renew through the terminal?

---

### Post by SlugSlug on 2011-12-12
sudo /etc/init.d/networking restart

or 
sudo ifconfig eth0 down && sudo ifconfig eth0 up

---

### Post by The Cog on 2011-12-12
**sudo dhclient** should work too.

---

### Post by jonobr on 2011-12-12
Turn your machine off and on.....

Just kidding:P SlugSlug and The Cog are right, In my day, (leans back and smokes a pipe)
with early versions of windows, I recall you had to actually do that. Maybe 3.1 and 95.


With PCMCIA cards you could stop and restart the hardware, but imagine that, having to reboot to change an ip address.

You tell the kids that and they wont believe you.....:lolflag:

---

### Post by SlugSlug on 2011-12-12
> **jonobr said:**
> Turn your machine off and on.....

Just kidding:P SlugSlug and The Cog are right, In my day, (leans back and smokes a pipe)
with early versions of windows, I recall you had to actually do that. Maybe 3.1 and 95.


With PCMCIA cards you could stop and restart the hardware, but imagine that, having to reboot to change an ip address.

You tell the kids that and they wont believe you.....:lolflag:
Yep! Belive it or not I had to network some NT3** machines last month, an IP change needed a reboot!

---

### Post by jonobr on 2011-12-12
Id believe it slugslug, Im just glad I dont have your job:-)

---

