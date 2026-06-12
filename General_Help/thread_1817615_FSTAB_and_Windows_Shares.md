---
title: "FSTAB and Windows Shares"
date: 2011-08-03
forum: General Help
---

### Post by nomad1970 on 2011-08-03
Hi,

About 4 years ago a I built a file server for a small business based on Ubuntu 9.xx Server.

Anyway, I'm a bit rusty and have forgotten some of the basics, so I'm hoping someone can answer some basic questions.

I currently am running Ubuntu Server 11.4 on an HP Proliant ML350, raid 1.

I've created a directory in /home call DATA and chmod 777 since it will accessed by all users.

This works fine as far as I can tell, I have full read / write and map easily from a windows 7 machine.

I can't however login to homes...

Looking at my notes from my 4 year ago server, I notice I mounted home in FSTAB.  Is this my problem?  Is there a connection between mapping drives through windows and having a mountpoint for home in FSTAB?

Is it because I chmod 777 on the DATA dir that it works without problems?  I obviously don't want to do that for home.

This is what my current FSTAB looks like:

Any help appreciated.

Thanks.

---

