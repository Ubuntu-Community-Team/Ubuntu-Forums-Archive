---
title: "user can't authenticate"
date: 2009-07-17
forum: General Help
---

### Post by simniger_jonathan on 2009-07-17
I have user in the office that can log on to her Ubuntu user account, but can't authenticate to do updates and other administrative tasks.  Shouldn't her login password also authenticate?  Will just resetting the password via rescue mode boot fix it?  I don't want to break things completely!

Thanks.

---

### Post by nikhilbhardwaj on 2009-07-17
the user must be a part of the administrators group
ordinary users can't install software or update the systen

---

### Post by nikhilk on 2009-07-17
> **simniger_jonathan said:**
> I have user in the office that can log on to her Ubuntu user account, but can't authenticate to do updates and other administrative tasks.  Shouldn't her login password also authenticate?

Does her account have sudo priviledges? The first account created on a fresh install is by default given sudo privileges.
Take a look at [this]("https://help.ubuntu.com/community/RootSudo") page describing the sudo concept.

---

