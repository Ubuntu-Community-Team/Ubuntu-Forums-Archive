---
title: "how to upgrade to 9.10rc"
date: 2009-10-23
forum: General Help
---

### Post by cmcanulty on 2009-10-23
I downloaded the cd now how do I upgrade from it? Thanks

---

### Post by Giblet5 on 2009-10-23
You boot from that CD and reinstall.

Or, you wait a few days for 9.10 to release, then do a true Upgrade from Update Manager.

;)

---

### Post by kilinu5889 on 2009-10-23
> **Giblet5 said:**
> You boot from that CD and reinstall.

Or, you wait a few days for 9.10 to release, then do a true Upgrade from Update Manager.

;)

Not really. Unless the update manager will actually update GRUB. That, and the people who have been using ext3 might want to upgrade to ext4.

---

### Post by Giblet5 on 2009-10-23
> **kilinu5889 said:**
> Not really. Unless the update manager will actually update GRUB. That, and the people who have been using ext3 might want to upgrade to ext4.

A version upgrade does overwrite grub (it does update-grub which is all you need on grub2)...

Ext4 is great for large file ops, but there's little change for regular file ops over ext3. It's not worth reinstalling for, IN MY OPINION. Here is a grain of salt . to take with that.

---

### Post by snowpine on 2009-10-23
You can always upgrade from one release to the next. Some users have been using Ubuntu for years without reinstalling. Other users prefer a fresh reinstall. It is purely a matter of preference and your individual needs.

---

