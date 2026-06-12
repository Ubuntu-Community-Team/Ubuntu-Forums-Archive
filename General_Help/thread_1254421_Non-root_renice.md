---
title: "Non-root renice"
date: 2009-08-31
forum: General Help
---

### Post by MWkemo on 2009-08-31
Hello,

having problem with renice. I wont to allow to user the renice for  processes from lower priority to higher. I can renice from higher priority to lower but not reverse. I did try to add to /etc/security/limits.conf line with "* - nice -19" and "* - renice -19" but this is not working. 
It's a Debian Lenny distribution.

Help please?

---

