---
title: "Software Raid on external, is it movable?"
date: 2011-01-01
forum: General Help
---

### Post by xkaliburx on 2011-01-01
I have an external icy doc with 4 750GB drives.  There connected via external esata to an older machine and I just built a raid 5 on it, and it seems perfect, mounted as /dev/md0, note this is running the latest 10.10. version.

I've been around a while, but never using software raid, but I want to upgrade the hardware here in the next few months so if I take that drive, plug it into the new server, under disk management, will I be able to just mount it?  I know there getting good, but I assume somewhere there has to be a config file or something that says 'hey use these 4 external drives' or something like that.

Thanks.

---

### Post by dcstar on 2011-01-02
> **xkaliburx said:**
> I have an external icy doc with 4 750GB drives.  There connected via external esata to an older machine and I just built a raid 5 on it, and it seems perfect, mounted as /dev/md0, note this is running the latest 10.10. version.

I've been around a while, but never using software raid, but I want to upgrade the hardware here in the next few months so if I take that drive, plug it into the new server, under disk management, will I be able to just mount it?  I know there getting good, but I assume somewhere there has to be a config file or something that says 'hey use these 4 external drives' or something like that.

Thanks.

You will need to copy the relevant data from /etc/fstab and mdadm.conf (?) files I would say.

---

