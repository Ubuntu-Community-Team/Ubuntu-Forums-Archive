---
title: "revert / permissions"
date: 2010-07-20
forum: General Help
---

### Post by lfitz on 2010-07-20
Hi,
Is there a way to revert to default permissions using chmod, for root filesystem?  As root I accidentally chmod'd / to 755, luckily this is a dev server and not production so its not critical to fix for me, just wondering though....

---

### Post by bodhi.zazen on 2010-07-20
> **lfitz said:**
> Hi,
Is there a way to revert to default permissions using chmod, for root filesystem?  As root I accidentally chmod'd / to 755, luckily this is a dev server and not production so its not critical to fix for me, just wondering though....

IMO it is easier, faster, and more reliable to back up the data and re-install.

I have seen two users undo this mistake in the last several years, and both took 4-5 days.

I have seen more users start, then give up.

See this thread : 

[http://ubuntuforums.org/showthread.php?t=1525655&highlight=permissions](http://ubuntuforums.org/showthread.php?t=1525655&highlight=permissions)

---

### Post by hikaricore on 2010-07-20
Resetting stock permissions on critical directories and files might be something worth submitting as an idea on launchpad if it's not been suggested already.

---

