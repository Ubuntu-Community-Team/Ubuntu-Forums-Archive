---
title: "Show a Users Groups ?"
date: 2009-08-17
forum: General Help
---

### Post by UltraDangerLord on 2009-08-17
Hello All,

I'm wondering how to show the groups a particular user belongs to, also how do I go about adding a existing user to a group ?lets say the wheel group.

I think its something like usermod user1 -G wheel

---

### Post by michy99 on 2009-08-17
To show groups:```
groups USERNAME
```To add a user to an existing group:```
sudo adduser USERNAME GROUP
```To make a new group:```
sudo addgroup GROUP
```

---

### Post by DaithiF on 2009-08-17
> **UltraDangerLord said:**
> 
I think its something like usermod user1 -G wheel

michy99's is the easiest way to remember, but just fyi, the version you were thinking of is:
```
sudo usermod -aG groupname user
```
the a is important as if you just do -G then any existing group memberships are removed, leaving ONLY the one you specify.

---

### Post by Bachstelze on 2009-08-17
> **UltraDangerLord said:**
> I'm wondering how to show the groups a particular user belongs to

```
id <user>
```

---

