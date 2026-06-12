---
title: "Add user not displaying in login screen"
date: 2009-11-05
forum: General Help
---

### Post by toreriks on 2009-11-05
Hi,

How can I add a user that will not show up in the login screen? The user will run wsgi deamon processes only, and should not be a regular login user.

So far I've tried the **adduser** command with both **--disabled-login** and **--disabled-password** options. Still, the user is displayed in the login screen.

Thanks,
tores

---

### Post by sisco311 on 2009-11-05
Set the UID of the user to less then 1000:
```
adduser --uid 999 ....
```

You can change the UID of an existing user with the usermod command:
```
usermod -u 999 username
```

---

