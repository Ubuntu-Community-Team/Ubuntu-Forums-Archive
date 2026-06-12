---
title: "burning data to DVD in Nautilus: does HD space matter"
date: 2006-06-27
forum: General Help
---

### Post by ChrisC on 2006-06-27
I am pulling my hair out trying to get my data backed up to a DVD-RW just so that I can do a dist-upgrade without risk of losing my personal data.

I created a folder of backup data (using sbackup) and it is 1.4 GB in size.  I then ran "sudo nautilus" so that I could write the root-owned files to the disc and preserve the ownership and permissions.  When I attempt to write to disc, it says that I do not have enough space.  DVD-RW discs are supposed to have a capacity of 4-5 GB.  Mine is blank.

I suspect that instead of the DVD space, it's actually trying to tell me that it's out of hard drive space.  Does nautilus cache the data to a /var directory or something?  I don't have a lot of space on my / (root) partition, certainly not 1.4 GB.

If it does cache to the hard drive, how can I change the default cache location?  My /home partition is huge.

---

### Post by professor_chaos on 2006-06-27
I can't answer your question, but can suggest gnome-baker for your buring needs, as it allows you to set this tmp dir.

---

### Post by ChrisC on 2006-06-27
Indeed, once I changed sbackup to write to a directory in /home, then cleaned out the .Trash (Nautilus -> Empty Trash), I created 7 GB of free space and the Nautilus DVD burning operation proceeded normally.  I'd file a bug (misleading error statement) on the Nautilus burn subsystem, but I'm running breezy and I assume that it's improved in dapper.  And the whole reason for this backup was so that I could proceed with the upgrade to dapper ... starting now!

---

