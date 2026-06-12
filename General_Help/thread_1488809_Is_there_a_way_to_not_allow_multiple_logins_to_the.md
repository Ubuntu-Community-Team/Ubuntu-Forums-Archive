---
title: "Is there a way to not allow multiple logins to the shell?"
date: 2010-05-20
forum: General Help
---

### Post by supradave on 2010-05-20
Is there a way to prevent a user from being able to login more than once.  Not a one-time login, but a single login.  What I'm trying to do here is in moving our email system, an email user would login to this account, enter some password information, sync up their email, and have the passwords files removed, then log off.  Next user can log in to the same account.

The reason for the single login is to protect the user's passwords.

---

### Post by iponeverything on 2010-05-20
There are many ways of doing this, two that come to mind that would easy to implement are:

- You could touch /etc/nologin on the user login and remove it on logout. 

- You could change the user account shell to /bin/false on login and change back on logout.

---

