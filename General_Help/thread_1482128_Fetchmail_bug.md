---
title: "Fetchmail bug"
date: 2010-05-13
forum: General Help
---

### Post by jdege on 2010-05-13
I'm setting up an ubuntu 10.04 system.  I usually use fetchmail to retrieve my mail, running it from cron.  (Installed with apt-get install fetchmail)

When I run fetchmail from the command-line, it works just fine.  When I run it from cron, I get error emails in my inbox:

   smbutil.c:90: unicodeToString: Assertion `len+1 < sizeof buf' failed.

Some Googling around lead me to a bug:

   [http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=449179](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=449179)

The thing is, that bug is being reported as being fixed, in version 
6.3.9~rc2-6.  But I'm running:
 
  fetchmail release 6.3.9-rc2+GSS+NTLM+SDPS+SSL+NLS+KRB5

So clearly the bug has not been fixed.

---

