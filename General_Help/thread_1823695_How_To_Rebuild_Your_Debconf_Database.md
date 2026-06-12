---
title: "How To Rebuild Your Debconf Database"
date: 2011-08-12
forum: General Help
---

### Post by msp3k on 2011-08-12
Hello gurus,

I recently had this error start cropping up when upgrading packages:

```

debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
debconf: DbDriver "templatedb": /var/cache/debconf/templates.dat is locked by another process: Resource temporarily unavailable

```

I found this disturbing, as there were no other processes running that were associated with package maintenance.

This was next followed by:

```

error: Cannot find a question for <some debconf key>

```

After running dpkg-get-selections, I found that my debconf database was nearly empty!  The only entries listed were for the ldap packages.  All other entries had been deleted.

Since this was my mail server I was desperate to find a quick fix, but a quick forums search and a quick google search failed me.  There may indeed be a fast and easy fix for this type of problem already out there, but I wasn't able to find it with a quick search.  So, for the benefit of others, if you should ever find yourself in the same boat one day, then here is how you fix it:

First, rebuild debconf's own debconf database entries:
```

dpkg-reconfigure debconf

```

Then, rebuild the debconf database for everything else:
```

for pkg in $(dpkg-query --show | awk '{print $1}'); do echo ; echo "--> $pkg" ; echo ; dpkg-reconfigure --frontend=noninteractive --priority=critical $pkg < /dev/null ; done

```

Press RETURN and watch stuff scroll by.

You will receive some errors about packages for whom debconf reconfiguration should be done via another package (ex: exim4-daemon-heavy).  It appears to be safe to ignore those.

I believe that the above command will NOT restore any debconf customization that you had set in the past.  It will merely restore the database with default configuration data.  (At least, this is my understanding.)  So you will still need to use dpkg-reconfigure to configure any packages that require custom settings.

---

