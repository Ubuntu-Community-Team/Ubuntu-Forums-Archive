---
title: "add program in start up"
date: 2009-11-21
forum: General Help
---

### Post by zeek333 on 2009-11-21
Hi, 
I installed 2 nodes lb1 and lb2 with heartbeat, all looks prety good just after restart heartbeat don't start automatically. 

does any1 could help me with that?

Thanx

---

### Post by Andreas1 on 2009-11-21
> **zeek333 said:**
> Hi, 
I installed 2 nodes lb1 and lb2 with heartbeat, all looks prety good just after restart heartbeat don't start automatically. 

does any1 could help me with that?

Thanx

not sure what you are talking about but i suppose you could just add an entry in System > Preferences > Autostart

---

### Post by zeek333 on 2009-11-24
*I can't go this way *System > Preferences > Autostart coz i don't use GUI

---

### Post by Zefal on 2009-12-09
Seems I was having the same issue as you my friend. I had installed heartbeat too and by default it is setup to start on boot however it simply didn't start. I confirmed it was setup with a script in init.d correctly and links were correct in rc*.d directories but just didn't start.

I changed the DISTFUNCS line in the heartbeat script to:

DISTFUNCS=/etc/init.d

as the previous parameter wasn't correct for ubuntu (/etc/rc.d/init.d/functions doesn't exist in Ubuntu)

This helped me and got it starting on boot. Let me know if this works for you too and I'll let the guy who wrote the script know so he can change it to work for Ubuntu and release it. :D

It is also worth noting that my two systems with this issue were running like a dog and after fixing - they were super speedy again!

Thanks,

Paul

---

