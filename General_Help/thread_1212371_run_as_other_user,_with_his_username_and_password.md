---
title: "run as other user, with his username and password"
date: 2009-07-13
forum: General Help
---

### Post by zoli on 2009-07-13
I have a really simple question, I've googled a lot but cannot find the result - maybe it's too simple :)

How to execute a program from console (bash) with a single command, using another user's username and password? Current user cannot be a sudoer, another user is not always the same so setuid is not an option - consider we have no root access at all.

Any help would be appreciated.
Thanks!

---

### Post by lambros on 2009-07-13
Have you tried the 'su' command?

```
su otheruser
```

---

### Post by bodhi.zazen on 2009-07-13
> **zoli said:**
> I have a really simple question, I've googled a lot but cannot find the result - maybe it's too simple :)

How to execute a program from console (bash) with a single command, using another user's username and password? Current user cannot be a sudoer, another user is not always the same so setuid is not an option - consider we have no root access at all.

Any help would be appreciated.
Thanks!

sudo -u <user> command

or su as above

---

