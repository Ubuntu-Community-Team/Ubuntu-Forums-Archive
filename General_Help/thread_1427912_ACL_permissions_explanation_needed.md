---
title: "ACL permissions explanation needed"
date: 2010-03-12
forum: General Help
---

### Post by dragos2 on 2010-03-12
I have these permissions on a Ubuntu acl samba:

```

# file: file
# owner: joe
# group: developer
user::rwx
user:john:rwx
group::rwx
mask::rwx
other::r-x
default:user::rwx
default:group::rwx
default:other::---

```As you can see the owner is joe and has rwx on the file, then there is john defined as an exception with rwx, the the group permissions, the mask.

Then the things gets messy: what are these default:user, other and group ? Only some files have these defaults and others don't.

What takes precedence: other, default: other or mask ?

Normal files look like this
```

# file: file2
# owner: mary
# group: c
user::rwx
group::r-x
other::r-x

```Can someone enlight me here please :)

---

