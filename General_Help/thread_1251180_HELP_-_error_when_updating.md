---
title: "HELP - error when updating?"
date: 2009-08-27
forum: General Help
---

### Post by dbpbandit on 2009-08-27
When I try and run the update manager I get the following error:

E: Could not get lock /var/cache/apt/archives/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the download directory

Can someone tell my what this means and how I can release the lock on the resource so the update can continue? thanks.

-Dave

---

### Post by MTGap on 2009-08-27
Something happened to package.

Just use this to remove the lock:

> sudo rm /var/cache/apt/archives/lock

You should be able to upgrade now.

---

### Post by dbpbandit on 2009-08-27
That did it, thanks.....

-Dave

---

