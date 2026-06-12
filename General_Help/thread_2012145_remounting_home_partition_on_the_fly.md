---
title: "remounting home partition on the fly"
date: 2012-06-28
forum: General Help
---

### Post by hwttdz on 2012-06-28
I've just updated my fstab and I would like to remount the home partition (as well as mount the mounts in the fstab), but I would like to do this without rebooting.  How can I go about doing this?  Would all users need to logout?

Ok, so I feel a little silly because I thought this was going to be more difficult than it was.  It is apparently enough to update the fstab and then run mountall as root.

---

### Post by Cheesemill on 2012-06-28
```
sudo mount -a
```
Will mount all filesystems defined in /etc/fstab

---

