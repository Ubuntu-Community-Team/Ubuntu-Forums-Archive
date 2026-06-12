---
title: "Groups for new user"
date: 2006-02-17
forum: General Help
---

### Post by eqisow on 2006-02-17
I want to create a new user that has the same admin privileges as the user that is created on a fresh install. However, I no longer have that original user on my computer so I'm not not sure what secondary groups this new user needs to be in. Could anybody pull up their user configuration and give me the groups? Thanks in advance.

---

### Post by jrib on 2006-02-17
For sudo privileges, your user should belong to the 'admin' group.  The other groups my user belongs to are: $USER adm dialout cdrom floppy audio dip video plugdev lpadmin scanner, where $USER is my username

I'm using gnome, but I suspect it makes no difference as to the other groups that a new user has.

---

