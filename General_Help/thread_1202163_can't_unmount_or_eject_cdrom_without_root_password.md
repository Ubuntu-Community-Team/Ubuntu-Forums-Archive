---
title: "can't unmount or eject cdrom without root password"
date: 2009-07-01
forum: General Help
---

### Post by buzzmandt on 2009-07-01
anytime I try to unmount or eject cdrom i must give root password.
sudo eject works, but would like to be able to left click, select eject like normal.  any ideas?  permission issue?  I have already ensured myself being checked on cdrom privelages and I am.

---

### Post by x22 on 2009-07-02
try adding "user" to yr /etc/fstab in the "defaults"
column like so

/dev/hdc    /cdrom   iso9660   user,noauto   0    0

---

