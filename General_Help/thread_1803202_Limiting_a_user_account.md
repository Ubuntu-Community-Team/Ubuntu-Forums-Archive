---
title: "Limiting a user account"
date: 2011-07-12
forum: General Help
---

### Post by Coor on 2011-07-12
Is it possible to limit a user account from accessing '/mnt/'?

---

### Post by JedMeister on 2011-07-13
I would imagine that you could use permissions to exclude access, although if it is to stop access to USBs and other removable media then IIRC Ubuntu uses FUSE to mount removable media (normally a user wouldn't otherwise have that sort of power). So you could somehow stop them from being able to run FUSE. 

Although I could be completely wrong and heading you off on a irrelevant tangent.

---

### Post by deserthowler on 2011-07-13
You should be able to limit groups the user belongs to.

Earl

---

