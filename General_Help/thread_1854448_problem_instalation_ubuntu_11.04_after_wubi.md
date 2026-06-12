---
title: "problem instalation ubuntu 11.04 after wubi"
date: 2011-10-04
forum: General Help
---

### Post by SeL81 on 2011-10-04
I`m a new user, after test ubuntu 11.04 by wubi, I decided to install it at all, but when I was intalling from wubi, there was a error making the partitions in the HD, the instalation window got freezed, but the rest of the aplication was normal, even I turned off the netbook with the menu.
 
When I would to turn on my netbook, after the screenshot of acer, the screen get black, I tried to access the Bios but I couldn`t; I disconected the HDD and turn on the netbook, and in this time I culd access the BIOS.
 
so if I format the HD in another PC, can I install ubuntu form USB?
 
Greetings
 
My netbook:
 
Acer aspire one 532h
Atom N450
HDd 250GB
2 GB RAM

---

### Post by Mark Phelps on 2011-10-04
Sorry, but I'm having a real hard time understanding what you did, and the order in which you did it ...

A Wubi install does not create any partitions, so installing that way will NOT fail on partitioning, since it is not involved.

If you installed via Wubi first, and then (while it was STILL on the PC) decided to install a second time to its own partition, you COULD get partition problems -- depending on the current partition setup on your PC.  At the very least, you should have REMOVED the Wubi install BEFORE attempting a second installation, if for no other reason, to free up the disk space used by the first install.

Installing either via Wubi or separately has NOTHING to do with your BIOS settings.  So, if you now can't access the BIOS setup, you've done something else.  You probably can access the BIOS with the drive disconnected because this is the default in the netbook if no drive is found during the initial boot.

Before providing any details, we would need to know WHAT is installed in the netbook drive at this time.  Which OSs, and which versions.

And yes, you CAN install Ubuntu from USB but if your drive is a mess, with remnants of different installs on it, that's not going to make things any better.

---

