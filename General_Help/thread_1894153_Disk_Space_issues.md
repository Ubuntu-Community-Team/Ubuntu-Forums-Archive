---
title: "Disk Space issues"
date: 2011-12-11
forum: General Help
---

### Post by CheezItMan on 2011-12-11
Hello,

We'd quickly run out of space on our primary hard drive for our school webserver.  So I installed a secondary HD and mounted it on /var/www/hdb and then moved several sites over to it.  That helped for a bit, but rapidly a df -h began to show the root partition running out of space.  Now almost all the sites are running on the secondary hard drive, so there's no way this should be filling up so quickly.

Is the / partition caching files on the other hard drive or something?

---

### Post by llamabr on 2011-12-11
Hard to tell.  What's on these disks, and how big are they?

---

### Post by lykwydchykyn on 2011-12-11
I'd try installing filelight and running it on / to see where all the space is being eaten up.

Sounds like a log file is going nuts, or some web service is generating files and not cleaning up after itself.

---

