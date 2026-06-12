---
title: "How to make init use a certain flag for a service it starts."
date: 2011-06-15
forum: General Help
---

### Post by Buttons840 on 2011-06-15
I've installed MongoDB and I want init to start the database with the --journal flag.  I'm quite rusty on how init works, but I know it involves the /etc/init and /etc/rc directories.

I've found /lib/init/upstart-job and someone in the chat is suggesting that I just edit that bash script, but I can see it's involved with more than half the system service, so I'm a little hesitant to edit it.  In fact, I'm pretty sure if I followed that advice I'd really screw up my system and then the person "helping" me would just stop responding.

Anyways, any ideas where I can start?

---

### Post by Buttons840 on 2011-06-16
I found that in general you can edit the conf files in /etc/init ; these are simple and short bash scripts and easy to modify the boot flags.  I was able to do what I wanted by editing /etc/init/mongodb.conf .

However, a better solution was to edit /etc/mongodb.conf .  I put "journal = true" in that file and it did what I wanted.  This way there was no need to edit the init bash script.

Hopefully this will help someone else.

---

