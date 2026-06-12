---
title: "Extended partition permissions / multiple users / groups."
date: 2009-08-23
forum: General Help
---

### Post by credobyte on 2009-08-23
```
**Group:** home
**Permissions:** read/write/delete

**Group:** home_limited
**Permissions:** read

```

Let me explain. All I want is to have my extended partition to be readable to *home_limited *users and read/write/delete permissions to *home* users.

So far I've only this. Sadly, it doesn't work the way I need ( no way I could add *home_limited* ) ..
```
sudo chown -R dainis:home /data
```

Any ideas/suggestions/commands appreciated :)

---

### Post by michy99 on 2009-08-23
> **credobyte said:**
> ```
**Group:** home
**Permissions:** read/write/delete

**Group:** home_limited
**Permissions:** read

```

Let me explain. All I want is to have my extended partition to be readable to *home_limited *users and read/write/delete permissions to *home* users.

So far I've only this. Sadly, it doesn't work the way I need ( no way I could add *home_limited* ) ..
```
sudo chown -R dainis:home /data
```

Any ideas/suggestions/commands appreciated :)
A file (everything in linux is a file, including a drive) can only have one owner and one group. You can set permissions for the owner, the group and others. If you use home as the group and set group permissions to read/write and set others permissions to read only, that would work.

Unless there are users which are not members of either group that you don't even want to have read permissions.

---

### Post by credobyte on 2009-08-23
> **michy99 said:**
> A file (everything in linux is a file, including a drive) can only have one owner and one group. You can set permissions for the owner, the group and others. If you use home as the group and set group permissions to read/write and set others permissions to read only, that would work.

Unless there are users which are not members of either group that you don't even want to have read permissions.

The problem is that I might want to populate home_limited permissions to read/write ( without delete ), not only read. That's why I need a way to not just add "nothing" but add something pre-defined.
More over, I will ( soon ) need to add a group which should have no access to this partition at all.

Regarding "everything is a file", what's the point of using *inode/directory* and *inode/file* ?

---

### Post by michy99 on 2009-08-23
I don't think there is any way to have write permissions but not delete permissions. Delete is part of being able to write to a file.

A directory is a special kind of file, but it is a file, nonetheless.

As to what you are trying to do, I don't think there is a way to do it with groups. Like i said, a file (or directory, or disk) can only have one group.

---

### Post by credobyte on 2009-08-23
> **michy99 said:**
> I don't think there is any way to have write permissions but not delete permissions. Delete is part of being able to write to a file.

A directory is a special kind of file, but it is a file, nonetheless.

As to what you are trying to do, I don't think there is a way to do it with groups. Like i said, a file (or directory, or disk) can only have one group.

Is there a way to change permissions to a user, not group ? I mean, if I create a new limited ( not an administrator account ) user and I want it to have read/write/delete permissions to /data .. Is there a way to achieve that without removing/changing current partitions owner/group ?

---

### Post by michy99 on 2009-08-23
It sounds like you want to create a hierarchy of users with different access levels. I'm sure there is a way to do it, but I don't know what it is.

---

### Post by credobyte on 2009-08-23
> **michy99 said:**
> It sounds like you want to create a hierarchy of users with different access levels. I'm sure there is a way to do it, but I don't know what it is.

Yes, that sounds quite close to what I'm trying to achieve - progress :)

---

