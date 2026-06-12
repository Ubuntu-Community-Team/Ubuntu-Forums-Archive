---
title: "Scripting Unison"
date: 2011-10-07
forum: General Help
---

### Post by Warthaug on 2011-10-07
I am trying to write a script which will synchronize several folders on my work desktop with a USB flash drive.  I want full two-way synchronization, which is why I'm not using rsync.

I've read though a dozen guides on this and cannot make it work.  No matter whose scripts I copy I always get the error "Too Many Roots, 2 expected but 4 provided".  I cannot find out what causes that error.

For example, I'd like to backup my "Grants" folder, located in my /data/ folder (/data is a separate partition on my HDD).  From my readings the following command should work:

unison /data "/media/MY USB/Desktop Sync" -path Grants

Bryan

---

