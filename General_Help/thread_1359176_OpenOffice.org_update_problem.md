---
title: "OpenOffice.org update problem"
date: 2009-12-19
forum: General Help
---

### Post by Dark Sorrow on 2009-12-19
I have downloaded OpenOffice.org 3.1.1 32-bit Linux DEB version. I extracted but unable to install it. Please help.
I got an error Conflicts with the installed package 'openoffice.org-core'.
Then i removed my exsiting OpenOffice.org through Add/Remove Program then also same error. Now i don't even have an OpenOffice.

---

### Post by Barriehie on 2009-12-19
> **Dark Sorrow said:**
> I have downloaded OpenOffice.org 3.1.1 32-bit Linux DEB version. I extracted but unable to install it. Please help.
I got an error Conflicts with the installed package 'openoffice.org-core'.
Then i removed my exsiting OpenOffice.org through Add/Remove Program then also same error. Now i don't even have an OpenOffice.

Try:
```

sudo apt-get purge openoffice.org-core
``` then reinstall via the repos.  There's usually a reason the repo versions are what they are for a given distro so when moving outside the repo versions it's a good idea to make a backup! :)

Barrie

---

### Post by Hagar Delest on 2009-12-19
See [[Ubuntu] Installing OOo on Debian and Co.](http://user.services.openoffice.org/en/forum/viewtopic.php?f=16&t=68)

---

