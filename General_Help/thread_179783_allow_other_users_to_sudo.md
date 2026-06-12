---
title: "allow other users to sudo"
date: 2006-05-20
forum: General Help
---

### Post by an.echte.trilingue on 2006-05-20
I know the answer to this is probably out there, but since almost every thread in this forum includes the string "sudo" it is really hard to search for questions about sudo.

Anyway, does anybody have any idea how to allow a second user to use the sudo command?

I have tried to add the user to all the same groups as the first account, and adding the second user to the sudoers file, but no avail.  I am kinda stumped.  Any ideas?

Using dapper, btw.

Thanks.

mat

---

### Post by IYY on 2006-05-20
Are you positive you added the second user to the admin group?

```
cat /etc/group | grep \^admin:
```

to check who's in that group.

---

### Post by an.echte.trilingue on 2006-05-22
Yup; it's there.  Output for adm:

```
adm:x:4:mat,venla
```

or for the group admin:

```
admin:x:4:1000,1001
```

I am pretty stumped.

I put this user in the every same group as the first user, no avail.

Thanks for responding, by the way.

---

