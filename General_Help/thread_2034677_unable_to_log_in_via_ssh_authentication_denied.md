---
title: "unable to log in via ssh authentication denied"
date: 2012-07-28
forum: General Help
---

### Post by Orang3 on 2012-07-28
any advice appreciated,

[http://paste.ubuntu.com/1105450/](http://paste.ubuntu.com/1105450/)

thanks,

---

### Post by Orang3 on 2012-07-29
ok, got this resolved with the help of escott from #ubuntu on freenode, and this forum thread 
[http://ubuntuforums.org/showthread.php?t=892686](http://ubuntuforums.org/showthread.php?t=892686)

Through reading the /var/log/auth.log on the server, and reading the thread linked above, it was found that the home/**username **directory had nonstandard permissions.  After changing them back to the standard, everything was okay.  The group and owner were changed back to the **username **(chown, chgrp), and the permissions were set back to 755 (chmod).

This problem was first discovered due to an amazon aws server being unable to be logged in to.  Authentication was refused after all methods were tried, and the verbose ssh log spit out a *roaming not allowed* message.  The drive was detached and attached to another (working) instance so the permissions could be set, and then reattached to the original server to check whether it worked.

---

