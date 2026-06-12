---
title: "Get an old version of mysql?"
date: 2006-03-13
forum: General Help
---

### Post by rshruti on 2006-03-13
Hi,

I just installed kubuntu, and I'm coming from gentoo.  I had a few mysql databases, although I am no mysql expert.  Unfortunately, when I was backing up, I just backed up the whole directory rather than exporting the tables.  Subsequent googling has indicated that I should have exported the tables and imported them on the new system.  Turns out the new system has a newer version of mysql (4.x, I think) and the old system had 3.something.  So it's not reading the tables.  My question is, how can I get the tables back?  Is there any way of upgrading the tables, or can I get an old version of mysql on my system that will read them?  Any help would be appreciated.  I'd rather not compile from source...

Thanks!

---

### Post by rshruti on 2006-03-13
Just thought I'd update - I downloaded a binary version of mysql (the old version I needed) and just ran it out of my home directory without installing it.  I was able to get my tables backed up and imported into the new version without having to mess with creating packages or uninstalling the old server or anything.

---

