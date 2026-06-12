---
title: "Can I set default ownership of a drive root?"
date: 2009-09-19
forum: General Help
---

### Post by wesg on 2009-09-19
I'm looking for a better way to handle permissions on my file server. I have multiple drives. Most are used for storage and I have no concern about security. 

How can I mount the drive AS a user, so that even copied data maintains those user details?

---

### Post by blueridgedog on 2009-09-19
Change the ownership of the mount point (prior to mounting) and the root of the mounted drive will be owned by the owner you select.

---

