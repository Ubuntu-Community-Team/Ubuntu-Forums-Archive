---
title: "Make /home mount / unmount"
date: 2009-09-26
forum: General Help
---

### Post by cat2005 on 2009-09-26
Is is safe to make /home mount and unmount by editing fstab?  I noticed it always automounts upon boot.  If I edited fstab to make mounting manual, then could doing so cause any problems, especially since I have several different user accounts using /home for their storage?

---

### Post by blueridgedog on 2009-09-26
Assuming the user's home directories are on /home, then you will have issues if a non-root user attempts to log in with it unmounted.

---

