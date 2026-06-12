---
title: "Creating System restore point"
date: 2011-04-23
forum: General Help
---

### Post by Kyzyks9001 on 2011-04-23
How can I create a system restore point in Ubuntu, and when I do so am I able to restore to a point before installing Ubuntu?

---

### Post by Frogs Hair on 2011-04-23
Ubuntu does not have system restore that is a Windows feature . There is backup software in the software center. If I have misunderstood please elaborate .

---

### Post by Mark Phelps on 2011-04-25
> **Kyzyks9001 said:**
> How can I create a system restore point in Ubuntu, and when I do so am I able to restore to a point before installing Ubuntu?

Your question makes me nervous -- because it looks like you intend to use Windows System Restore to back up your Windows install before installing Ubuntu -- to get Windows back if anything goes wrong.

That is NOT how System Restore works.  It does NOT back up your Windows installation; instead, it makes a copy of some Windows settings, some config files, and some system files.  It does NOT backup your data or applications.

To make a restorable backup of your Windows install, you need to backup the entire partition -- and for that you need different tools.

---

