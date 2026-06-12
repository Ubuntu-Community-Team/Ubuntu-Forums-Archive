---
title: "Users and Groups Not Working"
date: 2010-08-10
forum: General Help
---

### Post by yedidyah on 2010-08-10
When I go to System-> Administration-> Users and Groups and click on Users and Groups I get the following error:

The configuration could not be loaded
An unknown error occurred.

Any quick fixes?

---

### Post by plucky on 2010-08-10
> **yedidyah said:**
> When I go to System-> Administration-> Users and Groups and click on Users and Groups I get the following error:

The configuration could not be loaded
An unknown error occurred.

Any quick fixes?

No quick fix,but from a terminal what does ```
users-admin
``` show you.

---

### Post by yedidyah on 2010-08-10
Within Terminal this is the response:

(users-admin:2118): Liboobs-WARNING **: There was an unknown error communicating with the backends: Launcher could not run (out of memory)


Outside Terminal the same pop-up came up saying:

The configuration could not be loaded
An unknown error occurred.


I don't know what "out of memory" means here my computer is large enough and powerful enough to handle these things.

AMD 64 Dual Core
2 GB of RAM
Dual Boot OS XP and Lucid
170 GB of available space on HD

---

### Post by yedidyah on 2010-08-10
Any ideas?

---

### Post by drdos2006 on 2010-08-10
try re-installing 'adduser' from the package manager.

regards

---

### Post by yedidyah on 2010-08-10
adduser reinstall is a no go.

---

### Post by drdos2006 on 2010-08-10
What happens when you use Terminal to add a dummy account with "adduser dummy" ?

regards

---

### Post by plucky on 2010-08-11
Found [this bug](https://bugs.launchpad.net/ubuntu/+source/system-tools-backends/+bug/574078) which has no solution.

Good Luck

---

### Post by yedidyah on 2010-08-11
> **drdos2006 said:**
> What happens when you use Terminal to add a dummy account with "adduser dummy" ?

regards
Can't locate auto/I18N/Langinfo/autosplit.ix in @INC (@INC contains: /etc/perl /usr/local/lib/perl/5.10.1 /usr/local/share/perl/5.10.1 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.10 /usr/share/perl/5.10 /usr/local/lib/site_perl .) at /usr/share/perl/5.10/AutoLoader.pm line 173.
 at /usr/lib/perl/5.10/I18N/Langinfo.pm line 10
adduser: Only root may add a user or group to the system.

---

### Post by yedidyah on 2010-08-11
> **plucky said:**
> Found [this bug](https://bugs.launchpad.net/ubuntu/+source/system-tools-backends/+bug/574078) which has no solution.

Good Luck
I am not sure how I am going to configure my printer for the network then.

---

### Post by yedidyah on 2010-08-13
So what is the ONLY solution reinstalling Lucid?!

---

