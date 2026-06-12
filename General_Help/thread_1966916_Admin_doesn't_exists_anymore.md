---
title: "Admin doesn't exists anymore"
date: 2012-04-27
forum: General Help
---

### Post by Ghost_Mazal on 2012-04-27
Lo guys ,

I see that the admin group doesn't exists anymore. Usually I added my 2nd sudo user to admin group.
Since the admin group have been removed (change is NOT always good) , how do I add a user to sudo on 12.04 ?

Thank you

---

### Post by mc4man on 2012-04-27
12.04 now uses the 'sudo' group instead of 'admin' though for compatibility with upgrade installs 'admin' still works (at least in some areas

So just add to the sudo group (/etc/group

Master bug on that may be helpful
[https://bugs.launchpad.net/ubuntu/+source/policykit-1/+bug/893842](https://bugs.launchpad.net/ubuntu/+source/policykit-1/+bug/893842)

---

### Post by mc4man on 2012-04-27
> **rockinfreeworld said:**
> aptitude is no longer installed by default

And how  that is relevant to this?

---

### Post by Ghost_Mazal on 2012-04-28
Thank you

---

