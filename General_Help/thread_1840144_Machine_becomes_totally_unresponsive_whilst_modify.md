---
title: "Machine becomes totally unresponsive whilst modifying files via samba"
date: 2011-09-07
forum: General Help
---

### Post by hymerman on 2011-09-07
I've had this a few times now, and it's really worrying me, as it means I have to hard reset. Normally Ubuntu is so stable!

I have samba set up on an Ubuntu server (11.04), sharing a directory mounted on a RAID 5 array managed by mdadm. If I access this via a Windows PC, and modify a large number of files quickly (e.g. some bulk edit operation, in this case applying changes to tags of music files), the server becomes completely unresponsive.

By that I mean the connection is lost, I can't SSH into or ping it, and pressing keys on the keyboard does nothing (which I can see if I log on locally first; after the lock up the terminal doesn't respond at all).

I left it for about an hour last time this happened and it didn't get any better, so I had to hard reset it, which I *really* don't want to do again. Also, just waiting isn't really a good solution, I'd expect it to always be responsive.

This has happened 3 or 4 times now, and seems completely repeatable - I get around it by modifying smaller batches of files.

Any ideas?

---

