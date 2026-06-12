---
title: "tzdata causes error"
date: 2010-05-02
forum: General Help
---

### Post by rmartin16 on 2010-05-02
Awhile ago I moved timezones and tried to adjust Ubuntu to reflect this.  Something went wrong and the system began using UTC for its local time.  At some point later I ran "apt-get upgrade" and my recent failed change caused an error with apt-get. Now apt-get upgrade returns:

Preconfiguring packages ...
Setting up tzdata (2010i-0ubuntu0.9.10) ...
dpkg: error processing tzdata (--configure):
 subprocess installed post-installation script returned error exit status 10
Errors were encountered while processing:
 tzdata
E: Sub-process /usr/bin/dpkg returned an error code (1)

The reason the above story is vague is because this has been a problem for nearly two months.  Since then, I have fixed my problems with the system time; however, resolving the apt-get error has eluded me.  I searched extensively for a solution and tried many things, including trying to remove and reinstall tzdata.  Anyway I've tried to do this is unsuccessful, as it insists the dependencies must also be removed or that my entire system will come crashing down.  That being said, if anyone finds an already posted solution, please direct me to it.

Ubuntu 9.10 Server is installed on this system without a desktop manager.

Any help is appreciated.  Thank you.

---

### Post by rmartin16 on 2010-05-09
for anyone with a similar issue, I've worked around this issue by renaming /var/lib/dpkg/info/tzdata.postinst.  After this, errors are not thrown during upgrade.  I'm not sure of the further and later ramifications of doing this, but I'm sure they'll come.

---

### Post by dcstar on 2010-05-10
> **rmartin16 said:**
> for anyone with a similar issue, I've worked around this issue by renaming /var/lib/dpkg/info/tzdata.postinst.  After this, errors are not thrown during upgrade.  I'm not sure of the further and later ramifications of doing this, but I'm sure they'll come.

Remove the cached (and probably corrupted) copy of the tzdata package in the apt cache and then reinstall it - that will force a download of a clean copy.

---

### Post by rmartin16 on 2010-05-10
As far as the system is concerned (i.e. apt-get install tzdata), tzdata is installed correctly and at the latest version.  This appears to be true as anything seemingly associated with tzdata works properly.  Unfortunately, I can't, or don't know how to, reinstall tzdata as apt-get informs me all of it's (many) dependencies will also be reinstalled.

---

