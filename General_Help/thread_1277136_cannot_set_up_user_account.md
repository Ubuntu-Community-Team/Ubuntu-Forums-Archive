---
title: "cannot set up user account"
date: 2009-09-27
forum: General Help
---

### Post by tvkpz on 2009-09-27
Hi

I am trying to set up a user account by the name 'MatlabUser'.

The system does not allow me to set up the account saying that user account name must be all lower case letters.

Any idea why ubuntu does not allow me to do this and how to set up the account. For some reason I need the account name to have the upper case letters.

Need an urgent reply on this. Thanks!

---

### Post by P4man on 2009-09-28
```
sudo adduser --force-badname YouRBadUseRName
sudo passwd YouRBadUseRName
```

---

