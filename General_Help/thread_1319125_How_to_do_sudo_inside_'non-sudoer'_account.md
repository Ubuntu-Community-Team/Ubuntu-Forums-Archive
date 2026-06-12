---
title: "How to do sudo inside 'non-sudoer' account"
date: 2009-11-08
forum: General Help
---

### Post by emigrant on 2009-11-08
hi all,
i have 4 accunts in my system.
im a sudoer and have access to all the other (non-sudoer) accoutns.
is there any way i can do sudo inside those non-sudoer accounts (without making them sudoers)?

for example, if i want to do sudo nautilus inside a non-sudo account, i have to come back to my sudo account and do it :(



thank you very much for your helps...

---

### Post by madverb on 2009-11-08
su <username>

That will start a shell as that user.

---

### Post by emigrant on 2009-11-08
thanks man it worked :).

---

