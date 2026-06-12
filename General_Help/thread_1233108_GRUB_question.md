---
title: "GRUB question"
date: 2009-08-06
forum: General Help
---

### Post by Psycho.mario on 2009-08-06
Would it be possible to add an option to my GRUB loader, so that it drops in to a (very) limited shell, and all it can do is networking (from /etc/network/interfaces) and bridges?

Currently i have two computers, one with two cards, and the other with only one, the computer with two cards gets the network through eth0 and bridges it to eth1. The second computers then uses this for it's networking. 

However, this setup means i have to have both computers on to give the second one networking, so is it possible to have a GRUB option in which all it does is networking?

Thanks

---

### Post by P4man on 2009-08-06
It might be possible to load ubuntu without gui from grub, but a better solution is probably installing a small dedicated distro that only does networking, next to your ubuntu installation. That would give you a convenient web interface to the pc(/router) and maybe some other functionality you may find useful.

There are dozens out there, to name two:
[http://smoothwall.org/](http://smoothwall.org/)
[http://trac.ebox-platform.com/](http://trac.ebox-platform.com/)

---

### Post by ptn107 on 2009-08-06
I believe 'Recovery Mode' might give you such an option.

---

### Post by Psycho.mario on 2009-08-06
Thanks, I think i am going to have a look at that eBox Platform. Looks good, shame there isn't a liveCD to test out my hardware :(

Thanks again

---

### Post by Psycho.mario on 2009-08-06
Although the ebox thing looks good, it doesnt work on my system (doesnt install)

Im looking at the other one now.

---

### Post by P4man on 2009-08-06
Just so you know, I have no experience installing either alongside ubuntu on the same drive. im not sure how they handle partitioning, i've used both (long time ago) but with a dedicated drive... Its probably a good idea to prepare a partition in ubuntu before installing any of those. Maybe better to put it on their own drive if you can. at least be careful you dont wipe your harddisk while installing.

edit: i just saw smoothwall only supports 1 harddisk I guess that means it wont play nice with ubuntu. 

Perhaps you can try something that boots from a usb / CF / floppy, like monowall:
[http://m0n0.ch/wall/installation_generic.php](http://m0n0.ch/wall/installation_generic.php)

---

### Post by Psycho.mario on 2009-08-06
I couldnt get either of those suggestions to work, im just about to try m0n0wall. I (purposely) wiped that computer to try out these things, it doesnt really matter as i have two, so i will play around till i find the right combination of softwares.

Thanks

---

