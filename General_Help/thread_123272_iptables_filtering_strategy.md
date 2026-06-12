---
title: "iptables filtering strategy"
date: 2006-01-29
forum: General Help
---

### Post by madcap_magician on 2006-01-29
I'm not sure if I'm totally understanding IPTables at this point.

I've got my home network behind a server running Ubuntu that I'm using for masquerading.  On the server eth1 connects to my home network hub, eth0 connects to my DSL modem and the internet.  Now I want to set up my IPTables to secure the box.

My original strategy was to block everything coming in on eth0 and then start opening ports 1 by 1 as I find out I need them.  Everything incoming on eth1 would be unblocked, as well as all outgoing on either NIC.

The problem I ran into is that I'm not sure how well that will work.  Most applications use a default port which I would open up (like 22 for ssh) to establish the connection but then move to a port above 1024 for transfering data.  Since in general I wouldn't have a way to control what port it moves to and it could be different every time it isn't practical to try to manually open one of these ports every time.

Will blocking all incoming connections except the ones I specifically allow cause a problem for applications that move to a diferent port?  Will this work?

Also, will it have any adverse effect on masquerading?

---

### Post by madcap_magician on 2006-01-30
Well, luckily you can change your iptables and they are automatically restored at reboot because I've toasted mine a dozen times now.  I'm setting them up over ssh so I can tell when I screw up because ssh no longer works.

I'm having problems with iptables-restore and iptables -F.  Both of these commands just hang and never do anything, I have to contorl-c to kill them.  Does anyone know what might be causing this?

---

