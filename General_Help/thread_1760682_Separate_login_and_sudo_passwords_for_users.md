---
title: "Separate login and sudo passwords for users?"
date: 2011-05-17
forum: General Help
---

### Post by c@ssie on 2011-05-17
sudo has the disadvantage that if someone hacks your user account, they get all your privileges too.  And using a rot password without sudo has the disadvantage that you can't give out subsets of privleges, anyone with the root password has access to everything.  

Is there a way to assign users both a login password, with no sudo privileges, and a separate sudo (not root) password, that can't be used to login?

---

