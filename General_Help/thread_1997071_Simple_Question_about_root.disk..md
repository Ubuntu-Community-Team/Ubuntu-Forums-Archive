---
title: "Simple Question about root.disk."
date: 2012-06-04
forum: General Help
---

### Post by emptycoder on 2012-06-04
Hi, I have a simple question about root.disk, I have installed Ubuntu alongside windows via WUBI, so if I copied root.disk to somewhere else (as a backup plan in case if something goes wrong) then copy it back and overwrite it, would it work?
Thanks.

---

### Post by oldfred on 2012-06-04
Yes & no. I do not use wubi, but understand you might have to reinstall for all configurations to be in Windows, so you get the default root.disk and then you could replace that root.disk with yours.

[https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)
[https://help.ubuntu.com/community/Wubi](https://help.ubuntu.com/community/Wubi)

If you find you like Ubuntu, then it may be time to change to a full partitioned install.
[http://howsoftwareisbuilt.com/2009/03/12/interview-with-agostino-russo-wubi-ubuntu/](http://howsoftwareisbuilt.com/2009/03/12/interview-with-agostino-russo-wubi-ubuntu/)
Agostino: Wubi actually wasn’t designed to do long-term installations. The main aim was really to let people try out Ubuntu with confidence. Normally, users that start with Wubi tend to upgrade to a full installation to a dedicated partition at the next release cycle.

HOWTO: migrate wubi install to partition - bcbc 
[https://help.ubuntu.com/community/MigrateWubi](https://help.ubuntu.com/community/MigrateWubi)

---

### Post by O2Blevel on 2012-06-04
> emptycoder:
Hi, I have a simple question about root.disk, I have installed Ubuntu alongside windows via WUBI, so if I copied root.disk to somewhere else (as a backup plan in case if something goes wrong) then copy it back and overwrite it, would it work?
Thanks.

That worked for me. What didn't work was to compress the root.disk and split it into several parts. Not sure what went wrong, could very well have been something I did.

---

### Post by emptycoder on 2012-06-05
Thanks a lot for the info!

---

