---
title: "samba Permissions acl"
date: 2012-05-13
forum: General Help
---

### Post by Elfish on 2012-05-13
Hi,

i got a problem with a samba share...
let's say i have 2 folders. the first folder is only accessible by 1 group (sharepriv), which has r/w access.

getfacl output:
```
# file: complete/
# owner: elfish
# group: elfish
user::rwx
group::rwx
group:sharepriv:rwx
mask::rwx
other::---
default:user::rwx
default:group::rwx
default:group:sharepriv:rwx
default:mask::rwx
default:other::---
```

i set the permission with the new acl modification feature
the 2nd folder is accessible by 2 groups and 1 user.
1 group has rw access (same group as on the first folder)
the 2nd group only has read permissions

getfacl output
```
# file: Sonstiges/
# owner: elfish
# group: elfish
user::rwx
user:shareguest:r-x
group::rwx
group:sharepub:r-x
group:sharepriv:rwx
mask::rwx
other::---
default:user::rwx
default:user:shareguest:r-x
default:group::rwx
default:group:sharepub:r-x
default:group:sharepriv:rwx
default:mask::rwx
default:other::---
```

if i move a file from the first folder to the second folder by cutting it out in windows and inserting in the 2nd folder
the 2nd group (sharepub) has no access to it.

i thought that the parent dir permissions are set to sub folders/files

oh and i enabled honor existing acls and enable permission inheritence, which i think should be correct.

anyone got an idea whats wrong?

the same happens if i use mv.
permissions are somehow preserved. is there anyway to disable that?

---

### Post by Elfish on 2012-05-17
bump

---

### Post by Elfish on 2012-07-02
bump

---

