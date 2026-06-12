---
title: "RAID question"
date: 2011-03-25
forum: General Help
---

### Post by Steam. on 2011-03-25
How can I find out what RAID level i am using/at?

I know there are two Seagate ST3500418AS HDD's(2x500GB), and when I open any home directory, it shows 856GB available.Just interested cause I need to take one out so i need to know if i take it out will the OS still work?

---

### Post by Smart Viking on 2011-03-25
Post the output of
```
mount
```

---

### Post by Grenage on 2011-03-25
> **Steam. said:**
> How can I find out what RAID level i am using/at?

I know there are two Seagate ST3500418AS HDD's(2x500GB), and when I open any home directory, it shows 856GB available.Just interested cause I need to take one out so i need to know if i take it out will the OS still work?

You're either using RAID0, or no RAID. If it's RAID0, it will stop working when you remove it; if it's not in a RAID, you'll simply not be able to access what's on it, and probably get some fstab warnings.

---

### Post by luceerose on 2011-03-25
```
sudo mdadm --detail /dev/md0
```
Replace 'md0' with whatever the drive designation for your raid is.
(If it's software raid, it should be md0 by default).

That should give you enough info.

---

